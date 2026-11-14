# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.523.4970N\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–13 (2023) Preprint 28 June 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **Resolving the Binary Components of the Outbursting Protostar HBC 494** **with ALMA**


Pedro Henrique Nogueira [1] _[,]_ [2] _[★]_, Alice Zurlo [1] _[,]_ [2], Sebastián Pérez [2] _[,]_ [3] _[,]_ [4], Camilo González-Ruilova [1] _[,]_ [2] _[,]_ [5],
Lucas A. Cieza [1] _[,]_ [2], Antonio Hales [6] _[,]_ [7], Trisha Bhowmik [1] _[,]_ [2] _[,]_ [3], Dary A. Ruíz-Rodríguez [7],
David A. Principe [8], Gregory J. Herczeg [9], Jonathan P. Williams [10], Jorge Cuadra [11] _[,]_ [13],
Matías Montesinos [12] _[,]_ [13], Nicolás Cuello [14], Prachi Chavan [1] _[,]_ [2], Simon Casassus [2] _[,]_ [15] _[,]_ [16] _[,]_ [17],
Zhaohuan Zhu [18] _[,]_ [19], Felipe G. Goicovic [20]


1 _Instituto de Estudios Astrofísicos, Facultad de Ingeniería y Ciencias, Universidad Diego Portales, Av. Ejército Libertador 441, Santiago, Chile_
2 _Millennium Nucleus on Young Exoplanets and their Moons (YEMS)_
3 _Departamento de Física, Universidad de Santiago de Chile, Av. Victor Jara 3659, Santiago, Chile_
4 _Center for Interdisciplinary Research in Astrophysics and Space Exploration (CIRAS), Universidad de Santiago de Chile, Santiago, Chile_
5 _European Southern Observatory, Alonso de Cordova 3107, Casilla 19001, Vitacura, Santiago, Chile_
6 _Joint ALMA Observatory, Avenida Alonso de Córdova 3107, Vitacura 7630355, Santiago, Chile_
7 _National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903-2475, USA_
8 _Massachusetts Institute of Technology, Kavli Institute for Astrophysics and Space Research, Cambridge, MA, 02138, USA_
9 _Kavli Institute for Astronomy and Astrophysics, Peking University, Yiheyuan Lu 5, Haidian Qu, 100871 Beĳing, People’s Republic of China_
10 _Institute for Astronomy, University of Hawaii at Manoa, Woodlawn Drive, Honolulu, HI, 96822, USA_
11 _Departamento de Ciencias, Facultad de Artes Liberales, Universidad Adolfo Ibáñez, Av. Padre Hurtado 750, Viña del Mar, Chile_
12 _Escuela de Ciencias, Universidad Viña del Mar, Viña del Mar, 2572007, Chile_
13 _Núcleo Milenio de Formación Planetaria - NPF, Universidad de Valparaíso, Av. Gran Bretaña 1111, Valparaíso, Chile_
14 _Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France_
15 _Departamento de Astronomía, Universidad de Chile, Casilla 36-D, Santiago, Chile_
16 _Facultad de Ingeniería y Ciencias, Universidad Adolfo Ibáñez, Av. Diagonal las Torres 2640, Peñalolén, Santiago, Chile_
17 _Data Observatory Foundation, Chile_
18 _Department of Physics and Astronomy, University of Nevada, Las Vegas, 4505 S. Maryland Parkway, Las Vegas, NV 89154, USA_
19 _Nevada Center for Astrophysics, University of Nevada, Las Vegas, 4505 South Maryland Parkway, Las Vegas, NV 89154, USA_
20 _Zentrum für Astronomie der Universität Heidelberg, Institut für Theoretische Astrophysik, Albert-Ueberle-Straße 2, 69120 Heidelberg, Germany_


Accepted 2023 May 24; Received 2023 May 19; in original form 2023 January 25


**ABSTRACT**

Episodic accretion is a low-mass pre-main sequence phenomenon characterized by sudden outbursts of enhanced accretion.
These objects are classified into two: protostars with elevated levels of accretion that lasts for decades or more, called FUors,
and protostars with shorter and repetitive bursts, called EXors. HBC 494 is a FUor object embedded in the Orion Molecular
Cloud. Earlier Atacama Large (sub-)Millimeter Array (ALMA) continuum observations showed an asymmetry in the disk at 0 [′′] _._ 2
resolution. Here, we present follow-up observations at ∼0 [′′] _._ 03, resolving the system into two components: HBC 494 N (primary)
and HBC 494 S (secondary). No circumbinary disk was detected. Both disks are resolved with a projected separation of ∼ 0 [′′] _._ 18
(75 au). Their projected dimensions are 84±1.8 × 66.9±1.5 mas for HBC 494 N and 64.6±2.5 × 46.0±1.9 mas for HBC 494 S.
The disks are almost aligned and with similar inclinations. The observations show that the primary is ∼5 times brighter/more
massive and ∼2 times bigger than the secondary. We notice that the northern component has a similar mass to the FUors, while
the southern has to EXors. The HBC 494 disks show individual sizes that are smaller than single eruptive YSOs. In this work,
we also report [12] CO, [13] CO, and C [18] O molecular line observations. At large scale, the [12] CO emission shows bipolar outflows,
while the [13] CO and C [18] O maps show a rotating and infalling envelope around the system. At a smaller scale, the [12] CO and
13 CO moment zero maps show cavities within the continuum disks’ area, which may indicate continuum over-subtraction or
slow-moving jets and chemical destruction along the line-of-sight.


**Key words:** stars: protostars – protoplanetary disks – radio continuum: planetary systems – accretion, accretion disks – radio
lines: planetary systems – ISM: jets and outflows


**1** **INTRODUCTION**



_★_ E-mail: pedro.soares@mail.udp.cl During their evolution, young stellar objects (YSOs) dissipate their

© 2023 The Authors envelopes while feeding their developing protostars through accre

2 _P. H. Nogueira et al._


tion via a disk. However, YSOs are underluminous compared to the
luminosity and accretion rates expected from steady disk accretion.
This discrepancy has been established as the “luminosity problem"
(Kenyon et al. 1990; Evans et al. 2009). One potential solution to the
luminosity problem is that young stars undergo episodes of high accretion interspersed by quiescent phases. During the episodes of enhanced accretion, large amounts of material are accreted very quickly
(e.g., Dunham & Vorobyov 2012). Such phenomena have been observed in low-mass pre-main sequence stars like FU Orionis and EX
Lupi, the prototypes of the two subclasses that display the episodic
accretion phenomenon.


FU Orionis type stars, a.k.a. FUors, are pre-main sequence lowmass stars that show variability in both luminosity and spectral type
due to variation in the accretion mass rate, on a short timescale
(Herbig 1966). Their optical brightness can dramatically increase due
to enhanced mass accretion by more than five magnitudes over a few
months. After this “outburst”, FUors can remain in this active state
for decades. This occurrence is considered episodic and suspected
to be common at the early stages of star formation. Throughout an
outburst, the star can accrete ∼ 0.01 M ⊙ of material, roughly the mass
of a typical T-Tauri disk (Andrews & Williams 2005). The bolometric
luminosity of the FUors during the outburst is 100–300 _𝐿_ ⊙ and the
accretion rate is between 10 [−][6] and 10 [−][4] M ⊙ yr [−][1] (Audard et al.
2014). EX Lupi type stars, a.k.a. EXors, are a scaled-down version
of the FUors, with shorter and less intense outbursts (Herbig 2007).
The EXors enhanced accretion stage can last months to years, with
accretion rates ranging from 10 [−][7] to 10 [−][6] M ⊙ yr [−][1], which are
the order up to 5 magnitudes brighter than quiescent periods. The
episodic recurrence is also on the order of years (e.g., Jurdana-Šepić
et al. 2018; Giannini et al. 2022).


The mechanisms producing the eruptions in systems like FUors
and EXors have yet to be understood (Cieza et al. 2018). Several
different triggers have been proposed to explain this phenomenon,
such as disk fragmentation (Vorobyov & Basu 2005, 2015; Zhu et al.
2012), coupling of gravitational and magneto-rotational instability
(MRI) (Armitage et al. 2001; Zhu et al. 2009), and tidal interaction
between the disk and a companion (Bonnell & Bastien 1992; Lodato
& Clarke 2004; Borchert et al. 2022b). In terms of evolution, a
scenario where FUors are understood as an earlier phase followed
by an EXor phase could explain some of the observed properties of
these systems (Cieza et al. 2018). EXors have less prominent (or lack
of) outflows, and smaller masses/luminosities than FUors since the
mass loss, accretion, and outbursts will significantly remove the gas
and dust material during their evolutionary stages.


If most stars undergo FUor/EXor-like episodic accretions during
their evolution, imaging the circumstellar disks of FUors at submm/mm wavelengths can inform or constrain the underlying outburst
mechanisms. For class 0/I objects (e.g., those still accreting from
their circumstellar disks and envelopes), the massive disk could be
expected to be prone to be gravitationally unstable, which can, consequently, trigger the MRI and/or disk fragmentation. Additionally,
close encounters of stars can shape both gas and dust disk morphology (Cuello et al. 2019). Inferring which scenario plays in each disk
requests an analysis that strongly depends on how well-resolved and
which features one can extract from the observations. Consequently,
when eruptive disks give a hint of irregular morphology or kinematics, follow-up observations at higher resolution are needed to resolve
the substructures and infer the nature of the system.


HBC 494 is a Class I protostar, located in the Orion molecular
cloud at a distance of 414±7 pc (Menten et al. 2007), and has been


MNRAS **000**, 1–13 (2023)



**Table 1.** List of the Cycle 4 ALMA observations of the target HBC 494, used

in this work


PI Proj. ID Ang. Res. Date of obs. Integration
(beam minor axis)


Zurlo 2016.1.00630.S 0 [′′] _._ 142 09/10/2016 8.39 min

Zurlo 2016.1.00630.S 0 [′′] _._ 027 26/09/2017 25.55 min


classified as a FUor [1] . This young eruptive object (also called Reipurth
50) was discovered during an optical survey and described as a bright,
conical, and large nebula reflecting light from a 1.5 arcmin away from
a 250 L⊙ infrared source. Both were located at the southern part of
the L1641 cloud in Orion (Reipurth 1985; Reipurth & Bally 1986).
This nebula was claimed to appear after 1955, and its first detailed
study showed high variability between 1982 and 1985, a consequence
of a primordial IR source variability. Posterior studies have also
confirmed its variability. For example, Chiang et al. (2015) reported
a dramatic brightening (thus clearing of part of the nebula) that
occurred between 2006 and 2014. These events can be explained by
an episode of outflow coming from HBC 494. More recently, Postel
et al. (2019), using archival photometry data along with Herschel
and Spitzer spectra presented the detection of several molecular lines
and the spectral energy distribution (SED) of HBC 494. The SED
presented strong continuum emission in the mid and far-infrared,
which is indicative of envelope emission. Such violent outflows were
observed and described in Ruíz-Rodríguez et al. (2017).
ALMA Cycle-2 observations in the millimeter continuum (∼0 [′′] _._ 25
angular resolution) show that the disk is elongated with an apparent asymmetry (Cieza et al. 2018), indicating the presence of an
unresolved structure or a secondary disk. In this work, we present
ALMA Cycle 4 observations at ∼0 [′′] _._ 03 angular resolution that reveal
the binary nature of the HBC 494 system. Only Cycle 4 data were
used in this work. The paper is structured as follows. The ALMA
observations and data reduction are described in section 2. The re
sults from the continuum and line analysis are described in section
3. The discussion is presented in section 4, while we conclude with
a summary of our results in section 5.


**2** **OBSERVATIONS AND DATA REDUCTION**


HBC 494 has been observed during the ALMA Cycle-4 in band 6
(program 2016.1.00630.S: PI Zurlo) for two nights, one on the 9 [th]

October 2016 and the other on the 26 [th] September 2017 (see table 1).
On the first night, the short baseline configuration was acquired, with
a precipitable water vapor of 0.42 mm. The ALMA configuration
of antennas was composed of 40 12-m antennas with a baseline
from 19 to 3144 m. The flux calibrator and bandpass calibrator were
both J0522-3627, and the phase calibrator was J0607-0834. The
total integration on the target was 8.39 min. The second night, the
long baseline dataset, had precipitable water vapor of 1.08 mm. The
ALMA configuration consisted of 40 12-m antennas with a baseline
from 42 m to 14851 m. The flux calibrator was J0423-0120, the
bandpass calibrator was J0510+1800, and the phase calibrator was
J0541-0541. The total integration on the target was 25.55 min.
The central frequencies of each spectral window were: 230.543
(to cover the transition [12] CO J=2-1), 233.010 (continuum), 220.403
( [13] CO J=2-1), 219.565 (C [18] O J=2-1), and 218.010 (continuum)


1 The FU Ori classification is still controversial and has been contested by
Connelley & Reipurth (2018).

_ALMA resolves the binary HBC 494_ 3



GHz. The minimum spectral resolution achieved (second night) for
12 CO was 15.259 kHz (∼ 0.02 km/s), while for 13 CO and C 18 CO, it
was 30.518 kHz (∼ 0.04 km/s). Both continuum bands presented
2 GHz bandwidths. The data were calibrated with the Common

Astronomy Software Applications package ( `CASA` v.5.5, McMullin
et al. 2007), and the python modules from CASA API, _casatasks_
and _casatools_ (CASA Team et al. 2022). The standard calibrations
include water vapor calibration, temperature correction, and phase,
amplitude, and bandpass calibrations.


**2.1** **Continuum imaging**









-7°27'29.5"


29.6"









29.7"


29.8"



















-7°27'29.5"


29.6"





We started our analysis by fixing the visibilities’ phase center on
J2000 05h40m27.448s -07d27m29.65s. The image synthesis of the
1.3 mm continuum emission was performed with the _tclean_ task of
CASA. For the high-resolution data, we used the Briggs weighting
scheme with a robust parameter of 0.5, resulting in a synthesized
beam size of 41.2 × 29.8 mas, and a position angle of 40.6. The
pixel scale of the image was set to 1.5 mas. One iteration step of
self-calibration was applied to both observations. For the first night
(low-resolution image: 142 mas), it resulted in an improvement of
∼6 SNR. For the second night (high-resolution image: 27 mas), it
resulted in an SNR improvement of ∼ 1.6.
Our final continuum image was produced from a concatenated
measurement set combining both, the short and the long baseline
visibilities, using the _concat_ task of CASA. We used the same image
synthesis parameters used for the second night of observation.


**2.2** **Line imaging**


The visibilities were fixed at the same phase center as was done for the
continuum coordinates (see subsection 2.1). After producing a dirty
image from the visibilities, we noticed that the emission mimicked the
presence of gaseous envelopes around the disks (moment 0 maps, see
Figure 1, left column) but no gas dynamic signatures were revealed
(moment 1 map, see Figure 1, right column). Therefore, we proceeded
to remove the visibility’s continuum contributions by using the CASA
task _uvcontsub_ .

Next, we performed the _tclean_ process using Briggs weighting
with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale
of 6 mas. The total velocity ranged between -6 km/s to 18 km/s,
although a smaller range (0 km/s to 11 km/s) was used to create the
13 CO and C 18 O moment maps. We used spectral resolution widths
of 1 km/s for [12] CO and of 0.3 km/s for [13] CO and C [18] O. The rms

values, obtained for the channel without a clear signal on the channel
maps (4 km/s), were 1.9, 3.6, and 2.6 mJy/beam for [12] CO, [13] CO and
C [18] O, respectively.



29.7"


29.8"


-7°27'29.5"


29.6"


29.7"


29.8"













1













**3** **RESULTS**


**3.1** **Continuum analysis**


With the high-resolution data shown in Figure 2, we could reveal the
binary nature of the HBC 494 system. Each of the components in
HBC 494 is surrounded by continuum emission, most likely associated with circumstellar disks.

We performed a 2D Gaussian fitting with the _imfit_ tool of CASA in
order to characterize the newly resolved components. The projected
separation between the two sources is 0 [′′] _._ 18 (75 au). We name each
component with the usual convention, i.e. “N” and “S” components,
referring to the northern and the southern source, respectively. We



**Figure 1.** Small-scale moment maps for the analyzed CO isotopologues, [12] CO
(top), [13] CO (middle) and C [18] O (bottom), without subtraction of the continuum. The black stars mark the peak flux positions of the continuum disks. The
dashed black contours correspond to 100×rms from the continuum emission
(100×34 _𝜇_ Jy/beam). Left: Moment 0 maps for each mentioned molecular line.
The rms values at the bottom of each panel are in units (mJy/beam)(km/s).
The [12] CO moment 0 map (top-left) has contour levels of 5, 7, and 9×rms
showed at the bottom of the panel. [13] CO and C [18] O moment 0 maps (middle
and bottom - left) have contour levels of 3 and 4×rms showed at the bottom
of each panel. Right: Moment 1 maps for each mentioned molecular lines.
The contours are the same as each left panel respectively. The maps include
only pixels above 3 times the rms measured from the set of channels used for
each molecular line (-6 km/s to 18 km/s for [12] CO and 0 km/s to 11 km/s for
13 CO and C 18 O).


assume the northern component to be the primary as it is five times
brighter than the southern (secondary) disk. Both individual disks are
resolved according to our Gaussian fit. For the primary component,
we find a major axis FWHM of 84.00 ± 1.82 mas and a minor axis of
66.94 ± 1.50 mas (34.8 ± 0.7 × 27.8 ± 0.6 au), with a position angle
of 70.01 ± 4.46 deg (values deconvolved from the beam). For the
secondary, the major axis FWHM is 64.60 ± 2.49 mas and the minor
axis FWHM is 45.96 ± 1.89 mas (26.7 ± 1.0 × 19.9 ± 0.8 au), and the
position angle is 65.38 ± 5.32 deg. The integrated fluxes for “N” and
“S” are 105.17 ± 1.89 mJy and 21.06 ± 0.63 mJy, respectively. The
peak fluxes are 22.96 ± 0.35 mJy/beam and 8.71 ± 0.21 mJy/beam for
the primary and secondary sources, respectively. The rms is ∼0.034
mJy/beam, as observed in a circular region with a radius of 225 mas
without emission. The inclinations are calculated using the aspect
ratios of the disks. These are assumed as projected circular disks
when face-on, thus elliptical when inclined:

_𝑖_ = arccos � _𝑏𝑎_ �,


where “b" and “a" are the semi-minor and semi-major axes, respectively. It resulted in 37.16 ± 2.36 degrees inclination for HBC 494 N


MNRAS **000**, 1–13 (2023)

4 _P. H. Nogueira et al._





**Figure** **2.** ALMA observations at 1.3 mm of the HBC 494 system. The images reveal the binary nature of HBC 494 with two components surrounded by
continuum emission associated with circumstellar dust. The respective signal-to-noise ratios of each image are shown in each panel. We show the resulting
images from the long baseline observation with a resolution of 0 [′′] _._ 027 arcsecond ( _left_ ), the short baseline data at 0 [′′] _._ 142 arcsecond resolution ( _middle_ ), and the
combination of the two observations with 0 [′′] _._ 0298 ( _right_ ). Dashed green lines in the left and middle images represent a 3-sigma contour associated with the
lower-resolution continuum image. The combined image has a beam size of ∼ 41 x 30 mas, shown in the lower-left corner of the image. Its contours correspond,
from the yellow (more external) to the pink dashed lines, to 10, 40, 70, and 100 times the rms value, respectively. The rms is ∼0.034 mJy/beam.



and 44.65 ± 3.27 for HBC 494 S. At 30 mas resolution, no substructures were detected (see the radial profiles in Figure 3).
A large fraction of the mm-sized grains in protoplanetary disks
resides in the midplane. They are usually optically thin to their own
radiation. Thus, assuming standard disks, we can use the observed
fluxes to estimate the dust masses of HBC 494 N and S. For that, we
use the following formula (as in Beckwith et al. 1990; Andrews &
Williams 2005; Cieza et al. 2018):


_𝐹_ _𝜈_ _𝑑_ [2]
_𝑀_ dust = (1)

_𝑘_ _𝜈_ _𝐵_ _𝜈_ ( _𝑇_ dust ) _[,]_


where _𝐹_ _𝜈_ is the observed flux, _d_ is the distance to the source, _𝐵_ _𝜈_ is the
Planck function and _𝜅_ _𝜈_ is the dust opacity. Adopting the distance of
414 pc, isothermal dust temperature ( _𝑇_ dust = 20 K) and dust opacity
assuming a _𝑀_ gas / _𝑀_ dust fraction of 100, ( _𝜅_ _𝜈_ = 10 ( _𝜈_ / 10 [12] Hz) cm [2]

g [−][1] ; Beckwith et al. 1990) we get dust masses of 1.43 _𝑀_ Jup (HBC
494 N) and 0.29 _𝑀_ Jup (HBC 494 S). Following the standard gasto-dust mass ratio of 100, we report disk gas masses estimations of
143.46 _𝑀_ Jup for HBC 494 N, and 28.68 _𝑀_ Jup for HBC 494 S. The
physical parameters based on the CASA analysis are listed in Table
2.


**3.2** **Line analysis**


The next two subsections describe the large and small-scale structure analyses. The large scale, using the extent of 8000 au, shows
the results of outflows and envelopes. At such a scale, there is not
enough resolution to display both disks’ dynamics and their possible
interactions. The small scale (150 au) fulfills this role, and thus, both
gas scenarios must be taken into account.


_3.2.1_ _Large-scale structures (8000 au)_


The channel maps (Figures 4, C1 and C2) show southern and northern
12 CO wide-angle arcs (∼ 150 ◦ ) and no clear signal of large structures


MNRAS **000**, 1–13 (2023)



**Table 2.** ALMA imfit analysis results and physical parameters inferred from
the HBC 494 continuum disks.


HBC 494 N HBC 494 S


Flux density (mJy) 105.2 ± 1.9 21.1 ± 0.6
Peak flux (mJy / beam) 23.0 ± 0.4 8.7 ± 0.2
Major axis (mas) 84.0 ± 1.8 64.6 ± 2.5
Minor axis (mas) 66.9 ± 1.5 46.0 ± 1.9
Major axis (au) 34.8 ± 0.7 26.7 ± 1.0
Minor axis (au) 27.8 ± 0.6 19.9 ± 0.8
Position angle (deg) 70.0 ± 4.5 65.4 ± 5.3
Beam major axis (mas) 41.2 41.2
Beam minor axis (mas) 29.8 29.8
Beam Position angle (deg) 40.6 40.6
Beam area (sr) 3.3e-14 3.3e-14
rms ( _𝜇_ Jy / beam) 34.0 34.0


Dust mass ( _𝑀_ Jup ) 1.4 0.3
Gas mass ( _𝑀_ Jup ) 143.5 28.7
Inclination (deg) 37.2±2.4 44.7±3.3
FWHM Radius (au) 34.8±0.7 26.7±1.0


from the other molecular lines. This bipolar outflow was previously
described in Ruíz-Rodríguez et al. (2017). The wide angular structure
shows an outflow morphology expected for Class I disks (Arce &
Sargent 2006). In our observations, the southern and northern arcs
are defined by the velocity ranges of [-6 km/s to 1 km/s] and [5 km/s
to 18 km/s], respectively. The moment 0 and 1 [12] CO arcs are shown
in Figure 5. However, it is noticeable that the northern arc (redshifted
emission) dominates the displayed velocities. The lack of signal in
the southern arc can be explained by lower molecular density, or due
to intracloud absorption. Figure 6 shows the three molecular lines’
concentration and dynamics (moment 0 and 1 maps), as well as the
spectral profile measured within the dashed regions.
The [13] CO emission traces the rotating, infalling, and expanding
envelope surrounding the system, showing a small deviation from
the [12] CO outflowing arcs’ rotation axis. The blue-shifted emission
concentrates around 3 km/s, while the red-shifted emission is around

1.0


0.8



_ALMA resolves the binary HBC 494_ 5


Radius [au]
0 10 20 30 40 50



0.6


0.4


0.2


0.0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||



0.00 0.02 0.04 0.06 0.08 0.10 0.12
Radius [ [′′] ]


**Figure 3.** Radial brightness profile of HBC 494 N and HBC 494 S. The surface brightness (dots), measured in apertures ranging from the beam’s major axis
to 3 times the semi-major axis FWHM of each continuum disk, were normalized to the peak fluxes. The shaded regions indicate 1 _𝜎_ error measured in each
aperture. The dashed lines correspond to the ALMA imfit FWHM of each disk.



5 km/s. It is noticeable that the [13] CO emission has a rotation axis
almost perpendicular to the [12] CO outflows axis, ensuring that the
physical processes behind the two are different. The spectral [13] CO
also shows a dip around 4 km/s, but this may not trace an absorption but a lack of signal due to the analyzed uv-coverage or cloud
contamination.
The C [18] O emission, however, is faint and hardly distinguishable
from the surrounding gas in moment 0 maps. It has also the lowest
abundance of the three analyzed isotopologues, being a good tracer
of the higher gas densities in the innermost regions of the cloud.
Its velocity maps show that a faint blueshifted motion was detected
around 3 km/s, very weak when compared to the redshifted emission
detected principally around 5 km/s. Due to the higher concentration
of gas in the northern part, it is reasonable that we observed a weak
gas counterpart in the southern region. At large-scale, our results are
comparable with the ones presented in (Ruíz-Rodríguez et al. 2017).
Furthermore, a lower limit of the envelope material of ∼600 Jy.km/s
towards HBC 494 could be traced using Total Power (TP), ALMA
compact array (ACA), and the main array ALMA observations with
C [18] O data in the range of 4.3±0.5 km s [−][1] (Ruíz-Rodríguez private
communication).


_3.2.2_ _Small scale structures (150 au resolution)_


We started by removing the continuum contribution from all molecular lines observed ( [12] CO, [13] CO, C [18] O). We already expected that
12 CO would trace the gas in larger scales due to its optical depth and,
thus, could blend with smaller gas signatures. To avoid cloud contamination during the creation of [12] CO small-scale moment maps,



we removed the channels that were more affected. We considered
velocities in the range of -6 km/s to 1 km/s, and from 5 km/s to 18
km/s, as similarly done for the different large-scale arcs described in
the previous subsection.

Following, CO channel maps and moment 0 and 1 maps were
produced to explore potential hints of interaction between the stars
and the two circumstellar disks. In particular, we looked for disk
substructures and perturbed rotation patterns. The moment maps can
indeed provide valuable information about the binary orbit and the
disks’ geometry. However, by looking at the molecular lines in this
scale (see the moment maps in Figure 7, left and middle columns), we
could not clearly detect the presence of the disks or their rotational
signatures. We can only notice that the [12] CO and [13] CO moment 0
maps show an interesting pattern, where less gas emission is found
where the continuum disks are. Additionally, the area within the
continuum disks highlights regions similar to cavities or “holes"
(Figure 7, left column, upper and middle row). Interestingly, RuízRodríguez et al. (2022) observed similar features from the same
molecular lines, in addition to HCO [+], for another FUor system,
V883 Ori. The work also showed that the origin of cavities and
ring emission around disks can be interpreted in two ways, one based
on gas removal and the other on optical depth effects.

If the signal traces the lack of gas surrounding the disks, the leading
mechanism may be slow-moving outflows. The central regions of
young continuum disks are expected to be constantly carved by the
influence of magneto-hydrodynamical jets (Frank et al. 2014). In
addition, it is also expected that the lower emission observed comes
from the chemical destruction by high-energy radiation (more active
disks will create bigger cavities). By looking at the size of the gaps,


MNRAS **000**, 1–13 (2023)

6 _P. H. Nogueira et al._


-7°27'20"


25"


30"


35"











10


8


6


4


2


0



-7°27'20"





















25"


30"


35"



-7°27'20"





















25"


30"


35"



-7°27'20"



















25"


30"


35"


-7°27'20"


25"


30"


35"




|-6 .00 km/s<br>2000 au|-6 .00 km/s|-5 .00 km/s<br>2000 au|-5 .00 km/s|-4 .00 km/s<br>2000 au|-4 .00 km/s|-3 .00 km/s<br>2000 au|-3 .00 km/s|-2 .00 km/s<br>2000 au|-2 .00 km/s|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|-1.00 km/s<br>2000 au|-1.00 km/s|-0.00 km/s<br>2000 au|-0.00 km/s|1.00 km/s<br>2000 au|1.00 km/s<br>2000 au|2.00 km/s<br>2000 au|2.00 km/s<br>2000 au|3.00 km/s<br>2000 au|3.00 km/s<br>2000 au|3.00 km/s<br>2000 au|
|4.00 km/s<br>2000 au|4.00 km/s<br>2000 au|5.00 km/s<br>2000 au|5.00 km/s<br>2000 au|6.00 km/s<br>2000 au|6.00 km/s<br>2000 au|7.00 km/s<br>2000 au|7.00 km/s<br>2000 au|8.00 km/s<br>2000 au|8.00 km/s<br>2000 au|8.00 km/s<br>2000 au|
|9.00 km/s<br>2000 au|9.00 km/s<br>2000 au|10.00 km/s<br>2000 au|10.00 km/s|11.00 km/s<br>2000 au|11.00 km/s|12.00 km/s<br>2000 au|12.00 km/s|13.00 km/s<br>2000 au|13.00 km/s|13.00 km/s|
|14.00 km/s<br>2000 au|14.00 km/s|15.00 km/s<br>2000 au|15.00 km/s|16.00 km/s<br>2000 au|16.00 km/s|17.00 km/s<br>2000 au|17.00 km/s|18.00 km/s<br>2000 au|18.00 km/s|18.00 km/s|



5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



**Figure 4.** [12] CO channel maps of the HBC 494 system. The star in the center marks the position of the continuum disks. The southern arc is more evident between
the velocities -6 km/s to 1 km/s, while the northern is more easily seen between 7 km/s and 18 km/s.



we can observe that HBC 494 S exerts a smaller influence on the gas
than HBC 494 N and, thus, HBC 494 N is the more active disk in the
system if this hypothesis is correct.


Another interpretation of the negatives in our gas maps is that this
is a spurious result of continuum subtraction. Usually, the continuum
emission is inferred from channels devoid of gas line emission. The
usual procedure does not consider the line emission where these
channels overlap. Suppose the emission lines are optically thick above
the continuum. In that case, the foreground gas can significantly
absorb the photons coming from the underlying continuum, which
may lead to a continuum overestimation. Consequently, in such cases,
the continuum may be over-subtracted, causing the “hole" feature that
is stronger where the line peaks (see e.g., Boehler et al. 2017; Weaver
et al. 2018).


MNRAS **000**, 1–13 (2023)



**4** **DISCUSSION**


**4.1** **Multiplicity and triggering mechanisms**


Besides HBC 494, there are ∼ 25 known FUor objects within 1 kpc
(Audard et al. 2014). As previously commented, many triggering
mechanisms can cause episodic accretion events. From this sample,
only HBC 494 and a few other FUor systems are known binaries
(e.g., FU Orionis, L1551 IRS, RNO 1B/C, AR 6A/B; Pueyo et al.
2012 and references therein).
Given the high occurrence rate of stellar binaries harboring disks,
the lack of detection of multiple YSO systems remains a case of investigation. Additionally, young disks evolve in crowded star-forming
regions, enhancing the hypothesis that the outbursts of Class 0/I disks
may affect other disks, driving episodic accretion events. Also, surveys and studies using ALMA and NIR data for Class I-III disks,

800


700


600


500


400


300



_ALMA resolves the binary HBC 494_ 7



-7°27'20"


25"


30"


35"





-7°27'20"


25"


30"


35"





0



200




|Moment 0 - southern arc|Col2|
|---|---|
|Moment 0 - southern arc||
|rms = 38.65 mJy/Beam.km/s<br>[-6 km/s to 1 km/s]<br>2000 au|rms = 38.65 mJy/Beam.km/s<br>[-6 km/s to 1 km/s]<br>2000 au|
|h40m280s<br>275s<br>270s|h40m280s<br>275s<br>270s|


|Moment 1 - southern arc|Col2|
|---|---|
|Moment 1 - southern arc||
|[-6 km/s to 1 km/s]<br>2000 au|[-6 km/s to 1 km/s]<br>2000 au|
|h40m280s<br>275s<br>270s|h40m280s<br>275s<br>270s|



-7°27'20"


25"


30"


35"



-7°27'20"


25"


30"


35"





1750


1500


1250


1000


750


500





1


2


3


4


5


6


10


9


8


7


6


5






|Moment 0 - northern arc|Col2|
|---|---|
|Moment 0 - northern arc||
|rms = 87.47 mJy/Beam.km/s<br>[5 km/s to 18 km/s]<br>2000 au|rms = 87.47 mJy/Beam.km/s<br>[5 km/s to 18 km/s]<br>2000 au|
|h40m280s<br>275s<br>270s|h40m280s<br>275s<br>270s|


|Moment 1 - northern arc|Col2|
|---|---|
|Moment 1 - northern arc||
|[5 km/s to 18 km/s]<br>2000 au|[5 km/s to 18 km/s]<br>2000 au|
|h40m280s<br>275s<br>270s|h40m280s<br>275s<br>270s|



**Figure** **5.** Large-scale [12] CO moment maps split in each one of the bipolar outflow structures. The left column corresponds to moment 0 maps, and the right
column to moment 1 maps. The plots in the same row refer to the same structure, which is the southern arc ( _upper row_ ), and the northern arc ( _bottom row_ ). The
position of the HBC 494 N is marked with a star. The maps include only pixels above 2 times the rms measured from the set of channels shown at the top of
each panel.



show that there is a lack of detection when only visual multiple systems (separations of 20-4800 au) are considered (e.g., Zurlo et al.
2020a, 2021). When all the possible separations are taken into account, the multiplicity frequencies considerably increase. For Taurus,
for example, it goes up to 70% when spectroscopic binaries are included (Kraus et al. 2011). In the case of Orion, 30% of the systems
are multiple with separations between 20 and, 10000 au (Tobin et al.
2022). The latter study also noticed that the separations decrease with
time (when comparing Class 0, I, and flat-spectrum disks) and that
the multiplicity frequency in Class 0 is higher than in the later evolutionary stages. Therefore, multiple eruptive young systems must be
common, and more detectable within evolutionary time. They probably are not frequently detected due to the short time duration of
enhanced accretion events in comparison with the lifetime of disks
in class 0/I stages (see Audard et al. 2014 for a FUors review). Still,



it is not clear if disks belonging to close-separation systems are more
susceptible to eruptive events than isolated ones.


For each HBC 494 disk, no clue of trigger mechanisms was found,
since the gas and continuum data did not reveal clear spiral or clumpy
features indicating a case of infall or GI (see e.g., Zhu et al. 2012;
Kratter & Lodato 2016). Looking at the dust continuum (Figure 2),
CO isotopologues moment maps (Figure 7), and the scattered [12] CO
emission (Figure 12 of Ruíz-Rodríguez et al. 2017), the hypothesis
of stellar flybys is also not encouraged since no trace of perturbation
was detected (Cuello et al. 2020, 2023). Moreover, dynamical data
(small-scale moment 1 maps) also can provide clues for the triggering mechanism (Vorobyov et al. 2021). However, it requires clear
detection of quasi-keplerian rotation, which was not observed.


In the case of binaries, the first component to ignite the FUor
outbursts can quickly trigger the secondary one by inducing per

MNRAS **000**, 1–13 (2023)

8 _P. H. Nogueira et al._


Moment 0 - [12] CO


500 1000 1500 2000 2500


-7°27'20"



-7°27'20"


25"


30"


35"



Moment 1 - [12] CO


2 0 2 4 6 8 10



Spectral profile - [12] CO









25"


30"


35"









5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]


Moment 0 - [13] CO


200 400 600



5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]


Moment 1 - [13] CO


3.0 3.5 4.0 4.5 5.0 5.5 6.0


-7°27'20"



5 0 5 10 15 20

RV (km/s)


Spectral profile - [13] CO



-7°27'20"


25"


30"


35"



25"


30"


35"















5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]


Moment 0 - C [18] O


200 400 600



5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]


Moment 1 - C [18] O


3.0 3.5 4.0 4.5 5.0


-7°27'20"



25


20


15


10


5


0


5


17.5


15.0


12.5


10.0


7.5


5.0


2.5


0.0


2.5


6


5


4


3


2


1


0



2 4 6 8

RV (km/s)


Spectral profile - C [18] O



-7°27'20"


25"


30"











25"


30"


35"





5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



2 4 6 8

RV (km/s)


**Figure 6.** Large-scale moment maps for the analyzed CO isotopologues and spectral fluxes. The left column corresponds to moment 0 maps, the middle one to
moment 1 maps, and the third column to spectral profiles. The rms values at the bottom of each panel in the left column are in units (mJy/beam)(km/s). The
plots in the same row refer to the same molecular lines, which are [12] CO ( _upper row_ ), [13] CO ( _middle row_ ), and C [18] O ( _bottom row_ ). The dashed black lines in
the moment 1 column correspond to the regions used to produce the spectral profiles. The red shaded area in [12] CO profile represents the channels we excluded
before creating the moment maps lying in the same row (to avoid cloud contamination). The center of stars, in the middle of each figure, marks the position of
both disks. The maps include only pixels above 2 times the rms measured from the set of channels used for each molecular line (-6 km/s to 18 km/s for 12CO
and 0 km/s to 11 km/s for 13CO and C18O).


MNRAS **000**, 1–13 (2023)

_ALMA resolves the binary HBC 494_ 9


Spectral profile - [12] CO


50

7


0


|rms = 22 19<br>.|Col2|Col3|
|---|---|---|
|rms = 22.19|rms = 22.19||
|rms = 22.19|rms = 22.19||


|Col1|Col2|
|---|---|
|||


|Col1|Col2|12CO<br>HBC494N<br>HBC494S|
|---|---|---|
||||


|rms = 15 77<br>.|Col2|Col3|
|---|---|---|
|rms = 15.77|rms = 15.77||
|rms = 15.77|rms = 15.77|rms = 15.77|


|Col1|Col2|
|---|---|
|||
|||
|||


|rms = 11 22<br>.|Col2|Col3|
|---|---|---|
|rms = 11.22|rms = 11.22||



0.0 2.5 5.0 7.5 10.0
RV (km/s)



-7°27'29.5"


29.6"


29.7"


29.8"


-7°27'29.5"


29.6"


29.7"


29.8"


-7°27'29.5"


29.6"


29.7"


29.8"



Moment 0 - [12] CO


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]


Moment 0 - [13] CO


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]


Moment 0 - C [18] O


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



70


50


30


25


15


23


18


13



Moment 1 - [12] CO


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]


Moment 1 - [13] CO


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]


Moment 1 - C [18] O


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5


3


8


6


4


7


5


3



50


100


150


0


50


100


20


0


20


40


60



-7°27'29.5"


29.6"


29.7"


29.8"


-7°27'29.5"


29.6"


29.7"


29.8"


-7°27'29.5"


29.6"


29.7"


29.8"





5 0 5 10 15 20
RV (km/s)


Spectral profile - [13] CO







0.0 2.5 5.0 7.5 10.0
RV (km/s)


Spectral profile - C [18] O





**Figure 7.** Small-scale moment maps for the analyzed CO isotopologues, after subtraction of the continuum, and their spectral profiles. The first column corresponds
to moment 0 maps, and the middle one to moment 1 maps. The rms values at the bottom of each panel in the left column are in units (mJy/beam)(km/s). The
molecular lines correspond to [12] CO ( _upper row_ ), [13] CO ( _middle row_ ) and C [18] O ( _bottom row_ ). The dashed black lines spatially correspond to the contour level
equal to 100 times the continuum rms (100×34 _𝜇_ Jy/beam), in the continuum combined image (Figure 2, _right_ ). The orange stars mark the peak flux positions of
the continuum disks. The right column represents the spectral profiles measured from velocity maps taken within each disk. The red shaded area in [12] CO profile
represents the channels we excluded before creating the moment maps lying in the same row (to avoid cloud contamination).



turbations and mutual gravitational interactions (Bonnell & Bastien
1992; Reipurth & Aspin 2004; Vorobyov et al. 2021; Borchert et al.
2022a,c). Therefore, we can assume that all the disks in FUor multiple
systems like HBC 494 might have undergone successive enhanced
eruptive stages, despite the differences in mass and radius between
each component. However, it is not clear how the outbursts in HBC
494 N and HBC 494 S affect each other since the moment maps do
not show the connection between disks. Although, on larger scales,
we detected the difference in the amount of gas mass detected in the
northern regions compared to the southern. This scenario may be
described if the more massive disk (i.e. HBC 494 N) has a higher
contribution to the outbursts and winds.


With astrometric data, the eccentricity of orbits can be determined.
If both disks are still accreting gas from the environment, it is expected that quasi-circular orbits trigger enhanced accretion every few
binary periods. Eccentric orbits, on the other hand, can induce eruptive events in every orbit, preferentially when the binaries reach the
pericentre (see e.g. Dunhill et al. 2015; Lai & Muñoz 2022). Obser


vational evidence of circumbinary disks in different YSO stages was
found (see e.g. Dutrey et al. 1994; Mathieu et al. 1997; Tobin et al.
2016a; Maureira et al. 2020) and are seen as a common counterpart
of young binaries in formation. However, no HBC 494 circumbinary
gas disk was observed due to cloud contamination and optical depth
effects.


**4.2** **Disk sizes and masses**


FU Orionis, the precursor of the classification FUor, is also a binary
system. HBC 494 system, however, has smaller disks separation compared to the 210 au between FU Orionis north and south components
(Pérez et al. 2020). FU Orionis components have similar sizes and
masses between their disks, contrary to the HBC 494 components.
We can argue that, due to HBC 494 being a close-packed system with
substantially different masses between their components, a scenario
of radius truncation can be tested. However, the FU Orionis disks
are exceptional compared to other FUors, which are generally more


MNRAS **000**, 1–13 (2023)

10 _P. H. Nogueira et al._


massive and larger. Nevertheless, it is important to check if HBC 494
follows the trend which shows that FUor objects are more massive
than class 0/I disks and that disks from multiple systems are smaller
compared to those from non-multiple systems (Cieza et al. 2018;
Hales et al. 2020; Tobin et al. 2020; Zurlo et al. 2020b). First, we
will describe our results regarding masses and radius. Then, we will
compare HBC 494 disks to FUors and Orion YSOs in the literature.
We assumed dust masses (assuming the gas-to-dust ratio of 100)
inferred by optically thin approximation (described in section 3.1).
However, it is worth mentioning that the optically thin analysis can
not take into account the innermost regions of the disk (optically
thick). This may lead to an underestimation of the dust masses.
Also, an underlying miscalculated dust grain temperature can alter
the results, overestimating the masses if the dust is warmer than
expected. The chosen assumptions of temperatures (fixed 20 K for
dust grains) and opacities for both disks lead to 1.43 _𝑀_ Jup and 0.29
_𝑀_ Jup for HBC 494 N and HBC 494 S, respectively. Based on these
results, we can say that the HBC 494 N is comparable to other
FUor sources, but HBC 494 S has its dust mass comparable to EXor
disks (Cieza et al. 2018). The disk sizes were calculated using the
deconvolved Gaussian FWHM/2 radius obtained from 2D Gaussian

fits. This methodology was also used for other ALMA datasets (e.g.,
Hales et al. 2020; Tobin et al. 2020). Therefore, it allows a consistent
comparison with other disks. The dust mass vs radius comparison
between HBC 494 N and HBC 494 S, a sample of 14 resolved FUors
and EXors (extracted from Hales et al. 2020) and Class 0/I systems
(Tobin et al. 2020), can be seen in figure 8. Here, as previously
stated, we notice that HBC 494 disks (black, hexagon symbols),
as other eruptive systems (hexagon, square, and triangle symbols),
present higher masses than young systems, which are not in the
stage of episodic accretion. However, there is no obvious distinction
between the disk sizes of individual systems, eruptive or not. A clear
difference is seen when we compare the disks from multiple systems
(hexagon symbols) and single systems. The latter present bigger sizes
as they are not targets for tidal truncation, enhanced radial drift, and
more aggressive photoevaporation — processes known to rule closesystems dynamics and evolution (see e.g., Kraus et al. 2012; Harris
et al. 2012; Rosotti & Clarke 2018; Zurlo et al. 2020a, 2021).


**4.3** **Binary formation and alignment**


Different scenarios have been proposed to explain the formation of
binary systems. The main one for close-separated systems is fragmentation, followed by dynamic interactions (for a review, see Offner
et al. 2022).
The fragmentation process consists of partial gravitational collapse
from self-gravitating objects. To be successful, many initial physical
conditions are relevant as thermal pressure, density, turbulence, and
magnetic fields. In addition, the fragmentation can be divided into
two main classes: direct/turbulent (e.g., Boss & Bodenheimer 1979;
Bate & Burkert 1997) and rotational (e.g., Larson 1972; Bonnell
1994; Bonnell & Bate 1994a,b; Burkert et al. 1997).
The direct/turbulent fragmentation from a collapsing core is highly
dependent on the initial density distribution. It can form wideseparated multiple YSO systems with uncorrelated angular momentum. Thus, the direct/turbulent fragmentation may lead to preferentially misaligned multiple systems (Bate 2000; Offner et al. 2016;
Bate 2018; Lee et al. 2019). The rotational fragmentation, instead,
is caused by instabilities in rotating disks and leads to preferentially
spin-aligned and coplanar systems (Offner et al. 2016; Bate 2018).
Moreover, later dynamical processes such as stellar flybys (Clarke &
Pringle 1993; Nealon et al. 2020; Cuello et al. 2023) and misaligned


MNRAS **000**, 1–13 (2023)



accretion from the environment (Dullemond et al. 2019; Kuffmeier
et al. 2020, 2021) can also induce alignment or misalignment.
The HBC 494 disks have similar inclinations (Δ _𝑖_ = 7.5 ± 4.1 degrees) and similar PAs (Δ _𝑃𝐴_ = 4.6 ± 7.0 degrees). The relative orientations of the disks suggest that the system is coplanar. Assuming
they are quasi-coplanar, with the same PA, the unprojected separation
would be ∼0 [′′] _._ 24 (99 au). Therefore, the HBC 494 disks may show
a spin-alignment situation, more typical to observed close-separated
systems (see, e.g., Tobin et al. 2016b, 2020). Thus, we tentatively
suggest that HBC 494 was formed by rotational disk fragmentation
rather than direct collapsing. However, more precise observation of
the kinematics of the surrounding gas on a small scale (Vorobyov
et al. 2021), complemented with orbital information coming from
astrometrical measurements, is required to evaluate this hypothesis.
In this context, IRAS 04158+2805 is of interest as Ragusa et al.
(2021) reported the detection of two circumstellar disks, similar to
HBC 494 in terms of small to moderate misalignment, and an external circumbinary disk. However, in contrast to IRAS 04158+2805, no
circumbinary disk was detected in HBC 494. This difference could be
explained either by the absorption of the circumbinary disk emission
due to cloud contamination, or because HBC 494 had enough time
to sufficiently empty the circumbinary mass reservoir. Since most
hydrodynamical models of star formation naturally produce young
binaries with individual disks and a surrounding circumbinary disk
(Bate 2018, 2019; Kuruwita et al. 2020), it is likely that a circumbinary disk formed at some earlier evolutionary stage of HBC 494. If
the circumbinary disk is actually there, but remains undetected, the
supply of material could extend the disk lifetime of the circumstellar disks in HBC 494. Deeper multi-wavelength observations would
provide more information, enabling us to solve this binary riddle.


**5** **CONCLUSIONS**


In this work, we presented high-resolution 1.3 mm observations of
HBC 494 with ALMA. The unprecedented angular resolution in this
source (0 [′′] _._ 027), reveals that HBC 494 is a binary that can be resolved
into two disks, HBC 494 N and HBC 494 S. The disks have a projected
separation of ∼75 au. We derived sizes, orientations, inclinations,
and dust masses for both components. Both objects appear to be in a
quasi-coplanar configuration and with their sizes halted by dynamical
evolution, besides preserving high masses, common to FUors and
EXors than typical (not eruptive) Class 0/I disks. Comparing the
two sources, we noticed that HBC 494 N is ∼5 times brighter/more
massive and ∼2 times bigger than HBC 494 S.
The gas kinematics was analyzed at two different spatial scales:
8000 au and 150 au. At large-scale, we have obtained similar results
as those presented in Ruíz-Rodríguez et al. (2017), revealing the wide
outflow arcs (traced by the [12] CO) and the infalling envelopes ( [13] CO
and C [18] O). At the small-scale, we detected depleted gas emission
(cavities) for both disks ( [12] CO and [13] CO, moment 0). They were
probably formed by slow outflows and jets coming from the disks
along the line of sight or by optical depth effects and over-subtraction
of the continuum emission. The dynamics of both disks in such scales
were masked principally by cloud contamination.
Further observations with similar resolution but of optically thinner molecular lines may lead to the characterization of the dynamical
interaction of the two components. For example, the identification
of rotational signatures from the disks can be used to identify the
dynamical masses of their central stars. With this information, we
could also constrain truncation radii. Additionally, observations of

_ALMA resolves the binary HBC 494_ 11
















|Col1|Col2|Col3|
|---|---|---|
|101<br>102<br>103<br>Mdust [M ]|V883Ori<br>HBC 494 N<br>HBC 494 S<br>V2775Ori<br>FU Ori N<br>FU Ori S<br>V1647Ori<br>NYOri<br>EXLup<br>UZTauE<br>V582Aur<br>V900Mon<br>GMCHa<br>L1551 IRS (N/S)<br>Haro5aIRS<br>V346Nor<br>Oi Cl 0I Tbi2020||
|101<br>102<br>103<br>Mdust [M ]|ron ass / (on+)|ron ass / (on+)|



10 [1] 10 [2]
R c [au]


**Figure 8.** Dust disk masses as a function of characteristic radii (FWHM/2) for FUors (blue triangles), EXors (red squares), for double FUor and EXor classification
(yellow stars), and Class 0/I objects (cyan crosses), as similarly presented in Hales et al. (2020). The horizontal arrow on V852 Aur denotes the disk radius
in an upper limit. The hexagons represent eruptive/multiple systems, with matching colors for disks lying in the same system. The data for HBC 494 disks
was generated in this work. The blue dashed line corresponds to the power-fit law to the FU/EXor data (Spearman correlation coefficient: 0.63), and the cyan
dash-dotted line, to the Class 0/I data (Spearman correlation coefficient: 0.55). To generate this plot, we obtained data from Kóspál et al. (2017); Hales et al.
(2018); Cieza et al. (2018); Takami et al. (2019); Cruz-Sáenz de Miera et al. (2019); Pérez et al. (2020); Hales et al. (2020).


.



small-scale gas structures, allied to astrometric measurements, can
be used to constrain the possible formation scenarios.
We conclude that the HBC 494 system constitutes a test bed for
eruptive binary-disk interactions and the connection between stellar
multiplicity and accretion/luminosity processes (such as outbursts).
Also, it provides a statistics enhancement about the rarely observed
systems FUors and Exors.


**ACKNOWLEDGEMENTS**


We want to thank the referee for their comments and suggestions that
significantly improved the manuscript. This paper makes use of the
following ALMA data: ADS/JAO.ALMA 2016.1.00630.S. ALMA
is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ. The National Radio Astronomy Observatory
is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work is
funded by ANID – Millennium Science Initiative Program – Center
Code NCN2021_080. P.H.N. acknowledges support from the Joint
China-Chile Committee fund and the ANID Doctorado Nacional



grant 21221084 from the government of Chile. A.Z. acknowledges
support from the FONDECYT Iniciación en investigación project
number 11190837. S.P. acknowledges support from FONDECYT
Regular project 1191934. L.A.C. acknowledges support from the
FONDECYT project number 1211656. M.M. acknowledges financial
support by Fondos de Investigación 2022 de la Universidad Viña del
Mar. J.C. and M.M. acknowledge support from ANID, – Millennium
Science Initiative Program – NCN19_171. S.C. acknowledges support from Agencia Nacional de Investigación y Desarrollo de Chile
(ANID) given by FONDECYT Regular grant 1211496, and ANID
project Data Observatory Foundation DO210001. T.B. acknowledges financial support from the Joint Committee ESO-Government
of Chile fund and the FONDECYT postdoctorado project number
3230470. This project has received funding from the European Union
(ERC, Stellar-MADE, No. 101042275).


**DATA AVAILABILITY**


This paper makes use of the following ALMA data:
ADS/JAO.ALMA 2016.1.00630.S. The data are downloadable from

the official ALMA archive and public. ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI


MNRAS **000**, 1–13 (2023)

12 _P. H. Nogueira et al._


(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ.


**REFERENCES**


[Andrews S. M., Williams J. P., 2005, ApJ, 631, 1134](http://dx.doi.org/10.1086/432712)
[Arce H. G., Sargent A. I., 2006, ApJ, 646, 1070](http://dx.doi.org/10.1086/505104)
[Armitage P. J., Livio M., Pringle J. E., 2001, MNRAS, 324, 705](http://dx.doi.org/10.1046/j.1365-8711.2001.04356.x)
[Audard M., et al., 2014, Protostars and Planets VI, pp 387–410](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch017)
[Bate M. R., 2000, MNRAS, 314, 33](http://dx.doi.org/10.1046/j.1365-8711.2000.03333.x)

[Bate M. R., 2018, MNRAS, 475, 5618](http://dx.doi.org/10.1093/mnras/sty169)

[Bate M. R., 2019, MNRAS, 484, 2341](http://dx.doi.org/10.1093/mnras/stz103)

[Bate M. R., Burkert A., 1997, MNRAS, 288, 1060](http://dx.doi.org/10.1093/mnras/288.4.1060)
[Beckwith S. V. W., Sargent A. I., Chini R. S., Guesten R., 1990, AJ, 99, 924](http://dx.doi.org/10.1086/115385)
Boehler Y., Weaver E., Isella A., Ricci L., Grady C., Carpenter J., Perez L.,
[2017, ApJ, 840, 60](http://dx.doi.org/10.3847/1538-4357/aa696c)
[Bonnell I. A., 1994, MNRAS, 269, 837](http://dx.doi.org/10.1093/mnras/269.3.837)
[Bonnell I., Bastien P., 1992, ApJ, 401, L31](http://dx.doi.org/10.1086/186663)
[Bonnell I. A., Bate M. R., 1994a, MNRAS, 269, L45](http://dx.doi.org/10.1093/mnras/269.1.L45)

[Bonnell I. A., Bate M. R., 1994b, MNRAS, 271, 999](http://dx.doi.org/10.1093/mnras/271.4.999)

[Borchert E. M. A., Price D. J., Pinte C., Cuello N., 2022a, MNRAS, 510, L37](http://dx.doi.org/10.1093/mnrasl/slab123)

Borchert E. M. A., Price D. J., Pinte C., Cuello N., 2022b, [MNRAS,](http://dx.doi.org/10.1093/mnras/stac2872) [517,](https://ui.adsabs.harvard.edu/abs/2022MNRAS.517.4436B)

[4436](https://ui.adsabs.harvard.edu/abs/2022MNRAS.517.4436B)

Borchert E. M. A., Price D. J., Pinte C., Cuello N., 2022c, [MNRAS,](http://dx.doi.org/10.1093/mnras/stac2872) [517,](https://ui.adsabs.harvard.edu/abs/2022MNRAS.517.4436B)

[4436](https://ui.adsabs.harvard.edu/abs/2022MNRAS.517.4436B)

[Boss A. P., Bodenheimer P., 1979, ApJ, 234, 289](http://dx.doi.org/10.1086/157497)
[Burkert A., Bate M. R., Bodenheimer P., 1997, MNRAS, 289, 497](http://dx.doi.org/10.1093/mnras/289.3.497)

[CASA Team et al., 2022, PASP, 134, 114501](http://dx.doi.org/10.1088/1538-3873/ac9642)
Chiang H.-F., Reipurth B., Walawender J., Connelley M. S., Pessev P., Geballe
[T. R., Best W. M. J., Paegert M., 2015, ApJ, 805, 54](http://dx.doi.org/10.1088/0004-637X/805/1/54)
[Cieza L. A., et al., 2018, MNRAS, 474, 4347](http://dx.doi.org/10.1093/mnras/stx3059)
[Clarke C. J., Pringle J. E., 1993, MNRAS, 261, 190](http://dx.doi.org/10.1093/mnras/261.1.190)
[Connelley M. S., Reipurth B., 2018, ApJ, 861, 145](http://dx.doi.org/10.3847/1538-4357/aaba7b)
Cruz-Sáenz de Miera F., Kóspál Á., Ábrahám P., Liu H. B., Takami M., 2019,

[ApJ, 882, L4](http://dx.doi.org/10.3847/2041-8213/ab39ea)
[Cuello N., et al., 2019, MNRAS, 483, 4114](http://dx.doi.org/10.1093/mnras/sty332510.48550/arXiv.1812.00961)

[Cuello N., et al., 2020, MNRAS, 491, 504](http://dx.doi.org/10.1093/mnras/stz2938)
[Cuello N., Ménard F., Price D. J., 2023, European Physical Journal Plus, 138,](http://dx.doi.org/10.1140/epjp/s13360-022-03602-w)

[11](https://ui.adsabs.harvard.edu/abs/2023EPJP..138...11C)

Dullemond C. P., Küffmeier M., Goicovic F., Fukagawa M., Oehl V., Kramer
[M., 2019, A&A, 628, A20](http://dx.doi.org/10.1051/0004-6361/201832632)
[Dunham M. M., Vorobyov E. I., 2012, ApJ, 747, 52](http://dx.doi.org/10.1088/0004-637X/747/1/52)
[Dunhill A. C., Cuadra J., Dougados C., 2015, MNRAS, 448, 3545](http://dx.doi.org/10.1093/mnras/stv284)
[Dutrey A., Guilloteau S., Simon M., 1994, A&A, 286, 149](https://ui.adsabs.harvard.edu/abs/1994A&A...286..149D)
[Evans Neal J. I., et al., 2009, ApJS, 181, 321](http://dx.doi.org/10.1088/0067-0049/181/2/321)
Frank A., et al., 2014, in Beuther H., Klessen R. S., Dullemond C. P., Henning T., eds, Protostars and Planets VI. p. 451 ( `[arXiv:1402.3553](http://arxiv.org/abs/1402.3553)` ),
[doi:10.2458/azu_uapress_9780816531240-ch020](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch020)
[Giannini T., et al., 2022, ApJ, 929, 129](http://dx.doi.org/10.3847/1538-4357/ac5a49)
[Hales A. S., et al., 2018, ApJ, 859, 111](http://dx.doi.org/10.3847/1538-4357/aac018)
[Hales A. S., et al., 2020, ApJ, 900, 7](http://dx.doi.org/10.3847/1538-4357/aba3c4)
[Harris R. J., Andrews S. M., Wilner D. J., Kraus A. L., 2012, ApJ, 751, 115](http://dx.doi.org/10.1088/0004-637X/751/2/115)
[Herbig G. H., 1966, Vistas in Astronomy, 8, 109](http://dx.doi.org/10.1016/0083-6656(66)90025-0)
[Herbig G. H., 2007, AJ, 133, 2679](http://dx.doi.org/10.1086/517494)
Jurdana-Šepić R., Munari U., Antoniucci S., Giannini T., Lorenzetti D., 2018,

[A&A, 614, A9](http://dx.doi.org/10.1051/0004-6361/201732131)
[Kenyon S. J., Hartmann L. W., Strom K. M., Strom S. E., 1990, AJ, 99, 869](http://dx.doi.org/10.1086/115380)
[Kóspál Á., et al., 2017, ApJ, 843, 45](http://dx.doi.org/10.3847/1538-4357/aa7683)
[Kratter K., Lodato G., 2016, ARA&A, 54, 271](http://dx.doi.org/10.1146/annurev-astro-081915-023307)
[Kraus A. L., Ireland M. J., Martinache F., Hillenbrand L. A., 2011, ApJ, 731,](http://dx.doi.org/10.1088/0004-637X/731/1/8)

[8](https://ui.adsabs.harvard.edu/abs/2011ApJ...731....8K)

[Kraus A. L., Ireland M. J., Hillenbrand L. A., Martinache F., 2012, ApJ, 745,](http://dx.doi.org/10.1088/0004-637X/745/1/19)

[19](https://ui.adsabs.harvard.edu/abs/2012ApJ...745...19K)

[Kuffmeier M., Goicovic F. G., Dullemond C. P., 2020, A&A, 633, A3](http://dx.doi.org/10.1051/0004-6361/201936820)
[Kuffmeier M., Dullemond C. P., Reissl S., Goicovic F. G., 2021, A&A, 656,](http://dx.doi.org/10.1051/0004-6361/202039614)
[A161](https://ui.adsabs.harvard.edu/abs/2021A&A...656A.161K)


MNRAS **000**, 1–13 (2023)



[Kuruwita R. L., Federrath C., Haugbølle T., 2020, A&A, 641, A59](http://dx.doi.org/10.1051/0004-6361/202038181)
[Lai D., Muñoz D. J., 2022, arXiv e-prints, p. arXiv:2211.00028](https://ui.adsabs.harvard.edu/abs/2022arXiv221100028L)
[Larson R. B., 1972, MNRAS, 156, 437](http://dx.doi.org/10.1093/mnras/156.4.437)
[Lee A. T., Offner S. S. R., Kratter K. M., Smullen R. A., Li P. S., 2019, ApJ,](http://dx.doi.org/10.3847/1538-4357/ab584b)

[887, 232](https://ui.adsabs.harvard.edu/abs/2019ApJ...887..232L)

[Lodato G., Clarke C. J., 2004, MNRAS, 353, 841](http://dx.doi.org/10.1111/j.1365-2966.2004.08112.x)

Mathieu R. D., Stassun K., Basri G., Jensen E. L. N., Johns-Krull C. M.,

[Valenti J. A., Hartmann L. W., 1997, AJ, 113, 1841](http://dx.doi.org/10.1086/118395)
Maureira M. J., Pineda J. E., Segura-Cox D. M., Caselli P., Testi L., Lodato
[G., Loinard L., Hernández-Gómez A., 2020, ApJ, 897, 59](http://dx.doi.org/10.3847/1538-4357/ab960b)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Menten K. M., Reid M. J., Forbrich J., Brunthaler A., 2007, A&A, 474, 515](http://dx.doi.org/10.1051/0004-6361:20078247)

[Nealon R., Cuello N., Alexander R., 2020, MNRAS, 491, 4108](http://dx.doi.org/10.1093/mnras/stz3186)
Offner S. S. R., Dunham M. M., Lee K. I., Arce H. G., Fielding D. B., 2016,

[ApJ, 827, L11](http://dx.doi.org/10.3847/2041-8205/827/1/L11)
Offner S. S. R., Moe M., Kratter K. M., Sadavoy S. I., Jensen E. L. N., Tobin
[J. J., 2022, arXiv e-prints, p. arXiv:2203.10066](https://ui.adsabs.harvard.edu/abs/2022arXiv220310066O)
[Pérez S., et al., 2020, ApJ, 889, 59](http://dx.doi.org/10.3847/1538-4357/ab5c1b)
Postel A., Audard M., Vorobyov E., Dionatos O., Rab C., Güdel M., 2019,

[A&A, 631, A30](http://dx.doi.org/10.1051/0004-6361/201935601)
[Pueyo L., et al., 2012, ApJ, 757, 57](http://dx.doi.org/10.1088/0004-637X/757/1/57)
[Ragusa E., et al., 2021, MNRAS, 507, 1157](http://dx.doi.org/10.1093/mnras/stab2179)
[Reipurth B., 1985, A&AS, 61, 319](https://ui.adsabs.harvard.edu/abs/1985A&AS...61..319R)
[Reipurth B., Aspin C., 2004, ApJ, 608, L65](http://dx.doi.org/10.1086/422250)
[Reipurth B., Bally J., 1986, Nature, 320, 336](http://dx.doi.org/10.1038/320336a0)
[Rosotti G. P., Clarke C. J., 2018, MNRAS, 473, 5630](http://dx.doi.org/10.1093/mnras/stx2769)
[Ruíz-Rodríguez D., et al., 2017, MNRAS, 466, 3519](http://dx.doi.org/10.1093/mnras/stw3378)
Ruíz-Rodríguez D. A., Williams J. P., Kastner J. H., Cieza L., Leemker M.,
[Principe D. A., 2022, MNRAS, 515, 2646](http://dx.doi.org/10.1093/mnras/stac1879)
[Takami M., et al., 2019, ApJ, 884, 146](http://dx.doi.org/10.3847/1538-4357/ab43c8)
[Tobin J. J., et al., 2016a, Nature, 538, 483](http://dx.doi.org/10.1038/nature20094)
[Tobin J. J., et al., 2016b, ApJ, 818, 73](http://dx.doi.org/10.3847/0004-637X/818/1/73)
[Tobin J. J., et al., 2020, ApJ, 890, 130](http://dx.doi.org/10.3847/1538-4357/ab6f64)
[Tobin J. J., et al., 2022, ApJ, 925, 39](http://dx.doi.org/10.3847/1538-4357/ac36d2)
[Vorobyov E. I., Basu S., 2005, ApJ, 633, L137](http://dx.doi.org/10.1086/498303)
[Vorobyov E. I., Basu S., 2015, ApJ, 805, 115](http://dx.doi.org/10.1088/0004-637X/805/2/115)
[Vorobyov E. I., Elbakyan V. G., Liu H. B., Takami M., 2021, A&A, 647, A44](http://dx.doi.org/10.1051/0004-6361/202039391)
[Weaver E., Isella A., Boehler Y., 2018, ApJ, 853, 113](http://dx.doi.org/10.3847/1538-4357/aaa481)
[Zhu Z., Hartmann L., Gammie C., McKinney J. C., 2009, ApJ, 701, 620](http://dx.doi.org/10.1088/0004-637X/701/1/620)
[Zhu Z., Hartmann L., Nelson R. P., Gammie C. F., 2012, ApJ, 746, 110](http://dx.doi.org/10.1088/0004-637X/746/1/110)
[Zurlo A., et al., 2020a, MNRAS, 496, 5089](http://dx.doi.org/10.1093/mnras/staa1886)

[Zurlo A., et al., 2020b, A&A, 633, A119](http://dx.doi.org/10.1051/0004-6361/201936891)

[Zurlo A., et al., 2021, MNRAS, 501, 2305](http://dx.doi.org/10.1093/mnras/staa3674)


**APPENDIX A:** **EFFECTS OF CONTINUUM**

**OVER-SUBTRACTION**


To evaluate the effects of continuum over-subtraction, we generated
spatial profiles for each disk using [12] CO moment 0 maps at small
scales before and after continuum subtraction. We created cuts that

crossed the semi-major axis of each disk (see red lines in Figure
A1, top panels) for this purpose. Figure A1, top-left panel displays
moment 0 maps before continuum removal, while the top-right panel
shows the same maps after this process. The comparison between
these effects is better visualized in the bottom panels, where continuum emission (magenta diamonds/lines) has a similar shape as [12] CO
before continuum subtraction (orange crosses/lines), but shifted in
flux, for both disks. The spatial profile subtractions are displayed
by black lines. However, they display higher fluxes when compared
to the spatial profiles produced after continuum subtraction (bluefilled circles/lines). Additionally, the continuum was overestimated

by foreground optical depth molecular lines that absorbed continuum emission and then propagated to the _uvcontsub_ CASA task. The
"holes" or cavities seen in the top-right panel could potentially be
diminished by manually adding back some of the lost line signal,
but this would only create a fake signal at the level of noise. Thus,
optically thinner lines must be used to obtain the real signal of disks
in moment 0 and 1 maps.


**APPENDIX B:** [12] **CO,** [13] **CO AND C** [18] **O CHANNEL MAPS**
**WITH CONTOURS AND THE EFFECT OF CLOUD**

**CONTAMINATION**


This appendix presents the [12] CO, [13] CO, and C [18] O channel maps
with contour plots (see Figures B1 and B2). To visualize the signals
and corresponding flux values using a color bar, we also provide
versions of the same channel maps without contours (see Figures 4
and C1).
Figure B1 shows the 3-rms significant southern arcs (velocity
channels from -6 km/s to 1 km/s) and northern arcs (velocity channels from 5 km/s to 18 km/s). However, cloud contamination affects
channels between 2 km/s and 6 km/s. These channels were not used in

the creation of large-scale moment maps. Channel 6 km/s shows the
most evidence of cloud contamination, with contour plots showing
innermost flux values near the disks (marked by the central orange
star). It also shows some significant contours on both horizontal extremes, which can be tracers of the filtered signals using only the
main array data. The data partially trace features that, due to their
large extension, require a combination of the ALMA main and single
dish arrays to recover extended flux emission.
In Figure B2, the [13] CO channel maps are heavily marked by 3rms black contours, which show the significant gas signal on each
channel. Specifically, channels from 2.20 km/s to 6.10 km/s indicate
gas infalling clumps near where the disks are located, but also show
random/scattered signals far from the disks due to cloud contamination.
The C [18] O channel maps represented in Figure B3 are also heavily
marked by 3-rms black contours. Channels from 2.80 km/s to 4.60
km/s indicate gas infalling clumps near where the disks are located,
but also show random/scattered signals far from the disks due to cloud
contamination. Other channels are affected by cloud contamination
or lack a significant signal.


**APPENDIX C:** **EXTRA CHANNEL MAPS**


The [13] CO (large scale), C [18] O (large scale), [12] CO (small scale and
with continuum subtracted), [13] CO (small scale and with continuum
subtracted), and C [18] O (small scale and with continuum subtracted)
channel maps are displayed in Figs. C1, C2, C3, C4, and C5, respectively.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



_ALMA resolves the binary HBC 494_ 13


MNRAS **000**, 1–13 (2023)

14 _P. H. Nogueira et al._


**Figure A1.** The top panels show the [12] CO moment 0 maps before (left) and after (right) continuum removal, along with their spatial profiles. The moment 0
contours represent values of 50, 75, 100, 150, and 200 times the rms (∼0.06 mJy/beam.km/s). The red lines trace the axis used to create spatial profiles, which
can be seen in the bottom panels. The bottom left panel shows the spatial profile of the HBC 494 N disk, while the bottom right panel shows that of the HBC
494 S disk. The vertical black dashed lines indicate the center of the disks. The orange crosses/lines represent spatial profiles before the continuum subtraction,
created using the red line axis in the top panel, left. The magenta diamonds/lines represent the continuum spatial profile. The black lines represent the subtraction
between the [12] CO+continuum and the continuum spatial profiles for each disk. The dark blue filled circles/lines represent spatial profiles after the continuum
subtraction, created using the red line axis in the top panel, right.


MNRAS **000**, 1–13 (2023)

-7°27'20"


25"


30"


35"



_ALMA resolves the binary HBC 494_ 15


10













2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"





















25"


30"


35"



2000 au 2000 au 2000 au 2000 ~~a~~ u 2000 au


-7°27'20"





















25"


30"


35"



2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"



















8


6


4


2


0



25"


30"


35"


-7°27'20"


25"


30"


35"





5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



**Figure B1.** [12] CO channel maps of HBC 494 system with contours. The contours were displayed in black and they are equivalent to 3 times the rms of every
channel. The rms values were calculated using all data in each channel, through the CASA task _imstat_ . The peak flux values have reached up to 19 times the rms
values. The star in the center marks the position of the continuum disk around HBC 494 N.


MNRAS **000**, 1–13 (2023)

16 _P. H. Nogueira et al._


-7°27'20"


25"


30"


35"











2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"





















25"


30"


35"



2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"





















10


8


6


4


2


0



25"


30"


35"



2000 au 2000 au 2000 au 2000 au 2000 a ~~u~~


-7°27'20"



















25"


30"


35"


-7°27'20"


25"


30"


35"





5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



**Figure B2.** [13] CO channel maps of HBC 494 system with contours. The contours were displayed in black and they are equivalent to 3 times the rms of every
channel. The rms values were calculated using all data in each channel, through the CASA task _imstat_ . The peak flux values have reached up to 11 times the rms
values. The star in the center marks the position of the continuum disk around HBC 494 N.


MNRAS **000**, 1–13 (2023)

-7°27'20"


25"


30"


35"



_ALMA resolves the binary HBC 494_ 17


6













2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"





















25"


30"


35"



2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"





















5


4


3


2


1


0



25"


30"


35"



2000 au 2000 au 2000 au 2000 au 2000 au


-7°27'20"



















25"


30"


35"


-7°27'20"


25"


30"


35"





5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



**Figure B3.** C [18] O channel maps of HBC 494 system with contours. The contours were displayed in black and they are equivalent to 3 times the rms of every
channel. The rms values were calculated using all data in each channel, through the CASA task _imstat_ . The peak flux values have reached up to 13 times the rms
values. The star in the center marks the position of the continuum disk around HBC 494 N.


MNRAS **000**, 1–13 (2023)

18 _P. H. Nogueira et al._


-7°27'20"


25"


30"


35"











-7°27'20"





















25"


30"


35"



-7°27'20"





















10


8


6


4


2


0



25"


30"


35"



-7°27'20"



















25"


30"


35"


-7°27'20"


25"


30"


35"




|100km/s<br>.<br>2000 au|130km/s<br>.<br>2000 au|160km/s<br>.<br>2000 au|190km/s<br>.<br>2000 au|220km/s<br>.<br>2000 au|Col6|
|---|---|---|---|---|---|
|2.50 km/s<br>2000 au|2.80 km/s<br>2000 au|3.10 km/s<br>2000 au|3.40 km/s<br>2000 au|3.70 km/s<br>2000 au|3.70 km/s<br>2000 au|
|4.00 km/s<br>2000 au|4.30 km/s<br>2000 au|4.60 km/s<br>2000 au|4.90 km/s<br>2000 au|5.20 km/s<br>2000 au|5.20 km/s<br>2000 au|
|5.50 km/s<br>2000 au|5.80 km/s<br>2000 au|6.10 km/s<br>2000 au|6.40 km/s<br>2000 au|6.70 km/s<br>2000 au|6.70 km/s<br>2000 au|
|7.00 km/s<br>2000 au|7.30 km/s<br>2000 au|7.60 km/s<br>2000 au|7.90 km/s<br>2000 au|8.20 km/s<br>2000 au|8.20 km/s<br>2000 au|



5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



**Figure C1.** [13] CO channel maps of HBC 494 system. The star in the center marks the position of the continuum disk around HBC 494 N.


MNRAS **000**, 1–13 (2023)

-7°27'20"


25"


30"


35"



_ALMA resolves the binary HBC 494_ 19


6













-7°27'20"





















25"


30"


35"



-7°27'20"





















5


4


3


2


1


0



25"


30"


35"



-7°27'20"



















25"


30"


35"


-7°27'20"


25"


30"


35"




|100km/s<br>.<br>2000 au|130km/s<br>.<br>2000 au|160km/s<br>.<br>2000 au|190km/s<br>.<br>2000 au|220km/s<br>.<br>2000 au|Col6|
|---|---|---|---|---|---|
|2.50 km/s<br>2000 au|2.80 km/s<br>2000 au|3.10 km/s<br>2000 au|3.40 km/s<br>2000 au|3.70 km/s<br>2000 au|3.70 km/s<br>2000 au|
|4.00 km/s<br>2000 au|4.30 km/s<br>2000 au|4.60 km/s<br>2000 au|4.90 km/s<br>2000 au|5.20 km/s<br>2000 au|5.20 km/s<br>2000 au|
|5.50 km/s<br>2000 au|5.80 km/s<br>2000 au|6.10 km/s<br>2000 au|6.40 km/s<br>2000 au|6.70 km/s<br>2000 au|6.70 km/s<br>2000 au|
|7.00 km/s<br>2000 au|7.30 km/s<br>2000 au|7.60 km/s<br>2000 au|7.90 km/s<br>2000 au|8.20 km/s<br>2000 au|8.20 km/s<br>2000 au|



5 [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



5 [s] [h] 40 [m] 28.0 [s] 27.5 [s] 27.0 [s]



**Figure C2.** C [18] O channel maps of HBC 494 system.



MNRAS **000**, 1–13 (2023)

20 _P. H. Nogueira et al._



-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"





















































5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



10


8


6


4


2


0



**Figure C3.** [12] CO channel maps of HBC 494 system, small-scale, after removing the continuum contribution.


MNRAS **000**, 1–13 (2023)

_ALMA resolves the binary HBC 494_ 21


10



-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"



|0 .00 km/s<br>50 au|1 .00 km/s<br>50 au|2 .00 km/s<br>50 au|
|---|---|---|
|3.00 km/s<br>50 au|4.00 km/s<br>50 au|5.00 km/s<br>50 au|
|6.00 km/s<br>50 au|7.00 km/s<br>50 au|8.00 km/s<br>50 au|
|9.00 km/s<br>50 au|10.00 km/s<br>50 au|5h40m27.46s<br>27.45s<br>27.44s<br>11.00 km/s<br>50 au|


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



8


6


4


2


0



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



**Figure C4.** [13] CO channel maps of HBC 494 system, small-scale, after removing the continuum contribution.


MNRAS **000**, 1–13 (2023)

22 _P. H. Nogueira et al._



-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"


-7°27'29.5"


29.6"


29.7"


29.8"


29.9"



|0 .00 km/s<br>50 au|1 .00 km/s<br>50 au|2 .00 km/s<br>50 au|
|---|---|---|
|3.00 km/s<br>50 au|4.00 km/s<br>50 au|5.00 km/s<br>50 au|
|6.00 km/s<br>50 au|7.00 km/s<br>50 au|8.00 km/s<br>50 au|
|9.00 km/s<br>50 au|10.00 km/s<br>50 au|5h40m27.46s<br>27.45s<br>27.44s<br>11.00 km/s<br>50 au|


5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



5 [h] 40 [m] 27.46 [s] 27.45 [s] 27.44 [s]



7


6


5


4


3


2


1


0



**Figure C5.** C [18] O channel maps of HBC 494 system, small-scale, after removing the continuum contribution.


MNRAS **000**, 1–13 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[0]",
  "value": "J2000 05h40m27.448s -07d27m29.65s",
  "failed_quote": "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007), and has been classified as a FUor1."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "414±7 pc",
  "failed_quote": "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007), and has been classified as a FUor1."
 },
 {
  "path": "science.targets[0].distance_source.evidence[0]",
  "value": "Menten et al. 2007",
  "failed_quote": "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007), and has been classified as a FUor1."
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "Central frequencies: 230.543 (12CO J=2-1), 233.010 (continuum), 220.403 (13CO J=2-1), 219.565 (C18O J=2-1), and 218.010 (continuum) GHz; min spectral resolution: 15.259 kHz (~0.02 km/s) for 12CO, 30.518 kHz (~0.04 km/s) for 13CO and C18O",
  "failed_quote": "The central frequencies of each spectral window were: 230.543 (to cover the transition 12CO J=2-1), 233.010 (continuum), 220.403 (13CO J=2-1), 219.565 (C18O J=2-1), and 218.010 (continuum) GHz."
 },
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "12CO",
  "failed_quote": "The central frequencies of each spectral window were: 230.543 (to cover the transition 12CO J=2-1), 233.010 (continuum), 220.403 (13CO J=2-1), 219.565 (C18O J=2-1), and 218.010 (continuum) GHz."
 },
 {
  "path": "data.lines_targeted[1].evidence[0]",
  "value": "13CO",
  "failed_quote": "The central frequencies of each spectral window were: 230.543 (to cover the transition 12CO J=2-1), 233.010 (continuum), 220.403 (13CO J=2-1), 219.565 (C18O J=2-1), and 218.010 (continuum) GHz."
 },
 {
  "path": "data.lines_targeted[2].evidence[0]",
  "value": "C18O",
  "failed_quote": "The central frequencies of each spectral window were: 230.543 (to cover the transition 12CO J=2-1), 233.010 (continuum), 220.403 (13CO J=2-1), 219.565 (C18O J=2-1), and 218.010 (continuum) GHz."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Distance to HBC 494 of 414±7 pc",
  "failed_quote": "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007), and has been classified as a FUor1."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Fit 2D Gaussians to the resolved binary components in the continuum image using CASA imfit, derive disk inclinations from the deconvolved aspect ratios, and extract radial brightness profiles in elliptical apertures.",
  "failed_quote": "The inclinations are calculated using the aspect ratios of the disks. These are assumed as projected circular disks when face-on, thus elliptical when inclined: 𝑖 = arccos (𝑏/𝑎), where “b\" and “a\" are the semi-minor and semi-major axes, respectively."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Disks are circular when face-on and elliptical when inclined",
  "failed_quote": "These are assumed as projected circular disks when face-on, thus elliptical when inclined: 𝑖 = arccos (𝑏/𝑎)"
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Compute dust mass from integrated 1.3 mm continuum flux density using the optically thin isothermal dust emission formula, and multiply by gas-to-dust ratio for gas mass.",
  "failed_quote": "Thus, assuming standard disks, we can use the observed fluxes to estimate the dust masses of HBC 494 N and S. For that, we use the following formula (as in Beckwith et al. 1990; Andrews & Williams 2005; Cieza et al. 2018): 𝑀dust = 𝐹𝜈 𝑑2 / 𝑘𝜈 𝐵𝜈 (𝑇dust)"
 },
 {
  "path": "results_numeric[16].evidence[0]",
  "value": "HBC 494 N inclination = 37.16 (37.2 in Table 2) deg",
  "failed_quote": "It resulted in 37.16 ± 2.36 degrees inclination for HBC 494 N and 44.65 ± 3.27 for HBC 494 S."
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "HBC 494 S inclination = 44.65 (44.7 in Table 2) deg",
  "failed_quote": "It resulted in 37.16 ± 2.36 degrees inclination for HBC 494 N and 44.65 ± 3.27 for HBC 494 S."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "At large scales (8000 au), 12CO traces wide-angle (~150 deg) bipolar outflow arcs while 13CO and C18O trace a rotating, infalling, and expanding envelope with a rotation axis nearly perpendicular to the outflow.",
  "failed_quote": "The channel maps (Figures 4, C1 and C2) show southern and northern 12CO wide-angle arcs (∼ 150◦) and no clear signal of large structures from the other molecular lines."
 }
]
```
