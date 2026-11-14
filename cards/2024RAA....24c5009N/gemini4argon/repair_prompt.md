# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024RAA....24c5009N\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Research in Astron. Astrophys. Vol.0 (20xx) No.0,


000–000


_http://www.raa-journal.org_ _http://www.iop.org/journals/raa_


(L [A] TEX: epaqrraa.tex; printed on August 9, 2024;


15:10)


## R esearch in A stronomy and A strophysics


# **EP Aquarii: a new picture of the circumstellar envelope**

## Pham T. Nhung, Do T. Hoai, Pierre Darriulat, Pham Tuan-Anh, Pham N. Diep, Nguyen B. Ngoc and Tran T. Thai

Department of Astrophysics, Vietnam National Space Center, Vietnam Academy of

Science and Technology, 18, Hoang Quoc Viet, Nghia Do, Cau Giay, Ha Noi,

Vietnam. _pttnhung@vnsc.org.vn_


Received 20xx month day; accepted 20xx month day


**Abstract** New analyses of earlier ALMA observations of oxygen-rich

AGB star EP Aquarii are presented, which complete a previously published

analysis and offer a different interpretation of the morpho-kinematics of

the circumstellar envelope (CSE). The birth of the equatorial density en
hancement (EDE) is shown to occur very close to the star where evidence

for rotation has been obtained. Close to the star and where outflows have

been observed: their interaction with the gas of the nascent EDE, is seen

to play an important role in the development of the wind and the evolution
of its radial velocity from 8-10 km s _[−]_ [1] on the polar symmetry axis to _∼_ 2
km s _[−]_ [1] at the equator. It implies a complex morpho-kinematics: making

reliable interpretations with reasonable confidence is difficult. In particu
lar, it questions an earlier interpretation implying the presence of a white

dwarf companion orbiting the star at an angular distance of _∼_ 0.4 arcsec

from its centre. It proposes instead an interpretation in terms of a standard

mass ejection associated with a shock wave leaving a void of emission in

its wake. High Doppler velocity wings are seen to consist of two compo
nents, the upper velocity end of the global wind, reaching above _±_ 12 km
s _[−]_ [1], and an effective line broadening, confined within 200 mas from the
centre of the star, reaching above _±_ 20 km s _[−]_ [1] and interpreted as caused by

2 Nhung P.T., Hoai D.T., Darriulat P. et al.


the pattern of shock waves resulting from the interaction between stellar

pulsation and convective cell partition.


**Key words:** stars: AGB and post-AGB – circumstellar matter – stars: in
dividual: EP Aqr – radio lines: stars


**1** **INTRODUCTION**


When instruments providing observations of high sensitivity and angular and spec
tral resolutions became available, mainly the Very Large Telescope (VLT) and the

Atacama Large Millimeter/submillimeter Array (ALMA), studies of the circumstel
lar envelopes (CSE) of Asymptotic Giant Branch (AGB) stars progressed rapidly. Yet,

many questions are still unanswered concerning the mechanism that governs the gen
eration and acceleration of the wind, in particular for oxygen-rich low mass-loss rate

stars. In contrast with carbon-rich stars, these have a dusty envelope that is more trans
parent in the visible and near-IR, giving a better view of the innermost dust-forming

atmospheric layers (H¨ofner & Freytag 2019). Their study supports a scenario where

the radiation pressure, which accelerates the outflows, is caused by photon scattering

on highly transparent iron-free grains, such as corundum (Al 2 O 3 ), which form a thin

gravitationally bound dust layer close to the stellar photosphere; beyond it, silicate dust

condenses on top of corundum cores, speeding up grain growth to the critical size.


Recent high-resolution imaging of nearby AGB stars at visible and infrared wave
lengths has revealed complex, non-spherical distributions of gas and dust in the close

circumstellar environment, with changes in morphology and grain sizes occurring over

the course of weeks or months. At millimetre wavelengths complexity is the main fea
ture that characterizes the morpho-kinematics of the CSE, with important anisotropy

and inhomogeneity. Such distribution of atmospheric gas emerges naturally in 3-D hy
drodynamical models (H¨ofner & Freytag 2019) as a consequence of large-scale con
vective flows below the photosphere and the resulting network of atmospheric shock

waves, the dynamical patterns in the gas being imprinted on the dust in the close stel
lar environment. Global AGB star models are characterized by giant convection cells,

which can span over a steradian, and have a lifetime of many years. Together with

radial pulsations, with typical periods at a few-month scale, they generate waves of

various frequencies and spatial scales, which quickly develop into shock waves giving

rise to ballistic gas motions peaking around 2 stellar radii. As the shock waves interact

and merge, they produce large-scale regions of enhanced densities in their wakes.

EP Aquarii: a new picture of the circumstellar envelope 3


A consequence of the resulting complexity is the difficulty to reconstruct reliably

the observed morpho-kinematics of the CSE in both velocity and space, driving its

study into proceeding somewhat by trials and errors: successive observations and anal
yses bring new information that helps refining the picture. EP Aquarii provides such an

example with four recent publications by Homan et al. (2018), Tuan-Anh et al. (2019),

Hoai et al. (2019) and Homan et al. (2020a). It is an M-type, semi-regular variable

star (spectral type M8III), with a pulsation period usually quoted as 55 days but more

like 110 _±_ 20 days (Eggen 1973; Tabur et al. 2009), located at 119 _±_ 6 pc from the solar

system (van Leeuwen 2007; Gaia Collaboration 2018); it shows no technetium in its

spectrum (Lebzelter & Hron 1999) and has an effective temperature of _∼_ 3240 K, a

mass of _∼_ 1.7 M _⊙_, a radius of _∼_ 0.77 au (Dumm & Schild 1998) and a mass-loss rate
of _∼_ (1.6 _±_ 0.4) 10 _[−]_ [7] M _⊙_ yr _[−]_ [1] (Hoai et al. 2019).

The resulting picture that emerges from the four more recent studies of the CSE is

a two-component morpho-kinematics producing a Doppler velocity spectrum made of

a narrow central peak at star systemic velocity and a broader plateau extending over
_∼±_ 10-11 km s _[−]_ [1] . The central peak is associated with an oblate, and the broad plateau

with a prolate volume of gas, both expanding radially and sharing a same axis that

projects _∼_ 20 _[◦]_ west of north and is inclined by only _∼_ 10 _[◦]_ with respect to the line of

sight. The oblate volume of gas, referred to as Equatorial Density Enhancement (EDE),

or occasionally torus or disc, is nearly face on, causing its radial expansion velocity to
be poorly defined, _∼_ 2 km s _[−]_ [1] . It hosts a complex pattern of arcs of enhanced CO(2
1) emission that is interpreted by Homan et al. (2018, 2020a) in terms of a spiral

produced by a white dwarf companion, with a mass of 0.65-0.80 M _⊙_, orbiting EP Aqr

at a distance of _∼_ 0.4 arcsec and currently located west of it. The prolate volume of gas,

usually referred to as polar or bi-conical outflows, displays maximal velocity along the

line of poles but clear density depressions near the poles, the maximum being reached

at stellar latitudes between _∼±_ 45 _[◦]_ and _∼±_ 60 _[◦]_ while the transition between oblate

and prolate components occurs progressively near stellar latitudes of _∼±_ 20 _[◦]_ .

Evidence for rotation within some 100-200 mas from the centre of the star, with
a rotation velocity at km s _[−]_ [1] scale, has been obtained from the observation of the

emissions of the CO(2-1), SO 2 (16 6 _,_ 10 -17 5 _,_ 13 ) and SO 2 (4 2 _,_ 2 -3 1 _,_ 3 ) lines (Homan et al.
2018, 2020a; Tuan-Anh et al. 2019). Observations of the dust induced polarization

of the 550-750 nm emission observed at the VLT using SPHERE-ZIMPOL (Homan

et al. 2020a) give evidence for a shell of dust surrounding the star and having an inner

radius slightly smaller than 100 mas. A study of dust emission in the infrared using the

Small Wavelength Spectrometer aboard ISO (Heras & Hony 2005) has given evidence

4 Nhung P.T., Hoai D.T., Darriulat P. et al.


for very low ratios of both gas-to-dust mass and aluminium oxide to silicates relative

abundance.


There exists no well-established interpretation of the observed morphology. EDE’s

are usually described as the result of the gravitational attraction of the stellar wind in

the orbital plane of a companion and the polar outflows are often interpreted as episod
ically produced by the rapid rotation of an accretion disc surrounding this companion

and reach very high velocities. Such are the cases of HD 101584 (Olofsson et al. 2019)
with highly collimated outflows reaching velocities of _∼±_ 140 km s _[−]_ [1], of _π_ [1] Gruis

(Doan et al. 2017, 2020; Homan et al. 2020b) with polar outflows consisting of thin
hourglass-shaped bubbles reaching a radial expansion velocity of _∼_ 60 km s _[−]_ [1], of V
Hya (Sahai et al. 2022) with high velocity lumpy jets of velocity _∼_ 175 km s _[−]_ [1], and of

R Aqr (Melnikov et al. 2018; Liimets et al. 2018; Bujarrabal et al. 2021) with outflows
made of curved central jets with velocity reaching _∼_ 240 km s _[−]_ [1] surrounded by hourglass bubbles in ballistic expansion with velocity of _∼_ 55 km s _[−]_ [1] . Much closer to the

morpho-kinematics of the EP Aqr CSE is that of AGB star RS Cnc, which however

displays a clear technetium signal, but is too boreal to be observed by ALMA and has

been studied in detail using NOEMA (Winters et al. 2022). It has a two-component

morpho-kinematics, quantitatively similar to EP Aqr, with an axis making an angle of
_∼_ 30 _[◦]_ with the line of sight and radial expansion velocities reaching 3-4 km s _[−]_ [1] in the
EDE and 8-9 km s _[−]_ [1] in the bipolar outflows.


Neither EP Aqr nor RS Cnc has been shown to host a companion (but in both cases

the presence of an undetected companion cannot be excluded) and no other known

AGB star displays a close enough morpho-kinematics to be claimed to serve as a model

for their CSE. The question of their genesis remains therefore open and, in the case of

EP Aqr, the picture proposed by Homan et al. (2020a), suggesting the presence of an

undetected white dwarf companion playing a major role in the formation and structure

of the EDE, leaves several questions unanswered that call for further study:


i) High Doppler velocity wings, reaching _∼±_ 20 km s _[−]_ [1], were interpreted by Tuan
Anh et al. (2019) as two narrow polar structures, referred to as jets, launched from

less than 25 au away from the star and building up between _∼_ 20 au and _∼_ 100 au

to maximal velocity. However, subsequent analyses of similar high Doppler velocity

wings observed in several other stars, as, for example _o_ Ceti (Hoai et al. 2020; Nhung

et al. 2022), favoured interpretations in terms of shocks produced close to the star

by pulsations and convective cells, shedding strong doubts on the jet interpretation

proposed for EP Aqr. It has therefore become imperative to reconsider the case.

EP Aquarii: a new picture of the circumstellar envelope 5


ii) The formation of the bipolar outflows remains unexplained. It may invite inter
pretations in terms of magnetic fields (Garc´ıa-Segura et al. 2005; Winters et al. 2022),

or in terms of interacting winds in a binary (Nordhaus & Blackman 2006; Castellanos
Ram´ırez et al. 2021), and more specifically in terms of an additional companion or
biting EP Aqr at a distance of _∼_ 10 au (Homan et al. 2020a), but none of these can be

solidly justified. The latter authors present a number of relevant suggestive arguments

in relation to the observation of a complex pattern of arcs in the emission of the polar

outflows.

iii) The formation of the EDE remains equally unexplained. The interpretation pro
posed by Homan et al. (2020a), in terms of focusing by an assumed white dwarf com
panion is in principle compelling but raises unanswered questions and is likely to face

inconsistencies when details of the observed morpho-kinematics are being considered.

iv) A clear depression of SiO(5-4) line emission is observed in the western blue
shifted octant and interpreted by Homan et al. (2020a) as the result of molecular disso
ciation produced by the UV radiation of the white dwarf companion. However, to the

extent that the companion can be naively expected to sit in the median plane of the disc

that it has generated, such dissociation should extend to the red-shifted hemisphere as

well and the observed morphology of the depression is difficult to understand in such

terms.

The aim of the present article is therefore to shed new light on these issues, by

presenting new additional analyses of the emissions of the CO(2-1) and SiO(5-4) lines,

in particular in the close neighbourhood of the star. As a brief reminder of the main

properties of the CSE of EP Aquarii, we display in Figure 1 intensity maps of the

CO(2-1) and SiO(5-4) line emissions, together with Doppler velocity spectra and a

schematic description of the axi-symmetric geometry.


**2** **OBSERVATIONS AND DATA REDUCTION**


We use archival ALMA observations of the CO(2-1) and SiO(5-4) line emis
sions of EP Aquarii that were performed in 2016 and 2019 under projects

ADS/JAO.ALMA#2016.1.00057.S and ADS/JAO.ALMA#2018.1.00750.S, respec
tively (PI W. Homan). Observations and data reduction have been described in much

detail by Homan et al. (2018, 2020a) and do not need to be repeated here. The latter

observations (referred to as TM0) used an extended antenna configuration and were

combined with the earlier observations of lower angular resolution by Homan et al.

(2020a) with a low weight of 20% by fear of possible artefacts associated with the lack

of short spacings. In the present article, in order to better understand their contribution

6 Nhung P.T., Hoai D.T., Darriulat P. et al.


~~a~~ ~~b~~ c



North


Polar
expansion



20 [o]


Equatorial
expansion



~~C~~ ounter~~c~~ lockwise
rotation



E ~~a~~ st West



Equatorial
expansion



Counterclockwise
rotation



Polar
expansion



South



Fig. 1: (a) intensity map of CO(2-1) emission; (b) intensity map of SiO(5-4) emis
sion; (c) Doppler velocity spectra of both CO(2-1) and SiO(5-4) line emissions; (d)

schematic of the red-shifts resulting from the tilted axi-symmetric geometry. The
colour scales are in units of Jy arcsec _[−]_ [2] km s _[−]_ [1] .


Table 1: Summary of Band 6 observations and data reduction of the CO(2-1) (230.55

GHz) and SiO(5-4) (217.12 GHz) line emissions.


Beam size Beam PA Channel width Time Noise rms Maximal Recoverable
Reference Epoch Line
(mas [2] ) ( _[◦]_ ) (km s _[−]_ [1] ) on source (mJy beam _[−]_ [1] ) Scale (”)

Homan et al. (2018) 2016 CO(2-1) 170 _×_ 150 _−_ 34 _∼_ 0.33 70 min (ACA) 1.25 15
SiO(5-4) 230 min (TM1,2)
Combined data 2016, CO(2-1) 87 _×_ 79 +15 _∼_ 0.33 _−_ 0.65 15
Homan et al. (2020a) 2019 SiO(5-4) 85 _×_ 79 +7

TM0 data CO(2-1) 32 _×_ 28 +13 0.95 1.0 0.5
2019 99 min
present work SiO(5-4) 32 _×_ 30 +22 0.34 1.34 0.5


to the combined data, we reduced them separately and report about the results in the

present section. The combined data are obtained from Homan et al. (2020a) via the

CDS (http://cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/642/A93). It should be sufficient to

summarize their main features in Table 1.

The 2019 observations were made in two steps, on June 5 and 14, respectively, with

a hybrid antenna configuration (C43-10 and C43-9) including _∼_ 46 antennas having

_∼_
baseline lengths between 83 and 16000 m. A gap at short spacing ( 100-200 m), seen

in the baseline length distribution of June 14 (Figure 2a), is due to the absence of four

antennas (circled in red in Figure 2b). Four spectral windows were selected to observe
line emissions of CO(2-1), SiO(5-4), SO 2 (4 2 _,_ 2 -3 1 _,_ 3 ), and [13] CO(2-1). However, the latter
two sets of data had insufficient sensitivity to contribute significantly new information

and their analysis is omitted from the present work.

The data of June 5 and 14 observations of the CO(2-1) and SiO(5-4) line emissions

have been merged with equal weights and grouped in frequency channels corresponding to Doppler velocity intervals of 0.95 and 0.34 km s _[−]_ [1], respectively. Natural weight
ing was used for cleaning, producing maps of 2000 _×_ 2000 pixels covering _±_ 4 arcsec

EP Aquarii: a new picture of the circumstellar envelope 7


in both _x_ (pointing east) and _y_ (pointing north), with FWHM beam sizes of 31.7 _×_ 28.0
mas [2] and 32.4 _×_ 30.0 mas [2], respectively. We did not subtract the continuum contribu
tion at visibility level, which would have been improper when looking over the stellar

disc because of important absorption. We performed self-calibration but, as it did not

result in a significant improvement of the quality of the line images, the data used here

do not include self-calibration.


The impact of the lack of short spacing below _∼_ 100 m was found to be different be
tween the CO(2-1) line, with emission extending up to some 10 arcsec angular distance

from the star and SiO(5-4) line emission, confined within some 3 arcsec. Moreover, in

the case of the CO(2-1) line emission, it was also observed to be stronger near sys
temic Doppler velocity, where the emission is dominated by a disc extending to large

angular distances. The size of the mask, which defines the region in the source plane

over which the cleaning procedure is applied, must therefore be chosen accordingly.

We studied in detail images obtained with different mask sizes and retained a radius of

2 arcsec for the SiO(5-4) data and of 1 arcsec for the CO(2-1) data, resulting in noise
levels of 1.34 mJy beam _[−]_ [1] for SiO(5-4) line emission and 1.0 mJy beam _[−]_ [1] for CO(2-1)

line emission. While the nominal maximal recoverable scale (MRS) corresponding to

the C43-10 antenna configuration is 0.46 arcsec, the impact on imaging of the lack of

short spacing cannot be simply measured by a single number. As the angular distance

from the star increases, it reduces the detected flux first uniformly, then introducing

anisotropic distortions of the emission pattern. We studied its effect in much detail,

both comparing the produced images with those given by the combined data and by

modelling the source as discs of various sizes. While the decline of detected flux starts

well below the nominal MRS, important distortions appear only beyond _∼_ 0.6-0.7 arc
sec. For the purpose of the present work, we checked carefully that whenever TM0 data

were used, proper account was taken of this issue. Channel maps of the SiO(5-4) and

CO(2-1) line emissions are shown in Figures S1 and S2 of the supplementary material.

Examples of comparison between TM0 and combined data are illustrated in Figures 2,

4, 14 and 15.


We use Cartesian coordinates with the _z_ axis pointing away from Earth in addition

to the _x_ and _y_ axes in the plane of the sky. We refer the Doppler velocity _V_ _z_ to a
systemic star velocity of _−_ 33.6 km s _[−]_ [1] in conformity with earlier work, but its value is
not known to better than a fraction of a km s _[−]_ [1] . We define an angular distance from the
centre of the star as _R_ =√ _x_ [2] + _y_ [2] and a position angle _ω_ measured counter-clockwise


from north.

8 Nhung P.T., Hoai D.T., Darriulat P. et al.


a b c d


Fig. 2: (a) distribution of the decimal logarithm of the uv distance (in meters) for the

different data sets; (b) antenna configuration (centre region); the four antennas circled

in red were absent for the June 14 observations; (c,d) radial distributions of CO (black)

and SiO (red) emissions using TM0 (c) and combined data (d).


**3** **EQUATORIAL DENSITY ENHANCEMENT**


**3.1** **CO(2-1) emission**


Evidence for the presence of an equatorial density enhancement (EDE) is known from

previous work to rest on the observation of the CO(2-1) and CO(1-0) line emissions

exclusively (Hoai et al. 2019). However, a clear distinction between EDE and polar

outflows could only be made at distances from the star exceeding _∼_ 2 arcsec. The avail
ability of high angular resolution data makes it now possible to study the EDE mor
phology at short distances from the star. As illustrated in the upper panels of Figure

3, Doppler velocity spectra integrated over successive rings centred on the star give

clear evidence for the presence of the narrow component when _R_ exceeds _∼_ 200 mas.
It covers Doppler velocities between 0 and +2 km s _[−]_ [1] . Remarkably, the neighbouring
channels, between _−_ 3 and 0 km s _[−]_ [1] and 2 and 5 km s _[−]_ [1], respectively, are depopulated.

This may suggest that very close to the star gas is bent toward the equatorial plane,

depopulating these channels to the benefit of the narrow component. Channel maps

integrated over the corresponding intervals of Doppler velocity are displayed in the

lower panels of Figure 3. In the blue-shifted depopulated Doppler velocity intervals,
emission is enhanced in the north-eastern quadrant. The intervals of high _|V_ _z_ _|_ values
( _−_ 10 to _−_ 3 and 5 to 12 km s _[−]_ [1] ) host outflows expanding along the polar axes; they are

discussed in Section 4.


In order to better explore the morpho-kinematics of the nascent EDE, we display

in Figure 4 _V_ _z_ vs _ω_ maps of the CO(2-1) emission in 100 mas wide rings centred on

the star. They show that the EDE is already present in the smaller ring, _R_ between 100

EP Aquarii: a new picture of the circumstellar envelope 9


and 200 mas, and its kinematics is dominated by rotation at a few km s _[−]_ [1] scale. This

evidence for very precocious formation of the EDE had not been made explicitly earlier

although Homan et al. (2020a) had remarked that it is suggested by their SPHERE data.

In particular, it raises questions in the context of the interpretation given by Homan

et al. (2020a), which would imply an inner EDE radius of _∼_ 400 mas, corresponding

to the orbit of the assumed companion, with strong anisotropy. Unfortunately, with

presently available data, it is difficult to tell apart, in the immediate neighbourhood

of the star, say below _R∼_ 200 mas, the contributions of expansion, of rotation and of

phenomena related to the generation of the nascent wind: dust formation and shock

waves caused by the interaction between stellar pulsation and convective cell partition

(see Section 5).


Farther away from the star, the EDE is seen to subsist up to large distances, as

illustrated in the pair of left panels of Figure 5 by the PV maps of the line emission

seen in the ring 1.2 _<R<_ 5.2 arcsec (see also channel maps of the CO(2-1) emission

shown in Appendix in both the _x_ vs _y_ plane, Figure A1, and the _ω_ vs _R_ plane, Figure

A2). These maps, drawn in the _V_ _z_ vs _R_ and _V_ _z_ vs _ω_ planes, respectively, show enhanced
emission over all values of _R_ and _ω_ in the central Doppler velocity interval, _|V_ _z_ _|<_ 2 km
s _[−]_ [1] . Similar PV maps drawn in small intervals of _R_ and _ω_ are shown in Appendix

(Figures A3 and A4). In each ( _ω, R_ ) bin, with a width of 10 _[◦]_ _×_ 100 mas, we calculate
the mean and rms values of _V_ _z_ over the central Doppler velocity interval, _|V_ _z_ _|<_ 2 km
s _[−]_ [1] . Their values are shown as a function of _R_ and _ω_ in the pair of right panels of
Figure 5. They display remarkable uniformity, the rms value staying near 1 km s _[−]_ [1]


over the whole radial range and the mean value near zero. A small _ω_ asymmetry of

the latter, below _R∼_ 3 arcsec, reveals an inclination of the EDE with respect to the

plane of the sky consistent with the known inclination of the axis of the CSE with
respect to the line of sight: it reaches values of _∼_ 0.3 km s _[−]_ [1] in the NW direction and
of _∼−_ 0.3 km s _[−]_ [1] in the SE direction. This suggests a radial expansion velocity at the
scale of _∼_ 0.3/sin10 _[◦]_ =1.7 km s _[−]_ [1], consistent with the low value of 1.9 km s _[−]_ [1] retained
in earlier studies (Hoai et al. 2019). The rms deviation of 1 km s _[−]_ [1] combines the effect
of the known rms flaring angle of _∼_ 15 _[◦]_, sin15 _[◦]_ _×_ 1.7=0.44 km s _[−]_ [1] to an intrinsic width
of _∼_ 0.9 km s _[−]_ [1] .


**3.2** **SiO(5-4) emission**


In order to compare CO(2-1) and SiO(5-4) line emissions in the close neighbourhood

of the star, we display in Figure 6 for SiO(5-4) (TM0 data) the same distributions as

10 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. 3: CO(2-1) line emission, TM0 data. Upper panels: Doppler velocity spectra in

successive rings, each 100 mas wide, starting from the circle of radius 100 mas centred

on the star. Lower panels: brightness maps averaged over the velocity intervals asso
ciated with the structure of the spectra displayed on the upper panels for _R>_ 200 mas,

and indicated on top of each panel.


Fig. 4: CO(2-1) emission: TM0 (upper row) and combined (lower row) data. _V_ _z_ vs _ω_

maps in 100 mas wide rings as indicated on top of each panel. The vertical lines are

at _ω_ values of 180, 270 and 360 _[◦]_ . The sine waves shown as reference correspond to
pure rotation with a velocity of 4 km s _[−]_ [1] . Pure expansion of a same velocity would be
phase-shifted by +90 _[◦]_ . The colour scales are in units of mJy beam _[−]_ [1] .

EP Aquarii: a new picture of the circumstellar envelope 11


~~a~~ ~~b~~ c ~~d~~


Fig. 5: CO(2-1) line emission, combined data. Left pair of panels: PV maps in the _V_ _z_

vs _ω_ (panel a) and _V_ _z_ vs _R_ (panel b) planes of the projections of the data cube defined
as 1.2 _<R<_ 5.2 arcsec and _|V_ _z_ _|<_ 8 km s _[−]_ [1] . Right pair of panels: distribution in the _ω_ vs

_R_ plane of the mean (panel c) and rms (panel d) values of _V_ _z_ over the central Doppler
velocity interval, _|V_ _z_ _|<_ 2 km s _[−]_ [1] .


shown in Figure 3 for CO(2-1). They show a very different picture than those of CO(2
1) emission. The spectra cover a broad range of Doppler velocities, independently from

the distance to the star, with no sign of change beyond 200 mas. The narrow component

contributes only a very small enhancement. Absorption from the outer layer having
reached terminal velocity at 8-10 km s _[−]_ [1] is seen on all four spectra. In contrast with

CO(2-1) emission, the brightness maps show little structure but reveal the presence of

a strong depression of emission at _∼_ 400 mas west from the centre of the star. This

depression has been abundantly studied and commented upon in the earlier literature

and we report on its properties in Section 4, to which we defer possible interpretations.

Here we simply remark that the different response to temperature of the two lines can
only have small effects. They differ essentially by the value of the energy _E_ up of the
upper level, 16.60 K for CO(2-1) and 31.26 K for SiO(5-4). This quantity enters in
the expression of the emissivity as a factor e _[−][E]_ [up] _[/T]_, where _T_ is the temperature. The

ratio between CO(2-1) and SiO(5-4) line emissions of the values taken by this factor

for _T_ =10 K, 20 K, 50 K and _>_ 100 K is 4.3, 2.1, 1.3 and _<_ 1.2, respectively.


**3.3** **Patterns of enhanced CO(2-1) emission**


The emission of the CO(2-1) line is known from earlier work to display significant

fluctuations. Hoai et al. (2019) remarked that both CO(1-0) and CO(2-1) emissions

in the EDE display remarkably similar intensity fluctuations, at the level of _∼±_ 36%,

dominated by an eastern enhancement in the form of an arc and a southwestern depres
sion, together having the appearance of a spiral. Homan et al. (2018) described similar

12 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. 6: Same as Figure 3 for the SiO(5-4) emission.


data as evidence for a bright nearly face-on spiral structure, claiming the first convinc
ing detection of a spiral in the circumstellar environment of an oxygen-rich AGB star,

with a higher degree of small scale hydrodynamical structure and wider spiral arms

than in carbon-rich environments. In their second paper, Homan et al. (2020a) gave

a very detailed description of the EDE intensity fluctuations and concluded that the

observed complex emission pattern strongly resembles the typical hydrodynamical gas

flow patterns associated with the interaction of a mass-losing AGB star with a com
panion. They claimed to have identified the flow along the L1 and L3 Lagrange points,

before they coalesce into the spiral that manifests at larger length-scales and argued

for the presence of a companion located at 0.4 arcsec to the west of the star, probably

a white dwarf, with a mass between 0.65 and 0.8 M _⊙_ .

Channel maps of the combined data of CO(2-1) line emission in the twelve frequency channels that bracket the systemic velocity of the star ( _−_ 2.0 _<V_ _z_ _<_ 1.8 km s _[−]_ [1] )

are shown in Figure 7. They display arcs of enhanced emission. The complexity of the

patterns makes a reliable interpretation in terms of well identified individual compo
nents difficult. In particular it makes it easy to interpret two partly overlapping arcs

as a single one and an arc that is not centred on the star as a spiral arm. The human

eye is too subjective a tool for a reliable interpretation of the observed patterns. In this

context, the reality of the spiral discovered by Homan et al. (2018) deserves being crit
ically discussed. There is no doubt that identifying such a spiral in the pair of central

EP Aquarii: a new picture of the circumstellar envelope 13


Fig. 7: Channel maps of the CO(2-1) line emission (combined data) over the Doppler
velocities (km s _[−]_ [1] ) covering the EDE ( _|V_ _z_ _|<∼_ 2 km s _[−]_ [1] ) as indicated on top of each
panel. The central region ( _R<_ 1.5 arcsec) is blanked-out for clarity. Contours are shown

at 50% of the maximal brightness.


frequency channels (centred at 0.05 and _−_ 0.27 km s _[−]_ [1], Figure 7) is a natural and rea
sonable thing to do. However, we note that the neighbouring channels (centred at 0.37
and _−_ 0.59 km s _[−]_ [1], respectively) host patterns suggesting that the source of emission

is in a plane inclined with respect to the sky plane: they shine in the NW direction for

the red-shifted side and in the SE direction for the blue-shifted side, as expected for a

plane perpendicular to the known axis of the CSE. Correcting for this tilt by averaging
the brightness over the four central channels, ( _−_ 0.75 _<V_ _z_ _<_ 0.53 km s _[−]_ [1] ) we obtain the

map shown in the left panel of Figure 8. The identification of a spiral as proposed by

Homan et al. (2018) and shown in the central panel of the figure is no longer obvious.

Assessing the reliability of the identification of such a spiral is indeed difficult. As il
lustrated in the right panel of Figure 8, arcs of spirals are excellent approximations to

arcs of circles having their centre offset with respect to the centre of the star. But the

two halves of a single circle correspond to different spirals winding in opposite direc
tions; a proper spiral winds instead in a single direction and expands indefinitely: an

arc having a point of closest approach to the star cannot be described as a single spiral.

In summary, the EDE is mostly seen in CO line emission as a disc slightly inclined

with respect to the plane of the sky, formed within some 100 mas from the centre of the

star and having an rms flaring angle of _∼_ 15 _[◦]_ . Its small inclination prevents a precise

evaluation of the morpho-kinematics but evidence has been obtained for rotation in the
central region evolving to radial expansion at a low rate of less than 2 km s _[−]_ [1] beyond a

14 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. 8: Left: Brightness of the CO(2-1) line emission (combined data) averaged over
the four central panels of Figure 7 ( _−_ 0.75 _<V_ _z_ _<_ 0.53 km s _[−]_ [1] ). Contours are shown at

50% and 70% of maximal brightness. Centre: from Figure 5 of Homan et al. (2018),

central channel of the CO(2-1) line emission. A black dashed Archimedean spiral is
over plotted to guide the eye. Right: Comparing two spirals of equation _ρ_ = 0 _._ 5 + _α/π_
(blue and red) with two circles (black) of radius _R_ = 1 _._ 5 (2) offset by _−_ 0.5 (+0.5) with

respect to the origin. The polar angle _α_ cancels on the axis along which the circles are

offset and increases clockwise for the blue spiral and counter-clockwise for the red

spiral.


fraction of an arcsec from the centre of the star. Such a small expansion velocity results

probably in part from the low penetration of the stellar radiation into the dense disc,

limiting its effectiveness at accelerating dust grains. Assuming a 10 arcsec disc radius

(Figure 6 of Homan et al. 2018), it implies that the disc is at least thirty centuries old.

Arcs of enhanced emission are observed on the disc but their interpretation as forming

a spiral has been disputed.


**4** **POLAR OUTFLOWS**


**4.1** **CO(2-1) emission**


The polar outflows cover a broad region of the sky up to large velocities. This is il
lustrated in Figure 9, which displays _V_ _z_ vs _R_ maps integrated over position angles for

the blue-shifted and red-shifted hemispheres separately. A simplified schematic of the

morpho-kinematics of the CSE is shown in the right panel of Figure 9.

The polar outflows were observed earlier to display density fluctuations at the level

of _∼±_ 26%, and to reveal both an asymmetry between blue- and red-shifted hemi
spheres and significant differences between CO(1-0) and CO(2-1) emissions (Hoai

et al. 2019). The higher angular resolution of the present data allows for an improved

EP Aquarii: a new picture of the circumstellar envelope 15



Toward
Earth


2 EDE

Flaring rms: ± 30-40 [o]


2 ± 1 km s [-1]


0


Polar outflow


-2


10 ± 2 km s [-1]



10 ± 2 km s [-1]


Centre region
R <∼ 200 mas
Rotation and
High V z wings
∼ 10 [o]


Pointing 20 [o]
West of North


2 ± 1 km s [-1]



Fig. 9: Left pair of panels: _V_ _z_ vs _R_ maps of CO(2-1) line emission integrated over
position angle for the blue-shifted ( _V_ _z_ _<−_ 3 km s _[−]_ [1] ) and red-shifted ( _V_ _z_ _>_ 3 km s _[−]_ [1] )

hemispheres, separately. Right panel: schematic drawing of the geometry.


study of the morphology of the enhancements of CO(2-1) line emission. We studied

in great detail the data cube (combined data) covering 51 frequency channels (Doppler
velocities between _−_ 8.2 and +8.2 km s _[−]_ [1] ) and projected angular distances from the

star between 1.2 and 5.2 arcsec (Figures A1 to A4 of the Appendix). In some cases

where one might have feared that the steep radial decline of the intensity would have

been a source of bias, we examined the brightness divided by a power fit to its radial

distribution in the relevant frequency channel, found to have an index between _−_ 0.2

and _−_ 0.4. In no case was it considered to be a source of significant bias.


Ideally, one would like to describe each channel map as a set of well-identified

separated arcs of enhanced emission. We attempted to do so by using an algorithm

lumping together the brighter pixels. But we failed to obtain a satisfactory result, the

complexity of the patterns preventing reliable pattern recognition. Instead, for each

frequency channel, we inspected carefully the different projections of the data cube

and tried to describe the observed patterns as simply and reliably as possible. Figure

10 displays a pair of representative examples; they have not been selected to show

particularly clear patterns. There are many examples of clearer cases as well as of

more obscure cases.


Rather than giving a detailed review of our observations, we simply list the main

statements which we can make with confidence: in each map, the pattern of enhanced

emission can be described as a set of arcs; they are too numerous, frequently overlap
ping, to allow for reliable pattern recognition; they can be approximated by arcs of

circles covering a few tens of degrees, typically less than 180 _[◦]_ ; the contrast is small,

with a peak-to-valley ratio not exceeding a factor 2; the arcs always wind around the

16 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. 10: Examples of patterns of enhanced emission in the blue-shifted (left) and red
shifted (right) hemispheres. Lines guide the eye on some arbitrarily selected patterns.


star, implying that the centre of the associated circle is offset by less than a radius,

typically half a radius, from the centre of the star; their radii cover a broad range of

values, from as small as permitted by the angular resolution to as large as permitted by

the size of the maps under study, namely from a fraction of an arcsecond up to over

5 arcsec; very similar patterns are observed in adjacent frequency channels, covering
ranges up to a few km s _[−]_ [1] . These comments complement usefully those made in this

context by Homan et al. (2020a).


Finally, we remark that the _V_ _z_ vs _R_ map shown in Figure 5b (see also Figure

A3 of the Appendix) provides precious information on the dependence of the ra
dial expansion velocity on stellar latitude _α_ . It was assumed to be of the form
_V_ = _V_ eq + ( _V_ pole _−_ _V_ eq ) _×_ sin [2] _α_ in Hoai et al. (2019), where _V_ eq and _V_ pole are the expansion velocities at equator and pole, respectively. As illustrated in Figure 11, a small

volume of gas at distance _r_ from the star, at latitude _α_ and having a radial velocity _V_

has coordinates _V_ _z_ = _V_ sin _α_ and _R_ = _r_ cos _α_ . Namely, a spherical shell expanding at

radial velocity _V_ 0 and observed when it reaches a radius _R_ 0 is seen as a circle of unit
radius in the PV map _V_ _z_ _/V_ 0 vs _R/R_ 0 . In contrast, a ring expanding at the equator at velocity _V_ 1 is seen as a point on the _R_ axis at _V_ 1 _/V_ 0 . Understanding the transition between

the polar outflows and the EDE implies understanding the transition between these two

regimes. Namely, a shell emitted at some time with velocity _V_ 0 at the pole and velocity
_V_ 1 at the equator is seen as a curve of equation _V/V_ 0 = _V_ 1 _/V_ 0 +(1 _−V_ 1 _/V_ 0 ) _f_ ( _ϑ_ ) where
_ϑ_ is the polar angle, with _f_ (0)=0 and _f_ (90 _[◦]_ )=1. But _ϑ_ is equal to the stellar latitude

_α_ because the reference radius _R_ 0 used to define the axis of abscissa is the distance

covered at velocity _V_ 0, used as reference velocity on the axis of ordinate. Namely the

curve representing the shell in the PV diagram is a direct representation of the function

EP Aquarii: a new picture of the circumstellar envelope 17


Fig. 11: Latitudinal dependence of the radial expansion velocity. Left: schematics.

Centre and right : two examples of _V_ _z_ vs _R_ maps (CO(2-1) combined data) at _ω_ =65 _[◦]_


and 205 _[◦]_, respectively (from Figure S3). The red lines in the central and right panels

guide the eye on the flows of maximal emission.


_f_ ( _α_ ) that describes the dependence on stellar latitude of the expansion velocity. The
left panel of Figure 11 shows three examples of function _f_ ( _α_ ), all three of the form
sin _[n]_ _α_, with _n_ = [1] 2 [, 1 and 2 respectively (in addition to the trivial cases] _[ f]_ [(] _[α]_ [)][=0 and 1).]

Comparison with low latitude observations, as shown in the right panels of Figure 11

(see also Figure S3), favours clearly values of _n_ smaller than 1, in contradiction with

the arbitrary assumption made in Hoai et al. (2019). Specifically, it suggests that the

outflows are close to portions of spherical shells when emitted at large stellar latitudes,

and that their radial velocity decreases rapidly at small latitudes where their intera
tion with the disc becomes important. This is important information for modelling the

hydrodynamical flow, however a task beyond the scope of the present work.


Tentatively, the properties of the enhanced patterns of CO line emission in the po
lar outflows suggest that they take the form of shells of episodic mass ejections and

associated shock waves triggered by pulsations of amplitudes enhanced on the surface

of convective cells. The confinement of such cells within solid angles at steradian scale

limits the patterns observed in the channel maps to finite arcs rather than full circles.

Their radial velocity is maximal at the centre of the cell and drops near its edges,

causing the intersection of the shell with the sky plane of a given frequency channel to

appear eccentric. Moreover, their mean radial velocity increases from the equator to the

poles, implying a similar decrease of their density and causing the polar depressions

described by Hoai et al. (2019) and the appellation of ”bi-conical outflows” adopted

by Homan et al. (2020a). Their patterns are best revealed when looking at the _V_ _z_ vs _R_

18 Nhung P.T., Hoai D.T., Darriulat P. et al.


distribution of the line emission in a wedge of position angles not exceeding the size

of the convective cell (as done in the pair of right panels of Figure 11); integrating

over the whole range of position angles or over a large radial distance smoothens out

the fluctuations resulting from the episodic nature of the mass ejections, which, as we

shall see later, succeed each other at time intervals at the scale of a few decades. At the

present stage, such an interpretation is highly speculative but we shall see that further

observations described in the reminder of the present section will confirm its likely

validity.


**4.2** **SiO(5-4) emission: general features**


In contrast to CO(2-1) emission, SiO(5-4) emission is confined within radial distances

of _∼_ 3 arcsec, as shown in Figure 12, which displays radial distributions for both SiO(5
4) and CO(2-1) emissions. The emissions of the two lines are indeed expected to differ

in several respects: the SiO emission decreases with distance to the star, both because of

condensation on dust grains and of dissociation by UV interstellar radiation; moreover,

it is an efficient shock tracer.


As already remarked, and clearly apparent on the distributions of SiO(5-4) emission

displayed in Figure 13, one observes a significant asymmetry between the blue-shifted

and red-shifted hemispheres. In particular the former reveals the presence of a strong

depression of emission at some 400 to 500 mas west of the centre of the star that is

challenging interpretation. In a first step, we limit therefore our considerations to the

morphokinematics of the red hemisphere. To illustrate the small inhomogeneity of the
data cube, we show in Figure 13 the radial distribution _U_ ( _R_ ), averaged over position
angle and integrated over _V_ _z_, and the Doppler velocity spectrum _S_ ( _V_ _z_ ), of the volume
of the data cube defined as 0.5 _<R<_ 2.3 arcsec, 0 _<V_ _z_ _<_ 8 km s _[−]_ [1] ; we then compare
the observed intensity to the product _U_ ( _R_ ) _× S_ ( _V_ _z_ ), properly normalized, in the right

panels of the same figure. At the same time as the result reveals clearly the morpho
kinematics of the observed deviations with respect to a smooth distribution, it shows
that their amplitude is relatively modest, typically at the level of _±_ 20%. Both _U_ ( _R_ )
and _S_ ( _V_ _z_ ) show no significant fluctuation and the lumps of enhanced emissions have

typical sizes at the scale of a fraction of an arcsec. In contrast, on the _V_ _z_ vs _R_ and _V_ _z_
vs _ω_ maps, they cover several km s _[−]_ [1] .


Repeating the same analysis for the blue-shifted hemisphere, we obtain the result

illustrated in the lower row of Figure 13. The main difference with the red-shifted

hemisphere is a lower intensity, by _∼_ 33%, dominated by an important depression in

EP Aquarii: a new picture of the circumstellar envelope 19


a b c d


Fig. 12: Radial distributions (combined data), shown separately in the blue-shifted and

red-shifted hemispheres, for the SiO(5-4) emission (a and b) and CO(2-1) emission (c

and d) integrated over position angle and over Doppler velocity intervals as indicated

in the inserts.


Fig. 13: SiO(5-4) emission (combined data) in the red-shifted (upper row) and blue
shifted (lower row) hemispheres and the radial interval 0.5 _<R<_ 2.3 arcsec. From left
to right: Doppler velocity spectrum, _S_ ( _V_ _z_ ); radial distribution, _U_ ( _R_ ); ratio of the observed intensity to _U_ ( _R_ ) _× S_ ( _V_ _z_ ), properly normalized, in the _x_ vs _y_, _V_ _z_ vs _R_ and _V_ _z_

vs _ω_ planes, respectively.


the western quadrant causing a deviation twice as large with respect to the smooth dis
tribution. If it were not for this depression, in the approximation of neglecting fluctua
tions at the level of _±_ 20%, both hemispheres would reveal similar morpho-kinematics,

which could be described by a simple nearly spherical model as previously remarked

by Homan et al. (2020a). It is therefore important to study it in detail, which we do in

the following sub-section.


Channel maps of the SiO(5-4) line emission are shown as supplementary material

(Figure S3). Also shown are PV maps in the _V_ _z_ vs _R_ plane (Figure S4) and in the _V_ _z_

vs _ω_ plane (Figure S5), which display episodic and lumpy emission.

20 Nhung P.T., Hoai D.T., Darriulat P. et al.


**4.3** **SiO(5-4) emission in the close neighbourhood of the star**


Qualitatively, the upper and lower rows of Figure 13 display some similarities: below

_R∼_ 1 arcsec, they both show enhanced emission in the polar outflows, at _V_ _z_ _∼_ 7 and
_−_ 5 km s _[−]_ [1], respectively, the former covering the southern quadrant and the latter cov
ering a broader interval of position angles, somewhat enhanced in the north-eastern

hemisphere. In contrast, beyond _R∼_ 1 arcsec, emission is enhanced near the EDE.


Figure 14 displays _V_ _z_ vs _ω_ maps of SiO(5-4) emission in 100 mas wide rings cen
tred on the star, in the same format as was shown for CO(2-1) emission in Figure 4.

Comparing the TM0 and combined data images, and accounting for the different an
gular resolutions, they clearly reveal the presence in the red-shifted hemisphere of an

outflow covering the southern quadrant and of a depression covering the northern quad
rant. The picture is less clear in the blue-shifted hemisphere where enhanced emission

is seen to cover velocity and position angle values closer to those displayed by the disc,

while the western void shows up clearly in both TM0 and combined data images.


While qualitative similarities between both outflows and associated voids are re
markable, as clearly illustrated in Figure 15, important differences must be noted: i)

the western blue-shifted depression of SiO(5-4) emission is stronger than the northern

red-shifted one, with a peak-to-valley ratio of _∼_ 6 compared with _∼_ 3; ii) the north
ern SiO(5-4) depression starts earlier than the western one and is already present in

the interval 0.1 _<R<_ 0.2 arcsec where the western depression is not only absent but

even partly replaced by a clear enhancement; iii) the southern outflow, covering large

Doppler velocities, is emitted in the red-shifted hemisphere close to the line of sight

while the blue-shifted outflow, covering small Doppler velocities, is likely to interact

with the nascent EDE in the equatorial plane. Indeed, Figure 16 shows that the CO(2
1) emission of the EDE displays a western void of emission clearly associated with the

edge of the blue-shifted void of SiO(5-4) emission, as had been previously remarked

by Homan et al. (2020a).


These observations underscore the complexity of the dynamics at stake and suggest

that the interaction between the blue-shifted outflow and the nascent EDE may play an

important role. Particularly puzzling are the properties displayed by the blue-shifted

western void of SiO(5-4) emission.


In order to explore these in more detail, we take advantage of its confinement to a

relatively narrow interval of position angle, 240 _[◦]_ _<_ _ω_ _<_ 300 _[◦]_ to study the distributions

of the CO and SiO line emissions in the _V_ _z_ vs _R_ plane, integrated over _ω_, which are

displayed in the left pair of panels of Figure 17. Both give evidence for a mass ejection

EP Aquarii: a new picture of the circumstellar envelope 21


Fig. 14: SiO(5-4) TM0 (upper row) and combined (lower row) data. _V_ _z_ vs _ω_ maps in

100 mas wide rings as indicated on top of each panel. Note that the _ω_ axis is offset by

90 _[◦]_ . A triangle and an ellipse, corresponding approximately to the location of the voids
of emission, are shown as reference in all panels. The colour scale is in mJy beam _[−]_ [1] .


Fig. 15: SiO(5-4) intensity maps integrated over _−_ 6 _<V_ _z_ _<−_ 3 km s _[−]_ [1] for the left pair of
panels and over 5 _<V_ _z_ _<_ 9 km s _[−]_ [1] for the right pair of panels. The intensity is multiplied

by _R_ /0.1 for _R>_ 0.1 arcsec. In each pair, TM0 data are shown left and combined data

are shown right.


in the form of a shell having a mean radius between 0.5 and 1 arcsec and a mean radial
velocity between 5 and 10 km s _[−]_ [1] . The void of emission, for both SiO and CO lines,

is clearly seen in its wake, suggesting that it simply results from the radial velocity

of the shell significantly exceeding that of the wind that followed it. As a distance

of 1 arcsec is covered in the plane of the sky in _∼_ 60 years at a velocity of 10 km
s _[−]_ [1], the mass ejection occurred a few decades ago. We note that the distribution of

the CO line emission suggests the presence of an earlier mass ejection that had taken

place again a few decades before the more recent one. It is not expected to be visible

on the distribution of SiO line emission as the density of SiO gas has significantly

decreased at the corresponding radial distance. In line with the interpretation given at

22 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. 16: EDE region, combined data. CO(2-1) (upper row) and SiO(5-4) (lower row)

emissions: channel maps centred at the Doppler velocities indicated on top of each

panel.


Fig. 17: Distributions of the line emission of SiO(5-4) and CO(2-1) over the _V_ _z_ vs

_R_ plane, integrated over position angles in the interval 240 _[◦]_ _<_ _ω_ _<_ 300 _[◦]_ (left pair of

panels) and 280 _[◦]_ _<_ _ω_ _<_ 360 _[◦]_ (right pair of panels). In each pair of panels SiO is left

and CO is right.


the end of Section 4.1 of the patterns observed in the CO line emission of the polar

outflows, Figure 17 suggests the occurrence of mass ejections triggered by pulsations

of amplitudes enhanced both episodically, with a time scale of a few decades, and

in solid angle, at the scale of a steradian corresponding to the presence of a large

convective cell. The angular resolution of the present observations cannot resolve the

fine time structure associated with the pulsation period, _∼_ 110 days.


A significant difference between the distributions of SiO and CO line emissions

displayed in Figure 17 is the evidence for SiO emission to have resumed after the mass

ejection, covering some 100 to 200 mas from the centre of the star, while CO emission

has not. Indeed, we saw in Figure 3 that close to the star and in the Doppler velocity

EP Aquarii: a new picture of the circumstellar envelope 23


interval _−_ 3 _< V_ _z_ _<_ 0 km s _[−]_ [1] CO line emission is instead enhanced in the north-eastern

quadrant. In contrast, we saw from Figure 6 that in the same region of the data-cube,

SiO emission covers the whole range of position angles. Understanding the reason

for such a difference would require understanding the mechanism that governs the

formation of the equatorial disc as well as observations of higher sensitivity and of

other line emissions, both of which are lacking. We note that the ejected shell covers

latitudes reaching down to the disc, implying that it interacts with it, making it even

more difficult to provide a reliable interpretation of the mechanism at stake.


With the aim of exploring the properties of the northern depression, we repeated the

analysis made for the western void in the interval of position angles 280 _[◦]_ _<_ _ω_ _<_ 360 _[◦]_ .

The result is illustrated in the right pair of panels of Figure 17. Here again, in the range
of large Doppler velocities, _V_ _z_ _>_ 7 km s _[−]_ [1], the depression is seen in the wake of a

shell-like enhancement of emission, much clearer on the CO distribution than it is on

the SiO distribution, and an earlier shell is clearly visible on the CO distribution. Also,

as for the western void, SiO line emission is seen to have resumed close to the star

after the mass ejection, but CO line emission has not. The features displayed by the

northern depression are qualitatively similar, but much less clear, than they are by the

western void.


While appealing, the interpretation of the western void proposed in the present sec
tion leaves a number of questions unanswered, in particular concerning the mechanism

responsible for the formation of the equatorial disc. The complexity of the observed

features prevents claiming its validity and unicity with strong confidence. But it ques
tions the validity of the interpretation proposed by Homan et al. (2020a) in terms of

photo-dissociation by a white dwarf companion: such a companion should have _V_ _z_

close to zero, like the disc that it is meant to have produced, and should irradiate both

the blue-shifted and red-shifted hemispheres. Additional observations of high sensitiv
ity and angular resolution, also including other line emissions, are required in order to

ascertain the validity of either of the two scenarios.


Additional figures of relevance to the description of the region of the western de
pression are displayed in Figures S7 to S9 of the supplementary material.


**4.4** **SiO(5-4) emission: patterns of enhanced emission**


In order to compare CO(2-1) and SiO(5-4) line emissions, we must limit the radial

range and compensate for the different radial declines. In practice, we consider the

ring 0.7 _<R<_ 2.0 arcsec, also excluding the western sextant 240 _[◦]_ _<ω<_ 300 _[◦]_ in the blue

24 Nhung P.T., Hoai D.T., Darriulat P. et al.


shifted hemisphere, and divide the observed intensity by a fit of the _R_ distribution to
a form _AR_ _[b]_ as was done in Section 4.1. Examples of the resulting maps are shown in

Figure 18, one in the blue-shifted hemisphere, with _b_ = _−_ 0.20 for CO(2-1) and _−_ 1.52

for SiO(5-4), and the other in the red-shifted hemisphere, with _b_ = _−_ 0.76 for CO(2-1)

and _−_ 1.20 for SiO(5-4). The normalised brightness have a mean of unity by con
struction and an rms width that provides a measure of the intensity contrast, larger

for CO(2-1) than for SiO(5-4): 0.30 and 0.31 for the former, 0.15 and 0.22 for the

latter, in the red-shifted and blue-shifted hemispheres, respectively. The correlation

between the CO(2-1) and SiO(5-4) normalised maps is illustrated in Figure 18 by plot
ting, for each pixel, the intensity of the latter vs that of the former. A fit of the form
_F_ norm (SiO)= _F_ 0 + _G_ 0 _×F_ norm (CO) gives a normalised _χ_ [2], with the values of ~~√~~ _χ_ [2] in the

examples shown in Figure 18 being 0.14 and 0.21, in the red- and blue-shifted hemi
spheres, respectively; the value of _G_ 0, which measures the strength of the correlation,

is 0.18 in both hemispheres. The pair of examples displayed in Figure 18 calls for a

number of remarks of general validity: the maps of CO(2-1) and SiO(5-4) line emis
sions display more similarities in the red-shifted hemisphere than in the blue-shifted

hemisphere; small enhancements of emission are seen on both maps, less contrasted

on the SiO map than on the CO map; some are common to both maps, others are seen
on only one of the two maps; in contrast to the higher _|V_ _z_ _|_ range illustrated in Figure

10, clear arcs are rarely observed.


**5** **HIGH DOPPLER VELOCITIES**


For a detailed study of the neighbourhood of the star and of the nature of the high

velocity wings, we use the high resolution TM0 data in the form of Doppler veloc
ity spectra of SiO(5-4) emission, integrated in 20 mas broad annular rings centred

on the star with mean radii increasing from 10 mas to 390 mas in steps of 20 mas.

On each of these we define values of the full width measured at 10% of maximum,

FWTM, as sketched in Figure 19a. This choice of 10% is a compromise between min
imizing systematic uncertainties and staying well above noise and its precise value is

of no relevance to the validity of the result. The dependence of FWTM on _R_ gives

evidence for confinement within some 200 mas (Figure 19b). It is well described by
a fit of the form 21.3+19.0 exp( _−R_ /0.10) km s _[−]_ [1] . The first term corresponds to the

velocity range covered by the bulk of the CSE, the second term to a region of high

velocities just above the photosphere, as observed in other oxygen-rich AGB stars, and

commonly interpreted as resulting from shock waves produced by the interaction of

stellar pulsation and convective cell partition (see for example Hoai et al. (2020) and

EP Aquarii: a new picture of the circumstellar envelope 25


~~a~~ ~~b~~ c d ~~e~~


f g h i ~~j~~


Fig. 18: Comparing CO(2-1) and SiO(5-4) emissions (combined data) in the polar out
flows: two examples (in the red-shifted hemisphere, upper row and in the blue-shifted

hemisphere, lower row). Left pair of panels: normalized channel maps for _V_ _z_ =3.6 km
s _[−]_ [1] and _V_ _z_ = _−_ 3.5 km s _[−]_ [1] . We have circled in black some features common to both the

CO and SiO maps and in red others that are seen in only one of the two maps. Central

panels: normalized _R_ and _ω_ distributions for CO(2-1) (black) and SiO(5-4) (red), re
spectively. Right: correlation between the normalised brightness of the two lines; the

line is the best fit result (see text).


Nhung et al. (2022)). We also estimate the maximal Doppler velocity _V_ max, reached

in the red-shifted hemisphere by the bulk of the expanding CSE, by extrapolating the

upper end of the spectrum down to continuum level (essentially zero) using the com
bined data. The dependence of _V_ _max_ on _R_ and _ω_ is well described by a fit of the form

_V_ max =(1.13 _−_ 0.11 _R_ ) _×_ [11.1+0.8 sin( _ω−_ 71 _[◦]_ )]. The rms deviation between data and fit
is 0.36 km s _[−]_ [1] . Panels c and d of Figure 19 compare these two factors to the measured

mean values of _V_ max, averaged over _ω_ and _R_, respectively. The dependence on _ω_ cor
responds well to what is expected from the tilt of the CSE axis, pointing _∼_ 20 _[◦]_ east of

south in the red hemisphere.

This analysis gives therefore evidence for two major contributions to the high ve
locity wings of the SiO(5-4) Doppler velocity spectrum: one, extending up to some
12 km s _[−]_ [1], is simply the upper edge of the velocity distribution of the polar outflows;
the other, reaching up to 20 km s _[−]_ [1], is confined to the close neighbourhood of the star

and corresponds to what is observed in most other oxygen-rich AGB stars where this

region of the CSE has been carefully explored. The interpretation given by Tuan-Anh

et al. (2019) of these high velocity wings, using data of lower angular resolution, was

mixing both contributions. This is clearly illustrated in Figure 20, which displays PV

26 Nhung P.T., Hoai D.T., Darriulat P. et al.


maps of _|V_ _z_ _|_ vs _R_ for both line emissions and both hemispheres separately. In all four

cases there is evidence for a clear separation between the two contributions, even if

significant differences exist between the CO(2-1) and SiO(5-4) lines as well as be
tween the red-shifted and blue-shifted hemispheres. Another illustration is given by
the intensity maps displayed in the left pair of panels of Figure 21 for 8 _<|V_ _z_ _|<_ 12 km
s _[−]_ [1] (combined data) and in the right pair of panels of the same figure for 12 _<|V_ _z_ _|<_ 20
km s _[−]_ [1] (TM0 data). The former give evidence for the above-mentioned asymmetry be
tween blue-shifted and red-shifted hemispheres along the projection of the CSE axis,

while the latter display instead a small elongation in the perpendicular direction where

they are better distinguishable from the bulk. This latter high _V_ _z_ component seems

however different from what we know of other stars by the absence of red-shifted ab
sorption, usually interpreted as evidence for in-falling gas, over the stellar disc (Figure

22). Unfortunately, the lack of reliable light curve measurements prevents commenting

on a possible relation with the stellar phase at the time of observations.


**6** **SUMMARY AND DISCUSSION**


Collecting the information obtained in both the present work and earlier publications to

draw a credible picture of the morpho-kinematics of the CSE of EP Aquarii is challeng
ing. The interpretation given by Homan et al. (2020a), giving a major role to a white

dwarf companion currently located at _∼_ 400 mas west of the star, has been shown to

be not unique and, accordingly, to be less reliable than previously thought, by the re
sults of the analyses made in the present work: the evidence for a spiral enhancement

of CO(2-1) emission and the interpretation of the lumps of CO(2-1) emission in the

neighbourhood of the star illustrated in Figure A12 of Homan et al. (2020a) have been

shown to become invalid when considering a slightly broader Doppler velocity inter
val. The detailed study of the blue-shifted western depression of SiO(5-4) emission

presented in Section 4.3 failed to support an interpretation in terms of dissociation by

UV radiation from a white dwarf companion. This does not mean that one can exclude

the presence of a companion and its possible role in shaping the CSE. In particular,

there is no reason to doubt that EP Aquarii, as most other stars, has several planets

orbiting it, some of which may already have been engulfed. But the complexity of the

observed morpho-kinematics, and the resulting difficulty to give a reliable interpreta
tion of its many features, prevent claiming a credible model of the mechanisms at stake

with sufficient confidence.

In general, the global morpho-kinematics of CO(2-1) emission observed in the

present work confirms the results of earlier analyses. The evidence for approximate

EP Aquarii: a new picture of the circumstellar envelope 27


a b c d


Fig. 19: (a): definition of the quantity FWTM (see text) taking as example the Doppler

velocity spectrum of SiO(5-4) line emission measured in the ring 60 _<R<_ 80 mas (see

Figure S6 of the supplementary material). The blue line is used to extrapolate the

spectrum (using a linear ordinate scale), its intersection with continuum level defin
ing _V_ max (see text). (b): dependence of FWTM on the ring radius, _R_ . The line is a fit

_−_
21.3+19.0 exp( _R_ /0.10) km s _[−]_ [1] . (c): comparison between the measured dependence
on _R_ of the mean value of _V_ max and the best fit _F_ ( _R_ )=(1.13 _−_ 0.11 _R_ ). (d): compari
son between the measured dependence on _ω_ of the mean value of _V_ max and the best fit
_V_ 0 ( _ω_ )=[11.1+0.8 sin( _ω−_ 71 _[◦]_ )].


Fig. 20: High Doppler velocities (combined data): PV maps of _|V_ _z_ _|_ vs _R_ for both hemi
spheres and both lines separately, as indicated on top of each panel.


axi-symmetry about an axis making an angle of _∼_ 10 _[◦]_ with the line of sight and pro
jecting _∼_ 20 _[◦]_ west of north on the plane of the sky has been strengthened by observa
tions of both the EDE and polar outflows. The latitudinal dependence of the expansion
velocity, evolving from _∼_ 2 km s _[−]_ [1] to _∼_ 10 km s _[−]_ [1] from equator to poles, has been

shown to imply a sin _[n]_ _α_ term with _n_ smaller than unity, in contrast with the assump
tion of _n_ =2 made by Hoai et al. (2019) (Section 4.1). Evidence for enhancements of

emission with a typical peak-to-valley ratio below a factor 2, has been found in both

EDE and polar outflows, as well as in both CO(2-1) and SiO(5-4) line emissions, often,

but not always, in coincidence. Their morphology in the CO line emission of the polar

28 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. 21: Left: intensity maps of the SiO(5-4) emission (combined data) measured in the
Doppler velocity intervals 8 _<|V_ _z_ _|<_ 12 km s _[−]_ [1] . Right: intensity maps of the SiO(5-4)
emission (TM0 data) measured in the Doppler velocity intervals 12 _<|V_ _z_ _|<_ 20 km s _[−]_ [1] .


Fig. 22: Doppler velocity spectra of SiO(5-4) (upper panels) and CO(2-1) (lower pan
els) line emissions (TM0 data) integrated in rings as indicated on top of the upper

panels.


outflows, taking the form of eccentric arcs, suggests that they are caused by shells of

mass ejections covering solid angles at steradian scale.

The birth of the equatorial enhancement observed in CO(2-1) emission has been

shown to occur very close to the star, first dominated by rotation, then by expansion,

becoming particularly clear at distances exceeding _∼_ 200 mas below which important

effective line broadening and dust formation are known to be present (Section 3.1).

Lack of evidence for a similar enhancement in SiO(5-4) emission is puzzling; only

a very small enhancement is visible at distances exceeding _∼_ 300 mas (Section 3.2).

This suggests that a disc is formed at short distances from the star probably caused

by the presence or the recent engulfment of a companion (Privitera et al. 2016); but

EP Aquarii: a new picture of the circumstellar envelope 29


this is pure speculation. An intrinsic rms width of nearly 1 km s _[−]_ [1] has been found to

contribute to the EDE flaring of _∼_ 40 _[◦]_ FWHM evaluated earlier (Hoai et al. 2019).

The strong difference between the morpho-kinematics displayed by the SiO(5-4)

and CO(2-1) emissions (Section 4.2) was understood as being largely due to the differ
ent radial ranges being explored, the former declining rapidly as a result of accretion by

dust grains and dissociation by the interstellar UV radiation. In a first approximation,

SiO(5-4) emission can qualitatively be described by the standard mass-loss mechanism

at play in other oxygen-rich AGB stars (H¨ofner & Freytag 2019), with a typical terminal radial expansion velocity at the scale of 10 km s _[−]_ [1] and some prolateness caused by

the presence of the EDE.

Indeed, a careful inspection of the morpho-kinematics of the SiO(5-4) line emis
sion in the close neighbourhood of the star has revealed the presence of two distinct

broad outflows hosting episodic mass ejections at a time scale of a few decades, cover
ing solid angles at steradian scale, probably associated with shock waves and leaving

a depression in their wake: if it were not for the presence of the EDE, the morpho
kinematics of the CSE could be understood as resulting from the standard mecha
nism of wind generation described by current state-of-the- art hydrodynamical models

(Freytag & H¨ofner 2023). However, the presence of the EDE causes the CSE to take

the form of two polar outflows having an increasing radial velocity, and an accordingly

decreasing density, when spanning from the equator to the poles.

Such a model, suggested by the results of the present analyses, is at significant

variance with that proposed by Homan et al. (2020a). However, in order to claim its

superiority, we would need to understand the details of what precisely causes the pro
gressive disappearance of SiO molecules, of what governs the morpho-kinematics of

the EDE, of what kind of dust takes part in the acceleration process, of what are the

relative roles of stellar pulsation and convective cell partition in giving the initial boost

to the wind, of which kind of pattern of shock waves is present.

Only then could one decide with confidence which of the two models is closer

to reality. In the present stage, we need additional ALMA observations of high an
gular resolution and sensitivity to tell them apart. Particularly informative would be

observations of the emission of molecular lines that probe preferentially the very close

environment of the star, such as from vibrational excited states. New infrared observa
tions of the dust, together with simultaneous monitoring of the light curve, are required

to possibly reveal correlation with the stellar phase.
Finally, the presence of high velocity wings, extending up to _∼_ 20 km s _[−]_ [1], pre
viously noted in earlier work, has been confirmed and shown to include two distinct

30 Nhung P.T., Hoai D.T., Darriulat P. et al.


components (Section 5): upper velocity ends of the polar winds, reaching typically 12
km s _[−]_ [1] but with weak tails reaching well above; and effective line broadening confined

to distances shorter than 200 mas from the centre of the star. The earlier interpretation

given by Tuan-Anh et al. (2019), was failing to make the distinction between these

two components. The observed line broadening, consistent with similar observations

in all other low mass-loss rate oxygen-rich AGB stars observed with sufficient angu
lar resolution and sensitivity, is believed to be due to lumpy emission of shock waves

associated with convective cell partition and stellar pulsation, but a detailed picture

is lacking. In general, presently available observations do not allow for telling apart,

in the close neighbourhood of the star, the contributions of pulsations, convective cell

partition, EDE formation, and dust condensation. EP Aquarii is clearly a star from

which one should learn more than currently feasible; it deserves being studied in as

many details as possible with state-of-the-art instruments; it still leaves us with many

open questions, the answers to which would be of great help to improve our under
standing of the mechanisms at stake in the generation and development of the wind of

oxygen-rich AGB stars.


**Acknowledgements** We thank Dr Ward Homan and Dr Anita Richards for clar
ifications concerning their earlier work and for sharing with us their understand
ing of the morpho-kinematics of EP Aquarii. We also thank Dr. Stefan Uttenthaler

for discussion related to the properties of the CSE. We thank the anonymous

referee for comments which helped with improving the presentation. This paper

makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00057.S and

ADS/JAO.ALMA#2018.1.00750.S. ALMA is a partnership of ESO (representing its

member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST

and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic

of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

We are deeply indebted to the ALMA partnership, whose open access policy means in
valuable support and encouragement for Vietnamese astrophysics. The combined data

are obtained from Homan et al. (2020a) via the CDS (http://cdsarc.u-strasbg.fr/viz
bin/cat/J/A+A/642/A93). Financial support from the World Laboratory, the Odon

Vallet Foundation and the Vietnam National Space Center is gratefully acknowl
edged. This research is funded by the Vietnam National Foundation for Science and

Technology Development (NAFOSTED) under grant number 103.99-2019.368.


**References**


Bujarrabal, V., Ag´undez, M., G´omez-Garrido, M., et al. 2021, A&A, 651, A4

EP Aquarii: a new picture of the circumstellar envelope 31


Castellanos-Ram´ırez, A., Rodr´ıguez-Gonz´alez, A., Meliani, Z., et al. 2021, MNRAS,

507, 4044


Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2017, A&A, 605, A28


Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2020, A&A, 633, A13


Dumm, T., & Schild, H. 1998, New Astron., 3, 137


Eggen, O. J. 1973, MmRAS, 77, 159


Freytag, B., & H¨ofner, S. 2023, A&A, 669, A155 and references therein


Gaia Collaboration. 2018, VizieR Online Data Catalog, I/345


Garc´ıa-Segura, G., L´opez, J. A., & Franco, J. 2005, ApJ, 618, 919


Heras, A. M., & Hony, S. 2005, A&A, 439, 171


Hoai, D. T., Tuan-Anh, P., Nhung, P. T., et al. 2020, MNRAS, 495, 943


Hoai, D. T., Nhung, P. T., Tuan-Anh, P., et al. 2019, MNRAS, 484, 1865


H¨ofner, S., & Freytag, B. 2019, A&A, 623, A158


Homan, W., Cannon, E., Montarg`es, M., et al. 2020a, A&A, 642, A93


Homan, W., Richards, A., Decin, L., de Koter, A., & Kervella, P. 2018, A&A, 616,

A34


Homan, W., Montarg`es, M., Pimpanuwat, B., et al. 2020b, A&A, 644, A61


Lebzelter, T., & Hron, J. 1999, A&A, 351, 533


Liimets, T., Corradi, R. L. M., Jones, D., et al. 2018, A&A, 612, A118


Melnikov, S., Stute, M., & Eisl¨offel, J. 2018, A&A, 612, A77


Nhung, P. T., Hoai, D. T., Tuan-Anh, P., et al. 2022, ApJ, 927, 169


Nordhaus, J., & Blackman, E. G. 2006, MNRAS, 370, 2004


Olofsson, H., Khouri, T., Maercker, M., et al. 2019, A&A, 623, A153


Privitera, G., Meynet, G., Eggenberger, P., et al. 2016, A&A, 593, A128

32 Nhung P.T., Hoai D.T., Darriulat P. et al.


Sahai, R., Huang, P. S., Scibelli, S., et al. 2022, ApJ, 929, 59


Tabur, V., Bedding, T. R., Kiss, L. L., et al. 2009, MNRAS, 400, 1945


Tuan-Anh, P., Hoai, D. T., Nhung, P. T., et al. 2019, MNRAS, 487, 622


van Leeuwen, F. 2007, Astrophysics and Space Science Library, Vol. 350, Hipparcos,

the New Reduction of the Raw Data (Springer Science+Business Media B.V.)


Winters, J. M., Hoai, D. T., Wong, K. T., et al. 2022, A&A, 658, A135


**Appendix A:**

EP Aquarii: a new picture of the circumstellar envelope 33


Fig. A1: Channel maps of CO(2-1) emission (combined data). Central Doppler velocities (km s _[−]_ [1] ) are indicated for each channel on the upper-left corner of the panel.

34 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. A2: Channel maps of CO(2-1) emission (combined data) in the _ω_ vs _R_ plane.
Central Doppler velocities (km s _[−]_ [1] ) are indicated for each channel on top of the panel.

EP Aquarii: a new picture of the circumstellar envelope 35


Fig. A3: Projections of the data cube of CO(2-1) emission (combined data) in 36 inter
vals of _ω_ (the central value in degree is indicated on top of each panel) on the _V_ _z_ vs _R_
plane ( _|V_ _z_ _|<_ 8 km s _[−]_ [1], 1.2 _<R<_ 5.2 arcsec).

36 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. A4: Projections of the data cube of CO(2-1) emission (combined data) in 40 inter
vals of _R_ (the central value in arcsec is indicated on top of each panel) on the _V_ _z_ vs _ω_
plane ( _|V_ _z_ _|<_ 8 km s _[−]_ [1], 0 _<ω<_ 360 _[◦]_ ).

EP Aquarii: a new picture of the circumstellar envelope 37


**SUPPLEMENTARY MATERIAL**


Fig. S1: Channel maps of the SiO(5-4) line emission (combined data). Brightness is
multiplied by _R_ . Central Doppler velocities (km s _[−]_ [1] ) are indicated for each channel on

top of the panel.

38 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. S2: SiO(5-4) emission (combined data): _V_ _z_ vs _R_ maps in 12 intervals of position

angle _ω_ as indicated on top of each panel. Ellipses corresponding to spherical shells
having radius of 1, 2 and 3 arcsec expanding at uniform radial velocity of 7 km s _[−]_ [1] are

shown as references.


Fig. S3: SiO(5-4) emission (combined data): _V_ _z_ vs _ω_ maps in 12 intervals of _R_ (arcsec)

as indicated on top of each panel.

EP Aquarii: a new picture of the circumstellar envelope 39


1 2 3 4 5 6 7


8 9 10 11 12 13 14


15 16 17 18 19 20


Fig. S4: Doppler velocity spectra of SiO(5-4) line emission (TM0 data). Spectra are

integrated in 4 quadrants (north (black), east (blue), south (green) and west (red)) of

20 rings, each 20 mas wide with mean radii increasing from 10 mas (panel 1) to 390

mas (panel 20).


Fig. S5: SiO(5-4) emission, TM0 data. _V_ _z_ vs _R_ maps in twelve 30 _[◦]_ wide sectors of _ω_

with _ω_ increasing from upper-left to lower-right panels.

40 Nhung P.T., Hoai D.T., Darriulat P. et al.


Fig. S6: Channel maps of combined SiO(5-4) data relevant to the region of western

depression. The lower row is a zoom of the upper row.


Fig. S7: SiO(5-4) emission, combined data. Projections of the data cube volume defined as 0.2 _<R<_ 0.7 arcsec, 240 _[◦]_ _<ω<_ 300 _[◦]_, _−_ 7 _<V_ _z_ _<−_ 1 km s _[−]_ [1] .


</paper>

## Items to check

```json
[
 {
  "path": "data.arrays.evidence[0]",
  "value": "ACA, 12m array (~46 antennas in 2019)",
  "failed_quote": "70 min (ACA) 230 min (TM1,2)"
 },
 {
  "path": "data.configurations.evidence[0]",
  "value": "ACA, TM1, TM2 (2016); hybrid C43-10 and C43-9 (TM0, 2019)",
  "failed_quote": "70 min (ACA) 230 min (TM1,2)"
 },
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "2016: 170 x 150 mas^2; Combined: 87 x 79 mas^2 (CO(2-1)), 85 x 79 mas^2 (SiO(5-4)); TM0: 31.7 x 28.0 mas^2 (CO(2-1)), 32.4 x 30.0 mas^2 (SiO(5-4))",
  "failed_quote": "87 × 79 +15 ∼ 0.33 − 0.65 15 SiO(5-4) 85 × 79 +7"
 },
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "15 arcsec (2016 and combined); 0.5 arcsec / 0.46 arcsec nominal (TM0 2019)",
  "failed_quote": "Maximal Recoverable Scale (”) 15 15 0.5 0.5"
 },
 {
  "path": "data.max_recoverable_scale.evidence[1]",
  "value": "15 arcsec (2016 and combined); 0.5 arcsec / 0.46 arcsec nominal (TM0 2019)",
  "failed_quote": "While the nominal maximal maximal recoverable scale (MRS) corresponding to the C43-10 antenna configuration is 0.46 arcsec, the impact on imaging of the lack of short spacing cannot be simply measured by a single number."
 },
 {
  "path": "data.sensitivity.evidence[1]",
  "value": "1.25 mJy beam^-1 (2016); 0.65 mJy beam^-1 (Combined); 1.0 mJy beam^-1 (TM0 CO(2-1)), 1.34 mJy beam^-1 (TM0 SiO(5-4))",
  "failed_quote": "Noise rms (mJy beam − 1 ) 1.25 0.65 1.0 1.34"
 },
 {
  "path": "data.time_on_source.evidence[0]",
  "value": "2016: 70 min (ACA), 230 min (TM1,2); 2019 (TM0): 99 min",
  "failed_quote": "70 min (ACA) 230 min (TM1,2)"
 },
 {
  "path": "processing.calibration.archive_products_used_as_is.evidence[0]",
  "value": "Combined data cubes from Homan et al. (2020a) used via CDS; TM0 data reduced separately by the authors",
  "failed_quote": "In the present article, in order to better understand their contribution to the combined data, we reduced them separately and report about the results in the present section."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "Natural weighting (TM0 data)",
  "failed_quote": "Natural weighting was used for cleaning, producing maps of 2000 × 2000 pixels covering ± 4 arcsec in both x (pointing east) and y (pointing north)"
 },
 {
  "path": "processing.imaging.cell_size.evidence[0]",
  "value": "4 mas (implied by 2000 x 2000 pixels covering ±4 arcsec)",
  "failed_quote": "Natural weighting was used for cleaning, producing maps of 2000 × 2000 pixels covering ± 4 arcsec in both x (pointing east) and y (pointing north)"
 },
 {
  "path": "processing.imaging.image_size.evidence[0]",
  "value": "2000 x 2000 pixels covering ±4 arcsec in x and y",
  "failed_quote": "Natural weighting was used for cleaning, producing maps of 2000 × 2000 pixels covering ± 4 arcsec in both x (pointing east) and y (pointing north)"
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "TM0: 31.7 x 28.0 mas^2, PA +13 deg (CO(2-1)); 32.4 x 30.0 mas^2, PA +22 deg (SiO(5-4)). Combined: 87 x 79 mas^2, PA +15 deg (CO(2-1)); 85 x 79 mas^2, PA +7 deg (SiO(5-4)). 2016: 170 x 150 mas^2, PA -34 deg",
  "failed_quote": "Beam size (mas 2 ) Beam PA ( ◦ ) 170 × 150 − 34 87 × 79 +15 85 × 79 +7 32 × 28 +13 32 × 30 +22"
 },
 {
  "path": "processing.imaging.final_rms.evidence[1]",
  "value": "TM0: 1.0 mJy beam^-1 (CO(2-1)), 1.34 mJy beam^-1 (SiO(5-4)); Combined: 0.65 mJy beam^-1; 2016: 1.25 mJy beam^-1",
  "failed_quote": "Noise rms (mJy beam − 1 ) 1.25 0.65 1.0 1.34"
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Merge June 5 and June 14, 2019 observations with equal weights, group into velocity channels, and clean using natural weighting with circular masks without continuum subtraction or self-calibration.",
  "failed_quote": "Natural weighting was used for cleaning, producing maps of 2000 × 2000 pixels covering ± 4 arcsec in both x (pointing east) and y (pointing north)"
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "Image size: 2000 x 2000 pixels covering ±4 arcsec; natural weighting",
  "failed_quote": "Natural weighting was used for cleaning, producing maps of 2000 × 2000 pixels covering ± 4 arcsec in both x (pointing east) and y (pointing north)"
 },
 {
  "path": "analysis_steps[0].validation.evidence[1]",
  "value": "Compared TM0 images with combined data cubes and modelled discs of various sizes to evaluate short-spacing flux loss and distortion beyond ~0.6-0.7 arcsec; tested different mask sizes and self-calibration.",
  "failed_quote": "While the decline of detected flux starts well below the nominal MRS, important distortions appear only beyond ∼ 0.6-0.7 arcsec."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Compare observed SiO(5-4) intensity in 0.5 < R < 2.3 arcsec to the smooth normalized product U(R) x S(Vz) in red and blue hemispheres; construct Vz vs omega maps in 100 mas inner rings and Vz vs R maps integrated over 240 deg < omega < 300 deg (western void) and 280 deg < omega < 360 deg (northern void) for both SiO and CO; normalize brightness by power-law fits A*R^b in 0.7 < R < 2.0 arcsec (excl",
  "failed_quote": "In practice, we consider the ring 0.7 <R< 2.0 arcsec, also excluding the western sextant 240 ◦ <ω< 300 ◦ in the blue-shifted hemisphere, and divide the observed intensity by a fit of the R distribution to a form AR b as was done in Section 4.1."
 },
 {
  "path": "analysis_steps[3].key_parameters[2].evidence[0]",
  "value": "Correlation region: 0.7 < R < 2.0 arcsec (excluding 240 deg < omega < 300 deg in blue-shifted hemisphere)",
  "failed_quote": "In practice, we consider the ring 0.7 <R< 2.0 arcsec, also excluding the western sextant 240 ◦ <ω< 300 ◦ in the blue-shifted hemisphere"
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "EDE inner detection radius in CO(2-1) = 100-200 mas",
  "failed_quote": "They show that the EDE is already present in the smaller ring, R between 100 and 200 mas, and its kinematics is dominated by rotation at a few km s − 1 scale."
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "SiO(5-4) blue-shifted hemisphere intensity reduction relative to red-shifted hemisphere = 33 %",
  "failed_quote": "The main difference with the red-shifted hemisphere is a lower intensity, by ∼ 33%, dominated by an important depression in the western quadrant"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Mean radius of ejected shell ahead of western void = 0.5-1 arcsec",
  "failed_quote": "Both give evidence for a mass ejection in the form of a shell having a mean radius between 0.5 and 1 arcsec and a mean radial velocity between 5 and 10 km s − 1 ."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Mean radial velocity of ejected shell ahead of western void = 5-10 km s^-1",
  "failed_quote": "Both give evidence for a mass ejection in the form of a shell having a mean radius between 0.5 and 1 arcsec and a mean radial velocity between 5 and 10 km s − 1 ."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The Equatorial Density Enhancement (EDE) is already formed within 100-200 mas of the star, where its kinematics is dominated by rotation (~few km s^-1) before transitioning to slow radial expansion (< 2 km s^-1) farther out.",
  "failed_quote": "They show that the EDE is already present in the smaller ring, R between 100 and 200 mas, and its kinematics is dominated by rotation at a few km s − 1 scale."
 },
 {
  "path": "findings_qualitative[0].evidence[1]",
  "value": "The Equatorial Density Enhancement (EDE) is already formed within 100-200 mas of the star, where its kinematics is dominated by rotation (~few km s^-1) before transitioning to slow radial expansion (< 2 km s^-1) farther out.",
  "failed_quote": "evidence has been obtained for rotation in the central region evolving to radial expansion at a low rate of less than 2 km s − 1 beyond a fraction of an arcsec from the centre of the star."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "The western blue-shifted depression in SiO(5-4) (and a weaker northern red-shifted depression) lies in the wake of a faster-moving shell of ejected gas (R ~ 0.5-1 arcsec, V ~ 5-10 km s^-1) launched a few decades ago, rather than being caused by UV dissociation from a white dwarf companion.",
  "failed_quote": "Both give evidence for a mass ejection in the form of a shell having a mean radius between 0.5 and 1 arcsec and a mean radial velocity between 5 and 10 km s − 1 . The void of emission, for both SiO and CO lines, is clearly seen in its wake, suggesting that it simply results from the radial velocity of the shell significantly exceeding that of the wind that followed it."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The birth of the EDE occurs very close to the star (R < 200 mas) and the identification of a single companion-induced spiral is not robust once the EDE tilt is accounted for.",
  "failed_quote": "They show that the EDE is already present in the smaller ring, R between 100 and 200 mas, and its kinematics is dominated by rotation at a few km s − 1 scale."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "The western SiO(5-4) depression is unsupported as a white dwarf UV dissociation zone (which would also irradiate the red hemisphere) and is instead explained as a density void in the wake of a standard episodic mass ejection triggered by pulsation and convective cells.",
  "failed_quote": "Both give evidence for a mass ejection in the form of a shell having a mean radius between 0.5 and 1 arcsec and a mean radial velocity between 5 and 10 km s − 1 . The void of emission, for both SiO and CO lines, is clearly seen in its wake, suggesting that it simply results from the radial velocity of the shell significantly exceeding that of the wind that followed it."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Re-reducing the 2019 extended-configuration (TM0) observations separately—which had been down-weighted to 20% in Homan et al. (2020a)—provides ~30 mas resolution needed to probe the inner 200 mas where the EDE, rotation, and high-velocity wings originate, while the combined cubes probe the extended envelope up to 5-10 arcsec.",
  "failed_quote": "The latter observations (referred to as TM0) used an extended antenna configuration and were combined with the earlier observations of lower angular resolution by Homan et al. (2020a) with a low weight of 20% by fear of possible artefacts associated with the lack of short spacings. In the present article, in order to better understand their contribution to the combined data, we reduced them separately"
 },
 {
  "path": "reasoning.how_they_decided_enough.evidence[0]",
  "value": "Cross-checked TM0 against combined data and simulated discs to ensure TM0 analysis was restricted to R < 0.6-0.7 arcsec where short-spacing distortions are negligible, while admitting that higher sensitivity and molecular lines from vibrationally excited states are still needed to definitively distinguish between models.",
  "failed_quote": "While the decline of detected flux starts well below the nominal MRS, important distortions appear only beyond ∼ 0.6-0.7 arcsec. For the purpose of the present work, we checked carefully that whenever TM0 data were used, proper account was taken of this issue."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Lack of short baselines (< 100 m, and a 100-200 m gap on June 14) in the 2019 TM0 data reduces detected flux and introduces anisotropic distortions beyond ~0.6-0.7 arcsec.",
  "failed_quote": "While the decline of detected flux starts well below the nominal MRS, important distortions appear only beyond ∼ 0.6-0.7 arcsec."
 }
]
```
