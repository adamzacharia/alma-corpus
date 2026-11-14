# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...626A..93V\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. PILS_bridgekinematics_for-arxiv ⃝c ESO 2019
April 1, 2019

### −
#### **The ALMA-PILS survey: Gas dynamics in IRAS 16293 2422 and the** **connection between its two protostars**


M. H. D. van der Wiel [1][,][ 2], S. K. Jacobsen [2], J. K. Jørgensen [2], T. L. Bourke [3], L. E. Kristensen [2], P. Bjerkeli [4][,][ 2],
N. M. Murillo [5], H. Calcutt [2], H. S. P. Müller [6], A. Coutens [7], M. N. Drozdovskaya [8], C. Favre [9], and S. F. Wampfler [8]


1 ASTRON, Netherlands Institute for Radio Astronomy, Oude Hoogeveensedijk 4, 7991 PD Dwingeloo, The Netherlands
email: `mhd@vanderwiel.org`
2 Centre for Star and Planet Formation, Niels Bohr Institute & Natural History Museum of Denmark, University of Copenhagen,
Øster Voldgade 5–7, 1350 Copenhagen K, Denmark
3 SKA Organisation, Jodrell Bank Observatory, Lower Withington, Macclesfield, Cheshire SK11 9DL, UK
4 Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, 43992 Onsala,
Sweden
5 Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA, Leiden, The Netherlands
6 I. Physikalisches Institut, Universität zu Köln, Zülpicher Str. 77, 50937 Köln, Germany
7 Laboratoire d’Astrophysique de Bordeaux, Univ. Bordeaux, CNRS, B18N, allée Geoffroy Saint-Hilaire, 33615 Pessac, France
8 Center for Space and Habitability, Universität Bern, Sidlerstrasse 5, 3012 Bern, Switzerland
9 INAF-Osservatorio Astrofisico di Arcetri, Largo E. Fermi 5, I-50125, Florence, Italy


April 1, 2019


**ABSTRACT**


_Context._ The majority of stars form in binary or higher order systems. The evolution of each protostar in a multiple system may start
at different times and may progress differently. The Class 0 protostellar system IRAS 16293−2422 contains two protostars, “A” and
“B”, separated by ∼600 au and embedded in a single, 10 [4] au scale envelope. Their relative evolutionary stages have been debated.
_Aims._ We aim to study the relation and interplay between the two protostars A and B at spatial scales of 60 au up to ∼10 [3] au.
_Methods._ We selected molecular gas line transitions of the species CO, H 2 CO, HCN, CS, SiO, and C 2 H from the ALMA-PILS
spectral imaging survey (329–363 GHz) and used them as tracers of kinematics, density, and temperature in the IRAS 16293−2422
system. The angular resolution of the PILS data set allows us to study these quantities at a resolution of 0.5 [′′] (60 au at the distance of
the source).
_Results._ Line-of-sight velocity maps of both optically thick and optically thin molecular lines reveal: (i) new manifestations of
previously known outflows emanating from protostar A; (ii) a kinematically quiescent bridge of dust and gas spanning between
the two protostars, with an inferred density between 4×10 [4] cm [−][3] and ∼3×10 [7] cm [−][3] ; and (iii) a separate, straight filament seemingly
connected to protostar B seen only in C 2 H, with a flat kinematic signature. Signs of various outflows, all emanating from source A,
are evidence of high-density and warmer gas; none of them coincide spatially and kinematically with the bridge.
_Conclusions._ We hypothesize that the bridge arc is a remnant of filamentary substructure in the protostellar envelope material from
which protostellar sources A and B have formed. One particular morphological structure appears to be due to outflowing gas impacting
the quiescent bridge material. The continuing lack of clear outflow signatures unambiguously associated to protostar B and the
vertically extended shape derived for its disk-like structure lead us to conclude that source B may be in an earlier evolutionary stage
than source A.


**Key words.** ISM: individual objects: IRAS 16293 – stars: formation – circumstellar matter – ISM: jets and outflows



**1.** **Introduction**


The majority of currently forming stars are part of multiple systems (Chen et al. 2013; Duchêne & Kraus 2013; Tobin et al.
2016b). Two main scenarios have been proposed to form stellar
systems of binary and higher order: disk fragmentation (Adams
et al. 1989; Bonnell & Bate 1994), leading to close binaries (up
to a few hundred au separation), and turbulent fragmentation of
a natal protostellar envelope (Offner et al. 2010; Pineda et al.
2015), leading to wide separation binaries (≳1000 au). The difference in initial separation is often obfuscated at later stages by
the effects of tidal interactions after the initial formation of protostars. Another observable difference that can help to distinguish
between formation scenarios is that binaries formed through disk
instability may be more prone to exhibit aligned rotation axes,



whereas rotation axes of those formed from turbulent fragmentation should be randomly distributed. The rotation axis of a protostar can be inferred through studying the morphology and kinematics of its disk-outflow system (Lee et al. 2016). High angular
resolution observations of embedded protostellar systems suggest that both mechanisms of multiple star formation occur in
nature (e.g., Tobin et al. 2016a; Brinch et al. 2016; Lee et al.
2017). In both cases, remnant material of the natal body may
manifest as a bridge between recently formed binary companions. The object of study in this paper is one of the most wellstudied protostellar binary systems, IRAS 16293−2422 (hereafter IRAS 16293), which has such a bridge and exhibits kinematic signatures of active outflow and infall (see below).


IRAS 16293 is a nearby, young, Class 0 protostellar system
in the Ophiuchus cloud complex (see Sect. 2 of Jørgensen et al.


Article number, page 1 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



2016 for a review of the source). The distance to three other
young stellar objects in the same cloud complex has been determined at 147±3 pc (Ortiz-León et al. 2017), and trigonometric
parallax measurements of water maser spots in IRAS 16293 itself put it at a distance of 141 − [+][30] 21 [pc (Dzib et al. 2018). However,]
to be consistent with earlier work and with detailed numerical
modeling of the IRAS 16293 system conducted by our team, we
adopt a distance estimate of 120 pc based on extinction measurements and VLBI parallax measurements of two stars in the core
of the complex (Loinard et al. 2008). This value is within the 1σ
uncertainty margin of Dzib et al. (2018). In general, an 18% increase in the source distance estimate (with an uncertainty margin of 15–20% of its own) inflates projected linear scales by a
factor 1.18, while quantities such as mass and luminosity, determined from broadband flux and column density, would scale by
the distance squared, that is, a factor 1.39. With _d_ =120 pc, the
angular distance of 5.3 [′′] between the two submillimeter sources
A and B corresponds to a projected distance of 636 au. The exact three-dimensional geometry of the two sources, their potential disks and the filament structure is unknown. Based on a total of 515 spectral lines from 54 molecular species detected in
a Submillimeter Array (SMA) spectral survey, Jørgensen et al.
(2011) derived LSR velocities of sources A and B of +3.2 and
+2.7 km s [−][1], respectively (throughout this work, IRAS 16293A
will be abbreviated as “source A” and IRAS 16293B as “source
B”). Different centroid velocities have been reported based on individual molecular lines: for source A, +3.8 km s [−][1] from C [17] O,
C [34] S (Favre et al. 2014), +3.6 km s [−][1] from HCN (Takakuwa
et al. 2007); for source B, +3.4 km s [−][1] from CH 3 OCHO, H 2 CCO
(Pineda et al. 2012). Differences in the derived centroid velocity
may stem from different angular resolution of the data sets, the
different molecular tracers used, and/or varying optical depth of
individual transitions of the same species, so that each traces a
somewhat different ensemble of gas. All of the centroid velocities listed above fall well within the ∼3–4 km s [−][1] wide distributions of _V_ lsr values fitted by Jørgensen et al. (2011).
Caux et al. (2011) used single-dish observations to estimate the masses of the two protostellar sources. Assuming that
the line broadening of the profiles is due to infalling motions,
these authors arrive at ∼0.8 _M_ ⊙ for source A and 0.1 _M_ ⊙ for
source B. The same mass of source A was found by Bottinelli
et al. (2004), also assuming infalling motion to explain the observed line broadening, but using interferometric observations
in which source A is spatially separated from source B. Alternatively, the line broadening could be caused by rotating motion instead of infall, as assumed for source A by Pineda et al.
(2012), who used observations of methyl formate (CH 3 OCHO)
and ketene (H 2 CCO) with a 2.2 [′′] ×1.0 [′′] beam to infer Keplerian
rotation around a central object of 0.53 _M_ ⊙ . Oya et al. (2016)
found a mass varying between 0.5 and 1.0 _M_ ⊙, depending on the
assumed inclination and centrifugal barrier radius. These studies
show that the source masses are in the regime of low-mass protostars, but the various methods yield masses differing by up to
a factor of two.

The binary protostellar system IRAS 16293 is embedded
in an envelope with a radius of (6–8)×10 [3] au (e.g., Schöier
et al. 2002; Crimier et al. 2010). Rotating, infalling motions
of this envelope have been inferred from spectral line profiles
(e.g., Menten et al. 1987; Zhou 1995; Ceccarelli et al. 2000;
Schöier et al. 2002; Takakuwa et al. 2007). In a detailed velocity model posited by Oya et al. (2016), the large-scale envelope
could transition into a Keplerian disk within the centrifugal barrier around source A, as indicated by observations presented in
Favre et al. (2014). The latter study found rotation on 50–400 au


Article number, page 2 of 27



scales, which could not be explained by simple Keplerian rotation around a point-mass, but needed to take into account the
extra material of the enclosed mass at these scales.

At least two major outflows have been observed from
IRAS 16293A: an east-west bipolar outflow (Yeh et al. 2008) and
a northwest-southeast outflow pair (Kristensen et al. 2013; Girart
et al. 2014). On larger scales of >5000 au, a northeast outflow
has also been observed (Mizuno et al. 1990; Stark et al. 2004),
the origin of which is speculated to be IRAS 16293A, based
on high-resolution CO images revealing a collimated structure
near source A (see Fig. 1). Combining single-dish observations
of a broad range of HCO [+] spectral lines ( _J_ =1–0 up to _J_ =13–
12), Quénard et al. (2018) conclude that the spatially unresolved
spectral line profiles are dominated by outflow contributions,
explained by these authors using a model of the northwestsoutheast outflow emanating from source A. In contrast, any
signs of outflows associated with IRAS 16293B have long escaped detection. Loinard et al. (2013) argued that the blueshifted
emission found southeast of source B is from a young monopolar outflow from source B, but Kristensen et al. (2013) demonstrated, using the same data, that it could be a bow-shock from
the northwest-southeast outflow from IRAS 16293A. Oya et al.
(2018) presented SiO velocity maps indicative of a pole-on pair
of outflows from source B, but these authors also recognize that
interaction with the outflow from source A is not ruled out as a
possible scenario.
The quadruple outflow structure from source A has led
to speculations that source A itself is a multiple system. Indeed, continuum observations at centimeter waves resolved
IRAS 16293A into two (Wootten 1989; Chandler et al. 2005) or
even three components (Loinard et al. 2007; Pech et al. 2010),
with a separation of up to ∼0.5 [′′] . The 0.5 [′′] resolution maps
from the ALMA PILS program appear to indicate a singularly
peaked source at the position of source A, both in continuum
(Jørgensen et al. 2016) and in optically thin C [17] O (Jacobsen
et al. 2018). However, the integrated C [17] O 3–2 intensity is affected by contamination from more complex molecules in the
dense, warm regions close to the two protostellar sources, which
modifies the apparent morphology of emission integrated over
channels bracketing the C [17] O line frequency (see Fig. A.1 in
Appendix A). Moreover, the 0.87 mm dust continuum is optically thick in the disk domains, which could hide any intrinsically multipeaked structure (Calcutt et al. 2018). In contrast, the
PILS maps of various isotopologues of methyl cyanide in Calcutt
et al. (2018), for which the emission is integrated over a moving velocity interval to avoid incorporating contributions from
other species, do show two clearly separated emission peaks.
The methyl cyanide peak positions are consistent with those of
radio continuum (3.6 cm) positions A1 and A2 from Loinard
et al. (2007) after correction for proper motion (Pech et al. 2010).
The slight offset of ∼0.2 [′′] is likely due to pointing errors and uncertainties in the proper motion correction coefficients (Calcutt
et al. 2018).
Material spanning the interbinary region between
IRAS 16293A and B was first identified in millimeter observations from the BIMA array [1] by Looney et al. (2000), who
interpreted it as a circumbinary envelope. The same bridge
material is also clearly detected in sensitive Atacama Large
Millimeter/Submillimeter Array (ALMA) observations (Pineda


1 BIMA stands for Berkeley-Illinois-Maryland Association, which operated and funded the nine-telescope array at Hat Creek in California
until 2004, when its hardware was relocated and merged into the Combined Array for Research in Millimeter-wave Astronomy (CARMA).

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



et al. 2012; Jørgensen et al. 2016). Observations of polarized
dust emission indicate that the magnetic field in the filamentary
bridge is oriented along the long axis of the bridge (Rao
et al. 2009, 2014; Sadavoy et al. 2018). Jacobsen et al. (2018)
(hereafter J2018) show that a dust filament model can match the
observed spatial emission from high-resolution submillimeter
continuum emission and C [17] O 3–2 gas line emission. Similar
structures observed in other multiple protostellar systems are
interpreted as fragmentation of large-scale circum-multiple
envelopes (Lee et al. 2017) or (Keplerian) rotating disks that
have become locally gravitationally unstable (Tobin et al. 2016a;
Fernández-López et al. 2017; Dutrey et al. 2014, 2016).


The exact evolutionary stage of the two protostars is unknown, partly because of the different inclination angles of
sources A (edge on; Pineda et al. 2012; Oya et al. 2016) and
B (face on; Oya et al. 2018). Given the outflow and infall signatures near source A, its status as a protostar is firmly established. In contrast, the apparent quiescence of source B has led
to speculations that it is not a young protostar, but rather harbors
a late-stage T Tauri disk (Stark et al. 2004). This interpretation
was later called into question when spectral line signatures of infalling material were observed toward source B (Chandler et al.
2005; Pineda et al. 2012; Jørgensen et al. 2012). In conclusion,
it is as yet unknown if the two protostars are at the same evolutionary stage, or that one may be more evolved than the other.


The outflows from source A, along with the striking arc of
dust and gas connecting sources A and B, make IRAS 16293 a
very complex system, where the observed gas line emission can
only be explained by a combination of multiple physical components. We aim to disentangle these structures in our new observations and to map the physical origins of the observed molecular
emission lines.


This paper is based on observations from the ALMA band 7
segment of the Protostellar Interferometric Line Survey (PILS [2] )
targeting IRAS 16293. The many thousands of line detections
in the PILS data set facilitate the discovery of complex organic
molecules (>6 atoms, including carbon; Herbst & Van Dishoeck
2009) and the study of their interstellar chemistry. Relatively
weak lines of complex molecules are most easily separable in
spectra extracted toward spatial positions near the kinematically
simple and spatially compact source B, with narrow (∼1 km s [−][1] ),
single-moded spectral line shapes. Most analysis based on the
PILS data cubes has therefore been restricted to spatial positions
close to the two protostars (e.g., Jørgensen et al. 2016; Coutens
et al. 2016; Lykke et al. 2017; Ligterink et al. 2017; Fayolle
et al. 2017; Coutens et al. 2018). In contrast, in this work, we
fully exploit the spatial dimensions of the PILS data set, but
focus on a few restricted frequency ranges containing lines of
well-known, simple molecular species. The aim is to study the
kinematic structure of the binary system and the intervening and
surrounding gaseous material.


We summarize the characteristics of the observational data in
Sect. 2, and describe the selection of molecular tracers and the
morphology and dynamics observed in each of them in Sect. 3.
Section 4 presents analysis of the physical characteristics of the
bridge filament between the two protostars and the kinematics
of outflow motions. Discussion of the results is given in Sect. 5,
and Sect. 6 summarizes the main conclusions.


2 `[http://youngstars.nbi.dk/PILS](http://youngstars.nbi.dk/PILS)`



**Table** **1.** Coordinates of submillimeter continuum peaks in
IRAS 16293−2422.


Component Right Ascension Declination
(J2000) (J2000)
source A 16 [h] 32 [m] 22 [s] .873 −24 [◦] 28 [′] 36 [′′] . 54
source B 16 [h] 32 [m] 22 [s] .6147 −24 [◦] 28 [′] 32 [′′] . 566


**Notes.** The uncertainties on fitted positions are 0.03 [′′] for both coordinates of component A, and 0.005 [′′] for component B.


**2.** **Observations**


The PILS program was conducted with ALMA between June
2014 and May 2015, using both the main array of 12-m dishes
and the shorter baselines available in the array of 7-m dishes
in the Atacama Compact Array (ACA). Its end product comprises a three-dimensional data set covering the uninterrupted
spectral range 329–363 GHz (all in ALMA band 7) in spectral
channels of 0.244 MHz in width. The sky area of ∼15 [′′] in diameter is covered in a single pointing with the primary beam
of the 12-m dishes, sampling the two binary components of
IRAS 16293 and their surroundings with a synthesized beam
FWHM of 0.5 [′′] . Self-calibration of the visibility phases was applied, based on the continuum signal. While the main array provides the unprecedented sensitivity, which is roughly uniform at
∼8 mJy beam [−][1] channel [−][1] across the full spectral range, the addition of ACA baselines ensures that large scale emission up to
∼13 [′′] is recovered. We refer to Jørgensen et al. (2016) for additional details of observing conditions, data characteristics, and
the data processing strategy.


**3.** **Results: observed dynamics and morphology**


The morphology of the dust continuum emission in IRAS 16293
as observed with ALMA at 0.5 [′′] resolution at 0.87 mm (Jørgensen et al. 2016; J2018) can be broken up into three distinct
components: a nearly circular structure that hints at a face-on
disk surrounding source B; an elliptically shaped structure related to the inclined disk-like structure around source A; and a
ridge of material stretching from B to A and even beyond, to
the southeast of A. The centroid coordinates of the continuum
peaks of components A and B, measured using two-dimensional
Gaussian fits on the PILS 0.826–0.912 mm continuum image,
are listed in Table 1. These positions of the 0.87 mm continuum
measured from our PILS data products are consistent with the
1.15–1.30 mm continuum peak locations reported by Oya et al.
(2018) to within 0.05 [′′], that is, one tenth of the synthesized beam
size of either observation.
We select spectral signatures of C [17] O, H [13] CN, H 2 CO,
H 2 [13] CO, C [34] S, SiO, [29] SiO, and C 2 H. The motivation for selecting these tracer transitions is that their emission is spatially extended across the inter- and circumbinary region, the molecules
are chemically simple, and are chosen because they probe a
range of densities, temperatures (see _E_ up and _n_ crit in Table 2)
and physical processes such as shocks. C [18] O 3–2 largely follows
the spatial distribution of C [17] O (J2018), and the former is not
further discussed in this paper. Although we recognize the additional value of studying other tracer molecules also covered
in the 329–363 GHz PILS data, the selection in this paper is
deliberately restricted to its current scope. The rest frequencies
for the relevant transitions of these species are listed in Table 2.
For the systemic velocities of each of the protostars, we adopt
the statistically averaged values based on the multiline analy

Article number, page 3 of 27

1”=120au













SE counterpart of NW

outflow

[PILS: SiO, H [13] CN]








|Col1|N<br>P . A . E a s to f N o r t h<br>E|
|---|---|
|<br>red side o<br>PA~270º<br>[PILS: high<br>redsh<br>   W outﬂow,<br> eh+ 2008]<br> 1990; Stark+ 2004]<br>quiescent bridge<br>[Pineda+ 2012, Oya+ 2018]<br>[PILS: dust, C18O, C17O]<br>e outﬂow<br> 004]<br>arcmin<br>[<br> rt of NW<br>w<br>  H13CN]<br>**A**<br>kinematically ﬂat<br>PA ~ 345º[PILS:<br>blueshifted<br>optically<br>thick CO<br>[Y08;PILS]<br>blue-shift<br>interface<br>bridge[PI<br>high-dens<br>borderin<br>[PILS:<br>H2O maser<br>[Dzib+ 2018]<br>[Oya+ 2018;PILS]<br>**B**<br>rotating structure, PA=56º||









**Fig. 1.** Illustration of physical components surrounding and bridging protostars A and B in the IRAS 16293 system, and outflows emanating from
IRAS 16293A. Thick, solid arrows at the edges of the panel point to scales beyond the ∼20 [′′] depicted in this illustration. Position angle (P.A.) is
defined from north to east, as indicated in the top right. Each component is labeled by a rectangular box, with literature sources listed in square
brackets. In all references given in square brackets in the illustration, ‘et al.’ is abbreviated as ‘+’: Dzib et al. (2018), Girart et al. (2014), Kristensen
et al. (2013), Loinard et al. (2007, 2013), Mizuno et al. (1990), Oya et al. (2016, 2018), Stark et al. (2004), Yeh et al. (2008) [further abbreviated
as ‘Y08’ where needed]; ‘PILS’ refers to structures observed in ALMA PILS observations (Jørgensen et al. 2016, J2018, and this work).



sis by Jørgensen et al. (2011). Velocity channel maps of each
of these species are shown in Figs. B.1–B.8, with a velocity
range in _V_ lsr between 0.0 and +6.5 km s [−][1], bracketing the systemic velocities of +3.2 and +2.7 km s [−][1] for sources A and B in
the IRAS 16293 binary (Jørgensen et al. 2011). As our aim is to
study material nearby, but not in the dense protostellar sources,
two masks are placed on the disks of each source in all maps presented in this work. This procedure ensures that high-intensity,
partially (self-)absorbed spectral line signals do not skew the intensity scaling on the integrated intensity maps and the calculation of the weighted velocity (moment 1) maps. Contamination
of the selected molecular line transitions by nearby transition of
other species are discussed in detail in Appendix A. Spectral line
shapes deviate from Gaussian profiles in some cases, particularly
in directions where line optical depth is high, and/or outflowing
or infalling gas motions contribute to the gas emission.


We construct velocity maps of the selected species by considering only channels with _V_ lsr in the range [−4,+11] km s [−][1]
(except for C 2 H, where we choose [−1,+7] km s [−][1] to limit
contamination by other species), and calculating an intensity

Article number, page 4 of 27



weighted mean velocity for each pixel, excluding all flux density values below 40 mJy beam [−][1] (i.e., roughly 4–6 σ depending
on the noise level in the particular section of frequency coverage). The result is shown in Fig. 2. The velocity structure of each
tracer is also displayed in the form of contour maps for three integrated ranges of velocity (red, systemic, blue) in Fig. 3, and
split out for each 0.2 km s [−][1] spectral channel in Appendix B.


As seen in Fig. 2, the C [17] O gas has an intensity-weighted
mean velocity restricted to ± 1 km s [−][1] of the systemic velocity in the bridge region between source A and B. The bridge is
therefore kinematically quiescent, that is, we find no evidence
that the bridge is part of an outflow motion nor that it is a rotating structure. The spatial distribution of C [17] O coincides with
the dust bridge traced by submillimeter continuum, while none
of the other (higher density) tracers in this study have intensity
peaks that are cospatial with the bridge, at 0.5 [′′] resolution (60 au
in projection, at the distance of the source). The bridge morphology is also recovered in the PILS C [18] O 3–2 map (J2018), while
the [13] CO 3–2 starts looking markedly different due to high line
optical depth (J2018). The C [34] S 7–6 distribution, discussed in

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars







































_−_ 1


_−_ 1




|Col1|Col2|Col3|
|---|---|---|
|B<br><br>H2CO 51,|A<br>B<br>5-41,4<br>300 au|A<br>B<br>H213CO 51,5–41,4|
|B<br><br>29SiO 8–7|A<br>B<br>|A<br>B<br>C34S 7–6|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. 2.** Velocity maps of molecular species listed in Table 2 (except [12] C [16] O, see Fig. 4). Black contours represent 0.87 mm dust continuum at levels
of 30, 45, 100, 250 mJy beam [−][1] . Gray contours for integrated spectral line intensity start at 0.35 Jy beam [−][1] km s [−][1], and velocity values are only
shown where the integrated intensity is above this threshold. The threshold for C 2 H is 0.07 Jy beam [−][1] km s [−][1], to reflect its narrower integration
range ([−1, +7] instead of [−4,+11] km s [−][1] ); it is 0.20 Jy beam [−][1] km s [−][1] for [29] SiO. Higher level integrated line intensity contours (also in gray)
cover 14 linear steps up to the maximum intensity in each map (in units of Jy beam [−][1] km s [−][1] ): 5.62 for C [17] O, 21.67 for H 2 CO, 8.10 for H 2 [13] CO,
32.55 for H [13] CN, 13.23 for SiO, 2.91 for [29] SiO, 6.54 for C [34] S, and 6.02 for C 2 H. For comparison with the contour levels: typical rms noise levels
in emission-free regions of the integrated intensity maps are 0.03–0.06 Jy beam [−][1] km s [−][1] . Velocities between +7 and +11 km s [−][1] are represented
by the darkest red color, and velocities between −4 and −1 km s [−][1] by the darkest blue color. The circular synthesized beam of 0.5 [′′] in FWHM is
indicated in the bottom right of all panels, except the H 2 CO panel, which features a scale bar representative of 300 au at the source distance of
120 pc. The blue ‘×’ sign in the top left panel marks the position 0.5 [′′] southwest of the continuum peak of source B, often used to extract signals of
complex organic molecules (e.g., Coutens et al. 2016; Lykke et al. 2017; Ligterink et al. 2017). The magenta ‘+’ sign marks the position at which
the representative bridge filament spectral profiles are extracted (see Appendix A).



more detailed in Sect. 4.3, may seem to overlap partly with the
dust and C [17] O, but we do not regard it as tracing the bridge.
A tentatively axisymmetric structure is seen in the channel
maps of H 2 CO and H [13] CN (Figs. 2, 3, B.2, B.3): two arcs emanating from source A, one on the NE side at velocities between
+2 and +3.5 km s [−][1], and its counterpart on the SW side at velocities between +4 and +5.5 km s [−][1] (e.g., Fig. B.2). These arcs
bracket the axis defined by the NW outflow seen in CO 6–5 by
Kristensen et al. (2013), and are kinematically symmetric around
_V_ lsr = +3 km s [−][1] . Examining the molecular tracers considered
in this work: this velocity gradient (roughly perpendicular to the
main axis of the bridge) is spatially more compact in H [13] CN than
in H 2 CO; there may be evidence of it in C [34] S; but it is absent in
C [17] O, SiO, and C 2 H (Fig. 2, Fig. 3). We therefore conclude that
the striking symmetry observed in H 2 CO is not the result of a
bulk rotation of the gas about the axis of the bridge or the axis of
the northwest outflow from source A.
While none of the tracer molecules listed above have signals bright enough to study faint line wings at velocity offsets
more than 4 km s [−][1], the main isotopologue of CO provides sufficiently bright signal to probe higher line-of-sight velocities. In
fact, in Fig. 4 we use only high-velocity (>5 km s [−][1] ) channels of
CO 3–2 emission, thereby avoiding complications in interpreting extremely optically thick emission at lower velocities. The
western lobe of the east-west outflow pair is prominently visible
in CO 3–2 in a cone-shaped distribution, with a much smaller re


gion of blueshifted counterpart appearing on the eastern side of
source A. At somewhat coarser angular resolution (1.5 [′′] beam,
using the SMA), Yeh et al. (2008) have previously studied the
east-west outflow from source A in CO 2–1 and 3–2. Compared
with their work, our 0.5 [′′] resolution map in CO 3–2 reveals a
more cone-like shape of the westward, redshifted outflow lobe,
and there is an apparent acceleration taking place with increased
distance from source A. See Sect. 4.3 for a discussion of the
structures described here. There is also bright CO 3–2 emission
with an emission peak 1 [′′] south of source B, with velocities ranging up to 10 km s [−][1] blueshifted with respect to source B. Its location is consistent with the position ‘b2’ described in Yeh et al.
(2008). In our map (Fig. 4), this blueshifted knot is clearly morphologically connected to source B.

We observe that the SiO velocity map in Fig. 2 traces both
sides of the NW-SE outflow pair extending up to ∼8 [′′] from
source A, blueshifted on the northwest side and redshifted on the
southeast side. The lower optical depth line of [29] SiO only shows
emission on the redshifted side southeast of source A. In contrast, a redshifted southeast outflow appears absent in the hightemperature tracer CO 6–5 (Kristensen et al. 2013), although it
is seen in colder gas (CO 2–1; Girart et al. 2014). Likewise, the
PILS CO 3–2 data (Fig. 4) do show redshifted emission about
6 [′′] southeast of source A, and it is very prominent in the SiO
velocity map (Fig. 2) at _V_ lsr ≥ +5 km s [−][1], as well as in H 2 CO and
H [13] CN. In addition, a significantly redshifted patch of emission


Article number, page 5 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv




























|3–2 [ −4 .0, +1 .9] H2CO 51,5-41,4<br>[+20+40]<br>., .<br>[+41+110]<br>., .<br>B<br>A A|H213CO 51,5–41,4<br>B B<br>A|H13CN 4 –3<br>B<br>A|
|---|---|---|
|A<br>B<br> 8–7<br>A<br>29SiO 8–7|B<br>A<br>B<br>C34S 7–6|A<br>B<br>C2H 47/2–35/2|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig.** **3.** Integrated velocity ranges (blue, gray, and red contours) for each molecular line tracer. Contour levels start from 0.2 Jy beam [−][1] km s [−][1]
(equivalent to 3.3–7σ), except for H 2 CO (0.4 Jy beam [−][1] km s [−][1], rms noise levels poorly quantified due to lack of emission-free regions), H 2 [13] CO
(0.1 Jy beam [−][1] km s [−][1], ∼3.5–5σ), [29] SiO and C 2 H (both 0.07 Jy beam [−][1] km s [−][1], ∼1.6–3.5σ), and increase by a factor of two to the next level.
Equivalent negative contours are plotted in dashed style. The 0.87 mm continuum emission is shown in grayscale, stretching from 0.002 to 2.0
Jy beam [−][1] . We note that in the SiO 8–7 panel, the scattered, compact, negative value contours with angular sizes less than one beam are not real
signal, but artefacts from the continuum subtraction process.



is observed in SiO about 3 [′′] . 5 due west of A (and 4 [′′] south of
B), overlapping with the ‘kink’ location in the CO outflow, as
highlighted in Fig. 5 (see also Sect. 4.3). SiO 8–7 is also seen
prominently 1–2 [′′] north and south of source B, with mixed red
and blue velocity components along the line of sight (Figs. 3,
B.6), as well as in the fainter [29] SiO line (Fig. B.7). This structure is consistent with that observed in SiO 6–5 by Oya et al.
(2018).
Finally, a filamentary structure connected to source B with
a position angle of ∼170 [◦] is visible in C 2 H, but not in any
other tracer. Its velocity structure is flat, restricted to _V_ lsr values between +2 and +4 km s [−][1] (see Sect. 4.3 for further discussion). The redshifted (>+5 km s [−][1] ) emission in the velocity map of C 2 H (Fig. 2) is due to a bright CH 3 CN transition at
349.393 GHz. In positions near source A, the CH 3 CN line also
contaminates channels closer to the systemic velocity of C 2 H
(see Appendix A). In other positions in the map with integrated
intensity of C 2 H above 0.07 Jy beam [−][1] km s [−][1], the spectral profile shows a characteristic structure with two roughly equal intensity peaks spaced by 1.4 MHz, the separation between the
_F_ =4–3 and _F_ =3–2 hyperfine components (see Table 2, Fig. A.8
in this work, and Fig. 4 of Murillo et al. 2018). The interpretation
of the observed morphology and velocity structure is addressed
in Sect. 4.3 and Sect. 5.


**4.** **Analysis**


_4.1._ _Radiative transfer modeling of the interbinary bridge_


The bridge between protostars A and B, as traced by the submillimeter dust continuum and cold C [17] O gas (Sect. 3), is


Article number, page 6 of 27



kinematically quiescent (Sect. 3) and its central velocity at
_V_ lsr =+3 km s [−][1] is consistent with the velocities of the individual protostars (+2.7 and +3.1 km s [−][1] ). It is therefore unlikely to
be associated with any of the outflows, and it is treated as a separate entity in this work. Besides C [17] O, none of the other selected
molecules match, simultaneously, the morphology of the dust
bridge filament and the narrow line-of-sight velocity distribution
of C [17] O.

In principle, an assessment of density and temperature
conditions throughout the inter- and circumbinary region of
IRAS 16293 could be set up using spectral line intensity ratios of
various molecules and transitions highlighted in this work (see
Table 2). However, given the multitude of partially resolved dynamical components, it is not at all certain that line intensities
measured toward a particular position emanate in the same gas
for one transition of a species and another transition of another
species. We therefore refrain from embarking on such an analysis.

To study the quiescent interbinary bridge, we use a curved
cylinder filament model, spanning 636 au between and enveloping the two sources in an arc-like structure. The density profile of
the bridge arc is a power-law which decreases with radius to the
power −0.25 and is independent of the distance from either protostellar source. The enclosing envelope extends to beyond our
field of view, and has a purely spherical geometry, with a density
profile decreasing radially with a power of −1.7 and a density
plateau imposed at radii within 600 au. This is the same filament
model used in J2018, who show that, when using luminosities
of 18 _L_ ⊙ and 3 _L_ ⊙ for sources A and B, respectively, the model
yields a qualitative match with the morphology and peak emis

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars


**Table 2.** Selected line transitions.


Molecule Transition Rest frequency _[a]_ _E_ up / _k_ _n_ crit _[b]_ Traced component _[f]_

(GHz) (K) (cm [−][3] )
Dust (continuum) 344 (0.87 mm) - - Quiescent bridge between A and B.
C [17] O _J_ = 3–2 337.061 _[c]_ 32.5 4.1×10 [4] Quiescent bridge between A and B.
12 16 _d_
C O _J_ = 3–2 345.796 33.2 4.1×10 [4] Redshifted, outflow cone accelerating westward from A;
onset of eastern counterpart of westward outflow;
blueshifted knot south of B.
H [13] CN _J_ = 4–3 345.33977 41.4 1.2×10 [8] Redshifted northern wall of PA 270 [◦] outflow;
Redshifted outflow southeast (PA 135 [◦] ) from A.
o-H 2 CO _J_ _K_ _a_, _K_ _c_ = 5 1,5 – 4 1,4 351.76864 62.5 7.5×10 [7] Redshifted northern wall of PA 270 [◦] outflow;
Blueshifted interface wall with bridge.
Redshifted outflow southeast (PA 135 [◦] ) from A.
o-H 2 [13] CO _J_ _K_ _a_, _K_ _c_ = 5 1,5 – 4 1,4 343.32571 61.3 7.5×10 [7] Redshifted northern wall of PA 270 [◦] outflow;
C [34] S _J_ = 7–6 337.39646 50.2 1.5×10 [8] Blueshifted gas in same direction as ‘axis’ of bridge.
SiO _J_ = 8–7 347.33058 75.0 6.1×10 [7] Axes of of redshifted (PA 135 [◦] ) and
blueshifted (315 [◦] ) outflows from A;
Mixed-velocity pockets north and south of B;
29
SiO _J_ = 8–7 342.98084 74.1 5.9×10 [7] Redshifted outflow southeast (PA 135 [◦] ) from A.
Mixed-velocity pockets north and south of B;
C 2 H _N_ _J_ = 4 7/2 – 3 5/2 349.39997 _[e]_ 41.9 1.4×10 [7] Quiescent, narrow filament across B.


**Notes.** [(] _[a]_ [)] Rest frequencies taken from the Cologne Database for Molecular Spectroscopy, CDMS (Müller et al. 2005; Endres et al. 2016). Original
sources of spectroscopic data: C [17] O, Klapper et al. (2003); CO, Winnewisser et al. (1997); H [13] CN, Cazzoli & Puzzarini (2005); H 2 CO and H 2 [13] CO,
Cornet & Winnewisser (1980); C [34] S Gottlieb et al. (2003); SiO and [29] SiO, Müller et al. (2013); C 2 H, Padovani et al. (2009).
( _b_ ) Critical density is calculated as the ratio of the Einstein _A_ coefficient and the collision rate at a temperature of 100 K, which are accessed through
the LAMDA database (Schöier et al. 2005), with the following original sources: CO (adopting o-H 2 as dominant collision partner), Yang et al.
(2010); H [13] CN, Dumouchel et al. (2010) for main isotopologue; H 2 CO and adopting identical rates for H 2 [13] CO, Wiesenfeld & Faure (2013); C [34] S
adopting rates for the main isotopologue C [32] S, Lique et al. (2006); SiO and adopting identical rates for [29] SiO, Dayou & Balança (2006); C 2 H,
Spielfiedel et al. (2012).
( _c_ ) The hyperfine splitting of C 17 O 3–2 and H 13 CN 4–3 is discussed in Appendix A.
( _d_ ) For 12 C 16 O, we study morphological features using only velocity channels at | _V_ lsr − v systemic | > 5 km s −1, as shown in Fig. 4.
( _e_ ) The rest frequency for C 2 H 4 7/2 – 3 5/2 is the average of the tabulated rest frequencies for the individual hyperfine components, _F_ =4–3 at
349.39928 GHz and _F_ =3–2 at 349.40067 GHz.
( _f_ ) source A and source B are abbreviated as ‘A’ and ‘B’; ‘PA’ denotes position angle east of north, following Fig. 1.



sion levels seen in the 0.87 mm dust continuum emission and
C [18] O/C [17] O gas line emission. The fiducial model adopted in this
paper is equivalent to ‘Rotating Toroid model 1’ in J2018. The
temperature structure of each cell in the model is derived selfconsistently, based on the adopted luminosities of both sources A
and B (Fig. F.4 of J2018). We do not scale distances in the model
to the newly published distance of IRAS 16293 (see Sect. 1), to
allow inclusion of and direct comparison with results from the
modeling work of J2018. An 18% increase in source distance
would have little impact on the model outcomes, compared with
other assumptions with considerably larger uncertainties, such
as dust opacity and sublimation thresholds (see below).


The line radiative transfer code `LIME` (Brinch & Hogerheijde
2010) is used to obtain synthetic line emission cubes of the
H 2 CO 5 1,5 –4 1,4 and H [13] CN 4–3 gas line emission, analogous
to the strategy used in J2018 for CO and its isotopologues. We
use an abundance jump model to emulate freeze-out onto the
dust grains. When the dust temperature is below the sublimation
temperature, the gas phase abundance is decreased by a depletion factor. See Table 3 for more information on the individual

molecules. Uncertainties in the sublimation thresholds could be
up to ∼30% (see references in Table 3). This study only considers the inter- and circumbinary region and excludes the warm
‘disk regimes’ at ≳50 K (cf. the model temperature structure in
Fig. F.4 of J2018). Therefore, adjusting the adopted sublimation
temperature by 30% would only impact the modeled emission
morphology of CO species, and only those that are optically thin



(C [17] O, C [18] O), while those of H 2 CO and H [13] CN would be left
unaffected. The number density of H 2 is above 10 [8] cm [−][3] in the
modeled bridge filament, sufficiently high to validate the occurrence of depletion of gas-phase molecules onto dust grain surfaces. Since we are investigating the appropriateness of a static
filament structure to the observation of the quiescent bridge only,
we keep the velocity structure of the model static, with only
random velocity dispersions included, such as from turbulence.
We fix the built-in velocity dispersion parameter (Doppler _b_ ) in
`LIME` to 1 km s [−][1] . This value is the 1/e half-width, equivalent to a
FWHM of 1.4 km s [−][1] for a Gaussian line profile, which is representative of the measured line widths in the region under study.
The only free parameter is the molecular abundance. Twenty different abundance values are run for each molecule in the range
given in Table 3. After `LIME` produces a synthetic line emission
cube, it is convolved with a 0.5 [′′] × 0.5 [′′] beam in the image analysis software package `MIRIAD` . We refer to J2018 for further details of the model definition and the radiative transfer approach.


In Fig. 6, integrated intensity maps of the radiative transfer calculations described above are juxtaposed with their observed counterparts. The latter are produced by integrating over
the narrow velocity range _V_ lsr =[+2.0,+4.0] km s [−][1] (i.e., all channels with contours in black in Figs. B.1–B.3 in the Appendix),
with the aim of filtering out dynamically active gas associated
to the various outflow components which are not included in
the density distribution of the model (J2018). As already concluded by J2018, the model in C [17] O provides a qualitative match


Article number, page 7 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



high-velocity CO 3–2



CO 3–2 and SiO 8–7



























23.2 _[s]_ 22.8 _[s]_ 16 _[h]_ 32 _[m]_ 22.4 _[s]_


RA (J2000)


**Fig. 4.** Map of six different velocity bins of the main CO isotopologue,
highlighting high-velocity gas at - 5 km s [−][1] from the systemic velocity ( _V_ lsr ≈+3 km s [−][1] ) of the protostars: absolute velocity difference of

[5,7] km s [−][1] in cyan and orange contours, of [7,9] km s [−][1] in black and
darker orange, and of [9,11] km s [−][1] in blue and red. The lowest contour
level and step to the next contour is 1.0 Jy beam [−][1] km s [−][1] . The 0.87 mm
dust continuum is shown in grayscale. The arrow indicates the slice for
the position-velocity diagram shown in Fig. 7. The position of the water
maser spot at _V_ lsr =+6.1 km s [−][1] (Dzib et al. 2018) is marked with a red
circle with a yellow outline, ∼1 [′′] west of source A. A linear scale indicator is plotted in the bottom right corner, and the size of the synthesized
PILS beam in the bottom left corner.


**Table 3.** `LIME` model parameters.


Molecule _X_ /H 2 _T_ subl _[a]_ Depletion _b_ _[c]_

range [K] factor _[b]_ [km s [−][1] ]
C [17] O 5.58×10 [−][8] 30 100 1
o-H 2 CO [1 × 10 [−][8], 3 × 10 [−][6] ] 50 100 1
H [13] CN [2 × 10 [−][12], 2 × 10 [−][10] ] 100 100 1


**Notes.** All parameters for C [17] O are identical to those in J2018 (see
their Table 3).
( _a_ ) Ice mantle sublimation temperature for HCN follows those of other
CN-bearing species (e.g., Noble et al. 2013). That of H 2 CO follows
Aikawa et al. (1997), Ceccarelli et al. (2001) and Rodgers & Charnley
(2003).
( _b_ ) When depletion is applied in the model, the gas phase abundance of
the molecule in question is divided by the depletion factor.
( _c_ ) Doppler parameter as defined in `LIME`, that is, the 1/e half-width of a
thermally broadened line.


to the morphology of the bridge connecting the two protostars,
although the observed C [17] O filament is laterally ∼3 times wider
than the modeled curved filament. Absolute flux values produced
by the model are a factor ∼2 higher than observed. H 2 CO is also
present and detected in its 5 1,5 –4 1,4 transition across the bridge
area outlined by the continuum contours, but its observed morphological shape is different from that of C [17] O and the continuum. The difference is partly due to the inclusion of outflow

Article number, page 8 of 27



23.2 _[s]_ 22.8 _[s]_ 16 _[h]_ 32 _[m]_ 22.4 _[s]_


RA (J2000)


**Fig.** **5.** Overlay of the maps of high-velocity CO emission (solid blue
and red contours), and non-systemic SiO emission (dash-dotted cyan
and magenta contours). The three separate CO velocity bins on either
side of the systemic velocity shown in Fig. 4 are collapsed into one bin
for this figure (solid blue and red contours). The blueshifted and redshifted SiO emission (dashed cyan and magenta contours) is the same
as shown in the bottom left panel of Fig. 3. A linear scale indicator and
the size of the synthesized PILS beam are plotted in the bottom right
and bottom left corners, respectively.


impacted gas, despite the attempt to exclude this by using a narrow velocity integration range. The modeled H 2 CO emission extends radially over many hundreds of au surrounding the binary,
an effect of H 2 CO molecules being present in the gas phase in
the spherical envelope component of the model. The superposed
density structure of the disks-bridge-envelope model is dominated by that of the spherical envelope model at such large radii
of ∼700 au (from the midpoint between A and B). Outside this
radial distance of 700 au, the number density of the modeled envelope component drops below 10 [7] cm [−][3] (the outermost gray,
circular contour in Fig. F.4 of J2018). Along with radially decreasing temperatures, this leaves conditions insufficient to excite o-H 2 CO 5 1,5, with a critical density of 7.5×10 [7] cm [−][3] and an
upper energy level of _E_ up / _k_ =62.5 K (Table 2). In addition to tracing the bridge filament, the H 2 CO model map shows enhanced
H 2 CO emission up to ∼2 [′′] above the disk of source A (northwest
and southeast of A), where the temperature is sufficiently high to
sublimate H 2 CO from dust grains (cf. 55 K contour in Fig. F.4 of
J2018). Finally, the observed morphology of H [13] CN in the interbinary region does not follow the shape of the bridge filament.
Most of the H [13] CN 4–3 emission shown in Fig. 6, bottom left,
is due to contamination from outflow-impacted components (despite our effort to exclude these using a narrow velocity integration interval), none of which are included in the physical model.
As expected from its high critical density, the radiative transfer
model does not populate the _J_ =4 level of HCN species beyond
the disk domains. The exception is a small region immediately
above the disk plane, where _T_ kin >100 K (again, see Fig. F.4 of
J2018), where the observed enhancement in H [13] CN emission is
reproduced by the model.

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars























9.60


4.80


2.40


1.20


0.60


0.30


0.15


6.4


3.2


1.6


0.8


0.4


0.2


0.1


6.4


3.2


1.6


0.8


0.4


0.2











0.1


**Fig. 6.** Comparison of observed (left) and modeled (right) morphology
of spectral line emission from C [17] O, H 2 CO, and H [13] CN. In the C [17] O
model panel, the disk domains are masked (as in Fig. 2). Total intensity from the observed cubes is calculated by integrating over _V_ lsr range

[+2,+4] km s [−][1] . The continuum peak locations are marked by star symbols, the ALMA interferometric beam size is indicated in the bottom
left of each ‘observed’ panel. The modeled line intensity maps are convolved with the observational beam size, to aid direct comparison. Line
intensity is represented by the color scale and gray contours (identical
for observed and modeled panels: lowest level at 0.15 for C [17] O, 0.10
Jy/beam km s [−][1] for H 2 CO and H [13] CN, and increasing by a factor of 2
each level). Black contours indicate the 0.87 mm dust continuum.


In conclusion, the bridge morphology is observed in dust,
C [17] O, and partly also in o-H 2 CO, and the physical model constructed by J2018 roughly reproduces the morphology of the
dust continuum and C [17] O emission. The partial overlap between
the observed H 2 CO emission and that produced by the model
(Fig. 6, middle panels) should not be over-interpreted. As shown
in Figs. 2 and B.3, the H 2 CO observed in the direction of the
bridge filament domain is largely at line-of-sight velocities that
are offset from the quiescent C [17] O bridge filament at the systemic velocity. In fact, the lower optical depth tracer H 2 [13] CO in
the same transition (Fig. B.4) shows no detectable emission in
the bridge domain in the _V_ lsr range from +2.0 to +4.0 km s [−][1] .
This means that the observed H 2 CO emission is not tracing the
bulk gas in the quiescent bridge filament, but rather surface layers of dynamically stirred components. In our interpretation, this
indicates that the number densities in the modeled bridge component are higher than in reality. A more realistic model would
not produce any H 2 CO emission from the bridge component.
H [13] CN 4–3 emission is not seen outside of the disk domains in



the modeled map, and does not trace the bridge morphology in
the observed map (Fig. 6, bottom panels). The explanation for
the lack of H 2 CO and H [13] CN emission in the bridge filament
is provided by the excitation balance governed by density and
temperature. Looking at the critical densities and _E_ up values in
Table 2, the upper levels of the relevant H [13] CN and H 2 CO transitions do not get populated sufficiently. The freeze-out abundance drop in the model (Table 3) is not the cause, which we
confirm with a separate radiative transfer model run in which
freeze-out is neglected completely, keeping all molecules in the
gas phase. In the resulting emission maps (shown in Fig. C.1
of Appendix C), there is still no H [13] CN 4–3 emission outside of
the disk regions. Without freeze-out, the model o-H 2 CO 5 1,5 –4 1,4
emission map is dominated by the contribution from the cold, extended envelope (Fig. C.1). In contrast with H [13] CN, H 2 CO still
does show a small intensity enhancement in part of the bridge
arc region, probably reflecting its slightly lower critical density
when compared with HCN 4–3. The total line-of-sight optical
depth of the superposed components, particularly for H [13] CN,
becomes much higher in the ‘no freeze-out’ case, as expected
when all H [13] CN molecules remain in the gas phase even in the
colder, extended envelope that surrounds the binary.

The fiducial model (RTM 1 from J2018) is not necessarily the
only and best fit to the data. The only observational constraints
that were taken into account were the multiwavelength SED
and the distribution of CO 3–2 isotopologues and submillimeter dust emission; the J2018 work did not include an assessment
of molecular lines tracing a range of densities. The number density at the axis of the modeled bridge arc is 7.5×10 [8] cm [−][3] . The
density structure that was adopted by J2018 was mainly driven
by the wish to reproduce the dust emission morphology. However, dust emission strength depends on several factors which are
all assumed to be fixed in the model setup: dust opacity, gas-todust ratio, and a dust temperature being coupled rigidly to that
of the gas. For example, if a different grain size distribution is
assumed, higher submillimeter grain opacities could arise, lowering the peak (column) density required to match the observed
dust emission. Similar arguments hold for a lower gas-to-dust ratio and a higher dust temperature. A combination of these effects
can easily bring the model peak number density down by a factor
of 10–100 to well below the critical densities of the CS, H 2 CO
and HCN transitions selected in this work (Table 2). In this work,
a suite of molecular tracers with different critical densities are
studied, among which C [17] O 3–2 (4×10 [4] cm [−][3] ), o-H 2 CO 5 1,5 –
4 1,4 (7.5×10 [7] cm [−][3] ) and H [13] CN 4–3 (1.2×10 [8] cm [−][3] ). Of these,
C [17] O 3–2 is the only species that traces the bridge morphology
observed in dust continuum (see above), and, additionally, the
distribution of two lines of [34] SO 2 observed in the PILS data
cube (critical densities of 3.8×10 [7] cm [−][3] and 8.3×10 [7] cm [−][3] ) is
also confined to the disk domains of the two protostellar sources
(Drozdovskaya et al. 2018). Put together, this indicates that, indeed, the real density of the bridge is likely between 4×10 [4] cm [−][3]
and 3×10 [7] cm [−][3] .
Besides the low-density tracers C [17] O 3–2 and 0.87 mm dust,
all emission observed from other molecular species in the vicinity of the bridge domain can be ascribed to components with a
measurable velocity along the line of sight, or their impact on
more quiescent regions (see below in Sect. 4.3).


_4.2._ _Fragmentation of the bridge_


It is conceivable that both protostellar sources A and B formed
from the bridge filament through gravitational instability. In this


Article number, page 9 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



context, we follow the analytic approach by Ostriker (1964) and
treat the bridge as an isothermal cylinder. In this idealized scenario (far more simplified than the self-consistently derived temperature structure modeled by J2018 and used in our Sect. 4.1),
the thermal pressure in the cylinder keeps it from collapsing radially if the mass per unit length, _M_ / _L_, is below a certain threshold,


_M_ / _L_ = [2] _[kT]_ [kin] (1)

µ _m_ 0 _G_ [.]


This quantity depends linearly on kinetic temperature _T_ kin and
is inversely proportional to the mass of the typical particle µ _m_ 0,
with _m_ 0 the mass of a proton. It is the equivalent of Jeans mass
in cylindrical geometry. Using µ = 2.0 for H 2 and three different temperature values of [25, 30, 40] K, we arrive at a stability
threshold of [0.14, 0.17, 0.23] _M_ ⊙ per 600 au (the approximate
projected length of the bridge).
We compare the mass per length stability criterion derived
above with an observationally derived mass of bridge material,
calculated as follows. We take the average C [17] O 3–2 intensity
of 600 mJy beam [−][1] (integrated over the [+2,+4] km s [−][1] velocity
range), and use `RADEX` (Van der Tak et al. 2007) non-LTE radiative transfer calculations to convert to a C [17] O column density.
Such a calculation requires a kinetic temperature and a number density of collision partners as input. To represent a natal, isothermal, cylindrical filament, we choose a temperature
between the minimum temperature of the modeled bridge arc
(24 K) and the average temperature in the bridge domain (41 K)
(see Sect. 4.1 and J2018). For number density, _n_ H 2, we adopt
10 [5] cm [−][3], which is between the critical density of C [17] O 3–2 and
those of HCN 3–2, H 2 CO 5 1,5 –4 1,4 and SO 2 17 4,14 –17 3,15 (Table 2, Sect. 4.1). With _T_ kin =[25, 30, 40] K, we obtain a C [17] O
column density of [6.2, 5.4, 4.8]×10 [15] cm [−][2], only mildly sensitive to temperature. Using a [16] O/ [17] O ratio [3] of 2.005×10 [3] (Wilson 1999) and CO/H 2 =10 [−][4], this corresponds to _N_ (H 2 )=[1.24,
1.08, 0.96]×10 [23] cm [−][2] . Taking a rough half-power width of the
dust bridge of 200 au, the total mass encompassed by the bridge
‘cylinder’ area of 200×600 au between sources A and B is

[0.0056, 0.0049, 0.0044] _M_ ⊙ .
On the other hand, integrating the mass of all dust and gas in
the bridge component of the model described in Sect. 4.1 yields
a tenfold higher total mass of 0.055 _M_ ⊙ . Either way, the total
bridge mass values are below the stability threshold at the assumed temperatures of 25, 30, and 40 K. The discrepancy between these two bridge mass calculations is not surprising, given
the assumptions in the dust model from J2018. The dust opacity
model, from Ossenkopf & Henning (1994), uses a micron-sized
dust distribution. In the hypothetical case that grain growth has
already taken place and that the true size distribution of dust
grains in the bridge peaks at sizes of 100-1000 µm, then opacities at 345 GHz (expressed per gram of material) can be up to
a factor of 10 larger, which would mean that the mass determination from our radiative transfer calculations is overestimated
by up to an order of magnitude. However, there is no evidence to
support that the size of the dust grains in the interbinary bridge of
IRAS 16293 would deviate from the roughly micron-sized populations representative of the unprocessed interstellar medium.
Moreover, the canonical gas-to-dust mass ratio of 100 was used,
and any deviation from this value would also change the total
mass estimate of the modeled filament.


3 The adopted 16 O/ 17 O ratio is consistent with that measured in H 2 CO
toward IRAS 16293B by Persson et al. (2018): (2.0–3.0)×10 [3] .


Article number, page 10 of 27



In the case presented above in which the filament mass is
below the Ostriker stability criterion, the filament would be supported against radial collapse. This scenario, in fact, is the only
way in which a filament may persist long enough for it to fragment along its vertical (length) direction (Inutsuka & Miyama
1992) and form additional dense cores. However, the total mass
budget available in the current bridge filament (see above) seems
insufficient to form even a brown dwarf. Again in an idealized
nearly isothermal scenario, Inutsuka & Miyama (1997) have
shown that separation between fragmented cores within a radially stable filament are on the order of four times its width.
This ratio is consistent with the bridge observed in IRAS 16293,
with an observed diameter of ∼200 au, and separation between
the cores of at least 600 au, knowing that the vector connecting
sources A and B may be inclined with respect to the plane of
the sky. While the bridge filament present little to no gas motion
along the line of sight (≲1 km s [−][1] ), observations presented in this
work and in other papers in the literature do not rule out gas flow
vectors in the plane of the sky along the length of the filament,
possibly regulated by the highly ordered magnetic field in the
bridge (Sadavoy et al. 2018).
Finally, we emphasize that, if indeed the bridge filament has
been host to sources A and B, the filament must have been considerably more massive in the past. After adding even half of the
current mass of sources A and B (0.5 _M_ ⊙ ) to the current bridge
filament mass calculated above, it is lifted to a factor few above
the gravitational instability threshold. We emphasize that the interpretation of stability of the filament, sketched in this section,
only holds for the filament in its current state. Radial collapse in
an earlier evolutionary stage, with a different mass distribution
and under different temperature conditions, is not ruled out. To
conclude, the observed filament is obviously more complex in
nature than a static, cylindrically symmetric shape characterized
by a single temperature. A true assessment of its gravitational
stability should include, for example, turbulent and magnetic
support. Any additional mechanisms to provide support against
gravitational collapse would only increase the stability threshold,
and the conclusions drawn in this section about the dynamical
stability of the filament would thus remain unchanged.


_4.3._ _Kinematics_


Besides the bridge filament (Sects. 4.1, 4.2), almost all other
morphological components discussed in this paper are dynamic
and can be attributed to protostellar outflow activity. Distinct
components are discussed in this subsection and are summarized
in Fig. 1 and Table 2.
The CO 3–2 velocity map in Fig. 4 clearly traces the western lobe of the known east-west outflow pair. However, its eastern counterpart and the separate southeast-northwest pair are
all much less pronounced, possibly because the eastern outflow is intrinsically dimmer (see also Yeh et al. 2008) and the
southeast-northwest pair may have lower line-of-sight velocity.
In fact, the southeast outflow lobe from source A is detected
in larger spatial extent at more modestly redshifted velocities
( _V_ lsr =[+6,+8] km s [−][1] ) than those shown in Fig. 4. The line-ofsight velocity in the western lobe increases with distance from
source A, implying an acceleration with time. This is consistent with a centrally driven outflow that would naturally accelerate as the density of the ambient envelope, and therefore the
pressure, decreases with radius (e.g., Moriarty-Schieven & Snell
1988; Arce et al. 2007) . In addition, the CO outflow in Fig. 4
exhibits a relatively collimated morphology up to ∼3 [′′] (∼350 au
in projection) from source A, at which point it abruptly fans out

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



into a cone-like structure. This position coincides with a marked
enhancement in SiO 8–7 emission (Fig. 5), possibly related to
a simultaneous acceleration of the outflow (leading to SiO enhancement through dust grain erosion) and decrease in ambient
pressure (leading to a wider angle CO structure). The position
of this kink may be related to the radial extent of the rotating
‘inner envelope’ described by Oya et al. (2016). However, these
authors infer a radius of the inner envelope of 200 au, whereas
a density drop would be needed beyond 300 au to explain the
location of the kink in the CO outflow morphology described
above. Alternatively, the opening angle of the western outflow
may be restricted by higher pressure inside the quiescent interbinary bridge described in Sect. 4.1 of this work. Its radius
(as observed in dust continuum and C [17] O, Fig. 2, top left; Fig. 6,
top left) appears to be more congruent with the 350 au radial
separation from source A.
Closer in to the source, at about 120 au projected distance
west of source A, a H 2 O maser spot detected by Dzib et al.
(2018) seems to coincide with the interface between the dense,
rotating, disk-like structure surrounding source A (blue on the
west, red on the east) and the emerging redshifted outflow in the
western direction (see Figs. 1, 4). The direction of proper motion of the maser spot (position angle ∼290 [◦], Dzib et al. 2018)
roughly follows the flow direction of the western outflow as seen
in CO 3–2 PILS data (Fig. 4). This overlap supports the suggestion made by Dzib et al. (2018) that the redshifted maser spot
may be due to a launching shock at the base of the outflow. A
similar argument may hold for a blueshifted maser spot detected
to the east of source A, although the spatial association is more
ambiguous than for the redshifted counterpart (Dzib et al. 2018).
In contrast to 12 C 16 O, the other molecular tracers selected from the PILS data set mainly highlight the collimated
northwest-southeast pair. Kristensen et al. (2013) detected only
the northwest side of this outflow in CO 6–5, while Girart et al.
(2014) detected both sides in CO 3–2 and SiO 8–7. In addition
to previously detected tracers, in this work, we also detect both
symmetric counterparts in o-H 2 CO, H [13] CN: redshifted with respect to source A to the southeast, blueshifted to the northwest
(Fig. 2). Blueshifted emission in o-H 2 CO, H 2 [13] CO, and H [13] CN
appears to trace the interface of the northwest outflow with the
dust bridge. This observed blueshifted emission at the southwestern edge (‘inside bend’) of the bridge could be an indication
of the outflow impacting the quiescent bridge and sweeping up
material in its wake. Pockets of enhanced H 2 CO emission may
be the result of molecules being sputtered from the mantles of
mildly shocked grains associated to one of the outflow lobes.
Model calculations show that such effects can be attained by
shock velocities of ∼10–15 km s [−][1] (Caselli et al. 1997; Suutarinen et al. 2014). More energetic shocks would produce increased
amounts of SiO in the gas phase through erosion of the grain
cores, for which simulations indicate that shock velocities should
exceed ∼25 km s [−][1] (e.g., Gusdorf et al. 2008a,b). The lack of
correlation between the observed spatial extent of gas-phase SiO
and H 2 CO suggests that it is not the same shocks responsible
for both molecules; other aspects, such as local density and temperature, must also play a role in determining the morphology
of the H 2 CO emission map. The morphology of SiO emission,
particularly on the southeast side of source A, outlines a more
collimated, redshifted outflow (jet) structure than the maps of
H 2 CO and H [13] CN do (Fig. 2).
The blueshifted structure of C [34] S is seen deeper into the
bridge than H 2 CO and H [13] CN, closer to the central axis of the
bridge. Despite the overlap between the bridge and the C [34] S, the
blueshifted velocities of the latter suggest that it is not part of


|Col1|CO<br>C17O<br>C2H<br>V sys,B<br>disk domain|
|---|---|
|||
|||



**Fig. 7.** Position-velocity diagram along the slice indicated by the arrow
in Fig. 4. Velocity is the intensity-weighted peak velocity, as in Fig. 2.
Position displacement is defined to be positive to the north of source B.
The ‘disk domain’, inside which intensity-weighted velocity values are
not meaningful, is marked with a partly transparent gray box.


the quiescent bridge. The redshifted emission component seen
in H 2 CO, H [13] CN and C [34] S appears to be at the northernmost
section of the redshifted outflow at position angle ∼270 [◦] (Yeh
et al. 2008). In summary, the two outflow-like emission shapes
at position angles 335 [◦] and 285 [◦] (Fig. 1) are interpreted as two
unrelated features. In our data, there is insufficient symmetry
and alignment to assign them to the rotating structures around
source A at position angle (rotation axis) 326–360 [◦] (Favre et al.
2014; Oya et al. 2016). We refer to Fig. 1 for an illustration of
the misalignment.
The picture drawn in Fig. 1 also addresses the coupling
of small scales (60–1500 au), as seen in interferometric observations, with larger scales (∼2000–30 000 au) measured in
single-dish observations. Firstly, we confirm the finding by Yeh
et al. (2008) that the east-west outflow pair at a few-hundred
au scales is consistent with the much larger outflow lobes extending out to thousands of au in the same direction, likely
both driven by component A in the IRAS 16293 system. Secondly, the arcminute-scale outflow pair which is redshifted to
the northeast and blueshifted to the southwest (Mizuno et al.
1990; Stark et al. 2004) does not appear to have any counterpart at scales below ∼1000 au. This points to an outflow driven
by IRAS 16293A at some time in the past, but which has been
quenched in recent times. Adopting an inclination angle of 65 [◦]
for the northeast-southwest outflow lobes and a line-of-sight velocity offset of 10 km s [−][1] (Stark et al. 2004), the absence of
a northeast-southwest flow at scales ≲1000 au translates into a
timeframe for the quenching of a few hundred years.
Finally, the strongly blueshifted components apparent in
CO 3–2 (Fig. 4) near source B are interpreted using the positionvelocity diagram in Fig. 7. We choose a south-north slice in order to cover the C 2 H emission on either side of source B as well
as the [12] CO blob south of source B. In the diagram, displacement values below −3 [′′] correspond to the regime of the northern
edge of the outflow cone emanating westward from source A,
where redshifted velocities are observed. All weighted velocity
values for the main CO isotopologue within 3 [′′] on either side
of source B, however, are significantly blueshifted with respect
to the systemic velocity of source B (vertical dotted black line


Article number, page 11 of 27



4


3


2


1


0


_−_ 1


_−_ 2


_−_ 3


_−_ 4



-2 +0 +2 +4 +6 +8
Intensity-weighted _V_ lsr (km s _[−]_ [1] )

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



in Fig. 7). This must mean that surface layers on the front side
(facing the observer), probed by optically thick CO emission, are
moving away from the center of mass of protostellar source B.
Already noted in the 2008 publication by Yeh et al. (their position ‘b2’), the origin of this kinematic structure is still under
debate. It may be a compact (and therefore young) outflow feature driven by source B (Loinard et al. 2013; Oya et al. 2018), or
alternatively, a bow shock feature related to the northwest outflow driven by A (Kristensen et al. 2013). If driven by B, it remains to be explained why the symmetrical counterpart is hidden
from sight, even at displacements 2–3 [′′] north of source B, where
dust optical depth would not be sufficient to absorb line emission from the background. If driven by source A, the relatively
modest velocity of the NW outflow axis, ≲5 km s [−][1] with respect
to either source (H [13] CN and SiO panels in Fig. 2), has somehow
been translated into much higher velocities for the dense material in the outskirts of source B (up to 10 km s [−][1] with respect to
the protostar, see dark blue contours in Fig. 4). One conceivable
scenario is that a dense stream of gas emanating from source A
impacts dense material around source B, which deflects part of
the gas such that its velocity vector becomes more aligned with
the line of sight direction, which leads to higher line-of-sight velocity offsets. It may also be that some other, yet unidentified dynamical process is contributing. In the same region where [12] CO
is blueshifted, the bulk mass traced by optically thin C [17] O has
velocities consistent with the systemic velocity of source B. In
the disk domain, masked in Fig. 7 with a box spanning a width
identical to the diameter of the masks in Fig. 2, even C [17] O is
affected by the high optical depth of line and continuum photons. The C 2 H emission, which also stretches north-south across
source B (Figs. 2, B.8), shows a velocity trend in Fig. 7 overlapping that of C [17] O. These two species show a modest velocity
gradient across source B,: _V_ lsr is +1.8 to +2.7 km s [−][1] north of
source B, and +2.6 to +4.1 km s [−][1] south of B, whichever physical component it traces.
Two pockets of SiO 8–7 emission are seen ∼1 [′′] north and
south of source B, at position angle 15 [◦] east of north (Fig. B.6),
not overlapping with the C 2 H filament (Sect. 5.4) at position angle −15 [◦] . Line of sight velocities of SiO in these pockets are
shifted toward both blue and red sides of the systemic velocity,
which makes their association to either outflow or inflow motions ambiguous. The much weaker, but optically thin emission
from [29] SiO (Fig. B.7) shows the same morphology, again with
mixed blue and red velocities. The morphology and kinematics
of SiO 8–7 in our map is consistent with that observed in SiO
7–6 by Oya et al. (2018), who interpret this structure as a signature of a pole-on pair of outflows.


**5.** **Discussion**


To highlight the different physical and dynamical components
studied in this work, the molecular gas observed between and
around the binary protostellar system IRAS 16293 at 60–1500 au
scales is divided into three distinct domains: (i) dense and hot
(>100 K) gas in the disk or disk-like regions around sources A
and B; (ii) more tenuous and colder gas residing in the dust
bridge between the protostars; and (iii) kinematically active gas
within or on the borders of outflow lobes driven by source A. Domain (i) is not examined in this work, but its kinematics and temperature structure was extensively studied, using a different set of
molecular tracers, by Oya et al. (2016) for source A and by Oya
et al. (2018) for source B. Domains (ii) and (iii) are discussed in
Sects. 5.1 and 5.2. A structure seen in C 2 H, seemingly unrelated
to outflow or infall dynamics, is addressed in Sect. 5.4. Finally,


Article number, page 12 of 27



the relative evolutionary stage of the two sources in IRAS 16293
is addressed in Sect. 5.5.


_5.1._ _The quiescent bridge_


The arc-like bridge structure between protostars A and B is
made up of material which has a moderate density (4×10 [4] cm [−][3] –
∼3×10 [7] cm [−][3] ). Evidence for the density range is provided by the
observation that the only molecular species clearly tracing the
morphology of the dust arc is C [17] O, while all tracers of higher
density (see Table 2) follow outflow structures and have lineof-sight velocity structures that deviate significantly from that of
C [17] O. This interpretation is supported when our observations are
compared with three-dimensional models from J2018, yielding
a qualitative match in morphology of the observed bridge structure (Sect. 4.1). To finally distinguish between the effects of gas
temperature and gas density, observation would be needed of the
distribution of a similarly high density tracer ( _n_ crit - 10 [6] cm [−][3] )
which at the same time has a low upper level energy ( _E_ up < 30 K).
For example, the _J_ =3–2 or _J_ =2–1 transition of H [13] CN both satisfy these conditions.
We hypothesize that the bridge is a remnant substructure of
the circumbinary envelope (Schöier et al. 2002) or a filamentary core, from which both protostellar sources have formed in
the past. With its current mass budget and temperature conditions, the IRAS 16293 bridge filament is stable against further
gravitational collapse (Sect. 4.2). In addition, the bridge arc is
kinematically quiescent, lying at a flat _V_ lsr within 0.5 km s [−][1] of
the systemic velocities of both protostars (Fig. 2, top left). This
straightforward observational fact rules out a scenario in which
the bridge arc is one segment of a large, circumbinary disk (or
torus) in which both protostars would be embedded. In such a
scenario, the bridge gas would have shown a line-of-sight velocity gradient following the kinematic signatures of sources A
(+3.1 km s [−][1] ) and B (+2.7 km s [−][1] ), that is, a blue-to-red gradient in the southeast-to-northwest direction. This would only
comply with the observed flat velocity distribution if the ‘disk’
would rotate entirely in the plane of the sky, which is inconsistent
with the line of sight velocity difference of the two protostars.
Compared to other, tighter protostellar binary systems such as
GG Tau (Dutrey et al. 2014, 2016) and IRS 43 (Brinch et al.
2016), the bridge that we observe between the components of
IRAS 16293 lacks a symmetric complement to close a full circumbinary disk or torus, and its velocity structure is inconsistent
with disk-like rotation. If there is any velocity gradient across
the bridge, it is in the transverse direction rather than along the
length of the arc.
Although the 600 au separation between the two components
in IRAS 16293 is somewhere in the mid-field between close and
wide binaries (see Sect. 1), we conclude that the formation of
protostars A and B has probably occurred through turbulent fragmentation. The reason is that the competing scenario, disk fragmentation (Adams et al. 1989), is unlikely due to: (i) the lack of
evidence for a remnant of a circumbinary disk, as discussed in
detail in this work (see above); and (ii) the stark misalignment
between the two disk-like structures, face-on for source B (Jørgensen et al. 2016; Oya et al. 2018), and roughly edge-on for
source A (Pineda et al. 2012; Girart et al. 2014).
Like IRAS 16293, the more evolved Class I binary protostellar system IRAS 04191+1523, with two components separated
by 860 au, also shows a bridge of gas connecting the two protostellar sources (Lee et al. 2017). Based on the velocity structure of the C [18] O bridge, Lee et al. (2017) conclude that the two

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



sources and the bridge are a substructure of the same natal envelope, which has given rise to protostar formation through turbulent fragmentation. The object L1521F, hosting only a very
young, low-luminosity source (Bourke et al. 2006), has also revealed a filamentary arc of gas (HCO [+] ) when studied at high
resolution with ALMA (Tokuda et al. 2014). In this case, the
filament itself is not detected in dust continuum emission; it
connects to a compact millimeter continuum component at its
western-most terminus, whereas protostars have not yet formed
on its eastern end. The dense core Barnard 5, with at least one
embedded protostar, also exhibits filamentary structure within
which three additional, possibly prestellar condensations have
formed (Pineda et al. 2015). The physical origin of the filaments
in both L1521F and in Barnard 5 is unclear, but their long axis dimensions of ≳1000 au make a disk origin seem unlikely. In contrast, the Class 0 L1448 IRS3B triple protostellar system hosts a
heavily curved connecting filament seen in C [18] O, and its kinematics are consistent with being a remnant of a 254 au diameter
disk that is hypothesized to have spawned all three cores through
fragmentation of a disk or the innermost envelope (Tobin et al.
2016a). A connecting bridge was also found in the triple system
SR24, with a ∼700 au size, by Fernández-López et al. (2017),
who suggest that it, too, may be interpreted as a remnant of a
disk spiral arm. In each of these case studies, the bridging filaments appear to have a relation to the nursery of the protostellar sources, either in the form of a protostellar disk undergoing fragmentation or a substructure of a larger-scale envelope.
IRAS 16293 appears to belong to the latter category.


_5.2._ _Outflow signatures_


The SiO gas surrounding IRAS 16293B at projected radii up to
250 au ( _J_ =8–7, Sect. 4.3 of this work; _J_ =7–6, Oya et al. 2018) is
of mixed blue- and red-shifted velocity up to ±3 km s [−][1] from the
systemic velocity of source B. The presence of SiO in the gas
phase is often used as a tracer of outflow shocks (e.g., Flower
et al. 1996; Caselli et al. 1997; Gusdorf et al. 2008a,b). While
the overlapping blueshifted and redshifted SiO emission is suggestive of a geometry with approaching and receding outflows
superposed in projection (Oya et al. 2018), the relatively low velocities would not be expected to lead to grain erosion. Correcting the observed velocity for projection effects has a marginal effect, since the _V_ lsr offset is necessarily almost completely parallel
with the true velocity vectors in case of a face-on disk launching
an outflow along the line of sight. However, in the scenario that
the SiO pockets near source B are due to impact of the northwest outflow from source A, the currently observed velocities
of 5–10 km s [−][1] may not lead to sufficiently strong shocks. Before silicate material from the grain cores is released into the gas
phase, relative velocities should exceed ∼15km s [−][1] (e.g., Caselli
et al. 1997; Gusdorf et al. 2008a). This leaves neither the pole-on
outflow from source B nor the impact of the outflow from A onto
source B as a fully viable scenario.
The morphology of two molecular lines that are sensitive to
densities above 10 [7] cm [−][3], o-H 2 CO 5 1,5 –4 1,4 and H [13] CN 4–3 (Table 2), are compared with a three-dimensional model in Sect. 4.1.
In the observed maps (Fig. 2), these high-density tracers do
not coincide with the axis of the dust/C [17] O bridge. The modeled structure (J2018; Sect. 4.1 of this work) does not produce
emission in H 2 CO or H [13] CN from its bridge domain, consistent
with the observations. Instead, the modeled emission is concentrated in the disk domains (and is extremely optically thick for oH 2 CO), with an extended hour-glass at positions above the disk
plane of source A, qualitatively consistent with enhanced pock


ets of emission seen in the observed maps southeast and northwest of the edge-on source A. This is caused by self-absorption
in the high-density midplane of the disk or disk-like structure,
whereas its surface regions are less opaque, but still sufficiently
dense and hot to excite the H [13] CN into _J_ =4. The absence of
H [13] CN in the bridge in the models is due to the chosen ice sublimation temperature of 100 K, which is only exceeded in the
innermost regions close to the protostars.


The high-density molecular gas observed in emission near
the bridge filament is interpreted as being the effect of two outflows at position angles 315 [◦] and 270 [◦], impacting patches of
higher density in the ambient envelope. The northernmost of the
two outflows is blueshifted, and is posited to be material on the
southwestern edge of the bridge, swept up by the blueshifted
side of the northwest-southeast outflow pair (Sect. 4.3, Fig. 1).
The southern, redshifted component at position angle 285 [◦], coincides with the northern border of the redshifted western outflow
cone (Yeh et al. 2008; Fig. 4 in this work). The same molecules
are not observed at the southern edge of the western outflow;
we speculate that this is due to a density contrast in the ambient medium, with higher density at the northern side, toward the
bridge filament. H 2 CO in particular is known to sublimate efficiently from dust grain surfaces not just by thermal desorption,
but also by photodesorption such as occurs in classical photodissociation regions (Van der Wiel et al. 2009; Guzmán et al. 2011).
Chemical models of outflow-envelope interface regions (Drozdovskaya et al. 2015) also show enhanced H 2 CO abundance, at
early times. It is therefore natural to expect enhanced gas-phase
H 2 CO abundances in directly irradiated walls of outflow cavities
in young protostellar systems such as IRAS 16293.


_5.3._ _Peak location for complex organic molecules_


Searches for spectral signatures of relatively faint molecular
line signals from new, complex (organic) molecules in the
IRAS 16293 system often focus on positions close to source B,
rather than source A. The primary reason is the simpler, narrower spectral line profiles near source B, owing to the difference
in orientation of the disk-like structures surrounding sources A
and B, and the multitude of dynamically active outflow components associated with source A (Sect. 4.3, 5.2). With intrinsically
narrower, symmetric line profiles, the disambiguation of nearby,
partially overlapping lines is more straightforward. Specifically,
the emission strength of lines of complex molecules is seen to
peak in a region west-southwest of source B at about 0.5 [′′] from
its continuum peak (e.g., Baryshev et al. 2015; Coutens et al.
2016; Jørgensen et al. 2016; Lykke et al. 2017; Ligterink et al.
2017; Calcutt et al. 2018). The offset can be explained by the
effect of high optical depth of both line and continuum emission
closer to the source center. The comparative lack of complex
molecule emission on the north and east side of source B may
be related to the bridge filament connecting to source B on that
side (Sect. 5.1), where physical conditions, such as temperature
and dust optical depth, are likely different. In addition, excitation
conditions and spectral line shapes on the east side of source B
may be affected by the northwest outflow from source A impacting there (Sect. 5.2). Finally, even to the south and west of
source B, dynamical effects do play a role in shaping molecular
emission, as shown for example in the SiO morphology (Sect. 3,
Fig. 2).


Article number, page 13 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



_5.4._ _The C_ 2 _H filament_


A narrow filament of material stretching across source B in the
south-north direction is visible in C 2 H, and a similar, but slightly
offset patch of high-velocity ( _V_ lsr <−6 km s [−][1] ) [12] CO up to 1 [′′] . 5
south of source B. Compared with the C 2 H emission observed
in single-dish JCMT observations (Caux et al. 2011), it is evident that the majority of C 2 H flux is filtered out in our interferometric ALMA observations, much more than for spectral
lines of other species. However, regardless of missing flux from
a smooth, large-scale component, our ALMA C 2 H map reveals
compact substructures at scales ∼10 [2] -10 [3] au. The velocity profiles of [12] CO, C [17] O and C 2 H along this feature are shown in
Fig. 7. C 2 H has a rather flat velocity structure along the length
of the filament, at _V_ lsr within ∼1 km s [−][1] of that of source B itself,
as already apparent from its intensity-weighted velocity map in
Fig. 2. The morphology of this feature, combined with its small
line of sight velocity gradient, would be more consistent with a
symmetric (outflow or infall) motion almost exactly in the plane
of the sky, than with an outflow emanating perpendicularly from
the face-on disk of source B. Moreover, the observed spatial distribution of C 2 H is not consistent with tracing one or multiple
walls of outflow cavities carved out by any of the outflows in
this system, such as has been observed in C 2 H morphologies in
other protostellar system at similar spatial scales, for example
IRAS 15398−3359 (Bjerkeli et al. 2016) and VLA 1623−2417
(Murillo et al. 2018).
The morphology of C 2 H in IRAS 16293 is also studied in
Murillo et al. (2018), who find that it anti-correlates with that of
cyclic C 3 H 2 . While non-overlapping distributions of these two
chemically related species (Gerin et al. 2011) may seem surprising, there are also models and observations that indicate somewhat different physical conditions being needed for C 2 H and _c_ C 3 H 2 emission lines to occur (e.g., Cuadrado et al. 2015). Lacking an obvious connection to any of the other features connected
to source A, the physical, dynamical and chemical origin of the
C 2 H emission remains an open question.


_5.5._ _The relative evolutionary stage of sources A and B_


Based on the conclusions drawn in this paper and accompanying
PILS papers (J2018; Calcutt et al. 2018), it remains unclear if
sources A and B in the IRAS 16293 system are coeval. Their rotation axes are not aligned and a formation scenario from a giant
circumbinary disk is therefore unlikely (see Sect. 5.1). Sources A
and B differ in various aspects. Here we list those of relevance to
the matter of evolutionary stage. ( _i_ ) Source A is known to drive
at least two sets of bipolar outflows, and an additional one in the
past, whereas source B shows signs of infall, but exhibits no unambiguous proof of outflow activity (Pineda et al. 2012; Loinard
et al. 2013; Kristensen et al. 2013; Sect. 4.3 of this work). ( _ii_ )
J2018 find that the observed dust emission of the face-on disk of
source B can only be explained with a vertically extended disk or
disk-like model (i.e., one that has not yet undergone significant
settling), while the vertical structure of the disk of source A is not
constrained by their model. ( _iii_ ) Chemical differentiation is seen
between both sources particularly when analyzing CN-bearing
species. Such species have time dependent formation pathways
(Garrod et al. 2017) with some, such as vinyl cyanide (C 2 H 3 CN),
being formed later during the warm-up phase, as a result of the
destruction of ethyl cyanide (C 2 H 5 CN). Calcutt et al. (2018) find
vinyl cyanide to be at least nine times more abundant toward
the B source. However, these authors stress that although this
could indicate that source A is less evolved, it could also im

Article number, page 14 of 27



ply that the warm-up timescales for source A were very short,
limiting the amount of vinyl cyanide that could be formed. Collecting the above information elements, ( _i_ ) and ( _ii_ ) are consistent
with a view that source B is at an earlier stage of evolution than
source A, whereas ( _iii_ ) could be explained either way, appreciating that the temperature history of each source is not necessarily
monotonous and smooth. We thus pose that source B is at the
same evolutionary stage or less evolved than source A.
If there is a difference in evolutionary stage between sources
A and B, outflowing material from source A may have provided
a trigger for gravitational collapse to set in, some six hundred
au (projected) further down its own natal filament. Alternatively,
even if the initial collapse of source B started spontaneously, the
northwest outflow from source A could now be feeding gas and
dust originating in protostar A onto the disk of source B. Such
a scenario would add a new element to the investigation of the
different levels of various groups of chemical compounds found
in sources A and B (Bisschop et al. 2008; Calcutt et al. 2018).


**6.** **Summary and conclusions**


We have presented an analysis of the distribution and kinematics
of molecular gas in the protostellar binary system IRAS 16293 at
scales of 60–2000 au, using ALMA-PILS observational data and
three-dimensional line radiative transfer modeling. The selected
tracers are 0.87 mm dust continuum, line transitions CO 3–
C2, [34] CS 7–6, SiO 8–7, [17] O 3–2, H [13] CN [29] SiO 8–7, and C4–3, o-H 2 CO 5 21 H 4,5 –4 7/12,4 –3, H 5/22 [13], together high-CO 5 1,5 –4 1,4,
lighting different aspect of the morphology and dynamics of the
system. The main conclusions are summarized here.


1. The arc-shaped filament connecting the two protostellar
sources is clearly seen in dust continuum and C [17] O 3–2
emission. The kinematic pattern of C [17] O indicates that it
is quiescent, and consistent with the systemic velocities of
both sources. Other molecular tracers considered in this work
show a different spatial distribution, different kinematics, or
both (Sect. 3). The gas density of the bridge filament is likely
to be between 4×10 [4] cm [−][3] and ∼3×10 [7] cm [−][3] (Sect. 4.1).
A three-dimensional radiative transfer model qualitatively
matches the observed structure in dust and C [17] O, but not
those in H [13] CN and H 2 CO emission (Sect. 4.1).
2. Using a simplified description of the bridge filament, balancing thermal pressure and gravity, the bridge is inferred to be
stable against radial collapse. While a radially stable filament
is a prerequisite for it to fragment along the direction of its
axis, our interpretation of the observations of the bridge filament in its current state does not necessarily extend to earlier
times when it was likely more massive and thus less stable
(Sect. 4.2).
3. Given the physical nature of the bridge filament, we pose
that it is a remnant substructure of a filamentary circumbinary envelope that has undergone turbulent fragmentation
to form both protostellar sources (Sect. 5.1). The possibility that the bridge is (a remnant of) a circumbinary disk is
ruled out (Sect. 5.1).
4. The western side of the east-west outflow pair is clearly
traced in CO 3–2 in our observations, shown to be accelerating with distance from the launching source A. In addition,
it is seen to change from a collimated to a more wide-angle
structure at a projected distance of ∼350 au from source A,
possibly related to a density and pressure gradient of one
of the more or less cylindrical structures observed in this

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



system. The launching point of the outflow may be connected to a H 2 O maser shock spot ∼120 au west of source A
(Sect. 4.3).
5. Molecular lines of (isotopologues of) H 2 CO, HCN, SiO,
and CS trace outflow motions or the impact of outflows
onto more quiescent components. Dynamic structures near
source B might be due to nearly pole-on outflow from
source B itself, or impact of the northwest outflow from
source A onto dense material in source B (Sect. 4.3). In our
observations, we find no counterpart for the large scale (thousands of au) northeast-southwest outflow pair, indicating that
its launching engine must have been quenched a few hundred
years ago (Sect. 4.3).
6. A striking, previously unknown structure stretches straight
across source B at position angle ∼15 [◦] . It is only seen in
C 2 H and is kinematically flat, which rules out an origin in
outflow activity of source B (Sect. 5.4).
7. Combining evidence from this work and other studies, we
suggest that IRAS 16293B is not more evolved than its sister
source A (Sect. 5.5).
8. When used as a target to search for complex (organic)
molecules, as is often done, the physical and dynamical complexity of the IRAS 16293 protostellar binary system should
be taken into account. While searches for complex molecules
generally avoid the broad line regions near source A, even the
often-used positions on or near the blue ‘×’ mark in Fig. 2,
0.5 [′′] offset from source B, may exhibit spectral line shapes
with evidence of line-of-sight motions, which will manifest
differently in different molecules (Sect. 5.3).


By abandoning spherically symmetric model descriptions
of the envelopes of IRAS 16293 (e.g., Jørgensen et al. 2002;
Schöier et al. 2002; Crimier et al. 2010) and other protostellar systems, J2018 have taken a significant leap by developing a three-dimensional density model that includes an envelope hosting two individual energy sources, A and B, disklike structures around each, an interbinary bridge filament, and
a self-consistently derived temperature structure of the ensemble. While the radiative transfer scheme initially included dust
and CO isotopologues, it was further expanded in this work to
include two additional molecular species, H 2 CO and H [13] CN.
However, there are still steps to be made to make such a model
more realistic. For example, chemistry, freezing out and sublimation of molecules could be included, beyond the current implementation using gas-phase abundance jumps at certain threshold temperatures. The current model also lacks various dynamic
components such as the outflows, and the rotating, disk-like
structure around source A, which may need to be expanded to
larger radii than the 150 au used in J2018. In addition, future observational work could answer currently open questions about,
for example, (i) the evolutionary state of source B, (ii) the debated small-scale multiplicity of source A, or (iii) the connection
between the relatively young, small-scale outflow signatures (a
few hundred to a few thousands au) observed in interferometric observations such as in this paper, and the older outflows
seen at distances of tens of thousands of au from the protostellar sources. Considering the already known level of complexity
of the system, and the additional aspects yet to be uncovered,
adding all these elements to a (self-consistent) physical model
would further increase the number of degrees of freedom, which
may result in challenges when attempting to sensibly constrain
the model parameters.
The protostellar stages of this and other binary systems
should be studied further in order to understand how interactions with binary companions (through direct illumination or



even mass transfer through an outflow) affect the evolution of
the inner tens to hundreds of au of such systems. From this work
and the literature so far, it appears that IRAS 16293 represents a
particular stage in the evolution of binary star systems, a phase
which many other protostars may go through at one point in their
evolution. IRAS 16293 may not be particularly special; it is thus
rather appropriate to use this system to study chemical and physical conditions in a representative analog of the young Solar sys
tem.


_Acknowledgements._ We thank the anonymous referee for thoughtful comments
that helped improve the quality of this paper. MHDvdW, SKJ, JKJ, LEK and
HC acknowledge support from the European Research Council (ERC) under
the European Union’s Horizon 2020 research and innovation program (grant
agreement No. 646908) through ERC Consolidator Grant “S4F”, as well as
from a Lundbeck Foundation Group Leader Fellowship. PB acknowledges support from the Swedish Research Council through contract 637-2013-472. Research at the Centre for Star and Planet Formation is funded by the Danish
National Research Foundation. The postdoctoral grant of AC is funded by the
ERC Starting Grant 3DICE (grant agreement 336474). MND acknowledges the
financial support of the Center for Space and Habitability (CSH) Fellowship
and the IAU Gruber Foundation Fellowship. CF acknowledges support from
the Italian Ministry of Education, Universities and Research, through the grant
project SIR (RBSI14ZRHR). This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2013.1.00278.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has made use of NASA’s
Astrophysics Data System Bibliographic Services. This research has made use
of APLpy, an open-source plotting package for Python (Robitaille & Bressert
2012); Astropy, a community-developed core Python package for Astronomy
(Astropy Collaboration 2013), the matplotlib plotting library (Hunter 2007), and
the CASA data processing package (McMullin et al. 2007).


**References**


Adams, F. C., Ruden, S. P., & Shu, F. H. 1989, ApJ, 347, 959
Aikawa, Y., Umebayashi, T., Nakano, T., & Miyama, S. M. 1997, ApJ, 486, L51
Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, Protostars and Planets V, 245
Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558,
A33
Baryshev, A. M., Hesper, R., Mena, F. P., et al. 2015, A&A, 577, A129
Bisschop, S. E., Jørgensen, J. K., Bourke, T. L., Bottinelli, S., & Van Dishoeck,
E. F. 2008, A&A, 488, 959
Bjerkeli, P., Jørgensen, J. K., & Brinch, C. 2016, A&A, 587, A145
Bonnell, I. A. & Bate, M. R. 1994, MNRAS, 269
Bottinelli, S., Ceccarelli, C., Neri, R., et al. 2004, ApJ, 617, L69
Bourke, T. L., Myers, P. C., Evans, Neal J., I., et al. 2006, ApJ, 649, L37
Brinch, C. & Hogerheijde, M. R. 2010, A&A, 523, A25
Brinch, C., Jørgensen, J. K., Hogerheijde, M. R., Nelson, R. P., & Gressel, O.
2016, ApJ, 830, L16
Calcutt, H., Jørgensen, J. K., Müller, H. S. P., et al. 2018, A&A, 616, A90
Caselli, P., Hartquist, T. W., & Havnes, O. 1997, A&A, 322, 296
Caux, E., Kahane, C., Castets, A., et al. 2011, A&A, 532, A23
Cazzoli, G. & Puzzarini, C. 2005, Journal of Molecular Spectroscopy, 233, 280
Ceccarelli, C., Castets, A., Caux, E., et al. 2000, A&A, 355, 1129
Ceccarelli, C., Loinard, L., Castets, A., et al. 2001, A&A, 372, 998
Chandler, C. J., Brogan, C. L., Shirley, Y. L., & Loinard, L. 2005, ApJ, 632, 371
Chen, X., Arce, H. G., Zhang, Q., et al. 2013, ApJ, 768, 110
Cornet, R. A. & Winnewisser, G. 1980, Journal of Molecular Spectroscopy, 80,
438
Coutens, A., Jørgensen, J. K., Van der Wiel, M. H. D., et al. 2016, A&A, 590, L6
Coutens, A., Willis, E. R., Garrod, R. T., et al. 2018, A&A, 612, A107
Crimier, N., Ceccarelli, C., Maret, S., et al. 2010, A&A, 519, A65
Cuadrado, S., Goicoechea, J. R., Pilleri, P., et al. 2015, A&A, 575, A82
Dayou, F. & Balança, C. 2006, A&A, 459, 297
Drozdovskaya, M. N., Van Dishoeck, E. F., Jørgensen, J. K., et al. 2018,
MNRAS, 476, 4949
Drozdovskaya, M. N., Walsh, C., Visser, R., Harsono, D., & Van Dishoeck, E. F.
2015, MNRAS, 451, 3836
Duchêne, G. & Kraus, A. 2013, ARA&A, 51, 269
Dumouchel, F., Faure, A., & Lique, F. 2010, MNRAS, 406, 2488
Dutrey, A., Di Folco, E., Beck, T., & Guilloteau, S. 2016, A&A Rev., 24, 5
Dutrey, A., Di Folco, E., Guilloteau, S., et al. 2014, Nature, 514, 600


Article number, page 15 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



Dzib, S. A., Ortiz-León, G. N., Hernández-Gómez, A., et al. 2018, A&A, 614,
A20
Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, J.
Mol. Spectrosc., 327, 95
Favre, C., Jørgensen, J. K., Field, D., et al. 2014, ApJ, 790, 55
Fayolle, E. C., Öberg, K. I., Jørgensen, J. K., et al. 2017, Nature Astronomy, 1,
703
Fernández-López, M., Zapata, L. A., & Gabbasov, R. 2017, ApJ, 845, 10
Flower, D. R., Pineau des Forets, G., Field, D., & May, P. W. 1996, MNRAS,
280, 447
Garrod, R. T., Belloche, A., Müller, H. S. P., & Menten, K. M. 2017, A&A, 601,
A48
Gerin, M., Ka´zmierczak, M., Jastrzebska, M., et al. 2011, A&A, 525, A116
Girart, J. M., Estalella, R., Palau, A., Torrelles, J. M., & Rao, R. 2014, ApJ, 780,
L11
Gottlieb, C. A., Myers, P. C., & Thaddeus, P. 2003, ApJ, 588, 655
Gusdorf, A., Cabrit, S., Flower, D. R., & Pineau Des Forêts, G. 2008a, A&A,
482, 809
Gusdorf, A., Pineau Des Forêts, G., Cabrit, S., & Flower, D. R. 2008b, A&A,
490, 695
Guzmán, V., Pety, J., Goicoechea, J. R., Gerin, M., & Roueff, E. 2011, A&A,
534, A49
Herbst, E. & Van Dishoeck, E. F. 2009, ARA&A, 47, 427
Hunter, J. D. 2007, Computing In Science & Engineering, 9, 90
Inutsuka, S.-I. & Miyama, S. M. 1992, ApJ, 388, 392
Inutsuka, S.-i. & Miyama, S. M. 1997, ApJ, 480, 681
Jacobsen, S. K., Jørgensen, J. K., Van der Wiel, M. H. D., et al. 2018, A&A, 612,
A72 [J2018]
Jørgensen, J. K., Bourke, T. L., Nguyen Luong, Q., & Takakuwa, S. 2011, A&A,
534, A100
Jørgensen, J. K., Favre, C., Bisschop, S. E., et al. 2012, ApJ, 757, L4
Jørgensen, J. K., Schöier, F. L., & Van Dishoeck, E. F. 2002, A&A, 389, 908
Jørgensen, J. K., Van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595,
A117
Klapper, G., Surin, L., Lewen, F., et al. 2003, ApJ, 582, 262
Kristensen, L. E., Klaassen, P. D., Mottram, J. C., Schmalzl, M., & Hogerheijde,
M. R. 2013, A&A, 549, L6
Lee, J.-E., Lee, S., Dunham, M. M., et al. 2017, Nature Astronomy, 1, 0172
Lee, K. I., Dunham, M. M., Myers, P. C., et al. 2016, ApJ, 820, L2
Ligterink, N. F. W., Coutens, A., Kofman, V., et al. 2017, MNRAS, 469, 2219
Lique, F., Spielfiedel, A., & Cernicharo, J. 2006, A&A, 451, 1125
Loinard, L., Chandler, C. J., Rodríguez, L. F., et al. 2007, ApJ, 670, 1353
Loinard, L., Torres, R. M., Mioduszewski, A. J., & Rodríguez, L. F. 2008, ApJ,
675, L29
Loinard, L., Zapata, L. A., Rodríguez, L. F., et al. 2013, MNRAS, 430, L10
Looney, L. W., Mundy, L. G., & Welch, W. J. 2000, ApJ, 529, 477
Lykke, J. M., Coutens, A., Jørgensen, J. K., et al. 2017, A&A, 597, A53
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical
Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Menten, K. M., Serabyn, E., Guesten, R., & Wilson, T. L. 1987, A&A, 177, L57
Mizuno, A., Fukui, Y., Iwata, T., Nozawa, S., & Takano, T. 1990, ApJ, 356, 184
Moriarty-Schieven, G. H. & Snell, R. L. 1988, ApJ, 332, 364
Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of
Molecular Structure, 742, 215
Müller, H. S. P., Spezzano, S., Bizzocchi, L., et al. 2013, Journal of Physical
Chemistry A, 117
Murillo, N. M., Van Dishoeck, E. F., Van der Wiel, M. H. D., et al. 2018, A&A,
617, A120
Noble, J. A., Theule, P., Borget, F., et al. 2013, MNRAS, 428, 3262
Offner, S. S. R., Kratter, K. M., Matzner, C. D., Krumholz, M. R., & Klein, R. I.
2010, ApJ, 725, 1485
Ortiz-León, G. N., Loinard, L., Kounkel, M. A., et al. 2017, ApJ, 834, 141
Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943
Ostriker, J. 1964, ApJ, 140, 1056
Oya, Y., Moriwaki, K., Onishi, S., et al. 2018, ApJ, 854, 96
Oya, Y., Sakai, N., López-Sepulcre, A., et al. 2016, ApJ, 824, 88
Padovani, M., Walmsley, C. M., Tafalla, M., Galli, D., & Müller, H. S. P. 2009,
A&A, 505, 1199
Pech, G., Loinard, L., Chandler, C. J., et al. 2010, ApJ, 712, 1403
Persson, M. V., Jørgensen, J. K., Müller, H. S. P., et al. 2018, A&A, 610, A54
Pineda, J. E., Maury, A. J., Fuller, G. A., et al. 2012, A&A, 544, L7
Pineda, J. E., Offner, S. S. R., Parker, R. J., et al. 2015, Nature, 518, 213
Quénard, D., Bottinelli, S., Caux, E., & Wakelam, V. 2018, MNRAS, 477, 5312
Rao, R., Girart, J. M., Lai, S.-P., & Marrone, D. P. 2014, ApJ, 780, L6
Rao, R., Girart, J. M., Marrone, D. P., Lai, S.-P., & Schnee, S. 2009, ApJ, 707,
921
Robitaille, T. & Bressert, E. 2012, APLpy: Astronomical Plotting Library in
Python, Astrophysics Source Code Library


Article number, page 16 of 27



Rodgers, S. D. & Charnley, S. B. 2003, ApJ, 585, 355
Sadavoy, S. I., Myers, P. C., Stephens, I. W., et al. 2018, ApJ, 869, 115
Schöier, F. L., Jørgensen, J. K., Van Dishoeck, E. F., & Blake, G. A. 2002, A&A,
390, 1001
Schöier, F. L., Van der Tak, F. F. S., Van Dishoeck, E. F., & Black, J. H. 2005,
A&A, 432, 369
Spielfiedel, A., Feautrier, N., Najar, F., et al. 2012, MNRAS, 421, 1891
Stark, R., Sandell, G., Beck, S. C., et al. 2004, ApJ, 608, 341
Suutarinen, A. N., Kristensen, L. E., Mottram, J. C., Fraser, H. J., & Van
Dishoeck, E. F. 2014, MNRAS, 440, 1844
Takakuwa, S., Ohashi, N., Bourke, T. L., et al. 2007, ApJ, 662, 431
Tobin, J. J., Kratter, K. M., Persson, M. V., et al. 2016a, Nature, 538, 483
Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016b, ApJ, 818, 73
Tokuda, K., Onishi, T., Saigo, K., et al. 2014, ApJ, 789, L4
Van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & Van Dishoeck,
E. F. 2007, A&A, 468, 627
Van der Wiel, M. H. D., Van der Tak, F. F. S., Ossenkopf, V., et al. 2009, A&A,
498, 161
Wiesenfeld, L. & Faure, A. 2013, MNRAS, 432, 2573
Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143
Winnewisser, G., Belov, S. P., Klaus, T., & Schieder, R. 1997, Journal of Molecular Spectroscopy, 184, 468
Wootten, A. 1989, ApJ, 337, 858
Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062
Yeh, S. C. C., Hirano, N., Bourke, T. L., et al. 2008, ApJ, 675, 454
Zhou, S. 1995, ApJ, 442, 685

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



**Appendix A:** **Line contamination**


Since the PILS data set, covering 329.15–362.90 GHz, has a line
density of about one line every 3 MHz (Jørgensen et al. 2016),
it is important to consider the effect of contamination of other
species contributing to the observed signal of a selected tracer.
The potential contributions from species and transitions other
than those listed in Table 2 are visualized in the spectral profiles
in Figs. A.1–A.8 below.
In general, while various contaminating contributions are
identified in the spectrum extracted toward the position one beam
west-southwest of source B, this signal is exclusively due to relatively complex molecular species, which are known to have
spatial distributions confined to the regions in the central 1–2 [′′]
around sources A and/or B (e.g., Baryshev et al. 2015; Lykke
et al. 2017; Ligterink et al. 2017), domains explicitly not under
study in the current work. The only exception is an SO 2 transition near H [13] CN 4–3 profiles. This and other cases that require
a more detailed description are addressed in the following paragraphs.


C [17] O. The hyperfine splitting for the C [17] O 3–2 rotational transition is only 0.5 MHz. We therefore indicate the rest frequency
of this transition with a single vertical dashed line in Fig. A.1,
derived from the mean frequency of the contributing hyperfine
components with Einstein _A_ coefficients >10 [−][6] s [−][1] .


H [13] CN 4–3. Of the three separated hyperfine components of
this rotational transition (Cazzoli & Puzzarini 2005), the central one (∆ _F_ =1) is taken as the reference for the velocity axis.
There is potential contamination of the H [13] CN 4–3 signal by the
SO 2 13 2,12 –12 1,11 transition (345.3385377 GHz), with a modest
upper level energy of 92 K, at only 1.2 MHz from the rest frequency of H [13] CN. At the position 0.5 [′′] southwest of source B
(‘×’ mark in Fig. 2), preferred for identifying spectral signa

frequency (GHz)





1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25


_−_ 0.50



frequency (GHz)


|H13CN4 3<br>–|Col2|core B off<br>bridge|
|---|---|---|
|||SO2<br>C2H5OH|





1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25


_−_ 0.50




|C17O3 2<br>–|Col2|core B off<br>bridge|Col4|
|---|---|---|---|
|||CH2DOH<br>CH3CHO|CH2DOH<br>CH3CHO|



_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig.** **A.1.** Spectral profiles of C [17] O 3–2 at two spatial positions: one
beam west-southwest of source B (blue ‘×’ mark in Fig. 2) and within
the bridge filament (magenta ‘+’ mark in the same figure). The frequency of the species of interest is marked by the blue, vertical dashed
line; other lines identified in the frequency range are marked with
dotted, dash-dotted, or solid lines. All rest frequencies are shifted by
+2.7 km s [−][1] to account for the systemic velocity of source B. The section of the velocity axis with white background denotes the maximum
range over which intensities are integrated.



_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig.** **A.2.** Same as Fig. A.1, but for H [13] CN. Its _J_ =4–3 transition has
three hyperfine components marked with the black arrows, in order
of increasing frequency (right to left): _F_ =4–4, several transitions with
∆ _F_ =1, and _F_ =3–3.


tures of rare, complex molecules in previous PILS papers (e.g.,
Coutens et al. 2016; Lykke et al. 2017; Ligterink et al. 2017),
lines are narrow and spectrally resolved, and we do not see evidence of SO 2 contribution to the H [13] CN total intensity beyond a
few percent. At other positions, for example in the western outflow from source A or close to source A itself, contamination
cannot be ruled out.


29 SiO 8–7. The signal of the [29] SiO 8–7 itself is weak and
somewhat blueshifted (∼1 km s [−][1] ) toward the position 0.5 [′′] offset from source B (Fig. A.7). We are confident, however, that
the signal ascribed to [29] SiO in the channel maps (Fig. B.7) and
velocity map (Fig. 2), because the morphology of the redshifted
29 SiO channel maps follows that of the brightest patches of SiO
(Fig. B.6) and the spectral line shape toward those positions (for
example, the extension southeast of source A) is single-peaked.


C 2 H 4 7/2 –3 5/2 . For the C 2 H _N_ _J_ =4 7/2 –3 5/2 transition, there are
two hyperfine structure components ( _F_ =4–3 and 3–2), separated
by 1.4 MHz. Such a small separation means that they lie within
1.2 km s [−][1] of one another in the spectral dimension, but are resolved in our 0.2 km s [−][1] spectral resolution data cubes, which
complicates the interpretation of its velocity structure. In this
work, the reference frequency (zero-point for _V_ lsr ) is taken as
the mid-point between the two hyperfine structure lines, _F_ =4–
3 at 349.39928 GHz and _F_ =3–2 at 349.40067 GHz (Padovani
et al. 2009). In addition, most of the redshifted (>+5 km s [−][1] )
emission in the velocity map of C 2 H (Fig. 2, Fig. B.8) is due to
the bright CH 3 CN 19 3 –18 3 transition at 349.39329 GHz. For this
reason, we have adopted a narrower integration for C 2 H than for
the other lines (cf. Fig. A.8 vs. Fig. A.1–A.7). In positions near
sources A and B, the CH 3 CN line also contaminates channels
closer to the systemic velocity of C 2 H.


**Appendix B:** **Channel map figures**


Channel maps of the molecular lines listed in Table 2 are shown
in Fig. B.1–B.8.


Article number, page 17 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv


frequency (GHz)







1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25


_−_ 0.50





1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25


_−_ 0.50








|347.35|347.32 347.33 347.34 frequency (GHz)|
|---|---|
||SiO 8–7|
|||



_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig. A.3.** Same as Fig. A.1, but for H 2 CO.


frequency (GHz)



_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig. A.6.** Same as Fig. A.1, but for SiO.


frequency (GHz)







1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25









_−_ 0.50


_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig. A.4.** Same as Fig. A.1, but for H 2 [13] CO.


frequency (GHz)


|29SiO8 7<br>–|Col2|
|---|---|
|||



_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig. A.7.** Same as Fig. A.1, but for [29] SiO.


frequency (GHz)



1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25


_−_ 0.50









1.25









1.00


0.75


0.50


0.25


0.00


_−_ 0.25


_−_ 0.50


_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig. A.5.** Same as Fig. A.1, but for C [34] S.


Article number, page 18 of 27



1.25


1.00


0.75


0.50


0.25


0.00


_−_ 0.25



_−_ 0.50

|C<br>2|H4 3<br>7/2– 5/2|
|---|---|
|||



_−_ 15 _−_ 10 _−_ 5 0 5 10 15 20
_V_ lsr (km/s)


**Fig. A.8.** Same as Fig. A.1, but for C 2 H.

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars


C [17] O 3–2



3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03




|28′28′′<br>+0 .2 km s−1 +0 .5 km s−1 +0 .7 km s−1 +0 .9 km s−1 +1 .1 km s−1<br>32′′<br>36′′<br>40′′<br>28′28′′<br>+1 .3 km s−1 +1 .5 km s−1 +1 .8 km s−1 +2 .0 km s−1 +2 .2 km s−1<br>32′′<br>36′′<br>40′′<br>28′28′′<br>+2 .4 km s−1 +2 .6 km s−1 +2 .8 km s−1 +3 .1 km s−1 +3 .3 km s−1<br>32′′<br>36′′<br>40′′<br>28′28′′<br>+3 .5 km s−1 +3 .7 km s−1 +3 .9 km s−1 +4 .1 km s−1 +4 .4 km s−1<br>32′′<br>36′′<br>40′′<br>28′28′′<br>+4 .6 km s−1 +4 .8 km s−1 +5 .0 km s−1 +5 .2 km s−1 +5 .4 km s−1<br>32′′<br>36′′<br>40′′<br>28′28′′<br>+5 .7 km s−1 +5 .9 km s−1 +6 .1 km s−1 +6 .3 km s−1 [−4 .0, +1 .9]<br>[+2 .0 +4 .0]<br>,<br>32′′<br>36′′ A<br>40′′<br>232s 228s m224s 232s 228s m224s 232s 228s m224s 232s 228s m224s 232s 228s<br>. . . . . . . . . . . . . .|+0 .7 km s−1 +0 .9 km s|−1 +1 .1 km s−1|
|---|---|---|
|40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>22.8_s_<br>23.2_s_<br>A<br>+0.2 km s_−_1<br>+0.5 km s_−_1<br>+0.7 km s_−_1<br>+0.9 km s_−_1<br>+1.1 km s_−_1<br>+1.3 km s_−_1<br>+1.5 km s_−_1<br>+1.8 km s_−_1<br>+2.0 km s_−_1<br>+2.2 km s_−_1<br>+2.4 km s_−_1<br>+2.6 km s_−_1<br>+2.8 km s_−_1<br>+3.1 km s_−_1<br>+3.3 km s_−_1<br>+3.5 km s_−_1<br>+3.7 km s_−_1<br>+3.9 km s_−_1<br>+4.1 km s_−_1<br>+4.4 km s_−_1<br>+4.6 km s_−_1<br>+4.8 km s_−_1<br>+5.0 km s_−_1<br>+5.2 km s_−_1<br>+5.4 km s_−_1<br>+5.7 km s_−_1<br>+5.9 km s_−_1<br>+6.1 km s_−_1<br>+6.3 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|+1.8 km s_−_1<br>+2.0 km s|_−_1<br>+2.2 km s_−_1|
|40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>22.8_s_<br>23.2_s_<br>A<br>+0.2 km s_−_1<br>+0.5 km s_−_1<br>+0.7 km s_−_1<br>+0.9 km s_−_1<br>+1.1 km s_−_1<br>+1.3 km s_−_1<br>+1.5 km s_−_1<br>+1.8 km s_−_1<br>+2.0 km s_−_1<br>+2.2 km s_−_1<br>+2.4 km s_−_1<br>+2.6 km s_−_1<br>+2.8 km s_−_1<br>+3.1 km s_−_1<br>+3.3 km s_−_1<br>+3.5 km s_−_1<br>+3.7 km s_−_1<br>+3.9 km s_−_1<br>+4.1 km s_−_1<br>+4.4 km s_−_1<br>+4.6 km s_−_1<br>+4.8 km s_−_1<br>+5.0 km s_−_1<br>+5.2 km s_−_1<br>+5.4 km s_−_1<br>+5.7 km s_−_1<br>+5.9 km s_−_1<br>+6.1 km s_−_1<br>+6.3 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|+2.8 km s_−_1<br>+3.1 km s|_−_1<br>+3.3 km s_−_1|
|40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>22.8_s_<br>23.2_s_<br>A<br>+0.2 km s_−_1<br>+0.5 km s_−_1<br>+0.7 km s_−_1<br>+0.9 km s_−_1<br>+1.1 km s_−_1<br>+1.3 km s_−_1<br>+1.5 km s_−_1<br>+1.8 km s_−_1<br>+2.0 km s_−_1<br>+2.2 km s_−_1<br>+2.4 km s_−_1<br>+2.6 km s_−_1<br>+2.8 km s_−_1<br>+3.1 km s_−_1<br>+3.3 km s_−_1<br>+3.5 km s_−_1<br>+3.7 km s_−_1<br>+3.9 km s_−_1<br>+4.1 km s_−_1<br>+4.4 km s_−_1<br>+4.6 km s_−_1<br>+4.8 km s_−_1<br>+5.0 km s_−_1<br>+5.2 km s_−_1<br>+5.4 km s_−_1<br>+5.7 km s_−_1<br>+5.9 km s_−_1<br>+6.1 km s_−_1<br>+6.3 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|+3.9 km s_−_1<br>+4.1 km s|_−_1<br>+4.4 km s_−_1|
|40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>22.8_s_<br>23.2_s_<br>A<br>+0.2 km s_−_1<br>+0.5 km s_−_1<br>+0.7 km s_−_1<br>+0.9 km s_−_1<br>+1.1 km s_−_1<br>+1.3 km s_−_1<br>+1.5 km s_−_1<br>+1.8 km s_−_1<br>+2.0 km s_−_1<br>+2.2 km s_−_1<br>+2.4 km s_−_1<br>+2.6 km s_−_1<br>+2.8 km s_−_1<br>+3.1 km s_−_1<br>+3.3 km s_−_1<br>+3.5 km s_−_1<br>+3.7 km s_−_1<br>+3.9 km s_−_1<br>+4.1 km s_−_1<br>+4.4 km s_−_1<br>+4.6 km s_−_1<br>+4.8 km s_−_1<br>+5.0 km s_−_1<br>+5.2 km s_−_1<br>+5.4 km s_−_1<br>+5.7 km s_−_1<br>+5.9 km s_−_1<br>+6.1 km s_−_1<br>+6.3 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|+5.0 km s_−_1<br>+5.2 km s|_−_1<br>+5.4 km s_−_1|
|40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>40_′′_<br>36_′′_<br>32_′′_<br>28_′_28_′′_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>_m_22.4_s_<br>22.8_s_<br>23.2_s_<br>22.8_s_<br>23.2_s_<br>A<br>+0.2 km s_−_1<br>+0.5 km s_−_1<br>+0.7 km s_−_1<br>+0.9 km s_−_1<br>+1.1 km s_−_1<br>+1.3 km s_−_1<br>+1.5 km s_−_1<br>+1.8 km s_−_1<br>+2.0 km s_−_1<br>+2.2 km s_−_1<br>+2.4 km s_−_1<br>+2.6 km s_−_1<br>+2.8 km s_−_1<br>+3.1 km s_−_1<br>+3.3 km s_−_1<br>+3.5 km s_−_1<br>+3.7 km s_−_1<br>+3.9 km s_−_1<br>+4.1 km s_−_1<br>+4.4 km s_−_1<br>+4.6 km s_−_1<br>+4.8 km s_−_1<br>+5.0 km s_−_1<br>+5.2 km s_−_1<br>+5.4 km s_−_1<br>+5.7 km s_−_1<br>+5.9 km s_−_1<br>+6.1 km s_−_1<br>+6.3 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|+6.1 km s_−_1<br>+6.3 km s|A<br>_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.1.** C [17] O 3–2 channel maps with contours representing logarithmically spaced line intensity in each channel. The first positive contour (solid
blue, black, or red) is at 0.03 Jy beam [−][1], the first negative contour (lighter, dashed) is at −0.06 Jy beam [−][1], with every next contour level spaced by
a factor of two. The bottom right panel displays three integrated velocity ranges in colored contours: all ‘blue’ channels, [−4.0, +2.0⟩ km s [−][1] ; all
‘systemic velocity’ channels, [+2.0, +4.0] km s [−][1] ; and all ‘red’ channels, ⟨+4.0, +11.0] km s [−][1] . For each of these three, the first contour level is
at 0.2 Jy beam [−][1] km s [−][1] and levels increase by factors of two, and equivalently for negative contours displayed in dashed line format. Gray scale
in bottom right panel (logarithmic stretch from 0.002 to 2.0 Jy beam [−][1] ), color scale in all other panels (logarithmic stretch indicated in color bar):
0.87 mm continuum. Star symbols mark the continuum peak locations of protostars A and B (see Table 1).


Article number, page 19 of 27

3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03









_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv


|H13CN 4–3|Col2|
|---|---|
|+0.8 km s_−_1<br>+1.0 km s_−_1<br>+1.2 km s_−_1||
|+1.8 km s_−_1<br>+2.0 km s_−_1<br>+2.2 km s_−_1||
|+2.9 km s_−_1<br>+3.1 km s_−_1<br>+3.3 km s_−_1||
|+3.9 km s_−_1<br>+4.2 km s_−_1<br>+4.4 km s_−_1||
|+5.0 km s_−_1<br>+5.2 km s_−_1<br>+5.4 km s_−_1||
|A<br>+6.1 km s_−_1<br>+6.3 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|B<br>[+4.1, +11.0]|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.2.** H [13] CN 4–3 channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.03 (−0.06) Jy beam [−][1] ; first
contour levels in the bottom right integrated ranges panel: 0.2 Jy beam [−][1] km s [−][1] .


Article number, page 20 of 27

3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03





M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars


H 2 CO 5 1,5 -4 1,4









RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.3.** H 2 CO 5 1,5 –4 1,4 channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.12 (−0.24) Jy beam [−][1] ;
first contour levels in the bottom right integrated ranges panel: 0.2 Jy beam [−][1] km s [−][1] .


Article number, page 21 of 27

_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_



_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


|Col1|Col2|H2|213CO 51,5–41,4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+0.2 km s_−_1|+0.4 km s_−_1<br>+0.6 k|m s_−_1<br>+0.8 k|m s_−_1<br>+1.1 km s_−_|1|1||
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+1.3 km s_−_1||m s_−_1<br>+1.9 k|m s_−_1<br>+2.1 km s_−_|1|1||
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+1.3 km s_−_1|+1.5 km s_−_1|+1.5 km s_−_1|+1.5 km s_−_1|+1.5 km s_−_1|+1.5 km s_−_1|+1.5 km s_−_1|
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+2.3 km s_−_1||m s_−_1<br>+3.0 k|m s_−_1<br>+3.2 km s_−_|1|1||
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+2.3 km s_−_1|+2.6 km s_−_1|+2.6 km s_−_1|+2.6 km s_−_1|+2.6 km s_−_1|+2.6 km s_−_1|+2.6 km s_−_1|
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+3.4 km s_−_1||m s_−_1<br>+4.0 k|m s_−_1<br>+4.3 km s_−_|1|1||
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+3.4 km s_−_1|+3.6 km s_−_1|+3.6 km s_−_1|+3.6 km s_−_1|+3.6 km s_−_1|+3.6 km s_−_1|+3.6 km s_−_1|
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+4.5 km s_−_1||m s_−_1<br>+5.1 k|m s_−_1<br>+5.3 km s_−_|1|1||
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+4.5 km s_−_1|+4.7 km s_−_1|+4.7 km s_−_1|+4.7 km s_−_1|+4.7 km s_−_1|+4.7 km s_−_1|+4.7 km s_−_1|
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+5.5 km s_−_1||m s_−_1<br>+6.2 k|m s_−_1<br>[_−_4.0, +1.9<br>[+2.0, +4.0|A<br>B<br>]<br>[+4.1, +11.0]<br>]|||
|_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br>_′′_<br><br><br><br><br><br>|+5.5 km s_−_1|+5.8 km s_−_1|+5.8 km s_−_1|+5.8 km s_−_1|+5.8 km s_−_1|+5.8 km s_−_1|+5.8 km s_−_1|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.4.** H 2 [13] CO 5 1,5 –4 1,4 channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.03 (−0.06) Jy beam [−][1] ;
first contour levels in the bottom right integrated ranges panel: 0.1 Jy beam [−][1] km s [−][1] .


Article number, page 22 of 27

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


|C34|4S 7–6|Col3|Col4|
|---|---|---|---|
|+0.3 km s_−_1<br>+0.5 km s_−_1|+0.7 km s|_−_1<br>+1.0 km s_−_1||
|+1.4 km s_−_1<br>+1.6 km s_−_1|+1.8 km s|_−_1<br>+2.0 km s_−_1||
|+2.5 km s_−_1<br>+2.7 km s_−_1|+2.9 km s|_−_1<br>+3.1 km s_−_1||
|+3.6 km s_−_1<br>+3.8 km s_−_1|+4.0 km s|_−_1<br>+4.2 km s_−_1||
|+4.6 km s_−_1<br>+4.9 km s_−_1|+5.1 km s|_−_1<br>+5.3 km s_−_1||
|+5.7 km s_−_1<br>+5.9 km s_−_1|+6.2 km s|A<br>B<br>_−_1<br>[_−_4.0, +1.9]<br>[<br>[+2.0, +4.0]|A<br>B<br>_−_1<br>[_−_4.0, +1.9]<br>[<br>[+2.0, +4.0]|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.5.** C [34] S channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.03 (−0.06) Jy beam [−][1] ; first contour
levels in the bottom right integrated ranges panel: 0.2 Jy beam [−][1] km s [−][1] .


Article number, page 23 of 27

3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03







_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv


|SiO 8–7|Col2|
|---|---|
|+0.4 km s_−_1<br>+0.7 km s_−_1|+0.9 km s_−_1<br>+1.1 km s_−_1|
|+1.5 km s_−_1<br>+1.7 km s_−_1|+1.9 km s_−_1<br>+2.1 km s_−_1|
|+2.5 km s_−_1<br>+2.8 km s_−_1|+3.0 km s_−_1<br>+3.2 km s_−_1|
|+3.6 km s_−_1<br>+3.8 km s_−_1|+4.0 km s_−_1<br>+4.2 km s_−_1|
|+4.7 km s_−_1<br>+4.9 km s_−_1|+5.1 km s_−_1<br>+5.3 km s_−_1|
|+5.7 km s_−_1<br>+5.9 km s_−_1|A<br>B<br>+6.1 km s_−_1<br>[_−_4.0, +1.9]<br>[+4.1, +11.0]<br>[+2.0, +4.0]|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.6.** SiO (main isotopologue) 8–7 channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.03 (−0.06)
Jy beam [−][1] ; first contour levels in the bottom right integrated ranges panel: 0.2 Jy beam [−][1] km s [−][1] .


Article number, page 24 of 27

_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_


_−_ 24 _[◦]_ 28 _[′]_ 28 _[′′]_


32 _[′′]_


36 _[′′]_


40 _[′′]_



M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars



3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


|Col1|Col2|29SiO 8–7|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|+0.3 km s_−_1|+0.5 km s_−_1|+0.7 km s_−_1|+0.9 km s_−_1|+1.2 km s_−_1|+1.2 km s_−_1||
|+1.4 km s_−_1|+1.6 km s_−_1|+1.8 km s_−_1|+2.0 km s_−_1|+2.2 km s_−_1|+2.2 km s_−_1||
|+2.4 km s_−_1|+2.6 km s_−_1|+2.9 km s_−_1|+3.1 km s_−_1|+3.3 km s_−_1|+3.3 km s_−_1||
|+3.5 km s_−_1|+3.7 km s_−_1|+3.9 km s_−_1|+4.1 km s_−_1|+4.4 km s_−_1|+4.4 km s_−_1||
|+4.6 km s_−_1|+4.8 km s_−_1|+5.0 km s_−_1|+5.2 km s_−_1|+5.4 km s_−_1|+5.4 km s_−_1||
|+5.6 km s_−_1|+5.8 km s_−_1|+6.1 km s_−_1|+6.3 km s_−_1|A<br>B<br>[_−_4.0, +1.9]<br>[+4.1, +11.0]<br>[+2.0, +4.0]|||



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.7.** 29 SiO 8–7 channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.02 (−0.04) Jy beam −1 ; first
contour levels in the bottom right integrated ranges panel: 0.07 Jy beam [−][1] km s [−][1] .


Article number, page 25 of 27

_A&A proofs:_ manuscript no. PILS_bridgekinematics_for-arxiv



3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03


3.00


1.00


0.30


0.10


0.03




|Col1|Col2|C2H 47/2–35/2|Col4|Col5|Col6|
|---|---|---|---|---|---|
|+0.3 km s_−_1|+0.5 km s_−_1|+0.7 km s_−_1|+0.9 km s_−_1<br>+1.1 km s_−_1|||
|+1.3 km s_−_1|+1.5 km s_−_1|+1.8 km s_−_1|+2.0 km s_−_1<br>+2.2 km s_−_1|||
|+2.4 km s_−_1|+2.6 km s_−_1|+2.8 km s_−_1|+3.0 km s_−_1<br>+3.2 km s_−_1|||
|+3.4 km s_−_1|+3.6 km s_−_1|+3.9 km s_−_1|+4.1 km s_−_1<br>+4.3 km s_−_1|||
|+4.5 km s_−_1|+4.7 km s_−_1|+4.9 km s_−_1|+5.1 km s_−_1<br>+5.3 km s_−_1|||
|+5.5 km s_−_1|+5.7 km s_−_1|+5.9 km s_−_1|A<br>+6.2 km s_−_1<br>[_−_4.0, +1.9]<br>[+2.0, +4.0]|B<br>[+4.1, +11.0]|B<br>[+4.1, +11.0]|



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



RA (J2000)



**Fig. B.8.** C 2 H channel maps. As Fig. B.1. First positive (negative) contour level in individual channel maps: 0.03 (−0.06) Jy beam [−][1] ; first contour
levels in the bottom right integrated ranges panel: 0.07 Jy beam [−][1] km s [−][1] . Note that emission in channels above +5 km s [−][1] is due to CH 3 CN
19(3)–18(3) and not C 2 H.


Article number, page 26 of 27

M. H. D. van der Wiel et al.: PILS: Gas dynamics in IRAS 16293 and the connection between its two protostars


**Appendix C:** **Model maps without freeze-out**


In Fig. C.1 we show, for completeness, the result of the radiative
transfer model (Sect. 4.1) with freeze-out effects discarded for
o-H 2 CO and H [13] CN. The dashed contours, representing negative intensity values, indicate that optical depth of H [13] CN 4–3 is
high when all H [13] CN of all model components is kept in the gas
phase, as discussed in Sect. 4.1. These ‘no freeze-out’ calculations are included in this work with the aim of disentangling effects of excitation and those of freeze-out and sublimation. They
are explicitly not meant to present an alternative physical scenario; freeze-out of molecules onto dust grain surfaces should
always be taken into account in conditions representative of starforming regions.







6.4


3.2


1.6


0.8


0.4


0.2



0.1


**Fig. C.1.** Radiative transfer model maps (see Sect. 4.1) of o-H 2 CO 5 1,5 –
4 1,4 (left) and H [13] CN 4–3 (right) with freeze-out effects ignored. These
maps are counterparts of the more physically correct ones where freezeout is implemented, in the middle right and bottom right panels of Fig. 6.
Color scales and contours are identical to those used in Fig. 6, with the
exception that negative intensity contours (dashed) are included in this
figure.



Article number, page 27 of 27


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: archival_reuse",
  "failed_quote": "This paper is based on observations from the ALMA band 7 segment of the Protostellar Interferometric Line Survey (PILS) targeting IRAS 16293."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Intensity-weighted mean velocity per pixel with disks masked, threshold 40 mJy/beam",
  "failed_quote": "calculating an intensity weighted mean velocity for each pixel, excluding all flux density values below 40 mJy beam [−][1]"
 }
]
```
