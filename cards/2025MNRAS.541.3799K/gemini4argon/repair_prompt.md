# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.541.3799K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 000–000 (0000) Preprint 8 July 2025 Compiled using MNRAS L [A] TEX style file v3.0

## **Extreme cloud collisions in nearby barred galaxies**


Tutku Kolcu [1] _[,]_ [2] _[⋆]_, Mattia C. Sormani [3], Witold Maciejewski [1], Sophia K. Stuber [4], Eva Schinnerer [4],
Francesca Fragkoudi [5], Ashley T. Barnes [6], Frank Bigiel [7], M´elanie Chevance [8] _[,]_ [9], Dario Colombo [7],
´Eric Emsellem [6] _[,]_ [10], Simon C. O. Glover [8], Jonathan D. Henshaw [4] _[,]_ [1], Ralf S. Klessen [8] _[,]_ [11] _[,]_ [12] _[,]_ [13],
Sharon E. Meidt [14], Justus Neumann [4], Francesca Pinna [15] _[,]_ [16], Miguel Querejeta [17],
Thomas G. Williams [18]

1 _School_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Nottingham,_ _University_ _Park,_ _Nottingham_ _NG7_ _2RD,_ _UK_
2 _Astrophysics_ _Research_ _Institute,_ _Liverpool_ _John_ _Moores_ _University,_ _IC2_ _Liverpool_ _Science_ _Park,_ _146_ _Brownlow_ _Hill,_ _L3_ _5RF,_ _UK_
3 _Como_ _Lake_ _centre_ _for_ _AstroPhysics_ _(CLAP),_ _DiSAT,_ _Universit`a_ _dell’Insubria,_ _via_ _Valleggio_ _11,_ _22100_ _Como,_ _Italy_
4 _Max-Planck-Institut_ _f¨ur_ _Astronomie,_ _K¨onigstuhl_ _17,_ _69117_ _Heidelberg,_ _Germany_
5 _Institute_ _for_ _Computational_ _Cosmology,_ _Department_ _of_ _Physics,_ _Durham_ _University,_ _DH1_ _3LE,_ _United_ _Kingdom_
6 _European_ _Southern_ _Observatory,_ _Karl-Schwarzschild_ _2,_ _85748_ _Garching_ _bei_ _Muenchen,_ _Germany_
7 _Argelander-Institut_ _f¨ur_ _Astronomie,_ _Universit¨at_ _Bonn,_ _Auf_ _dem_ _H¨ugel_ _71,_ _53121_ _Bonn,_ _Germany_
8 _Institut_ _f¨ur_ _Theoretische_ _Astrophysik,_ _Zentrum_ _f¨ur_ _Astronomie_ _der_ _Universit¨at_ _Heidelberg,_ _Albert-Ueberle-Strasse_ _2,_ _69120_
_Heidelberg,_ _Germany_
9 _Cosmic_ _Origins_ _Of_ _Life_ _(COOL)_ _Research_ _DAO,_ _coolresearch.io_
10 _Univ_ _Lyon,_ _Univ_ _Lyon_ _1,_ _ENS_ _de_ _Lyon,_ _CNRS,_ _Centre_ _de_ _Recherche_ _Astrophysique_ _de_ _Lyon_ _UMR5574,_ _69230_ _Saint-Genis-Laval,_ _France_
11 _Universit¨at_ _Heidelberg,_ _Interdisziplin¨ares_ _Zentrum_ _f¨ur_ _Wissenschaftliches_ _Rechnen,_ _Im_ _Neuenheimer_ _Feld_ _225,_ _69120,_
_Heidelberg,_ _Germany_
12 _Harvard-Smithsonian_ _Center_ _for_ _Astrophysics,_ _60_ _Garden_ _Street,_ _Cambridge,_ _MA_ _02138,_ _U.S.A_
13 _Elizabeth_ _S._ _and_ _Richard_ _M._ _Cashin_ _Fellow_ _at_ _Radcliffe_ _Institute_ _for_ _Advanced_ _Studies_ _at_ _Harvard_ _University,_ _10_ _Garden_ _Street,_ _Cambridge,_ _MA_
14 _Sterrenkundig_ _Observatorium,_ _Universiteit_ _Gent,_ _Krijgslaan_ _281_ _S9,_ _B-9000_ _Gent,_ _Belgium_
15 _Instituto_ _de_ _Astrof´ısica_ _de_ _Canarias,_ _C/_ _V´ıa_ _L´actea_ _s/n,_ _E-38205,_ _La_ _Laguna,_ _Spain_
16 _Departamento_ _de_ _Astrof´ısica,_ _Universidad_ _de_ _La_ _Laguna,_ _Av._ _del_ _Astrof´ısico_ _Francisco_ _S´anchez_ _s/n,_ _E-38206,_ _La_ _Laguna,_ _Spain_
17 _Observatorio_ _Astron´omico_ _Nacional_ _(IGN),_ _C/Alfonso_ _XII_ _3,_ _Madrid_ _28014,_ _Spain_
18 _Sub-department_ _of_ _Astrophysics,_ _Department_ _of_ _Physics,_ _University_ _of_ _Oxford,_ _Keble_ _Road,_ _Oxford_ _OX1_ _3RH,_ _UK_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

The inner regions of the Milky Way are known to contain an enigmatic population of prominent molecular clouds
characterised by extremely broad lines. The physical origin of these “extended velocity features” (EVFs) is still
debated, although a connection with the “dust lanes” of the Galactic bar has been hypothesised. In this paper, we
search for analogous features in the dust lanes of nearby barred galaxies using the PHANGS-ALMA CO(2-1) survey.
We aim to confirm existence of EVFs in other galaxies and to take advantage of the external perspective to gain
insight into their origin. We study a sample of 29 barred galaxies and find that 34% contain one or more EVFs,
while the remaining lack obvious signs of EVFs. Upon analysing the physical properties of the EVFs, we find they
possess large virial parameters, ranging from few hundreds to several thousand, indicating that they are strongly outof-equilibrium. The most likely explanation for their origin is extreme cloud-cloud collisions with relative velocities
in excess of 100km/s in highly non-circular flow driven by the bar. This interpretation is consistent with previous
high-resolution observations in Milky Way. Further corroboration of this interpretation comes from the inspection
of high-sensitivity infrared observations from the PHANGS-JWST Treasury Survey that reveals streams of gas that
appear to be hitting the dust lanes at locations where EVFs are found. We argue that EVFs are the clearest examples
of cloud-cloud collisions available in literature and represent a unique opportunity to study cloud collisions and their
impact on star formation.


**Key** **words:** galaxies: general - galaxies: star formation - galaxies: kinematics and dynamics - shock waves 

**1** **INTRODUCTION**



_⋆_ Contact e-mail: [Tutku.Kolcu@nottingham.ac.uk](mailto:T.Kolcu@2020.ljmu.ac.uk)


© 0000 The Authors



It has been known for several decades that the innermost
few kpc of the Milky Way (MW) contain an enigmatic pop

2 _Kolcu_ _et_ _al._


ulation of prominent molecular clouds characterised by extremely broad lines (spanning velocity ranges in excess of
100-200 km s _[−]_ [1], e.g. Bitran et al. 1997; Kumar & Riffert 1997;
Liszt 2006). These peculiar objects are found only in the
vicinity of the Galactic centre (Galactic longitudes _|l| <_ 6 _[◦]_ ),
in the region where the gravitational potential is dominated
by the Galactic bar, and can be immediately identified in
the longitude-velocity diagrams as near-vertical features (see
Fig. 1 below or Fig. 2 in Henshaw et al. 2023). Following Sormani et al. (2019) and Henshaw et al. (2023), we will refer to
these objects as Extended Velocity Features (EVFs).
A number of diverse interpretations have been put forward
for the origin of EVFs. Stark & Bania (1986), Boyce et al.
(1989), Lee et al. (1999) and Baba et al. (2010) suggested
that they are streams of clouds falling towards the Galactic
centre, although as Stark & Bania (1986) acknowledged, this
explanation requires the clouds to be near-perfectly aligned
along the line-of-sight (the so-called “fingers of God” effect).
Fukui et al. (2006) (see also Fujishita et al. 2009; Torii et al.
2010; Suzuki et al. 2015; Enokiya et al. 2021) argued that
they are the footprints of giant magnetic loops that are lifted
above the Galactic plane by magnetic buoyancy through the
Parker (1966) instability.
Several authors have proposed that the EVFs are related
to gas flow in the non-axisymmetric gravitational potential
generated by the Galactic bar, with the interpretation being
modified and refined over the years. Kumar & Riffert (1997)
suggested that the velocity extent of the EVFs is simply turbulent velocity dispersions caused by cloud-cloud collisions
in the bar potential. Fux (1999) and Liszt (2006) modified
this interpretation and suggested that EVFs are lumps of
gas that are traversing the “dust lanes” of the Milky Way
bar. According to these authors, the velocity extent is not
simply a velocity dispersion but reflects a steep velocity gradient due to the rapid differential acceleration of the cloud
as it crosses the dust lanes, which from a hydrodynamical
point of view are large-scale shocks in the gas flow and therefore locations where the velocity changes abruptly (Athanassoula 1992; Piner et al. 1995; Fragkoudi et al. 2016). Sormani
et al. (2019) further refined this interpretation by showing
that EVF-like features are naturally produced in simulations
of gas flow in barred potentials. EVFs arise when a stream
of gas travelling towards the Galactic centre along one of the
dust lanes collides with 1) a stream of gas coming from the
other dust lane on the opposite side of the Galaxy that has
‘overshot’ the central molecular zone (CMZ) gas ring; or 2) a
stream of gas orbiting in the CMZ ring, which has orbital velocities substantially lower than the material infalling along
the dust lane. Recent high-resolution zoom-in observations
of the MW’s EVFs are consistent with this picture and show
velocity bridges that can be interpreted as a direct interaction between two colliding clouds/streams with very different
bulk velocities (Busch et al. 2022; Gramze et al. 2023).
Despite these efforts, it has remained difficult to conclusively confirm or disprove the above bar-related interpretation due to our embedded perspective within the Milky Way
disc. In this paper, we therefore turn our attention to external galaxies and search for EVF analogues in nearby barred
galaxies. We aim to confirm the existence of EVFs in external galaxies and use the vantage provided by our external point of view to gain insight into their physical origin.
Since the extent of the largest EVFs in the MW is approx

MNRAS **000**, 000–000 (0000)



imately 0 _._ 7 _[◦]_ _∼_ 100 pc at the distance of the Galactic centre, this program requires observations of molecular clouds
in nearby galaxies at resolutions on the order of _∼_ 100 pc
or better. These have only recently become available thanks
to data obtained by the _Physics_ _at_ _High_ _Angular_ _resolution_
_in_ _Nearby_ _GalaxieS_ _(PHANGS)_ collaboration, in particular
the PHANGS-ALMA survey (Leroy et al. 2021b) that has
mapped [12] CO _J_ = 2 _→_ 1 line emission in 90 nearby (distance ⩽ 20 Mpc) massive star-forming galaxies at a spatial
resolution of 50-150 pc, and the PHANGS-JWST Treasury
Survey (Lee et al. 2023) that has obtained infrared imaging
of many of the same galaxies at a resolution of 5–50 pc.
The paper is structured as follows. In Sect. 2, we describe
the PHANGS–ALMA and PHANGS–JWST data. In Sect. 3,
we describe the construction of the diagnostic maps used in
our study to identify EVFs. In Sect. 4 we present our results.
We provide conclusions in Sect. 5.


**2** **OBSERVATIONAL** **DATA**


**2.1** **PHANGS-ALMA** **CO(2–1)** **Survey**


We use the [12] CO(2–1) datacubes from the PHANGS–ALMA
survey (Leroy et al. 2021b). The survey mapped the CO(2–1)
emission of 90 nearby (distance _<_ 20 Mpc) star-forming
galaxies in the southern sky. Observations of 58 galaxies
within the PHANGS-ALMA sample were taken as a part
of Cycle 5 ALMA Large Program. Observations of the remaining galaxies were taken as a part of several smaller programmes. The position-position-velocity (PPV) datacube has
a velocity resolution of 2.5 km s _[−]_ [1] and an angular resolution
of _∼_ 1 _[′′]_, which corresponds to a typical spatial resolution of
_∼_ 50–150 pc depending on the distance to the galaxy. For
more details on the PHANGS-ALMA Survey data, see Leroy
et al. (2021b) and for an in-depth discussion of the data reduction, pipeline and imaging see Leroy et al. (2021a).
The PHANGS-ALMA Survey is a “cloud-scale” spectroscopic survey in the sense that the observations have the
resolution, point-source sensitivity, and beam diameter sufficient to resolve and study individual giant molecular clouds
(GMCs). These GMCs typically have radii around 30 to 60 pc
and characteristic molecular masses on the order of 10 [5] M _⊙_
(Bolatto et al. 2008; Freeman et al. 2017; Rosolowsky et al.
2021; Schinnerer & Leroy 2024). The provided data offers sufficient spatial and velocity resolution for our study aimed at
identifying features that have typical sizes comparable to the
most prominent EVFs of the MW ( _∼_ 100 pc, see introduction).
As discussed in Stuber et al. (2023) (see their Sect. 5.1
and Appendix C), the molecular gas response to the underlying gravitational potential can lead to morphological features that differ from those observed in stellar light. This
can result in significant discrepancies between classifications
based on photometric surveys, such as the Spitzer Survey
of Stellar Structure in Galaxies (S [4] G; Buta et al. 2015),
and those based on molecular gas morphology. For example, some galaxies classified as strongly barred in the literature appear unbarred in CO(2–1), potentially indicating gasdepleted bars where further inflow has ceased, or cases where
star-forming clumps mimic elongated features in stellar light
but lack coherent gas structures in CO. Conversely, certain

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 3


**Figure** **1.** CO(1-0) emission maps of the central regions of the Milky Way. The top and bottom panels display the longitude-latitude
( _l, b_ ) and longitude-velocity ( _l, v_ los ) CO(1-0) emission maps respectively from the survey by Bitran et al. (1997). The two most prominent
EVFs of the Galaxy, located at _l_ = 5 _._ 4 _[◦]_ and _l_ = 3 _._ 2 _[◦]_, are marked with magenta boxes and are coloured in indigo and green respectively.
Red and blue are the emission from the bar dust lanes on the redshifted (DL1) and blueshifted (DL2) sides of the Galaxy. The orange
box marks the Central Molecular Zone (CMZ). The Galactic centre is located at ( _l, b_ ) = (0 _,_ 0).



galaxies (e.g., NGC 4941) show clear bar-like features in CO
that are absent or ambiguous in optical and infrared images,
suggesting that molecular gas can reveal structures that are
not easily detectable in stellar light.
Therefore, to ensure that our selected galaxies exhibit a
bar-like feature in molecular gas, in this work we use a sample of 29 galaxies from the PHANGS-ALMA dataset, listed in
Table 1, all classified as barred, based on their CO(2–1) morphology, by Stuber et al. (2023) (class B and C there). This
selection lessens the potential biases introduced by stellar
light-based classifications and ensures a consistent approach
in studying bar-driven processes in molecular gas. For each
galaxy, we use the ALMA CO(2–1) datacubes to identify
EVFs.


**2.2** **PHANGS-JWST** **Treasury** **Survey**


We complement the PHANGS-ALMA CO(2–1) observations
with data from the PHANGS-JWST Treasury Survey (Lee
et al. 2023), which provides observations from the MidInfrared Instrument (MIRI) of JWST for 19 galaxies in Cycle
1 and 55 galaxies in Cycle 2. Among these, observations of
18 out of the 29 galaxies in our sample are included within
their public data release. Further information on the Cycle 1 observations of the Treasury Survey can be found in
Lee et al. (2023), and more details on the PHANGS-JWST
data release, data reduction, and processing can be found in
Williams et al. (2024).
The mid-IR emission captured by MIRI bands provides



key insights into the interstellar medium (ISM) by acting as
a tracer of _both_ gas column densities and star forming regions
(Leroy et al. 2023). In this work, we use the 770W filter, which
is sensitive to 7.7 _µ_ m emission from polycyclic aromatic hydrocarbons (PAHs) (Smith et al. 2007; Li 2020). PAHs produce distinctive emission features when they are heated by
ultraviolet (UV) photons. Near star-forming regions, the UV
radiation field is usually dominated by radiation from young
stars, but away outside star forming regions it also includes a
contribution from the interstellar radiation field. As a result,
the 7.7 _µ_ m emission has been shown to correlate well with
both H _α_ emission (which traces star forming regions) and
CO gas (which traces molecular gas), so that this emission is
a superposition of a CO-tracing component and H _α_ -tracing
component in roughly equal proportions (Leroy et al. 2023).
Crucially for this work, the 7.7 _µ_ m emission has a strong correlation to the CO (2-1) emission away from star forming regions, allowing us to detect CO streams that go undetected
in the CO-ALMA data because they fall below the sensitivity
limit of the latter.


**3** **EVF** **IDENTIFICATION** **AND** **PROPERTY**

**ESTIMATION**


**3.1** **Diagnostic** **maps** **and** **EVF** **identification**


To search for EVFs in each of the 29 galaxies of our sample,
we construct one position position (PP) and two positionvelocity (PV) maps from its PHANGS-ALMA CO(2–1) data


MNRAS **000**, 000–000 (0000)

4 _Kolcu_ _et_ _al._


**Table** **1.** Sample of barred galaxies considered in this work. Columns are: (1) Galaxy ID; (2) Distances obtained from Anand et al. (2021)
(3) Physical resolution in native resolution cube provided in Leroy et al. (2021c); (4) inclination – “...” indicates that the uncertainties are
not provided and (5) kinematic position angle of LON from Lang et al. (2020) when available, otherwise, from Salo et al. (2015) (entries
from the latter are marked with an asterisk, _∗_ ); (6) position angle of the bar provided in the S [4] G Survey Buta et al. (2015); HerreraEndoqui et al. (2015) or Salo et al. (2015) ; (7) Bar class assigned by Stuber et al. (2023) based on CO morphology; (8) Photometric bar
classification in literature obtained from Buta et al. (2015) (NIR) if available or from de Vaucouleurs et al. (1991) (optical); (9) Presence
of EVFs identified in this work, based on PP and PV diagrams, as discussed in Sect.4 .‘Y’ indicates that EVF signatures are found in the
galaxy, while ‘N’ indicates no clear signatures of EVFs are detected.


Galaxy ID Distance Resolution _i_ PA of LON PA of bar Bar Type Bar Type EVF
(Mpc) (pc) (deg) (deg) (deg) (CO morph) (Photometric) (Y,N)
(1) (2) (3) (4) (5) (6) (7) (8) (9)


NGC 0253 3.70 150.2 75.0 _±_ ... 52 _[∗]_ 66 B SAB N

NGC 0685 19.94 163.0 23.0 _±_ 43.4 101 55 B SB N

NGC 1087 15.85 123.1 42.9 _±_ 3.9 179 128 B SB N

NGC 1097 13.58 111.7 48.6 _±_ 6.0 122 141 C SB **Y**

NGC 1300 18.99 113.1 31.8 _±_ 6.0 98 99 C SB **Y**

NGC 1317 19.11 147.1 23.2 _±_ 7.7 42 150 B SB N

NGC 1365 19.57 130.8 55.4 _±_ 6.0 21 86 C SB N

NGC 1433 18.63 99.1 28.6 _±_ 6.0 20 95 C SB N

NGC 1512 18.83 94.5 42.5 _±_ 6.0 82 42 C SB **Y**

NGC 1566 17.69 107.6 29.6 _±_ 10.7 35 177 C SAB N

NGC 1637 11.7 78.9 31.0 _±_ ... 21 _[∗]_ 85 B SAB N

NGC 1672 19.4 181.7 42.6 _±_ 6.0 134 96 C SAB N

NGC 2566 23.44 145.3 48.5 _±_ 6.0 132 66 C SB **Y**

NGC 2903 10.0 70.5 66.8 _±_ 3.1 24 28 C SB **Y**

NGC 3059 20.23 119.9 29.4 _±_ 11.0 165 40 B SB N

NGC 3351 9.96 70.7 45.1 _±_ 6.0 13 112 C SB N

NGC 3507 23.55 155.2 21.7 _±_ 11.3 56 112 C SAB N

NGC 3627 11.32 89.2 57.3 _±_ 1.0 173 160 C SB **Y**

NGC 4303 16.99 149.3 23.5 _±_ 9.2 132 178 C SAB **Y**

NGC 4321 15.21 122.9 38.5 _±_ 2.4 156 115 C SAB N

NGC 4535 15.77 119.1 44.7 _±_ 10.8 180 42 C SAB **Y**

NGC 4548 16.22 132.7 38.3 _±_ 6.0 138 61 C SB **Y**

NGC 4579 21.00 182.7 40.2 _±_ 5.6 91 53 C SB N

NGC 4654 21.98 182.8 55.6 _±_ 5.9 123 121 B SB N

NGC 4941 15.00 115.3 53.4 _±_ 1.1 22 16 C SA N

NGC 5236 4.89 50.7 24.0 _±_ ... 45 _[∗]_ 50 C SAB N

NGC 5643 12.68 79.9 29.9 _±_ 6.0 139 84 C SAB **Y**

NGC 6300 11.58 60.4 49.6 _±_ 5.9 105 71 C SB N

NGC 7496 18.72 152.0 35.9 _±_ 0.9 14 147 C SB N



cube by integrating the cube over velocities and over two spatial dimensions, respectively. Before the integration, the cube
is rotated so that the positive half of the line of nodes is along
the negative x-axis. In this work, PAs of the LONs for majority of our sample galaxies are taken from Lang et al. (2020)
when available, otherwise taken from Salo et al. (2015) (see
Table 1). Then we convert angular (arcseconds) into physical
(kpc) scales assuming the distances from Anand et al. (2021),
so that _x_ and _y_ cos( _i_ ) are the spatial coordinates in kpc in
the sky plane (corresponding to _x_ and _y_ coordinates in the
disc plane).


To identify EVFs, in analogy with the MW’s EVFs we
look for features on the dust lanes that have an unusually
large velocity spread but are relatively compact in size. Thus
we first visually identify the dust lanes in the CO(2–1) PP
maps. These typically appear unambiguously as two nearly
straight or curved features, located on either side of the bar,
extending from the nucleus to the bar ends (see Sect. 3.2.2 of
Stuber et al. 2023 for further details). To better visualise
each dust lane we draw a contour enclosing it in the PP
map, and we colour in red or blue all data in the data cube


MNRAS **000**, 000–000 (0000)



with spatial coordinates falling within this contour. For this
purpose we use the visualisation software `glue` [1] (Beaumont
et al. 2015; Robitaille et al. 2017). While this procedure is
somewhat subjective, the results are reasonable, as the dust
lanes are typically coherent and continuous structures in PP
space. The top and middle panels of Fig. 2 show the results
of this procedure for NGC 1300. In the following, we will refer
to these diagrams as “diagnostic maps”.
We then visually select the EVFs within the extracted dust
lanes by looking in the PV maps for features that are abnormally broad-lined compared to the rest of the material on
the dust lane, and that have physical sizes in the PP maps
smaller or comparable to the width of the dust lane. Each
selected EVF is outlined by rectangular boxes in PP and PV
maps in Fig. 2 and Figs. A1a–A9a, and if more than one EVF
is present in a galaxy, the EVFs are named F1, F2, etc., with
the names plotted in the figures and listed in Table 2.
The EVFs identified in this way typically look like “blobs”
with an approximately circular shape in PP space, likely due


1 The `glue` webpage can be accessed via `[https://glueviz.org](https://glueviz.org)`

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 5



to the resolution limitations. In several galaxies, as discussed
in Sect. 4, these blobs are resolved into smaller clumps in
7.7 _µ_ m emission (see Fig. 3 for NGC 1300). These clumps
might host incipient star formation activity, potentially triggered by molecular cloud collisions.
Only the PHANGS-ALMA CO(2-1) data is used to identify EVFs. The mid-infrared PHANGS-JWST observations
are not utilized for EVF identification, but they are used to
further inspect the vicinity of a CO-identified EVF and trace
gas that falls below the sensitivity threshold of the CO data.
As we shall see, this often reveals streams of gas connecting to the EVF that are invisible in the CO data. We focus
only on the 7.7 _µ_ m wavelength from MIRI/JWST as these are
available for all galaxies in our sample that exhibit EVFs and
have been shown to trace well the gas column density (Leroy
et al. 2023). The bottom panel of Fig. 2 shows an example
JWST mid-infrared map for NGC 1300.
The diagnostic maps and 7.7 _µ_ m images of the remaining
galaxies in our sample are presented in Appendix A.


**3.2** **EVF** **properties** **estimation**


To estimate the physical size of the EVFs, we first visually
define a circular region on the dust lane, in PP space, that
encompasses the entire EVF. We make the radius of the circle big enough to contain the whole EVF and small enough
that it excludes (as much as possible) other nearby unrelated
features. We also ensure that the circular region remains entirely within the dust lane. This region is then extracted and
isolated for further analysis.
We estimate the EVF radius as follows. We centre the ex
tracted region on the brightest point as an initial guess for the
EVF centre. We then fit a 2D Gaussian function to the PP
map. We thus obtain values for the centre coordinates and
standard deviations _σ_ _x_ and _σ_ _y_ . We then calculate the EVF
radius using the following formula (see Eq. 9 of Rosolowsky
et al. 2021):


_R_ EVF = _η_ ~~_[√]_~~ _σ_ _x_ _σ_ _y_ _,_ (1)


where the factor _η_ = ~~_√_~~ 2 ln 2 = 1 _._ 18 comes by modelling the

surface brightness as a two-dimensional Gaussian and using
the half width at half maximum as the radius (Rosolowsky
et al. 2021). We note that this procedure will overestimate the
radius of unresolved EVFs, so the radii should be considered
upper limits.
Further, to obtain the galactocentric distance ( _R_ cen ) of the
EVFs, we use the coordinates of the EVF centre ( _x_ and _y_ ),
determined from the 2D Gaussian fit described above, in the
formula


_R_ cen = ~~�~~ ( _x −_ _x_ _o_ ) [2] + ( _y −_ _y_ _o_ ) [2] _,_ (2)


where ( _x_ _o_, _y_ _o_ ) are the coordinates of the galaxy centre. The
measurement uncertainty of the EVF centre and the uncertainty in inclination is propagated to the uncertainty in _R_ cen .
To estimate the velocity extent of the EVFs, we construct
the total spectrum — intensity versus velocity — in the region enclosed by _R_ EVF . We then fit a single Gaussian to the
total spectrum. The standard deviation _σ_ _v_ of the fit is taken
as a measure of the velocity dispersion, and the full width
at half maximum (FWHM) of the fit as a measure of the
velocity extent, ∆ _v_ = (2 ~~_√_~~ 2 ln 2) _σ_ _v_ .

Example spectra for the two EVFs identified in NGC 1300



and Gaussian fits are shown in Fig. 4. The uncertainties in
all fitted parameters, including the centre coordinates, _σ_ _x_, _σ_ _y_
and ∆ _v_, were estimated from the square roots of the diagonal elements of the covariance matrix obtained during the respective fitting processes. These uncertainties reflect the confidence intervals in the fitting only and they do not take into
account that the shape of the intensity distribution within
EVF region might be non-Gaussian, that there might be contaminating emission from other features overlapping with the
EVF in PP space, or that the radius can be overestimated
when the EVF is unresolved.

To estimate the EVF masses, we calculate the total integrated CO intensity, _I_ CO, within the determined _R_ EVF . We
then convert this total intensity into mass using the relation:


_M_ CO = _α_ CO _I_ CO _,_ (3)


where _α_ CO = 6 _._ 69 M _⊙_ pc _[−]_ [2] (K km s _[−]_ [1] ) _[−]_ [1] is the CO(2-1)-toH 2 conversion factor, and is derived from the Galactic value of
4.35 M _⊙_ pc _[−]_ [2] (K kms _[−]_ [1] ) _[−]_ [1] estimated by Bolatto et al. (2013),
with the factor 0.70 accounting for the conversion between
12 CO _J_ = 2 _−_ 1 and _J_ = 1 _−_ 0 transitions (Leroy et al.
2022). We adopt this procedure for simplicity, but note that
it ignores galaxy-scale variations (e.g. den Brok et al. 2025)
and might overestimate the mass for high-velocity dispersion
features such as the EVF since high velocity dispersion often
causes lower _α_ CO values near galactic centres (Teng et al.
2023).
Following Bertoldi & McKee (1992) and Rosolowsky et al.
(2021), we calculate the virial masses and virial parameters

as:


_v_ _[R]_ EVF
_M_ vir = [5] _[σ]_ [2] _,_ (4)

_G_

_α_ vir = [2] _[M]_ [vir] (5)

_M_ CO _[.]_


The virial mass represents an estimate of the mass of the EVF
under the assumption of dynamical equilibrium. The virial
parameter _α_ vir compares the virial mass to the CO-measured
mass, and is a measure of the ratio between the kinetic and
gravitational binding energy of the cloud. In dynamical equilibrium, the virial parameter is expected to be of order unity,
while a large virial parameter indicates an out-of-equilibrium
unbound situation (kinetic energy _≫_ gravitational energy).
All estimated properties of the EVF regions are provided
in Table 2.


**3.3** **Milky** **Way** **spectra**


As we view the Milky Way almost edge-on, we cannot separate the bar lanes in the PP maps as we did in Sect. 3.1 for
external galaxies. Therefore in the MW, we identify both the
EVF regions and the bar lanes in the PV diagram using the
data from Bitran et al. (1997). As in Sect. 3.1, for visualising
the dust lanes and EVF regions we use the `glue` software.
The dust lanes and EVF regions are then overplotted in different colours on top of the main emission in greyscale in
the PP and PV maps in Fig. 1, where we highlight the EVF
regions within magenta rectangular boxes. Figure 5 presents
the CO(1–0) spectra of the two EVF regions. The left panel
presents the total spectrum within the extracted EVF region
at _l_ = 3 _._ 2 _[◦]_, corresponding to emission at a longitude range


MNRAS **000**, 000–000 (0000)

6 _Kolcu_ _et_ _al._


**Figure** **2.** The diagnostic maps and 7.7 _µ_ m emission image of NGC 1300. _Top:_ Position-position (PP) and Position-velocity (PV) diagrams.
The galaxy is rotated in the plane of the sky such that the PA of the LON aligns with the _x_ -axis. Red and blue colours highlight the
dust lanes. _Bottom:_ 7.7 _µ_ m emission in gray-scale, with CO(2–1) intensity as in PP diagram in yellow contours. Magenta lines mark the
streams that appear to extend over large radii and reach to the regions where EVFs are seen. In all panels, the rectangular boxes mark
the regions of EVFs.


MNRAS **000**, 000–000 (0000)

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 7


**Figure** **3.** Close-up views of the EVF regions, marked with rectangular boxes in the bottom panel of Fig. 2. Both panels show the 7.7 _µ_ m
emission in gray-scale overlaid with CO(2–1) emission in yellow contours.





























Velocity [km/s]



Velocity [km/s]



**Figure** **4.** The CO(2–1) spectra within the regions enclosed within rectangular boxes in Fig. 2 where EVFs are seen, for F1 on left and
for F2 on right. Gray solid lines shows the total intensity, the purple dashed lines are the Gaussian fit to the spectrum and blue dashed
lines mark the FWHM of the fits.



2.7–3.4 _[◦]_, latitude not restricted. The right panel presents the
total spectrum within the extracted EVF region at _l_ = 5 _._ 4 _[◦]_,
corresponding to the emission at a longitude range of 5.0–
5.6 _[◦]_, latitude unresricted. Due to our embedded perspective
within the MW disk, the EVFs are “contaminated” by overlapping features along the line-of-sight, resulting in spectra
that appear more complex than those of external galaxies.


The spectrum on the left panel (EVF at _l_ = 3 _._ 2 _[◦]_ ) shows
contamination from a feature that is known to be a secondary
dust lane (Liszt 2008), which appears as a narrow peak superimposed on the broader EVF peak. Since the single Gaussian fitting technique used for external galaxies is inadequate
for cases with overlapping features, we simply adopt a double Gaussian fitting approach to accurately model multiple
components and account for foreground contamination. This
yields a FWHM 70 _._ 64 _±_ 2 _._ 07 km s _[−]_ [1] for the EVF component
and a 13 _._ 92 _±_ 2 _._ 14 km s _[−]_ [1] for the component of the overlap


We note that the method for estimating ∆ _v_ for the MW
and external galaxies is slightly different as we used a double
Gaussian to get rid of contaminating features in the first case.
This difference in methodology should be borne in mind when
comparing ∆ _v_, but it does not affect any of our conclusions
below as they are not very sensitive to the exact values of
∆ _v_ .


MNRAS **000**, 000–000 (0000)



ping dust lane. We take the first as our estimate of the EVF
velocity extension ∆ _v_ .


The spectrum on the right panel (EVF at _l_ = 5 _._ 4 _[◦]_ ) shows
two broad peaks, and it is not obvious what constitutes foreground contamination and what is genuine EVF emission. To
produce nevertheless an estimate of ∆ _v_, we again fit a double Gaussian and consider the broadest peak to be the EVF,
resulting in ∆ _v_ = 68 _._ 40 _±_ 4 _._ 19 km s _[−]_ [1] .

8 _Kolcu_ _et_ _al._


**Table** **2.** Properties of the EVFs identified in this paper. Columns are: Galaxy ID, label of each EVF identified in each galaxy, galactrocentric distance from the EVF centre, radius of the EVF, velocity dispersion of the Gaussian fit to the EVF, velocity spread of the EVF
(FWHM of the Gaussian fit), total CO(2–1) mass within each EVF region, the virial alpha parameter for each EVF and index for each
feature which is used in figures to distinguish between EVFs.


Galaxy ID Feature _R_ cen _R_ EVF _σ_ _v_ ∆ _v_ M CO(2 _−_ 1) _α_ vir Index
(kpc) (kpc) ( km s _[−]_ [1] ) ( km s _[−]_ [1] ) ( _×_ 10 [5] M _⊙_ )


NGC1097 F1 3.53 _±_ 0.42 0.12 30.86 _±_ 0.39 72.68 _±_ 0.91 2.13 _±_ 0.61 1207 1

NGC1300 F1 3.56 _±_ 0.23 0.10 13.33 _±_ 1.08 31.40 _±_ 2.55 0.39 _±_ 0.13 1043 2

F2 4.77 _±_ 0.31 0.12 18.56 _±_ 0.29 43.70 _±_ 0.68 2.71 _±_ 0.64 368 3

NGC1512 F1 3.00 _±_ 0.29 0.11 30.63 _±_ 1.05 72.13 _±_ 2.47 1.71 _±_ 0.44 1464 4

NGC2566 F1 3.09 _±_ 0.37 0.15 25.89 _±_ 0.60 60.97 _±_ 1.41 4.21 _±_ 1.27 550 5

F2 3.56 _±_ 0.42 0.14 28.82 _±_ 0.70 67.87 _±_ 1.66 4.72 _±_ 1.33 565 6

NGC2903 F1 2.92 _±_ 0.37 0.09 30.24 _±_ 0.46 71.20 _±_ 1.08 1.88 _±_ 0.96 969 7

F2 3.45 _±_ 0.44 0.07 18.81 _±_ 0.21 44.31 _±_ 0.50 1.21 _±_ 0.68 509 8

NGC3627 F1 1.08 _±_ 0.03 0.09 25.21 _±_ 0.27 59.37 _±_ 0.64 1.68 _±_ 0.51 778 9

F2 2.79 _±_ 0.08 0.08 18.98 _±_ 0.19 44.71 _±_ 0.46 1.31 _±_ 0.45 524 10

F3 3.60 _±_ 0.10 0.09 18.88 _±_ 0.36 44.47 _±_ 0.84 1.55 _±_ 0.55 492 11

F4 1.37 _±_ 0.04 0.11 29.18 _±_ 0.42 68.72 _±_ 0.99 9.67 _±_ 2.61 223 12

NGC4303 F1 2.50 _±_ 0.17 0.14 11.50 _±_ 0.05 27.08 _±_ 0.13 5.55 _±_ 1.52 76 13

F2 0.84 _±_ 0.06 0.13 17.91 _±_ 0.21 42.18 _±_ 0.50 7.11 _±_ 1.59 140 14

NGC4535 F1 1.17 _±_ 0.22 0.15 21.17 _±_ 0.63 49.85 _±_ 1.49 1.76 _±_ 0.68 903 15

NGC4548 F1 0.67 _±_ 0.06 0.14 21.05 _±_ 1.18 49.56 _±_ 2.78 0.50 _±_ 0.13 2925 16

F2 3.02 _±_ 0.25 0.14 15.73 _±_ 0.45 37.05 _±_ 1.05 0.86 _±_ 0.24 932 17

NGC5643 F1 0.73 _±_ 0.04 0.11 22.66 _±_ 0.25 53.36 _±_ 0.60 8.77 _±_ 1.79 146 18





175


150


125


100


75


50


25


0



40 60 80 100 120 140 160 180
LSR Velocity [km/s]







70


60


50


40


30


20


10


0



40 60 80 100 120 140 160
LSR Velocity [km/s]



**Figure** **5.** The spectra (black full curves) and double Gaussian fits (dashed curves) for two MW EVFs highlighted in Fig. 1 and located
at _l_ = 3 _._ 2 _[◦]_ (left) and _l_ = 5 _._ 4 _[◦]_ (right). The two components of the double Gaussian fits are in blue and green, and their sum is in purple.



**4** **RESULTS**


After examining the PP and PV diagrams of the 29 galaxies
in our sample, we identified EVFs in 10 out of 29 galaxies,
which represents approximately 34% of the total. The remaining 19 galaxies (about 66%) did not show obvious features
that we could identify as EVFs, although it is not excluded
(and is actually likely) that higher resolution/sensitivity surveys might reveal more features. The 10 galaxies exhibiting
signatures of EVFs are: NGC 1097, NGC 1300, NGC 1512,
NGC 2566, NGC 2903, NGC 3627, NGC 4303, and NGC 4535,
NGC 4548 and NGC 5643. Amongst these 10, 4 galaxy exhibited one EVF each, while the remaining 6 galaxies exhibited
more than one EVF. In total, we identified 18 EVFs within 10
galaxies. To interpret the nature of these features, we study
their spectra, locations and physical properties as discussed
below.


Let us use NGC 1300, shown in Figs. 2, as an illustra

MNRAS **000**, 000–000 (0000)



tive example. In this galaxy, we identified two EVFs: one
on the dust lane coloured in red at a radius of approximately
3.6 kpc from the galactic centre, and one on the dust lane
coloured in blue at a radius of approximately 4.8 kpc. These
are marked with rectangular boxes in Fig. 2. The EVFs show
enhanced CO(2–1) intensity in the PP diagrams, confined to
rather round, blob-like regions. The most prominent of the
two EVFs is the feature on the dust lane coloured in blue.

Similar to EVFs observed in the MW, this feature has a large
vertical and narrow horizontal extent in the PV diagram.


In the vicinity of approximately 12 of the EVF regions,
while CO(2–1) emission appears as round blob-like features,
the emission in 7.7 _µ_ m is resolved into smaller clumps. An
example of this can be seen in Fig. 3 for NGC 1300, see also
Figs. A1b, A3b(F2), A4b, A5b, A6b(F1) for several other
galaxies. These clumps might contain enhanced star formation activity in smaller collapsed regions, possibly triggered
by molecular cloud collisions near the EVFs. In fact, a re

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 9



**Table** **3.** Sample of galaxies classified consistently as ‘unbarred’
from both CO morphology (Stuber et al. 2023) and photometry
(de Vaucouleurs et al. 1991; Buta et al. 2015) used in this work to
search for EVFs as test cases. Columns are: Galaxy ID; Distances
obtained from Anand et al. (2021); Physical resolution in native
resolution cube Leroy et al. (2021c); kinematic position angle of
LON and inclination inferred from Lang et al. (2020); Presence
of EVFs identified in this work, based on PP and PV diagrams,
as discussed in Sect.4.‘Y’ indicates that EVF signatures are found
in the galaxy, while ‘N’ indicates no clear signatures of EVFs are
detected.


Galaxy ID Distance Resolution PA of LON _i_ EVF
(Mpc) (pc) (deg) (deg) (Y,N)


NGC 0628 9.84 53.5 21 9 Y

NGC 1546 17.69 109.6 148 70 N

NGC 1792 16.20 150.9 134 65 N

NGC 1809 19.95 136.0 139 58 N

NGC 2090 11.75 73.8 13 65 N

NGC 3137 16.37 120.0 180 70 N

NGC 3521 13.24 85.5 163 69 N

NGC 3596 11.30 66.9 78 25 N

NGC 3621 7.06 62.4 164 66 N

NGC 4254 13.10 113.1 68 34 N

NGC 4298 14.92 114.7 134 59 N

NGC 4689 15.00 86.0 164 39 N

NGC 4826 4.41 26.9 114 59 N


cent study of NGC 3627 by (Maeda et al. 2025) shows that,
despite being less efficient at high collisional velocities, cloud
collisions can still enhance the star formation in bar lanes.

For the remaining 6 EVF regions, we do not see strong intensity enhancement or clumpiness in 7.7 _µ_ m emission; see
Figs. A2b and A8b as examples.
To check whether unbarred galaxies can also contain EVFs,
we examined all galaxies that are classified as lacking bar-like
features in the molecular gas morphology (Class A) in Stuber
et al. (2023) which are also classified as unbarred (‘SA’) in
photometric studies (de Vaucouleurs et al. 1991; Buta et al.
2015). These 13 galaxies are presented in Table 3. Of these,
only one galaxy –NGC 628– exhibited a tentative EVF-like
signature in the PV diagram, along one of its spiral arms.
The CO velocity and velocity dispersion maps of NGC 628
appear relatively undisturbed, but several faint gas streams
are visible, seemingly connecting to the region where the EVF
occurs. These findings suggest that a cloud collision might
be happening in the spiral arm of this galaxy, leading to the
emergence of EVF signatures in their PV diagrams. However,
the general absence of EVF signatures in unbarred galaxies supports the argument that EVFs arise primarily due to
cloud-cloud or stream-stream collisions in bar lanes.


**4.1** **Physical** **properties** **of** **EVFs**


Table 2 lists the properties of all of the EVFs identified in
our sample. Typical masses are in the range 10 [5] -10 [6] _M_ _⊙_,
while typical sizes are of the order of 100 pc. These values are similar to the MW EVFs shown in Fig. 1, which
have radii of _∼_ 100 pc and estimated masses ranging from a
few 10 [4] _M_ _⊙_ to a few 10 [6] _M_ _⊙_ depending on the method used
(Liszt 2006; Gramze et al. 2023). Figure 6 shows the EVFs’
properties against their galactocentric radius (left panels) and
their physical radius (right panels), illustrating that they are
found at different distances from the galactic centre, span


ning the full extent of the bar lanes. All these characteristics
are consistent with the EVFs identified in our sample being
analogues of the MW features.
For all of the EVFs we identified, the virial parameter, _α_ vir,
is exceptionally large, ranging from a few hundred to several
thousand (see Table 2). Bound molecular clouds should have
_α_ vir ⩽ 2, while unbound systems have _α_ vir _>_ 2 (e.g. Bertoldi
& McKee 1992). This indicates that EVFs are all unbound
systems that are very far from virial equilibrium, consistent
with the idea that they are the sites of extreme cloud-cloud
(or stream-stream) collisions. We caveat that if the EVFs
are unresolved in the PHANGS-ALMA CO data (which is
possible given their ‘blobby’ appearance), then we will overestimate their virial parameter since _R_ EVF will be larger than
the true cloud size. If instead, we overestimate _M_ CO due to
the simple _α_ CO prescription adopted (Sect. 3.2), then we will
underestimate the virial parameter. However, these effects are
unlikely to affect our conclusions, because even in the worst
case we would not expect the virial parameters to change
by more than a factor of a few, so the EVFs would still be
strongly super-viral.
The formulae for both the virial mass and the virial parameter, given in Sect. 3.2, which result in the values given
above, assume an isotropic velocity distribution. On the other
hand, if the EVFs are sites of collisions of clouds moving with
markedly different velocities, their velocity extent may be dictated by the velocity difference between the colliding clouds.
In particular, it may not be isotropic, as the colliding clouds
move in the galaxy plane. If the velocity dispersion is not
isotropic, but mainly in the disc plane, one should observe a
trend of the EVF velocity difference being larger in galaxies
that are more highly inclined.
In the left panel of Fig. 7, we show the velocity extent, ∆ _v_
against sin( _i_ ) for our EVFs. We include the MW results for
comparison, although we remind the reader that the method
for obtaining the ∆ _v_ is slightly different (see Sect. 3.3) than
how we inferred the parameter in external galaxies. For external galaxies, ∆ _v_, ranges from approximately 27 km s _[−]_ [1] to
72 km s _[−]_ [1] . Both of the MW EVFs with _∼_ 70 km s _[−]_ [1] are on

the higher end of this range. The figure shows a rough correlation between ∆ _v_ and sin( _i_ ), consistent with expectations
for the EVF velocity extent resulting from velocity difference
of the colliding clouds. Particularly, it suggests that the ∆ _v_
is likely not driven by isotropic velocity dispersion. Although
the scatter in this figure is large, this is not surprising since
in different galaxies, and in different EVFs clouds can collide
with different relative velocities.
If the velocity extent of EVFs is dictated entirely by the
velocity difference of colliding clouds, then one should expect
the largest velocity extent for bars roughly perpendicular to
the line of nodes. This is because, to the first approximation, the radial velocity in the bar lane gets reverted (outflow
upstream from the bar lane turns into inflow downstream
from it), while the azimuthal velocity continues as prograde
rotation, and the radial velocity dominates the observed lineof-sight velocity in the direction perpendicular to the line of
nodes. In the right panel of Fig. 7, we show the ∆ _v/_ sin( _i_ ) as
a function of PA LON _−_ PA bar . There is no clear minimum at
PA LON = PA bar . This may indicate that turbulent random
motions resulting from the collision significantly contribute
to the velocity extent of EVFs, which therefore is not solely
caused by the velocity difference of the colliding clouds.


MNRAS **000**, 000–000 (0000)

10 _Kolcu_ _et_ _al._


70



















60


50

































40


30















1000 2000 3000 4000 5000



60 80 100 120 140 160



12


10







8


6















4


2































0

1000 2000 3000 4000 5000



60 80 100 120 140 160





10 [4]


10 [3]




































|4|Col2|
|---|---|
|~~7~~<br>~~1~~|~~7~~<br>~~1~~|
||~~5~~<br><br>~~8~~<br><br>|

















10 [2]







1000 2000 3000 4000 5000
R cen [pc]



60 80 100 120 140 160
R EVF [pc]



**Figure** **6.** Physical properties of EVFs plotted against the radius from the galaxy center (left) and the physical radius of the EVF (right).
From top to bottom: velocity extent ∆ _v_, mass _M_ CO, virial parameter _α_ vir . Each point is numbered according to the assigned EVF index
listed in Table 2.



**4.2** **JWST** **gas** **streams**


PHANGS-JWST observations have no velocity information,
but are much more sensitive to low surface density gas and
have higher spatial resolution than the PHANGS-ALMA CO
data. We use them to trace the gas that falls below the sensitivity threshold of the CO data. The 7.7 _µ_ m band observations of NGC 1300, presented in the bottom panel of Fig 2,
reveals many streams of gas in the bar region surrounding the
dust lanes that indeed are invisible in the CO data. Several

streams connecting to the EVFs are marked by faint magenta arrows. These streams appear to extend continuously



from the opposite side of the galaxy for several kpc, either
in straight or slightly curving forms, and reach the location
of the EVF, where enhanced CO(2–1) intensity is seen. In
the cloud-cloud collision interpretation (see Sect. 1), EVFs
originate from collisions of gas streams along the bar lanes
with gas streams coming from the opposite side of the galaxy.
We hypothesise that these are the streams that collide with
the dust lane streams, with almost opposite velocity vectors,
giving rise to the EVFs. The direction of the streams shown
by the magenta arrows is an educated guess based on the



MNRAS **000**, 000–000 (0000)

80


70


60


50


40


30


20













_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 11


140


120



















_−_ 50 0 50 100 150
PA lon _−_ PA bar [deg]











































0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8 1 _._ 0
sin( _i_ )



100


80


60


40



**Figure** **7.** The distribution of ∆ _v_ against sin( _i_ ) (left) and the distribution of ∆ _v_ /sin( _i_ ) against the difference of PA of the LON and
PA of the bar (right). The points are numbered according to galaxy and EVF index, as listed in Table 2. Triangle markers in left panel
represent the measurements from the EVF of MW.



observed morphology and theoretical knowledge of gas flow
in barred potentials.


Upon examining the 7.7 _µ_ m band observations of all galaxies with EVFs, we find that out of 18 EVF regions, 9 are
associated with faint streams extending from the opposite
end of the bar toward the EVF location. In some galaxies,
such as NGC 1300, multiple faint streams reach the EVF regions. The galaxies displaying these streams of overshot gas
are NGC 1300, NGC 1097, NGC 2566 (only F1), NGC 3627
(except F1), NGC 4548 (F2), and NGC 5643. For 5 EVFs

_∼_
( 28%) we cannot determine whether streams are associated
due to star-forming activity within the bar regions. These
cases are found in NGC 2566 (F2), NGC 2903, NGC 3627
(F1), and NGC 4303 (F1). For the remaining 4 ( _∼_ 22%)
EVFs— in NGC 1512 (F1), NGC 4303 (F2), NGC 4535 (F1),
and in NGC 4548 (F1)—we did not identify any associated
streams of overshot gas.


Several factors may contribute to the absence of observable streams in other galaxies exhibiting EVFs. One possibility is an intrinsically low gas density, where the emission
is too weak to be detected in 7.7 _µ_ m observations. Additionally, environmental effects such as global rotational flow and
turbulence within the intergalactic medium could introduce
kinematic disturbances, leading to gas dissipation through
mixing, making the streams too faint to be traced. Stacking
observations across different MIRI filters could help produce
deeper images and reveal fainter structures. However, since
such data were not consistently available for all galaxies, we
did not pursue this approach in our analysis. It is also possible that that the stream was a short segment which is lost
to the collision.


In the collision interpretation, the geometry of the collision might lead us to expect that the EVFs should occur
on the trailing side of the bar lanes. Although it is difficult to assess this conclusively as dust lanes are thin and the
spatial resolution is not sufficient to examine this in detail,
some galaxies appear consistent with this expectation (e.g.
NGC 1512, NGC 2903, NGC 3627), but for some other galax


ies the EVFs seem to occur on the leading side of the bar
lanes (e.g. NGC 1097 and NGC 4535). There might be various explanations for this phenomenon within our cloud-cloud
collision hypotheses. For example, the gas could traverse the
dust lane while the collision is still taking place, as the simulations show that it is a collision between streams, which happens over an extended period in time (Sormani et al. 2019).
Another reason might be the gas clumpiness, so the incoming streams might find holes in the gas distribution and only
collide with other gas parcels when it has traversed the relatively short thickness of the dust lane (in other words, the
mean free path might be comparable to the lane thickness).


**5** **SUMMARY** **&** **CONCLUSIONS**



The inner regions of the MW are known to harbour an
enigmatic population of prominent molecular clouds characterised by extremely broad lines. The physical origin of these
“extended velocity features” (EVF) has remained controversial, but a connection with the dust lanes of the Galactic bar
has been suggested by several authors.
In this study, we searched for analogous features in the bar
dust lanes of 29 nearby barred galaxies using the PHANGSALMA CO(2–1) survey, with the aim of confirming the existence of EVF-like features in other galaxies and of using
the external perspective to gain insight into their origin. We
found EVFs in 10 out of the 29 galaxies, corresponding to
34% of our sample. The EVF features stand out as relatively compact structures that have an unusually large velocity spread in the PPV diagrams compared to the rest of
the material on the dust lane. Upon examining a test sample
of 13 unbarred galaxies, we find a general absence of EVFs
in their PPV diagrams.
We analysed the physical properties of the EVFs and
found that they all have virial parameters ranging from
few 100s to several 1000s, indicating highly unbound structures. The most likely explanation for their origin is extreme cloud-cloud, or more appropriately stream-stream, col

MNRAS **000**, 000–000 (0000)

12 _Kolcu_ _et_ _al._


lisions with relative velocities in excess of 100 km s _[−]_ [1] . Fur
ther support to this interpretation is provided by PHANGSJWST MIRI 7.7 _µm_ observations, revealing low-intensity,
CO-invisible streams of gas in 50% of the EVF cases, that
appear, based on their morphology, to be hitting the dust
lanes at the location where EVFs are found.

Our findings support the idea that EVFs are the result
of extreme collisions between gas streams occurring in the
dust lanes of barred galaxies. They are probably the clearest
examples of cloud-cloud collisions available in the literature.
Thus, they are unique astrophysical laboratories to study the
physics and chemistry of complex cloud collisions and their
impact on star formation in galaxies.


**ACKNOWLEDGEMENTS**


TK acknowledges the joint studentship support from Liverpool John Moores University the Faculty of Engineering and
Technology, and the Science Technology Facilities Council.
TK also acknowledges the financial support from The Leverhulme Trust. MCS acknowledges financial support from the
European Research Council under the ERC Starting Grant
“GalFlow” (grant 101116226) and from Fondazione Cariplo
under the grant ERC attrattivit`a n. 2023-3014. FF is supported by a UKRI Future Leaders Fellowship (grant no.
MR/X033740/1). MC gratefully acknowledges funding from
the DFG through an Emmy Noether Research Group (grant
number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. SCOG
and RSK acknowledge financial support from the European
Research Council via the ERC Synergy Grant “ECOGAL”
(project ID 855130) and from the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”, funded by
the German Excellence Strategy. RSK also acknowledges support from the German Ministry for Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206).
RSK is grateful for computing resources provided by the Ministry of Science, Research and the Arts (MWK) of the State
of Baden-W¨urttemberg through bwHPC and the German
Science Foundation (DFG) through grants INST 35/11341 FUGG and 35/1597-1 FUGG, and also for data storage at
SDS@hd funded through grants INST 35/1314-1 FUGG and
INST 35/1503-1 FUGG. RSK also thanks the 2024/25 Class
of Radcliffe Fellows for their company and for highly stimulating discussions. FP acknowledges support from the Horizon
Europe research and innovation programme under the Marie
Sk�lodowska-Curie grant “TraNSLate” No 101108180, and
from the Agencia Estatal de Investigaci´on del Ministerio de
Ciencia e Innovaci´on (MCIN/AEI/10.13039/501100011033)
under grant (PID2021-128131NB-I00) and the European Regional Development Fund (ERDF) “A way of making Europe”.
MQ acknowledges support from the Spanish grant PID2022-138560NB-I00, funded by
MCIN/AEI/10.13039/501100011033/FEDER, EU.


This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2012.1.00650.S,
ADS/JAO.ALMA#2013.1.00803.S,
ADS/JAO.ALMA#2013.1.01161.S,


MNRAS **000**, 000–000 (0000)



ADS/JAO.ALMA#2015.1.00121.S,
ADS/JAO.ALMA#2015.1.00782.S,
ADS/JAO.ALMA#2015.1.00925.S,
ADS/JAO.ALMA#2015.1.00956.S,
ADS/JAO.ALMA#2016.1.00386.S,
ADS/JAO.ALMA#2017.1.00392.S,
ADS/JAO.ALMA#2017.1.00766.S,
ADS/JAO.ALMA#2017.1.00886.L,
ADS/JAO.ALMA#2018.1.00484.S,
ADS/JAO.ALMA#2018.1.01321.S,
ADS/JAO.ALMA#2018.1.01651.S,
ADS/JAO.ALMA#2018.A.00062.S,
ADS/JAO.ALMA#2019.1.01235.S,
ADS/JAO.ALMA#2019.2.00129.S,


ALMA is a partnership of ESO (representing its member
states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The
Joint ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ. The National Radio Astronomy Observatory is a
facility of the National Science Foundation operated under a
cooperative agreement by Associated Universities, Inc.
Part of this work is based on observations made with the
NASA/ESA/CSA JWST. The data were obtained from the
Mikulski Archive for Space Telescopes at the Space Telescope
Science Institute, which is operated by the Association of
Universities for Research in Astronomy, Inc., under NASA
contract NAS 5-03127 for JWST. These observations are as
sociated with program 2107.
_Software:_ This research made use of `ASTROPY` and its affiliated packages (Astropy Collaboration et al. 2018, 2022); and
`glue` software of multidimensional data visualisation (Beaumont et al. 2015; Robitaille et al. 2017).


**DATA** **AVAILABILITY**


The specific observations used in this work are obtained
from PHANGS-ALMA, publicly accessible at `[https:](https://www.canfar.net/storage/list/phangs/RELEASES/PHANGS-ALMA/)`
```
//www.canfar.net/storage/list/phangs/RELEASES/
```

`[PHANGS-ALMA/](https://www.canfar.net/storage/list/phangs/RELEASES/PHANGS-ALMA/)`, and the PHANGS-JWST Treasury Survey,
available at DOI: `[http://dx.doi.org/10.17909/ew88-jt15](http://dx.doi.org/10.17909/ew88-jt15)` .
As a continuation of Cycle 1, the PHANGS-JWST Treasury Survey Cycle 2 with program ID 3707 (PI: Leroy) is
ongoing, and a publication detailing the data is currently in
preparation.


**REFERENCES**


Anand G. S., et al., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa3668) 501, 3621
Astropy Collaboration et al., 2018, [AJ,](http://dx.doi.org/10.3847/1538-3881/aabc4f) 156, 123
Astropy Collaboration et al., 2022, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac7c74) 935, 167
Athanassoula E., 1992, [MNRAS,](http://dx.doi.org/10.1093/mnras/259.2.345) 259, 345
Baba J., Saitoh T. R., Wada K., 2010, [PASJ,](http://dx.doi.org/10.1093/pasj/62.6.1413) 62, [1413](https://ui.adsabs.harvard.edu/abs/2010PASJ...62.1413B)
Beaumont C., Goodman A., Greenfield P., 2015, in Taylor A. R.,
Rosolowsky E., eds, Astronomical Society of the Pacific Conference Series Vol. 495, Astronomical Data Analysis Software
an Systems XXIV (ADASS XXIV). p. 101
Bertoldi F., McKee C. F., 1992, [ApJ,](http://dx.doi.org/10.1086/171638) 395, 140
Bitran M., Alvarez H., Bronfman L., May J., Thaddeus P., 1997,

[A&AS,](http://dx.doi.org/10.1051/aas:1997214) [125,](https://ui.adsabs.harvard.edu/abs/1997A&AS..125...99B) 99

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 13



Bolatto A. D., Leroy A. K., Rosolowsky E., Walter F., Blitz L.,
2008, [ApJ,](http://dx.doi.org/10.1086/591513) 686, 948

Bolatto A. D., Wolfire M., Leroy A. K., 2013, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-082812-140944) 51, 207
[Boyce P. J., Cohen R. J., Dent W. R. F., 1989, MNRAS, 239, 1013](http://dx.doi.org/10.1093/mnras/239.3.1013)

Busch L. A., Riquelme D., G¨usten R., Menten K. M., Pillai T.
G. S., Kauffmann J., 2022, [A&A,](http://dx.doi.org/10.1051/0004-6361/202244870) 668, [A183](https://ui.adsabs.harvard.edu/abs/2022A&A...668A.183B)

Buta R. J., et al., 2015, [ApJS,](http://dx.doi.org/10.1088/0067-0049/217/2/32) [217,](https://ui.adsabs.harvard.edu/abs/2015ApJS..217...32B) 32

Enokiya R., Torii K., Fukui Y., 2021, [PASJ,](http://dx.doi.org/10.1093/pasj/psz119) 73, S75
[Fragkoudi F., Athanassoula E., Bosma A., 2016, MNRAS, 462, L41](http://dx.doi.org/10.1093/mnrasl/slw120)
Freeman P., Rosolowsky E., Kruijssen J. M. D., Bastian N., Adamo
A., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx499) 468, 1769

Fujishita M., et al., 2009, [PASJ,](http://dx.doi.org/10.1093/pasj/61.5.1039) 61, [1039](https://ui.adsabs.harvard.edu/abs/2009PASJ...61.1039F)

Fukui Y., et al., 2006, [Science,](http://dx.doi.org/10.1126/science.1130425) 314, 106

Fux R., 1999, [A&A,](http://dx.doi.org/10.48550/arXiv.astro-ph/9903154) 345, 787

Gramze S. R., Ginsburg A., Meier D. S., Ott J., Shirley Y., Sormani
M. C., Svoboda B. E., 2023, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ad01be) [959,](https://ui.adsabs.harvard.edu/abs/2023ApJ...959...93G) 93

Henshaw J. D., Barnes A. T., Battersby C., Ginsburg A., Sormani
M. C., Walker D. L., 2023, in Inutsuka S., Aikawa Y., Muto
T., Tomida K., Tamura M., eds, Astronomical Society of the
Pacific Conference Series Vol. 534, Protostars and Planets VII.
p. 83 ( `[arXiv:2203.11223](http://arxiv.org/abs/2203.11223)` ), [doi:10.48550/arXiv.2203.11223](http://dx.doi.org/10.48550/arXiv.2203.11223)
Herrera-Endoqui M., D´ıaz-Garc´ıa S., Laurikainen E., Salo H., 2015,

[A&A,](http://dx.doi.org/10.1051/0004-6361/201526047) 582, A86

Kumar P., Riffert H., 1997, [MNRAS,](http://dx.doi.org/10.1093/mnras/292.4.871) 292, 871

Lang P., et al., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab9953) 897, 122

Lee C. W., Lee H. M., Ann H. B., Kwon K. H., 1999, [ApJ,](http://dx.doi.org/10.1086/306846) [513,](https://ui.adsabs.harvard.edu/abs/1999ApJ...513..242L)

[242](https://ui.adsabs.harvard.edu/abs/1999ApJ...513..242L)

Lee J. C., et al., 2023, [ApJ,](http://dx.doi.org/10.3847/2041-8213/acaaae) 944, L17

Leroy A. K., et al., 2021a, [ApJS,](http://dx.doi.org/10.3847/1538-4365/abec80) [255,](https://ui.adsabs.harvard.edu/abs/2021ApJS..255...19L) 19
Leroy A. K., et al., 2021b, [ApJS,](http://dx.doi.org/10.3847/1538-4365/ac17f3) [257,](https://ui.adsabs.harvard.edu/abs/2021ApJS..257...43L) 43
Leroy A. K., et al., 2021c, [ApJS,](http://dx.doi.org/10.3847/1538-4365/ac17f3) [257,](https://ui.adsabs.harvard.edu/abs/2021ApJS..257...43L) 43
Leroy A. K., et al., 2022, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac3490) 927, 149
Leroy A. K., et al., 2023, [ApJ,](http://dx.doi.org/10.3847/2041-8213/acaf85) [944,](https://ui.adsabs.harvard.edu/abs/2023ApJ...944L...9L) L9
Li A., 2020, Nature [Astronomy,](http://dx.doi.org/10.1038/s41550-020-1051-1) 4, [339](https://ui.adsabs.harvard.edu/abs/2020NatAs...4..339L)
Liszt H. S., 2006, [A&A,](http://dx.doi.org/10.1051/0004-6361:20054070) 447, 533

Liszt H. S., 2008, [A&A,](http://dx.doi.org/10.1051/0004-6361:200809748) 486, 467

Maeda F., Ohta K., Egusa F., Fujimoto Y., Kobayashi M. I. N.,
Inoue S., Habe A., 2025, Galactic structure dependence of
cloud-cloud collisions driven star formation in the barred
galaxy NGC 3627 ( `[arXiv:2502.06102](http://arxiv.org/abs/2502.06102)` ), `[https://arxiv.org/](https://arxiv.org/abs/2502.06102)`
```
  abs/2502.06102

```

Parker E. N., 1966, [ApJ,](http://dx.doi.org/10.1086/148828) 145, 811

Piner B. G., Stone J. M., Teuben P. J., 1995, [ApJ,](http://dx.doi.org/10.1086/176075) 449, 508

Robitaille T., Beaumont C., Qian P., Borkin M., Goodman
A., 2017, glueviz v0.13.1: multidimensional data exploration,
[doi:10.5281/zenodo.1237692](http://dx.doi.org/10.5281/zenodo.1237692)
Rosolowsky E., et al., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/stab085) 502, 1218

Salo H., et al., 2015, [ApJS,](http://dx.doi.org/10.1088/0067-0049/219/1/4) [219,](https://ui.adsabs.harvard.edu/abs/2015ApJS..219....4S) 4

Schinnerer E., Leroy A. K., 2024, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-071221-052651) 62, 369

Smith J. D. T., et al., 2007, [ApJ,](http://dx.doi.org/10.1086/510549) 656, 770

Sormani M. C., et al., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz2054) 488, 4663

Stark A. A., Bania T. M., 1986, [ApJ,](http://dx.doi.org/10.1086/184695) 306, L17

Stuber S. K., et al., 2023, [A&A,](http://dx.doi.org/10.1051/0004-6361/202346318) 676, [A113](https://ui.adsabs.harvard.edu/abs/2023A&A...676A.113S)

Suzuki T. K., Fukui Y., Torii K., Machida M., Matsumoto R.,
2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv2188) 454, 3049

Teng Y.-H., et al., 2023, [ApJ,](http://dx.doi.org/10.3847/1538-4357/accb86) 950, 119

Torii K., et al., 2010, [PASJ,](http://dx.doi.org/10.1093/pasj/62.5.1307) 62, [1307](https://ui.adsabs.harvard.edu/abs/2010PASJ...62.1307T)

Williams T. G., et al., 2024, arXiv [e-prints,](http://dx.doi.org/10.48550/arXiv.2401.15142) p. [arXiv:2401.15142](https://ui.adsabs.harvard.edu/abs/2024arXiv240115142W)

de Vaucouleurs G., de Vaucouleurs A., Corwin Jr. H. G., Buta
R. J., Paturel G., Fouque P., 1991, Third Reference Catalogue
of Bright Galaxies
den Brok J., et al., 2025, [AJ,](http://dx.doi.org/10.3847/1538-3881/ad888a) [169,](https://ui.adsabs.harvard.edu/abs/2025AJ....169...18D) 18



**APPENDIX** **A:** **DIAGNOSTIC** **MAPS,** **IMAGES**
**AND** **PLOTS** **OF** **SAMPLE** **GALAXIES** **WHICH**

**ARE** **EXHIBITING** **EVFS**


The figures in this section are configured as follows.
For galaxies where EVFs are identified, figures with caption
numbering ending with an “a” (e.g., Figs. A1a– A9a) present
the CO(2–1) PP and PV, JWST/MIRI 7.7 _µ_ m band image,
and spectra with Gaussian fits within the identified EVF regions. The allocation of the panels are configured similarly
to Figs. 2 and 4. Following these, figures with caption numbering ending with a “b” (e.g., Figs. A1b – A9b) provide the
zoom-in view of the regions marked with rectangular boxes
in the 7.7 _µ_ m band observations of the corresponding galaxy
similar to what is shown in Fig. 3.


MNRAS **000**, 000–000 (0000)

14 _Kolcu_ _et_ _al._


**Figure** **A1a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 1097.


**Figure** **A1b.** Zoomed-in 7.7 _µ_ m band observations of NGC 1097.


MNRAS **000**, 000–000 (0000)

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 15


**Figure** **A2a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 1512.


**Figure** **A2b.** Zoomed-in 7.7 _µ_ m band observations of NGC 1512.


MNRAS **000**, 000–000 (0000)

16 _Kolcu_ _et_ _al._


**Figure** **A3a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 2566.


**Figure** **A3b.** Zoomed-in 7.7 _µ_ m band observations of NGC 2566.


MNRAS **000**, 000–000 (0000)

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 17


**Figure** **A4a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 2903. The left panels show the same
as in Figs. 2, and the right panels show the same as in Fig. 4.


**Figure** **A4b.** Zoomed-in 7.7 _µ_ m band observations of NGC 2903.


MNRAS **000**, 000–000 (0000)

18 _Kolcu_ _et_ _al._


**Figure** **A5a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 3627.


MNRAS **000**, 000–000 (0000)

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 19


**Figure** **A5a.** _Continued_ . CO(2–1) spectra within EVF regions for NGC 3627.


**Figure** **A5b.** Zoomed-in 7.7 _µ_ m band observations of NGC 3627.


MNRAS **000**, 000–000 (0000)

20 _Kolcu_ _et_ _al._


**Figure** **A6a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 4303.


**Figure** **A6b.** Zoomed-in 7.7 _µ_ m band observations of NGC 4303.


MNRAS **000**, 000–000 (0000)

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 21


**Figure** **A7a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 4535.


**Figure** **A7b.** Zoomed-in 7.7 _µ_ m band observations of NGC 4535.


MNRAS **000**, 000–000 (0000)

22 _Kolcu_ _et_ _al._


**Figure** **A8a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 4548.


**Figure** **A8b.** Zoomed-in 7.7 _µ_ m band observations of NGC 4548.


MNRAS **000**, 000–000 (0000)

_Extreme_ _cloud_ _collisions_ _in_ _nearby_ _barred_ _galaxies_ 23


**Figure** **A9a.** Diagnostic maps, 7.7 _µ_ m band observations and spectra within EVF regions for NGC 5643.











0 _._ 5 1 _._ 0
_x_ [kpc]





**Figure** **A9b.** Zoomed-in 7.7 _µ_ m band observations of NGC 5643.



MNRAS **000**, 000–000 (0000)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Rotate each CO(2-1) datacube so the positive half of the line of nodes aligns with the negative x-axis, convert angular scales to physical kpc, integrate over velocity and spatial dimensions to create 1 PP and 2 PV maps, visually enclose bar dust lanes with contours in glue, and visually select compact, broad-lined EVFs in the PV maps.",
  "failed_quote": "To search for EVFs in each of the 29 galaxies of our sample, we construct one position position (PP) and two position-velocity (PV) maps from its PHANGS-ALMA CO(2–1) data cube by integrating the cube over velocities and over two spatial dimensions, respectively."
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Visually define a circular region on the dust lane in PP space encompassing the EVF, centre on the brightest point, fit a 2D Gaussian to the PP map to get centre coordinates (x, y) and standard deviations (sigma_x, sigma_y), and compute R_EVF and R_cen.",
  "failed_quote": "Further, to obtain the galactocentric distance (Rcen) of the EVFs, we use the coordinates of the EVF centre (x and y), determined from the 2D Gaussian fit described above, in the formula Rcen = sqrt((x - xo)^2 + (y - yo)^2)"
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "eta = sqrt(2 ln 2) = 1.18 in R_EVF = eta * sqrt(sigma_x * sigma_y)",
  "failed_quote": "R_EVF = η sqrt(σ_x σ_y) , (1) where the factor η = sqrt(2 ln 2) = 1.18 comes by modelling the surface brightness as a two-dimensional Gaussian and using the half width at half maximum as the radius (Rosolowsky et al. 2021)."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Delta v = (2 sqrt(2 ln 2)) sigma_v; MW longitude ranges l = 2.7-3.4 deg (for l=3.2 deg EVF) and l = 5.0-5.6 deg (for l=5.4 deg EVF), latitude unrestricted",
  "failed_quote": "The standard deviation σv of the fit is taken as a measure of the velocity dispersion, and the full width at half maximum (FWHM) of the fit as a measure of the velocity extent, ∆v = (2 sqrt(2 ln 2))σv."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "Delta v = (2 sqrt(2 ln 2)) sigma_v; MW longitude ranges l = 2.7-3.4 deg (for l=3.2 deg EVF) and l = 5.0-5.6 deg (for l=5.4 deg EVF), latitude unrestricted",
  "failed_quote": "The left panel presents the total spectrum within the extracted EVF region at l = 3.2◦, corresponding to emission at a longitude range 2.7–3.4◦, latitude not restricted. The right panel presents the total spectrum within the extracted EVF region at l = 5.4◦, corresponding to the emission at a longitude range of 5.0–5.6◦, latitude unresricted."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Integrate CO intensity I_CO within R_EVF, multiply by constant alpha_CO to get M_CO, and compute M_vir = 5 sigma_v^2 R_EVF / G and alpha_vir = 2 M_vir / M_CO.",
  "failed_quote": "Following Bertoldi & McKee (1992) and Rosolowsky et al. (2021), we calculate the virial masses and virial parameters as: Mvir = 5σv^2 REVF / G (4) αvir = 2Mvir / MCO . (5)"
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Multidimensional data visualisation and isolating bar dust lanes and EVF regions in PP and PV maps",
  "failed_quote": "To better visualise each dust lane we draw a contour enclosing it in the PP map, and we colour in red or blue all data in the data cube with spatial coordinates falling within this contour. For this purpose we use the visualisation software glue (Beaumont et al. 2015; Robitaille et al. 2017)."
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Milky Way EVF (l = 3.2 deg) velocity spread (FWHM) = 70.64 km s^-1",
  "failed_quote": "This yields a FWHM 70.64 ± 2.07 km s−1 for the EVF component and a 13.92 ± 2.14 km s−1 for the component of the overlapping dust lane."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Resolving features comparable to the largest Milky Way EVFs (~100 pc) requires cloud-scale (~50-150 pc) molecular gas spectroscopy from PHANGS-ALMA, while PHANGS-JWST 7.7 um imaging traces lower column density gas streams that fall below the CO sensitivity limit.",
  "failed_quote": "Since the extent of the largest EVFs in the MW is approximately 0.7◦∼100 pc at the distance of the Galactic centre, this program requires observations of molecular clouds in nearby galaxies at resolutions on the order of ∼100 pc or better."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Photometric stellar bar classification (rejected for sample selection because stellar bars can be gas-depleted or unbarred in CO, and vice versa)",
  "failed_quote": "For example, some galaxies classified as strongly barred in the literature appear unbarred in CO(2–1), potentially indicating gas-depleted bars where further inflow has ceased, or cases where star-forming clumps mimic elongated features in stellar light but lack coherent gas structures in CO."
 }
]
```
