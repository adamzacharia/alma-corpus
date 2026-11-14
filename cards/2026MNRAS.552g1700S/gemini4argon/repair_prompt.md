# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026MNRAS.552g1700S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–18 (2026) Preprint 7 September 2026 Compiled using MNRAS L [A] TEX style file v3.3

## **Dust Substructures and Line Perturbations driven by a Forming Planet in** **J16120**



Anibal Sierra [1] _[,]_ [2] _[★]_, Andrés F. Izquierdo [3] _[,]_ [4], Paola Pinilla [2], Kan Chen [5], Myriam Benisty [6], Laura Pérez [7],
Teresa Paneque-Carreño [8], Carolina Agurto-Gangas [9], Jaehan Bae [3], John Carpenter [10], Luca Cieza [11] _[,]_ [12],
Dingshan Deng [13], Stefano Facchini [14], Camilo González-Ruilova [12] _[,]_ [15] _[,]_ [16], Nicolás Kurtovic [6] _[,]_ [17],
Aleksandra Kuznetsova [18] _[,]_ [19], Carlo F. Manara [20], James Miley [10] _[,]_ [12] _[,]_ [21], Álvaro Ribas [22] _[,]_ [23],
Giovanni Rosotti [14], Miguel Vioque [20]

1 _Universidad Nacional Autónoma de México. Instituto de Astronomía. A.P. 70-264, 04510. Ciudad de México, México_
2 _Mullard Space Science Laboratory, University College London, Holmbury St Mary, Dorking, Surrey RH5 6NT, UK_
3 _Department of Astronomy, University of Florida, Gainesville, FL 32611, USA_
4 _NASA Hubble Fellowship Program Sagan Fellow_
5 _Kavli Institute for Astronomy and Astrophysics, Peking University, Beijing 100871, People’s Republic of China_
6 _Max-Planck Institute for Astronomy (MPIA), Königstuhl 17, 69117 Heidelberg, Germany_
7 _Departamento de Astronomía, Universidad de Chile, Camino El Observatorio 1515, Las Condes, Santiago, Chile_
8 _Department of Astronomy, University of Michigan, Ann Arbor, MI 48109, USA_
9 _Departamento de Física, Universidad Técnica Federico Santa María, Vicuña Mackenna 3939, San Joaquín, Santiago de Chile, Chile_
10 _Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura, Santiago 763-0355, Chile_
11 _Instituto de Estudios Astrofísicos, Universidad Diego Portales, Av. Ejercito 441, Santiago, Chile_
12 _Millennium Nucleus on Young Exoplanets and their Moons (YEMS), Chile_
13 _Lunar and Planetary Laboratory, the University of Arizona, Tucson, AZ 85721, USA_
14 _Dipartimento di Fisica, Università degli Studi di Milano, Via Celoria 16, Milano, Italy_
15 _Departamento de Física, Universidad de Santiago de Chile, Av. Victor Jara 3659, Santiago, Chile_
16 _Center for Interdisciplinary Research in Astrophysics and Space Science (CIRAS), Universidad de Santiago, Chile_
17 _Max Planck Institute for Extraterrestrial Physics, Giessenbachstrasse 1, D-85748 Garching, Germany_
18 _Center for Computational Astrophysics, Flatiron Institute, 162 Fifth Ave., New York, New York, 10025, USA_
19 _Department of Physics, University of Connecticut, 196A Auditorium Road, Unit 3046, Storrs, CT 06269, USA_
20 _European Southern Observatory, Karl-Schwarzschild-Strasse 2, D-85748 Garching bei München, Germany_
21 _European Southern Observatory, Alonso de Córdova 3107, Vitacura, Santiago, Chile_
22 _Astronomy Unit, Department of Physics and Astronomy, Queen Mary University of London, Mile End Road, London E1 4NS, UK_
23 _Institute of Astronomy, University of Cambridge, Madingley Road, Cambridge CB3 0HA, UK_


Accepted 2026 September 3. Received 2026 July 31; in original form 2026 June 9


**ABSTRACT**

Hints of planet formation have been independently reported within the gap of the disc around 2MASS J16120668–301027 from
millimetre continuum, infrared, and H _𝛼_ observations. In this work, we present new evidence for ongoing planet formation based
on Atacama Large Millimeter/submillimeter Array (ALMA) Band 7 observations, detecting 0.87 mm dust continuum emission
together with [12] CO (J=3–2) and [13] CO (J=3–2) line emission. Visibility modelling of the continuum data reveals an inner disc and
two dust rings peaking at 23 and 75 au. The continuum morphology is better reproduced by an eccentric disc model ( _𝑒_ ∼ 0 _._ 1) than
by an axisymmetric disc. We further investigate the gas kinematics through modelling of the [12] CO channel maps. The residual
line-width map shows a localised increase in velocity dispersion at the position of a previously reported circumplanetary disc
candidate (deprojected radius ∼32 au, position angle ∼170 [◦] ) and along its orbit. This signal is spatially coincident with kink-like
features and a transition from sub-Keplerian to super-Keplerian velocities. In addition, the velocity residual map exhibits an
arc-like structure extending outward from the planet candidate, while the gas kinematics—despite substantial uncertainties—is
consistent with inflow towards the candidate’s orbital radius. The observed increase in velocity dispersion agrees with predictions
from planet–disc interaction simulations, which produce enhanced turbulence both at the planet location and along its orbital
path. Taken together, the continuum morphology and gas kinematic signatures provide compelling new evidence for ongoing
planet formation within the disc gap.


**Key words:** Techniques: Interferometric – Protoplanetary discs


_★_ E-mail: asierra@astro.unam.mx
© 2026 The Authors

2 _A. Sierra et al._


**1** **INTRODUCTION**


Protoplanetary discs have been the subject of extensive observational studies for several decades across a wide range of star-forming
regions, providing key insights into the physical and chemical conditions under which planets form (e.g., Beckwith et al. 1990; Williams
& Cieza 2011; Dent et al. 2013; Ansdell et al. 2016; Pascucci et al.
2016; Andrews et al. 2018; Cieza et al. 2019; Öberg et al. 2021;
Benisty et al. 2023; Teague et al. 2025; Zhang et al. 2025). These
observations, spanning wavelengths from the infrared to the millimetre, have revealed a rich diversity of disc structures, including rings,
gaps, spirals, and asymmetries (e.g., Andrews et al. 2018; Long et al.
2018; Andrews 2020; Law et al. 2021b; Bae et al. 2023; Ginski
et al. 2024; Garufi et al. 2024; Valegård et al. 2024; Guerra-Alvarado
et al. 2025), many of which are thought to be linked to ongoing
planet formation. In parallel, theoretical frameworks describing the
formation and early evolution of planets have progressed from the
foundational core accretion and gravitational instability models to
more recent developments incorporating disc evolution, dust growth,
and planet–disc interactions (e.g., Goldreich & Ward 1973; Lissauer
1993; Pollack et al. 1996; Liu & Ji 2020; Manara et al. 2023; Orcajo
et al. 2025).

Despite this progress, directly detecting forming planets within
their natal discs remains observationally challenging. Young planets
are expected to be deeply embedded and often obscured by optically
thick dust and gas (Sanchis et al. 2020), while their observational
signatures can be subtle and easily confused with disc substructures
produced by other mechanisms (Currie et al. 2015; Montesinos &
Cuello 2018; Szulágyi et al. 2018, 2019; Szulágyi & Garufi 2021).
As a result, robust confirmation typically requires the combination
of multiple independent tracers, probing both dust and gas, and often
spanning several wavelengths and observing techniques. Even though
hundreds of discs have substructures, only a handful of proto-planets
have been confirmed to date, specifically in the discs around PDS 70
(Keppler et al. 2018; Haffert et al. 2019; Benisty et al. 2021) and
WISPIT 2 (van Capelleveen et al. 2025; Close et al. 2025). These
rare systems provide crucial benchmarks for testing planet formation theories and motivate continued high-resolution, multi-tracer
observations of discs with potential proto-planets.

Other systems in which tentative direct evidence for embedded planets has been suggested from infrared observations include
AB Aurigae (Currie et al. 2022), and HD 169142 (Hammond et al.
2023), where point sources have been identified within dust gaps
potentially carved by the planets themselves. In contrast, systems
showing indirect evidence, such as HD 163296 (Teague et al. 2021;
Izquierdo et al. 2022, 2026a), Elias 24 (Pinte et al. 2023), HD 100546
(Casassus & Pérez 2019), AS 209 (Bae et al. 2022; Izquierdo et al.
2023), exhibit either gas kinematic perturbations, Doppler flips, or
chemical tracers sensitive to localised planet-induced heating. Additionally, the presence of a young massive planet has recently been
proposed using Gaia astrometry combined with ALMA observations
in the disc around MP Mus (Ribas et al. 2025), demonstrating that
giant planets can also be identified through proper-motion anomalies.

A recently proposed planet-host candidate studied across multiple wavelengths is the disc around 2MASS J16120668–301027
(hereafter J16120). ALMA Band 6 ( _𝜆_ = 1 _._ 3 mm) dust continuum
observations suggested the presence of a dusty circumplanetary disc
(CPD) within a gap, at a radial separation of 32 au from the central star (Sierra et al. 2024a); although higher angular resolution and
sensitivity observations obtained one year later did not confirm this
detection (Li et al. 2025). In contrast, SPHERE infrared data (Ginski
et al. 2025) revealed point sources in the H (1.6 _𝜇_ m) and K (2.2


MNRAS **000**, 1–18 (2026)



_𝜇_ m) bands around the same location, and H _𝛼_ observations detected
localised excess emission with a signal-to-noise ratio ≳ 5 (Li et al.
2025). The latter may trace accretion onto a forming planet embedded within the gap, analogous to the H _𝛼_ features observed around
planets PDS 70 b and c (Haffert et al. 2019; Thanathibodee et al.
2019).
Although the exact location of the planet candidate differs between
tracers, Li et al. (2025) demonstrated that the offset between the
H _𝛼_ emission and the infrared point source in the K band can be
explained by orbital motion over the two-year interval between the
observations. Together, these findings provide compelling evidence
for the presence of a forming planet within the gap. The mass of the
planet candidate is estimated to lie between 0.1 and 5 M J, depending
on the adopted models (Ginski et al. 2025), which would be capable
of carving the gap observed at millimetre and infrared wavelengths.
J16120 is an M0-M0.5 star with an age between 5 and 10 Myr,
a luminosity of 0 _._ 25 _𝐿_ ⊙ (Fang et al. 2023; Ginski et al. 2025), an
effective temperature of 3810 K, and an accretion rate of log _𝑀_ [�] acc =
−9 _._ 21 ± 0 _._ 5 _𝑀_ ⊙ yr [−][1] (Ginski et al. 2025). Its X-Shooter spectrum
is consistent with a 0 _._ 60 ± 0 _._ 05 M ⊙ star (Ginski et al. 2025), while
its dynamical mass estimated from the CO kinematics is ∼ 0 _._ 7 _𝑀_ ⊙
(Sierra et al. 2024a). All these properties are similar to the stellar
properties of PDS 70 (Müller et al. 2018).
J16120 is located in the Upper Scorpius star-forming region at a
distance of 132.1 pc (Gaia Collaboration et al. 2023), and its disc has
previously been studied as part of the Upper Scorpius survey by Carpenter et al. (2025) and the AGE-PRO ALMA Large Program (Zhang
et al. 2025). In the latter, the disc was detected in several molecular
lines (Agurto-Gangas et al. 2025), including [12] CO (J=2–1), [13] CO
(J=2–1), C [18] O (J=2–1), N 2 H+ (J=3–2), H 2 CO (J=4 (0 _,_ 4) –3 (0 _,_ 3) ), and
C [34] S (J=6–5), while it was not detected in DCN (J=4–3) and DCO [+]

(J=4–3). From N 2 H [+] and CO isotopologues, the gas disc mass was
estimated to be 3 _._ 24 [+] − [1] 0 _[.]_ _._ [33] 72 [×][ 10] [−][3] _[ 𝑀]_ [⊙] [(][Trapman et al. 2025][), consis-]
tent with the external-photoevaporative viscous evolution models of
Anania et al. (2025). The comparison between the dust and gas extents of J16120 indicates that radial drift has been halted or slowed by
some mechanism (Agurto-Gangas et al. 2025), possibly linked to the
ring-like structure, where dust grains may be trapped. In addition to
the inner planet candidate, Sierra et al. (2024a) also reported a kink
observed in several CO channel maps beyond the dust continuum
emission. They speculated that the origin of this feature could be a
second planet candidate in the outer disc.
In this paper, we present new high-sensitivity, high-angularresolution, and high-spectral-resolution Band 7 ( _𝜆_ = 0 _._ 87,mm) observations of J16120 in dust continuum emission, [12] CO ( _𝐽_ = 3–2),
and [13] CO ( _𝐽_ = 3–2), revealing new evidence of planet formation
associated with the inner planet candidate in the gas emission. These
observations reinforce earlier reports of a forming planet in the gap
of J16120 and constitute a significant step forward in the detection
of planetary signatures in protoplanetary discs.


**2** **OBSERVATIONS**


The disc around J16120 was observed by ALMA in Band 7 ( _𝜆_ =
0 _._ 87 mm) from January to July 2024 (Project code: 2023.1.01100.S,
PI: Anibal Sierra) in configurations C43-6 (∼ 0 _._ 10 [′′] ) and C43-3
(∼ 0 _._ 47 [′′] ) at a representative frequency of 345.80 GHz. The former
configuration consists of four long baseline (LB) executions, and the
latter of three short baseline (SB) executions. The spectral setup was
configured with four spectral windows, with frequencies between
330.35 - 332.23 GHz, 330.55 - 330.61 GHz, 344.05 - 345.93 GHz,

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 3



345.76 - 345.82 GHz, and spectral resolution of 30.52 kHz and
976.56 kHz. This setup detects and spectrally resolves [12] CO (J=3–
2), [13] CO (J=3–2), and dust continuum emission.

The continuum data and continuum-subtracted line emission were

obtained following the imaging strategies for the discs in Upper
Scorpius of AGE-PRO (Zhang et al. 2025; Agurto-Gangas et al.
2025). The continuum-only datasets were obtained by identifying and
flagging the molecular lines in each spectral window. All executions
were aligned by fitting a 2D Gaussian to a low-angular-resolution
image of the dust continuum in each execution, allowing us to identify
the disc centre. We then re-centred all images to a common phase
centre, chosen as J2000 16h12m06.664505s -30d10m27.61789s, to
match the disc centre reported in Band 6 ( _𝜆_ = 1 _._ 3 mm) in Sierra et al.
(2024a).
Before self-calibrating the data, we examined the dust continuum visibilities from each execution to identify any flux offsets
between datasets. We found a flux difference of ≲ 10% between
the short-baseline (SB) and long-baseline (LB) executions. The flux
calibrators were observed closer in time to the LB executions [1]


(∼2 days of difference for executions uid://a002/X1198c0c/X2af,
uid://a002/X1199f9e/X528, and uid://a002/X1199f9e/X7f3a) compared to the SB executions (∼10 days of difference). Therefore, we
adopt the flux of the concatenated LB executions as reference and
scale the fluxes of all executions accordingly using the task `gencal` .
We double-check that de-coherence is not an important issue before
applying the flux-rescaling.
Self-calibration was performed using CASA (McMullin et al.
2007) version 6.4.3.27. We first self-calibrated the SB data
only. After two rounds of phase self-calibration where all the
SB spectral windows and scans were combined using the task
`gaingal` using `coombine=’spws,` `scans’`, time interval solutions
`solint=’inf’,` `’360s’`, and calibrating the data only using the
task `applymode=’calonly’`, the signal-to-noise (SNR) improved
by a factor of 143% and 8% with respect to the previous iteration,
respectively. Then, we concatenate the LB executions and proceed
to self-cal the whole dataset. In this process, the antenna reference is
taken as that with the best SNR, as reported by the weblog. After one
round of phase self-calibration where spectral windows and scans
were combined and time interval solution of `solint=’inf’` was

applied, the SNR increased by 5.6%. Additional tests using shorter
solution intervals and amplitude self-calibration did not result in significant SNR improvements, so these were not applied to the final
products. The final dust continuum image has an angular resolution
of 0 _._ 125 [′′] × 0 _._ 095 [′′], and a SNR of 69 when imaged with robust = 0.5.
Compared to the dust continuum image in Band 6 (Sierra et al.
2024a), both beam area and SNR of the Band 7 image in this work
are smaller by a factor of 2.
The molecular line data were obtained by applying the same astrometric aligns, flux offset scales, and self-calibration tables to the
original datasets without channel averaging, and subtracting the dust
continuum using the task `uvcontsub` . The final datasets are resample onto a regular velocity grid using the task `cvel2`, with a spectral
resolution of 25 m s [−][1] .
The dust continuum, [12] CO, and [13] CO datasets were imaged using
the `tclean` task in CASA, employing the multi-scale deconvolution algorithm with scales corresponding to point sources, one beam
size, and two beam sizes. For the molecular lines, we generated a
grid of image cubes with varying spectral resolutions (25, 50, and
100 m s [−][1] ) and Briggs robust parameters ( _𝑟_ = 0 _._ 0 _,_ 0 _._ 5 _,_ 1 _._ 0 _,_ 1 _._ 5 _,_ 2 _._ 0),


1 `[https://almascience.eso.org/sc/](https://almascience.eso.org/sc/)`



**Table 1.** Band 7 image parameters.


Data Robust Beam rms [∗] VRes

[mas × mas; deg] [mJy beam [−][1] ] [m s [−][1] ]


Continuum 0.5 125 × 95; -75.2 0.021  12 CO (J=3–2) 1.5 181 × 145; -78.8 4.9 25
13 CO (J=3–2) 2.0 183 × 143; -75.6 4.0 50


∗ For line maps, this is the rms per channel.


**Table 2.** Disc Sizes and Integrated Fluxes of J16120.


Data _𝑅_ 90 _𝑅_ 68 Flux

[au] [au] [mJy km/s] [∗]


Continuum ( _𝜆_ = 0 _._ 87 mm) 95 ± 14 81 ± 14 68 ± 3
13 CO (J=3–2) 140 ± 20 113 ± 20 2600 ± 300
12 CO (J=3–2) 180 ± 20 123 ± 20 10600 ± 500


∗ For continuum, units are mJy.


aiming to identify the optimal combination where small-scale spatial structures can be observed with good SNR in individual channel
maps. The fiducial products were generated with a spectral resolution of 25 m s [−][1] and a Briggs robust parameter of 1.5 for [12] CO, and
50 m s [−][1] with a robust parameter of 2.0 for [13] CO. For the dust continuum, we adopted a robust parameter of 0.5. The JvM correction
Jorsater & van Moorsel (1995); Czekala et al. (2021) was not applied to any of the final products; however, we cleaned down to a
1 _𝜎_ threshold, with very little signal not included in the clean model
and therefore affected by the non-Gaussianity of the beam (Zhang
et al. 2025). Table 1 shows a summary of the image parameter of the
fiducial products for the Band 7 observations.
Additionally, we use the self-calibrated Band 6 observations of
J16120 presented in Li et al. (2025), in which data from programs 2021.1.00128.L (PI: Ke Zhang, Zhang et al. 2025) and
2022.1.00646.S (PI: Feng Long) were concatenated to produce the
final dust continuum products. We refer the reader to Appendix A of
Li et al. (2025) for details of the Band 6 self-calibration procedure.


**3** **RESULTS**


**3.1** **Dust continuum and molecular moment maps**


The map of the dust continuum emission, and moment maps (computed using Discminer, Izquierdo et al. 2021) from [12] CO, and [13] CO
are presented in Figure 1. The moments were computed by clipping
the data to 1 _𝜎_ for Moment 0 (Integrated intensity map), and 3 _𝜎_ for
the peak intensity map, and the peak velocity.
The disc presents a ring like morphology and a bright inner disc
in both dust and [13] CO emission, as revealed by the moment 0 brightness radial profile. The peaks of the dust continuum and the [13] CO
emission coincide, likely indicating an accumulation of both dust
and gas in this region. The observed morphology is consistent with
previous millimetre and infrared observations (Sierra et al. 2024a;
Ginski et al. 2025; Li et al. 2025). The central emission in [12] CO is
more homogeneous (probably due to optical depth effects) but still
presents evidence of a ring and a bright central component. The peak
brightness reveals different disc morphologies in [12] CO and [13] CO. In
the optically thick regime (as typically expected for [12] CO), the peak
intensity approximates the brightness of the emitting layer. However,
in the optically thin case (more representative of [13] CO), the peak in

MNRAS **000**, 1–18 (2026)

4 _A. Sierra et al._


∆RA [au]
75 0 _−_ 75


75


0


_−_ 75





10







40


30


20



20


15


10



0





1 _._ 0


0 _._ 5


0 _._ 0







8


6


4


2


8


6


4


2


|200 0 −200 ∆RA [au] 1.5|Col2|
|---|---|
|12CO Mom0<br>12CO Peak<br>nuum<br>O Mom0<br>O Mom0<br>_−_200<br>0<br>200<br>13CO Mom0<br>13CO Peak<br>0_._0<br>0_._5<br>1_._0<br>1_._5<br>mJy beam_−_1<br>0<br>100<br>200<br>300<br>mJy beam_−_1 km s_−_1<br><br>10<br>20<br>30<br>40<br>mJy beam_−_1 km s_−_1||
|12CO Mom0<br>12CO Peak<br>nuum<br>O Mom0<br>O Mom0<br>_−_200<br>0<br>200<br>13CO Mom0<br>13CO Peak<br>0_._0<br>0_._5<br>1_._0<br>1_._5<br>mJy beam_−_1<br>0<br>100<br>200<br>300<br>mJy beam_−_1 km s_−_1<br><br>10<br>20<br>30<br>40<br>mJy beam_−_1 km s_−_1||


|12COv0|Col2|
|---|---|
|13CO v0||



0 50 100 150 200

Radius [au]


**Figure 1.** ALMA Band 7 ( _𝜆_ = 0 _._ 87 mm) observations of the disc around J16120. First row: Dust continuum map (left), Moment 0 (middle-left), peak intensity
(middle-right), and Gaussian velocity map (right) map of the [12] CO emission. Second row: Normalised brightness profiles computed from the integrated Moment
0 maps (left), Moment 0 (middle-left), peak intensity (middle-right), and Gaussian velocity map (right) map of the [13] CO emission. The vertical dashed lines in
the left panel show the _𝑅_ 90 radius of each tracer.



tensity traces a combination of gas surface density and temperature
(at lower vertical heights compared to [12] CO).
The circumplanetary disc (CPD) candidate observed in Band 6
( _𝜆_ = 1 _._ 3 mm) by Sierra et al. (2024a) in the centre of the gap is
not observed in the Band 7 ( _𝜆_ = 0 _._ 87 mm) data. Both observations
have a sensitivity of 0.021 mJy beam [−][1] (or ∼ 20 mK). This CPD
candidate was also not recovered in the deeper observations in Band
6 by Li et al. (2025). In Sierra et al. (2024a), the recovery fraction
(the fraction of point sources that are recovered from injection test)
of such CPD candidate in the disc gap is only ∼ 0 _._ 2. Consequently,
the evidence for dust continuum compact emission at the centre of
the gap in J16120 is unlikely to be robust and may be associated
to an imaging artifact or thermal noise. Estimations on the Band 7
detectability based on the expected spectral index are discussed in
Section 4.1.1.

The line-of-sight velocity exhibits the characteristic blue- and redshifted pattern of a rotating disc and is globally consistent with Keplerian motion (Section 3.3.1). The disc radii enclosing 90% and 68%
of the total flux ( _𝑅_ 90 and _𝑅_ 68, respectively), and fluxes of each tracer
are reported in Table 2. These values were derived using the emission
curve of growth (COG), and omitting emission at radii greater than
4 [′′] from the disc centre to avoid contamination from a millimetre

dust continuum background source (Appendix A). Although there is
not gas emission associated to the background source, we also omit
the emission beyond 4 [′′] for the gas tracers. This choice does not
affect the measured radii, as it is at least a factor of 3 larger than the
measured CO radii.
Both the dust continuum and [12] CO radii are consistent (within
the error bars and taking into account the beam difference) with the
values reported in Agurto-Gangas et al. (2025) at ALMA Band 6.
The [12] CO and [13] CO radii are approximately 1 _._ 9 and 1 _._ 5 times larger
than the dust-continuum radii, respectively, implying that this source
is not affected by efficient radial drift (Facchini et al. 2017; Trapman
et al. 2019; Toci et al. 2021; Pinilla et al. 2025). The morphology of
the dust continuum and line emission are studied in Sections 3.2 and

3.3 respectively.


MNRAS **000**, 1–18 (2026)



**3.2** **Dust continuum emission morphology**


The dust continuum map of J16120 presents two clear bright spots
along the semi-major axis of the disc. This may arise from disc
azimuthal asymmetries or from an optically thin and geometrically
thick disc (Doi & Kataoka 2021). Additionally, the disc is known
to exhibit significant azimuthal asymmetries that appear to follow a
_𝑚_ = 1 spiral arm structure (Sierra et al. 2024a). Therefore, to explore both scenarios, we study the dust continuum morphology in
the visibility plane, assuming both an axisymmetric disc (Section
3.2.1) and an eccentric disc (Section 3.2.2). In the former, we use
frankenstein (Jennings et al. 2020), which assumes and axisymmetric disc, and in the latter we use Galario (Tazzari et al. 2018) to
explore the free parameters that describe the eccentric disc morphology. In both cases, the continuum visibilities were extracted from the
self-calibrated measurement sets using the function _export_uvtable_
in Tazzari (2017), but normalising the uv-distances with the wavelength of each spectral windows and channel.
Before modelling the visibilities, we compute constraints to the
disc geometry by minimizing the spread of the real part of the visibilities (Isella et al. 2019) in both Band 6 and 7. We obtained an inclination of inc=36 _._ 9 [+] − [0] 0 _[.]_ _._ [7] 1 [deg, and a position angle of PA=45] _[.]_ [0] [+] − [0] 0 _[.]_ _._ [7] 2 [deg]
in Band 7, and inc=37 _._ 0 [+] − [0] 0 _[.]_ _._ [1] 2 [deg, PA=45] _[.]_ [1] [+] − [0] 0 _[.]_ _._ [2] 9 [deg in Band 6. These]
values are identical. From here on out, we use the inclination and
position angle inferred from the optically thinner Band 6 as the geometric constraints.


_3.2.1_ _Axisymmetric dust disc_


The Frankenstein visibility modelling of the self-calibrated dust
continuum visibilities of the disc around J16120 at ALMA Band

6 ( _𝜆_ = 1 _._ 3 mm) and 7 ( _𝜆_ = 0 _._ 87 mm) are shown in the left panel
of Figure 2. In both cases, the disc centres were computed by minimizing the imaginary part of the visibilities, obtaining an offset
in Right Ascension and Declination of (ΔRA, ΔDec) = (−27 _._ 1 [+] − [2] 0 _[.]_ _._ [4] 1
mas, −22 _._ 3 [+] − [0] 0 _[.]_ _._ [4] 1 [mas) for Band 7, and (][−][11] _[.]_ [6] [+] − [0] 0 _[.]_ _._ [8] 6 [mas,][ −][1] _[.]_ [6] [+] − [0] 0 _[.]_ _._ [9] 4 [mas)]

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 5



for Band 6. Additionally, in both cases we fit the visibilities using the hyper-parameters _𝛼_ = 1 _._ 05, and _𝑤_ smooth = 0 _._ 1. The former
guarantees that low–signal-to-noise data are incorporated into the
fit, whereas the latter represents a conservative choice that mitigates over-fitting of the visibility power spectrum. Tests with various
hyper-parameter combinations revealed no significant differences.
The middle panel of Figure 2 shows the brightness temperature radial profile obtained from the Frankenstein fit, without assuming
the Rayleigh-Jeans approximation. Two bright rings at 23 and 75 au
(B23, B75, respectively) are independently inferred in both wavelengths in addition to the inner bright disc, and two gaps at 14 and 39
au (D14, D39, respectively). The D39 dust gap also coincides with a
gas gap partially observed in [12] CO, and fully observed in [13] CO. The
B23 ring was already reported in the visibility modelling of Li et al.
(2025).


The right panel in Figure 2 presents the radial spectral index profile
between the two wavelengths, revealing local minima associated with
the bright rings and local maxima located in the gaps. The spectral
index in the innermost region ( _<_ 5 au) is below 2, suggesting very
optically thick emission and important scattering effects (Zhu et al.
2019; Sierra & Lizano 2020) or free-free contamination (Rota et al.
2024), although the latter is not expected to contribute significantly
at ALMA Band 6 and 7 wavelengths. Outside this region, the spectral index is above 3, except around B75, where it is ∼ 2 _._ 3. In the
region around the D39 gap, where the disc emission in both Band 7
and Band 6 is on the order of the thermal noise, the spectral index
reaches unphysical high values (∼ 7). All these values are subject
to uncertainties in the flux calibration, which can vertically shift the
spectral index radial profile by ∼ 0 _._ 5.


We also use the multi-wavelength modelling described in Sierra
et al. (2024b) to study the distribution of solids (such as maximum
grain size, temperature, and dust surface density, e.g., CarrascoGonzález et al. 2019; Macías et al. 2021; Sierra et al. 2021; Viscardi
et al. 2025), and we find that the posterior probabilities of both the
maximum grain size and the dust surface density tend to peak values
at the locations of the bright rings, suggesting the presence of dust
traps in B23 and B75. The spectral index also shows local minima
at the same locations, which is also indicative of dust growth in
pressure bumps or dust traps (e.g., Pinilla et al. 2012). However,
as discussed in Viscardi et al. (2025), using only two millimetre
wavelengths is insufficient to constrain the dust properties due to
significant degeneracies. At least one additional independent dust
continuum observation at a different wavelength is therefore required
to confirm these trends. Moreover, in Section 3.3.1, we suggest that
the gas around B23 may be flowing from the outer disc towards this
orbit, further supporting the dust trap scenario.


The left panel of Figure 3 shows the map of the residual visibilities
(Data - Frankestein fit). This map shows a positive residual structure
in the Eastern region of the ring, and a negative residual in the
West, similar to the residual map at Band 6 in Sierra et al. (2024a);
Vioque et al. (2025); Li et al. (2025). In the former, a spiral function
was fitted to the positive residuals. This possible spiral spatially
coincides with the positive residuals observed in Band 7 (green lines),
suggesting that this apparent spiral is not an artifact (e.g., by errors
in the disc geometry or offset, Andrews et al. 2021), but a real nonaxisymmetric structure. In the next section we show that some of this
non-axisymmetric structure can also be described by a non-eccentric
disc.



where _𝑟, 𝜙_ are the radial and azimuthal coordinates measured relative
to the disc centre and the disc minor axis in the North-West, respectively, _𝑒_ is the disc eccentricity, and _𝜔_ is the periastron. We use the
Python library emcee introduced in Foreman-Mackey et al. (2013)
to explore the posterior distributions of the parameters describing
the disc model, and Galario to compute their visibilities. The pixel
size and number of pixels are fixed to 10 mas and 1024, respectively.
The inclination and position angle are fixed at 37.0 deg and 45.1 deg,
respectively, to avoid degeneracies with the disc periastron.
The disc model consists of three Gaussians: _𝑔_ 0, _𝑔_ 23, _𝑔_ 75, which
mimic the ring like structure inferred from the axisymmetric disc.
The centre ( _𝑟_ _𝑖_ ), amplitude ( _𝐴_ _𝑖_ ), and width ( _𝜎_ _𝑖_ ) of each Gaussian are
free parameters of the model, in addition to the disc offset (ΔRA,
ΔDec), the eccentricity ( _𝑒_ ), and periastron ( _𝜔_ ), resulting in a total of
13 free parameters. The explored parameter space for the Gaussian
components are motivated by the results of the axisymmetric disc.
For the eccentricity, we explore values between 0 and 1, and for the
periastron between − _𝜋_ and _𝜋_ . In all cases, we adopt uniform (linear)
priors. The number of walkers is set to eight times the number of
free parameters. Convergence is assessed by inspecting the walker
chains and their autocorrelation times after 8000 steps. The bestfit parameter values (the one that minimises the chi-squared) are
summarised in Appendix B.
The residual map of the eccentric model is presented in the right
panel of Figure 3. Unlike the residuals from the axisymmetric disc
model, the eccentric model better reproduces the continuum asymmetries. We also tested models that include additional rings in the fit,
but neither the residual maps nor the chi-squared values show significant improvement. This simple eccentric three-ring model does a
better job at reproducing the disc morphology (in particular, the azimuthal asymmetries) compared to the axisymmetric disc. However,
some of the spiral-like residuals present in the axisymmetric model
remain, leaving open the possibility that a spiral is present.


**3.3** **Gas emission morphology**


Gas disc morphology is influenced by the presence of embedded
planets (Kley & Nelson 2012). The high angular resolution and sensitivity of the observations of the [12] CO (J=3–2) and [13] CO (J=3–2)
emission around J16120 motivate an investigation into the origin
of the observed gas substructures and their potential connection to
embedded planet candidates.
Selected channel maps (within 3.875 - 4.500 km s [−][1] ) are shown in
Figure 4. The [13] CO emission shows low intensity within the cavity,
consistent with the presence of a gas cavity as revealed by the moment
0 map (Figure 1). The [12] CO emission extends towards the inner disc,
with some asymmetries, or kink-like features, at an orbital radius
of ∼ 50 au. As these features lie in the vicinity of the inner planet
candidate proposed in Sierra et al. (2024a) at 32 au, they could be


MNRAS **000**, 1–18 (2026)



_3.2.2_ _Eccentric dust disc_


Motivated by the residuals obtained after subtracting an axisymmetric model, we explore in this section a more sophisticated nonaxisymmetric disc morphology. In particular, we describe the disc
morphology using an eccentric disc following the eccentric coordinates implemented in previous works (e.g., Marino et al. 2019; Booth
et al. 2021; Kurtovic et al. 2022), where the semi-major axis is given
by:



1 − _𝑒_ cos( _𝜙_ − _𝜔_ )
_𝑎_ ( _𝑟, 𝜙_ ) = _𝑟_
� 1 − _𝑒_ [2]



_,_ (1)
�

6 _A. Sierra et al._


75


50


25


0


_−_ 25


0 _._ 01 0 _._ 10 1 _._ 00

Baseline [M _λ_ ]



Flux Cal Err


0 20 40 60 80 100 120

Radius [au]



5


4


3


2


1



Band 7

Band 6



6


4


2



13 CO _,_ Mom0


0 20 40 60 80 100 120

Radius [au]



**Figure 2.** Left: Visibilities of the dust continuum emission at Band 7 ( _𝜆_ = 0 _._ 87 mm, blue) and 6 ( _𝜆_ = 0 _._ 87 mm, orange). The frankenstein models are shown
as a solid line. Middle: Brightness radial profiles obtained from visibility fit, alongside the [13] CO Moment 0 radial profile scaled for visual comparison on the
same vertical axis. Right: Spectral index between Band 7 and 6. The error bar in the bottom right corner is the Flux calibrator error assuming 10% of flux
uncertainty in each band. The vertical axis is truncated at _𝛼_ = 5, as the spectral index attains very high values in the vicinity of the deep dust continuum gap.
The dashed/dashed-dotted vertical lines in the middle and right panel indicate the position of the rings/gaps.



Eccentric model


75 0 _−_ 75

∆RA [au]



75


0


_−_ 75



axi _−_ symmetric model


75 0 _−_ 75

∆RA [au]




[SNR]


_−_ 12 _−_ 9 _−_ 6 _−_ 3 3 6 9 12


**Figure** **3.** Band 7 ( _𝜆_ = 0 _._ 87 mm) dust continuum residual map after subtracting the best-fit model from Frankenstein (left panel) and eccentric
parametric model with Galario (right panel). The green line in both panels
shows the spiral structure observed in the residual maps of the best fit model
using Band 6 data (Sierra et al. 2024a). The iso-contours show the dust con
tinuum ALMA Band 7 data at 7- _𝜎_ level.


associated with its presence. After modelling the disc kinematics, we
discuss the significance of these features in more detail in Section 4.2.
On the other hand, we identify another intensity feature resembling
a kink-like morphology in the outer disc, possibly associated with
kinematic perturbations, toward the southern side of the disc in both
molecular tracers. These structures are located between radii of ∼

125 au and ∼ 171 au (Hereafter, we refer to the associated planet
candidate as the 148 au planet candidate, corresponding to the mean
radius of these structures), far beyond the outer edge of the dust
continuum emission. In Sierra et al. (2024a), these structures were
reported to lie at a de-projected radius of ∼ 112au based on the
velocity residual map. However, the current observations show that
they extend significantly farther out.
In some channels, particularly in [13] CO, the features appear partially detached from the global disc emission and resemble the intensity signatures expected from planet-disc interactions (e.g., Izquierdo
et al. 2021) or from a gaseous circumplanetary disc (e.g., Bae et al.
2022). However, the location where these structures are observed


MNRAS **000**, 1–18 (2026)



varies significantly between channels, making these interpretations
less plausible. In Section 4.2, we discuss how these features may be
explained by projection effects arising from the front and back sides
of the disc, although they may also trace a gas gap. We also assess the
significance of these features with respect to the best-fit Keplerian
model.


_3.3.1_ _Disc kinematics_


The high sensitivity, spectral resolution, and angular resolution of
the gas observations toward J16120 make this dataset exceptionally
well suited for kinematic modelling. We use discminer (Izquierdo
et al. 2021) to fit the intensities and rotation velocities encoded in the
channel maps of the [12] CO (J=3–2) and [13] CO (J=3–2) emission from
this target.
Following Izquierdo et al. (2025), our models adopt smooth parametric prescriptions to describe the radial variations of the lineprofile properties of each tracer, including the peak intensity, line
width, and line slope. The velocity shifts of the model lines are computed assuming Keplerian motion set by the stellar mass _𝑀_ _★_, with
differential rotation as a function of height above the disc midplane.
We also include the systemic velocity of the source, _𝜐_ sys, as a free
parameter. The models further account for the projected geometrical structure of the channel maps, defined by the disc inclination _𝑖_
and position angle PA (both treated as free parameters, with bestfit values consistent with those inferred from the dust continuum

analysis; Section 3.2), as well as the emission surface height _𝑧_ ( _𝑟_ ) in
the front and back sides of the disc, independently parametrised as
exponentially tapered radial profiles (see Eq. 2).
We explore the parameter space using the MCMC ensemble sampler emcee (Foreman-Mackey et al. 2013), employing 230 walker
chains, burn-in phases of 80,000 and 30,000 steps for the [12] CO and
13 CO cubes, respectively, and an additional 10% of steps to sample
the posterior distributions. To study the presence of perturbations
in the disc, we compare the best-fit model channels with those of
the data to extract residual maps that reveal deviations from Keplerian rotation, as well as gas substructures manifested as intensity
and line-width fluctuations. Because the backside of the disc does

not contribute significantly to the observed emission (see discussion
in Izquierdo et al. 2025, or model images in Figure C1), we adopt
Gaussian profiles to estimate centroid velocity, peak intensity, and
line-width maps from both the data and the corresponding discminer
model. The best fit parameters are summarised in Appendix B.

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 7











100


80


60


40


20


50


40


30


20


10



100


0


_−_ 100


100


0


_−_ 100





















100 0 _−_ 100

|3875kms−1<br>.<br>inner<br>feature<br>1<br>outer<br>2 feature|3925kms−1<br>.<br>inner<br>feature<br>1<br>2|4000kms−1<br>.<br>1<br>outer<br>2 feature|4225kms−1<br>.<br>1<br>2|4300kms−1<br>.<br>1 au<br>125<br>au<br>171<br>2|Col6|
|---|---|---|---|---|---|
|3_._875 km s_−_1<br>outer<br>feature<br>inner<br>feature<br>1<br>2|3_._925 km s_−_1<br>inner<br>feature<br>1<br>2|4_._000 km s_−_1<br>outer<br>feature<br>1<br>2|4_._225 km s_−_1<br>1<br>2|4_._300 km s_−_1<br>125 au<br>171 au<br>1<br>2||
|_−_100<br>0<br>100<br>3_._900 km s_−_1<br>1<br>2|4_._000 km s_−_1<br>1<br>2|4_._200 km s_−_1<br>outer<br>feature<br>1<br>2|4_._250 km s_−_1<br>outer<br>feature<br>1<br>2|4_._500 km s_−_1<br>125 au<br>171 au<br>1<br>2||
|_−_100<br>0<br>100<br>3_._900 km s_−_1<br>1<br>2|4_._000 km s_−_1<br>1<br>2|4_._200 km s_−_1<br>outer<br>feature<br>1<br>2|4_._250 km s_−_1<br>outer<br>feature<br>1<br>2|4_._500 km s_−_1<br>125 au<br>171 au<br>1<br>2||
|||||||



**Figure 4.** Continuum-subtracted selected [12] CO (top panels) and [13] CO (bottom panels) channel maps showing gas features in the inner disc (blue arrows) and in
the outer disc (green arrows). The latter may arise from projection effects between the front and back sides of the disc, or a gas gap. The position of the inner
planet candidate at _𝑟_ = 32 au is marked by � **1**, while that of the outer planet candidate at _𝑟_ = 148 au is marked by � **2** . The radial range between 125 and 171 au,
where the outer feature is observed, is marked in the right panels. Colour bar in all panels starts at 1 _𝜎_ . The iso-contours show the ALMA Band 7 dust continuum

emission at 7- _𝜎_ level.


**Figure** **5.** Kinematics of the [12] CO emission around J16120. Left: Peak velocity along the line of sight. Middle: Discminer model. Right: Residual map. The
position of the inner planet candidate at _𝑟_ = 32 au is marked by � **1**, while that of the outer planet candidate at _𝑟_ = 148 au is marked by � **2** . The arrows indicate
the location of elongated residual substructures.



Selected channel maps of the disc model and residuals are shown
in Figure C1. The results for the velocity along the line of sight for
12 CO are shown in Figure 5, and in Figure C2 for 13 CO. In both
tracers, the disc model successfully reproduces the overall rotation
pattern of the system.


The channel residual maps (bottom panels of Figure C1) show that
the intensity residuals around the outer kink-like feature are generally
not significant. Although a few residual structures remain (e.g., [13] CO
at 4.500 km s [−][1], where the peak residual reaches 20.6 mJy beam [−][1],
corresponding to an SNR of ∼5), in most channels, including those
around the kink-like features, the residuals render these features con


sistent with the measured image noise. Similar substructures have
been reported in the channel maps of Elias 2-27 (Paneque-Carreño
et al. 2021), where they were not interpreted as deviations from
Keplerian rotation. Instead, that study attributed the emission to projection effects from the upper and lower disc surfaces, connected by
material bridging the midplane between the two sides, although they
could also have been associated with gravitational instability.

On the other hand, the [12] CO velocity residuals (right panel of Figure 5) reveal two elongated substructures extending toward the inner
and outer regions of the disc, closely overlapping with the locations
of the planet candidates proposed by Sierra et al. (2024a). No com

MNRAS **000**, 1–18 (2026)

8 _A. Sierra et al._


parable structures are observed in the [13] CO residuals; however, the
lower sensitivity of this line makes it harder to assess the presence or
absence of signatures associated with the proposed planet candidates.
Figure 6 shows the de-projected residual maps of the velocity along
the line of sight (left panel), line width (middle panel), and peak
intensity (right panel). The position of the inner planet candidate
suggested from ALMA Band 6 dust continuum emission (32 au,
Sierra et al. 2024a) lies in the transition between a blue and red
residual, similar to the spiral wakes pattern expected from a planet
embedded in the disc (e.g., Perez et al. 2015; Pérez et al. 2018). A
strong positive residual is also observed in the vicinity of the planet
candidate, at ∼ 50 au, coinciding with the location where kink-like
features were identified in the individual channel maps (Figure 4).
Additionally, positive line width residuals ∼ 0 _._ 14 km s [−][1], more than
five times the spectral resolution) are detected at the location of
the inner planet candidate and at other positions along the same
orbital radius (i.e. a ring of high velocity dispersion), similar to
the expected line width residuals observed in the simulations in
Dong et al. (2019) for an embedded planet. However, there is no
any particular localized peak intensity residual (e.g., tracing local
heating) in the same location.
The second planet candidate proposed from the kink-like features
in the outer disc (originally suggested in Sierra et al. 2024a) also
lies in a region exhibiting a transition between sub-Keplerian and
super-Keplerian velocities, together with positive line width residuals. However, unlike the inner planet candidate, the velocity residual
pattern does not resemble that expected from a spiral wake, and the
positive line width residuals do not span a broad azimuthal extent
along the planet candidate’s orbit.
Figure 7 presents the radial profiles of the gas velocity components,
the observed and modelled line widths, and the corresponding linewidth residuals derived from the [12] CO discminer modelling.
In the region between B23 and D39, the gas rotates at superKeplerian velocities and their central values exhibits a radially inward flow (although the error bars are significative), while the line
width simultaneously departs from the model, resulting in significant
residuals. The distance between B23 and D39 is approximately one
beam size; therefore, local variations within this resolution element
should be interpreted with caution. We discuss these gas structures
in further detail in Section 4.2.


_3.3.2_ _Emission surface_


It is well established that different molecules trace different vertical

heights (e.g., Law et al. 2021a), with optically thinner molecules
probing regions closer to the disc midplane. Owing to the moderate
inclination of J16120 (37.0 deg), we can study the vertical emission
surface of the detected CO lines (e.g., Pinte et al. 2018) using the nonparametric package disksurf, and compare it with the parametrised
emission surface derived from the discminer modelling.
Left panel of Figure 8 shows the vertical emission profile for the
12 CO (J=3–2) in this work, and 12 CO (J=2–1) in Sierra et al. (2024a).
These profiles were computed by masking the data with a SNR _<_ 3,
fixing disc geometry and offset to the values in Section 3.2, and
binning the profiles by a quarter of the beam size.
The emission surface of the J=3–2 transition is located at higher
altitudes than that of the J=2–1 transition by a factor of 1.3. This offset
may reflect differences in optical depth, although previous studies
have suggested that different transitions of the same isotopologue
often trace comparable emission heights (e.g., Paneque-Carreño et al.
2025; Rosotti et al. 2025). Around the innermost planet candidate,
we find that the vertical emission surface of [12] CO (J=3–2) appears


MNRAS **000**, 1–18 (2026)



nearly flat and uniform between B23 and D39, although no significant
changes are expected within this radial extent, which is comparable
in size to the beam.

The middle panel of Figure 8 shows a comparison between the disc
surfaces derived with disksurf and discminer for [12] CO (J=3–2). We
fit the disksurf data points using the same tapered power-law model
adopted in discminer, given by



_𝑞_ taper
_,_ (2)
� �



_𝑟_
_𝑧_ ( _𝑟_ ) = _𝑧_ 0
� 100au



_𝜓_ _𝑟_
exp −
� � � _𝑟_ taper



where _𝑧_ 0 is a characteristic height, _𝜓_ is the power-law exponent, _𝑟_ taper
is the characteristic radius, and _𝑞_ taper is the power-law of the tapered
function. The best fit values are reported in Appendix B for [12] CO
(J=3–2). The fit for [13] CO using disksurf shows strong degeneracies
due to the low signal-to-noise ratio (SNR); therefore, we do not
report it. Although the best-fit values obtained from discminer and
disksurf do not perfectly match, the combination of each set of
parameters predicts an emission height that is consistent within the
error bars. The emission surfaces only diverge beyond ∼ 120 au,
where the geometric methodology implemented in disksurf tends
to underestimate the emission surface in sub-Keplerian discs, as is
the case for J16120 (see the left panel of Figure 7). In contrast,
discminer appears to be less sensitive to these sub-Keplerian flows
(see Appendix A of Galloway-Sprietsma et al. 2025).
The average elevation of the [12] CO emission surface is computed
following Galloway-Sprietsma et al. (2025), where it is estimated by
taking the mean of the binned surface profile interior to the radius
where the peak surface height is found (i.e. 120 au for J16120). The
resulting average elevation is _𝑧_ / _𝑟_ = 0 _._ 15 ± 0 _._ 07, which is consistent
with the mean value reported for discs in the Upper Scorpius starforming region (Zallio et al. 2025), but lower than the typical values
found for bright and more extended discs ( _𝑧_ / _𝑟>_ 0 _._ 3, e.g., Law et al.
2021a; Paneque-Carreño et al. 2023, 2025; Galloway-Sprietsma et al.
2025).
The middle panel in Figure 8 also shows the isothermal scale height
_𝐻_ g, which is estimated via _𝐻_ g = _𝑐_ _𝑠_ /Ω K, where _𝑐_ _𝑠_ = ~~√~~ _𝑘_ _𝐵_ _𝑇_ / _𝜇𝑚_ _𝐻_ is

the sound speed computed from the gas temperature _𝑇_, the StephanBoltzmann constant _𝑘_ _𝐵_, the mean molecular weight _𝜇_ = 2 _._ 3, and the
Hydrogen mass _𝑚_ _𝐻_ . Ω K is the Keplerian angular velocity for a 0.7
_𝑀_ ⊙ star (Sierra et al. 2024a, and this work). The gas temperature is
estimated by assuming that the [12] CO emission is optically thick, and
using the azimuthally averaged [12] CO (J=3–2) brightness temperature
profile along the front surface (right panel of Figure 8).


_3.3.3_ _Gas mass_


Gas constitutes the primary mass reservoir in protoplanetary discs.
Massive discs may undergo gravitational instability (GI), which can
give rise to disc substructures (e.g., Speedie et al. 2024). Therefore,
constraining the gas mass of J16120 is important to assess whether GI
could be responsible for its observed morphology. However, measuring the gas mass is non-trivial and typically requires chemical modelling of optically thin CO isotopologues or less abundant molecular
tracers (Miotello et al. 2014, 2016), or indirect estimates based on
the dust mass. Uncertainties in the dust-to-gas mass ratio and in the
relative abundances of different gas species with respect to H 2 make
these methodologies subject to significant systematic uncertainties.
Recently, a combination of CO isotopologues and diazenylium
(N 2 H [+] ) has demonstrated to be a good tracer of the total gas mass
(Anderson et al. 2019, 2022; Trapman et al. 2022), and it was used
in the AGE-PRO large program (including J16120, Zhang et al.
2025) to derive the disc gas masses (Trapman et al. 2025). The

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 9


**Figure** **6.** De-projected residual maps after subtracting the best fit discminer model. Left: disc velocity residuals. Middle: line width residuals. Right: peak
intensity residuals. The position of the inner planet candidate at _𝑟_ = 32 au is marked by � **1**, while that of the outer planet candidate at _𝑟_ = 148 au is marked by

� **2** . A strong positive residual, coinciding with the features observed in the individual channel maps at ∼ 50 au, is highlighted in the left panel. Note that, in this
figure, the north direction is oriented toward the bottom-right. The radial range within one beam width of the disc centre is masked in grey.



1 _._ 0


0 _._ 5



0 _._ 2


0 _._ 1


0 _._ 0


_−_ 0 _._ 1


_−_ 0 _._ 2



0 _._ 2


0 _._ 1







0 _._ 0


_−_ 0 _._ 1



_−_ 0 _._ 2


|Col1|Planet candidate|orbit<br>∆vφ<br>vz<br>vr|
|---|---|---|
|B23|D39<br>B75||


|Col1|Col2|Col3|Col4|
|---|---|---|---|
|B23|D39|B75|B75|





20 40 60 80 100 120 140 160 180

Radius [au]



20 40 60 80 100 120 140 160 180

Radius [au]



**Figure 7.** Left panel: Gas velocity along the vertical ( _𝑣_ _𝑧_ ) and radial ( _𝑣_ _𝑅_ ) axes, and the azimuthal velocity difference with respect to the azimuthal rotation model
(Δ _𝑣_ _𝜙_ ). Middle panel: Azimuthally averaged line width from the data and model. Right panel: Azimuthally averaged line width residuals. The dashed/dasheddotted vertical lines indicate the position of the rings/gaps. The dotted vertical line in the left panel indicate the radial position of the planet candidate at 32 au.







30


20







10











20 40 60 80 100 120 140 160

Radius [au]



20 40 60 80 100 120 140 160

Radius [au]



20 40 60 80 100 120 140 160

Radius [au]



**Figure** **8.** Left: Emission surfaces from CO isotopologue tracers and transitions. Middle: [12] CO (J=3–2) discminer emission surface (solid line), disksurf
emission surface (dashed line), and isothermal scale height (dots). The inclined dashed lines indicate disc aspect ratios of 0.1, 0.2, and 0.3. Right: Radial profile
of the azimuthally averaged [12] CO (J=3–2) brightness temperature along the front surface. The vertical dashed and dashed-dotted line in all panels indicate the
position of the bright and dark dust continuum rings, respectively.


MNRAS **000**, 1–18 (2026)

10 _A. Sierra et al._


**Table 3.** Gas mass estimation for J16120


Methodology Gas mass (×10 [−][3] M ⊙ ) Reference


CO isotopologues + N 2 H [+] 3 _._ 2 [+] − [1] 0 _[.]_ _._ [3] 7 1
Dust mass ×100 2 _._ 6 [+] − [0] 1 _[.]_ _._ [2] 7 1,2
CO emitting height 0 _._ 25 [+] − [0] 0 _[.]_ _._ [60] 18 This work [∗]


1: Trapman et al. (2025), 2: Sierra et al. (2024a). [∗] Following the
methodology in Paneque-Carreño et al. (2025) and a Carbon depletion of 10.


gas mass constrain for J16120 in the AGE-PRO collaboration is
3 _._ 24 [+] − [1] 0 _[.]_ _._ [33] 72 [×][10] [−][3] _[𝑀]_ [⊙] [, similarly to the gas mass estimated from scaling]
the dust mass by a typical factor of 100 (their error bars overlap).
By modelling and comparing the obtained gas mass with the observed CO lines, Trapman et al. (2025) determined that the relative
abundance of CO with respect to H 2 for J16120 is log 10 _𝑥_ CO =
−4 _._ 82 [+] − [0] 0 _[.]_ _._ [11] 18 [,] [giving] [a] [CO] [depletion] [factor] [of] [∼] [10] [compared] [to] [the]
ISM value of log _𝑥_ CO ≈−4.
Because we only detect CO lines in Band 7, we adopt the methodology of Paneque-Carreño et al. (2025), who demonstrated how CO
depletion and the vertical location of CO emitting surfaces can be
used to estimate the total disc gas mass. As mentioned above, we
obtain an average aspect ratio of _𝑧_ / _𝑟_ = 0 _._ 15 ± 0 _._ 07 within _𝑟<_ 120
au (where the [12] CO emission surface peaks). Therefore, assuming a
Carbon depletion of 10 (as constrained from Trapman et al. 2025),
and using the scale height-disc mass relations from Paneque-Carreño
et al. (2025), extended to the lower-mass disc regime by PanequeCarreño (in prep.), for a stellar mass of M _★_ = 0.6, we estimate a gas
mass of M gas = 0 _._ 25 [+] − [0] 0 _[.]_ _._ [60] 18 [×][ 10] [−][3] [M] [⊙] [.]
Note that J16120 has a higher stellar mass than the model uses.
The scale height – disc mass relationship is sensitive to stellar mass
changes, with higher stellar masses yielding higher estimated disc
mass values for the same aspect ratio and carbon depletion conditions, therefore our inferred disc mass from the height analysis is a
lower boundary of the system, in agreement to previous constraints.
Additionally, the models are full gas disc models (no substructures),
however our system has a clear inner cavity, which will affect the
thermal structure and inferred heights when calculating the aspect
ratio from the full radial extent.

Nevertheless, the gas disc mass estimated from different methodologies is smaller than the dynamical mass of the central star by a
factor of ∼200–2000, confirming that the disc is gravitationally stable
and the observed disc morphologies are not driven by gravitational
instabilities. All values and their corresponding methodologies are
summarised in Table 3.

Finally, we note that the emission surface shown in Figure 8 only
rises beyond ∼D39. At smaller radii, the emission surface remains
relatively flat and close to the midplane. When computing the aspect
ratio relative to the radius at which the surface begins to rise ( _𝑟_ =
39au), we obtain _𝑧_ /( _𝑟_ − 39 au) = 0 _._ 32 ± 0 _._ 10, which is approximately
a factor of two higher than the aspect ratio measured relative to the
central star, and significantly change the estimated disc gas mass to
4 _._ 2 [+] − [11] 3 _._ 4 _[.]_ [9] [×][10] [−][3] [ M] [⊙] [. However, althoughthroughout thiswork we adopt]
the scale height–disc mass relation using the aspect ratio measured
relative to the central star, it remains unclear how the dust and gas
surface density distributions, such as the dust rings and gaps observed
in J16120, affect the disc emission surface and, consequently, the
inferred disc gas mass. This effect could be explored in future work
using coupled gas and dust models in order to quantify their impact
on the vertical disc structure and the inferred gas masses (see the
example on IM Lup in Deng et al. 2025).


MNRAS **000**, 1–18 (2026)



**4** **DISCUSSION**


The morphology of the J16120 disc provides an opportunity to investigate the possible role of planet–disc interactions in shaping its
observed substructures. The dust continuum emission fits well within

the evolutionary sequence of planet-induced morphologies proposed
by Cieza et al. (2021); Orcajo et al. (2025), showing strong similarities to the fiducial stage V model. This interpretation is further
supported by the relatively older age of J16120 compared to the other
systems in the sequence. We therefore discuss below the main dust
and gas features of the disc, with particular attention to structures
that may be associated with embedded planet candidates.


**4.1** **Planet Signatures in the Dust Emission?**


_4.1.1_ _No ALMA Band 7 CPD Detection_


A compact dust-continuum point source was reported in the ALMA
Band 6 observations by Sierra et al. (2024a). This point source was
detected with an SNR of 3 _𝜎_ (63 _𝜇_ Jy), at a de-projected distance of
32 au from the central star and at a position angle of ∼ 170 deg.
The point source is not detected in the Band 7 dust-continuum observations presented in this work. Instead, diffuse continuum emission
is observed within the gap (see comparison in Figure 9). The rms
measured in a emission free region far from the disc in Bands 7 is
21 _𝜇_ Jy beam [−][1] (Section 2). However, pixel intensities within the gap
are typically correlated (Andrews et al. 2021), increasing the rms
within the gap [2] to _𝜎_ gap = 98 _𝜇_ Jy beam [−][1] . Therefore, we can rule
out Band 7 ( _𝜆_ = 0 _._ 87 mm) point sources within the gap with a SNR
_>_ 3 _𝜎_ gap ∼ 300 _𝜇_ Jy.
The flux observed in ALMA Band 6 in Sierra et al. (2024a) is
63 _𝜇_ Jy. Therefore, assuming an optimistic optically thin spectral index of 3, the expected flux in Band 7 is ∼ 200 _𝜇_ Jy, which lies below
3 _𝜎_ gap, making detection difficult. For reference, the flux of the CPD
around PDS 70c in Band 7 is 86 ± 16 _𝜇_ Jy (Benisty et al. 2021), which
would also not be detectable at SNR _>_ 3 given our current rms noise
level, _𝜎_ gap . Recently, the CPD around WISPIT2 b, which lies within
a deep disc gap where the emission is negligible and the pixels are
therefore not strongly correlated, was not detected either (Facchini
et al. 2026). In that work, the authors ruled out point-like emission
at the location of the planet with a flux density greater than 45 _𝜇_ Jy at
the 3 _𝜎_ level. These results highlight the difficulty of detecting CPDs
at millimetre wavelengths.
The point source in the gap of J16120 was not detected in the
Band 6 dust continuum observations at higher resolution in Li et al.
(2025) either (rms of 10 _𝜇_ Jy beam [−][1] ). However, in that work, H _𝛼_
point sources were detected with a SNR ≳ 5 within the gap, at a deprojected distance of ∼ 23 _._ 5 au, and a position angle of ∼ 159 deg,
close to the point source detected in K band at 22 _._ 7 ± 2 _._ 3 au with
SPHERE/IRDIS (Ginski et al. 2025), and around the Band 6 dust
continuum point source in Sierra et al. (2024a), as shown in Figure
9. Their positions are still consistent within the beam size of 20.6 au.
However, Li et al. (2025) demonstrated that the position of the H _𝛼_
point source align with the position of the point source detected in K
when considering the orbital motion and the time difference between
observations.

Nevertheless, in this work we find a faint dust-continuum ring
at 23 au, which coincides with the de-projected radius where the
H _𝛼_ emission is observed. Therefore, it is not clear how such a planet


2 This rms is computed by measuring the brightness standard deviation in a
region within the disc gap.

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 11



















**Figure 9.** Central dust continuum emission from the J16120 disc observed in
Band 7 (left; this work) and Band 6 (right; Sierra et al. 2024a). Contours are
shown at 6, 9, 12, and 15 _𝜎_ for the Band 7 image, and at 3, 6, 9, and 12 _𝜎_
for the Band 6 image. The × and + markers are the location of the H _𝛼_ and
K-band point sources in Li et al. (2025) and Ginski et al. (2025), respectively.
The beam sizes are shown in the bottom-left corner of each panel.


could reside on the same orbit as a dust continuum ring mainly tracing
millimetre dust grains. There is no significant asymmetric feature in
the B23 ring (Figure 1), nor a significant local intensity drop in the
region around the H _𝛼_ position. However, we cannot rule out that this
ring could be associated with dust trapped in the horseshoe orbit of
the planet candidate (Ataiee et al. 2013; Ragusa et al. 2017). Deeper
observations would be required to confirm or rule out this hypothesis.
Although less plausible, another possible explanation for the nondetection of a point source in the gap of J16120 in Band 7 is variability. The recent non-detection of the circumplanetary disc around
PDS 70c in ALMA Band 9 (Domínguez-Jamett et al. 2025) suggests
that its millimetre emission may originate from free-free emission of
ionised gas shocked at the CPD surface, rather than from dust, and
is therefore expected to be variable at sub-millimetre wavelengths.
However, free–free emission from ionised gas is expected to be subdominant at ALMA Band 7, where the continuum is typically dominated by thermal dust emission. While limited sensitivity is likely
the dominant factor behind the non-detection, the possibility that a
CPD is not present cannot be ruled out.


_4.1.2_ _Eccentricity as a Signature of an Embedded Planet_


The dust continuum morphology of J16120 is better described by
an eccentric disc (Section 3.2). The best fit value for the disc eccentricity is significant ( _𝑒_ = 95 [+] − [4] 3 [×][ 10] [−][3] [), and may be associated with]
several physical processes. For example, gravitational instability (GI)
may trigger non-axisymmetric structures and eccentric modes (Papaloizou & Savonije 1991; Laughlin et al. 1997; Rice et al. 2003).
However, massive discs ( _𝑀_ disc / _𝑀_ _★_ _>_ 0 _._ 1) are needed for GI to act,
which is not the case of J16120, as shown in Section 3.3.3. Stellar
companions may also drive eccentricity in the central cavity, having a higher impact on the millimetre dust continuum morphology
compared to that onto the gas (Ragusa et al. 2017), and shaping the
millimetre surface brightness maps (Lynch & Lovell 2022; Lovell
& Lynch 2023). However, using Gaia measurements, Vioque et al.
(2026) found no evidence that the astrometry of J16120 is consistent
with a stellar companion within ∼0.1–10 au, although spectroscopic
binaries could still be present at separations below 0.1 au. Likewise,
a stellar companion at separations out to ∼10 au would likely have
been detected in near-IR or optical images.
Shadows, created by a warped or misalignment inner disc, can also
trigger eccentricity, due to the azimuthally varying heating, which



create asymmetric pressure forces, and spiral or eccentric variation
can emerge (e.g., Montesinos et al. 2016; Su & Bai 2024), like in
the disc around HD 142527 (Casassus et al. 2015; Marino et al.
2015). We test this hypothesis by constraining changes in the disc
inclination as a function of radius using the [12] CO residual velocity
map (Appendix D). We found that the highest inclination difference
is ∼ 4 deg. This difference is smaller than the [12] CO gas opening angle
estimated from the emission surface or the isothermal scale height
in Section 3.3.2, _𝐻_ / _𝑟>_ 0 _._ 1 (or ∼ 5 _._ 7 deg). Therefore, the inner disc
(which is found to be highly optically thick due to its low spectral
index, Figure 2) is not expected to produce effective shadowing or
a strong pressure gradient across the outer disc or ring, and is thus
unlikely to drive significant eccentricity.
Eccentric substructures can also be induced by non-axisymmetric
mechanisms, such as flybys (e.g., Clarke & Pringle 1993; Cuello
et al. 2019), or the Rossby Wave Instability (e.g., Pierens & Lin
2018). However, there is currently no evidence for either in J16120.
As such, the leading explanation for the observed eccentricity is
the presence of a planet embedded within the disc dust-gap. Several works (e.g., Kley & Dirksen 2006; Ataiee et al. 2013; Pinilla
et al. 2015; Teyssandier & Ogilvie 2017; Ragusa et al. 2018) have
demonstrated that a planet to star mass ratios larger than 3 × 10 [−][3]

can lead to eccentricity growth in the disc. For J16120, with a central star of 0 _._ 7 M ⊙ star, the planet candidate should have a mass
M p ≳ 700 M ⊕ = 2 _._ 2 M Jup, consistent with the 4 M Jup planet mass
constrained from the SPHERE band K and H _𝛼_ emission (Li et al.
2025).
Recent studies have shown that disc eccentricity is expected to
decrease rapidly beyond the planet orbit (Padgett & Fung 2026). In
the case of J16120, the eccentricity may therefore be largely confined
to the inner disc and the B23 ring, both of which lie within the orbit of
the 32 au planet candidate. This scenario would also explain why the
eccentricity does not strongly affect the large-scale disc kinematics
(e.g., as those observed in MWC 758 Izquierdo et al. 2026b), where
eccentric discs are expected to produce elongated structures (Ragusa
et al. 2024).


**4.2** **Signatures of a Planet in the Gas Emission**


A large diversity of gas substructures is observed and inferred in
J16120. The channel maps of [12] CO and [13] CO (Figure 4) show a
kink like structure in the South of the disc, in a de-projected orbit
between ∼ 125 and 171 au, and over a large range of velocities (from
∼ 3.7 to 4.5 km s [−][1] ), indicating possible extended deviations from
Keplerian motion rather than localised substructures. Additionally,
the azimuthal position of the feature is not the same through different
channel maps, but it moves following approximately the same orbit,
which is between the de-projected _𝑅_ 90 radius of [12] CO and [13] CO.
Similar features are also observed in some channel maps on the
opposite side of the disc (towards the north), which could suggest the
presence of a gas gap. However, we do not detect a clear gap at these
radii in either the moment 0 or peak intensity maps, nor in the radial
profiles shown in Figure 1. Consequently, we consider the gas-gap
interpretation as the origin of the features to be inconclusive.
Similar structures have been also observed in other discs around

the outer border of the disc (e.g., Paneque-Carreño et al. 2021),
where it has been interpreted as projected emission from the upper and lower side of the disc, which is connected by gas around the
disc midplane. An inspection of the Keplerian discminer model (top
panels of Figure C1) shows that the combined front- and backside
emission can reproduce these structures, resulting in negligible residuals (top-middle panels of Figure C1). Therefore, the superposition


MNRAS **000**, 1–18 (2026)

12 _A. Sierra et al._


of front- and backside emission mimics the kink-like structures ob
served in the outer disc, confirming previous interpretations of these
substructures and suggesting that the gas features detected beyond
the dust continuum emission in this work and by Sierra et al. (2024a)
may not have a planetary origin.
On the other hand, the inner planet candidate at 32 au presents new
interesting evidence that suggest a planetary origin. The discminer
residuals maps in Figure 6 around the inner planet candidate presents
1) a localised velocity residual similar to a Doppler flip, and 2) a localised positive line width residual at the location of the planet and
along its orbit. Additionally, the [12] CO channel maps in the region
around 50 au (just exterior to the inner planet’s orbit) exhibit asymmetries that resemble kink-like features, and the gas kinematics also
suggests radially inward flow towards the disc cavity. All these properties may suggest a planetary origin and are individually discussed
below.


_4.2.1_ _Planet Kinematic Signatures in the Velocity Residual Map_


The localized velocity residual around the inner planet candidate
is associated with a spiral wake-like structure, which changes from
sub-Keplerian to super-Keplerian velocities across the location of the
planet candidate. This pattern may be associated with a Doppler flip
caused by the presence of a planet (e.g., Casassus & Pérez 2019),
supporting the hypothesis of a planet at this location, or changes in
the disc geometry (e.g., Calcino et al. 2024).
We also observe kink-like features at ∼ 50 au (Figure 4), exterior
to the planet’s orbit at 32 au. The velocity residuals in the moment
maps (left panel of Figure 6) reveal a localised positive residual at

∼
50 au. This residual lies within one beam of the planet candidate’s
orbit and may be related to the kinematic signatures expected from
the planet.
As mentioned above, some of the large-scale residual velocities
may also be associated to changes in the disc geometry, and in particular to a warped disc, as recently shown for the exo-ALMA discs
(Teague et al. 2025; Winter et al. 2025). We use the methodology
and tools in Winter et al. (2025) to study the velocity residual maps
in our work, and look for radial variations of the disc inclination and
position angle. The results (shown in Appendix D) show a maximum
inclination variation of ∼ 4 deg, and a maximum PA variation of
∼ 3 deg, a bit lower than the variation for MWC 758 (Winter et al.
2025). The best-fitting model reproduces most of the observed residuals at _𝑟<_ 60 au, and the positive residuals on the western side of the
disc (left panel of Figure D). However, it fails in reproducing the positive localised velocity residual in the vicinity of the planet candidate
at ∼ 50 au (marked with an arrow in Figure D), as revealed by the
Residual map (top-right panel in Figure D). The origin of the latter
remains uncertain. However, as it lies in the outer vicinity of previously identified tracers suggesting the presence of a planet candidate,
it may likewise be induced by the same planetary companion.
At the location of the outer planet candidate, the velocity residuals
also transition from sub- to super-Keplerian velocities. However,
unlike the inner planet candidate, they are not connected to a spiral
wake-like structure, making this outer feature less compelling as
evidence for a planet, while its origin remains uncertain.


_4.2.2_ _Line width residuals revealing an embedded planet_


The line-width residual map in the middle panel of Figure 6 shows
distinct substructures. The positive residuals near the inner planet
candidate and along its orbit resemble the signatures predicted by


MNRAS **000**, 1–18 (2026)



the hydrodynamic simulations of Dong et al. (2019), where a planet
is embedded in a protoplanetary disc in a circular orbit of 30 au
and around a 1 _𝑀_ ⊙ star, similar to the position of the proposed
inner planet (∼32 au) and stellar parameters of J16120. The origin
of the enhanced line width at the planet’s orbit in their simulations is
increased velocity dispersion due to planet-induced turbulence.
The azimutally-averaged line width radial profile of J16120 deviates from the model by ∼ 0 _._ 05 km s [−][1] (6%) at D39 (Figure 7). Such
a deviation is much smaller than the line-width broadening expected
for a 4 _𝑀_ Jup planet, and slightly smaller than the 10% non-thermal
velocity dispersion predicted for a 1 _𝑀_ Jup planet in the simulations of
Dong et al. (2019), which assume a fixed disc viscosity of _𝛼_ = 10 [−][3]

and a vertically isothermal disc structure. This suggests that, if the
enhanced line broadening observed in J16120 is produced solely by
an embedded planet, and the disc parameters of J16120 are similar
to those in Dong et al. (2019), the mass of the planet is likely constrained to ∼ 1 _𝑀_ Jup . However, it is important to note that spatial
smearing can artificially reduce the observed velocity dispersion, as
demonstrated by Izquierdo et al. (2026b), implying that the inferred
planet mass may be underestimated and that the estimated value of
1 _𝑀_ Jup should therefore be regarded as an approximation to lower
limit mass.

On the other hand, positive line width residuals are also present
at the location of the outer planet candidate. However, the positive
residual structure along this orbit extends over only ∼ 70 deg in azimuth and is weaker than that observed for the inner planet candidate,
making these features insufficiently robust to be considered reliable
signatures of an embedded planet.
Figure 10 shows the line profile at different disc locations. Positions
A, B, and C lie at the same orbital radius as D39. At position A and
C, where the line width residuals presents an excess, the full-widthhalf-maxima (FWHM) is 2.178 and 2.364 km s [−][1], respectively. These
values are a factor of 1.5 and 1.6 larger than the FWHM at B, where
the line width is narrower than the average value in the same orbit.
The line widths at position D and E (same orbital radius as B75)
show similar FWHM of ∼ 0 _._ 8 km s [−][1], as also expected from the
line width model [3] (middle panel of Figure 7). At position F (far from
the disc centre ∼ 155 au), the FWHM decreases to 0.472 km s [−][1] .
No double peak is observed in the spectra at the locations where the
line width is enhanced, possibly due to the difficulty to distinguish
between the front side and back side of the disc at 39 au.

The similarity of the line width residuals in J16120 compared
with the simulations in Dong et al. (2019) is landmark observational
case to date. The coincidence of the line width residuals with previously reported planet-formation signatures from different tracers
(Sierra et al. 2024a; Ginski et al. 2025; Li et al. 2025) around the
same region is suggestive of a forming planet in this orbit. However, a
comprehensive understanding of the line width enhancement requires
exploring the role of additional physical processes beyond a planetary origin. Future studies combining multi-line observations (e.g.,
SO tracing local planet heating), improved thermochemical modelling, and self-consistent MHD simulations will be key to isolating
the specific contribution of an embedded planet from other mechanisms that may also contribute to line broadening. For example, the
simulations in Barraza-Alfaro et al. (2025) clearly identify and separate the effects of the vertical shear instability, the magnetorotational
instability, and the gravitational instability in the localised kinematic
signatures observed in the exoALMA Large Program (Teague et al.


3 Note that the line width from the discminer model is parametrised using
the half width of the profile at half power.

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 13



|F .W 45H M 0=<br>33 km s−1 1 5 ± .0<br>B<br>)|F .W 36H M 0=<br>27 km s−1 2 4 ± .0<br>C|39kms−1|D F<br>C<br>A B E<br>Line Width Residuals|
|---|---|---|---|
|12 km s_−_1<br>FWHM =<br>0_._862_ ±_ 0_._0<br>E|12 km s_−_1<br>FWHM =<br>0_._472_ ±_ 0_._0<br>F|15 km s_−_1|15 km s_−_1|
|4<br>6<br>8<br>_−_2<br>0<br>2<br>4<br>6<br>8<br>_−_2<br>0<br>2|4<br>6<br>8<br>_−_2<br>0<br>2<br>4<br>6<br>8<br>_−_2<br>0<br>2|4<br>6<br>8<br>100<br>0<br>_−_100|4<br>6<br>8<br>100<br>0<br>_−_100|


Velocity [km s _[−]_ [1] ]



Velocity [km s _[−]_ [1] ]







100


0


_−_ 100





1 _._ 0


0 _._ 5


0 _._ 0



FWHM =
2 _._ 178 _±_ 0 _._ 033 km s _[−]_ [1]


A

(inner planet)


FWHM =
0 _._ 879 _±_ 0 _._ 012 km s _[−]_ [1]


D


_−_ 2 0 2 4 6 8

Velocity [km s _[−]_ [1] ]



∆RA [au]





**Figure 10.** [12] CO line profiles extracted at selected pixel locations; the corresponding coordinates are over-plotted on the line width residual map on the right.
The dashed ellipses indicate the position of the B23, B75 rings, while the dashed-dotted are the D14, D39 rings. The Full-Width-Half-Maxima of each line
profile is reported in the top-left corner of each panel. Pixel A is located at the position of the inner planet candidate at 32 au.


2025). A similar effort is required to disentangle their respective
contributions to line-width enhancement.

0 _._ 01


_4.2.3_ _Hints of Gas Flow Towards the Planet’s Orbit_



Gas kinematics can also be used to search for evidence of planet
formation in gas-rich protoplanetary discs. For example, the presence
of forming planets may trigger meridional flows (e.g., Morbidelli
et al. 2014) that transport material from the disc midplane—where the
dynamics are dominated by planetary torques—to the disc surface,
which is dominated by viscous torques (e.g., Dong et al. 2019; Kley
et al. 2001). Radially, gas in the midplane is driven away from the
planet’s orbit by Lindblad torques (e.g., Masset 2002), while in the
disc surface layers it moves toward the orbit due to the pressure drop
induced by the planet. For optically thick line emission, the observed
kinematics predominantly trace the disc surface, where the gas is
therefore expected to flow toward the planet’s orbit.
In the specific case of J16120, the left panel of Figure 7 shows a
trend towards negative radial velocities ( _𝑣_ _𝑟_ ) beginning at B75 and
reaching a minimum at 32 au, corresponding to the location of the
inner planet candidate. Interior to the planet’s orbit, we have only a
single radial measurement, limiting our ability to constrain the radial
velocity in that region. Note that the velocity uncertainties remain
significant for _𝑟<_ 75 au and are also consistent with zero, so these
measurements should be interpreted with particular care. In the outer
disc (beyond B75), the radial velocity is flat and around zero.
On the other hand, the gas is super-Keplerian inside 120 au (Δ _𝑣_ _𝜙_ _>_
0), including the vicinity of the inner planet candidate. The radial
gradient of Δ _𝑣_ _𝜙_ becomes negative around B75, reaching a local
minimum at approximately the same location, as shown in Figure 11.
Co-spatiality between millimetre rings and pressure maxima has been
observed in many discs (Rosotti et al. 2020; Izquierdo et al. 2023;
Stadler et al. 2025). This behaviour is indicative of dust trapping and
was previously suggested for J16120 based on Band 6 observations
(Sierra et al. 2024a).
Finally, the vertical velocity ( _𝑣_ _𝑧_ ) tends toward positive values



0 _._ 00


_−_ 0 _._ 01

|B23 D39 B75|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|D39<br>B23<br>B75||||||||||
|||||||||||
||B23|D39|D39|B75|B75|B75|B75|B75|B75|
|||||||||||
|||||||||||



20 40 60 80 100 120 140 160 180

Radius [au]


**Figure 11.** Derivative of the azimuthal velocity deviation relative to the Keplerian disc. The vertical dashed and dashed-dotted line indicate the position
of the bright and dark dust continuum rings, respectively.


around the planet candidate’s orbit; however, the associated uncertainties and limited angular resolution make it difficult to draw firm
conclusions about the presence of meridional flows in this region,
such as those observed in HD 163296 (Teague et al. 2019).


**5** **A PLANET EMBEDDED IN THE J16120 DISC?**


Multiple lines of evidence for a forming planet have been reported
within the gap of J16120, including a CPD candidate identified in
ALMA Band 6 observations (Sierra et al. 2024a), point sources detected in the H and K bands with SPHERE (Ginski et al. 2025), H _𝛼_
emission (Li et al. 2025), line-width enhancements tracing increased
velocity dispersion around the planet candidate and along its orbit,
as well as a suggestive Doppler flip and gas flow directed towards
the planet’s orbit (this work). Although the exact radial locations of


MNRAS **000**, 1–18 (2026)

14 _A. Sierra et al._


these tracers differ, they remain consistent within the observational
uncertainties, as shown in Figure 12. Moreover, some of the apparent
offsets may arise from orbital motion. For example, Li et al. (2025)
showed that the positional offset between the K-band and H _𝛼_ detections can be explained by the orbital motion of the planet candidate
over the time elapsed between the observations.
In Figure 12, we also include the radial extent of the gas gap
observed in the current [13] CO data, as well as a second, as-yet undetected planet candidate proposed by Li et al. (2025) at an orbital
radius of ∼ 37 au based on the gap size and the massive accreting
gap-planet model of Close (2020). Interestingly, this orbital radius
coincides with the location of the D39 gap reported in this work.
Such an additional planet candidate could also play a significant role
in shaping the disc eccentricity (e.g., Lee & Peale 2002), such as the
eccentric structure described in Section 3.2.2.

Future observations will be crucial for testing the planet formation
scenario in J16120. In particular, VLTI/GRAVITY+ spectroscopy,
infrared observations with the James Webb Space Telescope, millimetre observations targeting gas tracers of planet formation, and
new high-resolution ALMA data will provide complementary constraints on the nature of the proposed planet candidate. These observations will help to characterise the circumplanetary environment, probe ongoing accretion processes, and search for additional
kinematic and structural signatures of planet–disc interactions. Ultimately, these data will help determine whether the observed substructures can be robustly attributed to ongoing planet formation within
the gap of J16120.


**6** **CONCLUSIONS**


We present new ALMA Band 7 observations of the disc around
J16120, revealing additional evidence for planet formation associated with a candidate embedded within the dust-disc gap. These
results provide further support for the presence of a planetary companion previously suggested by millimetre (Sierra et al. 2024a), infrared (Ginski et al. 2025), and H _𝛼_ observations (Li et al. 2025). We
summarise our main findings below:


 - The detected dust continuum, [12] CO (J=3–2), [13] CO (J=3–2)
emission reveal a bright disc and a ring-like structure peaking at
75 au, consistent with morphologies previously observed at millimetre and infrared wavelengths. The Band 6 and Band 7 dust continuum
data also reveal a faint ring at 23 au and gaps at 14 and 39 au. The
spectral index between the two bands exhibits local maxima at the
gap locations (D14 and D39) and local minima at the rings (B23
and B75), suggesting the presence of dust traps. This interpretation
is further supported by local minima in the radial derivative of the
azimuthal gas velocity, which are also indicative of dust trapping. No
ALMA Band 7 ( _𝜆_ = 0 _._ 87 mm) point sources are detected within the
disc gap at a SNR > 3 _𝜎_ gap ∼ 300 _𝜇_ Jy.

 - The residual map of the Band 7 ( _𝜆_ = 0 _._ 87 mm) dust continuum
emission, obtained after subtracting the azimuthally averaged profile,
shows positive residuals that align with the _𝑚_ = 1 spiral structure also
observed in Band 6 ( _𝜆_ = 1 _._ 3 mm). However, most of these features
disappear when the dust continuum morphology is modelled with
an eccentric disc rather than an axisymmetric disc. The best-fitting
eccentric disc model yields an eccentricity of _𝑒_ = 95 [+] − [4] 3 [×][ 10] [−][3] [, and]
we suggests that its origin may be associated with the presence of a
planetary-mass companion (with a mass of ≳ 2 _._ 2 M Jup ) embedded
within the disc gap, consistent with previous constraints obtained
from SPHERE band K and H _𝛼_ emission.


MNRAS **000**, 1–18 (2026)




 - The gas mass of J16120, estimated from the [12] CO emission surface following the methodology in Paneque-Carreño et al. (2025), is
0 _._ 25 [+] − [0] 0 _[.]_ _._ [60] 18 [×][ 10] [−][3] _[ 𝑀]_ [⊙] [. This is value is lower than previous estimates]
based on CO isotopologue and N 2 H [+] observations (Trapman et al.
2025); however, it should be interpreted as a lower limit on the disc
gas mass. For all estimated gas masses, the disc is insufficiently massive to become gravitationally unstable and account for the observed
disc substructures.

 - After subtracting a non-eccentric Keplerian model, the [12] CO
velocity residual map reveals spiral wake-like structures that appear
to originate from a region near the location of the inner planet candidate at 32 au. This planet candidate lies at the transition between
sub-Keplerian and super-Keplerian rotation, resembling the Doppler
flip expected from an embedded planet.

 - The residual map of the [12] CO line width shows a prominent
positive residual (amplitude of ∼ 0 _._ 14 km s [−][1] ) at the location of
the planet candidate at 32 au, as well as similar positive residuals
along the same orbit. These features are consistent with the expected
signatures of an embedded planet (Dong et al. 2019), which enhances
the local velocity dispersion along its orbit. This suggests that a
planetary companion may be responsible for the observed line-width
broadening in J16120. Based on the simulations of Dong et al. (2019)
and accounting for the spatial smearing of the observations (Izquierdo
et al. 2026b), the planet mass is constrained to be ≳ 1 _𝑀_ Jup .

 - Hints of gas flowing toward the orbital radius of the planet candidate are inferred from the disc kinematics, although the associated
error bars remain significant. Such a flow is nevertheless expected
from the pressure minima within a gap carved by an embedded planet.
Similarly, the vertical gas velocity appears to suggest a flow from the
disc midplane toward the upper disc layers at the location of the
planet candidate. However, these interpretations should be treated
with caution, as the uncertainties associated with the velocity component remain substantial, preventing robust conclusions from being
drawn.


 - We did not detect any robust signatures of an outer planet beyond
the dust continuum emission. However, we confirm the presence of
a feature that resembles a kink-like structure (previously reported in
Band 6 by Sierra et al. 2024a), located at an orbital radius between
125 and 171 au. Given its large azimuthal extent, its proximity to
the outer edge of the gas disc, and the fact that gas disc modelling
indicates consistency with Keplerian motion (residuals below 5 _𝜎_ ),
we suggest that this feature is unlikely to be of planetary origin and
may instead be associated with projected emission from the upper
and lower surfaces of the disc.


The dust continuum eccentricity, localised velocity structures, enhanced line widths, and disc kinematics provide new and compelling
evidence for a planetary companion at an orbital radius of ∼32 au
in J16120. Together with previous hints of planet formation, these
findings make J16120 one of the strongest candidates for hosting an
embedded protoplanet, alongside the confirmed planetary systems
PDS 70 and WISPIT 2. Future observations at shorter and longer
millimetre wavelengths, in both dust continuum and molecular lines,
particularly those sensitive to local planet-induced heating like SO,
SiS, HCN, or C 2 H (Law et al. 2023; Izquierdo et al. 2026a), will
be essential to confirm these findings and to further characterise the
planet embedded within the gap of J16120.


**ACKNOWLEDGMENTS**


This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2023.1.01100.S ALMA is a partnership of ESO

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 15

### Hints of planets in J16120



(1)


(2)


(3)


(4)


(1)


(4)



Line width enhacement

Dusty CPD candidate

Point Source

Point Source

Gas Gap


2nd Planet candidate _∗_




|D14 ontinuum|B23|Col3|Col4|Col5|Col6|)|Col8|
|---|---|---|---|---|---|---|---|
|D14<br>ontinuum|<br>B23|<br>B23||ALMA (Band 7|ALMA (Band 7|ALMA (Band 7|ALMA (Band 7|
|D14<br>ontinuum|<br>B23|<br>B23||ALMA (Band 6)|ALMA (Band 6)|||
|D14<br>ontinuum|<br>B23|<br>B23||ALMA (<br>H_α_<br>K_ −_Band<br>D39|_ −_Band|_ −_Band|_ −_Band|
|D14<br>ontinuum|<br>B23|<br>B23||ALMA (<br>H_α_<br>K_ −_Band<br>D39|ALMA (|Band 7)|Band 7)|
|D14<br>ontinuum|<br>B23|<br>B23||ALMA (<br>H_α_<br>K_ −_Band<br>D39|ALMA (|||
|||||||||



10 20 30 40 50

Radius [au]


**Figure 12.** Summary of the different signatures of planet formation within the gap of J16120. The background profile shows the radial dust continuum emission
observed in Band 7 (this work). The vertical lines indicate the position of rings (B) and gaps (D). References: (1) This work, (2) Sierra et al. (2024a), (3) Ginski
et al. (2025), (4) Li et al. (2025). *: Second, as-yet undetected, planet candidate proposed by Li et al. (2025).



(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ. The National Radio Astronomy Observatory is a facility of
the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research was supported in
part by grant NSF PHY-2309135 to the Kavli Institute for Theoretical
Physics (KITP).
A.S. acknowledges support from UNAM DGAPA-PAPIIT grant
IG101224. A.S. and P.P. acknowledge funding from the UK Research and Innovation (UKRI) under the UK government’s Horizon
Europe funding guarantee from ERC (under grant agreement No
101076489). T.P.-C. acknowledges support from the Michigan Society of Fellows and has received funding by the Heising-Simons
foundation through the 51 Pegasi B Fellowship. L.P. acknowledges
support from ANID BASAL project FB210003 and ANID FONDECYT Regular 1262272. C.A.G. acknowledges support from Comité
Mixto ESO-Gobierno de Chile 2023, under grant 072-2023. A.R. has
received funding from the Royal Society through a University Research Fellowship grant number URF\R1\241791. L.A.C. acknowledges support from the Millennium Nucleus on Young Exoplanets
and their Moons (YEMS), NCN2024_001, Chile and FONDECYT
Regular grant 1241056. S.F. acknowledges financial contributions
from the European Union (ERC, UNVEIL, 101076613) and from
PRIN-MUR 2022YP5ACE. Views and opinions expressed are however those of the authors only and do not necessarily reflect those of
the European Union or the European Research Council. Neither the
European Union nor the granting authority can be held responsible
for them. C.F.M. is Funded by the European Union (ERC, WANDA,
101039452). Views and opinions expressed are however those of the
author(s) only and do not necessarily reflect those of the European
Union or the European Research Council Executive Agency. Neither
the European Union nor the granting authority can be held responsible for them. J.M. acknowledges support from ANID – Millennium
Science Initiative Program – Center Code NCN2024_001. G.R. acknowledges support from the European Union (ERC Starting Grant
DiscEvol, project number 101039651) and from Fondazione Cariplo,
grant No. 2022-1217. Views and opinions expressed are, however,
those of the author(s) only and do not necessarily reflect those of
the European Union or the European Research Council. Neither the



European Union nor the granting authority can be held responsible
for them.


**SOFTWARE**


This work made use of the following software: Astropy (Astropy
Collaboration et al. 2018), CASA (McMullin et al. 2007), Discminer (Izquierdo et al. 2021), Emcee (Foreman-Mackey et al.
2013), Frankenstein (Jennings et al. 2020), Matplotlib (Hunter
2007), Numpy (Harris et al. 2020).


**DATA AVAILABILITY**


The self-calibrated data underlying this article will be available at
[zenodo.org.](https://zenodo.org/) The non-calibrated data is publicly available at [alma-](https://almascience.nrao.edu/aq/)
[science.nrao.edu/aq using the project code 2023.1.01100.S.](https://almascience.nrao.edu/aq/)


**REFERENCES**


[Agurto-Gangas C., et al., 2025, ApJ, 989, 4](http://dx.doi.org/10.3847/1538-4357/adc7ab)
[Anania R., et al., 2025, ApJ, 989, 8](http://dx.doi.org/10.3847/1538-4357/adb587)
Anderson D. E., Blake G. A., Bergin E. A., Zhang K., Carpenter J. M.,
[Schwarz K. R., Huang J., Öberg K. I., 2019, ApJ, 881, 127](http://dx.doi.org/10.3847/1538-4357/ab2cb5)
Anderson D. E., Cleeves L. I., Blake G. A., Bergin E. A., Zhang K., Carpenter
[J. M., Schwarz K. R., 2022, ApJ, 927, 229](http://dx.doi.org/10.3847/1538-4357/ac517e)
[Andrews S. M., 2020, ARA&A, 58, 483](http://dx.doi.org/10.1146/annurev-astro-031220-010302)
[Andrews S. M., et al., 2018, ApJ, 869, L41](http://dx.doi.org/10.3847/2041-8213/aaf741)
[Andrews S. M., et al., 2021, ApJ, 916, 51](http://dx.doi.org/10.3847/1538-4357/ac00b9)
[Ansdell M., et al., 2016, ApJ, 828, 46](http://dx.doi.org/10.3847/0004-637X/828/1/46)
[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
Ataiee S., Pinilla P., Zsom A., Dullemond C. P., Dominik C., Ghanbari J.,

[2013, A&A, 553, L3](http://dx.doi.org/10.1051/0004-6361/201321125)
[Bae J., et al., 2022, ApJ, 934, L20](http://dx.doi.org/10.3847/2041-8213/ac7fa3)
Bae J., Isella A., Zhu Z., Martin R., Okuzumi S., Suriano S., 2023, in Inutsuka
S., Aikawa Y., Muto T., Tomida K., Tamura M., eds, Astronomical Society
of the Pacific Conference Series Vol. 534, Protostars and Planets VII.
p. 423 ( `[arXiv:2210.13314](http://arxiv.org/abs/2210.13314)` [), doi:10.48550/arXiv.2210.13314](http://dx.doi.org/10.48550/arXiv.2210.13314)
[Barraza-Alfaro M., et al., 2025, ApJ, 984, L21](http://dx.doi.org/10.3847/2041-8213/adc42d)
[Beckwith S. V. W., Sargent A. I., Chini R. S., Guesten R., 1990, AJ, 99, 924](http://dx.doi.org/10.1086/115385)
[Benisty M., et al., 2021, ApJ, 916, L2](http://dx.doi.org/10.3847/2041-8213/ac0f83)


MNRAS **000**, 1–18 (2026)

16 _A. Sierra et al._


Benisty M., et al., 2023, in Inutsuka S., Aikawa Y., Muto T., Tomida K.,
Tamura M., eds, Astronomical Society of the Pacific Conference Series Vol. 534, Protostars and Planets VII. p. 605 ( `[arXiv:2203.09991](http://arxiv.org/abs/2203.09991)` ),
[doi:10.48550/arXiv.2203.09991](http://dx.doi.org/10.48550/arXiv.2203.09991)

Booth M., Schulz M., Krivov A. V., Marino S., Pearce T. D., Launhardt R.,

[2021, MNRAS, 500, 1604](http://dx.doi.org/10.1093/mnras/staa3362)

[Calcino J., et al., 2024, MNRAS, 534, 2904](http://dx.doi.org/10.1093/mnras/stae2233)
Carpenter J. M., Esplin T. L., Luhman K. L., Mamajek E. E., Andrews S. M.,
[2025, ApJ, 978, 117](http://dx.doi.org/10.3847/1538-4357/ad8ebc)
[Carrasco-González C., et al., 2019, ApJ, 883, 71](http://dx.doi.org/10.3847/1538-4357/ab3d33)
[Casassus S., Pérez S., 2019, ApJ, 883, L41](http://dx.doi.org/10.3847/2041-8213/ab4425)
[Casassus S., et al., 2015, ApJ, 812, 126](http://dx.doi.org/10.1088/0004-637X/812/2/126)
[Cieza L. A., et al., 2019, MNRAS, 482, 698](http://dx.doi.org/10.1093/mnras/sty2653)

[Cieza L. A., et al., 2021, MNRAS, 501, 2934](http://dx.doi.org/10.1093/mnras/staa3787)
[Clarke C. J., Pringle J. E., 1993, MNRAS, 261, 190](http://dx.doi.org/10.1093/mnras/261.1.190)
[Close L. M., 2020, AJ, 160, 221](http://dx.doi.org/10.3847/1538-3881/abb375)
[Close L. M., et al., 2025, ApJ, 990, L9](http://dx.doi.org/10.3847/2041-8213/adf7a5)
[Cuello N., et al., 2019, MNRAS, 483, 4114](http://dx.doi.org/10.1093/mnras/sty3325)
Currie T., Cloutier R., Brittain S., Grady C., Burrows A., Muto T., Kenyon
[S. J., Kuchner M. J., 2015, ApJ, 814, L27](http://dx.doi.org/10.1088/2041-8205/814/2/L27)
[Currie T., et al., 2022, Nature Astronomy, 6, 751](http://dx.doi.org/10.1038/s41550-022-01634-x)
[Czekala I., et al., 2021, ApJS, 257, 2](http://dx.doi.org/10.3847/1538-4365/ac1430)
[Deng D., Gorti U., Pascucci I., Ruaud M., 2025, ApJ, 995, 98](http://dx.doi.org/10.3847/1538-4357/ae0e66)
[Dent W. R. F., et al., 2013, PASP, 125, 477](http://dx.doi.org/10.1086/670826)
[Doi K., Kataoka A., 2021, ApJ, 912, 164](http://dx.doi.org/10.3847/1538-4357/abe5a6)
[Domínguez-Jamett O., et al., 2025, A&A, 702, A18](http://dx.doi.org/10.1051/0004-6361/202554485)
[Dong R., Liu S.-Y., Fung J., 2019, ApJ, 870, 72](http://dx.doi.org/10.3847/1538-4357/aaf38e)
[Facchini S., Birnstiel T., Bruderer S., van Dishoeck E. F., 2017, A&A, 605,](http://dx.doi.org/10.1051/0004-6361/201630329)

[A16](https://ui.adsabs.harvard.edu/abs/2017A&A...605A..16F)

Facchini S., Curone P., Benisty M., Zagaria F., Teague R., Cugno G., Bae J.,
[2026, ApJ, 998, L16](http://dx.doi.org/10.3847/2041-8213/ae3c0a)
Fang M., Pascucci I., Edwards S., Gorti U., Hillenbrand L. A., Carpenter
[J. M., 2023, ApJ, 945, 112](http://dx.doi.org/10.3847/1538-4357/acb2c9)
[Foreman-Mackey D., Hogg D. W., Lang D., Goodman J., 2013, PASP, 125,](http://dx.doi.org/10.1086/670067)
[306](https://ui.adsabs.harvard.edu/abs/2013PASP..125..306F)

[Gaia Collaboration et al., 2023, A&A, 674, A1](http://dx.doi.org/10.1051/0004-6361/202243940)
[Galloway-Sprietsma M., et al., 2025, ApJ, 984, L10](http://dx.doi.org/10.3847/2041-8213/adc437)
[Garufi A., et al., 2024, A&A, 685, A53](http://dx.doi.org/10.1051/0004-6361/202347586)

[Ginski C., et al., 2024, A&A, 685, A52](http://dx.doi.org/10.1051/0004-6361/202244005)

[Ginski C., et al., 2025, A&A, 699, A237](http://dx.doi.org/10.1051/0004-6361/202451647)
[Goldreich P., Ward W. R., 1973, ApJ, 183, 1051](http://dx.doi.org/10.1086/152291)
Guerra-Alvarado O. M., van der Marel N., Williams J. P., Pinilla P., Mulders

[G. D., Lambrechts M., Sanchez M., 2025, A&A, 696, A232](http://dx.doi.org/10.1051/0004-6361/202453338)

Haffert S. Y., Bohn A. J., de Boer J., Snellen I. A. G., Brinchmann J., Girard
[J. H., Keller C. U., Bacon R., 2019, Nature Astronomy, 3, 749](http://dx.doi.org/10.1038/s41550-019-0780-5)
Hammond I., Christiaens V., Price D. J., Toci C., Pinte C., Juillard S., Garg
[H., 2023, MNRAS, 522, L51](http://dx.doi.org/10.1093/mnrasl/slad027)

[Harris C. R., et al., 2020, Nature, 585, 357](http://dx.doi.org/10.1038/s41586-020-2649-2)
[Hilder T., et al., 2025, ApJ, 984, L13](http://dx.doi.org/10.3847/2041-8213/adc435)
[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
Isella A., Benisty M., Teague R., Bae J., Keppler M., Facchini S., Pérez L.,
[2019, ApJ, 879, L25](http://dx.doi.org/10.3847/2041-8213/ab2a12)
Izquierdo A. F., Testi L., Facchini S., Rosotti G. P., van Dishoeck E. F., 2021,

[A&A, 650, A179](http://dx.doi.org/10.1051/0004-6361/202140779)
Izquierdo A. F., Facchini S., Rosotti G. P., van Dishoeck E. F., Testi L., 2022,

[ApJ, 928, 2](http://dx.doi.org/10.3847/1538-4357/ac474d)
Izquierdo A. F., Testi L., Facchini S., Rosotti G. P., van Dishoeck E. F., Wölfer
[L., Paneque-Carreño T., 2023, A&A, 674, A113](http://dx.doi.org/10.1051/0004-6361/202245425)
[Izquierdo A. F., et al., 2025, ApJ, 984, L8](http://dx.doi.org/10.3847/2041-8213/adc439)
[Izquierdo A. F., et al., 2026a, arXiv e-prints, p. arXiv:2601.10631](http://dx.doi.org/10.48550/arXiv.2601.10631)
[Izquierdo A. F., et al., 2026b, ApJ, 1000, L13](http://dx.doi.org/10.3847/2041-8213/ae48fd)
Jennings J., Booth R. A., Tazzari M., Rosotti G. P., Clarke C. J., 2020,

[MNRAS, 495, 3209](http://dx.doi.org/10.1093/mnras/staa1365)

[Jorsater S., van Moorsel G. A., 1995, AJ, 110, 2037](http://dx.doi.org/10.1086/117668)
[Keppler M., et al., 2018, A&A, 617, A44](http://dx.doi.org/10.1051/0004-6361/201832957)
[Kley W., Dirksen G., 2006, A&A, 447, 369](http://dx.doi.org/10.1051/0004-6361:20053914)
[Kley W., Nelson R. P., 2012, ARA&A, 50, 211](http://dx.doi.org/10.1146/annurev-astro-081811-125523)
[Kley W., D’Angelo G., Henning T., 2001, ApJ, 547, 457](http://dx.doi.org/10.1086/318345)


MNRAS **000**, 1–18 (2026)



[Kurtovic N. T., et al., 2022, A&A, 664, A151](http://dx.doi.org/10.1051/0004-6361/202243505)
[Laughlin G., Korchagin V., Adams F. C., 1997, ApJ, 477, 410](http://dx.doi.org/10.1086/303682)
[Law C. J., et al., 2021a, ApJS, 257, 4](http://dx.doi.org/10.3847/1538-4365/ac1439)
Law C. J., et al., 2021b, ApJS, in press
[Law C. J., Booth A. S., Öberg K. I., 2023, ApJ, 952, L19](http://dx.doi.org/10.3847/2041-8213/acdfd0)
[Lee M. H., Peale S. J., 2002, ApJ, 567, 596](http://dx.doi.org/10.1086/338504)
[Li J., et al., 2025, ApJ, 990, L70](http://dx.doi.org/10.3847/2041-8213/adfcbd)
[Lissauer J. J., 1993, ARA&A, 31, 129](http://dx.doi.org/10.1146/annurev.aa.31.090193.001021)
[Liu B., Ji J., 2020, Research in Astronomy and Astrophysics, 20, 164](http://dx.doi.org/10.1088/1674-4527/20/10/164)
[Long F., et al., 2018, ApJ, 869, 17](http://dx.doi.org/10.3847/1538-4357/aae8e1)
[Lovell J. B., Lynch E. M., 2023, MNRAS, 525, L36](http://dx.doi.org/10.1093/mnrasl/slad083)
[Lynch E. M., Lovell J. B., 2022, MNRAS, 510, 2538](http://dx.doi.org/10.1093/mnras/stab3566)
Macías E., Guerra-Alvarado O., Carrasco-González C., Ribas Á., Espaillat
[C. C., Huang J., Andrews S. M., 2021, A&A, 648, A33](http://dx.doi.org/10.1051/0004-6361/202039812)
Manara C. F., Ansdell M., Rosotti G. P., Hughes A. M., Armitage P. J., Lodato
G., Williams J. P., 2023, in Inutsuka S., Aikawa Y., Muto T., Tomida
K., Tamura M., eds, Astronomical Society of the Pacific Conference
Series Vol. 534, Protostars and Planets VII. p. 539 ( `[arXiv:2203.09930](http://arxiv.org/abs/2203.09930)` ),
[doi:10.48550/arXiv.2203.09930](http://dx.doi.org/10.48550/arXiv.2203.09930)

[Marino S., Perez S., Casassus S., 2015, ApJ, 798, L44](http://dx.doi.org/10.1088/2041-8205/798/2/L44)
Marino S., Yelverton B., Booth M., Faramaz V., Kennedy G. M., Matrà L.,
[Wyatt M. C., 2019, MNRAS, 484, 1257](http://dx.doi.org/10.1093/mnras/stz049)
[Masset F. S., 2002, A&A, 387, 605](http://dx.doi.org/10.1051/0004-6361:20020240)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Miotello A., Bruderer S., van Dishoeck E. F., 2014, A&A, 572, A96](http://dx.doi.org/10.1051/0004-6361/201424712)

Miotello A., van Dishoeck E. F., Kama M., Bruderer S., 2016, [A&A,](http://dx.doi.org/10.1051/0004-6361/201628159) [594,](https://ui.adsabs.harvard.edu/abs/2016A&A...594A..85M)

[A85](https://ui.adsabs.harvard.edu/abs/2016A&A...594A..85M)

[Montesinos M., Cuello N., 2018, MNRAS, 475, L35](http://dx.doi.org/10.1093/mnrasl/sly001)

Montesinos M., Perez S., Casassus S., Marino S., Cuadra J., Christiaens V.,
[2016, ApJ, 823, L8](http://dx.doi.org/10.3847/2041-8205/823/1/L8)
Morbidelli A., Szulágyi J., Crida A., Lega E., Bitsch B., Tanigawa T., Kana[gawa K., 2014, Icarus, 232, 266](http://dx.doi.org/10.1016/j.icarus.2014.01.010)
[Müller A., et al., 2018, A&A, 617, L2](http://dx.doi.org/10.1051/0004-6361/201833584)
[Öberg K. I., et al., 2021, ApJS, 257, 1](http://dx.doi.org/10.3847/1538-4365/ac1432)
[Orcajo S., et al., 2025, ApJ, 984, L57](http://dx.doi.org/10.3847/2041-8213/adcd58)
[Padgett C., Fung J., 2026, ApJ, 1000, 65](http://dx.doi.org/10.3847/1538-4357/ae4339)
[Paneque-Carreño T., et al., 2021, ApJ, 914, 88](http://dx.doi.org/10.3847/1538-4357/abf243)
Paneque-Carreño T., Miotello A., van Dishoeck E. F., Tabone B., Izquierdo
[A. F., Facchini S., 2023, A&A, 669, A126](http://dx.doi.org/10.1051/0004-6361/202244428)
Paneque-Carreño T., Miotello A., van Dishoeck E. F., Rosotti G., Tabone B.,
[2025, A&A, 698, A231](http://dx.doi.org/10.1051/0004-6361/202451862)
[Papaloizou J. C., Savonije G. J., 1991, MNRAS, 248, 353](http://dx.doi.org/10.1093/mnras/248.3.353)
[Pascucci I., et al., 2016, ApJ, 831, 125](http://dx.doi.org/10.3847/0004-637X/831/2/125)
Perez S., Dunhill A., Casassus S., Roman P., Szulágyi J., Flores C., Marino
[S., Montesinos M., 2015, ApJ, 811, L5](http://dx.doi.org/10.1088/2041-8205/811/1/L5)
[Pérez S., Casassus S., Benítez-Llambay P., 2018, MNRAS, 480, L12](http://dx.doi.org/10.1093/mnrasl/sly109)
[Pierens A., Lin M.-K., 2018, MNRAS, 479, 4878](http://dx.doi.org/10.1093/mnras/sty1314)

Pinilla P., Birnstiel T., Ricci L., Dullemond C. P., Uribe A. L., Testi L., Natta

[A., 2012, A&A, 538, A114](http://dx.doi.org/10.1051/0004-6361/201118204)
Pinilla P., de Juan Ovelar M., Ataiee S., Benisty M., Birnstiel T., van Dishoeck
[E. F., Min M., 2015, A&A, 573, A9](http://dx.doi.org/10.1051/0004-6361/201424679)

[Pinilla P., et al., 2025, MNRAS, 543, 2723](http://dx.doi.org/10.1093/mnras/staf1624)

[Pinte C., et al., 2018, A&A, 609, A47](http://dx.doi.org/10.1051/0004-6361/201731377)

[Pinte C., et al., 2023, MNRAS, 526, L41](http://dx.doi.org/10.1093/mnrasl/slad010)
Pollack J. B., Hubickyj O., Bodenheimer P., Lissauer J. J., Podolak M.,
[Greenzweig Y., 1996, Icarus, 124, 62](http://dx.doi.org/10.1006/icar.1996.0190)
Ragusa E., Dipierro G., Lodato G., Laibe G., Price D. J., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stw2456)

[464, 1449](https://ui.adsabs.harvard.edu/abs/2017MNRAS.464.1449R)
Ragusa E., Rosotti G., Teyssandier J., Booth R., Clarke C. J., Lodato G., 2018,

[MNRAS, 474, 4460](http://dx.doi.org/10.1093/mnras/stx3094)
Ragusa E., Lynch E., Laibe G., Longarini C., Ceppi S., 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202449583) [686,](https://ui.adsabs.harvard.edu/abs/2024A&A...686A.264R)
[A264](https://ui.adsabs.harvard.edu/abs/2024A&A...686A.264R)
[Ribas Á., et al., 2025, Nature Astronomy, 9, 1176](http://dx.doi.org/10.1038/s41550-025-02576-w)
Rice W. K. M., Armitage P. J., Bate M. R., Bonnell I. A., 2003, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2003.06253.x)

[339, 1025](https://ui.adsabs.harvard.edu/abs/2003MNRAS.339.1025R)

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 17



Rosotti G. P., Teague R., Dullemond C., Booth R. A., Clarke C. J., 2020,

[MNRAS, 495, 173](http://dx.doi.org/10.1093/mnras/staa1170)
[Rosotti G. P., et al., 2025, ApJ, 984, L20](http://dx.doi.org/10.3847/2041-8213/adc42e)
Rota A. A., Meijerhof J. D., van der Marel N., Francis L., van der Tak F. F. S.,
[Sellek A. D., 2024, A&A, 684, A134](http://dx.doi.org/10.1051/0004-6361/202348387)
Sanchis E., Picogna G., Ercolano B., Testi L., Rosotti G., 2020, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa074)

[492, 3440](https://ui.adsabs.harvard.edu/abs/2020MNRAS.492.3440S)
[Sierra A., Lizano S., 2020, ApJ, 892, 136](http://dx.doi.org/10.3847/1538-4357/ab7d32)
[Sierra A., et al., 2021, ApJS, 257, 14](http://dx.doi.org/10.3847/1538-4365/ac1431)
[Sierra A., et al., 2024a, ApJ, 974, 102](http://dx.doi.org/10.3847/1538-4357/ad6e73)
[Sierra A., et al., 2024b, ApJ, 974, 306](http://dx.doi.org/10.3847/1538-4357/ad7460)
[Speedie J., et al., 2024, Nature, 633, 58](http://dx.doi.org/10.1038/s41586-024-07877-0)
[Stadler J., et al., 2025, ApJ, 984, L11](http://dx.doi.org/10.3847/2041-8213/adb152)
[Su Z., Bai X.-N., 2024, ApJ, 975, 126](http://dx.doi.org/10.3847/1538-4357/ad7581)
[Szulágyi J., Garufi A., 2021, MNRAS, 506, 73](http://dx.doi.org/10.1093/mnras/stab1723)
Szulágyi J., Plas G. v. d., Meyer M. R., Pohl A., Quanz S. P., Mayer L.,
[Daemgen S., Tamburello V., 2018, MNRAS, 473, 3573](http://dx.doi.org/10.1093/mnras/stx2602)
[Szulágyi J., Dullemond C. P., Pohl A., Quanz S. P., 2019, MNRAS, 487, 1248](http://dx.doi.org/10.1093/mnras/stz1326)
Tazzari M., 2017, mtazzari/uvplot, [doi:10.5281/zenodo.1003113,](http://dx.doi.org/10.5281/zenodo.1003113) `[https:](https://doi.org/10.5281/zenodo.1003113)`
```
  //doi.org/10.5281/zenodo.1003113
```

[Tazzari M., Beaujean F., Testi L., 2018, MNRAS, 476, 4527](http://dx.doi.org/10.1093/mnras/sty409)
[Teague R., Bae J., Bergin E. A., 2019, Nature, 574, 378](http://dx.doi.org/10.1038/s41586-019-1642-0)
[Teague R., et al., 2021, ApJS, 257, 18](http://dx.doi.org/10.3847/1538-4365/ac1438)
[Teague R., et al., 2025, ApJ, 984, L6](http://dx.doi.org/10.3847/2041-8213/adc43b)
[Teyssandier J., Ogilvie G. I., 2017, MNRAS, 467, 4577](http://dx.doi.org/10.1093/mnras/stx426)
Thanathibodee T., Calvet N., Bae J., Muzerolle J., Hernández R. F., 2019,

[ApJ, 885, 94](http://dx.doi.org/10.3847/1538-4357/ab44c1)
Toci C., Rosotti G., Lodato G., Testi L., Trapman L., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/stab2112) [507,](https://ui.adsabs.harvard.edu/abs/2021MNRAS.507..818T)

[818](https://ui.adsabs.harvard.edu/abs/2021MNRAS.507..818T)

Trapman L., Facchini S., Hogerheijde M. R., van Dishoeck E. F., Bruderer
[S., 2019, A&A, 629, A79](http://dx.doi.org/10.1051/0004-6361/201834723)
Trapman L., Zhang K., van’t Hoff M. L. R., Hogerheijde M. R., Bergin E. A.,
[2022, ApJ, 926, L2](http://dx.doi.org/10.3847/2041-8213/ac4f47)
[Trapman L., et al., 2025, ApJ, 989, 5](http://dx.doi.org/10.3847/1538-4357/adcd6e)
[Valegård P.-G., et al., 2024, A&A, 685, A54](http://dx.doi.org/10.1051/0004-6361/202347452)
[Vioque M., et al., 2025, ApJ, 989, 9](http://dx.doi.org/10.3847/1538-4357/adc7b0)
[Vioque M., et al., 2026, A&A, 705, A238](http://dx.doi.org/10.1051/0004-6361/202557086)
Viscardi E. M., Macías E., Zagaria F., Sierra A., Jiang H., Yoshida T. C.,
[Curone P., 2025, A&A, 695, A147](http://dx.doi.org/10.1051/0004-6361/202452935)

[Williams J. P., Cieza L. A., 2011, ARA&A, 49, 67](http://dx.doi.org/10.1146/annurev-astro-081710-102548)
[Winter A. J., et al., 2025, ApJ, 990, L10](http://dx.doi.org/10.3847/2041-8213/adf113)
[Zallio L., et al., 2025, arXiv e-prints, p. arXiv:2511.16734](http://dx.doi.org/10.48550/arXiv.2511.16734)
[Zhang K., et al., 2025, ApJ, 989, 1](http://dx.doi.org/10.3847/1538-4357/addebe)
[Zhu Z., et al., 2019, ApJ, 877, L18](http://dx.doi.org/10.3847/2041-8213/ab1f8c)
[van Capelleveen R. F., et al., 2025, ApJ, 990, L8](http://dx.doi.org/10.3847/2041-8213/adf721)


**APPENDIX A:** **BACKGROUND MILLIMETRE OBJECT**


We report the Band 7 ( _𝜆_ = 0 _._ 87 mm) detection of a resolved millimetre source at a projected distance of ∼ 4 _._ 4 [′′] (∼ 582 au) from the
J16120 centre (Figure A1). The dust continuum flux of this source
is 0 _._ 81 ± 0 _._ 02 mJy, and no [12] CO nor [13] CO emission is detected in
its surroundings. This source was also observed in Band 6 in Sierra
et al. (2024a), with a dust continuum flux of 0 _._ 12 ± 0 _._ 02 mJy. Therefore, its spectral index between ALMA Band 7 ( _𝜆_ = 0 _._ 87 mm) and 6
( _𝜆_ = 1 _._ 3 mm) is _𝛼_ = 4 _._ 56 ± 0 _._ 40, suggesting optically thin emission
from small dust grains. However, the steep spectral index, lack of
associated CO emission, and large projected separation also make a
background sub-millimetre galaxy the most plausible interpretation.


**APPENDIX B:** **BEST-FIT MODEL PARAMETERS**


Table B1 summarises the best-fitting parameters of the eccentric disc
model presented in Section 3.2.2. Table B2 presents the best fit model



_−_ 200


0 _._ 0


0 _−_ 200 _−_ 400 _−_ 600


∆RA [au]


**Figure A1.** Extended Band 7 dust continuum emission, within which a submillimetre source, potentially a background sub-millimetre galaxy, is de
tected. Contours indicate the ALMA Band 7 dust continuum emission at the

7- _𝜎_ level.


**Table B1.** Best fit parameters of the eccentric disc modelling.


Parameter [Units] Value


ΔRA [mas] 87 _._ 6 [+] − [2] 1 _[.]_ _._ [5] 9
ΔDec [mas] 34 _._ 6 [+] − [2] 1 _[.]_ _._ [2] 6
_𝑒_ 95 [+] − [4] 3 [×][ 10] [−][3]

_𝜔_ [deg] 120 ± 2
_𝑟_ 0 [au] 4 _._ 3 [+] − [1] 4 _[.]_ _._ [2] 3
_𝑟_ 23 [au] 22 _._ 5 [+] − [2] 4 _[.]_ _._ [5] 0
_𝑟_ 75 [au] 76 _._ 4 ± 0 _._ 1
_𝜎_ 0 [au] 1 _._ 5 [+] − [3] 0 _[.]_ _._ [1] 2
_𝜎𝜎_ 2375 [au][au] 910 _._ 2 _._ ±9 [+] − 0 [3] 2 _[.]_ _._ _._ [3] 1 1
_𝐴_ 0 [ _𝜇_ Jy/pix] 8 _._ 5 [+] − [2] 3 _[.]_ _._ [3] 3
_𝐴_ 23 [ _𝜇_ Jy/pix] 1 _._ 2 ± 0 _._ 1
_𝐴_ 75 [ _𝜇_ Jy/pix] 12 _._ 1 ± 0 _._ 1


parameters for the discminer model in both [12] CO (J=3–2) and [13] CO
(J=3–2). The parameters presented in the table corresponds to the
parametrization of the attributes as following.


 - Peak intensity: _𝐼_ _𝑝_ = _𝐼_ _𝑝_ 0 ( _𝑅_ /100au) _[𝑝]_ _[𝑝]_ ( _𝑧_ /100au) _[𝑞]_ _[𝑝]_

 - Line width: _𝐿_ _𝑤_ = _𝐿_ _𝑤_ 0 ( _𝑅_ /100au) _[𝑝]_ _[𝑤]_ ( _𝑧_ /100au) _[𝑞]_ _[𝑤]_

 - Line slope: _𝐿_ _𝑠_ = _𝐿_ _𝑠_ 0 ( _𝑅_ /100au) _[𝑝]_ _[𝑠]_

 - Upper surface: _𝑧_ _𝑈_ = _𝑧_ _𝑈_ 0 ( _𝑅_ /100au) _[𝑝]_ _[𝑈]_ exp(−( _𝑅_ / _𝑅_ _𝑈𝑡_ ) _[𝑞]_ _[𝑈]_ )

 - Lower surface: _𝑧_ _𝐿_ = _𝑧_ _𝐿_ 0 ( _𝑅_ /100au) _[𝑝]_ _[𝐿]_ exp(−( _𝑅_ / _𝑅_ _𝐿𝑡_ ) _[𝑞]_ _[𝐿]_ )


Additionally, the mass of the central star (M _★_ ), the systemic velocity
(v sys ), the disc inclination, and position angle are free parameters of
the fit. See Izquierdo et al. (2021) for more details.
Table B3 lists the best-fitting emission-surface parameters derived with discminer for [12] CO (J=3–2) and [13] CO (J=3–2), and with
disksurf for [12] CO (J=3–2), as described in Section 3.3.2. The error

bars from the discminer fit in Table B2 and B3 are derived from

the walker distributions by computing the 16th and 84th percentiles.
However, these uncertainties are likely underestimated. Using spatial correlations in the image plane, Hilder et al. (2025) showed that
accurately quantifying the true errors is not straightforward, but that
they may be up to an order of magnitude larger than those inferred
from the Bayesian analysis.


MNRAS **000**, 1–18 (2026)



1 _._ 5


1 _._ 0


0 _._ 5



100


0


_−_ 100

18 _A. Sierra et al._


**Table B2.** Best fit parameters for the discminer model.


Parameter [Units] Best-fit ( [12] CO) Best-fit ( [13] CO)


M _★_ [M ⊙ ] 0 _._ 7 ± 0 _._ 1 0 _._ 7 ± 0 _._ 1
v sys [km s [−][1] ] 4 _._ 527 ± 0 _._ 025 4 _._ 524 ± 0 _._ 025
i [deg] 38 _._ 3 [+] − [0] 0 _[.]_ _._ [1] 1 37.0*
PA [deg] 44 _._ 4 [+] − [0] 0 _[.]_ _._ [1] 1 45.1*
_𝐼_ _𝑝_ 0 [mJy pix [−][1] ] 0 _._ 37 ± 0 _._ 01 0 _._ 55 ± 0 _._ 01
_𝑝_ _𝑝_ −3 _._ 26 ± 0 _._ 01 −0 _._ 53 ± 0 _._ 06
_𝑞_ _𝑝_ 1 _._ 80 ± 0 _._ 01 1 _._ 13 ± 0 _._ 04
_𝐿_ _𝑤_ 0 [km s [−][1] ] 0 _._ 54 ± 0 _._ 01 1 _._ 45 ± 0 _._ 23
_𝑝_ _𝑤_ −1 _._ 20 ± 0 _._ 01 −0 _._ 32 ± 0 _._ 03
_𝑞_ _𝑤_ 0 _._ 28 ± 0 _._ 01 0 _._ 49 ± 0 _._ 03
_𝐿_ _𝑠_ 0 1 _._ 93 ± 0 _._ 01 1 _._ 66 ± 0 _._ 02
_𝑝_ _𝑠_ 0 _._ 35 ± 0 _._ 01 0 _._ 67 ± 0 _._ 03
_𝑧_ _𝑈_ 0 [au] 44 _._ 6 ± 0 _._ 6 25 _._ 3 ± 1 _._ 6
_𝑝_ _𝑈_ 2 _._ 8 ± 0 _._ 1 2 _._ 9 ± 0 _._ 1
_𝑞_ _𝑈_ 1 _._ 7 ± 0 _._ 1 1 _._ 4 ± 0 _._ 1
_𝑅_ _𝑈𝑡_ [au] 110 _._ 0 ± 1 _._ 0 58 _._ 2 ± 1 _._ 7
_𝑧_ _𝐿_ 0 [au] 22 _._ 1 ± 0 _._ 1 1 _._ 1 ± 0 _._ 2
_𝑝_ _𝐿_ 1 _._ 84 ± 0 _._ 01 0 _._ 28 ± 0 _._ 07
_𝑞_ _𝐿_ 1 _._ 06 ± 0 _._ 01 3 _._ 03 ± 0 _._ 80
_𝑅_ _𝐿𝑡_ [au] 228 _._ 2 ± 2 _._ 0 388 _._ 3 ± 44 _._ 5


*: The disc inclination and position angle for [13] CO were fixed to those
computed from the dust continuum (Section 3.2).


**Table B3.** Best fit parameters of the upper emission surface for the molecular

lines in this work.


Disksurf Discminer Discminer
Parameter 12 CO (J=3–2) 12 CO (J=3–2) 13 CO (J=3–2)


_𝑧_ 0 [au] 93 _._ 5 [+] − [56] 38 _[.]_ _._ [2] 4 44 _._ 6 ± 0 _._ 6 25 _._ 3 ± 1 _._ 6
_𝑟_ taper [au] 86 _._ 6 [+] − [18] 13 _[.]_ _._ [5] 8 110 _._ 0 ± 1 _._ 0 58 _._ 2 ± 1 _._ 7
_𝜓_ 4 _._ 4 ± 0 _._ 7 2 _._ 8 ± 0 _._ 1 2 _._ 9 ± 0 _._ 1
_𝑞_ taper 2 _._ 3 [+] − [0] 0 _[.]_ _._ [6] 4 1 _._ 7 ± 0 _._ 1 1 _._ 4 ± 0 _._ 1


**APPENDIX C:** **MORE ABOUT DISCMINER MODELLING**


Figure C1 shows the discminer models of the [12] CO and [13] CO emission (top panels) and the corresponding residuals (bottom panels),
displayed for the same channel maps as the data shown in Figure 4.
The substructures observed between 125 and 171 au have corre
sponding residuals within ±5 _𝜎_, making them compatible with the
Keplerian discminer model.
Figure C2 shows the kinematic model and residuals for [13] CO.
The sensitivity and angular resolution make it difficult to study the
regions around the inner and outer planet candidates.


**APPENDIX D:** **WARPED DISC**


Figure D shows the results of the velocity residual analysis using
a warped disc model, obtained with the fitting scripts described in
Winter et al. (2025). The model reproduces most of the observed
red- and blue-shifted residuals, including the spiral-like structure
associated with the inner planet candidate. The maximum difference
in the disc inclination and position angle are ∼ 4 _,_ 3 deg, respectively.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–18 (2026)

_Dust Substructures and Line Perturbations driven by a Forming Planet in J16120_ 19









100


80


60


40


20


50


40


30


20


10


5

4

3

2

_−_ 2

_−_ 3

_−_ 4

_−_ 5


5

4

3

2

_−_ 2

_−_ 3

_−_ 4

_−_ 5



100


0


_−_ 100


100


0


_−_ 100


100


0


_−_ 100


100


0


_−_ 100


|3 .875 km s−1<br>1<br>front −side<br>2<br>back −side|3 .925 km s−1<br>1<br>2|4 .000 km s−1<br>1<br>front −side<br>2<br>back −side|4 .225 km s−1<br>1<br>2|4 .300 km s−1<br>1 au<br>125 au<br>171<br>2|Col6|
|---|---|---|---|---|---|
|3_._875 km s_−_1<br>front_ −_side<br>back_ −_side<br>1<br>2|3_._925 km s_−_1<br>1<br>2|4_._000 km s_−_1<br>front_ −_side<br>back_ −_side<br>1<br>2|4_._225 km s_−_1<br>1<br>2|4_._300 km s_−_1<br>125 au<br>171 au<br>1<br>2||
|_−_100<br>0<br>100<br>3_._900 km s_−_1<br>1<br>2|4_._000 km s_−_1<br>1<br>2|4_._200 km s_−_1<br>1<br>2|4_._250 km s_−_1<br>1<br>2|4_._500 km s_−_1<br>125 au<br>171 au<br>1<br>2||
|_−_100<br>0<br>100<br>3_._900 km s_−_1<br>1<br>2|4_._000 km s_−_1<br>1<br>2|4_._200 km s_−_1<br>1<br>2|4_._250 km s_−_1<br>1<br>2|4_._500 km s_−_1<br>125 au<br>171 au<br>1<br>2||
|||||||



















100 0 _−_ 100


|3 .875 km s−1<br>1<br>2|3 .925 km s−1<br>1<br>2|4 .000 km s−1<br>1<br>2|4 .225 km s−1<br>1<br>2|4 .300 km s−1<br>1 au<br>125 au<br>171<br>2|
|---|---|---|---|---|
|_−_100<br>0<br>100<br>3_._900 km s_−_1<br>1<br>2|4_._000 km s_−_1<br>1<br>2|4_._200 km s_−_1<br>1<br>2|4_._250 km s_−_1<br>1<br>2|4_._500 km s_−_1<br>125 au<br>171 au<br>1<br>2|



100 0 _−_ 100


**Figure C1.** Model (top rows) and residual maps (bottom rows) after subtracting the best fit discminer model. The green arrows indicate the emission from the
frontside and backside of the disc in a few channel maps, which may mimic kink-like features. The position of the inner planet candidate at _𝑟_ = 32 au is marked
by � **1**, while that of the outer planet candidate at _𝑟_ = 148 au is marked by � **2** . The iso-contours show the ALMA Band 7 dust continuum emission at 7- _𝜎_ level.


**Figure C2.** Same as Figure 5 but for [13] CO.


MNRAS **000**, 1–18 (2026)

20 _A. Sierra et al._


Top panels: Observed (left), Model (middle), and Residual (right) maps of the [12] CO velocity residuals of J16120, assuming a warped disc. The arrow indicates
the location of a positive localised velocity substructure that is not reproduced by the model. Radial profiles: Changes in the disc inclination ( _𝛿_ i) and position
angle ( _𝛿_ PA), and the physical warp properties tilt _𝛽_, twist _𝛾_, and the warp amplitude _𝜓_ .


MNRAS **000**, 1–18 (2026)


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[1]",
  "value": "What are the dust substructures and gas kinematic signatures of ongoing planet formation in the protoplanetary disc around 2MASS J16120668–301027?",
  "failed_quote": "In this paper, we present new high-sensitivity, high-angular-resolution, and high-spectral-resolution Band 7 ( 𝜆 = 0 . 87,mm) observations of J16120 in dust continuum emission, 12 CO ( 𝐽 = 3–2), and 13 CO ( 𝐽 = 3–2), revealing new evidence of planet formation"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[1]",
  "value": "Representative frequency 345.80 GHz; 4 spectral windows: 330.35-332.23 GHz, 330.55-330.61 GHz, 344.05-345.93 GHz, 345.76-345.82 GHz; spectral resolution 30.52 kHz and 976.56 kHz",
  "failed_quote": "The spectral setup was configured with four spectral windows, with frequencies between 330.35 - 332.23 GHz, 330.55 - 330.61 GHz, 344.05 - 345.93 GHz, 345.76 - 345.82 GHz, and spectral resolution of 30.52 kHz and 976.56 kHz."
 },
 {
  "path": "processing.inherited[4].what.evidence[0]",
  "value": "Smooth parametric prescriptions in discminer for line-profile properties",
  "failed_quote": "Following Izquierdo et al. (2025), our models adopt smooth parametric prescriptions to describe the radial variations of the line-profile properties of each tracer, including the peak intensity, line width, and line slope."
 },
 {
  "path": "analysis_steps[5].method.evidence[2]",
  "value": "Extract 12CO (J=3-2) vertical emission surface with disksurf and fit with tapered power law; compute average elevation z/r within r < 120 au; compute isothermal scale height H_g from front-surface brightness temperature; infer gas mass from z/r and CO depletion factor using Paneque-Carreno et al. (2025) relations",
  "failed_quote": "Therefore, assuming a Carbon depletion of 10 (as constrained from Trapman et al. 2025), and using the scale height-disc mass relations from Paneque-Carreño et al. (2025), extended to the lower-mass disc regime by Paneque-Carreño (in prep.), for a stellar mass of M ★ = 0.6, we estimate a gas mass of M gas = 0 . 25 + − 0 0 . . 60 18 × 10 −3 M ⊙ ."
 },
 {
  "path": "findings_qualitative[3].evidence[0]",
  "value": "Outer kink-like features in 12CO and 13CO channel maps (125-171 au) are reproduced by a Keplerian model combining front- and back-side disc emission surfaces, rather than an outer planet.",
  "failed_quote": "Therefore, the superposition of front- and backside emission mimics the kink-like structures observed in the outer disc, confirming previous interpretations of these substructures and suggesting that the gas features detected beyond the dust continuum emission in this work and by Sierra et al. (2024a) may not have a planetary origin."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "The outer kink-like features are unlikely to be of planetary origin and are instead explained by projection effects from the superposition of upper and lower disc emission surfaces.",
  "failed_quote": "Therefore, the superposition of front- and backside emission mimics the kink-like structures observed in the outer disc, confirming previous interpretations of these substructures and suggesting that the gas features detected beyond the dust continuum emission in this work and by Sierra et al. (2024a) may not have a planetary origin."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "High-sensitivity, high-angular-resolution, and high-spectral-resolution ALMA Band 7 observations of continuum, 12CO, and 13CO were obtained to test previous millimetre, IR, and H-alpha hints of an embedded forming planet in J16120 across both dust and gas kinematics.",
  "failed_quote": "In this paper, we present new high-sensitivity, high-angular-resolution, and high-spectral-resolution Band 7 ( 𝜆 = 0 . 87,mm) observations of J16120 in dust continuum emission, 12 CO ( 𝐽 = 3–2), and 13 CO ( 𝐽 = 3–2), revealing new evidence of planet formation"
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Raw ALMA data publicly available on the ALMA Science Archive (2023.1.01100.S); self-calibrated data to be released on Zenodo.",
  "failed_quote": "The self-calibrated data underlying this article will be available at zenodo.org. The non-calibrated data is publicly available at almascience.nrao.edu/aq using the project code 2023.1.01100.S."
 }
]
```
