# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.537..520Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–17 (2024) Preprint 14 January 2025 Compiled using MNRAS L [A] TEX style file v3.0

## WISDOM Project – XXII. A 5% precision CO-dynamical supermassive **black hole mass measurement in the galaxy NGC 383**


Hengyue Zhang, [1] _[★]_ Martin Bureau, [1] - Ilaria Ruffa, [2] _[,]_ [3] _[,]_ [6] Michele Cappellari, [1] Timothy A. Davis, [2]

Pandora Dominiak, [1] Jacob S. Elford, [2] Satoru Iguchi, [4] _[,]_ [5] Federico Lelli, [6] Marc Sarzi, [7] Thomas G. Williams [1]

1 _Sub-department of Astrophysics, Department of Physics, University of Oxford, Denys Wilkinson Building, Keble Road, Oxford, OX1 3RH, UK_
2 _School of Physics & Astronomy, Cardiff University, Queens Buildings, The Parade, Cardiff, CF24 3AA, UK_
3 _INAF - Istituto di Radioastronomia, via P. Gobetti 101, 40129 Bologna, Italy_
4 _Graduate Institute for Advanced Studies, SOKENDAI, Mitaka, Tokyo 181-8588, Japan_
5 _National Astronomical Observatory of Japan, National Institutes of Natural Sciences, Mitaka, Tokyo 181-8588, Japan_
6 _INAF, Arcetri Astrophysical Observatory, Largo Enrico Fermi 5, I-50125 Florence, Italy_
7 _Armagh Observatory and Planetarium, College Hill, Armagh BT61 9DG, UK_


14 January 2025


**ABSTRACT**

We present a measurement of the supermassive black hole (SMBH) mass of the nearby lenticular galaxy NGC 383, based
on Atacama Large Millimeter/sub-millimeter Array (ALMA) observations of the [12] CO(2-1) emission line with an angular
resolution of 0 [′′] _._ 050 × 0 [′′] _._ 024 (≈ 16 × 8 pc [2] ). These observations spatially resolve the nuclear molecular gas disc down to
≈ 41 _,_ 300 Schwarzschild radii and the SMBH sphere of influence by a factor of ≈ 24 radially, better than any other SMBH mass
measurement using molecular gas to date. The high resolution enables us to probe material with a maximum circular velocity
of ≈ 1040 km s [−][1], even higher than those of the highest-resolution SMBH mass measurements using megamasers. We detect a
clear Keplerian increase (from the outside in) of the line-of-sight rotation velocities, a slight offset between the gas disc kinematic
(i.e. the position of the SMBH) and morphological (i.e. the centre of the molecular gas emission) centres, an asymmetry of the
innermost rotation velocity peaks and evidence for a mild position angle warp and/or non-circular motions within the central
≈ 0 [′′] _._ 3. By forward modelling the mass distribution and ALMA data cube, we infer a SMBH mass of (3 _._ 58 ± 0 _._ 19) × 10 [9] M ⊙
(1 _𝜎_ confidence interval), more precise (5%) but consistent within ≈ 1 _._ 4 _𝜎_ with the previous measurement using lower-resolution
molecular gas data. Our measurement emphasises the importance of high spatial resolution observations for precise SMBH mass

determinations.


**Key words:** galaxies: individual: NGC 383 – galaxies: nuclei – galaxies: kinematics and dynamics – galaxies: ISM – galaxies:
elliptical and lenticular, cD



**1** **INTRODUCTION**


Research in the past few decades has revealed tight correlations between supermassive black hole (SMBH) mass ( _𝑀_ BH ) and properties
of the host galaxy such as stellar velocity dispersion, bulge mass and
stellar mass (e.g. Ferrarese & Merritt 2000; Gebhardt et al. 2000;
Beifiori et al. 2012; Kormendy & Ho 2013), thus providing strong
evidence that SMBHs co-evolve with their host galaxies across cosmic time. It is now believed that feedback from active galactic nuclei
(AGN) plays a crucial role driving and regulating this co-evolution,
by changing the physical conditions of the interstellar medium (ISM)
and/or removing it from the nuclear regions, thus quenching star
formation (see e.g. Alexander & Hickox 2012, Morganti 2017 and
Harrison et al. 2018 for reviews). Yet, the exact mechanisms underlying these processes remain unclear (e.g. Kormendy & Ho 2013;
D’Onofrio et al. 2021). Moreover, increasing evidence suggests that
SMBH – galaxy correlations depend on the galaxy’s morphological


_★_ E-mail: hengyue.zhang@physics.ox.ac.uk

- E-mail: martin.bureau@physics.ox.ac.uk


© 2024 The Authors



type and total stellar mass (e.g. McConnell & Ma 2013; van den
Bosch 2016; Krajnović et al. 2018), although the underlying causes
are again uncertain. To constrain the mechanisms governing SMBH –
galaxy co-evolution and their dependence on galaxy type, obtaining
many more precise and accurate SMBH mass measurements across
a diverse range of galaxies is crucial.


Reliable SMBH mass measurements require spatially resolving
and modelling the kinematics of matter within the SMBH’s sphere of
influence (SoI), where the SMBH gravitational influence dominates
over that of other mass components (stars, gas, dust and dark matter). Common kinematic tracers include stars (e.g. Cappellari et al.
2002; Krajnović et al. 2009; Drehmer et al. 2015), ionised gas (e.g.
Ferrarese et al. 1996; Sarzi et al. 2001; Walsh et al. 2013) and megamasers (hereafter “maser” for short; e.g. Herrnstein et al. 2005; Kuo
et al. 2011; Gao et al. 2017). Measurements of SMBH masses using
maser kinematics are currently considered the most precise and accurate (e.g. Kormendy & Ho 2013; Gao et al. 2017), as maser emission
is typically observed using very long baseline interferometry (yielding angular resolutions much higher than those of other methods)

2 _H. Zhang et al._


and traces material very close to the SMBHs. However, the maser
method is biased towards galaxies with 10 [6] ≲ _𝑀_ BH ≲ 10 [8] M ⊙,
as the required maser emission originates from a specific type of
nuclear activity almost exclusively present in Seyfert 2 AGN of lowmass galaxies (see Lo 2005 for a review). By contrast, measurements
using stellar kinematics probe a wider range of SMBH masses but
are biased towards relatively dust-free and non-disturbed objects with
massive SMBHs. Most of these are early-type galaxies (ETGs; Kormendy & Ho 2013).
In recent years, substantial improvements in the sensitivity and
angular resolution of sub-millimetre interferometers have enabled a
new method to measure SMBH masses: probing the kinematics of
molecular gas discs down to the SoI. This molecular gas method is
well suited to a wide range of galaxy masses and nuclear activities,
with ≈ 35 _,_ 000 potential local targets (Davis 2014). It is however challenging to apply the technique to objects with prominent non-circular
motions (e.g. Combes et al. 2019) or central holes in their molecular
gas discs (e.g. Kabasares et al. 2022; Ruffa et al. 2023). The mm-Wave
Interferometric Survey of Dark Object Masses (WISDOM) project,
using high-resolution CO observations from primarily the Atacama
Large Millimeter/sub-millimeter Array (ALMA), has so far provided
accurate SMBH masses of eleven typical ETGs (Davis et al. 2013b;
Onishi et al. 2017; Davis et al. 2017, 2018; Smith et al. 2019; North
et al. 2019; Smith et al. 2021; Ruffa et al. 2023; Dominiak et al.
2024a), a dwarf ETG (Davis et al. 2020) and a peculiar luminous infrared galaxy with central spiral arms (Lelli et al. 2022). Other groups
have presented similar molecular-gas SMBH mass measurements of
thirteen additional ETGs (Barth et al. 2016; Boizelle et al. 2019;
Nagai et al. 2019; Ruffa et al. 2019b; Boizelle et al. 2021; Cohn et al.
2021; Kabasares et al. 2022; Nguyen et al. 2022; Cohn et al. 2023,
2024; Dominiak et al. 2024b) and three late-type galaxies (LTGs, all
barred spirals; Onishi et al. 2015; Nguyen et al. 2020, 2021).
This paper presents a measurement of the SMBH mass of the ETG
NGC 383 using ultra-high resolution (≈ 0 [′′] _._ 034) ALMA observations
of the [12] CO(2-1) emission line. A previous WISDOM study (North
et al. 2019) inferred a SMBH mass of (4 _._ 2 ± 0 _._ 4) × 10 [9] M ⊙ using
≈ 0 [′′] _._ 13 ALMA observations of the same line. According to Zhang
et al. (2024), the physical scale probed by this prior measurement
is only ≈ 3 times worse than that of the best SMBH measurement
using masers (Herrnstein et al. 2005), when evaluated in unit of the
SMBH Schwarzschild radius ( _𝑅_ Sch ≡ 2 _𝐺𝑀_ BH / _𝑐_ [2], where _𝐺_ is the
gravitational constant and _𝑐_ is the speed of light). With ≈ 4 times
better angular resolution, this new study aims to achieve the highest
spatial resolution measurement (in the unit of _𝑅_ Sch ) of all SMBH
mass measurements to date, spatially resolving the central molecular
gas disc with unprecedented detail to derive a much more precise
SMBH mass. Section 2 introduces the target and presents our new
ALMA observations and data reduction. We describe our molecular

gas dynamical modelling technique to measure the SMBH mass in
Section 3 and discuss the sources of uncertainties and the importance
of high-resolution observations in Section 4. We conclude briefly in
Section 5.


**2** **ALMA OBSERVATIONS**


**2.1** **Target: NGC 383**


NGC 383 is an unbarred dusty lenticular galaxy (de Vaucouleurs et al.
1991) and the brightest galaxy of the NGC 383 group of galaxies,
consisting of 11 members (Sakai et al. 1994). It is also the host galaxy
of the radio source 3C 031, an AGN with relatively low-power radio


MNRAS **000**, 1–17 (2024)



jets showing a characteristic Fanaroff-Riley type I morphology (Fanaroff & Riley 1974) on kpc scales, with optical spectral properties
typical of low-excitation radio galaxies (LERGs; see e.g. MacDonald
et al. 1968; Bridle & Perley 1984; Laing & Bridle 2002; van Velzen
et al. 2012). The combination of these characteristics makes 3C 031
the prototype of this class of AGN (see also Ruffa et al. 2020). We
adopt a distance _𝐷_ = 66 _._ 6 ± 9 _._ 9 Mpc derived by Freedman et al.
(2001) using the Tully-Fisher relation (Tully & Fisher 1977). At this
distance, an angle of 1 [′′] corresponds to a spatial extent of ≈ 323 pc.
The SMBH of NGC 383 has a large SoI. Adopting _𝑀_ BH = (4 _._ 2 ±
0 _._ 4) × 10 [9] M ⊙ from North et al. (2019) and an effective (half-light)
stellar velocity dispersion _𝜎_ e = 239±16 km s [−][1] from van den Bosch
(2016), we expect the radius of the SoI to be _𝑅_ SoI ≡ _𝐺𝑀_ BH / _𝜎_ e [2] =
320 pc or ≈ 1 [′′] _._ 0. Our 0 [′′] _._ 050 × 0 [′′] _._ 024 (geometric average ≈ 0 [′′] _._ 034)
angular resolution ALMA observations presented in the next subsection spatially resolve this SoI by a factor of ≈ 29 in radius (≈ 24
for our updated _𝑀_ BH in Section 3.5), and should thus enable a precise
SMBH mass determination.
The total molecular gas mass of NGC 383 is (1 _._ 49±0 _._ 19)×10 [9] M ⊙
(Ocaña Flaquer et al. 2010), derived from single-dish observations
of the [12] CO(1-0) and the [12] CO(2-1) lines with the Institut de Radioastronomie Millimétrique (IRAM) 30-m telescope. North et al.
(2019) however showed that the molecular gas mass enclosed in the
nuclear region is negligible compared to the enclosed SMBH and
stellar masses.


**2.2** **Observations and data reduction**


We observed the [12] CO(2-1) line of NGC 383 with ALMA using
configuration C43-10 from 2021 September 5 to 2021 September 9,
as part of project 2019.1.00582.S (PI: M. Bureau). The observations
consist of three tracks with a total on-source integration time of
3 _._ 9 h. The shortest and the longest baselines are 122 and 16 _,_ 196 m,
respectively, providing a maximum recoverable scale (MRS) of 0 [′′] _._ 5
(0 _._ 16 kpc). Because the MRS is smaller than the expected _𝑅_ SoI, we
combine those data with two prior intermediate-resolution observing
tracks to improve the _𝑢𝑣_ -plane coverage and fully recover the SoI.
One track (project 2015.1.00419.S, PI: T. Davis) was observed on
2016 June 21, using ALMA configuration C36-4 (baselines of 15
to 704 m). The other track (project 2016.1.00437.S, PI: T. Davis)
was observed on 2017 August 16, using ALMA configuration C407 (baselines of 21 to 3637 m). These two lower-resolution tracks
were used in North et al. (2019) to derive the previous SMBH mass.
The MRS of the combined observing tracks is ≈ 2 [′′] _._ 7 (≈ 0 _._ 87 kpc),
approximately the size of the molecular gas disc as estimated by
North et al. (2019). The details of all observing tracks used in this
study are summarised in Table 1.
Each of the five (three new and two previous) observing tracks has
four spectral windows (SPWs). A high-resolution SPW with a bandwidth of 1 _._ 875 GHz (≈ 2500 km s [−][1] ) was centred on the redshifted
12 CO(2-1) line frequency (≈ 227 GHz) in ALMA band 6. The new
observations used 1920 channels of 976 _._ 6 kHz (≈ 1 _._ 3 km s [−][1] ),

whereas the old observations used 3840 channels of 488 _._ 3 kHz
(≈ 0 _._ 65 km s [−][1] ). Three additional SPWs, each of 2 GHz with 128
channels of 15 _._ 63 MHz (≈ 20 _._ 3 km s [−][1] ), were employed to detect
continuum emission. The properties of the spectral windows of all
adopted observing tracks are listed in Table 2. For all observing
tracks, a standard calibration strategy was adopted, using a single
bright quasar as both flux and bandpass calibrator and another one
(or two) as phase calibrator. The flux and bandpass calibrator of
the new high-resolution tracks presented here was J2253+1608. The
phase calibrators were J0057+3021 and J0112+3208.

_WISDOM XXII. SMBH of NGC 383_ 3


**Table 1.** Properties of ALMA observing tracks.


Project code Track Date Config. Baseline range ToS MRS Calibration
(s) (arcsec, kpc)
(1) (2) (3) (4) (5) (6) (7) (8)
2015.1.00419.S `uid_A002_Xb499c3_X377d` 2016-06-21 C36-4 15 m – 0.7 km 121 7.9, 2.6 Pipeline, CASA 4.5.3
2016.1.00437.S `uid_A002_Xc36f2a_X46c` 2017-08-16 C40-7 21 m – 3.6 km 1669 1.7, 0.5 Pipeline, CASA 4.7.2
2019.1.00582.S `uid_A002_Xf031e1_X16fe` 2021-09-05 C43-10 122 m – 16.2 km 4940 0.5, 0.2 Excluded manually
`uid_A002_Xf031e1_X1dfe` 2021-09-05 C43-10 122 m – 16.2 km 4757 0.5, 0.2 Pipeline & manual phase-only
self-calibration, CASA 6.2.1.7
`uid_A002_Xf06573_X1594` 2021-09-09 C43-10 122 m – 16.2 km 4494 0.5, 0.2 Pipeline & manual phase-only
self-calibration, CASA 6.2.1.7
_Notes._ Columns: (1) Project code. (2) Track ID. (3) Observation date (year-month-day). (4) ALMA array. (5) Minimum and maximum baseline length. (6) Total
on-source time (ToS). (7) Maximum recoverable scale (MRS), i.e. the largest angular scale that can be recovered with the given array. (8) Calibration method.


**Table 2.** Properties of spectral windows of adopted observing tracks.


Project code Track SPW Bandwidth _𝑁_ channel Channel width Central frequency Flagged
(GHz, km s [−][1] ) (MHz, km s [−][1] ) (GHz)
(1) (2) (3) (4) (5) (6) (7) (8)

2015.1.00419.S `uid_A002_Xb499c3_X377d` 0 2, 2600 128 15.63, 20.3 228.6 No

1 2, 2600 128 15.63, 20.3 241.8 No

2 2, 2600 128 15.63, 20.3 243.8 No

3 1.88, 2500 3840 0.49, 0.6 226.6 No

2016.1.00437.S `uid_A002_Xc36f2a_X46c` 0 2, 2600 128 15.63, 20.3 228.7 No

1 2, 2600 128 15.63, 20.3 242.0 No

2 2, 2600 128 15.63, 20.3 243.9 No

3 1.88, 2500 3840 0.49, 0.6 226.8 No

2019.1.00582.S `uid_A002_Xf031e1_X1dfe` 0 2, 2600 128 15.63, 20.3 228.8 Yes

1 2, 2600 128 15.63, 20.3 240.6 Yes

2 2, 2600 128 15.63, 20.3 242.5 Yes

3 1.88, 2500 1920 0.98, 1.3 226.8 No

`uid_A002_Xf06573_X1594` 0 2, 2600 128 15.63, 20.3 228.8 No

1 2, 2600 128 15.63, 20.3 240.6 No

2 2, 2600 128 15.63, 20.3 242.5 No

3 1.88, 2500 1920 0.98, 1.3 226.8 No
_Notes._ Columns: (1) Project code. (2) Track ID. (3) SPW ID. (4) Total bandwidth. (5) Number of channels. (6) Channel width. (7) Central frequency. (8)
Whether the SPW is flagged manually.



All the new high-resolution observing tracks were calibrated with
the Common Astronomy Software Application (CASA) package [1] (McMullin et al. 2007), version 6.2.1.7, using the standard
pipeline provided by the ALMA Science Archive [2] . While carefully
inspecting the calibrated visibilities of the three tracks using the
CASA task `plotms`, prominent residual noise spikes were identified
in some edge channels of the three continuum SPWs, which were
flagged manually using the CASA task `flagdata` . The diagnostic
weblog generated by the ALMA pipeline for the same tracks also revealed that the weather conditions at the ALMA site were very poor
during the observations. Combined with the very extended configuration of the array, this resulted in substantial residual phase noise
(inducing significant amplitude decorrelation) after the standard calibration. A continuum image of each new track was thus created,
revealing that only the first track was severely affected by the adverse
weather conditions (showing substantial signal decorrelation and image artefacts). We therefore excluded this track from the rest of the
analysis and combined the remaining calibrated (two new and two
previous) tracks from all three ALMA projects using the CASA task

`concat` .

The analysis reported in the following was carried out using this
combined dataset only, which was imaged using CASA version 6.5.2.


1 `[https://casa.nrao.edu/](https://casa.nrao.edu/)`
2 `[https://almascience.eso.org/aq/](https://almascience.eso.org/aq/)`



All the data products were created with a Högbom deconvolver (Högbom 1974), a pixel size of 0 [′′] _._ 01 and an image size of 960×960 pixels,
to reduce file sizes while sampling the synthesised beams properly.


**2.3** **Continuum emission**


The continuum SPWs and the line-free channels of the line SPWs of

the combined dataset were used to produce the continuum image. Various experiments with data reduction revealed that self-calibration [3]

could improve the quality of the data products. We thus performed
two runs of phase-only self-calibration using the CASA task `gain-`
`cal`, progressively decreasing the solution interval from 5 to 1 min,
leading to an increase of the dynamic range (i.e. the ratio between the
peak flux and the root-mean-square noise) of the continuum image
by a factor of about 4 (from ≈ 1000 to ≈ 4000). The final continuum
image was created using the `tclean` task in multi-frequency synthesis mode (Rau & Cornwell 2011), with no spectral dependence, and
Briggs weighting with a robust parameter of 2 (equivalent to natural
weighting). The latter choice was made to maximise the sensitivity
and possibly image emission from the base of the radio jets, that are
known to dominate the continuum spectrum of LERGs like NGC 383
down to mm wavelengths (see e.g. Ruffa et al. 2019a, 2020). Indeed,


3 `[https://casaguides.nrao.edu/index.php/First_Look_at_](https://casaguides.nrao.edu/index.php/First_Look_at_Self_Calibration_CASA_6.5.4)`

```
Self_Calibration_CASA_6.5.4

```

MNRAS **000**, 1–17 (2024)

4 _H. Zhang et al._


0.15


0.10


0.05


0.00


0.05


0.10



0.04


0.02


0.00


0.02


0.04



70


60


50


40


30


20


10



0.15


|0.04 0.02 0.00 0.02 0.04 RA offset (kpc)|Col2|
|---|---|
||0<br>0<br>0|
|||
|||



0.1 0.0 0.1
RA offset (arcsec)



**Figure** **1.** Central region (0 [′′] _._ 3 × 0 [′′] _._ 3) of the NGC 383 1 _._ 3 mm continuum
image, showing the only (point) source detected. Contour levels are equally
spaced between the peak intensity of 72 _._ 7 ± 0 _._ 6 mJy beam [−][1] and 50 times
the RMS noise. The synthesised beam (0 [′′] _._ 080 × 0 [′′] _._ 051) is shown in the
bottom-left corner as a black open ellipse.


the galaxy’s radio-sub-mm spectral energy distribution was analysed
by North et al. (2019), who reported a best-fitting power-law index
_𝛼_ = −0 _._ 66 ± 0 _._ 03, consistent with synchrotron radiation from AGN
radio jets (see e.g. Laing & Bridle 2002; Ruffa et al. 2020).
The continuum image obtained has a root-mean-square (RMS)
noise of 18 _𝜇_ Jy beam [−][1] and a synthesised beam full-width at halfmaximum (FWHM) of 0 [′′] _._ 080 × 0 [′′] _._ 051 (≈ 26 × 16 pc [2] ) at a position
angle (PA) of 14 [◦] _._ 3. As shown in Figure 1, the continuum image reveals only one source near the galaxy’s kinematic centre (best-fitting
SMBH position; see Section 3.5), with an integrated flux density of
71 _._ 0 ± 0 _._ 6 mJy, consistent (within the usual ≈ 10% ALMA flux calibration uncertainty) with that reported by North et al. (2019). The
deconvolved size of the source, derived by fitting a two-dimensional
(2D) Gaussian with the CASA task `imfit`, is consistent with it being
spatially unresolved (i.e. a point source). The source remains unresolved if we image the continuum with a different robust parameter
(e.g. 0 _._ 5).


**2.4** **Line emission**


_2.4.1_ _Imaging_


After applying the continuum self-calibration to the line SPWs, the
CO line emission was isolated in the _𝑢𝑣_ -plane using the CASA task
`uvcontsub`, which forms a continuum model from linear fits to linefree channels in frequency and then subtracts this model from the
visibilities. We then created the CO data cube using the `tclean` task
with Briggs weighting and a robust parameter of 0 _._ 5, to maximise the
angular resolution while achieving sufficient sensitivity. We adopted
a channel width of 20 km s [−][1], larger than that of North et al. (2019;
10 km s [−][1] ) but necessary as the combined data cube used here generally has lower signal-to-noise ratios ( _𝑆_ / _𝑁_ ). The channel velocities
were computed in the rest frame, a velocity of zero corresponding
to the rest frequency of the [12] CO(2-1) line (i.e. 230 _._ 538 GHz). The
continuum-subtracted dirty cube was cleaned in regions of line emission (identified interactively) to a conservative threshold of about
1 _._ 5 times the RMS noise ( _𝜎_ RMS ; measured from line-free channels). The final, self-calibrated and cleaned [12] CO(2-1) data cube


MNRAS **000**, 1–17 (2024)



has _𝜎_ RMS = 0 _._ 14 mJy beam [−][1] and a synthesised beam FWHM of
0 [′′] _._ 050 × 0 [′′] _._ 024 (≈ 16 × 8 pc [2] ) with a PA of 22 [◦] _._ 5, well resolving the
SoI. The data cube dynamic range (peak _𝑆_ / _𝑁_ ) is ≈ 9.


_2.4.2_ _Moment maps_


We visualise the final data cube by creating zeroth-moment
(integrated-intensity) and first-moment (intensity-weighted mean
line-of-sight velocity) maps using a masked moment technique (e.g.
Dame 2011). The mask is generated by taking a copy of the original
data cube and smoothing that copy first spatially with a uniform filter
and then spectrally with a Hanning window. Due to the small synthesised beam of our data cube, the _𝑆_ / _𝑁_ (≈ 3 per synthesised beam per
20 km s [−][1] channel) are generally not as high as those of the North
et al.’s (2019) data cube. We thus chose the size of the filters (3 times
the synthesised beam FWHM spatially and 11 channels spectrally)
and the clipping threshold (0 _._ 5 _𝜎_ RMS of the unsmoothed data cube or
≈ 6 _._ 5 _𝜎_ RMS of the smoothed cube) to optimise the trade-off between
flux recovery and noise reduction. As a result, we smoothed over
more pixels to suppress the noise in the moment maps and reduced
the clipping threshold until most of the flux was recovered. All pixels
in the smoothed cube above the threshold were then selected, and the
moment maps were created from the unsmoothed cube using only
those pixels. Irrespective of this procedure, we stress that the modelling described in Section 3 uses the final unmasked data cube, not
the moment maps.
Figure 2 shows the resulting moment maps. The molecular gas
disc extends ≈ 2 kpc in radius along its major axis, and we recover
the weak spiral structure seen in CO by North et al. (2019). The slight
central dip in the zeroth-moment map is likely a physical decrease
of the CO surface brightness within a radius of ≈ 0 [′′] _._ 1, rather than
an artefact of the masking procedure as suggested by North et al.
(2019), as the dip remains as the clipping threshold of the mask is
decreased. Dips or holes are often present at the centres of molecular
gas discs observed at high resolution (e.g. Davis et al. 2018; Izumi
et al. 2020; Nguyen et al. 2021; Ruffa et al. 2023). They are potentially
due to the dissociation or excitation of CO caused by AGN activity
(e.g. Izumi et al. 2020) and/or the suppression of molecular cloud
formation due to strong tidal forces (Sarzi et al. 2005). Nevertheless,
the CO central depression of NGC 383 does not impact the SMBH
mass measurement, as there is sufficient emission within the fainter
region to robustly trace the kinematics near the SMBH (see Section
4.1.3 for a zoomed-in view of the nuclear disc). The first-moment
(mean velocity) map reveals a typical dynamically cold rotating disc,
ideal for a SMBH mass measurement. The enhanced velocities at

the centre of the velocity map clearly indicate the presence of a
SMBH. In contrast to the previous observations of North et al. (2019)
suggesting an unwarped disc, our high-resolution observations reveal
a slight twist of the isovelocity contours within the central ≈ 0 [′′] _._ 3 in
radius, indicative of a PA warp and/or non-circular motions. We
present models of this feature in Section 4.1. Other features match
those recovered at lower angular resolution by North et al. (2019).


_2.4.3_ _Total flux_


Figure 3 shows the integrated [12] CO(2-1) spectrum of NGC 383,
extracted from the central 6 [′′] × 6 [′′] region of our high-resolution
data cube, thus covering all of the detected emission. The spectrum
clearly shows the typical double-horned shape of a rotating disc,
also observed by Lim et al. (2000), Okuda et al. (2005) and North
et al. (2019). The total [12] CO(2-1) flux in the cleaned data cube

_WISDOM XXII. SMBH of NGC 383_ 5



3


2


1


0


1


2


3



60


40


20



400


200


0


200


400



3


2


1


0


1


2


3



RA offset (kpc)
1.0 0.5 0.0 0.5 1.0


300 pc


2 0 2
RA offset (arcsec)



1.0


0.5


0.0


0.5


1.0



RA offset (kpc)
1.0 0.5 0.0 0.5 1.0


300 pc


2 0 2
RA offset (arcsec)



1.0


0.5


0.0


0.5


1.0



**Figure** **2.** Zeroth-moment (integrated-intensity; left panel) and first-moment (intensity-weighted mean line-of-sight velocity; right panel) maps of NGC 383
created from our ALMA [12] CO(2-1) data cube. The synthesised beam (0 [′′] _._ 050 × 0 [′′] _._ 024) is shown as a black filled ellipse in the bottom-left corner of each panel,
while a 300 pc scale bar is shown in the bottom-right corner of each panel. Positions are measured relative to the best-fitting kinematic centre; velocities relative
to the best-fitting systemic velocity (see Section 3.5).



is 128 _._ 9 ± 1 _._ 3 Jy km s [−][1] . This is about 50% larger than the total
flux of 87 _._ 1 Jy km s [−][1] reported by North et al. (2019). The flux
discrepancy becomes even larger if we perform another `tclean` run
with a shallower cleaning threshold of 2 _𝜎_ RMS, the total flux in
the resultant data cube then increasing to 161 _._ 0 ± 1 _._ 3 Jy km s [−][1] .
This flux discrepancy is due to a known issue (e.g. Jorsater & van
Moorsel 1995; Bureau & Carignan 2002) when evaluating total fluxes
of certain multi-configuration datasets. When the dirty beam has a
highly irregular shape, its effective area can differ substantially from
that of the (clean) Gaussian beam of equivalent angular resolution,
causing the true total flux in the residual map of `tclean` (hereafter
"residual flux" for short) to be lower than the measured residual flux
by a factor



_𝜖_ = [clean beam area] (1)

dirty beam area _[.]_


Here, _𝜖_ is thus the correction factor required to obtain the true residual
flux. The true total flux _𝑇_ is thus related to the total flux in the CLEAN

components _𝐶_ and the measured residual flux _𝑅_ by


_𝑇_ = _𝐶_ + _𝜖𝑅,_ (2)


while the measured total flux _𝑀_ is


_𝑀_ = _𝐶_ + _𝑅._ (3)


For a data cube produced with a deeper CLEAN, the discrepancy
between _𝑀_ and _𝑇_ is smaller, as less flux remains in the residual map.
Thus _𝑀_ should converge asymptotically to _𝑇_ for a sufficiently deep
cleaning threshold (≪ 1 _𝜎_ RMS ). Such a deep CLEAN is however
impractical, as it introduces numerous artefacts in the output data
cube, so we instead compute _𝑇_ and _𝜖_ using the two different values
of _𝐶_ and _𝑅_ from our two `tclean` runs, following the prescription of
Jorsater & van Moorsel (1995):




[−] _[𝐶]_ [1]
_𝜖_ = _[𝐶]_ [2] (4)

_𝑅_ 1 − _𝑅_ 2




[−] _[𝐶]_ [1] _[𝑅]_ [2]
_𝑇_ = _[𝑅]_ [1] _[𝐶]_ [2] _._ (5)

_𝑅_ 1 − _𝑅_ 2



Substituting _𝐶_ 1 = 61 _._ 5 Jy km s [−][1] and _𝑅_ 1 = 67 _._ 4 ± 1 _._ 3 Jy km s [−][1]

from the deeper `tclean` run, and _𝐶_ 2 = 51 _._ 4 Jy km s [−][1] and _𝑅_ 2 =
109 _._ 5 ± 1 _._ 3 Jy km s [−][1] from the shallower `tclean` run, we obtain
_𝜖_ = 0 _._ 24 ± 0 _._ 01 and _𝑇_ = 77 _._ 6 ± 0 _._ 9 Jy km s [−][1] . We verified this
result by creating two other data cubes cleaning down to thresholds
of 1 _𝜎_ RMS and 0 _._ 7 _𝜎_ RMS, respectively. The _𝜖_ and _𝑇_ derived from
those two additional data cubes agree well with those above.
We note that the total flux of each data cube used in this flux cor
rection procedure is obtained by integrating over the channels of the
integrated spectrum with _𝑆_ / _𝑁_ ⩾ 3. Integrating over the full velocity
range of each data cube yields a consistent total flux within the statistical uncertainties. Our computed total [12] CO(2-1) flux is slightly
smaller than that reported by North et al. (2019), but it is consistent
with the single-dish [12] CO(2-1) flux of 74 _._ 4 ± 2 _._ 8 Jy km s [−][1] from
Ocaña Flaquer et al. (2010) considering ALMA’s flux calibration
uncertainty (≈ 10%). This implies that the fluxes reported by North
et al. (2019) might also have been slightly overestimated, for similar
reasons. In any case, our SMBH mass measurement is insensitive
to this flux rescaling, so we proceed with the conservatively cleaned
data cube (with a threshold of 1 _._ 5 _𝜎_ RMS ) to minimise the artefacts
introduced by `tclean` .


_2.4.4_ _PVD_


Figure 4 shows the kinematic major-axis position-velocity diagram
(PVD) of NGC 383, extracted along a PA of 142° (the best-fitting
PA obtained in Section 3.5) by summing the flux within a 15-pixel
wide pseudo slit. When creating PVDs, we adopt a masking procedure slightly different from that used to create the moment maps,
to avoid masking out the central region: we use a spatial Gaussian
filter of FWHM equal to that of the synthesised beam (rather than
the larger uniform filter). We then select all pixels in the smoothed
cube above 0 _._ 5 _𝜎_ RMS of the unsmoothed data cube. Figure 4 shows
only the central 1 [′′] _._ 5 on either side of the kinematic centre, revealing a sharp Keplerian rise (from the outside in) of the line-of-sight
velocities within the central ≈ 0 [′′] _._ 5 in radius, the characteristic kinematic signature of a SMBH. As our high-resolution observations


MNRAS **000**, 1–17 (2024)

6 _H. Zhang et al._


Velocity (km s 1 )
1000 500 0 500 1000


400


300


200


100


0


4000 4500 5000 5500 6000
Velocity (km s 1 )


**Figure** **3.** Integrated [12] CO(2-1) spectrum of NGC 383, extracted from the
central 6 [′′] × 6 [′′] region of our high-resolution data cube, covering all of the
detected emission. Velocities are measured relative to the best-fitting systemic
velocity along the top axis (see Section 3.5). The dot-dashed line indicates
the zero flux level. The spectrum shows the typical double-horned shape of a
rotating disc.


spatially resolve material ≈ 4 times closer to the SMBH than the
previous observations of North et al. (2019), we detect velocities up
to ≈ 635 km s [−][1] in the blueshifted half of the disc, ≈ 1 _._ 8 times larger
than the highest velocity previously detected (≈ 350 km s [−][1] ).
A Keplerian circular velocity curve _𝑣_ circ ( _𝑟_ ) ∝ _𝑟_ [−][1][/][2], where
_𝑣_ circ ( _𝑟_ ) is the circular velocity at radius _𝑟_, and the four times better angular (and thus spatial) resolution, suggest we should detect a
maximum velocity of ≈ 700 km s [−][1] (twice the previous maximum
velocity). Features up to ≈ 700 km s [−][1] are indeed detected if we
lower the clipping threshold of the PVD, but those features are indistinguishable from noise due to the low _𝑆_ / _𝑁_ . Hence, we do not claim
detection of such high velocities.
Noticeably, our high-resolution observations reveal a mild asymmetry in the detected velocity peaks at small radii; the redshifted
component of the molecular gas disc only reaches ≈ 535 km s [−][1] .
This asymmetry could arise from non-circular motions (e.g. gas inflows/outflows) or a deficiency of gas in the redshifted component
of the nuclear disc (due to a specific gas morphology, e.g. a nuclear
spiral). We discuss this further in Section 4.1. Another noticeable
feature is that a small amount of central emission extends beyond the
major-axis position of zero to the opposite side of the disc (i.e. into
the "forbidden quadrants" of the PVD). This is consistent with the
observed central twist of the isovelocity contours of the velocity map,
again indicating a possible PA warp and/or non-circular motions. We
attempt to reproduce this feature with 3D disc models in Section 4.1.


**3** **DYNAMICAL MODELLING**


Our method to measure the SMBH mass of NGC 383 has been used

and described extensively in previous WISDOM papers (e.g. Davis
et al. 2017; Smith et al. 2019; North et al. 2019; Ruffa et al. 2023),
but as is often the case we need to make slight adjustments to these
procedures for the specific galaxy being studied. We thus summarise
the method and discuss the specifics of the NGC 383 modelling in
this section.


MNRAS **000**, 1–17 (2024)



5600


5400


5200


5000


4800


4600


4400



Position (pc)
400 200 0 200 400



600


400


200


200


400


600



1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)


**Figure** **4.** Major-axis position-velocity diagram of NGC 383, covering the
central 1 [′′] _._ 5 on either side of the kinematic centre. The sharp increase (from
the outside in) of the line-of-sight velocities within the central ≈ 0 [′′] _._ 5 is a clear
kinematic signature of a central SMBH. Positions are measured relative to
the best-fitting kinematic centre; velocities relative to the best-fitting systemic
velocity along the right axis (see Section 3.5). The cross in the bottom-left
corner shows the synthesised beam FWHM along the kinematic major axis
and the channel width. Velocities up to ≈ 635 km s [−][1] are detected, ≈ 1 _._ 8
times larger than the highest velocity (≈ 350 km s [−][1] ) probed by the earlier
observations of North et al. (2019).


We analyse the observed gas kinematics using the publicly available Python version of the Kinematic Molecular Simulation
tool [4] (KinMS; Davis et al. 2013a). This takes an input model of
the gas distribution and kinematics to create a mock data cube, taking into account beam smearing, spatial and velocity binning, and
line-of-sight projection effects. The simulated data cube can then be
compared directly to the observed data cube to infer the best-fitting
parameters of the input model as well as their uncertainties, calculated via a Markov chain Monte Carlo (MCMC) _𝜒_ [2] minimisation
routine.
When computing the _𝜒_ [2], we rescale the uncertainties of the data
cube by a factor of (2 _𝑁_ ) [0] _[.]_ [25], where _𝑁_ = 404 _,_ 722 is the number
of pixels with detected emission, defined as the pixels included in
the mask of Section 2.4. This approach attempts to account for the
potential systematic uncertainties usually dominating large data sets,
leading to more realistic fit uncertainties. The idea was proposed by
van den Bosch & van de Ven (2009) when using _𝜒_ [2] confidence levels
and was later adapted by Mitzkus et al. (2017) for Bayesian methods.
We have since adopted this approach in various WISDOM papers
(e.g. Smith et al. 2019; North et al. 2019). In addition, we assume a
diagonal covariance matrix, ignoring the correlation between nearby
pixels. Applying the full covariance matrix would be computationally
intractable, and the impact would be much smaller than that of the
rescaling described above (see Davis et al. 2017 for an extensive
discussion of this issue).


**3.1** **Mass model**


To generate a model of the gas kinematics, we assume that the gas
particles are in circular motions (we explore the validity of this assumption in Section 4.1), with the circular velocity curve determined


4 `[https://github.com/TimothyADavis/KinMS_fitter](https://github.com/TimothyADavis/KinMS_fitter)`
```
 https://kinms.space/

```

**Table 3.** MGE parameterisation of the NGC 383 stellar light distribution.


_𝐼_ _𝑗_ _𝜎_ _𝑗_ _𝑞_ _𝑗_
( _𝐿_ ⊙ _,_ F160W pc [−][2] ) (arcsec)
(1) (2) (3)

5789.27 0.114 0.9

2359.50 0.836 0.95

6889.76 1.07 0.95

4379.08 2.34 0.95

3535.85 4.61 0.903

999.79 12.5 0.95

_Notes._ Parameters of the deconvolved Gaussian components. (1) Surface
brightness. (2) Standard deviation (width). (3) Axial ratio.


only by the mass distribution of the galaxy. When creating the mass
model, we assume that the gravitational potential within the region
of interest is dominated by the stars and the SMBH, ignoring contributions from other possible mass components (e.g. molecular gas,
ionised gas, dust and dark matter). This assumption is reasonable as
the molecular gas mass of NGC 383 is insignificant within the SMBH
SoI (North et al. 2019), and dark matter is usually negligible in the
nuclear regions of massive galaxies (e.g. Cappellari et al. 2013; Zhu
et al. 2024).
We construct our model of the stellar mass distribution using an
approach similar to that of North et al. (2019). The stellar light
distribution is modelled by performing a multi-Gaussian expansion (MGE; Emsellem et al. 1994), using the Python version of the
`mge_fit_sectors_regularized` procedure [5] of Cappellari (2002)
on a combined _Hubble Space Telescope_ ( _HST_ ) Near Infrared Camera and Multi-Object Spectrometer F160W-filter and Two Micron
All Sky Survey (2MASS) _𝐻_ -band image. We mask the _HST_ image
to exclude regions obscured by dust and mask the 2MASS image to
remove pixels contaminated by a nearby star, using the same masks
as North et al. (2019). The combined masked image is thus fit by
a sum of 2D Gaussians that are then analytically deprojected to a
three-dimensional (3D) axisymmetric light distribution (given a free
inclination _𝑖_ ). We list the parameters of each spatially-deconvolved
Gaussian of the MGE model in Table 3.

Our MGE model yields a light profile almost identical to that used
by North et al. (2019), except for the innermost Gaussian component. The MGE components published by North et al. (2019) were
deconvolved by the point-spread function (PSF) of the 2MASS image, mistakenly even in regions of the _HST_ image, resulting in an
unrealistically narrow innermost component. By contrast, our listed
MGE components have been deconvolved by the _HST_ PSF calculated
using the TinyTim package [6] (Krist et al. 2011). Nevertheless, the difference between the integrated masses of the previous and the new
innermost Gaussian components is less than 20% of the SMBH mass
uncertainty derived in Section 3.5 and less than 7% of the difference
between the SMBH masses derived from the intermediate-resolution

data and new high-resolution data. In the comparison of the statistical
and systematic uncertainties of the two measurements presented in
Section 4.2, this small difference is negligible.
The circular velocity curve corresponding to the 3D stellar light
distribution is computed using the `mge_circular_velocity` procedure of the Jeans Anisotropic Modelling (JAM) package [7] of
Cappellari (2008). This procedure assumes a solar mass-to-light ra

5 Version 5.0 from `[https://pypi.org/project/mgefit/](https://pypi.org/project/mgefit/)`
6 Version 7.5 from `[https://github.com/spacetelescope/tinytim/](https://github.com/spacetelescope/tinytim/releases/tag/7.5)`
```
releases/tag/7.5
```

7 Version 7.2 from `[https://pypi.org/project/jampy/](https://pypi.org/project/jampy/)`



_WISDOM XXII. SMBH of NGC 383_ 7


tio ( _𝑀_ / _𝐿_ ), so we multiply the circular velocity generated with this
procedure by the square root of our (free) _𝑀_ / _𝐿_ . As in North et al.
(2019), we adopt a linearly varying _𝑀_ / _𝐿_ :



where _𝑅_ is the cylindrical radius, _𝑀_ / _𝐿_ inner is the _𝑀_ / _𝐿_ at _𝑅_ = 0 and
_𝑀_ / _𝐿_ outer is the _𝑀_ / _𝐿_ at _𝑅_ = 3 [′′] _._ 5 (approximately the outer edge of
the gas disc). The inner and the outer _𝑀_ / _𝐿_ are free parameters of
our model, and the _𝑀_ / _𝐿_ is constant (at _𝑀_ / _𝐿_ outer ) at _𝑅>_ 3 [′′] _._ 5.
Finally, we add a central point mass representing the SMBH and
compute the circular velocity curve resulting from both the stars and
the SMBH. KinMS then combines the circular velocity curve with
a variable velocity dispersion to model the kinematics of the gas
distribution.


**3.2** **Gas distribution**


The mild spiral structure in the molecular gas disc of NGC 383 makes
it inappropriate to assume a smooth axisymmetric gas distribution
described by a simple parametric function (e.g. an exponential disc).
Instead of attempting to construct a complicated function describing
this 2D light/mass density distribution (that would necessarily have
a large number of parameters), we simply adopt the observed but
spatially-deconvolved molecular gas distribution as the input. Using
the SkySampler tool [8] developed by Smith et al. (2019), we thus
uniformly sample the (deconvolved) CLEAN components produced
by the CASA task `tclean`, and generate 4 _._ 1 × 10 [6] gas particles
that exactly replicate the observed CO surface brightness distribution when convolved by the synthesised beam. The gas particles are
then passed to KinMS with the position, systemic velocity, PA and
inclination of the gas disc (assumed to be equal to those of the stars)
as free parameters. Our procedure is identical to that used by North
et al. (2019) but uses the CLEAN components of our new combined
observations rather than the old ones.


**3.3** **Nuisance parameters**


Our dynamical modelling involves four nuisance parameters: the two
coordinates of the kinematic centre (where the SMBH is) relative to
the phase centre of the data cube, the systemic velocity of the gas
disc and the integrated intensity of the CLEAN components (i.e.
the scaling factor of the input gas distribution). We note that previous WISDOM papers assumed that the kinematic centre coincides
with the gas disc’s morphological centre (the centre of the molecular
gas emission). This assumption was usually valid as the separation between the kinematic and the morphological centres was often
much smaller than the synthesised beam size. However, in our highresolution data cube, the two positions are more than one synthesised
beam apart. We thus fit the two positions separately.
As we adopt the CLEAN components as the input gas distribution
model, we can directly compute the position of the morphological
centre relative to the data cube’s phase centre, by calculating the
intensity-weighted average position of the gas particles sampled from
the CLEAN components. In this way, we confirm that this offset is
less than 1% of the synthesised beam FWHM, so from now on
we assume that the morphological centre coincides with the data
cube’s phase centre. This leaves only the coordinates of the kinematic


8 `[https://github.com/Mark-D-Smith/KinMS-skySampler](https://github.com/Mark-D-Smith/KinMS-skySampler)`


MNRAS **000**, 1–17 (2024)



_𝑅_
_𝑀_ / _𝐿_ ( _𝑅_ ) = _𝑀_ / _𝐿_ inner + ( _𝑀_ / _𝐿_ outer − _𝑀_ / _𝐿_ inner )
� 3 _._ 5 arcsec



_,_ (6)
�

8 _H. Zhang et al._


centre (relative to the phase centre) as free parameters, speeding up

convergence.


**3.4** **Prior distributions**


Although our data cube has a substantially higher angular and thus
spatial resolution than the previous one from North et al. (2019),
a MCMC fit with uninformative priors does not guarantee a more
precise SMBH mass because of the lower _𝑆_ / _𝑁_ of our data cube
(typically ≈ 3 per synthesised beam per 20 km s [−][1] channel). Indeed,
the lower _𝑆_ / _𝑁_ worsens the constraint on the inclination, which tightly
correlates with the SMBH mass (through the deprojection of the
velocities, i.e. _𝑀_ BH ∝ sin [−][2] _𝑖_ ) and dominates the error budget (see
Section 4.2.2). Hence, we place informative priors on the inclination
and the _𝑀_ / _𝐿_ using constraints derived from fitting the previous
intermediate-resolution data cube.

Rather than directly adopting the results of North et al. (2019) as
priors, we re-analyse the intermediate-resolution data cube with our
modified code that does not assume an overlap of the molecular gas
kinematic and morphological centres. Table 4 lists the best-fitting
parameters and associated uncertainties resulting from fitting the
intermediate-resolution data cube with our modified code. The best
fitting SMBH mass log ( _𝑀_ BH /M ⊙ ) = 9 _._ 59 ± 0 _._ 05 (1 _𝜎_ uncertainty
here and throughout this paper), consistent within 1 _𝜎_ with the SMBH
mass log ( _𝑀_ BH /M ⊙ ) = 9 _._ 63 ± 0 _._ 04 of North et al. (2019) (here and
throughout this paper, when we evaluate the difference of two mea
surements, we adopt an uncertainty _𝜎_ = ~~√~~ _𝜎_ 1 [2] [+] _[ 𝜎]_ 2 [2] [,] [where] _[𝜎]_ [1] [and]

_𝜎_ 2 are the uncertainties of the first and the second measurement,
respectively). The slight difference is statistically insignificant but
could be the result of separating the kinematic and morphological
centres and/or the improved MGE model. The systemic velocity of
4977 ± 1 km s [−][1] is significantly higher than that of North et al.
(2019; 4925 ± 1 km s [−][1] ), as we have corrected a previous inaccuracy in imaging the intermediate-resolution data: when converting
from frequency to velocity, the previous imaging pipeline adopted a
rounded rest frequency of 230 _._ 5 GHz for the [12] CO(2-1) line, instead
of the more accurate 230 _._ 538 GHz, causing a (non-physical) velocity
offset of ≈ 49 km s [−][1] . The best-fitting systemic velocity of North
et al. (2019) agrees with ours after accounting for this inaccuracy.
We then adopt the posterior distributions of the inclination and the
inner and outer _𝑀_ / _𝐿_ as priors when fitting the high-resolution data
cube. We use flat priors for all other parameters except the SMBH
mass, for which we use a flat logarithmic prior. The ranges of the flat
priors are listed in the second column of Table 4.


**3.5** **Results**


We fit the entire high-resolution data cube using a MCMC of
10 [5] steps, ensuring that the chain has converged and fully sampled the posterior distribution. The best-fitting parameters and their
uncertainties are listed in the last three columns of Table 4. The one
dimensional marginalised posterior distribution of each non-nuisance
parameter and the covariances between them are shown in Figure 5.
The best-fitting SMBH mass is (3 _._ 58 ± 0 _._ 19) × 10 [9] M ⊙, in good
agreement with that obtained from fitting the intermediate-resolution
data cube. The SMBH mass precision has however improved from
≈ 10% to ≈ 5%. The central panel of Figure 6 shows the kinematic major-axis PVD of the best-fitting model overlaid on the observed PVD. The Keplerian rise (from the outside in) of the velocities up to ≈ 635 km s [−][1] due to the SMBH is well reproduced by


MNRAS **000**, 1–17 (2024)



our model. By contrast, a model with no SMBH (left panel of Figure 6) fails to account for the Keplerian rise. The best-fitting model
of North et al. (2019; right panel of Figure 6, with corrected kinematic centre and systemic velocity) reproduces the PVD nicely up
to ≈ 350 km s [−][1], the highest velocity detected by the intermediateresolution observations, but it slightly overshoots the Keplerian rise
beyond ≈ 350 km s [−][1] . Indeed, our best-fitting model has a reduced
_𝜒_ [2] ( _𝜒_ r [2] ) after rescaling of 1 _._ 59 for the high-resolution data cube
and 1 _._ 20 for the intermediate-resolution data cube, better than the
_𝜒_ r [2] of the best-fitting model of North et al. (2019), that are 1 _._ 97 for
the high-resolution data cube and 1 _._ 27 for the intermediate-resolution
data cube. This highlights the importance of high-resolution observations, that fully resolve the high-velocity material around the SMBH,
to the precision and accuracy of SMBH mass measurements.
We note that our best-fitting model does not reproduce the extended
emission in the forbidden quadrants of the PVD, as it assumes an
unwarped disc and purely circular orbits. We present models of this
feature and show that it does not affect the best-fitting SMBH mass
in Section 4.1.

The stellar mass-to-light ratio of NGC 383 decreases from
3 _._ 16 ± 0 _._ 15 M ⊙ /L ⊙ _,_ F160W at the centre of the galaxy to 2 _._ 32 ±
0 _._ 09 M ⊙ /L ⊙ _,_ F160W at the outer edge of the molecular gas disc
( _𝑅_ = 3 [′′] _._ 5). Both the inner and the outer _𝑀_ / _𝐿_ agree with those
of the intermediate-resolution fit. However, the systemic velocity is
lower by ≈ 2 _._ 9 _𝜎_, potentially because of the larger channel width
(20 km s [−][1] ) of the high-resolution data cube.


**4** **DISCUSSION**


**4.1** **Warps and/or non-circular motions**


A potential source of systematic error in our model is the simplification that the molecular gas moves in circular orbits in an unwarped
disc. Contrary to this assumption, the high-resolution velocity map
(right panel of Figure 2) reveals a twist of the isovelocity contours
within the central ≈ 0 [′′] _._ 3 in radius, suggesting a PA warp and/or noncircular motions. A distortion of the velocity field is also suggested
by the forbidden quadrant emission in the kinematic major-axis PVD
(Figure 4). We thus also created a kinematic minor-axis PVD of the
data, shown in Figure 7. For a rotating disc with no warp nor noncircular motion, the minor-axis PVD traces the zero-velocity contour
as well as some emission at non-zero velocities due to the velocity
dispersion, beam smearing and the finite width of the pseudo slit,
that should be perfectly symmetric in all four quadrants. By contrast,
the minor-axis PVD of NGC 383 appears asymmetric, with more
positive-velocity emission near −0 [′′] _._ 2 and more negative-velocity
emissions near +0 [′′] _._ 2, consistent with the shape of the isovelocity
contour twist.

Despite the many features that suggest a PA warp and/or noncircular motions, the low _𝑆_ / _𝑁_ and the relatively small number of
pixels in the region of the velocity twist make it challenging to model
those features using the current data cube. Instead, we re-image the
data with Briggs weighting and a robust parameter of 2 _._ 0 (equivalent
to natural weighting), to maximize the _𝑆_ / _𝑁_ . The resulting data cube
has a synthesised beam FWHM of 0 [′′] _._ 093 × 0 [′′] _._ 062 (≈ 30 × 20 pc [2] )
with a PA of 12 [◦] _._ 9, sufficient to resolve the velocity twist. The twist is
more prominent in the velocity map of the new data cube (see the left
panels of Figure 8), thanks to the improved _𝑆_ / _𝑁_ (new cube dynamic
range, i.e. peak _𝑆_ / _𝑁_, of ≈ 22). We thus only use this naturallyweighted data cube for the investigations in this sub-section.

_WISDOM XXII. SMBH of NGC 383_ 9


**Table 4.** Best-fitting parameters and associated uncertainties, from the fits to the intermediate-resolution and high-resolution data cubes.


Intermediate resolution High resolution
Parameter Search range
Best fit 1 _𝜎_ uncertainty 3 _𝜎_ uncertainty Best fit 1 _𝜎_ uncertainty 3 _𝜎_ uncertainty

**Mass model**

log ( _𝑀_ BH /M ⊙ ) 8 _._ 70 – 9 _._ 95 9 _._ 60 ± 0 _._ 05 −0 _._ 11, +0 _._ 15 9 _._ 55 ± 0 _._ 02 ± 0 _._ 07
Inner stellar _𝑀_ / _𝐿_ (M ⊙ /L ⊙ _,_ F160W ) 0 _._ 01 – 10 3 _._ 04 −0 _._ 28, +0 _._ 32 −0 _._ 71, +1 _._ 1 3 _._ 16 ± 0 _._ 15 −0 _._ 42, +0 _._ 41
Outer stellar _𝑀_ / _𝐿_ (M ⊙ /L ⊙ _,_ F160W ) 0 _._ 01 – 10 2 _._ 41 −0 _._ 17, +0 _._ 24 −0 _._ 39, +0 _._ 60 2 _._ 32 −0 _._ 08,+0 _._ 10 −0 _._ 25, +0 _._ 28
**Molecular gas disc**
Position angle (degree) 112 – 172 142 _._ 11 −0 _._ 37, +0 _._ 34 ± 1 _._ 1 142 _._ 01 −0 _._ 30, +0 _._ 29 −0 _._ 90, +0 _._ 80
Inclination (degree) 26 – 89 37 _._ 2 −2 _._ 2, +2 _._ 0 ± 5 _._ 3 37 _._ 6 ± 1 _._ 0 −2 _._ 3, +2 _._ 8
Velocity dispersion ( km s [−][1] ) 0 – 25 9 _._ 3 ± 1 _._ 0 −3 _._ 0, +3 _._ 4 10 _._ 6 ± 0 _._ 9 −2 _._ 7, +2 _._ 8
**Nuisance parameters**
Integrated intensity (Jy km s [−][1] ) 5 – 200 74 _._ 8 −4 _._ 8, +5 _._ 0 −13, +15 82 _._ 6 ± 4 _._ 1 −12, +11
Kinematic centre _𝑋_ offset (arcsec) −3 _._ 5 – 3 _._ 5 −0 _._ 12 ± 0 _._ 02 ± 0 _._ 05 −0 _._ 12 ± 0 _._ 01 ± 0 _._ 03
Kinematic centre _𝑌_ offset (arcsec) −3 _._ 5 – 3 _._ 5 0 _._ 00 ± 0 _._ 02 −0 _._ 05, +0 _._ 06 0 _._ 00 ± 0 _._ 01 ± 0 _._ 03
Systemic velocity ( km s [−][1] ) 4890 – 5040 4977 _._ 1 −1 _._ 3, +1 _._ 4 −4 _._ 4, +4 _._ 1 4971 _._ 9 ± 1 _._ 0 −2 _._ 8, +3 _._ 0
_Notes._ The _𝑋_ and _𝑌_ offsets are measured relative to the phase centre of the high-resolution data cube, RA = 01 [h] 07 [m] 24 [s] _._ 96, Dec _._ = 32°24 [′] 45 [′′] _._ 21 (J2000.0).



_4.1.1_ _Tilted-ring models_


To create a non-parametric model of a PA warp and/or non-circular
motions, we first use the `3DFIT` task of the [3D] Barolo package [9] (Di
Teodoro & Fraternali 2015) to fit a tilted-ring model to the data cube.
We divide the central 1 [′′] _._ 2 in radius of the cube into 20 rings, each
with a width of 0 [′′] _._ 06 (approximately the FWHM of the synthesised
beam’s minor axis), fully covering and sufficiently sampling the region of the velocity twist. By default, each ring is characterised by
ten parameters: _𝑥_ and _𝑦_ coordinates of the ring’s centre ( _𝑥_ 0 _, 𝑦_ 0 ),
systemic velocity ( _𝑉_ sys ), position angle (PA), inclination (Inc), gas
surface density (Σ gas ), vertical thickness ( _𝑧_ 0 ), rotation velocity ( _𝑉_ rot ),
radial velocity ( _𝑉_ rad ) and velocity dispersion ( _𝜎_ gas ). We normalise
the gas surface density using the azimuthal average of the observed
12 CO(2-1) intensity in each ring and fix _𝑧_ 0 to be zero (infinitely
thin disc approximation), leaving only eight free parameters. We set
"TWOSTAGE=true" so that all parameters vary freely in the first
fitting stage, but the geometric parameters _𝑥_ 0, _𝑦_ 0 and _𝑉_ sys of each
ring are regularised and kept fixed (by default to the median of the
20 rings) in the second fitting stage.
As disc warps and non-circular motions are often degenerate, causing similar distortions of the isovelocity contours, we perform two
separate fits. In the first fit (warp model), the PA and Inc of each ring
are regularised by Bezier interpolation in the second fitting stage,
allowing them to vary across rings (i.e. create a warp), but the radial
velocity is fixed to _𝑉_ rad = 0. In the second fit (radial motion model),
the PA and Inc are fixed to the median across the rings in the second
fitting stage, but the radial velocity _𝑉_ rad is left free, providing a pure
radial motion model. In both fits, we only consider pixels within a
boolean mask, constructed similarly to the mask used to create the
moment maps in Section 2.4, except that we clip at 1 _𝜎_ RMS of the
naturally-weighted data cube. All other parameters of the `3DFIT` task
are set to their defaults.

For the warp model, the best-fitting ring parameters yielded by
the second fitting stage suggest that the velocity field at the centre of
NGC 383 is consistent with an abrupt change of PA from 142° in the
outer region to ≈ 110° in the inner region near _𝑅_ = 0 [′′] _._ 2. However,
the PA of the innermost region is highly uncertain and is sensitive
to the initial guess. Any PA between ≈ 100° and ≈ 130° yields a
similar RMS of ≈ 30 km s [−][1] in the first-moment (i.e. intensityweighted mean line-of-sight velocity) residuals within the central
1 [′′] _._ 2 in radius. For reference, a model with no PA warp nor radial


9 Version 1.7 from `[https://bbarolo.readthedocs.io/en/latest/](https://bbarolo.readthedocs.io/en/latest/)`



motion has a RMS residual velocity of ≈ 50 km s [−][1] in the same
region. For the radial motion model, Figure 9 shows the radial profile
of the radial velocities yielded by the second fitting stage. _𝑉_ rad is
inconsistent with zero (to 1 _𝜎_ ) at _𝑅_ ⩽ 0 [′′] _._ 21 only, revealing a roughly
linear trend of increasing radial velocity towards the centre. The
RMS of the residual velocities is ≈ 20 km s [−][1] . The [3D] Barolo

tilted-ring fits therefore provide mildly more compelling evidence
for radial motions than for a PA warp. To determine whether the
radial motions represent an inflow or an outflow, one has to know
which side of the gas disc is closer to the observer. As the dust lanes
in the galaxy’s _HST_ image appear only on the southwestern side of
the galaxy (North et al. 2019), the southwestern side is likely the near
side, and the gas disc is likely rotating in a clockwise direction in the
plane of the sky. The radial motions (if confirmed) therefore likely
represent an outflow.


_4.1.2_ _Parametric models_


To obtain parametric models of the PA warp and radial motions and
fully sample the posterior distributions of the parameters, we repeat
the above analysis with KinMS. While [3D] Barolo allows the kinematics of each ring to vary freely without considering the underlying
mass distribution, the circular velocity curve of KinMS is determined by the mass profile. KinMS thus allows us to check whether
the best-fitting SMBH mass changes after incorporating a PA warp
or non-circular motions in the kinematic model. Motivated by the
3D Barolo results, we thus use KinMS to fit a warp involving an
abrupt PA change at a particular radius but no radial motion (warp
model) and to fit radial motions with a linear variation of the radial
velocities with radius but no warp (radial motion model). The warp
model replaces the PA in the model of Section 3 with three new free
parameters: the PA in the inner region (PA inner ), the PA in the outer
region (PA outer ) and the radius at which the PA changes abruptly
( _𝑅_ change ). The radial motion model has two additional parameters:
the radial velocity at _𝑅_ = 0 ( _𝑉_ rad _,_ 0 ) and the radius beyond which the
radial velocity is 0 ( _𝑅_ cutoff ). Other parameters are identical to the
ones listed in Section 3 for the model with no warp nor radial motion
(hereafter "regular disc model").
The best-fitting warp model yields an inner PA PA inner = 117° [+] − [25] 31 [°] °
and an outer PA PA outer = 142 [◦] _._ 08 ± 0 [◦] _._ 13. The PA changes abruptly
at _𝑅_ change = 0 [′′] _._ 18 ± 0 [′′] _._ 05. The remaining best-fitting parameters,
including the SMBH mass, are almost identical to those of the regular disc model. Because the inner PA is consistent with the outer

PA within 1 _𝜎_, the warp model is not strongly favoured over models


MNRAS **000**, 1–17 (2024)

10 _H. Zhang et al._


13.5


12.0


10.5



9.0


7.5

143.0


142.5


142.0


141.5


141.0


40.5


39.0


37.5


36.0


3.6


3.4


3.2


3.0


2.8


2.55


2.40


2.25


2.10



M/L o (M /L )



log(M BH /M )



gas [ (km s] 1 )



PA (degree)



Inc (degree)



M/L i (M /L )



**Figure 5.** Corner plots showing the covariances between non-nuisance model parameters. The colours represent increasing confidence levels, from 68 _._ 3% (red,
1 _𝜎_ ) to 99 _._ 7% (grey, 3 _𝜎_ ). The histograms show the one-dimensional marginalised posterior distribution of each parameter; the dashed lines indicate the median

and the 1 _𝜎_ confidence interval.



with no PA warp. Table 5 compares the statistics of the best-fitting
warp model to those of the best-fitting regular disc model. Although
the warp model has a slightly lower _𝜒_ r [2], it has two more free parameters. Considering instead the Bayesian information criterion (BIC),
defined as BIC ≡ _𝑘_ ln _𝑁_ − 2 ln _𝑃_, where _𝑘_ is the number of free
parameters, _𝑁_ the number of constraints, and −2 ln _𝑃_ is the _𝜒_ [2] defined in Section 3, the warp model is actually less preferred than the
regular disc model. The top panels and the middle panels of Figure 8
show the central 1 [′′] _._ 5 × 1 [′′] _._ 5 of first-moment map of the regular disc
model and of the warp model, respectively, the data and the residuals
(data − model). The mask used to create the first-moment maps here
is again similar to that used in Section 2.4, but we clip at 0 _._ 65 _𝜎_ RMS
of the naturally-weighted data cube. As the regular disc model does
not produce any velocity twist, velocity residuals up to ±280 km s [−][1]

remain in the central region. By contrast, the warp model produces


MNRAS **000**, 1–17 (2024)



a mild velocity twist and reduces the velocity residuals. However, it
does not fully reproduce the observed twist and leaves residuals up
to ≈ 210 km s [−][1] at the centre. We have also tested other parametric
models of a PA warp (e.g. linear warp with radius), but none yields
a better BIC than the current model. This strongly suggests that a PA
warp does not satisfactorily explain the twist observed in the velocity
field.


It is also worth noting that if a PA warp from 142° in the outer
CO disc to ≈ 110° in the inner CO disc is present in NGC 383,
then the rotation axis of the inner CO disc would align better with
the radio jet (with a position angle PA jet = −19 _._ 7° ± 1 _._ 0°; Laing &
Bridle 2014) than that of the outer CO disc. Although recent studies
(e.g. Ruffa et al. 2020) suggest that jets and 100-pc-scale CO discs
are not preferentially aligned, the relative orientations of jets and the
rotation axes of sub-pc maser discs are usually within ≈ 30° (Kamali

_WISDOM XXII. SMBH of NGC 383_ 11



1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)





5600


5400


5200


5000


4800


4600


4400



Position (pc)
400 200 0 200 400



Position (pc)
400 200 0 200 400



600


400


200


200


400


600



1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)



Position (pc)
400 200 0 200 400


1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)



**Figure 6.** Observed kinematic major-axis position-velocity diagram of NGC 383 (orange scale with black contours), overlaid with the PVDs of different models
(cyan contours): no SMBH (left), best-fitting model from this work (centre) and best-fitting model from North et al. (2019; right). Positions are measured relative
to the best-fitting kinematic centre; velocities relative to the best-fitting systemic velocity along the right axis (see Section 3.5). The cross in the bottom-left
corner of each panel shows the synthesised beam FWHM along the kinematic major axis and the channel width. Our best-fitting model reproduces the material
beyond ≈ 350 km s [−][1] better than the best-fitting model of North et al. (2019), demonstrating the importance of high-resolution observations to the precision
and accuracy of SMBH mass measurements.



Position (arcsec)



600


400


200



5600


5400


5200


5000


4800


4600


4400



Position (pc)



Position (pc)



200


400


600



Position (arcsec)



Position (pc)


Position (arcsec)



**Figure 7.** Same as Figure 6, but showing the kinematic minor-axis PVD of NGC 383 imaged with natural weighting, overlaid with the PVDs of the best-fitting
model with no warp nor radial motion (left), a warp (centre) and radial motions (right). Although the warp model suggests a different minor-axis PA in the
innermost region, we adopt the same large-scale PA as other models to compare them. The asymmetry of the observed minor-axis PVD within the central ≈ 0 [′′] _._ 2
in radius is consistent with the observed twist of the zero-velocity contour. Both the warp and the radial motion model partly reproduce the asymmetry, while
the model with no warp nor radial motion has a symmetric minor-axis PVD by construction.



**Table 5.** Statistics of the models discussed.


Model Max | _𝑉_ res | RMS _𝑉_ res _𝜒_ r [2] _𝑘_ BIC
( km s [−][1] ) ( km s [−][1] )
(1) (2) (3) (4) (5) (6)

Regular disc 281 26 2 _._ 080 10 12043
Warp 207 24 2 _._ 075 12 12063
Radial motion 224 23 2 _._ 072 12 12060

_Notes._ (1) Model. (2) Maximum velocity residual (central 1 [′′] _._ 5 × 1 [′′] _._ 5). (3)
RMS velocity residual (central 1 [′′] _._ 5 × 1 [′′] _._ 5). (4) Reduced _𝜒_ [2] statistic (entire
cube). (5) Number of free parameters. (6) Bayesian information criterion.


et al. 2019). As our high-resolution observations of NGC 383 probe
the same physical scale (in the unit of the Schwarzschild radius) as
maser observations (Zhang et al. 2024), the PA warp could be an
indication that our observations start to reveal CO gas more closely
related to the central accretion disc that powers the AGN jet than
earlier CO observations.

The best-fitting radial motion model suggests a radial velocity
linearly decreasing from _𝑉_ rad = 294 [+] − [136] 181 [km s] [−][1] [ at] _[ 𝑅]_ [=][ 0 to] _[ 𝑉]_ [rad] [=][ 0]
at _𝑅_ cutoff = 0 [′′] _._ 28 [+] − [0] 0 _[.]_ _._ [05] 07 [.] [These] [parameters] [are] [consistent] [with] [the]



3D Barolo tilted-ring fits (Figure 9) but have large uncertainties. We
thus only have tentative evidence of radial motions, with _𝑉_ rad _,_ 0 only
≈ 1 _._ 6 _𝜎_ different from zero. The remaining best-fitting parameters,
including the SMBH mass, are all in agreement with those of the
regular disc model. Table 5 lists the statistics of the radial motion
model, while the bottom panels of Figure 8 shows the first-moment
maps of the model and data, and the associated velocity residual map.
The radial motion model has the smallest _𝜒_ r [2] of the three models, but
it is still not preferred over the regular disc model when considering
the BIC. It yields the smallest RMS velocity residual in the central
region, but large residuals up to ≈ 220 km s [−][1] remain, suggesting
non-circular motions more complicated than pure radial motions.


Finally, we compare the kinematic major-axis and minor-axis
PVDs of the three models to those of the data in Figures 10 and
7, respectively. Although the warp model suggests a different majoraxis PA in the innermost region, we adopt the same large-scale PA
as other models to compare them. Both the warp and the radial
motion models partly but not fully reproduce the forbidden quadrant
emission of the major-axis PVD and the asymmetry of the minor-axis


MNRAS **000**, 1–17 (2024)

12 _H. Zhang et al._


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2



600


400


200


0


200


400


600


600


400


200


0


200


400


600


600


400


200


0


200


400


600



600


400


200


0


200


400


600


600


400


200


0


200


400


600


600


400


200


0


200


400


600



600


400


200


0


200


400


600


600


400


200


0


200


400


600


600


400


200


0


200


400


600



0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.6


0.4


0.2


0.0


0.2


0.4


0.6



100 pc


0.5 0.0 0.5
RA offset (arcsec)


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


100 pc


0.5 0.0 0.5
RA offset (arcsec)


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


100 pc


0.5 0.0 0.5
RA offset (arcsec)



RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


No PA warp nor V rad


100 pc


0.5 0.0 0.5
RA offset (arcsec)


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


Warp model


100 pc


0.5 0.0 0.5
RA offset (arcsec)


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


Radial motion model


100 pc


0.5 0.0 0.5
RA offset (arcsec)



0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2



0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.6


0.4


0.2


0.0


0.2


0.4


0.6



RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


No PA warp nor V rad


100 pc


0.5 0.0 0.5
RA offset (arcsec)


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


Warp model


100 pc


0.5 0.0 0.5
RA offset (arcsec)


RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


Radial motion model


100 pc


0.5 0.0 0.5
RA offset (arcsec)



0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2



0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2



0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.6


0.4


0.2


0.0


0.2


0.4


0.6



**Figure 8.** Left panels: first-moment (intensity-weighted mean line-of-sight velocity) map of the NGC 383 data cube imaged with natural weighting, showing
only the central 1 [′′] _._ 5 × 1 [′′] _._ 5. The central velocity twist is more prominent as natural weighting maximises the _𝑆_ / _𝑁_ . Middle panels: first-moment maps of the
best-fitting dynamical model with no PA warp nor non-circular motion (top), the best-fitting warp model (middle) and the best-fitting radial motion model
(bottom). Right panels: corresponding first-moment residual maps (data − model). The synthesised beam (0 [′′] _._ 093 × 0 [′′] _._ 062) is shown as a black open ellipse in
the bottom-left corner of each panel, while a 100 pc scale bar is shown in the bottom-right corner of each panel. Positions are measured relative to the best-fitting
kinematic centre; velocities relative to the best-fitting systemic velocity (see Section 3.5). The model with no warp nor non-circular motion produces no velocity
twists, leaving residuals up to ±280 km s [−][1] in the inner parts. Both the warp and the radial motion models partially reproduce the central velocity twist, but
large velocity residuals (≈ 210 and ≈ 220 km s [−][1], respectively) remain at the centre.



PVD, suggesting again that neither model fully explains the observed
distortions of the velocity field.
We note that we have also tested parametric models combining
a PA warp and radial motions. However, the models’ PA warp and
radial motion parameters could not be simultaneously constrained,
leading to unconverged MCMC chains, nor could the combined models significantly reduce the velocity residuals, again because the data
do not have sufficient _𝑆_ / _𝑁_ to break the degeneracy between a PA
warp and a non-zero _𝑉_ rad .


_4.1.3_ _Implications for the SMBH mass_


As neither a PA warp nor pure radial motion satisfactorily explains
the observed velocity twist, that feature is more likely associated with


MNRAS **000**, 1–17 (2024)



more complicated non-circular motions (not necessarily pure radial
inflow or outflow) that depend on the azimuthal angle and involve
rotation velocities that are increased or decreased compared to those
expected from pure circular motions. For example, the strong kink
along the minor axis of the observed first-moment map, located at
approximately (−0 [′′] _._ 1, 0 [′′] _._ 2) from the centre, is reminiscent of those
due to streaming motions along spiral arms or barred orbits. To
search for such structures in the nuclear region, the central 1 [′′] _._ 5 × 1 [′′] _._ 5
of the zeroth-moment map of the data cube imaged with natural
weighting is shown in the left panel of Figure 11. The zeroth-moment
map of an axisymmetric model generated using [3D] Barolo and the
associated residuals (data − model) are also shown in the middle
and right panels of Figure 11, respectively. This reveals two armlike structures of positive residuals near (0 [′′] _._ 25, −0 [′′] _._ 5) and (0 [′′] _._ 2,

Radius (pc)
0 50 100 150 200 250 300 350


250


200


150


100


50


0



250


200


150


100


50


|Col1|2<br>2<br>1<br>1<br>5|
|---|---|
|||
|||
|||
|||



0.0 0.2 0.4 0.6 0.8 1.0 1.2
Radius (arcsec)


**Figure** **9.** Radial profile of the best-fitting radial velocities (with 1 _𝜎_ error
bars), from our [3D] Barolo radial motion model of NGC 383. The radial
velocity is inconsistent with zero (to 1 _𝜎_ ) at _𝑅_ ⩽ 0 [′′] _._ 21 only, revealing
evidence of radial motions in the innermost region of NGC 383.


0 [′′] _._ 45), that may be evidence of a weak spiral structure. However, that
structure is speculative and statistically insignificant compared to the
substantial random and structured noise near the centre of the zeroth
moment map. Future observations with higher sensitivity are required
to confirm the nature of this feature. The large-scale spiral features
observed by North et al. (2019; see also the left panel of Figure 2)
are also recovered in the velocity residual map covering the entire
molecular gas disc (Figure 12). The tentative spiral-like structure in
the zoomed-in zeroth-moment map is potentially a continuation of
that large-scale spiral structure and could explain the velocity twist
in the nuclear region. Unfortunately, the relatively low _𝑆_ / _𝑁_ and the
limited number of pixels in the region of the velocity twist make it
difficult to fit more complicated non-circular motion models to the
data. In any case, we note that our best-fitting SMBH mass is not
sensitive to potential non-circular motions, because of the dominance
of the SMBH on the kinematics in the central region. All the models
discussed above yield almost identical SMBH masses _𝑀_ BH ≈ 3 _._ 6 ×
10 [9] M ⊙, and the best-fitting _𝑀_ BH remains unchanged even if we
mask out the twist region during the fit. Hence, we continue to adopt
the results of the regular disc model in the following discussions, as
it has the smallest BIC (Table 5).
Despite the evidence of non-circular motions, the asymmetry
between the redshifted and blueshifted central velocity peaks of
NGC 383 is unlikely to be caused by non-circular motions, as this
feature is well reproduced by our best-fitting regular disc model assuming pure circular motions (see Figure 6). This implies that the
asymmetry is most likely due to a deficiency of [12] CO(2-1) emission on the redshifted side of the innermost region, that has already
been incorporated into our model by construction as we use the
observed (but deconvolved) intensity distribution as the input gas
distribution. This deficit can have multiple origins, in particular, a
non-axisymmetric gas morphology (e.g. the tentative nuclear spiral
discussed above).


**4.2** **Uncertainties**


Thetypical uncertaintiesassociated withaSMBHmassmeasurement
using molecular gas kinematics have been discussed extensively in



_WISDOM XXII. SMBH of NGC 383_ 13


**Table** **6.** Best-fitting parameters and associated 1 _𝜎_ uncertainties, obtained
via MCMC with _𝜒_ [2] rescaling and bootstrapping, respectively.


Parameter _𝜒_ [2] rescaling Bootstrapping

**Mass model**

log ( _𝑀_ BH /M ⊙ ) 9 _._ 554 ± 0 _._ 022 9 _._ 571 ± 0 _._ 024
Inner stellar _𝑀_ / _𝐿_ (M ⊙ /L ⊙ _,_ F160W ) 3 _._ 16 ± 0 _._ 15 3 _._ 04 ± 0 _._ 17
Outer stellar _𝑀_ / _𝐿_ (M ⊙ /L ⊙ _,_ F160W ) 2 _._ 32 ± 0 _._ 09 2 _._ 32 ± 0 _._ 10
**Molecular gas disc**
Position angle (degree) 142 _._ 01 ± 0 _._ 29 142 _._ 19 ± 0 _._ 27
Inclination (degree) 37 _._ 6 ± 1 _._ 0 38 _._ 0 ± 1 _._ 0
Velocity dispersion ( km s [−][1] ) 10 _._ 6 ± 0 _._ 9 10 _._ 2 ± 0 _._ 9


previous WISDOM papers (Onishi et al. 2017; Davis et al. 2017,
2018; Smith et al. 2019; North et al. 2019; Smith et al. 2021; Lelli
et al. 2022; Ruffa et al. 2023). In the following, we thus discuss
only the dominant sources of uncertainties of the SMBH mass of
NGC 383, as derived from our high-resolution observations.


_4.2.1_ _𝜒_ [2] _rescaling_


As discussed in Section 3, we rescaled the uncertainties of the data
cube by (2 _𝑁_ ) [0] _[.]_ [25] to attempt to account for the potential systematic uncertainties usually dominating large data sets. Without _𝜒_ [2]

rescaling, the SMBH mass precision would be 0 _._ 05%, an unrealistic
uncertainty that severely underestimates potential systematic effects.
To verify that this procedure provides a reasonable estimate of the
systematic uncertainties and to confirm that the high-resolution data
truly yields a more precise SMBH mass, we perform an independent
estimate of the systematic uncertainties by adopting a procedure
analogous to bootstrapping. We divide the data cube into four subsamples, each one a spatial quadrant of the data cube, bounded by
planes of fixed position angles. We fit each sub-sample independently,
keeping the kinematic centre position and the systemic velocity fixed
to their best-fitting values in Table 4. For each model parameter, we
then adopt the mean of the four best-fitting parameters as the overall
best fit, and their standard deviation as the 1 _𝜎_ uncertainty. Table 6
compares the best-fitting parameters and the associated 1 _𝜎_ uncertainties obtained using this approach to those obtained in Section
3.5 using the MCMC approach with _𝜒_ [2] rescaling. The best-fitting
parameters obtained using the bootstrapping-like approach all agree
within 1 _𝜎_ with those obtained using the MCMC approach and the
uncertainties are also very similar. We thus confirm that the _𝜒_ [2]

rescaling adopted provides reasonable estimates of the systematic
uncertainties of all (non-nuisance) parameters of our model.


_4.2.2_ _Other uncertainties_


As our observations spatially resolve the SMBH’s SoI by a factor of ≈
24 radially (estimated using our updated SMBH mass and _𝜎_ e, but see
Section 4.3 for a more physically-motivated calculation), they probe
the innermost region of the molecular gas disc where the kinematics
is dominated by the SMBH and is essentially independent of the
stellar mass distribution. Consequently, the inferred SMBH mass
depends only weakly on the stellar _𝑀_ / _𝐿_ . The positive correlation
between SMBH mass and outer _𝑀_ / _𝐿_ (see Figure 5) is likely a byproduct of the SMBH mass – inclination (anti-)correlation and the
_𝑀_ / _𝐿_ – inclination (anti-)correlation. We verified that a model with
a spatially-constant _𝑀_ / _𝐿_ does not improve the fit quality (using
the BIC as the metric) and yields a SMBH mass log ( _𝑀_ BH /M ⊙ ) =
9 _._ 58 ± 0 _._ 02 consistent with that from our radially linearly-varying
_𝑀_ / _𝐿_ model.


MNRAS **000**, 1–17 (2024)

14 _H. Zhang et al._


Position (pc)
400 200 0 200 400



1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)



5600


5400


5200


5000


4800


4600


4400



PA: 142.0 M BH = 3.6 × 10 [9] M
No PA warp nor V rad


100 pc



Position (pc)
400 200 0 200 400


PA: 142.0 M BH = 3.6 × 10 [9] M
Radial motion model


100 pc



600


400


200


0


200


400


600



1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)



Position (pc)
400 200 0 200 400


PA: 142.0 M BH = 3.6 × 10 [9] M
Warp model


100 pc


1.5 1.0 0.5 0.0 0.5 1.0 1.5

Position (arcsec)



**Figure** **10.** Same as Figure 7, but showing the kinematic major-axis PVD of NGC 383 imaged with natural weighting. Both the warp and the radial motion
model reproduce the forbidden quadrant emission slightly better than the model with no warp nor radial motion (in which all forbidden quadrant emission is due
to beam smearing).



150


100


50



0.6


0.4


0.2


0.0


0.2


0.4


0.6



RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


100 pc


0.5 0.0 0.5
RA offset (arcsec)



0.2


0.1


0.0


0.1


0.2



RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


100 pc


0.5 0.0 0.5
RA offset (arcsec)



0.2


0.1


0.0


0.1


0.2



0.6


0.4


0.2


0.0


0.2


0.4


0.6



100


75


50


25


0


25


50


75


100



RA offset (kpc)
0.2 0.1 0.0 0.1 0.2


100 pc


0.5 0.0 0.5
RA offset (arcsec)



0.2


0.1


0.0


0.1


0.2



150


100


50



0.6


0.4


0.2


0.0


0.2


0.4


0.6



**Figure 11.** Left: zeroth-moment (integrated-intensity) map of the NGC 383 data cube imaged with natural weighting, showing only the central 1 [′′] _._ 5 × 1 [′′] _._ 5. The
dip within a radius of ≈ 0 [′′] _._ 1 is a physical decrease of the CO surface brightness. Middle: zeroth-moment map of the best-fitting axisymmetric model generated
with [3D] Barolo. The innermost few contours appear slightly asymmetric due to the elongation of the synthesised beam. Right: corresponding zeroth-moment
residual map (data − model). The two arm-like structures of positive residuals near (0 [′′] _._ 25, −0 [′′] _._ 5) and (0 [′′] _._ 2, 0 [′′] _._ 45) may be evidence of a weak spiral structure.



The SMBH mass of NGC 383 is however strongly degenerate
with the inclination of the molecular gas disc. As _𝑀_ BH ∝ sin [−][2] _𝑖_,
the SMBH mass uncertainty is often dominated by the inclination
uncertainty, especially when the gas disc is nearly face-on. With an
inclination of only 38°, the inclination uncertainty contributes ≈ 55%
to the NGC 383 SMBH mass uncertainty budget. If the inclination
were fixed to the best-fitting inclination, the SMBH mass precision
would be ≈ 4% for the high-resolution data cube fit and ≈ 9% for the
intermediate-resolution data cube fit.

We note that every uncertainty discussed so far is much smaller
than that introduced by the ≈ 15% uncertainty of the adopted distance
(66 _._ 6 ± 9 _._ 9 Mpc; Freedman et al. 2001). Indeed, as the SMBH mass
scales linearly with the adopted distance, the distance uncertainty can
impact the SMBH mass more than all other uncertainties combined.
Nevertheless, as scaling the SMBH mass to a different distance is
straightforward (i.e. it does not require redoing the fit), we follow the
customary practice of not including the distance uncertainty in our
results.


**4.3** **Merits of high-resolution observations**


Our high-resolution observations of the molecular gas disc of
NGC 383 spatially resolve material with a maximum line-of-sight
velocity _𝑉_ obs ≈ 635 km s [−][1], higher than the ≈ 350 km s [−][1] detected


MNRAS **000**, 1–17 (2024)



by the intermediate-resolution observations of North et al. (2019).
Deprojecting this with _𝑉_ c = _𝑉_ obs /sin _𝑖_, where the best-fitting inclination _𝑖_ = 37 [◦] _._ 6, the highest-velocity material resolved by our observations has a circular velocity _𝑉_ c ≈ 1040 km s [−][1] . This is larger than
the maximum circular velocities probed by all previous molecular
gas kinematic SMBH mass measurements (Zhang et al. 2024). This
largest _𝑉_ c is the result of our measurement resolving material physically closest to the SMBH in terms of the number of Schwarzschild
radii ( _𝑅_ / _𝑅_ Schw ≈ 4 _._ 1 × 10 [4] ), as ( _𝑉_ c / _𝑐_ ) = ~~√~~ 2 ( _𝑅_ Schw / _𝑅_ ) [1][/][2] for a

Keplerian circular velocity curve (North et al. 2019). Our measurement also has the largest _𝑅_ SoI / _𝑅_ ratio ( _𝑅_ SoI / _𝑅_ ≈ 24; Zhang et al.
2024), thus spatially resolving the SoI (defined using the effective
stellar velocity dispersion _𝜎_ e ) better than all existing molecular gas
SMBH mass measurements.

We also consider an alternative definition of the SoI radius, the
radius _𝑅_ eq at which the enclosed stellar mass equals the SMBH mass:


_𝑀_ ∗ ( _𝑅_ = _𝑅_ eq ) = _𝑀_ BH _._ (7)


This _𝑅_ eq is a more accurate definition of the SoI radius than
_𝑅_ SoI ≡ _𝐺𝑀_ BH / _𝜎_ e [2], as _𝜎_ e is only a proxy of the galaxy’s gravitational potential and thus the stellar mass at large spatial scales. By
contrast, _𝑅_ eq is defined from an explicit comparison of the SMBH
mass and the stellar mass. Using the MGE model in Table 3 and the
best-fitting _𝑀_ / _𝐿_ and SMBH mass, we derive _𝑅_ eq = 0 [′′] _._ 88 ± 0 [′′] _._ 02

150


100


50


0


50


100


150



2


1


0


1


2



RA offset (kpc)
0.5 0.0 0.5


200 pc


2 0 2
RA offset (arcsec)



0.75


0.50


0.25


0.00


0.25


0.50


0.75



**Figure** **12.** Full (i.e. entire disc) first-moment (i.e. intensity-weighted mean
line-of-sight velocity) residual map of NGC 383, created by subtracting the
first-moment map of the best-fitting model with no warp nor radial motion
from the first-moment map of the data cube imaged with natural weighting.
Apart from the large residuals at the centre, the large-scale spiral features
observed by North et al. (2019; see also the left panel of Figure 2) are also
recovered. This suggests non-circular motions more complicated than pure

radial motions.


(285 ± 6 pc), in good agreement with _𝑅_ SoI = 0 [′′] _._ 84 ± 0 _._ 05. Our observations thus resolve _𝑅_ eq by a factor of ≈ 25, again better than all
prior molecular gas SMBH measurements (Zhang et al. 2024).
In other words, using either _𝑅_ Schw, _𝑅_ SoI or _𝑅_ eq as the reference
spatial scale, our measurement is the highest-resolution SMBH mass
measurement using molecular gas kinematics to date. We note that
our observations spatially resolve material closer to the SMBH in
the unit of _𝑅_ Schw than even the best SMBH mass measurement using
masers ( _𝑅_ / _𝑅_ Schw ≈ 4 _._ 4×10 [4] for NGC 4258; Herrnstein et al. 2005).
The high spatial resolution of our observations results in a SMBH
mass precision of 5% after _𝜒_ [2] rescaling, consistent with the uncertainty estimated via bootstrapping. The SMBH mass uncertainty can
not be directly compared to those of previous SMBH mass measurements, as each measurement adopts a different approach to incorporate systematic uncertainties. Among the measurements that use _𝜒_ [2]

rescaling and do not fix the inclination, our SMBH mass precision
is higher than all but those of NGC 3557 (5%; Ruffa et al. 2019b)
and NGC 7052 (4%; Smith et al. 2021). This demonstrates again the
importance of high spatial resolution for a precise SMBH mass.
NGC 383’s SMBH mass uncertainty arises primarily from the inclination uncertainty. The mass precision would improve more substantially with spatial resolution for a less face-on disc. We note that
the precision of a SMBH measurement also depends on the _𝑆_ / _𝑁_, but
at a given _𝑆_ / _𝑁_ the ALMA integration time ( _𝑡_ int ) is inversely proportional to the fourth power of the synthesised beam’s FWHM ( _𝜃_ beam ):
_𝑡_ int ∝ _𝜃_ beam [−][4] [.] [Therefore,] [ultra-high-resolution] [observations] [require]
much longer integration times that limit their schedulability, or one
must make do with lower _𝑆_ / _𝑁_ . With the current high-resolution
observations, the SMBH mass precision is impaired by the limited
_𝑆_ / _𝑁_ . If our high-resolution observations had achieved the same _𝑆_ / _𝑁_
as the existing intermediate-resolution observations, the mass precision would have been ≈ 4%, estimated by re-running the MCMC
assuming a lower _𝜎_ RMS . To summarise, higher spatial resolution
observations should lead to better SMBH mass precision at a given
inclination and _𝑆_ / _𝑁_, but achieving the desired _𝑆_ / _𝑁_ is more costly.



_WISDOM XXII. SMBH of NGC 383_ 15


A higher spatial resolution should improve not only the precision
but also the accuracy of a SMBH mass measurement, as it can reveal features that can bias the kinematic modelling but often remain
unresolved and thus undetected at lower resolutions. For example,
our high-resolution observations of NGC 383 reveal an asymmetry
of the central blueshifted and redshifted velocity peaks and an offset
between the kinematic and morphological centres, both unseen in the
intermediate-resolution observations. By incorporating both features
in our model, we reduced the inaccuracy of our kinematic modelling.
The best-fitting SMBH mass changed slightly from (4 _._ 2 ± 0 _._ 4) × 10 [9]

to (3 _._ 6 ± 0 _._ 2) × 10 [9] M ⊙ (both 1 _𝜎_ uncertainties), although the two
masses are statistically consistent. The high-resolution observations
also unveiled a velocity twist within the central ≈ 0 [′′] _._ 3 in radius,
thus providing evidence of non-circular motions in the circumnuclear disc. Although the best-fitting _𝑀_ BH is unaffected in this case
because the twist is limited to the central region where the SMBH
dominates the kinematics, an accurate model of non-circular motions
could substantially improve the SMBH mass constraint for similar
observations of other galaxies (e.g. Lelli et al. 2022).
We however caution that a higher spatial resolution does not guarantee a more precise and accurate SMBH mass measurement when
there is a central dip or hole in the CO surface brightness distribution.
Although the slight central dip of NGC 383 does not affect our measurement, a central hole in the CO distribution often prevents highresolution observations from probing emission sufficiently close to
the SMBH and thus prohibits a precise SMBH mass measurement
(e.g. Kabasares et al. 2022; Ruffa et al. 2023). Nevertheless, one may
be able to adopt a different kinematic tracer, such as [CI], which often extends closer to the SMBH than CO and does not have a central

hole in its distribution (e.g. Izumi et al. 2020; Nguyen et al. 2021),
to obtain a precise SMBH mass measurement even in the presence
of a central CO hole.


**5** **CONCLUSIONS**


We presented a measurement of the SMBH mass of NGC 383, a
lenticular galaxy hosting a jetted AGN. We used ALMA observations
of the [12] CO(2-1) emission line with a synthesised beam FWHM of
0 [′′] _._ 050×0 [′′] _._ 024 (≈ 16×8 pc [2] ), ≈ 4 times better than previous observations, spatially resolving the SMBH SoI by a factor of ≈ 24 in radius.
This spatial resolution, in the unit of either _𝑅_ Schw, _𝑅_ SoI or _𝑅_ eq, is the
highest of all SMBH mass measurements using molecular gas. The
observations also spatially resolve material closer to the SMBH in
terms of the number of Schwarzschild radii ( _𝑅_ / _𝑅_ Schw ≈ 4 _._ 1 × 10 [4] )
than the best measurements using masers ( _𝑅_ / _𝑅_ Schw ≈ 4 _._ 4 × 10 [4]

for NGC 4258; Herrnstein et al. 2005). Our high-resolution data
detect a clear Keplerian rise (from the outside in) of the (deprojected) circular velocities up to ≈ 1040 km s [−][1] . They also reveal
features undetected in previous observations: an offset between the
gas disc’s kinematic and morphological centres, a mild asymmetry
in the innermost velocity peaks and a central velocity twist suggesting non-circular motions. Our best-fitting kinematic model yields a
SMBH mass of (3 _._ 58 ± 0 _._ 19) × 10 [9] M ⊙, more precise but consistent
within ≈ 1 _._ 4 _𝜎_ with the previous SMBH mass of (4 _._ 2±0 _._ 4)×10 [9] M ⊙
derived from intermediate-resolution data (North et al. 2019). This
SMBH mass is insensitive to models of the central velocity twist. The
F160W-filter stellar _𝑀_ / _𝐿_ decreases from 3 _._ 16 ± 0 _._ 15 M ⊙ /L ⊙ _,_ F160W
at the centre to 2 _._ 32 ± 0 _._ 09 M ⊙ /L ⊙ _,_ F160W at the outer edge of the
molecular gas disc ( _𝑅_ = 3 [′′] _._ 5).
Despite this highest spatial resolution, this SMBH mass measurement is not the most precise because of the relatively low inclination,


MNRAS **000**, 1–17 (2024)

16 _H. Zhang et al._


associated with a high inclination uncertainty, and the relatively low
_𝑆_ / _𝑁_ . It nevertheless demonstrates the importance of high resolution
to the precision and accuracy of SMBH mass measurements. Although high-resolution observations require relatively long ALMA
integration times, they will steadily increase the number of precise
and accurate SMBH mass measurements using molecular gas kinematics, and they will ultimately rival the "gold standard" measurements using masers. This will, in turn, allow constraining SMBH –
galaxy scaling relations more tightly across the entire galaxy range.


**ACKNOWLEDGEMENTS**


HZ acknowledges support from a Science and Technology
Facilities Council (STFC) DPhil studentship under grant
ST/X508664/1 and the Balliol College J. T. Hamilton Scholarship in physics. MB was supported by STFC consolidated grant
‘Astrophysics at Oxford’ ST/K00106X/1 and ST/W000903/1.
IR and TAD acknowledge support from STFC consolidated grant ST/S00033X/1. This paper makes use of the
following ALMA data: ADS/JAO.ALMA#2015.1.00419.S,
ADS/JAO.ALMA#2016.1.00437.S and

ADS/JAO.ALMA#2019.1.00582.S. ALMA is a partnership of
ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic
of Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ. This research made use of the NASA/IPAC

Extragalactic Database (NED), which is operated by the Jet
Propulsion Laboratory, California Institute of Technology, under
contract with the National Aeronautics and Space Administration.


**DATA AVAILABILITY**


The raw data used in this study are publicly available on the
ALMA Science Archive: `[https://almascience.eso.org/aq/](https://almascience.eso.org/aq/)`,
and on the Hubble Science Archive: `[https://hst.esac.esa.](https://hst.esac.esa.int/ehst/)`
`[int/ehst/](https://hst.esac.esa.int/ehst/)` . The calibrated data, final data products and original
plots generated for this research will be shared upon reasonable requests to the first author.


**REFERENCES**


[Alexander D. M., Hickox R. C., 2012, New Astron. Rev., 56, 93](http://dx.doi.org/10.1016/j.newar.2011.11.003)
Barth A. J., Boizelle B. D., Darling J., Baker A. J., Buote D. A., Ho L. C.,
[Walsh J. L., 2016, ApJ, 822, L28](http://dx.doi.org/10.3847/2041-8205/822/2/L28)
[Beifiori A., Courteau S., Corsini E. M., Zhu Y., 2012, MNRAS, 419, 2497](http://dx.doi.org/10.1111/j.1365-2966.2011.19903.x)
Boizelle B. D., Barth A. J., Walsh J. L., Buote D. A., Baker A. J., Darling J.,
[Ho L. C., 2019, ApJ, 881, 10](http://dx.doi.org/10.3847/1538-4357/ab2a0a)
[Boizelle B. D., et al., 2021, ApJ, 908, 19](http://dx.doi.org/10.3847/1538-4357/abd24d)
[Bridle A. H., Perley R. A., 1984, ARA&A, 22, 319](http://dx.doi.org/10.1146/annurev.aa.22.090184.001535)
[Bureau M., Carignan C., 2002, AJ, 123, 1316](http://dx.doi.org/10.1086/338899)
[Cappellari M., 2002, MNRAS, 333, 400](http://dx.doi.org/10.1046/j.1365-8711.2002.05412.x)
[Cappellari M., 2008, MNRAS, 390, 71](http://dx.doi.org/10.1111/j.1365-2966.2008.13754.x)
Cappellari M., Verolme E. K., van der Marel R. P., Verdoes Kleĳn G. A.,
[Illingworth G. D., Franx M., Carollo C. M., de Zeeuw P. T., 2002, ApJ,](http://dx.doi.org/10.1086/342653)
[578, 787](https://ui.adsabs.harvard.edu/abs/2002ApJ...578..787C)
[Cappellari M., et al., 2013, MNRAS, 432, 1709](http://dx.doi.org/10.1093/mnras/stt562)
[Cohn J. H., et al., 2021, ApJ, 919, 77](http://dx.doi.org/10.3847/1538-4357/ac0f7810.48550/arXiv.2104.07779)
[Cohn J. H., et al., 2023, ApJ, 958, 186](http://dx.doi.org/10.3847/1538-4357/ad029d)
[Cohn J. H., et al., 2024, arXiv e-prints, p. arXiv:2409.08812](http://dx.doi.org/10.48550/arXiv.2409.08812)
[Combes F., et al., 2019, A&A, 623, A79](http://dx.doi.org/10.1051/0004-6361/201834560)


MNRAS **000**, 1–17 (2024)



D’Onofrio M., Marziani P., Chiosi C., 2021, Frontiers in [Astronomy](http://dx.doi.org/10.3389/fspas.2021.694554) and
[Space Sciences, 8, 157](http://dx.doi.org/10.3389/fspas.2021.694554)
[Dame T. M., 2011, arXiv e-prints, p. arXiv:1101.1499](http://dx.doi.org/10.48550/arXiv.1101.1499)
[Davis T. A., 2014, MNRAS, 443, 911](http://dx.doi.org/10.1093/mnras/stu1163)

[Davis T. A., et al., 2013a, MNRAS, 429, 534](http://dx.doi.org/10.1093/mnras/sts353)
Davis T. A., Bureau M., Cappellari M., Sarzi M., Blitz L., 2013b, [Nature,](http://dx.doi.org/10.1038/nature11819)

[494, 328](https://ui.adsabs.harvard.edu/abs/2013Natur.494..328D)
Davis T. A., Bureau M., Onishi K., Cappellari M., Iguchi S., Sarzi M., 2017,

[MNRAS, 468, 4675](http://dx.doi.org/10.1093/mnras/stw3217)

[Davis T. A., et al., 2018, MNRAS, 473, 3818](http://dx.doi.org/10.1093/mnras/stx2600)

[Davis T. A., et al., 2020, MNRAS, 496, 4061](http://dx.doi.org/10.1093/mnras/staa1567)

[Di Teodoro E. M., Fraternali F., 2015, MNRAS, 451, 3021](http://dx.doi.org/10.1093/mnras/stv1213)
[Dominiak P., et al., 2024a, arXiv e-prints, p. arXiv:2404.11260](http://dx.doi.org/10.48550/arXiv.2404.11260)
Dominiak P., Bureau M., Davis T. A., Ma C.-P., Greene J. E., Gu M., 2024b,


[MNRAS, 529, 1597](http://dx.doi.org/10.1093/mnras/stae314)
Drehmer D. A., Storchi-Bergmann T., Ferrari F., Cappellari M., Riffel R. A.,
[2015, MNRAS, 450, 128](http://dx.doi.org/10.1093/mnras/stv536)

[Emsellem E., Monnet G., Bacon R., 1994, A&A, 285, 723](https://ui.adsabs.harvard.edu/abs/1994A&A...285..723E)
[Fanaroff B. L., Riley J. M., 1974, MNRAS, 167, 31P](http://dx.doi.org/10.1093/mnras/167.1.31P)
[Ferrarese L., Merritt D., 2000, ApJ, 539, L9](http://dx.doi.org/10.1086/312838)
[Ferrarese L., Ford H. C., Jaffe W., 1996, ApJ, 470, 444](http://dx.doi.org/10.1086/177876)
[Freedman W. L., et al., 2001, ApJ, 553, 47](http://dx.doi.org/10.1086/320638)
[Gao F., et al., 2017, ApJ, 834, 52](http://dx.doi.org/10.3847/1538-4357/834/1/52)
[Gebhardt K., et al., 2000, ApJ, 539, L13](http://dx.doi.org/10.1086/312840)
Harrison C. M., Costa T., Tadhunter C. N., Flütsch A., Kakkad D., Perna M.,
[Vietri G., 2018, Nature Astronomy, 2, 198](http://dx.doi.org/10.1038/s41550-018-0403-6)
[Herrnstein J. R., Moran J. M., Greenhill L. J., Trotter A. S., 2005, ApJ, 629,](http://dx.doi.org/10.1086/431421)

[719](https://ui.adsabs.harvard.edu/abs/2005ApJ...629..719H)

[Högbom J. A., 1974, A&AS, 15, 417](https://ui.adsabs.harvard.edu/abs/1974A&AS...15..417H)
[Izumi T., et al., 2020, ApJ, 898, 75](http://dx.doi.org/10.3847/1538-4357/ab9cb1)
[Jorsater S., van Moorsel G. A., 1995, AJ, 110, 2037](http://dx.doi.org/10.1086/117668)
[Kabasares K. M., et al., 2022, ApJ, 934, 162](http://dx.doi.org/10.3847/1538-4357/ac7a38)
[Kamali F., et al., 2019, A&A, 624, A42](http://dx.doi.org/10.1051/0004-6361/201834600)
[Kormendy J., Ho L. C., 2013, ARA&A, 51, 511](http://dx.doi.org/10.1146/annurev-astro-082708-101811)
[Krajnović D., McDermid R. M., Cappellari M., Davies R. L., 2009, MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.15415.x)

[399, 1839](https://ui.adsabs.harvard.edu/abs/2009MNRAS.399.1839K)
[Krajnović D., Cappellari M., McDermid R. M., 2018, MNRAS, 473, 5237](http://dx.doi.org/10.1093/mnras/stx2704)
Krist J. E., Hook R. N., Stoehr F., 2011, in Kahan M. A., ed., Society
of Photo-Optical Instrumentation Engineers (SPIE) Conference Series
Vol. 8127, Optical Modeling and Performance Predictions V. p. 81270J,
[doi:10.1117/12.892762](http://dx.doi.org/10.1117/12.892762)

[Kuo C. Y., et al., 2011, ApJ, 727, 20](http://dx.doi.org/10.1088/0004-637X/727/1/20)
[Laing R. A., Bridle A. H., 2002, MNRAS, 336, 1161](http://dx.doi.org/10.1046/j.1365-8711.2002.05873.x)
[Laing R. A., Bridle A. H., 2014, MNRAS, 437, 3405](http://dx.doi.org/10.1093/mnras/stt2138)
Lelli F., Davis T. A., Bureau M., Cappellari M., Liu L., Ruffa I., Smith M. D.,
[Williams T. G., 2022, MNRAS, 516, 4066](http://dx.doi.org/10.1093/mnras/stac249310.48550/arXiv.2209.00363)
[Lim J., Leon S., Combes F., Dinh-V-Trung 2000, ApJ, 545, L93](http://dx.doi.org/10.1086/317885)
[Lo K. Y., 2005, ARA&A, 43, 625](http://dx.doi.org/10.1146/annurev.astro.41.011802.094927)

[MacDonald G. H., Kenderdine S., Neville A. C., 1968, MNRAS, 138, 259](http://dx.doi.org/10.1093/mnras/138.3.259)
[McConnell N. J., Ma C.-P., 2013, ApJ, 764, 184](http://dx.doi.org/10.1088/0004-637X/764/2/184)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Mitzkus M., Cappellari M., Walcher C. J., 2017, MNRAS, 464, 4789](http://dx.doi.org/10.1093/mnras/stw2677)
[Morganti R., 2017, Frontiers in Astronomy and Space Sciences, 4, 42](http://dx.doi.org/10.3389/fspas.2017.00042)
[Nagai H., et al., 2019, ApJ, 883, 193](http://dx.doi.org/10.3847/1538-4357/ab3e6e)
[Nguyen D. D., et al., 2020, ApJ, 892, 68](http://dx.doi.org/10.3847/1538-4357/ab77aa)
[Nguyen D. D., et al., 2021, MNRAS, 504, 4123](http://dx.doi.org/10.1093/mnras/stab1002)
[Nguyen D. D., et al., 2022, MNRAS, 509, 2920](http://dx.doi.org/10.1093/mnras/stab3016)
[North E. V., et al., 2019, MNRAS, 490, 319](http://dx.doi.org/10.1093/mnras/stz2598)
[Ocaña Flaquer B., Leon S., Combes F., Lim J., 2010, A&A, 518, A9](http://dx.doi.org/10.1051/0004-6361/200913392)
[Okuda T., Kohno K., Iguchi S., Nakanishi K., 2005, ApJ, 620, 673](http://dx.doi.org/10.1086/427140)
[Onishi K., Iguchi S., Sheth K., Kohno K., 2015, ApJ, 806, 39](http://dx.doi.org/10.1088/0004-637X/806/1/39)
Onishi K., Iguchi S., Davis T. A., Bureau M., Cappellari M., Sarzi M., Blitz
[L., 2017, MNRAS, 468, 4663](http://dx.doi.org/10.1093/mnras/stx631)

[Rau U., Cornwell T. J., 2011, A&A, 532, A71](http://dx.doi.org/10.1051/0004-6361/201117104)

[Ruffa I., et al., 2019a, MNRAS, 484, 4239](http://dx.doi.org/10.1093/mnras/stz255)

[Ruffa I., et al., 2019b, MNRAS, 489, 3739](http://dx.doi.org/10.1093/mnras/stz2368)
Ruffa I., Laing R. A., Prandoni I., Paladino R., Parma P., Davis T. A., Bureau
[M., 2020, MNRAS, 499, 5719](http://dx.doi.org/10.1093/mnras/staa3166)

[Ruffa I., et al., 2023, MNRAS, 522, 6170](http://dx.doi.org/10.1093/mnras/stad1119)
[Sakai S., Giovanelli R., Wegner G., 1994, AJ, 108, 33](http://dx.doi.org/10.1086/117042)
Sarzi M., Rix H.-W., Shields J. C., Rudnick G., Ho L. C., McIntosh D. H.,
[Filippenko A. V., Sargent W. L. W., 2001, ApJ, 550, 65](http://dx.doi.org/10.1086/319724)
Sarzi M., Rix H.-W., Shields J. C., Ho L. C., Barth A. J., Rudnick G., Filip[penko A. V., Sargent W. L. W., 2005, ApJ, 628, 169](http://dx.doi.org/10.1086/428637)
[Smith M. D., et al., 2019, MNRAS, 485, 4359](http://dx.doi.org/10.1093/mnras/stz625)

[Smith M. D., et al., 2021, MNRAS, 503, 5984](http://dx.doi.org/10.1093/mnras/stab791)
[Tully R. B., Fisher J. R., 1977, A&A, 54, 661](https://ui.adsabs.harvard.edu/abs/1977A&A....54..661T)
[Walsh J. L., Barth A. J., Ho L. C., Sarzi M., 2013, ApJ, 770, 86](http://dx.doi.org/10.1088/0004-637X/770/2/86)
[Zhang H., et al., 2024, MNRAS, 530, 3240](http://dx.doi.org/10.1093/mnras/stae1106)
[Zhu K., Lu S., Cappellari M., Li R., Mao S., Gao L., Ge J., 2024, MNRAS,](http://dx.doi.org/10.1093/mnras/stad3213)

[527, 706](https://ui.adsabs.harvard.edu/abs/2024MNRAS.527..706Z)

de Vaucouleurs G., de Vaucouleurs A., Corwin Herold G. J., Buta R. J., Paturel
G., Fouque P., 1991, Third Reference Catalogue of Bright Galaxies
van Velzen S., Falcke H., Schellart P., Nierstenhöfer N., Kampert K.-H., 2012,

[A&A, 544, A18](http://dx.doi.org/10.1051/0004-6361/201219389)
[van den Bosch R. C. E., 2016, ApJ, 831, 134](http://dx.doi.org/10.3847/0004-637X/831/2/134)
[van den Bosch R. C. E., van de Ven G., 2009, MNRAS, 398, 1117](http://dx.doi.org/10.1111/j.1365-2966.2009.15177.x)


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



_WISDOM XXII. SMBH of NGC 383_ 17


MNRAS **000**, 1–17 (2024)


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "0.050 arcsec × 0.024 arcsec (CO robust = 0.5); 0.080 arcsec × 0.051 arcsec (continuum robust = 2); 0.093 arcsec × 0.062 arcsec (CO robust = 2.0)",
  "failed_quote": "The final, self-calibrated and cleaned [12] CO(2-1) data cube has _𝜎_ RMS = 0 _._ 14 mJy beam [−][1] and a synthesised beam FWHM of 0 [′′] _._ 050 × 0 [′′] _._ 024 (≈ 16 × 8 pc [2] ) with a PA of 22 [◦] _._ 5, well resolving the SoI."
 },
 {
  "path": "data.sensitivity.evidence[1]",
  "value": "18 uJy beam^-1 (continuum); 0.14 mJy beam^-1 per 20 km s^-1 channel (CO cube, robust = 0.5)",
  "failed_quote": "The final, self-calibrated and cleaned [12] CO(2-1) data cube has _𝜎_ RMS = 0 _._ 14 mJy beam [−][1] and a synthesised beam FWHM of 0 [′′] _._ 050 × 0 [′′] _._ 024 (≈ 16 × 8 pc [2] ) with a PA of 22 [◦] _._ 5, well resolving the SoI."
 },
 {
  "path": "processing.calibration.self_calibration.evidence[0]",
  "value": "Two runs of phase-only self-calibration using CASA task gaincal, decreasing solution interval from 5 to 1 min, increasing continuum dynamic range from ~1000 to ~4000; applied to line SPWs",
  "failed_quote": "We thus performed two runs of phase-only self-calibration using the CASA task `gaincal`, progressively decreasing the solution interval from 5 to 1 min, leading to an increase of the dynamic range (i.e. the ratio between the peak flux and the root-mean-square noise) of the continuum image by a factor of about 4 (from ≈ 1000 to ≈ 4000)."
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "0.080 arcsec × 0.051 arcsec, PA 14.3 deg (continuum); 0.050 arcsec × 0.024 arcsec, PA 22.5 deg (CO robust = 0.5); 0.093 arcsec × 0.062 arcsec, PA 12.9 deg (CO robust = 2.0)",
  "failed_quote": "The final, self-calibrated and cleaned [12] CO(2-1) data cube has _𝜎_ RMS = 0 _._ 14 mJy beam [−][1] and a synthesised beam FWHM of 0 [′′] _._ 050 × 0 [′′] _._ 024 (≈ 16 × 8 pc [2] ) with a PA of 22 [◦] _._ 5, well resolving the SoI."
 },
 {
  "path": "processing.imaging.final_rms.evidence[1]",
  "value": "18 uJy beam^-1 (continuum); 0.14 mJy beam^-1 per 20 km s^-1 channel (CO cube, robust = 0.5)",
  "failed_quote": "The final, self-calibrated and cleaned [12] CO(2-1) data cube has _𝜎_ RMS = 0 _._ 14 mJy beam [−][1] and a synthesised beam FWHM of 0 [′′] _._ 050 × 0 [′′] _._ 024 (≈ 16 × 8 pc [2] ) with a PA of 22 [◦] _._ 5, well resolving the SoI."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Calibrate tracks with ALMA pipeline, manually flag edge-channel noise spikes in continuum SPWs using flagdata, exclude the first C43-10 track due to poor weather decorrelation, concatenate the remaining four tracks with concat, perform two rounds of phase-only self-calibration with gaincal, image with tclean in MFS mode, and fit a 2D Gaussian with imfit.",
  "failed_quote": "We thus performed two runs of phase-only self-calibration using the CASA task `gaincal`, progressively decreasing the solution interval from 5 to 1 min, leading to an increase of the dynamic range (i.e. the ratio between the peak flux and the root-mean-square noise) of the continuum image by a factor of about 4 (from ≈ 1000 to ≈ 4000)."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[1]",
  "value": "Circular gas orbits in an unwarped thin disc; spatially constant gas velocity dispersion; diagonal covariance matrix; morphological centre coincides with phase centre while kinematic centre is offset",
  "failed_quote": "To generate a model of the gas kinematics, we assume that the gas particles are in circular motions (we explore the validity of this assumption in Section 4.1), with the circular velocity curve determined only by the mass distribution of the galaxy."
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Maximum observed line-of-sight velocity (blueshifted) = 635 km s^-1",
  "failed_quote": "As our high-resolution observations spatially resolve material ≈ 4 times closer to the SMBH than the previous observations of North et al. (2019), we detect velocities up to ≈ 635 km s [−][1] in the blueshifted half of the disc, ≈ 1 _._ 8 times larger than the highest velocity previously detected (≈ 350 km s [−][1] )."
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "Sphere of influence radius (R_SoI) = 0.84 arcsec",
  "failed_quote": "Using the MGE model in Table 3 and the best-fitting _𝑀_ / _𝐿_ and SMBH mass, we derive _𝑅_ eq = 0 [′′] _._ 88 ± 0 [′′] _._ 02 (285 ± 6 pc), in good agreement with _𝑅_ SoI = 0 [′′] _._ 84 ± 0 _._ 05."
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Equal-mass sphere of influence radius (R_eq) = 0.88 arcsec",
  "failed_quote": "Using the MGE model in Table 3 and the best-fitting _𝑀_ / _𝐿_ and SMBH mass, we derive _𝑅_ eq = 0 [′′] _._ 88 ± 0 [′′] _._ 02 (285 ± 6 pc), in good agreement with _𝑅_ SoI = 0 [′′] _._ 84 ± 0 _._ 05."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "Neither a simple PA warp nor pure radial motion satisfactorily explains the central velocity twist (which likely reflects more complex azimuthal non-circular motions such as nuclear spiral streaming), and the inferred SMBH mass is insensitive to these features.",
  "failed_quote": "Both the warp and the radial motion models partly but not fully reproduce the forbidden quadrant emission of the major-axis PVD and the asymmetry of the minor-axis PVD, suggesting again that neither model fully explains the observed distortions of the velocity field."
 }
]
```
