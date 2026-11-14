# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...693A..91L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. aanda ©ESO 2024
November 15, 2024

## Gas dynamics in an AGN-host galaxy at z ≃ 2 . 6 :
### **regular rotation, non-circular motions, and mass models**


Lingrui Lin [1][,][ 2], Federico Lelli [3], Carlos De Breuck [4], Allison Man [5], Zhi-Yu Zhang [1][,][ 2], Paola Santini [6], Antonino
Marasco [7], Marco Castellano [6], Nicole Nesvadba [8], Thomas G. Bisbas [9], Hao-Tse Huang [10][,][ 11][,][ 5], and Matthew Lehnert [12]


1 School of Astronomy and Space Science, Nanjing University, Nanjing 210023, China
2 Key Laboratory of Modern Astronomy and Astrophysics, Nanjing University, Ministry of Education, Nanjing 210023, China
3 INAF - Arcetri Astrophysical Observatory, Large E. Fermi 5, 50125, Florence, Italy; e-mail: `federico.lelli@inaf.it`
4 European Southern Observatory, Karl-Schwarzschild-Str. 2, 85748, Garching bei München, Germany
5 Department of Physics & Astronomy, The University of British Columbia, 6224 Agricultural Road, Vancouver BC, V6T 1Z1,
Canada
6 INAF - Osservatorio Astronomico di Roma, Via Frascati 33, 00078, Monteporzio Catone, Italy
7 INAF - Osservatorio Astronomico di Padova, vicolo dell’Osservatorio 5, 35122 Padova, Italy
8 Université de la Côte d’Azur, Observatoire de la Côte d’Azur, CNRS, Laboratoire Lagrange, Bd de l’Observatoire, CS 34229,
06304 Nice cedex 4, France
9 Research Center for Astronomical Computing, Zhejiang Laboratory, Hangzhou 311100, China
10 Department of Astronomy, University of California at Berkeley, Berkeley, CA 94720, USA
11 Department of Physics, The Chinese University of Hong Kong, Shatin, N.T., Hong Kong
12 Centre de Recherche Astrophysique de Lyon, ENS de Lyon, Université Lyon 1, CNRS, UMR5574, 69230 Saint-Genis-Laval,
France


Received September 15, 1996; accepted March 16, 1997


**ABSTRACT**


The gas dynamics of galaxies provide critical insights into the evolution of both baryons and dark matter (DM) across cosmic time.
In this context, galaxies at cosmic noon — the period characterized by the most intense star formation and black hole activities —
are particularly significant. In this work, we present an analysis of the gas dynamics of PKS 0529-549: a galaxy at _z_ ≃ 2.6, hosting a
radio-loud active galactic nucleus (AGN). We use new ALMA observations of the [C i] (2-1) line at a spatial resolution of 0.18 [′′] (∼1.5
kpc). We find that (1) the molecular gas forms a rotation-supported disk with _V_ vrot /σ v = 6 ± 3 and displays a flat rotation curve out
to 3.3 kpc; (2) there are several non-circular components including a kinematically anomalous structure near the galaxy center, a gas
tail to the South-West, and possibly a second weaker tail to the East; (3) dynamical estimates of gas and stellar masses from fitting
the rotation curve are inconsistent with photometric estimates using standard gas conversion factors and stellar population models,
respectively; these discrepancies may be due to systematic uncertainties in the photometric masses, in the dynamical masses, or in
the case a more massive radio-loud AGN-host galaxy is hidden behind the gas-rich [C i] emitting starburst galaxy along the line of
sight. Our work shows that in-depth investigations of 3D line cubes are crucial for revealing the complexity of gas dynamics in high- _z_
galaxies, in which regular rotation may coexist with non-circular motions and possibly tidal structures.


**Key words.** dark matter – galaxies: active –galaxies: evolution – galaxies: formation – galaxies: high-redshift – galaxies: kinematics
and dynamics



**1.** **Introduction**


The study of gas dynamics provides key insights in the formation and evolution of galaxies across cosmic time. On global
scales, the distributions of baryons and dark matter (DM) shape
the gravitational potential of galaxies, affecting their overall gas
kinematics (e.g., van Albada & Sancisi 1986). In addition, the
feedback effects from massive stars (e.g., stellar winds and supernovae) and active galactic nuclei (AGN) inject energy into the
interstellar medium (ISM), stirring the star-forming gas and possibly quenching the star formation of galaxies (e.g., Silk & Mamon 2012). In this context, galaxies at redshift _z_ ≃ 1 − 3 are particularly important because both the cosmic star formation history and the accretion history of supermassive black holes peak
around this epoch, which is known as “cosmic noon” (Madau &
Dickinson 2014).



Rapid developments in astronomical instruments have been
boosting spatially-resolved studies of gas kinematics in high- _z_
galaxies. Near-infrared (NIR) spectroscopy with integral field
units (IFUs) has enabled studies of the kinematics of warm ionized gas in galaxies at _z_ ≃ 1−3, using Hα or [O iii] emission lines
(e.g., Förster Schreiber et al. 2009; Gnerucci et al. 2011; Wisnioski et al. 2015, 2019; Di Teodoro et al. 2016; Stott et al. 2016;
Turner et al. 2017). Radio and (sub-)millimeter interferometers
can resolve kinematics of cold molecular gas, which is composed
mostly of molecular hydrogen (H 2 ). However, the symmetric H 2
molecule does not have a permanent dipole moment so it hardly
emits any lines in the cold molecular gas. Practically, we observe H 2 -tracers like CO (Hodge et al. 2012; Tadaki et al. 2017;
Talia et al. 2018; Übler et al. 2018; Rizzo et al. 2023; Lelli et al.
2023), [C i] (Lelli et al. 2018; Dye et al. 2022; Gururajan et al.
2022; Rizzo et al. 2023), or [C ii] (De Breuck et al. 2014; Jones


Article number, page 1 of 17

_A&A proofs:_ manuscript no. aanda



et al. 2017; Smit et al. 2018; Rizzo et al. 2020; Lelli et al. 2021;
Rizzo et al. 2021) lines.
Emission lines of different species trace distinct phases of the
interstellar gas. In nearby galaxies, the warm ionized gas traced
by Hα is often found to rotate slower and has a larger velocity dispersion than the cold molecular gas traced by low- _J_ CO
lines (e.g., Levy et al. 2018; Su et al. 2022). In galaxies hosting starbursts and/or AGNs, emission lines of Hα and [O iii] can
be dominated by galactic outflows (Arribas et al. 2014; Harrison et al. 2014; Concas et al. 2017, 2019, 2022), which further
complicates analyses of galaxy rotation.
For high- _z_ galaxies, the beam smearing effect (Warner et al.
1973; Bosma 1978; Begeman 1989) also becomes significant as
usually these galaxies can be spatially resolved only with a few
independent elements with current facilities. This will lead to the
observed emission lines being broadened by both the intrinsic
turbulent motion of the interstellar gas and the unresolved rotation velocity ( _V_ rot ) structure within the telescope beam. In addition, the observed line-of-sight velocity is intensity-weighted so
it is biased towards small galactic radii where the surface brightness is higher. To overcome the beam smearing effect, various
tools have been developed to fit a rotating disk model directly to
the 3-dimensional (3D) emission-line cubes (e.g., Bouché et al.
2015; Di Teodoro & Fraternali 2015; Kamphuis et al. 2015).
Therefore, to study the dynamics of high- _z_ galaxies, especially the extreme cases at cosmic noon, one needs multi-phase
gas tracers for a panchromatic view of both circular and noncircular motions as well as careful treatment of beam smearing
effects (i.e., high-resolution data and reliable modeling). To date,
such studies are only limited to a handful of cases (e.g., Chen
et al. 2017; Übler et al. 2018; Lelli et al. 2018, 2023).
PKS 0529-549 is a well-studied radio galaxy at _z_ ≃ 2.57
with plenty of multi-wavelength data — optical spectroscopy,
NIR imaging, and radio polarimetry (Broderick et al. 2007),
Spitzer Infrared Array Camera (IRAC), Infrared Spectrograph
(IRS), and Multiband Imaging Photometer for Spitzer (MIPS)
imaging (De Breuck et al. 2010), Herschel Photodetector Array
Camera and Spectrometer (PACS) and Spectral and Photometric
Imaging Receiver (SPIRE) imaging (Drouart et al. 2014), 1.1mm data from AzTEC (Humphrey et al. 2011), Very Large Telescope (VLT) Spectrograph for INtegral Field Observations in the
Near Infrared (SINFONI) imaging spectroscopy (Nesvadba et al.
2017), Atacama Large Millimeter Array (ALMA) [C i] (2-1) line
(Lelli et al. 2018) and band-6 continuum (Falkendal et al. 2019),
and VLT/X-Shooter spectra from rest-frame ultra-violet (UV) to
optical (Man et al. 2019).
PKS 0529-549 hosts a Type-ii AGN and two radio lobes
(Broderick et al. 2007). The Eastern lobe has the highest Faraday
rotation measure ever observed to date (Broderick et al. 2007),
suggesting that the galaxy is surrounded by a medium with high
electron density and/or a strong magnetic field. PKS 0529-549
has an estimated stellar mass ( _M_ ⋆ ) of 3 × 10 [11] M ⊙ (De Breuck
et al. 2010) derived by fitting the stellar spectral energy distribution (SED), and a star formation rate (SFR) of 1020 [+] − [190] 170 [M] [⊙] [yr] [−][1]
(Falkendal et al. 2019) derived by the total infrared luminosity.
PKS 0529-549 has experienced at least two bursts of recent star
formation in the past, 6 Myr and - 20 Myr, respectively, based
on an analysis of the photospheric absorption features in the restframe UV spectrum (Man et al. 2019).
Using ALMA observations, Lelli et al. (2018) found that
the [C i] [3] P 2 → [3] P 1 emission (hereafter [C i] (2-1)) is consistent
with a rotating disk. The [O iii] λ5007 emission (Nesvadba et al.
2017), on the other hand, is more extended and is aligned with
the radio lobes, so it is probably dominated by an AGN-driven


Article number, page 2 of 17



outflow. The rotation speed of the gas disk traced by [C i] provided a total dynamical mass consistent with the observed baryonic mass, but detailed mass models that separate the gravitational contributions of baryons and/or DM could not be constructed due to the low resolution and sensitivity of the [C i] (21) data. For the same reasons, it was not possible to measure the
gas velocity dispersion and to investigate possible non-circular
motions in the molecular disk.
In this work, we present new ALMA [C i] (2-1) observations
of PKS 0529-549 with high spatial resolution and sensitivity.
The [C i] lines are among the most efficient H 2 -tracers for galaxies at cosmic noon because they are accessible through ALMA
band 4 and band 6. At _z_ ∼ 2, the CO lines ( _J_ ≥ 3) covered by
ALMA are weak. The [C ii] 158-µm line, instead, is difficult to
observe at _z_ ≃ 1 − 3 due to its high frequency (even though redshifted) that requires excellent weather conditions at the ALMA
site, but it is cost-effective for galaxies at _z_ - 4 because it becomes observable with ALMA band 7 (e.g., De Breuck et al.
2014; Jones et al. 2017; Smit et al. 2018; Lelli et al. 2021).
This paper is structured as follows. Section 2 describes the
new ALMA observations and the data reduction. Section 3 describes the gas and dust distribution as well as their radial surface
brightness profile. Section 4 studies the gas kinematics and measures the rotation curve of PKS 0529-549 as well as non-circular
motions. Section 5 builds mass models with different combinations of baryonic and DM components, testing the consistency
of our observations with the expectations from the Λ cold dark
matter (ΛCDM) cosmology. Section 6 discusses the implications
of our results. Section 7 provides a summary.
Throughout this paper, we assume a flat ΛCDM cosmology
with _H_ 0 = 67.4 km s [−][1] Mpc [−][1], Ω m = 0.315, and Ω Λ = 0.685
(Planck Collaboration et al. 2020). In this cosmology, 1 arcsec
corresponds to 8.22 kpc at the redshift of PKS 0529-549 ( _z_ =
2.57), while the age of the Universe and the lookback time are
2.5 Gyr and 11.3 Gyr, respectively.


**2.** **Data analysis**


_2.1._ _ALMA observations_


The ALMA band-6 observations were carried out during ALMA
Cycle 6 (Project ID: 2018.1.01669.S, PI: Federico Lelli), targeting the [C i] (2-1) line. Four spectral windows were centered at
226.200, 228.075, 240.000, and 241.875 GHz — each covers
1.875 GHz with 480 channels for a native velocity resolution of
5 km s [−][1] . The first spectral window was chosen to cover both
the [C i] (2-1) line (rest-frequency of 809.341970 GHz) and the
CO _J_ = 7 − 6 line (rest-frequency of 806.651806 GHz); the other
three spectral windows cover the continuum emission. Three execution blocks (EBs) were conducted on 9 August, 23 August,
and 18 September, respectively, in 2019. The on-source times
were 32.93, 32.93, and 15.20 min, respectively (1.35 hours in
total). The first EB was labeled as semi-pass in the initial quality
assurance (QA0) but we kept this EB because it improved the
imaging quality after careful manual calibration. The latter two
EBs (QA2 pass) were calibrated using the standard Common
Astronomy Software Applications (CASA) pipeline (v5.6.1-8)
(CASA Team et al. 2022).


_2.2._ _Imaging and cleaning_


Imaging of the [C i] (2-1) cube was interactively done with the
`tclean` task in CASA (v6.5.2.26), using Briggs’ weighting with
a robust parameter of 1.5 and a uv-taper of 0.05 arcsec. This

L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics



gave a restored beam of 0.178 arcsec × 0.163 arcsec with a position angle PA = −20.9 deg. To reach an optimal compromise
between resolution and sensitivity, we circularized the beam to
0.18 arcsec and rebinned the velocity resolution to 25.8 km s [−][1] .
The root-mean-square (RMS) noise of the final [C i] (2-1) cube is
∼ 0.15 mJy beam [−][1] . The continuum of the [C i] (2-1) cube was
subtracted by fitting a zeroth-order polynomial using the linefree channels (227.4047 to 228.9916 GHz) in the image plane.
The CO _J_ = 7 − 6 line in the same spectral window was masked
by visually trimming the spectrum.
A band-6 continuum image was created by combining the
spectral windows centered at 228.075, 240.000, and 241.875
GHz. We used `tclean` in interactive mode with Briggs’ weighting, robust parameter of 1.5, and a uv-taper of 0.1 arcsec. This
gave a restored beam of 0.199 arcsec × 0.195 arcsec with a position angle PA = 89.5 deg. The RMS noise of the band-6 continuum image is ∼ 0.012 mJy beam [−][1] .


**3.** **Dust and gas distribution**


_3.1._ _Global overview_


Fig. 1 shows the ALMA band-6 (354 µm at rest-frame of
PKS 0529-549) continuum map at ∼ 0.2 [′′] resolution. We confirm
the two continuum components discussed in Lelli et al. (2018):
the one on the East coincides with the radio lobe from the Australia Telescope Compact Array (ATCA) 18-GHz observations,
while the one in the middle coincides with the [C i] (Fig. 2) and

optical emission. Falkendal et al. (2019), indeed, have shown
that the Eastern compact source is consistent with the extrapolation of the power-law synchrotron emission from the radio band
to the sub-mm band, while the central emission coincides with
the gas disk and is contributed mostly by the cold dust in the
galaxy. The new ALMA data confirm this interpretation.
To create a continuum map that contains only dust emission, we used the following procedure to remove the Eastern
synchrotron component. We first interactively drew a mask enclosing only the synchrotron component in the `tclean` task
(with `savemodel=‘modelcolumn’` ). Next, we subtracted the
synchrotron clean component from the original uv-data (using
the `uvsub` task) and redid the imaging. The top-left panel of
Fig. 2 shows the outcome of this procedure.
The [C i] (2-1) moment maps were constructed with 3DBased Analysis of Rotating Object via Line Observations
( [3D] Barolo, Di Teodoro & Fraternali 2015), considering the

[C i] (2-1) signal within a fiducial mask created by the task
`Smooth` `&` `Search` (see Section 4). The moment maps are
shown in Fig. 2. The new ALMA data unambiguously confirm
and spatially resolve the rotating disk identified in Lelli et al.
(2018). In addition, the moment maps reveal a gas tail to the
South-West of the rotating disk. In Section 4.4, we present a
detailed 3D analysis which reveals a kinematically anomalous
component in the blueshifted side of the disk and a second,
weaker gas tail in the redshifted side to the East. It is possible
that these three different non-circular components have a common physical origin, as we discuss in Section 6.1.


_3.2._ _Radial surface brightness profiles_


Radial surface brightness profiles provide an effective 1-D description of the dust and gas distribution in galaxies. They are
useful for measuring characteristic scale lengths, such as the effective radius ( _R_ e ) that contains half of the total flux. They are
also needed to study the overall mass distribution of galaxies


|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|N<br>E<br>Radio lobes<br>1 kpc|N<br>E<br>Radio lobes<br>1 kpc|N<br>E<br>Radio lobes<br>1 kpc|N<br>E<br>Radio lobes<br>1 kpc|N<br>E<br>Radio lobes<br>1 kpc|



because one needs radial surface density profiles of different
baryonic components to compute their gravitational field in the
galaxy mid-plane out to infinity (see section 5).
For the dust radial profile, we use the synchrotron-subtracted
band-6 continuum image (top-left panel in Fig. 2). We measure
the surface brightness profile averaging over a set of elliptical
annuli, positioned according to the kinematic center, the inclination and position angle of the rotating disk (as derived in Section 4.1). The annulus spacing is half of the beam size of the
dust continuum (0.10 arcsec). The results are shown in Fig. 3
(top panel).
UV emission from both young stellar populations and the
AGN can heat up the dust grains, though the latter is expected
to contribute a negligible fraction to the Rayleigh-Jeans tail of
the cold dust emission (Falkendal et al. 2019; Lamperti et al.
2021). To test this effect, we measure the radial profile using
also the ALMA band-4 continuum map at 625 µm rest-frame
(Huang et al. 2024). We find that the dust emission profile at
band 4 is consistent with that at band 6, confirming that the dust
continuum at band 6 is dominated by cold dust grains heated by
young stars. Actually, Man et al. (2019) have shown that the UV
emission from the host galaxy is dominated by the young stellar
population, not the AGN.
For the gas radial profile, we use a [C i] (2-1) moment-0 map
integrated within (−550, 550) km s [−][1] centered at the [C i] (21) systematic velocity (Section 4) to account for possible faint
emissions missed by the source mask. We measure the surface
brightness profile using the same set of annuli as for the dust
profile. The annuli spacing is half of the beam size of the [C i] (21) cube (0.09 arcsec). The results are shown in Fig. 3 (bottom
panel).
Both profiles are fitted with a Sèrsic function (Sersic 1968)
parameterized by the Sèrsic index ( _n_ ) and the effective radius
( _R_ e ). The fitting is done using the orthogonal-distance-regression
method in `scipy.odr` . For the dust profile, we fit the data out


Article number, page 3 of 17



Band 6 continuum [mJy beam _[−]_ [1] ]
0.00 0.05 0.10 0.15 0.20

_A&A proofs:_ manuscript no. aanda



Band 6 continuum (dust only) [mJy beam _[−]_ [1] ]
0.00 0.05 0.10 0.15 0.20



0.5 _[′′]_


0.0 _[′′]_


_−_ 0.5 _[′′]_


0.5 _[′′]_


0.0 _[′′]_


_−_ 0.5 _[′′]_






|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|










[C i] 2-1 mom-0 [Jy beam _[−]_ [1] km s _[−]_ [1] ]
0.1 0.2 0.3 0.4


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|N<br>E<br>1 kpc|



contour). The black dashed line represents the kinematic major axis. In the moment-2 map, the contours are the same as in the moment-0 map.



to radii _R_ = 1 arcsec and obtain _n_ = 1.3 ± 0.2. For the gas
profile, we fit only the data at _R_ < 0.7 arcsec because we aim to
trace the inner rotating disk without contribution from the outer
gas tail. We obtain _n_ = 0.52 ± 0.01, which properly captures
the inner flattening of the gas profile. The best-fit radial density
profiles are shown in Fig. 3 and the best-fit parameters are given
in Table 1.


**Table** **1.** Outputs of Sèrsic fits to the gas and dust surface brightness
profiles.


Component Sèrsic _n_ _R_ e (arcsec) _R_ e (kpc)

Gas 0.52 ± 0.01 0.313 ± 0.003 2.57 ± 0.02

Dust 1.3 ± 0.2 0.57 ± 0.04 4.7 ± 0.3


Article number, page 4 of 17



**4.** **Gas kinematics**


We study the gas kinematics of PKS 0529-549 using [3D] Barolo
(Di Teodoro & Fraternali 2015). In [3D] Barolo, a rotating disk is
modeled with a set of tilted rings, each characterized by five geometric parameters — center coordinates ( _x_ 0, _y_ 0 ), systemic velocity ( _V_ sys ), position angle ( _PA_ ), and inclination ( _i_ ) — and five
physical parameters — rotation velocity ( _V_ rot ), radial velocity
( _V_ rad ), velocity dispersion (σ v ), surface density (Σ gas ), and vertical thickness ( _z_ 0 ). The tilted-ring model is convolved with the
telescope beam and then is iteratively compared with the observations to obtain the best-fit parameters.
The 3D fit of [3D] Barolo is performed on a masked cube
which includes mostly real line emission and avoids noisy pixels.
We generate the source mask by setting `MASK=SMOOTH&SEARCH`,

L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics



0.0


_−_ 0.5


_−_ 1.0


_−_ 1.5

0.0





_−_ 0.5


_−_ 1.0


_−_ 1.5

|Sersicprofile<br>[CI]21<br>-|Col2|Col3|
|---|---|---|
|Sersic proﬁle<br>[CI] 2-1|Sersic proﬁle<br>[CI] 2-1|Sersic proﬁle<br>[CI] 2-1|
|Exp Disk<br>Dust|Exp Disk<br>Dust|Exp Disk<br>Dust|


0.0 0.2 0.4 0.6 0.8 1.0

Radius [arcsec]


**Fig.** **3.** Radial surface brightness profiles of [C i] (2-1) (top, green diamonds) and dust continuum (bottom, red squares). The random error of
each data point is ≲ 6%. The black dashed lines show Sèrsic fits to each
profile.


`FACTOR=1.8` (factor by which the cube is spatially smoothed
before source search), `SNRCUT` =4 (primary S/N threshold),
`GROWTHCUT=3` (secondary S/N threshold to growth the primary
mask), and `MINCHANNELS=2` (minimum number of channels for
an accepted detection). A different choice of the source mask
would not substantially change our general results.

Within the source mask, the [C i] (2-1) disk of PKS 0529-549
can be fitted with five rings. The width of each ring is 0.09 arcsec, which is half of the beam size of the [C i] (2-1) cube. We set
`NORM=AZIM` so that the observed moment-0 map is azimuthally
averaged to obtain the Σ gas of each ring in the model. For the
vertical density distribution, we assume an exponential profile
( `LTYPE=3` ) with a fixed scale height of 300 pc (∼ 0.04 arcsec).
The disk scale height is much smaller than the [C i] (2-1) beam
(0.18 arcsec) so it has negligible impact on the kinematic fitting.
We also fix _V_ rad = 0 because there are no indications for strong
radial motions, which generally produce a non-orthogonality between the kinematic major and minor axes (e.g., Lelli et al.
2012a,b; Di Teodoro & Peek 2021). Therefore, seven free parameters need to be optimized: _x_ 0, _y_ 0, _V_ sys, _PA_, _i_, _V_ rot, and σ v .
To obtain the rotation curve, we first estimate the geometric parameters and then fit the kinematic parameters ( _V_ rot and σ v ) with
the disk geometry fixed.


_4.1._ _Disk geometry_


We first run `3DFIT` on the [C i] (2-1) cube, leaving all seven parameters free. To estimate the overall geometry, all pixels are
uniformly weighted ( `WFUNC=0` ) and both sides of the rotating
disk are considered ( `SIDE=B` ). We set the initial _PA_ = 75 [◦] and
initial _i_ = 50 [◦] . We also set `DELTAPA=15` and `DELTAINC=15`
such that _PA_ and _i_ can explore the parameter space within ±15 [◦]
around their initial guesses. The initial value of σ v is 30 km
s [−][1] (Lelli et al. 2018). We let [3D] Barolo guess the initial values
of _V_ sys and _V_ rot automatically.



                                      After several tests, we find that the kinematic center is diffi
cult to measure because the best-fit value does not coincide with
the kinematic minor axis (defined by the iso-velocity contour
equal to _V_ sys ) as expected for a rotating disk. This is likely due to
the disturbed gas kinematics on the approaching side of the disk.
Therefore, we fix the kinematic center of the galaxy to (R.A.,
Dec.) = (5 [h] 30 [m] 25.447 [s], −54 [◦] 54 [′] 23.165 [′′] ) so that it lies along
the kinematic minor axis (see the bottom left panel of Fig. 2),
and re-run the fits with five free parameters.
Table 2 summarizes the disk geometric parameters fitted by
3D Barolo. The adopted values of _V_ sys, _PA_, and _i_ are measured
as the median values across different rings. The uncertainties are
estimated as



where _N_ = 5 is the number of rings, MAD is the median absolute deviation across the rings, and δ _i_ are the individual errors
on the given parameter at each ring. Under the radical sign, the
first term considers the variation among different rings while the
second term considers the uncertainty of each ring.
The best-fit _PA_ and _i_ are perfectly consistent with the values
from Lelli et al. (2018) of 75 [◦] and 50 [◦], respectively. For such an
inclination angle, _V_ rot is not sensitivity to the inclination correction; for example, _V_ rot only changes by ∼10% when _i_ varies from
50 [◦] to 60 [◦] .


**Table 2.** Disk geometric parameters of PKS 0529-549.


Parameter Value

R.A. (J2000) 5 [h] 30 [m] 25.447 [s]


Dec. (J2000) −54 [◦] 54 [′] 23.165 [′′]

_V_ sys (km s [−][1] ) 47 ± 16
_PA_ ( [◦] ) 75 ± 7

_i_ ( [◦] ) 53 ± 5


**Notes.** _V_ sys is relative to _z_ = 2.570, as measured by the [C i] (2-1) emission from Lelli et al. (2018). Uncertainties are calculated using Eq. 1.


_4.2._ _Rotation velocity and velocity dispersion_


Fixing the geometric parameters, we run `SPACEPAR` in [3D] Barolo
to look for global minima in the parameter space of _V_ rot − σ v .
We explore _V_ rot within [200, 450] km s [−][1] and σ v within [1, 200]
km s [−][1], both with a grid step of 1 km s [−][1] . The residual function
to be minimized is | _M_ − _D_ | ( `FUNC=2` ), where _M_ and _D_ are the
intensity values at each 3D voxel of the model and the data cube,
respectively. To examine the effect of non-circular motions (such
as the enhanced kinematic irregularities on the blueshifted side),
we run `SPACEPAR` separately on the approaching (blueshifted,
`SIDE=A` ) and receding sides (redshifted, `SIDE=R` ), as well as simultaneously on both sides ( `SIDE=B` ).
Fig. 4 shows _V_ rot and σ v of each ring optimized on different sides. The rotation velocities are consistent within the errors among the three different runs. When fitting only the approaching side, the velocity dispersion shows an elevated value
at _R_ ≃ 0.135 [′′], which is likely due to complex non-circular motions rather than a real increase in the gas turbulence (see Fig. 5).
The non-circular motions are examined in detail in Section 4.4.
The current data are unable to properly constrain the radial
profile of the gas velocity dispersion, so we calculate the median


Article number, page 5 of 17



δ =



~~�~~ �
1 [1]
N [MAD] [2] [ +] N [2]
�



N
� δ [2] i (1)

i

1.2


1.0


0.8


0.6


0.4





_A&A proofs:_ manuscript no. aanda


PKS ~~0~~ 529-549 _φ_ =75 _[◦]_


400


200


0


_−_ 200





_−_ 400




|Col1|Rotatingdisk|Col3|
|---|---|---|
||Rotating disk||
||Rotating disk||
||Rotating disk||
|Anomalous<br>structure|||
|Anomalous<br>structure|||





0.1 0.2 0.3 0.4

Radius [arcsec]


**Fig.** **4.** Rotation velocity and velocity dispersion of the [C i] (2-1) disk
by fitting the approaching side (blue crosses), the receding side (red
diamonds), and both sides (green dots). The green band is centered at
the median σ v = 47 km s [−][1] from the two-sides fitting and has a halfwidth of 16 km s [−][1], representing the uncertainty of σ v (see Section 4.2).


σ v from the two-sides fitting (47±16 km s [−][1] ) and use it as our
fiducial estimate of the intrinsic gas velocity dispersion. The uncertainty is calculated using Eq. 1. This measurement of σ V is
consistent within the errors with the fiducial upper limit of ∼30
km s [−][1] estimated by Lelli et al. (2018).
As a final step, we rerun `3DFIT`, fixing σ v = 47 km s [−][1] and
leaving only _V_ rot free. We set `WFUNC=2` to give more weights
along the kinematic major axis. Fig. 5 compares the positionvelocity (PV) diagram along the kinematic major axis of the observed cube with the best-fit model cube. Overall, the disk model
provides a good description of the observations. In particular, the
thickness of the observed PV diagram is well reproduced by the
model, indicating that the velocity dispersion is reasonable. Noncircular motions that cannot be reproduced by the rotating disk
model will be described in detail in Section 4.4.


_4.3._ _Asymmetric drift correction_


The gas disk of PKS 0529-549 is rotationally supported, having a median _V_ rot /σ v = 6 ± 3. The uncertainty is calculated by
propagating the errors on _V_ rot and σ v, which are estimated using
Eq. 1. Turbulent motions, however, may provide non-negligible
pressure support, so we estimate the asymmetric drift correction
(ADC) to obtain the circular velocity ( _V_ c ) that directly relates to
the gravitational potential.
The ADC depends on the radial gradients of σ v and Σ gas
(see, e.g., Eq. 4 in Lelli 2023). In [3D] Barolo, the ADC can be
computed using polynomials to describe the radial profiles of σ v


Article number, page 6 of 17



_−_ 0.75 _−_ 0.50 _−_ 0.25 0.00 0.25 0.50 0.75

Offset [arcsec]


**Fig.** **5.** Position-velocity diagram along the kinematic major axis. The
systemic velocity of the rotating disk is set at _V_ LOS = 0 km s [−][1] . The
color-scale and the blue contours show the observed [C i] (2-1) data.
The red contours and yellow dots show, respectively, the best-fit rotating
disk model and the rotation velocity projected along the line of sight,
assuming a constant velocity dispersion (σ v = 47 km s [−][1] ). The contour
levels are at _S_ / _N_ = (±2, 3, 5); negative contours are shown with gray
dashed lines.


and Σ gas . Fig. 6 shows the resulting _V_ c ( _R_ ) assuming a constant
σ v = 47 km s [−][1] or a radially varying σ v ( _R_ ) (taken from the twosides fitting). We find that the values of _V_ rot and the two versions
of _V_ c are consistent within the errors, confirming that the rotation
support is dominant while pressure support is nearly negligible.
Hereafter, we use _V_ c from a radially constant σ v for simplicity.


400


350


300


250


200


150



100


50





0

0.1 0.2 0.3 0.4

Radius [arcsec]


**Fig.** **6.** The circular-velocity curve of PKS 0529-549 after correcting
for pressure support. The black dots with errorbars show the observed
rotation velocity from `3DFIT` . The red squares and the blue diamonds
show the circular velocities after asymmetric drift correction assuming
a constant σ v and a radially varying σ v, respectively.

L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics



**Table 3.** [C i] (2-1) fluxes of the non-circular components.


Structure Flux (Jy km s [−][1] )

Anomalous structure 0.20 ± 0.02

SW-tail 0.10 ± 0.01

E-tail 0.030 ± 0.003


**Notes.** The random errors of the fluxes are less than 1%. A fiducial
flux calibration error of 10% is taken as a more realistic estimate of the
uncertainty.


_4.4._ _Non-circular motions_


The channel maps (Fig. 7) show that there are non-circular motions that cannot be reproduced by the rotating disk model: 1)
a gas tail to the South-West of the rotating disk at line-of-sight
(LoS) velocities from −191 to −88 km s [−][1] (SW-tail); 2) a second
weaker gas tail to the East of the rotating disk at LoS velocities
from 274 to 377 km s [−][1] (E-tail); and 3) an anomalous structure
at _R_ ≃ 0.1 − 0.3 [′′] at LoS velocities from −501 to −346 km s [−][1]
(see also Fig. 5). These non-circular components are also visible
in the residual [C i] (2-1) moment-0 map (left panel of Fig. 8),
which is obtained by subtracting the best-fit model cube from
the observed cube.


To better visualize the tail-like structures, we construct the
so-called “Renzograms” (Sancisi 1976) from the [C i] (2-1) cube
by integrating over the velocity intervals of the two gas tails
specified above, and overlay them on the dust-only continuum
map (Fig. 9). While the contours around the kinematic center
are influenced by emission from the rotating disk (especially for
the blue contours), the outer parts trace mostly the gas tails, possibly extending beyond the main body of the galaxy disk. The
SW-tail is significantly detected at _S_ / _N_ - 3 while the E-tail is
detected at _S_ / _N_ ∼ 2 − 3.


The right panel of Fig. 8 shows a PV diagram extracted along
the path in the left panel, averaging over a width of 0.225 arcsec.
It is difficult to tell whether the anomalous structure and the SWtail are kinematically connected because the eventual connection
occurs at the same LoS velocities of the gas disk. The physical
nature of these three non-circular components remains unclear
and will be discussed in Section 6.1. A sensible hypothesis is that
we are seeing two "leftover" tidal tails due to a past major merger
and a gas inflow towards the galaxy center, possibly related to the
SW-tail.


Using the residual [C i] (2-1) moment-0 map, we estimate the

[C i] (2-1) flux associated with the non-circular motions. We sum
over pixels with _S_ / _N_ - 3 enclosed by the apertures shown in
the left panel of Fig. 8. The fluxes and the fiducial uncertainties
are given in Table 3 but we stress that these values are lower
limits. In fact, given that the rotating disk model assumes axissymmetry, the flux in the observed moment-0 map is azimuthally
averaged over rings, including the flux of the non-circular motions. This explains why the residuals along the minor axis of
the galaxy are systematically negative. The low- _S_ / _N_ pixels associated with the gas tails are also discounted. The non-circular
motions are responsible for at least 12% of the total flux in the
gas disk (2.8 ± 0.3 Jy km s [−][1] ). We will further discuss the noncircular motions in Section 6.1.



where _V_ c is the observed circular velocity at the _k_ −th radius _R_ k
and δ _V_ c is the associated uncertainty.
Apart from the free parameters in _V_ mod, the disk inclination
_i_ is treated as a nuisance parameter. We impose a Gaussian prior
on _i_ centered at _i_ 0 = 53 [◦] and with a standard deviation of 5 [◦] to
account for the observational uncertainties (see Section 4.1 and
Table 2). When sampling in the parameter space of _i_, _V_ c and δ _V_ c
change by a factor of sin( _i_ 0 )/ sin( _i_ ) accordingly.
In the following sections, we explore different mass models
and clarify priors on the related free parameters. We start with
partial mass models with a limited amount of baryonic components; these models are probably unphysical but are useful to set
hard upper limits on gas and stellar masses. Next, we build complete mass models, but warn that the masses of the different components are often degenerate. The best-fit models are shown in
Fig. 10 & 11 and the MCMC corner plots are shown in Fig. A.1
& A.2. Median values and associated uncertainties of parameters
of each model are presented in Table 4.


_5.2._ _Partial mass models_


5.2.1. Gas only


To set a hard upper limit on the gas mass, we start with a minimalist mass model where the gas disk is the only dynamically
important component. This mass model is probably unphysical;
as we will show, indeed, it cannot reproduce the observed rotation curve.
The gas gravitational contribution ( _V_ gas ) is calculated by numerically solving the Poisson’s equation for a finite-thickness
disk with a density profile ρ( _R_, _z_ ) = Σ( _R_ )ξ( _z_ ), where Σ( _R_ ) is the
radial surface density profile and ξ( _z_ ) is the vertical profile. To
this aim, we use the `vcdisk` package [1] . For Σ( _R_ ), we take the
Sèrsic profile fitted to the [C i] (2-1) surface brightness profile in
Section 3.2. For ξ( _z_ ), we assume an exponential distribution with
a constant scale height of 300 pc.
For practical reasons, we calculate _V_ gas for a normalization
mass ( _M_ 0 ) defined for _R_ →∞ and we introduce a dimensionless
scaling factor Υ gas = _M_ gas / _M_ 0 of the order of unity, where _M_ gas
is the actual gas mass. Therefore, we have _V_ mod [2] [=] [Υ] [gas] _[V]_ gas [2] [. For]
numerical convenience, we take _M_ 0 = 10 [11] M ⊙ and apply hard


1 https://github.com/lposti/vcdisk


Article number, page 7 of 17



**5.** **Mass models**


_5.1._ _Bayesian rotation-curve fitting_


In this section, we build a set of mass models with different combinations of mass components (gas, star, dark matter halo). The
model circular velocity ( _V_ mod ), therefore, is determined by several free parameters _**p**_ depending on which mass components
are included. To determine the parameter values and uncertainties, we use a Markov-Chain-Monte-Carlo (MCMC) method to
sample the posterior probabilities of the free parameters (see Appendix A for details).
In Bayesian inference, the posterior probability distribution
of the free parameters is the product of the likelihood function
(based on new observations) and their priors (based on previous
knowledge or assumptions). We define the likelihood function as
L = exp(−0.5χ [2] ) with




[ _V_ c − _V_ mod ( _**p**_ )] [2]

, (2)
δ [2]
_V_ c



χ [2] =



_N_
�

_k_ =1

_A&A proofs:_ manuscript no. aanda



1.50

1.25


1.00


0.75






































|-553 km s−1<br>1 kpc|-501 km s−1<br>1 kpc|-449 km s−1<br>1 kpc|-398 km s−1<br>1 kpc|
|---|---|---|---|
|-346 km s_−_1<br>1 kpc|-294 km s_−_1<br>1 kpc|-243 km s_−_1<br>1 kpc|-191 km s_−_1<br>1 kpc|
|-139 km s_−_1<br>1 kpc|-88 km s_−_1<br>1 kpc|-36 km s_−_1<br>1 kpc|16 km s_−_1<br>1 kpc|
|67 km s_−_1<br>1 kpc<br>274 km s_−_1|119 km s_−_1<br>1 kpc<br>326 km s_−_1|171 km s_−_1<br>1 kpc<br>377 km s_−_1|222 km s_−_1<br>1 kpc<br>429 km s_−_1|
|1 kpc|1 kpc|1 kpc|1 kpc|









0.50









The red contours show the best-fit rotating disk model (Section. 4). The contour levels are at _S_ / _N_ = (±2, 3, 5); negative contours are shown with
gray dashed lines. The axis coordinates are relative to the kinematic center (golden star). The line-of-sight velocities are relative to the redshift of

[C i] (2-1) line. The synthesized beam of the [C i] (2-1) cube is shown in the bottom-left corner of each panel.



boundaries on log(Υ gas ) ∈ (−2, 2). Therefore, _M_ gas has a uniform
“uninformative” prior within (10 [9], 10 [13] ) M ⊙ .


The best-fit model gives _M_ gas = 8.6×10 [10] M ⊙ . This value, as
we will discuss in Section 6.2.1, is comparable to the molecular
gas mass inferred from the CO _J_ = 4 − 3 (hereafter CO (4-3))
flux but is three times smaller than those inferred from [C i] and
dust emissions (Huang et al. 2024).


The left panel of Fig. 10 shows that it is impossible to reproduce the inner parts of the rotation curve using only the gas
disk component. The high rotation velocities in the innermost
two rings require the existence of a central mass concentration,
such as a stellar spheroid and/or a supermassive black hole.


Article number, page 8 of 17



5.2.2. Stars only


We now consider a mass model where _V_ mod is fully determined
by the stellar component while the gas contribution is neglected.
Since PKS 0529-549 is very bright in [C i], this model corresponds to a scenario where the [C i]-to- _M_ gas conversion factor
is extremely small (see discussions in Section 6.2.1), so that the
gravitational contribution from gas is much smaller than that
from stars. This model is probably unrealistic but is useful for
setting hard upper limits on the stellar mass.


Given the lack of high-resolution optical/NIR imaging for
PKS 0529-549, we cannot directly compute _V_ ⋆ using the observed stellar surface brightness profile (as for _V_ gas ). Therefore,
we adopt a sensible parametric function for the stellar mass distribution by assuming a spherical stellar component described by
a Sèrsic profile. The stellar gravitational contribution at radius _R_

L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics




[C i] 2-1 mom-0 residual [Jy beam _[−]_ [1] km s _[−]_ [1] ]
_−_ 0.10 _−_ 0.05 0.00 0.05 0.10



400


200


0


-200


-400





0.5 _[′′]_


0.0 _[′′]_


_−_ 0.5 _[′′]_







1.0


0.9


0.8


0.7


0.6


0.5


0.4


0.3









0.5 _[′′]_ 0.0 _[′′]_ _−_ 0.5 _[′′]_ _−_ 1.0 _[′′]_


R.A. offset




|Rotatingdisk<br>SW -tail<br>Anomalous<br>structure|Col2|
|---|---|
|SW-tail<br>Rotating disk<br>Anomalous<br>structure||
|SW-tail<br>Rotating disk<br>Anomalous<br>structure||
|SW-tail<br>Rotating disk<br>Anomalous<br>structure||
|SW-tail<br>Rotating disk<br>Anomalous<br>structure||
|SW-tail<br>Rotating disk<br>Anomalous<br>structure||
|.0<br>0.5<br>1.0<br>1.5<br>Offset [arcsec]|.0<br>0.5<br>1.0<br>1.5<br>Offset [arcsec]|



**Fig. 8.** Left: Residual [C i] (2-1) map obtained by subtracting the best-fit rotating disk model from the observed moment-0 map. The synthesized
beam of [C i] data is shown at the lower-left. The axis coordinates are relative to the kinematic center (white star). The dashed circles show the
aperture to measure the flux of the enclosed structures. The black contours correspond to _S_ / _N_ = 3 × (1, 2, 3) of the residual map. The blue dashed
arrow indicates the path for extracting the PV diagram on the right. The upper-left end of the arrow indicates the width of the path. The blue dotted
tickmarks indicate offsets of 0.0 arcsec, 0.5 arcsec, 1.0 arcsec, and 1.5 arcsec along the path. Right: Position-velocity diagram along the path on
the left. The color coding and the contour levels are the same as those in Fig. 5.









malizing mass _M_ 0 = 10 [11] M ⊙ and introduce a dimensionless parameter Υ ⋆ = _M_ ⋆ / _M_ 0 so that _V_ mod [2] [=] [Υ] [⋆] _[V]_ ⋆ [2] [. We apply uniform]
priors on _n_ ⋆ ∈ (0.5, 10), log(Υ ⋆ ) ∈ (−2, 2), and _R_ e,⋆ ∈ (0.1, 5)
kpc.


The right panel of Fig. 10 shows that this single-component
model can fit the observed rotation curve. The best-fit _n_ ⋆ = 5.7
reconfirms that the stellar mass distribution should be centrally
concentrated but _R_ e,⋆ is unconstrained (see the corner plot in
Fig. A.1). Given that the model neglects gas and DM contributions, the best-fit stellar mass (∼ 1.1×10 [11] M ⊙ ) represents a hard
upper limit on the actual stellar mass of the galaxy. This value
is not sensitive to _R_ e,⋆, as is shown in Fig. A.1, and is about a
factor of three smaller than the value estimated from SED fitting
(De Breuck et al. 2010, 3 × 10 [11] M ⊙,). We will discuss possible
reasons for this discrepancy in Section 6.2.2.







**Fig.** **9.** [C i] (2-1) Renzograms (red and blue contours) overlaid on the
dust-only continuum map (grayscale and gray dotted contours). The
blue and red contours show “narrow” [C i] (2-1) moment-0 maps integrated within LoS velocities from −191 to −88 km s [−][1] and 274 to 377
km s [−][1], respectively. The contour levels are at _S_ / _N_ = (2, 3, 5). A single
contour at _S_ / _N_ = 2 of the dust continuum is also shown. The synthesized beam of the dust continuum is shown in the lower-left corner.


is then given by



We have also explored a mass model (Fig. A.3) where the
stellar component is given by the sum of an exponential disk and
a De Vaucouleurs’ bulge (with _n_ ⋆, _bul_ = 4). This multi-component
mass model has four strongly degenerate parameters: the stellar
masses and the effective radii of each component. Since our main
aim is to obtain an upper limit on the total stellar mass, the effective radius of the disk was fixed to be equal to that of the dust
component _R_ e,dust (Fig. 3), while that of the bulge was fixed to
0.1 × _R_ e,dust . This multi-component model also gives a good fit
to the rotation curve and returns a total stellar mass (bulge plus
disk) of ∼ 8 × 10 [10] _M_ ⊙ . This mass is slightly smaller than the
one from the single-component spherical model because of the
well-known fact that a highly flattened mass distribution implies
higher circular velocities than the equivalent spherical mass distribution (e.g., Lelli 2023). The bulge-to-disk ratio is ∼ 0.9, but
this value is highly uncertain and depends on the adopted effective radii. Future high-resolution NIR images are needed to
better constrain the stellar mass distribution.


Article number, page 9 of 17



_V_ ⋆ ( _R_ ) =



_G_ N _M_ ⋆


_R_

~~�~~



_M_ ⋆ γ( _n_ ⋆ (3 − _p_ ), _b_ ( _R_ / _R_ e,⋆ ) [1][/] _[n]_ )


_R_ Γ _n_ −



, (3)
Γ( _n_ ⋆ (3 − _p_ ))



where the fitting parameters are the stellar mass _M_ ⋆, the stellar
half-mass radius _R_ e,⋆, and the Sèrsic index _n_ ⋆ . The parameters _p_
and _b_ are functions of _n_ ⋆ . The incomplete and complete gamma
functions are denoted as γ and Γ, respectively (see Terzi´c & Graham 2005). Similarly to Section 5.2.1, we calculate _V_ ⋆ for a nor

400


350


300


250


200


150


100


50


0



_A&A proofs:_ manuscript no. aanda


400


350


300


250


200


150


100


50


0





0 1 2 3

Radius [kpc]



0 1 2 3

Radius [kpc]



**Fig.** **10.** Partial mass models: gas only (left panel) and stars only (right panel). In both panels, the black dots with errorbars show the observed
circular velocities. The gravitational contributions from gas and stars are shown with a green dotted line and a brown dashed line, respectively.



400


350


300


250


200


150


100


50


0





400


350


300


250


200


150


100


50


0





0 1 2 3

Radius [kpc]



0 1 2 3

Radius [kpc]



**Fig. 11.** Complete mass models: baryons only (left panel) and baryons+DM (right panel). In both panels, the black dots with errorbars show the
observed circular velocities, while the black line shows the best-fit mass model. The gravitational contribution from gas, stars, and DM are shown,
respectively, with a green dotted line, a brown dashed line, and a purple dash-dotted line.


**Table 4.** Parameters of the mass models described in Section 5.


Model _i_ _M_ gas _M_ ⋆ _M_ bar _n_ ⋆ _R_ e,⋆ _M_ 200 _C_ 200
(deg.) (10 [10] _M_ ⊙ ) (kpc) (10 [12] _M_ ⊙ )
Gas only 53.0 [+] − [4] 4 [.] . [8] 9 8.5 [+] − [1] 1 [.] . [7] 6 ... 8.5 [+] − [1] 1 [.] . [7] 6 ... ... ... ...
Stars only 53.0 [+] − [4] 4 [.] . [8] 9 ... 10.5 [+] − [3] 4 [.] . [4] 2 10.5 [+] − [3] 4 [.] . [4] 2 5.6 [+] − [2] 2 [.] . [3] 0 3.0 [+] − [1] 1 [.] . [4] 5 ... ...
Baryons only 52.5 [+] − [4] 4 [.] . [9] 9 1.8 [+] − [1] 1 [.] . [3] 8 6.9 [+] − [3] 4 [.] . [6] 6 8.7 [+] − [3] 4 [.] . [8] 9 5.0 [+] − [1] 1 [.] . [6] 5 1.8 [+] − [1] 1 [.] . [9] 2 ... ...
Baryons + DM 52.4 − [+] 4 [4] . [.] 9 [9] 1.4 − [+] 1 [1] . [.] 4 [1] 4.7 [+] − [2] 2 [.] . [5] 8 6.1 [+] − [2] 3 [.] . [7] 2 5.1 [+] − [1] 1 [.] . [7] 7 1.3 [+] − [1] 0 [.] . [7] 8 2.2 [+] − [1] 1 [.] . [4] 3 3.6 [+] − [0] 0 [.] . [9] 9


**Notes.** The values show medians (50% quantile) with 16% and 84% quantiles in sub- and super-scripts, respectively.



_5.3._ _Complete mass models_


5.3.1. Baryons only


Compared to the single-component models, a more complete
model includes the gravitational contributions of both gas and
stars. In this case, _V_ mod [2] [= Υ] [gas] _[V]_ gas [2] [+ Υ] [⋆] _[V]_ ⋆ [2] [.]
To alleviate the degeneracy among the parameters, we add
the following physically-motivated priors:


Article number, page 10 of 17



1. A log-normal prior on Υ gas . Based on the CO (4-3) flux, the
CO line ratio _r_ 41 = 0.46, and a CO conversion factor α CO =
0.8, Huang et al. (2024) estimate that the molecular gas mass
of PKS 0529-549 is 7.3 ± 0.9 × 10 [10] M ⊙ . Considering the
uncertainties of the assumed CO conversion factor and the
CO line ratio, we center the prior of log(Υ gas ) at −0.14 with
a standard deviation of 0.7 (a factor of 5 for Υ gas ).

L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics



2. A Gaussian prior on _n_ ⋆ . In Section 5.2.2, we have demonstrated that the high circular velocities at small radii require
the stellar profile to be centrally concentrated. Therefore, we
center the prior at _n_ ⋆ = 4 with a standard deviation of 2,
given that the vast majority of stellar spheroids have Sèrsic
indexes between ∼2 (such as pseudo-bulges) and ∼6 (such as
compact ellipticals, Lacerna et al. 2020).


The left panel of Fig. 11 combines the gravitational contribution of both gas and stars. The _M_ gas and _M_ ⋆ values in this model
are 1.8 × 10 [10] M ⊙ and 7.0 × 10 [10] M ⊙, respectively. As expected,
both masses decrease with respect to those in the partial models. The stellar component dominates the total gravitational contribution otherwise the circular velocities at the innermost radii

cannot be recovered.


5.3.2. Baryons plus dark matter


In Section 5.3.1, we have shown that the rotation curve of
PKS 0529-549 is well fitted by a baryon-only model with sensible baryonic masses. Therefore, it is immediately clear that the
DM contribution is unconstrained due to the disk-halo degeneracy (van Albada et al. 1985; Lelli 2023). Nevertheless, we tentatively add a Navarro-Frenk-White (NFW) dark matter halo with
constraints based on ΛCDM cosmology. In this way, we can examine whether the observed rotation curve is consistent with the
expectations from the ΛCDM cosmology.
The NFW-profile is parameterized by the halo concentration
_C_ 200 and the halo mass _M_ 200 (or equivalently the halo velocity
_V_ 200 ). Including the contributions of both baryons and the NFW
DM halo, _V_ mod is thus given by


_V_ mod [2] [= Υ] [⋆] _[V]_ ⋆ [2] [+ Υ] [gas] _[V]_ gas [2] [+] _[ V]_ NFW [2] [(] _[M]_ [200] [,] _[C]_ [200] [)][,] (4)


where _V_ NFW is the circular velocity of the NFW halo (Eq. 10
in Li et al. 2020). In addition to the baryonic priors described in
Section 5.3.1, we use two ΛCDM scaling relations as DM priors:


1. A log-normal prior on _M_ 200 . Legrand et al. (2019) determined the stellar-to-halo mass relations in different redshift bins using a parametric abundance matching technique.
Here, we relate the mean _M_ 200 to _M_ ⋆ through their Eq. 1
with their best-fit parameters at _z_ = [2, 2.5]. A conservative
scatter in log( _M_ 200 ) of 0.2 is adopted.
2. A log-normal prior on _C_ 200 . Dutton & Macciò (2014) fitted
the _M_ 200 − _C_ 200 relation from N-body cosmological simulations. The mean _C_ 200 is related to _M_ 200 through their Eq. 7
with redshift-dependent parameters given by their Eq. 10 and
Eq. 11. We adopt a scatter of 0.11 in log( _C_ 200 ).


Compared to the baryons-only model, including a DM halo
decreases the gas mass and stellar mass, but these different
estimates are all consistent within uncertainties. Even though
the DM contribution is not constrained, the rotation curve of
PKS 0529-549 is consistent with the expectations from the
ΛCDM cosmology.


**6.** **Discussion**


PKS 0529-549 is about 10−100 times more luminous in the [C i]
line than the majority of high- _z_ radio galaxies (HzRG, Kolwa
et al. 2023), enabling detailed studies of its gas distribution
and kinematics. On the other hand, the SFR of PKS 0529-549
(1020 [+] − [190] 170 [M] [⊙] [yr] [−][1] [, Falkendal et al. 2019) indicates that its ISM]
condition should be extreme (e.g., strong UV field, cosmic ray



intensity, gas turbulence, and high gas density and temperature),
which could complicate the abundances of molecular gas tracers
and the excitation of molecular lines.


_6.1._ _Circular and non-circular motions_


In Section 4, we show that PKS 0529-549 has a regular rotating disk, with _V_ rot /σ v = 6 ± 3. This value is larger than what
is predicted by the disk-instability model from Wisnioski et al.
(2015) at the redshift of PKS 0529-549, but is consistent with recent ALMA observations in a significant sample of high- _z_ starforming galaxies (Lelli et al. 2023; Rizzo et al. 2023, 2024).
Given that PKS 0529-549 is an AGN-host starburst with an extreme SFR of 1020 [+] − [190] 170 [M] [⊙] [yr] [−][1] [(Falkendal] [et] [al.] [2019),] [it] [is]
surprising that its gas disk is still dynamically cold.
In addition to the overall regular rotation of the gas disk,
there are clear signatures of non-circular motions, i.e, the SWtail, the E-tail, and the anomalous structure (Section 4.4). The
gas tails may be remnants of a past major merger event, which
could have triggered a gas inflow (possibly related to the anomalous kinematic structure near the center) and therefore the high
star-formation rate and radio-loud AGN activity of the galaxy.
Alternatively, the two gas tails may be spiral arms in a more extended gas disk, while the kinematically anomalous component
may be something unrelated, such as a gas outflow. Future images from the Hubble Space Telescope (HST) or the James Webb
Space Telescope (JWST) are key to elucidating their origins.
Considering the fraction of non-circular motions in the total flux of PKS 0529-549 as well as the gas mass obtained using
the “gas-only” mass model, we obtain hard upper limits on the
gas mass of the non-circular structures, which is about 1.0 × 10 [10]
M ⊙ . Here we assume that the flux-to-mass conversion factors are
the same in the rotating disk and the non-circular structures. If
we take the gas mass from the “Baryons+DM” mass model, the
mass of the non-circular motions decreases to 1.7 × 10 [9] M ⊙ . In
both cases, the molecular gas involved in the non-circular components is a minor fraction (12%) of the total gas mass that resides in the rotating disk.


_6.2._ _Discrepancies in different mass estimates_


Mass models fitted to the observed [C i] rotation curve allow us
to obtain dynamical upper limits on the gas and stellar masses
of this galaxy. In the following, we compare our mass measurements with those from independent methods, finding some puzzling discrepancies.


6.2.1. Discrepancies in gas masses and conversion factors


To estimate the total molecular gas mass ( _M_ mol ) of a galaxy, one
usually measure the line luminosity of an H 2 -tracer and adopt
a luminosity-to-mass conversion factor. For example, CO lines
have been widely used (Carilli & Walter 2013). The CO-to-H 2
conversion _M_ mol and the luminosity of the CO (1-0) line,factor α CO is typically defined as the _L_ CO (1 ′ ratio −0) between [(Bolatto]
et al. 2013). This conversion factor must be calibrated with an
independent measurement of _M_ mol, such as the one derived with
dynamical methods. By doing so, the underlying assumption is
that molecular gas dominates the total gas mass ( _M_ gas ) in the
inner galaxy regions.
_L_ CO (4 ′ In the case of PKS 0529-549, using the CO (4-3) luminosity −3) [=][ (4][.][2][ ±][ 0][.][5)][ ×][ 10] [10] [K km s] [−][1] [pc] [2] [(Huang et al. 2024),]
′ ′
a typical CO line ratio of _r_ 41 ≡ _L_ CO (4−3) [/] _[L]_ CO (1−0) [=] [0][.][5 (Carilli]


Article number, page 11 of 17

_A&A proofs:_ manuscript no. aanda



& Walter 2013), and the upper-limit on _M_ gas from the gas-only
mass model (Section 5.2.1), we get an upper limit on α CO <
1.0 ( _r_ 41 /0.5) M ⊙ (K km s [−][1] pc [2] ) [−][1] . This is similar to what is

∼
commonly used for starbursts ( 0.8, Bolatto et al. 2013; Carilli
& Walter 2013), but we stress that it is a very hard upper limit
because it neglects contributions from stars and DM in the mass
model. If we instead consider the gas mass from the complete
mass model with baryons plus DM, we find α CO = 0.17 ( _r_ 41 /0.5)
M ⊙ (K km s [−][1] pc [2] ) [−][1] .

′
Using the [C i] (1-0) luminosity _L_ [C I] [=][ (3][.][12][ ±][ 0][.][67)][ ×][ 10] [10]

K km s [−][1] pc [2] (Huang et al. 2024) and the upper-limit of _M_ gas
from the gas-only model, we get an upper ′ limit on the [C i]-to_M_ gas conversion factor α [C I] ≡ _M_ gas / _L_ [C I] [<] [2][.][8][ ±][ 0][.][8] [M] [⊙] [(K]
km s [−][1] pc [2] ) [−][1] . This value is about 1/7 of the mean value in high_z_ metal-rich galaxies (∼20, Dunne et al. 2022). If we consider
the gas mass from the complete mass model with baryons plus
DM, the inferred value of α [C I] goes down to 0.4 M ⊙ (K km s [−][1]
pc [2] ) [−][1], which is 50 times lower than the usual value.
One possibility is that PKS 0529-549 has a [C i]/H 2 abundance ratio at least seven times the value taken for local ultraluminous infrared galaxies (∼ 3 × 10 [−][5], Papadopoulos & Greve
2004). If PKS 0529-549 is the progenitor of a local early-type
galaxy (ETG), we may indeed expect that its star-forming gas is
already significantly enriched (e.g., Thomas et al. 2005, 2010).
Moreover, considering the intense star formation and AGN activity in PKS 0529-549, the [C i]/H 2 ratio can also be enhanced
by the dissociating far-UV photons and cosmic rays (Bisbas et al.
2024).
Another possibility is that the radiative transfer of [C i] lines
is complicated by the intense star formation and AGN activity,
leading to enhanced [C i] emission and the failing of the usual
conversion factor. Moreover, the [C i] (1-0) flux is very uncertain
and there may be spatial variations of the [C i] line ratio that we
cannot probe with the current data.


6.2.2. Discrepancies in stellar masses


The upper limit on _M_ ⋆ given by the star-only mass model is
about a factor of ∼ 3 smaller than the value estimated from fitting the spectral energy distribution (SED) with stellar population models (De Breuck et al. 2010). The discrepancy increases
up to a factor of ∼ 6 if the gravitational contributions of gas and
DM are included in the mass models. The discrepancy is quite
serious, so we discuss three possibilities to explain it: (1) the
SED fitting overestimates the stellar mass; (2) the rotating disk
is not in full equilibrium, so the circular velocities underestimate the dynamical mass; and (3) we are observing two different
galaxies along the line of sight.
(1) Regarding the SED fitting, the stellar mass comes from
De Breuck et al. (2010), where 70 HzRGs were studied based on
Spitzer photometry. The SED fitting assumes an elliptical galaxy
template for the stellar component, which may not be ideal for
PKS 0529-549 given its high SFR (Falkendal et al. 2019). Two
or three black body functions are assumed for dust emissions.
The inherent uncertainty of stellar mass derived from SED fitting
(Seymour et al. 2007) is smaller than its difference from the stellar mass derived using dynamic mass models. To further investigate the issue, we have constructed a new SED with 22 photometric points from the rest-frame optical to the radio, using data
from Gemini Flamingos-2, VLT Infrared Spectrometer And Array Camera (ISAAC), Spitzer/MIPS and IRAC, Herschel/SPIRE
and PACS, ALMA band 4 and band 6, and ATCA. Preliminary SED fittings with Code Investigating GALaxy Emission


Article number, page 12 of 17



(CIGALE, Boquien et al. 2019) show that the best-fit stellar mass
can range from 0.4×10 [11] to 1.2×10 [11] M ⊙ depending on the chosen AGN model, so it may be consistent with the dynamicallyinferred value of _M_ ⋆ . The SED fittings, however, are not fully
satisfactory, especially in the AGN-dominated far-infrared portion of the spectrum, so we will investigate this issue in more
detail in a future paper, in which we will test different SED fitting codes and AGN models.


(2) Regarding the dynamical equilibrium, the [C i] (2-1) velocity field is relatively symmetric and shows regular rotation
(Fig. 2), which is usually interpreted as the cold gas being in
equilibrium with the gravitational potential. Our 3D kinematic
modeling, however, reveals an anomalous kinematic structure
in the approaching side of the disk (Fig. 5) and two extended
gaseous tails. If PKS 0529-549 has indeed undergone a recent
major merger, the inner disk may not have had enough time to
relax with the overall gravitational potential, so that the dynamical mass is potentially underestimated (Lelli et al. 2015).


Using the outermost measured point of the rotation curve,
we estimate the orbital time of PKS 0529-549, which is _t_ orb ∼ 80
Myr. This is larger than the time from the two recent bursts of
star formation: 6 Myr and > 20 Myr (Man et al. 2019). If the two
star formation bursts are driven by a major merger, it is therefore
possible that the gas disk of PKS 0529-549 is not relaxed because it did not have enough time to complete several rotations
since the time of the latest starburst. Custom-built hydrodynamical simulations are needed to investigate whether such a merger
event could be strong enough to drive the rotating disk out of
dynamical equilibrium, leading to a systematic underestimate of
the dynamical mass.


(3) Regarding the third possibility, the scenario is that we
are seeing two galaxies roughly aligned along the line of sight:
a [C i]-emitting, gas-rich, star-forming galaxy on the foreground
and a [O iii]-emitting, gas-poor, AGN-dominated galaxy on the
background. As strange as it may sound, there are actually several clues in this direction.


First, the [O iii] λ5007 emission is systematically redshifted
with respect to the [C i] (2-1) emission (Fig. 12). The redshifts
of [C i] (2-1) and [O iii] λ5007 lines are 2.5706 ± 0.0002 and
2.5745 ± 0.0001 (Nesvadba et al. 2017), respectively. Their redshift difference corresponds to either a velocity difference of
∼ 350 km s [−][1] with respect to the [C i] (2-1) rest frame, or a comoving distance difference of ∼ 4.5 Mpc if we consider the [C i]
and [O iii] redshifts as distinct reference frames. Given the cosmological scale-factor of 0.28 at _z_ = 2.57, the physical distance
between the [C i] and [O iii] emitters would be of 1.3 Mpc, so the
two putative galaxies would probably be unbound.

Second, the [O iii] λ5007 kinematic major axis is offset by
∼ 30 [◦] with respect to the [C i] disk major axis (see Fig. 12).
This fact was already noticed by Lelli et al. (2018, see their Fig.
1), who interpreted the [O iii] emission as coming from the redshifted, far-side of an ionized gas outflow, given that the [O iii]
kinematic major axis is well aligned with the AGN-driven radio
lobes.


Discrepant redshifts from several different lines were also
found in Man et al. (2019) using rest-frame UV absorption lines
from VLT/X-Shooter observations. This two-galaxies scenario is
similar to the configuration of the Dragonfly Galaxy (Lebowitz
et al. 2023), where two galaxies (though both gas-rich) are merging, while one of them hosts an AGN and two radio lobes. To
test this scenario, we need high-resolution images from HST or
JWST to possibly discern two separate stellar components.

550


500


450


400


350



L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics











300


250


200






|2.0′′|Col2|Col3|
|---|---|---|
|0<br>500<br>1000<br>1500<br>city [km s_−_1]<br>2.0_′′_<br>1.0_′′_<br>0.0_′′_<br>_−_1.0_′′_<br>_−_2.0_′′_<br>2.0<br>1.0_′′_<br>0.0_′′_<br>_−_1.0_′′_<br>_−_2.0_′′_<br>R.A. offset<br>Dec. offset<br>N<br>E<br>1 kpc<br>    VLT/SINFONI, and VLT/X-Shooter data (see also Lelli et al. 2018). Left: The [C i] (2-1) (green<br>es are extracted from an aperture of 1-arcsec in diameter centered at the kinematic center. The H<br>     om (Man et al. 2019). The velocities of [C i] (2-1), [O iii] λ5007, and He ii λ1640 are relative to th<br>02). The CO (7-6) emission adjacent to [C i] (2-1) is marked with green dotted line (not shifted in<br>   ted from Nesvadba et al. 2017; Lelli et al. 2018) is overlaid with the radio lobes from ATCA 18-G<br>   s are with respect to the redshift of [C i] (2-1). The kinematic major axes of the [C i] (2-1) and [O<br>       ine and the red dash-dotted line, respectively. The FWHM of the SINFONI point-spread function (<br>        left corner. The axis coordinates are relative to the kinematic center (white star).|N<br>E<br>1 kpc||
|0<br>500<br>1000<br>1500<br>city [km s_−_1]<br>2.0_′′_<br>1.0_′′_<br>0.0_′′_<br>_−_1.0_′′_<br>_−_2.0_′′_<br>2.0<br>1.0_′′_<br>0.0_′′_<br>_−_1.0_′′_<br>_−_2.0_′′_<br>R.A. offset<br>Dec. offset<br>N<br>E<br>1 kpc<br>    VLT/SINFONI, and VLT/X-Shooter data (see also Lelli et al. 2018). Left: The [C i] (2-1) (green<br>es are extracted from an aperture of 1-arcsec in diameter centered at the kinematic center. The H<br>     om (Man et al. 2019). The velocities of [C i] (2-1), [O iii] λ5007, and He ii λ1640 are relative to th<br>02). The CO (7-6) emission adjacent to [C i] (2-1) is marked with green dotted line (not shifted in<br>   ted from Nesvadba et al. 2017; Lelli et al. 2018) is overlaid with the radio lobes from ATCA 18-G<br>   s are with respect to the redshift of [C i] (2-1). The kinematic major axes of the [C i] (2-1) and [O<br>       ine and the red dash-dotted line, respectively. The FWHM of the SINFONI point-spread function (<br>        left corner. The axis coordinates are relative to the kinematic center (white star).|N<br>E<br>1 kpc||
|0<br>500<br>1000<br>1500<br>city [km s_−_1]<br>2.0_′′_<br>1.0_′′_<br>0.0_′′_<br>_−_1.0_′′_<br>_−_2.0_′′_<br>2.0<br>1.0_′′_<br>0.0_′′_<br>_−_1.0_′′_<br>_−_2.0_′′_<br>R.A. offset<br>Dec. offset<br>N<br>E<br>1 kpc<br>    VLT/SINFONI, and VLT/X-Shooter data (see also Lelli et al. 2018). Left: The [C i] (2-1) (green<br>es are extracted from an aperture of 1-arcsec in diameter centered at the kinematic center. The H<br>     om (Man et al. 2019). The velocities of [C i] (2-1), [O iii] λ5007, and He ii λ1640 are relative to th<br>02). The CO (7-6) emission adjacent to [C i] (2-1) is marked with green dotted line (not shifted in<br>   ted from Nesvadba et al. 2017; Lelli et al. 2018) is overlaid with the radio lobes from ATCA 18-G<br>   s are with respect to the redshift of [C i] (2-1). The kinematic major axes of the [C i] (2-1) and [O<br>       ine and the red dash-dotted line, respectively. The FWHM of the SINFONI point-spread function (<br>        left corner. The axis coordinates are relative to the kinematic center (white star).|N<br>E<br>1 kpc||



_6.3._ _The disk-halo degeneracy_


In the previous sections, we discussed discrepancies between
stellar and gas masses from “photometric” and “dynamical”
methods. These discrepancies already emerge when we consider
single-component mass models, which provide hard upper limits to the mass of each individual component. Clearly, the discrepancies become even more severe when we consider twocomponent models (gas and stars) or multi-component models
with a DM halo. These facts highlight the severity of the diskhalo degeneracy at high _z_ (Lelli 2023): if we cannot measure
with high confidence the stellar and gas masses with “photometric” methods, there is little hope to measure the DM content.
The disk-halo degeneracy has been a long-standing issue in
building mass models at _z_ = 0 (van Albada et al. 1985). In particular, van Albada & Sancisi (1986) showed that one needs to
know the baryonic mass with an accuracy of about 25% to fully
break the degeneracy, even when extended rotation curves from
H i observations are available (see their Fig. 5). For galaxies at
cosmic noon, the stellar masses from SED fitting and the gas
masses from standard methods (often based on high- _J_ CO lines)
are surely more uncertain than 25%, indicating that major observational and technical endeavours are needed to address the
crucial question of the DM content of high- _z_ galaxies.
In recent years, several studies reported DM fractions of
galaxies at cosmic noon (Price et al. 2021; Nestor Shachar et al.
2023; Puglisi et al. 2023) and some of them even argued to find
evidence for DM cores (Genzel et al. 2020; Bouché et al. 2022).
These works, however, rarely discuss or investigate the disk-halo
degeneracy, possibly indicating some over-confidence in knowing the true baryonic masses of high- _z_ galaxies. At _z_ ≃ 0, one
approach to break the disk-halo degeneracy has been to use NIR
surface photometry in combination with dedicated stellar population models (Schombert & McGaugh 2014; Schombert et al.
2019). Even so, some systematic uncertainties remain due to the
choice of the specific stellar population model and stellar initial mass function, so additional dynamical arguments are used



to set the absolute calibration of the stellar mass (McGaugh &
Schombert 2015; Lelli et al. 2016b,a,c). At high _z_, the current
situation is much more uncertain, but rest-frame NIR imaging
with JWST may be a promising route to measure robust stellar masses, while multi-line gas tracer observations may allow
to measure robust gas masses, so that the disk-halo degeneracy
could be ameliorated, using stringent, physically motivated priors when fitting the rotation curve.


**7.** **Conclusions**


In this work, we study the gas distribution and dynamics of a
radio-loud AGN-host galaxy at _z_ ≃ 2.6, PKS 0529-549, using
ALMA data of the [C i] (2-1) line with a superb spatial resolution
of 0.18 [′′] (∼1.5 kpc). Our results can be summarized as follows:


1. The [C i] (2-1) emission forms a dynamically cold, rotation
supported disk with _V_ rot /σ v = 6 ± 3, confirming the overall
picture from low-resolution data (Lelli et al. 2018);
2. We discover two gas tails extending beyond the rotating disk
and a kinematically anomalous gas component at ∼2 kpc
from the galaxy center. These non-circular structures may
be related and be due to a past merger event;
3. Our 3D kinematic modeling returns a flat rotation curve at
large radii, which implies a total dynamical mass of ∼10 [11]
M ⊙ within about 3.3 kpc;
4. Mass models with multiple components display a strong
disk-halo degeneracy: models with or without a DM halo can
explain equally well the observed circular velocities, so the
DM content is virtually unconstrained;
5. The dynamical upper limit on _M_ ⋆ is exceeded by the stellar masses from available SED fitting, while the dynamical
upper limit on _M_ gas is exceeded by gas masses from usual
recipes. The origin of these discrepancies remain unclear.


High-resolution optical/NIR images, such as those from HST
and/or JWST, are needed to probe the stellar mass distribution


Article number, page 13 of 17

_A&A proofs:_ manuscript no. aanda



and break the disk-halo degeneracy, so to measure the actual
DM content of high- _z_ galaxies. These images may also help to
understand the discrepancies between the different methods for
estimating stellar and gas masses at high _z_, which are key aspects
to understand the formation and evolution of galaxies.


_Acknowledgements._ L. L. and F. L. acknowledge the hospitality of ESO Garching, where most of this work was done. L.L. and Z.Y.Z acknowledge the support from the National Key R&D Program of China (2023YFA1608204). L.L.
and Z.Y.Z acknowledge the support of the National Natural Science Foundation of China (NSFC) under grants 12173016 and 12041305. L.L. and Z.Y.Z
acknowledge the science research grants from the China Manned Space Project,
CMS-CSST-2021-A08 and CMS-CSST-2021-A07. L.L. and Z.Y.Z acknowledge
the Program for Innovative Talents, Entrepreneur in Jiangsu. A. M. acknowledges the support of the Natural Sciences and Engineering Research Council of
Canada (NSERC) through grant reference number RGPIN-2021-03046. T.G.B.
acknowledges support from the Leading Innovation and Entrepreneurship Team
of Zhejiang Province of China (Grant No. 2023R01008). This paper makes use of
the following ALMA data: ADS/JAO.ALMA#2018.1.01669.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan),
together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.


**References**


Arribas, S., Colina, L., Bellocchi, E., Maiolino, R., & Villar-Martín, M. 2014,
A&A, 568, A14
Begeman, K. G. 1989, A&A, 223, 47
Bisbas, T. G., Zhang, Z.-Y., Gjergo, E., et al. 2024, MNRAS, 527, 8886
Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207
Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103
Bosma, A. 1978, PhD thesis, University of Groningen, Netherlands
Bouché, N., Carfantan, H., Schroetter, I., Michel-Dansac, L., & Contini, T. 2015,
AJ, 150, 92
Bouché, N. F., Bera, S., Krajnovi´c, D., et al. 2022, A&A, 658, A76
Broderick, J. W., De Breuck, C., Hunstead, R. W., & Seymour, N. 2007, MNRAS, 375, 1059
Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105
CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501
Chen, C.-C., Hodge, J. A., Smail, I., et al. 2017, ApJ, 846, 108
Concas, A., Maiolino, R., Curti, M., et al. 2022, MNRAS, 513, 2535
Concas, A., Popesso, P., Brusa, M., et al. 2017, A&A, 606, A36
Concas, A., Popesso, P., Brusa, M., Mainieri, V., & Thomas, D. 2019, A&A, 622,
A188
De Breuck, C., Seymour, N., Stern, D., et al. 2010, ApJ, 725, 36
De Breuck, C., Williams, R. J., Swinbank, M., et al. 2014, A&A, 565, A59
Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021
Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016, A&A, 594, A77
Di Teodoro, E. M. & Peek, J. E. G. 2021, ApJ, 923, 220
Drouart, G., De Breuck, C., Vernet, J., et al. 2014, A&A, 566, A53
Dunne, L., Maddox, S. J., Papadopoulos, P. P., Ivison, R. J., & Gomez, H. L.
2022, MNRAS, 517, 962
Dutton, A. A. & Macciò, A. V. 2014, MNRAS, 441, 3359
Dye, S., Eales, S. A., Gomez, H. L., et al. 2022, MNRAS, 510, 3734
Falkendal, T., De Breuck, C., Lehnert, M. D., et al. 2019, A&A, 621, A27
Foreman-Mackey, D. 2016, The Journal of Open Source Software, 1, 24
Förster Schreiber, N. M., Genzel, R., Bouché, N., et al. 2009, ApJ, 706, 1364
Genzel, R., Price, S. H., Übler, H., et al. 2020, ApJ, 902, 98
Gnerucci, A., Marconi, A., Cresci, G., et al. 2011, A&A, 528, A88
Gururajan, G., Béthermin, M., Theulé, P., et al. 2022, A&A, 663, A22
Harrison, C. M., Alexander, D. M., Mullaney, J. R., & Swinbank, A. M. 2014,
MNRAS, 441, 3306
Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11
Huang, H.-T., Man, A. W. S., Lelli, F., et al. 2024, arXiv e-prints,
arXiv:2411.04290
Humphrey, A., Zeballos, M., Aretxaga, I., et al. 2011, MNRAS, 418, 74
Jones, G. C., Carilli, C. L., Shao, Y., et al. 2017, ApJ, 850, 180
Kamphuis, P., Józsa, G. I. G., Oh, S. . H., et al. 2015, MNRAS, 452, 3139
Kolwa, S., De Breuck, C., Vernet, J., et al. 2023, MNRAS, 525, 5831
Lacerna, I., Ibarra-Medel, H., Avila-Reese, V., et al. 2020, A&A, 644, A117
Lamperti, I., Harrison, C. M., Mainieri, V., et al. 2021, A&A, 654, A90
Lebowitz, S., Emonts, B., Terndrup, D. M., et al. 2023, ApJ, 951, 73
Legrand, L., McCracken, H. J., Davidzon, I., et al. 2019, MNRAS, 486, 5468
Lelli, F. 2023, arXiv e-prints, arXiv:2305.18224
Lelli, F., De Breuck, C., Falkendal, T., et al. 2018, MNRAS, 479, 5440
Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713


Article number, page 14 of 17



Lelli, F., Duc, P.-A., Brinks, E., et al. 2015, A&A, 584, A113
Lelli, F., McGaugh, S. S., & Schombert, J. M. 2016a, AJ, 152, 157
Lelli, F., McGaugh, S. S., & Schombert, J. M. 2016b, ApJ, 816, L14
Lelli, F., McGaugh, S. S., Schombert, J. M., & Pawlowski, M. S. 2016c, ApJ,
827, L19
Lelli, F., Verheijen, M., & Fraternali, F. 2014, MNRAS, 445, 1694
Lelli, F., Verheijen, M., Fraternali, F., & Sancisi, R. 2012a, A&A, 537, A72
Lelli, F., Verheijen, M., Fraternali, F., & Sancisi, R. 2012b, A&A, 544, A145
Lelli, F., Zhang, Z.-Y., Bisbas, T. G., et al. 2023, A&A, 672, A106
Levy, R. C., Bolatto, A. D., Teuben, P., et al. 2018, ApJ, 860, 92
Li, P., Lelli, F., McGaugh, S., & Schombert, J. 2020, ApJS, 247, 31
Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415
Man, A. W. S., Lehnert, M. D., Vernet, J. D. R., De Breuck, C., & Falkendal, T.
2019, A&A, 624, A81
McGaugh, S. S. & Schombert, J. M. 2015, ApJ, 802, 18
Nestor Shachar, A., Price, S. H., Förster Schreiber, N. M., et al. 2023, ApJ, 944,
78

Nesvadba, N. P. H., De Breuck, C., Lehnert, M. D., Best, P. N., & Collet, C.
2017, A&A, 599, A123
Papadopoulos, P. P. & Greve, T. R. 2004, ApJ, 615, L29
Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6
Price, S. H., Shimizu, T. T., Genzel, R., et al. 2021, ApJ, 922, 143
Puglisi, A., Dudzeviˇci¯ut˙e, U., Swinbank, M., et al. 2023, MNRAS, 524, 2814
Rizzo, F., Bacchini, C., Kohandel, M., et al. 2024, A&A, 689, A273
Rizzo, F., Roman-Oliveira, F., Fraternali, F., et al. 2023, A&A, 679, A129
Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS,
507, 3952
Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201
Sancisi, R. 1976, A&A, 53, 159
Schombert, J. & McGaugh, S. 2014, PASA, 31, e036
Schombert, J., McGaugh, S., & Lelli, F. 2019, MNRAS, 483, 1496
Sersic, J. L. 1968, Atlas de Galaxias Australes
Seymour, N., Stern, D., De Breuck, C., et al. 2007, ApJS, 171, 353
Silk, J. & Mamon, G. A. 2012, Research in Astronomy and Astrophysics, 12,
917

Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178
Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS, 457, 1888
Su, Y.-C., Lin, L., Pan, H.-A., et al. 2022, ApJ, 934, 173
Tadaki, K.-i., Kodama, T., Nelson, E. J., et al. 2017, ApJ, 841, L25
Talia, M., Pozzi, F., Vallini, L., et al. 2018, MNRAS, 476, 3956
Terzi´c, B. & Graham, A. W. 2005, MNRAS, 362, 197
Thomas, D., Maraston, C., Bender, R., & Mendes de Oliveira, C. 2005, ApJ, 621,
673

Thomas, D., Maraston, C., Schawinski, K., Sarzi, M., & Silk, J. 2010, MNRAS,
404, 1775
Turner, O. J., Cirasuolo, M., Harrison, C. M., et al. 2017, MNRAS, 471, 1280
Übler, H., Genzel, R., Tacconi, L. J., et al. 2018, ApJ, 854, L24
van Albada, T. S., Bahcall, J. N., Begeman, K., & Sancisi, R. 1985, ApJ, 295,
305
van Albada, T. S. & Sancisi, R. 1986, Philosophical Transactions of the Royal
Society of London Series A, 320, 447
Warner, P. J., Wright, M. C. H., & Baldwin, J. E. 1973, MNRAS, 163, 163
Wisnioski, E., Förster Schreiber, N. M., Fossati, M., et al. 2019, ApJ, 886, 124
Wisnioski, E., Förster Schreiber, N. M., Wuyts, S., et al. 2015, ApJ, 799, 209

L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics


**Appendix A:** **Posterior probability distribution from**
**Markov-Chain Monte-Carlo fits**


Fig. A.1 and Fig. A.2 show “corner plots” from MCMC fits to the
rotation curves (see Section 5). The corner plots are obtained using the `corner` package (Foreman-Mackey 2016). The various
panels of the corner plots show the posterior probability distribution of pairs of the fitting parameters (inner panels) as well as
the marginalized 1D probability distribution of each parameter
(outer panels). In the inner panels, individual MCMC samples
outside the 2σ confidence region are shown with black dots,
while binned MCMC samples inside the 2σ confidence region
are shown by a grayscale; the black contours correspond to the
1σ and 2σ confidence regions. In the outer panels (histograms),
red solid lines and dashed black lines correspond to the median
and ±1σ values, respectively. The red solid lines continue in
the outer panels, hitting the median value of the parameter (red
square).
The four corner plots correspond to the different mass models presented in Section 5, having an increasing number of
mass components and free parameters. In addition, we show in
Fig. A.3 a mass models where the stellar component is divided
up in a thick exponential disk and spherical De Vaucouleurs’
bulge. In general, the posterior probability distributions are wellbehaved and show clear peaks, indicating that the fitting quantities are well measured. The only exception is represented by
the effective radius of the stellar spheroid ( _R_ e ) which is poorly
constrained in all models, so it should be interpreted as a fiducial
upper limit.



Article number, page 15 of 17

_i_ = 53.02 [+4.82] _−_ 4.90


_i_



log( _Y_ gas ) = _−_ 0.07 [+0.09] _−_ 0.08


log( _Y_ gas )



_A&A proofs:_ manuscript no. aanda


_i_ = 52.87 [+4.88] _−_ 4.89



_i_



log( _Y_ star ) = 0.02 [+0.14] _−_ 0.18


log( _Y_ star )



_R_ e = 2.96 [+1.40] _−_ 1.51


_R_ e



**Fig. A.1.** Corner plots for partial mass models: gas-only model (left) and stars-only model (right). See Section 5 for details.



_i_ = 52.52 [+4.95] _−_ 4.93


_i_



log( _Y_ gas ) = _−_ 0.74 [+0.30] _−_ 0.44


log( _Y_ gas )



log( _Y_ star ) = _−_ 0.16 [+0.23] _−_ 0.29


log( _Y_ star )



_R_ e = 1.84 [+1.87] _−_ 1.17


_R_ e



sersic ~~n~~ = 5.01 [+1.62] _−_ 1.52


sersic ~~n~~



log( _Y_ gas ) = _−_ 0.85 [+0.33] _−_ 0.44


log( _Y_ gas )



log( _Y_ star ) = _−_ 0.33 [+0.24] _−_ 0.26


log( _Y_ star )



_R_ e = 1.25 [+1.70] _−_ 0.80


_R_ e



sersic ~~n~~ = 5.06 [+1.71] _−_ 1.69


sersic ~~n~~



sersic ~~n~~ = 5.65 [+2.32] _−_ 1.95


sersic ~~n~~


log( _V_ 200) = 2.46 [+0.09] _−_ 0.08


log( _C_ 200) = 0.56 [+0.11] _−_ 0.11



log( _V_ 200)



_i_ = 52.36 [+4.94] _−_ 4.86


_i_



log( _C_ 200)



**Fig. A.2.** Corner plots for complete mass models: baryons-only model (left) and baryons-plus-DM model (right). See Section 5 for details.


Article number, page 16 of 17

log( _Y_ disk ) = _−_ 0.44 [+0.40] _−_ 0.89


log( _Y_ disk )



400


350


300


250


200


150


100


50


0



L. Lin et al.: PKS 0529-549 [C i] (2-1) kinematics


_i_ = 52.89 [+4.86] _−_ 4.86



log( _Y_ bul ) = _−_ 0.38 [+0.11] _−_ 0.12


log( _Y_ bul )



0 1 2 3

Radius [kpc]



_i_



**Fig. A.3.** Left: A mass model where the stellar component is composed of an exponential disk (blue dashed line) and a De Vaucouleurs bulge (red
dash-dotted line). The black dots with errorbars show the observed circular velocities, while the black line shows the best-fit mass model. This
model gives a total stellar mass (bulge plus disk) of 8.0 [+] − [3] 7 [.] . [5] 8 [×][ 10] [10] [M] [⊙] [. Right: Corner plot for the stellar disk][ +][ bulge mass model.]


Article number, page 17 of 17


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0.18 arcsec ([C I] (2-1) cube, circularized from 0.178 x 0.163 arcsec); 0.199 x 0.195 arcsec (Band 6 continuum)",
  "failed_quote": "This gave a restored beam of 0.178 arcsec × 0.163 arcsec with a position angle PA = −20.9 deg. To reach an optimal compromise between resolution and sensitivity, we circularized the beam to 0.18 arcsec"
 },
 {
  "path": "data.external_data_from_literature[4].what.evidence[0]",
  "value": "VLT/X-Shooter spectrum and ages of two recent star formation bursts (6 Myr and > 20 Myr)",
  "failed_quote": "PKS 0529-549 has experienced at least two bursts of recent star formation in the past, 6 Myr and - 20 Myr, respectively, based on an analysis of the photospheric absorption features in the rest-frame UV spectrum (Man et al. 2019)."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "0.18 arcsec circularized (from 0.178 arcsec x 0.163 arcsec, PA = -20.9 deg) for [C I] (2-1) cube; 0.199 arcsec x 0.195 arcsec, PA = 89.5 deg for Band 6 continuum",
  "failed_quote": "This gave a restored beam of 0.178 arcsec × 0.163 arcsec with a position angle PA = −20.9 deg. To reach an optimal compromise between resolution and sensitivity, we circularized the beam to 0.18 arcsec"
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "3D spherical Sersic circular velocity formulation",
  "failed_quote": "The incomplete and complete gamma functions are denoted as γ and Γ, respectively (see Terzić & Graham 2005)."
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "MASK=SMOOTH&SEARCH, FACTOR=1.8, SNRCUT=4, GROWTHCUT=3, MINCHANNELS=2",
  "failed_quote": "We generate the source mask by setting MASK=SMOOTH&SEARCH, FACTOR=1.8 (factor by which the cube is spatially smoothed before source search), SNRCUT=4 (primary S/N threshold), GROWTHCUT=3 (secondary S/N threshold to growth the primary mask), and MINCHANNELS=2 (minimum number of channels for an accepted detection)."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[2]",
  "value": "Annulus spacing = 0.10 arcsec (dust) and 0.09 arcsec (gas, half beam size); fitting range R <= 1 arcsec (dust) and R < 0.7 arcsec (gas)",
  "failed_quote": "For the dust profile, we fit the data out to radii R = 1 arcsec and obtain n = 1.3 ± 0.2. For the gas profile, we fit only the data at R < 0.7 arcsec because we aim to trace the inner rotating disk without contribution from the outer gas tail."
 },
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Compared SPACEPAR fits on approaching (SIDE=A), receding (SIDE=R), and both (SIDE=B) sides; compared major-axis PV diagram and channel maps of model vs data; compared ADC with constant vs radially varying sigma_v",
  "failed_quote": "Fig. 5 compares the position-velocity (PV) diagram along the kinematic major axis of the observed cube with the best-fit model cube."
 },
 {
  "path": "analysis_steps[4].method.evidence[2]",
  "value": "Numerically solve Poisson's equation for the finite-thickness gas disk using vcdisk; model stars with a spherical Sersic profile (or exponential disk + De Vaucouleurs bulge) and DM with an NFW profile; sample posterior probability distributions of partial (gas-only, stars-only) and complete (baryons-only, baryons+DM) mass models using MCMC; compare dynamical masses with CO, [C I], and SED estimate",
  "failed_quote": "Preliminary SED fittings with Code Investigating GALaxy Emission (CIGALE, Boquien et al. 2019) show that the best-fit stellar mass can range from 0.4×1011 to 1.2×1011 M⊙ depending on the chosen AGN model,"
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "Normalization mass M0 = 10^11 M_sun; gas disk vertical scale height = 300 pc; Sersic gas profile n = 0.52, Re = 2.57 kpc",
  "failed_quote": "For numerical convenience, we take M0 = 1011 M⊙ and apply hard boundaries on log(Υgas) ∈ (−2, 2)."
 },
 {
  "path": "analysis_steps[4].assumptions[1].evidence[2]",
  "value": "Spherical Sersic stellar mass distribution (or exponential disk with Re = Re,dust plus n=4 bulge with Re = 0.1 Re,dust); NFW dark matter halo profile; CO line ratio r41 = 0.5",
  "failed_quote": "a typical CO line ratio of r41 ≡ L′CO (4−3)/L′CO (1−0) = 0.5 (Carilli & Walter 2013),"
 },
 {
  "path": "analysis_steps[4].validation.evidence[1]",
  "value": "Tested an alternative stellar disk + De Vaucouleurs bulge model (Fig. A.3) and inspected MCMC posterior corner plots for convergence and parameter degeneracies",
  "failed_quote": "In general, the posterior probability distributions are well-behaved and show clear peaks, indicating that the fitting quantities are well measured."
 },
 {
  "path": "software[3].used_for.evidence[2]",
  "value": "Source masking (Smooth & Search), moment map creation, 3D tilted-ring kinematic modeling (3DFIT, SPACEPAR), and asymmetric drift correction",
  "failed_quote": "In 3DBarolo, the ADC can be computed using polynomials to describe the radial profiles of σv and Σgas."
 },
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Preliminary 22-point spectral energy distribution fitting to estimate stellar mass",
  "failed_quote": "Preliminary SED fittings with Code Investigating GALaxy Emission (CIGALE, Boquien et al. 2019) show that the best-fit stellar mass can range from 0.4×1011 to 1.2×1011 M⊙ depending on the chosen AGN model,"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Intrinsic gas velocity dispersion (sigma_v) = 47 km s^-1",
  "failed_quote": "so we calculate the median σv from the two-sides fitting (47±16 km s−1) and use it as our fiducial estimate of the intrinsic gas velocity dispersion."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Previous [C I] (2-1) observations had insufficient spatial resolution and sensitivity to measure the gas velocity dispersion, investigate non-circular motions, or construct multi-component mass models; [C I] lines are efficient H2 tracers in ALMA Band 4/6 at z ~ 2 where CO(J>=3) is weak and [C II] requires difficult high-frequency weather.",
  "failed_quote": "The rotation speed of the gas disk traced by [C i] provided a total dynamical mass consistent with the observed baryonic mass, but detailed mass models that separate the gravitational contributions of baryons and/or DM could not be constructed due to the low resolution and sensitivity of the [C i] (2-1) data."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Current [C I] (2-1) data cannot properly constrain the radial profile of the gas velocity dispersion.",
  "failed_quote": "The current data are unable to properly constrain the radial profile of the gas velocity dispersion, so we calculate the median σv from the two-sides fitting (47±16 km s−1) and use it as our fiducial estimate of the intrinsic gas velocity dispersion."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Fluxes of the non-circular components measured from the residual moment-0 map are lower limits because the axisymmetric disk model azimuthally averages over all emission including non-circular features and low-S/N tail pixels are excluded.",
  "failed_quote": "The fluxes and the fiducial uncertainties are given in Table 3 but we stress that these values are lower limits. In fact, given that the rotating disk model assumes axis-symmetry, the flux in the observed moment-0 map is azimuthally averaged over rings, including the flux of the non-circular motions."
 }
]
```
