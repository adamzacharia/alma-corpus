# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.496.5330F\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–10 (2020) Preprint 29 June 2020 Compiled using MNRAS L [A] TEX style file v3.0

## **Gas kinematics of key prebiotic molecules in GV Tau N** **revealed with an ALMA, PdBI, and Herschel synergy**


### A. Fuente, [1][⋆] S. P. Trevi˜no-Morales [2], R. Le Gal [3], P. Rivi`ere-Marichalar [1], P. Pilleri [4], M. Rodr´ıguez-Baras [1], and D. Navarro-Almaida [1]

1 _Observatorio_ _Astron´omico_ _Nacional_ _(OAN,IGN),_ _Alfonso_ _XII,_ _3,_ _28014,_ _Madrid,_ _Spain_
2 _Chalmers_ _University_ _of_ _Technology,_ _Department_ _of_ _Space,_ _Earth_ _and_ _Environment,_ _SE-412_ _93_ _Gothenburg,_ _Sweden_
3 _Center_ _for_ _Astrophysics_ _|Harvard_ _&_ _Smithsonian,_ _60_ _Garden_ _St.,_ _Cambridge,_ _MA_ _02138,_ _USA_
4 _Institut_ _de_ _Recherche_ _en_ _Astrophysique_ _et_ _Plan ˜Al’tologie,_ _9_ _avenue_ _du_ _colonel_ _Roche,_ _31028_ _Toulouse_ _Cedex_ _4,_ _France_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
A large effort has been made to detect warm gas in the planet formation zone of
circumstellar discs using space and ground-based near infrared facilities. GV Tau N,
the most obscured component of the GV Tau system, is an outstanding source, being
one of the first targets detected in HCN and the only one detected in CH 4 so far.
Although near infrared observations have shed light on its chemical content, the physical structure and kinematics of the circumstellar matter remained unknown. We use
interferometric images of the HCN 3→2 and [13] CO 3→2 lines, and far-IR observations
of [13] CO, HCN, CN and H 2 O transitions to discern the morphology, kinematics, and
chemistry of the dense gas close to the star. These observations constitute the first
detection of H 2 O towards GV Tau N. Moreover, ALMA high spatial resolution (∼ 7
au) images of the continuum at 1.1 mm and the HCN 3→2 line resolve different gas
components towards GV Tau N, a gaseous disc with R∼25 au, an ionized jet, and one
(or two) molecular outflows. The asymmetric morphology of the gaseous disc shows
that it has been eroded by the jet. All observations can be explained if GV Tau N
is binary, and the primary component has a highly inclined individual disc relative
to the circumbinary disc. We discuss the origin of the water and the other molecules
emission according to this scenario. In particular, we propose that the water emission
would come from the disrupted gaseous disc and the molecular outflows.


**Key** **words:** stars: formation – stars: individual (GV Tau N) – stars: variables: T
Tauri – protoplanetary discs – ISM: jets and outflows – astrochemistry



**1** **INTRODUCTION**


A fraction of the gas and dust in protoplanetary discs will
end up in planets and may constitute the basis to form prebiotic species. A large effort has been made to detect the
warm gas in the planet formation zone using Spitzer and
ground-based facilities such as the Very Large Telescope
(VLT) and the Keck Observatory telescopes. In a pioneering
work, Lahuis et al. (2006) detected strong HCN absorption
toward one source, IRS 46, from a sample of more than 100
Class I and II sources located in nearby star-forming regions.
Later, Gibb et al. (2007) detected the HCN absorption in GV
Tau. Since then, the observation of absorption and emission
lines have provided a view of the molecular content of the


⋆ E-mail: a.fuente@oan.es


© 2020 The Authors



very inner regions of protoplanetary discs with several detections of molecules such as CO, CO 2, H 2 O, OH, HCN,
and C 2 H 2 (Salyk et al. 2007, 2008, 2011, 2019; Carr & Najita 2008, 2011, 2014; Pontoppidan et al. 2010; Najita et al.
2010, 2013; Kruger et al. 2011; Doppmann et al. 2008, 2011;
Fedele et al. 2011; Mandell et al. 2012; Bast et al. 2013; Gibb
& Horne 2013; Sargent et al. 2014; Banzatti et al. 2017). In
addition, the organic species CH 4 has been detected towards
GV Tau N (Gibb & Horne 2013). In many cases the profiles
of the detected lines are broad and centrally peaked (Mandell et al. 2012; Salyk et al. 2019). This kind of centrally
peaked profile is observed even for discs with previously determined high inclination angle and has been interpreted as
emission from a disc wind. By now, direct imaging of the circumstellar material remains difficult with current telescopes,
which challenges the interpretation.

2 _A._ _Fuente_ _et_ _al._


The launch of the Herschel Space Observatory allowed
to investigate the chemical content of discs at far-IR wavelengths (Thi et al. 2011; Salinas et al. 2016), providing valuable information on the abundance of H 2 O in large disc samples (Hogerheijde et al. 2011; Riviere-Marichalar et al. 2012;
Meeus et al. 2012; Fedele et al. 2012, 2013; Podio et al. 2013;
Salinas et al. 2016; Alonso-Mart´ınez et al. 2017). Warm water coming from the inner R∼2−3 au disc region was detected
through the 63.3 µm line observed with PACS (RiviereMarichalar et al. 2012; Meeus et al. 2012). The emission
of the ground ortho and para water lines are thought to
originate in the disc surfaces where UV radiation desorbs
the water from the icy mantles (Hogerheijde et al. 2011; Podio et al. 2013; Salinas et al. 2016). In Class I sources, a
fraction of the warm water can be emitted in shocks along
the outflow cavity as well (Kristensen et al. 2012; Karska
et al. 2013; Mottram et al. 2014). Thus, the study of farIR H 2 O lines provides essential information to characterize
the H 2 O abundance from the inner to the cold outer regions
of discs. Moreover, several guaranteed and open time Herschel Key Programs: ”Water In star-forming regions with
Herschel” (WISH; van Dishoeck et al. 2011), ”CHEmical
Survey of Star-forming regions” (CHESS; Ceccarelli et al.
2010), ”Dust, Ice and Gas in Time” (DIGIT; Green et al.
2013), and ”GAS in protoplanetary systems (GASPS Mathews et al. 2010; Dent et al. 2013), have provided information
on water in a large number of low-mass protostars at different evolutionary stages, allowing us to figure out how water
is transported from the molecular cloud to planet-forming
discs.

The chemical composition of discs in Class I protostars
is receiving increasing attention. The presence of discs in
all Class 0 protostars (ages∼0.2 Myr) is still debated (see
e.g. Maret et al. 2020). If indeed discs are present, their
masses have been suggested to be high (∼0.05−0.1 M ⊙ ; Jørgensen et al. 2009) and they might be gravitationally unstable. Conversely, the masses of Class II discs in Taurus
and Orion (ages∼1−5 Myr) have been well studied and are
found to have a median mass of 0.001 M ⊙ (e.g. Eisner et al.
2008; Andrews et al. 2013; Tobin et al. 2020). These median masses are low compared with the amount of matter
needed to form giant planets, estimated to be 0.01−0.1 M ⊙
(e.g. Weidenschilling 1977; Desch 2007). Class I discs would
then be in a transitional stage between massive, highly unstable protoplanetary discs to stable discs in which planet
formation is progressing. The discs around Class I objects
may therefore accurately represent the initial mass budget
for forming planets.
GV Tau (Haro 6-10) is a T Tauri binary system embedded in the L1524 molecular cloud (d=180±17 pc) (Gaia
Collaboration 2018). It is one of the few young binary systems with the primary source (GV Tau S) optically visible,
and the companion (GV Tau N), located 1.2” to the North,
obscured. It is associated with a parsec-scale Herbig-Haro
flow which extends for 1.6 pc to the North and ∼1 pc to the
South (Devine et al. 1999; Movsessian & Magakian 1999).
Both stars have been classified as Class I objects with masses
of M∼0.8 M ⊙ and ages of ∼ 3 Myr (Doppmann et al. 2008).
Only the GV Tau N disc has been detected in the HCN
and C 2 H 2 absorption ro-vibrational lines (Gibb et al. 2007,
2008). Indeed GV Tau N is an outstanding source, being
one of the first targets detected in HCN and the only one



detected in CH 4 (Gibb & Horne 2013). Moreover, the mass
of its protoplanetary disc falls near the Minimum Mass Solar Nebula, and it may have just enough mass to form giant
planets (Sheehan & Eisner 2014). Being a Class I disc with
a chemistry rich in organic species, GV Tau N is a priority
target to investigate how organics are delivered from the gas
rich disc to planets. Fuente et al. (2012) reported interferometric images of the HCN 3→2 and HCO [+] 3→2 lines at
an angular resolution of ∼50 au. Only the HCN 3→2 emission was detected towards GV Tau N, and was interpreted
as coming from the unresolved planet forming region.
This paper explores the physical structure, kinematics,
and chemistry of the gas in the planet forming region of
GV Tau N based on high spatial resolution images of the
HCN 3→2 and the [13] CO 3→2 lines, and far-IR observations
of the high excitation lines of [13] CO, H 2 O, HCN and CN.
In particular, we present the first water detection in this

system.


**2** **OBSERVATIONS**


GV Tau was observed with the IRAM [1] Plateau de Bure
Interferometer (PdBI), the Atacama Large Millimeter/submillimeter Array (ALMA) and the HIFI instrument (de
Graauw et al. 2010) on board the Herschel Space Telescope
(Pilbratt et al. 2010). Observations of the [13] CO 3→2 and
C [18] O 3→2 lines were carried out using the Plateau de Bure
Interferometer (PdBI) in its A configuration during OctoberNovember, 2014. This configuration provided a beam of
0.35” × 0.18” PA 25 [◦] (∼63 au×32 au at the Taurus distance).
During the observations two 40 MHz correlator units were
placed at the frequencies of the [13] CO (330.588 GHz) and
C [18] O 3→2 (329.330 GHz) lines providing a spectral resolution of 78 kHz. The C [18] O 3→2 line was not detected with
an rms of 46 mJy/beam. Calibration and imaging were performed using the Grenoble Image and Line Data Analysis
Software (GILDAS; Pety 2005).
Our study uses the HCN 3→2 line observations obtained
from the ALMA archive. These observations were performed
during Cycle 4 within project number 2016.1.00813.S. The
line was observed with a spectral resolution of ∼488.25 kHz
and the synthesized beam is 0.07 [′′] × 0.04 [′′] with PA 27 [◦] . This
provides an unprecedented spatial resolution of ∼12 au×7 au
and the achieved rms is 2.4 mJy/beam. We produced a
1.1 mm continuum image with the channels and spectral
windows empty of line emission. The continuum image has
a synthesized beam of 0.06” × 0.03” with PA 27 [◦], and a rms
of 0.13 mJy/beam. The data were manually calibrated using
the 4.7.1 version of the Common Astronomy Software Applications (CASA; McMullin et al. 2007) while the imaging
process was performed using CASA version 5.4.1 following
the National Radio Astronomy Observatory (NRAO) imaging guide.
The Herschel Space Observatory (Pilbratt et al. 2010)
observations presented here were obtained with the heterodyne instrument for the far infrared HIFI (de Graauw
et al. 2010) (OT ~~1~~ ~~a~~ fuent ~~e~~ ~~2~~ ). The basic data reduction


1 IRAM is supported by INSU/CNRS (France), MPG (Germany), and IGN (Spain)


MNRAS **000**, 1–10 (2020)

3


**Figure** **1.** _Left:_ Continuum image at 1.1 mm as observed with ALMA. Levels are 5σ, 10σ, 20σ to 100σ by 20σ where σ=0.13 mJy/beam.
_Center:_ Zero moment map of the HCN 3→2 line in units of Jy/beam×km s [−][1] . Contour levels are 0.01, 0.025, 0.05, 0.1, 0.15, and 0.175
Jy/beam×km/s. The red line indicates the jet direction derived from the 1.1mm continuum observations, and the circle marks the radius
of the gaseous disc, R=0.18”. In white, the contours of the 1.1 mm continuum emission. _Right:_ Interferometric spectra of the HCN 3→2
and [13] CO 3→2 lines towards the star position (black and white crosses in left and center panels, respectively) as observed with ALMA
and PdBI. The HCN 3→2 spectrum at the emission peak in the gaseous disc (white and black triangles in the left and center panels)
and the averaged HCN 3→2 spectrum in the region R<0.18” are shown in the right panel. The intensity scale in the spectra is main
beam brightness temperature. Vertical lines mark v lsr =6.3 km s [−][1] and 8.7 km s [−][1] .



was performed using the standard pipeline provided with
the version 7.0 of HIPE (Ott 2010) and then exported to
GILDAS/CLASS (Pety 2005) for a more detailed analysis.


**3** **(SUB-)MILLIMETER** **INTERFEROMETRIC**
**IMAGES**


Fig. 1 shows the high angular resolution 1.1 mm continuum
image obtained from ALMA data. Based on a 2D Gaussian fit, we derive the flux, position and size of the compact
continuum source. The estimated flux is ∼48 mJy which
is in good agreement with the previous measurement by
Fuente et al. (2012). The size of the compact source is 94±1
mas×66±1 mas, which constrains the radius of the dusty
circumstellar disc to R∼8 au. In addition to the compact
source, elongated emission is detected in the direction of the
outflow at >10σ level (see Fig. 1). It should be noted that the
coordinates of the compact continuum source are α(J2000)
= 04 [h] 29 [m] 23 [s] .731, δ(J2000) = 24 [◦] 33 [′] 01 [′′] .11. This position is
offset 0.19 [′′] to the South as compared to the position measured by Fuente et al. (2012), which would imply proper motion of ∼(0,−34) mas yr [−][1] . The most recent estimation of the
proper motions of GV Tau N are (+8.695±0.853) mas yr [−][1]

in right ascension, and (−25.085± 0.672) mas yr [−][1] in declination (Gaia Collaboration 2018). Taking into account the
lower angular resolution of Fuente et al. (2012), beam∼0.5 [′′],
we consider that the observed displacement can be due to
the proper motions of GV Tau N. The position of the continuum source is adopted as offset (0 [′′],0 [′′] ) through this paper.

Reipurth et al. (2004) measured a 3.6 cm flux of
0.10±0.01 mJy towards GV Tau N. We estimate a flux of
4.6±0.5 mJy for the extended component, which would imply a 3.6 cm to 1.1 mm spectral index, α 1 [3] . [.] 1 [6] mm [cm] [∼] [+][1.1.] [This]


MNRAS **000**, 1–10 (2020)



spectral index is higher than the one expected for an ionized spherical wind, α∼+0.6, and usually found in T Tauri
and Herbig Ae/Be stars (Skinner et al. 1993; Alonso-Albi
et al. 2009). This higher spectral index is still consistent
with an ionized wind but with unconventional assumptions,
i.e a velocity power law v(R)∝R or a density law, n e (R)∝R [−][3]

(Panagia 1988). We should also consider the possibility that
radio emission has varied on time scales of tens of years.
Variability is a common phenomenum in young T Tauri systems (Ubach et al. 2017; Liu et al. 2017). It would be also
possible that we have overestimated the flux coming from
the jet because a fraction of the extended emission is coming
from dust thermal emission. Simultaneous measurements of

the flux at several wavelengths would be desirable to further
constrain the cm-mm spectral index.


Mid-infrared interferometry (VLTI/MIDI) observations
to probe the circumstellar material around GV Tau N and S
were carried out by Roccatagliata et al. (2011). They modeled the emission assuming the existence of two different
black-body components, which accounts for the different disc
regions. They obtained that the emission within 1.5 au has
a temperature of 900 K, while a second colder emission at
150 K originates within 10 au from the central star. The sizes
of these two components are consistent with the size of the
1.1mm compact source as observed with ALMA for which
we derive a radius R∼8 au. Based on the measureded visibil
ities, they estimate an inclination, _i_ = 80 [◦] for the GV Tau N
disc. This value is consistent with GV Tau N being a highly
obscured star.


Intense emission of the HCN 3→2 line is detected to
wards GV Tau N. We have produced the zero-moment map
using only the channels with emission >3σ. Based on this
map, we estimate that the size of the HCN emission is
R∼0.18”, significantly larger than the small compact con

4 _A._ _Fuente_ _et_ _al._


tinuum clump (see Fig. 1). The total velocity integrated
flux within R∼0.18” is ∼1.4 Jy/beam×km s [−][1] . In order to
check for possible filtering in the HCN 3→2 line map, we
have compared ALMA fluxes with those measured by Fuente
et al. (2012) using the PdBI. Fuente et al. (2012) derived
a total flux of 3.64±0.21 Jy×km s [−][1] in a region of 0.32 [′′] ×
0.25 [′′] . Therefore, the high spatial resolution ALMA observations recover ∼ 40% of the flux detected in PdBI observations. This is consistent with the zero-moment map shown
in Fig. 1, which presents evidence of a resolved component
that extends towards the East.

An intense and asymmetric molecular ring is observed
in the HCN 3→2 image shown in Fig. 1. The inner and
outer radii of this ring are R in ∼0.04” (6 au) and R out ∼0.18”
(17 au), respectively. In the azimuthal direction, the minimum of emission is located in the outflow direction, suggesting that the jet has eroded the circumstellar material,
sweeping out the molecular gas. In Fig 1 we also show the
HCN 3→2 spectra towards the star and the emission peak
in the molecular ring. The velocity profile towards the star
is wide, with Full Width Half Power (FWHP) of ∼12 kms [−][1],
and asymmetric, with the emission at highest velocities in
the redshifted range. The spectrum towards the emission
peak is narrower with FWHP∼10 km s [−][1], and presents two
peaks located at blue-shifted and red-shifted velocities with
respect to the systemic velocity, which is not expected in a
pure rotation scenario. This wide line is not surprising and
it is most likely due to the strong interaction between the
jet and the surrounding molecular gas. Also, self-absorption
by the lower density envelope at the systemic velocity would
produce the two-peak feature.
The [13] CO 3→2 line is detected towards GV Tau N with
a complex profile (see Fig. 1). The emission presents high
velocity wings at the same velocities as the HCN 3→2 spectrum. In addition, a narrow, FWHP∼2 km s [−][1], absorption
feature is observed at v lsr = 9.0 km s [−][1], i.e., red-shifted from
the systemic velocity of v lsr = 6.3 km s [−][1] and consistent with
the emission coming from infalling gas. It is interesting to
note that Doppmann et al. (2008) detected HCN and C 2 H 2
absorbing gas at v lsr = 8.7±0.3 km s [−][1] (blue-dashed line in
Fig. 1), which is close to the velocity of the absorption detected in [13] CO. The signal-to-noise ratio of our [13] CO 3→2
observations does not allow to obtain a good quality image.


**4** **FAR** **INFRARED** **LINES**


High excitation lines of [13] CO, H 2 O, HCN and CN were observed with high spectral resolution using the instrument
HIFI onboard Herschel (see Fig. 2). High signal-to-noise
detections were obtained for the [13] CO 10→9, and H 2 O
1 11 →0 00, 1 10 →1 01 and 2 02 →1 11 lines. The HCN 7→6 and
CN 6→5 lines were detected at 4σ level (see Fig. 2). Unfortunately, the Herschel angular resolution does not allow to
resolve the two components of the binary, GV Tau N and
GV Tau S, and we need to use the kinematic information to
discern the origin of the observed lines.
It is remarkable the difference between the profile of the
13 CO 10→9 line and those of the H 2 O lines. The 13 CO 10→9
line presents a narrow profile, with FWHP∼2.7 km s [−][1], and
is centered at v lsr =6.74±0.05 km s [−][1] . The profiles of the
ground ortho- and para-water lines are significantly wider,



and show a strong absorption at v lsr ∼6.0 km s [−][1] . The absorption is not observed in the higher excitation p-H 2 O 2 02 →1 11
line (E u /k∼100 K). Indeed, the profile of the water lines can
be fitted using two components: i) a wide Gaussian with
FWHP∼ 8 km s [−][1], and (ii) a narrower component with
FWHP∼2.7 km s [−][1], similar to [13] CO. Fig. 2 shows the decomposition of the water line profiles in these two components
that we hereafter name wide and narrow components. The
Gaussian fits to these components are shown in Table A1. It
is specially interesting to discern whether the emission of the
wide component arises in the compact gaseous disc detected
with the ALMA maps or it is coming from a large scale
outflow(s). In order to explore the origin of this component,
we compare its profile with the mean HCN 3→2 spectrum
in the region R<0.3” (see Fig. 3). The wings of the p-H 2 O
2 02 →1 11 line are similar to those of the interferometric HCN
3→2 line, suggesting that the origin might be similar. We
further discuss the origin of this component in Section 6.
In the bottom panels of Fig. 2 we show the profiles of the
water narrow component. This component presents absorption at blue-shifted velocities. We recall that the absorptions
observed in the NIR observations lie at red-shifted velocities,
∼8.7 km s [−][1] . An absorption at similar velocity, ∼9 km s [−][1],
has been observed in our PdBI spectrum of the [13] CO 3→2
line. Thus, the blue absorption features detected in the FIR
water lines are more likely caused by a colder layer in the
outer envelope. Fig. 2 also shows the spectra of the HCN
7→6 and CN 5→4 lines. These spectra only present the narrow component. We cannot discard, however, the existence
of a weaker wide component that it is not detected because
of the low S/N of the detections. This should be the case
of HCN 7→6, for which emission presents a slightly wider
spectrum. It should be noticed that the peak of the weak
and narrow HCN 7→6 lines is at the velocity of the dip
observed in the ALMA HCN 3→2 profile, suggesting that
the narrow line observed with Herschel is probing the lower
density envelope.


**5** **KINEMATICS** **OF** **THE** **MOLECULAR** **GAS**


In Fig. 4 we present the first and second moment maps of
the HCN 3→2 emisison as observed with ALMA. The emis
sion at high red- and blue-shifted velocities, |v − v 0 | - 4 km
s [−][1], shows the presence of two misaligned outflow lobes: the
red lobe is close to the direction defined by the giant Herbig
Haro flow, PA=222 [◦] (Devine et al. 1999) (hereafter, _Jet_ 1),
and the blue lobe is placed at PA=195 [◦], the direction of the
Herbig Haro jet detected by Movsessian & Magakian (1999)
(hereafter, _Jet_ 2). This misalignment can be interpreted as
the consequence of a precessing bipolar outflow. Alternatively, these lobes might belong to two different bipolar outflows.
In order to discern between these two scenarios we in
spect the channel maps shown in Fig. A1 and Fig. A2. The
directions of _Jet_ 1 and _Jet_ 2 are indicated in each panel. The
red lobe of _Jet_ 1 is clearly seen in panels v lsr =10.28 km s [−][1]

to 13.36 km s [−][1], located SW from the star. The blue counterpart is missing in the HCN 3→2 channels maps. The molecular outflow is formed by the circumstellar matter that is
being swept up by the ionized jet. The lack of a blue lobe
is due to the absence of the molecular gas in this direction,


MNRAS **000**, 1–10 (2020)

5


**Figure** **2.** Spectra of the [13] CO 10→9, H 2 O 1 11 →0 00, 1 10 →1 01 and 2 02 →1 11 lines obtained with the HIFI instrument on board the Herschel
Space Observatory towards GV Tau N. The systemic velocity, v lsr =6.3 km s [−][1], is indicated with the red dashed line.



**Figure** **3.** Spectra of the H 2 O 2 02 →1 11 line obtained with the
HIFI instrument on board the Herschel Space Observatory towards GV Tau N. For comparison we have plotted the averaged
ALMA spectrum of HCN 3→2 in a circle of R<0.3” around GV
Tau N scaled to match the intensity of the H 2 O 2 02 →1 11 line.
The systemic velocity, v lsr =6.3 km s [−][1], is indicated with the red

dashed line.


where a wide cavity has already being excavated by the jet,
and the molecular gas has been cleaned. The existence of
high velocity gas along _Jet_ 2 is not such clear since the kinematic signatures of the blue and red lobes are mixed with
the disc rotation. High velocity gas along _Jet_ 2 is detected in
panels v lsr =−1.48 km s [−][1] to 2.16 km s [−][1] . Fig. A2 shows that
high velocity gas is detected in panels v lsr =−13.08 km s [−][1]

to 14.48.16 km s [−][1] which is located in the _Jet_ 2 direction

and can be interpreted as the red lobe of this outflow. Given
the angular resolution of the observations, it might also be
associated to the walls of the cavity excavated by _Jet_ 1.
Fig. 5 shows the position-velocity (p-v) diagrams along
_Jet_ 1 and _Jet_ 2. The _Jet_ 1 p-v diagram presents clumpy
emission with small changes in the velocity between one
small bright clump and the following. These bright spots
are also observed as narrow features in the HCN 3→2 spectrum shown in Fig 1. This kind of ”saw-like” features have
been detected in high velocity jets and were interpreted as
oblique shocks formed in the interphase between the high
velocity jet and the circumstellar matter (Santiago-Garc´ıa


MNRAS **000**, 1–10 (2020)



et al. 2009). In this scenario, the clumps at red-shifted and
blue-shifted velocities correspond to the back and front walls
of the cavity excavated by the jet in the gaseous disc. This
interpretation is also consistent with the morphology observed in the zero moment map of the HCN 3→2 emission
(see Fig. 1). The outflow _Jet_ 1 crosses the molecular ring
through the azimuthal minimum of the HCN 3→2 emission,
probing that the gas has been swept up.

The p-v diagram along _Jet_ 2 is also shown in Fig. 5.The
outflow _Jet_ 2 presents bipolar morphology with the highest velocities close to the star. In this case, the blue lobe is
more intense than the red lobe, contrary to the case of _Jet_ 1.
However, an intense clump is detected at 10 km s [−][1] in the
direction of _Jet_ 2 (R1 in Fig. 5) that might be disc gas accelerated by the _Jet_ 2. However, we need to be cautious in our
conclusions because the sensitivity and angular resolution of
the HCN 3→ observations do not allow to fully disentangle
_Jet_ 2 from the gas that is accelerated in the walls of the
cavity excavated by _Jet_ 1.

In order to explore the kinematics of the circumbinary
disc, we performed the p-v diagrams along the directions
perpendicular to _Jet_ 1 and _Jet_ 2, named _D_ 1 and _D_ 2, respectively (Fig. 5). The p-v diagrams along _D_ 1 and _D_ 2 present
emission in the four quadrants, which is not compatible with
a pure rotating disc. A combination of rotation and outflow
is necessary to explain this pattern. Furthermore, there is
a gap around the position of the stars with a size, R∼8 au,
in both diagrams. In spite of the highly disturbed kinematics, we can see a hint for Keplerian rotation in the p-v diagram along _D_ 1. For comparison we compare the observations
with the Keplerian curves for a star with M ∗ =0.8 M ⊙ and
inclination angles i=20 [◦], 40 [◦], and 65 [◦] . We find reasonable
agreement between the observations in the inner R<20 au
region and the Keplerian curves assuming i=40 [◦] curve. This
supports the interpretation that the HCN 3→2 line comes
from a rotating disc which kinematics is highly perturbed by
the interaction with the bipolar outflow(s). We recall that
there is a degeneracy between the stellar mass and the inclination angle. If GV Tau N is a binary, the stellar mass
content would be larger, and a lower inclination angle would

6 _A._ _Fuente_ _et_ _al._


**Figure** **4.** Continuum image at 1.1 mm and moment maps of the HCN 3→2 emission as observed with ALMA. Dashed lines indicate
the direction of the giant Herbig Haro flow at PA = 222 [◦] (Devine et al. 1999) and of the optical jet detected at PA=195 [◦] (Movsessian &
Magakian 1999). We also indicate the directions perpendicular to Jet 1, named D1, and to Jet 2, named D2. Panels _c)_ and _d)_ show the
same map with different colour scales to highlight the bipolar outflow(s) ( _c)_ ) or the rotation motion ( _d)_ ). The directions Jet 1, Jet 2,
D1 and D2 are selected to perform the position-velocity diagrams.


**Figure** **5.** Position-velocity diagrams of the HCN 3→2 line along the strips Jet 1, Jet 2, D1 and D2. In panel D1, we show the Keplerian
velocity curves assuming M ∗ =0.8 M ⊙ and i=20 [◦], 40 [◦], and 65 [◦] (i=0 [◦] would be face-on) for the circumbinary disc. Observational data fits
better the i=40 [◦] curve. Contour levels are 2σ to 5σ in steps of 1σ (σ=2.4 mJy/beam).



be required to fit the observations. This would be consistent
with the observed morphology, which is that expected for an
almost face-on disc.


Doppmann et al. (2008) proposed that GV Tau N could
be a binary to explain the large difference between the velocity of the lines coming from the stellar photosphere and the
molecular gas. The existence of two bipolar outflows would
also explain the kinematics observed in the ALMA HCN
3→2 cube. The most energetic outflow, _Jet_ 1, should be in
(or close to) the equatorial plane of the circumbinary disc
in order to explain the cavity cleaned of gas observed in
the HCN maps. The second outflow would be perpendicular, or close to the perpendicular direction, to the circumbinary disc, hence flowing away with little interaction with the
molecular gas (see a sketch in Fig. 6). This geometry would
imply that the two components of the binary are highly misaligned.


Binarity could also explain the different morphology of
the gas and dust around GV Tau N, the size of the dust continuum emission being smaller. Stellar binaries exert gravi


tational torques on inclined circumbinary discs causing radially differential precession and, under some circumstances,
warps in the disc. Large dust grains in thick discs pile up at
the warp location, forming narrow dust rings within an extended gaseous disc (Aly & Lodato 2020). This warped narrow dust ring could be the emitting region of the T=150 K
component detected in the mid-IR interferometric observations by Roccatagliata et al. (2011).
Misaligned binaries are common in young stellar systems (see e.g. Brinch et al. 2016; Takakuwa et al. 2017). GV
Tau S was also proposed to be a spectroscopic binary by
Doppmann et al. (2008). If confirmed, GV Tau would be
a quadruple star system such as GG Tau (Andrews et al.
2014) and HD98800B (Kennedy et al. 2019).


**6** **MOLECULAR** **CHEMISTRY**


In this Section we compile the column densities and rotation temperatures that have been derived using observations from NIR to mm wavelengths (see Table 1). Even when


MNRAS **000**, 1–10 (2020)

**Figure** **6.** Sketch of the geometry proposed for GV Tau N to
explain ALMA spectroscopic observations.


comparing lines of the same species, ro-vibrational and rotational lines are emitted from different regions of this complex
system and the comparison is not straightforward. Our goal
is to put together all the pieces of information to figure out
the overall scenario.

The physical and chemical conditions in the inner
R<1−10 au are better probed by NIR observations. Different
rotation temperatures and molecular column densities have
been measured with NIR molecular absorption observations
towards GV Tau N (see Table 1). In particular, Gibb et al.
(2007) derived T rot = 115±11 K and N(HCN)= (3.7 ± 0.3)
× 10 [16] cm [−][2] in the first detection of the HCN absorption
lines towards this star. Later, Doppmann et al. (2008) and
Bast et al. (2013) estimated a higher rotation temperature,
T rot >500 K for HCN (see Table 1). Doppmann et al. (2008)
argued that this difference is due to the different set of lines
used in the calculations. Gibb et al. (2007) calculations were
based on lines at lower energy and obtained a lower rotation
temperature, as expected in the case of a steep gas kinetic
temperature gradient along the line of sight. The velocity
centroid of the C 2 H 2 and HCN absorption lines is v lsr =
8.7 ±0.3 km s [−][1], similar to that of the absorption feature
that we have detected in the [13] CO 3→2 line on the top
of high velocity wings, thus consistent with the scenario of
these molecules coming from infalling gas towards the star.
Gibb et al. (2007, 2008) also derived [12] CO, [13] CO, and C [18] O
rotation temperatures based on molecular absorption (see
Table 1). They obtained T rot = 140 K − 260 K, suggesting
that the observed lines are probing molecular gas located
further from the star than HCN and C 2 H 2 although along
the line of sight.
We present the first detection of water towards GV Tau
(see Fig. 2). In particular, three water lines, p-H 2 O 1 11 →0 00,
o-H 2 O 1 10 →1 01 and p-H 2 O 2 02 →1 11 have been detected.
The emission of the ground ortho and para water lines are
thought to originate in the disc surfaces and in shocks along
the outflow cavity in Class I sources (Hogerheijde et al. 2011;
Kristensen et al. 2012; Karska et al. 2013; Podio et al. 2013;
Mottram et al. 2014; Salinas et al. 2016). The FIR water
lines show two well differentiated components: one with a
wide profile, very similar to that derived from the interferometric HCN 3→2 observations; the second one is characterized by a narrow profile and was interpreted as coming
from the outer envelope. In the following, we explore the


MNRAS **000**, 1–10 (2020)



7


possibility that the emission of the wide component comes
from the GV Tau N disrupted gaseous disc detected with
ALMA observations of the HCN 3→2 line. First, we would
assume that the bulk of the water emission is coming from
GV Tau N. This is a reasonable assumption taking into account that previous NIR and millimeter observations showed
that molecular absorption/emission is mainly coming from
the North component (Gibb et al. 2007, 2008; Doppmann
et al. 2008; Bast et al. 2013; Fuente et al. 2012). Secondly,
we use the two observed p-H 2 O line to investigate the physical conditions of the emitting region. Based on our Gaussian
fits to the wide component (Table1), and after correcting for
the small difference in the beam size, we derive an integrated
intensity ratio, R obs (H 2 O@987 GHz/1113 GHz)= 1.0±0.1 for
the two p-H 2 O lines observed. This ratio is not consistent
with optically thin emission. In the optically thin limit, and
assuming Local Thermodynamic Equilibrium (LTE), we estimate R LTE (H 2 O@987 GHz/1113 GHz)=0.5 at 200 K, and
increases with temperature until ∼0.63 for T k >500 K. The
observed ratio can only be explained if the emission of pH 2 O is optically thick. This would imply N(p-H 2 O)> a few
10 [17] cm [−][2] . This high value of the water column density is
within the range of water column densities derived towards
T Tauri stars using Spitzer observations (Salyk et al. 2007).
Thus, it is not unreasonable that the emission comes from
the compact disrupted gaseous disc. To further check the
consistency of our interpretation, we perform the following
calculation: assuming T rot ∼ 500 K as derived from HCN absorption observations, optically thick emission, and a source
size of 0.5” (see Fig. 1), we predict T mb ∼ 0.23 K for the pH 2 O lines after diluting to the Herschel beam, which is fully
consistent with Herschel observations.

It is also interesting to compare the intensities of
the ground p-H 2 O line with the o-H 2 O 1 10 →1 01 line at
557 GHz. In the optically thick case, we would expect
R thick (H 2 O@1113 GHz/557 GHz)∼4.7 because of the different observational beams. Instead, the observed value is
R obs (H 2 O@1113 GHz/557 GHz)∼2.4±0.1. This can be explained if the size of the emitting region is larger for orthoH 2 O than for the para-H 2 O. Indeed, this is expected according to the critical densities of these line (∼2×10 [7] cm [−][3] and
∼2×10 [8] cm [−][3] at 50 K for the 557 and 1113 GHz lines, respectively), and the higher abundance of o-H 2 O (the orthoto-para ratio is ∼3 at high temperatures). Direct imaging of
these lines at high angular resolution is required to confirm
this scenario.
We have also derived [13] CO, HCN and CN column
densities based on FIR observations. In these cases, the
lines show narrow profile and therefore, we assume a lower
rotation temperature T rot =250 K, similar to those measured from NIR absorption lines of [13] CO (Gibb et al. 2007,
2008). Again, the unknown source size introduces a large
uncertainty in our calculations. In order to make a fair
comparison between molecules, we assumed a source size

”
of 18.5 . With these assumptions we derive the following
source-averaged column densities: N( [13] CO)=5.0×10 [14] cm [−][2],
N(HCN)= 4.0×10 [11] cm [−][2], and N(HCN)= 6.0×10 [11] cm [−][2] .
Finally, we explore the chemistry of the compact emission around GV Tau N using the millimeter interferometric
images. Fuente et al. (2012) concluded that the HCN/HCO [+]

abundance ratio should be >300 to be compatible with the
non-detection of HCO [+] 3→2 with PdBI observations. Here,

8 _A._ _Fuente_ _et_ _al._


**Table** **1.** Summary of molecular observations


NIR molecular absorption
Species T rot (K) N(cm [−][2] ) Ref


12 CO 200±40 ∼1.2×10 [19] (1)
13 CO 260±20 ∼1.1×10 [17] (1)
C [18] O 140±50 (1.4 ± 0.5) × 10 [16] (1)
C 2 H 2 170±20 (7.3 ± 0.2) × 10 [16] (1)
720±60 (1.4 ± 0.3) × 10 [16] (3)
CH 4 750±50 (2.8±0.2)×10 [17] (4)
CO 2 250±25 (5.1 ± 0.7) × 10 [16] (3)
HCN 115±11 (3.7 ± 0.3) × 10 [16] (1)
440±40 (1.8 ± 0.4) × 10 [16] (3)
550 1.5 × 10 [17] (2)


FIR molecular emission
Species T rot (K) N(cm [−][2] ) Comments


o-H 2 O 500 >10 [17] Wide
p-H 2 O 500 >10 [17] Wide
13 CO 250 5.0×10 [14] Narrow [1]

HCN 250 4.0×10 [11] Narrow [1]

CN 250 6.0×10 [11] Narrow [1]


mm interferometric emission
Species T rot (K) N(cm [−][2] ) Comments


13 CO 250−500 (2.6−5.0)×10 [17] Wide
HCN 250−500 (2.0−3.5)×10 [15] Wide


References: (1) Gibb et al. 2007, 2008; (2) Doppmann et al. 2008;
(3) Bast et al. 2013; (4) Gibb & Horne 2013
1 Beam averaged column densities (beam=18.5”).


we will compare the HCN 3→2 observations obtained with
ALMA with the PdBI observations of the [13] CO →2 line.

For this comparison we use the averaged HCN 3→2 spectrum in R<0.18”, since the beam of [13] CO 3→2 observations
is ∼ 0.3”. We can fit the PdBI [13] CO 3→2 line profile, assuming LTE, T rot =250−500 K and N( [13] CO)=(2.6−5.0)×10 [17]

cm [−][2] . At these high temperatures, the emission of the [13] CO
3→2 is optically thin and it is not very dependent on the
assumed gas kinetic temperature. This estimate is in reasonable agreement with the value derived from the NIR absorption lines, suggesting that we are probing the same gas component. The R<0.18” averaged profile of the HCN 3→2 emission can be fitted with T rot =250−500 K and N(HCN)=(2.03.5)×10 [15] cm [−][2], i.e., two orders of magnitude lower than
the values derived from the NIR molecular absorptions. This
suggest that the mm emission is probing a different gas component than the molecular absorption in NIR. Molecular absorptions arise in a very small and hot region where the HCN
lines are optically thick, and T b (HCN 3→2) ∼ 500 K. In order to be compatible with ALMA observations, the size of
this region should be R∼ 2−3 au around the star, confirming
its origin in the GV Tau N individual disc.
The observation of 13 CO and HCN with different
techniques provides valuable information on the chemical
changes occurring in this complex system. As shown in Table 1, we obtain that the HCN/ [13] CO abundance ratio is
∼10 [−][3] based on the FIR observations, ∼10 [−][2] in the gaseous
disc traced with ALMA and PdBI observations, and ∼1 in
the close vicinity of the star where NIR molecular absorptions arise. These different values of the HCN/ [13] CO ratio testify for chemical gradients in this system, with the



HCN/ [13] CO ratio decreasing with the distance from the star.
This behavior of the HCN abundance, peaking at R∼2-3 au
from the star is consistent with chemical models predictions
(see e.g. Walsh et al. (2010); Ag´undez et al. (2018)). These
models also predict that a high abundance of H 2 O is expected in this inner region, coeval with HCN. The narrow
component appearing in the H 2 O line profiles is thought to
come from a more extended envelope component.


**7** **CONCLUDING** **REMARKS**


The high spatial resolution of ALMA observations allows
us, for the first time, to discern the different gas components in the vicinity of GV Tau N. The young star GV Tau
N is located in the inner gap of a gaseous Keplerian disc
of R∼20 au. An ionized jet is detected in the continuum at
1.1 mm. Furthermore, ALMA observations present evidence
of the existence of two molecular outflows, one of them associated with the continuum jet. We propose that all these
observations can be easily explained if GV Tau N is a binary, as already suggested by Doppmann et al. (2008). The
individual disc of the primary is highly misaligned relative to
the circumbinary disc, and its jet is disrupting the molecular
ring (see Fig. 6).
The present detection of the o-H 2 O and p-H 2 O line in
GV Tau N is of paramount importance. Determining the water abundance in proto-planetary discs has been remarkably
difficult. Water vapor detections using the ground state H 2 O
lines have been reported for just two discs, the well-known
transition disc TW Hya (Hogerheijde et al. 2011; Salinas
et al. 2016), and the Class I disc DG Tau (Podio et al. 2013).
Stringent upper limits to the water abundance have been reported for a dozen other sources at an order of magnitude
lower than expected (Bergin et al. 2010; Du et al. 2017).
Recently, Harsono et al. (2020) unsuccessfully searched for
water in five Class I discs using ALMA observations of millimeter lines of the rarer isotopologue H [18] 2 [O.] [The] [detection]
of cold water towards Class I protostar GV Tau stands as a
major result that deserves further study.
We also present observations of high excitation lines of
13 CO, HCN and CN as observed with the HIFI/Herschel instrument, which provide information on the column densities
of these species at spatial scales of ∼ a few 10”. As shown
in Table 1, the HCN/ [13] CO abundance ratio is ∼10 [−][3] in the
warm envelope, ∼10 [−][2] in the gaseous disc better traced with
ALMA and PdBI observations, and ∼1 in the close vicinity
of the star where NIR molecular absorptions arise. This behavior of the HCN abundance, peaking at R∼2-3 au from
the star is consistent with chemical models predictions (see
e.g. Walsh et al. (2010); Ag´undez et al. (2018)). These models also predict that a high abundance of H 2 O is expected
in this inner region, coeval with HCN.
Spitzer observations revealed that GV Tau N is specially
rich in organic species (Gibb et al. 2007, 2008; Doppmann
et al. 2008; Bast et al. 2013). The interaction of the jet with
the circumbinary gaseous disc is expected to produce intense
shocks that could contribute to enhance the abundance of

organic species in this disc. High spatial resolution interferometric observations are required to disentangle the interplay between chemistry and dynamics in this prototypical
system.


MNRAS **000**, 1–10 (2020)

**DATA** **AVAILABILITY**


The data underlying this article will be shared on reasonable
request to the corresponding author.


**ACKNOWLEDGEMENTS**


This paper makes use of the following ALMA data:
ADS/JAO. 2016.1.00813.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation
with the Republic of Chile. The Joint ALMA Observatory
is operated by ESO, AUI/NRAO and NAOJ. We thank
the Spanish MINECO for funding support from AYA201675066-C2-2-P. SPTM has received funding from the European Union’s Horizon 2020 research and innovation program
under grant agreement No 639459 (PROMISE).


**REFERENCES**


Ag´undez M., Roueff E., Le Petit F., Le Bourlot J., 2018, [A&A,](http://dx.doi.org/10.1051/0004-6361/201732518)

616, A19
Alonso-Albi T., Fuente A., Bachiller R., Neri R., Planesas P.,
Testi L., Bern´e O., Joblin C., 2009, [A&A,](http://dx.doi.org/10.1051/0004-6361/200810401) 497, 117
Alonso-Mart´ınez M., Riviere-Marichalar P., Meeus G., Kamp I.,
Fang M., Podio L., Dent W. R. F., Eiroa C., 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201629005) [603,](https://ui.adsabs.harvard.edu/abs/2017A&A...603A.138A)
[A138](https://ui.adsabs.harvard.edu/abs/2017A&A...603A.138A)

Aly H., Lodato G., 2020, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz3633) 492, 3306
Andrews S. M., Rosenfeld K. A., Kraus A. L., Wilner D. J., 2013,

[ApJ,](http://dx.doi.org/10.1088/0004-637X/771/2/129) 771, 129
Andrews S. M., et al., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/787/2/148) 787, 148
Banzatti A., Pontoppidan K. M., Salyk C., Herczeg G. J., van
Dishoeck E. F., Blake G. A., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/834/2/152) 834, 152
Bast J. E., Lahuis F., van Dishoeck E. F., Tielens A. G. G. M.,
2013, [A&A,](http://dx.doi.org/10.1051/0004-6361/201219908) 551, [A118](https://ui.adsabs.harvard.edu/abs/2013A&A...551A.118B)
Bergin E. A., et al., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/201015104) 521, L33
Brinch C., Jørgensen J. K., Hogerheijde M. R., Nelson R. P.,
Gressel O., 2016, [ApJ,](http://dx.doi.org/10.3847/2041-8205/830/1/L16) 830, L16
Carr J. S., Najita J. R., 2008, [Science,](http://dx.doi.org/10.1126/science.1153807) 319, 1504
Carr J. S., Najita J. R., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/733/2/102) 733, 102
Carr J. S., Najita J. R., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/788/1/66) [788,](https://ui.adsabs.harvard.edu/abs/2014ApJ...788...66C) 66
Ceccarelli C., et al., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/201015081) 521, L22
Dent W. R. F., et al., 2013, [PASP,](http://dx.doi.org/10.1086/670826) 125, 477
Desch S. J., 2007, [ApJ,](http://dx.doi.org/10.1086/522825) 671, 878
Devine D., Reipurth B., Bally J., Balonek T. J., 1999, [AJ,](http://dx.doi.org/10.1086/300886) [117,](https://ui.adsabs.harvard.edu/abs/1999AJ....117.2931D)

[2931](https://ui.adsabs.harvard.edu/abs/1999AJ....117.2931D)

Doppmann G. W., Najita J. R., Carr J. S., 2008, [ApJ,](http://dx.doi.org/10.1086/590328) 685, 298
Doppmann G. W., Najita J. R., Carr J. S., Graham J. R., 2011,

[ApJ,](http://dx.doi.org/10.1088/0004-637X/738/1/112) 738, 112
Du F., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa70ee) [842,](https://ui.adsabs.harvard.edu/abs/2017ApJ...842...98D) 98
Eisner J. A., Plambeck R. L., Carpenter J. M., Corder S. A., Qi
C., Wilner D., 2008, [ApJ,](http://dx.doi.org/10.1086/588524) 683, 304
Fedele D., Pascucci I., Brittain S., Kamp I., Woitke P., Williams
J. P., Dent W. R. F., Thi W. F., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/732/2/106) 732, 106
Fedele D., Bruderer S., van Dishoeck E. F., Herczeg G. J., Evans
N. J., Bouwman J., Henning T., Green J., 2012, [A&A,](http://dx.doi.org/10.1051/0004-6361/201219615) [544,](https://ui.adsabs.harvard.edu/abs/2012A&A...544L...9F)

[L9](https://ui.adsabs.harvard.edu/abs/2012A&A...544L...9F)

Fedele D., et al., 2013, [A&A,](http://dx.doi.org/10.1051/0004-6361/201321118) 559, A77
Fuente A., Cernicharo J., Ag´undez M., 2012, [ApJ,](http://dx.doi.org/10.1088/2041-8205/754/1/L6) [754,](https://ui.adsabs.harvard.edu/abs/2012ApJ...754L...6F) L6
Gaia Collaboration 2018, VizieR Online Data Catalog, p. [I/345](https://ui.adsabs.harvard.edu/abs/2018yCat.1345....0G)
Gibb E. L., Horne D., 2013, [ApJ,](http://dx.doi.org/10.1088/2041-8205/776/2/L28) 776, L28
Gibb E. L., Van Brunt K. A., Brittain S. D., Rettig T. W., 2007,

[ApJ,](http://dx.doi.org/10.1086/513502) 660, 1572


MNRAS **000**, 1–10 (2020)



9


Gibb E. L., Van Brunt K. A., Brittain S. D., Rettig T. W., 2008,

[ApJ,](http://dx.doi.org/10.1086/591644) 686, 748
Green J. D., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/770/2/123) 770, 123
Harsono D., et al., 2020, [A&A,](http://dx.doi.org/10.1051/0004-6361/201935994) 636, A26
Hogerheijde M. R., et al., 2011, [Science,](http://dx.doi.org/10.1126/science.1208931) 334, 338
Jørgensen J. K., van Dishoeck E. F., Visser R., Bourke T. L.,
Wilner D. J., Lommen D., Hogerheijde M. R., Myers P. C.,
2009, [A&A,](http://dx.doi.org/10.1051/0004-6361/200912325) 507, 861
Karska A., et al., 2013, [A&A,](http://dx.doi.org/10.1051/0004-6361/201220028) 552, [A141](https://ui.adsabs.harvard.edu/abs/2013A&A...552A.141K)
Kennedy G. M., et al., 2019, Nature [Astronomy,](http://dx.doi.org/10.1038/s41550-018-0667-x) 3, [230](https://ui.adsabs.harvard.edu/abs/2019NatAs...3..230K)
Kristensen L. E., et al., 2012, [A&A,](http://dx.doi.org/10.1051/0004-6361/201118146) [542,](https://ui.adsabs.harvard.edu/abs/2012A&A...542A...8K) A8
Kruger A. J., Richter M. J., Carr J. S., Najita J. R., Doppmann
G. W., Seifahrt A., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/729/2/145) 729, 145
Lahuis F., et al., 2006, [ApJ,](http://dx.doi.org/10.1086/500084) 636, [L145](https://ui.adsabs.harvard.edu/abs/2006ApJ...636L.145L)
Liu H. B., et al., 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201630263) 602, A19
Mandell A. M., Bast J., van Dishoeck E. F., Blake G. A., Salyk
C., Mumma M. J., Villanueva G., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/747/2/92) [747,](https://ui.adsabs.harvard.edu/abs/2012ApJ...747...92M) 92
Maret S., et al., 2020, [A&A,](http://dx.doi.org/10.1051/0004-6361/201936798) 635, A15
Mathews G. S., et al., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/201014595) 518, [L127](https://ui.adsabs.harvard.edu/abs/2010A&A...518L.127M)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K.,
2007, CASA Architecture and Applications. p. 127
Meeus G., et al., 2012, [A&A,](http://dx.doi.org/10.1051/0004-6361/201219225) 544, A78
Mottram J. C., et al., 2014, [A&A,](http://dx.doi.org/10.1051/0004-6361/201424267) 572, A21
Movsessian T. A., Magakian T. Y., 1999, A&A, 347, 266
Najita J. R., Carr J. S., Strom S. E., Watson D. M., Pascucci I.,
Hollenbach D., Gorti U., Keller L., 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/712/1/274) 712, 274
Najita J. R., Carr J. S., Pontoppidan K. M., Salyk C., van
Dishoeck E. F., Blake G. A., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/766/2/134) 766, 134
Ott S., 2010, The Herschel Data Processing System — HIPE and
Pipelines — Up and Running Since the Start of the Mission.
p. 139
Panagia N., 1988, in Pudritz R. E., Fich M., eds, NATO Advanced
Science Institutes (ASI) Series C Vol. 232, NATO Advanced
Science Institutes (ASI) Series C. p. 25, [doi:10.1007/978-94-](http://dx.doi.org/10.1007/978-94-009-2973-9_2)
[009-2973-9](http://dx.doi.org/10.1007/978-94-009-2973-9_2) ~~2~~

Pety J., 2005, in Casoli F., Contini T., Hameury J. M., Pagani L.,
eds, SF2A-2005: Semaine de l’Astrophysique Francaise. p. 721
Pilbratt G. L., et al., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/201014759) [518,](https://ui.adsabs.harvard.edu/abs/2010A&A...518L...1P) L1
Podio L., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/2041-8205/766/1/L5) [766,](https://ui.adsabs.harvard.edu/abs/2013ApJ...766L...5P) L5
Pontoppidan K. M., Salyk C., Blake G. A., Meijerink R., Carr
J. S., Najita J., 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/720/1/887) 720, 887
Reipurth B., Rodr´ıguez L. F., Anglada G., Bally J., 2004, [AJ,](http://dx.doi.org/10.1086/381062)

127, 1736
Riviere-Marichalar P., et al., 2012, [A&A,](http://dx.doi.org/10.1051/0004-6361/201118448) [538,](https://ui.adsabs.harvard.edu/abs/2012A&A...538L...3R) L3
Roccatagliata V., Ratzka T., Henning T., Wolf S., Leinert C.,
Bouwman J., 2011, [A&A,](http://dx.doi.org/10.1051/0004-6361/201116805) 534, A33
Salinas V. N., et al., 2016, [A&A,](http://dx.doi.org/10.1051/0004-6361/201628172) 591, [A122](https://ui.adsabs.harvard.edu/abs/2016A&A...591A.122S)
[Salyk C., Blake G. A., Boogert A. C. A., Brown J. M., 2007, ApJ,](http://dx.doi.org/10.1086/512012)

655, [L105](https://ui.adsabs.harvard.edu/abs/2007ApJ...655L.105S)
Salyk C., Pontoppidan K. M., Blake G. A., Lahuis F., van
Dishoeck E. F., Evans Neal J. I., 2008, [ApJ,](http://dx.doi.org/10.1086/586894) 676, L49
Salyk C., Pontoppidan K. M., Blake G. A., Najita J. R., Carr
J. S., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/731/2/130) 731, 130
Salyk C., Lacy J., Richter M., Zhang K., Pontoppidan K., Carr
J. S., Najita J. R., Blake G. A., 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab05c3) [874,](https://ui.adsabs.harvard.edu/abs/2019ApJ...874...24S) 24
Santiago-Garc´ıa J., Tafalla M., Johnstone D., Bachiller R., 2009,

[A&A,](http://dx.doi.org/10.1051/0004-6361:200810739) 495, 169
Sargent B. A., et al., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/792/2/83) [792,](https://ui.adsabs.harvard.edu/abs/2014ApJ...792...83S) 83
Sheehan P. D., Eisner J. A., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/791/1/19) [791,](https://ui.adsabs.harvard.edu/abs/2014ApJ...791...19S) 19
Skinner S. L., Brown A., Stewart R. T., 1993, [ApJS,](http://dx.doi.org/10.1086/191803) 87, 217
Takakuwa S., Saigo K., Matsumoto T., Saito M., Lim J., Hanawa
T., Yen H.-W., Ho P. T. P., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa6116) [837,](https://ui.adsabs.harvard.edu/abs/2017ApJ...837...86T) 86
Thi W. F., et al., 2011, [A&A,](http://dx.doi.org/10.1051/0004-6361/201116678) [530,](https://ui.adsabs.harvard.edu/abs/2011A&A...530L...2T) L2
Tobin J. J., et al., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab6f64) 890, 130
Ubach C., Maddison S. T., Wright C. M., Wilner D. J., Lommen
D. J. P., Koribalski B., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx012) 466, 4083
Walsh C., Millar T. J., Nomura H., 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/722/2/1607) 722, 1607
Weidenschilling S. J., 1977, [Ap&SS,](http://dx.doi.org/10.1007/BF00642464) 51, 153

10 _A._ _Fuente_ _et_ _al._


de Graauw T., et al., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/201014698) [518,](https://ui.adsabs.harvard.edu/abs/2010A&A...518L...6D) L6
van Dishoeck E. F., et al., 2011, [PASP,](http://dx.doi.org/10.1086/658676) 123, 138


**APPENDIX** **A:** **SUPPORTING** **MATERIAL**



This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.


MNRAS **000**, 1–10 (2020)

11

#### Δ⍺ (‘’)


**Figure** **A1.** Channel maps of the HCN 3→2 line as observed with ALMA. Solid lines indicate the directions of Jet 1, Jet 2, D1 and D2.


MNRAS **000**, 1–10 (2020)

12 _A._ _Fuente_ _et_ _al._


**Table** **A1.** Gaussian fits to FIR observations


line Freq beam Area V lsr FWHP T mb
(GHz) (”) (K km s [−][1] ) (km s [−][1] ) (km s [−][1] ) (K)


o-H 2 O 1 10 →1 01 556.94 40 0.93 ( 0.02) 7.52 ( 0.09) 7.92 ( 0.23) 0.11
p-H 2 O 1 11 →0 00 1113.34 18.5 2.14 ( 0.05) 7.58 ( 0.08) 7.42 (0.20) 0.27
p-H 2 O 2 02 →1 11 987.93 20 1.79 ( 0.06) 7.32 ( 0.09) 6.64 (0.29) 0.25
13 CO 10→9 1101.35 18.5 1.18 ( 0.03) 6.72 ( 0.03) 2.97 ( 0.08) 0.37
CN 5→4 566.95 40 0.04 ( 0.01) 7.25 ( 0.13) 1.65 ( 0.25) 0.02
HCN 7→6 620.30 35 0.14 ( 0.03) 7.02 ( 0.37) 3.71 ( 1.14) 0.04

#### Δ⍺ (‘’)


**Figure** **A2.** The same as Fig. A1.


MNRAS **000**, 1–10 (2020)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Fit Gaussian components to Herschel/HIFI spectra of H2O, 13CO 10→9, HCN 7→6, and CN 5→4, decomposing water lines into a wide (FWHP ~ 8 km s^-1) and a narrow (FWHP ~ 2.7 km s^-1) component.",
  "failed_quote": "The basic data reduction was performed using the standard pipeline provided with the version 7.0 of HIPE (Ott 2010) and then exported to GILDAS/CLASS (Pety 2005) for a more detailed analysis."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Standard pipeline basic data reduction of Herschel/HIFI observations",
  "failed_quote": "The basic data reduction was performed using the standard pipeline provided with the version 7.0 of HIPE (Ott 2010)"
 }
]
```
