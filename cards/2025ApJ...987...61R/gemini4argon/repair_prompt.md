# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...987...61R\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version May 20, 2025
Typeset using L [A] TEX **twocolumn** style in AASTeX631


**Resolved ALMA [C** ii **] 158 μm Observations at Cosmic Noon: ISM Structure and Dynamics of**
**Starbursting QSO SDSSJ1000**


[Christopher Rooney,](http://orcid.org/0000-0002-8513-2971) [1, 2] [Bo Peng,](http://orcid.org/0000-0002-1605-0032) [3] [Amit Vishwas,](http://orcid.org/0000-0002-4444-8929) [4] [Gordon Stacey,](http://orcid.org/0000-0003-1260-5448) [1] [Thomas Nikola,](http://orcid.org/0009-0000-6722-7216) [4] [Cody Lamarche,](http://orcid.org/0000-0003-1874-7498) [5]

[Catie Ball,](http://orcid.org/0000-0002-1895-0528) [1] [Carl Ferkinhoff,](http://orcid.org/0000-0001-6266-0213) [5] [Drew Brisbin,](http://orcid.org/0000-0002-4795-419X) [6] [and Steven Hailey-Dunsheath](http://orcid.org/0000-0002-8504-7988) [7]


1 _Department of Astronomy, Cornell University, Ithaca, NY 14853, USA_
2 _National Institute of Standards and Technology, Boulder, CO 80305, USA_
3 _Max Planck Institute for Astrophysics¸ Garching, Germany_
4 _Cornell Center for Astrophysics and Planetary Science, Cornell University, Ithaca, NY 14853, USA_
5 _Department of Physics, Winona State University, Winona, MN 55987, USA_
6 _Joint ALMA Observatory, Alonso de Cordova 3107, Vitacura, Santiago, Chile_
7 _California Institute of Technology, Pasadena, CA 91125, USA_


ABSTRACT
We present spatially resolved Alma Band-9 observations of the [Cii] 158 μm fine structure line
from an optically selected quasar, Sdss J100038.01+020822.4 (j1000), at _z_ = 1 _._ 8275. By utilizing

[Oi] 63 μm line observations from Herschel/pacs and constructing a detailed dust sed using Herschel and Spitzer archival imaging data, we show that the [Cii] line emission is well explained by a
photodissociation region (pdr) model, in which the emission arises from the surfaces of molecular
clouds exposed to far-uv radiation fields _∼_ 5 _·_ 10 [3] times the local interstellar radiation field (G 0 ). We
find a factor of 30 variation in spatially resolved [CII]/Far-IR continuum across the source which is
explained by the reduced fraction of cooling via [Cii] line emission at such high far-uv field strengths.
By matching derived pdr parameters to the observed far-IR line and continuum intensities we derive

_∼_
cloud size-scales and find that typical cloud radii in J1000 are 3.5 pc, perhaps indicating an ism that
is highly fractured due to intense star formation activity. We model the galaxy dynamically and find
that the [Cii] emission is contained within a compact, dynamically cold disk with _v/σ_ = 6 _._ 2, consistent with the IllustrisTNG50 cosmological simulation. We also report the discovery of a companion
galaxy to j1000 confirmed by the detection of [Cii] and use recently obtained Jwst/nircam imaging
of the system to argue for j1000 being an interacting system. With total stellar mass _∼_ 1 _._ 5 _×_ 10 [10] M _⊙_
and main-component dynamical mass ≳ 10 [11] M _⊙_, the j1000 system is a progenitor to the most massive
galaxies seen in the local Universe.


_Keywords:_ High-redshift galaxies (734), Galaxy spectroscopy (2171), Photodissociation regions (1223),
Dust continuum emission (412), Interstellar medium (847), Galaxy dynamics (591)



1. INTRODUCTION

During the epoch of Cosmic Noon ( _z_ _∼_ 1 _−_ 3), the
star formation rate density (sfrd) peaked, so much so
that a majority of stars in the present-day Universe were
formed during this time period (Madau & Dickinson
2014). While recent studies have pushed the frontiers
of our understanding of galaxy evolution to higher and


Corresponding author: Christopher Rooney
[ctr44@cornell.edu](mailto: ctr44@cornell.edu)



higher redshifts (e.g. Rybak et al. 2020b; Rizzo et al.
2022; Atek et al. 2023; Curtis-Lake et al. 2023), constructing a complete picture of galaxy evolution during
Cosmic Noon is challenging due to difficulties arising
from the fact that important tracers of dusty star formation, such as the far-infrared (fir) fine-structure (fs)
lines [Cii] 158 μm and [Oiii] 88 μm, are redshifted to
narrow, low-transmission telluric windows for groundbased observations.
Fir fs lines are an essential part of a complete understanding of the conditions of star formation. Firstly,

2 Rooney et al.



they are relatively unaffected by dust extinction. This is
important since the majority of the most extreme starformation episodes and on average about half of the star
formation in the history of the Universe occurred in
dusty star-forming galaxies (dsfgs, see e.g.: Houck et al.
1985, Whitaker et al. 2017, Zavala et al. 2021). Optical
wavelength lines will not escape from heavily extincted
starformationregions, andevenmoderateextinctionrequires correction in line ratios. The fir lines avoid this
complexity by simply having longer wavelengths. Second, the excitation potential of fir fs lines, of order
100 K, is very low compared to that of optical lines, and
comparable with physical gas temperatures, so fir line
emissivities are only weakly dependent on gas temperature. In contrast, optical lines, which have emitting levels that are _∼_ 30 _,_ 000 K above the ground state, have
emissivities that are very strongly temperature dependent.
The [Cii] 158μm line in particular is among the
brightest emission lines from star forming galaxies, often amounting to a few percent of the total luminosity
of the system (Carilli & Walter 2013), so it is a natural target for studies of galaxy evolution. Since carbon’s
ionization potential, 11.3 eV, is lower than that of hydrogen, [Cii] emission can come from the neutral gas
phase of the ism in addition to the ionized phase. This
is useful for dynamical studies, providing velocity information for both of those parts of the galaxy, but complicates the use of [Cii] as a star formation tracer as [Cii]
comes from these diverse types of regions and its luminosity is sensitive to the physical conditions of the emitting gas. However, in combination with other spectral
lines and the far-ir continuum emission, one can derive
the physical conditions of the emitting gas and its cooling rate, and therefore the properties of the sources of
gas heating. The preponderance of [Cii] line emission
from most star forming galaxies arises from the warm,
dense photodissociated surfaces of molecular clouds exposed to far-uv (fuv, 6 eV _<_ _hν_ _<_ 13 _._ 6 eV) radiation
from nearby OB stars. The [Cii] line to far-ir continuum luminosity ratio is a sensitive indicator for the
fuv field strength within these photo-dissociation regions (pdrs), and by combining it with other spectral
lines and bolometric luminosity measurements, appropriate corrections can be made to measure the physical
properties of the gas associated with pdrs.

[Cii] line emission has been reported from hundreds
of extragalactic sources from the initial surveys in the
local Universe with the Kuiper Airborne Observatory
(e.g. Stacey et al. 1991, Crawford et al. 1985), iso (e.g.
Luhman et al. 1998, Malhotra et al. 2001) and Herschel (D´ıaz-Santos et al. 2013), to high redshift surveys



with, for example, the Caltech Submillimeter Observatory (cso; Hailey-Dunsheath et al. 2010, Stacey et al.
2010, Brisbin et al. 2015), Apex (Gullberg et al. 2015;
Ferkinhoff et al. 2014), and the Atacama Large Millimeter/submillimeter Array (Alma; e.g. Schaerer et al.
2015; Umehata et al. 2017; Zanella et al. 2018; Schaerer
et al. 2020; Bouwens et al. 2022; Decarli et al. 2018; Rybak et al. 2021).
However, the numbers of sources reported from
galaxies at Cosmic Noon in the [CII] line emission remains modest due to the challenging nature of observations with the high frequency Bands 9 and 10 of Alma
(Lamarche et al. 2018; McKinney et al. 2020; Rybak
et al. 2021). Here we present Alma Band 9 observations of the [Cii] 158 μm line and the underlying
dust continuum from an optically selected quasar, Sdss
J100038.01+020822.4 at redshift _z_ = 1 _._ 8275, hereafter referred to as sdss j1000 or simply j1000. Sdss
j1000 was selected based on its high 1.2 mm brightness
(4 _._ 8 _±_ 1 _._ 0 mJy) in the Mambo-2/iram survey of the
Cosmos field (Bertoldi et al. 2007). In addition, Aravena et al. (2008) observed four CO lines, (2–1), (4–
3), (5–4) and (6–5), with the Iram 30 m telescope, and
their Large Velocity Gradient analysis indicated that the
active galactic nucleus (agn) is likely not the dominant
heat source for the molecular gas, instead preferring star
formation as the main heat source. Sdss j1000 was also
included in the first [Cii] survey at the Cosmic Noon
performed using the z (Redshift) and Early Universe
Spectrometer (Zeus-1) on the Caltech Submillimeter
Observatory (cso, Stacey et al. 2010), which supported
a scenario in which star formation is extended on kiloparsec scales in Cosmic Noon star-forming galaxies and

some quasars.
Due to its classification as an optically-selected quasar
and its high star-formation rate, j1000 is referred to
as a “mixed” system, a type of galaxy only seen in the
Cosmic Noon era of the Universe. In the Sanders
et al. (1988) paradigm, this class of systems is transitioning from ulirg-like, with high star formation, to
agn-dominated, quiescent systems. This is a reasonable interpretation for j1000 as shown by the short
gas-depletion time observed by Aravena et al. (2008)
(for other studies on the interactions between agn and
star formation see Perna et al. 2018; Stacey et al. 2018;
Valentino et al. 2021; Frias Castillo et al. 2024).
The paper is organized as follows. Section 2 presents
our Alma observations and ancillary data sets. Section
3 presents our main results derived from these data, and
Section 4 discusses the implications of these results includingtheconfirmationofanassociatedsatellitegalaxy

Resolved ALMA Study of SDSS J1000 3



andphotodissociationregionmodeling. Section5isour
summary and outlook for future investigations.
In this work we assume a Λ cold dark matter
flat
cosmology with Ω _m_ = 0 _._ 3, Ω Λ = 0 _._ 7 and _H_ 0 =
70 km s _−_ 1 Mpc _−_ 1 . At _z_ = 1 _._ 8275, this corresponds to an
_−_ 1
angular scale of 8 _._ 44 kpc arcsec, luminosity distance
_D_ _L_ = 13 _._ 91 Gpc.


2. OBSERVATIONS

2.1. _Alma Observations_

We carried out observations targeting the [Cii]
158μmspectrallineandtheunderlyingdustcontinuum
in sdss j1000 using Alma. At _z_ = 1 _._ 8275, the [Cii]
158 μm line is redshifted to 446 μm, placing it in Alma
Band 9. The observations were carried out in Cycle 3 in
two execution blocks on November 16, 2016 and April
22, 2017 under some of the best observing conditions
possible at the Chajnantor plateau with precipitable water vapor (pwv) 0.26 mm and 0.39 mm respectively. A
total of 42 and 40 antennas were utilized in the 12-m array with source-projected baselines ranging from 15 m
to 919 m and 15 m to 430 m in the first and second execution blocks, resulting in maximum recoverable scales
of 1 _[′′]_ _._ 3 and 2 _[′′]_ _._ 0 respectively. The integration time was 22
minutes in each execution block, for a total on-source
time of 44 minutes.
We carried out standard data reduction using pipeline
version `42030` within the Common Astronomy Software Application (casa) version `5.4.0-68` (McMullin
et al. 2007). As an additional check, we manually inspected and flagged any outliers and baselines at the raw
visibilities level. The data from the two execution blocks
was then combined for imaging.
We identified the spectral channels containing the line
emission and flagged them before using the casa routine `UVContSub` to and remove a linear continuum
fit
model from the data. We then imaged the continuumfree raw visibilities to create a line cube with a channel width of 50 km/s and pixel size 0 _[′′]_ _._ 015 _×_ 0 _[′′]_ _._ 015 using Briggs weighting with a robustness parameter of 0.5.
This results in a synthesized beam size of 0 _[′′]_ _._ 20 _×_ 0 _[′′]_ _._ 17
with position angle 55°, which corresponds to a spatial
resolution 1 _._ 7 _×_ 1 _._
4 kpc at the source redshift. After flagging, the 5th percentile baseline length was 53 m, giving our image a maximum recoverable scale of 1 _[′′]_ _._ 7. We
achieved a 1- _σ_ sensitivity of 2 mJy/beam/ch for the spectral line cube.
We also created a dust-continuum image of sdss
j1000 by combining all the line-free spectral channels.
The data were imaged with the same pixel size as above
using Briggs weighting with a robustness parameter 0.5,
resulting in a synthesized beam size of 0 _[′′]_ _._ 19 _×_ 0 _[′′]_ _._ 16 with



100


50


0


_−_ 50


_−_ 100





_−_ 150


_−_ 1000 _−_ 500 0 500 1000

Velocity, km s _[−]_ [1]


**Figure** **1.** Continuum-subtracted Herschel/pacs spectrum
of the [Oi] 63 μm line from sdss j1000 in blue. The shaded
region indicates the portion of the spectrum summed to estimate the total line flux, and the orange line shows the bestfit Gaussian line profile. The velocity axis is shown relative to
_z_ = 1 _._ 8275 to match the Alma spectra presented below.


position angle 55°. This corresponds to a spatial resolution of 1 _._ 6 _×_ 1 _._ 4 kpc. The continuum image has a 1- _σ_ sensitivity of 0.3 mJy/beam and is centered at 669.5 GHz,
or 158.3 μm rest-frame.


2.2. _Herschel [O_ i _] Line Observation_

Toenablemodelingofthe[Cii]lineemissioninapdr
paradigm, we also utilized [Oi] 63.184 μm observations
thatwereconductedwiththeHerschel/pacsspectrometer (Poglitsch et al. 2010) targeting sdss j1000 (Program `OT1_gstacey_3`, ObsID `1342233711` ). The red
_._
shifted wavelength of 178 56 μm was observed in 3 nod
cycles with 10 repetitions per nod cycle. The data were
reduced with the Herschel Interactive Processing Environment (hipe, v12.1.0; Ott 2010) with `oversample=2`

.
for a Nyquist sampled spectral resolution of 103 km s _[−]_ [1]
Sdss j1000 is small compared to the beam size of Herschel, soonlythespectrumofthecentralspaxel wasconsidered. After the point-source correction was applied,
the spectrum was continuum-subtracted and a Gaussian line was estimated from the continuumprofile
subtracted spectrum (Fig. 1). The line flux was estimated by integrating the continuum-subtracted spectrum over a Δ _λ_ = 2 _×_ fwhm of the
wavelength range
Gaussian profile. This yields a line flux of 29 _±_ 9 Jy km
s _[−]_ [1] including only statistical uncertainty, with an addi
.
tional 12% calibration uncertainty [1]


1 Herschel Explanatory Supplement Volume III (HERSCHEL-HSCDOC-2101, version 4.0.1)

2 _×_ _RMS_, where _RMS_ = 0 _._ 7 Jy km s _[−]_ [1] beam _[−]_ [1] . Nircam
images from three bandpass filters, f115w, f150w, and f277w
were mapped to the blue, green, and red channels (respectively) of the displayed cutout. The astrometric calibration of
the jwst data is good to within _∼_ 0 _[′′]_ _._ 1 . The possible tidal tail
and bridge between the two components are called out. The
2 _[′′]_ diameter circle is provided to give an idea of the scale of
the emission relative to the Alma maximum recoverable scale,
which is 2 _[′′]_ in the most optimistic scenaro.


2.3. _Archival Continuum Observations and Data_

ScovSdss j1000 is in the well-studied cosmos field (
ille et al. 2007) and therefore has a rich, multiwavelength set of archival data.
ThenewestobservationsinthearchivearefromJwst,
and were observed and released on April 15, 2023 as part
of the Cosmos-Web Cosmic Origins Survey (Casey
et al. 2023), Jwst program number 1727 (PI: Kartaltepe). During this program, Jwst nircam observed a
field containing j1000 in 4 bands: f115w, f150w, f227w,
and f444w. By mapping the three shorter wavelength
bands to red, green, and blue, we created a color photometric image of j1000 (Fig. 2) and overlaid our Alma

[Cii] contours. This extremely deep Jwst imaging reveals possible tidal interaction features between the two
sources, and beautiful spiral arms in the main component!
We extracted far-ir to sub-mm photometry for sdss
j1000 from the Herschel Point Source Archive (Marton
et al. 2017; Schulz et al. 2017) for both spire and pacs,
yielding five photometric data points between 100-500
μm (see Table 1) sampling the peak of the dust emission.
The Herschel beam size ranged from 7 _[′′]_ for the 100 μm
observation to 30 _[′′]_ for the 500 μm observation, so no
morphological information could be recovered. Uncer


tainties due to confusion are included in the errors reported in Table 1.
Finally, we used (observed frame) 24 and 70 μm fluxes
from Spitzer/mips for sed modeling, from Sanders
et al. (2007), 872.6 μm flux from Alma program
`2016.1.00463.S`, 2068 μm flux from Alma program
`2021.1.00705.S`, and 3038 μm flux from Alma program `2021.1.00246.S` (see Table 1).


3. RESULTS

Our Alma observations detect the [Cii] 158 μm line
and continuum from sdss j1000 at high significance,
as seen in the spectral line map with continuum contours in Fig. 3 (top). The moment-0 map in Fig. 3 (top)
was constructed by stacking the channels containing the
line, resulting in an image with an _RMS_ = 0 _._ 7 Jy km
s _[−]_ [1] beam _[−]_ [1] . The moment-1 map also shows [Cii] 158
μmfluxco-spatialtoasourcepreviouslyreportedinhst
imaging by Aravena et al. (2008) 1 _[′′]_ _._ 9 west-south-west
(wsw) from the main source.
To estimate line and continuum we numerifluxes,
cally integrate the flux within a circular aperture centered on the source, and to estimate the error in these
measurements we measure the rms in an
flux equalsizedaperturecenteredaway fromthesource(inunitsof
Jy/beam) and multiply by _[√]_ ~~_n_~~ _beams_ ~~.~~ For the main source’s
1 _[′′]_ _._ 45 and calculate a to
[Cii] flux, we use a diameter =
tal line flux of 37 _._ 7 _±_ 3 _._ 3 Jy km s _[−]_ [1] . This flux is about
half the flux detected by cso/Zeus-1 observations conducted by Stacey et al. (2010). Much of this could be attributed to flux calibration and statistical errors within
the Zeus-1 observations, but in light of the large scale
stellar emission detected with Jwst nircam (see Fig. 2)
itisalsolikelythatsome[Cii]linefluxobservedwiththe
11 _[′′]_ _._ 5 Zeus-1 beam is “resolved out” by Alma (see §4.1).
A bright source to the west of sdss j1000 is detected
in Hst/acs imaging (Aravena et al. 2008). We report
the detection of [Cii] 158 μm line emission co-spatial
with this source, at the same redshift, thereby spectroscopicallyconfirmingthatitisphysicallyassociatedwith
j1000. We will refer to j1000 as the “main” source and
the western companion source as the “satellite” in this
paper. We extract the [Cii] flux for the satellite using a
circular aperture of 0 _[′′]_ _._ 35 and detect it at 4 _σ_ significance
with a flux of 2 _._ 3 _±_ 0 _._ 6 Jy km s _[−]_ [1] .
The dust continuum emission from the main source
is spatially resolved but is found to be relatively compact as compared to the extent of the [Cii] line emission: The 2-D Gaussians of best fit to the cleaned images have fwhms 0 _[′′]_ _._ 216 _±_ 0 _[′′]_ _._ 006 for the continuum and
0 _[′′]_ _._ 43 _±_ 0 _[′′]_ _._ 04 for the line emission. There is extended
emission beyond the Gaussian shape, however, for both

Resolved ALMA Study of SDSS J1000 5



the continuum and the line, so we use larger diameter
apertures for computing the total flux of both. Using a
circular aperture of 1 _[′′]_ _._ 05, we measure the main source’s
continuum flux density = 55 _._ 6 _±_ 1 _._ 8 mJy. We also mea
_[′′]_ _._ 4
sure the integrated flux density for the satellite in a 0
diameter aperture to be 3 _._ 5 _±_ 0 _._ 7 mJy.
This Alma data has considerably higher spectral resolution than previous observations of this source. Using the same apertures as we used for the [Cii] line
integrated flux measurements, we also create the spec
.
tral profiles seen in Fig. 4 We clearly recover a doublehorned spectral profile for j1000 offset by +80 km s _[−]_ [1]
relative to the previously reported redshift of _z_ = 1 _._ 8275
and report a [Cii] redshift of _z_ = 1 _._ 82825 _±_ 0 _._ 00002.
The double-horned spectral profile and the symmetry
seen in the moment 1 map (Fig. 3, bottom) suggest that
a rotationally supported disk geometry is an appropriate
model for the dynamical structure of j1000. We explore
this idea further in §3.2.
Leveraging the sensitivity of our continuum and spec
_[′′]_ _._ 04 _±_ 0 _[′′]_ _._ 02
tral line maps, we identify a spatial offset of 0
between the dust continuum peak and the peak of [Cii]
line emission. This modestly significant offset can be
seen by eye by comparing the contours to the image in
Fig. 3 (top).


3.1. _SED analysis_
Using publicly-available Herschel data and
previously-published continuum measurements (listed
in Table 1), we create a model for the dust sed of sdss
j1000 (Fig. 5). We use the modified blackbody routine
mercurius (Witstok et al. 2022), which parameterizes
the dust emission in the form



2 _[◦]_ 08 _[′]_ 23 _._ 0 _[′′]_


22 _._ 5 _[′′]_


22 _._ 0 _[′′]_


21 _._ 5 _[′′]_


10 [h] 00 [m] 38 _._ 05 [s] 38 _._ 00 [s] 37 _._ 95 [s] 37 _._ 90 [s]


RA (J2000)


2 _[◦]_ 08 _[′]_ 23 _._ 0 _[′′]_


22 _._ 5 _[′′]_


22 _._ 0 _[′′]_


21 _._ 5 _[′′]_


10 [h] 00 [m] 38 _._ 05 [s] 38 _._ 00 [s] 37 _._ 95 [s] 37 _._ 90 [s]


RA (J2000)



6


5


4


3


2


1


0


_−_ 1


200


100


0



_S_ _ν_ = _M_ dust _κ_ _ν_ _D_ [1 +] [2] _L_ [(] _[ z][z]_ [)] [[] _[B]_ _[ν]_ [ (] _[T]_ [dust] [)] _[ −]_ _[B]_ _[ν]_ [ (] _[T]_ [CMB] [ (] _[z]_ [))]] (1)



where _κ_ _ν_ _∝_ _ν_ _[β]_, to model the continuum emission from
sdss j1000. With this model, we find fir [2] luminosity =
(7 _._ 2 _±_ 0 _._ 3) _·_ 10 [12] L _⊙_, star-formation rate = 1640 _±_ 80 M _⊙_
yr _[−]_ [1], and dust mass = (1 _._ 8 _±_ 0 _._ 1) _·_ 10 [9] M _⊙_ . These results
match those obtained through the methods detailed in
Brisbin et al. (2015), using template fitting of Dale &
Helou (2002) models.


3.2.
_Disk fitting_
As mentioned above, the symmetry in the moment-1
map of sdss j1000 suggests the presence of ordered rotation. To investigate this further, we use the UVModelDisk routine from Pavesi et al. (2018) to model j1000


2 Following Brisbin et al. (2015), we define fir luminosity as the integrated luminosity between 42.5 and 122.5 μm, and tir (total infrared) luminosity as the integrated luminosity from 8-1000 μm



**Figure 3.** Top: The moment-0 map of the [Cii] line in sdss
j1000, with rest-frame 158μm continuum contours superimposed. Bottom: The moment-1 velocity map of the [Cii] line
emission, alsowithrest-frame158μmcontinuumcontours. In
both cases the continuum contour levels are 1.5–19.5 mJy in
steps of 3 mJy.


**Table** **1.**
Sdss j1000 continuum fluxes used for sed modeling. Spitzer mips data are provided by the s-cosmos project
Sanders et al. (2007); bolocam data is from Aravena et al.
(2008). Herschel/pacs and spire data from their respective Herschel Point Source Catalogs: Marton et al. (2017) and
Schulz et al. (2017). All of these observations treat j1000 as a


|Schulz et al. ( point source. [μm]|(2017). All of these observations treat j1000 as a Flux Density [mJy] Source|
|---|---|
|_λobs_ [μm]|Flux Density [mJy]<br>Source|
|70<br>100<br>160<br>250<br>350<br>500<br>446<br>873<br>1100<br>1200<br>2068<br>3038|7_ ±_ 2<br>mips<br>24_ ±_ 4<br>Herschel/pacs<br>73_ ±_ 9<br>Herschel/pacs<br>85_ ±_ 5<br>Herschel/spire<br>69_ ±_ 8<br>Herschel/spire<br>35_ ±_ 7<br>Herschel/spire<br>55_._6_ ±_ 1_._8<br>Alma/this work<br>9_._8_ ±_ 0_._4<br>Alma` 2016.1.00463.S`<br>5_._6_ ±_ 1_._9<br>Bolocam<br>4_._8_ ±_ 1_._0<br>Mambo<br>0_._3_ ±_ 0_._1<br>Alma` 2021.1.00705.S`<br>0_._11_ ±_ 0_._02<br>Alma` 2021.1.00246.S`|

6 Rooney et al.





Main component spectrum


|== =71 1.. 21 1 .70 6+ − 9+ − 30 0.0 −73 .0 3. 00 . + − 0 .5 · 18 .5 18 51 31 1· 0 M ·1 1 10 2 ⊙ 1 L3 ⊙ y L Mr⊙ − ⊙1 TT T p d dz eu u= βaks s0 It t == = 36 6 6 23 3 . .. . 2 28 8 −++ −+ − 001 1 −01 1. . .4 4 8. . .05 5 8 .K K K<br>= + 0 0 9 R = + 0. 1 10 0|Col2|
|---|---|
|||







_λ_ obs (mm)
10 _[−]_ [1] 10 [0]













0 500 1000 1500 2000 2500

Radio Velocity, km s _[−]_ [1]


Satellite component spectrum









0 _._ 0


0 _._ 0



0 500 1000 1500 2000 2500

Radio Velocity, km s _[−]_ [1]


**Figure 4.** The continuum-subtracted [Cii] 158 μm spectrum
of sdssj1000’scomponents: extractedfromanapertureofdiameter 1 _[′′]_ _._ 45 centered on the main source (top) and, extracted
using an 0 _[′′]_ _._ 35 aperture centered on the satellite source (bottom). Velocity is plotted with respect to _z_ = 1 _._ 8275, with the
vertical line indicating the central velocity from the disk modeling routine. The atmospheric transmission is plotted below
the spectrum.


as a rotating disk. Within UVModelDisk, the goodnessof-fit parameter is computed by transforming the disk
model to the uv plane and comparing the resulting visibilities to the calibrated Alma visibilities. This is beneficial due to the fact that visibilities are statistically independent, while pixels in Alma images are not, and thus
no covariance matrices need to be computed when running UVModelDisk. More technical details of the process are described in Appendix A.


3.2.1. _Model parameters_

Ten physical parameters of a rotating disk, listed in Table 2, were varied during model construction, and an
additional four parameters corresponding to the continuum emission were fixed to the values output by the
casa routine `UVModelFit` in “Gaussian Source” mode
on channels which do not contain the line. This produces a 2-dimensional Gaussian model of the continuum in the image plane, and assumes that the continuum is constant in frequency. For each parameter that
is allowed to vary, UVModelDisk returns its posterior









Here, _r_ 0 _,v_ is the characteristic distance scale of the velocity curve, expressed in terms of apparent distance on sky
in arcsec. In our case, where _r_ 0 _,v_ _≪_ beam size, this reduces to a flat rotation curve where _v_ = _v_ _max_ .
Following Rizzo et al. (2020), we can compute the
_v/σ_ ratio to determine how ordered or disordered the
galaxy’s bulk motion is. When _v/σ_ _>_ 2, ordered motion
dominates over random motion. We calculate _v/σ_ = 6 _._ 2

Resolved ALMA Study of SDSS J1000 7


**Table 2.** [Top] The parameters used in the UVModelDisk routine. Parameter names are listed in the first column, followed by the
prior ranges used in the nested sampling routine, the prior types used, and the median and 1 _σ_ width of the posterior distribution.

[Bottom] Parameters for the continuum model were fixed beforehand and not allowed to vary during the sampling.

|Parametername|Prior Priortype Posterior|
|---|---|
|Gas velocity dispersion (_ρσ_) [km/s]<br>Brightness fwhm [arcsec]<br>Maximum Rotational Velocity [km s_−_1]<br>Velocity Scale [arcsec]<br>Velocity center [GHz, observed]<br>Inclination angle [deg]<br>Position angle [deg]<br>Ra center [arcsec]a<br>Dec center [arcsec]a<br>Total Flux[Jy km s_−_1]<br>|10-700<br>Log<br>56_._8+2_._6<br>_−_2_._2<br>0.05-1<br>Log<br>0_._456+0_._012<br>_−_0_._011<br>100-1000<br>Log<br>351+25<br>_−_19<br>0.001-1<br>Log<br>0_._001+0_._002<br>_−_0_._001<br>671.8-672.2<br>Uniform<br>671_._9833+0_._0047<br>_−_0_._0058<br>20-70<br>Sin<br>36_._5+2_._6<br>_−_2_._9<br>10-100<br>Uniform<br>28_._9_ ±_ 1_._1<br>-0.1-0.1<br>Uniform<br>0_._03_ ±_ 0_._003<br>-0.1-0.1<br>Uniform<br>_−_0_._001_ ±_ 0_._003<br>25-35<br>Log<br>28_._1+0_._8<br>_−_0_._7<br>|
|Continuum ra ofset [arcsec]<br>Continuum dec ofset [arcsec]<br>Continuum fux fwhm [arcsec]<br>Continuum fux density [mJy]|0<br>[fxed]<br>0<br>[fxed]<br>0.22<br>[fxed]<br>52.7<br>[fxed]|



_a_ offset from continuum center



for j1000, which indicates that it is a dynamically cold
disk. This places it squarely within the range predicted
by the Illustris tng50 simulation (Pillepich et al. 2019)
in terms of dynamical evolution as presented in Fig. 3
of Rizzo et al. (2020). However, other galaxies are presented there too which are cold disks at much earlier
times ( _z ∼_ 4).


3.3. _PDR model_

Assuming that the [Cii] and [Oi] lines and fir continuum arise from pdrs, we use the Pdr Toolbox
(pdrt; Kaufman et al. 2006; Pound & Wolfire 2008,
2011, 2023) to estimate the fir fine-structure line intensitiesproducedbygaswithdensity _n_ andincidentfar-uv
_G_ . The `wk2020` models included in pdrt make calflux [3]
culations to a depth equal to visual extinction A _V_ = 7
and Solar metallicity (Z = 1), and the model fuv field
strengths and gas densities are plotted as a grid in Fig. 6
as functions of two diagnostic line ratios: [Cii] 158
μm/[Oi] 63 μm and ([Oi] 63 μm + [Cii] 158 μm)/fir.
Tocomparethismodelwithourobservations,westart
with our observed [Cii] luminosity, our derived _L_ _FIR_
from sed modeling, and the [Oi] 63 μm luminosity =
(9 _._ 8 _±_ 3 _._ 7) _·_ 10 [9] L _⊙_, and apply corrections for ionized
gas and optical depth. About 25% of the observed [Cii]
line radiation likely arises from ionized gas (Oberst et al.
2006), so we multiply the [Cii] line luminosity by a fac

3 Following Tielens & Hollenbach (1985) we define _G_ 0 as the Habing
flux ( _G_ 0 = 1 _._ 6 _×_ 10 _[−]_ [6] W m _[−]_ [2] or 1 _._ 3 _×_ 10 _[−]_ [7] W m _[−]_ [2] sr _[−]_ [1] in intensity
units) and express the far-uv flux _G_ in terms of _G_ 0 .



tor of 3 _/_ 4. If the emitting clouds are externally heated
spherical clouds, the observed optically thin [Cii] line
and fir continuum will arrive from the entire clouds’
surfaces, with area 4 _πr_ [2], while the optically thick [Oi]
63 μm line will only arrive from a surface of area _∼_ _πr_ [2] .
We therefore multiply the observed [Oi] line by a factor of 2 since something between a factor of 1 and 4 of
After
the [Oi] line flux will be blocked from our view.
applying these corrections, we plot the diagnostic line
ratios for j1000 and all other galaxies with the same line
observations available in the literature in Fig. 6.
In Fig. 7 we show a different view of the pdrt model
for sdss j1000, where the parameter space of _G_ and _n_
is shown shaded with the allowed regions for different
line ratios. The solution at _n_ = 6 _×_ 10 [3] cm _[−]_ [3], and
uv field _G_ = 5 _×_ 10 [3] _G_ 0 corresponds with the value
shown in Fig. 6. Focusing only on [Oi], [Cii], and fir,
another solution also exists, with _n_ = 1 _._ 5 _×_ 10 [5] cm _[−]_ [3],
_G_ = 3 _G_ 0, and distinguishing between the two involves
thoughts about filling factors. Dust is heated by nearby
starlightandre-radiatesitsenergyinthefircontinuum.
Typically half the starlight that heats this dust is in the
fuv, so that a beam filling factor of unity would have
fir intensity matching half the fuv intensity: _I_ _FIR_ =
_L_ _FIR_ _/_ (4 _πd_ [2] Ω _source_ ) = 1 _._ 9 _×_ 10 _[−]_ [3] W m [2] sr _[−]_ [1] = 2 _G_ _⇒_ _G_ =
1 _._ 5 _×_ 10 [4] _G_ 0 . The low _G_ solution requires a filling factor
of 5000, which is implausible. The high _G_ solution has
a much more plausible beam filling factor of 4.
Looking at the CO lines plotted in Fig. 7 paints a
somewhat different picture. The ratios of different CO
transitions agree with the [Oi], [Cii], and fir solution

8 Rooney et al.





10 [6]


10 [5]





10 [0]


10 _[−]_ [1]








|l|og(|n)|log(|G0)|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|~~[~~|~~cm~~|~~_−_3~~<br>2|~~]~~<br>.0<br>~~[Ha~~|~~bing]~~<br>2.0|||||||
|||3.<br>4<br>~~5.~~|0<br>.0<br>~~0~~|3.0<br>4.0<br>~~5.0~~|||||||
||||||||||||
||||||||||||
||||||||||||
|||L<br>~~S~~|IRGS<br>~~b-LIRGS~~|_z <_ 2<br>~~_ >_ 2~~|||||||
|||U|LIRGS|~~_z_ ~~<br>Low-z QSO|||||||
|||D|warf|<br>J1000|||||||



10 _[−]_ [4] 10 _[−]_ [3] 10 _[−]_ [2] 10 _[−]_ [1]


([Oi] 63 μm + [Cii] 158 μm)/I _FIR_


**Figure 6.** Here we plot the pdr parameter space ( _G_, _n_ ) from
Pound & Wolfire (2023) for two fir line diagnostics, the [Cii]
158 μm/[Oi] 63 μm ratio and [Oi] 63 μm + [Cii] 158 μm
to fir ratio. The two spectral lines account for most of the
gas cooling. For comparison, we plot observations of j1000
(purple) and all other galaxies with [Cii], [Oi], and fir observations that we could reasonably account for in the literature: Zhang et al. (2018); Fern´andez Aranda et al. (2024);
Rigopoulou et al. (2018); Brisbin et al. (2015); Zhao et al.
(2016); D´ıaz-Santos et al. (2017); Brauher et al. (2008); and
Ishii et al. (2024). Line fluxes for the plotted galaxies have been
corrected for ionized gas and optical depth by multiplying the

[Cii] flux by 0.75 and the [Oi] flux by 2 (see text of §3.3).
Representative uncertainties can be assumed to be 0.3 dex for
points not presented with error bars.


to within a couple _σ_, but the [Cii]/CO ratio intersects
with the others at a in
very different point parameter
which indicates an excess of CO line emission.
space,
This excess could be explained in a couple of different
ways. In the standard pdr paradigm (which is what
we adopt for the remainder of this work), [Oi], [Cii],
and fir emission are predominantly from the pdr itself, while the CO emission could arise from molecular clouds not associated with pdrs in addition to those
which are (Mashian et al. 2015) or could additionally be
excited by shocks. Alternatively, the [Oi] or CO emission could arise from xdrs in addition to pdrs (van der
Werf et al. 2010). We adopt the explanation that the CO
emission comes from cooler, higher-density parts of the
molecular clouds, but distinguishing between these scenarios requires additional observations.


3.4. _[C_ ii _]/FIR Map_
Our spatially-resolved observations of sdss j1000 allow us to produce a map of the [Cii]/fir ratio. By
assuming a constant dust temperature throughout the
source, we create a map of the spatial distribution of the
total fir luminosity of the galaxy. Next, we combine
this with our [Cii] luminosity map to produce the ratio
map. Wemasktheimagebyincludingonlypixelsthatlie



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [1] 10 [2] 10 [3] 10 [4] 10 [5] 10 [6] 10 [7]


n [cm _[−]_ [3] ]


**Figure 7.** Pdrt (Pound & Wolfire 2023) model showing regions in ( _G_, _n_ ) parameter space allowed by ratios of the two
fine-structure line luminosities and _L_ _FIR_ we have observed, and
CO luminosity from Aravena et al. (2008). The disagreement between ratios involving CO (pink, brown, orange) and
those involving only fine-structure lines and _L_ _FIR_ (blue and
green) could have several explanations (see text), but distinguishing between them would require resolved observations
of CO in this source. In this paper we adopt the solution at
_n_ = 6 _×_ 10 [3] cm _[−]_ [3], and _G_ = 5 _×_ 10 [3] _G_ 0, with uncertainties
_∼_ 0 _._ 3 dex.


in the contiguous regions around the two sources where
the [Cii] luminosity and fir luminosity remain above
1 _._ 3 _·_ 10 [8] L _⊙_ /px and 5 _·_ 10 [10] L _⊙_ /px respectively, which correspond to 1 _σ_ thresholds. Using our values from pdrt
_n_ = 10 [4] cm _[−]_ [3]
and assuming a constant density we produce the of far-uv incident on the
map flux galaxy’s
pdrs shown in Fig. 8.
Much has been said about the “[Cii] deficit”, where
the [Cii] line luminosity decreases as a function of farir luminosity, anda variety of models, somerather complex, have been proposed to explain the deficit. The simplest way to understand the [Cii] deficit, however, is by
the physics of pdrs: simply put, the efficiency of line
production is reduced as the strength of the fuv field
goes up. As we will show, our spatially resolved observations of the [Cii]/fir ratio (Fig. 9) are in clear agreement with this idea.
In Fig. 9, we plot the [Cii]/fir ratio in the various
beams across sdss j1000 against the far-IR flux scaled to
sfr surface density Σ _SFR_ using the relationship of Ken

Resolved ALMA Study of SDSS J1000 9



2 _[◦]_ 08 _[′]_ 23 _._ 0 _[′′]_


22 _._ 5 _[′′]_


22 _._ 0 _[′′]_


21 _._ 5 _[′′]_


10 [h] 00 [m] 38 _._ 05 [s] 38 _._ 00 [s] 37 _._ 95 [s] 37 _._ 90 [s]


RA (J2000)



10 _._ 0


7 _._ 5


5 _._ 0


2 _._ 5







**Figure 8.** Spatially resolved map of the far-uv field strength
_G_ in sdss j1000, derived from the [Cii]/fir ratio using the
Pound & Wolfire (2023) models. We assume a constant gas
density of _n_ = 10 [4] cm _[−]_ [3] throughout the galaxy, but this choice
has little effect on the plot given that the [Cii]/fir ratio is insensitive to density (Stacey et al. 2010). Superimposed are restframe 158 μm continuum contours, the same as Fig. 3. The
Almabeamsizeisshowninthelower-leftcornerinblack. Values of _G_ correspond inversely to the raw value of the [Cii]/fir
ratio as shown by the solid blue line in Fig. 9.


nicutt (1998):


SFR [M _⊙_ yr _[−]_ [1] ] = 1 _._ 7 _·_ 10 _[−]_ [10] L FIR [L _⊙_ ]


our resolved measurements we a blue
Alongside plot
line showing the predicted [Cii]/fir for a given _G_ from
Pound & Wolfire (2023), scaled to fir by the relationship in Kaufman et al. (1999). It is immediately apparent that the slope of the theoretical line matches the
slope of the observed ratios from many resolved galaxies.
Morequantitatively, Rybaketal. (2020a)and Lamarche
et al. (2018) determined power-law slopes of _−_ 0 _._ 75 and
_−_ 0 _._ 7 for sdp.81 and sdp.11 respectively. We find that
sdss j1000 has a power-law slope of _−_ 0 _._ 61 _±_ 0 _._ 08, and
Pound & Wolfire (2023)’s pdr model grids (which assume a plane-parallel geometry) have a power-law slope
of _−_ 0 _._ 80 _±_ 0 _._ 05, indicating that j1000 and the other
resolved galaxies have a [Cii] _excess_, not deficit. The
horizontal offset between the model value and the observed relationship is simply the area filling factor of the
source, since increasing filling factor increases fir luminosity without changing any ratios. An adjustment for
the filling factor ( _ϕ_ _A_ = 4 _._ 2, dotted blue line) shows excellent agreement with the data, making a compelling
argument that the [Cii] emission is dominated by pdrs,
and the dependence of [Cii] emission on fir flux is explained simply by the physics of the pdr. There are two
effects in the details of pdr models that predict a reduction in the [Cii] to fir continuum luminosity ratio as
the strength of the fuv field grows. First, in the regime
ofveryintensefuvfields, inparticular when _G/n_ islarge,



|102 103 104 105 G [Habing, ΦA=1]|Col2|104 105 =1]|
|---|---|---|
|108<br>109<br>1010<br>1011<br>1012<br>F_FIR_ [L_⊙_kpc_−_2]<br>10_−_1<br>100<br>101<br>102<br>103<br>Σ_SFR_ [M_⊙_yr_−_1 kpc_−_2]<br>10_−_4<br>10_−_3<br>10_−_2<br>L_CII_/L_FIR_<br>Filli~~ng Factor~~<br>GOALS<br>High-z<br>Rybak+ 2020<br>Lamarche+ 2018<br>Rybak+ 2019<br>Smith+ 2017<br>Gullberg+ 2018<br>Litke+ 2019<br>Our Model<br>This work|108<br>109<br>1010<br>1011<br>1012<br>F_FIR_ [L_⊙_kpc_−_2]<br>10_−_1<br>100<br>101<br>102<br>103<br>Σ_SFR_ [M_⊙_yr_−_1 kpc_−_2]<br>10_−_4<br>10_−_3<br>10_−_2<br>L_CII_/L_FIR_<br>Filli~~ng Factor~~<br>GOALS<br>High-z<br>Rybak+ 2020<br>Lamarche+ 2018<br>Rybak+ 2019<br>Smith+ 2017<br>Gullberg+ 2018<br>Litke+ 2019<br>Our Model<br>This work|1011<br>1012<br>2]|
|108<br>109<br>1010<br>1011<br>1012<br>F_FIR_ [L_⊙_kpc_−_2]<br>10_−_1<br>100<br>101<br>102<br>103<br>Σ_SFR_ [M_⊙_yr_−_1 kpc_−_2]<br>10_−_4<br>10_−_3<br>10_−_2<br>L_CII_/L_FIR_<br>Filli~~ng Factor~~<br>GOALS<br>High-z<br>Rybak+ 2020<br>Lamarche+ 2018<br>Rybak+ 2019<br>Smith+ 2017<br>Gullberg+ 2018<br>Litke+ 2019<br>Our Model<br>This work|Filli~~ng Factor~~<br>GOALS<br>High-z||
|108<br>109<br>1010<br>1011<br>1012<br>F_FIR_ [L_⊙_kpc_−_2]<br>10_−_1<br>100<br>101<br>102<br>103<br>Σ_SFR_ [M_⊙_yr_−_1 kpc_−_2]<br>10_−_4<br>10_−_3<br>10_−_2<br>L_CII_/L_FIR_<br>Filli~~ng Factor~~<br>GOALS<br>High-z<br>Rybak+ 2020<br>Lamarche+ 2018<br>Rybak+ 2019<br>Smith+ 2017<br>Gullberg+ 2018<br>Litke+ 2019<br>Our Model<br>This work|Rybak+ 2020<br>Lamarche+ 201<br>Rybak+ 2019<br>Smith+ 2017<br>Gullberg+ 2018<br>Litke+ 2019<br>Our Model<br>This work|Rybak+ 2020<br>Lamarche+ 201<br>Rybak+ 2019<br>Smith+ 2017<br>Gullberg+ 2018<br>Litke+ 2019<br>Our Model<br>This work|


**Figure** **9.** Resolved [Cii]/fir measurements in sdss j1000
(large violet circles) are compared to similar resolved measurements of other high-z targets from Rybak et al. (2020a);
Lamarche et al. (2018); Rybak et al. (2019); Gullberg et al.
(2018); Litke et al. (2019), and unresolved measurements from
goals (D´ıaz-Santos et al. 2017) and unresolved high-z observations presented in Smith et al. (2017). Each data point presented here for sdss j1000 represents one independent beam
from our Alma data. Also shown are the corresponding fir
flux values and far-uv flux values to the sfr surface density
on the x-axis. fir is scaled to Σ _SFR_ using the relationship of
Kennicutt (1998) and to _G_ using the relationship of Kaufman
et al. (1999). The model in solid blue is the pdr toolbox model
from Pound & Wolfire (2023), relating _G_ to [Cii]/fir asuming _n_ = 10 [4] cm _[−]_ [3] and the dotted line is the same model shifted
by the filling factor _ϕ_ _A_ = 4 _._ 2.


thelargechargeonagrainwillincreasesothattheenergy
lost by a photo-electron ejected from such a grain decreases, thereby decreasing the gas heating rate. Second,
since the penetration of fuv photons capable of ionizing carbon to form C+ is limited by dust extinction, the
emitting column of C+ grows logarithmically with fuv
flux. In contrast, the optically thin dust emission grows
linearly with fuv so that the line to continuum ratio decreases with increasing fuv field strength (Wolfire et al.
1990; Stacey et al. 1991, 2010). The excellent fit of the
data to pdr models is very strong evidence that the socalled “[Cii] deficit” is the expected result of standard
pdr physics.
The differences in slope from this work to Smith
et al. (2017) and D´ıaz-Santos et al. (2013) in resolved
star-forming galaxies and local ulirgs respectively can
likely be attributed to geometry. Ferkinhoff (2015) and
Herrera-Camus et al. (2018) show that the expected dependence of [Cii]/fir on Σ SFR changes based on geom

10 Rooney et al.



etry and total Σ SFR . In geometries with pdrs closely associated to individual ionizing sources, the power-law
slope is consistent with that of local ulirgs at _−_ 0 _._ 26,
but this relation steepens at Σ FIR _>_ 3 _·_ 10 [10] L _⊙_ kpc _[−]_ [2] or
when the geometry is that of a uniform interstellar radiation field irradiating molecular clouds with pdrs at the
interface. It is conceivable that galaxies with more extreme Σ FIR are more likely to take on the second geometry as uv fields become stronger throughout the source.


4. DISCUSSION

4.1.
_Extended flux: Resolved Out Emission or Low_
_Surface Brightness?_
The Zeus-1 detection of [Cii] from sdss j1000
(Stacey et al. 2010) found significantly higher line flux
than detected in our Alma imaging (78 _±_ 18 Jy km s _[−]_ [1]
and 37 _._ 7 _±_ 3 _._ 3 Jy km s _[−]_ [1], respectively). The values are
nearly consistent if we take into account calibration uncertainties in the Zeus-1 data and its modest statistical
significance. If we take the flux discrepancy at face value,
it could also be explained by the presence of a diffuse
component to the [Cii] emission that is detected within
the11 _[′′]_ _._ 5Zeus-1/csobeambuteitherresolvedoutbythe
maximum recoverable scale of our Alma observations
or at a surface brightness that is simply too low to be recovered from the noise in the Alma map.
Using new observational constraints from nircam
imaging,wecanestimatetheexpectedsurfacebrightness
of the “missing” flux. It is reasonable to assume that the
gas brightness distribution is traced by rest-frame stellar
emission seen in the nircam imaging, which is clearly
distributed on scales of _∼_ 2 _[′′]_
. If we assume the extra flux
detected by Zeus-1 is spread uniformly on a 2 _[′′]_ diameter
disk (84 beams), the expected surface brightness would
be 0.3 Jy km s _[−]_ [1] beam _[−]_ [1] . This is only 40% of the rms
value of the line image: 0.7 Jy km s _[−]_ [1] beam _[−]_ [1] .
This already low detectability is further compounded
by the maximum recoverable scale (mrs) of our Alma
observations. The mrs is the size of a uniform disk
for which observations would detect 10% of the
flux
(Alma technical handbook cycle 4), and response scales
as _∝_ exp( _θ_ [2] _L_ [2] min [) (Where] _[ L]_ [min] [ is the minimum baseline]
length; Wilner &Welch 1994). As mentionedin §2.1 the
mrss for our observations were 1 _[′′]_ _._ 3 and 2 _[′′]_ _._ 0 in the two
execution blocks, and in the final combined image it was
1 _[′′]_ _._ 7. So in the most optimistic scenario with mrs=2 _[′′]_ _._ 0,
much of any putative emission at 2 _[′′]_ scales would be resolvedout. Forcomparison, a2 _[′′]_ circleisdrawnin Fig.2.


4.2.
_Confirmation of Physically Associated Satellite_

deWe confirmed the redshift of the satellite galaxy,
tecting its [Cii] line at redshift _z_ = 1 _._ 82821 _±_ 0 _._ 00040,



consistent with the center velocity of the main component (1 _._ 82825 _±_ 0 _._ 00002). This indicates the two
components are physically associated, and allows us to
estimate a merger timescale. If we assume the line of
sight difference between the two sources is small and calculate _t_ _dyn_ using only the transverse distance, 15 _._ 7 kpc,
and the mass of the system derived by Liu et al. (2019),
1 _._ 5 _·_ 10 [11] M _⊙_, we calculate _t_ _dyn_ _∼_ 400 Myr. Merger
timescales are estimated to be similar to the dynamical timescales within a factor of a few (Solanes et al.
2018; Boylan-Kolchin et al. 2008), indicating a possible
merger in ≳ 400 Myr.
Further evidence of an ongoing interaction between
the main source and satellite is provided by recent imagingofthesourcebyjwst(see Fig.2). Herebothabridge
feature between the two systems and an approximately
20 kpc tidal tail streaming away from the satellite galaxy
are apparent, confirming that the j1000 pair are interacting.
Additionally the satellite’s position relative to j1000 is
approximately perpendicular to the axis of rotation of
j1000 (see the moment-1 map in Fig. 3, bottom), which
could be an indication that the companion was accreted
from the same strand of the Cosmic Web that formed
the main galaxy.


4.3. _Neutral Gas Cloud Parameters: cloud radius and_
_numbers, volume, and area filling factors_
Molecular clouds are not singular units. They are
complex entities fractured by the effects of star formation including the turbulent outflows from young stellar objects and winds and dissociating far-UV flux from
high mass stars. It is challenging to directly discern
the physical properties of molecular cloud distributions
such as cloud size and filling factor in galaxies both near
and far. This is because the common tracers of molecular clouds are the low-excitation CO lines in the millimeter wave regime where spatial resolution is modest
andbecausetheCOlinesareopticallythicksothatcomplex internal structures within cloud complexes are well
masked. Initial CO surveys of the Galaxy suggested sizescales of order 4 – 40 pc (Solomon et al. 1987), but later
observationsinthemuchmoreopticallythin [13] COlines
have shown that typical cloud sizes are much smaller, of
the order 2 to 6 pc (Heyer et al. 2009). In external galaxies systematic surveys do not reach spatial resolutions
below 10 pc, even for our neighbor m31, where Submillimeter Array (sma) observations in CO(2-1) only reach
spatial resolutions of 14 pc (Lada et al. 2024). High spatial resolution is much more difficult to obtain for high
redshift systems where even for lensed galaxies like the

Resolved ALMA Study of SDSS J1000 11



“Cosmic Snake” the best linear resolution obtained is
30 pc (Dessauges-Zavadsky et al. 2019).
Fortunately, much as for stars, where their diameters
are measured through a combination of physics (the
radiation laws) and observations (parallax), the size of
molecular clouds can be derived through a combination
of astrophysics (pdr models) and observations ([Cii]
and CO line, and far-ir continuum intensities). In
the following, we reintroduce this astrophysically based
method that was demonstrated et al.
first by Wolfire
(1990).
In §3.3 we used the observed pdr line fluxes and far-ir
continuum flux and their ratios within a pdr paradigm
to derive the overall properties of the emitting medium
including gas density _n_ _H_ and fuv flux _G_ impinging on
the emitting clouds (Fig. 6). Comparing pdr parameters to the observed [Cii] line intensity we can derive
important cloud parameters including cloud size, numbers of clouds and the volume and area factors
filling
within a toy model that assumes spherical clouds exterThe denally heated by the stellar fuv radiation field.

.
tails of this model are given in Appendix B
The key to our model is that we assume uniform density spherical clouds that are illuminated externally by
a stellar fuv radiation field of strength _G_ . The [Cii]
line arises from the molecular cloud surfaces and the
depth of the emission region is given by the pdr models, so the cloud surface area and photodissociated skin
depth Δ _r_ are determined. The CO line intensity traces
the molecular cloud mass which is proportional to the
cloud volume. Under the assumption that the pdr has
the same gas density as the molecular cloud, the line
can then be used to derive the cloud size in a
fluxes
pdr paradigm. From our pdr models above we derived
_n_ _H_ = 6 _×_ 10 [3] cm _[−]_ [3] and _G_ = 5 _×_ 10 [3] _G_ 0 . We adopt
_M_ _m_ = 4 _._ 5 _×_ 10 [10] for the total molecular gas mass in j1000
derived by Aravena et al. (2008) using a value for the observed CO intensity to molecular gas mass conversion
factor _α_ _CO_ = 0 _._ 8 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] . Using our toy
model we derive a beam filling factor _ϕ_ _A_ = 4 _._ 2, a cloud
radius, _r_ _CO_ = 3 _._ 4 pc _×_ ( _α_ _CO_ _/_ 0 _._ 8), and a [Cii] line emitting shell depth of Δ _r_ _∼_ 4 _._ 0 _×_ 10 [21] cm _[−]_ [2] _/n_ _H_ = 0 _._ 22
pc. There are _∼_ 10 [6] clouds in an emission region of volume 2 _._ 3 _×_ 10 [11] pc [3], so the cloud volume filling factor is
_ϕ_ _vol_ = 0 _._ 077%. The total mass of each individual cloud,
including the molecular core and the photodissociated
surface is 5 _._ 2 _×_ 10 [4] M _⊙_ _×_ ( _α_ _CO_ _/_ 0 _._ 8) [3] .
The cloud radius including the pdr surface is 3.5 pc
which is somewhat smaller than those inferred through
CO measurements of nearby galaxies, but of the same
order as those discerned in [13] CO surveys. This is likely
because the [Cii] line arises from cloud surfaces so that



**Table 3.** Observational parameters, parameters derived from
the pdr model in §3.3, and assumptions used for deriving the
filling factor in j1000.


Metric Value

_z_ 1.8275

_D_ _L_ 13.9 Gpc

[Cii] line flux 37 _._ 7 _±_ 3 _._ 3 Jy km s _[−]_ [1]

[Cii] luminosity (5 _._ 1 _±_ 0 _._ 4) _×_ 10 [9] L _⊙_
fir luminosity (7 _._ 2 _±_ 0 _._ 3) _×_ 10 [12] L _⊙_
sfr 1640 _±_ 80 M _⊙_ yr _[−]_ [1]

_n_ 6 _·_ 10 [3] cm _[−]_ [3] _±_ 0 _._ 3 dex
_G_ 5 _·_ 10 [3] _G_ 0 _±_ 0 _._ 3 dex
_I_ CII 10 _[−]_ [3] ergs s _[−]_ [1] cm _[−]_ [2] sr _[−]_ [1]

_R_ 0 _[′′]_ _._ 456 = 3 _._ 85 kpc
_M_ _m_ 4 _._ 5 _·_ 10 [10] M _⊙_
Ω 1 _._ 3 _·_ 10 _[−]_ [11] sr = 0 _._ 57 arcsec [2]


pdr-derived estimates are sensitive to the internal structures of molecular cloud complexes. Smaller scale structures would be expected for clouds turbulently stirred
and fractionated recent intense of star
up by episodes
formation. It is also important to note that the cloud
radius estimate from this model scales linearly with _M_ _m_,
total molecular gas mass, which includes an assumption
for the value of _α_ _CO_ .


4.4. _Detailed Analysis of Masses_
With the data discussed thus far, we can constrain
sdss j1000’s dynamical mass, stellar mass, and dust
mass, and the satellite’s stellar mass. In this section we
report these values.
First,wecalculatethedynamicalmassusingtheresults
of our disk modeling in §3.2. In general, the mass inside a certain radius is related to the rotational velocity
bying a flat rotation curve as found by the disk modeling _M_ ( _r_ ) = _[rV]_ _G_ [2] [.] [Substituting in our values, and assum-]

_−_ 1
(see §3.2.2), we find _M_ ( _r_ ) = _r ·_ 3 _._ 0 _·_ 10 [10] M _⊙_ kpc . Our
disk model finds that the fwhm of [Cii] brightness is
0 _[′′]_ _._ 45 _±_ 0 _[′′]_ _._ 04or3 _._ 8 _±_ 0 _._ 3kpc. Usingthisasaradius, weestimate a dynamical mass of (1 _._ 14 _±_ 0 _._ 10) _·_ 10 [11] M _⊙_ . This
includes inclination effects. Jwst imaging in Fig. 2 supports a much more extended source, with radius closer
to 1 _[′′]_ _._
0. If we assume that the flat rotation curve extends
totheJwstradiusof8.4kpc,thedynamicalmasswould
be _∼_ 2 _._ 5 _·_ 10 [11] M _⊙_ .
This is compatible with stellar mass estimates from
Liu et al. (2019), who finds stellar mass = 7 _._ 9 _·_ 10 [10] M _⊙_
for sdss j1000 and 7 _._ 4 _·_ 10 [10] M _⊙_ for the satellite. Given
the similarity of stellar masses between the satellite and
j1000, and Liu et al. (2019)’s estimate that the sfr in the
satelliteisatenththatofthemainsource,wecansurmise

12 Rooney et al.



that the stellar population in the satellite is much older
than that of j1000.
Ongoing intense star formation and the potential
merger would add to this already massive ( _∼_ 10 [11] M _⊙_ )
stellar inventory, supporting an argument that j1000 is
evolving to be among the most massive galaxies seen today.
In §3.1 we used our Far-IR SED to constrain the dust
massinSDSSJ1000. Wefoundadustmassof(1 _._ 4 _±_ 0 _._ 1) _·_
10 [9] M _⊙_ . This is relatively consistent with previous dust
mass estimates such as those presented by Aravena et al.
(2008).


5. SUMMARY AND OUTLOOK

Within this work, we have investigated the star formation properties of sdss j1000, an optically selected
quasaratredshift1.8275withalargemoleculargasreservoir that feeds an obscured starburst. j1000 was one of
the first galaxies at Cosmic Noon to be detected in the
158 μm [Cii] line, which inspired followup measurements of the 63 μm [Oi] line with Herschel/pacs and
imaging of the [Cii] line at better than 0 _[′′]_ _._ 2 spatial resolution with Alma. Through comparison of these data
with archival data we find:

  - The [Cii] line emission is spatially resolved. The

[Cii]velocityfieldisconsistentwithadynamically
cold rotating disk, presented to us at an inclination of _∼_ 36 _[◦]_ with a diameter _≥_ 3 _._ 8 kpc and maximum rotation velocity of 350 km/sec. Within this
radius, the enclosed mass is dominated by that of
the stellar population. The [Cii] emitting disk is
enveloped by spiral arms visible in the rest-frame
optical.


  - By comparing our [Cii] results with Herschel

[Oi] observations and archival rest frame fir continuumobservations,weshowthatthe[Cii]emission is dominated by pdrs with disk-averaged
fuv intensity _∼_ 5000 G 0 and gas density _∼_
6000 cm _[−]_ [3] .


  - Making use of the spatially resolved 158 μm rest
frame continuum as a proxy for the fir luminosity, we find that the [Cii] line to fir continuum
luminosity ratio falls off with fuv field strength
in a manner consistent with predictions of pdr
models. Thereforethisratioisagoodproxyforthe
strength of the local fuv fields, or star formation
surface density as originally proposed in Wolfire
et al. (1990) and utilized in the Stacey et al. (1991)

survey.


  - We use a simple model based on our pdr modeling results to derive typical cloud radii _r_ _co_ = 3 _._ 4 pc



_×_ ( _α_ _CO_ _/_ 0 _._ 8) and mass 4 _._ 9 _×_ 10 [4] M _⊙_ _×_ ( _α_ _CO_ _/_ 0 _._ 8) [3] in
J1000 and both are smaller than values typical for
nearby galaxies. This is likely the result of the intense star formation disrupting their natal cloud
complexes.

  - We report the spectroscopic confirmation of a
satellite galaxy within a projected distance of _∼_
16 kpc of j1000. Jwst nircam imaging reveals
both a bridge of material between the two sources
and a tidal tail feature extension for about 20 kpc
roughly the opposite direction of the connecting
bridge. We suggest that the system interaction axis
the dark matter distribumay reflect underlying
tion of the system and provide evidence of interaction.


These rare Alma Band 9 observations of a high_z_ galaxy, consisting of only 2 hrs of telescope time,
demonstrate capabilities of Alma that are seldom
achieved.


6. ACKNOWLEDGMENTS

CR thanks the National Research Council for their
generous support through grant `506872.B3587` . This
work was supported by the National Science Foundation through the following grants: `NRAO` `SOS` `1519126,`
`AST-1716229,` `AST-1910107,` `CAREER-1847892` and
`AST-2009767`, and Nasa/Usra Sofia grants `09-0185`
and `07-0209` .
Herschel is an Esa space observatory with science instruments provided by European-led Principal Investigator consortia and with important participation from
Nasa.
This makes use of the Alma data:
paper following
```
ADS/JAO.ALMA #2015.1.01362.S, #2016.1.00463.S,
```

`#2021.1.00246.S`, and `#2021.1.00705.S` . Alma is a
partnership of Eso (representing its member states),
Nsf (Usa) and Nins (Japan), together with Nrc
(Canada), Most and Asiaa (Taiwan), and Kasi (Republic of Korea), in cooperation with the Republic of
Chile. The Joint Alma Observatory is operated by eso,
Aui/Nrao and Naoj. The National Radio Astronis a of the National Science
omy Observatory facility
Foundation operated under cooperative agreement by
Associated Universities, Inc.
This work is based in part on observations made
with the Nasa/Esa/Csa James Webb Space Telescope.
The data were obtained from the Mikulski Archive for
Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under Nasa contract `NAS` `5-03127` for Jwst. These observations are as

Resolved ALMA Study of SDSS J1000 13


sociated with program `#1727` . The specific observations This research made use of Nasa’s Astrophysics Data

.
analyzed can be accessed via [doi: 10.17909/8sg7-7w28](https://doi.org/10.17909/8sg7-7w28) System Bibliographic Services.
We thank the anonymous referee for their helpful
comments which substantially improved this publication.


REFERENCES



Aravena, M., Bertoldi, F., Schinnerer, E., et al. 2008, A&A,

[491, 173, doi: 10.1051/0004-6361:200810628](http://doi.org/10.1051/0004-6361:200810628)

Atek, H., Shuntov, M., Furtak, L. J., et al. 2023, MNRAS,
[519, 1201, doi: 10.1093/mnras/stac3144](http://doi.org/10.1093/mnras/stac3144)
Bertoldi, F., Carilli, C., Aravena, M., et al. 2007, ApJS, 172,
[132, doi: 10.1086/520511](http://doi.org/10.1086/520511)
Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931,
[160, doi: 10.3847/1538-4357/ac5a4a](http://doi.org/10.3847/1538-4357/ac5a4a)
Boylan-Kolchin, M., Ma, C.-P., & Quataert, E. 2008,
[MNRAS, 383, 93, doi: 10.1111/j.1365-2966.2007.12530.x](http://doi.org/10.1111/j.1365-2966.2007.12530.x)
Brauher, J. R., Dale, D. A., & Helou, G. 2008, ApJS, 178,
[280, doi: 10.1086/590249](http://doi.org/10.1086/590249)
Brisbin, D., Ferkinhoff, C., Nikola, T., et al. 2015, ApJ, 799,
[13, doi: 10.1088/0004-637X/799/1/13](http://doi.org/10.1088/0004-637X/799/1/13)
Buchner, J., Georgakakis, A., Nandra, K., et al. 2014, A&A,
[564, A125, doi: 10.1051/0004-6361/201322971](http://doi.org/10.1051/0004-6361/201322971)

Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105,

[doi: 10.1146/annurev-astro-082812-140953](http://doi.org/10.1146/annurev-astro-082812-140953)

Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023,
[ApJ, 954, 31, doi: 10.3847/1538-4357/acc2bc](http://doi.org/10.3847/1538-4357/acc2bc)
Crawford, M. K., Genzel, R., Townes, C. H., & Watson,
[D. M. 1985, ApJ, 291, 755, doi: 10.1086/163113](http://doi.org/10.1086/163113)
Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023,
Nature Astronomy, 7, 622,
[doi: 10.1038/s41550-023-01918-w](http://doi.org/10.1038/s41550-023-01918-w)

Dale, D. A., & Helou, G. 2002, ApJ, 576, 159,
[doi: 10.1086/341632](http://doi.org/10.1086/341632)

Davis, T. A., Alatalo, K., Bureau, M., et al. 2013, MNRAS,

[429, 534, doi: 10.1093/mnras/sts353](http://doi.org/10.1093/mnras/sts353)
Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854,
[97, doi: 10.3847/1538-4357/aaa5aa](http://doi.org/10.3847/1538-4357/aaa5aa)
Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019,
Nature Astronomy, 3, 1115,
[doi: 10.1038/s41550-019-0874-0](http://doi.org/10.1038/s41550-019-0874-0)

D´ıaz-Santos, T., Armus, L., Charmandaris, V., et al. 2013,
[ApJ, 774, 68, doi: 10.1088/0004-637X/774/1/68](http://doi.org/10.1088/0004-637X/774/1/68)
D´ıaz-Santos, T., Armus, L., Charmandaris, V., et al. 2017,
[ApJ, 846, 32, doi: 10.3847/1538-4357/aa81d7](http://doi.org/10.3847/1538-4357/aa81d7)
Ferkinhoff, C. 2015, in American Astronomical Society
Meeting Abstracts, Vol. 225, American Astronomical
Society Meeting Abstracts #225, 141.19



Ferkinhoff, C., Brisbin, D., Parshley, S., et al. 2014, ApJ, 780,
[142, doi: 10.1088/0004-637X/780/2/142](http://doi.org/10.1088/0004-637X/780/2/142)
Fern´andez Aranda, R., D´ıaz Santos, T., Hatziminaoglou, E.,
et al. 2024, A&A, 682, A166,

[doi: 10.1051/0004-6361/202347869](http://doi.org/10.1051/0004-6361/202347869)

Feroz, F., Hobson, M. P., & Bridges, M. 2009, MNRAS,
[398, 1601, doi: 10.1111/j.1365-2966.2009.14548.x](http://doi.org/10.1111/j.1365-2966.2009.14548.x)
Frias Castillo, M., Rybak, M., Hodge, J., et al. 2024, A&A,
[683, A211, doi: 10.1051/0004-6361/202347596](http://doi.org/10.1051/0004-6361/202347596)
Gullberg, B., De Breuck, C., Vieira, J. D., et al. 2015,
[MNRAS, 449, 2883, doi: 10.1093/mnras/stv372](http://doi.org/10.1093/mnras/stv372)
Gullberg, B., Swinbank, A. M., Smail, I., et al. 2018, ApJ,
[859, 12, doi: 10.3847/1538-4357/aabe8c](http://doi.org/10.3847/1538-4357/aabe8c)
Hailey-Dunsheath, S., Nikola, T., Stacey, G. J., et al. 2010,
[ApJL, 714, L162, doi: 10.1088/2041-8205/714/1/L162](http://doi.org/10.1088/2041-8205/714/1/L162)
Herrera-Camus, R., Sturm, E., Graci´a-Carpio, J., et al. 2018,
[ApJ, 861, 95, doi: 10.3847/1538-4357/aac0f9](http://doi.org/10.3847/1538-4357/aac0f9)
Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009,
[ApJ, 699, 1092, doi: 10.1088/0004-637X/699/2/1092](http://doi.org/10.1088/0004-637X/699/2/1092)
Houck, J. R., Schneider, D. P., Danielson, G. E., et al. 1985,
[ApJL, 290, L5, doi: 10.1086/184431](http://doi.org/10.1086/184431)
Ishii, N., Hashimoto, T., Ferkinhoff, C., et al. 2024, arXiv
e-prints, arXiv:2408.09944,
[doi: 10.48550/arXiv.2408.09944](http://doi.org/10.48550/arXiv.2408.09944)
Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006,
[ApJ, 644, 283, doi: 10.1086/503596](http://doi.org/10.1086/503596)
Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., &
[Luhman, M. L. 1999, ApJ, 527, 795, doi: 10.1086/308102](http://doi.org/10.1086/308102)
Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189,
[doi: 10.1146/annurev.astro.36.1.189](http://doi.org/10.1146/annurev.astro.36.1.189)

Lada, C. J., Forbrich, J., Petitpas, G., & Viaene, S. 2024, ApJ,
[966, 193, doi: 10.3847/1538-4357/ad38bf](http://doi.org/10.3847/1538-4357/ad38bf)
Lamarche, C., Verma, A., Vishwas, A., et al. 2018, ApJ, 867,
[140, doi: 10.3847/1538-4357/aae394](http://doi.org/10.3847/1538-4357/aae394)
Litke, K. C., Marrone, D. P., Spilker, J. S., et al. 2019, ApJ,
[870, 80, doi: 10.3847/1538-4357/aaf057](http://doi.org/10.3847/1538-4357/aaf057)
Liu, D., Lang, P., Magnelli, B., et al. 2019, ApJS, 244, 40,
[doi: 10.3847/1538-4365/ab42da](http://doi.org/10.3847/1538-4365/ab42da)

Luhman, M. L., Satyapal, S., Fischer, J., et al. 1998, ApJL,
[504, L11, doi: 10.1086/311562](http://doi.org/10.1086/311562)
Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415,

[doi: 10.1146/annurev-astro-081811-125615](http://doi.org/10.1146/annurev-astro-081811-125615)

14 Rooney et al.



Malhotra, S., Kaufman, M. J., Hollenbach, D., et al. 2001,
[ApJ, 561, 766, doi: 10.1086/323046](http://doi.org/10.1086/323046)
Marton, G., Calzoletti, L., Perez Garcia, A. M., et al. 2017,
arXiv e-prints, arXiv:1705.05693.
[https://arxiv.org/abs/1705.05693](https://arxiv.org/abs/1705.05693)
Mashian, N., Sturm, E., Sternberg, A., et al. 2015, ApJ, 802,
[81, doi: 10.1088/0004-637X/802/2/81](http://doi.org/10.1088/0004-637X/802/2/81)
McKinney, J., Pope, A., Armus, L., et al. 2020, ApJ, 892, 119,
[doi: 10.3847/1538-4357/ab77b9](http://doi.org/10.3847/1538-4357/ab77b9)

McMullin, J. P., Waters, B., Schiebel, D., Young, W., &
Golap, K. 2007, in Astronomical Society of the Pacific
Conference Series, Vol. 376, Astronomical Data Analysis
Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Oberst, T. E., Parshley, S. C., Stacey, G. J., et al. 2006, ApJL,
[652, L125, doi: 10.1086/510289](http://doi.org/10.1086/510289)
Ott, S. 2010, in Astronomical Society of the Pacific
Conference Series, Vol. 434, Astronomical Data Analysis
Software and Systems XIX, ed. Y. Mizumoto, K. I. Morita,
[& M. Ohishi, 139, doi: 10.48550/arXiv.1011.1209](http://doi.org/10.48550/arXiv.1011.1209)
Pavesi, R., Riechers, D. A., Sharon, C. E., et al. 2018, ApJ,
[861, 43, doi: 10.3847/1538-4357/aac6b6](http://doi.org/10.3847/1538-4357/aac6b6)
Perna, M., Sargent, M. T., Brusa, M., et al. 2018, A&A, 619,
[A90, doi: 10.1051/0004-6361/201833040](http://doi.org/10.1051/0004-6361/201833040)
Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS,
[490, 3196, doi: 10.1093/mnras/stz2338](http://doi.org/10.1093/mnras/stz2338)
Poglitsch, A., Waelkens, C., Geis, N., et al. 2010, A&A, 518,
[L2, doi: 10.1051/0004-6361/201014535](http://doi.org/10.1051/0004-6361/201014535)
Pound, M. W., & Wolfire, M. G. 2008, in Astronomical
Society of the Pacific Conference Series, Vol. 394,
Astronomical Data Analysis Software and Systems XVII,
ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654
Pound, M. W., & Wolfire, M. G. 2011, PDRT: Photo
Dissociation Region Toolbox, Astrophysics Source Code
Library, record ascl:1102.022. [http://ascl.net/1102.022](http://ascl.net/1102.022)
[—. 2023, AJ, 165, 25, doi: 10.3847/1538-3881/ac9b1f](http://doi.org/10.3847/1538-3881/ac9b1f)
Rigopoulou, D., Pereira-Santaella, M., Magdis, G. E., et al.
[2018, MNRAS, 473, 20, doi: 10.1093/mnras/stx2311](http://doi.org/10.1093/mnras/stx2311)

Rizzo, F., Kohandel, M., Pallottini, A., et al. 2022, A&A,
[667, A5, doi: 10.1051/0004-6361/202243582](http://doi.org/10.1051/0004-6361/202243582)
Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584,
[201, doi: 10.1038/s41586-020-2572-6](http://doi.org/10.1038/s41586-020-2572-6)
Rybak, M., Hodge, J. A., Vegetti, S., et al. 2020a, MNRAS,
[494, 5542, doi: 10.1093/mnras/staa879](http://doi.org/10.1093/mnras/staa879)
Rybak, M., Zavala, J. A., Hodge, J. A., Casey, C. M., & Werf,
P. v. d. 2020b, ApJL, 889, L11,
[doi: 10.3847/2041-8213/ab63de](http://doi.org/10.3847/2041-8213/ab63de)

Rybak, M., Calistro Rivera, G., Hodge, J. A., et al. 2019, ApJ,
[876, 112, doi: 10.3847/1538-4357/ab0e0f](http://doi.org/10.3847/1538-4357/ab0e0f)



Rybak, M., da Cunha, E., Groves, B., et al. 2021, ApJ, 909,
[130, doi: 10.3847/1538-4357/abd946](http://doi.org/10.3847/1538-4357/abd946)
Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325,
[74, doi: 10.1086/165983](http://doi.org/10.1086/165983)
Sanders, D. B., Salvato, M., Aussel, H., et al. 2007, ApJS,
[172, 86, doi: 10.1086/517885](http://doi.org/10.1086/517885)
Schaerer, D., Boone, F., Jones, T., et al. 2015, A&A, 576, L2,
[doi: 10.1051/0004-6361/201425542](http://doi.org/10.1051/0004-6361/201425542)
Schaerer, D., Ginolfi, M., B´ethermin, M., et al. 2020, A&A,
[643, A3, doi: 10.1051/0004-6361/202037617](http://doi.org/10.1051/0004-6361/202037617)

Schulz, B., Marton, G., Valtchanov, I., et al. 2017, arXiv
e-prints, arXiv:1706.00448.
[https://arxiv.org/abs/1706.00448](https://arxiv.org/abs/1706.00448)
Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1,
[doi: 10.1086/516585](http://doi.org/10.1086/516585)

Smith, J. D. T., Croxall, K., Draine, B., et al. 2017, ApJ, 834,
[5, doi: 10.3847/1538-4357/834/1/5](http://doi.org/10.3847/1538-4357/834/1/5)
Solanes, J. M., Perea, J. D., & Valent´ı-Rojas, G. 2018, A&A,
[614, A66, doi: 10.1051/0004-6361/201832855](http://doi.org/10.1051/0004-6361/201832855)
Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987,
[ApJ, 319, 730, doi: 10.1086/165493](http://doi.org/10.1086/165493)
Stacey, G. J., Geis, N., Genzel, R., et al. 1991, ApJ, 373, 423,
[doi: 10.1086/170062](http://doi.org/10.1086/170062)
Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al.
[2010, ApJ, 724, 957, doi: 10.1088/0004-637X/724/2/957](http://doi.org/10.1088/0004-637X/724/2/957)
Stacey, H. R., McKean, J. P., Robertson, N. C., et al. 2018,
[MNRAS, 476, 5075, doi: 10.1093/mnras/sty458](http://doi.org/10.1093/mnras/sty458)
Tazzari, M., Beaujean, F., & Testi, L. 2018, MNRAS, 476,
[4527, doi: 10.1093/mnras/sty409](http://doi.org/10.1093/mnras/sty409)
Tielens, A. G. G. M., & Hollenbach, D. 1985, ApJ, 291, 722,
[doi: 10.1086/163111](http://doi.org/10.1086/163111)

Umehata, H., Matsuda, Y., Tamura, Y., et al. 2017, ApJ, 834,
[doi: 10.3847/2041-8213/834/2/L16](http://doi.org/10.3847/2041-8213/834/2/L16)

Valentino, F., Daddi, E., Puglisi, A., et al. 2021, A&A, 654,
[A165, doi: 10.1051/0004-6361/202141417](http://doi.org/10.1051/0004-6361/202141417)
van der Werf, P. P., Isaak, K. G., Meijerink, R., et al. 2010,
[A&A, 518, L42, doi: 10.1051/0004-6361/201014682](http://doi.org/10.1051/0004-6361/201014682)
Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850,
[208, doi: 10.3847/1538-4357/aa94ce](http://doi.org/10.3847/1538-4357/aa94ce)
Wilner, D. J., & Welch, W. J. 1994, ApJ, 427, 898,
[doi: 10.1086/174195](http://doi.org/10.1086/174195)

Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS,
[515, 1751, doi: 10.1093/mnras/stac1905](http://doi.org/10.1093/mnras/stac1905)
Wolfire, M. G., Tielens, A. G. G. M., & Hollenbach, D. 1990,
[ApJ, 358, 116, doi: 10.1086/168966](http://doi.org/10.1086/168966)
Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481,
[1976, doi: 10.1093/mnras/sty2394](http://doi.org/10.1093/mnras/sty2394)
Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ,
[909, 165, doi: 10.3847/1538-4357/abdb27](http://doi.org/10.3847/1538-4357/abdb27)

Resolved ALMA Study of SDSS J1000 15


Zhang, Z.-Y., Ivison, R. J., George, R. D., et al. 2018,
[MNRAS, 481, 59, doi: 10.1093/mnras/sty2082](http://doi.org/10.1093/mnras/sty2082)
Zhao, Y., Yan, L., & Tsai, C.-W. 2016, ApJ, 824, 146,
[doi: 10.3847/0004-637X/824/2/146](http://doi.org/10.3847/0004-637X/824/2/146)

16 Rooney et al.


APPENDIX


A. DISK MODELING TECHNICAL ADDENDUM


A.1. _Data preparation_
It is imperative that the data weights for the observed visibilities are set correctly. To accomplish that goal, we used
the following data routines. First, `initweights` is used with the parameter `dowtsp=True` in order to generate weights
for each spectral channel. Then the casa measurement set can be exported to uvfits. [4]


A.2. _Modeling and Results_
The nested sampling routine PyMultiNest (Buchner et al. 2014; Feroz et al. 2009) was used to explore the parameter
space of the model. In each iteration of the nested sampling, KinMS (Davis et al. 2013) is used to create a model
rotating disk spectral cube in the image plane based on ten parameters. The image plane datacube is converted to
visibilities using Galario (Tazzari et al. 2018), using the same baselines as the real Alma observations to ensure that the
comparison between the model and data is as statistically robust as possible.

.
The full corner plot for our disk model is shown in Fig. 10 Note that inclination angle and maximum velocity are
strongly covariant, as expected from geometry.


A.3. _Residuals_

In Fig. 11 we show an integrated image of the UVModelDisk model and also the residuals. Residuals were calculated
`tclean` .
by subtracting the model visibilities from the data visibilities and creating a dirty image of the result with
Note that the hole in the residual is not an indication that the flux was over-predicted, because it is surrounded by an
annulus of positive flux. Instead it is merely an indication that the source shape is slightly flatter than Gaussian. During
modeling we only considered emission from the main source, not the satellite, so the satellite is visible in the residual
image (Fig. 11, right).


B. MODELING CLOUD SIZE AND EMISSION FILLING FACTORS
We describe below how the observed pdr and CO lines, and the far-ir continuum flux and their ratios are used to
derive cloud parameters within the pdr paradigm including cloud size, numbers of clouds and the volume and area
filling factors within a toy model that assumes spherical clouds externally heated by fuv flux.
We begin by deriving the beam filling factor _ϕ_ _A_ . The ratios of relevant line fluxes are used within the PDR Toolbox
to divide out beam filling factors. The raw output of the model line intensities assumes the source fills the beam, so
that the ratio of the observed line intensity to the model outputs is the beam filling factor. For a source at redshift _z_,
the beam filling factor for the [Cii] line is therefore: _ϕ_ _A_ = (1 + _z_ ) [4] ( _F_ [Cii] _/_ Ω([Cii])) _/I_ [Cii] . Here _F_ [Cii] _/_ Ω([Cii]) is the
observed intensity of the [Cii] line in a beam and _I_ [Cii] is the line intensity given in the pdrt models. The factor of
(1 + _z_ ) [4] comes from cosmological surface brightness dimming. For an optically thick line emerging from a spherical
cloud, the emitting surface area is _A_ _cloud_ = _πr_ [2] . The single surface emission would also be true for the optically thin

[Cii] line if the cloud were illuminated by a central source, so only one surface emits [Cii] line radiation. However,
if the clouds are spherical and uniformly illuminated externally by a pervasive radiation field, as one might expect for
an extended star formation region, the surface area of each cloud for the optically thin line will be four times larger:
_A_ _cloud_ = 4 _πr_ [2] . Using the observed [Cii] line flux, derived [Cii] line intensity from the pdrt models and the beam size
from Table 3 we find the beam area filling factor is: _ϕ_ _A_ = 4 _._ 2. There are typically 4 sheets of [Cii] emitting pdr gas
along each line of sight.
One may also derive the overall structure of the interstellar medium through a simple model of the ism based on
the assumption that the CO line emission arises from molecular clouds and traces the molecular cloud mass, and the
preponderance of the [Cii] line emission arises from pdrs on the surfaces of these molecular clouds (Wolfire et al.
1990). Here we make a simple model that assumes the pdr gas number density is the same as that of the molecular


4 If `WEIGHT` ~~`S`~~ `PECTRUM` in the ms was unset, the weights in the uvfits
would be equal to the weights in the MS divided by the number
of channels as explained in the casa Docs, [https://casadocs.](https://casadocs.readthedocs.io/en/stable/api/tt/casatasks.data.exportuvfits.html)
[readthedocs.io/en/stable/api/tt/casatasks.data.exportuvfits.html,](https://casadocs.readthedocs.io/en/stable/api/tt/casatasks.data.exportuvfits.html)
and therefore too small by a factor of _n_ _chan_ .

Gas sigma [km/s] = 56.81 [+2.54] 2.24


~~B~~ rightness fwhm [''] = 0.46 [+0.01] 0.01



Resolved ALMA Study of SDSS J1000 17


V max [km/s] = 351.33 [+25.43] 18.99


Velocity scale [''] = 0.00 [+0.00] 0.00


~~Vel~~ ocity center [km/s] = 24.58 [+2.04] 2.57


Inclination [ ] = 36.55 [+2.61] 2.85


Position angle [ ] = 28.91 [+1.07] 1.08


X center [''] = 0.03 [+0.00] 0.00


Y center [''] = 0.00 [+0.00] 0.00


Flux [Jy km/s] = 28.04 [+0.75] 0.68



Position angle [ ]



Gas sigma [km/s]



Brightness fwhm ['']



V max [km/s]



Velocity scale ['']



Velocity center [km/s]



Inclination [ ]



X center ['']



Y center ['']



Flux [Jy km/s]



**Figure 10.** Results from the UVModelDisk procedure. Here sdss j1000 is modeled as a rotating disk. Each panel is a histogram
of the model parameters visited by the nested sampling algorithm, which is proportional to the posterior probability of those pa
rameters.
The 2-D histograms show the covariance of different parameters, while the 1-D histograms show the total probability
distribution of that parameter. All parameters are well constrained, with the exception of the expected degeneracy between maximum circular velocity and disk inclination angle. Note also that, for the modeling procedure, the velocity zero point is set to the
center velocity of the sub-cube used for modeling, rather than the prior redshift estimate, and the velocity sign convention is reversed
due to channel ordering. This offset is 54 km s _[−]_ [1], which, when combined with the best model center velocity of _−_ 25 km s _[−]_ [1], yields
a center velocity estimate of +80 km s _[−]_ [1]

18 Rooney et al.



2 _[◦]_ 08 _[′]_ 20 _._ 0 _[′′]_


19 _._ 5 _[′′]_


19 _._ 0 _[′′]_


10 [h] 00 [m] 38 _._ 25 [s] 38 _._ 20 [s] 38 _._ 15 [s] 38 _._ 10 [s]


RA (J2000)



2 _[◦]_ 08 _[′]_ 20 _._ 0 _[′′]_


19 _._ 5 _[′′]_


19 _._ 0 _[′′]_


10 [h] 00 [m] 38 _._ 2538 [s] _._ 20 [s] 38 _._ 15 [s] 38 _._ 10 [s]


RA (J2000)



20


10


0



4


2


0


_−_ 2



**Figure 11.** [Left] Image of the best model from the UVModelDisk procedure. [Right] Dirty image of the residual visibilities from
```
                                                      tclean
```
the best-fit model. This is an image of the (data visibilities - model visibilities). Both of these images were produced using the
task in casa on visibilities exported from UVModelDisk.



cloud interior ( _n_ _H_ _∼_ _n_ _H_ 2 ), we have spherical clouds, all of which have the same molecular cloud radius, _r_, with a [Cii]
emitting pdr surface of depth Δ _r_, and they are illuminated by a uniform fuv field with strength _G_ . In such a model,
the molecular cloud mass of each cloud is: _m_ _m_ = [4] ~~3~~ _[πr]_ [3] _[·][ n]_ _[H]_ [2] _[m]_ _[H]_ [2] [and the mass of the [Cii] emitting surface layer is:]

_m_ _PDR_ = 4 _πr_ [2] Δ _r · n_ _H_ _m_ _H_, so that the molecular to pdr gas mass ratio is:



4
_m_ _m_ ~~3~~ _[πr]_ [3] _[ ·][ n]_ _[H]_ [2] _[·][ m]_ _[H]_ [2]
_m_ _PDR_ [=] 4 _πr_ [2] Δ _r · n_ _H_ _· m_ _H_ [=] 3Δ [2] _[r]_ _r_ (B1)



If we assume all the clouds are identical and all the molecular and atomic gas is in the clouds, the ratio of total
moleculargastototalatomicmassinthegalaxy _M_ _m_ _/M_ _PDR_ = _m_ _m_ _/m_ _PDR_ . Thecolumndensityofthe[Cii]emittingregion
in a pdr is related to both the pdr density and incident fuv field strength. For _n_ _H_ = 6 _×_ 10 [3] cm _[−]_ [3] and _G_ = 5 _×_ 10 [3] _G_ 0
the column density (assuming solar abundances) is _N_ _H_ = 4 _×_ 10 [21] cm _[−]_ [2] (Wolfire et al. 1990), so that Δ _r_ _∼_ 4 _._ 0 _×_ 10 [21]
cm _[−]_ [2] _/n_ _H_ = 0 _._ 22 pc, and:



_M_ _m_ ( _Mα_ _COPDR_ _/_ 0 _._ 8) = 6 _._ 0 _×_ 10 _r · n_ [21] _H_ cm _[−]_ [2] [=] � 19401



_r_
�� pc



_n_ _H_
�� cm _[−]_ [3]



(B2)
�



To highlight the dependence of the following parameters on _α_ _CO_, note that the molecular gas mass _M_ _m_ _∝_ _α_ _CO_ and
Aravena et al. (2008) used _α_ _CO_ = 0 _._ 8 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] to derive _M_ _m_ = 4 _._ 5 _×_ 10 [10] M _⊙_ . We have included a
unitless scaling factor of 1 = ( _α_ _CO_ _/_ 0 _._ 8) where _α_ _CO_ is important. From our pdr modeling, _n_ _H_ = 6 _×_ 10 [3] cm _[−]_ [3], and
using our [Cii] flux with Eq. 2 from Wolfire et al. (1990) _M_ _PDR_ _∼_ 4 _._ 4 _×_ 10 [9] M _⊙_, so that the mass ratio is: _M_ _m_ _/M_ _PDR_ =
10( _α_ _CO_ _/_ 0 _._ 8). Therefore, the radius of the CO emitting core of the cloud is: _r_ _CO_ = 3 _._ 4 pc ( _α_ _CO_ _/_ 0 _._ 8). The total cloud
radius is: _r_ _cloud_ = _r_ _CO_ + Δ _r_ = 3 _._ 6 pc (since _r_ _CO_ _≫_ Δ _r_, to good approximation _r_ _cloud_ _∝_ _α_ _CO_ ). The mass of a single cloud
core is: _m_ _m_ = 4 _π/_ 3 _r_ _CO_ [3] _[·][ n]_ _[H]_ 2 _[·][ m]_ _[H]_ 2 [= 4] _[.]_ [7] _[ ×]_ [ 10] [4] [ M] _[⊙]_ [(] _[α]_ _[CO]_ _[/]_ [0] _[.]_ [8)] [3] [.] [Including the mass in the pdr we get a total neutral gas]
mass of 5 _._ 2 _×_ 10 [4] M _⊙_ per cloud (and since _m_ _m_ _≫_ _m_ _PDR_, _m_ _tot_ _∝_ _α_ [3] _CO_ [to good approximation).]
The total number of clouds is the ratio of the total mass to the mass in a cloud: _N_ _clouds_ = (4 _._ 83 _×_ 10 [10] ) _/_ (5 _._ 2 _×_ 10 [4] ) =
9 _._ 5 _×_ 10 [5] . The [Cii] emitting region has an apparent radius of 0 _[′′]_ _._ 456, which corresponds to a physical size of 3.85 kpc
at the redshift of j1000 (z = 1.8275) so that assuming a sphere, the total volume of the emission region is 2 _._ 3 _×_ 10 [11] pc [3] .
Within this volume there are 9 _._ 5 _×_ 10 [5] clouds, each of which occupies 192 pc [3] so the volume filling factor is _ϕ_ _vol_ =
0 _._ 077%. These model parameters are in very good agreement with models for pdr geometry in unresolved systems
presented in Wolfire et al. (1990).


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[1].coordinates.evidence[1]",
  "value": "1.9 arcsec WSW from J1000",
  "failed_quote": "We confirmed the redshift of the satellite galaxy, detecting its [Cii] line at redshift _z_ = 1 _._ 82821 _±_ 0 _._ 00040, consistent with the center velocity of the main component (1 _._ 82825 _±_ 0 _._ 00002)."
 },
 {
  "path": "science.targets[1].redshift_or_distance.evidence[1]",
  "value": "z = 1.82821 ± 0.00040",
  "failed_quote": "We confirmed the redshift of the satellite galaxy, detecting its [Cii] line at redshift _z_ = 1 _._ 82821 _±_ 0 _._ 00040, consistent with the center velocity of the main component (1 _._ 82825 _±_ 0 _._ 00002)."
 },
 {
  "path": "science.targets[1].distance_source.evidence[1]",
  "value": "[CII] line detection in this work",
  "failed_quote": "We confirmed the redshift of the satellite galaxy, detecting its [Cii] line at redshift _z_ = 1 _._ 82821 _±_ 0 _._ 00040, consistent with the center velocity of the main component (1 _._ 82825 _±_ 0 _._ 00002)."
 },
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "0.20 × 0.17 arcsec (1.7 × 1.4 kpc) for line; 0.19 × 0.16 arcsec (1.6 × 1.4 kpc) for continuum",
  "failed_quote": "The data were imaged with the same pixel size as above using Briggs weighting with a robustness parameter 0.5, resulting in a synthesized beam size of 0 _[′′]_ _._ 19 _×_ 0 _[′′]_ _._ 16 with position angle 55°."
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[1]",
  "value": "PDR Toolbox (PDRT) wk2020 models (A_V = 7, Solar metallicity Z = 1)",
  "failed_quote": "The `wk2020` models included in pdrt make calculations to a depth equal to visual extinction A _V_ = 7 and Solar metallicity (Z = 1)"
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "0.20 × 0.17 arcsec, PA 55° (line cube); 0.19 × 0.16 arcsec, PA 55° (continuum)",
  "failed_quote": "resulting in a synthesized beam size of 0 _[′′]_ _._ 19 _×_ 0 _[′′]_ _._ 16 with position angle 55°."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "UVModelDisk kinematic disk modeling routine in the visibility plane",
  "failed_quote": "To investigate this further, we use the UVModelDisk routine from Pavesi et al. (2018) to model j1000 as a rotating disk."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "dowtsp=True; fixed continuum parameters (RA offset 0, Dec offset 0, FWHM 0.22 arcsec, flux density 52.7 mJy); 10 varied disk parameters with priors in Table 2",
  "failed_quote": "Continuum ra ofset [arcsec] 0 [fxed] Continuum dec ofset [arcsec] 0 [fxed] Continuum fux fwhm [arcsec] 0.22 [fxed] Continuum fux density [mJy] 52.7 [fxed]"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[1]",
  "value": "2D Gaussian spatial brightness profile for disk and continuum; arctan asymptotic rotation curve; constant continuum in frequency; flat rotation curve M(r) = r V^2 / G for dynamical mass",
  "failed_quote": "Notice that UVModelDisk parameterizes the velocity curve using the asymptotic function _v_ ( _r_ ) = [2] _π_ _[v]_ _[max]_ [ arctan]  _r_ 0 _r_ _,v_ "
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "wk2020 model grid (A_V = 7, Z = 1); 1σ pixel masks at L_[CII] > 1.3 × 10^8 L_sun/px and L_FIR > 5 × 10^10 L_sun/px; fixed n = 10^4 cm^-3 for resolved G map",
  "failed_quote": "The `wk2020` models included in pdrt make calculations to a depth equal to visual extinction A _V_ = 7 and Solar metallicity (Z = 1)"
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "wk2020 model grid (A_V = 7, Z = 1); 1σ pixel masks at L_[CII] > 1.3 × 10^8 L_sun/px and L_FIR > 5 × 10^10 L_sun/px; fixed n = 10^4 cm^-3 for resolved G map",
  "failed_quote": "Wemasktheimagebyincludingonlypixelsthatlie in the contiguous regions around the two sources where the [Cii] luminosity and fir luminosity remain above 1 _._ 3 _·_ 10 [8] L _⊙_ /px and 5 _·_ 10 [10] L _⊙_ /px respectively, which correspond to 1 _σ_ thresholds. Using our values from pdrt _n_ = 10 [4] cm _[−]_ [3] and assuming a constant density we produce the of far-uv incident on the map flux galaxy’s pdrs shown in Fig. 8."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "[C II] luminosity multiplied by 3/4 (25% ionized gas contribution); [O I] 63 μm luminosity multiplied by 2 (optically thick spherical clouds); constant dust temperature across source; Kennicutt (1998) SFR-L_FIR relation",
  "failed_quote": "About 25% of the observed [Cii] line radiation likely arises from ionized gas (Oberst et al. 2006), so we multiply the [Cii] line luminosity by a factor of 3 _/_ 4."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[2]",
  "value": "[C II] luminosity multiplied by 3/4 (25% ionized gas contribution); [O I] 63 μm luminosity multiplied by 2 (optically thick spherical clouds); constant dust temperature across source; Kennicutt (1998) SFR-L_FIR relation",
  "failed_quote": "In Fig. 9, we plot the [Cii]/fir ratio in the various beams across sdss j1000 against the far-IR flux scaled to sfr surface density Σ _SFR_ using the relationship of Kennicutt (1998): SFR [M _⊙_ yr _[−]_ [1] ] = 1 _._ 7 _·_ 10 _[−]_ [10] L FIR [L _⊙_ ]"
 },
 {
  "path": "analysis_steps[5].assumptions[0].evidence[0]",
  "value": "Identical uniform-density spherical clouds illuminated externally by uniform FUV field G; n_H ~ n_H2; solar abundances",
  "failed_quote": "Here we make a simple model that assumes the pdr gas number density is the same as that of the molecular cloud interior ( _n_ _H_ _∼_ _n_ _H_ 2 ), we have spherical clouds, all of which have the same molecular cloud radius, _r_, with a [Cii] emitting pdr surface of depth Δ _r_, and they are illuminated by a uniform fuv field with strength _G_ ."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Fitting a 3D rotating disk model directly to calibrated ALMA visibilities",
  "failed_quote": "To investigate this further, we use the UVModelDisk routine from Pavesi et al. (2018) to model j1000 as a rotating disk."
 },
 {
  "path": "software[11].used_for.evidence[1]",
  "value": "Modeling PDR gas density n and incident FUV flux G from [C II], [O I], CO, and FIR observations",
  "failed_quote": "The `wk2020` models included in pdrt make calculations to a depth equal to visual extinction A _V_ = 7 and Solar metallicity (Z = 1)"
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Herschel/PACS [O I] 63 μm line flux (J1000) = 29 Jy km s^-1",
  "failed_quote": "This yields a line flux of 29 _±_ 9 Jy km s _[−]_ [1] including only statistical uncertainty, with an additional 12% calibration uncertainty"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "[C II] redshift of satellite galaxy = 1.82821 dimensionless",
  "failed_quote": "We confirmed the redshift of the satellite galaxy, detecting its [Cii] line at redshift _z_ = 1 _._ 82821 _±_ 0 _._ 00040, consistent with the center velocity of the main component (1 _._ 82825 _±_ 0 _._ 00002)."
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "Disk rotation-to-dispersion ratio (v/σ) = 6.2 dimensionless",
  "failed_quote": "We calculate _v/σ_ = 6 _._ 2 for j1000, which indicates that it is a dynamically cold disk."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "SDSS J1000 hosts a compact, dynamically cold rotating gas disk consistent with IllustrisTNG50 cosmological simulation predictions.",
  "failed_quote": "We calculate _v/σ_ = 6 _._ 2 for j1000, which indicates that it is a dynamically cold disk."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "FIR fine-structure lines like [C II] 158 μm and [O I] 63 μm are unaffected by dust extinction, have low excitation potentials (~100 K) weakly dependent on gas temperature, and together with FIR continuum constrain PDR gas physical conditions and kinematics at sub-arcsecond resolution.",
  "failed_quote": "Fir fs lines are an essential part of a complete understanding of the conditions of star formation. Firstly, they are relatively unaffected by dust extinction."
 }
]
```
