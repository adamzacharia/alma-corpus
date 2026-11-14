# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023FaDi..245..164B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
### Streamers feeding the SVS13-A protobinary system: astrochemistry reveals accretion shocks?

Eleonora Bianchi, _[a]_ Ana López-Sepulcre, _[b][,][c]_ Cecilia Ceccarelli, _[b]_ Claudio Codella, _[d][,][b]_ Linda
Podio, _[d]_ Mathilde Bouvier, _[e]_ Joan Enrique-Romero, _[f]_ Rafael Bachiller, _[g]_ and Bertrand Lefloch _[b][,][h]_



We report ALMA high-angular resolution ( _∼_ 50 au) observations of the binary system SVS13-A. More specifically, we analyse deuterated water (HDO) and sulfur dioxide (SO 2 ) emission.
The molecular emission is associated with both the components of
the binary system, VLA4A and VLA4B. The spatial distribution is
compared to that of formamide (NH 2 CHO), previously analysed
in the system [1] . Deuterated water reveals an additional emitting
component spatially coincident with the dust accretion streamer,
at a distance _≥_ 120 au from the protostars, and at blue-shifted
velocities ( _>_ 3 km s _[−]_ [1] from the systemic velocities). We investigate the origin of the molecular emission in the streamer, in
light of thermal sublimation temperatures calculated using updated binding energies (BE) distributions. We propose that the
observed emission is produced by an accretion shock at the in
terface between the accretion streamer and the disk of VLA4A.

Thermal desorption is not completely excluded in case the source
is actively experiencing an accretion burst.


1 Introduction


Our understanding of how a star and a planetary system form
has evolved substantially in the latest years. On the one hand,
observations have revealed the presence of substructures such
as gaps and rings in very young protostellar disks (age _∼_ 10 [5]

years) [2–4] . On the other hand, evolved Class II disks (age _>_ 10 [6]


_a_ _Excellence Cluster ORIGINS, Boltzmannstraße 2,_ _85748,_ _Garching bei München, Ger-_
_many._ _E-mail:_ _eleonora.bianchi@origins-cluster.de_

_b_ _Univ._ _Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France._


_c_ _Institut de Radioastronomie Millimétrique, 38406 Saint-Martin d’ Hères, France._

_d_ _INAF, Osservatorio Astrofisico di Arcetri, Largo E. Fermi 5, I-50125, Firenze, Italy._


_e_ _Leiden_ _Observatory,_ _Leiden_ _University,_ _P.O._ _Box_ _9513,_ _2300_ _RA,_ _Leiden,_ _The_ _Nether-_

_lands_


_f_ _Leiden_ _Institute_ _of_ _Chemistry,_ _Gorlaeus_ _Laboratories,_ _Leiden_ _University,_ _P.O._ _Box_

_9502, 2300 RA Leiden, The Netherlands_


_g_ _Observatorio Astronómico Nacional (OAN-IGN), Alfonso XII 3, 28014 Madrid, Spain_

_h_ _Laboratoire d’astrophysique de Bordeaux, Univ._ _Bordeaux, CNRS, B18N, allée Geoffroy_

_Saint-Hilaire, 33615 Pessac, France_



years) contain not enough dust mass to explain the observed exoplanets population, in contrast to early Class 0 and I disks which
are more massive [5] . These indications suggest that planetesimal
formation start already in the early phases of protostellar disks.
In this respect, it is of paramount importance to investigate the
properties of young Class 0 (age _∼_ 10 [4] years) and Class I disks
(age _∼_ 10 [5] years) in order to define the initial conditions for
planet formation. Since young disks are typically deeply embedded in the parent envelope, the characterisation of their physical
and chemical properties is not trivial from an observation point
of view. If simple parameters, such as the disk dust and gas
mass, are already difficult to measure (see e.g. [6,7] ), their chemical
composition is even less explored. Nevertheless, the molecular
complexity present in the disk will be inherited from the forming planets, at least in the outer regions (e.g. [8,9] and references
therein). Shedding light on the chemical composition of young
disks is the only way to investigate the initial chemical budget
available for planets when they start to form. Because of an important envelope contribution, the standard gas tracers (e.g. CO
isotopologues) fail in the observation of the inner disk regions of
young protostars. Other tracers, such as interstellar complex organic molecules (molecules with 6 or more atoms and based on
carbon; e.g. [9,10] ) demonstrated to be more effective to study the
complex processes happening in the disk. However, their employment require at the same time sensitive observations and a better understanding of the chemical/physical processes that release
the molecules we observe in the gas. In this context, a strong
synergy between astronomical observations, quantum chemistry
calculations and laboratory experiments is required. In this paper, we present new observations performed using the Atacama
Large Millimeter/submillimeter Array (ALMA) of the protobinary
system SVS13-A. In Sec. 2 we present the source background and

in Sec. 3 we describe the ALMA observations. The main results

of our analysis are presented in Sec. 4. Section 5 discuss the possible origin of the detected molecular emission, using the most


1–10 | 1

up-to-date binding energies distributions. The main conclusions
are reported in Sec. 6.


2 The protostellar binary system SVS13-A


SVS13-A is a perfect target to perform astrochemical studies and
tackle some of the questions above. It is very well studied, in
Perseus, at a distance of _∼_ 299 pc ( _Gaia_, [11] ). The system has a
bolometric luminosity of 58.8 L _⊙_ [12] and it is at the origin of the
famous Herbig–Haro (HH) chain 7–11 [13], a molecular jet and a
large-scale outflow [14,15] . SVS13-A is composed of a close binary
system with a separation of 0 _._ _[′′]_ 3 [16] . The proper motion of the two
components VLA4A and VLA4B have been investigated for almost
30 yrs [17,18] . A third companion, called SVS13A2 is detected at a
distance of _∼_ 5 _[′′]_ [ 19,20] . The continuum emission at high-angular
resolution shows two circumstellar disks and circumbinary material distributed in spiral arms which suggest accretion streamers
(see Fig. 1 [1,18,20] ). More specifically, a bright arc is observed from
the position of VLA4A extending towards the south-east. Other
two arcs are extending from VLA4B towards the east and the west
side of VLA4A. In addition, we detect three elongated structures
**which** extend from the northern edge of the continuum associated with VLA4A and B towards the north. For simplicity, further

in the text we refer to the central arc-like structure as the northern

streamer. In order to verify that these structures are not artifacts
introduced by the cleaning process, we test different beam tapering. All the elongated arc-like structures are still present when
using a larger circular beam. We conclude that the dust emission
is tracing accretion streamers extending towards the north and
the south and feeding VLA4A and VLA4B.


The optical source position measured using _Gaia_ is very close
to VLA4B, even though there is a non-negligible discrepancy suggesting that the protostar is very embedded and the optical emission is due to light scattered by the circumbinary material [18] . The
source driving the molecular jet, as well as a microjet traced by

[Fe II], has also been identified with VLA4B [15,21] . When observed
at mm wavelengths, VLA4B is brighter than VLA4A of a factor
3.8 at 7 mm and 3.7 at 9mm [16], while the flux becomes comparable at longer wavelengths [5,20] . The situation reverses at 1.2
mm where VLA4A is brighter by a factor of 1.5 [1] . The analysis of
SEDs reveals the presence of free-free emission for both VLA4A
and VLA4B, consistent with the presence of radio jets [18] . The different spectral indices measured toward the sources, as well as
the change in intensities, suggest that the dust at 1.2 mm is optically thick in VLA4A and very optically thick in VLA4B [5,18] . In this
context, VLA4B is interpreted as the primary and more massive
component of the binary system, while VLA4A would be the less
evolved secondary component. Taking into account the high uncertainties related to the free-free contamination, the disk masses
have been estimated to be _∼_ 0.2 M _⊙_ for VLA4B and _∼_ 0.08 M _⊙_ for
VLA4A [5], confirming this picture. Interestingly, SVS13-A has been
also deeply investigated in the NIR and found to be in a phase
of active accretion [12] . The quick rise of magnitude in the _K_ -band,
followed by a slow decline, is reminiscent of FU Ori sources while
the small bursts amplitude and the line rich spectra resemble EX
Ori sources [21] .


2 | 1–10



Fig. 1 Continuum emission as observed by ALMA at 1.2 mm (color scale
and contours) [1] . First contours (gray) and steps (black) are 8 _σ_, corresponding to 3.35 mJy beam _[−]_ [1] . The beam size is 0 _._ _[′′]_ 19 _×_ 0 _._ _[′′]_ 13 (PA=+5 _[◦]_ ).
The binary system is composed of VLA4A (right) and VLA4B (left). Coordinates are _α_ J2000 = 03 [h] 29 [m] 3 _._ [s] 75, _δ_ J2000 = +31 _[◦]_ 16 _[′]_ 03 _._ _[′′]_ 81 and _α_ J2000
= 03 [h] 29 [m] 3 _._ [s] 773, _δ_ J2000 = +31 _[◦]_ 16 _[′]_ 03 _._ _[′′]_ 81 for VLA4A and VLA4B, respectively. The blue arrows indicate the directions toward HH11 (133 _[◦]_ )
as well as the main axis of the H 2 /CO jet (155 _[◦]_ ) as inferred by Lefèvre
_et_ _al._ [15] . The white arrow indicates the position of the norther streamer
discussed in the text.


**2.1** **The prototype Class I hot corinos**

The SVS13-A has been found to host a hot corino chemistry. More
specifically, young Class 0 protostars possess an inner region, typically _≤_ 100 au, where the gas temperature is high enough ( _≥_
100 K) to desorbe the icy mantles of dust grains and release
into the gas phase complex molecules which can in turn react
in the gas-phase and form more complex molecular species. The
hot corino phenomenon was first observed in Class 0 protostars
(e.g. IRAS16293–2422 [22] ) and only recently it was also discovered in more evolved Class I objects. In this respect, SVS13-A
provided the first evidence that Class I objects can be as chemically rich as young Class 0 sources [23] . More specifically, water
and iCOMs emission have been detected from a compact ( _<_ 100
au) and hot ( _>_ 100 K) region [23–25] towards the source. Since
then the chemistry of the system was deeply investigated thanks
to several observational Large Programs including ASAI (Astrochemical Surveys At IRAM 30m; [26] ), CALYPSO (Continuum and
Lines in Young ProtoStellar Objects; [27] ) with the Plateau de Bure
interferometer, SOLIS (Seed Of Life In Space; [28] ) with IRAMNOEMA and PEACHES (Perseus ALMA Chemistry Survey; [29] ).
These projects identified more than 100 emission lines emitted by iCOMs including CH 3 OH and its isotopologues, CH 3 CHO,
HCOOCH 3, CH 3 OCH 3, HCOCH 2 OH, NH 2 CHO, CH 3 CH 2 OH. The
broad spectral coverage of these surveys allowed a detailed multi
line analysis, which results in an accurate determination of the
gas properties. In particular, rotational temperatures and column
density of each molecule have been determined and compared

to those measured in other objects. The relative iCOMs abundances are in good agreement both with measurements in Class
0 protostars and to those in the 67P/Churyumov–Gerasimenko
comet, suggesting to some extent inheritance of complexity from
the early stages [23] . ALMA high-angular resolution observations
( _∼_ 50 au) shed new light on the distribution of iCOMs across
the binary system. In particular, a striking chemical segregation
was observed. Some molecular species, such as methanol and
dimethyl ether, are detected in both VLA4A and VLA4B while
others, e.g. formamide and ethylene glycol are detected only in
VLA4A [1,18] . Interestingly, the line emission appears to be elongated towards the north (up to _∼_ 150 au), where one of the accretion streamers in the dust is present (see Fig. 1). The origin of
such molecular line distribution needs to be clarified using different molecular tracers. To this purpose we report here the analysis
of sulfur dioxide SO 2 and deuterated water HDO in the SVS13-A

system.


3 Observations


The observations presented here have been acquired using the
Atacama Large Millimeter/submillimeter Array (ALMA) on 2019
September 8 during the project (2018.1.01461.S, see also [1] ). The
telescope was in the C43-6 configuration, with baselines between
43 m and 5.9 km. The center of the observed field is _α_ J2000 = 03 [h]

29 [m] 3 _._ [s] 8, _δ_ J2000 = +31 _[◦]_ 16 _[′]_ 03 _._ _[′′]_ 8. The bandpass and flux calibrator was the quasar J0510+1800, while the phase calibrator was
J0336+3218. Data calibration was performed using the standard
ALMA calibration pipeline in CASA [30] . Successively, we used the
IRAM-GILDAS [*] package to determine line-free continuum channels, perform phase self-calibration and apply the solution both
to the continuum and the spectral cubes. The final calibration
uncertainty on the absolute flux is 20%.


4 Results


We detect and analyse the HDO 2(1,1)–2(1,2) transition at
241.561550 GHz with an upper level energy (E up ) of 95 K. In
the same spectral window we also detect the SO 2 5(2,4)–4(1,3)
transition at 241.615797 GHz with E up of 24 K. The line spectroscopic parameters are listed in Table 1. The rms noise is typically
4.8 mJy beam _[−]_ [1] km s _[−]_ [1] using spectral channels of 122 kHz (0.15
km s _[−]_ [1] ). The synthesized beam is 0 _._ _[′′]_ 21 _×_ 0 _._ _[′′]_ 14 for both the
line cubes. The analysis is supported by the NH 2 CHO 12(1,12)–
11(1,11) transition at 243.521044 GHz, previously published in [1] .
Figure 2 shows the spatial distribution of the HDO (left panel),
NH 2 CHO (middle panel) and SO 2 (right panel) lines with respect
to the dust continuum emission. In particular, the line emission is
integrated over the whole velocity interval and reported in color
scale superposed to the continuum emission in white contours. As
already noticed in [1], the NH 2 CHO emission is more compact and
centered in VLA4A while HDO and SO 2 have a broader emission,
extended also towards VLA4B. This finding confirms the chemical segregation reported in the binary system using iCOMs [1,18] .
Moreover, HDO and SO 2 emission show an elongation toward the


- `[[http://www.iram.fr/IRAMFR/GILDAS]](http://www.iram.fr/IRAMFR/GILDAS)`



north, as already observed for iCOMs.
In order to further investigate the lines, radial and vertical distribution, we plot in Fig. 3 the intensity [Jy] profiles of SO 2, HDO
and NH 2 CHO extracted from the moment 0 maps (see Fig. 2)
along a horizontal axis connecting the two protostars (left panel)
and a vertical axis between the protostars crossing the northern
streamer (right panel). The x-axis reports the offset in astronomical units with respect to the position of VLA4A. The vertical
dashed lines indicate the positions of the two protostars. The radial profiles show that HDO and SO 2 are extended in a region covering both protostars with a peak of emission in between. Despite
the difference in the peak intensity, there are not substantial differences between the spatial distribution of HDO and SO 2 . Conversely, NH 2 CHO has the peak of the emission closer to VLA4A [1] .
In addition, the vertical profiles show that all the molecules are
extended toward the north direction at a larger distance than the
dust streamer, located at about _∼_ 0 _._ _[′′]_ 4 (corresponding to 120 au at
the source distance). The radial and vertical profiles do not show
a trend with the upper level energy of the different lines, confirming that the molecular distribution do not strongly depend on the
excitation conditions [1] .

We report in Table 1 the integrated line intensities extracted
from the continuum peak positions of VLA4A and VLA4B, respectively, and their intensity ratios. The intensity ratio for HDO is
2.0 (0.6), suggesting that water is distributed in both the protostars, even if it is more abundant in VLA4A. Similar intensity ratios were derived for iCOMs such as CH 3 OH, and CH 3 CHO [1] . On
the other hand, the intensity ratio measured for the NH 2 CHO line
is 7 (2), confirming the presence of formamide predominantly towards VLA4A. We also reported the intensity of SO 2 in VLA4A
and VLA4B. The ratio is not reported in this case since the blueshifted part of the line is contaminated and the line intensity
extracted in VLA4A is a lower limit. The HDO line intensity in
the brighter source, VLA4A, is consistent with the rotational temperature of 150-260 K and a column density of 4 _×_ 10 [17] cm _[−]_ [2],
derived using IRAM-30m data collecting the emission from both
protostars [24] . The NH 2 CHO rotational temperatures and column
densities derived in [1], are T rot =140 K and N _tot_ =5.9(0.9) _×_ 10 [15]

cm _[−]_ [2] in VLA4A and T rot =170 K and N _tot_ =1.4(0.3) _×_ 10 [15] cm _[−]_ [2]


in VLA4B.

Figure 4 shows the spatial distribution of HDO (upper panels),
NH 2 CHO (middle panels) and SO 2 (lower panels) with respect to
the dust continuum emission. More specifically, line emission is
integrated in five different velocity channels and showed in cyan
contours superposed to the continuum emission in color scale.
The NH 2 CHO emission in all the velocity intervals traces only
VLA4A and it is elongated toward the northern streamer. For HDO
the blue-shifted emission in the velocity intervals 2.4-4.4 km s _[−]_ [1]

and 4.6-6.5 km s _[−]_ [1] shows the same distribution. In the velocity
intervals 6.7-8.7 km s _[−]_ [1], 8.8-10.5 km s _[−]_ [1] and 10.6-11.8 km s _[−]_ [1]

the line emission is associated with both protostars, peaking in
between. The central panels correspond to the systemic velocities of VLA4A and VLA4B, which are +7.7 km s _[−]_ [1] and +8.5 km
s _[−]_ [1], respectively, and have been determined from methanol emission [1] . SO 2 emission is also associated to both protostars in the
velocity intervals 6.6-8.7 km s _[−]_ [1], 8.9-10.4 km s _[−]_ [1], and 10.5-11.9


1–10 | 3

Fig. 2 Velocity integrated emission (moment 0) of the HDO 2(1,1)–2(1,2) (left panel), NH 2 CHO 12(1,12)–11(1,11) (middle panel) and SO 2 5(2,4)–
4(1,3) (right panel) lines, in colour scale, superposed to the dust emission in white contours. The synthesised beams are reported in white in the lower
right corner of each panel. The black and red stars indicate the VLA4A and VLA4B positions, respectively.


Table 1 List of transitions and line properties (in T MB scale) of the HDO, SO 2 and NH 2 CHO emission. The columns report the transition and their
frequency (GHz), the upper level energy E up (K), the line strength _Sµ_ [2] (D [2] ), the velocity integrated line intensity I int (mK km s _[−]_ [1] ) and the intensity
ratio.


Species Transition _ν_ [a] E up [a] _Sµ_ [2a] I int [b] Intensity ratio
(GHz) (K) (D [2] ) (K km s _[−]_ [1] )

VLA4A VLA4B VLA4A/VLA4B

HDO 2(1,1)–2(1,2) 241.561550 95 0.4 349 (70) 177 (36) 2.0 (0.6)
SO 2 [c] 5(2,4)–4(1,3) 241.615797 24 5.7 _≥_ 126 _≥_ 175 NH 2 CHO [d] 12(1,12)–11(1,11) 243.521044 79 156 267 (59) 40 (11) 7 (2)
a Frequencies and spectroscopic parameters have been provided by 31 for HDO, and retrieved from the Jet Propulsion Laboratory molecular database (https://spec.jpl.nasa.gov/) [32] . For SO 2 spectroscopic parameters are provided by the Cologne Database for Molecular
Spectroscopy [(http://www.astro.unikoeln.de/cdms/)](http://www.astro.unikoeln.de/cdms/) [33] . For NH 2 CHO spectroscopic parameters are provided by [34] and retrieved from
the CDMS database. [b] Errors on the integrated intensity include 20% of calibration. [c] Contaminated by the CH 2 DOH 4 3 _,_ 1 –5 1 _,_ 5 e1 line
at 241.61928840 GHz, at –4.3 km s _[−]_ [1] from the SO 2 rest line. [d] From [1] .



km s _[−]_ [1] . Even if the blue-shifted part of the line (velocities lower
than +6.5 km s _[−]_ [1] ) is contaminated by the CH 2 DOH(4 3 _,_ 1 –5 1 _,_ 5 )e1
line at 241.61928840 GHz (see Table 1), the SO 2 emission in
the other available channels shows a spatial distribution similar
to that of HDO. The overall line distribution confirms what previously reported by [1] but the HDO emission highlights an additional
structure (i) with a peak spatially shifted with respect to the protostars position, and (ii) at velocities blue-shifted by _≥_ 3 km s _[−]_ [1] .
This component is perfectly aligned with the northern streamer
traced by the dust, thus revealing molecular gas associated with
the streamer itself. Interestingly, in the same blue-shifted velocity
range, NH 2 CHO shows hints of this component even if the S/N is
lower than that of HDO (see Fig. 3).


5 Discussion


**5.1** **Binding energies and sublimation temperatures**


As we will discuss in more detail in the next subsection, the presence in the gas-phase of deuterated water, SO 2 and formamide
provides new insights into their origin.


First, deuterated water is prevalently formed in the cold
prestellar phase on the grain surfaces, in the so-called mantle
(e.g. [35] ). Therefore, HDO remains frozen unless it is released
into the gas-phase by some process. In general, two processes


4 | 1–10



can possibly inject HDO into the gas-phase (e.g. see the discussion in [9] ): the thermal sublimation from warm dust grain or a
(non-thermal) shock. Other possible mechanisms, such as chemical desorption or photo-desorption, would not be efficient here.
About formamide, there is some discussion on its formation route.
In principle, it can be synthesised on the grain surfaces (e.g. [36] )
or in the gas-phase [37] from reactants (H 2 CO and NH 2 ) that are
formed on the grain surfaces, or both. If formed on the grain surfaces, formamide would need to be released into the gas-phase
by either thermal sublimation or a (non-thermal) shock, as HDO.
The same consideration applies if formamide is formed in the gasphase, because the two reactants H 2 CO and NH 2 would need to
be in the gaseous form. Finally, SO 2 is formed in the gas-phase,
but Sulphur is observed to be depleted, by about a factor 20, in
the cold molecular clouds [38], so that it is often taken as a tracer
of warm and shocked regions. In summary, the presence of HDO,
SO 2 and NH 2 CHO, implies that either they (or their precursors)
are thermally sublimated or they are injected from the frozen
mantles into the gas-phase by a shock.


In order to distinguish which of the two hypothesis is correct, one has to evaluate the thermal sublimation temperature
of deuterated water, SO 2 and formamide. To this end, we used

0 _._ 7


0 _._ 6


0 _._ 5


0 _._ 4


0 _._ 3


0 _._ 2


0 _._ 1


0 _._ 0


_−_ 0 _._ 1



beam

|Radial Profiles|Col2|
|---|---|
|VLA4A<br>SO2 E_up_=24<br>HDO 95 K<br>NH2CHO 79|VLA4A<br>SO2 E_up_=24<br>HDO 95 K<br>NH2CHO 79|
|||



_−_ 200 0 200 400
### Offset [au]



0 _._ 7


0 _._ 6


0 _._ 5


0 _._ 4


0 _._ 3


0 _._ 2


0 _._ 1


0 _._ 0


_−_ 0 _._ 1



|VLA4A&B<br>beam|Col2|SO E up=24 K<br>2<br>HDO95K<br>NH 2CHO 79 K<br>North|
|---|---|---|
||||


_−_ 200 0 200 400 600
### Offset [au]


#### Vertical Profiles







Fig. 3 _Left_ _panel:_ Intensity profile of the HDO line at 241.56155 GHz (blue) and the SO 2 line at 241.615797 GHz (orange) extracted along the line
connecting VLA4A with VLA4B. The two vertical dashed lines show the position of VLA4A (black) and VLA4B (red). _Right_ _panel:_ Intensity profile
of the same lines extracted along the vertical line crossing the northern streamer. The vertical dashed lines show the position of VLA4A and VLA4B.



the half-life time _t_ _sub_ of the frozen species:


_t_ _sub_ = _ln_ (2) _/k_ des (1)


The rate of desorption _k_ des is given by the usual equation:


_k_ des = _ν_ _des_ exp( _−BE/T_ ) (2)


where BE is the binding energy, given in units of temperature, and
_ν_ _des_ is the pre-exponential factor, which depends on the adsorbate
and surface (e.g. [39,40] ).


Table 2 list the BE of HDO, SO 2 and NH 2 CHO over an amorphous water surface, as computed by [41] and [42] on a ice model of

60 water molecules. Note that the HDO BE was assumed to be

equal to that of H 2 O, an assumption demonstrated to be valid
by new computations of Tinacci et al. (submitted) on a large
(200 molecules) water ice grain. The table also reports the preexponential factor _ν_ of H 2 O and NH 2 CHO, computed by [39] following the [43] formalism (Table 5 of [39] ). The pre-exponential factor of
SO 2 was estimated by us using the formalism by [43] .


Figure 5 shows the derived sublimation temperature of deuterated water and formamide, for a time interval between 10 [3] and
10 [5] yr. We do not show the case of SO 2 for clarity reasons, since
its sublimation temperature would lie below that of HDO. The figure shows three sublimation temperature curves for each species,
corresponding to the average, minimum and maximum BE com


Species BE [K] _ν_ [s _[−]_ [1] ]
HDO 3605–6111 5 _×_ 10 [15]

SO 2 2105 – 5827 2 _×_ 10 [16]

NH 2 CHO 5793–10960 4 _×_ 10 [18]


Table 2 Binding energies (BE) and pre-exponential factor ( _ν_ ) used for
deriving the sublimation temperatures shown in Fig. 5. The BE are
from [41] and [42] . The pre-exponential factors are from [39] (see text). Note
that the second column reports minimum and maximum values of BE
computed on a amorphous water surface model of 60 molecules. Third
column reports the pre-exponential factor computed using the [43] method,
also described and discussed in [39] and [40] .


puted by [41] . Assuming that, in reality, BE has a distribution of
values approximately described by a gaussian (e.g. [45] ), the curve
corresponding to the average would represent where most of the
relevant molecules would thermally sublimate. While the HDO
being in the gaseous form is, in principle (see below) compatible
with thermal sublimation, formamide is not. The implication of
this fact will be discussed in the following subsection.


**5.2** **Accretion streamers feeding the disks**

The bolometric luminosity (L _bol_ ) of VLA4A and VLA4B is not measured singularly due to angular resolution limitations at infrared
wavelengths. The total bolometric luminosity of VLA4A+VLA4B
is estimated to be in the range 45-55 L _⊙_ [20,46] at the source dis

1–10 | 5

tance of 299 pc. The dust streamer traced by the continuum emission extends at a distance larger than 0 _._ _[′′]_ 4 (120 au). If we consider a spherical envelope-like distribution, and conservatively a
bolometric luminosity of 55 L _⊙_, the temperature at this distance
from the protostars is lower than 100 K (see e.g. [47] ). The presence of formamide at this position, considering the information
on the binding energies and the corresponding sublimation temperatures (see 5.1 and Fig. 5), suggests that formamide is not
thermally desorbed. In the case of HDO and SO 2 the binding energies are lower so their presence cannot exclude thermal desorption. If the continuum emission around the protostars originates
from an inclined disk (instead of a spherical envelope), as suggested by the observed geometry [18], the snowlines of NH 2 CHO,
HDO, and SO 2, would be even closer to the source. Therefore the
detection of molecules at a distance of _≥_ 120 au, would exclude
the thermal evaporation scenario.
However, episodic accretion is a common process in young stellar objects. More specifically, observations performed using the
Very Large Telescope, indicate that SVS13-A is in a phase of active
accretion, deriving a mass accretion rate of a few 10 _[−]_ [6] M _⊙_ yr _[−]_ [1][ 12]

(see also [48] ). The presence of an accretion burst is in principle expected to move the snowlines outwards and inject into the gas
phase the molecules stored in the dust mantles, as in the case of
the Fu Ori V833 disk [49] . However, at near-IR wavelengths VLA4A
is not detected [21], suggesting a negligible contribution to the bolometric luminosity which will be instead dominated by VLA4B [12] .
This is consistent with VLA4B being the primary and more massive component of the binary system, while VLA4A would be the
less massive secondary component. The process of differential
accretion in a binary system has been studied using numerical
simulations and the secondary is expected to accrete most of the
gas, except in the case of very eccentric orbits (e.g. [50,51] ). In this
scenario VLA4A would be the component actively accreting, and
the associated accretion burst may be at the origin of the detected
molecular emission associated with VLA4A. In order to definitely
exclude the possibility that thermal sublimation is responsible for
the chemical enrichment at distances larger than 120 au, it is

crucial to have an estimate of the individual VLA4A and VLA4B

luminosities.

Alternatively, the emission may be produced by an accretion shock, sputtering the grains, occurring when the accretion
streamer impacts the disk of VLA4A. This would also justify the

fact that the molecular emission shows emission at both blue
shifted and red-shifted velocities in the streamer (see Fig. 4),
which may be due to the velocity dispersion caused by the shock.
Indeed, a similar scenario has been proposed to explain SO, and
SO 2 emission where molecular streamers impact onto the disks
in Class I/II sources observed by the ALMA-DOT project [52] . Also
in these sources we observe both blue-shifted and red-shifted SO,
and SO 2 emission at the impact region.
Recently, the possible presence of **accretion** **shocks** **or** selfgravitating substructures (see e.g. [53] ) has been invoked to explain
local temperature enhancements in the circumbinary material of
the Class 0 source IRAS16293-2422 [54] . However, in the case
of SVS13-A the circumstellar disks around VLA4A and VLA4B,
as well as the circumbinary material are expected to be stable


6 | 1–10



against local gravitational instabilities, as found by [18] .
In summary, a major result of the presented observations is the
detection of molecular gas in the accretion streamer feeding the
system SVS13-A, on scales of _∼_ 100-200 au. Interestingly, an accretion streamer connecting the source to the outer envelope, up
to _∼_ 700 au has been recently imaged in DCN using the IRAM
NOEMA interferometer [55] . The detected DCN streamer is associ
ated with the southern dusty streamer, even though some emission is present also in the northern region (see their Fig. C.1).
However, the limited angular resolution of the NOEMA observations (synthesized beam of 1 _._ _[′′]_ 2 _×_ 0 _._ _[′′]_ 7) prevents a proper comparison with the ALMA continuum emission. Finally, the present
observations confirm that deuterated water and iCOMs, including formamide, are as effective as classical tracers such as SO and
SO 2, in revealing and investigating accretion processes in young

embedded Class 0/I disks.


6 Conclusions


We report new ALMA observations of HDO and SO 2 at a _∼_ 50 au
angular resolution of the protobinary system SVS13-A. The line
spatial distribution, as well as the radial and vertical profiles indicates that HDO and SO 2 are associated with both the two components of the binary system, VLA4A and VLA4B. We compare the
spatial distribution with that of NH 2 CHO, which instead mainly
trace the VLA4A component, confirming a chemical differentiation around the two protostars. In addition, the channel maps
of HDO emission reveal a further component at blue-shifted velocities (+2.42–4.39 km s _[−]_ [1] ) spatially coincident with the dust
accretion streamer. The streamer traced by HDO is located at a
distance _≥_ 120 au from the VLA4A and VLA4B protostars. Formamide is also detected at the same spatial position. In order to
investigate the origin of the molecular emission in the streamer,
we evaluate the thermal sublimation temperatures of deuterated
water, SO 2 and formamide, using updated BE distributions. We
find that a thermal sublimation origin of the molecular emission
is excluded, unless the VLA4A source is currently experiencing an
accretion burst. Alternatively, the emission morphology is consistent with an accretion shock, produced by an accretion streamer
impacting the VLA4A disk, as previously found in more evolved
protoplanetary disks. Finally, water has a key role in the planet
formation process and it is relevant to investigate its abundance
across the different evolutionary stages. The spatial distribution

of HDO in SVS13-A demonstrates that in Class I disks water is not

necessarily confined in the inner 10 au, as suggested by previous
ALMA and NOEMA H [18] 2 [O observations in 5 Class I disks] [56] [.] [In this]
respect, accretion processes are a powerful tool to investigate the
amount of water present in the young disks that will be eventually
inherited from the forming planetary systems.


Acknowledgements


This project has received funding from: 1) the Deutsche
Forschungsgemeinschaft (DFG, German Research Foundation)
under Germany´s Excellence Strategy – EXC 2094 – 390783311;
2) the European Research Council (ERC) under the European
Union’s Horizon 2020 research and innovation program, for
the Project “The Dawn of Organic Chemistry” (DOC), grant

agreement No 741002; 3) the PRIN-INAF 2016 The Cradle
of Life - GENESIS-SKA (General Conditions in Early Planetary Systems for the rise of life with SKA); 4) the European Union’s Horizon 2020 research and innovation programs under projects “Astro-Chemistry Origins” (ACO), Grant
No 811312. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2018.1.01461.S. ALMA is a partnership
of ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ. Most of the computations presented in this paper were performed using the GRICAD infrastructure (https://gricad.univ-grenoble-alpes.fr), which is partly
supported by the Equip@Meso project (reference ANR-10-EQPX29-01) of the programme Investissements d’Avenir supervised by
the Agence Nationale pour la Recherche.
_Software:_ astropy [57,58], matplotlib [59] .


Conflicts of interest


There are no conflicts to declare.


Notes and references


1 E. Bianchi, A. López-Sepulcre, C. Ceccarelli, C. Codella, L. Podio, M. Bouvier and
J. Enrique-Romero, _ApJL_, 2022, **928**, L3.
2 ALMA Partnership, C. L. Brogan, L. M. Pérez, T. R. Hunter, W. R. F. Dent,
A. S. Hales, R. E. Hills, S. Corder, E. B. Fomalont, C. Vlahakis, Y. Asaki,
D. Barkats, A. Hirota, J. A. Hodge, C. M. V. Impellizzeri, R. Kneissl, E. Liuzzo, R. Lucas, N. Marcelino, S. Matsushita, K. Nakanishi, N. Phillips, A. M. S.
Richards, I. Toledo, R. Aladro, D. Broguiere, J. R. Cortes, P. C. Cortes, D. Espada, F. Galarza, D. Garcia-Appadoo, L. Guzman-Ramirez, E. M. Humphreys,
T. Jung, S. Kameno, R. A. Laing, S. Leon, G. Marconi, A. Mignano, B. Nikolic,
L.-A. Nyman, M. Radiszcz, A. Remijan, J. A. Rodón, T. Sawada, S. Takahashi,
R. P. J. Tilanus, B. Vila Vilaro, L. C. Watson, T. Wiklind, E. Akiyama, E. Chapillon, I. de Gregorio-Monsalvo, J. Di Francesco, F. Gueth, A. Kawamura, C.-F. Lee,
Q. Nguyen Luong, J. Mangum, V. Pietu, P. Sanhueza, K. Saigo, S. Takakuwa,
C. Ubach, T. van Kempen, A. Wootten, A. Castro-Carrizo, H. Francke, J. Gallardo, J. Garcia, S. Gonzalez, T. Hill, T. Kaminski, Y. Kurono, H.-Y. Liu, C. Lopez,
F. Morales, K. Plarre, G. Schieven, L. Testi, L. Videla, E. Villard, P. Andreani, J. E.
Hibbard and K. Tatematsu, _ApJL_, 2015, **808**, L3.
3 P. D. Sheehan, J. J. Tobin, S. Federman, S. T. Megeath and L. W. Looney, _ApJ_,
2020, **902**, 141.
4 D. M. Segura-Cox, A. Schmiedeke, J. E. Pineda, I. W. Stephens, M. FernándezLópez, L. W. Looney, P. Caselli, Z.-Y. Li, L. G. Mundy, W. Kwon and R. J. Harris,
_Nature_, 2020, **586**, 228–231.
5 Ł. Tychoniec, J. J. Tobin, A. Karska, C. Chandler, M. M. Dunham, R. J. Harris, K. M. Kratter, Z.-Y. Li, L. W. Looney, C. Melis, L. M. Pérez, S. I. Sadavoy,
D. Segura-Cox and E. F. van Dishoeck, _ApJS_, 2018, **238**, 19.
6 A. Miotello, I. Kamp, T. Birnstiel, L. I. Cleeves and A. Kataoka, _arXiv_ _e-prints_,
2022, arXiv:2203.09818.
7 P. D. Sheehan, J. J. Tobin, L. W. Looney and S. T. Megeath, _ApJ_, 2022, **929**, 76.
8 K. I. Öberg and E. A. Bergin, _Phys. Rep._, 2021, **893**, 1–48.
9 C. Ceccarelli, C. Codella, N. Balucani, D. Bockelée-Morvan, E. Herbst, C. Vastel, P. Caselli, C. Favre, B. Lefloch and K. Öberg, _arXiv_ _e-prints_, 2022,
arXiv:2206.13270.

10 E. Herbst and E. F. van Dishoeck, _ARA&A_, 2009, **47**, 427–480.
11 C. Zucker, E. F. Schlafly, J. S. Speagle, G. M. Green, S. K. N. Portillo, D. P.
Finkbeiner and A. A. Goodman, _ApJ_, 2018, **869**, 83.
12 E. Fiorellino, C. F. Manara, B. Nisini, S. Ramsay, S. Antoniucci, T. Giannini,
K. Biazzo, J. Alcalà and D. Fedele, _A&A_, 2021, **650**, A43.
13 B. Reipurth, R. Chini, E. Krugel, E. Kreysa and A. Sievers, _A&A_, 1993, **273**,
221–238.

14 B. Lefloch, A. Castets, J. Cernicharo, W. D. Langer and R. Zylka, _A&A_, 1998,
**334**, 269–279.
15 C. Lefèvre, S. Cabrit, A. J. Maury, F. Gueth, B. Tabone, L. Podio, A. Belloche,
C. Codella, S. Maret, S. Anderl, P. André and P. Hennebelle, _A&A_, 2017, **604**,
L1.

16 G. Anglada, L. F. Rodríguez and J. M. Torrelles, _ApJL_, 2000, **542**, L123–L126.
17 C. Carrasco-González, G. Anglada, L. F. Rodríguez, J. M. Torrelles and M. Osorio,
_AJ_, 2008, **136**, 2238–2243.
18 A. K. Diaz-Rodriguez, G. Anglada, G. Blázquez-Calero, M. Osorio, J. F. Gómez,
G. A. Fuller, R. Estalella, J. M. Torrelles, S. Cabrit, L. F. Rodríguez, C. Lefèvre,



E. Macías, C. Carrasco-González, L. A. Zapata, I. de Gregorio-Monsalvo and
P. T. P. Ho, _ApJ_, 2022, **930**, 91.
19 L. F. Rodríguez, G. Anglada and S. Curiel, _ApJL_, 1997, **480**, L125–L128.
20 J. J. Tobin, L. W. Looney, Z.-Y. Li, C. J. Chandler, M. M. Dunham, D. Segura-Cox,
S. I. Sadavoy, C. Melis, R. J. Harris, K. Kratter and L. Perez, _ApJ_, 2016, **818**, 73.
21 K. W. Hodapp and R. Chini, _ApJ_, 2014, **794**, 169.
22 S. Cazaux, A. G. G. M. Tielens, C. Ceccarelli, A. Castets, V. Wakelam, E. Caux,
B. Parise and D. Teyssier, _ApJL_, 2003, **593**, L51–L55.
23 E. Bianchi, C. Codella, C. Ceccarelli, F. Vazart, R. Bachiller, N. Balucani, M. Bouvier, M. De Simone, J. Enrique-Romero, C. Kahane, B. Lefloch, A. LópezSepulcre, J. Ospina-Zamudio, L. Podio and V. Taquet, _MNRAS_, 2019, **483**, 1850–
1861.

24 C. Codella, C. Ceccarelli, E. Bianchi, L. Podio, R. Bachiller, B. Lefloch, F. Fontani,
V. Taquet and L. Testi, _MNRAS_, 2016, **462**, L75–L79.
25 M. De Simone, C. Codella, L. Testi, A. Belloche, A. J. Maury, S. Anderl, P. André,
S. Maret and L. Podio, _A&A_, 2017, **599**, A121.
26 B. Lefloch, R. Bachiller, C. Ceccarelli, J. Cernicharo, C. Codella, A. Fuente, C. Kahane, A. López-Sepulcre, M. Tafalla, C. Vastel, E. Caux, M. González-García,
E. Bianchi, A. Gómez-Ruiz, J. Holdship, E. Mendoza, J. Ospina-Zamudio, L. Podio, D. Quénard, E. Roueff, N. Sakai, S. Viti, S. Yamamoto, K. Yoshida, C. Favre,
T. Monfredini, H. M. Quitián-Lara, N. Marcelino, H. M. Boechat-Roberty and
S. Cabrit, _MNRAS_, 2018, **477**, 4792–4809.
27 A. Belloche, A. J. Maury, S. Maret, S. Anderl, A. Bacmann, P. André, S. Bontemps, S. Cabrit, C. Codella, M. Gaudel, F. Gueth, C. Lefèvre, B. Lefloch, L. Podio
and L. Testi, _A&A_, 2020, **635**, A198.
28 C. Ceccarelli, P. Caselli, F. Fontani, R. Neri, A. López-Sepulcre, C. Codella,
S. Feng, I. Jiménez-Serra, B. Lefloch, J. E. Pineda, C. Vastel, F. Alves, R. Bachiller,
N. Balucani, E. Bianchi, L. Bizzocchi, S. Bottinelli, E. Caux, A. Chacón-Tanarro,
R. Choudhury, A. Coutens, F. Dulieu, C. Favre, P. Hily-Blant, J. Holdship,
C. Kahane, A. Jaber Al-Edhari, J. Laas, J. Ospina, Y. Oya, L. Podio, A. Pon,
A. Punanova, D. Quenard, A. Rimola, N. Sakai, I. R. Sims, S. Spezzano,
V. Taquet, L. Testi, P. Theulé, P. Ugliengo, A. I. Vasyunin, S. Viti, L. Wiesenfeld
and S. Yamamoto, _ApJ_, 2017, **850**, 176.
29 Y.-L. Yang, N. Sakai, Y. Zhang, N. M. Murillo, Z. E. Zhang, A. E. Higuchi, S. Zeng,
A. López-Sepulcre, S. Yamamoto, B. Lefloch, M. Bouvier, C. Ceccarelli, T. Hirota,
M. Imai, Y. Oya, T. Sakai and Y. Watanabe, _ApJ_, 2021, **910**, 20.
30 J. P. McMullin, B. Waters, D. Schiebel, W. Young and K. Golap, in _CASA_ _Archi-_
_tecture and Applications_, ed. R. A. Shaw, F. Hill and D. J. Bell, 2007, vol. 376, p.
127.

31 J. K. Messer, F. C. De Lucia and P. Helminger, _Journal of Molecular Spectroscopy_,
1984, **105**, 139–155.
32 H. M. Pickett, R. L. Poynter, E. A. Cohen, M. L. Delitsky, J. C. Pearson and H. S. P.
Müller, _J. Quant. Spec. Radiat. Transf._, 1998, **60**, 883–890.
33 H. S. P. Müller, F. Schlöder, J. Stutzki and G. Winnewisser, _Journal of Molecular_
_Structure_, 2005, **742**, 215–227.
34 S. G. Kukolich and A. C. Nelson, _Chemical Physics Letters_, 1971, **11**, 383–384.
35 C. Ceccarelli, P. Caselli, D. Bockelée-Morvan, O. Mousis, S. Pizzarello, F. Robert
and D. Semenov, _Protostars and Planets VI_, 2014, 859–882.
36 R. T. Garrod, S. L. Widicus Weaver and E. Herbst, _ApJ_, 2008, **682**, 283–302.
37 D. Skouteris, F. Vazart, C. Ceccarelli, N. Balucani, C. Puzzarini and V. Barone,
_MNRAS_, 2017, **468**, L1–L5.
38 A. Fuente, P. Rivière-Marichalar, L. Beitia-Antero, P. Caselli, V. Wakelam,
G. Esplugues, M. Rodríguez-Baras, D. Navarro-Almaida, M. Gerin, C. Kramer,
R. Bachiller, J. R. Goicoechea, I. Jiménez-Serra, J. C. Loison, A. Ivlev,
R. Martín-Doménech, S. Spezzano, O. Roncero, G. Muñoz-Caro, S. Cazaux and
N. Marcelino, _A&A_, 2023, **670**, A114.
39 M. Minissale, Y. Aikawa, E. Bergin, M. Bertin, W. A. Brown, S. Cazaux, S. B.
Charnley, A. Coutens, H. M. Cuppen, V. Guzman, H. Linnartz, M. R. S. McCoustra, A. Rimola, J. G. M. Schrauwen, C. Toubin, P. Ugliengo, N. Watanabe,
V. Wakelam and F. Dulieu, _ACS Earth and Space Chemistry_, 2022, **6**, 597–630.
40 S. Ferrero, F. Grieco, A. S. Ibrahim Mohamed, F. Dulieu, A. Rimola, C. Ceccarelli,
C. Nervi, M. Minissale and P. Ugliengo, _MNRAS_, 2022, **516**, 2586–2596.
41 S. Ferrero, L. Zamirri, C. Ceccarelli, A. Witzel, A. Rimola and P. Ugliengo, _ApJ_,
2020, **904**, 11.
42 J. Perrero, J. Enrique-Romero, S. Ferrero, C. Ceccarelli, L. Podio, C. Codella,
A. Rimola and P. Ugliengo, _ApJ_, 2022, **938**, 158.
43 S. L. Tait, Z. Dohnálek, C. T. Campbell and B. D. Kay, _J. Chem. Phys._, 2005, **122**,
164708–164708.

44 E. Bianchi, C. Ceccarelli, C. Codella, A. López-Sepulcre, S. Yamamoto, N. Balucani, P. Caselli, L. Podio, R. Neri, R. Bachiller, C. Favre, F. Fontani, B. Lefloch,
N. Sakai and D. Segura-Cox, _A&A_, 2022, **662**, A103.
45 L. Tinacci, A. Germain, S. Pantaleone, S. Ferrero, C. Ceccarelli and P. Ugliengo,
_ACS Earth and Space Chemistry_, 2022, **6**, 1514–1526.
46 L. Podio, B. Tabone, C. Codella, F. Gueth, A. Maury, S. Cabrit, B. Lefloch,
S. Maret, A. Belloche, P. André, S. Anderl, M. Gaudel and L. Testi, _A&A_, 2021,
**648**, A45.
47 C. Ceccarelli, A. Castets, E. Caux, D. Hollenbach, L. Loinard, S. Molinari and
A. G. G. M. Tielens, _A&A_, 2000, **355**, 1129–1137.
48 T.-H. Hsieh, N. M. Murillo, A. Belloche, N. Hirano, C. Walsh, E. F. van Dishoeck,
J. K. Jørgensen and S.-P. Lai, _ApJ_, 2019, **884**, 149.
49 J.-E. Lee, S. Lee, G. Baek, Y. Aikawa, L. Cieza, S.-Y. Yoon, G. Herczeg, D. Johnstone and S. Casassus, _Nature Astronomy_, 2019, **3**, 314–319.
50 M. R. Bate and I. A. Bonnell, _MNRAS_, 1997, **285**, 33–48.


1–10 | 7

51 S. Ceppi, N. Cuello, G. Lodato, C. Clarke, C. Toci and D. J. Price, _MNRAS_, 2022,
**514**, 906–919.
52 A. Garufi, L. Podio, C. Codella, D. Segura-Cox, M. Vander Donckt, S. Mercimek,
F. Bacciotti, D. Fedele, M. Kasper, J. E. Pineda, E. Humphreys and L. Testi, _A&A_,
2022, **658**, A104.
53 K. Kratter and G. Lodato, _ARA&A_, 2016, **54**, 271–311.
54 M. J. Maureira, M. Gong, J. E. Pineda, H. B. Liu, K. Silsbee, P. Caselli, J. Zamponi, D. M. Segura-Cox and A. Schmiedeke, _ApJL_, 2022, **941**, L23.
55 T. H. Hsieh, D. M. Segura-Cox, J. E. Pineda, P. Caselli, L. Bouscasse, R. Neri,
A. Lopez-Sepulcre, M. T. Valdivia-Mena, M. J. Maureira, T. Henning, G. V.
Smirnov-Pinchukov, D. Semenov, T. Möller, N. Cunningham, A. Fuente,
S. Marino, A. Dutrey, M. Tafalla, E. Chapillon, C. Ceccarelli and B. Zhao, _A&A_,
2023, **669**, A137.
56 D. Harsono, M. V. Persson, A. Ramos, N. M. Murillo, L. T. Maud, M. R. Hogerheijde, A. D. Bosman, L. E. Kristensen, J. K. Jørgensen, E. A. Bergin, R. Visser,
J. C. Mottram and E. F. van Dishoeck, _A&A_, 2020, **636**, A26.
57 Astropy Collaboration, T. P. Robitaille, E. J. Tollerud, P. Greenfield, M. Droettboom, E. Bray, T. Aldcroft, M. Davis, A. Ginsburg, A. M. Price-Whelan, W. E.
Kerzendorf, A. Conley, N. Crighton, K. Barbary, D. Muna, H. Ferguson, F. Grollier,
M. M. Parikh, P. H. Nair, H. M. Unther, C. Deil, J. Woillez, S. Conseil, R. Kramer,
J. E. H. Turner, L. Singer, R. Fox, B. A. Weaver, V. Zabalza, Z. I. Edwards, K. Azalee Bostroem, D. J. Burke, A. R. Casey, S. M. Crawford, N. Dencheva, J. Ely,
T. Jenness, K. Labrie, P. L. Lim, F. Pierfederici, A. Pontzen, A. Ptak, B. Refsdal,
M. Servillat and O. Streicher, _A&A_, 2013, **558**, A33.
58 Astropy Collaboration, A. M. Price-Whelan, B. M. Sip˝ocz, H. M. Günther, P. L.
Lim, S. M. Crawford, S. Conseil, D. L. Shupe, M. W. Craig, N. Dencheva, A. Ginsburg, J. T. VanderPlas, L. D. Bradley, D. Pérez-Suárez, M. de Val-Borro, T. L.
Aldcroft, K. L. Cruz, T. P. Robitaille, E. J. Tollerud, C. Ardelean, T. Babej, Y. P.
Bach, M. Bachetti, A. V. Bakanov, S. P. Bamford, G. Barentsen, P. Barmby,
A. Baumbach, K. L. Berry, F. Biscani, M. Boquien, K. A. Bostroem, L. G. Bouma,
G. B. Brammer, E. M. Bray, H. Breytenbach, H. Buddelmeijer, D. J. Burke,
G. Calderone, J. L. Cano Rodríguez, M. Cara, J. V. M. Cardoso, S. Cheedella,
Y. Copin, L. Corrales, D. Crichton, D. D’Avella, C. Deil, É. Depagne, J. P. Dietrich, A. Donath, M. Droettboom, N. Earl, T. Erben, S. Fabbro, L. A. Ferreira,
T. Finethy, R. T. Fox, L. H. Garrison, S. L. J. Gibbons, D. A. Goldstein, R. Gommers, J. P. Greco, P. Greenfield, A. M. Groener, F. Grollier, A. Hagen, P. Hirst,
D. Homeier, A. J. Horton, G. Hosseinzadeh, L. Hu, J. S. Hunkeler, Ž. Ivezi´c,
A. Jain, T. Jenness, G. Kanarek, S. Kendrew, N. S. Kern, W. E. Kerzendorf,
A. Khvalko, J. King, D. Kirkby, A. M. Kulkarni, A. Kumar, A. Lee, D. Lenz, S. P. Littlefair, Z. Ma, D. M. Macleod, M. Mastropietro, C. McCully, S. Montagnac, B. M.
Morris, M. Mueller, S. J. Mumford, D. Muna, N. A. Murphy, S. Nelson, G. H.
Nguyen, J. P. Ninan, M. Nöthe, S. Ogaz, S. Oh, J. K. Parejko, N. Parley, S. Pascual, R. Patil, A. A. Patil, A. L. Plunkett, J. X. Prochaska, T. Rastogi, V. Reddy
Janga, J. Sabater, P. Sakurikar, M. Seifert, L. E. Sherbert, H. Sherwood-Taylor,
A. Y. Shih, J. Sick, M. T. Silbiger, S. Singanamalla, L. P. Singer, P. H. Sladen,
K. A. Sooley, S. Sornarajah, O. Streicher, P. Teuben, S. W. Thomas, G. R. Tremblay, J. E. H. Turner, V. Terrón, M. H. van Kerkwijk, A. de la Vega, L. L. Watkins,
B. A. Weaver, J. B. Whitmore, J. Woillez, V. Zabalza and Astropy Contributors,
_AJ_, 2018, **156**, 123.
59 J. D. Hunter, _Computing in Science & Engineering_, 2007, **9**, 90–95.


8 | 1–10

Fig. 4 _Upper panels:_ Channel map of the HDO(2 1 _,_ 1 _−_ 2 _,_ 2) emission (cyan contours) overlapped on the 1.2 continuum map of SVS13-A VLA4A and
VLA4B (see Fig. 1). Five velocity intervals have been considered (reported in the Top-Left corners). First contours and steps correspond to 5 _σ_
(20 mJy beam _[−]_ [1] km s _[−]_ [1] for all the channels but the most blue- and red-shifted ones, 16 mJy beam _[−]_ [1] km s _[−]_ [1] ), and 2 _σ_, respectively. The systemic
velocities are: +7.7 km s _[−]_ [1] (VLA4A), and +8.5 km s _[−]_ [1] (VLA4B). The synthesised beam (Bottom-Left) is 207 _×_ 136 mas (PA = +5 _[◦]_ ). _Middle panels:_
same as Upper for NH 2 CHO (12 1 _,_ 12 _−_ 11 1 _,_ 11 ). First contours and steps as for HDO. _Lower panels:_ same as Upper for SO 2 (5 2 _,_ 4 _−_ 4 1 _,_ 3 ). First contours
and steps as for HDO. In this case, only three velocity intervals can be drawn because of the contamination due to the CH 2 DOH(4 3 _,_ 1 _−_ 5 1 _,_ 5 )e1 line at
241.61928840 GHz, i.e. at –4.3 km s _[−]_ [1] from the SO 2 rest line (see Table 1).


1–10 | 9

Fig. 5 Sublimation temperature of deuterated water (HDO; red lines)
and formamide (NH 2 CHO; blue lines). The three curves for each species
correspond to the average (solid line), minimum and maximum (dashed
lines) BE computed by [41] and reported in Table 2 (see text). Note that
for the HDO we used the same BE of H 2 O, as demonstrated to be valid by
Tinacci et al. (submitted). The green area shows the grain temperature
derived by [44] assuming a bolometric luminosity of 55 L _o_ and a distance
from the center of 120 au (see text).


10 | 1–10


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "Pre-exponential factors (ν) of H2O and NH2CHO",
  "failed_quote": "The table also reports the pre-exponential factor ν of H 2 O and NH 2 CHO, computed by [39] following the [43] formalism (Table 5 of [39] )."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Pre-exponential factor formalism for thermal desorption rate calculation",
  "failed_quote": "The table also reports the pre-exponential factor ν of H 2 O and NH 2 CHO, computed by [39] following the [43] formalism (Table 5 of [39] )."
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "SO2 velocity intervals: 6.6-8.7, 8.9-10.4, and 10.5-11.9 km s^-1 (velocities < +6.5 km s^-1 excluded due to CH2DOH contamination)",
  "failed_quote": "SO 2 emission is also associated to both protostars in the velocity intervals 6.6-8.7 km s − 1, 8.9-10.4 km s − 1, and 10.5-11.9 km s − 1 ."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Compute the half-life time t_sub = ln(2)/k_des and desorption rate k_des = ν_des exp(-BE/T) for HDO, SO2, and NH2CHO over timescales of 10^3 to 10^5 yr using quantum chemical binding energy distributions and pre-exponential factors; compare sublimation curves with expected dust grain temperature at ≥ 120 au.",
  "failed_quote": "In order to distinguish which of the two hypothesis is correct, one has to evaluate the thermal sublimation temperature of deuterated water, SO 2 and formamide. To this end, we used the half-life time t sub of the frozen species: t sub = ln (2) /k des (1)"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[3].evidence[0]",
  "value": "Self-gravitating substructures causing local temperature enhancements (rejected because the disks and circumbinary material in SVS13-A are expected to be gravitationally stable).",
  "failed_quote": "Recently, the possible presence of accretion shocks or selfgravitating substructures (see e.g. [53] ) has been invoked to explain local temperature enhancements in the circumbinary material of the Class 0 source IRAS16293-2422 [54] . However, in the case of SVS13-A the circumstellar disks around VLA4A and VLA4B, as well as the circumbinary material are expected to be stable against local gravitational instabilities, as found by [18] ."
 }
]
```
