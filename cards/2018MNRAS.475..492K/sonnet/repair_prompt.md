# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018MNRAS.475..492K\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–17 (2017) Preprint 4 December 2017 Compiled using MNRAS L [A] TEX style file v3.0

## **ALMACAL III: A combined ALMA and MUSE Survey for** **Neutral, Molecular, and Ionised Gas in an HI-Absorption-** **Selected System**

### A. Klitsch, [1][,][2][⋆] C. P´eroux, [3] M. A. Zwaan, [1] I. Smail, [2] I. Oteo, [1] A. D. Biggs, [1]


### G. Popping [1][,][4] and A. M. Swinbank [2]

1 _European_ _Southern_ _Observatory,_ _Karl-Schwarzschild-Str._ _2,_ _85748_ _Garching_ _near_ _Munich,_ _Germany_
2 _Centre_ _for_ _Extragalactic_ _Astronomy,_ _Durham_ _University,_ _Department_ _of_ _Physics,_ _South_ _Road,_ _Durham_ _DH1_ _3LE,_ _UK_
3 _Aix_ _Marseille_ _Univ,_ _CNRS,_ _LAM,_ _(Laboratoire_ _d’Astrophysique_ _de_ _Marseille),_ _UMR_ _7326,_ _13388,_ _Marseille,_ _France_
4 _Max-Planck-Institut_ _f¨ur_ _Astronomie,_ _K¨onigstuhl_ _17,_ _69117_ _Heidelberg,_ _Germany_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**


Studying the flow of baryons into and out of galaxies is an important part of understanding the evolution of galaxies over time. We present a detailed case study of the
environment around an intervening Ly α absorption line system at _z_ abs = 0.633, seen
towards the quasar J0423−0130 ( _z_ QSO = 0.915). We detect with ALMA the [12] CO(2–1),
12 CO(3–2) and 1.2 mm continuum emission from a galaxy at the redshift of the Ly α
absorber at a projected distance of 135 kpc. From the ALMA detections, we infer ISM
conditions similar to those in low redshift Luminous Infrared Galaxies. DDT MUSE
integral field unit observations reveal the optical counterpart of the [12] CO emission line
source and three additional emission line galaxies at the absorber redshift, which together form a galaxy group. The [12] CO emission line detections originate from the most
massive galaxy in this group. While we cannot exclude that we miss a fainter host,
we reach a dust-uncorrected star-formation rate (SFR) limit of _>_ 0.3 M⊙ yr [−][1] within
100 kpc from the sightline to the background quasar. We measure the dust-corrected
SFR (ranging from 3 to 50 M⊙ yr [−][1] ), the morpho-kinematics and the metallicities of
the four group galaxies to understand the relation between the group and the neutral
gas probed in absorption. We find that the Ly α absorber traces either an outflow
from the most massive galaxy or intra-group gas. This case study illustrates the power
of combining ALMA and MUSE to obtain a census of the cool baryons in a bounded
structure at intermediate redshift.


**Key words:** galaxies: evolution – galaxies: formation – galaxies: ISM – ISM: molecules
– quasars: absorption lines – intergalactic medium



**1** **INTRODUCTION**


A key part of understanding the evolution of galaxies is to
determine how gas is accreted onto galaxies and how it is
exchanged with their surroundings via outflows. Since ultimately the respective evolutions of gas, stars, and metals
are connected through the stellar life cycle, gas flows have
an immediate impact on the history of star formation (SF)
and the chemical enrichment. Inflows of pristine gas might
dilute the metal content of galaxies and certainly fuel their
SF, whereas outflows take away the metals, chemically enriching the circum-galactic medium (CGM). High column


⋆ E-mail: aklitsch@eso.org (A. Klitsch)


© 2017 The Authors



density gas lying along a quasar line of sight is an ideal
tool to study the CGM. These gas clouds characterized by
Ly α or metal absorption profiles can probe not only a static
CGM, but also flows of gas through the halo. To obtain a
full picture of the CGM and its interplay with galaxies, it is
important to study the location, kinematics, and metallicity
of both the absorbing gas and the nearby galaxy.
Using integral field spectroscopy (IFS) it is possible to
efficiently identify galaxies at the redshift of absorbers as
well as determine their star-formation rate (SFR), kinematics and metallicity (e.g. Bouch´e et al. 2007; P´eroux et al.
2011; Jorgenson & Wolfe 2014; P´eroux et al. 2017). Interestingly, recent studies have shown that the identification of
the Ly α absorber host galaxy is not always unique. In some

2 _A._ _Klitsch_ _et_ _al._


cases, the absorber can be linked to one galaxy, but in other
cases, it is associated with intra-group gas (Whiting et al.
2006; Kacprzak et al. 2010; Gauthier 2013; Rahmani et al.
2017; Bielby et al. 2017; Fumagalli et al. 2017; P´eroux et al.
2017).


Recent studies have shown that the CGM extends to
at least 100 kpc for isolated galaxies (Prochaska et al. 2017)
and 140 kpc in groupdf of galaxies (Bordoloi et al. 2011).
These distances convert to a radial angular extent of ∼ 20 [′′]

at intermediate redshifts of _z_ = 0.5 requiring a large field of
view integral field unit (IFU) such as MUSE to cover the
full potential extent of the CGM.


Large surveys aiming to understand the connection between absorption line systems and their host galaxies either
use galaxy-quasar pairs searching for absorption from the
known galaxy in the quasar spectrum (e.g. Tumlinson et al.
2013) or target known absorbers and search for the associated galaxies using integral field spectroscopy (e.g. Schroetter et al. 2016; Rahmani et al. 2017; Bielby et al. 2017; Fumagalli et al. 2017; P´eroux et al. 2017). Outflows are ubiquitously observed at all redshifts (e.g. Rupke et al. 2005;
Veilleux et al. 2005; Tremonti et al. 2007; Weiner et al. 2009)
while direct observations of inflows are less commonly found
(e.g. Martin et al. 2012; Bouch´e et al. 2013), possibly because they are more difficult to observe.


A completely new perspective is opened by studying
the molecular gas of the Ly α absorber host galaxy traced
by [12] CO emission lines. Recently, Neeleman et al. (2016) reported the first detection of [12] CO(1-0) emission from such
a host galaxy at _z_ = 0.101. Moreover, the combination of
12 CO emission line detections with IFS, potentially allows
us to get a complete census of the stars and the cool gas
in such systems. This is the next important step towards a
better understanding of such systems and therefore the flow
of baryons through galaxies.


In our new (sub)mm survey ALMACAL, we detect for
the first time multiple [12] CO transitions from a galaxy first
identified as an intervening absorber at _z_ abs = 0.633 towards
the quasar J0423−0130 ( _z_ QSO = 0.915). We have obtained additional MUSE observations revealing a group of four galaxies at the absorber redshift, where one of these is coincident
with the [12] CO emission seen in the ALMA observations. The

immediate aim of this study is to identify the origin of the
absorption seen towards the quasar. In a broader perspective, this system serves us as a reference system to demonstrate the need for a multi-wavelength study of intervening
absorbers and their environment.


This paper is organized as follows: In _§_ 2 we describe
our dataset from the ALMA archive, the new MUSE observations, the ancillary archival data and previous work. We
describe the source detections and measurements from the

ALMA and MUSE observations, the broad-band photometry based on archival data, and the analysis of the measurements in _§_ 3. In _§_ 4 we discuss possible scenarios explaining
the absorption. A summary and the conclusions are given
in _§_ 5. We present additionally morpho-kinematic modelling
and the fitting of the absorption lines in the quasar spectrum in the Appendix. Throughout the paper, we adopt an
H 0 = 70 km s [−][1] Mpc [−][1], Ω M = 0.3, and Ω Λ = 0.7 cosmology.



**Table** **1.** Summary of the used ALMACAL observations of

J0423−0130


Project code Date Scan Band 12 CO t exp
Intent Trans. [s]


2015.1.00920.S 09.01.2016 B 4 2−1 604.8

2015.1.00262.S 22.08.2016 B 4 2−1 728.5

2012.1.00350.S 04.12.2013 B 6 3−2 302.4

2013.1.00403.S 13.06.2014 B 6 3−2 302.4

2013.1.00111.S 05.07.2015 B 6  - 302.4

2013.1.01175.S 19.07.2015 B 6  - 605.8

2013.1.01175.S 19.07.2015 F 6  - 302.4

2013.1.01225.S 05.08.2015 B 6  - 302.4

2012.1.00146.S 28.05.2015 F 6  - 151.2

2015.1.00350.S 27.10.2015 B 6  - 302.4

2013.1.00198.S 06.06.2015 B 6  - 302.4

2013.1.01172.S 30.06.2014 B 6  - 483.8

2013.1.00815.S 28.06.2014 F 6  - 151.2

2013.1.00815.S 16.06.2014 B 6  - 604.8

2013.1.00710.S 12.12.2014 F 6  - 151.2

2015.1.00920.S 01.01.2016 B 6  - 302.4

2016.1.00724.S 27.12.2016 F 6  - 151.2

2016.1.00683.S 29.11.2016 F 6  - 151.2

2016.1.00627.S 03.12.2016 F 6  - 151.2

2016.1.00627.S 01.12.2016 F 6  - 302.4

2016.1.01453.S 22.11.2016 F 6  - 151.2

2016.1.01262.S 30.11.2016 F 6  - 151.2

2015.1.00296.S 22.06.2016 F 6  - 151.2


Note: Scan intent B denotes the bandpass calibrator, and F denotes the flux calibrator.


**2** **OBSERVATIONS** **AND** **DATA** **REDUCTION**


The aim of this work is to identify and characterize galaxies
connected to the intervening quasar absorber with a particular focus on the molecular gas content of the host galaxies.
To do this, we use ALMACAL, a novel wide and deep (sub-)
millimetre survey utilizing calibrator observations from the
ALMA archive (Oteo et al. 2016).
From our parent sample we have identified a particular absorber at _z_ = 0.633 towards the quasar J0423−0130
(04h23m15.8s −01d20m33s, _z_ = 0.915). The absorber is
a Lyman Limit System with an HI column density of
log( _N_ (HI)/ atoms cm [−][2] ) = 18.54 − [+] 0 [0] . [.] 10 [07] [.] [We] [choose] [this] [source]
for our pilot study, because we detect two [12] CO emission
lines in our ALMACAL data. We have obtained MUSE

follow-up observations of the field. We show that combining
these two datasets with other ancillary data yields a more
complete picture of such systems.


**2.1** **ALMACAL**


The data used in this work are taken from the ALMACAL

survey, a wide and deep survey utilizing the ALMA calibrator archive. The retrieval and calibration of the ALMA
calibrator data are described in detail by Oteo et al. (2016).
Up until 1. July 2017, the quasar J0423−0130 was observed four times at frequencies corresponding to possible
12 CO emission lines at the absorber redshift. Two observa
tions are available in Band 4 covering the frequency of the
redshifted [12] CO(2–1) emission line and two observations in
Band 6 covering the frequency of the redshifted [12] CO(3–2)
emission line. The details of these observations are given in


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 3

|QSO<br>J0423A<br>J0423B<br>J0423C<br>J0423D|Col2|
|---|---|
|||



3, 5, and 7σ levels in the respective mapdf, where negative contours are dashed. The galaxies identified to be at the absorber redshift

based on out MUSE and ALMA observations are marked with the yellow boxes, the quasar is marked with the black box. The galaxies 1
and 2 in Table 3 are not detected in our observations and therefore not shown in the figure and not considered in the analysis presented
here. The dashed large and small circles mark the ALMA half power beam width in Band 4 and Band 6, respectively. The small black
circles in the bottom left corner show the synthesized beams of the ALMA Band 4 and Band 6 observations which have a comparable
size. A zoom in on J0423B is shown in Fig. 3. The second OB of the MUSE observations was rotated by 5 [◦] with respect to the first OB
due to a technical problem.


**Table** **2.** Summary of the final J0423−0130 ALMA data cube properties.


Band Freq med. Ang. Res. r.m.s. ∆v PB

[GHz] [ [′′] ] [mJy beam [−][1] ] [km s [−][1] ] FWHM [ [′′] ]


4 141.166 0.43 0.28 66 48

6 211.742 0.70 0.37 44 27


MNRAS **000**, 1–17 (2017)

4 _A._ _Klitsch_ _et_ _al._


Table 1. The total integration time is 1333 s in Band 4 and
605 s in Band 6 for the observations covering the [12] CO emission lines. Furthermore, we use all well calibrated Band 6 observations that do not cover the [12] CO(3–2) emission line to
search for continuum emission. The corresponding datasets
are listed in Table 1.

We carry out the calibration and data reduction using the Common Astronomy Software Applications (CASA)
software package version 4.7. We examine each individual
dataset used for the emission line search first in the _u_ v plane
to apply further interactive flagging if necessary. We reduce
the spectral resolution to a maximum of 15.625 kHz. This
results in a velocity resolution of 33 km s [−][1] (and 66 km s [−][1]

after Hanning smoothing) for the Band 4 observations and
a velocity resolution of 22 km s [−][1] (and 44 km s [−][1] after Hanning smoothing) for the Band 6 observations. The spectral
resolution ensures that an emission line with a width of
≳ 300 km s [−][1] is covered by at least 5 and 7 channels in
the respective bands. Before the imaging, we concatenate
the two datasets in each band.

For the image cubes and the continuum image, the
imaging was done using the standard ‘clean’ algorithm. A
‘robust’ weighting scheme was applied, using a Briggs parameter of 0.5, which guarantees a nearly optimal sensitivity while still providing a high spatial resolution and a
well-behaved synthesized beam. In Band 4 we have two observations with a spatial resolution of 1.84 [′′] and 0.39 [′′] and
therefore we use an outer taper of 0.5 [′′] to prevent too high
a weighting of the higher resolution data. The final parameters of the image cubes are given in Table 2. The resulting mean r.m.s. noise level in Band 4 is measured to be
∼ 0.28 mJy beam [−][1] per 66 km s [−][1] and the median angular
resolution of the final data cube is ∼ 0.43 [′′] . The r.m.s. noise
level in the Band 6 image cube is ∼ 0.37 mJy beam [−][1] per
44 km s [−][1] and the median angular resolution of the final
data cube is ∼ 0.70 [′′] . The r.m.s. noise level in the 1.2 mm
continuum image is ∼ 96 mJy beam [−][1] km s [−][1] and the median angular resolution is ∼ 0.75 [′′] . We use a pixel size of
0.15 [′′] in the Band 4 image cube, 0.24 [′′] in the Band 6 image
cube covering the [12] CO(3–2) emission line and 0.15 [′′] in the
Band 6 continuum image cube.


**2.2** **New** **MUSE** **Observations**


We obtain Multi Unit Spectroscopic Explorer (MUSE) ob
−
servations in the field of J0423 0130 through Director’s Discretionary Time. Although the previously identified galaxies
from our ALMACAL observations and another galaxy identified in the broad-band imaging by Rao et al. (2011) are
located south of the quasar, we centre the field of view on
the quasar in order to not exclude a priori the possibility
to find a galaxy north of the quasar. The observations were
carried out in service mode under programme ESO 298.A5017 at the European Southern Observatory using MUSE
at the Nasmyth focus of the 8.2 m Very Large Telescope
UT4. Two “Observing Blocks” (OBs) were taken on the 23
and 24 December 2016. The field is rotated by 180 degrees
between these two OBs. The OBs are further divided into

two sub-exposures, with an additional rotation of 90 degrees
and a sub-arcsec dithering pattern. The exposure time of
each sub-exposure is 1405s with a seeing of 0.55 [′′] - 0.7 [′′]

resulting in a total exposure time of 5620 s. The spectral



coverage is ∼ 4800 – 9300 [˚] A. At the redshift of the absorber
( _z_ abs = 0.633) we, therefore, cover all emission lines between

[OII] and [OIII], but not H α.
We reduce the data with v1.6.1 of the ESO MUSE
pipeline and use the Zurich Atmosphere Purge (ZAP) code
for the sky subtraction (Soto et al. 2016). We use the master bias, master flat field and arc lamp exposures taken
closest in time to the science observations to correct the

raw data cubes. This is done with the scibasic recipe. We
do the correction to a heliocentric reference system using
the scipost recipe. In this step, we do not perform a skyremoval since ZAP is best performing on non-sky-subtracted
cubes. We check the wavelength solution using the position of the brightest sky lines and find it to be accurate to
10 km s [−][1] . The offset table is created for each cube by comparing the positions of point sources in the field using the
recipe ex ~~p~~ ~~a~~ lign. In the final step, the cubes are combined
using the recipe ex ~~p~~ ~~c~~ ombine. The seeing of the final cube
measured from the quasar and other point sources is 0.71 [′′]

at 7000 [˚] A. To ensure a precise astrometry, we match the position of the quasar with its high precision position known
from Very Long Baseline Array (VLBA) (Lanyi et al. 2010).
We remove the sky emission lines using the ZAP code
(Soto et al. 2016). To determine regions with pure sky emission a mask is created from the reconstructed white light
image. In this step, we set the flux levels accordingly to include bright objects in the mask. ZAP isolates the emission
lines caused by sky emission using a principle component
analysis and removes them from the data cube.
The quasar in this field is highly variable at optical
wavelengths and we do not cover any other standard star
with our field, so we estimate the flux error to be ±10% based
on our previous experience (Rahmani et al. 2017; P´eroux
et al. 2017).


**2.3** **Ancillary** **Data**


The target studied in this paper is the intervening metal line
absorber initially detected by Wills et al. (1980) as an FeII
and MgII absorber at _z_ abs = 0.6320 towards the quasar QSO
J0423−0130 ( _z_ QSO = 0.915).


_2.3.1_ _Early_ _Observations_


This system was observed by several authors using narrow-band [OII] filters
(Yanny et al. 1990; Yanny & York 1992) and broadband imaging (Churchill et al. 1996; Rao et al. 2011) to
determine the galaxy associated with the intervening
absorber. In total six systems were reported with an impact
parameter ≲ 200 kpc. However, no consensus was reached
on what is causing the absorption. The coordinates of these
galaxies are listed in Table 3.


_2.3.2_ _Quasar_ _Spectroscopy_


The strong FeII and MgII absorber was reobserved by
Churchill et al. (1996) as part of a program to study the
spatial and velocity distribution of absorbing systems with
known galaxy counterparts. The authors obtained a highresolution spectrum of J0423−0130 in January 1995 using


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 5


**Table** **3.** Summary of all previously detected galaxies connected to the absorber towards J0423-0130.


ID RA (J2000) Dec (J2000) θ [kpc] Previous Detection Ref. Detected in this Work


1 n.a. n.a. 14.7 broad-band Churchill et al. (1996) No
2 04 23 15.58 −01 20 34.6 24.7 broad-band Rao et al. (2011) No
3 04 23 16.18 −01 20 46.9 102 [OII] Yanny & York (1992), Yes     - J0423A
Rao et al. (2011)
4 04 23 16.07 −01 20 52.1 133 [OII] Yanny & York (1992) Yes     - J0423B
5 04 23 15.54 −01 20 54.0 146 [OII] Yanny & York (1992) Yes     - J0423C
6 04 23 15.30 −01 21 03.7 216 [OII] Yanny & York (1992) Yes     - J0423D


Note: For galaxy 1 Churchill et al. (1996) only report the impact parameter, but not the coordinates. Yanny & York (1992) do not give
the coordinates of the detected galaxies. Therefore, we match the galaxies with our observations and quote the coordinates based on this.



the HIRES echelle spectrometer (Vogt et al. 1994) on the
Keck 10m telescope. The spectral resolution is 6.6 km s [−][1] .
The absorber towards J0423−0130 was also part of
an MgII-FeII absorber sample, which was followed up by
Rao et al. (2006) using the _Hubble_ _Space_ _Telescope_ _(HST)_
_Space_ _Telescope_ _Imaging_ _Spectrograph_ _(STIS)_ spectrograph
in Cycle 9 (PID 8569). The HI column density was determined to be log( _N_ (HI)/ atoms cm [−][2] ) = 18.54 [+] − [0] 0 [.] . [07] 10 [.]


_2.3.3_ _Imaging_ _of_ _the_ _Field_ _of_ _J0423-0130_


Churchill et al. (1996) obtained broad-band imaging for the
field of J0423−0130 and reported a galaxy associated with
the absorber at an impact parameter of 14.7 kpc.
Furthermore, Rao et al. (2011) observed this field using the
MDM Observatory 2.4 m Hiltner telescope. They analysed
a 30 [′′] × 30 [′′] wide region of their images corresponding to
a field of view of 205 × 205 kpc at the absorber redshift.
The images were taken in the _B_, _R_, _I_, _J_, _H_, and _K_ bands.
The pdfF of the quasar was only subtracted in the optical
bands. Rao et al. (2011) performed a stellar population synthesis modelling for the five sources they detected within a
100 kpc radius around the quasar. It was found that only
one galaxy has a photometric redshift of _z_ = 0.637 ± 0.031
consistent with the absorber ( _z_ abs = 0.6331). The impact parameter of this galaxy is 14.5 [′′] or 99.6 kpc. Furthermore,
it was reported that another source might be at an impact
parameter of 3.6 [′′], which would translate to 25 kpc at the
absorber redshift. However, it was only visible in the infrared data and the spatial resolution prevented the isolation of the object from the quasar in these frames. Therefore, Rao et al. (2011) could not perform stellar population
synthesis modelling for this source. The coordinates of the
detected galaxies are given in Table 3. In the analysis we use
the broad-band images to obtain broad-band photometry of
the MUSE detected galaxies.


**3** **ANALYSIS**


**3.1** **ALMA** **Source** **Detection** **and** **Flux**

**Measurement**


We aim to detect [12] CO emission from galaxies connected
to the Lyman Limit System (LLS) at _z_ = 0.633. Thus, we
search for emission lines in the ALMA Band 4 and Band 6


MNRAS **000**, 1–17 (2017)






|Col1|12CO(2 1)<br>-|Col3|J0423B|Col5|
|---|---|---|---|---|
|0<br>2<br>4<br>6<br><br> density [|||||
|0<br>2<br>4<br>6<br><br> density [|||||


|-4 -2 0 2 4 6 8 10 12 Flux density [mJy] 12|-1000 -500 0 v [km 12CO(2-1)|500 1000 m/s] J0423B|Col4|
|---|---|---|---|
|0<br>2<br>4<br>6<br>8<br>10<br><br>x density [mJy]|_v_ ~~[km~~<br>12CO(3-2)|~~/s]~~<br>J0423B|~~/s]~~<br>J0423B|
|0<br>2<br>4<br>6<br>8<br>10<br><br>x density [mJy]|_v_ ~~[km~~<br>12CO(3-2)|~~/s]~~<br>J0423B||
|4<br>_−_2<br>Flu||||



_−_ 1000 _−_ 500 0 500 1000

_v_ [km/s]


**Figure** **2.** [12] CO(2–1) (top) and [12] CO(3–2) (bottom) emission
lines observed in our ALMACAL data cubes centred in position
on the quasar J0423-0130. The zero velocity corresponds to the
redshift determined from the respective [12] CO emission line. The
yellow region marks velocity range over which we integrate the
total flux. The dotted lines show the position of the main absorption component at a redshift of 0.633174. The peak in the [12] CO
emission line redshift corresponds exactly with that of the Lyman alpha absorption line, which signifies the clear association
between the absorption system and the [12] CO gas. The spectra
are binned to a resolution of 66 and 88 km s [−][1] for the [12] CO(2–1)
and [12] CO(3–2), respectively.


image cubes using the Source Finding Application ( `SoFiA` ) [1]

(Serra et al. 2015) that incorporates a number of different
source detection algorithms to find emission lines in radio
data cubes. We use the “Smooth + Clip Finder”, which uses
an algorithm developed by Serra et al. (2012). It smooths
the data in both spatial and spectral direction using a number of different 3D smoothing kernels. A search of emission
lines is performed on each smoothed cube by detecting spaxels above a user-defined threshold. The complete discussion


1 `[httpdf://github.com/SoFiA-Admin/SoFiA](httpdf://github.com/SoFiA-Admin/SoFiA)`

6 _A._ _Klitsch_ _et_ _al._


**Table** **4.** ALMA detection of the galaxy J0423B


Line z S peak S int L CO [′] FW H M

[mJy] [Jy km s [−][1] ] [×10 [−][10] K km s [−][1] pc [2] ] [km s [−][1] ]


12 CO(2–1) 0.63317 8.4 ± 0.7 3.6 ± 0.2 1.9 ± 0.1 590 ± 30
12 CO(3–2) 0.63335 10 ± 1 5.2 ± 0.3 1.2 ± 0.1 610 ± 40


**1.2mm** **continuum** **optical** **image**


**Figure** **3.** Zoom in on J0423B in Fig. 1. The 1.2 mm continuum emission is shown in grey scales on the left and the MUSE reconstructed
white light image is shown in grey scales on the right. In both panels we show the ALMA [12] CO(2–1) in red contours, ALMA [12] CO (3–2)

in cyan contours at 3, 5, 7 sigma of the respective mapdf overlaid. The ellipdfes in the lower left corner show the beam size in the Band 4
and Band 6 observations where the red ellipdfe corresponds to the beam in the [12] CO(2–1) line map, the cyan ellipdfe corresponds to
the beam in the [12] CO(3–2) emission line map and the black ellipdfe corresponds to the beam in the 1.2 mm continuum map. Negative
contours are marked with dashed lines, but are not present in this close-up.



of the relative strengths and weaknesses of all possible source
finding strategies is presented by Popping et al. (2012). We
chose the “Smooth + Clip Finder” since it offers the highest
completeness and reliability for finding sources on a variety
of scales. This is appropriate in our case since we do not
know a priori whether our sources are spatially resolved. We
use twelve smoothing kernels between 0.7 [′′] and 4.2 [′′] in the
spatial dimension and between 66 km s [−][1] and 990 km s [−][1]

for the Band 4 data cube and 44 km s [−][1] and 660 km s [−][1]


for the Band 6 data cube in the spectral dimension. The detection threshold is 4σ for both data cubes. We require the
detection to be within a range of ±2000 km s [−][1] relative to
the absorber redshift, because we are targeting [12] CO emission at the absorber redshift. We run the source finder on
the non-primary beam corrected cubes to ensure a constant
noise level throughout the cube.

Using the detection method described above, we find
12 CO(2–1) and 12 CO(3–2) emission at the same position
in the Band 4 and Band 6 cubes. We find no other emission lines which are detected in only one of the two data
cubes. The emission lines are shown as contours in Fig. 1.
The source is named J0423B throughout the paper. To our
knowledge, this is the first time that multiple [12] CO transitions have been observed from one galaxy associated with a
Ly α absorber. This allows us to investigate the properties
of the interstellar-medium in this galaxy.

We determine the size of the emission by fitting a twodimensional Gaussian function to the integrated intensity
mapdf. Here, we report the FWHM along the major axis



deconvolved with the beam. The size of the [12] CO(2–1) emission is 1.3 ± 0.2 [′′], the [12] CO(3–2) emission and the 1.2 mm
continuum emission are not resolved.

Before extracting the spectra, we perform a primary
beam correction on the image cube using impbcor to account for the primary beam response function. We note that
the primary beam correction at the position of our detected
12 CO lines in Band 6 is large because the 12 CO detection
lies at 19.4 [′′] from the centre of the field, and the Band 6
primary beam width is only 13.5 [′′] . We determine the redshift of the [12] CO emission lines from the mean of the two
frequencies at which the flux reached 50% of the maximum
flux density. The emission line spectra are shown in Fig. 2.
The flux is measured by integrating the spectra over
two times the FWHM indicated by the yellow shaded region
shown in Fig. 2. We have subtracted the continuum from the
image cube using the task imcontsub with a linear fit to the
spectrum. We determine the width of the line profiles from
the 50% level of the maximum flux density. The observed
line flux densities are converted to line luminosities using
the following equation (Solomon et al. 1992):


_D_ [2]
_L_ line [′] [=][ 3][.][25][ ×][ 10] [7] [ ×] _[ S]_ [line] [∆][v] L K km s [−][1] pc [2], (1)
(1 + _z_ ) [3] _f_ obs [2]


where _S_ line ∆v is the observed velocity integrated line
flux density in Jy km s [−][1], _D_ L is the luminosity distance to
the galaxy in Mpc, and _f_ obs is the observed line frequency
in GHz. A summary of the emission line properties is given
in Table 4. We estimate the error of the integrated line flux


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 7



to be 5% based on the expected accuracy of the flux calibration. The FWHM of the [12] CO emission lines is within the

observed range for star-forming dusty galaxies at _z_ < 0.35
(Villanueva et al. 2017). The projected impact parameter between the [12] CO detection and the quasar sight line is 133 kpc
and the position of the [12] CO detection is aligned with that of
one of the galaxies detected in the MUSE cube. We discuss
this in more detail in Section 3.2.

Furthermore, we combine all Band 6 observations from
ALMACAL to search for continuum emission from the

CO-detected galaxy. Hence, we can compare the total farinfrared luminosity based SFR with the SFR based on the
dust-uncorrected [OII] emission line flux. We show in Fig. 3
(left) the Band 6 continuum map with the [12] CO (2–1) and
12 CO (3–2) emission line contours overplotted. We exclude
any contamination from the [12] CO(3-2) emission line by excluding the datasets covering the relevant frequency. The
total flux density at 1.2 mm is (0.8 ± 0.2) mJy and the peak
intensity is (0.56 ± 0.09) mJy beam [−][1] .
Finally, we explore the possibility to observe molecular absorption lines towards the quasar in our Band 4 and
Band 6 observations. The 3σ detection limit for the integrated optical depth is 0.01 km s [−][1] and 0.003 km s [−][1] for
12 CO (2–1) and 12 CO (3–2), respectively. We note, however, that the velocity resolution is very coarse and might
be not sufficient to detect absorption lines.


**3.2** **MUSE** **Source** **detection** **and** **Flux**

**Measurement**


We blindly search for line and continuum emission from
galaxies in our MUSE cube. To this end, we search for emission line and continuum sources using the MUSELET source
finding algorithm included in MPDAF [2] . MUSELET runs
SExtractor (Bertin & Arnouts 1996) on each 1.25 [˚] A-wide
slice of the cube to find any source of emission. We detect 50
emission line sources and continuum sources in the MUSE

cube with this method. The galaxies at the absorber redshift
( _z_ = 0.633) are selected based on two criteria: 1) searching
for emission line sources, and 2) by searching for the 4000 [˚] A
break at the rest frame of the absorber in all 50 spectra. We
find four emission line sources at the absorber redshift, but
we do not detect continuum sources at the absorber redshift.

The full spectra of the four emission line galaxies are shown
in Fig. 4. In Fig. 1 we mark the positions of these galaxies:
J0423A, J0423B, J0423C and J0423D.
We determine the redshift of the galaxies by fitting a
Gaussian to the detected emission lines. Since we detect

multiple lines for all galaxies, we determine the redshift of
each galaxy as the median redshift from the Gaussian fit to
the detected lines. The respective redshifts and emission line
fluxes are shown in Table 5. We do not detect [OIII]4959A [˚]
for any of our galaxies and therefore give only upper limits
on the line flux. This is consistent with the expected line-flux
assuming a doublet flux-ratio of 3 (Storey & Zeippen 2000).
Furthermore, we detect H β in only two of the galaxies. The
given upper limits are calculated from a maximum emission
of 3σ and the FWHM measured from the sky emission lines


2 http://mpdaf.readthedocs.io/en/latest/


MNRAS **000**, 1–17 (2017)



corresponding to 3 [˚] A. The line width of the detected lines
determined from the Gaussian fitting is listed in Table 5.
In Fig. 3 (right) we show a comparison of the ALMA
collapdfed [12] CO emission line map and the MUSE pdfeudowhite-light image. It can be seen that the [12] CO gas is coincident with the optical position of galaxy J0423B. No emission from the other MUSE-detected galaxies is found in the
ALMA cubes. Furthermore, comparing the FWHM of the

[OIII] lines and the [12] CO emission lines, we find that the
molecular gas disk seems slightly more extended than the
ionized gas.


**3.3** **Broad-band** **Photometry** **and** **Stellar** **Mass**


We estimate the stellar mass of the four galaxies, to infer
the molecular gas mass ratio of J0423B and determine the
total dynamical mass of the group. For this purpose, we
use the broad-band imaging from Rao et al. (2011) to measure the broad-band photometry which we use as input for
the spectral energy distribution (SED) fitting. The apparent magnitudes of the detected galaxies are determined using
SExtractor and are listed in Table 5.

This broad-band photometry is used as
input for the SED fitting with Le Phare [3]

(Arnouts et al. 1999; Ilbert et al. 2006) to estimate the
stellar masses of the galaxies. To perform the SED fitting
the algorithm compares the observed colours with the
ones predicted from a set of template SEDs. We fix the
redshift for the SED fitting to the spectroscopic redshift
determined from our MUSE spectra described in Section
3.2. The template SEDs are convolved with standard _B_,
_R_, _I_, _J_, _H_, and _K_ filter functions and a χ [2] minimization
is performed. We quote the stellar mass of the galaxies in
Table 6. Comparing our stellar masses to the galaxy stellar
mass function at redshift 0.4 < _z_ < 0.6 and 0.6 < _z_ < 0.8 for
which Drory et al. (2009) report a log(M [⋆] ) of 10 [10][.][91][−][10][.][95],
we find that the CO-detected, most massive galaxy J0423B
has a stellar mass of almost 2 M [⋆], while the other galaxies
J0423A, J0423C and J0423D have stellar masses below M [⋆] .


**3.4** **Molecular** **Gas** **Mass**


Until now the molecular gas content of galaxies associated
with intervening Ly α absorbers has been determined only
once (Neeleman et al. 2016). We combine the molecular gas
mass with the stellar mass from the SED fitting to determine
a census of the molecular gas and stars in galaxies associated
with intervening absorbers. In the following, we determine
the molecular gas mass using the two [12] CO emission lines.
We use the following conversion:


_M_ mol = α CO × _L_ CO [′] (1−0) [,] (2)


where _L_ CO [′] (1−0) [is] [the] [luminosity] [of] [the] [12] [CO(1-0)] [emis-]
sion line and the conversion factor α CO depends on the temperature, density, metallicity, and column density of the interstellar medium.


3 `[http://www.cfht.hawaii.edu/~arnouts/lephare.html](http://www.cfht.hawaii.edu/~arnouts/lephare.html)`

8 _A._ _Klitsch_ _et_ _al._


**Table** **5.** Observed properties of the galaxies from the MUSE observation and the broad-band imaging.


Name J0423A J0423B J0423C J0423D


Ra (J2000) 04 23 16.18 04 23 16.07 04 23 15.54 04 23 15.30
Dec (J2000) −01 20 46.9 −01 20 52.1 −01 20 54.0 −01 21 03.7
θ [ [′′] ] 14.9 19.4 21.3 31.6
θ [kpc] 102 133 146 216
z 0.6332 ± 0.0005 0.6331 ± 0.0005 0.6338 ± 0.0003 0.6323 ± 0.0005
Line Width σ([OII]) 170 ± 10 220 ± 10 170 ± 10 140 ± 10
FWHM([OII]) 400 ± 20 520 ± 30 390 ± 30 330 ± 30
σ([H β]) 120 ± 50              - 120 ± 40              FWHM([H β]) 290 ± 110           - 290 ± 90           σ([OIII]5007 [˚] A) 150 ± 20 170 ± 30 160 ± 40 70 ± 20
FWHM([OIII]5007 [˚] A) 360 ± 50 400 ± 70 380 ± 90 160 ± 40
Line Fluxes

[10 [−][17] erg s [−][1] cm [−][2] ] [OII] 5.3 ± 0.5 11.0 ± 1.1 3.6 ± 0.4 3.0 ± 0.3
H β 1.7 ± 0.2 < 0.9 1.7 ± 0.2 < 2

[OIII] 4959 < 0.9 < 1 < 0.6 < 1

[OIII] 5007 2.1 ± 0.2 2.9 ± 0.3 1.3 ± 0.1 2.2 ± 0.2
B [mag] 23.8 ± 0.4 25.2 ± 0.5 24.6 ± 0.3 < 25.82
R [mag] 22.10 ± 0.18 21.68 ± 0.18 22.72 ± 0.15 23.75 ± 0.17
I [mag] 21.0 ± 0.3 20.0 ± 0.2 21.8 ± 0.2 < 25.15
J [mag] 20.43 ± 0.12 19.64 ± 0.09 20.90 ± 0.13 21.67 ± 0.11
H [mag] 19.83 ± 0.19 18.91 ± 0.12 20.3 ± 0.2 20.90 ± 0.19
K [mag] 19.87 ± 0.13 18.78 ± 0.08 20.34 ± 0.15 20.80 ± 0.11


Note: θ is the impact parameter given here in [′′] and kpc.



To apply the above mentioned conversion to the total
molecular gas mass, we need to convert the [12] CO(2–1) line
flux to the [12] CO(1-0) line flux using a suitable conversion
factor. The ratio of _L_ CO [′] (3−2) [/] _[L]_ CO [′] (2−1) [is] [0][.][63][ ±][ 0][.][09] [suggest-]

ing a [12] CO excitation ladder similar to that of a Luminous
Infrared Galaxy (LIRG) (Papadopoulos et al. 2012a). We
note that this value is also consistent with the expected
ratio of 0.54 for Milky Way-type galaxies (Carilli & Walter
2013). However, based on further evidence presented in
Sec. 4.1 we believe that the LIRG-type conversion factor
is more appropriate. Therefore, we adopt a conversion
factor of _L_ CO [′] (2−1) [/] _[L]_ CO [′] (1−0) [=][ 0][.][9][,] yielding an _L_ CO [′] (1−0)
of (2.1 ± 0.1) × 10 [10] K km s [−][1] pc [2] . Furthermore, we use
α CO = 0.6M⊙(K km s [−][1] pc [2] ) [−][1], appropriate for LIRGs
derived by Papadopoulos et al. (2012b) including a factor
of 1.36 to account for the presence of helium. This yields a
molecular gas mass of _M_ mol = (1.27 ± 0.07) × 10 [10] M⊙. To indicate the uncertainty in the derived H 2 mass, we also apply
a conversion factor of α CO = 4.3M⊙(K km s [−][1] pc [2] ) [−][1] typical
for Milky Way-type galaxies and including a factor of 1.36
to account for the presence of helium (Bolatto et al. 2013).
This yields a molecular gas mass 9 × 10 [10] M⊙ and so we
adopt a molecular gas mass of 1 − 9 × 10 [10] M⊙.


We have also extracted spectra from our ALMA cubes
at the positions of J0423A and J0423C, but we could not find
any clear sign of emission. For these two galaxies, we calculate upper limits for _L_ CO [′] (2−1) [based on the][ 3][σ] [noise level and]

assuming a width of the line of 500km s [−][1] based on the w 50
measured from the [12] CO detections for J0423B. This yields
an upper limit for the integrated flux of _S_ int = 0.4 Jy km s [−][1],
assuming that the flux is evenly distributed over the full
width of the profile. Therefore, the upper limit on the line
luminosity of _L_ CO [′] (2−1) [is] [2][ ×][ 10] [9] [K km s] [−][1] [pc] [2] [.] [We] [assume] [a]



Milky Way-type _L_ CO [′] (2−1) [/] _[L]_ CO [′] (1−0) [emission] [line] [ratio] [of] [0][.][5]
(Carilli & Walter 2013) and a Milky Way-type CO-to-H 2
conversion factor of α CO = 4.3M⊙(K km s [−][1] pc [2] ) [−][1] including a factor of 1.36 to account for the presence of helium (Bolatto et al. 2013). This yields an upper limit for the
molecular gas mass of _M_ mol < 1.7 × 10 [10] M⊙ for J0423A and
J0423C.


**3.5** **Star-Formation** **Rates**


We determine the SFR of the CO-detected galaxy J0423B
to test whether it is comparable with the identification of a
LIRG based on the CO line flux ratios.
We estimate the SFR of J0423B based on the 1.2 mm

flux. We use a set of template spectra for starburst galaxies
from Polletta et al. (2007) which we scale to the observed
1.2 mm flux converted to the rest wavelength. The fitted
spectrum is then integrated in the wavelength range from
8 - 1000 µm to obtain the total far-infrared luminosity _L_ FIR .
This is converted to the SFR using the Kennicutt (1998)
relation:


_SFR_ FIR = 4.5 × 10 [−][44] _L_ FIR (3)


based on this, we estimate a SFR of (50 ± 10) M⊙ yr [−][1] .
We note, however, that the uncertainty in this calculation
is high since we use the median SFR from a set of template
spectra which we scale to the flux at 1.2 mm.
Furthermore, we derive the SFRs for the remaining
three emission line galaxies based on the [OII] emission line
using the relation given by Kennicutt (1998), which includes
a dust correction:


_SFR_ [OII] = (1.4 ± 0.4) × 10 [−][41] _L_ ([OII]) × 10 [0][.][4A] [[][OII][]] . (4)


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 9


2500

















3800 4000 4200 4400 4600 4800 5000
Rest wavelength [ A] [˚]


**Figure** **4.** Rest frame optical spectra of the four group members identified from our MUSE observation (offset by an arbitrary number
for clarity). The spectra are shifted to rest wavelength using the redshift determined from the emission lines quoted in Table 5. The
grey area marks the regions possibly contaminated by telluric absorption and emission. The strongest emission line in all spectra is [OII]
at λ = 3727 [˚] A. The dashed-dotted line marks with increasing wavelength the [OII], H β, [OIII]4959 [˚] A, and [OIII]5007A [˚] emission line.
The dotted lines mark the Balmer absorption lines from H γ to H 12 with decreasing wavelength. The dashed lines mark the Ca H&K
absorption lines. We note, that the features at the [OIII]4959A [˚] and H β wavelength in J0423D as well as the narrow feature at the

[OIII]4959A [˚] wavelength in J0423A are marginal given the SNR of the spectrum.



where _A_ [OII] is the extinction of the [OII] emission line.
We determine the dust correction based on the stellar mass
dependent _A_ H α given by Garn & Best (2010) at _z_ ∼ 0.1,
which is found to be valid up to _z_ ∼ 1.5 (Sobral et al. 2012).
To convert the _A_ H α to _A_ [OII] we use the prescription given
by Calzetti (1997). The resulting dust-corrected SFRs are
given in Table 6.


To test the identification of J0423B being a LIRG, we
calculate the dust-uncorrected SFR based on the [OII] emission line for a comparison with the infrared based SFR. We
derive a SFR of 2.7 ± 0.3 M⊙ yr [−][1] from the [OII] emission.
This is 13 - 25 times lower than the SFR inferred from the

far-infrared luminosity. This is in the lower envelope of the
population of very luminous infrared galaxies studied by
(Poggianti & Wu 2000). This is a further piece of evidence
that J0423B is a LIRG.


We determine the limiting SFR for our MUSE observations based on the detection limit of the [OII] line to infer
the maximum SFR of potential galaxy candidates below our
detection limit. The mean r.m.s. noise in the MUSE cube
around the [OII] emission line is measured from the cube
with a velocity width of 865 km s [−][1] . We perform a 3σ clipping on this cube and another 3σ clipping on the clipped
cube to remove any contribution from actual emission. The


MNRAS **000**, 1–17 (2017)



mean r.m.s. noise is then determined from this emission-free

cube. Furthermore, we assume, that the minimum size of a
galaxy is given by the seeing of 0.7 [′′], which corresponds to
4.8 kpc at the absorber redshift and the FWHM of the line
is at least 3 [˚] A. The resulting [OII] flux would be 0.3 × 10 [−][17]

erg s [−][1] cm [−][2] . This converts into a 3σ limiting SFR of
0.2 M⊙ yr [−][1] . Additionally, we determine the limiting SFR
at the quasar position. Therefore, we extract a 2 [′′] × 2 [′′] wide
cube at the position of the quasar with a width of 865 km s [−][1]

centred on the expected [OII] emission line covering all the
observed [OII] emission. The emission from the quasar is
determined by a linear fit and removed from the data cube.
The limiting SFR at the position of the quasar is calculated
from the noise in the continuum subtracted cube and assum
ing the same emission properties as described above. This
yields a non-dust-corrected limiting SFR of 0.3 M⊙ yr [−][1] .


**4** **DISCUSSION**


**4.1** **The** **Nature** **of** **the** **galaxy** **J0423B**


Galaxy J0423B is detected in [12] CO(2–1) and the [12] CO(3–2)
as well as our MUSE observations. Here we collect all this

information and discuss the nature of this galaxy. In _§_ 3.4 it

10 _A._ _Klitsch_ _et_ _al._


**Table** **6.** Summary of the physical properties of the galaxies at the absorber redshift based on our MUSE data and the SED fitting.


Name z SFR log M ⋆ 12 + log(O/H)

[M⊙ yr [−][1] ] [M⊙]


J0423A 0.63317 ± 0.00048 7.5 ± 0.6 10.4 ± 0.2 8.80 ± 0.10 [a]

J0423B 0.63312 ± 0.00048 50 ± 10 11.2 ± 0.1 9.1 ± 0.9 [b]


J0423C 0.63376 ± 0.00032 4.6 ± 0.5 10.3 ± 0.2 8.94 ± 0.06 [a]

J0423D 0.63229 ± 0.00048 3.2 ± 0.5 10.2 ± 0.2 9.0 ± 0.9 [b]


Note: The SFRs of J0423A, J0423C, J0423D reported in this table are based on the [OII] emission line and are dust corrected. The
SFR of J0423B is derived from L FIR . The metallicity [a] is determined from the emission lines and the metallicity [b] is derived from the
mass-metallicity relation.


quasar point spread function.

22



20


18


16


14


12


0 50 100 150 200

b [kpc]


**Figure** **5.** Column density of the intervening absorber as a function of impact parameter from J0423B (red star), DLAs from
Zwaan et al. (2005) (black triangles) and P´eroux et al. (2011)
(blue circles) and subDLAs and LLS from the COS halos survey (Prochaska et al. 2017) (green triangles).


is shown that the ratio of the [12] CO(2–1) and the [12] CO(3–
2) emission line is consistent with J0423B being a LIRG.
Furthermore, the SFR based on _L_ FIR reported in _§_ 3.5 is
50±10 M⊙ yr [−][1] . We compare this to the SFR from the dustuncorrected [OII] line flux, which is 13 - 25 times lower. This
is in the lower envelope of the very luminous infrared galaxy
population studied by Poggianti & Wu (2000). Combining
these pieces of evidence we conclude that J0423B is a LIRG.


**4.2** **Assessing** **the** **Possibility** **of** **a** **Misidentification**


The fact that we only detect galaxies at large impact
parameters from the quasar sight-line raises the question
whether an undetected galaxy hiding in the bright quasar
light could be responsible for the absorption. Interestingly,
Churchill et al. (1996) report a galaxy at an impact parameter of 2.1 [′′] or 14.6 kpc and Rao et al. (2011) report another
galaxy at an impact parameter of 3.6 [′′] or 25 kpc. We do not
detect either of these galaxies in our data. In addition, these
objects are not seen in quasar pdfF-subtracted archival
HST/NICMOS images (PID 7451). We determine the
non-dust-corrected limiting SFR of 0.2 M⊙ yr [−][1] over the
full field of view and 0.3 M⊙ yr [−][1] in a 2 [′′] × 2 [′′] wide field
centred on the position of the quasar. We take this as the
upper limit on the SFR of an undetected galaxy within the



We compare the HI column density of the absorber and
the impact parameter of the most massive group member
with the column density - impact parameters observed for
DLAs (Zwaan et al. 2005; P´eroux et al. 2011) and subDLAs
and LLS from the COS Halos survey (Prochaska et al. 2017)
in Fig. 5. Assuming that J0423B can be uniquely associated
with the Ly α absorption line, we see it is in the upper
envelope of the relation between impact parameter and column density, but not atypical compared to other identified
galaxy-absorption line pairs from the literature. This lessens
the immediate need for another galaxy at a smaller impact
parameter.


**4.3** **The** **Nature** **of** **the** **Absorbing** **Gas**


Here, we discuss the possibility that the absorbing gas is
tracing an outflow or intra group medium.
We consider whether the gas seen in absorption could be
related to an outflow from one of the identified galaxies. In
this galaxy group an outflow is most likely starburst-driven
and would, therefore, originate from J0423B. This is further
supported by the morpho-kinematic properties of the galaxies studied in _§_ A. If we assume that the outflow of gas from
galaxies is most efficient along the minor axis theoretically
predicted by Kereˇs et al. (2009); Stewart et al. (2011) and
empirically motivated by recent studies (e.g. Bordoloi et al.
2011; Bouch´e et al. 2012; Schroetter et al. 2015) the best
candidate having an outflow that could be probed by the
absorption is J0423B. Furthermore, we assume a constant
typical velocity of a galactic wind in a star-forming galaxy
of 300 km s [−][1] (Veilleux et al. 2005). This yields a travel time
of ∼ 430 Myr from J0423B to the position where we see
the absorption. Recently, first attempts in theoretical modelling were made to understand how a cool outflow can be
produced (Richings & Faucher-Giguere 2017).
Another explanation for the gas seen in absorption
could be that it is tracing the intra-group medium. The
MUSE observations revealed four galaxies at the absorber
redshift, which is an over-density compared to the total redshift range. We expect based on the [OII] luminosity function given by Ly et al. (2007) 0.05 galaxies above the limiting SFR within the MUSE field of view in a redshift range
covered by the galaxy group. Therefore, we finally consider
whether the gas seen in absorption against the background
quasar is probing the CGM of the group of galaxies that
we identify to be close in redshift space and in projected
separation. We compare the alignment of the galaxies and


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 11



1 _._ 2


1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0


15

|ensity[mJy]<br>10<br>5|Col2|J0423B:<br>CO(21)<br>-,<br>CO(32)<br>-|Col4|Col5|
|---|---|---|---|---|
|0<br>Flux d|||||



700

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|0<br>100<br>200<br>300<br>400<br>500<br>lux density<br>20 erg cm_−_2 s||J0423A:<br>[OII]|J0423A:<br>[OII]||
|0<br>100<br>200<br>300<br>400<br>500<br>lux density<br>20 erg cm_−_2 s|||||



1200


600

|Col1|Col2|J0423C:|Col4|
|---|---|---|---|
|0<br>100<br>200<br>300<br><br>lux densit<br>0 erg cm_−_2||[OII]||
|0<br>100<br>200<br>300<br><br>lux densit<br>0 erg cm_−_2||||



500





the absorber in velocity space. In Fig. 6 we show the position of the absorber, the [12] CO detections from the ALMA
observations and the ionized gas detected with MUSE in velocity space with respect to the absorber redshift. We find
that all galaxies align well with the absorber, where J0423C
is redshifted by 200 km s [−][1] and J0423D is blueshifted by
−250 km s [−][1] with respect to the absorber systemic velocity.
This could indicate that the quasar absorption line probes
the intra-group gas rather than the CGM of a single galaxy.
Intervening absorbers are often found to trace intra-group
gas at low redshift (Whiting et al. 2006; Kacprzak et al.
2010; Gauthier 2013; Rahmani et al. 2017; Bielby et al.
2017; Fumagalli et al. 2017; P´eroux et al. 2017). In these
cases the velocity width of the absorption ranges from less
than 100 km s [−][1] to more than 600 km s [−][1] . At this stage, we
cannot distinguish intra-group gas from CGM based on this
property.
The spatial extent of the CGM in group galaxies is reported to be more than 140 kpc and the intra-group gas can
be even more extended (Bordoloi et al. 2011).
As an illustration, we compute an estimate of the dynamical mass of the group and the radius of the zero-velocity
surface. To calculate the dynamical mass, we use the ‘projected mass estimator’ (Heisler et al. 1985) defined by:



8 _GT_ 2
_R_ 0 = _M_ dyn
� π [2]



32/π
_M_ PM =
G( _N_ m − 1.5)



� v i [2] _[r]_ [i] [,] (5)

i



where G is the gravitational constant, _N_ m is the number
of observed group members, v i is the velocity of the group
member _i_ with respect to the group mean velocity and _r_ i
is the projected distance of the group member _i_ from the
group centre. Here we define the most massive galaxy as
the group centre since we cannot be sure that all group
members are observed. This yields a dynamical mass of
the group of 10 [12][.][9] M⊙. Furthermore, we compute the radius of the zero-velocity surface, _R_ 0, defined as the surface
beyond which galaxies participate in the Hubble expansion
(Sandage 1986). It is derived as follows:



1/3
, (6)
�



_−_ 100

|s−1]<br>400<br>Fluxdensity<br>300 cm−2<br>200<br>g<br>100 er<br>10−20<br>0|Col2|Col3|Col4|J0423D:<br>[OII]|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|0<br>100<br>200<br>300<br>400<br><br>Flux density<br>10_−_20 erg cm_−_2 s_−_1]|0<br> <br>10_−_|||||||


_−_ 600 _−_ 400 _−_ 200 0 200 400 600

Velocity [km s _[−]_ [1] ]


**Figure** **6.** Comparison of all detected systems from top to bottom: MgII absorption in the quasar spectrum from the HIRES
spectrum, [12] CO(2–1) (blue) and [12] CO(3–2) (red) from J0423B
from ALMACAL, the continuum subtracted [OII] emission line
spectra from J0423A, J0423B, J0423C and J0423D all plotted
relative to the absorber redshift. We stress that the width of the
12 CO and [OII] emission lines cannot be directly compared in this
plot since the [OII] emission line doublet is not resolved in the
MUSE observations.


MNRAS **000**, 1–17 (2017)



where _T_ is the age of the group. We assume that the
age of the group is 7.5 Gyr, which is the age of the universe
at the redshift of the group. This yields a radius of the zerovelocity surface of 1.2 Mpc. The gas that is probed by the
Ly α absorption is well within this radius.
Furthermore, it is well known from nearby interacting
groupdf that the group galaxies can be embedded in a largescale atomic gas reservoir (Yun et al. 1994).


**5** **SUMMARY** **AND** **CONCLUSION**


In this case study of a Lyman Limit System at _z_ = 0.633,
we show the power of combining observations of the cool
ionized gas with MUSE and ALMA observations of the
12 CO emission lines tracing the molecular gas in galaxies
connected with a Ly α absorber. We measure two rotational
transitions of the [12] CO line in emission, corresponding to
a galaxy at the same redshift as the Ly α absorption line.

12 _A._ _Klitsch_ _et_ _al._


This allows us to determine the molecular gas mass, as well
as to put constraints on the ISM properties of this galaxy.
We can efficiently identify star-forming galaxies at the
absorber redshift using additional optical IFU observations.
With these observations, we can probe the cool ionized
gas in the galaxies and study their morpho-kinematics.
In combination with the observations of the neutral gas
probed in absorption, the observations of the cool ionized
and molecular gas offer a complete census of the cool gas,
which is needed to gain a better understanding of what
types of galaxies are probed by Ly α absorbers.


In the particular system presented in this study
we find a group of massive galaxies with masses
of M ⋆ = 10 [10][.][3][−][11][.][2] M⊙ connected to a LLS with
log( _N_ (HI)/atomscm [−][2] ) = 18.54 [+] − [0] 0 [.] . [07] 10 [at a redshift of] _[ z]_ [=][ 0][.][633][.]
The impact parameter between the quasar sightline and the
closest galaxy is 102 kpc and 133 kpc for the most massive galaxy. No other galaxy is detected closer to the quasar
down to a dust-uncorrected limiting SFR of 0.2 M⊙ yr [−][1] in
the field and 0.3 M⊙ yr [−][1] at the quasar position. For the
three lower mass galaxies, we find a dust corrected SFR of
3 M⊙ yr [−][1] < SFR < 7.5 M⊙ yr [−][1] and for the most massive galaxy we find a SFR based on the total far-infrared
luminosity of (50 ± 10) M⊙ yr [−][1] .
The most massive galaxy is also detected in our ALMA
12 CO(2–1) and 12 CO(3–2) observations, from which we derive a molecular gas mass of M H2 = 1 − 9 × 10 [10] M⊙. We infer
that this galaxy is likely to be a LIRG based on the emission
line ratios as well as the ratio of the far-infrared based SFR

and the dust-uncorrected SFR based on the [OII] emission
line flux. This is the first time that multiple [12] CO transitions
are observed from one galaxy connected to a Ly α absorber.
For the other galaxies in the field we determine an upper
limit of M H2 < 17 × 10 [9] M⊙.
We are able to model the morpho-kinematics of the
three closest galaxies. As presented in A, all three galaxies
have velocity fields consistent with a rotating disk. Moreover,
we construct a line of sight velocity map from the [12] CO(2–
1) emission line for J0423B. It is found that the velocity
field from the cool ionized gas and the molecular gas are
comparable.
We explore different explanations for the neutral gas
probed in absorption.


 - Another galaxy could be closer to the line of sight towards the quasar, that is not seen in our observations. The
limiting dust-uncorrected SFR in our MUSE data cubes is
0.2 M⊙ yr [−][1] in the field and 0.3 M⊙ yr [−][1] at the position of
the quasar. At this low SFR, the galaxy is unlikely to have
an outflow and therefore it must be close to the quasar line
of sight and the absorption is actually probing the ISM of
this galaxy. We note that we cannot rule out this possibility
completely, but we emphasize that our MUSE observations
reach a higher completeness compared to previous studies
using broad-band imaging.

 - The neutral gas could be tracing an outflow from the
most massive galaxy J0423B since the quasar line of sight is
aligned with the minor axis of the galaxy. We estimate, that
for a constant outflow speed of 300 km s [−][1] it would take
the gas 400 Myr to travel to the position of the absorber.
However, the question remains how the gas can stay cool



in the outflow or whether it can cool at larger distances.
Furthermore, outflows of neutral gas are not yet observed at
such large distances.

 - The impact parameter of 133 kpc for the most massive
galaxy is comparable with the spatial extent of the intragroup gas quoted by Bordoloi et al. (2011). Moreover, recent studies frequently find intervening absorbers probing
the intra-group gas. We argue that this is, apart from an undetected galaxy closer to the quasar-line-of-sight, the most
probable explanation for the gas traced by the absorption.


Finally, finding multiple galaxies at the absorber redshift adds further evidence to the findings by Whiting et al.
(2006); Kacprzak et al. (2010); Gauthier (2013); Rahmani
et al. (2017); Bielby et al. (2017); Fumagalli et al. (2017);
P´eroux et al. (2017) suggesting that the classical picture of
a one to one correlation between a Ly α absorber and the
host galaxy is incomplete and needs to be revised.


**ACKNOWLEDGEMENTS**


We thank the anonymous referee for a constructive report.
The authors thank Chris Churchill for kindly providing
us with the reduced HIRES spectrum of the quasar and
Sandhya Rao for kindly providing us with the broad band
images. We also thank Nicolas Bouch´e for his advice on the
morpho-kinematic modelling using Galpak [3D] . The authors
thank Hadi Rahmani for useful discussion about intra-group
medium. We are grateful to the ESO staff at Paranal and in
Garching for performing the MUSE observations in service
mode. AK acknowledges support from the STFC grant
ST/P000541/1 and Durham University. CP was supported
by an ESO science visitor programme and the DFG cluster
of excellence ‘Origin and Structure of the Universe’. IRS
acknowledges support from the ERC Advanced Grant
DUSTYGAL (321334), a Royal Society/Wolfson Merit
Award and STFC (ST/P000541/1). IO acknowledges
support from the European Research Council in the form of
the Advanced Investigator Programme, 321302, cosmicism.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2015.1.00920.S,
ADS/JAO.ALMA#2015.1.00262.S,
ADS/JAO.ALMA#2012.1.00350.S,
ADS/JAO.ALMA#2013.1.00403.S.
ADS/JAO.ALMA#2013.1.00111.S,
ADS/JAO.ALMA#2013.1.01175.S,
ADS/JAO.ALMA#2013.1.01175.S,
ADS/JAO.ALMA#2013.1.01225.S,
ADS/JAO.ALMA#2012.1.00146.S,
ADS/JAO.ALMA#2015.1.00350.S,
ADS/JAO.ALMA#2013.1.00198.S,
ADS/JAO.ALMA#2013.1.01172.S,
ADS/JAO.ALMA#2013.1.00815.S,
ADS/JAO.ALMA#2013.1.00815.S,
ADS/JAO.ALMA#2013.1.00710.S,
ADS/JAO.ALMA#2015.1.00920.S,
ADS/JAO.ALMA#2016.1.00724.S,
ADS/JAO.ALMA#2016.1.00683.S,
ADS/JAO.ALMA#2016.1.00627.S,
ADS/JAO.ALMA#2016.1.00627.S,
ADS/JAO.ALMA#2016.1.01453.S,
ADS/JAO.ALMA#2016.1.01262.S,


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 13



ADS/JAO.ALMA#2015.1.00296.S,
ADS/JAO.ALMA#2013.1.01175.S,
and ADS/JAO.ALMA#2012.1.00650.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with
NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ. This work makes use of observations made with the NASA/ESA Hubble Space Telescope, or obtained from the data archive at the Space Telescope Institute (STScI), which is a collaboration between
STScI/NASA, the Space Telescope European Coordinating
Facility (STECF/ESA) and the Canadian Astronomy Data
Centre (CADC/NRC/CSA). This research made use of Astropy, a community-developed core Python package for Astronomy (Astropy Collaboration et al. 2013).


**REFERENCES**


Amorisco N. C., Bertin G., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/201014387) 519, A47
Arnouts S., Cristiani S., Moscardini L., Matarrese S., Lucchin F.,
Fontana A., Giallongo E., 1999, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.1999.02978.x) 310, 540
Asplund M., Grevesse N., Sauval A. J., Scott P., 2009, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.46.060407.145222)

47, 481
Astropy Collaboration et al., 2013, [A&A,](http://dx.doi.org/10.1051/0004-6361/201322068) 558, A33
Belfiore F., et al., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx789) 469, 151
Bertin E., Arnouts S., 1996, [A&AS,](http://dx.doi.org/10.1051/aas:1996164) 117, 393
Bielby R., Crighton N. H. M., Fumagalli M., Morris S. L., Stott
J. P., Tejos N., Cantalupo S., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx528) 468, 1373
Bolatto A. D., Wolfire M., Leroy A. K., 2013, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-082812-140944) 51, 207
Bordoloi R., et al., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/743/1/10) [743,](http://adsabs.harvard.edu/abs/2011ApJ...743...10B) 10
Bouch´e N., Murphy M. T., P´eroux C., Davies R., Eisenhauer F.,
F¨orster Schreiber N. M., Tacconi L., 2007, [ApJ,](http://dx.doi.org/10.1086/523594) [669,](http://adsabs.harvard.edu/abs/2007ApJ...669L...5B) L5
Bouch´e N., et al., 2012, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.19500.x) [419,](http://adsabs.harvard.edu/abs/2012MNRAS.419....2B) 2
Bouch´e N., Murphy M. T., Kacprzak G. G., P´eroux C., Contini
T., Martin C. L., Dessauges-Zavadsky M., 2013, [Science,](http://dx.doi.org/10.1126/science.1234209) [341,](http://adsabs.harvard.edu/abs/2013Sci...341...50B)

[50](http://adsabs.harvard.edu/abs/2013Sci...341...50B)

Bouch´e N., Carfantan H., Schroetter I., Michel-Dansac L., Contini
T., 2015, [AJ,](http://dx.doi.org/10.1088/0004-6256/150/3/92) [150,](http://adsabs.harvard.edu/abs/2015AJ....150...92B) 92
Calzetti D., 1997, [AJ,](http://dx.doi.org/10.1086/118242) 113, 162
Carilli C. L., Walter F., 2013, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-082812-140953) 51, 105
Christensen L., Møller P., Fynbo J. P. U., Zafar T., 2014, [MN-](http://dx.doi.org/10.1093/mnras/stu1726)
[RAS,](http://dx.doi.org/10.1093/mnras/stu1726) 445, 225
Churchill C. W., Steidel C. C., Vogt S. S., 1996, [ApJ,](http://dx.doi.org/10.1086/177960) 471, 164
Drory N., et al., 2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/707/2/1595) 707, 1595
Fumagalli M., et al., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx1896) 471, 3686
Garn T., Best P. N., 2010, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2010.17321.x) 409, 421
Gauthier J.-R., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt565) 432, 1444
Heisler J., Tremaine S., Bahcall J. N., 1985, [ApJ,](http://dx.doi.org/10.1086/163584) [298,](http://adsabs.harvard.edu/abs/1985ApJ...298....8H) 8
Ho I.-T., Kudritzki R.-P., Kewley L. J., Zahid H. J., Dopita M. A.,
Bresolin F., Rupke D. S. N., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv067) 448, 2030
Ilbert O., et al., 2006, [A&A,](http://dx.doi.org/10.1051/0004-6361:20065138) 457, 841
Jorgenson R. A., Wolfe A. M., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/785/1/16) [785,](http://adsabs.harvard.edu/abs/2014ApJ...785...16J) 16
Kacprzak G. G., Murphy M. T., Churchill C. W., 2010, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2010.16667.x)

406, 445
Kennicutt Jr. R. C., 1998, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.36.1.189) 36, 189
Kereˇs D., Katz N., Fardal M., Dav´e R., Weinberg D. H., 2009,

[MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.14541.x) 395, 160
Kobulnicky H. A., Kewley L. J., 2004, [ApJ,](http://dx.doi.org/10.1086/425299) 617, 240
Lanyi G. E., et al., 2010, [AJ,](http://dx.doi.org/10.1088/0004-6256/139/5/1695) 139, 1695
Ly C., et al., 2007, [ApJ,](http://dx.doi.org/10.1086/510828) 657, 738
Maiolino R., et al., 2008, [A&A,](http://dx.doi.org/10.1051/0004-6361:200809678) 488, 463


MNRAS **000**, 1–17 (2017)



Martin C. L., Shapley A. E., Coil A. L., Kornei K. A., Bundy K.,
Weiner B. J., Noeske K. G., Schiminovich D., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/760/2/127) [760,](http://adsabs.harvard.edu/abs/2012ApJ...760..127M)

[127](http://adsabs.harvard.edu/abs/2012ApJ...760..127M)

Neeleman M., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/2041-8205/820/2/L39) 820, L39
Oteo I., Zwaan M. A., Ivison R. J., Smail I., Biggs A. D., 2016,

[ApJ,](http://dx.doi.org/10.3847/0004-637X/822/1/36) [822,](http://adsabs.harvard.edu/abs/2016ApJ...822...36O) 36
Pagel B. E. J., Edmunds M. G., Blackwell D. E., Chun M. S.,
Smith G., 1979, [MNRAS,](http://dx.doi.org/10.1093/mnras/189.1.95) [189,](http://adsabs.harvard.edu/abs/1979MNRAS.189...95P) 95
Papadopoulos P. P., van der Werf P. P., Xilouris E. M., Isaak
K. G., Gao Y., M¨uhle S., 2012a, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.21001.x) 426, 2601
Papadopoulos P. P., van der Werf P., Xilouris E., Isaak K. G.,
Gao Y., 2012b, [ApJ,](http://dx.doi.org/10.1088/0004-637X/751/1/10) [751,](http://adsabs.harvard.edu/abs/2012ApJ...751...10P) 10
Peng C. Y., Ho L. C., Impey C. D., Rix H.-W., 2002, [AJ,](http://dx.doi.org/10.1086/340952) [124,](http://adsabs.harvard.edu/abs/2002AJ....124..266P)

[266](http://adsabs.harvard.edu/abs/2002AJ....124..266P)

P´eroux C., Bouch´e N., Kulkarni V. P., York D. G., Vladilo G.,
2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2010.17598.x) 410, 2237
P´eroux C., Kulkarni V. P., York D. G., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt2084) 437, 3144
P´eroux C., et al., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stw2444) 464, 2053
Poggianti B. M., Wu H., 2000, [ApJ,](http://dx.doi.org/10.1086/308243) 529, 157
Polletta M., et al., 2007, [ApJ,](http://dx.doi.org/10.1086/518113) [663,](http://adsabs.harvard.edu/abs/2007ApJ...663...81P) 81
Popping A., Jurek R., Westmeier T., Serra P., Fl¨oer L., Meyer
M., Koribalski B., 2012, Publ. Astron. Soc. Australia, 29, 318
Prochaska J. X., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa6007) 837, 169
Rahmani H., et al., 2017, preprint, ( `[arXiv:1710.08398](http://arxiv.org/abs/1710.08398)` )
Rao S. M., Turnshek D. A., Nestor D. B., 2006, [ApJ,](http://dx.doi.org/10.1086/498132) 636, 610
Rao S. M., Belfort-Mihalyi M., Turnshek D. A., Monier E. M.,
Nestor D. B., Quider A., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.19119.x) 416, 1215
Richings A. J., Faucher-Giguere C.-A., 2017, preprint,
( `[arXiv:1706.03784](http://arxiv.org/abs/1706.03784)` )
Rupke D. S., Veilleux S., Sanders D. B., 2005, [ApJS,](http://dx.doi.org/10.1086/432889) 160, 115
Sandage A., 1986, [ApJ,](http://dx.doi.org/10.1086/164387) [307,](http://adsabs.harvard.edu/abs/1986ApJ...307....1S) 1
Schroetter I., Bouch´e N., P´eroux C., Murphy M. T., Contini T.,
Finley H., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/804/2/83) [804,](http://adsabs.harvard.edu/abs/2015ApJ...804...83S) 83
Schroetter I., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/1538-4357/833/1/39) [833,](http://adsabs.harvard.edu/abs/2016ApJ...833...39S) 39
Serra P., et al., 2012, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.20219.x) 422, 1835
Serra P., et al., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv079) 448, 1922
Sobral D., Best P. N., Matsuda Y., Smail I., Geach J. E., Cirasuolo
[M., 2012, Monthly Notices of the Royal Astronomical Society,](http://dx.doi.org/10.1111/j.1365-2966.2011.19977.x)
420, 1926
[Solomon P. M., Downes D., Radford S. J. E., 1992, ApJ, 398, L29](http://dx.doi.org/10.1086/186569)
Soto K. T., Lilly S. J., Bacon R., Richard J., Conseil S., 2016,

[MNRAS,](http://dx.doi.org/10.1093/mnras/stw474) 458, 3210
Stewart K. R., Kaufmann T., Bullock J. S., Barton E. J., Maller
A. H., Diemand J., Wadsley J., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/738/1/39) [738,](http://adsabs.harvard.edu/abs/2011ApJ...738...39S) 39
Storey P. J., Zeippen C. J., 2000, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2000.03184.x) 312, 813
[Tremonti C. A., Moustakas J., Diamond-Stanic A. M., 2007, ApJ,](http://dx.doi.org/10.1086/520083)

663, L77
Tumlinson J., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/777/1/59) [777,](http://adsabs.harvard.edu/abs/2013ApJ...777...59T) 59
Veilleux S., Cecil G., Bland-Hawthorn J., 2005, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.43.072103.150610) 43, 769
Villanueva V., et al., 2017, preprint, ( `[arXiv:1705.09826](http://arxiv.org/abs/1705.09826)` )
Vogt S. S., et al., 1994, in Crawford D. L., Craine E. R., eds,
Proc. SPIEVol. 2198, Instrumentation in Astronomy VIII.
p. 362, [doi:10.1117/12.176725](http://dx.doi.org/10.1117/12.176725)
Weiner B. J., et al., 2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/692/1/187) 692, 187
Whiting M. T., Webster R. L., Francis P. J., 2006, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2006.10101.x) [368,](http://adsabs.harvard.edu/abs/2006MNRAS.368..341W)

[341](http://adsabs.harvard.edu/abs/2006MNRAS.368..341W)

Wills B. J., Uomoto A. K., Wills D., Netzer H., 1980, [ApJ,](http://dx.doi.org/10.1086/157871) [237,](http://adsabs.harvard.edu/abs/1980ApJ...237..319W)

[319](http://adsabs.harvard.edu/abs/1980ApJ...237..319W)

Yanny B., York D. G., 1992, [ApJ,](http://dx.doi.org/10.1086/171371) 391, 569
Yanny B., York D. G., Williams T. B., 1990, [ApJ,](http://dx.doi.org/10.1086/168473) 351, 377
Yun M. S., Ho P. T. P., Lo K. Y., 1994, [Nature,](http://dx.doi.org/10.1038/372530a0) 372, 530
Zahid H. J., Dima G. I., Kudritzki R.-P., Kewley L. J., Geller
M. J., Hwang H. S., Silverman J. D., Kashino D., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/791/2/130)
791, 130
Zwaan M. A., van der Hulst J. M., Briggs F. H., Verheijen
M. A. W., Ryan-Weber E. V., 2005, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2005.09698.x) 364, 1467

14 _A._ _Klitsch_ _et_ _al._


**Figure** **A1.** The intensity weighted line-of-sight velocity field of
the [12] CO(2–1) emission from the ALMA observations for J0423B.
The velocity map is consistent with a rotating disk and the orientation is consistent with the model velocity field based on [OIII]
emission shown in Fig. A2.


**APPENDIX** **A:** **MORPHOLOGY** **AND**

**KINEMATICS**


To study the kinematics of the molecular gas, we create
a line-of-sight velocity map using the CASA task IMMOMENTS including pixels where the [12] CO line emission is
detected at 3σ above the noise in each velocity channel
of the cube. The resulting map is shown in Fig. A1. The
velocity field is sampled with only three resolution elements
across the major axis, but given this limitation, the velocity
field is consistent with that of a rotating disk.


To determine the morphology and kinematics of the
four [OIII]-detected galaxies in our MUSE cube, we perform a two-step analysis. First, we perform a Sersic-fit
of the [OIII] pdfeudo-narrow-band image using Galfit
(Peng et al. 2002). Second, we use the GALPAK [3D] algorithm (Bouch´e et al. 2015) to perform a 3D morphokinematic fit to the [OIII] emission line cube. We use the
Sersic profile as input for the 3D morpho-kinematic fit. We
infer from this fit whether the kinematics are compatible
with that observed in a rotating disk and how the position
angles of the galaxies are related to each other and how the
quasar absorption is oriented with respect to the major and
minor axes of the galaxies. However, given the data quality
we will not be able to detect warpdf in the disks.
We determine the half-light radius, axis ratio, position angle (PA) and the Sersic index from the [OIII]
pdfeudo-narrow-band image using Galfit. This is a twodimensional fitting algorithm extracting structural parameters from galaxy images. The algorithm models the light
profile and is designed to fit multiple components. Here we
perform a single component fit of the [OIII] pdfeudo-narrow
band image. The fitting results are shown in Table A1. We
find that for J0423D the PA and Sersic index are not very
well constrained due to the low SNR of the detected line

emission.
The GALPAK [3D] algorithm is used to derive the kinematics of the galaxies based on the [OIII] emission line. We



do not use the [OII] emission line, because it is an unresolved
doublet and we do not know the exact line ratio.
The GALPAK [3D] algorithm directly compares a number
of parametric models, created from a Markov Chain Monte
Carlo (MCMC) algorithm and mapped in _x_, y, λ coordinate
system, to the data. GALPAK [3D] fits the model in three dimensions and offers even in poor seeing conditions a robust
determination of the morpho-kinematics. It probes the posterior possibility density distribution via an MCMC chain
of 15, 000 runs and fits 10 parameters simultaneously (position ( _x_, y, λ), flux, half-light radius, inclination, PA, turnover
radius, maximum velocity and intrinsic velocity dispersion).
The algorithm can only converge if the maximum SNR

- 3 per pixel, which is not fulfilled for J0423D. Furthermore,
the maximum velocity is overestimated if the ratio of galaxy
half-light radius to seeing radius is smaller than about 1.5.
We use the half-light radius from the 2D fitting as
a fixed input parameter for J0423B. For J0423A it is
necessary to fix the turnover radius to break the degeneracy
with the maximum velocity. We set the turnover radius to
0.9 times the half-light radius based on the scaling relation
found in local disc galaxies (Amorisco & Bertin 2010). Since
all of the galaxies are found to be compact already from
independent 2D profile fitting, we expect that the GalpaK [3D]

will overestimate the maximum velocity. The final fitting
parameters are given in Table A1. We find that the velocity
fields of the galaxies J0423A, J0423B, and J0423C are
consistent with rotating disks. As can be seen in Table A1
the PAs from different objects are not aligned. Comparing
the PA derived with Galpak [3D] with the PA from the 2D
fitting with Galfit we find that they are comparable
within the errors. We show the observed and model velocity
fields from the MUSE observations in Fig. A2. It can be
seen that in J0423B the velocity field of the ionized gas
traced by the [OIII] emission line and of the molecular gas
traced by the [12] CO(2–1) emission line shown in Fig. A1 are
consistent. Furthermore, we find that the angular extent of
1.4 [′′] ± 0.1 [′′] for the [OIII] emission line matches the angular extent of 1.3 [′′] ±0.2 [′′] found for the CO(2–1) emission line.


We explore the possibility that the absorption in the
quasar spectrum is tracing the extended rotating gas disk of
one of the two closest galaxies J0423A and J0423B. Therefore, we extrapolate the model velocity field derived above
to the position of the absorber. The expected velocity is
overplotted in the velocity space of the absorber on the
MgII2796A [˚] absorption line in the last panel of Fig. B1. It
can be seen that the expected velocity from J0423A does
not match the absorption profile. For J0423B on the other
hand, we find that it agrees very well with one of the absorption components in the MgII2796A [˚] absorption profile.
Intriguingly, this galaxy is the one for which we measure
a large cold gas content. We note, however, that projected
separation between the quasar sight line and the gas-rich
galaxy is 133 kpc, so the simple extrapolation of a rotating
disk is a very naive assumption.


**APPENDIX** **B:** **NEUTRAL** **GAS** **PROPERTIES**


In this section, we use the quasar spectrum presented by
Churchill et al. (1996) to fit the absorption lines, determine


MNRAS **000**, 1–17 (2017)

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 15





160

120

80

40

0

_−_
40

_−_
80

_−_
120


600

450

300

150

0

_−_
150

_−_
300

_−_
450


500

400

300

200

100

0

_−_
100

_−_
200

_−_
300



**Figure** **A2.** Results from the morpho-kinematic fitting to the [OIII] emission detected with MUSE, including the observed velocity
field (left), the model velocity field from GalpaK [3D] fitting (middle) and the residual map (right) for J0423A (top), J0423B (middle) and
J0423C (bottom). The arrow indicated the direction towards the quasar sight-line. We find that all three galaxies have velocity fields
consistent with rotating disks. We caution that the maximum velocity from the modelling is uncertain because all three galaxies are very
compact (< 3 kpc) and GalpaK [3D] is known to overestimate the maximum velocity in the case of compact galaxies (Bouch´e et al. 2015).
We also note that the observed velocity fields are spatially re-sampled for display purpose.


**Table** **A1.** Summary of the morphological parameters from 2D fitting and morpho-kinematic parameters from 3D fitting.


Name r 1 [Galfit] /2 r 1 [GalpaK] /2 PA [Galfit] PA [GalpaK] i [Galfit] i [GalpaK] Sersic index v max [GalpaK] σ 0 [GalpaK]

[kpc] [kpc] [ [◦] ] [ [◦] ] [ [◦] ] [ [◦] ] [km s [−][1] ] [km s [−][1] ]


J0423A 1.5 ± 0.6 2.9 ± 0.3 106 ± 4 115 ± 4 33 ± 3 42 ± 6 3 ± 1 < 410 11 ± 7

J0423B 2.77 ± 0.08 2.77 [⋆] 90 ± 2 54 ± 24 40.5 ± 0.8 51 ± 17 1.04 ± 0.03 < 170 84 ± 17

J0423C 1.54 ± 0.09 2.73 ± 0.03 67 ± 6 54 ± 21 47 ± 3 50 ± 16 0.71 ± 0.06 < 191 87 ± 17

J0423D 0.5 ± 0.1 −90 ± 90 60 ± 30 0.3 ± 0.4


Note: [⋆] is fixed based on the 2D fitting from Galfit. We find that for J0423A, J0423B and J0423C the morphological parameters from
independent 2D and 3D fitting are comparable.



the minimum number of components needed to reproduce
the absorption profile and determine their redshift. We will
use these fits in Section C2 to derive a lower limit on the
total metallicity of the absorbing neutral gas. We use the
kinematic information and the metallicity of the absorber


MNRAS **000**, 1–17 (2017)



to infer the alignment with the galaxies in velocity space as
well as the possibility of probing an extended galactic disk
with the absorption.


We model the metal absorption lines in the quasar spectrum associated with the Lyman Limit system with Voigt

16 _A._ _Klitsch_ _et_ _al._


1.6









1.6

-300 -200 -100 0 100 200 300



-300 -200 -100 0 100 200 300

Velocity [km s _[−]_ [1] ]









**Figure** **B1.** Fits to the FeII2382 [˚] A, FeII2600 [˚] A, MgII2796 [˚] A, MgII2803 [˚] A, MgI2852A [˚] absorption lines in the QSO spectrum. In the fitting
using vpfit we assumed two components for FeII and MgI and six components for the saturated MgII. Velocity zero corresponds to
the redshift of the main component from the joint fits of FeII2600 [˚] A, FeII2382 [˚] A, MgI2852A. [˚] The last panel shows a comparison of the
MgII2796 [˚] A absorption line profile with the expected absorption caused by an extended rotating disk of J0423A and J0423B at the position
of the quasar sight-line. We find that the absorption cannot be caused by an extended disk of J0423A, but the velocity extrapolated from
the disk of J0423B matches the absorption profile. We note, however, that due to the large impact parameter of 133 kpc the absorption
is unlikely tracing the disk of J0423B.



profiles using VPFIT [4] v.10.2. The VPFIT code is developed
to fit multiple Voigt profiles to spectroscopic data by minimizing the χ [2] . Here, we have performed a multicomponent
fit assuming that for each absorption component all ions
have the same redshift. We show the spectra and the Voigt
profile fits in Fig. B1. It can be seen that the MgII2803 [˚] A, and
MgII2796 [˚] A absorption lines are saturated and more complex
than the FeII2600 [˚] A, FeII2382 [˚] A, and MgI2852A [˚] absorption
lines. Therefore, we fit the two sets of absorption lines separately. We find that the absorption lines are well fitted using
two-components for the FeII and MgI lines. A separate fit is
performed for the strong MgII lines using six components.
We summarize the corresponding fit parameters in Table B1.


**APPENDIX** **C:** **METALLICITIES**


We study the metallicity of the ionised gas in the galaxies
and of the neutral gas traced by the absorption. Using this
information, we can compare the metallicities observed at
different positions with each other and infer from this the
connection between the galaxies and the absorbing gas.


4 `[httpdf://www.ast.cam.ac.uk/~rfc/vpfit.html](httpdf://www.ast.cam.ac.uk/~rfc/vpfit.html)`



(C1)


We derive the metallicities according to the formalism
described as the “best” oxygen abundance determined by
Kobulnicky & Kewley (2004). We use the O32 parameter
( _f_ [OIII] / _f_ [OII] ) as a branch indicator (Maiolino et al. 2008),
where O32 - 2 suggests the lower branch solution and
O32 < 1 suggests the upper branch solution. The four galaxies in this study have O32 values between 0.26 and 0.74 indicating that the upper branch solution is appropriate. The
derived metallicities of our galaxies are listed in Table 5.
Compared to the solar abundance of log(O/H) + 12 = 8.69
(Asplund et al. 2009) we find that galaxy J0423A and
J0423C have metallicities of 0.11 and 0.25. However, since


MNRAS **000**, 1–17 (2017)



**C1** **HII** **Metallicities**


To determine the gas metallicities of the MUSE-detected
galaxies from the emission lines, we use the R23 method as
first introduced by Pagel et al. (1979), which is widely used
to determine gas metallicities if the H β, [OII], and [OIII]
fluxes are known. It uses the log _R_ 23 parameter, which is
defined as follows:



_F_ ([ _OII_ ]λ3727, 3729) + _F_ ([ _OIII_ ]λ4959, 5007)
log( _R_ 23 ) = log
� _F_ ( _H_ β)



.
�

_ALMACAL_ _III:_ _Neutral,_ _Molecular,_ _and_ _Ionised_ _Gas_ _around_ _an_ _Absorption-Selected_ _System_ 17



**Table** **B1.** Fit parameters for the absorption line Voigt profile
fitting using vpfit.


Ion No. z b log N

[atoms cm [−][2] ]


FeII 1 0.633174 ± 0.000006 3.0 ± 2.4 12.21 ± 0.13

FeII 2 0.633080 ± 0.000005 8.9 ± 1.4 12.80 ± 0.05

MgI 1 0.633174 ± 0.000006 3.0 ± 2.4 11.04 ± 0.15
MgI 2 0.633080 ± 0.000005 8.9 ± 1.4 11.50 ± 0.07


MgII 1 0.631791 ± 0.000002 7.7 ± 0.5 12.49 ± 0.02
MgII 2 0.632558 ± 0.000005 5.7 ± 1.3 12.09 ± 0.06
MgII 3 0.632648 ± 0.000005 7.0 ± 1.8 12.16 ± 0.08
MgII 4 0.632788 ± 0.000003 2.9 ± 1.4 12.36 ± 0.09
MgII 5 0.632855 ± 0.000004 20.6 ± 0.9 13.17 ± 0.02
MgII 6 0.633108 ± 0.000003 11.5 ± 0.4 13.49 ± 0.04


Note: The top four rows above the dividing line show the parameters for the Voigt Profile fitting using only FeII and MgI. The
bottom six lines below the dividing line show the fit parameters
for the Voigt profile fit using only the MgII absorption lines. No.
denotes the number of the component that is simultaneously fit
in multiple absorption lines.


we are not applying a dust correction we could overestimate
the metallicities.

Since we do not detect the H β emission line from
J0423B and J0423D, we use the stellar mass-metallicity relation to determine the gas phase metallicity of these two
galaxies. We use the relation given by Zahid et al. (2014)
who fits the following function to a sample from DEEP2 at
_z_ ≃ 0.8:



**Table** **C1.** Metallicity of the galaxies and expected metallicity
based on extrapolation using a constant slope at the absorber
position assuming an extended gas disk


Name Z mean Z central θ[kpc] Z exp /Z⊙


J0423A 0.1 ± 0.1 0.2 ± 0.1 102 −2 ± 1

J0423B 0.4 ± 0.9 0.5 ± 0.9 133 −3 ± 1

J0423C 0.25 ± 0.06 0.32 ± 0.06 146 −3 ± 2

J0423D 0.3 ± 0.9 0.3 ± 0.9 216 −5 ± 2


Note: Z = 0 is equal to the solar abundance.


the ones probed in the aforementioned studies. We test
whether we can connect the galaxies with the absorbing
gas using a uniform metallicity gradient. We extrapolate
the metallicity observed in the four galaxies to the position
of the intervening absorber using a constant gradient from
the literature. First, we derive the central metallicity of
the galaxies from the total metallicity reported in Table 6
and using the solar abundance of log(O/H) + 12 = 8.69
(Asplund et al. 2009). To derive the central metallicity
we assume a linear distribution of the mean metallicity
quoted in Table C1 over two _r_ 1/2 where we use _r_ 1/2 from
the 3D fitting if available. We use the standard metallicity
gradient determined within the disk quoted above. The
same metallicity gradient is then used to extrapolate the
derived central gas phase metallicity to the position of the
absorber. The mean and central metallicity of the galaxies
and the expected metallicity at the position of the absorber
are given in Table C1. We find that the extrapolated
metallicity is above a simple extrapolation of the metallicity
gradient. This shows that the metallicity gradient cannot
be extended to such large distances.


However, here we are comparing the metallicity of the
ionized gas in the galaxy with the metallicity of neutral gas
probed by the absorption. Furthermore, the standard deviation in the observed gradients is ±0.010 dex kpc [−][1] in the
study by Ho et al. (2015). The corresponding uncertainty in
the extrapolation is shown in Table C1. Considering this and
the additional caveat of using uniform gradients discussed
above we regard this calculation only as an indication.


This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.



12 + log(O/H) = Z 0 + log 1 − exp − M ⋆
� � � M 0



γ
, (C2)
� ��



where _Z_ 0 = 9.10, log( _M_ 0 [M⊙]) = 9.80 and γ = 0.52.
This yields a metallicity of 12 + log(O/H) = 9.1 ± 0.9 and
9.0±0.9 for J0423B and J0423D, respectively. The 1σ scatter
in the DEEP2 data is quite large and therefore the derived
metallicity has a large error bar.


**C2** **Neutral** **Gas** **Metallicity**


We use the combined fits of FeII2600 [˚] A, and FeII2382A [˚]
and the HI column density derived by (Rao et al. 2006)
to determine the metallicity of the absorbing gas without
taking dust into account. We report a lower limit to reflect possible ionisation correction. We find that [Fe/H] =
log(Fe/H) abs − log(Fe/H)⊙ is higher than −1.16.


**C3** **Comparison**


Large integral field surveys have shown that galaxies with
log( _M_ ⋆ ) - 9.6 have a uniform metallicity gradient within
the disk of −0.026 dex kpc [−][1] Ho et al. (2015). However,
at distances beyond 2 _R_ e first pieces of evidence for a
flattening of the metallicity gradients are found (Belfiore
et al. 2017). For absorption line systems a similar shallow
negative metallicity gradient is observed out to 25 kpc (e.g.
P´eroux et al. 2014; Christensen et al. 2014; Rahmani et al.
2017). In the system presented in this work the impact
parameter is - 100 kpc and therefore much larger than


MNRAS **000**, 1–17 (2017)


</paper>

## Items to check

```json
[
 {
  "path": "processing.calibration.flux_scale_uncertainty.evidence[0]",
  "value": "5% on integrated line flux",
  "failed_quote": "We estimate the error of the integrated line flux to be 5% based on the expected accuracy of the flux calibration."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "flux error 5%",
  "failed_quote": "We estimate the error of the integrated line flux to be 5% based on the expected accuracy of the flux calibration."
 },
 {
  "path": "software[8].used_for.evidence[0]",
  "value": "3D morpho-kinematic fit of [OIII] cube",
  "failed_quote": "we use the GALPAK 3D algorithm (Bouché et al. 2015) to perform a 3D morphokinematic fit"
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "template scaling",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[5].fitting.evidence[0]",
  "value": "chi2 minimisation (Le Phare, VPFIT); MCMC (GalPaK3D)",
  "failed_quote": "(no quote given)"
 }
]
```
