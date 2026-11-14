# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...677A..65G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
A&A, 677, A65 (2023)
[https://doi.org/10.1051/0004-6361/202346518](https://doi.org/10.1051/0004-6361/202346518)
© The Authors 2023


# **Astronom** **y**
### &
# **Astrophysics**


## **Rotational spectrum and interstellar detection of the first** torsionally excited state of methylamine [⋆]

P. Gyawali [1], R. A. Motiyenko [1], A. Belloche [2], I. Kleiner [3], V. V. Ilyushin [4], E. A. Alekseev [1,4],
I. Gulaczyk [5], and M. Kreglewski [5]


1 Univ. Lille, CNRS, UMR 8523 – PhLAM – Physique des Lasers Atomes et Molécules, 59000 Lille, France
e-mail: `[roman.motiyenko@univ-lille.fr](mailto:roman.motiyenko@univ-lille.fr)`
2 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany
3 Université Paris-Cité and Univ. Paris-Est Creteil, CNRS, LISA, 75013 Paris, France
4 Radiospectrometry Department, Institute of Radio Astronomy of NASU, Mystetstv 4, 61002 Kharkiv, Ukraine
5 Faculty of Chemistry, Adam Mickiewicz University in Pozna´n, ul. Uniwersytetu Pozna´nskiego 8, 61-614 Pozna´n, Poland


Received 28 March 2023 / Accepted 14 June 2023


**ABSTRACT**


_Context._ Methylamine (CH 3 NH 2 ) was first detected in the interstellar medium (ISM) toward Sgr B2 almost 50 years ago by observation
of rotational transitions in its torsional ground state. Methylamine exhibits two large-amplitude motions (LAMs), the methyl torsion
and amine wagging, which complicate the spectral analysis, especially in excited vibration states. The lack of an accurate model of the
two coupled LAMs has also hampered the identification in the ISM of rotational transitions in excited vibrational states.
_Aims._ The aim of this work is to study the terahertz and microwave rotational spectra of methylamine experimentally and theoretically
in order to provide a reliable basis for the detection of its rotational transitions in the first torsionally excited state, � _t_ = 1, in the ISM.
_Methods._ The terahertz spectrum of methylamine was measured from 150 to 1520 GHz with the Lille fast scan spectrometer. Using
a new “hybrid” Hamiltonian model, we were able to analyze the nuclear quadrupole hyperfine structure and to accurately fit the
rotational spectrum of the � _t_ = 1 state of methylamine. We used the imaging spectral line survey ReMoCA performed with the Atacama
Large Millimeter/submillimeter Array (ALMA) to search for rotational transitions of methylamine in its first torsionally excited state
toward the high-mass star forming region Sgr B2(N). The observed spectra are modeled under the assumption of local thermodynamic
equilibrium (LTE).
_Results._ Accurate spectral predictions were obtained for the ground and first excited states of CH 3 NH 2 . We report the first interstellar
detection of methylamine in the � _t_ = 1 state toward the offset position Sgr B2(N1S) in the hot molecular core Sgr B2(N1). The LTE
parameters derived previously from the rotational emission of methylamine in its torsional ground state toward Sgr B2(N1S) yield
synthetic spectra of methylamine in the � _t_ = 1 state that are fully consistent with the ALMA spectra and allow us to identify five
rotational lines of this state.


**Key words.** ISM: molecules – methods: laboratory: molecular – submillimeter: ISM – molecular data – line: identification



**1. Introduction**


Methylamine (CH 3 NH 2 ) is a seven-atom organic molecule and
the simplest primary alkylamine. It is considered to be a possible
precursor of the simplest amino acid, glycine, NH 2 CH 2 COOH
(Holtom et al. 2005). In particular, the radical–radical reaction
of CH 2 NH 2 and HOCO in the gas phase, on grain surface,
and in bulk ice is considered to be one of the most feasible
glycine formation routes (see Joshi & Lee 2022, and references
therein). Another recent review (see Aponte et al. 2017, and references therein) provides an analysis of potential synthetic routes
of glycine and methylamine from a common set of precursors
present in carbonaceous chondrite meteorites, as both molecules
have also been detected in multiple extraterrestrial samples (e.g.,
Pizzarello & Holmes 2009).
Methylamine was first detected in the interstellar medium
(ISM) almost 50 years ago by observation of rotational transitions in its torsional ground state toward the high-mass star


⋆ Full Tables B.1 and B.2 are only available at the CDS via anonymous
ftp to `[cdsarc.cds.unistra.fr](https://cdsarc.cds.unistra.fr)` ( `[130.79.128.5](ftp://130.79.128.5)` ) or via `[https://](https://cdsarc.cds.unistra.fr/viz-bin/cat/J/A+A/677/A65)`
```
cdsarc.cds.unistra.fr/viz-bin/cat/J/A+A/677/A65

```


forming region Sagittarius B2 (Sgr B2) located in the Galactic
center region (Kaifu et al. 1974; Fourikis et al. 1974). For a long
time, methylamine was only securely detected toward Sgr B2, in
particular in its hot molecular cores, Sgr B2(N) and Sgr B2(M)
(Belloche et al. 2013; Halfen et al. 2013). With the imaging
spectral line survey Re-exploring Molecular Complexity with
ALMA (ReMoCA) performed toward Sgr B2(N) with the Atacama Large Millimeter/submillimeter Array (ALMA; Belloche
et al. 2019), the abundance of methylamine was found to be
0.07 relative to methanol toward the main hot core of Sgr B2(N)
(Kisiel et al. 2022; Motiyenko et al. 2020). Methylamine was
also detected in G+0.693–0.27, a shocked region of the Sgr B2
molecular cloud complex not related to the hot cores, with an
abundance of 0.2 relative to methanol, which is close to the value
derived toward the main hot core of Sgr B2(N) (Zeng et al. 2018;
Rodríguez-Almeida et al. 2021) [1] . A tentative detection for the
first time outside the Galactic center region was reported with


1 The column density of methylamine reported in Table 2 of Zeng et al.
(2018) is erroneous. The value should be ten times higher. However, the
abundance of methylamine relative to H 2 reported in their Table 5 is
correct (V. Rivilla, priv. comm.).


A65, page 1 of 17



[Open Access article, published by EDP Sciences, under the terms of the Creative Commons Attribution License (https://creativecommons.org/licenses/by/4.0),](https://www.edpsciences.org/en/)
which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.
[This article is published in open access under the Subscribe to Open model.](https://www.aanda.org/subscribe-to-open-faqs) [Subscribe to A&A to support open access publication.](mailto:subscribers@edpsciences.org)

Gyawali, P., et al.: A&A, 677, A65 (2023)



ALMA in the nearby star forming region Orion KL by Pagani
et al. (2017).
Nondetections of methylamine were reported in a number
of hot cores by Ligterink et al. (2015) with upper limits to
the abundance ratio of methylamine to methanol of between
0.02 and 2, most of them being at a similar level to the ratio
measured toward the main hot core of Sgr B2(N). However, a
nondetection was also reported toward the low-mass Class 0
protostar IRAS 16293–2422B, where the abundance of methylamine relative to methanol was determined to be lower than
5.3 × 10 [−][5], which is nearly three orders of magnitude lower
than in Sgr B2(N) (Ligterink et al. 2018). This substantial difference departs from the overall good correlation found by
Jørgensen et al. (2020) between the abundances of complex
organic molecules, that is, carbon-bearing molecules containing at least six atoms (Herbst & van Dishoeck 2009), in
IRAS 16293–2422B and the secondary hot core of Sgr B2(N).

Ohishi et al. (2019) detected methylamine with the
Nobeyama radio telescope in another hot core, G10.47+0.03.
Bøgelund et al. (2019) also managed to detect CH 3 NH 2 with
ALMA toward at least one hot core within the molecular
cloud complex NGC 6334 [2], with an abundance ratio relative to
methanol of about one order of magnitude lower than that found
for the main hot core of Sgr B2(N). These detections, along
with the detection in Orion KL, suggest that methylamine is
more widespread – albeit difficult to detect – in our Galaxy than
initially thought. Methylamine has even been detected with the
Australia Telescope Compact Array (ATCA) in the disk of a spiral galaxy at a redshift of 0.89 (Muller et al. 2011). The detection
was made in absorption against the bright background quasar
PKS 1830–211. Muller et al. (2011) derived a methylamine abundance on the order of 0.1–0.2 relative to methanol, which is similar to the ratios measured in the main hot core of Sgr B2(N) and
G+0.693–0.027.
On the chemical modeling side, the recent models of gasgrain chemistry in hot molecular cores presented by Garrod
et al. (2022) predict that methylamine is predominantly formed
in the ice mantles of dust grains at low temperature during
the prestellar phase. The ratio of peak gas-phase abundances of
methylamine to methanol during the warm-up phase predicted by
these models is in the range 0.03–0.04 depending on the warmup timescale, which agrees within a factor of about two with the
ratio reported above for the main hot core of Sgr B2(N). This
agreement suggests that the formation of methylamine in Sgr B2
is dominated by radical reactions in the solid phase rather than
gas-phase chemistry.
Given the intensities of the � t = 0 transitions of methylamine
measured toward Sgr B2(N1S) with the ReMoCA survey and
their rotational temperature of ∼230 K (Kisiel et al. 2022), we
expected the strongest � t = 1 transitions of methylamine to be
detectable above the 3σ level in this survey. Detecting such rotational transitions within the first torsionally excited state requires
laboratory measurements and a good spectroscopic modeling of
their frequencies and intensities.
So far, methylamine has only been detected in its ground
torsional state, mainly due to the lack of a complete and precise spectroscopic database in the excited states. In this paper,
we derive those parameters for the first excited torsional state of
methylamine. The methylamine rotational spectrum has a complex structure due to two coupled large-amplitude motions: the
methyl torsion and the amine inversion, or wagging. The ground


2 The other two detections reported in Fig. 2 of Bøgelund et al. (2019)
are debatable.


A65, page 2 of 17



rotational state of methylamine was successfully analyzed using
the effective Hamiltonian approach (high-barrier “tunneling”
approach) of Ohashi and Hougen (Ohashi & Hougen 1987). In
this approach, each � _t_ torsional state is fitted separately (with its
own set of molecular parameters). The analysis yielded an accurate model of the rotational spectrum in the � _t_ = 0 state (Ilyushin
et al. 2005; Motiyenko et al. 2014), but showed some limitations
with respect to the � _t_ = 1 state. To overcome these limitations, we
use a new hybrid model and the BELGI-hybrid code described
in Kleiner & Hougen (2015) which takes into account all the torsional states arising from internal rotation of the methyl group
of methylamine in a global way (Kleiner & Hougen 2020). The
second large-amplitude motion of the NH 2 inversion is taken into
account within the tunneling approach.
In our first paper on CH 3 NH 2 (Kleiner & Hougen 2020), we
used a dataset for � _t_ = 0 and 1 that combines previously published data in the infrared (Ohashi et al. 1987, 1988; Gulaczyk
et al. 2017) with data in the microwave spectral range (Motiyenko
et al. 2014; Ohashi et al. 1989; Kr˛eglewski & Wlodarczak 1992;
Ilyushin et al. 2005; Ilyushin & Lovas 2007), which were fitted using the tunneling formalism from Hougen and Ohashi.
We successfully fitted 11880 � _t_ = 1 ← 0 transitions in the farinfrared spectral range, as well as 2288 rotational transitions
belonging to the ground torsional state � _t_ = 0 in the microwave
spectral range, but we only fitted a limited number (137) of
pure rotational transitions belonging to the first excited state
� _t_ = 1–1. The aim of this paper is to extend our analysis
of the first torsionally excited state of methylamine using the
“hybrid” approach.
The paper is divided into five further sections. Section 2
describes the experimental details. Section 3 presents the spectral data used in the present fit. Section 4 describes the Hamiltonian theoretical model and BELGI-hybrid code that we used,
including the nuclear quadrupole hyperfine structure and the
intensity calculation. Section 5 presents the results of the search
for � _t_ = 1 rotational transitions of methylamine in the ISM, and
Sect. 6 gives a discussion of some spectroscopic and observational issues connected to our current results. The conclusions
of this work are presented in Sect. 7.


**2. Experimental details**


We performed a new series of measurements of the rotational
spectrum of methylamine in the framework of the present study.
All the spectra were recorded in absorption mode using the
Lille fast-scan hybrid spectrometer (Zakharenko et al. 2015;
Motiyenko et al. 2019). The measurements cover the frequency
range 150 – 1520 GHz with a few small gaps. We used a 99%
pure commercial sample of methylamine purchased from SigmaAldrich. The optimal gas pressure in the absorption cell for
the best signal-to-noise ratio (S/N) of the recorded spectra was
between 30 µbar and 60 µbar, with higher pressures preferred
at higher frequencies. Due to partially resolved or unresolved
nuclear quadrupole hyperfine structure, the measurement uncertainty is estimated to be around 60 kHz for relatively strong
isolated lines and 100 kHz for weak or slightly distorted line
shapes, and for the lines measured above 1 THz due to line
broadening effects (both Doppler and pressure).
As the main goal of the study is the assignment of excited
vibrational states, the spectra were acquired with an increased
amplitude resolution. In standard conditions, the spectral amplitude resolution is limited by the resolution of the analog-todigital converter. In the present study, we used a SR7270 DSP

Gyawali, P., et al.: A&A, 677, A65 (2023)



**Fig. 1.** Loomis-Wood diagram centered on predicted frequencies of _E_ 1
_c_ _Q_ -type series of transitions of methylamine with _K_ _a_ ′′ [=][ −][8][ ←] _[K]_ _a_ [′] [=][ −][7.]


lock-in amplifier, the ADC of which has a resolution of 16 bits.
To increase the amplitude resolution, each spectral segment was
recorded twice with two gain factors that differed by 20 dB.
Lower gain spectra were used to assign the strongest lines,
whereas higher gain spectra were particularly useful for the
assignment of weak lines in excited torsional states.


**3. Spectral data**


_3.1. Microwave, millimeter, and submillimeter data_


The assignment of the rotational spectrum of methylamine
in excited vibrational states was aided by Loomis-Wood-type
diagrams (Loomis & Wood 1928). These diagrams allow the
accurate assignment of broadband spectra, especially at the initial stage of analysis when predicted transition frequencies may
be significantly different from observed ones. The technique consists in superposing portions of spectra centered on predicted
frequencies of a particular series of transitions where only one
quantum number is varied and the rest are kept constant. In this
case, the shifts of the observed lines with respect to the predicted
ones exhibit a smooth (typically polynomial) behavior as a function of the varied quantum number and can be easily located on
the diagram. An example of a Loomis-Wood plot for a series
of � _t_ = 1–1 rotational transitions is shown in Fig. 1. This latter was built using the predicted frequencies from our previous
study (Kleiner & Hougen 2020). Even if the lines are shifted
with respect to predictions by 15 to 20 MHz, the smooth variation allows easy identification. After the series was included
in the fit, and after the refinement of the Hamiltonian parameters, the newly predicted frequencies almost coincide with the
observed ones. In this case, all experimental lines would be
vertically aligned on the new diagram. To build Loomis-Wood
plots, we used home-made software for spectral analysis, which
is available from the corresponding author upon request.
In the present study, using the new spectra records, the
dataset for the ground torsional state � _t_ = 0–0 was increased to
2790 microwave, millimeter and submillimeter transitions, compared to the published 2400 transitions up to _J_ = 40 from the



supplementary material from Motiyenko et al. (2014) and compared to our previous fit of 2288 transitions from Kleiner &
Hougen (2020). For the first excited state, about 212 microwave
lines existed in the literature (Ohashi et al. 1987, 1988; Gulaczyk
et al. 2017) and in our previous paper we only fitted 137 of
them (Kleiner & Hougen 2020). In the present work, we were
able to assign and fit 2921 new � _t_ = 1–1 rotational transitions.
These were combined with previously assigned � _t_ = 1–1 lines
in the frequency range 49–149 GHz (Motiyenko, priv. comm.).
These assignments were done using the spectrum records
obtained for methylamine by Ilyushin et al. (2005). In addition,
40 � _t_ = 2–2 rotational transitions were also newly assigned and
fitted. We also replaced 3 lines from Kr˛eglewski & Wlodarczak
(1992) and 132 lines from Ohashi et al. (1989) with our more

accurate measurements.
As in our previous paper, the frequency measurement
uncertainties of microwave transitions ranged between 20 kHz,
50 kHz, 60 kHz, 100 kHz, 200 kHz, and 500 kHz depending on
the measurement source. The hyperfine structure was removed
for most of those lines in the literature, but for some of them this
was done only by visual inspection, and so they were given a
weight of 500 kHz, whereas the hyperfine splittings for the lines
from Motiyenko et al. (2014) were removed properly, and so they
were given weights from 20 to 200 kHz (see Sect. 2 of Kleiner
& Hougen 2020).


_3.2. Far-infrared data_


The number of transitions in the far-infrared fundamental band
� _t_ = 1 ← 0 was kept about the same (11643) as in our previous
paper (11880) with _J_ up to 40 and _K_ up to 17. In the present fit,
we added 6155 transitions belonging to the hot band � _t_ = 2 ← 1
and 5253 transitions belonging to the overtone � _t_ = 2 ← 0
from (Gulaczyk et al. 2018; Gulaczyk & Kr˛eglewski 2020). We
decided to include neither the previously published ground state
� _t_ = 0 combination differences (GSCDs) – as their large number tends to decrease the impact of the more accurate microwave
transitions, thus causing the parameters to drift – nor the pure
rotational transitions � _t_ = 0–0, � _t_ = 1–1 or � _t_ = 2–2, which
were initially measured in the far-infrared range, as for a number of them our remeasurements in high-resolution THz spectra
obtained in this study showed discrepancies in the measured
frequencies of up to 30 MHz, which is much higher than the
microwave measurement accuracy.


_3.3. Hyperfine structure analysis_


In methylamine, the interaction of the [14] N electric quadrupolar
moment with the molecular field gradient results in the hyperfine structure of the rotational spectrum. The interaction couples
the nuclear spin _I_ to the molecular rotational angular momentum _J_ to form a resultant total angular momentum vector _F_ . As
the nuclear spin of [14] N is _I_ = 1, each rotational level of methylamine is split into three hyperfine sublevels: _F_ = _J_ + 1, _F_ = _J_,
and _F_ = _J_ − 1. The transitions between hyperfine levels obey the
selection rules ∆ _F_ = 0, ±1 and can give rise to a complex hyperfine structure for low- _J_ rotational transitions. With increasing _J_,
only hyperfine transitions with ∆ _F_ = ∆ _J_ selection rule are usually observed, as their sum of relative intensities represents more
than 99% of the total intensity of the hyperfine components for a
given rotational transition. Therefore, the hyperfine structure for
high- _J_ transitions of methylamine is usually represented by three
components.


A65, page 3 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Table 1.** [14] N nuclear quadrupole coupling parameters for methylamine


Parameter This study Motiyenko et al. (2014)


χ + (MHz) –2.4139(63) –2.4129(12)
χ − (MHz) 6.4058(85) 6.0697(25)
Transitions [(] _[a]_ [)] 1456 1132
rms [(] _[b]_ [)] (MHz) 0.0129 0.0082


**Notes.** [(] _[a]_ [)] Number of hyperfine transitions used in the fit. In this study,
the number of transitions includes 324 � _t_ = 1–1 hyperfine components
( _b_ ) Root-mean-square deviation of the hyperfine fit.



**Fig. 2.** Partially resolved hyperfine structure of the � _t_ = 1–1 14 1,13 –14 0,14
_E_ 1 transition of methylamine. The stick spectrum shows the calculated
positions of hyperfine components.


Due to Doppler-limited spectral resolution, the hyperfine
structure in the spectrum of methylamine has only been partially
resolved for a limited number of rotational transitions. A resolved
pattern of the hyperfine structure was observed as a doublet with
an intensity ratio of 2:1. The stronger doublet component contains unresolved transitions with _F_ [′] = _J_ [′] + 1 ← _F_ = _J_ + 1 and
_F_ [′] = _J_ [′] − 1 ← _F_ = _J_ − 1 selection rules, whereas the weaker
doublet component corresponds to the _F_ [′] = _J_ [′] ← _F_ = _J_ transition. An example of partially resolved hyperfine structure for a
� _t_ = 1–1 rotational transition of methylamine is shown in Fig. 2.
Each hyperfine transition frequency may be expressed as


_f_ hf = _f_ rot + _[E]_ [hf] [(] _[I]_ [,] _[ J]_ [′] [,] _[ F]_ [′] [)][ −] _[E]_ [hf] [(] _[I]_ [,] _[ J]_ [,] _[ F]_ [)], (1)

_h_


where _f_ rot is the hyperfine-free central frequency and _E_ hf denotes
the addition to the energy due to hyperfine coupling. _E_ hf may be
expressed in terms of rotational angular momentum operators
and nuclear quadrupole coupling tensor components χ _i j_, _i_, _j_ =
_a_, _b_, _c_ as (Ilyushin et al. 2005):



1
_E_ hf ( _I_, _J_, _F_ ) = � 2 [χ] [+] � _J_ _b_ [2] [+] _[ J]_ _c_ [2] [−] [2] _[J]_ _a_ [2] � − 2 [1]



2 [χ] [−] � _J_ _b_ [2] [−] _[J]_ _c_ [2] �



(2)

+ χ _ab_ ⟨ _J_ _a_ _J_ _b_ + _J_ _b_ _J_ _a_ ⟩ 2 _f_ ( _I_, _J_, _F_ )/ _J_ ( _J_ + 1)
�



rotational transition frequencies, each hyperfine component
was fitted to Eq. (1). The linear least-squares Gauss-Newton
algorithm was applied using a dedicated Python code. In the
present study, we assigned 324 partially resolved hyperfine
components of � _t_ = 1–1 rotational transitions. These were fitted
together with 1132 � _t_ = 0–0 components from this and previous
studies (Ilyushin et al. 2005; Motiyenko et al. 2014) to yield
653 hyperfine-free rotational transition frequencies and two
hyperfine constants χ + and χ −, the values of which are given in
Table 1. As a point of comparison, the last column of Table 1
provides the corresponding values obtained using high-barrier
tunneling Hamiltonian expectation values. As can be seen from
Table 1, the χ + values match well, whereas the χ − values are
outside the confidence intervals of both studies. This significant
difference in the χ − parameter probably arises from the different
Hamiltonians used for obtaining expectation values of the necessary rotational operators. In this connection, it is interesting
to note that our current value for χ − = 6.4058(85) MHz is in
much better agreement with χ − = 6.3746(81) MHz obtained by
Kr˛eglewski et al. (1992), which supports our hypothesis that the
difference with our previous result is caused by the difference in
the Hamiltonian models used.


**4. Theoretical model and analysis**


The theoretical Hamiltonian model used in our fit is the so-called
hybrid Hamiltonian, which allows us to deal with the two coupled large-amplitude motions present in methylamine, namely
the internal rotation of the methyl group CH 3 and the backand-forth oscillatory inversion motion, or wagging, of the amine
group NH 2 . This approach has been tested in the ground torsional state of methyl-malonaldehyde (Kleiner & Hougen 2015),
and also in our previous study of the ground and first excited
state of methylamine (Kleiner & Hougen 2020).
As the hybrid model and the BELGI-hybrid code have been
presented in detail elsewhere (Kleiner & Hougen 2015, 2020),
here we only give a short summary of the approach. In the hybrid
Hamiltonian, we mix two methods to deal with the coupling of
two large-amplitude motions. The first method treats the internal rotation of the CH 3 group in a similar way to the method
presented in the series of BELGI programs (Kleiner et al. 1992;
Kleiner 2010). Those “BELGI”-type terms contain an explicit
form for the potential barrier hindering the methyl internal rotation or torsion. For the internal rotation of the CH 3 group, the
rotation–torsion Hamiltonian has the form:


_H_ _TR_ = _F_ ( _P_ α − ρ _J_ _z_ ) [2] + _V_ (α) + _AJ_ _z_ [2] [+] _[ BJ]_ _x_ [2] [+] _[ CJ]_ y [2] [+][ higher order]


torsion–rotation terms as found in the BELGI code,

(3)



where χ + = −χ _aa_, χ − = χ _cc_ − χ _bb_ and _f_ ( _I_, _J_, _F_ ) is the Casimir
function (Gordy & Cook 1984).
Equations (1) and (2) were used to obtain hyperfine-free
rotational transition frequencies _f_ rot for the global fit. We used
a perturbation approach similar to that used for acetamide, a
_C_ _s_ molecule with one methyl internal rotor large-amplitude
motion, and one nitrogen quadrupole nucleus (see Eq. (1)
of Suenram et al. 2001). The same approach was also used
in the analysis of the ground-state rotational spectrum of
12 _C_ −methylamine (Ilyushin et al. 2005; Motiyenko et al.
2014) and [13] _C_ −methylamine (Motiyenko et al. 2016). Using
the BELGI-hybrid code, we obtained the rotation-torsion
eigenvalues and eigenvectors from the usual two-step diagonalization of the Hamiltonian _H_ WTR, as described in Sect. 4. The
global fitting BELGI-hybrid program was modified to output
expectation values of ⟨ _J_ _a_ ⟩ [2], ⟨ _J_ _b_ ⟩ [2], ⟨ _J_ _c_ ⟩ [2], and ⟨ _J_ _a_ _J_ _b_ + _J_ _b_ _J_ _a_ ⟩
in the rho axis system ( _a_, _b_, _c_ ). To obtain hyperfine-free


A65, page 4 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Table** **2.** Overview of a fit of 28 802 transitions of methylamine with _J_ ≤ 40, _K_ ≤ 17, using 79 parameters floated to give a weighted standard
deviation of 1.53.


Previous study (Kleiner & Hougen 2020) Present work
Transitions [(] _[a]_ [)] Number [(] _[b]_ [)] WRMS [(] _[c]_ [)] RMS [(] _[d]_ [)] Number [(] _[b]_ [)] WRMS [(] _[c]_ [)] RMS [(] _[d]_ [)]


Microwave v _t_ = 0 2288 1.07 0.088 MHz 2790 2.38 0.154 MHz
Microwave v _t_ = 1 137 1.39 0.154 MHz 2921 3.35 0.218 MHz
Microwave v _t_ = 2 – – – 40 3.10 0.289 MHz


MW A/B [(] _[e]_ [)] species 1098 1.04 2287 3.03
MW E [(] _[f]_ [)] species 1327 1.13 3464 2.85


Infrared v _t_ = 1 ← 0 11 880 1.09 0.00053 cm [−][1] 11 643 0.29 0.00015 cm [−][1]

Infrared v _t_ = 2 ← 1 – – 6155 1.25 0.00063 cm [−][1]

Infrared v _t_ = 2 ← 0 – – 5253 1.27 0.00064 cm [−][1]


Present work
Exp. Unc. [(][g][)] Number [(] _[b]_ [)] WRMS [(] _[c]_ [)] RMS [(] _[d]_ [)]

0.0008 cm [−][1] 23 051 0.59 0.00047 cm [−][1]

0.020 MHz 390 4.45 0.089 MHz

0.045 MHz 210 3.89 0.194 MHz

0.060 MHz 3293 3.05 0.183 MHz

0.100 MHz 1626 2.12 0.212 MHz

0.200 MHz 105 1.33 0.257 MHz

0.500 MHz 127 0.48 0.238 MHz


**Notes.** [(] _[a]_ [)] Transitions in the upper part of this table are grouped by their torsional � _t_ quantum numbers and/or symmetry species. [(] _[b]_ [)] Number of lines
in the category of this row included in the fit. [(] _[c]_ [)] Weighted root-mean-square residual for the lines in this row. [(] _[d]_ [)] Root-mean-square residual in the
units of measurement for the lines in this row. [(] _[e]_ [)] Microwave A 1, A 2, B 1 and B 2 species. [(] _[ f]_ [)] Microwave E 1, E 2 species. [(][g][)] Transitions in the lower
part of this table are grouped by assigned measurement uncertainty.



where _F_ is the internal rotation constant, _P_ α is the internal rotation angular momentum, ρ is the coupling constant between
internal and global rotation, _J_ _x_, _J_ y, and _J_ _z_ are angular momentum projections along _x_, y, and _z_ molecular axes, and _V_ (α) is the
potential internal rotation barrier described as a Fourier series:



Eq. (1) of Kleiner & Hougen (2020), with blocks noted by
_L_ (eft) _L_ (eft), _L_ (eft) _R_ (ight), RL, and RR:



LL LR

[ _H_ ] =
RL RR
�



, (5)
�



_V_ (α) = _[V]_ [3]




[3]

_[V]_ [6]
2 [(1][ −] [cos 3][α][)][ +] 2



2 [(1][ −] [cos 6][α][)]



+ _[V]_ [9] (4)

2 [(1][ −] [cos 9][α][)][ +][ ...]



where _H_ RR corresponds to the torsion-rotation Hamiltonian,
which is identical to that used in the BELGI series of codes
for the one-top molecules, where the amino group NH 2 of the
methylamine molecule is locked in one of its two symmetrically equivalent equilibrium inversion positions and is localized
in a well on the positive side of the γ axis, where γ designates the inversion or wagging coordinate. _H_ LL represents the
BELGI matrix, which corresponds to a methylamine molecule
with the amino group locked in the other of the two symmetrically equivalent equilibrium inversion positions and localized
in the negative side of the γ axis. _H_ RL and _H_ LR contain matrix
elements that describe the amino group tunneling from the positive region of γ to the negative region, or vice versa; that is, they
describe inversion motion.


_4.1. Fit with the hybrid formalism_


The BELGI-hybrid code globally fits a large microwave, millimeter, and submillimeter dataset for 2790 � _t_ = 0–0, 2921 � _t_ =
1–1, and 40 � _t_ = 2 − 2 pure rotational transitions, as well as the
far-infrared dataset involving 11643 � _t_ = 1 ← 0, 6155 � _t_ = 2 ←
1, and 5253 � _t_ = 2 ← 0 transitions up to _J_ = 40.
As can be seen from Table 2, we achieve a global unitless
standard deviation of 1.53 for 28802 transitions. The quality of
the fit is satisfactory, although not completely within experimental uncertainty for the microwave transitions. The upper part


A65, page 5 of 17



The second method treats the back-and-forth (wagging) motion
of the amino group NH 2 using the tunneling approach as
described by Ohashi & Hougen (1987). Those tunneling-type
terms, which contain matrix elements associated with tunneling
between the two positions of the amino group, do not contain any explicit form for the double-well tunneling potential.
Instead _H_ = _T_ + _V_ for the wagging motion is replaced with one
tunneling splitting parameter plus higher-order torsion–rotation
corrections.
Here, we used a two-step diagonalization procedure similar
to the one used in the one-top BELGI code (Kleiner et al. 1992;
Kleiner 2010). In the first step, we diagonalize the torsion-Krotation part of the matrix associated with the two first terms
of the Hamiltonian given in Eq. (3). We separate the nondegenerate torsional-wagging-rotational (twr) states (of symmetry
species [twr] _A_ 1 ⊕ [twr] _A_ 2 ⊕ [twr] _B_ 1 ⊕ [twr] _B_ 2 ) from the set of doubly
degenerate states (of species [twr] _E_ 1 ⊕ [twr] _E_ 2 ) using the σ = 0
and σ = − [+] 1 characters associated with irreducible representations of the permutation-inversion _G_ 12 group. We then separately
diagonalize the Hamiltonian matrix for each of those two sets.
This torsion-wagging-rotational hybrid Hamiltonian matrix
_H_ twr is partitioned into four square submatrices, as shown in

Gyawali, P., et al.: A&A, 677, A65 (2023)



of the table presents transitions grouped by their torsional � _t_
quantum numbers (and spectral range) and/or symmetry species.
The lower part of the table shows root-mean-squared deviations
grouped by assigned measurement uncertainty.
The 79 floated molecular parameters (plus eight additional
parameters, which were fixed at values from previous fits, such
as _F_, _V_ 9, _D_ _K_, WCPG (which multiplies the _P_ γ _J_ y operator),
and some higher order _K_ dependent parameters) are listed in
Table A.1 and compared to the 74 floated and two fixed parameters in the previous work, where we fitted a total of 15081
transitions (Kleiner & Hougen 2020). The increase in the number of parameters is very reasonable considering that the number
of lines increased by almost a factor of two. As detailed in
Kleiner & Hougen (2020), the first column of Table A.1, labeled
_ntr_ w, contains four indices describing the order of the term with
_n_ = _t_ + _r_ + w, where _t_ and _r_ are the traditional torsional and rotational orders and w is the amino wagging order (see Kleiner &
Hougen 2020 for details). The second column gives the name
of the molecular parameter as used in the BELGI-hybrid code
and the operator that it multiplies. These operators must all be:
(i) Hermitian, (ii) of species _A_ 1 in the permutation-inversion
group G 12 (Kleiner & Hougen 2015), and (iii) invariant to
time reversal. The third column gives numerical values for the
molecular parameters obtained from the previous fit (Kleiner &
Hougen 2020), and the fourth column gives the values of the
parameters as obtained from the present fit described in Table 2,
together with their standard errors. As already mentioned in
Kleiner & Hougen (2020), we note that a factor of γ was omitted in three operators of Table 5 of Kleiner & Hougen (2015),
namely those multiplied by the coefficients DAB, ODAB, and
ODELTA in that table. The correct operators are those given in
Table A.1 here, where we also change the name of the ODELTA
parameter to AXGK.
Compared to our previous fit, the variation of the secondorder term in the potential ( _V_ 6 ) is relatively large, showing the
influence of the � _t_ = 1 and 2 excited states in determining the
potential terms in the Fourier expansion. We also noticed that a
number of low-order parameters have changed sign (such as _V_ 6,
AXG, and DAB which multiply 2 [1] [(1][ −] [cos 6][α][) term,][ γ] _[P]_ [α] _[J]_ _[x]_ [term]

and γ{ _J_ _x_, _J_ _z_ } respectively).
Compared to the previous tunneling fits of the literature,
here a large reduction in parameters is obtained in our global
fit, because the 55 + 88 = 143 tunneling parameters used in
the final fit of Gulaczyk & Kr˛eglewski (2020) are reduced by
almost a factor of 1.6 to 79 (+8 fixed parameters) in Table A.1.
For the far-infrared data, our rms deviations for the fundamental band � _t_ = 1 ← 0, the hot band � _t_ = 2 ← 1, and the overtone
v _t_ = 2 ← 0 are 0.00015 cm [−][1] for 11643 lines, 0.00063 cm [−][1] for
6155 lines, and 0.00064 cm [−][1] for 5253 lines compared to the
rms of 0.00058 cm [−][1] for 12237 lines, 0.00209 cm [−][1] for 6609
lines, and 0.00197 cm [−][1] for 7735 lines obtained in Gulaczyk &
Kr˛eglewski (2020) for the same bands, respectively. This comparison is not totally fair because the number of transitions fitted
in Gulaczyk & Kr˛eglewski (2020) is not the same as ours; in their
study they fit up to _J_ = 50. In the present work, because of the
size of the matrix that we need to take into consideration in our
global approach and the computer time required subsequently,
we decided to fit only up to _J_ = 40.
In the microwave spectral range, the rms we obtained for the
fit of the ground torsional � _t_ = 0–0 state is higher (154 kHz)
than the rms obtained by the tunneling approach (102 kHz),
but we included 236 more lines in our fit (2790 lines instead
of 2554 lines) than in Gulaczyk & Kr˛eglewski (2020). For the
first excited state � _t_ = 1–1, we obtained a rms of 218 kHz for


A65, page 6 of 17



2921 lines. In Gulaczyk & Kr˛eglewski (2020), only 214 transitions were available at that time and these authors fitted them
with a rms of 183 kHz. Finally, our � _t_ = 2–2 data fit with a rms
of 289 kHz.
In a general way, and this was also noticed in our previous
paper (Kleiner & Hougen 2020), poorly fitted lines belong to
high _J_ and/or high _K_ transitions and this tendency is also visible
in the microwave spectral range. A number of transitions � _t_ = 1–
1 with _K_ = 0 and 1 in the _A_ and _B_ nondegenerate species did
not fit either within experimental accuracy, and large observedcalculated values of up to 1 or 2 MHz are observed. The energy
levels of those transitions were shown by Ohashi et al. (1989,
see their Figs. 1 and 2) to contribute to an avoided crossing in
the case of the _B_ species and to an unavoided crossing for the _A_
species series. We used several Hamiltonian terms with matrix
elements connecting energy levels differing by ∆ _K_ = ±1 to take
into account this perturbation, such as DAB, AXG, DAC (see
Table A.1) and so on, but we did not succeed in decreasing the
observed-calculated values for those lines with _K_ = 0 and 1 and
we finally omitted them in the fit.
The lists of rotational and rovibrational transitions of methylamine are presented in Tables B.1 and B.2 and are available
at the CDS [3] . In the first ten columns of both tables, the quantum numbers for each spectral line are given: � _t_, _J_, _K_ _a_, _K_ _c_, and
symmetry label Γ. In the subsequent four columns, we provide
the observed transition frequencies, measurement uncertainties,
residuals from the fit, and a binary flag indicating whether
the transition was included in the final fit. The last column of
Table B.1 contains a reference from which the measurements
were obtained. The last column of Table B.2 contains an optional
flag “L” for � _t_ = 2 ← 1 and � _t_ = 2 ← 0 transitions of _A_ 1, _A_ 2,
_B_ 1, and _B_ 2 symmetries. The flag indicates that the _K_ _a_ = 2 and
_K_ _a_ = 4 labels are reversed compared to the labels from Gulaczyk
& Kr˛eglewski (2020). This difference in the labeling occurs during the procedure of assignment of the _K_ _a_ quantum number after
the diagonalization of the Hamiltonian matrix and reveals the
mixing of the eigenfunctions.


_4.2. Intensity calculation_


The BELGI-hybrid code was modified to provide the line
strength calculations for methylamine transitions. The line
strength ( _S_ ) of the torsion-rotation transition between the level _L_ [′]
containing all (2 _J_ [′] + 1) _M_ [′] components and the level _L_ containing all (2 _J_ + 1) _M_ components is given by the formula (Ilyushin
& Lovas 2007):



_S_ ( _L_ [′] ; _L_ ) = [1]



3
����� �
_M_



�

_K_ [′], _K_ =− _J_, _J_
v [′′′] _t_ [,v] [′′] _t_ [=][0][,] _[N]_ _[t]_ [−][1]



�
µ [2]



g



_t_ [,σ] [′] [,w] [′]
_C_ _[J]_ [′] [,τ] [′] [,v] [′] _C_ _[J]_ [,τ,][�] _[t]_ [,σ,w]

_K_ [′],v [′′′] _t_ _K_,v [′′] _t_



2
× ⟨ _K_ [′], v [′′′] _t_ [, σ] [′] [, w] [′] [|][ µ] [g] [|] _[K]_ [, v] [′′] _t_ [, σ, w][⟩× ⟨] _[J]_ [′] [,] _[ K]_ [′] [,] _[ M]_ [|][ Φ] _[Z]_ [g] [|] _[J]_ [,] _[ K]_ [,] _[ M]_ [⟩],
�����

(6)


where | _K_, v _t_, σ, w⟩ and | _J_, _K_, _M_ ⟩ are the torsion-rotation-inversion
and symmetric rotor basis functions used to set up the waggingtorsion-rotation Hamiltonian matrix for the second diagonalization step; the coefficients _C_ _K_ _[J]_ [,τ,v],v [′′] _t_ _[t]_ [,σ,w] are the eigenvectors
coefficients obtained after diagonalization of the waggingtorsion-rotation Hamiltonian matrix; the Φ _Z_ g represents direction cosines, and µ g is the electric dipole moment along the


3 `[http://cdsweb.u-strasbg.fr/](http://cdsweb.u-strasbg.fr/)`

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Fig.** **3.** Observed (in blue) and predicted (in red) � _t_ = 0–0 and � _t_ = 1–1 rotational spectrum of methylamine around 1.38 THz. The individual
contributions of � _t_ = 0–0 and � _t_ = 1–1 transitions are shown in magenta and green, respectively. Regular series of lines refer to _[c]_ _Q_ -type transitions
with _K_ _a_ = 9 ← 8 and symmetry selection rules: _E_ 1 ← _E_ 1 for � _t_ = 0–0, and _E_ 1 ← _E_ 1 (stronger) and _E_ 2 ← _E_ 2 (weaker) for � _t_ = 1–1.



molecular-fixed g = _x_, y, _z_ axis. The electric dipole moment is a
function of the methyl torsion angle α and of the amino umbrella
γ coordinate (Ilyushin & Lovas 2007). The torsional dependence
of µ g is given as a Fourier expansion in the torsional angle
(see Eq. (19) of Hougen et al. 1994). For the present work,
we are concerned with the intensities of pure rotational transitions and so we neglect the cosine and sine dependence of the
dipole moment components, and keep only the leading (independent of α) terms. We also neglected the tunneling contributions
in γ of the dipole moments, as was also done in Ilyushin &
Lovas (2007). For methylamine, the nonzero value of the dipole
moment components are µ _a_ (µ _z_ ) and µ _c_ (µ _x_ − [+] _i_ µ y ).
In the Principal Axis Method (PAM), the dipole moment
components are measured using Stark effect measurements by
Lide (1957), and are then corrected by Takagi & Kojima (1973)
with µ _a_ = −0.307 D and µ _c_ = 1.258 D. In the Rho Axis Method
(RAM), those values need to be transformed using Eq. (20) of
Kleiner (2010), but since for methylamine the angle between
PAM and RAM is very small, the values we used for the
dipole moments in this system, namely µ _a_ = −0.226 D and
µ _c_ = 1.275 D, are very close to the PAM ones.
As the hyperfine splittings for methylamine can reach up
to a few MHz and are essential in correctly fitting the astronomical spectra, we also calculate the relative intensities of
the quadrupole hyperfine components using the formula given
by Townes & Schawlow (1955). We multiply the µ [2] _S_ of each
rotational transition by the relative intensity of the quadrupole
component. For the intensity calculation we also had to take into
account the nuclear spin statistical weight ( _W_ st ), which is equal
to 1 for _A_ 1, _A_ 2, and _E_ 2 species and to 3 for _B_ 1, _B_ 2, and _E_ 1 .
The calculated � _t_ = 1–1 rotational spectrum of methylamine
is available at the Lille Spectroscopic Database [4] (LSD) in two
versions: (1) pure rotational transition frequencies, and (2) a
rotational spectrum, taking the nuclear hyperfine structure into


4 `[https://lsd.univ-lille.fr/](https://lsd.univ-lille.fr/)`



account. The spectra may be generated with different line “intensity” units: line strength (D [2] ), Einstein _A_ _i j_ coefficients (s [−][1] ), and
absorption cross-sections (nm [2] MHz/molecule). For the latter,
the rotational partition function calculated from first principles
by Motiyenko et al. (2014) is used. We also note that although
the “hybrid” global model used in the present study predicts
both � _t_ = 0–0 and � _t_ = 1–1 rotational transitions, in the LSD, we
decided to keep the spectral predictions calculated by Motiyenko
et al. (2014) as the entries for � _t_ = 0–0 spectra. We did this for
two reasons. First, the effective high-barrier tunneling Hamiltonian model from Motiyenko et al. (2014) covers the wider range
of rotational quantum numbers up to _J_ ≤ 50, whereas present
hybrid model fits rotational levels only up _J_ ≤ 40 (this reduction in the upper value of _J_ is caused by the necessity to keep
the computation time within reasonable limits in the case of the
hybrid approach because it deals with a much larger basis set
than high-barrier tunneling Hamiltonian). Second, we believe
that for the � _t_ = 0–0 transitions, high-barrier tunneling formalism provides predictions of slightly better accuracy, as evidenced
by the better rms and weighted rms deviations achieved for � _t_ =
0–0 in Motiyenko et al. (2014) in comparison with our current
result with the hybrid approach. This is due to the fact that separate state models of the high-barrier tunneling approach do not
need to accommodate torsion–rotation and intervibrational perturbations from higher excited states in methylamine. However,
this advantage of the high barrier tunneling formalism becomes
a disadvantage when we need to deal with the first excited torsional state, where the hybrid approach indeed shows much
better results. Therefore, at present, we believe that it is better to
use predictions based on the high-barrier tunneling Hamiltonian
of Motiyenko et al. (2014) for � _t_ = 0–0 transitions and predictions
based on the current hybrid approach for � _t_ = 1–1 transitions.
To illustrate the quality of the rotational transitions of methylamine in the ground and first excited torsional states calculated
in this study, we compare an experimental (in blue) and a modeled (in red) spectrum around 1.38 THz in Fig. 3; here, we also


A65, page 7 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Table 3.** Parameters of our best-fit LTE model of methylamine (with hyperfine structure) toward Sgr B2(N1S).


Molecule Status [(] _[a]_ [)] _N_ det [(] _[b]_ [)] Size [(] _[c]_ [)] _T_ rot [(] _[d]_ [)] _N_ [(] _[e]_ [)] _F_ vib [(] _[ f]_ [)] ∆ _V_ [(][g][)] _V_ off [(] _[h]_ [)] _NN_ ref ( _i_ )

( [′′] ) (K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] )


CH 3 NH 2, � = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1
� t = 1 d 5 2.0 230 1.4 (18) 1.25 5.0 0.0 1


**Notes.** [(] _[a]_ [)] d: detection. [(] _[b]_ [)] Number of detected lines (conservative estimate, see Sect. 3 of Belloche et al. 2016). One line of a given species may mean
a group of transitions of that species that are blended together. [(] _[c]_ [)] Emission size (FWHM). [(] _[d]_ [)] Rotational temperature. [(] _[e]_ [)] Total column density of the
molecule. _x_ (y) means _x_ × 10 [y] . [(] _[f]_ [)] Correction factor that was applied to the column density to account for the contribution of vibrationally excited
states in the cases where this contribution was not included in the partition function of the spectroscopic predictions. [(][g][)] Line width (FWHM).
( _h_ ) Velocity offset with respect to the assumed systemic velocity of Sgr B2(N1S), _V_ sys = 62 km s −1 . ( _i_ ) Column density ratio, with _N_ ref the column
density of the previous reference species marked with a ⋆.



show individual contributions of � _t_ = 0–0 and � _t_ = 1–1 transitions. Overall, the agreement in terms of frequency and relative
intensity is good. We also note that, in this frequency region,
the great majority of strong lines refer to � _t_ = 0–0 and � _t_ = 1–1
transitions.


**5. Interstellar detection of methylamine in its first**
**torsionally excited state**


_5.1. Observations_


The imaging spectral line survey Reexploring Molecular Complexity with ALMA (ReMoCA) targeted the high-mass star
forming protocluster Sgr B2(N) with ALMA. We used this
survey to carry out an interstellar search for methylamine in
its first torsionally excited state. The main features of the survey are summarized below. More details about the observations
and data reduction can be found in Belloche et al. (2019). The
phase center is located at the equatorial position (α, δ) J2000 =
(17 [h] 47 [m] 19 [s] .87, −28 [◦] 22 [′] 16 [′′] . 0), which is halfway between the two
hot molecular cores Sgr B2(N1) and Sgr B2(N2). The survey
covers the frequency range from 84.1 GHz to 114.4 GHz at a
spectral resolution of 488 kHz (1.7 to 1.3 km s [−][1] ). This coverage was obtained with five different frequency tunings. The
observations achieved a sensitivity per spectral channel ranging
between 0.35 mJy beam [−][1] and 1.1 mJy beam [−][1] (rms) depending
on the setup, with a median value of 0.8 mJy beam [−][1] . The angular resolution (half-power beam width, HPBW) varies between
∼0.3 [′′] and ∼0.8 [′′] with a median value of 0.6 [′′] that corresponds
to ∼4900 au at the distance of Sgr B2 (8.2 kpc, Reid et al. 2019).
Here, we used the slightly improved version of the data reduction
that one of us described in Melosso et al. (2020).
As in Belloche et al. (2019), we analyzed the spectrum obtained toward the position Sgr B2(N1S) at (α, δ) J2000 =
(17 [h] 47 [m] 19 [s] .870, −28 [◦] 22 [′] 19 [′′] . 48), which is offset by about 1 [′′] to
the south of the main hot core Sgr B2(N1). This position was
chosen for its lower continuum opacity compared to the peak of
the hot core. We compared the observed spectrum to synthetic
spectra computed under the assumption of local thermodynamic
equilibrium (LTE) with the astronomical software Weeds (Maret
et al. 2011). This assumption is justified by the high densities of
the regions where hot-core emission is detected in Sgr B2(N)
(> 1 × 10 [7] cm [−][3], see Bonfand et al. 2019).
The software takes the angular resolution of the observations
and the optical depth of the rotational transitions into account.
We derived a best-fit synthetic spectrum for each molecule separately, and then added together the contributions of all identified
molecules. Each species was modeled with a set of five parameters: size of the emitting region (θ s ), column density ( _N_ ),


A65, page 8 of 17



temperature ( _T_ rot ), line width (∆ _V_ ), and velocity offset ( _V_ off )
with respect to the assumed systemic velocity of the source,
_V_ sys = 62 km s [−][1] . The line width and velocity offset are obtained
directly from the well-detected and uncontaminated lines. The
emission of complex organic molecules is extended over several arcseconds around Sgr B2(N1) (see Busch et al. 2022). For
the LTE modeling, we assumed an emission size of 2 [′′], as in
Belloche et al. (2019), which is much larger than the beam, meaning that the derived column densities do not depend on the exact
value of this size parameter.


_5.2._ _Detection of CH_ _3_ _NH_ _2_ _in its first torsionally excited state_


One of us reported the detection of methylamine in its torsional ground state toward Sgr B2(N1S) in Kisiel et al. (2022;
see their Fig. A.5). The analysis presented in this latter study
used the spectroscopic entry 31008 (version 1) available in the
Jet Propulsion Laboratory (JPL) spectroscopic database (Pickett
et al. 1998), which is based on the combined fit by Ilyushin et al.
(2005). This entry does not account for the hyperfine structure
of methylamine. However, we found that the spectral broadening
due to the hyperfine structure is not negligible for some methylamine lines given the typical line width of 5 km s [−][1] (about
1.7 MHz) toward Sgr B2(N1S). Therefore, here we used the
spectroscopic entry 31802 (version 2021.08) of the LSD, which is
based on Motiyenko et al. (2014) and accounts for the hyperfine
structure.
The LTE synthetic spectrum computed with the LSD entry
using the same LTE parameters as those reported in Table 3
of Kisiel et al. (2022) is compared to the ReMoCA spectrum
of Sgr B2(N1S) in Fig. C.1. These LTE parameters are listed
in Table 3. A detailed comparison of Fig. A.1 to Fig. A.5 of
Kisiel et al. (2022) shows that the hyperfine structure does indeed
broaden several lines of methylamine and in turn reduces their
peak temperature compared to the previous study, where the
hyperfine structure was not accounted for (see, e.g., the lines at
84.215, 86.075, or 95.146 GHz). As a result, several lines that
were counted as detected in Table 3 of Kisiel et al. (2022) are
now below the threshold considered here to count a line as firmly
detected. The adopted threshold depends on the degree of contamination of the line, but it roughly corresponds to two-thirds of
the peak of the observed line. To count a given line as detected,
we also require that there be a clear peak in the observed spectrum at the frequency of this line, and that the peaks of both the
synthetic and observed lines be above three times the rms noise
level (dotted lines in the figures). With these criteria, we count
10 lines of methylamine in its torsional ground state as detected
in Fig. C.1 while 15 were counted in the previous study that

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Fig.** **4.** Selection of rotational transitions of methylamine CH 3 NH 2 in its first torsionally excited state covered by the ReMoCA survey. The LTE
synthetic spectrum of CH 3 NH 2 � t = 1 is displayed in red and overlaid on the observed spectrum of Sgr B2(N1S) shown in black. The blue synthetic
spectrum contains the contributions of all molecules identified in our survey so far, including the contribution of the species shown in red. The
values written below each panel correspond from left to right to the half-power beam width, the central frequency in MHz, the width in MHz of each
panel in parentheses, and the continuum level in K of the baseline-subtracted spectra in brackets. The y-axis is labeled in brightness temperature
units (K). The dotted line indicates the 3σ noise level. The green stars highlight the lines of methylamine in its first torsionally excited state that
are not excessively contaminated by emission from other species and are counted as detected lines in Table 3.



ignored the hyperfine structure of methylamine. The ten detected
ground-state lines of methylamine are marked with a green star
in Fig. C.1.
We computed an LTE synthetic spectrum of the rotational
transitions of methylamine in its first torsionally excited state
using the spectroscopic predictions obtained in Sect. 4 and
assuming the same LTE parameters as for the torsional ground
state. This synthetic spectrum is a good match to the ReMoCA
spectrum of Sgr B2(N1S) (see Fig. 4). Many transitions are contaminated by emission from other molecules, but five lines of
CH 3 NH 2 � t = 1 are strong enough and sufficiently uncontaminated to be counted as detected. They are highlighted with a



green star in Fig. 4. One comment should be made concerning
the � _t_ = 1 line of methylamine at 86657 MHz. The two strong
transitions on each side of this line are from ethylene glycol
(CH 2 OH) 2 . As can be seen in Fig. 4, the LTE model displayed in
blue, which includes the contribution of all identified molecules,
slightly overestimates the widths of these ethylene glycol lines
in this frequency range, which artificially increases the contamination of the methylamine line that lies in between. This is why
we still consider this line of methylamine as being sufficiently
uncontaminated.
We produced a population diagram that includes transitions
from both torsional states (Fig. 5). After correction for the


A65, page 9 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)



**Fig.** **5.** Population diagram of CH 3 NH 2 toward Sgr B2(N1S). The
observed data points are shown in black for � = 0 and in blue for � t = 1
while the synthetic populations are shown in red. No correction is
applied in panel a. In panel b, the optical depth correction has been
applied to both the observed and synthetic populations and the contamination by all other species included in the full model has been
subtracted from the observed data points. The purple line is a linear
fit to the observed populations (in linear-logarithmic space).


**Table** **4.** Rotational temperature of methylamine derived from its
population diagram toward Sgr B2(N1S).


Molecule States [(] _[a]_ [)] _T_ fit [(] _[b]_ [)]

(K)


CH 3 NH 2 � = 0, � t = 1 222 ( 8)


**Notes.** [(] _[a]_ [)] Vibrational states that were taken into account to fit the population diagram. [(] _[b]_ [)] The standard deviation of the fit is given in parentheses.
As explained in Sect. 3 of Belloche et al. (2016) and in Sect. 4.4 of
Belloche et al. (2019), this uncertainty is purely statistical and should be
viewed with caution. It may be underestimated.


optical depth of the lines and subtraction of the contamination from other molecules included in our full model (i.e., the
difference between the blue and red spectra in Figs. C.1 and
4), the observed data points are roughly distributed along a
straight line, which indicates that the emission of methylamine
in both torsional states can be described by a single temperature
component. A fit to the population diagram yields a rotational
temperature of 222 ± 8 K, as reported in Table 4. The temperature that we assumed for the LTE synthetic spectra (see Table 3)
is consistent with the temperature derived from the population
diagram within 1σ. The partition function of both the � = 0 and
� t = 1 spectroscopic entries includes only the rotational part. The
column density derived in Table 3 was corrected to account for
the vibrational part of the partition function. This correction was
computed in the harmonic approximation using the vibrational
energies of methylamine provided by Shimanouchi (1972) and
Gulaczyk & Kr˛eglewski (2020).


**6. Discussion**


It is evident that we came up against problems in current analysis that prevented us from achieving a fit within the experimental
error for the available dataset. Indeed, as seen from Table 2, even
for the torsional ground state, the weighted rms deviation for the


A65, page 10 of 17



microwave data is 2.38. The fact that we get greater rms deviation for the ground state in comparison with the previous fit
with the tunneling approach is not surprising. This is because
in the present study, we worked with a semi-global approach,
which fits the data belonging to a number of torsional states with
one set of parameters, and therefore the problems with fitting
excited torsional states may also diminish the quality of fitting
for the ground state. On the one hand, we are not able to rule
out a situation where our current fit corresponds to some local
minimum in vicinity of the global minimum in the functional
space of Hamiltonian parameters. Indeed, here we deal with the
two large-amplitude vibrational motions, which produce a rather
complicated landscape in the Hamiltonian parameter space. The
fact that a number of low-order parameters (such as _V_ 6, AXG,
DAB) have changed sign in comparison with our first methylamine study using the hybrid approach (Kleiner & Hougen
2020) shows that, at least with respect to our previous study, we
changed our position in the Hamiltonian parameter space quite
significantly and therefore we could still be out of a global minimum with our fit. Further extension of the analysis to the second
torsionally excited state may provide necessary information for
improving the situation with the global versus local minimum
by putting additional constraints on the Hamiltonian parameter
set. On the other hand, this problem might be circumvented simply by finding an optimal set of high-order parameters in our
Hamiltonian model that allow us to take into account all peculiarities of the energy level structure of the excited torsional states.
Here, the fact that poorly fitted lines belong to high _J_ and/or
high _K_ transitions – as mentioned above – may be considered
as an argument in favor of this explanation. Although our search
for the high-order Hamiltonian terms that could help to improve
the situation was quite extensive, it was not exhaustive, because
this search is very time consuming in view of the complexity
of the Hamiltonian parameter space in the case of two coupled,
large-amplitude motions.
A further possible explanation for the remaining problems
with fitting the available dataset is the strong influence of
intervibrational interactions arising from low-lying nontorsion
vibrations in the molecule. In methylamine, the third excited
torsional state is already close in energy to the NH 2 wagging
mode (see e.g., Fig. 2 of Gulaczyk et al. 2017) and strong Fermi
and Coriolis-type resonances have been reported for this state
(Gulaczyk et al. 2010). Therefore, it is quite probable that these
perturbations propagate down through numerous intertorsional
interactions and affect the energy level structure of the lower
torsional states. Our current model is not capable of explicitly
taking these intervibrational interactions into account since the
tunneling part of the hybrid approach represents only a separate
wagging state (in our current case, this is the ground wagging
state). Therefore, perturbations arising from this intervibrational
interaction may only be taken into account indirectly by our
current theoretical approach through some additional high-order
wagging-torsion-rotation Hamiltonian terms with no guarantee
that all the perturbations are accommodated in this way. It may
be that it will be impossible to get a fit within experimental
error for the current dataset without building a new theoretical approach allowing us to explicitly take into account the
intervibrational interactions arising from nontorsion vibrations.
On the observational side, in Sect. 5.2 we claim the detection of methylamine in its first torsionally excited state on the
basis of five relatively uncontaminated lines. While this would
be insufficient for the secure identification of a new molecule
in the ISM, the situation here is different. We already presented
a secure detection of methylamine in its torsional ground state

Gyawali, P., et al.: A&A, 677, A65 (2023)



toward Sgr B2(N1S), from which we derived LTE parameters
(Kisiel et al. 2022). The synthetic spectrum of methylamine in
its � t =1 state computed with the same set of LTE parameters
was found here to be consistent with the observed spectrum
of Sgr B2(N1S). Five transitions are even sufficiently free of
contamination, which means that this match is unlikely due to
chance. Other COMs in Sgr B2(N) were also detected in � = 0
and �>0 states with intensities consistent with a single set of LTE
parameters per molecule (see, e.g., the case of aminoacetonitrile
in Melosso et al. 2020). Therefore, we believe our claim of a
detection of methylamine in its � t = 1 state to be robust given the
combination of the fact that the synthetic spectra computed with
the same set of LTE parameters match lines in both the ground
and first torsionally excited states of methylamine and the fact
that five � t = 1 lines are relatively uncontaminated.


**7. Conclusions**


We carried out a new analysis of the rotational spectrum for the
first excited torsional state of CH 3 NH 2 up to 1.52 THz. Improving upon the results of the tunneling approach used previously
for the ground state analysis and having shown limitations for
analyzing the microwave and millimeter-wave data of the first
excited state � _t_ = 1, we were able to generate global fits for � _t_ = 0,
1, and 2 using our new hybrid Hamiltonian model. In addition, a
number of far-infrared transitions are fitted alongside microwave
data, achieving a weighted standard deviation of 1.53.
We report the first interstellar detection of methylamine in
its first torsionally excited state. The detection was obtained with
ALMA toward the offset position Sgr B2(N1S) of the hot molecular core Sgr B(N1). Five lines were unambiguously assigned to
rotational transitions of this state and their measured intensities
are consistent with the emission of methylamine in the torsional
ground state at a temperature of about 230 K with a column
density of 1.4 × 10 [18] cm [−][2] .
The identification of a handful of rotational lines from the
first torsionally excited state of methylamine contributes to our
efforts to reduce the number of unidentified lines in the ReMoCA
survey. The identification of new molecules in such a survey –
with its high spectral line density— requires us to account for
the contribution of all known interstellar species in order to avoid
erroneous assignments. Therefore, expanding the spectroscopic
predictions of known interstellar molecules to account for rotational transitions in their torsionally and vibrationally excited
states is of prime importance for the analysis of astronomical
spectral line surveys and should be continued.


_Acknowledgements._ Part of this work has been funded by French ANR agency
under contract No. ANR-11-LABX-0005-01 CaPPA (Chemical and Physical
Properties of the Atmosphere) and also supported by the Programme National
“Physique et Chimie du Milieu Interstellaire” (PCMI) of CNRS/INSU with
INC/INP co-funded by CEA and CNES. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00074.S. ALMA is a partnership of
ESO (representing its member states), NSF (USA), and NINS (Japan), together
with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea),
in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The interferometric data are available
in the ALMA archive at `[https://almascience.eso.org/aq/](https://almascience.eso.org/aq/)` . Part of this
work has been carried out within the Collaborative Research Centre 956, subproject B3, funded by the Deutsche Forschungsgemeinschaft (DFG) – project
ID 184018867.


**References**


[Aponte, J. C., Elsila, J. E., Glavin, D. P., et al. 2017, ACS Earth Space Chem., 1,](http://linker.aanda.org/10.1051/0004-6361/202346518/1)
[3](http://linker.aanda.org/10.1051/0004-6361/202346518/1)

Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013,

[A&A, 559, A47](http://linker.aanda.org/10.1051/0004-6361/202346518/2)



[Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, A&A, 587,](http://linker.aanda.org/10.1051/0004-6361/202346518/3)
[A91](http://linker.aanda.org/10.1051/0004-6361/202346518/3)

[Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10](http://linker.aanda.org/10.1051/0004-6361/202346518/4)
Bøgelund, E. G., McGuire, B. A., Hogerheijde, M. R., van Dishoeck, E. F., &
[Ligterink, N. F. 2019, A&A, 624, A82](http://linker.aanda.org/10.1051/0004-6361/202346518/5)
[Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27](http://linker.aanda.org/10.1051/0004-6361/202346518/6)
Busch, L. A., Belloche, A., Garrod, R. T., Müller, H. S. P., & Menten, K. M.
[2022, A&A, 665, A96](http://linker.aanda.org/10.1051/0004-6361/202346518/7)
[Fourikis, N., Takagi, K., & Morimoto, M. 1974, ApJ, 191, L139](http://linker.aanda.org/10.1051/0004-6361/202346518/8)
[Garrod, R. T., Jin, M., Matis, K. A., et al. 2022, ApJS, 259, 1](http://linker.aanda.org/10.1051/0004-6361/202346518/9)
Gordy, W., & Cook, R. L. 1984, Microwave Molecular [Spectra,](http://linker.aanda.org/10.1051/0004-6361/202346518/10) Techniques of
[Chemistry, XVIII (New York: Wiley)](http://linker.aanda.org/10.1051/0004-6361/202346518/10)
[Gulaczyk, I., & Kr˛eglewski, M. 2020, JQSRT, 252, 107097](http://linker.aanda.org/10.1051/0004-6361/202346518/11)
[Gulaczyk, I., Łodyga, W., Kr˛eglewski, M., & Horneman, V.-M. 2010, Mol. Phys.,](http://linker.aanda.org/10.1051/0004-6361/202346518/12)
[108, 2389](http://linker.aanda.org/10.1051/0004-6361/202346518/12)
Gulaczyk, I., Kr˛eglewski, M., & Horneman, V. 2017, J. Mol. [Spectrosc.,](http://linker.aanda.org/10.1051/0004-6361/202346518/13) 342,
[25](http://linker.aanda.org/10.1051/0004-6361/202346518/13)
[Gulaczyk, I., Kr˛eglewski, M., & Horneman, V.-M. 2018, JQSRT, 217, 321](http://linker.aanda.org/10.1051/0004-6361/202346518/14)
[Halfen, D. T., Ilyushin, V. V., & Ziurys, L. M. 2013, ApJ, 767, 66](http://linker.aanda.org/10.1051/0004-6361/202346518/15)
[Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427](http://linker.aanda.org/10.1051/0004-6361/202346518/16)
Holtom, P. D., Bennett, C. J., Osamura, Y., Mason, N. J., & Kaiser, R. I. 2005,

[ApJ, 626, 940](http://linker.aanda.org/10.1051/0004-6361/202346518/17)
[Hougen, J. T., Kleiner, I., & Godefroid, M. 1994, J. Mol. Spectrosc., 163](http://linker.aanda.org/10.1051/0004-6361/202346518/18)
[Ilyushin, V. V., & Lovas, F. J. 2007, J. Phys. Chem. Ref. Data, 36, 1141](http://linker.aanda.org/10.1051/0004-6361/202346518/19)
Ilyushin, V., Alekseev, E., Dyubko, S., Motiyenko, R., & Hougen, J. T. 2005,

[J. Mol. Spectrosc., 229, 170](http://linker.aanda.org/10.1051/0004-6361/202346518/20)
[Jørgensen, J. K., Belloche, A., & Garrod, R. T. 2020, ARA&A, 58, 727](http://linker.aanda.org/10.1051/0004-6361/202346518/21)
[Joshi, P. R., & Lee, Y.-P. 2022, Commun. Chem., 5, 62](http://linker.aanda.org/10.1051/0004-6361/202346518/22)
[Kaifu, N., Morimoto, M., Nagane, K., et al. 1974, ApJ, 191, L135](http://linker.aanda.org/10.1051/0004-6361/202346518/23)
[Kisiel, Z., Kolesniková, L., Belloche, A., et al. 2022, A&A, 657, A99](http://linker.aanda.org/10.1051/0004-6361/202346518/24)
[Kleiner, I. 2010, J. Mol. Spectrosc., 260, 1](http://linker.aanda.org/10.1051/0004-6361/202346518/25)
[Kleiner, I., & Hougen, J. T. 2015, J. Phys. Chem. A, 119, 10664](http://linker.aanda.org/10.1051/0004-6361/202346518/26)
[Kleiner, I., & Hougen, J. T. 2020, J. Mol. Spectrosc., 368, 111255](http://linker.aanda.org/10.1051/0004-6361/202346518/27)
Kleiner, I., Hougen, J. T., Suenram, R. D., Lovas, F. J., & Godefroid, M. 1992,

[J. Mol. Spectrosc., 153, 578](http://linker.aanda.org/10.1051/0004-6361/202346518/28)
[Kr˛eglewski, M., & Wlodarczak, G. 1992, J. Mol. Spectrosc., 156, 393](http://linker.aanda.org/10.1051/0004-6361/202346518/29)
[Kr˛eglewski, M., Stahl, W., Grabow, J.-U., & Wlodarczak, G. 1992, Chem. Phys.](http://linker.aanda.org/10.1051/0004-6361/202346518/30)
[Lett., 196, 155](http://linker.aanda.org/10.1051/0004-6361/202346518/30)
[Lide, D. R., Jr. 1957, J. Chem. Phys., 27, 343](http://linker.aanda.org/10.1051/0004-6361/202346518/31)
[Ligterink, N. F. W., Tenenbaum, E. D., & van Dishoeck, E. F. 2015, A&A, 576,](http://linker.aanda.org/10.1051/0004-6361/202346518/32)
[A35](http://linker.aanda.org/10.1051/0004-6361/202346518/32)
[Ligterink, N. F. W., Calcutt, H., Coutens, A., et al. 2018, A&A, 619, A28](http://linker.aanda.org/10.1051/0004-6361/202346518/33)
[Loomis, F., & Wood, R. 1928, Phys. Rev., 32, 223](http://linker.aanda.org/10.1051/0004-6361/202346518/34)
Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, [A&A,](http://linker.aanda.org/10.1051/0004-6361/202346518/35) 526,
[A47](http://linker.aanda.org/10.1051/0004-6361/202346518/35)
Melosso, M., Belloche, A., Martin-Drumel, M. A., et al. 2020, ApJ, 641,
[A160](http://linker.aanda.org/10.1051/0004-6361/202346518/36)
Motiyenko, R. A., Ilyushin, V. V., Drouin, B. J., Yu, S., & Margulès, L. 2014,

[A&A, 563, A137](http://linker.aanda.org/10.1051/0004-6361/202346518/37)
[Motiyenko, R. A., Margulès, L., Ilyushin, V. V., et al. 2016, A&A, 587, A152](http://linker.aanda.org/10.1051/0004-6361/202346518/38)
Motiyenko, R. A., Armieieva, I., Margulès, L., Alekseev, E., & Guillemin, J.-C.
[2019, A&A, 623, A162](http://linker.aanda.org/10.1051/0004-6361/202346518/39)
[Motiyenko, R. A., Belloche, A., Garrod, R. T., et al. 2020, A&A, 642, A29](http://linker.aanda.org/10.1051/0004-6361/202346518/40)
[Muller, S., Beelen, A., Guélin, M., et al. 2011, A&A, 535, A103](http://linker.aanda.org/10.1051/0004-6361/202346518/41)
[Ohashi, N., & Hougen, J. T. 1987, J. Mol. Spectrosc., 121, 474](http://linker.aanda.org/10.1051/0004-6361/202346518/42)
Ohashi, N., Takagi, K., Hougen, J. T., Olson, W. B., & Lafferty, W. J. 1987,

[J. Mol. Spectrosc., 126, 443](http://linker.aanda.org/10.1051/0004-6361/202346518/43)
Ohashi, N., Takagi, K., Hougen, J. T., Olson, W. B., & Lafferty, W. J. 1988,

[J. Mol. Spectrosc., 132, 242](http://linker.aanda.org/10.1051/0004-6361/202346518/44)
[Ohashi, N., Tsunekawa, S., Takagi, K., & Hougen, J. T. 1989, J. Mol. Spectrosc.,](http://linker.aanda.org/10.1051/0004-6361/202346518/45)
[137, 33](http://linker.aanda.org/10.1051/0004-6361/202346518/45)
[Ohishi, M., Suzuki, T., Hirota, T., Saito, M., & Kaifu, N. 2019, PASJ, 71, 86](http://linker.aanda.org/10.1051/0004-6361/202346518/46)
[Pagani, L., Favre, C., Goldsmith, P. F., et al. 2017, A&A, 604, A32](http://linker.aanda.org/10.1051/0004-6361/202346518/47)
[Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883](http://linker.aanda.org/10.1051/0004-6361/202346518/48)
[Pizzarello, S., & Holmes, W. 2009, Geochim. Cosmochim. Acta, 73, 2150](http://linker.aanda.org/10.1051/0004-6361/202346518/49)
[Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131](http://linker.aanda.org/10.1051/0004-6361/202346518/50)
[Rodríguez-Almeida, L. F., Jiménez-Serra, I., Rivilla, V. M., et al. 2021, ApJ, 912,](http://linker.aanda.org/10.1051/0004-6361/202346518/51)
[L11](http://linker.aanda.org/10.1051/0004-6361/202346518/51)
Schimanouchi, T. 1972, Tables of Molecular [Vibrational](http://linker.aanda.org/10.1051/0004-6361/202346518/52) Frequencies, Vol. I:
consolidated (Washington, DC: National Bureau of Standards)
[Suenram, R. D., Golubiatnikov, G. Y., Leonov, I., et al. 2001, J. Mol. Spectrosc.,](http://linker.aanda.org/10.1051/0004-6361/202346518/53)
[208, 188](http://linker.aanda.org/10.1051/0004-6361/202346518/53)
[Takagi, K., & Kojima, T. 1973, ApJ, 181, L91](http://linker.aanda.org/10.1051/0004-6361/202346518/54)
Townes, C. H., & Schawlow, A. L. 1955, Microwave Spectroscopy (New York,
NY: McGrawHill)
Zakharenko, O., Motiyenko, R. A., Margulès, L., & Huet, T. R. 2015, J. [Mol.](http://linker.aanda.org/10.1051/0004-6361/202346518/56)
[Spectrosc., 317, 41](http://linker.aanda.org/10.1051/0004-6361/202346518/56)
[Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, MNRAS, 478, 2962](http://linker.aanda.org/10.1051/0004-6361/202346518/57)


A65, page 11 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Appendix A:** **Molecular parameters of methylamine**


Table A.1: Molecular parameters _[a]_ (in cm [−][1] ) _[b]_ determined from the dataset summarized in Table 2.


ntrw _[c]_ Parameter × Operator _[d]_ Value(unc) from previous fit _[e]_ Value(unc) from present fit _[e]_

2200 _P_ ~~[2]~~ α [×] _[ F]_ [15.1412489] _[f]_ [15.08857388] _[f]_

12 [(1][ −] [γ][ cos 3][α][)][ ×] _[ V]_ [3] 695.320556(53) 682.911087(19)
2110 _P_ α _J_ _z_ × RHORHO _[a]_ 0.64935371(10) _[a]_ 0.649355515(26) _[a]_
γ _P_ α _J_ _x_ × AXG 0.15595(28) -0.158311(17)
2020 _J_ _x_ [2] [×][ B] 0.7256934(20) 0.72874862(31)
_J_ y [2] [×][ C] 0.75613394(18) 0.756180141(42)
_J_ _z_ [2] [×][ A] 3.44098285(66) 3.40280(23)
γ{ _J_ _x_, _J_ _z_ }× DAB -0. 07373(13) 0.1704383(82)
2002 1 × WAG2 -0.64470(98) -0.31490(10)
3012 _P_ γ _J_ y × WCPG -0.000844(13) [0.001052604] _[f]_

4400 _P_ [4] α [×][ AK4] 0.00005168(11) -0.001353681(63)
21 [(1][ −] [cos 6][α][)][ ×] _[V]_ [6] -27.594750(75) 0.316699(41)
4310 _P_ [3] α _[J]_ _[z]_ [×][ AK3] 0.00075529(31) 0.00439259(13)
γ _P_ [3] α _[J]_ _[x]_ [×][ AXG3] -0.0000137(20) 0.00040774(39)
γ{ _P_ α, cos 3α} _J_ _z_ × AK6 – 0.02926(18)
4220 (γ − cos 3α){ _J_ _x_, _J_ _z_ } × ODAB 0.009123(14) -0.1053088(21)
(1 − γ cos 3α) _J_ [2] × FV -0.00380679(55) -0.00451830(10)
(1 − γ cos 3α) _J_ _z_ [2] [×][ AK5] 0.0206331(18) 0.05982(23)
(1 − γ cos 3α)( _J_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ C2] -0.00027295(28) -0.00107326(18)
sin 3α{ _J_ y, _J_ _z_ } × DAC -0.00366(11) -0.003623(16)
γ sin 3α{ _J_ _x_, _J_ y } × DBC -0.001638(11) -0.0008978(42)
_P_ [2] α _[J]_ [2] [×][ GV] 0. 000060955(15) -0.0000636354(17)
_P_ [2] α _[J]_ _z_ [2] [×][ AK2] -0. 00243340(42) -0.00592494(10)
2 _P_ [2] α [(] _[J]_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ C1] 0.00004680(22) 0.000030801(80)
γ _P_ [2] α [{] _[J]_ _[x]_ [,] _[ J]_ _[z]_ [}][ ×][ DELTA] -0.0001072(20) -0.00036012(25)
4202 _P_ [2] α [×][ WF] 0.006876(39) 0.0062553(23)
4130 _P_ α _J_ [2] _J_ _z_ × ALV 0.000078897(23) [0.0000813080] _[f]_

_P_ α _J_ _z_ [3] [×][ AK1] 0.00218065 (27) 0.003655932(35)
_P_ α { _J_ _z_, ( _J_ _x_ [2] [−] _[J]_ y [2] [)}][ ×][ C4] -0.00006847(24) -0.000052393(85)
γ _P_ α { _J_ _x_, _J_ _z_ [2] [}][ ×][ AXGK] 0.0000976(17) 0.00015818(17)
4112 _P_ α _J_ _z_ × WRHO -0. 011533(34) -0.0106006(33)
4040       - _J_ [4] × DJ 1.325232(21) × 10 [−][6] 1.322019(15) × 10 [−][6]

               - _J_ [2] _J_ _z_ [2] [×][ DJK] 0.31574(12) × 10 [−][3] 0.0303198(21) × 10 [−][3]

               - _J_ _z_ [4] [×][ DK] 0.628 648(76) × 10 [−][3] [0.862705 × 10 [−][3] ] _[f]_

-2 _J_ [2] ( _J_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ ODELN] -0.060514(10) × 10 [−][6] -0.0623674(68) × 10 [−][6]

-{ _J_ _z_ [2] [,][ (] _[J]_ _x_ [2] [−] _[J]_ y [2] [)}][ ×][ ODELK] -0.023204(36) × 10 [−][3] -0.022551(15) × 10 [−][3]

γ{ _J_ _z_, ( _J_ + [3] [+] _[ J]_ − [3] [)}][ ×][ GZJ3] – 0.00030773(61) × 10 [−][3]

4022 _J_ [2] × WAG2J 0.000012493(51) 0.000001786(26)
( _J_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ WAGBC] [g] -0.000019827(54) -0.0000217525(69)
_J_ _z_ [2] [×][ WAG2K] 0.0049756(56) 0.0044477(13)
5212 _P_ γ sin 3α _J_ _z_ × WS3APG -0.06189(28) 0.0
5032 _P_ γ { _J_ y, _J_ _z_ [2] [}][ ×][ WCPGK] 0.002908(71) × 10 [−][3] 0.0
5302 _P_ γ { _P_ α, sin 3α} × WPGS3 0. 04353(26) -0.0032152(41)
6420 (1 − cos 6α) _J_ [2] × ANV -0.00002144(44) -0.000515585(45)
_P_ [4] α _[J]_ _z_ [2] [×][ BK1] -0.0011407(55) × 10 [−][3] 0.0045914(25) × 10 [−][3]

(1 − cos 6α)( _J_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ C11] – -0.00037596(18)
_P_ [4] α _[J]_ [2] [ ×][ AMV] – 0.034865(94) × 10 [−][6]

6402 _P_ [4] α [×][ WAK4] 0.0000426(15) 0.000016369(92)
cos 6α × WCOS6 – 0.30313(42)
6330 _P_ [3] α _[J]_ [2] _[J]_ _[z]_ [×][ AK3J] -0.02939(42) × 10 [−][6] -0.09069(21) × 10 [−][6]


A65, page 12 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


Table A.1: continued.


ntrw _[c]_ Parameter × Operator _[d]_ Value(unc) from previous fit _[e]_ Value(unc) from present fit _[e]_

_P_ ~~[3]~~ α _[J]_ _z_ ~~[3]~~ [×][ AK3K] 0.002682(15) × 10 [−] ~~[3]~~ [-0.000006508] _[f]_

6312 _P_ [3] α _[J]_ _[z]_ [×][ WAK3] -0.0000987(30) -0.00001807(25)
6240 (1 − γ cos 3α) _J_ [4] × OFV 0.01504(15) × 10 [−][6] 0.012634(19) × 10 [−][6]

(1 − γ cos 3α) _J_ [2] _J_ _z_ [2] [×][ AK5J] 0.128(13)× 10 [−][6] -1.0766(13) × 10 [−][6]

(1 − γ cos 3α) _J_ [2] ( _J_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ C2J] 0.00569(12)× 10 [−][6] 0.007165(36)× 10 [−][6]

(1 − γ cos 3α){ _J_ _z_ [2] [,][ (] _[J]_ _x_ [2] [−] _[J]_ y [2] [)}][ ×][ C2K] 0.863(17)× 10 [−][6] 0.0
_P_ [2] α _[J]_ [4] [×][ GVJ] 0.0007172(91) × 10 [−][6] 0.0003411(11) × 10 [−][6]

_P_ [2] α _[J]_ [2] _[J]_ _z_ [2] [×][ AK2J] 0.08167(86) × 10 [−][6] 0.09305(24) × 10 [−][6]

_P_ [2] α _[J]_ _z_ [4] [×][ AK2K] -0.002274(17) × 10 [−][3] 0.00502932(90) × 10 [−][3]

sin 3α{ _J_ _z_, ( _J_ + [3] [−] _[J]_ − [3] [)}][ ×][ S3Z3] – 0.04912(24) × 10 [−][6]

6510 _P_ [5] α _[J]_ _[z]_ [×][ AK3B] – -0.0016609(31) × 10 [−][3]

6600 _P_ [6] α [×][ AK4B] – 0.0002405(12) × 10 [−][3]

12 [(1][ −] [γ][ cos 9][α][)][ ×] _[V]_ [9] [32.9134] _[f]_ [-0.087806] _[f]_

6222 cos 3α{ _J_ _x_, _J_ _z_ } × WODAB -0.1309(63) × 10 [−][3] 0.0
sin 3α{ _J_ y, _J_ _z_ } × WS3AC -0.00380(23) × 10 [−][3] 0.01303(11) × 10 [−][3]

_P_ [2] α _[J]_ _z_ [2] [×][ WAK2] 0.0000791(19) -0.00002106(26)
_P_ [2] α _[J]_ [2] [×][ WGV] – -0.0001860(11) × 10 [−][3]

2 _P_ [2] α [(] _[J]_ _x_ [2] [−] _[J]_ y [2] [)][ ×][ WC1] – -0.00011844(19) × 10 [−][3]

6150 _P_ α _J_ [4] _J_ _z_ × OLV -0.001148(12) × 10 [−][6] -0.0003594(17) × 10 [−][6]

_P_ α _J_ [2] _J_ _z_ [3] [×][ AK1J] -0.07904(66) × 10 [−][6] -0.04550(13)× 10 [−][6]

_P_ α _J_ _z_ [5] [×][ AK1K] 0.0008177(80) × 10 [−][3] -0.00201816(35) × 10 [−][3]

6132 _P_ α _J_ [2] _J_ _z_ × WALV 0.0001479(19) × 10 [−][3] 0.0003005(12)× 10 [−][3]

_P_ α _J_ _z_ [3] [×][ WAK1] -0.00002176(42) 0.00003544(12)
_P_ α { _J_ _z_, ( _J_ _x_ [2] [−] _[J]_ y [2] [)}][ ×][ WC4] – 0.10614(20)× 10 [−][6]

6042 _J_ [4] × WAG2JJ 0.000641(18) × 10 [−][6] 0.0003878(16) × 10 [−][6]

_J_ [2] _J_ _z_ [2] [×][ WAG2JK] -0.1177(14) × 10 [−][6] -0.14392(43) × 10 [−][6]

_J_ _z_ [4] [×][ WAG2KK] – -0.000012280(23)
( _J_ + [4] [+] _[ J]_ − [4] [)][ ×][ WAJ4] -0.000246(12) × 10 [−][6] 0.0
6060 _J_ [6] × HJ -0.000600(5) × 10 [−][9] 0.0
_J_ [4] _J_ _z_ [2] [×][ HJK] 0.0004579(61)× 10 [−][6] 0.00011487(80) × 10 [−][6]

_J_ [2] _J_ _z_ [4] [×][ HKJ] 0.02533(19) × 10 [−][6] 0.009285(28) × 10 [−][6]

_J_ _z_ [6] [×][ HK] -0.1032(15)× 10 [−][6] [0.3296476 × 10 [−][6] ] _[f]_

7322 _P_ γ { _P_ α, sin 3α} _J_ _z_ [2] [×][ WPGS3K] 0.04814(17) × 10 [−][4] [0.000005145] _[f]_

8440 (1 − cos 6α) _J_ [2] _J_ _z_ [2] [×][ BK2J] -0.4030(81) × 10 [−][6] 0.0
(1 − cos 6α) _J_ _z_ [4] [×][ BK2K] – 0.0005581(29) × 10 [−][3]

8422 _P_ [4] α _[J]_ [2] [ ×][ WMV] 0.0000183(35) × 10 [−][6] -0.005912(42) × 10 [−][6]

_P_ [4] α _[J]_ _z_ [2] [×][ WBK1] – 0.003706(10) × 10 [−][6]

(1 − cos 6α) _J_ _z_ [2] [×][ WBK2] – -0.00047000(96)
(1 − cos 6α) _J_ [2] × WNV – -0.000021572(56)
8152 _P_ α _J_ [2] _J_ _z_ [3] [×][ WAK1J] -0.0000302(21) × 10 [−][6] 0.002588(14) × 10 [−][6]

8242 _P_ [2] α _[J]_ [2] _[J]_ _z_ [2] [×][ WAK2J] – -0.010096(56) × 10 [−][6]

_P_ [2] α _[J]_ _z_ [4] [×][ WAK2K] – -0.0034899(99) × 10 [−][6]

8332 _P_ [3] α _[J]_ _[z]_ _[J]_ [2] [×][ WAK3J] – 0.013237(83)× 10 [−][6]

8080 _J_ [2] _J_ _z_ [6] [×][ ALJKK] -0.015(1) × 10 [−][12] 0.0
_J_ [4] { _J_ _z_ [2] [,][ (] _[J]_ _x_ [2] [−] _[J]_ y [2] [)}][ ×][ OHJK] -0.06510(68) × 10 [−][9] 0.0
10802 cos 12α × WCOS12 – -0.9862(65)


**Notes.** [(] _[a]_ [)] The product of the parameter and operator from a given row yields the term used in the torsion-rotation-tunneling Hamiltonian, except
for _F_, ρ, and _A_, which occur in the Hamiltonian in the form _F_ ( _P_ α − ρ _P_ _a_ ) [2] + _AP_ [2] _a_ [,] [where] [γ] [in] [these] [operators] [is] [shorthand] [for] [γ/][ ⟨] _[R]_ [|][γ][|] _[R]_ [⟩] [and] [so]
its matrix elements give only a − [+] sign to the final matrix element of the full operator expression (see Kleiner & Hougen (2015)). Operators of
species _B_ 1 in _G_ 12 (such as cos3α) are not allowed in the Hamiltonian. Such operators can be made _A_ 1 in _G_ 12 by multiplying them by the wagging
coordinate γ (which is also _B_ 1 in _G_ 12 ). [(] _[b]_ [)] All parameters are given in cm [−][1] except for RHORHO, which is unitless. The parameter value given in
square parentheses (such as _F_ and _V_ 9 ) was fixed in our final fit at a value taken from an earlier fit where it was floated. [(] _[c]_ [)] The symbols t and r give
the order of the torsional part and the rotational part of the operator, as defined in (Kleiner & Hougen 2015); w gives the wagging order, n = t + r +
w gives the total order of the operator. [(] _[d]_ [)] The column contains the operator used in the hybrid Hamiltonian multiplied by the parameter adjusted in
the least-square fit. [(] _[e]_ [)] This column contains the value of the parameter determined in the fit, with one standard uncertainty in units of the last digits
given in parentheses. [(] _[f]_ [)] Value fixed in the fit. [(][g][)] This parameter was erroneously named FWAGBC in the previous paper (Kleiner & Hougen 2020).


A65, page 13 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Appendix B:** **Assigned microwave and FIR transitions of methylamine**


Table B.1: A part of the table available in CDS, with measured pure rotational transitions of methylamine.


� [′] _t_ _J_ [′] _K_ _a_ [′] _K_ _c_ [′] Γ [′] � [′′] _t_ _J_ [′′] _K_ _a_ [′′] _K_ _c_ [′′] Γ [′′] Obs. freq. Uncertainty obs.-calc. Incl. Ref.
(MHz) (MHz) (MHz)
1 21 5 17 B2 1 20 6 14 B1 163610.558 0.060 1.425 0 1

0 2 1 2 B1 0 1 0 1 B2 169447.508 0.100 0.010 1 2

1 10 2 8 E2 1 9 3 7 E2 169533.747 0.100 -0.222 1 1

0 2 -1 1 E2 0 1 0 1 E2 171035.274 0.100 -0.044 1 2

1 10 1 9 E1 1 9 2 8 E1 171816.649 0.060 0.166 1 1

1 23 4 20 E1 1 22 5 17 E1 172601.330 0.060 0.101 1 1

0 2 -1 2 E1 0 1 0 1 E1 173267.798 0.100 -0.068 1 2

1 4 0 5 B2 1 3 1 2 B1 174950.669 0.100 -0.483 0 4

1 4 1 4 A1 1 3 1 3 A2 175338.833 0.100 -0.026 1 4

1 4 1 4 B1 1 3 1 3 B2 175340.894 0.100 0.023 1 4

2 4 1 3 E1 2 3 1 2 E1 176314.060 0.100 0.233 1 1

2 4 0 4 E1 2 3 0 3 E1 176394.935 0.100 0.153 1 1


**References.** (1) this study; (2) Motiyenko et al. (2014); (3) Ohashi et al. (1989); (4) Kr˛eglewski & Wlodarczak (1992); (5) Motiyenko
(priv. comm.)


Table B.2: A part of the table available in CDS, with measured rovibrational transitions of methylamine.


� [′] _t_ _J_ [′] _K_ _a_ [′] _K_ _c_ [′] Γ [′] � [′′] _t_ _J_ [′′] _K_ _a_ [′′] _K_ _c_ [′′] Γ [′′] Obs. freq. Uncertainty obs.-calc. Incl. _K_ _a_ = 2
(cm [−][1] ) (cm [−][1] ) (cm [−][1] ) flag
2 40 -9 32 E1 1 40 -10 30 E1 165.6057 0.0008 -0.0123 0

2 21 -3 18 E2 1 21 -4 18 E2 165.6144 0.0008 0.0009 1

2 13 2 11 A2 1 13 5 8 A1 165.6243 0.0008 -0.0001 1 L

2 13 2 12 A1 1 13 5 9 A2 165.6243 0.0008 -0.0000 1 L

1 23 -11 12 E2 0 24 -12 13 E2 165.6243 0.0008 0.0013 0

1 16 14 0 B 0 17 15 0 B 165.6280 0.0008 -0.0006 1

2 16 2 15 B2 1 16 5 12 B1 165.6330 0.0008 0.0007 1

2 16 2 14 B1 1 16 5 11 B2 165.6330 0.0008 0.0004 1

1 18 -13 5 E2 0 19 -14 6 E2 165.6801 0.0008 -0.0002 1

2 12 2 10 A1 1 12 5 7 A2 165.6934 0.0008 -0.0000 1 L

2 12 2 11 A2 1 12 5 8 A1 165.6934 0.0008 -0.0000 1 L


A65, page 14 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


**Appendix C:** **ReMoCA detection of methylamine in its torsional ground state**


Figure C.1 shows the rotational transitions of methylamine in its torsional ground state that are covered by the ReMoCA survey and
contribute significantly to the signal detected toward Sgr B2(N1S). The spectroscopic entry used to produce the synthetic spectra of
methylamine accounts for the hyperfine structure, which was not the case for the synthetic spectra shown in Fig. A.5 of Kisiel et al.
(2022).


Fig. C.1: Same as Fig. 4 but for CH 3 NH 2, � = 0.


A65, page 15 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


Fig. C.1: continued.



A65, page 16 of 17

Gyawali, P., et al.: A&A, 677, A65 (2023)


Fig. C.1: continued.



A65, page 17 of 17


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[0]",
  "value": "To experimentally and theoretically study the terahertz and microwave rotational spectra of methylamine and search for its rotational transitions in the first torsionally excited state (v_t = 1) in the interstellar medium toward Sgr B2(N).",
  "failed_quote": "The aim of this work is to study the terahertz and microwave rotational spectra of methylamine experimentally and theoretically in order to provide a reliable basis for the detection of its rotational transitions in the first torsionally excited state,  _t_ = 1, in the ISM."
 },
 {
  "path": "data.lines_targeted[0].evidence[2]",
  "value": "CH3NH2",
  "failed_quote": "One comment should be made concerning the  _t_ = 1 line of methylamine at 86657 MHz."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Previously published infrared and microwave transition datasets for methylamine (v_t = 0, 1, 2)",
  "failed_quote": "we used a dataset for  _t_ = 0 and 1 that combines previously published data in the infrared (Ohashi et al. 1987, 1988; Gulaczyk et al. 2017) with data in the microwave spectral range (Motiyenko et al. 2014; Ohashi et al. 1989; Kr˛eglewski & Wlodarczak 1992; Ilyushin et al. 2005; Ilyushin & Lovas 2007)"
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Previously published infrared and microwave transition datasets for methylamine (v_t = 0, 1, 2)",
  "failed_quote": "In the present fit, we added 6155 transitions belonging to the hot band  _t_ = 2 ← 1 and 5253 transitions belonging to the overtone  _t_ = 2 ← 0 from (Gulaczyk et al. 2018; Gulaczyk & Kr˛eglewski 2020)."
 },
 {
  "path": "analysis_steps[0].method.evidence[2]",
  "value": "Record absorption spectra from 150 to 1520 GHz using the Lille fast-scan hybrid spectrometer, assign transitions using Loomis-Wood diagrams, and fit hyperfine components to derive hyperfine-free frequencies and quadrupole coupling constants",
  "failed_quote": "To obtain hyperfine-free rotational transition frequencies, each hyperfine component was fitted to Eq. (1). The linear least-squares Gauss-Newton algorithm was applied using a dedicated Python code."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "1456 hyperfine transitions (including 324 v_t = 1-1 components) fitted to yield 653 hyperfine-free frequencies",
  "failed_quote": "In the present study, we assigned 324 partially resolved hyperfine components of  _t_ = 1–1 rotational transitions. These were fitted together with 1132  _t_ = 0–0 components from this and previous studies (Ilyushin et al. 2005; Motiyenko et al. 2014) to yield 653 hyperfine-free rotational transition frequencies"
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Two-step diagonalization of the hybrid Hamiltonian matrix using BELGI-hybrid to globally fit microwave, mm/submm, and far-infrared transitions for v_t = 0, 1, 2 up to J = 40, and compute line strengths and hyperfine intensities",
  "failed_quote": "The BELGI-hybrid code globally fits a large microwave, millimeter, and submillimeter dataset for 2790  _t_ = 0–0, 2921  _t_ = 1–1, and 40  _t_ = 2 − 2 pure rotational transitions, as well as the far-infrared dataset involving 11643  _t_ = 1 ← 0, 6155  _t_ = 2 ← 1, and 5253  _t_ = 2 ← 0 transitions up to _J_ = 40."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "theta_s = 2.0'', T_rot = 230 K, N = 1.4e18 cm^-2, F_vib = 1.25, Delta_V = 5.0 km s^-1, V_off = 0.0 km s^-1 (with V_sys = 62 km s^-1)",
  "failed_quote": "Each species was modeled with a set of five parameters: size of the emitting region (θ s ), column density ( _N_ ), temperature ( _T_ rot ), line width (∆ _V_ ), and velocity offset ( _V_ off ) with respect to the assumed systemic velocity of the source, _V_ sys = 62 km s [−][1] ."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "theta_s = 2.0'', T_rot = 230 K, N = 1.4e18 cm^-2, F_vib = 1.25, Delta_V = 5.0 km s^-1, V_off = 0.0 km s^-1 (with V_sys = 62 km s^-1)",
  "failed_quote": "CH 3 NH 2,  = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1"
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "v = 0 and v_t = 1 transitions included",
  "failed_quote": "CH 3 NH 2  = 0,  t = 1 222 ( 8)"
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "Global fitting of the hybrid wagging-torsion-rotation Hamiltonian and calculation of line strengths and expectation values for methylamine",
  "failed_quote": "The BELGI-hybrid code globally fits a large microwave, millimeter, and submillimeter dataset for 2790  _t_ = 0–0, 2921  _t_ = 1–1, and 40  _t_ = 2 − 2 pure rotational transitions"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Number of detected lines of CH3NH2 v = 0 toward Sgr B2(N1S) = 10 dimensionless",
  "failed_quote": "CH 3 NH 2,  = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Total column density of CH3NH2 toward Sgr B2(N1S) (LTE model) = 1.4e18 cm^-2",
  "failed_quote": "CH 3 NH 2,  = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1"
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Rotational temperature of CH3NH2 toward Sgr B2(N1S) (LTE model) = 230 K",
  "failed_quote": "CH 3 NH 2,  = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Line width (FWHM) of CH3NH2 toward Sgr B2(N1S) = 5.0 km s^-1",
  "failed_quote": "CH 3 NH 2,  = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Vibrational partition function correction factor F_vib for CH3NH2 at 230 K = 1.25 dimensionless",
  "failed_quote": "CH 3 NH 2,  = 0 [⋆] d 10 2.0 230 1.4 (18) 1.25 5.0 0.0 1"
 },
 {
  "path": "results_numeric[13].evidence[1]",
  "value": "Rotational temperature of CH3NH2 from population diagram fit (v = 0 and v_t = 1) = 222 K",
  "failed_quote": "CH 3 NH 2  = 0,  t = 1 222 ( 8)"
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "First interstellar detection of methylamine (CH3NH2) in its first torsionally excited state (v_t = 1) toward Sgr B2(N1S).",
  "failed_quote": "We report the first interstellar detection of methylamine in the  _t_ = 1 state toward the offset position Sgr B2(N1S) in the hot molecular core Sgr B2(N1)."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "Accounting for nuclear quadrupole hyperfine structure broadens several methylamine lines and reduces their peak brightness temperatures compared to models without hyperfine structure, reducing the number of firmly detected v = 0 lines from 15 to 10.",
  "failed_quote": "With these criteria, we count 10 lines of methylamine in its torsional ground state as detected in Fig. C.1 while 15 were counted in the previous study that ignored the hyperfine structure of methylamine."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "The hybrid Hamiltonian approach overcomes the limitations of the separate-state tunneling formalism for the v_t = 1 state and provides accurate spectral predictions for astronomical searches, although the fit is not completely within experimental uncertainty.",
  "failed_quote": "For the first excited state  _t_ = 1–1, we obtained a rms of 218 kHz for 2921 lines."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "Methylamine in its first torsionally excited state is robustly detected for the first time in the ISM toward Sgr B2(N1S), with intensities fully consistent with the torsional ground state.",
  "failed_quote": "The LTE parameters derived previously from the rotational emission of methylamine in its torsional ground state toward Sgr B2(N1S) yield synthetic spectra of methylamine in the  _t_ = 1 state that are fully consistent with the ALMA spectra and allow us to identify five rotational lines of this state."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Given the strong v_t = 0 intensities and ~230 K rotational temperature toward Sgr B2(N1S) in the ReMoCA survey, the strongest v_t = 1 transitions were expected to be detectable above 3 sigma; the offset position Sgr B2(N1S) was chosen for its lower continuum opacity compared to the main hot core peak.",
  "failed_quote": "Given the intensities of the  t = 0 transitions of methylamine measured toward Sgr B2(N1S) with the ReMoCA survey and their rotational temperature of ∼230 K (Kisiel et al. 2022), we expected the strongest  t = 1 transitions of methylamine to be detectable above the 3σ level in this survey."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "The hybrid Hamiltonian approach was used because the high-barrier tunneling approach showed limitations for the v_t = 1 state; LTE modeling with Weeds is justified by the high gas densities (> 1e7 cm^-3) in Sgr B2(N) hot cores, and LSD hyperfine predictions were used because hyperfine splitting broadens lines at the 5 km s^-1 linewidth of Sgr B2(N1S).",
  "failed_quote": "The analysis yielded an accurate model of the rotational spectrum in the  _t_ = 0 state (Ilyushin et al. 2005; Motiyenko et al. 2014), but showed some limitations with respect to the  _t_ = 1 state. To overcome these limitations, we use a new hybrid model and the BELGI-hybrid code"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Including previously published ground-state v_t = 0 combination differences (GSCDs) and far-infrared pure rotational transitions in the global fit was rejected because GSCDs caused parameters to drift and FIR pure rotational lines had frequency discrepancies up to 30 MHz.",
  "failed_quote": "We decided to include neither the previously published ground state  _t_ = 0 combination differences (GSCDs) – as their large number tends to decrease the impact of the more accurate microwave transitions, thus causing the parameters to drift – nor the pure rotational transitions  _t_ = 0–0,  _t_ = 1–1 or  _t_ = 2–2, which were initially measured in the far-infrared range"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Replacing the Motiyenko et al. (2014) tunneling model predictions for v_t = 0-0 in the Lille Spectroscopic Database with the new hybrid model predictions was rejected because the tunneling model covers up to J <= 50 (versus J <= 40) and achieves a slightly better rms for v_t = 0-0.",
  "failed_quote": "Therefore, at present, we believe that it is better to use predictions based on the high-barrier tunneling Hamiltonian of Motiyenko et al. (2014) for  _t_ = 0–0 transitions and predictions based on the current hybrid approach for  _t_ = 1–1 transitions."
 },
 {
  "path": "reasoning.how_they_decided_enough.evidence[1]",
  "value": "In the spectroscopic fit, J was limited to <= 40 to keep matrix sizes and computation time reasonable; in the astronomical analysis, 5 uncontaminated v_t = 1 lines matching the pre-existing v = 0 LTE parameters were judged sufficient for a robust detection of an excited state of an already securely detected molecule.",
  "failed_quote": "Therefore, we believe our claim of a detection of methylamine in its  t = 1 state to be robust given the combination of the fact that the synthetic spectra computed with the same set of LTE parameters match lines in both the ground and first torsionally excited states of methylamine and the fact that five  t = 1 lines are relatively uncontaminated."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[1]",
  "value": "ALMA interferometric data are available in the ALMA archive; full transition tables B.1 and B.2 are available at CDS; calculated v_t = 1-1 and v_t = 0-0 spectroscopic catalogs are available at the Lille Spectroscopic Database (LSD).",
  "failed_quote": "The calculated  _t_ = 1–1 rotational spectrum of methylamine is available at the Lille Spectroscopic Database [4] (LSD) in two versions"
 }
]
```
