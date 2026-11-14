# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...684A.107M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. Article ©ESO 2024
January 19, 2024

## **Optical tomography of the born-again ejecta of A 58**


B. Montoro-Molina [1], D. Tafoya [2], M. A. Guerrero [1], J. A. Toalá [3], and E. Santamaría [3]


1 Instituto de Astrofísica de Andalucía, CSIC, Glorieta de la Astronomía S/N, Granada, E-18008, Spain
e-mail: `borjamm@iaa.es`
2 Department of Space, Earth, and Environment, Chalmers University of Technology, Onsala Space Observatory, SE-3992 Onsala,
Sweden
3 Instituto de Radioastronomía y Astrofísica, Universidad Nacional Autónoma de México, Antigua Carretera a Pátzcuaro 8701,
Ex-Hda San José de la Huerta, Morelia 58089, Michoacán, Mexico


January 19, 2024


**ABSTRACT**


In a born-again planetary nebula (PN), processed H-deficient material has been injected inside the old, H-rich nebula as a result of
a very late thermal pulse (VLTP) event. Long-slit spectra have been used to unveil the chemical and physical differences between
these two structures, but the ejection and shaping processes remain still unclear. In order to peer into the morpho-kinematics of the
H-deficient ejecta in the born-again PN A 58, we present the first integral field spectroscopic observations of a born-again PN as
obtained with GTC MEGARA. We detect emission from the Hα, He i, [O iii], [N ii] and [S ii] emission lines, which help us unveil the
expansion patterns of the different structures. In combination with ALMA and _Hubble Space Telescope_ data we are able to produce
a complete view of the H-deficient ionized and molecular ejecta in A 58. We propose an hourglass structure for the ionized material
that embraces molecular high-velocity polar components, while bisected by an expanding toroidal molecular and dusty structure. Our
results leverage the role of a companion in shaping the VLTP ejecta in this born-again PN.


**Key** **words.** (ISM:) planetary nebulae: general – (ISM:) planetary nebulae: individual: PN A66 58 (a.k.a. PN G037.5−05.1) –
Techniques: imaging spectroscopy — Stars: evolution — Stars: winds, outflows



**1.** **Introduction**


Born-again planetary nebulae (PNe) are objects whose central stars (CSPNe) have experienced a very late thermal pulse
(VLTP) when descending the white dwarf (WD) cooling track
(Schönberner 1979; Iben et al. 1983). These thermonuclear explosive events are rare, given that the VLTP is produced when
the outer He layer of the WD reaches unique conditions to ignite into C, engulfing the remnant H on the surface. As a consequence, this process injects H-deficient material inside an old, Hrich PN, creating double-shell structure (e.g., Toalá et al. 2021b;
Rodríguez-González et al. 2023).
Models predict that the duration of the VLTP is short (10–
200 yr; Miller Bertolami et al. 2006), which makes it difficult to identify born-again PNe. This would explain that only a
handful of objects have been identified as born-again PNe, being A 30, A 58, A78 and the Sakurai’s Object the most studied cases (see, e.g., Jacoby 1979; Nakano et al. 1996; Clayton
et al. 2006). Spectroscopic studies have helped unveil the extreme abundances differences between the born-again ejecta and
those of the outer H-rich nebula (Jacoby & Ford 1983; Hazard
et al. 1980; Manchado et al. 1988; Montoro-Molina et al. 2022,
2023; Wesson et al. 2008; Simpson et al. 2022).
The kinematics of the H-deficient ejecta is far from simple.
High-dispersion optical spectroscopy works of the most evolved
objects of this class, A 30 and A 78, found that the H-deficient
material in these born-again PNe has velocities ranging from
40 km s [−][1] up to 500 km s [−][1] (Meaburn & Lopez 1996; Meaburn
et al. 1998). In addition, _Hubble_ _Space_ _Telescope_ ( _HST_ ) observations show that the inner structures of the H-deficient ejecta
in A 30, A 58 and A 78 have bipolar morphology consisting of



a disk-like (or toroidal) structure and a pair of bipolar ejections (Borkowski et al. 1993, 1995; Clayton et al. 2013). The
H-deficient clumps have a tadpole (clump-head and tail) morphology, which is indicative of the complex interactions of this
material with the photoionization flux and the current fast wind
from the CSPN (Fang et al. 2014; Rodríguez-González et al.
2022).
The disk-jet morphology of the H-poor ejecta in born-again
PNe is suggestive of the action of binary systems. Moreover
born-again PNe are listed among the PNe with the highest abundance discrepancy factor, which is interpreted as caused by the
evolution through a binary system (Wesson et al. 2018). The
C/O abundances ratio of born-again ejecta seems also consistent
with those of novae (Lau et al. 2011), although, once that the C
trapped in dust is accounted for, the C/O ratio is actually more
consistent with the predictions of a VLTP event of single stellar
evolution models (see Toalá et al. 2021a, for the case of A 30).
Although VLTP events and binary systems would seem unrelated, a common envelope phase with a binary companion after
the VLTP event has been recenlty invoked to explain the bipolar structures and their specific kinematic signatures (RodríguezGonzález et al. 2022).
It is thus clear that an appropriate determination of the kinematics of the H-deficient ejecta is most needed to peer into
the single versus binary scenarios. Thus far, the best determination for the youngest born-again PNe have been achieved
studying the molecular emission. Atacama Large Milimeter/submillimeter Array (ALMA) observations of the Sakurai’s
Object and A 58 have shown that in both cases the molecular
CO emission exhibit bipolar outflows protruding from an expanding toroidal structure; in the Sakurai’s Object the depro

Article number, page 1 of 11

_A&A proofs:_ manuscript no. Article



jected disk velocity is 53 km s [−][1] and that of the bipolar outflow
∼1000 km s [−][1] (Tafoya et al. 2023), while in A 58 the disk is
estimated to expand at a velocity of 90 km s [−][1] and its bipolar
outflow at 280 km s [−][1] (Tafoya et al. 2022).
In this paper we start a series of works to study the morphokinematics of the H-deficient ejecta of a sample of born-again
PNe using the unrivaled capabilities of high-dispersion integral
field spectroscopic (IFS) observations obtained with the MultiEspectrógrafo en GTC de Alta resolución para Astronomía
(MEGARA; Gil de Paz et al. 2018) at the 10.4 m Gran Telescopio Canarias (GTC). Here we present results for A 58 that in
conjunction with the available molecular emission detected by
ALMA provide an unprecedented view of this born-again PN.
This paper is organized as follows. In Section 2 we describe
our observations and their reduction. The analysis procedure of
the data is presented in Section 3. The discussion of our results
in presented in Section 4. Finally, our conclusions are presented
in Section 5.


**2.** **Observations and data Reduction**


_2.1._ _Integral Field Spectroscopy_


IFS observations of A 58 were obtained on 2022 June 21 (Program ID 24-GTC29/22A) using MEGARA at the GTC of the
Observatorio de El Roque de los Muchachos (ORM, La Palma,
Spain). The Integral Field Unit (IFU) mode, also called Large
Compact Bundle (LCB), was used. It consists of 567 hexagonal spaxels of 0 [′′] . 62 in diameter resulting in a field of view
(FoV) of 12 [′′] . 5×11 [′′] . 3. The volume phase holographics VPH443MR (MR-UB), VPH481-MR (MR-B), and VPH665-HR (HR-R)
were used as dispersion elements. The details of the observations, including spectral properties, exposure times, and observing conditions, are presented in Table 1.
The raw MEGARA data were reduced following the Data
Reduction Cookbook (Pascual et al. 2019) using the _megaradrp_
v0.10.1 pipeline released on 2019 June 29. This pipeline applies
sky and bias subtraction, flat-field correction using halogen internal lamps, wavelength calibration, and spectra tracing and extraction. The final output is a FITS file that contains the sciencecalibrated row-stack-spectra (RSS) for each fiber, with metadata
of the relative fiber positions to the IFU center. This RSS FITS
file is converted into a 52×58 map of 0.2 arcsec pix [−][1] on the spatial dimension and 4300 spaxel along the spectral axis using the
regularization grid task _megararss2cube_ . The flux calibrations
were performed using observations obtained immediately after
those of A 58 of the spectrophotometric standard stars HR 7950,
HR 7596, and HR 4963 for the VPH665-HR, VPH481-MR, and
VPH443-MR, respectively.


_2.2._ _Long-slit Echelle Spectroscopy_


High-dispersion spectroscopic observations of A 58 were obtained on 2002 June 23 using the echelle spectrograph on the
Cerro Tololo Interamerican Observatory (CTIO) 4 m Víctor
Blanco (a.k.a. Blanco) telescope. The spectrograph was used in
its long-slit mode with the 6563/75 narrow-band filter, whose
≈75 Å in FWHM bandwidth isolates the echelle order including
the Hα and [N ii] λλ6548,6584 emission lines. The 79 line mm [−][1]
echelle grating and the long-focus red camera were used, resulting in a reciprocal dispersion of 3.4 Å mm [−][1] . The data were
recorded with the SITe 2K CCD #6, whose pixel size of 24 µm
provides a spatial scale of 0 [′′] . 26 and a spectral sampling of 0.081
Å pixel [−][1] (i.e., 3.7 km s [−][1] pixel [−][1] ) along the dispersion direction.


Article number, page 2 of 11



The slit has an unvignetted length of 3 arcmin and its width was
set to 1 [′′] . 4, resulting in an instrumental resolution of 9.1 km s [−][1] .
Two individual 750 s exposures were obtained with the slit oriented along a position angle (PA) of 50 [◦], i.e., along the central
ejecta. The angular resolution, determined by the seeing measured at the DIMM, was ≈1 [′′] . 0.
The spectra were reduced using standard IRAF (Tody 1993)
routines for two-dimensional spectra. The wavelength scale and
geometrical distortion were corrected using a two-dimensional
fit to an arc exposure obtained using Th-Ar calibration lamps immediately after the science exposure. The deviation of the residuals of the two-dimensional fit to the Th-Ar arc is found to be
better than ≈0.004 Å (0.2 km s [−][1] ). The telluric emission lines,
which includes mostly OH emission lines, but also the geocoronal Hα line, were removed by fitting and subtracting the background using low-order polynoms. Before this procedure, the telluric lines were used to confirm the accuracy of the wavelength
calibration to be better than 0.3 km s [−][1] using their theoretical
wavelengths (Osterbrock et al. 1996).


_2.3._ _Milimeter/submillimeter Interferometric Observations_


We retrieve high angular resolution (0 [′′] . 07 × 0 [′′] . 1) observations
obtained with the ALMA used to detect the continuum and
molecular emission from A 58. These observations correspond
to project 2019.1.01408.S (PI: D. Tafoya) and their details can
be found in Tafoya et al. (2022).


**3.** **Data analysis**


_3.1._ _Spectral Line Profiles_


The GTC MEGARA observations detected emission
from the [O iii]λλ4363, 4959, 5007, [N ii]λλ6548, 6584,

[S ii]λλ6716, 6731, He i λ6678, He ii λ4686, Hβ and Hα
emission lines. We note that the C ii 4267 Å emission line is not
detected in the VPH433-MR observations at a 3-σ upper limit
of 3.6×10 [−][16] erg cm [−][2] s [−][1] .
Spectral profiles of key emission lines of A 58 are presented
in Fig. 1. The profiles of the H-poor ejecta (red dashed histograms in Fig. 1) have been extracted from a circular region 1 [′′] . 8
in radius around the brightest region. These spectra include significant contamination from the surrounding old, H-rich nebula.
This emission is estimated by averaging four apertures located
in each quadrant of MEGARA’s FoV with the same size as that
used for the central ejecta. The emission line profiles from the
surrounding nebula (gray solid histograms in Fig. 1) present a
well-marked double-peak structure in the [N ii] and H i Balmer
lines, as well as in the fainter and noisier [S ii] emission lines.
The [O iii] emission line seems to be consistent with a doublepeak profile, but the components are broader and blended. Although this could be attributed to the lower spectral resolution of
the blue MR-B VPH ( _R_ ≃ 13200) that registered this line compared to the red HR-R VPH ( _R_ ≃ 20050), the similarity of the
Hβ (not shown here) and Hα nebular profiles implies that the
components of the nebular [O iii] emission line are truly broader.
Finally the [O iii] λ4363 and He lines do not present emission
from the surrounding old nebula.
The blue component of the different emission lines from the
outer nebula is consistently narrower and more intense than its
red counterpart. If the expansion velocity of the nebula, _V_ exp,
is assumed to be half the separation between the red and blue
components, we derive velocities of 30 and 35 km s [−][1] for Hα
and [N ii], respectively, which are consistent with the expansion

B. Montoro-Molina et al.: Optical tomography of the born-again ejecta of A 58


**Table 1.** Details of the GTC MEGARA observations of A 58 analyzed in this work.


Dispersion Element R Spectral Range Exposure Time Moon Sky Airmass Seeing
(Å) (s) (arcsec)

VPH665HR-R 20050 6405.6–6798.0 3 × 300 Dark Clear 1.49 0.9

VPH481MR-B 13200 4585.7–5025.1 3 × 600 Dark Clear 1.43 0.9

VPH443MR-UB 13050 4226.4–4625.8 6 × 900 Dark Clear 1.57 0.9



200 0 200 400 600



200 0 200 400 600





Velocity Offset (km s 1 )

200 0 200 400 600

































Velocity LSR (km s 1 )





**Fig. 1.** GTC MEGARA emission line profiles of the central ejecta of A 58 (red dashed line) extracted from a 1 [′′] . 8 in radius circular region, and
surrounding nebula (grey solid line) averaged from four regions of the same size located at the corners of the MEGARA FoV. The [N ii] λ6584,
Hα, [O iii] λ5007, and [S ii] λ6716 emission line profiles of the central ejecta include notable contribution from the surrounding nebula. The
surrounding nebula emission profiles of these lines have been subsequently subtracted to obtain the net emission line profiles of the central ejecta
(black solid line), whereas for the He i λ6678 and [O iii] λ4363 emission line profiles only a constant level representative of the continuum emission
has been subtracted. As described in the text the subtraction of the emission from the surrounding nebula is not perfect most likely given its non
uniform surface brightness. The horizontal line marks the continuum level, while the vertical line marks the systemic velocity of +103 km s [−][1] of
the surrounding nebula.



velocities of these emission lines derived from the CTIO longslit echelle data.


Once the contribution of the old surrounding nebula is subtracted from the spectrum of the aperture encompassing the central ejecta, the remaining emission shall be attributed to net emission from that central ejecta (solid black lines in Fig 1). We note,
however, that some residual emission subsists, as, for instance,
the blue-shifted peak at _V_ LSR ≈ 60 km s [−][1] in the [N ii] emission line and the narrow components at _V_ LSR ≈ 60 km s [−][1] and
≈ 130 km s [−][1] in Hα. These residuals most likely result from spatial variations of the emission of the surrounding old nebula (see,
e.g., figure 2 in Guerrero & Manchado 1996).


The spectral profile from the central ejecta is asymmetric in
all emission lines shown in Fig. 1. The emission peaks bluewards, very notably in the [N ii] and [O iii] emission lines at
_V_ LSR ≈−20 km s [−][1] . In these emission lines, the line profiles
show wings that extends in the range −200 km s [−][1] ≲ _V_ LSR ≲
+300 km s [−][1] . The overall properties of these emission lines are
very similar to those presented by Pollacco et al. (1992), although the data presented here have higher signal-to-noise ratio



and reveal more clearly the line wings. Otherwise only the blue
component is detected in the Hα, [S ii], and He i emission lines.
We emphasize that the non-detection of the He ii λ4686 emission
line discards the possible contribution of He ii λ6560 to the emission bluewards of Hα, which is thus confidently attributed to the
ejecta. This is the first time that the Hα emission of the bornagain ejecta is unambiguously detected, although a revision of
figure 2 in Pollacco et al. (1992) reveals arguable evidence for
its detection.


3.1.1. Systemic velocities of A 58 and its central ejecta


Considering the average of the nebular red and blue components
to be the systemic velocity, _V_ sys, we derive velocities in the Local Standard of Rest (LSR) from the CTIO echelle data of 101.8
km s [−][1] and 104.4 km s [−][1] for the Hα and [N ii] lines, respectively.
An average of 103 km s [−][1] can thus be adopted for the systemic
velocity of the old surrounding nebula, which is marked by a
vertical dashed line in the different panels of Fig. 1. These values are found to be consistent to the observed dips in the GTC


Article number, page 3 of 11

13.5


14.0


14.5


15.0


15.5


16.0

|-250:-200|Col2|-200:-150|-150:-100|-100:-50|Col6|Col7|
|---|---|---|---|---|---|---|
|-250:-200|-250:-200|-200:-150|-150:-100|-100:-50|||
|-50:0|-50:0|0:50|50:150|150:200|150:200|150:200|
|-50:0|-50:0|0:50|50:150|150:200|150:200||
|-50:0|-50:0|0:50|50:150|150:200|150:200||
|200:250|200:250|250:300|300:350|350:400|350:400|350:400|
|200:250|200:250|250:300|300:350|350:400|350:400||
|200:250|200:250|250:300|300:350|350:400|350:400||



14.50


14.75


15.00


15.25


15.50


15.75


16.00


16.25



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



_A&A proofs:_ manuscript no. Article


[O III] Velocity(LSR) Maps


0.0 2.5 5.0 7.5 10.0 12.5
Offset (arcsec)

[N II] Velocity(LRS) Maps


|-250:-200|-200:-150|-150:-100|-100:-50|Col5|
|---|---|---|---|---|
|-50:0|0:50|50:150|150:200|150:200|
|200:250|250:300|300:350|350:400|350:400|



0.0 2.5 5.0 7.5 10.0 12.5
Offset (arcsec)


**Fig.** **2.** GTC MEGARA VPH481-MR [O iii] λ5007 (top) and VPH665-HR [N ii] λ6584 (bottom) channel maps of A 58. Each map shows the
integrated emission in the channles within the LSR velocity range labeled on the upper right corner of each map. Contours corresponding to 2.4%,
5%, 11%, 23%, and 48% of the emission peak (1.71×10 [−][14] and 1.61 × 10 [−][15] for [O iii] and [N ii], respectively) are overlaid in all maps (solid white
lines). The approximate location of the central star is marked by a white star.



MEGARA Hα and [N ii] λ6584 spectral profiles of the outer
nebular shell shown in Fig. 1.


The only previous high-dispersion spectra of A 58, obtained
with the Anglo-Australian Telescope Coudé échelle spectrograph (UCLES), implied a systemic velocity in the LSR of its
outer nebula of 86 km s [−][1] (corresponding to a heliocentric ve

Article number, page 4 of 11



locity of 70 km s [−][1], Pollacco et al. 1992). This value is not associated to a specific emission line by the authors, neither there is
a description of the slit position, besides the information on the
2 [′′] -wide slit. Due to the broad slit width, the nebular emission in
the Hα and [N ii] emission lines is more prominent than the profile shown in Fig. 1, making the double-peak quite noticeable.

B. Montoro-Molina et al.: Optical tomography of the born-again ejecta of A 58



Later on, Clayton et al. (2013) analyzed the spectra presented by
Pollacco et al. (1992) and derived a systemic velocity in the LSR
of 96 km s [−][1] (or a heliocentric velocity of 80 km s [−][1] ).
The differences between the systemic velocity derived here
and those reported by Pollacco et al. (1992) and Clayton et al.
(2013) are 17 km s [−][1] and 7 km s [−][1], respectively. It is important to
note that the original spectra presented by Pollacco et al. (1992)
were not available to Clayton et al. (2013), who used a digitized
version of the figures of the spectra and therefore adopted the
same wavelength calibration. If we compare the dispersion of
the UCLES and CTIO spectra, the spectral dispersion of the latter is approximately ten times higher than that of the UCLES
spectra. The calibration and analysis of the CTIO data seems
very reliable, as described in Section 2.2. Therefore the value of
103 km s [−][1] presented here is preferred for the systemic velocity
of the outer shell of A 58.

Regarding the central ejecta of A 58, it is not possible to derive a systemic velocity from the optical emission lines as their
profiles are highly asymmetric, most likely due to the strong extinction of this region (Montoro-Molina et al. 2022) absorbing
preferentially the red component. On the other hand the radio
emission of molecular material, which is mostly unaffected by
the extinction, allows a more reliable determination of the systemic velocity of the recent ejecta. The spectral profile of the CO
( _J_ = 3 → 2) emission from the central region of A 58 detected
by the 12 m Atacama Pathfinder Experiment (APEX) implied
an average velocity in the LSR of 96±11 km s [−][1], which was interpreted as the systemic velocity of the molecular gas around
V605 Aql (Tafoya et al. 2017) in agreement with the value proposed by Clayton et al. (2013). We note, however, that the quality
of the APEX spectral profile of the CO ( _J_ = 3 →2) emission line
is limited. The subsequent ALMA spectral profiles of the CO
( _J_ = 3 →2), HCN ( _J_ = 4 →3), and HCO [+] ( _J_ = 4 →3) emission
line profiles presented by Tafoya et al. (2022) are of higher quality, but these were not used to derive new values of the systemic
velocity. Instead, the authors conclude that the systemic velocity
derived from APEX were consistent with the double-peak symmetric spectral profiles detected in the ALMA observations.
There is thus a difference of 7 km s [−][1] between the systemic
velocity of the H-rich outer nebula derived from the CTIO optical data and that of the H-poor born-again ejecta derived from the
APEX radio data, but these can be considered consistent given
the uncertainties.

Indeed the dips between the blue and red components of the
CO ( _J_ = 3 →2) and HCO [+] ( _J_ = 4 →3) emission lines detected by ALMA are suggestive of a value of the systemic velocity slightly larger than that derived from APEX data. We will
hereafter consider the systemic velocity of A 58 and the H-poor
ejecta around V605 Aql to be 103 km s [−][1] . For this systemic velocity, the peaks of the H-poor ejecta [N ii] and [O iii] emission
line profiles are shifted by ≈−120 km s [−][1] with respect to the
systemic velocity, and their wings extend ≈−300 km s [−][1] and
≈ +200 km s [−][1] .


_3.2._ _Channel Maps_


The GTC MEGARA data cube also allows obtaining spatial information for each spectral channel. The channel maps of the
bright [O iii] λ5007 and [N ii] λ6584 emission lines in the central ejecta of A 58 are shown in Fig. 2. Each map is obtained by
combining channels within a velocity range of 50 km s [−][1], except
those around the systemic velocity including the nebular emission that have been computed for a velocity range of 100 km s [−][1] .



Fig. 2 reveals a trend in the spatial location of the emission
from the born-again ejecta of A 58. The bluest velocity channels,
in the range from −250 to −50 km s [−][1], show emission Northeast of the CSPN, whereas the emission of the reddest velocity
channels in the range from +50 to +350 km s [−][1] departs notably
towards the Southwest.


3.2.1. Relative location of V605 Aql and the optical outflow


The CSPN of A58, V605 Aql, has not been visible since 1923,
when it underwent a brightening to fade away immediately afterwards (Seitter 1985; Harrison 1996). Ninety years later, Clayton et al. (2013) estimated its position at R.A.=19 [h] 18 [m] 20 [s] .538,
DEC.=+1°46 [′] 58 [′′] . 74 under the reasonable assumption that the
_HST_ F547M image was dominated by the C iv Wolf–Rayet emission feature in the spectrum of V605 Aql, therefore its peak
emission revealing its position. The accuracy of these coordinates, however, is affected by the intrinsic limitations of _HST_
to assign absolute positions. Indeed the comparison of the _HST_
coordinates of V605 Aql with the position of the CO molecular
emission derived from ALMA observations, which have higher
absolute precision in establishing coordinates, revealed a notorious displacement between them.
At any rate there is no information on the absolute positioning of the MEGARA data cubes, which compromises a comparison of the spatial properties of the optical outflow with the _HST_
and ALMA observations. To compensate this lack of information and to allow the spatial comparison of the _HST_, ALMA and
MEGARA observations, the stellar continuum in the MEGARA
observations can be used to determine the position of V605 Aql.
Continuum images were thus built from the VPH481-MR and
VPH665-HR data cubes collapsing spectrally all channels with
no line emission contribution, avoiding the noisiest ones as well.
The position of V605 Aql was then determined by adjusting a
two-dimensional Gaussian to the stellar emission located near
the center of the image. This procedure revealed an offset between the position of the star in the VPH481-MR and VPH665HR data cubes of 1.3 pixels, i.e., 0 [′′] . 26, which is most likely due
to irregularities in the surface and/or exact positioning of these
two VPHs.

It is worth noting that we also explored the possibility of assigning the position of the centroid of the emission at the systemic velocity to V605 Aql. However, this method revealed a
quite noticeable shift with the position of the stellar continuum.
Apparently the emission at the systemic velocity does not correspond to the location of the CSPN, which reveals a far from
simple 3D physical structure of the ejecta.


_3.3._ _Boosting the Tomography Spatial Resolution_


The spatial resolution of the GTC MEGARA data is limited by
the ≈0 [′′] . 9 seeing during the observations and the coarse 0 [′′] . 62 in
diameter spaxel sampling, which results in a spatial resolution
≈1 [′′] . 1. Otherwise the spectral resolution allows investigating the
spatial location of the born-again ejecta at different velocities.
The high S/N achieved in the MEGARA data actually allows
increasing the accuracy of the spatial location of the emission
at each velocity channel by a factor ≈10 by the determining the
position of the centroid of the optical emission through a twodimensional Gaussian fit (Condon 1997).
In the top panel of Fig. 3 we present both the centroids and
the FWHMs (represented as ellipses) of the Gaussian resulting
from the fittings for the [O iii] (left) and [N ii] (right) emission


Article number, page 5 of 11

1.0


0.5


0.0


0.5


1.0


1.0


0.5


0.0


0.5


1.0



_A&A proofs:_ manuscript no. Article


300


1.0


200


0.5


100



0.0


0.5


1.0


1.0


0.5


0.0


0.5


1.0



0.60.6 0.4 0.2 0 ~~.~~ 0 0.2 0.4 0.60. ~~6~~

RA offset (arcsec)



1.0 0.5 0.0 0.5 1.0

RA offset (arcsec)



1.0 0.5 0.0 0.5 1.0

RA offset (arcsec)



1.0 0.5 0.0 0.5 1.0

RA offset (arcsec)


0.6 0.6



1.0 0.5 0.0 0.5 1.0

RA offset (arcsec)


0.6 0.6



0.60.6 0.4 0.2 0.0 0.2 0.4 0.60. ~~6~~

RA offset (arcsec)



0


100


200


300


300


200


100


0


100


200


300


100


75


50


25


0


25


50


75


100



300


200


100


0


100


200


300


300


200


100


0


100


200


300


100


75


50


25


0


25


50


75


100



**Fig. 3.** Top panels shows the positions of the centroids and the FWHM (ellipses contours) of 2-dimensional Gaussian fits to the emission of [O iii]
λ5007 (left panels) and [N ii] λ6584 (right panels) at each spectral channel of the outflow of A 58 with a color-coded according to their velocity
with respect to the _V_ sys (see text for details). The middle panel show the top panels superimposed over the _HST_ [O iii] λ5007 (left) and [N ii] λ6584
(right) images of A 58 obtained in 2009 (PI: G. Clayton; Program ID: 11985). The bottom panel present the spatio-kinematic distribution of CO
( _J_ = 3 → 2) obtained with ALMA (see figure 5 in Tafoya et al. 2022). In these panels the centroids in the velocity range −100 km s [−][1] ≃ V offset
≃+100 km s [−][1] are plotted in green whereas centroids with velocities < −100 km s [−][1] and - +100 km s [−][1] are represented by blue and red filled
dots, respectively. The approximate location of the central star is marked by a black, red and yellow stars in the top, middle and bottom panels,
respectively.


Article number, page 6 of 11

B. Montoro-Molina et al.: Optical tomography of the born-again ejecta of A 58



lines, with the position of V605 Aql marked using a ⋆ symbol.
These fittings were conducted for channels within the LSR velocity range from −250 to +350 km s [−][1] . Channels with associated centroids located more than 1 [′′] away from the position of
V605 Aql or with Gaussian FWHM exceeding 1 [′′] . 5 in any of its
axes were excluded. The centroids and FWHMs are represented
with a color code indicating their velocity with respect to the
adopted systemic velocity of +103 km s [−][1] .
The spatial distribution of the centroids provides a clearer
representation of the trend hinted in Fig. 2. The red-shifted emission shifts notably towards the southeast (SE) direction, while
the blue-shifted emission moves towards the northeast (NE) direction, which is more pronounced for [O iii] than for [N ii]. Furthermore, the [O iii] emission exhibits a much more neat structure than that of [N ii], with centroids of velocity channels ranging from −200 to +80 km s [−][1] with respect to the systemic velocity consistently oriented along a specific direction, whereas
the centroids of the [N ii] emission are more widely scattered,
covering a slightly broader region around the central star. This
dispersion cannot be completely attributed to the lower S/N ratio
of this line, but more likely to a broader spatial distribution of
the [N ii] emission, may be located outside that of [O iii].
The spatial behavior of the [O iii] emission of the highest
velocity channels is noteworthy. The centroids trace a peculiar
loop, moving back towards the position of the CSPN first, shifting then to the northwest (NW) direction, and finally receding
back to a lesser extent to the northeast (NE) direction. Similar
trend is not observed for the red-shift emission, which seems to
simply move away with increasing velocity. This is further discussed in Section 4.
The middle panels of Fig. 3 show the _HST_ [O iii] and [N ii]
images with the MEGARA centroids and FWHMs of the corresponding top panel superimposed for comparison. The location
of the CSPN was set at the peak of the [O iii] image as settled
by Clayton et al. (2013) based on the _HST_ F547M continuum
image. The emission observed from the ejecta by MEGARA
is consistent with the emission from the _HST_ images, although
the emission in the MEGARA maps appears to cover a slightly
smaller region than in _HST_ . This is somehow unexpected because the expansion of the ejecta ≃10 mas yr [−][1] (Clayton et al.
2013) implies an even larger size of the emission from the time
lapse ≈13.3 years between the _HST_ images (March 2009) and
the MEGARA observations (June 2022).
Finally the lower panels of Fig. 3 show the CO ( _J_ = 3 →2)
first momentum image presented by Tafoya et al. (2022) overplotted by the MEGARA [O iii] and [N ii] centroids presented in
the upper panels. To establish a morpho-kinematic parallelism
between the centroids obtained and the disk-jet scenario described by this author, the color code was modified. Centroids
with system velocities from −100 to +100 km s [−][1], in the range of
the molecular material at the disk, are represented as filled green
points, while centroids below −100 and above +100 km s [−][1] are
shown in blue and red, respectively. The color code reveals that
those centroids of the [O iii] emission line presumed to belong to
the disk are actually aligned along a distinct direction, PA=60 [◦],
while those at higher velocities deviate from this orientation.
This pattern is more evident in Fig. 4, where the positionvelocity diagrams of the centroids are displayed along two distinct directions: PA=60 [◦] (parallel to the disk) and PA=150 [◦] (perpendicular to it). A dashed horizontal line has been added at the
position of the CSPN and a vertical line for _V_ sys = +103 km s [−][1] .
In the direction of PA=60 [◦] (upper panel), it can be observed that,
within the velocity range of −100 to +140 km s [−][1] in the LSR system, the centroids remain relatively flat around zero. For veloci

|300|200 100 0 Velocity Offset (km|100 200 m s )|Col4|
|---|---|---|---|
|||[O III]<br>[N II]||
|||[O III]<br>[N II]|0<br>0|
|P|A 60|||



|300|200 100 0|100 200|Col4|Col5|
|---|---|---|---|---|
|||||0|
|PA|150||||
|200<br>100<br>0<br>100<br>200<br>Velocity LSR (km s<br>1)|200<br>100<br>0<br>100<br>200<br>Velocity LSR (km s<br>1)|200<br>100<br>0<br>100<br>200<br>Velocity LSR (km s<br>1)|200<br>100<br>0<br>100<br>200<br>Velocity LSR (km s<br>1)|200<br>100<br>0<br>100<br>200<br>Velocity LSR (km s<br>1)|


**Fig. 4.** Position-velocity (PV) plots in the [O iii] λ5007 (red dots) and

[N ii] λ6584 (blue dots) of the CSPN of A 58 along the PA=60 [◦] and
PA=150 [◦] . Positions have been obtained using a 2-dimensional Gaussian fit of the emission at each spectral channel (see text for details).
The x-axis are showed in LSR system (bot) and respect to the systemic
velocity (top) for both panels. The systemic velocity of the ejecta and
the location of the CSPN are marked by vertical and horizontal dashed
lines, respectively.


ties below −140 and above +160 km s [−][1], there is only a minimal
displacement of 0 [′′] . 2 relative to the position of the CSPN.


**4.** **Discussion**


_4.1._ _Physical Structure of the H-poor Ejecta of A 58_


The physical structure of the H-poor ejecta of A 58 has been subject of different st ~~u~~ dies in the framework of the born-again phenomenon. Pollacco et al. (1992), Guerrero & Manchado (1996),
and Clayton et al. (2013) investigated it from its optical emission, but these studies are hampered by the high and spatially inhomogeneous extinction. Otherwise the radio and ~~s~~ ub-mm emission is much less prone to absorption (Tafoya et al. 2017, 2022).
Tafoya et al. (2022) proposed a model for the physical
structure of the molecular gas based on the high-resolution
CO (J=3→2) emission detected with ALMA. The model consisted of a radially expanding disk-like or toroidal structure tilted
along a PA of 63 [◦] with an inclination angle _i_ ≈ 60 [◦] with the plane
of the sky and an expansion velocity up to 80 km s [−][1], and two
high-velocity components (HVCs) orthogonal to the disk with
velocities −140 ≲ _V_ offset ≲ −100 and +100 ≳ _V_ offset ≳ +140.
According to this model based on the CO (J=3→2) spatiokinematic information, the redshifted emission from the disk is
found towards the NE of the CSPN, while the blueshifted emission is found towards the SW. This is exactly the opposite to the
spatial distribution of the [O iii] and [N ii] emission (Fig. 3), thus
indicating that the molecular disk is not emitting in the optical


Article number, page 7 of 11



Velocity Offset (km s 1 )



200 100 0 100 200 300

the SHAPE mesh model. For comparison the right panel of Fig. 5 in Tafoya et al. (2022) is shown in the upper right corner of this panel. (bottom)
_HST_ [O iii] image (left) and synthetic image (right). The [O iii] synthetic image is computed from the ionized bipolar outflows. The molecular disk
does not contribute to the emission, but it rather absorbs the optical emission behind it, which is accounted for adopting an ad hoc emission law
for the ionized material See Section 4.1 for details.



range, or at least, it is not the dominant structure. The spatial orientation of the CO HVCs is otherwise consistent with that of the

[O iii] and [N ii] emission lines, but the CO HVCs exhibit noticeably lower velocities, in the range from −140 to +140 km s [−][1],
to those revealed by the optical emission lines (see Fig. 1), in
the velocity range from −300 up to +200 km s [−][1] . The detailed
spatial distributions of the CO HVCs and optical emission lines
neither agree, with the redshifted optical emission being at the
edge of the disk, further away from the CSPN than the corresponding CO HVC, whereas the blueshifted optical emission is
generally located closer to the central star than the HVC. The velocity and spatial differences between the molecular and ionized
components of the ejecta of A 58 suggest that they do not share
the same physical structure.


Elaborating on the high-dispersion spatially-unresolved
spectra presented by Pollacco et al. (1992) and using highresolution multi-epoch _HST_ WFPC2 images, Clayton et al.
(2013) proposed a sketch for the physical structure of the optical ejecta of A 58. This model consisted of a central disk-like
or torus and material moving away from the CSPN perpendicular to the disk, very alike the model proposed for the molecular
component by Tafoya et al. (2022). This structure was further
geometrically simplified, assuming that the ejecta behaved as
an expanding sphere and adopting an extinction that depended
on the azimuthal coordinate within it with respect to the line of
sight. Although the model reasonably reproduces the emission
profile of the spectra, it does not provide information on the ac

Article number, page 8 of 11



tual morphology of the ejecta. The variations in the MEGARA
centroids of [O iii] and [N ii] (Fig. 3) do not follow that expected
from a simple spherical model, although Clayton et al. (2013)
noted variations in the profiles of these emission lines that attributed to small-scale dust inhomogeneities or material clumps.
These indentations in the emission line profiles are otherwise not
present in our higher-quality spectra (Fig. 1). Finally, the symmetric high-velocity ejecta arising from the innermost regions
of A 58 sketched by Clayton et al. (2013) requires the spatial
location of blue- and red-shifted velocity channels with similar
offset velocity to be distributed symmetrically at both sides of
the CSPN, with the systemic velocity at its position, which is
not the case (Fig. 3).


The discrepancies of the predictions of the model presented
by Clayton et al. (2013) with the MEGARA observations and the
lack of correspondence between the molecular and ionized gas
indicate that the physical structure of the latter is rather complex.
We here propose a model, whose schematic representation is
shown in Figure 5, that includes the different molecular and ionized gas components of the H-poor ejecta of A 58. The upper-left
panel of this figure shows a spatio-kinematic model created with
the software SHAPE (Steffen et al. 2011) consisting of a bipolar
structure and a radially expanding disk inclined at an angle of
_i_ = 63 [◦] ± 4 [◦] with respect to the line of sight. These structures,
oriented along a PA of 63 [◦] (as proposed by Tafoya et al. 2022),
produce the image shown in the upper-right panel of the figure.
The mesh model shows the combination of the optical (blue and

B. Montoro-Molina et al.: Optical tomography of the born-again ejecta of A 58



red) and molecular (green) emissions of A 58, where the geometrical model of the innermost molecular component presented by
Tafoya et al. (2022) is shown for comparison. In this new approach, the optical outflows exhibit an hourglass-like morphology, instead of the high-velocity clumps used for the molecular
gas. The bipolar lobes have a noticeable thickness, similar to the
structure recently proposed for the young molecular ejecta of
the Sakurai’s object by Tafoya et al. (2023). The high-velocity
components observed in the CO ( _J_ = 3 → 2) emission line are
located within the cavities formed by the ionized gas, which is
escaping around it, most likely transferring momentum to the
molecular material and dragging it outwards.
The molecular disk is not expected to emit in the optical
emission line, but it rather extincts the emission behind it. In this
sense it should be noted that SHAPE does not account for radiative transfer physics, thus the effects of the spatially-varying
extinction caused by the disk cannot be modeled. Instead an arbitrary emission law has been included in the model to simulate
both the effects of extinction (emission decreasing with the optical depth along the line of sight and very particularly behind the
molecular disk) and distance to the CSPN (emission decreasing
with radial distance to the CSPN). The bottom panels show the
_HST_ [O iii] image (left) and a synthetic image rendered from
the SHAPE model (right). We remark that the bright “equatorial” band observed in the _HST_ images does not arise from the
molecular disk, but it originates from the region of the hourglass
structures closest to the disk, where they overlap.
Considering this physical structure for the ionized material
and assuming a radial velocity vector with homologous expansion at each point, it is possible to interpret the behavior of the

[O iii] emission centroids shown in Fig. 3. The emission from
the outflow, whose kinematics is best seen in the view from the
plane of the sky shown in the left panel of Fig. 5, can be split into
two components: one expanding close to the plane of the sky (1)
and another one expanding mostly perpendicularly to it (2). The
first component would correspond to those centroids of the emission in the low-velocity range from −100 to +100 km s [−][1] . The
spatial distribution of the emission at velocities within this range
would be reasonably aligned with the direction of the outflow
(PA of 63 [◦] ) and would be more intense in the central regions for
the blue emission, where material thickness is maximal, and beyond the molecular disk for the red emission, where extinction is
minimal. These emissions would delineate the maximum spatial
extent of the outflow. On the other hand, the emission expanding
away on near- and far-side within the second, mostly along the
line of sight component, will have the highest projected velocities. It would be located closer to the CSPN star in the plane
of the sky compared to the emission from the first component.
This behavior is reflected in the centroids of gas with velocities
- +120 and < −120 km s [−][1] . We note that the traces of the centroids form a kind of loop, more evident in the less extincted
emission heading towards us. This may suggest either density
inhomogeneities within the structure or emission from the edge
of the hourglass structure.
The proposed morphology for the H-deficient ionized and
molecular components reveals an evolving physical structure,
where the acceleration of material close to the CSPN by its sudden ionization and by the emerging stellar wind generates dynamical effects on the molecular material which has prevailed
until now, eroding the molecular disk and accelerating the bipolar molecular outflows. In addition to a high adf value in A 58,
in the range ∼90 (Wesson et al. 2018) [1], these characteristics


1 See `[https://nebulousresearch.org/adfs/](https://nebulousresearch.org/adfs/)`



support previous suggestions of the presence of a companion
in born-again PNe (Soker 1997). A companion is definitely required to explain the formation of an equatorial disk and bipolar
outflows, but the details of the (stellar or sub-stellar) companion
and its orbital parameters are yet unknown.
It is interesting to note that the abundances of the H-deficient
material in A 58 obtained from optical spectroscopy agree with
predictions from nova events and, thus, a nova-like event has
been proposed to have taken place here (Lau et al. 2011). In
such models the companion is of stellar origin, but we note that
the velocity of the bipolar ejection in A 58 might actually suggest differently. The velocity of the molecular jet must be similar to the escape velocity ( _v_ esc ) of the companion and, thus,
the ≈ 280 km s [−][1] velocity of the molecular emission (Tafoya
et al. 2022) seems to suggest the presence of a substellar object
more massive than a Jupiter-like planet ( _v_ esc ≈ 60 km s [−][1] ) or
a main-sequence stellar companion with spectral type later than
M9 ( _v_ esc ≈ 600 km s [−][1] ; Kaltenegger & Traub 2009).
An alternative channel for the formation of disk/jet structures
in born-again pNe has recently been proposed by RodríguezGonzález et al. (2022). It is suggested that a WD in a binary
system, after experiencing a VLTP, inflates its outer layers and
enters a common envelope with its companion (that, in the case
of A 58, would be a substellar companion). Even though the duration of the VLTP is short (≲200 yr; Miller Bertolami et al.
2006), these authors argue that it is sufficient to allow the companion to shape the H-deficient ejecta into a disk plus a bipolar
structure. We note that such claims will have to be put to test with
future numerical simulations following the specific evolution of
a star experiencing a VLTP in a binary system.


_4.2._ _Spatial distribution of the HCN and CO high-velocity_
_components_


The ALMA CO molecular emission of A 58 has been attributed
to a radially expanding disk-like structure and orthogonal compact high-velocity components (Tafoya et al. 2022). This spatiokinematical structure differs notably from that derived here from
optical emission lines of ionized material. Interestingly the spectral profiles of emission lines of other molecules arising from
the born-again ejecta, most notably the HCN (J=4 → 3) shown
in the left panel of Figure 6, also present high-velocity components whose spatial distribution can be compared to those of
CO (J=3 → 2), [O iii] and [N ii].
The ALMA observations have then been used to obtain the
first moment image of the HCN (J=4 → 3) emission line shown
in the right panel of Figure 6. Contrary to the CO molecule, the
spatial distribution of the high-velocity component of HCN is
not compact, but it is rather diffuse and more extended. While
CO is well known for being an excellent tracer of molecular
outflows, which could include a wide range of physical conditions, HCN and HCO [+] molecules are typically excited within
high-density gas. The optical emission lines from ionized material and the HCN molecule would then trace highly excited gas,
expelled from regions closer to the central source, whereas the
CO molecule would probe denser material from the expanding
equatorial disk and molecular outflow.


**5.** **Conclusions**


We presented the analysis of IFS observations of the born-again
PN A 58 obtained with GTC MEGARA. These observations
helped us disclose the true kinematics of the optical emission


Article number, page 9 of 11

_A&A proofs:_ manuscript no. Article


3.0





1.0 0.5 0.0 0.5 1.0

|Col1|Col2|10|
|---|---|---|
||1<br>0<br>0.0<br>0.5<br>1.0|0<br>2<br>5<br>7<br>1|
||1<br>0<br>0.0<br>0.5<br>1.0|.5|
||1<br>0<br>0.0<br>0.5<br>1.0|.0|

RA offset (arcsec)



50


75


100





100


25


|Col1|Col2|
|---|---|
|||



velocity offset (km s 1 )



**Fig. 6.** Spatio-kinematical distribution of the HCN( _J_ = 4 → 3) emission around V605 Aql. Left: ALMA HCN ( _J_ = 4 → 3) emission line profile
from V605 Aql. Right: velocity field (first moment) of the HCN ( _J_ = 4 → 3) emission around V605 Aql in the velocity range −100 < _V_ offset (km
s [−][1] ) <100. is shown as a color map, according to the color code of the emission line profile in the left panel. The pixels with emission below 3
times the rms noise level of 0.2 mJy beam [−][1] were masked. The gray contours show the velocity-integrated emission (zeroth moment) of the HCN
( _J_ = 4 → 3) in the velocity range −100 < _V_ offset (km s [−][1] ) < 100. The gray contours are drawn from 3σ on steps of 3σ (where σ = 6.5 mJy
beam [−][1] km s [−][1] is the rms noise level of the zeroth moment image). The blue and red contours show the zeroth moment emission of the HCN
( _J_ = 4 → 3) in the velocity range −165 < _V_ offset (km s [−][1] ) < −100 and +100 - _V_ offset (km s [−][1] ) > +180, respectively. The red contours are drawn
for 9, 12 and 15 mJy whereas blue contours are drawn for 7, 9 and 11 mJy.



from the born-again ejecta in this PNe. MEGARA’s high spectral
resolution has allowed us to directly detect the H-alpha emission
from the H-poor ejecta without any contamination, which, until
now, had only been estimable through various methods, for instance, Wesson et al. (2008) and Montoro-Molina et al. (2022).
Only the blue component is detected, whereas the red component is deemed to be completely absorbed behind a high-density
molecular and dusty disk.
We used observations from CTIO to estimate an average systemic velocity of +103 km s [−][1] consistent with the MEGARA
data. Previous measurements, both 96 km s [−][1] obtained by Clayton et al. (2013) and Tafoya et al. (2017) for the inner ejecta, are
also consistent within the errors values. Nevertheless, the brightening of one side of A 58 and the blue components of the nebular
emission lines being broader than the red ones seem to suggest
the interaction of the PN with the ISM, which may result in different radial velocities of the old nebula and recent VLTP ejecta.
We have also performed a channel-by-channel Gaussian adjusting of the ejecta emission, improving the modest spatial resolution of our data. This has allowed us to refine the description
of the morphology of the optical emission of the ejecta, which
initially was assumed to be practically identical to the molecular
emission. The high-velocity components now result in a hourglass structure, within which the high-velocity molecular components are located. The SHAPE model presented reasonably
reflects the emission detected in the [O iii] λ5007 line obtained
with the _HST_ . It is worth mentioning that the sketches presented
by Montoro-Molina et al. (2022) are in good agreement both
with the spectral variability observed in the ejecta and with the
proposed spatio-kinematic structure.
Prior knowledge of the spatial distribution of the molecular
content of the H-poor ejecta of A 58 has allowed us to interpret
the results obtained in the optical range, which would have other

Article number, page 10 of 11



wise been nearly impossible. This insight reveals that molecular
material may be playing a significant role in the rest of known
born-again PNe, namely A 30, A 78, HuBi 1, and the Sakurai’s
Object.


_Acknowledgements._ The authors thanks the referee, Geoffrey Clayton, for his
comments and suggestions to improve the presentation of the manuscript.
B.M.M. and M.A.G. are funded by grants PGC2018-102184-B-I00 and
PID2022-142925NB-I00 of the Ministerio de Educación, Innovación y Universidades (MCIU) cofunded with FEDER funds. J.A.T. thanks Dirección General de Asuntos del Personal Académico (DGAPA) of the Universidad Nacional
Autónoma de México (UNAM, Mexico) project IA101622, and support from
the Marcos Moshinksy Foundation and the Visiting-Incoming programme of the
IAA-CSIC through the Centro de Excelencia Severo Ochoa (Spain). This work
as made extensive use of the NASA’s Astrophysics Data System (ADS).


**References**


Borkowski, K. J., Harrington, J. P., Tsvetanov, Z., & Clegg, R. E. S. 1993, ApJ,
415, L47
Borkowski, K. J., Harrington, J. P., & Tsvetanov, Z. I. 1995, ApJ, 449, L143
Clayton, G. C., Bond, H. E., Long, L. A., et al. 2013, ApJ, 771, 130
Clayton, G. C., Kerber, F., Pirzkal, N., et al. 2006, ApJ, 646, L69
Condon, J. J. 1997, PASP, 109, 166
Fang, X., Guerrero, M. A., Marquez-Lugo, R. A., et al. 2014, ApJ, 797, 100
Gil de Paz, A., Carrasco, E., Gallego, J., et al. 2018, in Society of Photo-Optical
Instrumentation Engineers (SPIE) Conference Series, Vol. 10702, Groundbased and Airborne Instrumentation for Astronomy VII, ed. C. J. Evans,
L. Simard, & H. Takami, 1070217
Guerrero, M. A. & Manchado, A. 1996, ApJ, 472, 711
Harrison, T. E. 1996, PASP, 108, 1112
Hazard, C., Terlevich, R., Morton, D. C., Sargent, W. L. W., & Ferland, G. 1980,
Nature, 285, 463
Iben, I., J., Kaler, J. B., Truran, J. W., & Renzini, A. 1983, ApJ, 264, 605
Jacoby, G. H. 1979, PASP, 91, 754
Jacoby, G. H. & Ford, H. C. 1983, ApJ, 266, 298
Kaltenegger, L. & Traub, W. A. 2009, ApJ, 698, 519
Lau, H. H. B., De Marco, O., & Liu, X. W. 2011, MNRAS, 410, 1870
Manchado, A., Pottasch, S. R., & Mampaso, A. 1988, A&A, 191, 128

B. Montoro-Molina et al.: Optical tomography of the born-again ejecta of A 58


Meaburn, J. & Lopez, J. A. 1996, ApJ, 472, L45
Meaburn, J., Lopez, J. A., Bryce, M., & Redman, M. P. 1998, A&A, 334, 670
Miller Bertolami, M. M., Althaus, L. G., Serenelli, A. M., & Panei, J. A. 2006,
A&A, 449, 313
Montoro-Molina, B., Guerrero, M. A., & Toalá, J. A. 2023, MNRAS[ `arXiv:2309.08242` ]
Montoro-Molina, B., Guerrero, M. A., Toalá, J. A., & Rodríguez-González, J. B.
2022, ApJ, 934, 18
Nakano, S., Sakurai, Y., Hazen, M., et al. 1996, IAU Circ., 6322, 1
Osterbrock, D. E., Fulbright, J. P., Martel, A. R., et al. 1996, PASP, 108, 277
Pascual, S., Cardiel, N., Gil de Paz, A., et al. 2019, in Highlights on Spanish Astrophysics X, ed. B. Montesinos, A. Asensio Ramos, F. Buitrago, R. Schödel,
E. Villaver, S. Pérez-Hoyos, & I. Ordóñez-Etxeberria, 227–227
Pollacco, D. L., Lawson, W. A., Clegg, R. E. S., & Hill, P. W. 1992, MNRAS,
257, 33P
Rodríguez-González, A., Peña, M., Hernández-Martínez, L., et al. 2023, ApJ,
955, 151
Rodríguez-González, J. B., Santamaría, E., Toalá, J. A., et al. 2022, MNRAS,
514, 4794
Schönberner, D. 1979, A&A, 79, 108
Seitter, W. C. 1985, in European Southern Observatory Conference and Workshop Proceedings, Vol. 21, European Southern Observatory Conference and
Workshop Proceedings, 253–258
Simpson, J., Jones, D., Wesson, R., & García-Rojas, J. 2022, Research Notes of
the American Astronomical Society, 6, 4
Soker, N. 1997, ApJS, 112, 487
Steffen, W., Koning, N., Wenger, S., Morisset, C., & Magnor, M. 2011, IEEE
Transactions on Visualization and Computer Graphics, 17, 454
Tafoya, D., Toalá, J. A., Unnikrishnan, R., et al. 2022, ApJ, 925, L4
Tafoya, D., Toalá, J. A., Vlemmings, W. H. T., et al. 2017, A&A, 600, A23
Tafoya, D., van Hoof, P. A. M., Toalá, J. A., et al. 2023, A&A, 677, L8
Toalá, J. A., Jiménez-Hernández, P., Rodríguez-González, J. B., et al. 2021a,
MNRAS, 503, 1543
Toalá, J. A., Lora, V., Montoro-Molina, B., Guerrero, M. A., & Esquivel, A.
2021b, MNRAS, 505, 3883
Tody, D. 1993, in Astronomical Society of the Pacific Conference Series, Vol. 52,
Astronomical Data Analysis Software and Systems II, ed. R. J. Hanisch,
R. J. V. Brissenden, & J. Barnes, 173
Wesson, R., Barlow, M. J., Liu, X. W., et al. 2008, MNRAS, 383, 1639
Wesson, R., Jones, D., García-Rojas, J., Boffin, H. M. J., & Corradi, R. L. M.
2018, MNRAS, 480, 4589



Article number, page 11 of 11


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "ALMA CO (J=3->2) spatio-kinematic distribution and geometrical model of the innermost molecular component",
  "failed_quote": "The mesh model shows the combination of the optical (blue and red) and molecular (green) emissions of A 58, where the geometrical model of the innermost molecular component presented by Tafoya et al. (2022) is shown for comparison."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Consistency between GTC MEGARA dips, CTIO echelle double-peak averages, and ALMA/APEX molecular line profiles.",
  "failed_quote": "These values are found to be consistent to the observed dips in the GTC MEGARA Hα and [N ii] λ6584 spectral profiles of the outer nebular shell shown in Fig. 1."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Extract the ALMA HCN (J=4->3) emission line profile and compute zeroth-moment (velocity-integrated) and first-moment (velocity field) maps across low-velocity (-100 to +100 km s^-1) and high-velocity (-165 to -100 km s^-1 and +100 to +180 km s^-1) intervals, masking pixels below 3 sigma.",
  "failed_quote": "The blue and red contours show the zeroth moment emission of the HCN (J = 4 → 3) in the velocity range −165 < Voffset (km s−1) < −100 and +100 < Voffset (km s−1) > +180, respectively."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[2]",
  "value": "3 sigma mask threshold = 3 x 0.2 mJy beam^-1; low-velocity range = -100 < V_offset < 100 km s^-1; high-velocity ranges = -165 < V_offset < -100 km s^-1 and +100 to +180 km s^-1",
  "failed_quote": "The blue and red contours show the zeroth moment emission of the HCN (J = 4 → 3) in the velocity range −165 < Voffset (km s−1) < −100 and +100 < Voffset (km s−1) > +180, respectively."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "The spatial velocity gradient of optical [O III] and [N II] emission (blueshifted to NE, redshifted to SE/SW) is opposite to that of the ALMA CO molecular disk (redshifted to NE, blueshifted to SW), showing that the molecular disk does not emit significantly in the optical.",
  "failed_quote": "According to this model based on the CO (J=3→2) spatio-kinematic information, the redshifted emission from the disk is found towards the NE of the CSPN, while the blueshifted emission is found towards the SW."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "The spatial velocity gradient of optical [O III] and [N II] emission (blueshifted to NE, redshifted to SE/SW) is opposite to that of the ALMA CO molecular disk (redshifted to NE, blueshifted to SW), showing that the molecular disk does not emit significantly in the optical.",
  "failed_quote": "This is exactly the opposite to the spatial distribution of the [O iii] and [N ii] emission (Fig. 3), thus indicating that the molecular disk is not emitting in the optical range, or at least, it is not the dominant structure."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The molecular disk does not emit optically but obscures the rear optical lobe; the ionized gas instead forms a thick hourglass bipolar outflow that embraces the molecular high-velocity components.",
  "failed_quote": "This is exactly the opposite to the spatial distribution of the [O iii] and [N ii] emission (Fig. 3), thus indicating that the molecular disk is not emitting in the optical range, or at least, it is not the dominant structure."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[1]",
  "value": "MEGARA data cubes lack absolute astrometric positioning, and there is a 0.26 arcsec (1.3 pixel) offset in the fitted stellar continuum position between VPH481-MR and VPH665-HR.",
  "failed_quote": "This procedure revealed an offset between the position of the star in the VPH481-MR and VPH665-HR data cubes of 1.3 pixels, i.e., 0′′.26, which is most likely due to irregularities in the surface and/or exact positioning of these two VPHs."
 }
]
```
