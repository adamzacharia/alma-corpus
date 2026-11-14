# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025PASJ...77..733T\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Publications of the Astronomical Society of Japan_, 2024, **00**, 1–20


doi: 10.1093/pasj/xxx000


Advance access publication date:

## **Nuclear Stellar Disk-like Nature in the Kinematics of SiO** Maser Stars around Sagittarius A [∗]


**Masato** **T** **SUBOI** **,** **[1]** _**[,][∗]**_ **Takahiro** **T** **SUTSUMI** **,** **[2]** _**[,][∗]**_ **Ryosuke** **M** **IYAWAKI** **,** **[3]** _**[,][∗]**_ **and Makoto** **M** **IYOSHI** **[4]** _**[,][∗]**_


1 School of Science and Engineering, Meisei University, 2-1-1 Hodokubo, Hino, Tokyo 191-8506, Japan

2 National Radio Astronomy Observatory (NRAO), P. O. Box O, Socorro, NM 87801-0387, USA

3 College of Arts and Sciences, J. F. Oberlin University, Machida, Tokyo 194-0294, Japan

4 National Astronomical Observatory of Japan (NAOJ), Mitaka, Tokyo 181-8588, Japan


_∗_ E-mail: masato.tsuboi@meisei-u.ac.jp, ttsutsum@nrao.edu, miyawaki@obirin.ac.jp, makoto.miyoshi@nao.ac.jp


ORCID: 0000-0001-8185-8954, 0000-0002-4298-4461, 0000-0001-5259-4080, 0000-0002-6272-507X


**Abstract**


We present a detailed analysis of the kinematics of SiO maser stars around the center of the Milky Way, Sagittarius A _[∗]_ (Sgr A _[∗]_ ). We used


the archive data in the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line obtained by the Atacama Large Millimeter/Submillimeter Array (ALMA) in 2017


and 2021 (#2016.1.00940.S, PI Darling, J. and #2019.1.00292.S, PI Paine, J.). We detected 37 SiO maser stars in the channel maps and


derived their angular offsets relative to Sgr A _[∗]_ and LSR radial velocities. We derived the proper motions of 35 stars by comparing their


angular offsets in the two epochs. The proper motions of Wolf-Rayet and O star in the Nuclear Star Cluster (NSC) are reported to be


rather random, except for the co-moving clusters IRS13E and IRS13N (Tsuboi et al. 2022). However, the derived proper motions of SiO


maser stars do not look completely random. The proper motions of the SiO maser stars show a tendency to lie along the Galactic plane.


The proper motion amplitudes of SiO maser stars are larger than the LSR velocity amplitudes. We estimated the 3D motions from the


proper motions and LSR velocities. Many 3D velocities are near to or larger than the upper limit velocities for Kepler orbits around Sgr A _[∗]_,


whose mass is assumed to be 4 _×_ 10 [6] _M_ _⊙_ . These indicate that the SiO maser stars around Sgr A _[∗]_ are members of the Nuclear Stellar


Disk rather than the NSC.


**Keywords:** Galaxy: center, Galaxy: kinematics and dynamics, stars: late-type, radio lines: stars


**1** **Introduction**


The Galactic Center (GC) region is the central region of the Milky Way galaxy, which is located at a

distance of _d ∼_ 8 _._ 2 kpc from us (e.g., Boehle et al. 2016, Gravity Collaboration 2018). It harbors the
Galactic Center Black Hole (GCBH), the super massive black hole with _M_ GCBH _∼_ 4 _×_ 10 [6] _M_ _⊙_ (e.g.

Ghez et al. 2008, Boehle et al. 2016, Gravity Collaboration 2018). The counterpart of the GCBH

is observed as Sagittarius A _[∗]_ (Sgr A _[∗]_ ) in radio, infrared (IR), and X-ray wavelengths. The Atacama

Large Millimeter/Submillimeter Array (ALMA) can image the region with the unprecedented small

synthesized beam size. High-resolution observations of the GC region are important not only to study

individual peculiar structures and phenomena in the region, but also to provide initial information for

the study of central regions in spiral galaxies.


**Received:**, **Accepted:**


© 2024. Astronomical Society of Japan.

**2** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


There are stratified groups of stars in the GC region. The innermost group is called "S-stars"

and is identified as a cluster of B stars within a few tenths of a pc of Sgr A _[∗]_ (e.g. Genzel et al. 1997,

Ghez et al. 1998, Ghez et al. 2003). On the other hand, a cluster within a few pc of Sgr A _[∗]_ is

called the Nuclear Star Cluster (NSC), which contains many O stars and Wolf-Rayet (WR) stars (e.g.

Genzel et al. 1996, Ghez et al. 1998, Paumard et al. 2006, Schödel, Merritt, & Eckart 2009, Genzel,

Eisenhauer, & Gillessen 2010, Eckart et al. 2013, Yelda et al. 2014). Because it is difficult to form

these stars in the strong tidal force environment of the GCBH, their origin is still controversial. A

disk-shaped group of stars is observed up to _l ∼±_ 1 _[◦]_ in the outer region (Launhardt, Zylka & Mezger

2002, Stolovy et al. 2006, Nishiyama et al. 2013). This is called the Nuclear Stellar Disk (NSD)

and is composed mainly of older stars. These groups have been identified mainly on the basis of IR

observations. There is an ongoing astrometric observing program with an IR space-borne telescope

called JASMINE to determine the origin of the NSD (Gouda, JASMINE Team 2021, Kawata et al.

2024).


Attempts to search for SiO maser stars in the region within a few pc of Sgr A _[∗]_ have been made

with ATCA, JVLA and ALMA (e.g. Li et al. 2011, Paine & Darling 2022, Darling et al. 2023, Paine

& Darling 2024). The 3D kinematics of these stars can be determined from the radial velocity and

the proper motion. The radial velocity of the maser star is easily observable, but that of the early-type

stars is not easy to infer. ALMA has a very sharp synthesized beam with very high sensitivity. ALMA

300
has a large field of view (FOV), 20 _._ _[′′]_ 6 _×_ _ν_ [GHz] [= 67] _[.]_ _[′′]_ [5][ in Full Width Half Maximum (FWHM) for the]
SiO _v_ = 1 _,J_ = 2 _−_ 1 maser emission line ( _ν_ = 86 _._ 2 GHz) (see ALMA technical handbook), which

corresponds to the area within the radius of _r ∼_ 1 _._ 4 pc of Sgr A _[∗]_ . Moreover, the position of the stars

can be measured directly by referencing the position of Sgr A _[∗]_ with ALMA, since ALMA can always

detect Sgr A _[∗]_ . Therefore, ALMA is a suitable tool for precision astrometry within a few arcminutes

of Sgr A _[∗]_ (e.g. Tsuboi et al. 2022, Paine & Darling 2022, Darling et al. 2023, Paine & Darling

2024).


Since the kinematics of these groups of stars are thought to be closely related to their origin,

precision astrometry is important. The 3D kinematics of the maser stars in the vicinity of Sgr A _[∗]_


are very important for studying the mass distribution, including the enclosed mass in the region (e.g.

Paine & Darling 2022, Darling et al. 2023). However, these studies implicitly assume that these

maser stars are members of the NSC only because they are observed in the direction of the NSC. The
ages of the maser stars are expected to be 10 [9] years. On the other hand, the ages of the early type
stars of the NSC are at most 10 [8] years. If these clusters of different ages belong to the same cluster,

there is a mechanism for the mixing of early type stars and maser stars. Alternatively, the mixing may

occur by chance only in the line of sight. Here we focus on resolving this question based on statistical

properties in the kinematics of SiO maser stars. Throughout this paper, we adopt _d_ = 8 _._ 2 kpc as the
distance to the Galactic center. 1 _[′′]_ corresponds to 0 _._ 03975 pc or 1 _._ 224 _×_ 10 [17] cm at the distance. And

we use the International Celestial Reference System (ICRS) as the coordinate system.


**2** **Data acquisition and reduction**


We have obtained the archive data in the SiO _J_ = 2 _−_ 1 emission lines observed by the ALMA

in 2017 and 2021 (#2016.1. 00940.S, PI Darling, J. and #2019.1.00292.S, PI Paine, J.) from the

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **3**


ALMA Science Archive (https://almascience.nao.ac.jp/aq/). The ALMA observations consist of a

single pointing toward Sgr A _[∗]_ with the 12-meter Array in the SiO _v_ = 0 _, J_ = 2 _−_ 1 (86 _._ 847010

GHz), SiO _v_ = 1 _,J_ = 2 _−_ 1 (86 _._ 243440 GHz), and SiO _v_ = 2 _,J_ = 2 _−_ 1 (85 _._ 640446 GHz) emission

lines. In addition, we simultaneously observed the continuum emission of this region. We used the

continuum map to derive the the position of Sgr A _[∗]_ . The observation epochs in 2017 and 2021 were

September 19, 2017 and August 19, 2021, respectively. The original widths of the velocity channel
are 0 _._ 42 km s _[−]_ [1] for the _v_ = 0 and _v_ = 2 emission lines and 0 _._ 21 km s _[−]_ [1] for the SiO _v_ = 1 emission

line, respectively. J1733-1304, J1744-3116, and J1924-2914 were used as a flux calibrator, a phase

calibrator, and a band pass calibrator, respectively.


The calibration and imaging of the data were performed by CASA (CASA Team 2022).

Before imaging in the the SiO maser lines, the continuum emission of Sgr A _[∗]_ and the surround
ing continuum features were subtracted from the original data using the CASA task, `uvcontsub`

`(fitorder=0)` . The beam sizes in FWHM using Briggs weighting (robust parameter = 0.5) as _u-v_
sampling are _θ_ FWHM = 0 _._ _[′′]_ 091 _×_ 0 _._ _[′′]_ 082 _,PA_ = 43 _[◦]_ in 2017 and _θ_ FWHM = 0 _._ _[′′]_ 150 _×_ 0 _._ _[′′]_ 091 _,PA_ = 87 _[◦]_


in 2021, respectively. The maximum detectable angular scale of this observation is about 10 times

larger than the angular resolution. The channel maps of the SiO maser lines were made in the velocity
range from _V_ LSR = _−_ 350 km s _[−]_ [1] to _V_ LSR = +350 km s _[−]_ [1] using the CASA task, `tclean` . To improve
the sensitivity, the velocity integration width of the channel map is set to ∆ _V_ = 5 km s _[−]_ [1] . The inte
gration width is too wide to study the maser emission from the stars itself. However, it is suitable to

derive the radial motions of SiO maser stars. The typical Root Mean Square (RMS) noise levels in
the emission-free areas of the resulting maps are 1 _._ 1 mJy/beam/5 km s _[−]_ [1] in 2017 and 1 _._ 4 mJy/beam/5
km s _[−]_ [1] in 2021, respectively. These noise levels are the values at the center of the FOV. The outer

limit of the FOV was set so that the attenuation by the primary beam pattern of the 12 m antenna is
0.2 because the ALMA has high sensitivity. Therefore the radius of the FOV was widen up to _∼_ 50 _[′′]_

or 2 pc. The noise levels at the outer limit are 5 _._ 5 mJy/beam/5 km s _[−]_ [1] in 2017 and 7 _._ 0 mJy/beam/5
km s _[−]_ [1] in 2021, respectively.


**3** **Results**


3.1 Positions, Line intensities, and LSR velocities of the SiO maser stars


The weakness of the SiO _v_ = 2 _, J_ = 2 _−_ 1 emission line compared to the SiO _v_ = 1 _, J_ = 2 _−_ 1

emission line has been reported for late-type stars detected in the Galactic disk region (e.g. Bujarrabal

et al. 1996, Nakashima & Deguchi 2007, Lewis, Pihlström, & Sjouwerman 2024). Only the SiO

_v_ = 2 _, J_ = 2 _−_ 1 emission line of IRS 7 (17454004-2900228) was detected in this sample. It is

confirmed that the SiO _v_ =2 _,J_ =2 _−_ 1 emission line is also much weaker than the SiO _v_ =1 _,J_ =2 _−_ 1

emission line in the Galactic center region. Therefore, we used only the latter for the astrometric

analysis which will be mentioned in the following subsection. We detected 37 SiO maser stars in

the channel maps of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line in both 2017 and 2021. This detection

number is significantly improved from the previous analysis using the same data, which detected 28

stars (Darling et al. 2023, Paine & Darling 2024). Then, the statistical analysis of the kinematics

of SiO maser stars shown in the following section is possible due to the increase in detection. The

positions in the ICRS coordinate system of the SiO maser stars are determined by the 2D Gaussian

**4** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0





48"


-29 [o] 00’00"


12"


24"


36"


48"


-29 [o] 01’00"


12"









17 [h] 45 [m] 43 [s] 42 [s] 41 [s] 40 [s] 39 [s] 38 [s] 37 [s]


IRCS Right Ascension


**Fig. 1.** Positions of detected stars in the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line plotted on the continuum map at 105 GHz (pseudo color; Tsuboi et al.


2016) and the integrated intensity map of the CS _J_ = 2 _−_ 1 emission line (contours; Tsuboi et al. 2018). The red circles show the position of


detected stars. The cross shows the position of Sgr A _[∗]_ . The famous ionized gas flow around Sgr A _[∗]_, called the "Mini-Spiral (MS)", is the three

armed spiral-like feature on the continuum map. There is the "Circum Nuclear Disk (CND)" surrounding the MS, which is a molecular gas ring


rotating around Sgr A _[∗]_ . There does not seem to be a large number of SiO maser stars in correlation with MS, CND, and Sgr A _[∗]_ . Alt text: Circles


shown positions of SiO maser stars on the two overlaid maps of CS line emission and 105 GHz continuum emission.


fitting to the star image in the channel maps using the CASA task, `imfit` . However, the positions of

two SiO maser stars, 17453828-2900069 and 17453854-2859582, could not be determined in 2021

although they were determined in 2017. These failures are caused by the line intensity decrease of

the SiO maser emission in 2021.


Figure 1 shows the positions in 2017 of the detected stars in the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission

line (red circles) plotted on the continuum map at 105 GHz (pseudo color; Tsuboi et al. 2016)

and the integrated intensity map of the CS _J_ = 2 _−_ 1 emission line (contours; Tsuboi et al. 2018).
The integration velocity range of the CS _J_ = 2 _−_ 1 emission line is from _V_ LSR = _−_ 150 km s _[−]_ [1] to
_V_ LSR = +150 km s _[−]_ [1] . The three-armed spiral-like feature on the continuum map is a famous ionized

gas flow around Sgr A _[∗]_ . It is called the "Mini-Spiral (MS)"(Eckers et al. 1983, Lo & Claussen

1983). There is also the "Circum Nuclear Disk (CND)" surrounding the MS in this figure, which is a

molecular gas ring rotating around the GCBH (e.g. Tsuboi et al. 2018 ). The SiO maser stars are not

only distributed on the MS, but also on the outside of the CND. However, there does not seem to be a

large number of SiO maser stars correlated with the MS, the CND, and Sgr A _[∗]_ . The positions of the

SiO maser stars in both 2017 and 2021 are summarized in Table 1.


Figure 2 shows the line profiles of the SiO _v_ = 1 _, J_ = 2 _−_ 1 emission line towards a SiO

maser star, 17454320-2900130, as an example. We made the line profiles of the SiO _v_ = 1 _,J_ = 2 _−_ 1

emission line from the channel maps and derived the LSR radial velocities from the line profiles with

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **5**


60





50


40


30


20


10


0


-10







-300 -200 -100 0 100 200 300



LSR Velocity (km s -1 )



**Fig. 2.** Line profiles of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line toward 17454320-2900130 as an example. The velocity interval is 5 km s _[−]_ [1] . All other


line profiles are shown in Figure 10 in Appendix. Alt text: Two line graphs showing the line profiles at 2017 and 2021 toward 17454320-2900130.


Gaussian fitting. To obtain the line intensity of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line, the attenuation
by the primary beam pattern at the angular distance from Sgr A _[∗]_, ∆ _θ_, was corrected by the formula;


_S_ _corr_ = _S_ _obs_ exp[4ln2(∆ _θ/FWHM_ ) [2] ] _._ (1)


All other line profiles are shown in Figure 10 in Appendix. Among the two SiO maser stars failed to

obtain the 2021 positions, the line profiles in both 2017 and 2021 are easily identifiable for 17453828
2900069 while the 2021 line profile is barely identifiable for 17453854-2859582.

Figure 3 shows the line intensity evolution of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line between

2017 and 2021. Although significant changes are observed for all stars between two epochs, all stars

are detected in both epochs as mentioned above. The line intensity of 19 stars decrease and those

of 18 stars increase between two epochs. These observed changes are consistent with those of late

type stars detected in the Galactic disk region, which is usually variable in several hundred days (e.g.

Nakashima & Deguchi 2007, Lewis, Pihlström, & Sjouwerman 2024). On the other hand, the change

of the LSR velocity is negligible for almost all stars. The LSR velocities of 15 stars have plus sign
and those of 22 stars have minus sign. The mean LSR velocity is _V_ LSR = _−_ 24 _._ 9 _±_ 86 _._ 7 km s _[−]_ [1] . There

is no significant trend in the LSR velocities. Note that the observed LSR velocities are those of the

SiO maser spots around the stars, not the LSR velocities of the stars themselves. The difference can
be as much as _∼_ 10 km s _[−]_ [1] . However, this is not a major problem in this analysis. The line intensities

and LSR velocities of the SiO maser stars are also summarized in Table 1.

Figures 4a and 4b show the histograms of the line intensities in the SiO _v_ = 1 _, J_ = 2 _−_ 1
emission line of the detected stars in 2017 and 2021, respectively. The line intensities of the _∼_ 70% of

the detected stars are less than 50 mJy in 2017. Only four stars have line intensities greater than 100

mJy. The average line intensities are 47 _._ 0 _±_ 43 _._ 6 mJy in 2017. On the other hand, the line intensities
of _∼_ 60% of the detected stars are smaller than 50 mJy in 2021. Five stars have line intensities

greater than 100 mJy. The average line intensities are 55 _._ 4 _±_ 52 _._ 0 mJy in 2021. The situation has not

changed between two epochs. Most of them could be observed as inconspicuous maser stars with line

**6** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


**Fig. 3.** Line intensity evolution of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line between 2017 and 2021. The horizontal axis and the vertical axis are the


line intensities in 2017 and 2019, respectively. Linear lines show the ratios of the line intensities at two epochs. Alt text: A dispersion diagram.

|a|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|a|a|||||
|||||||
|||||||
|||||||
|||||||



0 50 100 150 200

|b|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|||||||||
|||||||||
|||||||||


Flux denisity (mJy)


**Fig. 4.** **a** Histogram of the line intensity of the SiO _v_ = 1 _, J_ = 2 _−_ 1 emission line of detected stars in 2017. The ratio of the detected stars with


smaller than 50 mJy in 2017 is _∼_ 70% . **b** Histogram of the line intensity of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line of detected stars in 2021. The


ratio of the detected stars with smaller than 50 mJy in 2021 is _∼_ 60% . Alt text: Two histograms. The horizontal axis and the vertical axis are the line


intensity and count, respectively.

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **7**


,


**Fig. 5.** Radial distribution of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line intensity of detected stars in 2017 on the angular distance from Sgr A _[∗]_ . Alt text:


A dispersion diagram. The horizontal axis and the vertical axis are the angular distance from Sgr A _[∗]_ and line intensity, respectively.


intensities of a few Jy when they were within a few kpc (Cf. Lewis, Pihlström, & Sjouwerman 2024).

Figure 5 shows the radial distribution of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line intensity of

the detected stars in 2017 as a function of the angular distance from Sgr A _[∗]_, whose derivation will

be mentioned in the next subsection. There is no clear trend in the radial distribution. The stars with

_S_ _>_ 100 mJy are widely scattered. The stars with 10 _< S_ _<_ 50 mJy were detected around Sgr A _[∗]_

and also near the outer edge of the channel map. On the other hand, the star with _S_ _<_ 10 mJy was

not detected near the outer edge of the channel map. Attenuation by the primary beam pattern causes

the detection efficiency to decrease somewhat near the outer edge. However, this could not affect the

astrometric analysis mentioned in the following subsection.


3.2 Proper motions of the SiO maser stars


Since the position of Sgr A _[∗]_ in the ICRS coordinate system changes with the Galactic rotation of the

Sun (e.g Reid&Brunthaler 2004, Xu et al. 2022, Oyama et al. 2024), the angular differences between

the positions of the SiO maser stars summarized in Table 1 are not their proper motions. On the contin
uum maps mentioned above, the positions of Sgr A _[∗]_ in the ICRS coordinate system were measured to
be (RA, Dec) ICRS = (17 [h] 45 [m] 40 _._ [s] 033456 _±_ 0 _._ [s] 000002, _−_ 29 _[◦]_ 00 _[′]_ 28 _._ _[′′]_ 22993 _±_ 0 _._ _[′′]_ 00002) at September 19,
2017 and (RA, Dec) ICRS = (17 [h] 45 [m] 40 _._ [s] 032847 _±_ 0 _._ [s] 000005, _−_ 29 _[◦]_ 00 _[′]_ 28 _._ _[′′]_ 26277 _±_ 0 _._ _[′′]_ 00003) at August
19, 2021, respectively. We obtained the positions relative to Sgr A _[∗]_, (∆RA, ∆Dec), by subtracting

these positions of Sgr A _[∗]_ from the positions shown in Table 1 using 2D Gaussian fitting, the CASA

task, `imfit` . The positions relative to Sgr A _[∗]_ of the SiO maser stars are summarized in Table 2.

We obtained the angular differences between their positions relative to Sgr A _[∗]_ in 2017 and

2021 in Cartesian coordinate system, which are given by


∆ _X_ = _−_ (∆RA 2021 _−_ ∆RA 2017 ) (2)

**8** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


-300 -200 -100 0 100 200 300 km s [-1]



















































17 [h] 45 [m] 43 [s] 42 [s] 41 [s] 40 [s] 39 [s] 38 [s] 37 [s]


IRCS Right Ascension


**Fig. 6.** Proper motions in vectors and LSR radial velocities in color of the SiO maser stars around Sgr A _[∗]_ plotted on the continuum map at 105


GHz (black and white; Tsuboi et al. 2016) and the integrated intensity map of the CS _J_ = 2 _−_ 1 emission line (contours; Tsuboi et al. 2018). The


lengths of the vectors indicate the amplitudes of the proper motions. The numbers to the sides of the vectors indicate the LSR velocities. Alt text:


Vectors shown proper motions of SiO maser stars on the two overlaid maps of CS line emission and 105 GHz continuum emission.


∆ _Y_ = ∆Dec 2021 _−_ ∆Dec 2017 _._ (3)



Then we determined the proper motions relative to Sgr A _[∗]_ of 35 SiO maser stars using the following

formula;
_|V_ prop _|_ [km s _[−]_ [1] ] = [38827] ∆ _t_ _√_ ∆ _X_ [2] + ∆ _Y_ [2] _._ (4)

The time difference between the observation epochs is ∆ _t_ = 3 _._ 917 years. Because the origin and

rotation direction of the position angle are defined as north and counterclockwise, respectively, the
different formula is used for the derivation in west (∆ _X_ _>_ 0) and east (∆ _X_ _<_ 0) . These are



∆ _t_



_√_



∆ _X_ [2] + ∆ _Y_ [2] _._ (4)



_PA_ [ _[◦]_ ] = _−_ 90 + arctan [∆] _[Y]_ _[>]_ [ 0)] (5)

∆ _X_ [(∆] _[X]_


and
_PA_ [ _[◦]_ ] = 90 + arctan [∆] _[Y]_ _[<]_ [ 0)] _[.]_ (6)

∆ _X_ [(∆] _[X]_

The derived proper motions of stars detected in previous observations, such as that of IRS7

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **9**

|a|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|a|a|a|a|a|a|||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||


|b|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|b|b|b|b|b|||||||
|b|b|b|||||||||
|b|b|b|||||||||
||||||||||||
||||||||||||



Position angle (deg.)


**Fig. 7.** **a** Histogram of the position angle of the proper motions relative to Sgr A _[∗]_ of 35 SiO maser stars. The black arrows indicate the direction of


Galactic plane. **b** Histogram of the position angle of the proper motions of the WR and O stars in the NSC, excluding the co-moving clusters IRS13E


and IRS13N (Tsuboi et al. 2022). Alt text: Two histograms. The horizontal axis and the vertical axis are the position angle and count, respectively.


(17454004-2900228), are consistent with the previously derived proper motions (e.g. Tsuboi et al.

2022, Darling et al. 2023, Paine & Darling 2024). The proper motions relative to Sgr A _[∗]_ of the SiO

maser stars are also summarized in Table 2.

Figure 6 shows the proper motions relative to Sgr A _[∗]_ in vectors and the LSR radial velocities

in color of the SiO maser stars plotted on the continuum map at 105 GHz (black and white; Tsuboi

et al. 2016) and the integrated intensity map of the CS _J_ = 2 _−_ 1 emission line (contours; Tsuboi

et al. 2018). The derived proper motions of the SiO maser stars do not look completely random. If

anything, some co-moving groups can be identified (Cf. Fig. 7 in Tsuboi et al. 2022). The ionized

gas streams of the MS have been reported to orbit the GCBH on high eccentricity Keplerian orbits

(Zhao et al. 2009). The derived proper motions of the SiO maser stars do not appear to be such

Keplerian orbits. While the CND has been reported to orbit the GCBH on a nearly circular orbit (e.g.

Tsuboi et al. 2018), the proper motions do not appear to be such a circular orbit. Therefore, the

proper motions are not correlated with the MS and the CND.


**4** **Discussion**


4.1 Proper motion along the Galactic plane


As mentioned above, we determined the proper motions relative to Sgr A _[∗]_ of 35 SiO maser stars.

Figure 7a shows the histogram of the position angles of the proper motion relative to Sgr A _[∗]_ of the

SiO maser stars. The distribution of the position angles are bipolar rather than random. The black

arrows indicate the direction of the Galactic plane. The peaks of the distribution coincide with the

direction of the Galactic plane. That is, the proper motions of the SiO maser stars show a tendency

to lie along the Galactic plane. For comparison, Figure 7b shows the histogram of the position angle

**10** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0

|a|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|a|a||||
|a|a||||
|a|||||
|a|||||
||||||



Velocity (km s ) -1


**Fig. 8.** **a** Histogram of the proper motion amplitudeof SiO maser stars. The mean proper motion amplitude is _|V_ prop _|_ = 153 _._ 2 _±_ 83 _._ 3 km s _[−]_ [1] . **b**


Histogram of the LSR velocity amplitude of SiO maser stars. The mean amplitude of the LSR velocity is _|V_ LSR _|_ = 66 _._ 1 _±_ 60 _._ 6 km s _[−]_ [1] . Alt text: Two


histograms. The horizontal axis and the vertical axis are the velocity and count, respectively.


Projected distance from Sgr A*, _r_ (cm)


**Fig. 9.** Space velocities of the SiO maser stars at projected distances, _r_, from Sgr A _[∗]_ . The solid line curve indicates the orbital velocity of circular



orbits, _V_ = ~~�~~ _GMr_ [,] [assuming] [that] [the] [mass] [of] [the] [GCBH] [is] _[M]_ [= 4] _[ ×]_ [ 10] [6] _[M]_ _[⊙]_ [.] [The] [dashed] [curve] [indicates] [the] [orbital] [velocity] [of] [extremely] [highly]



eccentric orbits, _V_ = ~~�~~ 2 _GMr_ . Alt text: A dispersion diagram.

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **11**


of the proper motions of the WR and O stars in the NSC, excluding the co-moving clusters IRS13E

and IRS13N (Tsuboi et al. 2022). The black arrows also indicate the direction of the galactic plane.

The proper motions of the NSC stars are rather random. A tendency along the Galactic plane is not

apparent. It is therefore plausible that the statistical property of the proper motions of the SiO maser

stars is different from that of the NSC.


If the SiO maser stars belonged to the NSC, their motions were well randomized by a short

time scale in the NSC, for example the period of the Keplerian orbit with the radius of 2 pc is _P_ _∼_
1 _._ 3 _×_ 10 [5] years. As the result, they should have a similar statistical property of the proper motions.

On the other hand, if the SiO maser stars belonged to the NSD, the position angles were such that

they were observed. This situation is consistent with that the proper motions of the SiO maser stars

are not correlated with the MS and the CND (see Results).


4.2 Disproportionate proper motion speed and LSR speed


Figures 8a and 8b show the histograms of the proper motion amplitude and the LSR velocity

amplitude of SiO maser stars, respectively. The mean proper motion amplitude is derived to be
_|V_ prop _|_ = 153 _._ 2 _±_ 83 _._ 3 km s _[−]_ [1] (Cf. _|V_ prop _|_ = 239 _._ 4 _±_ 127 _._ 7 km s _[−]_ [1] for the NSC stars in Tsuboi et al.
2022). While the mean amplitude of the LSR velocity is derived to be _|V_ LSR _|_ = 66 _._ 1 _±_ 60 _._ 6 km s _[−]_ [1] .
The proper motion amplitude is larger than the LSR velocity amplitude. That is, in the observed

SiO maser stars, the motions across the line of sight dominate the motions along the line of sight.

Moreover the motions have a tendency to be along the Galactic plane (see Figure 7a).


If the SiO maser stars belonged to the NSC, their motions would be well randomized (see the

previous subsection) and both amplitudes should be similar. On the other hand, if the SiO maser stars

belong to the NSD (see Sanders et al. 2022), they would pass in front of or behind the GCBH on

orbits with larger radii. Then their motions should be such that they could be observed here.


4.3 Large enclosed mass



We derived the space velocities of the SiO maser stars from these proper motions and the LSR radial
velocities using _V_ space = _V_ prop [2] _._ [+] _[ V]_ LSR [2] [.] [Figure 9 shows the space velocities of the SiO maser stars]
~~�~~
at projected distances, _r_, from Sgr A _[∗]_ . There is no clear tendency for stars near Sgr A _[∗]_ to have

large velocities and stars far from Sgr A _[∗]_ to have small velocities, as observed in the NSC. The solid
line curve indicates the orbital velocity of circular orbits, _V_ = _GMr_ [,] [assuming] [that] [the] [mass] [of]
~~�~~



line curve indicates the orbital velocity of circular orbits, _V_ = _r_ [,] [assuming] [that] [the] [mass] [of]

the GCBH is _M_ = 4 _×_ 10 [6] _M_ _⊙_ . The dashed curve indicates the orbital velocity of extremely highly
eccentric orbits, _V_ = 2 _GMr_ [.] [Many inferred space velocities are larger than the former.] [Several reach]
~~�~~



eccentric orbits, _V_ = _r_ [.] [Many inferred space velocities are larger than the former.] [Several reach]

or exceed the latter (Cf. Fig.8 in Tsuboi et al. 2022).


If the stars belong to the NSC, the _V_ = 2 _GMr_ should be the upper limit of the space velocities.
~~�~~

To resolve the discrepancy with the observed space velocities, it is hypothesized that there may be

additional mass in the region. Since the mass appears to accelerate the velocities of the stars by up
to several 10 %, the required mass is expected to be as large as _M_ _∼_ 10 [6] _M_ _⊙_ . However, such a mass

has not been observed in other observations (e.g. Reid&Brunthaler 2004, Oyama et al. 2024). If the

SiO maser stars belong to the NSD, this kinematics can be expected.



If the stars belong to the NSC, the _V_ = 2 _GMr_
~~�~~

**12** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


**5** **Conclusions**


We present the kinematics of SiO maser stars around Sgr A _[∗]_ using the archive data in the SiO _v_ =

1 _,J_ = 2 _−_ 1 emission line obtained by the Atacama Large Millimeter/Submillimeter Array (ALMA)

in 2017 and 2021.


 - We detected 37 SiO maser stars and derived their angular offsets relative to Sgr A _[∗]_ and LSR radial

velocities.

 - We derived the proper motions of 35 SiO maser stars by comparing their angular offsets in the two

epochs.

 - The proper motions of the SiO maser stars show a tendency to lie along the Galactic plane.

 - The proper motion amplitudes are larger than the LSR velocity amplitude.

 - Many 3D velocities are near to or larger than the upper limit velocities for Kepler orbits around Sgr
A _[∗]_, whose mass is assumed to be 4 _×_ 10 [6] _M_ _⊙_ .

 - These results indicate that the SiO maser stars are members of the NSD rather than the NSC.


**Acknowledgments**


ALMA is a partnership of European Southern Observatory (ESO) (representing its member states),

the National Science Foundation (NSF) (USA) and National Institutes of Natural Sciences (NINS)

(Japan), together with National Research Council Canada (NRC) (Canada), Ministry of Science

and Technology (MOST) and Institute of Astronomy and Astrophysics, Academia Sinica (ASIAA)

(Taiwan), and Korea Astronomy and Space Science Institute (KASI) (Republic of Korea), in cooper
ation with the Republic of Chile. The National Radio Astronomy Observatory (NRAO) is a facility

of NSF operated under cooperative agreement by Associated Universities, Inc. USA (AUI). The Joint

ALMA Observatory (JAO) is operated by ESO, AUI/NRAO and National Astronomical Observatory

of Japan (NAOJ). This paper makes use of the following ALMA data ADS/JAO. ALMA#2016.1.

00940.S and ALMA#2019.1.00292.


**Appendix.** **Line profiles of SiO** _**v**_ **= 1** _**,J**_ **= 2** _**−**_ **1** **Maser stars**


Figures 10 show the line profiles of the SiO _v_ = 1 _,J_ = 2 _−_ 1 emission line toward the detected SiO

maser stars except for 17454320-2900130.

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **13**


SiO _v_ =1, _J_ =2-1


**Fig. 10.** Line profiles of SiO _v_ = 1 _,J_ = 2 _−_ 1 maser stars. The velocity interval is 5 km s _[−]_ [1] . Alt text: 36 divisions. Two line graphs showing the line


profiles at 2017 and 2021 toward a SiO maser stars in a division.

**14** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


SiO _v_ =1, _J_ =2-1


**Fig. 10.** Continued.

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **15**


SiO _v_ =1, _J_ =2-1


**Fig. 10.** Continued.

**16** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **17**

**18** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **19**

**20** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0



**References**


Gravity Collaboration; Abuter, R. et al. 2018, A&A, 615, L15


Boehle, A. et al. 2016, ApJ, 830, id 17


Bujarrabal, V., Alcolea, J., Sanchez Contreras, C., & Colomer, F., 1996,


A&A, 314, 883


CASA Team, Bean, B., Bhatnagar, S., Castro, S., et al. 2022, PASP, 134,


id.114501


Darling, J., Paine, J., Reid, M. J. et al., 2023, ApJ, 955, id.117


Ekers R. D., van Gorkom, J. H., Schwarz, U. J. & Goss, W. M. 1983


A&A122 143


Eckart, A. et al. 2013, A&A, 551, A18


Genzel, R., Thatte, N., Krabbe, A., Kroker, H., & Tacconi-Garman, L. E.


1996, ApJ, 472, 153


Genzel, R., Eckart, A.Ott, T., & Eisenhauer, 1997, MNRAS, 291, 219


Genzel, R., Eisenhauer, F., & Gillessen, S. 2010, _Rev._ _Mod._ _Phys_, 82,


3121


Ghez, A. M., Klein, B. L., Morris, M. & Becklin, E. E., 1998, ApJ, 509,


678


Ghez, A. M., Duchêne, G., Matthews, K. et al. 2003, ApJ, 586,L127


Ghez, A. M., et al. 2008, ApJ, 689, 1044


Gouda, N., JASMINE Team, 2021, New Horizons in Galactic Center


Astronomy and Beyond, eds. M. Tsuboi and T. Oka, ASP Conf. Ser.,


528, 163


Kawata, D., Kawahara, H., Gouda, N. et al., 2024, PASJ, 76, 386


Launhardt, R., Zylka, R., & Mezger, P. G., 2002, A&A, 384, 112


Lewis, M. O., Pihlström, Y. M., & Sjouwerman, L. O., 2024, Cosmic


Masers: Proper Motion Toward the Next-Generation Large Projects,


Proceedings of the International Astronomical Union, 380, 314


Lo, K.Y. & Claussen, M. J. 1983 Nature306 647


Li, J., An, T., Shen, Z., & Miyazaki, A., 2011, The Galactic Center:


a Window to the Nuclear Environment of Disk Galaxies, eds. M. R.


Morris, Q. D. Wang, & F. Yuan. ASP Conf. Ser.439, 260


Mužic, K., Schödel, R., Eckart, A., Meyer, L., & Zensus, A. 2008, A&A,


482,173


Nakashima, J. & Deguchi, S., 2007, ApJ, 669,446


Nishiyama, S., Yasui, K.m Nagata, T. et al. 2013, ApJ, 769, 28


Oyama, T., Nagayama, T., Yamauchi, A., et al. / 2024, PASJ, 76, 163


Paine, J. & Darling, J., 2022,ApJ, 927, 181


Paine, J. & Darling, J., 2024, Cosmic Masers: Proper Motion Toward


the Next-Generation Large Projects, Proceedings of the International


Astronomical Union, 380, 101


Paumard, T., et al. 2006, ApJ, 643, 1011


Reid, M. J. &Brunthaler, A. 2004, ApJ, 616, 872


Sanders, J. L., Matsunaga, N., Kawata, D., Smith, L. C., Minniti, D., &


Lucas, P. W., 2022, MNRAS, 517, 257


Schödel, R., Merritt, D.& Eckart, A., 2009, A&A, 502, 91



Stolovy, S., Ramirez, S., Arendt, R. G. et al. 2006, The Universe Under


the Microscope   - Astrophysics at High Angular Resolution, eds. R.


Schödel, A. Eckart, S. Pfalzner and E. Ros, Journal of Physics:


Conference Series, 54, 176


Tsuboi, M., Kitamura,Y., Miyoshi, M., Uehara, K., Tsutsumi, T., &


Miyazaki, A., 2016, PASJ, 68, id.L7


Tsuboi, M., Kitamura, Y., Uehara, K., Tsutsumi, T., Miyawaki, R.,


Miyoshi, M., & Miyazaki, A., 2018, PASJ, 70, id.85


Tsuboi, M., Tsutsumi, Miyazaki, A.,T., Miyawaki, R., & Miyoshi, M.,


2022, PASJ, 74, 738


Xu, S., Zhang, B., Reid, M. J. et al., 2022, apj, 940,15


Yelda, S., Ghez, A. M., Lu, J. R., et al. 2014, ApJ, 783, 131


Zhao, J.-H., Morris, M. R., Goss, W. M., & An, T., 2009, ApJ, 699,186


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: archival_reuse",
  "failed_quote": "We have obtained the archive data in the SiO J = 2 - 1 emission lines observed by the ALMA in 2017 and 2021 (#2016.1. 00940.S, PI Darling, J. and #2019.1.00292.S, PI Paine, J.) from the ALMA Science Archive (https://almascience.nao.ac.jp/aq/)."
 },
 {
  "path": "science.targets[0].coordinates.evidence[2]",
  "value": "(17h45m40.033456s, -29d00m28.22993s) ICRS (2017) and (17h45m40.032847s, -29d00m28.26277s) ICRS (2021)",
  "failed_quote": "On the continuum maps mentioned above, the positions of Sgr A* in the ICRS coordinate system were measured to be (RA, Dec) ICRS = (17 h 45 m 40.s 033456 +- 0.s 000002, - 29 deg 00' 28.'' 22993 +- 0.'' 00002) at September 19, 2017"
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[2]",
  "value": "8.2 kpc",
  "failed_quote": "On the continuum maps mentioned above, the positions of Sgr A* in the ICRS coordinate system were measured to be (RA, Dec) ICRS = (17 h 45 m 40.s 033456 +- 0.s 000002, - 29 deg 00' 28.'' 22993 +- 0.'' 00002) at September 19, 2017"
 },
 {
  "path": "science.targets[0].distance_source.evidence[2]",
  "value": "Boehle et al. 2016, Gravity Collaboration 2018",
  "failed_quote": "On the continuum maps mentioned above, the positions of Sgr A* in the ICRS coordinate system were measured to be (RA, Dec) ICRS = (17 h 45 m 40.s 033456 +- 0.s 000002, - 29 deg 00' 28.'' 22993 +- 0.'' 00002) at September 19, 2017"
 },
 {
  "path": "science.question.evidence[2]",
  "value": "Whether the SiO maser stars around Sagittarius A* are members of the Nuclear Star Cluster (NSC) or the Nuclear Stellar Disk (NSD) based on statistical properties of their 3D kinematics.",
  "failed_quote": "These indicate that the SiO maser stars around Sgr A* are members of the Nuclear Stellar Disk rather than the NSC."
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "SiO v=0, J=2-1 (86.847010 GHz, channel width 0.42 km/s), SiO v=1, J=2-1 (86.243440 GHz, channel width 0.21 km/s), SiO v=2, J=2-1 (85.640446 GHz, channel width 0.42 km/s), plus simultaneous continuum",
  "failed_quote": "The ALMA observations consist of a single pointing toward Sgr A* with the 12-meter Array in the SiO v = 0, J = 2 - 1 (86.847010 GHz), SiO v = 1 ,J = 2 - 1 (86.243440 GHz), and SiO v = 2 ,J = 2 - 1 (85.640446 GHz) emission lines."
 },
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "SiO",
  "failed_quote": "The ALMA observations consist of a single pointing toward Sgr A* with the 12-meter Array in the SiO v = 0, J = 2 - 1 (86.847010 GHz), SiO v = 1 ,J = 2 - 1 (86.243440 GHz), and SiO v = 2 ,J = 2 - 1 (85.640446 GHz) emission lines."
 },
 {
  "path": "data.lines_targeted[1].evidence[0]",
  "value": "SiO",
  "failed_quote": "The ALMA observations consist of a single pointing toward Sgr A* with the 12-meter Array in the SiO v = 0, J = 2 - 1 (86.847010 GHz), SiO v = 1 ,J = 2 - 1 (86.243440 GHz), and SiO v = 2 ,J = 2 - 1 (85.640446 GHz) emission lines."
 },
 {
  "path": "data.lines_targeted[2].evidence[0]",
  "value": "SiO",
  "failed_quote": "The ALMA observations consist of a single pointing toward Sgr A* with the 12-meter Array in the SiO v = 0, J = 2 - 1 (86.847010 GHz), SiO v = 1 ,J = 2 - 1 (86.243440 GHz), and SiO v = 2 ,J = 2 - 1 (85.640446 GHz) emission lines."
 },
 {
  "path": "data.arrays.evidence[0]",
  "value": "12-meter Array",
  "failed_quote": "The ALMA observations consist of a single pointing toward Sgr A* with the 12-meter Array in the SiO v = 0, J = 2 - 1 (86.847010 GHz), SiO v = 1 ,J = 2 - 1 (86.243440 GHz), and SiO v = 2 ,J = 2 - 1 (85.640446 GHz) emission lines."
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0.091'' x 0.082'', PA = 43 deg (2017); 0.150'' x 0.091'', PA = 87 deg (2021)",
  "failed_quote": "The beam sizes in FWHM using Briggs weighting (robust parameter = 0.5) as u-v sampling are theta_FWHM = 0.''091 x 0.''082 ,PA = 43 deg in 2017 and theta_FWHM = 0.''150 x 0.''091 ,PA = 87 deg in 2021, respectively."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[1]",
  "value": "Proper motions of Wolf-Rayet (WR) and O stars in the Nuclear Star Cluster (NSC)",
  "failed_quote": "The mean proper motion amplitude is derived to be |V_prop| = 153.2 +- 83.3 km s^-1 (Cf. |V_prop| = 239.4 +- 127.7 km s^-1 for the NSC stars in Tsuboi et al. 2022)."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "Briggs weighting (robust parameter = 0.5)",
  "failed_quote": "The beam sizes in FWHM using Briggs weighting (robust parameter = 0.5) as u-v sampling are theta_FWHM = 0.''091 x 0.''082 ,PA = 43 deg in 2017 and theta_FWHM = 0.''150 x 0.''091 ,PA = 87 deg in 2021, respectively."
 },
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "uvcontsub (fitorder=0)",
  "failed_quote": "Before imaging in the the SiO maser lines, the continuum emission of Sgr A* and the surrounding continuum features were subtracted from the original data using the CASA task, uvcontsub (fitorder=0)."
 },
 {
  "path": "processing.imaging.primary_beam_correction.evidence[0]",
  "value": "S_corr = S_obs exp[4 ln 2 (Delta_theta / FWHM)^2]",
  "failed_quote": "To obtain the line intensity of the SiO v = 1 ,J = 2 - 1 emission line, the attenuation by the primary beam pattern at the angular distance from Sgr A*, Delta_theta, was corrected by the formula; S_corr = S_obs exp[4ln2(Delta_theta/FWHM)^2]."
 },
 {
  "path": "processing.imaging.smoothing.evidence[0]",
  "value": "velocity integration width Delta_V = 5 km s^-1",
  "failed_quote": "To improve the sensitivity, the velocity integration width of the channel map is set to Delta_V = 5 km s^-1."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "0.091'' x 0.082'', PA = 43 deg (2017); 0.150'' x 0.091'', PA = 87 deg (2021)",
  "failed_quote": "The beam sizes in FWHM using Briggs weighting (robust parameter = 0.5) as u-v sampling are theta_FWHM = 0.''091 x 0.''082 ,PA = 43 deg in 2017 and theta_FWHM = 0.''150 x 0.''091 ,PA = 87 deg in 2021, respectively."
 },
 {
  "path": "processing.inherited[0].what.evidence[1]",
  "value": "Distance to the Galactic center d = 8.2 kpc and GCBH mass M_GCBH ~ 4 x 10^6 M_sun",
  "failed_quote": "It harbors the Galactic Center Black Hole (GCBH), the super massive black hole with M_GCBH ~ 4 x 10^6 M_sun (e.g. Ghez et al. 2008, Boehle et al. 2016, Gravity Collaboration 2018)."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Subtract continuum emission using uvcontsub (fitorder=0) and image both continuum and SiO maser line channel maps from V_LSR = -350 to +350 km s^-1 with 5 km s^-1 velocity integration width using tclean.",
  "failed_quote": "Before imaging in the the SiO maser lines, the continuum emission of Sgr A* and the surrounding continuum features were subtracted from the original data using the CASA task, uvcontsub (fitorder=0)."
 },
 {
  "path": "analysis_steps[0].method.evidence[2]",
  "value": "Subtract continuum emission using uvcontsub (fitorder=0) and image both continuum and SiO maser line channel maps from V_LSR = -350 to +350 km s^-1 with 5 km s^-1 velocity integration width using tclean.",
  "failed_quote": "To improve the sensitivity, the velocity integration width of the channel map is set to Delta_V = 5 km s^-1."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "fitorder = 0",
  "failed_quote": "Before imaging in the the SiO maser lines, the continuum emission of Sgr A* and the surrounding continuum features were subtracted from the original data using the CASA task, uvcontsub (fitorder=0)."
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "Briggs weighting (robust = 0.5)",
  "failed_quote": "The beam sizes in FWHM using Briggs weighting (robust parameter = 0.5) as u-v sampling are theta_FWHM = 0.''091 x 0.''082 ,PA = 43 deg in 2017 and theta_FWHM = 0.''150 x 0.''091 ,PA = 87 deg in 2021, respectively."
 },
 {
  "path": "analysis_steps[0].key_parameters[2].evidence[1]",
  "value": "Delta_V = 5 km s^-1, V_LSR = -350 to +350 km s^-1",
  "failed_quote": "To improve the sensitivity, the velocity integration width of the channel map is set to Delta_V = 5 km s^-1."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Perform 2D Gaussian fitting on the star images in the SiO v=1, J=2-1 channel maps and on Sgr A* in the continuum maps using the CASA task imfit, then subtract Sgr A* positions to obtain relative angular offsets (Delta_RA, Delta_Dec).",
  "failed_quote": "The positions in the ICRS coordinate system of the SiO maser stars are determined by the 2D Gaussian fitting to the star image in the channel maps using the CASA task, imfit."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Perform 2D Gaussian fitting on the star images in the SiO v=1, J=2-1 channel maps and on Sgr A* in the continuum maps using the CASA task imfit, then subtract Sgr A* positions to obtain relative angular offsets (Delta_RA, Delta_Dec).",
  "failed_quote": "We obtained the positions relative to Sgr A*, (Delta_RA, Delta_Dec), by subtracting these positions of Sgr A* from the positions shown in Table 1 using 2D Gaussian fitting, the CASA task, imfit."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "2D Gaussian fitting via CASA imfit",
  "failed_quote": "The positions in the ICRS coordinate system of the SiO maser stars are determined by the 2D Gaussian fitting to the star image in the channel maps using the CASA task, imfit."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Extract SiO v=1, J=2-1 line profiles from the channel maps, fit Gaussians to derive LSR radial velocities, and apply Gaussian primary beam attenuation correction based on angular distance from Sgr A*.",
  "failed_quote": "We made the line profiles of the SiO v = 1 ,J = 2 - 1 emission line from the channel maps and derived the LSR radial velocities from the line profiles with Gaussian fitting."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Extract SiO v=1, J=2-1 line profiles from the channel maps, fit Gaussians to derive LSR radial velocities, and apply Gaussian primary beam attenuation correction based on angular distance from Sgr A*.",
  "failed_quote": "To obtain the line intensity of the SiO v = 1 ,J = 2 - 1 emission line, the attenuation by the primary beam pattern at the angular distance from Sgr A*, Delta_theta, was corrected by the formula; S_corr = S_obs exp[4ln2(Delta_theta/FWHM)^2]."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "FWHM = 67.5'' at 86.2 GHz",
  "failed_quote": "ALMA has a large field of view (FOV), 20.''6 x 300 / nu [GHz] = 67.''5 in Full Width Half Maximum (FWHM) for the SiO v = 1 ,J = 2 - 1 maser emission line (nu = 86.2 GHz) (see ALMA technical handbook)"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "1D Gaussian fitting to spectral line profiles",
  "failed_quote": "We made the line profiles of the SiO v = 1 ,J = 2 - 1 emission line from the channel maps and derived the LSR radial velocities from the line profiles with Gaussian fitting."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Compute Cartesian angular differences between 2017 and 2021 relative positions (Delta_X, Delta_Y) over the time baseline Delta_t = 3.917 years, convert to proper motion speed |V_prop| and position angle PA.",
  "failed_quote": "We obtained the angular differences between their positions relative to Sgr A* in 2017 and 2021 in Cartesian coordinate system, which are given by Delta_X = - (Delta_RA_2021 - Delta_RA_2017) (2) Delta_Y = Delta_Dec_2021 - Delta_Dec_2017. (3)"
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Compute Cartesian angular differences between 2017 and 2021 relative positions (Delta_X, Delta_Y) over the time baseline Delta_t = 3.917 years, convert to proper motion speed |V_prop| and position angle PA.",
  "failed_quote": "Then we determined the proper motions relative to Sgr A* of 35 SiO maser stars using the following formula; |V_prop| [km s^-1] = 38827 / Delta_t sqrt(Delta_X^2 + Delta_Y^2). (4)"
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Compute Cartesian angular differences between 2017 and 2021 relative positions (Delta_X, Delta_Y) over the time baseline Delta_t = 3.917 years, convert to proper motion speed |V_prop| and position angle PA.",
  "failed_quote": "The time difference between the observation epochs is Delta_t = 3.917 years."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "Delta_t = 3.917 years",
  "failed_quote": "The time difference between the observation epochs is Delta_t = 3.917 years."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Distance d = 8.2 kpc (1'' corresponds to 0.03975 pc or 1.224 x 10^17 cm)",
  "failed_quote": "Throughout this paper, we adopt d = 8.2 kpc as the distance to the Galactic center. 1'' corresponds to 0.03975 pc or 1.224 x 10^17 cm at the distance."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Compared derived proper motions of previously known stars (such as IRS7) with previously published proper motions.",
  "failed_quote": "The derived proper motions of stars detected in previous observations, such as that of IRS7 (17454004-2900228), are consistent with the previously derived proper motions (e.g. Tsuboi et al. 2022, Darling et al. 2023, Paine & Darling 2024)."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Combine proper motion speeds and LSR radial velocities in quadrature to obtain 3D space velocities V_space = sqrt(V_prop^2 + V_LSR^2), and compare as a function of projected distance r from Sgr A* against circular (sqrt(GM/r)) and parabolic/highly eccentric (sqrt(2GM/r)) Keplerian velocities.",
  "failed_quote": "We derived the space velocities of the SiO maser stars from these proper motions and the LSR radial velocities using V_space = sqrt(V_prop^2 + V_LSR^2)."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Combine proper motion speeds and LSR radial velocities in quadrature to obtain 3D space velocities V_space = sqrt(V_prop^2 + V_LSR^2), and compare as a function of projected distance r from Sgr A* against circular (sqrt(GM/r)) and parabolic/highly eccentric (sqrt(2GM/r)) Keplerian velocities.",
  "failed_quote": "The solid line curve indicates the orbital velocity of circular orbits, V = sqrt(GM/r), assuming that the mass of the GCBH is M = 4 x 10^6 M_sun. The dashed curve indicates the orbital velocity of extremely highly eccentric orbits, V = sqrt(2GM/r)."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "GCBH mass M = 4 x 10^6 M_sun",
  "failed_quote": "The solid line curve indicates the orbital velocity of circular orbits, V = sqrt(GM/r), assuming that the mass of the GCBH is M = 4 x 10^6 M_sun."
 },
 {
  "path": "software[0].used_for.evidence[1]",
  "value": "Calibration, continuum subtraction (uvcontsub), channel map and continuum imaging (tclean), and 2D Gaussian source fitting (imfit).",
  "failed_quote": "Before imaging in the the SiO maser lines, the continuum emission of Sgr A* and the surrounding continuum features were subtracted from the original data using the CASA task, uvcontsub (fitorder=0)."
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Subtracting continuum emission of Sgr A* and surrounding features from visibility data.",
  "failed_quote": "Before imaging in the the SiO maser lines, the continuum emission of Sgr A* and the surrounding continuum features were subtracted from the original data using the CASA task, uvcontsub (fitorder=0)."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "2D Gaussian fitting to determine ICRS positions of SiO maser stars and Sgr A*.",
  "failed_quote": "The positions in the ICRS coordinate system of the SiO maser stars are determined by the 2D Gaussian fitting to the star image in the channel maps using the CASA task, imfit."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Number of detected SiO v=1, J=2-1 maser stars = 37 dimensionless",
  "failed_quote": "We detected 37 SiO maser stars in the channel maps and derived their angular offsets relative to Sgr A* and LSR radial velocities."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Sgr A* RA (ICRS) on September 19, 2017 = 17h45m40.033456s hms",
  "failed_quote": "On the continuum maps mentioned above, the positions of Sgr A* in the ICRS coordinate system were measured to be (RA, Dec) ICRS = (17 h 45 m 40.s 033456 +- 0.s 000002, - 29 deg 00' 28.'' 22993 +- 0.'' 00002) at September 19, 2017"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Sgr A* Dec (ICRS) on September 19, 2017 = -29d00m28.22993s dms",
  "failed_quote": "On the continuum maps mentioned above, the positions of Sgr A* in the ICRS coordinate system were measured to be (RA, Dec) ICRS = (17 h 45 m 40.s 033456 +- 0.s 000002, - 29 deg 00' 28.'' 22993 +- 0.'' 00002) at September 19, 2017"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Sgr A* RA (ICRS) on August 19, 2021 = 17h45m40.032847s hms",
  "failed_quote": "and (RA, Dec) ICRS = (17 h 45 m 40.s 032847 +- 0.s 000005, - 29 deg 00' 28.'' 26277 +- 0.'' 00003) at August 19, 2021, respectively."
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Sgr A* Dec (ICRS) on August 19, 2021 = -29d00m28.26277s dms",
  "failed_quote": "and (RA, Dec) ICRS = (17 h 45 m 40.s 032847 +- 0.s 000005, - 29 deg 00' 28.'' 26277 +- 0.'' 00003) at August 19, 2021, respectively."
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Mean LSR velocity of SiO maser stars (V_LSR) = -24.9 km s^-1",
  "failed_quote": "The mean LSR velocity is V_LSR = - 24.9 +- 86.7 km s^-1."
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Average SiO v=1, J=2-1 line intensity in 2017 = 47.0 mJy",
  "failed_quote": "The average line intensities are 47.0 +- 43.6 mJy in 2017."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Average SiO v=1, J=2-1 line intensity in 2021 = 55.4 mJy",
  "failed_quote": "The average line intensities are 55.4 +- 52.0 mJy in 2021."
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Mean proper motion amplitude of SiO maser stars (|V_prop|) = 153.2 km s^-1",
  "failed_quote": "The mean proper motion amplitude is derived to be |V_prop| = 153.2 +- 83.3 km s^-1 (Cf. |V_prop| = 239.4 +- 127.7 km s^-1 for the NSC stars in Tsuboi et al. 2022)."
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Mean LSR velocity amplitude of SiO maser stars (|V_LSR|) = 66.1 km s^-1",
  "failed_quote": "While the mean amplitude of the LSR velocity is derived to be |V_LSR| = 66.1 +- 60.6 km s^-1."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "The spatial distribution and proper motions of the SiO maser stars are not correlated with the Mini-Spiral (MS) or the Circum Nuclear Disk (CND).",
  "failed_quote": "However, there does not seem to be a large number of SiO maser stars correlated with the MS, the CND, and Sgr A*."
 },
 {
  "path": "findings_qualitative[4].evidence[0]",
  "value": "Many 3D space velocities of the SiO maser stars approach or exceed the upper limit for bound Keplerian orbits around a 4 x 10^6 M_sun black hole, indicating they belong to the Nuclear Stellar Disk (NSD) rather than the Nuclear Star Cluster (NSC).",
  "failed_quote": "Many 3D velocities are near to or larger than the upper limit velocities for Kepler orbits around Sgr A*, whose mass is assumed to be 4 x 10^6 M_sun."
 },
 {
  "path": "findings_qualitative[4].evidence[1]",
  "value": "Many 3D space velocities of the SiO maser stars approach or exceed the upper limit for bound Keplerian orbits around a 4 x 10^6 M_sun black hole, indicating they belong to the Nuclear Stellar Disk (NSD) rather than the Nuclear Star Cluster (NSC).",
  "failed_quote": "These indicate that the SiO maser stars around Sgr A* are members of the Nuclear Stellar Disk rather than the NSC."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The dominance of transverse motion along the Galactic plane and 3D space velocities near or above the Keplerian escape limit indicate that the SiO maser stars around Sgr A* belong to the NSD rather than the NSC.",
  "failed_quote": "The mean proper motion amplitude is derived to be |V_prop| = 153.2 +- 83.3 km s^-1 (Cf. |V_prop| = 239.4 +- 127.7 km s^-1 for the NSC stars in Tsuboi et al. 2022). While the mean amplitude of the LSR velocity is derived to be |V_LSR| = 66.1 +- 60.6 km s^-1."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The dominance of transverse motion along the Galactic plane and 3D space velocities near or above the Keplerian escape limit indicate that the SiO maser stars around Sgr A* belong to the NSD rather than the NSC.",
  "failed_quote": "Many 3D velocities are near to or larger than the upper limit velocities for Kepler orbits around Sgr A*, whose mass is assumed to be 4 x 10^6 M_sun. These indicate that the SiO maser stars around Sgr A* are members of the Nuclear Stellar Disk rather than the NSC."
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "ALMA has a sharp synthesized beam, high sensitivity, a large FOV (67.5'' FWHM at 86.2 GHz), and simultaneously detects Sgr A* in continuum so star positions can be directly referenced to Sgr A* while radial velocities are easily obtained from the SiO maser line.",
  "failed_quote": "Moreover, the position of the stars can be measured directly by referencing the position of Sgr A* with ALMA, since ALMA can always detect Sgr A*."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Velocity integration width was set to 5 km s^-1 to improve sensitivity for detecting fainter stars and increase the sample size for statistical kinematics, and outer FOV limit was extended to primary beam attenuation of 0.2.",
  "failed_quote": "To improve the sensitivity, the velocity integration width of the channel map is set to Delta_V = 5 km s^-1."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Additional enclosed mass of M ~ 10^6 M_sun within the region to bind the high-velocity stars to the NSC was considered and rejected because such a large additional mass has not been observed in other observations.",
  "failed_quote": "To resolve the discrepancy with the observed space velocities, it is hypothesized that there may be additional mass in the region. Since the mass appears to accelerate the velocities of the stars by up to several 10 %, the required mass is expected to be as large as M ~ 10^6 M_sun."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Public archival data obtained from the ALMA Science Archive (https://almascience.nao.ac.jp/aq/).",
  "failed_quote": "We have obtained the archive data in the SiO J = 2 - 1 emission lines observed by the ALMA in 2017 and 2021 (#2016.1. 00940.S, PI Darling, J. and #2019.1.00292.S, PI Paine, J.) from the ALMA Science Archive (https://almascience.nao.ac.jp/aq/)."
 }
]
```
