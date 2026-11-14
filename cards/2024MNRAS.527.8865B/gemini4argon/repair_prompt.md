# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.527.8865B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–27 (2023) Preprint 30 November 2023 Compiled using MNRAS L [A] TEX style file v3.0

## FLASH: Faint Lenses from Associated Selection with Herschel


Tom J. L. C. Bakx [1] _[,]_ [2] _[,]_ [3] _[★]_, Bethany S. Gray [4], Joaquin González-Nuevo [5] _[,]_ [6], Laura Bonavera [5] _[,]_ [6],
Aristeidis Amvrosiadis [7], Stephen Eales [8], Masato Hagimoto [2], and Stephen Serjeant [9] .
1 _Department of Space, Earth, & Environment, Chalmers University of Technology, Chalmersplatsen 4 412 96 Gothenburg, Sweden_
2 _Department of Physics, Graduate School of Science, Nagoya University, Aichi 464-8602, Japan_
3 _National Astronomical Observatory of Japan, 2-21-1, Osawa, Mitaka, Tokyo 181-8588, Japan._
4 _Department of Architecture & Civil Engineering, University of Bath, Claverton Down, Bath, BA2 7AY, UK_
5 _Departamento de Fisica, Universidad de Oviedo, C. Federico Garcia Lorca 18, E-33007 Oviedo, Spain_
6 _Instituto Universitario de Ciencias y Tecnologas Espaciales de Asturias (ICTEA), C. Independencia 13, E-33004 Oviedo, Spain_
7 _Institute for Computational Cosmology, Durham University, South Road, Durham DH1 3LE, UK_
8 _School of Physics and Astronomy, Cardiff University, The Parade, Cardiff, CF24 3AA, UK_
9 _School of Physical Sciences, The Open University, Milton Keynes, MK7 6AA, UK_


Accepted 2023 November 27. Received 2023 November 22; in original form 2023 September 18


**ABSTRACT**

We report the ALMA Band 7 observations of 86 _Herschel_ sources that likely contain gravitationally-lensed galaxies. These
sources are selected with relatively faint 500 _𝜇_ m flux densities between 15 to 85 mJy in an effort to characterize the effect of
lensing across the entire million-source _Herschel_ catalogue. These lensed candidates were identified by their close proximity
to bright galaxies in the near-infrared VISTA Kilo-Degree Infrared Galaxy Survey (VIKING) survey. Our high-resolution
observations (0.15 arcsec) confirm 47 per cent of the initial candidates as gravitational lenses, while lensing cannot be excluded
across the remaining sample. We find average lensing masses (log _𝑀_ / _𝑀_ ⊙ = 12 _._ 9 ± 0 _._ 5) in line with previous experiments,
although direct observations might struggle to identify the most massive foreground lenses across the remaining 53 per cent of
the sample, particularly for lenses with larger Einstein radii. Our observations confirm previous indications that more lenses exist
at low flux densities than expected from strong galaxy-galaxy lensing models alone, where the excess is likely due to additional
contributions of cluster lenses and weak lensing. If we apply our method across the total 660 sqr. deg. H-ATLAS field, it would
allow us to robustly identify 3000 gravitational lenses across the 660 square degree _Herschel_ ATLAS fields.


**Key words:** general – galaxies: evolution - submillimetre: galaxies – galaxies: high-redshift - gravitational lensing: strong



**1** **INTRODUCTION**


Concentrated mass distributions, such as stars (Dyson et al. 1920;
Kelly et al. 2018; Welch et al. 2022), galaxies (Treu 2010) and galaxy
clusters (Kneib & Natarajan 2011; González-Nuevo et al. 2012, 2017;
Bonavera et al. 2019; Crespo et al. 2022; Fernandez et al. 2022) can
redirect light, extending the number of sightlines onto an object
resulting in so-called gravitational lensing. Particularly in the case of
strong gravitational lensing, defined as a magnification _𝜇>_ 2, these
cases can offer a significant increase in spatial and observational
sensitivity. This effect is determined by the foreground distribution
of matter, and can thus provide a constraint on the mass distribution
of our Universe (Kochanek 1992, 1996; Grillo et al. 2008; Oguri
et al. 2012; Eales 2015).
Especially given the low angular resolution of sub-mm observations, the increase in angular resolution by gravitational lensing
resulted in spectacular images of dust-obscured star-formation at
cosmic noon (ALMA Partnership et al. 2015; Dye et al. 2015; Rybak et al. 2015a; Tamura et al. 2015). Initial observations in the late


_★_ E-mail: tom.bakx@chalmers.se (Chalmers University)


© 2023 The Authors



1990’s had revealed a population of dust-obscured galaxies rivaling
the total galaxy evolution seen in optical wavelengths (Smail et al.
1997; Hughes et al. 1998; Ivison et al. 1998). The brightest dusty
star-forming galaxies (DSFGs) have observed star-formation rates
in excess of 1000 M ⊙ /yr, resulting in an unsustainable evolutionary
phase through violent star-formation feedback (Andrews & Thompson 2011; Rowan-Robinson et al. 2016). The evolutionary pathway
of these star-forming systems is still not adequately understood, as
demonstrated by the prevalence estimates from DSFG models, which
often predict three to four orders of magnitudes below what is observed (Baugh et al. 2005). Because these galaxies are very rare
(a few / deg [2] ), hydrodynamical models struggle to include enough
volume to simulate these galaxies accurately in order to test the evolutionary pathways of these DSFGs (e.g., Narayanan et al. 2015).
As a consequence, the best path to understanding dusty star-forming
galaxies is through direct observations of complete samples. Gravitational lensing offers an opportunity to study these DSFGs at high
resolution. Meanwhile, observations to date have revealed a large
source-to-source variation, with some sources showing stable rotation (Dye et al. 2018; Rizzo et al. 2020), while other sources appear
to be in a state of rapid collapse (e.g., SDP.81; Dye et al. 2015; Rybak et al. 2015b; Tamura et al. 2015). In order to capture this large

2 _Tom Bakx et al._


variation of sources, large samples ( _>_ 100) of lensed DSFGs are
needed to characterize the evolutionary pathway(s) of these extreme
star-forming systems.
Although lensing is a rare phenomena, large area surveys in submm and mm revealed a large population of ultra-bright sources, that
upon further inspection were revealed to be gravitationally-lensed
(Negrello et al. 2010, 2014, 2017; Vieira et al. 2013). The steep
bright-end of the luminosity function (i.e., brighter sources are increasingly rare; Lapi et al. 2011) means that the unlikely gravitational lensing magnification of fainter but more numerous sources
are statistically-preferred to observing non-lensed intrinsically hyperluminous sources. As a result, in the sub-mm domain, the wide-field
H-ATLAS (Eales et al. 2010) and HerMES (Oliver et al. 2012) surveys with the _Herschel Space Observatory_ have revealed a population
of dusty lensed sources by selecting sources at _𝑆_ 500 _>_ 100 mJy (Negrello et al. 2010). Similarly, the large-area nature of CMB-studies
with ground- and space-based telescopes means that these surveys
are also well-suited towards lens selection, with the all-sky _Planck_
survey showcasing exceptional lensing morphologies (Kamieneski
et al. 2023), and perfectly-circular Einstein rings shown in the South
Pole Telescope survey — revealed in high-resolution with ALMA
and JWST (Spilker et al. 2016; Rizzo et al. 2020). Finally, while
the mapping speed of ground-based observations at submm wavelengths is limited by the atmospheric transmission, the recent largearea SCUBA-2 Large eXtragalactic Survey (S2XLS) is bridging the
border between lenses and intrinsically-bright sources (Garratt et al.
2023). The large beam-width of these selection techniques, however, mean that only time-expensive follow-up observations of these
sources can reveal the true nature of these galaxies (Bussmann et al.
2013, 2015; Spilker et al. 2016) — and worse yet, the intrinsic properties of the sample as a whole (Gruppioni et al. 2013).
One way to circumvent these limitations is by a search for the
foreground lensing systems at complementary wavelengths such as
optical or near-infrared. These foreground galaxies might be detected
in optical (SDSS; González-Nuevo et al. 2012, 2017, 2019; Bourne
et al. 2016) or near-infrared (NIR; e.g., VIKING; Fleuren et al. 2012;
Bakx et al. 2020a; Ward et al. 2022) surveys, while the dusty nature of these DSFGs mean the background galaxies are likely not
detected in optical/NIR surveys. These tests vary in their sophistication, with several models simply identifying nearby foreground
galaxies (Roseboom et al. 2010; Negrello et al. 2010), to innovative
mathematical techniques (Fleuren et al. 2012; Bourne et al. 2016)
and statistical correlations accounting for redshifts and spatial distributions (González-Nuevo et al. 2019), even including the additional
spatial offsets due to gravitational lensing (Bakx et al. 2020a).
These methods can statistically characterize the prevalence of
lensed sources across the full extent of the _Herschel_ sample — near
one million dusty sources (Valiante et al. 2016; Furlanetto et al.
2018; Maddox et al. 2018; Shirley et al. 2021; Ward et al. 2022) —
however, they have not been tested experimentally. The best way of
resolving gravitational lensing directly is through resolved sub-mm
observations to reveal the lensing structures (Spilker et al. 2016;
Amvrosiadis et al. 2018; Dye et al. 2018; Kamieneski et al. 2023).
While the easiest lenses to identify are at the brightest flux densities
( _>_ 100 mJy at 500 micron Negrello et al. 2010, 2014, 2017), both in
terms of their apparent brightness and their likelihood to be lensed,
the bulk of the _Herschel_ population – and thus also the lenses – reside
at the lower flux densities (20 mJy _>_ _𝑆_ 500 _>_ 40 mJy). A thorough
test of the fidelity of a lens-selection method should thus focus on
these low flux-density sources.
In this paper, we report on the observation of 86 galaxies selected using a method based on a VIKING (+ KiDS)-based analysis


MNRAS **000**, 1–27 (2023)



from Bakx et al. (2020a). In Section 2, we describe the selection
method. Section 3 details the observations, and Section 4 describes
the implications of this survey on lenses within _Herschel_ samples.
We conclude in Section 5. Throughout this paper, we assume a flat
Λ-CDM cosmology with the best-fit parameters derived from the
_Planck_ results (Collaboration et al. 2018), which are Ω m = 0 _._ 315,
Ω Λ = 0 _._ 685 and _ℎ_ = 0 _._ 674.


**2** **LENS IDENTIFICATION AND SAMPLE SELECTION**


In this section, we describe the method for finding lenses through
combined near- and far-infrared surveys, as well as the selected galaxies for this pilot survey.


**2.1** **Lens identification**


The lens identifying method is based on finding a VIKING galaxy
which is statistically likely to be associated with a _Herschel_ source.
As a further requirement, the presumed foreground source should be
at a lower redshift than the estimated redshift of the submm source

– estimated from the sub-mm colours of the source (Pearson et al.
2013; Bakx et al. 2018) – and is therefore highly likely to be a lens
(Bakx et al. 2020a). The standard statistical way of finding associated
sources is by finding galaxies close enough to the _Herschel_ positions
that they are unlikely to be there by chance (Bourne et al. 2016).
Our new method relies on the fact that most high-redshift ( _𝑧>_ 2)
submillimetre galaxies are not bright enough to be detected on widearea optical and NIR surveys such as SDSS and VIKING (Wright
et al. 2019), and so any galaxy that is close to the _Herschel_ position
on these images could likely be the lens (González-Nuevo et al.
2017), although a subset of SMGs may not be NIR-faint (GonzálezNuevo et al. 2012). The statistical tool used for identifying lenses is
called the likelihood estimator (Sutherland & Saunders 1992). This

likelihood estimator calculates an individual so-called likelihood of

an association of a NIR source close to a _Herschel_ -source given the
magnitude distribution of the NIR magnitude and spatial offset. The
likelihood reflects how unlikely each NIR- _Herschel_ couple is through
a measure of how many similar fields one would need to see before
encountering a single one of these associations. The likelihood, _𝐿_, of
lensing candidates is often in excess of several hundreds or thousands,
and is calculated as follows:


_[𝑓]_ [(] _[𝑟]_ [)]
_𝐿_ = _[𝑞]_ [(] _[𝑚]_ [)] _._ (1)

_𝑛_ ( _𝑚_ )


In this equation, _𝑞_ ( _𝑚_ ) represents the probability distribution of
genuine counterparts at a magnitude _𝑚_, _𝑛_ ( _𝑚_ ) represents the background surface density distribution of unrelated objects (in units of
arcsec [−][2] ), and _𝑓_ ( _𝑟_ ) represents the distribution of offsets between
sub-mm and near-IR positions produced by both positional errors
between both catalogues and gravitational lensing offsets (in units of
arcsec [−][2] ; see Bakx et al. 2020a).
In order to arrive at a single probability – here called the reliability
( _𝑅_ _𝑗_ ) – the likelihoods of each nearby NIR source are added together,
and include the possibility of the foreground source being too faint
to be detected in the VIKING survey (i.e., _𝑄_ 0 = 0 _._ 82; Fleuren et al.
2012; Bourne et al. 2016; Bakx et al. 2020a):

_𝑅_ _𝑗_ = � _𝑖_ _[𝐿]_ _𝑖_ [+ (] _𝐿_ _𝑗_ [1][ −] _[𝑄]_ 0 [)] _[.]_ (2)


In this equation, the reliability of each potential match, _𝑗_, is calculated
from the sum of the likelihoods of all nearby matches ( [�] _𝑖_ _[𝐿]_ _𝑖_ [) and the]

possibility that the foreground source is too faint to be detected. Bakx
et al. (2020a) have found that the SDSS also misses about half the
lenses, so an essential part of our method is that the search for the lens
is carried out in the _𝐾_ _𝑆_ -band in the VIKING survey, where the lens
(often a massive ‘red-and-dead’ elliptical) is virtually always bright
enough to be detected (Bakx et al. 2020a). On top of this, unlike other
methods for finding associated sources, we calibrated our statistical
estimator on a sample of gravitationally-lensed galaxies: the _Herschel_
_Bright_ _Sources_ (HerBS; Bakx et al. 2018, 2020b). This resulted in
the insight that the angular distribution of lensed galaxies is not
simply described by a Gaussian distribution, but instead requires a
distribution that accounts for an additional offset due to galaxy-galaxy
and galaxy-cluster lenses. The likelihood estimator does introduce
biases in the types of lenses we can find. The VIKING survey is deep
enough to detect most lensing galaxies (M ∗ _>_ 10 [8] M ⊙ ). Meanwhile,
the radial probability distribution is non-zero out to ≈ 10 arcseconds,
allowing us to find most cases of galaxy-galaxy lensing ( _<_ 10 arcsec;
Amvrosiadis et al. 2018). We do note, however, that the method
becomes increasingly less sensitive towards larger offsets between
the lensed galaxy and the deflector.


**2.2** **The FLASH sample: Faint lenses found through Associated**
**Selection from Herschel**


This survey is based on the H-ATLAS 12-hour equatorial field (Eales
et al. 2010; Valiante et al. 2016), which has good coverage with the
VIKING NIR and the optical KIDS survey. This field contains 35 512
_Herschel_ sources. The radio NRAO VLA Sky Survey (NVSS) survey
was used to remove blazars from the sample. A total of 350 H-ATLAS
sources fall within 10 arcseconds of an NVSS source, i.e., within the
typical combined angular precision of _Herschel_ (∼ 2 arcsec) and
NVSS (∼ 7 arcsec). Here we note that this step could also remove
bright DSFGs in our sample, which is not an important drawback,
since we are mostly interested in the fainter DSFGs, and here choose
sample purity over completeness. The photometric redshifts of the
H-ATLAS sources is then estimated by fitting a modified blackbody SED to the 250, 350 and 500 _𝜇_ m fluxes (Pearson et al. 2013;
Bakx et al. 2018). Subsequently, we impose a redshift cut for all
H-ATLAS sources, demanding _𝑧_ phot _>_ 2 _._ 0. These sources were
then passed through the counterpart analysis of Bakx et al. (2020a),
which identifies counterparts on the VIKING _𝐾_ _𝑆_ -band images that
are likely to be statistically associated with the _Herschel_ sources.
This uses a standard likelihood estimator (Sutherland & Saunders
1992; Fleuren et al. 2012; Bourne et al. 2016; Bakx et al. 2020a),
which provides a probability for a VIKING counterpart to be genuine.
A total of 7 362 GAMA-12 _Herschel_ sources have nearby VIKING
counterparts, no nearby NVSS radio sources, and lie above _𝑧_ phot _>_ 2.
Wright et al. (2019) have used the nine photometric bands of VIKING
and KIDS to produce photometric redshifts and stellar masses for the
objects detected in the surveys. By comparing these redshift estimates
and their errors, in combination with the photometric redshifts for
the sub-mm sources and their errors (assuming Δ _𝑧_ = 0 _._ 13(1 + _𝑧_ );
Pearson et al. 2013), we identify the systems for which there was
only a 0.1 per cent chance (∼ 3 _._ 1 _𝜎_ ) that the _Herschel_ source and the
potential counterpart are actually at the same redshift, for a total of
6 823 sources. In order to test the evolution of the lensing probability
with _Herschel_ flux density, we identify the most likely sources to
be gravitationally-lensed across a wide 500 _𝜇_ m flux density range,
selecting towards the highest reliabilities within each 10 mJy flux
density region that can be observed in a single observation by ALMA.
In order to efficiently observe these sources, we require each source to
be within ten degrees from a single phase-centre to observe all targets



_Finding lenses in a FLASH_ 3


100


50


20


Lens Sample

VIKING sources

Parent sample


10

0 2 4 6
redshift


**Figure 1.** The photometric redshift distribution of the foreground ( _blue cir-_
_cles_ ) VIKING and background ( _red_ _squares_ ) _Herschel_ sources. The _𝑧>_ 2
_Herschel_ sources from the equatorial GAMA 12 field are indicated in _grey_
_points_ . We link the associated points together with a _blue_ _dashed_ _line_ . The
redshift difference between the sources provides confidence in being different
galaxies (or not the same galaxy) as the _Herschel_ sources.


within a minimum number of Scheduling Blocks. Above 40 mJy,
fewer sources could be found in a single field that would be reliable
candidates for gravitational lensing, and as a result most of the sources
have _𝑆_ 500 between 20 and 40 mJy. As a consequence of the dearth of
likely-lensed sources at the higher fluxes, several sources have standout properties such as large angular separations or lower reliabilities.
We list the catalogue in Table 1, and show the redshift against the
500 _𝜇_ m flux in Figure 1. The sources are sorted from lowest _𝑆_ 500 to
highest.


**2.3** **The statistics of the FLASH selection**


Although these sources are the most likely gravitationally-lensed
candidates with _𝑆_ 500 = 10 − 90 mJy, with very high individual
probabilities, the large parent sample implies that there is a possibility
for chance encounters. In an example as to why this is the case: even
if there were no true lensing candidates, the size of our sample
would by chance pick up sources as lensing candidates. Figure 2
shows a schematic overview of the FLASH source selection, starting
from a perfect understanding of lensed ( _𝑎_ ) and non-lensed sources
( _𝑏_ ). The photometric selection ( _𝑧_ phot _>_ 2) reduces the fraction of
lensed and non-lensed sources with _𝐹_ _𝑍𝐿_ and _𝐹_ _𝑍𝑁_, respectively. The
subsequent cross-identification and removal of sources that are likely
at the same redshift reduces the fraction by an additional _𝐹_ _𝐾𝐿_ and
_𝐹_ _𝐾𝑁_, respectively. The sources can then be placed in four different
categories according to a confusion matrix proportional to


true positives = _𝑊_ = _𝑎𝐹_ _𝑍𝐿_ _𝐹_ _𝐾𝐿_ _,_


false positives = _𝑋_ = _𝑏𝐹_ _𝑍𝑁_ _𝐹_ _𝐾𝑁_ _,_


false negatives = _𝑌_ = _𝑎_ (1 − _𝐹_ _𝑍𝐿_ _𝐹_ _𝐾𝐿_ ) _,_ and


true negatives = _𝑍_ = _𝑏_ (1 − _𝐹_ _𝑍𝑁_ _𝐹_ _𝐾𝑁_ ) _._


MNRAS **000**, 1–27 (2023)

4 _Tom Bakx et al._


**Figure** **2.** A schematic overview of the FLASH source selection provides
insight in the total number of expected lenses in the FLASH sample and
the total number of lenses in the _Herschel_ sample. True lenses and nonlenses are initially classified by a redshift cut ( _𝑧>_ 2), followed by the crossidentification analysis (Bakx et al. 2020a) and a 3 _._ 1 _𝜎_ redshift difference
between VIKING and _Herschel_ sources. The subsequent confusion matrix
contains a measure for the true positives, the additional false positives, and
the completeness of the FLASH method.


The objective of these ALMA observations is to identify the true
positive sources, _𝑊_, although it is not clear how many false positives
are included in the FLASH selection. The ALMA observations will

be able to identify the lens candidates from the sample, and provide
a measure of _𝑓_ ALMA = _𝑊_ /( _𝑊_ + _𝑋_ ). Rewriting this equation, we find


_𝑎_
_𝑓_ ALMA = (3)
_𝑎_ + _𝑄_ [−][1] _𝑏_ _[,]_


MNRAS **000**, 1–27 (2023)



with _𝑄_ a representative of the quality of our FLASH selection,


_𝑄_ = _[𝐹]_ _[𝑍𝐿]_ _[𝐹]_ _[𝐾𝐿]_ _._ (4)

_𝐹_ _𝑍𝑁_ _𝐹_ _𝐾𝑁_


This allows us to find a rough estimate for the number of lenses we can
expect to detect with these ALMA observations. The lensing fraction
of sources decreases dramatically with decreasing flux density, which
thus drives up the false-positive fraction at the lower fluxes. For
instance, the lensing fraction predicted from cosmological models
(Cai et al. 2013) suggest that only one to two per cent of _𝑧>_ 2 submm sources is lensed at _𝑆_ 500 = 30 mJy, i.e., _𝑎_ /( _𝑎_ + _𝑏_ ) = 0 _._ 01 − 0 _._ 02.
The selection effects of the cross-identification is roughly _𝐹_ _𝐾𝐿_ =
0 _._ 82 (Bakx et al. 2020a), under the assumption that there are no
systematic differences between the brighter lens samples (i.e., _𝑆_ 500 _>_
80 mJy) and the bulk of lenses in _Herschel_ . This is in line with a brief
comparison of the equatorial sources reported in both Negrello et al.
(2017) and Bakx et al. (2020a): for eight sources in the lensed sample
of Negrello et al. (2017), seven are strong lensing candidates in Bakx
et al. (2020a), or a _𝐹_ _𝐾𝐿_ [′] [=][ 0] _[.]_ [88] [±] [0] _[.]_ [12. The fraction of lower-redshift]
lenses excluded ( _𝑧<_ 2) can be estimated from the fraction of such
sources documented in Negrello et al. (2017). They report fifteen
out of 80 lens candidates to have photometric redshifts below 2, or
_𝐹_ _𝑍𝐿_ = 0 _._ 82. By comparing the photometric redshifts of the _Herschel_
catalogues (Valiante et al. 2016; Furlanetto et al. 2018), we find that
around 46 per cent of sources in a flux-limited ( _𝑆_ 500 _>_ 15 mJy)
sample lie below _𝑧<_ 2; i.e., _𝐹_ _𝑍𝑁_ = 0 _._ 54. The main uncertainty of
the method lies in our ability to remove false positives through the
cross-identification analysis (Bakx et al. 2020a). As a lower limit,
we can use the fact that _Herschel_ and VIKING sources are excluded

to be at the same redshift by _𝐹_ _𝐾𝑁_ _<_ 0 _._ 001, although there are no
direct measurements of _𝐹_ _𝐾𝑁_ possible without observations. For an
intrinsic lensing fraction of _𝑎_ /( _𝑎_ + _𝑏_ ) = 0 _._ 01, we can expect a high
lensing fraction of _𝑓_ ALMA = 0 _._ 9, and a _𝑄_ -value of 1250. We compare
the sources in our sample against the lensing fraction predicted from
cosmological models (Cai et al. 2013), and find a total of 82 out of
86 sources are likely lensed based on the above predictions.
The method further provides insight in the total number of lenses
in the _Herschel_ samples. The completeness of the sample, _𝐶_, is equal
to the number of lenses our method is able to identify among all true
lenses,


_𝑊_
_𝐶_ = _[𝐹]_ _[𝐾𝐿]_ _[𝐹]_ _[𝑍𝐿]_ _[.]_ (5)
_𝑊_ + _𝑌_ [=]


As a result, an initial estimation of the completeness of the FLASH
selection is around _𝐶_ ≈ 0 _._ 82 × 0 _._ 8175 ≈ 0 _._ 7 ± 0 _._ 1.

Table 1: FLASH catalogue


Name _Herschel_ Position _𝑆_ 250 _𝜇_ m _𝑆_ 350 _𝜇_ m _𝑆_ 500 _𝜇_ m _𝑧_ phot _,_ submm VIKING Position _𝜃_ z phot _,_ VIK _𝐾_ _𝑆_ LHR _𝑀_ ∗

[hms dms] mJy mJy mJy [hms dms] [”] mag AB [0 - 1] M ⊙
FLASH-1 12:14:36.2 -01:24:06.9 23.0 ± 5.9 32.4 ± 7.4 12.2 ± 7.7 2.08 12:14:36.2 -01:24:06.3 0.93 0 _._ 84 [+] − [0] 0 _[.]_ _._ [03] 04 18 _._ 87 ± 0 _._ 02 0.997 11.21
FLASH-2 11:36:31.9 +00:40:21.7 30.8 ± 7.5 42.5 ± 8.1 19.7 ± 8.7 2.18 11:36:31.9 +00:40:21.8 0.16 0 _._ 75 [+] − [0] 0 _[.]_ _._ [11] 05 20 _._ 63 ± 0 _._ 10 0.997 10.07
FLASH-3 11:46:51.9 -00:00:44.1 24.6 ± 6.1 18.4 ± 7.4 19.8 ± 7.8 2.18 11:46:51.9 -00:00:45.1 0.97 1 _._ 1 [+] − [0] 0 _[.]_ _._ [12] 05 20 _._ 26 ± 0 _._ 05 0.995 11.05
FLASH-4 11:54:08.8 -01:44:16.1 33.2 ± 7.4 34.5 ± 8.2 20.7 ± 8.7 2.01 11:54:08.8 -01:44:16.6 0.57 1 _._ 25 [+] − [0] 0 _[.]_ _._ [20] 13 20 _._ 75 ± 0 _._ 12 0.995 10.95
FLASH-5 12:21:23.7 +00:28:34.7 28.7 ± 7.3 33.9 ± 8.2 21.9 ± 8.8 2.32 12:21:23.6 +00:28:35.9 1.96 1 _._ 33 [+] − [0] 0 _[.]_ _._ [03] 03 18 _._ 94 ± 0 _._ 03 0.991 11.18
FLASH-6 12:16:56.5 -02:37:41.2 29.0 ± 7.3 39.1 ± 8.2 22.2 ± 8.5 2.36 12:16:56.5 -02:37:41.9 0.67 0 _._ 63 [+] − [0] 0 _[.]_ _._ [04] 05 20 _._ 60 ± 0 _._ 11 0.995 9.677
FLASH-7 11:59:32.4 +00:02:17.9 21.3 ± 5.7 32.7 ± 7.4 22.3 ± 7.7 2.91 11:59:32.4 +00:02:17.9 0.36 0 _._ 19 [+] − [0] 0 _[.]_ _._ [03] 04 20 _._ 24 ± 0 _._ 05 0.997 8.983
FLASH-8 12:19:11.4 -00:30:36.9 29.4 ± 7.3 38.4 ± 8.0 22.4 ± 8.5 2.34 12:19:11.4 -00:30:36.8 0.9 1 _._ 31 [+] − [0] 0 _[.]_ _._ [04] 04 19 _._ 86 ± 0 _._ 06 0.995 10.72
FLASH-9 12:15:14.0 -01:59:52.8 36.2 ± 7.0 39.9 ± 7.8 22.6 ± 8.2 2.04 12:15:14.0 -01:59:52.3 0.76 0 _._ 66 [+] − [0] 0 _[.]_ _._ [02] 04 18 _._ 76 ± 0 _._ 01 0.998 10.83
FLASH-10 11:45:49.3 +00:20:38.0 27.6 ± 6.5 20.3 ± 7.5 22.8 ± 7.7 2.27 11:45:49.3 +00:20:39.2 1.51 1 _._ 28 [+] − [0] 0 _[.]_ _._ [05] 08 20 _._ 60 ± 0 _._ 07 0.99 10.67
FLASH-11 11:34:08.3 +00:27:47.9 30.2 ± 7.5 25.3 ± 8.2 22.9 ± 9.3 2.14 11:34:08.3 +00:27:48.8 0.99 1 _._ 12 [+] − [0] 0 _[.]_ _._ [41] 02 19 _._ 85 ± 0 _._ 04 0.995 11.25
FLASH-12 11:39:05.7 -01:10:30.7 27.8 ± 7.5 33.2 ± 8.2 23.2 ± 8.6 2.44 11:39:05.6 -01:10:30.3 0.93 0 _._ 45 [+] − [0] 0 _[.]_ _._ [03] 04 19 _._ 08 ± 0 _._ 03 0.997 10.41
FLASH-13 12:01:18.9 -02:23:28.8 35.5 ± 7.2 35.6 ± 8.1 23.6 ± 8.7 2.06 12:01:18.9 -02:23:30.0 1.74 0 _._ 46 [+] − [0] 0 _[.]_ _._ [02] 03 18 _._ 19 ± 0 _._ 01 0.994 10.74
FLASH-14 12:17:00.0 -00:35:14.8 34.2 ± 7.4 29.8 ± 8.3 23.9 ± 8.9 2.04 12:17:00.0 -00:35:15.3 0.59 1 _._ 26 [+] − [0] 0 _[.]_ _._ [09] 10 19 _._ 83 ± 0 _._ 04 0.997 11.23
FLASH-15 11:59:30.8 -01:04:52.5 29.1 ± 6.4 29.0 ± 7.3 24.3 ± 7.6 2.4 11:59:30.8 -01:04:54.0 1.65 0 _._ 69 [+] − [0] 0 _[.]_ _._ [03] 03 18 _._ 78 ± 0 _._ 02 0.994 10.70
FLASH-16 12:19:34.2 +00:22:15.4 31.5 ± 7.4 21.4 ± 8.1 24.3 ± 8.6 2.07 12:19:34.2 +00:22:15.4 0.17 0 _._ 95 [+] − [0] 0 _[.]_ _._ [03] 04 18 _._ 67 ± 0 _._ 02 0.999 11.38
FLASH-17 11:36:41.7 -01:17:26.6 29.5 ± 7.3 34.3 ± 8.2 24.6 ± 8.4 2.43 11:36:41.8 -01:17:26.4 0.2 1 _._ 05 [+] − [0] 0 _[.]_ _._ [03] 05 19 _._ 51 ± 0 _._ 02 0.998 11.04
FLASH-18 11:44:18.6 +00:04:54.3 30.0 ± 6.5 28.0 ± 7.5 24.7 ± 7.7 2.35 11:44:18.5 +00:04:53.9 1.18 1 _._ 07 [+] − [0] 0 _[.]_ _._ [04] 06 19 _._ 60 ± 0 _._ 04 0.994 11.01
FLASH-19 11:56:00.4 -01:49:55.2 32.7 ± 7.5 31.9 ± 8.2 24.8 ± 8.6 2.23 11:56:00.4 -01:49:54.9 0.35 1 _._ 01 [+] − [0] 0 _[.]_ _._ [03] 05 19 _._ 28 ± 0 _._ 03 0.998 11.02
FLASH-20 12:02:08.7 -02:34:13.6 37.1 ± 7.2 37.9 ± 8.1 24.9 ± 8.6 2.08 12:02:08.7 -02:34:12.7 0.89 0 _._ 72 [+] − [0] 0 _[.]_ _._ [02] 04 18 _._ 87 ± 0 _._ 02 0.997 10.67
FLASH-21 12:14:25.6 -00:43:15.9 35.4 ± 6.5 39.0 ± 7.5 25.0 ± 7.7 2.18 12:14:25.6 -00:43:16.4 0.73 0 _._ 63 [+] − [0] 0 _[.]_ _._ [02] 31 20 _._ 45 ± 0 _._ 09 0.996 9.923
FLASH-22 11:50:34.9 -00:54:26.1 37.7 ± 7.4 37.8 ± 8.1 25.1 ± 8.5 2.06 11:50:35.0 -00:54:24.9 1.42 1 _._ 02 [+] − [0] 0 _[.]_ _._ [03] 04 18 _._ 98 ± 0 _._ 02 0.995 11.20
FLASH-23 11:57:23.2 +01:13:12.5 30.1 ± 7.3 26.8 ± 8.1 25.3 ± 8.6 2.38 11:57:23.2 +01:13:12.6 0.15 1 _._ 32 [+] − [0] 0 _[.]_ _._ [06] 07 20 _._ 20 ± 0 _._ 10 0.998 10.75
FLASH-24 11:56:49.2 +00:35:49.1 26.7 ± 6.4 23.4 ± 7.4 25.4 ± 7.6 2.66 11:56:49.2 +00:35:47.9 1.39 0 _._ 72 [+] − [0] 0 _[.]_ _._ [02] 04 19 _._ 55 ± 0 _._ 03 0.994 10.65
FLASH-25 11:50:55.9 -01:33:54.9 33.8 ± 7.3 22.3 ± 8.0 26.0 ± 8.6 2.04 11:50:56.0 -01:33:55.5 1.56 0 _._ 66 [+] − [0] 0 _[.]_ _._ [02] 04 19 _._ 11 ± 0 _._ 06 0.994 10.59
FLASH-26 11:46:26.8 -01:45:41.4 38.4 ± 6.5 34.9 ± 7.4 26.3 ± 7.8 2.04 11:46:26.7 -01:45:40.4 1.51 1 _._ 2 [+] − [0] 0 _[.]_ _._ [09] 10 20 _._ 01 ± 0 _._ 06 0.992 11.07
FLASH-27 11:53:05.8 -00:37:46.0 31.8 ± 7.4 35.4 ± 8.3 26.4 ± 8.8 2.42 11:53:05.7 -00:37:45.0 1.78 0 _._ 56 [+] − [0] 0 _[.]_ _._ [03] 04 17 _._ 98 ± 0 _._ 01 0.994 10.97
FLASH-28 11:48:36.3 +01:01:10.7 30.8 ± 7.3 23.5 ± 8.1 26.4 ± 8.7 2.36 11:48:36.4 +01:01:10.7 0.85 0 _._ 98 [+] − [0] 0 _[.]_ _._ [09] 08 20 _._ 79 ± 0 _._ 12 0.994 10.36
FLASH-29 12:04:29.4 -00:42:43.4 29.7 ± 7.1 33.7 ± 7.8 26.6 ± 8.2 2.55 12:04:29.4 -00:42:43.3 0.63 1 _._ 06 [+] − [0] 0 _[.]_ _._ [06] 06 19 _._ 88 ± 0 _._ 05 0.997 10.64
FLASH-30 12:14:41.5 +00:24:08.1 32.5 ± 7.3 34.1 ± 8.2 26.7 ± 8.8 2.38 12:14:41.6 +00:24:07.5 0.81 0 _._ 67 [+] − [0] 0 _[.]_ _._ [03] 03 18 _._ 47 ± 0 _._ 01 0.998 10.92
FLASH-31 12:01:37.1 -00:04:19.1 34.8 ± 7.3 41.1 ± 8.2 26.9 ± 8.7 2.33 12:01:37.1 -00:04:20.2 1.03 0 _._ 69 [+] − [0] 0 _[.]_ _._ [02] 04 19 _._ 29 ± 0 _._ 04 0.996 10.56
FLASH-32 11:59:37.8 -00:06:25.8 32.6 ± 6.5 35.5 ± 7.4 27.1 ± 7.7 2.42 11:59:37.9 -00:06:23.8 2.58 0 _._ 73 [+] − [0] 0 _[.]_ _._ [04] 06 20 _._ 45 ± 0 _._ 07 0.964 10.06
FLASH-33 12:01:28.9 -01:10:15.9 26.3 ± 6.3 24.8 ± 7.4 27.6 ± 7.7 2.91 12:01:28.9 -01:10:16.0 0.21 0 _._ 89 [+] − [0] 0 _[.]_ _._ [04] 04 19 _._ 28 ± 0 _._ 03 0.997 10.96
FLASH-34 12:25:09.9 -00:18:06.0 38.5 ± 7.3 35.8 ± 8.1 27.6 ± 8.6 2.12 12:25:09.9 -00:18:07.4 1.34 0 _._ 23 [+] − [0] 0 _[.]_ _._ [47] 02 20 _._ 59 ± 0 _._ 09 0.989 9.012
FLASH-35 12:06:08.8 -00:34:57.5 34.1 ± 7.0 36.1 ± 7.9 28.4 ± 8.3 2.42 12:06:08.7 -00:34:57.2 0.69 0 _._ 07 [+] − [0] 0 _[.]_ _._ [03] 03 20 _._ 31 ± 0 _._ 10 0.995 8.116
FLASH-36 11:54:37.3 +00:59:37.0 37.5 ± 7.3 37.0 ± 8.3 28.5 ± 8.9 2.23 11:54:37.7 +00:59:33.9 6.41 0 _._ 54 [+] − [0] 0 _[.]_ _._ [04] 04 18 _._ 79 ± 0 _._ 01 0.961 10.63
FLASH-37 12:17:23.4 -02:06:00.3 43.3 ± 7.2 41.4 ± 8.2 28.5 ± 8.7 2.02 12:17:23.4 -02:05:59.2 1.06 1 _._ 06 [+] − [0] 0 _[.]_ _._ [06] 05 19 _._ 71 ± 0 _._ 03 0.995 10.66
_Continued on next page..._

Table 1 – _continued from previous page_

Name _Herschel_ Position _𝑆_ 250 _𝜇_ m _𝑆_ 350 _𝜇_ m _𝑆_ 500 _𝜇_ m _𝑧_ phot _,_ submm VIKING Position _𝜃_ z phot _,_ VIK _𝐾_ _𝑆_ Rel. log 10 _𝑀_ ∗

[hms dms] mJy mJy mJy [hms dms] [”] mag AB [0 - 1] log 10 _𝑀_ ⊙
FLASH-38 11:49:25.7 -02:07:21.2 36.5 ± 7.2 40.9 ± 8.3 28.5 ± 8.7 2.33 11:49:25.7 -02:07:23.4 2.14 0 _._ 64 [+] − [0] 0 _[.]_ _._ [03] 05 20 _._ 18 ± 0 _._ 09 0.982 10.00
FLASH-39 12:19:50.5 +00:33:35.5 39.4 ± 7.4 39.9 ± 8.2 29.0 ± 8.9 2.2 12:19:50.5 +00:33:41.6 6.08 0 _._ 59 [+] − [0] 0 _[.]_ _._ [02] 04 19 _._ 01 ± 0 _._ 03 0.945 10.51
FLASH-40 11:59:41.3 +00:02:41.7 39.3 ± 6.5 38.5 ± 7.4 29.0 ± 7.7 2.19 11:59:41.2 +00:02:41.2 0.8 1 _._ 19 [+] − [0] 0 _[.]_ _._ [05] 14 20 _._ 59 ± 0 _._ 07 0.98 10.34
FLASH-41 12:13:48.9 -01:03:11.4 43.0 ± 6.5 40.5 ± 7.4 29.4 ± 7.7 2.05 12:13:48.8 -01:03:13.8 2.65 1 _._ 16 [+] − [0] 0 _[.]_ _._ [04] 06 19 _._ 70 ± 0 _._ 06 0.975 10.80
FLASH-42 11:59:10.0 -01:20:58.1 31.1 ± 6.6 27.0 ± 7.5 30.1 ± 7.8 2.71 11:59:10.0 -01:20:57.3 0.92 0 _._ 64 [+] − [0] 0 _[.]_ _._ [03] 03 19 _._ 04 ± 0 _._ 04 0.997 10.47
FLASH-43 12:23:05.3 -01:13:10.2 40.2 ± 7.4 43.6 ± 8.1 30.3 ± 8.6 2.26 12:23:05.2 -01:13:12.1 2.27 0 _._ 17 [+] − [0] 0 _[.]_ _._ [03] 03 19 _._ 35 ± 0 _._ 04 0.987 9.236
FLASH-44 12:00:47.6 -00:40:19.6 11.1 ± 4.7 23.1 ± 7.4 31.3 ± 7.7 5.56 12:00:47.6 -00:40:18.8 1.03 0 _._ 75 [+] − [0] 0 _[.]_ _._ [04] 04 19 _._ 18 ± 0 _._ 04 0.996 10.85
FLASH-45 11:36:53.6 +01:16:32.9 32.2 ± 7.2 24.8 ± 8.2 32.0 ± 8.8 2.76 11:36:53.6 +01:16:33.7 0.82 1 _._ 23 [+] − [0] 0 _[.]_ _._ [02] 04 19 _._ 19 ± 0 _._ 01 0.997 10.99
FLASH-46 12:14:12.1 -00:52:13.6 34.6 ± 6.5 33.7 ± 7.5 33.0 ± 7.7 2.67 12:14:12.2 -00:52:13.7 1.17 0 _._ 44 [+] − [0] 0 _[.]_ _._ [02] 04 18 _._ 56 ± 0 _._ 01 0.969 10.57
FLASH-47 12:20:19.6 -00:39:12.3 50.8 ± 7.3 53.3 ± 8.2 34.1 ± 8.5 2.1 12:20:19.5 -00:39:11.7 1.29 0 _._ 25 [+] − [0] 0 _[.]_ _._ [05] 06 20 _._ 68 ± 0 _._ 11 0.992 8.972
FLASH-48 12:01:15.4 -01:27:22.0 14.6 ± 5.0 20.5 ± 7.4 34.2 ± 7.8 5.1 12:01:15.5 -01:27:23.0 1.53 0 _._ 96 [+] − [0] 0 _[.]_ _._ [03] 04 19 _._ 38 ± 0 _._ 03 0.995 11.19
FLASH-49 11:58:05.5 -01:55:47.6 43.2 ± 6.8 36.2 ± 7.6 34.3 ± 7.9 2.25 11:58:05.4 -01:55:47.9 1.45 0 _._ 95 [+] − [0] 0 _[.]_ _._ [03] 04 19 _._ 23 ± 0 _._ 02 0.986 10.78
FLASH-50 12:05:31.3 -00:37:00.5 39.1 ± 7.0 43.8 ± 7.8 34.7 ± 8.3 2.54 12:05:31.3 -00:37:01.1 1.1 0 _._ 37 [+] − [0] 0 _[.]_ _._ [17] 03 19 _._ 34 ± 0 _._ 03 0.996 10.29
FLASH-51 12:01:41.9 -02:20:06.2 41.2 ± 7.4 32.5 ± 8.2 34.8 ± 8.5 2.37 12:01:41.9 -02:20:04.6 1.85 0 _._ 69 [+] − [0] 0 _[.]_ _._ [03] 04 18 _._ 41 ± 0 _._ 02 0.994 11.03
FLASH-52 11:50:09.4 -00:36:51.9 34.7 ± 7.4 40.2 ± 8.3 35.1 ± 8.8 2.8 11:50:09.4 -00:36:51.8 0.42 1 _._ 43 [+] − [0] 0 _[.]_ _._ [09] 08 20 _._ 24 ± 0 _._ 10 0.997 11.02
FLASH-53 11:49:21.6 -01:03:02.1 40.6 ± 7.1 41.8 ± 8.0 35.2 ± 8.4 2.48 11:49:21.6 -01:03:01.9 0.23 0 _._ 53 [+] − [0] 0 _[.]_ _._ [10] 06 20 _._ 20 ± 0 _._ 08 0.997 10.14
FLASH-54 12:08:06.2 +00:45:10.3 27.5 ± 6.5 38.9 ± 7.4 35.8 ± 7.7 3.38 12:08:06.1 +00:45:10.3 1.05 0 _._ 87 [+] − [0] 0 _[.]_ _._ [04] 04 19 _._ 54 ± 0 _._ 05 0.996 10.95
FLASH-55 11:55:00.7 -00:07:22.0 22.4 ± 6.8 31.8 ± 8.3 36.3 ± 8.7 4.04 11:55:00.6 -00:07:21.2 1.26 0 _._ 26 [+] − [0] 0 _[.]_ _._ [03] 03 19 _._ 51 ± 0 _._ 05 0.994 9.235
FLASH-56 12:16:54.3 -01:27:29.9 24.8 ± 7.1 40.9 ± 8.2 36.6 ± 8.8 3.68 12:16:54.4 -01:27:31.1 1.35 0 _._ 7 [+] − [0] 0 _[.]_ _._ [03] 03 19 _._ 93 ± 0 _._ 04 0.994 10.19
FLASH-57 11:46:10.1 -00:50:28.4 39.4 ± 6.5 41.7 ± 7.4 37.0 ± 7.8 2.64 11:46:10.0 -00:50:27.4 1.67 1 _._ 43 [+] − [0] 0 _[.]_ _._ [13] 06 19 _._ 93 ± 0 _._ 06 0.991 10.99
FLASH-58 11:43:59.8 -00:16:00.1 36.0 ± 6.5 41.0 ± 7.5 37.7 ± 7.8 2.88 11:43:59.9 -00:16:01.1 1.4 0 _._ 44 [+] − [0] 0 _[.]_ _._ [04] 03 18 _._ 46 ± 0 _._ 03 0.996 10.72
FLASH-59 12:22:11.4 -01:41:53.8 37.6 ± 7.3 39.4 ± 8.1 37.8 ± 8.5 2.8 12:22:11.4 -01:41:53.9 1.19 0 _._ 2 [+] − [0] 0 _[.]_ _._ [03] 04 20 _._ 70 ± 0 _._ 12 0.989 9.216
FLASH-60 11:50:55.0 -00:44:06.1 52.7 ± 7.5 51.6 ± 8.1 38.7 ± 8.6 2.18 11:50:54.9 -00:44:06.6 1.09 0 _._ 33 [+] − [0] 0 _[.]_ _._ [05] 05 20 _._ 31 ± 0 _._ 09 0.994 9.426
FLASH-61 12:14:27.1 -02:24:46.6 24.7 ± 7.0 25.3 ± 8.1 39.0 ± 8.5 4.09 12:14:27.1 -02:24:45.5 1.23 0 _._ 59 [+] − [0] 0 _[.]_ _._ [03] 05 19 _._ 98 ± 0 _._ 06 0.994 10.15
FLASH-62 12:14:02.6 -01:43:07.4 42.7 ± 6.5 57.1 ± 7.4 39.0 ± 7.6 2.61 12:14:02.6 -01:43:04.9 2.83 0 _._ 92 [+] − [0] 0 _[.]_ _._ [37] 07 20 _._ 87 ± 0 _._ 19 0.944 10.35
FLASH-63 11:44:39.9 +00:54:32.4 48.2 ± 6.5 35.4 ± 7.4 39.4 ± 7.7 2.24 11:44:39.9 +00:54:30.9 1.61 0 _._ 93 [+] − [0] 0 _[.]_ _._ [06] 10 20 _._ 31 ± 0 _._ 07 0.99 10.63
FLASH-64 11:58:50.0 -00:57:08.3 57.4 ± 6.5 59.6 ± 7.4 39.5 ± 7.6 2.12 11:58:49.8 -00:57:08.3 3.97 0 _._ 47 [+] − [0] 0 _[.]_ _._ [02] 03 18 _._ 28 ± 0 _._ 01 0.938 10.71
FLASH-65 12:10:58.0 -00:44:38.3 50.8 ± 6.5 63.0 ± 7.5 39.7 ± 7.8 2.36 12:10:58.0 -00:44:40.0 1.91 0 _._ 71 [+] − [0] 0 _[.]_ _._ [03] 06 19 _._ 42 ± 0 _._ 04 0.991 10.66
FLASH-66 12:13:58.5 +01:10:47.6 37.1 ± 7.2 46.0 ± 8.1 40.9 ± 8.9 3.0 12:13:58.5 +01:10:48.3 1.2 1 _._ 14 [+] − [0] 0 _[.]_ _._ [04] 06 19 _._ 71 ± 0 _._ 04 0.994 10.89
FLASH-67 12:24:46.0 -01:52:39.9 36.8 ± 7.3 40.4 ± 8.3 41.9 ± 8.7 3.11 12:24:46.0 -01:52:39.7 0.2 0 _._ 07 [+] − [0] 0 _[.]_ _._ [02] 04 20 _._ 86 ± 0 _._ 13 0.997 7.860
FLASH-68 12:18:20.7 +01:13:46.5 64.6 ± 7.4 58.5 ± 8.1 44.3 ± 8.8 2.04 12:18:20.7 +01:13:48.5 2.07 1 _._ 2 [+] − [0] 0 _[.]_ _._ [05] 09 19 _._ 76 ± 0 _._ 03 0.988 11.15
FLASH-69 11:44:40.4 +00:26:49.2 59.1 ± 6.4 54.4 ± 7.4 45.1 ± 7.7 2.21 11:44:40.4 +00:26:50.4 1.14 0 _._ 61 [+] − [0] 0 _[.]_ _._ [03] 06 20 _._ 47 ± 0 _._ 12 0.992 10.02
FLASH-70 12:13:57.7 +00:09:11.0 38.9 ± 7.5 41.9 ± 8.2 45.7 ± 8.7 3.21 12:13:57.7 +00:09:11.0 0.15 1 _._ 34 [+] − [0] 0 _[.]_ _._ [19] 11 20 _._ 94 ± 0 _._ 11 0.985 10.48
FLASH-71 12:24:07.6 -00:33:31.8 52.9 ± 7.4 42.8 ± 8.2 45.9 ± 8.4 2.44 12:24:07.6 -00:33:32.6 1.09 1 _._ 08 [+] − [0] 0 _[.]_ _._ [14] 09 20 _._ 46 ± 0 _._ 08 0.993 10.77
FLASH-72 12:06:32.2 -00:33:11.2 58.0 ± 7.0 58.5 ± 7.8 47.8 ± 8.2 2.38 12:06:32.1 -00:33:12.4 2.23 0 _._ 49 [+] − [0] 0 _[.]_ _._ [03] 06 19 _._ 84 ± 0 _._ 08 0.983 9.985
FLASH-73 12:05:53.3 -01:51:18.0 67.7 ± 7.3 83.9 ± 8.3 51.4 ± 8.6 2.32 12:05:53.4 -01:51:18.0 0.42 0 _._ 6 [+] − [0] 0 _[.]_ _._ [03] 04 18 _._ 24 ± 0 _._ 01 0.985 10.92
FLASH-74 11:39:32.4 -01:54:58.5 74.4 ± 7.4 63.3 ± 8.1 52.4 ± 8.8 2.04 11:39:32.4 -01:54:58.8 0.4 0 _._ 98 [+] − [0] 0 _[.]_ _._ [05] 04 19 _._ 88 ± 0 _._ 04 0.998 10.84
FLASH-75 12:07:00.2 -01:13:03.3 59.1 ± 7.5 54.0 ± 8.2 52.6 ± 8.9 2.51 12:07:00.2 -01:13:03.2 0.13 0 _._ 63 [+] − [0] 0 _[.]_ _._ [02] 03 18 _._ 45 ± 0 _._ 01 0.999 10.72
_Continued on next page..._

Table 1 – _continued from previous page_

Name _Herschel_ Position _𝑆_ 250 _𝜇_ m _𝑆_ 350 _𝜇_ m _𝑆_ 500 _𝜇_ m _𝑧_ phot _,_ submm VIKING Position _𝜃_ z phot _,_ VIK _𝐾_ _𝑆_ Rel. log 10 _𝑀_ ∗

[hms dms] mJy mJy mJy [hms dms] [”] mag AB [0 - 1] log 10 _𝑀_ ⊙
FLASH-76 12:02:23.8 +01:03:17.3 73.0 ± 7.4 69.1 ± 8.1 52.6 ± 8.6 2.14 12:02:23.8 +01:03:17.5 0.18 1 _._ 03 [+] − [0] 0 _[.]_ _._ [10] 08 20 _._ 44 ± 0 _._ 10 0.998 10.28
FLASH-77 12:05:43.1 -00:38:33.1 75.9 ± 7.1 82.8 ± 8.0 55.5 ± 8.6 2.23 12:05:42.9 -00:38:34.3 3.07 0 _._ 7 [+] − [0] 0 _[.]_ _._ [06] 06 19 _._ 55 ± 0 _._ 05 0.955 10.78
FLASH-78 11:39:01.2 -02:14:12.1 51.2 ± 7.4 61.4 ± 8.1 55.5 ± 8.7 2.96 11:39:01.1 -02:14:11.6 1.66 1 _._ 07 [+] − [0] 0 _[.]_ _._ [12] 07 20 _._ 20 ± 0 _._ 07 0.99 10.89
FLASH-79 11:45:15.4 -00:08:44.9 46.6 ± 6.5 57.7 ± 7.5 56.4 ± 7.7 3.23 11:45:15.3 -00:08:42.3 3.02 0 _._ 67 [+] − [0] 0 _[.]_ _._ [24] 09 20 _._ 76 ± 0 _._ 13 0.812 10.24
FLASH-80 11:38:16.0 -01:31:18.1 60.1 ± 7.4 74.8 ± 8.0 60.1 ± 8.5 2.77 11:38:16.1 -01:31:20.5 3.11 1 _._ 2 [+] − [0] 0 _[.]_ _._ [07] 10 20 _._ 45 ± 0 _._ 08 0.945 10.76
FLASH-81 11:57:14.8 -00:28:41.9 84.2 ± 7.3 88.1 ± 8.1 62.1 ± 8.7 2.22 11:57:14.8 -00:28:40.8 1.45 0 _._ 95 [+] − [0] 0 _[.]_ _._ [04] 05 19 _._ 91 ± 0 _._ 05 0.993 10.85
FLASH-82 11:52:51.5 -01:52:20.0 91.4 ± 7.3 93.7 ± 8.1 62.7 ± 8.5 2.11 11:52:51.4 -01:52:19.1 2.56 1 _._ 28 [+] − [0] 0 _[.]_ _._ [05] 06 20 _._ 41 ± 0 _._ 07 0.978 10.76
FLASH-83 11:44:04.4 +00:38:49.9 96.8 ± 6.6 94.7 ± 7.5 69.3 ± 7.7 2.14 11:44:04.4 +00:38:43.8 6.14 1 _._ 04 [+] − [0] 0 _[.]_ _._ [06] 03 18 _._ 42 ± 0 _._ 01 0.954 11.43
FLASH-84 11:36:16.6 +00:48:54.7 90.6 ± 7.3 99.2 ± 8.1 71.7 ± 8.7 2.34 11:36:17.0 +00:48:51.7 6.39 0 _._ 55 [+] − [0] 0 _[.]_ _._ [04] 03 19 _._ 50 ± 0 _._ 05 0.944 10.34
FLASH-85 11:37:39.2 -02:44:43.5 63.2 ± 7.4 85.8 ± 8.2 73.2 ± 8.7 3.09 11:37:39.1 -02:44:45.0 2.23 0 _._ 57 [+] − [0] 0 _[.]_ _._ [03] 05 18 _._ 65 ± 0 _._ 01 0.99 10.78
FLASH-86 11:54:33.7 +00:50:42.3 53.9 ± 7.4 85.8 ± 8.1 83.9 ± 8.6 3.85 11:54:33.7 +00:50:42.1 0.51 0 _._ 69 [+] − [0] 0 _[.]_ _._ [04] 06 20 _._ 26 ± 0 _._ 13 0.997 10.57

**Notes:** Col. 1: Source name, sorted from lowest 500 _𝜇_ m flux to highest. Col. 2: RA and DEC positions in hms and dms units, respectively. Col. 3 - 5: The _Herschel_
photometry Col. 6: Photometric redshift of the _Herschel_ source based on the fitting of the modified black-body template from Pearson et al. (2013). Typical errors on this
fit are on the order of 0 _._ 13(1 + _𝑧_ ). Col. 7: The position of the VIKING-identified source from the catalogues described in Wright et al. (2019) Col. 8: The angular offset
in units of arcseconds between the _Herschel_ and VIKING source. Col. 9: The photometric redshift of the VIKING source based on both VISTA and KiDS photometry
best-fit (Wright et al. 2019). Col. 10: The AB-magnitude in the _𝐾_ _𝑆_ -band photometry. Col. 11: The reliability (i.e., the probability) of the _Herschel_ and VIKING sources
to be associated. Note that this does not account for the inclusion of false positives in a large-area survey. Col. 12: The stellar mass estimate of the VIKING source
identified from the KIDS and VISTA photometry, as described in Wright et al. (2019). This table is available in machine-readable form in the supplementary material.

8 _Tom Bakx et al._


Figure 3 shows the distribution of properties of the FLASH
sources. Unlike previous studies of gravitational lenses that focus
on _𝑆_ 500 _>_ 100 mJy (Negrello et al. 2017, or equivalent fluxes at
longer wavelengths; Vieira et al. 2013; Spilker et al. 2016; Harrington et al. 2021; Kamieneski et al. 2023), this survey selects relatively
low 500 _𝜇_ m fluxes. The reliability, or the statistical association of the
_Herschel_ sources to VIKING galaxies, of these sources is high due
to a combination of low angular separation and bright foreground
galaxy selection. The angular separation is on the order of the typical
astrometric uncertainties (e.g., Valiante et al. 2016). In fact, most
association probabilities of FLASH sources are above the 99 [th] percentile. The foreground VIKING sources have information from both
VISTA (Z, Y, J, H, and K _𝑆_ ) and from the KiDS survey (u, g, r, and i).
Spectral fitting (Wright et al. 2019) provides a stellar mass estimate
of the foreground objects, which suggests massive ( _𝑀_ ∗ _>_ 10 [10] _𝑀_ ⊙ )
galaxy systems at lower redshifts. As previously mentioned, the sample is drawn from a relatively small patch of sky to facilitate efficient
ALMA observations. As a consequence, each distribution appears
to have one to three outliers source with a large separations (≈ 6";
FLASH-39, -83 and -84), a low reliability ( _𝑅_ ≈ 0 _._ 8; FLASH-79) or
a low stellar mass ( _𝑀_ ∗ ≈ 10 [7] _[.]_ [8] _𝑀_ ⊙ ; FLASH-67), although each such
source is different, and do not suggest impurity of the sample.


**3** **ALMA OBSERVATIONS, REDUCTION AND RESULTS**


**3.1** **ALMA observations and reduction**


We observe using Band 7 continuum observations to test whether
these sources are actually lensed. The observation depth is based on
a Cycle 2 ALMA program of 16 bright _Herschel_ sources that showed
that even short (2 minute) continuum observations were enough to
reveal the lensed structure with enough signal-to-noise and resolution
for a full lensing reconstruction (Amvrosiadis et al. 2018; Dye et al.
2018). In this study (2019.1.01784.S; P.I. Bakx), we have used the
same resolution (∼ 0 _._ 15 arcsec) but scaled the integration times to
allow for the fainter flux densities of the sources by 50 per cent
deeper observations (see Table 2). The quasars J1058+0133 and
J1256-0547 were used as bandpass calibrators, and quasars J12170029 and J1135-0428 were used as complex gain calibrators.
Data reduction was performed following the standard procedure
and using the ALMA pipeline. Then, we use CASA for imaging the
_uv_ -visibilities using Briggs weighting with a robust parameter of 2.0
(to maximize the depth of the observations at the expense of slightly
increasing the final synthesized beam size). The resulting beam size
is 0 [′′] _._ 18 by 0 [′′] _._ 14 with a beam angle of −71 degrees at a continuum
depth of 72 _𝜇_ Jy/beam.
In order to test the effect of resolved observations and to facili
tate aperture extraction, we also generate images with a tapering of
0.5 arcseconds. The resulting continuum maps have a beam size of
0 [′′] _._ 60 by 0 [′′] _._ 56 at the same beam angle of −71 degrees at a continuum
depth of 137 _𝜇_ Jy/beam.


**3.2** **ALMA photometry**


The source fluxes are extracted from the tapered image using the
CASA IMFIT routine. For each source, the routine is repeated until
no obvious sources exist in the residual image ( _>_ 3 _𝜎_ ). The resulting
positions and fluxes are shown in Table 3. For significantly sources
or sources where the lensing causes the emission to be spread across
multiple components, we mention the individual extracted positions,


MNRAS **000**, 1–27 (2023)



20


10


0

20 40 60 80

S 500 [mJy]


20


10


0

0 2 4 6 8

Angular separation [arcsec]


60


40


20


0

0.80 0.85 0.90 0.95 1.00

Reliability


20


10


0

8 9 10 11

log 10 Stellar mass [M ]


**Figure 3.** The FLASH sources are selected with _faint_ 500 _𝜇_ m flux densities,
relative to the bulk of the lenses found by _Herschel_ and other lensing surveys
(i.e., the expected or observed _𝑆_ 500 of _Planck_, SPT, ACT are _>_ 100 mJy).
They are found close to bright VIKING sources, with most _Herschel_ and
VIKING sources only 2 arcseconds removed from on the sky, within the
typical astrometric uncertainties. As a result of the close location on the sky,
the FLASH sources have high reliabilities (i.e., association probabilities) for
each _Herschel_ and VIKING-association, with most association probabilities
above the 99 [th] percentile. The foreground VIKING sources have information
from both VISTA (Z, Y, J, H, and K _𝑆_ ) and from the KiDS survey (u, g, r, and
i). Spectral fitting (Wright et al. 2019) provides a stellar mass estimate of the
foreground objects, which suggests massive ( _𝑀_ ∗ _>_ 10 [10] _𝑀_ ⊙ ) galaxy systems
at lower redshifts. Interestingly, each distribution appears to have one to three
_straggling_ sources with a large separations (≈ 6"; FLASH-39, -83 and -84), a
low reliability ( _𝑅_ ≈ 0 _._ 8; FLASH-79) or a low stellar mass ( _𝑀_ ∗ ≈ 10 [7] _[.]_ [8] _𝑀_ ⊙ ;
FLASH-67), although each such source is different, and it does not suggest
impurity of the sample.

_Finding lenses in a FLASH_ 9


**Table 2.** Parameters of the ALMA observations


UTC start time Baseline length N ant Frequency T int PWV

[YYYY-MM-DD hh:mm:ss] [m] [GHz] [min] [mm]


2021-05-10 03:08:31 14 – 2492 44 343.484 49.0 0.96

2021-05-16 03:21:37 14 – 2517 47 343.484 48.8 0.96

2021-05-17 00:05:58 14 – 2517 47 343.484 48.9 0.65

2021-05-17 01:55:18 14 – 2517 48 343.484 49.0 0.64

2021-05-17 02:43:09 14 – 2517 48 343.484 21.8 0.45

2021-05-18 00:13:21 14 – 2517 49 343.484 42.3 0.62

2021-05-18 04:03:52 14 – 2517 49 343.484 42.3 0.39


as well as the combined flux of the source. We indicate these sources

with italics.

The resulting images are shown in Figure 4. These images, whose
identification and FLASH-number are listed at the top, show the
VIKING image in the background, with foreground contours from the
high-resolution (white contours) and tapered (solid black contours).
Inset images provide the high-resolution (0.15 arcsec resolution, red
contours) for sources where zoom-ins are necessary. The images
are centered on the VIKING position (which is also the ALMA
phase center), and the orange cross indicates the _Herschel_ position
from Valiante et al. (2016). The red squares indicate the individual
positions of the extracted fluxes.


MNRAS **000**, 1–27 (2023)

10 _Tom Bakx et al._


**Figure 4.** The VIKING images of the FLASH sources are shown in the _blue_ background, with their FLASH-number and identification listed in the top of the
figure. Contours in the central panels show either the robust parameter = 2 maps ( _white contours_ ; beam ≈ 0 _._ 15 arcsec) or the tapered data ( _black contours_ ; beam
≈ 0 _._ 55 arcsec). The contours are drawn at 3 _,_ 5 _,_ 8 _,_ 10 and 20 _𝜎_ . The beams are shown in the lower-left of the panels, and the images are scaled to include all
ALMA-identified galaxies. The angular scale is shown in the lower-right of each figure in units of arcseconds. The extraction positions of the sources in Table 3
are indicated with _red boxes_, and where applicable, we provide insets of each source using red contours on the scale to capture the entire emission. In order to
boost the fidelity of these insets, we lower the contour levels to 2 _,_ 3 _,_ 5 _,_ 10 and 20 _𝜎_ . The images are centered on the VIKING-position, and the _orange cross_
indicates the _Herschel_ position. The FLASH numbering is sorted by increasing 500 _𝜇_ m flux, _𝑆_ 500 .


MNRAS **000**, 1–27 (2023)

**Figure 4.** _Continued._



_Finding lenses in a FLASH_ 11


MNRAS **000**, 1–27 (2023)

12 _Tom Bakx et al._


MNRAS **000**, 1–27 (2023)



**Figure 4.** _Continued._

**Figure 4.** _Continued._



_Finding lenses in a FLASH_ 13


MNRAS **000**, 1–27 (2023)

14 _Tom Bakx et al._


MNRAS **000**, 1–27 (2023)



**Figure 4.** _Continued._

_Finding lenses in a FLASH_ 15


Table 3: ALMA observations catalogue


Name Lens? ALMA Position _𝑆_ 1 _._ 1mm _𝜃_ ALMA _,_ VIK _𝜃_ ALMA _,𝐻𝑒𝑟𝑠𝑐ℎ𝑒𝑙_

[hms dms] mJy [”] [”]
FLASH-1NE C-grade 12:14:36.9 -01:24:03.0 2.14 ± 0.66 (3.3 _𝜎_ ) 10.0 10.9
FLASH-1NW ... 12:14:36.7 -01:24:11.7 1.17 ± 0.4 (2.9 _𝜎_ ) 9.1 9.4
FLASH-2S C-grade 11:36:31.5 +00:40:22.4 6.81 ± 0.3 (22.4 _𝜎_ ) 4.7 4.6
FLASH-2NW ... 11:36:32.3 +00:40:14.5 2.1 ± 0.7 (3.0 _𝜎_ ) 9.7 9.8
FLASH-3 A-grade 11:46:51.9 -00:00:45.0 0.96 ± 0.19 (5.0 _𝜎_ ) 0.3 1.0
FLASH-4E B-grade 11:54:08.9 -01:44:12.8 2.13 ± 0.32 (6.7 _𝜎_ ) 3.9 3.3
FLASH-4C ... 11:54:08.8 -01:44:16.6 0.67 ± 0.19 (3.5 _𝜎_ ) 0.4 0.5
FLASH-4S ... 11:54:08.3 -01:44:14.3 1.72 ± 0.58 (3.0 _𝜎_ ) 8.2 7.9
FLASH-5E C-grade 12:21:23.8 +00:28:41.2 1.83 ± 0.4 (4.6 _𝜎_ ) 6.2 6.7
FLASH-5W ... 12:21:23.3 +00:28:28.2 1.53 ± 0.57 (2.7 _𝜎_ ) 8.9 8.9
FLASH-6 C-grade 12:16:56.6 -02:37:42.2 0.49 ± 0.28 (1.8 _𝜎_ ) 1.7 2.0
FLASH-7W C-grade 11:59:32.4 +00:02:14.0 2.28 ± 0.25 (9.1 _𝜎_ ) 4.0 3.9
FLASH-7SW ... 11:59:32.2 +00:02:13.3 1.66 ± 0.53 (3.1 _𝜎_ ) 5.8 5.5
FLASH-8C B-grade 12:19:11.4 -00:30:36.8 4.01 ± 0.32 (12.7 _𝜎_ ) 0.1 0.8
FLASH-8W ... 12:19:11.2 -00:30:44.4 1.03 ± 0.48 (2.2 _𝜎_ ) 8.2 7.8
FLASH-9W B-grade 12:15:14.0 -01:59:57.6 1.44 ± 0.28 (5.1 _𝜎_ ) 5.3 4.8
FLASH-9C ... 12:15:14.0 -01:59:52.6 1.16 ± 0.37 (3.1 _𝜎_ ) 0.4 0.9
FLASH-10 B-grade 11:45:49.3 +00:20:39.3 1.05 ± 0.28 (3.7 _𝜎_ ) 0.1 1.6
FLASH-11 B-grade 11:34:08.3 +00:27:48.8 1.1 ± 0.34 (3.3 _𝜎_ ) 0.2 1.1
FLASH-12 A-grade 11:39:05.7 -01:10:30.0 3.63 ± 0.23 (15.5 _𝜎_ ) 1.9 1.2
_FLASH-13_ A-grade 3.68 ± 0.31 (11.78 _𝜎_ )
FLASH-13E ... 12:01:18.9 -02:23:28.9 2.4 ± 0.21 (11.5 _𝜎_ ) 1.1 0.9
FLASH-13N ... 12:01:18.9 -02:23:30.6 0.98 ± 0.21 (4.6 _𝜎_ ) 0.8 1.9
FLASH-13SW ... 12:01:19.0 -02:23:29.7 0.3 ± 0.09 (3.2 _𝜎_ ) 0.9 2.3
FLASH-14 A-grade 12:17:00.0 -00:35:15.4 1.7 ± 0.3 (5.6 _𝜎_ ) 0.4 0.7
FLASH-15 C-grade 11:59:31.4 -01:04:51.4 5.46 ± 0.73 (7.4 _𝜎_ ) 9.8 8.8
FLASH-16 B-grade 12:19:34.2 +00:22:15.3 0.71 ± 0.19 (3.8 _𝜎_ ) 0.1 0.1
FLASH-17SW B-grade 11:36:41.3 -01:17:33.0 2.29 ± 0.52 (4.4 _𝜎_ ) 10.0 9.8
FLASH-17C ... 11:36:41.7 -01:17:26.4 1.41 ± 0.32 (4.3 _𝜎_ ) 0.2 0.2
FLASH-18 C-grade 11:44:18.7 +00:04:58.0 7.18 ± 0.32 (22.2 _𝜎_ ) 4.8 4.0
FLASH-19 B-grade 11:56:00.4 -01:49:54.8 0.46 ± 0.21 (2.2 _𝜎_ ) 0.4 0.8
FLASH-20 A-grade 12:02:08.7 -02:34:14.4 0.31 ± 0.16 (1.9 _𝜎_ ) 1.6 0.8
_FLASH-21_ A-grade 3.87 ± 0.29 (13.29 _𝜎_ )
FLASH-21C ... 12:14:25.5 -00:43:16.9 2.77 ± 0.22 (12.8 _𝜎_ ) 0.7 1.4
FLASH-21N ... 12:14:25.7 -00:43:16.3 1.1 ± 0.19 (5.6 _𝜎_ ) 1.5 1.1
FLASH-22SW B-grade 11:50:34.8 -00:54:24.0 3.41 ± 0.36 (9.5 _𝜎_ ) 2.7 2.8
FLASH-22S ... 11:50:34.7 -00:54:25.2 2.35 ± 0.26 (9.1 _𝜎_ ) 4.9 4.2
FLASH-23C A-grade 11:57:23.2 +01:13:12.7 1.92 ± 0.38 (5.0 _𝜎_ ) 0.1 0.2
FLASH-23S ... 11:57:22.6 +01:13:09.9 0.57 ± 0.22 (2.6 _𝜎_ ) 8.5 8.4
FLASH-24 C-grade 11:56:49.7 +00:35:41.4 2.78 ± 0.62 (4.4 _𝜎_ ) 9.5 9.9
FLASH-25 C-grade 11:50:55.6 -01:33:58.1 1.41 ± 0.48 (3.0 _𝜎_ ) 7.0 6.0
FLASH-26E A-grade 11:46:26.5 -01:45:29.5 5.64 ± 0.86 (6.6 _𝜎_ ) 11.4 12.7
FLASH-26C ... 11:46:26.7 -01:45:40.6 1.56 ± 0.36 (4.4 _𝜎_ ) 0.2 1.4
FLASH-26NW ... 11:46:27.0 -01:45:45.4 0.9 ± 0.25 (3.6 _𝜎_ ) 6.6 5.1
_FLASH-27_ A-grade 1.74 ± 0.41 (4.27 _𝜎_ )
FLASH-27E ... 11:53:05.7 -00:37:44.0 0.68 ± 0.2 (3.3 _𝜎_ ) 1.0 2.3
FLASH-27N ... 11:53:05.7 -00:37:45.5 0.5 ± 0.2 (2.5 _𝜎_ ) 0.7 2.0
FLASH-27SW ... 11:53:05.8 -00:37:44.8 0.56 ± 0.29 (1.9 _𝜎_ ) 0.8 1.3
FLASH-28 A-grade 11:48:36.4 +01:01:10.7 1.74 ± 0.21 (8.4 _𝜎_ ) 0.3 0.6
FLASH-29E C-grade 12:04:29.2 -00:42:48.9 1.01 ± 0.3 (3.4 _𝜎_ ) 6.3 6.5
FLASH-29W ... 12:04:29.7 -00:42:36.9 1.07 ± 0.34 (3.2 _𝜎_ ) 7.9 7.6
FLASH-29C ... 12:04:29.5 -00:42:42.4 0.92 ± 0.33 (2.8 _𝜎_ ) 2.1 1.6
FLASH-30NW A-grade 12:14:41.3 +00:24:12.1 2.1 ± 0.58 (3.7 _𝜎_ ) 5.8 5.0
FLASH-30SE ... 12:14:41.8 +00:24:04.3 1.34 ± 0.37 (3.6 _𝜎_ ) 4.5 5.4
FLASH-31 B-grade 12:01:37.3 -00:04:19.8 0.82 ± 0.35 (2.3 _𝜎_ ) 2.2 2.3
FLASH-32 C-grade 11:59:37.8 -00:06:26.6 9.21 ± 0.26 (36.0 _𝜎_ ) 3.3 0.8
_Continued on next page_


MNRAS **000**, 1–27 (2023)

16 _Tom Bakx et al._


Table 3 – _continued from previous page_


Name Lens? ALMA Position _𝑆_ 1 _._ 1mm _𝜃_ ALMA _,_ VIK _𝜃_ ALMA _,𝐻𝑒𝑟𝑠𝑐ℎ𝑒𝑙_

[hms dms] mJy [”] [”]
FLASH-33W C-grade 12:01:28.6 -01:10:12.3 2.0 ± 0.28 (7.1 _𝜎_ ) 5.6 5.4
FLASH-33SE ... 12:01:28.9 -01:10:24.4 3.77 ± 0.77 (4.9 _𝜎_ ) 8.4 8.5
FLASH-33C ... 12:01:28.7 -01:10:16.1 1.35 ± 0.48 (2.8 _𝜎_ ) 2.7 2.6
FLASH-34 A-grade 12:25:10.2 -00:18:05.8 0.89 ± 0.27 (3.2 _𝜎_ ) 4.5 4.1
FLASH-35S B-grade 12:06:08.5 -00:34:57.4 4.9 ± 0.23 (20.9 _𝜎_ ) 3.3 3.9
FLASH-35N ... 12:06:09.5 -00:34:52.9 5.99 ± 1.01 (6.0 _𝜎_ ) 12.4 12.0
FLASH-36SE C-grade 11:54:37.1 +00:59:39.4 2.78 ± 0.67 (4.2 _𝜎_ ) 9.7 3.4
FLASH-36W ... 11:54:37.7 +00:59:24.7 1.88 ± 0.67 (2.8 _𝜎_ ) 9.2 13.6
FLASH-36N ... 11:54:38.2 +00:59:35.3 0.67 ± 0.26 (2.6 _𝜎_ ) 7.9 13.5
FLASH-37 A-grade 12:17:23.4 -02:05:59.9 10.42 ± 0.25 (41.4 _𝜎_ ) 1.0 0.8
FLASH-38W B-grade 11:49:25.9 -02:07:29.0 4.33 ± 0.34 (12.7 _𝜎_ ) 6.4 8.4
FLASH-38SE ... 11:49:25.5 -02:07:16.5 3.15 ± 0.39 (8.1 _𝜎_ ) 7.7 5.8
FLASH-38S ... 11:49:25.3 -02:07:20.8 1.14 ± 0.35 (3.3 _𝜎_ ) 6.9 6.3
FLASH-39SW C-grade 12:19:50.3 +00:33:33.4 3.63 ± 0.48 (7.6 _𝜎_ ) 8.8 4.4
FLASH-39W ... 12:19:50.4 +00:33:34.2 0.98 ± 0.33 (3.0 _𝜎_ ) 7.5 2.3
_FLASH-40_ A-grade 5.37 ± 0.55 (9.79 _𝜎_ )
FLASH-40CS ... 11:59:41.2 +00:02:41.2 1.77 ± 0.19 (9.3 _𝜎_ ) 0.8 1.5
FLASH-40NE ... 11:59:41.5 +00:02:45.6 1.47 ± 0.31 (4.7 _𝜎_ ) 6.1 5.3
FLASH-40CN ... 11:59:41.3 +00:02:41.0 0.9 ± 0.21 (4.3 _𝜎_ ) 0.9 0.7
FLASH-40SE ... 11:59:40.9 +00:02:49.2 1.23 ± 0.35 (3.5 _𝜎_ ) 9.6 9.5
FLASH-41 B-grade 12:13:48.8 -01:03:13.9 1.6 ± 0.37 (4.3 _𝜎_ ) 0.1 2.7
FLASH-42S A-grade 11:59:09.9 -01:20:57.7 2.4 ± 0.27 (9.1 _𝜎_ ) 1.0 1.3
FLASH-42N ... 11:59:10.4 -01:20:57.2 1.15 ± 0.24 (4.7 _𝜎_ ) 5.6 5.3
FLASH-43 B-grade 12:23:05.3 -01:13:07.9 5.54 ± 0.3 (18.5 _𝜎_ ) 4.2 2.3
FLASH-44S B-grade 12:00:47.4 -00:40:19.8 7.55 ± 0.28 (27.2 _𝜎_ ) 2.7 3.1
FLASH-44NW ... 12:00:48.1 -00:40:26.9 7.04 ± 0.78 (9.1 _𝜎_ ) 11.0 10.0
FLASH-45S A-grade 11:36:53.7 +01:16:34.9 0.78 ± 0.28 (2.8 _𝜎_ ) 1.7 2.3
FLASH-45NE ... 11:36:53.6 +01:16:33.6 1.0 ± 0.37 (2.7 _𝜎_ ) 0.3 0.8
FLASH-46 A-grade 12:14:12.1 -00:52:14.6 2.57 ± 0.23 (11.0 _𝜎_ ) 1.4 1.0
_FLASH-47_ A-grade 5.7 ± 0.31 (18.66 _𝜎_ )
FLASH-47SW ... 12:20:19.4 -00:39:14.0 3.88 ± 0.22 (17.2 _𝜎_ ) 2.8 3.3
FLASH-47E ... 12:20:19.6 -00:39:11.5 1.82 ± 0.21 (8.8 _𝜎_ ) 0.2 1.3
_FLASH-48_ A-grade 7.69 ± 0.44 (17.6 _𝜎_ )
FLASH-48NW ... 12:01:15.6 -01:27:24.9 6.11 ± 0.34 (18.0 _𝜎_ ) 2.5 4.0
FLASH-48SW ... 12:01:15.5 -01:27:22.7 1.58 ± 0.27 (5.7 _𝜎_ ) 0.5 1.0
FLASH-49 C-grade 11:58:06.0 -01:55:53.1 6.39 ± 0.72 (8.8 _𝜎_ ) 10.7 9.7
FLASH-50 B-grade 12:05:31.5 -00:37:04.3 6.47 ± 0.26 (25.0 _𝜎_ ) 4.8 4.6
FLASH-51 C-grade 12:01:42.1 -02:20:12.0 6.27 ± 0.38 (16.4 _𝜎_ ) 7.8 6.8
FLASH-52C A-grade 11:50:09.4 -00:36:52.1 4.12 ± 0.3 (13.7 _𝜎_ ) 0.3 0.4
FLASH-52E ... 11:50:09.6 -00:36:45.6 1.69 ± 0.54 (3.1 _𝜎_ ) 6.6 6.9
FLASH-53SE B-grade 11:49:21.5 -01:02:59.7 4.92 ± 0.21 (23.3 _𝜎_ ) 2.9 3.1
FLASH-53S ... 11:49:21.1 -01:03:03.1 5.86 ± 0.4 (14.8 _𝜎_ ) 7.2 7.1
FLASH-54N A-grade 12:08:06.2 +00:45:09.6 7.24 ± 0.29 (25.0 _𝜎_ ) 1.8 0.9
FLASH-54SE ... 12:08:05.7 +00:45:16.9 1.46 ± 0.33 (4.5 _𝜎_ ) 8.6 9.3
FLASH-55W C-grade 11:55:00.5 -00:07:29.2 9.34 ± 0.39 (23.9 _𝜎_ ) 8.4 7.9
FLASH-55NW ... 11:55:00.9 -00:07:24.9 2.44 ± 0.28 (8.9 _𝜎_ ) 6.0 4.7
FLASH-55S ... 11:55:00.4 -00:07:21.2 0.68 ± 0.24 (2.9 _𝜎_ ) 4.3 5.3
FLASH-56E C-grade 12:16:54.5 -01:27:24.6 7.29 ± 0.3 (24.3 _𝜎_ ) 6.7 5.7
FLASH-56S ... 12:16:53.8 -01:27:27.4 1.09 ± 0.39 (2.8 _𝜎_ ) 9.5 8.5
FLASH-56N ... 12:16:54.6 -01:27:29.7 0.95 ± 0.38 (2.5 _𝜎_ ) 4.1 4.5
FLASH-57 A-grade 11:46:10.0 -00:50:27.3 2.67 ± 0.48 (5.6 _𝜎_ ) 0.1 1.7
_FLASH-58_ A-grade 6.47 ± 0.68 (9.48 _𝜎_ )
FLASH-58S ... 11:43:59.9 -00:16:00.7 4.07 ± 0.46 (8.8 _𝜎_ ) 0.8 0.6
FLASH-58N ... 11:44:00.0 -00:16:01.2 2.41 ± 0.5 (4.8 _𝜎_ ) 0.2 1.6
FLASH-59SW C-grade 12:22:11.2 -01:41:57.3 3.33 ± 0.24 (14.1 _𝜎_ ) 4.3 5.2
FLASH-59NE ... 12:22:11.7 -01:41:44.2 4.0 ± 0.89 (4.5 _𝜎_ ) 11.4 10.7
FLASH-60N A-grade 11:50:55.1 -00:44:06.0 7.51 ± 0.25 (30.0 _𝜎_ ) 2.8 1.8
_Continued on next page_


MNRAS **000**, 1–27 (2023)

_Finding lenses in a FLASH_ 17


Table 3 – _continued from previous page_


Name Lens? ALMA Position _𝑆_ 1 _._ 1mm _𝜃_ ALMA _,_ VIK _𝜃_ ALMA _,𝐻𝑒𝑟𝑠𝑐ℎ𝑒𝑙_

[hms dms] mJy [”] [”]
FLASH-60C ... 11:50:55.0 -00:44:06.9 2.31 ± 0.18 (12.7 _𝜎_ ) 0.9 0.9
FLASH-61 A-grade 12:14:27.0 -02:24:47.1 6.89 ± 0.23 (29.9 _𝜎_ ) 2.3 2.1
FLASH-62C B-grade 12:14:02.6 -01:43:04.9 5.0 ± 0.3 (16.9 _𝜎_ ) 0.1 2.8
FLASH-62SW ... 12:14:02.4 -01:43:06.9 1.27 ± 0.21 (6.0 _𝜎_ ) 3.3 4.0
FLASH-63 A-grade 11:44:40.0 +00:54:30.9 1.64 ± 0.19 (8.4 _𝜎_ ) 1.4 1.7
FLASH-64NE B-grade 11:58:50.1 -00:57:02.0 1.57 ± 0.47 (3.3 _𝜎_ ) 8.5 6.5
FLASH-64E ... 11:58:49.8 -00:57:07.4 0.84 ± 0.33 (2.5 _𝜎_ ) 1.1 3.7
FLASH-64W ... 11:58:49.6 -00:57:13.4 0.56 ± 0.23 (2.4 _𝜎_ ) 5.4 7.7
FLASH-64NW ... 11:58:49.9 -00:57:11.1 0.33 ± 0.16 (2.0 _𝜎_ ) 3.8 3.1
_FLASH-65_ A-grade 9.05 ± 0.47 (19.36 _𝜎_ )
FLASH-65E ... 12:10:58.0 -00:44:38.6 5.53 ± 0.27 (20.8 _𝜎_ ) 1.4 0.5
FLASH-65SE ... 12:10:57.9 -00:44:38.4 3.52 ± 0.38 (9.1 _𝜎_ ) 1.6 1.1
FLASH-66 C-grade 12:13:58.2 +01:10:43.9 7.54 ± 0.3 (25.1 _𝜎_ ) 6.6 5.4
FLASH-67NE B-grade 12:24:46.4 -01:52:36.6 6.11 ± 0.34 (17.8 _𝜎_ ) 7.5 7.4
FLASH-67NW ... 12:24:46.3 -01:52:50.4 7.14 ± 1.02 (7.0 _𝜎_ ) 12.0 11.8
FLASH-67N ... 12:24:46.2 -01:52:39.0 1.77 ± 0.27 (6.5 _𝜎_ ) 3.9 3.9
FLASH-68 A-grade 12:18:20.7 +01:13:48.6 1.91 ± 0.2 (9.7 _𝜎_ ) 0.3 2.3
FLASH-69S A-grade 11:44:40.3 +00:26:50.5 2.05 ± 0.2 (10.2 _𝜎_ ) 1.7 2.1
FLASH-69NW ... 11:44:40.7 +00:26:45.6 1.01 ± 0.27 (3.7 _𝜎_ ) 6.5 5.8
FLASH-70SE A-grade 12:13:57.4 +00:09:16.1 1.49 ± 0.27 (5.4 _𝜎_ ) 6.2 6.1
FLASH-70N ... 12:13:57.9 +00:09:09.6 1.35 ± 0.28 (4.9 _𝜎_ ) 3.8 3.9
FLASH-70C ... 12:13:57.7 +00:09:10.8 0.76 ± 0.23 (3.3 _𝜎_ ) 0.3 0.4
FLASH-71N A-grade 12:24:07.7 -00:33:31.4 7.09 ± 0.23 (31.1 _𝜎_ ) 2.6 1.6
FLASH-71NE ... 12:24:08.2 -00:33:26.2 3.02 ± 0.8 (3.8 _𝜎_ ) 11.1 10.0
FLASH-72NE B-grade 12:06:32.3 -00:33:11.1 3.93 ± 0.24 (16.1 _𝜎_ ) 3.0 0.8
FLASH-72E ... 12:06:32.1 -00:33:05.9 2.63 ± 0.47 (5.6 _𝜎_ ) 6.5 5.5
FLASH-72W ... 12:06:32.1 -00:33:11.0 0.95 ± 0.25 (3.8 _𝜎_ ) 1.5 1.5
_FLASH-73_ A-grade 14.26 ± 0.63 (22.49 _𝜎_ )
FLASH-73N ... 12:05:53.4 -01:51:18.0 7.71 ± 0.27 (28.4 _𝜎_ ) 1.1 1.5
FLASH-73S ... 12:05:53.3 -01:51:18.1 3.85 ± 0.47 (8.2 _𝜎_ ) 0.3 0.2
FLASH-73E ... 12:05:53.4 -01:51:17.3 2.7 ± 0.33 (8.2 _𝜎_ ) 0.9 1.2
FLASH-74C B-grade 11:39:32.4 -01:54:58.9 2.88 ± 0.19 (14.8 _𝜎_ ) 0.1 0.5
FLASH-74SW ... 11:39:32.3 -01:55:02.1 0.77 ± 0.24 (3.2 _𝜎_ ) 3.8 4.2
FLASH-75NE A-grade 12:07:00.1 -01:13:01.2 3.98 ± 0.22 (18.0 _𝜎_ ) 2.9 2.8
FLASH-75S ... 12:07:00.0 -01:13:03.6 2.05 ± 0.38 (5.4 _𝜎_ ) 3.0 2.9
_FLASH-76_ A-grade 11.54 ± 0.42 (27.52 _𝜎_ )
FLASH-76W ... 12:02:23.8 +01:03:14.3 8.68 ± 0.37 (23.7 _𝜎_ ) 3.2 3.1
FLASH-76E ... 12:02:23.8 +01:03:18.0 2.86 ± 0.2 (14.0 _𝜎_ ) 0.6 0.8
FLASH-77N C-grade 12:05:43.1 -00:38:33.6 8.34 ± 0.24 (34.3 _𝜎_ ) 3.4 0.7
FLASH-77NW ... 12:05:43.2 -00:38:36.4 3.92 ± 0.43 (9.0 _𝜎_ ) 5.2 3.8
FLASH-78E A-grade 11:39:01.1 -02:14:10.4 6.55 ± 0.23 (28.5 _𝜎_ ) 1.4 1.9
FLASH-78NW ... 11:39:01.3 -02:14:17.7 1.82 ± 0.55 (3.3 _𝜎_ ) 7.1 5.9
FLASH-78C ... 11:39:01.1 -02:14:11.6 1.05 ± 0.37 (2.9 _𝜎_ ) 0.2 1.8
FLASH-79NE C-grade 11:45:15.6 -00:08:37.9 9.59 ± 0.41 (23.2 _𝜎_ ) 6.3 7.8
FLASH-79W ... 11:45:15.3 -00:08:48.5 0.89 ± 0.25 (3.5 _𝜎_ ) 6.3 4.0
FLASH-79E ... 11:45:15.5 -00:08:37.3 1.29 ± 0.49 (2.6 _𝜎_ ) 5.6 7.7
_FLASH-80_ A-grade 13.24 ± 0.45 (29.51 _𝜎_ )
FLASH-80N ... 11:38:16.3 -01:31:20.7 10.88 ± 0.25 (44.3 _𝜎_ ) 2.2 4.9
FLASH-80S ... 11:38:16.1 -01:31:20.5 2.36 ± 0.38 (6.3 _𝜎_ ) 0.3 2.9
FLASH-81SW B-grade 11:57:14.7 -00:28:43.3 10.32 ± 0.23 (44.0 _𝜎_ ) 3.5 2.0
FLASH-81N ... 11:57:15.2 -00:28:41.6 4.19 ± 0.35 (12.0 _𝜎_ ) 5.6 6.5
FLASH-82NW A-grade 11:52:51.4 -01:52:20.3 7.86 ± 0.26 (29.9 _𝜎_ ) 1.3 2.0
FLASH-82N ... 11:52:51.6 -01:52:21.6 3.07 ± 0.44 (6.9 _𝜎_ ) 4.8 2.4
FLASH-83NE A-grade 11:44:04.8 +00:38:46.8 3.94 ± 0.36 (11.1 _𝜎_ ) 6.3 6.2
FLASH-83C ... 11:44:04.4 +00:38:43.9 1.0 ± 0.27 (3.7 _𝜎_ ) 0.3 6.1
FLASH-83N ... 11:44:05.1 +00:38:48.3 3.03 ± 0.9 (3.4 _𝜎_ ) 11.6 10.5
FLASH-84S C-grade 11:36:16.5 +00:48:52.1 12.66 ± 0.34 (36.9 _𝜎_ ) 6.3 2.7
_Continued on next page_


MNRAS **000**, 1–27 (2023)

18 _Tom Bakx et al._


Table 3 – _continued from previous page_


Name Lens? ALMA Position _𝑆_ 1 _._ 1mm _𝜃_ ALMA _,_ VIK _𝜃_ ALMA _,𝐻𝑒𝑟𝑠𝑐ℎ𝑒𝑙_

[hms dms] mJy [”] [”]
FLASH-84SE ... 11:36:16.6 +00:48:54.0 3.01 ± 0.3 (9.9 _𝜎_ ) 6.2 0.6
_FLASH-85_ A-grade 35.19 ± 0.99 (35.41 _𝜎_ )
FLASH-85NW ... 11:37:39.2 -02:44:46.0 18.64 ± 0.65 (28.8 _𝜎_ ) 1.2 2.7
FLASH-85N ... 11:37:39.2 -02:44:46.0 7.39 ± 0.51 (14.5 _𝜎_ ) 1.5 2.6
FLASH-85NW ... 11:37:39.2 -02:44:45.4 2.97 ± 0.24 (12.5 _𝜎_ ) 1.2 2.0
FLASH-85SE ... 11:37:39.1 -02:44:44.7 4.44 ± 0.39 (11.4 _𝜎_ ) 0.6 2.5
FLASH-85W ... 11:37:39.2 -02:44:44.9 1.76 ± 0.32 (5.5 _𝜎_ ) 1.2 1.5
_FLASH-86_ A-grade 39.77 ± 0.52 (77.12 _𝜎_ )
FLASH-86N ... 11:54:33.7 +00:50:42.0 30.82 ± 0.39 (79.0 _𝜎_ ) 0.2 0.7
FLASH-86S ... 11:54:33.6 +00:50:41.8 8.94 ± 0.34 (26.5 _𝜎_ ) 0.9 0.6

**Notes:** Col. 1: Source name. We identify the fluxes of the individually-extracted fluxes (red boxes in Figure 4), and for extended or lensed
sources, we provide the total flux and weighted signal-to-noise ratios of the lensed components in the sources indicated with italics. The
additional letters in the naming convention refer to N, E (left in figures), S, W (right in figures) for North, East, South and West. C refers to
Centre, for sources closer to the centre than others. Col. 2: The identification of the source, as discussed in Section 4.1. Col. 3: The RA and
DEC position of the ALMA positions in units of hms and dms respectively. We do not provide the position for the combined lensed sources, as
these do not represent any physical position. Col. 4: The 1.1 mm flux density followed by the signal-to-noise ratio of the detection in brackets.
Col. 5: The angular offset between the ALMA and VIKING position in units of arcseconds. Col. 5: The angular offset between the ALMA and
_Herschel_ position in units of arcseconds. This table is available in machine-readable form in the supplementary material.


MNRAS **000**, 1–27 (2023)

0.1 1 10
Observed VIKING separation [arcsec]


**Figure** **5.** The observed ALMA flux densities ( _solid_ _blue_ _circles_ for single
sources; _red_ _squares_ for composite sources, where composite sources are
shown in italics in Table 3) are shown against the angular offset from the
phase centre, i.e., the VIKING source position. The _solid_ _black_ _line_ _and_
_fill_ indicate the ALMA primary beam sensitivity down to 3 _𝜎_ . The typical
flux densities of the sources are higher than the observation depth. Although
most sources are detected away from the edge of the ALMA beam, we cannot
guarantee that sources could lie outside of the Field-of-View. Similarly, several
sources scatter below the detection threshold, and particularly since lensed
sources could be extended, we cannot guarantee the sample observations are
complete.


**3.3** **ALMA observation completion**


Several sources do not have bright emission in their reduced images.
Notably FLASH-6 ( _𝑆_ 500 = 22 _._ 2 mJy) does not show any emission
in the ALMA imaging. Here we explore the reasons for these nondetections. The ALMA observations were centered on the VIKING

position, in order to accurately probe the lensing structure expected
around the foreground lens. The field-of-view (FoV) of ALMA is
limited to ∼ 15 arcseconds, however, and there exists the possibility
of sources falling outside of the primary beam – although this is increasingly unlikely to be due to galaxy-galaxy lensing (Amvrosiadis
et al. 2018).
Figure 5 shows the observed offset between the ALMA-identified
sources and the VIKING central source. The black line shows the

3 _𝜎_ detection limit based on the 0.5 arcsecond tapered image used for
source extraction. The majority of sources have detected emission
within the FoV of ALMA, and importantly, the typical source flux
lies a factor of two or more above the detection limit. However,
the individual sources approach the end of the FoV of the Band 7
observations by ALMA, even though the selection towards large
values of the reliability means that these sources have a small distance
between the VIKING and _Herschel_ -estimated position for the source.
Even a shift of five arcseconds – common across the sample – could
push sources into a less sensitive part of the primary beam, and result
in non-detections. The fact that lenses can be extended across the

source further increases the detection threshold, further complicates
this matter. On the whole, we have a large detection fraction for
most sources, although current observations cannot exclude faint,



_Finding lenses in a FLASH_ 19


**Table 4.** The classification of FLASH sources


S 500 [mJy] Nr. A-grade B-grade C-grade


10 - 25 21 29 % 33 % 38 %

25 - 35 30 43 % 30 % 27 %

35 - 45 17 53 % 24 % 24 %

45 - 55 8 75 % 0 % 25 %

55 - 65 6 50 % 33 % 17 %

65 - 75 3 67 % 33 % 0 %

75 - 85 1 100 % 0 % 0 %


**Notes:** Col. 1: The 500 _𝜇_ m flux bin. Col. 2: The number of sources contributing to each flux bin. Col. 3: The expected number of lenses based on the
false-positive considerations in the Sample selection (Section 2). Col. 4 – 6:

The distribution of sources in each bin.


extended, or cluster lenses to be completely accounted for in the
ALMA observations.


**4** **LENSING IN** _**HERSCHEL**_ **SAMPLES**


In this section we discuss the lensing nature of FLASH sources based
on the ALMA images. Here, we differentiate obvious strong lenses,
investigate more difficult sources which could be lensed or not lensed,
and explore the effects of selection biases in the sample. Finally, we
zoom out to the complete perspective of lenses to be found in the
_Herschel_ samples with the FLASH method.


**4.1** **Lensing nature of FLASH sources**


The ALMA observations reveal a large spread in the observed morphologies (Figure 4). Some _Herschel_ sources are easy to visually
identify as gravitational lenses, showing morphological features such
as arcs, multiple images and even near-complete Einstein rings.
Other sources have multiple nearby counterparts, making interpretation of their lensing nature more difficult. These systems could
be chance alignments, a situation where the _Herschel_ source and
VIKING galaxy are the same source, or cases of cluster lensing,
where foreground clusters provide a speckled ALMA field with multiple sources, as well as the possibility of (proto-)cluster environments where overdensities in the cosmic web are seen through an
excess of ALMA sources. We summarize our knowledge on the lensing nature of each source by a grade ranging from A (secure lens
identification) via B (some evidence for lensing) to C (no indications
for lensing, or the lack thereof).

In brief, we identify A-grade lenses as sources where robust
ALMA emission shows lensing features such as arcs or rings, or
where the ALMA emission is between 0.2 to 2 arcseconds removed

from the central VIKING galaxy. B-grade sources consist of sources
with emission either removed further than 2 arcseconds – but mor
phologically appears to be consistent with lensing – or is within
0.2 arcseconds of the VIKING galaxy – where we cannot exclude the
ALMA observation of the VIKING galaxy. Sources without any of
these features are categorized as C-grade. Below, the lens identification criteria are discussed in detail, and we summarize the results in

Table 4.


_4.1.1_ _Identifying lenses in FLASH_


We investigate the lensing features of sources visually, identifying
A-grade lenses by their extended or arced ALMA emission close to


MNRAS **000**, 1–27 (2023)

20 _Tom Bakx et al._


the central VIKING sources (i.e., _<_ 2 arcsec). These sources were
selected with a small spatial separation between the _Herschel_ and
VIKING positions. The combined source-to-source angular separation of _Herschel_ and VIKING sources, particularly at the lowersignificance levels, is on the order of one or two arcseconds. For
sources without obvious lensing features such as arcs or rings (e.g.,
FLASH-3), we interpret ALMA emission offset from the central
VIKING source by more than 0.2 but less than 2 arcseconds as
indications of strong gravitational lensing. At these separations,
the emission is likely not originating from the near-infrared emitting VIKING galaxy given the accurate photometry of ALMA and
VIKING ( _<_ 0 _._ 1 arcsec; Wright et al. 2019), but instead is lensed
by the foreground source. On the other hand, if there exists bright
VIKING emission at the position of the ALMA emission, we exclude
the source as a lensing candidate, and award the source a B-grade.
These provide us with a first-pass estimate of the number of A-grade
lens candidates in the FLASH sample, for a total of 37 sources.
Since the sensitivity of our observations is not guaranteed to detect
extended lensing features for all sources, we measure the curveof-growth of ALMA emission through multiple annuli at different
widths (0.15, 0.3 and 0.5). We calculate the signal-to-noise ratio for
all pixels _𝑖_ within the annulus using the following equation,


[︁]


[︁]



detect carbon monoxide (CO), atomic Carbon ([C i]) or atomic lines
of galaxies in the sample, see Figure 7. For most of these solutions,
the uncertainty in the photometric redshift is too large to use just
a single line for a robust redshift identification, particularly since
several of these sources were extracted at low flux densities.

Using the tapered data cubes, we initially inspect the galaxies at
the extraction position. These tapered data cubes are created by effectively down-weighing the long baselines of ALMA. This allows us to
extract positions and fluxes with higher fidelity, since tapering results
in higher-significance detections at a moderate cost in resolution for
resolved sources. After a visual inspection of the spectra, we perform per-source based aperture photometry to extract the emission
line across the source.

In total, five sources show line emission at their ALMA position.
We note that these are tentative spectroscopic redshift solutions, and
require confirmation.
**FLASH-28** ( _A-grade_ ) has a line feature at 348 GHz, with an extension at 348.3 GHz. The source is identified as a gravitational lens,
with an expected VIKING-lens redshift of _𝑧_ = 0 _._ 9 to 1.07. The background photometric redshift is _𝑧_ _𝑠𝑢𝑏_ = 2 _._ 36, and a potential redshift
solution could be _𝑧_ = 2 _._ 312 from CO(10-9).
**FLASH-33C** ( _C-grade_ ) has a line feature at 350.2 GHz. This source
could be associated with the foreground VIKING source, and while

[︁] thephotometric redshift betweenbackground redshift ( _𝑧_ _𝑠𝑢𝑏_ _𝑧_ == 20 _.._ 91),85 to 0.93. The source is offsetthe VIKING system has a

by 2.7 arcseconds, and is likely not associated to the foreground system. The curve-of-growth analysis finds a ringed system surrounding
FLASH-33, on top of the multiple components identified by direct
imaging. It is thus likely that it is a background source at _𝑧_ spec = 2 _._ 62
for CO(10–9) for example.
**FLASH-49** ( _A-grade_ ) has a line feature at 351 GHz. This ALMAdetected source, with _𝑧_ _𝑠𝑢𝑏_ = 2 _._ 25, is likely unrelated to the foreground VIKING source between _𝑧_ = 0 _._ 91 to 0.98 given its spatial

[︁] offset. A potential solution would be the CO(10-9) line at redshift

_𝑧_ = 2 _._ 284.

**FLASH-76W** ( _A-grade_ ) shows a line feature at 338.0 GHz with an
additional feature at 339 GHz. The _Herschel_ source is expected to lie
at _𝑧_ _𝑠𝑢𝑏_ = 2 _._ 14, with the VIKING source between _𝑧_ = 0 _._ 95 to 1.13.
The ALMA morphology suggests it is a lensed system, although
no line emission was seen in the weaker counter-image. A potential
redshift solution could be that these are the CO(7-6) and [C i](2-1)
emission lines at _𝑧_ = 1 _._ 387. The fidelity of the second line is currently still too low to exclude any other solutions.
**FLASH-86N** ( _A-grade_ ) shows an absorption feature at 336.2 GHz.
The source at _𝑧_ = 3 _._ 85 is lensed by a foreground VIKING source
between _𝑧_ = 0 _._ 63 to 0.73. The only bright absorption feature is the
CH [+] (2-1) absorption line, confirming its redshift to be _𝑧_ = 3 _._ 965.
Although four of these five sources had already been confirmed to
be lensing systems through the visual identification methods, none
of the five sources with line observations provide indications of
confusion between the foreground and background source. At least,
this provides some confidence in the redshift cut between the foreand background source.
In Figure 8, we show the distribution of the photometric redshift difference between sources with different lensing classifications.
Simplistically, the assumption could be that the confusion between
fore- and background sources would show up as a lower average difference between the two sources. Instead, there does not appear to
be a significant difference between the redshift difference of A-grade
sources and the B- and C-grade classifications. There could thus
be a small contribution of confusion between fore- and background
systems, although so far there are no concrete indications from spec


SNR =
∑︁

_𝑖_ [︁]


[︁]



_𝑆_ _𝑖_
_._ (6)
_𝜎_ ~~[√]~~ [︁] _𝑁_ pix _𝑁_ beam


[︁]




[︁]


In this explicit equation, the per-beam flux density, _𝑆_ _𝑖_ [Jy / beam], is
converted to the per-pixel flux density by dividing by the number of
pixels per beam, _𝑁_ beam . Subsequently, the per-pixel flux is summed
over all pixels in the annulus, _𝑁_ pix . and is normalized to the perfield standard-deviation, _𝜎_ . The pixels are cross-correlated on the
scale of a beam, so this standard-deviation needs to be corrected
by the square-root of the number of pixels per beamsize, as well
as correct for the reduced uncertainty for the larger aperture, i.e.,
_𝜎_ / ~~[√]~~ [︁] _𝑁_ pix _𝑁_ beam, resulting in a noise profile with a unit variance
centered around zero.

Figure 6 shows the annuli-based curve-of-growth analyses for the
three sources where additional _>_ 5 _𝜎_ ring-like features were found
below the ordinary detection threshold: FLASH-30, FLASH-34 and
FLASH-75. These graphs show the 5.5 arcsecond surroundings of
the VIKING sources, and fit annuli with three different widths (0.15,
0.3, and 0.5 arcseconds) in an effort to reveal lensing features. The
bottom panels show the signal-to-noise ratio as a function of angular
distance. Direct observations of lensing features is explicitly less
sensitive to larger lensing arcs, and all these features indicate Einstein
radii below 1 arcsecond. Several more sources have ∼ 4 _𝜎_, although
deeper observations are necessary to confirm these sources to exclude
false-positives.


_4.1.2_ _Confusion between fore- and background sources_


Our source selection included a low probability ( _<_ 0 _._ 1 %) of overlap
between the redshift probabilities of VIKING galaxies and _Herschel_
sources. However, without spectroscopic observations, both of the
VIKING galaxies and _Herschel_ sources, we cannot exclude the possibility of observing the same object in VIKING as in _Herschel_ .
Since these sources are selected from roughly 50 square degrees, our
method could instead be an effective way for finding near-infrared
bright DSFGs (to be VIKING-detected) with cold dust (resulting in
a vast over-estimation of the sub-mm photometric redshift).
While the main goal of the ALMA observations was to unravel the
morphologies of these galaxies, the observations also offer spectral
information on these sources. Given the spectral coverage, we could


MNRAS **000**, 1–27 (2023)

4


2


0


2


4



0.15"

0.3"

0.5"


0 1 2 3 4 5

Ring Radius [arcsec]



_Finding lenses in a FLASH_ 21


0.15"

0.3"

0.5"


0 1 2 3 4 5

Ring Radius [arcsec]



4


2


0


2



0.15"

0.3"

0.5"


0 1 2 3 4 5

Ring Radius [arcsec]



4


2


0


2


4



**Figure 6.** Top panels show a 11 by 11 arcsecond view of the high-resolution (0.15 arcsec) ALMA continuum, with _red contours_ at 2, 3, 5, 8, 10 and 20 _𝜎_, with
the dashed contours indicating negative continuum at the same levels. The _blue_ _diamond_ shows the VIKING position, with centred circles at 1, 2, 3, 4, and
5 arcseconds in radius. The filled contour indicates the most significant emitting annulus. The bottom panels show the annulus-integrated signal-to-noise of the
sources as a function of the ring radius for three different annulus widths. These three sources are the only sources where lensing was not already identified
through direct observations, and the signal-to-noise in one of the three annuli exceeds 5 _𝜎_ .



30



C-grade

B-grade

A-grade



**Figure** **7.** The ALMA observations have the ability to detect spectroscopic
features. As galaxies red-shift, different lines come into view. The _black lines_
indicate the CO lines, starting at CO(3-2) on the left-hand side. The _blue_
_lines_ indicate alternative lines we can expect to detect, such as [C i], H 2 O and

[N ii]. The graph was made using the redshift-search-graph tool by Bakx &
Dannerbauer (2022), which highlights redshift regions where single CO lines
are targeted in _orange_, and where multiple lines are detected in _blue_ . Since
no blue regions are seen, no redshift regions would expect more than a single
CO line detection, although combinations of [C i], H 2 O and CO lines are still
possible.


troscopy or from the redshift difference distributions. The redshift
selection criterion in the selection technique appears robust.



25


20


15


10


5


0

0 1 2 3 4 5

Redshift difference


**Figure** **8.** The distributions of the redshift difference between sources with
different lensing classifications. The redshift difference distributions do not
appear different between the A-, B- and C-grade sources, suggesting there is
no large contribution of confusion between fore- and background sources.


_4.1.3_ _Cluster lenses and protoclusters in the FLASH sample_


The sources in the FLASH sample are selected from _Herschel_ catalogues, which are extracted from the ≈ 18 arcsecond-wide SPIRE
250 _𝜇_ m point-spread functions. This has increased the possibility of
_source_ _confusion_, where multiple sources are confused as a single
emitting source. While the FLASH sources are selected as singular


MNRAS **000**, 1–27 (2023)

22 _Tom Bakx et al._


_Herschel_ sources, they could instead be resolved into multiple sources
by ALMA. Particularly at fluxes of _𝑆_ 500 = 20 − 40, the confusion
fraction can be around 40 per cent (Scudder et al. 2016) or higher (see
Bendo et al. 2023 for a more complete discussion). Based on number
counts from a hydrodynamical model by Lagos et al. (2020), about
half of the fields is predicted to contain an additional emitter at 3 _𝜎_,
although the _Herschel_ source pre-selection increases this probability.
47 fields contain more than one emitter (excluding multiple images
from lenses), in line with the prediction from random pointings. This
does not mean that there is no indication of excess sources. Six
teen fields contain more than two sources, of which FLASH-40 and
-64 contain four ALMA sources, far above the expected number of
fields with multiplicity. The FLASH-40 system has a A-grade lens,
while FLASH-64 has a nearby source that could indicate a lensed
galaxy, suggesting that source multiplicity is not the only driver of
such sources, but that gravitationally-lensed sources could also trace
environments with multiple sources (Overzier 2016).
On the other hand, the foreground imaging from VIKING reveals
around twelve fields with multiple NIR bright sources. Our selection method aims towards galaxy-galaxy lensing, but might also pick
up galaxy-cluster lensing. Using a visual identification, we identify two A-grade sources (FLASH-21 and -82), five B-grade sources
(FLASH-4, -35, -43, -44, and -62) and five C-grade sources (FLASH1, -6, -29, -56, and -77) with additional bright VIKING galaxies. The
grade identification relies on low angular separations, in line with
high-magnification galaxy-galaxy lenses, however our method might
not be as good at identifying cluster lenses with larger separations,
or galaxy-galaxy lenses with large separations and lower magnifications, perhaps in the range of weak lensing.


**4.2** **Effectiveness of the FLASH method**


We robustly identify 40 lensed sources (A-grade), at 47 per cent of
the total sample. In 23 cases, there are some tentative indications of
lensing, which cannot be confirmed with current observations (Bgrade). For the remaining 23 cases, the ALMA observations provide
no indications of gravitational lensing (C-grade). Several stand-out
sources show-case lensing in near-complete Einstein rings, such as
FLASH-13, -27, -58, -73, -85 and -86 (see Appendix Figure A1).
Particularly the lensing nature of FLASH-13, selected at a mere
_𝑆_ 500 = 23 _._ 6 mJy, confirms that our method is capable of selecting
lenses at four or five times lower apparent flux densities than previous
methods (Negrello et al. 2010, 2014, 2017; Vieira et al. 2013). Meanwhile, several A-grade sources do not have apparent counter-images
in the ALMA observations, which could indicate weaker lensing
below the strong-lensing regime of _𝜇>_ 2.

Figure 9 shows the distribution of source types as a function of their
flux density. Equation 3 predicted a high lensing fraction among the
sample ( _𝑓_ ALMA = 0 _._ 9), however we are only able to confirm lensing
for 47 per cent of sources (A-grade) through the ALMA observations.
Meanwhile, the method appears to be most successful at the highest
flux-densities, as expected from previous lensing searches that focus
on sources with a higher probability to be gravitationally lensed, such
as Negrello et al. (2010).

The selection of foreground galaxies through VIKING could introduce a bias in the redshift selection. In Figure 10, the redshifts of
the fore- and background sources of each grade are shown against
predictions from Lapi et al. (2012); Cai et al. (2013) and Eales (2015)
for the foreground distributions. The models are dependent on the
background source distribution. Here, we assume a lensed source
redshift of _𝑧_ _𝑙_ = 2 _._ 5, in line with the average redshift of our sample
( _𝑧_ l _,_ FLASH = 2 _._ 5 ± 0 _._ 6). The redshift distribution of the foreground


MNRAS **000**, 1–27 (2023)



1.0


0.0

|0<br>.<br>8<br>.|Col2|Col3|Col4|Col5|Col6|Col7|grade<br>-grade<br>-grade|
|---|---|---|---|---|---|---|---|
|.8<br>.0||||||||
|.8<br>.0||||||||
|.8<br>.0||||||||
|.8<br>.0||||||A-<br>B<br>C|A-<br>B<br>C|
|.4<br>.6|.4<br>.6|.4<br>.6|.4<br>.6|.4<br>.6|.4<br>.6|.4<br>.6|.4<br>.6|
|.4<br>.6|.4<br>.6|.4<br>.6||||||
|.4<br>.6|.4<br>.6|.4<br>.6||||||
|.4<br>.6|.4<br>.6|||||||
|0<br>.2|0<br>.2|0<br>.2|0<br>.2|0<br>.2|0<br>.2|0<br>.2|0<br>.2|


20 30 40 50 60 70 80
Flux density [mJy]


**Figure** **9.** The fraction of sources in each classification is shown for each
flux density interval at _𝑆_ 500 . The different categories of sources are coloured
in _blue_ and _red_, with A-grade lens candidates in _blue_, B-grade candidates
in _dark_ _red_, and C-grade candidates in _light_ _red_ . The number of confirmed
lens candidates (A-grade) is highest for the brightest sources, although robust

lensed sources are seen at all flux densities.



25


20





15


10


5


0

0 1 2 3 4 5

Photometric Redshift


**Figure 10.** The fore- ( _hatched histograms_ ) and background ( _filled histograms_ )
redshift distribution of sources in A- ( _blue_ ), B- ( _dark red_ ) and C-grade ( _light-_
_red_ ). The foreground redshift distribution appears similar to the ones predicted
from cosmological models (Lapi et al. (2012); Eales (2015), assuming _𝑧_ _𝑠_ =
2 _._ 5). This suggests there is no obvious redshift bias in the foreground lensing

distribution.

0.999



A-grade

B-grade

C-grade

GAMA-12



0.99


0.9


10 20 30 40 50 60 70 80
500 micron flux density [mJy]


**Figure** **11.** The distribution of sources as a function of their flux density
and reliability for different source grades. There does not appear to be a
clear correlation between the reliability and the nature of the source at these
high reliabilities, likely because these sources pre-select towards _Herschel_
positions scattered close to VIKING sources, which could pose a fundamental
limit to the highest-fidelity lens selection based on positions. Meanwhile, the
method can accurately select lenses, even at lower reliabilities, enabling large
lensing samples in the future. We show the underlying population of GAMA12 sources with a similar selection function as the FLASH survey, as well as
a line indicating the region where the FLASH observations are representative
of the underlying population.


sources in FLASH is similar to the distributions predicted by the
models, and there thus does not appear to be a preferential selection
to either low- or high-redshift lenses in the FLASH method.

In Figure 11, the reliability of each source is compared against their
500 _𝜇_ m flux density, highlighting the different nature of the sources
accordingly. There does not appear to be a clear split in reliability
between the C- and A-grade sources throughout the sample, with
several C-grade sources at reliabilities _𝑅_ ∼ 0 _._ 995. The effect of the
false-positives might thus be less than expected from previous work
(Bakx et al. 2020a), which should increase rapidly for decreasing
reliabilities. FLASH targeted the most likely lens candidates, and is
representative of the sources with the highest reliabilities among the
GAMA-12 sources, with reliabilities between 0.9 and 0.99.
The angular offset of the ALMA sources from the _Herschel_ position is between 0.5 to 2 arcseconds even for A-grade lens candidates.
This indicates that one of the core ingredients in the lensing identification method, namely the angular offset, could be more uncertain
than predicted. There thus exists an additional uncertainty in the
likelihood ratio, resulting in scatter in the reliabilities of sources at
the high end of the reliabilities. Instead, there could be a fundamental limit to the reliability of fainter sources, and consequently, there
could be a certain level of false-positives that statistical estimators
for gravitational lenses are likely to include also in future works. The
method from Bakx et al. (2020a), as well as other methods such as
SHALOS (González-Nuevo et al. 2019), offer the ability to include
the effect of additional angular offset, however it is likely that the
highest reliability sources ( _𝑅>_ 0 _._ 99) will always be those scattered
close to the nearby VIKING source. Conversely, the ability of this



_Finding lenses in a FLASH_ 23


method to select lenses even at lower reliabilities suggests that it is
useful to target lower-reliability sources, enabling large lens samples
in the near future.


**4.3** **The lensed galaxies of the FLASH sample**


The properties of a galaxy-galaxy lensing event are described perfectly in the geometric terms of general relativity, as a function of
the distances between the foreground and background galaxy, their
individual distances towards our telescope, and the mass distribution
of the source. For a Single Isothermal Sphere mass profile, the resulting angular separation between the centre-of-mass of the foreground
source and the dust emission, _𝜃_ _𝐸_, can be simplified to the equation



In this equation, the velocity dispersion _𝜎_ v is taken to be √︁ _𝐺𝑀_ /2 _𝑟_ _ℎ_,

with the halo definition ratio ( _𝑟_ _ℎ_ ) take as the _𝑟_ 200 = 3 _𝑀_ /(4 _𝜋_ 200 ∗
_𝜌_ crit ( _𝑧_ _𝑙_ )), where _𝜌_ crit ( _𝑧_ _𝑙_ ) is the critical density of the Universe at
redshift _𝑧_ _𝑙_ (Bartelmann & Schneider 2001). _𝑀_ is the total lensing
mass, _𝐷_ _𝐿𝑆_ is the angular distance between the sub-mm source and
the lens, and _𝐷_ _𝑆_ represents the angular distance of the sub-mm

source.


The VIKING catalogue provides a stellar mass based on a fit
to the optical and NIR fluxes (Wright et al. 2019). In the case of
galaxy-galaxy lensing, these sources are assumed to be massive cuspy
systems, typically red-and-dead elliptical galaxies with little dust
obscuration. Although the gas fraction of these galaxies is likely low
– and the baryonic mass is thus locked up in the stars – the lensing
mass of galaxies is dominated by the dark matter content of these
sources. Cosmological models predict roughly a stellar-to-halo mass
ratio of ∼ 10−1000, depending on the halo mass (Girelli et al. 2020).
The ALMA observations provide a high-resolution view at the
lensing geometry, and thus an estimate for _𝜃_ _𝐸_ . In Figure 12 we compare the observed separation against the one predicted from the equation 7. The observed separation are taken from the weighted average
of the positions of B- and C-grade lens candidates. For A-grade lens
candidates, we select the weighted average of the angular separation
of the sources that are the lensed counterpart (see Table 3). There
is a clear distribution of sources based on their observed separation,
although we note that this is part of the lensing grade identification.
The A-grade sources are distributed below 2 arcseconds. The Bgrade sources are roughly distributed in two clumps, one group lies
below 0.3 arcseconds separation, where it is not possible to clearly
differentiate between the foreground and background source, and the
other group lies at separations above one arcsecond. The C-grade
sources are seen above 2 arcseconds. A-grade sources are scattered
around and below the predicted separation (i.e., _𝑀_ lens = 100 _𝑀_ ∗ ; see
for example Crespo et al. 2022; Fernandez et al. 2022), with masses
between 10 and 1000 times the solar mass of the foreground system.
Sources with B- and C-grades at higher separations could be more
massive ( _𝑀_ lens _>_ 1000 _𝑀_ ∗ ) lensing events that are difficult to confirm with our current data. It is important to note that, although the
Einstein radius used in equation 7 is correct for an SIS, the observed
angular separation from the VIKING source to the ALMA-observed
emission is an upper limit for _𝜃_ E . This measure also includes an additional factor that accounts for the source plane impact parameter,
which can reduce the necessary mass to produce an observed offset.
As a result, the most conservative approach would be to take the
extreme offsets as upper limits.

We further compare the relative mass estimates of the sources in


MNRAS **000**, 1–27 (2023)



_𝜎_ _𝑣_
_𝜃_ E = 4 _𝜋_
� _𝑐_



2 _𝐷_ LS
_._ (7)
� _𝐷_ S

24 _Tom Bakx et al._













**Figure** **12.** The expected separation based on the stellar mass estimates of
the VIKING sources compared for the different source types. The lensing
nature of the foreground sources depends on the total mass, including the
enclosed dark-matter halo. The A-grade sources are located at lower lensingto-stellar mass ratios. B-grade sources are split in two groups, with one group
at low separation, while the other group suggests higher lensing-to-stellar
mass ratios. C-grade sources are found at the highest separations, although
they could still be lensed through galaxy-cluster lensing at larger separations.


Figure 13, where we show the mass of the foreground system, based
on the angular offset between the ALMA and VIKING source, and
the stellar mass of the foreground source. The average mass for the
A-grade lens candidates is log 10 _𝑀_ / _𝑀_ ⊙ = 12 _._ 9 ± 0 _._ 5, and lies approximately one order of magnitude below the C-grade sources. The
uncertainty in the lensing mass is well below one order of magnitude,
and results from a combination in uncertainty in redshift and stellar
mass. The effect of redshift has been studied in Serjeant (2012), who
reports a relatively minor variation ( _<_ 50 %) for a large deflector
redshift variation between _𝑧_ _𝑑_ = 0 _._ 3 and _𝑧_ _𝑑_ = 1 _._ 5 for a lensed source
at redshift _𝑧_ _𝑙_ = 2 _._ 5. The uncertainty in the stellar masses is also relatively low, however we should consider that these observations target
a very specific galaxy population, which could introduce a systemic
uncertainty in stellar masses. That said, the stellar masses are unlikely
to exceed much beyond 10 [11] _𝑀_ ⊙, and due to the square-root coefficient in equation 7, the resulting uncertainty will also be below 50 %
( _<_ 0 _._ 2 dex; Wright et al. 2019). We estimate the halo-to-stellar mass
ratio of our A-grade lens candidates, which is around 10 [2] _[.]_ [2][±][0] _[.]_ [1] _𝑀_ ⊙,
with a source-to-source variation on the order of 0.9 dex. These val
ues are in line with previous works from (Amvrosiadis et al. 2018;
Crespo et al. 2022; Fernandez et al. 2022). Halo-to-stellar mass ratios in excess of 100 are high for dark matter haloes, although the
profile taken in equation 7 assumes all the mass to be located solely
at _𝜃_ _𝐸_ . Similarly, galaxies could be lensed by a group ( _𝑁<_ 5) of
sources, which would not be included in the stellar mass estimate
from Wright et al. (2019). The mass ratio is around 0.5 dex. higher
than those predicted in models from Girelli et al. (2020) for halo
masses around 10 [12] _[.]_ [9] M ⊙ around _𝑧_ = 0 − 1.
In part, this could be because of weak lensing affecting the sample
(see further discussion of this in Section 4.4). Our lens identification
method skews towards high-magnification, galaxy-galaxy lenses with


MNRAS **000**, 1–27 (2023)



**Figure 13.** A histogram of the logarithm of the lensing mass expected from
the observed angular separation between the foreground and background
source, and the stellar mass derived from the VIKING photometry (Wright
et al. 2019). It shows that the average mass of an A-grade lens candidates
is log 10 _𝑀_ / _𝑀_ ⊙ = 12 _._ 9 ± 0 _._ 5. The B-grade candidates are more broadly
distributed, and C-grade candidates lie at larger lensing masses if their ALMA
emission is lensed by foreground VIKING galaxies, necessitating galaxycluster lensing events.


cuspy profiles, however the VIKING images appear to indicate several fields with multiple galaxies, producing galaxy-cluster lensing
missed in this analysis. Empirically, Dunne et al. (2020) found that
weak lensing boosted the selection of even nearby ( _𝑧_ = 0 _._ 35) galaxies.
As a result of using direct ALMA observations to identify lensing,
we are likely missing weak lensing events. As a consequence, highermass haloes are likely contributing to the B- and C-grade sources, as
shown in Figure 13, although we note that it is necessary to account
for the additional effect of the impact parameter of the sources, which
is not perfectly represented by using the observed angular separation
as _𝜃_ _𝐸_ in equation 7, as discussed above.


**4.4** **Total number of lenses in the** _**Herschel**_ **catalogue**


This is not the first search for gravitational lenses among the _Herschel_
sample, however it is one of the first study to comprehensively test
the method across the _Herschel_ fluxes using high-resolution sub-mm
observations. In Figure 14, we compare the source counts of sub-mm
galaxies at 500 _𝜇_ m for both purely-lensed candidate samples and
non-differentiated samples. We compare these against the source
counts of the lensed sources found by the FLASH method across
the 53.56 sqr. deg. GAMA-12 field. We use the success ratio of the
FLASH observations across the regime where the observations are
representative for the underlying GAMA-12 field (see Figure 11),
and calculate the number of lensed sources that the current FLASH

configuration will be able to identify. At the faintest flux end, we
include an adjustment to show the effect of the 250 _𝜇_ m selection in
light red: in the original _Herschel_ catalogues, sources are extracted
by their _𝑆_ 250 flux density, removing some of the highest-redshift
galaxies. We adjust this by comparing the fraction of sources with

low redshift ( _𝑧<_ 2) to high redshift ( _𝑧>_ 2) for the lowest two flux
bins when compared to the highest flux bins.

The lensed candidates from the SHALOS method from González
Nuevo et al. (2019) and the VIKING-based selection from Ward et al.
(2022) are compared against the non-differentiated selections from
_Planck_ (Trombetti et al. 2021), the brightest _Herschel_ galaxies from
Negrello et al. (2017), and the recent discovery of a lens among the
STUDIES sample (Pearson et al. 2023). Surveys from SCUBA-2 at
450 _𝜇_ m from Casey et al. (2013); Chen et al. (2013) and Zavala et al.
(2017) explore the lower flux-density regime. Note that all lensed
candidate samples are based on unresolved predictions. We compare the sources against the different known 500 _𝜇_ m-bright emitters,
namely late-type local galaxies at the brightest end, radio sources,
lensed galaxies from the galaxy evolution model of Cai et al. (2013)
– assuming a maximum lensing magnification of _𝜇_ max = 15 – and
finally unlensed DSFGs.
The predicted number of lenses found with the method described
in Bakx et al. (2020a) is in agreement with the predicted values from
Ward et al. (2022) and with those found in the SDSS-based estimates by González-Nuevo et al. (2019), even though the SDSS have
been shown to be incomplete for the highest-redshift lenses (Bakx
et al. 2020a). Similar to previous statistical studies, we now robustly
confirm the elevated number of lensed sources starting at ∼ 60 mJy
when compared to strong-lensing models. These models only account for galaxy-galaxy lensing, which misses galaxy-cluster lenses
that have already been shown to dominate at lower flux densities
through unresolved statistical studies (González-Nuevo et al. 2012,
2014). Although these galaxy-cluster lenses are an important contributor to the total number of lensed sources, identifying these systems
is difficult given the requirement for deeper observations at larger
fields-of-view. As noted in Ward et al. (2022), the likelihood estimator is not well-suited for the large separations of galaxy-cluster lenses
(∼ 20 arcseconds), and even misses the majority of galaxy-galaxy
sources with separations above 8 arcsec. Our research is unable to
quantify the galaxy-cluster lensing beyond a tentative visual tally of
twelve fields with excess VIKING sources, particularly in B- and
C-grade fields. Meanwhile, these sources would still not be able to
account for the 0.7 dex excess relative to the predicted models. The
most likely explanation is the contribution of weak lensing, since
the galaxy evolution models have a minimum classification of strong
lensing at _𝜇>_ 2, and some of our sources might be only weakly
magnified. This is corroborated by a visual inspection of our sources
finds some sources with lensing identification (i.e., grade A) without
multiple imaging or a counter-image resolved in the ALMA imaging.
Although this does not exclude strong lensing. The contribution of
weak lensing from our sub-sample of eighteen sources without multiple imaging (FLASH-3, -12, -14, -20, -28, -30, -34, -37, -46, -47, -52,
-54, -60, -61, -65, -68, -69, -71) would nearly double (18/40 = 45 %)
the number of strongly-lensed sources when compared to the _𝜇>_ 2
strong-lensing criterion adopted by Cai et al. (2013). This is on the
same order as the excess of lenses seen between the lenses found by
FLASH against those predicted in the galaxy evolution model of Cai
et al. (2013).

For submillimeter galaxies with a redshift around 2.5, the likelihood of the flux at 250 micron being close to the detection limits
increases as the flux density at 500 micron becomes fainter. This is a
consequence of the detection strategy employed to construct the official H-ATLAS catalogues, as previously mentioned. Consequently,
some of these sources are detected primarily due to lensing amplification, even with relatively small amplification factors ranging from
5 per cent to 20 per cent. This phenomenon, known as magnification
bias, has received considerable attention in recent years and has been



_Finding lenses in a FLASH_ 25


the subject of detailed measurement and analysis (Bonavera et al.
2022 provides a concise overview of the topic).
Notably, the halo masses of the lenses, derived from the analysis
of the cross-correlation function, exhibit a strong agreement with
those estimated directly from individual lensing events in the current
study, yielding an approximate range of 10 [12][−][12] _[.]_ [5] (González-Nuevo
et al. 2017, 2021; Bonavera et al. 2019, 2021; Cueli et al. 2021,
2022). Furthermore, these studies have concluded that the majority of
magnification bias arises not from isolated galaxies, but from small
groups of galaxies featuring one or two dominant members and a
few satellites (see also Fernandez et al. 2022; Crespo et al. 2022).
Therefore, it is likely that some of the lensing events observed in the
current sample are also caused by small groups of galaxies. While
there are indications in the images, verifying these observational
findings would require data beyond the scope of this current study.
Finally, similar to the discoveries made by Dunne et al. (2020), a
few of the lensing events examined in this work can be considered as
direct observations of magnification bias, which is typically studied
only at a statistical level. In the study by Dunne et al. (2020), weak
lensing modestly biased their fluxes even in the low redshift Universe,
although further investigations of the cluster-lensing population is
necessary to see whether the excess is indeed due to galaxy-cluster
lenses or whether an excess of lensed sources exist – an important
point indeed, since this would require additional masses to exist
beyond the ones predicted in our current cosmological paradigm
(e.g., Eales 2015).
Accounting for the efficiency and the strict selection criteria of our
sample, a total of 3000 lenses are expected to be observable across the
660 square degree H-ATLAS survey. This assumes the existence of
complete VIKING-level observations, which are non-existent in the
Northern field to date. This is large relative to the SHALOS method
described in González-Nuevo et al. (2019), that provides a sample –
adjusted for the total 660 square degrees of H-ATLAS – of ∼ 870
robust lensed candidates. The southern-field study of Ward et al.
(2022) has already demonstrated efficient selection of lensed sources
down to ∼ 30 mJy at 500 _𝜇_ m, and they report the ability to find 13 730
lensed sources across the entire H-ATLAS fields, which suggests it is
worthwhile to test the FLASH method more comprehensively down
to lower reliabilities as shown in Figure 11.
At the lowest 500 _𝜇_ m flux densities, the H-ATLAS survey thins
out significantly due to the prior selection at 250 _𝜇_ m in the catalogues. Lensed sources, located at redshifts above 2.5, would have
lower fluxes at 250 _𝜇_ m. Our estimate based on the photometric
redshift estimates of the entire _Herschel_ catalogues, the expected
number of sources across the full _Herschel_ catalogues could be expanded to 7000 sources (a 2 _._ 35 × increase if we remove our current
_𝜎_ 250 ≈ 7 mJy criterion). These sources would be worthwhile to include in future lensing models, since (i) these sources have a larger
cosmic volume for foreground lenses to magnify the background
population, and more importantly, (ii), higher-redshift galaxies are
rarer in 500 _𝜇_ m-selected samples. Their steeper luminosity function (Gruppioni et al. 2013) ensures that more of the apparentlybright high-redshift population is instead fainter gravitationallylensed sources. Future works could further improve lens selection
by investigating samples that explicitly overcome this 250 _𝜇_ m selection, either through re-extraction (Ivison et al. 2016; Oteo et al.
2017) or through 500 _𝜇_ m − 250 _𝜇_ m difference maps (Asboth et al.
2016; Duivenvoorden et al. 2018). That said, the current methods
are already powerful enough to enable large sub-mm selected lens
samples (e.g., Eales 2015), and an ALMA survey of such large lens
samples could become an important cosmological tool in the near
future.


MNRAS **000**, 1–27 (2023)

26 _Tom Bakx et al._


1000


100


10


1


0.1


0.01


0.001





10 [6]


10 [5]


10 [4]


10 [3]


10 [2]


10 [1]


10 [0]



|FLASH<br>radio<br>unlen<br>late-t<br>lense<br>SCUB<br>SCUB<br>SCUB<br>Hersc<br>SHAL<br>Hersc<br>Planc<br>STUD|(this paper)<br>sources<br>sed galaxies<br>ype galaxies<br>d DSFGs (Cai+13)<br>A-2 (Casey+13)<br>A-2 (Chen+13)<br>A-2 (Zavala+17)<br>hel (Negrello+17)<br>OS (P > 0.7; GN+2019)<br>hel (Ward+22)<br>k (Trombetti+21)|
|---|---|
|FLASH<br>radio<br>unlen<br>late-t<br>lense<br>SCUB<br>SCUB<br>SCUB<br>Hersc<br>SHAL<br>Hersc<br>Planc<br>STUD|IES (lens; Pearson+23)|
|10<br>20<br>50<br>100<br>500 m flux density|10<br>20<br>50<br>100<br>500 m flux density|


**Figure** **14.** Cumulative number counts at 500 _𝜇_ m for the lensed sources in
the FLASH sample and other samples – both pre-selected to contain lenses
and without lens-preselections. _Red_ _squares_ indicate the number counts for
all _Herschel_ sources based on the FLASH-selection and _light-red_ _squares_
show the source counts including an additional correction for the redshiftincompleteness towards lower flux densities. The counts of late-type, normal,
and starburst galaxies and of unlensed dusty star-forming galaxies (DSFGs),
interpreted as proto-spheroidal galaxies in the process of forming the bulk of
their stars, are from the Cai et al. (2013) model, as well as the yellow line
indicating the source counts for lensed sources with a magnification cut-off
at _𝜇_ max = 15. As seen in previous studies, these counts exceed the predicted
number counts for lensed sources in the 10 − 60 mJy regime, as these models
only account for strong galaxy-galaxy lensing, and do not account for galaxycluster lensing or weak lensing events potentially identified by the FLASH

method.


**5** **CONCLUSIONS**


The _Herschel_ Space Observatory detected near-one million sources
across 1000 square degrees from low to high redshift. In this study,
we observationally test the validity of the selection method through
resolved observations with ALMA, by targeting a sample of 86 likely
lensed sources identified by close, bright VIKING counterparts. We
find:


  - The ALMA observations are able to confirm 40 (47 per cent) of
these sources to be strong lenses (A-grade lens candidates). For an
additional 23 (27 per cent) sources, there are tentative indications of
lensing, however our ALMA observations are not able to conclusively
indicate lensing (B-grade lens candidates). For the final 23 (27 per
cent), it remains unclear whether these sources are lensed (C-grade
lens candidates).

  - The number of robust lensed sources is below what is expected
from false-positive estimations, although we note that our current
false-positive estimations might not be a reliable estimator, and future
tests can focus on a more comprehensive study of _𝑅>_ 0 _._ 9 sources
to verify the FLASH method and increase the number of lensed
_Herschel_ sources we can identify.

  - Although we do not find direct indication for sources where
the VIKING galaxy and _Herschel_ source are the same object, nearinfrared spectroscopic confirmation of the foreground objects and
sub-mm spectroscopic confirmation of the background sources is
important to exclude such sources, particularly for the B-grade lens
candidates below 1 arcsecond separation.


MNRAS **000**, 1–27 (2023)




  - Most of the lensing features would require a total lensing
mass between 10 and 1000 times that of the stellar emission re
ported for these VIKING sources, with typical lensing masses of
log 10 _𝑀_ / _𝑀_ ⊙ = 12 _._ 9 ± 0 _._ 5, in line with previous observations
(Amvrosiadis et al. 2018) and above what is predicted from models (Girelli et al. 2020). The ALMA identification method likely
misses several sources at larger angular separations, potentially due
to weak gravitational lensing.

  - Our method will be able to find ∼ 3000 lensed sources over the

entire H-ATLAS field, in excess of what is expected from the galaxygalaxy strong lensing predicted by the galaxy evolution models of
Cai et al. (2013).


**ACKNOWLEDGEMENTS**


This work was supported by NAOJ ALMA Scientific
Research Grant Nos. 2018-09B and JSPS KAKENHI

No. 17H06130, 22H04939, 22J21948, and 22KJ1598. JGN
and LB acknowledge the PID2021-125630NB-I00 project
funded by MCIN/AEI/10.13039/501100011033/FEDER. LB
also acknowledges the CNS2022-135748 project funded by
MCIN/AEI/10.13039/501100011033 and by the EU “NextGenerationEU/PRTR”. SS was partly supported by the ESCAPE project;
ESCAPE – The European Science Cluster of Astronomy and Particle
Physics ESFRI Research Infrastructures has received funding from
the European Union’s Horizon 2020 research and innovation
programme under Grant Agreement No. 824064. SS also thanks
the Science and Technology Facilities Council for financial support
under grant ST/P000584/1. This paper makes use of the following
ALMA data: ADS/JAO.ALMA#2019.1.01784.S. We would like to

kindly thank the anonymous referee for their insightful comments
and suggested additions.


**DATA AVAILABILITY**


The reduced, calibrated and science-ready ALMA data
are available from the ALMA Science Archive at

`https://almascience.eso.org/asax/` .


**REFERENCES**


[ALMA Partnership et al., 2015, ApJ, 808, L4](http://dx.doi.org/10.1088/2041-8205/808/1/L4)
[Amvrosiadis A., et al., 2018, MNRAS, 475, 4939](http://dx.doi.org/10.1093/mnras/sty138)
[Andrews B. H., Thompson T. A., 2011, ApJ, 727, 97](http://dx.doi.org/10.1088/0004-637X/727/2/97)
[Asboth V., et al., 2016, MNRAS, 462, 1989](http://dx.doi.org/10.1093/mnras/stw1769)

[Bakx T. J. L. C., Dannerbauer H., 2022, MNRAS, 515, 678](http://dx.doi.org/10.1093/mnras/stac1306)

[Bakx T. J. L. C., et al., 2018, MNRAS, 473, 1751](http://dx.doi.org/10.1093/mnras/stx2267)

[Bakx T. J. L. C., Eales S., Amvrosiadis A., 2020a, MNRAS, 493, 4276](http://dx.doi.org/10.1093/mnras/staa506)

[Bakx T. J. L. C., et al., 2020b, MNRAS, 494, 10](http://dx.doi.org/10.1093/mnras/staa658)
[Bartelmann M., Schneider P., 2001, Phys. Rep., 340, 291](http://dx.doi.org/10.1016/S0370-1573(00)00082-X)
Baugh C. M., Lacey C. G., Frenk C. S., Granato G. L., Silva L., Bressan A.,
[Benson A. J., Cole S., 2005, MNRAS, 356, 1191](http://dx.doi.org/10.1111/j.1365-2966.2004.08553.x)

[Bendo G. J., et al., 2023, MNRAS, 522, 2995](http://dx.doi.org/10.1093/mnras/stac3771)
[Bonavera L., et al., 2019, J. Cosmology Astropart. Phys., 2019, 021](http://dx.doi.org/10.1088/1475-7516/2019/09/021)
Bonavera L., Cueli M. M., González-Nuevo J., Ronconi T., Migliaccio M.,
[Lapi A., Casas J. M., Crespo D., 2021, A&A, 656, A99](http://dx.doi.org/10.1051/0004-6361/202141521)
Bonavera L., Cueli M. M., Gonzalez-Nuevo J., 2022, Proceedings of the
MG16 Meeting on General Relativity, R. Ruffini & G. Vereshchagin
[eds., World Scientific., p. arXiv:2112.02959](https://ui.adsabs.harvard.edu/abs/2021arXiv211202959B)
[Bourne N., et al., 2016, MNRAS, 462, 1714](http://dx.doi.org/10.1093/mnras/stw1654)
[Bussmann R. S., et al., 2013, ApJ, 779, 25](http://dx.doi.org/10.1088/0004-637X/779/1/25)

[Bussmann R. S., et al., 2015, ApJ, 812, 43](http://dx.doi.org/10.1088/0004-637X/812/1/43)
[Cai Z.-Y., et al., 2013, ApJ, 768, 21](http://dx.doi.org/10.1088/0004-637X/768/1/21)
[Casey C. M., et al., 2013, MNRAS, 436, 1919](http://dx.doi.org/10.1093/mnras/stt1673)
Chen C.-C., Cowie L. L., Barger A. J., Casey C. M., Lee N., Sanders D. B.,
[Wang W.-H., Williams J. P., 2013, ApJ, 776, 131](http://dx.doi.org/10.1088/0004-637X/776/2/131)
Collaboration P., et al., 2018, Planck 2018 results. VI. Cosmological parameters ( `[arXiv:1807.06209](http://arxiv.org/abs/1807.06209)` )
Crespo D., González-Nuevo J., Bonavera L., Cueli M. M., Casas J. M., Goitia
[E., 2022, A&A, 667, A146](http://dx.doi.org/10.1051/0004-6361/202244016)
Cueli M. M., Bonavera L., González-Nuevo J., Lapi A., 2021, [A&A,](http://dx.doi.org/10.1051/0004-6361/202039326) [645,](https://ui.adsabs.harvard.edu/abs/2021A&A...645A.126C)

[A126](https://ui.adsabs.harvard.edu/abs/2021A&A...645A.126C)

Cueli M. M., Bonavera L., González-Nuevo J., Crespo D., Casas J. M., Lapi
[A., 2022, A&A, 662, A44](http://dx.doi.org/10.1051/0004-6361/202142949)

[Duivenvoorden S., et al., 2018, MNRAS, 477, 1099](http://dx.doi.org/10.1093/mnras/sty691)

Dunne L., Bonavera L., Gonzalez-Nuevo J., Maddox S. J., Vlahakis C., 2020,


[MNRAS, 498, 4635](http://dx.doi.org/10.1093/mnras/staa2665)
[Dye S., et al., 2015, MNRAS, 452, 2258](http://dx.doi.org/10.1093/mnras/stv1442)
[Dye S., et al., 2018, MNRAS, 476, 4383](http://dx.doi.org/10.1093/mnras/sty513)
[Dyson F. W., Eddington A. S., Davidson C., 1920, Philosophical Transactions](http://dx.doi.org/10.1098/rsta.1920.0009)
[of the Royal Society of London Series A, 220, 291](http://dx.doi.org/10.1098/rsta.1920.0009)
[Eales S. A., 2015, MNRAS, 446, 3224](http://dx.doi.org/10.1093/mnras/stu2214)

[Eales S., et al., 2010, PASP, 122, 499](http://dx.doi.org/10.1086/653086)

Fernandez L., Cueli M. M., González-Nuevo J., Bonavera L., Crespo D.,
[Casas J. M., Lapi A., 2022, A&A, 658, A19](http://dx.doi.org/10.1051/0004-6361/202141905)
[Fleuren S., et al., 2012, MNRAS, 423, 2407](http://dx.doi.org/10.1111/j.1365-2966.2012.21048.x)

[Furlanetto C., et al., 2018, MNRAS, 476, 961](http://dx.doi.org/10.1093/mnras/sty151)

[Garratt T. K., et al., 2023, MNRAS,](http://dx.doi.org/10.1093/mnras/stad307)

Girelli G., Pozzetti L., Bolzonella M., Giocoli C., Marulli F., Baldi M., 2020,


[A&A, 634, A135](http://dx.doi.org/10.1051/0004-6361/201936329)
[González-Nuevo J., et al., 2012, ApJ, 749, 65](http://dx.doi.org/10.1088/0004-637X/749/1/65)
[González-Nuevo J., et al., 2014, MNRAS, 442, 2680](http://dx.doi.org/10.1093/mnras/stu1041)

[González-Nuevo J., et al., 2017, J. Cosmology Astropart. Phys., 2017, 024](http://dx.doi.org/10.1088/1475-7516/2017/10/024)
[González-Nuevo J., et al., 2019, A&A, 627, A31](http://dx.doi.org/10.1051/0004-6361/201935475)

González-Nuevo J., Cueli M. M., Bonavera L., Lapi A., Migliaccio M.,
[Argüeso F., Toffolatti L., 2021, A&A, 646, A152](http://dx.doi.org/10.1051/0004-6361/202039043)
[Grillo C., Lombardi M., Bertin G., 2008, A&A, 477, 397](http://dx.doi.org/10.1051/0004-6361:20077534)

[Gruppioni C., et al., 2013, MNRAS, 432, 23](http://dx.doi.org/10.1093/mnras/stt308)
[Harrington K. C., et al., 2021, ApJ, 908, 95](http://dx.doi.org/10.3847/1538-4357/abcc01)
[Hughes D. H., et al., 1998, Nature, 394, 241](http://dx.doi.org/10.1038/28328)
Ivison R. J., Smail I., Le Borgne J. F., Blain A. W., Kneib J. P., Bezecourt J.,
[Kerr T. H., Davies J. K., 1998, MNRAS, 298, 583](http://dx.doi.org/10.1046/j.1365-8711.1998.01677.x)

[Ivison R. J., et al., 2016, ApJ, 832, 78](http://dx.doi.org/10.3847/0004-637X/832/1/78)
[Kamieneski P. S., et al., 2023, arXiv e-prints, p. arXiv:2301.09746](http://dx.doi.org/10.48550/arXiv.2301.09746)
[Kelly P. L., et al., 2018, Nature Astronomy, 2, 334](http://dx.doi.org/10.1038/s41550-018-0430-3)
[Kneib J.-P., Natarajan P., 2011, A&ARv, 19, 47](http://dx.doi.org/10.1007/s00159-011-0047-3)
[Kochanek C. S., 1992, ApJ, 384, 1](http://dx.doi.org/10.1086/170845)
[Kochanek C. S., 1996, ApJ, 473, 595](http://dx.doi.org/10.1086/178175)
Lagos C. d. P., da Cunha E., Robotham A. S. G., Obreschkow D., Valentino
[F., Fujimoto S., Magdis G. E., Tobar R., 2020, MNRAS, 499, 1948](http://dx.doi.org/10.1093/mnras/staa2861)
[Lapi A., et al., 2011, ApJ, 742, 24](http://dx.doi.org/10.1088/0004-637X/742/1/24)
Lapi A., Negrello M., González-Nuevo J., Cai Z. Y., De Zotti G., Danese L.,
[2012, ApJ, 755, 46](http://dx.doi.org/10.1088/0004-637X/755/1/46)
[Maddox S. J., et al., 2018, ApJS, 236, 30](http://dx.doi.org/10.3847/1538-4365/aab8fc)
[Narayanan D., et al., 2015, Nature, 525, 496](http://dx.doi.org/10.1038/nature15383)
[Negrello M., et al., 2010, Science, 330, 800](http://dx.doi.org/10.1126/science.1193420)
[Negrello M., et al., 2014, MNRAS, 440, 1999](http://dx.doi.org/10.1093/mnras/stu413)
[Negrello M., et al., 2017, MNRAS, 465, 3558](http://dx.doi.org/10.1093/mnras/stw2911)
[Oguri M., et al., 2012, AJ, 143, 120](http://dx.doi.org/10.1088/0004-6256/143/5/120)
[Oliver S. J., et al., 2012, MNRAS, 424, 1614](http://dx.doi.org/10.1111/j.1365-2966.2012.20912.x)
[Oteo I., et al., 2017, ApJ, 850, 170](http://dx.doi.org/10.3847/1538-4357/aa8ee3)
[Overzier R. A., 2016, A&ARv, 24, 14](http://dx.doi.org/10.1007/s00159-016-0100-3)

[Pearson E. A., et al., 2013, MNRAS, 435, 2753](http://dx.doi.org/10.1093/mnras/stt1369)

[Pearson J., et al., 2023, arXiv e-prints, p. arXiv:2309.00888](http://dx.doi.org/10.48550/arXiv.2309.00888)
Rizzo F., Vegetti S., Powell D., Fraternali F., McKean J. P., Stacey H. R.,
[White S. D. M., 2020, Nature, 584, 201](http://dx.doi.org/10.1038/s41586-020-2572-6)

[Roseboom I. G., et al., 2010, MNRAS, 409, 48](http://dx.doi.org/10.1111/j.1365-2966.2010.17634.x)

[Rowan-Robinson M., et al., 2016, MNRAS, 461, 1100](http://dx.doi.org/10.1093/mnras/stw1169)



_Finding lenses in a FLASH_ 27


Rybak M., McKean J. P., Vegetti S., Andreani P., White S. D. M., 2015a,

[MNRAS, 451, L40](http://dx.doi.org/10.1093/mnrasl/slv058)
Rybak M., McKean J. P., Vegetti S., Andreani P., White S. D. M., 2015b,

[MNRAS, 451, L40](http://dx.doi.org/10.1093/mnrasl/slv058)
Scudder J. M., Oliver S., Hurley P. D., Griffin M., Sargent M. T., Scott D.,
[Wang L., Wardlow J. L., 2016, MNRAS, 460, 1119](http://dx.doi.org/10.1093/mnras/stw1044)
[Serjeant S., 2012, MNRAS, 424, 2429](http://dx.doi.org/10.1111/j.1365-2966.2012.20761.x)
[Shirley R., et al., 2021, MNRAS, 507, 129](http://dx.doi.org/10.1093/mnras/stab1526)
[Smail I., Ivison R. J., Blain A. W., 1997, ApJ, 490, L5](http://dx.doi.org/10.1086/311017)
Spilker J. S., Bezanson R., Marrone D. P., Weiner B. J., Whitaker K. E.,
[Williams C. C., 2016, ApJ, 832, 19](http://dx.doi.org/10.3847/0004-637X/832/1/19)
[Sutherland W., Saunders W., 1992, MNRAS, 259, 413](http://dx.doi.org/10.1093/mnras/259.3.413)
Tamura Y., Oguri M., Iono D., Hatsukade B., Matsuda Y., Hayashi M., 2015,

[PASJ, 67, 72](http://dx.doi.org/10.1093/pasj/psv040)

[Treu T., 2010, ARA&A, 48, 87](http://dx.doi.org/10.1146/annurev-astro-081309-130924)
Trombetti T., Burigana C., Bonato M., Herranz D., De Zotti G., Negrello M.,
[Galluzzi V., Massardi M., 2021, A&A, 653, A151](http://dx.doi.org/10.1051/0004-6361/202140830)

[Valiante E., et al., 2016, MNRAS, 462, 3146](http://dx.doi.org/10.1093/mnras/stw1806)

[Vieira J. D., et al., 2013, Nature, 495, 344](http://dx.doi.org/10.1038/nature12001)

[Ward B. A., et al., 2022, MNRAS, 510, 2261](http://dx.doi.org/10.1093/mnras/stab3300)
[Welch B., et al., 2022, ApJ, 940, L1](http://dx.doi.org/10.3847/2041-8213/ac9d39)
[Wright A. H., et al., 2019, A&A, 632, A34](http://dx.doi.org/10.1051/0004-6361/201834879)
[Zavala J. A., et al., 2017, MNRAS, 464, 3369](http://dx.doi.org/10.1093/mnras/stw2630)


**APPENDIX A:** **COMPILATION OF STRONG LENSES**


We present a graphical depiction of strong lenses detected across the
spread in 500 _𝜇_ m flux density in Figure A1, showing the capability
of FLASH to detect strong lenses down to _𝑆_ 500 = 20 mJy.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–27 (2023)

28 _Tom Bakx et al._


**Figure A1.** These six ALMA images ( _foreground red_ ) indicate the ability of the FLASH method to select select strong lenses by matching _Herschel_ and VIKING
images ( _Background images_ ) from low- to high 500 _𝜇_ m flux densities. The images are 5 arcseconds across, except for FLASH-48 (7 arcseconds), FLASH-85
(4 arcseconds) and -86 (3 arcseconds). The _red foreground_ is drawn at 1 _𝜎_ and beyond for FLASH-13, -27 and -58, and it is drawn starting at 2 _𝜎_ for FLASH-48,
-85 and -86 to best show the lensing behaviour and extent.


MNRAS **000**, 1–27 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[1]",
  "value": "Can high-resolution ALMA Band 7 continuum observations confirm the lensing nature of 86 faint Herschel submillimetre sources (S500 = 15-85 mJy) identified through statistical association with foreground VIKING near-infrared galaxies, and what does this imply for the total number of lenses across Herschel surveys?",
  "failed_quote": "A thorough test of the fidelity of a lens-selection method should thus focus on these low flux-density sources. In this paper, we report on the observation of 86 galaxies selected using a method based on a VIKING (+ KiDS)-based analysis from Bakx et al. (2020a)."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "VIKING Ks-band counterpart likelihood ratio and reliability lens-selection method, including lensing offset radial distribution f(r) and Q0 = 0.82",
  "failed_quote": "In this paper, we report on the observation of 86 galaxies selected using a method based on a VIKING (+ KiDS)-based analysis from Bakx et al. (2020a)."
 },
 {
  "path": "analysis_steps[0].method.evidence[2]",
  "value": "Start from 35,512 H-ATLAS GAMA-12 sources; remove sources within 10 arcsec of NVSS radio sources; fit modified blackbody SEDs to 250, 350, 500 um fluxes and require z_phot > 2.0; apply VIKING Ks-band likelihood ratio and reliability estimator; require <0.1% (~3.1 sigma) probability that VIKING and Herschel redshifts overlap; select highest reliability sources in 10 mJy S500 bins within 10 degrees ",
  "failed_quote": "In order to efficiently observe these sources, we require each source to be within ten degrees from a single phase-centre to observe all targets within a minimum number of Scheduling Blocks."
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "While bright lenses (S500 > 100 mJy) are easily identified, the bulk of Herschel lenses lie at faint flux densities (20-40 mJy); resolved ALMA Band 7 continuum observations at 0.15 arcsec resolution directly test the fidelity of VIKING-Herschel lens selection at these faint fluxes and require each target to lie within 10 degrees of a single phase centre for scheduling efficiency.",
  "failed_quote": "In order to efficiently observe these sources, we require each source to be within ten degrees from a single phase-centre to observe all targets within a minimum number of Scheduling Blocks."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[1]",
  "value": "The ALMA Band 7 primary beam (~15 arcsec FoV) and surface brightness sensitivity limit the detection of faint, extended, or large-separation cluster lenses, and sources shifted by ~5 arcsec fall into less sensitive regions of the primary beam.",
  "failed_quote": "On the whole, we have a large detection fraction for most sources, although current observations cannot exclude faint, extended, or cluster lenses to be completely accounted for in the ALMA observations."
 }
]
```
