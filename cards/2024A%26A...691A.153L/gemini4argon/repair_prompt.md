# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A.153L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2025
March 3, 2025

## GA-NIFS: JWST/NIRSpec IFS view of the z ∼ 3 . 5 galaxy GS5001 and
### **its close environment at the core of a large-scale overdensity**


Isabella Lamperti [1][,][ 2][,][ 3][,][⋆], Santiago Arribas [1], Michele Perna [1], Bruno Rodríguez Del Pino [1], Chiara Circosta [4][,][ 5],
Pablo G. Pérez-González [1], Andrew J. Bunker [6], Stefano Carniani [7], Stéphane Charlot [8], Francesco D’Eugenio [9][,][ 10],
Roberto Maiolino [9][,][ 10][,][ 5], Hannah Übler [9][,][ 10], Chris J. Willott [11], Elena Bertola [3], Torsten Böker [12], Giovanni Cresci [3],
Mirko Curti [13], Gareth C. Jones [6], Nimisha Kumari [14], Eleonora Parlanti [7], Jan Scholtz [9][,][ 10], and Giacomo Venturi [7]


1 Centro de Astrobiología (CAB), CSIC-INTA, Ctra. de Ajalvir Km. 4, 28850 Torrejón de Ardoz, Madrid, Spain
2 Dipartimento di Fisica e Astronomia, Università di Firenze, Via G. Sansone 1, 50019, Sesto F.no (Firenze), Italy
3 INAF - Osservatorio Astrofisico di Arcetri, largo E. Fermi 5, 50127 Firenze, Italy
4 European Space Agency (ESA), European Space Astronomy Centre (ESAC), Camino Bajo del Castillo s/n, 28692 Villanueva de
la Cañada, Madrid, Spain
5 Department of Physics and Astronomy, University College London, Gower Street, London WC1E 6BT, UK
6 University of Oxford, Department of Physics, Denys Wilkinson Building, Keble Road, Oxford OX13RH, United Kingdom
7 Scuola Normale Superiore, Piazza dei Cavalieri 7, I-56126 Pisa, Italy
8 Sorbonne Université, CNRS, UMR 7095, Institut d’Astrophysique de Paris, 98 bis bd Arago, 75014 Paris, France
9 Kavli Institute for Cosmology, University of Cambridge, Madingley Road, Cambridge, CB3 0HA, UK
10 Cavendish Laboratory - Astrophysics Group, University of Cambridge, 19 JJ Thomson Avenue, Cambridge, CB3 0HE, UK
11 NRC Herzberg, 5071 West Saanich Rd, Victoria, BC V9E 2E7, Canada
12 European Space Agency, c/o STScI, 3700 San Martin Drive, Baltimore, MD 21218, USA
13 European Southern Observatory, Karl-Schwarzschild-Strasse 2, 85748 Garching, Germany
14 AURA for the European Space Agency, Space Telescope Science Institute, Baltimore, MD, USA


March 3, 2025


**ABSTRACT**


We present JWST Near-Infrared Spectrograph (NIRSpec) observations in integral field spectroscopic (IFS) mode of the galaxy
GS5001 at redshift z=3.47, the central member of a candidate protocluster in the GOODS-S field. The data cover a field of view (FoV)
of 4 [′′] × 4 [′′] (∼ 30 × 30 kpc [2] ) and were obtained as part of the Galaxy Assembly with NIRSpec IFS (GA-NIFS) GTO programme.

∼ ∼
The observations include both high (R 2700) and low (R 100) spectral resolution data, spanning the rest-frame wavelength ranges
3700-6780 Å and 1300-11850 Å, respectively. These observations enable the detection and mapping of the main optical emission lines
from [O ii]λλ3726, 29 to [S iii]λ9531. We analysed the spatially resolved ionised gas kinematics and interstellar medium properties,
including obscuration, gas metallicity, excitation, ionisation parameter, and electron density. In addition to the main galaxy (GS5001),
the NIRSpec FoV covers a close companion in the south, with three sub-structures with velocities blueshifted by ∼−150 km s [−][1] with
respect to GS5001, and another source in the north redshifted by ∼ 200 km s [−][1] . Optical line ratio diagnostics indicate star formation ionisation and electron densities of ∼ 500 cm [−][3] across all sources in the FoV. The gas-phase metallicity in the main galaxy is
12+log(O/H) = 8.45 ± 0.04, and slightly lower in the companions (12+log(O/H)= 8.34 − 8.42), consistent with the mass-metallicity
relation at _z_ ∼ 3. We find peculiar line ratios (high log[N ii]/Hα= [−0.45, −0.3], low log[O iii]/Hβ= [0.06, 0.10]) in the northern part of
GS5001. These could be attributed to either higher metallicity, or to shocks resulting from the interaction of the main galaxy with the
northern source. We identify a spatially resolved outflow in the main galaxy, traced by a broad symmetric component in Hα and [O iii],
with an extension of about 3 kpc. We find maximum outflow velocities of ∼ 400 km s [−][1], an outflow mass of (1.7 ± 0.4) × 10 [8] M ⊙,
a mass outflow rate of 23 ± 5 M ⊙ yr [−][1], and a mass loading factor of 0.23. These properties are compatible with star formation being
the driver of the outflow. Our analysis of these JWST NIRSpec IFS data therefore provides valuable, unprecedented insights into the
interplay between star formation, galactic outflows, and interactions in the core of a _z_ ∼ 3.5 candidate protocluster.


**Key words.** galaxies: evolution – galaxies:high-redshift – galaxies:ISM



**1.** **Introduction**


Understanding the complex processes governing galaxy formation and evolution in the early Universe requires detailed observations of their interstellar medium (ISM) properties and kinematics. The ISM’s physical properties and kinematics provide
essential clues to the mechanisms driving galaxy evolution, including star formation, gas inflows and outflows, and the chemical enrichment (e.g. Naab & Ostriker 2017; Cresci & Maiolino


⋆ E-mail: isabella.lamperti@unifi.it



2018; Maiolino & Mannucci 2019). Over the past few decades,
several studies have investigated how the ISM properties evolve
with cosmic time, focussing for instance on the ionisation parameter, electron density and temperature, and metallicity (e.g.
Nakajima & Ouchi 2014; Kaasinen et al. 2017, 2018; Davies
et al. 2021; Curti et al. 2024; Reddy et al. 2023a,b; Sanders et al.
2016, 2021, 2024).
One of the most significant advancements in this field has
been the advent of spatially resolved studies of galaxies at redshifts of _z_ = 1−3. These studies have highlighted the importance


Article number, page 1 of 28

_A&A proofs:_ manuscript no. main



of resolving the inner structure of the ISM properties in order to
understand galaxy evolution (e.g. Cresci et al. 2010; Troncoso
et al. 2014; Stott et al. 2016; Curti et al. 2020a; Gillman et al.
2022). Spatially resolved observations of optical emission lines
have also allowed the study of the internal kinematics of galaxies
up to high redshift ( _z_ ∼ 1 − 3, e.g. Wisnioski et al. 2015, 2019;
Harrison et al. 2017; Förster Schreiber et al. 2018; van Houdt
et al. 2021; Genzel et al. 2023; Übler et al. 2024b). These studies have also identified and characterised outflows powered by
active galactic nuclei (AGN) and star-bursts (e.g. Genzel et al.
2014; Förster Schreiber et al. 2014, 2019).
The ability to resolve the internal structure of galaxies is crucial for understanding how they evolve over time and how the
conditions within their ISM change. By mapping the distribution of star formation, one can determine where stars are forming within a galaxy, and hence whether star formation is concentrated in the nucleus or more spread out across the disc (e.g.
González Delgado et al. 2016; Spindler et al. 2018). Mapping
gradients of gas-phase metallicity allows us to study the flows
of gas within galaxies and where the enrichment of metals of
the ISM takes place (e.g. Cresci et al. 2010; Maiolino & Mannucci 2019). Moreover, the internal kinematics of galaxies allow
us to assess whether galaxies at high redshift were already settled into well-ordered rotating discs or if they exhibited more
chaotic, turbulent motions. Additionally, kinematic information,
gas-phase metallicity, and star formation distributions are essential for understanding the role of inflows and outflows in regulating the growth of galaxies across cosmic time (e.g. Naab &
Ostriker 2017; Nelson et al. 2019; Förster Schreiber & Wuyts
2020; Scharré et al. 2024).
At cosmic noon ( _z_ = 1 − 2), many of these studies have
been performed using ground-based facilities with near-infrared
integral field spectroscopy (IFS) instruments. However, groundbased observations are limited in their ability to probe beyond a
redshift of _z_ ∼ 2.5 for emission lines like Hα, and up to _z_ ∼ 3.5
for Hβ and [O iii]. These transitions are key to infer the ISM
chemical and kinematic properties. The IFS capabilities of the
NIRSpec instrument (Jakobsen et al. 2022; Böker et al. 2022) on
board the _James Webb_ Space Telescope (JWST) enable one for
the first time to map the optical lines at _z_ - 3 with a spatial resolution of ∼ 0.1". Several works have demonstrated the capability
of JWST/NIRSpec integral field units to study the ISM properties and gas kinematics in star-forming galaxies and AGN host
galaxies at _z_ - 3 (e.g. Wylezalek et al. 2022; Übler et al. 2023,
2024a,c; Perna et al. 2023; Arribas et al. 2024; Parlanti et al.
2024; Vayner et al. 2024; Wang et al. 2024; Roy et al. 2024;
Saxena et al. 2024).
In this work, we present JWST/NIRSpec IFS observations
of the galaxy GS5001 and its close companions. GS5001 (also
known as Candels-5001 and as ID 4417 in the GOODS-MUSIC
catalogue, Grazian et al. 2006) is a Lyman-break selected galaxy
in the GOODS-S field at z=3.473 (Maiolino et al. 2008) at
co-ordinates R.A. 03h32m23.35s, Dec. −27 [◦] 51’57.13” (J2000).
Two other galaxies detected in the HST/UV images lie in a
close projected separation (1-2 [′′], 7-15 kpc): GS4921 to the south
(ID 4414 in the GOODS-MUSIC catalogue) and GS4923 to the
north (see central panel in Fig. 1). GS4921 was confirmed to
be at a similar redshift ( _z_ = 3.471), based on VLT/SINFONI
observations (Maiolino et al. 2008). GS4923 has a photometric redshift of 0.2 (Pérez-González et al. 2005), but some [O iii]
emission at a similar redshift of 3.47 was tentatively identified at
its location using VLT/SINFONI data (Ginolfi et al. 2017).
GS5001 is the central member of a system classified as a
candidate protocluster, as it lies in a large-scale overdensity of


Article number, page 2 of 28



galaxies (Franck & McGaugh 2016). Ginolfi et al. (2017) detect
a large reservoir of molecular gas, traced by CO(4–3), which extends up to 40 kpc around this system. Additionally, they detect several CO(4–3)-emitting systems within a radius of 250
kpc, mostly distributed along the same northeast-southwest direction as the CO(4–3) reservoir (see their Fig. 9); they suggest
that these systems are tracing the inner and densest regions of a
large-scale accreting stream feeding the central massive galaxy
GS5001.
GS5001 has a star formation rate (SFR) in the range 150240 M ⊙ yr [−][1] (Troncoso et al. 2014; Pacifici et al. 2016; PérezGonzález et al. 2005; Guo et al. 2013), derived from spectral
energy distribution (SED) fitting of the UV to FIR photometry, and a stellar mass in the range _M_ ⋆ = 1 − 4 × 10 [10] M ⊙
(Maiolino et al. 2008; Pérez-González et al. 2005; Guo et al.
2013; Santini et al. 2015; Pacifici et al. 2016). The southern
companion, GS4921, has SFR = 35 − 70 M ⊙ yr [−][1] and stellar
mass _M_ ⋆ = 0.5 − 2.3 × 10 [10] M ⊙ (Maiolino et al. 2008; PérezGonzález et al. 2005; Guo et al. 2013). All values reported here
have been homogenised to a Chabrier (2003) IMF. GS5001 is
also detected in the X-ray, although with a small number of
counts (20 counts), and has an aperture corrected X-ray luminosity of _L_ 0.5−7 keV = 9.5 × 10 [42] erg s [−][1] (Fiore et al. 2012; Luo et al.
2017). Despite the high X-ray luminosity, it is not clear whether
this object hosts an AGN, because its very high SFR could be
responsible for most of the X-ray flux (Fiore et al. 2012).
The goal of this work is the detailed characterisation of the
physical and kinematic properties of GS5001 and its close environment. Other recent studies characterising dense environments
in the early universe using JWST/NIRSpec IFS include those by
Perna et al. (2023, LBQS 0302-0019; a dual AGN with multiple companions at _z_ ∼ 3.3), Rodríguez Del Pino et al. (2024,
GS4891; a galaxy group at _z_ ∼ 3.7), Jones et al. (2024a, HZ10;
a galaxy group at _z_ ∼ 5.7), Jones et al. (2024b, HFLS3; an overdensity at _z_ ∼ 6.3), and Arribas et al. (2024, SPT0311-58; a
protocluster core at _z_ ∼ 6.9). This paper is organised as follows.
Section 2 presents the JWST/NIRSpec observations and the data
reduction. In Section 3 we describe the different components of
the GS5001 system. Section 4 describes the method used for the
emission line fitting. In Section 5 we present the results. First,
we show the ionised gas kinematics (Sec. 5.1) and then the properties of the ISM (attenuation, source of excitation, metallicity,
ionisation parameter, electron density, Sec. 5.2). The Discussion
is in Section 6 and the Conclusions in Section 7.
Throughout this work, we assume a cosmological model
with Ω λ = 0.7, Ω M = 0.3, and _H_ 0 = 70 km s [−][1] Mpc [−][1], which
results in a scale of 7.34 kpc/arcsec at _z_ = 3.47. In this work, we
assume a Chabrier (2003) initial mass function (IMF).


**2.** **Observations and data reduction**


_2.1._ _JWST/NIRSpec observations_


We present observations of GS5001 obtained on December 10
2022 as part of the Galaxy Assembly with NIRSpec Integral
Field Spectroscopy (GA-NIFS [1] ) GTO programme (PIs: S. Arribas, R. Maiolino), contained within programme #1216 (PI:
K. Isaak). The main goal of GA-NIFS is to study the internal
structure and the close environment of a sample of 55 galaxies
and AGN at _z_ = 2 − 11 (Perna 2023).
GS5001 was observed with NIRSpec IFS (Böker et al. 2022;
Rigby et al. 2023) both with the high-resolution ( _R_ ∼ 2700)


1 [https://ga-nifs.github.io](https://ga-nifs.github.io)

I. Lamperti et al.: JWST/NIRSpec view of GS5001



HST/ACS F775W





53 _[◦]_ 05 _[′]_ 52 _[′′]_ 51 _[′′]_ 50 _[′′]_ 49 _[′′]_ 48 _[′′]_

R _._ A _._ (J2000)



2.00


1.00


0


- 1.00



2.00


1.00


0


- 1.00



NIRSpec [OIII]







0.8


0.6


0.4


0.2


0.0


0.2


0.4


0.6




- 2.00

|GS4923<br>GS5001<br>GS4921<br>5kpc|Col2|
|---|---|
|5 kpc<br>GS5001<br>GS4921<br>GS4923||
|5 kpc<br>GS5001<br>GS4921<br>GS4923||


2.00 1.00 0   - 1.00   - 2.00
∆R. A. [arcsec]



8


6


4


2


0




- 2.00

|n3 n2 n1<br>north<br>main<br>south<br>c<br>5kpc s3<br>s2 s1|0<br>0<br>0<br>0<br>0|Col3|
|---|---|---|
|5 kpc<br>s1<br>s2<br>s3<br>n1<br>n2<br>n3<br>c<br>main<br>south<br>north|||
|5 kpc<br>s1<br>s2<br>s3<br>n1<br>n2<br>n3<br>c<br>main<br>south<br>north|||
|5 kpc<br>s1<br>s2<br>s3<br>n1<br>n2<br>n3<br>c<br>main<br>south<br>north|||
|5 kpc<br>s1<br>s2<br>s3<br>n1<br>n2<br>n3<br>c<br>main<br>south<br>north|||


2.00 1.00 0   - 1.00   - 2.00
∆R. A. [arcsec]



Fig. 1: Identification of galaxies and structures around GS5001. _Left:_ NIRCam three-colour image of GS5001 (F090W filter in
blue, F200W filter in green and F444W filter in red). _Middle:_ HST/ACS F775W band image with contours of the NIRSpec [O iii]
emission in red. In blue are the names of the sources identified in CANDELS. _Right:_ NIRSpec [O iii] flux map with contours of
the HST ACS/F775W emission in black. Blue and green regions mark the different components identified in the [O iii] map, from
which we extracted the integrated spectra reported in Fig. 4 and Fig. G.1 in the appendix. The green crosses show the centre of the
continuum emission in the HST/WFC3 F125W filter, used for astrometric registration.



and with the low-resolution ( _R_ ∼ 100) mode. The R2700 observations use the grating/filter pair G235H/F170LP, covering
the wavelength range 1.66 − 3.16 µm with a spectral resolution
R∼ 1900 − 3500, corresponding to σ ∼ 35 − 70 km s [−][1] (Jakobsen
et al. 2022). The R100 PRISM/CLEAR data covers the range
0.6 − 5.3 µm with R∼ 30 − 300, corresponding to σ ∼ 300 −
4000 km s [−][1] (Jakobsen et al. 2022). Both observations were taken
using an IRS [2] detector readout pattern (NRSIRS2 for R2700
and NRSIRS2RAPID for R100; Rauscher et al. 2017), which
significantly reduces the detector noise with respect to the standard procedure. The R2700 observations have an exposure time
of 4.1 hours, while the R100 observations an exposure time of
1.1 hours. We use an 8-point medium cycling dither pattern,
which provides a total observed field of view (FoV) of ∼ 4” × 4”
(∼ 30 × 30 kpc [2] at the redshift of the target).


_2.2._ _Data reduction_


The raw data were reduced with the JWST calibration pipeline
version 1.8.2, using the CRDS context file _jwst_1068.pmap_ . The
default reduction pipeline was modified to improve the data quality, as is explained in detail in Perna et al. (2023) and D’Eugenio
et al. (2023). We build the final cubes with a spaxel size of 0.05"
using the ‘drizzle’ method.
For the subtraction of the background emission from the
R100 data cube, we extract spectra from spaxels in regions of the
FoV where no galaxy emission is present and calculate a median
spectrum. Then, we subtract this median spectrum from the data
cube. The background subtraction is not needed for the R2700
data, as the background contribution is not significant and it is
accounted for during the line fitting procedure.
We note that the noise given in the data cube (‘ERR’ extension) is underestimated compared to the actual noise in the
data. Therefore, we re-scale the ‘error’ vector in each spaxel by
a factor of (median 1.6) to match the noise estimated from the
standard deviation of the continuum in spectral regions free of
line emission (following the method used by e.g. Übler et al.
2023; Rodríguez Del Pino et al. 2024). Specifically, we selected
the continuum spectral regions 4700 − 4800 Å, 5050 − 5200 Å,
and 6000 − 6400 Å (rest-frame wavelength).



Fig. 2 shows the R2700 and R100 spectra extracted from the
central 3×3 spaxels of the main galaxy. This figure illustrates the
wavelength range spanned by the two spectra, the main emission
lines and the quality of the data.


_2.3._ _Ancillary data_


In addition to the NIRSpec data, we also consider other observations of GS5001. In particular, we use images from HST and
JWST/NIRCam, and ALMA observations of the CO(4–3) emission line.


The HST/ACS WFC F755W and HST/WFC3 F125W images of GS5001 have been downloaded from the Rainbow Cosmological Survey database [2] . The astrometric alignment is explained in the following section. We also download publicly
available JWST/NIRCam images (F090W, F200W, F444W) of
GS5001 from the multi-object JWST Deep Extragalactic Survey
(JADES; Eisenstein et al. 2023; Rieke et al. 2023). The astrometric alignment of the NIRCam images is described in Rieke
et al. (2023).


In this work, we also use ALMA Band 3 observations of the
CO(4–3) emission line at rest-frequency 461.04 GHz (project
ID 2012.1.00423.S, P.I. T. Nagao), which have been presented
in Ginolfi et al. (2017). We obtain the calibrated measurement
sets (MS) from the European ALMA Regional Centre (ARC).
We create a data cube of the CO(4–3) spectral window using
the ALMA data reduction software `CASA` v6.2.1 (CASA Team
et al. 2022). We use the CASA task `tclean` applying natural
weighting to generate a data cube with synthesised beam FWHM
1.9 × 1.3 arcsec [2] . The original spectral resolution of the observations is ∼ 2.5 km s [−][1] and we binned the spectral channels to
reach a resolution of ∼ 10 km s [−][1] . The CO(4–3) intensity map
(moment 0) is produced by integrating the continuum subtracted
data cube in the spectral channels within ±800 km s [−][1] from the
CO(4–3) emission frequency at _z_ = 3.47.


2 [https://arcoirix.cab.inta-csic.es/Rainbow_Database/](https://arcoirix.cab.inta-csic.es/Rainbow_Database/)


Article number, page 3 of 28

3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.40


0.35


0.30


0.25


0.20


0.15


0.10


0.05


0.00



4000 5000 6000 7000 8000 9000
rest − frame wavelength [Å]



_A&A proofs:_ manuscript no. main


4000 4500 5000 5500 6000 6500
rest − frame wavelength [Å]


obs. wavelength [µm]
2.0 2.5 3.0 3.5 4.0





Fig. 2: Average rest-frame spectrum of the main galaxy central 3 × 3 spaxels (0.15 [′′] × 0.15 [′′] ), from the high-resolution ( _R_ ∼ 2700,
upper) and low-resolution ( _R_ ∼ 100, lower) NIRSpec data. The aperture was chosen as it is representative of the aperture used
for the spaxel-by-spaxel fit. For R100, only the portion of the spectrum with the lines of interest is shown. Vertical dashed lines
mark the position of the detected emission lines. The shaded grey area shows the error on the fluxes. The magenta line in the R100
panel shows the wavelength range covered by the R2700 data. The light blue lines show the wavelength ranges used to create the
continuum maps shown in Fig. 3.



3.1 − 4.0 µm


14


12


10


8


6


4


2


0


2.00 1.00 0 - 1.00 - 2.00
∆RA [arcsec]



2.00


1.00


0


- 1.00



1.7 − 2.0 µm



10.5


9.0


7.5


6.0


4.5


3.0



2.3 − 2.8 µm


10.5


9.0


7.5


6.0


4.5


3.0


1.5


0.0


2.00 1.00 0 - 1.00 - 2.00
∆RA [arcsec]



1.5


0.0

- 2.00

2.00 1.00 0   - 1.00   - 2.00
∆RA [arcsec]



Fig. 3: Continuum maps obtained collapsing the R100 data cube over three different (observed) wavelength ranges, as is indicated
above the panels. The wavelength ranges are also shown in the R100 spectrum in Fig. 2. The green ellipses indicate the three main
components (‘main’, ‘south’ and ‘north’), the light blue circles indicate the identified sub-clumps.



_2.4._ _Astrometry_


We register the astrometry of the NIRSpec data by matching
the central position of the target GS5001 in the NIRSpec data
cube and in the HST/WFC3 F125W band image, after aligning the HST image to the _Gaia_ co-ordinates frame. To derive
the absolute astrometry of the HST image, we used the two


Article number, page 4 of 28



stars present in a 90 [′′] × 90 [′′] FoV around GS5001 and calculated the mean offset of their position from the co-ordinates reported in the _Gaia_ DR3 catalogue (Gaia Collaboration et al.
2016; Gaia Collaboration et al. 2023). The derived offset (coord(HST)-co-ord( _Gaia_ )) is ∆R.A. = −0.1969 ± 0.0430 arcsec
and ∆Dec. = −0.27479 ± 0.0081 arcsec. The uncertainties, cal

I. Lamperti et al.: JWST/NIRSpec view of GS5001



culated from the standard deviation of the offsets of the two stars,
are 43mas in R.A. and 8mas in Dec.

Then, we align the position of the peak emission of our target (GS5001) in the HST/WFC3 125W band, derived with a 2D
Gaussian fit, and in an image created by collapsing the NIRSpec
R100 data cube over a similar wavelength range (1.1 − 1.4µm
observed wavelength). In this way, we derive a correction of
∆R.A. = −0.1291 arcsec and ∆Dec. = −0.1554 arcsec for the
astrometry of the NIRSpec data cubes. This offset is consistent
with the expected accuracy of JWST pointing without a dedicated target acquisition procedure (Böker et al. 2023). We check
that the positions of the other sources in the FoV are well aligned
in the HST and NIRSpec image, so no rotation term is considered.


**3.** **Description of the GS5001 system**


Figure 1 shows the map of the integrated [O iii] flux of the system (right panel) obtained from the emission line fit of the R2700
NIRSpec data cube (see Sec. 4), together with the HST/ACS
F755W image (central panel) and a NIRCam three-colour image (left panel; F090W filter in blue, F200W filter in green and
F444W filter in red). The ionised gas emission extends over
more than 20 kpc and is divided in different structures: a central
galaxy, and two other components, one extending to the northeast and one to the south-west.

In the south component, we identify three sub-structures (s1,
s2, s3), two of which are well detected in the HST/ACS image
(s1 and s2). These two sub-structures were previously identified
in the CANDELS catalogue as the source GS4921 (Guo et al.
2013, see Fig. 1). In the north, the [O iii] emission is concentrated in a region to the east of the UV-bright galaxy detected
in the HST/ACS image, with CANDELS identifier 4923. This
galaxy has a photometric redshift of _z_ = 0.2 (Pérez-González
et al. 2005). Given the lack of emission lines in the NIRSpec
data cubes, it is indeed compatible with being a low-redshift
foreground galaxy. The [O iii] emission in the north shows three
peaks (n1, n2, n3) and a long tail elongated towards the southeast. The [O iii] emission detected in the SINFONI data to the
north of GS5001, with a similar redshift of _z_ ∼ 3.47 and originally attributed to GS4923 (Ginolfi et al. 2017), is likely coming
from the north companion (see Fig. 1). We identify an additional
clump (‘c’) to the south-west of the main source, which is clearly
visible in the velocity channels [130 − 150] km s [−][1] (see Fig. D.1
in the appendix). We shall discuss the nature of this clump in
Section 6.1. We also detect diffuse ionised gas emission in the
regions in between the three components (called ‘main’, ‘south’
and ‘north’ from now on).
To investigate the nature of the north and south components,
we construct continuum maps by collapsing the R100 data cube
in three wavelength ranges that are free from strong line emission: 1.7–2.08 µm, 2.3–2.8 µm and 3.1–4.0 µm (observed wavelength). We could not use the NIRCam images for this purpose
because they are contaminated by strong emission lines ([O ii],

[O iii], [S iii]). The south component and its three sub-clumps are
detected in the three continuum bands (see Fig. 3). The source
s3 is fainter than the other two, but it is well detected in continuum. The north component is also detected in the three continuum bands. The continuum is strongest where the n1 peak is
located, and fainter in the position of the n3 peak.
The presence of extended [O iii] and continuum emission
suggests that GS5001 is in a complex environment, with two
close companions and evidence of gravitational interactions. The



nature of each substructure in the three systems is further investigated in the next sections.


**4.** **Analysis: Emission line fitting**


To derive the properties of the ionised gas in this system, we
use two approaches. First, we run a spaxel-by-spaxel fit, which
allows us to derive spatially resolved maps of the gas physical
conditions and kinematics. Since some emission lines are faint,
we also extract aperture spectra from different regions of the system to increase the S/N and derive more robust measurements of
their physical properties. The apertures used to extract the spectra are shown in the right panel of Fig. 1. In particular, we extract
the spectra of the ‘main’ galaxy and the two ‘north’ and ‘south’
components (green ellipses in Fig. 1). Additionally, we extract
spectra of the ‘sub-structures’ identified as [O iii] peaks (n1, n2,
n3, s1, s2, s3) and the clump ‘c’ (blue circles in Fig. 1).


_4.1._ _R2700 data_


In this section, we describe the method used to derive the emission line properties by fitting the R2700 data cube. We first measure the continuum level by taking the mean of the flux in two
continuum spectral windows free from emission lines on the two
sides of the Hα line. In the cases where the continuum is detected
(i.e. the mean flux is larger than zero), we model it by interpolating the flux across the entire wavelength range, excluding the
spectral regions within ±10 Å from the position of the emission
lines. We interpolate the flux using a Savitzky-Golay filter (Savitzky & Golay 1964) and first-order polynomials. If the continuum is not detected, we do not apply this interpolation.
After subtracting the continuum, we fit the following emission lines: Hα, Hβ, Hγ, [O iii]λλ4959,5007, [N ii]λλ6548,6583,

[S ii]λλ6716,6731, [O ii]λλ3726,3729, [O i]λ6300. We fit all
these lines simultaneously using a combination of Gaussian profiles. We force the kinematic parameters (velocity centroid and
line velocity width) of all lines to be the same. We fix the flux ratio of the [N ii]λ6583/[N ii]λ6548 and [O iii]λ5007/[O iii]λ4959
lines to the theoretical value 2.99 (Osterbrock & Ferland 2006).
The relative flux of the [O ii] and [S ii] doublets is allowed to vary
between 0.384 < [O ii]λ3729/ [O ii]λ3726 < 1.456 and 0.438 <

[S ii]λ6716/[S ii]λ6731 < 1.448, which correspond to the theoretical limits for densities in the range 1 − 10 [5] cm [−][3] (Sanders
et al. 2016). To retrieve the intrinsic line width, we convolve the
Gaussian profiles with the line spread function at the corresponding wavelength during the fitting procedure, using the resolving
power as a function of wavelength presented in Jakobsen et al.
(2022) [3] .
We consider two models: one with a single Gaussian and one
with two Gaussian components (narrow+broad) for each emission line. For the one-component model, we constrain the width
of the line to be 20 km s [−][1] < σ < 300 km s [−][1] . We set the
lower limit due to the spectral resolution, and the higher value
to guide the fit and avoid fitting noise. For the two-component
model, we constrain the width of the narrow component to be
20 km s [−][1] < σ _n_ < 120 km s [−][1] and the width of the broad component to be 140 km s [−][1] < σ _b_ < 300 km s [−][1] . We use as initial guess
for the redshift the value _z_ = 3.473 (Maiolino et al. 2008).
- _Spaxel-by-spaxel spectral fit_ :
We fit the emission lines across the FoV of the data cube to derive spatially resolved properties. In order to increase the S/N,


3 Downloaded from [https://jwst-docs.stsci.edu/jwst-near-infrared-](https://jwst-docs.stsci.edu/jwst-near-infrared-spectrograph/nirspec-instrumentation/nirspec-dispersers-and-filters)
[spectrograph/nirspec-instrumentation/nirspec-dispersers-and-filters.](https://jwst-docs.stsci.edu/jwst-near-infrared-spectrograph/nirspec-instrumentation/nirspec-dispersers-and-filters)


Article number, page 5 of 28

_A&A proofs:_ manuscript no. main



we calculate the average of the spectrum in the selected spaxel
and in the eight adjacent spaxels (3 × 3). We fit the emission
lines using the Python routine ‘scipy.optimize.curve_fit’, which
uses non-linear least-squares to fit a function to data. We fit the
data cube with the one-component and two-component models, and then we select the number of components to use in
each spaxel based on the Bayesian Information Criterion (BIC,
Schwarz 1978). We select the two-component model if it causes
an improvement in the BIC larger than 20%.
In Fig. B.1 in the appendix we show the spectrum of one
spaxel together with its best-fit model as an example. Figure 5 shows the maps of the Hα flux and kinematics obtained
with the best-fit model. For comparison, we also report in
Fig. Fig. C.1 the appendix the velocity maps obtained with the
one-component Gaussian fit, showing no significant differences
from those in Fig. 5. The S/N in each line is calculated by taking
the ratio of the amplitude of the best-fit model over the noise,
estimated by taking the standard deviation of a close spectral region free of line emission.

_Spatially integrated spectral fit:_
We also fit the integrated R2700 spectra of the different components of the system identified in Figure 1. Specifically, we extract
integrated spectra of the main galaxy, the south component and
its three sub-structures in the south (s1, s2, s3), the north component and its three sub-structures (n1, n2, n3). The positions and
sizes of the apertures are reported in Table 1 and shown in Figure 1. We use the same methodology (same model and parameter
constraints) as for the spatially resolved fit. In this case, we fitted
the spectra using the Markov chain Monte Carlo (MCMC) programme `emcee` (Foreman-Mackey et al. 2013), which allows us
to robustly estimate the uncertainties. The MCMC approach was
not used for the spatially resolved fit because it is too computationally expensive. We assume a Gaussian likelihood and use
uniform priors within the velocity ranges specified above. We
derive the best-fit parameters by taking the median values from
the marginal posterior distributions. The uncertainties are given
as the average of the differences between the median and the
16th and 84th percentiles of the posterior distributions. To decide whether a two-component model is needed, we use the BIC,
and require that BIC(2comp) is smaller than the BIC(1comp) by
- 20%. The two-component model is needed only for the spectrum of the main galaxy.
he integrated spectrum of the main galaxy together with the
best-fit model is shown in Fig. 4. The integrated spectra of the
other components (south, north, s1, s2, s3, n1, n2, n3, c) are
shown in Fig. G.1 in the appendix. In Table 1 we report physical properties derived for the different regions, while the integrated fluxes measured from the integrated spectra are reported
in Table A.1.


_4.2._ _R100 data_


We fit the R100 data cube to extract the [S iii]λλ9069, 9531
line fluxes, since this wavelength range is not covered by
the R2700 data (see Fig. 2). These fluxes, together with the

[S ii]λλ6717, 6731 fluxes, will be used to estimate the ionisation parameter, as is described in Sec. 5.2.5. We use the same
methodology as for the fit of the R2700 data cube. In this case,
we do not convolve the line width with the line spread function
of the NIRSpec PRISM, as we note that in some regions the
emission lines are narrower than the pre-flight estimates of the
spectral resolution curve reported in Jakobsen et al. (2022). This
does not affect our results as we are only interested in extracting
the line fluxes from the R100 data and not the kinematics.


Article number, page 6 of 28



The continuum is modelled and subtracted before the emission line fit using the same method described above for the
R2700 data. Given the low spectral resolution, we just employ
one Gaussian to model each line. We model simultaneously the
two [S iii] lines, using a single Gaussian component for each line
with the same width (in velocity space). We also fit the Hα, [N ii]
and [S ii] complex in a separate fit, forcing the line width to be
the same for all the lines. The spectral resolution is too low to
resolve the [S ii] doublet, but for the purpose of deriving the
ionisation parameter, we only need the sum of the fluxes of the
two lines. As specified above, we use the [S iii] fluxes together
with the [S ii] fluxes to estimate the ionisation parameter. For this
aim, we use [S iii] and [S ii] fluxes derived from the same cube
(R100) to avoid potential discrepancies in the flux calibration
of the R100 and R2700 observations (e.g. Arribas et al. 2024).
Table A.2 reports the measured fluxes of the [S ii] and [S iii] doublets derived from the R100 data cube for the different regions.


**5.** **Results**


_5.1._ _Kinematic properties_


5.1.1. Velocity maps


Figure 5 shows the maps of the Hα line derived from the fit with
one or two Gaussian components. The optimal number of Gaussian components to be used in each spaxel was selected based
on a BIC threshold. Only spaxels with peak S/N> 3.5 in the Hα
line are shown. The maps show the total observed line flux (not
corrected for obscuration), the velocity at the peak of the line,
and the line width W80 (width encompassing 80% of the total line emission, calculated as the difference between the 10th
and 90th percentiles velocities). The zero velocity is determined
based on the redshift of the central target, derived from the integrated spectrum ( _z_ = 3.4705 ± 0.0001).
The southern clumps s1, s2, and s3 have velocities
blueshifted by −160, −153, −80 km s [−][1], respectively, with respect to the central galaxy (see Table 1). The northern clumps
n1, n2, and n3 instead are redshifted by 213, 218, 182 km s [−][1],
respectively, and the tail shows a velocity gradient going from
∼ 100 km s [−][1] close to the north galaxy to −100 km s [−][1] towards
the SE direction.

In the central galaxy, we see a gradient with the velocity increasing from –30 km s [−][1] in the north-east to 50 km s [−][1] in the
south-west. If we interpret this gradient as rotation, the kinematic
major axis is roughly along the NE-SW direction. We note that
the direction of this velocity gradient (kinematic major axis) is
not aligned with the photometric major axis, which is roughly
in the north-south direction (shift of ∼ 40 [◦] between photometric
and kinematic major axes), as commonly observed in interacting systems and mergers at low-redshift (e.g. Barrera-Ballesteros
et al. 2015; Perna et al. 2022). The peak velocity increases at the
location of the clump ‘c’, which indeed has a velocity redshifted
by ∼ 140 km s [−][1] . If we were to exclude this clump, the velocity
gradient could be more aligned with the E-W direction, instead
of NE-SW. However, the low S/N prevents us from separating
the clump ‘c’ from the rest of the galaxy, so, the direction of the
kinematic axis remains uncertain.

We note that the velocities of the companions do not follow the rotation of the central target. The NE part of the central
target has blueshifted velocities, while the north companion has
redshifted velocities. Similarly, the SW part of the central target shows redshifted velocities while the south companions have
bluer velocities.

I. Lamperti et al.: JWST/NIRSpec view of GS5001



100


50


0


15
10
10 [505]
15
20


200


150


100


50


0


15
10
10 [505]
15
20



3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]


v : 0 ± 1 km/s
σ : 68 ± 2 km/s
v(b) : − 25 ± 4 km/s
σ(b) : 222 ± 10 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]



4300 4320 4340 4360 4380 4400
rest. wavelength [A]


6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]



4850 4900 4950 5000
rest. wavelength [A]


6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]



Fig. 4: Integrated spectrum of GS5001 (‘main’ source in Fig. 1). Data are shown in black, the total best fit in blue, the narrow and
broad components are shown in light blue and red, respectively, shifted vertically for visual purposes. The vertical lines mark the
wavelength positions of the emission lines at the systemic redshift of the source ( _z_ = 3.4705). The fitting residuals are shown in the
bottom panel.


Table 1: Physical properties of the different components of the system.


region ∆RA ∆Dec apert. angle SFR A _V_ 12+log(O/H) log U n _e_ _v_ σ

[arcsec] [arcsec] [arcsec] [degrees] [M ⊙ yr [−][1] ] [mag.] [cm [−][3] ] [km s [−][1] ] [km s [−][1] ]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)
main [∗] 0 0 0.25×0.45 0 180±1 1.54±0.07 8.45±0.04 –2.9±0.1 540 [+] − [120] 100 –1±1 93±1
main narrow 100±2 1.37±0.14 8.45±0.04 - - 0±1 68±2

main broad - 2.29±0.53 8.47±0.07 - - –25±4 222±10
south –1.29 –1.00 0.55×0.30 -20 76±1 1.31±0.09 8.39±0.04 –3.1±0.1 750 [+] − [220] 180 [–133][±][1] 80±1
north 0.40 0.95 0.45×0.25 -10 106±1 2.44±0.16 8.39±0.06 –2.8±0.1 150 [+] − [130] 90 191±1 100±2
s1 –1.75 –1.05 0.20×0.20 0 12±1 0.63±0.20 8.36±0.07 –2.7±0.2 - –161±2 68±2
s2 –1.29 –1.00 0.20×0.20 0 19±1 1.34±0.13 8.41±0.04 –3.2±0.1 630 [+] − [210] 180 [–154][±][1] 77±1
s3 –0.84 –0.80 0.20×0.20 0 30±1 1.75±0.10 8.37±0.05 –2.7±0.2 200 [+] − [130] 100 –82±1 77±1
n1 0.18 0.92 0.12×0.12 0 12±1 1.82±0.16 8.42±0.05 –2.9±0.2 260 [+] − [200] 150 211±1 80±2
n2 0.40 1.05 0.12×0.12 0 13±1 2.43±0.22 8.36±0.07 –3.0±0.2 510 [+] − [320] 220 217±1 73±2
n3 0.75 0.98 0.15×0.15 0 27±1 3.20±0.48 8.34±0.11 –3.1±0.1 - 180±3 104±3

c –0.30 –0.40 0.12×0.12 0 6±1 1.75±0.25 8.44±0.07 –3.2±0.2 - 67±2 73±3


**Notes.** Properties of the different components identified in Fig. 1. (1) Name of the component. (2) and (3) Distance in R.A. and Dec. from the central
(main) source at co-ordinates R.A. 03h32m23.3497s, Dec. –27 [◦] 51’57.13”. (4) Semi-axes of the ellipse used as extraction aperture. (5) Angle of the
major axis of the ellipse used as extraction aperture measured east of north (anticlockwise). (6) SFR derived from the dust-corrected Hα luminosity
using the relation from Kennicutt & Evans (2012), assuming a Chabrier (2003) IMF. (7) Extinction derived from the Balmer decrement, assuming
a Cardelli et al. (1989) attenuation law. (8) Metallicity calculated from the R3, O3O2 and R23 calibrations from Curti et al. (2020b). (9) Ionisation
parameter inferred using the S2S3 calibration from Díaz et al. (2000). (10) Electron density estimated from the simultaneous fit of the [S ii] and

[O ii] line ratio, using the formulas from Sanders et al. (2016), assuming the typical electron temperature of HII regions _T_ _e_ = 10 [4] K. (11) Velocity
with respect to the redshift of the narrow component of the main target ( _z_ = 3.4705 ± 0.0001). (12) Velocity dispersion.
∗ For the main target, we show the properties inferred from the fit with one component, and the properties derived separately from the narrow and
broad component of the two components fit.


Article number, page 7 of 28

_A&A proofs:_ manuscript no. main



peak velocity [km s [−][1] ]



2


1

|N components|Col2|
|---|---|
|||
|||
|||



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



2.00


1.00


0


- 1.00


- 2.00



log(f/[10 [−][19] erg s [−][1] cm [−][2] ])



1.0


0.8


0.6


0.4


0.2


0.0


0.2


0.4


0.6



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



50


100


150



200


150


100



W80 [km s [−][1] ]


440


400


360


320


280


240


200


160

|Col1|Col2|
|---|---|
|||
|||



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



Fig. 5: Maps of the observed Hα emission obtained from the emission line fit with the best-model (with one or two Gaussian
components). The number of components used for the fit in each spaxel is indicated in the right panel. Only spaxels with peak
S/N> 3.5 in the Hα line are shown. From left to right: integrated observed flux (not corrected for obscuration), velocity at the peak
of the emission, line width W80 (width encompassing 80% of the flux, derived from the total line profile), number of Gaussian
components used in the fit. Contours in the flux map show the [20, 40, 60, 80, 90] percentiles; contours in the velocity map start at
–150 km s [−][1] and increase every 50 km s [−][1] ; contours in the W80 map are at [200, 300, 400] km s [−][1] .



The W80 map shows values in the range 140 −
450 km s [−][1] (corresponding to σ ∼ 55 − 175 km s [−][1] ), with lower
values in the companions (140 − 250 km s [−][1], see third panel in
Fig. 5). This map shows two regions with enhanced values in
the main target (W80 - 400 km s [−][1] ). They lie at the edge of
the emission, roughly aligned with the photometric minor axis.
These regions could indicate the presence of an outflow. Another
possibility is that these increases in W80 are caused by interaction of the central galaxy with the other components of the system. These possibilities are discussed in details in the next Section 5.1.2. Enhanced line width (W80 > 300 km s [−][1] ) is also seen
at the boundary between the central and north galaxies, possibly
due to the superposition along the line-of-sight of the emission
coming from two or more components with different velocities,
or by an enhanced turbulence produced by interactions.


5.1.2. High-velocity dispersion regions: Outflow or
gravitational interaction


The integrated spectrum of the main target (see Fig. 4) shows
two kinematic components: a narrow and a broad component
clearly detected both in the Balmer lines Hα and Hβ, and also
in [O iii] and [N ii]. The broad component, which has a W80∼
560 km s [−][1] (velocity dispersion σ ∼ 220 km s [−][1] ), could be indicative of an outflow. Additionally, the W80 map of the total
profile obtained from the spaxel-by-spaxel analysis shows two
off-nuclear regions with large line widths (see Fig. 5), again
compatible with an outflow.

We further analyse the Hα line in order to characterise this
broad component, since it is the line with the highest S/N.
In Figure 6 we show the Hα spectra from the two regions
with enhanced velocity dispersion (σ - 160 km s [−][1], or W80
- 350 km s [−][1] ) in the E and W parts of the main galaxy, together with the spectrum of the central region. The three spectra
are extracted within circular apertures of radius 0.15 [′′] . We fit
these spectra using a two-component model. In the off-nuclear
regions, the broad component is very prominent compared to
the flux of the narrow component, while in the central region
the narrow component dominates, giving a much smaller W80
of the total profile (∼ 250 km s [−][1] ). The broad components
have W80 ∼ 500 − 770 km s [−][1] (i.e. a velocity dispersion of
σ ∼ 200 − 300 km s [−][1] ). The broad component in these two
external regions has a very small velocity shift with respect to


Article number, page 8 of 28



the systemic velocity, making the shape of the total profile fairly
symmetric.
All these morphological and kinematic characteristics are
compatible with a bi-conical outflow. The selected off-nuclear
regions with highest W80 (Fig. 5) are in the direction of the photometric minor axis, as was expected from star-formation-driven
outflows, which typically expand perpendicular to the disc (e.g.
Bellocchi et al. 2013).
Another possibility is that the large line widths are caused
by turbulence due to the interactions of the main galaxy with
the north companion. The high W80 in the two regions at the
east and west of the main galaxy could be due to galaxy-galaxy
interaction. However, in this scenario we would expect to observe the highest W80 values in the region between the main and
north galaxy. Moreover, we observe a prominent broad component also in the centre of the main galaxy (see central panel of
Fig. 6). The right panel of Fig. 6 shows a map of the flux of
the broad Hα emission [4] (i.e. all the Gaussian components with
σ - 140 km s [−][1], equivalent to W80 ≳ 360 km s [−][1] ), illustrating
that the broad component flux peaks a bit south of the centre of
the main galaxy (defined as the centroid of the continuum emission in the HST/WFC3 F125W filter). This broad component
in the centre is difficult to explain with interactions, and instead
could be explained by an outflow originating from a nuclear starburst. Indeed, the peak of the SFR density is located in a similar
position as the peak of the broad component flux (see Sec. 5.2.4
and Fig. 11, left panel). Thus, we favour the outflow scenario
to explain the enhanced line widths in the off-nuclear regions
of the main galaxy, even though we acknowledge the possibility
that galaxy interactions may also contribute to the broadening
of the lines. We discuss the properties and possible origin of the
outflow in Sec. 6.2.


_5.2._ _Properties of the interstellar medium_


5.2.1. Dust attenuation


We measure the dust attenuation in each spaxel using the Balmer
decrement Hα/Hβ. We use the results of the fit with only one
component across the whole data cube, as we are interested in
the obscuration of the dominant gas component (i.e. not the out

4
The map of the velocity ( _v_ 50) and line width (W80) associated with
the broad Hα emission are reported in Figure E.1 in the appendix.

I. Lamperti et al.: JWST/NIRSpec view of GS5001





f(broad)[10 [−][19] erg s [−][1] cm [−][2] ])



1.00


0.50


0


- 0.50




|3.0|2|Col3|Col4|Col5|
|---|---|---|---|---|
|0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>.|2||||
|0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>.|||||





70


60


50


40


30


20


10


0



3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.5







10600 400 200 0 200 400 600













1.00


0.50


0


- 0.50



5.4


4.8


4.2


3.6


3.0


2.4


1.8


1.2


0.6




- 1.00



600 400 200 0 200 400 600
velocity [kms [−][1] ]




- 1.00

1.00 0.50 0   - 0.50   - 1.00
∆R. A. [arcsec]



Fig. 6: Spectra and distribution of the Hα broad component emission. _Left_ _panel_ : Map of the line width (W80) of Hα derived
from the best-fit model. The three circles indicate the extraction regions of the spectra shown on the middle panel. _Middle panel_ :
Comparison of the spectra extracted from the central region (upper row), and from the two regions with a high velocity dispersion
(middle and bottom row). The extraction regions are shown in the left panel and have a radius of 0.15 [′′] . _Right panel_ : Map of the Hα
broad component flux. This map is created by adding the flux of all Gaussian component with σ - 140 km s [−][1] . This map has not
been corrected for obscuration. Light blue circles mark the positions of the regions 2 and 3.



flow). We assume a theoretical value of Hα/Hβ= 2.86, estimated
for Case B recombination assuming a temperature of 10 [4] K and
an electron density _n_ _e_ = 10 [2] − 10 [3] cm [−][3] (Osterbrock & Ferland
2006). We adopt the Cardelli et al. (1989) attenuation law. We
derive the attenuation for the global emission inferred from the
one-component fits, as the S/N of the broad component is not
high enough to derive reliable line ratios separately for the broad
and narrow components in individual spaxels, nor binning 3 × 3
adjacent spaxels. We shall discuss the attenuation of the outflow
component detected in the integrated spectrum in Sec. 6.2.
Figure 7 shows the map of the visual attenuation _A_ _V_ . We consider only spaxels with S/N(Hα)> 3 and S/N(Hβ)> 2. There are
some spaxels where Hα is detected while Hβ is below the detection threshold (S/N(Hβ)< 2). Those spaxels are illustrated with
a grey contour in Fig. 7. In those regions, the attenuation could
be even higher than the maximum value measured in the spaxels
with Hβ detection ( _A_ _V_ = 2.7), but the low S/N in Hβ prevents
use from measuring _A_ _V_ . The central galaxy has _A_ _V_ in the range
0.5 − 2.7. The attenuation is enhanced in a region ∼ 0.3 − 0.5 [′′] to
the NW and in a region ∼ 0.2−0.4” to the SW from the centre. A
region with lower attenuation is found close to the centre and extending towards the SE. This low-attenuation region corresponds
to an area with high ionisation parameter (traced by [S iii]/[S ii],
see section 5.2.5).

The high attenuation in the region between the main component and the north component corresponds to a dust lane that is
visible in the composite NIRCam image shown in Fig. 1. In Figure 7, we show with contours the location where the ratio of the
F444W/F090W NIRCam maps is higher, to highlight the region
with redder colour, which we interpret as a dust lane.
The northern component (particularly the n2 and n3 clumps)
and the south clump s3 show the highest attenuation values
( _A_ _V_ - 2.4, see Table 1). These components were not detected
in the HST UV map (see Fig. 1): the low UV fluxes could indeed be due to the high attenuation. The clump s1 instead shows
the lowest _A_ _V_ ∼ 0.2 − 0.7.

In summary, we observe a rather heterogeneous distribution
of dust over the system with typical sub-kiloparsec variations
of _A_ _V_ ∼ 1 mag. The least obscured regions ( _A_ _V_ < 0.5 mag.) are



Fig. 7: Visual attenuation map inferred from the Hα/Hβ line
ratio, using the Cardelli et al. (1989) reddening law. We show
spaxels with S/N(Hα)> 3 and S/N(Hβ)> 2. Black contours indicates the dust lane identified in the map ratio of the NIRCam
F444W/F090W filters. Orange circles indicate the position of the
components identified in Fig. 1. The grey contour indicate the region where Hα is detected with S/N>3.


found at the south, while those most attenuated ( _A_ _V_ - 2 mag) are
in the north component and associated with a dust lane identified
by NIRCam broad band imaging (see Fig. 7). We also find a
relatively low attenuated region in the main target, to the southeast of the centre, corresponding to an area with high ionisation
parameter (see Sec. 5.2.5). We use this _A_ _V_ map to correct for
attenuation the fluxes of the measured emission lines.


Article number, page 9 of 28



2.00


1.00


0


- 1.00



A V






- 2.00

2.00 1.00 0   - 1.00   - 2.00
∆R. A. [arcsec]



2.5


2.0


1.5


1.0


0.5


0.0

_A&A proofs:_ manuscript no. main



5.2.2. Emission line diagnostics of gas excitation
mechanisms


In this subsection, we investigate the source of ionisation in a
spatially resolved way. In Figure 8, we present the maps of the
line ratios [N ii]/Hα and [O iii]/Hβ, together with the emission
line diagnostic diagram (BPT; Baldwin et al. 1981). We show
here all the spaxels with S/N>3 in the Hα, Hβ, [N ii] and [O iii]
lines.
The line ratios in our target are all below the separation line
between star formation and AGN found by Kewley et al. (2001)
for local sources, thus, they are consistent with ionisation from
HII regions. The line ratios are higher than the typical line ratios
of star-forming galaxies in the local Universe (see SDSS contours), but they follow quite well the locus of star-forming galaxies at _z_ = 2 − 3 from the KBSS-MOSFIRE sample presented by
Strom et al. (2017). Recently, some high-redshift AGN discovered by JWST have been reported to be on the same location of
the KBSS-MOSFIRE sample (Übler et al. 2023; Maiolino et al.
2023; Scholtz et al. 2023). However, our target is at a lower redshift and more metal rich (see Sec. 5.2.3) than the AGN explored
in those JWST studies, thus the BPT classification should still
be reliable. The scatter in our points is partly due to uncertainties (the average uncertainties are of the order of 0.1 dex). The
south and north companions, shown with light blue and red dots,
respectively, have lower [N ii]/Hα and higher [O iii]/Hβ values
compared with the main target (orange dots). This is consistent
with these targets having lower metallicity (see Sec. 5.2.3).
The north part of the main target shows the highest values of

[N ii]/Hα and lowest [O iii]/Hβ values. We investigate two possible mechanisms that could explain these line ratios. One possibility is that the [N ii]/Hα ratio is enhanced by shocks. If the line
ratios are driven by shocks, they are expected to correlate with
the kinematics of the gas (e.g Monreal-Ibero et al. 2006; Arribas
et al. 2014; Ho et al. 2014; McElroy et al. 2015; Perna et al. 2017,
2020; Mingozzi et al. 2019; Johnston et al. 2023). The velocity
dispersion in that region is indeed higher than in the south part
of the main target (see W80 map in Fig. 5). In Fig. 9 we show
the line ratio [N ii]/Hα versus the velocity dispersion. The points
in Fig. 9 are colour-coded according to a combination of the two
quantities on the x and y axes, using the expression from Eq. 1
in D’Agostino et al. (2019):


_X_ − _min_ ( _X_ ) _Y_ − _min_ ( _Y_ )
_Q_ = (1)
_max_ ( _X_ ) − _min_ ( _X_ ) [×] _max_ ( _Y_ ) − _min_ ( _Y_ ) [,]


where _X_ = log [N ii]/Hα and _Y_ is the velocity dispersion σ.
The upper panel of Fig. 9 shows the map of the system colourcoded by _Q_, illustrating that the highest values of velocity dispersion and [N ii]/Hα are found in the northern part of the main
galaxy. There is an overall correlation between the two quantities (Spearman’s rank correlation coefficient _r_ = 0.71, _p_ -value
< 0.01). The slope of the correlation is flatter at low values of log

[N ii]/Hα< 0.6, and then it becomes steeper and more scattered
at higher [N ii]/Hα values. This could indicate that the shocks are
affecting the line ratios in regions with a high velocity dispersion
(σ > 100 km s [−][1] ), while at lower σ photo-ionisation is probably
the main mechanism driving the changes in the line ratio.
In Fig. 9, we overlaid a set of shock models calculated with
the code MAPPING V (Sutherland & Dopita 2017; Sutherland
et al. 2018). We use the 3MdBs database (Alarie & Morisset
2019) to download the grid of models presented in Allen et al.
(2008). We consider models with solar metallicity, magnetic
fields values in the range 1-10 µG, and pre-shock densities in the
range of 1−10 cm [−][3] (which correspond to [S ii]-based post-shock


Article number, page 10 of 28



electron densities in the range 50 − 4000 cm [−][3] ). The models assume shock velocities >100 km s [−][1] . In the velocity range covered by both the observations and the models (100-160 km s [−][1] ),
the shock models match the observed [N ii]/Hα line ratios.
Another possibility is that the enhanced [N ii]/Hα and diminished [O iii]/Hβ line ratios is due to higher metallicity in that
region. We shall discuss this possibility further in the next section. In summary, the spatially resolved [O iii]/Hβ and [N ii]/Hα
line ratios are consistent with emission due to star formation,
with no sign of AGN ionisation. We find a region with enhanced

[N ii]/Hα and low [O iii]/Hβ, located in the northern part of the
main target. This peculiar line ratios could be due to shocks, or
to a higher metallicity.


5.2.3. Gas-phase metallicity


In this section, we study the gas-phase metallicity in our
system. We calculate the gas-phase metallicity following
the prescriptions from Curti et al. (2020b, 2024). We prefer to use these prescriptions even if they are calibrated
for local galaxies, because prescriptions for higher redshift galaxies do not cover well the high metallicity regime
(12+log(O/H)> 8.4, e.g. Sanders et al. 2024). We consider the metallicity indicators based on the line ratios
R3=[O iii]λ5007/Hβ, O3O2=[O iii]λ5007/[O ii]λ3727,3729, and
R23= ([O ii]λ3727,3729+ [O iii]λ4959,5007)/Hβ. We decide to
use this set of line ratios, because they are appropriate for the
metallicity regime of our target. We did not include the N2 =

[N ii]/Hα line ratio because, as we have seen in Sec. 5.2.2, it
may be affected by shocks. We fit simultaneously the R3, O3O2
and R23 parameters to reduce the uncertainties, following the
procedure described in Curti et al. (2024).
From the integrated spectrum of the main target we measure
12+log(O/H) = 8.45 ± 0.04. For the stellar mass of GS5001
- that is, log( _M_ ⋆ / _M_ ⊙ ) = 10.0 − 10.6 (see Sec. 1) - the massmetallicity relation derived by Sanders et al. (2021) for galaxies
at _z_ = 3.3 predicts a metallicity 12+log(O/H)= 8.42−8.49 [5], consistent with our measurement. The north and south companions
show slightly lower metallicities (12+log(O/H)∼ 8.34 − 8.44)
compared to the central target. This is expected considering that
the companions have a lower stellar mass than the central galaxy.
We do not have estimates of the stellar masses for the individual companions; however, for the south source (which includes s1, s2, and s3) there is an estimate from the literature
(log( _M_ ⋆ / _M_ ⊙ ) = 9.7 − 10.4, see Sec. 1). For this stellar mass, the
mass-metallicity relation by Sanders et al. (2021) would predict
12+log(O/H)∼ 8.4 − 8.6, in agreement within the uncertainties
with the measured values.

Figure 10 shows a resolved map of the metallicity in the system. The main galaxy shows a metallicity gradient, with lower
metallicity in the south (12+log(O/H)=8.4) and a higher metallicity in the NE region, reaching values of 12+log(O/H)=8.58.
The lower metallicity in the south could be due to an inflow
of lower metallicity gas. We note that in this position we also
identify a small clump (c) that is merging with the main galaxy.
This clump could be part of an inflowing stream of gas, or be a
lower metallicity companion. We note that the region with lowmetallicity observed in the south part of the main galaxy is more
extended than the clump ‘c’. Similar metallicity gradients have
been recently reported in galaxies at _z_ = 3.6 − 7.9 (Arribas et al.


5 We re-scale the values by –0.1 dex, to account for the fact that
Sanders et al. (2021) use a different metallicity calibration from Bian
et al. (2018) (see also Curti et al. 2024).

I. Lamperti et al.: JWST/NIRSpec view of GS5001



2.00


1.00


0


- 1.00


- 2.00



log[NII]/Hα



0.40


0.48


0.56


0.64


0.72


0.80


0.88



1.00


0


- 1.00


- 2.00

|log[OIII]/Hβ|Col2|
|---|---|
|||
|||
|||


2.00 1.00 0   - 1.00   - 2.00
∆R. A. [arcsec]







0.56


0.48


0.40


0.32


0.24


0.16


0.08











2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



Fig. 8: Spatially resolved maps of the emission line ratios [N ii]/Hα and [O iii]/Hβ. The circles show the colour-coding for the
spaxels in the BPT diagram in the right panel. _Right:_ Emission line diagnostic diagram for the single spaxels. Spaxels belonging to
the north, main, and south regions are indicated in red, orange, and light blue, respectively. A representative (median) error bar is
shown in the top right. The line ratios derived from the integrated spectra of the three regions are shown with squares. The orange
diamond shows the line ratios of the outflow, derived from the broad component of the integrated spectrum of the main target. In
black are shown the demarcation lines from Kewley et al. (2001) (solid) and Kauffmann et al. (2003) (dashed). The dashed green
line show the locus of star-forming galaxies at _z_ = 2 − 3 from Strom et al. (2017). The location of galaxies from the SDSS sample
(Abazajian et al. 2009) is illustrated with the grey contours showing the 50th, 90th, and 98th percentiles of the sample.



2024; Rodríguez Del Pino et al. 2024; Venturi et al. 2024), and
were explained by possible accretion of low metallicity gas and
merger event with a lower-metallicity satellite.
Another possibility is that the north part has been enriched in
metals, due to a past episode of enhanced SF activity in the interacting region between the ‘main’ galaxy and the northern component. We note however that the possible presence of shocks in
this region (see Fig. 9) may also increase the line ratios mimicking a further rise in metallicity. Then, the derived high metallicities may be a consequence of both enhanced SF and the presence
of shocks.
We note that the interacting region shows also a higher level
of obscuration with respect to the rest of the galaxy, and that it
may be coincident with a dust lane (see Fig. 7). Previous works
have found a correlation between the obscuration in the UV
(traced by the UV slope) and the gas-phase metallicity (Heckman et al. 1998; Reddy et al. 2010). Their interpretation is that
the extinction of the UV emission increases as the dust-to-gas
ratio increases with gas-phase metallicity. Similarly, the higher
_A_ _V_ and higher metallicity in the interacting region of our system
could be related to a higher dust-to-gas ratio.
In summary, we find that the main galaxy has an average
metallicity of 12+log(O/H)= 8.45 and the companions have
slightly lower metallicities (8.34 − 8.44), consistent with the
mass-metallicity relation at _z_ ∼ 3. The main target shows a
metallicity gradient with lower values in the SW region and
higher in the NE, the region close to the north target. This metallicity gradient could be explained by an inflow of low-metallicity
gas or accretion of a lower metallicity companion from the south,
or by an increase in the metallicity in the north due to a past
star formation episode triggered by the interaction with the north
component.


5.2.4. Star formation rates


In Section 5.2.2, we showed that the ionisation in our system is
dominated by star formation, thus, we can use the Hα luminosity
to trace the SFR. We first correct the Hα fluxes for obscuration
using the Balmer decrement (see Sec. 5.2.1). Then, we convert



the Hα luminosity into SFR using the relation from Kennicutt
& Evans (2012) (see also Murphy et al. 2011; Hao et al. 2011),
assuming a Chabrier (2003) IMF.


In Table 1 we report the SFRs derived from the integrated
spectra of the different components. For the main target, the SFR
derived from the narrow component flux is 100 M ⊙ yr [−][1] . Considering the star-formation main-sequence definition at _z_ = 3.5
from Schreiber et al. (2015) and a stellar mass log _M_ ⋆ / _M_ ⊙ =
10 − 10.6 (see Sec. 1), GS5001 would be 0.1-0.2 dex above
the main-sequence. The south clumps have SFRs between 1230 M ⊙ yr [−][1], for a combined SFR of ∼ 76 M ⊙ yr [−][1], while the
north component has a total SFR of 106 M ⊙ . Thus, the north
and south companions have a total SFR comparable to the main
target, and the total SFR of the system is ∼ 300 M ⊙ yr [−][1] . Previous estimates of the SFR, derived from SED fitting, were in the
range 150-240 M ⊙ yr [−][1] for the central galaxy and in the range
60-110 M ⊙ yr [−][1] for the south component, consistent with our
measurements within a factor of two (see Sec. 1).


Figure 11 shows the maps of the SFR surface density (Σ _S FR_ )
derived from Hα, together with the F090W NIRCam image, trac
∼
ing the UV flux at 2000 Å rest-frame. In the F090W image,
we can identify three peaks in the central target, aligned in the
N-S direction. The region with the highest Σ _S FR_ is also aligned
in the same direction. Overall, the Σ _S FR_ is very high in the central target, where it reaches values of ∼ 10 M ⊙ yr [−][1] kpc [−][2] . Also
in the companions the values are relatively high, in the range
0.3 − 6 M ⊙ yr [−][1] kpc [−][2] .


SFR densities for galaxies at redshift _z_  - 3 have been reported in the literature, mainly from integrated measurements
(e.g. Reddy et al. 2023a,b; Morishita et al. 2024). Thanks to NIRSpec IFS, it is now possible to derive spatially resolved maps.
Rodríguez Del Pino et al. (2024) reported similar high values
(Σ _S FR_ ∼ 8 M ⊙ yr [−][1] kpc [−][2] ) in the central region of GS4891, a
star-forming galaxy at z=3.7, also part of the GA-NIFS sample. Morishita et al. (2024) finds similarly high values (Σ _S FR_ 10 M ⊙ yr [−][1] kpc [−][2] ) in a sample of compact sources at _z_ - 5.


Article number, page 11 of 28

Z(R3, O32, R23)



8.55


8.50


8.45


8.40


8.35



2.00


1.00


0


- 1.00


- 2.00



_A&A proofs:_ manuscript no. main


2.00







1.00


0


- 1.00



180


160


140


120


100


80


60


40

1.0 0.8 0.6 0.4 0.2

#### Hα log[NII]/


Fig. 9: Comparison of mission line ratio [N ii]/Hα and velocity dispersion. _Lower panel:_ Emission line ratio [N ii]/Hα versus
the velocity dispersion for individual spaxels. Points are colourcoded based on the function _Q_ described in Equation 1, which
combines [N ii]/Hα and velocity dispersion. Black curves show
shock models derived with MAPPINGS V (see text). _Upper_
_panel:_ Map colour-coded as in the lower panel, showing the region with high [N ii]/Hα and high velocity dispersion.


5.2.5. Ionisation parameter


We calculated the ionisation parameter, U - in other words,
the ratio of (hydrogen-)ionising photons over the gas density - using the prescriptions from Diaz et al. (1991); Diaz
(1999). We consider the calibrations involving the flux line ratio S2S3=([S ii]λ6717+[S ii]λ6731)/([S iii]λ9069+[S iii]λ9531),
measured from the R100 data cube. The S2S3 line ratio is less
dependent on metallicity than O3O2, thus it is considered to be
a more accurate estimator of the ionisation parameter (Mathis
1982; Dopita & Evans 1986; Kewley & Dopita 2002; Kewley
et al. 2019; Mingozzi et al. 2020).
The values of the ionisation parameter derived from the integrated spectra of the different components of the system are
reported in Table 1. The values of the ionisation parameter span
a range from log U = [-3.1, -2.7]. These values are within the


Article number, page 12 of 28




- 2.00

2.00 1.00 0   - 1.00   - 2.00
∆R. A. [arcsec]



Fig. 10: Gas-phase metallicity map calculated using three metallicity calibrations R3, O32, and R23, following the prescriptions
from Curti et al. (2020b). The dashed circle shows the position
of the clump ‘c’.


range measured by Reddy et al. (2023a) using the O3O2 ratio in
a sample of galaxies at _z_ = 1.9 − 3.7 (log U = [-3.25, -2.05]).



Figure 12 shows the map of the ionisation parameter obtained using the S2S3 calibrations. We show only
spaxels with S/N>3 in the sum of the [S iii] and [S ii]
lines (i.e. S/N([S iii]λ9069)+S/N([S iii]λ9531) - 3 and
S/N([S ii]λ6717)+S/N([S ii]λ6731) - 3) and with S/N(Hβ) - 2,
to ensure that we can correct the fluxes for obscuration using the
Balmer decrement. The values of the ionisation parameter span
a range from log U = –3.8 to –2.3. In the main target, the ionisation parameter is enhanced (by ∼ 0.4 dex) with respect to the rest
of the galaxy in a region south of the continuum peak pointing
toward the south-east. We note that this region has lower obscuration ( _A_ _V_ ) than the rest of the main galaxy (see Fig. 7). The
clump s3 also shows a similar enhancement of the ionisation parameter. We note that these regions corresponds to the regions
with brighter Hα flux, and therefore higher SFR (see Fig. 11).
The north companion and the clumps s1 and s2 have low ionisation parameter (log U < −3) similar to the values in the north
part of the main target.


We calculated the ionisation parameter maps also using the
O3O2, S2Hβ and O2Hβ calibrations from Díaz et al. (2000).
These maps show similar spatial variations, even though the normalisation is different.



In our target, we observe that the regions with high ionisation parameter (region south of the continuum peak, and clump
s3) correspond to regions with elevated SFR surface density (see
Fig. 11). A correlation between ionisation parameter and SFR
surface density has been observed in previous spatially resolved
studies of nearby galaxies (Dopita et al. 2014; Kaplan et al.
2016), but also within a galaxy sample at _z_ = 1.9 − 3.7 (Reddy
et al. 2023a). This correlation suggests that SFR plays an important role in regulating the ionisation parameter (Reddy et al.
2023a).

I. Lamperti et al.: JWST/NIRSpec view of GS5001



2.00


1.00


0


- 1.00


- 2.00



log Σ SFR [M ⊙ yr [−][1] kpc [−][2] ]



1.00


0.75


0.50


0.25


0.00


0.25


0.50


0.75



log F(F090W) [erg/s/cm [2] /Å]
2.00


1.00


0


- 1.00


- 2.00

2.00 1.00 0   - 1.00   - 2.00
∆R. A. [arcsec]



20.0


20.4


20.8


21.2


21.6


22.0


22.4


22.8



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



Fig. 11: Maps of star formation rate tracers. _Left:_ Map of the SFR surface density, inferred from the dust-corrected Hα luminosity.
_Right:_ Flux in the NIRCam filter F090W.



2.00


1.00


0


- 1.00


- 2.00



log U (S2S3)



2.4


2.6


2.8


3.0


3.2


3.4


3.6


3.8


|Col1|Col2|
|---|---|
|||
|||



2.00 1.00 0     - 1.00     - 2.00
∆R. A. [arcsec]


Fig. 12: Maps of the ionisation parameter derived from the S2S3
line ratio. We show only spaxels with S/N>2 in Hβ, and S/N>3
in the sum of the [S iii] and [S ii] lines.


5.2.6. Electron density


The electron density can be derived using the ratios of the

[S ii]λλ6716,31 or the [O ii]λλ3726,29 doublets (Osterbrock &
Ferland 2006). In our case, the S/N is not enough to study these
line ratios spaxel-by-spaxel, thus, we focus on the integrated
spectra. We note that the two [O ii] lines are not fully spectroscopically resolved in our data. On the other hand, the [S ii] lines
are well resolved, but have lower S/N. In order to better constrain the electron density, we fit simultaneously the [S ii] and

[O ii] lines, forcing the line ratios to agree on the same _n_ _e_ parameter, following the same approach used by Rodríguez Del Pino
et al. (2024). We use the formulas presented in Sanders et al.
(2016) that relate the [S ii] and [O ii] line ratios to the electron
density. We do not attempt to model the emission lines with two
components (broad and narrow), because even in the integrated



spectrum of the main galaxy the S/N of the broad component is
not high enough to derive meaningful constraints on the electron
density (see Fig. F.2 in the appendix). The results of the fit of the

[O ii] and [S ii] doublets of the main target are shown in Fig. 13.
For the main target, we find _n_ _e_ = 540 [+] − [120] 100 [cm] [−][3] [. The indepen-]
dent modelling of the [S ii] line ratio would give _n_ _e_ ([S ii])= 73 [+] − [70] 50
cm [−][3], while the [O ii] line ratio gives _n_ _e_ ([O ii])= 1480 [+] − [400] 320 [cm] [−][3] [.]
These estimates have large uncertainties due to the issues mentioned above. We note that the electron densities derived from

[O ii] are systematically higher than the ones derived from [S ii]
for all the sources in our system. Kewley et al. (2019) highlight
that the [S ii] and [O ii] lines are produced in different regions
of ionised nebulae: the [S ii] lines are produced in the extended
partially ionised region of the nebula, while the [O ii] lines are
produced closer to the ionising source. If the density is higher
close to the ionising source than further out, this could explain
the different _n_ _e_ estimates from [S ii] and [O ii].
We note that the fit of the main galaxy shows significant
residuals (> 3σ) on the blue side of the [O ii] doublet (see left
panel of Fig. 13). This is probably due to the outflow component that we are not considering in the fit. An attempt to fit
simultaneously the [S ii] and [O ii] lines with two components
(narrow+broad) gives similar results for the electron density of
the narrow component ( _n_ _e_ = 540 [+] − [270] 280 [cm] [−][3] [),] [while] [the] [elec-]
tron density of the broad component is unconstrained ( _n_ _e_ =
340 [+] − [1400] 280 [cm] [−][3] [, see Fig. F.2.]
For the companions, we find electron densities in the range
200-600 cm [−][3] from the simultaneous fit of [O ii] and [S ii]. The
results of the fit of the [O ii] and [S ii] doublets of the companions
are shown in Fig. F.1 in the appendix, while the values of the
electron densities are reported in Table 1.

Our results are consistent with the electron densities of starforming galaxies at redshifts of _z_ ∼ 1 − 2.5 derived from
the [O ii] or [S ii] ratios from the literature (e.g. Masters et al.
2014; Steidel et al. 2014; Shimakawa et al. 2015; Sanders et al.
2016; Kaasinen et al. 2017; Kashino et al. 2017). Recently, Rodríguez Del Pino et al. (2024) measured an electron density of
_n_ _e_ = 776±307 cm [−][3] in a star-forming galaxy at a similar redshift
of _z_ = 3.7 (GS4891), using NIRSpec data, in agreement with our

measurement.


Article number, page 13 of 28

_A&A proofs:_ manuscript no. main



80


60


40


20


~~0~~


20

20
15
10
5
0
5

10
15
20




[OII] n e : 545 − [+125] 104 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]




[SII]


6710 6720 6730 6740
rest. wavelength [Å]



Fig. 13: Simultaneous spectral fit of the [O ii]λλ3726, 29 and

[S ii]λλ6716, 31 doublets to derive the electron density from the
integrated spectrum of the main target. The blue curve shows
the total best-fit model, the light blue curves show the best-fit
Gaussians for the individual emission lines, and the grey curves
the uncertainties of the MCMC fit. The bottom panels show the
residuals, the dashed magenta line indicates the average 1σ noise
level.


Reddy et al. (2023b) study a sample of ∼ 50 galaxies
at _z_ = 2.7 − 6.3, and report average electron densities of ∼
100 − 500 cm [−][3] . Interestingly, they find higher electron densities ( _n_ _e_ ∼ 500 cm [−][3] ) in galaxies with higher SFR surface
density (Σ _S FR_ - 1 M ⊙ yr [−][1] kpc [−][2], see also Shimakawa et al.
2015; Reddy et al. 2023a), similar to the Σ _S FR_ values observed
in GS5001 (see Fig. 11). Recently, Isobe et al. (2023) measure
_n_ _e_ ≳ 300 cm [−][3] in a sample of 14 galaxies at _z_ = 4 − 9 (see
also Marconcini et al. 2024). They find that the _n_ _e_ are higher
than those of lower-redshift galaxies with similar values of stellar mass, SFR or specific SFR. GS5001 has a SFR comparable
to that of local ULIRGs (SFR - 150 M ⊙ yr [−][1] ), which have an
average electron density ∼ 300 cm [−][3] (Arribas et al. 2014), a bit
lower than our measurement. This suggests that, apart from an
increase in SFR with redshift, the gas conditions at high redshift
also lead to higher electron densities (but see also Kaasinen et al.
2017).
In summary, we take advantage of the large wavelength
range covered by NIRSpec to measured the electron densities
by modelling simultaneously the [S ii] and [O ii] doublets. We
measure an electron density of 540 − [+][120] 100 [cm] [−][3] [ in the main targets,]
and _n_ _e_ = 200 − 600 cm [−][3] in the companions. We note that using
only the [S ii] or [O ii] lines would provide different results, with
larger uncertainties.


**6.** **Discussion**


_6.1._ _Dynamical and physical status of the system:_
_A pre-coalescence merger_


Our NIRSpec observations confirm the interesting nature of this
system and allow the spatially resolved study of the central
galaxy and its close companions (< 15 kpc). From the ionised
gas (Fig. 5) and continuum emission maps (Fig. 3), we identified


Article number, page 14 of 28



two additional companions other than the central galaxy. The
south component is blueshifted by ∼ 130 km s [−][1] with respect
to the central galaxy, and shows three sub-structures identified
as peaks in the [O iii] flux and continuum emission maps. The
north companion is redshifted by ∼ 200 km s [−][1] with respect to
the main galaxy, and its ionised gas emission shows three peaks.
We also detect continuum emission associated with this source.
The presence of continuum emission in both the south and north
companions indicates that these are not just gas clumps but are
likely galaxies with a significant stellar component. Indeed, the
estimated stellar mass for the south companion from the literature is in the range _M_ ⋆ = 0.5 − 2.3 × 10 [10] M ⊙ (Maiolino et al.
2008; Pérez-González et al. 2005; Guo et al. 2013).
We observe signs of interactions between the northern companion and the central galaxy: in this region, the ionised gas is
more turbulent and the ISM shows peculiar properties (higher

[N ii]/Hα, higher metallicity, and higher obscuration than elsewhere). Additionally, the north companion has a tidal tail extending for 10 kpc, which can be interpreted as a sign of interactions. Given the low relative velocities of the companions
(< 200 km s [−][1] ) and projected distance (< 10 kpc), we can expect that they will coalesce with the central galaxy in the future.
We note however that we can only measure projected velocities,
thus, the ‘true’ relative velocities are uncertain.
Moreover, we identify one clump (‘c’), which is probably in
the process of merging with the main galaxy. This clump could
be situated between the main galaxy and us. Since its emission is
redshifted with respect to the main target by ∼ 70 km s [−][1], in this
scenario the clump would be moving towards the main galaxy
and may be in the process of merging. Given that its Hα luminosity is only 3% of the one of the main galaxy, we can consider it a
minor merger event. From the gas-phase metallicity map shown
in Fig. 10, we see that at the position of this clump the metallicity is lower compared to the values measured in the north-east
part of the main galaxy. Thus, this clump could be part of a lowmetallicity inflow, or be a low-metallicity clump falling onto the
main target. As an alternative scenario, this clump could be located behind the main galaxy, moving away from us. In this case,
it could be interpreted as a low-velocity clump associated with
ejected (outflowing) gas, or, more in general, a debris formed by
galaxy interactions.
The north and south companions could be part of a large
scale gas filament that is feeding the central galaxy. Ginolfi et al.
(2017) identify several CO emitters oriented along the NE-SW
within a radius of ∼ 250 kpc. They interpret them as tracers of a
cold gas stream feeding the central galaxy. The north and south
companions, which are broadly oriented along the same direction (see Fig. 14), could have formed in this gas filament and be
in the process of moving towards the central galaxy and merging
with it. This scenario would explain the peculiar ISM properties in the region between the main and north component, and
the presence of the extended tidal tail towards the north-east and
the line emitter ‘c’. Hence, this system may be comparable to the
Spiderweb Galaxy at _z_ ∼ 2.2, where a cloud of molecular gas extending for tens of kiloparsecs seems to be feeding the innermost
(merging) galaxies in the proto-cluster (Emonts et al. 2016).
Recently, Jin et al. (2023) identified an overdensity consisting of a group of six galaxies within a FoV of 10 × 20 kpc [2] at a
redshift of _z_ ∼ 5.2, CGG-z5, using NIRCam observations. Five
companions with log( _M_ ⋆ / _M_ ⊙ ) ∼ 8.4 − 9.2 are aligned along two
directions around a central more massive galaxy (log( _M_ ⋆ / _M_ ⊙ ) ∼
9.8). The geometry looks remarkably similar to our system. Jin
et al. (2023) look for similar compact structures in the EAGLE
cosmological simulations (Crain et al. 2015; Schaye et al. 2015),

I. Lamperti et al.: JWST/NIRSpec view of GS5001





















Fig. 14: Map of the [O iii] integrated flux with overlaid contours
of the CO(4-3) emission from ALMA. Solid contours are at levels [1, 2, 3, 4, 5] × rms, and dashed contours show the −1× rms
level. The magenta oval shows the 1.9 [′′] × 1.3 [′′] ALMA beam. Arrows indicate the direction (NW-SE) of the large scale filament
traced by CO emitters discovered by Ginolfi et al. (2017).


and follow their evolution with cosmic time. They find that the
identified structures will merge into a single galaxy by _z_ ∼ 3.
Therefore, GS5001 could be a similar system, in which all the
currently identified structures will merge at a later cosmic epoch.


_6.2._ _The kiloparsec-scale outflow in GS5001: properties,_
_origin and effects_


In section 5.1.2, we present the regions with high velocity dispersion in the main galaxy and we discuss whether this enhancement is due to an outflow or galaxy-galaxy interaction. Although
both scenarios are plausible, we favour the outflow explanation
based on geometric considerations, while acknowledging that we
cannot entirely exclude the interaction scenario. In this section,
we describe the properties of gas in the ionised outflow, and we
estimate the outflow energetics. As the limited signal-to-noise
prevents us from studying the physical properties of the outflow spaxel-by-spaxel, we consider the integrated spectrum of
the main target, and use the two-component fit to separate the
flux due to the outflow (see Fig. 4).


6.2.1. Outflow properties


The spatially integrated properties of the broad outflow component are reported in Table 1. The dust attenuation measured in the
broad component, tracing the outflow, is higher ( _A_ _V_ = 2.3 ± 0.5)
compared to the rest of the galaxy ( _A_ _V_ = 1.4 ± 0.1). Higher dust
attenuation in the outflows than in the galaxy disc has been observed in several studies at lower redshift (e.g. Holt et al. 2011;
Villar Martín et al. 2014; Perna et al. 2015; Perna et al. 2019).
In GS5001 the metallicity of the outflow (12 + log (O/H) =
8.47 ± 0.07) is similar to the one derived from the narrow component (12 + log (O/H) = 8.45 ± 0.04). The line ratios [N ii]/Hα
and [O iii]/Hβ in the broad component are also very similar
to the ones observed in the narrow component (log [N ii]/Hα=



−0.61 ± 0.07, log [O iii]/Hβ= 0.36 ± 0.07), thus, the ionisation source of the outflow is compatible with star formation (see
Sec. 5.2.2).
We provide here an estimate of the outflow mass and mass
outflow rate. We estimate a (projected) outflow radius of 0.4"
(3 kpc), corresponding to the distance from the centre to the regions with high velocity dispersion (regions 2 and 3 in Fig. 6).
To estimate the maximum outflow velocity, we use the average of
the absolute values of _v_ 05 and _v_ 95 (5th and 95th percentiles) velocities estimated from the integrated spectra of the high-velocity
dispersion regions (see Fig. 6), following Cresci et al. (2015) and
Harrison et al. (2016). The assumption behind this method is that
the outflow broadens the line profile due to having components
in multiple directions, and the maximum velocity in the wings
is produced by those components directed closer to line of sight,
and is hence less affected by projection effects. Thus, the maximum velocity is a good approximation of the intrinsic outflow
velocity (Cresci et al. 2023). As in our case the profiles are symmetric and roughly centred around the zero velocity, _v_ 05 and _v_ 95
have a similar absolute value of _v_ _max_ = 400 km s [−][1] .
Another common definition of the outflow velocity used in
the literature is _v_ out = _v_ _broad_ + 2σ _broad_ (e.g. Fiore et al. 2017).
This definition would give _v_ out = 470 km s [−][1] using the velocity parameters derived from the broad component of the integrated spectrum of the ‘main’ galaxy, which is slightly higher
than the value estimated from _v_ 05 and _v_ 95. We cannot estimate the electron density in the outflow component as the broad
component of [S ii] and [O ii] are too faint, so we use the electron density estimated for the total line profile ( _n_ _e_ = 540 ±
110 cm [−][3], see Sec. 5.2.6). We calculate the outflow mass following Cresci et al. (2017): _M_ out = 3.2·10 [5] - ( _L_ broad (Hα)/10 [40] erg/s)·
(100 cm [−][3] / _n_ _e_ ) M ⊙ = (1.7 ± 0.4) × 10 [8] M ⊙ . The corresponding
mass outflow rate is _M_ [˙] out = _M_ out - _v_ out / _R_ out = 23 ± 5 M ⊙ yr [−][1] .
We estimate the escape velocity following Arribas et al.
(2014). We assume the dynamical mass is twice the stellar mass
(Erb et al. 2006); that is, _M_ _dyn_ = 2−8×10 [10] M ⊙ . We calculate the
escape velocity at a radius of 3 kpc (size of the outflow), assuming a truncation radius of 30 kpc. We obtain escape velocities in
the range ∼ 330−660 km s [−][1] . On the basis of this calculation, we
estimate that less than 15% of the outflowing gas has velocities
large enough to escape from the galaxy potential well.


6.2.2. Origin of the outflow


As was shown in Section 5.1.2, the outflow reaches maximum
projected velocities (as traced by _v_ 05 and _v_ 95) of ∼±400 km s [−][1] .
These velocities are comparable to the velocities measured in
ionised outflows driven by star formation (e.g. Arribas et al.
2014; Förster Schreiber et al. 2019; Swinbank et al. 2019). The
SFR surface density, estimated from the Hα flux, in the central region of GS5001 reaches 10 M ⊙ yr [−][1] kpc [−][2] (see Fig. 11).
This high Σ _S FR_ can explain the observed outflow, since it is
known that the prevalence of outflows in star-forming galaxies
increases with Σ _S FR_ (Förster Schreiber et al. 2019). Additionally,
the global geometry with the outflow direction roughly aligned
with the minor axis is what is expected for a SF-driven outflow.
The mass loading factor, assuming the SFR from the narrow˙
Hα component SFR∼ 100 M ⊙ yr [−][1], is η = _M_ _out_ /SFR = 0.23.
The moderate mass loading factor (< 1) means that the outflow
is not having a significant impact on the total star formation of
GS5001. We note however that we are only tracing the ionised
outflow, while the molecular and atomic phases of the outflow
could also contribute significantly to the total mass outflow rate
(e.g. Fiore et al. 2017; Herrera-Camus et al. 2019; Ginolfi et al.


Article number, page 15 of 28

_A&A proofs:_ manuscript no. main



2020; Fluetsch et al. 2021; Belli et al. 2023; D’Eugenio et al.
2023).


The mass loading factor in GS5001 is in agreement with
other studies of outflows in star-forming galaxies at lower redshift ( _z_ = 0.5 − 3). For instance, Förster Schreiber et al. (2019)
find average η = 0.1 − 0.25 in a sample at _z_ = 0.6 − 2.7, while
Swinbank et al. (2019) report η = 0.2 − 0.4 in star-forming
galaxies at _z_ ∼ 1. Rodríguez Del Pino et al. (2024) detected a
resolved ionised outflow in the star-forming galaxy GS4891 at
_z_ = 3.7, which has a SFR of ∼ 45 M ⊙ yr [−][1] . This outflow has
a similar outflow velocity of 400 km s [−][1], but lower mass outflow rate _M_ [˙] out = 2 M ⊙ yr [−][1] and η = 0.02 compared to GS5001,
which could be related to the lower SFR of GS4891 compared
to GS5001.


_6.3._ _No evidence of an active galactic nucleus in GS5001_


As was discussed in the Introduction, from previous observations it is not clear whether an AGN in present in GS5001. We
do not find evidence of AGN activity in the NIRSpec data of
GS5001. The emission line diagnostic diagram (BPT, see Fig. 8)
shows line ratios similar to other star-forming galaxies at the
same redshift, with no spaxels above the AGN separation line.
We note that the line ratios for GS5001 do not fall in the region of the BPT diagram where low-metallicity AGN and starforming galaxies tend to overlap at high redshifts (Maiolino et al.
2023; Scholtz et al. 2023). Our target is at lower redshift and
have higher metallicity than the AGN presented in those works;
therefore, the classical BPT diagram can still be effectively used
to distinguish between AGN and star-forming galaxies.


GS5001 has been detected in the X-ray, with an X-ray luminosity of _L_ 0.5−7 _keV_ = (9.5 ± 2.8) × 10 [42] erg s [−][1] (Fiore et al. 2012;
Luo et al. 2017). In the Chandra Deep Field-South 7Ms catalogue (Luo et al. 2017), it has been classified as an AGN, based
on an intrinsic X-ray luminosity _L_ 0.5−7 _keV_ - 3 × 10 [42] erg/s. However, for this target no additional criteria could be applied. Therefore, Luo et al. (2017) caution that X-ray emission in this sources
may come from intense star formation. A SFR∼ 520 ± 180
M ⊙ yr [−][1] would be required to explain the observed X-ray luminosity of this target by assuming the Ranalli et al. (2003) relation
adapted for a Chabrier (2003) IMF (Kennicutt & Evans 2012).
Thus, the majority of this X-ray luminosity could be explained
by the observed SFR of this system (total SFR of the main, south
and north components: ∼ 300 M ⊙ yr [−][1] ). Lyu et al. (2022) classify this galaxy as an AGN based on the X-ray-to-radio luminosity ratio _L_ X-ray [erg s [−][1] ]/ _L_ 3 GHz [W Hz [−][1] ] - 8 × 10 [18] . However,
we note that GS5001 is only ∼ 0.25 dex above this threshold and
that the X-ray luminosity has been inferred from an extremely
small number of counts.


A recent SED analysis including JWST/NIRcam and MIRI
photometry up to restframe wavelengths < 6 µm classify this
galaxy as an AGN, because the AGN template dominates in the
range 3 − 6 µm (Lyu et al. 2024). However, given the limited
coverage in the infra-red, a fit with a galaxy dust template and a
weaker AGN component would still be acceptable. From an SED
fitting analysis with the Code Investigating GALaxy Emission
( `CIGALE` ; Burgarella et al. 2005; Noll et al. 2009; Boquien et al.
2019) from the UV to the FIR, we find that a strong AGN component in the MIR is not required to produce a good fit (C. Circosta et al., in prep.). In summary, we do not find evidence for
an AGN in GS5001, even though we cannot rule out that a weak
and possibly obscured AGN is present.


Article number, page 16 of 28



**7.** **Summary and conclusions**


In this work, we present JWST/NIRSpec IFS observations of the
galaxy GS5001 and its companions at redshift _z_ = 3.47 within
a FoV of 4” × 4” (30 × 30 kpc [2] ). We analysed the properties
of the emission lines using the high-resolution (R2700) data,
complemented by the low-resolution (R100) data, which allowed
us to cover the optical emission lines from [O ii]λλ3726, 29 to

[S iii]λ9531. We fit the data cube to derive the maps of the emission line fluxes as well as kinematic maps of the ionised gas.
The main results of this study are:


**–**
We identify several companions close to GS5001 (main target). In particular, we identify a companion in the south,
with three sub-structures (s1, s2, s3), and a companion in
the north, with three sub-structures (n1, n2, n3), showing
also an extended tail. The south components show velocities blueshifted by [-160, -153, -80] km s [−][1] with respect to
the main target, while the north companion is redshifted by
190 km s [−][1] (see Sec. 5.1).
**–** The spatially resolved emission line ratios are in the starforming region of the BPT diagram, with no sign of AGN
excitation (see Sec. 5.2.2).

**–**
We estimate the gas-phase metallicity using the R3, R23, and
O32 line ratios. We find that the main galaxy has a metallicity of 12+log(O/H)= 8.45 ± 0.04, and the companions show
slightly lower metallicities 12+log(O/H)= 8.32 − 8.42, consistent with the mass-metallicity relation at _z_ ∼ 3. The main
galaxy shows higher metallicity in the north-east region, and
lower in the south-east (see Sec. 5.2.3).
**–** From the dust-corrected Hα luminosity, we infer a total SFR
of 100 M ⊙ yr [−][1] in the main target. The south companions
have a combined SFR of 76 ± 2 M ⊙ yr [−][1] and the north companion a SFR of 106 ± 1 M ⊙ yr [−][1] . The SFR surface density
reaches values of Σ _S FR_ = 10 M ⊙ yr [−][1] kpc [−][2] in the central
region of the main galaxy (see Sec. 5.2.4).

**–**
We find that the region between the north companion and the
main target has high [N ii]/Hα and low [O iii]/Hβ line ratios,
compared with the rest of the main galaxy. These line ratios could be due to the higher metallicity or to shocks. The
gas in this region also shows enhanced velocity dispersion,
probably due to the interaction between the main and north
components (see Sec. 5.2.2).

**–**
We identify an outflow traced by a broad symmetric component clearly visible in Hα and [O iii] (with velocity dispersion
∼ 220 km s [−][1], or FWHM of ∼ 520 km s [−][1] ). The outflow originates in the nucleus of the main galaxy, and extends up to

∼
3 kpc, where interaction with the north companion might
also contribute to the broadening of the lines. The outflow
has maximum velocity of ∼ 400 km s [−][1], outflow mass of
(1.7 ± 0.4) × 10 [8] M ⊙, mass outflow rate 23 ± 5 M ⊙ yr [−][1], and
a mass loading factor of 0.23 (see Sec. 6.2). This indicates
that probably the outflow is not going to impact significantly
the star formation in the host galaxy. We note however that
we are not tracing the neutral and molecular phases of the
outflow.


JWST NIRSpec IFS data allowed us to obtain unprecedented
insights into the interplay between star formation, galactic outflows and interactions in the core of a _z_ ∼ 3.5 candidate protocluster. This valuable information could be used to inform
hydro-dynamical simulations and therefore follow the evolutionary path of GS5001 and other similar systems, like the Spiderweb Galaxy (Emonts et al. 2016) and CGG-z5 (Jin et al. 2023).


_Acknowledgements._ We thank the anonymous referee for a constructive report
that helped to improve the quality of this manuscript. This paper makes use

I. Lamperti et al.: JWST/NIRSpec view of GS5001



of the following ALMA data: ADS/JAO.ALMA#2012.1.00423.S. ALMA is a
partnership of ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work
has made use of data from the European Space Agency (ESA) mission _Gaia_
( `[https://www.cosmos.esa.int/gaia](https://www.cosmos.esa.int/gaia)` ), processed by the _Gaia_ Data Processing and Analysis Consortium (DPAC, `[https://www.cosmos.esa.int/web/](https://www.cosmos.esa.int/web/gaia/dpac/consortium)`
`[gaia/dpac/consortium](https://www.cosmos.esa.int/web/gaia/dpac/consortium)` ). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the _Gaia_ Multilateral Agreement. This work has made use of the Rainbow Cosmological
Surveys Database, which is operated by the Centro de Astrobiología (CAB),
CSIC-INTA, partnered with the University of California Observatories at Santa
Cruz (UCO/Lick,UCSC). The project leading to this publication has received
support from ORP, that is funded by the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 [ORP].
This research made use of Astropy, a community-developed core Python package
for Astronomy (The Astropy Collaboration et al. 2013), `Matplotlib` (Hunter
2007), `NumPy` (Van Der Walt et al. 2011), `corner` (Foreman-Mackey 2016).
This research has made use of "Aladin sky atlas" developed at CDS, Strasbourg Observatory, France (Bonnarel et al. 2000). IL acknowledges support
from PID2022-140483NB-C22 funded by AEI 10.13039/501100011033, from
BDC 20221289 funded by MCIN by the Recovery, Transformation and Resilience Plan from the Spanish State, and by NextGenerationEU from the European Union through the Recovery and Resilience Facility, and from PRIN-MUR
project "PROMETEUS" (202223XPZM). SA, MP and BRdP acknowledges
grant PID2021-127718NB-I00 funded by the Spanish Ministry of Science and
Innovation/State Agency of Research (MICIN/AEI/ 10.13039/501100011033).
PGP-G acknowledges support from Spanish Ministerio de Ciencia e Innovación MCIN/AEI/10.13039/501100011033 through grant PGC2018-093499B-I00. AJB, JC and GCJ acknowledges funding from the “FirstGalaxies” Advanced Grant from the European Research Council (ERC) under the European
Union’s Horizon 2020 research and innovation programme (Grant agreement
No. 789056). SCa and GV acknowledges support from the European Union
(ERC, WINGS,101040227). RM, FDE and JS acknowledge support by the Science and Technology Facilities Council (STFC), by the ERC through Advanced
Grant 695671 “QUENCH”, and by the UKRI Frontier Research grant RISEandFALL. HÜ gratefully acknowledges support by the Isaac Newton Trust and by
the Kavli Foundation through a Newton-Kavli Junior Fellowship. EB and GC acknowledges the support of the INAF Large Grant 2022 "The metal circle: a new
sharp view of the baryon cycle up to Cosmic Dawn with the latest generation
IFU facilities".


**References**


Abazajian, K. N., Adelman-McCarthy, J. K., Agüeros, M. A., et al. 2009, The
Astrophysical Journal Supplement, 182, 543
Alarie, A. & Morisset, C. 2019, Rev. Mexicana Astron. Astrofis., 55, 377
Allen, M. G., Groves, B. A., Dopita, M. A., Sutherland, R. S., & Kewley, L. J.
2008, ApJS, 178, 20
Arribas, S., Colina, L., Bellocchi, E., Maiolino, R., & Villar-Martín, M. 2014,
A&A, 568, A14
Arribas, S., Perna, M., Rodríguez Del Pino, B., et al. 2024, A&A, 688, A146
Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, Astronomical Society of
the Pacific, 93, 5
Barrera-Ballesteros, J. K., García-Lorenzo, B., Falcón-Barroso, J., et al. 2015,
A&A, 582, A21
Belli, S., Park, M., Davies, R. L., et al. 2023, arXiv e-prints, arXiv:2308.05795
Bellocchi, E., Arribas, S., Colina, L., & Miralles-Caballero, D. 2013, A&A, 557,
A59
Bian, F., Kewley, L. J., & Dopita, M. A. 2018, ApJ, 859, 175
Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82
Böker, T., Beck, T. L., Birkmann, S. M., et al. 2023, PASP, 135, 038001
Bonnarel, F., Fernique, P., Bienaymé, O., et al. 2000, A&AS, 143, 33
Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103
Burgarella, D., Buat, V., & Iglesias-Páramo, J. 2005, Monthly Notices of the
Royal Astronomical Society, 360, 1413
Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, Astrophysical Journal, 345,
245
CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501
Chabrier, G. 2003, The Publications of the Astronomical Society of the Pacific,
115, 763
Crain, R. A., Schaye, J., Bower, R. G., et al. 2015, Monthly Notices of the Royal
Astronomical Society, 450, 1937
Cresci, G. & Maiolino, R. 2018, Nature Astronomy, 2, 179
Cresci, G., Mannucci, F., Maiolino, R., et al. 2010, Nature, 467, 811
Cresci, G., Marconi, A., Zibetti, S., et al. 2015, A&A, 582, A63



Cresci, G., Tozzi, G., Perna, M., et al. 2023, A&A, 672, A128
Cresci, G., Vanzi, L., Telles, E., et al. 2017, A&A, 604, A101
Curti, M., Maiolino, R., Cirasuolo, M., et al. 2020a, MNRAS, 492, 821
Curti, M., Maiolino, R., Curtis-Lake, E., et al. 2024, A&A, 684, A75
Curti, M., Mannucci, F., Cresci, G., & Maiolino, R. 2020b, MNRAS, 491, 944
D’Agostino, J. J., Kewley, L. J., Groves, B. A., et al. 2019, Monthly Notices of
the Royal Astronomical Society: Letters, 485, L38
Davies, R. L., Förster Schreiber, N. M., Genzel, R., et al. 2021, ApJ, 909, 78
D’Eugenio, F., Perez-Gonzalez, P., Maiolino, R., et al. 2023, arXiv e-prints,
arXiv:2308.06317
Diaz, A. I. 1999, Ap&SS, 263, 143
Díaz, A. I., Castellanos, M., Terlevich, E., & Luisa García-Vargas, M. 2000,
MNRAS, 318, 462
Diaz, A. I., Terlevich, E., Vilchez, J. M., Pagel, B. E. J., & Edmunds, M. G. 1991,
MNRAS, 253, 245
Dopita, M. A. & Evans, I. N. 1986, ApJ, 307, 431
Dopita, M. A., Rich, J., Vogt, F. P. A., et al. 2014, Ap&SS, 350, 741
Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023, arXiv e-prints,
arXiv:2306.02465
Emonts, B. H. C., Lehnert, M. D., Villar-Martín, M., et al. 2016, Science, 354,
1128
Erb, D. K., Steidel, C. C., Shapley, A. E., et al. 2006, ApJ, 646, 107
Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143
Fiore, F., Puccetti, S., Grazian, A., et al. 2012, A&A, 537, A16
Fluetsch, A., Maiolino, R., Carniani, S., et al. 2021, MNRAS, 505, 5753
Foreman-Mackey, D. 2016, The Journal of Open Source Software, 1, 24
Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications
of the Astronomical Society of Pacific, 125, 306
Förster Schreiber, N. M., Genzel, R., Newman, S. F., et al. 2014, ApJ, 787, 38
Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21
Förster Schreiber, N. M., Übler, H., Davies, R. L., et al. 2019, ApJ, 875, 21
Förster Schreiber, N. M. & Wuyts, S. 2020, ARA&A, 58, 661
Franck, J. R. & McGaugh, S. S. 2016, ApJ, 817, 158
Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1
Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1
Genzel, R., Förster Schreiber, N. M., Rosario, D., et al. 2014, ApJ, 796, 7
Genzel, R., Jolly, J. B., Liu, D., et al. 2023, ApJ, 957, 48
Gillman, S., Puglisi, A., Dudzeviˇci¯ut˙e, U., et al. 2022, MNRAS, 512, 3480
Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90
Ginolfi, M., Maiolino, R., Nagao, T., et al. 2017, MNRAS, 468, 3468
González Delgado, R. M., Cid Fernandes, R., Pérez, E., et al. 2016, A&A, 590,
A44
Grazian, A., Fontana, A., de Santis, C., et al. 2006, A&A, 449, 951
Guo, Y., Ferguson, H. C., Giavalisco, M., et al. 2013, ApJS, 207, 24
Hao, C.-N., Kennicutt, R. C., Johnson, B. D., et al. 2011, The Astrophysical
Journal, 741, 124
Harrison, C. M., Alexander, D. M., Mullaney, J. R., et al. 2016, MNRAS, 456,
1195
Harrison, C. M., Johnson, H. L., Swinbank, A. M., et al. 2017, MNRAS, 467,
1965
Heckman, T. M., Robert, C., Leitherer, C., Garnett, D. R., & van der Rydt, F.
1998, ApJ, 503, 646
Herrera-Camus, R., Tacconi, L., Genzel, R., et al. 2019, The Astrophysical Journal, 871, 37
Ho, I. T., Kewley, L. J., Dopita, M. A., et al. 2014, MNRAS, 444, 3894
Holt, J., Tadhunter, C. N., Morganti, R., & Emonts, B. H. C. 2011, MNRAS,
410, 1527
Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90
Isobe, Y., Ouchi, M., Nakajima, K., et al. 2023, ApJ, 956, 139
Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80
Jin, S., Sillassen, N. B., Magdis, G. E., et al. 2023, A&A, 670, L11
Johnston, V. D., Medling, A. M., Groves, B., et al. 2023, ApJ, 954, 77
Jones, G. C., Bunker, A. J., Telikova, K., et al. 2024a, arXiv e-prints,
arXiv:2405.12955
Jones, G. C., Übler, H., Perna, M., et al. 2024b, A&A, 682, A122
Kaasinen, M., Bian, F., Groves, B., Kewley, L. J., & Gupta, A. 2017, MNRAS,
465, 3220
Kaasinen, M., Kewley, L., Bian, F., et al. 2018, MNRAS, 477, 5568
Kaplan, K. F., Jogee, S., Kewley, L., et al. 2016, MNRAS, 462, 1642
Kashino, D., Silverman, J. D., Sanders, D., et al. 2017, ApJ, 835, 88
Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, Monthly Notices of
the Royal Astronomical Society, 346, 1055
Kennicutt, R. C. & Evans, N. J. 2012, Annual Review of Astronomy and Astrophysics, 50, 531
Kewley, L. J. & Dopita, M. A. 2002, ApJS, 142, 35
Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J.
2001, The Astrophysical Journal, 556, 121
Kewley, L. J., Nicholls, D. C., & Sutherland, R. S. 2019, ARA&A, 57, 511
Luo, B., Brandt, W. N., Xue, Y. Q., et al. 2017, The Astrophysical Journal Supplement Series, 228, 2


Article number, page 17 of 28

_A&A proofs:_ manuscript no. main



Lyu, J., Alberts, S., Rieke, G. H., & Rujopakarn, W. 2022, ApJ, 941, 191
Lyu, J., Alberts, S., Rieke, G. H., et al. 2024, ApJ, 966, 229
Maiolino, R. & Mannucci, F. 2019, A&A Rev., 27, 3
Maiolino, R., Nagao, T., Grazian, A., et al. 2008, A&A, 488, 463
Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2023, arXiv e-prints,
arXiv:2308.01230
Marconcini, C., D’Eugenio, F., Maiolino, R., et al. 2024, MNRAS[ `arXiv:2407.08616` ]
Masters, D., McCarthy, P., Siana, B., et al. 2014, ApJ, 785, 153
Mathis, J. S. 1982, ApJ, 261, 195
McElroy, R., Croom, S. M., Pracy, M., et al. 2015, MNRAS, 446, 2186
Mingozzi, M., Belfiore, F., Cresci, G., et al. 2020, A&A, 636, A42
Mingozzi, M., Cresci, G., Venturi, G., et al. 2019, A&A, 622, A146
Monreal-Ibero, A., Arribas, S., & Colina, L. 2006, ApJ, 637, 138
Morishita, T., Stiavelli, M., Chary, R.-R., et al. 2024, ApJ, 963, 9
Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, The Astrophysical Journal, 737, 67
Naab, T. & Ostriker, J. P. 2017, ARA&A, 55, 59
Nakajima, K. & Ouchi, M. 2014, MNRAS, 442, 900
Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234
Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793
Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and
active galactic nuclei
Pacifici, C., Kassin, S. A., Weiner, B. J., et al. 2016, ApJ, 832, 79
Parlanti, E., Carniani, S., Übler, H., et al. 2024, A&A, 684, A24
Pérez-González, P. G., Rieke, G. H., Egami, E., et al. 2005, ApJ, 630, 82
Perna, M. 2023, IAU Symposium, 373, 268
Perna, M., Arribas, S., Catalan-Torrecilla, C., et al. 2020, A&A, 643, A139
Perna, M., Arribas, S., Colina, L., et al. 2022, A&A, 662, A94
Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89
Perna, M., Brusa, M., Cresci, G., et al. 2015, A&A, 574, A82
Perna, M., Cresci, G., Brusa, M., et al. 2019, A&A, 623, A171
Perna, M., Lanzuisi, G., Brusa, M., Cresci, G., & Mignoli, M. 2017, A&A, 606,
A96
Ranalli, P., Comastri, A., & Setti, G. 2003, A&A, 399, 39
Rauscher, B. J., Arendt, R. G., Fixsen, D. J., et al. 2017, PASP, 129, 105003
Reddy, N. A., Erb, D. K., Pettini, M., Steidel, C. C., & Shapley, A. E. 2010, ApJ,
712, 1070
Reddy, N. A., Sanders, R. L., Shapley, A. E., et al. 2023a, ApJ, 951, 56
Reddy, N. A., Topping, M. W., Sanders, R. L., Shapley, A. E., & Brammer, G.
2023b, ApJ, 952, 167
Rieke, M. J., Robertson, B., Tacchella, S., et al. 2023, ApJS, 269, 16
Rigby, J., Perrin, M., McElwain, M., et al. 2023, PASP, 135, 048001
Rodríguez Del Pino, B., Perna, M., Arribas, S., et al. 2024, A&A, 684, A187
Roy, N., Heckman, T., Overzier, R., et al. 2024, arXiv e-prints,
arXiv:2401.11612
Sanders, R. L., Shapley, A. E., Jones, T., et al. 2021, ApJ, 914, 19
Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2016, ApJ, 816, 23
Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy, N. A., & Brammer, G. B.
2024, ApJ, 962, 24
Santini, P., Ferguson, H. C., Fontana, A., et al. 2015, The Astrophysical Journal,
801, 97
Savitzky, A. & Golay, M. J. E. 1964, Analytical Chemistry, 36, 1627
Saxena, A., Overzier, R. A., Villar-Martín, M., et al. 2024, arXiv e-prints,
arXiv:2401.12199
Scharré, L., Sorini, D., & Davé, R. 2024, arXiv e-prints, arXiv:2404.07252
Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, Monthly Notices of the Royal
Astronomical Society, 446, 521
Scholtz, J., Maiolino, R., D’Eugenio, F., et al. 2023, arXiv e-prints,
arXiv:2311.18731
Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74
Schwarz, G. 1978, Ann. Statist., 6(2), 461
Shimakawa, R., Kodama, T., Steidel, C. C., et al. 2015, MNRAS, 451, 1284
Spindler, A., Wake, D., Belfiore, F., et al. 2018, MNRAS, 476, 580
Steidel, C. C., Rudie, G. C., Strom, A. L., et al. 2014, The Astrophysical Journal,
795, 165
Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS, 457, 1888
Strom, A. L., Steidel, C. C., Rudie, G. C., et al. 2017, ApJ, 836, 164
Sutherland, R., Dopita, M., Binette, L., & Groves, B. 2018, MAPPINGS V: Astrophysical plasma modeling code, Astrophysics Source Code Library, record
ascl:1807.005
Sutherland, R. S. & Dopita, M. A. 2017, ApJS, 229, 34
Swinbank, A. M., Harrison, C. M., Tiley, A. L., et al. 2019, MNRAS, 487, 381
The Astropy Collaboration, Robitaille, Thomas P., Tollerud, Erik J., et al. 2013,
A&A, 558, A33
Troncoso, P., Maiolino, R., Sommariva, V., et al. 2014, A&A, 563, A58
Übler, H., D’Eugenio, F., Perna, M., et al. 2024a, MNRAS[ `arXiv:2403.03192` ]
Übler, H., Förster Schreiber, N. M., van der Wel, A., et al. 2024b, MNRAS, 527,
9206
Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, A&A, 677, A145


Article number, page 18 of 28



Übler, H., Maiolino, R., Pérez-González, P. G., et al. 2024c, MNRAS, 531, 355
Van Der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science
and Engineering, 13, 22
van Houdt, J., van der Wel, A., Bezanson, R., et al. 2021, ApJ, 923, 11
Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2024, ApJ, 960, 126
Venturi, G., Carniani, S., Parlanti, E., et al. 2024, arXiv e-prints,
arXiv:2403.03977
Villar Martín, M., Emonts, B., Humphrey, A., Cabrera Lavers, A., & Binette, L.
2014, MNRAS, 440, 3202
Wang, W., Wylezalek, D., De Breuck, C., et al. 2024, arXiv e-prints,
arXiv:2401.02479
Wisnioski, E., Förster Schreiber, N. M., Fossati, M., et al. 2019, ApJ, 886, 124
Wisnioski, E., Förster Schreiber, N. M., Wuyts, S., et al. 2015, ApJ, 799, 209
Wylezalek, D., Vayner, A., Rupke, D. S. N., et al. 2022, ApJ, 940, L7

I. Lamperti et al.: JWST/NIRSpec view of GS5001



**Appendix A:** **Tables of the emission line fluxes**


In Tables A.1 and A.2 we report the emission line fluxes
measured from the spectra integrated over the different regions
shown in Fig. 1, from the R2700 and R100 data cubes, respectively.


**Appendix B:** **Example of spectral fit of one spaxel**


Figure B.1 shows the spectrum extracted from one spaxel
close to the centre of the main galaxy ( _x_, _y_ = 44, 46), together with the best-fit model obtained with the python routine
‘scipy.optimize.curve_fit’.


**Appendix C:** **H** α **maps from the one-component**
**Gaussian fit**


In this section, we show the maps of the Hα flux, velocity (v50)
and velocity dispersion, obtained from the fit with one Gaussian
component (Figure C.1). These maps are qualitatively similar to
the maps obtained with a variable number of components (one
or two) shown in Fig. 5 of the paper.


**Appendix D:** **Channel maps to highlight the**
**position of clump ‘c’**


In this section we show channel maps that we use to identified
a clump (‘c’) at the south-west of the main galaxy. Figure D.1
shows continuum-subtracted channel maps of Hα. The channels have a width of 40 km s [−][1] and span the range from –80 to
240 km s [−][1] with respect to the systemic redshift of the main
galaxy ( _z_ = 3.4705). The emission at the position of the clump
is visible in the channels from −40 to 160 km s [−][1] . In particular,
the morphology in the channel 120-160 km s [−][1] shows that at the
clump position there is a clear peak, separated from the emission
of the main galaxy.


**Appendix E:** **Two component fit: kinematic maps of**
**the broad component of H** α


Figure E.1 shows the maps of the broad emission of Hα, including all Gaussian components with σ - 140 km s [−][1] . The three
panels show the flux, central velocity ( _v_ 50) and the line width
(W80).


**Appendix F:** **Fit of [S** ii **] and [O** ii **] for deriving the**
**electron densities**


In this section, we show the fit of [S ii] and [O ii] for the four
regions in which we could estimate the electron density: south,
north, s2, s3, n1, and n2.
We also show the fit of [S ii] and [O ii] lines of the main target using two components (narrow+broad). The electron density derived for the narrow component is similar to the value
inferred from the one-component fit but with larger uncertainties
( _n_ _e_ = 540 [+] − [270] 280 [cm] [−][3] [). The electron density of the broad compo-]
nent is unconstrained ( _n_ _e_ = 340 [+] − [1400] 280 [cm] [−][3] [).]


**Appendix G:** **Integrated spectra**


In this section we show the integrated spectra of the regions defined in Fig. 1, together with the best-fit model. In particular,



we show the spectra of the regions ‘south’ and ‘north’, the substructures s1, s2, s3, n1, n2, n3, and the clump ‘c’.


Article number, page 19 of 28

_A&A proofs:_ manuscript no. main


Table A.1: Emission line fluxes of the different components (and sub-components) of the system, in units of [×10 [−][18] erg s [−][1] cm [−][2] ].


region [O ii]λ3726 [O ii]λ3729 Hγ Hβ [O iii]λ5007 [O i]λ6300 Hα [N ii]λ6584 [S ii]λ6716 [S ii]λ6731

main 180.7 ± 1.9 127.3 ± 0.8 45.2 ± 0.4 106.8 ± 0.4 227.6 ± 0.4 7.6 ± 0.5 305.3 ± 0.8 78.6 ± 0.5 28.1 ± 0.7 20.9 ± 0.3

main n 77.9 ± 1.7 60.9 ± 0.9 28.4 ± 0.4 59.6 ± 0.6 125.8 ± 0.6 5.1 ± 0.4 170.3 ± 1.2 43.1 ± 0.7 14.6 ± 0.6 11.0 ± 0.4

main b 316.1 ± 4.0 134.0 ± 1.4 11.2 ± 0.6 89.7 ± 1.1 197.5 ± 1.8 3.1 ± 0.5 256.4 ± 4.0 63.8 ± 1.7 26.7 ± 1.1 21.1 ± 0.8

south 81.9 ± 1.6 60.1 ± 0.7 21.3 ± 0.3 45.0 ± 0.3 125.0 ± 0.4 4.5 ± 0.4 128.6 ± 0.6 18.8 ± 0.4 13.2 ± 0.7 10.7 ± 0.3

north 189.8 ± 1.0 210.9 ± 0.5 42.1 ± 0.3 63.2 ± 0.2 202.5 ± 0.3 2.5 ± 0.3 180.7 ± 0.4 29.2 ± 0.3 20.9 ± 0.4 15.7 ± 0.2

s1 8.7 ± 1.0 5.7 ± 0.4 2.1 ± 0.2 7.0 ± 0.2 20.4 ± 0.3 0.6 ± 0.2 20.0 ± 0.4 2.1 ± 0.3 1.6 ± 0.3 1.8 ± 0.2

s2 23.4 ± 0.5 19.6 ± 0.2 5.0 ± 0.1 11.5 ± 0.1 31.2 ± 0.1 1.3 ± 0.1 32.9 ± 0.2 6.0 ± 0.1 3.4 ± 0.2 2.8 ± 0.1

s3 30.8 ± 0.4 24.2 ± 0.2 9.3 ± 0.1 18.0 ± 0.1 54.6 ± 0.1 1.7 ± 0.1 51.5 ± 0.2 6.9 ± 0.1 4.9 ± 0.1 3.5 ± 0.1

n1 12.0 ± 0.2 10.2 ± 0.1 2.0 ± 0.1 7.2 ± 0.1 17.6 ± 0.1 0.3 ± 0.1 20.5 ± 0.1 2.6 ± 0.1 1.8 ± 0.1 1.4 ± 0.1

n2 24.5 ± 0.2 21.4 ± 0.1 4.1 ± 0.1 7.5 ± 0.1 27.2 ± 0.1 0.9 ± 0.1 21.5 ± 0.1 3.8 ± 0.1 2.1 ± 0.1 1.8 ± 0.1

n3 99.2 ± 0.4 79.1 ± 0.2 31.3 ± 0.1 16.2 ± 0.1 78.8 ± 0.1 1.6 ± 0.1 46.2 ± 0.1 4.3 ± 0.1 3.7 ± 0.1 3.3 ± 0.1

c 6.2 ± 0.2 5.6 ± 0.1 1.4 ± 0.1 3.5 ± 0.1 8.2 ± 0.1 0.5 ± 0.1 10.0 ± 0.1 2.2 ± 0.1 0.7 ± 0.1 0.6 ± 0.1


**Notes.** Fluxes of the different components identified in Fig. 1. For the main galaxy, we report the fluxes obtained with one Gaussian component
model (main) and the fluxes obtained with a two-component model (narrow (main n) and broad (main b) components). The label ‘main n’ and
‘main b’ refer to the narrow and broad component of the two-component model, respectively. For the other regions, the fluxes have been obtained
with the one-component model fit. Fluxes have been corrected for obscuration using a Cardelli et al. (1989) attenuation law as described in
Sec. 5.2.1.


2.0


1.5


1.0


0.5


0.0


0.3
0.2
0.1
0.0
0.1
0.2
0.3



4300 4320 4340 4360 4380 4400
rest. wavelength [A]


6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]



4850 4900 4950 5000
rest. wavelength [A]


6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]



3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.4
0.3
0.2
0.1
0.0
0.1
0.2
0.3



3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]


v : − 5 km/s
σ : 60 km/s
v(b) : − 17 km/s
σ(b) : 172 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]



Fig. B.1: Example of fit of the average spectrum of nine adjacent spaxels close to the centre of the ‘main’ galaxy, used for the
spatially-resolved fit. Data are shown in black, the total best fit in blue, the narrow and broad components are shown in lightblue
and red, respectively, shifted vertically for visual purposes. The vertical lines mark the wavelength positions of the emission lines at
the systemic redshift of the source ( _z_ = 3.4705). The fitting residuals are shown in the bottom panel.


Article number, page 20 of 28

I. Lamperti et al.: JWST/NIRSpec view of GS5001



v50 [km s [−][1] ]



W80 [km s [−][1] ]



2.00


1.00


0


- 1.00


- 2.00



log(f/[10 [−][19] erg s [−][1] cm [−][2] ])



1.0


0.8


0.6


0.4


0.2


0.0


0.2



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



50


100


150



200


150


100



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



350


325


300


275


250


225


200


175


150



2.00 1.00 0 - 1.00 - 2.00
∆R. A. [arcsec]



Fig. C.1: Maps of the observed Hα emission obtained from the spatially resolved emission line fit with one Gaussian component.
From left to right: integrated observed flux (not corrected for obscuration), 50th percentile velocity ( _v_ 50), line width W80 (difference
between 10th and 90th percentile velocity). Contours in the flux map show the [20,40, 60, 80, 90] percentiles, contours in the _v_ 50
map start at -150 km s [−][1] and increase every 50 km s [−][1], contours in the W80 map are at [200, 300, 400] km s [−][1] .



1.25


0.62


0


- 0.62



v = [−80, − 40] km s [−][1]



v = [−40, 0] km s [−][1]



v = [0, 40] km s [−][1]



2.0


1.8


1.6


1.4


1.2


1.0


0.8



v = [40, 80] km s [−][1]



1.25


0.62


0


- 0.62



1.25


0.62


0


- 0.62



0.8


- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]







1.8


1.6


1.4


1.2


1.0



1.25


0.62


0


- 0.62




- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]



1.6


1.4


1.2


1.0


0.8




- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]



2.0


1.8


1.6


1.4


1.2


1.0


0.8


1.4


1.2


1.0


0.8




- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]



1.25


0.62


0


- 0.62



1.25



1.25


0.62


0


- 0.62



v = [80, 120] km s [−][1]



v = [120, 160] km s [−][1]





v = [160, 200] km s [−][1]



v = [200, 240] km s [−][1]



1.25


0.62


0


- 0.62












- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]




- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]





∆R. A. [arcsec]




- 1.251.25 0.62 0 - 0.62 - 1.25

∆R. A. [arcsec]



Fig. D.1: Channel maps of the Hα emission to illustrate the position of the clump ‘c’, on the south-west of the central target. The
channels have a width of 40 km s [−][1] and the velocities are given with respect to the systemic velocity. The clump ‘c’ is indicated
with a blue circle and is visible in the velocity channels [0–200] km s [−][1] .





0.60


0.30


0


- 0.30


- 0.60











0.60 0.30 0 - 0.30 - 0.60
∆R. A. [arcsec]



30


60


90


120


150


180



0.60 W80(broad) [km s [−][1] ]


0.30


0


- 0.30


- 0.60



800


750


700


650


600


550


500


450


400





Fig. E.1: Maps of the broad emission of Hα, including all Gaussian components with σ > 140 km s [−][1] . For the spaxels fitted with a
two-Gaussian model, the broader component is shown. For the spaxels fitted with a one-component model, the component is shown
only if σ - 140 km s [−][1] . From left to right: observed flux (not corrected for attenuation), centroid velocity, and velocity dispersion
(W80). Only spaxels with S/N> 3 are shown.


Article number, page 21 of 28

60


50


40


30


20


10


~~0~~


10


15

10

5

0

5


10

15


15


10


5


~~0~~


5
4
3
2
1
0
1
2
3
4


4


3


2


1


~~0~~


1


2


3


4

3

2

1

0

1

2

3




[OII] n e : 753 − [+217] 178 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]


[OII] n e : 624 − [+214] 183 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]


[OII] n e : 254 − [+199] 146 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]



_A&A proofs:_ manuscript no. main


30



20


10


~~0~~


10


15

10

5

0

5


10

15


12


10


8


6


4


2


~~0~~


2


6

4

2

0

2

4

6


4


3


2


1


~~0~~


1


2


43

3

2

1

0

1

2

3




[SII] south


6710 6720 6730 6740
rest. wavelength [Å]


[SII] s2


6710 6720 6730 6740
rest. wavelength [Å]


[SII] n1


6710 6720 6730 6740
rest. wavelength [Å]




[SII] north


6710 6720 6730 6740
rest. wavelength [Å]


[SII] s3


6710 6720 6730 6740
rest. wavelength [Å]


[SII] n2


6710 6720 6730 6740
rest. wavelength [Å]




[OII] n e : 149 − [+124] 90 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]


[OII] n e : 201 − [+128] 103 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]


[OII] n e : 512 − [+319] 216 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]



Fig. F.1: Simultaneous spectral fit of the [O ii]λλ3726, 29 and [S ii]λλ6716, 31 doublets to derive the electron density from the
integrated spectrum of the targets south and north (upper raw), s2 and s3 (middle raw), n1 and n2 (lower raw). The blue curve shows
the total best-fit model, the light-blue curves show the best-fit Gaussians for the individual emission lines and the gray curves show
the uncertainties of the MCMC fit. The bottom panels show the residuals, the dashed line shows the one-sigma error level.


Article number, page 22 of 28

I. Lamperti et al.: JWST/NIRSpec view of GS5001


Table A.2: Fluxes of the different components of the system derived from the R100 data cube, in units of [×10 [−][18] erg s [−][1] cm [−][2] ].


region [S ii]λ6716 + λ6731 [S iii]λ9069 [S iii]λ9531

main 55.3 ± 6.8 17.2 ± 3.3 43.1 ± 4.1

south 27.9 ± 3.6 6.8 ± 1.8 19.9 ± 2.3

north 23.0 ± 3.1 8.5 ± 1.2 21.0 ± 1.4

s1 4.0 ± 0.8 2.0 ± 0.6 3.8 ± 0.8

s2 8.2 ± 1.0 1.5 ± 0.4 4.7 ± 0.6

s3 6.5 ± 1.4 2.4 ± 0.7 7.6 ± 0.8

n1 3.0 ± 0.6 1.1 ± 0.3 2.7 ± 0.3

n2 3.8 ± 0.6 1.1 ± 0.3 2.6 ± 0.3

n3 6.7 ± 0.9 1.1 ± 0.2 4.4 ± 0.3

c 2.6 ± 0.4 0.6 ± 0.2 1.4 ± 0.3


**Notes.** Fluxes of the different components identified in Fig. 1. Fluxes
have been corrected for obscuration using a Cardelli et al. (1989) attenuation law as described in Sec. 5.2.1. We report the total flux of the

[S ii]λ6716 + [S ii]λ6731 doublet, since the two lines are not resolved in
the R100 data.


80




[SII]


6710 6720 6730 6740
rest. wavelength [Å]



60


40


20


~~0~~


20

20
15
10
5
0
5

10
15
20




[OII] n e : 543 − [+280] 272 [cm] [−][3]


3720 3730 3740 3750
rest. wavelength [Å]



Fig. F.2: Simultaneous spectral fit of the [O ii]λλ3726, 29 and

[S ii]λλ6716, 31 doublets to derive the electron density from
the integrated spectrum of the main target using two components (broad and narrow). The blue curve shows the total best-fit
model, the light-blue and red curves show the best-fit narrow
and broad Gaussian components, respectively, for the individual
emission lines. The grey curves the uncertainties of the MCMC
fit. The bottom panels show the residuals.



Article number, page 23 of 28

6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]



120


100


80


60


40


20


0


20
15
10
10 [505]
15
20


100


80


60


40


20


0


20
15
10
10 [505]
15
20



v : − 133 ± 1 km/s
σ : 80 ± 1 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



_A&A proofs:_ manuscript no. main


6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘south’. The total best fit is shown in blue. The individual narrow components are shown
in lightblue, shifted vertically for visual purposes. The vertical lines mark the wavelength positions of the emission lines at the
systemic redshift of the main source ( _z_ = 3.4705). The fitting residuals are shown in the bottom panel.



6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



50


40


30


20


10


0


10


15
10
5
0
5

10
15


40


30


20


10


0


10


15
10
5
0
5

10
15



v : 191 ± 1 km/s
σ : 100 ± 2 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘north’.



Article number, page 24 of 28

I. Lamperti et al.: JWST/NIRSpec view of GS5001



40


30


20


10


0


10


15
10
5
0
5

10
15


40


30


20


10


0


10


15
10
5
0
5

10
15



v : − 161 ± 2 km/s
σ : 68 ± 2 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘s1’.



30


25


20


15


10


5


0


65
4
2
0
2
4
6


25


20


15


10


5


0


65

4
2
0
2

4



v : − 154 ± 1 km/s
σ : 77 ± 1 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]



3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘s2’.



6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]


6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]


Article number, page 25 of 28

35


30


25


20


15


10


5


0


6
4
2
0
2
4
6


30


25


20


15


10


5


0


6
4
2
0
2
4
6


12


10


8


6


4


2


0


2

[2101234] 3


8


6


4


2


0


2

[2101234] 3



v : 211 ± 1 km/s
σ : 80 ± 2 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



v : − 82 ± 1 km/s
σ : 77 ± 1 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



_A&A proofs:_ manuscript no. main


6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘s3’.



6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]


6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]



6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘n1’.



Article number, page 26 of 28

I. Lamperti et al.: JWST/NIRSpec view of GS5001



6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



8


6


4


2


0


2

[2101234] 3


8


6


4


2


0


2

[2101234] 3


6


4


2


0


2


4

[2101234] 3


6


4


2


0


2


4

3
2
1
0
1
2
3



v : 217 ± 1 km/s
σ : 73 ± 2 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



v : 180 ± 3 km/s
σ : 104 ± 3 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘n2’.



6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘n3’.



6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]


6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]


Article number, page 27 of 28

6660 6680 6700 6720 6740 6760 6780
rest. wavelength [A]


4850 4900 4950 5000
rest. wavelength [A]



_A&A proofs:_ manuscript no. main


6520 6540 6560 6580 6600 6620 6640
rest. wavelength [A]


4300 4320 4340 4360 4380 4400
rest. wavelength [A]



6


4


2


0


32
2

1
0

1
2


5


4


3


2


1


0


1


2

3
2

1
0

1
2



v : 67 ± 2 km/s
σ : 73 ± 3 km/s


6240 6260 6280 6300 6320 6340 6360
rest. wavelength [A]


3720 3740 3760 3780 3800 3820 3840
rest. wavelength [A]



Fig. G.1: Integrated spectrum of source ‘c’.



Article number, page 28 of 28


</paper>

## Items to check

```json
[
 {
  "path": "data.alma_project_codes[0].evidence[1]",
  "value": "2012.1.00423.S",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00423.S."
 },
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "Integral field spectroscopy (IFS) in high-resolution (R2700, G235H/F170LP) and low-resolution (R100, PRISM/CLEAR) modes from GA-NIFS GTO programme #1216.",
  "failed_quote": "GS5001 was observed with NIRSpec IFS (Böker et al. 2022; Rigby et al. 2023) both with the high-resolution (R ∼ 2700) and with the low-resolution (R ∼ 100) mode."
 },
 {
  "path": "data.other_facilities[3].provided.evidence[0]",
  "value": "DR3 catalogue star positions used for absolute astrometric registration of HST and NIRSpec data.",
  "failed_quote": "To derive the absolute astrometry of the HST image, we used the two stars present in a 90′′ × 90′′ FoV around GS5001 and calculated the mean offset of their position from the co-ordinates reported in the Gaia DR3 catalogue"
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "JWST/NIRSpec IFS enables spatially resolved mapping of rest-frame optical emission lines (including Hα, Hβ, [O III], [S III]) at z > 3 at ~0.1 arcsec resolution, which is inaccessible from the ground.",
  "failed_quote": "The IFS capabilities of the NIRSpec instrument (Jakobsen et al. 2022; Böker et al. 2022) on board the James Webb Space Telescope (JWST) enable one for the first time to map the optical lines at z > 3 with a spatial resolution of ∼ 0.1\"."
 }
]
```
