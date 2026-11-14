# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.531.4045C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–15 (2023) Preprint 3 June 2024 Compiled using MNRAS L [A] TEX style file v3.0

## **WISDOM Project – XXI. Giant molecular clouds in the central** **region of the barred spiral galaxy NGC 613: a steep size – linewidth** **relation**

### Woorak Choi, [1] [★] Martin Bureau, [2] † Lĳie Liu, [3] [,] [4] Michele Cappellari, [2] Timothy A. Davis, [5] Jindra Gensior, [6] Fu-Heng Liang, [2] Anan Lu, [7] Sanghyuk Moon, [8] Ilaria Ruffa, [5] [,] [9]


### Thomas G. Williams [2] and Aeree Chung [1] ‡

1 _Department of Astronomy, Yonsei University, 50 Yonsei-ro, Seodaemun-gu, Seoul 03722, Republic of Korea_
2 _Sub-department of Astrophysics, Department of Physics, University of Oxford, Keble Road, Oxford OX1 3RH, UK_
3 _Cosmic Dawn Center (DAWN), Technical University of Denmark, DK2800 Kgs. Lyngby, Denmark_
4 _DTU-Space, Technical University of Denmark, Elektrovej 327, DK2800 Kgs. Lyngby, Denmark_
5 _Cardiff Hub for Astrophysics Research and Technology, School of Physics and Astronomy, Cardiff University, Queens Buildings, Cardiff, CF24 3AA, UK_
6 _Department of Astrophysics, University of Zurich, Winterthurerstrasse 190, 8057 Zürich, Switzerland_
7 _McGill Space Institute and Department of Physics, McGill University, 3600 University Street, Montreal QC, H3A 2T8, Canada_
8 _Department of Astrophysical Sciences, Princeton University, Princeton, NJ 08544, USA_
9 _INAF - Istituto di Radioastronomia, via P.Gobetti 101, 40129 Bologna, Italy_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
NGC 613 is a nearby barred spiral galaxy with a nuclear ring. Exploiting high spatial resolution
(≈ 20 pc) Atacama Large Millimeter/sub-millimeter Array [12] CO(1-0) observations, we study
the giant molecular clouds (GMCs) in the nuclear ring and its vicinity, identifying 158 spatiallyand spectrally-resolved GMCs. The GMC sizes ( _𝑅_ c ) are comparable to those of the clouds in
the Milky Way (MW) disc, but their gas masses, observed linewidths ( _𝜎_ obs _,_ los ) and gas mass
surface densities are larger. The GMC size – linewidth relation ( _𝜎_ obs _,_ los ∝ _𝑅_ c [0] _[.]_ [77] ) is steeper than
that of the clouds of the MW disc and centre, and the GMCs are on average only marginally
gravitationally bound (with a mean virial parameter ⟨ _𝛼_ obs _,_ vir ⟩≈ 1 _._ 7). We discuss the possible
origins of the steep size – linewidth relation and enhanced observed linewidths of the clouds
and suggest that a combination of mechanisms such as stellar feedback, gas accretion and
cloud-cloud collisions, as well as the gas inflows driven by the large-scale bar, may play a role.


**Key** **words:** galaxies: spiral and bar – galaxies: individual: NGC 613 – galaxies: nuclei –
galaxies: ISM – radio lines: ISM – ISM: clouds



**1** **INTRODUCTION**


As giant molecular clouds (GMCs) are the gas reservoirs where
most star formation takes place, understanding their life cycle and
characteristics is essential to comprehend the formation and evolution of galaxies. Early studies of GMCs were limited to Milky
Way (MW) and Local Group galaxies such as the Large Magellanic Cloud (LMC; e.g. Fukui et al. 2008), Small Magellanic Cloud
(SMC; e.g. Muller et al. 2010), M 31 (e.g. Rosolowsky 2007) and
M 33 (e.g. Rosolowsky et al. 2003, 2007). These studies revealed
that the GMCs of these galaxies have similar properties and size
– linewidth relations, with typical sizes of 10 – 100 pc, typical


_★_ E-mail: woorak.c@gmail.com

- E-mail: martin.bureau@physics.ox.ac.uk

- E-mail: achung@yonsei.ac.kr


© 2023 The Authors



masses of 10 [4] – 10 [7] M ⊙ and typical velocity dispersions of 1 –
10 km s [−][1] (e.g. Larson 1981; Bolatto et al. 2008).


With improvements of the resolution and sensitivity of molecular line observations, GMCs are now studied in extragalactic objects,
revealing deviations from the properties of Local Group GMCs (e.g.
Bolatto et al. 2008; Rosolowsky et al. 2021). For example, the characteristics of the GMCs of some late-type galaxies (LTGs) vary with
galactic environment and do not universally conform to the usual
scaling relations of MW clouds (e.g. M 51, Hughes et al. 2013,
Colombo et al. 2014; NGC 253, Leroy et al. 2015). The GMCs
of early-type galaxies (ETGs) also have either no or different size
– linewidth relations and are brighter, denser and have higher velocity dispersions than GMCs in the MW disc (MWd) and Local
Group galaxies (Utomo et al. 2015; Liu et al. 2021). In addition, the
molecular gas (and clouds) in the bar regions of local star-forming
galaxies has higher velocity dispersions and surface densities than

2 _Choi et al._


that in the discs (Sun et al. 2020, 2022). These results strongly
suggest that galactic environment affects GMC properties. More
studies of GMCs in galaxies with diverse morphologies and substructures are thus required to probe these variations and unravel
the underlying physics.
Barred galaxies generally have gas inflows toward their central
regions, due to their non-axisymmetric gravitational potentials (e.g.
Athanassoula 1992; Sormani et al. 2015; Sormani & Barnes 2019;
Henshaw et al. 2023; Sormani et al. 2023). Several CO surveys
have shown higher concentrations of molecular gas in the central
regions of barred galaxies than in unbarred galaxies (e.g. Sakamoto
et al. 1999), as well as increased molecular gas linewidths and
surface densities (Sun et al. 2020, 2022). Recent high-resolution
CO observations of barred disc galaxies have also revealed the
presence of distinct structures similar to those observed at optical
wavelengths, such as nuclear rings, nuclear bars and nuclear spiral
arms, with non-circular motions (e.g. Salak et al. 2016; Cuomo et al.
2019; Bewketu Belete et al. 2021; Sato et al. 2021). Studying barred
disc galaxies therefore enables the exploration of GMC properties,
including scaling relations, within different galactic environments.
However, there have been only a few studies investigating GMCs in
barred galaxies so far (e.g. Hirota et al. 2018; Maeda et al. 2020;
Sato et al. 2021), including GMCs in the MW (e.g. Solomon et al.
1987; Oka et al. 1998; Heyer et al. 2009; Kauffmann et al. 2017).
Rosolowsky et al. (2021) investigated GMCs in ten nearby galaxies,
but only one out of their six barred galaxies was observed with a
spatial resolution sufficient to spatially resolve individual GMCs
( _<_ 30 pc spatial resolution) and thus analyse their scaling relations
and physical properties such as size, mass and linewidth.

Choi et al. (2023) recently investigated the molecular gas of
the barred spiral galaxy NGC 5806 at the GMC scale (≈ 24 pc
spatial resolution). Despite the GMCs having typical properties on
average, they reported that the GMCs in the nuclear ring and its
vicinity have a size ( _𝑅_ c ) – linewidth ( _𝜎_ obs _,_ los ) relation ( _𝜎_ obs _,_ los ∝
_𝑅_ c [1] _[.]_ [2] [)] [that] [is] [much] [steeper] [than] [that] [of] [the] [GMCs] [in] [the] [MW] [or]
other galaxies. This result implies that the GMCs at the centres
of barred galaxies can differ from those in the discs. However, as
this behaviour has been observed in a single object and there is no
adequate sample for comparison, one cannot conclude yet that it is
the bar and associated gas inflow toward the nuclear ring that cause
the steep size – linewidth relation.
To further test this conjecture, we examine the GMCs at the
centre of the barred spiral galaxy NGC 613 (SBbc(rs)) in this paper.
NGC 613 has a large-scale bar, an inner star-forming ring encircling
the bar and weak spiral arms protruding from the bar, at a distance
_𝐷_ = 17 _._ 5 Mpc (Tully 1988). In the central regions (i.e. well within
a diameter of 1 kpc), NGC 613 has a bright core and a well-studied
star-forming nuclear ring (Hummel & Jorsater 1992; Böker et al.
2007, 2008; Falcón-Barroso et al. 2008, 2014; Miyamoto et al. 2017,
2018), that are prominent in both optical continuum and molecular
gas emission. NGC 613 also harbours a nuclear spiral (Audibert et al.
2019), a low-luminosity active galactic nucleus (LL-AGN; VeronCetty & Veron 1986; Hummel et al. 1987; Goulding & Alexander
2009), prominent radio jets (Miyamoto et al. 2017), shock excitation
(Falcón-Barroso et al. 2014) and a shock co-spatial with the peak
of the radio jet (Davies et al. 2017). The size of the nuclear ring of
NGC 613 (radius 300 pc) is almost identical to that of NGC 5806
(radius 330 pc), and the molecular gas mass of NGC 613 is about
30% larger than that of NGC 5806 when a Galactic conversion factor
is applied. NGC 613 also has a total stellar mass (≈ 4 _._ 5 × 10 [10] M ⊙ )
similar to that of NGC 5806 (≈ 3 _._ 9 × 10 [10] M ⊙ ), and a relative
size of the nuclear ring with respect to the galaxy optical diameter



**Table 1.** NGC 613 characteristics.


Quantity Value Reference
Type SB(rs)bc (1)
R.A. (J2000) 1 [h] 34 [m] 18 [s] _._ 19 (2)
Dec. (J2000) −29 [◦] 25 [′] 6 [′′] _._ 6 (2)
Distance (Mpc) 17 _._ 5 (3)
Position angle (degree) 118 ± 4 (2)
Inclination (degree) 46 ± 1 (2)
Systemic velocity (km s [−][1] ) 1471 ± 3 (2)
Central molecular gas mass (M ⊙ ) 3 × 10 [8] (2)
Total stellar mass (M ⊙ ) 4 _._ 5 × 10 [10] (4)
Stellar velocity dispersion (km s [−][1] ) 92 ± 3 (5)
Total star-formation rate (M ⊙ yr [−][1] ) 5 _._ 2 (4)


_References:_ (1) de Vaucouleurs et al. (1991). (2) Miyamoto et al.
(2017). The central molecular gas mass was calculated using the
12 CO(3-2) intensity integrated over the central region of NGC 613
only (radius ≤ 22 [′′] ), assuming a CO-to-molecules conversion factor
_𝑋_ CO(3−2) = 0 _._ 5 × 10 [20] cm [−][2] (K km s [−][1] ) [−][1] . (3) Tully (1988). (4) Combes
et al. (2019). The total stellar mass was calculated using the total 3 _._ 6 _𝜇_ m
luminosity and a mass-to-light ratio _𝑀_ / _𝐿_ 3 _._ 6 _𝜇_ m = 0 _._ 5 M ⊙ /L ⊙ _,_ 3 _._ 6 _𝜇_ m.
The total star-formation rate was calculated using the total infrared
luminosity (NASA/IPAC Extragalactic Database). (5) da Silva et al. (2020).
Luminosity-weighted stellar velocity dispersion within the central region of
NGC 613 (radius ≤ 7 [′′] ).


_𝐷_ 25 (0 _._ 024) similar to that of NGC 5806 (0 _._ 023; Agüero et al.
2016). This leads us to expect the nuclear ring of NGC 613 to
have conditions similar to those of the NGC 5806 nuclear ring,
making a comparison highly relevant. Sato et al. (2021) recently
investigated the properties of the molecular gas in and around the
nuclear ring of NGC 613. While they identified GMCs and measured
their properties, they did not conduct a detailed analysis of the GMC
characteristics, such as the size – linewidth relation. We thus first
identify and then thoroughly explore the properties of the GMCs in
and around the nuclear ring of NGC 613 here. Key characteristics
of NGC 613 are summarised in Table 1.

This paper is structured as follows. In Section 2, we describe
the data and the methodology used to identify GMCs in NGC 613.
The GMCs identified and their properties are discussed in Section 3.
In Section 4, we investigate and discuss the GMC size – linewidth
relation and dynamical states, and the clouds in the nuclear ring
only. We summarise our findings in Section 5.


**2** **OBSERVATIONS**


**2.1** **Data**


NGC 613 was observed in the [12] CO(1-0) line (rest frequency
115 _._ 271 GHz) using the Atacama Large Millimeter/sub-millimeter
Array (ALMA). The observations were carried out using two different 12-m array configurations in November and December 2017
(programme 2017.1.01671.S, configurations C43-6 and C43-8, PI
Miyamoto). The C43-6 configuration observations had 6500 s onsource using 47 antennae and baselines of 15 – 2500 m, leading
to a maximum recoverable scale (MRS) of 5 [′′] _._ 5. The C43-8 configuration observations had 9500 s on-source using 46 antennae and
baselines of 110 – 11 _,_ 000 m, leading to a MRS of 1 [′′] _._ 7. Both configurations have a primary beam of 54 [′′] _._ 4 full-width at half-maximum
(FWHM). The correlator was set up with one spectral window of
468 _._ 750 MHz (≈ 1200 km s [−][1] ) bandwidth and 1920 channels each
of 244 kHz (≈ 0 _._ 63 km s [−][1] ) centred on the redshifted [12] CO(1-0)


MNRAS **000**, 1–15 (2023)

line. The three remaining spectral windows each have a 1 _._ 875 GHz
bandwidth with 1920 channels of 976 kHz and were used to observe

the continuum.


_2.1.1_ _Data reduction_


The raw data of each configuration were calibrated and then combined using the standard ALMA pipeline version 5.6.1-8, using
Common Astronomy Software Applications (casa; McMullin
et al. 2007) version 5.6.1. Continuum emission was measured using
line-free channels and subtracted from the data using the casa task
`UVCONTSUB` . We imaged the data using Briggs weighting with a robust parameter of 0 _._ 5 and cleaned using the `tclean` task to a depth
equal to twice the root-mean-square (RMS) noise of the dirty data
cube (respectively the continuum image), yielding synthesised beam
FWHM of 0 [′′] _._ 27 × 0 [′′] _._ 20 (≈ 24 × 18 pc [2] ) with a position angle of 86 [◦]

for the [12] CO(1-0) line and 0 [′′] _._ 29 × 0 [′′] _._ 21 (≈ 26 × 19 pc [2] ) with a position angle of 86 [◦] for the continuum. We chose a pixel size of 0 [′′] _._ 05
to balance image size and spatial sampling, yielding approximately
4×6 pixels across the synthesised beam for the line data. We thus created a fully calibrated and cleaned cube encompassing most of the
primary beam spatially, with 2 km s [−][1] (binned) channels spectrally.
The RMS noise of the [12] CO(1-0) cube is _𝜎_ rms = 0 _._ 59 mJy beam [−][1]

(1 _._ 10 K) per channel. The continuum image has the RMS noise of
6 _._ 5 _𝜇_ Jy beam [−][1] and the flux of the continuum emission within the
nuclear ring (radius ≤ 6 [′′] ) is 11 _._ 7 mJy.


**2.2** **Moment maps**


Figure 1 shows the zeroth-moment (integrated-intensity), firstmoment (intensity-weighted mean line-of-sight velocity) and
second-moment (intensity-weighted line-of-sight velocity dispersion) maps of the [12] CO(1-0) emission of NGC 613. These were
generated using a smooth-moment masking method (e.g. Dame
2011). In summary, we convolved the [12] CO(1-0) data cube spatially with a Gaussian of width equal to that of the synthesised
beam and Hanning-smoothed the cube spectrally. To create a mask
we then selected only pixels with intensities exceeding three times
the RMS noise of the smoothed cube, and applied this mask to the
original cube to generate the moment maps.
The integrated intensity map of NGC 613 (top-left panel of
Figure 1) reveals a highly structured molecular gas distribution.
There are at least three clearly distinguishable structures: a nucleus
at the very centre of the galaxy, a nuclear ring with a radius of ≈
300 pc and offset dust lanes stretching from the northeast (toward the
northwest) and the southwest (toward the southeast). The interface
between the nuclear ring and the dust lane in the east has intensities
higher than those in the rest of the nuclear ring, and there is a
gradual decrease of the intensities as a function of the azimuthal
angle in a counter-clockwise direction. The interface in the west
also has higher intensities but it does not show a clear decrease of
the intensities along the nuclear ring. Finally, there are faint nuclear
spiral arms between the nucleus and the nuclear ring.
The mean velocity map (top-middle panel of Figure 1) clearly
shows roughly circular motions throughout the disc and particularly
within the nuclear ring, with a projected angular momentum vector pointing toward the northeast. The zero-velocity curve shows
significant twists, however, particularly along the dust lanes, implying significant non-circular motions. These motions are as expected
from the shocks and non-axisymmetric perturbations driven by the
large-scale bar of a disc galaxy (e.g. Athanassoula 1992).


MNRAS **000**, 1–15 (2023)



_WISDOM XXI. GMCs in NGC 613_ 3


The velocity dispersion of the molecular gas (top-right panel
of Figure 1) ranges from 0 to 60 km s [−][1], higher than typical velocity
dispersions across discs of galaxies but similar to those in the central
region of nearby disc galaxies (e.g. Wilson et al. 2011; Mogotsi et al.
2016; Sun et al. 2018). The nucleus has particularly high velocity
dispersion (20 – 40 km s [−][1] ). As NGC 613 hosts an AGN and radio
jets, this might be due to the AGN and its feedback. The velocity
dispersions at the interfaces between the nuclear ring and the offset
dust lanes also have high velocity dispersions (20 – 60 km s [−][1] ),
higher than those in the rest of the nuclear ring (0 – 25 km s [−][1] ).
In particular, the interface to the west of the nucleus has velocity
dispersions higher (30 – 60 km s [−][1] ) than those in the interface to
the east of the nucleus (10 – 35 km s [−][1] ), indicating that the two
regions are slightly different. Indeed, Sato et al. (2021) revealed that
the gas inflow velocity toward the eastern side of the nuclear ring
from the northeast dust lane (≈ 70 km s [−][1] ) is lower than that toward
the western side of the nuclear ring from the southwest dust lane
(≈ 170 km s [−][1] ).
The [12] CO(1-0) spectrum of NGC 613 integrated within a central region of 15 [′′] × 15 [′′] (bottom-left panel of Figure 1) reveals
multiple peaks, suggesting again complex molecular gas distribution and kinematics. The total [12] CO(1-0) flux in that region is
512 Jy km s [−][1] .
The 100 GHz continuum map of NGC 613 (bottom-middle
of Figure 1) shows two distinct structures: one associated with the
nuclear ring, the other in the centre and elongated roughly northsouth. By showing that the spectral index between 4 _._ 9 and 95 GHz
_𝛼_ ≈−0 _._ 2 in the nuclear ring while _𝛼_ ≈−0 _._ 6 in the central region,
Miyamoto et al. (2017) suggested that the continuum emission in the
nuclear ring likely arise from free-free emission from H ii regions
while the elongated continuum emission at the centre is due to the
jet. Additionally, they reported that SiO(2-1) (a shock tracer; e.g.
García-Burillo et al. 2001) is detected at both ends of the elongated
continuum (blue stars in bottom-middle of Figure 1).
The bottom-right panel of Figure 1 illustrates our definitions
of four distinct regions based on the moment maps: nucleus (blue),
arcs (green), nodes (red) and dust lanes (yellow). The nucleus encompasses the inner 180 pc in radius. The arcs refer to the regions
of relatively low velocity dispersions (0 – 25 km s [−][1] ) of the nuclear
ring, while the nodes refer to the regions of relatively high velocity
dispersions (≳ 25 km s [−][1] ) of the nuclear ring, at the interfaces
between the offset dust lanes and the nuclear ring. As expected, the
dust lanes encompass the two offset dust lanes stretching from the
east of the nuclear ring toward the northwest and from the west of
the nuclear ring toward the southeast, that are often present in barred
disc galaxies (e.g. Athanassoula 1992). Note that we will also refer
to the nuclear ring in its entirety, encompassing both the arcs and
the nodes.

Interestingly, the molecular gas distribution of NGC 613 is
very similar to that in the central region of NGC 5806 (Choi et al.
2023), except for the fact that NGC 5806 has similar gas inflow
velocities at the nodes on either side of the nuclear ring. The GMCs
of NGC 613 and NGC 5806 are thus also expected to have similar
characteristics.


**3** **CLOUD IDENTIFICATION AND PROPERTIES**


**3.1** **Cloud identification**


To identify the clouds of NGC 613 (and to be consistent with previous works), we use our own modified version of the algorithms

4 _Choi et al._


**Figure 1.** [12] CO(1-0) emission of NGC 613. **Top-left** : zeroth-moment (integrated-intensity) map. **Top-middle** : first-moment (intensity-weighted mean line-ofsight velocity) map. **Top-right** : second-moment (intensity-weighted line-of-sight velocity dispersion) map. The synthesised beam of 0 [′′] _._ 27×0 [′′] _._ 20 (≈ 24×18 pc [2] )
is shown in the bottom-left corner of each moment map as a filled black ellipse. **Bottom-left** : Integrated [12] CO(1-0) spectrum, extracted from a 15 [′′] × 15 [′′]

region around the galaxy centre. **Bottom-middle** : 100 GHz continuum map. The synthesised beam of 0 [′′] _._ 29 × 0 [′′] _._ 21 is shown in the bottom-left corner as a
filled black ellipse. The blue stars indicate the regions where SiO(2-1) is detected (Miyamoto et al. 2017). **Bottom-right** : resolved clouds (black circles; see
Figure 2) of the nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow), as defined in Section 2.2.



of cpropstoo (Liu et al. 2021), an updated version of CPROPS
(Rosolowsky & Leroy 2006; Leroy et al. 2015). Due to fewer free
parameters, our version is more efficient and leads to a more robust
cloud identification in complex and crowded environments.


We refer the reader to Liu et al. (2021) for full details of
our version of cpropstoo, but introduce here the main parameters of the algorithms. cpropstoo identifies and divides clouds into
resolved and unresolved clouds based on fixed input parameters.
The algorithm generates a three-dimensional (3D) mask using two
parameters, _high-threshold_ and _low-threshold_ . The mask initially
chooses only pixels for which two adjacent channels are above _high-_
_threshold_, and then expands this region to include all neighbouring
pixels for which two adjacent channels are above _low-threshold_ . To
identify individual clouds from the selected pixels, the algorithm
imposes a minimum cloud area ( _minarea_ ) and a minimum number
of cloud velocity channels ( _minvchan_ ). Lastly, the _convexity_ parameter (defined as the ratio of the volume of a cloud’s 3D intensity
distribution to that of its convex envelope) is used to identify struc


tures over multiple spatial scales with less arbitrariness. We set
the minimum contrast between a cloud’s peak and its boundary at
Δ _𝑇_ max = 2 _𝜎_ rms = 2 _._ 20 K.


In this work, we run cpropstoo on a 15 [′′] × 15 [′′] region of the
12 CO(1-0) cube centred on the galaxy centre, thus encompassing all
of the emission detected in the zeroth-moment map (see Figure 1),
adopting _high-threshold_ = 4 _._ 5 _𝜎_ rms, _low-threshold_ = 2 _._ 0 _𝜎_ rms,
_minvchan_ = 2 and _convexity_ = 0 _._ 65. We assign _minarea_ a range of
120 – 24 spaxels (the synthesised beam area) with a step size of 24
spaxels in descending order, rather than adopting a single value. As
a result, we identify 356 GMCs, 158 of which are both spatially and
spectrally resolved, shown in Figure 2. We note that while different
sets of parameters yield slightly different cloud identification results,
we have verified that for reasonable parameters the overall results
and conclusions remain unaffected.


MNRAS **000**, 1–15 (2023)

_WISDOM XXI. GMCs in NGC 613_ 5


︂



_𝜈_ obs the observed line frequency. To obtain the molecular gas mass,
we adopt a CO-to-molecule conversion factor (including helium)
_𝑋_ CO = 2 × 10 [20] cm [−][2] (K km s [−][1] ) [−][1], equivalent to a conversion
factor _𝛼_ CO(1−0) ≈ 4 _._ 4 M ⊙ (K km s [−][1] pc [2] ) [−][1], yielding

_𝑀_ gas _𝐿_ CO(1−0)

≈ 4 _._ 4 _._ (4)

� M ⊙ � � K km s [−][1] pc [2] �


︂



_𝐿_ CO(1−0)
� ≈ 4 _._ 4 � K km s [−][1] pc [2]


︂



_._ (4)
�


︂



︂



**Figure** **2.** [12] CO(1-0) integrated-intensity map of NGC 613, with the 356
GMCs identified overlaid. Resolved clouds are shown as dark blue open
ellipses, unresolved clouds as cyan open ellipses. The major and minor axes
of each ellipse represent the RMS spatial extent of the associated cloud along
its major and minor axes, respectively, extrapolated to the limit of perfect
sensitivity but not been corrected (i.e. deconvolved) for the finite angular

resolution.


The synthesised beam (0 [′′] _._ 27 × 0 [′′] _._ 20 or ≈ 24 × 18 pc [2] ) is shown in the
bottom-left corner as a filled black ellipse.


**3.2** **Cloud properties**


We calculate the physical properties of the clouds as described in
Liu et al. (2021) and references therein (Rosolowsky & Leroy 2006;
Leroy et al. 2015). We describe here the three key properties of
the clouds (size, velocity dispersion and gas mass), from which the
virial parameter is derived.
The cloud size (radius _𝑅_ c ) is defined as


_𝑅_ c ≡ _𝜂_ [√︁] _𝜎_ maj _,_ dc _𝜎_ min _,_ dc _,_ (1)


where _𝜂_ is a geometric parameter, _𝜎_ maj _,_ dc and _𝜎_ min _,_ dc are the deconvolved RMS spatial extent along the major and the minor axis
of the cloud, respectively, and we adopt _𝜂_ = 1 _._ 91 for consistency
with earlier studies (e.g. Solomon et al. 1987; Utomo et al. 2015;
Liu et al. 2021).
The observed velocity dispersion ( _𝜎_ obs _,_ los ) is calculated as


︂



︂


_𝜎_ obs _,_ los ≡



︂
~~√~~ � _𝜎_ v [2] −(Δ _𝑉_ chan [2] [/][2] _[𝜋]_ [)] � _,_ (2)



︂


where _𝜎_ v is the second moment extrapolated to the limit of infinite
sensitivity ( _𝑇_ edge = 0 K) along the velocity axis and Δ _𝑉_ chan is the
channel width of 2 km s [−][1] .
The molecular gas mass ( _𝑀_ gas ) is obtained from the [12] CO(1-0)
luminosity

_𝐿_ CO(1−0) = 3 _._ 25 × 10 7 _𝐹_ CO(1−0) _𝜈_ obs −2 [�] _𝐷_
� K km s [−][1] pc [2] � � (1 + _𝑧_ ) [3] �� Jy km s [−][1] �� GHz � Mpc �


(3)


where _𝐹_ CO(1−0) is the [12] CO(1-0) flux, _𝑧_ the galaxy redshift and


MNRAS **000**, 1–15 (2023)



_3.2.1_ _General properties_


Table 2 lists the three aforementioned (intensity-weighted) properties of each cloud and many more (see Liu et al. 2021): each cloud’s
central position (R.A. and Dec.), mean local standard of rest velocity ( 12 CO(1-0) luminosity ( _𝑉_ LSR ), size (radius _𝑅𝐿_ COc ), observed velocity dispersion ( (1−0) ), molecular gas mass ( _𝑀_ gas _𝜎_ obs ), peak _,_ los ),
intensity ( _𝑇_ max ), gradient-subtracted velocity dispersion ( _𝜎_ gs _,_ los )
and deprojected distance from the galaxy centre ( _𝑅_ gal ). _𝜎_ gs _,_ los represents the "turbulent" motions within a cloud, having subtracted
all bulk motions due to e.g. shear or internal rotation, and we refer readers to Utomo et al. (2015) for its definition (see also Liu
et al. 2021). The uncertainties of the above quantities are derived
via 500 bootstrap resampling. The uncertainty of the distance to
NGC 613 is not propagated through, as a distance error translates
to a systematic scaling of some of the estimated quantities: _𝑅_ c ∝ _𝐷_,
_𝐿_ CO(2−1) ∝ _𝐷_ [2], _𝑀_ gas ∝ _𝐷_ [2], _𝑀_ vir ∝ _𝐷_ and _𝛼_ vir ∝ _𝐷_ [−][1] (see
Section 4).

Figure 3 shows the number distributions of _𝑅_ c, _𝑀_ gas, _𝜎_ obs _,_ los
and gas mass surface density (Σ gas ≡ _𝑀_ gas / _𝜋𝑅_ c [2] ) of the resolved
clouds of NGC 613. In each panel, the black histogram and overlaid
black Gaussian fit show the full cloud sample, while the colourcoded histograms and Gaussians show only the clouds in the nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow), respectively. The means of all the quantities are listed in Table 3.
The resolved clouds of NGC 613 have sizes ( _𝑅_ c ) ranging from
15 to 70 pc (top-left panel of Figure 3) with a mean of ≈ 38 pc. They
have gas masses ( _𝑀_ gas ) ranging from 2 _._ 9 × 10 [5] to 5 _._ 0 × 10 [7] M ⊙
(top-right panel of Figure 3) with a mean of ≈ 7 × 10 [6] M ⊙ . Most
(134/158) of the resolved clouds are massive ( _𝑀_ gas ≥ 10 [6] M ⊙ ).
The observed velocity dispersions of the resolved clouds range from
2 to 36 km s [−][1] (bottom-left panel of Figure 3) with a mean of
≈ 13 km s [−][1], while the gas mass surface densities range from 100
to 6300 M ⊙ pc [−][2] (bottom-right panel of Figure 3) with a mean of
≈ 1200 M ⊙ pc [−][2] .
The clouds in the arcs (9 _._ 3 ± 1 _._ 6 × 10 [6] M ⊙ ) and the dust lanes
(4 _._ 1 ± 0 _._ 6 × 10 [6] M ⊙ ) tend to be more and less massive than the
clouds in the nucleus (7 _._ 7±2 _._ 8×10 [6] M ⊙ ) and the nodes (7 _._ 3±1 _._ 3×
10 [6] M ⊙ ), respectively. The clouds in the dust lanes tend to be less
turbulent than those in the other three regions (11 _._ 2 ± 0 _._ 7 km s [−][1]

vs. 14 _._ 4 ± 2 _._ 1, 13 _._ 5 ± 0 _._ 7 and 13 _._ 1 ± 0 _._ 8 km s [−][1] ). However, there

︂ is no significant size variation across the four regions, resulting in

higher and lower gas mass surface densities for the clouds in the
arcs (1630 ± 200 M ⊙ pc [−][2] ) and the dust lanes (780 ± 70 M ⊙ pc [−][2] )
compared to those in the nucleus (1290 ± 350 M ⊙ pc [−][2] ) and the
nodes (1290 ± 140 M ⊙ pc [−][2] ), respectively. In particular, the clouds
in the dust lanes have smaller gas mass surface densities than those
in the other three regions (see the double-peaked black histogram
in the bottom-right panel of Figure 3). This implies that the clouds
get denser as they migrate into the nuclear ring.
In Figure 4, we compare the properties of the GMCs of the
MWd, MW central molecular zone (CMZ) and other external galaxies with those of the NGC 613 GMCs using violin plots. The resolved clouds of NGC 613 have comparable sizes but larger masses,



︂


7
3 _._ 25 × 10

=
� � (1 + _𝑧_ ) [3]



︂


�� Jy km s _𝐹_ CO(1− [−] 0) [1]



︂


_𝜈_ obs
�� GHz



︂


� −2 [�] Mpc _𝐷_



︂


2

_,_
�



︂


(1 + _𝑧_ ) [3]

6 _Choi et al._


**Table 2.** Measured properties of the clouds of NGC 613. A complete machine-readable version of this table is available in the online journal version.


ID R.A. (2000) Dec. (2000) _𝑉_ LSR _𝑅_ c _𝜎_ obs _,_ los _𝜎_ gs _,_ los _𝐿_ CO(2−1) _𝑀_ gas _𝑇_ max _𝑅_ gal
(h:m:s) ( [◦] : [′] : [′′] ) (km s [−][1] ) (pc) (km s [−][1] ) (km s [−][1] ) (10 [4] K km s [−][1] pc [−][2] ) (10 [5] M ⊙ ) (K) (pc)

1 1:34:18.49 -29:25:08.16 1267.1 44.41 ± 3.54 11.44 ± 1.01 9.16 ± 1.12 53.035 ± 3.525 23.335 ± 1.551 9.5 357

2 1:34:18.45 -29:25:07.07 1282.3  - 5.87 ± 6.31 2.38 ± 7.14 16.063 ± 33.692 7.068 ± 14.825 11.2 305

3 1:34:18.47 -29:25:06.99 1293.4 38.21 ± 2.34 12.11 ± 0.74 8.72 ± 0.61 93.500 ± 3.926 41.140 ± 1.728 13.2 328

4 1:34:18.51 -29:25:08.43 1310.5 55.94 ± 1.57 20.15 ± 0.52 17.95 ± 0.51 416.533 ± 6.462 183.274 ± 2.843 17.7 385

5 1:34:18.65 -29:25:07.95 1304.3  - 4.82 ± 3.60 3.62 ± 5.89 4.883 ± 5.776 2.149 ± 2.541 5.6 539

6 1:34:18.55 -29:25:07.80 1308.3  - 4.05 ± 4.82 0.97 ± 2.38 6.225 ± 12.051 2.739 ± 5.302 7.3 420

   -   -   -   -   -   -   -   -   -   -   
356 1:34:17.91 -29:25:07.39 1668.8  - 4.36±2.16 2.78±1.79 4.461±2.141 1.963±0.942 7.8 384

[︁]



**Figure 3.** Number distributions of _𝑅_ c, log( _𝑀_ gas /M ⊙ ), _𝜎_ obs _,_ los and log(Σ gas /M ⊙ pc [−][2] ) with Gaussian fits overlaid for the 158 resolved clouds of NGC 613
(black lines and histograms), and for the clouds in the nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow) only. The black arrows in the two left
panels represent our ability to resolve clouds spatially (top-left; 0 _._ 43 _𝜂_ ~~[√]~~ [︁] _𝜃_ maj _𝜃_ min, where _𝜃_ maj and _𝜃_ min are the synthesised beam’s FWHM) and spectrally
(bottom-left; channel width of 2 km s [−][1] ).




[︁]


**Table 3.** Mean quantities of resolved GMCs.


Sample _𝑅_ c _𝑀_ gas _𝜎_ obs _,_ los Σ gas
( _𝑁_ clouds ) (pc) (10 [6] M ⊙ ) (km s [−][1] ) (10 [3] M ⊙ pc [−][2] )
All (158) 37 _._ 8 ± 0 _._ 9 7 _._ 1 ± 0 _._ 7 12 _._ 8 ± 0 _._ 4 1 _._ 25 ± 0 _._ 09
Nucleus (11) 38 _._ 3 ± 2 _._ 8 7 _._ 7 ± 2 _._ 8 14 _._ 4 ± 2 _._ 1 1 _._ 29 ± 0 _._ 35
Arcs (48) 39 _._ 1 ± 1 _._ 6 9 _._ 3 ± 1 _._ 6 13 _._ 5 ± 0 _._ 7 1 _._ 63 ± 0 _._ 20
Nodes (51) 37 _._ 2 ± 1 _._ 6 7 _._ 3 ± 1 _._ 3 13 _._ 1 ± 0 _._ 8 1 _._ 29 ± 0 _._ 14
Dust lanes (48) 37 _._ 0 ± 1 _._ 7 4 _._ 1 ± 0 _._ 6 11 _._ 2 ± 0 _._ 7 0 _._ 78 ± 0 _._ 07


velocity dispersions and gas mass surface densities than the clouds
of the MWd (≤ 20 pc spatial resolution; Heyer et al. 2009; Rice
et al. 2016; Heyer & Dame 2015; and references therein). On the
other hand, they have larger sizes and masses but smaller velocity
dispersions than the clouds of the CMZ (≤ 1 _._ 5 pc resolution; Oka
et al. 1998, 2001).
Most clouds in LTGs have larger sizes and comparable gas
masses but smaller observed velocity dispersions and gas mass




[︁]


surface densities (10 – 80 pc resolution; e.g. Donovan Meyer et al.
2012; Gratier et al. 2012; Colombo et al. 2014; Rosolowsky et al.
2021; Liu et al. submitted) than the NGC 613 clouds. Clouds in
ETGs (NGC 4526 and NGC 4429) have smaller sizes, gas masses
and observed velocity dispersions (≤ 20 pc resolution; Utomo et al.
2015; Liu et al. 2021) than the clouds of NGC 613. The gas mass
surface densities of the clouds of NGC 4526 and NGC 4429 are
comparable to (⟨Σ gas ⟩≈ 1000 M ⊙ pc [−][2] ) and smaller than (⟨Σ gas ⟩≈
150 M ⊙ pc [−][2] ) that of the clouds of NGC 613, respectively.


The clouds in the morphologically-similar galaxy NGC 5806
(≈ 24 pc resolution; Choi et al. 2023) have very similar sizes (15
– 85 pc, ⟨ _𝑅_ c ⟩ = 34 _._ 5 pc), but their gas masses (1 _._ 2 × 10 [5] – 3 _._ 6 ×
10 [7] M ⊙, ⟨ _𝑀_ gas ⟩ = 6 _._ 9 × 10 [5] M ⊙ ), velocity dispersions (1 _._ 6 –
20 km s [−][1], ⟨ _𝜎_ obs _,_ los ⟩ = 6 _._ 6 km s [−][1] ) and gas mass surface densities
(⟨Σ gas ⟩≈ 200 M ⊙ pc [−][2] ) are much smaller than those of the clouds
of NGC 613. For both NGC 613 and NGC 5806, the clouds in the


MNRAS **000**, 1–15 (2023)

_WISDOM XXI. GMCs in NGC 613_ 7


**Figure 4.** Violin plots showing the distributions of _𝑅_ c, _𝑀_ gas, _𝜎_ obs _,_ los and Σ gas for the NGC 613 resolved clouds and other extragalactic GMC populations. The
ranges for NGC 613 have been derived in this work, while those for the other objects are from the literature: MWd (Heyer et al. 2009; Rice et al. 2016; Heyer
& Dame 2015; and references therein), CMZ (Oka et al. 2001), LTGs (Donovan Meyer et al. 2012; Gratier et al. 2012; Colombo et al. 2014; Rosolowsky et al.
2021; Liu et al. submitted), ETGs (Utomo et al. 2015; Liu et al. 2021) and NGC 5806 (Choi et al. 2023). The black vertical lines in each violin plot represent
the 5 [th], 50 [th] and 95 [th] percentiles of the distribution, while the red line indicates the mean.


arcs and nodes have gas mass surface densities higher than those in
the dust lanes.

Overall, there is no significant cloud size variation across the
four regions of NGC 613. The clouds in the arcs are generally more
massive and have larger gas mass surface densities than the clouds
in the dust lanes, while the clouds in the nucleus and nodes are in

between. The clouds in the dust lanes tend to be less turbulent than

those in other the regions.


_3.2.2_ _Cloud kinematics_



By comparing the observed velocity dispersions ( _𝜎_ obs _,_ los ) with the
gradient-subtracted velocity dispersions ( _𝜎_ gs _,_ los ), we can assess
whether bulk motions (due to e.g. galaxy rotation and/or shear)
contribute significantly to the observed velocity dispersions of the
clouds. If the gradient-subtracted velocity dispersions are much
smaller than the observed velocity dispersions, bulk motions are
dominant in the clouds. Figure 5 shows the relation between _𝜎_ obs _,_ los
and _𝜎_ gs _,_ los . More than 80% of the clouds (138/158) of NGC 613
have a small difference between the two velocity dispersions (i.e. a
ratio between the two velocity dispersions _𝜎_ gs _,_ los / _𝜎_ obs _,_ los _>_ 0 _._ 7,
with a mean ratio of 0 _._ 82), suggesting that the observed velocity
dispersions are dominated by internal turbulent motions rather than
bulk motions inherited from larger-scale galaxy rotation. This is
similar to the case of NGC 5806, for which more than 60% of the
clouds have a ratio larger than 0 _._ 7 (Choi et al. 2023).
We also confirm that the rotation axes of the NGC 613 clouds

are not well aligned with the isovelocity contours, which is consistent with the case of NGC 5806, supporting that the galaxy rotation
does not affect the internal rotation of the clouds. This is similar to

the case of the MW (Koda et al. 2006), M 31 (Rosolowsky 2007),
NGC 5806 (Choi et al. 2023) and NGC 5064 (Liu et al. 2023), but
different from that of the ETGs NGC 4526 (Utomo et al. 2015) and
NGC 4429 (Liu et al. 2021), where the rotation axes are well aligned
with the isovelocity contours.


**4** **DYNAMICAL STATES OF CLOUDS**


Using the cloud properties calculated above, we now attempt to
diagnose the dynamical states of the clouds. A standard relation


MNRAS **000**, 1–15 (2023)



**Figure** **5.** Comparison of the observed ( _𝜎_ obs _,_ los ) and gradient-subtracted
( _𝜎_ gs _,_ los ) velocity dispersion measures for the 158 resolved clouds of
NGC 613. The four black diagonal lines represent the 1 : 1, 1 : 0 _._ 9, 1 : 0 _._ 8
and 1 : 0 _._ 7 ratio, respectively.


to characterise clouds is the size – linewidth relation, known to
have the form of a power law (e.g. _𝜎_ obs _,_ los ∝ _𝑅_ c [0] _[.]_ [5] [,] [Larson] [1981][;]
Solomon et al. 1987). Another relation quantifying the gravitational
boundness of clouds is that between the virial mass and gas mass,
the ratio of which corresponds to the virial parameter of the clouds.
We now discuss both relations in turn.


**4.1** **Steep size – linewidth relation**


The size – linewidth relation is usually interpreted as being due
to the internal turbulent motions of clouds (Falgarone et al. 1991;
Heyer & Brunt 2004; Elmegreen & Scalo 2004; Lequeux 2005). In
the case of incompressible turbulence, _𝜎_ obs _,_ los ∝ _𝑅_ c [1][/][3] is expected,
which comes from the assumption that the energy cascades conservatively down to smaller scales (i.e. constant energy transfer rate,

8 _Choi et al._


Kolmogorov 1941). In the case of compressible turbulence, the energy transfer down to a smaller scale is not conservative since the
energy can be directly dissipated at large scales via shocks and/or
gas compression, leading to steeper size – linewidth relations with
power-law indices of 1/2 – 3/5 (e.g. Cen 2021, McKee & Ostriker
2007, and references therein).
The left panel of Figure 6 shows the size – linewidth relation
of all resolved clouds of NGC 613 (coloured circles). There is
a clear correlation between size and linewidth, with a Spearman
rank correlation coefficient of 0 _._ 60 and a _𝑝_ -value of 10 [−][16] . To
calculate the best-fitting power-law relation taking into account both
_𝑅_ c and _𝜎_ obs _,_ los uncertainties, and to be consistent with previous
GMC studies (e.g. Liu et al. 2021; Choi et al. 2023), we use a
hierarchical Bayesian method called Linmix (Kelly 2007). This
yields a best-fitting relation



log _𝜎_ obs _,_ los
� km s [−][1]



_𝑅_ c
= (0 _._ 77 ± 0 _._ 11) log
� � pc



−(0 _._ 10 ± 0 _._ 18) _,_ (5)
�



is strongly affected by a tidal interaction (e.g. de Vaucouleurs &
Freeman 1972; van der Marel 2001). In addition, the slope of the
NGC 4429 clouds is much shallower (≈ 0 _._ 24; Liu et al. 2021) than
that of the NGC 613 clouds once the influence of the large-scale
galaxy rotation on the cloud velocity dispersions is removed.
More recently, Physics at High Angular resolution in Nearby
GalaxieS (PHANGS) studies (e.g. Sun et al. 2020, Sun et al. 2022
and references therein) have been systematically probing the properties of extragalactic molecular gas at intermediate spatial scales.
While most of the PHANGS studies were carried out using a beamby-beam or pixel-by-pixel approach, Rosolowsky et al. (2021) identified GMCs in ten nearby galaxies. The spatial resolutions mostly
range from 60 to 90 pc, with only two galaxies observed with a
spatial resolution comparable to that of our study, but Rosolowsky
et al. (2021) report slopes similar to that of the MWd clouds. The
GMC velocity dispersions are however observed to be higher at a
given cloud size in the central regions than in the outer regions,
potentially also resulting in a steeper slope.


_4.1.1_ _Size – linewidth relation in galaxy centres_


We now investigate whether the steep size – linewidth relation of the
NGC 613 clouds is primarily due to the fact that the relation has been
measured in the central region of the galaxy. For instance, the large
velocity dispersions and relatively steep slope of the CMZ clouds
are the most distinguishing features of their size – linewidth relation,
compared to that of the MWd clouds. Moreover, the clouds in the
central regions of both NGC 613 and NGC 5806 have steep size –
linewidth relations. On the other hand, the clouds in the centres of
other galaxies have size – linewidth relations much shallower than
(or comparable to) that of the MWd clouds (e.g. no correlation in
NGC 6946, Wu et al. 2017; slope of 0 _._ 6 ± 0 _._ 1 in NGC 5064, Liu
et al. submitted; no correlation in NGC 4526, Utomo et al. 2015;
slope of 0 _._ 29 ± 0 _._ 11 in NGC 1387, Liang et al. in prep.). Although
the clouds in the centre of M 83 have higher velocity dispersions
than those of the MWd clouds and have a steep size – linewidth
relation, the correlation is very weak. And while the clumps in the
central region of the dwarf lenticular galaxy NGC 404 also have
a steep size – linewidth relation (Liu et al. 2022), the comparison
is arguably inappropriate as the clumps are much smaller (≈ 3 pc)
than the clouds considered in other studies. Therefore, while the
centres of galaxies may partially contribute to steep size – linewidth
relations, they are not likely to be the primary driver of them.


_4.1.2_ _Large-scale bars and nuclear rings_


Although the GMCs of barred-spiral galaxies have been investigated
previously (e.g. M 83 and NGC 1300; Hirota et al. 2018; Maeda
et al. 2020), only the GMCs in the central region of NGC 5806
display a very steep size – linewidth relation, with a slope of ≈ 1 _._ 2
(purple dotted line in Figure 6). However, among these three galaxies, only the observations of NGC 5806 have a spatial resolution
sufficient to resolve GMCs and cover the whole central region. Thus,
in Choi et al. (2023), we first suggested that bar-driven gas shocks
and inflows toward the nuclear ring, which can potentially cause
additional turbulence within the clouds, may be the main reasons
for the steep size – linewidth relation of NGC 5806. Intriguingly,
in this work, we find another example of a steep size – linewidth
relation in and around the nuclear ring of a barred spiral galaxy
(NGC 613). We thus discuss briefly below whether bar-driven inflows can contribute to the enhanced cloud linewidths and a steep
cloud size – linewidth relation in the nuclear ring of NGC 613.


MNRAS **000**, 1–15 (2023)



shown in Figure 6 as a black solid line. The best-fitting relations
of MWd (Solomon et al. 1987) and CMZ (e.g. Kauffmann et al.
2017) clouds are also shown as black dashed and black dotted lines,
respectively.
The best-fitting slope (0 _._ 77 ± 0 _._ 11) is steeper than that of
the clouds in the MWd (0 _._ 5 ± 0 _._ 05; Solomon et al. 1987) but
is comparable to that of the clouds in the CMZ (0 _._ 66 ± 0 _._ 18;
Kauffmann et al. 2017) within the uncertainties, and the zero-point
(0 _._ 79 ± 0 _._ 33 km s [−][1] ) is comparable to that of the MWd clouds
(1 _._ 0 ± 0 _._ 1 km s [−][1] ; Solomon et al. 1987) but is much smaller than
that of the CMZ clouds (5 _._ 5 ± 1 _._ 0 km s [−][1] ; Kauffmann et al. 2017).
The slope is also steeper than that of the clouds in most nearby
galaxies (0 _._ 4 – 0 _._ 8; Rosolowsky et al. 2003; Rosolowsky 2007; Bolatto et al. 2008; Wong et al. 2011) and the predicted slopes of some
theoretical models (1/3 – 3/5; Kolmogorov 1941; Cen 2021).The
grey solid line in Figure 6, which shows an even steeper slope, is that
from the best-fitting relation derived using the orthogonal distance
regression (ODR) algorithm ( _𝜎_ obs _,_ los ∝ _𝑅_ c [1] _[.]_ [58][±][0] _[.]_ [15] ). This slope is
even steeper than that of NGC 5806 (1 _._ 20 ± 0 _._ 10) and any other
galaxy. We however again note that it is the slope yielded by the
Linmix algorithm that will be used for the following discussion, to
be consistent with previous GMC studies.
The right panel of Figure 6 shows the size – linewidth relations
of the two ETGs NGC 4526 (≈ 20 pc spatial resolution and ≈ 0 _._ 7 K
sensitivity) and NGC 4429 (≈ 13 pc and ≈ 0 _._ 5 K) and the LMC
(≈ 11 pc and ≈ 0 _._ 3 K), that have observations with comparable
spatial resolutions and sensitivities. While the observations of M 51
(Colombo et al. 2014) and M 33 (Gratier et al. 2012) are more
different in term of the spatial resolution, we also include them
in the right panel of Figure 6 to illustrate the size – linewidth
relations of a broader variety of galaxy morphological types. Each
coloured contour encompasses 68% of the distribution of the clouds
of the associated galaxy, including NGC 5806 (purple contour) and
NGC 613 (black contour). The black curve with filled black circles

shows the binned trend of NGC 613 from this work. It connects

the median velocity dispersions measured in ten bins along the
abscissa, each containing an equal number of clouds. Except the
LMC (0 _._ 80 ± 0 _._ 05, Wong et al. 2011) and NGC 5806 (purple dotted
line), none of these galaxies shows a steeper slope than NGC 613
(M33, 0 _._ 45 ± 0 _._ 02, Rosolowsky et al. 2003; M51, no correlation,
Colombo et al. 2014; NGC 4429, 0 _._ 82 ± 0 _._ 13, Liu et al. 2021;
NGC 4526, no correlation, Utomo et al. 2015). The LMC has a
comparable slope and a large-scale bar, but comparison with it is
not fully justified as the bar is off centred and the whole galaxy

_WISDOM XXI. GMCs in NGC 613_ 9


**Figure 6. Left:** Size – linewidth relation of the resolved clouds of the nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow) of NGC 613. The black
and grey solid lines show the best-fitting power-law relations of all resolved clouds of NGC 613 using the Linmix and ODR algorithm, respectively. The black
dashed and black dotted lines show the best-fitting relation of the MWd (Solomon et al. 1987) and CMZ (Kauffmann et al. 2017) clouds, respectively. The
purple dotted line shows the best-fitting relation of the NGC 5806 clouds. **Right:** Same as the left panel, but with coloured contours encompassing 68% of
the distribution of the data points of a number of galaxies (LMC, Wong et al. 2011; M 33, Gratier et al. 2012; M 51, Colombo et al. 2014; NGC 4429, Liu
et al. 2021; NGC 4526, Utomo et al. 2015). The contours are colour-coded according to each galaxy’ morphological type (see the colour bar). The black and
purple contours show the corresponding distributions of NGC 613 and NGC 5806 (Choi et al. 2023). The black curve with filled black circles shows the binned
relation of NGC 613 (medians in abscissa bins containing equal numbers of clouds).



Adopting the gas inflow velocities ( _𝑉_ in _,_ east ≈ 70 km s [−][1] and
_𝑉_ in _,_ west ≈ 170 km s [−][1] ) inferred by Sato et al. (2021), the total mass
inflow rate along each of the two dust lanes can be estimated as


�
_𝑀_ in _,_ east = ⟨Σ gas ⟩ _𝑊_ in _𝑉_ in _,_ east ≈ 5 _._ 8 M ⊙ yr [−][1] _,_

� (6)
_𝑀_ in _,_ west = ⟨Σ gas ⟩ _𝑊_ in _𝑉_ in _,_ west ≈ 14 M ⊙ yr [−][1] _,_


where ⟨Σ gas ⟩≈ 400 M ⊙ pc [−][2] and _𝑊_ in ≈ 100 pc are our measured
mean molecular gas mass surface density and width of the gas
inflow in both dust lanes, respectively. To examine whether these
bar-driven gas inflows carry enough energy to drive turbulence in
the nuclear ring, we estimate the total kinetic energy per unit time
transported by these gas inflows to the nuclear ring:


� � �
_𝐸_ in _,_ total = _𝐸_ in _,_ east + _𝐸_ in _,_ west



≈ [1]



2 _𝑀_ � in _,_ west _𝑉_ in [2] _,_ west



(7)



�

[1] 2 _𝑀_ in _,_ east _𝑉_ in [2] _,_ east [+] [1] 2



mean velocity dispersion and scale height of the molecular gas
in the nuclear ring, respectively. This scale height was estimated
as _ℎ_ NR = ⟨ _𝜎_ NR ⟩/ _𝜅_ NR (Lin & Pringle 1987), where _𝜅_ NR is the
epicyclic frequency at the nuclear ring radius, that can be calculated

as _𝜅_ NR [2] [≡] � _𝑅_ _[𝑑]_ [Ω] _𝑑𝑅_ [2] [(] _[𝑅]_ [)] + 4Ω [2] ( _𝑅_ )���� _𝑅_ = _𝑅_ NR, where Ω( _𝑅_ ) ≡ _𝑉_ c ( _𝑅_ )/ _𝑅_,

_𝑉_ c ( _𝑅_ ) is the circular velocity of NGC 613 and _𝑅_ NR is the radius (at
the centre) of the nuclear ring ( _𝑅_ NR ≈ 270 pc). We took _𝑉_ c ( _𝑅_ ) from
Audibert et al. (2019), who derived a rotation curve from [12] CO(3-2)
line observations of NGC 613 assuming the gas is on circular orbits,
leading to _𝜅_ NR ≈ 1 _._ 2 km s [−][1] pc [−][1] and in turn _ℎ_ NR ≈ 14 pc.


If the kinetic energy input rate is balanced by the turbulent energy dissipation rate (i.e. _𝐸_ [�] diss ≈ _𝐸_ [�] in ), the turbulence in the nuclear
ring can be sustained by the gas inflows. Although Equation 7 and
Equation 8 contain large uncertainties, the estimated input rate is
approximately half of the estimated dissipation rate. This estimation suggests that, while bar-driven molecular gas inflows may be a
major contributor to the high velocity dispersions and the steep size
– linewidth relation observed, they are not sufficient to fully explain
them.


By comparing the dissipation timescale and the cloud travel
time, we can also constrain the necessity of additional turbulence
sources. If the dissipation timescale is significantly shorter than the
cloud travel time, this suggests that the turbulence of clouds is not
maintained during travel from one node to the other and thus clouds
are not sustained. The turbulence dissipation timescale of a GMC
can be estimated as _𝑡_ diss ∼ _𝑅_ c / _𝜎_ obs _,_ los (McKee & Ostriker 2007),
yielding a range of 1 – 9 Myr and a mean of 3 _._ 1 Myr for the nuclear
ring clouds of NGC 613. Taking into account the rotation of the
large-scale bar, the cloud travel time between the two nodes can be



≈ 1 _._ 3 × 10 [5] M ⊙ km [2] s [−][2] yr [−][1] _._


We note that this is an upper limit, as it assumes that the kinetic
energy transported by the inflows is entirely converted into turbulent
energy in the nuclear ring.
To verify whether these bar-driven gas inflows are sufficient to
maintain the turbulence in the nuclear ring, we also calculate the
turbulent energy dissipation rate _𝐸_ [�] diss, defined as


�
_𝐸_ diss ≈ _𝑀_ NR ⟨ _𝜎_ NR ⟩ [3] /(2 _ℎ_ NR )

(8)
≈ 3 _._ 4 × 10 [5] M ⊙ km [2] s [−][2] yr [−][1] _,_


(e.g. Mac Low & Klessen 2004), where _𝑀_ NR ≈ 1 _._ 2 × 10 [9] M ⊙,
⟨ _𝜎_ NR ⟩≈ 17 km s [−][1] and _ℎ_ NR ≈ 14 pc are the total mass,


MNRAS **000**, 1–15 (2023)

10 _Choi et al._


estimated as


_𝑡_ travel = _𝜋𝑅_ NR /( _𝑉_ c _,_ NR − Ω p _𝑅_ NR ) (9)


(Koda 2021), where _𝑉_ c _,_ NR is the circular velocity at the radius of
the nuclear ring ( _𝑉_ c _,_ NR ≈ 170 km s [−][1] ) and Ω p is the pattern speed
of the large-scale bar. The bar pattern speed of NGC 613 has never
been measured, and it is not possible to estimate it from the current
observations as they cover only the central region of the galaxy. We
can obtain a firm lower limit to the travel time by adopting Ω p = 0
in Equation 9 (yielding _𝑡_ travel ≳ 4 _._ 85 Myr), but instead we derive
the bar pattern speed by assuming that NGC 613 has a flat rotation
curve in the outer parts of the disc (i.e. around corotation) and
by adopting the dimensionless bar rotation rate and projected bar
radius measured by Seigar et al. (2018): R ≡ _𝑅_ CR / _𝑅_ bar = 1 _._ 5 ± 0 _._ 1
(where _𝑅_ CR is the bar corotation radius and _𝑅_ bar the deprojected
bar half-length) and _𝑅_ bar = 90 [′′] _._ 0 ± 4 [′′] _._ 0. This leads to a bar pattern
speed Ω p = _𝑉_ c _,_ NR /R _𝑅_ bar = 18 _._ 5 ± 1 _._ 3 km s [−][1] kpc [−][1] . In turn,
using Equation 9, this leads to a travel time _𝑡_ travel ≈ 5 _._ 0 Myr, so that
the average turbulent dissipation timescale is roughly half the travel
time between the two nodes and the turbulent dissipation timescales
of most nuclear ring clouds (92/99) are shorter than 5 _._ 0 Myr. This
implies that the turbulence of the clouds would be dissipated before
they travel from one node to the other, and therefore that turbulence
must be continuously supplied to the nuclear ring clouds (from
additional sources) to maintain the high cloud velocity dispersions.


_4.1.3_ _Other mechanisms inducing the high velocity dispersions_
_of the clouds_


As discussed in the previous section, in addition to the impact of the
bar and the nuclear ring, other mechanisms are needed to explain
the excess cloud turbulence in the central region of NGC 613.
**AGN Feedback** . NGC 613 is known to host an AGN with radio

jets (e.g. Veron-Cetty & Veron 1986; Hummelet al. 1987; Miyamoto
et al. 2017), and AGN feedback is a mechanism known to commonly
create high velocity dispersions in molecular gas (e.g. Schawinski
et al. 2009; Simionescu et al. 2018; Nesvadba et al. 2021; Ruffa
et al. 2022). Several simulations have also suggested that AGN
feedback can severely affect molecular gas near galaxy centres (e.g.
Wada et al. 2009; Mukherjee et al. 2018), and have shown that the
AGN impact is limited to several hundred parsecs in radius within
the galactic discs (but extends beyond 1 kpc perpendicularly to the
discs). In the case of NGC 613, the high Fe ii to Br _𝛾_ line flux ratio
suggests that there is an interaction between the radio jets and the
nuclear ring (Falcón-Barroso et al. 2014), but this appears limited
to only a small region of the nuclear ring (see the blue stars in
the continuum map of Figure 1). In addition, shocks due to the
interaction of the radio jets with the surrounding medium appear
to influence only the circumnuclear disc (i.e. the nucleus according
to our region definition; Miyamoto et al. 2017). Miyamoto et al.
(2017) also reported that there are only two small regions where the
shock tracer SiO(2-1) is detected near the nuclear ring, as shown
in Figure 1. Therefore, the impact of the AGN feedback on the
molecular gas in the nuclear ring and its vicinity appears limited to
small regions and thus only a portion of the NGC 613 clouds.
**Stellar** **Feedback** . Early stellar feedback can contribute to
cloud turbulence in the forms of stellar winds and the expansion
of H ii regions (e.g. Mac Low & Klessen 2004). Mazzuca et al.
(2008) measured a star-formation rate of ≈ 2 _._ 2 M ⊙ yr [−][1] using the
H _𝛼_ emission from the nuclear ring (within a radius of 400 pc) of
NGC 613. This ring was also observed in the Br _𝛾_ line using the



Very Large Telescope SINFONI integral-field spectrograph, revealing sequential star-forming clumps with an age gradient along the
nuclear ring (Böker et al. 2008; Falcón-Barroso et al. 2014). As Br _𝛾_
is predominantly produced by the dense H ii regions surrounding
young OB stars (Ho et al. 1990) and can be used to trace recent star
formation (Pasha et al. 2020), early stellar feedback is likely to affect
the molecular gas of the nuclear ring and thus drive the cloud turbulence, suggesting that it can contribute to the high cloud velocity
dispersions. Once a massive star dies, it explodes and thus injects
significant energy into its surroundings, so-called supernova (SN)
feedback. SN feedback is well known as one of the major energy
sources regulating the evolution of the interstellar medium (Mac
Low & Klessen 2004). It has in fact been suggested that SN feedback is the dominant mechanism driving the turbulence of molecular
gas (e.g. Padoan et al. 2016). Using near-infrared line diagnostic diagrams (Colina et al. 2015), Audibert et al. (2019) showed that the
nuclear ring of NGC 613 has characteristics of young stars and/or
aged (≈ 8 – 40 Myr) star-forming clumps dominated by SN. SN can
thus also contribute to the high cloud velocity dispersions present
in the nuclear ring of NGC 613.
**Accretion-driven** **turbulence** . Goldbaum et al. (2011) suggested that gas accretion, i.e. the flow of surrounding cold gas onto
a molecular cloud, and star formation feedback (in the form of
H ii region expansion) contribute roughly equally to the turbulent
kinetic energy over the lifetime of a cloud. However, in high gas
mass surface density environments, gas accretion dominates the
cloud energy budget (over star-formation feedback). As the centre
of NGC 613 has high molecular gas mass surface densities, and
there are gas inflows toward the nuclear ring via the large-scale
bar, accretion-driven turbulence is likely to contribute to the high
velocity dispersions of the clouds. Indeed, the molecular gas mass
and surface density of the clouds in the nuclear ring are higher than
those of the clouds in the dust lanes, implying there is gas accretion
that can induce cloud turbulence in the nuclear ring. We note that
accretion-driven turbulence is distinct from turbulence driven by
bar-driven gas inflows in terms of both physical scale and location.
The former occurs at the cloud scale and can take place at any
position in and around the nuclear ring, while the latter indicates
an energy transfer from large-scale gas inflows to the nuclear ring
molecular gas and can only occur near the nodes.
**Cloud-cloud collisions** . Cloud-cloud collisions have been proposed as another mechanism that can limit cloud lifetimes and act
as a source of turbulence within clouds (e.g. Tan 2000; Li et al.
2018; Wu et al. 2018). For instance, using simulations Wu et al.
(2018) suggested that GMC collisions can create and maintain large
turbulence within dense gas structures. To assess whether cloudcloud collisions are important in the nuclear ring of NGC 613,
we calculate the cloud-cloud collision timescale. This can be es
timated as _𝑡_ coll = 1/ _𝑁_ mc _𝐷_ c _𝜎_ cc (Koda et al. 2006), where _𝑁_ mc is
the cloud number surface density, _𝐷_ c is the mean cloud diameter
(2 ⟨ _𝑅_ c ⟩≈ 76 pc; see Table 3) and _𝜎_ cc is the cloud-cloud velocity dispersion, generally assumed to be ≈ 10 km s [−][1] (e.g. Koda
et al. 2006; Inutsuka et al. 2015). To calculate _𝑁_ mc, we consider
the 99 nuclear ring clouds within an elliptical annulus of inner
semi-major axis length 240 pc, outer semi-major axis length 385 pc
and ellipticity 0 _._ 3, yielding _𝑁_ mc ≈ 470 kpc [−][2] . Overall, this yields
_𝑡_ coll ≈ 3 _._ 0 Myr, more than half of the cloud travel time between
the nodes (ratio of ≈ 0 _._ 6). However, Li et al. (2018) suggested that
cloud-cloud collisions play an important role in driving cloud turbulence only when collisions are more frequent (collision to orbital
timescale ratio ranging from 0 _._ 1 to 0 _._ 2). Thus, while cloud-cloud
collision can contribute to cloud turbulence, they are not likely to be


MNRAS **000**, 1–15 (2023)

a significant source of turbulence in the nuclear ring of NGC 613.
We note that the collision timescale at the nodes should be shorter

than the estimated collision timescale above since the cloud number

density is higher at the nodes than at the arcs. Thus, cloud-cloud
collisions could be more important at the nodes than the arcs.
In summary, no potential source of turbulence appears to be
dominant over the others in the nuclear ring of NGC 613. Among
them, stellar feedback, gas accretion and cloud-cloud collisions are
all plausible sources for the elevated velocity dispersions of the
clouds and the steep size – linewidth relation. We note that all the
mechanisms suggested above can also destroy clouds depending on
their strengths. Thus, a more quantitative investigation of stellar
feedback and accretion-driven turbulence is required to better understand their impact on the turbulence of the clouds in NGC 613.


_4.1.4_ _Possible mechanisms for a steep size – linewidth relation_


Although we suggested several mechanisms that can enhance the
linewidth of the clouds in and around the nuclear ring of NGC 613,
it is still unclear why those clouds show a steep size – linewidth
relation. To show a steep size – linewidth, one of two things (or
both) must happen. Either smaller clouds have lower turbulence or
larger clouds are selectively injected with more turbulence.
Firstly, the interstellar medium is highly compressible, indicating that turbulent energy may not fully cascade down to small
scales, but rather be spent on shocks and/or gas compression (e.g.
Mac Low & Klessen 2004). As a consequence, smaller clouds can
exhibit considerably lower turbulence than larger ones, resulting in
a steep size-linewidth relation. However, various numerical simulations have shown that the slope of the size-linewidth relation for
strongly compressible flows typically ranges from 0 _._ 25 to 0 _._ 5 (e.g.
Padoan et al. 2006, 2007, Schmidt et al. 2009, McKee & Ostriker
2007 and references therein) and rarely exceeds this range. In addition, Cen (2021) recently suggested a new size – linewidth relation
with a slope of 0 _._ 6 from a theoretical approach, which is still not
sufficiently high to explain our findings. Kauffmann et al. (2017)
also attempted to suggest plausible explanations for an unusually
steep size-linewidth relation of CMZ clouds. They suggested that
the prevalence of shocks, possibly resulting from cloud-cloud collisions and evidenced by SiO emission, could contribute to elevated
velocity dispersions. They also proposed stellar feedback and intermittent activity from Sgr A [∗] as potential additional mechanisms
contributing to elevated linewidths and a steep size-linewidth relation. Nevertheless, the absence of a dominant mechanism and the
lack of theoretical arguments explaining the steep size-linewidth
remain unaddressed. Therefore, whether the turbulent energy of
molecular gas in and around the nuclear ring cascades down to
small scales less efficiently (and the mechanisms that cause this)
remains to be clarified.

Another way to create a steep size – linewidth relation is to
inject more turbulence into the larger clouds. All the mechanisms
suggested above can increase the velocity dispersions of clouds of
all sizes, but each mechanism may have a characteristic injection
scale, that can in turn lead to a steep size – linewidth relation. This
is thus another aspect that requires further study.


**4.2** **Cloud virialisation** [︁]


We assess the dynamical state of a cloud using the virial parameter



_WISDOM XXI. GMCs in NGC 613_ 11


Here, _𝐾_ and _𝑈_ are the kinetic and gravitational potential energies,
respectively, and _𝑏_ s is a geometrical factor that depends on the internal structure of a cloud, for which we adopt _𝑏_ s = 1/5 assuming the
clouds are homogeneous and spherical. Note that we have customequalityarily defined the virial massof Equation 10. The _𝑀_ virial obs _,_ vir theorem≡ _𝜎_ obs [2] _,_ los states _[𝑅]_ [c] [/(] that _[𝑏]_ [s] _[𝐺]_ [)] a [ in the last] turbulent
pressure-dominated cloud would collapse if _𝛼_ obs _,_ vir _<_ 1 (or equivalently, _𝑀_ gas _>_ _𝑀_ obs _,_ vir ) while it must be either confined by external
pressure and/or magnetic fields or disperse when _𝛼_ obs _,_ vir ≳ 2.
The top panel of Figure 7 shows the virial masses of the resolved clouds of NGC 613 (calculated using the observed velocity
dispersion _𝜎_ obs _,_ los ; see Equation 10) as a function of their gas
masses, overlaid with the best-fitting power law (black solid line).
The black dashed and black dotted lines indicate _𝛼_ obs _,_ vir = 1 and
_𝛼_ obs _,_ vir = 2, respectively. The best-fitting power law is


[︁]



log _𝑀_ obs _,_ vir
� M ⊙


[︁]



= (0 _._ 94 ± 0 _._ 03) log _𝑀_ gas
� � M ⊙


[︁]



+ (0 _._ 58 ± 0 _._ 02) _,_ (11)
�


[︁]




[︁]


_𝜎_ [2]
obs _,_ los _[𝑅]_ [c]

[2] _[𝐾]_

| _𝑈_ | [=] _𝑏_ s _𝐺𝑀_




[︁]


_[,]_

_._ (10)
_𝑀_ gas




[︁]


_𝛼_ obs _,_ vir ≡ [2] _[𝐾]_




[︁]


obs _,_ los [c] ≡ _[𝑀]_ [obs] _[,]_ [vir]

_𝑏_ s _𝐺𝑀_ gas _𝑀_ gas



implying that the resolved clouds of NGC 613 are virialised on

average.
To investigate the virialisation of the resolved clouds of
NGC 613 further, we analyse the distributions of _𝛼_ obs _,_ vir for all the
GMCs of NGC 613 and those in each region individually, as shown
in the middle panel of Figure 7. The mean (median) of _𝛼_ obs _,_ vir is
1 _._ 66 (1 _._ 58), indicating that on average the clouds are marginally
bound (black solid line). However, _𝛼_ obs _,_ vir has a broad distribution
and about 59% of the clouds (93/158) lie between _𝛼_ obs _,_ vir = 1 and
_𝛼_ obs _,_ vir = 2. About 23% of the clouds (36/158) have _𝛼_ obs _,_ vir _>_ 2,
while about 18% of the clouds (29/158) have _𝛼_ obs _,_ vir _<_ 1. Among
the four regions, clouds in the arcs tend to have smaller virial parameters (mean of 1 _._ 39) than those of the other three regions (mean
of 1 _._ 71 to 1 _._ 84). This indicates that the clouds in the arcs are more
strongly gravitationally bound than those in the other three regions.
However, we note that the virial parameters scale inversely with
the CO-to-molecule conversion factor _𝑋_ CO . For instance, Sato et al.
(2021) used _𝑋_ CO = 0 _._ 8 × 10 [20] cm [−][2] (K km s [−][1] ) [−][1] and a different
cloud finding algorithm (Dendrogram; Rosolowsky et al. 2008)
for NGC 613, yielding a mean cloud virial parameter of ≈ 2 _._ 8,
approximately 70% larger than ours. It is worth noting that our
analysis is more elaborate than theirs, possibly also contributing to
the observed differences. Nevertheless, similar to our results, they
also reported that the clouds in the arcs tend to have virial parameters lower than those in the dust lanes. Interestingly, low conversion
factors have been reported in galaxy centres (e.g. Sandstrom et al.
2013), and Teng et al. (2022, 2023) reported that the conversion
factors of barred galaxy centres are 4 – 15 times lower than that
of the MWd. These results imply that the virial parameters of the
clouds of NGC 613 could be at least four times larger than currently calculated, which would in turn imply that the clouds are
not gravitationally bound but either confined by external forces or
short-lived.

The bottom panel of Figure 7 shows the correlation between
molecular gas mass surface density (Σ gas ) and _𝜎_ obs _,_ los _𝑅_ c [−][1][/][2] for
all the resolved clouds of NGC 613, providing another perspective
to assess the dynamical states of the clouds (Field et al. 2011).
Regardless of how well clouds obey the size – linewidth relation, if the clouds are virialised they should be clustered around
_𝜎_ obs _,_ los _𝑅_ c [−][1][/][2] = ~~[√]~~ [︁] _𝜋𝛼_ obs _,_ vir _𝐺𝑏_ s Σ gas, indicated by the black dashed
( _𝛼_ obs _,_ vir = 1) and black dotted ( _𝛼_ obs _,_ vir = 2) diagonal lines. If the
clouds are not virialised ( _𝛼_ obs _,_ vir ≳ 2) but are nevertheless longlived, external pressure ( _𝑃_ ext ) should be important to confine them
(otherwise the clouds are likely transient structures). In this case,




[︁]


MNRAS **000**, 1–15 (2023)

12 _Choi et al._


**Figure** **7.** **Top** : Molecular gas mass – virial mass relation for the resolved
clouds of the nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow)
of NGC 613. The black solid line shows the best-fitting power-law relation,
while the black dashed and black dotted lines indicate _𝛼_ obs _,_ vir = 1 and
_𝛼_ obs _,_ vir = 2, respectively. **Middle** : Distribution of log _𝛼_ obs _,_ vir, where the
black solid line shows the mean virial parameter ⟨ _𝛼_ obs _,_ vir ⟩ = 1 _._ 66, and the
black dashed and black dotted lines indicate _𝛼_ obs _,_ vir = 1 and _𝛼_ obs _,_ vir = 2,
respectively. **Bottom** : Relation between molecular gas mass surface density
and _𝜎_ obs _,_ los _𝑅_ c [−][1][/][2] for the same clouds. The black dashed and black dotted
diagonal lines show the solutions for a simple (i.e. _𝛼_ obs _,_ vir = 1) and a
marginal (i.e. _𝛼_ obs _,_ vir = 2) virial equilibrium, respectively. The V-shaped
black solid curves show solutions for pressure-bound clouds at different
pressures ( _𝑃_ ext / _𝑘_ B = 10 [5], 10 [6], 10 [7] and 10 [8] K cm [−][3] ). A typical uncertainty
is shown as a black cross in the bottom right of the panel.



(Field et al. 2011).
The molecular gas mass surface densities of the resolved clouds
of NGC 613 are broadly distributed, varying by 1 _._ 5 orders of magnitude, and are positively correlated with _𝜎_ obs _,_ los _𝑅_ c [−][1][/][2] . Given the
uncertainties, some clouds with _𝛼_ obs _,_ vir _>_ 2 distributed across the
V-shaped curves do seem to be bound by high external pressures
(10 [6] ≲ _𝑃_ ext / _𝑘_ B ≲ 10 [8] K cm [−][3], if indeed they are bound). However, the majority of the clouds are located between the _𝛼_ obs _,_ vir = 2
and _𝛼_ obs _,_ vir = 1 lines, implying that external pressure is unlikely
to be important to constrain them. However, we again note that this
is impacted by the uncertainties of the CO-to-molecule conversion
factor. For example, if we adopt a conversion factor 4 times lower,
the cloud molecular gas mass surface densities and virial parameters are in turn 4 times lower. Should that be the case, the clouds
of NGC 613 would be unbound (or pressure-bound), similar to the
states of the CMZ clouds.

In summary, Figure 6 shows that the size – linewidth relation
of the resolved clouds of NGC 613 has a slope that is at least
as steep as that of CMZ clouds (or much steeper if we adopt the
ODR algorithm). For NGC 613, bar-driven gas inflows alone are not
sufficient to explain the increased linewidths of the clouds, and other
processes such as stellar feedback, cloud-cloud collisions and/or gas
accretion must also contribute. Most of the clouds are marginally
gravitationally bound (⟨ _𝛼_ obs _,_ vir ⟩≈ 1 _._ 7 with _𝑋_ CO of the MW) and
do not seem affected by external pressure (Figure 7).


**4.3** **Nuclear ring clouds**


As discussed in the previous section (Section 4.1), gas inflows driven
by the bar are likely to have an impact on the cloud characteristics
within the nuclear ring, an effect that has been explored in some
previous studies (e.g. Salak et al. 2016; Sato et al. 2021; Choi
et al. 2023). Additionally, some galaxies with a nuclear ring show
an azimuthal stellar age gradient within it (Mazzuca et al. 2008).
Therefore, it is important to investigate whether the nodes have any
influence on the cloud properties and whether the cloud properties
change with azimuthal angle along the nuclear ring of NGC 613.
Figure 8 presents the number of clouds and other cloud properties as
a function of azimuthal angle (measured counterclockwise from the
western node): virial parameter, gas mass, velocity dispersion, size
and gas mass surface density. Interestingly, the number of clouds
decreases from one node to the other (see panel (a) of Figure 8), yet
other cloud properties show no discernible trend and exhibit large
scatters as a function of azimuthal angle (see panels (b) – (f) of
Figure 8).
In our previous work, we reported an analogous trend in
NGC 5806 (see Figure 12 of Choi et al. 2023), i.e. the number
of clouds decreases gradually from one node to the other but none
of the cloud properties varies significantly along the nuclear ring.
We speculated that these trends are due to the gas inflows along the
large-scale bar inducing violent collisions at the nodes, leading to the
formation of many clouds, which are then gradually destroyed while
moving along the nuclear ring. We also suggested that cloud-cloud
collisions, shear and stellar feedback are plausible mechanisms for
the changes of cloud number and properties along the nuclear ring,
as their timescales appear to be shorter than the estimated cloud


MNRAS **000**, 1–15 (2023)



the clouds will be distributed around the black solid V-shape curves
in the bottom panel of Figure 7:



_𝑃_ ext

[4] (12)

3 Σ gas



_𝜎_ obs _,_ los _𝑅_ c [−][1][/][2] =



√︄



_𝜋𝛼_ obs _,_ vir _𝐺_ Σ gas



_𝐺_ Σ gas

+ [4]
5 3

_WISDOM XXI. GMCs in NGC 613_ 13


**Figure 8.** Properties of the clouds in the nuclear ring (both arcs and nodes) of NGC 613, as a function of the azimuthal angle (measured counter-clockwise from
the western node). From left to right, top to bottom: number of resolved clouds, virial parameter, molecular gas mass, velocity dispersion, size and molecular
gas mass surface density. The red data points are averages in azimuthal bins of width 30 [◦], while the red error bars indicate the 1 _𝜎_ scatter within each bin.
Black vertical dashed lines indicate the positions of the two nodes, and black vertical dotted lines indicate the boundary between two adjacent zones of each
half of the nuclear ring (top-left panel only), used to calculate Equation 14.



lifetimes in NGC 5806. It is therefore interesting to verify whether
the same reasoning applies to NGC 613.
To compare the different mechanisms, we first calculate the
characteristic cloud lifetime, adopting the same method used in our
previous work (Choi et al. 2023). The azimuthal variation of the
number of clouds depends on the characteristic cloud lifetime, that
can be estimated as


1

_𝑡_ lifetime = _[𝑡]_ [travel] _,_ (13)

2 _𝐹_ lost


where _𝐹_ lost is the fraction of clouds lost (i.e. the decline of the number of clouds) as they move between the two nodes. This argument is
similar to that introduced by Meidt et al. (2015) to estimate the cloud
lifetimes in the inter-arm region of a spiral galaxy. They suggested
that the number changes as the cloud travels and evolves from one
region to another, and that the cloud lifetime can be inferred from
this. This formalism relies on a number of assumptions: 1) cloud
formation is negligible between the two zones and 2) clouds follow
circular paths. In the case of NGC 613, we assume that most cloud
formation occurs near the nodes. There are non-circular motions,
but they are neither significant nor relevant in the nuclear ring. The
fraction of clouds lost between the two nodes is


[−] _[𝑁]_ [II]
_𝐹_ lost = _[𝑁]_ [I] _,_ (14)

_𝑁_ I


where _𝑁_ I and _𝑁_ II are the number of clouds in two adjacent zones
that span equal ranges of azimuth (see panel (a) of Figure 8). We
count the numbers of clouds in the first half of the nuclear ring
(from the western node to the eastern node), yielding _𝑁_ I = 27 and
_𝑁_ II = 8 (and thus _𝐹_ lost = 0 _._ 67), while in the second half (from the
eastern node to the western node) this yields _𝑁_ I = 35 and _𝑁_ II = 24
(and thus _𝐹_ lost = 0 _._ 31).


MNRAS **000**, 1–15 (2023)



Combined with our estimated travel time, these two fractions of
lost clouds yield two characteristic cloud lifetime estimates, that we
take as a range, _𝑡_ lifetime = 3 _._ 7 – 8 _._ 1 Myr. This cloud lifetime is larger
than that of the clouds in the CMZ (1 – 4 Myr; e.g. Kruĳssen et al.
2015; Jeffreson et al. 2018), but is smaller than that of the clouds in
the LMC (≈ 11 Myr; Ward et al. 2022), the central 3 _._ 5 kpc radius
of M 51 (20 – 50 Myr; Meidt et al. 2015), nearby galaxies (5 –
100 Myr; Jeffreson & Kruĳssen 2018; Chevance et al. 2020; Kim
et al. 2022), between spiral arms of disc galaxies (≈ 100 Myr; e.g.
Koda et al. 2009) and NGC 5806 (≈ 7 _._ 4 Myr; Choi et al. 2023).


Prior to making a comparison of the estimated cloud lifetime with other timescales, we calculate the shear timescale, which
can also regulate cloud’s lifetimes, especially in galaxy centres
where strong shear can lead to cloud disruption and/or mass loss
(e.g. Meidt et al. 2015; Jeffreson & Kruĳssen 2018). We estimate the shear timescale as _𝑡_ shear = 1/2 _𝐴_ (Liu et al. 2021), where



≈ 0 _._ 14 km s [−][1] pc [−][1] is Oort’s con�



_𝐴_ ≡ [1]

2



_𝑉_ c ( _𝑅_ NR )

_𝑅_ NR

�



( _𝑅_ NR ) − _[𝑑𝑉]_ [c]

_𝑅_ NR _𝑑𝑅_



_𝑑𝑅_



��� _𝑅_ NR



stant evaluated at the nuclear ring using the aforementioned rotation
curve, yielding _𝑡_ shear ≈ 3 _._ 5 Myr.


Consequently, these other timescales ( _𝑡_ coll ≈ 3 Myr and
_𝑡_ shear ≈ 3 _._ 5 Myr) tend to be shorter than the characteristic cloud lifetime ( _𝑡_ lifetime = 3 _._ 7 – 8 _._ 1 Myr), indicating that they could also play
a role and affect the number of clouds and other cloud properties
along the nuclear ring, in addition to the stellar feedback discussed
previously. It is, therefore, still unclear which mechanism primarily
regulates the cloud lifetimes and causes the number of clouds to
decrease with azimuth while other cloud properties remain roughly
constant. Quantifying the impact of each of these mechanisms on
the nuclear ring clouds will be important in the future.

14 _Choi et al._


**5** **SUMMARY**


We presented high-resolution (24 × 18 pc [2] ) [12] CO(1-0) ALMA observations of the barred spiral galaxy NGC 613. We identified 356
GMCs, 158 of which are spatially and spectrally resolved, with a
modified version of cpropstoo. We investigated the cloud properties and scaling relations and explored potential explanations for
our findings. Our results can be summarised as follows:


(i) The GMCs of NGC 613 have sizes (15 – 75 pc) that are
comparable to, but molecular gas masses (3 × 10 [5] – 5 × 10 [7] M ⊙ ),
velocity dispersions (2 – 36 km s [−][1] ) and molecular gas mass surface
densities (100 – 6000 M ⊙ pc [−][2] ) that are larger than those of the
Milky Way disc and Local Group galaxy GMCs (Figure 3).

(ii) The GMCs sizes are similar across the different regions of
the galaxy (nucleus, arcs, nodes and dust lanes), but the GMCs in
the dust lanes have molecular gas masses, velocity dispersions and
gas mass surface densities smaller than those of the GMCs in the
other regions. The GMCs in the arcs tend to have gas masses and
gas mass surface densities larger than those of the GMCs in the
other regions.

(iii) The GMCs of NGC 613 have a steep size – linewidth relation
( _𝜎_ obs _,_ los ∝ _𝑅_ c [0] _[.]_ [77][±][0] _[.]_ [11] ; Figure 6).
(iv) The kinetic energy injection rate from the gas inflows driven
by the large-scale bar is smaller than the turbulent energy dissipation
rate, and the turbulence dissipation timescale is shorter than the
cloud travel time, suggesting that additional sources of turbulence
are required beside the gas inflows.

(v) AGN feedback has a limited impact on the cloud turbulence,
while stellar feedback, gas accretion and cloud-cloud collisions are
plausible turbulence sources. Gas inflows into the nuclear ring from
the dust lanes remain one of the likely explanations for the clouds’
high velocity dispersions. However, quantitative analyses to assess
the relative importance of the different mechanisms are required.

(vi) The GMCs of NGC 613 are marginally gravitationally bound
(⟨ _𝛼_ obs _,_ vir ⟩≈ 1 _._ 7 with _𝑋_ CO of the MW), and the GMCs in the arcs
tend to have smaller virial parameters than the GMCs in the other
regions.

(vii) The number of clouds decreases azimuthally downstream
from the nodes within the nuclear ring (Section 4.3). By tracking
cloud disruption through GMC number statistics, we estimate the
characteristic cloud lifetime to be between 3 and 8 Myr. This tends
to be larger than the estimated timescales of cloud-cloud collisions,
shear and/or stellar feedback (≈ 3 Myr), suggesting that any of
those could also contribute to the destruction of the clouds within

the nuclear ring.


As seen in this work, GMCs in nuclear rings clearly show
distinct size-linewidth relations compared to those in other local
environments when inspected in a similar manner. However, GMC
properties and in particular the slopes of scaling relations can change
depending on how individual clouds are defined (e.g. Pan et al. 2015;
Dobbs et al. 2019). Therefore, in a follow-up study, we will compare
different cloud-finding algorithms to further validate our results
(Choi et al. in prep.). Lastly, it is worth mentioning that we are
currently analysing high spatial resolution numerical simulations
of a galactic nuclear ring to gain physical insights into the high
velocity dispersions of the GMCs, while also collecting more GMC
observations of comparable quality for similar objects.



**ACKNOWLEDGEMENTS**


We thank the anonymous referee for helpful and constructive comments and Dr. Chang-Goo Kim for useful discussions and comments. WC and AC acknowledge support by the National Research
Foundation of Korea (NRF), grant Nos. 2022R1A2C100298212,
and 2022R1A6A1A03053472. This work was also supported by
National R&D Program through the National Research Foundation of Korea (NRF) funded by the Korea government (Ministry
of Science and ICT) (RS-2022-00197685). LL was supported by a
Hintze Fellowship, funded by the Hintze Family Charitable Foundation, and by a DAWN Fellowship, funded by the Danish National Research Foundation under grant No. 140. MB was supported by UK Science and Technology Facilities Council (STFC)
consolidated grant “Astrophysics at Oxford” ST/K00106X/1 and
ST/W000903/1. TAD and IR acknowledges support from the STFC
grants ST/S00033X/1 and ST/W000830/1. JG gratefully acknowledges financial support from the Swiss National Science Foundation
(grant No. CRSII5 193826). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01671.S. ALMA is a
partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), NSC and ASIAA
(Taiwan) and KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ. This research has made use of the
NASA/IPAC Extragalactic Database (NED), which is operated by
the Jet Propulsion Laboratory, California Institute of Technology,
under contract with the National Aeronautics and Space Administration.


**DATA AVAILABILITY**


The data underlying this article are available in the ALMA archive
( `[https://almascience.eso.org/asax/](https://almascience.eso.org/asax/)` ) under project code
2017.1.01671.S. All higher-level data products will be shared upon
reasonable request.


**REFERENCES**


[Agüero M. P., Díaz R. J., Dottori H., 2016, International Journal of Astron-](http://dx.doi.org/10.4236/ijaa.2016.63018)
[omy and Astrophysics, 6, 219](http://dx.doi.org/10.4236/ijaa.2016.63018)
[Athanassoula E., 1992, MNRAS, 259, 345](http://dx.doi.org/10.1093/mnras/259.2.345)

[Audibert A., et al., 2019, A&A, 632, A33](http://dx.doi.org/10.1051/0004-6361/201935845)

[Bewketu Belete A., et al., 2021, A&A, 654, A24](http://dx.doi.org/10.1051/0004-6361/202140492)
Böker T., Falcon-Barroso J., Knapen J. H., Schinnerer E., Allard E., Ryder
[S., 2007, Stellar Populations as Building Blocks of Galaxies, 241, 497](http://dx.doi.org/10.1017/S1743921307008873)
Böker T., Falcón-Barroso J., Schinnerer E., Knapen J. H., Ryder S., 2008,

[AJ, 135, 479](http://dx.doi.org/10.1088/0004-6256/135/2/479)
[Bolatto A. D., Leroy A. K., Rosolowsky E., Walter F., Blitz L., 2008, ApJ,](http://dx.doi.org/10.1086/591513)

[686, 948](https://ui.adsabs.harvard.edu/abs/2008ApJ...686..948B)
[Cen R., 2021, ApJ, 906, L4](http://dx.doi.org/10.3847/2041-8213/abcecb)
[Chevance M., et al., 2020, MNRAS, 493, 2872](http://dx.doi.org/10.1093/mnras/stz3525)

[Choi W., et al., 2023, MNRAS, 522, 4078](http://dx.doi.org/10.1093/mnras/stad1211)

[Colina L., et al., 2015, A&A, 578, A48](http://dx.doi.org/10.1051/0004-6361/201425567)
[Colombo D., et al., 2014, ApJ, 784, 3](http://dx.doi.org/10.1088/0004-637X/784/1/3)
[Combes F., et al., 2019, A&A, 623, A79](http://dx.doi.org/10.1051/0004-6361/201834560)
Cuomo V., Lopez Aguerri J. A., Corsini E. M., Debattista V. P., Méndez[Abreu J., Pizzella A., 2019, A&A, 632, A51](http://dx.doi.org/10.1051/0004-6361/201936415)
[Dame T. M., 2011, arXiv e-prints, p. arXiv:1101.1499](https://ui.adsabs.harvard.edu/abs/2011arXiv1101.1499D)
[Davies R. L., et al., 2017, MNRAS, 470, 4974](http://dx.doi.org/10.1093/mnras/stx1559)
Dobbs C. L., Rosolowsky E., Pettitt A. R., Braine J., Corbelli E., Sun J.,
[2019, MNRAS, 485, 4997](http://dx.doi.org/10.1093/mnras/stz674)
[Donovan Meyer J., et al., 2012, ApJ, 744, 42](http://dx.doi.org/10.1088/0004-637X/744/1/42)


MNRAS **000**, 1–15 (2023)

[Elmegreen B. G., Scalo J., 2004, ARA&A, 42, 211](http://dx.doi.org/10.1146/annurev.astro.41.011802.094859)
Falcón-Barroso J., Böker T., Schinnerer E., Knapen J. H., Ryder S., 2008,

[Formation and Evolution of Galaxy Bulges, 245, 177](http://dx.doi.org/10.1017/S1743921308017584)
Falcón-Barroso J., Ramos Almeida C., Böker T., Schinnerer E., Knapen
[J. H., Lançon A., Ryder S., 2014, MNRAS, 438, 329](http://dx.doi.org/10.1093/mnras/stt2189)
[Falgarone E., Phillips T. G., Walker C. K., 1991, ApJ, 378, 186](http://dx.doi.org/10.1086/170419)
[Field G. B., Blackman E. G., Keto E. R., 2011, MNRAS, 416, 710](http://dx.doi.org/10.1111/j.1365-2966.2011.19091.x)
[Fukui Y., et al., 2008, ApJS, 178, 56](http://dx.doi.org/10.1086/589833)
García-Burillo S., Martín-Pintado J., Fuente A., Neri R., 2001, [ApJ,](http://dx.doi.org/10.1086/338391) [563,](https://ui.adsabs.harvard.edu/abs/2001ApJ...563L..27G)

[L27](https://ui.adsabs.harvard.edu/abs/2001ApJ...563L..27G)

[Goldbaum N. J., Krumholz M. R., Matzner C. D., McKee C. F., 2011, ApJ,](http://dx.doi.org/10.1088/0004-637X/738/1/101)

[738, 101](https://ui.adsabs.harvard.edu/abs/2011ApJ...738..101G)
[Goulding A. D., Alexander D. M., 2009, MNRAS, 398, 1165](http://dx.doi.org/10.1111/j.1365-2966.2009.15194.x)
[Gratier P., et al., 2012, A&A, 542, A108](http://dx.doi.org/10.1051/0004-6361/201116612)
Henshaw J. D., Barnes A. T., Battersby C., Ginsburg A., Sormani M. C.,
Walker D. L., 2023, in Inutsuka S., Aikawa Y., Muto T., Tomida K.,
Tamura M., eds, Astronomical Society of the Pacific Conference Series Vol. 534, Protostars and Planets VII. p. 83 ( `[arXiv:2203.11223](http://arxiv.org/abs/2203.11223)` ),
[doi:10.48550/arXiv.2203.11223](http://dx.doi.org/10.48550/arXiv.2203.11223)

[Heyer M. H., Brunt C. M., 2004, ApJ, 615, L45](http://dx.doi.org/10.1086/425978)
[Heyer M., Dame T. M., 2015, ARA&A, 53, 583](http://dx.doi.org/10.1146/annurev-astro-082214-122324)
[Heyer M., Krawczyk C., Duval J., Jackson J. M., 2009, ApJ, 699, 1092](http://dx.doi.org/10.1088/0004-637X/699/2/1092)
[Hirota A., et al., 2018, PASJ, 70](http://dx.doi.org/10.1093/pasj/psy071)
[Ho P. T. P., Beck S. C., Turner J. L., 1990, ApJ, 349, 57](http://dx.doi.org/10.1086/168293)
[Hughes A., et al., 2013, ApJ, 779, 46](http://dx.doi.org/10.1088/0004-637X/779/1/46)
[Hummel E., Jorsater S., 1992, A&A, 261, 85](https://ui.adsabs.harvard.edu/abs/1992A&A...261...85H)
[Hummel E., Jorsater S., Lindblad P. O., Sandqvist A., 1987, A&A, 172, 51](https://ui.adsabs.harvard.edu/abs/1987A&A...172...51H)
[Inutsuka S., Inoue T., Iwasaki K., Hosokawa T., 2015, A&A, 580, A49](http://dx.doi.org/10.1051/0004-6361/201425584)
[Jeffreson S. M. R., Kruĳssen J. M. D., 2018, MNRAS, 476, 3688](http://dx.doi.org/10.1093/mnras/sty594)
Jeffreson S. M. R., Kruĳssen J. M. D., Krumholz M. R., Longmore S. N.,
[2018, MNRAS, 478, 3380](http://dx.doi.org/10.1093/mnras/sty1154)
Kauffmann J., Pillai T., Zhang Q., Menten K. M., Goldsmith P. F., Lu X.,
[Guzmán A. E., 2017, A&A, 603, A89](http://dx.doi.org/10.1051/0004-6361/201628088)
[Kelly B. C., 2007, ApJ, 665, 1489](http://dx.doi.org/10.1086/519947)
[Kim J., et al., 2022, MNRAS, 516, 3006](http://dx.doi.org/10.1093/mnras/stac2339)
Koda J., 2021, Research Notes of the [American](http://dx.doi.org/10.3847/2515-5172/ac2d34) Astronomical Society, [5,](https://ui.adsabs.harvard.edu/abs/2021RNAAS...5..222K)

[222](https://ui.adsabs.harvard.edu/abs/2021RNAAS...5..222K)

[Koda J., Sawada T., Hasegawa T., Scoville N. Z., 2006, ApJ, 638, 191](http://dx.doi.org/10.1086/498640)
[Koda J., et al., 2009, ApJ, 700, L132](http://dx.doi.org/10.1088/0004-637X/700/2/L132)
[Kolmogorov A., 1941, Akademiia Nauk SSSR Doklady, 30, 301](https://ui.adsabs.harvard.edu/abs/1941DoSSR..30..301K)
[Kruĳssen J. M. D., Dale J. E., Longmore S. N., 2015, MNRAS, 447, 1059](http://dx.doi.org/10.1093/mnras/stu2526)
[Larson R. B., 1981, MNRAS, 194, 809](http://dx.doi.org/10.1093/mnras/194.4.809)
[Lequeux J., 2005, The Interstellar Medium, doi:10.1007/b137959.](http://dx.doi.org/10.1007/b137959. )
[Leroy A. K., et al., 2015, ApJ, 801, 25](http://dx.doi.org/10.1088/0004-637X/801/1/25)
[Li Q., Tan J. C., Christie D., Bisbas T. G., Wu B., 2018, PASJ, 70, S56](http://dx.doi.org/10.1093/pasj/psx136)
[Lin D. N. C., Pringle J. E., 1987, MNRAS, 225, 607](http://dx.doi.org/10.1093/mnras/225.3.607)
Liu L., Bureau M., Blitz L., Davis T. A., Onishi K., Smith M., North E.,
[Iguchi S., 2021, MNRAS, 505, 4048](http://dx.doi.org/10.1093/mnras/stab1537)
[Liu L., et al., 2022, MNRAS, 517, 632](http://dx.doi.org/10.1093/mnras/stac2287)

Liu L., et al., 2023, MNRAS, submitted
[Mac Low M.-M., Klessen R. S., 2004, Reviews of Modern Physics, 76, 125](http://dx.doi.org/10.1103/RevModPhys.76.125)
[Maeda F., Ohta K., Fujimoto Y., Habe A., 2020, MNRAS, 493, 5045](http://dx.doi.org/10.1093/mnras/staa556)
[Mazzuca L. M., Knapen J. H., Veilleux S., Regan M. W., 2008, ApJS, 174,](http://dx.doi.org/10.1086/522338)

[337](https://ui.adsabs.harvard.edu/abs/2008ApJS..174..337M)

[McKee C. F., Ostriker E. C., 2007, ARA&A, 45, 565](http://dx.doi.org/10.1146/annurev.astro.45.051806.110602)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in
Shaw R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific
Conference Series Vol. 376, Astronomical Data Analysis Software and
Systems XVI. p. 127
[Meidt S. E., et al., 2015, ApJ, 806, 72](http://dx.doi.org/10.1088/0004-637X/806/1/72)
Miyamoto Y., Nakai N., Seta M., Salak D., Nagai M., Kaneko H., 2017,

[PASJ, 69, 83](http://dx.doi.org/10.1093/pasj/psx076)
Miyamoto Y., Seta M., Nakai N., Watanabe Y., Salak D., Ishii S., 2018,

[PASJ, 70, L1](http://dx.doi.org/10.1093/pasj/psy016)
Mogotsi K. M., de Blok W. J. G., Caldú-Primo A., Walter F., Ianjamasi[manana R., Leroy A. K., 2016, AJ, 151, 15](http://dx.doi.org/10.3847/0004-6256/151/1/15)
Mukherjee D., Bicknell G. V., Wagner A. Y., Sutherland R. S., Silk J., 2018,

[MNRAS, 479, 5544](http://dx.doi.org/10.1093/mnras/sty1776)


MNRAS **000**, 1–15 (2023)



_WISDOM XXI. GMCs in NGC 613_ 15


[Muller E., et al., 2010, ApJ, 712, 1248](http://dx.doi.org/10.1088/0004-637X/712/2/1248)
[Nesvadba N. P. H., et al., 2021, A&A, 654, A8](http://dx.doi.org/10.1051/0004-6361/202140544)
[Oka T., Hasegawa T., Hayashi M., Handa T., Sakamoto S., 1998, ApJ, 493,](http://dx.doi.org/10.1086/305133)

[730](https://ui.adsabs.harvard.edu/abs/1998ApJ...493..730O)

Oka T., Hasegawa T., Sato F., Tsuboi M., Miyazaki A., Sugimoto M., 2001,

[ApJ, 562, 348](http://dx.doi.org/10.1086/322976)
[Padoan P., Juvela M., Kritsuk A., Norman M. L., 2006, ApJ, 653, L125](http://dx.doi.org/10.1086/510620)
[Padoan P., Nordlund Å., Kritsuk A. G., Norman M. L., Li P. S., 2007, ApJ,](http://dx.doi.org/10.1086/516623)

[661, 972](https://ui.adsabs.harvard.edu/abs/2007ApJ...661..972P)
[Padoan P., Pan L., Haugbølle T., Nordlund Å., 2016, ApJ, 822, 11](http://dx.doi.org/10.3847/0004-637X/822/1/11)
Pan H.-A., Fujimoto Y., Tasker E. J., Rosolowsky E., Colombo D., Benincasa
[S. M., Wadsley J., 2015, MNRAS, 453, 3082](http://dx.doi.org/10.1093/mnras/stv1843)
[Pasha I., Leja J., van Dokkum P. G., Conroy C., Johnson B. D., 2020, ApJ,](http://dx.doi.org/10.3847/1538-4357/aba0b1)

[898, 165](https://ui.adsabs.harvard.edu/abs/2020ApJ...898..165P)
Rice T. S., Goodman A. A., Bergin E. A., Beaumont C., Dame T. M., 2016,

[ApJ, 822, 52](http://dx.doi.org/10.3847/0004-637X/822/1/52)
[Rosolowsky E., 2007, ApJ, 654, 240](http://dx.doi.org/10.1086/509249)
[Rosolowsky E., Leroy A., 2006, PASP, 118, 590](http://dx.doi.org/10.1086/502982)
[Rosolowsky E., Engargiola G., Plambeck R., Blitz L., 2003, ApJ, 599, 258](http://dx.doi.org/10.1086/379166)
[Rosolowsky E., Keto E., Matsushita S., Willner S. P., 2007, ApJ, 661, 830](http://dx.doi.org/10.1086/516621)
[Rosolowsky E. W., Pineda J. E., Kauffmann J., Goodman A. A., 2008, ApJ,](http://dx.doi.org/10.1086/587685)

[679, 1338](https://ui.adsabs.harvard.edu/abs/2008ApJ...679.1338R)
[Rosolowsky E., et al., 2021, MNRAS, 502, 1218](http://dx.doi.org/10.1093/mnras/stab085)
Ruffa I., Prandoni I., Davis T. A., Laing R. A., Paladino R., Casasola V.,
[Parma P., Bureau M., 2022, MNRAS, 510, 4485](http://dx.doi.org/10.1093/mnras/stab3541)
[Sakamoto K., Okumura S. K., Ishizuki S., Scoville N. Z., 1999, ApJ, 525,](http://dx.doi.org/10.1086/307910)
[691](https://ui.adsabs.harvard.edu/abs/1999ApJ...525..691S)

[Salak D., Nakai N., Hatakeyama T., Miyamoto Y., 2016, ApJ, 823, 68](http://dx.doi.org/10.3847/0004-637X/823/1/68)
[Sandstrom K. M., et al., 2013, ApJ, 777, 5](http://dx.doi.org/10.1088/0004-637X/777/1/5)
Sato K., Miyamoto Y., Kuno N., Salak D., Wagner A. Y., Seta M., Nakai N.,
[2021, PASJ, 73, 1019](http://dx.doi.org/10.1093/pasj/psab060)
[Schawinski K., et al., 2009, ApJ, 690, 1672](http://dx.doi.org/10.1088/0004-637X/690/2/1672)
[Schmidt W., Federrath C., Hupp M., Kern S., Niemeyer J. C., 2009, A&A,](http://dx.doi.org/10.1051/0004-6361:200809967)

[494, 127](https://ui.adsabs.harvard.edu/abs/2009A&A...494..127S)
[Seigar M. S., Harrington A., Treuthardt P., 2018, MNRAS, 481, 5394](http://dx.doi.org/10.1093/mnras/sty2709)
Simionescu A., Tremblay G., Werner N., Canning R. E. A., Allen S. W.,
[Oonk J. B. R., 2018, MNRAS, 475, 3004](http://dx.doi.org/10.1093/mnras/sty047)
[Solomon P. M., Rivolo A. R., Barrett J., Yahil A., 1987, ApJ, 319, 730](http://dx.doi.org/10.1086/165493)
[Sormani M. C., Barnes A. T., 2019, MNRAS, 484, 1213](http://dx.doi.org/10.1093/mnras/stz046)
[Sormani M. C., Binney J., Magorrian J., 2015, MNRAS, 449, 2421](http://dx.doi.org/10.1093/mnras/stv441)
[Sormani M. C., et al., 2023, MNRAS, 523, 2918](http://dx.doi.org/10.1093/mnras/stad1554)
[Sun J., et al., 2018, ApJ, 860, 172](http://dx.doi.org/10.3847/1538-4357/aac326)
[Sun J., et al., 2020, ApJ, 901, L8](http://dx.doi.org/10.3847/2041-8213/abb3be)
[Sun J., et al., 2022, AJ, 164, 43](http://dx.doi.org/10.3847/1538-3881/ac74bd)
[Tan J. C., 2000, ApJ, 536, 173](http://dx.doi.org/10.1086/308905)
[Teng Y.-H., et al., 2022, ApJ, 925, 72](http://dx.doi.org/10.3847/1538-4357/ac382f)
[Teng Y.-H., et al., 2023, ApJ, 950, 119](http://dx.doi.org/10.3847/1538-4357/accb86)
Tully R. B., 1988, Nearby galaxies catalog
Utomo D., Blitz L., Davis T., Rosolowsky E., Bureau M., Cappellari M.,
[Sarzi M., 2015, ApJ, 803, 16](http://dx.doi.org/10.1088/0004-637X/803/1/16)
[Veron-Cetty M. P., Veron P., 1986, A&AS, 66, 335](https://ui.adsabs.harvard.edu/abs/1986A&AS...66..335V)
[Wada K., Papadopoulos P. P., Spaans M., 2009, ApJ, 702, 63](http://dx.doi.org/10.1088/0004-637X/702/1/63)
Ward J. L., Kruĳssen J. M. D., Chevance M., Kim J., Longmore S. N., 2022,

[MNRAS, 516, 4025](http://dx.doi.org/10.1093/mnras/stac2467)

[Wilson C. D., et al., 2011, MNRAS, 410, 1409](http://dx.doi.org/10.1111/j.1365-2966.2010.17646.x)
[Wong T., et al., 2011, ApJS, 197, 16](http://dx.doi.org/10.1088/0067-0049/197/2/16)
[Wu Y.-L., Sakamoto K., Pan H.-A., 2017, ApJ, 839, 6](http://dx.doi.org/10.3847/1538-4357/aa68de)
[Wu B., Tan J. C., Nakamura F., Christie D., Li Q., 2018, PASJ, 70, S57](http://dx.doi.org/10.1093/pasj/psx140)
[da Silva P., Menezes R. B., Steiner J. E., Fraga L., 2020, MNRAS, 496, 943](http://dx.doi.org/10.1093/mnras/staa1500)
[de Vaucouleurs G., Freeman K. C., 1972, Vistas in Astronomy, 14, 163](http://dx.doi.org/10.1016/0083-6656(72)90026-8)
de Vaucouleurs G., de Vaucouleurs A., Corwin Herold G. J., Buta R. J., Paturel G., Fouque P., 1991, Third Reference Catalogue of Bright Galaxies
[van der Marel R. P., 2001, AJ, 122, 1827](http://dx.doi.org/10.1086/323100)


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


</paper>

## Items to check

```json
[
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "1 SPW of 468.750 MHz (1920 channels of 244 kHz / 0.63 km s^-1) on 12CO(1-0); 3 continuum SPWs of 1.875 GHz (1920 channels of 976 kHz)",
  "failed_quote": "The correlator was set up with one spectral window of 468.750 MHz (≈ 1200 km s−1) bandwidth and 1920 channels each of 244 kHz (≈ 0.63 km s−1) centred on the redshifted 12CO(1-0) line."
 },
 {
  "path": "data.baselines.evidence[0]",
  "value": "15 - 2500 m (C43-6) and 110 - 11,000 m (C43-8)",
  "failed_quote": "The C43-6 configuration observations had 6500 s on-source using 47 antennae and baselines of 15 – 2500 m, leading to a maximum recoverable scale (MRS) of 5′′.5."
 },
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "5.5'' (C43-6) and 1.7'' (C43-8)",
  "failed_quote": "The C43-6 configuration observations had 6500 s on-source using 47 antennae and baselines of 15 – 2500 m, leading to a maximum recoverable scale (MRS) of 5′′.5."
 },
 {
  "path": "data.time_on_source.evidence[0]",
  "value": "6500 s (C43-6) and 9500 s (C43-8)",
  "failed_quote": "The C43-6 configuration observations had 6500 s on-source using 47 antennae and baselines of 15 – 2500 m, leading to a maximum recoverable scale (MRS) of 5′′.5."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "Modified version of CPROPSTOO algorithm and cloud physical property calculation methodology",
  "failed_quote": "To identify the clouds of NGC 613 (and to be consistent with previous works), we use our own modified version of the algorithms of cpropstoo (Liu et al. 2021), an updated version of CPROPS (Rosolowsky & Leroy 2006; Leroy et al. 2015)."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Run modified CPROPSTOO algorithm on the central 15'' x 15'' region of the 12CO(1-0) cube to identify 3D cloud structures and classify them as spatially and spectrally resolved or unresolved.",
  "failed_quote": "To identify the clouds of NGC 613 (and to be consistent with previous works), we use our own modified version of the algorithms of cpropstoo (Liu et al. 2021), an updated version of CPROPS (Rosolowsky & Leroy 2006; Leroy et al. 2015)."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Gaussian fits overlaid on number distributions of cloud properties",
  "failed_quote": "In each panel, the black histogram and overlaid black Gaussian fit show the full cloud sample, while the colour-coded histograms and Gaussians show only the clouds in the nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow), respectively."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Calculate bar-driven mass inflow rates, kinetic energy injection rate E_dot_in,total, turbulent energy dissipation rate E_dot_diss, turbulence dissipation timescale t_diss, inter-node travel time t_travel, cloud-cloud collision timescale t_coll, shear timescale t_shear, and characteristic cloud lifetime t_lifetime from azimuthal cloud number drop between nodes.",
  "failed_quote": "To verify whether these bar-driven gas inflows are sufficient to maintain the turbulence in the nuclear ring, we also calculate the turbulent energy dissipation rate 𝐸diss, defined as"
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Identifying GMCs and calculating their physical properties",
  "failed_quote": "To identify the clouds of NGC 613 (and to be consistent with previous works), we use our own modified version of the algorithms of cpropstoo (Liu et al. 2021), an updated version of CPROPS (Rosolowsky & Leroy 2006; Leroy et al. 2015)."
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Size-linewidth relation power-law slope (Linmix) = 0.77 dimensionless",
  "failed_quote": "log 𝜎obs,los km s−1 = (0.77 ± 0.11) log 𝑅c pc −(0.10 ± 0.18), (5)"
 },
 {
  "path": "results_numeric[16].evidence[0]",
  "value": "Size-linewidth relation intercept (Linmix) = -0.10 dex (km s^-1)",
  "failed_quote": "log 𝜎obs,los km s−1 = (0.77 ± 0.11) log 𝑅c pc −(0.10 ± 0.18), (5)"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Virial mass - gas mass power-law slope = 0.94 dimensionless",
  "failed_quote": "log 𝑀obs,vir M⊙ = (0.94 ± 0.03) log 𝑀gas M⊙ + (0.58 ± 0.02), (11)"
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "The modified CPROPSTOO algorithm and Linmix Bayesian regression were chosen to ensure consistency with previous WISDOM GMC studies and because the modified CPROPSTOO has fewer free parameters and is more robust in complex, crowded environments.",
  "failed_quote": "To identify the clouds of NGC 613 (and to be consistent with previous works), we use our own modified version of the algorithms of cpropstoo (Liu et al. 2021), an updated version of CPROPS (Rosolowsky & Leroy 2006; Leroy et al. 2015). Due to fewer free parameters, our version is more efficient and leads to a more robust cloud identification in complex and crowded environments."
 }
]
```
