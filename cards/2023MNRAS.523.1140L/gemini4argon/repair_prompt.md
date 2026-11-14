# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.523.1140L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–13 (2023) Preprint 12 May 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **NGC 1436: the making of a lenticular galaxy in the Fornax cluster**


Alessandro Loni, [1][,][2] [⋆] Paolo Serra, [2] Marc Sarzi, [1] Gyula I. G. Józsa, [3][,][4] Pablo M. Galán−de Anta, [1][,][5] Nikki Zabel, [6]

Dane Kleiner, [7][,][2] Filippo M. Maccagni, [7][,][2] Daniel Molnár, [2] Mpati Ramatsoku, [4][,][2] Francesca Loi, [2]

Enrico M. Corsini, [8][,][9] D. J. Pisano, [6] Peter Kamphuis, [10] Timothy A. Davis, [11] W. J. G. de Blok, [7][,][12][,][13]

Ralf J. Dettmar, [10] Jesus Falcon-Barroso, [14][,][15] Enrichetta Iodice, [16] Maritza A. Lara-López, [17]

S. Ilani Loubser, [18] Kana Morokuma-Matsui, [19] Reynier Peletier, [12] Francesca Pinna, [20] Adriano Poci, [21]

Matthew W. L. Smith, [11] Scott C. Trager, [12] and Glenn van de Ven [22]

1 _Armagh Observatory and Planetarium, College Hill, Armagh BT61 9DG, UK_
2 _INAF_ − _Osservatorio Astronomico di Cagliari, Via della Scienza 5, 09047, Selargius, CA, Italy_
3 _Max-Plank-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany_
4 _Department of Physics and Electronics, Rhodes University, PO Box 94, Makhanda 6140, South Africa_
5 _Astrophysics Research Centre, School of Mathematics and Physics, Queen’s University Belfast, Belfast BT7 INN, UK_
6 _Department of Astronomy, University of Cape Town, Private Bag X3, Rondebosch 7701, South Africa_
7 _Netherlands Institute for Radio Astronomy (ASTRON), Oude Hoogeveensedĳk 4, 7991 PD Dwingeloo, the Netherlands_
8 _Dipartimento di Fisica e Astronomia “G. Galilei”, Università di Padova, vicolo dell’Osservatorio 3, I-35122 Padova, Italy_
9 _INAF - Osservatorio Astronomico di Padova, vicolo dell’Osservatorio 2, I-35122 Padova, Italy_
10 _Ruhr University Bochum, Faculty of Physics and Astronomy, Astronomical Institute, 44780 Bochum, Germany_
11 _School of Physics and Astronomy, Cardiff University, Queens Buildings The Parade, Cardiff, CF24 3AA, UK_
12 −
_Kapteyn Astronomical Institute, University of Groningen, PO Box 800, NL_ _9700 AV Groningen, the Netherlands_
13 _The Inter-University Institute for Data Intensive Astronomy, Department of Astronomy, University of Cape Town,_
_Private Bag X3, Rondebosch, 7701, South Africa_
14 _Instituto de Astrofísica de Canarias, Vía Láctea s/n, E-38205 La Laguna, Tenerife, Spain_
15 _Departamento de Astrofísica, Universidad de La Laguna, E-38200 La Laguna, Tenerife, Spain_
16 _INAF_ − _Astronomical Observatory of Capodimonte, Salita Moiariello 16, 80131, Naples, Italy_
17 _Departamento de Física de la Tierra y Astrofísica, Instituto de Física de Partículas y del Cosmos, IPARCOS._
_Universidad Complutense de Madrid (UCM), 28040, Madrid, Spain_
18 −
_Centre for Space Research, North_ _West University, Potchefstroom 2520, South Africa_
19 _Center for Computational Sciences, University of Tsukuba, Ten-nodai, 1-1-1 Tsukuba, Ibaraki 305-8577, Japan_
20 _Max-Planck-Institut für Astronomie, Königstuhl 17, D-69117 Heidelberg, Germany_
21 _Centre for Extragalactic Astronomy, University of Durham, Stockton Road, Durham DH1 3LE, United Kingdom_
22 _Department of Astrophysics, University of Vienna, Türkenschanzstraße 17, 1180 Vienna, Austria_


Accepted 2023 May 09. Received 2023 May 08; in original form 2023 March 02


**ABSTRACT**

We study the evolutionary path of the Fornax cluster galaxy NGC 1436, which is known to be currently transitioning from a spiral
into a lenticular morphology. This galaxy hosts an inner star-forming disc and an outer quiescent disc, and we analyse data from
the MeerKAT Fornax Survey, ALMA, and the Fornax 3D survey to study the interstellar medium and the stellar populations of
both disc components. Thanks to the combination of high resolution and sensitivity of the MeerKAT data, we find that the H I is
entirely confined within the inner star-forming disc, and that its kinematics is coincident with that of the CO. The cold gas disc
is now well settled, which suggests that the galaxy has not been affected by any environmental interactions in the last ∼ 1 Gyr.
The star formation history derived from the Fornax 3D data shows that both the inner and outer disc experienced a burst of star
formation ∼ 5 Gyr ago, followed by rapid quenching in the outer disc and by slow quenching in the inner disc, which continues
forming stars to this day. We claim that NGC 1436 has begun to effectively interact with the cluster environment 5 Gyr ago,
when a combination of gravitational and hydrodynamical interactions caused the temporary enhancement of the star-formation
rate. Furthermore, due to the weaker gravitational binding H I was stripped from the outer disc, causing its rapid quenching. At
the same time, accretion of gas onto the inner disc stopped, causing slow quenching in this region.


**Key** **words:** Galaxies: individual: NGC 1436 – Galaxies: evolution – Galaxies: ISM – Galaxies: star formation – Galaxies:

cluster


⋆ E-mail: alessandro.loni@armagh.ac.uk (AL)
© 2023 The Authors

2 _A. Loni et al._


**1** **INTRODUCTION**


Due to their discy structure and old stellar populations lenticular
galaxies (S0s) share properties both with spirals and ellipticals (Hubble 1936; van den Bergh 1976). The distribution and fractional number of lenticular galaxies in the Universe at different epochs (lower
at higher redshift and outside groups and clusters of galaxies) suggest that they form mainly (but not always, c.f. van den Bergh 2009)
from the evolution of blue star-forming spiral galaxies in dense environments (Dressler 1980; Dressler et al. 1997; Fasano et al. 2000;
Postman et al. 2005). Although there are still many open questions
about how this morphological transformation happens, it is clear that
environmental interactions can play an important role (e.g. Merritt
1983; Moore et al. 1996).

A peculiar characteristic of the morphological evolution of galaxies in dense environments is that it proceeds outside-in. This transformation requires, in the first place, to stop cold gas accretion onto
galaxies, which would otherwise supply material to form new stars.
This process is commonly referred to as "starvation" (Larson et al.
1980). Then, the cold gas, mainly made of neutral atomic hydrogen
(H I ), may be actively removed from the outer disc, where the weaker
gravitational potential is not able to hold it in place against the action of environmental interactions. Therefore, whereas the outskirts
of galaxies, which are experiencing cold gas removal, are quenched
quickly if no further cold gas is supplied, star formation can continue
in the inner - and still H I rich - part of these systems. The outside-in
transformation of galaxies which live in dense environments is opposite to what happens to field and void galaxies, where accretion
of gas from the intergalactic medium generally keeps fuelling starformation in the outer disc (e.g. Bell & de Jong 2000; Boselli &
Gavazzi 2006; Boselli et al. 2006).

Through the study of the distribution and kinematics of the cold
gas, one can gain information on which kind of interactions a galaxy
might have experienced after its starvation has begun (if at all). On the
one hand hydrodynamical interactions (e.g. ram pressure stripping
Gunn & Gott 1972; Abadi et al. 1999; Quilis et al. 2000), which only
affect the gas component, cause highly asymmetric perturbations
in the cold gas distribution, producing H I tails which trail along
the orbit of the galaxy. On the other hand, the footprint of tidal
interactions in the cold gas distribution and possibly in the stellar disc
is more symmetric as one can see in some two tailed objects in Arp
(1966), whose evolutionary scenarios are discussed and modelled by
Struck & Smith (2012). Indeed, these interactions can cause two long
streams of material in opposite directions (although they can have
very different sizes).

The main difference between starvation and starvation plus active
gas removal concerns different quenching time scales. Although in
the literature there are several definitions of quenching timescale (see
Cortese et al. 2021 for a discussion), starvation implies longer time
scales for a galaxy to halt its star formation (roughly 4 Gyr; Boselli
et al. 2014b) with respect to the shorter time scales due to active gas
removal (of the order of a few hundreds of Myr). If the study of the
cold gas distribution and kinematics can help us understand the cause
of relatively recent gas removal, the analysis of the stellar populations
and, thus, of the star formation history (SFH) of a galaxy is crucial
to distinguish between slow (starvation-like) and fast (stripping-like)
quenching.

One of the members of the nearby Fornax galaxy cluster (distance ∼ 20 Mpc; Jensen et al. 2001; Tonry et al. 2001; Blakeslee
et al. 2009; Spriggs et al. 2021), NGC 1436 (FCC 290), is a perfect target to study "how" and "how quickly" the evolution of spirals
into S0’s can happen in dense environments. This galaxy is located


MNRAS **000**, 1–13 (2023)



-35°50'00"


51'00"


52'00"


53'00"





3 ~~[h]~~ 43 ~~[m]~~ 45 ~~[s]~~ 40 ~~[s]~~ 35 ~~[s]~~ 30 ~~[s]~~


RA (J2000)


**Figure** **1.** Optical _g_ −band image of NGC 1436 from the Fornax Deep Survey (Peletier et al. 2020) showing the morphological distinction between the
inner star-forming regions characterised by flocculent spiral features and the
quiescent and smoother outer disc. The footprint of the Fornax3D observations for NGC 1436 (Sarzi et al. 2018) (white squares) and the map of the
Hα emission detected in the MUSE data by Iodice et al. 2019b (yellow) are
also shown. The latter measurements set the extent of the star-forming disc
( _R_ SF 59 [′′], dashed green line), while the cyan isophotal radius measured
at 25 mag arcsec [−][2] in B-band (de Vaucouleurs et al. 1991) gives an overall
indication for the extent of NGC 1436.


∼ 0.5×R vir = 350 kpc south-east from the center of the cluster, and
it has a systemic velocity of 1392 km s [−][1] similar to the recessional
velocity of the Fornax cluster (1442 km s [−][1], Maddox et al. 2019).
Neither the 2D distribution of the Fornax galaxies nor their position
in the projected phase space diagram (Iodice et al. 2019a) show any
obvious companion for NGC 1436. The closest galaxy with a known
redshift is FCC 298, which is at 17 [′] ∼ 100 kpc, and ∼230 km s [−][1] away
from NGC 1436. Deep optical observations from the Fornax Deep
Survey (Peletier et al. 2020) suggest that NGC 1436 is in the transitional stage to become a S0 (Iodice et al. 2019b; Raj et al. 2019).
In Fig. 1 we see that the disc of NGC 1436 shows two distinct parts:
a clumpy inner disc with a tightly wound spiral structure, abundant
dust with numerous star-forming regions, and an outer disc which
appears featureless (no dust, spiral arms, or star forming regions).
Raj et al. (2019) measured a break in the surface brightness slope at
their boundary.
Data from the Fornax 3D survey (Sarzi et al. 2018) obtained with
the Multi-Unit Spectroscopic Explorer (MUSE) on the ESO Very
Large Telescope also show how this galaxy is still forming stars in
the inner disc (see the Hα emission in Fig. 1) while its outskirts
appear to be already quenched (Iodice et al. 2019b). This is further
supported by the Atacama Large Millimeter/submillimeter Array
(ALMA) measurement of Zabel et al. (2019), which reveals the presence of molecular gas only within the inner disc. Zabel et al. (2021)
found that the radial profile of the H 2 -to-dust ratio in NGC 1436
drops suddenly at a radius of 3.5 kpc, suggesting that environmental
interactions were more efficient in removing dust rather than H 2 .
In this multi-wavelength picture of NGC 1436, high resolution
H I data were still missing. Indeed, the H I resolution and sensitivity
of the recent interferometric ATCA H I survey of Fornax (∼ 1 [′] and
∼ 10 [7] M ⊙, respectively; Loni et al. 2021) are insufficient to _(i)_

_NGC 1436: the making of a lenticular galaxy in the Fornax cluster_ 3



establish whether the galaxy has recently interacted with the cluster
environment _(ii)_ recover the same total H I flux of a single dish (the
ATCA H I flux is 2.8× lower than that measured with the Green Bank

Telescope – by Courtois et al. 2009).
In this paper we present H I data of NGC 1436 from the MeerKAT
Fornax Survey (Serra et al. 2023), whose resolution and sensitivity
are at least a factor of 10 better than those of the previous ATCA
H I data. We then compare the H I distribution and kinematics with
those of CO (Zabel et al. 2019). This will establish whether the cold
gas disc is well settled (if they are both distributed regularly and
co-rotate), and thus whether NGC 1436 is currently in a state of
slow evolution (no sign of recent interactions such as asymmetries).
Finally, using MUSE data from the Fornax 3D survey (Sarzi et al.
2018), we measure and compare the SFH of the inner star-forming
disc with that of the outer quiescent disc. By performing this analysis,
we aim to understand in which epoch environmental interactions
might have become relevant for this galaxy, and what consequences
these had for its evolution.

The paper is organized as follows: in Sect 2 we present the
MeerKAT, ALMA and MUSE data. In Sect. 3 we analyse the distribution and kinematics of H I and CO. In Sect. 4 we describe the MUSE

data analysis and the measurement of the SFH of the quiescent and
star-forming disc. In Sect. 5 we discuss the most likely evolutionary
scenario which explains both the distribution and kinematics of the
cold gas disc and the SFH of the quiescent and star-forming discs of
NGC 1436, and in Sect. 6 we summarise our results.


**2** **DATA**


**2.1** **MeerKAT**


We study the distribution and kinematics of H I in NGC 1436 using
data products from the MeerKAT Fornax Survey. The survey goals,
design, observations and H I data processing are described in Serra
et al. (2023). Here we make use of the H I subcubes and moment
images of NGC 1436 at a resolution of 11 [′′] and 66 [′′] (see Table 2 in
Serra et al. 2023). The 11 [′′] cube has a noise level of 0.28 mJy beam [−][1]

and a 3σ H I column density sensitivity of 4.5 × 10 [19] cm [−][2] . The
66 [′′] cube has a noise level of 0.29 mJy beam [−][1] and a 3σ H I column
density sensitivity of 1.3 × 10 [18] cm [−][2] . In both cases the column
density sensitivity is calculated assuming a linewidth of 25 km s [−][1] .
The spectral resolution of both cubes is 1.4 km s [−][1] .


**2.2** **ALMA**


The ALMA observations of the [12] CO(1–0) line used in this work,
whose data reduction is described in Zabel et al. (2021), consist
of a combination of high resolution data from the ALMA Fornax
Cluster Survey obtained with the 12-m configuration array (Zabel
et al. 2019) and deep data from the ALMA archive (MorokumaMatsui et al. 2022) obtained with the Atacama Compact Array. The
final cube has a velocity resolution of 10 km s [−][1], a synthesized beam
size of 2.68 [′′] ×2.06 [′′], and a noise level of ∼2.0 mJy beam [−][1] .


**2.3** **MUSE**


The MUSE data used in this work were collected as part of the
Fornax 3D survey (Sarzi et al. 2018). The MUSE telescope (Bacon
et al. 2010) ensures high-quality 3D spectroscopy with: ( _i_ ) a spatial
sampling of 0.2 [′′] ×0.2 [′′] in a field of view of 1 [′] ×1 [′], per pointing; ( _ii_ ) a
wavelength range of 4650-9300 Å with a nominal spectral resolution



of 2.5 Å (FWHM) at 7000 Å and a spectral sampling of 1.25 Å/pixel.
Due to the combination of different, slightly offset, exposures taken
at different position angles (PAs), the average spectral resolution is
2.8 Å (FHWM). The data reduction, performed using the MUSE
pipeline version 1.6.2 (Weilbacher et al. 2012, 2016) is described in
Sarzi et al. (2018).


**3** **MORPHOLOGY AND KINEMATICS OF THE COLD GAS**

**DISC**


Since H I discs are usually more extended than the stellar ones, they
are excellent tracers of recent/on-going interactions with the local
environment. As mentioned in Sect. 1, previous results on the H I
emission in NGC 1436 (Loni et al. 2021) are not exhaustive and also
have a large discrepancy with single dish data from Courtois et al.
(2009). The high sensitivity, spatial and spectral resolution of the
MeerKAT Fornax Survey data fulfils well our needs, providing us
with an ideal data-set to study in detail the properties of the cold
gas disc of NGC 1436. The high-resolution cube allows us to gain
information both on the H I morphology and kinematics, while the
low-resolution cube, with better column density sensitivity, might
recover more flux.
Fig. 2 shows both the 11 [′′] and 66 [′′] resolution HI images, while
the bottom left panel shows their comparison after smoothing the
former to the resolution of the latter. Note that the 11 [′′] image was
made with a different Briggs robust and a different detection mask
than the 66 [′′] image, and therefore could in principle miss some of the
66 [′′] outer flux (see Serra et al. 2023). We see that the match between
these contours is excellent, meaning that NGC 1436 does not host any
diffuse, low-column density H I in excess of the H I detected at high
resolution. This implies that the H I disc is sharply truncated and does
not extend beyond the inner, star-forming disc of NGC 1436. Since
the data are extremely sensitive, and the H I cubes do not show any
evidence of distortions, asymmetries or tails at low column density,
we can confidently rule out any recent disturbance to the gas disc,
while we see the presence of a H I depression in the center of the
galaxy.
The agreement between the 11 [′′] and 66 [′′] H I data cubes is also
clear in the bottom right panel of Fig. 2, where we compare the
spectra extracted using the respective detection masks. We also show
the single-dish spectrum (GBT - Courtois et al. 2009), whose total
flux is consistent with those measured with MeerKAT within 1σ.

Using Eq. 50 in Meyer et al. (2017), we estimate the total _M_ H I to
be [�] 1.9 ± 0.2 [�] × 10 [8] M ⊙ . Based on ATCA data, Loni et al. (2021)
pointed out that NGC 1436 is a H I -deficient galaxy with a large
_M_ H 2 / _M_ H I ratio. These results do not change if we use the MeerKAT
_M_ H I value, which is 4σ larger than the ATCA one, the same _M_ ⋆
value calculated in Loni et al. (2021), and the _M_ H 2 value by Zabel
et al. (2021) (which is a factor ∼1.4 smaller than that used in Loni
et al. 2021 from Zabel et al. 2019). Indeed, ( _i_ ) the offset between
the _M_ H I / _M_ ⋆ ratio of NGC 1436 and the xGASS _M_ H I - _M_ ⋆ scaling
relation (Catinella et al. 2018) is still larger than the RMS deviation
of a sample of non-cluster galaxies (Kreckel et al. 2012; Boselli et al.
2014a) and ( _ii_ ) the _M_ H 2 / _M_ H I ratio of NGC 1436 is 1.0±0.1, resulting
∼ 12 σ above the xGASS weighted average of log 10 ( _M_ H 2 / _M_ H I ).
The top left panel in Fig. 3 shows the _g_ -band Fornax Deep Survey
optical image (Iodice et al. 2016; Venhola et al. 2018; Peletier et al.
2020) of NGC 1436 where we overlay both the 11 [′′] MeerKAT H I
image contours (red and black contours are the same as in the top
right panel of Fig. 2) and the CO contours (white color) from Zabel
et al. (2021). Here, we can see that the CO follows the H I ring and


MNRAS **000**, 1–13 (2023)

4 _A. Loni et al._





-35°48'


50'


52'


54'







2.00


1.75


1.50


1.25


1.00


0.75


0.50





-35°50'


51'


52'





3 ~~[h]~~ 43 ~~[m]~~ 50 ~~[s]~~ 40 ~~[s]~~ 30 ~~[s]~~


RA (J2000)


1.3e+18 cm 2 1.3e+18 cm 2 4.5e+19 cm 2


-35°49'


50'


51'


52'


53'



40


35


30


25


20


15


10


5


0



|Col1|35s 30s 2000) 5.0 kpc 0.00 0.25|Col3|
|---|---|---|
||||
|0<br>5<br>10<br>Flux density [mJy]<br>MeerKAT 66'' - Flux|= 201 ± 020 J km s<br>1||
|0<br>5<br>10<br>Flux density [mJy]<br>MeerKAT 66'' - Flux|ot . . y<br>ot = 2.03 ± 0.21 Jy km s<br>1<br>ot = 1.70 ± 0.20 Jy km s<br>1|ot . . y<br>ot = 2.03 ± 0.21 Jy km s<br>1<br>ot = 1.70 ± 0.20 Jy km s<br>1|


1250 1300 1350 1400 1450 1500 1550


Velocity [Km s 1 ]







54'



3 ~~[h]~~ 43 ~~[m]~~ 48 ~~[s]~~ 42 ~~[s]~~ 36 ~~[s]~~ 30 ~~[s]~~ 24 ~~[s]~~


RA (J2000)



**Figure** **2.** The top panels show the MeerKAT H I image at a resolution of 66 [′′] (left) and 11 [′′] (right). In each panel the value on the top left gives the level of
the lowest H I contour (shown in red), which is calculated as the 3σ sensitivity over a 25 km s [−][1] line width. The H I contours increase by a factor of 2 at each
step. The PSF and a 5 kpc scale bar are shown on the bottom-left and bottom-right corner, respectively. The bottom left panel shows with green, red and purple
contours the ( _1_ ) 66 [′′] H I image ( _2_ ) lowest reliable contour of the 11 [′′] H I image ( _3_ ) 11 [′′] image convolved to a 66 [′′] resolution. With the same colors we show the 3σ
column density sensitivity of the respective H I image (top of the image) and their PSFs (bottom-left). The _g_ -band optical image comes from the Fornax Deep
Survey (Peletier et al. 2020). The bottom right panel shows spectra extracted from the 11 [′′] (red) and 66 [′′] (green) cubes, and from single-dish data (GBT, Courtois
et al. 2009 - black), respectively. The legend shows the total fluxes obtained from these data. The uncertainties on the total MeerKAT fluxes are calculated by
summing in quadrature the statistical uncertainties – derived from the local RMS and the number of independent pixels detected in each channel – and the 10%
MeerKAT flux uncertainty measured in Serra et al. (2023). The spectral axis shows velocity in the optical convention.



that there is no CO detected in the center of the galaxy. In the top
right panel of the figure we show the H I velocity field within the
lowest reliable H I contour, where we see that the H I disc is regularly
rotating with a slight PA warp at the edge of the disc. This is visible
as an anticlockwise rotation of the outer isovelocity contours. The
bottom panels show the position-velocity diagrams (PVDs) along
the kinematical major axis (left, PA = 330 [◦] ) and minor axis (right,
PA = 240 [◦] ) of both H I (background colour) and CO (contours). The
rotational velocity of H I and CO are consistent with one another
and follow the typical rotation of a settled disc. Judging from the
appearance of the velocity field and the H I PVD, we see that the
rotation curve is rising in the inner ∼half of the H I disc, and flattens
further out.


In the rest of this section we show results obtained by fitting the
H I kinematics of the high-resolution cube with the Tilted Ring Fit

MNRAS **000**, 1–13 (2023)



ting Code [1] (TiRiFiC - Józsa et al. 2012). TiRiFiC models the galaxy
in rings, where the model parameters are fitted to best reproduce
the H I geometry and kinematics in the data (further details in Józsa
et al. 2007). This allows us to measure the H I surface brightness
profile and to find the best-fitting values for geometric parameters
(e.g. inclination, PA) and for the rotation curve. We followed two
modelling approaches. In the former, we model our galaxy with a
flat disc (i.e., we forced TiRiFiC to fit a single value for PA and
inclination across all rings). In the latter, we forced TiRiFiC to fit a
flat rotation curve, but allowed the disc to warp letting the inclination vary. Between these two approaches, we obtained better results
modelling NGC 1436 with a flat disc. We further improve the output flat disc model by using an advanced feature of TiRiFiC, which


1 The software is available at the following link `[https://gigjozsa.](https://gigjozsa.github.io/tirific/index.html)`
```
github.io/tirific/index.html

```

_NGC 1436: the making of a lenticular galaxy in the Fornax cluster_ 5


1500





-35°50'00"


51'00"


52'00"


53'00"







-35°50'00"


51'00"


52'00"


53'00"



1450


1400


1350


1300


1250


1.0


0.8


0.6


0.4


0.2


0.0


0.2


0.4


0.6



3 ~~[h]~~ 43 ~~[m]~~ 45 ~~[s]~~ 40 ~~[s]~~ 35 ~~[s]~~ 30 ~~[s]~~


RA (J2000)



3 ~~[h]~~ 43 ~~[m]~~ 45 ~~[s]~~ 40 ~~[s]~~ 35 ~~[s]~~ 30 ~~[s]~~


RA (J2000)



1500


1450


1400


1350


1300


1250


|Col1|1.|
|---|---|
||0<br>0<br>0<br>0<br>0<br>1|
|||
|||



-0.01 0.00 0.01


Angular offset [deg]



1500


1450


1400


1350


1300


1250



-0.01 0.00 0.01


Angular offset [deg]



**Figure** **3.** Top-left: comparison between the H I and CO gas distribution from the MeerKAT (red and black contours as in the top-right panel of Fig. 2) and
ALMA (white contours) data, with corresponding beam sizes shown in the lower-left corner of this panel (in black and white, respectively). Bottom panels:
comparison of the PV-diagram of H I and CO along the major axis (green line on the top left panel) and minor axis. The background image shows the H I while
the green contours show the CO emission at 2.5σ, increasing in steps of 2. Cyan contours show the negative signal in the CO ALMA cube, whose absolute level
is the same as that of the first positive green contour.



allows us to fit and interpolate some model parameters in groups of
model rings rather than for each ring independently. Eventually, we
chose the model that better follows the distribution and kinematics

of the observed H I based on visual inspection. Appendix A includes
a visual comparison between the data and the TiRiFiC model.


Fig. 4 shows the H I rotation curve and the surface brightness (SB)
of NGC 1436 obtained through our TiRiFiC fitting. As anticipated,
the velocity increases with galactocentric distance in the inner regions, and it reaches a plateau at ∼50 [′′] . In the bottom panel, we
show the derived SB, which peaks at 45 [′′] . The best-fitting model
shows some low level fluctuations, which are unlikely to be real and
disappear when convolving the profile with the 11 [′′] beam (orange
line in Fig. 4). It is worth noting that, if we use our best model as
first guess and let PA and inclination vary, we obtain the same SB
and rotational velocity.


The H I disc diameter of NGC 1436, measured where the surface
brightness is 1 M ⊙ pc [−][2], is ∼110 [′′] (∼ 11 kpc). This allows us to verify
that NGC 1436 is 2.26σ above - and thus in agreement with - the H I



size - mass relation (Wang et al. 2016) similarly to the truncated H I
discs in the Virgo cluster.
In general, by studying the distribution and kinematics of both
H I and CO, we appreciate the high level of symmetry of the cold
gas in NGC 1436. Both H I and CO are distributed within a settled
ring where they are co-rotating, with no hints of any recent tidal or
hydrodynamical disturbances. Given that the orbital time at the disc’s
edge is of ∼300 Myr (as derived from the de-projected rotational
velocity of ∼130 km s [−][1] at a radius of ∼ 6.7 kpc) we can rule out
strong interactions in the last few orbital times, roughly 1 Gyr.


**4** **STAR FORMATION HISTORY**


The analysis on the cold gas disc establishes that previous interactions between the local environment and NGC 1436 left the galaxy
with a relaxed truncated H I disc and a clear demarcation between the

star-forming inner disc regions and passively-evolving outer ones. In
this section, we now aim at reconstructing the history of this morpho

MNRAS **000**, 1–13 (2023)

6 _A. Loni et al._


125


100


75


50


25


0


3


2


1





0



0 10 20 30 40 50 60 70
Radius [arcsec]



**Figure 4.** Results from tilted-ring analysis of the MeerKAT H I data, showing
the TiRiFiC H I rotation curve (top panel) and H I surface-brightness profile
(bottom panel). The latter shows clearly the abrupt transition towards the H I
deficient and quiescent outer disc beyond a radius of 55 [′′] .


logical transition by tracing the SFH imprinted in the inner and outer
stellar populations. For this we adopt a non-parametric approach
based on single-age stellar population models (SSP) and on the use
of the Penalised Pixel-Fitting [2] (pPXF; Cappellari & Emsellem 2004)
and the Gas and Absorption Line Fitting codes [3] (GandALF; Sarzi
et al. 2006; Falcón-Barroso et al. 2006) to fit the MUSE data. However, rather than aiming at a regularized SFH solution (Cappellari
2017) we decide to exploit the axisymmetry of the system to capture
the uncertainties of the SFH-reconstruction, as done earlier using
MUSE data by Martinsson et al. (2018).
More specifically, we derive the SFH for two sets of spectra extracted from sectors of elliptical annuli covering the star-forming and
quiescent disc, respectively, as shown in Fig. 5. Since the stellar populations within such annular sectors should be rather similar for the

inner and outer disc, respectively, beyond the short timescales (≲ 100
Myr) corresponding to the orbital times between adjacent sectors,
we use the variance between the SFHs recovered in such sectors to

estimate the uncertainty. In total we define 18 sectors in the inner
disc and 8 sectors in the outer disc, with average S/N per pixel of 100
and 20, respectively. Where necessary, foreground and background
sources were masked out before extracting these aperture spectra,
which we also corrected for foreground Galactic extinction using the
Calzetti dust extinction law (Calzetti et al. 2000) and a _AV_ 0.029
value in the direction of Fornax from Schlafly & Finkbeiner (2011).
To derive the SFH from each of these aperture spectra, we fit
them with pPXF and GandALF using SSP models from the MILES
library of Vazdekis et al. (2015) [4], which covers a range in age between
30 Myr and 14 Gyr, with total metallicity −2.27 ≤[M/H]≤ 0.4 dex,


2 `[https://www-astro.physics.ox.ac.uk/~mxc/software/](https://www-astro.physics.ox.ac.uk/~mxc/software/)`
3 `[https://star.herts.ac.uk/~sarzi/](https://star.herts.ac.uk/~sarzi/)`
4 The MILES stellar-population model library can be found at the following
link `[http://miles.iac.es/](http://miles.iac.es/)`


MNRAS **000**, 1–13 (2023)



5.0 kpc 4.5e+19 cm 2


-35°50'00"


51'00"


52'00"


3 ~~[h]~~ 43 ~~[m]~~ 44 ~~[s]~~ 40 ~~[s]~~ 36 ~~[s]~~ 32 ~~[s]~~


RA (J2000)


**Figure 5.** Comparison between the reconstructed MUSE image, MUSE Hα
emission and the MeerKAT H I data for NGC 1436 informing the location of
the MUSE aperture spectra used in our star-formation history analysis. As in
Fig. 1 the cyan and green ellipses indicated, respectively, the isophotal level
at 25 mag/arcsec [2] in B-band and the limit of the star-forming disc, where the
Hα emission is traced by the yellow contours. The extent of the gas reservoir
in NGC 1436 is traced here by the red contours for a limiting H I column
density of 4.5 × 10 [19] cm [−][2], which are best fitted by the shown red ellipse
setting the radius of the H I disc at _R_ HI 70 [′′] . Finally, the white dashed lines
show the location of the annular sectors used to extract the aperture spectra
in both the inner and outer disc for our SFH analysis, where the former avoid
the bulge regions (inside 9 [′′] ) and extend to the limit of the MUSE central
pointing whereas the latter start at the edge of the H I disc and reach out to the
25 mag/arcsec [2] B-band isophote.


and α-element overabundance [α/Fe] between 0 and 0.4 dex. Since
without a dedicated methodology (e.g. Martín-Navarro et al. 2019,
2021) we do not expect to be able to capture variations in the stellar
initial mass faction (IMF) through direct spectral fitting, here we
further restrict the fits to using models with a Kroupa IMF (Kroupa
2001).
As in Sarzi et al. (2018), we first fit the MUSE data with pPXF
to measure the stellar kinematics using only the bluer part of the
MUSE spectrum in the 4800 – 5850 Å spectral range. Subsequently,
we extend the GandALF fitting range out to 6850 Å to also include
the typically strong Hα, [N ii], and [S ii] emission and in turn better
constrain the overall contribution of the emission-line spectrum to our
models. During the pPXF fit we mask regions potentially affected
by emission and adopt an additive correction for the shape of the
continuum. Using a shorter wavelength range speeds up the pPXF
fitting process and delivers robust kinematic results owning to the
presence of several strong stellar absorption features at the bluer end
of the MUSE spectra. The GandALF fit is constrained to the pPXF
kinematics, but is allowed to change the optimal combination of SSP
templates in the stellar models in response to the additional use of
emission lines in the fit, which are represented by Gaussian functions.
In particular, we include both the Hβ and Hα recombination lines
and the [O iii]λλ4959, 5007, [N i]λλ5198, 5200, [O ii]λλ6300, 6363,

[N ii]λλ6548, 6583, [S ii]λλ6713, 6730 forbidden ones, tying all lines
to the same, optimally-adjusted line profile, while also accounting

_NGC 1436: the making of a lenticular galaxy in the Fornax cluster_ 7



Spectrum GandALF best fit Emission-line best fit


40000


20000


0


0.25 Residual


0.00


1.025


1.000


0.975


4750 5000 5250 5500 5750 6000 6250 6500 6750
[Å]



0

0.05 Residual


0.00


1.10


1.05


4750 5000 5250 5500 5750 6000 6250 6500 6750
[Å]



Spectrum GandALF best fit Emission-line best fit



100000


50000



**Figure 6.** Examples of GandALF (orange) to the MUSE spectra (blue) extracted in the outer (left) and inner disc (right). The green line shows the emission line
best fit. The middle panel shows the residuals of the fit. The gap within the residuals indicates that we excluded that wavelength range from the GandALF fit.
The vertical dashed red lines show the emission lines we fitted. In both cases shown, we used a 7-th order polynomial, whose shapes are shown in the bottom
panels, respectively.



Single sector Mean



Single sector Mean



10 [0]


10 1


10 2


10 3


10 4


10 5



10 [0]


10 1


10 2


10 3


10 4


10 5



10 6

0 2 4 6 8 10 12 14
Lookback time (Gyr)



10 6

0 2 4 6 8 10 12 14
Lookback time (Gyr)



**Figure 7.** Sample normalised SFH of the quiescent (left) and the star-forming disc (right) of NGC 1436 obtained combining the results from the 8 and 18 sectors
shown in Fig. 5 and while useing a 7-th order multiplicative polynomial correction for the continuum shape as illustrated in the examples of Fig. 6. In both
panels the black dots represent the average fractional stellar mass formed within each age bin in each of our disc sectors, whereas the larger filled circles and
shaded regions indicate the overall averages and standard deviations for the fractional SFRs, calculated including also zero fractional SFR values from individual
sectors. The empty circles and gray bands highlight the unreliable measurements of the fractional SFR at younger ages (see text).



for the varying spectral resolution of the MUSE spectra (e.g., Guérou
et al. 2016).

Ideally, the GandALF fit would include a two-component reddening correction: the first affecting the whole spectrum to mimic diffuse
dust; and the second affecting the emission line spectrum only, representing dust localised in emission line regions and matching the
observed Balmer decrement (e.g., Oh et al. 2011). However, the quality of the relative flux calibration of the MUSE data is insufficient to
grant such an approach, and we resort to using a multiplicative polynomial correction instead. This still allows us to obtain very good
fits to our aperture spectra, but the use of multiplicative polynomials
effectively introduces a nuisance parameter in our analysis as polynomial correction of varying order will lead to fits of very similar
quality beyond a certain minimum order. Furthermore, not being able
to account for dust reddening limits our control over unrealistic values for the Balmer decrement and spurious Hβ line detections, which
in turn can affect the stellar-template optimal combination process



and lead to biased SFH results. For these reasons we decide to omit

the Hβ line from our GandALF fits for the outer quiescent disc,
where Hα emission from diffuse ionised gas is only barely detected.
Finally, we note that in the fits we further ignore the wavelength region around the NaDλλ5896, 5890, as often this part of the spectrum
presents strong continuum shape issues related to the relative flux
calibration.


Figure 6 shows examples of aperture spectra extracted in the outer
quiescent disc (left) and in the inner star-forming disc (right) of
NGC 1436, along with our best GandALF fit to them. Residuals
from the sky emission-line subtraction process are evident in the
outer-disc aperture spectra but do not affect the overall quality of our
fit nor our SFH results, in particular as these artifacts do not interest
the more age- and metallicity-sensitive absorption-line features in
our fitting range. The fits in Fig. 6 include a 7-th order multiplicative
polynomial adjustment that is more substantial in the case of the


MNRAS **000**, 1–13 (2023)

8 _A. Loni et al._





10 [0]


10 1


10 2


10 3


10 4


10 5


10 6





10 [0]


10 1


10 2


10 3


10 4


10 5


10 6



10 7

|Single run Mean SFR(H ) up|Col2|
|---|---|
||Mtot = 1.6× 109M|
|||


0 2 4 6 8 10 12 14
Lookback time (Gyr)



10 7

|Singlerun Mean SFR(H )|Col2|Col3|
|---|---|---|
||Mtot = 1.1× 1010M|Mtot = 1.1× 1010M|
||Mtot = 1.1× 1010M||
||Mtot = 1.1× 1010M||
||||


|Col1|Col2|
|---|---|
|||


0 2 4 6 8 10 12 14
Lookback time (Gyr)



**Figure 8.** Final normalised SFH for the quiescent (left) and the star-forming disc (right) obtained by combining the GandALF results of 20 different fit runs that
_(i)_ varied the order of the multiplicative polynomial correction between 6 and 15 and _(ii)_ considered either the entire MILES SSP library or only SSP models
older than 1 Gyr. In both panels the black dots represent the average fractional SFR obtained from the individual fit runs (the same as the large filled circles in the
example shown Fig. 7. The larger filled circles and shaded regions represent the average and standard deviation of the average fractional SFR of the single runs,
including those equal to 0. For the earliest age bin, where our SFH reconstruction is unreliable (open circles and shaded grey band), we uses the MUSE Hα maps
to measure or place an upper limit on the present-day star-formation rate across our inner or outer disc sectors, respectively, converting these in estimate (blue
cross, right panel) or upper-limits (red downward arrow, left panel) on the fractional SFR of the first 1 Gyr by assuming such an activity remained constant over
this period of time. On the top right of each panel we report the total M ⋆ subtended by our 8 outer and 18 inner disc sectors, which cover an area of 12.5 kpc [2]

and 18 kpc [2], respectively.



central star-forming regions, where such a correction is also needed
to mimic the impact of reddening by dust.

During the fitting process, GandALF finds the best combination of
our adopted stellar population templates returning a corresponding
list of best-fitting weights. Since each MILES model corresponds to
a stellar population with an initial mass of one solar mass, accounting
for the distance to the object allows us to turn each of these weights
into a stellar mass formed at the look back time corresponding to
the age of the _i_ -th SSP model. Given that only a few SSP templates
receive a non-zero weight during the GandALF fit, to estimate the
SFH in each sector _s_ we bin the resulting initial stellar-mass values
bins beyond that. Dividing the total stellar mass _M_ _i_ [SSP], _s_ in 1-Gyr-wide age bins between 0 and 6 Gyr and in 2-Gyr-wide _M_ _s_ ( _t_ _j_ ) formed in the
_j_ -th time bin by the corresponding time bin width ∆ _t_ _j_, we obtain the
average star-formation rate (SFR) in that bin _SFR_ _s_ ( _t_ _j_ ) = _M_ _s_ ( _t_ _j_ )/∆ _t_ _j_ .
This effectively gives us a SFR history for each sector, which we
divide by the total stellar mass formed over time, _M_ _s_ =Σ _j_ _M_ _s_ ( _t_ _j_ ) to
derive the fractional stellar mass formed per unit time in each sector.

This normalised SFH varies strongly from sector to sector in both
the inner disc and the outer disc. This variation largely reflects the
uncertainties in our template-optimisation process. To estimate these
uncertainties and obtain a more reliable average trend we calculate
the average and standard deviation of the normalised star formation
histories across all sectors assigning _S FR_ _s_ ( _t_ _j_ ) = 0 to sectors and age
bins with no non-zero weights. Fig. 7 shows the normalised SFHs
for the inner and outer disc obtained after this averaging, using a 7-th
order multiplicative correction as in Fig. 6. The average values and
corresponding uncertainties on the normalised star-formation history
(coloured large circles and shaded regions, respectively) already indicate that both central and outer regions went through a recent peak
of star-formation some 4 Gyrs ago. event was much more pronounced
in the inner disc (by a factor 4-5) and more rapidly quenched in the
outer disc.


MNRAS **000**, 1–13 (2023)



However, we note that in the quiescent outer disc our GandALF
fit seems to require a small contribution from very young SSPs. The
presence of such young stars is at odds with the notable absence
of any star-formation activity and it is certainly a bias in the template mix adjustment process, which in turn may stem from intrinsic
limitations in our ability to constrain the presence of young stellar
populations using the MUSE spectra, as indeed these do not extend
down to important features (e.g. the D4000 break and Hδ). For this
reason we decided to repeat our analysis while also removing all SSP
templates younger than 1 Gyr and include this second set of fits in the
overall averaging and variance estimation process for the normalised
SFHs. We highlight that the actual choice of polynomial order is also
quite arbitrary, as the quality of the fit does not change significantly
while varying the polynomial order between 6 and 15. Treating this
as an additional source of uncertainty we thus repeat our fits varying
the polynomial order within the above limits, including the corresponding results in the derivation of the final normalised SFH and
associated uncertainties for the inner and outer disc.


Fig. 8 shows the final normalised SFH in the outer quiescent disc
(left) and inner star-forming disc (right) obtained combining the
normalised SFHs from their corresponding apertures, considering
20 different fits (10 polynomial orders, and including or excluding
SSP templates younger than 1 Gyr). The clearer trends of Fig. 8
confirm the picture drawn from our simpler analysis shown in Fig. 7,
according to which NGC 1436 experienced a burst of star formation
between 3 to 4 Gyr ago that saw the birth of ∼50% and ∼20% of all
the stars that ever formed in the inner and outer disc, respectively.
Such an activity faded considerably in the past 3 Gyr, and most
dramatically in the outer disc where the absence of any present starformation activity (from the Hα data) is consistent with the lack of star
formation between 1 and 2 Gyr in our reconstructed SFH. Clearly,
our ability to assess the rate of recent decline in star formation in
NGC 1436 is limited by the aforementioned biases in recovering the

_NGC 1436: the making of a lenticular galaxy in the Fornax cluster_ 9



4.0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0



SubID: 220600


0 1 2 3 4
Lookback Time [Gyr]



800


700


600


500


400


300


200


100


0


|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||



6 4 2 0 2 4 6
x [kpc]



6


4


2


0


2


4


6



0.75


1.00


1.25


1.50


1.75


2.00


2.25


2.50



**Figure** **9.** The left panel shows an example from the TNG50 simulation run (Pillepich et al. 2019) of a disk galaxy that recently fell in a Fornax-like cluster
environment in this simulation (Galán-de Anta et al. 2022) identified through the SUBFIND algorithm (Springel et al. 2001). As inferred from our SFH analysis
for NGC 1436, this simulated object experienced a burst of star formation upon its first pericentre passage, followed by a steady drop in star-formation activity.
The purple line traces the radial distance from the cluster center as a function of time, whereas the dot-dashed blue line follows the evolution of star-formation
activity. The horizontal dashed purple line indicate the virial radius of this particular Fornax-like TNG50 cluster. The right panel shows the SFR map of the
target TNG50 disc galaxy at _z_ =0. Black contours show the surface mass density which highlight that, similarly to NGC 1436, the star formation is occurring just
within the inner part of the disc.



SFH in the last 1 Gyr. As a sanity check, in the inner disc we can at
least provide an estimate for the fractional stellar mass formed in the
last Gyr assuming that stars formed at their present-day level over this
period of time. Using the MUSE Hα maps of Iodice et al. (2019a)
and restricting our analysis to emission-line regions firmly classified
as H ii regions we obtained the total star-formation rate in the regions
subtended by our inner-disc sectors, using the Calzetti et al. (2012)
conversion SFR(M ⊙ /yr) = 5.5×10 [−][42] L Hα ergs and taking a distance
of 20 Mpc. The estimate derived in this way (blue cross in Fig. 8) is
consistent with the upper edge for the fractional stellar mass formed
in the last 1 Gyr. Similarly, from the Hα map of the outer disc,
we measure a 3σ SFR upper limit (red downward arrow) using the 8
sectors of the outer disc. Finally, the reconstructed SFH of NGC 1436
shows that before the onset of its recent starburst, some 4 to 5 Gyrs
ago, this disc galaxy was evolving according to the cosmological
picture with its star-formation activity having already peaked at a
redshift between 1 and 2, or some 8 to 10 Gyrs ago (López Fernández
et al. 2018). In fact, the steeper decline in star-formation activity in the
inner regions at these earlier times, is consistent with the commonly
observed inside-out evolution of disc galaxies (e.g., Kepner 1999;
Nelson et al. 2016; Johnston et al. 2022). In summary, our SFH
analysis indicates that both the inner and outer disc populations went
through three main star-formation phases: _(i)_ a rather typical build
up activity and a steady decline in star-formation activity until some
5 Gyr ago, _(ii)_ a burst of star formation peaking between 3 and 4
Gyr ago, and _(iii)_ a final drop in star-formation until present times,
gradually reducing it by two orders of magnitude in the inner disc
and completely quenching star formation in the outer disc.


**5** **DISCUSSION**


Several properties of the multi-phase gas disc indicate that NGC 1436
has not experienced any significant tidal or hydrodynamical interac


tion in recent times: ( _i_ ) the highly symmetric morphology and settled
kinematics of the H I disc observed with MeerKAT at a resolution
of ∼ 10 [′′] ∼ 1 kpc; ( _ii_ ) the absence of H I disturbances, asymmetries or tails down to a column density of ∼ 10 [18] cm [−][2] (resolution
∼ 60 [′′] ∼ 6 kpc); _(iii)_ the perfect match between the regular morphology and kinematics of the various gas phases (atomic, molecular and
ionised). The fact that the disc is settled now, does not imply that
NGC 1436 has never experienced environmental interactions in the
past. For example, in the Virgo cluster, some of the most gas-poor
galaxies which went through ram-pressure stripping are symmetric
systems with a severely truncated H I disc (Yoon et al. 2017). That is,
after a few orbital periods any sign of interactions would disappear.
Given the orbital time of NGC 1436 (300 Myr at the edge of the H I
disc - Sect. 3), NGC 1436 has not undergone any significant environmental interaction in the last few orbits, say ∼ 1 Gyr. Thus we
wonder "whether", "when" and "how" interactions with the Fornax
cluster environment were relevant for the history of NGC 1436.


Useful insights come from our reconstructed SFH for the inner and
outer disc of this galaxy. The SFH of the quiescent and star-forming
disc of Fig. 8 indeed suggests that NGC 1436 was not a member
of the cluster earlier than ∼6 Gyr ago, with the Fornax environment
becoming relevant for its evolution starting around 5 Gyr ago. Indeed,
between 14 and 5 Gyr NGC 1436 seem to have followed the expected
cosmic evolution for star-formation activity (López Fernández et al.
2018) while also following a typical inside-out evolution. That is,
up to ∼ 5 Gyr ago NGC 1436 seems to have formed its stars as a
regular spiral in a low-density environment, without being affected
by strong tidal or hydrodynamical interactions. Since entering the
cluster it must have taken ∼ 1 Gyr for NGC 1436 to reach its first
pericentre passage (τ cross is indeed about 2 Gyr for Fornax where
_R_ vir = 700 kpc and σ cl = 318 km s [−][1], Drinkwater et al. 2001) when
interactions between the galaxy and the Fornax environment would
have been more extreme.


MNRAS **000**, 1–13 (2023)

10 _A. Loni et al._


Drawing from the inferred rise and decline of star formation activity, we thus speculate that ∼ 4 Gyr ago, at about pericentre, a
tidal interaction and/or ram-pressure was able to compress and then
remove the majority of the H I content from the galaxy outer disc,
causing a temporary SFR enhancement followed by a rapid quenching of its star formation. NGC 1436 could only keep some H I within
the inner star forming disc thanks to the stronger gravitational binding. However, by the time gas removal from the outer disc was complete, the accretion of cold gas onto the galaxy must have completely
stopped. Therefore, the subsequent evolution (with NGC 1436 now
moving away from pericentre) must have been characterised by a
fully quenched outer disc and a starving inner disc. This would explain why the SFR of the inner disc has decreased in the last few
Gyr, but not gone to zero. The lookback time of the environmental
interactions, which caused the enhancement of the SFR, is consistent
with the conclusion of Iodice et al. (2019a) that NGC 1436 is an

intermediate infaller in Fornax.

The relative role that gravitational and hydrodynamical processes
might have played to drive such a morphological transformation is
not clear. In the literature there is evidence that both tidal interactions

and ram pressure might separately trigger a temporary enhancement
in star-formation activity and the removal of cold gas (Toomre &
Toomre 1972; Barnes 2004; Li et al. 2008; Poggianti et al. 2017;
Vulcani et al. 2018; Ramatsoku et al. 2019; Molnár et al. 2022). Alternatively, a combination of both gravitational (possibly a merger)
and hydrodynamical interactions might have been at work in the
specific case of NGC 1436. For example, NGC 1436 might have
experienced tidal interaction near pericentre, which may have triggered a central SFR enhancement while, at the same time, moving
some gas to large radius via tidal forces, from where it could more
easily be stripped by ram pressure. In this case, NGC 1436 would
share a similar evolutionary path to that of the Fornax galaxies with
one-sided HI tails described in Serra et al. (2023).
Interestingly, the recent evolution of NGC 1436 can also be observed in cosmological simulations. For instance, looking at the
TNG50 simulation (Pillepich et al. 2019), among the 16 presentday disc galaxy found in Fornax-like environments (Galán-de Anta
et al. 2022) we find six currently star-forming objects that entered
their cluster environment between 3 and 5 Gyrs ago and had only
one pericentre passage. Among these, the left panel of Fig 9 shows
the SFH of the simulated galaxy that matched more closely the one
inferred from our SFH analysis. The right panel of this figure shows
that the disc of this simulated object also appears to be forming stars
only in its inner part while its outskirts have already been quenched,
as for NGC 1436.


**6** **SUMMARY**


Using H I cubes from the MeerKAT Fornax Survey (Serra
et al. 2023), with a resolution of 11 [′′] and 66 [′′], sensitivity
_N_ HI (3σ, 25 kms [−][1] ) = 4.5×10 [19] cm [−][2] and 1.3×10 [18] cm [−][2], respectively, and a spectral resolution of ∼1.4 km s [−][1], we have investigated
the distribution and kinematics of the H I in NGC 1436 finding that: _(i)_
the H I distribution is truncated within the inner and still star-forming
disc _(ii)_ the H I kinematics is consistent with that of CO (Zabel et al.
2019) and ionized gas (Iodice et al. 2019a), and thus NGC 1436
has not experience any recent environmental interactions in the last

∼
1 Gyr (a few orbital times of the interstellar medium).
With Fornax 3D data (Sarzi et al. 2018), we further reconstructed
the SFHs of the outer (currently quiescent) and inner (still starforming) part of the disc of NGC 1436, which show ( _i_ ) a faster


MNRAS **000**, 1–13 (2023)



evolution of the inner disc with respect to the outer disc from 14 to
5 Gyr ago ( _ii_ ) a burst of star formation ∼ 4 ago in both parts of the
disc ( _iii_ ) a steady decline and a fast quenching of the star formation
activity in the inner and outer disc, respectively.
These findings suggest that before the star formation burst,
NGC 1436 was evolving in a low-density environment outside the
Fornax cluster. While falling into the cluster and approaching its
pericentre, environmental interactions have promoted a temporary
enhancement in SFR. These interactions were also able to remove

H I from the outskirts of the galaxy, which caused the fast quenching
of the outer disc. The lack of subsequent cold gas accretion onto the
inner disc is causing its current slow quenching.
Similar evolutionary paths have been observed in cosmological
simulations (Pillepich et al. 2019) in disc galaxies evolving in Fornaxlike clusters (Galán-de Anta et al. 2022).


**7** **FUTURE PLAN**


This work demonstrates how mapping the star-formation history in
galaxies with deep H I data is effective for understanding both the past
and on-going impact of gravitational and hydrodynamic processes
on galaxies moving from low to high density environments.
As a next step, we will apply the stellar-population analysis approach used for NGC 1436 to the other galaxies in the Fornax cluster
with available VLT-MUSE data and detected with MeerKAT. Mainly
coming from Fornax3D sample (Sarzi et al. 2018), they will result in
a sample of 13 galaxies covering a range of HI morphologies, galaxy
mass, and position within the cluster that will provide an ideal basis
for further comparisons with the predictions from numerical simulations. At the same time, we intend to improve our constraints on the
young stellar population by taking also into account data extending
beyond the MUSE spectral range. For instance, we intend to collect
near-IR data using the NIRWALS integral-field spectrograph (Wolf
et al. 2018) mounted on the South African Large Telescope (SALT),
which will cover absorption bands from thermally-pulsating asymptotic giant branch stars that are good indicators of intermediate age
populations (between 0.3 and 2 Gyr, Maraston 2005).


**ACKNOWLEDGEMENTS**


This project has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and
innovation programme (grant agreement no. 679627; project name
FORNAX). The MeerKAT telescope is operated by the South African
Radio Astronomy Observatory, which is a facility of the National
Research Foundation, an agency of the Department of Science and
Innovation. We acknowledge the use of the Ilifu cloud computing
facility - www.ilifu.ac.za, a partnership between the University of
Cape Town, the University of the Western Cape, the University of
Stellenbosch, Sol Plaatje University, the Cape Peninsula University
of Technology and the South African Radio Astronomy Observatory. The Ilifu facility is supported by contributions from the InterUniversity Institute for Data Intensive Astronomy (IDIA - a partnership between the University of Cape Town, the University of Pretoria
and the University of the Western Cape), the Computational Biology division at UCT and the Data Intensive Research Initiative of
South Africa (DIRISA). This project and both AL and MS have received support from the Science and Technologies Facilities Council
(STFC) through their New Apllicant grant ST/T000503/1. FL acknowledges financial support from the Italian Minister for Research

_NGC 1436: the making of a lenticular galaxy in the Fornax cluster_ 11



and Education (MIUR), project FARE, project code R16PR59747,

−
project name FORNAX B. FL acknowledges financial support from
the Italian Ministry of University and Research – Project Proposal
CIR01_00010. J. F-B acknowledges support through the RAVET
project by the grant PID2019-107427GB-C32 from the Spanish Ministry of Science, Innovation and Universities (MCIU), and through
the IAC project TRACES which is partially supported through the
state budget and the regional budget of the Consejería de Economía,
Industria, Comercio y Conocimiento of the Canary Islands Autonomous Community. EMC acknowledges support by Padua University grants DOR 2020–2022 and by Italian Ministry for Education
University and Research (MIUR) grant PRIN 2017 20173ML3WW001. AP is supported by the Science and Technology Facilities Council through the Durham Astronomy Consolidated Grant 2020–2023
(ST/T000244/1). This project has received funding from the European Research Council (ERC) under the European Union’s Horizon
2020 research and innovation program grant agreement No. 882793,
project name MeerGas. NZ is supported by the South African Research Chairs Initiative of the Department of Science and Technology and National Research Foundation. At RUB, this research is
supported by the BMBF project 05A20PC4 for D-MeerKAT.


**DATA AVAILABILITY**


The data underlying this article from: _(i)_ the MeerKAT Fornax Survey
are available at the following link `[https://sites.google.com/](https://sites.google.com/inaf.it/meerkatfornaxsurvey/data)`
`[inaf.it/meerkatfornaxsurvey/data](https://sites.google.com/inaf.it/meerkatfornaxsurvey/data)`, _(ii)_ the Fornax3D survey
are available in the ESO archive (program ID: 296.B-5054 - see
also [new-data-release-of-muse-data-cubes-of-the-fornax3d-survey),](http://archive.eso.org/cms/eso-archive-news/new-data-release-of-muse-data-cubes-of-the-fornax3d-survey.html)
_(iii)_ the ALMA Fornax Cluster Survey and the Deep CO(J=1-0) mapping survey of Fornax galaxies with Morita array are available in the
ALMA archive (project code 2015.1.00497.S and 2017.1.00129.S,
respectively).


**REFERENCES**


[Abadi M. G., Moore B., Bower R. G., 1999, MNRAS, 308, 947](http://dx.doi.org/10.1046/j.1365-8711.1999.02715.x)
Arp H., 1966, Atlas of peculiar galaxies
Bacon R., et al., 2010, in McLean I. S., Ramsay S. K., Takami H., eds, Society
of Photo-Optical Instrumentation Engineers (SPIE) Conference Series
Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy
III. p. 773508 ( `[arXiv:2211.16795](http://arxiv.org/abs/2211.16795)` [), doi:10.1117/12.856027](http://dx.doi.org/10.1117/12.856027)
[Barnes J. E., 2004, MNRAS, 350, 798](http://dx.doi.org/10.1111/j.1365-2966.2004.07725.x)
[Bell E. F., de Jong R. S., 2000, MNRAS, 312, 497](http://dx.doi.org/10.1046/j.1365-8711.2000.03138.x)
[Blakeslee J. P., et al., 2009, ApJ, 694, 556](http://dx.doi.org/10.1088/0004-637X/694/1/556)
[Boselli A., Gavazzi G., 2006, PASP, 118, 517](http://dx.doi.org/10.1086/500691)

Boselli A., Boissier S., Cortese L., Gil de Paz A., Seibert M., Madore B. F.,
[Buat V., Martin D. C., 2006, ApJ, 651, 811](http://dx.doi.org/10.1086/507766)
[Boselli A., Cortese L., Boquien M., 2014a, A&A, 564, A65](http://dx.doi.org/10.1051/0004-6361/201322311)
Boselli A., Cortese L., Boquien M., Boissier S., Catinella B., Lagos C.,
[Saintonge A., 2014b, A&A, 564, A66](http://dx.doi.org/10.1051/0004-6361/201322312)
Calzetti D., Armus L., Bohlin R. C., Kinney A. L., Koornneef J., Storchi[Bergmann T., 2000, ApJ, 533, 682](http://dx.doi.org/10.1086/308692)
[Calzetti D., Liu G., Koda J., 2012, ApJ, 752, 98](http://dx.doi.org/10.1088/0004-637X/752/2/98)
[Cappellari M., 2017, MNRAS, 466, 798](http://dx.doi.org/10.1093/mnras/stw3020)
[Cappellari M., Emsellem E., 2004, PASP, 116, 138](http://dx.doi.org/10.1086/381875)
[Catinella B., et al., 2018, MNRAS, 476, 875](http://dx.doi.org/10.1093/mnras/sty089)

Cortese L., Catinella B., Smith R., 2021, Publ. Astron. Soc. Australia, [38,](https://ui.adsabs.harvard.edu/abs/2021PASA...38...35C)

[e035](https://ui.adsabs.harvard.edu/abs/2021PASA...38...35C)

Courtois H. M., Tully R. B., Fisher J. R., Bonhomme N., Zavodny M., Barnes
[A., 2009, AJ, 138, 1938](http://dx.doi.org/10.1088/0004-6256/138/6/1938)
[Dressler A., 1980, ApJ, 236, 351](http://dx.doi.org/10.1086/157753)
[Dressler A., et al., 1997, ApJ, 490, 577](http://dx.doi.org/10.1086/304890)



[Drinkwater M. J., Gregg M. D., Colless M., 2001, ApJ, 548, L139](http://dx.doi.org/10.1086/319113)
[Falcón-Barroso J., et al., 2006, MNRAS, 369, 529](http://dx.doi.org/10.1111/j.1365-2966.2006.10261.x)
Fasano G., Poggianti B. M., Couch W. J., Bettoni D., Kjærgaard P., Moles
[M., 2000, ApJ, 542, 673](http://dx.doi.org/10.1086/317047)
[Galán-de Anta P. M., et al., 2022, MNRAS, 517, 5992](http://dx.doi.org/10.1093/mnras/stac3061)
Guérou A., Emsellem E., Krajnović D., McDermid R. M., Contini T., Weil[bacher P. M., 2016, A&A, 591, A143](http://dx.doi.org/10.1051/0004-6361/20162874310.48550/arXiv.1605.07667)
[Gunn J. E., Gott J. Richard I., 1972, ApJ, 176, 1](http://dx.doi.org/10.1086/151605)
Hubble E. P., 1936, Realm of the Nebulae
[Iodice E., et al., 2016, ApJ, 820, 42](http://dx.doi.org/10.3847/0004-637X/820/1/42)
[Iodice E., et al., 2019a, A&A, 627, A136](http://dx.doi.org/10.1051/0004-6361/201935721)

[Iodice E., et al., 2019b, A&A, 627, A136](http://dx.doi.org/10.1051/0004-6361/201935721)
Jensen J. B., Tonry J. L., Thompson R. I., Ajhar E. A., Lauer T. R., Rieke
[M. J., Postman M., Liu M. C., 2001, ApJ, 550, 503](http://dx.doi.org/10.1086/319819)
[Johnston E. J., et al., 2022, MNRAS, 514, 6141](http://dx.doi.org/10.1093/mnras/stac1447)

[Józsa G. I. G., Kenn F., Klein U., Oosterloo T. A., 2007, A&A, 468, 731](http://dx.doi.org/10.1051/0004-6361:20066164)
Józsa G. I. G., Kenn F., Oosterloo T. A., Klein U., 2012, TiRiFiC: Tilted Ring
Fitting Code (ascl:1208.008)
[Kepner J. V., 1999, ApJ, 520, 59](http://dx.doi.org/10.1086/307419)
Kreckel K., Platen E., Aragón-Calvo M. A., van Gorkom J. H., van de Wey[gaert R., van der Hulst J. M., Beygu B., 2012, AJ, 144, 16](http://dx.doi.org/10.1088/0004-6256/144/1/16)
[Kroupa P., 2001, MNRAS, 322, 231](http://dx.doi.org/10.1046/j.1365-8711.2001.04022.x)
[Larson R. B., Tinsley B. M., Caldwell C. N., 1980, ApJ, 237, 692](http://dx.doi.org/10.1086/157917)
Li C., Kauffmann G., Heckman T. M., Jing Y. P., White S. D. M., 2008,

[MNRAS, 385, 1903](http://dx.doi.org/10.1111/j.1365-2966.2008.13000.x)

[Loni A., et al., 2021, A&A, 648, A31](http://dx.doi.org/10.1051/0004-6361/202039803)
[López Fernández R., et al., 2018, A&A, 615, A27](http://dx.doi.org/10.1051/0004-6361/201732358)
Maddox N., Serra P., Venhola A., Peletier R., Loubser I., Iodice E., 2019,


[MNRAS, 490, 1666](http://dx.doi.org/10.1093/mnras/stz2530)

[Maraston C., 2005, MNRAS, 362, 799](http://dx.doi.org/10.1111/j.1365-2966.2005.09270.x)

[Martín-Navarro I., et al., 2019, A&A, 626, A124](http://dx.doi.org/10.1051/0004-6361/201935360)

[Martín-Navarro I., et al., 2021, A&A, 654, A59](http://dx.doi.org/10.1051/0004-6361/202141348)
Martinsson T. P. K., Sarzi M., Knapen J. H., Coccato L., Falcón-Barroso J.,
[Elmegreen B. G., de Zeeuw T., 2018, A&A, 612, A66](http://dx.doi.org/10.1051/0004-6361/201730955)
[Merritt D., 1983, ApJ, 264, 24](http://dx.doi.org/10.1086/160571)
Meyer M., Robotham A., Obreschkow D., Westmeier T., Duffy A. R.,
[Staveley-Smith L., 2017, Publ. Astron. Soc. Australia, 34, 52](http://dx.doi.org/10.1017/pasa.2017.31)
[Molnár D. C., et al., 2022, A&A, 659, A94](http://dx.doi.org/10.1051/0004-6361/202142614)

[Moore B., Katz N., Lake G., Dressler A., Oemler A., 1996, Nature, 379, 613](http://dx.doi.org/10.1038/379613a0)
[Morokuma-Matsui K., et al., 2022, ApJS, 263, 40](http://dx.doi.org/10.3847/1538-4365/ac983b)
[Nelson E. J., et al., 2016, ApJ, 828, 27](http://dx.doi.org/10.3847/0004-637X/828/1/27)
[Oh K., Sarzi M., Schawinski K., Yi S. K., 2011, ApJS, 195, 13](http://dx.doi.org/10.1088/0067-0049/195/2/1310.48550/arXiv.1106.1896)
[Peletier R., et al., 2020, arXiv e-prints, p. arXiv:2008.12633](https://ui.adsabs.harvard.edu/abs/2020arXiv200812633P)
[Pillepich A., et al., 2019, MNRAS, 490, 3196](http://dx.doi.org/10.1093/mnras/stz2338)
[Poggianti B. M., et al., 2017, ApJ, 844, 48](http://dx.doi.org/10.3847/1538-4357/aa78ed)
[Postman M., et al., 2005, ApJ, 623, 721](http://dx.doi.org/10.1086/428881)
[Quilis V., Moore B., Bower R., 2000, Science, 288, 1617](http://dx.doi.org/10.1126/science.288.5471.1617)
[Raj M. A., et al., 2019, A&A, 628, A4](http://dx.doi.org/10.1051/0004-6361/201935433)
[Ramatsoku M., et al., 2019, MNRAS, 487, 4580](http://dx.doi.org/10.1093/mnras/stz1609)

[Sarzi M., et al., 2006, MNRAS, 366, 1151](http://dx.doi.org/10.1111/j.1365-2966.2005.09839.x)

[Sarzi M., et al., 2018, A&A, 616, A121](http://dx.doi.org/10.1051/0004-6361/201833137)
[Schlafly E. F., Finkbeiner D. P., 2011, ApJ, 737, 103](http://dx.doi.org/10.1088/0004-637X/737/2/103)
[Serra P., et al., 2023, arXiv e-prints, p. arXiv:2302.11895](http://dx.doi.org/10.48550/arXiv.2302.11895)
[Spriggs T. W., et al., 2021, A&A, 653, A167](http://dx.doi.org/10.1051/0004-6361/202141314)
[Springel V., White S. D. M., Tormen G., Kauffmann G., 2001, MNRAS, 328,](http://dx.doi.org/10.1046/j.1365-8711.2001.04912.x)
[726](https://ui.adsabs.harvard.edu/abs/2001MNRAS.328..726S)

[Struck C., Smith B. J., 2012, MNRAS, 422, 2444](http://dx.doi.org/10.1111/j.1365-2966.2012.20798.x)
Tonry J. L., Dressler A., Blakeslee J. P., Ajhar E. A., Fletcher A. B., Luppino
[G. A., Metzger M. R., Moore C. B., 2001, ApJ, 546, 681](http://dx.doi.org/10.1086/318301)
[Toomre A., Toomre J., 1972, ApJ, 178, 623](http://dx.doi.org/10.1086/151823)
[Vazdekis A., et al., 2015, MNRAS, 449, 1177](http://dx.doi.org/10.1093/mnras/stv151)

[Venhola A., et al., 2018, A&A, 620, A165](http://dx.doi.org/10.1051/0004-6361/201833933)
[Vulcani B., et al., 2018, ApJ, 866, L25](http://dx.doi.org/10.3847/2041-8213/aae68b)
Wang J., Koribalski B. S., Serra P., van der Hulst T., Roychowdhury S.,
[Kamphuis P., Chengalur J. N., 2016, MNRAS, 460, 2143](http://dx.doi.org/10.1093/mnras/stw1099)
Weilbacher P. M., Streicher O., Urrutia T., Jarno A., Pécontal-Rousset A.,
Bacon R., Böhm P., 2012, in Radziwill N. M., Chiozzi G., eds, Society of
Photo-Optical Instrumentation Engineers (SPIE) Conference Series Vol.


MNRAS **000**, 1–13 (2023)

12 _A. Loni et al._


8451, Software and Cyberinfrastructure for Astronomy II. p. 84510B,
[doi:10.1117/12.925114](http://dx.doi.org/10.1117/12.925114)

Weilbacher P. M., Streicher O., Palsa R., 2016, MUSE-DRP: MUSE Data
Reduction Pipeline (ascl:1610.004)
Wolf M. J., et al., 2018, in Evans C. J., Simard L., Takami H., eds, Society of
Photo-Optical Instrumentation Engineers (SPIE) Conference Series Vol.
10702, Ground-based and Airborne Instrumentation for Astronomy VII.
[p. 107022O, doi:10.1117/12.2312792](http://dx.doi.org/10.1117/12.2312792)
[Yoon H., Chung A., Smith R., Jaffé Y. L., 2017, ApJ, 838, 81](http://dx.doi.org/10.3847/1538-4357/aa6579)
[Zabel N., et al., 2019, MNRAS, 483, 2251](http://dx.doi.org/10.1093/mnras/sty3234)

[Zabel N., et al., 2021, MNRAS, 502, 4723](http://dx.doi.org/10.1093/mnras/stab342)

de Vaucouleurs G., de Vaucouleurs A., Corwin Herold G. J., Buta R. J., Paturel
G., Fouque P., 1991, Third Reference Catalogue of Bright Galaxies
[van den Bergh S., 1976, ApJ, 206, 883](http://dx.doi.org/10.1086/154452)
[van den Bergh S., 2009, ApJ, 702, 1502](http://dx.doi.org/10.1088/0004-637X/702/2/1502)


MNRAS **000**, 1–13 (2023)

_NGC 1436: the making of a lenticular galaxy in the Fornax cluster_ 13


**APPENDIX A:**


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–13 (2023)

14 _A. Loni et al._



**Figure A1.** We show the comparison between the channel-maps of the 11 [′′] cube (green) and the TiRiFiC model (blue) used to measure the rotational velocity
and SB in Fig. 4. For presentation purpose, we re-binned the channel-maps in velocity to 23 km s [−][1] channels. We show the same contours at ∼3σ (where σ is
the RMS of the re-binned cube), with subsequent contours increasing as ×2 _[n]_ (with n=1,2,3 ..), both for the data and the model. In general, the model follows the
H I rotation in the data, and in the two middle rows, we can see how TiRiFiC nicely models the H I depression visible in the center of the galaxy. Black contours
are the 11 [′′] H I image (Fig. 2).


MNRAS **000**, 1–13 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Overlay 11'' and 66'' MeerKAT HI contours and ALMA CO contours on FDS optical image, extract HI spectra using detection masks, compute M_HI using Eq. 50 in Meyer et al. (2017), and compute M_H2/M_HI using M_H2 from Zabel et al. (2021)",
  "failed_quote": "Using Eq. 50 in Meyer et al. (2017), we estimate the total M H I to be (1.9 ± 0.2) × 10 [8] M ⊙ ."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Fit the 11'' MeerKAT HI cube using a tilted-ring model in TiRiFiC with a flat disc (single PA and inclination across all rings) and parameter interpolation in groups of rings",
  "failed_quote": "In the rest of this section we show results obtained by fitting the H I kinematics of the high-resolution cube with the Tilted Ring Fitting Code (TiRiFiC - Józsa et al. 2012)."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Tilted ring fitting and interpolation of model parameters in groups of model rings",
  "failed_quote": "We further improve the output flat disc model by using an advanced feature of TiRiFiC, which allows us to fit and interpolate some model parameters in groups of model rings rather than for each ring independently."
 },
 {
  "path": "analysis_steps[2].key_parameters[1].evidence[0]",
  "value": "MILES SSP models: age 30 Myr to 14 Gyr, -2.27 <= [M/H] <= 0.4 dex, [alpha/Fe] between 0 and 0.4 dex",
  "failed_quote": "we fit them with pPXF and GandALF using SSP models from the MILES library of Vazdekis et al. (2015), which covers a range in age between 30 Myr and 14 Gyr, with total metallicity −2.27 ≤[M/H]≤ 0.4 dex, and α-element overabundance [α/Fe] between 0 and 0.4 dex."
 },
 {
  "path": "analysis_steps[2].key_parameters[2].evidence[0]",
  "value": "Multiplicative polynomial order varied between 6 and 15; age bins: 1-Gyr wide (0-6 Gyr) and 2-Gyr wide (>6 Gyr)",
  "failed_quote": "to estimate the SFH in each sector s we bin the resulting initial stellar-mass values M i SSP, s in 1-Gyr-wide age bins between 0 and 6 Gyr and in 2-Gyr-wide bins beyond that."
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Tilted ring fitting of the high-resolution MeerKAT HI cube kinematics and surface brightness profile",
  "failed_quote": "In the rest of this section we show results obtained by fitting the H I kinematics of the high-resolution cube with the Tilted Ring Fitting Code (TiRiFiC - Józsa et al. 2012)."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Total HI flux (MeerKAT 66'') = 2.01 Jy km s^-1",
  "failed_quote": "MeerKAT 66'' - Flux = 201 ± 020 J km s 1"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Total HI mass (M_HI) = 1.9e8 M_sun",
  "failed_quote": "Using Eq. 50 in Meyer et al. (2017), we estimate the total M H I to be (1.9 ± 0.2) × 10 [8] M ⊙ ."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "CO follows the HI ring, has no central detection, and co-rotates consistently with the HI in a settled disc.",
  "failed_quote": "Here, we can see that the CO follows the H I ring and that there is no CO detected in the center of the galaxy."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "MeerKAT data available on survey website; Fornax3D MUSE data in ESO archive (296.B-5054); ALMA data in ALMA archive (2015.1.00497.S and 2017.1.00129.S).",
  "failed_quote": "The data underlying this article from: (i) the MeerKAT Fornax Survey are available at the following link https://sites.google.com/inaf.it/meerkatfornaxsurvey/data, (ii) the Fornax3D survey are available in the ESO archive (program ID: 296.B-5054 - see also new-data-release-of-muse-data-cubes-of-the-fornax3d-survey), (iii) the ALMA Fornax Cluster Survey and the Deep CO(J=1-0) mapping survey of Fornax galaxies with Morita array are available in the ALMA archive (project code 2015.1.00497.S and 2017.1.00129.S, respectively)."
 }
]
```
