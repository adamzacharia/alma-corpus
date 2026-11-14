# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.193W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# A&A, 687, A193 (2024)https://doi.org/10.1051/0004-6361/202450206 Astronomy
### &
# ⃝c The Authors 2024 Astrophysics

## **Continuum and spectral-line observations of the OH megamaser**

# −
## **galaxy IRAS 01298 0744**

Zhongzu Wu [1], Yulia Sotnikova [2,4], Timur Mufakharov [2,4], Zhiqiang Shen [3], Yongjun Chen [3],
Shouzhi Wang [1], and Jiangfeng Wu [1]


1 College of Physics, Guizhou University, 550025 Guiyang, PR China
e-mail: `[zzwu08@gmail.com](mailto:zzwu08@gmail.com)`
2 Special Astrophysical Observatory of RAS, Nizhny Arkhyz 369167, Russia
3 Shanghai Astronomical Observatory, Chinese Academy of Sciences, 80 Nandan Road, Shanghai 200030, PR China
4 Kazan Federal University, 18 Kremlyovskaya St, Kazan 420008, Russia


Received 2 April 2024 / Accepted 19 April 2024


**ABSTRACT**


We present Very Long Baseline Array observations of radio continuum and OH line emission toward the OH megamaser (OHM)

−
galaxy IRAS 01298 0744. We recover over 82% of the OH line emission seen in single-dish observations, including multiple strong
OH line components and the broad shallow line profile spanning over 1000 km s [−][1] . The OH emission spatially has four compact
components, as well as diffuse emission, and the 3σ signals are distributed in a rectangular region with size of ∼40 × 30 mas. The
spatial-velocity structure is complex and is consistent with that from HCN and HCO [+] lines in the literature, indicating that the nuclear
region of this source is likely still in the merging process characterized by intense nuclear activities. The multiple strong OH peaks are
blue-shifted compared to dense millimetre-wave molecular gas tracers, but similar to optical Na I absorption. This suggests that the
compact masers might be in an outflow driven by an active galactic nucleus or starburst. We have detected compact radio continuum
emissions adjacent to the maser positions with a brightness temperature of around 3 × 10 [6] K, similar to other OHM galaxies with
very-long-baseline interferometry observations in the literature, which is consistent with a starburst origin.


**Key words.** galaxies: active – galaxies: nuclei – galaxies: starburst



**1.** **Introduction**


Hydroxyl megamasers (OHMs) are bright sources of OH maser
emission found in luminous and ultraluminous infrared galaxies
(LIRGs and ULIRGs), which result from interactions and mergers of gas-rich disk galaxies (Sanders & Mirabel 1996). To date,

∼
150 OHMs have been discovered, primarily on the 1667 MHz
main line, while the 1665 MHz main line is generally weak
or absent (see Zhang et al. 2024, and reference therein). OHM
emission is typically thought to be stimulated by far-infrared
radiation from their surroundings and to amplify an intense
background of radio continuum emission.
Meanwhile, the relationship between OH megamasers and
active galactic nucleus (AGN) processes remains unclear, as the
OHM emission may arise from a central AGN, be contaminated
by the emission from circumnuclear star-forming regions, or
occur in an intermediate stage between a starburst and the emergence of an AGN (see Hekatelyne et al. 2018a, 2020).
High-resolution observations are crucial to determining
whether OHM galaxies host an AGN or compact starburst
and their associations with merging stages and environmental factors (Peng et al. 2020). However, due to the low flux
densities of OH megamaser emission, only a limited number of bright OHM galaxies (typically around a dozen) have
been examined using very long baseline interferometry (VLBI)
techniques. Early VLBI observations of OHM galaxies have
unveiled rotating, dusty, molecular structures in various galaxies,
such as Mrk 231 (Klöckner et al. 2003), Arp 220 (Rovilos et al.
2003), III Zw 35 (Trotter et al. 1997), IRAS 17208−0014



(Momjian et al. 2006), and IRAS 12032+1707 (Pihlström et al.
2005). These findings indicate a rotating disc or torus surrounding the nuclear supermassive black holes. Meanwhile,
these high resolutions of OH emission also show additional
activities including inflow/outflow, two rotating discs, or turbulent nuclei (e.g., Pihlström et al. 2005; Momjian et al. 2006;
Hekatelyne et al. 2018a). Furthermore, non-circumnuclear origins for OH maser emissions have also been identified in
IRAS 20100−4156 (see Gowardhan et al. 2018) and Zw049-057
(Aalto et al. 2024). We also observe that the two OH emission
regions of IIzw 096 reside in a dense gas environment, prompting speculation that these OH emission regions might originate from two or more systems (see Wu et al. 2022). Thus, the
velocity structure of known OHM galaxies with high-resolution
observations is complex, indicating that they are experiencing
different merging activities, as OHM emissions are believed
to be produced by major galaxy mergers (Roberts et al. 2021).
Therefore, VLBI observations of bright OH masers from diverse
environments are necessary to better understand the formation
of OH megamasers.
IRAS 01298−0744 exhibits a peak flux density of 118 mJy
in the 1667 MHz line (see Fig. 1) and is the brightest among
all OHMs detected by the Green Bank Telescope (see Willett
2012). The OHM emission peak may be related to low-velocity
outflows, as it is blueshifted from the systematic velocity (see
Fig. 1). The optical image of IRAS 01298−0744 reveals two
prominent tidal tails, indicating a recent merger (Veilleux et al.
2002). Based on the morphology and projected nuclear separation, Yuan et al. (2010) classified it as a compact merger.


A193, page 1 of 12



[Open Access article, published by EDP Sciences, under the terms of the Creative Commons Attribution License (https://creativecommons.org/licenses/by/4.0),](https://www.edpsciences.org)
which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.
[This article is published in open access under the Subscribe to Open model.](https://www.aanda.org/subscribe-to-open-faqs) [Subscribe to A&A to support open access publication.](mailto:subscribers@edpsciences.org)

Wu, Z., et al. : A&A, 687, A193 (2024)



Moreover, Rigopoulou et al. (1999) suggested that it has completed the merger and is evolving into a more relaxed system. Several studies provide evidence of an AGN in the
nuclear region. Yuan et al. (2010) classified this source as
a starburst-AGN composite galaxy based on optical emission lines. According to infrared spectroscopy and bolometric luminosity, this galaxy can be classified as a buried AGN
galaxy (see Imanishi et al. 2011; Nardini et al. 2009). Furthermore, Papaefthymiou et al. (2022) classified this source as a
low-ionisation nuclear emission line region (LINER). Multifrequency Very Large Array (VLA) observations of the radio
continuum emission of this source reveal a gigahertz-peaked
spectrum, indicating that the radio continuum emission arises
from an AGN rather than a starburst (see Hayashi et al. 2021).
The optical redshift of IRAS 01298−0744 is 0.1362
(Soto & Martin 2012). At the distance of this galaxy,
1 mas corresponds to approximately 2.3 pc, assuming _H_ 0 =
73 km s [−][1] Mpc [−][1], Ω M = 0.27, and Ω Λ = 0.73. The primary
objective of this paper is to investigate the high-resolution
properties of OH line and radio continuum emission from
IRAS 01298−0744, and better understand the relationship
between OHM emission and the nuclear region’s environment,
including the merging phase, the presence of a radio AGN, dense
gas, and possible low-velocity outflows. The observations and
data reduction methods are detailed in Sect. 2, and the results
and discussions are presented in Sects. 3 and 4. We summarise
our results in Sect. 5.


**2.** **Observations and data reduction**


We conducted continuum and OH line observations of
IRAS 01298−0744 using the Very Long Baseline Array
(VLBA) for eight hours on August 2, 2022. Nine VLBA antennas
participated in the observation, with the exception of the Kitt
Peak antenna. The pointing position was from VLA images in the
_U_ band in the A configuration (Nagar et al. 2003), and we found
that this position was within 10 mas of our _L_ -band VLBA observation. We observed with two sub-bands centred at 1440.250
and 1696.172 MHz, with each sub-band having a bandwidth of
128 MHz. We employed J0127−0821 as the phase-referencing
calibrator, situated at a separation of approximately 1.53 deg from
the target. The observation durations for the phase-calibrator and
target are roughly one minute and three minutes, respectively,
in each cycle. To resolve the spectral line, a zoomed-in 16 MHz
band with 1000 evenly spaced channels from the first sub-band
centred at 1467.5 MHz, which corresponds to the redshifted
frequency of the OH 1667 MHz line, was utilised. The remaining
bandwidth of the first sub-band and the full bandwidth of the
second sub-band were used for radio-continuum studies (see
Table 1 for additional information on this observation).
To calibrate the VLBA data, we utilised the NRAO Astronomical Image Processing System (AIPS) package. The datareduction process involved several steps, including ionospheric
correction, amplitude calibration, editing, bandpass calibration,
instrumental phase corrections, antenna-based fringe fitting of
the phase calibrator, and application of the solutions to the target source. We also set the velocity using the heliocentric system
with the optical definition for velocity. The calibrated data were
imported into the DIFMAP package (Shepherd 1997) to generate continuum- and spectral-line images. Despite the weak radiocontinuum emission compared to the OH line emission, we also
subtracted the continuum emission using a CLEANed map of
the continuum emission. Additionally, we utilised the ‘Spectral
Profile’ tool in the Common Astronomy Software Application


A193, page 2 of 12



package (CASA; McMullin et al. 2007) to generate and fit OH
line profiles at selected pixels.
In addition to the VLBA observations, we also analysed the
sub-millimetre radio continuum and line emission of this source
from the archival Atacama Large Millimeter Array (ALMA)
project 2017.1.00057.S (PI M. Imanishi). The basic parameters of this project can be found in Table 1. To analyse the
data of the sub-millimetre HCN and HCO [+] lines, we initially
restored the data calibrated by the pipeline and binned the channels to 14 km s [−][1] using the CASA package. These data were
reimaged following the parameters outlined by Imanishi et al.
(2019), specifically employing Briggs weighting with robust =
0.5 and gain = 0.1 settings. The two sub-millimetre emission
lines exhibited similar properties, including the peak velocity,
line width, and emission regions, which were consistent with the
results reported by Imanishi et al. (2019). For our examination
of the sub-millimetre radio-continuum emission, we utilised the
primary-beam-corrected image file of Project 2017.1.00057.S,
which is readily accessible in the ALMA archive.


**3.** **Results**


We generated the OH line profiles by integrating the flux densities over an area of approximately 50 mas squared in each
channel image (see Figs. 1 and 2). The VLBA OH line profile displays multiple strong and narrow components, as well as
broad, shallow OH emission spanning more than 1000 km s [−][1],
similar to what is observed in the single-dish Green Bank Telescope (GBT) line profile. Moreover, the VLBA observation captures over 82% of the integrated flux densities across the velocity
ranges presented in the single-dish GBT profile (see Fig. 1). We
overlaid the OH emission onto an optical _R_ -band Sloan Digital
Sky Survey (SDSS) image and compared it to the HCN emission
and sub-millimetre radio-continuum images (see Fig. 3). We can
see that the OH emission spans a region of <50 mas and is likely
centred on the central region of the galaxy.
The emission of the OH line presents four distinct compact
components, designated as A, B, C, and D, as depicted in Fig. 2.
We employed Gaussian fitting for these components and determined that their sizes are smaller than the beam FWHM, as summarised in Table 1. Additionally, we selected a square region
measuring 50 mas in size to encompass the broader OH emission. Within this region, we extracted spectra for each pixel,
allowing the creation of a velocity field for OH emission (see
Fig. 4). This figure clearly illustrates the presence of higher
velocities, approximately within the range of 40–100 km s [−][1], in
the western portion of the OH emission region. In particular,
multiple peaks were observed in the OH lines, both within the
D region and between components C and B. The OH spectra of
these components, as well as eight additional locations labelled
OH1-8, are shown in Figs. 5 and A.2. We performed line profile
fitting for the four primary components (A, B, C, and D), as well
as for OH5, which exhibited multiple components. The results
of these fits are documented in Table 2. In particular, Component
A displayed the highest emission intensity, featuring five peaks,
including two strong peaks and three weaker ones. The other
components also displayed multiple peaks. For OH1-8, with the
exception of OH5, we used single-peak fitting, and the results
are outlined in Table A.1.

Our VLBA observation has detected radio-continuum emission with a signal-to-noise ratio (S/N) greater than nine, as
illustrated in Figs. 3 and 2. Its peak brightness reached around
0.19 mJy beam [−][1] . To measure the total continuum emission, we
performed a direct fit of calibrated visibilities using an elliptical

Wu, Z., et al.: A&A, 687, A193 (2024)


**Table 1.** Parameters of high-resolution observations.


Epoch Freq. Line/continuum Array Phase calibrator Program ∆ _V_ Beam PA rms
(GHz) km s [−][1] mas × mas ◦ mJy beam [−][1]


2022Aug.02 1.5 OH VLBA J0127−0821 BW144 3.8 12.4 × 5.1 −0.3 1.9
... . . . Continuum . . . . . . . . . – 11.7 × 4.9 −3.5 0.021

2022May30 2.2 Continuum VLBA J0132−0804 BH237D – 8.2 × 2.3 −4.2 0.22
... 8.4 . . . . . . . . . . . . – 2.9 × 1.2 −16.9 0.025

2017Dec.10 233.1–237.9 HCN(3–2) ALMA J0141−0928 2017.1.00057.S 14.2 150 × 120 −55 0.53
... . . . HCO [+] (3–2) . . . . . . . . . . . . . . . . . . 0.47

... . . . Continuum . . . . . . . . . – . . . . . . 0.032













1.1


1







-20









0.9


0.8



0.7


0.6


0.5









V Helio -40000 (km s [-1] )



0 500 1000 1500
V Helio -40000 (km s [-1] )



−
**Fig. 1.** Comparison of OH line with other molecular and atomic line profiles of IRAS 01298 0744. The left panel shows the line profiles of OH
and HCN, while the right panel displays the line profiles of OH and Na I D. The OH line profile obtained from GBT observations by Willett (2012)
is represented by the solid line. The red dash-dotted line represents the integrated VLBA OH line profile extracted from a square region measuring
about 50 × 50 mas and centred at RA:01 32 21.415 Dec:−07 29 08.347, which has been smoothed to about 20 km s [−][1] . The three downward arrows
represent the three peaks of the OH emission profile. The HCN line profiles obtained from ALMA observations (project: 2017.1.00057.S) are
depicted by the dashed black line, which was generated in a circular region (radius ∼150 mas) and has been smoothed to 45 km s [−][1] . The upward
arrow corresponds to the optical system velocity _c_ ∗ _z_ ( _z_ = 0.1362; Soto & Martin 2012). The normalised Na I D spectra from Rupke et al. (2005)
are represented by the black dotted line in the right panel. The _y_ -axis of the OH lines is on the left, while the _y_ -axis of the other lines is on the right
in both panels.



Gaussian model to mitigate potential deconvolution effects
(Martí-Vidal et al. 2014). After obtaining the clean image, we
further integrated over a 50 mas region to determine the radiocontinuum flux. Both techniques provided a flux density close
to 2 mJy. OH regions B and C lie near the continuum emission, but regions D and A are offset by roughly 22 mas (see
Fig. 2). Generally, the uncertainties of the offset between continuum emission and line emission derived from the same data
are only limited by the S/Ns with equation (Tarchi et al. 2011):
σ rel = �(θ line /(2 ∗ SNR line )) [2] + (θ cont /(2 ∗ SNR cont )) [2], where θ
denotes the beam FWHM of the map, and line and cont refer to
line and continuum emission. Based on this equation, we estimate that the error σ rel on the relative positions between component A/D and the continuum emission is about 0.8 mas, which
supports the existence of apparent offset between the peak OHM
emission and radio-continuum emission in this source.


**4.** **Discussion**


Our VLBA observations precisely identified the locations of
compact OH maser sources in IRAS 01298−0744. These sources



In Fig. 1, the OH line profiles present three discernible peaks.
Peaks 1 and 2 are the brightest, with central velocities of
approximately 40 720 km s [−][1] and 40 760 km s [−][1], respectively.
On the other hand, Peak 3 stands alone with a velocity around
40 870 km s [−][1] . The profiles of the OH line at points A, B, C,
and D are depicted in Fig. 5, along with the Gaussian components described in Table 2. In particular, Component A features
its two most radiant line elements, A2 and A3. Components B
and C both present a narrow line feature (B1 and C1 respectively, as indicated in Table 2) and a broader characteristic (B2
and C2, respectively). Component D unveils four line characteristics, with D4 being its most prominent narrow-line element.


A193, page 3 of 12



are situated close to the galaxy’s centre, as observed in the _R_ band SDSS image (see Fig. 3). The OH line emission is primarily concentrated in a region less than 50 mas in size, equivalent to about 116 pc. Within this area, we detected four distinct
bright components and additional diffuse OH emission enveloping them.


_4.1._ _The OH line profile and different OH components_

Wu, Z., et al. : A&A, 687, A193 (2024)



V=40554-40937 km/s


-7°29'08.30"


08.32"


08.34"


08.36"


08.38"


1 [h] 32 [m] 21.418 [s] 21.416 [s] 21.414 [s] 21.412 [s]


RA (J2000)


V=40791.8 km/s



0.008


0.007


0.006


0.005


0.004


0.003


0.002


0.001


0.016


0.014


0.012


0.010


0.008


0.006


[Jy/beam]



1 [h] 32 [m] 21.418 [s] 21.416 [s] 21.414 [s] 21.412 [s]


RA (J2000)


V=40851.8 km/s



V=40709.3 km/s



1 [h] 32 [m] 21.418 [s] 21.416 [s] 21.414 [s] 21.412 [s]


RA (J2000)



-7°29'08.30"


08.32"


08.34"


08.36"


08.38"







0.0250


0.0225


0.0200


0.0175


0.0150


0.0125


0.0100


0.0075


0.0050


[Jy/beam]


0.020


0.018


0.016


0.014


0.012


0.010


0.008


0.006



-7°29'08.30"


08.32"


08.34"


08.36"


08.38"





-7°29'08.30"


08.32"


08.34"


08.36"


08.38"





1 [h] 32 [m] 21.418 [s] 21.416 [s] 21.414 [s] 21.412 [s]


RA (J2000)




[Jy/beam]



**Fig.** **2.** OH line emission maps of IRAS 01298−0744 from VLBA observation. The top left image shows the integrated channel image of OH
emission encompassing velocities from 40 554 to 40 937 km s [−][1] . The other three images depict channel images at three peak velocities, each with
a velocity width of approximately 3.8 km s [−][1], highlighting the brightest components A, B, C, and D. Their respective coordinates are as follows:
A: 01 32 21.415, −07 29 08.346; B: 01 32 21.414, −07 29 08.336; C: 01 32 21.414, −07 29 08.348; D: 01 32 21.415, and −07 29 08.344. The
red and black contours represent the OH line emission (40 554–40 937 km s [−][1] ), with contour levels of 0.72 mJy beam [−][1] × (1, 2, 4, 8), and the radio
continuum emission, with contour levels of 0.06 mJy beam [−][1] × (1, 2), respectively. The colour bar on the right of each figure shows the OH line
flux densities at each pixel in Jy beam [−][1] . The synthesised beam of each channel image is shown in the bottom left corner.



Furthermore, two specific areas, the region between C and B and
the region D itself, display OH line profiles with two or more
evident peaks, as shown in Fig. 4.
Based on refractive interstellar scintillation models,
Darling & Giovanelli (2002) suggested that the size scales of
narrow OH line features should be less than 2 pc if they exhibit
variability and a few parsecs if they remain quiescent. By
comparing the peaks in the single-dish profile (peaks 1–3 in
Fig. 1) with the line profiles derived from different pixels in the
VLBA image (see Figs. 5 and A.2), our results suggest that the
narrow-line features observed in the single-dish OH spectrum
may not originate from a single bright component. Instead, they
may result from multiple compact components and may also
include contributions from diffuse OH emissions. Moreover,
the broad line feature is present in all four regions and their
surroundings (see Fig. A.2). These broad line profiles at each
pixel might mean that the beam size is not enough to resolve the
OH clouds at a particular velocity. An alternate scheme is that
the clouds of similar velocities cover a broad area. In that case,


A193, page 4 of 12



the multiple OH lines and the broad OH line profiles at various
spots may be due to the overlapping of OH clouds at different
velocities.
Generally, the brightness in a VLBI image is derived from
measurements of antenna gains and system temperatures. These
measurements carry uncertainties ranging from about ±10% to
15% (see ‘uncertainties in VLBI data’ in the EVN data reduction guide [1] ). In Fig. 1, the OH line profile from our VLBA
observation aligns fairly well with the GBT measurement. However, the VLBA spectrum exhibits values that are approximately
20% lower at the flux-density peaks. This discrepancy might be
attributed to calibration uncertainties. Yet, it is also feasible that
the OH emission has been slightly resolved in the VLBA channel
images.
In addition to the distinct, narrow line peaks, the GBT OH
line profile also exhibits a broad, shallow feature that spans over
1000 km s [−][1] . The OH line profile from our VLBA observation


1 `[https://www.evlbi.org/evn-data-reduction-guide#](https://www.evlbi.org/evn-data-reduction-guide#)`

-7°29'03"


06"


09"


12"



Wu, Z., et al.: A&A, 687, A193 (2024)


-7°29'08.0"


08.2"


08.4"


08.6"


08.8"



32 m



m 21.44 s



s



21.42 s


RA (J2000)



21.40 s



21.38 s



h



s



21.4 s



21.2 s



1 h



m



32



m



21.6



1



RA (J2000)



**Fig. 3.** OH emission overlaid on multi-band images of IRAS 01298−0744. Left panel: blue contours indicate the Very Large Array Sky Survey
(VLASS, Lacy et al. 2020) continuum emission (with contour levels of 0.33 mJy beam [−][1] × (1, 2, 4)) superposed on an SDSS _R_ -band grey image.
Right panel: dashed lines show continuum emission from ALMA observations at 235 GHz, with contour levels of 0.1 mJy beam [−][1] × (1,2,4), while
the solid contours represent HCN line emission ( _J_ = 3−2) with levels of 0.23 mJy beam [−][1] × (1, 2, 4, 8, 16). As the OH emission region is relatively
small when compared to the two images, the red star in both images denotes the location of the OH emission, identified by the coordinates RA: 01
32 21.415 and Dec: −07 29 08.347.


× 10 [4]

300



08 [s] .32


08 [s] .33


08 [s] .34


08 [s] .35


-07 [d] 29 [m] 08 [s] .36



01 [h] 32 [m] 21 [s] .416 21 [s] .415 21 [s] .414

RA (J2000)



08 [s] .32


08 [s] .33


08 [s] .34


08 [s] .35


-07 [d] 29 [m] 08 [s] .36



















4.095


4.09


4.085


4.08


4.075


4.07


4.065


km/s





250


200


150


100


50


km/s









01 [h] 32 [m] 21 [s] .416 21 [s] .415 21 [s] .414

RA (J2000)



**Fig.** **4.** Velocity (left panel) and FWHM line-width distributions (right panel) of OHM emission from our VLBA observation. A, B, C, and D
represent the locations of four bright OH components. The numbers 1–8 represent the example pixel from which we extracted OH line profiles.
The ellipse at the bottom left of each panel represents the synthesised beam of each channel image. The contours indicate the OH emission
channel image at _V_ = 40709.3 km s [−][1] at levels of 0.005 Jy beam [−][1] *(1,2,4,8. . . ). The blue spots indicate where the extracted spectra show two or
more peaks, roughly distributed in regions around component D and between B and C.



aligns with the GBT profile throughout the velocity range. Our
high-resolution findings indicate that the expansive OH line profiles in this source arise from a masing region, characterised by
a confidence level of 3σ within a rectangular area that approximately measures 40 × 30 mas, as deduced from Fig. 4. This
equates to an area of approximately 92 × 69 pc, which aligns
with the idea that OH maser emissions are primarily localised
within a radius of 100 pc in the nucleus (see Hess et al. 2021,
and reference therein).


_4.2._ _Comparing OH with sub-millimetre line emission_


Generally, OHM formation appears to be related to dense
molecular gas, as evidenced by dense gas tracers such as
HCN and HCO [+] (see Darling 2007; Huang et al. 2018). HCN
and HCO [+] line emissions from IRAS 01298−0744 have been



detected by Imanishi et al. (2019). The full widths at halfmaximum (FWHMs) of the two lines are 621 and 634 km s [−][1],
respectively, making this galaxy among the broadest in a
selected sample of 26 nearby ULIRGs at _z_ < 0.15 in
Imanishi et al. (2019).
Our VLBA observation shows that both OH-line and radiocontinuum emissions coincide with dense HCN emission (see
Fig. 3). However, a significant portion of the OH emission occurs
at considerably lower velocities compared to the molecular line
emission. The HCN and HCO [+] lines likely contain a minor
blueshifted component, while the OH emission is consistent with
this dense gas component (see Figs. 1 and A.1). Therefore, the
OH emission may share a similar origin with the blueshifted
dense-gas component, possibly originating in a different region
or displaying distinct kinetic properties in comparison to the
dominant dense gases.


A193, page 5 of 12

4.04 4.06 4.08 4.10 4.12

V helio ( × 10 [4] km s [-1] )


4.04 4.06 4.08 4.10 4.12

V helio ( × 10 [4] km s [-1] )



Wu, Z., et al. : A&A, 687, A193 (2024)


50


40


30


20


10


0



50


40


30


20


10


0


50


40


30


20


10


0





50


40


30


20


10


0





4.04 4.06 4.08 4.10 4.12

V helio ( × 10 [4] km s [-1] )


4.04 4.06 4.08 4.10 4.12

V helio ( × 10 [4] km s [-1] )



50


40


30


20


10


0


4.04 4.06 4.08 4.10 4.12

V helio ( × 10 [4] km s [-1] )


**Fig.** **5.** OH emission lines extracted at four bright compact spots of IRAS 01298−0744 (see Fig. 4). The OH line profiles are fitted with two or
more Gaussian components, and the upper spectrum of each panel shows the residual spectrum (data-model), which are plotted with an offset
(+44 mJy) for clarity.



_4.3._ _The velocity structure and merging activities_


Generally, OHMs are products of gas-rich major mergers (see
Roberts et al. 2021). The optical image of IRAS 01298−0744
shows two prominent tidal tails, which are indicative of a recent


A193, page 6 of 12



merger (Veilleux et al. 2002; Yuan et al. 2010). Optical emission lines suggest rotation in the central and northern regions of
the disc (Soto & Martin 2012). Furthermore, Rigopoulou et al.
(1999) speculated that this source has completed the merger and
is gradually evolving into a more relaxed system.

Wu, Z., et al.: A&A, 687, A193 (2024)


**Table 2.** OH line spectrum of the components in IRAS 01298-07.


Components Major Minor PA Line Amplitude Center _FWHM_ Area
(mas) (mas) ( [◦] ) mJy beam [−][1] km s [−][1] km s [−][1] mJy beam [−][1] *km s [−][1]


A <6.7 <2.2 – 1 4.8 ± 0.7 40 663 ± 25 139 ± 41 711 ± 229

2 28 ± 2 40 704 ± 1 28 ± 2 815 ± 77

3 24 ± 2 40 745 ± 1 39 ± 3 998 ± 125

4 6 ± 1 40 795 ± 2 17 ± 5 104 ± 38

5 3.7 ± 0.7 40 860 ± 4 44 ± 11 173 ± 54

B 7 ± 2 4 ± 1 16 1 5 ± 1 40 697 ± 3 33 ± 8 159 ± 51

2 5.7 ± 0.6 40 718 ± 6 180 ± 14 1100 ± 140

C 8 ± 3 3 ± 2 148 1 3.3 ± 0.6 40 745 ± 13 198 ± 26 692 ± 153

2 7.2 ± 0.8 40 784 ± 2 48 ± 7 368 ± 67

D 6 ± 1 2 ± 1 15 1 8 ± 1 40 703 ± 2 31 ± 5 259 ± 55

2 3.3 ± 0.7 40 722 ± 13 224 ± 36 793 ± 205

3 5 ± 1 40 748 ± 3 32 ± 9 170 ± 58

4 12 ± 1 40 856 ± 1 27 ± 3 334 ± 42

OH5 – – – 1 5.0 ± 0.8 40 701 ± 3 36 ± 7 192 ± 50

2 7.9 ± 0.5 40 786 ± 3 82 ± 8 686 ± 81


**Notes.** Columns (1) and (2): emission components; Cols. (3)–(6): the Gaussian-fitted model parameters.



We find that the OH emission is predominantly concentrated
towards the central region of the nucleus, potentially slightly
offset to the eastern portion of the nucleus (see Fig. 3). Additionally, the velocity structure of the OH emission in this source
is depicted in Fig. 4. Notably, both the western section of the
nucleus and the edge of its eastern section display marginally
higher velocities, with the most luminous region around point A
exhibiting the bluest peak velocity. The velocity maps derived
from the HCN and HCO [+] lines, peaking at velocities 200 km s [−][1]
higher than the OH line (ranging from 40 900 to 41 100 km s [−][1] ),
have been presented by Imanishi et al. (2019). These maps reveal
that the edge of the nucleus’s western part possesses the highest peak velocity. Moreover, there is no clearly ordered velocity
field (see Fig. 12 in Imanishi et al. 2019). Therefore, the velocity
structures derived from the OH, HCN, and HCO [+] lines appear to
be intricate, different from the ordered velocity structures identified in other OHM galaxies in the existing literature (for more
details, see Pihlström 2007, and the references therein). In conclusion, our findings suggest that the central nuclear region of
this galaxy might still be experiencing a merging phase characterized by intense nuclear activities, such as outflows or inflows.
This phase has yet to reach its final relaxed state.


_4.4._ _The nature of the continuum emission and association_

_of the OH line_


Multi-frequency VLA observations of IRAS 01298−0744 display typical non-thermal emission features that are characteristic of AGNs, including a gigahertz-peaked spectrum steepening towards higher frequencies (see Hayashi et al. 2021). Our
VLBA observation detected radio-continuum emission with a
peak flux density of 0.19 mJy beam [−][1] and a total flux density
of approximately 2 mJy (see Sect. 3). This accounts for only half
of the total flux densities observed from the NRAO VLA Sky
Survey (NVSS; Condon et al. 1998). The radio-continuum emission (>3σ) is confined to a region with a diameter of less than
30 mas. Similarly, this emission fits a component size of roughly
50 × 20 mas with a position angle of −30 [◦] . The OH emission
appears to be distributed within a boxy region measuring approximately 40 × 30 mas. Given that only half of the radio-continuum



emission was detected in our VLBA observation, and over 80%
of the OH line emission was captured, it is plausible that the
radio-continuum emission is less compact than the OH emission,
possibly spanning larger scales than the OHM emission.
The estimated brightness temperature of the radio continuum emission (∼3 × 10 [6] K) is consistent with clustered supernova remnants and/or luminous radio supernovae, supporting
a starburst origin for the emission (see Momjian et al. 2006;
Pihlström et al. 2005, and references therein). We also tried
to find compact radio-continuum emission from the archival
VLBA project BH237D (see Table 1). The dirty images from
the VLBA observations at _S_ and _X_ bands are presented in
Fig. A.3. As the _S_ -band VLBA radio-continuum emission could
be comparable to our _L_ -band VLBA observation (approximately
0.2 mJy beam [−][1] ), the non-detection in the _S_ -band image is likely
due to the high noise level (0.19 mJy beam [−][1] ). The _X_ -band image
likely shows a feature at the 4σ level with a peak of about
0.1 mJy beam [−][1] (the prominent feature near the western edge of
the VLBA _L_ -band radio contour, see the right panel of Fig. A.3);
we estimate that the brightness temperature is about 8.7 × 10 [5] K,
which is consistent with the results from our _L_ -band VLBA
observation. These results support the starburst origin of OHMs.
Generally, the radio emission from (U)LIRGs at low
frequencies may experience significant optical depth effects
due to free-free absorption and/or synchrotron self-absorption
(e.g., Leroy et al. 2011; Hayashi et al. 2021). Consequently, the
observed brightness temperature at 1.5 GHz might be underestimated, representing only a lower limit. Additionally, the characteristics of radio AGN cores and jet components in nearby
(U)LIRGs are likely compact, with physical scales of several parsecs, or even sub-parsec scales (e.g., Lonsdale et al.
2003; Pérez-Torres et al. 2010; Romero-Cañizales et al. 2017).
These scales might correspond to less than 4 mas for
IRAS 01298−0744. Although VLBA _X_ -band observations have
suitable resolution to identify potential compact features, the S/N
of the compact feature is low (approximately 4), which may also
stem from calibration errors (see the right panel of Fig. A.3).
Thus, further high-sensitivity and high-resolution VLBI observations of the radio-continuum emission are essential to conclusively confirm or reject the existence of the compact component


A193, page 7 of 12

Wu, Z., et al. : A&A, 687, A193 (2024)



as a plausible radio core or jet component associated with the
radio AGN in IRAS 01298−0744.


_4.5._ _The possible physical scheme of OH emission in_
_IRAS 01298_ − _0744_


4.5.1. The outflowing activities and OHM emission


Generally, OH line profiles often exhibit multiple components
that can be attributed to a combination of gas-rotation, inflow,
and outflow processes (see Pihlström et al. 2001; Momjian et al.
2006). Alternatively, they may be primarily related to outflow
and inflow activities near the central AGN (see Gowardhan et al.
2018; Hekatelyne et al. 2018a). Our results suggest that the
dominant OH emission in IRAS 01298−0744 may originate
from outflows, based on the following evidence. First, the peak
OH emission is blueshifted compared to the systemic velocity, inferred from optical and dense gas tracers. Also, the
velocity range of the brightest OH line components is similar to the blueshifted component seen in dense gas tracers
(see Figs. 1 and A.1). Second, Rupke et al. (2005) identified a
broad and blueshifted Na I D interstellar absorption feature in
IRAS 01298−0744, which is likely attributed to the presence
of a superwind in this infrared-luminous galaxy. The Na I D
absorption feature is indicative of neutral gas, and its presence
is believed to unambiguously indicate the outflow of gas (see
Rupke et al. 2005). Given that the OH velocities align with the
Na I D absorption feature (as depicted in Fig. 1), it suggests that
the OH emission might share a common origin with the Na I D
absorption feature. This supports the scheme that the OH gas is
also moving outward from the central region.
The third factor is that Imanishi et al. (2019) found that there
are regions with enhanced HCN-to-HCO [+] flux ratios near the
western nucleus of IRAS 01298−0744, which may be due to
shocks related to the outflow. We find a broad component of
OH emission across all bright OH regions, and this component
has an FWHM of 200 km s [−][1] (see Fig. 5 and Table 2), consistent with the shock component from optical line profiles of
the nuclear region (see Soto & Martin 2012), which displays an
FWHM of 177 km s [−][1] . In addition to the shock component, the
optical line emission also shows a broad line feature with an
FWHM of about 447 km s [−][1], and the full velocity ranges are
more than 1000 km s [−][1], which is similar to the OH, HCO [+], and
HCN line profiles present in Figs. 1 and A.1. Soto & Martin
(2012) attribute the broad profiles to H ii emission or shocks.


4.5.2. Comparison with the knowledge of OHM emission in
the literature


VLBI observations of about a dozen bright OHM galaxies
have revealed that the OHM maser emission regions are generally compact, typically ∼100 pc in their extent (see Hess et al.
2021; Wu et al. 2023, and reference therein). Two different
types of OH emission (diffuse and compact emission) are commonly observed. Our high-resolution VLBA observations of
IRAS 01298−0744 show that the OH maser emission is also
spread over a nearly 100 pc region centred on the nucleus.
Although a small fraction of the emission might be diffuse,
most are found in several compact components <6.8 × 2.5 mas
(1 mas ∼ 2.3 pc) in size (see Sect. 3). These properties of OH
emission agree well with those of other OHMs with VLBI observations in the literature.
The prevailing model for OH megamasers is that they
are pumped by far-infrared radiation and are low-gain unsat

A193, page 8 of 12



urated amplifiers of the background radio continuum (Baan
1985). This model can generally account for diffuse OH megamaser emission, and the compact OH maser can be further
explained by a refined standard model with clumpy-ring maser
geometry, such that compact OH masers are caused by an
overlapping effect along the line of sight (Parra et al. 2005;
Lockett & Elitzur 2008). The observational findings indicate that
IRAS 01298−0744 may exhibit shocks, with the bright compact OH emission possibly stemming from the outflowing gas
(see Sect. 4.5.1). Typically, galaxies hosting outflowing sources
tend to exhibit a more face-on orientation compared to others
(see Heckman et al. 2000). As a result, the face-on alignment
of the disc/torus in the central region could lead to a lack of
prominent high optical depth tangent points within the inclined
disc/torus (see Lockett & Elitzur 2008), potentially explaining
the absence of bright OH emission associated with systemic
velocity in IRAS 01298−0744.
Based on the velocity structure of IRAS 01298−0744, we
propose a simplified scheme regarding the OHM emission in
IRAS 01298−0744. It is suggested that merging or outflow activities have generated clouds with varying velocities distributed
within a region approximately 100 pc in size. These clouds
become mixed together, leading to the observation of broad,
shallow-line profiles consistent with dense gas tracers. Meanwhile, the narrow, bright, compact OH maser emission may arise
from denser gas clouds along our line of sight, either due to a
longer gain path or the overlapping of denser gas clouds that are
slowly moving along our line of sight. Thus, while the OH line
emission is associated with dense gas, the brightest OH emission may not only be correlated with dense gas emission, but it
may also be influenced by the possible overlapping geometry of
the OH clouds, which can provide sufficient gain length, such
as inclined discs/tori, inflows, and outflows. A hypothesis proposed that the OH megamaser traces a phase in a galaxy where
the AGN is being triggered (see Hekatelyne et al. 2020, 2018a,b;
Sales et al. 2019, and references therein); it is possible that a particular geometry for the formation of bright compact OHM emission is more likely, such as the inclination of the disc/torus and
the inflows or outflows along our line of sight.
Approximately 80% of (U)LIRGs show no OHM activity (Roberts & Darling 2024a). There is no optical nuclear
distinction between masing and non-masing (U)LIRGs
(Roberts & Darling 2024a; Darling & Giovanelli 2006), and
there are also no discernible differences in radio-continuum
properties between masing and non-masing (U)LIRGs (Wu et al.
2023). Darling (2007) demonstrated that OHMs have significantly higher average dense gas fractions than non-masing
ULIRGs, while Roberts & Darling (2024b) scrutinised this
hypothesis with a sample size three times larger than the
original sample and showed that it fails to differentiate between
masing and non-masing ULIRGs in a diverse population. This
suggests that the mechanism of OH megamaser emission and
dense gas emission may not be entirely the same. Dense gas
emissions must be concentrated and massive to achieve the
mean density required to form an OHM in a galactic nucleus
(Darling 2007). The spatial alignment of OHM emission and

−
dense gas emission in IRAS 01298 0744 suggests a correlation
between them. While compact OH megamasers may also rely
on particular geometries that provide a sufficient gain path along
our line of sight (Parra et al. 2005), the differing peak velocities
of the OH emission and dense gas in IRAS 01298−0744 may
support distinct geometries for OH megamaser emission and
dense gas emission. It is noteworthy that high-resolution observations of OHM galaxies and dense gas emissions are scarce

Wu, Z., et al.: A&A, 687, A193 (2024)



in the literature, highlighting the importance of expanding the
sample size to ascertain their correlations.


**5.** **Summary**


We present our findings from the VLBA observations of
IRAS 01298−0744, focusing on its radio-continuum and OH
line emission. Our results are summarised as follows.
First, we detected OH emission on parsec scales, consisting
of four compact components (A, B, C, and D) and diffuse emission distributed in a region smaller than 50 mas (i.e., less than
116 pc). All of these components are smaller than the observation beam. The total OH emission recovered in our VLBA
observation is at least 82% of the flux density of single-dish
GBT observations. The ’missing’ 18% of the single-dist flux
density could be accounted for with absolute flux-scale calibration differences and/or some large-scale emission resolved by
our shortest interferometer baselines. Each bright narrow peak
in IRAS 01298−0744 in the single-dish OH spectrum might not
only be related to one single compact feature, but it is also likely
caused by an accumulation of more than one compact component, as well as diffuse components.
Second we found a slightly higher peak OH velocity at the
western and eastern edges of the source. The velocity range
of the dominant OH emission (from peak 1 to 2) is consistent with the deepest absorption Na I D profiles. Taking
into account these characteristics, we propose that the compact OH emission in this galaxy may be indicative of a lowvelocity outflow, similar to what has been observed in Zw049057 (Aalto et al. 2024), IRAS 20100−4156 (Gowardhan et al.
2018), and IRAS F23199+023 (Hekatelyne et al. 2018a). This
suggests the potential existence of a subgroup of OHM galaxies where compact OH emissions primarily stem from nuclear
outflows rather than from a disc or torus-ring structure.
Third, we measure the brightness of the 1.4 GHz radio continuum emission of approximately 3 × 10 [6] K. Our VLBA observations reveal that the total radio continuum emission is approximately 2 mJy. These results are consistent with previous observations of OHM galaxies using VLBI, which suggest a starburst
origin for radio continuum emission in OHM galaxies.


_Acknowledgements._ We thank an anonymous referee for useful suggestions and
comments that helped to improve the paper. This work is supported by NSFC
grants (Grant No. 12363001,U1931203). The National Radio Astronomy Observatory is operated by Associated Universities, Inc., under a cooperative agreement with the National Science Foundation.


**References**


[Aalto, S., Lankhaar, B., Wethers, C., Moldon, J., & Beswick, R. 2024, in Cosmic](http://linker.aanda.org/10.1051/0004-6361/202450206/1)
Masers: Proper Motion Toward [the](http://linker.aanda.org/10.1051/0004-6361/202450206/1) Next-Generation Large Projects, eds. T.
Hirota, H. Imai, K. Menten, & Y. Pihlström, 380, 40
[Baan, W. A. 1985, Nature, 315, 26](http://linker.aanda.org/10.1051/0004-6361/202450206/2)
[Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693](http://linker.aanda.org/10.1051/0004-6361/202450206/3)
[Darling, J. 2007, ApJ, 669, L9](http://linker.aanda.org/10.1051/0004-6361/202450206/4)
[Darling, J., & Giovanelli, R. 2002, ApJ, 569, L87](http://linker.aanda.org/10.1051/0004-6361/202450206/5)
[Darling, J., & Giovanelli, R. 2006, AJ, 132, 2596](http://linker.aanda.org/10.1051/0004-6361/202450206/6)



Gowardhan, A., Spoon, H., Riechers, D. A., et al. 2018, ApJ, 859,
[35](http://linker.aanda.org/10.1051/0004-6361/202450206/7)
[Hayashi, T. J., Hagiwara, Y., & Imanishi, M. 2021, MNRAS, 504, 2675](http://linker.aanda.org/10.1051/0004-6361/202450206/8)
Heckman, T. M., Lehnert, M. D., Strickland, D. K., & Armus, L. 2000, [ApJS,](http://linker.aanda.org/10.1051/0004-6361/202450206/9)
[129, 493](http://linker.aanda.org/10.1051/0004-6361/202450206/9)
[Hekatelyne, C., Riffel, R. A., Sales, D., et al. 2018a, MNRAS, 474, 5319](http://linker.aanda.org/10.1051/0004-6361/202450206/10)
[Hekatelyne, C., Riffel, R. A., Sales, D., et al. 2018b, MNRAS, 479, 3966](http://linker.aanda.org/10.1051/0004-6361/202450206/11)
[Hekatelyne, C., Riffel, R. A., Storchi-Bergmann, T., et al. 2020, MNRAS, 498,](http://linker.aanda.org/10.1051/0004-6361/202450206/12)
[2632](http://linker.aanda.org/10.1051/0004-6361/202450206/12)

[Hess, K. M., Roberts, H., Dénes, H., et al. 2021, A&A, 647, A193](http://linker.aanda.org/10.1051/0004-6361/202450206/13)
[Huang, Y., Zhang, J., Liu, W., & Xu, J. 2018, J. Astrophys. Astron., 39, 34](http://linker.aanda.org/10.1051/0004-6361/202450206/14)
[Imanishi, M., Imase, K., Oi, N., & Ichikawa, K. 2011, AJ, 141, 156](http://linker.aanda.org/10.1051/0004-6361/202450206/15)
[Imanishi, M., Nakanishi, K., & Izumi, T. 2019, ApJS, 241, 19](http://linker.aanda.org/10.1051/0004-6361/202450206/16)
[Klöckner, H.-R., Baan, W. A., & Garrett, M. A. 2003, Nature, 421, 821](http://linker.aanda.org/10.1051/0004-6361/202450206/17)
[Lacy, M., Baum, S. A., Chandler, C. J., et al. 2020, PASP, 132, 035001](http://linker.aanda.org/10.1051/0004-6361/202450206/18)
[Leroy, A. K., Evans, A. S., Momjian, E., et al. 2011, ApJ, 739, L25](http://linker.aanda.org/10.1051/0004-6361/202450206/19)
[Lockett, P., & Elitzur, M. 2008, ApJ, 677, 985](http://linker.aanda.org/10.1051/0004-6361/202450206/20)
[Lonsdale, C. J., Lonsdale, C. J., Smith, H. E., & Diamond, P. J. 2003, ApJ, 592,](http://linker.aanda.org/10.1051/0004-6361/202450206/21)
[804](http://linker.aanda.org/10.1051/0004-6361/202450206/21)
[Martí-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563,](http://linker.aanda.org/10.1051/0004-6361/202450206/22)
[A136](http://linker.aanda.org/10.1051/0004-6361/202450206/22)
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in
Astronomical Data Analysis Software and Systems XVI, eds. R. A. Shaw,
[F. Hill, & D. J. Bell, ASP Conf. Ser., 376, 127](http://linker.aanda.org/10.1051/0004-6361/202450206/23)
Momjian, E., Romney, J. D., Carilli, C. L., & Troland, T. H. 2006, ApJ, 653,
[1172](http://linker.aanda.org/10.1051/0004-6361/202450206/24)
[Nagar, N. M., Wilson, A. S., Falcke, H., Veilleux, S., & Maiolino, R. 2003, A&A,](http://linker.aanda.org/10.1051/0004-6361/202450206/25)
[409, 115](http://linker.aanda.org/10.1051/0004-6361/202450206/25)
[Nardini, E., Risaliti, G., Salvati, M., et al. 2009, MNRAS, 399, 1373](http://linker.aanda.org/10.1051/0004-6361/202450206/26)
Papaefthymiou, E. S., Michos, I., Pavlou, O., Papadopoulou Lesta, V., &
[Efstathiou, A. 2022, MNRAS, 517, 4162](http://linker.aanda.org/10.1051/0004-6361/202450206/27)
[Parra, R., Conway, J. E., Elitzur, M., & Pihlström, Y. M. 2005, A&A, 443, 383](http://linker.aanda.org/10.1051/0004-6361/202450206/28)
[Peng, H., Wu, Z., Zhang, B., et al. 2020, A&A, 638, A78](http://linker.aanda.org/10.1051/0004-6361/202450206/29)
Pérez-Torres, M. A., Alberdi, A., Romero-Cañizales, C., & Bondi, M. 2010,

[A&A, 519, L5](http://linker.aanda.org/10.1051/0004-6361/202450206/30)
Pihlström, Y. M. 2007, in Astrophysical Masers [and](http://linker.aanda.org/10.1051/0004-6361/202450206/31) their Environments, eds.
J. M. Chapman, W. A. Baan, 242, 446
Pihlström, Y. M., Conway, J. E., Booth, R. S., Diamond, P. J., & Polatidis, A. G.
[2001, A&A, 377, 413](http://linker.aanda.org/10.1051/0004-6361/202450206/32)
Pihlström, Y. M., Baan, W. A., Darling, J., & Klöckner, H.-R. 2005, ApJ, 618,
[705](http://linker.aanda.org/10.1051/0004-6361/202450206/33)
[Rigopoulou, D., Spoon, H. W. W., Genzel, R., et al. 1999, AJ, 118, 2625](http://linker.aanda.org/10.1051/0004-6361/202450206/34)
[Roberts, H., & Darling, J. 2024a, in Cosmic Masers: Proper Motion Toward the](http://linker.aanda.org/10.1051/0004-6361/202450206/35)
[Next-Generation](http://linker.aanda.org/10.1051/0004-6361/202450206/35) Large Projects, eds. T. Hirota, H. Imai, K. Menten, & Y.
Pihlström, 380, 16
[Roberts, H., & Darling, J. 2024b, Am. Astron. Soc. Meet. Abstr., 56, 406.07](http://linker.aanda.org/10.1051/0004-6361/202450206/36)
[Roberts, H., Darling, J., & Baker, A. J. 2021, ApJ, 911, 38](http://linker.aanda.org/10.1051/0004-6361/202450206/37)
[Romero-Cañizales, C., Alberdi, A., Ricci, C., et al. 2017, MNRAS, 467, 2504](http://linker.aanda.org/10.1051/0004-6361/202450206/38)
Rovilos, E., Diamond, P. J., Lonsdale, C. J., Lonsdale, C. J., & Smith, H. E. 2003,

[MNRAS, 342, 373](http://linker.aanda.org/10.1051/0004-6361/202450206/39)
[Rupke, D. S., Veilleux, S., & Sanders, D. B. 2005, ApJS, 160, 87](http://linker.aanda.org/10.1051/0004-6361/202450206/40)
[Sales, D. A., Robinson, A., Riffel, R. A., et al. 2019, MNRAS, 486, 3350](http://linker.aanda.org/10.1051/0004-6361/202450206/41)
[Sanders, D. B., & Mirabel, I. F. 1996, ARA&A, 34, 749](http://linker.aanda.org/10.1051/0004-6361/202450206/42)
Shepherd, M. C. 1997, in Astronomical Data Analysis Software and Systems VI,
[eds. G. Hunt, & H. Payne, ASP Conf. Ser., 125, 77](http://linker.aanda.org/10.1051/0004-6361/202450206/43)
[Soto, K. T., & Martin, C. L. 2012, ApJS, 203, 3](http://linker.aanda.org/10.1051/0004-6361/202450206/44)
[Tarchi, A., Castangia, P., Henkel, C., Surcis, G., & Menten, K. M. 2011, A&A,](http://linker.aanda.org/10.1051/0004-6361/202450206/45)
[525, A91](http://linker.aanda.org/10.1051/0004-6361/202450206/45)
Trotter, A. S., Moran, J. M., Greenhill, L. J., Zheng, X.-W., & Gwinn, C. R. 1997,

[ApJ, 485, L79](http://linker.aanda.org/10.1051/0004-6361/202450206/46)
[Veilleux, S., Kim, D. C., & Sanders, D. B. 2002, ApJS, 143, 315](http://linker.aanda.org/10.1051/0004-6361/202450206/47)
Willett, K. W. 2012, in Cosmic Masers - from OH to H0, eds. R. S. Booth, W. H.
[T. Vlemmings, & E. M. L. Humphreys, IAU Symp., 287, 345](http://linker.aanda.org/10.1051/0004-6361/202450206/48)
[Wu, H., Wu, Z., Sotnikova, Y., et al. 2022, A&A, 661, A125](http://linker.aanda.org/10.1051/0004-6361/202450206/49)
[Wu, Z., Sotnikova, Y. V., Zhang, B., et al. 2023, A&A, 669, A148](http://linker.aanda.org/10.1051/0004-6361/202450206/50)
[Yuan, T. T., Kewley, L. J., & Sanders, D. B. 2010, ApJ, 709, 884](http://linker.aanda.org/10.1051/0004-6361/202450206/51)
Zhang, C.-P., Cheng, C., Zhu, M., Xu, J.-L., & Jiang, P. 2024, arXiv e-prints

[arXiv: `[2401.15397](https://arxiv.org/abs/2401.15397)` ]


A193, page 9 of 12

Wu, Z., et al. : A&A, 687, A193 (2024)


**Appendix A:** **Additional material**


**Table A.1.** OH line spectrum of the components in IRAS 01298-07.


Components amplitude center FWHM area
mJy beam [−][1] km s [−][1] km s [−][1] mJy beam [−][1] *km s [−][1]


OH1 3.5 ±0.4 40737±8 134±18 503±62

OH2 4.9±0.5 40714±5 96±11 507±53

OH3 4.1±0.4 40708±7 142±16 612±64

OH4 6.4±0.4 40710±5 146±11 999±68

OH6 4.4±0.4 40776±5 105±12 494±53

OH7 5.0±0.4 40823±5 121±11 646±57

OH8 3.8±0.5 40793±6 102±14 411±53


**Notes.** Columns (1): the emission components; Columns (2)-(5) The Gaussian-fitted model parameters.























V Helio -40000 (km s [-1] )


**Fig. A.1.** Line profiles of OH and HCO [+] . The OH line profile obtained from GBT observations by Willett (2012) is represented by the solid line.
The red, dash-doted line represents the integrated VLBA OH line profile extracted from a square region measuring about 50 × 50 mas centred at
RA:01 32 21.415 DEC:-07 29 08.347, which has been smoothed to about 20 km s [−][1] . The three downward arrows represent the three peaks of the
OH emission profile. The HCO [+] line profiles obtained from ALMA observations (project: 2017.1.00057.S) are depicted by the dashed black line,
which was generated in a circular region (radius ∼ 150 mas) and has been smoothed to 45 km s [−][1] . The upward arrow corresponds to the optical
system velocity c*z (z=0.1362 Soto & Martin (2012)). The y-axis of the OH lines is on the left, whereas the y-axis of the other lines is on the right
in both panels.


A193, page 10 of 12

Wu, Z., et al.: A&A, 687, A193 (2024)



10


5


0


-5


10


5


0


-5


10


5


0


-5


10



4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio


4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio


4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio



10


5


0


-5


10


5


0


-5


10


5


0


-5



4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio



4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio


4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio





5


0


-5

4.04 4.06 4.08 4.10 4.12

V ( × 10 [4] km s [-1] )
helio


**Fig. A.2.** OH emission lines extracted at various points of IRAS 01298−0744. The positions of these points are presented in Fig. 4 and the line
profiles are fitted with one Gaussian component.


A193, page 11 of 12

Wu, Z., et al. : A&A, 687, A193 (2024)



VLBA 2.3 GHz dirty I map@2022 May 30



VLBA 8.4 GHz dirty I map@2022 May 30



-7°29'08.30"


08.32"


08.34"


08.36"


08.38"


1 [h] 32 [m] 21.418 [s] 21.416 [s] 21.414 [s] 21.412 [s]


RA (J2000)



-7°29'08.30"


08.32"


08.34"


08.36"


08.38"


1 [h] 32 [m] 21.418 [s] 21.416 [s] 21.414 [s] 21.412 [s]


RA (J2000)



0.8


0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.8



0.100


0.075


0.050


0.025


0.000


0.025


0.050


0.075


0.100



**Fig.** **A.3.** VLBA S- and X-band dirty images of IRAS 01298−0744. The colour bar on the right of each figure shows the radio-continuum flux
densities in mJy beam [−][1] . The noise levels of the two images is 0.22mJy beam [−][1] and 0.025mJy beam [−][1], respectively. The beam FWHM of the two
images: 2.9 ×1.2 mas at 17 [◦], 8.2 × 2.3 mas at −4 [◦] . The contours are for radio-continuum emission with levels of 0.06 mJy beam [−][1] ×(1, 2) from
VLBA L-band observation (see Table 1).


A193, page 12 of 12


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].fitting.evidence[1]",
  "value": "Direct fit of calibrated continuum visibilities with an elliptical Gaussian model, plus image-plane Gaussian fitting for compact OH components A-D.",
  "failed_quote": "To measure the total continuum emission, we performed a direct fit of calibrated visibilities using an elliptical Gaussian model to mitigate potential deconvolution effects (Martí-Vidal et al. 2014)."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The dominant compact OH maser emission likely stems from a low-velocity nuclear outflow driven by an AGN or starburst.",
  "failed_quote": "Taking into account these characteristics, we propose that the compact OH emission in this galaxy may be indicative of a low-velocity outflow"
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Fitted calibrated visibilities directly with an elliptical Gaussian model to mitigate potential deconvolution effects.",
  "failed_quote": "To measure the total continuum emission, we performed a direct fit of calibrated visibilities using an elliptical Gaussian model to mitigate potential deconvolution effects (Martí-Vidal et al. 2014)."
 }
]
```
