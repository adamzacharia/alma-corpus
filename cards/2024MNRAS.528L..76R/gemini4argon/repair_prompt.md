# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.528L..76R\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–7 (2015) Preprint 7 November 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **A fundamental plane of black hole accretion at millimetre wavelengths**


Ilaria Ruffa, [1] _[,]_ [2] _[★]_ Timothy A. Davis, [1] Jacob S. Elford, [1] - Martin Bureau, [3] Michele Cappellari, [3] Jindra Gensior, [4]

Daryl Haggard, [5] Satoru Iguchi, [6] _[,]_ [7] Federico Lelli, [8] Fu-Heng Liang, [3] Lĳie Liu, [9] _[,]_ [10] Marc Sarzi, [11]

Thomas G. Williams, [3] and Hengyue Zhang [3]

1 _Cardiff Hub for Astrophysics Research & Technology, School of Physics & Astronomy, Cardiff University, Queens Buildings, The Parade, Cardiff, CF24 3AA, UK_
2 _INAF - Istituto di Radioastronomia, via P. Gobetti 101, 40129 Bologna, Italy_
3 _Sub-department of Astrophysics, Department of Physics, University of Oxford, Keble Road, Oxford, OX1 3RH, UK_
4 _Institute for Computational Science, University of Zurich, Winterthurerstrasse 190, Zürich, 8057, Switzerland_
5 _Trottier Space Institute and Department of Physics, McGill University, 3600 rue University, Montreal, QC H3A 2T8, Canada_
6 _Department of Astronomical Science, SOKENDAI (The Graduate University of Advanced Studies), Mitaka, Tokyo 181-8588, Japan_
7 _National Astronomical Observatory of Japan, National Institutes of Natural Sciences, Mitaka, Tokyo 181-8588, Japan_
8 _INAF, Arcetri Astrophysical Observatory, Largo Enrico Fermi 5, I-50125, Florence, Italy_
9 _Cosmic Dawn Center (DAWN), Technical University of Denmark, DK2800 Kgs. Lyngby, Denmark_
10 _DTU-Space, Technical University of Denmark, Elektrovej 327, DK2800 Kgs. Lyngby, Denmark_
11 _Armagh Observatory and Planetarium, College Hill, Armagh BT61 9DG, UK_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

We report the discovery of the “mm fundamental plane of black-hole accretion”, which is a tight correlation between the nuclear
1 mm luminosity ( _𝐿_ _𝜈,_ mm ), the intrinsic 2 – 10 keV X-ray luminosity ( _𝐿_ X _,_ 2−10 ) and the supermassive black hole (SMBH) mass
( _𝑀_ BH ) with an intrinsic scatter ( _𝜎_ int ) of 0 _._ 40 dex. The plane is found for a sample of 48 nearby galaxies, most of which are
low-luminosity active galactic nuclei (LLAGN). Combining these sources with a sample of high-luminosity (quasar-like) nearby
AGN, we show that the plane still holds. We also find that _𝑀_ BH correlates with _𝐿_ _𝜈,_ mm at a highly significant level, although such
correlation is less tight than the mm fundamental plane ( _𝜎_ int = 0 _._ 51 dex). Crucially, we show that spectral energy distribution
(SED) models for both advection-dominated accretion flows (ADAFs) and compact jets can explain the existence of these
relations, which are not reproduced by the standard torus-thin accretion disc models usually associated to quasar-like AGN.
The ADAF models reproduces the observed relations somewhat better than those for compact jets, although neither provides a
perfect fit. Our findings thus suggest that radiatively-inefficient accretion processes such as those in ADAFs or compact (and
thus possibly young) jets may play a key role in both low- and high-luminosity AGN. This mm fundamental plane also offers a
new, rapid method to (indirectly) estimate SMBH masses.


**Key words:** galaxies: active – galaxies: nuclei – black hole physics – X-rays: galaxies – submillimetre: galaxies



**1** **INTRODUCTION**


The many details of the processes regulating the connection between the growth of central super-massive black holes (SMBHs)
and the evolution of their host galaxies (so-called "co-evolution”;
e.g. Kormendy & Ho 2013) are still poorly understood (e.g.
D’Onofrio et al. 2021). Understanding the physics of accretion onto
SMBHs, determining if and how it changes in objects with different
types of nuclear activity, as well as setting accurate constraints on
fundamental SMBH properties such as its mass, are all crucial steps
to get a comprehensive view of the SMBH-host galaxy interplay.
The so-called “fundamental plane of BH accretion” (heareafter FP)
is an empirical correlation between the SMBH masses ( _𝑀_ BH ), 5 GHz
radio ( _𝐿_ 5GHz ) and 2 - 10 keV X-ray ( _𝐿_ X _,_ 2−10 ) luminosities, which
was initially reported by Merloni et al. (2003) and Falcke et al. (2004).


_★_ E-mail: ruffai@cardiff.ac.uk

- First-authorship is shared between Ruffa, Davis & Elford


© 2015 The Authors



The origin of the FP is still debated, but it is widely believed to carry
information on the physics of SMBH accretion (see e.g. Gültekin
et al. 2019a). However, the scatter around this correlation varies
significantly depending on the sample and the method used to fit
the plane, reaching values up to 0 _._ 88 dex (e.g. Merloni et al. 2003;
Gültekin et al. 2009; Plotkin et al. 2012; Saikia et al. 2015; Gültekin
et al. 2019a, and references therein). Furthermore, the nature of
the radio emission in the FP is not yet well understood (potentially
arising from compact jets or complex shock dynamics). All the above
somehow limit the diagnostic power of the FP.


In this Letter, we report the discovery of a FP at millimetre wavelengths, namely the existence of a tight correlation between the nuclear (i.e. ≪ 100 pc) mm luminosities ( _𝐿_ _𝜈,_ mm ), _𝑀_ BH and intrinsic
_𝐿_ X _,_ 2−10, which we find to hold for both high- and low-luminosity
AGN (within _𝑧_ ≲ 0 _._ 05). We also present the analysis of the physics
underlying such correlation, and discuss how our results may have
profound implications for our understanding of BH accretion in different AGN types.

2 _I. Ruffa et al._


**2** **PRIMARY SAMPLE AND DATA**


Our sample was primarily drawn from the mm-Wave Interferometric
Survey of Dark Object Masses (WISDOM) project, which mainly
exploits high-resolution Atacama Large Millimeter/submillimeter
Array (ALMA) CO observations to dynamically estimate SMBH
masses in a varied sample of galaxies (e.g. Davis et al. 2017). We
included 31 WISDOM galaxies (see Table A1) at _𝑧_ ≲ 0 _._ 03, spanning
a range of AGN bolometric luminosities ( _𝐿_ bol = 10 [41] – 10 [46] erg s [−][1] )
andontomostlytheir central(but notSMBHsexclusively)( _𝑀_ [�] ≲having10 [−][3] very _𝑀_ � Edd low; Elfordratesetofal.accretion2023).
As such, most of these objects are classified as low-luminosity AGN
(LLAGN; Ho 2008). To increase the statistics, we supplemented
these 31 with a further 17 galaxies (see Table A1), selected from the
literature to have dynamical SMBH masses, existing high-resolution
ALMA 1 mm and high-quality X-ray data. The majority of these are
nearby ellipticals and span ranges of _𝐿_ bol and _𝑀_ [�] similar to those of
the WISDOM sources. Hereafter, we refer to the 31 WISDOM plus
17 literature sources as the _primary sample_ .

The 1 mm luminosities of the primary sample sources were derived from high-angular-resolution ALMA Band 6 continuum observations, taken between 2013 and 2021 as part of a large number of
projects. All data were reduced using the Common Astronomy Software Applications (casa) pipeline (McMullin et al. 2007), adopting
a version appropriate for each dataset and a standard calibration strategy. For more details on the data reduction see Davis et al. (2022).

For each dataset, continuum images were produced by combining
the continuum spectral windows (SPWs) and the line-free channels
of the line SPW (when included) using the CASA task tclean in
multi-frequency synthesis (MFS) mode. The resulting continuum
maps have synthesised beams ranging from 0 [′′] _._ 042 to 0 [′′] _._ 723, corresponding to 6 – 330 pc (average spatial resolution ≈ 25 pc). For
each source, we measured the continuum flux density _𝑓_ mm from the
innermost synthesised beam, coincident with the galaxy core. The
mm luminosities were then estimated as _𝐿_ _𝜈,_ mm = 4 _𝜋𝐷_ [2] L _[𝑓]_ [mm] _[𝜈]_ [obs] [,]
where _𝐷_ L is the luminosity distance and _𝜈_ obs the observed frequency
(between 231 and 239 GHz). As all the data were obtained with longbaseline configurations, extended dust emission is resolved out. We
indeed typically detect only a point-like source at each galaxy centre,
arising from unresolved core emission. In 3 (out of 48) galaxies, the
emission is slightly resolved, making our measurements more uncertain. Removing these 3 objects, however, does not affect our results
in any way. The obtained _𝐿_ _𝜈,_ mm are listed in Table A1.
The intrinsic (absorption-corrected) 2–10 keV luminosities
( _𝐿_ X _,_ 2−10 ) of the primary sample sources were retrieved from the
literature, as detailed in Elford et al. (2023). In short, eight of these
galaxies have no X-ray data available and were thus not considered
in the parts of the analysis where _𝐿_ X _,_ 2−10 was required. For the vast
majority of the objects with X-ray data (33/40), the adopted _𝐿_ X _,_ 2−10
was derived from _Chandra_ observations, including only emission
from the unresolved AGN core. For most of the _Chandra_ -observed

objects (26/33), accurate (intrinsic) nuclear _𝐿_ X _,_ 2−10 were retrieved
from the catalogue of Bi et al. (2020, see also Table A1).

Dynamically-determined SMBH masses (from stellar, ionised gas,
molecular gas and/or maser kinematics) are available for a total of
31 primary sample sources (see Table A1). For the remaining 17
galaxies, we estimated _𝑀_ BH using the _𝑀_ BH – _𝜎_ _★_ relation of van den
Bosch (2016), where _𝜎_ _★_ is the stellar velocity dispersion within one
effective radius. This was retrieved from the compilations of van den
Bosch (2016) and Cappellari et al. (2013) when available, from the
HyperLeda database otherwise ( `[http://leda.univ-lyon1.fr](http://leda.univ-lyon1.fr)` ).
Crucially, although constructed based on data availability only (and


MNRAS **000**, 1–7 (2015)



thus not meant to be complete in any statistical sense), our primary
sample spans four orders of magnitude in SMBH mass.


**3** **THE MM FUNDAMENTAL PLANE**


As illustrated in Fig. 1 (left panel), the SMBH masses of our primary
sample galaxies strongly correlate with their _𝐿_ _𝜈,_ mm . A power law was
fitted to the observed trend, using the lts_linefit routine (Cappellari
et al. 2013). This combines the least-trimmed-squares (LTS) robust
regression technique (Rousseeuw 1984) with a least-squares fitting
algorithm, and allows for intrinsic scatter and uncertainties in all
coordinates. The resulting best-fitting power law is:



= (0 _._ 79 ± 0 _._ 08) log 10
� �



_𝐿_ _𝜈,_ mm
� erg s [−][1]



− 39 + (8 _._ 2 ± 0 _._ 1) _,_
� �


(1)



log 10



_𝑀_ BH
� _𝑀_ ⊙



with an observed scatter ( _𝜎_ obs ) of 0 _._ 55 dex and an estimated intrinsic
scatter ( _𝜎_ int ) of 0 _._ 51±0 _._ 08 dex. When including _𝐿_ X _,_ 2−10, we discover
the existence of a tighter correlation (Fig. 1, right panel). In this case,
we used the lts_planefit routine (Cappellari et al. 2013) to find the
best-fitting plane in the (log _𝑀_ BH, log _𝐿_ X _,_ 2−10, log _𝐿_ _𝜈,_ mm ) space:



= (−0 _._ 23 ± 0 _._ 05) log 10
� �



_𝐿_ X _,_ 2−10
� erg s [−][1]



− 40
� �



log 10



_𝑀_ BH
� _𝑀_ ⊙



+(0 _._ 95 ± 0 _._ 07) log 10
�



_𝐿_ _𝜈,_ mm
� erg s [−][1]



− 39 + (8 _._ 35 ± 0 _._ 08) _,_ (2)
� �



with _𝜎_ obs = 0 _._ 45 dex and _𝜎_ int = 0 _._ 40 ± 0 _._ 07 dex. We verified that
this multi-variate plane fit provides a significantly better predictor
for _𝑀_ BH than the simple line fit, having a Δ BIC _>>_ 10 (where Δ BIC is
the difference in the Bayesian information criterion between the line
and plane fits). For both correlations, we also performed Spearman
rank analyses to quantify their statistical significance, and show the
resulting correlation coefficients in the top-left corner of each panel
of Fig. 1. Since the nuclear mm and X-ray emission from AGN is
known to be time variable (typically by a factor of 2 – 3 over year
timescales; Prieto et al. 2016; Fernández-Ontiveros et al. 2019; Behar
et al. 2020), variability likely dominates the observed scatters (and
thus the underlying correlations may be tighter). By analogy with the
previous FP, we dub the correlation in the right panel of Fig. 1 as the
“mm fundamental plane of BH accretion" (hereafter mmFP).
We note that the error budget of the derived _𝐿_ _𝜈,_ mm is dominated
by the ALMA flux calibration uncertainties (≈10% for Band 6 data).
These are, however, much smaller than the estimated intrinsic scatters
of the correlations in Fig. 1 (see above), and thus have a negligible
impact on our results. We also note that the _𝐿_ X _,_ 2−10 of the five
X-ray observed sources without available _Chandra_ data could be
slightly overestimated, due to contamination from diffuse hot gas
in the galactic and circum-galactic medium (CGM; although this
mainly emits in the 0 _._ 3 – 2 keV range) and/or X-ray binaries. While
we verified that any such contamination should be minimal (based
on the scaling laws of Grimm et al. 2003, Kim & Fabbiano 2004
and Boroson et al. 2011), we cannot rule it out entirely. In any case,
removing these five sources does not make any relevant change in
the best-fitting parameters of the mmFP. The same applies when
removing the sources without a robust, dynamical _𝑀_ BH estimate
(the best-fitting line and planes are identical, within their respective
errors, and the observed scatters become only slightly smaller).

_The mm Fundamental Plane_ 3





10


9


8


7


6


5


|=0 .79 p=7 .37e-10<br>,|Col2|=0 .88 p=4 .09e-13<br>,<br>Dynamical MBH<br>M- MBH|
|---|---|---|
|=0.79,p=7.37e-10|||



35 36 37 38 39 40 41 42
log(L, mm /erg s 1 )



5 6 7 8 9 10
-0.23(log(L X, 2 10 [) -40) + 0.95(log(][L], mm [)-39) + 8.35]



**Figure** **1.** Correlation between _𝑀_ BH and _𝐿_ _𝜈,_ mm (left panel) and edge-on view of the _𝑀_ BH - _𝐿_ X _,_ 2−10 - _𝐿_ _𝜈,_ mm correlation (right panel) for the primary sample
galaxies. In both panels, filled blue circles show sources with dynamical _𝑀_ BH measurements, open circles sources with _𝑀_ BH from the _𝑀_ BH – _𝜎_ _★_ relation of
van den Bosch (2016). Error bars are plotted for all points but some are smaller than the symbol used. The best-fitting power-laws (Section 3) are overlaid as a
black solid lines, the observed scatter as black dashed lines. The correlation coefficients _𝜌_ and _𝑝_ -values of the performed Spearman rank analysis are reported
in the top-left corner of each panel.



**3.1** **BASS galaxies**


Although the majority of the primary sample galaxies are LLAGN,
a handful are more luminous systems (see Elford et al. 2023), which
still follow the mmFP. To investigate whether this result holds more
generally, we built a comparison sample from the _Swift_ -BAT AGN
Spectroscopic Survey (BASS), comprising AGN with median _𝑧_ =
0 _._ 05, _𝐿_ bol = 10 [44] erg s [−][1] and _𝑀_ [�] = 0 _._ 01 − 0 _._ 1 _𝑀_ [�] Edd (Koss et al.
2017). We included only the BASS sources for which both ALMA
1 mm observations (with spatial resolutions similar to those of the
primary sample) and nuclear intrinsic _𝐿_ X _,_ 2−10 were available (88
sources; Kawamuro et al. 2022). The SMBH masses of these objects
were taken from the compilation of Koss et al. (2022). The BASS
galaxies are typically more distant than those in the primary sample,
so their _𝑀_ BH have been estimated with a variety of methods (see
Fig. 2). However, most of the sources (50/88) have their _𝑀_ BH from
the _𝑀_ BH – _𝜎_ _★_ relation of Kormendy & Ho (2013). We re-calibrated
these measurements using the _𝑀_ BH – _𝜎_ _★_ relation of van den Bosch
(2016), for consistency with the 17 primary sample sources without
a dynamical SMBH mass estimate.
As illustrated in Fig. 3b, the BASS sources are in agreement with
the best-fitting mmFP, albeit with a larger observed scatter. We performed a Spearman rank analysis to quantify the statistical significance of this relation for the BASS points alone, and verified that they
do show a significant correlation ( _𝑝_ = 0 _._ 002), but with a correlation
coefficient ( _𝜌_ =0.32) smaller than that of the primary sample. Fig. 2
suggests that the larger scatter in this population is (at least partly)
driven by the _𝑀_ BH uncertainties, as the position of a BASS galaxy
with respect to the best-fitting mmFP depends on the method used to
estimate its _𝑀_ BH . For instance, sources with _𝑀_ BH from reverberation
mapping or broad-line methods are located systematically below the
best-fitting line, likely reflecting the different biases in place when
using such techniques (e.g. Farrah et al. 2023).


**4** **PHYSICAL DRIVERS**


The fact that the BASS galaxies are consistent with a relation
mainly defined by LLAGN is surprising. To determine the underlying physics, we compared the observed nuclear mm and X-ray
luminosities of both the primary sample and BASS sources to those
extracted from mock nuclear SEDs arising from both “classic” and



M BH measurement method


**Figure 2.** Residuals of our primary sample (grey shaded region) and BASS
sources (white region) from the best-fitting mmFP, plotted as a function of
the SMBH mass measurement method. “Dyn” refers to dynamical mass measurements, “ _𝜎_ _★_ ” to estimates from the _𝑀_ BH – _𝜎_ _★_ relation of van den Bosch
(2016), “H _𝛼_ /H _𝛽_ ” to the broad-line method and “Reverb” to reverberation
mapping. Each set of data points is represented by a violin describing the
underlying distribution. The number of sources in the mmFP whose _𝑀_ BH has
been estimated using that particular method is indicated above each violin. In
each case, the blue horizontal lines denote the 18 [th], 50 [th] and 85 [th] percentiles

of the distribution.


radiatively-inefficient (ADAF-like) accretion flows, and from compact radio jets.


**4.1** **Torus model**


AGN in the BASS sample (and a few in the primary sample) have
_estimated_ accretion rates in the range _𝑀_ [�] ∼ 0 _._ 01 − 0 _._ 1 _𝑀_ [�] Edd . According to the standard paradigm, in this type of systems the accretion
should occur through the classic geometrically-thin and opticallythick accretion disc surrounded by a dusty torus (e.g. Heckman &
Best 2014). In this scenario, both the mm and the 2 – 10 keV emission arise from the accretion disc, reprocessed by dust in the torus
in the mm and Compton-up scattered by the hot corona in X-rays.
To check if this type of model can reproduce the observed mm and
X-ray luminosities, we used the SKIRTOR library (Stalevski et al.
2012, 2016). The SED models were retrieved from the SKIRTOR


MNRAS **000**, 1–7 (2015)



1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0

4 _I. Ruffa et al._


webpage ( `[https://sites.google.com/site/skirtorus/](https://sites.google.com/site/skirtorus/)` ), but
their spectral coverage (from 300 GHz to 1 _._ 24 keV) is slightly shorter
than that required for this work. We thus expanded the models to the
full range of wavelengths probed here, treating the emission mechanisms self-consistently as prescribed in the original version of the
code (i.e. using the same grey-body curve for millimetre emission,
and a power-law in the X-ray regime; Yang et al. 2020). We followed
the prescriptions of Stalevski et al. (2012, 2016) to scale the models for different _𝐿_ bol, in the range 10 [7] _[.]_ [5] – 10 [12] _[.]_ [5] L ⊙ (i.e. the range
covered by the primary and BASS sources; the torus is expected
to disappear at low accretion rates, but the resulting model predictions are nevertheless instructive). For each SKIRTOR SED model,
we then extracted the predicted 1 mm (specifically, the luminosity
at 237.5 GHz, that is the median ALMA continuum frequency for
both the primary and BASS sources) and intrinsic 2-10 keV luminosities, and compared them with the measured ones. The resulting
predictions are shown in Fig. 3a as a hexagonally binned histogram
(coloured by mean L bol ). The luminosities extracted from the torus
models reasonably reproduces the slope of the _𝐿_ X _,_ 2−10 – _𝐿_ _𝜈,_ mm relation of the BASS sources, but with an offset of about two orders of
magnitude at a given L bol . On the other hand, to explain _𝐿_ _𝜈,_ mm of the
lower accretion rate galaxies, the mm luminosities in the SKIRTOR
models would need to be at least four orders of magnitude larger at a
given accretion rate (and thus X-ray luminosity).


**4.2** **ADAF model**


To build model SEDs arising from radiatively-inefficient accretion
flows around SMBHs, we used the “LLAGN” model of Pesce et al.
(2021, itself a development of previous models by Narayan & Yi
1995a and Mahadevan 1997). In typical LLAGN and some (lowaccretion-rate) Seyferts, the classic accretion disc is either absent or
truncated at some inner radius (the transition usually happens beyond
a few tens of Schwarzschild radii), and replaced by a geometricallythick two-temperature structure in which the ion temperature is
greater than the electron temperature and the accretion occurs at rates
well below the Eddington limit (i.e. ≪ 0 _._ 01 _𝑀_ [�] Edd ; Narayan & Yi
1995b; Ho 2008). The electrons in such radiatively-inefficient flows
(such as advection-dominated accretion flows; ADAFs) cool down
via a combination of self-absorbed synchrotron, bremsstrahlung and
inverse Compton radiation, which together give rise to the nuclear
SED from the mm to the X-rays. The LLAGN model adopted here
solves for the energy balance between the heating and cooling of the
electrons in the flow. We generated a set of model SEDs for a grid
of SMBH masses (10 [6] – 10 [10] M ⊙ ) and Eddington ratios (10 [−][7] –
10 [−][2] ), while all the other free parameters were kept at the defaults
discussed in Appendix A of Pesce et al. (2021). We then extracted
the predicted 237 _._ 5 GHz and 2 − 10 keV luminosities, as described
above. As illustrated by the shape of the model grid in Fig. 3a, the
mm and X-ray luminosities of all the sources (and thus the observed
correlations) are well explained if they arise from an ADAF-like accretion mechanism. The grid is almost aligned with the axes, thus
predicting that the mm luminosity primarily depends on _𝑀_ BH, while
_𝐿_ X _,_ 2−10 primarily traces the Eddington ratio. The tighter correlation
obtained when including _𝐿_ X _,_ 2−10 can be explained by the fact that
the slight tilt of the grid is then taken into account, especially at
higher Eddington ratios. A 3D version of Fig. 3a (including all the
primary sample and only the BASS sources with the most robust, dynamical _𝑀_ BH measurements; see Sect. 3.1 and Fig. 2) is provided as
supplementary online material. In Fig. 3b, we show the projection of
the ADAF model grid onto the best-fitting mmFP. This latter seems
to arise naturally from these models, as an (almost) edge-on view


MNRAS **000**, 1–7 (2015)



10 [41]


10 [39]


10 [37]


10 [35]


10


9


8


7


6


5



(a)


-4.0



10


9


-5.0



8


-6.0



-3.0



12


11


10


-2.0


9


Primary


BASS
ADAF model 8



~~6~~


-7.0



M BH


7


L/L edd



10 [36] 10 [38] 10 [40] 10 [42] 10 [44] 10 [46]

L X, 2 10 [ (erg s] 1 )


(b)



=0.88, p=4.09e-13



ADAF Model

Primary sample (Dyn M BH )


Primary sample (M- M BH )



BASS


5 6 7 8 9 10
-0.23(log(L X, 2 10 [) -40) + 0.95(log(][L], mm [)-39) + 8.35]


**Figure** **3.** **Top** : Correlation between _𝐿_ X _,_ 2−10 and _𝐿_ _𝜈,_ mm for the primary
sample (blue circles) and the BASS (square symbols, coloured by their _𝐿_ bol )
sources. Error bars are plotted for all points but some are smaller than the
symbol used. The black grid illustrates the area covered by the ADAF model
solutions as a function of _𝑀_ BH and the Eddington ratio _𝐿_ / _𝐿_ Edd (Section 4.2).
The purple–yellow coloured bins indicate the region covered by the extrapolated SKIRTOR torus models (Section 4.1), where each hexagonal bin is
coloured by the mean _𝐿_ bol of the sources within that bin. **Bottom** : As the
right panel of Figure 1, but with the BASS galaxies overlaid as green squares
and the grid of ADAF models from Figure 3a projected onto the plane as a
grey shaded area (including a small offset for clarity; see Section 4.2).


of the 3D ( _𝑀_ BH, _𝐿_ X _,_ 2−10, _𝐿_ _𝜈,_ mm ) relation. We note, however, that
keeping the default model parameters from Pesce et al. (2021), the
model well predicts the gradient of the mmFP, but is offset by a small
amount (i.e. the model overpredicts _𝐿_ _𝜈,_ mm at a given SMBH mass
by ≈ 0 _._ 5 dex). Tweaking the model parameters to reduce the effective radiative efficiency easily removes this offset (e.g. by changing
some combination of the effective viscosity, ratio of gas to magnetic
pressure, fraction of viscous heating going directly to the electrons,
outer radius of the ADAF, and/or power-law index of the mass accretion rate as a function of radius). However, as the correct values
of these parameters is not well constrained, here we simply offset the
model grid by a constant 0 _._ 5 dex in SMBH mass to align it with the
observed correlation. We stress that this scaling factor is significantly
smaller than the one required for torus models to reproduce the observed trend (see Section 4.1), and is well within the uncertainties for
the adopted model parameters (see Pesce et al. 2021). Future work
exploring the parameters of ADAF-like models in sources with more
extensive (sub-)mm coverage will allow to better understand the observed correlation, the small offset, and the physics of accretion onto
these SMBHs. This is discussed further in Section 5.

10 [35] 10 [37] 10 [39] 10 [41] 10 [43] 10 [45] 10 [47]



L X, 2 10 [ (erg s] 1 )

**Figure 4.** As Figure 3, but with slightly expanded axis ranges. In this case, the
grids overlaid in black and green illustrate the areas covered by the compact
jet model solutions as a function of _𝑀_ BH and the jet power (Section 4.3),
for jet inclinations of 2.5 [◦] and 90 [◦], respectively. Solutions with intermediate
inclinations lie in-between these two extremes (see Section 4.3).


**4.3** **Compact jet model**


Unlike extended jets (where the synchrotron emission is opticallythin), compact radio jets have self-absorbed synchrotron spectra (similar to those from ADAFs) and have been argued to dominate the nuclear SEDs of LLAGN. In some cases, they are preferred over a pure
ADAF solution, as this would be overly luminous at near-infrared and
optical wavelengths (e.g. Fernández-Ontiveros et al. 2023). To determine if compact jets can explain the observed trends, we used the
Bhjet model of Lucchini et al. (2022). We fixed most of the model
parameters to the values found for M81, a prototypical AGN with
compact jets (Model B in Table 3 of Lucchini et al. 2022), and generated a grid of models varying the SMBH mass (10 [6] – 10 [10] M ⊙ ), jet
power (10 [−][5] _[.]_ [5] – 10 [−][0] _[.]_ [5] L Edd ) and jet inclination to the line-of-sight
(2.5 [◦] – 90 [◦] ). We then extracted from the resulting model SEDs the
predicted _𝐿_ _𝜈,_ mm and _𝐿_ X _,_ 2−10 (as above), and compare them with
the observed ones. In Fig. 4 we show the _𝐿_ X _,_ 2−10 – _𝐿_ _𝜈,_ mm relation
with overlaid the resulting model grids for the extremes in jet inclination (2.5 [◦] and 90 [◦] ). Jets at intermediate inclinations lie between
these two extremes (but evolve quickly towards the i=90 [◦] solution
once the line-of-sight is no longer aligned along the jet cone). The
model grids encompass the majority of the LLAGN and some BASS
sources, but they have significant curvature in the 3D _𝑀_ BH - _𝐿_ X _,_ 2−10 _𝐿_ _𝜈,_ mm space (as for Fig. 3a, a 3D version of Fig. 4 is provided in the
online material). The correlations in Fig. 1 do not seem to occur naturally within this model (as projections of the higher-order surface
onto the axes). The luminosities of high-accretion-rate AGN from
the primary and the BASS samples are harder to explain with these
models, and would require additional X-ray emitting components.
This is perhaps unsurprising, as compact jet models are substantially
more complex than ADAFs (see also Section 5).


**4.4** **Distance uncertainties**


Both _𝑀_ BH and luminosity measurements are systematically affected
by the assumed galaxy distance _𝐷_, with _𝑀_ BH ∝ _𝐷_ and _𝐿_ ∝ _𝐷_ [2] .
Large distance errors can thus introduce large uncertainties on _𝑀_ BH
and _𝐿_, and the difference in how these quantities scale with distance
can give rise to spurious correlations. To test that this is not affecting
our results, we performed a simple Monte Carlo simulation, drawing
_𝑀_ BH and the luminosities from independent Gaussian distributions
that are truly uncorrelated, forcing a correlation to arise due to distance errors alone. The magnitude of the distance errors required



_The mm Fundamental Plane_ 5


to reproduce the Spearman rank correlation coefficients in Fig. 1
turned out to be ≥1.5 dex, much higher than that of our primary
sample sources and - more in general - expected for real distance
measurements. In addition, the slope of relations purely due to distance uncertainties would be substantially flatter than those observed
(gradients of 0.5 for the _𝑀_ BH - _𝐿_ _𝜈,_ mm correlation and 0.25 for the
mmFP, as opposed to the observed ≈0.8 and ≈1, respectively).
To further check for any systematic distance bias, we carried out
a simple quality-checking exercise for our primary sample. We restricted our analysis to only those sources with the most accurate
(redshift-independent) distances (26/48), i.e. derived from surface
brightness fluctuations, tip of the red giant branch methods, supernovae, Cepheids, masers, the planetary nebula luminosity function
and the globular cluster luminosity function. This led us to obtain
much tighter correlations, with an intrinsic scatter of 0 _._ 19 dex for the
_𝑀_ BH − _𝐿_ _𝜈,_ mm relation and only 0 _._ 11 dex for the mmFP. The corresponding Spearman rank coefficients are _𝜌_ = 0 _._ 84 ( _𝑝_ = 5 _._ 05 × 10 [−][7] )
and _𝜌_ = 0 _._ 93 ( _𝑝_ = 2 _._ 67 × 10 [−][9] ), respectively. We thus conclude that
our results are not biased due to distance uncertainties.


**5** **DISCUSSION AND CONCLUSIONS**


We report here the finding of tight _𝑀_ BH − _𝐿_ _𝜈,_ mm and _𝑀_ BH − _𝐿_ X _,_ 2−10 −
_𝐿_ _𝜈,_ mm correlations (Fig. 1). We dub the latter the “mm fundamental
plane of BH accretion" and find it to hold for both low- (mostly WISDOM) and high- (mostly BASS) luminosity AGN. To understand the
physics underlying the mmFP, we compared the observed trend with
models predicting the emission from different nuclear mechanisms.
We find that the results for both our sample and the BASS sources
are best explained if their emission in the mm and X-rays primarily arises from an ADAF-like process, but cannot be explained by
a classic torus model (see Fig. 3). This suggests that some kind of
radiatively-inefficient accretion process may play a role in both lowand high-luminosity AGN, at least in the range of luminosities and
accretion rates probed by the sources included in this work. While
torii are known to exist in many of these AGN, some regions around
their SMBHs may be radiatively-inefficient. For instance, some accretion disc solutions allow discs to transition from ADAF-like to

geometrically-thin (and vice versa at different radii), and ADAFs
could also exist above and below classic accretion discs (Mahadevan
1997). Although the exact conditions under which this applies are
still to be investigated, it is clear that - if confirmed - our results will
have profound implications for our understanding of BH accretion in
many different types of AGN.
We also explored the possibility that both the mm and X-ray emissions arise from compact (and thus probably young; O’Dea & Saikia
2020) radio jets (Section 4.3). These have been argued to dominate the whole SEDs of LLAGN (e.g. Fernández-Ontiveros et al.
2023) and have spectral properties similar to those of an ADAF at
the wavelengths probed here. This is also consistent with one of the
most popular scenarios for the origin of the radio FP of LLAGN,
suggesting that the correlation arises from strongly sub-Eddington
jet-dominated emission (e.g. Falcke et al. 2004; Plotkin et al. 2012).
The contribution of compact jets to the nuclear SEDs of radiativelyefficient, quasar-like AGN is instead still hotly debated (e.g. Fawcett
et al. 2020; Girdhar et al. 2022). Our results are marginally consistent with these scenarios, as we find that compact jet models can
explain the correlations for most of the LLAGN, but additional X-ray
emitting components are required in the higher-luminosity systems.
In short, we demonstrated that ADAF-like models convincingly
predict the mmFP. Compact jets are also a plausible explanation (at
least for LLAGN), but the corresponding models do not reproduce


MNRAS **000**, 1–7 (2015)

6 _I. Ruffa et al._


the correlation as naturally as the ADAF-like ones. We caution, however, that the plasma physics underlying both the ADAF and compact
jet models is not well constrained, and significant uncertainties are
present in all the model parameters and how they interact. We thus
conclude that, while “classic” torus models seem to be ruled out, either ADAF-like or compact jet emission have the potential to explain
the observed trend. The presence of one (or more) of these mechanisms could even help explaining the increased far-infrared/sub-mm
contribution attributed to AGN in some empirical SED models (e.g.
Symeonidis 2022). The tight _𝐿_ X _,_ 2−10 - _𝐿_ _𝜈,_ mm correlation observed
in Fig. 3a for the BASS sources is also consistent with the one reported by Ricci et al. (2023) between the 100 GHz and 14-150 keV
luminosities (see also Behar et al. 2018), and our results add interesting clues onto its origin. Determining with certainty the relevant
mechanism(s) giving rise to the observed correlations is beyond the
scope of this work, but is crucial to further our understanding of the
SMBH accretion/ejection processes in different AGN types.
Beyond carrying information on the nuclear physics, the correlations presented here provide new rapid methods to indirectly estimate
the mass of SMBHs (or their accretion rates, if one has alternative,
robust estimates of _𝑀_ BH and _𝐿_ _𝜈,_ mm ; see e.g. Ricci et al. 2023). Although direct _𝑀_ BH estimates can be obtained using a variety of techniques (e.g. stellar or gas kinematics, reverberation mapping), these
typically require very time-consuming observational campaigns and
currently have limited application beyond the local Universe. The
ability to use nuclear mm and (optionally) X-ray luminosities allows _𝑀_ BH estimates when dynamical measurements are not possible
and/or the standard scaling relations are unusable (such as in dwarf
or disturbed galaxies). It also allows _𝑀_ BH predictions over a wider
range of redshifts. At the high-mass end of the correlations, ALMA
can allow us to constrain _𝑀_ BH up to _𝑧_ ≈ 0 _._ 3 (and is limited more
by angular resolution and frequency coverage than sensitivity). Proposed new interferometers (such as the next-generation Very Large
Array, ngVLA) should be able to push this to _𝑧_ = 1 and beyond.
Large X-ray surveys that can provide complementary X-ray data are
also ongoing (e.g. eROSITA), and next-generation satellites (such as
the Advanced Telescope for High ENergy Astrophysics, _Athena_ ) will
extend these to higher- _𝑧_ . We also note that the intrinsic scatter of
the _𝑀_ BH − _𝐿_ _𝜈,_ mm relation is comparable to that of the _𝑀_ BH − _𝜎_ _★_
relation (e.g. van den Bosch 2016), and _𝜎_ int of the mmFP in Fig. 1 is
comparable or even lower than that of its radio counterpart (depending on the sample used to fit the plane; see e.g. Merloni et al. 2003;
Falcke et al. 2004; Plotkin et al. 2012; Gültekin et al. 2019b). When
restricting our analysis to only those primary sample sources with
the most accurate (redshift-independent) distances, we obtain much
tighter correlations (see Section 4.4), with _𝜎_ int comparable to that
of the tightest scaling relations in Astronomy (such as the Baryonic
Tully-Fisher relation; e.g. Lelli et al. 2016, 2019). This technique if sufficiently verified - is thus well suited to constrain the details of
SMBH-host galaxy co-evolution in regimes that have been difficult
to access up to now (Williams et al. 2023).


**ACKNOWLEDGEMENTS**


IR and TAD acknowledge support from grant ST/S00033X/1 through
the UK Science and Technology Facilities Council (STFC). MB and
TGW were supported by STFC consolidated grant ‘Astrophysics
at Oxford’ ST/H002456/1 and ST/K00106X/1. DH acknowledges
support from the Canada Research Chairs (CRC) program, the
NSERC Discovery Grant program, and the Canadian Tri-Agency
New Frontiers in Research – Explorations fund. This paper makes
use of ALMA data. ALMA is a partnership of ESO (representing
its member states), NSF (USA) and NINS (Japan), together with


MNRAS **000**, 1–7 (2015)



NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.
We acknowledge also the usage of the HyperLeda database and the
NASA/IPAC Extragalactic Database (NED).


**DATA AVAILABILITY**


The ALMA data used in this article are all available to download at

the ALMA archive ( `[https://almascience.nrao.edu/asax/](https://almascience.nrao.edu/asax/)` ).
The calibrated data, final products and original plots generated for
this research study will be shared upon reasonable request to the first
author. The X-ray data have been retrieved from the catalogue of Bi
et al. (2020) or from the NASA/IPAC Extragalactic Database (NED;
`[https://ned.ipac.caltech.edu/](https://ned.ipac.caltech.edu/)` ).


**REFERENCES**


[Behar E., Vogel S., Baldi R. D., Smith K. L., Mushotzky R. F., 2018, MNRAS,](http://dx.doi.org/10.1093/mnras/sty850)

[478, 399](https://ui.adsabs.harvard.edu/abs/2018MNRAS.478..399B)

[Behar E., et al., 2020, MNRAS, 491, 3523](http://dx.doi.org/10.1093/mnras/stz3273)
[Bi S., Feng H., Ho L. C., 2020, ApJ, 900, 124](http://dx.doi.org/10.3847/1538-4357/aba761)
[Boroson B., Kim D.-W., Fabbiano G., 2011, ApJ, 729, 12](http://dx.doi.org/10.1088/0004-637X/729/1/12)
[Cappellari M., et al., 2013, MNRAS, 432, 1709](http://dx.doi.org/10.1093/mnras/stt562)
D’Onofrio M., Marziani P., Chiosi C., 2021, Frontiers in [Astronomy](http://dx.doi.org/10.3389/fspas.2021.694554) and
[Space Sciences, 8, 157](http://dx.doi.org/10.3389/fspas.2021.694554)
Davis T. A., Bureau M., Onishi K., Cappellari M., Iguchi S., Sarzi M., 2017,

[MNRAS, 468, 4675](http://dx.doi.org/10.1093/mnras/stw3217)

[Davis T. A., et al., 2022, MNRAS, 512, 1522](http://dx.doi.org/10.1093/mnras/stac600)
Elford J. S., et al., 2023, WISDOM Project - XVI. The link between circumnuclear molecular gas reservoirs and active galactic nucleus fuelling,

Submitted to MNRAS

[Falcke H., Körding E., Markoff S., 2004, A&A, 414, 895](http://dx.doi.org/10.1051/0004-6361:20031683)
[Farrah D., et al., 2023, ApJ, 943, 133](http://dx.doi.org/10.3847/1538-4357/acac2e)
Fawcett V. A., Alexander D. M., Rosario D. J., Klindt L., Fotopoulou S.,
[Lusso E., Morabito L. K., Calistro Rivera G., 2020, MNRAS, 494, 4802](http://dx.doi.org/10.1093/mnras/staa954)
Fernández-Ontiveros J. A., López-Gonzaga N., Prieto M. A., Acosta-Pulido
[J. A., Lopez-Rodriguez E., Asmus D., Tristram K. R. W., 2019, MNRAS,](http://dx.doi.org/10.1093/mnras/stz716)
[485, 5377](https://ui.adsabs.harvard.edu/abs/2019MNRAS.485.5377F)
[Fernández-Ontiveros J. A., López-López X., Prieto A., 2023, A&A, 670, A22](http://dx.doi.org/10.1051/0004-6361/202243547)
[Girdhar A., et al., 2022, MNRAS, 512, 1608](http://dx.doi.org/10.1093/mnras/stac073)
[Grimm H. J., Gilfanov M., Sunyaev R., 2003, MNRAS, 339, 793](http://dx.doi.org/10.1046/j.1365-8711.2003.06224.x)
[Gültekin K., et al., 2009, ApJ, 698, 198](http://dx.doi.org/10.1088/0004-637X/698/1/198)
Gültekin K., King A. L., Cackett E. M., Nyland K., Miller J. M., Di Matteo
[T., Markoff S., Rupen M. P., 2019a, ApJ, 871, 80](http://dx.doi.org/10.3847/1538-4357/aaf6b9)
Gültekin K., King A. L., Cackett E. M., Nyland K., Miller J. M., Di Matteo
[T., Markoff S., Rupen M. P., 2019b, ApJ, 871, 80](http://dx.doi.org/10.3847/1538-4357/aaf6b9)
[Heckman T. M., Best P. N., 2014, ARA&A, 52, 589](http://dx.doi.org/10.1146/annurev-astro-081913-035722)

[Ho L. C., 2008, ARA&A, 46, 475](http://dx.doi.org/10.1146/annurev.astro.45.051806.110546)
[Kawamuro T., et al., 2022, ApJ, 938, 87](http://dx.doi.org/10.3847/1538-4357/ac8794)
[Kim D.-W., Fabbiano G., 2004, ApJ, 611, 846](http://dx.doi.org/10.1086/422210)
[Kormendy J., Ho L. C., 2013, ARA&A, 51, 511](http://dx.doi.org/10.1146/annurev-astro-082708-101811)
[Koss M., et al., 2017, ApJ, 850, 74](http://dx.doi.org/10.3847/1538-4357/aa8ec9)
[Koss M. J., et al., 2022, ApJS, 261, 2](http://dx.doi.org/10.3847/1538-4365/ac6c05)
[Lelli F., McGaugh S. S., Schombert J. M., 2016, ApJ, 816, L14](http://dx.doi.org/10.3847/2041-8205/816/1/L14)
Lelli F., McGaugh S. S., Schombert J. M., Desmond H., Katz H., 2019,

[MNRAS, 484, 3267](http://dx.doi.org/10.1093/mnras/stz205)

[Lucchini M., et al., 2022, MNRAS, 517, 5853](http://dx.doi.org/10.1093/mnras/stac2904)
[Mahadevan R., 1997, ApJ, 477, 585](http://dx.doi.org/10.1086/303727)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Merloni A., Heinz S., di Matteo T., 2003, MNRAS, 345, 1057](http://dx.doi.org/10.1046/j.1365-2966.2003.07017.x)
[Narayan R., Yi I., 1995a, ApJ, 444, 231](http://dx.doi.org/10.1086/175599)
[Narayan R., Yi I., 1995b, ApJ, 452, 710](http://dx.doi.org/10.1086/176343)

[O’Dea C. P., Saikia D. J., 2020, arXiv e-prints, p. arXiv:2009.02750](https://ui.adsabs.harvard.edu/abs/2020arXiv200902750O)
[Pesce D. W., et al., 2021, ApJ, 923, 260](http://dx.doi.org/10.3847/1538-4357/ac2eb5)
Plotkin R. M., Markoff S., Kelly B. C., Körding E., Anderson S. F., 2012,

[MNRAS, 419, 267](http://dx.doi.org/10.1111/j.1365-2966.2011.19689.x)
Prieto M. A., Fernández-Ontiveros J. A., Markoff S., Espada D., González[Martín O., 2016, MNRAS, 457, 3801](http://dx.doi.org/10.1093/mnras/stw166)
[Ricci C., et al., 2023, arXiv e-prints, p. arXiv:2306.04679](http://dx.doi.org/10.48550/arXiv.2306.04679)
Rousseeuw P. J., 1984, Journal of the American Statistical Association., 79
[Saikia P., Körding E., Falcke H., 2015, MNRAS, 450, 2317](http://dx.doi.org/10.1093/mnras/stv731)
[Stalevski M., Fritz J., Baes M., Nakos T., Popović L. Č., 2012, MNRAS, 420,](http://dx.doi.org/10.1111/j.1365-2966.2011.19775.x)
[2756](https://ui.adsabs.harvard.edu/abs/2012MNRAS.420.2756S)

Stalevski M., Ricci C., Ueda Y., Lira P., Fritz J., Baes M., 2016, [MNRAS,](http://dx.doi.org/10.1093/mnras/stw444)


[458, 2288](https://ui.adsabs.harvard.edu/abs/2016MNRAS.458.2288S)
[Symeonidis M., 2022, MNRAS, 509, 3209](http://dx.doi.org/10.1093/mnras/stab3037)
Williams J. K., Gliozzi M., Bockwoldt K. A., Shuvo O. I., 2023, [MNRAS,](http://dx.doi.org/10.1093/mnras/stad718)


[521, 2897](https://ui.adsabs.harvard.edu/abs/2023MNRAS.521.2897W)
[Yang G., et al., 2020, MNRAS, 491, 740](http://dx.doi.org/10.1093/mnras/stz3001)
[van den Bosch R. C. E., 2016, ApJ, 831, 134](http://dx.doi.org/10.3847/0004-637X/831/2/134)


**APPENDIX A:** **DATA TABLE**


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



_The mm Fundamental Plane_ 7


MNRAS **000**, 1–7 (2015)

8 _I. Ruffa et al._


**Table A1.** Full list and main parameters of the galaxies in the primary sample.


Sample Galaxy D log _𝑀_ BH Δlog _𝑀_ BH Method log _𝐿_ _𝜈,_ mm ALMA project log _𝐿_ X _,_ 2−10 Δlog _𝐿_ X _,_ 2−10
(Mpc) (M ⊙ ) (dex) (erg s [−][1] ) (erg s [−][1] ) (dex)
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10)


WISDOM FRL49 85.7 8.20 0.2 Dyn 39.28 a 43.27 0.04
FRL1146 136.7 7.85 0.30 _𝜎_ _★_ _<_ 38 _._ 76 a 43.41 0.04
MRK567 140.6 7.48 0.30 _𝜎_ _★_ 39.39 a – –
**NGC0404** 3.0 5.74 0.30 Dyn 35.99 b 37.20 0.04
NGC0449 66.3 8.77 0.30 _𝜎_ _★_ 38.87 c 40.58 0.04
NGC0524 23.3 8.60 0.32 Dyn 38.94 d 38.55 0.04
**NGC0708** 58.3 8.30 0.30 Dyn 39.10 d 39.39 0.04
NGC1194 53.2 7.85 0.10 Dyn 39.09 e 41.54 0.04
**NGC1387** 19.9 6.90 0.20 Dyn 38.07 c 39.33 0.04
NGC1574 19.3 8.05 0.20 Dyn 38.55 f – –
**NGC2110** 35.6 8.77 0.30 _𝜎_ _★_ 39.89 g 42.71 0.04
**NGC3169** 18.7 7.85 0.30 _𝜎_ _★_ 38.53 h 41.53 0.04
NGC3351 10.0 5.85 0.30 _𝜎_ _★_ _<_ 37 _._ 25 i 38.74 0.04
NGC3368 18.0 6.87 0.10 Dyn _<_ 37 _._ 73 g 39.30 0.05
**NGC3607** 22.2 8.14 0.15 Dyn 38.58 h 39.16 0.04
NGC4061 94.1 9.30 0.30 Dyn 39.78 j – –
NGC4429 16.5 8.17 0.10 Dyn 38.08 i 39.12 0.10
**NGC4435** 16.5 7.40 0.20 Dyn 37.76 h 39.47 0.04
**NGC4438** 16.5 7.70 0.30 _𝜎_ _★_ 37.61 h 39.08 0.04
**NGC4501** 14.0 6.79 0.30 _𝜎_ _★_ 37.90 k 40.09 0.04
**NGC4697** 11.4 7.20 0.10 Dyn 37.25 h 38.52 0.04
NGC4826 7.4 6.20 0.11 Dyn 36.99 i 37.96 0.11
NGC5064 34.0 8.39 0.30 _𝜎_ _★_ 37.96 k – –
**NGC5765b** 114.0 7.32 0.30 _𝜎_ _★_ 39.06 e 40.73 0.05
NGC5806 21.4 6.95 0.30 _𝜎_ _★_ _<_ 37 _._ 26 c – –
**NGC5995** 107.5 8.55 0.30 _𝜎_ _★_ 39.51 a 43.39 0.04
NGC6753 42.0 8.42 0.30 _𝜎_ _★_ _<_ 37 _._ 82 k – –
NGC6958 30.6 7.89 0.30 _𝜎_ _★_ 39.47 k – –
**NGC7052** 51.6 8.91 0.30 _𝜎_ _★_ 40.13 j 40.02 0.05
**NGC7172** 33.9 8.05 0.30 _𝜎_ _★_ 39.44 l 43.00 0.05
PGC043387 95.8 8.42 0.30 _𝜎_ _★_ 38 _._ 90 h – –


Literature **Circinus** 4.2 6.23 0.08 Dyn 37.57 m 42.20 0.04
**IC1459** 25.9 9.45 0.30 Dyn 40.60 n 40.91 0.10
**M87** 16.5 9.81 0.04 Dyn 40.75 o 40.56 0.05
**NGC1316** 19.9 8.23 0.08 Dyn 38.73 p 39.65 0.04
**NGC1332** 22.3 8.82 0.04 Dyn 38.91 q 39.15 0.08
**NGC1380** 17.1 8.17 0.17 Dyn 38.53 r 39.07 0.04
NGC3227 17.0 7.18 0.17 Dyn 37.70 s 41.95 0.09
NGC3245 21.5 8.32 0.10 Dyn 38.42 t 38.88 0.09
NGC3393 53.6 7.52 0.03 Dyn 38.34 e 40.92 0.09
NGC3489 12.0 6.78 0.07 Dyn 36.77 u 39.07 0.09
NGC3504 13.6 7.00 0.07 Dyn 38.38 v 41.05 0.09
**NGC3585** 20.6 8.52 0.13 Dyn 37.89 t 38.85 0.04
**NGC4374** 18.5 8.96 0.05 Dyn 39.84 w 39.95 0.04
**NGC4388** 19.8 6.94 0.01 Dyn 38.88 x 42.33 0.05
**NGC4395** 4.4 5.60 0.31 Dyn 35.85 y 39.91 0.05
**NGC6861** 27.3 9.30 0.22 Dyn 39.52 r 39.29 0.04
**UGC2698** 91.0 9.39 0.12 Dyn 39.53 z 40.46 0.09


_Notes:_ (1) Sub-sample. (2) Galaxy name. (3) Most accurate galaxy distance. (4), (5) and (6) SMBH mass, uncertainty, and measurement method. “Dyn” refers to
dynamical measurements, “ _𝜎_ _★_ ” to estimates from the _𝑀_ BH – _𝜎_ _★_ relation of van den Bosch (2016). (7) Millimetre luminosity. Errors are not reported because they
are simply dominated by flux calibration uncertainties, which are ≈10% for ALMA Band 6 (see Section 2 of the main paper). (8) Project code of the ALMA continuum observations, where a: 2017.1.00904.S, b: 2017.1.00572.S, c: 2016.1.00437.S, d: 2017.1.00391.S, e: 2016.1.01553.S, f: 2015.1.00419.S, g: 2016.1.00839.S,
h: 2015.1.00598.S, i: 2013.1.0049.S, j: 2018.1.00397.S, k: 2015.1.00466.S, l: 2019.1.00363.S, m: 2018.1.01321.S, n: 2015.1.01572.S, o: 2015.1.01352.S,
p: 2017.1.01140.S, q: 2015.1.00896.S, r: 2013.1.00229.S, s: 2016.1.00254.S, t: 2017.1.00301.S, u: 2017.1.00766.S, v: 2017.1.00964.S, w: 2013.1.00828.S,
x: 2012.1.00139.S, y: 2015.1.00597.S, z: 2016.1.01010.S. (9) and (10) intrinsic (absorption-corrected) 2 − 10 keV X-ray luminosity, and associated uncertainty. Galaxies highlighted in bold have their _𝐿_ X _,_ 2−10 taken from the catalogue of Bi et al. (2020).


MNRAS **000**, 1–7 (2015)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[3].provided.evidence[0]",
  "value": "Comparison sample of 88 luminous AGN with ALMA 1 mm, X-ray, and SMBH mass data",
  "failed_quote": "To investigate whether this result holds more generally, we built a comparison sample from the Swift -BAT AGN Spectroscopic Survey (BASS), comprising AGN with median 𝑧 = 0 . 05, 𝐿 bol = 10 44 erg s −1 and 𝑀  = 0 . 01 − 0 . 1 𝑀  Edd (Koss et al. 2017)."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "M_BH - L_nu,mm power-law slope = 0.79 dimensionless",
  "failed_quote": "= (0 . 79 ± 0 . 08) log 10   𝐿 𝜈, mm  erg s −1 − 39 + (8 . 2 ± 0 . 1) ,"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "M_BH - L_nu,mm power-law intercept = 8.2 dex",
  "failed_quote": "= (0 . 79 ± 0 . 08) log 10   𝐿 𝜈, mm  erg s −1 − 39 + (8 . 2 ± 0 . 1) ,"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "mmFP log(L_X,2-10) coefficient = -0.23 dimensionless",
  "failed_quote": "= (−0 . 23 ± 0 . 05) log 10   𝐿 X , 2−10  erg s −1 − 40"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "mmFP log(L_nu,mm) coefficient = 0.95 dimensionless",
  "failed_quote": "+(0 . 95 ± 0 . 07) log 10  𝐿 𝜈, mm  erg s −1 − 39 + (8 . 35 ± 0 . 08) , (2)"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "mmFP intercept = 8.35 dex",
  "failed_quote": "+(0 . 95 ± 0 . 07) log 10  𝐿 𝜈, mm  erg s −1 − 39 + (8 . 35 ± 0 . 08) , (2)"
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "ADAF models naturally reproduce the slope and nearly edge-on projection of the mmFP (with a 0.5 dex offset in M_BH using default parameters), while compact jet models encompass most LLAGN but exhibit 3D curvature and require extra X-ray components for high-luminosity AGN.",
  "failed_quote": "In Fig. 3b, we show the projection of the ADAF model grid onto the best-fitting mmFP. This latter seems to arise naturally from these models, as an (almost) edge-on view of the 3D ( 𝑀 BH, 𝐿 X , 2−10, 𝐿 𝜈, mm ) relation."
 },
 {
  "path": "claims[3].evidence[1]",
  "value": "Radiatively-inefficient processes (ADAF-like flows or compact jets) likely play a key role in both low- and high-luminosity AGN, with ADAF models reproducing the relation more naturally.",
  "failed_quote": "In short, we demonstrated that ADAF-like models convincingly predict the mmFP. Compact jets are also a plausible explanation (at least for LLAGN), but the corresponding models do not reproduce the correlation as naturally as the ADAF-like ones."
 }
]
```
