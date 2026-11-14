# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...684A...4U\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars ©ESO 2023
December 15, 2023

## Charting Circumstellar Chemistry of Carbon-rich AGB Stars [⋆]

### **I. ALMA 3 mm spectral surveys**


R. Unnikrishnan [1], E. De Beck [1], L.-Å. Nyman [1][,][ 3][,][ 4], H. Olofsson [1], W. H. T. Vlemmings [1], D. Tafoya [2], M. Maercker [1], S.
B. Charnley [5], M.A. Cordiner [6][,][ 7], I. de Gregorio [4], E. Humphreys [3][,][ 4], T. J. Millar [8], and M. G. Rawlings [9][,][ 10]


1 Department of Space, Earth and Environment, Chalmers University of Technology, SE-412 96 Gothenburg, Sweden
e-mail: `ramlal.unnikrishnan@chalmers.se`
2 Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory (OSO), SE-439 92,
Onsala, Sweden
3 Joint ALMA Observatory (JAO), Alonso de Córdova 3107, Vitacura 763-0355, Casilla 19001, Santiago, Chile
4 European Southern Observatory (ESO), Alonso de Córdova 3107, Vitacura 763-0355, Santiago, Chile
5 NASA Goddard Space Flight Center, 8800 Greenbelt Road, Greenbelt, MD 20771, USA
6 Solar System Exploration Division, NASA Goddard Space Flight Center, 8800 Greenbelt Road, Greenbelt, MD 20771, USA.
7 Department of Physics, Catholic University of America, Washington, DC 20064, USA
8 Astrophysics Research Centre, School of Mathematics and Physics, Queen’s University Belfast, University Road, Belfast, BT7
1NN, UK
9 Gemini Observatory / NSF’s NOIRLab, 670 N. A’ohoku Place, Hilo, Hawai’i, 96720, USA
10 East Asian Observatory / James Clerk Maxwell Telescope, 660 N. A’ohoku Place, Hilo, HI 96720, USA


Received 28 February 2023 / Accepted 4 December 2023


**ABSTRACT**


_Context._ Asymptotic giant branch (AGB) stars are major contributors to the chemical enrichment of the interstellar medium (ISM)
through nucleosynthesis and extensive mass loss. Direct measures of both processes can be obtained by studying their circumstellar
envelopes in molecular line emission. The relation between circumstellar molecular abundances and stellar elemental abundances is
determined by atmospheric and circumstellar chemistry. Most of our current knowledge of these, in particular in a C-rich environment,
is based on observations of the carbon star IRC +10 216.
_Aims._ We aim to obtain a more generalised understanding of the chemistry in C-rich AGB circumstellar envelopes by studying a

− − −
sample of three carbon stars, IRAS 15194 5115, IRAS 15082 4808, and IRAS 07454 7112, and observationally test the archetypal
status often attributed to IRC +10 216.
_Methods._ We performed spatially resolved, unbiased spectral surveys in ALMA Band 3 (85 − 116 GHz). We estimated the sizes of
the molecular emitting regions using azimuthally-averaged radial profiles of the line brightness distributions. We derived abundance
estimates using a population diagram analysis for molecules with multiple detected lines, and using single-line analytical calculations
for the others.
_Results._ We identify a total of 132 rotational transitions from 49 molecular species. There are two main morphologies of the brightness
distributions: centrally-peaked (CS, SiO, SiS, HCN) and shell-like (CN, HNC, C 2 H, C 3 H, C 4 H, C 3 N, HC 5 N, c-C 3 H 2 ). The brightness
distributions of HC 3 N and SiC 2 have both a central and a shell component. The qualitative behaviour of the brightness distributions
of all detected molecules, in particular their relative locations with respect to the central star, is the same for the three stars, and
consistent with those observed towards IRC +10 216. Of the shell distributions, the cyanopolyynes peak at slightly smaller radii than
the hydrocarbons, and CN and HNC show the most extended emission. The emitting regions for each species are the smallest for
IRAS 07454−7112, consistent with this object having the lowest circumstellar density within our sample. We find that, within the
uncertainties of the analysis, the three stars present similar abundances for most species, also compared to IRC +10 216. We find
that SiO is more abundant in our three stars compared to IRC+10 216, and that the hydrocarbons are tentatively under-abundant in
IRAS 07454−7112 compared to the other stars and IRC +10 216. Our estimated [12] C/ [13] C ratios match well the literature values for the
three sources and our estimated silicon and sulphur isotopic ratios are very similar across the three stars and IRC +10 216.
_Conclusions._ The observed circumstellar chemistry appears very similar across our sample and compared to that of IRC +10 216,
both in terms of the relative location of the emitting regions and molecular abundances. This implies that, to a first approximation, the
chemical models tailored to IRC +10 216 are, at least, able to reproduce the observed chemistry in C-rich envelopes across roughly
an order of magnitude in wind density.


**Key** **words.** stars: AGB and post-AGB – stars: mass-loss – stars: winds, outflows – circumstellar matter – submillimeter: stars –
astrochemistry


**1.** **Introduction**



⋆ Tables B.1 and B.2 are available in electronic form at the CDS,
along with the reprocessed ALMA cubes and line spectra, via anonymous ftp to `cdsarc.u-strasbg.fr` ( `130.79.128.5` ) or via `[http:](http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/)`
`[//cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/](http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/)` .



Stars of low-to-intermediate zero-age-main-sequence mass
(∼0.8 _M_ ⊙ < _M_ < 8 _M_ ⊙ ) populate the asymptotic giant branch
(AGB) during their late evolution, after the end of helium fusion


Article number, page 1 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



in their cores. In this phase, stars are characterised by an inert
carbon-oxygen core surrounded by shells of helium and hydrogen. Contraction of the core causes the outer layers of the star
to expand, resulting in cool, luminous giants ( _T_ eff ≲ 3000 K,
_L_ ∗ ∼ 10 [3] − 10 [4] _L_ ⊙, _R_ ∗ ∼ 100 _R_ ⊙ ; Herwig 2005). Microscopic
dust grains (with radius _a_ in the range 0.1 µm ≤ _a_ ≤ 0.5 µm,
e.g. Groenewegen 1997; Höfner 2008; Yasuda & Kozasa 2012)
formed in the cool, dense upper stellar atmosphere, are levitated
by pulsations, accelerated by radiation pressure, and push gas radially outwards through dust-gas momentum exchange (Höfner
2015). This causes extensive mass loss from the stellar surface. AGB mass-loss rates (hereafter MLR) range from 10 [−][8] to
10 [−][4] _M_ ⊙ yr [−][1], dominating the evolution on the AGB (e.g. Höfner
& Olofsson 2018). The winds of AGB stars are major sources of
gas and dust feedback into the interstellar medium (ISM, e.g.
Matsuura et al. 2009; Tielens 2005).
The mass loss creates an expanding envelope of chemically
rich material around the star, called the circumstellar envelope
(CSE). The radial density distribution of material in the CSE is a
tracer of the temporal variations in the mass loss. The elemental
compositions of gas and dust in the CSE reflect the composition
of the atmosphere of the star at the time of the ejection of the
circumstellar material.

Based on their atmospheric carbon-to-oxygen elemental
abundance ratio, AGB stars are classified into two main groups:
C-type (C/O > 1) and M-type (C/O < 1). AGB stars in the mass
range 1.5−4 _M_ ⊙ (at solar composition) evolve into C-type stars in
the absence of hot-bottom burning (Lattanzio et al. 1997), as the
carbon produced in the helium-burning layer is brought up to the
surface by convection (e.g. Di Criscienzo et al. 2016) during the
third dredge-up (Herwig 2005). The excess of carbon over oxygen for C-type stars allows a wide range of C-bearing species to
form in their CSEs, including long carbon chains and possibly
also PAHs (e.g. Cherchneff et al. 1992; Allain et al. 1997), as
well as carbonaceous dust (e.g. Kraemer et al. 2019; Sloan et al.
1998; Zijlstra et al. 2006). With 96 molecular species detected
in carbon star CSEs so far, compared to only around 34 species
found in oxygen-rich circumstellar environments, the CSEs of
C-type stars are generally richer in chemistry than those of their
M-type counterparts (Agúndez 2022; McGuire 2022; Cernicharo
et al. 2023a,b).
The advent of high-angular resolution mm/sub-mm interferometers like the Atacama Large Millimeter/submillimeter Array
(ALMA) has made it possible to explore the chemical complexity of AGB CSEs in unmatched detail. However, notwithstanding
these significant advances in instrumentation, much of our current knowledge of AGB circumstellar chemistry is still based on
observational results and modelling focussed on a single object,
the C-type IRC +10 216 (CW Leonis), owing primarily to its
proximity (120 − 190 pc), high MLR ( _M_ [˙] = 2 − 4 × 10 [−][5] _M_ ⊙ yr [−][1] ),
and molecular richness (e.g. Andriantsaralaza et al. 2022; Agúndez et al. 2017; He et al. 2008; Cernicharo et al. 2000; Cordiner
& Millar 2009; Groenewegen et al. 2012; Guélin et al. 2018;
Pardo et al. 2022; Patel et al. 2011; Tenenbaum et al. 2010;
Velilla-Prieto et al. 2019; Van de Sande et al. 2019).
Studies of the molecular chemistry in the CSE of IRC
+10 216, from single-dish spectral surveys (e.g. Cernicharo et al.
2000; Agúndez et al. 2012) to interferometric maps (e.g. Patel et al. 2011; Velilla Prieto et al. 2015a; Agúndez et al. 2017)
have revealed a host of information about circumstellar chemical
pathways and the physical structure of its CSE, including complex substructure within its molecular emitting shells. Radiative
transfer and chemical models of AGB CSEs which take into account the clumps and arcs seen in the emission have also been


Article number, page 2 of 114



presented (e.g. Cordiner & Millar 2009; Agúndez et al. 2017;
Van de Sande et al. 2018; Van de Sande & Millar 2022). Chemical modelling of the photochemistry in AGB CSEs has shed light
on their diverse chemical pathways (e.g. Li et al. 2014; Saberi
et al. 2019), and the effects of potential binarity (e.g. Siebert et al.
2022; Van de Sande & Millar 2022).
There have only been very few detailed investigations into
the circumstellar chemistry of C-rich AGB stars other than
IRC +10 216. Nyman et al. (1993); Woods et al. (2003) and
Smith et al. (2015) performed single-dish spectral surveys in
mm/sub-mm wavelengths towards selected C-type AGB stars.
A few studies of larger source samples in fewer molecules have
also been performed (e.g. Schöier et al. 2006, 2007, 2013; Massalkhi et al. 2019).
A large variety of molecules present in AGB CSEs have
rotational transitions at mm/sub-mm wavelengths. Analysis of
these lines can help constrain the physics and chemistry of these
sources. Therefore, spectral surveys in this wavelength regime
offer an ideal method to study both the chemical composition
and the kinematic and thermodynamic properties of AGB CSEs.
The single-dish spectral line survey by Woods et al. (2003)
observed the stars in our sample (Sect. 2) in the frequency range
85 − 266 GHz. However, to determine accurate molecular abundances, spatial information on the emitting regions is required.
Woods et al. (2003) used indirect methods such as modelling of
photodissociation radii and scaling of the known emitting-region
sizes for IRC +10 216 with the MLRs and expansion velocities
of the respective sources, to estimate the sizes of the molecular emitting regions of their stars. It is in this context that the
study of spatially-resolved data of a subset of C-type AGB stars,
as presented in this work, is highly relevant. Our interferometric observations make it possible to directly obtain the spatial
extents of the emitting regions for individual stars. Thus, along
with mapping the physical conditions like density and temperature across the CSEs, the observations presented will also help
provide better estimates of molecular abundances and isotopic
ratios.
This paper is the first in a series of planned publications,
which together aim to advance our understanding of the molecular chemistry in carbon-rich AGB CSEs by studying a sample of
stars other than IRC +10 216. The primary aim of this paper is to
present ALMA spectral surveys of three carbon stars, showcasing the large number of detected spectral lines and their emission
maps. Detailed non-LTE radiative transfer modelling is required
to constrain molecular abundances to the best possible accuracy,
and will be presented in a subsequent paper. In the current work,
we adopt a qualitative approach using simplistic LTE models to
obtain order-of-magnitude estimates of the abundances.
This paper is organised as follows. The sample is described
in Sect. 2. The details of the observations and data processing
procedures employed are described in Sect. 3. We present the
line identifications and abundance estimates in Sect. 4 and end
with a qualitative discussion of the chemical and morphological similarities and differences between the three stars, also in
comparison to IRC +10 216, in Sect. 5.


**2.** **The sources**


We have observed a sample of three C-type AGB stars, IRAS
15194−5115, IRAS 15082−4808, and IRAS 07454−7112, using ALMA. Owing to their high MLRs, they are expected to
present strong emission from a large variety of molecules. The
stars were chosen for their similar physical outflow properties
(see Table 1), both among themselves and in comparison to

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table 1: Source properties


Source Variable Distance [(] _[a]_ [)] MLR [(] _[b]_ [)] 12 C/ 13 C ( _c_ ) � sys [(] _[d]_ [)] � exp [(] _[e]_ [)] Period
Name (pc) ( _M_ ⊙ yr [−][1] ) (km/s) (km/s) (days)

IRAS 15194−5115 II Lup 690 (+130/−90) 1.6×10 [−][5] 6 −15.0 21.5 575 [(] _[g]_ [)]

IRAS 15082−4808 V358 Lup 1050 (±60) 2.7×10 [−][5] 35 −3.3 19.5 632 [(] _[h]_ [)]

IRAS 07454−7112 AI Vol 580 (+70/−60) 3.4×10 [−][6] 17 −38.7 13.0 511 [(] _[i]_ [)]

IRC +10 216 CW Leo 190 (±20) 3.0×10 [−][5] 45 [(] _[f]_ [)] −26.5 [(] _[f]_ [)] 14.5 [(] _[f]_ [)] 630 [(] _[j]_ [)]


**Notes.** [(] _[a]_ [)] distance estimates from Andriantsaralaza et al. (2022); [(] _[b]_ [)] mass loss rates from Woods et al. (2003), scaled to the listed distance estimates
from Andriantsaralaza et al. (2022); [(] _[c]_ [)] circumstellar [12] CO/ [13] CO ratios derived by Woods et al. (2003) from CO radiative transfer modelling;
( _d_ ) systemic velocities of the sources, from Woods et al. (2003); ( _e_ ) expansion velocities of the source CSEs, from Woods et al. (2003); ( _f_ ) The listed
12 C/ 13 C ratio, � sys, and � exp for IRC +10 216 are from Cernicharo et al. (2000); ( _g_ ) Feast et al. (2003); ( _h_ ) Whitelock et al. (2006); ( _i_ ) Whitelock et al.
(2006); [(] _[j]_ [)] Menten et al. (2012).



IRC +10 216. They possess expanding, largely spherical CSEs
with similar expansion velocities, sampling roughly an order of
magnitude in MLRs. They sample a broad range of [12] C/ [13] C ratios (Table 1), which may be due to differences in their nucleosynthetic histories. These properties make them ideal candidates for a comparative study of C-type CSEs. The MLRs listed
were obtained by scaling the values from Woods et al. (2003) to
the new distance estimates from Andriantsaralaza et al. (2022).
IRAS 15194−5115 (II Lup) is a J-type (Smith et al. 2015)
Mira variable with a pulsation period of 575 days (Feast et al.
2003). It is the third brightest carbon star at 12 µm, surpassed
only by IRC +10 216 and CIT 6 (Nyman et al. 1993). IRAS
15082−4808 (V358 Lup) is a Mira variable with a period of
632 days (Whitelock et al. 2006). It has an MLR comparable to
that of IRAS 15194−5115 and IRC+10126. IRAS 07454−7112
(AI Vol) is also a Mira variable with a pulsational period of 511
days (Whitelock et al. 2006). It has a lower MLR than the other
two stars, by approximately an order of magnitude. Based on
their MLRs, all three stars in our sample are currently expected
to be in the high-MLR phase at the end of their AGB evolution
(Vassiliadis & Wood 1993).


**3.** **Observations and data reduction**


_3.1._ _Observations_


Interferometric spectral survey observations in the frequency
range 85 − 116 GHz towards the three sources were carried out
with angular resolutions in the range 0 [′′] . 7 - 1 [′′] . 7 using the band
3 receiver (Claude et al. 2005) of the ALMA 12 m array in Cycle 2 (project code: 2013.1.00070.S; PI: Nyman, L. Å.). A detailed list of the observational and technical parameters is given
in Table 2. The maximum recoverable scale (MRS) of the observations ranges from 4.3 [′′] − 9.3 [′′], and the field of view from
54 [′′] − 63 [′′] . Each source was observed in five tunings, each with
four 1.875 GHz wide spectral windows, together covering the
entire Band 3 frequency range (Table 3). Based on the expected
line widths (Table 1), a spectral resolution of 0.49 MHz (∼1.6
km/s) was chosen for IRAS 07454-7112, while 0.98 MHz (∼3.2
km/s) was used for the other two stars, in order to resolve structure in the line profiles to a similar detail for the three sources.
We also observed the three stars and IRC +10 216 using
the Atacama Pathfinder Experiment telescope (APEX; Güsten
et al. 2006a). All stars were observed in the full bandwidths of
APEX bands 5 (159 − 211 GHz) and 6 (200 − 270 GHz). The
SEPIA receiver was used for the band 5 observations (Billade
et al. 2012; Belitsky et al. 2018). For band 6, the SHeFI receiver
(Vassilev et al. 2008) was used for IRAS 15194−5115, whereas



the PI230 receiver [1] was used for the other stars. Additionally,
IRAS 15194−5115 was also observed in APEX band 7 (SHeFI,
272 − 376 GHz). The Kelvin-to-Jansky conversion factor [2] for
the APEX lines is 34 (Band 5) and 40 (Bands 6 and 7), with
5 − 10% uncertainty in each case (Güsten et al. 2006b). Several
lines from the APEX surveys have been used in this work (Table B.2, Figs. C.109−C.185). The integrated intensities of these
lines are listed in Table B.2. The spectra of these lines are shown
in Figs. C.109−C.185. The full APEX surveys will be presented
in a forthcoming paper.


_3.2._ _Data reduction_


We retrieved the data stored in the ALMA Science Archive,
which were calibrated and imaged using the Common Astronomy Software Applications (CASA) package (McMullin et al.
2007) versions 4.3 and 4.4. The archival image cubes of IRAS
15194−5115 exhibited weak, extended, symmetric artefacts that
were not associated with the actual source structure (Fig. 1).
Also, for this source, some of the spectral windows in tunings a
and d (Table 3) showed intensity mismatches for the lines falling
within their overlapping frequency ranges. Such issues were
partly caused by the fact that the archival images were produced
using a now deprecated version of the CASA task clean, probably leading to inadequate cleaning at different spatial scales. In
addition, we found that the flux scales used for the calibration
of the archival data of several tunings of IRAS 15194-5115 and
IRAS 15082-4808 were obtained using a model of the solar system object Ceres that was poorly defined (see Butler 2012, and
also Appendix C in the CASA User Manual [3] ). This led us to
use quasars (Table 3), originally serving as phase calibrators, instead of Ceres to calibrate the flux scales of these tunings. The
spectral indices of these quasars were obtained by interpolating
the corresponding flux values from the ALMA calibrator source
catalogue [4] .
With this change, we manually re-calibrated the whole
dataset using CASA version 4.3.1. Water vapour radiometer data
was used to correct atmospheric variations at the time of observations. The continuum was estimated using a first order polynomial fit to the line-free channels, and subtracted from the cali

1 PI230 is a collaboration between the European Southern Observatory
(ESO) and the Max-Planck-Institut für Radioastronomie (MPIfR).
2 `[https://www.apex-telescope.org/telescope/](https://www.apex-telescope.org/telescope/efficiency/)`
```
efficiency/
```

3 `[https://casa.nrao.edu/docs/UserMan/casa_cookbook014.](https://casa.nrao.edu/docs/UserMan/casa_cookbook014.html)`
```
html
```

4 `[https://almascience.eso.org/sc/](https://almascience.eso.org/sc/)`


Article number, page 3 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


Table 2: Observational details


Source Date(s) of _B_ min [(] _[b]_ [)] _B_ max [(] _[c]_ [)] θ [(] _[d]_ [)] MRS [(] _[e]_ [)] _t_ on [(] _[f]_ [)] (min) PWV [(] _[g]_ [)] ∆v [(] _[h]_ [)]
_N_ ant [(] _[a]_ [)]
(IRAS) Observation (m) (m) ( [′′] ) ( [′′] ) (per tuning) (mm) (km/s)
15194−5115 2015 September 15,16 39 15.1 1574.4 0.7 − 0.9 4.9 9.6 1.4 3.2


15194−5115 [(] _[i]_ [)] 2016 September 22 37 15.1 3144.0 0.4 8.0 10.1 2.5 3.3


15194−5115 [(] _[ j]_ [)] 2016 May 14 41 15.1 639.6 1.3 13.3 10.1 2.7 3.3



15082−4808 2015 August 17 [(] _[k]_ [)] 37 43.3 1574.4 0.7 − 1.2 4.3 9.6 1.1 3.2

2015 September 9 [(] _[l]_ [)] 36 15.1 5.0 9.6 3.8


15082−4808 [(] _[i]_ [)] 2016 September 22 37 15.1 3144.0 0.4 8.0 31.3 2.4 3.3


15082−4808 [(] _[ j]_ [)] 2016 May 14 41 15.1 639.6 1.3 13.3 15.6 2.8 3.3



2015 June 7 [(] _[m]_ [)] 36 9.3 0.5
07454−7112 21.2 783.1 1.3 − 1.7 9.6 1.6

2015 June 13 [(] _[n]_ [)] 35 7.7 0.6



**Notes.** [(] _[a]_ [)] _N_ ant : Number of antennae used; [(] _[b]_ [)] _B_ min : minimum baseline; [(] _[c]_ [)] _B_ max : maximum baseline; [(] _[d]_ [)] θ: Major axis (FWHM) of median synthesised
beam; [(] _[e]_ [)] MRS: Maximum Recoverable Scale; [(] _[f]_ [)] _t_ on : time on source per tuning; [(] _[g]_ [)] PWV: Precipitable water vapour; [(] _[h]_ [)] ∆v: velocity resolution;
( _i_ ) Extended configuration from 2015.1.01271.S; ( _j_ ) Compact configuration from 2015.1.01271.S; ( _k_ ) Tunings a, b, e; ( _l_ ) Tunings c, d; ( _m_ ) Tunings a, b,
c; [(] _[n]_ [)] Tunings d, e.





20


20 10 0 -10 -20

RA offset (")



20


10


0


-10


-20



20 10 0 -10 -20

RA offset (")



40



Fig. 1: CS _J_ = 2 − 1 emission at 97.98 GHz towards IRAS
15194−5115, in a 3.3 km/s wide channel centred on the systemic velocity. Left: archival data, right: reprocessed data. The
emission shown has been capped at 50 mJy/beam to make the
low-level extended artefacts clearly visible. The white contours
are at 5 mJy/beam. Synthesised beams are shown as filled black
ellipses in the bottom left corner of each panel.


brated visibilities. Imaging was performed with the newer CASA
version 6.3.0-48, using the Multi-Scale deconvolving parameter
of the CASA task tclean (Cornwell 2008), and adopting a Briggs
weighting scheme with robust parameter 0.5. The clean masks
were set automatically using the auto-multithresh algorithm (Kepley et al. 2020). This significantly improved the image quality
over the archival image cubes (Fig. 1), and the extended artefacts present in the archival images of IRAS 15194−5115 were
successfully removed by the reprocessing.
The use of quasars instead of solar system objects as flux
calibrators implies an absolute flux calibration uncertainty of
∼ 5 − 10% (e.g. Goddi et al. 2019; Guzmán et al. 2019). In this
work, we adopt a conservative estimate of 10%, also considering the fact that the observation times of our data and the measurements from the calibrator catalogue often differ by several
days. With the reprocessing, the intensity mismatches between
the lines in the overlapping tunings for IRAS 15194−5115 were
reduced to within the absolute calibration uncertainty (10%). In


Article number, page 4 of 114



addition, given that the channel maps in tuning d have more significant residuals after cleaning and the channel maps in tuning a show a better signal-to-noise ratio, we estimated a 20%
calibration uncertainty for the lines from tuning d of IRAS
15194−5115.


Self-calibration was attempted in tunings with bright and
compact lines available, but did not result in any significant improvement in signal-to-noise ratio, and was hence not implemented. The observed continuum emission could not be used for
self-calibration due to its low intensity. The average beam sizes
and spectral resolution of the final processed data are listed in
Table 2. Figure 2 shows the variation in the achieved rms in the
different spectral windows, as a function of frequency. The atmospheric transmission in ALMA Band 3 is also shown, which
corresponds well to the increase in rms at higher frequencies.


0.08



95


90


85


80



0.06


0.04


0.02





90 100 110
Frequency (GHz)


Fig. 2: The rms noise in the spectra as a function of frequency.
Each point denotes the average rms in a spectral window centred on the corresponding frequency. The black line is the atmospheric transmission at ALMA at 2 mm PWV.

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table 3: Observational setup and flux calibrators


LSB [(] _[a]_ [)] USB [(] _[b]_ [)]
Tuning Flux calibrator [(] _[c]_ [)]
(GHz) (GHz)


15194−5115 15082−4808 07454−7112

a 85.1 − 88.9 97.1 − 100.9 J1617−5848 [(] _[d]_ [)] J1514−4748 [(] _[d]_ [)] J0519−454
b 88.9 − 92.6 100.9 − 104.6 J1617−5848 [(] _[d]_ [)] J1514−4748 [(] _[d]_ [)] Callisto
c 92.6 − 96.4 104.6 − 108.4 J1617−5848 [(] _[d]_ [)] Titan Callisto
d 96.4 − 100.1 108.4 − 112.1 J1617−5848 [(] _[d]_ [)] Titan J0519−454
e 100.1 − 103.9 112.1 − 115.9 J1617−5848 [(] _[d]_ [)] J1514−4748 [(] _[d]_ [)] J0519−454


**Notes.** [(] _[a]_ [)] LSB: Lower side band; [(] _[b]_ [)] USB: Upper side band; [(] _[c]_ [)] Flux calibrator used in the manual reprocessing (see Sect. 3.2) of our dataset
(ADS/JAO.ALMA#2013.1.00070.S); [(] _[d]_ [)] For IRAS 15194−5115, the default flux calibrator Ceres was replaced with the quasar J1617-5848 in all
five tunings. For IRAS 15082−4808, Ceres was replaced by J1514-4748 in tunings a, b, and e. For IRAS 07454−7112, no tunings had Ceres
as the default flux calibrator. J1617-5848 and J1514-4748 were originally observed as phase calibrators for the corresponding tunings for IRAS
15194−5115 and IRAS 15082−4808, respectively.


_3.3._ _Data combination_







For IRAS 15194−5115 and IRAS 15082−4808, observations with higher spatial resolution (0 [′′] . 4) were available in the
ALMA archive (project code: 2015.1.01271.S, PI: Keller, D.),
but covering only the frequency ranges 87.27 − 90.97 GHz and
99.14 − 102.89 GHz. The details of this dataset are given in Table 2. This dataset includes observations with both more extended (hereafter high angular resolution dataset) and more compact (hereafter low angular resolution dataset) baseline configurations compared to our data (hereafter intermediate angular
resolution dataset). We therefore combined the corresponding
visibilities from this project with our observations to increase
the sensitivity to the emission on compact and extended spatial
scales. This helps to increase the MRS of the observations, enabling us to recover the weak, extended molecular emission on
large spatial scales which could have been filtered out due to
the lack of very short baselines in the intermediate resolution
data before combination, while also lowering the rms noise in
the combined maps. The data combination was performed using
the task concat in CASA version 6.3.0-48. Figure 3 shows the
combined visibilities towards IRAS 15082−4808, depicting the
extended and compact baseline coverages added.


As these two datasets were observed several months apart, it
can be argued that they might not be compatible due to a possible time variation of the sources related to (1) the evolution of
the ejected material and (2) changes in the molecular excitation.
We note that any spatial variation in the circumstellar gas distribution occurring during the interval between these observations
(≤ 1 yr) will be far below the spatial resolution of both datasets.

−
For example, in the case of IRAS 15194 5115, given the expansion velocity of 21.5 km/s at a distance of ∼696 pc (Table 1),
the increase in angular size in 1 year is only 6 mas, around two
orders of magnitude less than the angular resolution of the observations. In contrast, by comparing the line intensities from the
two epochs used in the data combination, we do detect line variability likely connected to the variability in the stellar radiation
field in two species, C 2 H and HC 3 N, for both IRAS 15194−5115
and IRAS 15082−4808. The observed variability is quantified in
Sect. 4.2, and its impact on our results is discussed in Sect. 5. We
still combine the two datasets for these lines, in order to trace the
spatial structure in as much detail as possible, while increasing
the uncertainty in the line intensities of these species by the observed percentage of variability.



Fig. 3: The _uv_ plane of the combined observations towards IRAS
15082−4808 in the frequency range 87.2 − 89.1 GHz. The data
from project 2015.1.01271.S has both long (orange) and short
(green) baseline configurations, which help to better recover the
compact and extended emission, respectively, compared to our
original observations.


**4.** **Analysis and results**


_4.1._ _Line detection and identification_


Continuum maps were produced from the line-free channels across the survey bandwidth (85-116 GHz) using multifrequency synthesis (Rau & Cornwell 2011). The continuum
emission is spatially unresolved for all three stars. The peak positions and total flux of the continuum maps are given in Table 4.
The continuum was then removed from the data to obtain the
continuum-subtracted line spectra.
Figure 4 shows an overview of the ALMA band 3 spectra
for all three stars. The full line-labelled ALMA Band 3 spectra of the three sources, extracted by integrating the intensity
in a circular aperture of 12.5 [′′] radius centred on the respective
continuum peaks, so as to recover emission from all molecules,
are presented in App. A. We used the Weeds (Maret et al. 2011)
package in GILDAS [5] to identify the emission lines. The Cologne


5 `[https://iram.fr/IRAMFR/GILDAS](https://iram.fr/IRAMFR/GILDAS)`


Article number, page 5 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


10


5


0


0.4


0.2


0.0


85 90 95 100 105 110 115

Frequency (GHz)


4


2


0


0.2


0.1


0.0


6


4


2


0


0.2


0.1


0.0


85 90 95 100 105 110 115
Frequency (GHz)


Fig. 4: ALMA band 3 spectra extracted using a 12 [′′] . 5 radius aperture centred on the star, for IRAS 15194−5115 (top), IRAS
15082−4808 (middle), and IRAS 07454−7112 (bottom). The spectrum in the lower panel for each star is capped at a low flux
density limit to reveal the weaker emission lines.



Database for Molecular Spectroscopy (CDMS [6] ; Müller et al.
2005) catalogue was referred to for line identification. Splatalogue [7] (Remijan et al. 2007) was also used as an interface to


6 `[https://cdms.astro.uni-koeln.de](https://cdms.astro.uni-koeln.de)`
7 `[https://splatalogue.online](https://splatalogue.online)`


Article number, page 6 of 114



obtain spectral line parameters. We detect, above the 3σ noise
level, a total of 314 spectral emission features across the three
stars, out of which 311 could be identified and assigned to 132
known rotational transitions of 49 molecular species, including
various isotopologues (see Fig. A.1 and Table B.1). All detected
lines, along with the associated spectroscopic parameters and ob

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



Table 4: Details of continuum emission


Peak Position Flux
IRAS
RA DEC (mJy)
(h:m:s) (d:m:s)

15194−5115 15:23:05.048 ± 0.004 −51:25:58.95 ± 0.06 3.25 ± 0.04

15082−4808 15:11:41.453 ± 0.005 −48:19:58.95 ± 0.08 1.84 ± 0.04

07454−7112 07:45:02.456 ± 0.008 −71:19:45.79 ± 0.12 2.17 ± 0.03


**Notes.** The listed RA uncertainties are in seconds and DEC uncertain
ties are in arcseconds.


served integrated intensities towards the three stars are tabulated
in Table B.1. Figures in App. C show the brightness distributions
at the systemic velocity and the spectra of the detected lines.
Most of the detected spectral lines are thermal emission lines
from transitions in the vibrational ground states. However, some
of the lines we detect, including HCN ν 2 =2, _J_ =1−0, _l_ =0, and
ν 2 =1, _J_ =2−1, _l_ =1 are known to display maser emission towards
carbon stars, including IRAS 15082−4808 (e.g. Guilloteau et al.
1987; Smith et al. 2014; Menten et al. 2018; Jeste et al. 2022).
We find both these lines to be masering towards all three stars
in our observations as well, based on their extremely narrow
linewidth and significantly different line shapes in comparison
to other non-masering lines. These maser lines are not a target
of study in this paper and are not considered for the morphological or abundance analysis presented below. In addition, SiS
maser action has been reported for _v_ =0 rotational lines towards
IRC +10 216 using 3D radiative transfer modelling based on mm
observations (Fonfría et al. 2018). In the SiS lines that we detect in our ALMA/APEX surveys, there are no apparent maser
spikes. In this work, we have therefore assumed that all of the
observed SiS line emissions are of primarily thermal nature. We
will come back on this issue in a forthcoming radiative transfer
analysis. Two of the three unidentified features in our data, at
86.886 GHz and 100.407 GHz, present narrow line profiles (Fig.
C.108) indicating that they could be masers and/or originate in
the inner parts of the CSE.
Owing to the increased sensitivity and better coverage of spatial scales in the combined data (see Sect. 3.3), we detected several additional lines, including lines from C 5 H, C 6 H, C 2 S, and
l-C 4 H 2, which were not detected in the intermediate resolution
data alone. Further, the emission maps of several lines, including
those of HC 3 N, HCN, HNC, C 3 N, and their [13] C isotopologues,
were enhanced by the data combination (e.g. Figs. C.21, C.25,
C.27, C.34, C.69), owing to the same reasons as above.
We report the first detections of lines of [29] SiO, [30] SiO, [29] SiS,
30 SiS, Si 34 S, and C 33 S towards the three sources. The source
with the largest number of detections is IRAS 15194−5115,
presenting lines from 119 rotational transitions, compared to
the 56 and 67 of IRAS 15082−4808, and IRAS 07454−7112,
respectively (see Table B.1). This is largely due to the high
abundance of [13] C in its CSE which leads to a large number
of molecules containing [13] C atoms, most of which are not detected towards the other two stars. We report the first detection
of Si [13] CC, and doubly [13] C−substituted isotopologues of HC 3 N
towards IRAS 15194−5115, along with the long-chain hydrocarbons C 6 H, C 8 H, l−C 4 H 2, which have not been detected towards
this source in previous observations.


_4.2._ _Line Variability_


The two datasets used for data combination (Sect. 3.3) were
observed several months apart (see Table 2). Hence, to check for



potential variability, we compared spectra produced from a subset of visibilities that have the same _uv_ -coverage in both datasets.
This removes any difference in amplitudes caused by the larger
_uv_ -coverage of one of the datasets, and would reflect only timedependent amplitude variations, connected to the variability in
the stellar radiation field.
Owing to the 10% absolute calibration uncertainty of our
data (see Sect. 3.2), and the ALMA band 3 standard calibration uncertainty of 5% [8] for the high and low angular resolution datasets (see Sect. 3.3), we estimate a relative calibration
uncertainty of ∼11% between the two observations. For both
IRAS 15194−5115 and IRAS 15082−4808, we find differences
in line intensity greater than the relative calibration uncertainty
only for two species, C 2 H and HC 3 N. For IRAS 15194−5115,
we find a ∼ 15 − 20% change in the integrated line intensity of
the strongest hyperfine component of the C 2 H, _N_ =1−0 line, and
∼ 10−15% in the HC 3 N, _J_ =11−10 line. For IRAS 15082−4808,
we find a ∼25-30% change for C 2 H, _N_ =1−0, while for HC 3 N,
_J_ =11−10, the change is ∼ 10 − 15%. The phase of the variability
is also opposite for C 2 H and HC 3 N. See Sect. 5 for a brief discussion of the detected variability in comparison with that found
in IRC +10 216.


_4.3._ _Morphological diversity_


Estimation of the extents of the emitting regions is needed
in order to calculate molecular fractional abundances and constrain the chemical models. Fourteen species (see Table 5) were
found to have non-blended lines with sufficiently high signalto-noise ratios (≥ 3σ) in the channel maps to allow extracting
information about the spatial distributions of the emission towards all three stars by producing azimuthally-averaged radial
profiles (hereafter AARPs; see Sect. 4.3.2) of the line brightness
distributions.

Four of these species, HCN, SiO, SiS, and CS, have line
brightness distributions that peak close to the central star and
extend radially outwards (Fig. 5, top panel and Figs. C.10,
C.21, C.35, C.60). These molecules are termed centrally-peaked
species. These encompass the so-called parent molecules formed
in the stellar photosphere or the extended atmosphere, or
molecules formed through circumstellar chemistry in the inner layer of the CSE (see Millar & Herbst 1994; Cordiner &
Millar 2009; Agúndez et al. 2017, 2020). Eight species, C 2 H,
C 3 H, C 4 H, c-C 3 H 2, CN, C 3 N, HC 5 N, and HNC, present brightness distributions in the form of rings at the systemic velocity (e.g. Fig. 5, bottom panel and Figs. C.14, C.18, C.24, C.34,
C.53, C.61, C.101). Our observations indicate that these species
are distributed around the stars as hollow spherical shells with
widths and peak radii that vary between molecules and stars.
Hereafter we call these molecules shell species. The shell species
are daughter molecules formed in the external layers of the
CSE (see Agúndez et al. 2020) from centrally-peaking parent
molecules, by photodissociation (e.g. C 2 H and CN) or due to
photo-induced chemistry (e.g. HNC and HC 5 N), either directly
or through series of intermediate steps (e.g. Daniel et al. 2012;
Agúndez et al. 2017). Two species, HC 3 N and SiC 2, show compound brightness distributions that have both centrally-peaked
and shell characteristics (Fig. 6, top-left panel and Figs. C.45,
C.69). Maps of the emission at the systemic velocity for all the
above species are shown in App. C.


8 See the ALMA Technical Handbook, `[https://almascience.](https://almascience.eso.org/proposing/technical-handbook)`
```
eso.org/proposing/technical-handbook

```

Article number, page 7 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



10.0


5.0


0.0


-5.0


-10.0


10.0


5.0


0.0


-5.0



10.0 5.0 0.0 -5.0 -10.0


RA offset (")



400


350


300


250


200


150


100


50


0


35


30


25


20


15


10


5



-10.0

0

|IRAS 07454-7112<br>CN (1-0)|Col2|
|---|---|
|||


10.0 5.0 0.0 -5.0 -10.0


RA offset (")


Fig. 5: Examples of centrally peaked (top) and shell (bottom)
morphologies. Maps show the emission at the systemic velocity
from the HCN (1 − 0) line (top) and the CN (1 − 0, hyperfine
components stacked) line (bottom) towards IRAS 07454−7112.
Contours are at 3, 5, and 10 σ, where σ refers to the rms noise
in the emission maps (σ = 1.9 mJy/beam (HCN), 1.2 mJy/beam
(CN)). The red + denotes the stellar position (continuum peak).


4.3.1. Complex morphology in the CSEs of
IRAS 15194 − 5115 and IRAS 15082 − 4808


The systemic-velocity brightness distributions of HC 3 N,
SiC 2, HNC, and C 2 H towards IRAS 15194−5115 and IRAS
15082−4808 are shown in Fig. 6. The lower spatial resolution
in the maps of IRAS 07454−7112 limits the detection of any
similar sub-structure around this star. The maps in Fig. 6 have
been produced by stacking the systemic-velocity emission from
all detected transitions in the ALMA Band 3 for each of these
molecules. We regridded the line cubes to be stacked to ensure
that they have the same spectral resolution (3.3 km/s) and velocity grid, and used the software LineStacker (Jolly et al. 2020)
to stack the cubes to extract the rms-weighted mean emission of
the channels centred on the systemic velocity for each molecule.
No channel averaging was performed as it would lead to the substructure visible at the systemic velocity to be smeared out. The
spatial profiles obtained through radial cuts at different position
angles on these maps are shown in Figs. 7 and 8.


Article number, page 8 of 114



For IRAS 15194−5115, the maps in Fig. 6 reveal welldefined arc structures within the emitting shell at the same locations in the HC 3 N and SiC 2 maps. The approximate radial coincidence of the arcs seen in HC 3 N and SiC 2 emission towards
IRAS 15194−5115 can also be seen from the spatial profiles in
Fig. 7. However, the SiC 2 emission does not appear to fully trace
the HC 3 N emission towards the southwest part of the image, and
also around position angle (PA) ≈110 [◦] (Fig. 6, top-left panel).
This could be due to the higher sensitivity of the HC 3 N data as
compared to those of SiC 2, since we have an HC 3 N line in the
combined data set (Sect. 3.3) with better _uv_ -coverage than in the
case of SiC 2 . Clumpiness cannot be ruled out either as a potential cause of this difference, as there exist significant differences
in the chemical pathways of the two species. The C 2 H emission presents a main shell and a faint extended arc at larger radii
(∼10 [′′] ), from the north down to the northeast part of the map.
The same arc is traced by the HNC emission as well (Fig. 6,
bottom-left panel), though this is somewhat hidden in the figure
by the C 2 H contours. Notably, there is C 2 H and HNC emission
visible even in areas between the arcs of the HC 3 N and SiC 2
emission, towards IRAS 15194−5115 (Fig. 6, middle-left and
bottom-left panels). The maps of the lines of C 2 H and HNC have
higher sensitivity in comparison to the SiC 2 maps, as they are imaged from the combined data and thus recover emission on more
spatial scales.
In the case of IRAS 15082−4808, the SiC 2 emission appears
confined to only the main shell region of the HC 3 N map, and
does not trace the outer arcs seen in the HC 3 N emission (Fig. 6,
top-right panel). This can be due to the lower signal-to-noise ratio of the SiC 2 maps, as in the case of IRAS 15194−5115. However, C 2 H and HNC trace both the main shell and the arcs to the
southwest in the HC 3 N image (Fig. 6, middle-right and bottomright panels).


4.3.2. Azimuthally averaged radial brightness profiles


Despite the complex morphology seen for some of the
molecular line emissions, we use AARPs to study the radial
structure of the emission for all sources, as discussed below. This
is the strategy used also by Agúndez et al. (2017) in their study
of IRC +10 216.
To obtain the inner ( _R_ i ) and outer ( _R_ e ) radii of the lineemitting regions for different species, we constructed the mean
AARPs (App. D) for the 14 molecules listed in Table 5. Several
detected isotopologues of HCN, CS, SiO, and HC 3 N (H [13] CN,
13 CS, C 34 S, 29 SiO, H 13 CCCN, HC 13 CCN and HCC 13 CN)
present emission with signal-to-noise ratios >3σ in their channel maps. Since the photodissociation of these molecules occurs
throughout the broadband continuum (van Dishoeck 1988), and
is not limited to narrow frequency ranges of discrete UV lines,
their rarer isotopologues are expected to be present in the same
spatial range as the main counterparts. Hence, to generate the
mean AARPs for these species, we have averaged together emission from the detected lines of their non-blended isotopologues
where such averaging increases the signal-to-noise ratio of the
resulting profile.
Non-blended line cubes for a given species were convolved
to a common circular beam with a size equal to the largest major
axis among the individual beams. For each of these commonbeam cubes, the emission from within a range of ±20% of the
expansion velocity centred on the systemic velocity was averaged together to increase the signal-to-noise ratio as we are now
focussing on the overall size of the emitting shell, and not the
substructure within. The resulting maps were divided into suc

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



10.0


5.0


0.0


-5.0


-10.0


10.0


5.0


0.0


-5.0


-10.0


10.0


5.0


0.0


-5.0


-10.0



10.0 5.0 0.0 -5.0 -10.0


RA offset (")


10.0 5.0 0.0 -5.0 -10.0


RA offset (")


10.0 5.0 0.0 -5.0 -10.0


RA offset (")



10.0 5.0 0.0 -5.0 -10.0


RA offset (")


10.0 5.0 0.0 -5.0 -10.0


RA offset (")


10.0 5.0 0.0 -5.0 -10.0


RA offset (")



17


15


12


10


7


5


2


0


17


15


12


10


7


5


2


0


8


7


6


5


4


3


2


1


0



10.0


5.0


0.0


-5.0


-10.0


10.0


5.0


0.0


-5.0


-10.0


10.0


5.0


0.0


-5.0


-10.0



14


12


10


8


6


4


2


0


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


0



Fig. 6: Average brightness distributions, in a 3.3 km/s wide channel centred on the systemic velocity, of selected molecules towards
IRAS 15194−5115 (left panels) and IRAS 15082−4808 (right panels). The names of the species whose emissions are shown in
colour and contours are given at the bottom right corner of each panel in green and white, respectively. The synthesised beams of
the colour maps and contours are shown as filled and hollow ellipses, respectively, at the bottom left corner of each panel. Contours
are from 3σ to 15σ in intervals of 1σ. The σ values of the contour maps are, for IRAS 15194−5115: SiC 2 : 0.68 mJy/beam, C 2 H:
0.50 mJy/beam, and for IRAS 15082−4808: SiC 2 : 1.1 mJy/beam, C 2 H: 0.31 mJy/beam. The red + denotes the stellar position
(continuum peak). Red circles of radius 2 [′′] . 5, 5 [′′] . 0 and 7 [′′] . 5 are drawn on each map to facilitate comparisons.


Article number, page 9 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars









|10<br>0<br>25<br>.<br>00<br>.<br>50<br>.<br>25<br>.<br>00<br>.<br>5<br>0|HC3N|
|---|---|
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>|SiC2|
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>|C2H|
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>|HNC|
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||
|0<br>10<br>0.0<br>2.5<br>0.0<br>2.5<br>5.0<br>0<br>5<br>||


15 10 5 0 5 10 15
Position offset ( ) along PA=0°



|10<br>0 SurfaceBrightness(mJy/beam)<br>25<br>.<br>00<br>.<br>5<br>0<br>10<br>0|HC3N|
|---|---|
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)|SiC2|
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)||
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)||
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)||
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)|C2H|
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)||
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)|HNC|
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)||
|0<br>10<br>0.0<br>2.5<br>0<br>5<br>0<br>10<br>Surface Brightness (mJy/beam)||


15 10 5 0 5 10 15
Position offset ( ) along PA=90°



Fig. 7: Brightness distributions of HC 3 N, SiC 2, C 2 H, and HNC, in a 3.3 km/s wide channel centred on the systemic velocity for IRAS
15194−5115, along a line that intersects the star at PA=0 [◦] (left), and PA=90 [◦] (right). These profiles are extracted from radial cuts
using the stacked images shown in Fig. 6. The horizontal shaded region for each profile shows the rms noise of the corresponding
emission map.





10


0


0


0


0


15 10 5 0 5 10 15
Position offset ( ) along PA=0°



20


10


0


0


0


5



15 10 5 0 5 10 15
Position offset ( ) along PA=90°





0



Fig. 8: Same as Fig. 7, for IRAS 15082−4808.


cessive concentric circular rings of increasing radii, centred on
the continuum peak, with widths equal to the common restoring
beam. The emission within each shell was averaged to obtain
the azimuthally averaged brightness at the corresponding radius.
These average brightnesses are plotted against the radii of the
corresponding shells to produce one AARP per line. The uncertainty in the radial average for each shell corresponds to the rms
noise in the channel map divided by the square root of the number of beams in the respective shell. The mean of these individual
line AARPs was calculated for each species, weighted by the reciprocal of the squared uncertainty, to obtain the mean AARPs
of the species shown in Fig. 9.


As part of this method, we verified for each species, that
the different transitions of all isotopologues are emitted from the
same region around the central star. Fewer pixels are used in the
azimuthal averaging as we calculate the AARP closer to the centre. This increases the chance that noise at the innermost radii



Article number, page 10 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



might not be effectively suppressed, and could give rise to artefacts which need not correspond to actual emission. This is the
reason why the error bars increase in size towards the inner part
of the AARPs.

In order to estimate the radial extents of the emitting regions, the mean AARPs of each molecule were fit with Gaussian profiles. We believe that Gaussian fits to the AARPs provide a reasonable way to systematically estimate the extent of the
various emitting regions, to a first approximation. For instance,
Fig. 10 shows such fits for the HCN and CN AARPs for IRAS
07454−7112. The Gaussian fits to the AARPs of the 14 selected
species for all three sources are shown in App. D. The common
restoring beam was used to obtain the beam-deconvolved sizes
of the brightness distributions. For centrally-peaked morphologies, the peak position ( _R_ p ) of the emission, and hence the inner radius ( _R_ i ) is set to 0. In this case, the outer radius ( _R_ e ) is
estimated as the half width at half maximum (HWHM) of the
Gaussian fit to the mean AARP. In the case of shell emission,
the inner and outer radii of the emission regions are given by
the half maxima points on either side of the peak position of the
Gaussian fit to the AARP. For each molecule, the aperture from
which line spectra are extracted is set to a circular region with a
radius equal to the peak position + 3σ of the Gaussian fit to the
AARP (i.e., _R_ p + 2.5×HWHM) of the corresponding molecule,
in order to extract the maximum amount of emission while including only a minimum number of pixels with only noise and
no emission.

Figure 11 shows the radial extent estimates of the average
brightness distributions of each of the 14 analysed molecules,
calculated using the Gaussian fits to their mean AARPs as discussed above. The observed values in angular scale have been
converted to a spatial scale using the distances provided in Table 1. The values of _R_ i and _R_ e, and the corresponding uncertainties are tabulated in Table 5. We present the qualitative results of
the morphological analysis below, taking into account the calculated uncertainties.


4.3.3. Centrally-peaked species


The AARPs of the centrally-peaked species (SiO, SiS, CS,
HCN) show clear deviations from a Gaussian profile in both
IRAS 15194−5115 and IRAS 15082−4808, whereas they are fit
well using Gaussians for IRAS 07454−7112 (an effect of the
lower spatial resolution in this case; see Figs. D.1, D.2 (right),
and D.3 (left)). For IRAS 15194−5115 and IRAS 15082−4808,
the emissions from these molecules peak sharply at the centre,
and then gradually fall off at larger radii. Due to this, the Gaussian fits underestimate the radii of the actual emitting regions, as
can be seen from Figs. D.1, D.2 (right), and D.3 (left).
The SiO and SiS emission regions are roughly co-spatial
in each source. The CS emission region is more extended than
those of SiO and SiS, while the HCN emission is the most extended of the centrally-peaked species for all stars (see Fig. 9).


4.3.4. Shell species


Hydrocarbons: Within the calculated uncertainties (see Table 5), the shells of C 2 H and C 4 H peak at the same radii (Fig. 9)
and have the same widths (Fig. 11) for the three stars, possibly
with the exception of IRAS 15082−4808, where the C 2 H emission appears to extend further out than that of C 4 H by roughly
10% (see Table 5). The main hydrocarbon shells are of roughly
the same thickness (∼5500 AU) towards IRAS 15194−5115 and



IRAS 15082−4808, but there are cases of faint extended emission beyond the main shell up to around 9300 AU for IRAS
15194−5115 (Fig. 9). IRAS 07454-7112 presents much thinner
shells for the hydrocarbons, with a thickness of only ∼1300 AU
(Table 5). C 5 H, C 6 H, and C 8 H have also been detected towards
IRAS 15082−4808 and/or IRAS 15194−5115 in the combined
data, but the lines are too weak for any morphological information to be extracted.
Cyanides: In addition to the expected shell emission (see
e.g. Agúndez et al. 2017, for the HC 3 N shell distribution for
IRC +10 216), HC 3 N also shows significant central emission
components towards all three stars. This is discussed in more
detail in Sect. 4.3.5. In the cases of IRAS 15082−4808 and
IRAS 07454−7112, the shell-HC 3 N and HC 5 N emissions trace
roughly the same radial range (Fig. 11 and Table 5), and they
peak at around the same distance from the centre (Fig. 9). In the
case of IRAS 15194−5115 the HC 3 N emission appears to peak
at a slightly smaller radius than the HC 5 N emission, by ∼30%
(Fig. 9). However, this could be due to contamination from the
central component of the HC 3 N emission and the low signal-tonoise in the HC 5 N maps towards this star. Compared to C 2 H and
C 4 H, the HC 3 N and the HC 5 N emissions peak at slightly smaller
radii in all three CSEs, by an estimated 10 − 40% (Fig. 9).
In general, CN, HNC, and the hydrocarbons present the most
extended emission among the observed molecules. The peaks
of the CN and C 3 N emissions are located roughly at the outer
edges of the HCN and the shell-HC 3 N emissions, respectively
(Figs. 9, 11 and Table 5). The CN AARP of IRAS 15194−5115
shows a secondary peak at larger radii (∼11 [′′], Fig. 9), which is
not present in the other two stars. For IRAS 15194−5115, we
see weak emission structures at roughly the same location as the
CN secondary peak also in SiC 2, HNC, C 3 N, C 2 H, C 4 H, and
possibly also C 3 H (Fig. 9). The fact that these arcs are traced by
multiple species suggests that they are most likely the result of
density enhancements (see also Sect. 5). The radial range of the
HNC emission is roughly coincident with that of the C 2 H and
C 4 H emission for all three stars (Fig. 11).
SiC 2 : SiC 2 is the only silicon-bearing molecule out of the
species studied in this paper that emits in a shell, whereas the
others (SiO and SiS) are centrally peaked. The peak of the SiC 2
emission is close to those of the HC 3 N and HC 5 N emissions
for all three stars (Fig. 9). However, SiC 2 also presents a central component that is further discussed below. We note that towards IRAS 15082−4808, the SiC 2 AARPs show negative dips
at larger radii (see Fig. 9), which is evidence of interferometric filtering out of extended emission. A similar behaviour is
exhibited by C 4 H towards both IRAS 15194−5115 and IRAS
15082−4808, and possibly HC 5 N towards IRAS 15194−5115.


4.3.5. Central emission components of HC 3 N and SiC 2


For IRAS 15194−5115 and IRAS 15082−4808, HC 3 N and
SiC 2 show central components above the respective 3σ noise
levels (Fig. 9). We stress that what we call central emission need
not necessarily originate in the extended atmosphere, but can
instead emanate from roughly anywhere within a synthesised
beam (∼700 AU for IRAS 15194−5115 and ∼1000 AU for IRAS
15082−4808, see Table 2) centred on the star. The central components of these species can be seen in the spatial profile plots
shown in Figs. 7 and 8 also. We note that even though C 2 H appears to have a central component towards IRAS 15082−4808
(see Fig. 6, middle-right panel and Fig. 8), this is due to the contamination from the blended hyperfine components of C 2 H, and
potentially also weak lines of c-C 3 H 2 and C 6 H (see Fig. A.1). In


Article number, page 11 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


Fig. 9: Normalised azimuthally-averaged radial profiles (AARPs) of molecular line brightness distributions for IRAS 15194−5115

− −
(left), IRAS 15082 4808 (middle), and IRAS 07454 7112 (right). The vertical grey gridlines apply to the lower x-axis in cm units.



the case of IRAS 07454−7112, the angular resolution compared
to the size of the emitting region is too poor to draw any conclusions about the behaviour of the brightness distributions in the
inner part of the CSE. The possible formation mechanisms of
these central components are discussed in more detail in Sect. 5.


_4.4._ _Column density and rotation temperature estimates_


We produce population diagrams (also referred to as rotation
diagrams) to obtain the rotational temperature ( _T_ rot ) and the column density ( _N_ tot ) for molecules with detected lines from three
or more rotational transitions. We have made a first-order correction for the optical depths. The method is described in detail
in App. E.1. The minimum and maximum line optical depths for
each molecule for which we have made population diagrams are
listed in Table E.1. In this section, we present the column densities and rotation temperatures obtained from the population diagram analysis. All population diagrams produced are shown in
Figs. E.1 − E.18. The rotational temperatures and column densities thus obtained are tabulated in Table 6 and shown in Fig. 12.

As the centrally-peaked species are located close to the star,
they are expected to have relatively high rotational temperatures.


Article number, page 12 of 114



However, for all centrally-peaked species, except SiS, the population diagrams yield much lower temperatures than expected
(∼10 − 20 K; Fig. 12, left panel). This is most likely due to
three effects: (1) the limited range of energy levels covered (e.g.,
the highest energy level observed for HCN is at ∼42 K, see
Table B.2), where, in particular, high-excitation transitions are
missing, yielding only a very limited sampling of the excitation
properties, (2) the contribution from different lines may come
from different regions based on their excitation conditions, and
thus may not sample regions with the same temperature, and (3)
the assumption of optically thin lines is not always fulfilled. For
the SiS emission, where the energy range covered is larger, we
obtain a somewhat higher rotational temperature of ∼40 K.
The shell species often cover a large range of energy levels (e.g. 20 - 187 K for C 4 H, see Tables B.1 and B.2), and the
emission from different lines of a species come from roughly the
same region. They are therefore are expected to produce reliable
estimates of rotation temperatures. HC 3 N and HC 5 N yield rotation temperatures in the range 15 − 30 K, whereas C 4 H and C 3 N
give slightly higher temperatures, around 30 − 45 K. Based on
these results, we use rotational temperatures of 40 K and 20 K
for centrally-peaked and shell species, respectively, in the abundance estimates based on single lines in Sect. E.3. We also note

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table 5: Extents of the emitting regions of selected molecular species.


IRAS 15194−5115 IRAS 15082−4808 IRAS 07454−7112

Molecule

R i R e R i R e R i R e


[ [′′] ] [cm] [ [′′] ] [cm] [ [′′] ] [cm] [ [′′] ] [cm] [ [′′] ] [cm] [ [′′] ] [cm]


SiO 0.0 0.0 1.8(1) 1.8×10 [16] 0.0 0.0 1.3(1) 2.1×10 [16] 0.0 0.0 0.9(1) 7.6×10 [15]

SiS 0.0 0.0 1.7(1) 1.8×10 [16] 0.0 0.0 1.2(1) 1.9×10 [16] 0.0 0.0 0.5(1) 4.6×10 [15]

CS 0.0 0.0 2.2(1) 2.3×10 [16] 0.0 0.0 1.6(1) 2.4×10 [16] 0.0 0.0 1.5(1) 1.3×10 [16]

HCN 0.0 0.0 3.0(2) 3.1×10 [16] 0.0 0.0 2.1(1) 3.3×10 [16] 0.0 0.0 1.5(1) 1.3×10 [16]

CN 4.4(7) 4.6×10 [16] 9.7(7) 1.0×10 [17] 2.1(2) 3.3×10 [16] 5.8(2) 9.1×10 [16] 1.1(1) 9.9×10 [15] 3.7(1) 3.3×10 [16]

C 2 H 3.7(3) 3.9×10 [16] 7.8(3) 8.1×10 [16] 1.8(2) 2.8×10 [16] 4.9(2) 7.7×10 [16] 0.7(2) 6.1×10 [15] 2.6(2) 2.3×10 [16]

C 3 H 2.8(2) 2.9×10 [16] 7.0(2) 7.3×10 [16] – – – – 0.3(1) 2.6×10 [15] 1.9(1) 1.7×10 [16]

C 4 H 4.4(2) 4.6×10 [16] 7.9(2) 8.2×10 [16] 2.0(3) 3.1×10 [16] 4.4(3) 6.9×10 [16] 0.3(4) 2.6×10 [15] 2.6(4) 2.3×10 [16]

c-C 3 H 2 3.4(7) 3.5×10 [16] 8.4(7) 8.7×10 [16] – – – – – – – –
SiC 2 2.3(3) 2.4×10 [16] 6.7(3) 7.0×10 [16] 1.2(4) 1.9×10 [16] 3.7(4) 5.8×10 [16] 0.3(1) 2.6×10 [15] 2.1(1) 1.8×10 [16]

HC 3 N 0.8(3) 8.3×10 [15] 5.9(3) 6.1×10 [16] 0.6(2) 9.4×10 [15] 3.5(2) 5.5×10 [16] 0.4(1) 3.4×10 [15] 2.0(1) 1.8×10 [16]

C 3 N 4.5(2) 4.7×10 [16] 8.0(2) 8.3×10 [16] 2.2(1) 3.5×10 [16] 4.9(1) 7.7×10 [16] 0.9(1) 8.5×10 [15] 2.6(1) 2.3×10 [16]

HC 5 N 3.0(7) 3.1×10 [16] 7.0(7) 7.3×10 [16] 1.2(2) 1.9×10 [16] 3.8(2) 6.0×10 [16] 0.7(2) 6.1×10 [15] 2.0(2) 1.7×10 [16]

HNC 3.3(3) 3.4×10 [16] 8.0(3) 8.3×10 [16] 1.5(1) 2.4×10 [16] 5.0(1) 7.9×10 [16] 0.7(1) 6.1×10 [15] 2.5(1) 2.2×10 [16]


**Notes.** R i and R e denote the inner and outer radii, respectively. For the centrally-peaked species (SiO, SiS, CS, and HCN), we set the inner radii to
zero. The values in parentheses in the arcsecond columns show the uncertainty in the last decimal place. These are formal errors from the Gaussian
fits from which the radii were obtained. Conversion from angular to spatial distances has been done using the distances in Table 1.


Table 6: Rotation temperatures and column densities obtained using population diagrams.


IRAS 15194−5115 IRAS 15082−4808 IRAS 07454−7112
Molecule


_T_ rot (K) _N_ tot (cm [−][2] ) _T_ rot (K) _N_ tot (cm [−][2] ) _T_ rot (K) _N_ tot (cm [−][2] )


SiO 14(1) 1.0(1)×10 [16] 13(1) 7(1)×10 [15] 18(2) 9(2)×10 [15]

29
SiO 15(1) 3.9(6)×10 [14] 14(1) 2.1(4)×10 [14] 18(2) 2.9(5)×10 [14]

30 SiO 28(9) 9(7)×10 [13] – – – –
SiS 39(2) 1.0(1)×10 [16] 35(3) 1.3(2)×10 [16] 91(21) 8(2)×10 [16]

29 SiS – – 26(2) 8(1)×10 [14] 91(22) 2.5(7)×10 [15]

30 SiS – – – – 85(27) 1.7(7)×10 [15]

Si [34] S – – 43(6) 5(1)×10 [14] – –
SiC 2 23(1) 4.4(3)×10 [14] 30(2) 8(1)×10 [14] 42(2) 1.7(1)×10 [15]

CS 12(1) 3.9(6)×10 [16] 11(1) 6(1)×10 [16] – –
13 CS 15(1) 2.5(5)×10 [15] – – – –
C [34] S 18(2) 5(1)×10 [14] 15(2) 7(1)×10 [14] 17(2) 4.1(8)×10 [14]

HCN 9(1) 1.4(3)×10 [16] 8(1) 4.8(9)×10 [16] 10(1) 3.7(6)×10 [16]

H [13] CN 8(1) 9(2)×10 [15] 7(1) 2.9(5)×10 [15] 9(1) 9(2)×10 [15]

HNC 7(1) 7(1)×10 [13] – – – –
HC 3 N 15(1) 5(1)×10 [14] 20(1) 9(1)×10 [14] 23(1) 1.6(1)×10 [15]

C 3 N – – 27(3) 2.9(6)×10 [14] 46(2) 2.7(3)×10 [14]

HC 5 N – – 20(3) 8(6)×10 [14] 27(4) 5(2)×10 [14]

C 2 H 12(1) 8(2)×10 [15] 16(6) 6(3)×10 [15] – –
C 4 H 35(1) 8.6(7)×10 [14] 44(2) 6.1(7)×10 [14] 75(10) 2.6(6)×10 [14]


**Notes.** _T_ rot and _N_ tot stand for rotational temperature, and total column density, respectively. The values in parentheses indicate the uncertainty in
the immediately preceding digit. This is a formal uncertainty of the fit, and hence provides a measure of the quality of the population diagram. The
absolute uncertainty, in particular for the column density, is substantially larger, as discussed in the text.



that, in general, the obtained rotational temperatures are highest
for IRAS 07454−7112 (Fig. 12, left panel).


_4.5._ _Abundance estimates_


For the species for which we could produce population diagrams (see Table 6 and App. E), we calculated fractional abun


dances from the corresponding column densities, using Eq. E.6.
For all the other species, we obtain a rough estimate of the abundance analytically using Eq. E.7. These two methods are described in App. E.
The fractional abundances estimated towards our stars are
listed in Table 7 and shown in Fig. 13, along with the corresponding abundances for IRC +10 216 obtained from the literature. We also show the abundances normalised with those of


Article number, page 13 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


Table 7: Molecular fractional abundances.


X/H 2
Molecule


15194−5115 15082−4808 07454−7112 IRC +10 216

SiO 4.0(-6) 1.8(-6) 4.6(-6) 1.7(-7) [(1)]

29 SiO 1.6(-7) 5.2(-8) 1.4(-7) 1.0(-8) [(] _[b]_ [)]

30 SiO 3.8(-8) 6.5(-9) [(] _[a]_ [)] 2.3(-8) [(] _[a]_ [)] 7.1(-9) [(] _[b]_ [)]

SiS 4.2(-6) 3.0(-6) 2.3(-5) 2.9(-6) [(1)]

29 SiS 1.7(-7) [(] _[a]_ [)] 1.9(-7) 7.3(-7) 1.7(-7) [(] _[b]_ [)]

30 SiS – 3.9(-8) [(] _[a]_ [)] 5.0(-7) 1.2(-7) [(] _[b]_ [)]

Si [34] S 8.2(-8) [(] _[a]_ [)] 1.1(-7) 1.4(-7) [(] _[a]_ [)] 1.6(-7) [(] _[b]_ [)]

SiC 2 1.1(-6) 8.0(-7) 2.3(-6) 3.6(-7) [(2)]

Si [13] CC 2.5(-7) [(] _[a]_ [)] – – 8.0(-9) [(] _[c]_ [)]

CS 2.0(-5) 1.9(-5) 4.8(-6) [(] _[a]_ [)] 3.9(-6) [(1)]

13 CS 1.3(-6) 1.0(-7) [(] _[a]_ [)] 2.2(-7) [(] _[a]_ [)] 8.7(-8) [(] _[c]_ [)]

C [33] S 6.9(-8) [(] _[a]_ [)] 1.2(-8) [(] _[a]_ [)] 2.5(-8) [(] _[a]_ [)] 4.2(-8) [(] _[b]_ [)]

C [34] S 2.8(-7) 2.1(-7) 3.5(-7) 2.0(-7) [(] _[b]_ [)]

HCN 1.0(-5) 1.9(-5) 3.1(-5) 1.9(-5) [(1)]

H [13] CN 6.6(-6) 1.1(-6) 7.7(-6) 4.3(-7) [(] _[c]_ [)]

CN 8.5(-7) [(] _[a]_ [)] 1.0(-6) [(] _[a]_ [)] 5.9(-6) [(] _[a]_ [)] 1.8(-6) [(3)]

HNC 2.3(-7) 1.2(-7) [(] _[a]_ [)] 5.3(-7) [(] _[a]_ [)] 6.8(-8) [(4)]

HN [13] C 4.6(-8) [(] _[a]_ [)] – – 1.6(-9) [(] _[c]_ [)]

HC 3 N 7.8(-7) 7.4(-7) 2.2(-6) 7.1(-7) [(3)]

H [13] CCCN 7.9(-8) [(] _[a]_ [)] 1.4(-8) [(] _[a]_ [)] 5.2(-8) [(] _[a]_ [)] 5.3(-9) [(] _[c]_ [)]

HC [13] CCN 8.0(-8) [(] _[a]_ [)] 1.4(-8) [(] _[a]_ [)] 4.5(-8) [(] _[a]_ [)] 5.3(-9) [(] _[c]_ [)]

HCC [13] CN 8.0(-8) [(] _[a]_ [)] 1.4(-8) [(] _[a]_ [)] 4.9(-8) [(] _[a]_ [)] 5.3(-9) [(] _[c]_ [)]

H [13] C [13] CCN 1.5(-8) [(] _[a]_ [)] – – –
H [13] CC [13] CN 2.2(-8) [(] _[a]_ [)] – – –
HC [13] C [13] CN 1.6(-8) [(] _[a]_ [)] – – –
C 3 N 4.2(-7) [(] _[a]_ [)] 4.9(-7) 6.3(-7) 1.5(-7) [(5)]

CC [13] CN 1.1(-7) [(] _[a]_ [)] – – 1.1(-9) [(] _[c]_ [)]

HC 5 N 2.3(-7) [(] _[a]_ [)] 8.7(-7) 8.6(-7) 2.1(-7) [(5)]

C 2 H 2.7(-5) 8.5(-6) 3.1(-6) [(] _[a]_ [)] 1.3(-5) [(6)]

C 3 H 5.7(-8) [(] _[a]_ [)] – 3.2(-8) [(] _[a]_ [)] 2.2(-7) [(] _[d]_ [)]

C 4 H 3.6(-6) 9.3(-7) 4.2(-7) 1.1(-6) [(5)]

13 CCCCH 2.7(-7) [(] _[a]_ [)] – – 5.9(-9) [(] _[c]_ [)]

C [13] CCCH 3.1(-7) [(] _[a]_ [)] – – 5.9(-9) [(] _[c]_ [)]

CC [13] CCH 3.2(-7) [(] _[a]_ [)] – – 5.9(-9) [(] _[c]_ [)]

CCC [13] CH 2.8(-7) [(] _[a]_ [)] – – 5.9(-9) [(] _[c]_ [)]

c-C 3 H 2 1.8(-7) [(] _[a]_ [)] – – 5.6(-8) [(5)]


**Notes.** _a_ ( _b_ ) corresponds to _a_ × 10 _[b]_ . We estimate an uncertainty of a factor of 3-5 for the abundances estimated from population diagrams and
an order of magnitude for single-line estimates (Sect. 4.5). [(] _[a]_ [)] Abundances estimated from single lines. All other abundances (for the three stars
in the sample) are from population diagrams. IRC +10 216 abundances are from: [(1)] Agúndez et al. (2012), [(2)] Massalkhi et al. (2018), [(3)] Agundez
(2009), [(4)] Daniel et al. (2012), [(5)] Gong et al. (2015), and [(6)] De Beck et al. (2012). [(] _[b]_ [)] Calculated by scaling the abundances of the corresponding
main isotopologue by the relevant isotopologue ratio from He et al. (2008). [(] _[c]_ [)] Scaled from the corresponding [12] C isotopologue using a [12] C/ [13] C
ratio of 45 (Cernicharo et al. 2000). [(] _[d]_ [)] Obtained by scaling the column density from Agundez (2009) by the _f_ X / _N_ tot ratio of C 2 H, assuming C 3 H
and C 2 H to be cospatial.



IRC +10 216, for an easier source-to-source comparison, and
normalised to each star’s C [34] S abundance, to eliminate sourcespecific uncertainties on distance and MLR. We chose C [34] S in
particular, since the S and [34] S abundances are not expected to
vary between the sample stars, nor with respect to IRC +10 216
(Henry et al. 2012). Whereas we find similar CS abundances for
all of the stars, we note that Massalkhi et al. (2019) have reported a decreasing CS peak abundance for increasing density in
carbon-rich CSEs.

We have made first-order corrections for optical depths, that
are particularly significant for HCN, SiO and CS. However, the


Article number, page 14 of 114



estimated rotational temperatures are much lower than expected
for these centrally-peaked species (see Table 6 and Fig. 12, left
panel), and we therefore believe that for these species the reported abundances are lower limits.


The abundances of the shell species are in general comparable, within the uncertainties, in the three stars. Since extended emission appears to have been resolved out for SiC 2 and
C 4 H towards IRAS 15194−5115 and IRAS 15082−4808 (see
Sect. 4.3.4), the ALMA points in the population diagrams of
these species for these sources could be slightly underestimated.

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


|Col1|Radialprofile<br>Gaussianfit<br>Beam-deconvolved fit<br>CenterofGaussian<br>Emittingregionradius<br>HWHM<br>HCN<br>IRAS074547112<br>-|
|---|---|
|||





1.0


0.8


0.6


0.4


0.2


0.0


1.0


0.8


0.6


0.4



Radius (cm) 1e17
0.0 0.2 0.4 0.6 0.8 1.0 1.2


0.0 2.5 5.0 7.5 10.0 12.5 15.0

Radius (")


Radius (cm) 1e17
0.0 0.2 0.4 0.6 0.8 1.0 1.2



SiC 2


c-C 3 H 2


C 4 H


C 3 H


C 2 H


HNC


HC 5 N


C 3 N


HC 3 N


CN


HCN


CS


SiS


SiO


|Col1|Col2|Col3|
|---|---|---|
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
|IRAS 15194-5115|IRAS 15194-5115|IRAS 15194-5115|
||IRAS 15082-4808<br>||
|~~IRAS 07454-7112~~|~~IRAS 07454-7112~~|~~IRAS 07454-7112~~|



0.2


0.0

|Col1|Radialprofile<br>Gaussianfit<br>Beam-deconvolved fit<br>CenterofGaussian<br>Emittingregionedges<br>FWHM<br>CN<br>IRAS074547112<br>-|
|---|---|
|||



0.0 2.5 5.0 7.5 10.0 12.5 15.0

Radius (")


Fig. 10: Examples of Gaussian fits to the AARPs: HCN
(centrally-peaked species, top panel), CN (shell species, bottom panel), both towards IRAS 07454−7112. The solid blue
lines show the mean AARPs and the dashed red lines show
the Gaussian fits. The dash-dotted black Gaussians are obtained
by deconvolving the beam from the Gaussian fit. The yellow
lines show the HWHM distance from the centre of the beamdeconvolved Gaussian on either side of the peak, and the horizontal pink line depicts the HWHM (for centrally-peaked emission, top panel) or the FWHM (for shell emission, bottom panel)
of the beam-deconvolved Gaussian.


We do not expect this to change the abundances beyond the estimated uncertainties.


4.5.1. Uncertainties of abundance estimates


The accuracy of a determined absolute abundance depends
on the method used to estimate it, the validity of the assumptions that went into the calculations, and the uncertainties of input parameters. We have assumed a simple circumstellar model
(including the shape of the radial abundance distributions), and
excitation in LTE of the molecular energy levels. Among the
input parameters, we have the adopted distances and the massloss rates. In addition, the amount and quality (including calibration uncertainties) of the observational data contribute to the
uncertainty, through the measured fluxes and estimated emittingregion sizes. This makes it difficult to estimate formal errors of
the abundances.



0.0 0.2 0.4 0.6 0.8 1.0
Radius (10 [17] cm)


Fig. 11: Estimates of the extents of the molecular line-emitting
regions. The horizontal lines show the radial extent of the
emitting regions, as determined through Gaussian fits, for
each molecule towards IRAS 07454−7112 (yellow), IRAS
15082−4808 (red), and IRAS 15194−5115 (blue). The ♦ signs
denote the positions of the emission peaks. The + signs indicate
species for which the emissions from several isotopologues (see
Sect. 4.3.2) were averaged to produce the AARP. The values of
the emission extents and their uncertainties are listed in Table 5.


The arcs seen in the molecular emission towards IRAS
15194−5115 and IRAS 15082−4808 suggest that there are density enhancements (see Sect. 4.3.4). These are not considered
in the assumed smooth H 2 flow, as we do not have a wellconstrained quantitative estimate of these enhancements. This
also adds to the uncertainty of the abundance estimates. Attempts
to address this demand detailed modelling which is outside the
scope of the present work.
In general, we estimate that the overall uncertainty, including all parameters and model assumptions, is about a factor of
3 − 5 for the absolute abundances estimated using population diagrams, depending on the quality of the population diagram. The
single-line estimates are, at best, order-of-magnitude estimates.
The uncertainty decreases to a factor of 2 − 3 and a factor of
5 in the cases of population diagram and single-line estimates,
respectively, when comparing abundances that are normalised
individually to the respective C [34] S abundance for each source
(Sect 4.5), since this means that the influences of distance, massloss rate, and circumstellar model to a large extent are removed.
The comparison abundances adopted for IRC +10 216, which
are obtained using different methods, have an uncertainty of at
least a factor of 2-3.


_4.6._ _Isotopic ratios_


Stellar elemental isotopic ratios are measures of the nucleosynthetic history (including dredge-up) of a star, and are, as
such, important observational results. Spectral lines from our
data can be used to estimate circumstellar isotopologue ratios. In
most cases, there is every reason to think that these are also good
estimates of the corresponding stellar isotope ratios, since the


Article number, page 15 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars





100


80


60


40


20





10 [17]


10 [16]


10 [15]


10 [14]



0

|Col1|Col2|151945115<br>-<br>150824808<br>-<br>074547112<br>-|
|---|---|---|
||||



Fig. 12: Rotation temperatures ( _T_ rot, left panel) and total column densities ( _N_ tot, right panel) obtained from population diagrams.
The dashed vertical black line separates the shell species and the centrally-peaked species.



different isotopologues are produced, destroyed, and excited in a
similar way, to first approximation. This applies, for instance, to
silicon and sulphur. For carbon, the situation is special since the
photo-dissociation process is isotope selective in the case of CO
(Saberi et al. 2019). However, the effect of this is estimated to be
small for high-mass-loss-rate objects (Saberi et al. 2020), that is,
the type of stars in this study.
For species for which we could make reliable population diagrams, the isotopic ratios are calculated from the abundance
ratios of the relevant molecules. For all other species, the isotopic ratio is determined by calculating the corresponding ′ line
intensity ratios. This method assumes that the _J_ − _J_ transition is
excited under the same conditions for both isotopologues. We refrain from performing any frequency corrections on the isotopic
ratios, as the uncertainties in the estimated ratios are significantly
greater than the magnitude of such corrections. We present estimates of the isotopic ratios for the three stars in Table 8, along
with isotopic ratios for IRC+10216 and the Sun obtained from
the literature for comparison.
Carbon: The [12] C/ [13] C ratios calculated from the optically thin
lines of HNC, SiC 2, HC 3 N, C 4 H, and C 3 N for all three stars
are consistent with their respective values obtained from the CO
radiative transfer modelling by Woods et al. (2003), though the
C 4 H ratio is slightly larger than the others.
Silicon: The [28] Si/ [29] Si, [28] Si/ [30] Si, and [29] Si/ [30] Si values in the
three stars are similar to the expected values of 20, 30, and 1.5,
the solar values (Asplund et al. 2009).
Sulphur: The [32] S/ [33] S and [32] S/ [34] S values, about 100 and 20,
respectively, in the three stars, are close to the expected solar
values of 125 and 22.


**5.** **Discussion**


A comparison of molecular radial brightness distributions
and abundances between the three stars and with IRC +10 216,
allows an understanding of whether and how the chemistry in Ctype AGB CSEs is affected by variations in properties including
the MLR and the stellar [12] C/ [13] C ratio. We compare the molecular
radial brightness distributions of various molecules focusing on
Figs. 9 and 11 and the molecular abundances based on Fig. 13.
Even though the AARPs show only the radial structure of the
emission and average out all azimuthal variations, they still pro

Article number, page 16 of 114



vide valuable information on the chemical stratification in the
CSE, and thereby on the formation and destruction mechanisms
of various molecules.

We start by analyzing whether the spatial extents of the
molecular CSEs follow that expected from photodissociation by
an external UV radiation field. The photodissociation radius of a
molecule depends on how well it is shielded from the interstellar
radiation field (ISRF). This is determined by the outward column density of dust, which in turn depends on the mass-loss rate,
or rather the circumstellar density (proportional to _M_ [˙] /� exp ), and
also on the gas-to-dust ratio. The circumstellar density is lowest for IRAS 07454−7112, and about three and five times higher
for IRAS 15194−5115 and IRAS 15082−4808, respectively (Table 1). The gas-to-dust ratios for the three sources are likely similar (Groenewegen et al. 1998). Thus, we expect the sizes of the
molecular shells to be smallest for IRAS 07454−7112, larger for
IRAS 15194−5115, and largest for IRAS 15082−4808. Indeed,
the shells of IRAS 07454−7112 are by far the smallest ones, by
about a factor of three (Figs. 9, 11, Table 5). However, those
of IRAS 15194−5115 and IRAS 15082−4808 are of about the
same size. They are also comparable in size to the molecular
shells seen towards IRC+10216, which has a circumstellar den
−
sity roughly 3 times higher than that of IRAS 15194 5115, and
1.5 times that of IRAS 15082−4808. This could be attributed
to errors in the distances (which affect mass-loss-rate estimates
and spatial extents), differences in the gas-to-dust ratio, differences in the circumstellar dust properties, and/or to the CSEs
being exposed to slightly different strengths of the ISRF. Thus,
our results, which are corroborated by the radial brightness profiles of also the centrally-peaked species, are not inconsistent
with the expected sizes of molecular distributions affected by
photo-dissociation by UV light from the outside. The next paper in the series will address this in a more quantitative way (see
Sect. 1). As mentioned above, the lower circumstellar density of
IRAS 07454−7112 leads to the parent molecules being photodissociated closer to the star than in the other two sources. This may
be reflected in the higher rotation temperatures obtained for the
daughter species for this object (Fig. 12, left panel).

When looking at the AARPs of shell species in more detail, we conclude that the cyanopolyynes are located slightly
inwards with respect to the hydrocarbons (see Figs. 9, 11 and
Table 5). The average peak position of the cyanopolyynes falls

10 5


10 6


10 7


10 8



R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRC+10216


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|Col27|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||||||||||
||||||||||||||||||||||||||||
||||||||||||||||||IRAS<br>IRAS<br>IRAS<br>|1519<br> 1508<br> 0745<br>|4-511<br> 2-480<br>4-711<br>|5<br> 8<br>2|||||||



10


1


100


10


1


0.1


Fig. 13: Molecular fractional abundances for the three stars (this work) and IRC +10 216 (from the literature, see Table 7). The
absolute abundances are shown in the top panel. The middle panel shows the abundances normalised to IRC +10 216, and the
bottom panel shows the abundances normalised to each star’s own C [34] S abundance. Uncertainties on these estimates are discussed
in Sect. 4.5.1.


Article number, page 17 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


Table 8: Isotopic ratios.


Source
Ratio Species

15194−5115 15082−4808 07454−7112 IRC +10 216 Solar [(] _[b]_ [)]


12 C/ 13 C HC 3 N 4.9(0.5) 31.0(3.5) 21.0(2.2)
C 4 H 10.4(1.5) – – 45(12) [(1)]

HNC 5.0(0.5) – – ≥ 38 [(2)]

SiC 2 5.8(0.6) – – 37(5) [(1)], 50(7) [(1)], 41(4) [(1)]

C 3 N 5.9(0.6) – – 35(15) [(1)]

Average 6.4(0.6) 31.0(3.5) 21.0(2.2) 45(3) [(1)] 89


32 S/ 34 S SiS 19(4) 28(8) [(] _[a]_ [)] 21(4) 18.9(1.3) [(3)] 22
34 S/ 33 S CS 4.8(1.0) 6.1(1.3) 5.4(1.0) 5.2(0.4) [(3)] 5.5
32 S/ 33 S [ [32] S/ [34] S]×[ [34] S/ [33] S] 93(28) 127(44) 115(29) 93(10) [(3)] 125


28 Si/ 29 Si SiS 16.8(2.1) 16(3) [(] _[a]_ [)] 16(7) 17.2(1.1) [(3)] 20


29 Si/ 30 Si SiO 1.3(0.2) 1.4(0.2) 1.4(0.3)
SiS – 2.2(0.5) 1.8(0.8)
Average 1.3(0.2) 1.8(0.3) 1.6(0.4) 1.46(0.11) [(3)] 1.5


28 Si/ 30 Si SiS – – 28(12) 24.7(1.8) [(3)] 30

[ [28] Si/ [29] Si]×[ [29] Si/ [30] Si] 21.8(3.2) 22(5) 21(9)


**Notes.** The values marked [(] _[a]_ [)] are from abundance ratios, and the others are from line intensity ratios. The multiple number of carbon atoms present
in a molecule has been taken into account when calculating the [12] C/ [13] C ratio from HC 3 N, C 4 H, and C 3 N. For IRC +10 216, isotopic ratios are
taken from [(1)] Cernicharo et al. (2000), [(2)] Kahane et al. (1988), and [(3)] He et al. (2008). [(] _[b]_ [)] Solar values are from Asplund et al. (2009). The values
given in parentheses are the estimated overall uncertainties.


inside that of the hydrocarbons by around 25-30% for both
IRAS 15194−5115 and IRAS 15082−4808, and by roughly 10%
for IRAS 07454−7112. We find no marked difference in the
locations among the species of these respective groups. The
largest spatial extents are found for HNC, CN, and possibly
C 3 N, and the hydrocarbons C 2 H and C 4 H. This is consistent
with the results of Daniel et al. (2012) and Cernicharo et al.
(2013) who found HNC emission extending to more than 30 [′′]
towards IRC +10 216, and Agúndez et al. (2017) who found CN
to present emission to similar radii, extending beyond that of
the other cyanides and cyanopolyynes around this star. The shell
of c-C 3 H 2, detected only towards IRAS 15194−5115, appears
roughly coincident with the C 2 H and C 4 H shells. In all of these
respects, we reproduce the findings of Agúndez et al. (2017) in
the case of IRC +10 216. We note that while Agúndez et al.
(2017) found that the CN emission towards IRC +10 216 clearly
extends beyond that of the C 2 H and C 4 H radicals, we observe
the faint extended emission from these radicals to have roughly
the same radial extent as the CN towards IRAS 15194−5115 and
IRAS 15082−4808 (Fig. 9). However, this is due to the most extended CN emission being filtered out due to the lack of very
short baselines in our observations, in contrast to that of Agúndez et al. (2017), who used single dish observations to recover
the flux filtered out by ALMA.

From our observations, we find that HC 3 N is present within
one synthesised beam around two of our stars, corresponding to ∼700 AU and ∼1000 AU for IRAS 15194−5115 and
IRAS 15082−4808, respectively. For IRC +10 216, Siebert et al.
(2022) found significant emission from high-excitation ( _J_ =
38 − 37, 30 − 29, 28 − 27) lines of HC 3 N within 350 AU from the
star. Herbst & Leung (1990), Howe & Millar (1990), and Agún

Article number, page 18 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



dez et al. (2017) suggest that HC 3 N is formed in C-type CSEs
mainly through the reaction


CN + C 2 H 2 → HC 3 N + H (1)


Hence, it is expected to appear in the inner CSE if there is enough
CN available. We cannot confirm this pathway as the main production channel, since we do not detect CN emission above the
noise level in the innermost part in any of our CSEs. However,
this could be a sensitivity effect since the surface brightness of
the CN emission is low at the systemic velocity for the two
sources where we have sufficient spatial resolution to do this.
Van de Sande & Millar (2022) suggested that a significant inner wind abundance of complex species, including HC 3 N, can
be indicative of the presence of a white dwarf binary companion. However, according to their models, this will also lead to
severely reduced SiO and SiS abundances, an effect not seen in
our data.
We find that the SiC 2 abundance distribution has both a central and a shell component. The presence of a central component
has been discussed before by, for instance, Lucas et al. (1995);
Fonfría et al. (2014); Velilla Prieto et al. (2015a); Massalkhi
et al. (2018). It is most likely explained by SiC 2 being formed
in the extended atmosphere, as already suggested by MacKay
& Charnley (1999), and predicted by the chemical models of
Agúndez et al. (2020). The detection of hot SiC 2 ro-vibrational
bands in the optical towards carbon stars (Sarre et al. 1996) supports this. The SiC 2 shell, on the other hand, is expected to be
formed due to the fast reaction of Si with C 2 H 2 in the lowtemperature (<100 K) conditions prevalent in the outer parts of
the CSE (Canosa et al. 2001; Cernicharo et al. 2010):


Si + C 2 H 2 → Si(CH) 2 → SiC 2 + H 2 (2)


Further out, it is photo-dissociated to form Si and C 2 (Harada
et al. 2010).
The arcs seen in the HC 3 N and SiC 2 emissions at the systemic velocity for IRAS 15194−5115 are clearly co-spatial
(Fig. 6, top left panel), though these molecules themselves do not
share any common chemistry. These arcs appear to be traced by
a variety of other molecules as well (Sect. 4.3.1). This suggests
that the arc structures seen are, predominantly, the result of density enhancements rather than abundance variations. Such thin
shells in various cyanopolyynes and hydrocarbons are also seen
in the CSE of IRC +10 216 (Agúndez et al. 2017). Additionally, for IRC +10 216, Mauron & Huggins (1999, 2000); Leão
et al. (2006) and Dinh-V-Trung & Lim (2008) showed that the
clumpy shells seen in cyanopolyyne emission coincide spatially
with the dust arcs observed in dust-scattered optical light, hence
representing the same density enhancements in the CSE. This
is in line with the suggestion by Lykou et al. (2018), based on
CO, SiO, CS, and HC 3 N emission and NACO/VLT near-infrared

−
data, that IRAS 15194 5115 could be a binary system in which a
spiral-like density structure would be imprinted in the CSE by an
orbiting companion. Similar substructure was observed in CO,
CN, and C 4 H towards IRC +10 216 by Cernicharo et al. (2015);
Decin et al. (2015) and Guélin et al. (2018), which was attributed
to episodic mass loss triggered by the existence of a putative
binary companion. Towards IRAS 15194−5115, we find emission from C 2 H also in the gaps between the arcs seen in HC 3 N
(Fig. 6, middle-left panel and Fig. 7). This need not be contrary
to the proposition of density-enhanced shells but can rather be
explained by the larger impact of density enhancements on the
abundance of HC 3 N (Cordiner & Millar 2009).
The rotation temperatures we estimate from our population diagrams match reasonably well with those estimated for



IRC +10 216. He et al. (2008) obtained a rotation temperature
of 28 K for HC 3 N, and Cernicharo et al. (2000) reported 35 K
for C 4 H and 20 K for C 3 N, which align with our estimates. We
note that Pardo et al. (2022) also present population diagrams of
C 4 H and HC 5 N, among other species, towards IRC +10 216 using lines from their 31.0-50.3 GHz spectral survey. These yield
rotation temperatures of 4.9 and 10.1 K respectively, much lower
than our estimates for these species (Table 6).
We have estimated that the uncertainties of the relative abundances when comparing our three stars are a factor of 2-3 for
population diagrams and a factor of 5 for single-line estimates.
When comparing with IRC +10 216 they increase to a factor of
5 for population diagrams and a factor of 10 for single-line estimates. Considering this, there are no significant differences or
trends in the abundances among our three stars, other than the
possibly lower hydrocarbon abundances in IRAS 07454−7112,
compared to the other two stars (Fig. 13). The latter can be a
result of the lower density of the CSE of IRAS 07454−7112.
When comparing with IRC +10 216, all abundances except that
of SiO are within a factor of ten, meaning that except for this
species, we find no significant differences with the abundances
estimated for IRC +10 216. The SiO abundances in our stars are
higher than that for IRC +10 216 by an order of magnitude. The
same discrepancy was observed by Woods et al. (2003) in their
single-dish line survey of these sources. The putative overabundance of SiO in our stars needs to be confirmed through a proper
radiative transfer analysis.
Time variability of the intensity of thermal (non-maser) line
emission has been reported for several species in the case of
IRC +10 216 (Cernicharo et al. 2014; Pardo et al. 2018; He
et al. 2019). By comparing the observations from two epochs,
we find variability in the 3 mm line emission of C 2 H and HC 3 N
towards IRAS 15194−5115 and IRAS 15082−4808. Our findings (Sect. 4.2) are in line with the conclusions of Cernicharo
et al. (2014) and Pardo et al. (2018), who show that C 2 H shows
the highest variability at 3 mm, and that the phase of variability
of the cyanopolyynes is opposite to that of C 2 H, for IRC +10 216
as well. We note that in addition to C 2 H and HC 3 N, Pardo et al.
(2018) also found time variability in the lines of CN, C 4 H, C 5 H,
and HC 5 N towards IRC +10 216, which we are unable to ascertain for the stars in our sample from the current data. This can
potentially be due to the intensity variation in the lines of these
species being lower than the calibration uncertainty.
The three stars in our sample have significantly different inferred [12] C/ [13] C ratios (Table 8), with IRAS 15194−5115 standing
out with a very low value of 6. For this star, Ramstedt & Olofsson (2014) report a [12] CO/ [13] CO ratio of 10, slightly higher than
the value of 6 estimated by Woods et al. (2003) and us (still
within the uncertainties of both estimates). The other two stars,
and IRC +10 216, have values in the range 20−50, which is consistent with typical AGB evolution models (see e.g. Lattanzio
& Boothroyd 1997, and references therein) where the surface
12 C/ 13 C ratio increases as the star evolves along the AGB. This
has also been traced by observations (e.g. Lambert et al. 1986;
Abia et al. 2001; Ramstedt & Olofsson 2014). It cannot be concluded with certainty that the low ratio in IRAS 15194−5115 is
due to hot-bottom burning (HBB) and a subsequent evolution to
a carbon star, as the star may not be massive enough for HBB
to occur. Whereas HBB efficiently produces N, we find no indications of any N enhancement in the circumstellar species for
this star. It has been suggested that the presence of a hot binary
companion may alter the circumstellar [12] CO/ [13] CO through differential photodissociation so that it differs from the atmospheric
12 C/ 13 C, whereas this is not the case for the isotopologues of the


Article number, page 19 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



other observed molecules in this study (see Vlemmings et al.
2013; Saberi et al. 2019). They are therefore expected to give
good estimates of the stellar [12] C/ [13] C ratio. The models by Izzard
& Tout (2003), combining nucleosynthesis and binary star evolution, have shown that the atmospheric [12] C/ [13] C can be lowered
significantly in the presence of binary companions.
Finally, the observed similarity of the silicon isotopic ratios
with the respective solar values is in line with AGB nucleosynthesis in lower-mass stars (≲4 _M_ ⊙, Karakas & Lugaro 2016). In
addition, the sulphur isotopic ratios being consistent with the
corresponding solar ratios is in line with the fact that these isotopes are not expected to be influenced by nucleosynthesis in
lower-mass stars (Shingles & Karakas 2013; Humire et al. 2020,
and references therein).


**6.** **Summary and conclusions**


Our unbiased ALMA spectral survey mapped for the first
time the 3 mm molecular rotational transitions in the CSEs of
the C-type AGB stars IRAS 15194−5115, IRAS 15082−4808,
and IRAS 07454−7112 at high spatial resolution (0 [′′] . 7 − 1 [′′] . 7,
corresponding to roughly 500 − 1000 AU). Extensive interferometric surveys of this kind have previously been performed
only towards IRC +10 216. The survey yielded 311 identified
lines (including hyperfine splitting components), from 132 rotational transitions of 49 molecular species, including various
isotopologues, and 3 unidentified lines. Data with sufficient
signal-to-noise ratio (≳3σ in the emission maps), which enabled us to comparatively analyse the morphological characteristics across the three stars was obtained for 14 species. We
produced azimuthally-averaged radial profiles (AARPs) to obtain the radial brightness distributions of these species, and estimated the extents of their emitting regions. We used opticaldepth-corrected population diagrams or single-line calculations
to calculate the fractional abundances of these molecules and
their less-abundant isotopologues. Lines from our APEX singledish surveys of the sources were used in the population diagrams
to complement those from the ALMA observations. We also report several new detections towards these stars, namely [29] SiO,
30 SiO, 29 SiS, 30 SiS, Si 34 S, C 33 S, Si 13 CC, C 6 H, C 8 H, l−C 4 H 2,
and doubly [13] C-substituted isotopologues of HC 3 N.
We find deviations from a smooth, spherically symmetric
CSE towards IRAS 15194−5115 and IRAS 15082−4808 in several molecules, and detect density enhancements similar to what
has previously been reported in the CSE of IRC +10 216, which
might indicate the presence of stellar/sub-stellar companions for
these stars. The very low [12] C/ [13] C ratio and the presence of a
‘central’ emission component for HC 3 N may also be indicative
of the presence of a binary companion for IRAS 15194−5115.
By comparing our morphological results for the three
sources amongst themselves and with results from the literature for IRC +10 216, we find that the chemistry in the CSEs,
as traced by the radial order in which different molecules exist around the central star, is very similar in our sources and
IRC +10 216. The chemistry does not seem significantly affected
by the differences in the nucleosynthetic history of the individual stars, indicated by differences in their [12] C/ [13] C ratios, except
for the expected increased abundance of singly- and doubly- [13] C
−
substituted isotopologues in the CSE of IRAS 15194 5115, owing to its low [12] C/ [13] C ratio. We find that, within the uncertainties of our analysis, most of the estimated fractional abundances
are similar across the source sample, and to the corresponding
IRC +10 216 values. The notable exception is SiO, which appears more abundant in the three stars in our sample in compar

Article number, page 20 of 114



ison to IRC +10 216, by an order of magnitude. The calculated
abundances of the shell species match reasonably well with photochemical models for all sources. We also detect variability in
the line emission of C 2 H and HC 3 N for two stars in our sample.
We estimate the carbon, silicon, and sulphur isotopic ratios for the three stars. The [12] C/ [13] C ratios match the values
from the literature for all stars, and the silicon and sulphur ratios of the three stars match reasonably well the corresponding
IRC +10 216 and solar values.
Overall, we conclude that the chemistry in the C-type AGB
CSEs studied in this paper, as judged from radial brightness
distributions and estimated abundances, is consistent across our
small sample and with that of IRC +10 216. This indicates that
IRC +10 216 serves reasonably well as an archetypal C-type
AGB star, in terms of modelling C-type CSE chemistry, at least
for MLRs within an order of magnitude of that of itself. However, we remind the reader of the possible binary nature of
IRC +10 216 and potentially also of some of the sources in our
study. Binarity might influence the chemical properties differently for different sources, depending on the properties of the
objects in the system.
Non-LTE radiative transfer modelling is necessary to more
accurately determine the molecular abundances. This, and the
subsequently updated chemical models will be presented in a
series of upcoming papers. More extensive observations, both
in terms of sources and spectral coverage are required to thoroughly constrain the chemical models and small-scale chemical
variations in the CSEs. A detailed investigation of the morphology of the CSEs of the stars in our sample and the possible presence of binary companions will require observations with higher
angular resolution and sensitivity.


_Acknowledgements._ RU acknowledges data reduction support from the Nordic
ALMA Regional Centre (ARC) node based at Onsala Space Observatory
(OSO), Sweden. The Nordic ARC node is funded through Swedish Research Council grant No 2017-00648. EDB acknowledges financial support
from the Swedish National Space Agency. SBC and MAC were supported
by the NASA Planetary Science Division Internal Scientist Funding Program through the Fundamental Laboratory Research work package (FLaRe).
IdG acknowledges support from grant PID2020-114461GB-I00, funded by
MCIN/AEI/10.13039/501100011033. The work of MGR is supported by NOIRLab, which is managed by the Association of Universities for Research in
Astronomy (AURA) under a cooperative agreement with the National Science Foundation, USA. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2013.1.00070.S, ADS/JAO.ALMA#2015.1.01271.S,
ADS/JAO.ALMA#2011.0.00001.CAL. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ. This paper is based on observations with the
Atacama Pathfinder EXperiment (APEX) telescope. APEX is a collaboration between the Max Planck Institute for Radio Astronomy, the European Southern Observatory, and the Onsala Space Observatory. Swedish observations on APEX are
supported through Swedish Research Council grant No 2017-00648. The APEX
observations were obtained under project numbers O-0107.F-9310 (SEPIA/B5),
O-0104.F-9305 (PI230), and O-087.F-9319, O-094.F-9318, O-096.F-9336, and
O-098.F-9303 (SHeFI).


**References**


[Abia, C., Busso, M., Gallino, R., et al. 2001, ApJ, 559, 1117](http://dx.doi.org/10.1086/322383)
Agundez, M. 2009, Estudio de la Química en la Envoltura Circunestelar IRC
[+10216, PhD thesis, Center for Astrobiology, Madrid](https://ui.adsabs.harvard.edu/abs/2009PhDT........98A)
Agúndez, M. 2022, in European Physical Journal Web of Conferences, Vol. 265,
[European Physical Journal Web of Conferences, 00029](https://ui.adsabs.harvard.edu/abs/2022EPJWC.26500029A)
[Agúndez, M., Cernicharo, J., Quintana-Lacaci, G., et al. 2017, A&A, 601, A4](http://dx.doi.org/10.1051/0004-6361/201630274)
[Agúndez, M., Fonfría, J. P., Cernicharo, J., et al. 2012, A&A, 543, A48](http://dx.doi.org/10.1051/0004-6361/201218963)
Agúndez, M., Martínez, J. I., de Andres, P. L., Cernicharo, J., & Martín-Gago,
[J. A. 2020, A&A, 637, A59](http://dx.doi.org/10.1051/0004-6361/202037496)
[Allain, T., Sedlmayr, E., & Leach, S. 1997, A&A, 323, 163](https://ui.adsabs.harvard.edu/abs/1997A&A...323..163A)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



Andriantsaralaza, M., Ramstedt, S., Vlemmings, W. H. T., & De Beck, E. 2022,

[A&A, 667, A74](http://dx.doi.org/10.1051/0004-6361/202243670)
[Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481](http://dx.doi.org/10.1146/annurev.astro.46.060407.145222)
[Belitsky, V., Lapkin, I., Fredrixon, M., et al. 2018, A&A, 612, A23](http://dx.doi.org/10.1051/0004-6361/201731458)
Billade, B., Nystrom, O., Meledin, D., et al. 2012, IEEE [Transactions](http://dx.doi.org/10.1109/TTHZ.2011.2182220) on Tera[hertz Science and Technology, 2, 208](http://dx.doi.org/10.1109/TTHZ.2011.2182220)
Butler, B. 2012, Atacama Large Millimeter/Submillimeter Array Memo 594,

[594, 1](https://ui.adsabs.harvard.edu/abs/2012ALMAM.594....1B)
[Canosa, A., Le Picard, S. D., Gougeon, S., et al. 2001, J. Chem. Phys., 115, 6495](http://dx.doi.org/10.1063/1.1396855)
Cernicharo, J., Cabezas, C., Pardo, J. R., et al. 2023a, arXiv [e-prints,](https://ui.adsabs.harvard.edu/abs/2023arXiv230405117C)
[arXiv:2304.05117](https://ui.adsabs.harvard.edu/abs/2023arXiv230405117C)
[Cernicharo, J., Daniel, F., Castro-Carrizo, A., et al. 2013, ApJ, 778, L25](http://dx.doi.org/10.1088/2041-8205/778/2/L25)
[Cernicharo, J., Guélin, M., & Kahane, C. 2000, A&AS, 142, 181](http://dx.doi.org/10.1051/aas:2000147)
[Cernicharo, J., Marcelino, N., Agúndez, M., & Guélin, M. 2015, A&A, 575, A91](http://dx.doi.org/10.1051/0004-6361/201424565)
[Cernicharo, J., Pardo, J. R., Cabezas, C., et al. 2023b, A&A, 670, L19](http://dx.doi.org/10.1051/0004-6361/202245816)
[Cernicharo, J., Teyssier, D., Quintana-Lacaci, G., et al. 2014, ApJ, 796, L21](http://dx.doi.org/10.1088/2041-8205/796/1/L21)
[Cernicharo, J., Waters, L. B. F. M., Decin, L., et al. 2010, A&A, 521, L8](http://dx.doi.org/10.1051/0004-6361/201015150)
[Cherchneff, I., Barker, J. R., & Tielens, A. G. G. M. 1992, ApJ, 401, 269](http://dx.doi.org/10.1086/172059)
Claude, S., Dindo, P., Erickson, D., et al. 2005, in The Joint 30th International
Conference on Infrared and Millimeter Waves and 13th International Confer
[ence on Terahertz Electronics, 407–408](https://ui.adsabs.harvard.edu/abs/2005imw..conf..407C)
[Cordiner, M. A. & Millar, T. J. 2009, ApJ, 697, 68](http://dx.doi.org/10.1088/0004-637X/697/1/68)
Cornwell, T. J. 2008, IEEE Journal of Selected [Topics](http://dx.doi.org/10.1109/JSTSP.2008.2006388) in Signal Processing, [2,](https://ui.adsabs.harvard.edu/abs/2008ISTSP...2..793C)
[793](https://ui.adsabs.harvard.edu/abs/2008ISTSP...2..793C)
[Daniel, F., Agúndez, M., Cernicharo, J., et al. 2012, A&A, 542, A37](http://dx.doi.org/10.1051/0004-6361/201118449)
[De Beck, E., Lombaert, R., Agúndez, M., et al. 2012, A&A, 539, A108](http://dx.doi.org/10.1051/0004-6361/201117635)
[Decin, L., Richards, A. M. S., Neufeld, D., et al. 2015, A&A, 574, A5](http://dx.doi.org/10.1051/0004-6361/201424593)
[Di Criscienzo, M., Ventura, P., García-Hernández, D. A., et al. 2016, MNRAS,](http://dx.doi.org/10.1093/mnras/stw1685)

[462, 395](https://ui.adsabs.harvard.edu/abs/2016MNRAS.462..395D)
[Dinh-V-Trung & Lim, J. 2008, ApJ, 678, 303](http://dx.doi.org/10.1086/527669)
[Feast, M. W., Whitelock, P. A., & Marang, F. 2003, MNRAS, 346, 878](http://dx.doi.org/10.1111/j.1365-2966.2003.07136.x)
Fonfría, J. P., Fernández-López, M., Agúndez, M., et al. 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu1968) [445,](https://ui.adsabs.harvard.edu/abs/2014MNRAS.445.3289F)
[3289](https://ui.adsabs.harvard.edu/abs/2014MNRAS.445.3289F)
[Fonfría, J. P., Fernández-López, M., Pardo, J. R., et al. 2018, ApJ, 860, 162](http://dx.doi.org/10.3847/1538-4357/aac5e3)
[Goddi, C., Martí-Vidal, I., Messias, H., et al. 2019, PASP, 131, 075003](http://dx.doi.org/10.1088/1538-3873/ab136a)
[Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209](http://dx.doi.org/10.1086/307195)
[Gong, Y., Henkel, C., Spezzano, S., et al. 2015, A&A, 574, A56](http://dx.doi.org/10.1051/0004-6361/201424819)
[Groenewegen, M. A. T. 1997, A&A, 317, 503](https://ui.adsabs.harvard.edu/abs/1997A&A...317..503G)
[Groenewegen, M. A. T., Barlow, M. J., Blommaert, J. A. D. L., et al. 2012, A&A,](http://dx.doi.org/10.1051/0004-6361/201219604)

[543, L8](https://ui.adsabs.harvard.edu/abs/2012A&A...543L...8G)
Groenewegen, M. A. T., Whitelock, P. A., Smith, C. H., & Kerschbaum, F. 1998,

[MNRAS, 293, 18](http://dx.doi.org/10.1046/j.1365-8711.1998.01113.x)
[Guélin, M., Patel, N. A., Bremer, M., et al. 2018, A&A, 610, A4](http://dx.doi.org/10.1051/0004-6361/201731619)
[Guilloteau, S., Omont, A., & Lucas, R. 1987, A&A, 176, L24](https://ui.adsabs.harvard.edu/abs/1987A&A...176L..24G)
[Güsten, R., Nyman, L. Å., Schilke, P., et al. 2006a, A&A, 454, L13](http://dx.doi.org/10.1051/0004-6361:20065420)
[Güsten, R., Nyman, L. Å., Schilke, P., et al. 2006b, A&A, 454, L13](http://dx.doi.org/10.1051/0004-6361:20065420)
[Guzmán, A. E., Verdugo, C., Nagai, H., et al. 2019, PASP, 131, 094504](http://dx.doi.org/10.1088/1538-3873/ab2d38)
Habing, H. J. & Olofsson, H. 2004, Asymptotic Giant Branch Stars
[Harada, N., Herbst, E., & Wakelam, V. 2010, ApJ, 721, 1570](http://dx.doi.org/10.1088/0004-637X/721/2/1570)
[He, J. H., Dinh-V-Trung, Kwok, S., et al. 2008, ApJS, 177, 275](http://dx.doi.org/10.1086/587142)
[He, J. H., Kami´nski, T., Mennickent, R. E., et al. 2019, ApJ, 883, 165](http://dx.doi.org/10.3847/1538-4357/ab3d37)
Henry, R. B. C., Speck, A., Karakas, A. I., Ferland, G. J., & Maguire, M. 2012,

[ApJ, 749, 61](http://dx.doi.org/10.1088/0004-637X/749/1/61)
[Herbst, E. & Leung, C. M. 1990, A&A, 233, 177](https://ui.adsabs.harvard.edu/abs/1990A&A...233..177H)
[Herwig, F. 2005, ARA&A, 43, 435](http://dx.doi.org/10.1146/annurev.astro.43.072103.150600)
[Höfner, S. 2008, A&A, 491, L1](http://dx.doi.org/10.1051/0004-6361:200810641)
Höfner, S. 2015, in Astronomical Society of the Pacific Conference Series, Vol.
497, Why Galaxies Care about AGB Stars III: A Closer Look in Space and
[Time, ed. F. Kerschbaum, R. F. Wing, & J. Hron, 333](https://ui.adsabs.harvard.edu/abs/2015ASPC..497..333H)
[Höfner, S. & Olofsson, H. 2018, A&A Rev., 26, 1](http://dx.doi.org/10.1007/s00159-017-0106-5)
[Howe, D. A. & Millar, T. J. 1990, MNRAS, 244, 444](https://ui.adsabs.harvard.edu/abs/1990MNRAS.244..444H)
[Huggins, P. J. & Glassgold, A. E. 1982, ApJ, 252, 201](http://dx.doi.org/10.1086/159547)
[Humire, P. K., Thiel, V., Henkel, C., et al. 2020, A&A, 642, A222](http://dx.doi.org/10.1051/0004-6361/202038216)
[Izzard, R. G. & Tout, C. A. 2003, PASA, 20, 345](http://dx.doi.org/10.1071/AS03026)
[Jeste, M., Gong, Y., Wong, K. T., et al. 2022, A&A, 666, A69](http://dx.doi.org/10.1051/0004-6361/202243365)
[Jolly, J.-B., Knudsen, K. K., & Stanley, F. 2020, MNRAS, 499, 3992](http://dx.doi.org/10.1093/mnras/staa2908)
[Justtanont, K., Barlow, M. J., Tielens, A. G. G. M., et al. 2000, A&A, 360, 1117](https://ui.adsabs.harvard.edu/abs/2000A&A...360.1117J)
[Kahane, C., Gomez-Gonzalez, J., Cernicharo, J., & Guelin, M. 1988, A&A, 190,](https://ui.adsabs.harvard.edu/abs/1988A&A...190..167K)
[167](https://ui.adsabs.harvard.edu/abs/1988A&A...190..167K)
[Karakas, A. I. & Lugaro, M. 2016, ApJ, 825, 26](http://dx.doi.org/10.3847/0004-637X/825/1/26)
[Kepley, A. A., Tsutsumi, T., Brogan, C. L., et al. 2020, PASP, 132, 024505](http://dx.doi.org/10.1088/1538-3873/ab5e14)
[Kraemer, K. E., Sloan, G. C., Keller, L. D., et al. 2019, ApJ, 887, 82](http://dx.doi.org/10.3847/1538-4357/ab4f6b)
[Lambert, D. L., Gustafsson, B., Eriksson, K., & Hinkle, K. H. 1986, ApJS, 62,](http://dx.doi.org/10.1086/191145)
[373](https://ui.adsabs.harvard.edu/abs/1986ApJS...62..373L)
Lattanzio, J. C. & Boothroyd, A. I. 1997, in American Institute of Physics Conference Series, Vol. 402, Astrophysical implications of the laboratory study
[of presolar materials, ed. T. J. Bernatowicz & E. Zinner, 85–114](https://ui.adsabs.harvard.edu/abs/1997AIPC..402...85L)
Lattanzio, J. C., Frost, C. A., Cannon, R. C., & Wood, P. R. 1997, in Stellar
[Ecology: Advances in Stellar Evolution„ 130–137](https://ui.adsabs.harvard.edu/abs/1997seas.conf..130L)



Leão, I. C., de Laverny, P., Mékarnia, D., de Medeiros, J. R., & Vandame, B.
[2006, A&A, 455, 187](http://dx.doi.org/10.1051/0004-6361:20054577)
[Li, X., Millar, T. J., Walsh, C., Heays, A. N., & van Dishoeck, E. F. 2014, A&A,](http://dx.doi.org/10.1051/0004-6361/201424076)

[568, A111](https://ui.adsabs.harvard.edu/abs/2014A&A...568A.111L)
[Lucas, R., Guélin, M., Kahane, C., Audinos, P., & Cernicharo, J. 1995, Ap&SS,](http://dx.doi.org/10.1007/BF00667860)

[224, 293](https://ui.adsabs.harvard.edu/abs/1995Ap&SS.224..293L)
[Lykou, F., Zijlstra, A. A., Kluska, J., et al. 2018, MNRAS, 480, 1006](http://dx.doi.org/10.1093/mnras/sty1903)
[MacKay, D. D. S. & Charnley, S. B. 1999, MNRAS, 302, 793](http://dx.doi.org/10.1046/j.1365-8711.1999.02175.x)
[Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, A&A, 526,](http://dx.doi.org/10.1051/0004-6361/201015487)
[A47](https://ui.adsabs.harvard.edu/abs/2011A&A...526A..47M)
[Massalkhi, S., Agúndez, M., & Cernicharo, J. 2019, A&A, 628, A62](http://dx.doi.org/10.1051/0004-6361/201935069)
[Massalkhi, S., Agúndez, M., Cernicharo, J., et al. 2018, A&A, 611, A29](http://dx.doi.org/10.1051/0004-6361/201732038)
[Matsuura, M., Barlow, M. J., Zijlstra, A. A., et al. 2009, MNRAS, 396, 918](http://dx.doi.org/10.1111/j.1365-2966.2009.14743.x)
[Mauron, N. & Huggins, P. J. 1999, A&A, 349, 203](https://ui.adsabs.harvard.edu/abs/1999A&A...349..203M)
[Mauron, N. & Huggins, P. J. 2000, A&A, 359, 707](https://ui.adsabs.harvard.edu/abs/2000A&A...359..707M)
[McGuire, B. A. 2022, ApJS, 259, 30](http://dx.doi.org/10.3847/1538-4365/ac2a48)
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical
Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
[Bell, 127](https://ui.adsabs.harvard.edu/abs/2007ASPC..376..127M)
[Menten, K. M., Reid, M. J., Kami´nski, T., & Claussen, M. J. 2012, A&A, 543,](http://dx.doi.org/10.1051/0004-6361/201219422)
[A73](https://ui.adsabs.harvard.edu/abs/2012A&A...543A..73M)
[Menten, K. M., Wyrowski, F., Keller, D., & Kami´nski, T. 2018, A&A, 613, A49](http://dx.doi.org/10.1051/0004-6361/201732296)
[Millar, T. J. & Herbst, E. 1994, A&A, 288, 561](https://ui.adsabs.harvard.edu/abs/1994A&A...288..561M)
Müller, H. S., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, [Journal](http://dx.doi.org/https://doi.org/10.1016/j.molstruc.2005.01.027) of
[Molecular Structure, 742, 215](http://dx.doi.org/https://doi.org/10.1016/j.molstruc.2005.01.027)
[Nyman, L. A., Olofsson, H., Johansson, L. E. B., et al. 1993, A&A, 269, 377](https://ui.adsabs.harvard.edu/abs/1993A&A...269..377N)
[Olofsson, H. 2003, in Asymptotic giant branch stars, 325–410](https://ui.adsabs.harvard.edu/abs/2003agbs.conf..325O)
[Pardo, J. R., Cernicharo, J., Tercero, B., et al. 2022, A&A, 658, A39](http://dx.doi.org/10.1051/0004-6361/202142263)
[Pardo, J. R., Cernicharo, J., Velilla Prieto, L., et al. 2018, A&A, 615, L4](http://dx.doi.org/10.1051/0004-6361/201833303)
[Patel, N. A., Young, K. H., Gottlieb, C. A., et al. 2011, ApJS, 193, 17](http://dx.doi.org/10.1088/0067-0049/193/1/17)
[Ramstedt, S. & Olofsson, H. 2014, A&A, 566, A145](http://dx.doi.org/10.1051/0004-6361/201423721)
[Rau, U. & Cornwell, T. J. 2011, A&A, 532, A71](http://dx.doi.org/10.1051/0004-6361/201117104)
Remijan, A. J., Markwick-Kemper, A., & ALMA Working Group on Spectral
Line Frequencies. 2007, in American Astronomical Society Meeting Ab[stracts, Vol. 211, American Astronomical Society Meeting Abstracts, 132.11](https://ui.adsabs.harvard.edu/abs/2007AAS...21113211R)
[Saberi, M., Olofsson, H., Vlemmings, W. H. T., et al. 2020, A&A, 638, A99](http://dx.doi.org/10.1051/0004-6361/202037668)
[Saberi, M., Vlemmings, W. H. T., & De Beck, E. 2019, A&A, 625, A81](http://dx.doi.org/10.1051/0004-6361/201935309)
Sánchez Contreras, C., Velilla Prieto, L., Agúndez, M., et al. 2015, [A&A, 577,](http://dx.doi.org/10.1051/0004-6361/201525652)
[A52](https://ui.adsabs.harvard.edu/abs/2015A&A...577A..52S)
[Sarre, P. J., Hurst, M. E., & Lloyd Evans, T. 1996, ApJ, 471, L107](http://dx.doi.org/10.1086/310336)
[Schöier, F. L., Bast, J., Olofsson, H., & Lindqvist, M. 2007, A&A, 473, 871](http://dx.doi.org/10.1051/0004-6361:20077887)
[Schöier, F. L., Olofsson, H., & Lundgren, A. A. 2006, A&A, 454, 247](http://dx.doi.org/10.1051/0004-6361:20054795)
[Schöier, F. L., Ramstedt, S., Olofsson, H., et al. 2013, A&A, 550, A78](http://dx.doi.org/10.1051/0004-6361/201220400)
[Shingles, L. J. & Karakas, A. I. 2013, MNRAS, 431, 2861](http://dx.doi.org/10.1093/mnras/stt386)
[Siebert, M. A., Van de Sande, M., Millar, T. J., & Remijan, A. J. 2022, ApJ, 941,](http://dx.doi.org/10.3847/1538-4357/ac9e52)
[90](https://ui.adsabs.harvard.edu/abs/2022ApJ...941...90S)

[Sloan, G. C., Little-Marenin, I. R., & Price, S. D. 1998, AJ, 115, 809](http://dx.doi.org/10.1086/300205)
[Smith, C. L., Zijlstra, A. A., & Fuller, G. A. 2014, MNRAS, 440, 172](http://dx.doi.org/10.1093/mnras/stu309)
[Smith, C. L., Zijlstra, A. A., & Fuller, G. A. 2015, MNRAS, 454, 177](http://dx.doi.org/10.1093/mnras/stv1934)
Tenenbaum, E. D., Dodd, J. L., Milam, S. N., Woolf, N. J., & Ziurys, L. M. 2010,

[ApJS, 190, 348](http://dx.doi.org/10.1088/0067-0049/190/2/348)
Tielens, A. G. G. M. 2005, The Physics and Chemistry of the Interstellar Medium
[Van de Sande, M. & Millar, T. J. 2022, MNRAS, 510, 1204](http://dx.doi.org/10.1093/mnras/stab3282)
Van de Sande, M., Sundqvist, J. O., Millar, T. J., Keller, D., & Decin, L. 2019,

[IAU Symposium, 343, 531](http://dx.doi.org/10.1017/S1743921318005434)
[Van de Sande, M., Sundqvist, J. O., Millar, T. J., et al. 2018, A&A, 616, A106](http://dx.doi.org/10.1051/0004-6361/201732276)
van Dishoeck, E. F. 1988, in Astrophysics and Space Science Library, Vol. 146,
[Rate Coefficients in Astrochemistry, ed. T. J. Millar & D. A. Williams, 49](https://ui.adsabs.harvard.edu/abs/1988ASSL..146...49V)
[Vassilev, V., Meledin, D., Lapkin, I., et al. 2008, A&A, 490, 1157](http://dx.doi.org/10.1051/0004-6361:200810459)
[Vassiliadis, E. & Wood, P. R. 1993, ApJ, 413, 641](http://dx.doi.org/10.1086/173033)
[Velilla-Prieto, L., Cernicharo, J., Agúndez, M., et al. 2019, A&A, 629, A146](http://dx.doi.org/10.1051/0004-6361/201834717)
Velilla Prieto, L., Cernicharo, J., Quintana-Lacaci, G., et al. 2015a, [ApJ,](http://dx.doi.org/10.1088/2041-8205/805/2/L13) [805,](https://ui.adsabs.harvard.edu/abs/2015ApJ...805L..13V)
[L13](https://ui.adsabs.harvard.edu/abs/2015ApJ...805L..13V)

[Velilla Prieto, L., Sánchez Contreras, C., Cernicharo, J., et al. 2015b, A&A, 575,](http://dx.doi.org/10.1051/0004-6361/201424768)
[A84](https://ui.adsabs.harvard.edu/abs/2015A&A...575A..84V)
[Vlemmings, W. H. T., Maercker, M., Lindqvist, M., et al. 2013, A&A, 556, L1](http://dx.doi.org/10.1051/0004-6361/201321821)
[Wesson, R., Cernicharo, J., Barlow, M. J., et al. 2010, A&A, 518, L144](http://dx.doi.org/10.1051/0004-6361/201014589)
Whitelock, P. A., Feast, M. W., Marang, F., & Groenewegen, M. A. T. 2006,

[MNRAS, 369, 751](http://dx.doi.org/10.1111/j.1365-2966.2006.10322.x)
Woods, P. M., Schöier, F. L., Nyman, L. Å., & Olofsson, H. 2003, [A&A,](http://dx.doi.org/10.1051/0004-6361:20030190) [402,](https://ui.adsabs.harvard.edu/abs/2003A&A...402..617W)
[617](https://ui.adsabs.harvard.edu/abs/2003A&A...402..617W)
[Yasuda, Y. & Kozasa, T. 2012, ApJ, 745, 159](http://dx.doi.org/10.1088/0004-637X/745/2/159)
[Zijlstra, A. A., Matsuura, M., Wood, P. R., et al. 2006, MNRAS, 370, 1961](http://dx.doi.org/10.1111/j.1365-2966.2006.10623.x)


Article number, page 21 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


**Appendix A:** **ALMA Band 3 spectra**



This appendix shows the entire ALMA Band 3 spectra of the three sources. The spectra have been extracted by integrating
the intensity in a circular aperture of 12.5 [′′] radius centred on the respective continuum peaks, so as to recover emission from all
molecules. Line detections (Table B.1) have been labelled in the figure at the corresponding frequencies.



















































































91 _._ 0 91 _._ 5 92 _._ 0 92 _._ 5

Frequency (GHz)


− −
Fig. A.1: ALMA band 3 line survey of IRAS 07454 7112 (black), IRAS 15082 4808 (blue; vertical offset of 0.1 Jy), and IRAS
15194−5115 (red; vertical offset of 0.2 Jy). Labels show the carrier molecule of the indicated emission. Red labels indicate tentative
or unidentified detections, and green labels indicate lines that have been identified only in central-pixel spectra (not shown). The
spectra from the combined data have been inserted in the respective frequency ranges (see Table 2).



Article number, page 22 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs











































98 _._ 5 99 _._ 0 99 _._ 5 100 _._ 0

Frequency (GHz)



**Fig. A.1.** continued.



Article number, page 23 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



100 _._ 0 100 _._ 5 101 _._ 0 101 _._ 5





104 _._ 5 105 _._ 0 105 _._ 5 106 _._ 0


106 _._ 0 106 _._ 5 107 _._ 0 107 _._ 5

Frequency (GHz)


**Fig. A.1.** continued.





















Article number, page 24 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



















































113 _._ 5 114 _._ 0 114 _._ 5 115 _._ 0

Frequency (GHz)


**Fig. A.1.** continued.



Article number, page 25 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


|Col1|Col2|Col3|
|---|---|---|
|C2|C2|C2|
||||



115 _._ 0 115 _._ 5 116 _._ 0 116 _._ 5

Frequency (GHz)


**Fig. A.1.** continued.


**Appendix B:** **Details of detected transitions**


This appendix lists the detected emission lines along with their upper-level energies and integrated intensities for the three
stars. Table B.1 presents the lines detected in the ALMA band 3 spectra, and Table B.2 lists the lines from the APEX surveys (see
Sect. 3.1) which are used in this work for abundance calculations.


Table B.1: Details of all detected transitions in the ALMA band 3 survey.


Molecule Transition Rest Freq.(GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (Jy km/s)


15194 15082 07454

HC 5 N 32-31 85.201340 67.5 – – 2.2(0.1)
C [13] CCCH N= 9-8, J=19/2-17/2 85.201897 20.4 9.4(0.4) – –
C [13] CH N= 1-0, J=3/2-1/2 85.229326 4.1 bl. – –
C [13] CCCH N= 9-8, J=17/2-15/2 85.239907 20.5 bl. – –
C [13] CH N= 1-0, J=1/2-1/2 85.314378 4.1 bl. – –
CC [13] CCH N= 9-8, J=19/2-17/2 85.331904 20.5 bl. – –
c-C 3 H 2 2 1,2 -1 0,1 85.338894 6.4 19.7(0.5) 2.9(0.2) 0.6(0.1)
CC [13] CCH N= 9-8, J=17/2-15/2 85.370342 20.5 5.9(0.4) – –
C 4 H N = 9-8, J = 19/2-17/2 85.634004 20.5 33.8 (0.4) 5.9(0.2) 0.8(0.1)
C 4 H N = 9-8, J = 17/2-15/2 85.672582 20.6 32.9(0.4) 6.6(0.2) 0.7(0.1)
29 SiO 2-1 85.759194 6.2 9.5(0.4) 2.5(0.2) 1.3(0.1)
C 4 H, ν 7 = 2 [0] N=9-8, J=19/2-17/2 86.047530 397.6 bl. – –
HC [15] N 1-0 86.054966 4.1 bl. – –
C 4 H, ν 7 = 2 [0] N=9-8, J=17/2-15/2 86.105294 397.6 3.0(0.7) – –
CCS 7 6 -6 5 86.181391 23.3 0.8(0.3) – 0.3(0.1)
H [13] CN 1-0 86.339921 4.1 249.5(0.4) 48.7(0.2) 37.8(0.1)
Si [13] CC 4 1,4 -3 1,3 86.562636 12.3 6.0(0.4) – –
SiO 2-1 86.846985 6.3 95.7(0.4) 35.8(0.2) 15.3(0.1)
u – 86.886000 – 1.0(0.3) – –
SiN? N=2-1, J=3/2-1/2 87.049857 6.3 – – –
HN [13] C 1-0 87.090825 4.2 13.2(0.4) – –
C 4 H, ν 7 = 1 J=19/2-17/2,Ω=3/2, l=e 87.142857 265.5 2.9(0.7) – –
C 2 H N=1-0 [(] _[a]_ [)] 87.316898 4.2 264.3(1.0) 58.5(0.6) 7.6(0.2)
C 6 H J=63/2-61/2, Ω=3/2, l=e 87.321504 67.9 bl. bl. –
C 6 H J=63/2-61/2, Ω=3/2, l=f 87.347994 67.9 2.1(0.5) 0.6(0.2) –
C 4 H, ν 7 = 1 J=19/2-17/2,Ω=3/2, l=f 87.371999 265.5 5.0(0.6) 2.0(0.3) –
30 c-CSiS 3 H 2 55-4 4,2 -5 3,3 87.43531887.550558 45.312.6 bl.bl. bl.bl. bl.–
SiN N=2-1, J=5/2-3/2 87.559811 6.3 bl. bl. –
u – 87.590000 – 1.0(0.3) – –
H [13] CC [13] CN 10-9 87.773712 23.2 4.2(0.3) – –
H [13] C [13] CCN 10-9 87.841102 23.2 2.9(0.3) – –
HC 5 N 33-32 87.863630 71.7 4.8(0.2) 6.2(0.1) 2.0(0.1)
C 6 H J=63/2-61/2, Ω=1/2, l=f 87.921593 90.7 2.5(0.5) 0.6(0.2) –
C 6 H J=63/2-61/2, Ω=1/2, l=e 87.967595 90.7 1.7(0.4) 1.1(0.2) –
HCN, ν 1 = 1? 1-0 88.006690 4768.7 – – –
HCN, ν 3 = 1? 1-0 88.027280 3021.1 – – –


Article number, page 26 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table B.1: continued.


Molecule Transition Rest Freq. (GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (Jy km/s)

15194 15082 07454

H [13] CCCN 10-9 88.166832 23.3 14.9(0.2) 1.8(0.1) 1.3(0.1)
Si [34] S 5-4 88.285828 12.7 – 0.7(0.1) 0.3(0.1)
C [13] CCN N=9-8 [(] _[a]_ [)] 88.561247 11.8 9.0(0.4) – –
HCN 1-0 88.631602 4.3 294.6(0.2) 224.8(0.1) 81.2(0.1)
CC [13] CN N=9-8, J=19/2-17/2 88.711791 11.8 4.9(0.2) – –
CC [13] CN N=9-8, J=17/2-15/2 88.730291 11.8 4.5(0.2) – –
l-C 4 H 2 10 1,10 -9 1,9 88.940236 37.0 1.8(0.5) 1.5(0.4) –
C 3 N 9-8 (A) 89.045592 21.4 18.1 (0.2) 10.4 (0.1) 2.0(0.1)
C 3 N 9-8 (B) 89.064352 21.4 18.1 (0.2) 10.0(0.1) 1.8(0.1)
HCN, ν 2 = 2 1 0 -0 0 89.087690 2035.0 2.5(0.2) 2.9(0.3) 0.7(0.1)
29 SiS 5-4 89.103749 12.8 2.5(0.2) 1.7(0.1) 0.4(0.1)
l-C 4 H 2 10 3,8 -9 3,7 89.289791 145.2 bl. bl. –
13 l-CCH 4 H 32 CN 510 4 -4 3,74 -9 3,6 89.28979389.304386 145.2127.4 bl.bl. bl.– ––
l-C 4 H 2 10 2,9 -9 2,8 89.305141 77.6 bl. bl. –
13 l-CCH 4 H 32 CN 510 3 -4 2,83 -9 2,7 89.30756389.316149 77.677.3 bl.bl. bl.– ––
13 CH 3 CN 5 2 -4 2 89.324555 41.5 bl. – –
13 CH 3 CN 5 1 -4 1 89.329599 20.0 bl. – –
13 CH 3 CN 5 0 -4 0 89.331282 12.9 bl. – –
l-C 4 H 2 10 1,9 -9 1,8 89.687047 37.2 bl. bl. –
C 6 H J=65/2-63/2, Ω=3/2, l=e 90.093295 72.2 3.5(0.5) – –
C 6 H J=65/2-63/2, Ω=3/2, l=f 90.121407 72.2 3.6(0.5) – –
HC [13] C [13] CN 10-9 90.204324 23.8 3.3(0.3) – –
HC 5 N 34-33 90.525890 76.0 3.9(0.2) 5.8(0.1) 1.8(0.1)
30 SiC 2 4 0,4 -3 0,3 90.562283 10.9 1.2(0.4) 0.9(0.3) –
HC [13] CCN 10-9 90.593059 23.9 16.4(0.2) (bl.) 2.3(0.4) (bl.) 1.2(0.1)
HCC [13] CN 10-9 90.601777 23.9 16.4(0.2) (bl.) 2.3(0.4) (bl.) 1.3(0.1)
HNC 1-0 90.663568 4.4 74.9(0.2) 36.5(0.1) 6.7(0.1)
CCS 7 7 -6 6 90.686381 26.1 1.8(0.4) 2.1(0.4) –
C 6 H J=65/2-63/2, Ω=1/2, l=f 90.712181 95.0 3.3(0.6) – –
C 6 H J=65/2-63/2, Ω=1/2, l=e 90.759297 95.1 bl. bl. –
SiS 5-4 90.771564 13.1 44.4(0.2) 22.9(0.1) 9.9(0.1)
Si [13] CC 4 0,4 -3 0,3 90.848527 11.0 6.9(0.2) – –
C 8 H J=155/2-153/2, Ω=3/2bbm 90.924649 171.2 4.0(0.6) – –
HC 3 N 10-9 90.979023 24.0 75.6(0.5) 56.1(0.3) 24.7(0.1)
13 CCCCH N=10-9, J=21/2-19/2 91.875516 24.3 3.6(0.4) – –
13 CCCCH N=10-9, J=19/2-17/2 91.906057 24.3 3.4(0.4) – –
CH 3 CN 5-4 [(] _[a]_ [)] 91.979995 41.8 15.4(0.8) 4.0(0.3) bl.
Si [13] CC 4 2,3 -3 2,2 92.064397 18.5 4.3(0.4) – –
CCC [13] CH N=10-9, J=21/2-19/2 92.277460 24.4 4.1(0.4) – –
CCC [13] CH N=10-9, J=19/2-17/2 92.314915 24.4 6.0(0.4) – –
Si [13] CC 4 3,2 -3 3,1 92.375409 27.9 2.7(0.4) – –
13 SiCS [13] CC 2-14 3,1 -3 3,0 92.40221692.494308 27.96.7 37.2(0.5)2.6(0.4) 2.9(0.3)– 2.1(0.1)–
SiC 2 4 0,4 -3 0,3 93.063639 11.2 39.7(0.4) 15.0(0.2) 5.5(0.1)
HC 5 N 35-34 93.188123 80.5 – – 1.6(0.1)
Si [13] CC 4 2,2 -3 2,1 93.432836 18.6 2.6(0.4) – –
C 4 H, ν 7 = 1 J=19/2-17/2,Ω=1/2, l=f 93.863370 272.1 bl. bl. bl.
CCS 7 8 -6 7 93.870107 19.9 bl. bl. bl.
SiC 2 4 2,3 -3 2,2 94.245393 19.1 26.4(0.4) 2.4(0.2) 3.8(0.1)
C [13] CCCH N=10-9, J=21/2-19/2 94.670247 25.0 5.4(0.4) – –
C [13] CCCH N=10-9, J=19/2-17/2 94.708239 25.0 4.7(0.4) – –
CC [13] CCH N=10-9, J=21/2-19/2 94.814723 25.0 4.4(0.4) – –
CC [13] CCH N=10-9, J=19/2-17/2 94.853133 25.0 6.4(0.4) – –
C 4 H N = 10-9, J = 21/2-19/2 95.150389 25.1 42.7(0.4) 9.3(0.3) 0.9(0.1)
C 4 H N = 10-9, J = 19/2-17/2 95.188949 25.1 43.5(0.4) 7.4(0.3) 1.0(0.1)
SiC 2 4 2,2 -3 2,1 95.579381 19.2 22.6(0.4) 12.0(0.3) 4.1(0.1)
C 4 H, ν 7 = 2 [0] N=10-9, J=21/2-19/2 95.611500 561.5 2.5(0.8) – –
C 4 H, ν 7 = 2 [0] N=10-9, J=19/2-17/2 95.667900 561.5 3.2(0.8) – –
HC 5 N 36-35 95.850335 85.1 – – 1.5(0.1)
C [34] S 2-1 96.412950 6.9 13.0(0.4) 6.6(0.2) 3.7(0.1)
C 4 H, ν 7 = 1 J=21/2-19/2,Ω=3/2, l=e 96.478780 270.1 2.1(0.7) – –


Article number, page 27 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


Table B.1: continued.


Molecule Transition Rest Freq. (GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (Jy km/s)

15194 15082 07454

H [13] CC [13] CN? 11-10 96.550615 27.8 – – –
C 4 H, ν 7 = 1 J=21/2-19/2,Ω=3/2, l=f 96.741210 270.2 2.7(0.9) – –
H [13] CCCN 11-10 96.983001 27.9 10.3(0.4) – 1.3(0.1)
C [33] S 2-1 97.172064 7.0 2.8(0.5) – –
CS, _v_ = 1? 2-1 97.270980 1837.4 – – –
Si [13] CC 4 1,3 -3 1,2 97.295257 13.6 7.4(0.5) – –
CS 2-1 97.980953 7.1 252.5(0.5) 127.7(0.2) 55.6(0.1)
C 3 H J=9/2-7/2, Ω=1/2 [(] _[a]_ [)] 98.012070 12.5 20.9(0.7) – 1.9(0.1)
C [13] CCN N=10-9 [(] _[a]_ [)] 98.401860 14.8 17.0(2.3) – –
HC 5 N 37-36 98.512524 89.8 – – 1.7(0.1)
CC [13] CN N=10-9, J=21/2-19/2 98.569079 14.8 3.9(0.5) – –
CC [13] CN N=10-9, J=19/2-17/2 98.587484 14.8 5.2(0.5) – –
C 3 N 10-9 (A) 98.940005 26.1 16.7 (0.5) 10.5(0.2) 3.2(0.1)
C 3 N 10-9 (B) 98.958774 26.1 19.0(0.5) 11.5(0.2) 2.9(0.1)
HC [13] C [13] CN 11-10 99.224259 28.6 3.1(0.4) – –
HC [13] CCN 11-10 99.651849 28.7 13.8(0.1) (bl.) 2.4(0.4) (bl.) 1.7(0.1)
HCC [13] CN 11-10 99.661467 28.7 13.8(0.1) (bl.) 2.4(0.4) (bl.) 1.6(0.1)
CCS 8 7 -7 6 99.866521 28.1 3.1(0.8) 1.3(0.4) 0.5(0.1)
HC 3 N 11-10 100.076392 28.8 71.8(0.2) 65.5(0.1) 27.5(0.1)
u – 100.407000 – 1.1(0.3) – –
13 CCCCH N=11-10, J=23/2-21/2 101.063060 29.1 6.5(0.2) – –
13 CCCCH N=11-10, J=21/2-19/2 101.094030 29.1 6.3(0.2) – –
HC 5 N 38-37 101.174677 94.7 3.2(0.2) 3.6(0.1) 1.4(0.1)
CCC [13] CH N=11-10, J=23/2-21/2 101.506343 29.2 7.7(0.2) – –
CCC [13] CH N=11-10, J=21/2-19/2 101.543766 29.2 7.9(0.2) – –
30 SiS, _v_ = 5 6-5 102.548508 5206.0 3.0(0.5) – –
C 4 H, ν 7 = 1 J=21/2-19/2,Ω=1/2, l=e 103.266200 277.0 3.1(1.0) – –
C 3 H J=9/2-7/2, Ω=3/2 [(] _[a]_ [)] 103.319530 32.9 4.7(0.7) – –
C 4 H, ν 7 = 1 J=21/2-19/2,Ω=1/2, l=f 103.576590 277.1 5.0(1.0) – –
CCS 8 8 -7 7 103.640759 31.1 3.2(1.0) – –
HC 5 N 39-38 103.836817 99.7 – – 1.3(0.1)
C [13] CCCH N=11-10, J=23/2-21/2 104.138540 30.0 9.8(0.5) – –
C [13] CCCH N=11-10, J=21/2-19/2 104.176220 30.0 8.8(0.5) – –
CC [13] CCH N=11-10, J=23/2-21/2 104.297340 30.0 8.8(0.5) – –
CC [13] CCH N=11-10, J=21/2-19/2 104.335720 30.1 10.3(0.5) – –
C 4 H N = 11-10, J = 23/2-21/2 104.666566 30.1 53.7(0.5) 5.6(0.3) 1.3(0.1)
C 4 H N = 11-10, J = 21/2-19/2 104.705110 30.2 55.5(0.5) 10.6(0.3) 1.0(0.1)
30 SiS 6-5 105.059203 17.6 – – 0.5(0.1)
C 4 H, ν 7 = 2 [0] N=11-10, J=23/2-21/2 105.174600 566.5 2.6(0.8) – –
C 4 H, ν 7 = 2 [0] N=11-10, J=21/2-19/2 105.230990 566.5 5.0(0.8) – –
H [13] CCCN 12-11 105.799113 33.0 9.0(0.5) – 1.2(0.1)
C 4 H, ν 7 = 1 J=23/2-21/2,Ω=3/2, l=e 105.837997 219.2 4.6(1.2) – –
Si [34] S 6-5 105.941503 17.8 2.2(0.5) – 0.5(0.1)
C 4 H, ν 7 = 1 J=23/2-21/2,Ω=3/2, l=f 106.133368 219.2 3.2(0.9) – –
CCS 8 9 -7 8 106.347726 25.0 3.0(1.0) – 0.6(0.2)
HC 5 N 40-39 106.498910 104.8 – – 1.2(0.1)
29 SiS 6-5 106.922980 18.0 3.0(0.5) – 0.8(0.1)
Si [13] CC 5 1,5 -4 1,4 107.971477 17.5 6.5(0.5) – –
C [13] CCN N=11-10 [(] _[a]_ [)] 108.242334 18.1 bl. – –
HC [13] C [13] CN 12-11 108.244051 33.8 bl. – –
SiS, _v_ = 1 6-5 108.394291 1089.3 – – –
CC [13] CN N=11-10, J=23/2-21/2 108.426168 18.1 bl. – –
CC [13] CN N=11-10, J=21/2-19/2 108.444688 18.1 3.1(0.5) – –
13 CN N= 1-0 108.780201 5.2 bl. bl. bl.
HC [13] CCN 12-11 108.710532 33.9 8.8(0.1) (bl.) – 1.6(0.1)
HCC [13] CN 12-11 108.720999 33.9 8.8(0.1) (bl.) – 1.4(0.1)
C 3 N 11-10 (A) 108.834250 31.3 10.7(0.6) 4.7(0.2) 3.8(0.1)
C 3 N 11-10 (B) 108.853005 31.3 16.4(0.6) 6.2(0.2) 3.6(0.1)
SiS 6-5 108.924301 18.3 46.1(0.6) 26.9(0.2) 11.6(0.1)
HC 5 N 41-40 109.160973 110.0 bl. bl. bl.
HC 3 N 12-11 109.173634 34.1 57.8(0.6) 50.1(0.3) 32.5(0.1)
13 CO 1-0 110.201354 5.3 119.6(1.6) – 18.4(0.2)
13 CCCCH N=12-11, J=25/2-23/2 110.250280 34.4 4.4(0.5) – –


Article number, page 28 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table B.1: continued.


Molecule Transition Rest Freq. (GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (Jy km/s)

15194 15082 07454


13 CCCCH N=12-11, J=23/2-21/2 110.281796 34.4 6.2(0.7) – –
CH 3 CN 6-5 [(] _[a]_ [)] 110.374989 47.1 bl. bl. bl.
CCC [13] CH N=12-11, J=25/2-23/2 110.735027 34.5 5.2(0.6) – –
CCC [13] CH N=12-11, J=23/2-21/2 110.772434 34.6 7.0(0.6) – –
HC 5 N 42-41 111.823024 115.4 – – 1.2(0.1)
Si [13] CC 5 0,5 -4 0,4 112.593212 16.4 8.0(0.6) – –
C 4 H, ν 7 = 1? J=23/2-21/2,Ω=1/2, l=e 112.922950 282.5 – – –
C 4 H, ν 7 = 1? J=23/2-21/2,Ω=1/2, l=f 113.266080 282.5 – – –
CN N= 1-0 [(] _[a]_ [)] 113.488120 5.4 179.0(2.0) 188.0(1.0) 256.5(0.4)
C [13] CCCH N=12-11, J=25/2-23/2 113.606341 35.4 7.4(0.6) – –
C [13] CCCH N=12-11, J=23/2-21/2 113.644283 35.5 6.9(0.6) – –
CC [13] CCH N=12-11, J=25/2-23/2 113.779720 35.5 9.1(0.6) – –
CC [13] CCH N=12-11, J=23/2-21/2 113.818080 35.5 13.1(0.6) – –
C 4 H N = 12-11, J = 25/2-23/2 114.182514 35.6 59.2(0.9) 14.9(0.7) 1.6(0.2)
C 4 H N = 12-11, J = 23/2-21/2 114.221044 35.6 66.6(0.9) 17.7(0.7) 2.0(0.2)
H [13] CCCN 13-12 114.614995 38.5 6.8(0.9) – 1.5(0.2)
CO 1-0 115.271202 5.5 439.2(2.0) [(] _[b]_ [)] 120.8(1.1) 166.7(0.5)
SiC 2 5 0,5 -4 0,4 115.382389 16.8 53.1(0.9) 28.2(0.7) 13.0(0.2)


**Notes.** All transitions listed are in the ground vibrational state unless otherwise specified. [(] _[a]_ [)] Lines with hyperfine components where only the
frequency of one of the components has been listed, but the integrated intensity given has been summed over all detected components. [(] _[b]_ [)] The
extended CO emission in IRAS 15194-5115 is not fully recovered by the observations. The line intensity given is hence underestimated. bl.
indicates blends, either between hyperfine components of the same transition, or between different lines. A ‘?’ next to the molecule name indicates
a tentative detection. The values in parentheses are the uncertainties obtained from the rms noise.


Table B.2: Details of the lines from APEX observations used in the population diagrams.


Molecule Transition Rest Freq.(GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (K km/s)


15194 15082 07454

C 4 H N=17-16 161.796566 70.5 5.83(1.17) 1.84(0.37) –
SiS 9-8 163.376785 39.3 4.18(0.84) 2.99(0.60) 1.80(0.36)
HC 3 N J=18-17 163.753389 73.9 0.84(0.19) 1.26(0.26) 0.75(0.15)
SiC 2 7 2,6 -6 2,5 164.069091 39.4 1.94(0.40) 1.46(0.29) 0.83(0.17)
C 3 N N=17-16 168.213682 72.0 – 1.10(0.24) –
C 4 H N=18-17 171.310707 78.8 5.53(1.11) 1.88(0.38) –
29 SiO 4-3 171.512796 20.5 0.96(0.21) 0.41(0.09) 0.21(0.06)
H [13] CN J=2-1 172.677851 12.4 20.58(4.12) 5.32(1.07) 3.49(0.70)
HC 3 N J=19-18 172.849300 82.1 0.54(0.13) 0.87(0.18) 0.65(0.14)
SiO 4-3 173.688238 20.8 9.94(1.99) 4.60(0.92) 1.90(0.38)
C 2 H N=2-1 174.663199 12.6 43.70(8.75) 17.10(3.44) 4.20(0.86)
HCN J=2-1 177.261111 12.8 34.48(6.90) 21.55(4.31) 8.41(1.68)
C 4 H N=19-18 180.824472 87.6 5.69(1.14) – –
HNC J=2-1 181.324758 13.0 4.39(0.88) – –
SiS 10-9 181.525218 48.0 3.93(0.79) – –
13 CS J=4-3 184.981772 22.2 3.67(0.74) – –
SiC 2 8 6,3 -7 6,2 188.385700 110.9 – 0.38(0.11) –
C 4 H N=20-19 190.337804 96.8 5.06(1.02) 1.97(0.40) –
HC 3 N J=21-20 191.040299 99.8 – 0.62(0.13) 0.49(0.11)
C [34] S 4-3 192.818457 23.1 1.67(0.35) 1.14(0.23) 0.61(0.13)
CS 4-3 195.954211 23.5 17.34(3.47) 12.81(2.56) –
SiS 11-10 199.672229 57.7 4.11(0.83) 3.32(0.66) 1.91(0.38)
C 4 H N=21-20 199.850787 106.4 4.91(0.99) 2.33(0.47) –
HC 3 N J=23-22 209.230234 119.2 – 0.22(0.05) 0.22(0.05)
C 4 H N=22-21 209.363302 116.6 3.66(0.74) 1.98(0.40) 0.34(0.07)
SiC 2 9 2,8 -8 2,7 209.892001 58.5 1.32(0.27) 1.59(0.32) 1.04(0.21)
SiC 2 9 6,4 -8 6,3 212.031878 121.1 0.53(0.14) 0.36(0.10) 0.31(0.08)
SiC 2 9 4,6 -8 4,5 213.208032 82.3 1.04(0.21) 0.70(0.14) –
SiC 29 SiS 2 912-11 4,5 -8 4,4 213.816140213.292337 66.682.3 1.09(0.22)– 0.160.74(0.15)(0.03) 0.180.69(0.14)(0.04)


Article number, page 29 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


Table B.2: continued.


Molecule Transition Rest Freq. (GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (K km/s)

15194 15082 07454


29 SiO 5-4 214.385752 30.8 1.18(0.24) 0.41(0.08) 0.30(0.06)
SiO 5-4 217.104919 31.2 11.40(2.28) 4.56(0.91) 2.73(0.55)
SiS 12-11 217.817663 68.1 3.92(0.78) 2.90(0.58) 2.34(0.47)
HC 3 N J=24-23 218.324723 129.6 – 0.24(0.05) 0.25(0.05)
C 4 H N=23-22 218.875369 127.2 2.73(0.55) 1.25(0.26) 0.37(0.08)
SiC 2 10 0,10 -9 0,9 220.773685 59.8 1.51(0.31) 1.13(0.23) 1.23(0.25)
SiC 2 9 2,7 -8 2,6 222.009386 60.2 1.66(0.33) 1.19(0.24) 1.21(0.24)
HC 3 N J=25-24 227.418905 140.4 – 0.22(0.05) 0.18(0.04)
C 3 N N=23-22 227.563276 129.8 – – 0.45(0.09)
C 4 H N=24-23 228.386962 138.2 3.46(0.70) 1.27(0.26) 0.43(0.09)
Si [34] S 13-12 229.500868 76.9 – 0.19(0.04) 0.18(0.04)
13 CS J=5-4 231.220685 33.3 5.37(1.07) – –
29 SiS 13-12 231.626673 77.8 – 0.18(0.04) 0.23(0.05)
SiC 2 10 2,9 -9 2,8 232.534070 69.6 1.60(0.32) 1.07(0.21) 1.20(0.24)
SiC 2 10 6,5 -9 6,4 235.712998 132.4 0.47(0.13) 0.36(0.10) 0.39(0.10)
SiS 13-12 235.961363 79.5 6.50(1.30) 3.46(0.69) 2.94(0.59)
HC 3 N J=26-27 236.512789 151.6 – 0.17(0.04) 0.18(0.04)
SiC 2 10 4,7 -9 4,6 237.150018 93.7 0.79(0.16) 0.76(0.15) 0.86(0.17)
SiC 2 10 4,6 -9 4,5 237.331309 93.7 1.01(0.20) 0.71(0.14) 0.76(0.15)
C 3 N N=24-23 237.453530 141.1 – – 0.38(0.08)
C 4 H N=25-24 237.898060 149.8 2.76(0.56) 0.96(0.20) 0.37(0.08)
C [34] S 5-4 241.016089 34.7 1.44(0.29) 0.91(0.18) 0.65(0.13)
SiC 2 11 0,11 -10 0,10 241.367708 71.4 1.07(0.22) 0.99(0.20) 1.21(0.24)
CS 5-4 242.913610 35.3 24.27(4.85) 10.98(2.20) 7.98(1.60)
Si [34] S 14-13 244.935556 88.7 – 0.18(0.04) 0.22(0.04)
C 3 N N=25-24 247.146242 152.9 – – 0.31(0.07)
C 4 H N=26-25 247.343351 161.7 – 0.81(0.17) 0.34(0.07)
SiC 29 SiS 2 1014-13 2,8 -9 2,7 247.529119247.408643 89.772.1 1.36(0.27)– 0.14(0.03)1.11(0.22) 0.23(0.05)1.33(0.27)
SiS 14-13 249.435412 91.7 5.50(1.10) 3.08(0.62) 3.53(0.71)
30 SiO 6-5 254.103211 42.7 0.77(0.16) – –
C 4 H N=27-26 254.216656 174.2 – 0.62(0.13) 0.34(0.07)
29 SiO 6-5 256.918691 43.1 1.11(0.22) 0.40(0.08) 0.31(0.06)
H [13] CN J=3-2 257.255213 24.9 25.64(5.13) 5.88(1.18) 5.86(1.17)
SiC 2 11 6,6 -10 6,5 259.011798 144.8 – 0.31(0.08) 0.37(0.10)
SiO 6-5 259.433309 43.7 10.23(2.05) 4.53(0.91) 3.16(0.63)
SiC 2 11 4,8 -10 4,7 260.518009 106.2 0.68(0.14) 0.55(0.11) 0.67(0.14)
SiC 2 11 4,7 -10 4,6 261.150695 106.2 0.61(0.13) 0.50(0.10) 0.68(0.14)
C 2 H N=3-2 261.509329 25.2 48.90(9.79) 25.30(5.07) 10.60(2.14)
30 SiS 15-14 262.064986 100.2 – – 0.19(0.04)
Si [34] S 15-14 262.585033 101.4 – – 0.21(0.04)
HCN J=3-2 264.789719 25.5 58.90(11.78) 27.29(5.46) 14.82(2.96)
C 4 H N=28-27 265.886434 187.1 – 0.48(0.10) 0.32(0.07)
C 3 N N=27-26 266.428184 177.8 – – 0.27(0.06)
29 SiS 15-14 267.102873 102.5 – – 0.30(0.06)
SiS 15-14 267.242218 104.8 5.36(1.08) – –
13 CS J=6-5 272.243052 46.6 5.61(1.12) – –
C [34] S 6-5 277.455405 48.6 1.97(0.40) – –
SiS 16-15 289.209068 118.8 6.38(1.28) – –
CS 6-5 290.380757 49.4 20.15(4.03) – –
30 SiO 7-6 293.912086 57.0 0.62(0.14) – –
29 SiO 7-6 296.575740 57.5 0.96(0.20) – –
SiO 7-6 300.120477 58.3 10.04(2.01) – –
SiS 17-16 303.926812 133.7 3.99(0.80) – –
C [34] S 7-6 308.516144 64.8 1.82(0.37) – –
30 SiO 8-7 337.396459 73.3 0.82(0.18) – –
CS 7-6 338.930044 65.9 14.85(2.97) – –
29 SiO 8-7 342.882850 74.0 0.80(0.17) – –
SiS 19-18 342.980847 166.0 4.15(0.83) – –
H [13] CN J=4-3 344.779481 41.5 27.50(5.50) – –
SiO 8-7 345.339769 75.0 10.41(2.08) – –
C 2 H N=4-3 347.330581 42.0 70.90(14.19) – –
HCN J=4-3 349.339066 42.5 38.01(7.60) – –
HNC J=4-3 354.505477 43.5 2.13(0.43) – –


Article number, page 30 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table B.2: continued.


Molecule Transition Rest Freq. (GHz) _E_ up / _k_ B (K) � _S_ ul _d_ � (K km/s)

15194 15082 07454

SiS 20-19 362.630303 183.5 3.88(0.78) – –


**Notes.** All transitions listed are in the ground vibrational state. For lines with hyperfine components, only the frequency of one of the components
has been listed, but the integrated intensity given has been summed over all detected components. The values in parentheses denote the total
uncertainty in the integrated intensity, including the 20% uncertainty in flux calibration.


**Appendix C:** **Emission maps and line spectra**



The below figures show the line emission maps (top panels) averaged over ±20% of the expansion velocity around the
systemic velocity, and the line spectra (bottom panels), for
IRAS 15194−5115 (left), IRAS 15082−4808 (centre), and IRAS
07454−7112 (right). The figures are ordered in increasing order
of line rest frequency, which is given in parentheses at the end of
the figure caption. The white contours in the emission maps are


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0

|Col1|Col2|
|---|---|
|||



70 20 30
Velocity (km/s)



at 3, 10 and 30 sigma. The synthesised beams are shown as filled
white ellipses at the bottom left of each map. The grey-shaded regions in the line spectra represent the channels used for calculating the integrated intensities of the lines, reported in Table B.1.
The dotted vertical line in the line spectra marks the systemic
velocity of the source. Missing plots indicate non-detection of
the concerned line towards the particular source.



Fig. C.1: C [13] CCCH, N=9-8, J=19/2-17/2 (85.201906 GHz)



Article number, page 31 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)


Fig. C.2: C [13] CH, N=1-0, J=3/2-1/2 (85.232792 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||



10.0 0.0 -10.0

RA offset ( )


0.15


0.10


0.05


0.00


0.05

40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.3: c-C 3 H 2, 2 1,2 -1 0,1 (85.338894 GHz)



Article number, page 32 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0

|Col1|Col2|
|---|---|
|||



70 20 30
Velocity (km/s)


Fig. C.4: CC [13] CCH, N=9-8, J=17/2-15/2 (85.37033 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


1.00


0.75


0.50


0.25


0.00


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||



10.0 0.0 -10.0

RA offset ( )


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.04


0.02


0.00


0.02



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.5: C 4 H, N=9-8, J=19/2-17/2 (85.634004 GHz)



Article number, page 33 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.5 5.0 7.5


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


1.00


0.75


0.50


0.25


0.00


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.6: C 4 H, N=9-8, J=17/2-15/2 (85.672582 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0 6.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.10


0.05


0.00


0.05


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.7: [29] SiO, 2-1 (85.759194 GHz)



Article number, page 34 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 100.0 200.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


12.5


10.0


7.5


5.0


2.5



IRAS 15082-4808


mJy/beam
0.0 20.0 40.0


10.0


0.0


-10.0

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||||



10.0 0.0 -10.0

RA offset ( )


1.5


1.0


0.5


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 100.0 200.0


8.0


0.0


-8.0

|Col1|Col2|
|---|---|
|||
|||



8.0 0.0 -8.0

RA offset ( )


1.5


1.0


0.5



70 40 10
Velocity (km/s)


Article number, page 35 of 114



0.0


12.0


0.0


-12.0



70 20 30
Velocity (km/s)



0.0



Fig. C.8: H [13] CN, 1-0 (86.339921 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0



12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


0.1

70 20 30
Velocity (km/s)


Fig. C.9: Si [13] CC, 4 1,4 -3 1,3 (86.562636 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 50.0 100.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


3


2


1


0

70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 20.0 40.0 60.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


1.25


1.00


0.75


0.50


0.25


0.00

40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 50.0 100.0 150.0


8.0


0.0


-8.0

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||||



8.0 0.0 -8.0

RA offset ( )


0.6


0.4


0.2


0.0

70 40 10
Velocity (km/s)



Fig. C.10: SiO, 2-1 (86.846985 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.4


0.2


0.0

|Col1|Col2|
|---|---|
|||



70 20 30
Velocity (km/s)


Fig. C.11: HN [13] C, 1-0 (87.090825 GHz)



Article number, page 36 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.08


0.06


0.04


0.02


0.00


40 0 40
Velocity (km/s)



Fig. C.12: C 2 H, N=1-0, J=3/2-1/2, F=1-1 (87.284105 GHz)



IRAS 15194-5115


mJy/beam
0.0 5.0 10.0


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


3


2


1



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )





8.0


0.0


-8.0



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0







8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)





0



70 20 30
Velocity (km/s)





40 0 40
Velocity (km/s)



Fig. C.13: C 2 H, N=1-0, J=3/2-1/2, F=2-1 (87.316898 GHz)



Article number, page 37 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )

0.10


0.08


0.06


0.04


0.02


0.00


40 0 40
Velocity (km/s)



Fig. C.14: C 2 H, N=1-0, J=1/2-1/2, F=1-0 (87.44647 GHz)


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.010


0.005


0.000


0.005


70 40 10
Velocity (km/s)


Fig. C.15: [30] SiS, 5-4 (87.550558 GHz)



Article number, page 38 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


70 20 30
Velocity (km/s)


Fig. C.16: H [13] CC [13] CN, 10-9 (87.773712 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.100


0.075


0.050


0.025


0.000


0.025


70 20 30
Velocity (km/s)


Fig. C.17: H [13] C [13] CCN, 10-9 (87.841102 GHz)



Article number, page 39 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0 3.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

RA offset ( )

0.25


0.20


0.15


0.10


0.05


0.00

40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.08


0.06


0.04


0.02


0.00



Fig. C.18: HC 5 N, 33-32 (87.86363 GHz)



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.5


0.4


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

RA offset ( )


0.08


0.06


0.04


0.02


0.00


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.19: H [13] CCCN, 10-9 (88.166832 GHz)



Article number, page 40 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

|Col1|10.0 0.0 RA offset|Col3|-10.0 ( )|Col5|
|---|---|---|---|---|
||||||
|01<br>02||||0<br>0.0|
|00|00|00|00|0.0<br>.|
|00|||||
|00|||||



40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.010


0.005


0.000


0.005



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )



Fig. C.20: Si [34] S, 5-4 (88.285828 GHz)



70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 200.0 400.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


4


3


2


1



IRAS 15194-5115


mJy/beam

0.0 50.0 100.0 150.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


12.5


10.0


7.5


5.0


2.5



IRAS 15082-4808


mJy/beam

0.0 50.0 100.0 150.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )

10


8


6


4


2



70 40 10
Velocity (km/s)


Article number, page 41 of 114



40 0 40
Velocity (km/s)



0.0



70 20 30
Velocity (km/s)



0



0



Fig. C.21: HCN, 1-0 (88.631602 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


70 20 30
Velocity (km/s)


Fig. C.22: CC [13] CN, N=9-8, J=19/2-17/2 (88.7117 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


70 20 30
Velocity (km/s)


Fig. C.23: CC [13] CN, N=9-8, J=17/2-15/2 (88.7302 GHz)



Article number, page 42 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0 3.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0



8.0


0.0


-8.0


0.100


0.075


0.050


0.025


0.000



8.0 0.0 -8.0

RA offset ( )



Fig. C.24: C 3 N, 9-8 (A) (89.0456 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )

0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.100


0.075


0.050


0.025


0.000



70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 43 of 114



Fig. C.25: C 3 N, 9-8 (B) (89.0643 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0



IRAS 15082-4808


mJy/beam


10.0


0.0


-10.0



12.0


0.0


-12.0



8.0


0.0


-8.0



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


|0.0 1.0 mJy/b|2.0 3.0 beam|
|---|---|
|||
|||



12.0 0.0 -12.0

RA offset ( )


0.08



10.0 0.0 -10.0

RA offset ( )


0.015



0.06


0.04


0.02


0.00


12.0


0.0


-12.0



0.100


0.075


0.050


0.025


0.000



0.010


0.005


0.000


0.005



70 20 30
Velocity (km/s)



40 0 40
Velocity (km/s)



Fig. C.26: [29] SiS, 5-4 (89.103749 GHz)



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.04


0.02


0.00


40 0 40
Velocity (km/s)



12.0 0.0 -12.0

RA offset ( )


0.08


0.06


0.04


0.02


0.00


0.02


70 20 30
Velocity (km/s)



Fig. C.27: l-C 4 H 2, 10 3,8 -9 3,7 (89.289791 GHz)



Article number, page 44 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.08


0.06


0.04


0.02


0.00


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.04


0.03


0.02


0.01


0.00


0.01

40 0 40
Velocity (km/s)



Fig. C.28: C 6 H, J=65/2-63/2 (90.093295 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.10


0.05


0.00


70 20 30
Velocity (km/s)


Fig. C.29: HC [13] C [13] CN, 10-9 (90.204324 GHz)



Article number, page 45 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0 3.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.20


0.15


0.10


0.05


0.00


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.08


0.06


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 5.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.30: HC 5 N, 34-33 (90.52589 GHz)



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.100


0.075


0.050


0.025


0.000


0.025


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.04


0.02


0.00

|Col1|Col2|
|---|---|
|||



40 0 40
Velocity (km/s)



Fig. C.31: [30] SiC 2, 4 0,4 -3 0,3 (90.562283 GHz)



Article number, page 46 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0



12.0


0.0


-12.0



10.0


0.0


-10.0



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


|Col1|Col2|
|---|---|
|||


|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )



10.0 0.0 -10.0

RA offset ( )



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



1.0


0.8


0.6


0.4


0.2


0.0


12.0


0.0


-12.0



0.125


0.100


0.075


0.050


0.025


0.000



70 20 30
Velocity (km/s)



40 0 40
Velocity (km/s)



Fig. C.32: HC [13] CCN, 10-9 (90.593059 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


|Col1|Col2|
|---|---|
|||


|0.0 1.0 mJy/b|2.0 beam|
|---|---|
|||
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 47 of 114



12.0 0.0 -12.0

RA offset ( )


1.0


0.8


0.6


0.4


0.2


0.0

70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



Fig. C.33: HCC [13] CN, 10-9 (90.601777 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.5 5.0 7.5


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


2.5


2.0


1.5


1.0


0.5


0.0

70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0 6.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

RA offset ( )


1.25


1.00


0.75


0.50


0.25


0.00

40 0 40
Velocity (km/s)



Fig. C.34: HNC, 1-0 (90.663568 GHz)



IRAS 07454-7112


mJy/beam
0.0 10.0 20.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.3


0.2


0.1


0.0

70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 50.0 100.0 150.0


8.0


0.0


-8.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


0.3


0.2


0.1


0.0

70 40 10
Velocity (km/s)



IRAS 15194-5115


mJy/beam
0.0 20.0 40.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


1.25


1.00


0.75


0.50


0.25



IRAS 15082-4808


mJy/beam
0.0 10.0 20.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.8


0.6


0.4


0.2



0.00



70 20 30
Velocity (km/s)



0.0

40 0 40
Velocity (km/s)


Fig. C.35: SiS, 5-4 (90.771564 GHz)



Article number, page 48 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )



0.20


0.15


0.10


0.05


0.00


0.05


12.0


0.0


-12.0



70 20 30
Velocity (km/s)


Fig. C.36: Si [13] CC, 4 0,4 -3 0,3 (90.848527 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0



12.0 0.0 -12.0

RA offset ( )


0.10


0.05


0.00


70 20 30
Velocity (km/s)


Fig. C.37: C 8 H, J=155/2-153/2 (90.92464 GHz)



Article number, page 49 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 5.0 10.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


2


1


0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 10.0 20.0 30.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||
||||
||||



10.0 0.0 -10.0

RA offset ( )


2.0


1.5


1.0


0.5


0.0

40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 50.0 100.0


8.0


0.0


-8.0

|Col1|Col2|Col3|
|---|---|---|
||||
||||
||||



8.0 0.0 -8.0

RA offset ( )


1.0


0.8


0.6


0.4


0.2


0.0

70 40 10
Velocity (km/s)



Fig. C.38: HC 3 N, 10-9 (90.979023 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


0.05


70 20 30
Velocity (km/s)


Fig. C.39: [13] CCCCH, N=10-9, J=21/2-19/2 (91.875516 GHz)



Article number, page 50 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.10


0.05


0.00


0.05


70 20 30
Velocity (km/s)


Fig. C.40: [13] CCCCH, N=10-9, J=19/2-17/2 (91.906057 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


0.1


70 20 30
Velocity (km/s)


Fig. C.41: Si [13] CC, 4 2,3 -3 2,2 (92.064397 GHz)



Article number, page 51 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


0.1



0.2


12.0


0.0


-12.0



70 20 30
Velocity (km/s)


Fig. C.42: CCC [13] CH, N=10-9, J=21/2-19/2 (92.277495 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0



12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


0.1


70 20 30
Velocity (km/s)


Fig. C.43: CCC [13] CH, N=10-9, J=19/2-17/2 (92.31491 GHz)



Article number, page 52 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 10.0 20.0


12.0


0.0



10.0


0.0



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0



IRAS 07454-7112


mJy/beam
0.0 5.0


8.0


0.0


-8.0



-12.0



-10.0



12.0 0.0 -12.0

RA offset ( )

1.25


1.00


0.75


0.50


0.25


0.00


70 20 30
Velocity (km/s)



10.0 0.0 -10.0

RA offset ( )


0.10


0.05


0.00


40 0 40
Velocity (km/s)



8.0 0.0 -8.0

RA offset ( )


0.100



0.075


0.050


0.025


0.000



Fig. C.44: [13] CS, 2-1 (92.494308 GHz)



70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 10.0 20.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0



IRAS 15082-4808


mJy/beam
0.0 2.5 5.0 7.5



12.0


0.0


-12.0



10.0


0.0


-10.0


|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


1.25


1.00


0.75


0.50


0.25


0.00

70 20 30
Velocity (km/s)



10.0 0.0 -10.0

RA offset ( )



40 0 40
Velocity (km/s)







Fig. C.45: SiC 2, 4 0,4 -3 0,3 (93.063639 GHz)



70 40 10
Velocity (km/s)


Article number, page 53 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.08


0.06


0.04


0.02


0.00


70 40 10
Velocity (km/s)


Fig. C.46: HC 5 N, 35-34 (93.188123 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0



IRAS 15082-4808


mJy/beam
0.0 2.5 5.0 7.5



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0



10.0


0.0


-10.0


|Col1|Col2|Col3|
|---|---|---|
||||


|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



12.0 0.0 -12.0

RA offset ( )



10.0 0.0 -10.0

RA offset ( )



8.0


0.0


-8.0


0.20


0.15


0.10


0.05


0.00



1.00


0.75


0.50


0.25


0.00



0.100


0.075


0.050


0.025


0.000


0.025



70 20 30
Velocity (km/s)



40 0 40
Velocity (km/s)



Fig. C.47: SiC 2, 4 2,3 -3 2,2 (94.245393 GHz)



Article number, page 54 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


70 20 30
Velocity (km/s)


Fig. C.48: C [13] CCCH, N=10-9, J=21/2-19/2 (94.670583 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00



0.05



70 20 30
Velocity (km/s)


Fig. C.49: C [13] CCCH, N=10-9, J=19/2-17/2 (94.708235 GHz)



Article number, page 55 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )



0.20


0.15


0.10


0.05


0.00


0.05


12.0


0.0


-12.0



70 20 30
Velocity (km/s)


Fig. C.50: CC [13] CCH, N=10-9, J=21/2-19/2 (94.814724 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0



12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


70 20 30
Velocity (km/s)


Fig. C.51: CC [13] CCH, N=10-9, J=19/2-17/2 (94.853126 GHz)



Article number, page 56 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0 6.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.04


0.02


0.00


0.02



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.52: C 4 H, N=10-9, J=21/2-19/2 (95.150389 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.5 5.0 7.5


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


1.5


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0 6.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.4


0.2


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00


0.02



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.53: C 4 H, N=10-9, J=19/2-17/2 (95.188949 GHz)



Article number, page 57 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.8


0.6


0.4


0.2


0.0

70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.5 5.0 7.5


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0 15.0



8.0


0.0


-8.0


0.20


0.15


0.10


0.05


0.00



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5



Fig. C.54: SiC 2, 4 2,2 -3 2,1 (95.579381 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00


0.05

70 20 30
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.55: HC 5 N, 36-35 (95.850335 GHz)



Article number, page 58 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.5 5.0 7.5


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.20


0.15


0.10


0.05


0.00


8.0


0.0


-8.0


0.06


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.0 4.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 59 of 114



Fig. C.56: C [34] S, 2-1 (96.41295 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.4


0.2


0.0


70 20 30
Velocity (km/s)



Fig. C.57: H [13] CCCN, 11-10 (96.983001 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.10


0.05


0.00


0.05


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.075


0.050


0.025


0.000


0.025

|Col1|Col2|
|---|---|
|||



40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.58: C [33] S, 2-1 (97.172064 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


70 20 30
Velocity (km/s)


Fig. C.59: Si [13] CC, 4 1,3 -3 1,2 (97.295257 GHz)



Article number, page 60 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 50.0 100.0 150.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


8


6


4


2



IRAS 15082-4808


mJy/beam
0.0 50.0 100.0 150.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


4


3


2


1



IRAS 07454-7112


mJy/beam
0.0 100.0 200.0


|Col1|Col2|
|---|---|
|||
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||



8.0 0.0 -8.0

RA offset ( )

|Col1|Col2|
|---|---|
|||



70 40 10
Velocity (km/s)


Article number, page 61 of 114



40 0 40
Velocity (km/s)



0


12.0


0.0


-12.0



70 20 30
Velocity (km/s)


IRAS 15194-5115


mJy/beam
0.0 2.0



Fig. C.60: CS, 2-1 (97.980953 GHz)


IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0



0


|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0

|Col1|Col2|
|---|---|
|||



70 20 30
Velocity (km/s)



10.0 0.0 -10.0

RA offset ( )

0.15


0.10


0.05


0.00


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


3


2


1


0


8.0


0.0


-8.0


0.04


0.02


0.00



Fig. C.61: C 3 H, J=9/2-7/2 (98.01207 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 07454-7112


mJy/beam



8.0


0.0


-8.0


0.08


0.06


0.04


0.02


0.00


Fig. C.62: HC 5 N, 37-36 (98.512524 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0

|Col1|Col2|
|---|---|
|||



70 20 30
Velocity (km/s)


|0.0 2.5 mJy/b|5.0 7 beam|
|---|---|
|||
|||



8.0 0.0 -8.0

RA offset ( )

|Col1|Col2|
|---|---|
|||



70 40 10
Velocity (km/s)



Fig. C.63: CC [13] CN, N=10-9, J=21/2-19/2 (98.569 GHz)



Article number, page 62 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0



8.0


0.0


-8.0


0.15


0.10


0.05


0.00



8.0 0.0 -8.0

RA offset ( )



Fig. C.64: C 3 N, 10-9 (A) (98.94 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.5


0.4


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.0 4.0 6.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.15


0.10


0.05


0.00



70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 5.0 10.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 63 of 114



Fig. C.65: C 3 N, 10-9 (B) (98.9588 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.10


0.05


0.00


70 20 30
Velocity (km/s)


Fig. C.66: HC [13] C [13] CN, 11-10 (99.224259 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.8


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0 3.0


10.0


0.0


-10.0

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||



10.0 0.0 -10.0

RA offset ( )


0.100


0.075


0.050


0.025


0.000

40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.075


0.050


0.025


0.000


0.025



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.67: HC [13] CCN, 11-10 (99.651849 GHz)



Article number, page 64 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0



10.0


0.0


-10.0



IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


|Col1|Col2|
|---|---|
|||


|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )



10.0 0.0 -10.0

RA offset ( )



8.0


0.0


-8.0


0.08


0.06


0.04


0.02


0.00



0.8


0.6


0.4


0.2


0.0





70 20 30
Velocity (km/s)



40 0 40
Velocity (km/s)



Fig. C.68: HCC [13] CN, 11-10 (99.661467 GHz)



IRAS 15194-5115


mJy/beam
0.0 5.0 10.0


12.0


0.0


-12.0



IRAS 15082-4808


mJy/beam
0.0 5.0 10.0 15.0


10.0


0.0


-10.0



IRAS 07454-7112


mJy/beam
0.0 50.0 100.0


|Col1|Col2|
|---|---|
|||


|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 65 of 114



12.0 0.0 -12.0

RA offset ( )

2.5


2.0


1.5


1.0


0.5



10.0 0.0 -10.0

RA offset ( )


2.5


2.0


1.5


1.0


0.5



8.0


0.0


-8.0


1.25


1.00


0.75


0.50


0.25


0.00



0.0



70 20 30
Velocity (km/s)



40 0 40
Velocity (km/s)



0.0



Fig. C.69: HC 3 N, 11-10 (100.076392 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)


Fig. C.70: [13] CCCCH, N=11-10, J=23/2-21/2 (101.06306 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)


Fig. C.71: [13] CCCCH, N=11-10, J=21/2-19/2 (101.09403 GHz)



Article number, page 66 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 1.0 2.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.15


0.10


0.05


0.00

|Col1|Col2|
|---|---|
|||



40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00



IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )

|Col1|Col2|
|---|---|
|||



70 40 10
Velocity (km/s)



Fig. C.72: HC 5 N, 38-37 (101.174677 GHz)


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)


Fig. C.73: CCC [13] CH, N=11-10, J=23/2-21/2 (101.506343 GHz)



Article number, page 67 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 1.0 2.0 3.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.25


0.20


0.15


0.10


0.05


0.00

70 20 30
Velocity (km/s)


Fig. C.74: CCC [13] CH, N=11-10, J=21/2-19/2 (101.543766 GHz)


IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.06


0.04


0.02


0.00



0.02


Fig. C.75: HC 5 N, 39-38 (103.836817 GHz)



70 40 10
Velocity (km/s)



Article number, page 68 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)


Fig. C.76: C [13] CCCH, N=11-10, J=23/2-21/2 (104.13854 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


0.1


70 20 30
Velocity (km/s)


Fig. C.77: C [13] CCCH, N=11-10, J=21/2-19/2 (104.17622 GHz)



Article number, page 69 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


0.1

70 20 30
Velocity (km/s)


Fig. C.78: CC [13] CCH, N=11-10, J=23/2-21/2 (104.29734 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


0.1

70 20 30
Velocity (km/s)


Fig. C.79: CC [13] CCH, N=11-10, J=21/2-19/2 (104.33572 GHz)



Article number, page 70 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


1.5


1.0


0.5


0.0

70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )



40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )



70 40 10
Velocity (km/s)



0.3


0.2


0.1


0.0



0.075


0.050


0.025


0.000


0.025


0.050



Fig. C.80: C 4 H, N=11-10, J=23/2-21/2 (104.666566 GHz)



IRAS 15194-5115


mJy/beam


12.0


0.0


-12.0

|0.0 2.0 mJy/|4.0 6.0 /beam|
|---|---|
|||
|||



12.0 0.0 -12.0

RA offset ( )


1.5


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.5 5.0 7.5


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.6


0.4


0.2


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00


0.02



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.81: C 4 H, N=11-10, J=21/2-19/2 (104.70511 GHz)



Article number, page 71 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 07454-7112


mJy/beam
0.0 5.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.020


0.015


0.010


0.005


0.000


70 40 10
Velocity (km/s)


Fig. C.82: [30] SiS, 6-5 (105.059203 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


0.1

70 20 30
Velocity (km/s)



8.0


0.0


-8.0


0.06


0.04


0.02


0.00


0.02



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.83: H [13] CCCN, 12-11 (105.799113 GHz)



Article number, page 72 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.100


0.075


0.050


0.025


0.000


0.025


70 20 30
Velocity (km/s)



8.0


0.0


-8.0


0.02


0.01


0.00


0.01



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.84: Si [34] S, 6-5 (105.941503 GHz)



IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )



0.06


0.04


0.02


0.00


0.02


Fig. C.85: CCS, 8 9 -7 8 (106.347726 GHz)



70 40 10
Velocity (km/s)


Article number, page 73 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.06


0.04


0.02


0.00


0.02


70 40 10
Velocity (km/s)


Fig. C.86: HC 5 N, 40-39 (106.49891 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0

|Col1|Col2|Col3|
|---|---|---|
||||



12.0 0.0 -12.0

RA offset ( )


0.15


0.10


0.05


0.00

|Col1|Col2|
|---|---|
|||



70 20 30
Velocity (km/s)


Fig. C.87: [29] SiS, 6-5 (106.92298 GHz)



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0


8.0


0.0


-8.0


8.0 0.0 -8.0

RA offset ( )


0.02


0.01


0.00



0.01



70 40 10
Velocity (km/s)



Article number, page 74 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.2


0.1


0.0


70 20 30
Velocity (km/s)


Fig. C.88: Si [13] CC, 5 1,5 -4 1,4 (107.971477 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)



8.0


0.0


-8.0


0.100


0.075


0.050


0.025


0.000


0.025



IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 75 of 114



Fig. C.89: HC [13] CCN, 12-11 (108.710532 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



8.0


0.0


-8.0


0.100


0.075


0.050


0.025


0.000


0.025



Fig. C.90: HCC [13] CN, 12-11 (108.720999 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)



8.0


0.0


-8.0







IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.91: [13] CN, N=1-0, J=3/2-1/2 (108.782374 GHz)



Article number, page 76 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0 10.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 5.0 10.0



8.0


0.0


-8.0


0.20


0.15


0.10


0.05


0.00



8.0 0.0 -8.0

RA offset ( )



Fig. C.92: C 3 N, 11-10 (A) (108.83425 GHz)



70 40 10
Velocity (km/s)


IRAS 07454-7112


mJy/beam
0.0 5.0 10.0



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )

0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 2.5 5.0 7.5


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


40 0 40
Velocity (km/s)



8.0


0.0


-8.0


0.15


0.10


0.05


0.00


0.05



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)


Article number, page 77 of 114



Fig. C.93: C 3 N, 11-10 (B) (108.853 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 10.0 20.0 30.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


1.5


1.0


0.5


0.0

70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 20.0 40.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )

1.0


0.8


0.6


0.4


0.2


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 100.0 200.0


8.0


0.0


-8.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


0.3


0.2


0.1


0.0

70 40 10
Velocity (km/s)



Fig. C.94: SiS, 6-5 (108.924301 GHz)



IRAS 15194-5115


mJy/beam
0.0 5.0 10.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


2.0


1.5


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 10.0 20.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


2.0


1.5


1.0


0.5


0.0

40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 50.0 100.0



8.0


0.0


-8.0


1.5


1.0


0.5


0.0


|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.95: HC 3 N, 12-11 (109.173634 GHz)



Article number, page 78 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


70 20 30
Velocity (km/s)


Fig. C.96: CCC [13] CH, N=12-11, J=25/2-23/2 (110.735027 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.3


0.2


0.1


0.0


0.1


70 20 30
Velocity (km/s)


Fig. C.97: CCC [13] CH, N=12-11, J=23/2-21/2 (110.772434 GHz)



Article number, page 79 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS 07454-7112


mJy/beam
0.0 2.0 4.0 6.0



8.0


0.0


-8.0


0.06


0.04


0.02


0.00


0.02


Fig. C.98: HC 5 N, 42-41 (111.823024 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0

|Col1|Col2|
|---|---|
|||



12.0 0.0 -12.0

RA offset ( )


0.4


0.3


0.2


0.1


0.0


0.1


70 20 30
Velocity (km/s)



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.99: Si [13] CC, 5 0,5 -4 0,4 (112.593212 GHz)



Article number, page 80 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.8


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

RA offset ( )


0.8


0.6


0.4


0.2


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 10.0 20.0 30.0


8.0


0.0


-8.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


1.5


1.0


0.5


0.0


70 40 10
Velocity (km/s)



Fig. C.100: CN, N=1-0, J=1/2-1/2, F=1/2-3/2 (113.144157 GHz)



IRAS 15194-5115


mJy/beam
0.0 2.0 4.0 6.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.8


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0 10.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

RA offset ( )


1.0


0.5


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam


8.0


0.0


-8.0

|.0 20.0 mJy/be|40.0 eam|
|---|---|
|||
|||



8.0 0.0 -8.0

RA offset ( )


1.5


1.0


0.5


0.0

70 40 10
Velocity (km/s)



Fig. C.101: CN, N=1-0, J=1/2-1/2, F=3/2-1/2 (113.170492 GHz)



Article number, page 81 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 2.5 5.0 7.5


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


1.0


0.8


0.6


0.4


0.2


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0 10.0


10.0


0.0


-10.0

|Col1|Col2|Col3|
|---|---|---|
||||



10.0 0.0 -10.0

RA offset ( )


1.00


0.75


0.50


0.25


0.00


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 20.0 40.0


8.0


0.0


-8.0

|Col1|Col2|
|---|---|
|||



8.0 0.0 -8.0

RA offset ( )


1.5


1.0


0.5


0.0

70 40 10
Velocity (km/s)



Fig. C.102: CN, N=1-0, J=1/2-1/2, F=3/2-3/2 (113.191279 GHz)


IRAS 15194-5115


mJy/beam
0.0 2.5 5.0 7.5


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )

0.3


0.2


0.1


0.0


0.1



0.2



70 20 30
Velocity (km/s)


Fig. C.103: C [13] CCCH, N=12-11, J=23/2-21/2 (113.6442 GHz)



Article number, page 82 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS 15194-5115


mJy/beam
0.0 2.5 5.0 7.5


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


0.4


0.2


0.0


70 20 30
Velocity (km/s)


Fig. C.104: CC [13] CCH, N=12-11, J=23/2-21/2 (113.81808 GHz)



IRAS 15194-5115


mJy/beam
0.0 5.0 10.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


1.5


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0 10.0


10.0


0.0


-10.0

|Col1|Col2|
|---|---|
|||



10.0 0.0 -10.0

RA offset ( )


0.6


0.4


0.2


0.0



8.0


0.0


-8.0


0.10


0.05


0.00


0.05



IRAS 07454-7112


mJy/beam
0.0 5.0


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



0.2



40 0 40
Velocity (km/s)



Fig. C.105: C 4 H, N=12-11, J=25/2-23/2 (114.182514 GHz)



Article number, page 83 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS 15194-5115


mJy/beam
0.0 5.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


2.0


1.5


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 5.0 10.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


0.8


0.6


0.4


0.2


0.0



8.0


0.0


-8.0


0.10


0.05


0.00


0.05



IRAS 07454-7112


mJy/beam
0.0 2.5 5.0 7.5


8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



0.2



40 0 40
Velocity (km/s)



Fig. C.106: C 4 H, N=12-11, J=23/2-21/2 (114.221042 GHz)



IRAS 15194-5115


mJy/beam
0.0 5.0 10.0 15.0


12.0


0.0


-12.0


12.0 0.0 -12.0

RA offset ( )


1.5


1.0


0.5


0.0


70 20 30
Velocity (km/s)



IRAS 15082-4808


mJy/beam
0.0 10.0


10.0


0.0


-10.0


10.0 0.0 -10.0

RA offset ( )


1.0


0.5


0.0


40 0 40
Velocity (km/s)



IRAS 07454-7112


mJy/beam
0.0 10.0 20.0 30.0



8.0


0.0


-8.0


0.6


0.4


0.2


0.0



8.0 0.0 -8.0

RA offset ( )


70 40 10
Velocity (km/s)



Fig. C.107: SiC 2, 5 0,5 -4 0,4 (115.382389 GHz)



Article number, page 84 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



0.3


0.2


0.1


0.0


0.1



0.05


0.00


0.05


86.88 86.93
Frequency (GHz)





0.10



0.10


0.05


0.00



87.58 87.63
Frequency (GHz)



100.38 100.42
Frequency (GHz)



−
Fig. C.108: Spectra of unidentified lines towards IRAS 15194 5115. The width of the region shaded in pink is twice the expansion
velocity of the source CSE. The feature to the left of the 87.59 GHz line is a blend of the [30] SiS 5−4 and SiN 2−1 lines. The u-lines
are too weak to show any structure in the emission maps. They are not detected in the other two sources.



The below figures show the spectra of the lines from the
APEX surveys that we have used in this work, for IRAS
15194−5115 (left), IRAS 15082−4808 (centre), and IRAS
07454−7112 (right). The figures are ordered in increasing order of line rest frequency, which is given in parentheses at the
end of the figure caption. Missing plots indicate non-detection
of the concerned line towards the particular source. The dotted vertical line marks the systemic velocity of the source. The
grey-shaded regions cover 1.2 times the expansion velocity on
either side of the systemic velocity. For non-blended lines, this



region represents the channels used for calculating the integrated
line intensities, reported in Table B.2. For the lines of C 3 N
(Figs. C.113, C.147, C.158, C.165, C.183), where the line profile consists of blended hyperfine components, the whole line
profile, not just the grey shaded region, has been integrated to
obtain the integrated line intensity. For lines of C 2 H and C 4 H,
which have hyperfine components, we have shown only the
strongest/unblended component, but the total integrated intensity
was calculated by summing up all the components per transition.



IRAS_15194-5115



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.08


0.06


0.04


0.02


0.00


0.125


0.100


0.075


0.050


0.025


0.000


0.025



IRAS_15194-5115


50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



50 0
V LSR (km/s)



Fig. C.109: C 4 H, N=17-16 (161.796566 GHz)



IRAS_07454-7112


0.08


0.06


0.04


0.02


0.00


100 50 0
V LSR (km/s)



0.10


0.08


0.06


0.04


0.02


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.110: SiS, 9-8 (163.376785 GHz)



Article number, page 85 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_07454-7112

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



0.03


0.02


0.01


0.00


0.01


0.06


0.04


0.02


0.00


0.08


0.06


0.04


0.02


0.00


Article number, page 86 of 114



IRAS_15194-5115


50 0
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00


0.01



Fig. C.111: HC 3 N, J=18-17 (163.753389 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)



0.05


0.04


0.03


0.02


0.01


0.00


0.01



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00


0.01



Fig. C.112: SiC 2, 7( 2, 6)- 6( 2, 5) (164.069091 GHz)


IRAS_15082-4808


0.02


0.01


0.00


0.01

50 0 50
V LSR (km/s)


Fig. C.113: C 3 N, N=17-16 (168.2043 GHz).



IRAS_15194-5115


50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.114: C 4 H, N=18-17 (171.310707 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS_07454-7112


50 0
V LSR (km/s)


IRAS_07454-7112


50 0
V LSR (km/s)



0.03


0.02


0.01


0.00


0.01



IRAS_15194-5115


50 0
V LSR (km/s)



0.015


0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.015


0.010


0.005


0.000


0.005



Fig. C.115: [29] SiO, 4-3 (171.512796 GHz)



IRAS_15194-5115



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.6


0.4


0.2


0.0


0.015


0.010


0.005


0.000


0.005


0.010



IRAS_15194-5115


50 0
V LSR (km/s)



0.20


0.15


0.10


0.05


0.00



0.04


0.03


0.02


0.01


0.00


0.01



0.15


0.10


0.05


0.00



50 0
V LSR (km/s)



Fig. C.116: H [13] CN, J=2-1 (172.677851 GHz)



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.03


0.02


0.01


0.00


0.01



IRAS_07454-7112


50 0
V LSR (km/s)



Fig. C.117: HC 3 N, J=19-18 (172.8493 GHz)



IRAS_07454-7112


50 0
V LSR (km/s)


Article number, page 87 of 114



0.3


0.2


0.1


0.0



IRAS_15194-5115


50 0
V LSR (km/s)



0.15


0.10


0.05


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.10


0.08


0.06


0.04


0.02


0.00



Fig. C.118: SiO, 4-3 (173.688238 GHz)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.6


0.5


0.4


0.3


0.2


0.1


0.0



IRAS_15194-5115


50 0
V LSR (km/s)



0.25


0.20


0.15


0.10


0.05


0.00



0.08


0.06


0.04


0.02


0.00



IRAS_07454-7112

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



Fig. C.119: C 2 H, N=2-1 (174.663199 GHz)



IRAS_15194-5115



0.5 IRAS_07454-7112


0.4


0.3


0.2


0.1


0.0

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



IRAS_15082-4808


50 0 50
V LSR (km/s)



1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.10


0.05


0.00


0.15


0.10


0.05


0.00


0.05


Article number, page 88 of 114



1.0


0.8


0.6


0.4


0.2


0.0



50 0
V LSR (km/s)



Fig. C.120: HCN, J=2-1 (177.261111 GHz)


IRAS_15194-5115


50 0
V LSR (km/s)


Fig. C.121: C 4 H, N=19-18 (180.824472 GHz)


IRAS_15194-5115


50 0
V LSR (km/s)


=
Fig. C.122: HNC, J 2-1 (181.324758 GHz)

0.10


0.05


0.00


0.05


0.10


0.05


0.00


0.05


0.08


0.06


0.04


0.02


0.00



R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS_15194-5115


50 0
V LSR (km/s)


Fig. C.123: SiS, 10-9 (181.525218 GHz)


IRAS_15194-5115


50 0
V LSR (km/s)


Fig. C.124: [13] CS, J=4-3 (184.981772 GHz)


0.03 IRAS_15082-4808


0.02


0.01


0.00


0.01


50 0 50
V LSR (km/s)


Fig. C.125: SiC 2, 8( 6, 3)- 7( 6, 2) (188.3857 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



0.04 IRAS_15082-4808


0.03


0.02


0.01


0.00


0.01


50 0 50
V LSR (km/s)



Fig. C.126: C 4 H, N=20-19 (190.337804 GHz)



Article number, page 89 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_15082-4808



IRAS_07454-7112



0.02


0.01



0.03


0.02


0.01



0.00

0.00


0.01


0.01

50 0 50
V LSR (km/s)


Fig. C.127: HC 3 N, J=21-20 (191.040299 GHz)



50 0
V LSR (km/s)



0.06


0.04


0.02


0.00


0.02



IRAS_15194-5115


50 0
V LSR (km/s)



0.05


0.04


0.03


0.02


0.01


0.00


0.01



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.03


0.02


0.01


0.00



Fig. C.128: C [34] S, 4-3 (192.818457 GHz)



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.6


0.4


0.2


0.0


0.15


0.10


0.05


0.00


Article number, page 90 of 114



IRAS_15194-5115


50 0
V LSR (km/s)



0.5


0.4


0.3


0.2


0.1


0.0



Fig. C.129: CS, 4-3 (195.954211 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)


IRAS_07454-7112


50 0
V LSR (km/s)



0.125


0.100


0.075


0.050


0.025


0.000



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.10


0.08


0.06


0.04


0.02


0.00



Fig. C.130: SiS, 11-10 (199.672229 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



0.08


0.06


0.04


0.02


0.00


0.06


0.04


0.02


0.00

|Col1|Col2|
|---|---|
|||



0.06


0.04


0.02


0.00


0.02



IRAS_15194-5115


50 0
V LSR (km/s)


|Col1|Col2|
|---|---|
|||



IRAS_15194-5115


50 0
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00


0.01



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.131: C 4 H, N=21-20 (199.850787 GHz)



IRAS_07454-7112


0.015


0.010


0.005


0.000


100 50 0
V LSR (km/s)



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.132: HC 3 N, J=23-22 (209.230234 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_15082-4808



0.025


0.020


0.015


0.010


0.005


0.000


0.005



0.0075


0.0050


0.0025


0.0000


0.0025


50 0 50
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)



Fig. C.133: C 4 H, N=22-21 (209.363302 GHz)



IRAS_07454-7112


50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00



Fig. C.134: SiC 2, 9( 2, 8)- 8( 2, 7) (209.892001 GHz)



Article number, page 91 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



0.025 IRAS_15082-4808


0.020


0.015


0.010


0.005


0.000


50 0 50
V LSR (km/s)



IRAS_07454-7112


0.02


0.01


0.00


100 50 0
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00


0.01


0.04


0.03


0.02


0.01


0.00


0.01


0.04


0.03


0.02


0.01


0.00


0.01


Article number, page 92 of 114



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



Fig. C.135: SiC 2, 9( 6, 4)- 8( 6, 3) (212.031878 GHz)



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



0.025


0.020


0.015


0.010


0.005


0.000



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.136: SiC 2, 9( 4, 6)- 8( 4, 5) (213.208032 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


0.03


0.02


0.01


0.00


100 50 0
V LSR (km/s)



0.025


0.020


0.015


0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.137: SiC 2, 9( 4, 5)- 8( 4, 4) (213.292337 GHz)



IRAS_15082-4808



IRAS_07454-7112



0.006


0.004


0.002


0.000


0.002



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025


|Col1|Col2|
|---|---|
|||



50 0 50
V LSR (km/s)


Fig. C.138: [29] SiS, 12-11 (213.81614 GHz)



50 0
V LSR (km/s)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS_07454-7112


0.015


0.010


0.005


0.000


100 50 0
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00


0.01



IRAS_15194-5115


50 0
V LSR (km/s)



0.015


0.010


0.005


0.000



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.139: [29] SiO, 5-4 (214.385752 GHz)



IRAS_15194-5115



IRAS_15082-4808



0.4


0.3


0.2


0.1


0.0


0.125


0.100


0.075


0.050


0.025


0.000



IRAS_15194-5115


50 0
V LSR (km/s)



0.10


0.08


0.06


0.04


0.02


0.00



0.125


0.100


0.075


0.050


0.025


0.000



0.15


0.10


0.05


0.00



0.150


0.125


0.100


0.075


0.050


0.025


0.000



50 0
V LSR (km/s)



50 0 50
V LSR (km/s)


Fig. C.140: SiO, 5-4 (217.104919 GHz)



IRAS_15082-4808


50 0 50
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)


IRAS_07454-7112


50 0
V LSR (km/s)



Fig. C.141: SiS, 12-11 (217.817663 GHz)



IRAS_07454-7112


0.010


0.005


0.000


100 50 0
V LSR (km/s)



0.0125


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.142: HC 3 N, J=24-23 (218.324723 GHz)



Article number, page 93 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_15082-4808



50 0 50
V LSR (km/s)



IRAS_07454-7112



0.06


0.04


0.02


0.00


0.04


0.02


0.00


0.02


0.05


0.04


0.03


0.02


0.01


0.00


0.01


Article number, page 94 of 114



IRAS_15194-5115


50 0
V LSR (km/s)



0.025


0.020


0.015


0.010


0.005


0.000



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025



100 50 0
V LSR (km/s)



Fig. C.143: C 4 H, N=23-22 (218.875369 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


0.05


0.04


0.03


0.02


0.01


0.00


100 50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.144: SiC 2, 10( 0,10)- 9( 0, 9) (220.773685 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.05


0.04


0.03


0.02


0.01


0.00



IRAS_07454-7112


50 0
V LSR (km/s)



Fig. C.145: SiC 2, 9( 2, 7)- 8( 2, 6) (222.009386 GHz)



IRAS_07454-7112


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.008


0.006


0.004


0.002


0.000


0.002



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.146: HC 3 N, J=25-24 (227.418905 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


IRAS_07454-7112


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)


Fig. C.147: C 3 N, N=23-22 (227.5539 GHz)



IRAS_07454-7112


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025


100 50 0
V LSR (km/s)



0.06


0.04


0.02


0.00


0.15


0.10


0.05


0.00



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)


|Col1|Col2|
|---|---|
|||



Fig. C.149: Si [34] S, 13-12 (229.500868 GHz)


IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)


Fig. C.150: [13] CS, J=5-4 (231.220685 GHz)



0.025


0.020


0.015


0.010


0.005


0.000



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.148: C 4 H, N=24-23 (228.386962 GHz)



IRAS_07454-7112


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025


100 50 0
V LSR (km/s)



0.008


0.006


0.004


0.002


0.000


0.002



IRAS_15082-4808


50 0 50
V LSR (km/s)



Article number, page 95 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_07454-7112


0.010


0.005


0.000

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.006


0.004


0.002


0.000


0.002



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.151: [29] SiS, 13-12 (231.626673 GHz)



0.04 IRAS_15082-4808


0.03


0.02


0.01


0.00


50 0 50
V LSR (km/s)



100 50 0
V LSR (km/s)



IRAS_07454-7112



0.04


0.02


0.00


0.04


0.02


0.00


0.02


0.15


0.10


0.05


0.00


Article number, page 96 of 114



IRAS_15194-5115


50 0
V LSR (km/s)



0.06


0.05


0.04


0.03


0.02


0.01


0.00



Fig. C.152: SiC 2, 10( 2, 9)- 9( 2, 8) (232.53407 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


0.03


0.02


0.01


0.00


0.01


100 50 0
V LSR (km/s)



0.025


0.020


0.015


0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.153: SiC 2, 10( 6, 5)- 9( 6, 4) (235.712998 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)



0.10


0.08


0.06


0.04


0.02


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.150


0.125


0.100


0.075


0.050


0.025


0.000



Fig. C.154: SiS, 13-12 (235.961363 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS_15082-4808



IRAS_07454-7112



0.0100

0.008

0.0075

0.006

0.0050

0.004

0.0025

0.002

0.0000

0.000

0.0025

0.002

0.0050


50 0 50
V LSR (km/s)

|Col1|Col2|
|---|---|
|||



Fig. C.155: HC 3 N, J=26-27 (236.512789 GHz)



50 0
V LSR (km/s)



0.03


0.02


0.01


0.00


0.01


0.03


0.02


0.01


0.00


0.01



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)



0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.04


0.03


0.02


0.01


0.00


0.01



Fig. C.156: SiC 2, 10( 4, 7)- 9( 4, 6) (237.150018 GHz)



0.025 IRAS_15082-4808


0.020


0.015


0.010


0.005


0.000


50 0 50
V LSR (km/s)



IRAS_07454-7112


0.03


0.02


0.01


0.00


100 50 0
V LSR (km/s)



Fig. C.157: SiC 2, 10( 4, 6)- 9( 4, 5) (237.331309 GHz)


IRAS_07454-7112


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)


Fig. C.158: C 3 N, N=24-23 (237.44415 GHz)


Article number, page 97 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



0.05


0.04


0.03


0.02


0.01


0.00


0.01


0.04


0.02


0.00


0.02


0.04


0.03


0.02


0.01


0.00


0.01


Article number, page 98 of 114



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



IRAS_07454-7112


50 0
V LSR (km/s)



0.015


0.010


0.005


0.000



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.010


0.005


0.000


0.005



Fig. C.159: C 4 H, N=25-24 (237.89806 GHz)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


0.03


0.02


0.01


0.00


100 50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.160: C [34] S, 5-4 (241.016089 GHz)



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



IRAS_07454-7112


0.05


0.04


0.03


0.02


0.01


0.00


100 50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.161: SiC 2, 11( 0,11)-10( 0,10) (241.367708 GHz)



IRAS_07454-7112


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.162: C [33] S, 5-4 (242.91361 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



0.8


0.6


0.4


0.2


0.0



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



0.4


0.3


0.2


0.1


0.0



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.4


0.3


0.2


0.1


0.0



IRAS_07454-7112


50 0
V LSR (km/s)


IRAS_07454-7112



Fig. C.163: CS, 5-4 (244.935556 GHz)


IRAS_15082-4808



0.0075


0.0050


0.0025


0.0000


0.0025



0.010


0.005


0.000


|Col1|Col2|
|---|---|
|||


|Col1|Col2|
|---|---|
|||



50 0 50
V LSR (km/s)



100 50 0
V LSR (km/s)



Fig. C.164: Si [34] S, 14-13 (247.146242 GHz)


IRAS_07454-7112


0.0125


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025

|Col1|Col2|
|---|---|
|||


100 50 0
V LSR (km/s)


Fig. C.165: C 3 N, N=25-24 (247.334 GHz)



IRAS_07454-7112

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.015


0.010


0.005


0.000



IRAS_15082-4808

|Col1|Col2|
|---|---|
|||



50 0 50
V LSR (km/s)



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025



Fig. C.166: C 4 H, N=26-25 (247.408643 GHz)



Article number, page 99 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_07454-7112


50 0
V LSR (km/s)



0.04


0.02


0.00


0.02


0.20


0.15


0.10


0.05


0.00


0.03


0.02


0.01


0.00


0.01


Article number, page 100 of 114



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.06


0.04


0.02


0.00



Fig. C.167: SiC 2, 10( 2, 8)- 9( 2, 7) (247.52912 GHz)



IRAS_15082-4808



IRAS_07454-7112



0.008


0.006


0.004


0.002


0.000


0.002



0.010


0.005


0.000



0.004


50 0 50
V LSR (km/s)

|Col1|Col2|
|---|---|
|||



Fig. C.168: [29] SiS, 14-13 (249.435412 GHz)



50 0
V LSR (km/s)



IRAS_15194-5115


50 0
V LSR (km/s)



IRAS_07454-7112


0.20


0.15


0.10


0.05


0.00


100 50 0
V LSR (km/s)



0.10


0.08


0.06


0.04


0.02


0.00



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.169: SiS, 14-13 (254.103211 GHz)



IRAS_15194-5115

|Col1|Col2|Col3|
|---|---|---|
||||
||||



50 0
V LSR (km/s)



IRAS_07454-7112


0.010


0.005


0.000


100 50 0
V LSR (km/s)



0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.170: [30] SiO, 6-5 (254.216656 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



IRAS_07454-7112


0.010


0.005


0.000


0.005

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.015


0.010


0.005


0.000



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.171: C 4 H, N=27-26 (256.918691 GHz)



IRAS_07454-7112


0.015


0.010


0.005


0.000


100 50 0
V LSR (km/s)



0.04


0.02


0.00


0.02



|5194-5115|Col2|
|---|---|
|||
|||
|||


50 0
V LSR (km/s)



0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.172: [29] SiO, 6-5 (257.255213 GHz)



1.0


0.8


0.6


0.4


0.2


0.0



IRAS_15194-5115


50 0
V LSR (km/s)



0.20


0.15


0.10


0.05


0.00



IRAS_07454-7112


100 50 0
V LSR (km/s)



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.3


0.2


0.1


0.0



Fig. C.173: H [13] CN, J=3-2 (259.011798 GHz)



IRAS_07454-7112


0.03


0.02


0.01


0.00

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.020


0.015


0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



Fig. C.174: SiC 2, 11( 6, 6)-10( 6, 5) (259.433309 GHz)



Article number, page 101 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



IRAS_15194-5115



IRAS_07454-7112


0.15


0.10


0.05


0.00


100 50 0
V LSR (km/s)



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.3


0.2


0.1


0.0


0.03


0.02


0.01


0.00


0.01


0.04


0.02


0.00


0.02


|5194-5115|Col2|
|---|---|
|||
|||



|5194-5115|Col2|
|---|---|
|||
|||


50 0
V LSR (km/s)



0.15


0.10


0.05


0.00



50 0
V LSR (km/s)



Fig. C.175: SiO, 6-5 (260.518009 GHz)



50 0
V LSR (km/s)



0.020


0.015


0.010


0.005


0.000


0.005



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.03


0.02


0.01


0.00



IRAS_07454-7112


50 0
V LSR (km/s)



Fig. C.176: SiC 2, 11( 4, 8)-10( 4, 7) (261.150695 GHz)



0.020 IRAS_15082-4808


0.015


0.010


0.005


0.000


0.005

50 0 50
V LSR (km/s)



IRAS_07454-7112


0.03


0.02


0.01


0.00


100 50 0
V LSR (km/s)



Fig. C.177: SiC 2, 11( 4, 7)-10( 4, 6) (261.509329 GHz)



0.150 IRAS_07454-7112


0.125


0.100


0.075


0.050


0.025


0.000


100 50 0
V LSR (km/s)



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.3


0.2


0.1


0.0


Article number, page 102 of 114



IRAS_15194-5115


50 0
V LSR (km/s)



0.25


0.20


0.15


0.10


0.05


0.00



Fig. C.178: C 2 H, N=3-2 (262.064986 GHz)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



0.006


0.004


0.002


0.000


0.002



IRAS_15082-4808

|Col1|Col2|
|---|---|
|||



50 0 50
V LSR (km/s)



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025



IRAS_07454-7112

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



Fig. C.179: [30] SiS, 15-14 (262.585033 GHz)


IRAS_07454-7112


0.010


0.005


0.000


0.005

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)


Fig. C.180: Si [34] S, 15-14 (264.789719 GHz)



2.0


1.5


1.0


0.5


0.0



IRAS_15194-5115

|Col1|Col2|
|---|---|
|||



50 0
V LSR (km/s)



1.0


0.8


0.6


0.4


0.2


0.0



IRAS_07454-7112


100 50 0
V LSR (km/s)



IRAS_15082-4808


50 0 50
V LSR (km/s)



0.8


0.6


0.4


0.2


0.0



=
Fig. C.181: HCN, J 3-2 (265.886434 GHz)



IRAS_07454-7112

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)



0.010


0.005


0.000



IRAS_15082-4808

|Col1|Col2|Col3|
|---|---|---|
||||
||||



50 0 50
V LSR (km/s)



0.010


0.005


0.000


0.005



Fig. C.182: C 4 H, N=28-27 (266.428184 GHz)



Article number, page 103 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


IRAS_07454-7112


0.010


0.005


0.000


0.005

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)


Fig. C.183: C 3 N, N=27-26 (267.11225 GHz)


0.05 IRAS_07454-7112


0.04


0.03


0.02


0.01


0.00

|Col1|Col2|
|---|---|
|||



100 50 0
V LSR (km/s)


Fig. C.184: [29] SiS, 15-14 (267.242218 GHz)



Article number, page 104 of 114



_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


**Appendix D:** **Azimuthally-averaged radial profiles (AARPs)**


The figures below show the Gaussian fits to the azimuthally-averaged radial profiles (AARPs) of the systemic velocity emission
maps of the 14 species shown in Fig. 9. The details of these profiles and fits are explained in Sect. 4.3.2.



1.0


0.8


0.6


0.4


0.2


0.0



|IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112<br>SiS|Col2|
|---|---|
|**SiS**<br>IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112||


0.0 0.5 1.0 1.5
Radial distance (cm) 1e17







1.0


0.8


0.6


0.4


0.2


0.0



0.0 0.5 1.0 1.5
Radial distance (cm) 1e17



Fig. D.1: AARPs (solid) and Gaussian fits (dashed) for SiO (left) and SiS (right) emission.



1.0


0.8


0.6


0.4


0.2


0.0


1.0


0.8


0.6


0.4


0.2


0.0



|Col1|IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112<br>SiC2|
|---|---|
|00<br>0<br>10<br>~~1~~|00<br>0<br>10<br>~~1~~|


Radial distance (cm) 1e17



1.0


0.8


0.6


0.4


0.2


0.0



0.0 0.5 1.0 1.5
Radial distance (cm) 1e17







Fig. D.2: Same as Fig. D.1 for SiC 2 (left) and CS (right) emission.









1.0


0.8


0.6


0.4


0.2


0.0



0.0 0.5 1.0 1.5
Radial distance (cm) 1e17


|Col1|IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112<br>CN<br>05 10 15<br>. . .<br>Radialdistance(cm) 1e17|
|---|---|
||**CN**<br>IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112|
|0.0<br>|0.0<br>|



Fig. D.3: Same as Fig. D.1 for HCN (left) and CN (right) emission.



Article number, page 106 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



1.0


0.8


0.6


0.4


0.2


0.0


1.0


0.8


0.6







0.0 0.5 1.0 ~~1~~ .5
Radial distance (cm) 1e17



0.4


0.2


0.0

|Col1|IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112<br>C4H|
|---|---|
||**C4H**<br>IRAS 07454-7112|
|0.0<br>0.5<br>1.0<br>~~1~~.5<br>Radial distance (cm)<br>1e17|0.0<br>0.5<br>1.0<br>~~1~~.5<br>Radial distance (cm)<br>1e17|



Fig. D.4: Same as Fig. D.1 for C 2 H (top left), C 3 H (top right), C 4 H (bottom left), and c-C 3 H 2 (bottom right) emission



1.0


0.8


0.6


0.4


0.2


0.0


1.0


0.8


0.6


0.4


0.2


0.0



0.0 0.5 1.0 1.5
Radial distance (cm) 1e17











1.0


0.8


0.6


0.4


0.2


0.0


1.0


0.8


0.6


0.4


0.2


0.0



0.0 0.5 1.0 1.5
Radial distance (cm) 1e17



0.0 0.5 1.0 1.5
Radial distance (cm) 1e17






|Col1|IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112<br>HC5N|Col3|
|---|---|---|
||**HC5N**<br>IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112|**HC5N**<br>IRAS 15194-5115<br>IRAS 15082-4808<br>IRAS 07454-7112|
|0.0<br>0<br>R|.5<br>~~1~~.~~0~~<br>1.5<br>adial dist~~a~~nce (c~~m~~)<br>1e17||



Fig. D.5: Same as Fig. D.1 for HC 3 N (top left), C 3 N (top right), HC 5 N (bottom left), and HNC (bottom right) emission


Article number, page 107 of 114

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


**Appendix E:** **Column densities and abundances: methods**



The results in this section are based on a simple model for the
CSE, assuming an isotropic, constant mass-loss rate and the gas
expanding at its terminal velocity. Nevertheless, there are clear
indications of deviations from such a simple model, particularly
in terms of the morphology, as discussed in Sect. 4.3.1.
We express molecular abundances as fractional abundances
relative to that of molecular hydrogen, H 2, which has the abundance distribution with the largest spatial extent (Huggins &
Glassgold 1982). The fractional abundance profile of a molecular species X is defined as


_f_ X ( _r_ ) = _[n]_ [X] [(] _[r]_ [)] (E.1)

_n_ H 2 ( _r_ ) [,]


where _n_ X ( _r_ ) and _n_ H 2 ( _r_ ) are the number density distributions of
the molecule and molecular hydrogen, respectively.
The excitation of a molecule in the CSE is determined by collisions and radiation, in particular the radiation fields of the central star and circumstellar dust. Non-local thermodynamic equilibrium (non-LTE) conditions can be prevalent in CSEs, which
calls for a detailed radiative transfer analysis for the proper treatment of molecular excitation. Such a non-LTE treatment is outside the scope of the current work, and shall be presented in an
upcoming paper. A simpler analysis assuming LTE conditions
can provide reasonable estimates of the molecular abundances
and offer substantial insights into circumstellar chemistry, and
is regularly employed as a first tool to analyse spectral surveys
and other large datasets of evolved stars (e.g. Cernicharo et al.
2000; Justtanont et al. 2000; Wesson et al. 2010; Patel et al. 2011;
Sánchez Contreras et al. 2015; Smith et al. 2015; Velilla Prieto
et al. 2015b; Pardo et al. 2022).
For molecules with multiple rotational transitions detected,
the rotational temperature and column density can be estimated
using a population diagram (Sect. E.1). The column densities
thus obtained, together with the emission region sizes calculated from the AARPs, can be used to estimate molecular fractional abundances. In those cases where the population-diagram
method can not be employed, owing to the lack of sufficient
number of transitions covering a broad range of upper-level energies, we perform an approximate calculation of the fractional
abundance using a single line for each species (Sect. E.3). We
describe both methods below.


_Appendix E.1:_ _The population diagram method_


The column density of each rotational energy level is related
to the rotational temperature, _T_ rot, and total column density, _N_ tot,
by the relation


_N_ tot _E_ u

ln _[N]_ [u] = ln (E.2)

_g_ u _Z_ ( _T_ rot ) [−] _k_ B _T_ rot


where _N_ u is the column density of molecules in the upper energy
level having energy _E_ u and statistical weight _g_ u, and _Z_ and _k_ B are
the partition function and the Boltzmann constant, respectively
(Goldsmith & Langer 1999).
For the calculation of partition functions, all molecules used
for producing population diagrams (see Table 6) have been regarded as linear rigid rotors, except SiC 2 and c-C 3 H 2, which
are asymmetric tops. In order to use the integrated intensities
summed over the hyperfine components wherever present (e.g.


Article number, page 108 of 114



C 2 H, C 3 N), we have calculated the partition functions, degeneracy factors, and the Einstein _A_ -coefficients under the assumption that the molecules do not possess hyperfine structure. For
the asymmetric tops, we interpolated the partition function values from the CDMS (Müller et al. 2005) catalogue to the rotation
temperatures obtained from our analysis.
The source-averaged column density of the upper state, _N_ u,
can be calculated from the observed velocity-integrated flux,
� _S_ ul _d_ �, of the corresponding rotational emission line as


4π � _S_ ul _d_ �
_N_ u = _hcA_ ul Ω _s_ _C_ τ ν (E.3)


where ν ul is the rest frequency of the transition, _A_ ul is the Einstein _A_ -coefficient, Ω _s_ is the solid angle of the emitting region, _h_
is the Planck constant, _c_ is the speed of light in vacuum, and C τ ν
is the optical depth correction factor (see Goldsmith & Langer
1999), given by



τ ν
_C_ τ ν = � 1 − _e_ [−][τ] [ν]



(E.4)
�



where τ ν is the optical depth of the line.
If the assumptions that the populations of the corresponding energy levels follow a Boltzmann distribution which can
be described by a single excitation temperature, _T_ rot, and that
the lines are optically thin are correct, the points in the plot of
ln( _N_ u / _g_ u ) versus _E_ u / _k_ B are expected to lie on a straight line (see
e.g. Fig. E.18). The rotational temperature and column density
of each molecule are calculated from the slope and intercept, respectively, of a linear fit to such a plot.
Using this method, we first obtained estimates of the rotational temperature and total column density for each species
without an optical depth correction (C τ ν = 1). From these values,
we then calculated a preliminary estimate of the optical depth for
each individual line of the species, using the standard equation


_N_ _tot_

τ ν = _[c]_ [3] _[g]_ _[u]_ _[A]_ _[ul]_ [−] [1)] (E.5)

8πν [3] ∆� _Z_ ( _T_ ) _[e]_ [−] _[E]_ _[u]_ [/] _[k]_ [B] _[T]_ [(] _[e]_ _[h]_ [ν/] _[k]_ [B] _[T]_


where ∆� is the full velocity width of the line. The range of optical depths thus calculated for each species for the three stars are
given in Table E.1.
Employing the correction factors (see Eq. E.4) obtained
from the calculated optical depths, we then produced opticaldepth-corrected population diagrams, from which optical-depthcorrected rotation temperatures and total column densities were
estimated. These values are presented in Table 6. The opticaldepth-corrected population diagrams are shown in Figs. E.1 E.18.
We note that along with the lines from the ALMA data,
we have also included lines detected in our APEX surveys (Table B.2 and Figs. C.109−C.185) in the population diagrams, so
that a wider range of energy levels can be sampled.


_Appendix E.2:_ _Abundance calculation from column densities_


Using the estimates of the radial extents of the emitting regions of different species obtained from the Gaussian fits to the
AARPs (see Sect. 4.3.2), we can estimate the molecular fractional abundances (Table 7) from the column densities of the

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs


Table E.1: Range of optical depths per molecule


Molecule IRAS


15194−5115 15082−4808 07454−7112


HCN 3.33 - 9.95 12.33 - 21.68 11.55 - 22.44
H [13] CN 2.34 - 8.26 2.94 - 5.18 6.28 - 11.64


CS 1.16 - 5.85 4.98 - 7.92 3.49 - 4.09
13 CS 0.56 - 1.08 – –
C [34] S 0.01 - 0.27 0.28 - 0.43 0.20 - 0.35


SiO 0.80 - 4.29 1.98 - 4.23 3.10 - 5.65
29 SiO 0.07 - 0.47 0.17 - 0.30 0.25 - 0.49
30 SiO 0.04 - 0.06 – –


C 2 H 0.51 - 1.21 0.33 - 0.88 0.05 - 0.32
C 4 H 0.01 - 0.05 0.01 - 0.03 ∼0.01


SiS 0.09 - 0.58 0.49 - 0.87 1.03 - 2.42
29 SiS – 0.03 - 0.07 0.04 - 0.12
30 SiS – – 0.03 - 0.09
Si [34] S – 0.02 - 0.03 0.02 - 0.08


HNC 0.05 - 0.39 – –


HC 3 N 0.02 - 0.18 0.01 - 0.28 0.02 - 0.54
C 3 N 0.05 - 0.1 0.03 - 0.05 0.01 - 0.04
HC 5 N ∼0.01 0.01 - 0.04 0.01 - 0.05


SiC 2 0.01 - 0.04 0.01 - 0.03 0.01 - 0.04


**Notes.** For each molecule per star, the table lists the optical depth values of the lines with the highest and lowest calculated optical depth.



respective species given by the population diagrams, using the
equation



assumed excitation temperature throughout the emitting region,
we use the following formula from Habing & Olofsson (2004, in
rewritten form)


� exp _DZ_ ( _T_ ex )
_f_ X = 1.3 × 10 [−][19] _S_ ul _d_ � (E.7)

_g_ u _A_ ul _M_ [˙] ( _R_ e − _R_ i ) _[e]_ _[E]_ [l] [/] _[k]_ [B] _[T]_ [ex] �


where � exp is given in km/s, _M_ [˙] in _M_ ⊙ yr [−][1], _D_ in kpc, _R_ i and
_R_ e in cm, and � _S_ ul _d_ � in Jy km/s. The assumed _T_ ex values are
40 K for centrally-peaked species and 20 K for shell species (see
Sect. 4.4 for a justification of these values). We note that we have
not performed optical depth corrections in the case of single-line
abundance estimates, as the temperature we use for these calculations is an assumed value, and since the high uncertainties
involved anyway deem the abundances thus calculated to be order of magnitude estimates.
The figures below show the population diagrams (see
Sect. E.1) of various molecular species (listed in Table 6) towards the three stars.


Article number, page 109 of 114



_f_ X = [2][π] _[m]_ [H] [�] [exp] ˙ _[N]_ [tot][,][X]

_M_



_R_ [2] e
� _R_ e − _R_ i



(E.6)
�



where _M_ [˙] is the hydrogen mass-loss rate, � exp the gas expansion
velocity, _m_ H the mass of the hydrogen atom, and _R_ i and _R_ e the inner and outer radii of the emitting region, respectively (Olofsson
2003).


_Appendix E.3:_ _Abundance calculation from single lines_


Population diagrams cannot be used in the case of molecules
for which only one or two lines are detected, or for which the
detected transitions are very close together in upper-level energies. In such cases, we obtain a rough estimate of the fractional
abundance, using the highest signal-to-noise line available, by
assuming it to be constant in the radial range _R_ i to _R_ e and zero
outside it. Assuming an _r_ [−][2] density distribution and a constant,

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



34


33


32


31


30


29



20 40 60
E u /k B (K)





33.5


33.0


32.5


32.0


31.5


31.0


30.5



33.5


33.0


32.5


32.0


31.5



10 20 30 40
E u /k B (K)





10 20 30 40
E u /k B (K)





− − −
Fig. E.1: Population diagrams for SiO for IRAS 15194 5115 (left), IRAS 15082 4808 (middle), and IRAS 07454 7112 (bottom).
The solid line (red) is the best-fit linear model to the data (black). Rotation temperatures _T_ rot and source-averaged column densities
_N_ tot are listed in the legends. Circle and square points denote lines observed with ALMA and APEX, respectively. Hollow circles
denote lines for which data combination (see Sect. 3.3) has been performed


.


31





30.0


29.5


29.0


28.5


28.0


27.5







30.0


29.5


29.0


28.5


28.0



10 20 30 40
E u /k B (K)





30


29


28


27


26


27.50


27.25


27.00


26.75


26.50


26.25







20 40 60
E u /k B (K)





10 20 30 40
E u /k B (K)


Fig. E.2: Same as Fig. E.1 for [29] SiO.


Fig. E.3: Same as Fig. E.1 for [30] SiO.



45 50 55 60 65 70
E u /k B (K)


Article number, page 110 of 114

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs



25 50 75 100 125 150
E u /k B (K)


Article number, page 111 of 114





20 40 60 80
E u /k B (K)



Fig. E.4: Same as Fig. E.1 for SiS.


Fig. E.5: Same as Fig. E.1 for [29] SiS.





20 40 60 80 100
E u /k B (K)



29.0


28.5


28.0


27.5


27.0







20 40 60 80
E u /k B (K)


Fig. E.6: Same as Fig. E.1 for Si [34] S.



29


28


27


26


25


24


23





29


28


27


26


25



33.6


33.4


33.2


33.0


32.8


32.6


32.4


30.2


30.0


29.8


29.6


29.4


29.2


29.0


28.8


29.5


29.0


28.5


28.0


27.5


27.0


26.5


26.0











20 40 60 80 100 120
E u /k B (K)



25 50 75 100 125 150
E u /k B (K)


Fig. E.7: Same as Fig. E.1 for SiC 2 .

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars



36.0


35.5


35.0


34.5


34.0


33.5


33.0







35


34


33


32


31


30


32.5


32.0


31.5


31.0


30.5


30.0


29.5


31


30


29


28







10 20 30 40 50 60
E u /k B (K)





10 15 20 25 30 35
E u /k B (K)


Fig. E.8: Same as Fig. E.1 for CS.


Fig. E.9: Same as Fig. E.1 for [13] CS.



10 20 30 40
E u /k B (K)





31.0


30.5


30.0


29.5


29.0



5 10 15 20 25
E u /k B (K)









10 20 30 40 50 60
E u /k B (K)


Article number, page 112 of 114



10 15 20 25 30 35
E u /k B (K)


Fig. E.10: Same as Fig. E.1 for C [34] S.


Fig. E.11: Same as Fig. E.1 for HCN.



30.5


30.0


29.5


29.0


36.0


35.5


35.0


34.5


34.0



10 15 20 25 30 35
E u /k B (K)

R. Unnikrishnan et al.: ALMA 3 mm spectral surveys of C-rich AGB CSEs





35


34


33


32


31


30



10 20 30 40
E u /k B (K)





34.0


33.5


33.0


32.5


32.0


31.5


31.0





25 50 75 100 125 150 175
E u /k B (K)


Article number, page 113 of 114





5 10 15 20 25
E u /k B (K)


Fig. E.12: Same as Fig. E.1 for H [13] CN.


Fig. E.13: Same as Fig. E.1 for HNC.


Fig. E.14: Same as Fig. E.1 for HC 3 N.


Fig. E.15: Same as Fig. E.1 for C 3 N.



35.0


34.5


34.0


33.5


33.0


32.5


29


28


27


26


25


24


27


26


25


24



5 10 15 20 25
E u /k B (K)







25 50 75 100 125 150
E u /k B (K)

_A&A proofs:_ manuscript no. Charting_Circumstellar_Chemistry_of_Carbon-rich_AGB_Stars


25.5


25.0


24.5


24.0





70 80 90 100 110
E u /k B (K)



50 100 150
E u /k B (K)



Fig. E.16: Same as Fig. E.1 for HC 5 N.


Fig. E.17: Same as Fig. E.1 for C 2 H.



29


28


27


26


25





28


27


26


25


24



23.5


27.5


27.0


26.5


26.0


25.5


25.0


24.5











25 50 75 100 125 150
E u /k B (K)


Article number, page 114 of 114



50 100 150
E u /k B (K)


Fig. E.18: Same as Fig. E.1 for C 4 H.


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "12C/13C ratio, systemic velocity, expansion velocity, and isotopic ratios for IRC +10 216.",
  "failed_quote": "( f ) The listed 12 C/ 13 C ratio,  sys, and  exp for IRC +10 216 are from Cernicharo et al. (2000)"
 },
 {
  "path": "processing.imaging.deconvolver.evidence[1]",
  "value": "Multi-Scale (spectral lines); multi-frequency synthesis (continuum)",
  "failed_quote": "Continuum maps were produced from the line-free channels across the survey bandwidth (85-116 GHz) using multi-frequency synthesis (Rau & Cornwell 2011)."
 },
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "first-order polynomial fit to line-free channels subtracted from calibrated visibilities",
  "failed_quote": "The continuum was estimated using a first order polynomial fit to the line-free channels, and subtracted from the calibrated visibilities."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Population diagram formalism and optical depth correction factor.",
  "failed_quote": "where Z and k B are the partition function and the Boltzmann constant, respectively (Goldsmith & Langer 1999)."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Image continuum from line-free channels across 85-116 GHz using multi-frequency synthesis, subtract continuum from visibilities, extract spectra from 12.5'' radius circular apertures centred on continuum peaks (and molecule-specific apertures of radius R_p + 2.5*HWHM), and identify lines using spectroscopic catalogues.",
  "failed_quote": "Continuum maps were produced from the line-free channels across the survey bandwidth (85-116 GHz) using multi-frequency synthesis (Rau & Cornwell 2011)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Convolve non-blended line cubes to a common circular beam, average channels within ±20% of v_exp around v_sys, compute azimuthally-averaged radial profiles in concentric rings of width equal to the common beam, average line profiles weighted by inverse squared uncertainty, and fit Gaussians to derive beam-deconvolved inner and outer radii.",
  "failed_quote": "For each of these common-beam cubes, the emission from within a range of ±20% of the expansion velocity centred on the systemic velocity was averaged together to increase the signal-to-noise ratio"
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Convolve non-blended line cubes to a common circular beam, average channels within ±20% of v_exp around v_sys, compute azimuthally-averaged radial profiles in concentric rings of width equal to the common beam, average line profiles weighted by inverse squared uncertainty, and fit Gaussians to derive beam-deconvolved inner and outer radii.",
  "failed_quote": "The resulting maps were divided into successive concentric circular rings of increasing radii, centred on the continuum peak, with widths equal to the common restoring beam."
 },
 {
  "path": "analysis_steps[5].validation.evidence[0]",
  "value": "Normalised abundances to each star's C34S abundance to eliminate distance and mass-loss rate uncertainties, and compared against IRC +10 216 and solar isotopic ratios.",
  "failed_quote": "We also show the abundances normalised with those of IRC +10 216, for an easier source-to-source comparison, and normalised to each star’s C [34] S abundance, to eliminate source-specific uncertainties on distance and MLR."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Spectroscopic catalogue for line identification and partition function interpolation.",
  "failed_quote": "The Cologne Database for Molecular Spectroscopy (CDMS [6] ; Müller et al. 2005) catalogue was referred to for line identification."
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Interface to obtain spectral line parameters.",
  "failed_quote": "Splatalogue [7] (Remijan et al. 2007) was also used as an interface to obtain spectral line parameters."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[1]",
  "value": "Population diagrams for centrally-peaked species (except SiS) yield unrealistically low rotational temperatures (10-20 K) due to limited upper-energy coverage, radially varying excitation conditions, and high optical depths, making their derived abundances lower limits.",
  "failed_quote": "However, the estimated rotational temperatures are much lower than expected for these centrally-peaked species (see Table 6 and Fig. 12, left panel), and we therefore believe that for these species the reported abundances are lower limits."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Raw ALMA data are in the ALMA Science Archive (2013.1.00070.S, 2015.1.01271.S); reprocessed ALMA cubes, line spectra, and Tables B.1 and B.2 are publicly available at CDS.",
  "failed_quote": "Tables B.1 and B.2 are available in electronic form at the CDS, along with the reprocessed ALMA cubes and line spectra, via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/."
 }
]
```
