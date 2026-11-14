# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.499.3909Y\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–12 (2020) Preprint 12 August 2020 Compiled using MNRAS L [A] TEX style file v3.0

###### **Evidence for a jet and outflow from Sgr A*:** **a continuum and spectral line study**


F. Yusef-Zadeh [1][⋆] M. Royster [1] M. Wardle [2] W. Cotton [3] D. Kunneriath [3]



I. Heywood [4][,][5][,][6] & J. Michail [1]

1 _CIERA,_ _Department_ _of_ _Physics_ _and_ _Astronomy_ _Northwestern_ _University,_ _Evanston,_ _IL_ _60208,_ _USA_
2 _Dept_ _of_ _Physics_ _and_ _Astronomy,_ _Research_ _Centre_ _for_ _Astronomy,_ _Astrophysics_ _and_ _Astrophotonics,_ _Macquarie_ _University,_ _Sydney_ _NSW_ _2109,_ _Au_
3 _National_ _Radio_ _Astronomy_ _Observatory,_ _Charlottesville,_ _VA,_ _22903,_ _USA_
4 _Astrophysics,_ _Department_ _of_ _Physics,_ _University_ _of_ _Oxford,_ _Keble_ _Road,_ _Oxford,_ _OX1_ _3RH,_ _UK_
5 _Department_ _of_ _Physics_ _and_ _Electronics,_ _Rhodes_ _University,_ _PO_ _Box_ _94,_ _Makhanda,_ _6140,_ _South_ _Africa_
6 _South_ _African_ _Radio_ _Astronomical_ _Observatory,_ _2_ _Fir_ _Street,_ _Black_ _River_ _Park,_ _Observatory,_ _Cape_ _Town,_ _7925,_ _South_ _Africa_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
We study the environment of Sgr A* using spectral and continuum observations with
the ALMA and VLA. Our analysis of sub-arcsecond H30α, H39α, H52α and H56α
line emission towards Sgr A* confirm the recently published broad peak ∼ 500 km
s [−][1] spectrum toward Sgr A*. We also detect emission at more extreme radial velocities
peaking near −2500 and 4000 km s [−][1] within 0.2 [′′] . We then present broad band radio
continuum images at multiple frequencies on scales from arcseconds to arcminutes. A
number of elongated continuum structures lie parallel to the Galactic plane, extending
from ∼ 0.4 [′′] to ∼ 10 [′] . We note a nonthermal elongated structure on an arcminute scale
emanating from Sgr A* at low frequencies between 1 and 1.4 GHz where thermal
emission from the mini-spiral is depressed by optical depth effects. The position angle
of this elongated structure and the sense of motion of ionized features with respect
to Sgr A* suggest a symmetric, collimated jet emerging from Sgr A* with an opening
angle of ∼ 30 [◦] and a position angle of ∼60 [◦] punching through the medium before
accelerating a significant fraction of the orbiting ionized gas to high velocities. The
jet with estimated mass flow rate ∼ 1.4 × 10 [−][5] _M_ ⊙ yr [−][1] emerges perpendicular to the
equatorial plane of the accretion flow near the event horizon of Sgr A* and runs along
the Galactic plane. To explain a number of east-west features near Sgr A*, we also
consider the possibility of an outflow component with a wider-angle launched from the
accretion flow at larger radii.


**Key** **words:** accretion, accretion disks — black hole physics — Galaxy: center



**1** **INTRODUCTION**


Our relative proximity to the supermassive black hole, Sgr
A*, at the center of the Galaxy provides a laboratory in
which to investigate the processes that lead to accretion and
ejection flows in the low luminosity nuclei of galaxies.The
bolometric luminosity of Sgr A* powered by the magnetized
accretion flow is several orders of magnitude below the luminosity estimated from the accretion of ionized stellar winds
feeding Sgr A*. Two broad classes of models have addressed
the low luminosity of Sgr A*. The first describes a radiatively inefficient accretion flow (RIAF) which argues that
only a fraction of the initially infalling material from stellar


⋆ E-mail: zadeh@northwestern.edu


© 2020 The Authors



winds fall onto Sgr A* and the rest is driven off as an outflow
from Sgr A* (e.g. Yuan et al. 2014; Quataert 2004; Wang
et al. 2013). Alternatively, most of the gas approaching Sgr
A* may be pushed away as part of a jet or an outflow (e.g.
Falcke and Markoff 2000; Becker et al. 2011; Yusef-Zadeh
et al. 2016). In either case, the accretion rate is well below
the Bondi accretion rate. The presence of a jet constrains
the accretion flow model and its interaction with the surrounding gas provides constraints on the jet power. Thus it
is important to establish if there is indeed a jet arising from
Sgr A*.
Recent H30α millimeter recombination line (mmRL)
observations using Atacama Large Millimeter/submillimeter
Array (ALMA) detected high velocity ionized gas associated with Sgr A*. A double peak mmRL was detected in
the spectrum of Sgr A* showing evidence of blue and red

2 _Yusef-Zadeh_ _et_ _al._


shifted ionized gas from the inner 0.23 [′′] (9 milli-pc) of Sgr A*
(Murchikova et al. 2019). The full linewidth of the velocity
profile was estimated to be 2200 km s [−][1] with peak velocity ±500 km s [−][1] . The ionized features have a position angle
(PA) of ∼ 64 [◦], directed roughly along the Galactic plane.
This double-lobed ionized structure ∼ 3600 _R_ s from Sgr A*
is interpreted as a tracer of a cool (∼ 10 [4] K) accretion flow
(Murchikova et al. 2019).
Another recent study detected high velocity ionized gas
with velocities ranging between –480 and –300 km s [−][1] SW
of Sgr A* and within 2 [′′] − 3 [′′] (0.08–0.12 pc) (Royster et al.
2019). These had been the highest radial velocities of diffuse ionized gas beyond the inner 1 [′′] of Sgr A*. To the NE
of Sgr A*, a number of red-shifted isolated features associated with cometary stellar sources have also been reported
(Royster et al. 2019). The blue- and red-shifted features were
interpreted in terms of the interaction of a collimated outflow with a position angle ∼ 60 [◦] East of North with respect
to Sgr A*. An outflow rate of 2×10 [−][7] or 4×10 [−][5] _M_ ⊙ yr [−][1] was
estimated for a relativistic jet-driven outflow from Sgr A* or
collimated stellar winds, respectively. Similar to this picture,
several past studies have also argued for the presence of an
outflow either due to a wind or a jet from Sgr A* in the
direction either along the Galactic plane or other directions,
details of which are provided below. There is currently no
direct evidence for a jet emanating from Sgr A* in the highly
confused region of the Galactic center containing: the minispiral feature tracing both ionized and cool dense material,
the Sgr A East SNR tracing nonthermal emission and high
density of evolved and young mass-losing stars orbiting Sgr
A*. However, morphological and kinematical studies infer
sites where the outflowing material emerging from Sgr A*
interact with orbiting gas and stars. A brief summary of the
results of these investigations indicate a collimated outflow
arising from Sgr A*, as we describe them next from small to
large scales.

   - Polarimetric near-IR measurements of flare emission from Sgr A* indicate a preferred direction of the polarization angle Eckart et al. (2006); Meyer, et al. (2007); Zamaninasab et al. (2011). These measurements give a statistically significant mean polarization angle of 60 [◦] (240 [◦] ) ± 20 [◦]

(Eckart et al. 2006). An ejection model of plasma blobs
has been considered to explain flaring activity of Sgr A*
(Yusef-Zadeh et al. 2006). If this arises in a jet, the PA of
synchrotron-emitting ejected material should be in the direction of the preferred polarization angle, thus directed on
both sides along the Galactic plane.

   - A chain of ionized blobs seen in radio continuum
leads from Sgr A* to a hole in the distribution of orbiting
ionized gas, the“mini-cavity” Wardle, & Yusef-Zadeh (1992).
The mini-cavity is kinematically disturbed and is located
about ∼ 3 [′′] SW of Sgr A*. The blobs, connected by a ridge
of emission to Sgr A* could be produced by an outflow from
Sgr A*.

   - Muzi´c et al. (2007, 2010); Peißker et al. (2019) reported the discovery of head-tail cometary stellar sources
within a few arcseconds to the SW of Sgr A*. These sources
display bow-shock structures pointing toward Sgr A*. The
PAs of these four stellar sources, X1, X3, X7 and X8, with
respect to Sgr A* are greater than 45 [◦] . There are also
cometary radio sources, f1 to f3, found to the NE of Sgr
A* with similar PAs (Yusef-Zadeh et al. 2016). Muzi´c et



al. (2010) argue for a collimated wind-driven outflow arising roughly parallel to the Galactic plane to account for the
cometary features X3 and X7.

   - Yusef-Zadeh et al. (2017) reported a 2.5 [′′] × 1.5 [′′]

(0.1×0.06 pc) mm halo surrounding Sgr A*. We interpreted
this diffuse halo as being generated by synchrotron emission
from relativistic electrons. The halo has an X-ray counterpart (Wang et al. 2013) and coincides with a dust cavity with
the low infrared extinction of ∼2.4 magnitudes. Two dust
cavities within 2 [′′] are elongated and run along the Galactic
plane (Sch¨odel et al. 2010; Yusef-Zadeh et al. 2017). The spatial anti-correlation of the halo emission and the low near-IR

extinction suggests evidence of an outflow sweeping up the
interstellar material, creating a dust cavity within 2 arcsec
of Sgr A* along the Galactic plane (Yusef-Zadeh et al. 2017).

   - Peißker et al. (2020) reported a number of dusty
stellar sources with near-infrared excess and a large [FeIII]
to Brγ line ratio. This is indicative of a spatial distribution
of sources with a high abundance to ionization parameter
by the interaction of a non-spherical outflow with the atmosphere of dusty stellar sources. The line ratio suggests an
excitation by an external non-spherical wind (Peißker et al.

2020).

    - Narrow and long cometary tails (fibrils) at millimeter are identified with two mass-losing young stars AF and
AFNW. These fibrils are pointing in the direction of Sgr
A* along the Galactic plane(Yusef-Zadeh et al. 2017). These
characteristics suggest an outflow is responsible for creating:
a synchrotron halo, dust cavities and cometary tails (YusefZadeh et al. 2017).

   - Morphological studies of high resolution radio continuum observations of the inner few pc of Sgr A* indicate
a faint continuous linear structure centered on Sgr A* with
a PA∼ 60 [◦] Yusef-Zadeh et al. (2012). Several blobs of radio emission were also identified along the continuous linear
structure. The extension of this feature terminated symmetrically by two linearly polarized structures ∼ 75 [′′] (3 pc) from
Sgr A*. Yusef-Zadeh et al. (2012) considered a mildly relativistic jet from Sgr A* with an outflow rate of 10 [−][6] _M_ ⊙
yr [−][1] to explain disturbed kinematics and enhanced FeII/III
line emission from the minicavity (Lutz et al. 1993).

   - Large-scale morphological studies of radio continuum emission showed a striking tower of nonthermal radio emission 150 [′′] (6 pc) extending away from Sgr A* at
PA∼ 50 [◦] −60 [◦] (Yusef-Zadeh et al. 2016). The tower structure
was argued to be the result of an interaction of a jet from
Sgr A* with the Sgr A East SNR which itself lies behind the
mini-spiral (Yusef-Zadeh et al. 1986; Pedlar et al. 1989). The
jet appears to drag a portion of the shell to the NE along
the Galactic plane. A jet outflow rate of 10 [−][7] _M_ ⊙ yr [−][1] is
needed to explain the origin of the tower (Yusef-Zadeh et al.
2016).
All the above studies generally indicate a collimated
jet from Sgr A* directed roughly along the Galactic plane.
There are other claims of a jet emanating from Sgr A* on
different scales with discrepant values of the inclination and
position angle of the jet. Most of these measurements indicate an outflow with an axis projected on the sky perpendicular to the Galactic plane or within 30 [◦] of the Galactic
plane (Yusef-Zadeh et al. (1986); Markoff et al. (2007); Broderick et al. (2011); Zamaninasab et al. (2011); Muno et al.
(2008); Li et al. (2013). On a milli-arcsecond (mas) scale, a


MNRAS **000**, 1–12 (2020)

number of VLBI measurements have also characterized the
size and PA of millimeter emission from Sgr A*. Recent 86
GHz continuum measurements of Sgr A* using ALMA and
VLBI indicate a size scale of of ∼ 0.2 mas and appears to
be elliptical with major axis PA∼ 84 [◦] (Issaoun et al. 2019).
Other mas-resolution 86 GHz measurements of Sgr A* also
indicate PAs ranging between 75 [◦] and 83 [◦] (Shen et al. 2005;
Lu et al. 2009; Johnson et al. 2018; Ortiz-Le´on et al. 2016;
Brinkerink et al. 2019).


Discrepant values of the PA of the jet are seen on small
scales which may result from the fact that data reduction is
challenging for a strong, time variable source on an hourly
time scale. In addition, Sgr A* has an inverted spectrum,
thus continuum imaging over a broad bandwidth has to account for the spectral index of Sgr A*. Confusing sources add
another challenge in searching for a large-scale jet with an established PA using continuum data. Lastly, the _uv_ converge
of interferometric measurements will provide additional limitations in imaging this source where there is emission on
a wide range of angular scales. However, detection of high
velocity ionized gas associated with Sgr A* is significant in
opening a new window to study processes that lead to accretion or ejection. The limiting factor is proper continuum
subtraction due to frequency-dependent time variability and
continuum flux of Sgr A* as well as a lack of sufficient line
free channels for continuum subtraction.


Unlike previous measurements, this study combines
spectroscopic and radio continuum data at multiple frequencies with different spatial resolutions. In particular, to detect
recombination line emission from Sgr A*, we use a different
technique, multiple transitions of hydrogen atom and a wider
spectral coverage. We use a technique in which the continuum subtraction is applied in the image plane toward Sgr A*
unlike the uv plane where the subtraction is done over the
entire field with contributions from multiple sources. These
new ALMA and VLA measurements have broader velocity coverage than earlier measurements (Murchikova et al.
2019). Amazingly, the lines we detect are so broad that the
measurements are still limited by not being able to conclusively identify line free channels from Sgr A*. Thus, we
make some assumptions and the results indicate that the 10
milli-pc (mpc) scale broad mmRL emission from Sgr A* is a
small extension of arcsecond and arc-minute scale structures

inferred from past radio continuum studies.


We also present new multi-wavelength radio continuum
images of Sgr A*. The time variability of Sgr A* due to flaring activity and spectral variation of Sgr A* across broad
observing bands can also lead to radio artifacts that can
easily be confused with real features. Given that high frequency features near Sgr A* are contaminated by phase and
amplitude errors, we analyze numerous data sets and describe features that persist and appear at different frequencies, epochs, and VLA array configurations, as these are unlikely to be generated by imaging artifacts.


The outline of this paper is as follows. In section 2, we
first describe and analyze spectroscopic data reduction using
both ALMA and VLA. In section 3, we focus on radio continuum data analysis of high and low-frequency measurements.
In section 4, we interpret the results of these measurements
before we provide a summary.


MNRAS **000**, 1–12 (2020)



3


**2** **SPECTROSCOPIC** **DATA** **ANALYSIS** **AND**

**RESULTS**


**2.1** **Data** **Preparation**


We examined the spectrum of Sgr A* in four different hydrogen recombination lines utilizing datasets from both ALMA
and the VLA. The data reduction techniques used to make
the final spectra of H30α, H39α, H52α and H56α line emission are described below.


_2.1.1_ _H30_ α _ALMA_ _Data_


Our earlier ALMA H30α mmRL observations of the Galactic
center were described in detail by Royster et al. (2019). H30α
is the same transition used by Murchikova et al. (2019). Our
ALMA data provides an independent means to confirm the
double-peak spectrum of Sgr A* because of the different observational setup and epochs. Observations were carried out
as part of a long multi-wavelength monitoring campaign of
Sgr A*, thus achieving excellent sensitivity to weak struc
tures.
The calibrated Band 6 archival data (project code
2015.A.00021.S) was observed on 2016 July 12/13 in Cycle 3.
The dataset was first combined along all spectral windows
prior to deriving and applying phase self-calibration solutions three times with decreasing time intervals before a final
phase and amplitude self-calibration solution was derived.
The image cube with a σ = 0.4 mJy per 3 km s [−][1] channel
was constructed after applying the self-calibration solution.
Continuum subtraction was not performed in the _uv_ plane,
instead the image cube was constructed immediately after
self-calibration. The data cube is made up of 45 km s [−][1] channels ranging from −3770 to +700 km s [−][1] over two spectral
windows relative to the rest frequency of H30α at 231.9 GHz.
A spectrum (which includes the continuum) was obtained from the inner 0.23 [′′] towards the position of Sgr A*
with a synthesized beam of 0.30 [′′] × 0.33 [′′] . In order to equalize the flux between the two spectral windows that are used
here, the five channels on the edge of each window were averaged to determine the relative difference. This resulted in
the need to multiply the lower velocity window by a factor of
1.0052 before concatenating the spectra together. Line free
channels were then chosen by inspection in order to subtract
the continuum emission.


_2.1.2_ _H39_ α _ALMA_ _Data_


We used archival ALMA data (project code 2011.0.00887.S,
PI Heino Falcke) observed on May 18, 2012 with 19 antennas using band 3. The calibrated dataset provided by the
ALMA archive consists of 4 spectral windows, each with 2
GHz bandwidth and 15.625 MHz channel width. Titan and

Neptune were used as flux calibrators, and J1924-292 and
NRAO530 were used as the bandpass and phase calibrator, respectively. We used CASA 5.4.0-74 to split out the
Band 3 spectral windows (spws), self-calibrate the measurement set and image the continuum as well as the H39α and
H49β line cubes at rest frequencies 106.737 GHz and 105.302
GHz, respectively. We performed two rounds of phase selfcalibration, deriving solutions per spectral window in the
first round and then for all spectral windows combined.

4 _Yusef-Zadeh_ _et_ _al._


_2.1.3_ _H52_ α _VLA_ _Data_


A-array observations were carried out in the (7mm) band on
2019, July 18 (19A-229). We used the 3-bit system and the
same calibration strategy as the 7mm (Q band) continuum
observations described in section 3.1.1. Phase self-calibration

was applied three times to all the data using the bright radio
source Sgr A*. The broad 8 GHz bandwidth is comprised of
64 spws, each having 64 channels of 2 MHz width. We imaged 12 individual spws close to the rest frequency of H52α
at 45.4538 GHz before continuum subtraction was applied.
These spectral windows correspond to a velocity range of∼
–4200 km s [−][1] to +6000 km s [−][1] .
Before a continuum was fitted and subtracted, it was
necessary to manually equalize the flux of each spectral window due to errors in flux calibration. We employed the following procedure beginning with the lowest frequency spectral window _j_ : (1) determine the ratio of the mean flux of
the last ten channels of spectral window _j_ with the mean
flux of the first ten channels of the next (higher frequency)
spectral window _j_ + 1, (2) multiply each channel of spectral window _j_ + 1 by this ratio to equalize it, (3) repeat the
previous steps but now starting with the newly equalized
spectral window _j_ + 1. The derived ratios used to normalize
the spws ranged from 0.9832 to 1.003. The spectral windows
were then concatenated as shown in Figure 3a.
A linear continuum was fit to the concatenated data
with channels with no strong line emission chosen between
–4200 to –3900 km s [−][1] and 5800 km s [−][1] to 6000 km s [−][1] . The

resultant subtracted spectra is shown in Figure 3b. Note
that although the absolute continuum flux is lost in Figure
3a, the line emission flux density is recovered in Figure 3b.


_2.1.4_ _H56_ α _VLA_ _Data_


We carried out A-array observations (19A-229) in the (9mm)
band on 2019, July 26. We used the 3-bit system and a
calibration strategy similar to that employed for the VLA
H52α data. Phase self-calibration was applied three times to
all the data using the bright radio source Sgr A*. The broad
8 GHz bandwidth is comprised of 64 spws, each having 64
channels of 2 MHz width. We imaged ten individual spws
close to the rest frequency of H56α at 36.466 GHz before
continuum subtraction. These spectral windows correspond
to a velocity range between ∼–4000 km s [−][1] and +6300 km
s [−][1] .

Continuum subtraction was performed with the same
technique that was applied to the H52α line data. A linear
continuum was fit to the concatenated data with channels
chosen between –4400 to –4150 km s [−][1] and 5800 km s [−][1] to
6000 km s [−][1] . The resultant with and without continuum

subtracted spectra are shown in Figure 4a,b, respectively.


**2.2** **Spectroscopic** **Results**


To confirm the results presented by Murchikova et al. (2019),
we used the four independent measurements of H30α, H39α,
H52α and H56α with different spectral setups. Despite having significantly broader spectral coverage than Murchikova
et al. (2019), it is still not clear where the true continuum is
because of a limited set of line free channels. Clearly, a dif


ferent spectral setup is required in the future to determine
true line free channels for proper continuum subtraction.


_2.2.1_ _H30_ α _Line_ _Emission_


We extracted H30α spectrum using the same scale size and
spectral resolution that were used by Murchikova et al.
(2019). However, our spectral coverage is wider than that
shown by Murchikova et al. (2019). As a result, we selected
two different sets of line free channels. The first was chosen to confirm the double-peak spectrum of Sgr A* as seen
by Murchikova et al. (2019). Channels between velocities
of –1300 km s [−][1] and –1800 km s [−][1] were used in a linear

χ-squared fit in the image plane to subtract the continuum. This mimics a line free channel selection process if
bandwidth was not available beyond –1800 km s [−][1] . Figure
1a,b shows the spectra of Sgr A* before and after the continuum subtraction, respectively. The subtracted linear fit
in Figure 1b shows a spectrum with similar shape to that
presented by Murchikova et al. (2019). This confirms the
double-peak spectrum of Sgr A* at ∼±500 km s [−][1] utilizing a different technique in continuum subtraction. The only
significant difference to Murchikova et al. (2019) is a higher
estimated flux density by ∼10 mJy. This is likely the result of
the amplitude and phase self-calibration applied to our data.
Atmospheric phase errors can cause reduced flux densities
of Sgr A* if proper self-calibration is not carried out. Alternatively, it is possible that the stimulated emission from
ionized gas toward Sgr A* is time variable and is responsible
for different flux density measured at different epochs.
The second set of line free channels was selected at the

extreme end of blue-shifted velocities between –3600 and
–3800 km s [−][1] . Figure 1c,d shows the constructed spectra
before and after applying continuum subtraction, respectively. There is a broad absorption line centered at –2600
km s [−][1] . Although this absorption contaminates the emission
from Sgr A*, it nevertheless shows emission that extends beyond –1500 km s [−][1] . The data presented by Murchikova et
al. (2019) did not contain velocity coverage beyond –2000
km s [−][1] . Thus, we tentatively show evidence of highly blueshifted velocities extending to –3500 km s [−][1] and a third
high-velocity peak near –2000 km s [−][1], in addition to ±500
km s [−][1] peaks.
Potential sources of the molecular absorption line found
at roughly –2665 km/s, as noted in Figures 1 and 2, are
identified in the H30α rest frame. The absorption is centered at 233.963 GHz. There are three candidates that could
be responsible for the absorption. One is CH 3 OH(5(1,5)4(1,4)) at center frequency 234.01158 GHz which would result in a red-shifted velocity of 62.19 km s [−][1] . This component has similar velocity to that of dense gas associated
with the molecular ring orbiting Sgr A* (e.g., Yusef-Zadeh
et al. (2017)), thus this red-shifted gas cloud close to Sgr
A* may be detected in absorption against Sgr A*. The others are OS [18] O(24(2,22)-24(1,23)) at 233.94997 GHz, blueshifted by –16.75 km s [−][1] or OS [18] O(52(7,46)-51(8,43)) centered at 233.9506176 GHz, blueshifted by –15.94 km/s. [1]


1 http://www.cv.nrao.edu/php/splat/sp-basic.html


MNRAS **000**, 1–12 (2020)

_2.2.2_ _H39_ α _Line_ _Emission_


Two spectra were obtained over the inner 0.75 [′′] towards the
position of Sgr A*. With respect to the rest frequency of
H39α at 106.737 GHz, one spectral window was available
between –3050 km s [−][1] to 1600 km s [−][1] and the other ranged
from 2575 km s [−][1] to 7200 km s [−][1], as shown in Figure 2.
There is no data available between these two spectral windows because of the initial observing setup. A linear continuum was fit individually to each spectra. For the more
blue-shifted window, the range –3000 km s [−][1] to –2300 km
s [−][1] was selected, while 5500 km s [−][1] to 7000 km s [−][1] was
chosen for the red-shifted component. The resultant H39α
emission with and without continuum subtraction is shown

in Figure 2a,b. We note broad H39α line emission from Sgr
A*. The emission confirms the results of Murchikova et al.
(2019) in that there are two high velocity ionized components peaking at ∼±500 km s [−][1] . Figure 2c also shows excess
emission detected at ∼−2000 km s [−][1], confirming the reality
of the H30α peak line emission shown in Figure 1c,d with
the caveat that the true line free channels in H39α and H30α

are unknown. Thus, we note tentative detection of H39α line
emission extending to 5500 km s [−][1] reflecting broader velocity coverage towards positive velocities.


_2.2.3_ _H52_ α _Line_ _Emission_


We used twelve adjacent spectral windows covering radial
velocities between ∼−4000 to ∼ 6300 km s [−][1] with re
spect to the rest frequency of H52α at 45.4538 GHz. The
spectra shown in Figure 3a,b were obtained over the inner
0.20 [′′] × 0.11 [′′] of Sgr A* with a spatial resolution of 77 × 35
mas and PA∼−2 [◦] . We detect an excess flux of H52α line
emission at roughly ∼ 500 km s [−][1] with a dip near 0 km s [−][1]

consistent with the earlier H30α measurements (Murchikova
et al. 2019). The −500 km s [−][1] feature is much weaker than
the 500 km s [−][1] feature but extends to more negative velocities. In addition, we note enhanced line emission that
extends to –1500 and +4000 km s [−][1] ; similar trends are also
noted in the H39α spectrum, as shown in Figure 3c.
In order to determine where high velocity ionized features are located with respect to Sgr A*, we selected the
spectral windows that showed enhanced –2500 and 4000 km
s [−][1] peak emission. Using two spectral windows, we made
moment maps of five channels centered near the low and
high velocity channels (channels 5-10 and 50-55), determined
the slope between the low and high velocity features for
each spectral window before subtracting them from each
other. The resulting continuum subtracted image of Figure
3c shows contours of blue- and red-shifted H56α line emission corresponding to ∼–2500 and ∼4000 km s [−][1], respectively. These high velocity features show a diagonal NE-SW
distribution along the Galactic plane similar to that found
by Murchikova et al. (2019) at ±500 km s [−][1] .


_2.2.4_ _H56_ α _Line_ _Emission_


We used ten adjacent spectral windows covering radial velocities between ∼−4000 to ∼ +6000 km s [−][1] with respect to the
rest frequency of H56α at 36.466 GHz. The spectra shown
in Figure 4a,b were obtained over a 0.22 [′′] ×0.27 [′′] region centered on Sgr A* with a spatial resolution of ∼ 95 × 49 mas


MNRAS **000**, 1–12 (2020)



5


and PA∼ 82 [◦] . We detect an excess flux of H56α line emission at roughly ∼ 500 km s [−][1] with a dip near 0 km s [−][1] consistent with earlier H30α measurements (Murchikova et al.
2019). However, the red-shifted component at radio is much
stronger than the blue-shifted component which is faint. It
is likely that the −500 km s [−][1] feature that Murchikova et
al. (2019) detects at higher frequencies is faint at H56α line
but extended to more negative velocities corresponding to ∼–
2500 and ∼4000 km s [−][1] . These high velocity features show a
diagonal NE-SW distribution along the Galactic plane similar to that found by The trend is similar to mm spectra
except that enhanced radio recombination line emission at
red-shifted velocities are 3-4 times stronger than the emission at blue-sifted velocities. In addition, we note enhanced
line emission that extends to –1500 and +4000 km s [−][1] ; similar trends are also noted in the H39α spectrum, as shown
in Figure 2c. We note two narrow and one broad absorption feature at velocities between –2500 and –4200 km s [−][1] .

The two narrow absorption lines are detected at 36.796 and
36.947 GHz, and are shown in Figure 4b. The 36.947 absorption line is centered on a broad absorption ranging over
a few hundred km s [−][1] . It is not clear what these lines are.

There is a family of methyl cyanide lines that range from
36.7937 - 36.7975 GHz as well as a methanol line at 36.7955

GHz. The latter corresponds to a radial velocity of ∼−4 km
s [−][1] with respect to the rest frequency. We also note that acetone lines between 36.952 and 36.940 GHz correspond to 40
km/s and −57 km s [−][1], respectively. These radial velocities
are in the range of velocities detected toward the molecular
ring orbiting Sgr A*.
In order to determine where the high velocity ionized
features are located with respect to Sgr A*, we selected
spectral windows that showed enhanced –2500 and 4000
km s [−][1] peak emission. From these windows five channels
were averaged near both the low and high velocity band
edges (channels 5-10 and 50-55), before subtracting them
from each other. The resulting continuum subtracted image
of Figure 4c shows contours of blue- and red-shifted H56α
line emission corresponding to ∼–2500 and ∼4000 km s [−][1],
respectively. These high velocity features show a similar distribution to that found for H52α line emission, i.e., diagonal
NE-SW orientation.


**3** **CONTINUUM** **DATA** **ANALYSIS** **AND**

**RESULTS**


**3.1** **Data** **Preparation**


We carried out radio continuum observations of Sgr
A* at multiple frequencies, each of which is described
below. All our continuum observations are centered
at the J2000 absolute position of Sgr A*, α, δ =
17 [h] 45 [m] 40 [s] .038, −29 [◦] 00 [′] 28 [′′] .069. We used 3C286 to calibrate the flux density scale, 3C286 and J1733-1304 (aka
NRAO530) to calibrate the bandpass and J1744-3116 to calibrate the complex gains in all of our observations.

6 _Yusef-Zadeh_ _et_ _al._


_3.1.1_ _Broadband_ _Q-band_ _(40–48_ _GHz)_ _and_ _Ka-band_
_(32–40_ _GHz)_


We observed Sgr A* on 2014 February 21 (14A-231) and
2018 April 3 (18A-091) in the most extended A-array configuration at 44 GHz. The Q-band (7mm band) was used
in the 3-bit system, which provided full polarization correlations in 4 basebands, each 2 GHz wide, centered around 44.5
GHz. Each baseband was composed of 16 subbands (spws),
each 128 MHz wide. Each subband in turn was made up
of 64 channels, each 2 MHz wide. This epoch of 44 GHz
observation, had effective bandwidth of 8 GHz.
In addition, A-array observations (14A-231, 16B138) in
the Ka (9mm) band on 2014, March 9 and 2016 July 19 at
34.5 GHz were carried out. We used the same 3-bit system
and the same calibration strategy for Ka band as we did
for the Q-band observations. A phase and amplitude selfcalibration procedure was applied to all data using Sgr A*.
To construct spectra at Ka and Q bands, as shown in Figures
3 and 4, only phase calibration was applied to the VLA data

sets.


_3.1.2_ _Broadband_ _Ku_ _band_ _13–15_ _GHz_


A-array observations (14A-231) were carried out on March
10, 2014 at 14 GHz utilizing full polarization correlations
in 2 basebands, each 1 GHz wide between 13.18 and 14.95
GHz. Each baseband was composed of eight 128 MHz wide
subbands. Each subband was made up of sixty-four 2 MHz
channels for a total effective bandwidth of 2 GHz. All of
the subbands were self-calibrated in phase separately. We
then combined all 14 useful spectral windows with the task
VBGLU in AIPS before we applied additional phase selfcalibration.


_3.1.3_ _Broadband_ _X_ _band_ _8–10_ _GHz_


A-array observations were carried out in two epochs on April
17, 2014, and August 17, 2019 at 8 GHz with identical system setup. We used the same backend as that of Ku data
for both data sets but with center frequency at 9 GHz and
total bandwidth of 2 GHz. Calibration on both data sets

was done independently similar to that of Ku data by phase
and amplitude calibration of individual spectral windows.
We combined both data sets followed by phase and amplitude self-calibration. All Stokes parameters were calibrated
in both data sets.


_3.1.4_ _Broadband_ _L_ _Band_ _1.4–2_ _GHz_


We carried out broad band VLA A-array observations of
the Galactic center at 1-2 GHz on 2014 April 02 (project
14A-231). The system we used provided full polarization in
both basebands. Each 1.4 GHz subband was made up of 64
channels of 1 MHz each. Several phase and amplitude selfcalibration procedures were applied to the data in OBIT
(Cotton 2008) using the bright radio source Sgr A* before
MFImager was used to construct a cube of 16 channels corresponding to each spectral window.



**3.2** **Radio** **Continuum** **Results**


We begin first by describing high frequency features within
5 [′′] −10 [′′] of Sgr A* followed by the arcminute structures in the
vicinity of Sgr A*. We then argue for a radio jet emanating
from Sgr A*. A trace of this jet is revealed at high frequencies, though with low signal-to-noise ratio. Many high frequency features that are described in the vicinity of Sgr A*
are several thousand times fainter than the bright source Sgr
A*, thus errors generated by the variable, strong continuum
from Sgr A* contaminate structural details in its vicinity. To
mitigate these difficulties, we focus on persistent structures
revealed from multiple observations with different frequencies and baselines.


_3.2.1_ _High_ _Frequency_ _Radio_ _Data_


_(a)_ _NE-SW_ _features_
Figure 5 shows a linear feature J1 with a PA∼ 23 [◦] extending NE of Sgr A* for ∼ 0.4 [′′], and having a typical surface
brightness of ∼ 300 µJy beam [−][1] at 44 GHz. As described below, this feature may be related to a more extended loop-like
structure. The rms noise of J1 in the immediate vicinity of
Sgr A* is ∼ 46 µJy beam [−][1] . There is also a fainter feature,
J2, which is 1/2 of typical surface brightness of J1, with
PA∼ 39 [◦] . The latter needs to be confirmed, though it is likely
to be associated with large-scale features J5, as described
below. The PAs of J1 and J5 range between 23 [◦] and 59 [◦]

and are similar to the PAs of highly red-shifted RRL components, as shown in Figures 3 and 4, and mmRL reported
by Murchikova et al. (2019). The H39α and H56α spectra
shown in Figures 2 and 4 include the region that contains
both J1 and J2. Thus, it is possible that the high velocity
redshifted components are related to elongated structures
J3 and J5 near Sgr A*, as seen in Figure 5.
Figure 6 shows another 44 GHz image of the same region
based on our second epoch observation. This image has a dynamic range of ∼ 9000 and rms noise of 17 µJy beam [−][1] . We
note a weak elongated feature J5 with a surface brightness of
∼ 50µJy beam [−][1] to the NE of IRS 16C and a PA∼ 59 [◦] . Two
faint linear features J3 and J4 are also found to the SW of
Sgr A* with surface brightness of 20-100 µJy beam [−][1] . The
position angles of J3 and J4 are 51 [◦] and 57 [◦], respectively. In
order to enhance the signal-to-noise ratio of J3, J4 and J5,
Figures 7a,b present the inner 5 [′′] of Sgr A* with a convolved
resolution of 76 milliarcsecond (mas). All three features have
PAs within six degrees of each other. The longest linear feature is J4 with an extent of ∼ 3. [′′] 5. A 9 GHz image of this
region in Figure 9d with lower spatial resolution than Figure
7 shows the same elongated structure emanating from Sgr
A*. The PAs of these features appear to be in the direction
where IRS 16C as well as cometary radio and near-IR stellar sources (F1, F2, F3, X3, X7, X8) lie (Muzi´c et al. 2007,
2010; Yusef-Zadeh et al. 2016; Peißker et al. 2019).
We notice that in numerous high frequency, high resolution images, the rms noise increases _only_ within ∼ 1 [′′] of
Sgr A*. For example, the rms noise in Figure 6 is about
three times higher. It is possible that phase and amplitude
errors are responsible for the increased noise. Alternatively,
the excess noise is due to diffuse emission at 44 GHz and
is intrinsic due to residual synchrotron emission detected at
mm and X-rays. This is a region where diffuse mm and X

MNRAS **000**, 1–12 (2020)

ray emission has previously been detected (Wang et al. 2013;
Yusef-Zadeh et al. 2017). Thus, that the dynamic range may
be limited due to highly turbulent multi-phase medium.


_(b)_ _western_ _minicavity_
Figure 8a shows a 36.8 GHz contour image of the inner
0.4 [′′] of Sgr A* constructed from data taken on 2016 July
19. The linear feature J1 is detected at a PA∼ 26 [◦] . Figure
8b shows contour emission from the inner 1 [′′] of Sgr A* with
a view of J1 based on a 9 GHz observation carried out on

2014 April 17. Again we notice an extension of J1 with similar PA to that at 36.8 GHz. Figure 8c shows the inner 4.5 [′′]

of Sgr A* at 15 GHz where we note two faint linear features
directed to the NE of Sgr A*. Both features, though with
low signal-to-noise ratio, appear to have a coherent structure
with similar PAs to J1 and J5, detected at other frequencies.
Figure 8d shows a greyscale image of the inner 4 [′′] of Sgr A*
at 9 GHz. The region to the southwest of Sgr A* in Figure
8c,d contains highly blue-shifted ionized gas associated with
the minicavity and a string of highly blue-shifted compact
velocity features which appear to bridge Sgr A* to the western edge of the mini-cavity. Compact sources, labeled C1 to
C4, are identified to have extremely blueshifted ionized gas
within 0.2pc of Sgr A* from –480 to –300 km s [−][1] (Royster
et al. 2019). The highly blue-shifted ionized gas has been
detected not only toward C1-C4, as labeled on Figure 8c,d,
but also toward the minicavity (Zhao et al. (2010) and multiple compact sources that lie close to the western edge of
the minicavity. Figure 8d shows a linear feature J4, as shown
in Figure 6a, that appears to cross a string of HII regions,
including C3. An excess of FeII/III line emission (Lutz et
al. 1993) and disturbed kinematics from the western edge
of the mini-cavity are unlikely to be due to orbital motion
because enhanced FeII/III line emission is detected only in
the mini-cavity. An external source of outflow impacting the
orbiting gas is likely to be responsible for producing shocked
gas, shaping morphological, kinematic structures to the SW
of Sgr A* (Yusef-Zadeh et al. 2016; Royster et al. 2019).
Lastly, Figures 8e,f show detailed images of the inner 4 [′′] constructed by combining two epochs of 9 GHz data. We note
that J2 and J5 appear to be parts of a coherent elongated
4 [′′] structure that extends the NE of Sgr A*. A loop-like
feature is also noted extending from the vertical feature to
the NE of Sgr A*. It is possible that J1 is part of this loop
feature within which there are additional diffuse features. A
north-south feature appears to be the radio counterpart to
a Brγ ionized bar that has recently been studied (Peißker,
et al. 2020). Figure 9c also shows contour representation of
the Brγ feature lying between J1 and the vertical feature.
_(c)_ _EW_ _ridge_
Figure 8 shows an EW ridge of mm emission which extends to the west of Sgr A* for ∼ 2 [′′] . This is also prominently
detected at 224 GHz within which a number of radio sources,
RS1-RS8, and a cluster of dusty infrared sources lie (YusefZadeh et al. 2017; Peißker et al. 2020). The trajectories of
dusty stellar sources detected at infrared indicate that they
are in an elliptical orbital motion around Sgr A* (Peißker
et al. 2020). Unlike many NE-SW features running along
the Galactic plane, as described earlier, the EW ridge has
a different orientation detected only on the western side of
Sgr A* but nevertheless appears to be associated with Sgr
A*. The EW ridge is revealed best at high radio frequencies,


MNRAS **000**, 1–12 (2020)



7


millimeter and infrared, suggesting that it consists of a mixture of dust, gas and dusty stellar sources. The kinematics of
dusty stellar sources in the ridge indicate that they are in an
elliptical counter-rotating orbit around Sgr A* (Peißker et
al. 2020), suggesting that they are impacted by a collimated
outflow from Sgr A*, as argued below.
To examine the morphology of the mini-cavity further,
Figures 9a,b present 9 GHz images of the inner 20 [′′] of Sgr
A* with two different brightness contrasts to highlight the
bright region of the mini-cavity. The mean flux density in
the western edge of the minicavity is twice that of the eastern edge. Assuming that the enhanced emission and the disturbed kinematics are due to a collimated outflow from Sgr
A*, the opening angle of the outflow must be ∼ 30 [◦], as indicated in Figure 9a, which covers not only the western half
of the mini-cavity but also the EW ridge.
_(d)_ _AF_ _and_ _AFNW_ _stars_
The SW extension of the minicavity directed towards
the southern arm of the minicavity shows a number of elongated sources and a tail of ionized gas crossing the southern
arm. Two mass-losing stars AF and AFNW have previously
been identified to have cometary tails directed away from
Sgr A* (Yusef-Zadeh et al. 2017). These features are likely
to reflect the interaction of an outflow from the direction of
Sgr A* with stellar sources and orbiting gas. Both the AF
and AFNW sources are located within the opening angle of
the jet beyond the minicavity; the white lines drawn on Figures 9a,b run parallel to a number of features that trace the
direction of the outflow from Sgr A*. lie within the opening
angle of the jet. In this picture, infrared stellar sources in
the EW ridge are also impacted by this outflow.
_(e)_ _bent_ _filament_
We also note in Figure 9 a bent filament to the north
of Sgr A* (Yusef-Zadeh et al. 2017; Morris et al. 2017).
Previous measurements have not been able to determine if
this filament is connected to Sgr A* and perhaps produced
by Sgr A* (Yusef-Zadeh et al. 2017; Morris et al. 2017).
There is no evidence for morphological association with Sgr
A* at 9 GHz. We note a compact source with a flux density of 0.15±0.5 mJy beam [−][1] coinciding with the southern
tip of the ′′ filament at α, δ J2000 = 17 [h] 45 [m] 40 [s] .101 ± 0.002 −
29 [◦] 00 [′] 23 .269 ± 0.118. To the NE of Sgr A*, J5 and J1 are
revealed with an average flux density of ∼ 100 µJy beam [−][1]

and a PA∼ 56 [◦] and 21 [◦], respectively. The extension of J5
appears to encounter the cometary tail of stellar source F1
to within one degree.
_(f)_ _vertical_ _feature_
We also note a vertical feature to the NW of Sgr A*. A
close up of this region, shown in Figure 9c, indicates a continuous structure from the eastern boundary of the minicavity. There is no kinematic information but it appears that
the ionized gas associated with the eastern boundary of the
minicavity is turning counterclockwise as it orbits Sgr A*.
A schematic diagram of features noted at high frequencies
is shown in Figure 9d.


_3.2.2_ _Low_ _Frequency_ _Radio_ _Data_


_(a)_ _NE-SW_ _radio_ _jet_
We have constructed images based on low-frequency
data taken with the VLA using its broad band capability.
Figure 10a,b show grayscale and contours of 20 cm contin

8 _Yusef-Zadeh_ _et_ _al._


uum emission from the inner ∼ 35 [′′] of Sgr A*. These images
are constructed by combining spectral windows with frequencies between 1 and 1.4 GHz. A prominent linear structure at PA∼ 60 [◦] is detected symmetrically only at the lowest
frequencies of the broad band. The arms of the mini-spiral
are seen in absorption against the strong nonthermal emission from the shell-type Sgr A East SNR, known to lie behind Sgr A* (Yusef-Zadeh et al. 1986; Pedlar et al. 1989).
The bent filament with PA∼−30 [◦] is seen immediately to
the north of Sgr A* (Yusef-Zadeh et al. 2017; Morris et al.
2017).
In order to show how features projected against a strong
nonthermal source, i.e. Sgr A East, are identified, we present
grayscale and contour images of all 16 spectral channels between 1 and 2 GHz, as seen in Figure 11a,b. At frequencies
- 1.5 GHz, thermal emission from the mini-spiral is bright
and stronger than the background nonthermal emission from
the Sgr A East SNR. On the other hand at low frequencies
(1-1.4 GHz), the ionized gas of the mini-spiral becomes optically thick and is only detected in absorption against the
strong nonthermal background emission. A ”sweet spot”, 1.4
GHz, demarcates where thermal and nonthermal emission
dominate at higher and lower frequencies, respectively.
Figure 12a shows a composite image of nonthermal and
thermal sources within 30 [′′] of Sgr A*. Low frequency (1–1.4
GHz) and high frequency images (1.5–1.9 GHz) are shown in
red and blue whereas green shows an image using the entire
range (1–1.9 GHz). We note that the optically thick ionized
gas associated with the mini-spiral is absent at low frequencies (red) and becomes optically thin at higher frequencies
(blue). Figure 12b shows another color image constructed
from combining a narrow low-frequency channel map (green)
and a broad high frequency channel map (red). The linear
nonthermal features are best seen at low frequencies where
thermal emission is suppressed. These images confirm that
the ionized mini-spiral features are in front of the nonthermal emission. More importantly, new linear features, a radio
jet and the bent filament are detected at low frequencies below 1.4 GHz, consistent with being nonthermal. Figure 12c
shows a diagram of the prominent thermal and nonthermal
components surrounding Sgr A*.
Figure 13a,b show a larger view of the region on a scale
of arcminutes where the mini-spiral, the Sgr A East SNR
and a string of HII regions at the eastern edge of the Sgr A
East shell lie. Unlike the broad band 20 cm image of Figure
13a, the narrow band image of Figure 13b shows the same
region where the low frequency radio jet is detected. The
position angle of the narrow jet runs 20 [◦] above the Galactic
plane at negative longitudes, centered on Sgr A*.
Figure 13c shows a close-up view of the southern extension of the radio jet and a number of Galactic center
nonthermal radio filaments. The prominent shell of the Sgr
A East SNR is known to be elongated along the Galactic
plane. One possibility that could explain the shape of Sgr A
East is that the expansion occurred in a medium that had
become anisotropic by an earlier outflow driven by the jet
activity of Sgr A* along the Galactic plane. In this picture,
the oval shape of the shell is produced by the material being
swept along the outflow axis to the onset of SNR expansion.
The magnetic field along the Galactic plane could also contribute to the formation of the elongated Sgr A East shell.
A 327 MHz image of large scale structures in the Sgr



A complex also shows extensions of arcminute jet feature
along the Galactic plane. The 327 MHz feature extends up
to about 5 [′] away from Sgr A* (see Figure 2 of Nord et al.
(2004)) having PAs similar to arcminute scale structures revealed at 1.4 GHz. Thus, it is possible that the jet to the NE
of Sgr A*, extends to ∼ 10 [′] (24 pc). High resolution broad
band observations are needed to determine the association of

linear features detected at 327 MHz with those at 1.4 GHz.


**4** **DISCUSSION**


The Galactic center is a challenging site to search for a jet
near Sgr A* because the dynamic range of high resolution
images is limited by confusing sources, limited _uv_ coverage,
and the intrinsic hourly time variability of Sgr A*, especially
at high frequencies. It is also difficult to identify nonthermal
sources because at low frequencies (325 MHz), the minispiral of ionized gas orbiting Sgr A* is seen in absorption
due to optical depth effects. At higher frequencies (8 GHz),
thermal features dominate the emission, making it difficult
to identify nonthermal sources. One approach to identify
both thermal and nonthermal sources is to employ broad
bandwidths at multiple frequencies. The upgraded VLA 1-2
GHz band, has changed our view of this region studied by
traditional narrow band observations. New images are providing evidence for a linear feature with the appearance of
a symmetrical jet originating from Sgr A*, pointing in the
direction of the Galactic plane.


_4.0.1_ _Collimated_ _Outflow_ _and_ _Interaction_ _Sites_


The overall distribution of the PAs of the linear features de
scribed here range between ∼ 30 [◦] and ∼ 60 [◦] . As we discuss
below, the inferred position angle of the jet is supported by
sources within the opening angle of the jet showing kinematical signatures of interactions with an anisotropic outflow. In
addition, the inferred jet and outflow properties are consistent with what is expected from models of the interaction of
the stellar winds from the WR stars on the central parsec
with Sgr A*.
First, the mini-cavity to the SW of Sgr A* shows the
highest radial velocities and electron temperatures from
radio recombination lines, as well as excess FeII/III and
FeIII/Brγ line ratios (Lutz et al. 1993; Zhao et al. 2010;
Yusef-Zadeh et al. 2012; Peißker et al. 2019; Peißker et al.

2020). Radio images presented here clearly indicate an increase in the surface brightness of the western edge of the
cavity. There is also the EW ridge showing similar characteristics to the mini-cavity, e.g., excess FeII/III and FeIII/Brγ
line ratios.

Recent spectroscopic studies suggest dust embedded
pre-main sequence stars in the EW ridge (Peißker et al.
2019). All these indicate shock excitation due to violent disturbance. We previously used the implied rate of change in
momentum of the disturbed gas and the angle that the western edge of the cavity subtends from Sgr A* to infer that the
(two-sided) jet momentum and opening angle are approximately 0.1 _M_ ⊙ yr [−][1] km s [−][1] and 30 [◦], respectively. We assume
that the jet is mildly relativistic, with βγ = 3, implying a
rest mass outflow rate ≈ 1 × 10 [−][7] _M_ ⊙ yr [−][1] (Yusef-Zadeh et
al. 2017).


MNRAS **000**, 1–12 (2020)

Other observations that can be explained by the impact of the jet with the mini-cavity is an X-ray source with
a luminosity of 2×10 [33] erg s [−][1] coincides with the cluster of
stars, IRS 13E, (Wang et al. 2020; Zhu et al. 2020) embedded within the western edge of the minicavity. Recent analysis of X-ray data concludes that colliding winds of masslosing stars in the cluster are responsible for production of
X-rays (Wang et al. 2020; Zhu et al. 2020). Alternatively,
we note that X-ray emission from the minicavity can also be
explained by the violent collision with the jet shocking the
gas to high temperatures. I another hard X-ray observations
between 20-40 keV over the inner few arcminutes of of Sgr
A* show extended symmetric emission with respect to Sgr
A* along the Galactic plane (Perez et al. 2015). The diffuse
hard X-ray emission is interpreted to be due to a population
of compact objects or particle outflow from Sgr A*. If the
latter, the jet-picture discussed here is likely to explain the
origin of diffuse X-ray emission.

Furthermore, gas compression can in principle increase
the gas density to overcome tidal shear by Sgr A*, thus
inducing star formation activity. Recent measurements Recent spectroscopic studies suggest dust embedded pre-main
sequence stars in the EW ridge as as well as bipolar CO
outflows indicating young star formation activity near Sgr
A*(Yusef-Zadeh et al. 2017; Peißker et al. 2019).
Second, a chain of radio blobs linking Sgr A* and the
western edge of the minicavity (Wardle, & Yusef-Zadeh
1992), show the highest velocity ionized gas, ∼−300 to −480
km s [−][1] detected beyond the inner 1 [′′] of Sgr A* (Royster et
al. 2019). Along the axis defined by the detection of highly
blue-shifted ionized gas, the cometary dusty stellar sources,
X3, X7, and X8 are also found to the SW of Sgr A* along
the extension of the jet feature (Muzi´c et al. 2007, 2010;
Peißker et al. 2019). These sources show a high abundance
of [FeIII] line emission, with similar characteristics to the
western edge of the minicavity (Peißker et al. 2019). To the
NE of Sgr A*, there is evidence of an elongated X-ray structure, NE plume in Yusef-Zadeh et al. (2012), a number of
cometary stellar sources pointing towards Sgr A* (F1, F2,
F3) and red-shifted ionized gas (Muzi´c et al. 2007, 2010;
Royster et al. 2019). Muzi´c et al. (2010) suggested that an
external wind with density ∼ 10 cm [−][3] and speed ∼>1000 km

s [−][1] emerging from the close vicinity of Sgr A* is responsible
for shaping the bow shocks and orienting them towards Sgr
A*. The inferred ram pressure, ρ v [2] ∼ 2 × 10 [−][7] dyn cm [−][2]

is one twentieth of the jet ram pressure thought to be responsible for the formation of the minicavity, As a working
hypothesis we assume that the opening angle of the outflow
is 60 [◦], with the inner 30 [◦] occupied by a mildly relativistic
jet. In this picture, the EW ridge at a PA ∼30 [◦] away from
the direction of the relativistic jet is mainly produced by the
interaction of the outflow with dusty infrared stellar sources.

Third, on scales of a few mpc, H30α, H39α and H56α
spectra exhibit broad blue- and red-shifted line emission
with a line width of thousands of km s [−][1] and oriented

roughly along the Galactic plane to the NE and SW, respectively. These have previously been interpreted as the red and
blue lobes of a highly inclined Keplerian disk (Murchikova
et al. 2019). However, our observations have wider frequency
coverage and find significantly broader line widths, >4000km
∼

s [−][1] consistent with Keplerian motion at about 1/5 the ob

MNRAS **000**, 1–12 (2020)



9


served angular scale of the emission. Instead, this emission
more likely arises from entrained material being accelerated
outwards by the jet. The mass of accelerated material cannot easily be inferred from the recombination-line fluxes because of the dominant contribution of stimulated emission.
The upper limit on the Brγ emission within 0.2 [′′] of Sgr A*
is ∼ 2 Jy km s [−][1] (Ciurlo et al. 2020).

The Brγ emissivity for T e ∼ 10 [4] K and n e ∼ 10 [4] cm [−][3]

is j γ ∼ 2.7 × 10 [−][28] erg s [−][1] cm [−][3] sr [−][1] (Hummer and Storey
1987). The Brγ luminosity for a source with volume emission
measure VEM=∫ _n_ e [2] _dV_, yielding a flux S γ = (j γ VEM)/d [2] ∼
0.96(VEM/(10 [58] cm [−][3] )) Jy km s [−][1] where a Galactic center
distance d=8 kpc has been adopted. This implies that the
volume emission measure of the material is ∼< 2 × 10 [58] cm [−][3],
and that stimulated emission amplifies the H30α line luminosity by at least a factor of 80 (Murchikova et al.
2019). Our radio continuum observations have tentatively
detected this material: the weak, extended features J1 and
J3 that lie within 0.2 [′′] of Sgr A* have flat spectra between 9 and 44 GHz, consistent with optically-thin thermal bremsstrahlung from the red- and blue-shifted components of this gas, respectively. J3 lies in an area confused
by extended continuum emission, making it difficult to extract reliable fluxes, so we focus on J1, which has an integrated flux ∼ 0.2 mJy at 36 GHz. The free-free emissivity
at 36 GHz is j ν / _n_ e [2] ∼ 2.2 × 10 [−][40] erg cm [3] Hz [−][1] sr [−][1], yielding a flux S ν = j ν VEM/d [2] ∼ 0.32 VEM/(10 [58] cm [−][3] ) mJy.
Thus, we infer VEM ≈ 6 × 10 [57] cm [−][3] for nominal temperature 10 [4] K. Adopting dimensions 0 [′′] . 2 × 0 [′′] . 02 × 0 [′′] . 02 consistent with Fig. 6(b) this implies _n_ e ≈ 1 × 10 [5] cm [−][3] and mass
≈ 6 × 10 [−][5] _M_ ⊙ .


One of the implications of the presence of ionized gas
on such a small scale associated with Sgr A* is that it can
also explain the large rotation measure detected toward Sgr
A* (RM∼−5 × 10 [5] rad m [−][2] ) (Bower et al. 2018). Assuming
that the parallel component of the magnetic field is 1.5 mG,
high velocity ionized gas detected within 0.1 [′′] of Sgr A* can
produce the observed Faraday rotation.


Fourth, on a scale of AU, the polarization angle of nearIR flaring activity of Sgr A* can be measured several times
a day. These measurements give a mean polarization angle
of 60 [◦] ± 20 [◦] consistent with the position angle of the larger
scale jet features (Eckart et al. 2006; Meyer, et al. 2007).
In addition, VLBI measurements provide highest resolution
images of millimeter emission from Sgr A* with mas size
scales. The PA of millimeter emission from Sgr A* is roughly
in agreement with a PA within 30 [◦] of the Galactic plane.
Thus, this emission could be associated with the large scale
jet feature having similar PA.


Fifth, the linear pc-scale jet-like features that we have
identified are stronger at 9 GHz than at 44 GHz, suggestive
of synchrotron emission from a jet emerging from the vicinity of Sgr A*. This confirms our earlier narrow band observations reporting a tentative detection of continuous linear
structure with an extent of ∼3 pc and PA∼ 60 [◦] (Yusef-Zadeh
et al. 2012). The extension of this feature appears to terminate symmetrically by linearly polarized structures at 8.4
GHz, ∼ 75 [′′] from Sgr A* (Yusef-Zadeh et al. 2012). For the
observed jet diameter (≈ 2 [′′] ) and 1.6 GHz surface brightness ≈ 0.2 mJy beam [−][1], we deduce an equipartition magnetic field ∼ 0.2 mG using standard (but uncertain) assump

10 _Yusef-Zadeh_ _et_ _al._


tions: an _E_ [−][2] electron spectrum running between 10 MeV
and 100 GeV and equal energy density in electrons and pro
tons.

Finally, the NE edge of Sgr A East is highly distorted
along the Galactic place (Yusef-Zadeh et al. 2016). In the jet
picture, the kinetic luminosity of the jet is likely responsible
for the distortion of Sgr A East. In addition, the puzzle of
why the Sgr A East shell is elongated along the Galactic
plane can also be explained by a medium that has been swept
by a symmetric outflow from Sgr A* along the Galactic plane
before the expansion of the remnant occurred.
The six characteristics described above provide overwhelming evidence for a jet extending from AU to pc scales
likely surrounded by a wider-angle outflow in the inner par
sec.


**4.1** **Orientation** **of** **the** **Jet**


The orientation, and mass flow rate of the jet is consistent with jet-launching models, which predict that the jet
emerges perpendicular to the equatorial plane of the accretion flow near the event horizon of Sgr A*. Here we define
the jet orientation to be the 3D unit vector parallel to the
red-shifted component, which we quantify by two angles, Ω j,
the PA of the arm (measured E of N), and the angle θ j that
the arm makes to the line of sight (so 0 [◦] ≤ θ j ≤ 90 [◦] ). The
inferred jet is aligned roughly NE-SW on the sky, and given
that the disturbed material in the mini-cavity is blue shifted,
we infer that the mini-cavity and the ionized bar lie in front
of Sgr A* and that the SW arm of the jet is approaching us.
Thus the red shifted arm of the jet emerges to the NE of Sgr
A* with PA Ω j ≈ 60 [◦] E of N and makes an angle θ j ≈ 45 [◦] to
the line of sight (which is directed away from the observer).
The angular momentum of the inner accretion flow on to Sgr
A* should then be parallel or anti parallel to the redshifted
arm, implying that the orbital elements of the disk, i.e. PA
of the ascending node, Ω, and inclination to the plane of the
sky, _i_, are either (i) Ω = Ω j − 90 [◦] ≈ 330 [◦], _i_ = 180 [◦] − θ j ≈ 120 [◦],
or (ii) Ω = Ω j + 90 [◦] ≈ 150 [◦], _i_ = θ j ≈ 120 [◦] . Figure 14a,b
show schematic diagrams of the possible orientations of the
jet launched from the accretion disk.
Sgr A* is fed by the combined winds of WR stars in
the inner ∼ 0.1 pc of the Galaxy (Coker and Melia 1997;
Cuadra et al. 2006, 2008; Ressler et al. 2019). The orbits
of most of these stars lie in the “clockwise disk”, with orbital planes distributed around a mean PA of their ascending
nodes Ω ≈ 106 [◦] E of N and mean inclination _i_ ≈ 126 [◦] to the
line of sight (Bartko et al. 2009; Gillessen et al. 2009; Yelda
et al. 2014; Gillessen et al. 2017). Figure 14c shows the orientation of clockwise stellar disk which is thought to be the
source of the accreting material. While the stellar disk orientation is significantly misaligned with the average angular
momentum of the inner accretion flow inferred from the jet
orientation, simulations show that the material in the inner
accretion flow was injected with low orbital angular momentum, i.e. the wind material that is ejected antiparallel to the
orbital motion of a small number of dominant WR stars
(Calderon et al. 2020; Gravity Collaboration 2020; Ressler
et al. 2019, 2020). The inherent granularity of this process introduces significant variations in the orientation of the
low-angular momentum material on ∼ 200 year time scales
as the stars move around their orbits (Ressler et al. 2020).



Further, astrometric observations of infrared flares with the
GRAVITY instrument on board the VLT suggest a hotspot
source orbiting Sgr A* with inclination _i_ ≈ 130 [◦] and Ω most
likely to be either ≈ 130 [◦] – consistent with the clockwise
stellar disk, or ≈ 300 [◦] – consistent with our observed jet orientation (Gravity Collaboration 2020). Finally, we note also
that the black hole spin, which reflects the accretion of angular momentum by the hole during its life time is likely to
be significantly misaligned with the clockwise disk, reflecting
instead the accumulation of material over cosmic time. If the

net spin is significant, one might expect the inner accretion
flow to be forced into alignment with the equatorial plane
of the Kerr space time on scales of a few gravitational radii.
We conclude then that the misalignment of the jet and the
angular momentum of the clockwise disk is not a significant

issue.


**5** **SUMMARY**


We presented multi-wavelength spectroscopic and broad
band continuum measurements over a wide range of angular
scales toward Sgr A* and its local environment. These measurements indicate a jet driven outflow arising from Sgr A*
on mpc to pc scales along the Galactic plane. The opening
angle of the outflow is 60 [◦], with the inner 30 [◦] occupied by the
relativistic jet. Our millimeter recombination line data supported earlier studies that the red and blue-shifted ionized
gas detected toward Sgr A* lie along the Galactic plane. We
argued that the interaction of the collimated outflow with
stellar atmospheres and gas clouds can be responsible for
disturbed kinematics of ionized gas, enhanced FeII/III and

[FeIII] to Brγ line ratios, head-tail cometary stellar sources,
X-ray emission from IRS 13 and high Faraday rotation observed toward Sgr A*. Shock heated gas resulting from the
interaction has other implications such as compressing the
gas to possibly overcome tidal shear, thus inducing star formation. The outflow could also shape the elongation of the
Sgr A East SNR and be responsible for high cosmic ray
ionization rate inferred from H [+] 3 [measurements] [within] [the]
molecular ring and the central molecular zone, e.g, (Goto et
al. 2014). Furthermore, our radio continuum data demonstrates that lower frequency emission from Sgr A* at ν < 1.4
GHz and its environment have the potential to determine the
mass of ionized gas. In the jet picture, a significant amount
of the power comes out in the form of the kinetic luminosity carrying off energy and angular momentum. This could
explain why Sgr A* appears radiatively under luminous.


**6** **DATA** **AVAILABILITY**


All the data that we used here are available online and are

not proprietary. We have reduced and calibrated these data
and are available if requested.


**ACKNOWLEDGMENTS**


This work is partially supported by the grant AST-0807400
from the NSF. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universi

MNRAS **000**, 1–12 (2020)

ties, Inc. This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2015.0.00021.S. ALMA is a partnership
of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), NSC and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.


**REFERENCES**


Becker, P. A., Das, S., & Le, T. 2011, ApJ, 743, 47
Bartko, H., Martins, F., Fritz, T. K., Genzel, R., Levin, Y., Perets,
H. B., et al. 2009, ApJ, 697, 1741
Broderick, A. E., Fish, V. L., Doeleman, S. S., Loeb, A. 2011,
The Astrophysical Journal 738, 38.
Bower, G. C., and 12 colleagues 2018, The Astrophysical Journal
868, 101.
Brinkerink, C. D., and 23 colleagues 2019, Astronomy and Astrophysics 621, A119.
Coker, R. F. & Melia, F. 1997, ApJ, 488, L149
Cotton, W. D. 2008, Publications of the Astronomical Society of
the Pacific 120, 439.
Cuadra, J., Nayakshin, S., & Martins, F. 2008, MNRAS, 383, 458
Cuadra, J., Nayakshin, S., Springel, V., & di Matteo, T. 2006,
MNRAS, 366, 358
Ciurlo, A., Campbell, R. D., Morris, M. R., Do, T., Ghez, A. M.,
Hees, A., et al. 2020, Nature, 577, 337
Calder´on, D., Cuadra, J., Schartmann, M., Burkert, A., & Russell,
C. M. P. 2020, ApJ, 888, L2
Dexter, J., Jim´enez-Rosales, A., Ressler, S. M., Tchekhovskoy, A.,
Baub¨ock, M., de Zeeuw, P. T., et al. 2020, arXiv:2004.00019
Eckart, A., Sch¨odel, R., Meyer, L., Trippe, S., Ott, T., Genzel, R.
2006. Astronomy and Astrophysics 455, 1.
Falcke, H., Markoff, S. 2000. Astronomy and Astrophysics 362,

113.

Hummer, D. G., Storey, P. J. 1987. Monthly Notices of the Royal
Astronomical Society 224, 801.
Goto, M., and 6 colleagues 2014, The Astrophysical Journal 786,

96.

Issaoun, S., and 43 colleagues 2019. The Astrophysical Journal
871, 30.
Li, Z., Morris, M. R., Baganoff, F. K. 2013. The Astrophysical
Journal 779, 154.
Lu, R.-S., and 7 colleagues 2011 Astronomy and Astrophysics 525,
A76.

Lu, J. R., Ghez, A. M., Hornstein, S. D., Morris, M. R., Becklin,
E. E., & Matthews, K. 2009, ApJ, 690, 1463
Lutz, D., Krabbe, A., Genzel, R. 1993. The Astrophysical Journal
418, 244.
Gillessen, S., Eisenhauer, F., Trippe, S., Alexander, T., Genzel,
R., Martins, F., et al. 2009, ApJ, 692, 1075
Gillessen, S., Plewa, P. M., Eisenhauer, F., Sari, R., Waisberg, I.,
Habibi, M., et al. 2017, ApJ, 837, 30
Gravity Collaboration, Baub¨ock, M., Dexter, J., Abuter, R.,
Amorim, A., Berger, J. P., et al. 2020, A&A, 635, A143
Johnson, M. D., and 14 colleagues 2018. The Scattering and Intrinsic Structure of Sagittarius A* at Radio Wavelengths. The
Astrophysical Journal 865, 104.
Meyer L., Sch¨odel R., Eckart A., Duschl W. J., Karas V.,
Dov _V_ ciak M., 2007, A&A, 473, 707
Markoff, S., Bower, G. C., Falcke, H. 2007. Monthly Notices of
the Royal Astronomical Society 379, 1519.
Morris, M. R., Zhao, J.-H., Goss, W. M. 2017. ApJ, 850, L23.
Muno, M. P., Baganoff, F. K., Brandt, W. N., Morris, M. R.,
Starck, J.-L. 2008. The Astrophysical Journal 673, 251.


MNRAS **000**, 1–12 (2020)



11


Murchikova, E. M., Phinney, E. S., Pancoast, A., et al. 2019,
Nature, 570, 83
Muzi´c, K., Eckart, A., Sch¨odel, R., et al. 2010, A&A, 521, A13
Muzi´c, K., Eckart, A., Sch¨odel, R., et al. 2007, A&A, 469, 993
Nord, M. E., and 6 colleagues 2004. The Astronomical Journal
128, 1646.
Ortiz-Le´on, G. N., and 21 colleagues 2016. The Intrinsic Shape
of Sagittarius A* at 3.5 mm Wavelength. The Astrophysical
Journal 824, 40.
Pedlar, A., and 6 colleagues 1989. The Astrophysical Journal 342,

769.

Peißker F., Eckart A., Sabha N. B., Zaja _V_ cek M., Bhat H., 2020,
ApJ, 897, 28
Peißker, F., Hosseini, S. E., Zaja _V_ cek, M., Eckart, A., Saalfeld,
R., Valencia-S., M., et al. 2020, A&A, 634, A35
Peißker, F., Zaja _V_ cek, M., Eckart, A., Sabha, N. B., Shahzamanian, B., Parsa, M. 2019. Astronomy and Astrophysics 624,
A97.

Perez K., Hailey C. J., Bauer F. E., Krivonos R. A., Mori K.,
Baganoff F. K., Barri`ere N. M., et al., 2015, Natur, 520, 646
Quataert, E. 2004, ApJ, 613, 322
Ressler, S. M., Quataert, E., & Stone, J. M. 2019, MNRAS, 482,

L123

Ressler, S. M., Quataert, E., & Stone, J. M. 2020, MNRAS, 492,

3272

Royster, M. J., Yusef-Zadeh, F., Wardle, M., et al. 2019, ApJ,
872, 2.
Sch¨odel R., Najarro F., Muzic K., Eckart A., 2010, A&A, 511,
A18

Shen, Z.-Q., Lo, K. Y., Liang, M.-C., Ho, P. T. P., Zhao, J.-H.
2005, Nature, 438, 62.
Wang, Q. D., Nowak, M. A., Markoff, S. B., et al. 2013, Science,
341, 981
Wang, Q. D., Li, J., Russell, C. M. P., Cuadra, J. 2020. Monthly
Notices of the Royal Astronomical Society 492, 2481.
Wardle, M. & Yusef-Zadeh, F. 1992, Nature, 357, 308
Yelda, S., Ghez, A. M., Lu, J. R., Do, T., Meyer, L., Morris, M.
R., et al. 2014, ApJ, 783, 131
Yuan, F., Quataert, E. & Narayan, R. 2004, ApJ, 606, 894
Yusef-Zadeh, F., Morris, M. 1987. The Astrophysical Journal 320,

545.

Yusef-Zadeh, F., Arendt, R., Bushouse, H., et al. 2012, ApJ, 758,

L11

Yusef-Zadeh, F., Wardle, M., Kunneriath, D., Royster, M., Wootten, A., Roberts, D. A. 2017. The Astrophysical Journal 850,

L30.

Yusef-Zadeh, F., Wardle, M., Sch¨odel, R., et al. 2016, ApJ, 819,

60

Yusef-Zadeh, F., Sch¨odel, R., Wardle, M., et al. 2017, MNRAS,
470, 4209
Yusef-Zadeh, F., Morris, M., Slee, O. B., Nelson, G. J. 1986, ApJ,
300, L47.
Yusef-Zadeh, F., Morris, M., Slee, O. B., Nelson, G. J. 1986 ApJ,
310, 689.
The Astrophysical Journal 300, L47.
Yusef-Zadeh, F., Roberts, D., Wardle, M., Heinke, C. O., Bower,
G. C. 2006. The Astrophysical Journal 650, 189.
Zamaninasab, M., and 12 colleagues 2011. Monthly Notices of the
Royal Astronomical Society 413, 322.
Zhao, J.-H., Blundell, R., Moran, J. M., Downes, D., Schuster,
K. F., Marrone, D. P. 2010. The Astrophysical Journal 723,

1097.

Zhu, Z., and 6 colleagues 2020. arXiv e-prints arXiv:2003.10311.

12 _Yusef-Zadeh_ _et_ _al._


H30α 0.46 [′′] (-1800 to -1400 km/ Continuum)

2500


2495


2490


2485


2480


2475



H30α 0.46 [′′] (-3700 to -3540 km/ Continuum)


−3500 −3000 −2500 −2000 −1500 −1000 −500 0 500

Velocity (km/ )


−3500 −3000 −2500 −2000 −1500 −1000 −500 0 500

Velocity (km/ )



2470


8


6


4


2


~~0~~


−2


−4


−6


−8


−10



−3500 −3000 −2500 −2000 −1500 −1000 −500 0 500

Velocity (km/ )



2500


2495


2490


2485


2480


2475


2470


8


6


4


2


~~0~~


−2


−4


−6


−8



**Figure** **1.** _(a_ _Top_ _Left)_ The spectrum of Sgr A* integrated over a beam with a diameter of 0.46 [′′] is shown before continuum subtraction.
In order to confirm the double-peak spectrum of Sgr A*, we used similar parameters to those of Murchikova et al. (2019), assuming line
free channels at velocities between –1300 and –1800 km s [−][1] (the shaded region). The overlayed line is the least squares straight-line fit
to the continuum in the shaded region. _(b_ _Bottom_ _Left)_ Identical to (a) except that the continuum has now been subtracted from the
spectrum. The vertical gray bars show the selected line free channels. _(Top_ _Right_ _c,_ _Bottom_ _Right_ _d)_ As for Figure 1 except line free
channels are instead chosen from –3600 and –3800 km s [−][1] (the shaded region). As before the top panel is before continuum subtraction
and the bottom panel is post continuum subtraction.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–12 (2020)

13



H39α 1.5 [′′] (−3000 o −2500 km/s Con inuum)



1900


1890


1880


1870


1860



H39α 1.5 [′′] (5500 to 7000 km/s Contin m)

|Col1|Col2|Col3|
|---|---|---|
|4000<br>5000<br>Velocity (km/s)|6000<br>7|000|
||||
||||



3000 4000 5000 6000 7000

Velocity (km/s)



1850


8


6


4


2


~~0~~



1745


1740


1735


1730


1725


1720


1715


1710


6


4


2


0


−2



−2

|Col1|Col2|
|---|---|
|000<br>−|2000<br>−1000<br>0<br>Velocity (km/s)|
|||
|||


−3000 −2000 −1000 0 1000

Veloci y (km/s)



H39α 1.5 [′′]

12


10


8


6


4


2


0


−2


−2000 0 2000 4000 6000

Velocity (km/s)


**Figure** **2.** _(a_ _Left)_ Emission with or without continuum subtraction from the inner 0.75 [′′] at the peak position of Sgr A* from –3050
km s [−][1] to1600km s [−][1] . A fitted continuum is shown as a result of fitting chosen line free channels from –3000km s [−][1] to –2500km s [−][1] . _(b_
_Right)_ Similar to _a_ except the emission from 2575 km s [−][1] to 7200 km s [−][1] is shown. The line free channels were chosen as 5500 km s [−][1] to
7000 km s [−][1] and the resultant fit is drawn. _(c_ _Bottom)_ Excess H39α emission found from subtracting continuum in the respective top
panels in (a,b).


MNRAS **000**, 1–12 (2020)

14 _Yusef-Zadeh_ _et_ _al._


1300


1290


1280


1270


1260



H52 (45.4537 GHz)



4000 2000 0 2000 4000 6000

Velocity (km/s)


15.0


12.5


10.0


7.5


5.0


2.5


0.0


2.5


4000 2000 0 2000 4000 6000

Velocity (km/s)


**Figure** **3.** _(a_ _Top_ _Left)_ A scatter plot of the spectrum of H52α emission without continuum subtraction from the inner 0.077 [′′] × 0.035 [′′]

(PA∼−2 [◦] ) of Sgr A* using twelve adjacent spectral windows. _(b_ _Botton_ _Left)_ Continuum subtracted H52α emission from Sgr A* presented
in histogram format. This continuum was fit in the range −4000 to −3600 and 6000 to 6300 km s [−][1] . The spectrum of individual spectral
window is scaled such that adjacent spws are continuous. This scaling removes the flux scale across the band which varies at a level of
few tenths of a percent. _(c_ _Left)_ Contour levels of red- and blue-shifted components of H52α are set at 0.18, 0.36, 0.54, 0.72 Jy beam [−][1]

km s [−][1] . The beam sizes for the blue- and red-shifted moment maps are 0.075 [′′] × 0.034 [′′] and 0.077 [′′] × 0.035 [′′], respectively. The blue and
red-shifted velocity ranges, in red, blue colors, correspond to ∼ 4000 and −2000 km s [−][1], respectively. The drawn cross coincides with the
position of Sgr A*.


**Figure** **4.** _(a_ _Top_ _Left)_ A scatter plot of the spectrum of H56α emission without continuum subtraction from the inner 0.22 [′′] × 0.27 [′′] of
Sgr A* using ten adjacent spectral windows. The rest frequency of H56α transition is at 0 km s [−][1] . _(b_ _Bottom_ _Left)_ Continuum subtracted
H56α emission from Sgr A* presented in histogram format. The spectrum of individual spectral window is scaled such that adjacent
spws are continuous. This scaling removes the flux scale across the band which varies at a level of few tenths of a percent. _(c_ _Right)_
Contour levels of red- and blue-shifted components of H56α are set at 1, 1.5, 2.25, 3.38, 5.06, 7.6 and 11.4 mJy per 0.099 [′′] × 0.05 [′′] beam
and 0.095 [′′] × 0.049 [′′] beam, respectively. The blue and red-shifted velocity ranges, in red, blue colors, correspond to ∼ 4000 and −2000 km
s [−][1], respectively. The drawn cross coincides with the position of Sgr A*.


MNRAS **000**, 1–12 (2020)

15









**2.0**


**1.5**


**1.0**


**0.5**


**0.0**


**-0.5**


**-1.0**


IRS 16C **-1.5**









**-2.0**


**2** **1** **0** **-1** **-2**
**Arc seconds**


**Figure** **5.** _(a)_ Grayscale continuum image of the inner 2.5 [′′] of Sgr A* at 44 GHz with a resolution of 0.087 [′′] × 0.036 [′′] (PA=13.41 [◦] ). The
dynamic range of this image with the peak flux 1.73 Jy beam [−][1] is 3700. _(b)_ The same as (a) except that contours are displayed at levels
-100, 100, 200, 300, 400, 500, 1000, 5000, 10000 µJy beam [−][1] . This data set was taken with the VLA on September 16, 2015.


MNRAS **000**, 1–12 (2020)

16 _Yusef-Zadeh_ _et_ _al._







**2.0**


**1.5**


**1.0**


**0.5**


**0.0**


**-0.5**


**-1.0**


**-1.5**


**-2.0**


**2** **1** **0** **-1** **-2**
**Arc seconds**


**Figure** **6.** _(a)_ A grayscale image of the inner 2.5 [′′] of Sgr A* at 44 GHz with a spatial resolution of 0.075 [′′] × 0.037 [′′] (PA=−0.86 [◦] ) taken on
April 3, 2018. The rms noise is 18µJy. Prominent features to the south are associated with the mini-spiral or Sgr A West. _(b)_ The same
as (a) except that contours are displayed at levels -100, -75, 75, 100, 125, 150, 200, 300, 400, 500, 750, 1000, 5000, 20000 µJy beam [−][1] .


MNRAS **000**, 1–12 (2020)

17













**Figure** **7.** _(a,_ _b)_ Two grayscale images of the inner 4 [′′] of Sgr A* at 44 GHz with two different brightness contrasts. The images are
similar to Figure 6 except they are convolved with a 0.076 [′′] Gaussian beam. The rms noise is 21µJy. The prominent feature to the west
is the mini-cavity.


MNRAS **000**, 1–12 (2020)

18 _Yusef-Zadeh_ _et_ _al._


**CONT: SGRA SPECLNM 3.9576E+10 IPOL SgrAKabill.Ka cub.1**


**400**


**300**



**CO** **SG** **S** **C** **8 9990** **09** **O** **SG**

**0.0** **0.5** **1.0**







**200**


**100**


**0**


**-100**


**-200**


**-300**


**-400**



**1.0**


**0.5**


**0.0**


**-0.5**


**-1.0**





**400** **300** **200** **100** **0** **-100** **-200** **-300** **-400**
**MilliArc seconds**

**C** **t** **t RA 17 45 40 0383003** **DEC** **29 00 28 068994**





**0.5** **0.0** **-0.5** **-1.0** **-1.5** **-2.0**
**Arc seconds**









**Figure** **8.** _(a)_ _Top_ _Left_ Contours of 35.72 GHz emission from the inner 0.45 [′′] of Sgr A* observed on March 9, 2014 at levels of (-2, -1, 1,
2,..., 8, 10, 50, 100, 200) ×81µJy beam [−][1] . The 8-GHz bandwidth was imaged in 24 different frequency channels and this map corresponds
to channel 16. The resolution of the image is 0.090 [′′] × 0.049 [′′] (PA=-5.38 [◦] ). _(b)_ _Top_ _Right_ Greyscale contours of 8.9 GHz emission with
levels at (-2, -1, 0..5, 0.5, 1, 1.5, 2, 3,..., 10, 12, 14,....20) times 0.1 mJy beam [−][1] . of 0.26 [′′] × 0.14 [′′] (PA=−1.5 [◦] ). _(c)_ _Bottom_ _Left_ A grayscale
15 GHz image of the inner 4 [′′] of Sgr A* with a resolution of 0.22 [′′] × 0.11 [′′] (PA=5.25 [◦] ). The highly blue-shifted negative velocity features
are labeled C1 to C4 (Royster et al. 2019). _(d)_ _Bottom_ _Right_ A 9 GHz image from data, as in (c), shows a grayscale image of the inner
4 [′′] of Sgr A*.


MNRAS **000**, 1–12 (2020)

19







**Figure** **8.** _(e)_ _Top_ A greyscale image of 9 GHz image using data taken in 17 April, 20014 with a resolution of 0.36 [′′] × 0.22 [′′] (PA=-1.88 [◦] ).
We used OBIT by splitting the 2 GHz bandwidth of 9 GHz data into 46 channels to account for frequency response of Sgr A* in each
frequency channel before the final image was made. Similar imaging was done with data taken on 17 August, 2019 and the features
described here were identified in both epochs. _(f)_ _Bottom_ Similar to (e) except with different contrasts to bring out faint features.


MNRAS **000**, 1–12 (2020)

20 _Yusef-Zadeh_ _et_ _al._











**Figure** **9.** _(a,_ _b)_ Grayscale 9 GHz continuum images of the inner of 20 [′′] of Sgr A* with a resolution of 0.35 [′′] × 0.18 [′′] (PA=5.61 [◦] ). The
flux density ranges between -0.6 and 10 mJy beam [−][1] with two different contrasts. This data set was taken on August 17, 2019. Black
lines show the opening angle of the jet arsing from Sgr A* to the SW. The white lines point to a number of sources that lie diagonally
along the direction of the outflow.


MNRAS **000**, 1–12 (2020)

21



**-200** **0** **200** **400**



**3**


**2**







**1**


**0**


**-1**


**-2**


**-3**


**2** **1** **0** **-1** **-2** **-3**
**Arc seconds**


**Figure** **9.** _(c)_ Grayscale contours of 9 GHz emission with levels (-2, -1, 1, 2, 3, 4, 6, 8, 10, 14, 18, 22, 30, 40, 50, 80, 100, 200, 500)
×50µJy beam [−][1] . _(d)_ A schematic diagram of prominent features in the inner 20 [′′] of Sgr A*. The double-peaked blue and red-shifted
mmRL emission associated with Sgr A* is shown in color. The positions of some of the sources, such as bow-shock sources, indicated on
this figure may not be accurate.


MNRAS **000**, 1–12 (2020)

22 _Yusef-Zadeh_ _et_ _al._


**SG** **O** **3** **000** **ob t** **O** **0**

**-2** **0** **2** **4** **6** **8**


**-29 00 00**

N. arm



**15**



bent

filament



**30**


**45**


S. arm


**01 00**


**17 45 41.5** **41.0** **40.5** **40.0** **39.5** **39.0** **38.5** **38.0**
**Right ascension (J2000)**



**0** **2** **4** **6** **8**


**-29 00 00**


**15**


**30**


**45**


**01 00**


**17 45 41.5** **41.0** **40.5** **40.0** **39.5** **39.0** **38.5** **38.0**
**Right ascension (J2000)**

**Grey scale flux range= -0.44 10.00 MilliJY/BEAM**


**CO** **J** **33** **3** **S** **C** **5** **09** **O** **J** **33** **ob t**

**0.0** **0.5** **1.0**


**10**


**8**


**6**


**4**


**2**


**0**


**-2**


**-4**


**-6**


**-8**


**15** **10** **5** **0** **-5** **-10** **-15**
**Arc seconds**

**Center at RA 17 33 02.70579** **DEC -13 04 49.5482**



**10**


**5**


**0**


**-5**


**-10**



**CO** **Grey scale flux range= -2.35 10.00 MilliJY/BEAM** **SG** **S** **C** **5** **09** **O** **sg** **a** **ob t**

**-10** **0** **10**


bent
filament


Radio jet


minicavity


E. arm


Radio jet


**10** **5** **0** **-5** **-10**
**Arc seconds**

**Center at RA 17 45 40.03830** **DEC -29 00 28.0690**



**Figure** **10.** _(a)_ 1-1.4 GHz image of the mini-spiral constructed by combining eight spectral windows with a resolution of 2.68 [′′] × 2.01 [′′]

(PA=36 [◦] ). _(b)_ Identical to (a) except grayscale contours are presented with levels -2, 2, 3, 4, 5, 7, 10, 15, 20, 30, 50 mJy beam [−][1] . The
coordinates are shown as offsets from the peak position of Sgr A*. _(c)_ Contours of 20cm emission from a narrow spectral window between
1.25 and 1.31 GHz with levels at (-4, 4, 5, 6, 7, 8, 9, 10, 15, 20 30, 50, 100) × 2 mJy beam [−][1] with a spatial resolution 2.94 [′′] × 2.17 [′′]

(PA=37.8 [◦] ). _(d)_ Radio emission from the calibrator J1733-1304 corresponding to the lowest frequency spectral window at 1.0 GHz with
a peak flux density of 4.02 Jy beam [−][1] and contour levels set at (1, 2, 3,....,9) mJy beam [−][1] with a resolution of 1.85 [′′] × 1.65 [′′] (PA=49.92 [◦] ).


MNRAS **000**, 1–12 (2020)

23



**G** **SG** **S** **C** **6** **5** **09** **O** **0c** **b** **C**



**0** **10** **20**



**0** **10** **20**



**0** **10** **20**



**0** **10** **20**



**5**



**6**



**-29 00 00**


**15**


**30**


**45**


**01 00**


**-29 00 00**


**15**


**30**


**45**


**01 00**


**-29 00 00**


**15**


**30**


**45**


**01 00**


**-29 00 00**


**15**


**30**


**45**


**01 00**



**3**



**4**



**7** **8** **9** **10**


**11** **12** **13** **14**



**15** **16**



**17** **18**



**17 45 42** **40** **38**



**17 45 42** **40** **38**
**Right ascension (J2000)**



**O** **Grey scale flux range= -1.00 30.00 MilliJY/BEAMSG** **S** **C** **6** **0** **09** **O** **sg** **a** **ob t**



**-10** **0** **10** **20** **-130**



**-130** **0** **10** **20** **-130**



**-130** **0** **10** **20** **-130**



**-130** **0** **10** **20** **30**



**5**



**6**



**40**


**20**


**0**


**-20**


**-40**

**40**


**20**


**0**


**-20**


**-40**

**40**


**20**


**0**


**-20**


**-40**

**40**


**20**


**0**


**-20**


**-40**



**15** **16**


**40** **20** **0** **-20** **-40**



**3**



**4**



**7** **8** **9** **10**


**11** **12** **13** **14**



**17** **18**


**40** **20** **0** **-20** **-40**
**Arc seconds**



**Center at RA 17 45 40.03830 DEC -29 00 28.0690**

**Grey scale flux range= -10.00 30.00 MilliJY/BEAM**
**C** **t** **k fl** **3 0000E** **00 JY/BEAM**


**Figure** **11.** _(a)_ Channel maps corresponding to 16 spectral windows are labeled between 1 and 2 GHz. Black traces radio emission
whereas white in the minispiral is seen in absorption. These channel maps reveal both thermal and nonthermal sources simultaneous
across the 1 GHz bandwidth in the L band. _(b)_ Channel maps corresponding to 16 spectral windows are labeled between 1 and 2
GHz. Black traces radio emission whereas white is seen in absorption. These channel maps reveal both thermal and nonthermal sources
simultaneous across a 1 GHz bandwidth.


MNRAS **000**, 1–12 (2020)

red represents the eight low frequency spectral windows. The green color represents the entire bandwidth.


MNRAS **000**, 1–12 (2020)

25


**Figure** **12.** _(c)_ A schematic diagram showing prominent nonthermal (hatched) and thermal (dotted) features at 20cm including a
symmetric jet-like feature with respect to Sgr A* and a bent jet-like feature to the north of Sgr A*.


MNRAS **000**, 1–12 (2020)

26 _Yusef-Zadeh_ _et_ _al._

















**Figure** **13.** _(a_ _Left)_ Images of the Sgr A East SNR and the mini-spiral are shown using the 20cm broad band between ∼1 and ∼1.9
GHz with a resolution of 2 [′′] .68 × 2 [′′] .03 (PA=36 [◦] .38). _(b_ _Right)_ Similar to (a) except a narrow band at 1.24 GHz is displayed. _(c_ _Bottom)_
Broad band 20cm VLA image of the region to the SW of Sgr A* with a resolution of 1.69 [′′] × 0.65 [′′] (PA=170 [◦] .56).


MNRAS **000**, 1–12 (2020)

27













**Figure** **14.** _(a,b_ _top_ _Left_ _and_ _Right)_ Two possible orientations of the accretion disk presumed to be driving the jet from Sgr A*, as
viewed by an observer. The red and blue cones represent the red and blue-shifted arms of the jet, which have PA 60 and 240 [◦] E of N,
respectively. The jet axis is perpendicular to the plane of the disk (cyan), which may rotate clockwise (left) or counter clockwise (right).
The corresponding PA of the ascending node, Ω, is indicated in each case. _(c_ _Bottom)_ For comparison, we show a jet-disk system with
orbital plane matching that of the clockwise stellar disk.


MNRAS **000**, 1–12 (2020)


</paper>

## Items to check

```json
[
 {
  "path": "processing.imaging.final_beam.evidence[2]",
  "value": "ALMA H30a: 0.30'' x 0.33''; VLA H52a: 77 x 35 mas (PA ~ -2 deg); VLA H56a: ~95 x 49 mas (PA ~ 82 deg); VLA 44 GHz: 0.087'' x 0.036'' and 0.075'' x 0.037''; VLA 1-1.4 GHz: 2.68'' x 2.01''",
  "failed_quote": "The spectra shown in Figure 4a,b were obtained over a 0.22′′ ×0.27′′ region centered on Sgr A* with a spatial resolution of ∼ 95 × 49 mas and PA∼ 82◦."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Self-calibrate VLA A-array broadband visibility data in phase and amplitude on Sgr A*, split bandwidth into multiple channels to account for frequency response, and construct high-dynamic-range continuum images and spectral channel cubes across Q, Ka, Ku, X, and L bands.",
  "failed_quote": "Several phase and amplitude self-calibration procedures were applied to the data in OBIT (Cotton 2008) using the bright radio source Sgr A* before MFImager was used to construct a cube of 16 channels corresponding to each spectral window."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Compute volume emission measure (VEM), electron density, and ionized mass of feature J1 from its 36 GHz optically-thin free-free flux density; estimate equipartition magnetic field of the pc-scale jet from its 1.6 GHz surface brightness; infer 3D jet and inner accretion disk orientation angles from PA and radial velocity signs.",
  "failed_quote": "For the observed jet diameter (≈ 2′′) and 1.6 GHz surface brightness ≈ 0.2 mJy beam−1, we deduce an equipartition magnetic field ∼ 0.2 mG using standard (but uncertain) assumptions: an E−2 electron spectrum running between 10 MeV and 100 GeV and equal energy density in electrons and protons."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[2]",
  "value": "J1 36 GHz integrated flux ~ 0.2 mJy; J1 dimensions 0.2'' x 0.02'' x 0.02''; jet diameter ~ 2'', 1.6 GHz surface brightness ~ 0.2 mJy beam^-1",
  "failed_quote": "For the observed jet diameter (≈ 2′′) and 1.6 GHz surface brightness ≈ 0.2 mJy beam−1, we deduce an equipartition magnetic field ∼ 0.2 mG using standard (but uncertain) assumptions: an E−2 electron spectrum running between 10 MeV and 100 GeV and equal energy density in electrons and protons."
 },
 {
  "path": "analysis_steps[4].assumptions[1].evidence[0]",
  "value": "Equipartition between electrons and protons with an E^-2 electron energy spectrum between 10 MeV and 100 GeV",
  "failed_quote": "For the observed jet diameter (≈ 2′′) and 1.6 GHz surface brightness ≈ 0.2 mJy beam−1, we deduce an equipartition magnetic field ∼ 0.2 mG using standard (but uncertain) assumptions: an E−2 electron spectrum running between 10 MeV and 100 GeV and equal energy density in electrons and protons."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Applying phase and amplitude self-calibration and splitting/imaging VLA broadband L-band (1-2 GHz) and X-band (9 GHz) data.",
  "failed_quote": "Several phase and amplitude self-calibration procedures were applied to the data in OBIT (Cotton 2008) using the bright radio source Sgr A* before MFImager was used to construct a cube of 16 channels corresponding to each spectral window."
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Constructing a 16-channel continuum cube from the VLA L-band (1-2 GHz) spectral windows.",
  "failed_quote": "Several phase and amplitude self-calibration procedures were applied to the data in OBIT (Cotton 2008) using the bright radio source Sgr A* before MFImager was used to construct a cube of 16 channels corresponding to each spectral window."
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Equipartition magnetic field of the pc-scale jet = 0.2 mG",
  "failed_quote": "For the observed jet diameter (≈ 2′′) and 1.6 GHz surface brightness ≈ 0.2 mJy beam−1, we deduce an equipartition magnetic field ∼ 0.2 mG using standard (but uncertain) assumptions: an E−2 electron spectrum running between 10 MeV and 100 GeV and equal energy density in electrons and protons."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The sub-arcsecond high-velocity ionized gas more likely arises from entrained material accelerated outwards by a collimated jet rather than a Keplerian disk.",
  "failed_quote": "However, our observations have wider frequency coverage and find significantly broader line widths, >∼4000km s−1 consistent with Keplerian motion at about 1/5 the observed angular scale of the emission."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[1]",
  "value": "Highly inclined cool Keplerian accretion disk model for the broad double-lobed recombination line emission (Murchikova et al. 2019); rejected because the newly detected >~ 4000 km s^-1 line widths correspond to Keplerian motion at 1/5 the observed angular scale.",
  "failed_quote": "However, our observations have wider frequency coverage and find significantly broader line widths, >∼4000km s−1 consistent with Keplerian motion at about 1/5 the observed angular scale of the emission."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Colliding stellar winds in the IRS 13E cluster as the sole origin of its X-ray emission; the authors propose jet collision with the minicavity as an alternative.",
  "failed_quote": "Recent analysis of X-ray data concludes that colliding winds of mass-losing stars in the cluster are responsible for production of X-rays (Wang et al. 2020; Zhu et al. 2020)."
 }
]
```
