# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.524.3671Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–13 (2023) Preprint 25 March 2026 Compiled using MNRAS L [A] TEX style file v3.2

## **Discovery of a radio jet in the Cloverleaf Quasar at z = 2.56**


Lei Zhang, [1] _[,]_ [2] Zhi-Yu Zhang, [1] _[,]_ [2] _[★]_ James. W. Nightingale, [3] Ze-Cheng Zou, [1] _[,]_ [2] Xiaoyue Cao, [4] _[,]_ [5] _[,]_ [6]

Chao-Wei Tsai, [5] Chentao Yang, [7] _[,]_ [8] Yong Shi, [1] _[,]_ [2] Junzhi Wang, [9] _[,]_ [10] Dandan Xu, [11] Ling-Rui Lin, [1] _[,]_ [2]

Jing Zhou, [1] _[,]_ [2] Ran Li, [6] _[,]_ [5] _[,]_ [4]

1 _School of Astronomy and Space Science, Nanjing University, Nanjing 210023, People’s Republic of China_
2 _Key Laboratory of Modern Astronomy and Astrophysics (Nanjing University), Ministry of Education, Nanjing 210023, People’s Republic of China_
3 _Department of Physics, Institute for Computational Cosmology, Durham University, South Road, Durham DH1 3LE, UK_
4 _School of Astronomy and Space Science, University of Chinese Academy of Sciences, Beijing 100049, People’s Republic of China_
5 _National Astronomical Observatories, Chinese Academy of Sciences, 20A Datun Road, Chaoyang District, Beijing 100012, People’s Republic of China_
6 _Institute for Frontiers in Astronomy and Astrophysics, Beijing Normal University, Beijing 102206, People’s Republic of China_
7 _Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, SE-439 92 Onsala, Sweden_
8 _European Southern Observatory, Alonso de Córdova 3107, Vitacura, Casilla 19001, Santiago de Chile, Chile_
9 _Shanghai Astronomical Observatory, Chinese Academy of Science, 80 Nandan Road, Shanghai 200030, People’s Republic of China_
10 _Guangxi Key Laboratory for Relativistic Astrophysics, Department of Physics, Guangxi University, Nanning 530004, PR China_
11 _Department of Astronomy, Tsinghua University, Beijing 100084, China_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

The fast growth of supermassive black holes and their feedback to the host galaxies play an important role in regulating
the evolution of galaxies, especially in the early Universe. However, due to cosmological dimming and the limited angular
resolution of most observations, it is difficult to resolve the feedback from the active galactic nuclei (AGNs) to their host galaxies.
Gravitational lensing, for its magnification, provides a powerful tool to spatially differentiate emission originating from AGN
and host galaxy at high redshifts. Here we report a discovery of a jet-like radio structure in a strongly lensed starburst quasar,
H1413+117 or Cloverleaf at redshift _𝑧_ = 2 _._ 56, based on observational data at optical, sub-millimetre, and radio wavelengths. With
both parametric and non-parametric lens models and with reconstructed images in the source plane, we find a well-separated,
kpc-scaled, single-sided radio jet located at projected ∼1 _._ 2 kpc to the northwest of the host galaxy in the source plane. This could
indicate the co-existence of feedback from the AGN by both wind and jet in the Cloverleaf quasar.


**Key words:** gravitational lensing: strong – galaxies: high-redshift – submillimetre: galaxies.



**1** **INTRODUCTION**


The correlated growth of the bulge mass of a galaxy and its supermassive black hole (SMBH) mass throughout cosmic time has been
described as their co-evolution (Ferrarese & Ford 2005; Kormendy
& Ho 2013). When the SMBH actively accretes, the active galactic nucleus (AGN) turns on, which can drive powerful feedback to
the surrounding interstellar medium (ISM) of the host galaxy. The
radiation pressure and the energetic particles in the AGN wind and
jet behave as the main forms of feedback. The feedback process can
sweep and heat up the cold gas along its radial paths and, as a result,
quench the star formation (Springel et al. 2005; McNamara & Nulsen
2007; Cattaneo et al. 2009). For the high-luminosity quasars, the host
galaxy and surrounding environment receive powerful feedback from
its AGN through electromagnetic radiation (known as quasar mode),
kinetic jets (known as radio mode), or both (Fabian 2012; Kormendy
& Ho 2013; Churazov et al. 2005).
Similar to the cosmic star formation, the evolution of quasi-stellar
object (QSO) activity also shows a strong cosmic evolution, reaching


_★_ E-mail: zzhang@nju.edu.cn


© 2023 The Authors



its peak at _𝑧_ ∼ 2 (e.g., Schmidt & Green 1983; Wolf et al. 2003).
The feedback of QSOs in this era is therefore considered as the key
mechanism to quench star formation. Galactic outflows driven by
AGNs (e.g., Farrah et al. 2012; Cano-Díaz et al. 2012; Nesvadba
et al. 2011; Alexander et al. 2010; Prochaska & Hennawi 2009;
Nesvadba et al. 2008) have shown evidence of quenching. Highvelocity galactic winds, which are commonly detected with the broad
absorption lines against a strong quasar continuum (e.g., Dunn et al.
2010; Moe et al. 2009; Saez et al. 2009) and also evidenced with
highly-ionized Fe lines in low-luminosity AGNs (Shi et al. 2021),
can efficiently remove the ISM from the host galaxies. On the other
hand, radio lobes/jets (e.g., Gopal-Krishna & Wiita 2001; McNamara
& Nulsen 2007; Cattaneo & Best 2009; Cattaneo et al. 2009; Fabian
2012), which are often discovered on scales from several tens of kpc
to Mpc, can also directly impact star formation.


However, the majority of high-redshift QSOs have very compact
sizes (Silverman et al. 2019; Li et al. 2021; Ding et al. 2022), which
limits the separation between their host galaxy and AGN-related components. Multiple-wavelength observations with spatial resolutions
on scales of sub-kpc are therefore needed, which are still extremely

2 _L. Zhang et al._


difficult, given the capability of current instruments and cosmological dimming effects (Lanzetta et al. 2002).


Gravitational lensing serves as a powerful tool to improve both
sensitivity and spatial resolution. With proper demagnification modelling, the lensing system allows us to resolve the detailed galactic
structures of high- _𝑧_ QSOs for case studies. Cloverleaf (also known as
H1413+117) is one such target. Discovered by Magain et al. (1988), it
is a strongly lensed starburst galaxy with a bright AGN at _𝑧_ = 2 _._ 558. It
contains four images at both optical and sub-millimetre wavelengths
(Kneib et al. 1998). With the detections of CO, HCN, and FIR emission, Cloverleaf is confirmed to contain an extensive molecular disc
of ∼1 _._ 6 kpc in diameter, a molecular gas mass of ∼ 10 [10] M ⊙, and a
star formation rate of 10 [3] M ⊙ yr [−][1] (Solomon et al. 2003; Venturini
& Solomon 2003; Barvainis et al. 1997; Weiß et al. 2003). On the
other hand, information about this system in the lens plane is limited
due to the lens galaxy’s faint emission (Lawrence 1996; Angonin
et al. 1990; Turnshek et al. 1997), while Chantry & Magain (2007)
suggested a deconvolved lens image from Hubble Space Telescope
(HST) _F160W_ and _F160W_ data. The redshift of the lens galaxy is derived from the Hi narrow absorption systems (Turnshek et al. 1988;
Magain et al. 1988) at _𝑧_ ∼ 1 _._ 7.


With the latest high-sensitivity, high-resolution, and high-fidelity
data of Cloverleaf system from ALMA, VLA, and HST, we are able
to not only compare morphologies from different gas phases but also
constrain the lens galaxy mass models more accurately than previous
models. The traditional method (e.g. Kneib et al. 1998), which is
based on parametric modelling, has limitations in the cases of irregular sources. The newly developed non-parametric modelling, which
is required for high angular resolution and high sensitivity analysis, greatly improves the reconstructed source plane (Nightingale &
Dye 2015; Nightingale et al. 2018) and thus, the structures of the
Cloverleaf system can be well distinguished.


This work focuses on observational data at three wavelengths: (i)
optical, which is dominated by the QSO emission and is seen as
almost four point sources from HST images (Kneib et al. 1998);
(ii) Sub-millimetre, which traces the gaseous dusty disk of the host
galaxy (Solomon et al. 2003; Granato et al. 1996), with current
ALMA observations having enough resolution to resolve the four
images and; (iii) radio, where the radio emission traces relativistic
charged particles accelerated by the radio jet (Kayser et al. 1990)
launched by the central AGN or starburst. With these data, we can
separate the AGN contribution from the host galaxy.


This paper is organized as follows: Observations and data reduction
are presented in Section 2. The modelling processes, the lens models
of the host galaxy, and the newly discovered radio jet, which are built
up with both parametric and non-parametric models, are shown in
Section 3. In Section 4, we analyse the spatial distribution of multiwavelength images and the spectral energy distribution (SED) of
radio emission. In Section 5, we discuss the confirmation, emission
components, and feedback of this radio jet. Last, we conclude the
summary in Section 6.


Throughout the paper, we assume a cosmology with Ω m = 0 _._ 310,
Ω Λ = 0 _._ 689, and _𝐻_ 0 = 67 _._ 7 km s [−][1] Mpc [−][1] (Planck Collaboration
et al. 2020). In this case, 1 [′′] corresponds to ∼8.7 kpc in the lens
plane at _𝑧_ = 1 _._ 7 and ∼8.22 kpc in the source plane at _𝑧_ = 2 _._ 56.


MNRAS **000**, 1–13 (2023)



**2** **MULTI-BAND OBSERVATIONAL DATA AND DATA**

**REDUCTION**


We obtain multi-wavelength, high-angular-resolution data from the
archival systems of HST (optical), ALMA (sub-millimetre), VLA
(radio), and e-Merlin (radio).


**2.1** **HST F814W Image**


The optical image is obtained from the HST archive. This three-orbit
observation was performed on 26th Jan 2000, with the Advanced
Camera for Surveys (ACS) and the F814W filter. We choose the ACS
images for their high spatial sampling rate of 0.05 [′′] pix [−][1] ( **?** ). We
stacked all ACS images with SWARP (Bertin et al. 2002). We use
imfit in Common Astronomy Software Applications version 6.1.2.7
(CASA) (McMullin et al. 2007) to fit a star located at (14 : 15 :
47 _._ 39856 _,_ +11 : 29 : 50 _._ 7480) (2MASS id: J14154739+1129507
(Cutri et al. 2003)) in the field and obtain its full width at half
maximum (FWHM) to be ∼0.08 arcsec, which is adopted as the
image resolution. The rms noise is evaluated to 0.2 erg s [−][1] cm [−][2] Å −1

(below referred as counts).


**2.2** **ALMA 300 GHz continuum**


We adopt the ALMA archival data from projects 2012.1.00175.S (PI:
van der Werf, Paul) and 2017.1.00963.S (PI: Sharon, Chelsea), both
observed at Band 7 (see Table 1 for observational details).
We calibrate the raw data with CASA (version 6.1.2.7 McMullin
et al. 2007) with the associated standard pipeline. Then we combine
all the calibrated on-source data and omit the frequency range of
CO _𝐽_ =11-10. We invert the combined visibility data by task tclean
with the ‘mfs’ mode, a gridder of mosaic, a cell size of 0.02 [′′], and a
Briggs weighting with a robust of 1.5. The synthesised image (see
Fig. 1 top right) has a beam size of 0 _._ 26 [′′] × 0 _._ 20 [′′] and a position
angle of −31 deg. The noise level is 35 _𝜇_ Jy beam [−][1], estimated from
the emission-free area in the field.


**2.3** **VLA Archival data**


_2.3.1_ _VLA 8.4 GHz continuum_


The Very Large Array (VLA) 8.4 GHz data were obtained from the
NRAO archive [1] . This data have been originally presented by Kayser
et al. (1990). The project IDs are AS357 and AC243, which were
performed on 13 Jan. 1989 and 04 Feb. 1989, respectively. Both
observations were done with the A-configuration of the VLA. The
total observing time was ∼5 hours and 4 hours, with ∼1.5 hours
and 1 hour effective on-source time, respectively. Each on-source
scan took 15 minutes and 10 minutes with a sampling time of 1
second. In both observations, 3C 286 (1328+307) was adopted as
both flux and bandpass calibrators, while the phase calibrator was
1413+135 in B1950 (or, J1415+1320 in J2000). The receivers were
configured with two spectral line windows (SPW), centring at 8.415
and 8.464 GHz, respectively. Each SPW covers a 50 MHz bandwidth,
offering a total bandwidth of 100 MHz, with full stock polarisations.
The baselines of both observations range from 15 k _𝜆_ to 950 k _𝜆_ in the
UV space.
The data was first imported to AIPS and converted to the uvfits


1 `[https://data.nrao.edu/portal](https://data.nrao.edu/portal)`

_Radio Jet of Cloverleaf_ 3


**Table 1.** Details of the observations on Cloverleaf from the ALMA data archive.


Proj. ID Date Calibrators Freq. Coverage Baseline On-source Time
Gain Flux/BP LSB (GHz) USB (GHz) _𝑘𝜆_ min


2012.1.00175.S 25 Jun. 2015 Titan J1415+1320 325.86–329.28 338.43–341.46 28–1433 68

2012.1.00175.S 30 Jun. 2015 J1550+054 J1415+1320 276.68–279.62 289.50–292.43 36–1530 9

2012.1.00175.S 27 Sep. 2015 J1550+054 J1415+1320 311.93–314.43 325.86–327.85 40–2414 17
2017.1.00963.S 22 May. 2018 J1337+1257 J1347+1217 341.42–345.04 353.42–357.04 14–372 5



counts
0 5 10 15 20 25 30 35



Jy beam 1
0 500 1000 1500 2000 2500 3000



11°29'44.5"


44.0"


43.5"


43.0"

















14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)


Jy beam 1
0 100 200 300 400



Jy/beam 1
10 0 10 20 30 40 50 60 70



14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)



Jy/beam 1
0 5 10 15 20







11°29'44.5"


44.0"


43.5"


43.0"











14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)



14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)



14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)



**Figure** **1.** Images of Cloverleaf at optical, sub-millimetre, and radio bands: Top Left: HST optical data where components A, B, C and D are four images of
this lensing system; the black pluses and the white pluses mark the peak positions of the model images with the parametric and the non-parametric lens model
respectively. Top Right: dust continuum data around 300 GHz where the black crosses mark the peak positions of four components in the HST data. Bottom:
Radio images of Cloverleaf at 1.5 GHz (left), 8.4 GHz (middle), and 33 GHz (right), respectively. Black crosses show the peak positions of four components in
the HST data. White lines are the contours of the ALMA dust continuum, starting from 25 _𝜎_, with steps of 30 _𝜎_ . The black ellipse presents the region we extract
fluxes of the radio jet. We use the same restoring beams of 0 _._ 25 [′′] in all radio images to generate the same source planes for spectral index analysis.



format. We use casa (ver. 6.1.0) to calibrate the data manually following standard procedures. We then image the data with task tclean
in casa, with the ‘mfs’ mode. We use a Briggs weighting with a
robust of 0.5. The final synthesised beam is 0 _._ 25 [′′] × 0 _._ 23 [′′] with a
position angle of −47 deg. We then convert the equatorial coordinate
from the B1950 epoch to the J2000 epoch with task imregrid. The
rms noise level is ∼14 _𝜇_ Jy beam [−][1] .



_2.3.2_ _VLA 33 GHz continuum_


We obtained the Ka band JVLA data from the NRAO archival system.
The project number is 13B-051 (PI: Sharon, Chelsea). This project
consists of a total of 18 execution blocks (EBs) targeting Cloverleaf.
However, three of them, taken before 22 Oct. 2013, were corrupted
and not usable due to incomplete execution. The remaining 15 EBs


MNRAS **000**, 1–13 (2023)

4 _L. Zhang et al._


were taken from 27 Oct. 2013 to 5 Jan. 2014, with the B-array
configuration. The pointing observations were performed at the Xband, and the observations were performed at the Ka band. These
observations adopted 27 antennas and took a total of ∼6.8 hours
on-source time.

The receiver covers a frequency range of 31.95–34.00 GHz, with
16 spectral line windows (128 MHz each) and two polarisations. The
total bandwidth is ∼2 GHz. The bandpass/flux calibrator and the gain
calibrator are 3C 286 and J1415+1320, respectively. The baselines
range from 16 k _𝜆_ to 1192 k _𝜆_ .
We calibrate the raw data using CASA (ver. 5.6.2-2) with the standard VLA data reduction pipeline. Then we combine all calibrated
data and abandon the spectral windows that contain the CO _𝐽_ =1→0
line emission. To save computational resources, we bin all channels
for each spectral line window. Considering a maximum offset of ∼2 [′′]

from the phase centre, the bandwidth smearing effect is negligible
((Δ _𝜈_ / _𝜈_ 0 ) × ( _𝜃_ offset / _𝜃_ HPBW ) ≤ 0 _._ 026) for Cloverleaf. Then we image
the visibility data with CASA (ver. 6.1.2.7), using task tclean. We
adopted the ‘mfs’ mode, a gridder of standard, a cell size of 0.05 [′′],
and a Briggs weighting with a robust of 1.5. The cleaned image has
a beam size of 0 _._ 26 [′′] × 0 _._ 23 [′′] with a position angle of −37 deg. The
rms noise level is ∼4 _._ 6 _𝜇_ Jy beam [−][1] .


**2.4** **E-Merlin 1.5 GHz continuum data**


The e-Merlin 1.5 GHz data was obtained from the e-Merlin archival

system. The project number is CY4215. The observation was performed on 09 Feb. 2017, with a total observing time of 13 hours. The
receiver covers a frequency range of 1.25–1.77 GHz, with eight spectral windows, of which each has 64 MHz sampled with 128 channels.
The total bandwidth is 512 MHz. The average sampling time is 2.0
seconds.

In total, seven antennas were adopted during the observations. The
bandpass and flux calibrator was 1331+305 (3C286), and the gain
calibrator was J1415+1320. Every 10 minutes, the telescope switch
between the target (7 minutes) and the gain calibrator (3 minutes). The
observations spanned ∼7.7 hours on source in total. The baselines
range from 24 k _𝜆_ to 1276 k _𝜆_ in the UV space.
The archival data has been correlated but not calibrated. We first

convert the common uvfits format to the format of ‘measurement set’

and use casa (ver. 6.1.0) to flag the data and calibrate manually. For
imaging, we adopted the ‘mfs’ mode, a gridder of standard, a cell
size of 0.05 arcsec, and a Briggs weighting scheme with a robust of
1.5. The cleaned image has a default beam size of 0 _._ 26 [′′] × 0 _._ 18 [′′] with
a position angle of 25 deg. The rms noise level is ∼47 _𝜇_ Jy beam [−][1] .
We also clean the e-Merlin data with a _nterm_ of 2 to get the spectral
index map in the lens plane (see Fig. 4).
In the spectral slope index analysis, we use a uniform restoring
beam of 0 _._ 25 [′′] × 0 _._ 25 [′′] for all radio images, to analyse these data
with the same reconstructed source plane.


**2.5** **Astrometric correction**


We notice a systematic astrometric position offset between the HST
image and those at radio/sub-mm bands. We fit the peak positions
of the four images with SAOimageDS9 (Joye & Mandel 2003) for
both the HST data and the ALMA continuum data. From these, we
get an average offset of 0.126 [′′] in the right ascension (R.A.) and
0.219 [′′] in the declination (Dec.). After we corrected the offset, the
peak positions of the images obtained from HST and ALMA (see
Fig. 1) are still not yet perfectly aligned (though the current offsets


MNRAS **000**, 1–13 (2023)



are within one pixel of the HST image), which may originate from
different emission areas and/or imperfections of the observations.
The radio band observations use the same phase calibrator
J1415+1320. Their coordinates are almost identical to each other.

The largest offset is lesser than 13 mas, which happens between the
VLA 8.4 GHz and 33 GHz data. Since the offset is smaller than the

pixel scale, we neglect it in the lens modelling below.


**3** **LENS MODELLING**


To analyse the detailed morphology of multi-wavelength images in
the source plane, we adopt the lens model software `PyAutoLens`
(AutoLens) [2] (Nightingale et al. 2021b; Nightingale & Dye 2015;
Nightingale et al. 2018). We model Cloverleaf with both parametric
and non-parametric models for the lensed source galaxy, following
the visual step-by-step guide provided in `PyAutoLens` [3] .
We take the assumption from Kneib et al. (1998) that the lens system is contributed by a single galaxy (the narrow absorption systems)
and a distant cluster both at _𝑧_ ∼ 1 _._ 7.


**3.1** **Overview of Lens Modelling Strategy**


We perform lens modelling with the following series of linked heuristic steps:


 - Fit the HST data using a simple lens model which assumes
point-source emission for the source galaxy. This provides an initial
estimate for the parametric lens mass model.

 - Take the highest likelihood results from the previous step as
the initial input to fit the ALMA 300 GHz continuum data with
another parametric mass model, using an extended source model
which follows a smoothly parameterized form of elliptical Sérsic
profile.

 - Using the mass model inferred in the previous step to initialise
the fit, fit different waveband datasets with a non-parametric source
reconstruction that uses a Voronoi mesh.


In our lens model, the redshift of the lens plane is set as 1.7 (Kneib
et al. 1998).


**3.2** **Parametric fitting—optical and sub-mm images**


_3.2.1_ _The HST optical data_


The HST optical (814 nm) image is shown in the top left panel of
Fig. 1. We use imfit to measure the sizes (FWHM) of the four
components (see Table 2), by assuming that they follow Gaussian
distributions. The fitted FWHMs of all four components are almost
identical to the FWHM of a point source (∼0 _._ 08 [′′] ), so all these images
can be treated as compact point sources without extended structures,
which is also consistent with the result that the optical emission is
dominated by a point-like AGN in the literature (Magain et al. 1988).
First, to model the HST data, we adopt an isothermal ellipsoid
with an external shear for the lens galaxy’s mass and use a “point” to
represent the source galaxy. With this optical-band lens modelling,
we can preliminary estimate the lens mass model, as well as the
source’s flux and position.


2 `[https://github.com/Jammy2211/PyAutoLens](https://github.com/Jammy2211/PyAutoLens)`
3 Both parametric and non-parametric fitting methods are provided
as Jupyter notebooks at the following link: `[https://github.com/](https://github.com/Jammy2211/autolens_likelihood_function)`
```
Jammy2211/autolens_likelihood_function

```

The four optical images of Cloverleaf point sources may suffer
from micro-lensing (Kayser et al. 1990), which may lead to a biased
result since the micro-lensing effect is not included in the strong lens
modelling. Additionally, the limited number of data (i.e., flux and
position) provided by the four lensed images only barely constrain
the lens model, resulting in considerable uncertainties. These two
limitations beg for a refined analysis at the submillimeter band, on
which we perform the lens modelling with an extended lensed arc
and use the modelling result of the optical band as a prior. The
extended lensed arc at the submillimeter wavelength is not subject to
the micro-lensing effect and its entire brightness distribution can be
used to improve the precision of the lens model.


_3.2.2_ _The ALMA 300 GHz continuum_


We next fit the ALMA 300 GHz sub-millimetre data with a more

complex parametric lens model. We adopt a power-law ellipsoid
(Tessore & Metcalf 2015) with an external shear as the lens galaxy
mass profile and model the source with an elliptical Sérsic profile.
We fix the centre of the lens mass model (from the result of the
HST data modelling) to reduce the dimensions of parametric space.
All remaining parameters from the previous model are then used to
create the initial input for this modelling. The inferred parameters of
the best-fit model at 1 − _𝜎_ confidence are shown in Table 3, including
the centre positions ( _𝑥_ & _𝑦_ ), the elliptical components ( _𝑒_ x & _𝑒_ y ), the
Einstein radius ( _𝑟_ ), the slope of the power-law profile ( _𝛼_ ), and the
elliptical components of the external shear ( _𝛾_ x & _𝛾_ y ).


**3.3** **Non-parametric fitting**


Non-parametric source reconstructions with `PyAutoLens` are performed using a Voronoi mesh, where the Voronoi cells adapt to the
source morphology. In this way, a relatively higher resolution is dedicated to its bright central regions than that in the outer region with
weaker signals. The source reconstruction is performed after an assumed parametric mass model maps coordinates from the lens plane
to the source plane with ray-tracing.


_3.3.1_ _The ALMA 300-GHz continuum_


When modelling the 300-GHz sub-millimetre data, we adopt iterative steps. To fit the non-parametric source, we first fix the parameters of the lens object according to our parametric mass model (see
Sect. 3.2.2), and then use a pixelized Voronoi grid that adapts to
the mass model’s magnification pattern, giving higher resolutions to
areas with higher magnification.
Then, we perform a fit where the source plane is reconstructed
by a brightness-weighted Voronoi (Fig. 2 left) mesh. We fit a new
mass model, a power-law ellipsoid (Tessore & Metcalf 2015) with
an external shear (shown in Table 3). With the Bayesian inference
(Dynesty) integrated within PyAutoLens, we adopt the best-fit results
and their associated errors as the lens profile (Table 3), which is
further used for the non-parametric modelling of the radio data.


_3.3.2_ _The 1.5-, 8.4-, and 33-GHz continuum_


The ALMA 300-GHz continuum image provides strong constraints
on our lensing galaxy mass model, therefore we fix the mass model
parameters to values derived from this data in order to perform nonparametric fitting at radio bands. Using the same mass model across



_Radio Jet of Cloverleaf_ 5


all wavelengths also ensures source reconstructions can be compared
in a uniform way.
For the data from VLA and e-Merlin, the source plane is reconstructed with a magnification-weighted Voronoi mesh instead of
a brightness-weighted one. This is because a magnification-based
mesh produces an identical grid of Voronoi cells across all three frequency channels, ensuring consistent sampling of the source when
calculating the spectral indices pixel by pixel to obtain a spectral indices map. The residual maps at multiple wavelengths are presented
in Appendix B. We measure the radio fluxes within two regions in
the source plane, shown as white and red ellipses in Figure 2. The
error compromises a 15% absolute flux uncertainty, a ∼ 5% error
from the uncertainty of the model by running multiple models with
all parameters randomly sampled with their probability density distributions, and a statistical error measured in emission-free regions.
The measured quantities of different components in the reconstructed
source plane are listed in Table 4.
To verify the consistency between the optical data and our
parametric/non-parametric models, we invert a simple point source
to the lens plane, with lens mass models derived from parametric
and non-parametric fitting. Both positions and fluxes of the point
source are adopted from the result first fitted with the HST data.
For both parametric and non-parametric models, the positions of the
simulated point source (Fig. 1) match well with all four images in the
HST data, within 0.5-pixel size. This indicates that our models are
reliable.


**4** **RESULTS**


**4.1** **Spatial distributions of multi-wavelength images**


As shown in Sect. 3, the HST optical images are point sources dominated by the central AGN. On the other hand, the 300 GHz image (see
Fig. 1 top right) shows that all four components are much larger than
the beam size (see Table 2), indicating that the sub-mm continuum
emission has extended structures.

The radio continuum images (shown in Fig. 1) also show resolved
extended structures. The B and D components tend to merge when
moving to the lower frequency, indicating that the source is lying
on the caustics. The other two, components A and C, both also have
spatial deviations, not only between different radio bands but also
between the images from HST and ALMA.
At 1.5 GHz band, the radio-to-submm spatial offsets are
(0 _._ 24 [′′] _,_ −0 _._ 01 [′′] ) and (−0 _._ 03 [′′] _,_ 0 _._ 24 [′′] ) in R.A. and Dec., for components A and C, respectively. All components in the images of
8.4 GHz and 33 GHz are irregular with respect to the synthesized
beam shapes at the corresponding wavelengths; thus, we do not fit
their locations with imfit.

Among the three radio bands (1.5 GHz, 8.4 GHz and 33 GHz),
the image morphologies are not identical in the source plane. The
1.5 GHz image shows almost no emission from the host galaxy, while
both 8.4 and 33 GHz radio images show detections at the same position. This suggests the multiple energy sources among different
wavelengths.


**4.2** **The discovery of a radio jet**


As shown in the reconstructed image of the source plane at 300 GHz
of Cloverleaf (Fig. 2), the cold dust emission shows an extended disklike structure of 0 _._ 115 [′′] × 0 _._ 109 [′′] in FWHM (0 _._ 946 kpc × 0 _._ 897 kpc)
rather than a point source.


MNRAS **000**, 1–13 (2023)

6 _L. Zhang et al._


Band ID Size (mas × mas) Peak S/N


814 nm A 89.4 × 85.6 173

814 nm B 84.3 × 77.5 151

814 nm C 91.3 × 86.7 106

814 nm D 82.4 × 76.6 106


300 GHz A 540 × 183 116

300 GHz B 490 × 254 122

300 GHz C 478 × 216 112

300 GHz D 426 × 180 75.8


1.5 GHz A 540 × 257 17.4

1.5 GHz B&D 443 × 121 28.4

1.5 GHz C 262 × 161 10.8


**Table 2.** Apparent sizes of four images of Cloverleaf at different wavelengths, fitted with Gaussian profiles. The sizes are described as (the FWHM of the major
axis) × (the FWHM of the minor axis).


Parameters Definition Parametric Model Non-parametric Model


_𝑥_ R.A. (hh:mm:ss) at mass centre 14:15:46.2384 [+] − _[<]_ _<_ [0] 0 _[.]_ _._ [0001] 0001 14:15:46.2325 [+] −0 _[<]_ _._ 0002 [0] _[.]_ [0001]
_𝑦_ Dec. ( [◦′] [′′] ) at mass centre 11:29:43.705 [+] − _[<]_ _<_ [0] 0 _[.]_ _._ [001] 001 11:29:43.694 [+] −0 _[<]_ _._ 002 [0] _[.]_ [001]
_𝑒_ x Elliptical component _𝑥_ −0.136 [+] − [0] 0 _[.]_ _._ [002] 002 −0.126 [+] −0 _[<]_ _._ 001 [0] _[.]_ [001]
_𝑒_ y Elliptical component _𝑦_ −0.263 [+] − [0] 0 _[.]_ _._ [002] 002 −0.270 [+] − [0] _<_ _[.]_ [003] 0 _._ 001
_𝑟_ Einstein radius ( [′′] ) 0.645 [+] − [0] 0 _[.]_ _._ [001] 001 0.636 [+] −0 _[<]_ _._ 001 [0] _[.]_ [001]
_𝛼_ Slope 1.897 [+] − [0] 0 _[.]_ _._ [003] 003 1.884 [+] −0 _[<]_ _._ 014 [0] _[.]_ [001]
_𝛾_ x Elliptical components _𝑥_ of shear 0.034 [+] − [0] 0 _[.]_ _._ [001] 001 0.043 [+] −0 _[<]_ _._ 004 [0] _[.]_ [001]
_𝛾_ y Elliptical components _𝑦_ of shear −0.054 [+] − [0] 0 _[.]_ _._ [001] 001 −0.057 [+] −0 _[<]_ _._ 003 [0] _[.]_ [001]


**Table 3.** Best fitted parameters with 1 − _𝜎_ confidence of the lens object models derived from the ALMA 300-GHz continuum data.


Component Frequency Flux Intrinsic Size Peak Position
(GHz) (µJy) ( [′′] × [′′] ) (R.A., Dec.)


host galaxy 300 2.0 ± 0.3 [± 0.3] ×10 [3] 0 _._ 12 × 0 _._ 11 (14:15:46.2378, 11:29:43.659)
host galaxy 33 4.8 ± 1.3 [± 0.7] 0 _._ 14 × 0 _._ 11 (14:15:46.2364, 11:29:43.659)
host galaxy 8.4 7 ± 2 [± 1] 0 _._ 14 × 0 _._ 095 (14:15:46.2383, 11:29:43.698)
host galaxy 1.5 26 ± 10 [± 4]              - (14:15:46.2388, 11:29:43.689)


radio jet 33 4.7 ± 1.0 [± 0.7] 0 _._ 15 × 0 _._ 086 (14:15:46.2315, 11:29:43.787)
radio jet 8.4 14 ± 3 [± 2] 0 _._ 11 × 0 _._ 049 (14:15:46.2315, 11:29:43.781)
radio jet 1.5 1.1 ± 0.2 [± 0.2] ×10 [2] 0 _._ 12 × 0 _._ 045 (14:15:46.2299, 11:29:43.781)


**Table** **4.** Measured quantities of the Cloverleaf components in the source plane at different wavelengths, where the fluxes are obtained within the ellipses in
Fig. 2, and the intrinsic sizes are described in (the FWHM of the major axis) × (the FWHM of the minor axis). The error (1- _𝜎_ ) consists of contributions from
statistical error and model uncertainty and from the absolute calibration error (15 %, shown in the squared bracket).



The peak of this dust continuum has an S/N ∼ 27, with substructures around it. The majority of the host galaxy emission is
distributed in the central region, inside the inner caustics, while a
small clump is located in the southwest to the centre. Due to the
uncertainty of the lens model, several emission clumps outside the
caustics have less fidelity.


All reconstructed radio images show extended emission to the
northwest of the dust continuum core, at a projected distance of
∼1 _._ 15 kpc (0 _._ 14 [′′] ) away from the centre of the host galaxy. The peaks
of this radio component are roughly consistent among different radio
wavebands. This indicates a single-sided radio jet launched from the
host galaxy, with a comparable size to the host galaxy at 300 GHz.
The FWHMs of this radio clump, fitted with Gaussian profiles, are
0 _._ 99 kpc × 0 _._ 37 kpc, 0 _._ 90 kpc × 0 _._ 40 kpc, and 1 _._ 23 kpc × 0 _._ 71 kpc, at
1.5 GHz, 8.4 GHz, and 33 GHz, respectively.


MNRAS **000**, 1–13 (2023)



On the other hand, in the source plane, the 1.5 GHz radio emission
from the host galaxy is almost negligible, while the 8.4 GHz and 33
GHz images show radio emission at the location of the host galaxy,
with their S/Ns of 3.5 and 3.7, respectively.


**4.3** **Spectral indices of the radio continuum**


The multiple-band radio maps allow us to probe the SEDs of both
the host galaxy and the radio jet. To evaluate the impact of the
differential magnification effect and to probe the power sources of
the radio emission, we construct SEDs derived from both the lens
plane and the source plane (see Fig. 3).
We first measure radio fluxes from regions shown in the lens
plane (Fig. 1) and the source plane (Fig. 2) for 1.5, 8.4, and 33 GHz,
respectively.

_Radio Jet of Cloverleaf_ 7



0.2


0.1


0.0


-0.1


-0.2


0.2


0.1


0.0


-0.1


-0.2



300 GHz source plane


0.2 0.1 0.0 -0.1 -0.2
R.A. ['']


8 GHz source plane


0.2 0.1 0.0 -0.1 -0.2
R.A. ['']



5000


4000


3000


2000


1000


0


200


150


100


50


0



1.5 GHz source plane


0.2 0.1 0.0 -0.1 -0.2
R.A. ['']


33 GHz source plane


0.2 0.1 0.0 -0.1 -0.2
R.A. ['']



1400


1200


1000


800


600


400


200


0


40


35


30


25


20


15


10


5


0



0.2


0.1


0.0


-0.1


-0.2


0.2


0.1


0.0


-0.1


-0.2



**Figure 2.** Reconstructed source planes of Cloverleaf at multiple bands: top left: sub-millimetre continuum at 300 GHz; top right: radio continuum at 1.5 GHz;
bottom left: radio continuum at 8.4 GHz; bottom right: radio continuum at 33 GHz. The solid black line is the inner caustics. The centre is on (14:15:46.2384 [h],
11:29:43.705) in the J2000.0 equatorial system of coordinates. The white solid ellipse and the red dashed ellipse are the areas to draw fluxes for SEDs of the
radio jet and the host galaxy, respectively.



The regions adopted to measure fluxes in the source plane are
shown in Fig. 2. In the lens plane, however, the emission from the
host galaxy and the radio jet do not show distinct spatial offsets
between each other. The radio emission of components B and D tend
to merge together, indicating that this emission component is lying
on the caustics (Appendix A), where the radio jet populates while the
host galaxy does not. Therefore, to eliminate contamination from the
host galaxy, we choose this region (shown as black ellipses in Fig. 1)
in the lens plane and construct the SED of the lensed radio structure.
On the other hand, we adopt beam-sized regions at the peaks of the
four image components to measure fluxes from the host galaxy. We
then sum up fluxes from all four components to increase the S/N.

Then we fit spectral indices with fluxes from all three radio bands,
which are shown in orange lines of Fig. 3. All SEDs can be fitted
with one single power-law profile.

We also use the e-Merlin data only, which covers 1.25 – 1.77 GHz



bandwidth, to fit a spectral index map (Fig. 4). We use a 5- _𝜎_ mask
from the e-Merlin continuum to mask the spectral index map and the
error map. The average spectral index of the merging components
B and D, which are labeled with the black dashed ellipse shown in
Fig.It represents 4, same as the black ellipse in Fig.the average spectral index 1, to beof the _𝛼_ lensed 1 [1] _._ _[.]_ 77 [25] [=][ 1] radio _[.]_ [35][ ±][ 0] jet _[.]_ [18.] at
1.5 GHz in the lens plane. All derived spectral indices for both the
host galaxy and the radio jet, are listed in Table 5.

Although the average slope of the e-Merlin spectral index map
is consistent with that obtained with _𝛼_ [1] _[.]_ [5] [1-] _[𝜎]_ [in] [the] [whole]
8 _._ 4 [within]
region, it also shows a systematic gradient of the radio slope from the
east to the west direction. This indicates that the radio jet may have
complex structures or physical processes that need higher-resolution
data to study in detail.

From the flux maps shown in Fig. 2, we fit a spectral index map
(Fig. 5, by the opposite sign convention of _𝛼_ ) using de-lensed flux


MNRAS **000**, 1–13 (2023)

8 _L. Zhang et al._


the radio jet in the lens plane



the radio jet in the source plane



500


100


50


500


100


50











1.5 8.4 33
Observing Frequency [GHz]


the host galaxy in the lens plane



50


10


5


50


10


5



1.5 8.4 33
Observing Frequency [GHz]


the host galaxy in the source plane











1.5 8.4 33
Observing Frequency [GHz]



1.5 8.4 33
Observing Frequency [GHz]



**Figure 3.** Spectral energy distributions (SEDs) of the radio jet and the host galaxy of Cloverleaf. _Top-Left_ : SED of the radio jet in the lens plane. _Top-Right_ :
SED of the radio jet in the source plane. _Bottom-Left_ : SED of the host galaxy in the lens plane. _Bottom-Right_ : SED of the host galaxy in the source plane. Radio
fluxes are measured from the regions shown in the lens plane (Fig. 1) and the source plane (Fig. 2). Orange lines show the best linear fitting result for all three
frequencies. The black dashed line in the top-left panel shows the spectral index of the radio jet in the lens plane derived from the 1.5 GHz e-Merlin data only.
All derived spectral indices are listed in Table 5. The error bars are at 1 − _𝜎_ confidence consisting of statistical error, lens model uncertainty, and absolute
calibration error (15 %).



maps in the source plane. As shown in Fig. 5, we fit power-law profiles
for all pixels at maps of 8.4 GHz, 1.5 GHz, and 33 GHz, with a mask
of S/N _>_ 3 _._ 5 at the 33 GHz source plane image. The spectral index
map shows flatter SED at the host galaxy position, while steeper SED
at the radio jet.


**5** **DISCUSSION**


**5.1** **Position offsets between sub-millimetre and radio emission**


Compared with the lensed image of Cloverleaf at ∼300 GHz, those
at radio bands have different spatial distributions, which indicates
that the emission distributions at different bands are different from

one another in the source plane, similar to the case of strongly lensed
quasar MG J0751+2716 with a radio jet (Spingola et al. 2018; Powell
et al. 2022). This can be inferred directly from the reconstructed
source planes (see Fig. 2). All reconstructed radio images contain


MNRAS **000**, 1–13 (2023)



radio structures on scales of ∼0 _._ 9 × 0 _._ 4 kpc, on the northwest part of
the inner caustics, which are absent at the sub-millimetre wavelength.


**5.2** **Possibility to be a jet in the foreground?**


One may also ask if the radio feature comes from the foreground lens
galaxy, instead of the background source galaxy. First, the multiple
components shown in all radio bands indicate that it is unlikely to
be multiple jets from the centre. Second, the spatial distributions of
all radio components are highly consistent with the scenario that the
radio structure locates on the caustics, i.e. merging between lensed
components (Appendix A). Therefore, we suggest that this radio
structure should reside in the source plane and originate from the
position on the northwest part of caustics.

1.0 1.2 1.4 1.6 1.8 2.0



_Radio Jet of Cloverleaf_ 9


error
0.0 0.2 0.4 0.6 0.8 1.0







11°29'44.5"


44.0"


43.5"


43.0"


14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)



14 [h] 15 [m] 46.30 [s] 46.25 [s] 46.20 [s]


R.A. (J2000)



**Figure 4.** Spectral index map (Left) and its error map (Right) in the lens plane at 1.5 GHz. The white and red lines are the contours of the images at 1.5 GHz
(8− _,_ 14− _,_ 20 − _𝜎_ ) and 300 GHz (50 − _𝜎_ ), respectively. The red circles represent the beam sizes. The mask we use is a 5- _𝜎_ cutoff from the e-Merlin continuum.
The black dashed line is the area we derive the spectral index at 1.5 GHz.


Component Plane _𝛼_ 8 [1] _._ _[.]_ 4 [5] _𝛼_ 33 [8] _[.]_ [4] _𝛼_ fitted _𝛼_ 1 [1] _._ _[.]_ 77 [25]


radio jet lens 1 _._ 10 ± 0 _._ 12 1 _._ 12 ± 0 _._ 16 1 _._ 11 ± 0 _._ 01 1 _._ 35 ± 0 _._ 18
radio jet source 1 _._ 17 ± 0 _._ 16 1 _._ 04 ± 0 _._ 19 1 _._ 11 ± 0 _._ 04                      host galaxy lens 0 _._ 84 ± 0 _._ 12 0 _._ 76 ± 0 _._ 16 0 _._ 80 ± 0 _._ 02                   host galaxy source 0 _._ 79 ± 0 _._ 15 0 _._ 58 ± 0 _._ 19 0 _._ 70 ± 0 _._ 06                   

**Table 5.** Spectral indices of different components in the lens plane and the source plane within 1- _𝜎_ : _𝛼_ fitted is the spectral index of the best linear fit, considering

fluxes in all three radio bands.



**5.3** **Why One-sided?**


On the other hand, the radio source only presents on one side of the
host galaxy, while the other side shows almost no signal. Depending
on the geometry, the other side of the radio jet might be too faint to
be detected due to being away from the caustics, or simply does not
exist. In any case, if the other side of the radio jet exists, it should
lead to emission populating the area between components A and C
(see Appendix A). Future deeper observations would be the key to
verifying this scenario.


**5.4** **The Power-Law Profiles of the SEDs**


As shown in Fig. 3 and Table 5, the SEDs of the radio jet in both lens
plane and source plane exhibit power-law profiles, and have similar
spectral indices, which indicates that the emission is dominated by
the synchrotron from electrons in the jet material.
On the position of the host galaxy, the SED can be also fitted with
one single power-law profile with a flatter spectral index (see Fig. 5
and Table 5) compared with the one at the position of the radio jet.
The emission (rest frequency, _𝑓_ rest ∼5-120 GHz) at this position may
have a contribution from free-free and/or dust continuum (Condon
1992), together with a contribution from the synchrotron emitted
from the relativistic electron accelerated by supernovae remnants.



**5.5** **AGN Feedback of Cloverleaf**


Based on the broad absorption line profile (Hazard et al. 1984; Magain et al. 1988) and the HST optical images (Fig. 1) of this quasar,
the wind/radiation feedback could take place in this galaxy.
On the other hand, this radio jet/structure is located at a projected
distance of ∼1 _._ 15 kpc (0 _._ 14 [′′] ) from the galaxy centre, with a size
similar to that of the host galaxy at 33 GHz. These are consistent
with radio lobe features found in massive radio galaxies (Fabian
2012), however, Cloverleaf seems to have a lower galaxy mass than
those massive galaxies (Solomon et al. 2003). The kinetic energy
residing in the jet could severely heat up the gas and drive strong
feedback to the star formation in Cloverleaf.


Chartas et al. (2004) constrained the mass of the SMBH in the
Cloverleaf quasar by the microlensed image A (the one located at the
south in the four images shown in Fig. 1) at X-ray band. They also
adopted the luminosity from Granato et al. (1996)’s dust-enshrouded
AGN models. Then the Eddington ratio of this AGN is found to be
∼ 0 _._ 1, assuming the magnification of the AGN to be 11 (Venturini &
Solomon 2003). The Eddington ratio of 0.1 indicates that the AGN
is not radiating close to the Eddington limit, yet is still a powerful

quasar.
Therefore, given its strong ongoing starburst, likely driven by the
interaction with a neighbouring gas-rich galaxy (Stacey & Arrigoni


MNRAS **000**, 1–13 (2023)

10 _L. Zhang et al._


spectral index map


0.2


0.1


0.0


-0.1


-0.2


0.2 0.1 0.0 -0.1 -0.2
R.A. ['']



1.2


1.0


0.8


0.6



**Figure** **5.** Spectral index map (derived from the reconstructed images at
1.5-, 8.4-, and 33- GHz) in the source plane: The black solid line is the
inner caustics. The centre is on (14:15:46.2384 _[ℎ]_, 11:29:43.705) in the J2000
equatorial system of coordinates. The white solid ellipse and the red dashed
ellipse mark the positions of the radio jet and the host galaxy, respectively.


Battaia 2022), together with the broad absorption line and the newly
discovered radio jet, we suggest that the AGN feedback in Cloverleaf
consists of coexistent contributions from both radiation-driven wind

and AGN-launched jet. High angular resolution observations of both
radio continuum and molecular gas tracers in the future, which help
resolve the jet structure and gas kinematics, could throw light on the
co-existence of both mechanisms of AGN feedback.


**6** **CONCLUSION**


With high angular resolution photometric data at optical, sub-mm,
and radio wavelengths, we reconstructed multi-band source images
of the gravitational lensed Cloverleaf QSO, with both parametric
and non-parametric modelling. From different emission locations,
we discovered a single-sided radio jet, with a size of ∼1 kpc, located
at projected ∼1.2 kpc to the northwest of Cloverleaf. The co-existence
of a radio jet and broad absorption line indicates that the Cloverleaf
quasar likely feedbacks its host galaxy with both AGN wind and radio
jet. This provides a unique case for the galaxy-SMBH co-evolution
studies at high redshifts.


**ACKNOWLEDGEMENTS**


Based on observations made with the NASA/ESA Hubble Space
Telescope, and obtained from the Hubble Legacy Archive, which
is a collaboration between the Space Telescope Science Institute
(STScI/NASA), the Space Telescope European Coordinating Facility (ST-ECF/ESAC/ESA) and the Canadian Astronomy Data Centre
(CADC/NRC/CSA). LZ acknowledges the referee for pointing out


MNRAS **000**, 1–13 (2023)



the mistake in data reduction and for kind and helpful suggestions,
which heavily polish this study. LZ appreciates Yunwei Deng and
Chengjiang Yin for their technical helps. ZYZ and LZ acknowledge
support of the National Natural Science Foundation of China (NSFC)
under grants No. 12041305, 12173016. ZYZ and LZ acknowledge the
Program for Innovative Talents, Entrepreneur in Jiangsu. ZYZ and
LZ acknowledge the science research grants from the China Manned
Space Project with NO.CMS-CSST-2021-A08. CY acknowledges
support from ERC Advanced Grant 789410. DDX acknowledges
the NSFC Grant 12073013. This work is supported by the China
Manned Space Project (No. CMS-CSST-2021-A07). RL acknowledges the support of National Nature Science Foundation of China
(Nos 11988101,11773032,12022306), the support from the Ministry of Science and Technology of China (Nos. 2020SKA0110100),
the science research grants from the China Manned Space Project
(Nos. CMS-CSST-2021-B01,CMS-CSST-2021-A01), CAS Project
for Young Scientists in Basic Research(No. YSBR-062). Z.-C. Z.
is supported by the National Natural Science Foundation of China
(Grant No. 12233002).
This work used the following software: Autolens(Nightingale &
Dye 2015; Nightingale et al. 2018, 2021b), CASA (McMullin et al.
2007), SAOimageDS9 (Joye & Mandel 2003), astropy (Astropy Collaboration et al. 2013; Price-Whelan et al. 2018), dynesty (Speagle
2020), corner (Foreman-Mackey 2016), emcee (Foreman-Mackey
et al. 2013), matplotlib (Hunter 2007), numpy (van der Walt et al.
2011), pyautofit(Nightingale et al. 2021a), pylops(Ravasi & Vasconcelos 2020), python (Van Rossum & Drake 2009), scipy (Virtanen
et al. 2020)


**DATA AVAILABILITY**


All data adopted in this work are publicly available in corresponding
data archival systems of HST, ALMA, VLA, and e-Merlin.


**REFERENCES**


Alexander D. M., Swinbank A. M., Smail I., McDermid R., Nesvadba N. P. H.,

[2010, MNRAS, 402, 2211](http://dx.doi.org/10.1111/j.1365-2966.2009.16046.x)
[Angonin M. C., Remy M., Surdej J., Vanderriest C., 1990, A&A, 233, L5](https://ui.adsabs.harvard.edu/abs/1990A&A...233L...5A)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Barvainis R., Maloney P., Antonucci R., Alloin D., 1997, ApJ, 484, 695](http://dx.doi.org/10.1086/304382)
Bertin E., Mellier Y., Radovich M., Missonnier G., Didelon P., Morin B.,
2002, in Bohlender D. A., Durand D., Handley T. H., eds, Astronomical
Society of the Pacific Conference Series Vol. 281, Astronomical Data
Analysis Software and Systems XI. p. 228
Cano-Díaz M., Maiolino R., Marconi A., Netzer H., Shemmer O., Cresci G.,

[2012, A&A, 537, L8](http://dx.doi.org/10.1051/0004-6361/201118358)

[Cattaneo A., Best P. N., 2009, MNRAS, 395, 518](http://dx.doi.org/10.1111/j.1365-2966.2009.14557.x)

[Cattaneo A., et al., 2009, Nature, 460, 213](http://dx.doi.org/10.1038/nature08135)
[Chantry V., Magain P., 2007, A&A, 470, 467](http://dx.doi.org/10.1051/0004-6361:20066839)
[Chartas G., Eracleous M., Agol E., Gallagher S. C., 2004, ApJ, 606, 78](http://dx.doi.org/10.1086/382743)
Churazov E., Sazonov S., Sunyaev R., Forman W., Jones C., Böhringer H.,
[2005, MNRAS, 363, L91](http://dx.doi.org/10.1111/j.1745-3933.2005.00093.x)

[Condon J. J., 1992, ARA&A, 30, 575](http://dx.doi.org/10.1146/annurev.aa.30.090192.003043)
[Cutri R. M., et al., 2003, VizieR Online Data Catalog, p. II/246](https://ui.adsabs.harvard.edu/abs/2003yCat.2246....0C)
Ding X., Silverman J. D., Onoue M., 2022, arXiv e-prints, [p.](https://ui.adsabs.harvard.edu/abs/2022arXiv220903359D)
[arXiv:2209.03359](https://ui.adsabs.harvard.edu/abs/2022arXiv220903359D)

[Dunn J. P., et al., 2010, ApJ, 709, 611](http://dx.doi.org/10.1088/0004-637X/709/2/611)
[Fabian A. C., 2012, ARA&A, 50, 455](http://dx.doi.org/10.1146/annurev-astro-081811-125521)
[Farrah D., et al., 2012, ApJ, 745, 178](http://dx.doi.org/10.1088/0004-637X/745/2/178)
[Ferrarese L., Ford H., 2005, Space Sci. Rev., 116, 523](http://dx.doi.org/10.1007/s11214-005-3947-6)
[Foreman-Mackey D., 2016, The J. Open Source Softw., 1, 24](http://dx.doi.org/10.21105/joss.00024)

[Foreman-Mackey D., Hogg D. W., Lang D., Goodman J., 2013, Publ. Astron.](http://dx.doi.org/10.1086/670067)
[Soc. Pac., 125, 306](http://dx.doi.org/10.1086/670067)

[Gopal-Krishna Wiita P. J., 2001, ApJ, 560, L115](http://dx.doi.org/10.1086/324310)
[Granato G. L., Danese L., Franceschini A., 1996, ApJ, 460, L11](http://dx.doi.org/10.1086/309977)
[Hazard C., Morton D. C., Terlevich R., McMahon R., 1984, ApJ, 282, 33](http://dx.doi.org/10.1086/162174)
[Hunter J. D., 2007, Comput Sci Eng, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
Joye W. A., Mandel E., 2003, in Payne H. E., Jedrzejewski R. I., Hook R. N.,
eds, Astronomical Society of the Pacific Conference Series Vol. 295,
Astronomical Data Analysis Software and Systems XII. p. 489
Kayser R., Surdej J., Condon J. J., Kellermann K. I., Magain P., Remy M.,
[Smette A., 1990, ApJ, 364, 15](http://dx.doi.org/10.1086/169382)
Kneib J. P., Alloin D., Mellier Y., Guilloteau S., Barvainis R., Antonucci R.,

[1998, A&A, 329, 827](https://ui.adsabs.harvard.edu/abs/1998A&A...329..827K)

[Kormendy J., Ho L. C., 2013, ARA&A, 51, 511](http://dx.doi.org/10.1146/annurev-astro-082708-101811)
Lanzetta K. M., Yahata N., Pascarelle S., Chen H.-W., Fernández-Soto A.,
[2002, ApJ, 570, 492](http://dx.doi.org/10.1086/339774)
Lawrence C. R., 1996, in Kochanek C. S., Hewitt J. N., eds, International
Astronomical Union Symposia Vol. 173, Astrophysical Applications of
Gravitational Lensing. p. 299
[Li J., et al., 2021, ApJ, 918, 22](http://dx.doi.org/10.3847/1538-4357/ac06a8)
[Magain P., Surdej J., Swings J. P., Borgeest U., Kayser R., 1988, Nature, 334,](http://dx.doi.org/10.1038/334325a0)
[325](https://ui.adsabs.harvard.edu/abs/1988Natur.334..325M)

McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[McNamara B. R., Nulsen P. E. J., 2007, ARA&A, 45, 117](http://dx.doi.org/10.1146/annurev.astro.45.051806.110625)

[Moe M., Arav N., Bautista M. A., Korista K. T., 2009, ApJ, 706, 525](http://dx.doi.org/10.1088/0004-637X/706/1/525)
Nesvadba N. P. H., Lehnert M. D., De Breuck C., Gilbert A. M., van Breugel
[W., 2008, A&A, 491, 407](http://dx.doi.org/10.1051/0004-6361:200810346)

Nesvadba N. P. H., Polletta M., Lehnert M. D., Bergeron J., De Breuck C.,
[Lagache G., Omont A., 2011, MNRAS, 415, 2359](http://dx.doi.org/10.1111/j.1365-2966.2011.18862.x)
[Nightingale J. W., Dye S., 2015, MNRAS, 452, 2940](http://dx.doi.org/10.1093/mnras/stv1455)
[Nightingale J. W., Dye S., Massey R. J., 2018, MNRAS, 478, 4738](http://dx.doi.org/10.1093/mnras/sty1264)
[Nightingale J. W., Hayes R. G., Griffiths M., 2021a, J. Open Source Softw.,](http://dx.doi.org/10.21105/joss.02550)
6, 2550

[Nightingale J. W., et al., 2021b, J. Open Source Softw., 6, 2825](http://dx.doi.org/10.21105/joss.02825)
[Planck Collaboration et al., 2020, A&A, 641, A6](http://dx.doi.org/10.1051/0004-6361/201833910)

Powell D. M., Vegetti S., McKean J. P., Spingola C., Stacey H. R., Fassnacht
[C. D., 2022, MNRAS, 516, 1808](http://dx.doi.org/10.1093/mnras/stac2350)

[Price-Whelan A. M., et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)

[Prochaska J. X., Hennawi J. F., 2009, ApJ, 690, 1558](http://dx.doi.org/10.1088/0004-637X/690/2/1558)
[Ravasi M., Vasconcelos I., 2020, SoftwareX, 11, 100361](http://dx.doi.org/https://doi.org/10.1016/j.softx.2019.100361)

[Saez C., Chartas G., Brandt W. N., 2009, ApJ, 697, 194](http://dx.doi.org/10.1088/0004-637X/697/1/194)
[Schmidt M., Green R. F., 1983, ApJ, 269, 352](http://dx.doi.org/10.1086/161048)
[Shi F., Li Z., Yuan F., Zhu B., 2021, Nature Astronomy, 5, 928](http://dx.doi.org/10.1038/s41550-021-01394-0)
[Silverman J. D., et al., 2019, ApJ, 887, L5](http://dx.doi.org/10.3847/2041-8213/ab5851)
[Solomon P., Vanden Bout P., Carilli C., Guelin M., 2003, Nature, 426, 636](http://dx.doi.org/10.1038/nature02149)

[Speagle J. S., 2020, MNRAS, 493, 3132](http://dx.doi.org/10.1093/mnras/staa278)
Spingola C., McKean J. P., Auger M. W., Fassnacht C. D., Koopmans L. V. E.,
[Lagattuta D. J., Vegetti S., 2018, MNRAS, 478, 4816](http://dx.doi.org/10.1093/mnras/sty1326)
[Springel V., Di Matteo T., Hernquist L., 2005, MNRAS, 361, 776](http://dx.doi.org/10.1111/j.1365-2966.2005.09238.x)
[Stacey H. R., Arrigoni Battaia F., 2022, MNRAS, 517, L11](http://dx.doi.org/10.1093/mnrasl/slac102)
[Tessore N., Metcalf R. B., 2015, A&A, 580, A79](http://dx.doi.org/10.1051/0004-6361/201526773)

[Turnshek D. A., Foltz C. B., Grillmair C. J., Weymann R. J., 1988, ApJ, 325,](http://dx.doi.org/10.1086/166036)
[651](https://ui.adsabs.harvard.edu/abs/1988ApJ...325..651T)

[Turnshek D. A., Lupie O. L., Rao S. M., Espey B. R., Sirola C. J., 1997, ApJ,](http://dx.doi.org/10.1086/304395)

[485, 100](https://ui.adsabs.harvard.edu/abs/1997ApJ...485..100T)

Van Rossum G., Drake F. L., 2009, Python 3 Reference Manual. CreateSpace,
Scotts Valley, CA
[Venturini S., Solomon P. M., 2003, ApJ, 590, 740](http://dx.doi.org/10.1086/375050)
[Virtanen P., et al., 2020, Nature Methods, 17, 261](http://dx.doi.org/10.1038/s41592-019-0686-2)

[Weiß A., Henkel C., Downes D., Walter F., 2003, A&A, 409, L41](http://dx.doi.org/10.1051/0004-6361:20031337)

Wolf C., Wisotzki L., Borch A., Dye S., Kleinheinrich M., Meisenheimer K.,
[2003, A&A, 408, 499](http://dx.doi.org/10.1051/0004-6361:20030990)

[van der Walt S., Colbert S. C., Varoquaux G., 2011, Comput Sci Eng, 13, 22](http://dx.doi.org/10.1109/MCSE.2011.37)



_Radio Jet of Cloverleaf_ 11


**APPENDIX A:** **MOCK DATA**


In Figure A1, we present the mock data of the lensing system of
Cloverleaf, to simulate the response of a background source with a
Sérsic profile. The lens model is the same as the one in our nonparametric model. The source is a Sérsic ellipsoid moving from the
northwest part to the southeast part of the inner caustics in the source
plane, and its centre is marked with red crosses as moving.


MNRAS **000**, 1–13 (2023)

12 _L. Zhang et al._


1.0


0.5


0.0


-0.5


-1.0



1.0


0.5


0.0


-0.5


-1.0





1.0 0.5 0.0 -0.5 -1.0



1.0 0.5 0.0 -0.5 -1.0


1.0 0.5 0.0 -0.5 -1.0


1.0 0.5 0.0 -0.5 -1.0
R.A. ['']





1.0


0.5


0.0


-0.5


-1.0


1.0


0.5


0.0


-0.5


-1.0



1.0 0.5 0.0 -0.5 -1.0


1.0 0.5 0.0 -0.5 -1.0


1.0 0.5 0.0 -0.5 -1.0
R.A. ['']





1.0


0.5


0.0


-0.5


-1.0

















1.0


0.5


0.0


-0.5


-1.0


1.0


0.5


0.0


-0.5


-1.0


1.0


0.5


0.0


-0.5


-1.0






1.0 0.5 0.0 -0.5 -1.0
R.A. ['']



**Figure A1.** Mock data of this lensing system: The lens model is the same as the one in our non-parametric model. The source is a Sérsic ellipsoid moving from
the northwest part to the southeast part of the inner caustics in the source plane, and its centre is marked with red crosses as moving. The solid black line and the
red solid line are the outer and the inner critical curve (which is incorrect due to the numerical issue and should be a point) in the lens plane respectively. The
solid black line (diamond-shaped) in the source plane is the inner caustics.


MNRAS **000**, 1–13 (2023)

**APPENDIX B:** **RESIDUAL**


In Figure B1, we present the residual maps of our lensing models of
the 300 GHz, 1.5 GHz, 8.4 GHz, and 33 GHz data.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



_Radio Jet of Cloverleaf_ 13


MNRAS **000**, 1–13 (2023)

14 _L. Zhang et al._


1.0


0.5


0.0


-0.5


-1.0



300 GHz residual map



1.5 GHz residual map


1.0 0.5 0.0 -0.5 -1.0
R.A. ['']


33 GHz residual map

|Col1|Col2|1<br>5<br>0|
|---|---|---|
||||
||||



1.0 0.5 0.0 -0.5 -1.0
R.A. ['']



150


100


50


100


5


10



1.0


0.5


0.0


-0.5


-1.0


1.0


0.5


0.0


-0.5


-1.0



400


200


200


400


600


10


20



1.0


0.5


0.0


-0.5


-1.0



1.0 0.5 0.0 -0.5 -1.0
R.A. ['']


8 GHz residual map

|Col1|Col2|2<br>1<br>0|
|---|---|---|
||||
||||



1.0 0.5 0.0 -0.5 -1.0
R.A. ['']



**Figure B1.** Residual maps of non-parametric models at 300 GHz, 1.5 GHz, 8.4 GHz, and 33 GHz: The red dot circle is the mask. The solid black line and the
red solid line are the outer critical curve and the inner critical curve (which is incorrect due to the numerical issue and should be a point) respectively.


MNRAS **000**, 1–13 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0.26'' x 0.20'' (PA -31 deg)",
  "failed_quote": "The synthesised image (see Fig. 1 top right) has a beam size of 0.26'' x 0.20'' and a position angle of -31 deg."
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "35 \\muJy beam^-1",
  "failed_quote": "The noise level is 35 \\muJy beam^-1, estimated from the emission-free area in the field."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "8.4 GHz (A-configuration, projects AS357 and AC243) and 33 GHz Ka-band (B-array, project 13B-051) continuum archival data.",
  "failed_quote": "The Very Large Array (VLA) 8.4 GHz data were obtained from the NRAO archive. This data have been originally presented by Kayser et al. (1990). The project IDs are AS357 and AC243"
 },
 {
  "path": "processing.imaging.line_free_channels.evidence[1]",
  "value": "Omit frequency range of CO J=11-10 (ALMA 300 GHz) and abandon spectral windows containing CO J=1-0 (VLA 33 GHz)",
  "failed_quote": "Then we combine all calibrated data and abandon the spectral windows that contain the CO J=1->0 line emission."
 },
 {
  "path": "processing.imaging.smoothing.evidence[0]",
  "value": "Uniform restoring beam of 0.25'' x 0.25'' for all radio images in spectral index analysis",
  "failed_quote": "In the spectral slope index analysis, we use a uniform restoring beam of 0.25'' x 0.25'' for all radio images, to analyse these data with the same reconstructed source plane."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "0.26'' x 0.20'', PA -31 deg (ALMA 300 GHz); 0.25'' x 0.23'', PA -47 deg (VLA 8.4 GHz); 0.26'' x 0.23'', PA -37 deg (VLA 33 GHz); 0.26'' x 0.18'', PA 25 deg (e-Merlin 1.5 GHz)",
  "failed_quote": "The synthesised image (see Fig. 1 top right) has a beam size of 0.26'' x 0.20'' and a position angle of -31 deg."
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "0.26'' x 0.20'', PA -31 deg (ALMA 300 GHz); 0.25'' x 0.23'', PA -47 deg (VLA 8.4 GHz); 0.26'' x 0.23'', PA -37 deg (VLA 33 GHz); 0.26'' x 0.18'', PA 25 deg (e-Merlin 1.5 GHz)",
  "failed_quote": "The final synthesised beam is 0.25'' x 0.23'' with a position angle of -47 deg."
 },
 {
  "path": "processing.imaging.final_beam.evidence[2]",
  "value": "0.26'' x 0.20'', PA -31 deg (ALMA 300 GHz); 0.25'' x 0.23'', PA -47 deg (VLA 8.4 GHz); 0.26'' x 0.23'', PA -37 deg (VLA 33 GHz); 0.26'' x 0.18'', PA 25 deg (e-Merlin 1.5 GHz)",
  "failed_quote": "The cleaned image has a beam size of 0.26'' x 0.23'' with a position angle of -37 deg."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "35 \\muJy beam^-1 (ALMA 300 GHz); ~14 \\muJy beam^-1 (VLA 8.4 GHz); ~4.6 \\muJy beam^-1 (VLA 33 GHz); ~47 \\muJy beam^-1 (e-Merlin 1.5 GHz)",
  "failed_quote": "The noise level is 35 \\muJy beam^-1, estimated from the emission-free area in the field."
 },
 {
  "path": "processing.imaging.final_rms.evidence[1]",
  "value": "35 \\muJy beam^-1 (ALMA 300 GHz); ~14 \\muJy beam^-1 (VLA 8.4 GHz); ~4.6 \\muJy beam^-1 (VLA 33 GHz); ~47 \\muJy beam^-1 (e-Merlin 1.5 GHz)",
  "failed_quote": "The rms noise level is ~14 \\muJy beam^-1."
 },
 {
  "path": "processing.imaging.final_rms.evidence[2]",
  "value": "35 \\muJy beam^-1 (ALMA 300 GHz); ~14 \\muJy beam^-1 (VLA 8.4 GHz); ~4.6 \\muJy beam^-1 (VLA 33 GHz); ~47 \\muJy beam^-1 (e-Merlin 1.5 GHz)",
  "failed_quote": "The rms noise level is ~4.6 \\muJy beam^-1."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Visual step-by-step guide and Jupyter notebooks for parametric and non-parametric lens modelling",
  "failed_quote": "We model Cloverleaf with both parametric and non-parametric models for the lensed source galaxy, following the visual step-by-step guide provided in PyAutoLens."
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "Uniform restoring beam of 0.25'' x 0.25'' for radio images in spectral index analysis",
  "failed_quote": "In the spectral slope index analysis, we use a uniform restoring beam of 0.25'' x 0.25'' for all radio images, to analyse these data with the same reconstructed source plane."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[1]",
  "value": "Bayesian inference with Dynesty in PyAutoLens; Gaussian profile fitting to measure FWHMs of source-plane components",
  "failed_quote": "The FWHMs of this radio clump, fitted with Gaussian profiles, are 0.99 kpc x 0.37 kpc, 0.90 kpc x 0.40 kpc, and 1.23 kpc x 0.71 kpc, at 1.5 GHz, 8.4 GHz, and 33 GHz, respectively."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Compare spectral indices between lens plane and source plane and against the in-band e-Merlin 1.25-1.77 GHz spectral index map.",
  "failed_quote": "Although the average slope of the e-Merlin spectral index map is consistent with that obtained with \\alpha_8.4^1.5 within 1-\\sigma in the whole region, it also shows a systematic gradient of the radio slope from the east to the west direction."
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "Importing archival VLA 8.4 GHz data and converting to uvfits format.",
  "failed_quote": "The data was first imported to AIPS and converted to the uvfits format."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Parametric and non-parametric strong gravitational lens mass modelling and Voronoi mesh source-plane reconstructions.",
  "failed_quote": "To analyse the detailed morphology of multi-wavelength images in the source plane, we adopt the lens model software PyAutoLens (AutoLens) (Nightingale et al. 2021b; Nightingale & Dye 2015; Nightingale et al. 2018)."
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Host galaxy source-plane intrinsic size (FWHM) at 300 GHz = 0.115 x 0.109 (0.946 x 0.897 kpc; 0.12 x 0.11 in Table 4) arcsec x arcsec",
  "failed_quote": "As shown in the reconstructed image of the source plane at 300 GHz of Cloverleaf (Fig. 2), the cold dust emission shows an extended disk-like structure of 0.115'' x 0.109'' in FWHM (0.946 kpc x 0.897 kpc) rather than a point source."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Radio jet source-plane intrinsic size (FWHM) at 1.5 GHz = 0.99 x 0.37 (0.12'' x 0.045'') kpc x kpc",
  "failed_quote": "The FWHMs of this radio clump, fitted with Gaussian profiles, are 0.99 kpc x 0.37 kpc, 0.90 kpc x 0.40 kpc, and 1.23 kpc x 0.71 kpc, at 1.5 GHz, 8.4 GHz, and 33 GHz, respectively."
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Radio jet source-plane intrinsic size (FWHM) at 8.4 GHz = 0.90 x 0.40 (0.11'' x 0.049'') kpc x kpc",
  "failed_quote": "The FWHMs of this radio clump, fitted with Gaussian profiles, are 0.99 kpc x 0.37 kpc, 0.90 kpc x 0.40 kpc, and 1.23 kpc x 0.71 kpc, at 1.5 GHz, 8.4 GHz, and 33 GHz, respectively."
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Radio jet source-plane intrinsic size (FWHM) at 33 GHz = 1.23 x 0.71 (0.15'' x 0.086'') kpc x kpc",
  "failed_quote": "The FWHMs of this radio clump, fitted with Gaussian profiles, are 0.99 kpc x 0.37 kpc, 0.90 kpc x 0.40 kpc, and 1.23 kpc x 0.71 kpc, at 1.5 GHz, 8.4 GHz, and 33 GHz, respectively."
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "Radio jet in-band spectral index \\alpha_1.77^1.25 (lens plane, e-Merlin) = 1.35 dimensionless",
  "failed_quote": "The average spectral index of the merging components B and D, which are labeled with the black dashed ellipse shown in Fig. 4, same as the black ellipse in Fig. 1, to be \\alpha_1.77^1.25 = 1.35 \\pm 0.18."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "The co-existence of broad absorption line winds and the newly discovered radio jet suggests AGN feedback in the Cloverleaf quasar operates via both radiation-driven wind and kinetic jet modes.",
  "failed_quote": "Therefore, given its strong ongoing starburst, likely driven by the interaction with a neighbouring gas-rich galaxy (Stacey & Arrigoni Battaia 2022), together with the broad absorption line and the newly discovered radio jet, we suggest that the AGN feedback in Cloverleaf consists of coexistent contributions from both radiation-driven wind and AGN-launched jet."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "AGN feedback in the Cloverleaf quasar likely involves co-existent contributions from both radiation-driven winds and an AGN-launched radio jet.",
  "failed_quote": "Therefore, given its strong ongoing starburst, likely driven by the interaction with a neighbouring gas-rich galaxy (Stacey & Arrigoni Battaia 2022), together with the broad absorption line and the newly discovered radio jet, we suggest that the AGN feedback in Cloverleaf consists of coexistent contributions from both radiation-driven wind and AGN-launched jet."
 }
]
```
