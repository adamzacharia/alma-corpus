# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.539.1977W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–31 (2025) Preprint 15 April 2025 Compiled using MNRAS L [A] TEX style file v3.0

### **ALMACAL XIV: X-Shooter Spectroscopy, Infrared Properties and Radio** **SEDs of Calibrators**


Simon Weng, [1] _[,]_ [2] _[,]_ [3] _[,]_ [4] _[★]_ Elaine M. Sadler, [1] _[,]_ [2] _[,]_ [3] Emily Kerrison, [1] _[,]_ [2] _[,]_ [3] Victoria Bollo, [5] Céline Péroux, [4] _[,]_ [5]

Martin Zwaan, [5] Elizabeth K. Mahony, [3] James R. Allison, [6] Jianhang Chen, [7] Roland Szakacs, [5]

Hyein Yoon, [8] _[,]_ [9]

1 _Sydney Institute for Astronomy, School of Physics A28, University of Sydney, NSW 2006, Australia_
2 _ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D)_
3 _ATNF, CSIRO Space and Astronomy, PO Box 76, Epping, NSW 1710, Australia_
4 _Aix Marseille Université, CNRS, LAM (Laboratoire d’Astrophysique de Marseille) UMR 7326, 13388, Marseille, France_
5 _European Southern Observatory, Karl-Schwarzschildstrasse 2, D-85748 Garching bei München, Germany_
6 _First Light Fusion Ltd., Unit 9/10 Oxford Pioneer Park, Mead Road, Yarnton, Kidlington OX5 1QU, UK_
7 _Max-Planck-Institut für Extraterrestrische Physik (MPE), Giessenbachstrasse 1, D–85748 Garching, Germany_
8 _Institute for Data Innovation in Science, Seoul National University, 1 Gwanak-ro, Gwanak-gu, Seoul 08826, Republic of Korea_
9 _Astronomy Program, Department of Physics and Astronomy, Seoul National University, 1 Gwanak-ro, Gwanak-gu, Seoul 08826, Republic of Korea_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

The ALMACAL−22 survey includes over 2700 hours of observations of ALMA phase and amplitude calibrators, spanning
frequencies from 84 to 950 GHz across bands 3 to 10. In total, 687 out of the 1,047 calibrators have redshifts confirmed with
spectroscopy and we find an additional 50 featureless blazars. The redshift distribution of the ALMACAL-22 sample peaks at
_𝑧_ ≈ 1 and spans a wide range, from the nuclei of nearby galaxies at _𝑧_ ≪ 0 _._ 01 to quasars at _𝑧_ = 3 _._ 742. 70 new VLT/X-Shooter
spectra of these sources covering UV to NIR wavelengths are also presented, which will be used in future stacking experiments
to search for cold gas in the circumgalactic medium. Infrared magnitudes from WISE indicate that the majority of the sources are
consistent with being quasars or blazars. After fitting the radio spectral energy distributions of the calibrators, we find that most
ALMA calibrators exhibit peaked spectra or are re-triggered which is surprising given the large number of blazars in the sample.
The peak frequencies span three orders of magnitude from 100 MHz to 170 GHz, corresponding to linear sizes ranging from
sub-pc to _>_ 10 kpc. In the future, when combined with high-resolution radio imaging, these results will offer valuable constraints
on the molecular gas content of the CGM, as well as the ages and duty cycles of AGN jets. The ever-growing ALMACAL data
set will remain an indispensable resource for studying the various aspects of galaxy formation and evolution.


**Key words:** radio continuum: galaxies – catalogues – galaxies: active – BL Lacertae objects: general – quasars: general



**1** **INTRODUCTION**


The Atacama Large Millimetre Array (ALMA) is a powerful radio
interferometer operating at frequencies of 35 to 950 GHz. Each science project using ALMA requires observations of bright (≈1 Jy),
compact calibrators near the target. The ALMACAL survey compiles ALMA observations of these calibrator sources used for flux,
phase, and bandpass calibration (Zwaan et al. 2022). These calibrator observations are taken at different times, in various ALMA
bands and array configurations, depending on the science project,
thus providing extensive coverage across the sub-mm spectrum. Additionally, the bright, compact nature of the calibrators allows for
precise self-calibration.
The total on-source time for calibrators accumulated until May
2022 exceeds 2700 hours and covers a sky area greater than 1000
arcmin [2] (Bollo et al. 2024). We will refer to this dataset as the


_★_ E-mail: simonw358@gmail.com


© 2025 The Authors



ALMACAL−22 sample. So far, various scientific investigations have
used fields containing ALMA calibrator sources. The calibrator data
have been employed to search for dusty star-forming galaxies (DSFGs; Oteo et al. 2016; Klitsch et al. 2020; Chen et al. 2023a,b) and
study their properties at higher resolution when data permits (Oteo
et al. 2017). Importantly, these calibrator fields are distributed across
the sky, making the measured number counts of DSFGs largely immune to cosmic variance, the variation of galaxy clustering properties
in different patches of sky. Furthermore, searching blindly for carbon
monoxide (CO) emission that traces molecular gas helps constrain
the evolution of the cosmic molecular gas density (Klitsch et al.
2019b; Hamanowicz et al. 2023; Bollo et al. 2025). Serendipitous
observations of galaxies associated with quasar absorption lines have
also enabled case studies of ionized, neutral, and molecular gas in
galaxies (Klitsch et al. 2018, 2019a). Additionally, stacking the submm spectra of calibrator sources at the redshift of nearby galaxies has
been used to place constraints on the amount of extended molecular
gas in the circumgalactic medium (CGM; Klitsch et al. 2023). As the

2 _Simon Weng et al._


volume of calibrator data continues to grow, these various scientific
endeavors will be pursued in greater depth in the future.
To fully exploit the ALMACAL data, understanding the properties
of the calibrators is crucial. For instance, obtaining accurate redshifts
is necessary to ensure that the calibrator is at a higher redshift than
foreground galaxies in stacking experiments (Klitsch et al. 2023).
Moreover, verifying that CO emitters are at different redshifts from
the calibrators is important to ensure that measured CO luminosity
functions are not affected by clustering (Hamanowicz et al. 2023;
Chen et al. 2023b). Bonato et al. (2018) presented the first catalogue
of 754 ALMA calibrators based on observations up until September
2017, focusing on radio classification, variability, and global spectral
energy distributions of the calibrators.
In this work, we present an updated catalogue of 1,047 calibration sources in the ALMACAL−22 sample, including new redshifts
obtained from recent Very Large Telescope (VLT) observations (Section 2). We examine the redshift properties of the calibrators, as well
as their infrared classifications based on WISE data (Section 3). Finally, we re-evaluate the radio spectral energy distributions of the
calibrators (Section 4) and discuss future research directions using
the expanding ALMACAL sample (Section 5).


**2** **METHODS**


**2.1** **The ALMACAL** −22 **sample**


The ALMACAL−22 sample presented in this work includes 1,047
sources observed between 2012 August and 2022 May for approximately 2750 hours. Observations span bands 3 to 10 and a distribution of integration times across the eight bands can be found in Bollo
et al. (2024). In Figure 1, we depict the distribution of sources on
the sky with colour representing the band dominating observations
and marker size proportional to the square root of the total on-source
time (∝ ~~[√]~~ _𝑇_ tot ).


**2.2** **Optical cross-matching**


We use the NASA Extragalactic Database (NED [1] ) and SIMBAD [2]

databases to search for optical counterparts to the ALMACAL
sources. Additionally, we perform a cross-match with an optical catalogue of sources in the Australia Telescope 20 GHz (AT20G) Survey
(Mahony et al. 2011). There is substantial overlap between the two
samples, as many of the southern ALMA calibrators were selected
from bright sources in Mahony et al. (2011). As ALMACAL sources
are typically bright and compact to ensure consistent flux, phase and
bandpass calibration, much of the difficulty and uncertainty in identifying optical counterparts to radio sources is mitigated. In Figure 2,
we show a histogram of on-sky separations after cross-matching ALMACAL sources with nearby optical sources. 97 per cent of optical
counterparts are found within 1 arcsecond of the radio position, while
only 6 radio sources do not have any counterpart within 3 arcseconds.
Sources without optical counterparts are tabulated in Table 1.
We give the names of and separations to the nearest optical source.
Three sources (J1032-5917, J1220-5604 and J1555-4150) are found
at low Galactic latitudes in crowded stellar fields, while the remainder
are likely too faint at visible wavelengths. All six sources without
counterparts are within the current footprint observed by the Vera


1 `[https://ned.ipac.caltech.edu/](https://ned.ipac.caltech.edu/)`
2 `[https://simbad.cds.unistra.fr/simbad/](https://simbad.cds.unistra.fr/simbad/)`


MNRAS **000**, 1–31 (2025)



Rubin Observatory (Ivezić et al. 2019), and an optical counterpart
will likely be identifiable in these deeper images.
Our choice of a 3-arcsecond threshold to determine whether an

ALMA calibrator is matched to an optical source is somewhat arbitrary. While ALMA calibrator positions are typically accurate to
within 3 mas due to their very-long-baseline interferometric (VLBI)
observations (Petrov & Kovalev 2025), the astrometric accuracy
of optical sources is more variable, as they are drawn from large
databases. To assess the likelihood of mismatches between radio and

optical sources, we cross-matched the ALMACAL catalog with NED
after shifting the radio coordinates by one arcminute in both RA and
Dec. We find that [0.5, 1.3, 3.5, 6.7] per cent of the radio sample
with scrambled positions matches an optical source within [0.5, 1,
2, 3] arcseconds. This suggests that at a 3-arcsecond separation, the
probability of a false positive in the cross-match is approximately 7
per cent, while the error rate drops to just 0.5 percent within 0.5 arcseconds (941 out of 1047 calibrators have separations smaller than
0.5 arcseconds).


**2.3** **VLT X-Shooter UV–NIR observations**


We obtained observations of cross-matched optical sources without
redshifts or spectra using VLT/X-Shooter (Vernet et al. 2011) in programmes 0101.A-0528 (PI. Mahony) and 111.253L.001 (PI. Weng).
We observed 70 southern ALMACAL calibrators across both programmes, including repeat observations of P101 targets with low
signal-to-noise ratio (SNR _<_ 3) spectra. Optically bright ( _𝑅<_ 21)
quasars were targeted to facilitate observations under ‘any-weather’
conditions. We chose slit widths of 1.3, 1.2 and 1.2 arcseconds for

−
the UVB, VIS and NIR arms (covering 300 2500 nm) to account for
poor seeing conditions. These widths correspond to a resolving power
of _𝑅_ = 4100 _,_ 6500 _,_ 4300, respectively. Each target was observed in
the NODDING mode to improve the removal of sky emission. Exposure times range from 900 to 2,700 seconds, depending on the
magnitude of the target.
We processed the X-shooter data from the two programs using
version 3.6.3 of the ESO X-shooter pipeline (Modigliani et al. 2010)
within the ESO Reflex environment (Freudling et al. 2013). The
data from each arm were independently reduced, using the nodding
mode setting in the pipeline. This automated workflow involves subtracting detector bias and dark current, followed by wavelength and
flux calibration, to produce flux-calibrated 1D spectra. In nodding
mode, science frames at different nodding positions along the slit are
combined into an image sequence, with pairs of combined frames
subtracted to achieve sky subtraction by differencing the images
from nodding positions A and B. After visually inspecting the twodimensional spectra, we extract the one-dimensional spectra using
the pipeline. For the P101 data, we reach median SNR values of [7.4,
12.7, 3.0], while for the P113 data, the median SNR values are [9.4,
13.0, 3.1] for the UV, VIS, and NIR arms, respectively. The signalto-noise ratio for the visible and infrared arms is calculated in regions
away from significant telluric bands, namely at _𝜆_ ≃ 7590 −−7700,
13450 − 14500 Å and 18000 − 20950 Å. We use marz [3] (Hinton et al.
2016) to determine redshifts. Examples of a featureless blazar and
QSO are shown in Figures 3 and 4, with the remainder provided in
Appendix A.


3 https://samreay.github.io/Marz/#/overview

_ALMACAL XIV_ 3









|75°<br>B and3 B and4 B and5 B and6 B and7 B and8 B and9 B and10<br>60°|Col2|Col3|
|---|---|---|
|-150°<br>-120°<br>-90°<br>-60°<br>°<br>30°<br>45°<br>|-30°<br>0°<br>30°<br>ALMACAL-22|60°<br>90°<br>120°<br>150°|
|-60°<br>-45°<br>-30°<br>°|-60°<br>-45°<br>-30°<br>°|-60°<br>-45°<br>-30°<br>°|


-75 °



15 °


0 °


-15 °





**Figure 1.** The distribution of 1,047 ALMACAL sources on the sky using an Aitoff projection. Each source is coloured by the band with the longest on-source
time, while the size of each source is proportional to the square root of the total integration time. We refer the reader to Chen et al. (2023a) for the distribution

of on-source times across each band.


ALMACAL ID RA Dec Nearest Source On-sky Separation
(hh:mm:ss) (dd:mm:ss) (arcseconds)

J0304+3348 00:32:51 02:47:41 2MASS J08123858+0247496 15.1

J0501-0159 04:51:57 00:06:11 MACS J0451.9+0006 10.1

J1032-5917 10:32:43 -59:17:57 2MASS J10324189-5917488 9.5

J1220-5604 12:20:26 -56:04:43 WISEA J122026.74-560446.0 4.8

J1555-4150 15:55:18 -41:50:32 WISEA J155517.78-415028.4 4.9

J1717-3948 12:41:57 -02:10:53 2MASS J12415707-0211059 13.1


**Table 1.** The ALMACAL sources without an optical counterpart within 3 arcesconds. Along with the ALMACAL name and coordinates, we provide the nearest
optical source from NED, including the separation in arcseconds to that optical source. The location of these sources near the Galactic plane or at very low
declinations are some of the reasons why an optical counterpart is not easily identifiable.



**2.4** **ALMACAL redshift catalogue construction**


To refine the redshift determination method, the co-authors (CP, EK,
EM, ES, HY, JA, JC, RS, SW) studied an initial sample of the same 20
calibrator sources. We noted any discrepancies and discussed ways
to standardise and optimise the process. In addition to large surveys
such as the Sloan Digital Sky Survey (SDSS; York et al. 2000) and
Dark Energy Spectroscopic Instrument (DESI) survey(DESI Collaboration et al. 2016, 2025), we found that several works following up
bright radio sources contributed multiple redshifts to the ALMACAL
catalogue and contained corresponding spectra (e.g. Drinkwater et al.
1997; Hook et al. 2003; Shaw et al. 2013; Titov et al. 2013) or a list of
emission lines (Hewitt & Burbidge 1987). These works were noted
by the team and increased the efficiency of determining redshifts and
their confidence. Spectroscopic redshift measurements for objects
not belonging to large surveys were each checked independently by
two members of the collaboration. An important part of this process was establishing the provenance of each redshift by tracking
back through the literature to identify and record the source of the



original measurement. In completing the redshift determinations,
the substantial dedication and meticulous effort invested by the team
were paramount. This labour-intensive and detail-oriented process
was crucial in enhancing both the precision and dependability of the
redshift values in the final ALMACAL catalogue.


The cross-matched ALMACAL sources were initially split into
two distinct catalogues based on whether the optical counterpart belonged to large surveys such as the Two-degree-Field Galaxy Redshift
Survey (2dFGRS; Colless et al. 2001), 6dF Galaxy Redshift Survey
(6dFGRS; Jones et al. 2004), SDSS and DESI DR1 (DESI Collaboration et al. 2025). Redshifts of sources with counterparts in these
surveys could more easily be determined by directly accessing the
spectra. Sources observed by X-Shooter were differentiated from the
remaining sources that required more extensive examination using
the NED and SIMBAD databases.


MNRAS **000**, 1–31 (2025)

4 _Simon Weng et al._


10 [3]


10 [2]


10 [1]


10 [0]


0 1 2
On-sky separation [arcsec]


**Figure** **2.** A histogram of the separations between the ALMACAL radio
source and cross-matched optical source. 90% (97%) of radio sources have
an optical counterpart within 0.5 (1.0) arcseconds. Only 6 out of 1,047
ALMACAL−22 sources do not have an known optical counterpart within

3 arcseconds.


_2.4.1_ _Format_


The final ALMACAL redshift catalogue is publicly available online
on GitHub [4] and VizieR. The column numbers, names and descriptions of the ALMACAL redshift catalogue are described in Table 2.
In the case where multiple sources cite the same redshift value,
precedence is given to papers with a publicly accessible spectrum.
In the ‘Confidence’ column, we assign a quality value from 0 to
4, or 6 or 7, classifying each source. This notation is adapted from
the 6dF survey (Jones et al. 2009), with an additional quality flag
7 included to indicate a featureless BL Lac spectrum. They are as
follows: (0) sources lacking both spectrum and redshift measurement,
(1) sources with a spectrum but no viable redshift estimate (excluding
featureless BL Lac sources), (2) sources with or without a spectrum
where a possible redshift is derived from weak absorption or emission
lines, (3) sources with a spectroscopic redshift from a published
paper but without a publicly available spectrum, or sources with a
spectrum showing a single strong absorption or emission feature and
weaker lines, (4) sources with a spectrum featuring multiple strong
absorption or emission lines, (6) sources that are the nuclei of galaxies
at redshift _𝑧_ ≪ 0 _._ 01 such as M87, and (7) BL Lac objects without
detectable emission lines. Hence, objects without a publicly available
spectrum can only be assigned a confidence of 3 or lower, and this
includes older works where only the emission lines are tabulated (e.g.
Hewitt & Burbidge 1987). Quantitatively, sources with redshift errors
≲ 300 km s [−][1] are classified with confidence 4, whereas a confidence
of 3 means that no error measurement is possible or errors are ≳ 300
km s [−][1] .

In Figure 5, the bar chart depicts the distribution of flags assigned
to the 1,047 ALMACAL sources. 687 objects are assigned flag values
of 3 or 4, signifying that ≈65 per cent of the sample have reliable red

4 `[https://github.com/simonw358/ALMACAL](https://github.com/simonw358/ALMACAL)`


MNRAS **000**, 1–31 (2025)



shift measurements. Additionally, 50 objects are spectroscopicallyconfirmed BL Lacs without detectable emission lines. A further 8

calibrators appear to be the active nuclei of nearby galaxies such as
M87 used for Event Horizon Telescope observations (Event Horizon
Telescope Collaboration et al. 2019).


**3** **SAMPLE PROPERTIES**


The properties of the ALMACAL calibrators have been previously
discussed in Bonato et al. (2018), where flux, spectral index, and
redshift distributions were presented using an earlier sample of 754
calibrators based on observations up to September 2017. In this
work, we revisit the redshift distribution with an updated catalogue
of 1,047 sources, incorporating revised redshifts. Additionally, we
include classifications of the sources from the Wide-field Infrared

Survey Explorer survey (Wright et al. 2010). A comprehensive study
of the ALMACAL−22 data products, including properties such as
sensitivity, resolution, and integration time for the same sample, can
be found in Bollo et al. (2024).


**3.1** **Redshift distribution**


We show the redshift distribution of the ALMA calibrators in the

left panel of Figure 6. The blue histogram represents the distribution
of 735 sources with redshift confidence ≥ 2, whereas the green
histogram represents sources with confidence 3 or 4. Similar to the
distribution of band 3 and 6 ALMACAL sources in Bonato et al.

(2018), the distribution peaks at _𝑧_ ≈ 1, and the highest-redshift
source is at _𝑧_ = 3 _._ 789.

Additionally, we show in Figure 6 (right panel) how the fraction
of sources with a successful redshift varies with their W1 magnitude
from WISE. We include error bars proportional to √ _𝑁_, where _𝑁_

is the number of sources in a given bin. Unlike typical redshift
surveys where completeness decreases with increasing magnitude,
we find a more varied relationship where completeness appears to
mildly increase (or plateau, considering the errors) between W1
= 12 _._ 5 and 15 mag. This is likely due to a significant fraction of the
brighter sources in the sample being blazars, where the non-thermal
continuum masks emission features, making redshift determination
difficult. The precise classification of ALMACAL−22 sources will
be discussed in the forthcoming section.


**3.2** **WISE classification**


We present classifications of the sources based on their infrared magnitudes from the WISE survey in Figure 7 (Wright et al. 2010). Using
astroquery (Ginsburg et al. 2019), we retrieve WISE magnitudes
for the cross-matched optical positions discussed in section 2 from
the NASA Extragalactic Database. In total, 774 sources have measurements of the W1, W2, and W3 magnitudes, corresponding to
3.4, 4.6, and 12 _𝜇_ m, respectively, which are required to produce the
WISE colour-colour plot (Wright et al. 2010).
Using the W1, W2, and W3 magnitudes, the WISE colour-colour
plot highlights the regions typically occupied by different object
types. As seen in the contours from a kernel density estimator, most
ALMACAL sources fall within the QSO and Seyfert loci, consistent
with these sources being active galactic nuclei (AGN), particularly
quasars and blazars. Objects outside these contours (22 purple diamonds) are potentially dust-obscured AGN or the nuclei of nearby
galaxies. Blazars have been found to delineate a specific region of the

_ALMACAL XIV_ 5



_×_ 10 _[−]_ [16]



4


2





0





2



0



2





1


0


**Figure 3.** Example of an X-Shooter spectrum of a featureless blazar with Mg ii λλ 2796, 2803 absorption lines at _𝑧_ abs = 0 _._ 462 highlighted in green. We include
a simulated atmospheric transmission curve in red for reference only for the optical and near-infrared wavelengths where there is telluric absorption (Bertaux
et al. 2014).


Number Name Description
1 Name_ALMACAL the name of the source in ALMACAL that is consistent with previous publications
2 RA_ALMACAL the right ascension of the radio source in ICRS co-ordinates (decimal degrees)
3 Dec_ALMACAL the declination of the radio source in ICRS co-ordinates (decimal degrees)

4 Redshift the redshift of the source

5 Spectrum a boolean 1/0 (TRUE/FALSE) flag indicating whether the optical spectrum for the source is publicly available
6 Provenance the original publication containing the redshift and spectrum, if available

7 Confidence the confidence of the redshift measurement

8 Name_IAU an IAU name of the source obtained from NED or SIMBAD
9 RA_Optical the right ascension of the optical source in ICRS co-ordinates (decimal degrees)
10 Dec_Optical the declination of the optical source in ICRS co-ordinates (decimal degrees)
11 Separation the separation between the radio and optical source (arcseconds)


**Table** **2.** The numbers, names, and descriptions of the columns in the ALMACAL catalogue in this table. Magnitudes can be retrieved using the optical
coordinates on NED or SIMBAD; magnitudes are not included in the table due to the large variety of instruments and filters.



WISE colour-colour diagram, known as the WISE blazar strip (Massaro et al. 2011, 2012), which corresponds to the green dashed line
in Figure 7. Separating blazars that are dominated by non-thermal
emission from the larger population of quasars is challenging based
on WISE colours alone, as they occupy similar regions in the diagram. However, the alignment of the contours with the gradient of

−
the blazar strip suggests that the ALMACAL 22 sample is predominantly composed of blazars. This result independently corroborates
the findings of Bonato et al. (2018), which, based on an earlier version
of the ALMACAL catalogue (up to September 2017), determined
that 97 per cent of the sources are consistent with being blazars, with
approximately half classified as flat-spectrum radio quasars. Their
classification was based on a cross-match with the Roma Multifre
quency Catalogue of Blazars (Massaro et al. 2009) and an analysis



of the low-frequency spectral index ( _𝛼_ low, measured between 1 and
5 GHz), supplemented by variability studies and the presence of
associated _𝛾_ -ray emission.


**4** **RADIO SPECTRAL ENERGY DISTRIBUTION**


Fitting the radio spectral energy distributions (SEDs) of ALMACAL
sources is particularly interesting because they represent the brightest
(sub-)mm sources in the sky. Typically, SED fitting is limited to
frequencies ≤ 20 GHz, with the upper frequency set by the AT20G
survey (Murphy et al. 2010). This process comes with challenges;
these sources are often highly variable, and dust emission may need
to be accounted for at these high frequencies. Nonetheless, these


MNRAS **000**, 1–31 (2025)

6 _Simon Weng et al._


_×_ 10 _[−]_ [16]


2







0

_×_ 10 _[−]_ [16] 3500 4000 4500 5000 5500





2



0



2


1


0





**Figure 4.** Example of an X-Shooter spectrum of a QSO with broad emission lines. The identical simulated transmission curve in Figure 3 is shown here in red.



challenges also provide opportunities to study the radio properties of
these sources using SEDs.
In this section, we present radio SED fits using the recently developed RadioSED [5] algorithm (Kerrison et al. 2024). RadioSED
offers an automated framework to retrieve data from large-area surveys and fit the corresponding data using a Bayesian nested sampling
approach. The SED is fitted using four analytical models: i) a power
law for steep, flat, or inverted spectra, ii) a simple peaked spectrum
source model (Snellen et al. 1998), iii) a peaked spectrum model with
curvature (Orienti et al. 2007) and iv) a re-triggered source modelled
by a linear combination of the power law and simple peaked spectrum source models. For a more detailed explanation of the modelling
framework and its applications, we refer readers to Kerrison et al.
(2024). Out of the 1,047 ALMACAL sources, we perform SED fitting
for 897 objects that are observed in the Rapid ASKAP Continuum
survey (RACS-low; Hale et al. 2021).
Five example SEDs are displayed in Figure 8, with four labelled
by their corresponding models: power law, peaked spectrum (simple
and curved) or re-triggered. The fifth example has been fit with a
re-triggered model that has significant residuals due to variability.
While there are four models used to fit the data, we use a marginally
different set of classifications by grouping both peaked spectrum
models together. We also introduce a final class labelled ‘complex’
to describe data that is poorly-fitted, has unusual model parameters
or unnatural spectral indices. Variability is typically responsible for
these fits as shown in the bottom-right SED of Figure 8. The data span
more than 20 epochs which can allow sources to exhibit variability.


5 `[https://github.com/ekerrison/RadioSED/](https://github.com/ekerrison/RadioSED/)`


MNRAS **000**, 1–31 (2025)



We note that after visually inspecting each SED, we find no evidence
for dust emission that could not be explained by variability.


The resulting distribution of the final classifications are shown in
the left panel of Figure 9. We find that ALMA calibrator sources
are typically peaked spectrum (PS) or re-triggered sources (RT).
‘Complex’ (C) sources form the largest category, which is unsurprising given we have found that the majority of ALMACAL sources
are blazars. In the right histograms of the same figure, we display
the distribution of rest-frame peak frequencies for peaked spectrum
sources in blue, and both the peak and trough frequencies for the retriggered sources in green (the trough being the frequency at which
the low-frequency upturn begins to dominate the spectrum). The
sample is clearly biased towards high-frequency peaked spectrum
sources which is consistent with the fact that the ALMACAL sam
ple represents the brightest mm-sources on the sky. We also include
an approximation of the linear source size on the secondary _𝑦_ -axis
using a scaling relation (Jeyakumar 2016). These highlight that the
majority of sources are compact, with sub-kpc linear sizes.


The 30 percent fraction of peaked spectrum sources in this sample is higher than in other samples with lower-frequency coverage
(O’Dea 1998; Callingham et al. 2017), and is surprising given the
large proportion of blazars this sample contains (typically PS and
blazar are considered mutually-exclusive categories, given blazars
are highly variable, while peaked spectrum sources are largely quiescent; O’Dea & Saikia 2021). Moreover, the peak frequencies are
higher, representing a subclass of peaked spectrum sources known as
high-frequency peaked (HFP) objects that peak at ≳ 5 GHz (O’Dea
1998; Dallacasa et al. 2000). While we expect a higher false detection
rate for peaks at higher frequencies near the edge of the measurement
range (Kerrison et al. 2024), HFP sources are still over-represented

500


400


300


200


100


0



0 1 2 3 4 5 6 7
Flag



**Figure 5.** Bar chart illustrating the number of sources associated with various
flag values. The _𝑥_ -axis represents the flag values, and the _𝑦_ -axis denotes the
number of sources. The flags represent specific criteria: (0) sources without a
spectrum or redshift measurement, (1) sources with a spectrum but no possible redshift estimate (excluding BL Lac objects), (2) sources with or without
a spectrum where a possible redshift is indicated by weak absorption or emission lines, (3) sources with a spectroscopic redshift reported in a published
paper but lacking a publicly available spectrum, or sources with a spectrum
showing a single strong absorption or emission feature, (4) sources with a
spectrum showing multiple strong absorption or emission features, (6) active
nuclei of galaxies such as M87 at redshift _𝑧_ ≪ 0 _._ 01, and (7) BL Lac objects.
A total of 687 objects have flag values of 3 or 4, indicating that approximately
65 per cent of the sample possesses reliable redshift measurements.


in this sample. The potential science with this selection of sources
will be discussed in the forthcoming section.


**5** **DISCUSSION**


In this section, we discuss ongoing science cases that are being
pursued using the ALMACAL survey. The unique combination of
high-sensitivity ALMA observations and multi-wavelength coverage
enables a range of investigations into how galaxies form and evolve.
We focus on two key topics: the properties of radio-loud active galactic nuclei and the presence of cold molecular gas in the circumgalactic
medium.


**5.1** **A unique population of radio-loud AGN**


Peaked spectrum sources are often associated with young active
galactic nuclei with compact radio emission (O’Dea 1998; Callingham et al. 2017; O’Dea & Saikia 2021). The ALMACAL sample
consists of the brightest mm-sources on the sky and, hence, is a particularly interesting sample for studying radio-loud AGN with recent jet
activity. Typically, these sources are considered distinct from blazars,
which exhibit compact radio emission due to the alignment of the jet
axis and the line of sight (Massaro et al. 2011). So the high fraction
of both blazars and sources with a peaked SED in ALMACAL−22



_ALMACAL XIV_ 7


makes it a useful sample for exploring the multiwavelength properties of each type of object. Multi-epoch, multi-band radio monitoring
of these sources in the manner of Ross et al. (2022) would allow for
a deeper understanding of their radio continuum properties, confirming the peaks identified here from inhomogeneous radio data,
and potentially providing insights into the intersection between these
two classes of AGN. In addition, re-triggered sources may provide
insights into the timescales at which radio jets switch on and off,
placing an upper limit on the AGN duty cycle, or into the environments responsible for these multiple epochs of activity (Hogan et al.
2015). Estimating an age from the SED requires a spectral break
above the peak frequency (see Allison et al. 2019, for an example),
which, after visual inspection for all sources, is not evident in this
sample. An alternative is to track sources using imaging to obtain
a dynamical age. This is more feasible for the ALMACAL sample,
given that many sources have VLBI observations spanning more
than 20 epochs (Petrov & Kovalev 2025). The broad range of redshifts (0 _<_ _𝑧<_ 4) also allows for studying jet ages and duty cycles
across cosmic time.

Moreover, serendipitous CO emission, consistent with the calibrator redshift, has been detected in the ALMACAL fields (Bollo
et al. 2025). This presents a unique opportunity to study the impact
of radio jets on molecular gas reservoirs in AGN and investigate
potential jet-induced outflows. In cases where galaxies at the calibrator redshift have been detected, analyzing their environment could
offer insights into the mechanisms that may have re-triggered AGN
activity. The mechanisms driving AGN activation remain uncertain
(Fabian 2012; Harrison & Ramos Almeida 2024), but further analysis
of the ALMACAL sample may yield valuable insights.


**5.2** **Probing the molecular gas content of the CGM**


Theoretical and observational studies increasingly suggest that cold
molecular gas can persist in the hot environment of the circumgalactic medium (Ginolfi et al. 2017; Cicone et al. 2021). Recent
simulations indicate that sufficiently large molecular clouds in a hot
medium ( _𝑇>_ 10 [5] K) can “splinter” into a mist of cold droplets
that survive (Farber & Gronke 2023). 21-cm observations of highvelocity clouds (HVCs) in the Milky Way reveal a cold neutral gas
component (Kalberla & Haud 2006; Moss et al. 2013; Westmeier
2018) and molecular gas has also been detected through the H 2 line
at UV wavelengths (Richter et al. 1999, 2001; Sembach et al. 2001;
Putman et al. 2012, for a review). The cold phase has also been found
entrained within the nuclear wind of the Milky Way (Di Teodoro
et al. 2020; Cashman et al. 2021). While individual extragalactic absorbers have been detected (Noterdaeme et al. 2017; Balashev et al.
2019; Klitsch et al. 2021), absorption-line stacking experiments suggest a scarcity of dust in the CGM, implying a lack of molecular gas
(Ménard et al. 2010; Zhu & Ménard 2013).
In a previous experiment, Klitsch et al. (2023) placed constraints
on the molecular gas covering fraction of galaxies with a median
redshift of _𝑧_ ≈ 0 _._ 05. Using a sample of mm-bright quasars and
foreground galaxies, the absence of any CO absorption after stacking
rules out large, smooth molecular gas reservoirs like those seen at
_𝑧>_ 2 in extreme overdensities (Cicone et al. 2014, 2021; Emonts
et al. 2016) and around massive star-forming galaxies (Ginolfi et al.
2017). Specifically, the observations show that clouds with radii of
approximately 30 pc and column densities _𝑁_ (CO) ≳ 10 [16] cm [−][2]

must have volume-filling factors of less than 0.2 per cent. Instead of
stacking at the redshifts of foreground galaxies, one can stack CO
spectra at the redshifts corresponding to intervening metal absorption
lines such as Mg ii. Ongoing efforts are being made to search for


MNRAS **000**, 1–31 (2025)

8 _Simon Weng et al._


40


30


20


10





1 _._ 0


0 _._ 9


0 _._ 8


0 _._ 7


0 _._ 6


0 _._ 5


0 _._ 4



7 _._ 5 10 _._ 0 12 _._ 5 15 _._ 0 17 _._ 5
W1 [3.4 _µ_ m] Magnitude



0



0 0 _._ 5 1 2 3 4

Redshift



200


150


100


50


0



**Figure 6.** The left histogram shows the redshift distribution of ALMA calibrators. Sources with redshift confidence ≥ 2 are represented in blue, while sources
with high confidence (3 or 4) are shown in green. The distribution peaks at _𝑧_ ≈ 1, with the highest redshift source at _𝑧_ = 3 _._ 789. On the right, we display how
the fraction of successfully redshifted sources varies with their WISE [3.4 _𝜇_ m] magnitude. On the right, we display how the fraction of successfully redshifted
sources varies with their WISE [3.4 _𝜇_ m] magnitude. Sources with a measured W1 magnitude are shown in pink, and the subsample with a confident redshift
is shown in orange. The navy blue line represents the fraction of sources with confident redshifts in each WISE magnitude bin, and we include this fraction
only for bins with more than 50 sources to minimise the variance associated with small sample sizes. We find evidence that the fraction increases (between W1
= 12 _._ 5 to 15 mag) or plateaus (after accounting for errors) as sources become fainter, which would be consistent with the observation that a significant portion
of the ALMACAL sample consists of blazars.



intervening absorbers in the X-Shooter spectra, as well as in publicly
available SDSS (York et al. 2000; Anand et al. 2021; Fresco et al.
2024) and DESI (DESI Collaboration et al. 2025; Napolitano et al.
2023) spectra, to generate a sample of over 100 absorbers that can
then be used to stack CO spectra. With future QSO surveys such as
4MOST ByCycle at resolution _𝑅_ = 20 _,_ 000, the velocity precision of
the stacking will further improve (Peroux et al. 2023).


**6** **CONCLUSIONS**


The ALMACAL sample is a continuously evolving data set with
numerous applications in the field of galaxy evolution and formation.
We present and release the catalogue of 1,047 calibrators observed
up until May 2022, with updated, visually inspected redshifts. Our
major results are summarised below:


- Approximately 65 per cent of the sample have reliable redshift
measurements, and an additional 50 objects are spectroscopically
confirmed featureless BL Lac objects. We also present 70 X-Shooter
observations of calibrator sources for the first time. More calibrators

will be observed in ongoing and future surveys of QSOs (Pieri et al.
2016; DESI Collaboration et al. 2016; Peroux et al. 2023).

- The ALMACAL-22 sample has a redshift distribution that peaks
at _𝑧_ ≈ 1 and ranges from the nuclei of galaxies at _𝑧_ ≪ 0 _._ 01, such
as M87, to quasars at _𝑧_ = 3 _._ 742. The fraction of sources with highconfidence redshifts increases or plateaus as sources become fainter
in the WISE W1 band, between magnitudes 13 and 15 (Figure 6).
This suggests that a significant fraction of the ALMACAL sources


MNRAS **000**, 1–31 (2025)



are blazars, a result confirmed by plotting their positions on the WISE
colour-colour plot (Figure 7).

- Analysing the radio spectral energy distributions of 897 ALMA calibrators reveals that roughly 30 per cent of the objects have peaked
spectra, with another third being re-triggered. The fraction of sources
with peaked spectra is higher than in other samples based on lowerfrequency data (O’Dea 1998; Callingham et al. 2017), which is unexpected given the large number of blazars in this sample. Sources with
complex SEDs, largely caused by variability, comprise 36 per cent
of the fitted calibrators, while only two per cent are consistent with a
power-law spectrum. The peak frequencies of the peaked spectrum
and re-triggered sources span three orders of magnitude, between
100 MHz and 170 GHz, with estimated linear sizes ranging from
sub-pc to _>_ 10 kpc scales.


The number of ALMA calibrator observations will only grow
with time, meaning that more calibrators will be observed, at greater
depths, or across more bands. Establishing a reliable redshift catalogue is necessary for the many scientific cases possible with this
data. For example, the search for dusty star-forming galaxies (Chen
et al. 2023b) and CO emitters (Bollo et al. 2025) requires an estimation of the clustering bias introduced when searching around a
calibrator source. Hence, understanding the properties of the calibrator itself is crucial for controlling this bias.
Moreover, the calibrators themselves are key in a variety of scientific cases that will be explored in the future. In an upcoming paper,
we will stack CO spectra for the elusive cold gas seen in the circumgalactic medium at the redshift of metal absorption lines in the
optical spectra of calibrators. Furthermore, combining radio spectral

2 _._ 5


2 _._ 0


1 _._ 5


1 _._ 0


0 _._ 5


0 _._ 0







1 2 3 4 5 6

[4.6]                    - [12] _µ_ m


**Figure** **7.** The positions of the ALMACAL sources are shown with black
contours and black diamonds, reflecting outliers, on a reconstructed WISE
colour-colour plot (Wright et al. 2010). The orange dashed line indicates the
position of blazars, which are dominated by non-thermal emission (Massaro
et al. 2011). The inner contour encloses approximately 10 per cent of the
sources, with each successive contour increasing the number of enclosed
calibrators by an additional 10 per cent. According to the WISE classifications,
the majority of ALMACAL sources are quasars and blazars, aligning with
previous findings (Bonato et al. 2018).


energy distributions with imaging of the calibrator sources may yield
unconstrained properties, such as the AGN age and their duty cycle.
The ALMACAL data set will be a continually valuable resource for
the study of how galaxies form and evolve.


**ACKNOWLEDGEMENTS**


We thank the anonymous referee for providing insightful comments.
This research is supported by an Australian Government Research
Training Program (RTP) Scholarship. EK, EMS and SW acknowledge the financial support of the Australian Research Council through
grant CE170100013 (ASTRO3D). This research was supported by
the International Space Science Institute (ISSI) in Bern, through
ISSI International Team project #564 (The Cosmic Baryon Cycle
from Space).
This research has made use of the NASA/IPAC Extragalactic
Database (NED), which is funded by the National Aeronautics and
Space Administration and operated by the California Institute of
Technology, and the SIMBAD database, operated at CDS, Strasbourg, France. The scientific colour map batlow (Crameri 2018) is
used in this study to prevent visual distortion of the data and exclusion
of readers with colour-vision deficiencies (Crameri et al. 2020).


**DATA AVAILABILITY**


The ALMACAL catalogue with redshift data is available online and
the reduced X-Shooter spectra can be found in the appendix. Based on



_ALMACAL XIV_ 9


observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programmes
0101.A-0528 and 111.253L.001. All other data is available upon
request to the corresponding author.


**REFERENCES**


[Allison J. R., et al., 2019, MNRAS, 482, 2934](http://dx.doi.org/10.1093/mnras/sty2852)

[Anand A., Nelson D., Kauffmann G., 2021, MNRAS, 504, 65](http://dx.doi.org/10.1093/mnras/stab871)

[Balashev S. A., et al., 2019, MNRAS, 490, 2668](http://dx.doi.org/10.1093/mnras/stz2707)

[Bertaux J. L., Lallement R., Ferron S., Boonne C., Bodichon R., 2014, A&A,](http://dx.doi.org/10.1051/0004-6361/201322383)


[564, A46](https://ui.adsabs.harvard.edu/abs/2014A&A...564A..46B)
Bollo V., Zwaan M., Péroux C., Hamanowicz A., Chen J., Weng S., Ivison
[R. J., Biggs A., 2024, A&A, 690, A258](http://dx.doi.org/10.1051/0004-6361/202450336)
[Bollo V., et al., 2025, arXiv e-prints, p. arXiv:2502.06778](https://ui.adsabs.harvard.edu/abs/2025arXiv250206778B)
[Bonato M., et al., 2018, MNRAS, 478, 1512](http://dx.doi.org/10.1093/mnras/sty1173)
[Callingham J. R., et al., 2017, ApJ, 836, 174](http://dx.doi.org/10.3847/1538-4357/836/2/174)
[Cashman F. H., et al., 2021, ApJ, 923, L11](http://dx.doi.org/10.3847/2041-8213/ac3cbc)
[Chen J., et al., 2023a, MNRAS, 518, 1378](http://dx.doi.org/10.1093/mnras/stac2989)

[Chen J., et al., 2023b, A&A, 675, L10](http://dx.doi.org/10.1051/0004-6361/202347107)
[Cicone C., et al., 2014, Astronomy & Astrophysics, 562, A21](http://dx.doi.org/10.1051/0004-6361/201322464)
[Cicone C., et al., 2021, Astronomy & Astrophysics, 654, L8](http://dx.doi.org/10.1051/0004-6361/202141611)
[Colless M., et al., 2001, MNRAS, 328, 1039](http://dx.doi.org/10.1046/j.1365-8711.2001.04902.x)
[Crameri F., 2018, Scientific colour maps, doi:10.5281/zenodo.2649252](http://dx.doi.org/10.5281/zenodo.2649252)
[Crameri F., Shephard G. E., Heron P. J., 2020, Nature Communications, 11,](http://dx.doi.org/10.1038/s41467-020-19160-7)
[5444](https://ui.adsabs.harvard.edu/abs/2020NatCo..11.5444C)

[DESI Collaboration et al., 2016, arXiv e-prints, p. arXiv:1611.00036](http://dx.doi.org/10.48550/arXiv.1611.00036)
[DESI Collaboration et al., 2025, arXiv e-prints, p. arXiv:2503.14745](http://dx.doi.org/10.48550/arXiv.2503.14745)
[Dallacasa D., Stanghellini C., Centonza M., Fanti R., 2000, A&A, 363, 887](http://dx.doi.org/10.48550/arXiv.astro-ph/0012428)
Di Teodoro E. M., McClure-Griffiths N. M., Lockman F. J., Armillotta L.,

[2020, Nature, 584, 364](http://dx.doi.org/10.1038/s41586-020-2595-z)

[Drinkwater M. J., et al., 1997, MNRAS, 284, 85](http://dx.doi.org/10.1093/mnras/284.1.85)

[Emonts B. H. C., et al., 2016, Science, 354, 1128](http://dx.doi.org/10.1126/science.aag0512)
[Event Horizon Telescope Collaboration et al., 2019, ApJ, 875, L6](http://dx.doi.org/10.3847/2041-8213/ab1141)
[Fabian A. C., 2012, ARA&A, 50, 455](http://dx.doi.org/10.1146/annurev-astro-081811-125521)

[Farber R. J., Gronke M., 2023, MNRAS, 525, 1839](http://dx.doi.org/10.1093/mnras/stad2373)
Fresco A., Péroux C., Merloni A., Comparat J., Szakacs R., Weng S., 2024,

[A&A, 684, A136](http://dx.doi.org/10.1051/0004-6361/202346866)
Freudling W., Romaniello M., Bramich D. M., Ballester P., Forchi V., García[Dabló C. E., Moehler S., Neeser M. J., 2013, A&A, 559, A96](http://dx.doi.org/10.1051/0004-6361/201322494)

[Ginolfi M., et al., 2017, MNRAS, 468, 3468](http://dx.doi.org/10.1093/mnras/stx712)
[Ginsburg A., et al., 2019, AJ, 157, 98](http://dx.doi.org/10.3847/1538-3881/aafc33)
[Hale C. L., et al., 2021, Publ. Astron. Soc. Australia, 38, e058](http://dx.doi.org/10.1017/pasa.2021.47)

[Hamanowicz A., et al., 2023, MNRAS, 519, 34](http://dx.doi.org/10.1093/mnras/stac3159)

[Harrison C. M., Ramos Almeida C., 2024, Galaxies, 12, 17](http://dx.doi.org/10.3390/galaxies12020017)
[Hewitt A., Burbidge G., 1987, ApJS, 63, 1](http://dx.doi.org/10.1086/191163)
Hinton S. R., Davis T. M., Lidman C., Glazebrook K., Lewis G. F., 2016,

[Astronomy and Computing, 15, 61](http://dx.doi.org/10.1016/j.ascom.2016.03.001)
[Hogan M. T., et al., 2015, Monthly Notices of the Royal Astronomical Society,](http://dx.doi.org/10.1093/mnras/stv1518)
453, 1223

Hook I. M., Shaver P. A., Jackson C. A., Wall J. V., Kellermann K. I., 2003,


[A&A, 399, 469](http://dx.doi.org/10.1051/0004-6361:20021803)
[Ivezić Ž., et al., 2019, ApJ, 873, 111](http://dx.doi.org/10.3847/1538-4357/ab042c)
[Jeyakumar S., 2016, MNRAS, 458, 3786](http://dx.doi.org/10.1093/mnras/stw181)
[Jones D. H., et al., 2004, MNRAS, 355, 747](http://dx.doi.org/10.1111/j.1365-2966.2004.08353.x)

[Jones D. H., et al., 2009, MNRAS, 399, 683](http://dx.doi.org/10.1111/j.1365-2966.2009.15338.x)

[Kalberla P. M. W., Haud U., 2006, A&A, 455, 481](http://dx.doi.org/10.1051/0004-6361:20054750)

Kerrison E. F., Allison J. R., Moss V. A., Sadler E. M., Rees G. A., 2024,


[MNRAS, 533, 4248](http://dx.doi.org/10.1093/mnras/stae1796)
Klitsch A., Péroux C., Zwaan M. A., Smail I., Oteo I., Biggs A. D., Popping
[G., Swinbank A. M., 2018, MNRAS, 475, 492](http://dx.doi.org/10.1093/mnras/stx3184)

[Klitsch A., et al., 2019a, MNRAS, 482, L65](http://dx.doi.org/10.1093/mnrasl/sly187)

[Klitsch A., et al., 2019b, MNRAS, 490, 1220](http://dx.doi.org/10.1093/mnras/stz2660)

[Klitsch A., et al., 2020, MNRAS, 495, 2332](http://dx.doi.org/10.1093/mnras/staa1315)
Klitsch A., Péroux C., Zwaan M. A., De Cia A., Ledoux C., Lopez S., 2021,

[MNRAS, 506, 514](http://dx.doi.org/10.1093/mnras/stab1668)


MNRAS **000**, 1–31 (2025)

10 _Simon Weng et al._


**Figure** **8.** Example spectral energy distributions and the four analytic models fitted (power law, simple peaked spectrum, curved peaked spectrum and a
re-triggered source). A final source is included which has been labelled as ‘complex’ because the fit is unreliable due to variability.



Linear Size [kpc]
2.95e+01 8.49e-01 2.44e-02 7.02e-04 2.02e-05


40


30


20


10



300


250


200


150


100


50


0



PL PS RT C
Classification



Linear Size [kpc]
2.95e+01 8.49e-01 2.44e-02 7.02e-04 2.02e-05


30


25


20


15


10


5



10 [2] 10 [3] 10 [4] 10 [5]
Rest-frame Peak Frequency [MHz]



10 [2] 10 [3] 10 [4] 10 [5]
Rest-frame Peak/Trough Frequency [MHz]



0



0



**Figure 9.** The distribution of radio spectral energy distribution classifications for 897 sources is shown in the left histogram. The categories include power law
(PL), peaked spectrum (PS), re-triggered (RT), and complex (C) SEDs. For the peaked spectrum sources, we display their rest-frame peak frequencies, which
approximately correspond to the linear sizes shown on the secondary _𝑦_ -axis (derived using the scaling relation from Jeyakumar (2016)). We repeat this for
re-triggered sources in green, showing both the peak and trough frequencies in darker and lighter shades, respectively.



Klitsch A., Davis T. A., Hamanowicz A., van de Voort F., Péroux C., Zwaan

[M. A., 2023, MNRAS, 523, L46](http://dx.doi.org/10.1093/mnrasl/slad053)
[Mahony E. K., et al., 2011, MNRAS, 417, 2651](http://dx.doi.org/10.1111/j.1365-2966.2011.19427.x)
Massaro E., Giommi P., Leto C., Marchegiani P., Maselli A., Perri M., Pira[nomonte S., Sclavi S., 2009, A&A, 495, 691](http://dx.doi.org/10.1051/0004-6361:200810161)
[Massaro F., D’Abrusco R., Ajello M., Grindlay J. E., Smith H. A., 2011, ApJ,](http://dx.doi.org/10.1088/2041-8205/740/2/L48)

[740, L48](https://ui.adsabs.harvard.edu/abs/2011ApJ...740L..48M)
Massaro F., D’Abrusco R., Tosti G., Ajello M., Gasparrini D., Grindlay J. E.,
[Smith H. A., 2012, ApJ, 750, 138](http://dx.doi.org/10.1088/0004-637X/750/2/138)
[Ménard B., Scranton R., Fukugita M., Richards G., 2010, MNRAS, 405, 1025](http://dx.doi.org/10.1111/j.1365-2966.2010.16486.x)
Modigliani A., et al., 2010, in Silva D. R., Peck A. B., Soifer B. T., eds,
Society of Photo-Optical Instrumentation Engineers (SPIE) Conference
Series Vol. 7737, Observatory Operations: Strategies, Processes, and
[Systems III. p. 773728, doi:10.1117/12.857211](http://dx.doi.org/10.1117/12.857211)
Moss V. A., McClure-Griffiths N. M., Murphy T., Pisano D. J., Kummerfeld
[J. K., Curran J. R., 2013, ApJS, 209, 12](http://dx.doi.org/10.1088/0067-0049/209/1/12)


MNRAS **000**, 1–31 (2025)



[Murphy T., et al., 2010, MNRAS, 402, 2403](http://dx.doi.org/10.1111/j.1365-2966.2009.15961.x)
[Napolitano L., et al., 2023, AJ, 166, 99](http://dx.doi.org/10.3847/1538-3881/ace62c)
[Noterdaeme P., et al., 2017, A&A, 597, A82](http://dx.doi.org/10.1051/0004-6361/201629173)

[O’Dea C. P., 1998, PASP, 110, 493](http://dx.doi.org/10.1086/316162)

[O’Dea C. P., Saikia D. J., 2021, A&ARv, 29, 3](http://dx.doi.org/10.1007/s00159-021-00131-w)
[Orienti M., Dallacasa D., Stanghellini C., 2007, A&A, 475, 813](http://dx.doi.org/10.1051/0004-6361:20078105)
[Oteo I., Zwaan M. A., Ivison R. J., Smail I., Biggs A. D., 2016, ApJ, 822, 36](http://dx.doi.org/10.3847/0004-637X/822/1/36)
Oteo I., Zwaan M. A., Ivison R. J., Smail I., Biggs A. D., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa5da4) [837,](https://ui.adsabs.harvard.edu/abs/2017ApJ...837..182O)

[182](https://ui.adsabs.harvard.edu/abs/2017ApJ...837..182O)

[Peroux C., et al., 2023, The Messenger, 190, 42](http://dx.doi.org/10.18727/0722-6691/5311)
[Petrov L. Y., Kovalev Y. Y., 2025, ApJS, 276, 38](http://dx.doi.org/10.3847/1538-4365/ad8c36)
Pieri M. M., et al., 2016, in Reylé C., Richard J., Cambrésy L., Deleuil M.,
Pécontal E., Tresse L., Vauglin I., eds, SF2A-2016: Proceedings of the
Annual meeting of the French Society of Astronomy and Astrophysics.
pp 259–266 ( `[arXiv:1611.09388](http://arxiv.org/abs/1611.09388)` [), doi:10.48550/arXiv.1611.09388](http://dx.doi.org/10.48550/arXiv.1611.09388)
[Putman M. E., Peek J. E. G., Joung M. R., 2012, ARA&A, 50, 491](http://dx.doi.org/10.1146/annurev-astro-081811-125612)

Richter P., de Boer K. S., Widmann H., Kappelmann N., Gringel W., Grewing
[M., Barnstedt J., 1999, Nature, 402, 386](http://dx.doi.org/10.1038/46492)
[Richter P., Sembach K. R., Wakker B. P., Savage B. D., 2001, ApJ, 562, L181](http://dx.doi.org/10.1086/338050)
Ross K., Hurley-Walker N., Seymour N., Callingham J. R., Galvin T. J.,
[Johnston-Hollitt M., 2022, MNRAS, 512, 5358](http://dx.doi.org/10.1093/mnras/stac819)
[Sembach K. R., Howk J. C., Savage B. D., Shull J. M., 2001, AJ, 121, 992](http://dx.doi.org/10.1086/318777)
[Shaw M. S., et al., 2013, ApJ, 764, 135](http://dx.doi.org/10.1088/0004-637X/764/2/135)
Snellen I. A. G., Schilizzi R. T., de Bruyn A. G., Miley G. K., Rengelink
[R. B., Roettgering H. J., Bremer M. N., 1998, A&AS, 131, 435](http://dx.doi.org/10.1051/aas:1998281)
Titov O., Stanford L. M., Johnston H. M., Pursimo T., Hunstead R. W., Jauncey
[D. L., Maslennikov K., Boldycheva A., 2013, AJ, 146, 10](http://dx.doi.org/10.1088/0004-6256/146/1/10)
[Vernet J., et al., 2011, A&A, 536, A105](http://dx.doi.org/10.1051/0004-6361/201117752)

[Westmeier T., 2018, MNRAS, 474, 289](http://dx.doi.org/10.1093/mnras/stx2757)
[Wright E. L., et al., 2010, AJ, 140, 1868](http://dx.doi.org/10.1088/0004-6256/140/6/1868)
[York D. G., et al., 2000, AJ, 120, 1579](http://dx.doi.org/10.1086/301513)
[Zhu G., Ménard B., 2013, ApJ, 773, 16](http://dx.doi.org/10.1088/0004-637X/773/1/16)
[Zwaan M., et al., 2022, The Messenger, 186, 10](http://dx.doi.org/10.18727/0722-6691/5256)


**APPENDIX A:** **X-SHOOTER SPECTRA**


In this section, we present the remaining 68 out of 70 total X-Shooter
spectra from programmes 0101.A-0528 and 111.253L.001. Each
spectrum has common quasar and galaxy emission lines marked
along with the redshift. The SNR ranges from 1 to over 100.



_ALMACAL XIV_ 11


MNRAS **000**, 1–31 (2025)

12 _Simon Weng et al._





5 _._ 0


2 _._ 5





0 _._ 0



2





0



1 _._ 0


0 _._ 5


0 _._ 0


4


2





**Figure A1.** 41 X-Shooter spectra from programme 0101.A-0528.











0





2





0





1


0


MNRAS **000**, 1–31 (2025)





**Figure A1.**

_ALMACAL XIV_ 13





2


1







0





1





0



1


0


5 _._ 0


2 _._ 5









**Figure A1.**







0 _._ 0





4


2





0



4


2


0







**Figure A1.**



MNRAS **000**, 1–31 (2025)

14 _Simon Weng et al._





5





0







2



0



5


0


4


2







**Figure A1.**







0





2


1





0







1


0


MNRAS **000**, 1–31 (2025)



**Figure A1.**

_ALMACAL XIV_ 15





1 _._ 0


0 _._ 5







0 _._ 0





5





0





500


0


2







**Figure A1.**







0



4


2







0



2


0





**Figure A1.**



MNRAS **000**, 1–31 (2025)

16 _Simon Weng et al._


1







0







1



0





1


0


2





Observed _λ_ [ [˚] A]


**Figure A1.**





0







2



0

_×_ 10 _[−]_ [16] 6000 7000 8000 9000 10000



2


1


0


MNRAS **000**, 1–31 (2025)





Observed _λ_ [ [˚] A]


**Figure A1.**

_ALMACAL XIV_ 17







1 _._ 0


0 _._ 5





0 _._ 0





5



0





5 _._ 0


2 _._ 5


0 _._ 0



**Figure A1.**







1





0



1 _._ 0


0 _._ 5





0 _._ 0



4


2


0









**Figure A1.**



MNRAS **000**, 1–31 (2025)

18 _Simon Weng et al._


_×_ 10 _[−]_ [16]


1





0



1 _._ 0


0 _._ 5





0 _._ 0



1 _._ 0


0 _._ 5


0 _._ 0


_×_ 10 _[−]_ [16]


4


2



**Figure A1.**





0



2


1





0



5 _._ 0


2 _._ 5


0 _._ 0


MNRAS **000**, 1–31 (2025)





**Figure A1.**

_ALMACAL XIV_ 19



2





0





1



0





4


2


0


5 _._ 0


2 _._ 5









**Figure A1.**





0 _._ 0





2



0



2


1


0



**Figure A1.**


MNRAS **000**, 1–31 (2025)

20 _Simon Weng et al._



2


1







0



1





0



4


2


0


1









**Figure A1.**





0





5



0





2


0


MNRAS **000**, 1–31 (2025)



**Figure A1.**

_ALMACAL XIV_ 21







5 _._ 0


2 _._ 5







0 _._ 0



4


2







0



2


1


0


1











**Figure A1.**







0



2


1







0







1


0





**Figure A1.**



MNRAS **000**, 1–31 (2025)

22 _Simon Weng et al._


5 _._ 0





2 _._ 5







0 _._ 0





4


2





0







2


0


1 _._ 0


0 _._ 5





**Figure A1.**









0 _._ 0





5



0



2


0


MNRAS **000**, 1–31 (2025)







**Figure A1.**

_ALMACAL XIV_ 23





4


2









0







1



0



2


1


0


5







**Figure A1.**





0





5



0







5


0



**Figure A1.**



MNRAS **000**, 1–31 (2025)

24 _Simon Weng et al._


2





0





1



0



1 _._ 0


0 _._ 5


0 _._ 0





**Figure A1.**





5





0



5 _._ 0


2 _._ 5





0 _._ 0



4


2


0


MNRAS **000**, 1–31 (2025)









**Figure A1.**

_ALMACAL XIV_ 25





5





0



1 _._ 0


0 _._ 5





0 _._ 0



5


0





**Figure A1.**



1 _._ 0


0 _._ 5





0 _._ 0





2



0





1


0





**Figure A1.**



MNRAS **000**, 1–31 (2025)

26 _Simon Weng et al._


4


2





0





1





0



1 _._ 0


0 _._ 5


0 _._ 0


5







**Figure A1.**



_×_ 10 _[−]_ [15]





0

_×_ 10 _[−]_ [15] 3500 4000 4500 5000 5500

4





2



0

_×_ 10 _[−]_ [15] 6000 7000 8000 9000 10000





1


0


MNRAS **000**, 1–31 (2025)



12000 14000 16000 18000 20000 22000 24000
Observed _λ_ [ [˚] A]


**Figure A1.**

_ALMACAL XIV_ 27



2





0



1 _._ 0


0 _._ 5





0 _._ 0





4


2


0





**Figure A1.**



2


1





0


2





1



0



2


1


0





**Figure A1.**


MNRAS **000**, 1–31 (2025)

28 _Simon Weng et al._


4


2







0



4


2







0



4


2


0







_×_ 10 _[−]_ [15]



**Figure A1.**



1





0

_×_ 10 _[−]_ [15] 3500 4000 4500 5000 5500



1 _._ 0


0 _._ 5







0 _._ 0



2


1


0


MNRAS **000**, 1–31 (2025)



**Figure A1.**

_ALMACAL XIV_ 29





4


2





0



2


1





0





2


1


0


5





**Figure A1.**



_×_ 10 _[−]_ [16]





0



4


2





0



2


1


0





**Figure A1.**



MNRAS **000**, 1–31 (2025)

30 _Simon Weng et al._





1 _._ 0


0 _._ 5





0 _._ 0







5



0





2


0


4


2





_×_ 10 _[−]_ [16]



**Figure A1.**





0



4


2







0

_×_ 10 _[−]_ [16] 6000 7000 8000 9000 10000





2


0


MNRAS **000**, 1–31 (2025)



12000 14000 16000 18000 20000 22000 24000
Observed _λ_ [ [˚] A]


**Figure A1.**

This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



_ALMACAL XIV_ 31


MNRAS **000**, 1–31 (2025)

32 _Simon Weng et al._


1 _._ 0


0 _._ 5





0 _._ 0





5



0



4


2


0



**Figure A2.** 29 X-Shooter spectra from programme 111.253L.001





5





0



5 _._ 0


2 _._ 5





0 _._ 0



4


2


0


MNRAS **000**, 1–31 (2025)



**Figure A2.**

_ALMACAL XIV_ 33







4


2







0







1



0





4


2


0


1 _._ 0


0 _._ 5









**Figure A2.**





0 _._ 0





5



0



5 _._ 0


2 _._ 5


0 _._ 0





**Figure A2.**



MNRAS **000**, 1–31 (2025)

34 _Simon Weng et al._


2





0





1



0





1


0


5







**Figure A2.**





0





5



0



4


2


0


MNRAS **000**, 1–31 (2025)





**Figure A2.**

_ALMACAL XIV_ 35



_×_ 10 _[−]_ [16]





1





0







1



0

_×_ 10 _[−]_ [16] 6000 7000 8000 9000 10000



1 _._ 0


0 _._ 5


0 _._ 0


2







**Figure A2.**







0





2



0







2


0





**Figure A2.**



MNRAS **000**, 1–31 (2025)

36 _Simon Weng et al._


1





0





1



0



2


1


0


2









**Figure A2.**



_×_ 10 _[−]_ [16]





0

_×_ 10 _[−]_ [16] 3500 4000 4500 5000 5500





2



0



2


1


0


MNRAS **000**, 1–31 (2025)





**Figure A2.**

_ALMACAL XIV_ 37



5 _._ 0


2 _._ 5



0 _._ 0





5 _._ 0


2 _._ 5





0 _._ 0





4


2


0


5



**Figure A2.**









0





5 _._ 0


2 _._ 5





0 _._ 0





4


2


0



**Figure A2.**


MNRAS **000**, 1–31 (2025)

38 _Simon Weng et al._


4


2









0



2


1







0



1


0


5







**Figure A2.**



_×_ 10 _[−]_ [17]





0





5



0



5 _._ 0


2 _._ 5


0 _._ 0


MNRAS **000**, 1–31 (2025)





**Figure A2.**

_ALMACAL XIV_ 39





2


1





0





2



0



4


2


0









**Figure A2.**





1





0



1 _._ 0


0 _._ 5





0 _._ 0





5


0



12000 14000 16000 18000 20000 22000 24000
Observed _λ_ [ [˚] A]


**Figure A2.**


MNRAS **000**, 1–31 (2025)

40 _Simon Weng et al._



1 _._ 0


0 _._ 5




[˚]





0 _._ 0







1



0





1 _._ 0


0 _._ 5


0 _._ 0


5 _._ 0


2 _._ 5





Observed _λ_ [ [˚] A]


**Figure A2.**









0 _._ 0





5 _._ 0


2 _._ 5





0 _._ 0



5 _._ 0





2 _._ 5


0 _._ 0


MNRAS **000**, 1–31 (2025)





**Figure A2.**

_ALMACAL XIV_ 41





5 _._ 0


2 _._ 5





0 _._ 0



5 _._ 0


2 _._ 5





0 _._ 0



4


2


0


_×_ 10 _[−]_ [17]



**Figure A2.**



5





0







5



0





2


0





**Figure A2.**



MNRAS **000**, 1–31 (2025)

42 _Simon Weng et al._


_×_ 10 _[−]_ [16]

2


1







0



2


1





0



1


0


2







**Figure A2.**





0





2



0



2


1


0


MNRAS **000**, 1–31 (2025)





**Figure A2.**

_ALMACAL XIV_ 43





2


1





0



2





0





2


1


0


5 _._ 0


2 _._ 5









**Figure A2.**











0 _._ 0







2





0



2


1


0









**Figure A2.**



MNRAS **000**, 1–31 (2025)

44 _Simon Weng et al._


2


1







0





1



0







1


0


5





**Figure A2.**









0



4


2







0





5







0


MNRAS **000**, 1–31 (2025)





**Figure A2.**

_ALMACAL XIV_ 45



_×_ 10 _[−]_ [17]





5





0



2


1





0





1


0


1



**Figure A2.**









0







5



0





5


0





**Figure A2.**



MNRAS **000**, 1–31 (2025)

46 _Simon Weng et al._


5









0





5 _._ 0


2 _._ 5





0 _._ 0





4


2


0


MNRAS **000**, 1–31 (2025)







**Figure A2.**


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "WISE colour-colour classification regions and WISE blazar strip",
  "failed_quote": "Blazars have been found to delineate a specific region of the WISE colour-colour diagram, known as the WISE blazar strip (Massaro et al. 2011, 2012), which corresponds to the green dashed line in Figure 7."
 },
 {
  "path": "results_numeric[5].evidence[1]",
  "value": "Number of calibrators with reliable spectroscopic redshifts (confidence flags 3 or 4) = 687 dimensionless",
  "failed_quote": "687 objects are assigned flag values of 3 or 4, signifying that ≈65 per cent of the sample have reliable redshift measurements."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "Most ALMACAL sources fall within the QSO and Seyfert loci of the WISE colour-colour diagram and align with the WISE blazar strip, confirming they are predominantly quasars and blazars.",
  "failed_quote": "However, the alignment of the contours with the gradient of the blazar strip suggests that the ALMACAL−22 sample is predominantly composed of blazars."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The infrared properties and redshift completeness trends independently confirm that ALMACAL-22 calibrators are predominantly quasars and blazars.",
  "failed_quote": "However, the alignment of the contours with the gradient of the blazar strip suggests that the ALMACAL−22 sample is predominantly composed of blazars."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[1]",
  "value": "Multi-epoch radio survey data span more than 20 epochs, so source variability causes poor SED fits (36% 'complex' class), and peaks near the upper edge of the frequency coverage have a higher false detection rate.",
  "failed_quote": "While we expect a higher false detection rate for peaks at higher frequencies near the edge of the measurement range (Kerrison et al. 2024), HFP sources are still over-represented in this sample."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[1]",
  "value": "The ALMACAL redshift catalogue is publicly available on GitHub and VizieR; reduced X-Shooter spectra are shown in the appendix; raw X-Shooter data are in the ESO archive under programmes 0101.A-0528 and 111.253L.001; other data available upon request.",
  "failed_quote": "The ALMACAL catalogue with redshift data is available online and the reduced X-Shooter spectra can be found in the appendix. Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programmes 0101.A-0528 and 111.253L.001. All other data is available upon request to the corresponding author."
 }
]
```
