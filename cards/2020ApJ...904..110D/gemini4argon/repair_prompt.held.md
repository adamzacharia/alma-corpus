# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...904..110D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version March 26, 2022
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Rotational** **spectra** **of** **vibrationally** **excited** **AlO** **and** **TiO** **in** **oxygen** **rich** **stars**


T. [Danilovich](http://orcid.org/0000-0002-1283-6038), [1] C. A. [Gottlieb](http://orcid.org/0000-0003-2845-5317), [2] L. [Decin](http://orcid.org/0000-0002-5342-8612), [1] A. M. S. [Richards](http://orcid.org/0000-0002-3880-2450), [3] K. L. [K.](http://orcid.org/0000-0002-1903-9242) Lee, [2] T. [Kami´nski](http://orcid.org/0000-0001-8541-8024), [4]

N. A. [Patel](http://orcid.org/0000-0002-6021-9421), [2] K. H. [Young](http://orcid.org/0000-0002-3666-4920), [2] and K. M. [Menten](http://orcid.org/0000-0001-6459-0669) 5


1 _Institute_ _of_ _Astronomy,_ _KU_ _Leuven,_ _Celestijnenlaan_ _200D,_ _3001_ _Leuven,_ _Belgium_
2 _Harvard-Smithsonian_ _Center_ _for_ _Astrophysics,_ _60_ _Garden_ _Street,_ _Cambridge,_ _MA_ _02138,_ _USA_
3 _JBCA,_ _Department_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Manchester,_ _Manchester_ _M13_ _9PL,_ _UK_
4 _Nicolaus_ _Copernicus_ _Astronomical_ _Center,_ _Polish_ _Academy_ _of_ _Sciences,_ _Rabia´nska_ _8,_ _87-100_ _Toru´n,_ _Poland_
5 _Max-Planck_ _Institut_ _f¨ur_ _Radioastronomie,_ _Auf_ _dem_ _H¨ugel_ _69,_ _D-53121_ _Bonn,_ _Germany_


(Received 6 June 2020; Revised March 26, 2022; Accepted)


ABSTRACT


Rotational transitions in vibrationally excited AlO and TiO — two possible precursors of dust —
were observed in the 300 GHz range (1 mm wavelength) towards the oxygen rich AGB stars R Dor and
IK Tau with ALMA, and vibrationally excited AlO was observed towards the red supergiant VY CMa
with the SMA. The _J_ = 11 _→_ 10 transition of TiO in the _v_ = 1 and 2 levels, and the _N_ = 9 _→_ 8
transition in the _v_ = 2 level of AlO were identified towards R Dor; the _J_ = 11 _→_ 10 line of TiO was
identified in the _v_ = 1 level towards IK Tau; and two transitions in the _v_ = 1 and 2 levels of AlO
were identified towards VY CMa. The newly-derived high vibrational temperature of TiO and AlO in
R Dor of 1800 _±_ 200 K, and prior measurements of the angular extent confirm that the majority of the
emission is from a region within ≲2 _R_ _⋆_ of the central star. A full radiative transfer analysis of AlO in
R Dor yielded a fractional abundance of _∼_ 3% of the solar abundance of Al. From a similar analysis
of TiO a fractional abundance of _∼_ 78% of the solar abundance of Ti was found. The observations

provide indirect evidence that TiO is present in a rotating disk close to the star. Further observations
in the ground and excited vibrational levels are needed to determine whether AlO, TiO, and TiO 2 are
seeds of the Al 2 O 3 dust in R Dor, and perhaps in the gravitationally bound dust shells in other AGB
stars with low mass loss rates.


_Keywords:_ stars: AGB and post-AGB — circumstellar matter — submillimeter: stars — line: identification



1. INTRODUCTION


Most low and intermediate mass stars ( _∼_ 0 _._ 8–8 M _⊙_ )
pass through the asymptotic giant branch (AGB) phase
after leaving the main sequence and exhausting the
hydrogen and helium in their cores. High-mass stars
(≳ 8 M _⊙_ ), however, pass through the similarly cool
red super giant (RSG) phase while fusing helium. Both
AGB and RSG stars have high mass-loss rates and produce a significant amount of dust in their molecule rich
stellar winds. For a comprehensive review of AGB and
RSG stars, see H¨ofner & Olofsson (2018) and Levesque
(2017).


Corresponding author: Ta¨ıssa Danilovich

taissa.danilovich@kuleuven.be



The precise formation pathways of dust in AGB and
RSG stars are not yet known, but in the past few years
astronomers have begun observing rotational lines of a
few small metal bearing molecules which might be the
precursors of the dust. The high sensitivity and angular
resolution of interferometers such as the Atacama Large
Millimeter/submillimeter Array (ALMA) have allowed
astronomers to compare the abundance distributions of
small gaseous molecules with the infrared emission from
the dust, and to consider the possible connection between the gaseous molecules and the dust formation and
growth process within a few stellar radii ( _R_ _⋆_ ) of the central star (Kami´nski 2019).
Optical and near-infrared polarimetric images of the
dust do not directly reveal the composition and processes by which the dust is formed (Khouri et al. 2016;

2 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



Ohnaka et al. 2016), but parallel studies of the abundance distributions of the gas phase molecules in the
dust forming region might help unravel the physicochemical processes that occur in the phase change from
small molecules to gas phase clusters and ultimately tiny
dust grains. Karovicova et al. (2013) used infrared interferometric observations from VLTI/MIDI (the MIDinfrared Interferometric instrument on the VLT interferometer) to show that two oxygen rich Mira stars with
low mass loss rates (S Ori and R Cnc) are surrounded
by an amorphous Al 2 O 3 shell at _∼_ 2 stellar radii; while
an AGB star with a high mass loss rate (GX Mon) is
surrounded by an Al 2 O 3 dust shell at around 2 stellar
radii and a silicate layer around 4 stellar radii. This
led Karovicova et al. to hypothesise that stars with low
mass loss rates primarily form dust whose spectral properties match Al 2 O 3, and stars with higher mass loss rate
form dust with the spectral properties of warm silicates.
In oxygen rich AGB and RSG stars (the focus of the
work here), the most accessible metal oxides and hydroxides in the millimeter band are SiO, AlO, AlOH,
TiO, and TiO 2 . SiO has been extensively studied since
the early days of millimetre astronomy (see for example Gonz´alez Delgado et al. 2003), and several studies
have been devoted to AlO, owing to its relatively intense
lines in the millimeter band and the possible correlation with the infrared emission from alumina (Al 2 O 3 )
in the dust forming region (e.g. Tenenbaum & Ziurys
2009; Kami´nski et al. 2016; Decin et al. 2017). But at
present it is not yet known for certain which metal oxides and hydroxides are the initial building blocks of the
identified dust species.
Rotational lines of AlO were first detected in the red
supergiant VY CMa with the Arizona Radio Observatory (ARO) 10 m antenna by Tenenbaum & Ziurys
(2009); and subsequently observed in an interferometric
spectral line survey of VY CMa with the Submillimeter Array (SMA) (Kami´nski et al. 2013b); and in Mira
( _o_ Cet, Kami´nski et al. 2016), W Hya (Takigawa et al.
2017), and R Dor and IK Tau with ALMA (Decin et al.
2017).
A major contribution toward elucidating the connection of AlO and the dust is the comprehensive study of
the Al content in R Dor by Decin et al. (2017). They
concluded that the principal small gaseous precursors
of aluminum grains (AlO, AlOH, and AlCl) are: (1) observed both in and beyond the dust formation region, (2)
account for only a small fraction of the aluminum budget, and (3) condensation of small gaseous aluminum
bearing molecules is not 100% efficient.
Parallel to the work on AlO, rotational lines of
TiO and TiO 2 were observed with low peak flux in



VY CMa in the same spectral line survey with the SMA
(Kami´nski et al. 2013b,a). Subsequently TiO 2 was observed with much higher sensitivity and angular resolution in VY CMa with ALMA by De Beck et al. (2015),
who concluded TiO 2 is not a tracer for “low grain formation efficiency” in the complex source VY CMa, because
the emission extends well beyond the dust condensation
radius.

Both TiO and TiO 2 were also observed with ALMA in
three nearby AGB stars: Mira A (the AGB component
of a binary, Kami´nski et al. 2017), and R Dor and IK Tau
(Decin et al. 2018). Kami´nski et al. (2017) concluded
on the basis of the observations of TiO and TiO 2 and
indirect chemical arguments, that it is unlikely that substantial amounts of Ti are locked up in solids in Mira A
because: (1) the abundance of gaseous titanium species
is very high; (2) a gas phase chemical model is in general
agreement with the measured abundances of TiO and
TiO 2 in the millimeter band (Gobrecht et al. 2016); and
(3) TiO 2 emission extends 5 _._ 5 _R_ _⋆_ from Mira A, rather
than close to the star where the temperature is higher
and inorganic dust is expected to form. However Khouri
et al. (2018) estimated 80% of the expected Ti in Mira A
is either in the atomic form or in the dust grains on the
basis of: (1) a full radiative transfer analysis of CO close
to the star and a radiative transfer analysis of dust; (2)
an LTE analysis of TiO 2 in the ground vibrational state;
and (3) the relative abundance of TiO and TiO 2 derived
by Kami´nski et al. (2017).
There is a general consensus that additional observations with ALMA of AlO, AlOH, TiO, TiO 2, and
other metal oxides and hydroxides are needed to establish more stringent constraints on the dynamical chemical models of the inner winds of oxygen rich AGB and
RSG stars. Conclusive evidence for a strong spatial correlation with the onset of the dust condensation in the

inner wind of oxygen rich stars can only be made in a
credible way if accurate abundance structures of AlO,
TiO, TiO 2, etc are retrieved from rotational spectra observed at high sensitivity and angular resolution — i.e.,
astronomers cannot simply rely on the apparent correlation of millimeter-wave rotational line emission and

IR dust emission close to the central star. As previous observations of AlO in the ground vibrational state
have shown (Kami´nski et al. 2016; Decin et al. 2017),
gaseous AlO and AlOH are observed beyond the dust
condensation zone, but these two principal small aluminum bearing molecules and AlCl only consume _∼_ 2%
of the total Al budget. Hence, there is ample room left
for other Al bearing dust species (or larger gas-phase
clusters) to form, and the same might hold for TiO and
TiO 2 . Instead what is needed is a proper assessment

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 3



of the total Ti consumed in the gas phase species, and
whether other explanations — e.g., unresolved complex
density structures close to the central star — can be
ruled out.

With the aim of advancing the observations of the
metal oxides we examined existing interferometric spectral line surveys of two AGB stars (R Dor and IK Tau)
and the RSG star VY CMa for evidence of vibrationally
excited AlO and TiO (Sect. 3). However, owing to subtleties in the rotational spectrum of vibrationally excited
AlO, and the sparsity of direct laboratory measurements
of rotational transitions in vibrationally excited TiO, we
first reviewed the pertinent molecular physics of these
two open shell molecules (Sect. 2). The identification of
millimeter-wave rotational lines of vibrationally excited
AlO in three stars (VY CMa, R Dor, and IK Tau), and
vibrationally excited TiO in two of these (R Dor, and
IK Tau) is described in Sect. 3. This is followed by a full
radiative transfer analysis of the rotational lines of AlO
and TiO in R Dor (Sect. 4), from which abundance distributions were derived from observational data of AlO
(Sects. 4.3) and TiO (Sect. 4.4). In Sect. 5 we critically considered the evidence for whether TiO (and by
inference TiO 2 ) are seeds of the Al 2 O 3 dust in the gravitationally bound dust shell (GBDS) of R Dor.
In the work here we have adhered to the description of R Dor in the recent papers by Khouri et al.
(2016); Van de Sande et al. (2018), and Decin et al.
(2017, 2018). The semiregular (SR) variable oxygen rich
star R Dor is the closest AGB star to our Sun (59 pc,
Knapp et al. 2003). It has a very low mass loss rate
(1 _._ 6 _×_ 10 _[−]_ [7] M _⊙_ yr _[−]_ [1], Maercker et al. 2016), the stellar diameter is large (54 mas, Norris et al. 2012), it is
molecule rich, and there is a 27 GHz wide spectral line
survey in Band 7 with ALMA (Decin et al. 2018) in
which 22 molecules and isotopologues have been identified. It has been shown from polarized dust emission,
at high angular resolution in the optical and near IR,
that there is a high density dust envelope — or gravitationally bound dust shell (GBDS) — in R Dor that
is close to the star (Khouri et al. 2016, and references
therein). Modelling such a shell is needed to account for
the infrared emission from amorphous Al 2 O 3 and the
fractions of scattered light seen towards low mass-loss
rate stars such as R Dor and W Hya (Khouri et al. 2015).
The GBDS around R Dor is located within 1 _._ 7 _−_ 1 _._ 9 _R_ _⋆_
(Khouri et al. 2016) and is thought to consist of amorphous Al 2 O 3 grains or Fe-free silicates with a preference
towards Al 2 O 3, because Al 2 O 3 can condense at higher
temperatures. The stellar wind is launched from the
outer edge of the GBDS (Van de Sande et al. 2018, and
references therein). The focus here is on the inner wind



region within 300 mas of the central star that includes
most of the AlO and TiO emission (Decin et al. 2017,
2018), and especially the region within the dust condensation radius at ≲ (2-3) _R_ _⋆_ of the central star (Van de
Sande et al. 2018).


2. MOLECULAR PHYSICS OF VIBRATIONALLY

EXCITED AlO AND TiO


2.1. _AlO_


The millimeter-wave rotational spectra of AlO were
directly measured in the laboratory in the _v_ = 1 and
_v_ = 2 levels (Goto et al. 1994) and are tabulated in Launila & Banerjee (2009) and CDMS [1] . The spectroscopic
constants in the higher vibrational levels ( _v_ = 3 _, · · ·,_ 7)
of AlO were derived from rotationally resolved spectra
of the two lowest electronic transitions ( _A_ [2] Π _→_ _X_ [2] Σ
and _B_ [2] Σ _→_ _X_ [2] Σ; Launila & Berg 2011). Rotational
transitions in the higher vibrational levels with _v_ _≥_ 3
calculated with the constants of Launila & Berg (2011)
should be sufficiently accurate for unambiguous identification in the frequency band in which lines of ground
state AlO have been observed.

The rotational lines of AlO in the ground vibrational
state are especially wide compared with other molecules
such as CO and SiO, whose lines are primarily broadened by the Doppler effect, owing to the expanding envelopes in which they are observed. The large observed
line widths of AlO are a consequence of the molecular
physics: the nuclear spin ( _I_ ) of [27] Al is 5/2; the Fermi
contact magnetic hyperfine constant ( _b_ _F_ ) is especially
large; and the spin-rotation interaction ( _γ_ ) in the _X_ [2] Σ
electronic ground state causes the hyperfine structure
to appear as two partially overlapping patterns of 5 to
7 hyperfine split components, whose centroids are split
by approximately _γ_ .
In most diatomic molecules _γ_ changes very little in
successive vibrational levels. However, owing to a second
order interaction of the _X_ [2] Σ electronic ground state of
AlO with the low lying _A_ [2] Π excited state (7775 K above
ground, Ito & Goto 1994), the magnitude of _γ_ changes
from one vibrational level to the next such that in the
ground ( _v_ = 0) vibrational state ( _γ_ = 51 _._ 66 MHz, Goto
et al. 1994) _γ_ is about 3 times larger than in the _v_ = 1
level ( _γ_ = 15 _._ 95 MHz, Goto et al. 1994); _γ_ changes sign


1 The emphasis in this paper is on the new astronomical observations of the rotational transitions in vibrationally excited AlO,
but a comprehensive list of the laboratory measurements including the ground vibrational state can be found on the CDMS website at [https://cdms.astro.uni-koeln.de/classic/entries/.](https://cdms.astro.uni-koeln.de/classic/entries/)

4 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



between the _v_ = 1 and _v_ = 2 levels, [2] and the magnitude
is 1.6 times larger in the _v_ = 2 than the _v_ = 1 level ( _γ_ =
_−_ 31 _._ 467 MHz, Goto et al. 1994); and the magnitude of _γ_
is 3.3 times larger in the _v_ = 3 level than the _v_ = 2 level
( _γ_ = _−_ 103 _._ 43 MHz, Launila & Berg 2011). Therefore
the rotational lines in the _v_ = 1 level are much narrower

than in ground state, but lines in the _v_ = 3 level are
predicted to be very broad and might be difficult to
detect. Because the widths of the rotational lines of AlO

vary so markedly from one vibrational level to the next,
they provide an independent spectroscopic confirmation
of the assignments.


2.2. _TiO_


The pure rotational spectrum of TiO in the ground
_X_ [3] ∆electronic state was measured directly in the
ground vibrational state (Namiki et al. 1998; Steimle &
Virgo 2003; Breier et al. 2019), and recently two transitions in the first excited vibrational level were also
measured by (Breier et al. 2019). Namiki et al. (1998)
measured 12 rotational transitions of TiO between the

_J_ = 6 and 14 levels in the 220 _−_ 460 GHz range in a
large absorption cell, and the two lowest transitions at
63 and 95 GHz by microwave optical double resonance;
from these Namiki et al. derived the leading spectroscopic constants of TiO in the _X_ [3] ∆ _i_ electronic ground
state. The same group subsequently measured the permanent electric dipole moment ( _µ_ ) of the _X_ [3] ∆state
in the optical Stark spectrum of three electronic transitions (Steimle & Virgo 2003). More recently Breier et al.
(2019) accurately measured 14 rotational transitions of
TiO between 253 and 384 GHz with a 1 _σ_ measurement

uncertainty of 50 kHz in the ground vibrational state,
and two transitions in the _v_ = 1 level of the [3] ∆ 2 spinorbit component in absorption (at 286.5 and 318.3 GHz
with an uncertainty of 100 kHz) in a supersonic molecular beam.

The most comprehensive spectroscopic analysis of
the rotational spectrum of TiO was by Ram et al.
(1999), who derived the rotational and fine structure
constants in the four lowest excited vibrational levels
( _v_ = 1 _, · · ·,_ 4) from a combined analysis of rotationally
resolved spectra of the _A_ [3] Φ _→_ _X_ [3] ∆electronic transition near 1 _µ_ m in the laboratory and in a sunspot, and of
the direct measurements in the ground vibrational state.
The TiO molecule in its _X_ [3] ∆ Ω ground electronic state


2 For the rotational transitions of AlO discussed here, the theoretical relative intensities of the two spin rotation components are
nearly the same: 1.19 for the _N_ = 6 _−_ 5 transition and 1.12 for
the _N_ = 9 _−_ 8 transition, where the _J_ = _N_ + 1 _/_ 2 component is
more intense and is at higher frequency if _γ_ is positive.



is a good Hund’s case ( _a_ ) molecule with electron spin
angular momentum (Σ) of 1; orbital angular momentum (Λ) of 2; Ω= _|_ Λ + Σ _|_, where, by vector addition, Ω
has the possible values of 1, 2, and 3; and the rotational
levels have integral values with _J_ _≥_ Ω. Because the
spin-orbit constant ( _A_ ) is positive, the _X_ [3] ∆ 1 spin orbit
component is lowest in energy followed by the _X_ [3] ∆ 2,
and _X_ [3] ∆ 3 components with relative energies of about
140 K between components (see Fig. 1). The three spin
components are metastable, because _A_ is much greater
than the rotational constant _B_, and as a result the line
strengths for cross ladder (∆Ω= _±_ 1) transitions are
very small.


3. ASTRONOMICAL OBSERVATIONS


Many unidentified (U) lines have been observed in
spectral line surveys of AGB stars, suggesting the identification of new species might be within reach. When
we considered possible carriers of the U lines, for example towards the oxygen rich stars VY CMa, R Dor
and IK Tau (Kami´nski et al. 2013a; Decin et al. 2018),
we realized rotational lines of vibrationally excited AlO
and TiO should be readily identifiable for three reasons.
First, the lowest vibrational levels of both molecules
will be populated in the inner wind, because the vibrational frequencies of AlO (1389 K) and TiO (1438 K)
are comparable to the kinetic temperature of the gas
( _T_ gas ) within a few stellar radii of the star (see for example Eq. 1 in Sect. 4.2.2). Second, a wealth of supporting laboratory spectroscopy for both molecules has
been published as summarized in Sects. 2.1 and 2.2. And
finally, the peak fluxes of the ground state lines in sensitive interferometric spectra are high enough so lines
in the lowest few excited vibrational levels should be

observable in existing surveys.


3.1. _VY_ _CMa_


We began by searching for vibrationally excited AlO
in the spectral line survey of VY CMa in the 279 _._ 5 _−_
355 GHz range observed with the eight element SMA
at a modest sensitivity and angular resolution ( _∼_ 1 _[′′]_ ;
Kami´nski et al. 2013a). The initial identifications of
vibrationally excited AlO were made on the basis of
the calculated rotational frequencies in the three lowest excited vibrational levels ( _v_ _≤_ 3) in the absence of
fine and hyperfine structure (i.e., with _γ, b_ _F_, the dipoledipole magnetic hyperfine constant _c_, and the electric
quadrupole coupling constant _eQq_ constrained to zero).
Although the frequencies of the rotational transitions of
AlO calculated with only two spectroscopic constants
(the rotational constant _B_ and centrifugal distortion
constant _D_ ) are approximate, the centroids of the synthetic line profiles reproduce the astronomical features

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 5


1000


5000


800


4000


600

3000



400


200


0



2000


1000


0


|Col1|Col2|Col3|
|---|---|---|
||||
||||



1 2 3



0 1 2 3

v



**Figure** **1.** Energy level diagram of TiO in the _X_ [3] ∆ Ω ground electronic state calculated with effective spectroscopic constants
(see Table 2 in Ram et al. 1999). _Left:_ The rotational levels with _J_ _≤_ 30 in the ground ( _v_ = 0) vibrational state of the three
fine structure components (Ω= 1 _,_ 2 _,_ and 3). _Right:_ Rotational levels with _J_ _≤_ 30 in the ground and three lowest excited
vibrational levels with the same color coding for Ωas in the panel on the left.


**Table** **1.** AlO in VY CMa Observed with the SMA


_N_ _[′]_ _→_ _N_ _v_ _ν_ calc _[a]_ _ν_ obs _[b]_ Peak Flux ∆ _υ_ _υ_ LSR _[d]_ Beam Int. Flux Line width


(MHz) (MHz) (mJy) (km s _[−]_ [1] ) (km s _[−]_ [1] ) ( _[′′]_ ) (Jy km s _[−]_ [1] ) ratio


8 _→_ 7 0 306,197.319 306,172.3 _±_ 0.8 580 53.8 _±_ 2.0 24.5 _±_ 0.8 0.91 32.4 _±_ 1.6 1.0

1 303,412.064 303,390.0 _±_ 0.6 477 17.5 _±_ 1.5 21.8 _±_ 0.6 0.91 8.9 _±_ 0.9 3 _._ 1 _±_ 0 _._ 3
2 300,611.392 300,591.0 _±_ 3.0 _[c]_ 340 41.0 _±_ 7.2 20.3 _±_ 3.0 0.92 7.7 _±_ 1.6 1 _._ 3 _±_ 0 _._ 2

9 _→_ 8 0 344,451.721 344,423.4 _±_ 0.3 1040 45.8 _±_ 0.7 24.6 _±_ 0.3 0.88 50.8 _±_ 1.0 1.0

1 341,318.153 341,294.6 _±_ 0.6 661 12.6 _±_ 1.1 20.7 _±_ 0.5 0.82 12.5 _±_ 1.1 3 _._ 6 _±_ 0 _._ 3
2 338,167.232 338,141.0 _±_ 1.0 _[c]_ 242 24.2 _±_ 2.1 23.3 _±_ 0.9 0.81 6.2 _±_ 0.7 1 _._ 9 _±_ 0 _._ 2


_a_ Rest frequencies of the rotational transitions calculated in the absence of fine and hyperfine structure — see text for
details.

_b_
Measured LSR frequency.

_c_ Frequency estimated for lines with low signal-to-noise.

_d_
LSR velocity calculated based on the difference between the rest frequency and the measured LSR frequency of each line.

6 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



344.5 344.4 344.3



(GHz)

12

10

8

6

4

2

0


-2

-4



(GHz)


(GHz)



341.4 341.3 341.2



338.2 338.1 338



14

12

10

8

6

4

2

0


-2







5

4

3

2

1

0


-1

-2

-3





-100 0 100

V LSR (km s [-1] )


306.2 306.1



(GHz)



-100 0 100

V LSR (km s [-1] )


300.7 300.6 300.5



-100 0 100

V LSR (km s [-1] )


303.5 303.4 303.3



10


8


6


4


2


0


-2





10


8


6


4


2


0


-2


-4





5

4

3

2

1

0


-1

-2

-3

-4





-100 0 100

V LSR (km s [-1] )



-100 0 100

V LSR (km s [-1] )



-100 0 100

V LSR (km s [-1] )



**Figure** **2.** Two successive rotational transitions of AlO observed with a 1 _[′′]_ beam in VY CMa with the SMA (Kami´nski et al.
2013a). The transition quantum numbers are indicated in the top left of each box. Data are plotted as red histograms, the
unresolved fine and hyperfine structure is indicated by the vertical lines in green, and theoretical Gaussian profiles from least
squares fits to the observed spectra are plotted in blue. In the _v_ = 2 level the full composite synthetic profile with hyperfine
structure is plotted, because the spectra were too noisy to analyze with a theoretical Gaussian profile.

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 7



to within a few MHz and are sufficient for establishing
the identification of lines of vibrationally excited AlO in
the astronomical spectra. The frequencies and relative
intensities of the hyperfine components used to calculate
the synthetic profiles of AlO in the _v_ = 0 _,_ 1 _,_ and 2 levels
are tabulated in (Launila & Banerjee 2009). The term
energy for the _v_ = 1 excited vibrational level is 1389 K
and 2758 K for the _v_ = 2 level.

Two successive rotational transitions of AlO in the
ground vibrational state ( _N_ = 8 _→_ 7 at 306 GHz, and
_N_ = 9 _→_ 8 at 344 GHz) were covered in the SMA
survey, and both were also observed in vibrationally excited levels: the _v_ = 1 and possibly the _v_ = 2 level in
the _N_ = 8 _→_ 7 transition, and _v_ = 1 and _v_ = 2 levels in the _N_ = 9 _→_ 8 transition (see Fig. 2 and Table
1). The line parameters for most measurements were
derived by fitting Gaussian profiles to the astronomical features. All measurements were done on spectra
obtained from the central pixel of the SMA data, corresponding to a restoring beam of _∼_ 1 _[′′]_ centred on the
continuum peak of VY CMa (for precise beam sizes at
different frequencies, see Kami´nski et al. 2013a). The
observed frequencies _ν_ obs in the ground vibrational state
and the _v_ = 1 level and the FWHM line width, ∆ _v_, were
derived from Gaussian profiles that were least squares fit
to the spectra (see Fig. 2). The synthetic profiles of the
lines in the _v_ = 2 vibrational state were obtained by
representing each hyperfine component with a Gaussian
profile whose HWHM was 2.5 km s _[−]_ [1] . The relative intensities of the hyperfine components were equivalent to
the theoretical relative intensities in Launila & Banerjee (2009). The variables in the least squares fit of the
synthetic profile to the observed profile were: an intensity (scaling) factor of the composite theoretical synthetic profile and the center frequency. The mean central LSR velocity _υ_ LSR = 21 _._ 5 _±_ 3 _._ 3 km s _[−]_ [1] for the four
rotational transitions in the excited vibrational levels

of AlO in Table 1 is in good agreement with the stellar velocity ( _v_ LSR = 22 km s _[−]_ [1], Kami´nski et al. 2013a)
and the LSR velocity of AlO in the ground vibrational
state ( _υ_ LSR = 25 _±_ 2 km s _[−]_ [1] ) observed with the SMA
in VY CMa by Kami´nski et al. (2013a), confirming the
assignment of the new lines of vibrationally excited AlO.
As expected, the FWHM of the lines are 3 _._ 3 _±_ 0 _._ 4 times
smaller in the _v_ = 1 level, and 1 _._ 6 _±_ 0 _._ 3 times smaller in
the _v_ = 2 level than those in the ground vibrational state
— i.e., close to the theoretical predictions discussed in
Sect. 2.1, thereby providing further confirmation of the
line assignments. The rotational lines in the _v_ = 3 vibrational level were not observed because the predicted
peak flux is comparable to the peak noise in the spectra



shown in Fig. 2. The details of the detected lines are
given in Table 1.


3.2. _R_ _Dor_ _and_ _IK_ _Tau_


The data used in this paper were taken from the
ALMA projects with codes and other observing details
given in Table 2; see the ALMA Science Archive for more
details. The raw data were calibrated using standard
ALMA procedures including application of instrumental calibration and corrections derived from the band
pass and phase reference sources. The flux scale is in
most cases accurate to 7% or better; however, for AlO
_N_ = 6 _→_ 5 the phase reference source flux density fluctuated by 12% over the observations, which is probably
bona fide variability but gives an upper bound to the uncertainty for these data. Decin et al. (2018) gives details
of the data reduction for 2013.1.00166.S and we followed

a similar route in all cases. In brief, line-free channels
were identified and used for self-calibration of the strong
continuum emission from the star (and potentially hot
dust). After applying all calibration to the line data,
spectral cubes were made at the resolutions and sensitivities given in Table 2, averaging where necessary to
improve surface brightness sensitivity.
The continuum was unresolved or barely resolved,
with a flux density ranging from 252 mJy in the image covering AlO _N_ = 6 _→_ 5, to 596 mJy covering AlO
_N_ = 9 _→_ 8. The relative astrometry between continuum
and line in the same data-set is limited by the synthesised beam/signal-to-noise ratio (S/N). This is _<_ 1 mas
for all continuum images. For the moment maps, the
relative position uncertainty is _∼_ 5 mas for the weakest
emission, down to _<_ 1 mas for the brightest — less than
a pixel in all cases.
We extracted spectra in an aperture of 150 mas radius
for AlO and 300 mas for TiO towards R Dor and in an

aperture of 320 mas for AlO or 160 mas for TiO for
IK Tau. The peak and integrated fluxes given in Tables
3 and 4 were measured from these spectra. We made
zeroth-order moments (integrated flux density) over the
channels where the line signal exceeded the rms. For
the cases where lines participate in overlaps with lines
of other species, the details are discussed in Sections
3.2.1 and 3.2.2 for AlO and TiO, respectively. Due to
the quality and quantity of data, we mostly focus on
R Dor for our analysis.


3.2.1. _AlO_


Following the initial identification of vibrationally excited AlO in the SMA survey of VY CMa, we found
evidence for the _N_ = 9 _→_ 8 transition in the _v_ = 2
level ( _E_ _u_ = 2758 K) with an approximate peak flux of
30 _±_ 8 mJy at the expected frequency and line width (see

8 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten


**Table** **2.** Details of ALMA observations of AlO and TiO towards R Dor and IK Tau.


Transition Freq Proposal Date(s) ToS _[a]_ PWV _[b]_ Synth. beam _[c]_ Vel. res. rms _[d]_ MRS _[e]_


(GHz) (yyyymmdd) (min) (mm) (mas,mas,deg) (km s _[−]_ [1] ) (mJy) (arcsec)


**R** **Dor**

AlO _N_ = 6 _→_ 5 229.670 2017.1.00824.S 20171024– 192 0.6 33, 29, +55 0.32 0.8 2.6

20171026

AlO _N_ = 7 _→_ 6 267.937 2017.1.00824.S 20171231– 165 1.2 138,131, _−_ 55 0.273 1.0 5.0

20180105

AlO _N_ = 8 _→_ 7 306.197 2017.A.00012.S 20181211 6.5 0.9 110, 88, _−_ 45 0.911 3.8 3.1

AlO _N_ = 9 _→_ 8 338.167– 2013.1.00166.S 20150827– 25.2 0.3– 165, 127, +29 0.9– 3.5– 3.1

& TiO lines 355.623 20150901 0.7 150, 125, +21 0.8 4.5

**IK** **Tau**

AlO _N_ = 9 _→_ 8 338.167– 2013.1.00166.S 20150813– 10 0.2– 175, 145, _−_ 15 1.7– 4.7– 3.1

& TiO lines 355.623 20150828 1.7 165, 135, _−_ 10 1.6 5.3


_a_ Time on source, interleaving with phase reference observations every 5–7 min.

_b_
Precipitable water vapour at time of observation.

_c_ Listed are the major and minor axes, and the position angle of the synthetic beam.

_d_
The rms is the noise per channel off-source in the line cube.

_e_ Maximum recoverable scale; reliable images can only be made at slightly smaller scales.



0.4


0.3


0.2


0.1


0.50 0.25 0.00 0.25 0.50

RA offset [arcsec]



0.50 0.25 0.00 0.25 0.50

RA offset [arcsec]



0.6


0.4


0.2


0.0


0.2


0.4


0.6



|Col1|AlO v=2 (9-8)|
|---|---|
|||
|||
|||
|||
|||
|||
|||


0.50 0.25 0.00 0.25 0.50

RA offset [arcsec]



0.5


0.4


0.3


0.2


0.1


0.0


0.1



0.6


0.4


0.2


0.0


0.2


0.4


0.6



1.0


0.8


0.6


0.4


0.2


0.0



0.6


0.4


0.2


0.0


0.2


0.4


0.6



**Figure** **3.** For R Dor: zeroth moment maps of rotational transitions of AlO in the ground ( _X_ [2] Σ) electronic state, observed
with ALMA. _Left:_ _N_ = 9 _→_ 8 in the _v_ = 2 vibrational state. _Centre:_ _N_ = 8 _→_ 7 in the ground vibrational state.
_Right:_ _N_ = 7 _→_ 6 in the ground vibrational state. The black dashed contours indicate flux levels at 3, 6, 12... times the
off-source noise rms for AlO. The synthesized beams are indicated by ellipses in the lower left corner of each panel. The dotted white contours are at levels of 1, 10, and 90% of the peak continuum flux and are included to indicate the position of the star.



Table 3) in a sensitive spectral line survey of R Dor over
the 335–362 GHz frequency range with ALMA (Decin
et al. 2018). Unfortunately the _N_ = 9 _→_ 8 transition
in the _v_ = 1 level of AlO at 341,318 MHz is within
3 _−_ 4 MHz of two transitions of SO 2 (for details of SO 2
in R Dor see Danilovich et al. 2020), and the rotational
transition in the _v_ = 3 level at 334,999 MHz lies just
outside of the frequency range of the survey. The corresponding lines of SO 2 are much less prominent in the
SMA survey of VY CMa than in the ALMA survey of



R Dor, and did not preclude the identification of the
_N_ = 9 _→_ 8 transition in the _v_ = 1 level in VY CMa.

In addition to these previously published data, we
have obtained some new observations using ALMA, in a
search for the _N_ = 6 _→_ 5 through _N_ = 8 _→_ 7 rotational
transitions in the ground vibrational state. In Table 3
we list the frequencies of all the observed AlO transitions in the absence of fine and hyperfine structure calculated from the rotational constant _B_ and centrifugal
distortion constant _D_ derived from the measurements

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 9


**Table** **3.** The observed transitions of AlO towards R Dor and IK Tau.


_v_ _N_ Frequency (MHz) _υ_ LSR _[e]_ Peak flux ∆ _υ_ Aperture Integrated flux

Laboratory _[a]_ Observed _[b]_ (km s _[−]_ [1] ) (mJy) (km s _[−]_ [1] ) (mas) (mJy km s _[−]_ [1] )


**R** **Dor**
0 6 _→_ 5 229,670.239 _· · ·_ _[c]_ _· · ·_ _· · ·_ _· · ·_ _· · ·_ _· · ·_

0 7 _→_ 6 267,936.560 267 _,_ 932 _._ 6 _±_ 5 _._ 4 4.4 19 _±_ 3 73 150 775 _±_ 23

0 8 _→_ 7 306,197.319 306 _,_ 191 _±_ 12 5.4 50 _±_ 6 68 150 1986 _±_ 90

0 9 _→_ 8 344,451.721 344 _,_ 445 _._ 1 _±_ 1 _._ 5 5.8 87 _±_ 12 51.0 150 3133 _±_ 75

2 9 _→_ 8 338,167.232 338 _,_ 156 _±_ 12 10.3 22 _±_ 5 29.7 150 612 _±_ 14

**IK** **Tau** _[d]_


0 9 _→_ 8 344,451.721 _· · ·_ _· · ·_ 23 _· · ·_ 320 247

2 9 _→_ 8 338,167.232 _· · ·_ _· · ·_ ≲ 10 _· · ·_ 320 _· · ·_


_a_ Frequencies of the rotational transitions given in the absence of fine and hyperfine structure — see text for
details.

_b_
Measured LSR frequency.

_c_ The high spatial resolution of this observation resulted in an image dominated by absorption against the star,
complicating the interpretation.
_d_ The peak and integrated flux values of the _N_ = 9 _→_ 8, _v_ = 0 line for IK Tau were taken from Decin et al.

(2017). All other values were obtained from our present analysis.

_e_ LSR velocity calculated based on the difference between the rest frequency and the observed LSR frequency
of each line.



tabulated in Lovas & Tiemann (1974). The full set of
AlO observed spectra towards R Dor is plotted with our
radiative transfer model results in Fig. 8.
The approximate location and extent of AlO in R Dor
was determined from zeroth moment and channel maps
obtained with ALMA (initially from the spectral line
survey of Decin et al. 2017, which shows the channel
maps of AlO _N_ = 9 _→_ 8, _v_ = 0 towards R Dor in their
Fig. 3). Although the AlO emission mainly coincides
with the continuum emission, there is additional emis
sion to the southeast that extends out to about 280 mas

from the star, as can be seen for the _N_ = 8 _→_ 7 and
_N_ = 7 _→_ 6 zeroth moment maps in Fig. 3. The
_N_ = 9 _→_ 8 emission (in both _v_ = 0 _,_ 2 vibrational
states) is only just resolved. Nevertheless, from the azimuthally averaged flux density versus distance from the
star, Decin et al. (2017) determined that approximately
50% of the AlO emission is within _∼_ 3 _R_ _⋆_ of the central
star (see their Fig. 4).
Shown in Fig. 4 is a vibrational temperature (VT)
diagram for AlO in R Dor. The purpose of the VT diagram is to establish: (1) whether there is any evidence
for anomalies in the emission in the ground and excited
vibrational levels; (2) whether the observed emission can
be analyzed in the 1D approximation; and (3) whether
the derived vibrational temperature ( _T_ vib ) can inform







0 1000 2000 3000
Energy (K)


**Figure** **4.** Vibrational temperature diagram for AlO in
R Dor derived from three successive rotational transitions in

the ground vibrational state and one in the second excited
( _v_ = 2) vibrational level.


us about the region where AlO is observed. The VT
diagram was constructed with the integrated flux of the
_N_ = 9 _−_ 8 transition in the _v_ = 2 excited vibrational

level, and three transitions in the ground vibrational
state (Fig. 4), and the standard expression (see Eq. A5
in Snyder et al. 2005) on the assumption the emission
fills the synthesized beam of the telescope. The parti

10 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



tion function ( _Z_ ) includes all the rotational-vibrational
levels with all the appropriate degeneracy factors in the
comprehensive analysis of Patrascu et al. (2015). From
this we determined the total column density ( _N_ ), but it
should be emphasized that a more informative description of the abundance of AlO in the inner wind is ob
tained from the full radiative transfer analysis discussed
in detail in Sect. 4. The high observed _T_ vib of AlO in
R Dor of 1860 _±_ 200 K implies a fraction of the emission
arises within about 2 _R_ _⋆_ (or _∼_ 60 mas) from the central
star — i.e., a fraction of the AlO emission is within the
dust formation zone of R Dor at ≲ 2 _R_ _⋆_ (Khouri et al.
2016) — whose effective temperature ( _T_ eff ) is 2400 K
(Maercker et al. 2016).
Although the AlO emission in the _N_ = 9 _→_ 8 line
in the ground vibrational state is very weak in IK Tau,
Decin et al. (2017) succeeded in deriving an abundance
distribution, but the spectra in IK Tau are not analyzed here because no new lines were observed in the
ground vibrational state and the line in the _v_ = 2 level
at 338,167 MHz is exceedingly weak.


3.2.2. _TiO_


Following the identification of vibrationally excited
AlO we turned our attention to TiO. The three spin
components of the _X_ [3] ∆ Ω electronic ground state (labelled Ω= 1 _,_ 2 _,_ 3) were observed in the spectral line
survey of R Dor and IK Tau by Decin et al. (2018).
Frequencies of the rotational transitions in the ground
vibrational state were calculated from constants derived
from the measurements in Namiki et al. (1998); Breier
et al. (2019), and CDMS; frequencies in the _v_ = 1 _,_ 2 _,_ 3
excited vibrational levels were calculated from the spectroscopic constants in Ram et al. (1999). The term
energies of the four lowest excited vibrational levels
( _v_ = 1 _,_ 2 _,_ 3 _,_ and 4) are 1438 K, 2863 K, 4275 K, and
5673 K.

In all, five lines of vibrationally excited TiO were identified towards R Dor: three in the _v_ = 1 level, and two
in the _v_ = 2 level (see Table 4). The _J_ = 11 _→_ 10 transition in the _v_ = 2 level of [3] ∆ 2 is uncertain, because it
is blended with a line of [34] SO 2 which is 8 MHz lower
in frequency. The TiO emission towards R Dor is not
spatially resolved in our observations, indicating that
it is less spatially extended than AlO. Frequencies and
other details of these lines are listed in Table 4. Based

on the line frequencies reported in Table 4, we find the
mean central velocity of the TiO lines towards R Dor is
_υ_ cent(TiO) = 7 _._ 8 _±_ 0 _._ 4 km s _[−]_ [1], based on fitting Gaussians
to the emission for lines with _v_ _≤_ 2 and excluding the
line blended with SO 2 . This is slightly red-shifted from
the _υ_ LSR = 7 _._ 0 _±_ 0 _._ 5 km s _[−]_ [1] of R Dor (Danilovich et al.



1.6


1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0



0.6


0.4


0.2


0.0


0.2


0.4


0.6




|Col1|TiO =1 v=0<br>,,|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||



0.50 0.25 0.00 0.25 0.50

RA offset [arcsec]


**Figure** **5.** Zeroth moment map of the lowest fine structure
component ( _X_ [3] ∆ 1 ) of TiO in the ground ( _v_ = 0) vibrational
state observed in R Dor with ALMA. Indicated in white in

the lower left corner is the 136 _×_ 147 mas beam. The white

dotted contours indicate the continuum flux at levels of 1,
10, and 90% of peak flux.


2016). A similar small shift of _∼_ 1 km s _[−]_ [1] was also seen
for vibrationally excited SO lines by Danilovich et al.
(2020) and could be due to dynamics in the inner region
of R Dor, where both TiO and vibrationally excited SO
originate.
The vibrational temperature for TiO in R Dor was
derived by the same procedure adopted for AlO in
Sect. 3.2.1, except the partition function is from McKemmish et al. (2019). Shown in Fig. 6 is a vibrational
temperature diagram for the rotational transitions in
the three spin components in the ground state and the
_v_ = 1 level, and two spin components in the _v_ = 2 level.
From the derived _T_ vib of 1800 _±_ 170 K (see diagram in
Fig. 6), we estimate the peak flux of the _J_ = 11 _→_ 10
rotational transitions in the _v_ = 3 excited vibrational
level ( _E_ _u_ = 4275 K) of 19 mJy is within a few mJy of
the peak flux in the spectra centered on the Ω= 2 and
Ω= 3 spin components (see Table 4 and Fig. 11).
We conclude that the identifications of the lines of
vibrationally excited TiO towards R Dor are secure and
no lines are missing. The calculated frequencies in the
_v_ = 1 _,_ and 2 levels reproduce the frequency of all five
astronomical features to within _±_ 0 _._ 3 MHz of the mean
central velocity _υ_ cent(TiO) = 7 _._ 8 km s _[−]_ [1] . The peak flux
of the lines in the three spin components in each excited
vibrational level are comparable: 2 _._ 4 _±_ 0 _._ 3 times lower
in the _v_ = 1 level, 3 _._ 3 _±_ 0 _._ 8 lower in _v_ = 2, and 15 _._ 1 _±_ 0 _._ 3
lower in _v_ = 3 than the corresponding transitions in the
ground vibrational state, as expected if TiO is close to
the central star and _T_ vib = 1800 K (cf. _T_ eff = 2400 K,
Decin et al. 2017).

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 11


**Table** **4.** The _J_ = 11 _→_ 10 transition of _X_ [3] ∆TiO in R Dor and IK Tau


Ω _v_ Frequency (MHz) _υ_ LSR _[d]_ Peak flux ∆ _υ_ Aperture Integrated flux

Laboratory Observed _[a]_ (km s _[−]_ [1] ) (mJy) (km s _[−]_ [1] ) (mas) (mJy km s _[−]_ [1] )


**R** **Dor**

1 0 348,159.8 348 _,_ 150 _._ 75 _±_ 0 _._ 22 7.8 221 _±_ 9 9 _._ 4 _±_ 0 _._ 4 300 2 _,_ 077 _±_ 122

1 346,198.2 346 _,_ 188 _._ 8 _±_ 0 _._ 4 8.1 91 _±_ 7 8 _._ 8 _±_ 0 _._ 9 300 804 _±_ 103

2 344,224.3 344 _,_ 225 _±_ 3 _._ 1 7.5 44 _±_ 4 8 _._ 2 _±_ 0 _._ 9 300 377 _±_ 13

3 342,239.0 _· · ·_ _[b]_ _· · ·_ _· · ·_ _· · ·_ 300 _· · ·_

2 0 352,157.6 352 _,_ 148 _._ 18 _±_ 0 _._ 25 8.0 184 _±_ 8 9 _._ 4 _±_ 0 _._ 5 300 1 _,_ 739 _±_ 119

1 350,147.5 350 _,_ 138 _._ 9 _±_ 0 _._ 4 7.4 88 _±_ 7 9 _._ 1 _±_ 0 _._ 9 300 799 _±_ 101
2 348,125.8 (348 _,_ 112 _._ 1 _±_ 0 _._ 17) _[c]_ _· · ·_ (73 _±_ 16) (12 _._ 9 _±_ 0 _._ 3) 300 (943)

3 346,090.1 _· · ·_ _· · ·_ 12 _±_ 1 8 _._ 7 _±_ 5 _._ 2 300 _· · ·_

3 0 355,623.3 355 _,_ 614 _._ 38 _±_ 0 _._ 26 7.5 208 _±_ 8 11 _._ 0 _±_ 0 _._ 5 300 2 _,_ 297 _±_ 137

1 353,573.4 353 _,_ 575 _._ 2 _±_ 0 _._ 7 8.5 75 _±_ 11 8 _._ 4 _±_ 1 _._ 4 300 630 _±_ 140

2 351,511.2 351 _,_ 502 _._ 5 _±_ 1 _._ 5 7.5 51 _±_ 14 7 _._ 7 _±_ 2 _._ 4 300 391 _±_ 127

3 349,436.5 _· · ·_ _· · ·_ 14 _±_ 1 17 _._ 2 _±_ 3 _._ 4 300 _· · ·_

**IK** **Tau**

1 0 348,159.8 348 _,_ 159 _._ 6 _±_ 0 _._ 8 32.2 25 _±_ 5 6 _._ 6 _±_ 1 _._ 5 160 230

1 346,198.2 _· · ·_ _· · ·_ _· · ·_ _· · ·_ 160 _· · ·_

2 0 352,157.6 352 _,_ 157 _._ 1 _±_ 0 _._ 8 31.2 30 _±_ 5 8 _._ 0 _±_ 1 _._ 5 160 198

1 350,147.5 350 _,_ 147 _._ 3 _±_ 2 _._ 5 32.4 17 _±_ 4 6 _._ 0 _±_ 5 _._ 1 160 139

3 0 355,623.3 355 _,_ 625 _._ 0 _±_ 4 _._ 1 32.2 41 _±_ 12 6 _._ 6 _±_ 5 _._ 7 160 239

1 353,573.4 353 _,_ 575 _._ 7 _±_ 1 _._ 6 32.2 15 _±_ 4 4 _._ 2 _±_ 3 _._ 4 160 75


_a_ Measured LSR frequency.
_b_ The 20 1 _,_ 19 _−_ 19 2 _,_ 18 transition of 34 SO 2 ( _E_ _u_ = 198 K) at 342,232 MHz and peak flux 93 mJy is within 7 MHz
of the transition in the _v_ = 3 level of [3] ∆ 1 TiO.

_c_ The rotational line in the _v_ = 2 level of 3 ∆ 2 TiO has a lower observed frequency than expected, and large line
width, owing to a blend with the 19 4 _,_ 16 _→_ 19 3 _,_ 17 transition of [34] SO 2 .

_d_
LSR velocity calculated based on the difference between the rest frequency and the observed LSR frequency of
each line.



For IK Tau the peak flux densities of the lines of TiO
in the ground vibrational state are about 10 times lower
than for R Dor (see Figures 7 and 11, and Table 4).
Lines in the _v_ = 1 level in the Ω= 2 and Ω= 3 spin
components were observed with a peak flux that is only
two times higher than the rms noise, and no lines were
detected in the _v_ = 2 level of TiO towards IK Tau. The

Ω= 1 component of the line in the _v_ = 1 state is also undetected, due to a strong overlap with the NS line group
at 346.22 GHz. The TiO emission from IK Tau is slightly
blue-shifted with respect to the LSR velocity. Considering only the five detected lines shown in Fig. 7, we find a
mean central velocity of _υ_ cent(TiO) = 32 _._ 4 _±_ 0 _._ 4 km s _[−]_ [1] .
This is offset from the _υ_ LSR = 34 _±_ 1 km s _[−]_ [1] of IK Tau
(Decin et al. 2018) by 1.6 km s _[−]_ [1] towards the blue, and
could also be due to as-yet unknown inner wind dynam


ics. However owing to the estimated uncertainties in
the rest frequencies and the low signal-to-noise of the
data, confirmation of the apparent offset in velocity will
require more accurate laboratory and more sensitive astronomical measurements.


4. RADIATIVE TRANSFER ANALYSIS OF R DOR


4.1. _Method_


Due to the quality and availability of observations, we
only performed radiative transfer analyses for R Dor.
For this, we used a 1D spherically symmetric nonLTE radiative transfer program based on the accelerated lambda iteration method (ALI; Rybicki & Hummer
1991; Maercker et al. 2008) to calculate the abundances
and line profiles of AlO and TiO. The calculated line
profiles were then compared with the lines of AlO or

12 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten





TiO observed with ALMA as described in Sects. 3.2.1

and 3.2.2.

For modelling purposes, we analyzed spectra extracted with a circular aperture with a radius of 150 mas,
for AlO, and 300 mas, for TiO, because this included
all the observed emission (see Sect. 3.2 for details).
When ray-tracing our modelled CSE, we used (circular) model beams the same size as the extraction aperture, to allow for direct comparisons. Our model circumstellar envelopes (CSEs) were divided into 30 shells,
evenly spaced on a logarithmic scale from an inner
radius _r_ 0 = 3 _._ 3 _×_ 10 [13] cm, out to an outer radius
_r_ max = 4 _×_ 10 [14] cm. The velocity resolution of the model
lines is approximately 0.5 km s _[−]_ [1], however the final resolution of the AlO lines, taking hyperfine structure into
account, is approximately 1 km s _[−]_ [1], to match the resolution of the observations. The observed AlO lines are

significantly broadened by the unresolved fine and hyperfine structure, and the TiO lines are split into three
fine structure components as discussed in Sects. 2.1 and
2.2, respectively. In the following two sections (4.1.1 and
4.1.2) we describe our treatment of hyperfine structure
for AlO and fine structure for TiO, respectively.


4.1.1. _AlO_





0 1000 2000 3000
Energy (K)


**Figure** **6.** Vibrational temperature diagram for TiO in
R Dor derived from the _J_ = 11 _−_ 10 rotational transition

in the three spin components in the ground vibrational state
and first excited _v_ = 1 vibrational level. Only two rotational
transitions were observed in the _v_ = 2 level, because of the
coincidence of the transition in the [3] ∆ 2 component with a
line of [34] SO 2 .

















































**Figure** **7.** The _J_ = 11 _→_ 10 rotational transition of TiO
in the three fine structure components in the ground ( _v_ = 0)
and first excited vibrational level ( _v_ = 1) observed towards
IK Tau. The spectra were extracted from the ALMA data
with an aperture whose radius is 160 mas. The grey dashed
vertical lines indicate the expected center of the TiO line
profiles for the assumed _υ_ LSR = 34 km s _[−]_ [1] . Lines of other
molecules are indicated in red.



Explicitly including all the AlO hyperfine levels and
the connecting transitions in the radiative transfer analysis is computationally prohibitive, even if the included
levels are restricted to a relatively small number of rotational levels (e.g., _N_ _≤_ 20). Following the procedure
in Decin et al. (2017), AlO was first treated without
hyperfine structure to obtain the total integrated line
strengths for each observed transition. The calculated
total integrated flux for each transition was then distributed among the individual hyperfine components according to their quantum mechanical line strengths (see
Yamada et al. 1990; Goto et al. 1994; Launila & Jonsson 1994; Launila & Banerjee 2009). These were then
summed to obtain the theoretical line profile shape. We
used Gaussians with a HWHM of 3 km s _[−]_ [1], close to the
innermost velocity as derived from the sound speed [3], to
represent the hyperfine components. In Sect. A.4 we discuss the impact of the choice of widths for the hyperfine

components.


4.1.2. _TiO_


To analyze TiO in the most efficient way possible, we
first ran a radiative transfer model excluding the fine
structure — i.e., TiO was treated as though it were a


3 The sound speed was found by assuming an ideal gas at a temperature of 1000 K.

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 13



closed shell molecule. To facilitate this, we took the
energy levels and Einstein A coefficients from McKemmish et al. (2019) for the lowest fine structure component Ω= 1 (see the left hand panel of Fig. 1 for an
overview of the fine structure in TiO). After running
a radiative transfer model excluding the fine structure,
we scaled the amplitude of the calculated line profiles
to the relative intensities of the transitions in the three

fine structure components tabulated in CDMS, on the
assumption of LTE and a gas kinetic temperature of
1800 K, and compared our calculated profiles with the
observed spectra. For _v_ _>_ 0 we assumed the same intensity scaling for the fine structure components as those
in the ground vibrational state (see Sect. 4.4).


4.2. _Input_ _parameters_


4.2.1. _Molecular_ _parameters_


A proper non-LTE analysis of the observations of the
two metal oxides AlO and TiO requires the following
molecular data: (1) Einstein _A_ coefficients for rotational
transitions in the _v_ = 0 state; (2) Einstein _A_ coefficients
for rotational transitions in the lower excited vibrational
levels; (3) Einstein _A_ coefficients for the rovibrational
∆ _v_ = 1 _,_ 2 _, · · ·_ transitions; and (4) collisional rates for
H 2 –AlO and H 2 –TiO. The Einstein _A_ coefficients for
AlO and TiO were from Patrascu et al. (2015) and McKemmish et al. (2019), respectively. The collision rates
for H 2 –AlO and H 2 –TiO have not been calculated. Instead the rates for He-SiO (Dayou & Balan¸ca 2006) and
He–NaCl (Quintana-Lacaci et al. 2016) — appropriately
scaled to account for the difference in mass of these systems (see Sch¨oier et al. 2005, for details) — were used
as surrogates.


4.2.2. _Stellar_ _and_ _circumstellar_ _parameters_


The circumstellar model in our radiative transfer cal
culations of AlO and TiO is based on the circumstellar
models of R Dor presented in Maercker et al. (2016),
Van de Sande et al. (2018), and Decin et al. (2017).
The present model includes more observations of AlO
and a larger number of energy levels and transitions
than the one in Decin et al. (2017). The TiO model
is based on the same circumstellar parameters as AlO,
which are given in Table 5. This leaves _f_ molecule, the
inner molecular abundance (relative to H 2 ), as the only
free parameter in our models.
The gas kinetic temperature was assumed to follow a
power law radial profile (Decin et al. 2006, and references
therein)



**Table** **5.** Stellar and circumstellar parameters for R Dor.


Property Units R Dor


_R_ _⋆_ cm 3 _._ 3 _×_ 10 [13]


_T_ eff K 2400

_D_ pc 59

_L_ _⋆_ L _⊙_ 6500
_M_ ˙ 10 _[−]_ [7] _M_ _⊙_ yr _[−]_ [1] 1 _._ 6
_υ_ _∞_ km _s_ _[−]_ [1] 5.7
_υ_ 0 km _s_ _[−]_ [1] 3
_υ_ LSR km _s_ _[−]_ [1] 7.0
_υ_ turb km _s_ _[−]_ [1] 1

_ϵ_ _· · ·_ 0.65

_β_ _· · ·_ 1.5
_r_ 0 cm 3 _._ 3 _×_ 10 [13]

_r_ _e_ cm 1 _×_ 10 [14]


with _ϵ_ = 0 _._ 65, _T_ eff = 2400 K, and _R_ _⋆_ = 3 _._ 3 _×_ 10 [13] cm.
This value of _R_ _⋆_ is derived from the implemented values
of _T_ eff and _L_ _⋆_, and is slightly larger than the value found
by Norris et al. (2012) of 2 _._ 4 _×_ 10 [13] cm (based on our
implemented distance of 59 pc) or that used by Van
de Sande et al. (2018) of 2 _._ 5 _×_ 10 [13] cm, who also used
a lower luminosity than ours of 4500 _L_ _⊙_, whereas our
luminosity value of 6500 _L_ _⊙_ is that found by Maercker
et al. (2016).
The parameterized _β_ -type accelerating wind is described by



_υ_ gas ( _r_ ) = _υ_ 0 + ( _υ_ _∞_ _−_ _υ_ 0 ) 1 _−_ _[r]_ [0]
� _r_



_β_
_,_ (2)
�



where the inner wind velocity _υ_ 0 = 3 km s _[−]_ [1] is set to
the approximate sound speed, _υ_ _∞_ = 5 _._ 7 km s _[−]_ [1] is the
terminal expansion velocity, _r_ 0 = _R_ _⋆_ is the radius at
which the wind is launched, and _β_ = 1 _._ 5. The values
of _υ_ _∞_ and _β_ were derived from an analysis of CO in
R Dor by Maercker et al. (2016). We also include a
constant turbulent velocity of _υ_ turb = 1 km s _[−]_ [1] . The
fractional abundance of AlO and TiO were represented
by a Gaussian profile



� 2 [�]



_f_ ( _r_ ) = _f_ molecule exp



_r_

_−_

� � _r_ _e_



_,_ (3)



centered on the central star, where _f_ molecule is the central abundance and _r_ _e_ is the _e_ -folding radius. For both
molecules, an _e_ -folding radius of 1 _×_ 10 [14] cm was used.
For AlO this is the _e_ -folding radius found by Decin et al.
(2017). For TiO we don’t have any more detailed spatial



_ϵ_
_,_ (1)
�



_T_ gas ( _r_ ) = _T_ eff



_R_ _⋆_
� _r_

14 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten


_̸_



_̸_



_̸_



information, since the emission is unresolved, but we assume a relatively compact distribution that we expect
to be approximately similar to that of AlO.


4.3. _AlO_ _results_


_̸_



_̸_



_̸_



_̸_



The AlO model presented in Decin et al. (2017) was
specifically fit to the _N_ = 9 _→_ 8 line in the ground vibrational state. Using the same model for the newer lines,
we found that the _v_ = 0 lines were reasonably well reproduced, but it was not possible to reproduce the _v_ = 2
line since the Decin et al. (2017) model only included
the ground vibrational state. When choosing how many
vibrationally excited levels needed to be included in our
model, we considered the effect of infrared pumping on
the population of the rotational levels of AlO. Infrared
emission of the central star has a maximum at around
1 _−_ 2 _µ_ m (Van de Sande et al. 2018), which is close to
the term energies of the excited vibrational levels of AlO
between _v_ = 5 and 10. Hence, we included all levels with
_N_ _<_ 20 and _v_ _≤_ 10 as tabulated in ExoMol (Patrascu
et al. 2015; Tennyson et al. 2016). Extending the molecular data in this way resulted in a well-reproduced _v_ = 2
line, while still giving well-reproduced _v_ = 0 lines.
Our best fitting model with the expanded molecular
data described above has _f_ AlO = 1 _._ 7 _×_ 10 _[−]_ [7] when using
collisional rates based on the Dayou & Balan¸ca (2006)
SiO rates (see Sect. A.1 for a more detailed discussion _̸_
of collisional rates). Our modelled lines are plotted on
the observed AlO lines in Fig. 8. As an aide for future
observations, we have plotted in Fig. 9 the calculated
line profiles for the _N_ = 9 _−_ 8 transition in the _v_ = 1
and 3 excited vibrational levels derived from the same

model. This shows the stark difference in width between
transitions in different vibrational states.
The peak abundance we obtained is approximately 3%
of the solar abundance of Al (Asplund et al. 2009). This
is larger than that found by Decin et al. (2017) by a
factor of two. This is most significantly due to the inclusion of the larger molecular dataset, since more levels
are available to be populated and infrared pumping is
able to contribute. The new observations of lines in the

ground vibrational state provided some additional constraints on the model, but the identification of the _v_ = 2
line was also crucial for checking the completeness and
accuracy of our model. In addition to the molecular
data, we also needed to use a smaller inner radius of _R_ _⋆_,
compared with the _∼_ 2 _R_ _⋆_ value used by Decin et al.
(2017), to properly reproduce the _v_ = 2 line.
Although the model discussed above reproduces our
AlO observations well, we investigated the effects of
other factors which might possibly alter our results. In
Sect. A.1 we discuss the effects of different choices of



_̸_



_̸_



_̸_



_̸_



_̸_



_̸_



_̸_



338.10 338.15 338.20 338.25


_̸_



0.000 0.002 0.004 0.006 0.008 0.010


_̸_



Frequency [GHz]


**Figure** **8.** Spectra (black histograms) of rotational transitions of AlO observed towards R Dor, plotted with our
synthetic profiles (red curves). Rotational (and vibrational
for _v_ = _̸_ 0) quantum numbers and extraction aperture radii
are indicated at the top of each box. The narrow feature at
267.871 GHz is the 15 3 _,_ 13 _−_ 15 2 _,_ 14 transition of [34] SO 2, and
the intense line at 338.245 GHz is the 8 _−_ 7 _, v_ = 2 transition
of [29] SiO.



_̸_



_̸_


334.90 334.95 335.00 335.05 335.10


Frequency [GHz]



_̸_


AlO (9-8, v=3), 150 mas



_̸_



_̸_



_̸_



_̸_



_̸_


AlO (9-8, v=1), 150 mas


341.25 341.30 341.35 341.40



_̸_


Frequency [GHz]



_̸_


**Figure** **9.** Synthetic line profiles of the _N_ = 9 _−_ 8 rotational
transition of AlO in the _v_ = 1 and _v_ = 3 excited vibrational

states.


collisional rates. Ultimately, we found that the choice of
collisional rates had a small but generally insignificant
impact on our model results. In Sect. A.2, we discuss
the impact of the choice of spectral extraction aperture
on the final model results. In Sect. A.3 we test the
influence of a disk on our model, such as that found
by Homan et al. (2018). We found that including an
approximation of a disk had some effect on our final re

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 15









|Col1|RDor|Col3|Observed<br>M d l|
|---|---|---|---|
|0.05<br>0.10<br>0.15<br>0.20<br>Flux [Jy]|TiO =1, v=0|oe|oe|
|0.05<br>0.10<br>0.15<br>0.20<br>Flux [Jy]||||


20 10 0 10 20 30

Velocity [km/s]


**Figure** **10.** The _J_ = 11 _−_ 10 rotational transition in the [3] ∆ 1
spin component of TiO in the ground ( _v_ = 0) vibrational
state at 348,159.8 MHz observed towards R Dor (black histograms). A theoretical line profile calculated assuming a
_β_ -velocity law is shown in blue (see text for details).


sults. We also tested the impact of an increased infrared
radiation field on our results. This is discussed in detail
at the end of Sect. 4.4 for TiO. We found that AlO is

not very sensitive to increases in the infrared radiation
field.


4.4. _TiO_ _results_


Analogous with our radiative transfer analysis of AlO,
we assumed that TiO could be described by a Gaussian
distribution centered on the star with the same stellar

and circumstellar parameters as in AlO, including the
same _e_ -folding radius _r_ _e_ = 1 _×_ 10 [14] cm (see Section 4.2.2
and Table 5). When adjusting our model to best reproduce the observations, we did not allow the fractional
abundance of TiO to exceed the solar abundance of Ti
(Ti _/_ H 2 = 1 _._ 8 _×_ 10 _[−]_ [7] ; Asplund et al. 2009). The initial analysis included rotational levels with _J_ _≤_ 20 and
vibrational levels with _v_ _≤_ 5, and the velocity profile
given by Eq. 2. The collisional rates for TiO were derived from the NaCl-He rates for a gas temperature of
700 K (Quintana-Lacaci et al. 2016), scaled for the difference in mass of the TiO-H 2 system (Sch¨oier et al.
2005).
From our first models, it was immediately apparent
that the observed TiO lines are much broader than the

line widths resulting from the velocity profile given in
Eq. 2. A sample line from such a model with _f_ TiO =
1 _._ 8 _×_ 10 _[−]_ [7] is shown in Fig. 10 and the full set of modelled and observed lines is shown in Fig. 16. Although
the peak of the _v_ = 0 model line corresponds well with
the observed peak, the calculated lines are _∼_ 50% of
the observed _v_ = 1 peaks and less than _∼_ 20% of the
_v_ = 2 peaks. We were able to better reproduce the
widths of the observed lines by implementing a constant
expansion velocity of 6 km s _[−]_ [1] in place of the _β_ -velocity
law. However, in this case the peaks of the model lines



significantly under-predicted the observations with the
_v_ = 0 model lines at _∼_ 40% of the observed peaks and
the _v_ _>_ 0 model lines at ≲ 10%. Although it did not
have a significant effect on our AlO model, we tested
the effect of the “overdensity” model from Danilovich
et al. (2020), with an increase in H 2 number density between _∼_ 3 _R_ _⋆_ and 4 _R_ _⋆_ by a factor of 8. This model, with
_f_ TiO = 1 _._ 0 _×_ 10 _[−]_ [7], produced similar line peaks as the initial velocity law model, including under-predicting the
higher- _v_ lines.
For AlO, our modelling could reproduce _v_ = 0 line
when we included a larger number of vibrational states
in our model. However, the vibrational levels included
in the TiO input molecular data for _v_ _≤_ 5 cover a similar extent in energy as those in AlO for _v_ _≤_ 10, so we
did not expect a significant difference when extending
the included levels. Indeed, a test with TiO vibrational
levels up to _v_ _≤_ 10 confirmed this. Aside from vibrationally excited levels, TiO has many low-lying electronically excited states, for which McKemmish et al. (2019)
provides line lists. The two lowest-lying electronic states
are the singlet states _a_ [1] ∆and _d_ [1] Σ [+] whose term energies of 3 _µ_ m and 1 _._ 8 _µ_ m are close to the peak flux of
the central star, and are also close to the term energies of the _v_ = 3 and _v_ = 5 excited vibrational levels
of the ground electronic state (X [3] ∆). We tested models including these two singlet states, and including a
larger complement of excited (singlet and triplet) states:
_X_ [3] ∆, _a_ [1] ∆, _d_ [1] Σ [+], _b_ [1] Π, _E_ [3] Π, _A_ [3] Φ, _B_ [3] Π, _C_ [3] ∆, and
_D_ [3] Σ _[−]_ . We found that including more electronic levels
only caused incremental differences and small improvements in the model, and the model did not adequately
reproduce the vibrationally excited lines. [4] For clarity,
we have included all the discussed models in Table 6.

All the models discussed until now have not taken dust
into account since a significant fraction of the TiO (and
AlO) emission comes from within the dust condensation
radius found by Maercker et al. (2016). Including silicate
dust with their derived opacity (optical depth of 0.05 at
10 _µ_ m, Maercker et al. 2016) did not have a noticeable
effect on the TiO (or AlO) emission. However, there is
evidence of a gravitationally bound dust shell (Khouri
2014) or ring (Khouri et al. 2016) in the innermost regions around R Dor, which may overlap with (or be the
same object as) the rotating disc seen in molecular lines
(Homan et al. 2018). Since the dust has been detected
with infrared observations, we assume it contributes an
additional infrared flux in the region of interest. To


4 Our modelling attempts including excited electronic states may
have been partly hampered by our inability to include collisional
transition rates for those states.

16 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten


**Table** **6.** Parameters in the radiative transfer calculations of TiO in R Dor.


Model designation Electronic states Details


I. _β_ -velocity law _X_ [3] ∆ Parameters from Table 5, _f_ TiO = 1 _._ 8 _×_ 10 _[−]_ [7], gas velocity from

Eq. 2, rotational levels _J_ _≤_ 20, and vibrational levels _v_ _≤_ 5.
II. _υ_ gas = 6 km/s _X_ [3] ∆ As in I, but with a constant outward gas velocity _υ_ gas = 6 km s _[−]_ [1]

III. Overdensity _X_ [3] ∆ As in II, but with the H 2 number density 8 times higher for
_∼_ 3–4 _R_ _⋆_ and _f_ TiO = 1 _._ 0 _×_ 10 _[−]_ [7] .
IV. Singlet states _X_ [3] ∆, _a_ [1] ∆, _d_ [1] Σ [+] As in III.
V. Many excited states _X_ [3] ∆, _a_ [1] ∆, _d_ [1] Σ [+], _b_ [1] Π, _E_ [3] Π, As in III.
_A_ [3] Φ, _B_ [3] Π, _C_ [3] ∆, _D_ [3] Σ _[−]_

VI. Higher IR field _X_ [3] ∆ As in III, but with an additional IR field.
VII. Final model _X_ [3] ∆ As in VI, but with _f_ TiO = 1 _._ 4 _×_ 10 _[−]_ [7] .



approximate this effect, we included an additional infrared radiation field in our model, based on a black
body with a temperature of 1200 K. Although we have
mainly discussed dust as the source of this additional
infrared flux, there are other potential sources. In particular, the disc found by Homan et al. (2018) could be
caused by a stellar or sub-stellar companion, such as a
brown dwarf, which could also be a source of additional
infrared flux. Another possible source is stellar fluctuations due to pulsations of the AGB star itself, especially
if the stellar parameters used are biased towards fainter
phases or epochs. To avoid the problems inherent in
choosing just one of these scenarios, we approximate the
presence of additional infrared flux using a uniform radiation field which does not vary with distance from the
star. This is done using a source function derived from a
black body with a temperature of 1200 K. This allows us
to check the impact of an increased infrared flux, while
leaving a more specific examination of the source of such
flux to future work, since it is beyond the scope of this
present study. With the inclusion of this additional infrared flux, we were finally able to reproduce all the TiO
lines, including those in higher vibrational states. Our
best fit model, which has _f_ TiO = 1 _._ 4 _×_ 10 _[−]_ [7] is shown in
Fig. 11, plotted with the observed spectra. Note that
this model includes levels with _J_ _≤_ 20, _v_ _≤_ 5 and in the
ground electronic state ( _X_ [3] ∆) only. The other models we tested, as detailed in entries I–VI in Table 6 are
plotted in Fig. 16 in the appendix.
For completion, we tested a model including the increased infrared radiation field for AlO and found no
significant difference between that model and the best
model found in Sect. 4.3. This is most likely due to the
significant difference in Einstein A coefficients for vibrational transitions, which are approximately 30 times
larger for TiO than AlO when considering the rotational



levels of interest here. This implies that the radiative
lifetimes of the excited vibrational levels are shorter for

TiO than for AlO, hence a higher infrared flux is needed
to maintain sufficient population of vibrationally excited
TiO molecules in the higher vibrational levels, to compensate for the shorter lifetimes. Conversely, the longer
radiative lifetimes for AlO mean that an increased in
frared flux is not needed to maintain the population
of vibrationally excited AlO molecules, and hence does
not result in a significantly higher amount of radiative
pumping.


5. DISCUSSION AND CONCLUSIONS


5.1. _Our_ _results_ _in_ _context_


Our radiative transfer calculations confirm the importance of infrared radiative pumping on the excitation
of AlO and TiO in the inner wind of R Dor when ob
served at high angular resolution. For AlO, we found
the most important factor was including sufficient vibrationally excited levels to facilitate infrared pumping.
However for TiO, we needed to include a sufficiently high
infrared flux to reproduce lines in the higher vibrational
levels (with _v_ _>_ 0). Such a flux, however, did not have
an effect on our AlO results.
It is apparent from this and prior work on AlO and
TiO in R Dor (see Sects. 3.2 and 4) that a substantial
fraction of both molecules are located in a region close
to the central star — i.e., _∼_ 50% of gaseous AlO is within
the dust condensation radius, and likely a larger fraction
of TiO since we only have spatially unresolved observations. A direct determination of the size of the compact
molecular emission is limited by the angular resolution
in the present observations ( _∼_ 140 mas, or 2.5 times the
stellar diameter _θ_ d ; Decin et al. 2018). As a result, we
can only determine the compact molecular emission is
from a region within _∼_ 70 mas or _∼_ 2 _R_ _⋆_ of the central

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 17























20 0 20



20 0 20





20 0 20















































































Velocity [km/s]



Velocity [km/s]



Velocity [km/s]



**Figure** **11.** The _J_ = 11 _→_ 10 rotational transitions of TiO observed towards R Dor (black histograms) with the vibrational
levels ( _v_ ) and fine structure components (Ω) noted in the top left corner of each plot. Model profiles are overplotted in red and
the vertical dashed grey lines indicate the LSR velocity of 7 km s _[−]_ [1] . Nearby lines are labelled with blue text.

18 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



star ( _R_ _⋆_ _≃_ 30 mas Norris et al. 2012). However, the radiative transfer analysis of the line profiles has yielded
some additional confirmation of the location of AlO and
TiO near and within the dust condensation radius.


5.1.1. _AlO_


Our observations of four successive rotational transi
tions of AlO in the ground vibrational state and one in
the second excited ( _v_ = 2) vibrational level are wellreproduced with our radiative transfer model when we
included an adequate number of vibrationally excited
levels (up to _v_ _≤_ 10, see Sect. 4.3). The model reproduces molecular emission which encompasses the region between the stellar photosphere and the region in
which dust starts to condense and extends beyond the
dust condensation radius (see Sect. 4; Decin et al. 2017;
Danilovich et al. 2016; Danilovich et al. 2020, and references therein).
Our revised fractional abundance of AlO in R Dor
( _f_ 0 = 1 _._ 7 _×_ 10 _[−]_ [7] ) is about 2 times higher than the earlier
estimate by Decin et al. (8 _._ 4 _×_ 10 _[−]_ [8], 2017), but it is still
much lower than the solar abundance of Al (5 _._ 6 _×_ 10 _[−]_ [6],
with respect to H 2 ; Asplund et al. 2009). Hence, this
result does not preclude the possibility of AlO being
incorporated into dust, even in regions overlapping with
our model region.


5.1.2. _TiO_


The line profiles of TiO are wider than expected based
on the assumption of the velocity law given in Eq. 2,
derived from older (less sensitive) single-antenna observations of R Dor (e.g Maercker et al. 2016, who find
_υ_ _∞_ = 5 _._ 7 km s _[−]_ [1] ). Lines wider than the previously determined expansion velocity have been seen for other
molecules observed by ALMA. For example, there are
faint wings either side of the intense emission lines of
CO, SiO, and SO in the ground vibrational state (also
observed in the ALMA spectral line survey of R Dor,
Decin et al. 2018). A more detailed analysis of the SO
emission by Danilovich et al. (2020) found that the SO
lines in the first vibrationally excited state were wider
than the HWHM of the _v_ = 0 lines; that is, rather than
just faint wide wings, the _v_ = 1 lines were overall as
wide as the wings of the _v_ = 0 lines. This was interpreted as emission coming from a rotating disk close to
the central star, such as that reported by Homan et al.
(2018), with a rotational velocity greater than the expansion velocity. In an LTE analysis of four rotational
lines of OH in non-maser emission from high lying rotational lines in R Dor, Khouri et al. (2019) estimated the
FWHM of the OH emission region is about 70 _±_ 20 mas
with possible evidence for line broadening. This is likely
due to the same underlying physical phenomenon. The



adjustments we made to our TiO model of a higher constant velocity and the inclusion of an overdense region
support the rotating disk interpretation. Although the
implemented expansion velocity of 6 km s _[−]_ [1] is unphysical in a region so close to the star [5], it can be thought of
here as a partial 1D approximation of the rotating disk.
The presence of photospheric TiO in M-type stars,
as seen in bands in the optical and infrared regimes, has
long been known and have been used in the spectral classification of these stars (see for example Gray et al. 2009,
and references therein). Hence, it is not unexpected that
we also detect rotational transitions of TiO close to the

surface of the star. However, since our observations are
not spatially resolved, we are unable to properly constrain the extent of the TiO emission, other than it is
within _∼_ 75 mas of the star, based on the ALMA beam
size of _∼_ 150 mas.
Our derived abundance of TiO is 1 _._ 4 _×_ 10 _[−]_ [7] rela
tive to H 2, which is close to the solar abundance of Ti
(1 _._ 8 _×_ 10 _[−]_ [7] Asplund et al. 2009). This does not leave
much Ti for the possible formation of TiO 2 if we assume
that TiO 2 is present in the same region as TiO. Evidence
for the presence of TiO 2 is discussed in the following Section 5.2. Since the TiO we detect is close to the star and

mostly or entirely within the dust condensation radius,
our results do not preclude the incorporation of TiO into
dust grains. In fact, a role in dust formation or growth
would explain the lack of TiO detections further from
the star. It is possible that our apparent high abundance of TiO may rather be attributable to the complex
density and velocity structures before the wind acceleration zone in R Dor, as revealed in recent polarimetric
observations in the optical and near infrared at high angular resolution (Khouri et al. 2016) and predicted in
theoretical dust driven models (H¨ofner et al. 2016, and
references therein).


5.2. _Evidence_ _for_ _gas-phase_ _TiO_ 2 _towards_ _R_ _Dor_


In an earlier survey of R Dor using the APEX telescope, De Beck & Olofsson (2018) found some very
tentative evidence for TiO 2 when stacking 18 lines covered by their frequency range. Using the more sensitive
ALMA telescope, Decin et al. (2018) observed some
possible TiO 2 lines as part of the previously discussed
Band 7 spectral line survey of R Dor (observation ID
2013.1.00166.S). We examined the identified lines in
more detail and determined that several lines are un

5 Unphysical under the condition of a smoothly accelerating wind.
Other causes of line broadening are also possible, in addition to
the rotating disc primarily discussed here, such as infall, expanding shockwaves or standing waves.

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 19









**Figure** **12.** The TiO 2 (26 0 _,_ 26 _→_ 25 1 _,_ 25 ) line at 350.399 GHz
(blue histograms) plotted with the TiO _J_ = 11 _→_ 10, Ω= 1
line in the ground vibrational state (grey dotted line). We
also show the same TiO line scaled down to the same peak
intensity as the TiO 2 line, to allow for a comparison of line
profile shapes. The vertical black dashed line represents the
systemic LSR velocity of 7 km s _[−]_ [1] for R Dor.


certain, in large part due to overlaps with other nearby
lines. In discussing TiO 2 below, we primarily refer to
the more certain identifications of lines that we do not
believe participate in overlaps, and in particular the
following three lines: (26 0 _,_ 26 _→_ 25 1 _,_ 25 ) at 350.399 GHz,
(25 2 _,_ 24 _→_ 24 1 _,_ 23 ) at 350.708 GHz, and (24 2 _,_ 22 _→_ 23 3 _,_ 21 )
at 347.788 GHz, listing in descending order of predicted
intensity. We plot one of these lines, (26 0 _,_ 26 _→_ 25 1 _,_ 25 )
at 350.399 GHz with the TiO _v_ = 0, Ω= 1 line in Fig.
12, showing the TiO line as observed and scaled down
to the same peak flux as the TiO 2 line. The rotational
lines of TiO 2 are 4–5 times less intense than those of
TiO, and the line profile shape may be narrower. However, the low intensity and lower signal to noise ratio
of the TiO 2 lines makes it difficult to conduct any conclusive analysis, since even the brightest lines, such as
that shown in Fig. 12 are only just detected above
the noise. The TiO 2 emission is also unresolved in our
channel maps and zeroth moment maps, supporting the
contention that it is located close to the star. This is

feasible since gaseous TiO 2 is made by the temperature
dependent exothermic reaction


TiO + OH _→_ TiO 2 + H _,_ (4)


which is very fast at the temperatures within a few stellar radii of oxygen rich AGB stars (see Fig. 2 in Plane
2013).
An estimate of the column density of TiO 2, derived
from a single transition in the ground vibrational state
(26 0 _,_ 26 _→_ 25 1 _,_ 25 ) at 350.399 GHz) on the assumption
that the excitation temperature is 1800 K, was comparable to the column density of TiO found in our mod


els. However, this value is very uncertain and does not
conclusively imply that there is a similar abundance of
TiO 2 as TiO (and hence we do not suggest that there is
a higher abundance of Ti in R Dor than in the Sun).
Other related laboratory work concerns the low abundance of TiO 2 in the few presolar grains that have been
analyzed (Stroud et al. 2004; Nittler et al. 2008). However, owing to the limitation of available samples, the sophisticated laboratory instruments used to analyze the
presolar grains from low mass AGB stars might not be
sensitive enough to detect TiO 2 seed crystals if they were
very small (L. Nittler, personal communication).
It has also been noted the abundance of TiO and TiO 2
derived from the rotational spectra in at least one source
(Mira A, see Kami´nski et al. 2017, and discussion in
Sect 1) appears too low to account for the total mass
of the dust in the dust forming region if the dust were
composed of TiO 2 . Yet there is substantial depletion
of Ti in the interstellar medium by about 0.1 or higher
(Jenkins 2009), suggesting TiO 2 might be involved in
dust formation. And as Boulangier et al. (2019) showed,
the number of TiO 2 clusters formed in their chemical
code ( _n_ (TiO 2 ) 1000 _/n_ _H_ _∼_ 10 _[−]_ [11] ) should be sufficient to
drive a wind and still be left with a large abundance of
gaseous TiO 2 /TiO/Ti.
Unfortunately, rotational lines of vibrationally excited
TiO 2 have not been observed in the laboratory, nor in
oxygen-rich AGB or RSG stars (for a more comprehensive look at TiO 2 in VY CMa, see Kami´nski et al.
2013b). This leaves us with few comparisons and little
room to draw any definite conclusions regarding TiO 2 .


5.3. _Dust_ _precursors_ _and_ _dust_ _formation_


Optical and infrared observations of R Dor and
W Hya, another oxygen-rich AGB star with a low massloss rate, established that there are transparent dust
grains within ≲ 2 _R_ _⋆_ of the central star (Norris et al.
2012; Khouri et al. 2016; Ohnaka et al. 2016). The composition of the dust grains has not been conclusively
confirmed, but the present evidence points to alumina
(Al 2 O 3 ) as the probable carrier of spectral features in
the mid IR, as observed at low angular resolution with
ISO SWS (see Khouri 2014; Decin et al. 2017, and references therein). More recently, these and other oxygenrich AGB stars have been observed at much higher angular resolution using mid and near IR interferometry
(Karovicova et al. 2013; Ohnaka et al. 2016), polarimetric interferometry (Norris et al. 2012), and polarimetric
imaging (Khouri et al. 2016; Ohnaka et al. 2016).
There has been a long standing debate about the formation mechanism(s) of solid Al 2 O 3 grains from gas
phase species, and whether it entails a homogenous or

20 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



a heterogenous process. Gail & Sedlmayr (1998, 1999)
concluded — on the assumption of chemical equilibrium
in the gas phase, approximate nucleation theories, and
extrapolation of bulk properties to gas phase clusters —
that a heteromolecular process in which small aluminum
bearing oxides and hydroxides (e.g., AlOH, Al 2 O, and
Al 2 O 2 ) condense on a grain surface and subsequently react to produce the Al 2 O 3 grains appears most probable [6] .
This is because the abundance of gaseous Al 2 O 3 is predicted to be far too low to form solid Al 2 O 3 by homogenous nucleation of gaseous Al 2 O 3 and subsequent condensation on TiO 2 nucleation seeds (Jeong et al. 2003).
There have also been some important advances in supporting laboratory measurements in the past 20 years.
These include measurements of the IR-REMPI spectra
of large gas phase (Al 2 O 3 ) _n_ and (TiO 2 ) _n_ clusters which
provide accurate wavelengths of the vibrational bands
in the IR, and establish Al 2 O 3 and TiO 2 clusters can
form in the gas phase under the specific conditions in
the laboratory (Demyk et al. 2004), but it is uncertain
whether the same conditions apply within a couple of
stellar radii of the low mass oxygen rich AGB stars.
In a recent study, Boulangier et al. (2019) examined
four precursor candidates of the dust with their selfconsistent wind model of oxygen rich AGB stars: TiO 2,
MgO, SiO, and Al 2 O 3 . On the basis of theoretical
quantum chemical calculations, they found there is a
sharp threshold in temperature of 1000–1200 K when
(TiO 2 ) 10 clusters form in their model AGB star; the
abundance of the (TiO 2 ) _n_ clusters is orders of magnitude lower at temperatures greater than 1200 K; Al 2 O 3
clusters are predicted at temperatures as high as 1800–
2400 K; and nearly all the available Al 2 O 3 monomers are
tied up in the clusters at slightly lower temperatures of
1600 _−_ 2200 K. Boulangier et al. (2019) ruled out TiO 2
clusters as nucleation seeds, because the observations

establish the dust exists close to the central star where

the temperatures are as high as 1500 _−_ 2000 K. However the uncertainties in the quantum calculations of
the temperature ranges are difficult to quantify. Also as
they note, their “comprehensive” chemical kinetic code,
which starts with atomic constituents, has several significant shortcomings: it includes a relatively modest
chemical network ( _∼_ 330 reactions) and, although TiO 2
and its clusters are produced, their kinetic code does
not form the Al 2 O 3 monomer or its clusters; AlO 2 and
Al 2 O 2 — the suspected precursors of Al 2 O 3 — are not
produced; and Mg remains in the atomic form and does
not form MgO.



In view of the current understanding of dust formation, further astronomical observations, and accompanying radiative transfer analysis of the suspected gas phase
precursors in the ground and excited vibrational levels
at high angular resolution and sensitivity are needed in
conjunction with: polarimetric observations in the optical and near IR, theoretical calculations, supporting
laboratory measured reaction rates and product distributions, and laboratory measurements of the rotational
spectra of key species in the kinetic models. At present
the relevant astronomical observations are available for

just a couple of specific sources, and there is insufficient
information to determine whether what we see are general trends in these types of sources. For example, it
is unclear whether gravitationally bound dust shells are
prevalent in oxygen rich AGB stars with low mass loss
rates as suspected (H¨ofner & Olofsson 2018), or whether
the Al 2 O 3 dust (and by inference gaseous AlO) and gravitationally bound dust shells are intimately connected in
these objects, or whether TiO 2 are the seeds of the alumina dust.


ACKNOWLEDGMENTS


We are very grateful for helpful discussions on the
molecular physics of TiO by Peter Bernath, elemental depletion by Tom Millar, and presolar grains by
Larry Nittler. We also thank the anonymous referees
for constructive comments. TD acknowledges support
from the Research Foundation Flanders (FWO) through
grant 12N9920N. CAG and KLKL acknowledges partial support from NSF grant AST-1615847. LD acknowledges support from the ERC consolidator grant
646758 AEROSOL and the FWO Research Project
grant G024112N. TK acknowledges funding from grant
no 2018/30/E/ST9/00398 from the Polish National
Science Center. This paper makes use of the following ALMA data: ADS/JAO.ALMA2013.0.00166.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together
with NRC (Canada) and NSC and ASIAA (Taiwan),
in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ. The SMA is a joint project between the
SAO and ASIAA and is funded by the Smithsonian Institution and the Academia Sinica.

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 21


REFERENCES



Andrews, L., Burkholder, T. R., & Yustein, J. T. 1992, The

Journal of Physical Chemistry, 96, 10182,

doi: [10.1021/j100204a018](http://doi.org/10.1021/j100204a018)


Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009,

ARA&A, 47, 481,

doi: [10.1146/annurev.astro.46.060407.145222](http://doi.org/10.1146/annurev.astro.46.060407.145222)


Boulangier, J., Gobrecht, D., Decin, L., de Koter, A., &

Yates, J. 2019, MNRAS, 489, 4890,

doi: [10.1093/mnras/stz2358](http://doi.org/10.1093/mnras/stz2358)


Breier, A. A., Waßmuth, B., Fuchs, G. W., Gauss, J., &

Giesen, T. F. 2019, Journal of Molecular Spectroscopy,

355, 46, doi: [10.1016/j.jms.2018.11.006](http://doi.org/10.1016/j.jms.2018.11.006)


Danilovich, T., De Beck, E., Black, J. H., Olofsson, H., &

Justtanont, K. 2016, A&A, 588, A119,

doi: [10.1051/0004-6361/201527943](http://doi.org/10.1051/0004-6361/201527943)


Danilovich, T., Richards, A. M. S., Decin, L., Van de

Sande, M., & Gottlieb, C. A. 2020, MNRAS, 494, 1323,

doi: [10.1093/mnras/staa693](http://doi.org/10.1093/mnras/staa693)


Dayou, F., & Balan¸ca, C. 2006, A&A, 459, 297,

doi: [10.1051/0004-6361:20065718](http://doi.org/10.1051/0004-6361:20065718)


De Beck, E., & Olofsson, H. 2018, A&A, 615, A8,

doi: [10.1051/0004-6361/201732470](http://doi.org/10.1051/0004-6361/201732470)


De Beck, E., Vlemmings, W., Muller, S., et al. 2015, A&A,

580, A36, doi: [10.1051/0004-6361/201525990](http://doi.org/10.1051/0004-6361/201525990)


Decin, L., Hony, S., de Koter, A., et al. 2006, A&A, 456,

549, doi: [10.1051/0004-6361:20065230](http://doi.org/10.1051/0004-6361:20065230)


Decin, L., Richards, A. M. S., Danilovich, T., Homan, W.,

& Nuth, J. A. 2018, A&A, 615, A28,

doi: [10.1051/0004-6361/201732216](http://doi.org/10.1051/0004-6361/201732216)


Decin, L., Richards, A. M. S., Waters, L. B. F. M., et al.

2017, A&A, 608, A55, doi: [10.1051/0004-6361/201730782](http://doi.org/10.1051/0004-6361/201730782)


Demyk, K., van Heijnsbergen, D., von Helden, G., &

Meijer, G. 2004, A&A, 420, 547,

doi: [10.1051/0004-6361:20034117](http://doi.org/10.1051/0004-6361:20034117)


Gail, H. P., & Sedlmayr, E. 1998, Faraday Discussions, 109,

303, doi: [10.1039/a709290c](http://doi.org/10.1039/a709290c)


—. 1999, A&A, 347, 594


Gobrecht, D., Cherchneff, I., Sarangi, A., Plane, J. M. C.,

& Bromley, S. T. 2016, A&A, 585, A6,

doi: [10.1051/0004-6361/201425363](http://doi.org/10.1051/0004-6361/201425363)


Gonz´alez Delgado, D., Olofsson, H., Kerschbaum, F., et al.

2003, A&A, 411, 123, doi: [10.1051/0004-6361:20031068](http://doi.org/10.1051/0004-6361:20031068)


6 Summarized in Appendix C are the theoretical structures, relative energies, and permanent electric dipole moments of the isomers of Al 2 O, Al 2 O, and Al 2 O 2 whose rotational spectra have
not yet been measured at high resolution in the laboratory or
identified by radio astronomers.



Goto, M., Takano, S., Yamamoto, S., Ito, H., & Saito, S.

1994, Chemical Physics Letters, 227, 287,
doi: [10.1016/0009-2614(94)00820-5](http://doi.org/10.1016/0009-2614(94)00820-5)

Gray, R., Corbally, C., & Burgasser, A. 2009, Stellar

Spectral Classification, Princeton Series in Astrophysics
(Princeton University Press)

H¨ofner, S., Bladh, S., Aringer, B., & Ahuja, R. 2016, A&A,
594, A108, doi: [10.1051/0004-6361/201628424](http://doi.org/10.1051/0004-6361/201628424)

H¨ofner, S., & Olofsson, H. 2018, A&A Rv, 26, 1,

doi: [10.1007/s00159-017-0106-5](http://doi.org/10.1007/s00159-017-0106-5)

Homan, W., Danilovich, T., Decin, L., et al. 2018, A&A,

614, A113, doi: [10.1051/0004-6361/201732246](http://doi.org/10.1051/0004-6361/201732246)

Ito, H., & Goto, M. 1994, Chemical Physics Letters, 227,
293, doi: [https://doi.org/10.1016/0009-2614(94)00821-3](http://doi.org/https://doi.org/10.1016/0009-2614(94)00821-3)

Jenkins, E. B. 2009, ApJ, 700, 1299,

doi: [10.1088/0004-637X/700/2/1299](http://doi.org/10.1088/0004-637X/700/2/1299)

Jeong, K. S., Winters, J. M., Le Bertre, T., & Sedlmayr, E.
2003, A&A, 407, 191, doi: [10.1051/0004-6361:20030693](http://doi.org/10.1051/0004-6361:20030693)

Kami´nski, T. 2019, in IAU Symposium, Vol. 343, IAU

Symposium, ed. F. Kerschbaum, M. Groenewegen, &
H. Olofsson, 108–118, doi: [10.1017/S1743921318006038](http://doi.org/10.1017/S1743921318006038)

Kami´nski, T., Gottlieb, C. A., Young, K. H., Menten,

K. M., & Patel, N. A. 2013a, ApJS, 209, 38,

doi: [10.1088/0067-0049/209/2/38](http://doi.org/10.1088/0067-0049/209/2/38)

Kami´nski, T., Gottlieb, C. A., Menten, K. M., et al. 2013b,

A&A, 551, A113, doi: [10.1051/0004-6361/201220290](http://doi.org/10.1051/0004-6361/201220290)

Kami´nski, T., Wong, K. T., Schmidt, M. R., et al. 2016,
A&A, 592, A42, doi: [10.1051/0004-6361/201628664](http://doi.org/10.1051/0004-6361/201628664)

Kami´nski, T., M¨uller, H. S. P., Schmidt, M. R., et al. 2017,

A&A, 599, A59, doi: [10.1051/0004-6361/201629838](http://doi.org/10.1051/0004-6361/201629838)

Karovicova, I., Wittkowski, M., Ohnaka, K., et al. 2013,

A&A, 560, A75, doi: [10.1051/0004-6361/201322376](http://doi.org/10.1051/0004-6361/201322376)

Khouri, T. 2014, PhD thesis, Univeristy of Amsterdam

Khouri, T., Velilla-Prieto, L., De Beck, E., et al. 2019,

A&A, 623, L1, doi: [10.1051/0004-6361/201935049](http://doi.org/10.1051/0004-6361/201935049)

Khouri, T., Vlemmings, W. H. T., Olofsson, H., et al. 2018,
A&A, 620, A75, doi: [10.1051/0004-6361/201833643](http://doi.org/10.1051/0004-6361/201833643)

Khouri, T., Waters, L. B. F. M., de Koter, A., et al. 2015,

A&A, 577, A114, doi: [10.1051/0004-6361/201425092](http://doi.org/10.1051/0004-6361/201425092)

Khouri, T., Maercker, M., Waters, L. B. F. M., et al. 2016,

A&A, 591, A70, doi: [10.1051/0004-6361/201628435](http://doi.org/10.1051/0004-6361/201628435)

Knapp, G. R., Pourbaix, D., Platais, I., & Jorissen, A.

2003, A&A, 403, 993, doi: [10.1051/0004-6361:20030429](http://doi.org/10.1051/0004-6361:20030429)

Launila, O., & Banerjee, D. P. K. 2009, A&A, 508, 1067,
doi: [10.1051/0004-6361/200913274](http://doi.org/10.1051/0004-6361/200913274)

Launila, O., & Berg, L. E. 2011, Journal of Molecular
Spectroscopy, 265, 10, doi: [10.1016/j.jms.2010.10.005](http://doi.org/10.1016/j.jms.2010.10.005)

Launila, O., & Jonsson, J. 1994, Journal of Molecular

Spectroscopy, 168, 1, doi: [10.1006/jmsp.1994.1257](http://doi.org/10.1006/jmsp.1994.1257)

22 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten



Levesque, E. M. 2017, Astrophysics of Red Supergiants


(IOP Publishing), doi: [10.1088/978-0-7503-1329-2](http://doi.org/10.1088/978-0-7503-1329-2)


Lovas, F. J., & Tiemann, E. 1974, Journal of Physical and


Chemical Reference Data, 3, 609


Maercker, M., Danilovich, T., Olofsson, H., et al. 2016,


A&A, 591, A44, doi: [10.1051/0004-6361/201628310](http://doi.org/10.1051/0004-6361/201628310)


Maercker, M., Sch¨oier, F. L., Olofsson, H., Bergman, P., &


Ramstedt, S. 2008, A&A, 479, 779,


doi: [10.1051/0004-6361:20078680](http://doi.org/10.1051/0004-6361:20078680)


McKemmish, L. K., Masseron, T., Hoeijmakers, H. J., et al.


2019, MNRAS, 488, 2836, doi: [10.1093/mnras/stz1818](http://doi.org/10.1093/mnras/stz1818)


Namiki, K.-i., Saito, S., Robinson, J. S., & Steimle, T. C.


1998, Journal of Molecular Spectroscopy, 191, 176,


doi: [10.1006/jmsp.1998.7634](http://doi.org/10.1006/jmsp.1998.7634)


Nittler, L. R., Alexander, C. M. O., Gallino, R., et al. 2008,


ApJ, 682, 1450, doi: [10.1086/589430](http://doi.org/10.1086/589430)


Norris, B. R. M., Tuthill, P. G., Ireland, M. J., et al. 2012,


Nature, 484, 220, doi: [10.1038/nature10935](http://doi.org/10.1038/nature10935)


Ohnaka, K., Weigelt, G., & Hofmann, K. H. 2016, A&A,


589, A91, doi: [10.1051/0004-6361/201628229](http://doi.org/10.1051/0004-6361/201628229)


Patrascu, A. T., Yurchenko, S. N., & Tennyson, J. 2015,


MNRAS, 449, 3613, doi: [10.1093/mnras/stv507](http://doi.org/10.1093/mnras/stv507)


Plane, J. M. C. 2013, Philosophical Transactions of the


Royal Society of London Series A, 371, 20120335,


doi: [10.1098/rsta.2012.0335](http://doi.org/10.1098/rsta.2012.0335)



Quintana-Lacaci, G., Cernicharo, J., Ag´undez, M., et al.
2016, ApJ, 818, 192, doi: [10.3847/0004-637X/818/2/192](http://doi.org/10.3847/0004-637X/818/2/192)

Ram, R. S., Bernath, P. F., Dulick, M., & Wallace, L. 1999,

ApJS, 122, 331, doi: [10.1086/313212](http://doi.org/10.1086/313212)

Rybicki, G. B., & Hummer, D. G. 1991, A&A, 245, 171

Sch¨oier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., &

Black, J. H. 2005, A&A, 432, 369,

doi: [10.1051/0004-6361:20041729](http://doi.org/10.1051/0004-6361:20041729)

Snyder, L. E., Lovas, F. J., Hollis, J. M., et al. 2005, ApJ,
619, 914, doi: [10.1086/426677](http://doi.org/10.1086/426677)

Steimle, T. C., & Virgo, W. 2003, Chemical Physics
Letters, 381, 30, doi: [10.1016/j.cplett.2003.09.102](http://doi.org/10.1016/j.cplett.2003.09.102)

Stroud, R. M., Nittler, L. R., & Alexander, C. M. O. 2004,

Science, 305, 1455, doi: [10.1126/science.1101099](http://doi.org/10.1126/science.1101099)

Takigawa, A., Kamizuka, T., Tachibana, S., & Yamamura,
I. 2017, Science Advances, 3, doi: [10.1126/sciadv.aao2149](http://doi.org/10.1126/sciadv.aao2149)

Tenenbaum, E. D., & Ziurys, L. M. 2009, ApJL, 694, L59,
doi: [10.1088/0004-637X/694/1/L59](http://doi.org/10.1088/0004-637X/694/1/L59)

Tennyson, J., Yurchenko, S. N., Al-Refaie, A. F., et al.

2016, Journal of Molecular Spectroscopy, 327, 73,
doi: [10.1016/j.jms.2016.05.002](http://doi.org/10.1016/j.jms.2016.05.002)

Van de Sande, M., Decin, L., Lombaert, R., et al. 2018,

A&A, 609, A63, doi: [10.1051/0004-6361/201731298](http://doi.org/10.1051/0004-6361/201731298)


Yamada, C., Cohen, E. A., Fujitake, M., & Hirota, E. 1990,

The Journal of Chemical Physics, 92, 2146,
doi: [10.1063/1.458005](http://doi.org/10.1063/1.458005)

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 23


APPENDIX


A. FURTHER DETAILED INVESTIGATION OF AlO MODELLING



A.1. _Choice_ _of_ _collisional_ _rates_ _for_ _AlO_


Since the cross sections for collisions between AlO and H 2 have not been measured or calculated, we tested the
dependence of our radiative transfer model on the choice of collisional rates. We implemented collisional rates calculated
for two other molecular systems: (1) SiO colliding with He which only includes levels in the ground vibrational state
(Dayou & Balan¸ca 2006); and (2) NaCl with He which includes rotational levels in the ground and vibrationally excited
states, and ro-vibrational collisional transitions (Quintana-Lacaci et al. 2016). In both systems, the collisional rates
were scaled for the difference in mass with that of AlO–H 2 (Sch¨oier et al. 2005).
To test the influence of the collisional excitation rates on the solutions to the statistical equations in the radiative
transfer analysis, we also ran models with (3) the collision rates adapted from the NaCl rates multiplied by 100, and
(4) all the collision rates set to zero. To compare the dependence of the models on the different collisional rates, we
first determined the best fitting model with the collisional rates adapted from the SiO rates ( _f_ AlO = 1 _._ 7 _×_ 10 _[−]_ [7] ), and
then used the same AlO abundance profile to run models with the other sets of collisional rates. Plotted in Fig. 13
are all the calculated line profiles superposed on the observed spectra.
The difference between the calculated lines profiles and the observed lines for the different sets of collisional rates
was negligible in the ground vibrational state and was small for the line in the excited _v_ = 2 level. The most
significant departure was for the model with the collisions adapted from NaCl multiplied by 100, which resulted in
only a minor difference for the _v_ = 0 lines, but produced a profile for the _v_ = 2 line that was 30% less intense than
the corresponding line calculated for NaCl collisions cross sections that were not multiplied by 100. The model which
neglected collisional excitation predicted slightly brighter lines for all observed transitions than the models for which
collisions were considered.





































**Figure** **13.** Spectra (black histograms) of four successive rotational transitions of AlO in the ground vibrational state and
one transition in the second excited ( _v_ = 2) level observed towards R Dor; and synthetic profiles (coloured curves). Rotational
quantum numbers and the extraction aperture radii are indicated at the top of each box.


A.2. _Impact_ _of_ _the_ _south-eastern_ _extension_ _in_ _AlO_ _emission_



When selecting spectra to use to constrain our 1D radiative transfer models of R Dor, we selected AlO spectra
extracted for a 150 mas radius aperture. This is in contrast with the 300 mas aperture spectra selected for TiO, which

24 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten


were chosen to capture the maximum amount of TiO flux, without being dominated by noise. In the case of AlO,
a smaller aperture was selected to avoid including the SE extension seen in the zeroth moment maps of Fig 3. The
extension breaks spherical symmetry and hence cannot be reproduced by a 1D model.
To emphasise the impact the SE extension and our choice of aperture, we plot in Fig. 14 the same model as shown
in Fig. 8 but for a spectral extraction aperture of 300 mas. The differences between Figures 8 and 14 clearly show
the impact of the SE extension: the ground state lines of (9 _→_ 8) and (8 _→_ 7) are slightly under-predicted when
additional emission from the SE extension is included in the observed spectra; and the (7 _→_ 6) and (6 _→_ 5) lines
are less over-predicted for the same reason. In addition, the 150 mas extraction of the (6 _→_ 5) is strongly affected
by resolved-out flux, which is a less prominent problem for the 300 mas aperture spectrum, since the latter is more
strongly dominated by noise.

































338.1 338.2
Frequency [GHz]



0.000 0.002 0.004 0.006 0.008 0.010



**Figure** **14.** Spectra (black histograms) of four successive rotational transitions of AlO in the ground vibrational state and one
transition in the second excited ( _v_ = 2) level observed towards R Dor; and synthetic profiles (red curves) calculated with our
best radiative transfer model. Data and models are shown for a spectral extraction aperture radius of _∼_ 300 mas.


A.3. _The_ _effects_ _of_ _a_ _disk_



In addition to investigating the impact of the particular set of collisional rates adopted, we checked the effect of a
possible disk in the inner regions of R Dor (see Homan et al. 2018) on our radiative transfer analysis of AlO. Because
our model is 1-dimensional and cannot fully reproduce a disk, we referred to the spherically symmetric approximations
implemented by Danilovich et al. (2020) in their analysis of SO around the same star. Specifically, we tested the effect
of their “overdensity” model in which the H 2 number density between _∼_ 3 _R_ _⋆_ and 4 _R_ _⋆_ was increased by a factor of 8.
Due to the overlap between this overdensity region and the region where AlO is primarily observed, the new model
does result in brighter AlO line profiles. Using this overdensity model, we adjusted our AlO abundance until we were
able to once again reproduce the observed lines. From this we found a new best fit model with _f_ AlO = 7 _×_ 10 _[−]_ [8] relative
to H 2 . This is more than a factor of two lower than our original model that does not include an overdense region.


A.4. _Widths_ _of_ _hyperfine_ _components_



In addition to the above, we tested the effect of the assumed widths of the theoretical Gaussian profiles representing
the unresolved hyperfine components of the very broad AlO lines. In general, smaller assumed widths resulted in
calculated line profiles in which the underlying hyperfine structure is more noticeable, while larger widths resulted in
smoother line profile shapes. Although we present our final model with HWHM widths set to 3 km s _[−]_ [1], we tested
different HWHM widths for all the lines. We found the theoretical line profiles which yielded the best fits were 3 km s _[−]_ [1]

for the _N_ = 9 _→_ 8 and 8 _→_ 7 lines, and 4.5 km s _[−]_ [1] for the 7 _→_ 6 line. The 6 _→_ 5 line is omitted from this analysis

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 25


due to lower data quality, but generally appears to correspond better with a larger HWHM. The tightest observational
constraints were found for the _N_ = 9 _→_ 8 and 7 _→_ 6 transitions in the ground vibrational state, where wider Gaussian
components produced a smoother line profile than was observed for the 9 _→_ 8 line, and narrower components produced
a jagged line profile that did not reproduce the 7 _→_ 6 line well. As shown in Fig. 15, the profile constructed from the
5.7 km s _[−]_ [1] hyperfine components does not reproduce the hyperfine structure observed with ALMA for the 9 _→_ 8 line,
whereas the the profile constructed from 3 km s _[−]_ [1] hyperfine components (also shown in Fig. 8 for all lines) is more
jagged than the observed 7 _→_ 6 profile.
The good agreement between most of the observed and synthetic line profiles for the 3 km s _[−]_ [1] hyperfine components
is part of the reason this value was chosen for the final model. However, we cannot easily explain why the 7 _→_ 6
line has smoother or less distinct hyperfine components. One possible explanation is that, as a lower-energy line, it is
formed further out in the envelope. However, the zeroth moment map of the emission (see Fig. 3) and the emission
extents predicted by our (spherically symmetric) radiative transfer model do not support this hypothesis. (Note that
the apparent larger size of the emission shown in Fig. 3 is mainly due to differences in sensitivity between the 7 _→_ 6
and 8 _→_ 7 observations.) Our radiative transfer model cannot account for non-spherically symmetric features, so it is
possible the 7 _→_ 6 line is excited more in (the faster rotating portion of) the disc than the other transitions. This is
not something we can check with our current level of observations, however.

















3 km/s 5.7 km/s


**Figure** **15.** Synthetic line profiles for two transitions of AlO towards R Dor calculated using two different HWHM (3 km s _[−]_ [1]

and 5.7 km s _[−]_ [1] ) for the Gaussians representing the hyperfine components. These curves are plotted over the observed line
profiles, which are shown as green histograms.


B. FURTHER DETAILS OF TESTED TiO MODELS


In Fig. 16 we plot the TiO models discussed in Sect. 4.4 and tabulated in entries I–VI of Table 6. Our final TiO
model, entry VII in Table 6, is not included here and can instead be seen in Fig. 11.


C. THEORETICAL STRUCTURES OF SMALL ALUMINUM OXIDES


There has been some confusion in the astronomical literature regarding the structures of the most stable forms of
the small aluminum oxides, owing to earlier calculations in the chemical literature at low levels of theory. Presented
here are couple cluster theory calculations of three aluminum oxides frequently cited as possible precursors of Al 2 O 3 :
Al 2 O (Fig. 17), AlO 2 (Fig. 18), and Al 2 O 2 (Fig. 19).


C.1. _Al_ _2_ _O_


There are three possible arrangements of the nuclei in Al 2 O (a _C_ 2 _v_ form like H 2 O, a _D_ _∞h_ form like CO 2, and a
_C_ _∞v_ form Al–Al–O), and two possible electron spin multiplicities (singlet and triplet). Summarized in Figure 17 are
the calculated structures, permanent electric dipole moments, and relative energies at the ae-CCSD(T)/cc-pWCVTZ
level of theory, where the zero-point energy was estimated with a smaller basis (cc-pWCVDZ).
The Al 2 O isomers with triplet multiplicity are at least 33,000 K or higher in energy than the singlet structures.
Singlet Al–O–Al is the most stable isomer and is probably the most abundant isomer in the inner wind of oxygen
rich AGB stars, but it is nonpolar and the rotational spectrum is unobservable with radio telescopes. Two of the

26 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten





















20 0 20



20 0 20





20 0 20





















































































Velocity [km/s]



Velocity [km/s]



Velocity [km/s]



**Figure** **16.** The _J_ = 11 _−_ 10 rotational transitions of TiO observed towards R Dor (black histograms) with the vibrational
levels ( _v_ ) and fine structure components (Ω) noted in the top left corner of each plot. Model profiles are overplotted in red and
the vertical dashed grey lines indicate the LSR velocity of 7 km s _[−]_ [1] . Nearby lines are labelled with red text.

Rotational spectra of vibrationally excited AlO and TiO in oxygen rich stars 27


remaining three isomers possess large dipole moments and have structures with _C_ _∞v_ symmetry — one is a singlet and
the other is a triplet. The triplet _C_ 2 _v_ form is calculated to be the lowest energy polar form of Al 2 O, although it might
prove difficult to detect because it possesses a small dipole moment (0.8 D), and it is nearly degenerate (to within
_∼_ 2500 K) with the _D_ _∞h_ structure. Depending on how well the relative energies are determined, the _D_ _∞h_ structure
might undergo thermal interconversion between the polar and nonpolar forms in the hot inner wind close to the central
star, and therefore warrants a more sophisticated quantum chemical treatment.


**Figure** **17.** Relative energies and dipole moments of the isomers of Al 2 O.


C.2. _AlO_ _2_


To assess whether the rotational spectrum of AlO 2 (all with doublet electron spin multiplicity) might be detectable with radio telescopes, we calculated the electronic and zero-point energy, and the dipole moments at the
ae-CCSD(T)/cc-pWCVTZ level of theory (Figure 18). The most stable isomer is the nonpolar _D_ _∞h_ structure, followed by the isomer with _C_ 2 _v_ symmetry, and a linear _C_ _∞v_ isomer. The dipole moments of the polar isomers are
modest, perhaps indicating their detection in the inner wind of oxygen rich AGB stars might be difficult. The calculated quadrupole coupling constant ( _eQq_ ) of _−_ 20 _._ 9 MHz for the _C_ 2 _v_ isomer and _−_ 26 _._ 6 MHz for the _C_ _∞v_ isomer are
similar to that of AlO ( _eQq_ = _−_ 26 _._ 1 _±_ 0 _._ 21 MHz; Goto et al. 1994), implying the Al—O bonding character is very
similar in AlO and AlO 2 .


C.3. _AlOAlO_


Linear AlOAlO (see Fig. 19) is an attractive candidate for astronomical detection in oxygen rich stars. It has
been observed at IR wavelengths trapped in an inert matrix (Andrews et al. 1992), and the permanent electric dipole
moment is large (5.16 D; S. Thorwirth, personal communication). Owing to its rigid linear geometry, the rotational
spectrum of AlOAlO consists of a single series of harmonically related rotational transitions spaced every 3.4 GHz

apart.

28 Danilovich, Gottlieb, Decin, Richards, Lee, Kaminski, Patel, Young and Menten


**Figure** **18.** Relative energies and dipole moments of three isomers of AlO 2 with electron spin multiplicity of 2.


**Figure** **19.** The two most stable isomers of Al 2 O 2 . The linear AlOAlO isomer is estimated to be 1,500 K higher in energy
than the most stable (cyclic) isomer of Al 2 O 2, but the rotational spectrum of the symmetric cyclic isomer is not observable.


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: observational_alma_primary",
  "failed_quote": "In addition to these previously published data, we have obtained some new observations using ALMA, in a search for the N = 6 -> 5 through N = 8 -> 7 rotational transitions in the ground vibrational state."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "59 pc",
  "failed_quote": "This is slightly red-shifted from the v_LSR = 7.0 +- 0.5 km s^-1 of R Dor (Danilovich et al. 2016)."
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "Knapp et al. 2003",
  "failed_quote": "This is slightly red-shifted from the v_LSR = 7.0 +- 0.5 km s^-1 of R Dor (Danilovich et al. 2016)."
 },
 {
  "path": "science.targets[1].redshift_or_distance.evidence[0]",
  "value": "v_LSR = 34 +- 1 km s^-1",
  "failed_quote": "This is offset from the v_LSR = 34 +- 1 km s^-1 of IK Tau (Decin et al. 2018) by 1.6 km s^-1 towards the blue, and could also be due to as-yet unknown inner wind dynamics."
 },
 {
  "path": "science.targets[1].distance_source.evidence[0]",
  "value": "Decin et al. (2018)",
  "failed_quote": "This is offset from the v_LSR = 34 +- 1 km s^-1 of IK Tau (Decin et al. 2018) by 1.6 km s^-1 towards the blue, and could also be due to as-yet unknown inner wind dynamics."
 },
 {
  "path": "science.targets[2].redshift_or_distance.evidence[0]",
  "value": "v_LSR = 22 km s^-1",
  "failed_quote": "The mean central LSR velocity v_LSR = 21.5 +- 3.3 km s^-1 for the four rotational transitions in the excited vibrational levels of AlO in Table 1 is in good agreement with the stellar velocity (v_LSR = 22 km s^-1, Kaminski et al. 2013a)"
 },
 {
  "path": "science.targets[2].distance_source.evidence[0]",
  "value": "Kaminski et al. 2013a",
  "failed_quote": "The mean central LSR velocity v_LSR = 21.5 +- 3.3 km s^-1 for the four rotational transitions in the excited vibrational levels of AlO in Table 1 is in good agreement with the stellar velocity (v_LSR = 22 km s^-1, Kaminski et al. 2013a)"
 },
 {
  "path": "data.alma_project_codes[0].evidence[0]",
  "value": "2017.1.00824.S",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.alma_project_codes[1].evidence[0]",
  "value": "2017.A.00012.S",
  "failed_quote": "AlO N = 8 -> 7 306.197 2017.A.00012.S 20181211 6.5 0.9 110, 88, -45 0.911 3.8 3.1"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "229.670 GHz (0.32 km s^-1), 267.937 GHz (0.273 km s^-1), 306.197 GHz (0.911 km s^-1), 338.167-355.623 GHz (0.8-1.7 km s^-1); 335-362 GHz survey",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[1]",
  "value": "229.670 GHz (0.32 km s^-1), 267.937 GHz (0.273 km s^-1), 306.197 GHz (0.911 km s^-1), 338.167-355.623 GHz (0.8-1.7 km s^-1); 335-362 GHz survey",
  "failed_quote": "AlO N = 7 -> 6 267.937 2017.1.00824.S 20171231- 165 1.2 138,131, -55 0.273 1.0 5.0"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[2]",
  "value": "229.670 GHz (0.32 km s^-1), 267.937 GHz (0.273 km s^-1), 306.197 GHz (0.911 km s^-1), 338.167-355.623 GHz (0.8-1.7 km s^-1); 335-362 GHz survey",
  "failed_quote": "AlO N = 9 -> 8 338.167- 2013.1.00166.S 20150827- 25.2 0.3- 165, 127, +29 0.9- 3.5- 3.1"
 },
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "AlO",
  "failed_quote": "0 6 -> 5 229,670.239 ... ... ... ... ... ..."
 },
 {
  "path": "data.lines_targeted[1].evidence[0]",
  "value": "AlO",
  "failed_quote": "0 7 -> 6 267,936.560 267,932.6 +- 5.4 4.4 19 +- 3 73 150 775 +- 23"
 },
 {
  "path": "data.lines_targeted[2].evidence[0]",
  "value": "AlO",
  "failed_quote": "0 8 -> 7 306,197.319 306,191 +- 12 5.4 50 +- 6 68 150 1986 +- 90"
 },
 {
  "path": "data.lines_targeted[3].evidence[0]",
  "value": "AlO",
  "failed_quote": "1 303,412.064 303,390.0 +- 0.6 477 17.5 +- 1.5 21.8 +- 0.6 0.91 8.9 +- 0.9 3.1 +- 0.3"
 },
 {
  "path": "data.lines_targeted[4].evidence[0]",
  "value": "AlO",
  "failed_quote": "2 300,611.392 300,591.0 +- 3.0 340 41.0 +- 7.2 20.3 +- 3.0 0.92 7.7 +- 1.6 1.3 +- 0.2"
 },
 {
  "path": "data.lines_targeted[5].evidence[0]",
  "value": "AlO",
  "failed_quote": "0 9 -> 8 344,451.721 344,445.1 +- 1.5 5.8 87 +- 12 51.0 150 3133 +- 75"
 },
 {
  "path": "data.lines_targeted[6].evidence[0]",
  "value": "AlO",
  "failed_quote": "1 341,318.153 341,294.6 +- 0.6 661 12.6 +- 1.1 20.7 +- 0.5 0.82 12.5 +- 1.1 3.6 +- 0.3"
 },
 {
  "path": "data.lines_targeted[7].evidence[0]",
  "value": "AlO",
  "failed_quote": "2 9 -> 8 338,167.232 338,156 +- 12 10.3 22 +- 5 29.7 150 612 +- 14"
 },
 {
  "path": "data.lines_targeted[8].evidence[0]",
  "value": "TiO",
  "failed_quote": "1 0 348,159.8 348,150.75 +- 0.22 7.8 221 +- 9 9.4 +- 0.4 300 2,077 +- 122"
 },
 {
  "path": "data.lines_targeted[9].evidence[0]",
  "value": "TiO",
  "failed_quote": "1 346,198.2 346,188.8 +- 0.4 8.1 91 +- 7 8.8 +- 0.9 300 804 +- 103"
 },
 {
  "path": "data.lines_targeted[10].evidence[0]",
  "value": "TiO",
  "failed_quote": "2 344,224.3 344,225 +- 3.1 7.5 44 +- 4 8.2 +- 0.9 300 377 +- 13"
 },
 {
  "path": "data.lines_targeted[11].evidence[0]",
  "value": "TiO",
  "failed_quote": "3 342,239.0 ... ... ... ... 300 ..."
 },
 {
  "path": "data.lines_targeted[12].evidence[0]",
  "value": "TiO",
  "failed_quote": "2 0 352,157.6 352,148.18 +- 0.25 8.0 184 +- 8 9.4 +- 0.5 300 1,739 +- 119"
 },
 {
  "path": "data.lines_targeted[13].evidence[0]",
  "value": "TiO",
  "failed_quote": "1 350,147.5 350,138.9 +- 0.4 7.4 88 +- 7 9.1 +- 0.9 300 799 +- 101"
 },
 {
  "path": "data.lines_targeted[14].evidence[0]",
  "value": "TiO",
  "failed_quote": "2 348,125.8 (348,112.1 +- 0.17) ... (73 +- 16) (12.9 +- 0.3) 300 (943)"
 },
 {
  "path": "data.lines_targeted[15].evidence[0]",
  "value": "TiO",
  "failed_quote": "3 346,090.1 ... ... 12 +- 1 8.7 +- 5.2 300 ..."
 },
 {
  "path": "data.lines_targeted[16].evidence[0]",
  "value": "TiO",
  "failed_quote": "3 0 355,623.3 355,614.38 +- 0.26 7.5 208 +- 8 11.0 +- 0.5 300 2,297 +- 137"
 },
 {
  "path": "data.lines_targeted[17].evidence[0]",
  "value": "TiO",
  "failed_quote": "1 353,573.4 353,575.2 +- 0.7 8.5 75 +- 11 8.4 +- 1.4 300 630 +- 140"
 },
 {
  "path": "data.lines_targeted[18].evidence[0]",
  "value": "TiO",
  "failed_quote": "2 351,511.2 351,502.5 +- 1.5 7.5 51 +- 14 7.7 +- 2.4 300 391 +- 127"
 },
 {
  "path": "data.lines_targeted[19].evidence[0]",
  "value": "TiO",
  "failed_quote": "3 349,436.5 ... ... 14 +- 1 17.2 +- 3.4 300 ..."
 },
 {
  "path": "data.lines_targeted[20].evidence[0]",
  "value": "TiO2",
  "failed_quote": "in particular the following three lines: (26_0,26 -> 25_1,25) at 350.399 GHz, (25_2,24 -> 24_1,23) at 350.708 GHz, and (24_2,22 -> 23_3,21) at 347.788 GHz"
 },
 {
  "path": "data.lines_targeted[21].evidence[0]",
  "value": "TiO2",
  "failed_quote": "in particular the following three lines: (26_0,26 -> 25_1,25) at 350.399 GHz, (25_2,24 -> 24_1,23) at 350.708 GHz, and (24_2,22 -> 23_3,21) at 347.788 GHz"
 },
 {
  "path": "data.lines_targeted[22].evidence[0]",
  "value": "TiO2",
  "failed_quote": "in particular the following three lines: (26_0,26 -> 25_1,25) at 350.399 GHz, (25_2,24 -> 24_1,23) at 350.708 GHz, and (24_2,22 -> 23_3,21) at 347.788 GHz"
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "33 x 29 mas to 165 x 127 mas (R Dor); 175 x 145 mas to 165 x 135 mas (IK Tau)",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "33 x 29 mas to 165 x 127 mas (R Dor); 175 x 145 mas to 165 x 135 mas (IK Tau)",
  "failed_quote": "AlO N = 9 -> 8 338.167- 2013.1.00166.S 20150827- 25.2 0.3- 165, 127, +29 0.9- 3.5- 3.1"
 },
 {
  "path": "data.angular_resolution.evidence[2]",
  "value": "33 x 29 mas to 165 x 127 mas (R Dor); 175 x 145 mas to 165 x 135 mas (IK Tau)",
  "failed_quote": "AlO N = 9 -> 8 338.167- 2013.1.00166.S 20150813- 10 0.2- 175, 145, -15 1.7- 4.7- 3.1"
 },
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "2.6 to 5.0 arcsec (R Dor); 3.1 arcsec (IK Tau)",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.max_recoverable_scale.evidence[1]",
  "value": "2.6 to 5.0 arcsec (R Dor); 3.1 arcsec (IK Tau)",
  "failed_quote": "AlO N = 7 -> 6 267.937 2017.1.00824.S 20171231- 165 1.2 138,131, -55 0.273 1.0 5.0"
 },
 {
  "path": "data.max_recoverable_scale.evidence[2]",
  "value": "2.6 to 5.0 arcsec (R Dor); 3.1 arcsec (IK Tau)",
  "failed_quote": "AlO N = 9 -> 8 338.167- 2013.1.00166.S 20150813- 10 0.2- 175, 145, -15 1.7- 4.7- 3.1"
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "0.8 to 4.5 mJy per channel (R Dor); 4.7 to 5.3 mJy per channel (IK Tau)",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.time_on_source.evidence[0]",
  "value": "192 min, 165 min, 6.5 min, 25.2 min (R Dor); 10 min (IK Tau)",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.time_on_source.evidence[1]",
  "value": "192 min, 165 min, 6.5 min, 25.2 min (R Dor); 10 min (IK Tau)",
  "failed_quote": "AlO N = 7 -> 6 267.937 2017.1.00824.S 20171231- 165 1.2 138,131, -55 0.273 1.0 5.0"
 },
 {
  "path": "data.time_on_source.evidence[2]",
  "value": "192 min, 165 min, 6.5 min, 25.2 min (R Dor); 10 min (IK Tau)",
  "failed_quote": "AlO N = 8 -> 7 306.197 2017.A.00012.S 20181211 6.5 0.9 110, 88, -45 0.911 3.8 3.1"
 },
 {
  "path": "data.observing_dates.evidence[0]",
  "value": "20150813-20150828, 20150827-20150901, 20171024-20171026, 20171231-20180105, 20181211",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "data.observing_dates.evidence[1]",
  "value": "20150813-20150828, 20150827-20150901, 20171024-20171026, 20171231-20180105, 20181211",
  "failed_quote": "AlO N = 7 -> 6 267.937 2017.1.00824.S 20171231- 165 1.2 138,131, -55 0.273 1.0 5.0"
 },
 {
  "path": "data.observing_dates.evidence[2]",
  "value": "20150813-20150828, 20150827-20150901, 20171024-20171026, 20171231-20180105, 20181211",
  "failed_quote": "AlO N = 8 -> 7 306.197 2017.A.00012.S 20181211 6.5 0.9 110, 88, -45 0.911 3.8 3.1"
 },
 {
  "path": "data.pi_or_archival_as_stated.evidence[1]",
  "value": "Combination of previously published data (2013.1.00166.S) and new ALMA observations (2017.1.00824.S, 2017.A.00012.S)",
  "failed_quote": "In addition to these previously published data, we have obtained some new observations using ALMA, in a search for the N = 6 -> 5 through N = 8 -> 7 rotational transitions in the ground vibrational state."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Peak and integrated flux values of the AlO N = 9 -> 8, v = 0 line for IK Tau",
  "failed_quote": "The peak and integrated flux values of the N = 9 -> 8, v = 0 line for IK Tau were taken from Decin et al. (2017)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Einstein A coefficients and partition functions for AlO",
  "failed_quote": "The partition function (Z) includes all the rotational-vibrational levels with all the appropriate degeneracy factors in the comprehensive analysis of Patrascu et al. (2015)."
 },
 {
  "path": "data.external_data_from_literature[5].what.evidence[1]",
  "value": "Solar abundances of Al and Ti",
  "failed_quote": "When adjusting our model to best reproduce the observations, we did not allow the fractional abundance of TiO to exceed the solar abundance of Ti (Ti/H2 = 1.8 x 10^-7; Asplund et al. 2009)."
 },
 {
  "path": "processing.calibration.flux_scale_uncertainty.evidence[0]",
  "value": "7% or better in most cases; 12% upper bound for AlO N = 6 -> 5",
  "failed_quote": "The flux scale is in most cases accurate to 7% or better; however, for AlO N = 6 -> 5 the phase reference source flux density fluctuated by 12% over the observations"
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "33 x 29 mas (+55 deg), 138 x 131 mas (-55 deg), 110 x 88 mas (-45 deg), 165 x 127 mas (+29 deg) to 150 x 125 mas (+21 deg) for R Dor; 175 x 145 mas (-15 deg) to 165 x 135 mas (-10 deg) for IK Tau",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "33 x 29 mas (+55 deg), 138 x 131 mas (-55 deg), 110 x 88 mas (-45 deg), 165 x 127 mas (+29 deg) to 150 x 125 mas (+21 deg) for R Dor; 175 x 145 mas (-15 deg) to 165 x 135 mas (-10 deg) for IK Tau",
  "failed_quote": "AlO N = 9 -> 8 338.167- 2013.1.00166.S 20150827- 25.2 0.3- 165, 127, +29 0.9- 3.5- 3.1"
 },
 {
  "path": "processing.imaging.final_beam.evidence[2]",
  "value": "33 x 29 mas (+55 deg), 138 x 131 mas (-55 deg), 110 x 88 mas (-45 deg), 165 x 127 mas (+29 deg) to 150 x 125 mas (+21 deg) for R Dor; 175 x 145 mas (-15 deg) to 165 x 135 mas (-10 deg) for IK Tau",
  "failed_quote": "AlO N = 9 -> 8 338.167- 2013.1.00166.S 20150813- 10 0.2- 175, 145, -15 1.7- 4.7- 3.1"
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "0.8, 1.0, 3.8, 3.5-4.5 mJy (R Dor); 4.7-5.3 mJy (IK Tau)",
  "failed_quote": "AlO N = 6 -> 5 229.670 2017.1.00824.S 20171024- 192 0.6 33, 29, +55 0.32 0.8 2.6"
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Overdensity model for testing inner disk / density enhancement",
  "failed_quote": "Although it did not have a significant effect on our AlO model, we tested the effect of the \"overdensity\" model from Danilovich et al. (2020), with an increase in H2 number density between ~ 3R_* and 4R_* by a factor of 8."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Extract spectra from the central pixel (~1'' beam) of SMA data and perform least-squares fits of Gaussian profiles (for v = 0, 1) and composite synthetic hyperfine profiles (for v = 2).",
  "failed_quote": "The observed frequencies nu_obs in the ground vibrational state and the v = 1 level and the FWHM line width, Delta v, were derived from Gaussian profiles that were least squares fit to the spectra (see Fig. 2)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Comparison of derived LSR velocity with stellar velocity and ground state AlO velocity, and comparison of line width ratios across v states with theoretical spin-rotation interaction predictions.",
  "failed_quote": "The mean central LSR velocity v_LSR = 21.5 +- 3.3 km s^-1 for the four rotational transitions in the excited vibrational levels of AlO in Table 1 is in good agreement with the stellar velocity (v_LSR = 22 km s^-1, Kaminski et al. 2013a)"
 },
 {
  "path": "analysis_steps[0].validation.evidence[1]",
  "value": "Comparison of derived LSR velocity with stellar velocity and ground state AlO velocity, and comparison of line width ratios across v states with theoretical spin-rotation interaction predictions.",
  "failed_quote": "As expected, the FWHM of the lines are 3.3 +- 0.4 times smaller in the v = 1 level, and 1.6 +- 0.3 times smaller in the v = 2 level than those in the ground vibrational state — i.e., close to the theoretical predictions discussed in Sect. 2.1"
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Extract spectra in circular apertures from calibrated spectral cubes, measure peak and integrated fluxes, fit Gaussians to TiO lines, and create zeroth-order moment maps over channels exceeding the rms.",
  "failed_quote": "Based on the line frequencies reported in Table 4, we find the mean central velocity of the TiO lines towards R Dor is v_cent(TiO) = 7.8 +- 0.4 km s^-1, based on fitting Gaussians to the emission for lines with v <= 2 and excluding the line blended with SO2."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Gaussian fitting to TiO emission lines",
  "failed_quote": "Based on the line frequencies reported in Table 4, we find the mean central velocity of the TiO lines towards R Dor is v_cent(TiO) = 7.8 +- 0.4 km s^-1, based on fitting Gaussians to the emission for lines with v <= 2 and excluding the line blended with SO2."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[1]",
  "value": "Linear fit in log(Nu/gu) vs Energy diagram",
  "failed_quote": "From the derived T_vib of 1800 +- 170 K (see diagram in Fig. 6)"
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Comparison of predicted v = 3 peak flux of TiO from T_vib with observed spectral features.",
  "failed_quote": "From the derived T_vib of 1800 +- 170 K (see diagram in Fig. 6), we estimate the peak flux of the J = 11 -> 10 rotational transitions in the v = 3 excited vibrational level (E_u = 4275 K) of 19 mJy is within a few mJy of the peak flux in the spectra centered on the Omega = 2 and Omega = 3 spin components"
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Model the circumstellar envelope using a 1D spherically symmetric non-LTE ALI radiative transfer code without hyperfine structure, then distribute integrated flux among hyperfine components according to quantum mechanical line strengths and sum Gaussians to obtain line profiles.",
  "failed_quote": "For this, we used a 1D spherically symmetric non-LTE radiative transfer program based on the accelerated lambda iteration method (ALI; Rybicki & Hummer 1991; Maercker et al. 2008) to calculate the abundances and line profiles of AlO and TiO."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "30 shells logarithmically spaced from r_0 = 3.3 x 10^13 cm to r_max = 4 x 10^14 cm; circular model beam radius = 150 mas",
  "failed_quote": "Our model circumstellar envelopes (CSEs) were divided into 30 shells, evenly spaced on a logarithmic scale from an inner radius r_0 = 3.3 x 10^13 cm, out to an outer radius r_max = 4 x 10^14 cm."
 },
 {
  "path": "analysis_steps[3].key_parameters[1].evidence[0]",
  "value": "Levels included: N < 20 and v <= 10; hyperfine Gaussian HWHM = 3 km s^-1",
  "failed_quote": "We used Gaussians with a HWHM of 3 km s^-1, close to the innermost velocity as derived from the sound speed, to represent the hyperfine components."
 },
 {
  "path": "analysis_steps[3].key_parameters[2].evidence[0]",
  "value": "Stellar/CSE parameters from Table 5: R_* = 3.3 x 10^13 cm, T_eff = 2400 K, D = 59 pc, L_* = 6500 L_sun, M_dot = 1.6 x 10^-7 M_sun yr^-1, v_inf = 5.7 km s^-1, v_0 = 3 km s^-1, v_LSR = 7.0 km s^-1, v_turb = 1 km s^-1, epsilon = 0.65, beta = 1.5, r_e = 1 x 10^14 cm",
  "failed_quote": "R_* cm 3.3 x 10^13 T_eff K 2400 D pc 59 L_* L_sun 6500 M_dot 10^-7 M_sun yr^-1 1.6"
 },
 {
  "path": "analysis_steps[3].key_parameters[2].evidence[1]",
  "value": "Stellar/CSE parameters from Table 5: R_* = 3.3 x 10^13 cm, T_eff = 2400 K, D = 59 pc, L_* = 6500 L_sun, M_dot = 1.6 x 10^-7 M_sun yr^-1, v_inf = 5.7 km s^-1, v_0 = 3 km s^-1, v_LSR = 7.0 km s^-1, v_turb = 1 km s^-1, epsilon = 0.65, beta = 1.5, r_e = 1 x 10^14 cm",
  "failed_quote": "v_inf km s^-1 5.7 v_0 km s^-1 3 v_LSR km s^-1 7.0 v_turb km s^-1 1 epsilon ... 0.65 beta ... 1.5 r_0 cm 3.3 x 10^13 r_e cm 1 x 10^14"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[2]",
  "value": "Gaussian fractional abundance profile with r_e = 1 x 10^14 cm; He-SiO collisional rates scaled by mass as surrogate for H2-AlO",
  "failed_quote": "For both molecules, an e-folding radius of 1 x 10^14 cm was used."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Tested sensitivity to different collisional rate sets (SiO, NaCl, NaCl x 100, zero collisions), extraction aperture size (300 mas vs 150 mas), inner disk overdensity model, hyperfine component HWHM (3 vs 4.5 vs 5.7 km s^-1), and increased IR radiation field.",
  "failed_quote": "In Sect. A.1 we discuss the effects of different choices of collisional rates. Ultimately, we found that the choice of collisional rates had a small but generally insignificant impact on our model results."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "Circular model beam radius = 300 mas; J <= 20, v <= 5 in X^3Delta state; constant outward gas velocity v_gas = 6 km s^-1; H2 number density 8 times higher for ~3-4 R_*; additional uniform IR field from a 1200 K blackbody",
  "failed_quote": "II. v_gas = 6 km/s X^3Delta As in I, but with a constant outward gas velocity v_gas = 6 km s^-1 III. Overdensity X^3Delta As in II, but with the H2 number density 8 times higher for ~ 3-4 R_* and f_TiO = 1.0 x 10^-7."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[2]",
  "value": "Circular model beam radius = 300 mas; J <= 20, v <= 5 in X^3Delta state; constant outward gas velocity v_gas = 6 km s^-1; H2 number density 8 times higher for ~3-4 R_*; additional uniform IR field from a 1200 K blackbody",
  "failed_quote": "VI. Higher IR field X^3Delta As in III, but with an additional IR field. VII. Final model X^3Delta As in VI, but with f_TiO = 1.4 x 10^-7."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "Gaussian fractional abundance profile with r_e = 1 x 10^14 cm; f_TiO constrained not to exceed solar Ti abundance (1.8 x 10^-7); He-NaCl collisional rates at 700 K scaled by mass; LTE at 1800 K for fine-structure scaling",
  "failed_quote": "When adjusting our model to best reproduce the observations, we did not allow the fractional abundance of TiO to exceed the solar abundance of Ti (Ti/H2 = 1.8 x 10^-7; Asplund et al. 2009)."
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "Adjusted model physics (Models I-VII in Table 6) and free parameter f_TiO to reproduce v = 0, 1, 2 line profiles",
  "failed_quote": "With the inclusion of this additional infrared flux, we were finally able to reproduce all the TiO lines, including those in higher vibrational states. Our best fit model, which has f_TiO = 1.4 x 10^-7 is shown in Fig. 11, plotted with the observed spectra."
 },
 {
  "path": "analysis_steps[4].validation.evidence[0]",
  "value": "Tested 7 model configurations (beta-velocity law, constant 6 km/s velocity, 3-4 R_* overdensity, inclusion of singlet and triplet excited electronic states, silicate dust opacity, and additional 1200 K IR field).",
  "failed_quote": "We tested models including these two singlet states, and including a larger complement of excited (singlet and triplet) states: X^3Delta, a^1Delta, d^1Sigma^+, b^1Pi, E^3Pi, A^3Phi, B^3Pi, C^3Delta, and D^3Sigma^-."
 },
 {
  "path": "analysis_steps[4].validation.evidence[1]",
  "value": "Tested 7 model configurations (beta-velocity law, constant 6 km/s velocity, 3-4 R_* overdensity, inclusion of singlet and triplet excited electronic states, silicate dust opacity, and additional 1200 K IR field).",
  "failed_quote": "Including silicate dust with their derived opacity (optical depth of 0.05 at 10 um, Maercker et al. 2016) did not have a noticeable effect on the TiO (or AlO) emission."
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Estimate TiO2 column density from the 26_0,26 -> 25_1,25 transition at 350.399 GHz assuming T_ex = 1800 K; calculate molecular structures, dipole moments, and relative energies of Al2O, AlO2, and Al2O2 isomers at the ae-CCSD(T)/cc-pWCVTZ level of theory.",
  "failed_quote": "An estimate of the column density of TiO2, derived from a single transition in the ground vibrational state (26_0,26 -> 25_1,25) at 350.399 GHz) on the assumption that the excitation temperature is 1800 K, was comparable to the column density of TiO found in our models."
 },
 {
  "path": "analysis_steps[5].key_parameters[0].evidence[0]",
  "value": "T_ex = 1800 K for TiO2; ae-CCSD(T)/cc-pWCVTZ and cc-pWCVDZ basis sets for aluminum oxides",
  "failed_quote": "An estimate of the column density of TiO2, derived from a single transition in the ground vibrational state (26_0,26 -> 25_1,25) at 350.399 GHz) on the assumption that the excitation temperature is 1800 K, was comparable to the column density of TiO found in our models."
 },
 {
  "path": "analysis_steps[5].assumptions[0].evidence[0]",
  "value": "Excitation temperature of TiO2 is 1800 K",
  "failed_quote": "An estimate of the column density of TiO2, derived from a single transition in the ground vibrational state (26_0,26 -> 25_1,25) at 350.399 GHz) on the assumption that the excitation temperature is 1800 K, was comparable to the column density of TiO found in our models."
 },
 {
  "path": "analysis_steps[5].validation.evidence[0]",
  "value": "Compared calculated quadrupole coupling constants (eQq) of AlO2 isomers with laboratory measurements of AlO.",
  "failed_quote": "The calculated quadrupole coupling constant (eQq) of -20.9 MHz for the C_2v isomer and -26.6 MHz for the C_inf_v isomer are similar to that of AlO (eQq = -26.1 +- 0.21 MHz; Goto et al. 1994), implying the Al-O bonding character is very similar in AlO and AlO2."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "1D spherically symmetric non-LTE radiative transfer modeling of AlO and TiO line profiles and abundances",
  "failed_quote": "For this, we used a 1D spherically symmetric non-LTE radiative transfer program based on the accelerated lambda iteration method (ALI; Rybicki & Hummer 1991; Maercker et al. 2008) to calculate the abundances and line profiles of AlO and TiO."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Continuum flux density of R Dor (at AlO N = 6 -> 5) = 252 mJy",
  "failed_quote": "The continuum was unresolved or barely resolved, with a flux density ranging from 252 mJy in the image covering AlO N = 6 -> 5, to 596 mJy covering AlO N = 9 -> 8."
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Continuum flux density of R Dor (at AlO N = 9 -> 8) = 596 mJy",
  "failed_quote": "The continuum was unresolved or barely resolved, with a flux density ranging from 252 mJy in the image covering AlO N = 6 -> 5, to 596 mJy covering AlO N = 9 -> 8."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Mean central LSR velocity of excited AlO lines in VY CMa = 21.5 km s^-1",
  "failed_quote": "The mean central LSR velocity v_LSR = 21.5 +- 3.3 km s^-1 for the four rotational transitions in the excited vibrational levels of AlO in Table 1 is in good agreement with the stellar velocity"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Integrated flux of AlO N = 8 -> 7 (v = 1) in VY CMa = 8.9 Jy km s^-1",
  "failed_quote": "1 303,412.064 303,390.0 +- 0.6 477 17.5 +- 1.5 21.8 +- 0.6 0.91 8.9 +- 0.9 3.1 +- 0.3"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Integrated flux of AlO N = 8 -> 7 (v = 2) in VY CMa = 7.7 Jy km s^-1",
  "failed_quote": "2 300,611.392 300,591.0 +- 3.0 340 41.0 +- 7.2 20.3 +- 3.0 0.92 7.7 +- 1.6 1.3 +- 0.2"
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Integrated flux of AlO N = 9 -> 8 (v = 1) in VY CMa = 12.5 Jy km s^-1",
  "failed_quote": "1 341,318.153 341,294.6 +- 0.6 661 12.6 +- 1.1 20.7 +- 0.5 0.82 12.5 +- 1.1 3.6 +- 0.3"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Integrated flux of AlO N = 9 -> 8 (v = 2) in VY CMa = 6.2 Jy km s^-1",
  "failed_quote": "2 338,167.232 338,141.0 +- 1.0 242 24.2 +- 2.1 23.3 +- 0.9 0.81 6.2 +- 0.7 1.9 +- 0.2"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Integrated flux of AlO N = 7 -> 6 (v = 0) in R Dor = 775 mJy km s^-1",
  "failed_quote": "0 7 -> 6 267,936.560 267,932.6 +- 5.4 4.4 19 +- 3 73 150 775 +- 23"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Integrated flux of AlO N = 8 -> 7 (v = 0) in R Dor = 1986 mJy km s^-1",
  "failed_quote": "0 8 -> 7 306,197.319 306,191 +- 12 5.4 50 +- 6 68 150 1986 +- 90"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Integrated flux of AlO N = 9 -> 8 (v = 0) in R Dor = 3133 mJy km s^-1",
  "failed_quote": "0 9 -> 8 344,451.721 344,445.1 +- 1.5 5.8 87 +- 12 51.0 150 3133 +- 75"
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Integrated flux of AlO N = 9 -> 8 (v = 2) in R Dor = 612 mJy km s^-1",
  "failed_quote": "2 9 -> 8 338,167.232 338,156 +- 12 10.3 22 +- 5 29.7 150 612 +- 14"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Vibrational temperature of AlO in R Dor = 1860 K",
  "failed_quote": "The high observed T_vib of AlO in R Dor of 1860 +- 200 K implies a fraction of the emission arises within about 2 R_* (or ~ 60 mas) from the central star"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Total column density of AlO in R Dor (VT diagram) = (1.9 +- 0.5) x 10^15 cm^-2",
  "failed_quote": "Shown in Fig. 4 is a vibrational temperature (VT) diagram for AlO in R Dor. ... From this we determined the total column density (N)"
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Vibrational temperature of TiO in R Dor = 1800 K",
  "failed_quote": "From the derived T_vib of 1800 +- 170 K (see diagram in Fig. 6), we estimate the peak flux of the J = 11 -> 10 rotational transitions in the v = 3 excited vibrational level"
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Mean central LSR velocity of TiO lines in R Dor = 7.8 km s^-1",
  "failed_quote": "Based on the line frequencies reported in Table 4, we find the mean central velocity of the TiO lines towards R Dor is v_cent(TiO) = 7.8 +- 0.4 km s^-1, based on fitting Gaussians to the emission for lines with v <= 2 and excluding the line blended with SO2."
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 1, v = 0) in R Dor = 2,077 mJy km s^-1",
  "failed_quote": "1 0 348,159.8 348,150.75 +- 0.22 7.8 221 +- 9 9.4 +- 0.4 300 2,077 +- 122"
 },
 {
  "path": "results_numeric[16].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 1, v = 1) in R Dor = 804 mJy km s^-1",
  "failed_quote": "1 346,198.2 346,188.8 +- 0.4 8.1 91 +- 7 8.8 +- 0.9 300 804 +- 103"
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 1, v = 2) in R Dor = 377 mJy km s^-1",
  "failed_quote": "2 344,224.3 344,225 +- 3.1 7.5 44 +- 4 8.2 +- 0.9 300 377 +- 13"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 2, v = 0) in R Dor = 1,739 mJy km s^-1",
  "failed_quote": "2 0 352,157.6 352,148.18 +- 0.25 8.0 184 +- 8 9.4 +- 0.5 300 1,739 +- 119"
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 2, v = 1) in R Dor = 799 mJy km s^-1",
  "failed_quote": "1 350,147.5 350,138.9 +- 0.4 7.4 88 +- 7 9.1 +- 0.9 300 799 +- 101"
 },
 {
  "path": "results_numeric[20].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 3, v = 0) in R Dor = 2,297 mJy km s^-1",
  "failed_quote": "3 0 355,623.3 355,614.38 +- 0.26 7.5 208 +- 8 11.0 +- 0.5 300 2,297 +- 137"
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 3, v = 1) in R Dor = 630 mJy km s^-1",
  "failed_quote": "1 353,573.4 353,575.2 +- 0.7 8.5 75 +- 11 8.4 +- 1.4 300 630 +- 140"
 },
 {
  "path": "results_numeric[22].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 3, v = 2) in R Dor = 391 mJy km s^-1",
  "failed_quote": "2 351,511.2 351,502.5 +- 1.5 7.5 51 +- 14 7.7 +- 2.4 300 391 +- 127"
 },
 {
  "path": "results_numeric[23].evidence[0]",
  "value": "Mean central LSR velocity of TiO lines in IK Tau = 32.4 km s^-1",
  "failed_quote": "Considering only the five detected lines shown in Fig. 7, we find a mean central velocity of v_cent(TiO) = 32.4 +- 0.4 km s^-1."
 },
 {
  "path": "results_numeric[24].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 2, v = 1) in IK Tau = 139 mJy km s^-1",
  "failed_quote": "1 350,147.5 350,147.3 +- 2.5 32.4 17 +- 4 6.0 +- 5.1 160 139"
 },
 {
  "path": "results_numeric[25].evidence[0]",
  "value": "Integrated flux of TiO J = 11 -> 10 (Omega = 3, v = 1) in IK Tau = 75 mJy km s^-1",
  "failed_quote": "1 353,573.4 353,575.7 +- 1.6 32.2 15 +- 4 4.2 +- 3.4 160 75"
 },
 {
  "path": "results_numeric[26].evidence[0]",
  "value": "Central fractional abundance of AlO relative to H2 in R Dor (f_AlO) = 1.7 x 10^-7 dimensionless",
  "failed_quote": "Our best fitting model with the expanded molecular data described above has f_AlO = 1.7 x 10^-7 when using collisional rates based on the Dayou & Balanca (2006) SiO rates"
 },
 {
  "path": "results_numeric[28].evidence[0]",
  "value": "Central fractional abundance of AlO relative to H2 in R Dor (overdensity disk model) = 7 x 10^-8 dimensionless",
  "failed_quote": "From this we found a new best fit model with f_AlO = 7 x 10^-8 relative to H2."
 },
 {
  "path": "results_numeric[29].evidence[0]",
  "value": "Central fractional abundance of TiO relative to H2 in R Dor (f_TiO) = 1.4 x 10^-7 dimensionless",
  "failed_quote": "Our best fit model, which has f_TiO = 1.4 x 10^-7 is shown in Fig. 11, plotted with the observed spectra."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "Rotational transitions of vibrationally excited AlO (v = 1, 2) are identified in VY CMa, AlO (v = 2) and TiO (v = 1, 2) in R Dor, and TiO (v = 1) in IK Tau.",
  "failed_quote": "The J = 11 -> 10 transition of TiO in the v = 1 and 2 levels, and the N = 9 -> 8 transition in the v = 2 level of AlO were identified towards R Dor; the J = 11 -> 10 line of TiO was identified in the v = 1 level towards IK Tau; and two transitions in the v = 1 and 2 levels of AlO were identified towards VY CMa."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "Vibrationally excited AlO and TiO rotational lines are securely identified in oxygen-rich stars, with AlO line width variations across vibrational levels matching theoretical spin-rotation interaction predictions.",
  "failed_quote": "The J = 11 -> 10 transition of TiO in the v = 1 and 2 levels, and the N = 9 -> 8 transition in the v = 2 level of AlO were identified towards R Dor; the J = 11 -> 10 line of TiO was identified in the v = 1 level towards IK Tau; and two transitions in the v = 1 and 2 levels of AlO were identified towards VY CMa."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "Vibrationally excited AlO and TiO rotational lines are securely identified in oxygen-rich stars, with AlO line width variations across vibrational levels matching theoretical spin-rotation interaction predictions.",
  "failed_quote": "As expected, the FWHM of the lines are 3.3 +- 0.4 times smaller in the v = 1 level, and 1.6 +- 0.3 times smaller in the v = 2 level than those in the ground vibrational state — i.e., close to the theoretical predictions discussed in Sect. 2.1, thereby providing further confirmation of the line assignments."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "A substantial fraction of AlO and TiO is located within ~2 R_* of the star (inside the dust condensation radius), and infrared radiative pumping is essential for populating their vibrationally excited states.",
  "failed_quote": "The newly-derived high vibrational temperature of TiO and AlO in R Dor of 1800 +- 200 K, and prior measurements of the angular extent confirm that the majority of the emission is from a region within <= 2R_* of the central star."
 },
 {
  "path": "claims[3].evidence[1]",
  "value": "While AlO and TiO abundances do not preclude incorporation into dust grains, current observations cannot conclusively determine whether AlO, TiO, and TiO2 are the seeds of Al2O3 dust without higher angular resolution and sensitivity.",
  "failed_quote": "Our revised fractional abundance of AlO in R Dor (f_0 = 1.7 x 10^-7) is about 2 times higher than the earlier estimate by Decin et al. (8.4 x 10^-8, 2017), but it is still much lower than the solar abundance of Al (5.6 x 10^-6, with respect to H2; Asplund et al. 2009). Hence, this result does not preclude the possibility of AlO being incorporated into dust"
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "R Dor is the closest AGB star to the Sun (59 pc) with a large stellar diameter (54 mas) and rich molecular spectrum, and existing sensitive interferometric spectral line surveys of R Dor, IK Tau, and VY CMa have high enough ground-state peak fluxes and gas temperatures (~1400 K) to make vibrationally excited AlO and TiO observable.",
  "failed_quote": "The semiregular (SR) variable oxygen rich star R Dor is the closest AGB star to our Sun (59 pc, Knapp et al. 2003). It has a very low mass loss rate (1.6 x 10^-7 M_sun yr^-1, Maercker et al. 2016), the stellar diameter is large (54 mas, Norris et al. 2012), it is molecule rich, and there is a 27 GHz wide spectral line survey in Band 7 with ALMA"
 },
 {
  "path": "reasoning.why_this_method.evidence[1]",
  "value": "Explicitly including all hyperfine levels of AlO or fine-structure ladders of TiO in non-LTE radiative transfer is computationally prohibitive, so radiative transfer was solved without hyperfine/fine structure and the resulting fluxes were distributed/scaled among components afterwards; a smaller 150 mas aperture was chosen for AlO in R Dor to exclude the asymmetric SE extension that a 1D spherica",
  "failed_quote": "To analyze TiO in the most efficient way possible, we first ran a radiative transfer model excluding the fine structure — i.e., TiO was treated as though it were a closed shell molecule."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Using a 300 mas spectral extraction aperture for AlO in R Dor was tested, showing that including the asymmetric SE extension causes the 1D model to under-predict the N = 9 -> 8 and 8 -> 7 lines.",
  "failed_quote": "The differences between Figures 8 and 14 clearly show the impact of the SE extension: the ground state lines of (9 -> 8) and (8 -> 7) are slightly under-predicted when additional emission from the SE extension is included in the observed spectra"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[3].evidence[0]",
  "value": "Including silicate dust with optical depth 0.05 at 10 um (Maercker et al. 2016) was tested and found to have no noticeable effect on TiO or AlO emission.",
  "failed_quote": "Including silicate dust with their derived opacity (optical depth of 0.05 at 10 um, Maercker et al. 2016) did not have a noticeable effect on the TiO (or AlO) emission."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[1]",
  "value": "The AlO N = 6 -> 5 observation towards R Dor at high spatial resolution (33 x 29 mas) is dominated by absorption against the star and affected by resolved-out flux, complicating interpretation and preventing its inclusion in the line fitting.",
  "failed_quote": "In addition, the 150 mas extraction of the (6 -> 5) is strongly affected by resolved-out flux, which is a less prominent problem for the 300 mas aperture spectrum, since the latter is more strongly dominated by noise."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Line overlaps/blends with SO2 and 34SO2 prevent measurement of AlO N = 9 -> 8 (v = 1) and TiO J = 11 -> 10 (Omega = 2, v = 2 and Omega = 1, v = 3) in R Dor, and NS blends obscure TiO (Omega = 1, v = 1) in IK Tau.",
  "failed_quote": "Unfortunately the N = 9 -> 8 transition in the v = 1 level of AlO at 341,318 MHz is within 3 - 4 MHz of two transitions of SO2"
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[1]",
  "value": "Line overlaps/blends with SO2 and 34SO2 prevent measurement of AlO N = 9 -> 8 (v = 1) and TiO J = 11 -> 10 (Omega = 2, v = 2 and Omega = 1, v = 3) in R Dor, and NS blends obscure TiO (Omega = 1, v = 1) in IK Tau.",
  "failed_quote": "The J = 11 -> 10 transition in the v = 2 level of ^3Delta_2 is uncertain, because it is blended with a line of 34SO2 which is 8 MHz lower in frequency."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "TiO and TiO2 emission in R Dor is spatially unresolved (~140-150 mas beam), preventing direct constraint of the radial abundance profile e-folding radius.",
  "failed_quote": "For TiO we don't have any more detailed spatial information, since the emission is unresolved, but we assume a relatively compact distribution that we expect to be approximately similar to that of AlO."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[1]",
  "value": "TiO and TiO2 emission in R Dor is spatially unresolved (~140-150 mas beam), preventing direct constraint of the radial abundance profile e-folding radius.",
  "failed_quote": "A direct determination of the size of the compact molecular emission is limited by the angular resolution in the present observations (~ 140 mas, or 2.5 times the stellar diameter theta_d; Decin et al. 2018)."
 },
 {
  "path": "reasoning.limitations_admitted[4].evidence[1]",
  "value": "The 1D spherically symmetric radiative transfer model cannot properly represent 3D non-spherical structures such as the rotating inner disk or the south-eastern AlO emission extension, and uses an unphysical constant 6 km s^-1 expansion velocity and uniform 1200 K blackbody radiation field as 1D approximations.",
  "failed_quote": "Although the implemented expansion velocity of 6 km s^-1 is unphysical in a region so close to the star, it can be thought of here as a partial 1D approximation of the rotating disk."
 },
 {
  "path": "reasoning.limitations_admitted[4].evidence[2]",
  "value": "The 1D spherically symmetric radiative transfer model cannot properly represent 3D non-spherical structures such as the rotating inner disk or the south-eastern AlO emission extension, and uses an unphysical constant 6 km s^-1 expansion velocity and uniform 1200 K blackbody radiation field as 1D approximations.",
  "failed_quote": "Our radiative transfer model cannot account for non-spherically symmetric features, so it is possible the 7 -> 6 line is excited more in (the faster rotating portion of) the disc than the other transitions."
 }
]
```
