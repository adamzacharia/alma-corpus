# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.520.4089Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–14 (2022) Preprint 2 February 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **Millimeter-wave spectrum of 2-propanimine**


Luyao Zou, [1][⋆] Jean-Claude Guillemin, [2] Arnaud Belloche, [3] Jes K. Jørgensen, [4]

Laurent Margulès, [1] Roman A. Motiyenko [1] and Peter Groner [5]

1 _Univ. Lille, CNRS, UMR 8523 – PhLAM – Physique des Lasers Atomes et Molécules, F-59000 Lille, France_
2 _Univ Rennes, Ecole Nationale Supérieure de Chimie de Rennes, CNRS, ISCR-UMR 6226, F-35000 Rennes, France_
3 _Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany_
4 _Niels Bohr Institute, University of Copenhagen, Copenhagen, Denmark_
5 _Department of Chemistry, University of Missouri – Kansas City, 5100 Rockhill Rd., Kansas City, MO 64110, USA_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

Up to date, only 6 imines have been detected in the interstellar medium. The 3-carbon imine, 2-propanimine ((CH 3 ) 2 C−−NH),
is predicted to be the structural isomer with the lowest energy in the C 3 H 7 N group, and appears to be a good candidate for
astronomical searches. Unexpectedly, no microwave or millimeter wave spectrum is available for 2-propanimine. In this work,
we provide the first high resolution millimeter wave spectrum of 2-propanimine and its analysis. With the guide of this laboratory measurement, we aim to search for 2-propanimine in two molecule-rich sources Sgr B2(N) and IRAS 16293-2422 using
observations from the Atacama Large Millimeter/submillimeter Array (ALMA). Starting from a synthesized sample, we measured the spectrum of 2-propanimine from 50 to 500 GHz, and the ground state lines are successfully assigned and fitted using
XIAM and ERHAM programs with the aid of theoretical calculations. The barriers to internal rotation of the two CH 3 tops
are determined to be 531.956(64) cm [−][1] and 465.013(26) cm [−][1] by XIAM. These data are able to provide reliable prediction of
transition frequencies for astronomical search. Although a few line matches exist, no confirmed detection of 2-propanimine has
been found in the hot molecular core Sgr B2(N1S) and the Class 0 protostar IRAS 16293B. Upper-limits of its column density
have been derived, and indicate that 2-propanimine is at least 18 times less abundant than methanimine in Sgr B2(N1S), and is
at most 50–83 % of methanimine in IRAS 16293B.


**Key words:** astrochemistry - molecular data - ISM: molecules - methods: laboratory: molecular



**1** **INTRODUCTION**


In the interstellar medium (ISM), N-bearing compounds are important prebiotic molecules because of their link to the chemical
synthesis of amino acids, the building blocks of proteins (Holtom
et al. 2005). The chemistry of aliphatic amines [1] and imines [2] is not
well understood; their detection in the ISM is also limited to only
a few sources, in great contrast to their O-bearing counterparts alcohols [3], aldehydes [4], and ketones [5] . Up to date, only six imines (including geometric isomers) have been detected. The simplest methanimine (CH 2 NH) is observed in various types of sources (Godfrey
et al. 1973; Widicus Weaver et al. 2017). In the group of two carbon imines, ( _E_ )- and ( _Z_ )- ethanimine (CH 3 CH−−NH) (Loomis et al.


⋆ Current address: Laboratoire de Physico-Chimie de l’Atmosphère, Université du Littoral Côte d’Opale, 189 A Ave. Maurice Schumann, F-59140
Dunkerque, France. E-mail: luyao.zou@univ-littoral.fr
1 −
Organic molecules carrying a C N single bond.
2 Organic molecules carrying a C−−N double bound.
3 −
Organic molecules carrying a O H single bond and this C is not directly
connected to an aromatic ring
4 Organic molecules carrying a −CHO terminal, where C and O are con
nected with double bond.
5 Organic molecules carrying a C−−O double bond and this C is connected to

two other C atoms.


© 2022 The Authors



2013), and ( _E_ )- and ( _Z_ )- cyanomethanimine (NH−−CHCN) (Zaleski
et al. 2013), have been observed in the hot core Sgr B2(N). One
3-carbon imine, propargylimine (HCCCH−−NH), has been detected
in the quiescent cloud G+0.693-0.027 (Bizzocchi et al. 2020). All
observed imines belong to aldimines [6], which are analogous to the
structure of aldehydes. No ketimine [7], with a structure analogous
to that of ketone, has been discovered in space yet. For amines,
the simplest amine, methylamine (CH 3 NH 2 ), has been observed in
only four sources: Sgr B2(N) (Kaifu et al. 1974; Fourikis et al.
1974), G10.47+0.03 (Ohishi et al. 2019), NGC 6334F (Ohishi et al.
2019), and NGC 6334I (Bøgelund et al. 2019). Aminoacetonitrile
(NH 2 CH 2 CN) has been detected in Sgr B2(N) (Belloche et al. 2008).
The other three larger amines, vinylamine (C 2 H 3 NH 2 ) (Zeng et al.
2021), ethylamine (C 2 H 5 NH 2 ) (Zeng et al. 2021), and ethanolamine
(NH 2 CH 2 CH 2 OH) (Rivilla et al. 2021), have been recently detected
or tentatively detected in G+0.693-0.027.
The difficulty to detect amines and imines in the ISM prevents
us from further understanding their interstellar chemistry. To explore the possibility of detecting more amines and imines, Sil et al.
(2018) performed a survey of all isomeric groups of amines and


6 Imines where the C in the C−−N bond is connected to an H atom and a C

atom
7 Imines where the C in the C−−N bond is connected to two other C atoms

2 _L. Zou et al._


imines of one to three carbons using theoretical calculation. In
the C 3 H 7 N group, 2-propanimine, (CH 3 ) 2 C−−NH, is the most stable
structural isomer and is the simplest ketimine. Following the minimum energy principle (Lattelais et al. 2010), 2-propanimine is a
good interstellar molecule candidate. Sil et al. (2018) claimed that
(Z)-1-propanimine, which is 6.45 kcal/mol (equivalent to 3246 K)
higher in energy than 2-propanimine, has a higher chance of detection because of its larger dipole moment value and higher estimated abundance from astrochemical modeling. A recent search
for 1-propanimine, however, has reported nondetection in Sgr B2(N)
(Margulès et al. 2022). That being said, it is unreasonable to rule out
2-propanimine as a potential interstellar molecule, considering the
variety of physical and chemical environments in the ISM, and the
uncertainties of theoretical calculation and modeling. 2-propanimine

−
possesses a structure analogous to acetone, with an N H moiety replacing the O atom in acetone. Because acetone is a well-known
interstellar molecule detected in multiple hot core regions (Combes
et al. 1987; Snyder et al. 2002; Friedel et al. 2005; Friedel & Snyder
2008; Friedel & Widicus Weaver 2012; Peng et al. 2013; Rolffs et al.
2011; Isokoski et al. 2013; Zou & Widicus Weaver 2017; Suzuki
et al. 2018), low-mass and intermediate mass protostars (Jørgensen
et al. 2011; Lykke et al. 2017; Fuente et al. 2014), it is also interesting in the future to investigate the chemical similarity and difference
between 2-propanimine and acetone in the ISM.


From the spectroscopic point of view, 2-propanimine is a
molecule in _C_ _s_ molecular symmetry and is associated with two
slightly nonequivalent CH 3 internal rotors. The inequality arises

−
from the slightly tilted N H bond, which creates nonequivalent barriers to internal rotation of the two CH 3 tops. In such case, the tunnelling effect of internal rotation splits each rotational level into 9
components, with one non-degenerate state belonging to the _A_ 1 symmetry, and four doubly degenerate states belonging to the _E_ symmetry ( _E_ 1, _E_ 2, _E_ 3, and _E_ 4 ). Each rotational line thus splits into five components, which can be labeled by two symmetry numbers σ 1, σ 2,
or conventionally by symmetry labels _A_ and _E_ . These components
correspond to σ 1, σ 2 = (0, 0), (0, 1), (1, 0), (1, 1) and (1, 2), or correspondingly, the _AA_, _AE_, _EA_, _EE_, and _EE_ [′] states. The (1, 1) and
(1, 2) are in most cases degenerate, and they separate only at low _J_
and high _K_ _a_ . The relative weight of the five components is 2:2:2:1:1.
If we consider the spin statistics of the six H-atoms of the two CH 3
tops, the total spin statistical weight is then 16:16:16:8:8. Because
the barriers to internal rotation of the two CH 3 tops of 2-propanimine
are only slightly different, the tunnelling splittings caused by the two
tops are nearly equal for the ground state. Therefore, we expect to
see sets of almost evenly spaced quadruplets of equal intensity in the
spectra, except when the degeneracy of the (1, 1) and (1, 2) states is
lifted at low _J_ values to reveal the quintuplets.


Under terrestrial conditions, 2-propanimine is unstable and is
usually produced in pyrolysis (Zheng et al. 2003) or flame reactions (Tian et al. 2009). High resolution spectroscopic study of 2propanimine is still lacking, and surprisingly, even no microwave
studies of 2-propanimine are available to our knowledge. In this
study, we present the first high resolution millimeter-submillimeter
wave spectrum of 2-propanimine from a pure synthesized sample.
The pure sample, which is free from the inevitable contamination of
side products in pyrolysis and flame reactions, allows us to obtain
high quality rotational spectrum of 2-propanimine between 50 and
500 GHz.


MNRAS **000**, 1–14 (2022)



**2** **EXPERIMENTAL METHODS**


The 2-propanimine was synthesized from the reaction of KOH and
precursor 2-amino-2-methylpropanenitrile. The synthesized sample
was collected and preserved under dry ice temperature. Spectroscopic measurement was performed using the fast absorption spectrometer at Lille. Throughout the measurement, the sample was submerged in an ethanol cold bath at −60 °C, and a minimum flow
of the sample vapor was maintained between 8–20 µBar. Spectrum was measured between 50–110 GHz, 150–330 GHz, and 360–
500 GHz using commercial frequency amplifier-multiplier chains
and frequency modulation and second harmonics detection techniques. Quantum chemical calculation using Gaussian16 (Frisch
et al. 2016) was also performed to guide the spectral analysis by estimating the structure, rotational constants, dipole moments, and the
barriers to internal rotation of the two CH 3 groups of 2-propanimine.
The experimental spectrum was processed using a custom spectral
assignment software, and fitted using XIAM (Hartwig & Dreizler
1996; Herbers & Nguyen 2020) and ERHAM (Groner 1997, 2012)
programs with an iterative approach starting from the predicted spectrum from quantum chemical calculation. More technical details can
be found in Appendix A.


**3** **RESULTS AND DISCUSSION**


All quantum calculation methods produce similar equilibrium structures of 2-propanimine (see Appendix B1). The potential energy surface (PES) scan with the N−H bond twisting with respect to the
C−C(N)−C plane supports that the minimum energy structure is
when the N−H bond lies within the same plane of the carbon skeleton, leading to the _C_ _s_ symmetry of the molecule. Supplementary 2dimentional PES scan (see Appendix B2) also excludes other local
minimum structure than the global equilibrium structure. Figure 1
illustrates this optimized molecular structure of 2-propanimine, in
which we denote “top 1” and “top 2” for the two methyl tops here
−
inafter. “Top 1” is the CH 3 group pointing away from the N H bond,

−
and “top 2” is the one facing to the N H bond. Dipole moment calculation gives µ _a_ = 1.37 D and µ _b_ = −2.06 D (MP2 value), which
correspond to _a_ - and _b_ - type rigid rotor selection rules. We note that
the dipole moment values reported by Sil et al. (2018) were erroneously taken from the initial structure of the molecule before geometry optimization, and therefore should not be used. We also show
evidence that the normal _c_ - type transitions, which correspond to a
non-zero µ _c_ dipole moment component, do not exist in the experimental spectra. More technical analysis on the _c_ - type selection rules
are discussed in Appendix B3.
In total, we identified 27,259 torsional-rotational transitions and
9,349 distinct line frequencies in our spectral analysis. The highest
upper state _J_ and _K_ _a_ accessed are 52, 26 for _R_ branch lines, and 64,
34 for _Q_ branch lines. The spectrum measured between 50 and 110
GHz was extremely useful because it accessed a large number of _Q_
branch transitions with high _J_ and _K_ _a_ values. All transition frequencies, uncertainties and relative weights used in the fit are listed in
Table 1. Typical _a_ -type and _b_ -type _R_ and _Q_ lines are plotted against
the predicted frequencies from the best fit in Figure 2.
The fit results with XIAM and ERHAM are both listed in Table 2. The XIAM fit produces a microwave root-mean-square (r.m.s.)
of 78.0 kHz and a dimensionless standard deviation of 1.38. The

ERHAM fit produces a lower microwave r.m.s. of 53.5 kHz and a
dimensionless standard deviation of 0.69. Detailed statistical anal
ysis (see Appendix B4) shows that the ERHAM model reaches ex

_MmW spectrum of 2-PA_ 3


**Table 1.** Measured and assigned transitions of 2-propanimine. [(1)]


_J_ [′′] _K_ _a_ [′′] _K_ _c_ [′′] σ 1 _J_ [′] _K_ _a_ [′] _K_ _c_ [′] σ 2 ν obs (MHz) Uncertainty (MHz) Weight [(2)] ν obs − ν calc (MHz) [(3)]


3 3 1 1 2 2 0 2 53833.392 0.050 1.000 0.0474

3 3 1 1 2 2 0 1 53834.919 0.050 1.000 0.0397

3 3 1 0 2 2 0 1 53837.233 0.025 1.000 0.0263

3 3 1 1 2 2 0 0 53840.874 0.025 1.000 −0.0103

3 3 1 0 2 2 0 0 53843.939 0.025 1.000 −0.0373


**Notes.** [(1)] The full table is available in machine-readable format in the online supplementary material. [(2)] Weight used in fitting blended transitions. Weight is
proportional to the line intensity and normalized to unity for all blended transitions associated with a single frequency. [(3)] ν calc obtained from the best ERHAM
fit parameters (see Table 2).



Vibrationally excited state ✶



23 11,12 ← 22 12,11



23 12,12 ← 22 11,11



23 12,12 ← 22 12,11



23 11,12 ← 22 11,11



318960 318970 318980 318990 319000 319010


Frequency (MHz)



43 10,34 ← 43 8,35
43 9,34 ← 43 8,35



43 10,34 ← 43 9,35
43 9,34 ← 43 9,35



**Figure 1.** Optimized molecular structure of 2-propanimine. “Top 1” refers to
the CH 3 group away from the N−H bond, and “top 2” refers to the one close
to the N−H bond. Atoms N1, C2, C4, C8, H3, H5, and H9 are all in the same
plane, which is the symmetry plane of the molecule. Atoms H6 and H7 are
symmetric with respect to this plane, as are atoms H10 and H11.


perimental accuracy, whereas the XIAM model cannot reach experimental accuracy because of the limited number of high order correction terms available in the model. The goodness of the fit and
the torsional splitting pattern can also be visualized in Figure 3,
where we plot the torsional splitting among the five components as
a function of the upper state _J_ [′′] and _K_ _c_ [′′] [. In this figure, the center fre-]
quency ( _f_ _c_ ) of each _J_ [′′] level is calculated from the weighted average
of the observed line frequencies of the five torsional components.
Then the observed line frequencies are plotted as the deviation from
this center frequency with ±3σ error bars. The predicted frequencies from the ERHAM fit are plotted as continuous curves. These
curves follow nicely with the observed frequencies within their uncertainty range. For most _J_ [′′] values, the (1, 1) and (1, 2) components
are merged, leaving four components symmetric around the center
frequency. When _K_ _c_ [′′] [becomes] [su][ffi][ciently] [small,] [the] [splitting] [be-]
tween (1, 1) and (1, 2) states becomes visible. In the figure, it is
shown as the separation of the curve in pale pink (the (1, 1) component) from the curve in blue (the (1, 2) component). The torsional
splitting pattern of the _R_ branch is relatively simple. The splitting
is maximized at medium _J_ [′′] value, and decreases with both the increase and decrease of _J_ [′′] . The torsional splitting pattern of the _Q_
branch is more complicated. As _J_ [′′] decreases, the splitting first decreases to zero where the five components cross each other, and then
the splitting increases again. This trend repeats three times to create
three cross-overs of the five components. It is also interesting to ex


(1,1)
(0,1) (1,0) (0,0)
(1,2)


291935 291940 291945 291950 291955


Frequency (MHz)


**Figure 2.** Spectrum of 2-propanimine with the characteristic quadruplets due
to torsional splitting. The vertical sticks represent the predicted frequencies
of the transitions from the final ERHAM fit. _R_ branch lines are plotted on
the top panel, and _Q_ branch lines are plotted on the bottom panel. In the _R_
branch panel, sticks in blue represent _b_ -type transitions, whereas sticks in
pink represent _a_ -type transitions. In the _Q_ branch panel, _a_ -type and _b_ -type

transitions become blended.


amine the separation of the torsional splitting from the molecule’s
overall asymmetric rotation. If we assume that there were no torsional splitting from internal rotation, the imagined pure rotational
transition of 2-propanimine would be the _f_ _c_ . We generated a line
list from _f_ _c_ and fitted it to a simple Watson’s A reduction Hamiltonian in _I_ _[r]_ representation using the CALPGM/SPFIT program (Pickett 1991). Then, the frequency difference from the fit is denoted as
∆ _f_ and plotted as dark green solid curves in Figure 3. The almost
invisible ∆ _f_ shows that indeed an asymmetric rotor model is able to
describe the averaged center frequencies _f_ _c_ of the torsional splitting

components.
Both XIAM and ERHAM fits determine well the parameters of


MNRAS **000**, 1–14 (2022)

4 _L. Zou et al._


**Table 2.** Spectroscopic parameters of 2-propanimine obtained from XIAM and ERHAM fit and from theoretical calculation.


Overall rotation Unit XIAM ERHAM Tunneling Unit ERHAM
parameters parameters [(1)]


_A_ MHz 9709.08619(11) 9709.082826(66) ϵ 01 MHz −64.4590(86)
_B_ MHz 8479.04382(16) 8478.033891(58) ϵ 02 MHz −0.0226(36)
_C_ MHz 4788.51105(14) 4789.524383(54) ϵ 10 MHz −30.0609(79)
∆ _J_ kHz 4.671205(73) 4.673412(56) ϵ 12 MHz 0.0204(33)
∆ _JK_ kHz −5.47595(24) −5.47338(14) _qq_ [′] = 01 _qq_ [′] = 10
∆ _K_ kHz 10.46953(39) 10.44279(23) [g _a_ ] _qq_ ′ MHz 0.04253(92) −0.00335(92)
δ _J_ kHz 1.982110(24) 1.982158(15) [ _D_ _ab_ ] _qq_ ′ MHz 0.0444(85) 0.0416(90)
δ _K_ kHz 0.826549(90) 0.829265(63) [ _A_ − ( _B_ + _C_ )/2] _qq_ ′ kHz 3.671(67) 2.042(66)
Φ _J_ Hz 0.005608(21) 0.006205(17) [( _B_ + _C_ )/2]] _qq_ ′ kHz −1.691(38) −1.146(41)
Φ _JK_ Hz −0.00536(12) −0.000357(69) [( _B_ − _C_ )/4] _qq_ ′ kHz −0.376(21) −0.353(23)
Φ _KJ_ Hz −0.04460(40) −0.06331(22) [∆ _J_ ] _qq_ ′ Hz 0.910(16) 0.451(17)
Φ _K_ Hz 0.08289(52) 0.08478(33) [∆ _JK_ ] _qq_ ′ Hz −2.456(56) −1.085(60)
φ _J_ Hz 0.0027909(75) 0.0030980(46) [∆ _K_ ] _qq_ ′ Hz 1.667(56) 0.620(59)
φ _JK_ Hz 0.011037(58) 0.014644(38) [δ _J_ ] _qq_ ′ Hz 0.4987(82) 0.2390(86)
φ _K_ Hz −0.00344(15) −0.007352(88) [δ _K_ ] _qq_ ′ Hz −1.042(16) −0.453(17)


Internal rotation Unit Top 1 Top 2
parameters XIAM ERHAM XIAM ERHAM


_V_ 3 cm [−][1] 531.956(64) 531.394 [(2)] 465.013(26) 462.284 [(2)]

ρ 0.0597139(75) 0.059652(20) 0.0591996(34) 0.0589308(90)
_F_ cm [−][1] 5.60425 [(3)] 5.6016(20) 5.62699 [(3)] 5.64411(87)
β [(4)] degree 26.3833 [(3)] 27.032(23) 151.6718 [(3)] 151.1511(91) [(6)]

α [(5)] degree 0 [(7)] 0 [(7)] 0 [(7)] 0 [(7)]

∠( _i_, _a_ ) [(8)] degree 29.5966(49) 30.299(24) 148.3136(24) 147.7540(97)
∠( _i_, _b_ ) [(8)] degree 60.4034(49) 59.701(24) 58.3136(24) 57.7540(97)
∠( _i_, _c_ ) [(8)] degree 90.0 [(7)] 90.0 [(7)] 90.0 [(7)] 90.0 [(7)]

∆ _pi_ 2 _J_ [(9)] MHz 0.0372(38) 0.1351(18)
∆ _pi_ 2 _K_ [(9)] MHz −0.158(12) −0.6502(58)
∆ _pi_ 2− [(9)] MHz 0.0201(28) 0.0538(13)


Fit Statistics Unit XIAM ERHAM


_n_ [(10)] 9349 9349
_N_ [(11)] 27259 27259
σ MW [(12)] kHz 78.0 53.5
σ w [(13)] 1.38 0.69


**Notes.** [(1)] Parameters only available in ERHAM. [(2)] Approximate values derived from program “BARRIER” using torsional energy differences. No statistical
standard deviation is available because there is no degree of freedom in the data set. (3) Values derived from XIAM and no statistical standard deviation is
available. (4) Polar angle between the ρ vector axis and the _a_ principal axis. (5) Azimuthal angle between the ρ vector axis and the _b_ principal axis. (6) In
ERHAM, the angle in the input file is the supplementary angle of β. [(7)] Fixed. [(8)] Angle between the internal rotor symmetry axis and the _a_, _b_, or _c_ principal
axis. [(9)] Parameters only available in XIAM. [(10)] Number of individual line frequencies. [(11)] Number of assigned transitions. [(12)] Microwave root-mean-square
of the fit [ [�] ((ν obs − ν calc )/w) [2] / [�] ((1/w) [2] )] [1][/][2] . [(13)] Dimensionless standard deviation of the fit [ [�] ((ν obs − ν calc )/w) [2] / _N_ ] [1][/][2] .



the molecule’s overall rotation, including the rotational constants
and the full set of quartic and sextic centrifugal distortion constants.
The parameters from these two fits agree well with each other, except
the _B_ and _C_ constants which differ by ∼1 MHz. It is not surprising
because the two programs treat the internal rotation differently, and
therefore may introduce different “effective” rotational constants introduced by the internal rotors into the _B_ and _C_ constants. For the internal rotation part, we note that XIAM and ERHAM are two different types of models, and therefore they do not share the exact same
set of parameters. XIAM fits directly the _V_ 3 barrier, the ρ parameter, the angle between the internal rotor axis and the ρ axis of the
molecule (β), and the three internal rotational correction parameters
∆ _pi_ 2 _J_, ∆ _pi_ 2 _K_, and ∆ _pi_ 2− . The _V_ 3 barriers to internal rotation of the two
rotors are determined to be 531.956(64) cm [−][1] and 465.013(26) cm [−][1],
respectively. ERHAM also fits the ρ and the angle parameters, but
it does not directly fit the barriers to internal rotation. Instead, it fits


MNRAS **000**, 1–14 (2022)



the tunneling parameters ϵ 01, ϵ 10, etc., and the correction terms for
each individual rotor. The _V_ 3 barriers are derived from the above parameters (Groner et al. 1986), and the results are 531.394 cm [−][1] and
462.284 cm [−][1], respectively. These values are lower than the XIAM
fitted values by less than 3 cm [−][1] . The ρ and ∠( _i_, _a_ ) determined by the
two fits also agree well with each other.
We compare several molecular structure parameters and the barriers to internal rotation of the two methyl tops from the spectral
fit with theoretical calculation values in Table 3. The calculation
systematically over-predicts the _A_, _B_, _C_ rotational constants with
<1.5 % error. MP2 predicts the most accurate _A_ constant, whereas
B3LYP predicts the most accurate _B_ and _C_ constants. For the _V_ 3 barriers, Figure 4 shows the 1-dimensional PES scans using different
level of theories. Overall, the calculated _V_ 3 barriers derived from the
PES scans agree with the experimentally fitted values within 10 %
difference. MP2 and MN15 return values closer to experimentally

_MmW spectrum of 2-PA_ 5







|(0,0) (0,1) (1,0) (1,1) (1,2)|Col2|Col3|
|---|---|---|
|15<br> 20<br> 25<br> 30<br> 35<br> 40<br> 45<br>R−branch,_a_−type<br>_K_a″=11<br>_K_a″+_K_c″ =_J_ ″+1<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|15<br> 20<br> 25<br> 30<br> 35<br> 40<br> 45<br>R−branch,_a_−type<br>_K_a″=11<br>_K_a″+_K_c″ =_J_ ″+1<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|15<br> 20<br> 25<br> 30<br> 35<br> 40<br> 45<br>R−branch,_a_−type<br>_K_a″=11<br>_K_a″+_K_c″ =_J_ ″+1<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|
|15<br> 20<br> 25<br> 30<br> 35<br> 40<br> 45<br>R−branch,_a_−type<br>_K_a″=11<br>_K_a″+_K_c″ =_J_ ″+1<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|R−branch,_a_−type<br>_K_a″=11<br>_K_a″+_K_c″ =_J_ ″+1||


30



35





30


25



700


600


500


400


300


200


100


0



20


15


10


5


−15 −10 −5 0 5 10 15

Splitting (MHz)



−180 −120 −60 0 60 120 180


Dihedral Angle (deg)









40


35


30


25


20


15


10


5



600


500


400


300


200


100


|(0,0) (0,1) (1,0) (1,1) (1,2)|Col2|Col3|
|---|---|---|
|0<br> 35<br> 40<br> 45<br> 50<br> 55<br> 60<br>Q−branch,_b_−type<br>_K_a″=25<br>_K_a″=_K_a′ + 1<br>_K_a″+_K_c″ =_J_ ″<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|0<br> 35<br> 40<br> 45<br> 50<br> 55<br> 60<br>Q−branch,_b_−type<br>_K_a″=25<br>_K_a″=_K_a′ + 1<br>_K_a″+_K_c″ =_J_ ″<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|0<br> 35<br> 40<br> 45<br> 50<br> 55<br> 60<br>Q−branch,_b_−type<br>_K_a″=25<br>_K_a″=_K_a′ + 1<br>_K_a″+_K_c″ =_J_ ″<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|
|0<br> 35<br> 40<br> 45<br> 50<br> 55<br> 60<br>Q−branch,_b_−type<br>_K_a″=25<br>_K_a″=_K_a′ + 1<br>_K_a″+_K_c″ =_J_ ″<br>(,)<br>(,)<br>(,)<br>(,)<br>(,)|Q−branch,_b_−type<br>_K_a″=25<br>_K_a″=_K_a′ + 1<br>_K_a″+_K_c″ =_J_ ″||



−15 −10 −5 0 5 10 15

Splitting (MHz)


**Figure** **3.** Torsional splitting patterns for (top) _a_ -type, R-branch, _K_ _a_ [′′] [=] [11,]
_K_ _a_ [′′] [+] _[K]_ _c_ [′′] = _J_ [′′] + 1 series; and (bottom) _b_ -type, Q-branch, _K_ _a_ [′′] = 25,
_K_ _a_ [′′] = _K_ _a_ [′] [+] [1,] [and] _[K]_ _a_ [′′] [+] _[K]_ _c_ [′′] = _J_ [′′] . The horizontal axis is the shift of
each torsional splitting component from the center frequency _f_ _c_, which is
the weighted average of the frequencies of all splitting components. The predicted frequency of each component is plotted as a solid curve, and the experimental values are marked as error bars with ±3 times the assigned measurement uncertainty. The dark green solid curve in the center is ∆ _f_, the
difference between _f_ _c_ and its asymmetric rotor fit result.


fitted values than B3LYP or M062X. MP2 overestimates the barriers, whereas DFT methods underestimate the barriers. MN15 is
an outlier in predicting the energy difference of the two barriers as
the difference is significantly underestimated compared to the other
methods. All calculations predict similar moment of inertia of the
CH 3 tops _I_ α, which is smaller than the experimentally fitted value.
The difference is expected because the experiment fits the effective
structure, whereas calculation predicts equilibrium structures that
lack the contribution from vibrational deformation. The smaller cal
culated _I_ α values also lead to higher calculated ρ. The angle between
the internal rotation axis and _a_ principal axis is systematically underestimated by a few degrees. Based on these comparisons, we may
consider that the MP2/aug-cc-pVTZ method predicts the parameters
with the smallest averaged error to experimental fitted values. It is

−
interesting that “top 2”, the CH 3 top closer to the N H bond, has the
lower _V_ 3 barrier.
Using the ERHAM fit, we generated a prediction of the transition frequencies of 2-propanimine up to _J_ [′′] = 80 and 1 THz. We
used the dipole moments from the MP2 calculation to calculate
the line strength. The predicted transition frequencies, along with
their uncertainties derived from the uncertainties of fitted parameters, are listed in Table 4 and also available in machine-readable
format at CDS (reference J/MNRAS/Vol/Page) and also at the Lille
Spectroscopic Database [8] (Motiyenko & Margulès 2022). Neverthe

8 https://lsd.univ-lille.fr/



0


−180 −120 −60 0 60 120 180


Dihedral Angle (deg)


**Figure 4.** The 1-dimension PES of “top 1” (top panel) and “top 2” (bottom
panel) CH 3 internal rotation in 2-propanimine.


less, the predicted frequencies of transitions not accessed by this
experiment should still be viewed with caution because the high
order terms in the ERHAM fit may be highly correlated and subject to large fluctuation if more spectral data were accessible. The
torsional-rotational partition function _Q_ ( _T_ ) was calculated by direct
summation of Boltzmann factors up to _J_ [′′] = 120 (maximum _J_ allowed in ERHAM) and listed in Table 5. We note that the partition
function and the upper state degeneracy listed in Table 4 are correlated and affected by the choice of spin statistics. If we consider
the full spin weight of the 6 H-atoms in the two methyl tops, the
total spin weight is 2 [6] = 64. The upper state degeneracies of the
(σ 1, σ 2 ) = (0, 0), (0, 1)(1, 0)(1, 1)(1, 2) torsional states will then be
16, 16, 16, 8, 8 times the rigid rotor state degeneracy, respectively.
On the other hand, the CALPGM/SPCAT format of the prediction
uses 3 columns to label the upper state degeneracy, and therefore
has a plafond of 999. For high _J_ states, the consideration of full spin
statistics leads to degeneracies exceeding 999. For this practical reason, we used a reduced spin weight of 2:2:2:1:1 for the five torsional
states. The total spin weight reduces from 64 to 8, and therefore the
partition function also reduces to 1/8 of the full spin weight case. The
logarithm line strength remains unchanged. To correctly calculate
line intensities using our prediction, it is necessary to choose the correct pair of spin weight and partition function. Furthermore, vibrational partition function can be estimated using the vibrational energies listed in Table B5, and combined with the torsional-rotational
partition function to provide more accurate line intensity estimation
under elevated temperature.
Harmonic vibrational frequency calculations predict that two torsional excited states lie around 100–200 cm [−][1] above the ground
state. By examining the derivative of normal coordinates, we can
associate these two excited states to the torsional motion of the two

methyl tops. The exact values of state energies are subject to some
uncertainty due to the level of theory used in the calculation. If


MNRAS **000**, 1–14 (2022)

6 _L. Zou et al._


**Table 3.** Comparison of molecular structure parameters between fit and calculation.


Parameter Unit ERHAM fit XIAM fit B3LYP M062X MN15 MP2


_A_ MHz 9709.082826(66) 9709.08619(11) 9757.1877 9780.7341 9771.8994 9721.3053
_B_ MHz 8478.033891(58) 8479.04382(16) 8508.6190 8573.1854 8584.7372 8559.6800
_C_ MHz 4789.524383(54) 4788.51105(14) 4813.2847 4839.8416 4841.0024 4821.2849
_V_ 3 (top 1) cm [−][1] 531.394 531.956(64) 489.49 494.03 511.30 547.64
_V_ 3 (top 2) cm [−][1] 462.284 465.013(26) 435.52 432.16 479.90 497.47
ρ (top 1) 0.059652(20) 0.0597139(75) 0.0602179 0.0604033 0.0603622 0.0600987
ρ (top 2) 0.0589308(90) 0.0591996(34) 0.0599404 0.0601071 0.0600893 0.0598149
2
_I_ α (top 1) amu·Å 3.2034(12) 3.20231(40) 3.123812 3.125991 3.126738 3.129077
2
_I_ α (top 2) amu·Å 3.17675(52) 3.18760(19) 3.109383 3.110658 3.112605 3.114300
∠( _i_, _a_ ) (top 1) degree 30.299(24) 29.5966(49) 25.756 25.482 24.612 26.627
∠( _i_, _a_ ) (top 2) degree 147.7540(97) 148.3136(24) 152.131 151.704 150.794 152.821
µ _a_ [(1)] Debye 1.3216 1.3142 1.2797 1.3711
µ _b_ [(1)] Debye −2.1122 −2.1066 −2.1242 −2.0643
ν 27 [(2)] cm [−][1] 122.447 114.190 126.645 119.892
ν 26 [(2)] cm [−][1] 178.662 183.843 185.232 183.404


**Notes.** [(1)] The vibrational averaged dipole moment at 298 K. [(2)] Harmonic vibrational energy.


**Table 4.** Prediction of 2-propanimine transitions up to _J_ [′′] = 80 and 1 THz using the ERHAM fit and reduced spin weight. Prediction uses dipole moment values
from the MP2/aug-cc-pVTZ calculation, and the table follows the CALPGM/SPCAT format. [(1)]


FREQ UNC LOGINT [(2)] DR ELO GUP [(3)] TAG QNFMT _J_ [′′] _K_ _a_ [′′] _K_ _c_ [′′] σ 1 _J_ [′] _K_ _a_ [′] _K_ _c_ [′] σ 2


17162.6416 0.0009 −6.5439 3 20.1322 34 57803 1404 8 6 2 0 8 5 3 1

17165.2573 0.0010 −6.5437 3 20.1294 34 57803 1404 8 6 2 1 8 5 3 0

17168.1874 0.0011 −6.5436 3 20.1269 34 57803 1404 8 6 2 0 8 5 3 0


**Notes.** [(1)] The full table is available in machine-readable format in the online supplementary material, as well as the CDS database (reference
J/MNRAS/Vol/Page) and Lille Spectroscopic database. [(2)] Intensity calculated using reduced partition function _Q_ = 353614.251 at 300 K. (3) To get full
spin weight of 6-H atoms, multiply this degeneracy by 8. The partition function should also be multiplied by 8 to get correct line intensity calculation.



**Table 5.** Rotational partition function of 2-propanimine from direct summation of Boltzmann factors up to _J_ = 120.


Temperature (K) _Q_ full [(1)] _Q_ red [(2)]


300 2828914.006 353614.251

225 1836813.509 229601.689

150 999569.239 124946.155

75 353416.309 44177.039

37.5 125041.237 15630.155

18.75 44286.338 5535.792

9.38 15727.703 1965.963

5.00 6160.952 770.119


**Notes.** [(1)] Partition function with full spin weight of 6-H atoms, total weight
2 [6] = 64. [(2)] Partition function with reduced spin weight, total weight 2 [3] = 8.


we take the MP2/aug-cc-pVTZ value based on its best agreement
of overall rotation and internal rotation parameters to experimentally fitted values, the energy of the two torsional excited states are
120 cm [−][1] and 183 cm [−][1], respectively, or 134 cm [−][1] and 171 cm [−][1]

with anharmonic correction. They correspond to 40–60 % of the
ground state population under 300 K. Under typical interstellar tem
∼
perature ( 150–200 K for hot cores), the intensity of the lines from
these excited states are expected to be less than 30 % of the ground
state lines. The search for these excited state lines may help the
identification of the molecule when ground state lines are heavily
blended with lines from other molecules, if the ground state lines


MNRAS **000**, 1–14 (2022)



themselves are sufficiently bright. In our laboratory spectra, we observed numerous lines from these two states with intensities con
sistent with our expectations. The analysis of these excited states,
however, is complicated due to their Coriolis coupling. To correctly
model the lines from these excited states, it is necessary to perform
a global analysis of them together with the ground state lines. The
global analysis, however, cannot be treated straightforwardly with
the tools we used to analyze the ground state. In this regard, we focus only on the analysis of and astronomical search for the ground
state lines in the current manuscript. The global spectroscopic modeling of these interacting torsional excited states and the search for
these lines in the ISM will be the subject of future study.


**4** **SEARCH FOR 2-PROPANIMINE IN THE ISM**


**4.1** **Search toward Sgr B2(N1)**


We used the imaging spectral line survey Reexploring Molecular Complexity with ALMA (ReMoCA) that targeted the highmass star forming protocluster Sgr B2(N) with ALMA. Details
about the observations and data reduction can be found in Belloche

et al. (2019). We summarize here the main features of the survey.
The phase center is located at the equatorial position (α, δ) J2000 =
(17 [h] 47 [m] 19 [s] .87, −28 [◦] 22 [′] 16 [′′] . 0). This position is half-way between the
two hot molecular cores Sgr B2(N1) and Sgr B2(N2). We covered
the frequency range from 84.1 GHz to 114.4 GHz at a spectral resolution of 488 kHz (1.7 to 1.3 km s [−][1] ) using five different frequency

tunings. The survey achieved a sensitivity per spectral channel that
varies between 0.35 mJy beam [−][1] and 1.1 mJy beam [−][1] (rms) depending on the setup, with a median value of 0.8 mJy beam [−][1] . The observations have an angular resolution (HPBW) ranging from ∼0.3 [′′]

to ∼0.8 [′′] with a median value of 0.6 [′′] that corresponds to ∼4900 au
at the distance of Sgr B2 (8.2 kpc, Reid et al. 2019). We used here
an improved version of the data reduction, as described in Melosso
et al. (2020).


We followed the same strategy as Belloche et al. (2019) and analyzed the spectrum obtained toward the position Sgr B2(N1S) at
(α, δ) J2000 = (17 [h] 47 [m] 19 [s] .870, −28 [◦] 22 [′] 19 [′′] . 48). This position is offset
by about 1 [′′] to the south of the main hot core Sgr B2(N1) and has a
lower continuum opacity compared to the peak of the hot core. The
observed spectrum was compared to synthetic spectra computed under the assumption of local thermodynamic equilibrium (LTE) with
the astronomical software Weeds (Maret et al. 2011). This assumption is justified by the high densities of the regions where hot-core
emission is detected in Sgr B2(N) (> 1×10 [7] cm [−][3], see Bonfand et al.
2019). We derived by hand a best-fit synthetic spectrum for each
molecule separately, and then added together the contributions of all
identified molecules. Each species was modeled with a set of five parameters: size of the emitting region (θ s ), column density ( _N_ ), temperature ( _T_ rot ), linewidth (∆ _V_ ), and velocity offset ( _V_ off ) with respect
to the assumed systemic velocity of the source, _V_ sys = 62 km s [−][1] .


The molecules included in the complete model comprise in particular those listed in Belloche et al. (2013). The linewidths and velocity offsets are directly evaluated on the individual lines. As explained in Belloche et al. (2019), the molecular emission toward
Sgr B2(N1S) is resolved and we fixed its size to 2 [′′] for the LTE
modeling. This size is much larger than the beam and, therefore, the
determination of the column densities does not depend on its exact value. The optimization of the rotation temperatures is guided
by population diagrams (see Belloche et al. 2019). In the end, for a
given molecule, the only really free parameter is the column density,
which we adjust until the peak temperatures of the synthetic lines
match the detected ones.


In order to search for 2-propanimine, CH 3 C(NH)CH 3, toward
Sgr B2(N1S), we relied on the LTE parameters that we previously
derived for methanimine, CH 2 NH, toward this position with the ReMoCA survey (Margulès et al. 2022). We employed the spectroscopic predictions derived for 2-propanimine in Sect. 3 to compute
LTE synthetic spectra and search for emission of this molecule. Figure 5 illustrates the results of this search. The spectrally unresolved
multiplet of transitions of 2-propanimine at ∼90.469 GHz matches a
line detected in the ReMoCA spectrum (top left panel of Fig. 5). No
other molecule contributes to the emission at this frequency in our
current complete model of Sgr B2(N1S). However, all other transitions of 2-propanimine that are expected to be stronger than 3σ
are heavily blended with emission from other molecules and cannot be identified. The spectrally unresolved multiplet of transitions
of 2-propanimine at ∼109.625 GHz (bottom right panel of Fig. 5)
contributes to about half of the flux density of the line detected at
this frequency, with another ∼25% contributed by an isotopolog of
ethyl cyanide. This is not sufficient to secure the identification of the
observed line. Overall, although the data may hint at the presence of
2-propanimine in Sgr B2(N1S), the evidence is not robust enough
to claim a detection of this molecule, not even a tentative detection.
Therefore, we consider the synthetic spectrum shown in red in Fig. 5
as an upper limit to the emission of 2-propanimine in this source and
we report the corresponding upper limit on its column density in Table 6, after accounting for the vibrational partition function. To our



_MmW spectrum of 2-PA_ 7


**Figure 5.** Selection of transitions of 2-propanimine CH 3 C(NH)CH 3 covered
by the ReMoCA survey. The LTE synthetic spectrum used to derive the upper limit on the column density of CH 3 C(NH)CH 3 is displayed in red and
overlaid on the observed spectrum of Sgr B2(N1S) shown in black. The blue
synthetic spectrum contains the contributions of all molecules identified in
our survey so far, but does not include the contribution of the species shown
in red. The values written below each panel correspond from left to right to
the half-power beam width, the central frequency in MHz, the width in MHz
of each panel in parentheses, and the continuum level in K of the baselinesubtracted spectra in brackets. The y-axis is labeled in brightness temperature
units (K). The dotted line indicates the 3σ noise level.


knowledge, 2-propanimine does not have conformers, which means
that no conformational correction to the column density is needed.
We recall in Table 6 the column density of methanimine and the
upper limit to the column densities of the _Z_ and _E_ conformers of
1-propanimine that we derived earlier with the ReMoCA survey toward Sgr B2(N1S) (Margulès et al. 2022). Table 6 indicates that
propanimine is at least 18 times less abundant than methanimine in
Sgr B2(N1S). The upper limit is a factor three more stringent than
the one obtained previously for 1-propanimine.


**4.2** **Search toward IRAS 16293-2422**


We also searched for 2-propanimine toward the “B component” of
the low-mass protostar IRAS 16293-2422 from data obtained in
connection with the Protostellar Interferometric Line Survey (PILS)
program (Jørgensen et al. 2016). We refer to Jørgensen et al. (2016)
for details about the survey but repeat the key information needed for
this analysis. PILS is an unbiased line survey of the Class 0 protostellar system, IRAS 16293-2422, often considered an astrochemical
template source. PILS covers the frequency range from 329.1 GHz
to 362.9 GHz in ALMA’s Band 7 at 0.2 km s [−][1] spectral resolution.
We focus on a position offset by one beam (0.5 [′′] or 70 au) from the B
component where the lines are narrow (≈ 1 km s [−][1] ) and absorption
due to optical thickness (of continuum and line) is less than toward
the location of the source itself. Toward this position methanimine
CH 2 NH was detected as part of PILS by Ligterink et al. (2018) with
a column density of 6–10×10 [14] cm [−][2] for excitation temperatures between 70 and 120 K.


MNRAS **000**, 1–14 (2022)

8 _L. Zou et al._


**Table 6.** Parameters of our best-fit LTE model of methanimine toward Sgr B2(N1S), and upper limits for 1-propanimine and 2-propanimine.


Molecule Status [a] _N_ det [b] θ s [c] _T_ rot [d] _N_ [e] _F_ vib [f] _F_ conf [g] ∆ _V_ [h] _V_ off [i] _NN_ ref j

( [′′] ) (K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] )


_Methanimine_
CH 2 NH [(k)] [(][⋆][)] d 4 2.0 230 9.0 (17) 1.00 – 5.0 0.0 1


_1-Propanimine_
_E_ -C 2 H 5 CHNH [(k)] n 0 2.0 230 < 1.5 (17) 3.54 1.19 5.0 0.0       - 6.1
_Z_ -C 2 H 5 CHNH [(k)] n 0 2.0 230 < 2.0 (17) 3.58 6.22 5.0 0.0        - 4.5


_2-Propanimine_
CH 3 C(NH)CH 3 n 0 2.0 230 < 5.0 (16) 3.33 1.00 5.0 0.0      - 18


**Notes.** [(a)] d: detection, n: nondetection. [(b)] Number of detected lines (conservative estimate, see Sect. 3 of Belloche et al. 2016). One line of a given species may
mean a group of transitions of that species that are blended together. [(c)] Source diameter (FWHM). [(d)] Rotational temperature. [(e)] Total column density of the
molecule. _x_ (y) means _x_ × 10 [y] . For 1-propanimine, the two conformers were modeled as independent species and a conformer correction ( _F_ conf ) was applied a
posteriori, such that each column density corresponds to the total column density of 1-propanimine. [(f)] Correction factor that was applied to the column density
to account for the contribution of vibrationally excited states, in the cases where this contribution was not included in the partition function of the spectroscopic
predictions. [(g)] Correction factor that was applied to the column density to account for the contribution of other conformers in the cases where this contribution
was not included in the partition function of the spectroscopic predictions. [(h)] Linewidth (FWHM). [(i)] Velocity offset with respect to the assumed systemic
velocity of Sgr B2(N1S), _V_ sys = 62 km s [−][1] . [(j)] Column density ratio, with _N_ ref the column density of the previous reference species flagged with a star ( [⋆] ).
(k) The parameters were derived from the ReMoCA survey by Margulès et al. (2022).



To perform the search, we calculated synthetic spectra for 2propanimine assuming optically thin emission and LTE using custom routines, which are used also for other papers from the PILS
program (see for example Jørgensen et al. 2016; Ligterink et al.
2018; Calcutt et al. 2018; Manigand et al. 2020; Coutens et al. 2022)
but equivalent to the methodology of using Weeds in the search for
2-propanimine toward Sgr B2(N1S). We adopted a temperature of
100 K and systemic velocities consistent with other species detected
in PILS. The spectral regions with the brightest predicted lines in
the PILS range are shown in Fig. 6. The upper limit to column density can be derived by comparing to the parts of the spectra where
no lines are seen down to the RMS noise level of the data (4–5
mJy beam [−][1] km s [−][1] ) but where 2-propanimine is predicted to show
emission, e.g., around 341.96, 346.86 and 361.34 GHz. The upper
limit found in this manner is 5 × 10 [14] cm [−][2], i.e., a ratio < 0.5–1 with
respect to CH 2 NH, thus significantly less constraining than the <
1/18 ratio toward Sgr B2(N1S).


**5** **CONCLUSIONS**


We have presented the measurement and analysis of the millimeterwave spectrum of 2-propanimine between 50 and 500 GHz for the
first time. We successfully assigned and fitted 27,259 transitions and
9,349 individual frequencies of 2-propanimine using XIAM and ERHAM, and fully determined its spectroscopic parameters and the
barriers to internal rotation of the two nonequivalent CH 3 tops in 2propanimine. A fit residual of 53.5 kHz and dimensionless standard
error of 0.69 were obtained by ERHAM using a total of 44 parameters, including the full set of rotational constants, quartic and sextic
centrifugal distortion constants, and 12 internal rotation and tunneling parameters. The barriers to internal rotation are fitted experimentally to 533.764(63) cm [−][1] and 466.657(26) cm [−][1] by XIAM. The
barriers and the molecular structure parameters from the fit agree
well with theoretical calculation values. A prediction to _J_ [′′] = 80
and 1 THz is generated using the best-fit parameters from ERHAM.
We report the nondetection of 2-propanimine toward the offset position Sgr B2(N1S) of the hot molecular core Sgr B(N1) and toward
the protostar IRAS 16293B. We find that 2-propanimine is at least


MNRAS **000**, 1–14 (2022)



18 times less abundant than methanimine in Sgr B2(N1), and at most
50–83 % of methanimine in IRAS 16293B.


**ACKNOWLEDGEMENTS**


The authors thank Zbigniew Kisiel for his helpful discussion
and modification of the ERHAM program, and Isabelle Kleiner
and Lam Nguyen for their reminder of a technical point in
the XIAM fit. This work was supported by the CNES and
the Action sur Projets de l’INSU, PCMI, and by the European Union’s Horizon 2020 research and innovation programme
under the Marie Skłodowska-Curie grant agreement (H2020MSCA-IF-2019, Project no. 894508). This paper makes use
of the following ALMA data: ADS/JAO.ALMA#2016.1.00074.S,
ADS/JAO.ALMA#2013.1.00278.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and
NAOJ. The interferometric data are available in the ALMA archive

at https://almascience.eso.org/aq/. Part of this work has been carried
out within the Collaborative Research Centre 956, sub-project B3,
funded by the Deutsche Forschungsgemeinschaft (DFG) – project
ID 184018867.


**DATA AVAILABILITY**


The data underlying this article are available in the online supplementary material of this article, as well as in the Zenodo repository
(Appendix C, DOI: 10.5281/zenodo.7541890). The spectral line
catalog is also available at CDS via anonymous ftp to cdsarc.ustrasbg.fr (130.79.128.5) or via https://cdsarc.unistra.fr/vizbin/cat/J/MNRAS, and the Lille Spectroscopic Database
(https://lsd.univ-lille.fr/).

**Figure** **6.** Search for 2-propanimine toward IRAS 16293B: the shown frequency windows contain some of the brightest transitions predicted for an
excitation temperature of 100 K. No lines can be claimed to be detected at
this level and the upper limit (red line) corresponds to a column density of
5 × 10 [14] cm [−][2] .


**REFERENCES**


Belloche A., Menten K. M., Comito C., Müller H. S. P., Schilke P., Ott J.,

[Thorwirth S., Hieret C., 2008, A&A, 482, 179](http://dx.doi.org/10.1051/0004-6361:20079203)

Belloche A., Müller H. S. P., Menten K. M., Schilke P., Comito C., 2013,


[A&A, 559, A47](http://dx.doi.org/10.1051/0004-6361/201321096)

[Belloche A., Müller H. S. P., Garrod R. T., Menten K. M., 2016, A&A, 587,](http://dx.doi.org/10.1051/0004-6361/201527268)

[A91](https://ui.adsabs.harvard.edu/abs/2016A&A...587A..91B)

Belloche A., Garrod R. T., Müller H. S. P., Menten K. M., Medvedev I.,

[Thomas J., Kisiel Z., 2019, A&A, 628, A10](http://dx.doi.org/10.1051/0004-6361/201935428)

[Bizzocchi L., et al., 2020, A&A, 640, A98](http://dx.doi.org/10.1051/0004-6361/202038083)
Bøgelund E. G., McGuire B. A., Hogerheijde M. R., van Dishoeck E. F.,
[Ligterink N. F. W., 2019, A&A, 624, A82](http://dx.doi.org/10.1051/0004-6361/201833676)
Bonfand M., Belloche A., Garrod R. T., Menten K. M., Willis E., Stéphan
[G., Müller H. S. P., 2019, A&A, 628, A27](http://dx.doi.org/10.1051/0004-6361/201935523)

[Calcutt H., et al., 2018, A&A, 616, A90](http://dx.doi.org/10.1051/0004-6361/201732289)

Combes F., Gerin M., Wootten A., Wlodarczak G., Clausset F., Encrenaz

[P. J., 1987, A&A, 180, L13](https://ui.adsabs.harvard.edu/abs/1987A&A...180L..13C)
Coutens A., Loison J.-C., Boulanger A., Caux E., Müller H. S. P., Wakelam
[V., Manigand S., Jørgensen J. K., 2022, A&A, 660, L6](http://dx.doi.org/10.1051/0004-6361/202243038)
Endres C. P., Drouin B. J., Pearson J. C., Müller H. S. P., Lewen F., Schlem
[mer S., Giesen T. F., 2009, A&A, 504, 635](http://dx.doi.org/10.1051/0004-6361/200912409)
[Fourikis N., Takagi K., Morimoto M., 1974, ApJL, 191, L139](http://dx.doi.org/10.1086/181570)
[Friedel D. N., Snyder L. E., 2008, ApJ, 672, 962](http://dx.doi.org/10.1086/523896)
[Friedel D. N., Widicus Weaver S. L., 2012, ApJS, 201, 17](http://dx.doi.org/10.1088/0067-0049/201/2/17)
Friedel D. N., Snyder L. E., Remijan A. J., Turner B. E., 2005, [ApJL,](http://dx.doi.org/10.1086/497986) [632,](https://ui.adsabs.harvard.edu/abs/2005ApJ...632L..95F)
[L95](https://ui.adsabs.harvard.edu/abs/2005ApJ...632L..95F)

Frisch M. J., et al., 2016, Gaussian 16 Revision C.01



_MmW spectrum of 2-PA_ 9


[Fuchs U., Winnewisser G., Groner P., Lucia F. C. D., Herbst E., 2003, ApJS,](http://dx.doi.org/10.1086/345100)

[144, 277](https://ui.adsabs.harvard.edu/abs/2003ApJS..144..277F)

[Fuente A., et al., 2014, A&A, 568, A65](http://dx.doi.org/10.1051/0004-6361/201323074)
[Godfrey P. D., Brown R. D., Robinson B. J., Sinclair M. W., 1973, ApJL, 13,](https://ui.adsabs.harvard.edu/abs/1973ApL....13..119G)

[119](https://ui.adsabs.harvard.edu/abs/1973ApL....13..119G)

[Groner P., 1997, J. Chem. Phys., 107, 4483](http://dx.doi.org/10.1063/1.474810)
[Groner P., 2012, J. Mol. Spectrosc., 278, 52](http://dx.doi.org/10.1016/j.jms.2012.06.006)
[Groner P., Johnson R., Durig J., 1986, J. Mol. Struct., 142, 363](http://dx.doi.org/10.1016/0022-2860(86)85134-1)
[Guillemin J.-C., Nasraoui W., Gazzeh H., 2019, Chem. Commun., 55, 5647](http://dx.doi.org/10.1039/C9CC01755K)
[Hartwig H., Dreizler H., 1996, Z. Naturforsch A, 51, 923](http://dx.doi.org/10.1515/zna-1996-0807)
[Herbers S., Nguyen H. V. L., 2020, J. Mol. Spectrosc., 370, 111289](http://dx.doi.org/10.1016/j.jms.2020.111289)
Holtom P. D., Bennett C. J., Osamura Y., Mason N. J., Kaiser R. I., 2005,

[ApJ, 626, 940](http://dx.doi.org/10.1086/430106)
[Isokoski K., Bottinelli S., van Dishoeck E. F., 2013, A&A, 554, A100](http://dx.doi.org/10.1051/0004-6361/201220959)
[Jenny C., Heimgartner H., 1986, Helv. Chim. Acta, 69, 374](http://dx.doi.org/10.1002/hlca.19860690217)
[Jørgensen J. K., Bourke T. L., Nguyen Luong Q., Takakuwa S., 2011, A&A,](http://dx.doi.org/10.1051/0004-6361/201117139)

[534, A100](https://ui.adsabs.harvard.edu/abs/2011A&A...534A.100J)
[Jørgensen J. K., et al., 2016, A&A, 595, A117](http://dx.doi.org/10.1051/0004-6361/201628648)
Kaifu N., Morimoto M., Nagane K., Akabane K., Iguchi T., Takagi K., 1974,

[ApJ, 191, L135](http://dx.doi.org/10.1086/181569)
Kisiel Z., 2001, Assignment and Analysis of Complex Rotational Spectra.
Springer Netherlands, Dordrecht, pp 91–106, [doi:10.1007/978-94-010-](http://dx.doi.org/10.1007/978-94-010-0832-7_6)
[0832-7_6,](http://dx.doi.org/10.1007/978-94-010-0832-7_6) `[https://doi.org/10.1007/978-94-010-0832-7_6](https://doi.org/10.1007/978-94-010-0832-7_6)`
[Lattelais M., Pauzat F., Ellinger Y., Ceccarelli C., 2010, A&A, 519, A30](http://dx.doi.org/10.1051/0004-6361/200913869)
[Lee C., Yang W., Parr R. G., 1988, Phys. Rev. B, 37, 785](http://dx.doi.org/10.1103/PhysRevB.37.785)
[Ligterink N. F. W., et al., 2018, A&A, 619, A28](http://dx.doi.org/10.1051/0004-6361/201731980)
[Loomis F. W., Wood R. W., 1928, Phys. Rev., 32, 223](http://dx.doi.org/10.1103/PhysRev.32.223)
[Loomis R. A., et al., 2013, ApJL, 765, L9](http://dx.doi.org/10.1088/2041-8205/765/1/L9)
[Lykke J. M., et al., 2017, A&A, 597, A53](http://dx.doi.org/10.1051/0004-6361/201629180)
[Manigand S., et al., 2020, A&A, 635, A48](http://dx.doi.org/10.1051/0004-6361/201936299)
Maret S., Hily-Blant P., Pety J., Bardeau S., Reynier E., 2011, [A&A,](http://dx.doi.org/10.1051/0004-6361/201015487) [526,](https://ui.adsabs.harvard.edu/abs/2011A&A...526A..47M)

[A47](https://ui.adsabs.harvard.edu/abs/2011A&A...526A..47M)

[Margulès L., et al., 2022, A&A, 663, A132](http://dx.doi.org/10.1051/0004-6361/202243172)
[Melosso M., et al., 2020, A&A, 641, A160](http://dx.doi.org/10.1051/0004-6361/202038466)
Motiyenko R. A., Margulès L., 2022, in 2022 International Symposium on
Molecular Spectroscopy.
Motiyenko R. A., Armieieva I. A., Margulès L., Alekseev E. A., Guillemin
[J.-C., 2019, A&A, 623, A162](http://dx.doi.org/10.1051/0004-6361/201834587)

[Ohishi M., Suzuki T., Hirota T., Saito M., Kaifu N., 2019, Publ. Astron. Soc.](http://dx.doi.org/10.1093/pasj/psz068)
[Jpn., 71](http://dx.doi.org/10.1093/pasj/psz068)
[Peng T. C., et al., 2013, A&A, 554, A78](http://dx.doi.org/10.1051/0004-6361/201220891)
[Pickett H. M., 1991, J. Mol. Spectrosc., 148, 371](http://dx.doi.org/10.1016/0022-2852(91)90393-O)
[Reid M. J., et al., 2019, ApJ, 885, 131](http://dx.doi.org/10.3847/1538-4357/ab4a11)
[Rivilla V. M., et al., 2021, Proc. Natl. Acad. Sci., 118](http://dx.doi.org/10.1073/pnas.2101314118)
[Rolffs R., Schilke P., Zhang Q., Zapata L., 2011, A&A, 536, A33](http://dx.doi.org/10.1051/0004-6361/201117112)
[Sil M., Gorai P., Das A., Bhat B., Etim E. E., Chakrabarti S. K., 2018, ApJ,](http://dx.doi.org/10.3847/1538-4357/aa984d)

[853, 139](https://ui.adsabs.harvard.edu/abs/2018ApJ...853..139S)
Snyder L. E., Lovas F. J., Mehringer D. M., Miao N. Y., Kuan Y.-J., Hollis
[J. M., Jewell P. R., 2002, ApJ, 578, 245](http://dx.doi.org/10.1086/342273)
Suzuki T., Ohishi M., Saito M., Hirota T., Majumdar L., Wakelam V., 2018,

[ApJS, 237, 3](http://dx.doi.org/10.3847/1538-4365/aac8db)
[Tian Z., Zhang L., Li Y., Yuan T., Qi F., 2009, Proc. Combust. Inst., 32, 311](http://dx.doi.org/10.1016/j.proci.2008.06.098)
Towns C. H., Schawlow A. L., 1955, Microwave Spectroscopy. Dover Publications, Inc., p. 152
Van V., Nguyen T., Stahl W., Nguyen H. V. L., Kleiner I., 2020, J. [Mol.](http://dx.doi.org/10.1016/j.molstruc.2020.127787)
[Struct., 1207, 127787](http://dx.doi.org/10.1016/j.molstruc.2020.127787)
[Widicus Weaver S. L., et al., 2017, ApJS, 232, 3](http://dx.doi.org/10.3847/1538-4365/aa8098)
[Yu H. S., He X., Li S. L., Truhlar D. G., 2016, Chem. Sci., 7, 5032](http://dx.doi.org/10.1039/C6SC00705H)
Zakharenko O., Motiyenko R. A., Margulès L., Huet T. R., 2015, J. [Mol.](http://dx.doi.org/10.1016/j.jms.2015.09.005)
[Spectrosc., 317, 41](http://dx.doi.org/10.1016/j.jms.2015.09.005)
[Zaleski D. P., et al., 2013, ApJ, 765, L10](http://dx.doi.org/10.1088/2041-8205/765/1/l10)
[Zeng S., et al., 2021, ApJ, 920, L27](http://dx.doi.org/10.3847/2041-8213/ac2c7e)
Zhao Y., Truhlar D. G., 2008, Theor. Chem. Acc., 120, 215
Zheng S., Dong W., Rui D., Maofa G., Dianxun W., Foo-Tim C., Mok D.
[K. W., 2003, J. Chem. Phys., 119, 293](http://dx.doi.org/10.1063/1.1577316)
[Zou L., Widicus Weaver S. L., 2017, ApJ, 849, 139](http://dx.doi.org/10.3847/1538-4357/aa8eea)


MNRAS **000**, 1–14 (2022)

10 _L. Zou et al._


**APPENDIX A:** **EXPERIMENTAL DETAILS**


**A1** **Synthesis of 2-propanimine**


2-Amino-2-methylpropanenitrile, prepared as previously reported
(Jenny & Heimgartner 1986), was vaporized in a vacuum line
equipped with a reactor half-filled with KOH in powder form and
heated to 90 °C. The vacuum line was also equipped with two Utubes with stopcocks (for similar experiments see Guillemin et al.
2019). The first stopcock was immersed in a cold bath at −60 °C
to trap compounds with high boiling point, and the second one in a
bath cooled to −100 °C to selectively trap the 2-propanimine. At the
end of the reaction, the stopcocks of the second U-tube were closed,
and the 2-propanimine sample was preserved in dry ice before connecting to the cell of the spectrometer.


**A2** **Millimeter-wave spectroscopy of 2-propanimine**


The spectrum was measured using the fast absorption spectrometer
at Lille. The details of the spectrometer have been described elsewhere (Zakharenko et al. 2015; Motiyenko et al. 2019), and here
we only state the specific conditions concerning this measurement.
After connecting the sample U-tube to our 2-meter-long glass absorption cell, the dry ice bath was removed, and the U-tube was immediately submerged into an ethanol bath at −60 °C throughout the
measurement. The stopcock was slightly opened to introduce a small
continuous flow of the sample vapor into the cell. The cell pressure
was maintained between 8–20 µBar, optimized in each millimetersubmillimeter wave band for the best signal-to-noise ratio (SNR).
The spectrum was measured between 50–110 GHz, 150–
330 GHz, and 360–500 GHz using commercial frequency amplifiermultiplier chains (50–75 GHz: Millitech AMC-15-R0000, above
75 GHz: Viginia Diodes, Inc.) driven by a microwave synthesizer
(Agilent, E8527). Signals were detected by solid state detectors
(Viginia Diodes, Inc.). We applied sine-wave frequency modulation
and second harmonics detection using a lock-in amplifier (METEK
7270 DSP). For the spectrum above 150 GHz, the modulation deviation after frequency multiplication was set to match the linewidth
of the spectral lines, at 240 kHz in 150–220 GHz, 270 kHz in 225–
330 GHz, and 540 kHz in 360–500 GHz. The time constant was
set to 0.2 ms, and 2–4 acquisitions were sufficient. For the spectrum below 110 GHz, the spectral intensity is weak due to the unfavorable Boltzmann distribution at room temperature. To improve
the SNR, we slightly exaggerated the modulation deviation over the
spectral linewidth. The modulation deviation was set to 200 kHz in
50–75 GHz, and 300 kHz in 75–110 GHz. A longer time constant,
1 ms in 50–75 GHz, and 0.5 ms in 75–110 GHz, was also chosen
together with 8 acquisitions to obtain the spectra with decent SNR.


**A3** **Quantum chemical calculation**


Quantum chemical calculations were performed on the Sakura highperformance computer cluster at PhLAM, using the Gaussian16
software (Frisch et al. 2016). Molecular structure of 2-propanimine,
fixed to _C_ _s_ symmetry, was optimized, and harmonics vibrational frequencies were calculated based on the optimized geometry. Several density functional theory (DFT) methods, B3LYP (Lee et al.
1988), M062X (Zhao & Truhlar 2008), MN15 (Yu et al. 2016), were
used with the 6-311++G(3df,3pd) basis set, which include polarization and diffuse functions. Second order Møller–Plesset perturbation (MP2) calculation was used with aug-cc-pVTZ basis set. The


MNRAS **000**, 1–14 (2022)



results of these calculations were used to estimate the barrier to in
ternal rotation of the two CH 3 groups in 2-propanimine, and to guide
the assignment of the experimental spectra. To estimate the barrier
to internal rotation of the two CH 3 groups, 1-dimensional potential
energy surface (PES) scan was conducted by twisting the dihedral
angle of one of the C−H bond in the CH 3 group with respect to
the central C−C(N)−C plane. In addition, 1-dimensional PES scan
was performed on the angle of the N−H bond with respect to the
central C−C(N)−C plane, in order to verify the symmetry group of
the molecule. During the PES scans, the molecular symmetry was
relaxed to allow re-optimization of the molecular structure at each
scanned point.


**A4** **Spectral analysis**


The experimental spectra were processed using a custom spectral assignment software. In the first step, the sinusoidal baseline produced
by standing waves in the absorption cell was removed by Fouriertransforming the spectrum, erasing their representative frequency
components, and then inverse Fourier-transforming back to the original frequency space. After baseline removal, peaks were identified
and fitted with a second-derivative Voigt line profile to obtain their
peak frequencies. We associated various uncertainties, ranging from
25 kHz to 200 kHz, to each fitted peak according to the frequency
resolution at each frequency band, and the SNR of the peaks represented by the peak frequency uncertainty from the least-square fit.
Typical uncertainty of individual lines is 25 kHz in 50–110 GHz,
50 kHz in 150–330 GHz, and 100 kHz above 360 GHz, and we
doubled the uncertainty for blended lines and lines with low SNR.
Weights were also assigned to blended transitions according to their
relative line intensities.

The spectral fit was performed using both the XIAM (Hartwig
& Dreizler 1996; Herbers & Nguyen 2020) and ERHAM (Groner
1997, 2012) programs with the standard Watson’s A reduction
Hamiltonian under the _I_ _[r]_ representation. As there is no available microwave study of 2-propanimine to our knowledge, we started our
assignment using XIAM to predict the spectrum of 2-propanimine
using the rotational constants, quartic centrifugal distortion constants, and internal rotation parameters obtained from the theoretical calculation. Once the strongest _R_ -branch lines were identified
and assigned, the assignment and fit was performed iteratively by
including more series of weaker lines into the fit. Throughout this iterative process, we used Loomis-Wood diagrams (Loomis & Wood
1928) to assist the identification of line series. Finally, ERHAM was
used to provide a refined fit with higher accuracy using the same
input line list as for the XIAM fit.
We noted that the number of transitions in our data set exceeded

the input limit of the publicly available XIAM and ERHAM programs, hosted at Zbigniew Kisiel’s website PROSPE [9] (Programs
for ROtational SPEctroscopy) (Kisiel 2001). Therefore, the source
codes of both programs were slightly modified to allow larger number of input lines. For XIAM, we obtained the source code of the
official “XIAM_mod” program [10], and modified the “ `DIMLIN` ” parameter, which controls the limit of input lines, to 99999. We also
changed the output format of the fitted parameters to display more
significant figures for the sextic centrifugal distortion constants.
The modified source code was compiled using the original MAKEFILE in the source code package on a Windows 10 computer us

9 http://www.ifpan.edu.pl/∼kisiel/prospe.htm
10 http://www.ifpan.edu.pl/∼kisiel/introt/xiam_mod/XIAM_mod.zip

|103,8 ← 101,9  JK,K″ ← JK,K′|102,8 ← 102,9|
|---|---|
|103,8 ← 102,9<br>,,<br>(1,1)<br>(1,2)<br>(0,1)<br>σ1, σ2)=<br>_K_a,_K_c  _K_a,_K_c<br>_F_=9,11  10<br>9,11  10<br>~~•~~<br>~~•~~<br>• •<br>• •|102,8 ← 101,9<br>,,<br>(1,0)<br>(0,0)<br>9,11  10<br>9,11  10<br>~~•~~<br>~~•~~<br>• •<br>• •|
|||



72135 72140 72145 72150 72155


Frequency (MHz)


**Figure A1.** Example of the treatment of the partially resolved hyperfine components. The observed hyperfine component frequencies are marked with
pink dots and sticks. The weighted averaged frequencies of these components, marked in blue dots and sticks, were used in the spectral fit.


ing the GNU Fortran 11.1.0 compiler. For ERHAM, the limit of
input lines was increased to 32768. The modification was kindly
provided by Dr. Kisiel, and the modified ERHAM code, named
`erham_r3a.exe`, can be also found in Kisiel’s website [11] .
Quadrupole hyperfine splitting due to the [14] N nuclei was partially
resolved in the spectra at low frequencies. Only the three strongest
components, namely, the ∆ _F_ = ∆ _J_ components, were observable
under our sensitivity level. The _F_ = _J_ ± 1 components are blended
and the _F_ = _J_ component is separated. Therefore, the spectral
line of each torsional-rotational transition further splits into 2 lines
with intensity ratio of roughly 2:1. The full treatment of the coupling between the nuclear spin with the internal rotor is extremely
complicated (Van et al. 2020). Without the access to microwavecavity spectrum at higher resolution, our millimeter-wave data alone
were not sufficient to fully determine this interaction. In addition,
the number of partially resolved hyperfine lines consists of only a
small portion, about 1 %, of the complete line list. Therefore, instead of including the hyperfine effect into the spectroscopy model,
we chose to treat these partially blended hyperfine lines separately
before the final spectral fit. For each set of hyperfine components,
we calculated the weighted averaged line frequency using the theoretical hyperfine intensity ratio as the weighting factor. For _R_ branch
lines, the intensity is proportional to


1
_F_ [′′] [(] _[J]_ [′′] [ +] _[ F]_ [′′] [ +][ 2)(] _[J]_ [′′] [ +] _[ F]_ [′′] [ +][ 1)(] _[J]_ [′′] [ +] _[ F]_ [′′] [ −] [1)(] _[J]_ [′′] [ +] _[ F]_ [′′] [ −] [2)][,]


and for _Q_ branch lines, the intensity is proportional to


2 _F_ [′′] + 1 � _J_ ′′ ( _J_ ′′ + 1) + _F_ ′′ ( _F_ ′′ + 1) − 2� 2 .
_F_ [′′] ( _F_ [′′] + 1)


_J_ [′′] and _F_ [′′] denote the _J_ and _F_ quantum numbers of the upper state
associated with the transition (Towns & Schawlow 1955). These
averaged line frequencies were then merged with other torsionalrotation line frequencies for the spectral fit. One example of such
weighted average treatment is shown in Figure A1. Pink dots mark
the experimentally measured frequencies of the hyperfine components, and blue dots mark their weighted average frequencies which
were then used in the spectral fit.
The barriers to internal rotation in the ERHAM model were derived from the torsional energy differences based on the method de

11 http://www.ifpan.edu.pl/∼kisiel/introt/erham/erhamz_R3a.exe



_MmW spectrum of 2-PA_ 11


**Table** **B1.** Optimized geometry of 2-propanimine using B3LYP/6311++G(3df,3pd). Unit is in Å.


Atom _x_ y _z_


N 0.045853 1.430604 0.000000

C 0.000000 0.160884 0.000000

H 1.009860 1.765233 0.000000

C −1.340658 −0.522810 0.000000

H −2.139230 0.213603 0.000000

H −1.442464 −1.166615 0.876838

H −1.442464 −1.166615 −0.876838

C 1.203943 −0.750007 0.000000

H 2.134212 −0.184332 0.000000

H 1.189704 −1.401953 −0.876286

H 1.189704 −1.401953 0.876286


**Table** **B2.** Optimized geometry of 2-propanimine using M062X/6311++G(3df,3pd). Unit is in Å.


Atom _x_ y _z_


N 0.047787 1.428742 0.000000

C 0.000000 0.163482 0.000000

H 1.014348 1.754234 0.000000

C −1.337039 −0.522386 0.000000

H −2.134648 0.213414 0.000000

H −1.430683 −1.164272 0.877171

H −1.430683 −1.164272 −0.877171

C 1.198484 −0.750195 0.000000

H 2.129394 −0.188104 0.000000

H 1.174546 −1.398798 −0.876535

H 1.174546 −1.398798 0.876535


scribed in Groner et al. (1986). The “BARRIER” program [12] available on the PROSPE website is designed to calculate such barrier
to internal rotation for single methyl rotor. Generally, it does not
treat the case of two methyl rotors. In our particular fit, however,
the statistically meaningful tunneling parameters are only those associated with the individual tops, i.e., ϵ 01, ϵ 02, and ϵ 10, ϵ 12 . The cross
terms such as ϵ 1,−1 and ϵ 1,1 are not significant. In this case, the two
methyl tops are almost independent (for the ground state), and we
can approximately use the “BARRIER” program to calculate their
_V_ 3 barriers individually. Since only the ground state energy difference is available, we calculate the _V_ 3 barrier height from only one
parameter; there is no estimated uncertainty. From these terms ERHAM calculates the torsional energy differences, which can then be
used to derive the barrier to internal rotation The _V_ 3 barriers are determined to be 531.394 cm [−][1] and 462.284 cm [−][1], respectively.


**APPENDIX B:** **SUPPLEMENTARY RESULTS**


**B1** **Calculation results**


The optimized _x_, y, _z_ coordinates of 2-propanimine using different
level of theory mentioned in Tables B1–B4. The harmonic and
anharmonic vibrational energies of 2-propanimine calculated by
MP2/aug-cc-pVTZ is listed in Table B5, which can be used to estimate the vibrational partition function.


12 http://www.ifpan.edu.pl/˜kisiel/introt/barrier/BARRIER.exe


MNRAS **000**, 1–14 (2022)

12 _L. Zou et al._


**Table** **B3.** Optimized geometry of 2-propanimine using MN15/6311++G(3df,3pd). Unit is in Å.


Atom _x_ y _z_


N 0.062586 1.429206 0.000000

C 0.000000 0.161241 0.000000

H 1.032955 1.748995 0.000000

C −1.341104 −0.511567 0.000000

H −2.132354 0.231737 0.000000

H −1.441746 −1.153897 0.876584

H −1.441746 −1.153897 −0.876584

C 1.190014 −0.759265 0.000000

H 2.124642 −0.201788 0.000000

H 1.163343 −1.409020 −0.876051

H 1.163343 −1.409020 0.876051


**Table B4.** Optimized geometry of 2-propanimine using MP2/aug-cc-pVTZ.
Unit is in Å.


Atom _x_ y _z_


N 0.037113 1.437086 0.000000

C 0.000000 0.156237 0.000000

H 1.008541 1.754321 0.000000

C −1.334190 −0.529263 0.000000

H −2.132032 0.207629 0.000000

H −1.429035 −1.170936 0.877544

H −1.429035 −1.170936 −0.877544

C 1.203722 −0.746205 0.000000

H 2.129794 −0.174356 0.000000

H 1.187395 −1.394967 −0.877149

H 1.187395 −1.394967 0.877149


**B2** **Molecular Structure**


Supplementary 2D PES scan regarding the internal rotation of CH 3
tops was performed to ensure that there is no other conformer, which
are local minimum in the PES, except for the optimized conformation shown in Figure 4. The PES scan was performed from 0° to 120°
with a step of 2°, and extrapolated to 360° based on the symmetry of
the PES. The basis set is reduced to 6-311+g(2d,2p) to speed up the
calculation. The result is plotted in Figure B1. The _x_ and y axes correspond to the dihedral angle of the rotation of each CH 3 top. From
the figure, We can find 9 equivalent global minima that correspond
to the optimized conformation, and there is no other local minimum.


**B3** **Selection rule and dipole moments**


We have stated in Section 3 that the dipole moment values of 2propanimine we obtained from theoretical calculation (µ _a_ = 1.37 D
and µ _b_ = −2.06 D) differ from the values reported by Sil et al.
(µ _a_ = −0.8107 D, µ _b_ = 1.8357 D, and µ _c_ = 1.4047 D). Several
evidences point out that our values are more reliable and the values
from Sil et al. are erroneous. First, considering the _C_ _s_ symmetry of
2-propanimine, one of the three dipole moment components must
be zero, otherwise the molecule will have no symmetry plane. Secondly, selection rules of rotational transitions state that a non-zero
µ _c_ dipole moment component corresponds to _c_ - type selection rule,
which is ∆ _K_ _c_ = even and ∆ _K_ _a_ = odd. In our experimental spectra,
we do no see these transitions. For example, in Figure B2, we unambiguously show the missing of _c_ -type transition lines 14 9,5 ← 13 8,5,
using the best-fit parameters from ERHAM and assumed µ _c_ =1 D


MNRAS **000**, 1–14 (2022)



**Table B5.** Harmonic and anharmonic vibrational energy of the fundamental
bands of 2-propanimine, calculated by MP2/aug-cc-pVTZ.


Mode _E_ harm (cm [−][1] ) _E_ anharm (cm [−][1] )


ν 1 3453.022 3287.214
ν 2 3193.330 3055.883
ν 3 3168.510 3029.200
ν 4 3067.467 2963.991
ν 5 3061.911 2961.916
ν 6 1694.215 1653.353
ν 7 1496.457 1453.421
ν 8 1488.849 1444.107
ν 9 1427.083 1385.101
ν 10 1409.339 1371.320
ν 11 1355.848 1322.955
ν 12 1135.544 1104.881
ν 13 1089.884 1065.154

ν 14 942.033 924.229
ν 15 824.252 806.235
ν 16 505.878 503.780
ν 17 381.089 386.913
ν 18 3143.859 3005.790
ν 19 3139.602 3003.191
ν 20 1508.360 1451.230
ν 21 1485.739 1443.779
ν 22 1112.528 1084.408
ν 23 1049.536 1019.205
ν 24 830.510 814.042
ν 25 463.680 461.770
ν 26 183.404 171.152
ν 27 119.892 133.962


dipole moment. Based on the noise level of the spectrum, the upper
limit of the µ _c_ = is only 0.2 D. Thirdly, line intensity is proportional
to the square of the dipole moment component. Using our dipole
moment values, the intensity ratio between the _a_ - and _b_ - type transitions is 1:2.26. If we use the dipole moment values from Sil et al., the
intensity ratio between the _a_ - and _b_ - type transitions will be 1:5.13.
In Figure 2, we have shown an example that the relative intensity
of _a_ - and _b_ - type lines is closer to 1:2, which agrees better with our
dipole moment values than the values from Sil et al.. With these reasons, we claim that our spectral data do not support the existence of
µ _c_ dipole moment component in 2-propanimine, and the values from
Sil et al. should not be used.

Despite the above arguments, we do have observed some spectral
lines with _c_ -type selection rule. This is not relevant to the dipole moment components, however, but an anomalous phenomenon caused
by internal rotation. The phenomenon has been observed and discussed in similar two methyl top systems, such as dimethyl ether
(Endres et al. 2009) and ethyl methyl ether (Fuchs et al. 2003). For
a rigid rotor with a symmetry plane spanned by the _a_ and _b_ principal axes, only _a_ - and _b_ -type rotational transitions are allowed, e.g.
transitions with ∆ _K_ _c_ = odd in the _J_, _K_ _a_, _K_ _c_ notation for the asymmetric rotor levels. For molecules with one methyl rotor, however, this
selection rule from dipole moment restriction applies only to the _A_ state (σ = 0) but not to the _E_ -state (σ = 1). For molecules with two
methyl rotors, it applies only to the (σ 1, σ 2 ) = (0, 0) state, but not to
any state where σ 1 or σ 2 or both are non-zero. In these cases, the _J_,
_K_ _a_, _K_ _c_ labels are at best approximate and at worst useless. Unfortunately, no easy-to-apply contradiction-free systems to assign asymmetric rotor labels exist in these cases. However, when such labels
are used anyway (e.g., when the levels ordered by increasing energy
are assigned as if they were those of a rigid asymmetric rotor), it

_MmW spectrum of 2-PA_ 13


_K_ a ″ = 12, _f_ c = 319100.0


(0,1) (0,0)(1,0)

|( (1,1)|Col2|Col3|(0, (0,1) (1,2)|Col5|Col6|Col7|Col8|,0) (1,|,0)|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|(1,1)|(1,1)|(1,1)|(1,2)|(1,2)|(1,2)|(1,2)|(1,2)||||
||||||||||||



-2 -1.5 -1 -0.5 0 0.5 1 1.5 2


_K_ a ″ = 13, _f_ c = 310668.0

|(0, (1,1) (1,2)|Col2|Col3|Col4|Col5|,1) (1,|Col7|Col8|(0,0,0)|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|(,)<br>(,)|(,)<br>(,)|(,)<br>(,)|(,)<br>(,)|(,)<br>(,)||||||||
|||||||||||||



-8 -6 -4 -2 0 2 4 6 8

(0,0)



_K_ a ″ = 14, _f_ c = 312615.0



(1,0)
(0,1)



(0,1) a c (0,1)
(1,1) (1,0)(1,2) (1,1) (1,2)



-300 -200 -100 0 100 200 300








|(0 1,1)|0,1)|(0, )(1,0)|Col4|,0) Ka″ = 15, fc = 317709.0|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|,<br>,2)||||(0,1)<br>(1,0)<br>(1,1)<br>(1,2)<br>|(0,1)<br>(1,0)<br>(1,1)<br>(1,2)<br>|(0,1)<br>(1,0)<br>(1,1)<br>(1,2)<br>|(0,1)<br>(1,0)<br>(1,1)<br>(1,2)<br>|(0,1)<br>(1,0)<br>(1,1)<br>(1,2)<br>|
||||||||||



**Figure** **B1.** 2D PES of CH 3 internal rotation in 2-propanimine calculated
with B3LYP/6-311+g(2d,2p). Energy step between contours is 100 cm [−][1] .
The structure at the global minimum, maximum and two saddle points are
presented and pointed by arrows.


19 7,12 ← 18 8,11


245990 246000 246010 246020 246030


Frequency (MHz)


**Figure** **B2.** Non-detection of regular _c_ -type transitions of 2-propanimine.
The blue sticks represent the torsional splitting components of the _b_ -type
transition 19 7,12 ← 18 8,11 . The brown sticks represent the expected location
of the _c_ -type transition 14 9,5 ← 13 8,5, if 2-propanimine would have µ _c_ = 1 D.
The missing spectral lines proves that 2-propanimine does not possess µ _c_, in
agreement with its _C_ _s_ molecular symmetry.


occurs frequently that, (based on the labels,) some transitions with
∆ _K_ _c_ = even (instead of ∆ _K_ _c_ = odd) “appear” regardless of µ _c_ = 0.
This effect is due to the labeling problem, and “ _d_ -type” transitions
(with ∆ _K_ _a_ = ∆ _K_ _c_ = even) may also appear. Due to heavy mixing of
asymmetric rotor wavefunctions, it is also common that both _b_ -type
and “ _c_ -type” (or _a_ -type and “ _d_ -type”) transitions may be observed
instead of one or the other.

In our 2-propanimine spectrum, these mis-labeled _c_ -type transitions appear when _K_ _c_ is sufficiently small compared to _K_ _a_, and they
only accompany _b_ -type transitions and not _a_ -type transitions. Figure B3 demonstrates the emergence of level crossing for the _b_ -type,
_R_ -branch, _J_ = 17 ← 16 lines. When _K_ _a_ [′′] [≤] [13,] [rotational] [quantum]
numbers with normal _b_ -type selection rule (∆ _K_ _a_ = 1, ∆ _K_ _c_ = −1)
correctly label the five torsional components with correct relative
intensity. At _K_ _a_ [′′] [=] [14, the tunneling splitting pattern abruptly alters]
into 9 components, in which five components remain the _b_ -type se

|(12)(11)<br>,,|Col2|Col3|K a″ = 16, f c = 322556 .0|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||


|(12) (11)<br>,,|Col2|Col3|K a″ = 17, f c = 327471 .0|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||



-15 -10 -5 0 5 10 15


Frequency (MHz)


**Figure B3.** Demonstration of the emergence of level crossing. The transition
frequencies of the _R_ -branch, _b_ -type transition series with _J_ [′′] = 17, _K_ _a_ [′′] [=]
_K_ _a_ [′] [+][ 1, and] _[ K]_ _a_ [′′] [+] _[ K]_ _c_ [′′] [=] _[J]_ [′′] [ are plotted from] _[ K]_ _a_ [′′] [=][ 12][ −] [17 with respect to the]
offset from the center frequency _f_ _c_ in each panel. Sticks in blue represent the
lines with normal _b_ -type selection rule, where ∆ _K_ _c_ = −1. Sticks in brown
represent the lines with _c_ -type selection rule due to level-crossing, where
∆ _K_ _c_ = 0. The height of the sticks is proportional to the relative intensity of
these components. The separation between the _b_ -type components and _c_ -type
components at _K_ _a_ [′′] [=][ 14 is the largest.]


lection rule, and four new components appear with _c_ -type selection
rule ∆ _K_ _c_ = 0. The separation between the _b_ -type and _c_ -type components is approximately 500 MHz, one order of magnitude larger
than the span of the regular torsional splitting, which rarely exceeds
50 MHz. These extra _c_ -type components arise from the mixing of
nearly degenerate asymmetric rotor wavefunctions, and intensities
are redistributed between them and their _b_ -type counterparts. As _K_ _a_ [′′]
continues to increase, the tunneling splitting pattern resumes to five
components, and the _b_ -type selection rule is only maintained in the
(σ 1, σ 2 ) = (0, 0) state, as it corresponds to the torsional sublevel of
the lowest energy that is not affected by the mislabeling.


**B4** **Fit statistics**


A detailed error analysis shows that in the XIAM model, 97.89 % of
the fitted transitions have frequency deviations within 3σ. 575 transitions (out of 27,259 transitions) have frequency deviations larger
than 3σ, in which 152 deviations are > 5σ. The maximum frequency
deviation is 22σ, which is an indication of the insufficiency of the
model. The transitions with the largest deviations are those with high
_K_ _a_ values. This result is expected because XIAM has a limited number of high order correction terms to treat a data set with such high
_J_ and _K_ _a_ values. In the ERHAM fit, 99.91 % of the fitted transitions


MNRAS **000**, 1–14 (2022)



-150 -100 -50 0 50 100 150


(0,1) (1,0) (0,0)


-15 -10 -5 0 5 10 15

(0,1) (1,0) (0,0)

14 _L. Zou et al._


have frequency deviations within 3σ, and the deviations of the rest
0.09 % transitions are all within 5σ. These statistics indicate that the

ERHAM fit has reached experimental accuracy.


**APPENDIX C:** **INPUT AND OUTPUT FILES FOR XIAM**

**AND ERHAM**


The input and output files for XIAM and ERHAM fit can be
found on Zenodo (DOI: 10.5281/zenodo.7541890) as `TableC1.xi`,
`TableC1.xo`, `TableC2.in`, and `TableC2.out` .


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–14 (2022)


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: archival_reuse",
  "failed_quote": "We used the imaging spectral line survey Reexploring Molecular Complexity with ALMA (ReMoCA) that targeted the high-mass star forming protocluster Sgr B2(N) with ALMA."
 },
 {
  "path": "processing.inherited[3].what.evidence[1]",
  "value": "PILS survey observations, data reduction, and custom LTE synthetic spectrum routines for IRAS 16293-2422",
  "failed_quote": "To perform the search, we calculated synthetic spectra for 2-propanimine assuming optically thin emission and LTE using custom routines, which are used also for other papers from the PILS program (see for example Jørgensen et al. 2016; Ligterink et al. 2018; Calcutt et al. 2018; Manigand et al. 2020; Coutens et al. 2022)"
 },
 {
  "path": "analysis_steps[1].validation.evidence[1]",
  "value": "Evaluated microwave rms (78.0 kHz for XIAM, 53.5 kHz for ERHAM), dimensionless standard deviation (1.38 for XIAM, 0.69 for ERHAM), and fraction of transitions within 3σ (99.91% for ERHAM)",
  "failed_quote": "In the ERHAM fit, 99.91 % of the fitted transitions have frequency deviations within 3σ, and the deviations of the rest 0.09 % transitions are all within 5σ."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[1]",
  "value": "Vibrational partition function estimated from harmonic/anharmonic vibrational energies in Table B5; no conformational correction needed (Fconf = 1.00)",
  "failed_quote": "To our knowledge, 2-propanimine does not have conformers, which means that no conformational correction to the column density is needed."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Compute LTE synthetic spectra assuming optically thin emission using custom PILS routines and compare predicted bright transitions against line-free regions of the observed ALMA Band 7 spectrum down to the RMS noise level",
  "failed_quote": "To perform the search, we calculated synthetic spectra for 2-propanimine assuming optically thin emission and LTE using custom routines"
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "Optically thin emission and LTE at excitation temperature of 100 K",
  "failed_quote": "To perform the search, we calculated synthetic spectra for 2-propanimine assuming optically thin emission and LTE using custom routines"
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "Compiling the modified XIAM source code",
  "failed_quote": "The modified source code was compiled using the original MAKEFILE in the source code package on a Windows 10 computer using the GNU Fortran 11.1.0 compiler."
 },
 {
  "path": "software[8].used_for.evidence[0]",
  "value": "Calculating optically thin LTE synthetic spectra for 2-propanimine toward IRAS 16293B",
  "failed_quote": "To perform the search, we calculated synthetic spectra for 2-propanimine assuming optically thin emission and LTE using custom routines, which are used also for other papers from the PILS program"
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "The ERHAM fit reaches experimental accuracy and provides reliable transition frequency predictions up to 1 THz for astronomical searches.",
  "failed_quote": "Detailed statistical analysis (see Appendix B4) shows that the ERHAM model reaches experimental accuracy, whereas the XIAM model cannot reach experimental accuracy because of the limited number of high order correction terms available in the model."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Used both XIAM (which directly fits V3 barriers) and ERHAM (which includes more higher-order tunneling terms to reach experimental accuracy); used LTE modeling justified by high gas densities (> 10^7 cm−3) in Sgr B2(N).",
  "failed_quote": "Detailed statistical analysis (see Appendix B4) shows that the ERHAM model reaches experimental accuracy, whereas the XIAM model cannot reach experimental accuracy because of the limited number of high order correction terms available in the model."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Predicted frequencies for transitions not accessed experimentally should be viewed with caution because high-order terms in the ERHAM fit may be correlated and fluctuate when extrapolated.",
  "failed_quote": "Nevertheless, the predicted frequencies of transitions not accessed by this experiment should still be viewed with caution because the high order terms in the ERHAM fit may be highly correlated and subject to large fluctuation if more spectral data were accessible."
 }
]
```
