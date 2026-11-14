# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...642A.222H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy_ _&_ _Astrophysics_ manuscript no. main _⃝_ c ESO 2020
September 21, 2020

## **Sulphur and carbon isotopes towards Galactic centre clouds**


P. K. Humire, [1] V. Thiel, [1] C. Henkel, [1] _[,]_ [ 2] _[,]_ [ 3] A. Belloche, [1] J.-C. Loison, [4] T. Pillai, [1] _[,]_ [ 5] D. Riquelme, [1] V.
Wakelam, [6] N. Langer, [1] _[,]_ [ 7] A. Hernández-Gómez, [1] R. Mauersberger, [1] and K. M. Menten [1]


1 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany
e-mail: `phumire@mpifr-bonn.mpg.de`
2 Dept. of Astron., King Abdulaziz University, P.O. Box 80203, Jeddah 21589, Saudi Arabia
3 Xinjiang Astronomical Observatory, Chinese Academy of Sciences, 830011 Urumqi, China
4 Institut des Sciences Moléculaires (ISM), CNRS, Univ. Bordeaux, 351 cours de la Libération, F-33400, Talence,
France
5 Institute for Astrophysical Research, 725 Commonwealth Ave, Boston University Boston, MA 02215, USA
6 Laboratoire d’astrophysique de Bordeaux, CNRS, Univ. Bordeaux, B18N, allée Geoffroy Saint-Hilaire, F-33615 Pessac, France
7 Argelander-Institut für Astronomie, Universität Bonn, Auf dem Hügel 71, 53121 Bonn, Germany


Received xxx, yyy; accepted xxx, yyy


**ABSTRACT**


_Context._ Measuring isotopic ratios is a sensitive technique used to obtain information on stellar nucleosynthesis and
chemical evolution.
_Aims._ We present measurements of the carbon and sulphur abundances in the interstellar medium of the central region
of our Galaxy. The selected targets are the +50km s _[−]_ [1] Cloud and several line-of-sight clouds towards Sgr B2(N).
_Methods._ Towards the +50 km s _[−]_ [1] Cloud, we observed the _J_ =2–1 rotational transitions of [12] C [32] S, [12] C [34] S, [13] C [32] S,
12 C 33 S, and 13 C 34 S, and the _J_ =3–2 transitions of 12 C 32 S and 12 C 34 S with the IRAM-30 m telescope, as well as the
_J_ =6–5 transitions of [12] C [34] S and [13] C [32] S with the APEX 12 m telescope, all in emission. The _J_ =2–1 rotational transitions
of [12] C [32] S, [12] C [34] S, [13] C [32] S, and [13] C [34] S were observed with ALMA in the envelope of Sgr B2(N), with those of [12] C [32] S
and [12] C [34] S also observed in the line-of-sight clouds towards Sgr B2(N), all in absorption.
_Results._ In the +50 km s _[−]_ [1] Cloud we derive a 12 C/ 13 C isotopic ratio of 22.1 +3 _−_ 2 _.._ 34 [,] [that] [leads,] [with] [the] [measured]
13 C 32 S/ 12 C 34 S line intensity ratio, to a 32 S/ 34 S ratio of 16.3 +3 _−_ 2 _.._ 04 [.] [We] [also] [derive] [the] [32] [S/] [34] [S] [isotopic] [ratio] [more]
directly from the two isotopologues [13] C [32] S and [13] C [34] S, which leads to an independent [32] S/ [34] S estimation of 16.3 _−_ [+2] 1 _[.]_ _._ [1] 7
and 17.9 _±_ 5.0 for the +50 km s _[−]_ [1] Cloud and Sgr B2(N), respectively. We also obtain a [34] S/ [33] S ratio of 4.3 _±_ 0.2 in the
+50 km s _[−]_ [1] Cloud.
_Conclusions._ Previous studies observed a decreasing trend in the [32] S/ [34] S isotopic ratios when approaching the Galactic
centre. Our result indicates a termination of this tendency at least at a galactocentric distance of 130 [+60] _−_ 30 [pc.] [This] [is]
at variance with findings based on [12] C/ [13] C, [14] N/ [15] N and [18] O/ [17] O isotope ratios, where the above-mentioned trend is
observed to continue right to the central molecular zone. This can indicate a drop in the production of massive stars
at the Galactic centre, in the same line as recent metallicity gradient ([Fe/H]) studies, and opens the work towards a
comparison with Galactic and stellar evolution models.


**Key** **words.** Galaxy: abundances – Galaxy: centre – Galaxy: evolution – ISM: abundances – ISM: molecules – radio
lines: ISM



**1.** **Introduction**


Studying stellar nucleosynthesis and chemical enrichment
of rare isotopes of a given element at optical wavelengths
is difficult because the observed atomic isotope lines are
usually affected by blending (e.g. Hawkins & Jura 1987;
Levshakov et al. 2006; Ritchey et al. 2011). However, at radio and (sub)millimeter wavelengths, transitions from rare
isotopic substitutions of a given molecular species, called
isotopologues, are well separated in frequency from their
main species, typically by a few percent of their rest fre
quency.
While the relative abundances of C, N, and O isotopes
provide information on carbon–nitrogen–oxygen (CNO)
and helium burning, sulphur isotopes allow us to probe late
evolutionary stages of massive stars and supernovae (SNe)



of Type Ib/c and II (oxygen-burning, neon-burning, and sprocess nucleosynthesis) (Wilson & Rood 1994; Chin et al.
1996; Mauersberger et al. 1996), filling a basic gap in our
understanding of stellar nucleosynthesis and the chemical
evolution of the universe (e.g. Wang et al. 2013).
In the interstellar medium (ISM), atomic sulphur is
thought to freeze out on dust grain mantles and to be later
released from the grains due to shocks, leading to the formation of several molecular species in the gas phase, such as
OCS, SO 2, H 2 S, and H 2 CS (Millar & Herbst 1990), which
serve as both shock and high-mass star formation tracers
in starburst galaxies (Bayet et al. 2008).
Among the sulphur-bearing compounds, CS (carbon
monosulfide) is the most accessible molecular species: its
lines are ubiquitous in the dense ISM and tend to be strong


Article number, page 1 of 16

_A&A_ _proofs:_ manuscript no. main



at sites of massive star formation in the spiral arms of our
Galaxy, in the Galactic centre (GC) region and in external
galaxies (e.g. Linke & Goldsmith 1980; Mauersberger et al.
1989; Bayet et al. 2009; Kelly et al. 2015).
Sulphur has four stable isotopes: [32] S, [33] S, [34] S, and [36] S.
Their solar system fractions are 95.018:0.750:4.215:0.017
(Lodders 2003), respectively. In the ISM, Chin et al.
32 34
(1996) found a relation between S/ S isotope
ratios and their galactocentric distance ( _D_ GC ) of
32 S/ 34 S=(3.3 _±_ 0.5)( _D_ GC /kpc)+(4.1 _±_ 3.1) by using a
linear least-squares fit to the unweighted data, with a
correlation coefficient of 0.84, while no correlation was
obtained between [34] S/ [33] S ratios and _D_ GC . However, most
of the sources observed in that study are located within the
galactocentric distance range 5.5 _≤_ _D_ GC _≤_ 7.0 kpc, with
the minimum distance at 2.9 kpc from the Galactic centre.
Therefore, it is important to also cover the inner region
of the Milky Way to find out whether the trend proposed
by Chin et al. (1996) is also valid for the inner Galaxy
as has been reported for the [12] C/ [13] C (see e.g. Yan et al.
2019), 14 N/ 15 N (Adande & Ziurys 2012) and 18 O/ 17 O
(Wouterloot et al. 2008; Zhang et al. 2015) isotopic ratios.
The GC region harbours one of the most intense and
luminous sites of massive star formation in the Galaxy,
Sgr B2 (Molinari et al. 2014; Ginsburg et al. 2018). It provides an extreme environment in terms of pressure, turbulent Mach number, and gas temperature (Ginsburg et al.
2016) over a much more extended region than encountered
in star-forming regions throughout the Galactic disc (Morris & Serabyn 1996; Ginsburg et al. 2016; Schwörer et al.
2019; Dale et al. 2019). These conditions are comparable to
those in starburst galaxies (Belloche et al. 2013; Schwörer
et al. 2019). We therefore expect unique results in this GC
study from sulphur ratios, which are a tool for tracing stellar processing (see Sect. 6). For a compilation of sulphur
ratios determined in our Milky Way, we refer to Tables 2
and 7 in Mauersberger et al. (2004) and Müller et al. (2006),
respectively.
As is true for our Galaxy, detections of [34] S in extragalactic objects remain scarce. Some observations, also accounting for [12] C/ [13] C ratios (using the double-isotope ratio
method, Sect. 4.1.1) led to values of _∼_ 16–25 and 13.5 _±_ 2.5
for the [32] S/ [34] S ratio in the nuclear starbursts of NGC 253
and NGC 4945, respectively (Wang et al. 2004; Henkel et al.
2014), although the value for NGC 4945 might be underestimated due to saturation of the CS lines (Martín et al. 2010).
A ratio of 20 _±_ 5 was obtained for N159 in the Large Magellanic Cloud (Johansson et al. 1994). At redshift _z_ =0.89,
a [32] S/ [34] S ratio of 10 _±_ 1 has been derived using absorption
lines from the spiral arm of a galaxy located along the line
of sight (l.o.s.) towards a radio loud quasar (Müller et al.
2006).
In the present study we focus on the _J_ =2–1 transitions
of [12] C [32] S (hereafter CS), [12] C [34] S (hereafter C [34] S), [13] C [32] S
(hereafter [13] CS), [12] C [33] S (hereafter C [33] S), and [13] C [34] S, the
_J_ =3–2 transitions of CS and C [34] S, and the _J_ =6–5 transitions of C [34] S and [13] CS, all observed together towards the
Sgr A Complex (see, e.g., Sandqvist et al. 2015). We have
also studied absorption features caused by the envelope of
Sgr B2(N) in the _J_ =2–1 rotational transition of CS, C [34] S,
13 CS and 13 C 34 S, as well as CS and C 34 S absorption features caused by l.o.s. clouds towards Sgr B2(N). These absorption and emission profiles allow us to obtain [12] C/ [13] C
and the missing [32] S/ [34] S ratios close to the Galactic nu

Article number, page 2 of 16



cleus. Expanding the database for sulphur isotope ratios in
the GC region is important in order to constrain models of
stellar interiors as well as models of the chemical evolution
of the Galaxy (e.g. Kobayashi et al. 2011).
The paper is organised as follows. In Sect. 2 we describe
the observations. In Sect. 3 we describe in detail our targets.
In Sect. 4 we present measured opacities and isotopologue
ratios from CS species, the modelling of our Sgr B2(N) data,
and a comprehensive study of CS fractionation. In Sect. 5
we compare our results with previous studies. In Sect. 6 we
discuss the results in the context of trends with galactocentric distance and give some explanations for our findings,
before summarising and concluding in Sect. 7.


**2.** **Observations**


_2.1._ + _50 km s_ _[−]_ [1] _Cloud_


The +50 km s _[−]_ [1] Cloud observations were conducted with
the IRAM 30 m and the APEX 12 m telescopes over a period of 1.5 years, from 2015 May to 2016 September, under varying weather conditions. The observed position was
_′_ _′′_
EQ J2000: 17 [h] 45 [m] 50 _._ 20 [s] _, −_ 28 _[◦]_ 59 41 _._ 1 for both telescopes,
and the representative spectral resolution was 0.6 km s _[−]_ [1] .
With the IRAM 30 m telescope, three frequency set-ups
were observed with the E090 and E150 receivers in combination with the Fast Fourier Transform Spectrometer
(FFTS, at 195 kHz resolution mode [1] ). For the observations
presented in this paper, we covered the 93.2–100.98 GHz
frequency range (CS, C [34] S, and C [33] S _J_ =2–1) in one setup with the E090 receiver. In a separate E090 set-up, our
tuning covered the frequency range 85.5-93.3 GHz ( [13] CS
and [13] C [34] S _J_ =2–1), while simultaneously the E150 receiver
covered the frequency range from 143.5 to 151.3 GHz (for
CS and C [34] S _J_ =3–2). The observations were conducted
in total power position switching mode. No spectral contamination was found in our off-source reference position
_′_ _′′_
(17 [h] 46 [m] 10 _._ 4 [s] _, −_ 29 _[◦]_ 07 08 ). The main beam efficiencies for
our IRAM 30 m measurements were computed using the
Ruze formalism (Ruze 1966). Adopted values were 0.8 and
0.7 at 98 and 147 GHz, respectively [2] . We discarded data
taken under poor weather conditions (precipitable water
vapour content (pwv) _>_ 7 mm) by discarding data taken
with system temperatures _>_ 500 K. The representative
half-power beam widths (HPBW) values are about 25 _[′′]_ at
98 GHz and 17 _[′′]_ at 147 GHz for the IRAM 30 m observa
tions.
The Atacama Pathfinder Experiment 12 m telescope
(APEX) 12 m (Güsten et al. 2006) was used for observations of the _J_ =6–5 lines of the CS, [13] CS, and [13] C [34] S isotopologues at roughly 280 GHz. The measurements were
conducted simultaneously using the FLASH345 (Klein et al.
2014) receiver connected to the extended FFTS (XFFTS)
backend. These observations were also executed in total
power position switching mode and the same off-source reference position, which was found to be clean. The HPBW
was about 22 _[′′]_ at the observed frequency and the adopted
main beam efficiency was 0.7.
All line intensities are reported in main beam brightness
temperature units ( _T_ MB ). While the spectral resolution was


1 http://www.iram.es/IRAMES/mainWiki/Backends
2 calculated following the table in `[https://www.iram.fr/](https://www.iram.fr/GENERAL/calls/w08/w08/node20.html)`
```
GENERAL/calls/w08/w08/node20.html

```

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A


instrument dependent (between 0.4 and 0.6 km s _[−]_ [1] for the
IRAM and 0.08 km s _[−]_ [1] for the APEX data), all spectra
were smoothed to a resolution of 3 km s _[−]_ [1] for analysis.
The data were reduced with the GILDAS package [3] and
required minimal flagging, followed by a baseline subtraction of order two.


_2.2._ _Line-of-sight_ _clouds_ _towards_ _Sgr_ _B2(N)_



For Sgr B2(N), we used the Exploring Molecular Complexity with ALMA (EMoCA) survey (Belloche et al. 2016)
that was performed with the Atacama Large Millimeter/submillimeter Array (ALMA) in the direction of this
source. The centre of the observed field (see Fig. 1) lies
in the middle (EQ J2000: 17 [h] 47 [m] 19 _._ 87 [s] _, −_ 28 _[◦]_ 22 _′_ 16 _′′_ ) between the two main hot cores, N1 and N2, which are separated by 4 _[′′]_ _._ 9 along the north–south direction, or around
0.19 pc in projection assuming a distance to the Galactic
centre, Sgr A _[∗]_, of 8.122 kpc (Gravity Collaboration et al.
2018). The survey covers the frequency range from 84.1 to
114.4 GHz, which includes carbon monosulfide _J_ =2–1 lines,
with a spectral resolution of 488 kHz (1.7 to 1.3 km s _[−]_ [1] ) at
a median angular resolution of 1 _[′′]_ _._ 6, or _∼_ 0.06 pc. The average noise level is _∼_ 3 mJy beam _[−]_ [1] per channel. Details of
the calibration and deconvolution of the data are reported
in Belloche et al. (2016, Sect. 2.2). For this work, we corrected the data for primary beam attenuation. Several isotopologues of CS are detected in the EMoCA survey. To
determine the [32] S/ [34] S and [12] C/ [13] C isotopic ratios, we use
four isotopologues: CS, C [34] S, [13] CS, and [13] C [34] S.
A list of the observed transitions of CS isotopologues
and some associated parameters is given in Table 1.


**3.** **Sources**


The +50 km s _[−]_ [1] Cloud (also known as M–0.02–0.07, although the +50 km s _[−]_ [1] Cloud could include additional
molecular knots on its positive-longitude side; (Ferrière
2012)), observed here with IRAM and APEX, is a giant
molecular cloud (GMC) of hook or indented-sphere shape,
considered to be one of the most prominent high-mass star
formation sites in the GC. It has a mass of _∼_ 5 _×_ 10 [5] M _⊙_ ;
a density of 10 [4] –10 [5] cm _[−]_ [3] ; a gas temperature of 80–100 K
(from NH 3, CH 3 CN, and CH 3 CCH; Güsten et al. 1985),
_∼_ 190 K (from H 2 CO, Ao et al. 2013), or 410 _±_ 10 K (from
NH 3, Mills & Morris 2013); and a dust temperature of 20–
30 K (Sandqvist et al. 2008). The energetics of at least a
part of the +50 km s _[−]_ [1] Cloud are influenced by the supernova (SN) remnant Sgr A East (Ferrière 2012; Uehara et al.
2019). In CS emission, its dense core peaks at a l.o.s. distance of 3 _±_ 3 pc relative to the Galactic centre (Ferrière
2012), coincident with 1.2 mm observations (Vollmer et al.
2003, and references therein), and peaks at (∆ _α,_ ∆ _δ_ ) _≈_ (3 _._ _[′]_ 0,
1 _._ _[′]_ 5) with respect to Sgr A _[∗]_, corresponding to _≈_ 7 _±_ 3 pc to
the east along the Galactic plane and 4.5 _±_ 3 pc to the south
from the Galactic plane (see the explanation for galactocentric Cartesian coordinates in Ferrière 2012, and their Table
1).
With ALMA we have observed Sgr B2(N)orth, one of
the sites of massive star formation associated with Sgr B2,
the most massive cloud in our Galaxy. The whole Sgr B2
complex has a total mass of 10 [7] M _⊙_ (Goldsmith et al. 1990)


3 `[https://www.iram.fr/IRAMFR/GILDAS](https://www.iram.fr/IRAMFR/GILDAS)`



Fig. 1: ALMA continuum map of Sgr B2(N) at 85 GHz. The
black contour lines show the flux density levels at 3 _σ_, 6 _σ_,
12 _σ_, and 24 _σ_ and the dotted lines indicate -3 _σ_, where _σ_ is
the rms noise level of 5.4 mJy beam _[−]_ [1] . The white crosses
denote the positions of the two main hot cores, Sgr B2(N1)
and Sgr B2(N2). The black cross, located between the white
ones, indicates the phase centre. The green crosses show
peaks of continuum emission selected for our absorption
study. They label the ultra compact H ii region K4, two
peaks in the shell of the H ii region K6 and one peak in
the shell of the H ii region K5 (Gaume et al. 1995). The
green ellipse in the lower left corner shows the size of the
synthesised beam of _∼_ 1 _[′′]_ _._ 6 (see Table 1).


and gas temperatures of at least 50 K (from p–H 2 CO in
Ginsburg et al. 2016, their Sect. 5.8). Most of the mass in
Sgr B2(N) ( _∼_ 73%) is contained in one single core (AN01)
(Sánchez-Monge et al. 2017). The densities and column densities of the hot cores in Sgr B2(N) are high ( _>_ 10 [6] cm _[−]_ [3]
and _>_ 10 [23] cm [2] ; Sánchez-Monge et al. 2017; Bonfand et al.
2019).
Sgr B2(N) is located at a galactocentric distance of
130 [+60] _−_ 30 [pc] [from] [Sgr A] _[∗]_ [(from] [Reid] [et] [al.] [2009][,] [consider-]
ing the projected distance of 100 pc as lower limit) or
_∼_ 8 kpc from us. Its diameter is _∼_ 0.8 pc (Lis & Goldsmith
1990; Schmiedeke et al. 2016). Several diffuse and translucent clouds are detected in absorption along the l.o.s. to
Sgr B2(N) (see e.g. Greaves & Williams 1994; Thiel et al.
2019). The exact locations of the different velocity components of the l.o.s. clouds towards Sgr B2(N) are not yet fully
constrained. In the case of our observations (see Table 4), we
can only suggest that the lines with negative velocities arise
from l.o.s. clouds between the Expanding Molecular Ring
(with a galactocentric radius of 200–300 pc, Whiteoak &
Gardner 1979) and the 1 kpc disc, while the lines with positive velocities arise from the envelope of Sgr B2(N) (Greaves
& Williams 1994; Wirström et al. 2010; Thiel et al. 2019).
Specifically, our lines in the range _−_ 105 to _−_ 70 km s _[−]_ [1] are
believed to be located within 1 kpc of the GC (Corby et al.


Article number, page 3 of 16

_A&A_ _proofs:_ manuscript no. main


Table 1: Some observational and physical parameters _[a]_ for the five measured CS isotopologue transitions in the +50km s _[−]_ [1]
Cloud and the four transitions from the l.o.s. clouds towards Sgr B2(N), which are also located in the Galactic centre
region.


Target Telescope Isotopologue Transition _ν_ 0 _[b]_ _E_ up _/k_ _[c]_ _A_ u _,_ l _[d]_ HPBW _[e]_

[GHz] [K] [s _[−]_ [1] ] [ _[′′]_ ]


+50 Cloud IRAM 30 m 13 C 34 S 2–1 90.9260260 6.55 1 _._ 19 _×_ 10 _[−]_ [5] 27.0
+50 Cloud IRAM 30 m 13 CS 2–1 92.4943080 6.66 1 _._ 41 _×_ 10 _[−]_ [5] 26.6
+50 Cloud IRAM 30 m C [34] S 2–1 96.4129495 6.25 1 _._ 60 _×_ 10 _[−]_ [5] 25.5
+50 Cloud IRAM 30 m C [33] S 2–1 97.1720639 7.00 1 _._ 63 _×_ 10 _[−]_ [5] 25.3
+50 Cloud IRAM 30 m CS 2–1 97.9809533 7.05 1 _._ 67 _×_ 10 _[−]_ [5] 25.1
+50 Cloud IRAM 30 m C [34] S 3–2 144.6171007 11.80 5 _._ 74 _×_ 10 _[−]_ [5] 17.0
+50 Cloud IRAM 30 m CS 3–2 146.9690287 14.10 6 _._ 05 _×_ 10 _[−]_ [5] 16.6
+50 Cloud APEX 12 m 13 CS 6–5 277.4554050 46.60 4 _._ 40 _×_ 10 _[−]_ [4] 22.1
+50 Cloud APEX 12 m C [34] S 6–5 289.2090684 38.19 4 _._ 81 _×_ 10 _[−]_ [4] 21.2
13 34
Sgr B2(N) ALMA C S 2–1 90.9260260 6.55 1 _._ 19 _×_ 10 _[−]_ [5] 1.8 _×_ 1.6
13
Sgr B2(N) ALMA CS 2–1 92.4943080 6.66 1 _._ 41 _×_ 10 _[−]_ [5] 2.9 _×_ 1.5
Sgr B2(N) ALMA C [34] S 2–1 96.4129549 6.25 1 _._ 60 _×_ 10 _[−]_ [5] 1.9 _×_ 1.4
Sgr B2(N) ALMA CS 2–1 97.9809533 7.05 1 _._ 67 _×_ 10 _[−]_ [5] 1.8 _×_ 1.3


**Notes.** [(] _[a]_ [)] The spectroscopic information for each molecule is taken from the Cologne Database for Molecular Spectroscopy
(CDMS, Müller et al. 2005; Endres et al. 2016). [(] _[b]_ [)] Rest frequency. [(] _[c]_ [)] Upper energy level. [(] _[d]_ [)] Einstein coefficient for spontaneous
emission from upper _u_ to lower _l_ level. [(] _[e]_ [)] Half-power beam width. For the IRAM sources it was calculated following Eq. 1 in
```
http://www.iram.es/IRAMES/telescope/telescopeSummary/telescope_summary.html.

```

Table 2: Line parameters for the nine measured CS isotopologue transitions in the +50 km s _[−]_ [1] Cloud.


Isotopologue Transition � _T_ mb dV Peak velocity FWHM _T_ [peak] mb _τ_ _[c]_

[K km s _[−]_ [1] ] [km s _[−]_ [1] ] [km s _[−]_ [1] ] [K]


13 C 34 S _d_ 2–1 1.25 _±_ 0.12 48.44 _±_ 0.92 20.99 _±_ 2.24 0.06 _±_ 0.005       13 CS 2–1 23.28 _±_ 0.28 46.94 _±_ 0.12 22.28 _±_ 0.29 0.98 _±_ 0.01 0.08 [+0] _−_ 0 _[.]_ _._ [05] 04
C [34] S 2–1 32.61 _±_ 0.41 46.45 _±_ 0.13 23.07 _±_ 0.32 1.33 _±_ 0.02    C [33] S 2–1 7.73 _±_ 0.31 47.05 _±_ 0.45 27.61 _±_ 1.14 0.26 _±_ 0.01    CS [+] 2–1 250.00 _±_ 6.66 48.10 _±_ 0.11 27.56 _±_ 0.51 8.52 _±_ 0.16 1.9 [+1] _−_ 0 _[.]_ _._ [1] 8
CS _[−]_ 2–1 -37.62 _±_ 6.13 48.09 _±_ 0.19 10.85 _±_ 0.82 -3.26 _±_ 0.32    C [34] S 3–2 21.19 _±_ 0.19 45.95 _±_ 0.09 22.39 _±_ 0.22 0.89 _±_ 0.01 0.05–0.15
CS [+] 3–2 250.00 _±_ 14.22 47.87 _±_ 0.10 25.59 _±_ 0.61 9.18 _±_ 0.73 1.0–2.8

CS _[−]_ 3–2 -78.71 _±_ 14.69 48.45 _±_ 0.12 13.97 _±_ 0.77 -5.29 _±_ 0.71    13 CS 6–5 2.39 _±_ 0.12 43.94 _±_ 0.43 18.61 _±_ 1.04 0.120 _±_ 0.005       C [34] S 6–5 3.32 _±_ 0.10 44.42 _±_ 0.26 18.51 _±_ 0.62 0.169 _±_ 0.005    

**Notes.** [(] _[c]_ [)] Peak opacity . [(] _[d]_ [)] a CH 3 OCH 3 (see Sect. 4.1 and Fig. 2) contribution was subtracted before performing a single Gaussian
fit to this line . [(][+][)] Positive component (in blue in Fig. 2) . [(] _[−]_ [)] Negative component (in green in Fig. 2).



2018, and references therein), and our lines with velocities around +60 km s _[−]_ [1] are associated with the envelope of
Sgr B2(N) (Wirström et al. 2010).


This massive star-forming region harbours five hot
cores, namely Sgr B2(N1–N5), with kinetic temperatures
ranging from _∼_ 130 to 150 K for N3–N5, between 150 and
200 K for N2, and between 160 and 200 K for N1, assuming LTE conditions in all these cases (Belloche et al. 2016;
Bonfand et al. 2017; Belloche et al. 2019). In addition, there
are 20 _∼_ 1.3 mm continuum sources associated with dense
clouds in Sgr B2(N) that exhibit a rich chemistry (SánchezMonge et al. 2017; Schwörer et al. 2019). Recently, Ginsburg et al. (2018) detected 271 compact continuum sources
at _∼_ 3 mm in the extended Sgr B2 cloud, thought to be
high-mass protostellar cores, representing the largest clus

Article number, page 4 of 16



ter of high-mass young stellar objects reported to date in
the Galaxy.


**4.** **Results**


In the following we first discuss the measured profiles towards the +50 km s _[−]_ [1] Cloud, and provide the equations
used to determine peak opacities and the carbon isotope
ratio (Sect. 4.1). Then we determine the [32] S/ [34] S isotope
ratio in two different ways (Sects. 4.1.1 and 4.1.2) from
the _J_ =2–1 lines of the different detected CS isotopologues.
The _J_ =3–2 opacities and the [34] S/ [33] S ratio are the topics of Sects. 4.1.3 and 4.1.4. Sgr B2(N) data are analysed
in Sect. 4.2, while the relation between the [32] S/ [34] S isotope
ratios from CS and the actual interstellar [32] S/ [34] S values is

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A



|Col1|CS J=|=2-1|Col4|1.4 C34S|S J=2-1|1|1.0 13CS J=2-1 0.3 C33S J=2-1|
|---|---|---|---|---|---|---|---|
|2.0<br>4.0<br>6.0<br>8.0||vr||0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>1.2<br>.<br>NCCHO<br>C2H5OH|||0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>0.0<br>0.1<br>0.2<br>.|
|2.0<br>.0|2.0<br>.0|2.0<br>.0|2.0<br>.0|2.0<br>.0|2.0<br>.0|2.0<br>.0|2.0<br>.0|


50 0 50 100150

1
v lsr [km s ]



13 C 34 S J=2-1


50 0 50 100150

1
v lsr [km s ]











50 0 50 100150

1
v lsr [km s ]



50 0 50 100150

1
v lsr [km s ]



50 0 50 100150

1
v lsr [km s ]



-0.05

|CS J=|=3-2|Col3|C34S J=|=3-2|0.20 C34S J=6-5 0.15|
|---|---|---|---|---|---|
||vr|0.4<br>0.6<br>0.8|||0.00<br>0.05<br>0.10<br>0.15<br>0.20<br><br>-0.03<br>0.00<br>0.03<br>0.05<br>0.07<br>0.10<br>0.12<br>0.15|
||vr|0.0<br>0.2|0.0<br>0.2|0.0<br>0.2|0.0<br>0.2|


50 0 50 100150

1
v lsr [km s ]



50 0 50 100150

1
v lsr [km s ]



13 CS J=6-5



8.0


6.0


4.0


2.0


0.0


-2.0


-4.0





50 0 50 100150

1
v lsr [km s ]



50 0 50 100150

1
v lsr [km s ]



-0.05



Fig. 2: From left to right and top to bottom: Observed line profiles of the _J_ =2–1 transitions of CS, C [34] S, [13] CS, C [33] S, and
13 C 34 S, the _J_ =3–2 transitions of CS and C 34 S, and the _J_ =6–5 transitions of C 34 S and 13 CS, in the +50 km s _−_ 1 Cloud
_′_ _′′_
(EQ J2000: 17 [h] 45 [m] 50 _._ 20 [s] _, −_ 28 _[◦]_ 59 41 _._ 1 ). Measured profiles are shown in black; the resulting Gaussian fitting is presented
in red. For the CS _J_ =2–1 and _J_ =3–2 lines, a double Gaussian fitting was performed to account for the self-absorbed
component (in green) in an attempt to retrieve the undisturbed emission line (in blue) (see Sect. 4.1). All the other lines
are well fitted by a single component. In the case of [13] C [34] S _J_ =2–1, the companion line is subtracted because of its
relatively strong emission and potential contamination. The dashed vertical lines denote the [13] CS _J_ =2–1 peak position
(46.94 km s _[−]_ [1], see Table 2). Dash-dotted red lines denote the redshifted velocity ( _v_ _r_ =63 km s _[−]_ [1] ) at which the CS _J_ =2–1
and _J_ =3–2 transition lines are not affected by self-absorption (see Sect. 4.1). Nearby lines likely observed are labelled.



the topic of Sect. 4.3. Generally, the analysis assumes that
lines with the same rotational quantum numbers, related
to different CS isotopologues, are co-spatial. We present a
summary of our results in Table 3.


_4.1._ _Peak_ _opacities_ _and_ _column_ _density_ _ratios_ _in_ _the_
+ _50 km s_ _[−]_ [1] _Cloud_


The CS emission lines observed towards the
+50 km s _[−]_ [1] Cloud are presented in Fig. 2. All lines
show peaks in agreement with the local standard of rest
(LSR) velocity of the system, _∼_ 50 km s _[−]_ [1] (Sandqvist et al.
2008; Requena-Torres et al. 2008). In addition to the CS
_J_ =2–1 isotopologue lines, there are probably weak features
of cyanoformaldehyde (NCCHO) and ethanol (C 2 H 5 OH)
at 96.4260958 GHz and 96.4273380 GHz, respectively, on
the blue-shifted side ( _∼_ 0 km s _[−]_ [1] ) of C [34] S; dimethyl ether
(CH 3 OCH 3 ) at 90.9375080 GHz or _∼_ 10 km s _[−]_ [1] on the
blue-shifted side dominates the [13] C [34] S spectrum. Those
molecules have been observed already in Sgr B2 (Zuckerman et al. 1975; Nummelin et al. 1998; Martín-Pintado
et al. 2001; Remijan et al. 2008; Belloche et al. 2013).

Moreover, the CS _J_ =2–1 and _J_ =3–2 line profiles show
double-peaked profiles, which are readily explained by selfabsorption, centred at the systemic velocity of the cloud in
the _J_ =2–1 transition and with a self-absorption marginally
redshifted (by _∼_ 0.4 km s _[−]_ [1] ) in the _J_ =3–2 transition. The



CS parameters allowed to vary freely and obtained from
single- or double-component Gaussian fitting are summarised in Table 2. They were obtained using a series of
Python codes, mainly within the lmfit package [4] .
As can be seen in Fig. 2, for the CS _J_ =2–1 and _J_ =3–2
lines, we have fitted a double Gaussian considering a positive (in blue) and a negative (in green) Gaussian component
each. Their parameters are summarised in Table 2, where
the uncertainties were taken directly from the lmfit package
(for details see Appendix D).
Given that CS _J_ = 2–1 and _J_ = 3–2 show double-peaked
profiles, while the rare isotopologues exhibit a single peak
in between, the CS lines are likely optically thick. This was
also suggested by Tsuboi et al. (1999) who find that CS
_J_ = 1–0 is moderately optically thick in this object, with
an opacity ( _τ_ ) of around 2.8. Then, we can further assume
as a first approximation that C [34] S _J_ = 2–1 is optically thin
in the expected case that [32] S/ [34] S _≫_ 3 (see Sect. 4.1.2 for
a confirmation of this assumption; see also Frerking et al.
(1980) and Corby et al. (2018)). In this case [13] C [34] S _J_ = 2–1
is definitively optically thin.
In the following we consider an excitation temperature
range of 9.4–300 K for our column density computations in
order to obtain conservative estimates. Our column density
values were calculated using Eq. 80 in Mangum & Shirley
(2015) assuming a filling factor of unity. We then deduce


4 `[https://lmfit.github.io/lmfit-py/intro.html](https://lmfit.github.io/lmfit-py/intro.html)`


Article number, page 5 of 16

_A&A_ _proofs:_ manuscript no. main


Fig. 3: EMoCA absorption spectra of four isotopologues of CS towards four positions in Sgr B2(N). The offsets (in units of
arcseconds, see Table 4 and Fig. 1) from the phase centre are indicated at the right of each row. The observed spectra are
shown in black and the synthetic spectra in magenta, purple, green, and blue, depending on the position. The synthetic
spectra were obtained by Thiel (2019). The dotted vertical lines indicate the velocities at which we determined the
isotopic ratios using the corresponding isotopologue. The velocities are listed in Table 4. The grey horizontal lines show
the continuum level.



from the integrated line intensities of C [34] S _J_ =2–1 and
13 C 34 S _J_ =2–1, converted to column densities, a 12 C/ 13 C
ratio of 22.1 _−_ [+3] 2 _[.]_ _._ [3] 4 [.] [This] [value] [is] [used] [in] [Equations] [1] [and] [2]
(denoted R C ), and it agrees with previous observations in

_∼_
the GC within the uncertainties ( 17-25; e.g. Frerking et al.
1980; Corby et al. 2018), and with the values derived from
many transitions of complex organic molecules (COMs) in
the hot core Sgr B2(N2) (Belloche et al. 2016; Müller et al.
2016), indicating that our approach is correct and confirming that C [34] S is indeed optically thin.


Article number, page 6 of 16



Assuming equal excitation temperatures (see Appendix B) and beam filling factors for [12] CS and [13] CS, the
13 CS _J_ =2–1 peak opacity _τ_ ( 13 CS) can then be determined
from



_T_ MB ( [12] CS) [1] _[ −]_ _[e]_ _[−][τ]_ [(] [13] [CS)R] [C]
_T_ MB ( [13] CS) [=] 1 _−_ _e_ _[−][τ]_ [(] [13] [CS)]




[CS)R] [C] 12

_[ −]_ _[e]_ _[−][τ]_ [(] C

1 _−_ _e_ _[−][τ]_ [(] [13] [CS)] _[,]_ [ R] [C] [=] 13 C



13 C _[.]_ (1)



However, as there is a self-absorption feature at the centre
of the [12] CS _J_ =2–1 and _J_ =3–2 profiles, we measure the line
temperatures of both [12] CS and [13] CS at a redshifted velocity, _v_ _r_ = 63 km s _[−]_ [1], where the line shape is not affected by

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A



self-absorption. We can then retrieve the opacity at the systemic velocity, assumed to be the [13] CS _J_ =2–1 peak velocity,
_v_ _sys_ =46.94 km s _[−]_ [1], by considering a Gaussian distribution.
First, we compute the opacities at _v_ _r_ in the following way:



_T_ MB ( [12] CS _v_ _r_ )

[1] _[ −]_ _[e]_ _[−][τ]_ [(] [13] [CS] _[vr]_ [)R] [C]
_T_ MB ( [13] CS _v_ _r_ ) [=] 1 _−_ _e_ _[−][τ]_ [(] [13] [CS] _[vr]_ [)]




[CS] _[vr]_ [)R] [C] 12

_[ −]_ _[e]_ _[−][τ]_ [(] C

1 _−_ _e_ _[−][τ]_ [(] [13] [CS] _[vr]_ [)] _[,]_ [ R] [C] [=] 13 C



13 C _[,]_ (2)



4.1.2. [32] S/ [34] S ratio from direct observations


As we have measured the [13] C [34] S _J_ =2–1 transition, we can
also obtain the [32] S/ [34] S ratio directly from


32 S _N_ ( [13] CS)

34 S [=] _N_ ( [13] C [34] S) _[.]_ (6)


Using this we obtain a [32] S/ [34] S _J_ =2–1 ratio of 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 [, con-]
sistent with the ratio obtained through the double-isotope
method in Eq. 5 and again indicating that our initial assumptions concerning line saturation were correct. In the
following, we use the latter value for our analysis because it
was determined in the most direct way. In order to estimate
the opacity of CS from C [34] S (see Sect. 4.1.3), we use this
C [32] S/C [34] S _J_ =2–1 ratio of 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 [as] [the] [sulphur] [isotopic]
ratio [32] S/ [34] S and call it R S .
To compare our results with those of Chin et al. (1996),
we also derived a sulphur ratio from the integrated intensities: [32] S _/_ [34] S _∼_ _I_ ( [13] CS) _/I_ ( [13] C [34] S). This results in a [32] S/ [34] S
value of 18.6 [+2] _−_ 1 _[.]_ _._ [2] 8 [.] [The] [differences] [between] [the] [column] [den-]
sity and integrated intensity ratios are due to the rotational partition functions, rotational constants, and Einstein A-coefficients for spontaneous emission of radiation
that slightly differ for the different isotopologues.


4.1.3. CS and C [34] S _J_ =3–2 opacities


Now we are able to determine the opacities of CS and C [34] S
_J_ =3–2 by proceeding in the same way as in Equations 2
and 4, but considering this time the sulphur ratio. Here,
as in Equation 2, we also assume equal excitation temperatures (see Appendix B) and beam filling factors, this time
for [12] CS and C [34] S _J_ =3–2:



4 _._ 26 _±_ 0 _._ 11 [1] _[ −]_ _[e]_ _[−]_ [22] _[.]_ [1] _−_ [+3] 2 _[.]_ _._ [3] 4 _[τ]_ [(] [13] [CS] _[v]_ _r_ [)] _._ (3)
0 _._ 24 _±_ 0 _._ 11 [=] 1 _−_ _e_ _[−][τ]_ [(] [13] [CS] _[vr]_ [)]


Here _T_ MB ( [12] CS _v_ _r_ ) and _T_ MB ( [13] CS _v_ _r_ ) are the mainbeam brightness temperatures of CS and [13] CS _J_ =2–1 at
_v_ _r_ . This results in _τ_ ( [13] CS _v_ _r_ ) = 0.02 _±_ 0.01, considering the
same uncertainties for the peak temperatures as those obtained by performing a single Gaussian fit in those lines.
We can now retrieve the opacity at the systemic velocity as


_τ_ ( [13] CS _v_ _sys_ ) = _e_ _[−]_ [(] _τ_ _[v]_ ( _[r]_ [13] _[−][v]_ CS _[sys]_ [)] _v_ [2] _r_ _[/]_ ) [2] _[σ]_ [2] _[,]_ (4)


where _σ_ is the full width at half maximum (FWHM)
of 13 CS _v_ _sys_ divided by �8 _ln_ (2) (FHWM/ ~~�~~ 8 _ln_ (2) =
9.46 _±_ 0.12 km s _[−]_ [1] ) and _v_ _sys_ =46.942 _±_ 0.118 km s _[−]_ [1] . We obtain _τ_ ( [13] CS _v_ _sys_ ) = 0.08 [+0] _−_ 0 _[.]_ _._ [05] 04 [.] [Multiplying] [this] [by] [R] [C] [,] [we]
obtain _τ_ ( [13] CS _v_ _sys_ )R C = _τ_ (CS _v_ _sys_ )=1.9 [+1] _−_ 0 _[.]_ _._ [1] 8 [,] [consistent] [with]
previous observations ( _τ_ (CS _v_ _sys_ ) _∼_ 2.8; Tsuboi et al. 1999).
The uncertainty on _v_ _sys_ corresponds to a 0.15% variation
in the _τ_ (CS _v_ _sys_ ) value in the worst case. Therefore, it is
ignored in the following.


4.1.1. A [32] S/ [34] S ratio obtained through the double isotope
method


As we have seen, CS must be moderately optically thick.
Then, the [32] S/ [34] S isotope ratios cannot be determined from
the observed _N_ ( [12] CS)/ _N_ (C [34] S) ratio. Instead, we can use
the column densities of [13] CS and C [34] S by realistically assuming that those lines are optically thin (see Sect. 4.1).
Therefore, we have derived the values for [32] S/ [34] S making
use of the carbon isotope ratio mentioned above, in the
following way:



_T_ MB ( [12] CS _v_ _r_ )

[1] _[ −]_ _[e]_ _[−][τ]_ [(C] [34] [S] _[vr]_ [)R] [S]
_T_ MB (C [34] S _v_ _r_ ) [=] 1 _−_ _e_ _[−][τ]_ [(C] [34] [S] _[vr]_ [)]




[S] _[vr]_ [)R] [S] 32

_[ −]_ _[e]_ _[−][τ]_ [(C] S

1 _−_ _e_ _[−][τ]_ [(C] [34] [S] _[vr]_ [)] _[,]_ [ R] [S] [=] 34 S



34 S _[.]_ (7)



32 S



12 C _N_ ( [13] CS)

13 C _N_ (C [34] S) _[.]_ (5)



32 S 12 C

34 S [=] 13 C



From Eq. 7, _τ_ (C [34] S _v_ _r_ )=0.01–0.03. Following the formalism
in Eq. 4, we obtain a _τ_ (C [34] S _v_ _sys_ ) value of 0.05–0.15. Entering this value and replacing _τ_ (C [34] S _v_ _sys_ )R _S_ by _τ_ (CS _v_ _sys_ ),
the CS _v_ _sys_ opacity results in a proper range of 1.0–2.8, considering throughout this calculation that this latter value
cannot lie below unity, since CS shows clear signs of optical thickness (see Sect 4.1). This is consistent with previous
observations (Tsuboi et al. 1999). All the derived opacities
are summarised in Table 2.


4.1.4. [34] S/ [33] S ratio from direct observations


The C [33] S _J_ =2–1 line was also observed. This offers the
possibility of obtaining the [34] S/ [33] S ratio for the GC. Since
C [33] S is less abundant than C [34] S, we can expect a clearly
optically thin profile. This ratio is easily obtained by



From Eq. 5 we obtain a [32] S/ [34] S _J_ =2–1 ratio of 16.3 [+3] _−_ 2 _[.]_ _._ [0] 4 [.]
By using the [13] CS and C [34] S _J_ =6–5 transitions, we obtain a
32 S/ 34 S _J_ =6–5 ratio of 15.8 +4 _−_ 3 _.._ 24 [. This agreement within the]
uncertainties can be taken as another argument in favour
of the low opacity of C [34] S and the subsequent validity of
our assumptions and calculations. If some of the C [34] S lines
in the rotational ladder were not optically thin, we would
expect different _N_ ( [13] CS)/ _N_ (C [34] S) ratios in the _J_ =2–1 and
6–5 transitions due to photon trapping leading to higher excitation temperatures in the more abundant isotopologue,
which is not observed.



We obtain a 34 S/ 33 S ratio of 4.3 _±_ 0.2 for the
+50 km s _[−]_ [1] Cloud. If we take the integrated intensities instead of the column densities, this ratio would be
4.2 _±_ 0.2, consistent with the lower end of the range of
ratios obtained by Chin et al. (1996), who derived [34] S/ [33] S
ratios between 4.38 and 7.53, irrespective of Galactic


Article number, page 7 of 16



34 S



(8)
_N_ (C [33] S) _[.]_



34 S _[N]_ [(][C] [34] [S][)]

33 S [=] _N_ [33]

_A&A_ _proofs:_ manuscript no. main



radius. Whether this is a first hint of a gradient remains to
be seen. Better data from the Galactic disc are necessary
to tackle this question.


Table 3: Summary for our carbon and sulphur column density ratio calculations in the +50 km s _[−]_ [1] Cloud.


12 C/ 13 C _a_ 32 S/ 34 S _b_ 32 S/ 34 S _c_ 34 S/ 33 S _d_
_J_ =2–1 _J_ =2–1/ _J_ =6–5 _J_ =2–1 _J_ =2–1


22.1 _−_ [+3] 2 _[.]_ _._ [3] 4 16.3 _−_ [+3] 2 _[.]_ _._ [0] 4 [/][15.8] _−_ [+4] 3 _[.]_ _._ [2] 4 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 4.3 _±_ 0.2


**Notes.** [(] _[a]_ [)] From _N_ (C [34] S)/ _N_ ( [13] C [34] S) _J_ =2–1 lines, as described
in Sect. 4.1. [(] _[b]_ [)] Through the double isotope method in Sect. 4.1.1.
( _c_ ) From direct observations in Sect. 4.1.2. ( _d_ ) Sect. 4.1.4.


_4.2._ _Modelling_ _the_ _Sgr_ _B2(N)_ _data_


Here we rely on the modelling of the absorption profiles of
the isotopologues of CS carried out by Thiel (2019) using
the EMoCA survey, following the same method as Thiel
et al. (2019). They used the software Weeds (Maret et al.
2011) to model the absorption profiles. Their work assumes
that all transitions of a molecule have the same excitation
temperature and that the beam filling factor is unity, which
is a reasonable assumption given that most absorption features are extended on scales of 15 _[′′]_ or beyond in the ALMA
maps (see Thiel et al. 2019, their Sect. 5.4), while the beam
size is 1 _[′′]_ _._ 6 (see Sect. 2.2, Fig. 1, and Table 1). The fitted
parameters were the column density, line width, and the
centroid velocity, under the assumption that the excitation
temperature is equal to the temperature of the cosmic microwave background (2.73 K).


We selected four continuum peaks inside Sgr B2(N)
(Fig. 1). We excluded the two strong continuum peaks at
which the main hot cores N1 and N2 are located because
at these positions the spectra are full of emission lines of
organic molecules (e.g. Bonfand et al. 2017) contaminating the carbon monosulfide absorption features. The offsets
to the centre of the observed field are (1 _[′′]_ _._ 8, 11 _[′′]_ _._ 1), (9 _[′′]_ _._ 3,
1 _[′′]_ _._ 8), (4 _[′′]_ _._ 8, 9 _[′′]_ _._ 3), and (6 _[′′]_ _._ 6, 3 _[′′]_ _._ 3) (see Fig. 1 and Table 4). The
observed absorption profiles and the corresponding Weeds
models for the four isotopologues and the four positions are
shown in Fig. 3. Using their results for the column densities,
we determined the isotopic ratios CS/C [34] S, [13] CS/ [13] C [34] S,
and C [34] S/ [13] C [34] S. We determined those ratios separately
for the envelope of Sgr B2(N) and some GC clouds along
the l.o.s. to Sgr B2(N), the latter with velocities lower than
_−_ 50 km s _[−]_ [1] . We only determine the ratio CS/C [34] S in those
cases where the absorption caused by CS is not optically
thick.


The resulting unweighted average values of the isotopic
ratios are listed in Table 4, namely a [32] S/ [34] S isotope ratio
of 16.3 _±_ 3.8 in the GC l.o.s. clouds towards Sgr B2(N) and
17.9 _±_ 5.0 in the envelope of Sgr B2(N). For this envelope we
obtain a [12] C/ [13] C ratio of 27.6 _±_ 6.5. It should be noted that
our uncertainties correspond to the standard deviation for
independent measurements, i.e. without dividing it by the
square root of the number of studied spectral components.


Article number, page 8 of 16



_4.3._ _Discussion_ _on_ _the_ _validity_ _of_ _using_ _C_ [32] _S/C_ [34] _S_ _as_ _a_ _proxy_
_for_ [32] _S/_ [34] _S_


Chin et al. (1996) estimated that sulphur fractionation is
marginal for CS isotopic ratios. If the bulk of the CS emission, which allows us to measure rare isotopes, arises from
the densest parts of the molecular clouds only, the heating
from the massive stars should inhibit significant fractionation (Chin et al. 1996). In that case, CS emission can be
used directly to determine sulphur isotope ratios from such

sources.
In their oxygen fractionation study, Loison et al. (2019)
analyse sulphur fractionation including CS. Some sulphur
fractionation is induced at low temperature by the [34] S [+]
+ CS _→_ S [+] + C [34] S reaction. To determine the potential
fractionation of sulphur, we used the network from Loison et al. (2019) in the +50 km s _[−]_ [1] Cloud, the l.o.s. clouds
towards Sgr B2(N) and the envelope of Sgr B2(N), with realistic physical conditions for these objects, in particular a
much higher value of the cosmic-ray ionisation rate (CRIR)
than the usual value in more local dense molecular clouds.
Some typical results are shown in Fig. 4 and are described
below.

In the simulations all elements with an ionisation potential below the maximum energy of ambient UV photons
(13.6 eV) are assumed to be initially in an atomic, singly
ionised state. We considered all sulphur in the S [+] form
without depletion, and we performed some tests to quantify
the effect of depletion, which is low (see below). Hydrogen,
with its high degree of self-shielding, is taken to be entirely
molecular. The initial abundances are similar to those in
Table 1 of Hincelin et al. (2011), the C/O elemental ratio
being equal to 0.7 in our study. We verified that the initial
state of carbon and nitrogen (C [+] versus CO and N versus
N 2 ) have very little influence on sulphur fractionation (less
than 4% for the typical ages considered: 10 [5] _[−]_ [6] years). The
estimation of the dense cloud ages is deduced from clouds
with similar density (10 [4] to a few 10 [5] cm _[−]_ [3] ) for which the
age is given by the best agreement between calculations
and observations for key species given by the so-called distance of disagreement (Wakelam et al. 2006). By key species
we mean species typically encountered in molecular clouds
such as HCN, HNC, CN, CH, C2H, _c_ –C3H, _c_ –C3H2, CO,
H 2 CO, CH 3 OH, NO, SO, CS, HCS [+], and H 2 CS (see e.g.
Wakelam et al. 2010; Agúndez & Wakelam 2013; Agúndez
et al. 2019).
For Fig. 4a, which represents conditions in the
+50 km s _[−]_ [1] Cloud, we adopted a density of 10 [5] cm _[−]_ [3] and a
CRIR of _ζ_ [H] [2] = 7 _×_ 10 _[−]_ [16] s _[−]_ [1] based on measurements in hot
cores of Sgr B2(N) by using COMs (Bonfand et al. 2019).
For Fig. 4b and c, which represent the conditions for the envelope of Sgr B2(N) and the l.o.s. clouds towards Sgr B2(N),
respectively, we chose a density of 10 [4] cm _[−]_ [3], an upper limit
for the volume density in those regions (see Thiel et al.
2019, their Table 12), in order to avoid possible UV heating
in our models. Due to this high density, we have adopted
a CRIR of _ζ_ [H] [2] = 3 _×_ 10 _[−]_ [15] s _[−]_ [1], i.e. one order of magnitude lower than the value usually obtained in the l.o.s. of
translucent and diffuse clouds towards the Galactic centre,
but within the range obtained for the nuclear _∼_ 100 pc of
our Galaxy (Indriolo et al. 2015; Le Petit et al. 2016). The
32 S/ 34 S isotope ratio chosen for each simulation is that obtained from our measurements, namely 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 [,] [17.9] _[±]_ [5.0,]
and 16.3 _±_ 3.8 for Figs. 4a, b, and c, respectively.

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A


Table 4: Isotopic ratios determined in the envelope of Sgr B2(N) ( [13] CS/ [13] C [34] S and C [34] S/ [13] C [34] S) and in GC clouds along
the line of sight to Sgr B2(N) (CS/C [34] S) using absorption lines of CS isotopologues.


Isotopic ratios determined in the envelope of Sgr B2(N)


∆ _x_ _[a]_ ∆ _y_ _[a]_ _V_ _LSR_ _N_ (C [34] S) _[b]_ _N_ ( [13] CS) _[b]_ _N_ ( [13] C [34] S) _[b]_ FWHM _[c]_ 13 CS/ 13 C 34 S C 34 S/ 13 C 34 S

[ _[′′]_ ] [ _[′′]_ ] [km s _[−]_ [1] ] [10 [12] cm _[−]_ [2] ] [10 [12] cm _[−]_ [2] ] [10 [12] cm _[−]_ [2] ] [km s _[−]_ [1] ]


1.8 11.1 71.6 70 _._ 0 _±_ 1 _._ 1 35 _._ 0 _±_ 1 _._ 2 2 _._ 5 _±_ 0 _._ 6 4.0 14 _._ 0 _±_ 3 _._ 3 28 _._ 0 _±_ 6 _._ 6

1.8 11.1 65.8 120 _._ 0 _±_ 1 _._ 6 90 _._ 0 _±_ 2 _._ 2 3 _._ 5 _±_ 0 _._ 7 5.0 25 _._ 7 _±_ 5 _._ 3 34 _._ 3 _±_ 7 _._ 1

1.8 11.1 61.1 65 _._ 0 _±_ 1 _._ 1 38 _._ 0 _±_ 1 _._ 4 2 _._ 6 _±_ 0 _._ 7 5.0 14 _._ 6 _±_ 4 _._ 1 25 _._ 0 _±_ 7 _._ 0


9.3 1.8 71.1 39 _._ 0 _±_ 0 _._ 9 30 _._ 0 _±_ 0 _._ 9 1 _._ 2 _±_ 0 _._ 4 4.0 25 _._ 0 _±_ 8 _._ 8 32 _._ 5 _±_ 11 _._ 4

9.3 1.8 63.8 200 _._ 0 _±_ 2 _._ 3 160 _._ 0 _±_ 2 _._ 1 8 _._ 2 _±_ 0 _._ 8 7.5 19 _._ 5 _±_ 2 _._ 0 24 _._ 4 _±_ 2 _._ 4


4.8 9.3 80.6 94 _._ 0 _±_ 3 _._ 1 74 _._ 0 _±_ 3 _._ 7 7 _._ 0 _±_ 1 _._ 9 9.0 10 _._ 6 _±_ 3 _._ 0 13 _._ 4 _±_ 3 _._ 7

4.8 9.3 61.3 280 _._ 0 _±_ 6 _._ 5 120 _._ 0 _±_ 4 _._ 7 8 _._ 0 _±_ 2 _._ 0 9.5 15 _._ 0 _±_ 3 _._ 8 35 _._ 0 _±_ 8 _._ 8


6.6 3.3 64.2 420 _._ 0 _±_ 4 _._ 5 280 _._ 0 _±_ 4 _._ 3 15 _._ 0 _±_ 1 _._ 5 12.5 18 _._ 7 _±_ 1 _._ 8 28 _._ 0 _±_ 2 _._ 7
average 17 _._ 9 _±_ 5 _._ 0 27 _._ 6 _±_ 6 _._ 5


Isotopic ratios determined in GC clouds along the line of sight to Sgr B2(N)


∆ _x_ _[a]_ ∆ _y_ _[a]_ _V_ _LSR_ _N_ (CS) _[b]_ _N_ (C [34] S) _[b]_ FWHM _[c]_ CS/C [34] S

[ _[′′]_ ] [ _[′′]_ ] [km s _[−]_ [1] ] [10 [12] cm _[−]_ [2] ] [10 [12] cm _[−]_ [2] ] [km s _[−]_ [1] ]


1.8 11.1 -73.3 26 _._ 0 _±_ 0 _._ 7 1 _._ 4 _±_ 0 _._ 5 3.5 18 _._ 6 _±_ 6 _._ 3

1.8 11.1 -81.2 45 _._ 0 _±_ 0 _._ 9 2 _._ 5 _±_ 0 _._ 6 5.0 18 _._ 0 _±_ 4 _._ 0

1.8 11.1 -104.2 58 _._ 0 _±_ 1 _._ 0 3 _._ 0 _±_ 0 _._ 6 5.0 19 _._ 3 _±_ 3 _._ 6


9.3 1.8 -82.5 16 _._ 0 _±_ 0 _._ 7 1 _._ 4 _±_ 0 _._ 4 2.5 11 _._ 4 _±_ 3 _._ 7

9.3 1.8 -92.6 20 _._ 0 _±_ 0 _._ 7 1 _._ 2 _±_ 0 _._ 5 2.5 16 _._ 7 _±_ 7 _._ 3

9.3 1.8 -104.7 63 _._ 0 _±_ 1 _._ 1 3 _._ 0 _±_ 0 _._ 7 6.5 21 _._ 0 _±_ 4 _._ 9


6.6 3.3 -71.8 65 _._ 0 _±_ 1 _._ 5 7 _._ 2 _±_ 0 _._ 8 5.5 9 _._ 0 _±_ 1 _._ 0

6.6 3.3 -79.8 29 _._ 0 _±_ 1 _._ 0 1 _._ 8 _±_ 0 _._ 6 4.0 16 _._ 1 _±_ 5 _._ 8
average 16 _._ 3 _±_ 3 _._ 8


**Notes.** [(] _[a]_ [)] The offset positions (∆ _x_, ∆ _y_ ) in units of arcseconds: (1.8, 11.1), (9.3, 1.8), (4.8,9.3), and (6.6, 3.3), correspond to K4,
K6 shell, K5 shell, and K6 shell _,_ a, in Fig. 1, respectively. See the caption to Fig. 1 and the green crosses in the image. [(] _[b]_ [)] Column densities
determined using Weeds. [(] _[c]_ [)] It is assumed that all isotopologues have the same FWHM . The average isotope ratios presented by
the lowest line of each panel are unweighted and provide the standard deviation of an individual measurement (without dividing
by the square root of the number of ratios).



Despite the limited literature on the subject, according
to models from Laas & Caselli (2019), the +50 km s _[−]_ [1] Cloud
is the only object in this study that could show signs of
sulphur depletion. However, for a depletion level of up to
90%, our models give results consistent with no sulphur depletion (which is the case for the results shown in Fig. 4)
because of the high temperatures that prevent any efficient
fractionation. It should be noted that if this cloud’s chemistry was determined in an earlier colder evolutionary period with possibly significant sulphur fractionation, CS, in
contrast to CO, could not accumulate because it would have
been destroyed by protonation as the dissociative recombination of HCS [+] leads mainly to S + CH and not to CS + H
(see Appendix A). Therefore, the memory effect for the CS
fractionation of such a dense cloud is small. For the l.o.s.
clouds towards Sgr B2(N) and the envelope of Sgr B2(N),
some runs (those shown in Fig. 4) give some sulphur fractionation when the gas temperature is low. This is due to
the combination of low density limiting the depletion of sul


phur and a high CRIR ( _ζ_ [H] [2] = 3 _×_ 10 _[−]_ [15] s _[−]_ [1] ). These characteristics induce an elevated concentration of S [+] in the
gas phase and then a [34] S enrichment through the [34] S [+] +
CS _→_ S [+] + C [34] S reaction (see Table 2 in Loison et al.
2019). It should be noted that the cases with some [34] S enrichment only concern low kinetic temperatures, and that
this relatively low enrichment will be even lower with some
sulphur depletion. This depletion is not well constrained in
the +50 km s _[−]_ [1] Cloud, the l.o.s. clouds towards Sgr B2(N),
and the envelope of Sgr B2(N), but it is high for some cold
dense molecular clouds (between 10 and 25 for the dark
cloud L1544 Barnard 1b (Fuente et al. 2016) and even up
to 200 for the dark cloud L1544 (Vastel et al. 2018).


The extremely low gas temperature cases in our models
(black lines in Fig. 4) are shown to demonstrate the dependence of sulphur depletion on gas temperature. Since
Galactic centre molecular cloud temperatures are higher
(Ginsburg et al. 2016), CS shows likely very little fractionation in [34] S for the purposes of this study and our measure

Article number, page 9 of 16

Fig. 4: Calculated abundance ratios of gas phase species C [32] S/C [34] S as a function of cloud age for conditions in (a) the
+50 km s _[−]_ [1] Cloud, (b) the envelope of Sgr B2(N), and (c) l.o.s. clouds towards Sgr B2(N) (see Sect. 4.2 for details). Low
values for the gas temperatures were chosen to illustrate an upper limit for fractionation. The vertical grey loci represent
values given by the most probable chemical age. The observational results from this study are illustrated as horizontal
light grey rectangles (including the uncertainties).



ments of the C [32] S/C [34] S ratio are a good approximation to
the [32] S/ [34] S ratio (even if the values thus obtained may
be slightly underestimated when considering the results of
the models). We can then expect a ≲10% increase in the
32 S/ 34 S ratios obtained for the +50 km s _−_ 1 Cloud in Fig. 4a
and slightly more for the l.o.s. clouds towards Sgr B(N) and
its envelope (≲15%), considering the conditions labelled in
red and blue in Figs. 4b and c.
Some measurements using the double-isotope ratio
method (see Sect. 4.1.1), which take the [12] C/ [13] C ratio into
account, may induce a bias since CS may show a nonnegligible fractionation into [13] C. There is no specific study
of the [13] C fractionation of CS, but the reactivity of C [+]
and C, in particular with CO and CN (but also with CS),
can induce an enrichment or depletion in [13] C of carbonaceous species including CS (Smith & Adams 1980; Roueff
et al. 2015). In that case, the good agreement between the
sulphur fractionation measurements using C [32] S/C [34] S and
the values obtained using the double-isotope method also
suggests a low [13] C fractionation of CS. This result is interesting and could initiate future studies on the modelling of
13 C fractionation in CS.


**5.** **Our** **results** **in** **the** **light** **of** **previous** **studies**


If we assume that the gradient proposed by Chin et al.
(1996) would also be valid in the Galactic centre region,
the [32] S/ [34] S ratio would decrease to values of 4.1 _±_ 3.1 at
the centre of our Galaxy, i.e. to a very low value, only 1/4
of the solar system ratio. This value is less than one fourth
of the value derived from integrated intensities in this work,
18.6 _−_ [+2] 1 _[.]_ _._ [2] 8 [.]
This difference can be explained in terms of the [12] C/ [13] C
ratios assumed in Chin et al. (1996), required to obtain
the [32] S/ [34] S ratio through the double-isotope method by
using the formalism of Eq. 5 (although using intensities instead of column densities). The [12] C/ [13] C ratios were derived from the relation found by Wilson & Rood (1994) of
12 C _/_ 13 C = (7 _._ 5 _±_ 1 _._ 9)( _D_ GC _/_ kpc) + (7 _._ 6 _±_ 12 _._ 9) that gives
a value of 7.6 [+12] _−_ 7 _._ 6 _[.]_ [9] for the Galactic centre, although the


Article number, page 10 of 16



authors claimed a value of _∼_ 20 near the Galactic nucleus
(Wilson & Rood 1994, Sect 5.1). This provides an idea of
the large uncertainty in this relation.
On the other hand, we are confident about our [12] C/ [13] C
ratio of 22.1 [+3] _−_ 2 _[.]_ _._ [3] 4 [(Sect.][ 4.1][) for] [two] [reasons:] [first,] [the agree-]
ment between the 32 S/ 34 S ratio obtained through the
double-isotope method (Sect. 4.1.1), which makes use of the
12 C/ 13 C ratio, and the 32 S/ 34 S ratio obtained directly from
13 CS/ 13 C 34 S (Sect. 4.1.2), i.e. independently of the carbon
ratio (this also indicates that the carbon fractionation is
low, as described in Sect. 4.3) and second, its proximity to
the ratio obtained through decades of observations in the
nuclear regions of our Galaxy ( [12] C/ [13] C = 17–25, Frerking
et al. 1980; Wilson & Rood 1994; Milam et al. 2005; Müller
et al. 2008; Corby et al. 2018), including LTE modelling
of complex organic molecules (Belloche et al. 2016; Müller
et al. 2016). There is no abrupt redirection in the [12] C/ [13] C
ratio (e.g. Henkel et al. 1985).
Recently, Corby et al. (2018) found 32 S/ 34 S ratios
mostly in the 5–10 range, based on C [32] S and C [34] S _J_ =1–0
absorption lines from diffuse clouds near the GC, with a
resolution of _∼_ 15 _[′′]_ . Considering their data in the –73 to –
106 km s _[−]_ [1] velocity range, corresponding to our GC l.o.s.
clouds towards Sgr B2(N), their observations reach values
between 6.6 _±_ 6 and 29 _±_ 14, consistent with our values between 9.0 _±_ 1.0 and 21.0 _±_ 4.9 (Table 4, lower panel).
In addition, Armijos-Abendaño et al. (2015), with a resolution of _∼_ 30 _[′′]_ –38 _[′′]_, found values of ≳22 and 8.7 _±_ 1.3 for
32 S/ 34 S isotope ratios in l.o.s. clouds towards Sgr A and
Sgr B2, respectively, consistent with previous estimations
(Frerking et al. 1980). However, their sulphur ratios were
obtained from OCS/OC [34] S, with OCS being potentially optically thick and OC [34] S spectra being badly affected by
band pass ripples, possibly providing only tentative detections. So we propose a more conservative lower limit for the
l.o.s. clouds towards Sgr A of _∼_ 10 and we suggest that the
uncertainty for their ratio in Sgr B2 was underestimated.
Both Corby et al. (2018) and Armijos-Abendaño et al.
(2015) employed integrated column density ratios, so we
should compare those measurements with our normal

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A



32 S/ 34 S isotope ratio estimation, that is 16.3 +2 _−_ 1 _.._ 17 [for] [the]
+50 km s _[−]_ [1] Cloud (as an approximation for their l.o.s.
clouds towards Sgr A) and 16.3 _±_ 3.8 for the l.o.s. clouds
towards Sgr B2 (see Table 4). Our data represent a significant improvement in terms of accuracy and precision with
respect to those previous observations. In addition, our estimation of 17.9 _±_ 5.0 for the envelope of Sgr B2(N) agrees
with both estimations for the +50 km s _[−]_ [1] Cloud and also
with previous calculations for the whole Sgr B2 region: _∼_ 16,
from the OCS/OC [34] S ratio, which is claimed to be derived
from optically thin lines (Goldsmith & Linke 1981).
Cutting-edge model calculations performed by
Kobayashi et al. (2011) relate sulphur isotope ratios
( [32] S/ [33] _[,]_ [34] _[,]_ [36] S) with metallicity ([Fe/H] [5] ). We can use this
relation in combination with a given metallicity gradient
along the Milky Way ([Fe/H] versus _D_ GC /kpc), to derive a
32 S/ 34 S versus _D_ GC /kpc relation and compare it with our
measurements.
Table 3 of Kobayashi et al. (2011) gives values for
the [32] S/ [34] S ratio as a function of [Fe/H] over the range
–0.5 _≤_ [Fe/H] _≤_ 0.0. We can derive the following relation by
interpolating their data:


32 S

34 S [=] _[ −]_ [19] _[.]_ [8] _[ ×]_ [ [Fe] _[/]_ [H] + 23] _[.]_ [2] _[.]_ (9)


Extrapolating up to [Fe/H] _≤_ 0.85, we can account for the
inner part of our Galaxy. Then, to relate [32] S/ [34] S to the
galactocentric distance, we can make use of the relations
obtained by Bovy et al. (2014) and Genovali et al. (2014),
valid for 5 _≤D_ GC /kpc _≤_ 14–19, respectively:


[Fe _/_ H] = ( _−_ 0 _._ 09 _±_ 0 _._ 01) _×_ ( _D_ GC _/_ kpc _−_ 8)+0 _._ 03 _±_ 0 _._ 01 _,_ (10)


[Fe _/_ H] = ( _−_ 0 _._ 06 _±_ 0 _._ 002) _× D_ GC _/_ kpc + 0 _._ 57 _±_ 0 _._ 02 _,_ (11)


and combine them with Eq. 9, to obtain the following relations:


32 S

34 S [= (1] _[.]_ [8] _[ ∓]_ [0] _[.]_ [2)] _[ ×]_ [ (] _[D]_ [GC] _[ −]_ [8 kpc) + 22] _[.]_ [6] _[ ∓]_ [0] _[.]_ [2] _[,]_ (12)


32 S

34 S [= (1] _[.]_ [2] _[ ∓]_ [0] _[.]_ [04)] _[ ×][ D]_ [GC] [ + 11] _[.]_ [9] _[ ∓]_ [0] _[.]_ [4] _[.]_ (13)


Equations (12) and (13) are plotted in Fig. 5 as hatchedshaded regions. As described in the legend, their extrapolations down to 2.53 kpc, following Inno et al. (2019, their
Figure 11), for both Eqs. 10 and 11, are indicated as hatched
regions only.
Additionally, we have accounted for iron abundances obtained from high-resolution near-infrared observations by
Davies et al. (2009) and Najarro et al. (2009) in the inner
30 pc of the Galaxy (see also Kovtyukh et al. 2019). Their
measurements are [Fe/H]=0.1 _±_ 0.2 and _−_ 0 _._ 06 _±_ 0.2, respectively, and we converted them to [32] S/ [34] S ratios of 21.2 _±_ 4
and 24.4 _±_ 4 by applying Eq. 9.
In summary, the relations of both Bovy et al. (2014)
and Genovali et al. (2014), through Eq. 9, give results closer
to those obtained from the double-isotope method (Eq. 5),


5 where [Fe/H] = log 10 ([ _N_ Fe / _N_ H ]) star - log 10 ([ _N_ Fe / _N_ H ]) sun



considering [12] C/ [13] C ratios by Yan et al. (2019) in combination with the [13] C [32] S/C [34] S ratios from Chin et al. (1996), as
can be seen in Fig. 5 (dotted blue line). In the nuclear region
of the Galaxy the Davies et al. (2009) and Najarro et al.
(2009) observations, when accounting for Eq. 9, are both
consistent with our measurements for the +50 km s _[−]_ [1] Cloud
and the envelope of Sgr B2(N).


**6.** **Discussion**


Among the four stable sulphur isotopes ( [32] S, [33] S, [34] S, and
36 S), 32 S is a primary nucleus which could be synthesised
in a single generation of massive stars. [32] S is mostly formed
during stages of hydrostatic and explosive oxygen-burning
(Wilson & Matteucci 1992) either preceding a Type II supernova event or in a Type Ia supernova, where two [16] O
nuclei collide to form [28] Si and [4] He, with these products subsequently fusing to yield [32] S. Type II supernovae synthesise
around ten times more [32] S than Type I supernovae, and
occur roughly 5 times as often as those of Type I (Hughes
et al. 2008). [33] S is partly a secondary isotope because it
can be formed by neutron capture from newly made [32] S if
the star not only has hydrogen and helium, but also carbon and oxygen in its initial composition (Clayton 2007).
It is synthesised in hydrostatic and explosive oxygen- and
neon-burning, also produced in massive stars. [34] S is partly
a secondary product because it can be formed from newly
made [32] S and [33] S by neutron capture, but also during oxygen burning in supernovae like the primary isotope, [32] S
(Hughes et al. 2008, and references therein). While the comprehensive calculations of Woosley & Weaver (1995) identify [32] S as a primary isotope, the same study also found
that [34] S is not a clean primary isotope; its yields decrease
with decreasing metallicity. However, they identify [33] S as a
primary isotope, in contradiction with later findings (Clayton 2007). [36] S is probably the only purely secondary sulphur isotope, being produced by s-process nucleosynthesis
in massive stars (Thielemann & Arnett 1985; Mauersberger
et al. 1996) and also by explosive C and He burning and
via direct neutron capture from [34] S, according to models
(Pignatari et al. 2016). [36] S could be the only S isotope not
only produced from massive stars but also, to a lesser extent, from AGB stars (Pignatari et al. 2016). However, lines
from C [36] S are too weak to be detected in this study. Massive stars, as well as Type Ib/c and II supernovae, appear
to slightly overproduce [34] S and underproduce [33] S compared
to [32] S, relative to the solar vicinity (Timmes et al. 1995).
The main result of our study is that the previous trend
observed by Chin et al. (1996) is broken near the centre of
our Galaxy. In other words, the increase in [32] S/ [34] S with
_D_ GC is not valid in the Galactic centre region. The values
of 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 [from] [the] [+][50 km s] _[−]_ [1] [Cloud] [and] [16.3] _[±]_ [3.8] [and]
17.9 _±_ 5.0 from the GC l.o.s. clouds towards Sgr B2(N) and
its envelope, respectively, contrast with the expected _∼_ 5–
10 regardless of the value of [12] C/ [13] C adopted (see Fig. 5)
when accounting for the [13] C [32] S/C [34] S ratios used in Chin
et al. (1996). It is also worth mentioning that our [32] S/ [34] S
isotope ratios derived from absorption lines from diffuse or
translucent clouds (Sgr B2(N)) are consistent with values
derived from emission lines from a prominent star-forming
region with dense molecular gas (the +50 km s _[−]_ [1] Cloud),
even though the chemistry for CS formation is completely
different in those regions (see Appendix A).


Article number, page 11 of 16

0



0 2 4 6 8
D GC [kpc]







Fig. 5: Sulphur isotope [32] S/ [34] S ratio variation when accounting for different carbon [12] C/ [13] C ratios as a function of
galactocentric radius, _D_ GC (e.g. Wilson & Rood 1994; Halfen et al. 2017; Milam et al. 2005; Yan et al. 2019) (for the
implemented [13] C [32] S/C [34] S ratios, see Chin et al. 1996). The [32] S/ [34] S to _D_ GC relations obtained from a linear leastsquares fit to weighted data (taken as 1/ _σ_, see Sect. 5) are shown and plotted as lines with different styles (see legend).
The [32] S/ [34] S ratios from this work are shown in orange, cyan, and light green. All ratios were gleaned from integrated
intensity ratios except for Sgr B2(N) (see Fig. 3), where our derived integrated column density ratios are used. Possible
differences between integrated column density ratios and line intensity ratios for the mean values in Sgr B2(N) fall inside
the error bars. For the case of the GC l.o.s. clouds towards Sgr B2(N), their distances are uncertain and they are believed
to be located within 1 kpc from the GC (see Sect. 3). As described in Sect. 5, the purple and yellow hatched-shaded loci
are derived from [Fe/H] vs _D_ GC relations obtained by Bovy et al. (2014) and Genovali et al. (2014), after accounting for
the models of Kobayashi et al. (2011); hatched-only loci correspond to an extrapolation of those relations, following Inno
et al. (2019). Using the same models, two [32] S/ [34] S ratios are included. These ratios are derived from iron abundances
measured in the central 30 pc of the Galaxy by Davies et al. (2009) and Najarro et al. (2009). A zoom on the results of
our study displayed in the left part of the figure is shown in Fig. C.1.



Frerking et al. (1980), even before the [32] S/ [34] S slope was
found, suggested values for [32] S/ [34] S of _∼_ 22 for the Galactic
centre. Therefore, the sulphur ratio seems to be constant,
or even increases with decreasing _D_ GC, within the inner
2.9 kpc of the Milky Way, in contrast to [12] C/ [13] C (e.g. Yan
et al. 2019), [14] N/ [15] N (e.g. Adande & Ziurys 2012), and
18 O/ 17 O (Wouterloot et al. 2008; Zhang et al. 2015). Intriguingly, [32] S/ [34] S behaves in a similar way to [16] O/ [18] O
(Polehampton et al. 2005), two nuclei with the bulk of their
formation taking place in massive stars ( _≥_ 10 M _⊙_ ) (Clayton
2007). This is surprising because [34] S is a tracer of secondary
processing as [13] C and [15] N, and therefore its abundance is
expected to increase in the same manner as observed for
those isotopes.


The fact that sulphur traces late evolutionary stages of
massive stars can give a clue to this difference in comparison
to C and N, which give information on CNO and helium
burning (Chin et al. 1996). Due to their short lives, the


Article number, page 12 of 16



star formation rate of massive stars can be traced by their
SN rate. Although the amount of [34] S is related to metallicity, which decreases with increasing galactocentric radius
especially in spiral galaxies (e.g. as observed from oxygen,
Henry & Worthey 1999), leading to a trend similar to C and
N, the production of [34] S is mostly related to SNe II, which
show a dip in the inner regions of our Galaxy and other
spiral galaxies (Anderson & James 2009), in good agreement with our higher than expected [32] S/ [34] S ratios in the
Galactic centre. However, these results are still under debate (see e.g. Hakobyan et al. 2009) and more observations
are needed.


Another argument in favour of the above could be that
metallicities traced by iron (Genovali et al. 2014; Kovtyukh
et al. 2019) instead of oxygen (Henry & Worthey 1999)
show a trend in good agreement with our observations (after
converting [Fe/H] to _D_ GC /kpc not only outside the central
2.53 kpc as in Fig. 5, but also in the GC region itself). This

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A



could also indicate a drop in the production of massive stars
at the Galactic centre compared to the rest of the Galaxy
and to less massive stars.
Our [32] S/ [34] S isotope ratio of 16.3 _−_ [+2] 1 _[.]_ _._ [1] 7 [can constrain opac-]
ity estimates of sulphur-bearing molecules in the Galactic
centre region and will considerably augment the confidence
in theoretical modelling of dense molecular clouds (e.g. Loison et al. 2019). Such results can then be used as initial inputs to reproduce hot core conditions (Charnley 1997; Viti
et al. 2004; Vidal et al. 2018).
Our new value for this ratio can also improve synthetic
spectral fitting and subsequent line identification, giving
better estimations to sulphur-bearing molecules. As a prime
example, we mention the recent work of Zakharenko et al.
(2019): the canonical ratio of [32] S/ [34] S = 22.5 (Frerking et al.
1980) is insufficient to reproduce their data, as can be seen
in their Fig. 4. Our value of 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 [leads] [to] [an] [enhance-]
ment of the [34] S isotopologue by a factor of 1.4 in their fit
(red line), better reproducing the lines detected at 99.512
and 99.520 GHz, and thus increasing the confidence in the
identification of CH 3 [34] SH in the hot core Sgr B2(N2).


**7.** **Summary** **and** **conclusions**


From our analysis of the emission line profiles of CS,
13 CS, C 34 S, 13 C 34 S _J_ =2–1, of CS and C 34 S _J_ =3–2, and
of [13] CS and C [34] S _J_ =6–5 in the +50km s _[−]_ [1] Cloud and CS,
13 CS, C 34 S, 13 C 34 S _J_ =2–1 observed in absorption towards
Sgr B2(N), we obtain the following main results:


**–** From measurements of the _J_ =2–1 lines of [12] C [34] S _J_ =2–1
and [13] C [34] S _J_ =2–1, we have obtained a [12] C/ [13] C isotope
ratio of 22.1 _−_ [+3] 2 _[.]_ _._ [3] 4 [near] [the] [centre] [of] [our] [Galaxy,] [in] [good]
agreement with previous estimations.
**–** For the +50 km s _[−]_ [1] Cloud we obtain a [34] S/ [33] S ratio of
4.3 _±_ 0.2, derived from C [34] S _J_ =2–1 and C [33] S _J_ =2–1 column densities. If we take the integrated intensities instead, this ratio would be 4.2 _±_ 0.2, consistent with the
lower end of the range of ratios obtained by Chin et al.
(1996), who derived [34] S/ [33] S ratios between 4.38 and
7.53, irrespective of Galactic radius. This might be a
first indication of a gradient with rising ratios as a function of increasing galactocentric distance, but data from
the Galactic disc have to become more precise for a definite result.

**–** From the _J_ =2–1 [13] CS and [13] C [34] S emission lines in the
+50 km s _[−]_ [1] Cloud, we derive, for the first time in a direct way, a [32] S/ [34] S column density ratio of 16.3 [+2] _−_ 1 _[.]_ _._ [1] 7 [,]
which is consistent with the [32] S/ [34] S ratio derived from
the _J_ =6–5 and _J_ =2–1 [13] CS and C [34] S isotopologues
when accounting for the above-mentioned [12] C/ [13] C ratio. Due to possible CS fractionation, the above ratio
might be underestimated by less than _∼_ 10%.
**–** We were able to directly obtain a 32 S/ 34 S ratio of
17.9 _±_ 5.0 for the envelope of Sgr B2(N), from the isotopologues [13] CS and [13] C [34] S in the _J_ =2–1 lines. Moreover, we have obtained a [32] S/ [34] S ratio of 16.3 _±_ 3.8 for
the GC l.o.s. clouds towards Sgr B2(N) through the CS
and C [34] S _J_ =2–1 isotopologue lines, when CS is not optically thick. Those ratios are prone to increase by up
to _∼_ 15%, when taking CS fractionation effects into account.



**–** Making use of the network presented in Loison et al.

(2019), we significantly improved CS fractionation estimations under conditions similar to those taking place
in massive molecular clouds, young stellar objects, and
diffuse or translucent cold molecular clouds.
**–** Comparing the sulphur ratios from this work with data
available in the literature that were obtained from larger
distances to Sgr A _[∗]_ and showed a decrease in [32] S/ [34] S
towards the Galactic centre, we can confidently establish
that this decrease terminates at least at a distance of
100 pc to Sgr A _[∗]_, at the position of Sgr B2(N) (Reid et al.
2009). This is different from trends previously reported
for [12] C/ [13] C, [14] N/ [15] N, and [18] O/ [17] O.
**–** Our improved [32] S/ [34] S isotope ratio will considerably
augment the confidence in theoretical modelling for hot
cores and in synthetic spectral fitting and subsequent
line identification, giving better constraints for the intensities of sulphur-bearing molecules.


Overall, our results suggest that processes occurring
at late evolutionary stages of massive stars could be better traced by sulphur isotopologues instead of the most
commonly studied CNO isotopes. Further observations targeting isotopologue ratios with distinct nucleogenesis like
32 34
S/ S (i.e. primary species versus secondary isotopologues) produced in advanced massive stars and SNe II can
lead to a better understanding of environmental discrepancies between the solar neighbourhood and the inner Galaxy.
This will allow, for example, a connection between metallicity gradients traced by iron (Genovali et al. 2014; Kovtyukh
et al. 2019) and observations of SNe II (Anderson & James
2009). The above could be also extrapolated to external
galaxies, especially with the advent of a new generation of
facilities.


_Acknowledgements._ We appreciate the important suggestions by
the anonymous referee that helped to express this research in a
clearer and more comprehensive way. PH is a member of and received financial support for this research from the International
Max Planck Research School (IMPRS) for Astronomy and Astrophysics at the Universities of Bonn and Cologne. This work makes
use of the following ALMA data: ADS/JAO.ALMA#2011.0.00017.S,
ADS/JAO.ALMA#2012.1.00012.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ. The interferometric data are available in the ALMA archive at
https://almascience.eso.org/aq/. This paper is partly based on data
acquired with the Atacama PathfinderEXperiment (APEX). APEX is
a collaboration between the Max Planck Institute for Radio Astronomy, the European Southern Observatory, and the Onsala Space Observatory. Part of this work is based on observations carried out with
the IRAM 30-meter telescope. IRAM is supported by INSU/CNRS
(France), MPG (Germany) and IGN (Spain). We acknowledge the
IRAM staff for the support and help offered during all the applicable
observational runs.


**References**


Adande, G. R. & Ziurys, L. M. 2012, ApJ, 744, 194
Adriaens, D. A., Goumans, T. P. M., Catlow, C. R. A., & Brown,
W. A. 2010, J. Phys. Chem. C, 114, 1892
Agúndez, M., Marcelino, N., Cernicharo, J., Roueff, E., & Tafalla, M.
2019, A&A, 625, A147
Agúndez, M. & Wakelam, V. 2013, Chemical Reviews, 113, 8710
Anderson, J. P. & James, P. A. 2009, MNRAS, 399, 559
Ao, Y., Henkel, C., Menten, K. M., et al. 2013, A&A, 550, A135
Armijos-Abendaño, J., Martín-Pintado, J., Requena-Torres, M. A.,
Martín, S., & Rodríguez-Franco, A. 2015, MNRAS, 446, 3842


Article number, page 13 of 16

_A&A_ _proofs:_ manuscript no. main



Bayet, E., Aladro, R., Martín, S., Viti, S., & Martín-Pintado, J. 2009,
ApJ, 707, 126
Bayet, E., Viti, S., Williams, D. A., & Rawlings, J. M. C. 2008, ApJ,
676, 978
Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628,
A10
Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016,
A&A, 587, A91
Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito,
C. 2013, A&A, 559, A47
Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27
Bonfand, M., Belloche, A., Menten, K. M., Garrod, R. T., & Müller,
H. S. P. 2017, A&A, 604, A60
Bovy, J., Nidever, D. L., Rix, H.-W., et al. 2014, ApJ, 790, 127
Charnley, S. B. 1997, ApJ, 481, 396
Chin, Y. N., Henkel, C., Whiteoak, J. B., Langer, N., & Churchwell,
E. B. 1996, A&A, 305, 960
Clayton, D. 2007, Handbook of Isotopes in the Cosmos (Cambridge
Planetary Science)
Corby, J. F., McGuire, B. A., Herbst, E., & Remijan, A. J. 2018,
A&A, 610, A10
Dale, J. E., Kruijssen, J. M. D., & Longmore, S. N. 2019, MNRAS,
486, 3307
Davies, B., Origlia, L., Kudritzki, R.-P., et al. 2009, ApJ, 694, 46
Drdla, K., Knapp, G. R., & van Dishoeck, E. F. 1989, ApJ, 345, 815
Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H.
S. P. 2016, Journal of Molecular Spectroscopy, 327, 95
Ferrière, K. 2012, A&A, 540, A50
Frerking, M. A., Wilson, R. W., Linke, R. A., & Wannier, P. G. 1980,
ApJ, 240, 65
Fuente, A., Cernicharo, J., Roueff, E., et al. 2016, A&A, 593, A94
Gaume, R. A., Claussen, M. J., de Pree, C. G., Goss, W. M., &
Mehringer, D. M. 1995, ApJ, 449, 663
Genovali, K., Lemasle, B., Bono, G., et al. 2014, A&A, 566, A37
Ginsburg, A., Bally, J., Barnes, A., et al. 2018, ApJ, 853, 171
Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50
Goldsmith, P. F. & Linke, R. A. 1981, ApJ, 245, 482
Goldsmith, P. F., Lis, D. C., Hills, R., & Lasenby, J. 1990, ApJ, 350,
186
González, M., Hijazo, J., Novoa, J. J., & Sayós, R. 1996, The Journal
of Chemical Physics, 105, 10999
Gravity Collaboration, Abuter, R., Amorim, A., et al. 2018, A&A,
615, L15
Greaves, J. S. & Williams, P. G. 1994, A&A, 290, 259
Güsten, R., Nyman, L. Å., Schilke, P., et al. 2006, A&A, 454, L13
Güsten, R., Walmsley, C. M., Ungerechts, H., & Churchwell, E. 1985,
A&A, 142, 381
Hakobyan, A. A., Mamon, G. A., Petrosian, A. R., Kunth, D., &
Turatto, M. 2009, A&A, 508, 1259
Halfen, D. T., Woolf, N. J., & Ziurys, L. M. 2017, ApJ, 845, 158
Hawkins, I. & Jura, M. 1987, ApJ, 317, 926
Henkel, C., Asiri, H., Ao, Y., et al. 2014, A&A, 565, A3
Henkel, C., Guesten, R., & Gardner, F. F. 1985, A&A, 143, 148
Henry, R. B. C. & Worthey, G. 1999, PASP, 111, 919
Hincelin, U., Wakelam, V., Hersant, F., et al. 2011, A&A, 530, A61
Hughes, G. L., Gibson, B. K., Carigi, L., et al. 2008, MNRAS, 390,
1710
Indriolo, N., Neufeld, D. A., Gerin, M., et al. 2015, ApJ, 800, 40
Inno, L., Urbaneja, M. A., Matsunaga, N., et al. 2019, MNRAS, 482,
83
Johansson, L. E. B., Olofsson, H., Hjalmarson, A., Gredel, R., &
Black, J. H. 1994, A&A, 291, 89
Kelly, G., Viti, S., Bayet, E., Aladro, R., & Yates, J. 2015, A&A, 578,
A70
Klein, T., Ciechanowicz, M., Leinz, C., et al. 2014, IEEE Transactions
on Terahertz Science and Technology, 4, 588
Kobayashi, C., Karakas, A. I., & Umeda, H. 2011, MNRAS, 414, 3231
Kovtyukh, V. V., Andrievsky, S. M., Martin, R. P., et al. 2019, MNRAS, 489, 2254
Laas, J. C. & Caselli, P. 2019, A&A, 624, A108
Le Petit, F., Ruaud, M., Bron, E., et al. 2016, A&A, 585, A105
Levshakov, S. A., Centurión, M., Molaro, P., & Kostina, M. V. 2006,
A&A, 447, L21
Lilenfeld, H. V. & Richardson, R. J. 1977, J. Chem. Phys., 67, 3991
Linke, R. A. & Goldsmith, P. F. 1980, ApJ, 235, 437
Lique, F., Spielfiedel, A., & Cernicharo, J. 2006, A&A, 451, 1125
Lis, D. C. & Goldsmith, P. F. 1990, ApJ, 356, 195
Lodders, K. 2003, ApJ, 591, 1220
Loison, J.-C., Wakelam, V., Gratier, P., et al. 2019, MNRAS, 485,
5777


Article number, page 14 of 16



Lucas, R. & Liszt, H. S. 2002, A&A, 384, 1054
Mangum, J. G. & Shirley, Y. L. 2015, PASP, 127, 266
Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011,
A&A, 526, A47
Martín, S., Aladro, R., Martín-Pintado, J., & Mauersberger, R. 2010,
A&A, 522, A62
Martín-Pintado, J., Rizzo, J. R., de Vicente, P., Rodríguez-Fernández,
N. J., & Fuente, A. 2001, ApJ, 548, L65
Mauersberger, R., Henkel, C., Langer, N., & Chin, Y. N. 1996, A&A,
313, L1
Mauersberger, R., Henkel, C., Wilson, T. L., & Harju, J. 1989, A&A,
226, L5
Mauersberger, R., Ott, U., Henkel, C., Cernicharo, J., & Gallino, R.
2004, A&A, 426, 219
Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff,
S. 2005, ApJ, 634, 1126
Millar, T. J. & Herbst, E. 1990, A&A, 231, 466
Mills, E. A. C. & Morris, M. R. 2013, ApJ, 772, 105
Molinari, S., Bally, J., Glover, S., et al. 2014, in Protostars and Planets
VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning,
125
Montaigne, H., Geppert, W. D., Semaniak, J., et al. 2005, ApJ, 631,
653
Morris, M. & Serabyn, E. 1996, ARA&A, 34, 645
Müller, H. S. P., Belloche, A., Menten, K. M., Comito, C., & Schilke,
P. 2008, Journal of Molecular Spectroscopy, 251, 319
Müller, H. S. P., Belloche, A., Xu, L.-H., et al. 2016, A&A, 587, A92
Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005,
Journal of Molecular Structure, 742, 215
Müller, S., Guélin, M., Dumke, M., Lucas, R., & Combes, F. 2006,
A&A, 458, 417
Najarro, F., Figer, D. F., Hillier, D. J., Geballe, T. R., & Kudritzki,
R. P. 2009, ApJ, 691, 1816
Nummelin, A., Bergman, P., Hjalmarson, Å., et al. 1998, ApJS, 117,
427
Pignatari, M., Herwig, F., Hirschi, R., et al. 2016, ApJS, 225, 24
Polehampton, E. T., Baluteau, J. P., & Swinyard, B. M. 2005, A&A,
437, 957
Reid, M. J., Menten, K. M., Zheng, X. W., Brunthaler, A., & Xu, Y.
2009, ApJ, 705, 1548
Remijan, A. J., Hollis, J. M., Lovas, F. J., et al. 2008, ApJ, 675, L85
Requena-Torres, M. A., Martín-Pintado, J., Martín, S., & Morris,
M. R. 2008, ApJ, 672, 352
Ritchey, A. M., Federman, S. R., & Lambert, D. L. 2011, ApJ, 728,
36
Roueff, E., Loison, J. C., & Hickson, K. M. 2015, A&A, 576, A99
Ruze, J. 1966, IEEE Proceedings, 54, 633
Sánchez-Monge, Á., Schilke, P., Schmiedeke, A., et al. 2017, A&A,
604, A6
Sandqvist, A., Larsson, B., Hjalmarson, Å., et al. 2008, A&A, 482,
849
Sandqvist, A., Larsson, B., Hjalmarson, Å., et al. 2015, A&A, 584,
A118
Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143
Schwörer, A., Sánchez-Monge, Á., Schilke, P., et al. 2019, A&A, 628,
A6
Smith, D. & Adams, N. G. 1980, ApJ, 242, 424
Thiel, V. 2019, PhD thesis, University of Bonn
Thiel, V., Belloche, A., Menten, K. M., et al. 2019, A&A, 623, A68
Thielemann, F. K. & Arnett, W. D. 1985, ApJ, 295, 604
Timmes, F. X., Woosley, S. E., & Weaver, T. A. 1995, ApJS, 98, 617
Tsuboi, M., Handa, T., & Ukita, N. 1999, ApJS, 120, 1
Uehara, K., Tsuboi, M., Kitamura, Y., Miyawaki, R., & Miyazaki, A.
2019, ApJ, 872, 121
van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., &
van Dishoeck, E. F. 2007, A&A, 468, 627
van Dishoeck, E. F. & Blake, G. A. 1998, ARA&A, 36, 317
Vastel, C., Quénard, D., Le Gal, R., et al. 2018, Monthly Notices of
the Royal Astronomical Society, 478, 5519
Vidal, T. H. G., Loison, J.-C., Jaziri, A. Y., et al. 2018, MNRAS, 469,
435
Viti, S. 2016, in IAU Symposium, Vol. 315, From Interstellar Clouds
to Star-Forming Galaxies: Universal Processes?, ed. P. Jablonka,
P. André, & F. van der Tak, 17–25
Viti, S., Collings, M. P., Dever, J. W., McCoustra, M. R. S., &
Williams, D. A. 2004, MNRAS, 354, 1141
Vollmer, B., Duschl, W. J., & Zylka, R. 2003, Astronomische
Nachrichten Supplement, 324, 613
Wakelam, V., Herbst, E., & Selsis, F. 2006, A&A, 451, 551

Humire et al. 2019: Sulphur and Carbon isotopes towards Sgr. A



Wakelam, V., Smith, I. W. M., Herbst, E., et al. 2010, Space Sci. Rev.,
156, 13
Wang, K. S., Bourke, T. L., Hogerheijde, M. R., et al. 2013, A&A,
558, A69
Wang, M., Henkel, C., Chin, Y. N., et al. 2004, A&A, 422, 883
Whiteoak, J. B. & Gardner, F. F. 1979, MNRAS, 188, 445
Wilson, T. L. & Matteucci, F. 1992, A&A Rev., 4, 1
Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191
Wirström, E. S., Bergman, P., Black, J. H., et al. 2010, A&A, 522,
A19
Woosley, S. E. & Weaver, T. A. 1995, ApJS, 101, 181
Wouterloot, J. G. A., Henkel, C., Brand, J., & Davis, G. R. 2008,
A&A, 487, 237
Yan, Y. T., Zhang, J. S., Henkel, C., et al. 2019, ApJ, 877, 154
Zakharenko, O., Lewen, F., Ilyushin, V. V., et al. 2019, A&A, 627,
A41
Zhang, J. S., Sun, L. L., Riquelme, D., et al. 2015, The Astrophysical
Journal Supplement Series, 219, 28
Zuckerman, B., Turner, B. E., Johnson, D. R., et al. 1975, ApJ, 196,
L99


**Appendix** **A:** **Chemical** **aspects**


In diffuse clouds, it has been suggested that CS forms
mainly by exothermic ion-molecule reactions of S [+] with
CH and C 2 (Drdla et al. 1989; van Dishoeck & Blake 1998).
However, these species require to be one order of magnitude
more abundant than currently observed in order to reproduce the observed quantities of CS (Lucas & Liszt 2002).
Currently, CS formation is believed to be dominated by the
exothermic reaction (Drdla et al. 1989; Lucas & Liszt 2002;
Montaigne et al. 2005; Laas & Caselli 2019)


HCS [+] + e _[−]_ _→_ CS + H _._ (A.1)


Subsequently, the dominant destruction route of CS is photodissociation, with destruction by He [+] being only significant in denser clouds (Drdla et al. 1989).
At higher densities, CS is mainly produced through
neutral-neutral reactions with atomic sulphur such as
(Fuente et al. 2016; Vidal et al. 2018; Laas & Caselli 2019)


S + CH _→_ CS + H _,_ (A.2a)


S + C 2 _→_ CS + C _,_ and (A.2b)


SO + C _→_ CS + O _._ (A.2c)


The dissociative recombination (DR) of HCS [+] becomes
the main path for CS destruction at low temperatures because HCS [+] is mainly produced through protonation of CS
and its DR leads mainly to S+CH and not to CS+H (Montaigne et al. 2005).
At higher temperatures, such as in hot cores and hot
corinos for which recent models suggest some changes in
sulphur chemistry (Vidal et al. 2018), CS is also destroyed
by atomic oxygen:


CS + O _→_ CO + S _._ (A.3)


This reaction is supposed to be negligible at low temperature due to the presence of a barrier (Lilenfeld & Richardson
1977; González et al. 1996). However the value of the barrier
is questionable (Adriaens et al. 2010) so that this reaction
may not be completely negligible at low temperature. Apart



from this reaction, and despite the recent advances in the
investigation of sulphur species in the interstellar medium
(Fuente et al. 2016; Vidal et al. 2018; Laas & Caselli 2019),
there are still large uncertainties with respect to CS and
HCS [+] chemistry.
Recent studies agree with the above reactions, but indicate that the dominant mechanism also depends on the cosmic ray ionisation rates (CRIR). At high CRIR, which may
be typical of the central parts of giant spiral galaxies, reactions (A.2c) and (A.3) dominate CS formation and destruction, but at lower CRIR the following reaction (route (A.4))
becomes dominant for the destruction of CS (Kelly et al.
2015; Viti 2016):


H 3 O [+] + CS _→_ HCS [+] + H 2 O _._ (A.4)


In hot cores and corinos, recent models suggest some deviations from the above-mentioned routes of sulphur chemistry
(Vidal et al. 2018). Specifically for CS, the main paths for
its formation and destruction continue being Eq. A.2c and
Eq. A.3, respectively. CS is initially destroyed by atomic
oxygen (Eq. A.3) both at 100 and 300 K, on timescales of
10 [4] and 10 [3] yr, respectively. Nevertheless, CS is then also
produced by


S H
S + CH 2 _→_ HCS _→_ CS 2 _→_ CS _._ (A.5)


**Appendix** **B:** **Excitation** **temperatures**


As mentioned in Sections 4.1 and 4.1.3, we assumed the
same excitation temperatures ( _T_ _ex_ ) in all our opacity calculations. This is argued by the low opacity of the isotopologues used to make such calculations.
Let us take an opacity ( _τ_ ) ranging between 0.04 and 0.15
(see Table 2) for both [13] CS _J_ =2–1 and C [34] S _J_ =3–2 with
which we obtained the opacity for [12] CS _J_ =2–1 and _J_ =3–2,
respectively. As can be seen in Fig. B.1, the variations in _T_ _ex_
within this range falls below 0.64 K. Considering that this
temperature will be inside an exponential as denominator
of a fraction and, furthermore, multiplied by the Boltzmann
constant (see Eq. 80 in Mangum & Shirley 2015), is reasonable to assume that _T_ _ex_ variations are negligible for the
scope of this work.
Calculations were done with a python version [6] of
RADEX (van der Tak et al. 2007), a statistical equilibrium
molecular radiative transfer code. Our inputs were a kinetic
temperature of 80, 200, and 400 K; 100 equally spaced values for the column density from 10 [11] to 10 [15] cm _[−]_ [2] ; and a H 2
volumetric density of 5 _×_ 10 [4] cm _[−]_ [3], in an attempt to emulate the conditions of the +50 km s _[−]_ [1] Cloud (see Section 3).
13 CS and C 34 S collision rates were taken from the Leiden
Atomic and Molecular Database (LAMDA, Schwörer et al.
2019), which in turn uses calculations made by Lique et al.
(2006).


**Appendix** **C:** **Zoom** **in** **for** **Figure** **5**


We plot our own data from Fig. 5 in a magnified way.
Data values for the l.o.s. clouds towards Sgr B2(N) and
its envelope are given in Table 4. The integrated intensity [32] S/ [34] S ratio of the +50 km s _[−]_ [1] Cloud (18.6 _−_ [+2] 1 _[.]_ _._ [2] 8 [) comes]
from Sect. 4.1.2.


6
see `[https://pypi.org/project/ndradex/](https://pypi.org/project/ndradex/)` for a full description. We have used the Grid RADEX run option.


Article number, page 15 of 16

_A&A_ _proofs:_ manuscript no. main



90


80


70


60


50


40


30


20


10


50



13 CS J=2-1, N = 10 11 10 [15] cm 2


0 1 2 3 4


C [34] S J=3-2, N = 10 [11] 10 [15] cm 2



Fig. C.1: Sulphur isotope [32] S/ [34] S ratio for the new data
presented in this paper as a function of galactocentric radius, _D_ GC .



25.0


22.5


20.0


17.5


15.0


12.5


10.0



0.0 0.2 0.4 0.6 0.8 1.0
D GC [kpc]



40


30


20


10


0 2 4 6 8 10


Fig. B.1: Excitation temperatures ( _T_ _ex_ ) as a function of
opacity ( _τ_ ) for [13] CS _J_ =2–1 (top) and C [34] S _J_ =3–2 (bottom). Molecular column densities range between 10 [11] and
10 [15] cm _[−]_ [2], and the kinetic temperature is 80, 200, and
400 K, represented by blue, green, and red lines, respectively. ∆( _T_ _ex_ ) refers to the _T_ _ex_ maximum variation between
_τ_ =0.04 and 0.15 (delineated by dashed vertical red lines).


**Appendix** **D:** **Gaussian** **fitting**


We preferred to use the lmfit package instead of Gildas [7],
for example, because the former has some improvements
related to uncertainty calculations. While both use minimisation, Simplex and Gradient methods, because of the use of
the Minimize package [8], lmfit has additional functions and
packages to ensure a proper uncertainty estimation ’even
in the most difficult cases’ [9] . We compared the uncertainties from Gildas and lmfit; those derived based on Gildas
are lower than those from lmfit by a small percentage (well
within the uncertainties), and at the same time the use of
Gildas results in a less successful fit in certain cases (not
shown). Given the rich available documentation for lmfit [10],
we opted for the lmfit-based fitting and associated uncertainty determination.


7 `[https://www.iram.fr/IRAMFR/GILDAS](https://www.iram.fr/IRAMFR/GILDAS)`
8 `[https://lmfit.github.io/lmfit-py/fitting.html#](https://lmfit.github.io/lmfit-py/fitting.html#the-minimize-function)`
```
the-minimize-function
```

9 `[https://lmfit.github.io/lmfit-py/](https://lmfit.github.io/lmfit-py/)`
10 `[https://lmfit.github.io/lmfit-py/](https://lmfit.github.io/lmfit-py/)`


Article number, page 16 of 16


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "GILDAS reduction, order-2 baseline, smoothing to 3 km/s; Gaussian fits (single or double for self-absorbed CS) with lmfit",
  "failed_quote": "The data were reduced with the GILDAS package and required minimal flagging, followed by a baseline subtraction of order two."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Tex vs opacity test",
  "failed_quote": "Calculations were done with a python version of RADEX (van der Tak et al. 2007)"
 }
]
```
