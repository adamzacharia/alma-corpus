# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025AJ....170..319I\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
The Astronomical Journal, 170:319 (6pp), 2025 December [https://doi.org/10.3847/1538-3881/ae0621](https://doi.org/10.3847/1538-3881/ae0621)


© 2025. The Author(s). Published by the American Astronomical Society.

# An Improved Upper Limit of Cyanodiacetylene ( HC 5 N ) in the Atmosphere of Titan


Takahiro Iino [1], Kotomi Taniguchi [2], Hideo Sagawa [1][,][3], Martin A. Cordiner [4][,][5], Shuya Tan [6], Shigeru Takahashi [1], and
Hikaru Kubota [7]

1 Information Technology Center, The University of Tokyo, 7-3-1, Hongo, Bunkyo, Tokyo 113-8654, Japan; [iino.takahiro@mail.u-tokyo.ac.jp,](mailto:iino.takahiro@mail.u-tokyo.ac.jp)

[sagawa@cc.kyoto-su.ac.jp,](mailto:sagawa@cc.kyoto-su.ac.jp) [shigeru.takahashi@mail.u-tokyo.ac.jp](mailto:shigeru.takahashi@mail.u-tokyo.ac.jp)
2 National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan; [kotomi.taniguchi@nao.ac.jp](mailto:kotomi.taniguchi@nao.ac.jp)
3 Faculty of Science, Kyoto Sangyo University, Motoyama, Kamigamo, Kita-ku, Kyoto 603-8555, Japan
4 Astrochemistry Laboratory, NASA Goddard Space Flight Center, 8800 Greenbelt Road, Greenbelt, MD 20771, USA; [martin.cordiner@nasa.gov](mailto:martin.cordiner@nasa.gov)
5 Department of Physics, Catholic University of America, Washington, DC 20064, USA
6 Institute for Extra-cutting-edge Science and Technology Avant-garde Research (X-star), Japan Agency for Marine-Earth Science and Technology (JAMSTEC),
Yokosuka, Kanagawa, 237-0061, Japan; [shtan@jamstec.go.jp](mailto:shtan@jamstec.go.jp)
7 Division of Science, Graduate School, Kyoto Sangyo University, Kamigamo Motoyama, Kita, Kyoto 603-8555, Japan; [i2485049@cc.kyoto-su.ac.jp](mailto:i2485049@cc.kyoto-su.ac.jp)

_Received_ _2025_ _May_ _4;_ _revised_ _2025_ _September_ _3;_ _accepted_ _2025_ _September_ _9;_ _published_ _2025_ _November_ _11_


**Abstract**

In the complex Titan atmospheric chemistry, photochemical reactions involving cyanodiacetylene (HC 5 N) may be
important as reaction pathways that could lead to the production of amines and aromatic molecules. We carried
out a new comprehensive search of HC 5 N in Titan’s atmosphere using Band 6 (215–275 GHz or 1.1–1.4 mm in
wavelength) spectroscopic archival data from the Atacama Large Millimeter/submillimeter Array. To search for a
faint spectral line feature of HC 5 N, we used a spectral stacking method that integrates different transition data.
Integrating six independent observation data sets with a total integration time of ∼15,000 s, we found no
statistically significant detection of an HC 5 N spectral feature. Using the Planetary Spectrum Generator for
radiative transfer modeling and employing the previously predicted vertical distribution proposed by V. Vuitton
et al., E. Lellouch et al., J. C. Loison et al., and V. A. Krasnopolsky, we derived the upper limit column density of
HC 5 N, corresponding to 3 _σ_ noise level, to be 0.3–10 × 10 [13] molecules cm [–2] above ∼60 km altitude (depending
on the assumed vertical profile). The corresponding upper limit of [HC 5 N]/[HC 3 N] ratio value derived from three
of four models seem to be lower than that measured in high-mass protostellar objects, possibly due to the lower
abundance of C 4 H 2 .

_Unified_ _Astronomy_ _Thesaurus_ _concepts:_ Submillimeter [astronomy](http://astrothesaurus.org/uat/1647) (1647); Planetary [atmospheres](http://astrothesaurus.org/uat/1244) (1244)



**1.** **Introduction**


The atmosphere of Saturn’s largest moon, Titan, contains
various nitriles such as HCN, HNC, HC 3 N, CH 3 CN, C 2 H 3 CN,
C 2 H 5 CN, and C 2 N 2 (e.g., V. G. Kunde et al. 1981; A. Marten
et al. 2002; R. Courtin et al. 2011; R. Moreno et al. 2011;
M. Rengel et al. 2014; M. A. Cordiner et al. 2015;
M. Y. Palmer et al. 2017). For detailed information on these
nitriles, see the review paper by C. A. Nixon (2024) and the
references therein. The nitrogen chemistry to produce such
complex molecules begins with the dissociation of N 2 and
CH 4, which is induced by UV radiation, cosmic rays, and highenergy electron influx (e.g., V. A. Krasnopolsky 2009;
J. C. Loison et al. 2015; M. Dobrijevic et al. 2016; V. Vuitton
et al. 2019). The chemical reactions for some key nitriles are as
follows: HCN is the most abundant nitrile and is formed
mainly by a reaction of H 2 CN + H ⟶ HCN + H 2, where
H 2 CN is formed from a CH 3 radical and an N atom produced
from N 2 dissociation (L. M. Lara et al. 1996; E. H. Wilson &
S. K. Atreya 2004; V. Vuitton et al. 2019). Cyanoacetylene
(HC 3 N), the simplest cyanopolyyne (HC _n_ N, _n_ = 3, 5, 7, ⋯),
was first detected in Titan’s stratosphere in 1980 by the
infrared interferometer spectrometer and radiometer instrument onboard the Voyager 1 spacecraft (V. G. Kunde et al.
1981). The production pathway for HC 3 N is related to HCN


Original content from this work may be used under the terms
[of the Creative Commons Attribution 4.0 licence. Any further](https://creativecommons.org/licenses/by/4.0/)
distribution of this work must maintain attribution to the author(s) and the title
of the work, journal citation and DOI.



chemistry in that the reaction of dissociated CN radicals with
C 2 H 2 is considered to be the main source of HC 3 N at altitudes
above 1000 km. And the reaction of CN radicals from HCN
and photos with hydrocarbons possibly produces more
complex cyanopolyynes. The larger the order of the cyanopolyynes, the smaller its abundance is expected to be. There are
several additional proposed neutral and ion reactions for HCN
and HC 3 N productions as found in interstellar clouds (e.g.,
S. R. Federman et al. 1990; C. A. Nixon 2024; K. Taniguchi
et al. 2024a).
The second-simplest cyanopolyyne, cyanodiacetylene or
pentadiynenitrile (HC 5 N), which is focused on this study, is
another molecule that has been the subject of research in
astrochemistry as a tracer of chemical diversity. Astronomical
observations of HC 5 N have been conducted in dark clouds in
low-mass star-forming regions (H. Suzuki et al. 1992),
intermediate-mass young stellar objects (K. Taniguchi et al.
2024b), high-mass starless cores and protostellar objects
(HMPOs; e.g., K. Taniguchi et al. 2018), and hot cores
(K. Taniguchi et al. 2017, 2023).
On Titan, several attempts have been made to detect HC 5 N
in both the middle and upper atmosphere. A. Marten et al.
(2002) searched for a spectral feature of HC 5 N, along with
other nitriles, in the millimeter wave band using the Institut de
Radioastronomie Millimétrique 30 m single-dish radio telescope. The derived upper-limit volume mixing ratio was
4 × 10 [−][10] at altitudes above 80 km. The discovery of HC 5 N
was achieved in the upper atmosphere (ionosphere) via in situ
measurements. The Ion and Neutral Mass Spectrometer



1

The Astronomical Journal, 170:319 (6pp), 2025 December Iino et al.


**Table** **1**
Summary of HC 5 N Spectroscopic/Observational Parameters


Transition Rest Freq. _E_ _L_ _E_ _U_ Observation Date Synthesized Beam Size Spectral Resolution Integration Time
(GHz) (K) (K) (y-m-d) (arcsec) (kHz) (s)


_J_ = 96–95 255.5094 582.59594 594.85854 2019-12-03 1.32 × 0.92 488 1828.32

2019-12-09 1.36 × 0.92 488 1826.83


_J_ = 99–98 263.4871 619.76669 632.41216 2019-12-10 1.17 × 0.88 244 2963.09

2019-12-10 1.32 × 0.88 244 2962.56

2019-12-16 1.11 × 0.84 244 2993.71

2019-12-16 1.16 × 0.87 244 2965.82



(INMS) onboard the Cassini spacecraft measured the atmospheric composition in the ionosphere and detected HC 5 N in
its protonated form, HC 5 NHS [+] . Using the ionospheric
chemistry model, V. Vuitton et al. (2007) derived the mole
fraction of HC 5 N in the ionosphere at an altitude of 1100 km to
be 1.0 × 10 [−][6], which is more than three orders of magnitude
larger than the upper limit in the lower atmosphere of
A. Marten et al. (2002). The Electron Spectrometer (ELS) of
the Cassini Plasma Spectrometer (CAPS) detected several
negative ions in the Titan’s upper atmosphere. V. Vuitton et al.
(2009) introduced negative ion chemistry into their model
based on the CAPS-ELS results, and updated the HC 5 N
mixing ratio as 1.3 × 10 [−][6] at 1015 km. These model studies
also show that, in the upper atmosphere, active ion-neutral
reactions produce long-carbon-chain molecules and nitriles,
and those complex molecules are transported to the lower
stratosphere where they condense. Thus, the abundances of
such complex molecules in the upper atmosphere are typically
higher than in the middle atmosphere.
The presence of HC 5 N in Titan’s low and middle
atmosphere has been predicted using a theoretical approach.
V. A. Krasnopolsky (2009) developed a neutral and ion
chemistry model for the Titan atmosphere, showing HC 5 N
abundances of 4 × 10 [−][10] in the stratosphere and 10 [−][5] in the
mesosphere. E. Lellouch et al. (2010b) discussed the feasibility
of observing the Titan atmosphere using a submillimeter waveband spectrometer from an orbiting instrument; as part of their
study, they presented a HC 5 N vertical profile by updating an
early photochemical model developed by P. P. Lavvas et al.
(2008) with a constraint of the mole fraction at 1100 km
derived by V. Vuitton et al. (2007). The HC 5 N volume mixing
ratio profile they developed has a “bump” feature at ∼150 km
instead of smoothly increasing with the altitude. This indicates
that there is a secondary production region at that altitude
level. J. C. Loison et al. (2015) developed a nitrogen chemistry
model that includes undiscovered trace species such as HC 5 N
and CH 3 C 3 N, the latter of which was detected later by groundbased submillimeter observation by A. E. Thelen et al. (2020).
J. C. Loison et al. (2015) showed a vertically uniform profile in
the stratosphere, where the reason why such a structure is
formed is the same as the bump feature modeled by
E. Lellouch et al. (2010b). Production pathways included in
their model are CN + C 4 H 2 ⟶ HC 5 N + H, C 3 N + C 2 H 2 ⟶
HC 5 N + H, and C 2 H + HC 3 N ⟶ HC 5 N + H. UV irradiation
possibly dissociates HC 5 N to produce C 5 N radicals, which
easily recycle HC 5 N via reaction with abundant CH 4 . It should
be noted that the stratospheric abundance showed a ∼2 orders
of magnitude difference between the models of J. C. Loison
et al. (2015) and E. Lellouch et al. (2010b), which implies that
there is still a lack of understanding on the HC 5 N chemistry.



HC 5 N is also of high scientific significance in terms of
photochemistry in haze layers: the condensed HC 5 N incorporated into haze particles has been suggested to undergo
photochemical reactions to produce complex molecules.
I. Couturier-Tamburelli et al. (2015) simulated Titan photochemistry of the frozen HC 5 N ice in the laboratory, and
suggested that HC 5 N may play an important role in the
production of even prebiotic molecules. In their experiments, a
HC 5 N ice film was irradiated with long-wavelength UV
( _λ_ - 300 nm), most of which penetrates into the lower
atmosphere of Titan. After the irradiation, the infrared spectra
of the sample showed less features due to HC 5 N. Orange and
brown nonvolatile photopolymers, possibly aromatic molecules, and/or monomers provided from the polymerization of
HC 5 N were generated by the irradiation. The nonvolatile
polymers showed a –NH stretching band feature. The infrared
spectrum of the –NH band supports the presence of the amine
functional group, which is incorporated into amino acids.
Investigation of the presence of HC 5 N on Titan is important
from both chemical and biological viewpoints. In this paper,
we report on a search for HC 5 N in Titan’s atmosphere by
conducting a new analysis of ground-based observation data
acquired by the Atacama Large Millimeter/submillimeter
Array (ALMA).


**2.** **Analysis**


_2.1._ _Imaging_ _and_ _Spectral_ _Stacking_


We focus on the comprehensive use of ALMA spectral
observation data on Titan to improve the sensitivity to a search
for new and very faint trace gases. An ALMA project
2019.1.00783.S (PI: M. A. Cordiner) targeted to detect new
trace species and to measure isotopic ratios (J. Nosowitz et al.
2025), and successfully reported the new detection of CH 3 C 3 N
(A. E. Thelen et al. 2020). We found out the data sets also
include several HC 5 N transitions. In addition, since the
integration time of each measurement was long
(2000–3000 s), achievable total sensitivity was the highest
ever for Titan, in this frequency range. From the observation
data sets, we extracted six data sets with two different spectral
settings. These two settings include _J_ = 96–95 and 99–98
transitions of HC 5 N, with total integration times of 3655 and
11,885 s, respectively. All observations were performed in
2019 December, approximately 2.5 yr after the Titan summer
solstice. While it is well known that the abundances of trace
species on Titan exhibit large temporal variations, we assume
no such variation for HC 5 N during the 14 days observation
period. The antenna configuration used here was C43–1, the
most compact configuration of the cycle 6 which allowed for
an achievable angular resolution of 1 . 5. The frequency



2

The Astronomical Journal, 170:319 (6pp), 2025 December Iino et al.


2.0





1.5


1.0


0.5


0.0


2.0


1.5


1.0


0.5


0.0









255.25 255.50 255.75 256.00 256.25 256.50 256.75

Frequency [GHz]





**Figure 1.** Entire spectral windows corresponding to the _J_ = 96–95 (top) and 99–98 (bottom) transitions of HC 5 N. Each four and two independent observations were
integrated. Blue triangles indicate rest frequencies of HC 5 N. Known molecular transitions are plotted with markers., -, � and + are for HC 3 N _v_ 6 = 1, HC 3 N
_v_ 7 = 2, CH 3 CCH and C 2 H 3 CN. Weak emissions of CH 3 C 3 N, reported for the first time in A. E. Thelen et al. (2020), are located at 256.0 GHz region.


300


200


100


0


0.06 0.04 0.02 0.00 0.02 0.04 0.06

Frequency offset [GHz]


**Figure** **2.** Integrated spectrum using six independent observation of _J_ = 96–95 and 99–98. Blue triangle indicate the rest frequency of HC 5 N.



resolution was set to 244 and 488 kHz, which was sufficient
for observing Titan’s narrow emission line. Details of the
observations are summarized in Table 1. To identify the weak
HC 5 N emission line, the spectral stacking technique (e.g.,
L. Neumann et al. 2023), which integrates multiple spectra
acquired in different measurements, was employed. Before the
stacking, the data sets were calibrated by using the standard
calibration scripts provided by the Joint ALMA Observaroty
(JAO) . The Common Astronomy Software Applications were
employed for both calibration and imaging processes. Since
each observation has a different spectral/spatial resolution,
they were newly CLEANed with a common synthesized beam
size—a circular beam with a 1 . 36 in diameter—instead of
using the QA2 CLEANed images originally stored in the
ALMA data archive. The adopted beam size is about twice the
Titan apparent disk size (0 . 65), thus the spectra analyzed in
this study correspond to disk-averaged ones. Furthermore,
because the _J_ = 99–98 data has a fine spectral resolution of
244 kHz, the resolution was smoothed to 488 kHz to match
that of the lower one. Before the CLEAN process, continuum
and line emission was separated. Disk-averaged spectra were
extracted from the disk center position determined by the
continuum emission map. Six independent spectra were
integrated according to the transition. The entire spectral
windows of the integrated _J_ = 96–95 and 99–98 data sets are
shown in Figure 1. The spectral region of the _J_ = 96–95 data
set was also shown in A. E. Thelen et al. (2020) to report the



new detection of CH 3 C 3 N. Known spectral lines and the rest
frequencies of HC 5 N are marked in the figure. Integration of
two HC 5 N transitions was performed using the weighted
averaging method according to the noise level measured in the
line-absent spectral area of the data sets as 21 and 23 mK for
_J_ = 96–95 and _J_ = 99–98 data, respectively. The result is
shown in Figure 2 with a red line. As shown in the Figure 2, no
clear emission structure of HC 5 N is found at the center
position, where both _J_ = 96–95 and 99–98 are aligned. The
achieved noise level was measured to be as low as 15 mK in
the brightness temperature scale, ∼0.9 mJy beam [–1] in the flux
density scale.


_2.2._ _Radiative_ _Transfer_ _Modeling_ _of_ _HC_ _5_ _N_


To investigate the upper limit abundance of HC 5 N, we
conducted a radiative transfer analysis using the Planetary
Spectrum Generator (PSG; G. L. Villanueva et al. 2018). For
the atmospheric model, we used an atmospheric temperature
profile inferred from recent ALMA observations by
A. E. Thelen et al. (2018). For the upper atmospheric structure,
which is not explicitly shown in A. E. Thelen et al. (2018)
paper, we extrapolated the temperature at ∼10 [−][6] bar as shown
in Figure 3. The structure was layered into 600 altitude levels
ranging from 0 to 1200 km with a step of 2 km. The spectral
parameters for HC 5 N used in the analysis are from the
Cologne Database for Molecular Spectroscopy
(H. S. P. Müller et al. 2001). As the pressure broadening



3

The Astronomical Journal, 170:319 (6pp), 2025 December Iino et al.


10 10







10 8


10 6


10 4


10 2


10 [0]









80 100 120 140 160 180

Temperature [K]







**Figure 3.** (Left) Atmospheric temperature profile used for the radiative transfer calculation. (Right) Vertical abundances of HC 5 N from models of V. Vuitton et al.
(2019; black), J. C. Loison et al. (2015; blue), E. Lellouch et al. (2010a; green), and V. A. Krasnopolsky (2009; magenta). Dashed and thick solid profile represent the
original abundance profiles from four previous studies and the multiplied 3 _σ_ upper limits, respectively.















|700|Col2|Lellouch+ 2010|
|---|---|---|
|100<br>200<br>300<br>400<br>500<br>600<br>700<br>Brightness Temperature [mK]||<br>Observation|
|100<br>200<br>300<br>400<br>500<br>600<br>700<br>Brightness Temperature [mK]|0<br>15<br>10<br>5<br>0<br>5<br>10<br>15<br>2|0<br>15<br>10<br>5<br>0<br>5<br>10<br>15<br>2|


Frequency offset [MHz]


|16<br>14<br>12 [mK]<br>10 Temperature<br>8<br>6 Brightness<br>4<br>2|Col2|Col3|Col4|V Ou bi st eto rvn a+ i2 o0 n19<br>t|
|---|---|---|---|---|
|2<br>4<br>6<br>8<br>10<br>12<br>14<br>16<br>Brightness Temperature [mK]|||||
|0|20<br>15<br>|10|5<br>0<br>5<br>Frequency offset [MHz]|10<br>15<br>20<br>|



|35|Col2|Krasnopolsky+ 2009|
|---|---|---|
|5<br>10<br>15<br>20<br>25<br>30<br><br>Brightness Temperature [K]||Krasnopolsky+ 2009<br>Observation|
|5<br>10<br>15<br>20<br>25<br>30<br><br>Brightness Temperature [K]|||
|5<br>10<br>15<br>20<br>25<br>30<br><br>Brightness Temperature [K]|||
|5<br>10<br>15<br>20<br>25<br>30<br><br>Brightness Temperature [K]|0<br>15<br>10<br>5<br>0<br>5<br>10<br>15<br>|0<br>15<br>10<br>5<br>0<br>5<br>10<br>15<br>|


Frequency offset [MHz]


**Figure** **4.** Integrated spectrum (red) and synthesized spectra (black) produced by four different profiles of E. Lellouch et al. (2010b), J. C. Loison et al. (2015),
V. Vuitton et al. (2019), and V. A. Krasnopolsky (2009). Error bars locate at the left side of the panels are 1 _σ_ noise level measured at line-free region.



coefficient, 0.07 cm [−][1] atm [−][1] with a power-law temperature
dependence of 0.05 was assumed. To reproduce the baseline
emission, the Collision Induced Absorption spectra of N 2 –N 2,
N 2 –CH 4 and CH 4 –CH 4 provided by the HITRAN 2016
database (H. M. Picket et al. 1998) was applied. Other spectral
parameters are summarized in Table 1. The synthesized
spectra corresponding to the multiple HC 5 N transitions of
_J_ = 96–95 and 99–98 were calculated separately by the PSG
and then added together with the same weighting used in the
integration of observed spectra.
As the a priori HC 5 N vertical distribution, we used profiles
predicted by the previous studies: E. Lellouch et al. (2010b),
J. C. Loison et al. (2015), V. Vuitton et al. (2019) and
V. A. Krasnopolsky (2009). These four a priori profiles are
plotted in Figure 3 with dashed lines. First, synthesized spectra
using the four a priori profiles were calculated. The resulting
spectra are shown in Figure 4, along with the observed
spectrum. Subsequently, as no emission feature was detected
in the integrated spectrum, we proceeded to determine the
upper limit abundance of HC 5 N. The upper limit abundance
was derived as a multiplication factor of four a priori models.
Since the HC 5 N exhibits emission structure, we measured the
synthesized peak emission intensity and derived the corresponding multiplication factor required to achieve three times the
intensity of the root mean square noise level measured in a



line-free frequency region as mentioned in the previous
section. This method was also applied in the search for
gaseous carbon monosulfide molecule on Neptune’s atmosphere (T. Iino et al. 2014). As shown in Figure 4, synthesized
spectra generated using profiles from E. Lellouch et al.
(2010b) and V. A. Krasnopolsky (2009) clearly exhibit
intensity above the noise level as ×47 and ×23000 of the
noise level, respectively. Thus, the derived best-fit multiplication factors were much smaller than 1.0. The derived bestfit multiplication factors and corresponding column densities
for E. Lellouch et al. (2010b) and V. A. Krasnopolsky (2009)
were 0.074 (2.3 × 10 [13] molecules cm [–2] ) and 0.00025
(0.90 × 10 [13] molecules cm [–2] ), respectively. In contrast, the
spectrum from V. Vuitton et al. (2019) and J. C. Loison et al.
(2015) shows extremely lower intensity as ×0.63 and
×0.03 of the noise level, respectively. The corresponding
best-fit multiplication factors and column densities were
derived for V. Vuitton et al. (2019) and J. C. Loison et al.
(2015) as 5.1 (46.0 × 10 [13] molecules cm [–2] ), 21.6 (3.9 ×
10 [13] molecules cm [–2] ), respectively. Because of the high
abundance in the lower atmospheric region, which does not
affect the emission feature, the model of V. Vuitton et al.
(2019) has 11–51 times higher column density than other
models. The resulting profiles are shown in Figure 4 as the
thick solid lines with left-pointing arrows.



4

The Astronomical Journal, 170:319 (6pp), 2025 December Iino et al.



**3.** **Discussion**


By integrating a relatively large amount of integration time
(more than 15,000 s), no spectral signature of HC 5 N was
detected in Titan’s atmosphere. The new upper limit obtained
based on the vertical profile with some basis in atmospheric
chemistry, instead of the two-layer model, could also be useful
for the laboratory experiment. To discuss the possibility of
prebiotic molecule production in the haze layer (I. Couturier-Tamburelli et al. 2015), our improved HC 5 N abundance may
provide important information as the initial condition of the
experiment. Newly achieved high sensitivity observations
have successfully constrained that the HC 5 N abundance
appears to be lower than the previous two models as ×0.074
and ×0.00025 for E. Lellouch et al. (2010b) and V. A. Krasnopolsky (2009), respectively. At an altitude of approximately
1000 km in the upper atmosphere, the expected abundance
from the model of V. A. Krasnopolsky (2009) shows a large
discrepancy, differing by a factor of ∼1000 from the INMS
result (V. Vuitton et al. 2007). This result may indicate that the
HC 5 N abundance is not vertically uniform at that altitude. The
result also indicates that deeper future observations will be
required to effectively constrain other two models of
J. C. Loison et al. (2015) and V. Vuitton et al. (2019), and
to assess the validity of the lower predicted value.
Previously, A. Marten et al. (2002) performed a similar deep
search of HC 5 N and derived an upper limit profile showing
that HC 5 N is uniformly present above 80 km with a volume
mixing ratio lower than 4 × 10 [−][10] . For comparison with their
result, we have used a similar kind of the vertical profile (twolayer model) and obtained the upper limit as 13% of A. Marten
et al. (2002). As stated in their paper, note that such a twolayer model is unlikely, and the slope-like vertical distribution
is a more appropriate description.
The [HC 5 N]/[HC 3 N] ratio is investigated in various
astronomical objects and used as a tracer of chemical diversity.
K. Taniguchi et al. (2019) performed chemical network
simulations of cyanopolyynes such as HC 3 N, HC 5 N, and
HC 7 N along with hot-core evolution, from the freefall to the
warm-up periods. In the warm-up period, when the temperature
exceeds 25 K, HC 5 N production works efficiently to achieve
high [HC 5 N]/[HC 3 N] value as ∼1, whereas the ratio at the
beginning of the period is ∼0.001. Observational results toward
14 HMPOs have shown high-HC 5 N abundances; the average

[HC 5 N]/[HC 3 N] ratio is 0.29. On Titan, using the model
expectation, V. Vuitton et al. (2007) derived a value of 0.025 for
the upper atmosphere. A previous ALMA observation
(M. A. Cordiner et al. 2014) measured HC 3 N column density
above 60 km as 2.3 × 10 [14] molecules cm [–2] . Using models other
than those of V. Vuitton et al. (2019), we obtained a lower upper
limit for the [HC 5 N]/[HC 3 N] ratio, with a value of 0.04–0.17,
which is lower than that found in protostellar objects. For the
case of V. Vuitton et al. (2019), by considering the HC 5 N
abundance only above 60 km, where HC 3 N is present
(M. A. Cordiner et al. 2014), the [HC 5 N]/[HC 3 N] ratio is
newly derived as <0.43. The corresponding column density is
10.0 × 10 [13] molecules cm [–2] . Similarly, HC 5 N column density
and [HC 5 N]/[HC 3 N] from V. A. Krasnopolsky (2009) changes
to 0.3 × 10 [13] molecules cm [–2] and 0.012, respectively. Note that
the column density value of V. Vuitton et al. (2019) and
V. A. Krasnopolsky (2009) highly depends on the HC 5 N
vertical profile in the lower region. The derived

[HC 5 N]/[HC 3 N] ratio in Titan seems to be the same or lower



than the averaged abundance ratio in HMPOs. The possible
difference between Titan and HMPOs in the cyanopolyyne
abundance ratio is due to the abundance of hydrocarbons. The
main neutral-neutral production pathways of HC 3 N and HC 5 N
are reactions of CN radical with C 2 H 2 and C 4 H 2, respectively.
On Titan, the Composite Infrared Spectrometer onboard the
Cassini spacecraft derived the column densities as 2–10 × 10 [−][6]

and 0.7–20 × 10 [−][9] for C 2 H 2 and C 4 H 2, respectively (A. Coustenis et al. 2016). The lower C 4 H 2 abundance may prevent
efficient production of HC 5 N as found in HMPOs.
To further constrain the presence of HC 5 N in Titan’s
atmosphere, targeted observations designed to evaluate two
models which were not ruled out in this study could be a
promising next step. To achieve such high sensitivity, it is
useful to use the lower frequency region where the expected
HC 5 N intensity is several times higher than those analyzed in
this study. In addition, effective use of upper and lower
sidebands to observe multiple HC 5 N transitions, along with the
Wideband Sensitivity Upgrade (J. Carpenter et al. 2023),
which allows us to obtain at least two HC 5 N transitions in each
sideband, is also helpful for increasing the signal-to-noise
ratios. The spectral stacking method applied in this work helps
us to integrate different transition data and will enable us to
obtain a more accurate [HC 5 N]/[HC 3 N] ratio in Titan’s
atmosphere with the appropriate observation time. Even with
state-of-the-art observational techniques, detecting the weak
HC 5 N emission predicted using the profile from J. C. Loison
et al. (2015) does not appear feasible. Nevertheless, since
HC 5 N remains an important molecule from an astrobiological
perspective, the derived upper limit will be valuable for
planning future in situ spacecraft missions.


**4.** **Conclusion**


We report a nondetection and upper limit on the HC 5 N
column density in Titan’s atmosphere, based on spectral
modeling of archival ALMA data. Our abundance upper limit
of 5.2 × 10 [−][11] above 60 km is 8 times lower than the
previously published upper limit for this species, which
demonstrates the power of ALMA for searching for new
molecules on Titan. The nondetection of HC 5 N is found to be
consistent with the photochemical model profile from
J. C. Loison et al. (2015) and V. Vuitton et al. (2019), but
not with the model of both E. Lellouch et al. (2010b) and
V. A. Krasnopolsky (2009)—the latter models significantly
overestimates the atmospheric HC 5 N column density. The
relatively low [HC 5 N]/[HC 3 N] ratio we found implies that
synthesis of progressively longer carbon chains is less efficient
on Titan than in the cold interstellar medium and protostellar
envelopes. Additional observations and theoretical modeling
would help reveal whether long-carbon chain-bearing molecules (with five or more carbon atoms) can be products of
Titan’s complex atmospheric chemistry.


**Acknowledgments**


This paper makes use of the following ALMA data: ADS/
JAO.ALMA#2019.1.00783.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA), and NINS
(Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation with
the Republic of Chile. The Joint ALMA Observatory is
operated by ESO, AUI/NRAO and NAOJ. This work was



5

The Astronomical Journal, 170:319 (6pp), 2025 December Iino et al.



financially supported by the Telecommunications Advancement Foundation, the JSPS Kakenhi (21H01142, 21H05420,
23K20872, 24K17096, and 24H00252) and the Astrobiology
Center Program of National Institutes of Natural Sciences
grants, and “Developing a Research Data Ecosystem for the
Promotion of Data-Driven Science” of the MEXT. In this
research work, we used the “mdx: a platform for building dataempowered society (T. Suzumura et al. 2022)”. M.A.C. was
supported by NSF grant AST-2407709.


**ORCID** **iDs**


Takahiro Iino [https://orcid.org/0000-0003-1502-178X](https://orcid.org/0000-0003-1502-178X)
Kotomi Taniguchi [https://orcid.org/0000-0003-4402-6475](https://orcid.org/0000-0003-4402-6475)
Hideo Sagawa [https://orcid.org/0000-0003-2064-2863](https://orcid.org/0000-0003-2064-2863)
Martin A. Cordiner [https://orcid.org/0000-0001-8233-2436](https://orcid.org/0000-0001-8233-2436)


**References**


Carpenter, J., Brogan, C., Iono, D., & Mroczkowski, T. 2023, in Proc. 7th
Chile-Cologne-Bonn Symp., Physics and Chemistry of Star Formation: The
Dynamical ISM Across Time and Spatial Scales, ed. V. Ossenkopf-Okada
et al. (Köln: Universitäts-und Stadtbibliothekj [Köln), 304](https://ui.adsabs.harvard.edu/abs/2023pcsf.conf..304C/abstract)
Cordiner, M. A., Nixon, C. A., Teanby, N. A., et al. 2014, [ApJL,](https://doi.org/10.1088/2041-8205/795/2/L30) [795,](https://ui.adsabs.harvard.edu/abs/2014ApJ...795L..30C/abstract) L30
Cordiner, M. A., Palmer, M. Y., Nixon, C. A., et al. 2015, [ApJL,](https://doi.org/10.1088/2041-8205/800/1/L14) [800,](https://ui.adsabs.harvard.edu/abs/2015ApJ...800L..14C/abstract) L14
Courtin, R., Swinyard, B. M., Moreno, R., et al. 2011, [A&A,](https://doi.org/10.1051/0004-6361/201118304) [536,](https://ui.adsabs.harvard.edu/abs/2011A&A...536L...2C/abstract) L2
Coustenis, A., Jennings, D. E., Achterberg, R. K., et al. 2016, [Icar,](https://doi.org/10.1016/j.icarus.2015.08.027) [270,](https://ui.adsabs.harvard.edu/abs/2016Icar..270..409C/abstract) 409
[Couturier-Tamburelli, I., Piétri, N., & Gudipati, M. S. 2015, A&A, 578, A111](https://doi.org/10.1051/0004-6361/201425518)
Dobrijevic, M., Loison, J., Hickson, K., & Gronoff, G. 2016, [Icar,](https://doi.org/10.1016/j.icarus.2015.12.045) [268,](https://ui.adsabs.harvard.edu/abs/2016Icar..268..313D/abstract) 313
Federman, S. R., Huntress, W. T. J., & Prasad, S. S. 1990, [ApJ,](https://doi.org/10.1086/168711) [354,](https://ui.adsabs.harvard.edu/abs/1990ApJ...354..504F/abstract) 504
Iino, T., Mizuno, A., Nakajima, T., et al. 2014, P&SS, [104,](https://ui.adsabs.harvard.edu/abs/2014P&SS..104..211I/abstract) 211
Krasnopolsky, V. A. 2009, [Icar,](https://doi.org/10.1016/j.icarus.2008.12.038) [201,](https://ui.adsabs.harvard.edu/abs/2009Icar..201..226K/abstract) 226



Kunde, V. G., Aikin, A. C., Hanel, R. A., et al. 1981, [Natur,](https://doi.org/10.1038/292686a0) [292,](https://ui.adsabs.harvard.edu/abs/1981Natur.292..686K/abstract) 686
Lara, L. M., Lellouch, E., López-Moreno, J. J., & Rodrigo, R. 1996, [JGRE,](https://doi.org/10.1029/96JE02036)
101, 23261
Lavvas, P. P., Coustenis, A., & Vardavas, I. M. 2008, P&SS, [56,](https://ui.adsabs.harvard.edu/abs/2008P&SS...56...27L/abstract) 27
Lellouch, E., Hartogh, P., Feuchtgruber, H., et al. 2010a, [A&A,](https://doi.org/10.1051/0004-6361/201014600) 518, L152
Lellouch, E., Vinatier, S., Moreno, R., et al. 2010b, [P&SS,](https://doi.org/10.1016/j.pss.2010.05.007) 58, 1724
Loison, J. C., Hébrard, E., Dobrijevic, M., et al. 2015, [Icar,](https://doi.org/10.1016/j.icarus.2014.09.039) [247,](https://ui.adsabs.harvard.edu/abs/2015Icar..247..218L/abstract) 218
Marten, A., Hidayat, T., Biraud, Y., & Moreno, R. 2002, [Icar,](https://doi.org/10.1006/icar.2002.6897) [158,](https://ui.adsabs.harvard.edu/abs/2002Icar..158..532M/abstract) 532
Moreno, R., Lellouch, E., Lara, L. M., et al. 2011, [A&A,](https://doi.org/10.1051/0004-6361/201118189) [536,](https://ui.adsabs.harvard.edu/abs/2011A&A...536L..12M/abstract) L12
Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, [A&A,](https://doi.org/10.1051/0004-6361:20010367)

370, L49
Neumann, L., den Brok, J. S., Bigiel, F., et al. 2023, [A&A,](https://doi.org/10.1051/0004-6361/202346129) 675, A104
Nixon, C. A. 2024, [ESC,](https://doi.org/10.1021/acsearthspacechem.2c00041) 8, 406
Nosowitz, J., Cordiner, M. A., Nixon, C. A., et al. 2025, [PSJ,](https://doi.org/10.3847/PSJ/adc390) 6, 107
Palmer, M. Y., Cordiner, M. A., Nixon, C. A., et al. 2017, [SciA,](https://doi.org/10.1126/sciadv.1700022) 3, 1
Picket, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, [JQSRT,](https://doi.org/10.1016/S0022-4073(98)00091-0) 60, 883
Rengel, M., Sagawa, H., Hartogh, P., et al. 2014, [A&A,](https://doi.org/10.1051/0004-6361/201321945) [561,](https://ui.adsabs.harvard.edu/abs/2014A&A...561A...4R/abstract) A4
Suzuki, H., Yamamoto, S., Ohishi, M., et al. 1992, [ApJ,](https://doi.org/10.1086/171456) [392,](https://ui.adsabs.harvard.edu/abs/1992ApJ...392..551S/abstract) 551
Suzumura, T., Sugiki, A., Takizawa, H., et al. 2022, in IEEE Int. Conf.
Dependable, Autonomic and Secure Computing (New York: IEEE)
Taniguchi, K., Gorai, P., & Tan, J. C. 2024a, [Ap&SS,](https://doi.org/10.1007/s10509-024-04292-9) [369,](https://ui.adsabs.harvard.edu/abs/2024AP&SS.369...34T/abstract) 34
Taniguchi, K., Gorai, P., Tan, J. C., et al. 2024b, [A&A,](https://doi.org/10.1051/0004-6361/202451499) [692,](https://ui.adsabs.harvard.edu/abs/2024A&A...692A..65T/abstract) A65
Taniguchi, K., Herbst, E., Ozeki, H., & Saito, M. 2019, [ApJ,](https://doi.org/10.3847/1538-4357/ab3eb8) [884,](https://ui.adsabs.harvard.edu/abs/2019ApJ...884..167T/abstract) 167
Taniguchi, K., Majumdar, L., Caselli, P., et al. 2023, [ApJS,](https://doi.org/10.3847/1538-4365/acd110) [267,](https://ui.adsabs.harvard.edu/abs/2023ApJS..267....4T/abstract) 4
Taniguchi, K., Saito, M., Hirota, T., et al. 2017, [ApJ,](https://doi.org/10.3847/1538-4357/aa7899) [844,](https://ui.adsabs.harvard.edu/abs/2017ApJ...844...68T/abstract) 68
Taniguchi, K., Saito, M., Sridharan, T. K., & Minamidani, T. 2018, [ApJ,](https://doi.org/10.3847/1538-4357/aaa66f)

854, 133
Thelen, A. E., Cordiner, M. A., Nixon, C. A., et al. 2020, [ApJL,](https://doi.org/10.3847/2041-8213/abc1e1) [903,](https://ui.adsabs.harvard.edu/abs/2020ApJ...903L..22T/abstract) L22
Thelen, A. E., Nixon, C. A., Chanover, N. J., et al. 2018, [Icar,](https://doi.org/10.1016/j.icarus.2017.10.042) [307,](https://ui.adsabs.harvard.edu/abs/2018Icar..307..380T/abstract) 380
Villanueva, G. L., Smith, M. D., Protopapa, S., Faggi, S., & Mandell, A. M.
2018, [JQSRT,](https://doi.org/10.1016/j.jqsrt.2018.05.023) [217,](https://ui.adsabs.harvard.edu/abs/2018JQSRT.217...86V/abstract) 86
Vuitton, V., Lavvas, P., Yelle, R. V., et al. 2009, [P&SS,](https://doi.org/10.1016/j.pss.2009.04.004) 57, 1558
Vuitton, V., Yelle, R. V., Klippenstein, S. J., Hörst, S. M., & Lavvas, P. 2019,

[Icar,](https://doi.org/10.1016/j.icarus.2018.06.013) [324,](https://ui.adsabs.harvard.edu/abs/2019Icar..324..120V/abstract) 120
Vuitton, V., Yelle, R. V., & McEwan, M. J. 2007, [Icar,](https://doi.org/10.1016/j.icarus.2007.06.023) [191,](https://ui.adsabs.harvard.edu/abs/2007Icar..191..722V/abstract) 722
Wilson, E. H., & Atreya, S. K. 2004, [JGRE,](https://doi.org/10.1029/2003JE002181) 109, [E06002](https://ui.adsabs.harvard.edu/abs/2004JGRE..109.6002W/abstract)



6


</paper>

## Items to check

```json
[
 {
  "path": "data.frequencies_and_spectral_setup.evidence[1]",
  "value": "two spectral settings covering J = 96–95 (255.5094 GHz, 488 kHz resolution) and J = 99–98 (263.4871 GHz, 244 kHz resolution)",
  "failed_quote": "The frequency resolution was set to 244 and 488 kHz, which was sufficient for observing Titan’s narrow emission line."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Pressure broadening coefficient = 0.07 cm^-1 atm^-1 with power-law temperature dependence of 0.05",
  "failed_quote": "As the pressure broadening coefficient, 0.07 cm −1 atm −1 with a power-law temperature dependence of 0.05 was assumed."
 }
]
```
