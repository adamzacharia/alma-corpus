# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...688A.146A\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2024
August 26, 2024

## **GA-NIFS: The core of an extremely massive protocluster at the** **epoch of reionisation probed with JWST/NIRSpec**


Santiago Arribas [1][⋆], Michele Perna [1], Bruno Rodríguez Del Pino [1], Isabella Lamperti [1], Francesco D’Eugenio [2][,][ 3], Pablo
G. Pérez-González [1], Gareth C. Jones [4], Alejandro Crespo Gómez [1], Mirko Curti [5], Seunghwan Lim [2][,][ 3], Javier
Álvarez-Márquez [1], Andrew J. Bunker [4], Stefano Carniani [6], Stéphane Charlot [7], Peter Jakobsen [8][,][ 9], Roberto
Maiolino [2][,][ 3][,][ 10], Hannah Übler [2][,][ 3], Chris J. Willott [11], Torsten Böker [12], Jacopo Chevallard [4], Chiara Circosta [13][,][ 10],
Giovanni Cresci [14], Nimisha Kumari [15], Eleonora Parlanti [6], Jan Scholtz [2][,][ 3], Giacomo Venturi [6], and Joris Witstok [2][,][ 3]


1 Centro de Astrobiología, (CAB, CSIC–INTA), Departamento de Astrofísica, Cra. de Ajalvir Km. 4, 28850 – Torrejón de Ardoz,
Madrid, Spain
2 Kavli Institute for Cosmology, University of Cambridge, Madingley Road, Cambridge, CB3 0HA, UK
3 Cavendish Laboratory - Astrophysics Group, University of Cambridge, 19 JJ Thomson Avenue, Cambridge, CB3 0HE, UK
4 Department of Physics, University of Oxford, Denys Wilkinson Building, Keble Road, Oxford OX1 3RH, UK
5 European Southern Observatory, Karl-Schwarzschild-Straße 2, 85748, Garching, Germany
6 Scuola Normale Superiore, Piazza dei Cavalieri 7, I-56126 Pisa, Italy
7 Sorbonne Université, CNRS, UMR 7095, Institut d’Astrophysique de Paris, 98 bis bd Arago, 75014 Paris, France
8 Cosmic Dawn Center (DAWN), Copenhagen, Denmark
9 Niels Bohr Institute, University of Copenhagen, Jagtvej 128, DK-2200, Copenhagen, Denmark
10 Department of Physics and Astronomy, University College London, Gower Street, London WC1E 6BT, UK
11 National Research Council of Canada, Herzberg Astronomy & Astrophysics Research Centre, 5071 West Saanich Road, Victoria,
BC V9E 2E7, Canada
12 European Space Agency, c/o STScI, 3700 San Martin Drive, Baltimore, MD 21218, USA
13 European Space Agency (ESA), European Space Astronomy Centre (ESAC), Camino Bajo del Castillo s/n, 28692 Villanueva de
la Cañada, Madrid, Spain
14 INAF - Osservatorio Astrofisco di Arcetri, largo E. Fermi 5, 50127 Firenze, Italy
15 AURA for European Space Agency, Space Telescope Science Institute, 3700 San Martin Drive. Baltimore, MD, 21210, USA


Received TBD; accepted TBD


**ABSTRACT**


_Context._ The SPT0311-58 system resides in a massive dark-matter halo at z ∼ 6.9. It hosts two dusty galaxies (E and W) with a
combined star formation rate (SFR) of ∼ 3500 M ⊙ yr [−][1], mostly obscured and identified by the rest-frame IR emission. The surrounding
field exhibits an overdensity of submillimetre sources, making it a candidate protocluster.
_Aims._ Our main goal is to characterise the environment and the properties of the interstellar medium (ISM) within this unique system.
_Methods._ We used spatially resolved low-resolution ( _R_ =100) and high-resolution ( _R_ =2700) spectroscopy provided by the
JWST/NIRSpec Integral Field Unit to probe a field of ∼ 17 × 17 kpc [2] around this object, with a spatial resolution of ∼ 0.5 kpc.
_Results._ These observations reveal ten new galaxies at z∼ 6.9 characterised by dynamical masses spanning from ∼10 [9] to 10 [10] M ⊙
and a range in radial velocity of ∼ 1500 km s [−][1], in addition to the already known E and W galaxies. The implied large number
density (ϕ ∼ 10 [4] Mpc [−][3] ) and the wide spread in velocities confirm that SPT0311–58 is at the core of a protocluster immersed in a
very massive dark-matter halo of ∼ (5 ± 3) × 10 [12] M ⊙, and therefore represents the most massive protocluster ever found at the epoch
of reionisation (EoR). We also studied the dynamical stage of its core and find that it is likely not fully virialised. The galaxies in
the system exhibit a wide range of properties and evolutionary stages. The contribution of the ongoing Hα-based unobscured SFR
to the total star formation (SF) varies significantly across the galaxies in the system. Their ionisation conditions range from those
typical of the field galaxies at similar redshift recently studied with JWST to those found in more evolved objects at lower redshift,
with log([OIII]/Hβ) varying from ∼ 0.25 to 1. The metallicity spans more than 0.8 dex across the FoV, reaching nearly solar values in
some cases. The detailed spatially resolved spectroscopy of the E galaxy reveals that it is actively assembling its stellar mass, showing
inhomogeneities in the ISM properties at subkiloparsec scales, and a metallicity gradient (∼ 0.1 dex/kpc) that can be explained by
accretion of low metallicity gas from the intergalactic medium. The kinematic maps also depict an unsettled disc characterised by
deviations from regular rotation, elevated turbulence, and indications of a possible precollision minor merger.
_Conclusions._ These JWST/NIRSpec IFS observations confirm that SPT0311–58 is at the core of an extraordinary protocluster, and
reveal details of its dynamical properties. They also unveil and provide insights into the diverse properties and evolutionary stages of
the galaxies residing in this unique environment.


**Key** **words.** Galaxies: starburst   - Galaxies: interactions   -   - Galaxies: kinematics and dynamics   - Galaxies: clusters   - Galaxies:
individual (SPT-S J031132-5823.4) - Techniques: imaging spectroscopy


Article number, page 1 of 27

_A&A proofs:_ manuscript no. main



**1.** **Introduction**


In the local Universe, observations have established the presence
of massive virialised clusters of galaxies formed by hundreds
to thousands of mainly passively evolving red quenched galaxies (Dressler 1980). Cosmological models based on the ΛCDM
paradigm explain these local clusters as the hierarchical buildup of overdensities in the early Universe (Springel et al. 2005;
Overzier et al. 2009). Protoclusters represent the early nonvirialised stages of the galaxy cluster assembly, a phase when the
galaxies were actively building up their stellar component and
the associated processes were in full action (i.e. gas inflow from
the cosmic web, supermassive black hole coevolution, metal enrichment of the intracluster media, mergers and interactions,
etc.). The protocluster phase therefore plays a crucial role in both
testing cosmology and studying galaxy formation and evolution
(Overzier 2016; Alberts & Noble 2022).
Considerable effort has been dedicated in recent decades to
the search for clusters and protoclusters at increasing redshifts.
At z - 2-3, the search techniques typically employed at lower
redshifts become inefficient, as the cluster members are difficult
to distinguish photometrically from those in the field, and the hot
intracluster medium (ICM) gas signatures (i.e. X-ray emission
and Sunyaev-Zel’dovich effect; e.g. Mantz et al. 2014; Bleem
et al. 2015) are out of reach with current instrumentation. The
presence of protoclusters at early cosmic times is therefore generally identified by a large concentration of galaxies in angular
coordinates and redshift (c.f. Overzier 2016).
An efficient way to search for overdensities at high-z is to
probe the environment of objects that are known to be the progenitors of the very massive brightest cluster galaxies (BCGs)
that reside at the centre of local clusters. One such class is the
high-z dusty star-forming galaxies (DSFGs; Casey et al. 2014,
2021; Swinbank et al. 2014; Magnelli et al. 2013), which are
thought to be the progenitors of local massive ellipticals (e.g.
Simpson et al. 2014) and quiescent galaxies at intermediate redshifts (z ∼ 2-4; e.g. Toft et al. 2014). Hence, several studies have
highlighted their importance for identifying overabundances at
high-z and studying the protocluster phase (e.g. Chapman et al.
2001, 2009; Daddi et al. 2009; Capak et al. 2011; Walter et al.
2012; Casey et al. 2014; Dannerbauer et al. 2014; Casey 2016;
Wang et al. 2016; Harikane et al. 2019; Wang et al. 2021; Lim
et al. 2021; Calvi et al. 2023; Zhou et al. 2024).
The advent of the _James_ _Webb_ Space Telescope (JWST;
Gardner et al. 2023), with its orders of magnitude improvement
in sensitivity, enhanced angular resolution in near- and midinfrared wavelengths, and superb instrumentation, is now opening the opportunity to study both the protocluster phase and the
nature of high-z DSFGs in unprecedented detail. Recent studies
using a variety of JWST observing modes have revealed galaxy
overdensities around the DSFG HDF850.1 at z = 5.2 (HerardDemanche et al. 2023; Sun et al. 2024), the QSOs J0100+2802
at z = 6.3 (Kashino et al. 2023), and J0305–3150 at z = 6.6
(Wang et al. 2024) behind cluster SMACS0723−7327 at z=7.66
(Laporte et al. 2022) and A2744-z7p9OD at z = 7.88 (Morishita
et al. 2023; Hashimoto et al. 2023). Moreover, protoclusters have
also been identified in several regions within the GOODS-North
and GOODS-South fields with redshifts ranging from 5.2 to 8.2
(Helton et al. 2024, 2023), and a protocluster core candidate has
been found around GN-z11 at z=10.6 (Scholtz et al. 2023). Recent JWST studies have also unveiled the properties of the DSFGs and their contribution to the star formation activity at cos

⋆ e-mail: arribas@cab.inta-csic.es


Article number, page 2 of 27



mic dawn (e.g. Pérez-González et al. 2023, Zavala et al. 2023,
Akins et al. 2023, Barrufet et al. 2023).
In this work, we present JWST Near-Infrared Spectrograph
(NIRSpec) Integral Field Unit (IFU) observations of SPT-S
J031132-5823.4 (hereafter SPT0311–58) at z=6.90, the most
distant and massive DSFG known (Strandet et al. 2017). ALMA
observations by Marrone et al. (2018) revealed that this mildly
lensed system (µ ∼ 1.3-2.2) consists of a pair of massive dusty
galaxies separated by a projected distance of 8 kpc, that form
stars at extreme rates (SFR ∼ 540 and 2900 M ⊙ yr [−][1] ) and contain enormous amounts of dust (M _dust_ ∼ 1-3 × 10 [9] M ⊙ ) and gas
(M _gas_ ∼ 1-3 × 10 [11] M ⊙ ; see also Jarugula et al. 2021, Witstok
et al. 2023). These galaxies have a clumpy structure and turbulent kinematics (Spilker et al. 2022; Álvarez-Márquez et al.
2023), and are undergoing fast metal enrichment (Litke et al.
2023). Marrone et al. (2018) also show that SPT0311–58 resides in one of the most massive dark-matter halos expected
to exist at z∼ 7. Due to its extreme luminosity at submillimetre (submm) wavelengths, SPT0311–58 was also included in the
study by Wang et al. (2021), who searched for overdensities in
the fields around the brightest high-redshift sources discovered
in the SPT 2500 deg [2] survey (Vieira et al. 2010, Mocanu et al.
2013, Everett et al. 2020). This study found that the surroundings of SPT0311–58 (i.e. R ≲ 1.3 Mpc) show a significant overdensity of submm sources and a compacted central distribution,
suggesting that it could potentially be at the centre of one of
the most distant protoclusters identified so far. In summary, all
these previous works have established that SPT0311-58 is indeed an extraordinary system that can be seen as an ideal laboratory for studying galaxy evolution in a massive halo at the epoch
of reionisation (EoR).
The JWST/NIRSpec IFU observations presented here cover
the rest-frame UV wavelengths and main optical emission lines
of SPT0311–58 (i.e. ∼ 0.13 – 0.67 µm). This allows us to characterise the physical and kinematic properties of the warm ionised
gas component of its ISM at subkpc scales (i.e. ∼ 0.5 kpc) over
a field of view of ∼ 17 × 17 kpc [2] . Being at z=6.9, SPT0311–
58 is at about the highest redshift for which Hα can be observed with the high angular resolution and sensitivity provided
by JWST/NIRSpec.
The present paper is organised as follows. In Section 2, we
describe the observations and reductions. In Section 3, we explain how we identified and spectrally characterised a group of
ten newly discovered z ∼ 6.9 galaxies around the two already
known massive galaxies in SPT0311–58, together with other
lower z sources also found in the field of view (FoV). Section
4 presents the stellar masses and then focuses on the ISM conditions, including the ionisation and metallicity properties. We
also obtain and discuss the ongoing Hα-based (unobscured) star
formation. In Sect. 5, we discuss the kinematic properties of the
system. In light of the results of this study, in Sect. 6, we discuss the protocluster scenario for SPT0311–58. We also discuss
the physical, chemical, and kinematic properties of the E galaxy,
for which the IFU data give detailed 2D information. Finally, in
Sect. 7, we summarise the main results of this study. Appendix A
provides details of the spectral analysis and Appendix B presents
the magnification map based on a gravitational lens model for
the SPT0311-58 system, making use of the new information provided by these IFU data.
In this work, we adopt the cosmological parameters from
Planck Collaboration et al. (2016): _H_ 0 = 67.7 km s [−][1] Mpc [−][1],
Ω _m_ = 0.307, and Ω Λ = 0.691, which provide a scale of 5.41
kpc/ [′′] at _z_ =6.90. Unless otherwise stated, we use proper distances throughout the paper. We refer to the two main galaxies in

Santiago Arribas et al.: The core of a protocluster at z=6.9



SPT0311-58 as W and E, according to their relative position on
the sky. We adopt a Kroupa initial mass function (IMF; Kroupa
2001)


**2.** **Observations and reductions**


_2.1._ _SPT0311-58 observations_


The present work is part of the GA-NIFS (Galaxy Assembly
with NIRSpec Integral Field Spectroscopy), a NIRSpec GTO
program designed to study the internal structure and the environment of a sample of ∼ 55 galaxies and active galactic nuclei
(AGN) with redshifts of between 2 and 11 by means of spatially
resolved spectroscopy obtained with IFS mode (Böker et al.
2022) of the NIRSpec instrument (Jakobsen et al. 2022). Details
of the GA-NIFS program can be found in Perna (2023). Among
other subsamples, the program includes several distant (i.e. z >
4) infrared-selected dusty star-forming galaxies: HLFS3 (Jones
et al. 2024), ALESS073.1 (Parlanti et al. 2024), GN20 (Übler
et al. 2024), and SPT0311-58, subject of the present study.
The NIRSpec-IFU observations of SPT0311-58 were executed in November 20, 2022, and are specified in PID1264
(PI: L. Colina). These NIRSpec observations were combined in
a single proposal with independent MIRI observations of the
same target (presented in Álvarez-Márquez et al. 2023) with
the aim of saving the telescope slew overhead. The NIRSpec
observations include two different spectral configurations: lowresolution (R100) spectroscopy with the prism covering the full
0.6–5.3 µm range, and high-resolution (R2700) spectroscopy
with the grating/filter combination G395H/F290LP, which covers from 2.8 to 5.27 µm, though due to the gap between the two
detectors the ∼ 3.98–4.20 µm range is not observed at R2700
(Böker et al. 2022). The FoV is ∼ 3 [′′] × 3 [′′] (i.e. ∼ 17 × 17 kpc [2]
at the redshift of SPT0311–58), and the native spaxel size 0.1 [′′]
(0.54 kpc).
We constrained the allowed position angle range for the observations to minimise the presence of bright sources in the MSA
FoV that could leak light and contaminate the IFU spectra. We
were primarily concerned about this potential problem for the
R100 spectra, and therefore we protected the region of the detector occupied by these spectra. For the high-resolution spectra,
MSA-leakage is not so critical as our main goal with this mode
is to analyse emission lines.
We use the first four positions of the medium cycling dither
pattern, which provide offsets large enough to deal with the
failed open micro-shutters and other sources of background,
while keeping a large effective FoV with the complete exposure
time. Also, this choice minimises the number of individual exposures, and therefore also the (dominant) detector noise.
No dedicated background exposures were obtained, as it was
expected that a substantial number of spaxels were free from
galaxy emission and suitable for deriving the background spec
trum.

The detector was configured with the improved reference
sampling and subtraction pattern (IRS [2] ), which significantly
reduces the readout noise with respect to the conventional
method (Rauscher et al. 2017). In particular, NRSIRS2RAPID
(60 groups) and NRSIRS2 (25 groups) options were respectively
selected for R100 and R2700 in a single integration. The different temporal sampling between the two spectral configurations
was motivated by data volume constraints. This gives a total onsource integration time of 3559 and 7352 s for R100 and R2700,
respectively.



_2.2._ _NIRSpec IFU data reduction_


The data reduction was performed with the JWST calibration
pipeline (Bushouse et al. 2023) version 1.8.2, using the context
file _jwst_1068.pmap_ . We follow the general procedure to correct
detector level defects (Stage 1), calibrate the data (Stage 2), and
combine the individual exposures and build the datacube (Stage
3). However, several modifications to the default reduction steps
were required to enhance data quality. These modifications, described in detail in Perna et al. (2023), are briefly summarised
here.


**–** The individual count-rate frames were further processed at
the end of Stage 1 to correct for the different zero-level in
the individual (dither) frames and subtract the vertical stripes
induced by the 1/f noise.
**–** We masked the regions affected by leakage from failed
open microshutters, including not only the pixels flagged as
‘MSA_FAILED_OPEN’, but also others not correctly associated with such leakage in the context file.
**–** In Stage 2, we masked detector pixels corresponding to the
edges of the IFU slices with unreliable _sflat_ corrections, as
they cause evident artefacts (stripes) in the final data cube.

**–**
Outliers were flagged and removed on the individual 2D exposures at the end of Stage 2, using an algorithm similar to
lacosmic (van Dokkum 2001). We calculated the derivative
of the count-rate maps along the (approximate) dispersion
direction, and rejected all measurements above a given percentile of the resulting distribution (D’Eugenio et al. 2023).
This threshold value was optimised after inspecting the products of the different realisations. We found that 98th and
99.5th percentiles were appropriate in our case for the R100
and R2700 data, respectively.
**–** After experimenting with the different methods and scale
options, we generated the final datacubes with the drizzle weighting method and a spaxel scale of 0.05 [′′] in the
_cube_build_ step.


As it has been reported by several authors (e.g. Rodríguez
Del Pino et al. 2024), the noise in the datacube provided by the
pipeline (i.e. ‘ERR’ extension) is underestimated, and we therefore rescaled it according to the standard deviation of the data
themselves (see Sect. 4.1).


_2.3._ _Astrometric registration_


In order to set the reduced data cube coordinates onto the _Gaia_
reference system, we applied the following two-step procedure.
Firstly, we aligned the IFU data with the _Hubble_ Space Telescope (HST) WFC3 images. With this goal, we generate an image over a band-pass similar to F125W by collapsing the R100
data-cube in the spectral range 1.1-1.4 µm (see Fig. 1). Then we
obtained the coordinate offsets to be applied to align this image
with the F125W HST image, taking as reference the flux peak
of the bright foreground galaxy (see inset in Fig. 1). We estimate
the uncertainties associated with this step to be ≲ 70 mas on
each axis. In this figure we can appreciate the slightly better resolution provided by NIRSpec IFU with respect to HST at these
wavelengths, as expected from their respective PSFs (NIRSpec:
D’Eugenio et al. 2023; WFC3: Dressel & Marinelli 2023). Secondly, the absolute astrometry of the HST/WFC3 F125W image
was derived by matching the position of four stars present in the
image FoV with the _Gaia_ DR3 catalogue (Gaia Collaboration
et al. 2023). The absolute sky coordinates (ICRS) of the centre
of the FoV (i.e. spaxel [55,55]) are α = 03 _[h]_ 11 _[m]_ 33 _[s]_ .248 and δ


Article number, page 3 of 27

_A&A proofs:_ manuscript no. main


**Fig.** **1.** Comparison of JWST/NIRSpec IFU and HST imaging. Left: Image generated from the NIRSpec R100 datacube, integrating over the
spectral range 1.1-1.4 µm. The colour bar is in units of 10 [−][19] erg s [−][1] cm [−][2] per spatial pixel. Right: HST image obtained with WFC3 and F125W
filter resampled at the pixel size used with NIRSpec (i.e. 0.050 [′′] ). The inset zooms in on the region around the emission peak used to align the
NIRSpec cube (red isophotes) with the image represented with an unsaturated colour code. Here, and in all the spectral maps presented in this
work, the (0,0) corresponds to coordinates α = 03 _[h]_ 11 _[m]_ 33 _[s]_ .248 and δ = –58º 23’ 33”.24 (white cross). In the image the peak of the lens galaxy is at
relative coordinates (–0.64 [′′], –0.29 [′′] ). The green lines indicate the border of the NIRSpec IFU FoV. The black and white circles in the bottom-left
corners of the panels represent the FWHW of the respective PSFs.



= –58º 23’ 33”.24, and correspond to (0,0) in Fig. 1, and other
spectral maps in the paper. The uncertainty in the astrometric
alignment is 17 mas in R.A. and 30 mas in Dec. The total offsets
applied were 0.155 and 0.305 arcsec in R.A. and Dec., respectively, and the absolute coordinates uncertainty, taking into account both steps, are estimated to be ∼ 80 mas in each direction.

We checked that the images generated from the R100 and
R2700 data-cubes were consistently aligned with each other. In
fact, a 2D Gaussian fit to the brightest region of the lens galaxy
in a common wavelength range led to differences smaller than a
fraction of a spaxel (i.e. < 10 mas).


_2.4._ _Background_


For the R100 datacube, the background spectrum was obtained
from the median of about 1550 spectra free from emission coming from SPT0311–58, the lens galaxy, or any other object in
the FoV. These spaxels were identified by inspecting the continuum and the line maps generated across the whole R100 wavelength range (Sect. 3 and Fig. 2) to make sure that neither continuum nor line emission from the galaxies was included. The area
covered by the background spaxels is shown in Fig. A.1, which
avoids the regions with emission from the galaxies (Fig. 3).

We report here that the individual R100 spectra presented a
strong feature at 1.083 µm, which may be due a metastable He
line (Brammer et al. 2014). This feature is found over the whole
FoV of the IFU with a uniform intensity. It is visible in the spaxels used to obtain the background spectrum (see Fig. 4 bottom
panel). It is already present in the raw data, and also in the reference file _nirspec_sflat_0185_ . As for the present analysis, we note
that this emission is removed in the background subtraction step.

For the R2700 spectra, we do not subtract the sky background. These high-resolution data are only used for the study
of the emission lines and the mean continuum is removed during
the fitting process (see Appendix A).


Article number, page 4 of 27



_2.5._ _Ancillary data_


In addition to the NIRSpec IFU data presented above, in this
study we made use of additional data that are briefly described
below.


**–** JWST/NIRSpec IFU: Calibration star: To derive aperture
corrections (Appendix A.2) and the FHWM of the PSF, we
used the high-resolution G395H/290LP observations of the
standard star 1808347 (PID:1128, Obs. 9; PI: N. Luetzgendorf), which were reduced with the same pipeline version
and context file as the data for SPT0311-58.
**–** HST imaging: HST imaging of SPT0311–58 obtained with
the WFC3 (filter F125W) was used to set the coordinate
system of the present NIRSpec data into _Gaia_ (see Sect.
2.3). The image was directly downloaded from MAST
(PID14740; PI: D. Marrone).
**–** ALMA: We used ALMA band 6 observations of the

[C ii]158µ _m_ line and the adjacent continuum from programs 2016.1.01293.S and 2017.1.01423.S (P.I. D. Marrone). These data have been presented in Marrone et al.
(2018) and Spilker et al. (2022). We requested the calibrated measurement sets (MS) from the EU ALMA Regional Centre (ARC). Data were calibrated with the standard pipeline procedure. To analyse the data, we used the
ALMA data reduction software `CASA` v6.2.1 (CASA Team
et al. 2022). We created a map of the continuum combining two line-free spectral windows, obtaining a synthesised
beam with FWHM of 0.09 × 0.08 arcsec [2] and a sensitivity
of 9.4 µJy beam [−][1] . As for the [C ii] data-cube, the synthesised beam FWHM is 0.08 × 0.07 arcsec [2] with a sensitivity of ∼ 150 µJy beam [−][1] in a 20 km s [−][1] channel. The [C ii]
moment 0 map (intensity map) was generated by integrating
the continuum subtracted data-cube in the spectral channels
from -1000 km s [−][1] to 1200 km s [−][1] with respect to _z_ = 6.900.
Before producing the moment 1 and moment 2 maps, the
spaxels with low signal-to-noise ratio (S/N< 2.3) and those

Santiago Arribas et al.: The core of a protocluster at z=6.9



with spurious emission in each 20 km s [−][1] velocity channel
were masked. Finally, the continuum image and [C ii] datacube were resampled to a spaxel size of 0.05" to match the
size of the NIRSpec spaxels using the `CASA` task `imregrid` .
**–** JWST/MIRI: The image of SPT0311-58 obtained with MIRI
at 10 µm and published by Álvarez-Márquez et al. (2023)
was kindly provided to us by the MIRI GTO team.


**3.** **Field characterisation: Discovery of 10 new z** ∼ **6.9**
**galaxies (and 3 low-z objects)**


The field around SPT0311-58 is very complex, as it includes a
large and bright lens galaxy, the two previously identified main
galaxies (i.e. E and W) and, as detailed below, ten additional
newly discovered galaxies at z ∼ 6.9, as well as a further three
lower redshift objects. In this section, we identify all of these
sources in the FoV, in most of the cases through spectral imaging with the NIRSpec R100 data cube. We then present their
R2700 and R100 spectra, which allow us to confirm their redshifts. We also briefly compare the NIRSpec images with those
obtained with MIRI and ALMA at longer wavelengths. Finally,
we identify one galaxy at z ∼ 6.9 via two-dimensional spectral
decomposition of the R2700 spectra.


_3.1._ _NIRSpec R100 spectral imaging: Identification of_
_continuum and line-emitting sources at z_ ∼ _6.9_


Fig. 2 (a) shows the image obtained from the R100 data-cube
after integrating over the spectral range 3.0 – 3.8 µm. For z ∼
6.9 sources, this spectral range is dominated by the stellar continuum, as it does not include prominent lines (i.e. rest-frame ∼
0.38 – 0.48 µm). The image shows the very bright lens galaxy,
the E galaxy, and several continuum-emitting galaxies labelled
as lz1, lz2, lz3, C1, C2, C3. The structure of the E galaxy is
clearly resolved, allowing us to distinguish the south and north
regions (ES and EN, respectively), which are also clearly seen
in Fig. 1. We also define subregions within EN with lower case
letters (i.e. a, b, c, from south to north). As we will see below
(Sect. 3.3.1), the spectra of the sources lz1, lz2, and lz3 indicate
that they are at lower z than SPT0311–58 (i.e. z < 3, hence the
‘lz’ identification label). Together with the lens galaxy, all these
low-z objects are labelled in cyan in the figure. One of these lowz objects (lz3) partially overlaps with ES. The spectra of sources
C1, C2, and C3 (Sect. 3.3.2) indicate that they are at z∼ 6.9,
and together with other sources at this redshift (i.e. E and its
substructures) they are labelled in yellow in Fig. 2 (a). To ease
the identification of sources detected in the field we include the
apertures used for extracting their spectra in Fig. 3.
Fig. 2 (b) and (c) presents the [OIII]λλ4959,5008 and Hα
(+[NII]λλ6548,6584) emission line maps, obtained by integrating the spectral ranges that cover these lines at a redshift of ∼
6.9, and subtracting a continuum measured close to the lines [1] .
Hence, these images allow us to identify line-emitting sources
at that particular redshift. These images reveal a total of nine
line-emitters: the continuum-detected C1, C2, C3 and six new
sources L1-L6 (see also Fig. 3). The detection of several emission lines in the spectra of all these sources confirmed that they
are at a redshift of ∼ 6.9 (see below in Sect. 3.3.2 ).


1 Specifically, the selected ranges are: 5.00 – 5.15 µm for Hα continuum and 5.17 – 5.23 µm for the Hα line, and 3.72 – 3.82 µm for the

[OIII] continuum and 3.90 – 4.00 µm for the [OIII]λλ4959,5008 lines.



We note the morphological differences between the continuum and the line maps. For instance, some bright line emitting
sources, like L1 and L5, are barely detected in the continuum.

[OIII] and Hα images also show distinct morphology. The E
galaxy is more extended in Hα than in [OIII], and shows a faint
diffuse component towards the north-west. The [OIII] shows a
tail towards the south-west, which is not seen in Hα. Source C3
is much brighter in Hα than in [OIII], and to the north there is
also a zone of faint extended Hα emission.

The top panels in Fig. 2 show that the main structure of the
W galaxy is not detected at spaxel level in the NIRSpec images
(continuum, Hα, or [OIII]). However, as shown in Sect. 3.3.2, the
R100 spectrum obtained integrating over a large aperture enables
us to recover its Hα flux.


_3.2._ _Morphological comparison with MIRI and ALMA imaging_


Fig.2(d) shows the 10 µm image obtained with JWST/MIRI,
after subtracting the lens foreground galaxy (Álvarez-Márquez
et al. 2023). At z=6.9, this image traces the stellar-continuum
at the near-IR rest-frame (i.e. 1.26 µm). The comparison with
the NIRSpec 3.0-3.8 µm image (Fig.2(a), rest-frame ∼ 0.43 µm)
shows clear differences. Although in the central regions of the E
galaxy the bulk of the NIRSpec emission approximately matches
the MIRI image, in the northern zone the mid-infrared emission
seems more extended to the west. The emission detected with
MIRI in the W galaxy has no NIRSpec counterpart. Conversely,
none of the new sources at z ∼ 6.9 discovered with NIRSpec
were reported by Álvarez-Márquez et al. (2023) as MIRI emitters. In fact, we performed aperture photometry at their positions
and find that none of them have 10 µm flux above the 5-sigma
noise level (0.345 µJy).
The NIRSpec and ALMA continuum images also show very
different structures. The W galaxy, very bright at 160 µm (Fig.
2(e)), is not seen by NIRSpec in the 3.0-3.8 µm map (Fig. 2(a)).
The NIRSpec region ENa and the ALMA clump E3 are in positional agreement within ∼ 0.1 arcsec. None of the other NIRSpec
sources at z ∼ 6.9 have ALMA continuum detections, except C3
whose aperture partially overlaps with the southern structure of
W.

As for the line emission maps, the main body of E in Hα
and [OIII] (Fig. 2(b,c)) approximately matches the [CII]λ158 µm
emission (Fig. 2(f)). Nearby regions C1 and L4 also have low

[CII] emission. Regarding the W galaxy, the bright [CII] regions
are not seen with NIRSpec, except weakly at L1. In addition,
the C3 aperture overlaps with the main W emission, but the fact
that it is at the edge of the NIRSpec FoV makes the comparison
difficult. The other NIRSpec newly discovered sources at z ∼
6.90 are not detected with ALMA at [CII]λ158 µm.


_3.3._ _Spectral characterisation of SPT0311-58_


To study the spectral properties in the complex FoV of
SPT0311–58, we followed different approaches. In this section,
we first present the integrated spectra extracted from the data
cubes for the sources and regions identified above. For details
on the spectral analysis see Appendix A.1. As we describe below, these spectra show that three objects (i.e. lz1, lz2, and lz3)
are at low redshift, while confirming that nine newly discovered
sources are at z ∼ 6.9.

Later in this section, we present a spatially resolved analysis
of the E galaxy using the R2700 data. This analysis reveals an
additional distinct galaxy at z∼ 6.90 overlapping along the line


Article number, page 5 of 27

_A&A proofs:_ manuscript no. main


**Fig.** **2.** Continuum and line emission NIRSpec IFU images, together with MIRI and ALMA data. (a): NIRSpec image generated by collapsing
the R100 datacube in the 3.0-3.8 µm spectral range (see text). The continuum emitting sources, whose spectra indicate they are at _z_ ∼ 6.9, are
identified with yellow labels (i.e. C1, C2, C3, E). In the E galaxy, we distinguish several subregions (ES, ENa,b,c). Sources that according to their
spectra are at lower z (i.e. lz1, lz2, lz3) are labelled in cyan, along with the foreground lens galaxy. The red isocontours (in red) correspond to 5,
10, 15, 30, and 100 σ values. (b): [OIII] emission image at z ∼ 6.9 obtained from the R100 datacube (see text for specific spectral ranges). Six
line-emitting sources that were not detected in the continuum map (panel a), are identified in this map as z ∼ 6.9 sources and labelled in yellow
(L1 to L6). White isolines correspond to 3, 5, 10, and 15 σ. Here, and in panels (c), (d), and (e), the red contours are the same as in panel (a), after
removing the ones for the lens galaxy for clarity. (c): Same as panel (b) but for the Hα emission. (d): MIRI image at 10 µm, after subtracting the
lens (Álvarez-Márquez et al. 2023). (e): ALMA continuum at 160 µm. We mark clumps E1 – E4 identified by Spilker et al. (2022). (f): ALMA map
of the [CII]λ158 line. The white isolines correspond to the Hα emission. Fig. 3 identify the targets and their apertures (for details see Appendix
A). In panels (c-f), these apertures are also shown with orange dashed lines. The green straight lines in all the pannels indicate the border of the
NIRSpec IFU FoV.


6.9 (nine sources identified through R100 spectral imaging, and
one through the analysis of the R2700 data), in addition to the
already known E and W galaxies.


3.3.1. Spectra of the lens and other low-z galaxies


The present data allowed us to accurately determine the redshift
of the foreground lens galaxy (i.e. z= 1.0343 ± 0.0002) via the
identification of Paα in the R2700 spectrum, improving on previous photometric determinations (z _phot_ =1.43 [+] − [0] 0 [.] . [42] 35 [,] [Marrone] [et] [al.]
2018). Hα and Paα are also clearly visible in the R100 spectrum shown in Fig. 4. Using this new redshift, together with a
panchromatic image (i.e. rest-frame ∼ 0.49 - 2.45 µm) obtained
from the R100 datacube, in Appendix B, we present the magnification map produced by the lens galaxy.



**Fig.** **3.** Identification of the different targets and regions in the FoV of
SPT0311–58. The apertures used to extract the spectra of the ∼ 6.9
sources are coded in red (with the subregions within E in orange), and
those for the low-z galaxies in blue. Source L7, which is identified by
spectral decomposition (Sect. 3.3.3), is shown for completeness. The W
galaxy is not detected at the resolution of the IFU, and is shown with a
dashed line. More details about the apertures in Appendix A.


of sight of E. In summary, we find ten galaxies at redshift ∼


Article number, page 6 of 27



Fig. 4 also presents the R100 spectra of lz1, lz2, and lz3.
lz1 shows very prominent emission lines, which are consistent
with Hα, [OIII]λ4959,5007 and [OII]λ3726,3728 for a galaxy at
z=2.576 ± 0.002. lz2 and lz3 have no emission lines, so their
redshift determination is less straightforward. For them we infer the redshifts by fitting the R100 spectra with EAZY (Brammer et al. 2008), and find z _ph_ (lz2)= 2.149 [+] − [0] 0 [.] . [175] 074 [,] [and] [z] _[ph]_ [(lz3)][=]
1.678 [+] − [0] 0 [.] . [032] 031 [(see] [also] [insets] [in] [Fig.] [4][).] [Therefore,] [together] [with]
the large foreground galaxy, lz1, lz2 and lz3 do not form part of
the high-z SPT0311-58 system, and they will not be discussed
further in the remainder of the paper.

Santiago Arribas et al.: The core of a protocluster at z=6.9


Aperture details and line fluxes derived from these spectra
are given in Tables A.1 and A.2. Further details about the methods followed can be found in Appendix A.


3.3.3. Identification of L7 at z ∼ 6.9 via 2D kinematic
decomposition



**Fig. 4.** R100 spectra of three newly identified galaxies with z < 3 found
in the FoV of SPT0311-58, together with the bright foreground (lens)
galaxy. The labels indicate their redshifts (see text). For lz2 and lz3 the
insets show the dependence of residuals (reduced χ [2] ) as a function of
the redshift, for the fits performed with EAZY (Brammer et al. 2008).
The horizontal blue line in the inset marks χ [2] _red_ [=][ 1. The sky background]
spectrum inferred from ∼ 1550 spaxels free from galaxy emission is also
shown in the bottom panel.


3.3.2. Spectra of the nine sources at z ∼ 6.9 identified with
R100 spectral imaging


The R100 and R2700 integrated spectra for the high-z sources
are presented in Fig. 5 and Fig. A.2, respectively. These spectra show several emission lines confirming that these sources
are undoubtedly at redshifts around 6.90 (for the specific redshift values see Table 2). In particular, most of the spectra
include Hα, [NII]λλ6548,6584, [OIII]λλ4959,5008, and Hβ.

[OII]λλ3726,3728 (unresolved) is also present in the spectra of
the brightest regions of E.
For the W galaxy, the extraction aperture overlaps with the
foreground lens galaxy (see Appendix A.1), and therefore the
resulting integrated spectrum includes emission from this bright
source (i.e. continuum, and Paα and Hα redshifted for z ∼
1.0343). Still, this spectrum clearly shows Hα at a redshift of
∼ 6.90 (Fig. 5). The line profiles for W and E in the R2700
spectra are largely oversampled due to the line broadening induced by the wide range in velocities covered by the aperture,
and therefore their S/N is lower than for the R100 spectra. For
these galaxies, we also obtained the spectra for their external
extended emission using the E _ext_ and W _ext_ apertures defined in
Appendix A.



In addition to the nine z ∼ 6.9 sources identified with R100 spectral imaging and confirmed spectroscopically above, we find evidence for a tenth source overlapping with the main structure of
the E galaxy. In fact, some spectra from individual spaxels close
to the central region of the E galaxy show evidence for a secondary gaseous component on top of the systemic one (see Fig.
6). Hence we performed a two-Gaussian model decomposition
of these two kinematically distinct components by comparing
the Bayesian information criterion (BIC) of fits performed with
one and two components (Perna et al. 2022). We also considered the possible presence of a third kinematic component that
could be associated with, for example an outflow, but the BIC
analysis did not support this possibility. Figure 7 presents the
corresponding moment 0, 1, and 2 maps for the two components
for the [OIII] line.
The secondary component (i.e. L7 hereafter) is relatively
faint and compact and is located in projection about 0.15 arcsec (i.e. 0.8 kpc) to the southeast from the peak of the main systemic component (i.e. E). Its radial velocity is offset by ∼ 300
km s [−][1] with respect to E, hence allowing us a secure kinematic
decomposition between the two sources. The fact the L7 is redshifted with respect to E excludes the possibility that the detected
emission is due to an outflow. As we show in Sect. 4.5 and 5.1,
the properties of L7 are similar to those of the other new sources
discovered at z ∼ 6.9. The kinematic properties of the E and L7
galaxy are discussed in Sec. 5.


_3.4._ _Summary of sources in the FoV of SPT0311-58_


We list below the various sources found in the field of view:


**–** Lens galaxy (z= 1.0343).
**–** Three low-z galaxies: lz1 (z=2.576±0.002), lz2 (z _ph_ =2.149),
and lz3 (z _ph_ =1.678).
**–** Nine z∼6.9 galaxies identified via R100 spectral imaging
(C1, C2, C3, L1, L2, L3, L4, L5, L6).
**–** One z∼6.9 galaxy identified through 2D spatially resolved
spectroscopy of the R2700 spectra (L7).

**–**
E galaxy, and its regions ES and EN (a, b, and c).

**–**
W galaxy


In addition, we obtained the spectra for the extended diffuse emission in the external regions of E and W. For all these
sources, we present the integrated spectra in the sections above,
except for the one identified via 2D spectroscopy (L7). For this
object, we give the Gaussian model after fitting two kinematically distinct components to the spectrum (see Fig. 6).


**4.** **Stellar masses, ISM conditions, and star**
**formation**


In this section, we obtain the stellar masses and study the ISM
properties for the high-z sources identified above. Details about
the methods followed for the spectral analysis (e.g. extraction
apertures, line fitting) are provided in Appendix A.


Article number, page 7 of 27

_A&A proofs:_ manuscript no. main





































































**Fig. 5.** R100 spectra for the different z ∼ 6.9 sources and regions identified in the spectral images presented in Figure 2. The apertures used are
shown in Fig. 3, and further details in Appendix A. The W spectrum is contaminated by the foreground lens galaxy continuum and Paα line
(marked in red), which is close to Hβ of W (see the lens spectrum in Fig. 4).The black vertical dashed lines mark the expected position of the
corresponding lines for a z∼ 6.92.



_4.1._ _Stellar masses_


Here we present stellar masses inferred from the integrated R100
spectra. We exclude W and L7 from this analysis as their stellar
continua are contaminated by those of the lens and the E galaxies, respectively. We note that, although some of the newly dis

Article number, page 8 of 27



covered sources are weak or undetected in a spaxel-by-spaxel
basis in the continuum images generated from the datacube,
they show continuum emission in their integrated spectra, which
typically are obtained after the combination of 25-50 spaxels.
The observed fluxes were corrected by a wavelength-dependent
aperture correction according to the empirical PSF derived by

Santiago Arribas et al.: The core of a protocluster at z=6.9



0.02


0.01



0.00



0.02



0.01



0.00





rest frame wavelength (Å)



**Fig.** **6.** R2700 spectrum showing the presence of two kinematically
distinct ionised gas components associated with the E galaxy, and the

                                          fainter and redshifted L7 source (see text). The panels represent the Hβ

[OIII] (top) and Hα-[NII] (bottom) spectral regions. The line profiles
are modelled with two Gaussians, distinguished with green and magenta
lines for E and L7, respectively. The total model profile is displayed in
red.


**Fig. 7.** 2D kinematic decomposition of the E and L7 galaxies. Moments
0, 1, and 2 maps for the E galaxy (upper) and the L7 source (bottom),
after the kinematic decomposition (see Sect. 3.3.3). From left to right,

[OIII] flux map (in units of 10 [−][18] erg s [−][1] cm [−][2] ), velocity field (km s [−][1] ),
and intrinsic velocity dispersion (σ 0 ) map (km s [−][1] ).


D’Eugenio et al. (2023), and by magnification (Appendix B).
As explained in Sect. 2.2, the errors in the flux provided by the
pipeline were rescaled by the standard deviation in the continuum, typically by factors of 2-3.
The SED fitting method is described in Pérez-González et al.
(2023) and D’Eugenio et al. (2023). In short, the NIRSpec R100
integrated spectra were compared to stellar population models
from the Bruzual & Charlot (2003) library, assuming a delayed
exponential star formation history characterised by a timescale
τ (taking values from 1 Myr to 1 Gyr in 0.1 dex steps) and age
_t_ 0 (ranging from 1 Myr to the age of the Universe at the redshift
of the galaxy). The stellar metallicity _Z_ was left as a free parameter, allowing us to take all the discrete values provided by the
Bruzual & Charlot (2003) library from 0.02 to 2.5 times solar.
Nebular (continuum and line) emission was taken into account
as described in Pérez-González et al. (2003, 2008). The attenuation of the stellar and nebular emission was modelled with a
Calzetti et al. (2000) law, with _A_ V values ranging from 0 to 3
magnitudes in 0.1 mag steps. The stellar mass is obtained by



scaling the mass-normalised stellar model to the spectrum. The
derived values are included in column 6 of Table 1. The quoted
stellar mass errors correspond to the uncertainties in the fit due
to flux errors, but they do not include systematic uncertainties
associated with the model assumptions, which are estimated to
be about factors of 1.5-2.
The stellar mass obtained for E (3.5±0.4 × 10 [10] M ⊙ ) is in excellent agreement with the one derived by Marrone et al. (2018)
(3.5±1.5 × 10 [10] M ⊙ ). The predicted value from the fit at 10 µm
(1.8 µJy) is also in good agreement with the actual MIRI measurement by Álvarez-Márquez et al. (2023) (1.6±0.3 µJy). For
this source we also perform a SED fit with CIGALE (Boquien
et al. 2019) following the prescription and initial parameters described in Álvarez-Márquez et al. (2023). They adopt a twocomponent SFH and a Lo Faro et al. (2017) attenuation law. We
combine the MIRI F1000W and FIR/submm data presented in
that work with the NIRSpec fluxes obtained in 22 pseudo-filters
between 1 and 5.2 µm. The derived value for the stellar mass is
2.1±0.5 × 10 [10] M ⊙, in agreement with the results above, taking
into account the expected systematic uncertainties.
The stellar masses for the newly discovered sources are
based on the R100 NIRSpec data only, as they were undetected
with MIRI (see Sect. 3.2). Nevertheless, we checked that the
MIRI detection limit was in all cases consistent with the predicted flux for the source at 10 µm according to the SED model.
We obtain a median stellar mass of ∼ 1.3 × 10 [9] M ⊙, with a range
of 0.35 - 3.4 × 10 [9] M ⊙ . We also note that recent work has shown
that stellar masses inferred by SED fitting without MIRI photometry may be overestimated by ∼ 0.4 dex for sources at the
high-redshift of SPT0311–58 (Papovich et al. 2023; Wang et al.
2024). Even taking into account this factor, our results indicate
that these galaxies have already assembled a significant amount
of stellar mass.

As commented above, we do not derive the stellar mass
for the W galaxy, since its flux at near-infrared wavelengths
is contaminated by the foreground lens galaxy. Therefore, we
adopt the stellar mass recently derived by Álvarez-Márquez et al.
(2023), which is based on a CIGALE SED fit using HST/WFC3,
JWST/MIRI, HERSCHEL/SPIRE, and ALMA photometry and
the Paα emission line flux. They find a stellar mass of (8.0 ±
2.4) × 10 [10] M ⊙ assuming a constant SFH, and report that a similar result is obtained when adopting a two-component SFH (for
further details, see Álvarez-Márquez et al. 2023). Further study
of the stellar population properties in SPT0311–58 is beyond the
scope of the present work.


_4.2._ _Nebular dust attenuation from the recombination lines_


The NIRSpec data presented here include the Hα and Hβ lines
and therefore they allow us to infer the nebular attenuation due to
dust from the commonly used Balmer decrement (i.e. Hα/Hβ).
In addition, for the E and the W galaxies, the dust attenuation
can also be obtained by combining the Hα fluxes measured with
NIRSpec with those for Paα recently obtained with MIRI/MRS
(Álvarez-Márquez et al. 2023). To convert recombination line
flux ratios into visual attenuation values (i.e. _A_ _V_ ) we take the intrinsic (dust-free) line ratio (Hα/Hβ) _int_ = 2.79 given by Reddy
et al. (2023), which is based on photoionisation modeling with
CLOUDY version 17.02 (Ferland et al. 2017) for Case B recombination (T _e_ =10000 K, n _e_ = 100 cm [−][3] ). This intrinsic line ratio
leads to _A_ _V_ values that are ∼ 0.086 mag higher than if (Hα/Hβ) _int_
= 2.86 (Osterbrock 1989) is adopted. We also use the Calzetti
et al. (2000) law as, e.g. in Domínguez et al. (2013). For com

Article number, page 9 of 27

_A&A proofs:_ manuscript no. main


**Table 1.** ISM properties, star formation, and stellar masses for sources in SPT0311–58


ID Hα flux SFR(Hα) _A_ _V_ SFR(Hα) (dust-corr.) 12+log(O/H) _M_ ⋆
(10 [−][18] ergs [−][1] cm [−][2] ) (M ⊙ yr [−][1] ) (mag.) (M ⊙ yr [−][1] ) (×10 [9] M ⊙ )
(1) (2) (3) (4) (5) (6) (7)
E 18.8 ± 0.8 62. ± 2. 1.7 ± 0.3 231. ± 10. 8.37 ± 0.06 35.4 ± 4.3
2.4 ± 0.3 [1] 377. ± 20. [2] 21.0 ± 5.2 [5]

E _ext_ 11 ± 2. 32. ± 3. (0.85) (61.) [7]

W 4.5 ± 0.9 8. ± 1. 5.8 ± 0.6 [1] 603. ± 121 [2] (80. ±24.) [6]

W _ext_ 5.3 ± 1.4 9. ± 1. (2.00) (39.) [7]

C1 1.5 ± 0.3 5.5 ± 1. 0.7 ± 0.6 9.2 ± 1.8 8.37 ± 0.10 1.60 ± 0.23

C2 0.92 ± 0.25 2. ± 0.4 1.0 ± 0.9 4.2 ± 1.1 7.97 ± 0.20 2.88 ± 0.68
C3 [3] 1.3 ± 0.4 6.2 ± 1.2 2.2 ± 1.6 33. ± 10. 8.56 ± 0.10 3.41 ± 0.94

L1 1.2 ± 0.3 2.9 ± 0.4 1.9 ± 0.8 12. ± 3. 7.86 ± 0.16 0.35 ± 0.04

L2 0.51 ± 0.07
L3 [3] 0.47 ± 0.25 1.2 ± 0.4 (0.85) (2.3) [7] 1.48 ± 0.35
L4 0.64 ± 0.22 1.1 ± 0.3 (0.85) (2.1) [7] 1.26 ± 0.19
L5 [3] 1.6 ± 0.4 3.9 ± 0.6 0.8 ± 0.6 7.0 ± 1.7 7.79 ± 0.35 1.17 ± 0.18
L6 0.49 ± 0.18 1.2 ± 0.3 (0.85) (2.0) [7] 0.56 ± 0.12
L7 [4] 0.85 ± 0.20 1.1 ± 0.3 (0.85) (2.0) [7] (7.58 ±0.46)


**Notes.** Column 1: Source identification. Column 2: Observed Hα flux obtained by averaging values from the R2700 and R100 spectra, if S/N >
3. The R100 fluxes were reduced by 10% to account for a known calibration factor (see Appendix A). For E _ext_, W and W _ext_, only R100 data were
used due to the low S/N of their R2700 spectra. In addition, for E _ext_ the fits could not resolve the Hα and the [NII] lines, and thus an average
factor of 0.77 was applied to account for the [NII] emission when deriving the corresponding Hα flux. Further details are provided in Appendix
A. Column 3: SFRs obtained with the relation of Kennicutt & Evans (2012). No dust correction is applied. For galaxies C2 and L1-L5 values
have been corrected by a factor 0.5 to account for their metallicity (see text). Column 4: Visual attenuation inferred from the Balmer decrement
(Hα/Hβ). For E and W the values inferred from Paα/Hα are also given. For C1 and C2, _A_ _V_ was obtained from the R100 spectra only, as the Hβ
R2700 fluxes have significantly lower S/N. Column 5: SFR after correction for the visual attenuation in column 4. The SFRs in columns 3 and 5
are corrected for the lensing magnification factors (see Appendix B) and the finite apertures used (Appendix A). Column 6: Metallicities based on
the Curti et al. (2017) calibration (see Sect. 4.4). For L7, the metallicity is not well constrained. Column 7: Stellar masses (see Sect. 4.1). They take
into account aperture and magnification corrections. The uncertainties correspond to 16- and 84- percentiles taking into account the flux errors,
but they do not include systematic uncertainties due to the model assumptions. [1] _A_ _V_ (Paα/Hα) using an aperture of 1 [′′], as in Álvarez-Márquez et al.
(2023). [2] Corrected with _A_ _V_ (Paα/Hα). [3] These sources are close the edge of the FoV, and subject to larger calibration uncertainties. [4] For this
galaxy the values are derived from the 2D kinematic decomposition (see text in Sect. 3.3.3). [5] Stellar mass inferred with CIGALE (see text). [6]

Stellar mass derived by Álvarez-Márquez et al. (2023) [7] Taking an average Av (see text).



parison, adopting the Cardelli et al. (1989) reddening law, the derived _A_ _V_ values would be 10% lower (Rodríguez Del Pino et al.
2024). The _A_ _V_ values for the various sources in SPT0311–58 are
presented in Table 1.

For the E galaxy, we find that the value inferred from Hα/Hβ
(i.e. _A_ _V_ (Hα/Hβ) = 1.7 ± 0.3) is lower than the one obtained from
Paα/Hα ( _A_ _V_ (Paα/Hα) = 2.4 ± 0.3) [2] . In local dusty objects such
as luminous and ultraluminous infrared galaxies (i.e. LIRGs and
ULIRGs, respectively), several authors have also reported that
the visual attenuation derived from Balmer lines ratios is lower
than that obtained from ratios involving infrared lines (e.g. Piqueras López et al. 2013; Giménez-Arteaga et al. 2022). Moreover, for intermediate redshifts (i.e. 1 < z < 3.1) Reddy et al.
(2023) have found that ratios involving Paschen lines lead to
reddening measurements that are often larger than those obtained with the Balmer decrement. These results are generally
explained by assuming that part of the flux in the infrared lines
comes from regions that are optically thick for the Balmer lines.
In other words, due to the lower obscuration at longer wavelengths, Hβ, Hα and Paα trace increasingly deeper dusty regions,
which leads to the above-mentioned differences.


2 Álvarez-Márquez et al. (2023) find a lower limit for _A_ _V_ (Paα/Hα) 4.3 mag, which is conflicting with the present results. This discrepancy
can be explained by the inconsistency in the upper limit for the Hα
found with MIRI and the NIRSpec measurement.


Article number, page 10 of 27



For the W galaxy, we cannot reliably infer _A_ _V_ (Hα/Hβ), as in
the R100 spectrum Hβ is blended with Paα from the lens galaxy,
and in the R2700 spectrum the Hα and Hβ fluxes are noisy due to
the broadening induced by the large range in velocities covered
by the aperture. However, the Hα and Paα fluxes obtained with
NIRSpec (R100) and MIRI, respectively, imply _A_ _V_ (Paα/Hα) =
5.8 ± 0.6. This value confirms that W is significantly more attenuated by dust than E, as previous studies (e.g. Marrone et al.
2018) have already shown, based mainly on far infrared measurements (see ALMA continuum map at 160 µm in Fig. 2).


∼
For several of the newly discovered z 6.9 sources (i.e. C1-3,
L1, L5) the _A_ _V_ (Hα/Hβ) could be estimated. The obtained values
range from ∼ 0.7 to 2.2 mag, and indicate that in general they
have lower attenuation than E and W. We note that the uncertainties for the individual values are large, and in some cases
they are also consistent with low or no attenuation. The lack of
ALMA continuum emission in these sources also supports a low
dust content. The regions in the eastern part (C1, C2, L5) have,
on average, a lower attenuation (< _A_ _V_ - ∼ 0.85 mag) than the ones
in the western region (C3, L1; < _A_ _V_ - ∼ 2 mag). We used these
average values to estimate the attenuation for sources that do not
have reliable Hβ fluxes, including the extended regions W _ext_ and
E _ext_ (see Table 1).

Santiago Arribas et al.: The core of a protocluster at z=6.9








































|1.2|Col2|Col3|
|---|---|---|
|2.0<br>1.5<br>1.0<br>0.5<br>0.0<br>0.5<br>log([NII]/H )<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>1.2<br>log([OIII]/H )<br>ES<br>ENa<br>ENb<br>E~~Nc~~<br>C1<br>C2<br>C3<br>L1<br>L5<br>E<br>L7<br>JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|ES<br>ENa<br>ENb<br>E~~Nc~~<br>C1<br>C2<br>C3<br>L1<br>L5<br>E<br>L7<br>JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|ES<br>ENa<br>ENb<br>E~~Nc~~<br>C1<br>C2<br>C3<br>L1<br>L5<br>E<br>L7<br>JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|
|2.0<br>1.5<br>1.0<br>0.5<br>0.0<br>0.5<br>log([NII]/H )<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>1.2<br>log([OIII]/H )<br>ES<br>ENa<br>ENb<br>E~~Nc~~<br>C1<br>C2<br>C3<br>L1<br>L5<br>E<br>L7<br>JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|
|2.0<br>1.5<br>1.0<br>0.5<br>0.0<br>0.5<br>log([NII]/H )<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>1.2<br>log([OIII]/H )<br>ES<br>ENa<br>ENb<br>E~~Nc~~<br>C1<br>C2<br>C3<br>L1<br>L5<br>E<br>L7<br>JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|JADES:z<br>6 C+23<br>CEERS:z<br> 5.6 S+23<br>GA-NIFS: AGN@z=5.5 Ü+23<br>(coloured): This work|0.5<br>0.0<br>0.5<br>I]/H )|



**Fig. 8.** Classical N2-BPT diagram and ionization map for the z ∼ 6.9 sources in SPT0311-58. Left: BPT diagram colour coded according to the

[OIII]λ5007/Hβ value. The line ratios are derived from the integrated R2700 spectra, and include the subregions within E and the five external z
∼ 6.9 sources with reliable line fluxes. Upper limits correspond to 3σ. Grey-shaded regions show the zones of the diagram covered by 70, 80, and
90 percent of the local SDSS sample of star forming galaxies and AGN. (York et al. 2000, Abazajian et al. 2009). Below the dashed line, local
galaxies are ionised by SF (Kauffmann et al. 2003), while above the dotted line the presence of AGN is required (Kewley et al. 2001). The region
beneath the black solid line corresponds to LI(N)ERs (Cid Fernandes et al. 2010). The magenta line is the locus of z ∼ 2–3 star-forming galaxies
found by Strom et al. (2017). The black symbols correspond to other galaxies at z > 5 observed with JWST/NIRSpec (C+23: Cameron et al. 2023;
S+23: Sanders et al. 2024; Ü+23: Übler et al. 2023). Right: Spatial distribution of the different galaxies in the SPT0311-58 system. The apertures
used (Appendix A.1) are colour coded according to their [OIII]λ5007/Hβ values, as in the left panel.


_4.3._ _Emission line ratio diagnostic diagrams_



We now discuss the excitation conditions in the different highz galaxies identified in SPT0311–58. In Fig. 8 (left) we present
the classical _N_ 2 ≡ [NII]/Hα vs. _R_ 3 ≡ [OIII]/Hβ BPT diagram
(hereafter N2-BPT; Baldwin et al. 1981). We include the z ∼ 6.9
sources with reliable line flux ratios (i.e. C1, C2, C3, L1, L5,
L7), in addition to the subregions within E. The line fluxes have
S/N - 3, except for the [NII] flux of some sources for which
upper limits are provided. Colours are assigned according to the

[OIII]/Hβ value. The figure shows the zones of the diagram covered by the z ∼ 0 SDSS galaxies (Abazajian et al. 2009) (shaded
grey), together with several well-established lines that demarcate
the different excitation regimes at low z. We also include in the
plot (magenta line) the locus of the intermediate redshift (i.e. z

∼
2–3) star-forming galaxies from the KBSS-MOSFIRE survey
(Strom et al. 2017), and results at redshifts higher than 5 recently
obtained with JWST (Cameron et al. 2023, Sanders et al. 2024,
Übler et al. 2023).

Fig. 8 shows that the sources in SPT0311–58 occupy zones
of the N2-BPT diagram barely populated by local galaxies, and
are distributed along the SF/AGN demarcation lines at z=0, covering more than 0.7 dex in _R_ 3. Although most of the sources
occupy the composite/AGN zones of local galaxies, they do not
exhibit clear evidence of AGN activity (e.g. Balmer broad lines
or signs of strong outflows). However, we do not exclude the
presence of AGN, as at high-z their associated outflows do not
appear to be very prominent (Maiolino et al. 2023, Carniani et al.
2024, Scholtz et al., in prep.). These z ∼ 6.9 sources are in a region shifted by 0.1-0.3 dex (in _N_ 2 or _R_ 3) with respect to the
star-formation locus at z∼ 2-3, enlarging further the offset with
respect to the z=0 population. We note that none of the galaxies
are in the local LI(N)ER part of the diagram, despite the likely
presence of shocks according to the observed kinematics (see
Sect. 5, and Spilker et al. 2022). The sources in SPT0311–58



**Fig. 9.** _R_ 23 – _O_ 32 diagnostic diagram. The blue dots represent the galaxies in SPT0311–58 and are based on R2700 fluxes (except when the
line was only detected in R100). They are corrected for attenuation and
aperture. Grey-shaded regions show the zones covered by 80, 90, and 99
percent of the local SDSS sample of star forming galaxies (York et al.
2000, Abazajian et al. 2009). Green and red isocontours correspond to
mass ranges log( _M_ ⋆ /M ⊙ ) = [8.5 - 9.5] and [9.5 - 10.5], respectively. The
black symbols are for stacked spectra of other high-z samples observed
with JWST/NIRSpec, as indicated by the labels (C+23: Cameron et al.
2023; S+23: Sanders et al. 2024).


with the highest _R_ 3 (i.e. C2, L1, and L5) are in similar regions of
the N2-BPT diagram as other galaxies at z > 6 recently observed
with JWST (e.g. Cameron et al. 2023, Sanders et al. 2024), and
also have faint or undetected [NII]λ6583 fluxes.

The spatial distribution of _R_ 3 reveals interesting trends (Fig.
8, right panel). First, the sources with the lowest _R_ 3 (ES, C3) are


Article number, page 11 of 27

_A&A proofs:_ manuscript no. main


found within or close the massive galaxies E and W. Second, E
shows a clear variation in _R_ 3 along its major axis, with increasing values from south to north (i.e. ES, ENa, ENb, ENc). We note
that L7 is seen in projection over the main structure of E, but it is
a separated source (see Sect. 3.3.3). Third, the sources with the
highest _R_ 3 (C2, L1, L5) are found in the external regions.



We now compare the observed positions in the N2-BPT diagram with the predictions of the theoretical study by Hirschmann
et al. (2023) based on the coupling of the state-of-the-art cosmological IllustrisTNG simulations (Springel 2010) with newgeneration nebular-emission models (Hirschmann et al. 2019).
While sources in SPT0311–58 show a wide range in _R_ 3 (i.e. 0.25
– 1), TNG50 galaxies at z ∼ 5-7 have _R_ 3 - 0.60 (Hirschmann
et al. 2023, their Fig.6). The external sources (i.e. C1, C2, L1,
L5) have observed values within this predicted range. However,
for regions within or close the two main galaxies (i.e. ES, ENa,
ENb, ENc, C3) the observed _R_ 3 are < 0.60, and only agree with
the theoretical predictions at low or intermediate redshifts (z∼
0.5–3). Therefore, these galaxies seem to have exceptional properties for their z, according to theoretical expectations.


In Fig. 9, we present the galaxies in the dust-corrected
_O_ 32- _R_ 23 diagram. _R_ 23 ≡ log(([OIII]λλ4959,5008 +

[OII]λλ3726,3729)/Hβ) is a proxy of the total excitation,
while _O_ 32 ≡ log([OIII]λ5008/[OII]λλ3726,3729) is sensitive to
the ionisation parameter and the metallicity (Kewley et al. 2019,
Cameron et al. 2023). This diagram reflects again the different
ISM conditions of the sources in SPT0311–58 in comparison
with those commonly found in local galaxies. The large range in
_O_ 32 indicates a significant variation of the ionisation parameter
and/or the metallicity among the sources in the FoV. It also
shows the dichotomy between the external regions (C2, L1, L5)
and those associated with the main structures of the E and W
galaxies (C3, ES, ENa, ENb, ENc), with the latter group having
lower _O_ 32. To take into account the interdependence of stellar
mass and metallicity, which are defined by the mass-metallicity
relation (MZR; e.g. Curti et al. 2024), in Fig. 9 we distinguish
two mass ranges for the local sample: log( _M_ ⋆ /M ⊙ ) = [8.5 - 9.5]
and [9.5 - 10.5]. The former is in principle more appropriate for
comparison with the newly discovered sources, while the latter
covers the mass of the E galaxy, and therefore adequate for its
subregions. The figure shows that again in this diagram C3 and
most of the regions within E, have positions closer to those
occupied by local galaxies. The external sources C2, L1, and L5
occupy a distinct position in the diagram, displaced with respect
to local galaxies with similar stellar mass. They are close to
the average position of the field galaxies at z ∼ 5.6 in CEERS
(Sanders et al. 2024, log( _M_ ⋆ /M ⊙ ) = 8.57), but seem to have a
lower _O_ 32 value with respect to the less luminous galaxies in
JADES (Cameron et al. 2023). Still, the low statistics prevent us
to perform a solid comparison with these samples.


In summary, we find that the ISM conditions in the sources of
SPT0311-58 are very diverse. While some of these z ∼ 7 objects
have properties similar to galaxies at these redshifts recently observed with JWST, others have conditions closer to those found
at lower redshifts. Most occupy the region of SF/AGN composite ionisation, and none are in the local LI(N)ER region despite
the likely presence of shocks. The diagnostic diagrams indicate
significant differences in the ionisation parameter and/or in the
metal content across the observed sources. In the next section we
study in more detail the metal content in the system.


Article number, page 12 of 27



**Fig. 10.** Metallicity map based on the calibrations of Curti et al. (2017,
2020b) in the 12+(O/H) scale. For the E galaxy, spaxel-by-spaxel information is provided. For the external regions, the value obtained from the
integrated spectra is assigned to the entire aperture. The region where
the galaxy L7 appears in projection over E, is indicated with a dotted
line. The line fluxes were corrected with the mean _A_ _V_ value for the apertures. The faint grey lines correspond to two low-level isocountours of
the Hα emission (Fig. 2 (c)) (see text).


_4.4._ _Metallicity_


In Fig. 10, we present the metallicity map of SPT0311-058 according to the calibration of Curti et al. (2017, 2020b). This calibration is based on local samples, but it has the advantage of
covering well the metallicity range observed in the system, and
it shows relatively low scatter. We also comment below the results when using the calibration by Sanders et al. (2024), which
is based on samples that cover well the redshift of SPT0311–
58, but presents larger scatter than local ones due to the lower
number of sources available and potential differences in the ISM
conditions at high-z. We followed the procedure developed by
Curti et al. (2024), which explores the log(O/H) parameter space
with a Markov Chain Monte Carlo (MCMC) algorithm and finds
the maximum likelihood taking into account the uncertainties of
the observed line ratios and the dispersion of the individual index calibrations. For the E galaxy, the metallicity is derived for
each spaxel (after a 3 x 3 binning) while for the external sources,
and due to their lower S/N, the integrated spectra are used to
derive a global value. For E, C1, C2 and L1 the metallicity is
inferred from the _R_ 2, _R_ 3, _R_ 23, _O_ 32, and _R_ _[ˆ]_ indexes, where _R_ 2 ≡
log([Oii] λλ3726, 29/Hβ) and _R_ _[ˆ]_ ≡ 0.47 _R_ 2 + 0.88 _R_ 3, as defined
by Laseter et al. (2024). For C3, _R_ 3 and _N_ 2 were used, while for
L5 and L7 only _R_ 3 was available due to the lack of reliable line
fluxes to derive other indexes. In Table 1 the individual metallicity values are presented.
Fig. 10 shows that the metallicity spans about 0.8 dex across
the FoV. On the one hand, the southern regions of E and C3
have the highest metallicities with values around 8.4-8.6 in the
12+log(O/H) scale. On the other hand, external galaxies C2, L1,
and L5 have low metal content, with values in the range ∼ 7.68.1. This pattern is consistent with the mass metallicity relation
(MZR, Curti et al. 2024), according to which the most massive galaxies (and therefore their subregions) have the highest
metallicities, and suggests that C3 is closely associated with the
massive W galaxy. The northern region of E, which shows low

Santiago Arribas et al.: The core of a protocluster at z=6.9



metallicity and therefore differs from this general behaviour, is
discussed below. The calibration by Sanders et al. 2024 leads to
qualitatively similar results, although it finds higher metallicity
(by ∼ 0.2 dex) in the metal rich regions C1, and E, while leaving
unaltered the values for C2 and L1, and suggesting lower metal
content in L5 (by ∼ 0.2 dex). Therefore, this calibration indicates an even larger range in metallicty across the FoV, though it
also increases the associated uncertainties of individual determi
nations.


Interestingly, the E galaxy shows a prominent metallicity
gradient along its major axis with a total peak-to-peak variation
of ∼ 0.7 dex, and also local inhomogeneities at subkpc scales.
The southern regions are the most metal-rich (i.e. ∼ 8.50), while
the lowest metallicity (i.e. ∼ 7.8) is found to the northwest. This
metal-poor region is adjacent to a zone of diffuse Hα (see grey
isocontours in Fig. 10) and [CII] emission (Fig. 2 c and f), indicating the presence of ionised and neutral gas. This suggests
that the accretion of low metallicity gas into the main structure
of E in the northwest may be the cause for the observed gradient. Gas accretion has been proposed to explain metal gradients
and inhomogeneities at high- and low-z (e.g. Cresci et al. 2010,
Kumari et al. 2017, Curti et al. 2020a, Rodríguez Del Pino et al.
2024). In Sect. 6.2, we will discuss further this scenario, as well
as other potential alternatives (i.e. merger event, outflows), also
taking into account the kinematic properties of the E galaxy.


Litke et al. (2023) have recently found a nearly solar metallicity in the massive galaxies of SPT0311–58 based on the observed far-infrared [OIII]λ 88µm /[NII]λ 122µm emission line
ratio, and the calibration proposed by Pereira-Santaella et al.
(2017) (i.e. 0.8 ± 0.4 Z ⊙ for E; 1.4 ± 1.0 Z ⊙ and 0.9 ± 0.4 Z ⊙ for
the northern and southern regions of W, respectively). To compare their results with our findings for E, we computed the global
metallicity over the integrated E spectrum. Using the _R_ 2, _R_ 3,
_R_ 23, _O_ 32, and _R_ _[ˆ]_ indexes and the calibration by Curti et al. (2017,
2020b), we infer an average value of 0.48 ± 0.07 Z ⊙ . Although
the difference with the Litke at al. result is not significant taking into account the uncertainties, it could be interpreted as due
to the different regions probed by the FIR and the optical lines.
While the FIR offers access to deeper, dustier, and likely more
metal-rich zones, the optical lines come from the less extincted
and likely more metal-poor regions. Finally, the comparison of
our metallicity value for C3 (i.e. 0.75 ± 0.18 Z ⊙ ), with the results
by Litke et al. (2023) for the southern part of the W galaxy show
good agreement.


In summary, we find a wide range of metallicities (by ∼ 0.7
dex) across the galaxies in SPT0311–58. The newly discovered
galaxies seem to have lower metal content than the relatively
metal-rich massive E and W galaxies. The E galaxy also shows
a metallicity gradient that is likely evidence for the presence of
pristine gas accretion. In Sect. 6.2 we discuss further this and
other alternative scenarios, also considering the kinematic properties of the system.


_4.5._ _H_ α _-based star formation_


The present observations allow us for the first time to measure
Hα fluxes in this system, and therefore to infer the unobscured
ongoing star formation using this well-calibrated tracer. We note
that SPT0311–58 is at about the highest z at which Hα-based
SFR can be derived at the sensitivity and angular resolution provided by NIRSpec (i.e. for z> 7, Hα is redshifted outside the
NIRSpec range).



We estimate the nearly instantaneous (i.e. last 3-10 Myrs)
star formation rate (SFR) from the Hα luminosity following the commonly used expression provided by Kennicutt &
Evans (2012) (see also Murphy et al. 2011; Hao et al. 2011):
SFR(Hα)/(M ⊙ yr [−][1] ) = 5.37 × 10 [−][42] L(Hα)/(erg s [−][1] ).
This relation presumes constant SFR over the mentioned
timescale, solar metallicity and a Kroupa IMF (Kroupa 2001)
3, and also assumes that all ionising photons actually ionise the
ISM. We note, however, that changing some of these assumptions may have significant effects. For instance, for subsolar
metallicities the SFRs provided by this equation should be corrected down because metal poor massive stars are more efficient
in producing ionising photons, which leads to higher L(Hα) per
unit of SFR as discussed by Reddy et al. (2022) (see also Shapley et al. 2023). To take into account this effect, and based on
the results of the previous section, the SFRs obtained with the
expression quoted above for galaxies C2, L1-L5 have been corrected accordingly by a factor 0.5. For the more metal-enriched
E and W galaxies (and C1 and C3), we have maintained the solar
abundance assumption. This allows us a more direct comparison
with previous SFR estimates for E and W (Marrone et al. 2018,
Álvarez-Márquez et al. 2023), and with determinations based
on general calibrations (e.g. Total Infrared Luminosity L(TIR)SFR, Calzetti 2013) that have used solar metallicity. The individual Hα fluxes and SFRs(Hα), corrected and uncorrected for
dust attenuation, are presented in Table 1.
As we can see in the table, and also in panel c of Fig. 2,
the main body of the E galaxy is the region in the FoV with the
highest Hα flux, and therefore where most of the unobscured (i.e.
uncorrected by dust attenuation) star formation is taking place at
a rate of ∼ 62 M ⊙ yr [−][1] . The dust-corrected SFR (377 M ⊙ yr [−][1] )
represents a large fraction (i.,e. ∼ 70-80 percent) of the total SFR
obtained by Marrone et al. (2018) from a SED analysis which includes the far-IR (ALMA) dust continuum emission (545 ± 175
M ⊙ yr [−][1] ), or by using the L(TIR)-SFR calibration by Calzetti
(2013) (∼ 466 M ⊙ yr [−][1] ). In addition to the Hα flux associated
with E, a low surface brightness Hα emission extends beyond its
main structure, particularly in the direction of source C1. This
external Hα flux is obtained integrating within aperture E _ext_ (see
Fig. A.1), and has an associated unobscured SFR(Hα) of ∼ 32
M ⊙ yr [−][1] (∼ 61 M ⊙ yr [−][1] dust-corrected).
For W the inferred unobscured SFR(Hα) is ∼ 8 M ⊙ yr [−][1],
which is a tiny fraction of the SFR obtained by Marrone et al.
2018 from a SED analysis including the FIR emission (i.e. 2900
+/- 1800 M ⊙ yr [−][1] ), or from the L(TIR)–SFR relation by Calzetti
2013 (3350 M ⊙ yr [−][1] ). In this case, the attenuation correction
factor is extremely large, as _A_ _V_ is 5.8 magnitudes. The dustcorrected SFR(Hα) is ∼ 600 M ⊙ yr [−][1], which is about one-fifth
of the total SF inferred including the far-infrared dust emission.
This suggests that W hosts a large fraction of star formation that
is totally obscured at rest-frame optical and near-IR wavelengths.
We note that a detailed comparison of the SFR obtained with
different tracers should also take into account the timescale assumed for their calibration and the star formation history (SFH)
of the source under study. For example, post-starburst (PSB)
galaxies (where star formation terminated rapidly and recently)
have systematically higher SFR(FIR)s than what is estimated
from recombination lines alone. This is observed both in the local Universe (Baron et al. 2023) as well as at z ∼ 1 (Wu et al.
2023). However, these PSB galaxies also display lower nebular
attenuation than what we infer for the W galaxy; in our case, be

3 Results for a Chabrier IMF (Chabrier 2003) are nearly identical (c.f.
Kennicutt & Evans 2012).


Article number, page 13 of 27

_A&A proofs:_ manuscript no. main



cause we are dealing with an extremely dusty galaxy, we favour
the star-forming interpretation, and explain the discrepancy between the SFR(Hα) and SFR(FIR) as due to heavy dust attenuation. The most rigorous approach would be to infer the full SFH,
but this is beyond the scope of the present study.
For the newly discovered sources at z ∼ 6.9, the unobscured
SFR(Hα) ranges from 1 to 6 M ⊙ yr [−][1], and totalling 14 M ⊙ yr [−][1] .
The sources with _A_ _V_ measurements (i.e. C1, C2, C3, L1, L5),
have individual dust-corrected SFR(Hα) ranging from ∼ 4 to 30
M ⊙ yr [−][1] . For the other sources, the star formation is not well
constrained as _A_ _V_ cannot be reliably derived (see Sect. 4.2). Using for them the average _A_ _V_ derived for the other sources, the
combined dust-corrected SFR(Hα) for all these objects is 74 M ⊙
yr [−][1], a small amount compared with the total SFR taking place
in E and W. As the new sources are undetected in ALMA continuum, their dust-corrected SFR(Hα) likely represent the total
SFR.

In summary, we find significant unobscured ongoing star formation activity within and around the E galaxy (∼ 94 M ⊙ yr [−][1] ).
The dust-corrected SFR(Hα) (∼ 430 M ⊙ yr [−][1] ) recovers a large
fraction of the total SFR obtained including the FIR emission.
In contrast, for W the current unobscured SFR(Hα) is small (8
M ⊙ yr [−][1] ), representing a tiny fraction of the total SFR of this
galaxy. An important fraction of the SFR in this galaxy is totally
obscured at optical and near-IR wavelengths, and cannot be recovered with the attenuation correction. As for the newly discovered external sources, their unobscured SFR(Hα)s are relatively
modest with individual values ∼ 1 - 6 M ⊙ yr [−][1] . Correction from
dust still leaves the combined contribution to these sources to the
total SFR of the system as minor (i.e. ∼ few percent).


**5.** **Kinematic properties**


This section is devoted to the kinematic properties of the different sources of SPT0311–58. First, we present the relative motion and velocity dispersion of the newly discovered sources at
z ∼ 6.9. We also derive their dynamical masses, and compare
them with the stellar masses. Second, we focus in more detail on
the E and W galaxies, and discuss the kinematics for the warm
and cold gas phases inferred from NIRSpec and ALMA, respectively.


_5.1._ _Newly discovered z_ ∼ _6.9 sources: Relative velocities,_
_velocity dispersions, and dynamical masses_


Fig. 11 (upper-right panel) shows the large-scale velocity field in
SPT0311–58 derived from the R2700 [OIII] line. In this figure
the differences in redshift are interpreted as relative velocities [4],
taking z = 6.902 the origin for the velocities (i.e. the redshift of
the most massive W galaxy inferred from the [CII] line, Sect.
5.3). The figure shows that the ten newly discovered galaxies
have a very large range of (projected) velocities: from -595 km
s [−][1] for L3 up to +932 km s [−][1] for C1 (see Table 2 for the individual redshifts). These velocities seem randomly distributed
across the FoV, with sources with high positive and negative values relatively close in projection (e.g. L2 and C2, L3 and C1).
This significant spread in velocities suggests that the mass of the


4 We note that, if the observed redshifts were alternatively interpreted
as spatial separations only, the proper distance between the two furthest
separated galaxies (i.e, L3 and C1) would be about 3.6 Mpc. This value
is similar to the rough estimate of the extent for the overdense region

∼
with submm galaxies ( 2.6 Mpc; Wang et al. 2021).


Article number, page 14 of 27



halo must be very large. In Sect. 6 we discuss further the relative
motions of the sources within the system.
The integrated velocity dispersion (σ, see Table 2) can be
used to estimate the dynamical mass (M dyn ) of the galaxies
through the formula:


_M_ dyn = _K_ [σ] [2] _[R]_ _[e]_, (1)

_G_


where _R_ _e_ is the effective radius, _G_ is the gravitational constant,
and _K_ is a factor that depends on the mass distribution in the
galaxy. We adopt _K_ =5±0.1, following the best-fitting virial relation calibrated by Cappellari et al. (2006). We also applied the
correction suggested by Übler et al. (2023), to account for the
differences in the integrated velocity dispersion of the ionised
gas and the stars found by Bezanson et al. (2018). For the present
range of integrated σ, this ∆ log(σ/(km s [−][1] )) correction varies
from 0. to +0.18. For the determination of the size, we fit the
emission in each source with a 2D Gaussian, and estimate _R_ _e_
from the largest of the two standard deviations provided by the
fit, after deconvolving with the PSF. To derive the properties of
the PSF, we used the data cube of the standard star (Sect. 2.5).
We first try to infer the sizes from a panchromatic image generated from the R100 cube in the 1-5 µm spectral range. This led
to acceptable results for sources well detected in the continuum
image (i.e. C1, C2, C3). For the other objects we used the [OIII]
image instead. The derived _R_ _e_ values are also given in Table 2.
The dynamical masses for the newly discovered galaxies are
in the range ∼ 10 [9] – 10 [10] M ⊙ (Table 2). Then, although these objects are significantly less massive than the two main galaxies in
SPT0311–58, they contain a substantial amount of mass for their
redshifts. In Figure 12 we compare these dynamical masses with
the stellar masses obtained in Sect. 4.1. The figure shows that on
average _M_ dyn is larger than _M_ ⋆ by a factor 2-3. This factor may
be even higher due to the systematic overestimation of _M_ ⋆ when
MIRI photometry is not included in the SED fitting (Papovich
et al. 2023; Wang et al. 2024). This result suggests that, as expected, these galaxies may have an important fraction of their
mass in gas (Tacconi et al. 2020). Additionally, or alternatively,
they might also have substantial amounts of dark matter, as suggested by recent NIRSpec observations of high-z galaxies (de
Graaff et al. 2024). We note that, in Figure 12, we also include
the E galaxy, for which we derive a dynamical mass of 6.0 ± 2
×10 [10] M ⊙ . Marrone et al. (2018) find a total baryonic (i.e. stars,
gas, and dust) mass of 7.5 ± 3.5 ×10 [10] M ⊙ and Álvarez-Márquez
et al. (2023) 4-5 ×10 [10] M ⊙ . Therefore, its M dyn determination is
consistent with previous results within the estimated uncertainties.


_5.2._ _E galaxy_


The kinematic maps for the E galaxy as inferred from the [OIII]
lines are presented in the upper panels of Fig. 7. The velocity
field shows a significant gradient of ∼ 200 km s [−][1] along the major
axis. The isovelocity lines clearly deviate from what is expected
for a regular rotating disc, especially to the northwest where they
are strongly twisted. For this spatially extended source, we are
able to measure the intrinsic velocity dispersion (σ 0, moment
2 in Fig. 7). Similarly to the velocity field, the σ 0 map deviates
from the expectation for a rotating disc, as it shows local changes
at subkpc scales, and higher values at the edges than to the centre. It also shows a general trend along the major axis with, on
average, higher values to southeast (σ 0 ∼ 120-145 km s [−][1] ) than
to the northwest (σ 0 ∼ 75-100 km s [−][1] ). The velocity dispersion

Santiago Arribas et al.: The core of a protocluster at z=6.9















































100


200



































100







**Fig. 11.** Kinematic maps of SPT0311–58. Upper panels: Large-scale velocity fields from the high resolution NIRSpec IFU spectra in the [OIII]Hβ complex (left), from the [CII]λ158 line observed with ALMA (centre), and difference (right). Lower panels: similar maps for the intrinsic
velocity dispersion (σ 0 ). The NIRSpec maps were obtained after a 3 × 3 spaxel binning, except for L2, L3, L4, L6 and L7 for which, due to
their low S/N, the values from the integrated spectrum were assigned to the entire extraction aperture. The values for L7 were obtained after the
kinematic decomposition of two overlapping systems (Sect. 3.3.3). The relative velocity values are in km s [−][1], taking as reference a redshift of
6.902. The NIRSpec velocity dispersions are corrected for the instrumental broadening according to the dispersion curves provided by Jakobsen
et al. (2022)























**Fig. 12.** Comparison between the dynamical and the stellar masses for
sources in SPT0311–58. For the E galaxy the position for the stellar
mass value obtained with CIGALE is indicated with Ec (see sections
5.1 and 4.1).


from the integrated spectrum (i.e. σ), which also includes the
global velocity gradient, is 155 ± 3 km s [−][1] . The median intrin


sic velocity dispersion (σ 0 ) over the area covered by Fig. 7 is
113 ± 19 km s [−][1] . From the fits with a 3 × 3 binning (Fig. 11),
which cover a larger area but are slightly contaminated by L7, the
median σ 0 = 120 km s [−][1] . These values are above the extrapolation of the average σ 0 − _z_ evolution found by Übler et al. (2019)
(i.e. σ 0 ∼ 70-80 km s [−][1] at z=7). Interpreting the velocity shear as
large-scale rotation and correcting by the inclination suggested
by its elliptical morphology, we obtain a rotational support factor, v/σ 0, of ∼ 1, significantly smaller than in other lower redshift
DSFGs (Lelli et al. 2021, Parlanti et al. 2024, Bik et al. 2023,
Übler et al. 2024). All these characteristics clearly indicate that
the ionised gas disc in the E galaxy in SPT0311–58 is not settled
yet.


We now compare the kinematic properties of the warm and
the cold gas phases, as inferred from NIRSpec and ALMA, respectively. The upper-right panel of Fig. 11 shows that, excluding the region where the source L7 appears in projection, the
warm and cold gas components in E have similar velocities,
though the latter recedes on average ∼ 25 km s [−][1] faster. This behaviour is not homogeneous, and in some spaxels towards the
south and east the warm gas has receding velocities of up to
∼ +80-100 km s [−][1] larger. These differences indicate that the
ionised and neutral gas components probed by NIRSpec and
ALMA are not cospatial. This may happen when they occupy
geometrically distinct regions, and/or as consequence of the dust


Article number, page 15 of 27

_A&A proofs:_ manuscript no. main


**Table 2.** Kinematic properties and dynamical mass estimates for sources in SPT0311-58


ID z ∆v σ R _e_ M dyn Dw
km s [−][1] km s [−][1] kpc 10 [9] M ⊙ kpc
C1 6.92655 ± 0.00019 932. ± 7. 99. ± 8. 0.64 ± 0.19 7.4 [+] − [10] 2.7 [.] 9.4 ± 0.3
C2 6.92419 ± 0.00010 843. ± 4. 57. ± 5. 0.69 ± 0.21 2.6 [+] − [3] 1 [.] . [7] 0 10.7 ± 0.3
C3 6.90638 ± 0.00035 166. ± 13. 106. ± 15. 0.75 ± 0.37 10. [+] − [20] 3.7 [.] 3.9 ± 0.5
L2L1 6.892566.89941 ± ± 0.00025 0.00005 -358.-98. ± ± 2. 9. 64.66. ± ± 12. 2. 0.510.73 ± ± 0.26 0.22 2.53.8 − [+][+] −0 [5][4] 1. [.][.] .9 [8][7] 4 7.65.1 ± ± 0.5 0.3
L3 6.88632 ± 0.00011 -595. ± 4. 36. ± 7. 0.68 ± 0.20 1.0 [+] − [2] 0 [.] . [0] 4 15.0 ± 0.5
L4 6.92425 ± 0.00056 845. ± 21. 99. ± 24. 0.70 ± 0.35 7.9 [+] − [20] 2.9 [.] 8.2 ± 0.5
L5 6.90940 ± 0.00004 281. ± 2. 36. ± 3. ... ... 14.2 ± 0.5
L6 6.91830 ± 0.00018 619. ± 7. 45. ± 10. 0.58 ± 0.17 1.4 − [+] 0 [2] . [.] 5 [8] 7.3 ± 0.5
L7 [1] 6.92644 ± 0.00054 928. ± 20. 93. ± 15. 0.53 ± 0.31 5.3 [+] − [1] 1 [.] . [8] 6 11.0 ± 0.5
E 6.91956 ± 0.00008 666. ± 3. 155. ± 3. 2.12 ± 0.63 59. [+] − [70] 21 [.] . 10.7 ± 0.3


**Notes.** Column 1: Source identification. Column 2: Redshift from the R2700 [OIII]-Hβ lines. Column 3: Relative velocity with respect to z=6.902,
as inferred for the W galaxy from the ALMA [CII] line (see Sect. 5.3). Column 4: Integrated velocity dispersion derived from the [OIII]-Hβ lines in
the R2700 integrated spectra, after deconvolving the instrumental profile (Appendix A). Column 5: Effective radius estimated as the largest sigma
of a 2D Gaussian fit to source emission, after deconvolving quadratically the PSF profile. To derive the properties of the PSF we used the datacube
of the standard star (see Sect. 2.5). For sources with significant continuum emission (C1, C2, C3) the sizes were inferred from a panchromatic
image generated from the R100 cube in the 1 to 5 µm spectral range. For the other sources, which have undetected (or very faint) continuum,
the [OIII] image was preferred. For the E galaxy the combination of continuum plus [OIII] was used. The Gaussian fits provided unrealistically
small errors. Instead, uncertainties are estimated to be 30%, except for some particularly problematic cases for which 50% was adopted instead,
specifically for C3 (edge of the FoV), L2 (faint), and L4 (badly defined). For L5, which is very close to the edge of the FoV, R _e_ could not be
estimated. Column 6: Dynamical mass of the source adopting the calibration by Cappellari et al. (2006) (see Sect. 5.1). Column 7: Distance to
spaxel (74,45), which is estimated to be at the centre of gravity of the system. [1] For L7, the kinematic properties were obtained after the 2D
kinematic decomposition of this source and the main component of the E galaxy (Sect. 3.3.3).



attenuation. ALMA traces regions over a large range of dust attenuation, while NIRSpec probes the ionised gas that is located
in less extincted (likely more external) regions. Hence, relative
motions between regions with different dust attenuation could
explain the observed velocity offsets.


As for the velocity dispersion, the cold and warm gas show
a significant difference, particularly towards the south and east
(see bottom-right panel of Fig. 11). Interestingly recent simulations of 4 < z < 9 galaxies by Kohandel et al. (2024) show
that the gas velocity dispersion estimates strongly depend on
the tracer used. According to this study, while [CII] traces the
gaseous disc, Hα also includes the contribution from extraplanar
ionised gas beyond the disc. This effect is more significant for
massive galaxies (i.e. _M_ ⋆ - 10 [9] M ⊙ ), for which σ (Hα) - 2 ×
σ ([CII]). These predictions are in general agreement with our
observations in the E galaxy, though we find significant spatial
variations. In the north and in the central regions the velocity dispersion obtained from [CII] and [OIII] are similar, while to the
south and east the σ ([OIII]) values are larger by factors of up to
∼ 2-3. [5]


A similarly relevant difference between the velocity dispersion of warm ionised gas and its cold phase counterpart has been
recently reported by Parlanti et al. (2024) in a z= 4.8 DSFG
observed with JWST. However, in that case the difference was
found in the central regions of the galaxy, and explained by the
feedback effects of an AGN, a scenario that can hardly be considered for interpreting the observed behaviour in SPT0311–58. In
Section 6, we discuss further the kinematics in E in connection
with other ISM properties.


5
We note that we do not find significant differences between σ (Hα)
and σ ([OIII]) in the spectra of SPT0311–58.


Article number, page 16 of 27



_5.3._ _W galaxy_


As commented above, the main body of the W galaxy is not detected in a spaxel-by-spaxel basis, and therefore we cannot infer
spatially resolved kinematic information with NIRSpec for this
galaxy. However, the R2700 integrated spectrum allow us to infer the redshift from the optical emission lines. As the [OIII]
lines are faint in this galaxy, we use the Hα-[NII] complex and
the Hβ line, and obtain z= 6.907 ± 0.002. We note that the uncertainty in this case is relatively large because the spectrum is
noisy (Fig. A.2).
We also derived the redshift from the integrated spectrum of
the [CII] line obtained using the same aperture as above. The

[CII] profile in this spectrum departs significantly from a Gaussian. So, rather than derive the redshift fitting the line, we obtain
the flux-weighted averaged wavelegth, and obtained z= 6.902 ±
0.002. This agrees within errors with the Strandet et al. 2017 determination (z=6.900 ± 0.002), who used several CO and [CII]
lines and a beam of 2-3 [′′] . We note that because the W galaxy is
well detected and resolved with ALMA, and it is also close to
the zone of multiple images, its redshift determination may be
affected by the lens, which introduces an additional uncertainty.
The differences in the redshifts derived from the optical and
the far infrared lines suggest an average shift of ∼ +200-300 km
s [−][1] between the warm and the cold gas phases. Álvarez-Márquez
et al. (2023) already reported an offset of Paα with respect to the

[CII] and [OIII] far-IR lines, though in this case significantly
larger in amplitude (i.e. +700 km s [−][1] ). For source C3, at the
south of W, the average relative velocity (cold-warm) is ∼ +80
km s [−][1] . As discussed for the E galaxy, this velocity difference
may be explained by the relative motions between the less attenuated regions traced with the optical lines, and the dustier zones
probed at the far infrared. The larger attenuation in W (see Sect.
4.2) could also qualitatively explain why we find a significantly
larger velocity offset in this galaxy than in E.

Santiago Arribas et al.: The core of a protocluster at z=6.9



3.5


3.0


2.5





2.0


1.5


1.0


0.5


0.0

0.00 0.05 0.10 0.15 0.20 0.25 0.30 0.35
R/R 200


**Fig. 13.** Projected phase space for the galaxies in SPT0311–58. The xaxis is the projected distance from the cluster centre in units of R 200 .
The y-axis shows the absolute value of the relative velocity along the
line of sight of each galaxy with respect to the global recessional velocity, normalised by the velocity dispersion of the cluster. The red dots
correspond to a global cluster redshift of z _sys_ =6.902 as inferred for the
W galaxy from the [CII] line, and the green dots are for an _ad-hoc_ z _sys_ =
6.912. The blue line represents the escape velocity normalised by the
velocity dispersion of the cluster for a Navarro, Frenk, and White dark
matter halo (Navarro et al. 1996) of M 200 = 5 × 10 [12] M ⊙, with the blue
shadow defining the region for masses between 2 and 8 × 10 [12] M ⊙ . The
point for the W galaxy at (0,0) has been slightly shifted to make it more
visible.


**6.** **Discussion**


_6.1._ _SPT0311–58: A protocluster core in a massive_
_dark-matter halo_


The possibility that SPT0311–58 forms part of a protocluster
was proposed by Wang et al. (2021), who found a significant
overdensity of bright submm sources in the field surrounding its
two main galaxies (r ≲ 1.3 Mpc). However, the lack of spectroscopic redshifts prevented Wang and collaborators to confirm
this scenario, and classified SPT0311–58 as a protocluster candidate. As has been detailed in Section 3, the present NIRSpec
data have revealed ten new spectroscopically confirmed z ∼ 6.9
sources in the IFU FoV (i.e. 17×17 kpc [2] ) in addition to the already known E and W galaxies, which strongly supports the idea
that SPT0311-58 is at the core of one of the most distant protoclusters known. Indeed, the number density of sources (ϕ ∼
10 [4] Mpc [−][3] ) is orders of magnitude above the expectation for the
field (ϕ _f_ ∼ 5 Mpc [−][3], for _M_ ⋆ - 10 [7] M ⊙ ), according to the observed galaxy stellar mass functions (e.g. Conselice et al. 2016).
In addition, we find that the sources in SPT0311–58 exhibit a
relatively large spread in radial velocity (∆v ∼ 1500 km s [−][1], Table 2), akin to other high-z protoclusters (z - 4, e.g. Chanchaiworawit et al. 2019, Hill et al. 2020, Calvi et al. 2021, Endsley &
Stark 2022, Morishita et al. 2023, Hashimoto et al. 2023, Scholtz
et al. 2023). This suggests that the mass of the halo must be very
large. In the following, we estimate the main properties of the
halo, and discuss the dynamical status of the core of this protocluster.


6.1.1. Main properties of the dark-matter halo


We estimate the mass of the halo from the stellar mass, which we
obtain by combining our results for the E galaxy and the newly



discovered sources with the one for the W galaxy determined
by Álvarez-Márquez et al. (2023) (see Sect. 4.1). We adopt the
mass determinations for E and W that include MIRI photometry. For the newly discovered sources, which have not MIRI
detections, we conservatively apply the corrective factor found
by Papovich et al. (2023) and Wang et al. (2024). The resulting
total stellar mass for the system is (1.1 ± 0.3) × 10 [11] M ⊙ . The
_M_ ⋆ / _M_ _h_ ratio is not well constrained for the redshift and stellar mass of SPT0311–58, but empirical modeling (UniverseMachine, Behroozi et al. 2019, 2020) and hidrodynamical simulations (MillenniumTNG, Kannan et al. 2023) suggest values of ∼
0.015– 0.03 [6], which leads to _M_ _h_ ∼ (5±3) × 10 [12] M ⊙ .
This result agrees well with the findings of Marrone et al.
(2018), who estimate _M_ _h_ in SPT0311–58 from its gas content
(Strandet et al. 2017). Specifically, they found that _M_ _h_ could vary
from a conservative lower limit of 1.7 × 10 [12] M ⊙ to 7.4 × 10 [12]
M ⊙, depending on the approach adopted to determine the mass of
the gas. However, we note that recently Jarugula et al. (2021), using nonlocal thermodynamic equilibrium radiative transfer models, have found that the mass of gas in SPT0311–58 is larger
than previously estimated. This result suggests that previous gasbased M _h_ determinations should be corrected by factors of 1.5-2.
Having an estimate for the halo mass, we can now derive the
expected size, R 200 [7], for a virialised dark matter (DM) halo at
z=6.9. By definition (e.g. Navarro et al. 1996):



ρ _c_ = [3] _[H]_ [2] [(] _[z]_ [)], (3)

8π _G_


with H(z) and G being the Hubble parameter and the gravitational constant, respectively. From these equations, we derive a
size of R 200 = 67 [+] − [9] 15 [kpc for a halo mass of (5][±][3)][ ×][ 10] [12] [M] [⊙] [.]
The centre of mass of this protocluster should be at the W
galaxy. This is based on previous works (Marrone et al. 2018;
Álvarez-Márquez et al. 2023) that have shown that the baryonic
mass of this galaxy is about one order magnitude larger than its
companion, the E galaxy. The newly discovered galaxies have
dynamical masses significantly lower than E (Sect. 5), so they
should not affect significantly the determination of the centre of
gravity of the system (CoG _sys_ ). We also adopt the redshift of the
W galaxy as the mean redshift for the system. As discussed in
Sect. 5.3, the redshift for W is subject to relatively large uncertainties compared with other sources, with significant differences
among the values inferred from the optical emission lines (NIRSpec), Paα (MIRI), and the molecular lines (ALMA), being also
possibly affected by the effects of the lens. We adopt the determination based on the [CII] line (i.e. z=6.902 ± 0.002), because
it is not affected by attenuation, and traces a significantly larger
amount of mass (see Sect. 5.3). Therefore, taking the W galaxy
as the centre of the protocluster, our NIRSpec observations probe
projected cluster-centric distances of up to 15 kpc (see Table 2),
which correspond to about 0.2 × R 200 .


6 Mock galaxy catalogues generated using the so-called UCHUU-UM
approach (Ishiyama et al. 2021; Prada et al. 2023) lead to a _M_ ⋆ / _M_ _h_ ratio
range in agreement with the one adopted here (E. Pérez, F. Prada, priv.
comm.).
7 R 200 is defined as the radius within which the mean enclosed mass
density is 200 times the critical density of the Universe at the corresponding redshift.


Article number, page 17 of 27



_M_ 200 ≡ 3 [4] [π] _[R]_ 200 [3] [200][ρ] _[c]_ [,] (2)


where M 200 ≡ M _h_, and ρ _c_ is the critical density that varies as

_A&A proofs:_ manuscript no. main



6.1.2. Probing the dynamical state of the protocluster core


Given that we are observing such an inner region of a protocluster, one might inquire whether it has already undergone (partial)
virialisation. In an attempt to answer this question, we analysed
whether the radial velocities of the 12 galaxies may be drawn
from a normal distribution, as expected for a system in equilibrium. With this aim, we performed a Kolmogorov-Smirnov
(K-S) test that led to a p-value of 0.04, and therefore we conclude that the observed region is not virialised yet. However,
we point out that the result of the K-S test is very dependent

                                      on the origin of the relative velocities. If we allow a global off
set to the radial velocities of 380 km s [−][1], the p-value reaches
0.75, suggesting a normal distribution. This change would imply
that the W galaxy is not at the centre of the protocluster, or that
its redshift is larger by ∆z ∼ 0.01, i.e. z = 6.912. We note that
this redshift falls between the one inferred from the optical lines
(z=6.907) and from Paα (z = 6.918) (Sect. 5.3). Still, for the reasons mentioned above, we argue that most likely the CoG _sys_ is at
W and z _sys_ = 6.902, and therefore the system does not seem to be
at equilibrium. Nevertheless, in the remainder of the section we
also evaluate how the results are affected if an ad hoc z = 6.912
is used as reference.

Using the present kinematic information, we can also assess
if the system is at equilibrium by comparing the velocity dispersion observed in SPT0311–58 with the one expected for its
mass in a virialised cluster. We derive the velocity dispersion
in our data by bootstrap, and obtain a mean estimate of σ _sys_
= 479 km s [−][1], and a range from 406 to 551 km s [−][1] with a 68
percent confidence [8] . According to the numerical simulations of
virialised clusters by Evrard et al. (2008), the predicted velocity dispersion at equilibrium for a cluster with a mass of (5 ±
3) × 10 [12] M ⊙ is 372 [+] − [65] 98 [km s] [−][1] [. Since we measure a larger face]
value of the velocity dispersion, this comparison suggests that
the core in SPT0311–58 is not virialised yet. However, taking
into account the associated uncertainties, the data are also compatible with being (partially) virialised. Alternatively, the Evrard
et al. (2008) relation and the observed velocity dispersion can be
used to predict the mass for a virialised protocluster. The derived
value (1.05 [+] − [0] 0 [.] . [55] 41 [×][10] [13] [M] [⊙] [) is larger than our halo mass estimate,]
which again suggests that the system has not reached equilibrium. However, as mentioned above, the uncertainties are large
and this conclusion lacks robustness.

In order to further analyse the dynamical status of the observed region, in Fig. 13 we locate the galaxies in the projected
phase space (PPS) diagram (e.g. Mahajan et al. 2011; Jaffé et al.
2015). The x-axis of the plot is the projected distance from the
cluster centre normalised to R 200, while the y-axis indicates the
(absolute) velocity of each galaxy with respect to the global recessional velocity (v) normalised by the velocity dispersion of
the cluster, that is, |∆v|/σ _sys_ . In the plot we also include with a
blue line the (projected) escape velocity from a Navarro Frenk
and White (NFW, Navarro et al. 1996) dark-matter halo of M 200
= 5 × 10 [12] M ⊙, normalised by σ _sys_ .The blue shadow region
refers to escape velocities for halo masses from 2 to 8 × 10 [12] M ⊙ .
For our primary reference (i.e. W at the CoG _sys_, z _sys_ =6.902, red
dots), most of the galaxies are below the escape velocity limit,
and therefore they are bound gravitationally to the halo. However, taking into account the uncertainties and the fact that in
the figure we present projected velocities corrected with an average factor, a few galaxies could also be consistent with being


8 The bootstrap estimate is preferred over the standard deviation (507
km s [−][1] ), as it is more robust for small samples (Beers et al. 1990).


Article number, page 18 of 27



unbound. When the _ad-hoc_ redshift (i.e. _z_ = 6.912, see above)
is adopted (i.e. green points), one galaxy (L3) appears unbound,
though the rest are located deeper into the potential well, showing on average lower |∆v|/σ _sys_ values.
In summary, our data suggest that the observed region in
SPT0311–58 is likely not totally virialised, though it may be not
far from reaching equilibrium. While a few galaxies could be flybys, the majority appear to be gravitationally bound to the halo,
for which we estimate a DM mass of ∼ 5 × 10 [12] M ⊙ . These results reinforce the findings by Marrone et al. (2018) who showed
that the halo mass for SPT0311–58 is very large according the
theoretical expectations at z∼ 6.90.


6.1.3. The SPT0311–58 protocluster in context: comparison
with cosmological simulations and other observations


The previous findings suggesting an extreme halo mass in
SPT0311–58 are strengthened further when comparing it with
the most massive protoclusters in the IllustrisTNG (e.g. Springel
et al. 2018) and FLAMINGO (Schaye et al. 2023; Kugel et al.
2023) cosmological simulations, as well as with previously observed protoclusters.
Figure 14 presents the position of SPT0311–58 in the _M_ _halo_  z plane together with the predictions from IllustrisTNG obtained
by Lim et al. (2021) by selecting the 25 most massive clusters
in the _z_ = 0 snapshot, and tracking them using the merger tree
to find their progenitors at higher redshifts. For FLAMINGO,
on the other hand, the figure includes the median and the full
range among the 100 highest-SFR haloes identified in each snapshot of its 2.8 Gpc and 1 Gpc box runs taken from Lim et al.
(2024). The figure clearly indicates that only the most massive
protoclusters in FLAMINGO simulations are able to reproduce
the SPT0311–58 position. Part of the reason why the protoclusters from IllustrisTNG have significantly lower mass is because of the smaller box size of 300 Mpc of these simulations,
which makes difficult to capture a rare object like SPT0311–
58. According to these simulations, protoclusters with masses
of ≳ 10 [12] M ⊙ at _z_ ≃ 7 could transform into 10 [15] M ⊙ systems at
_z_ = 0, though this may not be necessarily the case (e.g. Remus
et al. 2023). These results suggest that SPT0311–58, for which
independent approaches find a dark matter halo mass higher than
10 [12] M ⊙, could be the progenitor of a Coma-like cluster.
Fig. 14 also includes a set of observationally identified protoclusters at _z_ ≳ 2 from the literature, which consists of GOODS-N _z_ = 1.99 protocluster (Blain et al. 2004;
Chapman et al. 2009), MRC1138−262 (Dannerbauer et al.
2014), SSA22 (Umehata et al. 2015), AzTEC-3 (Capak et al.
2011), SPT2349−56 (Miller et al. 2018; Hill et al. 2020),
ZFIRE (Hung et al. 2016), PHz G237.01+42.50 (Polletta et al.
2021), CC2.2 (Darvish et al. 2020), PCL1002 (Casey et al.
2015), CLJ1001 (Wang et al. 2018), ), a LAE overdensity at
z=6.5 (Chanchaiworawit et al. 2019), a protocluster in COSMOS (Brinch et al. 2024), MAGAZ3NE J095924+022537 and
MAGAZ3NE J100028+023349 (both from McConachie et al.
2022), HDF850.1 (Calvi et al. 2021), z57OD and z66OD
(Harikane et al. 2019), an overdensity at _z_ = 7.66 (Laporte et al.
2022), A2744-z7p9OD (Morishita et al. 2023), the seventeen
protocluster candidates identified with JWST by Helton et al.
(2024, 2023), and GNz11 (Scholtz et al. 2023). This illustrates
the distinct mass of SPT0311−58 among the protoclusters discovered at high redshifts, being currently the most massive
known at the EoR.
The present study, although admittedly subject to large uncertainties, represents one of the first attempts to characterise

#### 10 [15] 10 [14] 10 [13] 10 [12] 10 [11] 10 [10]



Santiago Arribas et al.: The core of a protocluster at z=6.9


|Col1|Col2|
|---|---|
|is work<br>AMINGO (2.8Gpc)<br>AMINGO (1Gpc)<br>G (300Mpc)<br>er obs|EoR|
|2<br>4<br>6<br>8<br>Redshift|2<br>4<br>6<br>8<br>Redshift|



**Fig. 14.** Halo mass of SPT0311-58 together with a compilation of z > 2 protoclusters as a function of redshift (see text). The orange lines correspond
to the halo accretion history of the 25 most massive clusters at z=0 in the IllustrisTNG simulation discussed by Lim et al. (2021). The FLAMINGO
simulations are taken from Lim et al. (2024), and represent the median and the full range among the 100 highest-SFR haloes identified in each
snapshot of its 2.8 Gpc and 1 Gpc box runs. The figure shows the extreme mass of SPT0311-58, being the most massive protocluster discovered so
far at EoR. It also shows the difficulty of TNG simulations to predict a rare system like SPT0311–58, as a consequence of their limited simulated
volume (i.e. box size of 300 Mpc). The position of SPT0311–58 can be reproduced by FLAMINGO simulations with larger box sizes (see text).



spectroscopically a protocluster at the epoch of reionisation, and
it shows the power of JWST for such studies. Further observations expanding the observed area will enable us to better characterise the field, and constrain the dynamical stage of this extreme
system.


_6.2._ _The turbulent early phases of galaxy assembly:_
_accretion, mergers, and gravitational interactions_


In this section, we discuss the ongoing physical processes and
the current evolutionary stage of the E galaxy, based on the detailed spatially resolved properties provided by the NIRSpec IFU
presented in previous sections.


6.2.1. Metallicity gradient and evidence of gas accretion in
the E galaxy


As shown in Fig. 10, the E galaxy shows a significant metallicity
gradient of ∼ 0.7 dex, with the lowest values (i.e. 12-log(O/H)
∼ 7.9) found in the northwest region. This is close to the zone
where the Hα and [CII] emission extends towards the position of
the C1 galaxy (see grey isocontours in Fig.10, and Fig. 2(c,f)),
indicating the presence of significant amounts of warm and cold
gas. In this region, the stellar component, as traced by the continuum maps (panels a and d in Fig. 2), is not prominent. This



indicates that the outskirts of E in the northwest direction should
be dominated by gas. Moreover, the velocity field in the northwest part of E shows significantly twisted isolines that cannot be
explained as part of a global regular rotation (Sec. 5). All these
features can be naturally explained as the result of the gas accretion of low-metallicity gas from the CGM into the main E

structure.

In lower redshift galaxies (i.e. z∼ 3) metallicity gradients
have also been found, and explained by the accretion of primordial gas (Cresci et al. 2010) as predicted by theoretical models
(Dekel et al. 2009). The gas accretion in SPT0311–58 could be
triggered by the interaction of E with the C1 galaxy, which is
only ∼ 100 km s [−][1] and 2 kpc apart in projection. According to
the velocity field of E and the radial velocity of C1, this possible
encounter would result in a prograde interaction, which is an efficient process at driving gas inflows (Barnes & Hernquist 1992,
Cox 2009, Lambas et al. 2012). Alternatively, E and C1 may
not be interacting (i.e. simply appear close in projection), and
the accretion of low-metallicity gas into E could be the result of
smooth streams of gas from the IGM (Sánchez Almeida et al.
2014). This possibility is consistent with cosmological simulations that predict that streams of inflowing gas from the cosmic
web are the dominant mechanism for the formation of galaxies
in massive halos (e.g. Dekel et al. 2009, Ceverino et al. 2016).
As we discuss in the previous section, SPT0311–58 resides in


Article number, page 19 of 27

_A&A proofs:_ manuscript no. main



a massive halo and therefore the presence of streams feeding
its central regions with gas from the IGM is naturally expected
when it is actively building its stellar component at rates > 100s
M ⊙ yr [−][1] .
The observed metallicity gradient could, in principle, also be
explained by the merging of two (or more) galaxies with a significant difference in metallicity. The continuum maps (Fig. 1,
Fig. 2(a)) show two distinct structures in the E galaxy, i.e. ES
and EN, which could be the result of two separate precoalesce
merging galaxies. The MIRI image (Fig. 2d) also shows a structure to the north-west that is not seen in NIRSpec likely due
to obscuration. However, the kinematic properties in the main
structure of E do not show evidence for two kinematically distinct objects, such as peaks in the velocity dispersion map, or
rotation associated with their nuclear regions. The [OIII] (Fig.
7 upper panels) and [CII] (Fig. 11) velocity fields also show a
smooth behaviour at large scales. The most significant distortion
in the velocity map is found at the northwest edge of the main
structure (i.e. not in an inner region), but the velocity dispersion
there is relatively low, which does not suggest gas motions associated with strong interactions. Therefore, while we cannot rule
out completely the merging scenario, the ionised gas, metallicity, and kinematic maps presented here favour the gas accretion
scenario in the E galaxy.
A third alternative to explain metallicity gradients is the presence of outflows (e.g. Rodríguez Del Pino et al. 2024). However,
we do not see any clear evidence for outflows in our spectra.
Moreover, if an outflow were present (or had been active in recent times), its most likely orientation would be along the minor
axis, which is perpendicular to the direction of the metallicity
gradient. Therefore, the outflow scenario can hardly explain the
case of SPT0311–58.


6.2.2. Kinematic evidence for an unsettled disc structure at

redshift ∼ 7


We now discuss the properties of L7, and the possibility that it
will merge with E. The kinematic maps for these two galaxies
are shown in Fig. 7. One clear feature that can be inferred from
the figure is that L7 is reshifted by ∼ 250 km s [−][1] with respect to
E. This fact has two implications. First, this significant kinematic
decoupling rules out that L7 has been formed by disc fragmentation in contrast to the clumps identified by Spilker et al. (2022)
at submm wavelengths. Second, the relative velocity between L7
and E allows us to constrain the geometry. In fact, taking into
account the dusty nature of E, L7 has necessarily to be located
between us and the main structure of E, as otherwise it could not
be observed through the dusty disc. Therefore its receding velocity suggests that it is falling into E. Although we cannot rule
out that L7 has a large velocity component perpendicular to the
line of sight, its already large projected velocity with respect to
W (i.e. +928 km s [−][1] ) makes this possibility unlikely (i.e. otherwise, its actual velocity with respect to W would be extremely
high). So, rather than a fortuitous alignment of a fly-by source,
the data suggest that we are witnessing the premerger phase between L7-E. The mass ratio of both galaxies is ≲ 1:8, and thus it
should be classified as a minor merger event, the likes of which
are expected to occur frequently according to theoretical models
(e.g. Ceverino et al. 2016).
In Sect. 5 we show that, in addition to the irregular velocity field, the velocity dispersion map of the E galaxy exhibits a
nonaxisymmetric structure with variations at subkpc scales and
a global trend along the northwest - southeast direction (Fig. 7).
The velocity dispersion is high everywhere, with values ranging


Article number, page 20 of 27



from ∼ 75 up to 150 km s [−][1], indicating high turbulence. The velocity dispersion map does not show the expected increase due
to beam-smeared velocity gradients in the central regions, as observed in discs formed at later cosmic times (e.g. Übler et al.
2019). The sparse isovelocity lines shown in Fig. 7 clearly indicate that the situation in this galaxy is rather different.
Then, the present 2D kinematic maps (i.e. both the velocity field and the velocity dispersion map) describe an ionised
gas structure that departs from what is expected for a settled rotating disc. The kinematics of the cold gas component obtained
with high-resolution [CII]λ158 µm ALMA observations (Spilker
et al. 2022), also reveal high velocity dispersions associated with
the clumps, indicating large turbulence. The mean radial velocities of the clumps also follow a global velocity gradient, and thus
they could be the result of disc fragmentation. Hence, the main
kinematic properties of the E galaxy, as inferred from the ionised
and neutral gas phases, differ significantly from the settled and
regular behaviour observed in some DSFGs at lower redshifts
(i.e. z ∼ 4-5, Fraternali et al. 2021; Rizzo et al. 2021; Lelli et al.
2021; Parlanti et al. 2024; Übler et al. 2024). In fact, the E galaxy
is actively assembling its stellar component undergoing a highly
turbulent phase marked by the presence of gravitational instabilities, gas accretion, and merger events. All of these processes
also account for the irregularities and subkiloparsec variations
in the interstellar medium (ISM) conditions, as evidenced by the
ionisation and metallicity maps.
Still, despite these tumultuous conditions, the velocity field
in E shows a clear large-scale velocity gradient of about 200 km
s [−][1] . If interpreted as global rotation, the E galaxy will have several complete revolutions (∼ 4 at r = 3 kpc) during the next ∼ 0.5
Gyr (i.e. by z ∼ 4.5). Together with other mixing mechanisms,
this will contribute to redistributing the gas and erase the physical and kinematic inhomogeneities produced by present and recent events. Therefore, it is conceivable that this process will
make the properties of the E galaxy in SPT0311–58 to evolve
into those of more settled DSFGs currently observed at z ∼ 4-5
(e.g. Rizzo et al. 2021, Parlanti et al. 2024, Übler et al. 2024),
unless additional accretion and/or mergers with nearby objects
continue to generate inhomogeneities in the ISM and disturb its
kinematics.


**7.** **Summary and conclusions**


We present JWST/NIRSpec IFU low-resolution (R=100) and
high-resolution (R=2700) spectroscopy of SPT0311-58 at z ∼
6.9, the most massive and distant dusty star-forming system
known, and a protocluster candidate. The main conclusions of
this paper can be summarised as follows:
(i) Our observations reveal ten new sources at a redshift of ∼
6.9 (and three additional foreground galaxies at z ∼ 1-3) in the
field around the two main, previously identified massive galaxies
of the system, referred to as the E and W galaxies. The newly discovered z ∼ 6.9 galaxies are characterised by dynamical masses
of ∼ 10 [9] -10 [10] M ⊙, and a wide range in relative velocity (∆v ≈
1500 km s [−][1] ). The high density of sources (ϕ ∼ 10 [4] Mpc [−][3] ) and
their spread in radial velocity confirm that SPT0311–58 is at the
core of an extremely massive protocluster, for which we estimate
a mass of ∼ (5 ± 3) × 10 [12] M ⊙ from its stellar content. SPT0311–
58 is therefore the most massive protocluster discovered so far
at the EoR. A basic analysis indicates that the innermost regions
of the protocluster (r < 0.2 R 200 ) have likely not yet reached
virial equilibrium. We also located the galaxies in the projected
phase space (PPS) diagram, and find that most are gravitationally bound to the halo. According to cosmological simulations

Santiago Arribas et al.: The core of a protocluster at z=6.9



for a protocluster with its mass, it could evolve into a Coma-like
system at z=0, though this may not be necessarily the case.
(ii) The ISM conditions of the sources in SPT0311–58 are
very diverse. While some of these z ∼ 6.9 objects have similar ionisation properties to those of the field galaxies at these
redshifts recently observed with JWST, others have conditions
mostly found in more evolved objects at lower redshift. In the
N2-BPT diagnostic diagram, most sources occupy the region of
composite SF/AGN ionisation at low-z, but we do not find clear
evidence for AGN. None are in the local LI(N)ER region, but
shocks are likely to be present in a turbulent ISM, which is expected to experience disc fragmentation, interactions, and minor mergers. Similarly, the metallicity varies by more than 0.8
dex across the galaxies in the FoV. The regions with the highest
metallicity are associated with the two main massive galaxies,
with nearly solar values of ∼ 8.5-8.6 in the 12+log(O/H) scale.
Three external sources show the lowest metallicities with values

of about 7.9-8.1.

(iii) Using Hα, we characterised the unobscured star formation (SFR(Hα)) in the system, and identified three distinct SF
regimes. First, the most massive W galaxy (M _bar_ ∼ 3 × 10 [11] M ⊙ )
has a very modest SFR(Hα) (∼ 8 M ⊙ yr [−][1] ) compared with the
enormous obscured SF detected with ALMA (i.e. SFR(FIR) ∼
3000 M ⊙ yr [−][1] ). Most of the SF in this galaxy is totally blocked
at optical and near-IR wavelengths, and cannot be recovered with
the dust-attenuation correction. Second, the less massive, though
still very massive (M _bar_ ∼ 4 × 10 [10] M ⊙ ) E galaxy, has significant SFR(Hα) ∼ 80 M ⊙ yr [−][1], with a dominant SFR (FIR) of ∼
500 M ⊙ yr [−][1] . The dust-corrected SFR (Hα) recovers most of the
total SFR of the system. Finally, the newly discovered sources
have SFR(Hα) ∼ 1-6 M ⊙ yr [−][1], and no obscured SF is detected
with ALMA. Their contribution to the total SF of the system is

∼
minor ( few percent).
(iv) The 2D physical, chemical, and kinematic information
of the E galaxy provided by the present data allows us to characterise the current early phases of its stellar mass assembly. The
velocity field and the velocity dispersion maps show asymmetric
and irregular patterns indicating clear departures from rotation
and high turbulence (intrinsic velocity dispersion, σ 0, ∼ 115 km
s [−][1] ). We find large-scale motions between the ionised gas component probed with NIRSpec and the cold gas phase counterpart
traced by ALMA. This galaxy shows a clear metallicity gradient
of ∼ 0.1 dex/kpc that is naturally explained by accretion of pristine gas from the IGM. We also identify a possible (precollision)
minor merger event. All these results suggest a scenario in which
the E galaxy is undergoing a tumultuous phase while actively assembling its stellar component. However, the large global velocity gradient observed suggests that it could evolve into a regular
settled rotating DSFG, similar to those observed at later cosmic
times (i.e. z ∼ 4-5).
The present study highlights the role of SPT0311–58 as an
ideal astrophysical laboratory for studying galaxy evolution in
a very massive dark-matter halo at the epoch of reionisation. It
also demonstrates the enormous potential of the JWST/NIRSpec
IFU for detailed spatially resolved analyses at these very early
cosmic times.


_Acknowledgements._ We thank an anonymous referee for constructive comments. We also thank Daniel Ceverino, Evencio Mediavilla, Charles Proffitt,
Francisco Prada, Enrique Pérez, Irene Shivaei, Rhea-Silvia Remus, Jorge
Jiménez-Vicente, and Jose Alberto Rubiño for uselful discussions, and valuable
input. This work is based on observations made with the NASA/ESA/CSA
_James_ _Webb_ Space Telescope. The data were obtained from the Mikulski
Archive for Space Telescopes at the Space Telescope Science Institute, which
is operated by the Association of Universities for Research in Astronomy,
Inc., under NASA contract NAS 5-03127 for JWST. SA, MP, and BRP



acknowledge support from the research project PID2021-127718NB-I00 of
the Spanish Ministry of Science and Innovation/State Agency of Research
(MICIN/AEI//10.13039/501100011033). IL acknowledges support from the
Spanish Ministry of Science and Innovation (MCIN) by means of the Recovery
and Resilience Facility, and the Agencia Estatal de Investigación (AEI) under
the projects with references BDC20221289 and PID2019-105423GA-I00.
PGP-G acknowledges support from grants PGC2018-093499-B-I00 and
PID2022-139567NB-I00 funded by Spanish Ministerio de Ciencia e Innovación
MCIN/AEI/10.13039/501100011033, FEDER, UE. RM, FSE, JS, JW, and SL
acknowledge support by the Science and Technology Facilities Council (STFC),
by the ERC through Advanced Grant 695671 “QUENCH”, and by the UKRI
Frontier Research grant RISEandFALL. RM also acknowledges funding from a
research professorship from the Royal Society. GC acknowledges the support
of the INAF Large Grant 2022 “The metal circle: a new sharp view of the
baryon cycle up to Cosmic Dawn with the latest generation IFU facilities”.
HÜ gratefully acknowledges support by the Isaac Newton Trust and by the
Kavli Foundation through a Newton-Kavli Junior Fellowship. AJB, GCJ, and
JCh acknowledge funding from the “FirstGalaxies” Advanced Grant from the
European Research Council (ERC) under the European Union’s Horizon 2020
research and innovation program (Grant agreement No. 789056). SC, EP, and
GV acknowledge support from the European Union (ERC, WINGS,101040227).
The Cosmic Dawn Center (DAWN) is funded by the Danish National Research
Foundation under grant DNRF140.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2016.1.01293.S and ADS/JAO.ALMA#2017.1.01423.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic of Chile. The
Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This
research has made use of "Aladin sky atlas" developed at CDS, Strasbourg
Observatory, France (Bonnarel et al. 2000) This research has made use of
NASA’s Astrophysics Data System, QFitsView, and SAOImageDS9, developed
by Smithsonian Astrophysical Observatory. This research made use of Astropy,
a community-developed core Python package for Astronomy (The Astropy
Collaboration et al. 2013), `Matplotlib` (Hunter 2007), `NumPy` (Van Der Walt
et al. 2011). This research has made use of "Aladin sky atlas" developed at CDS,
Strasbourg Observatory, France (Bonnarel et al. 2000).


**References**


Abazajian, K. N., Adelman-McCarthy, J. K., Agüeros, M. A., et al. 2009, ApJS,
182, 543
Akins, H. B., Casey, C. M., Allen, N., et al. 2023, ApJ, 956, 61
Alberts, S. & Noble, A. 2022, Universe, 8, 554
Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671,
A105
Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5
Barnes, J. E. & Hernquist, L. 1992, ARA&A, 30, 705
Baron, D., Netzer, H., French, K. D., et al. 2023, MNRAS, 524, 2741
Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, MNRAS, 522, 449
Beers, T. C., Flynn, K., & Gebhardt, K. 1990, AJ, 100, 32
Behroozi, P., Conroy, C., Wechsler, R. H., et al. 2020, MNRAS, 499, 5702
Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, MNRAS, 488,
3143
Bezanson, R., van der Wel, A., Pacifici, C., et al. 2018, ApJ, 858, 60
Bik, A., Álvarez-Márquez, J., Colina, L., et al. 2023, arXiv e-prints,
arXiv:2312.03074 (accepted for publication in A&A)
Blain, A. W., Chapman, S. C., Smail, I., & Ivison, R. 2004, ApJ, 611, 725
Bleem, L. E., Stalder, B., de Haan, T., et al. 2015, ApJS, 216, 27
Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82
Bonnarel, F., Fernique, P., Bienaymé, O., et al. 2000, A&AS, 143, 33
Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103
Brammer, G., Pirzkal, N., McCullough, P., & MacKenty, J. 2014, Time-varying
Excess Earth-glow Backgrounds in the WFC3/IR Channel, Instrument Science Report WFC3 2014-03, 14 pages
Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503
Brinch, M., Greve, T. R., Sanders, D. B., et al. 2024, MNRAS, 527, 6591
Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000
Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2023, JWST Calibration
Pipeline, https://doi.org/10.5281/zenodo.8380331
Calvi, R., Castignani, G., & Dannerbauer, H. 2023, A&A, 678, A15
Calvi, R., Dannerbauer, H., Arrabal Haro, P., et al. 2021, MNRAS, 502, 4558
Calzetti, D. 2013, in Secular Evolution of Galaxies, ed. J. Falcón-Barroso & J. H.
Knapen (Cambridge University Press), 419
Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682
Cameron, A. J., Saxena, A., Bunker, A. J., et al. 2023, A&A, 677, A115
Capak, P. L., Riechers, D., Scoville, N. Z., et al. 2011, Nature, 470, 233


Article number, page 21 of 27

_A&A proofs:_ manuscript no. main



Cappellari, M., Bacon, R., Bureau, M., et al. 2006, MNRAS, 366, 1126
Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245
Carniani, S., Venturi, G., Parlanti, E., et al. 2024, A&A, 685, A99
CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501
Casey, C. M. 2016, ApJ, 824, 36
Casey, C. M., Cooray, A., Capak, P., et al. 2015, ApJ, 808, L33
Casey, C. M., Narayanan, D., & Cooray, A. 2014, Physics Reports, 541, 45
Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, ApJ, 923, 215
Ceverino, D., Sánchez Almeida, J., Muñoz Tuñón, C., et al. 2016, MNRAS, 457,
2605
Chabrier, G. 2003, PASP, 115, 763
Chanchaiworawit, K., Guzmán, R., Salvador-Solé, E., et al. 2019, ApJ, 877, 51
Chapman, S. C., Blain, A., Ibata, R., et al. 2009, ApJ, 691, 560
Chapman, S. C., Lewis, G. F., Scott, D., et al. 2001, ApJ, 548, L17
Cid Fernandes, R., Stasi´nska, G., Schlickmann, M. S., et al. 2010, MNRAS, 403,
1036
Conselice, C. J., Wilkinson, A., Duncan, K., & Mortlock, A. 2016, ApJ, 830, 83
Cox, T. J. 2009, in Astronomical Society of the Pacific Conference Series, Vol.
419, Galaxy Evolution: Emerging Insights and Future Challenges, ed. S. Jogee, I. Marinova, L. Hao, & G. A. Blanc, 235
Cresci, G., Mannucci, F., Maiolino, R., et al. 2010, Nature, 467, 811
Curti, M., Cresci, G., Mannucci, F., et al. 2017, MNRAS, 465, 1384
Curti, M., Maiolino, R., Cirasuolo, M., et al. 2020a, MNRAS, 492, 821
Curti, M., Maiolino, R., Curtis-Lake, E., et al. 2024, A&A, 684, A75
Curti, M., Mannucci, F., Cresci, G., & Maiolino, R. 2020b, MNRAS, 491, 944
Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517
Dannerbauer, H., Kurk, J. D., De Breuck, C., et al. 2014, A&A, 570, A55
Darvish, B., Scoville, N. Z., Martin, C., et al. 2020, ApJ, 892, 8
de Graaff, A., Rix, H.-W., Carniani, S., et al. 2024, A&A, 684, A87
Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451
D’Eugenio, F., Perez-Gonzalez, P., Maiolino, R., et al. 2023, arXiv e-prints,
arXiv:2308.06317 (submitted to Nature Astronomy)
Domínguez, A., Siana, B., Henry, A. L., et al. 2013, ApJ, 763, 145
Dressel, L. & Marinelli, M. 2023, in WFC3 Instrument Handbook for Cycle 31
v. 15.0, Vol. 15, 15
Dressler, A. 1980, ApJ, 236, 351
Endsley, R. & Stark, D. P. 2022, MNRAS, 511, 6042
Everett, W. B., Zhang, L., Crawford, T. M., et al. 2020, ApJ, 900, 55
Evrard, A. E., Bialek, J., Busha, M., et al. 2008, ApJ, 672, 122
Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, Rev. Mexicana Astron.
Astrofis., 53, 385
Fraternali, F., Karim, A., Magnelli, B., et al. 2021, A&A, 647, A194
Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1
Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001
Giménez-Arteaga, C., Brammer, G. B., Marchesini, D., et al. 2022, ApJS, 263,
17
Hao, C.-N., Kennicutt, R. C., Johnson, B. D., et al. 2011, ApJ, 741, 124
Harikane, Y., Ouchi, M., Ono, Y., et al. 2019, ApJ, 883, 142
Hashimoto, T., Álvarez-Márquez, J., Fudamoto, Y., et al. 2023, ApJ, 955, L2
Helton, J. M., Sun, F., Woodrum, C., et al. 2024, ApJ, 962, 124
Helton, J. M., Sun, F., Woodrum, C., et al. 2023, arXiv e-prints,
arXiv:2311.04270 (submitted to ApJ)
Herard-Demanche, T., Bouwens, R. J., Oesch, P. A., et al. 2023, arXiv e-prints,
arXiv:2309.04525 (submitted to MNRAS)
Hill, R., Chapman, S., Scott, D., et al. 2020, MNRAS, 495, 3124
Hirschmann, M., Charlot, S., Feltre, A., et al. 2023, MNRAS, 526, 3610
Hirschmann, M., Charlot, S., Feltre, A., et al. 2019, MNRAS, 487, 333
Hung, C.-L., Casey, C. M., Chiang, Y.-K., et al. 2016, ApJ, 826, 130
Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90
Ishiyama, T., Prada, F., Klypin, A. A., et al. 2021, MNRAS, 506, 4210
Jaffé, Y. L., Smith, R., Candlish, G. N., et al. 2015, MNRAS, 448, 1715
Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80
Jarugula, S., Vieira, J. D., Weiß, A., et al. 2021, The Astrophysical Journal, 921,
97, arXiv:2108.11319 [astro-ph]
Jiménez-Vicente, J., Mediavilla, E., Kochanek, C. S., & Muñoz, J. A. 2015, ApJ,
806, 251
Jones, G. C., Übler, H., Perna, M., et al. 2024, A&A, 682, A122
Kannan, R., Springel, V., Hernquist, L., et al. 2023, MNRAS, 524, 2594
Kashino, D., Lilly, S. J., Simcoe, R. A., et al. 2023, Nature, 617, 261
Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055
Kennicutt, R. C. & Evans, N. J. 2012, Annual Review of Astronomy and Astrophysics, 50, 531
Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J.
2001, ApJ, 556, 121
Kewley, L. J., Nicholls, D. C., & Sutherland, R. S. 2019, ARA&A, 57, 511
Kohandel, M., Pallottini, A., Ferrara, A., et al. 2024, A&A, 685, A72
Kroupa, P. 2001, MNRAS, 322, 231
Kugel, R., Schaye, J., Schaller, M., et al. 2023, MNRAS, 526, 6103
Kumari, N., James, B. L., & Irwin, M. J. 2017, MNRAS, 470, 4618
Lambas, D. G., Alonso, S., Mesa, V., & O’Mill, A. L. 2012, A&A, 539, A45


Article number, page 22 of 27



Laporte, N., Zitrin, A., Dole, H., et al. 2022, A&A, 667, L3
Laseter, I. H., Maseda, M. V., Curti, M., et al. 2024, A&A, 681, A70
Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713
Lim, S., Scott, D., Babul, A., et al. 2021, MNRAS, 501, 1803
Lim, S., Tacchella, S., Schaye, J., et al. 2024, arXiv e-prints, arXiv:2402.17819
Litke, K. C., Marrone, D. P., Aravena, M., et al. 2023, ApJ, 949, 87
Lo Faro, B., Buat, V., Roehlly, Y., et al. 2017, MNRAS, 472, 1372
Magnelli, B., Popesso, P., Berta, S., et al. 2013, A&A, 553, A132
Mahajan, S., Mamon, G. A., & Raychaudhury, S. 2011, MNRAS, 416, 2882
Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2023, arXiv e-prints,
arXiv:2308.01230 (submitted to A&A)
Mantz, A. B., Abdulla, Z., Carlstrom, J. E., et al. 2014, ApJ, 794, 157
Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51
McConachie, I., Wilson, G., Forrest, B., et al. 2022, ApJ, 926, 37
Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469
Mocanu, L. M., Crawford, T. M., Vieira, J. D., et al. 2013, ApJ, 779, 61
Morishita, T., Roberts-Borsani, G., Treu, T., et al. 2023, ApJ, 947, L24
Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67
Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563
Nightingale, J., Hayes, R., Kelly, A., et al. 2021, The Journal of Open Source
Software, 6, 2825
Nightingale, J. W. & Dye, S. 2015, MNRAS, 452, 2940
Nightingale, J. W., Dye, S., & Massey, R. J. 2018, MNRAS, 478, 4738
Osterbrock, D. E. 1989, Astrophysics of Gaseous Nebulae and Active Galactic
Nuclei (University Science Books)
Overzier, R. A. 2016, A&A Rev., 24, 14
Overzier, R. A., Guo, Q., Kauffmann, G., et al. 2009, MNRAS, 394, 577
Papovich, C., Cole, J. W., Yang, G., et al. 2023, ApJ, 949, L18
Parlanti, E., Carniani, S., Übler, H., et al. 2024, A&A, 684, A24
Pereira-Santaella, M., Rigopoulou, D., Farrah, D., Lebouteiller, V., & Li, J. 2017,
MNRAS, 470, 1218
Pérez-González, P. G., Barro, G., Annunziatella, M., et al. 2023, ApJ, 946, L16
Pérez-González, P. G., Gil de Paz, A., Zamorano, J., et al. 2003, MNRAS, 338,
508
Pérez-González, P. G., Rieke, G. H., Villar, V., et al. 2008, ApJ, 675, 234
Perna, M. 2023, IAU Symposium, 373, 60
Perna, M., Arribas, S., Colina, L., et al. 2022, A&A, 662, A94
Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89
Piqueras López, J., Colina, L., Arribas, S., & Alonso-Herrero, A. 2013, A&A,
553, A85
Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13
Polletta, M., Soucail, G., Dole, H., et al. 2021, A&A, 654, A121
Prada, F., Behroozi, P., Ishiyama, T., Klypin, A., & Pérez, E. 2023, arXiv e-prints,
arXiv:2304.11911 (submitted to Nature)
Rauscher, B. J., Arendt, R. G., Fixsen, D. J., et al. 2017, PASP, 129, 105003
Reddy, N. A., Topping, M. W., Sanders, R. L., Shapley, A. E., & Brammer, G.
2023, ApJ, 948, 83
Reddy, N. A., Topping, M. W., Shapley, A. E., et al. 2022, ApJ, 926, 31
Remus, R.-S., Dolag, K., & Dannerbauer, H. 2023, ApJ, 950, 191
Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS,
507, 3952
Rodríguez Del Pino, B., Perna, M., Arribas, S., et al. 2024, A&A, 684, A187
Sánchez Almeida, J., Elmegreen, B. G., Muñoz-Tuñón, C., & Elmegreen, D. M.
2014, A&A Rev., 22, 71
Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy, N. A., & Brammer, G. B.
2024, ApJ, 962, 24
Schaye, J., Kugel, R., Schaller, M., et al. 2023, MNRAS, 526, 4978
Scholtz, J., Witten, C., Laporte, N., et al. 2023, arXiv e-prints, arXiv:2306.09142
(submitted to A&A)
Shapley, A. E., Sanders, R. L., Reddy, N. A., Topping, M. W., & Brammer, G. B.
2023, ApJ, 954, 157
Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, ApJ, 788, 125
Spilker, J. S., Hayward, C. C., Marrone, D. P., et al. 2022, ApJ, 929, L3
Springel, V. 2010, MNRAS, 401, 791
Springel, V., Pakmor, R., Pillepich, A., et al. 2018, MNRAS, 475, 676
Springel, V., White, S. D. M., Jenkins, A., et al. 2005, Nature, 435, 629
Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJ, 842, L15
Strom, A. L., Steidel, C. C., Rudie, G. C., et al. 2017, ApJ, 836, 164
Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69
Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267
Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157
The Astropy Collaboration, Robitaille, Thomas P., Tollerud, Erik J., et al. 2013,
A&A, 558, A33
Toft, S., Smolˇci´c, V., Magnelli, B., et al. 2014, ApJ, 782, 68
Übler, H., D’Eugenio, F., Perna, M., et al. 2024, arXiv e-prints,
arXiv:2403.03192 (submitted to MNRAS)
Übler, H., Genzel, R., Wisnioski, E., et al. 2019, ApJ, 880, 48
Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, A&A, 677, A145
Umehata, H., Tamura, Y., Kohno, K., et al. 2015, ApJ, 815, L8
Van Der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science
and Engineering, 13, 22
van Dokkum, P. G. 2001, PASP, 113, 1420
Vieira, J. D., Crawford, T. M., Switzer, E. R., et al. 2010, ApJ, 719, 763
Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233
Wang, F., Yang, J., Hennawi, J. F., et al. 2024, ApJ, 962, L11
Wang, G. C. P., Hill, R., Chapman, S. C., et al. 2021, MNRAS, 508, 3754
Wang, T., Elbaz, D., Daddi, E., et al. 2016, ApJ, 828, 56
Wang, T., Elbaz, D., Daddi, E., et al. 2018, ApJ, 867, L29
Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS,
523, 3119
Wu, P.-F., Bezanson, R., D’Eugenio, F., et al. 2023, ApJ, 955, 75
York, D. G., Adelman, J., Anderson, John E., J., et al. 2000, AJ, 120, 1579
Zavala, J. A., Buat, V., Casey, C. M., et al. 2023, ApJ, 943, L9
Zhou, L., Wang, T., Daddi, E., et al. 2024, A&A, 684, A196

Santiago Arribas et al.: The core of a protocluster at z=6.9



**Appendix A:** **Spectral characterisation: Methods**


_Appendix A.1:_ _Definition of extraction apertures for regional_
_integrated spectra_


We defined a set of extraction apertures, which were used to obtain the integrated spectra for the sources in SPT0311–58 (Fig.
A.1). The definition of these apertures is, in some cases, difficult
because the emission distribution of the lines and the continuum
is different, and also because the presence of artefacts force us
to exclude some spaxels from the aperture that would have been
otherwise included. As a consequence, the absolute fluxes inferred from the spectra should be taken with caution, also considering that the calibration of the instrument is not consolidated
yet. However, the velocity determinations, and the flux line ratios should be reliable within the uncertainties imposed by the
S/N. In addition, we obtained and applied specific aperture corrections to the individual apertures, which (partially) correct the
derived absolute fluxes (see next section).


Figure A.1 shows the apertures used. On the left panel, yellow lines indicate the apertures for the z ∼ 6.9 sources. For the W
galaxy we use a dashed line to indicate that this aperture is not
defined on the basis of the NIRSpec data, but from the 160 µm
continuum ALMA image. Subregions within the E galaxy are
indicated with pink lines. For the low-z objects the apertures are
displayed with cyan lines (see also Fig. 3 for a simplified version
of this figure). The red region in this panel represents the region
used to obtain the background spectrum. In the right panel, we
show additional apertures, including the ones with 1 arcsec in diameter (i.e. E1c and W1c, in orange lines) used to compare with
the Paα measurements obtained with MIRI (Álvarez-Márquez
et al. (2023)). In this panel the red regions represent the spaxels used to probe the external diffuse external emission outside
the E and W galaxies (i.e. the E _ext_ and W _ext_ apertures). These
extended apertures were only used to probe the Hα emission at
the redshift of SPT0311–58, so the fact that for the W it includes
some emission from the lens galaxy is not critical. Nevertheless,
as it can be seen in the figure, we exclude the spaxels with the
brightest emission from the lens galaxy to minimise the noise.


_Appendix A.2:_ _Aperture corrections_


We obtained the aperture corrections making use of the highresolution G395H/290LP observations of the standard star
1808347 (PID:1128, Obs. 9; PI: N. Luetzgendorf), which were
reduced using the same pipeline version and context as for the
SPT0311–58 data. The aperture masks were shifted such that
they were centered with the peak of the star emission. Then
we define _filters_ of about 200 spectral pixels around two wavelengths (3.4 and 5.2 µm), and the fractions of light contained
within the aperture with respect to the total in the FoV were
computed. The results are summarised in Table A.1. We note
that for E _ext_ and W _ext_, defined for tracing the extended emission,
the aperture correction were not obtained. For L7, characterised
with a 2D spectral decomposition, the aperture correction is not
either computed.


_Appendix A.3:_ _High resolution (R2700) integrated spectra_


The integrated R2700 spectra for the sources and regions in
SPT0311–58 are presented in Fig. A.2. The R100 spectra were
presented in Fig. 5.



**Table A.1.** Aperture positions and corrections


ID X Y ∆α (”) ∆δ (”) AC-3.4 AC-5.2
E 35 52 +1.00 -0.15 0.87 0.83
E _cir_ [1] 34 52 +1.05 -0.15 0.92 0.89
ESb 33 43 +1.10 -0.60 0.72 0.65

EN 36 57 +0.95 +0.10 0.81 0.75

ENa 34 52 +1.05 -0.15 0.50 0.44

ENb 36 57 +0.95 +0.10 0.63 0.55

ENc 36 62 +0.50 +0.15 0.46 0.40

W 73 41 -0.90 -0.70 0.89 0.86
W _cir_ [1] 73 41 -0.90 -0.70 0.92 0.89
C1 49 70 +0.30 +0.75 0.76 0.70

C2 55 80 +0.00 +1.25 0.72 0.66

C3 80 32 -1.25 -1.15 0.51 0.45

L1 83 61 -1.40 +0.30 0.64 0.58

L2 67 73 -0.60 +0.90 0.55 0.49

L3 32 80 +1.15 +1.25 0.60 0.54

L4 45 58 +0.50 +0.15 0.62 0.56

L5 24 35 +1.55 -1.00 0.68 0.61

L6 49 36 +0.30 -0.95 0.59 0.56

lz1 28 32 +1.35 -1.15 0.34 0.27

lz2 17 39 +1.90 -0.80 0.54 0.48

lz3 27 42 +1.40 -0.65 0.61 0.54


**Notes.** Column 1: Aperture identification, Columns 2 and 3: X and Y
coordinates in the cube for the central spaxel of the aperture, Columns
4 and 5: relative sky coordinates with respect to the centre of the FoV
(i.e. spaxel [55,55], sky coordinates: α = 03 _[h]_ 11 _[m]_ 33 _[s]_ .248 and δ = -58º
23’ 33”.24). Columns 6 and 7: Aperture corrections at 3.4 µm and 5.2
µm, which correspond approximately to the observed wavelength of Hγ
and Hα at z=6.90. [1] Circular aperture of 1 arcsec in diameter.


_Appendix A.4:_ _Line fitting_


The emission lines in the R100 and R2700 integrated spectra were fit to single Gaussian profiles linking their relative
fluxes and wavelengths according to their atomic parameters,
and imposing the same line width for all the lines. The spectral ranges [OII], Hβ-[OIII], and Hα-[NII] were fitted independently, though for the [OII] and Hα-[NII], the kinematic parameters were constrained to the one derived for the Hβ-[OIII] complex.
In the R100 spectra Hα and the [NII] lines are not well resolved and the results of the fit may be degenerated, especially at
low S/N. The [OII]λλ3726, 3728 doublet is unresolved at R2700
and fit with a single Gaussian, as in this case we were only interested in the total flux (i.e. not in the kinematics).
For the regions with the highest S/N (i.e. E galaxy), line fitting at spaxel level (or with moderate binning) was performed.
The R2700 spectra were used to disentangle two kinematically
distinct components following the approach described in Perna
et al. (2022) (see Sect. 3.3.3).


_Appendix A.5:_ _Line fluxes_


Table A.2 gives the line fluxes and their uncertainties obtained
from the Gaussian fits of the R100 and R2700 spectra for the

[OII]λλ3726, 3728, Hβ, [OIII]λ5008, Hα, and [NII]λ6584 lines.
As the main lines used in this work appear in both the R100
and R2700 datacubes, this give us the opportunity to compare
the derived fluxes with the two spectral configurations (see Fig.
A.3). As it is shown in the Figure, the fluxes span more than


Article number, page 23 of 27

_A&A proofs:_ manuscript no. main


**Fig. A.1.** Selected apertures. Left panel: Yellow lines indicate the apertures for the z ∼ 6.9 sources, while with cyan is used for the low-z objects,
including the lens galaxy. For the W galaxy we use a dashed line to indicate that this aperture is not defined on the basis of the NIRSpec data, but
from the 160 µm continuum ALMA image. Apertures for the subregions within the E galaxy are indicated with pink lines. The red region in this
panel marks the region used to obtain the background spectrum. Right panel: Additional apertures, including the ones with 1 arcsec in diameter
(i.e. E1c and W1c, in orange lines) used by Álvarez-Márquez et al. (2023). In this panel the red regions represent the spaxels used to probe the
diffuse external emission outside the E and W galaxies (i.e. the E _ext_ and W _ext_ apertures).



two orders of magnitude and indicate in general good agreement.
There is however a small systematic trend in the sense that R100
fluxes are about 10 percent higher than R2700 ones. As the R100
data are subject to larger uncertainties in the absolute calibration
(Charles Profitt, priv. comm.), we applied this 10 percent correction to the R100 data. After taking into account this factor
fluxes typically agree better than 20 percent, except few cases.
There is not a configuration (i.e. R100 or R2700) that is generally preferred for obtaining the fluxes. Their spectra have S/N
that in many cases are comparable, though they may differ on
other data quality aspects. For instance, the Hα line at the redshift of SPT0311–58 is very close the edge of the spectra, leaving
in the case of R100 few pixels for the determination of the continuum redwards the line. Moreover, in R100 spectra Hα and the

[NII] lines are not resolved, which makes the fits degenerated
especially in a low S/N regime. On the other hand, the R2700
datacube is affected in some cases by artefacts that could not be
removed by the pipeline nor by a posterior processing. Table A.2
gives further details on the derived fluxes for the lines.


**Appendix B:** **Magnification map**


The present data allow us to determine accurately the redshift,
light profile, and stellar mass of the lens galaxy, and therefore
they offer the opportunity to create a lens model and obtain the
magnification factors for each source in the FoV. To this aim
we use the public lens modeling software PyAutoLens (Nightingale & Dye 2015, Nightingale et al. 2018, 2021), and follow the
methodology described in Jones et al. (2024).
First, we generate a panchromatic image collapsing the R100
datacube over the spectral range 1–5 µm (i.e. rest-frame ∼ 0.49 –
2.45 µm at the lens redshift). The light profile for the lens galaxy
in this image was fitted with a Sérsic profile, and we model the
PSF as a circular Gaussian with FWHM= 0.1 [′′] . The fitting process results in the best-fit centroid position, intrinsic axis ratio
( _q_ ≡ _a_ / _b_ ), position angle (ϕ), effective radius (r eff ), and Sérsic
index (n) of the light profile. We assume that the mass profile
can be represented by an isothermal ellipsoid with the same ge

Article number, page 24 of 27



ometrical properties as the light profile (i.e. centroid, q, ϕ), but
an Einstein radius based on the stellar mass of the galaxy obtained from the R100 spectra as in Sect. 4.1 (i.e. log( _M_ ⋆ /M ⊙ =
9.39) and the expected stellar mass surface fraction following
Jiménez-Vicente et al. (2015). The resulting lens parameters are
listed in Table B.1. This model was used to create a magnification map, from which we obtained the factors included in Table
B.2 (see also Fig. B.1). Since source W is multiply imaged, it
was not included in this simple analysis, and we adopt the magnification factor of Marrone et al. (2018) instead.

Santiago Arribas et al.: The core of a protocluster at z=6.9


**Table A.2.** Line fluxes for the sources and regions in the FoV [1]


Sp OII-R100 OII-R2700 Hβ-R100 Hβ-R2700 OIII-R100 OIII-R2700 Hα-R100 Hα-R2700 NII-R100 NII-R2700
E 8.71±0.48 8.52±0.43 4.50±0.17 4.46±0.24 15.49±0.19 14.48±0.28 21.03±0.33 18.59±0.56 5.54±0.27 4.52±0.48

E1c 8.08±0.56 8.91±0.56 4.65±0.19 4.77±0.29 15.46±0.22 14.47±0.34 22.91±0.52 18.57±0.71 5.24±0.43 4.12±0.61
E _ext_ 10.04±0.56 10.77±0.83 15.38±1.51 [2] 13.82±2.34 0.14±2.64
ES 1.95±0.18 1.51±0.17 0.70±0.08 0.70±0.08 2.00±0.09 1.98±0.09 3.88±0.11 3.09±0.25 0.98±0.09 1.25±0.23

EN 4.74±0.24 4.39±0.25 2.81±0.10 2.42±0.14 10.26±0.11 9.14±0.16 11.88±0.20 10.49±0.32 3.33±0.17 1.85±0.27

ENa 1.15±0.07 1.41±0.11 0.73±0.04 0.86±0.07 2.93±0.05 2.95±0.08 3.02±0.05 3.34±0.20 0.81±0.04 0.88±0.19

ENb 1.86±0.12 1.35±0.10 1.00±0.05 0.87±0.05 3.47±0.05 3.10±0.06 4.06±0.10 3.39±0.12 1.21±0.08 0.56±0.10

ENc 0.40±0.05 0.35±0.07 0.20±0.04 0.14±0.03 0.91±0.04 0.69±0.03 0.99±0.05 0.76±0.06 0.22±0.04 0.16±0.05
W [3] 1.28±0.28 4.93±0.52 1.08±0.41

W1c 1.10±0.24 2.78±0.32 3.02±0.49 1.13±0.26 1.32±0.41
W _ext_ 2.12±0.66 7.35±0.64 6.00±0.74 5.77±0.78 3.01±0.68
C1 1.41±0.12 1.14±0.13 0.54±0.09 0.31±0.08 1.55±0.10 1.52±0.09 1.74±0.12 1.39±0.24 0.38±0.10 <0.876
C2 0.54±0.10 0.47±0.11 0.31±0.07 1.59±0.09 1.27±0.06 1.07±0.12 [2] 0.88±0.13 <0.465

C3 0.55±0.17 0.26±0.07 0.32±0.06 0.77±0.08 0.64±0.07 1.49±0.19 1.19±0.18 0.54±0.15

L1 0.49±0.11 0.30±0.07 0.28±0.05 3.17±0.08 2.95±0.06 1.28±0.12 1.29±0.12 <0.429

L2 0.64±0.06 0.40±0.04

L3 0.70±0.09 0.77±0.05 0.50±0.12 0.49±0.12
L4 (0.74±0.06) [4] (0.31±0.05) [4] 0.76±0.09 0.59±0.13 0.29±0.08
L5 0.71±0.10 0.41±0.05 3.16±0.12 2.56±0.06 1.89±0.23 [2] 1.55±0.11 <0.565

L6 0.61±0.08 0.59±0.06 0.51±0.08 0.52±0.10


**Notes.** [1] From the integrated spectra in the apertures defined in Fig. A.1, in units of 10 [−][18] erg/s/cm [−][2] . For E and W galaxies we also include values
in apertures of 1 arcsec in diameter as in Álvarez-Márquez et al. (2023). No aperture corrections, nor 10 percent correction for R100 fluxes are
applied. [2] The fit for the Hα -[NII] complex gives no flux for the [NII]lines. [3] For W, R100 Hβ flux is contaminated by the lens galaxy. For the
Hα flux the R100 spectrum is preferred because the large velocity range covered by the aperture induces a significant increase of noise in the high
resolution spectrum. [4] Difference between R100 and R2700 fluxes are larger than × 2, and not considered. The upper limits correspond to 3-σ the
noise level.


_q_ ϕ [ [◦] ] r eff [ [′′] ] _n_ r Ein [ [′′] ]
2.92 ± 0.01 59.32 ± 0.08 0.266 ± 0.001 1.01 ± 0.01 0.17
**Table** **B.1.** Best-fit lens model parameters, including axis ratio ( _q_ ), position angle ϕ, effective radius and Sérsic radius of the light profile, and
Einstein radius.


Component Magnification
E,L7 1.15
C1 1.21

C2 1.10

C3 1.40

L1 1.14

L2 1.12

L3 1.11

L4 1.62

L5 1.06

L6 1.14
W (2.2)
**Table** **B.2.** Approximate magnification factors for each galaxy in the
FoV, as derived from the determinant of the Jacobian of our best-fit lens
model. Since source W is multiply imaged, it is not included in this
simple analysis and we state the magnification factor of Marrone et al.
(2018) instead.


Article number, page 25 of 27

0


50


0


10


5


20


0


5


0


10


0


2


0

50


0


50


0


5


0


5


0


5


0


10


0


2


0

5


0


2



50


0


0


10


5



_A&A proofs:_ manuscript no. main


0


50


0


10


5


20


0


5


0


10


0


2


0

50


0


50


0


5


0


5


0


5


0


10


0


2


0

5


0


2





20


0


0


0





2


0

50


0



50


0





5


0





5


0



0


10


0


2


0







5


0


0

20



0

20


0


2.5





0


2.5





0

20


0


2.5



0.0
2.90 2.95 3.00 3.05 3.10



0.0



0.0
5.10 5.15 5.20 5.25



3.103.80 3.85 3.90 3.95 4.00
### Observed wavelength ( m)



**Fig.** **A.2.** R2700 spectra in the region of the [OII]λλ3726,3728, Hβ-[OIII]λλ4959,5007, and Hα-[NII]λ6584 for the sources and regions in
SPT0311-58. The vertical lines mark the central position of these lines at the redshift of the source.


Article number, page 26 of 27

Santiago Arribas et al.: The core of a protocluster at z=6.9


**Fig. A.3.** Comparison of the line fluxes obtained from R100 and R2700 integrated spectra. Fluxes from R100 spectra are reduced by 10 percent
(see text). The dashed lines correspond to the 1:1 and 1:1.1 ratios. Colours distinguish between lines, and green text labels indicate the aperture/spectrum.


2.0

1.8



-58°23'32"


33"


34"


35"


36"











1.6


1.4


1.2


1.0









3 [h] 11 [m] 33.4 [s] 33.2 [s] 33.0 [s]


Right Ascension


**Fig. B.1.** Magnification map defined as the inverse of the determinant of the Jacobian of our best-fit lens model. The critical lines are displayed
in cyan, and positions of galaxies are marked with text. In order to display the small magnifications of the distant components, we only display
magnifications below µ < 2. For reference, we display the panchromatic image of the lensing galaxy.


Article number, page 27 of 27


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[1]",
  "value": "03h11m33.248s -58d23m33.24s",
  "failed_quote": "The absolute sky coordinates (ICRS) of the centre of the FoV (i.e. spaxel [55,55]) are α = 03 h 11 m 33 s .248 and δ = –58º 23’ 33”.24, and correspond to (0,0) in Fig. 1, and other spectral maps in the paper."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "z = 6.90",
  "failed_quote": "The absolute sky coordinates (ICRS) of the centre of the FoV (i.e. spaxel [55,55]) are α = 03 h 11 m 33 s .248 and δ = –58º 23’ 33”.24, and correspond to (0,0) in Fig. 1, and other spectral maps in the paper."
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "Strandet et al. (2017); spectroscopic measurements in this paper",
  "failed_quote": "The absolute sky coordinates (ICRS) of the centre of the FoV (i.e. spaxel [55,55]) are α = 03 h 11 m 33 s .248 and δ = –58º 23’ 33”.24, and correspond to (0,0) in Fig. 1, and other spectral maps in the paper."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "SED fitting method for R100 spectra and empirical PSF for aperture correction",
  "failed_quote": "The observed fluxes were corrected by a wavelength-dependent aperture correction according to the empirical PSF derived by D’Eugenio et al. (2023), and by magnification (Appendix B)."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[1]",
  "value": "spaxel scale = 0.05 arcsec; [C II] integration range = -1000 to +1200 km s^-1 (w.r.t. z=6.900); S/N threshold for [C II] moment 1 and 2 = 2.3",
  "failed_quote": "Before producing the moment 1 and moment 2 maps, the spaxels with low signal-to-noise ratio (S/N< 2.3) and those with spurious emission in each 20 km s −1 velocity channel were masked."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Isothermal ellipsoid mass profile for lens with same centroid, axis ratio, and PA as light profile; mu = 2.2 for galaxy W from Marrone et al. (2018)",
  "failed_quote": "We assume that the mass profile can be represented by an isothermal ellipsoid with the same geometrical properties as the light profile (i.e. centroid, q, ϕ)"
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Compute galaxy dynamical masses from R2700 [O III] velocity dispersions and 2D Gaussian effective radii; compare NIRSpec [O III] and ALMA [C II] kinematics; estimate protocluster dark-matter halo mass M_h and R_200 from total stellar mass; and test virialisation via K-S test, bootstrap cluster velocity dispersion, and projected phase space diagram.",
  "failed_quote": "The integrated velocity dispersion (σ, see Table 2) can be used to estimate the dynamical mass (M dyn ) of the galaxies through the formula: M dyn = K σ 2 R e / G"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Redshift of E galaxy ([O III]-H-beta) = 6.91956 dimensionless",
  "failed_quote": "E 6.91956 ± 0.00008 666. ± 3. 155. ± 3. 2.12 ± 0.63 59. +70 −21 . 10.7 ± 0.3"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Integrated velocity dispersion of E galaxy (sigma) = 155 km s^-1",
  "failed_quote": "E 6.91956 ± 0.00008 666. ± 3. 155. ± 3. 2.12 ± 0.63 59. +70 −21 . 10.7 ± 0.3"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Dynamical mass of E galaxy (M_dyn) = 59e9 M_sun",
  "failed_quote": "E 6.91956 ± 0.00008 666. ± 3. 155. ± 3. 2.12 ± 0.63 59. +70 −21 . 10.7 ± 0.3"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Post-starburst interpretation for the discrepancy between SFR(FIR) and SFR(H-alpha) in the W galaxy: rejected in favour of heavy dust obscuration because W is extremely dusty with high nebular attenuation.",
  "failed_quote": "However, these PSB galaxies also display lower nebular attenuation than what we infer for the W galaxy; in our case, because we are dealing with an extremely dusty galaxy, we favour the star-forming interpretation, and explain the discrepancy between the SFR(Hα) and SFR(FIR) as due to heavy dust attenuation."
 }
]
```
