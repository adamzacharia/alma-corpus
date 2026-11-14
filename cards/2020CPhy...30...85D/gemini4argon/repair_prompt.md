# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020CPhy...30...85D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Submit to “Communications in Physics”, (2020), pp. 1-12

[DOI:10.15625/0868-3166/0/0/0](http://dx.doi.org/10.15625/0868-3166/0/0/0)


**OBSERVATION OF HIGH DOPPLER VELOCITY WINGS IN THE NASCENT**

**WIND OF R DORADUS**


D.T. HOAI, P.T. NHUNG, P. TUAN-ANH, P. DARRIULAT, P.N. DIEP, N.T. PHUONG AND

T.T. THAI

_Vietnam National Space Center (VNSC), Vietnam Academy of Science and Technology (VAST),_
_18 Hoang Quoc Viet, Cau Giay, Ha Noi, Vietnam_


_E-mail:_ [dthoai@vnsc.org.vn](mailto:dthoai@vnsc.org.vn)


_Received 18 November 2021_

_Accepted for publication DD MM YYYY_


**Abstract.** _We study the morpho-kinematics in the nascent wind of AGB star R Doradus in the light_
_of high Doppler velocity wings observed in the spectral lines of several species. We probe distances_
_from the star between ∼10 and ∼100 au using ALMA observations of the emission of five different_
_molecular_ _lines._ _High_ _Doppler_ _velocity_ _enhancements_ _of_ _the_ _line_ _emission_ _are_ _observed_ _in_ _the_
_vicinity of the line of sight crossing the star, reminiscent of those recently interpreted as gas streams_
_in the nascent wind of a similar AGB star, EP Aqr._ _They are present in both blue-shifted and red-_
_shifted_ _hemispheres_ _but_ _are_ _not_ _exactly_ _back-to-back._ _They_ _are_ _accelerated_ _at_ _a_ _typical_ _rate_ _of_
_0.7 km s_ _[−]_ [1] _au_ _[−]_ [1] _up to some 20 km s_ _[−]_ [1] _._ _Important differences are observed between the emissions_
_of_ _different_ _molecules._ _We_ _exclude_ _an_ _effect_ _of_ _improper_ _continuum_ _subtraction._ _However,_ _in_
_contrast_ _to_ _EP_ _Aqr,_ _the_ _line_ _of_ _sight_ _plays_ _no_ _particular_ _role_ _in_ _the_ _R_ _Dor_ _morpho-kinematics,_
_shedding doubt on the validity of a gas stream interpretation.We discuss possible interpretations_
_in terms of stellar pulsations or of rotation of the gas in the environment of the star._ _We conclude_
_that,_ _in_ _the_ _state_ _of_ _current_ _knowledge,_ _no_ _fully_ _convincing_ _picture_ _of_ _the_ _physics_ _governing_ _the_
_production of such high velocities, typically twice as large as the terminal velocity, can be reliably_
_drawn._ _New_ _high_ _resolution_ _analyses_ _of_ _observations_ _of_ _the_ _nascent_ _wind_ _of_ _oxygen-rich_ _AGB_
_stars are needed to clarify the issue._


_Keywords: stars:_ _AGB and post-AGB, circumstellar matter, stars:_ _individual:_ _R Dor, radio lines:_

_stars._


_Classification numbers: 97.60-s._


_⃝_ c 2020 Vietnam Academy of Science and Technology

2 D. T. Hoai


**I** . **INTRODUCTION**


The occasional presence of large Doppler velocity wings in some line emission spectra of
oxygen-rich evolved stars has been known for some time [2]. They are particularly visible in
SiO line profiles and may typically reach twice the terminal wind velocity. Single dish millimetre
observations analysed by Winters et al. (2003) [29] and more recently by de Vincente et al. (2016)

[6] have suggested that the emission occurs close to the star, where SiO grains have not yet fully
formed, and is somehow related to star pulsations.
In the past few years, the availability of high angular resolution ALMA observations of the
nascent winds of two similar AGB stars, EP Aqr and R Dor, has shed new light on this issue.
The presence of high Doppler velocity components in the [28] SiO( _ν_ = 0 _,_ _J_ = 5 _−_ 4) line
emission of the nascent wind of EP Aqr was first noted by Homan et al. (2018a) [11] in Section
4.4 of their article. The morpho-kinematics of the circumstellar envelope of EP Aqr is known to
display axi-symmetry about an axis close to the line of sight [10]. The study of SO 2 line emission
very close to the star gives evidence for rotation about the same axis [11, 24]. Inhomogeneity
has been revealed in the equatorial plane, close to the plane of the sky, in the form of a spiral of
intensity [11] and of concentric rings of radial velocity [10]. The spiral of intensity was tentatively
interpreted by Homan et al. (2018a) [11] as evidence for the presence of a companion. In such a
context it was therefore natural for Homan et al. (2018a) [11] to consider the possibility that the
complex dynamics in the wind-companion interaction zone not only accelerate a large portion of
the outflow material along the equatorial plane, but also along the polar axis, causing some of this
material to have increased velocities along the line of sight.
Tuan-Anh et al. (2019) [24] have then performed a detailed study of the morpho-kinematics
of the high velocity wings of the [28] SiO( _ν_ = 0 _,_ _J_ = 5 _−_ 4) line emission and have shown that they
are also present, but much weaker, in the [12] CO(2-1) line emission. Their absence from the SO 2
line emission, at very short distances from the star, disfavours too sudden an acceleration and, in
particular, an interpretation in terms of star pulsation. Tuan-Anh et al. (2019) [24] propose instead
a picture of two narrow polar streams of gas, referred to as jets, being launched from less than 25
au away from the star, building up between _∼_ 20 au and _∼_ 100 au to a velocity of _∼_ 20 km s _[−]_ [1] and
fading away at larger distances.
Both Homan et al. (2018a) [11] and Tuan-Anh et al. (2019) [24] insist on the complexity
of the morpho-kinematics of the nascent wind of EP Aqr when observed with the high angular
resolution offered by ALMA and on the difficulty to draw a convincing and reliable picture of the
physics at stake.
Decin et al. (2018) [5] were first to discuss the presence of high velocity wings in some line
emission spectra of the nascent wind of R Dor, far above the canonical terminal wind velocities
although hints of their existence had been mentioned earlier (e.g. Justtanont et al. 2012 [13]).
They quote a maximal Doppler velocity of 23 km s _[−]_ [1] reached in the line emission of SiO( _ν_ =
0 _,_ _J_ = 8 _−_ 7) (note that the velocity scale in their Figure 8 is a factor 2 too large, we thank Pr Leen
Decin for clarification on this point). They show in their Figure 10 typical values of the end point
velocity of different line spectra reaching some _∼_ 15 km s _[−]_ [1] . On the basis of a model proposed
by Nowotny et al. (2010) [22] they argue that star pulsations cannot significantly contribute to
the generation of such high velocities. They conclude that the origin of the large velocities is a

High Doppler velocity wings in the nascent wind of R Doradus 3


genuine physical mechanism not linked to thermal motions of the gas or pulsation behaviour of
the atmospheric layers and that their impact on the mass-loss rate cannot be underestimated.
They privilege a scenario developed by Homan et al. (2018b) [12] suggesting the presence
of a rotating disc, seen nearly edge-on, in the close neighbourhood of the star. It covers radial distances between 6 and 25 au and the Doppler velocity is maximal on the inner rim where it reaches
12 km s _[−]_ [1] . The relation between this disc and the high Doppler velocity wings is the suspected
presence of an evaporating companion planet providing the necessary angular momentum to the
disc rotation. Evidence for the possible existence of such a companion rests on the observation
of high Doppler velocity emission in the blue-shifted hemisphere near the middle of the southeastern quadrant. This enhanced emission is referred to as the “blue blob” by both Decin et al.
(2018) [5] and Homan et al. (2018b) [12]. They discuss critically the properties of the “blue blob”
and carefully conclude that follow-up high-resolution observations are needed to test their claims,
and to deeper investigate the true nature of both the disk-like signal and the blue blob.
Finally, Vlemmings et al. (2018) [28] analyse ALMA observations made two years later
with a four times better angular resolution than Decin et al. (2018) [5], _∼_ 35 mas instead of
_∼_ 150 mas. From continuum emission they resolve the stellar radio photosphere as a circle of 31
mas radius. The analysis covers the compact emission of two lines: SiO( _ν_ = 3 _,_ _J_ = 5 _−_ 4) and
SO 2 ( _J_ _Ka,Kc_ = 16 3 _,_ 13 _−_ 16 2 _,_ 14 ) and the absorption of a third, [29] SiO( _ν_ = 1 _,_ _J_ = 5 _−_ 4). The line
emissions are shown to be properly described by solid body rotation of expanding shells having
average radii of 36 mas (2.2 au) and 66 mas (4.0 au) for SiO( _ν_ = 3 _,_ _J_ = 5 _−_ 4) and SO 2 ( _J_ _Ka,Kc_ =
16 3 _,_ 13 _−_ 16 2 _,_ 14 ) respectively. The authors claim that their result contradicts the interpretation made
by Homan et al. of a nearly edge-on rotating disc. Their model implies a positive radial velocity
gradient, at variance with the disc model of Homan et al. (2018b) [12] that implies a negative
radial velocity gradient. However, following Homan et al., they suggest that the most likely cause
of the observed rotation is the presence of a companion. They show a position-velocity diagram
illustrating the region of the “blue blob” discovered earlier by Decin et al. (2018) [5]. This diagram
is using [29] SiO( _ν_ = 0 _,_ _J_ = 5 _−_ 4) observations about which no detail is given. The Doppler velocity
reaches some 15 km s _[−]_ [1] . The authors discuss it in the framework of their solid body rotation
model and recognize that the origin of the fast rotating feature out to _>_ 10 _R_ _∗_ remains unclear and
that this feature could be unrelated to the rotation and represent a seemingly one-sided ejection
of material. Apart from the discussion of this feature, the authors do not mention the possible
existence of high Doppler velocity wings but simply quote line widths of _∼_ 5 _−_ 10 km s _[−]_ [1] for
the SO 2 line, _∼_ 10 km s _[−]_ [1] for the SiO _ν_ = 3 line, and _∼_ 15 _−_ 20 km s _[−]_ [1] for the [29] SiO _ν_ = 1
line. A fortiori, they do not discuss possible causes for their existence, such as the effect of stellar
pulsations.
The lack of a convincing physical picture of the mechanism governing the production of
high Doppler velocity wings in the nascent winds of EP Aqr and R Dor, together with the absence of a detailed and dedicated analysis of their morpho-kinematics in the case of R Dor, have
motivated the present work.
EP Aqr and R Dor are both semi-regular variables of the SRb type and belong to similar
spectral classes, M8IIIvar and M8IIIe. They have similar initial masses, between 1 and 2 M _⊙_,
similar mass loss rates, _∼_ 1.6 10 _[−]_ [7] M _⊙_ yr _[−]_ [1] [10,18] and similar temperatures, within 100 K from
3150 K [7]. They are both close to the Sun, at distances of _∼_ 119 pc [8, 27] and _∼_ 59 pc [15],
respectively. Both display no technetium in their spectrum [16] and have the same [12] CO/ [13] CO

4 D. T. Hoai


abundance ratio of _∼_ 10 [23, 24]. They differ by their pulsation period, 55 days for EP Aqr [17]
and a dual period of 175 and 332 days for R Dor [1] but their infrared emissions above black body
between 1 and 40 _µ_ m wavelength are similar [9], the main difference being a relative enhancement
of silicates and depression of aluminium oxide in the EP Aqr dust.
The morpho-kinematics of the circumstellar envelope of EP Aqr has been measured up to
some 1000 au from the star [10, 11, 20, 24]. It is dominated above 200 au by an axi-symmetric
radial wind having reached a terminal velocity of _∼_ 2+9sin [2] _α_ km s _[−]_ [1], _α_ being the stellar latitude
and the polar axis making an angle of _∼_ 10 _[◦]_ with the line of sight. The circumstellar envelope of R
Dor has been probed by ALMA with a resolution of _∼_ 4 au up to some 60 au from the star [5,12,28]
and the dust has been observed at the VLT with a resolution of 1.2 au [14]. In addition, below _∼_ 15
au, the analyses of Danilovich et al. (2016) [3], De Beck & Olofsson (2018) [4] and Van de Sande
et al. (2018) [26] have contributed a considerable amount of detailed information of relevance to
the physico-chemistry and dynamics of both dust and gas. At larger distances from the star, an
analysis of ALMA observations of SO( _J_ _K_ = 6 5 _−_ 5 4 ) emission [21], probing distances between
20 and 100 au, gives evidence for the wind to host a radial outflow covering large solid angles
and displaying strong inhomogeneity both in direction and radially: the former takes the form of
multiple cores and the latter displays a radial dependence suggesting an episode of enhanced mass
loss having occurred a century or so ago.
In what follows, we explore a possible interpretation of the high velocity wings present
in the nascent wind of R Dor in terms similar to those observed in EP Aqr. We study the large
Doppler velocity features displayed by line emissions detected between _∼_ 15 and _∼_ 50 au from the
star [5], which suggest similarities with the EP Aqr dynamics. These include excitations of five
different molecules: CO, SiO, SO, SO 2 and HCN.


**II** . **OBSERVATIONS AND DATA REDUCTION**


The data are retrieved from ALMA archives.

The SO data (time on source of 2.7 hours) are from project 2017.1.00824.S observed in
December 2017 in band 6 with an average of 45 antennas. They have been used by Nhung et
al. (2019b) [21] to study the slow wind using the calibrations and deconvolution provided by the
standard ALMA pipeline. We have checked the quality of the data reduction and evidence for the
Gaussian distribution of the noise and for the proper description of the continuum map is given
there, together with channel maps. These data have not been used by other authors and the study
of Nhung et al. (2019b) [21] does not address the issue of large Doppler velocity components.
All other data (time on source of _∼_ 25 minutes) are from project 2013.1.00166.S observed
in summer 2015 in band 7 with an average of 39 antennas (Table 1). They have been used by
Decin et al. (2018) [5] who show channel maps but do not perform a detailed analysis of the
large Doppler velocity components. These observations, reduced using the results of the standard
ALMA pipeline, include datasets associated with significantly different _uv_ coverage, implying
different maximal recoverable scales. While this implies important differences in the flux-density
measured in the region of the slow wind, we have checked that very similar results are instead
obtained in the region of large Doppler velocities explored here at small projected distance from
the star.

High Doppler velocity wings in the nascent wind of R Doradus 5


**Table 1.** Line emissions considered in the present work. All are in the vibrational ground state.


Line CO(3-2) SiO(8-7) ( _J_ _K_ =SO 6 5 -5 4 ) (13 4 _,_ 10 SO-13 2 3 _,_ 11 ) HCN(4-3)

Frequency (GHz) 345.796 347.331 251.826 357.165 354.505
Beam FWHM (mas [2] ) 180 _×_ 140 180 _×_ 130 154 _×_ 147 160 _×_ 130 157 _×_ 145

Noise
5.5 4.8 1.1 6.3 8.5
(mJy beam _[−]_ [1] channel _[−]_ [1] )

Channel spacing
0.42 0.42 0.29 0.41 0.41
(km s _[−]_ [1] )

Peak intensity
0.74 1.31 0.13 0.17 0.39
(Jy beam _[−]_ [1] )

_E_ _u_ _/k_ (K) 33.2 75.0 50.7 123 42.5


In the present work we also use SiO line data from the same project reduced by us without
subtracting the continuum. They were calibrated from the raw data available in the archive and
deconvolved using the same procedure as for the continuum subtracted data.


**III** . **LARGE DOPPLER VELOCITY COMPONENTS**


We use coordinates rotated to have the “blue-blob” detected by Decin et al. (2018) [5] at a
position angle of approximately 180 _[◦]_, meaning that the _x_ axis points 35 _[◦]_ north of east and the _y_
axis 35 _[◦]_ west of north; the _z_ axis points away from us, parallel to the line of sight, and the origin of
coordinates is taken at the centre of continuum emission. Doppler velocity ( _V_ _z_ ) spectra are referred
to a local standard of rest velocity of 7.0 km s _[−]_ [1] .


**III.1** . **Interpretation in terms of gas streams**


Projections of the data-cubes on the ( _x,V_ _z_ ) and ( _y,V_ _z_ ) planes, to which we refer as P-V
maps, are shown in Figure 1. In contrast with standard P-V diagrams, these are not restricted to
narrow slits but are summed over the data-cube, namely integrated over _y_ and _x_ respectively. In all
cases the larger values of _|V_ _z_ _|_ are confined near _x_ = 0, very much as was observed in EP Aqr [24].
We define large Doppler velocity components as having _|V_ _z_ _| >_ 7 _._ 5 km s _[−]_ [1] in order to separate
them from the slower wind. Figure 2 displays the maps of their integrated intensity. Together with
Figure 1, they show an accelerating stream-like morphology, which was already apparent from the
progression of the “blue-blob” toward the star at a rate of _∼_ 0.7 km s _[−]_ [1] au _[−]_ [1] in the SO 2 channel
maps displayed in Figure B1 of Decin et al. (2018) [5]. They are particularly visible in the CO,
SiO and SO maps, both in the blue-shifted and red-shifted hemispheres, but more clearly in the
former than in the latter. The interpretation of the high Doppler velocity components as streams
rather than blobs is justified from their continuity with the slow wind: they only appear as blobs
when considering a slice confined to an interval of Doppler velocity. Figure 1 shows that they
clearly stand out from the region of phase-space covered by the slow wind, making the distinction
between high Doppler velocity wings and slow wind meaningful. This is further illustrated in
Figure 3, which displays channel maps of the large Doppler velocity components for SO emission;
other lines show similar patterns. We note the presence of an enhancement of emissivity near the

6 D. T. Hoai


line of sight in the lower _|V_ _z_ _|_ intervals of the blue-shifted hemisphere, suggesting the presence of
another component closer to the region of the slow wind. While the global picture is dominated
by the former, which extends down to _−_ 20 km s _[−]_ [1] with intensity comparable to the red-shifted
component, the presence of this enhancement cannot be ignored and needs to be studied in relation
with the complex morpho-kinematics of the slow wind [21]. However, this is beyond the scope of
the present work that focuses on the dominant large Doppler velocity components.
Globally, as illustrated in Figure 4 for the case of SO emission, the _V_ _z_ spectra are dominated
by the slow wind, the high velocity wings having much lower intensities on both the red-shifted
and blue-shifted sides. This allows for a reliable evaluation of the end points of the Doppler
velocity spectra of the slow wind, which we measure at _∼_ 7.0, _∼_ 8.3, _∼_ 6.2, _∼_ 6.0 and _∼_ 6.8 km
s _[−]_ [1] for CO, SiO, SO, SO 2 and HCN respectively on the red-shifted side. Very similar values
are obtained on the blue-shifted side. As the maximal recoverable scales pertinent to each line
are similar, these differences probably reveal different radial dependence of the molecular relative
abundance and/or emissivity being probed along the line of sight. In particular, evidence for
stream-like morphology is barely significant in the case of HCN as had first been noted by Decin
et al. (2018) [5]. The fact that the CO, SiO and SO 2 observations were made on a same day with
a same antenna pattern while HCN was observed the day before with a different antenna pattern
but a similar maximal recoverable scale is unlikely to explain the difference. We note that HCN is
not expected to form in O-rich environments, its relatively strong emission in the slow wind may
be explained by pulsation-induced shock-chemistry and the absence of detection at large Doppler
velocities may simply be the result of insufficient sensitivity.
The fact that the two candidate streams have the same reach in _|V_ _z_ _|_ suggests that they are
essentially symmetric with respect to the star. However, the red-shifted stream projects on the
star within a beam size while the blue-shifted stream spans a significant _y_ interval, implying that
such symmetry is not perfect. This may be because the streams are unrelated and that the same
reach in _|V_ _z_ _|_ is accidental. In this case, the streams may make very different angles _i_ 1 and _i_ 2 with
respect to the line of sight as long as their velocities _V_ 1 and _V_ 2 obey _V_ 1 cos _i_ 1 = _V_ 2 cos _i_ 2 . But if the
same reach in _|V_ _z_ _|_ is not accidental the two streams are expected to be at small angle to each other
and therefore at similar angles _i_ 1 _∼_ _i_ 2 _∼_ _i_ from the line of sight. The effect of de-projection is
essentially to change the _z_ scale to the extent that, to first order, _z_ may be approximated by a linear
function of _V_ _z_ . In particular, in principle, the large Doppler velocity components may be confined
to the very close environment of the star. In order to get some idea of a possible geometry, we
use an example illustrated in the left panel of Figure 5, where we assume arbitrarily that a stream
velocity of 20 km s _[−]_ [1] is reached over a distance of 60 au along the line of sight. Approximating
the stream projections on the P-V maps of Figure 1 as shown by black arrows, we find that the
red-shifted stream reaches this distance at _∼−_ 0 _._ 1 arcsec in _x_ and _∼_ 0.1 arcsec in _y_ while the blueshifted stream reaches it at _∼_ 0.1 arcsec in _x_ and _∼−_ 0 _._ 35 arcsec in _y_ . This means an angle of _∼_ 8 _[◦]_

between the red-shifted stream and the line of sight, an angle of _∼_ 20 _[◦]_ between the blue-shifted
stream and the line of sight, and an angle of _∼_ 14 _[◦]_ between the two streams. Of course, these
numbers scale with the arbitrary length of 60 au used in the example and are simply meant to
illustrate a possible stream geometry.
The _x_ and _y_ profiles of the gas streams (excluding HCN) are illustrated in the right panels
of Figure 5. They are referred to the stream axes indicated as black arrows in Figure 1 and have
Doppler velocities in excess of the slow wind end-point velocities listed above. On average, they

High Doppler velocity wings in the nascent wind of R Doradus 7


**Fig.** **1.** P-V maps in the _V_ _z_ vs _x_ and vs _y_ planes. The colour scale is in units of Jy
arcsec _[−]_ [1] . Yellow lines show the cuts applied in the definition of the large Doppler velocity
components. The SO map extends up to 2 arcsec. The black arrows cover from the origin
to ( _x,_ _y_ )=(0.1, _−_ 0.35) arcsec and _V_ _z_ = _−_ 20 km s _[−]_ [1] in the blue-shifted hemisphere and to
( _x,_ _y_ )=( _−_ 0.1,0.1) arcsec and _V_ _z_ =20 km s _[−]_ [1] in the red-shifted hemisphere.


**Fig. 2.** Intensity maps of the high _|V_ _z_ _|_ components. Contours show the red-shifted stream,
the colour maps show the blue-shifted stream. The colour scale is in units of Jy beam _[−]_ [1]

km s _[−]_ [1] . The contour levels are at 10%, 20%, 30%, 50%, 70% and 90% of the peak
intensity of the blue-shifted stream. The beams are shown in the lower left corners. The
white crosses mark the position of the continuum peak.


are well centred to within _±_ 30 mas (1.8 au); Gaussian fits give standard deviations with respect to
the mean of 90 mas in _x_ and 120 mas in _y_, meaning, after beam de-convolution, 70 mas (4.2 au) in _x_
and 90 mas (5.4 au) in _y_ . The opening angle of the streams depends on their longitudinal extension;
using as an example a mean distance of 30 au along the line of sight, this would correspond to an
opening angle (standard deviation) of _±_ 9 _[◦]_ .
While beyond the scope of the present article, we note the presence of significant depletions
in well-defined regions of the data-cubes, in particular between Doppler velocities of _−_ 1 and 3 km

8 D. T. Hoai


**Fig. 3.** Channel maps of the large Doppler velocity components of the SO line in the blueshifted (upper panels) and red-shifted (lower panels) hemispheres. For each hemisphere
we use 1 km s _[−]_ [1] bins in _|V_ _z_ _|_, the velocity is indicated in the upper left corner of each
panel. The common colour scale is in units of mJy beam _[−]_ [1] . The white crosses mark the
position of the continuum peak.

High Doppler velocity wings in the nascent wind of R Doradus 9


**Fig.** **4.** Doppler velocity spectrum of SO emission summed in the sky plane over a 1
arcsec radius circle centred on the star. The red lines are linear fits to the edge of the
profile used to define the separation of the large Doppler velocity components from the
slow wind.


**Fig. 5.** Left panel: illustration of a possible geometry assuming that the streams reach a
velocity of 20 km s _[−]_ [1] over a distance of 60 au along the line of sight (see text). Right
panels: dependence of the integrated intensity on _x_ (upper panels) and _y_ (lower panels)
measured with respect to the stream axes defined by black arrows in Figure 1. Lines
are labelled on top of the upper panels. The integration is made over _|V_ _z_ _| >_ 7.0, 8.3,
6.2 and 6.0 km s _[−]_ [1] for CO, SiO, SO and SO 2 respectively. For convenience, different
arbitrary scales are used for different lines. Blue and red profiles are for blue-shifted and
red-shifted hemispheres respectively. The curves show Gaussian fits.


s _[−]_ [1] . This is reminiscent of the blue-western depletion observed in EP Aqr by Tuan-Anh et al.
(2019) [24], who argue that it may be related to the nascent streams. In the present case, the
complexity of the observed morpho-kinematics [21] prevents from asserting reliably the existence
of such a relation.

|D<br>.|T Hoai<br>.|
|---|---|
|D.||


**Fig. 6.** Doppler velocity distributions obtained for _|V_ _z_ _| >_ 8 km s _[−]_ [1] using two datasets of
SiO line emission having significantly different _uv_ coverage. The continuum, which has
not been subtracted, is seen at the level of 0 _._ 6 Jy. The dataset having the larger maximal
recoverable scale is shown for _R <_ 1 _._ 5 arcsec (red) and for _R <_ 0 _._ 3 arcsec (blue). The
dataset having the smaller maximal recoverable scale is shown for _R <_ 1 _._ 5 arcsec (black).


**III.2** . **Eliminating a possible effect related to continuum subtraction**


The confinement of the red-shifted stream in the vicinity of the line of sight crossing the
star in its centre comes as a surprise: at variance with EP Aqr, where axi-symmetry about this
line of sight is well established, R Dor displays no obvious axi-symmetry and this line of sight
does not seem to play any particular role in the complex morpho-kinematics of the circumstellar
envelope [12,21,28]. In particular, the rotation axis observed by Homan et al. [12] makes an angle
of only 20 _±_ 20 _[◦]_ with the plane of the sky. This remark may suggest that the gas stream appearance
of the high velocity wings is not real but is mimicked by some effect that has been overlooked.
If such were the case, it would also shed doubts on the validity of the gas stream interpretation
in the case of EP Aqr. It is therefore essential to review critically such possible effects. The next
section discusses possible physical interpretations. Here, we address instead a possible effect of
inadequate continuum subtraction.
As continuum emission is confined near the star and covers uniformly the observed range
of Doppler velocities, inadequate continuum subtraction is a candidate for producing artefacts
mimicking high velocity wings emitted along the line of sight near the origin of coordinates.
The data used in the present work have been obtained after subtraction in the _uv_ plane of the
contribution of continuum emission. An imperfection in the procedure of Fourier-transforming
from the _uv_ plane to the sky plane or of producing the clean maps might have generated the
undesired artefacts and have remained unnoticed. In order to check on this, we repeated the
analysis of the SiO observations without performing any continuum subtraction, namely Fouriertransforming directly the measured visibilities. Not subtracting the continuum is a simplification
and obviously does not affect significantly the main results in terms of beam size, maximum
recoverable scale, etc. The result is illustrated in Figure 6 using two datasets having different
antenna configurations. The Doppler velocity distributions obtained for _|V_ _z_ _| >_ 8 km s _[−]_ [1] display
uniform continuum emission beyond _|V_ _z_ _| >_ 20 km s _[−]_ [1] at a level of _∼_ 0 _._ 60 _±_ 0 _._ 03 Jy on both redshifted and blue-shifted sides. Here the uncertainty accounts for both noise levels and differences
between different data sets. In comparison, the continuum level measured by Decin et al. [5] is

High Doppler velocity wings in the nascent wind of R Doradus 11


0.65 Jy with an uncertainty that does not exceed 0.01 Jy: our result is therefore _∼_ 0 _._ 05 _±_ 0 _._ 03
Jy smaller. While of little relevance to the argument of the present article, this small difference
is significant and probably reveals systematic differences in the data samples used and in their
reduction. This result gives confidence in the reality of the high Doppler velocity components,
seen to rise above continuum emission below _|V_ _z_ _| ∼_ 20 km s _[−]_ [1] . It displays a remarkable symmetry
between blue-shifted and red-shifted wings, at variance with an earlier interpretation of the “blue
blob” as causing one-sided ejection of material [28]. It provides evidence for the emission to
be essentially contained within an aperture radius of 0.3 arcsec (18 au). The mean projected
acceleration, averaged over the ( _V_ _z_ vs _y_ ) P-V maps of Figure 1 is 0.68 _±_ 0.10 km s _[−]_ [1] au _[−]_ [1] . However,
to the extent that the large Doppler velocities are interpreted in terms of radial expansion, namely
that blue- and red-shifted components are emitted from opposite sides of the star, the nearly perfect
blue-red symmetry would suggest that effects of absorption and radiative transfer are small and
can be ignored.


**III.3** . **Interpretations in terms of pulsations or rotations**

A gas stream interpretation implies that the streams are accelerated to nearly 20 km s _[−]_ [1]

over long enough a distance to justify such a description. Quantitatively, we may get an idea of
how long if we accept that the streams are approximately symmetric with respect to the star. The
projected acceleration being estimated to reach _∼_ 0.7 km s _[−]_ [1] au _[−]_ [1] on the blue-shifted side, the
Doppler velocity of 20 km s _[−]_ [1] is reached near 30 au projected distance from the star. If the blueshifted stream were in the plane of the sky, it would reach a space velocity of 20 km s _[−]_ [1] in _∼_ 30 au
and so would the red-shifted stream. But in projected distance the red-shifted stream stays within
some 10 au from the star. Then, it would make an angle of cos _[−]_ [1] (10 _/_ 30) = 70 _[◦]_ with the plane of
the sky (which contains the blue-shifted stream) contradicting the hypothesis that the two streams
are nearly symmetric. If the blue-shifted stream makes an angle _i_ _B_ and the red-shifted stream an
angle _i_ _R_ with the line of sight, the common stream length is 30 _/_ sin _i_ _B_ = 10 _/_ sin _i_ _R_ au, the right
hand side of the equation being an upper limit, namely sin _i_ _R_ _<_ [1] _/_ 3 sin _i_ _B_ . For _i_ _B_ = 30 _[◦]_ _i_ _R_ _<_ 10 _[◦]_

corresponding to a stream length of 60 au. This very crude estimate gives the scale of acceptable
stream lengths in the hypothesis of approximately symmetric streams; it corresponds to a space
acceleration of _∼_ 1.5 km s _[−]_ [1] au _[−]_ [1] . If the acceleration was more sudden other interpretations, such
as stellar pulsations or rotation, would become possible.
In the case of rotation, one would typically expect a line profile covering twice the maximal
rotation velocity. Homan et al. (2018b) [12] quote a rotation velocity of only 12 km s _[−]_ [1] at a
distance of 6 au from the star. Keplerian rotation would imply that the maximal observed velocity
of 20 km s _[−]_ [1] would be reached at only _∼_ 2.2 au from the star centre, very close to the stellar
surface. The absence of detection in the [28] SiO( _ν_ = 1 _,_ _J_ = 8 _−_ 7) data analysed by Homan et
al. (2018b) [12] would then have to be blamed on insufficient sensitivity if a Keplerian rotation
scenario was retained. Vlemmings et al. (2018) [28] quote a solid body rotation of 1.0 _±_ 0.1 km
s _[−]_ [1] at the stellar surface ( _∼_ 1.9 au) meaning that a rotation velocity of 20 km s _[−]_ [1] would be reached
at a distance of _∼_ 38 au from the star, nearly twice as far as the canonical limit that has been set.
Unfortunately, the authors do not comment on the high Doppler velocity wings in general. They
only illustrate the blue-shifted stream, which they claim to be one-sided, with a P-V diagram of
29 SiO( _ν_ = 0 _,_ _J_ = 5 _−_ 4) data that is consistent with the gas stream interpretation.

12 D. T. Hoai


An interpretation in terms of a pulsating spherical shell is equally challenging. It has been
explicitly excluded by Decin et al. (2018) [5] on the basis of a model [22]. For an expanding
spherical shell to reproduce the narrow high velocity features observed in Figure 1, its radius must
not exceed some 15 to 20 au. In principle, the very high angular resolution observations analysed
by Vlemmings et al. (2018) [28] should allow for a measurement of the maximal Doppler velocity
reached within an aperture at au scale. Unfortunately the authors do not address the issue: no
measurement of the maximal velocity reached in a very small aperture is quoted.
Both interpretations, rotation and pulsation, predict red-blue symmetry in contrast with
what is observed. The possible presence of a companion, interfering with the blue-shifted high
velocity wing, could then be invoked. Decin et al. (2018) [5], followed by Homan et al. (2018b)

[12] and Vlemmings et al. (2018) [28] have noted that such presence would provide a welcome
explanation of the large angular momentum implied by the observed rotation.


**IV** . **CONCLUSION**


Evidence has been obtained for a possible description of the nascent wind of AGB star R
Dor in terms of a pair of high velocity gas streams emitted nearly back-to-back near the line of
sight. They are reminiscent of those observed in similar conditions in the nascent wind of EP Aqr,
an AGB star having properties very similar to R Dor. However, at variance with EP Aqr, the R Dor
streams make a large angle with the rotation axes favoured by Vlemmings et al. (2018) [28] for
the star and by Homan et al. (2018b) [12] for the rotating disc surrounding it. This may suggest
that they be artefacts of improper data reduction and/or continuum subtraction but an analysis of
continuum-unsubstracted data confirms the validity of the gas stream interpretation. Moreover,
interpretations in terms of rotation or pulsations have been shown to meet important difficulties
that prevent retaining such interpretations with reasonable confidence. A possibility that has not
been seriously explored would be that the large Doppler velocities, rather than revealing large
radial wind velocities, would instead reveal large line widths caused by turbulence, which would
then be dominantly detected on the Earth side of the star atmosphere and would provide a simple
explanation for the nearly perfect blue-red symmetry displayed in Figure 6. In principle, important
relevant information should be contained in the very high angular resolution ALMA observations
analysed by Vlemmings et al. (2018) [28] but, as far as we know, the issue has not been addressed
by the authors in published material. The presence of large velocity components, reaching three
times the terminal wind velocity, less than 100 au from each of two similar AGB stars, cannot be
ignored when attempting a description of the mechanism governing the launch of their nascent
wind and the breaking of the spherical symmetry present in the Red Giant phase. However, today,
no fully convincing interpretation of the physics governing their existence can be reliably proposed. Future high resolution studies of other AGB stars displaying significantly higher Doppler
velocities than the terminal wind will help clarifying this important issue.


**ACKNOWLEDGEMENT**


We are grateful to Dr Ward Homan for sharing with us information on the analysis of
R Doradus observations and to Professor Albert Zijlstra for support and advice. We thank the
referees Professors Jan Martin Winters and Pierre Lesaffre for useful comments that helped improving the quality of the manuscript. This paper makes use of the following ALMA data:

High Doppler velocity wings in the nascent wind of R Doradus 13


ADS/JAO.ALMA#2017.1.00824.S and ADS/JAO.ALMA#2013.1.00166.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.
[The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ. We](http://jvo.nao.ac.jp/portal)
are deeply indebted to the ALMA partnership, whose open access policy means invaluable support
and encouragement for Vietnamese astrophysics. Financial support from the World Laboratory,
VNSC and NAFOSTED is gratefully acknowledged. This research is funded by the Vietnam National Foundation for Science and Technology Development (NAFOSTED) under grant number
103.99-2018.325.


**REFERENCES**


[1] T.R. Bedding, A.A Zijlstra, A. Jones & G. Foster, MNRAS 301(1998) 1073

[2] J. Cernicharo, J. Alcolea, A. Baudry & E. Gonzalez-Alfonso, A&A 319(1997) 607

[3] T. Danilovich, E. De Beck, J.H. Black et al., A&A 588(2016) A119

[4] E. De Beck & H. Olofsson, A&A 615(2018) A8

[5] L. Decin, A.M.S. Richards, T. Danilovich et al., A&A 615(2018) A28

[6] P. de Vicente et al.,A&A 589(2016) A74

[7] T. Dumm & H. Schild, New Astr. 3(1998) 137

[8] Gaia Collaboration, 2018, VizieR Online Data Catalog, I/345

[9] M. Heras & S. Hony, A&A 439(2005) 171

[10] D.T. Hoai, P.T. Nhung, P. Tuan-Anh et al., MNRAS 484(2019) 1865

[11] W. Homan, A. Richards, L. Decin et al., A&A 616(2018a) A3

[12] W. Homan, T. Danilovich, L. Decin et al., A&A 614(2018b) A113

[13] K. Justtanont, T. Khouri, M. Maercker et al., A&A 537(2012) A144

[14] T. Khouri, M. Maercker, L.B.F.M. Waters et al., A&A 591(2016) A70

[15] G.R. Knapp, D. Pourbaix, I. Platais & A. Jorissen, A&A 403(2003) 993

[16] T. Lebzelter & J. Hron, A&A 351(1999) 533

[17] T. Lebzelter, & K.H. Hinkle, A&A 393(2002) 563

[18] M. Maercker, T. Danilovich, H. Olofsson et al., A&A 591(2016) A44

[19] I. McDonald & A.A. Zijlstra, ApJ 823(2016) L38

[20] P.T. Nhung, D.T. Hoai, P. Tuan-Anh P. et al., RAA 19(2019a) 43

[21] P.T. Nhung, D.T. Hoai, P. Tuan-Anh et al., MNRAS 490(2019b) 3329

[22] W. Nowotny, S. H¨ofner & B. Aringer, A&A 514(2010) A35

[23] S. Ramstedt & H. Olofsson, A&A 566(2014) A145

[24] P. Tuan-Anh, D.T. Hoai, P.T. Nhung et al., MNRAS 487(2019) 622

[25] Van de Sande M., Decin L., Lombaert, et al., 2015, EAS Publications Series, 71-72, 255-257

[26] M. Van de Sande, L. Decin, R. Lombaert et al., A&A 609(2018) A63

[27] F. van Leeuwen, A&A, 474(2007) 653

[28] W.H.T. Vlemmings, T. Khouri, E. De Beck et al., A&A 613(2018) L4

[29] J.M. Winters, T. Le Bertre, K.S. Jeong et al., A&A 409(2003) 715


</paper>

## Items to check

```json
[
 {
  "path": "data.alma_project_codes[0].evidence[1]",
  "value": "2017.1.00824.S",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00824.S and ADS/JAO.ALMA#2013.1.00166.S."
 },
 {
  "path": "data.alma_project_codes[1].evidence[1]",
  "value": "2013.1.00166.S",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00824.S and ADS/JAO.ALMA#2013.1.00166.S."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[1]",
  "value": "Continuum flux level (0.65 Jy), 'blue-blob' feature, and channel maps in project 2013.1.00166.S",
  "failed_quote": "In comparison, the continuum level measured by Decin et al. [5] is 0.65 Jy with an uncertainty that does not exceed 0.01 Jy"
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Define stream axes in P-V maps from origin to (x, y) = (0.1, -0.35) arcsec at Vz = -20 km s^-1 (blue-shifted) and (-0.1, 0.1) arcsec at Vz = 20 km s^-1 (red-shifted); integrate intensity above slow-wind end-point velocities (|Vz| > 7.0, 8.3, 6.2, 6.0 km s^-1 for CO, SiO, SO, SO2) and fit 1D Gaussians to transverse x and y profiles with respect to stream axes; compute beam-deconvolved widths and me",
  "failed_quote": "On average, they are well centred to within ±30 mas (1.8 au); Gaussian fits give standard deviations with respect to the mean of 90 mas in x and 120 mas in y, meaning, after beam de-convolution, 70 mas (4.2 au) in x and 90 mas (5.4 au) in y."
 },
 {
  "path": "analysis_steps[3].validation.evidence[1]",
  "value": "Compared unsubtracted continuum flux (~0.60 ± 0.03 Jy) beyond |Vz| > 20 km s^-1 with Decin et al. (2018) value (0.65 ± 0.01 Jy) and verified consistency between two datasets with different uv coverage.",
  "failed_quote": "In comparison, the continuum level measured by Decin et al. [5] is 0.65 Jy with an uncertainty that does not exceed 0.01 Jy: our result is therefore ∼ 0.05 ± 0.03 Jy smaller."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Stream centring accuracy relative to stream axes = 0 mas",
  "failed_quote": "On average, they are well centred to within ±30 mas (1.8 au); Gaussian fits give standard deviations with respect to the mean of 90 mas in x and 120 mas in y, meaning, after beam de-convolution, 70 mas (4.2 au) in x and 90 mas (5.4 au) in y."
 }
]
```
