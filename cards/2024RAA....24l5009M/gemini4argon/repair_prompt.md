# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024RAA....24l5009M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Research in Astron. Astrophys. Vol.0 (20xx) No.0, 000–000
_http://www.raa-journal.org_ _http://www.iop.org/journals/raa_
(L [A] TEX: MANUSCRIPT.tex; printed on December 3, 2024; 4:07)



_**R**_ _esearch in_
_**A**_ _stronomy and_
_**A**_ _strophysics_


## **ALMA and GMRT Studies of Dust Continuum Emission and** **Spectral Lines Toward Oort Cloud Comet C/2022 E3 (ZTF)**

Arijit Manna [1], Sabyasachi Pal [1], Sekhar Sinha [2] and Sushanta Kumar Mondal [2]


1 Department of Physics and Astronomy, Midnapore City College, Paschim Medinipur 721129, India
2 Department of Physics, Sidho-Kanho-Birsha University, Ranchi Road, Purulia 723104, India


Received 20xx month day; accepted 20xx month day


**Abstract** The atomic and molecular compounds of cometary ices serve as valuable
knowledge into the chemical and physical properties of the outer solar nebula, where
comets are formed. From the cometary atmospheres, the atoms and gas-phase molecules
arise mainly in three ways: (i) the outgassing from the nucleus, (ii) the photochemical process, and (iii) the sublimation of icy grains from the nucleus. In this paper, we present the
radio and millimeter wavelength observation results of Oort cloud non-periodic comet
C/2022 E3 (ZTF) using the Giant Metrewave Radio Telescope (GMRT) band L and
the Atacama Large Millimeter/Submillimeter Array (ALMA) band 6. We do not detect
continuum emissions and an emission line of atomic hydrogen (HI) at rest frequency
1420 MHz from this comet using the GMRT. Based on ALMA observations, we detect the dust continuum emission and rotational emission lines of methanol (CH 3 OH)
from comet C/2022 E3 (ZTF). From the dust continuum emission, the activity of dust
production (Af _ρ_ ) of comet ZTF is 2280 _±_ 50 cm. Based on LTE spectral modelling, the
column density and excitation temperature of CH 3 OH towards C/2022 E3 (ZTF) are
(4.50 _±_ 0.25) _×_ 10 [14] cm _[−]_ [2] and 70 _±_ 3 K. The integrated emission maps show that CH 3 OH
was emitted from the coma region of the comet. The production rate of CH 3 OH towards C/2022 E3 (ZTF) is (7.32 _±_ 0.64) _×_ 10 [26] molecules s _[−]_ [1] . The fractional abundance
of CH 3 OH with respect to H 2 O in the coma of the comet is 1.52%. We also compare our
derived abundance of CH 3 OH with the existence modelled value, and we see the observed
and modelled values are nearly similar. We claim that CH 3 OH is formed via the subsequential hydrogenation of formaldehyde (H 2 CO) on the grain surface of comet C/2022
E3 (ZTF).


**Key** **words:** comets: general – planets and satellites: composition – radio continuum:
planetary systems – submillimetre: planetary systems – astrochemistry


**1** **INTRODUCTION**


Comets are kilometre-sized, ice-rich objects made of refractory, and volatile chemical compounds
(Ehrenfreund & Charnley 2000). This is the most pure remnant of the formation of the solar system,
just 4.6 billion years ago. Comets are the most excellent insight to study the volatile compositions of
the solar protoplanetary disks since they gather some of the solar system’s most ancient and primordial substances, including ices. Previous studies show that water (H 2 O) and different organic matters
may have reached the early Earth through comets as well (Hartogh et al. 2011). Since comets travel in

2 Manna et al.


Fig. 1: Orbital configuration of comet C/2022 E3 (ZTF) and inner solar system on February 5, 2023
(date of GMRT observation) and March 2, 2023 (date of ALMA observation).


the interstellar medium (ISM), they collect complex compounds, including amino acids (R–CH(NH 2 )–
COOH), from molecular clouds, star-formation regions, and protoplanetary disks and transport them
into the planetary atmosphere via collision with the planet (Ehrenfreund & Charnley 2000). Thus, it
is crucial to understand the variability in composition and isotopic ratios of cometary material to evaluate such scenarios (Altwegg & Bockel´ee-Morvan 2003; Bockel´ee-Morvan et al. 2015). Previously,
more than 60 molecular compounds were identified towards comet 67P/Churyumov-Gerasimenko between 2014 and 2016 using the Rosetta Orbiter Spectrometer for Ion and Neutral Analysis (ROSINA),
and their chemical compositions have been investigated using both in situ and remote ways (see Biver
& Bockel´ee-Morvan (2019) and references therein). In recent years, high-sensitivity ground-based millimeter wavelength telescopes have identified over 25 complex molecular compounds from the cometary
atmospheres (see Figure 1 of Biver & Bockel´ee-Morvan (2019) and references therein). Earlier, Altwegg
et al. (2016) detected the simplest amino acid glycine (NH 2 CH 2 COOH), phosphorus (P), and different
complex compounds from the 67P/Churyumov-Gerasimenko using the ROSINA. After that, Hadraoui
et al. (2019) made a chemical model and showed that NH 2 CH 2 COOH ejected from the nucleus due to
the sublimation of ice from the dust particles. Recently, centimeter and millimeter wavelength observations found evidence of atomic hydrogen (HI) and molecular emission lines of HCN, HNC, CH 3 OH,
CS, CH 3 CN, H 2 CO, SO, HC 3 N, and H 2 S from comet C/2020 F3 (NEOWISE) (Biver et al. 2022; Pal &
Manna 2024).
One of the most common interstellar molecules, methanol (CH 3 OH), was discovered in space for
the first time over 54 years ago (Ball et al. 1970). In the ISM, CH 3 OH has been found in gaseous
and solid forms (Ehrenfreund & Charnley 2000). The evidence of CH 3 OH is found in hot molecular cores, hot corinos, dark clouds, the Galactic Centre, and protoplanetary disks (Herbst & van
Dishoeck 2009; Thiel et al. 2017; Manigand et al. 2020; Booth et al. 2021; Chen et al. 2022). Earlier,
Drabek-Maunder et al. (2019) claimed the detection of CH 3 OH with transition J = 5(1,1)–4(1,1) towards Saturn’s moon Enceladus using IRAM 30-m telescope, but a single transition line of complex
molecules does not provide a secure detection. So it is challenging to believe the detection of CH 3 OH
towards Enceladus by Drabek-Maunder et al. (2019). The emission lines of CH 3 OH are also found in the
cometary atmosphere. In the solar system, the CH 3 OH lines were first found from comets Austin (1990
V) and Levy (1990 XX) with the IRAM 30-m telescope (Bockel´ee-Morvan et al. 1994a). The emission
lines of CH 3 OH are also found from comets P/Swift-Tuttle (1992) (Bockel´ee-Morvan et al. 1994b),

Continuum and spectral lines in C/2020 E3 (ZTF) 3


Table 1: Orbital properties of comet ZTF.


Parameters Symbol Value
Orbit eccentricity e 1.0000290
Orbit inclination i 109.16920 _[◦]_
Perihelion distance q 1.1126880 AU
Aphelion distance Q 2800 AU
Semi-major axis a _−_ 4087 AU
Orbital period P 50,000 years
Time of perihelion passage T 2459957.18000 JD
Longitude of ascending node Ω 302.53990 _[◦]_
Argument of perihelion _ω_ 145.80970 _[◦]_
Longitude of perihelion L 315.11506 _[◦]_
Latitude of perihelion B 32.05853 _[◦]_
Classification Nearly isotropic (a _>_ 10000 AU)
Note: The orbital parameters of comet ZTF are taken from Bolin et al. (2022) and NASA JPL Horizons System.


Hyakutake (C/1996 B2) (Womack et al. 1997), Lee (C/1999 H1) (Biver et al. 2000), HaleBopp (C/1995
O1) (Biver et al. 1999a), P/Halley (Eberhardt et al. 1994), C/2012 S1 (ISON) (Ag´undez et al. 2014),
C/2013 R1 (Lovejoy) (Ag´undez et al. 2014), C/2012 F6 (Lemmon) (Bøgelund & Hogerheijde 2017),
C/2012 K1 (PanSTARRS) (Cordiner et al. 2017), 46P/Wirtanen (Cordiner et al. 2023), and C/2020 F3
(NEOWISE) (Biver et al. 2022). Previously, Greenberg (1982) demonstrated that the chemical composition of cometary grains exhibits a strong similarity to those found in the ISM and circumstellar disks,
which indicates the formation pathways of CH 3 OH towards the cometary atmosphere are nearly similar
to interstellar grains. Earlier, Garrod (2019) showed that the formation pathways of CH 3 OH towards the
cometary atmosphere are similar to the star-formation regions.
C/2022 E3 (ZTF) (hereafter ZTF) is a long-period Oort-cloud comet (initial semi-major axis of 2000
AU) that was discovered on March 2, 2022, using the Zwicky Transient Facility at a heliocentric distance
of 4.3 AU (Bolin et al. 2022). The orbital properties of comet ZTF are shown in Table 1. This comet came
closest to Earth on February 1, 2023, at a distance of 0.28 AU. The close distance indicates that comet
ZTF is a near-Earth object. In March 2022, comet ZTF showed interesting cometary features, including
a green coma of diatomic carbon (C 2 ), a yellow dust tail, and a thin ion tail. After the identification
of this comet, Liu & Liu (2024) observed that the heliocentric distance of ZTF decreased with time,
which indicates the sublimation of the volatile species from the grain surface of the nucleus due to the
acceleration of solar heat, which enhances the luminosity of green coma. The production rates of OH and
H 2 O towards comet ZTF were _Q_ _OH_ = 3.51 _×_ 10 [28] s _[−]_ [1] and _Q_ _H_ 2 _O_ = 4.8 _×_ 10 [28] s _[−]_ [1], respectively (Jehin
et al. 2022; Schleicher et al. 2023). The production rates of CN, C 3, and C 2 on 10 March 2023 were
(5.43 _±_ 0.11) _×_ 10 [25] s _[−]_ [1], (2.01 _±_ 0.04) _×_ 10 [24] s _[−]_ [1], and (3.08 _±_ 0.50) _×_ 10 [25] s _[−]_ [1], respectively (Bolin et al.
2024). Liu & Liu (2024) shows that the size of the nucleus of the comet ZTF is 2.79 km. In February
2023, the Trivandrum Observatory post-perihelion observation data showed that the apparent sizes of the
tail and head of the comet ZTF were noticeably decreased (Jayakrishnan et al. 2023). Recently, Biver et
al. (2024) detected several rotational emission lines of complex organic molecules, including CH 3 OH,
towards comets ZTF and C/2021 A1 (Leonard) using the IRAM 30-m telescope. Biver et al. (2024) also
claimed the detection of ethylene glycol ((CH 2 OH) 2 ) and methyl cyanide (CH 3 CN) from comets ZTF
and C/2021 A1 (Leonard). Biver et al. (2024) also does not discuss the formation pathways of CH 3 OH
towards comet ZTF.

This paper presents the centimeter and millimeter wavelength observations of comet ZTF using the
high-resolution GMRT and ALMA. We also detected the rotational emission lines of CH 3 OH from the
coma region of this comet. The observational methods and data analysis techniques used in this study
are described in Section 2. The results and discussions of the detection of dust continuum and line

emissions are shown in Section 3. The conclusions are presented in Section 4.

|200<br>0<br>200<br>-|Col2|Col3|22479GHz<br>.<br>-200 0 200|200<br>0<br>200<br>-|Col6|Col7|22684GHz<br>.<br>Trail<br>Sun<br>-200 0 200|Col9|200<br>0<br>200<br>-|Col11|23912GHz<br>.<br>200 0|Col13|Col14|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||-|-|200<br>||
|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|239.94 GHz<br><br><br>|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|
|0<br>200<br>-200||||||||||||||


|200<br>0<br>200<br>-|Col2|
|---|---|
|||



We used the publicly available archival data of comet ZTF, which was observed on March 2, 2023, using
the high-resolution Atacama Large Millimeter/Submillimeter Array (ALMA) 12-m arrays with band 6
(PI: Martin Cordiner, ID: 2022.1.00997.T). This observation aimed to study the millimeter-wavelength
dust continuum emission and detection of volatile molecules. On March 2, 2023, the distance between
the comet ZTF and Earth was 0.96 AU. Similarly, the distance between ZTF and the Sun was 1.35 AU.
The orbital configuration of comet ZTF on March 2, 2023, is shown in Figure 1. This observation was
carried out in the frequency ranges of 223.85–225.73 GHz, 225.91–227.79 GHz, 239.01–239.25 GHz,
239.89–240.01 GHz, 240.78–240.90 GHz, and 241.67–243.55 GHz with a spectral resolution of 976.56
kHz. A total of 39 antennas were used during the observation. The minimum and maximum baselines
were 15.3 m and 783.1 m. The on-source integration time was 44.352 m. During the observation, the
comet was continuously tracked, and the phase centre position in the sky was updated in real-time using
the JPL Horizons orbital solution #JPL 81. During the observation of comet ZTF, the flux and bandpass
calibrator were taken as J0423–0120. Similarly, J0442–0017 was used as a phase calibrator.
For the analysis of the raw data of ZTF, we used the Common Astronomy Software Application
(CASA 5.4.1) with standard pipeline scripts delivered by the Joint ALMA Observatory (JAO) (Team
et al. 2022). For flux calibration, we used the task SETJY with the Perley-Butler 2017 flux calibrator model (Perley & Butler 2017). We also used the pipeline tasks HIFA ~~B~~ ANDPASSFLAG and
HIFA FLAGDATA to remove the bad antenna data. After analysing the raw data, we split the target
source (ZTF ~~C~~ 2022 ~~E~~ 3) with the help of the CASA task MSTRANSFORM. Before imaging, we sub

Continuum and spectral lines in C/2020 E3 (ZTF) 5


Table 2: Dust continuum emission properties of comet ZTF based on ALMA data.


Frequency Integrated fuxl Peak fuxl RMS Synthesized beam Deconvolved source size
(GHz) ( _µ_ Jy) ( _µ_ Jy beam _[−]_ [1] ) ( _µ_ Jy) ( _[′′]_ ) ( _[′′]_ )
224.79 124 _±_ 17 120 _±_ 10 9.45 0.53 ~~_[′′]_~~ _×_ 0.42 ~~_[′′]_~~ 0.51 ~~_[′′]_~~ _×_ 0.44 ~~_[′′]_~~

226.84 132 _±_ 49 106 _±_ 12 5.87 0.53 _[′′]_ _×_ 0.41 _[′′]_ 0.49 _[′′]_ _×_ 0.42 _[′′]_

239.12 138 _±_ 17 109 _±_ 13 7.52 0.50 _[′′]_ _×_ 0.39 _[′′]_ 0.47 _[′′]_ _×_ 0.38 _[′′]_

239.94 140 _±_ 25 112 _±_ 9 5.20 0.50 _[′′]_ _×_ 0.39 _[′′]_ 0.48 _[′′]_ _×_ 0.38 _[′′]_

240.83 145 _±_ 38 115 _±_ 10 4.68 0.50 _[′′]_ _×_ 0.39 _[′′]_ 0.48 _[′′]_ _×_ 0.37 _[′′]_

242.60 155 _±_ 32 120 _±_ 15 6.68 0.50 _[′′]_ _×_ 0.39 _[′′]_ 0.49 _[′′]_ _×_ 0.38 _[′′]_


tract the continuum from the visibilities by fitting the second-order polynomial to the line-free channels
in all spectral windows. We also used the CASA task CVEL for Doppler correction to the rest frame
of the comet. We make the dust continuum and spectral images of ZTF using the task TCLEAN with
hogbom deconvolution and the SPEC = CUBE parameter. To make the dust continuum emission images, we used line-free channels. At last, we corrected the primary beam pattern in both continuum and
spectral images using the task IMPBCOR.


**2.2** **Giant Metrewave Radio Telescope (GMRT)**


Comet ZTF was also observed on February 5, 2023, using the Giant Meterwave Radio Telescope
(GMRT) band L (1050–1450 MHz). GMRT is located in Khodad near Pune in India (PI: Arijit Manna,
ID: ddtC267). This observation aimed to study the radio wavelength continuum emission in frequency
ranges of 1050–1450 MHz and the emission/absorption line of atomic HI at 1420 MHz. On February
5, 2023, the distance between the ZTF and Earth was 0.30 AU. The distance between ZTF and the
Sun was 1.16 AU on that day. The orbital configuration of comet ZTF on February 5, 2023, is shown
in Figure 1. During the observation, a total of 30 fully steerable, 45-m-diameter antennas were used,
with minimum and maximum baselines of _∼_ 100 m and _∼_ 25 km, respectively. The National Centre for
Radio Astrophysics (NCRA), a division of the esteemed Tata Institute of Fundamental Research (TIFR),
operates this radio telescope. A total of 8192 number of channels were used with a spectral resolution
of 0.0488 MHz. The on-source integration time was 3 hours and 15 minutes. During the observation,
quasar 3C 147 was used as a flux and phase calibrator.
We used the standard calibration method using CASA to reduce the data of comet ZTF. We import
the raw GMRT data in CASA using the task IMPORTGMRT. During calibration, we remove the bad
spectral channels and damage antenna data. To calibrate the flux, we used the SETJY task, utilizing the
Perley-Butler 2017 flux calibrator model (Perley & Butler 2017). We also make the bandpass calibration
using the 3C 147. After gain calibration and transferring the gain calibration to the target, we applied
the task MSTRANSFORM to split the target data. We make the continuum emission images of ZTF
with w-projection and the multi-frequency synthesis mode with 2nd-order expansion (Rau & Cornwell
2011). We also used the GAINCAL and APPLYCAL tasks for better image sensitivity. After making
the continuum emission images, we subtract the continuum emission from the visibility using the task
UVCONTSUB. We make the spectral images using the TCLEAN task with the SPECMODE = CUBE
parameter. We also applied the task WPBGMRT for primary beam correction of the continuum and
spectral images.


**3** **RESULT & DISCUSSION**


**3.1** **Results based on ALMA data**


_3.1.1_ _Dust continuum emission towards comet ZTF_


We observed that the comet ZTF is detected in the frequency ranges of 224.79 GHz to 242.60 GHz, as
shown in Figure 2. To estimate the dust continuum parameters of comet ZTF, we fitted the 2D Gaussian
using the CASA task IMFIT over the cometary area with a circle of radius 1.7 _[′′]_ . The physical parameters

6 Manna et al.


Fig. 3: SED plot of comet ZTF based on ALMA band 6 observations (left panel). In the SED plot,
the solid orange lines are the fluxes of ZTF with error bars, and the black line indicates the best-fitted
SED with the blackbody model. The right panel shows a corner diagram demonstrating the results
of our MCMC parameter estimation for the SED model. The diagonal panels display 1-D histograms
representing the marginalized posterior distributions for dust temperature and dust spectral index ( _β_ ).
Meanwhile, the off-diagonal panels illustrate 2-D projections of the posterior probability distributions,
showcasing the correlations between each pair of parameters.


are shown in Table 2. The direction of motion of comet ZTF and the Sun is shown in Figure 2. Comet
ZTF is not resolved in the frequency ranges of 224.79 GHz to 242.60 GHz as the deconvolved source
sizes are smaller than the synthesized beam sizes. We plot the spectral energy distribution (SED) of the
ZTF in the frequency ranges of 224.79 GHz to 242.60 GHz. After SED plotting, we fitted the comet flux
values using the blackbody model with the help of the Python package ASTROPY (version 5.0). We
used the Markov Chain Monte Carlo (MCMC) algorithm to fit the blackbody model over the observed
flux values. The SED plot and corner diagram based on MCMC analysis are shown in Figure 3. After
SED analysis, we found the dust temperature and dust spectral index ( _β_ ) of comet ZTF were 65.05 _±_ 4.65
K and 1.20 _±_ 0.44.


Now, we estimate the activity of dust production (Af _ρ_ ) of comet ZTF using the following equation
(A’Hearn et al. 1984):



_h_ [∆] [2]
_Afρ_ = [4] _[ R]_ [2]



(1)
_F_ _⊙_



_h_ [∆] _F_ _com_

_ρ_ _F_ _⊙_



In equation 1, _R_ _h_ is the distance between comet and Sun in AU, ∆ is the distance between Earth
and comet in cm, _F_ _com_ is the flux of comet in unit of erg cm _[−]_ [2] s _[−]_ [1], _ρ ∼_ 6500 km is the nucleocentric
distance of the comet ZTF (Bolin et al. 2024), and _F_ _⊙_ is the solar flux in unit of erg cm _[−]_ [2] s _[−]_ [1] at 1
AU. The solar flux is taken from the high-resolution solar spectrum of Kurucz et al. (1984). During
the estimation of Af _ρ_, we used the flux value at frequencies of 242.60 GHz. Using equation 1, the
calculated value of Af _ρ_ of comet ZTF, based on ALMA data, is 2280 _±_ 50 cm, which is nearly similar
to the estimated value of Jehin et al. (2023). Recently, Bolin et al. (2024) estimated the value of Af _ρ_ in
optical wavelengths toward comet ZTF as 1483 _±_ 40 cm, which is smaller than the estimated value of
Af _ρ_ using ALMA data in millimeter wavelengths. Our estimated higher value of Af _ρ_ using the ALMA
data indicates a high level of dust production due to the close distance between ZTF and the Sun during
our observation.

Now, we compare the Af _ρ_ value of the comet ZTF with different dynamical types of other comets,
as shown in Table 3. After comparison, we observe that comet P/Halley exhibits a higher Af _ρ_ at _R_ _h_ of
1.53 AU. Similarly, we found the Af _ρ_ value of comet ZTF is 2280 _±_ 50 cm at _R_ _h_ of 1.35 AU, which is

Continuum and spectral lines in C/2020 E3 (ZTF) 7


Table 3: Comparision of the activity of dust production (Af _ρ_ ) with comet ZTF and other comets.


Comet Af _ρ_ _R_ _h_ Reference
(cm) (AU)
C/2023 E3 (ZTF) 2280 _±_ 50 1.35 This study
4P _/_ Faye 1146.0 _±_ 1.2 1.62 Gillan et al. (2024)
6P _/_ d _[′]_ Arrest 203 _._ 8 _±_ 1 _._ 5 1.54 Gillan et al. (2024)
11P _/_ Tempel-Swift-LINEAR 17 _._ 8 _±_ 0 _._ 3 1.39 Gillan et al. (2024)
108P _/_ Ciffreo 146 _._ 2 _±_ 1 _._ 5 1.67 Gillan et al. (2024)
114P _/_ Wiseman-Skiff 76 _._ 7 _±_ 0 _._ 3 1.59 Gillan et al. (2024)
132P _/_ Helin-Roman-Alu 128 _._ 6 _±_ 0 _._ 5 1.70 Gillan et al. (2024)
156P _/_ Russell-LINEAR 681 _._ 6 _±_ 0 _._ 4 1.35 Gillan et al. (2024)
254P _/_ McNaught 360 _._ 0 _±_ 6 _._ 5 3.68 Gillan et al. (2024)
398P _/_ Boattini 72 _._ 1 _±_ 0 _._ 1 1.31 Gillan et al. (2024)
409P _/_ LONEOS-Hill 53 _._ 6 _±_ 1 _._ 0 1.75 Gillan et al. (2024)
425P _/_ Kowalski 63 _._ 3 _±_ 3 _._ 6 2.90 Gillan et al. (2024)
449P _/_ Leonard (2020 S6) 8 _._ 2 _±_ 0 _._ 6 1.88 Gillan et al. (2024)
P _/_ 2019 LD2 (ATLAS) 303 _._ 4 _±_ 21 _._ 7 4.61 Gillan et al. (2024)
P _/_ 2020 T3 (PANSTARRS) 17 _._ 5 _±_ 0 _._ 5 1.47 Gillan et al. (2024)
P _/_ 2020 U2 (PANSTARRS) 90 _._ 8 _±_ 0 _._ 8 1.88 Gillan et al. (2024)
P _/_ 2020 WJ5 (Lemmon) 193 _._ 4 _±_ 16 _._ 1 5.07 Gillan et al. (2024)
P _/_ 2021 Q5 (ATLAS) 41 _._ 0 _±_ 0 _._ 9 1.27 Gillan et al. (2024)
67P/Churyumov-Gerasimenko 233 _±_ 12 1.36 Schleicher (2006)
P/Halley 20400 _±_ 110 1.53 Schleicher et al. (1998)
C/2014 UN 271 (Bernardinelli-Bernstein) 15000 _±_ 250 20 Lellouch et al. (2022)


higher than the rest of the comets but lower than the comet P/Halley and C/2014 UN 271 (BernardinelliBernstein). We found different Af _ρ_ values for different comets owing to the different grain sizes, perihelion distances, and ice compositions, which produced more dust as ice vaporized and released dust
particles.


_3.1.2_ _Methanol (CH_ _3_ _OH) towards comet ZTF_



We extracted the molecular spectra from the spectral images by making a 0.8 _[′′]_ diameter circular region over the cometary area. The synthesized beam sizes of the spectral images in the frequency
ranges of 223.85–225.73 GHz, 225.91–227.79 GHz, 239.01–239.25 GHz, 239.89–240.01 GHz, 240.78–
240.90 GHz, and 241.67–243.55 GHz were 0.50 _[′′]_ _×_ 0.39 _[′′]_, 0.51 _[′′]_ _×_ 0.39 _[′′]_, 0.51 _[′′]_ _×_ 0.38 _[′′]_, 0.50 _[′′]_ _×_ 0.38 _[′′]_,
0.50 _[′′]_ _×_ 0.39 _[′′]_, and 0.51 _[′′]_ _×_ 0.39 _[′′]_ . For spectral analysis, we used the CASSIS software (Vastel et al.
2015). For detection of the rotational emission lines of CH 3 OH, we used the Local Thermodynamic
Equilibrium (LTE) model with the Cologne Database for Molecular Spectroscopy (CDMS) databases
(M¨uller et al. 2005). To fit the local thermodynamic equilibrium (LTE) spectral model to the observed
emission lines of CH 3 OH, we utilized the MCMC algorithm within the CASSIS software package.
After spectral analysis, we detected a total of 15 transition lines of CH 3 OH from the comet ZTF. The
detected emission lines of CH 3 OH exhibited upper state energies ( _E_ _up_ ) ranging from 34.82 K to 130.82
K. CH 3 OH is a slightly asymmetric top molecule with an internal torsional motion of CH 3 around the
molecular symmetry axis relative to the OH radical. The transitions of CH 3 OH are explained by _J_,
_±K_ _a_, and Γ. In transitions of CH 3 OH, we used Γ = A, where Γ is associated with ‘–’ or ‘+’ sign
indicates the parity. Similarly, we also used the Γ = E in the transitions of CH 3 OH because, in the
absence of parity, the energy levels (E1 and E2) of CH 3 OH are distinguished by _±K_ . After detection
_′_ _′′_
of the rotational emission lines of CH 3 OH, we obtained molecular transitions (J K _[′]_ a [Γ] _[′]_ [–][J] K _[′′]_ a [Γ] _[′′]_ [ ),] [upper]

state energy ( _E_ _u_ ) in K, Einstein coefficients ( _A_ _ij_ ) in s _[−]_ [1], line intensity ( _Sµ_ [2] ) in Debye [2], full-width
half maximum (FWHM) in km s _[−]_ [1], optical depth ( _τ_ ), and integrated intensities (� T mb dV) in K km
s _[−]_ [1] . The detected emission lines and spectral line parameters of CH 3 OH are shown in Figure 4 and
Table 4. We also observed that the detected emission lines of CH 3 OH are optically thin. After spectral
line analysis using the LTE model, we found the column density and excitation temperature of CH 3 OH



_′_ _′′_

K _[′]_ a [Γ] _[′]_ [–][J]




[upper]
K _[′′]_ a [Γ] _[′′]_ [ ),]

8 Manna et al.


Fig. 4: Rotational emission lines of CH 3 OH towards comet ZTF (upper panel). In the spectra, the black
lines are the observed spectra, and the red lines are the best-fit LTE model spectra of CH 3 OH. The lower
panel shows the rotational diagram of CH 3 OH.


are (4.50 _±_ 0.25) _×_ 10 [14] cm _[−]_ [2] and 70 _±_ 3 K respectively. During LTE fitting, we used the source size
_∼_ 0.5 _[′′]_ . To verify the temperature of CH 3 OH, we also made the rotational diagram of CH 3 OH, which is
shown in Figure 4. The methods and theory of the rotational diagram are well discussed in Manna &
Pal (2024). After the rotational diagram, we found the rotational temperature of CH 3 OH is 72 _±_ 12 K,
which is very close to the excitation temperature of CH 3 OH. Recently, Biver et al. (2024) also claimed
the detection of CH 3 OH towards comet ZTF, and they estimated the rotational temperature of CH 3 OH
is 58 _±_ 4 K using the rotational diagram. The derived rotational temperature of CH 3 OH by Biver et al.
(2024) is lower than that of the present paper. The estimated rotational temperature of CH 3 OH by Biver
et al. (2024) is less because it is measured by the IRAM 30 m single dish, whose resolution is much

Continuum and spectral lines in C/2020 E3 (ZTF) 9


Table 4: Spectral line properties of CH 3 OH towards comet ZTF.

Frequency Quantum number _E_ _u_ _A_ _ij_ g _up_ _Sµ_ [2] FWHM � T mb dV Optical depth



_′_ _′′_

K _[′]_ a [Γ] _[′]_ [ –][J] K



_′_
(GHz) (J



K _[′′]_ a [Γ] _[′′]_ [ )] (K) (s _[−]_ [1] ) (Debye [2] ) (km s _[−]_ [1] ) (K km s _[−]_ [1] ) ( _τ_ )



241.700 5(-0,5)–4(-0,4)E, _v_ _t_ = 0 47.93 6.04 _×_ 10 _[−]_ [5] 11 16.15 1.52 _±_ 0.23 0.62 _±_ 0.02 0.02
241.767 5(1,5)–4(1,4)E, _v_ _t_ = 0 40.39 5.81 _×_ 10 _[−]_ [5] 11 15.53 1.54 _±_ 0.25 0.65 _±_ 0.01 0.03
241.791 5(0,5)–4(0,4)A, _v_ _t_ = 0 34.82 6.05 _×_ 10 _[−]_ [5] 11 16.16 1.50 _±_ 0.32 0.67 _±_ 0.04 0.04
241.806 5(4,2)–4(4,1)A, _v_ _t_ = 0 115.16 2.18 _×_ 10 _[−]_ [5] 11 5.82 1.57 _±_ 0.55 0.22 _±_ 0.06 0.02
241.813 5(4,2)–4(4,1)E, _v_ _t_ = 0 122.72 2.18 _×_ 10 _[−]_ [5] 11 5.82 1.72 _±_ 0.62 0.17 _±_ 0.03 0.05
241.829 5(-4,1)–4(-4,0)E, _v_ _t_ = 0 130.82 2.19 _×_ 10 _[−]_ [5] 11 5.85 1.62 _±_ 0.56 0.12 _±_ 0.02 0.03
241.832 5(3,3)–4(3,2)A, _v_ _t_ = 0 84.62 3.87 _×_ 10 _[−]_ [5] 11 10.33 1.52 _±_ 0.26 0.31 _±_ 0.02 0.06
241.833 5(3,2)–4(3,1)A, _v_ _t_ = 0 84.62 3.87 _×_ 10 _[−]_ [5] 11 10.33 1.52 _±_ 0.26 0.31 _±_ 0.02 0.06
241.842 5(2,4)–4(2,3)A, _v_ _t_ = 0 72.53 5.12 _×_ 10 _[−]_ [5] 11 13.66 1.56 _±_ 0.52 0.37 _±_ 0.02 0.05
241.843 5(-3,3)–4(-3,2)E, _v_ _t_ = 0 82.53 3.88 _×_ 10 _[−]_ [5] 11 10.36 1.56 _±_ 0.52 0.37 _±_ 0.02 0.05
241.852 5(3,2)–4(3,1)E, _v_ _t_ = 0 97.53 3.89 _×_ 10 _[−]_ [5] 11 10.40 1.52 _±_ 0.24 0.13 _±_ 0.01 0.02
241.879 5(-1,4)–4(-1,3)E, _v_ _t_ = 0 55.87 5.96 _×_ 10 _[−]_ [5] 11 15.92 1.53 _±_ 0.32 0.42 _±_ 0.06 0.03
241.887 5(2,3)–4(2,2)A, _v_ _t_ = 0 72.53 5.12 _×_ 10 _[−]_ [5] 11 13.67 1.53 _±_ 0.38 0.35 _±_ 0.02 0.02
241.904 5(2,3)–4(2,2)E, _v_ _t_ = 0 60.73 5.09 _×_ 10 _[−]_ [5] 11 13.59 1.58 _±_ 0.26 0.78 _±_ 0.02 0.03
241.904 5(-2,4)–4(-2,3)E, _v_ _t_ = 0 57.07 5.03 _×_ 10 _[−]_ [5] 11 13.43 1.58 _±_ 0.27 0.78 _±_ 0.02 0.03



Table 5: Production rate of CH 3 OH towards comet ZTF.
Frequency(GHz) Quantum number(J _′_ _[′]_ _[′]_ [ –][J] _′′_ _[′′]_ _[′′]_ [ )] (km s _v_ _exp_ _[−]_ [1] ) Production rate ((molecule s _[−]_ [1] ) _Q_ )



_′_ _′′_

K _[′]_ a [Γ] _[′]_ [ –][J]



K _[′′]_ a [Γ] _[′′]_ [ )] (km s _[−]_ [1] ) (molecule s _[−]_ [1] )



241.700 5(-0,5)–4(-0,4)E, _v_ _t_ = 0 0.76 _±_ 0.02 (7.25 _±_ 0.29) _×_ 10 [26]

241.767 5(1,5)–4(1,4)E, _v_ _t_ = 0 0.77 _±_ 0.03 (6.82 _±_ 0.62) _×_ 10 [26]

241.791 5(0,5)–4(0,4)A, _v_ _t_ = 0 0.75 _±_ 0.04 (7.02 _±_ 0.55) _×_ 10 [26]

241.806 5(4,2)–4(4,1)A, _v_ _t_ = 0 0.78 _±_ 0.02 (7.36 _±_ 0.78) _×_ 10 [26]

241.813 5(4,2)–4(4,1)E, _v_ _t_ = 0 0.86 _±_ 0.03 (7.55 _±_ 0.21) _×_ 10 [26]

241.829 5(-4,1)–4(-4,0)E, _v_ _t_ = 0 0.81 _±_ 0.06 (7.82 _±_ 0.30) _×_ 10 [26]

241.832 5(3,3)–4(3,2)A, _v_ _t_ = 0 0.76 _±_ 0.06 (6.98 _±_ 0.53) _×_ 10 [26]

241.833 5(3,2)–4(3,1)A, _v_ _t_ = 0 0.76 _±_ 0.05 (6.97 _±_ 0.55) _×_ 10 [26]

241.842 5(2,4)–4(2,3)A, _v_ _t_ = 0 0.78 _±_ 0.07 (7.09 _±_ 1.20) _×_ 10 [26]

241.843 5(-3,3)–4(-3,2)E, _v_ _t_ = 0 0.78 _±_ 0.06 (7.10 _±_ 1.22) _×_ 10 [26]

241.852 5(3,2)–4(3,1)E, _v_ _t_ = 0 0.76 _±_ 0.02 (7.52 _±_ 0.98) _×_ 10 [26]

241.879 5(-1,4)–4(-1,3)E, _v_ _t_ = 0 0.76 _±_ 0.02 (7.36 _±_ 0.76) _×_ 10 [26]

241.887 5(2,3)–4(2,2)A, _v_ _t_ = 0 0.76 _±_ 0.05 (7.29 _±_ 0.90) _×_ 10 [26]

241.904 5(2,3)–4(2,2)E, _v_ _t_ = 0 0.79 _±_ 0.06 (7.82 _±_ 0.55) _×_ 10 [26]

241.904 5(-2,4)–4(-2,3)E, _v_ _t_ = 0 0.79 _±_ 0.08 (7.92 _±_ 0.22) _×_ 10 [26]

Average production rate ( _Q_ _CH_ 3 _OH_ ) (7.32 _±_ 0.64) _×_ 10 [26]


less than the present observation. Biver et al. (2024) could not study the spatial distribution of CH 3 OH
towards ZTF.

After detection of the emission lines of CH 3 OH, we also made the integrated intensity maps of
CH 3 OH based on four high-intensity lines using the CASA task IMFIT. The integrated intensity maps
of CH 3 OH towards comet ZTF are shown in Figure 5. The integrated intensity maps clearly show
that the CH 3 OH emits from the inner coma region of comet ZTF. After fitting the 2D Gaussian over
the integrated intensity maps, we observed that the emitting regions of CH 3 OH vary between 0.47 _[′′]_

and 0.49 _[′′]_ . The derived emitting regions of CH 3 OH are lower than the synthesized beam sizes of the
integrated intensity maps, which shows that the integrated intensity maps are not resolved.


_3.1.3_ _Production rate of CH_ _3_ _OH towards comet ZTF_


To derive the production rate ( _Q_ ) of CH 3 OH using the line area (� T mb dV) and rotational temperature
towards comet ZTF, we used the following equation (Drahus et al. 2010):



2 _k_ _b_ ∆ _v_ _exp_ _hν_
_Q_ =
~~_√_~~ _π_ ln 2 _h_ _DI_ ( _T_ ) _ν_ [(exp] � _kT_



_−_ 1) T mb dV (2)
� �

10 Manna et al.
















|J = 5( -0,5) –4( -0,4)E vt = 0<br>200,<br>0<br>200<br>-|Col2|Col3|Col4|200<br>0<br>200<br>-|Col6|Col7|J = 5(0,5) –4(0,4)A vt = 0<br>,<br>Trail<br>Sun|
|---|---|---|---|---|---|---|---|
|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|
||0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|
|0<br>-200<br>200|0<br>-200<br>200|0<br>-200<br>200|0<br>-200<br>200<br>**J = 5(-1,4)–4(-1,3)E, vt = 0**<br>**J = 5(2,4)–4(2,3)A, vt = 0**|0<br>-200<br>200<br>**J = 5(-1,4)–4(-1,3)E, vt = 0**<br>**J = 5(2,4)–4(2,3)A, vt = 0**|0<br>-200<br>200<br>**J = 5(-1,4)–4(-1,3)E, vt = 0**<br>**J = 5(2,4)–4(2,3)A, vt = 0**|0<br>-200<br>200<br>**J = 5(-1,4)–4(-1,3)E, vt = 0**<br>**J = 5(2,4)–4(2,3)A, vt = 0**|0<br>-200<br>200<br>**J = 5(-1,4)–4(-1,3)E, vt = 0**<br>**J = 5(2,4)–4(2,3)A, vt = 0**|
|||0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|0<br>200<br>-200|

Continuum and spectral lines in C/2020 E3 (ZTF) 11


Table 6: Comparision of the abundance of CH 3 OH with comet ZTF and other comets.


Comet Abundance of CH 3 OH Reference
( _X_ = _Q_ ( _CH_ 3 _OH_ ) _/Q_ ( _H_ 2 _O_ ) in %)
C/2023 E3 (ZTF) 1.52 This study
Austin (1990 V) 5 Bockel´ee-Morvan et al. (1994a)
Levy (1990 XX) 0.91 Bockel´ee-Morvan et al. (1994a)
P/Swift-Tuttle (1992) 4 Bockel´ee-Morvan et al. (1994b)
P/Halley 1.71 Eberhardt et al. (1994)
C/1996 B2 (Hyakutake) 2.01 Biver et al. (1999b)
C/1995 O1(Hale-Bopp) 2.40 Bockel´ee-Morvan et al. (2000)
C/1999 H1 (Lee) 2.10 Mumma et al. (2001)
153P/2002 C1 (Ikeya-Zhang) 2.50 Disanti et al. (2002)
C/2002 T7 (LINEAR) 1.50 Remijan et al. (2008)
C/2013 R1 (Lovejoy) 0.37 Ag´undez et al. (2014)
C/2012 K1 (PanSTARRS) 1.33 Cordiner et al. (2017)
C/2012 F6 (Lemmon) 0.96 Bøgelund & Hogerheijde (2017)
C/2012 S1 (ISON) 0.48 Bøgelund & Hogerheijde (2017)
C/2020 F3 (NEOWISE) 2.30 Biver et al. (2022)
46P/Wirtanen 2.70 Cordiner et al. (2023)
67P/Churyumov-Gerasimenko 2.10 Biver et al. (2023)
C/2021 A1 (Leonard) 0.88 Biver et al. (2024)


from the coma region. Using Equation 2, we estimate the production rates of CH 3 OH based on all
detected transitions, which are listed in Table 5. The error bars in production rate values were estimated
based on the error values of _v_ _exp_ and � T mb dV. After averaging those 15 production rate values, we
obtain the final production rate of CH 3 OH towards comet ZTF is (7.32 _±_ 0.64) _×_ 10 [26] molecules s _[−]_ [1] .
The production rate of CH 3 OH towards comet ZTF estimated by Biver et al. (2024) using the Haser
model is 8.78 _×_ 10 [26] molecules s _[−]_ [1], which is very close to our estimated production rate of CH 3 OH
using Equation 2. The abundance of CH 3 OH with respect to H 2 O towards comet ZTF is 1.52 _×_ 10 _[−]_ [2]

(alternatively 1.52%), where the production rate of H 2 O towards comet ZTF is 4.8 _×_ 10 [28] molecules s _[−]_ [1]

(Schleicher et al. 2023).


_3.1.4_ _Comparision of the abundance of CH_ _3_ _OH between ZTF and other comets_


Now, we compare the abundance of CH 3 OH towards comet ZTF with other comets to understand the
ice composition, as shown in Table 6. After comparison, we observe that the comet Austin (1990
V) exhibited a higher CH 3 OH abundance. The abundance of CH 3 OH towards comet ZTF is nearly
similar to that of comets P/Halley, C/2002 T7 (LINEAR), and C/2012 K1 (PanSTARRS). The abundance of CH 3 OH towards the ZTF is lower than that of P/Swift-Tuttle (1992), C/1996 B2 (Hyakutake),
C/1995 O1 (Hale-Bopp), C/1999 H1 (Lee), 153P/2002 C1 (Ikeya-Zhang), C/2020 F3 (NEOWISE),
67P/Churyumov-Gerasimenko, and 46P/Wirtanen. Similarly, the abundance of CH 3 OH towards ZTF is
higher than that of Levy (1990 XX), C/2013 R1 (Lovejoy), C/2012 F6 (Lemmon), C/2012 S1 (ISON),
and C/2021 A1 (Leonard). Since the abundance of CH 3 OH towards ZTF is very similar to P/Halley,
C/2002 T7 (LINEAR), and C/2012 K1 (PanSTARRS), there is a chance that the formation mechanism
of CH 3 OH and the icy compositions of these four comets may be the same.


_3.1.5_ _Formation mechanism of CH_ _3_ _OH) towards comet ZTF_


High-resolution ALMA observations show that CH 3 OH emits from the very deep cometary coma, which
means there is a chance to form this molecule in the grain surface. Previous studies showed that if
CH 3 OH is formed in cometary ices, then this molecule may be an old part of the star formation regions
because comets move from several star-forming regions in the ISM (Remijan et al. 2008). For the production of CH 3 OH, two efficient reactions are available: (i) the radiative association of CH 3 [+] and H 2 O
creates CH 3 OH 2 [+] (CH 3 [+] + H 2 O _→_ CH 3 OH 2 [+] ) and CH 3 OH is formed when CH 3 OH 2 [+] recombine
with an electron in the gas phase (CH 3 OH 2 [+] + e _[−]_ _→_ CH 3 OH), and (ii) the subsequential hydrogena

12 Manna et al.


tion of CO formed CH 3 OH in grain surface (CO + 2H _→_ H 2 CO + 2H _→_ CH 3 OH) (Remijan et al. 2008;
Garrod 2019; Faggi et al. 2023).
Now, we compare our estimated abundance of CH 3 OH with the modelled value of Garrod (2019) to
understand the possible formation pathway of CH 3 OH towards comet ZTF. The estimated abundance of
CH 3 OH towards cometary atmosphere by Garrod (2019) is 1.3 _×_ 10 _[−]_ [2] (1.3%) at 5 _×_ 10 [9] yr (see Table 4
in Garrod (2019)), which was very close to the observed abundance of CH 3 OH towards comet ZTF.
The modelled value of Garrod (2019) is also very close to the abundance of CH 3 OH towards other
comets P/Halley, C/2002 T7 (LINEAR), and C/2012 K1 (PanSTARRS). That indicates CH 3 OH may
be formed via the subsequential hydrogenation of formaldehyde (H 2 CO) on the grain surface of comets
ZTF, P/Halley, C/2002 T7 (LINEAR), and C/2012 K1 (PanSTARRS). Similarly, the chemical models of
Garrod (2019) show that CH 3 OH is destroyed in the cometary atmosphere via photoionization processes
(CH 3 OH + h _ν_ _−→_ CH 2 + H 2 O).


**3.2** **Results based on GMRT data**


After analysing the GMRT data, we did not detect the dust continuum emission from the comet ZTF.
The upper limit flux density of comet ZTF at frequency 1250 MHz was _≤_ 1.50 _±_ 0.21 mJy, where the
synthesized beam size of the continuum emission image was 2.66 _[′′]_ _×_ 1.50 _[′′]_ . After that, we extracted the
atomic spectra by making a 5.0 _[′′]_ diameter circular region over the spectra images. After analysing the
atomic spectra, we could not detect the HI line at 1420 MHz. We estimate the upper limit column density
of atomic HI using the following equation (Chengalur et al. 2013):


_N_ _HI_ = 1 _._ 823 _×_ 10 [18] T s _τ_ dV (3)
�


In the above equation, _T_ _s_ indicates the spin temperature of HI in K, _τ_ is the optical depth of the HI
spectra, and � dv is the integrated area in km s _[−]_ [1] . The equation 3 is well described in Pal & Manna
(2024). We used the value of _T_ _s_ = 100 K (Paris 2017), _τ_ _≤_ 0.23, and � dv _≤_ 0.36. Using Equation 3, we
found the upper limit column density of atomic HI is _≤_ 1.50 _×_ 10 [19] cm _[−]_ [2] .


**4** **CONCLUSION**


In this article, we present the radio and millimeter-wavelength studies of comet ZTF using the GMRT
band L and the ALMA band 6. The principal conclusions derived from this study are summarized below:


1. We detected the dust continuum emission from comet ZTF using the ALMA between the frequency ranges of 223.85 GHz and 243.55 GHz. The activity of dust production (Af _ρ_ ) of comet ZTF is
2280 _±_ 50 cm.


2. We detected the rotational emission lines of CH 3 OH towards comet ZTF using the ALMA. A
total of 15 transition lines of CH 3 OH is detected. Using the LTE model, we found the column density
and excitation temperature of CH 3 OH are (4.50 _±_ 0.25) _×_ 10 [14] cm _[−]_ [2] and 70 _±_ 3 K. From the integrated
emission maps, we observed that the emission lines of CH 3 OH emit from the coma region of the
comet ZTF. The production rate of CH 3 OH on March 2, 2023 is (7.32 _±_ 0.64) _×_ 10 [26] molecules s _[−]_ [1] .
The abundance of CH 3 OH with respect to H 2 O in the coma of the comet is 1.52%. We compared
our derived abundance of CH 3 OH with the modelled value of Garrod (2019), and we noticed that the
observed and modelled values are nearly similar. We claim that CH 3 OH is formed via the subsequential
hydrogenation of formaldehyde (H 2 CO) on the grain surface of comet ZTF.


3. From the GMRT data, continuum emission and emission line of atomic HI are not detected.
The upper limit flux density of comet ZTF at frequency 1250 MHz is _≤_ 1.50 _±_ 0.21 mJy. The upper limit
column density of atomic HI towards comet ZTF is _≤_ 1.50 _×_ 10 [19] cm _[−]_ [2] .

Continuum and spectral lines in C/2020 E3 (ZTF) 13


**ACKNOWLEDGMENTS**


We thank the anonymous reviewers for their helpful comments, which helped to make the manuscript
stronger. A.M. acknowledges the Swami Vivekananda Merit cum Means Scholarship (SVMCM),
Government of West Bengal, for financial support for this research. Supplementary materials, including
additional plots and data, are available from the corresponding author upon reasonable request. We are
grateful to the staff of the Giant Metrewave Radio Telescope (GMRT) for their support during the observation. The raw data of comet ZTF presented in this paper can be accessed through the GMRT archive
using the proposal code ddtC267. The GMRT is operated by the National Centre for Radio Astrophysics
(NCRA), a facility of the Tata Institute of Fundamental Research (TIFR). This paper makes use of the
following ALMA data: ADS /JAO.ALMA#2022.1.00997.T. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The joint ALMA
Observatory is operated by ESO, AUI/NRAO, and NAOJ. We also acknowledge Gideon van Buitenen
[(http://astro.vanbuitenen.nl/comet/2022E3) for providing the track of comets and im-](http://astro.vanbuitenen.nl/comet/2022E3)
ages of the inner solar system.


**CONFLICTS OF INTEREST**


The authors declare no conflict of interest.


**References**


[Ag´undez, M., Biver, N., Santos-Sanz, P., Bockel´ee-Morvan, D., Moreno, R., 2014, A&A, 564, L2](https://doi.org/10.1051/0004-6361/201423639)
[A’Hearn, M. F., Schleicher, D. G., Millis, R. L., Feldman, P. D., Thompson, D. T., 1984, AJ, 89, 579](https://ui.adsabs.harvard.edu/abs/1984AJ.....89..579A/abstract)
[Altwegg, K., & Bockel´ee-Morvan, D. 2003, Space Sci. Rev., 106, 139](https://doi.org/10.1023/A:1024685620462)
Altwegg K., Balsiger H., Bar-Nun A., Berthelier J.-J., Bieler A., Bochsler P., Briois C., et al., 2016,

[SciA, 2](https://www.science.org/doi/full/10.1126/sciadv.1600285)
[Ball, J. A., Gottlieb, C. A., Lilley, A. E., & Radford, H. E., 1970, ApJ, 162, L203](https://adsabs.harvard.edu/full/1970ApJ...162L.203B)
[Biver, N., & Bockel´ee-Morvan, D, 2019, ESC, 3, 1550](https://doi.org/10.1021/acsearthspacechem.9b00130)
Biver, N., Bockel´ee-Morvan, D., Handzlik, B., Sandqvist, A., Boissier, J., Drozdovskaya, M. N.,
[Moreno, R., et al., 2024, A&A, 690, A271](https://doi.org/10.1051/0004-6361/202450921)
Biver, N., Bockel´ee-Morvan, D., Crovisier, J., Sandqvist, A., Boissier, J., Lis, D. C., Cordiner, M., et al.,
[2023, A&A, 672, A170](https://doi.org/10.1051/0004-6361/202245672)
[Biver, N., Bockel´ee-Morvan, D., Colom, P., et al. 1999, EM&P, 78, 5](https://doi.org/10.1023/A:1006229818484)
Biver, N., Bockel´ee-Morvan, D., Crovisier, J., Davies, J. K., Matthews, H. E., Wink, J. E., Rauer, H., et
[al., 1999, AJ, 118, 1850](https://iopscience.iop.org/article/10.1086/301033/meta)
[Biver, N., Bockel´ee-Morvan, D., Crovisier, J., et al. 2000, AJ, 120, 1554](https://iopscience.iop.org/article/10.1086/301529/meta)
[Biver, N., Boissier, J., Bockel´ee-Morvan, D., et al., 2022, A&A, 668, A171](https://doi.org/10.1051/0004-6361/202244970)
[Bockel´ee-Morvan, D., Crovisier, J., Colom, P., Despois, D., 1994a, A&A, 287, 647](https://adsabs.harvard.edu/full/1994A%26A...287..647B)
[Bockel´ee-Morvan, D., Padman, R., Davies, J. K., & Crovisier, J., 1994b, Planet. Space Sci., 42, 655](https://doi.org/10.1016/0032-0633(94)90043-4)
[Bockel´ee-Morvan, D., Calmonte, U., Charnley, S., et al. 2015, Space Sci. Rev., 197, 47](https://doi.org/10.1007/s11214-015-0156-9)
Bockel´ee-Morvan, D., Lis, D. C., Wink, J. E., Despois, D., Crovisier, J., Bachiller, R., Benford, D. J., et
[al., 2000, A&A, 353, 1101](https://adsabs.harvard.edu/full/2000A&A...353.1101B)
[Bolin, B. T., Masci, F. J., Ip, W.-H., et al. 2022, Minor Planet Electronic Circulars (USA: IAU), 2022-](https://ui.adsabs.harvard.edu/abs/2022MPEC....F...13B/abstract)
F13

[Bolin, B., Masci, F., Duev, D., et al. 2024, MNRAS, 527, L42](https://doi.org/10.1093/mnrasl/slad139)
Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., van Dishoeck, E. F., Ilee, J. D., Hogerheijde,
[M. R., Kama, M., et al., 2021, NatAs, 5, 684](https://doi.org/10.1038/s41550-021-01352-w)
[Bøgelund, E. G., & Hogerheijde, M. R., 2017, A&A, 604, A131](https://doi.org/10.1051/0004-6361/201629197)
[Chen, L. F., Li, D., Quan, D., 2022, ApJ, 928, 175](https://iopscience.iop.org/article/10.3847/1538-4357/ac5a45/meta)
[Cordiner, M. A., Biver, N., Crovisier, J., et al., 2017, ApJ, 837, 177](https://iopscience.iop.org/article/10.3847/1538-4357/aa6211/meta)
[Cordiner, M. A., Roth, N. X., Milam, S. N., et al., 2023, ApJ, 953, 59](https://iopscience.iop.org/article/10.3847/1538-4357/ace0bc/meta)

14 Manna et al.


[Chengalur, J. N., Kanekar, N., Roy, N., 2013, MNRAS, 432, 3074](https://doi.org/10.1093/mnras/stt658)
[Drabek-Maunder, E., Greaves, J., Fraser, H. J., Clements, D. L., Alconcel, L. -N., 2019, IJAsB, 18, 25](https://doi.org/10.1017/S1473550417000428)
[Drahus, M., Kuppers, M., Jarchow, C., et al. 2010, A&A, 510, A55](https://doi.org/10.1051/0004-6361/20078882)
Disanti, M. A., dello Russo, N., Magee-Sauer, K., Gibb, E. L., Reuter, D. C., Mumma, M. J., 2002,

[ESASP, 500, 571](https://ui.adsabs.harvard.edu/abs/2002ESASP.500..571D/abstract)
[Eberhardt, P., Meier, R., Krankowsky, D., Hodges, R. R., 1994, A&A, 288, 315](https://adsabs.harvard.edu/full/1994a%26a...288..315e)
[Ehrenfreund, P., & Charnley, S. B., 2000, ARA&A, 38, 427](https://doi.org/10.1146/annurev.astro.38.1.427)
[Faggi, S., Lippi, M., Mumma, M. J., Villanueva, G. L., 2023, PSJ, 4, 8](https://iopscience.iop.org/article/10.3847/PSJ/aca64c/meta)
[Garrod, R. T., 2019, ApJ, 884, 69](https://iopscience.iop.org/article/10.3847/1538-4357/ab418e/meta)
Gillan, A. F., Fitzsimmons, A., Denneau, L., Siverd, R. J., Smith, K. W., Tonry, J. L., Young, D. R.,
[2024, PSJ, 5, 25](https://iopscience.iop.org/article/10.3847/PSJ/ad1394/meta)
[Greenberg, J. M., 1982, come.coll, 131](https://ui.adsabs.harvard.edu/abs/1982come.coll..131G/abstract)
[Hadraoui, K. Cottin, H. Ivanovski, S. L., et al., 2019, A&A, 630, A32](https://doi.org/10.1051/0004-6361/201935018)
[Hartogh, P., Lis, D. C., Bockel´ee-Morvan, D., et al. 2011, Nature, 478, 218](https://doi.org/10.1038/nature10519)
[Herbst, E., & van Dishoeck, E. F., 2009, ARA&A, 47, 427](https://doi.org/10.1146/annurev-astro-082708-101654)
[Jayakrishnan, R., Dev L, R., & Aalim, M. 2023, Res. Notes AAS, 7, 44](https://iopscience.iop.org/article/10.3847/2515-5172/acc185/meta)
[Jehin, E., Donckt, M. V., Manfroid, J., & Moulane, Y. 2022, ATel, 15743, 1](https://ui.adsabs.harvard.edu/abs/2022ATel15743....1J/abstract)
Jehin, E., Donckt, M. V., Manfroid, J., Hmiddouch, S., Moulane, Y., Jabiri, A., Benkhaldoun, Z., 2023,

[ATel, 15973](https://ui.adsabs.harvard.edu/abs/2023ATel15973....1J/abstract)
Kurucz, R. L., Furenlid, I., Brault, J., & Testerman, L. 1984, Solar Flux Atlas from 296 to 1300 nm
[(Sunspot, NM: National Solar Observatory)](https://ui.adsabs.harvard.edu/abs/1984sfat.book.....K/abstract)
[Liu, B., & Liu, X., 2024, A&A, 683, A51](https://doi.org/10.1051/0004-6361/202348663)
[Lellouch, E., Moreno, R., Bockel´ee-Morvan, D., Biver, N., Santos-Sanz, P., 2022, A&A, 659, L1](https://doi.org/10.1051/0004-6361/202243090)
[Manigand, S., Jørgensen, J. K., Calcutt, H., et al., 2020, A&A, 635, A48](https://doi.org/10.1051/0004-6361/201936299)
[Manna, A., & Pal, S., 2024, NewA, 109](https://doi.org/10.1016/j.newast.2024.102199)
[M¨uller, H. S. P., Schl¨oder, F., Stutzki, J., Winnewisser, G., 2005, JMoSt, 742, 215](https://doi.org/10.1016/j.molstruc.2005.01.027)
Mumma, M. J., McLean, I. S., DiSanti, M. A., Larkin, J. E., Dello Russo, N., Magee-Sauer, K., Becklin,
[E. E., et al., 2001, ApJ, 546, 1183](https://iopscience.iop.org/article/10.1086/318314/meta)
[Pal, S., & Manna, A., 2024, J Astrophys Astron, 45, 10](https://doi.org/10.1007/s12036-024-09998-4)
[Paris, A. 2017, J. Wash. Acad. Sci., 103, 1](https://ui.adsabs.harvard.edu/abs/2017arXiv170603259P/abstract)
[Perley, R. A., & Butler, B. J., 2017, ApJ, 230, 1538](https://iopscience.iop.org/article/10.3847/1538-4365/aa6df9/meta)
[Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71](https://doi.org/10.1051/0004-6361/201117104)
Remijan, A. J., Milam, S. N., Womack, M., Apponi, A. J., Ziurys, L. M., Wyckoff, S., A’Hearn, M. F.,
[et al., 2008, ApJ, 689, 613](https://iopscience.iop.org/article/10.1086/592242/meta)
Schleicher, D. G., Knight, M. M., Skiff, B. A., 2023, Asteroids, Comets, Meteors Conference [(LPI](https://ui.adsabs.harvard.edu/abs/2023LPICo2851.2532S/abstract)
[Contributions), 2851, 2532](https://ui.adsabs.harvard.edu/abs/2023LPICo2851.2532S/abstract)
[Schleicher, D. G., 2006, Icarus, 181, 442](https://doi.org/10.1016/j.icarus.2005.11.014)
[Schleicher, D. G., Millis, R. L., Birch, P. V., 1998, Icarus, 132, 397](https://doi.org/10.1006/icar.1997.5902)
[CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501](https://iopscience.iop.org/article/10.1088/1538-3873/ac9642/meta)
[Thiel, V., Belloche, A., Menten, K. M., Garrod, R. T., M¨uller, H. S. P., 2017, A&A, 605, L6](https://doi.org/10.1051/0004-6361/201731495)
[Vastel, C., Bottinelli, S., Caux, E., Glorian, J.-M., Boiziot, M., 2015, sf2a.conf, 313](https://ui.adsabs.harvard.edu/abs/2015sf2a.conf..313V/abstract)
[Womack, M., Stern, S. A., & Festou, M. C. 1997, Planet. Space Sci., 45, 711](https://doi.org/10.1016/S0032-0633(97)00080-9)


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[4].what.evidence[0]",
  "value": "Spin temperature of HI T_s = 100 K",
  "failed_quote": "We used the value of Ts = 100 K (Paris 2017), τ ≤ 0.23, and ∫ dv ≤ 0.36."
 },
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "second-order polynomial fit to line-free channels in visibilities across all spectral windows",
  "failed_quote": "Before imaging, we subtract the continuum from the visibilities by fitting the second-order polynomial to the line-free channels in all spectral windows."
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Equation for production rate Q of CH3OH (Equation 2)",
  "failed_quote": "To derive the production rate (Q) of CH3OH using the line area (∫ T mb dV) and rotational temperature towards comet ZTF, we used the following equation (Drahus et al. 2010):"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Local Thermodynamic Equilibrium (LTE) and optically thin emission lines",
  "failed_quote": "For detection of the rotational emission lines of CH3OH, we used the Local Thermodynamic Equilibrium (LTE) model with the Cologne Database for Molecular Spectroscopy (CDMS) databases (Müller et al. 2005)."
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Calculate production rate Q for each of the 15 transitions using Equation 2 (Drahus et al. 2010), average them, divide by Q(H2O) to get fractional abundance, and compare with Garrod (2019) chemical model.",
  "failed_quote": "To derive the production rate (Q) of CH3OH using the line area (∫ T mb dV) and rotational temperature towards comet ZTF, we used the following equation (Drahus et al. 2010):"
 },
 {
  "path": "analysis_steps[6].key_parameters[0].evidence[1]",
  "value": "5.0'' diameter circular extraction region; tau <= 0.23; int dv <= 0.36 km s^-1",
  "failed_quote": "We used the value of Ts = 100 K (Paris 2017), τ ≤ 0.23, and ∫ dv ≤ 0.36."
 },
 {
  "path": "analysis_steps[6].assumptions[0].evidence[0]",
  "value": "HI spin temperature T_s = 100 K (Paris 2017)",
  "failed_quote": "We used the value of Ts = 100 K (Paris 2017), τ ≤ 0.23, and ∫ dv ≤ 0.36."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": " Spectroscopic database for detection and LTE modelling of CH3OH transitions",
  "failed_quote": "For detection of the rotational emission lines of CH3OH, we used the Local Thermodynamic Equilibrium (LTE) model with the Cologne Database for Molecular Spectroscopy (CDMS) databases (Müller et al. 2005)."
 },
 {
  "path": "results_numeric[15].evidence[1]",
  "value": "CH3OH column density (LTE) = 4.50e14 cm−2",
  "failed_quote": "After spectral line analysis using the LTE model, we found the column density and excitation temperature of CH3OH are (4.50 ± 0.25) × 1014 cm−2 and 70 ± 3 K respectively."
 },
 {
  "path": "results_numeric[16].evidence[1]",
  "value": "CH3OH excitation temperature (LTE) = 70 K",
  "failed_quote": "After spectral line analysis using the LTE model, we found the column density and excitation temperature of CH3OH are (4.50 ± 0.25) × 1014 cm−2 and 70 ± 3 K respectively."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "CH3OH is emitted from the inner coma region of comet ZTF with a higher rotational temperature in the compact ALMA beam than in single-dish IRAM 30-m observations.",
  "failed_quote": "After spectral line analysis using the LTE model, we found the column density and excitation temperature of CH3OH are (4.50 ± 0.25) × 1014 cm−2 and 70 ± 3 K respectively."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Gas-phase ion-molecule formation of CH3OH (CH3+ + H2O -> CH3OH2+, followed by electron recombination) considered alongside grain-surface hydrogenation of CO/H2CO, with grain-surface hydrogenation favored based on comparison with Garrod (2019).",
  "failed_quote": "For the production of CH3OH, two efficient reactions are available: (i) the radiative association of CH3+ and H2O creates CH3OH2+ (CH3+ + H2O → CH3OH2+) and CH3OH is formed when CH3OH2+ recombine with an electron in the gas phase (CH3OH2+ + e− → CH3OH), and (ii) the subsequential hydrogenation of CO formed CH3OH in grain surface (CO + 2H → H2CO + 2H → CH3OH) (Remijan et al. 2008; Garrod 2019; Faggi et al. 2023)."
 }
]
```
