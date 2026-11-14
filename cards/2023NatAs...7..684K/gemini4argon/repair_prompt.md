# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023NatAs...7..684K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Nature Astronomy_ (2023), 1–22


**ARTICLE**

## **Azimuthal C/O Variations in a Planet-Forming Disk**


Luke Keyte, [1] Mihkel Kama, [1,2] Alice S. Booth, [3] Edwin A. Bergin, [4] L. Ilsedore Cleeves, [5] Ewine F. van Dishoeck, [3,6] Maria N.
Drozdovskaya, [7] Kenji Furuya, [8] Jonathan Rawlings, [1] Oliver Shorttle, [9] and Catherine Walsh [10]


1 Department of Physics and Astronomy, University College London, Gower Street, WC1E 6BT London, United Kingdom
2 Tartu Observatory, Observatooriumi 1, Tõravere 61602, Tartu, Estonia
3 Leiden Observatory, Leiden University, 2300 RA Leiden, the Netherlands
4 Department of Astronomy, University of Michigan, 311 West Hall, 1085 S. University Ave, Ann Arbor, MI 48109, USA
5 Department of Astronomy, University of Virginia, Charlottesville, VA 22904, USA
6 Max-Planck Institut für Extraterrestrische Physik (MPE), Giessenbachstr. 1, 85748 Garching, Germany
7 Center for Space and Habitability, Universität Bern, Gesellschafsstrasse 6, CH-3012 Bern, Switzerland
8 National Astronomical Observatory of Japan, Osawa 2-21-1, Mitaka, Tokyo 181-8588, Japan
9 Department of Earth Sciences & Institute of Astronomy, University of Cambridge, United Kingdom
10 School of Physics and Astronomy, University of Leeds, Leeds, UK, LS2 9JT
**Author for correspondence:** L. Keyte, Email: luke.keyte.18@ucl.ac.uk.


Accepted by Nature Astronomy 03/03/2023


**Abstract**


The elemental carbon-to-oxygen ratio (C/O) in the atmosphere of a giant planet is a promising diagnostic of that planet’s formation history in
a protoplanetary disk. Alongside efforts in the exoplanet community to measure C/O in planetary atmospheres, observational and theoretical
studies of disks are increasingly focused on understanding how the gas-phase C/O varies both with radial location and between disks. This
is mostly tied to the icelines of major volatile carriers such as CO and H 2 O. Using ALMA observations of CS and SO, we have unearthed
evidence for an entirely novel type of C/O variation in the protoplanetary disk around HD 100546: an _azimuthal_ variation from a typical,

_∼_
oxygen-dominated ratio (C/O 0.5) to a carbon-dominated ratio (C/O ≳ 1.0). We show that the spatial distribution and peculiar line kinematics
of both CS and SO molecules can be well-explained by azimuthal variations in the C/O ratio. We propose a shadowing mechanism that could
lead to such a chemical dichotomy. Our results imply that tracing the formation history of giant exoplanets using their atmospheric C/O ratios
will need to take into account time-dependent azimuthal C/O variations in a planet’s accretion zone.



Facilities such as the James Webb Space Telescope and
ESA’s upcoming Ariel mission are opening a new era of exoplanetary studies, promising to characterise the atmospheric
composition of over one thousand worlds by the early 2030s.
Such observations provide exciting opportunities to constrain
planetary formation and evolution models. To enable this science, we must understand the chemical budget of planetary
nurseries.


Of particular significance are carbon and oxygen, which
are among the most abundant volatile elements, and prominent in both protoplanetary disk and planetary chemistry. The
elemental C/O ratio is a potential formation tracer, linking the
volatile composition of an exoplanet atmosphere directly to
the disk region in which it was accreted (Madhusudhan, 2012;
Cridland et al., 2016; Mordasini et al., 2016). The classical view
of the C/O ratio in disk gas or solids is that of a multi-step
function, with jumps at the snowlines of dominant molecular species (Oberg et al., 2011). Considering dust growth and
drift, vapour diffusion, refractory carbon destruction, chemical
kinetics, and planetesimal and disk evolution adds substantial
complexity, but the fundamental conclusion remains that the
planetary C/O ratio is related to its formation history (Madhusudhan et al., 2014; Bergin et al., 2016; Booth et al., 2017;
Krijt et al., 2018; Booth & Ilee, 2019; Cridland et al., 2019; van
’t Hoff et al., 2020; Bosman et al., 2021; Turrini et al., 2021;
Van Clepper et al., 2022; Hobbs et al., 2022).



Empirical findings based on spectroscopic observations
support the hypothesis that the gas-phase elemental C and O
abundances can vary both with radial location in a disk and
between different disks (Favre et al., 2013; Qi et al., 2013; van
der Marel et al., 2016; Du et al., 2017; Cleeves et al., 2018;
Zhang et al., 2019, 2020). While determining the precise
C/O ratio in planet-forming gas is generally not simple, distinguishing between oxygen- or carbon-dominated chemistry
(C/O < 1 or ≳ 1, respectively) is more feasible. The two
chemical regimes are characterised by entirely different compositions. The C 2 H molecule is a powerful C/O tracer, strong
C 2 H emission being a beacon of C/O ≳ 1 in the disk gas due
to the orders-of-magnitude increase in the abundance of hydrocarbons when excess carbon is available (Bergin et al., 2016;
Miotello et al., 2019; Bergner et al., 2019; Bosman et al., 2021).
Another probe is the CS/SO molecular ratio, which varies by
up to four orders of magnitude for small variations in C/O
(Semenov et al., 2018; Booth et al., 2021), and has led to claims
of C/O > 1 in at least six disks (Dutrey et al., 2011; Bosman
et al., 2021; Le Gal et al., 2021). Such results are usually diskaveraged (i.e. unresolved) or indicative of _radial_ variations in
the gas composition. Until now, combined observations of CS
and SO have not been made in any disk, so it has not been
possible to fully utilize the diagnostic power of the CS/SO
ratio in cases of asymmetric emission.


In this paper, using observations of both CS and SO, we

2 Luke Keyte _et al._


present a remarkable _azimuthal_ C/O variation in the planetforming disk around HD 100546, the first time such a variation
has been observed.



**1.** **RESULTS**

_**1.1**_ _**Data & observational findings**_
We present a new detection of CS in HD 100546, alongside
ALMA SO observations first presented in (Booth et al., 2022)
(Figures 1 and 2). HD 100546 is a well-studied 2.49 _±_ 0.02 _M_ _⊙_

_∼_
Herbig Be star, with an estimated age of 5 Myr (Arun et al.,
2019), and distance of 110 _±_ 1 pc. The star hosts a bright disk
with a central dust cavity out to 13 au and another dust gap
between _r_ _∼_ 40 - 150 au, bounded on both sides by dust rings
(Walsh et al., 2014; Fedele et al., 2021). Multiple observations
provide evidence for at least two planetary candidates within
the disk at _r_ _∼_ 13 and 55 au (Walsh et al., 2014; Quanz et al.,
2015; Currie et al., 2015; Pinilla et al., 2015).
CS is detected at 9 σ confidence (0.90 _±_ 0.10 Jy beam [–1] km
s [–1] at emission peak, as measured from the integrated intensity
map), using the Atacama Compact Array (ACA) in Cycle 4
(Figure 2, top right). The emission is essentially unresolved,
since the beam size (4.78") is almost equal to the radial extent
of the gas disk, as traced by CO (Walsh et al., 2017). Fitting
a Gaussian, we find the peak of the CS emission to be significantly offset from the host star by _∼_ 1". We confirm that the
offset is related to a physical characteristic of the source, rather
than a pointing error (Supplementary Information 1). We
determine the radial separation between the peak of the emission and the host star by exploiting the known inclination and
position angle of the disk to deproject the image, finding the
emission peak to be radially offset _∼_ 100 au from the source.
We complement the new CS detection with high resolution Cycle 7 observations of SO, first presented in (Booth et al.,
2022) (Figure 2, top left). The emission primarily emanates
from the inner dust cavity and the inside edge of the dust ring
( _r_ _∼_ 13 au), displaying a clear azimuthal brightness asymmetry,
where emission from the eastern side of the disk is a factor of

_∼_
2 brighter than from the western side.
The distinct morphologies of the SO and CS emission are
mirrored in their respective spectral lines (Figure 3), which
have unusual and disparate velocity profiles. The SO line is
broad ( FWZI _∼_ 15 km s [–1] ) and asymmetric, with a prominent
blueshifted Keplerian peak at _∼_ –7.5 km s [–1] . In contrast, the
CS emission is narrower (FWZI _∼_ 10 km s [–1] ) and sharply
peaked in the red ( _∼_ +1.5 km s [–1] ).
In summary, the CS and SO emission display clear azimuthal asymmetries in their spatial morphologies, and peculiar spectral line profiles. It is striking that emission from each
of these species appears to emanate from distinct and opposite
azimuthal regions of the disk. We argue that these features can
be fully explained by chemistry resulting from azimuthal C/O
variations in the disk.


_**1.2**_ _**Modelling**_
To investigate the origin of the spatial and spectral asymmetries
in the CS and SO emission, we ran source-specific models us


**Figure 1. Azimuthal disparity of SO and CS emission** ALMA 870µm continuum emission map (Fedele et al., 2021), overlaid with SO 7 7 -6 6 +7 8 -6 7 emission contours (green) and CS 7-6 emission contours (white). The continuum
emission has been scaled by _r_ [3] to highlight emission in the outer disk. Contours are logarithmically spaced between 1 σ and peak flux. The position of
the star is denoted by the yellow cross. Beam sizes are _∼_ 0.18"/ 20 au (SO)
and _∼_ 4.78"/ 525 au (CS).


ing the 2D physical-chemical code DALI (Bruderer et al., 2012;
Bruderer, 2013). The disk chemical composition is obtained
from a chemical network simulation, in which the gas-grain
chemistry is solved time-dependently. Our model uses a geometry outlined in Figure 4, in which the disk is composed of
two chemically distinct regions. The majority of the disk has
a composition consistent with previous studies of HD 100546,
in which C/O=0.5 (Kama et al., 2016). We vary the composition in a small angular region of the disk, such that C/O
is elevated within an azimuthally localized ‘wedge’ (C/O>1),
dictated by variations in the gas-phase H 2 O, CO, and atomic
O abundances (see Supplementary Information 5).
We explored a wide parameter space, taking into account
a range of wedge sizes and azimuthal locations, carbon and
oxygen abundances, and chemical timescales. The model presented here incorporates a high-C/O wedge extending azimuthally 60 [o], centered ten degrees north of west. Modelled
integrated intensity maps for both the CS 7-6 and stacked SO
7 7 -6 6 + 7 8 -6 7 emission are presented in Figure 2 (lower panel).
Our model reproduces the CS emission morphology well. The
emission peak is significantly offset towards the west ( _∼_ 75 au
deprojected), with a peak flux that matches the observation
within a factor of _∼_ 1.1. The brightness asymmetry in the SO
emission is also reproduced by our model, peaking towards
the southwest at a radial separation of _∼_ 20 au. The peak flux
matches the observations within a factor of _∼_ 1.2. A more
refined model may be needed to fully reproduce the SO brightness distribution, although we note that the precise distribution
can vary depending on the parameters used for the data reduction (Booth et al., 2022). The east/west asymmetry is always

_Nature Astronomy_ 3


**Figure 2.** **Detected and modelled SO and CS emission in HD 100546** . _Top lef:_ Integrated intensity map of the stacked SO 7 7 – 6 6 and 7 8 – 6 7 transitions
observed with the ALMA ((Booth et al., 2022)). _Top right:_ Integrated intensity map of the CS 7-6 transition observed with ACA, with a 1 σ clip. _Bottom lef:_
Modelled stacked SO 7 7 – 6 6 and 7 8 – 6 7 integrated intensity map. _Bottom right:_ Modelled CS 7-6 integrated intensity map. The position of the star is indicated
with the green ‘x’.



maintained, and is the key feature reproduced by our model.
The modelled spectral lines are shown in Figure 3. The
modelled CS line profile includes a prominent narrow single
peak, red-shifted _∼_ 2 km s [–1] from the source velocity, matching the observation to within _∼_ 0.5 km s [–1] . While it is possible
to match the peak location more precisely by changing the
orientation of the high-C/O wedge, this results in a slightly
lower peak flux (Supplementary Information 3). The modelled
SO line profile reproduces both the double-peaked structure
and peak flux value. The linewidth is a close match to the observation, where the flux density in the blue shifted component
is _∼_ 1.5 _×_ greater than that of the red-shifted component.
Modelled CS and SO abundance maps are presented in
Supplementary Information 2. We note that our model predicts



that the bulk of the SO emission emanates from the dust ring
just outside the cavity, whereas (Booth et al., 2022) used the
line kinematics to infer that it originates primarily from within
the cavity itself. One possible explanation is that our model
lacks a smooth transition between the cavity and dust ring,
instead having a sharp boundary. Additionally, the inclination
and stellar mass used in our model differs from the values
reported in (Booth et al., 2022). Literature values vary between
_i_ = 32 – 44 _[◦]_ (Walsh et al., 2014; Pineda et al., 2019) and
_M_ _∗_ = 2.2 – 2.5 _M_ _⊙_ (Pineda et al., 2019; Arun et al., 2019;
Wichittanakom et al., 2020) which can result in variations of

_∼_
the predicted inner edge of the SO emission ( 9 – 18 au).

4 Luke Keyte _et al._


**Figure 3. Spectral line profiles** . _Lef:_ Observed stacked SO 7 7 – 6 6 and 7 8 – 6 7 spectrum extracted using a 0.6" elliptical mask (grey) and model (blue). _Right:_
Observed CS 7-6 spectrum extracted using a 5" elliptical mask smoothed by the beam (grey) and model (blue). Line profile velocities have been corrected for
the source velocity ( _V_ LSRK = 5.7 km s [–1] ).



**2.** **DISCUSSION**


We have shown that the emission from CS and SO in the
HD 100546 protoplanetary disk can be well-reproduced by a
chemical model that incorporates an azimuthal C/O variation.
This adds a new dimension of complexity to the relationship
between C/O in disks and their planetary progeny. We now
aim to understand the origin of this novel type of chemical
dichotomy.
The depletion of volatile elemental carbon and oxygen
is ubiquitous in protoplanetary disks around both T Tauri
and Herbig Ae/Be stars. For instance, disks around AS 209,
MWC 480, and HD 163296 all exhibit sub-stellar C/H and
O/H ratios (Bosman et al., 2021). Oxygen is typically more depleted than carbon due to its removal from the disk atmosphere
through the freezing out of water onto large dust grains, re
_∼_
sulting in elevated C/O ratios ( 2). However, our modelling
of HD 100546 finds no evidence of significant oxygen depletion relative to carbon in this disk, with a best-fit _disk-averaged_
C/O ratio < 1. The majority of the disk is warm enough to
preclude freeze-out of CO and CO 2 (Supplementary Information 4), and water loss through freeze-out onto large grains is
tempered by the presence of a dust cavity where large grains
are heavily depleted (small grains are not as significant for
_permanent_ freeze-out, as they cycle vertically within the disk
due to turbulence, releasing their ices upon each return to the
disk atmosphere). Photodesorption also limits the extent of the
water snow surface (Figure 5) Analysis of water emission from
HD 100546 reveals a high H 2 O abundance in the photodesorption region is necessary to match observations, with line
kinematics indicating that the emission extends out to r _∼_ 300
au (Pirovano et al., 2022; van Dishoeck et al., 2021). Therefore, we expect the majority of the HD 100546 disk to have
a gas-phase C/O ratio closer to 0.5, and attribute the observed
asymmetries to a region of elevated C/O localized in azimuth.
The main feature we have identified is an azimuthally confined zone of elevated CS abundance, coincident with a region
of depleted SO, which we ascribe to a local enhancement in



the C/O ratio (> 1). How could this come about? Asymmetries
in the structure of both dust and gas are common in protoplanetary disks, particularly transition disks like HD 100546
which have large central cavities (Francis & van der Marel,
2020). Dust asymmetries are often attributed to the trapping
of millimeter-sized grains in vortices formed by the Rossby
Wave Instability (Lovelace et al., 1999), induced by a planetary companion. Vortices can also form through various
hydrodynamical instabilities, or at the edges of low-viscosity
’dead-zones’. In recent years, high-resolution ALMA observations have enabled comparisons between dust asymmetries
and molecular gas at small scales. While several studies have
drawn tentative links (Law et al., 2021; Zhang et al., 2021;
Guzman et al., 2021; Alarcon et al., 2021; Ilee et al., 2021; van
der Marel et al., 2021), there is often no clear connection to
be made. Furthermore, asymmetries observed in a particular
species are often not observed in other species or transitions
of the same species within the same disk. The physical mechanisms responsible for gas asymmetries cannot therefore be
easily attributed to vortices.


In HD 100546, gas-phase asymmetries have previously
been observed in a range of molecular species, including various CO transitions (e.g. Panic et al., 2010; Kama et al., 2016;
Miley et al., 2019), OH (Fedele et al., 2015), and SO (Booth
et al., 2017). These have often been attributed to temperature variations which are thought to result from obscuration
by a warped inner dust disk (Panic et al., 2010; Walsh et al.,
2017), such that one side of the disk is 10-20 K cooler than the
other. In such a scenario, an azimuthal variation in the temperature structure could have significant impact on the disk chemistry, resulting in azimuthal variations in molecular abundances
(Young et al., 2021). However, near-IR observations at small

_∼_
spatial scales ( 1 au) find no evidence supporting an inclined
inner dust disk ( _r_ < 1 au) (Garufi et al., 2016; Follette et al., 2017;
Lazareff et al., 2017; Bohn et al., 2022), which may indicate
that the structure of the gas and dust is significantly different
within the inner few au. Currently, no physical mechanism

_Nature Astronomy_ 5


**Figure 4. Geometry of the HD 100546 disk model.** The disk is composed of two chemically distinct regions; the majority of the disk has C/O=0.5, apart from
a 60 _[◦]_ arc where C/O>1 We propose that an overdensity of dust, associated with a newly forming planet within the cavity, casts a shadow over an azimuthally
localized region of the disk. This results in lower temperatures, which causes additional H 2 O freeze-out, leading to an elevated gas-phase C/O ratio. Note that
this schematic is not to scale; the gas disk extends out to _∼_ 500 au.



is known to cause such decoupling between the gas and small
dust grains, suggesting that another process might be at play.
An alternative scenario is that asymmetric emission is connected to on-going planet formation within HD 100546’s inner cavity. (Booth et al., 2022) propose that the observed SO
asymmetry may be tracing shocked gas in the vicinity of a
circumplanetary disk. Indeed, the peak of the observed SO
emission is cospatial with the location of a protoplanet candidate inferred from scattered light images (Currie et al., 2015)
and excess CO emission (Brittain et al., 2019). Comparing
Cycle 7 and Cycle 0 spectra of SO emission provides further
evidence of a newly-forming planet, as the shift in emission
peak is consistent with a hot-spot of molecular gas in orbital
rotation within the inner cavity (Booth et al., 2017, 2022).
Our findings do not rule out this possibility. While our model
can be modified to account for an additional component of
SO emission related to a CPD, a CPD alone is not able to
account for the asymmetries observed in both the SO and CS.
Both the kinematics and the spatially resolved SO emission are
consistent with a Keplerian protoplanetary disk. The spatial
distribution of the emission indicates that any contribution
from a CPD to the total SO flux would be relatively small.
This leads us to propose an alternative explanation, consistent with an azimuthal C/O variation. We suggest that an
overdensity of dust associated with the inner protoplanet casts
a shadow on an azimuthally localised region of the outer disk.
This causes dust temperatures in the disk atmosphere to decrease, which leads to additional H 2 O freeze-out on grain
surfaces. In turn, this locks a significant fraction of gas-phase
oxygen into ices, causing the local gas-phase C/O ratio to
become super-solar. As the disk chemistry rebalances, SO is
rapidly destroyed while CS is rapidly formed, on timescales
shorter that the shadow transit time.
Falsifying this hypothesis using past observations is not
straightforward. Our understanding of dust substructures
within HD 100546 is shaped by both infrared and (sub)millimeter
observations, which contain many features. These include spiral arms, dark and bright azimuthal wedges, emission hotspots
(Garufi et al., 2016; Sissa et al., 2018). and an inner ring sculpted



by a maze of ridges and trenches (Pérez et al., 2020; Fedele
et al., 2021). We note that the location of the protoplanet
within HD 100546’s inner cavity is not coincident with our
high-C/O wedge towards the west, but closer to the region
of bright SO emission. Nevertheless, material associated with
a forming planet can be highly azimuthally and vertically extended (Zhu et al., 2014). Indeed, several features suggestive
of shadowing have been identified on the western side of the
disk. The most prominent is a dark region towards the northwest, already linked to a possible large-scale shadow (Garufi
et al., 2016). This region covers a similar azimuthal width to
the high-C/O wedge used in our model, and overlaps with it
significantly (the local minimum in the azimuthal brightness
profile is orientated slightly further northwest by _∼_ 10 _[◦]_ ). At
least one other similar dark wedge was identified on the opposite side of the disk (Norfolk et al., 2022). Other features that
could be related to a dust overdensity include a horseshoe-like
structure identified in 7mm observations at the inner southwest
edge(Wright et al., 2015), and a bar-like structure seen in H α
polarized light, which may be a “streamer” of dust dragged
in by gas flowing from the outer to inner disk (Mendigutia
et al., 2017). However, it is unclear whether such features
could lead to large-scale shadowing. So, while HD 100546
clearly displays a number of morphological features that could
be related to shadowing, linking any such feature to the region
of high-C/O identified here remains open to interpretation.

To determine if a shadow could cause the required chemical
changes to produce C/O > 1, we examined three timescales:
cooling, freeze-out, and chemical conversion (Supplementary
Information 5). As the shadow falls on a part of the disk, the
dust must cool enough for H 2 O to freeze out. Kinetics will
then funnel O from other reservoirs (atomic O, CO) into
the water-ice sink, eventually elevating the CS abundance
and depleting SO within the shadowed region. The combined
time needed for these processes to operate must be shorter than

_∼_
the time spent in shadow, which converges to 5 years in the
outer disk (based on model parameters). Considering a range
physical conditions from our model in the CS-emitting region
(Supplementary Information 2), we find that the C/O ratio can

6 Luke Keyte _et al._



**Figure** **5.** **HD** **100546** **model** **dust** **temperature** **map** . Most of the disk is
warm enough to preclude freeze-out of CO and CO 2 . The H 2 O snow surface
(blue line) largely coincides with a dust gap in the outer disk (white dotted
lines). Millimeter-sized grains are highly depleted in this region, removing
grain surface area available for permanent H 2 O freeze-out. The outer edge
of the snow surface is curtailed by photodesorption.


exceed unity in _≤_ 5 years inside of _r_ ≲ 200 au. These results
are illustrated in Figure 6. The shadowing hypothesis can be
tested in the near future with high-resolution observations
of the CS emission, to establish whether the feature moves.
Moving shadows of this nature have already been observed in
other disks such as TW Hya (Debes et al., 2017).
Regardless of the precise mechanisms which lead to azimuthal C/O variations in the HD 100546 disk, it is clear that
such a chemical dichotomy will have a profound impact on
the final composition of planets forming within it. Growing
planets are supplied by gas and dust from their surroundings.
Planets which move in and out of two chemically distinct
regions during the course of their evolution can be expected
to have chemically complex envelopes, formed of material
accreted from both regions. The degree to which envelope
composition mirrors that of either region in the disk will be
governed by complex chemical and physical processes. If shadowing is indeed responsible for the azimuthal C/O variation,
we may expect its effect on planetary composition to be even
more profound in warm disks such as HD 100546, where there
is a higher fraction of gas-phase water available for freeze-out.
The results presented here therefore add a new consideration to the way in which we interpret observations and model
gas-phase asymmetries in protoplanetary disks. The classical
view of a radially varying C/O ratio must be readdressed if
we are to draw meaningful links between the composition
of exoplanet atmospheres, and the disks in which they form.
Determining the C/O ratio at small spatial scales must be a
major goal of future observations, if we are to build models
that can meaningfully predict planetary formation pathways.


**3.** **METHODS**

_**3.1**_ _**Data reduction**_

HD 100546 was observed with the Atacama Compact Array (ACA) in
Band 7 during Cycle 4, in two separate execution blocks on November 14th and November 24th 2016 (program 2016.1.01339.S, PI: M.
Kama). The observations cover 8 molecular rotational transitions of 7



sulfur-bearing species/isotopologues, outlined in Table 2. Eight scans
were performed for a total on-source time of 50.64 minutes, with
baselines ranging from 8-45 m. System temperatures varied from
103-170 K and the average precipitable water vapour was 1.0 mm.
J1058+0133 was used as both the bandpass and flux calibrator, while
J1147-6753 was used as the phase calibrator.
The data reduction was completed using the ALMA Pipeline in
the Common Astronomy Software Package (CASA) version 5.6.1-8.
Self-calibration was performed but found to have marginal impact due
to low S/N of the data. Continuum and line imaging were performed
with the tCLEAN algorithm using natural weighting in order to
maximize the S/N ratio of the data. The resulting synthesized beam
size was _∼_ 4.78" x 4.06", with slight variations depending on the
spectral window. We used a cell size of 0.5" to ensure that the beam is
well sampled. Continuum subtraction was performed with the CASA
task _uvcontsub_, using a single-order polynomial fit to the line free
channels. The spectral resolution, bandwidth, synthesized beam size
for each of the transitions are listed in Table 2.
CS 7-6 at 342.883 GHz is successfully detected, while all other
transitions are undetected. The CS 7-6 integrated intensity map (Figure 2, top right) was generated from a 20"x20" region centred on the
source, where the integrated intensity is determined between -14.5
to 25.5 km s [–1], corresponding to channels expected to contain significant emission ( _∼±_ 20 km s [–1] from the source velocity _V_ LSRK = 5.7
km s [–1] ). The detection is made at a 9 σ confidence level, with a peak
flux of 0.90 Jy beam [–1] km s [–1], and rms of 0.10 Jy beam [–1] km s [–1] as
measured from the emission-free regions of the integrated intensity
map. Channel maps are presented in Supplementary Information 6,
from which we measure a peak flux density of 0.21 Jy beam [–1] and
rms of 0.024 Jy beam [–1] .
We extracted the spectrum from the CLEAN cube using an elliptical aperture with a 5.0" radius centred on the source (approximately
the same size as the disk as traced by [12] CO emission (Walsh et al.,
2014)), where the edges of the mask were smoothed by the beam.
We also extracted a spectrum using a Keplerian mask, which excludes
noisy pixels that are not directly associated with emission from a disk
in Keplerian rotation (Teague, 2020). The mask identifies which
pixels in the image cubes have Doppler shifted line velocities that
match the Keplerian velocity, based on the velocity profile of a disk
rotating around a star of mass _M_ _⋆_ = 2.4 _M_ _⊙_ . Pixels with velocities
that do not match the Keplerian velocity are masked. The mask is
convolved with a beam of equal size to the observation, in order to
provide a buffer between the mask edge and emission edge. The
total disk-integrated flux was extracted using the CASA task _specflux_,
and determined to be 0.62 Jy km s [–1] for the Keplerian-masked cube,
where the mask was cut at _±_ 4 km s [–1] either side of the source velocity
in order to remove noisy channels. The disk-integrated flux extracted
from the elliptically masked cube was 1.02 Jy km s [–1] . Due to the
peculiar nature of the CS line profile, our analysis utilises only the
elliptically-masked spectrum, in order to not mistakenly remove any
real emission.
We employed a number of techniques in an attempt to extract
weak spectral signatures from the remaining spectral windows centred
on other molecular species (Table 2). We began by extracting spectra
from the CLEAN image cubes using an elliptical aperture with a 5.0"
radius centred on the source. Integrated intensity maps were created
from the CLEAN cubes, which yielded no detections.
Next, we applied a Keplerian mask to each of the CLEAN image
cubes in order to maximise the S/N in the image plane. We extracted
spectra and generated integrated intensity maps from the masked
cubes, which again resulted in no detections. We also tried stacking

_Nature Astronomy_ 7


the maximum recoverable scale of the observations is 10.422" ( _∼_ 1150
au), which is much larger than the gas disk (Walsh et al., 2014), and we
therefore do not expect any flux missing on short spacings. Similarly,
the maximum recoverable scale of our ACA observations is 21.266"
( _∼_ 2350 au), also much larger than the gas-disk. The full list of line
fluxes and upper limits used to constrain our model is presented in
Supplementary Information 9.



**Figure** **6.** **Cooling,** **freeze-out,** **and** **chemical** **timescales** . The maximum
time available for the combination of cooling, freeze-out, and shadowing
to occur is dictated by the period a specific region of the disk remains
in shadow, which is related to the orbital period of the shadowing material (black line). The cooling timescale is denoted in light blue, freeze-out
timescale in dark blue (for a range of ∆ g/d ), and chemical timescale in red.
The green shaded area represents the sum total of these timescales within
the range of considered ∆ g/d, which follows the freeze-out timescale since
the cooling and chemical timescales are negligable. Purple shaded regions
denote location of millimeter dust rings.


the SO 2 1 -1 0 and 8 8 -7 7 lines in the image plane by adding together
the integrated intensity maps and spectra. However, SO remained
undetected.
Finally, we applied a matched filter to the visibility data, to maximize the S/N in the _uv_ -plane (Loomis et al., 2018). The matched filter
technique utilises a template image cube that samples the _uv_ -space in
order to obtain a set of template visibilities. These can then be used
as a filter, which is cross-correlated with the data in an attempt to
detect any weak emission. Matched filtering has previously been used
to successfully detect weak spectral line features in HD 163296, TW
Hya, and HD 100546, providing an improvement in the S/N of up
to _∼_ 500% when compared to alternative techniques (Carney et al.,
2017; Loomis et al., 2018; Booth et al., 2018). We created template
emission profiles for each of the spectral windows in the ACA data by
modelling the spectral line emission with the DALI thermo-chemical
disk modelling code (see section 3.3). The matched filter was then
run for each of the spectral lines individually, which again resulted in
non-detections for all lines. We derived 3 σ upper limits for the diskintegrated flux for each of the non-detected spectral lines, calculated
from the elliptically masked integrated intensity maps (see Table 2).
We also report the serendipitous detection of C [18] O 3-2 in the
spectral window centred on SO 2 1 -1 0 at 329.385 GHz. The detection
is made at a _∼_ 24 σ confidence level, with a peak flux of 7.2 _±_ 0.3 Jy
beam [–1] km s [–1], as measured from the integrated intensity map. The
disk integrated flux is measured using the procedure outlined above,
determined to be 5.41 Jy km s [–1] using a Keplerian mask, and 8.22 Jy
km s [–1] using an elliptical mask.


_**3.2**_ _**Complementary data**_
To complement our CS 7-6 data for HD 100546, we make use of a
wide range of archival data. Of particular significance to this study are
detections of SO 7 7 -6 6 and SO 7 8 -6 7 first presented in (Booth et al.,
2022) (ALMA program 2019.1.00193.S, PI A. S. Booth). We note that



_**3.3**_ _**Chemical modelling**_
To investigate the origin of the azimuthal asymmetries in various
molecular species in the HD 100546 disk, we ran source specific
models using the 2D physical-chemical code DALI (Bruderer et al.,
2012; Bruderer, 2013). The code begins with a parameterised gas
and dust density distribution and an input stellar spectrum, then
uses Monte Carlo radiative transfer to determine the UV radiation
field and dust temperature. This provides an initial guess for the
gas temperature, which begins an iterative process in which the gasgrain chemistry is solved time-dependantly. Finally, the raytracing
module is used to obtain spectral image cubes, line profiles, and diskintegrated line fluxes.


_3.3.1_ _Disk parameters_
The disk structure is fully parameterised, with a surface density that
follows the standard form of a power law with an exponential taper:



2– γ
(1)
� �



_r_
Σ gas = Σ c _·_ � _R_ _c_



– γ
_r_

_·_ exp –
� � � _R_ _c_



where _r_ is the radius, γ is the surface density exponent, Σ c is some
critical surface density, and _R_ c is some critical radius, such that the
surface density at _R_ c is Σ c / _e_ . The scale height is then given by:



ψ
(2)
�



_h_ ( _r_ ) = _h_ _c_



_r_
� _R_ _c_



where _h_ c is the scale height at _R_ c, and the power law index of the
scale height, ψ, describes the flaring structure of the disk.
Σ gas and Σ dust extend from the dust sublimation radius ( _R_ sub ) to
the edge of the disk ( _R_ out ), and can be varied independantly inside
the cavity radius _R_ cav with the multiplication factors δ gas and δ dust .
The gas-to-dust ratio is denoted ∆ g/d . Dust settling is implemented by considering two different populations of grains; small
grains (0.005-1 µ m) and large grains (0.005-1mm). The vertical density structure of the dust is such that large grains are settled towards
the midplane, prescribed by the settling parameter χ :



ρ dust, large = ~~_√_~~ _f_ Σ 2 π dust _r_ χ



Σ dust _·_ exp – [1]

2 π _r_ χ _h_ � 2



2
(3)
� �



2



π /2 – θ
� χ _h_




_[f]_ [)] [Σ] [dust]
ρ dust, small = [(][1 –]
~~_√_~~ 2 π _rh_




_[f]_ [)] [Σ] [dust]

_·_ exp – [1]
2 π _rh_ � 2



2
(4)
� �



2



π /2 – θ
� _h_



where _f_ is the mass fraction of large grains and θ is the opening
angle from the midplane as viewed from the central star. The physical
disk parameters used in our model are given in Table 1.


_3.3.2_ _Stellar parameters_
HD 100546 is a well-studied 2.49 _±_ 0.02 _M_ _⊙_ Herbig Be star of spectral
type B9V, with an estimated age of _∼_ 5 Myr (Arun et al., 2019). The
star is noted for its proximity, located at a distance of 110 _±_ 1 pc (Gaia
Collaboration et al., 2018). We note that this differs non-trivially
from previous estimates of 97 _±_ 4 from _Hipparcos_ . The stellar spectrum

8 Luke Keyte _et al._



was modelled by Bruderer et al. (2012) using dereddened FUSE and
IUE observations at UV wavelengths, and then extended to longer
wavelengths using the B9V template of (Pickles, 1998). The stellar
luminosity is 36 _L_ _⊙_ (Kama et al., 2016).


_3.3.3_ _Chemical network_

The chemical network used in our model is based on a subset of the
UMIST 06 (Woodall et al., 2007) network. It consists of 122 species
(including neutral and charged PAHs) and 1701 individual reactions.
The code includes H 2 formation on dust, freeze-out, thermal and
non-thermal desorption, hydrogenation, gas-phase reactions, photodissociation and -ionization, X-ray induced processes, cosmic-ray
induced reactions, PAH/small grain charge exchange/hydrogenation,
and reactions with vibrationally excited H 2 . For grain-surface chemistry, only hydrogenation of simple species is considered (C, CH,
CH 2, CH 3, N, NH, NH 2, O, and OH). The details of these processes
are described more fully in (Bruderer et al., 2012). Of particular
relevance to this study, the network includes reactions for 30 sulfurbearing species, including all those listed in Table 2. Model parameters
of relevance to the disk chemistry are listed in Table 1.


_3.3.4_ _Basic fitting procedure_
Our fitting process follows the precedure outlined in (Kama et al.,
2016), making use of additional observational constraints and a larger
grid of models. We begin by fitting the SED using a grid of 1728
models, in which the parameters _R_ gap, ψ, _h_ _c_, δ dust and ∆ g/d are varied.
At this stage, Σ gas is kept fixed at an arbitrary value such that changes
to ∆ g/d are equivalent to changes only in the dust mass, thus providing
us with a baseline estimate for the total dust mass. We find a best fit
total dust mass of 1.12 _×_ 10 [–3] _M_ _⊙_, consistent with previous studies
(Kama et al., 2016).
Next, we use the upper limits of the HD 56 µ m and 112 µ m
lines to constrain the maximum gas mass. A second grid of models is
run in which Σ gas and ∆ g/d are varied in lockstep, allowing the gas
mass to vary whilst maintaining the best-fit dust mass. We constrain
the total gas mass to < 5.6 _×_ 10 [–1] _M_ _⊙_, equivalent to a gas-to-dust
ratio of ∆ g/d _≈_ 390 (taking into account dust depletion in the inner
cavity). This is not a tight enough constraint to uniquely determine
the gas-to-dust ratio, so from this point on we adopt the interstellar
value of ∆ g/d = 100, equivalent to a total gas mass of 1.45 _×_ 10 [–1] _M_ _⊙_ .
Our model allows for varitions in ∆ g/d within the inner dust cavity,
but does not take into account other radial variations such as the
observed dust gap in the outer disk between _r_ _∼_ 40 – 150 au.

[C]/[H] gas and [O]/[H] gas are constrained by modelling the CO
ladder, the line profiles of the CO 3-2, CO 6-5 and [CI] transitions,
and the radial profile of the CO 3-2 emission from (Walsh et al., 2014).
We find a best fit oxygen abundance of [O/H] gas _≈_ (1 – 7) _×_ 10 [–5] .
When [O/H] gas - 7 _×_ 10 [–5], the [CI] line is underpredicted or the
CO ladder is overpredicted, depending on [C/H] gas . When [O/H] gas
< 1 _×_ 10 [–5], the CO ladder is underpredicted for all values of [C/H] gas .
Adopting a fiducial oxygen abundance of [O/H] gas = 2 _×_ 10 [–5], we find

[C/H] gas _≈_ (1 – 2) _×_ 10 [–5] . C 2 H upper limits presented in (Kama et al.,
2016) constrain the global C/O ≲ 1, and we adopt [C/H] gas = 1 _×_ 10 [–5]

for our fiducial model, giving a C/O ratio of 0.5. These values are
consistent with those found in previous studies of HD 100546 (e.g.
Kama et al., 2016). As with that study, the main uncertainties are due
to the limited constraints on the gas-to-dust ratio.
Finally, we constrain the gas-phase elemental sulfur abundance
using the disk-integrated CS 7-6, SO 7 7 -6 6 and SO 7 8 -6 7 fluxes and



radial intensity profiles, and upper limits for other sulfur-bearing
species listed in Table 2. For this study, we adopt a radially varying
sulfur abundance profile, in which [S/H]= 10 [–9] between 13-30 au
and [S/H]= 10 [–8] between 150-230 au, coincident with prominent
millimeter dust rings. Outside of these regions, the sulfur is further
heavily depleted by a factor of 1000. This is based on high resolution
SO observations which suggest some level of correlation between
SO emission and dust ring location (Booth et al., 2022). If a single
sulfur abundance is used for the entire disk, our model overpredicts
SO emission from the outer dust cavity. A detailed study into the
volatile sulfur abundance in HD 100546 is the focus of an upcoming
companion paper (in prep).


_3.3.5_ _Modelling azimuthal asymmetries_
We hypothesize that the asymmetries in the observed CS and SO
emission can be explained by significant azimuthal variations in the
elemental carbon and/or oxygen abundances in HD 100546. In such
a scenario, the resulting chemistry leads to an azimuthal disparity in
the production of carbon- and oxygen-bearing species.
Our aim is to produce a model in which oxygen-based chemistry
dominates in one region of the disk, while carbon-based chemistry
dominates in another region of the disk. We investigate whether
such a model, using time-dependant chemistry, can self-consistently
reproduce the asymmetry in the CS and SO emission.
We simplify our assumptions about the chemistry by constructing
a model in which the disk consists of two distinct spatial regions. DALI
is a 2-dimensional code which relies upon azimuthal symmetry to
produce 3-dimensional outputs, so in order to simulate azimuthal
asymmetries it is necessary to run two separate models and splice
together the outputs using the following procedure.
Our starting point is the full-disk model outlined in the previous
section, where C/O=0.5 (‘model A’). Using the raytracing module
in DALI, we obtain spectral image cubes for each transition, with
the velocity resolution set to match the observations. Next, we run
a second full-disk model in which the carbon and/or oxygen abundances are varied, such that the resulting C/O ratio is different from
the first model (‘model B’). Using a custom Python script, for each
transition the spectral cube from model B is spliced together with
its counterpart from model A, following the geometry outlined in
Figure 4. The resulting cube consists of a large ‘crescent’ region taken
from model A, in which the C/O ratio is 0.5, and a smaller ‘wedge’
region extracted from model B, with a different C/O ratio. The size
of the wedge is prescribed by the angle θ, and the orientation by the
angle φ (measured from the centre of the wedge arc). Angles are
measured in the plane of the cube i.e. they are not projected on to
the disk, and as such do not directly correlate to angles measured
in the disk plane. The result is that the angular region from which
the wedge is extracted cuts through very slightly different azimuthal
regions for different vertical positions within the disk. A more sophisticated model could take the vertical disk structure into account, but
we expect the overall effect on the intensity maps and line profiles to
be negligible. We note that that there is precedent in the literature
for this kind of chemical modelling (Cleeves et al., 2015). We process
the model cubes using the CASA tasks _simobserve_ and _simanalyze_ in
order to create simulated ALMA observations, using parameters that
match the observations. Spectra are extracted and the cubes are then
collapsed to generate moment 0 integrated intensity maps.
We explored a wide parameter space, considering large scale
variations in the carbon/oxygen abundance, wedge size and position,
and chemical timescale. Our model grid covers elemental carbon
and oxygen abundances that range from 1.0 _×_ 10 [–6] to 2 _×_ 10 [–4], and

_Nature Astronomy_ 9



_∼_
C/O between 0.3 - 3.0 ( 570 models in total). The angular size and
position from which we extracted the wedge used parameters that
varied from θ = 10 – 90 [o] and φ = 0 – 180 [o] . Both the carbon/oxygen
abundances and overall size of the wedge are largely constrained by
the best-fit full disk model outlined in the previous section; the vast
majority of the total disk structure must conform to this model if the
general fit is to be maintained. Thus, the wedge region cannot be too
large, nor can the carbon/oxygen abundances vary too dramatically
without significantly affecting the overall model fit. While large
wedge angles better produce the spatial morphology of the SO emission, they lead to disk-integrated CS fluxes that are too high. Smaller
wedge angles better reproduce the CS flux, but fail to reproduce the
offset in the CS emission from the host star, and lead to SO emission
that extends too far around the western side of the disk.
We simulate the effects of disk shadowing by using the output
abundances from the C/O = 0.5 model as input abundances to the
chemical network for the high-C/O wedge model, such that the
chemical conditions at the beginning of shadowing are similar to that
of the unshadowed region of the disk. Before running the chemical
network, we decrease the input H 2 O, CO, and atomic O abundances
by varying amounts in order to investigate a range of C/O ratios. The
physical justification for depleting each of these species is discussed
in Supplementary Information 5. Models are run for a range of
chemical timescales, in order to assess how quicky the chemistry
rebalances. This method allows us to constrain the CO depletion
factor to ≲ 0.8, via comparison with the CO 6-5, CO 3-2, and

[CI] 1-0 lines obtained by APEX and previously presented in (Kama
et al., 2016) (see Supplementary Information 7) (the depletion factor
is defined as the ratio of the new abundance to the initial abundance).
The CO 6-5 line profile has a significant asymmetry in which the
blue-shifted peak is _∼_ 1.25x brighter than the red-shifted peak. CO
depletion factors higher than _∼_ 0.8 fail to reproduce any significant
asymmetry. We test the effects of modelling a range of CO depletion
factors between 0 to 0.8, while at the same time varying the level of
atomic oxygen and H 2 O depletion, as to cover a range of C/O ratios.
In order to investigate C/O ratios significantly greater than unity,
it is necessary to redistribute some of the carbon from the removed
CO into other gas-phase species. In this case, we place the carbon
into neutral atomic carbon, following (Bergin et al., 2016). The
model presented here uses a CO depletion factor of 0.3, an atomic
oxygen depletion factor of 0.3, and an H 2 O depletion factor of 0
(i.e. total removal), resulting in a gas-phase C/O ratio of 1.5. The
model is run to a chemical age of 5 years, based on the approximate
shadow transit time (Supplementary Information 5). The full set
of parameters used for the model presented in this study are listed
in Table 1 (Supplementary Information 8). Using these values, we
find that a wedge size of θ = 60 [o] centred ten degrees north of west
west ( φ = 10 [o] ) accurately reproduces both the CS and SO emission
morphology and line profiles.



**Data availability**
The data presented here is from the ALMA Cycle 4 program 2016.1.01339.S
(PI M. Kama). The raw data is publicly available from the ALMA
archive. The reduced data and final imaging products are available
upon reasonable request from the corresponding author.



**Corresponding author**
Correspondence and requests for materials should be addressed to
Luke Keyte (luke.keyte.18@ucl.ac.uk).



**Acknowledgement**
We acknowledge D.Fedele for sharing the ALMA 870 µ m continuum
data. L.K. acknowledges funding via a Science and Technology Facilities Council (STFC) studentship. E.F.v.D. is supported by A-ERC
grant agreement No. 101019751 MOLDISK. M.N.D. acknowledges
the Swiss National Science Foundation (SNSF) Ambizione grant no.
180079, the Center for Space and Habitability (CSH) Fellowship,
and the IAU Gruber Foundation Fellowship. C.W. acknowledges
financial support from the University of Leeds, the Science and Technology Facilities Council, and UK Research and Innovation (grant
numbers ST/T000287/1 and MR/T040726/1).


**Author contributions**
LK reduced the ACA CS data, ran the chemical models, performed
analysis of both the data and models, and wrote the manuscript. MK
contributed to the analysis of both the data and models, original
research concepts, and writing of the manuscript, and led the proposal for the ACA data. A.S.B provided the ALMA SO data and
contributed to the writing of the manuscript. E.A.B., L.I.C., E.F.v.D.,
M.N.D., K.F., J.R., O.S., and C.W. contributed to the writing of the
manuscript.


**References**
Alarcon, F., Bosman, A. D., Bergin, E. A., et al. 2021, ApJS, 257, 8
Arun, R., Mathew, B., Manoj, P., et al. 2019, AJ, 157, 159
Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101
Bergner, J. B., Oberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25
Bohn, A. J., Benisty, M., Perraut, K., et al. 2022, A&A, 658, A183
Booth, A. S., Ilee, J. D., Walsh, C., et al. 2022, arXiv e-prints,
arXiv:2210.14820


Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi,
S. 2021, A&A, 651, L6

Booth, A. S., Walsh, C., Kama, M., et al. 2018, A&A, 611, A16
Booth, R. A., Clarke, C. J., Madhusudhan, N., & Ilee, J. D. 2017, MNRAS,
469, 3994
Booth, R. A., & Ilee, J. D. 2019, MNRAS, 487, 3998

Bosman, A. D., Alarcó n, F., Bergin, E. A., et al. 2021, ApJ Supplement Series,
257, 7

Brittain, S. D., Najita, J. R., & Carr, J. S. 2019, ApJ, 883, 37
Bruderer, S. 2013, A&A, 559, A46
Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A,
541, A91
Carney, Hogerheijde, M. R., Loomis, R. A., et al. 2017, A&A, 605, A21
Cleeves, L. I., Bergin, E. A., & Harries, T. J. 2015, ApJ, 807, 2
Cleeves, L. I., Oberg, K. I., Wilner, D. J., et al. 2018, ApJ, 865, 155
Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693
Cridland, A. J., Eistrup, C., & van Dishoeck, E. F. 2019, A&A, 627, A127
Cridland, A. J., Pudritz, R. E., & Alessi, M. 2016, MNRAS, 461, 3274
Currie, T., Cloutier, R., Brittain, S., et al. 2015, ApJ, 814, L27
Debes, J. H., Poteet, C. A., Jang-Condell, H., et al. 2017, ApJ, 835, 205
Du, F., Bergin, E. A., Hogerheijde, M., et al. 2017, ApJ, 842, 98
Dutrey, A., Wakelam, V., Boehler, Y., et al. 2011, A&A, 535, A104
Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. 2016,
Journal of Molecular Spectroscopy, 327, 95

Favre, C., Cleeves, L. I., Bergin, E. A., Qi, C., & Blake, G. A. 2013, ApJ, 776,
L38


Fedele, D., Bruderer, S., van den Ancker, M. E., & Pascucci, I. 2015, ApJ, 800,
23

Fedele, D., Toci, C., Maud, L. T., & Lodato, G. 2021, A&A

Fedele, D., Bruderer, S., van Dishoeck, E. F., et al. 2013, A&A, 559, A77
Follette, K. B., Rameau, J., Dong, R., et al. 2017, AJ, 153, 264

10 Luke Keyte _et al._



Francis, L., & van der Marel, N. 2020, ApJ, 892, 111
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1
Garufi, A., Quanz, S. P., Schmid, H. M., et al. 2016, A&A, 588, A8
Guzman, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6
Hobbs, R., Shorttle, O., & Madhusudhan, N. 2022
Ilee, J. D., Walsh, C., Booth, A. S., et al. 2021, ApJS, 257, 9
Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83
Krijt, S., Schwarz, K. R., Bergin, E. A., & Ciesla, F. J. 2018, ApJ, 864, 78
Law, C. J., Loomis, R. A., Teague, R., et al. 2021, ApJ Supplement Series, 257,
3

Lazareff, B., Berger, J.-P., Kluska, J., et al. 2017, A&A, 599, A85
Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJ Supplement Series, 257,
12
Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018, AJ, 155, 182
Lovelace, R. V. E., Li, H., Colgate, S. A., & Nelson, A. F. 1999, ApJ, 513, 805
Madhusudhan, N. 2012, ApJ, 758, 36
Madhusudhan, N., Knutson, H., Fortney, J. J., & Barman, T. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, &
T. Henning, 739
Meeus, Montesinos, B., Mendigutia, I., et al. 2012, A&A, 544, A78
Mendigutia, I., Oudmaijer, R. D., Garufi, A., et al. 2017, A&A, 608, A104
Miley, J. M., Panic, O., Haworth, T. J., et al. 2019, MNRAS, 485, 739
Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69
Mordasini, C., van Boekel, R., Molliè re, P., Henning, T., & Benneke, B.
2016, ApJ, 832, 41
Muller, Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49
Muller, H. S., Schloder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of
Molecular Spectroscopy, 742, 215
Norfolk, B., Pinte, C., Calcino, J., et al. 2022
Oberg, K. I., Murray-Clay, R., & Bergin, Edwin A., E.-m. k. 2011, Astrophysical Journal Letters, 743, doi:10.1088/2041-8205/743/1/L16
Panic, van Dishoeck, E. F., Hogerheijde, M. R., et al. 2010, A&A, 519, A110
Pérez, S., Casassus, S., Hales, A., et al. 2020, ApJ, 889, L24
Pickles, A. J. 1998, PASP, 110, 863
Pineda, J. E., Szulá gyi, J., Quanz, S. P., et al. 2019, ApJ, 871, 48
Pinilla, P., Birnstiel, T., & Walsh, C. 2015, A&A, 580, A105

Pirovano, L. M., Fedele, D., van Dishoeck, E., et al. 2022, A&A
Qi, C., Öberg, K. I., Wilner, D. J., et al. 2013, Science, 341, 630
Quanz, S. P., Amara, A., Meyer, M. R., et al. 2015, ApJ, 807, 64
Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005,
A&A, 432, 369

Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28
Sissa, E., Gratton, R., Garufi, A., et al. 2018, A&A, 619, A160
Sturm, B., Bouwman, J., Henning, T., et al. 2010, Astronomy and Astrophysics, 518, L129
Teague, R. 2020, doi:10.5281/zenodo.4321137
Tielens, A. G. G. M. 2005, The Physics and Chemistry of the Interstellar
Medium

Turrini, D., Schisano, E., Fonte, S., et al. 2021, ApJ, 909, 40
Van Clepper, E., Bergner, J., Bosman, A., Bergin, E., & Ciesla, F. 2022, ApJ,
927, 206

van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi,
S. 2021, A&A, 651, L5

van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585,

A58

van der Wiel, M. H. D., Naylor, D. A., Kamp, I., et al. 2014, MNRAS, 444,
3911–3925

van Dishoeck, E. F., Kristensen, L. E., Mottram, J. C., et al. 2021, A&A, 648,
A24

van Scheltinga, J. T., Ligterink, N. F. W., Bosman, A. D., Hogerheijde, M. R.,
& Linnartz, H. 2022, doi:10.48550/ARXIV.2208.13789
van ’t Hoff, M. L. R., Bergin, E. A., Jørgensen, J. K., & Blake, G. A. 2020,
ApJ, 897, L38



Walsh, C., Daley, C., Facchini, S., & Juhász, A. 2017, A&A, 607, A114
Walsh, C., Juhász, A., Pinilla, P., et al. 2014, ApJ, 791, L6
Wichittanakom, C., Oudmaijer, R. D., Fairlamb, J. R., et al. 2020, MNRAS,
493, 234
Woodall, J., Agundez, M., Markwick-Kemper, A. J., & Millar, T. J. 2007,
A&A, 466, 1197
Wright, C. M., Maddison, S. T., Wilner, D. J., et al. 2015, MNRAS, 453, 414
Young, A. K., Alexander, R., Walsh, C., et al. 2021, MNRAS, 505, 4821
Zhang, K., Bergin, E. A., Schwarz, K., Krijt, S., & Ciesla, F. 2019, ApJ, 883,
98

Zhang, K., Bosman, A. D., & Bergin, E. A. 2020, ApJ, 891, L16
Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5
Zhu, Z., Stone, J. M., Rafikov, R. R., & ning Bai, X. 2014, ApJ, 785, 122

_Nature Astronomy_ 11



**Supplementary Information 1.** **Assessingthesignificanceofthe**
**CS 7-6 emission offset**
Here, we assess whether the observed offset in the peak of the CS
7-6 emission is related to a physical phenomenon, or the result of
an observational error. We begin by comparing the CS emission to
the continuum and C [18] O 3-2 observations from our ACA dataset
(Figure 7). Both the continuum and C [18] O 3-2 line are detected at
high signal-to-noise (see Section 3). A previous study has suggested
that both the continuum and C [18] O 2-1 emission may be slightly
asymmetric, with emission peaks that are offset from the star by
_∼_ 0.08" and _∼_ 0.11" respectively (Miley et al., 2019). However, such
deviations are significantly smaller than the observed CS offset of
_∼_ 1" (by factors of _∼_ 12.5 and _∼_ 9). At the scale of our observations
(using a _∼_ 5" synthesized beam and pixel size of 0.5"), any offset in the
continuum or C [18] O emission will be contained entirely within the
central pixel. It is therefore reasonable to utilise the continuum and
C [18] O emission peaks as reference locations for the host star. We also
note that the C [18] O 3-2 spectrum presented here (Figure 7, bottom
panel) is symmetric about the source velocity, in contrast to the C [18] O
2-1 line presented in (Miley et al., 2019). This suggests that the layer
traced by C [18] O 3-2 emission is more symmetric that that traced by
the 2-1 emission, and strengthens the case to use it as a frame of
reference for the host star. By comparision, it is clear that the CS 7-6
emission is significantly offset from the central star, and the offset
cannot therefore be related to the absolute astronometric precision
of the observation. We created a residual map by subtracting the CS
7-6 integrated intensity map from the C [18] O 3-2 integrated intensity
map. A 1 σ clip was first applied to the CS data, and the C [18] O peak
flux was then scaled to match that of the CS. The residuals were then
divided by the rms of the CS data.
Next, we calculate the uncertainty in the beam centroid, given
by the following equation (Condon et al., 1998):


σ _P_ _≈_ [1] (5)

2 [σθ] [/] _[S]_ _[P]_


where σ _P_ is the positional uncertainty, σ is the rms, θ is the beam
FWHM, and _S_ _P_ is the peak flux density. Using our reported values
of σ = 0.1 Jy beam [–1], θ = 4.78", and _S_ _P_ = 0.9 Jy beam [–1], we find:


σ _P_ _≈_ [1] (6)

2 _[×]_ [ 0.1] _[ ×]_ [ 4.78/0.9] _[ ≈]_ [0.27] [”]


We therefore find the CS 7-6 emission peak to be offset by _∼_
1 _±_ 0.27". Since the offset is a factor of _∼_ 4 times the uncertainty,
we can be confident that it is at least partly related to a physical
characteristic of the source.
Next, we assess the offset in the visibility plane, using the CASA
task _uvmodelfit_ to fit a model directly to the UV-data. We first
split out the spectral windows containing the CS 7-6 emission from
continuum-subtracted measurement set, using only the channels centered _±_ 10 km s [–1] from the source velocity. We then fit a Gaussian to
the data, where the initial guess for shape is based on the synthesized
beam properties, and the initial guess for the emission peak is the
image centre (ie. location of the star). We run 20 iterations, with the
model converging after _∼_ 8. The offset in the emission peak is found
to be 0.88 _±_ 0.23" west and 0.68 _±_ 0.25" south, corresponding to a
total absolute offset of 1.11 _±_ 0.33". Since _uvmodelfit_ can be sensitive
to the initial conditions, we repeat the fitting using a range of initial
guesses for the location of the emission peak. In all cases the models



converge to close to the same result, deviating by a maximum of _∼_ 8
% from the value reported here.
Finally, we looked at data in the ALMA archive for other spectral line observations which might display similar asymmetries. We
uncovered an unpublished observation of C 2 H at 349 GHz (ALMA
project 2017.1.00845.S, PI: E. Bergin), obtained at high angular resolution (beam size _∼_ 0.3", approximately 30 au). C 2 H is a powerful
tracer of the C/O ratio, with numerous studies having linked strong
C 2 H emission to chemical environments where C/O > 1 (e.g. Bergin
et al., 2016; Miotello et al., 2019; Bergner et al., 2019; Bosman et al.,
2021). An emission map created from the pipeline data products
reveals that C 2 H is concentrated in a ring at _∼_ 230 au, which approximately coincides with the outer edge of a millimeter dust ring. The
total flux on the red-shifted side of the disk is a factor of _∼_ 1.5 greater
that that on the shifted side, which may be indicative of an elevated
C/O ratio. This is in agreement with our CS 7-6 observation, where
the emission is significantly offset towards the red shifted side of the
disk. We do not formally present the C 2 H observatiom here, since
a full analysis is well beyond the scope of this work. However, we
note that the pipeline data products are freely available in the ALMA
archive.


**Supplementary Information 2.** **Abundance maps and contribu-**
**tion functions**


Figure 8 shows CS and SO abundance maps, for both the C/O=0.5
region and C/O>1 wedge . Contribution functions for the CS 7-6
and SO 7 7 -6 6 +7 8 -6 7 transitions are overlaid (25% and 75% contours).


**Supplementary Information 3.** **Varying the size and position of**
**the high-C/O wedge**

Figure 9 shows the effect of varying the size and position of the highC/O wedge on the modelled spectra. The wedge size is described by
the arc subtended by the angle θ . The wedge position is described
using the azimuthal angle φ (where φ = 0 points due west, and is
measured positively anti-clockwise). A given angle φ corresponds to
the position of the arc centre.
We vary the angular size of the high-C/O wedge between θ =
20 _[◦]_ to 180 _[◦]_, while keeping the centre of the wedge arc fixed at
φ = 0 (Figure 9, top panel). Asymmetries in the SO spectra are
more pronounced for larger wedge angles, with increasing wedge
sizes leading to decreasing peak fluxes on the red-shifted side of the
spectrum. The CS spectrum remains highly asymmetric about the
source velocity, regardless of wedge size, with larger wedges result
in broader line profiles and higher peak fluxes.
We vary the angular position of the high-C/O wedge between
φ = –60 _[◦]_ to 60 _[◦]_, while keeping the angular size fixed at θ = 60 _[◦]_

(Figure 9, bottom panel). Asymmetries in the SO spectra are most
pronounced when the wedge points towards 60 _[◦]_, since this corresponds to the region of the disk in which line-of-sight velocities are
most highly red-shifted. Rotating the arc position clockwise through
to –60 _[◦]_ results in a incrementally smaller contribution to the SO spectra from the highly red-shifted part of the disk, and therfore a more
symmetric double-peaked structure. Similarly, the CS spectrum is
most highly red-shifted when the high-C/O wedge is positioned at
60 _[◦]_, with a narrow profile and high peak flux. As the arc position is
rotated clockwise through to –60 _[◦]_, the line becomes broader with
smaller peak flux, with the peak of the line profile moving closer to
the source velocity.

12 Luke Keyte _et al._



**Supplementary Information 4.** **Temperature and density maps**
Figure 10 shows the temperature and density maps for dust and gas
in the HD 100546 disk model.


**Supplementary Information 5.** **Cooling, freeze-out, and chemi-**
**cal timescales**

We propose that material associated with a protoplanet in HD 100546’s
inner dust cavity casts a shadow on a region of the outer disk, resulting in the azimuthal chemical variations described in this work. In
order for such material to cast a shadow covering an angular region of
60 _[◦]_, as prescribed by our model, the azimuthal extent of the material
must be much larger than the host star. At a radial distance of 13 au,
which is equivalent to the outer edge of the dust cavity, the necessary
azimuthal extent of the shadowing material is _∼_ 15 au. Additionally, the material must extend vertically such that the shadow enables
freeze-out of H 2 O in the upper layers of the disk atmosphere. Taking
_r_ = 100 au and _z_ / _r_ = 0.25 as a representative location for excess H 2 O
freeze-out (via comparison with the modelled H 2 O snow surface,
see Figure 5), the necessary vertical extent of the shadowing material
is _∼_ 3.2 au. This is reasonable, since hydrodynamic simulations of
disks show that dust concentrations associated with large embedded
protoplanets can be highly elongated, especially in the φ direction
(e.g. Zhu et al., 2014).
If the material responsible for shadowing orbits at 13 au, it will
complete one orbit in _∼_ 30 years. A shadow covering an azimuthal
region of 60 _[◦]_ will therefore transit a given region of the disk in
30 _×_ (60/360) = 5 years. However, since the shadowed material is
in orbit itself, the total time spent in shadow will vary as a function
of orbital separation. Shadowing timescales are longest in the inner
disk, where the orbital period of the material being shadowed is
comparible to the orbital period of the shadow. This falls off rapidly
with radius, approaching the minimum shadowing time of _∼_ 5 years
in the outer disk. Since reproducing the offset in the CS emission
requires a large increase in the CS abundance in the outer disk, we
take 5 years as our upper limit on the time available for changes
in the chemistry to occur such that the C/O ratio becomes supersolar. To assess the feasibility of the shadowing scenario, we present a
simple analytical model that takes into consideration three important
timescales; cooling, freeze-out, and chemical conversion.
The cooling timescale for a single dust grain is given by:


_t_ cooling = _[mC]_ _Q_ rad [∆] _P_ _[T]_ (7)


where _m_ is the mass of the dust grain, _C_ is the specific heat
capacity, ∆ _T_ is the change in temperature, and _P_ = _A_ σ _T_ [4] is the
radiative power of the dust grain (where A is the grain surface area,
and σ is the Stefan-Boltzmann constant). _Q_ rad is the Planck mean
efficiency for dust grains at temperatures between 10-250 K (where
_Q_ rad = 1.25 _×_ 10 [–5] _T_ _d_ [2] [(] _[r]_ [/1] [µ] _[m]_ [), where] _[ r]_ [is the grain radius (Tielens,]
2005)).
We make the simplifying assumption that gas in the disk atmosphere is coupled to a population of small dust grains of equal size
_r_ = 1 µ _m_ . Taking ρ = 4 g cm [–3] as a typical value for grain density
(based on silicate materials such as olivine), the grain mass is then
_m_ = ρ (4/3 π _r_ [3] ) _≈_ 1.68 _×_ 10 [–14] kg. We take _C_ = 2000 J kg [–1] K [–1],
which is again typical of silicate material. Finally, we make the simplification that all H 2 O is in gaseous form at 100 K and in ice at 50
K i.e. ∆ _T_ = 50 K. Note that these approximate values are lower
than the canonical freezeout temperature for H 2 O to account for the



effects of photodesorption. For grains with radius _r_ = 1 µ _m_ at 100 K,
_Q_ rad = 0.125. The cooling timescale can then be calculated as:



where _k_ is the Boltzmann constant and _m_ is the mass of the H 2 O
molecule. The freeze-out timescale, which is equal to the collision
timescale, is then given by:


_t_ freeze = µ (11)
_v_ rms


Note that it is not necessary for the bulk of the gas to cool down
to the dust temperature for freezeout to occur when the gas and
dust are thermally decoupled, as is the case in the disk atmosphere
(Extended Data Fig. 3). The increase in dust temperature due to a
collision will be extremely small, and since the dust cooling timescale
is extremely short this can be considered negligible. The timescale
for the dust and gas to reach thermal equilibrium will be longer that
the timescale derived here, but our calculation is reasonable when
considering freezeout in the conditions described above.
We compute _t_ freeze for a range of gas-to-dust ratios between
∆ g/d = 10 – 390, where the lower limit is taken from (Kama et al.,
2016) and the upper limit is based on constraints from modelling HD
lines (see Section 3.3). We find that _t_ freeze can vary from _∼_ 47 hours
to 4500 years between _r_ = 13 to 300 au, depending on ∆ g/d . These
values are subject to large uncertainties because _n_ dust can vary quite
dramatically depending on the precise location of the disk atmosphere
from which it is extracted, in addition to uncertainties in ∆ due
g/d
to dust settling and radial drift. While the simple calculations we
present here relate to a single grain, these can reasonably be used as
an approximation for the entire local grain population in the optically
thin regime, which is a reasonable assumption for material in the
upper surface layers of the disk.
Finally, we consider the relevant chemical timescales. We simulate the effects of shadowing by first extracting the final elemental and
molecular abundances from our ‘unshadowed’ C/O=0.5 model, using
these as an input for the shadow model. The total elemental gas-phase
oxygen is then depleted by setting the input H 2 O abundance to zero
(representing total freeze-out). This complete removal of H 2 O is
not enough to increase the gas-phase C/O above unity, since the
majority of element oxygen is tied up in atomic O and CO. However,
our chemical models show that when H 2 O is removed from the gas
phase on such a large scale, the following chemical rebalance leads



_t_ cooling = 0.1251.68 _× ×_ 4 π 10(10 [–14][–6] ) _×_ [2] _×_ 2000 5.67 _× ×_ ( 10100 – 50 [–8] _×_ 100) [4]


_≈_ 189 s



(8)



We now consider the freeze-out timescale, which is dictated by
the efficiency with which gas-phase H 2 O molecules collide with
cooled grains. The mean free path of a gas molecule is given by:


1
µ = (9)
_n_ π _r_ [2]


where _n_ is the number density of the dust grains, and _r_ is the
grain radius. We extract values for _n_ directly from our chemical
model, from a range of grid cells that trace the location of the H 2 O
freeze-out in the upper disk atmosphere, then reduce the value by a
factor of 100 to account for dust settling to the midplane.
The average gas speed of a molecule is given by:



_v_ rms = ~~�~~ ¯ _v_ [2] =



3 _kT_

(10)

~~�~~ _m_

_Nature Astronomy_ 13



to a significant production of new gas-phase H 2 O via the following
pathway:


H 2 + O _→_ OH + H (12)

H 2 + OH _→_ H 2 O + H (13)


The subsequent freeze-out of this newly-produced gas-phase
H 2 O therefore provides a route by with atomic oxygen can be removed from the gas phase, further elevating the C/O ratio. Additional
oxygen (and carbon) may be removed by the conversion of gas-phase
CO into CO 2 ice, via a surface reaction with OH radicals produced
by UV irradiation of amorphous solid water:


CO + OH _→_ _trans_ – HOCO (14)

_trans_ – HOCO _→_ _cis_ – HOCO (15)

_cis_ – HOCO _→_ CO 2 + H (16)


We can expect reactions 14 - 16 to be enhanced in the shadowed
region, since the lower temperature locks a larger fraction of H 2 O into
ices. Laboratory experiments show that this pathway can permanently
sequester gas-phase CO into CO 2 ice at temperatures between 40-60
K (well above the canonical CO freeze-out temperature), with an
efficiency of up to 27% (van Scheltinga et al., 2022). While reactions
14 - 16 are not included in our chemical network, we take them
into account by manually adjusting the abundances as follows. We
adjust the initial conditions of our shadow model, depleting not only
H 2 O, but also a fraction of atomic O and CO, such that the resulting
gas-phase C/O > 1.0 (see Section 3.3). We let the chemistry evolve
and extract the CS and SO abundances as a function of time from
key regions of the disk. We find that the newly elevated C/O ratio
favours both the formation of CS and destruction of SO, primarily
via the reactions:


C + SO _→_ CS + O (17)

C + SO _→_ CO + S (18)


These reactions have no activation barrier and so can proceed
in cold gas. CS is formed at a faster rate than SO is destroyed, since
there are prominent CS formation pathways in addition to reaction
17:


CH 2 + S _→_ CS + H 2 (19)

C + HS _→_ CS + H (20)


The effect of this time evolution on the CS and SO abundances
and disk integrated line fluxes is illustrated in Figure 11. The CS
7-6 disk-integrated line flux steadily increases with time in the superstellar C/O environment, with the SO 7 7 -6 6 disk-integrated line flux
showing the opposite trend. To approximate the timescale at which
this phenomenon becomes apparent in observations, we define the
chemical timescale as the period in which the CS abundance increases
by a factor of two, and the SO abundance decreases by a factor of
two, whichever is longest (see Figure 11). We calculate the chemical
timescale at different radial regions in the disk, by extracting the
variations in CS and SO abundance from key grid cells in the model
(Figure 11, lower panels). We find that the chemical timescale varies
between _∼_ 2 _×_ 10 [–4] to _∼_ 5 years, for radial regions between 13-300

au.



The combined results for cooling, freeze-out, and chemical conversion are illustrated in Figure 6. The total time is almost entirely
dependent on the freeze-out timescale, since the cooling and chemical timescales are negligable compared to the shadow transit time.
We show that, within the _∼_ 5 year period it takes the shadow to
transit a given region of the disk, the gas-phase C/O ratio can become
super-solar within the inner _∼_ 200 au of the disk (within _∼_ 150 au
for ∆ g/d = 100). Considering the fact that prominent emission from
both CS and SO emanates from inside of _∼_ 200 au (Supplementary
Information 2), and the uncertainties associated with the freeze-out
timescale, we conclude that shadowing is a plausible means by which
the local C/O ratio can become elevated, leading to the spatial and
spectral asymmetries presented in this work.
A more sophisticated model could take into account the reverse
timescale, and the cyclical nature of disk shadowing, by addressing
the effects of many transits over the lifetime of the disk. Such an
investigation is beyond the scope of this work.


**Supplementary Information 6.** **CS 7-6 channel maps**
Figure 12 shows the individual channel maps for the CS 7-6 detection
with the ACA.


**Supplementary Information 7.** **CO 6-5, CO 3-2, and [CI] spectra**
Figure 13 shows the modelled and observed CO 6-5, CO 3-2, and

[CI] 1-0 spectral lines, used to constrain the level of CO depletion in
the high-C/O wedge (see Section 3.3).


**Supplementary Information 8.** **Disk model parameters**
The parameters used in our disk models are listed in Table 1.


**Supplementary Information 9.** **Observational data**
The observational parameters for each of the spectral windows in the
ACA dataset are given in Table 2. The full list of line fluxes and upper
limits used to constrain our model is given in Table 3.

14 Luke Keyte _et al._


**Figure 7. Comparison between continuum, C** [18] **O, and CS ACA data** . _Top lef:_ Continuum emission map. _Top right:_ C [18] O 3-2 integrated intensity map. _Middle_
_lef:_ CS 7-6 integrated intensity map. _Middle right:_ Residual map created by subtracting the CS emission from the C [18] O emission. The C [18] O flux was scaled to
match the peak flux of the CS emission, and a 1σ clip was applied to the CS emission. The residuals are divided by the rms of the CS data, from which it is
evident that the CS emission is significantly offset from the star (denoted with ‘x’). _Bottom:_ C [18] O 3-2 spectrum.

_Nature Astronomy_ 15


**Figure 8. Abundance maps and contribution functions for the modelled CS and SO emission in HD 100546** . Each panel shows an abundance map overlaid
with contours representing 25% and 75% line emission (white). Top: CS 7-6 emission from the C/O=0.5 region ( _lef_ ) and C/O>1 wedge ( _right_ ). Bottom: SO
7 7 – 6 6 + 7 8 – 6 7 emission from the C/O=0.5 region ( _lef_ ) and C/O>1 wedge ( _right_ ).

16 Luke Keyte _et al._


**Figure 9. Effect of varying the high-C/O wedge size and position on the modelled spectra** . _Top panel:_ SO 7 7 -6 6 +7 8 -6 7 (lef) and CS 7 – 6 (right) spectra for
variations in wedge size (θ), centered on position φ = 0 . _Bottom panel:_ SO 7 7 -6 6 +7 8 -6 7 (lef) and CS 7 – 6 (right) spectra for variations in wedge position (φ),
for a fixed angular size θ = 60 _[◦]_ .

_Nature Astronomy_ 17


**Figure 10. Temperature and density maps for the baseline HD 100546 disk model (C/O=0.5)** . _Top lef:_ Gas number density. _Bottom lef:_ Dust number density.
_Top right:_ Gas temperature. _Bottom right:_ Dust temperature.

18 Luke Keyte _et al._


**Figure 11. Time-dependent disk-integrated fluxes and abundances in the high C/O wedge** . _Top panel:_ Disk-integrated CS 7–6 (green) and SO 7 7 –6 6 (purple)
fluxes, as a function of time in the region where C/O>1. _All other panels:_ CS (green) and SO (purple) abundances at different radial locations, as a function of
time in the region where C/O>1. All values are extracted from the model at z/r _∼_ 0.25 . Dotted lines represent the point in time where the CS flux increases by
a factor of two from its initial values (green), and the SO flux decreases by a factor of two from its initial value (purple). The longer of these two times is taken
as the chemical timescale at that particular radius.

_Nature Astronomy_ 19


**Figure 12.** **CS 7-6 channel maps at a spectral resolution of 0.5 km s** [–1] . Contours are at 35%, 50%, 65%, and 80% peak flux. The source velocity is _V_ LSRK =
5.7 km s [–1] . The white cross denotes the position of the star.

20 Luke Keyte _et al._


**Figure 13. Modelled and observed CO and [CI] spectra** . Modelled CO 6-5 (blue), CO 3-2 (green), and [CI] 1-0 (purple) spectra. APEX observations in grey. The
model reproduces the asymmetry of the CO 6-5 spectral line (but underpredicts the peak CO 6-5 flux, as in previous studies of HD 100546 (Kama et al., 2016)).

_Nature Astronomy_ 21


**Table 1.** HD 100546 disk model parameters.


Parameter Description Fiducial


_R_ sub Sublimation radius 0.25 au


_R_ gap Inner disk size 1.0 au


_R_ cav Cavity radius 13 au


_R_ out Disk outer radius 1000 au


_R_ _c_ Critical radius for surface density 50 au


δ gas Gas depletion factor inside cavity 1

δ dust Dust depletion factor inside cavity 10 [–4]


γ Power law index of surface density profile 1.0


χ Dust settling parameter 0.2


_f_ Large-to-small dust mixing parameter 0.85

Σ _c_ Σ gas at _R_ _c_ 82.75 g cm [–2]

_h_ _c_ Scale height at _R_ _c_ 0.10


ψ Power law index of scale height 0.20


∆ g/d Gas-to-dust mass ratio 100


_L_ _∗_ Stellar luminosity 36 _L_ _⊙_
_L_ _X_ Stellar X-ray luminosity 7.94 _×_ 10 [28] erg s [–1]

_T_ _X_ X-ray plasma temperature 7.0 _×_ 10 [7] K

ζ cr Cosmic ray ionization rate 3.0 _×_ 10 [–17] s [–1]

_M_ gas Disk gas mass 1.45 _×_ 10 [–1] _M_ _⊙_
_M_ dust Disk dust mass 1.12 _×_ 10 [–3] _M_ _⊙_

[C/H] gas Initial carbon abundance (relative to hydrogen) 1.0 _×_ 10 [–5] (where C/O=0.5)

[O/H] gas Initial oxygen abundance (relative to hydrogen) 2.0 _×_ 10 [–5] (where C/O=0.5)


_t_ chem Timescale for time-dependent chemistry 5 Myr (where C/O=0.5)


**Table 2.** Observational parameters for molecular species in HD 100546 from the ACA (program 2016.1.01339.S). Upper limits are at 3σ level, denoted by ‘<’.
Detections are given for Keplerian masked cubes ( _a_ ) and elliptically masked cubes ( _b_ ).


Molecule Transition ν (GHz) ∆ ν (GHz) E up (K) A ul (s [–1] ) Beam Size RMS (Jy beam [–1] km s [–1] ) Flux (Jy km s [–1] )

SO 2 1    - 1 0 329.385 0.250 15.8 1.423 _×_ 10 [–5] 4.83 ” _×_ 4.08 ” 0.14 < 0.66


SO 2 4 3,1    - 3 2,2 332.505 0.250 31.3 3.290 _×_ 10 [–4] 4.84 ” _×_ 4.07 ” 0.10 < 0.48


C [36] S 7 – 6 332.510 0.250 63.9 6.951 _×_ 10 [–4] 4.78 ” _×_ 4.07 ” 0.10 < 0.46


HCS [+] 8 – 7 341.339 0.250 73.7 8.352 _×_ 10 [–4] 4.62 ” _×_ 4.03 ” 0.14 < 0.71


CS 7 – 6 342.883 0.250 65.8 8.368 _×_ 10 [–4] 4.78 ” _×_ 4.06 ” 0.10 0.62 _[a]_, 1.02 _[b]_

H 2 CS 10 0,10   - 9 0,9 342.946 0.250 90.6 6.080 _×_ 10 [–4] 4.73 ” _×_ 3.90 ” 0.31 < 1.50

34 SO 2 3     - 2 1 343.851 0.250 20.9 1.382 _×_ 10 [–7] 4.63 ” _×_ 3.89 ” 0.31 < 1.60


SO 8 8    - 7 7 344.310 0.250 87.5 5.188 _×_ 10 [–4] 4.62 ” _×_ 3.89 ” 0.30 < 1.50

C [18] O 3 – 2 329.330 0.250 31.6 2.172 _×_ 10 [–6] 4.96 ” _×_ 4.21 ” 0.30 5.41 _[a]_, 8.22 _[b]_

22 Luke Keyte _et al._


**Table 3.** Disk-integrated line fluxes and upper limits used to constrain our model.



Molecule Transition Flux (W m [–2] ) Reference


CO 3-2 1.72 _±_ 0.04 _×_ 10 [–18] (Kama et al., 2016)


CO 6-5 1.61 _±_ 0.08 _×_ 10 [–17] (Kama et al., 2016)


CO 7-6 2.35 _±_ 0.27 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 8-7 3.31 _±_ 0.35 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 9-8 4.53 _±_ 0.41 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 10-9 5.53 _±_ 0.37 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 11-10 5.13 _±_ 0.45 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 12-11 5.83 _±_ 0.33 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 13-12 6.07 _±_ 0.47 _×_ 10 [–17] (van der Wiel et al., 2014)


CO 14-13 6.00 _±_ 0.83 _×_ 10 [–17] (Meeus et al., 2012)


CO 15-14 8.83 _±_ 0.97 _×_ 10 [–17] (Meeus et al., 2012)


CO 16-15 5.88 _±_ 0.97 _×_ 10 [–17] (Meeus et al., 2012)


CO 17-16 7.39 _±_ 1.0 _×_ 10 [–17] (Meeus et al., 2012)


CO 18-17 7.15 _±_ 0.69 _×_ 10 [–17] (Meeus et al., 2012)


CO 19-18 6.47 _±_ 0.85 _×_ 10 [–17] (Meeus et al., 2012)


CO 20-19 4.99 _±_ 0.57 _×_ 10 [–17] (Meeus et al., 2012)


CO 21-20 6.50 _±_ 0.88 _×_ 10 [–17] (Meeus et al., 2012)


CO 22-21 _≤_ 4.2 _×_ 10 [–17] (Meeus et al., 2012)


CO 23-22 7.84 _±_ 1.1 _×_ 10 [–17] (Meeus et al., 2012)


CO 24-23 7.13 _±_ 1.2 _×_ 10 [–17] (Meeus et al., 2012)


CO 25-24 _≤_ 7.71 _×_ 10 [–17] (Meeus et al., 2012)


CO 28-27 8.15 _±_ 1.1 _×_ 10 [–17] (Meeus et al., 2012)


CO 29-28 7.86 _±_ 1.9 _×_ 10 [–17] (Meeus et al., 2012)


CO 30-29 7.34 _±_ 1.5 _×_ 10 [–17] (Meeus et al., 2012)


CO 31-30 _≤_ 1.40 _×_ 10 [–16] (Meeus et al., 2012)


CO 32-31 _≤_ 6.53 _×_ 10 [–17] (Meeus et al., 2012)


CO 33-32 _≤_ 8.45 _×_ 10 [–17] (Meeus et al., 2012)


CO 34-33 5.31 _±_ 1.4 _×_ 10 [–17] (Meeus et al., 2012)


CO 35-34 _≤_ 4.41 _×_ 10 [–17] (Meeus et al., 2012)


CO 36-35 5.29 _±_ 1.3 _×_ 10 [–17] (Meeus et al., 2012)


CO 37-36 _≤_ 8.29 _×_ 10 [–17] (Meeus et al., 2012)


CO 38-37 _≤_ 1.07 _×_ 10 [–16] (Meeus et al., 2012)


13 CO 3-2 _≤_ 6.6 _×_ 10 [–19] (Panic et al., 2010)


13 CO 6-5 _≤_ 7.5 _×_ 10 [–18] (van der Wiel et al., 2014)


13 CO 7-6 _≤_ 7.2 _×_ 10 [–18] (van der Wiel et al., 2014)


13 CO 8-7 _≤_ 1.02 _×_ 10 [–17] (van der Wiel et al., 2014)


13 CO 9-8 _≤_ 1.44 _×_ 10 [–17] (van der Wiel et al., 2014)


13 CO 11-10 _≤_ 1.68 _×_ 10 [–17] (van der Wiel et al., 2014)


OI 145µm 3.57 _±_ 0.13 _×_ 10 [–16] (Meeus et al., 2012; Fedele, D. et al., 2013)



Molecule Transition Flux (W m [–2] ) Reference


OI 63µm 5.54 _±_ 0.05 _×_ 10 [–15] (Meeus et al., 2012; Fedele, D. et al., 2013)


CI 1-0 6.60 _±_ 2.0 _×_ 10 [–19] (Kama et al., 2016)


CI 2-1 _≤_ 3.58 _×_ 10 [–18] (Kama et al., 2016)


CII 158µm 1.35 _±_ 0.15 _×_ 10 [–16] (Meeus et al., 2012; Fedele, D. et al., 2013)

HD 112µm _≤_ 2.7 _×_ 10 [–16] (Kama et al., 2016)

HD 56µm _≤_ 1.6 _×_ 10 [–17] (Fedele, D. et al., 2013)


C 2 H 29 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 30 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 31 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 32 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 33 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 34 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 35 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 36 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 37 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 38 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


C 2 H 39 _≤_ 4.8 _×_ 10 [–21] (Kama et al., 2016)


HCO [+] 1-0 _≤_ 7.0 _×_ 10 [–20] (Kama et al., 2016)


HCO [+] 4-3 6.81 _±_ 1.0 _×_ 10 [–20] (Kama et al., 2016)


H 2 O 63.32 _≤_ 2.59 _×_ 10 [–17] (Meeus et al., 2012)


H 2 O 71.946 _≤_ 5.09 _×_ 10 [–17] (Meeus et al., 2012)


H 2 O 78.74 _≤_ 5.70 _×_ 10 [–17] (Meeus et al., 2012)


H 2 O 179.52 3.05 _±_ 4.8 _×_ 10 [–17] (Sturm et al., 2010)


H 2 O 180.42 _≤_ 1.71 _×_ 10 [–17] (Meeus et al., 2012)


H 2 O 90.00 1.160 _±_ 0.161 _×_ 10 [–16] (Sturm et al., 2010)


H 2 O 557 GHz 1.41 _±_ 0.0259 _×_ 10 [–18] (Du et al., 2017)


H 2 O 1113 GHz 5.09 _±_ 0.0844 _×_ 10 [–18] (Du et al., 2017)


H 2 O 1153 GHz _≤_ 1.98 _×_ 10 [–17] (Du et al., 2017)


SO 7 7 -6 6 1.25 _×_ 10 [–21] (Booth et al., 2022)


SO 7 8 -6 7 1.45 _×_ 10 [–21] (Booth et al., 2022)


C [18] O 3-2 9.03 _×_ 10 [–20] This work


SO 2 1 -1 0 _≤_ 7.25 _×_ 10 [–21] This work

SO 2 4 3,1 -3 2,2 _≤_ 5.32 _×_ 10 [–21] This work

C [36] S 7-6 _≤_ 5.10 _×_ 10 [–21] This work


HCS [+] 8-7 _≤_ 8.08 _×_ 10 [–21] This work


CS 7-6 1.167 _×_ 10 [–20] This work


H 2 CS 10 0,10 -9 0,9 _≤_ 1.72 _×_ 10 [–20] This work

34 SO 2 3 -2 1 _≤_ 1.84 _×_ 10 [–20] This work


SO 8 8 -7 7 _≤_ 1.72 _×_ 10 [–20] This work


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[1]",
  "value": "How does the gas-phase elemental C/O ratio vary azimuthally in the protoplanetary disk around HD 100546, and what explains the spatial and kinematic asymmetries in CS and SO emission?",
  "failed_quote": "To investigate the origin of the spatial and spectral asymmetries in the CS and SO emission, we ran source-specific models using the 2D physical-chemical code DALI (Bruderer et al., 2012; Bruderer, 2013)."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "UV observations for modelling the stellar spectrum",
  "failed_quote": "The stellar spectrum was modelled by Bruderer et al. (2012) using dereddened FUSE and IUE observations at UV wavelengths, and then extended to longer wavelengths using the B9V template of (Pickles, 1998)."
 },
 {
  "path": "data.other_facilities[2].provided.evidence[0]",
  "value": "UV observations for modelling the stellar spectrum",
  "failed_quote": "The stellar spectrum was modelled by Bruderer et al. (2012) using dereddened FUSE and IUE observations at UV wavelengths, and then extended to longer wavelengths using the B9V template of (Pickles, 1998)."
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "2D physical-chemical disk models computed with DALI, spliced in 3D and processed with CASA simobserve and simanalyze",
  "failed_quote": "To investigate the origin of the spatial and spectral asymmetries in the CS and SO emission, we ran source-specific models using the 2D physical-chemical code DALI (Bruderer et al., 2012; Bruderer, 2013)."
 },
 {
  "path": "processing.imaging.masking.evidence[2]",
  "value": "5.0\" radius elliptical aperture smoothed by the beam and Keplerian mask (for ACA); 0.6\" elliptical mask (for SO spectrum)",
  "failed_quote": "Left: Observed stacked SO 7 7 – 6 6 and 7 8 – 6 7 spectrum extracted using a 0.6\" elliptical mask (grey) and model (blue)."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Input stellar spectrum model from FUSE, IUE, and B9V template, and DALI chemical network processes",
  "failed_quote": "The stellar spectrum was modelled by Bruderer et al. (2012) using dereddened FUSE and IUE observations at UV wavelengths, and then extended to longer wavelengths using the B9V template of (Pickles, 1998)."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "Wedge size θ = 60 deg, wedge orientation φ = 10 deg north of west, wedge C/O = 1.5 (CO depletion factor = 0.3, O depletion factor = 0.3, H2O depletion factor = 0), chemical age = 5 years; grid of ∼570 models with θ = 10-90 deg, φ = 0-180 deg, C/O = 0.3-3.0",
  "failed_quote": "Our model grid covers elemental carbon and oxygen abundances that range from 1.0 × 10–6 to 2 × 10–4, and C/O between 0.3 - 3.0 ( 570 models in total)."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "2D physical-chemical disk modelling, radiative transfer, time-dependent gas-grain chemistry, and raytracing spectral image cubes",
  "failed_quote": "To investigate the origin of the spatial and spectral asymmetries in the CS and SO emission, we ran source-specific models using the 2D physical-chemical code DALI (Bruderer et al., 2012; Bruderer, 2013)."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "Shadowing by an inner dust overdensity associated with a forming protoplanet at 13 au can cool the outer disk, freeze out H2O, and chemically convert O and S reservoirs to yield C/O > 1 within the ∼5 year shadow transit time inside r ≲ 200 au.",
  "failed_quote": "Considering a range physical conditions from our model in the CS-emitting region (Supplementary Information 2), we find that the C/O ratio can exceed unity in ≤ 5 years inside of r ≲ 200 au."
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "Disk shadowing is a physically plausible mechanism for producing the localized high-C/O wedge, though linking it to a specific observed dust structure remains open to interpretation.",
  "failed_quote": "Considering a range physical conditions from our model in the CS-emitting region (Supplementary Information 2), we find that the C/O ratio can exceed unity in ≤ 5 years inside of r ≲ 200 au."
 }
]
```
