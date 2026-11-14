# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019NatAs...3.1115D\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# **Molecular clouds in the Cosmic Snake normal** **star-forming galaxy 8 billion years ago**

### Miroslava Dessauges-Zavadsky [1] *, Johan Richard [2], Françoise Combes [3,4], Daniel Schaerer [1,5], Wiphu Rujopakarn [6,7,8], Lucio Mayer [9,10], Antonio Cava [1], Frédéric Boone [11], Eiichi Egami [12], Jean-Paul Kneib [13,14], Pablo G. Pérez-González [15], Daniel Pfenniger [1], Tim D. Rawle [16], Romain Teyssier [9,10 ] and Paul P. van der Werf [17 ]



**The cold molecular gas in contemporary galaxies**
**is structured in discrete cloud complexes. These**
**giant molecular clouds (GMCs), with 10** **[4]** **–10** **[7]** **solar**
**masses (** _**M**_ ⊙ **) and radii of 5–100 parsecs, are the**
**seeds** **of** **star** **formation** **[1]** **.** **Highlighting** **the**
**molecular gas structure at such small scales in**
**distant galaxies is observationally challenging.**
**Only a handful of molecular clouds were reported**
**in two extreme submillimetre galaxies at high**
**redshift** **[2-4]** **. Here we search for GMCs in a typical**
**Milky Way progenitor at** _**z**_ **= 1.036. Using the**
**Atacama Large Millimeter/submillimeter Array**
**(ALMA), we mapped the CO(4–3) emission of this**
**gravitationally lensed galaxy at high resolution,**
**reading down to 30 parsecs, which is comparable**
**to the resolution of CO observations of nearby**
**galaxies** **[5]** **. We identify 17 molecular clouds,**
**characterized by masses, surface densities and**
**supersonic turbulence all of which are 10–100**
**times higher than present-day analogues. These**
**properties question the universality of GMCs** **[6]** **and**
**suggest that GMCs inherit their properties from**
**ambient interstellar medium. The measured cloud**

**gas masses are similar to the masses of stellar**
**clumps seen in the galaxy in comparable**
**numbers** **[7]** **. This corroborates the formation of**

**molecular clouds by fragmentation of distant**



**turbulent galactic gas disks** **[8][,][9]** **, which then turn into**
**stellar clumps ubiquitously observed in galaxies at**
**‘cosmic noon’ (ref.** **[10]** **).** **[1]**
The targeted galaxy [7], dubbed the ‘Cosmic Snake’
because of its peculiar shape on the sky, has a stellar mass
of (4.0 ± 0.5) × 10 [10] M ⊙, a star-formation rate of 30 ± 10
M ⊙ yr [–1] and a molecular gas to stellar mass fraction of
25% ± 4%. It is representative of main-sequence starforming galaxies at _z_ ≃ 1 and is recognized to be a Milky
Way progenitor observed 8 billion years ago [11] . Mainsequence galaxies contribute to ~90% of the cosmic starformation rate density [12] and are of general relevance to
probing galaxy evolution. The Cosmic Snake galaxy has
a clumpy morphology strewn with 21 bright stellar
clumps identified in Hubble Space Telescope (HST)
ultraviolet to near-infrared images [7] . The kinematics of
the ionized gas reveals a turbulent, rotationally supported
and marginally stable disk, inclined by 70 ± 5° and
rotating at the maximal speed of 225 ± 1 km s [−1] with an
internal velocity dispersion of 44 ± 30 km s [−1] (ref. [13] ).
These morphological and kinematical characteristics are
common for galaxies around the peak of the cosmic starformation history [10][,][14] . It has been proposed, on the basis
of numerical simulations [8][,][9], that such gas-rich, turbulent,
marginally stable galactic disks fragment because of
gravitational instability caused by intense cold gas
accretion flows [15] and produce bound gas clouds believed
to be the progenitors of the stellar clumps we see.



1 Observatoire de Genève, Université de Genève, Versoix, Switzerland. 2 Université Lyon, Université Lyon1, ENS de Lyon,
CNRS, Centre de Recherche Astrophysique de Lyon UMR5574, Saint-Genis-Laval, France. [3] LERMA, Observatoire de Paris,
PSL Research Université, CNRS, Sorbonne Université, UPMC Paris, France. [4] Collège de France, Paris, France. [5] CNRS,
IRAP, Toulouse, France. [6] Department of Physics, Faculty of Science, Chulalongkorn University, Bangkok, Thailand. [7] National
Astronomical Research Institute of Thailand (Public Organization), Chiang Mai, Thailand. [8] Kavli Institute for the Physics and
Mathematics of the Universe (WPI), The University of Tokyo Institutes for Advanced Study, University of Tokyo, Kashiwa,
Japan. [9] Center for Theoretical Astrophysics and Cosmology, Institute for Computational Science, University of Zurich, Zurich,
Switzerland. [10] Physik-Institut, University of Zurich, Zurich, Switzerland. [11] Université Paul Sabatier, CNRS, IRAP, Toulouse,
France. [12] Steward Observatory, University of Arizona, Tucson, AZ, USA. [13] Laboratoire d’Astrophysique Ecole Polytechnique
Fédérale de Lausanne, Observatoire de Sauverny,Versoix, Switzerland. [14] Aix Marseille Université, CNRS, LAM (Laboratoire
d’Astrophysique de Marseille), UMR7326 Marseille, France. [15] Centro de Astrobiología, CAB, CSIC-INTA, Madrid, Spain.
16 ESA/Space Telescope Science Institute (STScI), Baltimore, MD, USA. 17 Leiden Observatory, Leiden University, Leiden, The
Netherlands. *e-mail: miroslava.dessauges@unige.ch


1

**b** **a** **c**























RA (J2000) 12 h 06 min



_X_ axis (pixels)



Fig. 1 | Molecular gas distribution in the strongly lensed Cosmic Snake galaxy. a, HST RGB-colour
composite image (red filter, F160W; green, F105W; blue, F606W) of the Cosmic Snake arc. The red solid line is
the critical line at _z_ =1.036 of our tailored lens model [7], which shows that the Cosmic Snake arc is a four-fold
multiple image. The overlaid yellow contours represent the ALMA CO(4–3) integrated intensity in levels of 3 _σ_, 4 _σ_,
5 _σ_, 7 _σ_, 9 _σ_, 11 _σ_ and 13 _σ_, with the root-mean-square noise of 0.02 Jy beam [−1] km s [−1] . The yellow filled ellipse (in



5 _σ_, 7 _σ_, 9 _σ_, 11 _σ_ and 13 _σ_, with the root-mean-square noise of 0.02 Jy beam [−1] km s [−1] . The yellow filled ellipse (in

the bottom-right corner) is the ALMA beam with a size of 0.22″×0.18″ at the position angle of +85°. b, The
source-plane reconstruction of the northern counter-image shows slightly more than half of the source galaxy.
The CO(4–3) emission is detected inside the 1.7 kpc galactocentric radius of the source galaxy. The red cross
marks the centre of the galaxy, identified as the peak of the HST F160W emission [7] . We observe that the HST
blue emission, dominated by the stellar clumps hosted in the galaxy [7], is spatially offset from the CO emission by
more than 400 pc. c, Zoom on the southern counter-image of the Cosmic Snake galaxy and the CO(4–3)
emission of the identified molecular clouds in the three-dimensional space of the _X_ and _Y_ space axes and the _Z_
frequency/velocity axis.

The Cosmic Snake galaxy is exceptionally (Fig. 1). They appear as twice to four times multiply
strongly lensed by the potential field of the foreground imaged CO(4–3) emissions in 10.3 km s [−1] channel
galaxy cluster MACS J1206.2–0847 (ref. [16] ), which acts intensity maps, and extend over two and more adjacent
as a gravitational telescope, producing four highly channels (Supplementary Fig. 1). We even find distinct
magnified and stretched galaxy images along a snake- GMCs distributed along the same line of sight. This is
like giant arc (Fig. 1). We mapped the CO _J_ = 4 − 3 line suggestive of a vertical-scale height of the galactic
emission of the arc with ALMA at an angular resolution gaseous disk possibly as high as the sum of the projected
of 0.22″ × 0.18″. At _z_ ≃ 1, we achieve linear physical sizes of the aligned GMCs (that is, at most ~450
scales of 30 pc in the regions with the highest although the strong inclination of the galaxy may also
magnification, ranging to 70 pc in the most weakly contribute to the apparent thickness.
magnified regions. The Cosmic Snake GMCs clearly differ from typical
We identify 17 molecular clouds at significance level GMCs in the local Universe. For their sizes between 30
>6–27 _σ_ (see Methods), distributed inside the 1.7 kpc pc and 210 pc in radius, they have very high molecular
central region of the Cosmic Snake galaxy and spatially gas masses of 8 × 10 [6] _M_ ⊙ to 1 × 10 [9] _M_ ⊙, derived from the
separated from stellar clumps by more than 400 pc CO(4–3) luminosity assuming the CO(4–3) to CO(1–0)



(Fig. 1). They appear as twice to four times multiply
imaged CO(4–3) emissions in 10.3 km s [−1] channel
intensity maps, and extend over two and more adjacent
channels (Supplementary Fig. 1). We even find distinct
GMCs distributed along the same line of sight. This is
suggestive of a vertical-scale height of the galactic
gaseous disk possibly as high as the sum of the projected
sizes of the aligned GMCs (that is, at most ~450 pc),
although the strong inclination of the galaxy may also
contribute to the apparent thickness.
The Cosmic Snake GMCs clearly differ from typical
GMCs in the local Universe. For their sizes between 30
pc and 210 pc in radius, they have very high molecular
gas masses of 8 × 10 [6] _M_ ⊙ to 1 × 10 [9] _M_ ⊙, derived from the
CO(4–3) luminosity assuming the CO(4–3) to CO(1–0)



2

40





30


20


10


0

|SnakeGMCs<br>SDP81GMCs<br>Localst arburstGMCs<br>LocalGMCs|Col2|Col3|limit .7σ detection 5|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|Snake GMCs<br>SDP81 GMCs<br>Local starburst GMCs<br>Local GMCs|||5.7_σ_ detection limit|5.7_σ_ detection limit|5.7_σ_ detection limit||||
|Snake GMCs<br>SDP81 GMCs<br>Local starburst GMCs<br>Local GMCs|||5.7_σ_ detection limit|5.7_σ_ detection limit|||||
|Snake GMCs<br>SDP81 GMCs<br>Local starburst GMCs<br>Local GMCs|||5.7_σ_ detection limit|5.7_σ_ detection limit|||||
|Snake GMCs<br>SDP81 GMCs<br>Local starburst GMCs<br>Local GMCs|||5.7_σ_ detection limit||||||
|Snake GMCs<br>SDP81 GMCs<br>Local starburst GMCs<br>Local GMCs|||||||||
|Snake GMCs<br>SDP81 GMCs<br>Local starburst GMCs<br>Local GMCs|||||||||


4 6 8 10


log ( _M_ molgas ) ( _M_ ⊙ )


Fig. 2 | Normalized distributions of molecular gas
mass for different GMC populations. We compare the
molecular gas masses ( _M_ molgas ) of GMCs identified in the
local quiescent galaxies (filled grey histogram [1][,][17][–][20] ), the
Cosmic Snake galaxy at _z_ =1.036 (filled magenta
histogram) and the submillimetre-bright SDP81 galaxy
at _z_ =3.042 (hatched blue histogram [2] ). The respective
medians and means are shown by the solid and dotted
vertical lines. The derived median molecular gas masses
are 2.9×10 [5] _M_ ⊙ for the local GMCs, 5.8×10 [7] _M_ ⊙ for the

Cosmic Snake GMCs and 5.2×10 [8] _M_ ⊙ for the SDP81

GMCs. Only the local starburst GMCs hosted in the
Antennae merging system [22] and the NGC 253 nuclear
starburst [23] have a molecular gas mass distribution (open
black histogram), median mass of 3.7×10 [7] _M_ ⊙, that

overlaps much with the Cosmic Snake GMC
distribution. The black long-dashed vertical line shows
our 5.7 _σ_ detection limit (corresponding to 100% fidelity;
see Methods) of 4×10 [6] _M_ ⊙ derived for the highest
magnification factor achieved in the Cosmic Snake
GMCs, whereas the black short-dashed vertical line is
the 5.7 _σ_ detection limit achievable without the help of
lensing. A Milky Way CO-to-H 2 conversion factor of 4.36
_M_ ⊙ (K km s [−1] pc [2] ) [−1] is assumed for all GMC populations
plotted.

luminosity correction factor of 0.33 and the Milky Way
CO-to-H 2 conversion factor (Supplementary Table 1).
The median mass of 5.8 × 10 [7] _M_ ⊙ is two orders of
magnitude higher than that of GMCs hosted in the Milky
Way, local dwarf galaxies and nearby spirals [1][,][17][–][20]
(Fig. 2). As a result, they are characterized by very high
surface densities of molecular gas mass, with a median
value of 2,600 _M_ ⊙ pc [−2], more than an order of magnitude
higher than the typical surface density of local GMCs
(100 _M_ ⊙ pc [−2] ). We also observe large internal velocity



dispersions of 9–33 km s [−1] . The five GMCs reported in
SDP81, a starbursting submillimetre-bright galaxy at
_z_ = 3.042, forming stars at a rate of 1–2 orders of
magnitude above the typical level of its epoch, are even
more massive and denser [2] .
The molecular clouds hosted in high-redshift galaxies
turn out to be offset from the Larson scaling relations
(Fig. 3), used as the benchmark of local GMC
populations [1][,][21] and thought to reflect universal GMC
physical properties. These scaling relations show, first,
the linear dependence of the molecular gas mass on size,
which implies a constant molecular gas mass surface
density for GMCs; and, second, the dependence of the
velocity dispersion on size, which follows a power law of
slope ~0.5 and calibrates the surface density of virialized
molecular clouds. How trustworthy is this offset?
Although the Cosmic Snake GMCs are spatially resolved
(Supplementary Fig. 4), we cannot rule out possible
projection effects along lines of sight, accentuated by the
inclination of the galaxy, which might result in molecular
cloud blends and artificial increase of their measured
masses and velocity dispersions. However, to reconcile
the Cosmic Snake GMCs with the mass–size relation of
local GMCs would require an unlikely configuration in
which about the same number (10 to 30) of typical local
GMCs happen to be superposed along each line of sight.
Therefore, we are confident that the Cosmic Snake
GMCs have intrinsically enhanced gas mass surface
densities and velocity dispersions.
Evidence is growing for genuine variations in the
average physical properties of GMCs hosted in different
interstellar environments of nearby galaxies [5][,][6] . In
particular, GMCs observed in environments with high
ambient pressure and high star-formation rate per unit
mass of molecular gas of starbursting central regions of
galaxies and merging galaxies are clearly more massive
and more turbulent than others, and have higher gas mass
surface densities [22][,][23] . Their properties, in fact, very much
resemble those of the high-redshift Cosmic Snake GMCs,
as shown in Figs. 2 and 3. Together they challenge the
universality of GMCs and point to a dependence of GMC
properties on the surrounding ambient environment of
the interstellar medium [5][,][6] .
The large internal velocity dispersions of the Cosmic
Snake GMCs reflect strong internal kinetic pressures of
10 [6.5] –10 [8.6] cm [−3] K (see Methods), which increase with
the gas mass surface density as has been reported for
local GMCs [6] . Here we show that this internal pressure
increase holds in more extreme local and high-redshift
environments, and extends over more than three orders
of magnitude in surface density (Fig. 4a). This goes
together with the strong hydrostatic pressure at the disk
midplane of the Cosmic Snake galaxy, considered as the
first-order approximation of the pressure at the boundary
of a given molecular cloud, and for which we obtain a
rough estimate of ~10 [7.7] cm [−3] K (see Methods), which is
thousands of times stronger than the hydrostatic pressure



3

**a** **b**

10 [10]



100





10 [9]


10 [8]


10 [7]


10 [6]


10 [5]


10 [4]





10



1 10



10


1


100 1



100



_R_ (pc) _R_ (pc)



Fig. 3 | Larson scaling relations. a, Molecular gas masses ( _M_ molgas ) as a function of radius ( _R_ ) for the GMCs
identified in the Cosmic Snake galaxy (magenta data points), the local quiescent galaxies (grey dots [1], triangles [17],
squares [18], crosses [19] and stars [20] ), the nearby starbursting galaxies (black filled circles [22][,][23] ) and the SDP81 galaxy
(blue data points [2] ). The magenta and blue dotted lines show the range of possible molecular gas masses of,
respectively, the Cosmic Snake and SDP81 GMCs as determined with two extreme CO-to-H 2 conversion factors:
the Milky Way value of 4.36 _M_ ⊙ (K km s [−1] pc [2] ) [−1] and the starburst value of 1.0 _M_ ⊙ (K km s [−1] pc [2] ) [−1] (ref. [24] ). The black



the Milky Way value of 4.36 _M_ ⊙ (K km s [−1] pc [2] ) [−1] and the starburst value of 1.0 _M_ ⊙ (K km s [−1] pc [2] ) [−1] (ref. [24] ). The black

lines show fixed molecular gas mass surface densities of, respectively, 100 _M_ ⊙ pc [−2] (solid line), 1,000 _M_ ⊙ pc [−2]
(dashed line) and 2,600 _M_ ⊙ pc [−2] (dotted line). The high-redshift GMCs have much higher gas mass surface densities
than typical local GMCs. b, Internal velocity dispersions ( _σ_ υ ) as a function of radius ( _R_ ), plotted for the same GMC
populations as in a. The black lines show the _σ_ υ ∝ _R_ [0.5] relation expected for virialized clouds with fixed gas mass
surface density (same values as in a). The high-redshift GMCs have on average larger velocity dispersions, required
for equilibrium given their higher surface densities, than typical local GMCs. In a and b, the error bars associated
with the Cosmic Snake GMCs correspond to the overall uncertainty, including the measurement uncertainties on
the CO(4–3) line flux per channel, the radius, and the velocity dispersion, and the uncertainty on the magnification
factors ~~used to obtain lensing-corrected CO(4–3) line~~ fluxes (and ~~hence molecular gas masses) and radii.~~

in the Milky Way disk. This corroborates the idea that hosted in the Cosmic Snake galaxy are clustered around
GMCs cannot be self-gravitating entities decoupled from this one-to-one relationship wit ~~hin a fac~~ tor of 3, which
the surrounding diffuse interstellar medium  gas with corresponds to the mean spread o ~~f local GMC~~ s (~0.4–0.5
universal physical properties [6], since typical local GMCs dex) and typical measurem ~~ent err~~ ors in this parameter
would be rapidly compressed and/or destroyed in media space (Fig. 4b).  Within these uncertainties, observers
of distant galaxies with such strong ambient pressure and assume GMCs to be in virial equilibrium, although one
turbulence exceeding the self-gravity of local GMCs. cannot exclude that some of them are transient structures

molecu ~~la~~ r clouds must inherit their properties (density For GMCs in virial equilibrium, we expect their virial
and tur ~~b~~ ulence) from the ambient interstellar conditions mass to be linearly proportional to CO luminosity [1][,][24] .
particul ~~a~~ r to the host galaxy. This enables us to obtain the first CO-to-H 2 conversion
Giv ~~e~~ n their physical properties, are the high-redshift factor measurements from the kinematics of independent
Cosmic Snake GMCs virialized gravitationally bound GMCs at _z_ ≃ 1. A secure determination of the CO-to-H 2
entities ~~, such that their internal kinetic energy is equal~~ to convers ~~ion factor is crucial for robust estimates~~ of

half their gravitational potential energy? To examine the molecular gas mass. We computed the virial masses of
dynamical state of molecular clouds, we can plot the the 14 Cosmic Snake GMCs found in approximate virial
size–velocity dispersion coefficient, which has a one-to- equilibrium by assuming that each cloud is spherical and
one relationship with gas mass surface density for a has a density profile inversely proportional to radius [1] . We
virialized cloud [1][,][17][,][23] . Regardless of the CO-to-H 2 derive a mean CO-to-H 2 conversion factor of 3.8 ± 1.1
conversion factor considered, 14 out of the 17 GMCs _M_ ⊙ (K km s [−1] pc [2] ) [−1] in this solar metallicity galaxy [13]



convers ~~ion factor is crucial for robust estimates~~ of
molecular gas mass. We computed the virial masses of
the 14 Cosmic Snake GMCs found in approximate virial
equilibrium by assuming that each cloud is spherical and
has a density profile inversely proportional to radius [1] . We
derive a mean CO-to-H 2 conversion factor of 3.8 ± 1.1
_M_ ⊙ (K km s [−1] pc [2] ) [−1] in this solar metallicity galaxy [13]



4

**a** **b**



100





10 [9]


10 [8]


10 [7]


10 [6]


10 [5]


10 [4]





1 10 10 [2]



10


1


0.1


0.01
10 [3] 10 [4] 10 [5] 1 10 10 [2] 10 [3] 10 [4] 10 [5]



_Σ_ molgas ( _M_ ⊙ pc [–2] ) _Σ_ molgas ( _M_ ⊙ pc [–2] )


Fig. 4 | Pressure confinement versus self-gravitating confinement of the Cosmic Snake GMCs. a, Internal
kinetic pressure ( _P_ int / _k_ ) of GMCs hosted in the Cosmic Snake galaxy (magenta data points) plotted as a function
of their molecular gas mass surface density ( _Σ_ molgas ). The dotted lines show the range of possible internal
pressures and surface densities of the Cosmic Snake GMCs as determined with two extreme CO-to-H 2
conversion factors: the Milky Way value of 4.36 _M_ ⊙ (K km s [−1] pc [2] ) [−1] and the starburst value of 1.0 _M_ ⊙ (K km s [−1]
pc [2] ) [−1] (ref. [24] ). For comparison, we consider the same local GMC populations as in Fig. 3. b, To analyse the
dynamical state of GMCs, we plot the size–velocity dispersion coefficient ( _c_ ) as a function of molecular gas mass
surface density ( _Σ_ molgas ). Virialized GMCs are expected to lie on the one-to-one relationship _Σ_ molgas ≈ 330% [2] &/'
(black solid line [1][,][17][,][23] ). The dotted lines show the range of possible surface densities of molecular gas mass for
Cosmic Snake GMCs, determined with two extreme CO-to-H 2 conversion factors as in a. Fourteen out of the 17
Cosmic Snake GMCs, highlighted by magenta filled circles, are virialized within a factor of 3 of the one-to-one
relationship (black dashed lines) regardless of the CO-to-H 2 conversion factor. In a and b, the error bars
associated with the Cosmic Snake GMCs reflect the overall uncertainty described in Fig. 3.

(Supplementary Fig. 5). This shows that despite the Cosmic Snake GMCs, we find that the mass of the most
stronger photodissociating radiation expected in high- massive GMCs is only slightly larger than that of the
redshift galaxies due to their increased star-formation most massive stellar clumps (Supplementary Fig. 6). If
rate [12], the CO-to-H 2 conversion factor remains Milky the identified GMCs are representative of the parent
Way-like. The molecular gas mass surface densities of GMC population that gave rise to the observed massive
the Cosmic Snake GMCs happen to be high enough to star cluster complexes, this would indicate a fairly high
shield the clouds from ambient radiation. star-formation efficiency of ~26–34% in the Cosmic
The GMCs hosted in the Cosmic Snake galaxy are Snake galaxy, much higher than the canonical values of
highly supersonic. Their median Mach number of 80 (see ≲6% measured in present-day galaxies [27] . This result is at
Methods) exceeds that of typical local GMCs by almost odds with the universally slow/inefficient star formation,
a factor of ten [23] . This enhanced turbulence may imply a but it anchors the recently predicted scaling of starhigh efficiency of star formation, since star clusters are formation efficiency with gas mass surface density [28],
expected to form by gravitational collapse of shock- which agrees with the inferred efficiency of star
compressed density fluctuations generated from the formation for the median surface density of 2,600 _M_ ⊙
supersonic turbulence in molecular clouds [25][,][26] . As we pc [−2] found for the Cosmic Snake GMCs. The strong shear
have identified, at a comparable spatial resolution, stellar observed over the Cosmic Snake galactic disk, except
clumps and GMCs in the same high-redshift galaxy, it is inside the internal 400 pc (see Methods), regulates the
tempting to estimate the efficiency of star formation in a star formation by stabilizing GMCs against collapse and
similar way as for the local Universe [27] by comparing the star formation while keeping the star-formation timescale
derived star cluster stellar masses [7] with the molecular gas close to, but shorter than, the shear timescale, such that
masses of the detected GMCs. Adopting the above CO- star formation is not stopped [29] . The extensive tidal forces
to-H 2 conversion  factor calibrated  for the  virialized also found over the same disk domain (see Methods)


5

similarly moderate the star formation by preventing
massive molecular clouds from collapsing [30] .
The molecular clouds detected in the Cosmic Snake
galaxy demonstrate the existence of parent gas clouds
with masses high enough to allow in situ formation of the
massive stellar clumps seen in the galaxy. Furthermore,
the GMCs found in virial equilibrium and the stellar
clumps show comparable distributions in mass to,
respectively, the gravitationally bound gas clouds and
stellar clumps produced in simulated host disk galaxies
with a baryonic mass similar to that of the Cosmic Snake
galaxy [8] . Altogether, these results offer new evidence of
disk fragmentation as the main mechanism of formation
of massive molecular clouds in distant galaxies.

**Methods**

**Lens model.** The Cosmic Snake galaxy is strongly lensed
by the galaxy cluster MACS J1206.2–0847 (ref. [16] ). It is
multiply imaged along a snake-like giant arc and has
another isolated counter-image (henceforth dubbed
‘Counterimage’). The tailored lens model of the cluster,
refined to match the arc in the image plane, was published
in ref. [7] and is adopted here. Lenstool [31] was used to
optimize all the model parameters for the total cluster mass
distribution, plus the potentials of four cluster members
located close to the arc. The resulting root-mean-square
(RMS) noise between the predicted and observed locations
of the strong lensing constraints as measured in the image
plane is as good as 0.15″. To estimate the uncertainty on
magnification factors, we generated 3,000 lens models
based on the Markov chain Monte Carlo output from
Lenstool, sampling the posterior probability distribution of
the lens model parameters. The median absolute deviation
of magnification factors derived from the 3,000 lens
models was used as the uncertainty on the magnification
factors inferred from the tailored lens model.
The Cosmic Snake arc is a four-fold multiple image
with magnifications between 10 and >100 (see the critical
line at _z_ =1.036, shown in red in Fig. 1). The northern and
southern parts of the arc are the counter-images of slightly
more than 50% of the source galaxy, and the arc’s central
part comprises two counter-images of slightly less than
20% of the source galaxy, but more strongly magnified.
The global view of the source galaxy is accessible through
the source-plane reconstruction of the Counterimage,
uniformly magnified by a factor of 4.3 (ref. [7] ).

**Observations, data reduction and imaging.** ALMA
observations of the Cosmic Snake arc were delivered in
August 2015. The field of view was centred at
RA = +12h 06min 10.76s and Dec = −08° 48′ 04.80″.  Onsource integration time of 52.3 minutes was obtained in
band 6 with 38 12m antennae in the extended C38-5
configuration, with maximum and minimum baselines of
1.6km and 47m, respectively. The spectral window 2, with
a spectral resolution set to 7.8125MHz (~10.343kms [−1] ),
was tuned at 226.44 GHz, the redshifted CO(4–3) line



frequency. The other three 1.875GHz spectral windows
were used for continuum emission.
The data were reduced as part of the standard
automated reduction procedure using the pipeline
distribution of the Common Astronomy Software
Application (CASA [32] ) package, version 4.2.2. 3C273 was
selected as flux calibrator, while J1216–1033 and J1256–
0547 were used for bandpass and phase calibrations. A
careful flagging of the pipeline-calibrated visibilities
yielded an improvement of ~10% in the final RMS.
We first imaged the calibrated visibilities of continuum
over the four spectral windows by excluding channels
where the CO(4–3) emission was detected and channels
contaminated by the atmospheric line at 239.1GHz. The
detected 1 mm continuum was then subtracted from
CO(4–3) spectral line visibilities. The CO(4–3) line
imaging was performed with Briggs weighting and robust
factor of 0.5, while interactively cleaning all channels with
the ‘clean’ routine in CASA, using a custom mask, until
convergence. The adopted weighting scheme, recognized
to yield lower sidelobe levels for ~1 hour observations
(ALMA Technical Handbook), gave a good trade-off
between resolution and sensitivity. Finally, we performed
the primary beam correction. The resulting CO(4–3) line
data cube has a synthesized beam size of 0.22″ × 0.18″ at
the position angle of +85° and an RMS of 0.29mJybeam [−1]
per 10.343kms [−1] channel.
Moment maps of the CO(4–3) emission were obtained
using the ‘immoments’ routine in CASA, and by setting
the threshold to the 3 _σ_ RMS level when computing the first
velocity moment and the second velocity dispersion
moment. The contours of the CO(4–3) integrated intensity
are plotted in Fig. 1. The source-plane reconstruction
shows that the CO(4–3) emission is confined inside the
1.7kpc galactocentric radius of the Cosmic Snake source
galaxy. The maximum recoverable scale of the
observations, _θ_ MRS = 3.4″, is comparable to the maximum
size of the molecular component in the Cosmic Snake arc
of ~3″ (that is, ~4.5kpc for the mean magnification factor
of 29.6 over the CO(4–3) emission). We are thus confident
that we recovered all the expected sizes of the CO(4–3)
emission, and no large-scale structure was filtered out.
The same immoments routine in CASA was used to
extract the 26-channel intensity maps, at the native spectral
resolution of 10.343kms [−1], of the CO(4–3) emission
distributed over velocities from –120kms [−1] to +140kms [−1],
with the zero velocity set to _z_ =1.036. The corresponding
channel maps are shown in Supplementary Fig. 1.
Plateau de Bure interferometer (PdBI) observations of
the Cosmic Snake arc were conducted in November 2012
using six antennas in compact D-configuration. The
frequency was tuned at 113.23GHz, the redshifted
frequency of the CO(2–1) line. We used the WideX
correlator, which provided continuous 3.6GHz coverage in
dual polarization with a fixed channel spacing of
1.95MHz. The on-source integration time was 2.16 hours.
Standard data reduction was performed using the GILDAS
software packages CLIC and MAPPING. The data were
mapped with the ‘clean’ procedure using the hogbom
deconvolution algorithm and combined with natural



6

weighting. The resulting CO(2–1) line data cube has a
synthesized beam size of 4.07″ × 2.04″ at the position
angle of +19° and an RMS of 1.78mJybeam [−1] per
31.771kms [−1] channel. We obtained the CO(2–1) integrated
intensity map by averaging the cleaned, weighted images
over channels where emission was detected. No continuum

was detected.
The integrated ALMA CO(4–3) and PdBI CO(2–1)
line profiles were best fitted with a double Gaussian
function, using a nonlinear _χ_ [2] minimization and the
Levenberg–Marquardt algorithm (Supplementary Fig. 2).
We inferred observed (not lensing-corrected) total lineintegrated fluxes of (5.2 ± 0.4)Jykms [−1] and
(3.2 ± 0.6)Jykms [−1] for  CO(4–3) and CO(2–1),
respectively. They yield a CO luminosity correction factor


′ ′

_푟_ 4,2 = _퐿_ CO(4−3 ) [/] _[퐿]_ CO(2−1) [=] [0.41±0.08][ for the Cosmic Snake ]



′



′



_푟_ 4,2 = _퐿_ CO(4−3 ) [/] _[퐿]_ CO(2−1) [=] [0.41±0.08][ for the Cosmic Snake ]

galaxy, in line with the CO excitation observed in _z_ ~1.5
BzK galaxies [33] . This further suggests that we do not lose
flux in the ALMA high-resolution observations.

**Molecular cloud identification.** To search for molecular
clouds in the Cosmic Snake galaxy, we exploited the three
dimensions of the data cube for the CO(4–3) line, through
the analysis of the 26-channel maps extracted over
the CO(4–3) emission. To evaluate the reliability of an
emission detection against noise, we computed the fidelity
of our search at a given emission candidate significance:



CO(4−3 ) [/] _[퐿]_



Fidelity( _S_ / _푁_ ) = 1−



) *+, (.⁄))

) 123 (.⁄))



where _N_ pos ( _S_ / _N_ ) and _N_ neg ( _S_ / _N_ ) are, respectively, the
number of positive and negative emission candidates with
a given signal-to-noise ratio ( _S_ / _N_ ) in the primary beam [34] .
In individual channel maps, the fidelity of 100% is reached
at _S_ / _N_ = 6.3. Therefore, we extracted all ≥6 _σ_ emissions per
channel. We then imposed, as an additional detection
criterion, emissions spatially overlapping in two adjacent
10.343kms [−1] channel maps. The corresponding fidelity
reaches 100% at _S_ / _N_ = 4 per channel, equivalent to
_S_ / _N_ = 5.7 for two adjacent channels. We thus also extracted
all ≥4 _σ_ emissions co-spatial in two adjacent channel maps.
All the extracted CO(4–3) emissions happen to overlap the
location of the Cosmic Snake arc’s detected CO(4–3)
integrated intensity.
The lens model accuracy enabled us to cross-match the
extracted emissions with 40 counter-images of 17
molecular clouds, which appear as multiply (twice to four
times) imaged CO(4–3) emissions in the 26-channel maps
analysed (Supplementary Fig. 1). We considered CO(4–3)
emissions as belonging to distinct molecular clouds when
their 4 _σ_ contours were not spatially overlapping in the
same channel map, or when their 4 _σ_ contours were cospatial, but not in adjacent channel maps (that is, when
separated by at least one channel). This allows molecular
clouds to overlap in either velocity or physical space, but
not both. The 17 identified molecular clouds are detected
at a significance level >6–27 _σ_ when integrated over their
extent in velocity (Supplementary Table 1).



The 17 molecular clouds are spread over two and more
adjacent channels, meaning either they really are spatially
extended along the line of sight, or some of them are
molecular cloud associations, composed of several
independent GMCs blended along the line of sight, which
only observations with better spectral resolution will
dissociate. We also find distinct molecular clouds
distributed along the same line of sight (for example clouds
4, 8 and 12; Supplementary Fig. 1).
To evaluate the reliability of the detected clouds
against a possibly CO(4–3) smooth exponential disk that
could appear artificially clumpy due to lensing and
interferometric effects [35], we performed CASA visibility
simulations with the ‘simobserve’ routine by setting up the
frequency, bandwidth, ALMA configuration, precipitable
water vapour and exposure time to our ALMA
observations. We produced realistic input models in the
image plane, using Lenstool and the tailored lens model,
of, first, a smooth exponential disk in the source plane with
disk characteristics comparable to the Cosmic Snake
galaxy (effective radius of 0.75 kpc as measured from the
radial profile of the CO(4–3) flux surface density; rotation
velocity as determined from the CO(4–3) velocity map;
data cube channel sampling of 10kms [−1] ) and, second, of
clumps placed over the underlying exponential disk. At a
noise level comparable to our ALMA observations and for
the observed total CO(4–3) line-integrated flux of
(5.2 ± 0.4)Jykms [−1], the CASA-simulated channel intensity
maps show that only when this total flux is distributed in
clumps do we detect the corresponding clump emissions,
whereas when the total flux is distributed across the
smooth exponential component it remains undetected
(Supplementary Fig. 3).

**Molecular cloud physical properties.** The molecular gas
masses, sizes and velocity dispersions were derived
independently for each counter-image of the 17 molecular
clouds identified in the Cosmic Snake galaxy.
The CO(4–3) line-integrated flux of a given counterimage, needed for the gas mass estimate, was obtained by
summing the fluxes of all the CO(4–3) emissions extracted
over channels encompassed by that counter-image. The
fluxes were measured using custom apertures per channel,
large enough to include, for each associated emission, all
the signal above local noise level. For cases in which the
≥3 _σ_ intensity contours of emissions associated with
different counter-images were spatially blended in a
channel map, we redistributed the blended flux among
counter-images proportionally to their respective fluxes
measured above the threshold at which they started to be
unblended. Each measured flux per channel, before
summing, was lensing-corrected by the harmonic mean
magnification factor ( _µ_ ) estimated over the area subtended
by the 4 _σ_ intensity contour of the associated emission. The
resulting total lensing-corrected CO(4–3) line-integrated
fluxes obtained for different counter-images of the same
molecular cloud agree within better than a factor of 2
(1–2 _σ_ flux error).
Altogether the 40 counter-images of the 17 molecular
clouds account for 77% of the total CO(4–3) line

7

integrated flux (that is, 4.0 ± 0.4Jykms [−1], not lensingcorrected). We thus expect ~23% of the total flux to be in
diffuse CO(4–3) emission.
To determine the molecular gas masses (4 56789: ), we
adopted the CO luminosity correction factor


′ ′

_푟_ 4,1 = _퐿_ CO(4−3) [/] _[퐿]_ CO(1−0) [=] [0.33][, extrapolated from ] _[r]_ [4,2]



′



′



_푟_ 4,1 = _퐿_ CO(4−3) [/] _[퐿]_ CO(1−0) [=] [0.33][, extrapolated from ] _[r]_ [4,2]

measured in the Cosmic Snake galaxy and _r_ 2,1 reported in _z_
~1.5 BzK galaxies [33], and assumed a CO-to-H 2 conversion
factor ( _α_ CO ):



CO(4−3) [/] _[퐿]_



4 56789: =
;



< =>
? ⊙ (@ A5 : [BC ] DE [F] ) [BC] [G;]



H@ A5 : [I] =>(JBK [BC ] ) /M.OODE [F] ~~[ G]~~ [4] [⊙]



where the CO(4–3) luminosity is derived from the
CO(4–3) line-integrated flux [36] .
The size of a given counter-image was estimated by
measuring, in each channel map encompassed by that
counter-image, the radius of the associated CO(4–3)
emission, and we adopted the larger radius measured as the
radius of that counter-image. This gave a conservative
estimate of the cloud radius, since a size variation of the
CO(4–3) emission from channel-to-channel of a given
counter-image might reflect a physical size variation of the
cloud in 10.343kms [−1] slices. More specifically, we
measured per channel the major ( _a_ ) and minor ( _b_ ) semiaxes of the elliptical region that best approximated the area
subtended by the 4 _σ_ intensity contour of the associated
emission. We defined the equivalent circularized radius,
' EPQERS = √VW. Assuming a two-dimensional Gaussian

distribution of the CO(4–3) emission with a peak flux
X DY9A, we computed the circularized radius at the fullwidth half-maximum,



yielded consistent velocity dispersion measurements per
counter-image and for different counter-images of the
same molecular cloud. We considered measurements from
the second approach.
In Supplementary Table 1 we summarize the physical
properties of the 17 molecular clouds identified in the
Cosmic Snake galaxy, adopted from respective counterimages that had the less blended CO(4–3) emissions in
channel maps. In Supplementary Fig. 4 we show the
derived molecular gas masses and radii as a function of
lensing magnification factor, together with the
magnification-dependent 5.7 _σ_ detection limit of the
molecular gas mass (corresponding to 100% fidelity) and
the magnification-dependent equivalent circularized beam
detection limit. All the Cosmic Snake GMCs have masses
and radii larger than their respective magnificationdependent detection limit, indicating they are spatially
resolved. However, as noted above, it remains hard to
distinguish between an individual GMC and an association
of molecular clouds superposed along the line of sight. The
70° inclination of the Cosmic Snake galaxy [13] is favourable
for possible projection effects along lines of sight.
Therefore, when referring to GMC masses and radii, we
should keep in mind they may still be upper limits.
The virial masses (4 pPQP97 ) were computed under the
assumption that GMCs are spherical and have a density
profile inversely proportional to radius [1,37] :



4 pPQP97 % w r
= 1,040 {km s [l•] ~~[Ä]~~



;pc ['] ~~[G]~~ [ 4] [⊙]



' Z[\] = ' EPQERS DY9A /RMS)⁄4). For cases in

^ln(2) /ln ((X

which the 4 _σ_ contours of emissions associated with
different counter-images were spatially blended in a
channel map, we used intensity contours at the RMS level
at which they started to be unblended to derive ' Z[\] .
The radii were then beam-deconvolved and demagnified
by the magnification factor used for the lensing-correction
of the corresponding CO(4–3) flux. The resulting physical
radii obtained for different counter-images of the same
molecular cloud agree, in general, within better than a
factor of 2 (1–2 _σ_ ' Z[\] /√ ~~f~~ error).
We used two approaches to determine the velocity
dispersion of a given counter-image. First, we measured at
the location of that counter-image the average velocity
dispersion in the CO(4–3) velocity dispersion map.
Second, we extracted the integrated CO(4–3) line
spectrum of that counter-image, and measured the line
FWHM by fitting a Gaussian function. The FWHM was
then corrected for final channel spacing:



In Supplementary Fig. 5 we show the virial masses as a
function of lensing-corrected CO(1–0) luminosity for the
17 molecular clouds. The 14 GMCs identified as virialized
(Fig. 4b) are distributed about the mean CO-to-H 2
conversion factor of _α_ CO = 3.8 _M_ ⊙ (Kkms [−1] pc [2] ) [−1] with a
standard deviation of 1.1 _M_ ⊙ (Kkms [−1] pc [2] ) [−1] .
We estimated the internal kinetic pressure (É Pmn / _k_ ) of
the Cosmic Snake GMCs following ref. [6] :



{km s% w [l•] ~~[Ä]~~ r



r



Pmn

Ñ [= 1,176] ~~[á]~~



lO



~~à~~ ;pc ['] ~~[G]~~



cm [lO] K



É Pmn



4 56789:



4
⊙



PmnQPm:PE 6o:YQpYq

jk(RlO) = ^FWHM jk(RlO)



FWHM
jk(RlO)



6o:YQpYq [r] −10.343 r, where



10.343kms [−1] is the spectral resolution that, in our spectral
configuration, equals the final channel spacing (ALMA
Technical Handbook). We obtained the velocity dispersion
from % w = FWHM jk(RlO)PmnQPm:PE /x8 ln (2). The two approaches



It varies over ~10 [6.5] –10 [8.6] cm [−3] K (Fig. 4a).


The Mach number ( __ ) was derived similarly to ref. [23] :


__ = [√][OS] [ä]

ã 3


where the sound speed _c_ s = 0.45kms [−1] was calculated for
molecular hydrogen at 35K (but does not change much for
typical temperatures of 20–50K). We obtained a median
Mach number of 80 ± 13 for the 17 molecular clouds in the
Cosmic Snake galaxy.
Stellar clumps were analysed throughout the HST
ultraviolet to near-infrared images of the Cosmic Snake arc
in ref. [7] . In Supplementary Fig. 6 we show the respective
mass distributions of these stellar clumps and GMCs


8

[é]

2 [G Σ] [89:] [ ;Σ] [89:] [ +]



identified in this work. Their comparison can be used to
estimate the efficiency of star formation of the galaxy,
å = 4 stars /(4 stars +4 molgas ) (ref. [27] ).

**Galactic shear, tides and hydrostatic pressure.** We used
the Counterimage to determine the radial profile of the
stellar mass of the whole Cosmic Snake galaxy. We
extracted the aperture-corrected photometry in the 16 HST
bands, available through the Cluster Lensing and
Supernovae survey with HST (CLASH [38] ), within 20
elliptical regions of the Counterimage. They correspond to
projections of 20 successive source-plane ellipses, oriented
along the position angle of +308°, starting at the
galactocentric radius of 360pc and in steps of 150pc. We
derived stellar masses contained within these elliptical
regions using the updated version of the Hyperz fitting
code for photometric redshift and spectral energy
distribution [39] . We used the energy-conserving models [40][,][41]
in which the dust attenuation was fixed at the observed
ratio of the infrared luminosity (derived from Herschel and
Spitzer photometry) over the ultraviolet luminosity [7] .
Stellar tracks from ref. [42] at solar metallicity were adopted,
and we allowed for variable star-formation histories,
parameterized by exponentially declining models with
timescales varying from 10Myr to infinity. Nebular
emission was neglected. We adopted the Salpeter initial
mass function [43] . The resulting cumulative lensingcorrected stellar mass distribution plotted as a function of
galactocentric radius, with errors corresponding to 68%
confidence level, is shown in Supplementary Fig. 7.
From this radial profile of stellar mass, assuming the
mass is confined to a thin disk with global axisymmetry,
and adding the measured molecular gas to stellar mass
fraction of 25% ± 4%, we derived the rotation curve from
the circular velocity, _V_ cir, the angular velocity, Ω = _V_ cir / _R_,
and the amount of shear quantified as dΩ/d _R_, where _R_ is
the galactocentric radius (Supplementary Fig. 8). The shear
is fairly strong all over the disk, since the rotation curve is
relatively flat and drops only inside 400pc. The ratio of the
shear timescale, _t_ sh = 2/ _R_ d _R_ /dΩ, over the star-formation
timescale, _t_ SF = 0.2 _t_ orbit (ref. [44] ), equals ~1.7 over the disk,
except inside 400pc where it rises to 8–10. The shear
cannot stop star formation, especially in the centre. It only
limits the size of the larger GMCs. In Supplementary
Fig. 8 we also added the normalized shear,
–d log(Ω)/d log( _R_ ), which is 1.6 _t_ SF / _t_ sh . The corresponding
Toomre critical velocity dispersion to stabilize the disk,
defined as _V_ crit = πGΣ/ _κ_ with Σ the surface density and _κ_
the epicyclic frequency, drops below 40kms [−1] at 1.7kpc
and remains low around 30kms [−1] until 7kpc. This means
the disk should be stable, except maybe in the centre.
Finally, we computed the tidal forces in the disk as the
derivative of the radial force or Ω [2] _R_ . They are extensive
(and not compressive) over the disk, with an absolute value
stronger in the centre.
We approximated the pressure at the boundary of a
given molecular cloud by the hydrostatic pressure at the
disk midplane for a two-component disk of gas and stars [45] :



where Σ 89:, Σ :n9Q:, and % 89:, % :n9Q: are the surface
densities and velocity dispersions of the gas and stars,
respectively. We considered the molecular gas phase as the
dominant phase of the neutral (atomic + molecular) gas in
this _z_ ≃1 galaxy. We derived surface densities from the
molecular gas and stellar masses contained within the
observed gas disk of 1.7kpc in galactocentric radius, and
assumed the velocity dispersions of gas and stars to be
comparable. We obtained the hydrostatic pressure of
~10 [7.7] cm [−3] K in the Cosmic Snake galaxy.

**Data availability**
The ALMA raw data of the Cosmic Snake arc are available
through the ALMA archive under the project identification
2013.1.01330.S. The HST images of MACS J1206.2–0847
are part of the CLASH, available at
https://archive.stsci.edu/prepds/clash/. The data that
support the plots within this paper and other findings of
this study are available from the corresponding author
upon reasonable request.

**Code availability**
The reduction of the ALMA data was performed with the
CASA pipeline version 4.2.2, available at
https://almascience.eso.org/processing/science-pipeline.
The PdBI data were reduced using GILDAS software,
available at http://www.iram.fr/IRAMFR/GILDAS. The
lens model was obtained using Lenstool, publicly available
at https://projets.lam.fr/projects/lenstool/wiki. The spectral
energy distribution fitting was performed with a modified
version of the Hyperz code, available in its original form at
https://ascl.net/1108.010.

**References**

1.  Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter,

F. & Blitz, L. The resolved properties of extragalactic
giant molecular clouds. _Astrophys. J._ **686**, 948–965
(2008).
2.  Swinbank, A. M. et al. ALMA resolves the properties

of star-forming regions in a dense gas disk at z ~ 3.
_Astrophys. J._ **806**, L17–L22 (2015).
3.  Sharda, P., Federrath, C., da Cunha, E., Swinbank,

A. M. & Dye, S. Testing star formation laws in a
starburst galaxy at redshift 3 resolved with ALMA.
_Mon. Not. R. Astron. Soc._ **477**, 4380–4390 (2018).
4.  Tadaki, K. et al. The gravitationally unstable gas disk

of a starburst galaxy 12 billion years ago. _Nature_ **560**,
613–616 (2018).
5.  Sun, J. et al. Cloud-scale molecular gas properties in

15 nearby galaxies. _Astrophys. J._ **860**, 172–211 (2018).
6.  Hughes, A. et al. A comparative study of giant

molecular clouds in M51, M33, and the Large
Magellanic Cloud. _Astrophys. J._ **779**, 46–66 (2013).
7.  Cava, A. et al. The nature of giant clumps in distant

galaxies probed by the anatomy of the Cosmic Snake.
_Nat. Astron._ **2**, 76–82 (2018).


9



É Yçn



% 89:

% :n9Q:



Σ :n9Q: K
Gcm [lO]



Yçn = [é]

Ñ 2

8.  Tamburello, V., Mayer, L., Shen, S. & Wadsley,

J. A lower fragmentation mass scale in high-redshift
galaxies and its implications on giant clumps: a
systematic numerical study. _Mon. Not. R. Astron. Soc._
**453**, 2490–2514 (2015).
9.  Mandelker, N. et al. Giant clumps in simulated

high-z galaxies: properties, evolution and dependence
on feedback. _Mon. Not. R. Astron. Soc._ **464**, 635–665
(2017).
10. Guo, Y. et al. Clumpy galaxies in CANDELS. I.

The definition of UV clumps and the fraction of
clumpy galaxies at 0.5 < z < 3. _Astrophys. J._ **800**, 39–60
(2015).
11. Behroozi, P. S., Wechsler, R. H. & Conroy, C. The

average star formation histories of galaxies in dark
matter halos from z = 0–8. _Astrophys. J._ **770**, 57–93
(2013).
12. Rodighiero, G. et al. The lesser role of starbursts in star

formation at z = 2. _Astrophys. J._ **739**, L40–L46 (2011).
13. Patrício, V. et al. Kinematics, turbulence, and star

formation of z ~ 1 strongly lensed galaxies seen with
MUSE. _Mon. Not. R. Astron. Soc._ **477**, 18–44 (2018).
14. Wisnioski, E. et al. The KMOS [3D] survey: design, first

results, and the evolution of galaxy kinematics from
0.7 ≤ z ≤ 2.7. _Astrophys. J._ **799**, 209–236 (2015).
15. Dekel, A. et al. Cold streams in early massive hot

haloes as the main mode of galaxy formation. _Nature_
457, 451–454 (2009).
16. Ebeling, H. et al. A spectacular giant arc in the massive

cluster lens MACS J1206.2-0847. _Mon. Not. R. Astron._
_Soc._ **395**, 1213–1224 (2009).
17. Heyer, M., Krawczyk, C., Duval, J. & Jackson, J. M.

Re-examining Larson’s scaling relationships in galactic
molecular clouds. _Astrophys. J._ **699**, 1092–1103
(2009).
18. Donovan Meyer, J. et al. Resolved giant molecular

clouds in nearby spiral galaxies: insights from the
CANON CO(1–0) survey. _Astrophys. J._ **772**, 107–123
(2013).
19. Colombo, D. et al. The PdBI Arcsecond Whirlpool

Survey (PAWS): environmental dependence of giant
molecular cloud properties in M51. _Astrophys. J._ **784**,
3–35 (2014).
20. Corbelli, E. et al. From molecules to young stellar

clusters: the star formation cycle across the disk of
M33. _Astron. Astrophys._ **601**, 146–164 (2017).
21. Larson, R. B. Turbulence and star formation in

molecular clouds. _Mon. Not. R. Astron. Soc._ **194**,
809–826 (1981).
22. Wei, L. H., Keto, E. & Ho, L. C. Two populations of

molecular clouds in the Antennae galaxies. _Astrophys._
_J._ 750, 136–154 (2012).
23. Leroy, A. K. et al. ALMA reveals the molecular

medium fueling the nearest nuclear starburst.
_Astrophys. J._ **801**, 25–53 (2015).
24. Bolatto, A. D., Wolfire, M. & Leroy, A. K. The

CO-to-H 2 conversion factor. _Annu. Rev. Astron._
_Astrophys._ **51**, 207–268 (2013).



25. McKee, C. F. & Ostriker, E. C. Theory of star

formation. _Annu. Rev. Astron. Astrophys._ **45**, 565–687
(2007).
26. Brunt, C. M., Heyer, M. H. & Mac Low, M.-M.

Turbulent driving scales in molecular clouds. _Astron._
_Astrophys._ **504**, 883–890 (2009).
27. Evans, N. J. II et al. The Spitzer c2d legacy results:

star-formation rates and efficiencies; evolution and
lifetimes. _Astrophys. J. Suppl._ **181**, 321–350 (2009).
28. Grudić, M. Y. et al. When feedback fails: the scaling

and saturation of star formation efficiency. _Mon. Not._
_R. Astron. Soc._ **475**, 3511–3528 (2018).
29. Kruijssen, J. M. D. et al. What controls star formation

in the central 500 pc of the Galaxy? _Mon. Not. R._
_Astron. Soc._ **440**, 3370–3391 (2014).
30. Renaud, F., Boily, C. M., Fleck, J.-J., Naab, T. &

Theis, Ch. Star cluster survival and compressive tides
in Antennae-like mergers. _Mon._ _Not. R. Astron. Soc._
**391**, L98–L102 (2008).
31. Jullo, E. et al. A Bayesian approach to strong lensing

modelling of galaxy clusters. _New J. Phys._ **9**, 447
(2007).
32. McMullin, J. P., Waters, B., Schiebel, D., Young, W.

& Golap, K. in _Astronomical Data Analysis Software_
_and Systems XVI_, Vol. 376 (eds. Shaw, R. A. et al.) 127
(Astronomical Society of the Pacific, 2007).
33. Daddi, E. et al. CO excitation of normal star-forming

galaxies out to z = 1.5 as regulated by the properties of
their interstellar medium. _Astron. Astrophys._ **577**,
A46–A65 (2015).
34. Walter, F. et al. ALMA Spectroscopic Survey in the

Hubble Ultra Deep Field: survey description.
_Astrophys. J._ **833**, 67–82 (2016).
35. Hodge, J. A. et al. Kiloparsec-scale dust disks in high
redshift luminous submillimeter galaxies. _Astrophys. J._
**833**, 103–118 (2016).
36. Solomon, P. M., Downes, D., Radford, S. J. E. &

Barrett, J. W. The molecular interstellar medium in
ultraluminous infrared galaxies. _Astrophys. J._ **478**,
144–161 (1997).
37. Solomon, P. M., Rivolo, A. R., Barrett, J. & Yahil, A.

Mass, luminosity, and line width relations of Galactic
molecular clouds. _Astrophys. J._ **319**, 730–741 (1987).
38. Postman, M. et al. The cluster lensing and supernova

survey with Hubble: an overview. _Astrophys. J. Suppl._
_Ser._ **199**, 25–47 (2012).
39. Schaerer, D. & de Barros, S. On the physical properties

of z ~ 6–8 galaxies. _Astron. Astrophys._ **515**, A73–A88
(2010).
40. Schaerer, D., de Barros, S. & Sklias, P. Properties of

z ~ 3–6 Lyman break galaxies. I. Testing star formation
histories and the SFR–mass relation with ALMA and
near-IR spectroscopy. _Astron. Astrophys._ **549**, A4–A24
(2013).
41. Sklias, P. et al. Star formation histories, extinction, and

dust properties of strongly lensed z ~ 1.5–3 starforming galaxies from the Herschel Lensing Survey.
_Astron. Astrophys._ **561**, A149–A176 (2014).



10

42. Bruzual, G. & Charlot, S. Stellar population synthesis

at the resolution of 2003. _Mon. Not. R. Astron. Soc._
**344**, 1000–1028 (2003).
43. Salpeter, E. E. The luminosity function and stellar

evolution. _Astrophys. J._ **121**, 161–167 (1955).
44. Elmegreen, B. G. Theory of starbursts in nuclear rings.

_Rev. Mex. Astron. Astrofis. Conf. Ser._ **6**, 165 (1997).
45. Elmegreen, B. G. Molecular cloud formation by

gravitational instabilities in a clumpy interstellar
medium. _Astrophys. J._ **344**, 306–310 (1989).

**Acknowledgements**
The work of M.D.-Z., D.S., L.M. and A.C. was supported
by the STARFORM Sinergia Project funded by the Swiss
National Science Foundation. J.R. acknowledges support
from the European Research Council starting grant
336736-CALENDS. W.R. is supported by the Thailand
Research Fund/Office of the Higher Education
Commission Grant Number MRG6280259 and
Chulalongkorn University’s CUniverse. P.G.P.-G.
acknowledges support from the Spanish Government grant
AYA2015-63650-P. This paper makes use of the following
ALMA data: ADS/JAO.ALMA#2013.1.01330.S. ALMA
is a partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ. We also used PdBI observations.
PdBI is run by the Institut de Radioastronomie
Millimétrique (IRAM, France), a partnership of the French



CNRS, the German MPG and the Spanish IGN. Part of the
analysis presented herein is also based on observations
made with the NASA/ESA Hubble Space Telescope, and
obtained from the Hubble Legacy Archive, which is a
collaboration between the Space Telescope Science
Institute (STScI/NASA), the Space Telescope European
Coordinating Facility (ST-ECF/ESA) and the Canadian
Astronomy Data Centre (CADC/NRC/CSA). We thank E.
Chapillon from the ALMA Regional Center node of IRAM
for her help and training on the reduction of the ALMA
data, V. Patricio for sharing the kinematic analysis of the

[O II ] emission of the Cosmic Snake galaxy and C. Georgy
for the presentation of the VisIt 3D visualization tool.

**Author contributions**

The data reduction was performed by M.D.-Z. W.R.
contributed to the production of the final CO(4–3) data
cube. J.R. and A.C. were responsible for the lens model.
M.D.-Z. carried out all the data analysis, following advice
from J.R., A.C., F.C., W.R. and F.B. F.C. computed the
radial dynamical properties and associated figures. Data
interpretation was led by M.D.-Z., with feedback from
F.C., D.S., L.M., D.P. and R.T. The main text and
Methods, with related figures and table, were written by
M.D.-Z. All authors commented on the paper, with
particular involvement of D.S., L.M., F.C. and T.D.R.

**Supplementary Information** Figs. 1–8, Table 1.



11

## **Supplementary Information**

This section contains all the supplementary data (8 figures and 1 table) supporting the analysis
presented in the main paper and the Method section.

**Supplementary** **Figure** **1** | **a**, Velocity map obtained with a threshold set to 0.9 mJy beam [−][1],
equivalent to 3 times the RMS noise level per beam. The color-coding ranges from −120 km s [−][1]

(magenta/blue) to +140 km s [−][1] (red). The red solid line shows the critical line at _z_ = 1 _:_ 036 of
our tailored lens model. **b** – **e**, Channel intensity maps of the CO(4–3) emission at the native spectral
resolution of 10 _:_ 343 km s [−][1] with gold contour levels starting at ±3 _ff_ and in steps of 1 _ff_ (RMS =
0 _:_ 003 Jy beam [−][1] km s [−][1] ); dashed gold contours for negative values. The plotted ellipses, color-coded
following the velocity map at their location, denote the 4 _ff_ intensity contours (and sometimes the 3 _ff_
intensity contours (for labels in parenthesis) if clearly identified) of the extracted CO(4–3) emissions
corresponding to 40 counter-images of 17 molecular clouds. They are labelled with letters ‘N’, ‘C’
and ‘S’ that refer to the counter-images detected, respectively, in the northern (N), central (C) north
and south, and southern (S) parts of the Cosmic Snake arc. The numbers which follow the letters
enumerate the 17 molecular clouds. Capital(small) letters correspond to equivalent circularised radii
of the 3 _ff_ intensity contours of the extracted CO(4–3) emissions bigger(smaller) than the equivalent
circularised radius of the beam.

|km/s<br>.3467<br>N34<br>,<br>-78<br>(ch109)<br>c3<br>c4<br>C4<br>S4<br>b|Col2|km/s<br>.0034<br>N34<br>,<br>-68<br>(ch110)<br>c3<br>c4<br>s4<br>S5<br>c|Col4|km/s<br>n5<br>.6601<br>-57<br>(ch111)<br>(c3)<br>(c6)<br>c7<br>c6<br>S6<br>S5<br>d|Col6|km/s<br>N5<br>.3169<br>(n8)<br>-47<br>(ch112)<br>(c8)<br>c6<br>C7<br>C6<br>(s6)<br>S5<br>e|
|---|---|---|---|---|---|---|
|s10<br>s9<br>N9,10<br>s8<br>(c8)<br>C8<br>N8<br>C7<br>S5<br>N5<br>(ch113) -36.9736 km/s<br>b|s10<br>s9<br>N9,10<br>s8<br>(c8)<br>C8<br>N8<br>C7<br>S5<br>N5<br>(ch113) -36.9736 km/s<br>b|c12<br>C11<br>S10<br>S9<br>N9,10<br>n8<br>C7<br>S5<br>N5<br>(ch114) -26.6304 km/s<br>c|c12<br>C11<br>S10<br>S9<br>N9,10<br>n8<br>C7<br>S5<br>N5<br>(ch114) -26.6304 km/s<br>c|S12<br>C12<br>C12<br>S11<br>C11<br>C11<br>S10<br>S9<br>(n9,10)<br>C7<br>S5<br>N5<br>(ch115) -16.2871 km/s<br>d|S12<br>C12<br>C12<br>S11<br>C11<br>C11<br>S10<br>S9<br>(n9,10)<br>C7<br>S5<br>N5<br>(ch115) -16.2871 km/s<br>d|s12<br>(c12)<br>C12<br>S11<br>C11<br>C11<br>n11,12<br>s13<br>N13<br>C7<br>S5<br>N5<br>(ch116) -5.9438 km/s<br>e|



**Supplementary** **Figure** **1** | Continued.

|km/s km/s km/s<br>km/s<br>N5 N5 N5 N5<br>N13 3994 7427 0860 4292<br>. . .<br>. +14 +25 +35<br>+4<br>(ch117)<br>(ch118) (ch119) (ch120)<br>C11 c11<br>C7 C7 C7<br>C7<br>C11 C11 C11<br>(s11) (s11) (s11)<br>s13 s13<br>S5 S5 S5 S5<br>a b c d e<br>km/s km/s km/s km/s<br>N15 n15 n15<br>N5 N5 N14 N5 N5<br>7725 1158 4590 8023<br>. . . .<br>+45 +56 +66 +76<br>(ch121) (ch122) (ch123) (ch124)<br>S14 S14<br>S5 S5 S5 S5<br>a b c s15 d S15 e|Col2|
|---|---|
|a|C7<br>S5<br>N5<br>(ch120) +35.4292 km/s<br>e|
|a|S15<br>n15<br>S5<br>N5<br>(ch124) +76.8023 km/s<br>e|



**Supplementary** **Figure** **1** | Continued.

|(n17) km/s km/s km/s km/s<br>N15 N15 (n15)<br>N5 N5 N5 N16<br>1455 .4888 832 175<br>. .<br>+107 +118<br>.<br>+87 +97<br>(ch125) (ch126) (ch127) (ch128)<br>s5 s5<br>a S15 b S15 c S15 d (s17) e<br>km/s km/s<br>n17<br>N16 (N16)<br>519 .862<br>.<br>+128 +138<br>(ch129) (ch130)<br>a (s17) b c|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|a|N15<br>**S15**<br>**s5**<br>**N5**<br>**(ch125) +87.1455 km/s**<br>b|S15<br>N15<br>s5<br>N5<br>(ch126) +97.4888 km/s<br>c|S15<br>(n15)<br>N5<br>(ch127) +107.832 km/s<br>d|(s17)<br>(n17)<br>N16<br>(ch128) +118.175 km/s<br>e|
|a|(s17)<br>n17<br>N16<br>(ch129) +128.519 km/s<br>b|(N16<br>(ch130) +138.862 km/s<br>c|)<br>|)<br>|



**Supplementary** **Figure** **1** | Continued.

**Supplementary** **Figure** **2** | **a**, ALMA CO(4–3) emission line spectrum in steps of 10 _:_ 343 km s [−][1] .
**b**, PdBI CO(2–1) emission line spectrum in steps of 31 _:_ 771 km s [−][1] . The cyan-shaded regions indicate
channels from −120 km s [−][1] to +140 km s [−][1], where the CO(4–3) and CO(2–1) emissions are detected.
These channels were used to derive the CO(4–3) and CO(2–1) line-integrated fluxes, the CO(4–3)
integrated intensity map, and the CO(4–3) channel intensity maps (Supplementary Figure 1). The
red solid line shows the double Gaussian profile that best fits the observed CO(4–3) and CO(2–1) line
profiles, and the red dotted lines show the individual Gaussian profiles together with their centroids
(vertical black bars). The zero velocity is set to _z_ = 1 _:_ 036.

**a** c e























**Supplementary** **Figure** **3** | **a**, Real ALMA CO(4–3) intensity map of channel 116. **b**, Model of a
lensed smooth exponential disk with an effective radius of 0.75 kpc, plus clumps that contain 77%
of the observed total CO(4–3) line-integrated flux of 5 _:_ 2 ± 0 _:_ 4 Jy km s [−][1] inferred from the ALMA
Cosmic Snake observations (fraction of diffuse gas ⇠ 23%). **c**, CASA simulated channel intensity
map of the model shown in **b** with a noise level comparable to real ALMA observations. The clumps
are clearly detected, but not the smooth disk component. **d**, Model of a lensed smooth exponential
disk in which we now distribute 100% of the observed total CO(4–3) line-integrated flux. **e**, CASA
simulated channel intensity map of the model shown in **d** with a noise level comparable to real ALMA
observations. No emission is detected.

**Supplementary** **Figure** **4** | **a**, Molecular gas masses ( _M_ molgas ) of the Cosmic Snake molecular clouds
plotted as a function of their harmonic mean lensing magnification factor ( _—_ ). The solid line shows
the magnification-dependent 5 _:_ 7 _ff_ detection limit of the molecular gas mass (corresponding to 100%
fidelity). **b**, Circularised FWHM radii ( _R_ FWHM ) of the Cosmic Snake molecular clouds plotted as
a function of their harmonic mean lensing magnification factor ( _—_ ). The dashed line shows the
magnification-dependent equivalent circularised beam detection limit. The error bars include the
measurement uncertainties on the CO(4–3) line flux and radius per molecular cloud, and the uncertainty on the magnification factor per cloud.

**Supplementary** **Figure** **5** | Virial masses ( _M_ virial ) of the Cosmic Snake molecular clouds plotted as
a function of their lensing-corrected CO(1–0) luminosity ( _L_ [0] CO(1−0) [).] [The] [CO(1–0)] [luminosities] [were]

derived from CO(4–3) luminosities assuming the CO(4–3) to CO(1–0) luminosity correction factor
_r_ 4 _;_ 1 = 0 _:_ 33. The magenta filled circles correspond to the 14 molecular clouds identified as virialized.
They are distributed about the mean CO-to-H 2 conversion factor of _¸_ CO = 3 _:_ 8 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1]

(black dashed line) with a standard deviation of 1 _:_ 1 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] (grey shaded area). The
error bars reflect the overall uncertainty, including the measurement uncertainties on the CO(4–3)
line flux, radius, and velocity dispersion per molecular cloud, and the uncertainty on the magnification
factor per cloud.

**Supplementary** **Figure** **6** | Comparison of the gas mass distribution of the Cosmic Snake molecular
clouds (filled magenta histogram) with the stellar mass distribution of the stellar clumps identified
in the HST ultraviolet to near-infrared images (hatched orange histogram). The respective medians
and means are shown by the solid and dotted vertical lines. The medians are 5 _:_ 0 ⇥ 10 [7] _M_ ⊙ for the
molecular clouds and 2 _:_ 6 ⇥ 10 [7] _M_ ⊙ for the stellar clumps. We assume the CO-to-H 2 conversion factor
of 3 _:_ 8 ± 1 _:_ 1 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] determined from the virialized Cosmic Snake molecular clouds
(Supplementary Figure 5).

**Supplementary** **Figure** **7** | Radial profile of the stellar mass of the Cosmic Snake galaxy as derived
from the uniformly magnified Counterimage. We measured lensing-corrected stellar masses ( _M_ stars )
contained within 20 successive elliptical regions sampling galactocentric radii ( _R_ ) from 360 pc to
7.2 kpc in steps of 150 pc. The error bars on stellar masses correspond to 68% confidence level. The
red curve shows the best fitted analytical function to the radial profile.









**Supplementary** **Figure** **8** | Radial dynamical properties obtained from the radial profile of the stellar
mass shown in Supplementary Figure 7, assuming the mass is confined to a thin disk with global
axisymmetry and adding the molecular gas to stellar mass fraction of 25% ± 4%. We derived the
circular velocity ( _V_ cir ; black curve), the angular velocity (⌦; red curve), the shear (d⌦ _=_ d _R_ ; blue curve),
the normalized shear (−d log(⌦) _=_ d log( _R_ ); green curve) and the Toomre critical velocity dispersion
( _V_ crit ; magenta curve) as a function of galactocentric radius ( _R_ ).

**Supplementary** **Table** **1** | Physical properties of the Cosmic Snake molecular clouds.


_F_ CO(4−3) [a] _M_ molgas [b] _R_ FWHM [c] _ff_ _fl_ [d] _—_ [e] Detection [f]

(mJy km s [−][1] ) (10 [7] _M_ ⊙ ) (pc) (km s [−][1] ) significance
Cloud 1 1 _:_ 73 ± 0 _:_ 33 8 _:_ 4 ± 1 _:_ 6 89 ± 21 19 ± 3 68 _:_ 9 ± 16 _:_ 9 10.8 _ff_
Cloud 2 0 _:_ 17 ± 0 _:_ 06 0 _:_ 8 ± 0 _:_ 3 30 ± 10 33 ± 10 223 _:_ 6 ± 23 _:_ 1 6.2 _ff_
Cloud 3 1 _:_ 19 ± 0 _:_ 21 5 _:_ 8 ± 1 _:_ 0 147 ± 29 13 ± 3 71 _:_ 7 ± 17 _:_ 9 8.7 _ff_
Cloud 4 0 _:_ 74 ± 0 _:_ 15 3 _:_ 6 ± 0 _:_ 7 50 ± 7 24 ± 4 48 _:_ 7 ± 6 _:_ 2 6.8 _ff_
Cloud 5 21 _:_ 94 ± 1 _:_ 38 107 ± 7 210 ± 36 32 ± 6 33 _:_ 7 ± 8 _:_ 0 27.3 _ff_
Cloud 6 0 _:_ 42 ± 0 _:_ 15 2 _:_ 0 ± 0 _:_ 7 54 ± 16 17 ± 7 138 _:_ 5 ± 18 _:_ 0 7.4 _ff_
Cloud 7 4 _:_ 53 ± 0 _:_ 31 22 _:_ 0 ± 1 _:_ 5 138 ± 19 31 ± 4 181 _:_ 0 ± 10 _:_ 9 22.5 _ff_
Cloud 8 0 _:_ 49 ± 0 _:_ 13 2 _:_ 4 ± 0 _:_ 6 99 ± 31 18 ± 5 70 _:_ 1 ± 17 _:_ 3 7.7 _ff_
Cloud 9 1 _:_ 34 ± 0 _:_ 31 6 _:_ 5 ± 1 _:_ 5 143 ± 34 13 ± 8 33 _:_ 6 ± 6 _:_ 6 9.0 _ff_
Cloud 10 0 _:_ 33 ± 0 _:_ 10 1 _:_ 6 ± 0 _:_ 5 78 ± 29 14 ± 5 75 _:_ 9 ± 15 _:_ 1 8.3 _ff_
Cloud 11 0 _:_ 84 ± 0 _:_ 10 4 _:_ 1 ± 0 _:_ 5 59 ± 11 22 ± 4 143 _:_ 5 ± 47 _:_ 1 15.1 _ff_
Cloud 12 0 _:_ 30 ± 0 _:_ 06 1 _:_ 5 ± 0 _:_ 3 78 ± 26 17 ± 7 62 _:_ 9 ± 14 _:_ 1 7.2 _ff_
Cloud 13 0 _:_ 42 ± 0 _:_ 12 2 _:_ 0 ± 0 _:_ 6 51 ± 16 21 ± 4 81 _:_ 6 ± 11 _:_ 6 8.1 _ff_
Cloud 14 1 _:_ 22 ± 0 _:_ 34 5 _:_ 9 ± 1 _:_ 6 179 ± 88 25 ± 7 33 _:_ 6 ± 6 _:_ 8 6.1 _ff_
Cloud 15 4 _:_ 21 ± 0 _:_ 47 20 _:_ 5 ± 2 _:_ 3 148 ± 35 24 ± 5 22 _:_ 8 ± 3 _:_ 9 12.1 _ff_
Cloud 16 3 _:_ 12 ± 0 _:_ 80 15 _:_ 2 ± 3 _:_ 9 135 ± 27 24 ± 5 25 _:_ 3 ± 5 _:_ 3 6.4 _ff_
Cloud 17 1 _:_ 30 ± 0 _:_ 52 6 _:_ 3 ± 2 _:_ 5 67 ± 14 9 ± 3 19 _:_ 2 ± 3 _:_ 2 6.1 _ff_


Note. — [a] Lensing-corrected CO(4–3) line-integrated flux. [b] Molecular gas mass derived assuming the CO(4–
3) to CO(1–0) luminosity correction factor _r_ 4 _;_ 1 = 0 _:_ 33 and the Milky Way CO-to-H 2 conversion factor of
4 _:_ 36 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1], which includes the correction factor of 1.36 for helium. [c] Beam-deconvolved and
lensing-corrected circularised radius at the full-width half-maximum. d Velocity dispersion. e Harmonic mean
magnification factor. [f] Detection significance level when integrated over the molecular cloud extent in velocity.


</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Mach number method",
  "failed_quote": "The Mach number ( ) was derived similarly to ref. [23]"
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Internal pressure formula",
  "failed_quote": "We estimated the internal kinetic pressure ( Pint / k) of the Cosmic Snake GMCs following ref. [6]"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Gaussian fit to spectrum",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "SED fitting",
  "failed_quote": "(no quote given)"
 }
]
```
