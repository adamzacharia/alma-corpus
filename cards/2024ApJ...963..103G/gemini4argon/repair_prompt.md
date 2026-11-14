# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...963..103G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version January 8, 2024
Typeset using L [A] TEX default style in AASTeX631


**The** **ALMA** **View** **of** **Positive** **Black** **Hole** **Feedback** **in** **the** **Dwarf** **Galaxy** **Henize** **2–10**


[Hansung](http://orcid.org/0000-0003-1436-7658) B. Gim [1] and Amy E. Reines [1, 2]


1 _Department_ _of_ _Physics,_ _Montana_ _State_ _University,_ _Bozeman,_ _MT_ _59717,_ _USA_
2 _eXtreme_ _Gravity_ _Institute,_ _Department_ _of_ _Physics,_ _Montana_ _State_ _University,_ _Bozeman,_ _MT_ _59717,_ _USA_


ABSTRACT


Henize 2–10 is a dwarf starburst galaxy hosting a _∼_ 10 [6] _M_ _⊙_ black hole (BH) that is driving an
ionized outflow and triggering star formation within the central _∼_ 100 pc of the galaxy. Here we
present ALMA continuum observations from 99 to 340 GHz, as well as spectral line observations of
the molecules CO (1–0, 3–2), HCN (1–0, 3–2), and HCO+ (1–0, 3–2), with a focus on the BH and
its vicinity. Incorporating cm-wave radio measurements from the literature, we show that the spectral
energy distribution of the BH is dominated by synchrotron emission from 1.4 to 340 GHz with a
spectral index of _α ≈−_ 0 _._ 5. We analyze the spectral line data and identify an elongated molecular gas
structure around the BH with a velocity distinct from the surrounding regions. The physical extent of
this molecular gas structure is _≈_ 130 pc _×_ 30 pc and the molecular gas mass is _∼_ 10 [6] _M_ _⊙_ . Despite an
abundance of molecular gas in this general region, the position of the BH is significantly offset from
the peak intensity, which may explain why the BH is radiating at a very low Eddington ratio. Our
analysis of the spatially-resolved line ratio between CO J=3–2 and J=1–0 implies that the CO gas in
the vicinity of the BH is highly excited, particularly at the interface between the BH outflow and the
regions of triggered star formation. This suggests that the cold molecular gas is being shocked by the
bipolar outflow from the BH, supporting the case for positive BH feedback.


_Keywords:_ galaxies:active – galaxies: dwarf –galaxies: individual (He 2–10)    - ISM: molecules


1. INTRODUCTION


Galaxy evolution is governed by the balance between star formation and quenching (Somerville & Dav´e 2015), and
Active Galactic Nuclei (AGN) are thought to play a crucial role in the extinguishing of star formation in massive
galaxies. Prior to the last decade, massive black holes (BHs) that sometimes accrete and shine as AGNs were almost
exclusively found in giant galaxies (e.g., Kormendy & Ho 2013). However, we now know that AGNs in dwarf galaxies
are much more common than previously thought and the BHs have typical masses of _M_ BH _<_ 10 [6] _M_ _⊙_ (for reviews, see
Greene et al. 2020; Reines 2022). Searching for and studying these systems is important for our understanding of the
role of AGN fueling and feedback in the low-mass regime and may also provide clues about the origin of the first BH
“seeds” in the early Universe (e.g., Volonteri et al. 2021).
Henize 2–10 (He 2–10) is a nearby (d=9 Mpc) dwarf starburst galaxy (e.g., Nguyen et al. 2014) that is particularly
remarkable for displaying evidence of positive AGN feedback (i.e., enhancing star formation; Schutte & Reines 2022,
see Figure 1 here). Multiwavelength studies have shown that this galaxy hosts a massive BH in its center (Reines
et al. 2011) through coincident peaks at radio and X-ray wavelengths (Reines et al. 2016) detected with the Very
Large Array (VLA) and the _Chandra_ _X-ray_ _Observatory_ (Chandra), respectively. The BH is also detected as a strong
non-thermal source by high-angular resolution observations using the Long Baseline Array (LBA, Reines & Deller
2012). The mass of the central BH is estimated to be M BH _∼_ 10 [6] M _⊙_ based on stellar velocity measurements (Riffel
2020) and the scaling relation between total stellar mass and BH mass (Reines & Volonteri 2015). Combined with the
X-ray luminosity, this indicates the BH is accreting at a very low Eddington ratio (Reines et al. 2016). A recent study


Corresponding author: Hansung B. Gim

[hansung.gim@montana.edu](mailto: hansung.gim@montana.edu)

2 Gim & Reines


**Figure** **1.** The four color composite image of He 2–10 is generated from F330W (B), F606W (V), F658N (H _α_ ), and F814W (I)
from the _HST_ . The white box shows the central 6 _[′′]_ _×_ 4 _[′′]_ region, and the inset shows the H _α_ +continuum image presenting the
outflow from the BH. (Credit to NASA, ESA, Zachary Schutte, & Amy Reines)


using _Hubble_ _Space_ _Telescope_ (HST) spectroscopy revealed that the central BH is driving an outflow of ionized gas,
which is triggering the formation of star clusters located _∼_ 70 pc ( _∼_ 1 _[′′]_ _._ 5) from the BH (Schutte & Reines 2022). This
is the first case of positive BH feedback found in a dwarf galaxy and may represent a low-power analog of radio-loud
AGNs experiencing “jet-mode” feedback (Schutte & Reines 2022).
Molecular gas and dust can both feed and obscure AGNs. While the cold gas distributions of He 2–10 have been
extensively studied for the galaxy as a whole and with a focus on the star-forming regions, very little is known about
the molecular gas in the immediate vicinity of the BH. Here we present and analyze high-resolution Atacama Large
Millimeter/submillimeter Array (ALMA) [1] observations of He 2–10 with a specific focus on the central massive BH
and its immediate surroundings ( _∼_ 130 pc). A summary of previous studies of the molecular gas in He 2–10 is given
below.

Baas et al. (1994) first observed the three CO transitions (J=1–0, J=2–1, and J=3–2) of He 2–10, showing that
hot and cold molecular gas is distributed throughout the galaxy. The first interferometric observations of CO J=1–0
with a synthesized beam size of 6 _[′′]_ _._ 5 _×_ 5 _[′′]_ _._ 5 (284 pc _×_ 240 pc) revealed an elongated morphology, indicating that He 2–10
could be a post-merger system and/or experiencing tidal interactions (Kobulnicky et al. 1995). Meier et al. (2001)
observed the CO J=3–2 line to investigate the interstellar medium (ISM) conditions in the central 13 _[′′]_ (567 pc) and
found a gas temperature of T K _∼_ 5 _−_ 10 K and a number density of n(H 2 ) _>_ 10 [3] _[.]_ [5] cm _[−]_ [3] . Higher transitions of
CO lines, J=3–2, 4–3, 6–5, and 7–6, were observed by Bayet et al. (2004). They found that the central region hosts


1 The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by
Associated Universities, Inc.

ALMA View of Positive Black Hole Feedback in the He 2–10 3


**Table** **1.** ALMA observations of He 2–10


(1) (2) (3) (4) (5) (6) (7) (8)


Project code Band Frequency Lines Integration Bandpass _[a]_ Phase _[b]_ Amplitude _[c]_


(GHz)


2011.0.00348.S [(1)] 3 86.95 – 102.47 HCN (1–0) 204m 37s J053851-440507 J082601-223027 Titan
HCO [+] (1–0) Ceres


J0750+1231
2012.1.00413.S [(2)] 6 248.79 – 267.73 HCN (3–2) 286m 47s J0538-4405 J0747-3310 J1037-295
HCO [+] (3–2) J0826-2230 J0538-4405
J1058+0133
2015.1.01569.S [(3)] 3 111.99 – 115.18 J0826-2230 J1107-4449
2016.1.00027.S [(3)] 3 99.72 – 115.17 CO (1–0) 187m 50s J1037-2934 J0538-4405 J0846-2607
2016.1.00492.S [(4)] 7 332.06 – 348.00 CO (3–2) 50m 29s J0538-4405 J0846-2607 J0538-4405


J0725-0054 J0725-0054
2019.1.01641.S [(5)] 3 96.91 – 112.51 – 103m 43s J0846-2607
J1037-2934 J1037-2934


Note— ( _a_ ) Bandpass calibrators ; ( _b_ ) Phase calibrators ; ( _c_ ) Amplitude calibrators
PI names: (1) Kelsey Johnson ; (2) Amy Reines ; (3) Nia Imara ; (4) Sara Beck ; (5) Zhiyu Zhang


warm and dense molecular gas with T _K_ _≈_ 50 _−_ 100 K and n(H 2 ) _>_ 10 [4] cm _[−]_ [3], which is an order of magnitude higher
than the temperature calculated with lower transitions of CO lines (J = 1–0, 2–1 and 3–2) by Meier et al. (2001).
Beck et al. (2018) observed the CO J=3–2 line with a synthesized beam size of 0 _[′′]_ _._ 3 (13 pc) using ALMA and found
several clumpy filaments separated spatially and kinematically. Their kinematic analysis led to the conclusion that
the molecular filaments feed the star formation in the star clusters. Imara & Faesi (2019) traced the CO J=1–0 line
with a synthesized beam size of 0 _[′′]_ _._ 67 _×_ 0 _[′′]_ _._ 58 (29 pc _×_ 25 pc) using ALMA and showed that He 2–10 has a more complex
morphology with clumps, ring-shaped structures, and high-density peak emissions.
Higher critical density molecular gas tracers have also been observed in He 2–10. Imanishi et al. (2007) observed
the HCN J=1–0 and HCO [+] J = 1–0 line with a beam size of 10 _[′′]_ _._ 8 _×_ 5 _[′′]_ _._ 5 (471 pc _×_ 240 pc) and reported the ratio of
HCN (1–0)/HCO [+] (1–0) _<_ 0 _._ 6, which is low compared to Luminous InfraRed Galaxies (LIRGs). The strong HCN
J=1–0 line was also recovered by the single dish observations of Santangelo et al. (2009). Johnson et al. (2018) used
ALMA observations tracing HCN J=1–0, HCO [+] J=1–0, HNC J=1–0, and CCH J=1–0 with a synthesized beam size
of 1 _[′′]_ _._ 7 _×_ 1 _[′′]_ _._ 6 (74 pc _×_ 70 pc) and showed that HCO [+] J=1–0 correlates with the thermal radio continuum in the intense
central star forming regions.
Here we present the first study of the molecular gas in the immediate vicinity of the central BH using high-resolution
observations with ALMA. We describe the observations and data reduction in § 2, the analysis and results in § 3, and
our conclusions in § 4.


2. ALMA OBSERVATIONS AND DATA REDUCTION


He 2–10 has been observed by ALMA in different bands for six different projects. The specifics of the ALMA
observations are summarized in Table 1, encompassing essential information such as project codes, bands, frequency
ranges, spectral lines, total integration time, bandpass, phase, and amplitude calibrators. The names of PIs are
presented in the caption located below the table. We downloaded all the data listed in Table 1 from the ALMA
archive website [2] . The calibrated data were processed using the _scriptForPI.py_ with the appropriate version of the
Common Astronomy Software Application (CASA, Bean et al. 2022) as outlined in the README files. We also
flagged some bad antennas, which improved the sensitivity.


2 The ALMA archival website is at [https://almascience.nrao.edu/aq/](https://almascience.nrao.edu/aq/)

4 Gim & Reines


2.1. _Spectral_ _Line_ _Image_ _Cubes_


Spectral line image cubes were generated using CASA 6.5.1 with the continuum-subtracted spectral line visibilities.
The continuum subtraction was performed using the CASA task _uvcontsub_, which uses line-free channels and a linear
fit of order 1 to estimate the continuum. The continuum-subtracted visibilities were then imaged using the CASA
task _tclean_ with the hogbom algorithm for deconvolution of the point spread function (PSF), _briggsbwtaper_, and
_perchanweightdensity_ . These options provide a flat root mean square (RMS) noise and beam size distribution over
the channels, and the beam size comparable to that of the continuum image. The velocity frame is set to BARY,
which normalizes the velocity to the barycentric system. The cleaning process was repeated until the maximum of
the residual map reached 2 _σ_, where _σ_ is the RMS noise of the image cube per channel. The line-free channels for the
continuum subtraction, image size, cell size, velocity spacing, robust value for the _briggsbwtaper_, and rest frequency
are summarized in Table 2. The resulting image cubes were smoothed to the largest beam size within the selected
velocity range including lines with the CASA task _imsmooth_ . The resulting beam sizes and RMS noises of molecular
line image cubes are summarized in Table 2.


2.2. _Continuum_ _Imaging_


We created four different continuum images: low-frequency Band 3 (low-Band 3), high-frequency Band 3 (high-Band
3), Band 6, and Band 7 continuum images. The Band 3 continuum data are from ALMA project codes 2011.0.00348.S,
2015.1.01569.S, 2016.1.00027.S, and 2019.1.01641.S, which were split into low- and high-frequency data at 110 GHz.
This frequency was chosen to maximize the angular resolution of the high-frequency Band 3 continuum image. The
Band 6 and 7 continuum data are from ALMA project codes 2012.1.00413.S and 2016.1.00492.S, respectively.
The continuum images were created by combining the visibilities from the continuum spectral windows (SPWs) with
wide channel widths of 15.625 MHz and the line-free channels from the SPWs containing spectral lines with narrow
channel widths (as explained in Section 2.1). The latter were smoothed to a channel width of 15.625 MHz in SPWs for
the continuum using the CASA task _mstransform_ . The continuum images were generated using the CASA 6.5.1 task
_tclean_ with the briggs weighting function and the hogbom deconvolution algorithm. The standard multi-frequency
synthesis (MFS) was applied for imaging the continuum data, except for the low-Band 3. For the low-Band 3 data, we
applied the multi-term MFS (Rau & Cornwell 2011), as its fractional bandwidth is about 23.7% (with a bandwidth
of 23.4 GHz, or 87.1–110.5 GHz, relative to the effective frequency of 98.8 GHz). We used _nterms_ =3, which yields a
more accurate intensity map by calculating the mean intensity, spectral index, and curvature over the frequency. The
cleaning was stopped when it reached 2 _σ_, where _σ_ is the RMS noise of the image. We summarized the parameters
used in the CASA task _tclean_ and the resulting synthesized beam sizes and RMS noise in Table 2.
The synthesized beam sizes and sensitivities of the continuum images in this paper are slightly different from
those obtained in Costa et al. (2021) for 113 and 340 GHz, while the characteristics of the 251 GHz image are the
same. Our 113 GHz continuum image was obtained by concatenating the data of 2015.1.01569.S, 2016.1.00027.S, and
2019.1.01641.S, which is different from Costa et al. (2021) who used 2016.1.00027.S for the 113 GHz continuum image.
The synthesized beam size and RMS noise were 0 _[′′]_ _._ 38 _×_ 0 _[′′]_ _._ 21 and 17 _µ_ Jy beam _[−]_ [1], respectively (Costa et al. 2021), where
the beam size is 18% better than our 113 GHz continuum image. This difference is attributed to adding two other
observations to our data, 2015.1.01569.S and 2019.1.01641.S, since the robust value used in CASA task _tclean_ was the
same as ours. The project codes 2015.1.01569.S and 2019.1.01641.S have maximum baselines of 1.4 km and 181.9 m,
respectively, while the project 2016.1.00027.S has a maximum baseline of 2.6 km. Adding these two data with shorter
baselines degraded the angular resolution when the data of 2016.1.00027.S is used solely. While the synthesized beam
sizes are almost same for the 340 GHz images, the RMS noises are 27.7 and 52.0 _µ_ Jy beam _[−]_ [1] for our image and that
of Costa et al. (2021). The reason for this difference is unclear.


2.3. _Astrometry_


It is important to facilitate the comparison of multi-wavelength observations of Henize 2–10 taken with different
telescopes. The location of the BH in He 2–10 was originally determined in the reference frame of 2MASS, due to its
absolute positional accuracy of ≲ 0 _[′′]_ _._ 1. Images from _HST_, the VLA, and _Chandra_ were shifted to match the locations
with the astrometric frame of it 2MASS (Reines et al. 2011). Here, we identified the offsets in our ALMA observations
with respect to the 2MASS reference frame and applied them to the ALMA observations.
We used the highest angular resolution ALMA continuum image at 251 GHz (with a synthesized beam size of
0 _[′′]_ _._ 18 _×_ 0 _[′′]_ _._ 16) and the 1.4 GHz continuum image observed at the Long Baseline Array (LBA) with a synthesized beam

ALMA View of Positive Black Hole Feedback in the He 2–10 5

6 Gim & Reines


size of 0 _[′′]_ _._ 11 _×_ 0 _[′′]_ _._ 03 to estimate the offset. The astrometry of the LBA 1.4 GHz continuum image was corrected to that
of the 2MASS (Reines & Deller 2012). The shift was determined by matching the local maximum in the 251 GHz
continuum image to the center of the BH in the 1.4 GHz continuum image. We estimated the shift of ∆RA =0 _[′′]_ _._ 0735
West and ∆DEC =0 _[′′]_ _._ 095 North and applied this shift to all ALMA spectral line image cubes and continuum images.


3. ANALYSIS AND RESULTS


3.1. _Continuum_ _Emission_ _and_ _Radio_ _SED_ _of_ _the_ _Black_ _Hole_


Figure 2 presents the sub-mm continuum maps at 99 (first row), 113 (second row), 251 (third row), and 340 GHz
(fourth row), respectively. The white contours show the 99 GHz continuum at 100, 150, 180, 200, and 250 _µ_ Jy
beam _[−]_ [1] . The local maxima of the contours in the center indicate the position of BH, which coincides with the
positions determined by the VLA & LBA (Reines et al. 2011; Reines & Deller 2012). The continuum images show two
prominent blobs and one central source. The two strong emission blobs correspond to the starburst regions, and the
central source indicates the massive BH (Reines et al. 2011; Reines & Deller 2012). The position of the BH is defined
in the continuum images as the local maxima in the central region between the two prominent starburst regions,
as indicated in the top panel of Figure 2. The two starburst regions are clearly visible in all the continuum maps;
however, the central BH is not seen in the 340 GHz continuum map. In the 340 GHz continuum image, the BH is
located between two small continuum sources located 0 _[′′]_ _._ 217 (10 pc) and 0 _[′′]_ _._ 526 (23 pc) away.
An earlier study by Allen et al. (1976) showed that He 2–10 as a whole is dominated by nonthermal emission.
However, high angular resolution VLA and ALMA observations have shown that the central few hundred parsecs
are dominated by free-free emission from bursty star formation (Johnson & Kobulnicky 2003; Johnson et al. 2018;
Costa et al. 2021). The central BH, on the other hand, is governed by nonthermal synchrotron emission (Johnson
& Kobulnicky 2003; Reines et al. 2011; Reines & Deller 2012; Costa et al. 2021). Although the VLA + ALMA
SED analysis for the BH has been done by Costa et al. (2021), we revisited this analysis with revised flux density
measurements of the submillimeter (sub-mm) continuum and inclusion of 1.4 GHz flux density observed at the LBA
(Reines & Deller 2012).
The radio SED of the BH from 1.4 to 340 GHz is shown in Figure 3. In addition to our new ALMA measurements
in the sub-mm regime (see below), we include measurements from the literature including 1.4 GHz data from the LBA
(Reines & Deller 2012), 5 and 8 GHz data from the VLA (Reines et al. 2011), as well as 15, 22, and 33 GHz data
from the VLA (Costa et al. 2021). Here, the flux density at 33 GHz is not included in this analysis because the data
suffered from decorrelation due to weather conditions and the low declination of He 2–10 at this high frequency (Costa
et al. 2021). Therefore, the flux density at 33 GHz is presented with a lower limit (upper arrow) in Figure 3.
The flux densities of the BH in the sub-mm regime were estimated with our reimaged ALMA continuum data.
First, to help mitigate the impact of different beam sizes, we convolved all the continuum images to have the same
synthesized beam size as the lowest one (0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 32 for the 99 GHz image) using the CASA task _imsmooth_ . While
the inherent limitation of interferometry may still result in different spatial sensitivities among the observations, as
well as the omission of large-scale emission, this would not be a major concern if the emission associated with the BH
is point-like. However, if the emission is marginally resolved, we may be missing flux density that could, for example,
lead to the low measurement at 251 GHz seen in Figure 3.
We performed aperture photometry on the sub-mm continuum using an elliptical aperture equivalent to one beam
size centered on the BH position (i.e., 0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 32 with PA=-64.0 _[◦]_ marked with a blue ellipse in Figure 3). The arrow
points to the BH which is shown as a black ellipse. The measured flux densities of the BH are 140 _±_ 14, 134 _±_ 21,
29 _±_ 46, and 57 _±_ 48 _µ_ Jy at 99, 113, 251, and 340 GHz, respectively. Here, it is worth noting that the uncertainty of
the flux density may be underestimated because we measured it as a mean of the RMS noise within an aperture. The
RMS noise maps were produced with the AIPS task _RMSD_ (Greisen 2003), which calculates the RMS of signals after
rejecting signals greater than 3 _σ_ within 150 pixels of each pixel.
Our measurements are consistent with those of Costa et al. (2021) at 113 GHz, but not at 251 and 340 GHz. Costa
et al. (2021) reported flux densities of 70 _±_ 30, 130 _±_ 30 _µ_ Jy at 258 and 340 GHz, respectively, while our measurements
are 29 _±_ 46 and 57 _±_ 48 _µ_ Jy at these frequencies. At 251 GHz, our photometry shows 2.4 times less flux density than
that of Costa et al. (2021). Costa et al. (2021) likely measured the flux density of a point source shown within the
contour in the center of panel (C) of Figure 2. However, this point source is smeared after convolution to the beamsize
of 0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 32 in our measurement, as shown in panel (C) of Figure 3. Since we applied aperture photometry on the
convolved image, we measured a smaller flux density. At 340 GHz, our measurement is 2.3 times fainter than the

ALMA View of Positive Black Hole Feedback in the He 2–10 7





**Figure** **2.** Continuum images at 99 GHz (A), 113 GHz (B), 251 GHz (C), and 340 GHz (D). The central BH is marked with
the black ellipse and red arrow in the 99 GHz continuum image (panel A). White contours represent the 99 GHz continuum at
levels of 50, 100, 150, and 200 _µ_ Jy beam _[−]_ [1] . The beam size in each image is shown as the gray ellipse at the bottom right.


flux density obtained by Costa et al. (2021). This difference is due to the difference in measurements. There are two
continuum sources near the BH position with distances of 0 _[′′]_ _._ 22 (source A) and 0 _[′′]_ _._ 53 (source B) from the BH, as shown
in panel (D) of Figure 3. Their flux densities were measured as 125 _±_ 80 and 342 _±_ 130 _µ_ Jy for the sources A and B,
respectively, using PyBDSF (Mohan & Rafferty 2015). Costa et al. (2021) likely reported the flux density of source A
as that of the BH. Our aperture for the BH does not include source A and source B entirely, but includes a part of

8 Gim & Reines



















**Figure** **3.** Continuum images at 99 GHz (A), 113 GHz (B), 251 GHz (C), 340 GHz (D), and the SED analysis (E). Continuum
images were convolved to have the same synthesized beam size of 0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 32. The central BH is marked with the small black
ellipse indicated by the arrow. The blue ellipse is the aperture of our flux density measurements. The beam size in each image
is shown as the gray ellipse at the bottom right. The source A and B in the 340 GHz continuum image (panel D) are adjacent
sources of the BH. In panel (E), the flux densities are depicted as black data points, with a black arrow indicating the lower
limit at 33 GHz. The best-fit model is represented by a red line, and the 1 _σ_ range of the best-fit model is delineated by the red
shaded region, providing a measure of the model’s uncertainty.


source A, as seen in panel (D) of Figure 3. Therefore, our reported values are more robust than the ones reported by
Costa et al. (2021).
Our measurements have larger uncertainties than those of Costa et al. (2021) at both 251 and 340 GHz. These
larger uncertainties are due to the convolution to the beamsize of 0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 32. The differences in beam area between
the original and convolved images are 6.5 and 2.0 at 251 and 340 GHz, respectively. Convolution to the larger beam
size introduces a larger uncertainty. Quantitatively, the 251 GHz image with the original synthesized beam size of
0 _[′′]_ _._ 18 _×_ 0 _[′′]_ _._ 14 has an RMS noise of 12.4 _µ_ Jy beam _[−]_ [1], but its RMS noise increases to 24.7 _µ_ Jy beam _[−]_ [1] after convolution to
a synthesized beamsize of 0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 32. Similarly, the 340 GHz image has an RMS noise of 27.7 _µ_ Jy beam _[−]_ [1] originally,
but increases to 38.7 _µ_ Jy beam _[−]_ [1] after convolution. Our measurements at 251 and 340 GHz had larger uncertainties,
but it is important to match the beamsizes across the frequencies in order to accurately measure the spectral index.
Additionally, it is important to measure the flux density of the BH at the correct position, rather than the flux density
of a nearby yet different source. As a result, the flux densities we report are more accurately measured than previous
values.

In order to estimate the best-fit parameters and corresponding uncertainties for an SED ranging from 1.4 to 340 GHz,
we employed the R function _nls_ for the non-linear least square fitting and utilized _confint2_ to estimate the uncertainties
of the best-fit parameters. Four models were tested, including i) a three-component model with non-thermal, freefree, and dust emission, _S_ _∼_ _S_ 0 _,nth_ _ν_ _[α]_ _[nth]_ + _S_ 0 _,ff_ _ν_ _[−]_ [0] _[.]_ [1] + _S_ 0 _,dust_ _ν_ [4], ii) a two-component model with non-thermal and
free-free emission, _S_ _∼_ _S_ 0 _,nth_ _ν_ _[α]_ _[nth]_ + _S_ 0 _,ff_ _ν_ _[−]_ [0] _[.]_ [1], iii) a two-component model with non-thermal and dust emission,
_S_ _∼_ _S_ 0 _,nth_ _ν_ _[α]_ _[nth]_ + _S_ 0 _,dust_ _ν_ [4], and iv) a one-component model with non-thermal emission, _S_ _∼_ _S_ 0 _,nth_ _ν_ _[α]_ _[nth]_ . The models
that included dust emission did not yield physical results. The two-component model with non-thermal and freefree emission had large uncertainties and poorly constrained solutions. The one-component model with non-thermal
emission provided a meaningful solution, with the best-fit model of _S_ = (1349 _±_ 217) _ν_ _[−]_ [0] _[.]_ [52] _[±]_ [0] _[.]_ [06] _µ_ Jy, represented by
the red line with a light red shaded region in panel E of Figure 3.


3.2. _Molecular_ _Line_ _Emission_


3.2.1. _Moment_ _Maps_


Moment maps of molecular gas can provide insight into the morphology and kinematics of the gas. Moment maps
were generated using the 3D-Based Analysis of Rotating Objects via Line Observations (3D-Barolo; Di Teodoro &
Fraternali 2015), which employs the Duchamp algorithm to identify pixels above a primary signal-to-noise ratio (S/N)

ALMA View of Positive Black Hole Feedback in the He 2–10 9















**Figure** **4.** Moment maps of CO (1–0), CO (3–2), HCN (1–0), HCO [+] (1–0), and HCO [+] (3–2) from top to bottom. Total
intensity, velocity field, and velocity dispersion maps are shown in the left, middle, and right panels, respectively. The black
contours indicate the flux density of the 99 GHz continuum, corresponding to 50 (5 _σ_ ), 100 (10 _σ_ ), 150 (15 _σ_ ), and 200 (20 _σ_ ) _µ_ Jy
per beam size of 0 _[′′]_ _._ 55 _×_ 0 _[′′]_ _._ 3. The BH is located in the center of the innermost black contour of the continuum. The beam sizes
are marked with solid ellipses in the bottom right corners.

10 Gim & Reines


and agglomerates neighboring pixels above a secondary S/N. The initial moment maps were created by running 3DBarolo on the non-primary beam (PB) attenuation corrected image cubes, and the final moment maps were derived
by multiplying the PB attenuation corrected image cubes by the mask image cubes created during the generation of
the initial moment maps. For this analysis, the primary and secondary S/N were set at 5 and 3, respectively.
In Figure 4, the moment maps of the CO (1–0), CO (3–2), HCN (1–0), HCO [+] (1–0), and HCO [+] (3–2) lines are
shown from top to bottom. The total intensity (moment 0), velocity field (moment 1), and velocity dispersion (moment
2) maps are displayed in the left, middle, and right panels, respectively. The black contours indicate the 99 GHz
continuum, with the BH located at the local maximum between two major blobs of star formation. The moment maps
of the molecular gas lines indicate that there is a significant amount of molecular gas beyond the continuum regions
traced by the black contours. These extended features are consistent with previous observations (Baas et al. 1994;
Beck et al. 2018; Imara & Faesi 2019). Total intensity maps of the molecular gas (left panels of Figure 4) show two
prominent regions corresponding to the strong continuum blobs of Figure 2. The maximum intensities of the molecular
gas in the left panels of Figure 4 coincide with the maximum positions in the continuum. The BH is located between
the two prominent starburst regions in the molecular gas distributions, forming a spur-like structure visible in the
high-resolution CO data. The detection of HCO [+] (1–0), HCO [+] (3–2), and HCN (1–0) above S/N _>_ 5 indicate the
existence of significant dense gas (with critical density ≳ 10 [6] cm _[−]_ [3] ) in the vicinity of the BH.


3.2.2. _Position-Velocity_ _Diagram_


The position-velocity diagram (PVD) serves as a valuable tool for elucidating the kinematics of gas. The ionized
gas in the central region of He 2–10 exhibits a sinusoidal motion in the PVD, which is well fit by the bipolar outflow
model presented in Schutte & Reines (2022). Schutte & Reines (2022) used _HST_ /STIS spectroscopy, employing a long
slit centered on the BH with a width of 0 _[′′]_ _._ 2 and a position angle of 100 _[◦]_ aligned with the ionized filament seen in H _α_
imaging. In our investigation, we look for a similar pattern in the velocities of the molecular gas by generating PVDs
along a line with a position angle of 100 _[◦]_, centered on the BH, from our CO (3–2) and CO (1–0) image cubes. We
extracted PVDs along the line in bins corresponding to the synthesized beam sizes of CO (3–2) and CO (1–0) image
cubes, i.e., 0 _[′′]_ _._ 3 and 0 _[′′]_ _._ 45, respectively. However, these values are more than 3 _×_ larger than the spatial resolution of
the _HST_ /STIS observations ( _∼_ 0 _[′′]_ _._ 1).
Figure 5 illustrates the resulting PVDs for CO (3–2) in panel (A) and CO (1–0) in panel (B). Unlike the ionized gas
observed by Schutte & Reines (2022), no sinusoidal motions were discerned in either PVD. This may be attributed
to the coarser angular resolution of our observations, leading to a beam smearing effect that obscures outflow signals
amid adjacent background emissions. Alternatively, the absence of sinusoidal motion in the molecular gas could signify
a genuine lack of such motion, suggesting a potential insensitivity of the molecular gas to the BH outflow, particularly
if the BH outflow lacks sufficient strength (Koudmani et al. 2022).
We calculated the velocity gradient from the PVD of the CO (3–2) line in panel (A) of Figure 5, leveraging the
smaller beam size of the CO (3–2) image cube compared to that of CO (1–0). We restrict this analysis to the gas in
the central region near the BH between -0 _[′′]_ _._ 4 ( _−_ 18 pc) to 0 _[′′]_ _._ 8 (35 pc) with velocities in the range _∼_ 870–900 km s _[−]_ [1] .
The resulting weighted mean velocity (red squares in Figure 5), determined above 3 _σ_ with a bin width of 0 _[′′]_ _._ 3 (where
_σ_ = 1 _._ 0 mJy beam _[−]_ [1] (1.693 km s _[−]_ [1] ) _[−]_ [1], yielded a velocity gradient of _−_ 5 _._ 8 km s _[−]_ [1] _[′′−]_ [1] . We repeated this analysis for
CO (1–0), constructing a PVD along a line with a position angle of 100 _[◦]_ and a width of 0 _[′′]_ _._ 45 (matching the beam size
of CO (1–0)), resulting in a similar velocity gradient of _−_ 4 _._ 6 km s _[−]_ [1] _[′′−]_ [1] ).
Our derived velocity gradient is shallower than the _−_ 7 _._ 8 km s _[−]_ [1] _[′′−]_ [1] reported by Imara & Faesi (2019). The
discrepancy can be attributed to differences in i) the length of the position axis used to estimate the velocity gradient,
ii) the position angle, and iii) the bin size used to trace gas velocity. Imara & Faesi (2019) estimated the velocity
gradient over a range of -1 _[′′]_ _._ 7 ( _∼_ 70 pc) to 1 _[′′]_ _._ 7 along a line with a position angle of 143 _[◦]_ and a width of 4 _[′′]_ . In our PVD
(Figure 5), molecular gas at approximately 1 _[′′]_ _._ 5 is associated with the western star-forming region, contributing to a
steeper velocity gradient due to its high velocity. The differences in position angle and bin size introduce additional
inconsistencies, particularly given the asymmetrical distribution of molecular gas around the BH.


3.2.3. _Molecular_ _Gas_ _in_ _the_ _Vicinity_ _of_ _the_ _BH_

ALMA View of Positive Black Hole Feedback in the He 2–10 11













**Figure** **5.** PVDs of CO J=3–2 (panel A) and CO J=1–0 (panel B) are presented with the weighted mean velocity in each
position bin above 3 _σ_ (red squares) and the velocity gradient (black lines). The light blue contours indicate 3, 10, and 50 _σ_ in
CO (3–2) and 3, 5, and 10 _σ_ in CO (1–0), respectively. The dotted vertical lines present the regions estimating the velocity
gradient, e.g., -0 _[′′]_ _._ 4 _< x <_ 0 _[′′]_ _._ 8 for CO (3–2) and -0 _[′′]_ _._ 5 _< x <_ 0 _[′′]_ _._ 85 for CO (1–0).


In this work, we are primarily interested in examining the molecular gas in the vicinity of the BH [3] . We define this
region (i.e., the BH vicinity) as follows. There is a distinct velocity gas blob near the BH in HCO [+] (3–2), seen in
the bottom middle panel of Figure 4. The velocity range of this blob is 852.1–904.6 km s _[−]_ [1] in HCO [+] (3–2). To help
isolate the gas in the vicinity of the BH, both spatially and in velocity, we generated moment maps of the molecular
gas tracers with higher angular resolution (CO (1–0), CO (3–2), and HCO [+] (3–2)) within this restricted velocity range
(Figure 6).
The resulting moment maps reveal an elongated CO gas structure with a distinct velocity from the surrounding
regions, as seen in the middle panels of Figure 6. This distinct velocity region is defined as the BH vicinity, represented
by the black ellipse in Figure 6. The ellipse is centered at RA 08 _[h]_ 36 _[m]_ 15.108 _[s]_ and Dec _−_ 26 _[◦]_ 24 _[′]_ 34.343 _[′′]_, with a size


3 The ALMA observations do not have sufficient angular resolution to probe the BH sphere of influence. Given the BH mass of _∼_ 10 6 M _⊙_
(Reines et al. 2016; Riffel 2020), the sphere of influence is _∼_ 4 pc (0 _[′′]_ _._ 1), which is at least three times smaller than the angular resolution
of our observations.

12 Gim & Reines







Right Ascension (J2000) Right Ascension (J2000) Right Ascension (J2000)



**Figure** **6.** Moment maps of the molecular gas species observed at high angular resolution including CO (1–0), CO (3–2), and
HCO [+] (3–2) (top to bottom), where the moment maps are generated with a restrictive velocity range of 852.1–904.6 km s _[−]_ [1] (see
§3.2). The total intensity, velocity field, and velocity dispersion are presented in the left, middle, and right panels, respectively.
The small black contour indicates the position of BH traced by the high brightness temperature radio core detected with the
LBA (Reines & Deller 2012). The outer black ellipse defines the region we refer to as the BH vicinity, which has a near uniform
velocity that is consistent with the systemic velocity of the galaxy, _V_ _sys_ = 873 km s _[−]_ [1] (Kobulnicky et al. 1995).


of 2 _[′′]_ _._ 97 _×_ 0 _[′′]_ _._ 79 ( _≈_ 128 pc _×_ 34 pc) and a position angle of 80.34 _[◦]_ as presented in Table 3. The moment maps in Figure 6
clearly demonstrate that the BH (small black contour) is located north of the BH vicinity (black ellipse) in molecular
gases such as CO and HCO [+] (3–2). In other words, the BH is not at the center of the molecular gas structure. The
lack of the molecular gas to the north of the BH is likely a result of star formation feedback occurring in the young
massive star clusters with ages of _∼_ 4 _−_ 5 Myrs (Beck et al. 2018), as seen in the H _α_ image in Figure 7. This could
help explain why the BH is accreting at such a low Eddington ratio ( _∼_ 10 _[−]_ [6] ; Reines et al. 2016). Furthermore, the
asymmetrical distribution of molecular gas around the massive BH resembles the central molecular zone of the Milky
Way (Bally et al. 1988) and the central region of NGC 253 (Meier et al. 2015; Krieger et al. 2019; Levy et al. 2022). In
the cases of the Milky Way and NGC 253, the origin of this asymmetry is attributed to feedback from star formation
in their centers (Henshaw et al. 2022; Krieger et al. 2019).
We have measured the velocity ranges within the BH vicinity using three different molecular lines: CO J=1–0, CO
J=3–2, and HCO [+] J=3–2. The velocity ranges were found to be 865–899 km s _[−]_ [1], 871–904 km s _[−]_ [1], and 871–904 km
s _[−]_ [1], respectively. Excluding the borders, the velocity ranges for CO J=1–0 and J=3–2 were reduced to 871–886 km

ALMA View of Positive Black Hole Feedback in the He 2–10 13


s _[−]_ [1] and 871–885 km s _[−]_ [1], respectively. The mean velocities within the BH vicinity are 880 _±_ 5 (CO J=1–0), 880 _±_ 6 (CO
J=3–2), and 875 _±_ 6 km s _[−]_ [1] (HCO [+] J=3–2), and are therefore consistent with one another within the uncertainties.
For reference, the systemic velocity of the galaxy is 873 km s _[−]_ [1] (Kobulnicky et al. 1995). The velocity field maps
do not show any significant rotation in the region defined as the BH vicinity. The velocity dispersion map of CO
J=3–2 shows some high velocity dispersion along the SE and NW directions with ∆ _σ_ _≈_ 7 km s _[−]_ [1] . The high velocity
dispersion (∆ _σ_ _≈_ 50 km s _[−]_ [1] ) of stellar motions near the BH observed by Riffel (2020) is not seen in the molecular gas.


**Table** **3.** Properties of molecular gas in the vicinity of the BH (black ellipse in Figure 6)

|Parameter|Value|
|---|---|
|Center coordinate|RA 08_h_ 36_m_ 15.108_s_, Dec _−_26_◦_24_′_ 34.343_′′_|
|Major & minor axes|2_.′′_97_×_0_.′′_79 (_≈_128 pc_×_34 pc)|
|Position angle|83.34_◦_|
|Mean velocity|880.2 _±_ 4.7 km s_−_1 in CO (1–0)<br>880.3 _±_ 5.9 km s_−_1 in CO (3–2)<br>875.3 _±_ 6.2 km s_−_1 in HCO+ (3–2)|
|H2 mass|(0.21–1.53)_×_106 M_⊙_|



The molecular gas mass within the BH vicinity is estimated using the scaling relation between molecular gas mass
_′_
and CO luminosity, M H 2 = _α_ CO L CO [.] [The] [conversion] [factor] _[α]_ _[CO]_ [depends] [on] [the] [metallicity] [(][Bolatto] [et] [al.] [2013][,] [and]
references therein). Cresci et al. (2017) conducted spectroscopic observations with _MUSE_ to determine the metallicity
of He 2–10, with a spatial sampling size of 0 _[′′]_ _._ 2 _×_ 0 _[′′]_ _._ 2. They created a map of metallicity distribution, which revealed
significant variation across the galaxy, largely due to change in ionization parameters. Through simultaneous linefitting on multiple lines, they found that the metallicity in the central region was super-solar, with 12 + [O _/_ H] _≈_ 9 _._ 0,
corresponding to Z = 0 _._ 044. Based on the relationship between _α_ CO and metallicity outlined in Bolatto et al.
(2013), we choose a range of _α_ CO values between 0.6 and 4.3 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1], where _α_ CO = 4 _._ 3 is the
value for the Milky Way. Our range of _α_ CO also includes the widely accepted value for the centers of starburst
galaxies with solar metallicities, _α_ CO _≈_ 1 _._ 1 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] (Leroy et al. 2015; Krieger et al. 2019). These
considerations ensure that our analysis is consistent with established standards in the field. Our estimated CO
luminosity is L _′_ CO [=] [3] _[.]_ [56] _[ ×]_ [ 10] [5] [K] [km] [s] _[−]_ [1] [pc] [2] [,] [which] [when] [combined] [with] [the] _[α]_ [CO] [range,] [results] [in] [an] [estimated]
molecular gas mass of M H 2 = (0 _._ 21 _−_ 1 _._ 53) _×_ 10 [6] M _⊙_ .


3.2.4. _CO_ _Line_ _Ratios_


Line ratios between different molecular gas tracers are good indicators of gas excitation (Privon et al. 2015). The
HCN (1–0) and HCO [+] (1–0) line image cubes have large beam sizes, and the HCO [+] (3–2) line image cube has a
relatively low signal-to-noise ratio, so we restricted our analysis to the line ratio between CO J=1–0 and J=3–2, which
have higher angular resolutions and better sensitivities. Given that the CO (3–2) line emission exhibits a more extended
distribution compared to the CO (1–0) line emission, the distribution of the CO line ratio is constrained by the CO
(1–0) line distribution. The line ratio is defined as R 31 = L CO(3 _−_ 2) _/_ L CO(1 _−_ 0) = ( _ν_ 32 _/ν_ 10 ) _[−]_ [2] (I CO(3 _−_ 2) _/_ I CO(1 _−_ 0) ), where
I CO is the velocity integrated line intensity in units of Jy km s _[−]_ [1] . Both image cubes were convolved to have the same
synthesized beam size of 0 _[′′]_ _._ 45 _×_ 0 _[′′]_ _._ 30 using the CASA task _imsmooth_ . We present the pixel-by-pixel CO line ratio map
in the left panel and an _HST_ H _α_ image (e.g., Schutte & Reines 2022) in the right panel of Figure 7. Our line ratio map
of the central region of the galaxy indicates highly excited CO molecular gas as evidenced by R 31 ≳ 1, exceeding the
typical range observed in the Milky Way, 0 _._ 3 _<_ R 31 _<_ 0 _._ 5 (Leroy et al. 2009; Carilli & Walter 2013). This result aligns
with the findings of Beck et al. (2018), who reported a high flux ratio of S CO(3 _−_ 2) _/_ S CO(1 _−_ 0) = 6 _._ 1 for this galaxy.


3.2.5. _Shocked_ _Molecular_ _Clouds_ _from_ _the_ _BH_ _Outflow_


The discovery of a low-velocity bipolar outflow originating from the BH was reported in ionized gas (Schutte &
Reines 2022). The precession angle and frequency of this outflow were estimated to be in the range of 2 _._ 4 _−_ 6 _._ 1 _[◦]_ and
3 _._ 0 _−_ 7 _._ 5 revolutions per Myr, respectively. Notably, Schutte & Reines (2022) identified several impacts of the BH
outflow, including the stimulation of star formation in the eastern star-forming region, as well as in the dark cloud
(region 5) and the dense clouds within the western star-forming region (region 6). The left panel of Figure 7 reveals

14 Gim & Reines















**Figure** **7.** Left: Pixel-by-pixel line ratio map between CO (3–2) and CO (1–0), _R_ 31 . Right: _HST_ H _α_ plus continuum image
with the same field of view. The BH position is marked with black contours from the LBA 1.4 GHz observations by Reines
& Deller (2012), and the region defined as the BH vicinity is indicated with the orange dashed ellipse. Regions 5 and 6 from
Schutte & Reines (2022) are presented as rectangles with the _HST_ slit position for the ionized gas outflow (Schutte & Reines
2022). The highest line ratios are observed at the interface between the BH outflow and the eastern star forming region, as
well as region 5 to the west of the BH. This implies the cold molecular gas in these regions is shocked by the bipolar outflow,
supporting the case for positive BH feedback.


that the highest R 31 line ratios are observed at the interface between the known ionized gas outflow from the BH and
the eastern star forming region (Schutte & Reines 2022), as depicted in the H _α_ image (right panel of Figure 7). The
line ratio at this interface is R 31 = 2 _._ 7 _±_ 0 _._ 2, while the region defined as the BH vicinity excluding this interface has
_R_ 31 = 1 _._ 3 _±_ 0 _._ 1. Additionally, we detect a high line ratio (R 31 = 2 _._ 5 _±_ 0 _._ 7) to the west of the BH at the boundary of
a dark cloud of gas and dust (region 5 in Figure 7). This region was previously identified by Schutte & Reines (2022)
and exhibits double-peaked optical emission lines, likely due to the other side of the bipolar BH outflow intercepting
dense clouds and pushing them laterally (as is the case with the eastern interface region). The CO line ratio at region
5 is comparable to that of interface between the outflow and the eastern star forming region, consistent with this
scenario. These findings suggest that the molecular gas impacted by the BH outflow to the east and west have both
high density and high kinetic temperature (Carilli & Walter 2013). It is noteworthy that the elevated R 31 may be an
edge effect limited by low flux densities of CO (1–0). Nevertheless, certain regions at the peripheries, particularly in
the northeast and south, exhibit low R 31 values. The presence of these regions implies that the the pixel-by-pixel R 31
values are influenced by the relative distributions of CO (1–0) and CO (3–2) due to some physical origins, rather than
being solely dictated by low CO (1–0) flux densities. Moreover, our derived R 31 values are robust, exhibiting similar
sensitivities, e.g., _σ_ =1.03 mJy beam _[−]_ [1] (1.693 km s _[−]_ [1] ) _[−]_ [1] for CO (1–0) and 1.00 mJy beam _[−]_ [1] (1.693 km s _[−]_ [1] ) _[−]_ [1] for
CO (3–2), respectively. Therefore, the elevated R 31 values observed in this study are not solely constrained by low
CO (1–0) flux densities.
Multiple studies have investigated the occurrence of elevated CO line ratios in different galaxies. Garc´ıa-Burillo
et al. (2014) and Viti et al. (2014) examined the CO line ratio in NGC 1068 and demonstrated that the ratio between
J=3–2 and J=1–0 vary significantly between the circumnuclear disk around the AGN ( _R_ 31 = 2 _._ 7) and the starburst
ring ( _R_ 31 = 1 _._ 2). Furthermore, they observed higher CO line ratios in more active star forming regions compared to
less active ones ( _R_ 31 = 0 _._ 7 _−_ 1 _._ 0). Their analysis suggested that the elevated CO line ratio in the circumnuclear disk is
a result of the AGN-driven outflow. The CO line ratio in IC 5063 was extensively studied by Dasyra et al. (2016) and
Oosterloo et al. (2017). They identified excited molecular gas along the radio jet and noted a higher CO line ratio in
the central region compared to the outer region. For instance, Dasyra et al. (2016) conducted a calculation of the line
ratio between CO (4–3) and CO (2–1), revealing a value of 12 in the robust jet-cloud interacting regions compared
to an average of 5. Oosterloo et al. (2017) demonstrated that _R_ 31 _>_ 1 along the jets as opposed to 0.17 in the disk.
Their study further indicated that the most elevated CO line ratio is proximate to the two radio lobes, implicating the

ALMA View of Positive Black Hole Feedback in the He 2–10 15


shock generated by the outflow as the causative factor (Morganti et al. 2021). More recently, Audibert et al. (2023)
identified a high CO line ratio between J= 3 _−_ 2 and J= 2 _−_ 1, specifically with _T_ _CO_ (3 _−_ 2) _/T_ _CO_ (2 _−_ 1) = 0 _._ 8 in the region
perpendicular to the radio jet, in contrast to the value of 0.4 in other regions within the type-2 QSO Teacup galaxy.
Their findings underscored that this augmented CO line ratio is a consequence of the jet-driven shock interacting with
the molecular gas.
Our observations align with the results reported by Garc´ıa-Burillo et al. (2014), where the _R_ 31 values stand at 2.7
in the circumnuclear disk, 1.2 in starburst regions, and 0.4 _−_ 0.5 in the halo. Consequently, the regions exhibiting high
_R_ 31 values in our study can be attributed to shock heating induced by the BH outflow.


3.2.6. _The_ _Western_ _Star_ _Forming_ _Region_


While prominent at radio wavelengths (e.g., Figure 2), the star-forming region to the west of the BH appears to
suffer from significant extinction at optical wavelengths (e.g., Figures 8 and 7). Schutte & Reines (2022) estimate a
stellar age of _<_ 3 Myr for region 6 (e.g., see Figure 7) based on the equivalent width of the H _α_ emission line. This
is consistent with a scenario in which the star clusters have not had enough time to clear away their birth material,
leading to high levels of extinction. We quantify their assertion with the molecular gas distribution.
Figure 8 presents channel maps of the CO (3–2) line within velocities of 864–888 km s _[−]_ [1] in panels (a) to (o), a
total intensity map in panel (p), an _HST_ I-band image in panel (q), and an _HST_ H _α_ plus continuum image in panel
(r). The total intensity map was produced using 3D-Barolo (Di Teodoro & Fraternali 2015) with a primary S/N of
5 and a second S/N of 3 on the image cube shown in panels (a)–(o). In the channel maps and total intensity map,
the bulk of the gas was masked to enhance contrast and highlight fainter emission. The red boxes (white boxes in
panel r) in each panel of Figure 8 indicate regions 5 and 6 defined by Schutte & Reines (2022), respectively. Figure 8
demonstrates that there is a significant amount of molecular gas between regions 5 and 6, implying that the molecular
gas is abundant enough to absorb the emission from young stellar populations embedded in the gas.
We estimate the optical extinction in this region as follows. The total intensity of the CO (1–0) line within the
span of regions 5 and 6 is measured as W CO(1 _−_ 0) = 788 _._ 2 _±_ 57 _._ 4 K km s _[−]_ [1], resulting in an estimated molecular gas
column density of N(H 2 ) = (2 _._ 21 _±_ 0 _._ 16) _×_ 10 [22] _−_ (1 _._ 58 _±_ 0 _._ 12) _×_ 10 [23] cm _[−]_ [2] . This estimation is derived from the mean
velocity-integrated flux density ratio of CO (3–2) to CO (1–0), represented as I CO(3 _−_ 2) _/_ I CO(1 _−_ 0) = 12 _._ 54 in this region.
The conversion factor X CO = (0 _._ 28 _−_ 2) _×_ 10 [20] cm _[−]_ [2] (K km s _[−]_ [1] ) _[−]_ [1], corresponding to _α_ CO = 0 _._ 6 _−_ 4 _._ 3 _M_ _⊙_ (K km s _[−]_ [1]

pc [2] ) _[−]_ [1], has been employed for this calculation. Kobulnicky et al. (1995) conducted observations of atomic hydrogen
(H I ) using the VLA at D-, C-, and B-arrays. In this region, the total intensity of H I was 1.52 _±_ 0.05 Jy beam _[−]_ [1] km
s _[−]_ [1], leading to a corresponding column density N(H I ) at (1.51 _±_ 0.05) _×_ 10 [18] cm _[−]_ [2], considering a synthesized beam size
of 31 _[′′]_ _×_ 30 _[′′]_ . Assuming a uniform distribution of H I, the optical extinction can be computed using the relationship
between N(H) and A _V_ (Zhu et al. 2017), A V = 4 _._ 81 _×_ 10 _[−]_ [22] (N(HI) + 2N(H 2 )). This calculation yields a range of
A V _∼_ 21 _−_ 152 mag. If the H I is more concentrated in this region, these values would represent lower limits. On the
other hands, the optical extinction is estimated to be A V _∼_ 7 _−_ 51 for the eastern star forming region, supporting that
the optically dark region is predominantly observed between region 5 and 6.
The 251 and 340 GHz images presented in Figure 2 showed that the compact features of region 6 align with peaks
in CO (3–2) and HCO [+] (3–2) shown in Figure 4. This observation is in line with the characteristics of bright and
compact embedded clusters seen in other young clusters, e.g., NGC 253 (Ando et al. 2017; Leroy et al. 2018; Levy
et al. 2021; Mills et al. 2021) and NGC 4945 (Emig et al. 2020). To quantify our findings, we focused on the radio
continuum blob located in the western star-forming region, corresponding to region 6 as defined in Schutte & Reines
(2022). Dust and gas mass estimations were carried out within this region. For the calculation of dust mass, we
utilized the 340 GHz flux density and employed the equation:


_S_ _ν_ _D_ [2]
_M_ _dust_ = (1)

_κ_ _ν_ _B_ _ν_ ( _T_ _d_ )


(Launhardt & Henning 1997). We adopted a dust absorption coefficient of _κ_ _ν_ = 1 _._ 3 cm [2] g _[−]_ [1] at 340 GHz (Costa
et al. 2021) and the dust temperature of 29 K (Santangelo et al. 2009). The measured flux density at 340 GHz is
_S_ 340 _GHz_ = 610 _._ 6 _±_ 30 _._ 0 _µ_ Jy, resulting in a calculated dust mass of (2 _._ 37 _±_ 0 _._ 12) _×_ 10 [3] M _⊙_ . The associated molecular
mass is _M_ H 2 = (7 _._ 79 _±_ 0 _._ 15) _×_ 10 [4] _−_ (5 _._ 65 _±_ 0 _._ 11) _×_ 10 [5] M _odot_ depending on the _α_ _CO_ . Consequently, the dust to
molecular gas mass ratio falls within the range of 1:33–238, which is consistent with the typical value of Milky Way
and other starburst galaxies, 1:120 (Wilson et al. 2008).

16 Gim & Reines



-26°24′32.5″


33.0″


33.5″


34.0″


34.5″


-26°24′32.5″


33.0″


33.5″


34.0″


34.5″


-26°24′32.5″


34.0″


-26°24′32.5″


33.0″


33.5″


34.5″


-26°24′32.5″


33.0″


33.5″


34.5″


35.0″


|(a) 864 .1 km s-1<br>5 6|(b) 865 .8 km s-1|(c) 867 .5 km s-1|
|---|---|---|
|869.1 km s-1<br>(d)|870.8 km s-1<br>(e)|872.5 km s-1<br>(f)|
|(g)<br>874.2 km s-1|(h)<br>875.9 km s-1|(i)<br>877.6 km s-1|
|(j)<br>879.3 km s-1|(k)<br>881.0 km s-1|(l)<br>882.7 km s-1|
|(m)<br>884.4 km s-1|(n)<br>886.1 km s-1|(o)<br>887.8 km s-1|



0.00 0.005 0.01 0.015 0.02 0 2 4 6 8 0 5 10 15 20 25 30 35

Integrated Flux Density [Jy km s [-1] ] Intensity Intensity





















**Figure** **8.** We present the channel maps of the CO (3–2) line within the velocity range of 864.1–887.8 km s _[−]_ [1] . In order to
highlight the faint emission beyond the BH vicinity (indicated by the dashed orange line), we have masked the majority of CO
gas. The 99 GHz continuum emission is depicted by black contours at levels of 50, 100, 200, and 300 _µ_ Jy beam _[−]_ [1] . The BH is
represented by a solid black ellipse, corresponding to the central maximum of the 1.4 GHz continuum observed in _LBA_ (Reines
& Deller 2012). The diagonal dotted lines illustrate the spectroscopic slit used in the _HST_ observations, with a width of 0 _[′′]_ _._ 2.
Additionally, the regions 5 (left) and 6 (right) previously discussed by Schutte & Reines (2022) are depicted by red boxes. The
ALMA beam size is provided in the bottom-right corner of each panel. The bottom row exhibits the total intensity map of the
CO (3–2) line on the left, followed by the _HST_ I-band image in the middle, and the _HST_ H _α_ +continuum image on the right.
In the H _α_ +continuum image (panel r), white contours represent the 99 GHz continuum map, cyan dotted lines depict the slit,
and green boxes highlight regions 5 and 6 for improved visibility.

ALMA View of Positive Black Hole Feedback in the He 2–10 17


The existence of abundant molecular gas and high optical extinction value in the optically dark regions (regions 5
and 6) indicate that the molecular gas in these regions is compressed. In He 2–10, the shock generated by the BH
outflow emerges as the most plausible source for the compression of molecular gas, contributing to the formation of
embedded star clusters. This is an example of the “positive feedback” of the BH outflow.
The asymmetric distributions of molecular gas and embedded star formation provides a key to understanding the
evolution of He 2–10. Given that He 2–10 has experienced a tidal interaction (Kobulnicky et al. 1995), the asymmetric
distributions of molecular gas result from the tidal interaction by disturbing the galaxy potential. This asymmetric
distribution of molecular gas might introduce the asymmetric embedded star formations via the asymmetric gas inflow,
similar to the Central Molecular Zone of the Milky Way (Battersby et al. 2020; Henshaw et al. 2022).


4. CONCLUSIONS


We re-imaged the ALMA archival data of He 2–10 using newly developed algorithms and studied properties of the
continuum and molecular gas, including CO (1–0), CO (3–2), HCN (1–0), HCO [+] (1–0), and HCO [+] (3–2), focusing on
the massive BH and its vicinity. We re-analyzed the radio–sub-mm SED of the BH with updated flux densities and
investigated the kinematics and morphology of molecular gas around the BH. Our main results are summarized below.


  - The radio–sub-mm SED of the BH from 1 _._ 4 _−_ 340 GHz is dominated by synchrotron emission with a best-fit
model of _S_ _ν_ = (1349 _±_ 217) _ν_ _[−]_ [0] _[.]_ [52] _[±]_ [0] _[.]_ [06] _µ_ Jy (Figure 3).


  - We find an elongated molecular gas structure ( _≈_ 128 pc _×_ 34 pc) in the vicinity of the BH with a distinct
velocity component in CO (1–0), CO (3–2), and HCO [+] (3–2) from the surrounding regions (Figure 6). The
mass of the molecular gas structure in the vicinity of the BH is M H 2 = (0 _._ 21 _−_ 1 _._ 53) _×_ 10 [6] M _⊙_ for a range of
metallicity-dependent values of _α_ _CO_ . While the position of the BH is within this region, it is significantly offset
from the peak intensity, which could explain why the BH is accreting at a low rate.


  - The ratio of CO (3–2) to CO (1–0) shows that the CO gas is highly excited in the BH vicinity (Figure 7). The
highest excitation values are located at the interface between the BH outflow and eastern region of triggered star
formation identified by Schutte & Reines (2022). Our results suggest that the molecular gas is being compressed
by the shock produced by the outflow from the BH, providing additional evidence for positive BH feedback.


  - The high excitation of the CO line ratio is also detected to the west of the BH, suggesting the other side of the
bipolar flow is shocking dense molecular clouds in the western star forming region as well. We find high molecular
gas column densities (N(H 2 ) _∼_ 10 [21] _[−]_ [22] cm _[−]_ [2] ) in this region, as well as high levels of extinction ( _A_ _V_ ≳ 2 _−_ 11
mag). This is consistent with a scenario in which the infant star clusters with stellar ages ≲ 3 Myr (Schutte &
Reines 2022) have not yet had enough time to destroy or disperse the dense molecular clouds from which they
formed.


The study presented in this paper constitutes the first investigation of the molecular gas properties in the immediate
vicinity of the massive BH in He 2–10. While our results provide additional support for positive BH feedback, future
observations with higher angular resolution are needed to resolve the sphere of influence of the BH and trace any
potential molecular gas outflow directly. Furthermore, analyzing the higher transitions of the CO molecular gas and
applying models for the photodissociation region (PDR) and/or X-ray dominated region (XDR) will provide additional
information on physical parameters such as density, temperature, and outflow power, ultimately yielding more insight
into the impact of BH feedback on nearby molecular gas.


_Facilities:_ ALMA, VLA, LBA, HST


_Software:_ CASA (Bean et al. 2022), AIPS (Greisen 2003), CARTA (Comrie et al. 2021), R (R Core Team 2022),
3D-Barolo (Di Teodoro & Fraternali 2015)


ACKNOWLEDGEMENT


The authors express their gratitude to the anonymous reviewer for their valuable contributions in enhancing the
quality of this paper. We are grateful to John Hibbard, Loreto Barcos-Munoz, Mark Lacy, Allison Costa, George
Privon at NRAO, Seth Kimbrell, and Sheyda Salehirad at Montana State University for valuable discussions. A.E.R.

18 Gim & Reines


acknowledges support for this work provided by NASA through EPSCoR grant number 80NSSC20M0231. This paper
makes use of the following ALMA data: ADS / JAO.ALMA #2011.0.00348.S, ADS / JAO.ALMA #2012.1.00413.S,
ADS / JAO.ALMA #2015.1.01569.S, ADS / JAO.ALMA #2016.1.00027.S, ADS / JAO.ALMA #2016.1.00492.S,
ADS / JAO.ALMA #2019.1.01641.S. ALMA is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in
cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.
This research has made use of NASA’s Astrophysics Data System Bibliographic Services.


REFERENCES



Allen, D. A., Wright, A. E., & Goss, W. M. 1976, MNRAS,


177, 91, doi: [10.1093/mnras/177.1.91](http://doi.org/10.1093/mnras/177.1.91)


Ando, R., Nakanishi, K., Kohno, K., et al. 2017, ApJ, 849,


81, doi: [10.3847/1538-4357/aa8fd4](http://doi.org/10.3847/1538-4357/aa8fd4)


Audibert, A., Ramos Almeida, C., Garc´ıa-Burillo, S., et al.


2023, A&A, 671, L12, doi: [10.1051/0004-6361/202345964](http://doi.org/10.1051/0004-6361/202345964)


Baas, F., Israel, F. P., & Koornneef, J. 1994, A&A, 284, 403


Bally, J., Stark, A. A., Wilson, R. W., & Henkel, C. 1988,


ApJ, 324, 223, doi: [10.1086/165891](http://doi.org/10.1086/165891)


Battersby, C., Keto, E., Walker, D., et al. 2020, ApJS, 249,


35, doi: [10.3847/1538-4365/aba18e](http://doi.org/10.3847/1538-4365/aba18e)


Bayet, E., Gerin, M., Phillips, T. G., & Contursi, A. 2004,


A&A, 427, 45, doi: [10.1051/0004-6361:20035614](http://doi.org/10.1051/0004-6361:20035614)


Bean, B., Bhatnagar, S., Castro, S., et al. 2022, PASP, 134,


114501, doi: [10.1088/1538-3873/ac9642](http://doi.org/10.1088/1538-3873/ac9642)


Beck, S. C., Turner, J. L., & Consiglio, S. M. 2018, ApJ,


867, 165, doi: [10.3847/1538-4357/aae481](http://doi.org/10.3847/1538-4357/aae481)


Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A,


51, 207, doi: [10.1146/annurev-astro-082812-140944](http://doi.org/10.1146/annurev-astro-082812-140944)


Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105,


doi: [10.1146/annurev-astro-082812-140953](http://doi.org/10.1146/annurev-astro-082812-140953)


Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA:


The Cube Analysis and Rendering Tool for Astronomy,


2.0.0, Zenodo, Zenodo, doi: [10.5281/zenodo.4905459](http://doi.org/10.5281/zenodo.4905459)


Costa, A. H., Johnson, K. E., Indebetouw, R., et al. 2021,


ApJ, 918, 76, doi: [10.3847/1538-4357/ac0e93](http://doi.org/10.3847/1538-4357/ac0e93)


Cresci, G., Vanzi, L., Telles, E., et al. 2017, A&A, 604,


A101, doi: [10.1051/0004-6361/201730876](http://doi.org/10.1051/0004-6361/201730876)


Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016,


A&A, 595, L7, doi: [10.1051/0004-6361/201629689](http://doi.org/10.1051/0004-6361/201629689)


Di Teodoro, E. M., & Fraternali, F. 2015, MNRAS, 451,


3021, doi: [10.1093/mnras/stv1213](http://doi.org/10.1093/mnras/stv1213)


Emig, K. L., Bolatto, A. D., Leroy, A. K., et al. 2020, ApJ,


903, 50, doi: [10.3847/1538-4357/abb67d](http://doi.org/10.3847/1538-4357/abb67d)


Garc´ıa-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A,


567, A125, doi: [10.1051/0004-6361/201423843](http://doi.org/10.1051/0004-6361/201423843)


Greene, J. E., Strader, J., & Ho, L. C. 2020, ARA&A, 58,


257, doi: [10.1146/annurev-astro-032620-021835](http://doi.org/10.1146/annurev-astro-032620-021835)



Greisen, E. W. 2003, in Astrophysics and Space Science


Library, Vol. 285, Information Handling in Astronomy  

Historical Vistas, ed. A. Heck, 109,


doi: [10.1007/0-306-48080-8](http://doi.org/10.1007/0-306-48080-8_7) ~~7~~


Henshaw, J. D., Krumholz, M. R., Butterfield, N. O., et al.


2022, MNRAS, 509, 4758, doi: [10.1093/mnras/stab3039](http://doi.org/10.1093/mnras/stab3039)


Imanishi, M., Nakanishi, K., Tamura, Y., Oi, N., & Kohno,


K. 2007, AJ, 134, 2366, doi: [10.1086/523598](http://doi.org/10.1086/523598)


Imara, N., & Faesi, C. M. 2019, ApJ, 876, 141,


doi: [10.3847/1538-4357/ab16cc](http://doi.org/10.3847/1538-4357/ab16cc)


Johnson, K. E., Brogan, C. L., Indebetouw, R., et al. 2018,


ApJ, 853, 125, doi: [10.3847/1538-4357/aa9ff8](http://doi.org/10.3847/1538-4357/aa9ff8)


Johnson, K. E., & Kobulnicky, H. A. 2003, ApJ, 597, 923,


doi: [10.1086/378585](http://doi.org/10.1086/378585)


Kobulnicky, H. A., Dickey, J. M., Sargent, A. I., Hogg,


D. E., & Conti, P. S. 1995, AJ, 110, 116,


doi: [10.1086/117500](http://doi.org/10.1086/117500)


Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511,


doi: [10.1146/annurev-astro-082708-101811](http://doi.org/10.1146/annurev-astro-082708-101811)


Koudmani, S., Sijacki, D., & Smith, M. C. 2022, MNRAS,


516, 2112, doi: [10.1093/mnras/stac2252](http://doi.org/10.1093/mnras/stac2252)


Krieger, N., Bolatto, A. D., Walter, F., et al. 2019, ApJ,


881, 43, doi: [10.3847/1538-4357/ab2d9c](http://doi.org/10.3847/1538-4357/ab2d9c)


Launhardt, R., & Henning, T. 1997, A&A, 326, 329


Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137,


4670, doi: [10.1088/0004-6256/137/6/4670](http://doi.org/10.1088/0004-6256/137/6/4670)


Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015,


ApJ, 801, 25, doi: [10.1088/0004-637X/801/1/25](http://doi.org/10.1088/0004-637X/801/1/25)


—. 2018, ApJ, 869, 126, doi: [10.3847/1538-4357/aaecd1](http://doi.org/10.3847/1538-4357/aaecd1)


Levy, R. C., Bolatto, A. D., Leroy, A. K., et al. 2021, ApJ,


912, 4, doi: [10.3847/1538-4357/abec84](http://doi.org/10.3847/1538-4357/abec84)


—. 2022, ApJ, 935, 19, doi: [10.3847/1538-4357/ac7b7a](http://doi.org/10.3847/1538-4357/ac7b7a)


Meier, D. S., Turner, J. L., Crosthwaite, L. P., & Beck,


S. C. 2001, AJ, 121, 740, doi: [10.1086/318782](http://doi.org/10.1086/318782)


Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, ApJ,


801, 63, doi: [10.1088/0004-637X/801/1/63](http://doi.org/10.1088/0004-637X/801/1/63)


Mills, E. A. C., Gorski, M., Emig, K. L., et al. 2021, ApJ,


919, 105, doi: [10.3847/1538-4357/ac0fe8](http://doi.org/10.3847/1538-4357/ac0fe8)

ALMA View of Positive Black Hole Feedback in the He 2–10 19



Mohan, N., & Rafferty, D. 2015, PyBDSF: Python Blob

Detection and Source Finder, Astrophysics Source Code
Library, record ascl:1502.007. [http://ascl.net/1502.007](http://ascl.net/1502.007)

Morganti, R., Oosterloo, T., Murthy, S., & Tadhunter, C.

2021, Astronomische Nachrichten, 342, 1135,

doi: [10.1002/asna.20210037](http://doi.org/10.1002/asna.20210037)

Nguyen, D. D., Seth, A. C., Reines, A. E., et al. 2014, ApJ,
794, 34, doi: [10.1088/0004-637X/794/1/34](http://doi.org/10.1088/0004-637X/794/1/34)

Oosterloo, T., Raymond Oonk, J. B., Morganti, R., et al.
2017, A&A, 608, A38, doi: [10.1051/0004-6361/201731781](http://doi.org/10.1051/0004-6361/201731781)

Privon, G. C., Herrero-Illana, R., Evans, A. S., et al. 2015,

ApJ, 814, 39, doi: [10.1088/0004-637X/814/1/39](http://doi.org/10.1088/0004-637X/814/1/39)

R Core Team. 2022, R: A Language and Environment for

Statistical Computing, R Foundation for Statistical

Computing, Vienna, Austria.
[https://www.R-project.org/](https://www.R-project.org/)

Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71,

doi: [10.1051/0004-6361/201117104](http://doi.org/10.1051/0004-6361/201117104)

Reines, A. E. 2022, Nature Astronomy, 6, 26,
doi: [10.1038/s41550-021-01556-0](http://doi.org/10.1038/s41550-021-01556-0)

Reines, A. E., & Deller, A. T. 2012, ApJL, 750, L24,

doi: [10.1088/2041-8205/750/1/L24](http://doi.org/10.1088/2041-8205/750/1/L24)

Reines, A. E., Reynolds, M. T., Miller, J. M., et al. 2016,
ApJL, 830, L35, doi: [10.3847/2041-8205/830/2/L35](http://doi.org/10.3847/2041-8205/830/2/L35)



Reines, A. E., Sivakoff, G. R., Johnson, K. E., & Brogan,


C. L. 2011, Nature, 470, 66, doi: [10.1038/nature09724](http://doi.org/10.1038/nature09724)


Reines, A. E., & Volonteri, M. 2015, ApJ, 813, 82,


doi: [10.1088/0004-637X/813/2/82](http://doi.org/10.1088/0004-637X/813/2/82)


Riffel, R. A. 2020, MNRAS, 494, 2004,


doi: [10.1093/mnras/staa903](http://doi.org/10.1093/mnras/staa903)


Santangelo, G., Testi, L., Gregorini, L., et al. 2009, A&A,


501, 495, doi: [10.1051/0004-6361/200911688](http://doi.org/10.1051/0004-6361/200911688)


Schutte, Z., & Reines, A. E. 2022, Nature, 601, 329,


doi: [10.1038/s41586-021-04215-6](http://doi.org/10.1038/s41586-021-04215-6)


Somerville, R. S., & Dav´e, R. 2015, ARA&A, 53, 51,


doi: [10.1146/annurev-astro-082812-140951](http://doi.org/10.1146/annurev-astro-082812-140951)


Viti, S., Garc´ıa-Burillo, S., Fuente, A., et al. 2014, A&A,


570, A28, doi: [10.1051/0004-6361/201424116](http://doi.org/10.1051/0004-6361/201424116)


Volonteri, M., Habouzit, M., & Colpi, M. 2021, Nature


Reviews Physics, 3, 732, doi: [10.1038/s42254-021-00364-9](http://doi.org/10.1038/s42254-021-00364-9)


Wilson, C. D., Petitpas, G. R., Iono, D., et al. 2008, ApJS,


178, 189, doi: [10.1086/590910](http://doi.org/10.1086/590910)


Zhu, H., Tian, W., Li, A., & Zhang, M. 2017, MNRAS, 471,


3494, doi: [10.1093/mnras/stx1580](http://doi.org/10.1093/mnras/stx1580)


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: archival_reuse",
  "failed_quote": "We downloaded all the data listed in Table 1 from the ALMA archive website ."
 },
 {
  "path": "data.pi_or_archival_as_stated.evidence[0]",
  "value": "Archival data; PIs: Kelsey Johnson, Amy Reines, Nia Imara, Sara Beck, Zhiyu Zhang",
  "failed_quote": "We downloaded all the data listed in Table 1 from the ALMA archive website ."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "1.4 GHz continuum image for astrometric alignment and SED measurement of the BH",
  "failed_quote": "and the 1.4 GHz continuum image observed at the Long Baseline Array (LBA) with a synthesized beam size of 0 ′′ . 11 × 0 ′′ . 03 to estimate the offset."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "Velocity range = 852.1–904.6 km s^-1; ellipse center = RA 08h36m15.108s, Dec -26d24m34.343s, size = 2.97\" x 0.79\" (128 pc x 34 pc), PA = 80.34 deg (or 83.34 deg in Table 3)",
  "failed_quote": "The ellipse is centered at RA 08 h 36 m 15.108 s and Dec − 26 ◦ 24 ′ 34.343 ′′ , with a size of 2 ′′ . 97 × 0 ′′ . 79 ( ≈ 128 pc × 34 pc) and a position angle of 80.34 ◦ as presented in Table 3."
 },
 {
  "path": "analysis_steps[6].method.evidence[2]",
  "value": "Measure CO (1-0) intensity between regions 5 and 6 to derive N(H2) and A_V (combining with VLA N(HI)), and measure 340 GHz continuum flux in region 6 to calculate dust mass and compare with H2 mass.",
  "failed_quote": "For the calculation of dust mass, we utilized the 340 GHz flux density and employed the equation: M dust = S ν D 2 / κ ν B ν ( T d )"
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "High-resolution multi-band ALMA archival observations trace both the sub-mm continuum and multiple molecular gas transitions (CO, HCN, HCO+) in the central ~130 pc around the BH.",
  "failed_quote": "Here we present and analyze high-resolution Atacama Large Millimeter/submillimeter Array (ALMA) observations of He 2–10 with a specific focus on the central massive BH and its immediate surroundings ( ∼ 130 pc)."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "All six ALMA datasets were downloaded from the public ALMA science archive.",
  "failed_quote": "We downloaded all the data listed in Table 1 from the ALMA archive website ."
 }
]
```
