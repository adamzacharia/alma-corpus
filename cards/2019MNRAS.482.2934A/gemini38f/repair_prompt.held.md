# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019MNRAS.482.2934A\gemini38f\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–16 (2017) Preprint 22 October 2018 Compiled using MNRAS L [A] TEX style file v3.0

## _−_ **PKS B1740 517: An ALMA view of the cold gas feeding a distant** **interacting young radio galaxy**

### J. R. Allison, [1] [,] [2] [⋆] E. K. Mahony, [3] V. A. Moss, [4] [,] [5] E. M. Sadler, [2] [,] [3] [,] [5] M. T. Whiting, [3] R. F. Allison, [6] J. Bland-Hawthorn, [2] [,] [5] S. J. Curran, [7] B. H. C. Emonts, [8] C. D. P. Lagos, [2] [,] [9] R. Morganti, [4] [,] [10] G. Tremblay, [11] M. Zwaan, [12] C. S. Anderson, [13] J. D. Bunton, [3] and M. A. Voronkov [3]

1 _Sub-Dept. of Astrophysics, Department of Physics, University of Oxford, Denys Wilkinson Building, Keble Rd., Oxford, OX1 3RH, UK_
2 _ARC Centre of Excellence for All-sky Astrophysics in 3 Dimensions (ASTRO 3D)_
3 _CSIRO Astronomy and Space Science, PO Box 76, Epping NSW 1710, Australia_
4 _ASTRON, The Netherlands Institute for Radio Astronomy, Postbus 2, NL-7900 AA Dwingeloo, the Netherlands_
5 _Sydney Institute for Astronomy, School of Physics A28, University of Sydney, NSW 2006, Australia_
6 _Heilbronn Institute for Mathematical Research, Bristol, UK_
7 _School of Chemical and Physical Sciences, Victoria University of Wellington, PO Box 600, Wellington 6140, New Zealand_
8 _National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903, USA_
9 _International Centre for Radio Astronomy Research (ICRAR), M468, University of Western Australia, 35 Stirling Hwy, Crawley, WA 6009, Australia._
10 _Kapteyn Astronomical Institute, University of Groningen, Postbus 800, NL-9700 AV Groningen, the Netherlands_
11 _Harvard-Smithsonian Center for Astrophysics, 60 Garden St., Cambridge, MA 02138, USA_
12 _European Southern Observatory, Karl-Schwarzschild-Str. 2, D85748 Garching, Germany_
13 _CSIRO Astronomy and Space Science, 26 Dick Perry Avenue, Kensington WA 6151, Australia_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
Cold neutral gas is a key ingredient for growing the stellar and central black hole mass
in galaxies throughout cosmic history. We have used the Atacama Large Millimetre Array
(ALMA) to detect a rare example of redshifted [12] CO (2-1) absorption in PKS B1740 _−_ 517, a
young ( _t ∼_ 1 _._ 6 _×_ 10 [3] yr) and luminous ( _L_ 5 GHz _≈_ 6 _._ 6 _×_ 10 [43] erg s _[−]_ [1] ) radio galaxy at _z_ = 0 _._ 44
that is undergoing a tidal interaction with at least one lower-mass companion. The coincident
H I 21-cm and molecular absorption have very similar line profiles and reveal a reservoir of
cold gas ( _M_ gas _∼_ 10 [7] _−_ 10 [8] _M_ _⊙_ ), likely distributed in a disc or ring within a few kiloparsecs
of the nucleus. A separate H I component is kinematically distinct and has a very narrow line
width (∆ _v_ FWHM ≲ 5 km s _[−]_ [1] ), consistent with a single diffuse cloud of cold ( _T_ k _∼_ 100 K)
atomic gas. The [12] CO (2-1) absorption is not associated with this component, which suggests
that the cloud is either much smaller than 100 pc along our sight-line and/or located in lowmetallicity gas that was possibly tidally stripped from the companion. We argue that the gas
reservoir in PKS B1740 _−_ 517 may have accreted onto the host galaxy _∼_ 50 Myr before the
young radio AGN was triggered, but has only recently reached the nucleus. This is consistent
with the paradigm that powerful luminous radio galaxies are triggered by minor mergers and
interactions with low-mass satellites and represent a brief, possibly recurrent, active phase in
the life cycle of massive early type galaxies.


**Key words:** galaxies: evolution – galaxies: high redshift – galaxies: ISM – galaxies: structure
– radio lines: galaxies



**1** **INTRODUCTION**


It is now well established that supermassive black hole (SMBH)
mass in galaxies is strongly correlated with the properties of their


_⋆_ E-mail: james.allison@physics.ox.ac.uk


_⃝_ c 2017 The Authors



stellar bulge, namely velocity dispersion, luminosity and mass (see
Kormendy & Ho 2013 for a review). This correlation implies that
the evolution of massive galaxies is physically connected to the
growth of their SMBH. However, given the disparate scales of the
sphere of influence of the SMBH ( _∼_ 1 pc) and the stellar bulge of a
massive galaxy ( _∼_ 1 kpc), the exact physical mechanisms building

2 _J. R. Allison et al._


such a relationship are not yet clear. Models invoke both negative
(Silk & Rees 1998; Fabian 1999; King 2003) and positive feedback
from the SMBH (e.g. Ishibashi & Fabian 2012; Silk 2013), during
a particularly active phase known as quasar mode feedback, or regulation of SMBH growth by the stellar bulge itself (e.g. Umemura
2001). Alternatively, such a tight correlation between bulge size
and SMBH may simply arise indirectly as a natural consequence
of several major galaxy mergers averaged over time (e.g. Jahnke &
Macciò 2011).
It is clear that a ready supply of cold gas (kinetic temperature _T_ k ≲ 10 [4] K) is a common factor driving both stellar mass
and SMBH growth in massive galaxies. At low to intermediate redshifts the most radiatively efficient active galactic nuclei (AGN),
with high accretion rates ( _L_ bol ≳ 0 _._ 01 _L_ Edd ), [1] are typically hosted
by star-forming galaxies with a central young stellar population and
ample cold gas reservoirs (e.g. Kauffmann et al. 2003, 2007; Kauffmann & Heckman 2009; LaMassa et al. 2013). This class of luminous AGN have a rapidly evolving volume density which mirrors
that of the global star formation rate (e.g. Ueda et al. 2003; Shankar
et al. 2009). In contrast, AGN that are radiatively inefficient (i.e.
_L_ bol ≲ 0 _._ 01 _L_ Edd ), but emit synchroton radiation at radio wavelengths, are typically hosted by higher mass passive galaxies that
are globally poor in neutral gas (e.g. Best & Heckman 2012; see
Heckman & Best 2014 for a review). Regular mechanical feedback
from their radio jets (i.e. radio mode feedback) is thought to regulate the cooling of gas from the halo onto these massive galaxies
and is an important factor in quenching further growth (e.g. Nulsen
& Fabian 2000; Croton et al. 2006). At higher redshifts ( _z_ _>_ 1 _._ 5)
there is evidence for a reversal in the stellar masses of these two

populations, consistent with downsizing of SMBH growth over
cosmic time (Delvecchio et al. 2017).
Although this two-flavour model elegantly explains the observed duality of the AGN population, and the role of SMBHs in
galaxy evolution, the detailed mechanics of how the gas reaches the
nucleus are not yet well determined from observation. In the case of
radiatively efficient AGN (i.e. Seyferts, high excitation radio galaxies, and quasars), the cold gas is thought to originate from an existing cold reservoir and loses angular momentum through secular
processes and merger events (e.g. Hopkins & Hernquist 2006; Hopkins et al. 2008). For radiatively inefficient AGN (i.e. LINERS and
low excitation radio galaxies) the mechanism by which gas reaches
the centre of the galaxy is less clear. The simplest model that reproduces the observed correlation between accretion rate and radio
jet power (e.g. Allen et al. 2006; Hardcastle et al. 2007, see also
Russell et al. 2013) is that the galactic halo supplies the AGN with
hot gas via Bondi accretion (Bondi 1952). However, this simplified model assumes spherical symmetry of the accreting material
and negligible angular momentum. A more plausible scenario predicted by recent hydrodynamic simulations is that cool gas clouds
condense out of the hot halo as a result of turbulence, which in turn
is regulated by heating from the radio jets, and lose their angular
momentum through collisions close to the Bondi radius (e.g. Gaspari et al. 2013; Li & Bryan 2014). Direct evidence for this chaotic
cold accretion is seen both from filamentary gas structures in wellresolved nearby cool-core clusters (e.g. Salomé et al. 2006; Lim


1 _L_ bol is the total bolometric luminosity of the AGN and _L_ Edd is the
Eddington luminosity limit, defined as _L_ Edd = [4] _[πGm]_ _σ_ _T_ [p] _[c]_ _M_ SMBH ; where

_G_ is the gravitational constant, _m_ p is the proton mass, _c_ is the speed of
light in vacuum, _σ_ _T_ is the electron Thomson scattering cross section, and
_M_ SMBH is the SMBH mass.



et al. 2008; McNamara et al. 2014; Russell et al. 2016) and inward
radial motion of individual atomic and molecular gas clouds seen
in absorption towards radio AGN (e.g. David et al. 2014; Maccagni
et al. 2014; Tremblay et al. 2016; Maccagni et al. 2018).
The most luminous and strongly accreting active galactic nuclei are thought to be triggered by interactions between galaxies,
which efficiently remove angular momentum from the cold gas
and funnel it towards the nucleus (e.g. Sanders et al. 1988; Hopkins et al. 2008; Ellison et al. 2011), briefly, but significantly, elevating the activity above that generated by stochastic accretion of
the gas. While major mergers between gas-rich massive galaxies
are thought to trigger quasars and drive the formation of massive
spheroids throughout the history of the Universe (e.g. Treister et al.
2012), minor mergers and interactions (with a mass ratio greater
than 3) can also trigger efficient AGN accretion in otherwise passive galaxies. Nearby powerful radio galaxies that are not in the
centres of massive cool-core clusters are typically associated with
an ongoing minor merger or interaction, indicating that the gas is
efficiently accreted through tidal stripping (Ramos Almeida et al.
2011, 2012). Direct evidence of ongoing star formation and radio AGN activity triggered by a minor interaction has been seen
in the young ( _t_ _∼_ 10 [5] yr) compact steep spectrum (CSS) radio
galaxy MRC B1221 _−_ 423 (Johnston et al. 2005, 2010; Anderson
et al. 2013).
Clearly measuring the kinematics and abundance of cold neutral gas in the host galaxies of AGN is crucial to understanding their
prevalence and evolution throughout cosmological history. However, due to current limitations on the sensitivity and observable
bands of radio telescopes, most of our knowledge of the cold gas
associated with AGN comes from studying nearby objects. Absorption lines, which are effectively detectable at any luminosity
distance for a given population of background sources, afford us
an opportunity to extend our knowledge of the cold gas in active
galaxies beyond _z_ _∼_ 0 _._ 1 to cosmological distances. Particularly
neutral atomic hydrogen (H I ), which is abundant in the interstellar
medium (ISM) and readily detectable via the 21-cm and Lyman _α_
lines, is an effective tracer of neutral gas in galaxies to high redshift
(see Kanekar & Briggs 2004; Morganti et al. 2015 and Wolfe et al.
2005 for reviews).
In the case of detecting the cold gas feeding radio-loud AGN
at cosmological distances (i.e. _z_ _≫_ 0 _._ 1) there has been mixed success (e.g. Uson et al. 1991; Carilli et al. 1998; Moore et al. 1999;
Vermeulen et al. 2003; Ishwara-Chandra et al. 2003; Curran et al.
2011a, 2013; Allison et al. 2015; Yan et al. 2016; Aditya et al. 2017;
Aditya & Kanekar 2018), due primarily to the low detection rates
associated with luminous AGN (see e.g. Curran & Whiting 2010)
and the targeted nature of these searches driven by limitations in
usable radio bands and survey speeds of existing radio telescopes.
However, new pathfinder telescopes to the planned Square Kilometre Array (SKA) provide an exciting opportunity to survey the cold
gas in active galaxies using the 21-cm absorption line. Recently,
Allison et al. (2015) (hereafter A15) and Moss et al. (2017) successfully demonstrated this with the Australian Square Kilometre
Array Pathfinder (ASKAP; Johnston et al. 2007). The combination
of a wide instantaneous bandwidth (300 MHz), and a band that at
frequencies below 1 GHz is typically clear of radio frequency interference (see e.g. Allison et al. 2017), enables 21-cm line surveys
to be carried out without the need for existing spectroscopicallydetermined redshifts. Future wide-field 21-cm line surveys with
telescopes such as ASKAP will search for the cold gas in thousands of radio galaxies (Maccagni et al. 2017; Morganti & Oosterloo 2018).


MNRAS **000**, 1–16 (2017)

_Cold gas feeding an interacting young radio galaxy_ 3



In this paper we present results from observations with the
Atacama Large Millimetre Array (ALMA) of PKS B1740 _−_ 517,
a compact (∆ _d_ src _∼_ 300 pc) GHz peaked spectrum (GPS) radio
source associated with a luminous AGN at a redshift of _z_ = 0 _._ 44.

A15 discovered H I absorption in the host galaxy of this source using the ASKAP Boolardy Engineering Test Array (BETA; Hotan
et al. 2014; McConnell et al. 2016). Here we have used ALMA
to search for [12] CO (2-1) emission and absorption, tracing the cold
molecular component of the neutral gas, and to provide a stronger
constraint on the high frequency continuum and hence spectral age
of the source. We also present further ASKAP observations of the
H I absorption line, allowing us to better constrain the kinematics
of the line-of-sight atomic gas. We structure the paper as follows.
In section 2 we describe the properties of PKS B1740 _−_ 517 and its
immediate environment. We present a brief description of our observations and data analysis in section 3. We present our results in
section 4 and in section 5 we discuss the implications for understanding this radio galaxy and future searches for molecular absorption at cosmological distances. We summarise our conclusions
in section 6. In all distance calculations dependent on cosmological
parameters we adopt a flat Λ cold dark matter (ΛCDM) cosmology
with _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1], Ω M = 0 _._ 3 and Ω Λ = 0 _._ 7.


**2** **PKS B1740-517: A DISTANT YOUNG RADIO GALAXY**


We summarise the known properties of PKS B1740 _−_ 517 and its
host galaxy in Table 1. The radio source is bright ( _S_ 843 MHz =
8 _._ 2 Jy; Mauch et al. 2003), and resolved by very long baseline interferometry (VLBI; King 1994) into two compact (≲ 10 mas) components separated by 52 mas. The radio spectral energy distribution
(SED) is peaked at about 1 GHz indicating that it is an intrinsically
young source and/or strongly confined by a dense ambient medium.
The redshift of _z_ = 0 _._ 44 (corresponding to a comoving distance of approximately 1700 Mpc) was first determined using the
21-cm line in absorption and later confirmed through measurement of the optical spectrum (A15). The optical spectrum is typical of an emission-line radio galaxy and exhibits radiatively efficient accretion on to the AGN (EW [OIII] = 23 _._ 73 _±_ 0 _._ 95 Å,

[O III ] _/_ H _β_ = 5 _._ 60 _±_ 1 _._ 43; A15). The [O III ] _λ_ 5007 line has
two peaks that are separated by approximately 500 km s _[−]_ [1] in radial velocity. These velocity components are spatially resolved by
GMOS long-slit observations (A15) into two distinct components
separated by 1.3 kpc, indicating either rotating circumnuclear, or
outflowing, ionised gas, on scales extending beyond the central region of the AGN.
The AGN is X-ray luminous ( _L_ 2 _−_ 10 keV _≈_ 6 _._ 2 _×_ 10 [44] erg s _[−]_ [1] )
when compared with other young compact radio galaxies (e.g.
Tengstrand et al. 2009; Siemiginowska et al. 2016). Fitting a simple absorption and power law model to the X-ray spectrum reveals an intrinsic absorbing medium with hydrogen column density _N_ H _,_ X _∼_ 10 [22] cm _[−]_ [2] (A15). However, the photon spectral index is particularly hard (Γ _≈_ 0 _._ 8), which may indicate either
secondary emission from scattering and a Compton-thick medium
( _N_ H _,_ X _>_ 10 [24] cm _[−]_ [2] ), or inverse-Compton scattering in the radio
lobes (e.g. Ostorero et al. 2010).
At near and mid-infrared wavelengths, photometry from the
Two Micron All-Sky Survey (2MASS; Skrutskie et al. 2006) and
the Wide-Field Infrared Survey Explorer (WISE; Wright et al.
2010) indicates a massive host galaxy with _M_ _∗_ _∼_ 5 _×_ 10 [10] M _⊙_,
assuming a stellar mass-to-light ratio of _M_ _∗_ _/L_ _∼_ 0 _._ 6 (Meidt


MNRAS **000**, 1–16 (2017)



**Table 1.** Selected properties of PKS B1740-517 and its host galaxy.


Property Value Unit Reference


RA(J2000) 17 [h] 44 [m] 25 [s] _._ 450 Fey et al. (2009)
Dec _._ (J2000) _−_ 51 _[◦]_ 44 _[′]_ 43 _[′′]_ _._ 79 Fey et al. (2009)
∆ _θ_ src 52 mas King (1994)
_S_ 843 MHz 8.2 Jy Mauch et al. (2003)
W4 (22 _µ_ m) 7.9 mag Wright et al. (2010)
W3 (12 _µ_ m) 10.5 mag Wright et al. (2010)
W2 (4 _._ 6 _µ_ m) 13.3 mag Wright et al. (2010)
W1 (3 _._ 4 _µ_ m) 14.4 mag Wright et al. (2010)
_K_ s 15 _._ 3 mag Skrutskie et al. (2006)
_R_ 20 _._ 8 mag Burgess & Hunstead (2006)
_b_ _J_ _>_ 21 _._ 5 mag Burgess & Hunstead (2006)
_z_ 0.4413 A15
_P_ 1 _._ 4 GHz 3 _._ 0 _×_ 10 [27] W Hz _[−]_ [1] This work
_L_ 5 GHz 6 _._ 6 _×_ 10 [43] erg s _[−]_ [1] This work
_L_ 12 _µ_ m 5.8 _×_ 10 [45] erg s _[−]_ [1] This work
_L_ 3 _._ 4 _µ_ m 3.7 _×_ 10 [44] erg s _[−]_ [1] This work
_L_ [O II] _λ_ 3727 _[a]_ 1 _._ 0 _×_ 10 [41] erg s _[−]_ [1] A15
_L_ [O III] _λ_ 5007 _[a]_ 3 _._ 4 _×_ 10 [41] erg s _[−]_ [1] A15
_L_ 2 _−_ 10 keV 6 _._ 2 _×_ 10 [44] erg s _[−]_ [1] A15
_N_ H _,_ X 1 _._ 2 _×_ 10 [22] cm _[−]_ [2] A15
_M_ _∗_ _∼_ 5 _×_ 10 [10] M _⊙_ This work


_a_ corrected for Galactic extinction ( _A_ v _≈_ 0 _._ 66 mag; Schlegel et al. 1998).


et al. 2014). The rest frame WISE colours ([3.4] _−_ [4.6] = 0.67 and

_−_

[4.6] [12] = 3.4) are typical for a Seyfert-like AGN.
In Figure 1 we show a three-colour optical image of the immediate environment, constructed from _g_ _[′]_ _r_ _[′]_ _i_ _[′]_ -band observations with
the 8-m Gemini-South telescope by A15. At least two candidate
companion galaxies can be seen within a projected distance of ap
_−_
proximately 11 kpc, which are connected to PKS B1740 527 by a
bridge of emission that indicates a possible ongoing tidal interaction. We also show the optical spectrum of one of these candidate
companion galaxies, which based on the [O II ] _λ_ 3727 and blended
Mg emission lines has a redshift _z_ = 0 _._ 44080 that is consistent
with that of PKS B1740 _−_ 517. There is therefore evidence that this

radio galaxy is located within an interacting group, which may have
triggered the most recent activity.


**3** **OBSERVATIONS AND DATA**


**3.1** **The Atacama Large Millimetre Array**


Millimetre wavelength observations of PKS B1740 _−_ 517 were carried using ALMA on 2016 July 20 to detect either line emission or
absorption from the _J_ = 1 _→_ 2 rotational transition of Carbon
Monoxide ( [12] CO). Our observations were prepared and submitted using Cycle-3 Phase-II version of the ALMA Observing Tool [2] .
PKS B1740 _−_ 517 was observed for a total of 23 mins, in three scans
each bracketed by 30 sec observations of a nearby phase calibra
_−_
tor (J1753 5015). A further 5 min observation of J1924-2914 was
used for calibration of the flux scale and spectral bandpass.
We centred one baseband on the expected frequency of
12
159.9 GHz for the redshifted CO (2-1) line, with 3840 _×_
0 _._ 488 MHz channels (∆ _v_ _≈_ 0 _._ 9 km s _[−]_ [1] ) spanning rest-frame radial velocities in the range _v_ _≈±_ 1760 km s _[−]_ [1] . After Hanning


2 [https://almascience.nrao.edu/](https://almascience.nrao.edu/documents-and-tools/cycle3/alma-ot-refmanual)
[documents-and-tools/cycle3/alma-ot-refmanual](https://almascience.nrao.edu/documents-and-tools/cycle3/alma-ot-refmanual)

4 _J. R. Allison et al._


**Figure 1.** Left: A three-colour optical image of PKS B1740 _−_ 517 constructed from _g_ _[′]_ _r_ _[′]_ _i_ _[′]_ -band observations with the 8-m Gemini-South telescope (A15). At
least one candidate companion galaxy (b) is evident, and a possible tidal interaction. To the south east, off the slit, we also see evidence of a possible second
companion. The diagonal blue lines indicate the position and width of the slit. Overlaid are ALMA 152 GHz continuum contours at 20 per cent intervals of
the peak continuum ( _S_ 152 GHz = 74 _._ 3 mJy). Right: Gemini spectra extracted at the position of PKS B1740 _−_ 517 (a) and candidate companion galaxy (b).
Identified spectral lines are as labeled.



smoothing the effective resolution is twice the channel spacing,
∆ _v_ _≈_ 1 _._ 8 km s _[−]_ [1] . We used the other three available basebands

to provide a sensitive continuum flux density measurement of
PKS B1740 _−_ 517 at 150 GHz. These were centred at sky frequencies of 146, 148, and 158 GHz, each with 128 channels spanning
a bandwidth of 1875 MHz. At 159.9 GHz, the primary beam full
width at half power of the 12-m antennas is 33 arcsec, and the array
configuration, spanning baseline lengths between approximately
15.1 m and 1.1 km, is sensitive to angular scales between about 0.35
and 26 arcsec with an elongation by a factor of approximately 2 in
the East-West direction.

Data importing, flagging and calibration were carried out using version 4.5.3 of the CASA [3] package (McMullin et al. 2007)
and the standard ALMA science pipeline tools [4] . Using visibility data from the continuum bands we generated a two-term Taylor multi-frequency synthesis image with Uniform weighting, giving a resolution of 0 _._ 33 _×_ 0 _._ 76 arcsec at 152 GHz. The continuum emission from PKS B1740 _−_ 517 is unresolved by our ALMA
observations, and has a total flux density of 72 _._ 5 _±_ 0 _._ 3 mJy at
152 GHz. However, we note that future observations with ALMA
that use the maximum 16 km antenna baseline (∆ _θ_ psf _≈_ 26 mas at
150 GHz) would be well matched to the known source separation
(∆ _θ_ src = 52 mas at 2.3 GHz; King 1994).
Imaging of the [12] CO (2-1) spectral line band was carried out
using two different approaches for detecting absorption and emission, respectively. For detecting [12] CO (2-1) absorption towards the
continuum source we imaged the visibilities at the full 2 km s _[−]_ [1] velocity resolution. Since the continuum source is not resolved with
uniform weighting we used natural weighting (with a resolution
of 0 _._ 5 _×_ 1 _._ 1 arcsec) to maximise detected signal-to-noise, and extracted the spectrum from the cube at the position of peak continuum flux density. We fitted a 1st-order polynomial to the continuum, which was then used to normalise the spectrum to units of
percentage absorption. We show the spectrum in Figure 2, overlaid
with the H I absorption detected with ASKAP. Although [12] CO (21) absorption is clearly detected above the RMS noise level of


3 [http://casa.nrao.edu](http://casa.nrao.edu)
4 [https://almascience.nao.ac.](https://almascience.nao.ac.jp/documents-and-tools/cycle-2/alma-pipeline-reference-manual)
[jp/documents-and-tools/cycle-2/](https://almascience.nao.ac.jp/documents-and-tools/cycle-2/alma-pipeline-reference-manual)

[alma-pipeline-reference-manual](https://almascience.nao.ac.jp/documents-and-tools/cycle-2/alma-pipeline-reference-manual)



3.1 per cent per 2 km s _[−]_ [1], there is a noticeable absence of molecular gas detected at the velocity of the narrower deeper H I component. We also do not detect any [12] CO (2-1) emission in this spectrum towards the continuum source above the RMS noise level of
1.98 mJy beam _[−]_ [1] per 2 km s _[−]_ [1] .
For detecting [12] CO (2-1) emission within the host galaxy we
first imaged and subtracted the continuum directly from the visibilities using UVSUB, followed by a first-order polynomial using
UVCONTSUB3 to remove any residual signal. We then formed a
data cube in 10 km s _[−]_ [1] velocity bins, again using natural weighting
to optimise detected signal-to-noise. We extracted the flux density
spectrum by summing pixels per spatial resolution element within
1.75 arcsec (a projected distance of 10 kpc) of PKS B1740 _−_ 517.
This spectrum (Figure 3) shows no evidence of [12] CO (2-1) emission above the RMS noise level of 2.10 mJy per 10 km s _[−]_ [1] .


**3.2** **The Australian SKA Pathfinder**


Further 21-cm observations of PKS B1740 _−_ 517 were undertaken

as part of ASKAP commissioning and early science verification.
We used two developmental stages of this telescope – the sixantenna Boolardy Engineering Test Array (ASKAP-BETA) and
ASKAP-12 (Hotan et al. 2014; McConnell et al. 2016) – which
differ principally in the design of their Phased Array Feeds (PAFs;
Hay & O’Sullivan 2008) and backend. ASKAP-12 is equipped
with new Mark II PAFs, which have improved sensitivity at
1400 MHz (Chippendale et al. 2015) and will be used for the
completed ASKAP telescope. We used the same observing strategy as described by A15, whereby we pointed the telescope at
PKS B1740 _−_ 517 and maximum S/N PAF beams were electroni
cally formed in an on-sky pattern that included a central beam on
the source. For each observation we included a short 15 min scan

of PKS B1934 _−_ 638 to calibrate the flux scale (using the model of
Reynolds 1994) and to obtain initial solutions for the antenna gains.
Further self-calibration, continuum-subtraction and imaging of the
target field were carried out using the MIRIAD [5] package (Sault


5 [http://www.atnf.csiro.au/computing/software/](http://www.atnf.csiro.au/computing/software/miriad/)

[miriad/](http://www.atnf.csiro.au/computing/software/miriad/)


MNRAS **000**, 1–16 (2017)

_Cold gas feeding an interacting young radio galaxy_ 5


**Table** **2.** Summary of our observations using the ASKAP BETA and ASKAP _−_ 12 telescopes (Hotan et al. 2014; McConnell et al. 2016). Each observation
is assigned a unique scheduling block identification (SBID) number for that telescope. _t_ int denotes the on-source observing time. _σ_ chan is the rms noise per
18.5 kHz channel at the H I line, as a fraction of the continuum flux density. _S_ cont is the total continuum flux density measured using the full bandwidth.


SBID Date Frequency band ASKAP antennas _[a]_ _t_ int _σ_ chan _S_ cont

[MHz] [h] [per cent] [Jy]


ASKAP-BETA
93 _[b]_ 2014 June 24 711.5 _−_ 1015.5 1, 8, 9, 15 11.5 0.24 8.0
315 _[b]_ 2014 August 03 711.5 _−_ 1015.5 1, 3, 6, 8, 15 3.0 0.59 7.9
514 _[b]_ 2014 September 01 711.5 _−_ 1015.5 1, 6, 8, 15 11.9 0.20 7.4
1808 2015 May 14 711.5 _−_ 1015.5 1, 3, 6, 8, 9, 15 12.0 0.17 7.4
1994 2015 June 25 711.5 _−_ 1015.5 1, 6, 8, 15 7.5 0.80 8.5

2009 2015 June 27 711.5 _−_ 1015.5 1, 6, 8, 15 11.0 0.47 6.6

3073 2015 November 09 711.5 _−_ 1015.5 1, 3, 6, 8, 15 6.0 0.32 6.8

3085 2015 November 11 711.5 _−_ 1015.5 1, 3, 6, 8, 15 12.0 0.22 6.9

3086 2015 November 12 711.5 _−_ 1015.5 1, 3, 6, 8, 15 12.0 0.22 6.8

3088 2015 November 13 711.5 _−_ 1015.5 1, 3, 6, 8, 15 12.0 0.22 6.9


ASKAP-12

3304 2017 January 31 799.4 _−_ 1039.4 1, 2, 4, 5, 6, 10, 12, 13, 2.0 0.16 8.3
14, 19, 24, 26, 27, 28


_a_ See Hotan et al. (2014) and Lee-Waddell et al. in preparation for details of the ASKAP-BETA and ASKAP-12 antenna
positions.
_b_ Originally published by Allison et al. (2015).



et al. 1995) as described by A15, but using a higher 1 MHz resolution to form the coarse-channel data (see Allison et al. 2017).


Increased backend capacity means that ASKAP-12 forms PAF
beams at 1 MHz intervals (c.f. 4 and 5 MHz intervals for ASKAPBETA). The element weights used to form PAF beams are applied
uniformly in these intervals before channelization at full 18.5 kHz
resolution. This process creates discontinuous jumps in amplitude
and phase as a function frequency, which typically dominate the
bandpass on these scales. In the case of ASKAP-BETA, these intervals in frequency equate to radial velocities ∆ _v_ _>_ 1000 km s _[−]_ [1]

at _z_ HI = 0 _._ 44 and so on these scales we can simply fit and subtract any residual continuum signal in the target spectrum using
UVLIN (see A15). However, for the smaller beam forming intervals of ASKAP-12, this approach would lead to subtraction of real
spectral features with linewidths ∆ _v_ _>_ 300 km s _[−]_ [1] at _z_ HI = 0 _._ 44.
In the case of PKS B1740 _−_ 517 we did not detect any significant
features in the ASKAP BETA spectra with these linewidths. Furthermore, since the ASKAP-12 data contribute only an additional
11 per cent to the S/N in the average spectrum, this affect is unlikely to influence detection of broad features that already exist in
the BETA data.


We summarise our observations in Table 2. The source is not

spatially resolved by either ASKAP-BETA or ASKAP-12. The averaged spectrum (shown in Figure 2) was constructed to have optimal S/N by weighting each observation by its inverse variance, with
a resulting RMS fractional continuum absorption of 0 _._ 07 per cent
per 5.6 km s _[−]_ [1] at the H I line. Two distinct velocity components
are seen in H I absorption. The third component, a possible broad
∆ _v_ _≈_ 300 km s _[−]_ [1] outflow reported by A15, remains tentative, and
corroborating evidence from either deeper observations or other gas
transitions are needed to resolve its authenticity.


MNRAS **000**, 1–16 (2017)



**4** **RESULTS**


**4.1** **Constraints on the line-of-sight cold gas**


Using ALMA we have detected [12] CO (2-1) absorption in the host
galaxy of PKS B1740 _−_ 517. In Figure 2 we show the ALMA spectrum overlaid with the H I absorption detected with ASKAP. Since
information about the gas kinematics encoded in the spectrum is
limited by the spatial extent of the continuum source, it is difficult
to determine the three dimensional motion of the gas from the unresolved absorption spectrum alone. However, the absorption lines
allow us to probe the neutral gas at small scales towards to the AGN
and we can use the known continuum source morphology, the lineof-sight gas kinematics, and simple priors for the gas distribution to
infer likely models. In the following we discuss our interpretation
of the features seen in the ALMA and ASKAP spectra, and how the
former has allowed us to further constrain our understanding of the
cold gas in the host galaxy.


_4.1.1_ _The broad absorption - a circumnuclear reservoir_


The H I absorption in PKS B1740 _−_ 517 has two distinct spectral components that are separated by a radial velocity of ∆ _v_ _≈_
115 km s [1] . The broader component has a FWHM of approximately
60 km s _[−]_ [1] and a redshift that is consistent with the centroid of the

double-peaked [O III ] _λ_ 5007 emission line, indicating that the gas
motion is symmetric about the galactic nucleus. The coincident
12 CO (2-1) line has a similar width and is therefore unlikely to arise
in a single molecular cloud; the velocity dispersion is significantly
larger than observed in any Galactic molecular cloud and the inferred linear size would be larger than a few kiloparsecs (Larson
1981; Solomon et al. 1987; Heyer et al. 2009). It is more likely
that the CO absorption is arising from several blended spectral features from individual parsec-scale molecular clouds embedded in a
larger gaseous structure with a velocity gradient.
In Figure 4 we show in the detail the absorption spectrum,
which reveals sub-structure in both the H I and [12] CO (2-1) lines

6 _J. R. Allison et al._


0


2


4


6


8


10


12





_−_ 1000 _−_ 500 0 500 1000
_v_ [km s _[−]_ [1] ]


**Figure** **3.** ALMA spectrum showing no evidence of CO (2-1) emission
within a projected distance of 10 kpc of PKS B1740 _−_ 517. The data have
been binned to a velocity resolution of 10 km s _[−]_ [1] . The velocity axis is as
defined in Figure 2.


sistent with the absorbed fraction of total continuum flux density
seen in the ALMA spectrum.
The H I absorption, which is assumed to trace the more diffuse cold gas, appears to have two prominent peaks, separated by
a radial velocity of ∆ _v_ _≈_ 20 km s _[−]_ [1] . Such symmetric doublepeaked structure could arise from a gaseous disc, or ring, which
is illuminated by continuum emission from the compact-double radio source. Given that the flux densities of the source components
are in the ratio _∼_ 4:1 (King 1994) it may seem surprising that the
optical depths of the two peaks are almost equal. However several
effects, including the detailed radial velocity distribution of the HI
gas in front of each source (including turbulence) and differences
in the physical conditions of the gas at different positions, could
easily account for this.
Using the separation of the velocity peaks (∆ _v_ ) and source
components (∆ _d_ src ) we can then obtain an approximate estimate
of the line-of-sight extent of the neutral gas (∆ _d_ gas ). For gas moving in a circular orbit with velocity _v_ circ with respect to the galactic centre, the radial velocity separation observed in the absorption
spectrum is given by (see Figure 5)


∆ _v_ _≈_ _v_ circ cos ( _i_ ) cos ( _φ_ ) cos ( _θ_ ) _,_ (3)


where









0


20


40


60


80


100


120



_−_ 600 _−_ 400 _−_ 200 0 200 400 600
_v_ [km s _[−]_ [1] ]


**Figure** **2.** ALMA spectrum of PKS B1740 _−_ 517 showing [12] CO (2-1) absorption towards the radio-loud AGN. Superposed is the average ASKAP
21-cm spectrum showing H I absorption. The data are given as a fraction of the total continuum flux density measured at that transition. The
ALMA and ASKAP data have been binned to velocity resolutions of 2.0
and 5.6 km s _[−]_ [1], respectively. The velocity axis is given in the rest frame
defined by the broader H I and CO absorption (at _z_ = 0 _._ 44185), which is
consistent with the AGN rest frame defined by the centroid of the doublepeaked [O III ] _λ_ 5007 emission line (see A15).


centred at _v_ _≈_ 0 km s _[−]_ [1] . The molecular absorption possibly has
more sub-structure, albeit at higher resolution and lower signalto-noise; several individual components are apparent with widths
∆ _v_ _∼_ 10 km s _[−]_ [1] . If the molecular gas is optically thick to [12] CO (21) then the seemingly low absorbed fraction of the total continuum
(i.e. less than 100 per cent) is likely the result of patchy obscuration
of the background source as a function of radial velocity (see e.g.
Wiklind & Combes 1997). This would be consistent with CO absorption through a line-of-sight distribution of discrete cold molecular cores, while the H I absorption arises from more diffuse coldphase atomic structures as observed in the ISM of the Milky Way
and Local Group galaxies (see e.g. Heiles & Troland 2003; Gibson
et al. 2005; Braun et al. 2009; Braun 2012).
From very long baseline interferometry at 2.3 GHz (King
1994) we know that the source components are separated in projection by approximately 300 pc and each has a size less than approximately 50 pc, which are thus likely to be fully subtended by
any coherent structure in the foreground interstellar medium (ISM).
Assuming uniformly distributed optically thick CO clouds ( _τ_ _>_ 1)
of radius _r_ mol and filling factor _f_ mol within a roughly spherical volume of characteristic radius _R_, the expected areal covering fraction
(allowing for overlapping clouds) is then given by



cos ( _θ_ ) = [∆] _[d]_ [src] (4)

∆ _d_ gas _[,]_


and _i_ and _φ_ are angles of the plane of rotation with respect to our
sight line and the projected source-AGN axis, respectively. We can
then infer the line-of-sight extent of the absorbing gas by rearranging this expression, as follows



_⟨c_ mol _⟩≈_ 1 _−_ 1 _−_ [3]
� 4


where



� _r_ mol _R_



2 [�] _[n]_ mol
_,_ (1)
�



∆ _d_ gas _≈_ _[v]_ ∆ [circ] _v_ [cos (] _[i]_ [) cos (] _[φ]_ [) ∆] _[d]_ [src] _[.]_ (5)


Following this simple geometrical argument, large radial velocities imply that the absorbing gas is close to the radio source, while
gas that is much further away will have an observed radial velocity close to zero. Deviations from a regular circular orbit will result in an error in the inferred radial distance of the absorbing gas.
Given that ∆ _d_ src _∼_ 300 pc, ∆ _v_ _∼_ 20 km s _[−]_ [1], 0 _≤_ _i_ _≤_ 90 _[◦]_ and


MNRAS **000**, 1–16 (2017)



_n_ mol = _f_ mol



_R_ 3

_._ (2)

� _r_ mol �



For the Milky Way ISM, _f_ mol ≲ 1 per cent and _r_ mol _∼_ 10 pc,
gives _⟨c_ mol _⟩_ ≲ 86 per cent for _R_ _∼_ 2 kpc (typical of the radial extent of molecular discs in massive early type galaxies; e.g. Davis
et al. 2013). Assuming that the molecular gas has a dispersion per
opaque cloud of _∼_ 4 km s _[−]_ [1] leads to a covering fraction of less than
_∼_ 10 per cent over a total line width of _∼_ 50 km s _[−]_ [1], which is con

_Cold gas feeding an interacting young radio galaxy_ 7


_d_ src

source



0


1


2


3







0


10


20


30



**Figure** **4.** An enlarged version of the absorption spectrum shown in Figure 2, highlighting the velocity structure at _v_ _∼_ 0 km s _[−]_ [1] that may indicate
illumination of a gaseous ring or disc.


0 _≤_ _φ_ _≤_ 90 _[◦]_, and assuming _v_ circ _∼_ 200 km s _[−]_ [1], we estimate
that the illuminated absorbing gas lies radially within ∆ _d_ gas _∼_
2 kpc of the AGN. A15 found similar double-peaked structure in
the [O III ] _λ_ 5007 emission line, separated by ∆ _v_ _∼_ 500 km s _[−]_ [1]

and resolved into two spatially distinct components separated by
1.3 kpc, indicating a possible ionised counterpart to the neutral gas
seen in absorption. The neutral and ionised gas detected towards
PKS B1740 _−_ 517 are thus consistent with a disc or ring within a
few kiloparsecs of the AGN.
We can estimate the column density of neutral atomic and
molecular gas from the integrated absorption line strength in the
ASKAP and ALMA spectra. In general the column density of
a gaseous species X populating an upper level _u_ of a transition
_u →_ _l_, with optical depth _τ_ X( _ul_ ) integrated over rest frame velocity
_v_, is given by



_N_ X( _u_ ) = [8] _c_ _[π]_ [3] _A_ 1 _ul_ _e_ _[hν]_ _[ul]_ _[/k]_ _ν_ [B] _ul_ [3] _[T]_ [ul] _−_ 1



_τ_ X( _ul_ ) d _v,_ (6)
�



where _ν_ _ul_ is the rest frequency, _A_ _ul_ is the Einstein coefficient for
spontaneous emission and _T_ ul is the excitation temperature. The
total column density for species X is calculated by multiplying this
by the partition function and dividing by the relative population of
the upper level _u_, giving




_[π]_ _ν_ _ul_ [3] _f_ ( _T_ ul )

_c_ [3] _g_ _u_ _A_ _ul_



_N_ X = [8] _[π]_



_A_ _ul_



_τ_ X( _ul_ ) d _v,_ (7)
�



where



_f_ ( _T_ ul ) = 1 _[Q]_ _−_ [(] _[T]_ _e_ [ul] _[−]_ [)] _[hν]_ _[ e]_ _[E]_ _[ul][l]_ _[/k][/k]_ [B][B] _[T][T]_ [ul][ul] _[,]_ (8)


_g_ _u_ is the statistical weight of _u_, _E_ _l_ is the lower energy level, and
_Q_ ( _T_ ul ) is the partition function assuming a single excitation temperature (e.g. Wiklind & Combes 1995).
For the 21-cm line of H I, _hν_ _ul_ _≪_ _k_ B _T_ ul and _A_ _ul_ = 2 _._ 85 _×_
10 _[−]_ [15] s _[−]_ [1], giving



cm _[−]_ [2] _,_ (9)
�



_T_ spin
_N_ HI _≈_ 1 _._ 823 _×_ 10 [20]
� 100 K



_τ_ HI d _v_
�� 1 km s [�] _[−]_ [1]



gas


_v_ circ cos( _i_ ) cos(f) cos( _θ_ )


**Figure** **5.** A schematic diagram (not to scale) showing the relative positions of the AGN (origin), radio source component (star) and absorbing gas
(cloud). The gas is assumed to be moving in a circular orbit with velocity
_v_ circ . The plane of rotation is centred on the origin and orientated with inclination angle _i_ to the line-of-sight and position angle _φ_ with respect to the
radio source axis. The component of velocity in the direction of the observer

is indicated.


solve the spatial structure of PKS B1740 _−_ 517, we can only estimate the average optical depth over the source cross-section, giving
� _τ_ HI d _v_ _≈_ 0 _._ 549 _±_ 0 _._ 019 km s _[−]_ [1] . If the H I does not subtend all
of the source then this can underestimate the true column of atomic

gas along our line-of-sight. However, we note that the source components have an angular size less than 10 mas, which corresponds
to a physical scale of approximately 57 pc at _z_ = 0 _._ 44. This is
similar to the scales typically measured for coherent absorbing H I
structures resolved in studies of the Local Group (e.g. Braun 2012
and references therein) and distant galaxies (e.g. Lane et al. 2000;
Gupta et al. 2012; Srianand et al. 2013; Borthakur et al. 2014; Biggs
et al. 2016; Dutta et al. 2016; Gupta et al. 2018), implying that the
covering factor may well be close to unity.
In the absence of independent measurements of the H I column density from Lyman- _α_ absorption or 21-cm line emission,
a canonical spin temperature of _T_ spin _∼_ 100 K is often adopted
based on the typical value for H I in the Milky Way (e.g. Heiles
& Troland 2003). However, given the proximity of the atomic
gas to PKS B1740 _−_ 517, a luminous AGN that is a strong source
of continuum radiation both at 21-cm and Lyman- _α_ wavelengths,
the spin temperature could be significantly larger than this value
(Bahcall & Ekers 1969). For example, Holt et al. (2006) used an
independent estimate of the neutral gas column from extinction
to derive a spin temperature lower limit of 3000 K in absorbing
gas in the host galaxy of the obscured quasar PKS 1549 _−_ 79. For
PKS B1740 _−_ 517, A15 compared the total hydrogen column density from the X-ray spectrum and the total integrated H I 21-cm
optical depth from the ASKAP spectrum to estimate an upper limit
for the spin temperature of _T_ spin ≲ 2430 _±_ 1050 K. We therefore consider spin temperatures in the range 100 to 2000 K, giving



where _T_ spin is the excitation temperature for the spin-flip transition. Since our observations with ASKAP and ALMA do not re

MNRAS **000**, 1–16 (2017)

8 _J. R. Allison et al._


an average H I column density in front of the source in the range
_N_ HI _∼_ 0 _._ 1 _−_ 2 _×_ 10 [21] cm _[−]_ [2] . Assuming that the atomic gas has
a scale height _h_ _∼_ 150 pc (so that the disc obscures both source
components) and a radial extent _∼_ 2 kpc from the AGN, we obtain
an enclosed mass for H I in the range _M_ HI _∼_ 0 _._ 3 _−_ 6 _×_ 10 [7] M _⊙_ .
For the _J_ = 2 _→_ 1 rotational transition of [12] CO, _A_ _ul_ =
7 _._ 36 _×_ 10 _[−]_ [7] s _[−]_ [1] (e.g. Chandra et al. 1996) and we can use the
rigid-rotor approximation, so that _h ν_ _ul_ _/k_ B _≈_ 2( _J_ _l_ + 1) _B_ = 4 _B_
and _E_ _l_ _/k_ B _≈_ _J_ _l_ ( _J_ _l_ + 1) _B_ = 2 _B_, where the rotational constant _B_ _≈_ 2 _._ 766 K. In the Milky Way ISM the typical temperature of the CO gas is _∼_ 16 K (Heyer et al. 2009). However, close
to a radio-loud active galactic nucleus the CO could be excited to
higher temperatures through shocks and turbulence in the gas (e.g.
Papadopoulos et al. 2008; Dasyra & Combes 2012). Under the assumption that _T_ ul _≫_ _B_, the partition function can be approximated by _Q_ ( _T_ ul ) _≈_ _T_ ul _/B_ . Assuming an excitation temperature
_T_ ul ≳ 10 K, we obtain a [12] CO column density of



_τ_ CO d _v_
_N_ CO ≳ 1 _._ 5 _×_ 10 [16]
� [�] 5 km s _[−]_ [1]



cm _[−]_ [2] _._ (10)
�



As with the H I absorption, the [12] CO (2-1) optical depth integrated
over the line shown in Figure 2 is an average over the total source
cross-section. However, unlike the H I, the molecular gas is distributed in clumpy dense clouds, which significantly reduces the
covering fraction against the continuum source. Given this uncertainty about the covering fraction we obtain a lower limit for the
integrated optical depth of � _τ_ CO d _v_ ≳ 4 _._ 78 _±_ 0 _._ 47 km s _[−]_ [1] . We
estimate a lower limit to the average CO column density in front of
the source of 1 _._ 5 _×_ 10 [16] cm _[−]_ [2] and, for a Milky Way [12] CO-to-H 2
abundance ratio in dense clouds of _Z_ CO _∼_ 1 _×_ 10 _[−]_ [4] (e.g. Sofia
et al. 2004), a corresponding cold H 2 column density lower limit of
_N_ H 2 ≳ 1 _._ 5 _×_ 10 [20] cm _[−]_ [2] . We note that the [12] CO-to-H 2 abundance
ratio can be two orders of magnitude lower in the diffuse interstellar medium than in dense clouds, in which case the total H 2 column
density in front of the radio AGN could be much higher than this
lower limit (Burgh et al. 2007).
We can compare this lower limit with the non-detection of
12 CO (2-1) emission on the same sight-line to see if they are consistent. Assuming optically thick CO emission from the molecular clouds, and _L_ CO(2 _−_ 1) = _L_ CO(1 _−_ 0), the H 2 column density is
given by



_._ (12)
�



of the spectrum, equal to 300 mJy km s _[−]_ [1], giving an upper limit for
undetected emission of � _S_ CO d _v_ _<_ 579 mJy km s _[−]_ [1] .
The _X_ CO conversion factor depends on the physical properties
of the molecular gas, including density, temperature and metallicity
(see Bolatto et al. 2013 for a review). At solar metallicities in the
inner disc of the Milky Way, _X_ CO _≈_ 2 _×_ 10 [20] cm _[−]_ [2] [K km s _[−]_ [1] ] _[−]_ [1],
but can take significantly lower values in the low density turbulent gas of ultraluminous infrared galaxies ( _X_ CO _≈_ 0 _._ 4 _×_
10 [20] cm _[−]_ [2] [K km s _[−]_ [1] ] _[−]_ [1] ), or higher values in low metallicity environments. A sub-solar CO-to-H 2 conversion factor could be expected for molecular gas near to the radio source, where heightened temperatures and turbulence could lead to optically thin CO
emission (as for example the jet-driven molecular outflows seen
in IC 5063; Oosterloo et al. 2017). Without further information
we use _X_ CO for molecular gas in the Milky Way, which gives
_N_ H 2 ≲ 1 _×_ 10 [22] cm _[−]_ [2], consistent with the lower limit estimated from the absorption line. Using the same disc model as the
atomic gas, we use our two limits on the _H_ 2 column density to
calculate an enclosed mass for cold molecular gas in the range
_M_ H 2 _∼_ 0 _._ 9 _−_ 60 _×_ 10 [7] M _⊙_ .
We note that both the H I and H 2 masses inferred here are
consistent with the lower end of the mass distributions for nearby
massive early-type galaxies with detected neutral gas (e.g. Young
et al. 2011; Serra et al. 2012). However, we stress that our estimates are only for line-of-sight gas detected in absorption towards
the radio source, and may underestimate the total masses in the
host galaxy. In Figure 3 we show that no [12] CO(2-1) emission is
detected within a projected distance of 10 kpc of PKS B1740 _−_ 517
to the same level as seen towards the nucleus. It it is possible that
most of the cold gas detected in absorption was accreted from its
companion through tidal interaction, in which case a future gas-rich
minor merger may increase the gas mass significantly (e.g. Davis
et al. 2015).
The H I and H 2 column densities equate to a total gas surface mass density in the range Σ gas _∼_ 4 _._ 4 _−_ 221 M _⊙_ pc _[−]_ [2] (with
a 37 per cent correction for helium and metals). The KennicuttSchmidt law (Kennicutt 1998) then gives a star formation rate surface density in the range Σ SFR _∼_ 0 _._ 002 _−_ 0 _._ 5 M _⊙_ yr _[−]_ [1] kpc _[−]_ [2] in
the direction towards the AGN. We separately estimate the total star
formation rate from the O [ II ] _λ_ 3727 emission line (see Figure 1)
using the following relationship given by Kewley et al. (2004),

SFR _L_ [OII]

= (6 _._ 58 _±_ 1 _._ 65) _._ (12)

� M _⊙_ yr _[−]_ [1] � � 10 [42] erg s _[−]_ [1] �


This is an upper limit since there is likely to be significant
contribution to the emission line from AGN-driven ionisation.

The O [ II ] _λ_ 3727 luminosity, corrected for Galactic extinction, is
_L_ [OII] _≈_ 1 _._ 01 _×_ 10 [41] erg s _[−]_ [1], giving a total SFR ≲ 0 _._ 66 M _⊙_ yr _[−]_ [1] .
The spectrum was extracted over a region of 0.7 arcsec (equal to
4 kpc at _z_ = 0 _._ 44), giving an average SFR surface density upper
limit of Σ SFR ≲ 0 _._ 05 M _⊙_ yr _[−]_ [1] kpc _[−]_ [2] . We therefore do not find
evidence for any significant ongoing star formation (i.e. starburst
behaviour) in PKS B1740 _−_ 517. This may not be surprising given
both the timescales involved in triggering the AGN following an
interaction and the suppression by several orders magnitude of star
formation efficiency seen in minor mergers involving massive early
type galaxies at lower redshifts (e.g. van de Voort et al. 2018).


_4.1.2_ _The narrow HI absorption_


We consider next the physical origin of the deeper narrow H I absorption, which rather strikingly has no associated CO absorption


MNRAS **000**, 1–16 (2017)



_L_ [OII]
= (6 _._ 58 _±_ 1 _._ 65)
� � 10 [42] erg s _[−]_ [1]



_N_ H 2 _≈_ 1 _._ 22 _×_ 10 [3] _X_ CO (∆ _θ_ maj ∆ _θ_ min ) _[−]_ [1] _ν_ obs _[−]_ [2]



_S_ CO d _v_ cm _[−]_ [2] _,_
�


(11)



where _X_ CO is the CO-to-H 2 conversion factor, in units of
cm _[−]_ [2] [K km s _[−]_ [1] ] _[−]_ [1], ∆ _θ_ maj and ∆ _θ_ min are the major and minor
axes of the spatial region from which the spectrum was measured,
in units of arcsec, _ν_ obs is the observed frequency in GHz, and
� _S_ CO d _v_ is the line integrated flux density in units of mJy km s _[−]_ [1] .
For the ALMA spectrum shown in Figure 2 and Figure 4, the spatial resolution is 0 _._ 5 _×_ 1 _._ 1 arcsec and the observed frequency is
159 _._ 9 GHz. We assume a line width of 400 km s _[−]_ [1] for the unde
tected line (based on typical rotation velocities of molecular discs
in massive galaxies; Helfer et al. 2003; Davis et al. 2013) and measure an RMS of 1.98 mJy per 2 km s _[−]_ [1], giving a 5- _σ_ detection limit
for the line integrated flux density of 279 mJy km s _[−]_ [1] . However, the
detected absorption will act to disguise any possible emission, effectively lowering our detection sensitivity to emission over that region of the spectrum. We take the somewhat conservative approach
and add the missing integrated flux density in the absorbed region

_Cold gas feeding an interacting young radio galaxy_ 9



0


10


10


0


_−_ 10


0


10


10


0


_−_ 10


0


10


10


0


_−_ 10


0





10


10


0


_−_ 10



|Col1|Col2|Col3|Col4|
|---|---|---|---|
||2014 June 24<br>Average|2014 Aug_._ 03<br>Average|2014 S<br>Averag|
|||||
|||||
|||||
||2015 May 14<br>Average|2015 June 25<br>Average|2015 Ju<br>Averag|
|||||
|||||
|||||
||2015 Nov_._ 09<br>Average|2015 Nov_._ 11<br>Average|2015 N<br>Averag|
|||||
|||||
||_−_200<br>|0<br>200<br>_−_200<br>0<br>200<br>2017 Jan_._ 31<br>Average|0<br>200<br>_−_200<br>0<br>200<br>2017 Jan_._ 31<br>Average|
||2015 Nov_._ 13<br>Average|2015 Nov_._ 13<br>Average|2015 Nov_._ 13<br>Average|
|||||
|||||


_−_ 200 0 200
_v_ [km s _[−]_ [1] ]



_−_ 200 0 200



**Figure 6.** Spectra showing H I absorption for each of the 11 epochs observed with ASKAP. The red line in each panel is the variance-weighted arithmetic mean
of the data from all observations. Note that the affect of averaging over the line, which moves with respect to a fixed frequency grid, is to smooth out structures
on the scale of a single channel spacing. The difference spectra (blue filled) are shown in the panels below each epoch and are given in units of the RMS
noise per channel. We attribute the symmetrically-distributed noise artefacts at the position of the deep narrow component to re-gridding the under-sampled
component to a common channel.


MNRAS **000**, 1–16 (2017)

10 _J. R. Allison et al._


in the ALMA spectrum. Under our previously stated assumptions
about the AGN rest frame, this component of the atomic gas is
blue shifted by 115 km s _[−]_ [1] with respect to the nucleus and hence
has radial motion towards the observer. However, the line width
(∆ _v_ FHWM _<_ 5 km s _[−]_ [1] ) is inconsistent with jet-driven gas outflows that are typically associated with young radio sources (e.g.
Holt et al. 2008, Morganti et al. 2005). Hydrodynamic simulations
of interactions between radio jets and the interstellar medium (e.g.
Wagner et al. 2012; Mukherjee et al. 2018) predict dispersion velocities between _∼_ 100 and 1000 km s _[−]_ [1], resulting from turbulence
generated as the jet passes through disc. It is unlikely that the gas
could be accelerated by the jet to more than 100 km s _[−]_ [1] and retain
such a low dispersion.


We show in Figure 6 the H I spectrum for each epoch observed with ASKAP. Although the narrow line is under-sampled
it does move systematically with respect to the observed frequency
grid as a result of the orbital motion of the Earth, thus indicating
that it has a finite width on scales comparable to the resolution
of the telescope. For example, between 2015 November 09 and
November 11 the line peak is seen to cross channels, thereby inverting the profile shape. In order to measure the line width we
repeat the method described by A15, jointly modeling the narrower
H I component as the superposition of two Gaussians and taking
into account the spectral resolution of the telescope by convolving
with the fine filter bank response (Tuthill et al. 2012). Assuming
no astrophysical variation in the absorption line over the timescale
of a few years (no variation in the equivalent width is evident),
we obtain a FHWM line width for the deep narrow component of
∆ _v_ FHWM = 4 _._ 77 _−_ [+0] 0 _[.]_ _._ [07] 07 [km s] _[−]_ [1] [. Since this equates to a kinetic tem-]
perature upper limit of _T_ k ≲ 500 K, we are likely seeing absorption
through a single diffuse structure of cold neutral medium (CNM;
_T_ k _∼_ 100 K, e.g Wolfire et al. 2003; Heiles & Troland 2003). Surprisingly, this feature is devoid of the [12] CO (2-1) absorption detected elsewhere towards PKS B1740 _−_ 517.


Before discussing a physical interpretation for the absence of
CO absorption associated with the narrow H I line, we should first
consider that the subtended continuum emission may be too faint
at mm-wavelengths to sufficiently detect any CO that is present.
Assuming that the flux density ratio of the two source components
at 2.3 GHz can be extrapolated to all frequencies, this interpretation would imply that the narrow H I line is located in front of the
weaker component, giving a large peak optical depth of _τ_ HI ≳ 0 _._ 9.
Assuming a spin temperature in the range 100 and 500 K (set by the
upper limit on the kinetic temperature), the average column density
of the atomic gas is then between _N_ HI _∼_ 1 and 5 _×_ 10 [21] cm _[−]_ [2], consistent with a cold CNM structure. If the detected [12] CO (2-1) absorption is seen only in front of the stronger component then given
the 3.9:1 ratio of the source components at 2.3 GHz (King 1994)
we predict a peak absorbed fraction of approximately 16 per cent.
If the molecular gas has a similar distribution and physical state
in front of both source components, then any absorption associated with the weaker component is expected to have a peak in the
ALMA spectrum (Figure 4) of approximately 4 per cent. The RMS
per 2 km s _[−]_ [1] is 3 per cent of the total continuum flux density, which
for a single molecular cloud of velocity dispersion ∆ _v_ _∼_ 4 km s _[−]_ [1]

(Heyer & Dame 2015) would give a 3- _σ_ detection limit on the peak
of approximately 6 per cent. The ALMA data are therefore consistent with not detecting [12] CO (2-1) absorption, if the sight-line giving rise to the narrow H I line is seen only toward the weaker source

component.



_4.1.3_ _An accreting cold atomic gas cloud?_


It is also possible that our sight-line misses the dense molecular gas
entirely, particularly if the H I structure giving rise to the narrow
line is much smaller than the supposed large-scale disc associated
with the broader absorption line. If we assume that the molecular
clouds are well mixed with the cold atomic gas, then we can use
Equation 1 to estimate the expected relative covering fraction for
different sizes of the absorbing region. We further assume that since
molecular clouds likely form in the CNM they will have on average
a larger volume filling fraction than in the large-scale warm ISM,
so that _f_ mol _/f_ CNM ≲ 30 per cent. For an absorbing region in the
atomic gas extending _R_ = 100 pc along our line-of-sight, we estimate an upper limit molecular covering fraction of _∼_ 90 per cent,
which decreases to _∼_ 34 per cent for _R_ = _r_ = 10 pc. This would
suggest that the gas giving rise to the narrow H I line is distributed
on scales smaller than 100 pc. The atomic cloud/structure clearly
has very different kinematics to the aforementioned disc, and may
be on a non-circular orbit that will eventually accrete onto the AGN
itself. Evidence is found for similar non-circular kinematics of in
dividual clouds detected in absorption in nearby radio AGN (e.g.
Maccagni et al. 2014; Tremblay et al. 2016; Maccagni et al. 2018).


_4.1.4_ _A low-metallicity cloud in the tidal stream?_


Alternatively, this narrow component of the H I line may arise in
atomic gas that has physically distinct properties to that of the
broader H I and CO absorption. In their 21-cm absorption survey
of quasar-galaxy pairs using the Green Bank Telescope and Jansky
Very Large Array, Borthakur et al. (2011, 2014) report a similarly
deep ( _τ_ _∼_ 1 _._ 37) and narrow (∆ _v_ _∼_ 1 _._ 1 km s _[−]_ [1] ) H I absorption
line in UCG 7408, a low-metallicity ([O _/_ H] _≈−_ 0 _._ 4) dwarf galaxy
towards the background quasar J122106.854+454852.16. The line
width is consistent with cold-phase atomic gas with a kinetic temperature upper limit of _T_ k ≲ 26 K, much lower than is typically
measured for CNM clouds in the Milky Way ( _T_ k _∼_ 60 K; e.g.
Heiles & Troland 2003; Murray et al. 2018). This is also seen in
well-studied low-metallicity environments in the local Universe;
for example in both the Large (e.g. Dickey et al. 1994; MarxZimmer et al. 2000) and Small Magellanic Clouds (e.g. Dickey
et al. 2000) where CNM temperatures are typically _T_ k ≲ 40 K.
It is therefore possible that the absence of [12] CO (2-1) absorption
associated with the narrow H I absorption in PKS B1740 _−_ 517 is
the result of the gas having lower metallicity than that seen in the
broader absorption. Lower gas-phase metallicity produces fewer
dust grains to catalyse H 2 formation and shield the molecular gas
from the background UV radiation field, thereby requiring a higher
column density of cold atomic gas to self-shield the molecular gas.
Our estimate of the H I column density of CNM that gives rise to
the narrow absorption line would require a metallicity that is approximately an order of magnitude lower than solar for H 2 not to
form (Krumholz et al. 2009). This is a lower limit since the relative
abundance of CO to H 2 is known to decrease strongly as a function
of metallicity (e.g. Wolfire et al. 2010; Bolatto et al. 2013).
Could this lower metallicity gas be external to the host galaxy
of PKS B1740 _−_ 517? In Figure 1 we see possible evidence of an
ongoing tidal interaction between the radio galaxy and at least
one candidate companion galaxy, including a possible tidal stream.
The radial velocity of one companion in the AGN rest frame is
∆ _v_ _≈−_ 220 km s _[−]_ [1], consistent with cosmological N-body simulations of an interacting central galaxy and low-mass satellite with a
combined stellar mass of _M_ _∗_ _∼_ 5 _×_ 10 [10] M _⊙_ (Moreno et al. 2013).


MNRAS **000**, 1–16 (2017)

_Cold gas feeding an interacting young radio galaxy_ 11



The similarity in direction and magnitude of the radial velocities of
the companion and the narrow H I line suggests that we may be seeing absorption through a cold atomic structure within the gas that
forms a stream between the two galaxies. It is therefore possible
that the absence of CO absorption associated with the narrow H I

_−_
absorption in PKS B1740 517 is evidence for low metallicity gas
that is being tidally stripped from a companion satellite galaxy.
We note that a dense H I structure in the outskirts of the host

galaxy (see e.g. Bland-Hawthorn et al. 2017) could also lack CO
gas as a natural consequence of the metallicity gradient. However,
the observed radial velocity of this structure with respect to the
compact radio source would mean that it is distinctly non-circular
at these large radii (see Figure 5), indicating a tidal interaction either way. In future, more sensitive optical spectroscopy of the tidal
feature seen in the Gemini image would enable stronger constraints
to be made on the kinematics of the ionised gas both in the candidate companion and tidal bridge, enabling stronger tests of these
scenarios. Furthermore, observations of the cold gas at higher spatial resolution using an extended configuration of ALMA, and very
long baseline interferometry at 21-cm wavelengths, would enable
better determination of the geometry of the absorbing gas with respect to the radio source.


**4.2** **Evidence for a young radio AGN**


Data from our ALMA observations at 150 GHz and the ALMA

calibrator catalogue at 97.4 GHz (Van Kempen et al. 2014) allow
us to determine the spectral energy distribution (SED) of the radio continuum well above the peak frequency, from which we can
estimate the spectral age of the radio galaxy. Furthermore, we can
use the high frequency end of the radio SED to confirm whether
the source has a compact double (i.e consistent steep-spectrum behaviour from the lobes and hot spots) or core-jet morphology (a flat
spectrum component).
In Figure 7 we show the integrated SED at radio wavelengths,
which is typical of a compact GPS source (∆ _d_ ≲ 1 kpc) exhibiting optically thick and thin synchrotron emission above and below
_ν_ _∼_ 1 GHz, respectively (see O’Dea 1998). The ALMA data show
a clear break from a single synchrotron power-law at _ν_ ≳ 20 GHz,
from which we conclude that both components identified by King
(1994) are probably associated with the hot spots and lobes of
a compact double source. We model the SED using the following parameterisation of Moffet (1975), adapted to include a highfrequency spectral break that accounts for synchrotron aging with
continuous injection of new electrons (Kardashev 1962; Murgia
2003),



10 [1]


10 [0]


10 _[−]_ [1]


10 _[−]_ [2]









� _−α_ tk _−α_ tn �



_−α_ tk 1 _−_ e _−_ � _νν_ p
�
�



_,_ if _ν_ _≤_ _ν_ br



10 [2] 10 [3] 10 [4] 10 [5]

_⌫_ [MHz]


**Figure** **7.** The integrated SED of PKS B1740 _−_ 517 at radio wavelengths,
compiled using our data and those in the literature. The frequency axis
is given in the observer rest frame. The dashed line denotes a best-fitting
model that includes optically thick and thin power-law spectra, and a
continuous-injection break at frequencies higher than 16 GHz. References
for the data: Hur17 – Hurley-Walker et al. (2017); Jac11 – Jacobs et al.
(2011); Int17 – Intema et al. (2017); Lar81 – Large et al. (1981); Cam94 –
Campbell-Wilson & Hunstead (1994); Mau03 – Mauch et al. (2003); Tin03
– Tingay et al. (2003); Wal75 – Wall et al. (1975); Mas08 – Massardi et al.
(2008); Wri94 – Wright et al. (1994); McC12 – McConnell et al. (2012);
Gregory et al. (1994) – Gre94; Hea07 – Healey et al. (2007); Ric06 – Ricci
et al. (2006); Lop07 – López-Caniego et al. (2007); Pla11 – Planck Collaboration VII (2011); Kem14 – Van Kempen et al. (2014)


typically shallower than the theoretical value predicted for homogeneous self-absorption ( _α_ tk = 2 _._ 5; e.g. Kellermann & PaulinyToth 1981) and differences are attributed to either clumpy selfabsorption or free-free absorption from a foreground inhomogeneous medium. At frequencies above the spectral peak, the optically thin spectral index is consistent with the canonical injection
index of _α_ in = _−_ 0 _._ 7.
We estimate the age of the source using the following relationship (e.g. Murgia 2003),


_t_ syn = 5 _._ 03 _×_ 10 [4] _B_ _[−]_ [1] _[.]_ [5] [(1 + _z_ ) _ν_ br ] _[−]_ [0] _[.]_ [5] yr _,_ (14)


where _B_ is the magnetic field flux density in mG and _ν_ br is the
break frequency in GHz. Assuming equipartition of the cosmic ray
and magnetic field energy densities, equal energy densities of electrons and protons, and source component sizes of ∆ _θ_ _∼_ 10 mas,
we estimate a magnetic flux density of _B_ _∼_ 3 _._ 4 mG. This gives an
approximate spectral age for the source of _t_ syn _∼_ 1600 yr. We note
this estimate of the source age involves several assumptions, including magnetic field uniformity, equipartition, and electron mixing (see e.g. Tribble 1993; Jones et al. 1999; Blundell & Rawlings
2000), and should therefore be considered a useful order of magnitude measurement of the source age. The linear separation of the
source components (∆ _d_ src _∼_ 300 pc) implies an expansion velocity of _v_ exp _∼_ 0 _._ 3 c, which is consistent with the distribution
of directly measured velocities in the literature (see e.g. de Vries
et al. 2009 and references therein). Since the unresolved emission
could be dominated by the younger hot spots, we caution that the
source may be older than our estimate based on the integrated SED.
However, in the case of intrinsically compact radio sources such as
PKS1740 _−_ 517, estimates of the age from spectral modeling are



_S_ ( _ν_ ) =







_S_ p _ν_
1 _−_ e _[−]_ [1] � _ν_ p



_S_ ( _ν_ br ) � _νν_ br



_α_ tn _−_ 0 _._ 5
_,_ otherwise
�



(13)


where _v_ p and _v_ br are the peak and break frequencies, _α_ tk and _α_ tn
are the optically thick and thin spectral indices, and _S_ p is the peak
flux density.
Least squares fitting gives _v_ p = 786 MHz, _v_ br = 16 GHz,
_α_ tk = 1 _._ 4, _α_ tn = _−_ 0 _._ 71, and _S_ p = 8 _._ 1 Jy. The optically thick
spectral index is consistent with the distribution seen in samples of
other peaked-spectrum radio sources (e.g. Callingham et al. 2017;
Snellen et al. 1998; O’Dea 1998; de Vries et al. 1997). These are


MNRAS **000**, 1–16 (2017)

12 _J. R. Allison et al._


typically consistent to within an order of magnitude with estimates
from hot spot advancement (see e.g. Murgia 2003). Therefore the
uncertainty in source age is unlikely to affect our conclusions about
the relative timescales for the galaxy interaction and AGN triggering.
The flux density data shown in Figure 7 span more than 30 yr
of observations, and are therefore potentially subject to both intrinsic source variability and external propagation processes, such
as Galactic interstellar scintillation or relative motion of an inho
mogeneous medium at the source. PKS B1740 _−_ 517 is an intrinsically compact double radio source with no evident Doppler beaming. Such “galaxy-type” peaked-spectrum sources (as opposed to
“quasar-type”; Snellen et al. 1998) typically exhibit low levels of
variability less than 10 per cent on year timescales (see e.g. O’Dea
1998; Jauncey et al. 2003; Liu et al. 2009; Orienti et al. 2010). Intrinsic variability at this level could be due to adiabatic expansion of
the self-absorbed young source as it advances through the interstellar medium of the host galaxy (Stanghellini et al. 1997; Orienti et al.
2010, see also Tingay et al. 2015). In the case of PKS B1740 _−_ 517,
Gaensler & Hunstead (2000) carried out a time series analysis of
observations at 843 MHz spanning almost 10 yr with the Molongolo Observatory Synthesis Telescope, detecting variability at the
level of _∼_ 6 _._ 3 per cent over a characteristic time scale _∼_ 6 _._ 8 yr.
At higher frequencies above the turnover, King (1994) and Jauncey
et al. (2003) report a systematic decrease in flux density at 2.3 GHz
of _∼_ 1 Jy (16 per cent) over almost 2 yr of observations with the
Mount Pleasant 26-m telescope. At 8.4 GHz they did not find evidence of changes in the flux density at a similar level.
In Table 2 we give the total continuum flux density of
PKS B1740 _−_ 517 measured from each observation with ASKAP.

The standard deviation as a fraction of the median is 8.4 per cent.
Although this is consistent with the previously measured low level
variability in this source, it is possible that these variations are the
result of relative changes in antenna gain between observations of
the calibrator PKS B1934 _−_ 638 and PKS B1740 _−_ 517. We test for

this by measuring the standard deviation in flux density for other
point sources within the same field. We choose sources that have a
flux density greater than 30 times their local image RMS, so that we
can detect any systematic behaviour in flux density at the level of
_∼_ 10 per cent. We only select those sources that are located within
the full width at half power of the PAF beam, thus avoiding any
error contribution associated with sources at the edge of an imperfectly formed PAF beam. We obtain a median standard deviation of
_⟨σ⟩_ = 10 _._ 2 _±_ 1 _._ 4 per cent and a median correlation coefficient with
the PKS B1740 _−_ 517 flux density of _⟨ρ⟩_ = 0 _._ 5 _±_ 0 _._ 1, indicating
that systematic errors in the flux density are a significant component of the variance. This is consistent with the error estimated by
Bhandari et al. (2018) for their ASKAP pilot survey for transients
and variables. In conclusion, the emission from PKS B1740 _−_ 517
may vary at the level of ≲ 10 per cent over timescales of a few
years, but this is not sufficient to affect our conclusions about its
spectral behaviour, morphology or age.


**5** **DISCUSSION**


**5.1** **PKS B1740** _−_ **517 - triggered by an interaction?**


PKS B1740 _−_ 517 is a distant young radio galaxy that seems to be
undergoing at least one tidal interaction with a lower-mass satellite
galaxy. We see evidence for a reservoir of cold atomic and molecular gas distributed in an inner disc or ring and a distinct diffuse



atomic gas cloud that appears to have different kinematics, and possibly physical properties, to that of the settled gas. This gas could
have accreted onto the host galaxy during tidal interaction with a
gas-rich lower-mass companion. The difference in physical properties could be the result of the location of the absorbing gas, where
star formation and gas mixing towards the centre of the host galaxy
could act to enrich the accreted gas.
The luminosity of the [O II ] _λ_ 3727 line in the companion
spectrum is _L_ [OII] _≈_ 1 _._ 9 _×_ 10 [40] erg s _[−]_ [1], which using Equation 12 (Kewley et al. 2004) gives a star formation rate of SFR _≈_
0 _._ 13 M _⊙_ yr _[−]_ [1] . This implies that the companion galaxy has sufficient gas mass ( _M_ gas _∼_ 10 [8] M _⊙_ ) to supply that detected in the
host galaxy of PKS B1740 _−_ 517. The dynamical timescale for the
interaction (based on the projected separation and relative radial
velocity) is significantly longer than the age of the AGN ( _t_ dyn _∼_
5 _×_ 10 [7] yr), implying that the gas accreted onto the host galaxy
well before the most recent episode of activity and may have been
prevented from fuelling the AGN by a burst of star formation that
has only recently been quenched.
This scenario is strikingly similar to that seen in the radio galaxy MRC B1221 _−_ 423, a young ( _t_ _∼_ 10 [5] yr) compact
steep spectrum (CSS) source that appears to be undergoing a
minor merger with a companion galaxy (Johnston et al. 2005).
Since this source is at a lower redshift ( _z_ = 0 _._ 1706; Simpson et al. 1993), and is older and therefore more extended than
PKS B1740 _−_ 517, radio imaging reveals a highly distorted morphology including a 180 _[◦]_ bent jet that is possibly due to interaction
with a highly dense medium (Johnston et al. 2010). The neutral gas
in MRC B1221 _−_ 423 (seen in H I absorption against the radio continuum) appears to be infalling towards the nucleus at a velocity
of _∼_ 250 km s _[−]_ [1] . In their IFU study of this radio galaxy, Anderson et al. (2013) find several stellar populations of different ages,
associated with dynamically unstable gas during successive periapses of the companion orbit. The radio source was triggered about
100 Myr after the most recent closest approach, indicating that this
is the timescale for gas to be able to sink to the nucleus. We suggest that a similar scenario may have occurred in the host galaxy
PKS B1740 _−_ 517, whereby we are seeing the activity from the most
recent periapsis and accretion of gas. A future resolved study of the
ionised emission from PKS B1740 _−_ 517 and its companion using
the NIRSpec IFU on the James Webb Space Telescope (Purll et al.
2017) would confirm this interpretation.
This sequence and timescale of events is consistent with that
seen for minor mergers in massive early type galaxies at lower
redshifts; in a study of 25 nearby dust-lane-selected early-types,
Shabala et al. (2017) find that those with radio-loud AGN tend to
have older star burst ages and lower star formation rates, pointing to
delayed onset of black hole accretion following the merger. More
generally, emission-line AGN are found to host on average stellar populations that are a few hundred Myr older than their more
vigorously star forming counterparts (e.g. Schawinski et al. 2007;
Wild et al. 2010). Furthermore, the prevalence of highly accreting
AGN identified in galaxies pairs and mergers is also found to peak
amongst those that are either post-merger or in the closest pairs, occurring later in the interaction than the onset of star formation (Ellison et al. 2013). PKS B1740 _−_ 517 is a rare example of the early
stage in a brief active phase of a massive early type galaxy that is
triggered by interactions and minor mergers with smaller companions. If this is the most recent event then it is possible that older
AGN activity may have been triggered by previous orbits of the
companion. We propose that radio emission from such recurrent
activity could be detected using new low-frequency radio arrays at


MNRAS **000**, 1–16 (2017)

_Cold gas feeding an interacting young radio galaxy_ 13



high surface brightness sensitivity, for the example the Murchison
Widefield Array (MWA; Tingay et al. 2013; Bowman et al. 2013)
and in the future SKA-Low.


**5.2** **Molecular absorption in distant radio galaxies**


Finding molecular absorption lines at cosmological distances is an
important probe of the physical conditions and chemistry of cold
gas in the ISM of galaxies at earlier epochs (e.g. Henkel et al.
2005; Bottinelli et al. 2009; Muller et al. 2014). In addition to their
importance as a tool for determining the role of the neutral ISM
in galaxy evolution, absorption lines also provide a useful independent means of determining key parameters in cosmology and
fundamental physics. If several species are detected under conditions where the excitation is determined by the cosmic microwave
background (CMB) radiation, then their relative strength can be
used to independently determine the CMB temperature at that redshift (Wiklind & Combes 1997; Muller et al. 2013). Furthermore,
comparison of the redshifts of several lines within the same absorber can be used to examine possible cosmological evolution of
the electron to proton mass ratio, the fine structure constant and the
proton gyromagnetic ratio (e.g. Wiklind & Combes 1997; Murphy
et al. 2001; Darling 2003; Murphy et al. 2008; Kanekar 2011; Curran et al. 2011b; Ellingsen et al. 2012; Kanekar et al. 2012, 2015,
2018, see also the review by Curran et al. 2004), thereby testing
fundamental physics.
Surveys for molecular absorption lines in the spectra of bright
radio sources should be observationally efficient at finding cold
molecular gas in galaxies at cosmologically significant distances.
This is principally due to absorption being observable at any luminosity distance, provided there exists a sufficiently bright background source of emission. However, in practice molecular absorption has proven to be relatively difficult to detect at redshifts
much beyond _z_ _∼_ 0 _._ 1. Including this work, only six molecular
absorbers have been detected at cosmological distances. Only one
of these was discovered in a genuinely blind search for molecular absorption (PKS B1830 _−_ 211; Wiklind & Combes 1996b), and
subsequent searches (e.g. Kanekar et al. 2014) have not yielded
detections. The key limiting factor is thought to be impact parameter, because the molecular component of the ISM is more centrally
concentrated than atomic gas in galaxies. This interpretation is certainly borne out in the detected systems; three are intrinsic to the

_−_
host galaxy of the radio source: PKS B1740 517 at z = 0.441 (this
work), PKS B1413+135 at _z_ = 0 _._ 247 (Wiklind & Combes 1994,
1997), and B1504+377 at _z_ = 0 _._ 685 (Wiklind & Combes 1996a).
The three intervening absorbers were all found to have sufficiently
low impact parameter that they gravitationally lens the background
quasar: B0218+357 at _z_ = 0 _._ 685 (Wiklind & Combes 1995),
PKS B1830 _−_ 211 at _z_ = 0 _._ 886 (Wiklind & Combes 1996b, 1998;
Muller et al. 2014) and PKS B0132 _−_ 097 at _z_ = 0 _._ 765 (Kanekar
et al. 2005; Wiklind et al. 2018).
Careful selection of targets is therefore key to detecting more
molecular absorbers at cosmological distances. The host galaxies
of compact steep spectrum and GPS radio sources, with existing
detections of cold gas through H I 21-cm absorption, are one possible avenue of investigation. Of the three known intrinsic molecular absorbers, PKS B1740 _−_ 517 and PKS B1413+135 have an intrinsically compact source morphology. These sources are intrinsically compact and therefore should not extend beyond the stellar
disc of their host (O’Dea 1998), increasing the probability of detecting line-of-sight molecular gas in absorption. Of course these
radio galaxies are not representative of the normal galaxy popula

MNRAS **000**, 1–16 (2017)



tion and therefore any conclusions drawn about the molecular gas
content should be considered in the context of their hosts. Several

surveys are planned to carry out wide-field blind searches for H I
21-cm absorption with pathfinder telescopes to the Square Kilometre Array (SKA). A summary of these in the context of intrinsic
absorption is provided by Morganti & Oosterloo (2018) (see also
Maccagni et al. 2017), and include the First Large Absorption Survey in HI with ASKAP (e.g. Johnston et al. 2007; Allison et al.
2016), the MeerKAT Absorption Line Survey (Gupta et al. 2016),
the MeerKAT International GHz Tiered Extragalactic Exploration
(MIGHTEE) Survey (Jarvis et al. 2017), and the Search for H I Absorption with AperTIF (e.g. Oosterloo et al. 2009). Together, these
surveys are expected to detect H I absorption in the host galaxies of
several thousand radio sources, spanning redshifts from the nearby
Universe to _z_ _∼_ 1 _._ 44. Although this seems promising, confined
and/or young radio sources typically have steep spectral indices
( _α_ _∼−_ 1), meaning that their flux density at 200 GHz can be two
orders of magnitude lower than at 1 GHz. In order to detect molecular absorption with an observed optical depth _τ_ _∼_ 0 _._ 1 within a
reasonable observing time with ALMA we require the source to be
brighter than _S_ 200 GHz _∼_ 10 mJy at 200 GHz, which corresponds
to _S_ 1 GHz _∼_ 1 Jy at 1 GHz. The proportion of detected H I absorbers with a radio continuum brighter than 1 Jy is expected to
be _∼_ 1 per cent (e.g. Condon et al. 1998; Mauch et al. 2003) of
which _∼_ 10 _−_ 30 per cent will be intrinsically compact and young
radio galaxies (e.g. O’Dea 1998). Although this means that only
a few detections with these surveys will provide useful targets for
molecular absorption line detection, this will greatly improve the
existing sample of high redshift systems currently known.


**6** **CONCLUSIONS**


Using ALMA we have detected a rare example of [12] CO (2-1) absorption at _z_ = 0 _._ 44 in the host galaxy of the luminous GPS radio
source PKS B1740 _−_ 517. Comparison of the CO and H I absorption
line profiles suggests that the CO is distributed in a more clumpy
medium of dense clouds while the H I seems to be more consistent

with larger diffuse structures. We argue that the broader atomic and
molecular absorption lines arise from a central reservoir of cold gas
( _M_ gas _∼_ 10 [7] _−_ 10 [8] _M_ _⊙_ ), likely distributed as a disc or ring within
a few kiloparsecs of the active nucleus. A separate kinematicallydistinct deep ( _τ_ peak ≳ 0 _._ 2) and narrow (∆ _v_ FWHM ≲ 5 km s _[−]_ [1] )
H I absorption line is consistent with a single diffuse cold atomic
structure ( _T_ k _∼_ 100 K). The absence of molecular gas suggests that
either this structure is much smaller than 100 pc along our line-ofsight and/or that it arises from lower metallicity gas, perhaps from
a companion galaxy.
Examination of optical imaging and spectroscopy from previous observations by A15 with the Gemini-South telescope reveal
at least one candidate lower-mass companion galaxy that appears
to be undergoing a tidal interaction. The dynamical timescale for
this interaction is approximately 50 Myr, implying that the onset of
the radio AGN, which we estimate to be only _∼_ 1600 yr old, is delayed with respect to the bulk accretion of gas from the companion.
This is consistent with previous studies of the relative timescales
of mergers, star formation and AGN triggering in massive galaxies.
PKS B1740 _−_ 517 is a luminous and young radio galaxy that provides a rare opportunity to study the cold gas content of massive
early type galaxies at cosmological distances. Future surveys for
H I 21-cm absorption will provide further targets for follow up ob

14 _J. R. Allison et al._


servations with ALMA, but will require careful selection based on
the morphology and spectral behaviour of the source.


**ACKNOWLEDGEMENTS**


We thank the anonymous referee for their careful comments that
helped improve the clarity of this paper. JRA acknowledges support from a Christ Church Career Development Fellowship. Parts
of this research were conducted by the Australian Research Council Centre of Excellence for All-sky Astrophysics in 3D (ASTRO
3D) through project number CE170100013. The National Radio
Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2015.1.00808.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ.

The Australian SKA Pathfinder is part of the Australia Telescope National Facility which is managed by CSIRO. Operation
of ASKAP is funded by the Australian Government with support
from the National Collaborative Research Infrastructure Strategy.
Establishment of the Murchison Radio-astronomy Observatory was
funded by the Australian Government and the Government of Western Australia. ASKAP uses advanced supercomputing resources at
the Pawsey Supercomputing Centre. We acknowledge the Wajarri
Yamatji people as the traditional owners of the Observatory site.
We have made use of A STROPY, a community-developed
core P YTHON package for astronomy (Astropy Collaboration et al.
2013); the NASA/IPAC Extragalactic Database (NED) and Infrared
Science Archive (IRSA), which are operated by the Jet Propulsion
Laboratory, California Institute of Technology, under contract with
the National Aeronautics and Space Administration; NASA’s Astrophysics Data System Bibliographic Services; and the VizieR catalogue access tool operated at CDS, Strasbourg, France.


**REFERENCES**


[Aditya J. N. H. S., Kanekar N., 2018, MNRAS, 473, 59](http://dx.doi.org/10.1093/mnras/stx2325)
Aditya J. N. H. S., Kanekar N., Prochaska J. X., Day B., Lynam P., Cruz J.,
[2017, MNRAS, 465, 5011](http://dx.doi.org/10.1093/mnras/stw3105)
Allen S. W., Dunn R. J. H., Fabian A. C., Taylor G. B., Reynolds C. S.,
[2006, MNRAS, 372, 21](http://dx.doi.org/10.1111/j.1365-2966.2006.10778.x)

[Allison J. R., et al., 2015, MNRAS, 453, 1249](http://dx.doi.org/10.1093/mnras/stv1532)

[Allison J. R., Zwaan M. A., Duchesne S. W., Curran S. J., 2016, MNRAS,](http://dx.doi.org/10.1093/mnras/stw1722)


[462, 1341](http://adsabs.harvard.edu/abs/2016MNRAS.462.1341A)

[Allison J. R., et al., 2017, MNRAS, 465, 4450](http://dx.doi.org/10.1093/mnras/stw2860)

[Anderson C. S., Johnston H. M., Hunstead R. W., 2013, MNRAS, 431, 3269](http://dx.doi.org/10.1093/mnras/stt406)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Bahcall J. N., Ekers R. D., 1969, ApJ, 157, 1055](http://dx.doi.org/10.1086/150135)
[Best P. N., Heckman T. M., 2012, MNRAS, 421, 1569](http://dx.doi.org/10.1111/j.1365-2966.2012.20414.x)

[Bhandari S., et al., 2018, MNRAS, 478, 1784](http://dx.doi.org/10.1093/mnras/sty1157)
Biggs A. D., Zwaan M. A., Hatziminaoglou E., Péroux C., Liske J., 2016,

[MNRAS, 462, 2819](http://dx.doi.org/10.1093/mnras/stw1786)
Bland-Hawthorn J., Maloney P. R., Stephens A., Zovaro A., Popping A.,
[2017, ApJ, 849, 51](http://dx.doi.org/10.3847/1538-4357/aa8f45)
[Blundell K. M., Rawlings S., 2000, AJ, 119, 1111](http://dx.doi.org/10.1086/301254)
[Bolatto A. D., Wolfire M., Leroy A. K., 2013, AR&A, 51, 207](http://dx.doi.org/10.1146/annurev-astro-082812-140944)
[Bondi H., 1952, MNRAS, 112, 195](http://dx.doi.org/10.1093/mnras/112.2.195)



Borthakur S., Tripp T. M., Yun M. S., Bowen D. V., Meiring J. D., York
[D. G., Momjian E., 2011, ApJ, 727, 52](http://dx.doi.org/10.1088/0004-637X/727/1/52)
Borthakur S., Momjian E., Heckman T. M., York D. G., Bowen D. V., Yun
[M. S., Tripp T. M., 2014, ApJ, 795, 98](http://dx.doi.org/10.1088/0004-637X/795/1/98)
[Bottinelli S., et al., 2009, ApJL, 690, L130](http://dx.doi.org/10.1088/0004-637X/690/2/L130)
[Bowman J. D., et al., 2013, PASA, 30, e031](http://dx.doi.org/10.1017/pas.2013.009)

[Braun R., 2012, ApJ, 749, 87](http://dx.doi.org/10.1088/0004-637X/749/1/87)
[Braun R., Thilker D. A., Walterbos R. A. M., Corbelli E., 2009, ApJ, 695,](http://dx.doi.org/10.1088/0004-637X/695/2/937)

[937](http://adsabs.harvard.edu/abs/2009ApJ...695..937B)

[Burgess A. M., Hunstead R. W., 2006, AJ, 131, 114](http://dx.doi.org/10.1086/498679)
[Burgh E. B., France K., McCandliss S. R., 2007, ApJ, 658, 446](http://dx.doi.org/10.1086/511259)
[Callingham J. R., et al., 2017, ApJ, 836, 174](http://dx.doi.org/10.3847/1538-4357/836/2/174)
Campbell-Wilson D., Hunstead R. W., 1994, Proc. of the Astro. Soc. Aust.,

[11, 33](http://adsabs.harvard.edu/abs/1994PASAu..11...33C)

[Carilli C. L., Menten K. M., Reid M. J., Rupen M. P., Yun M. S., 1998, ApJ,](http://dx.doi.org/10.1086/305191)

[494, 175](http://adsabs.harvard.edu/abs/1998ApJ...494..175C)

[Chandra S., Maheshwari V. U., Sharma A. K., 1996, A&A, 117, 557](http://adsabs.harvard.edu/abs/1996A%26AS..117..557C)

Chippendale A. P., et al., 2015, in 2015 International Conference on Electromagnetics in Advanced Applications (ICEAA). IEEE, pp 541 – 544
[(arXiv:1509.00544)](http://arxiv.org/abs/1509.00544)
Condon J. J., Cotton W. D., Greisen E. W., Yin Q. F., Perley R. A., Taylor
[G. B., Broderick J. J., 1998, AJ, 115, 1693](http://dx.doi.org/10.1086/300337)

[Croton D. J., et al., 2006, MNRAS, 365, 11](http://dx.doi.org/10.1111/j.1365-2966.2005.09675.x)

[Curran S. J., Whiting M. T., 2010, ApJ, 712, 303](http://dx.doi.org/10.1088/0004-637X/712/1/303)
Curran S. J., Kanekar N., Darling J. K., 2004, New [Astronomy](http://dx.doi.org/10.1016/j.newar.2004.09.004) Reviews,

[48, 1095](http://adsabs.harvard.edu/abs/2004NewAR..48.1095C)

[Curran S. J., et al., 2011a, MNRAS, 413, 1165](http://dx.doi.org/10.1111/j.1365-2966.2011.18209.x)

Curran S. J., Tanna A., Koch F. E., Berengut J. C., Webb J. K., Stark A. A.,
[Flambaum V. V., 2011b, A&A, 533, A55](http://dx.doi.org/10.1051/0004-6361/201117457)

[Curran S. J., Whiting M. T., Sadler E. M., Bignell C., 2013, MNRAS, 428,](http://dx.doi.org/10.1093/mnras/sts171)
[2053](http://adsabs.harvard.edu/abs/2013MNRAS.428.2053C)

[Darling J., 2003, Physical Review Letters, 91, 011301](http://dx.doi.org/10.1103/PhysRevLett.91.011301)
[Dasyra K. M., Combes F., 2012, A&A, 541, L7](http://dx.doi.org/10.1051/0004-6361/201219229)
[David L. P., et al., 2014, ApJ, 792, 94](http://dx.doi.org/10.1088/0004-637X/792/2/94)
[Davis T. A., et al., 2013, MNRAS, 429, 534](http://dx.doi.org/10.1093/mnras/sts353)

[Davis T. A., et al., 2015, MNRAS, 449, 3503](http://dx.doi.org/10.1093/mnras/stv597)

[Delvecchio I., et al., 2017, A&A, 602, A3](http://dx.doi.org/10.1051/0004-6361/201629367)

Dickey J. M., Mebold U., Marx M., Amy S., Haynes R. F., Wilson W., 1994,
[A&A, 289, 357](http://adsabs.harvard.edu/abs/1994A%26A...289..357D)

Dickey J. M., Mebold U., Stanimirovic S., Staveley-Smith L., 2000, [ApJ,](http://dx.doi.org/10.1086/308953)

[536, 756](http://adsabs.harvard.edu/abs/2000ApJ...536..756D)

[Dutta R., Gupta N., Srianand R., O’Meara J. M., 2016, MNRAS, 456, 4209](http://dx.doi.org/10.1093/mnras/stv2980)
Ellingsen S. P., Voronkov M. A., Breen S. L., Lovell J. E. J., 2012, [ApJL,](http://dx.doi.org/10.1088/2041-8205/747/1/L7)

[747, L7](http://adsabs.harvard.edu/abs/2012ApJ...747L...7E)

Ellison S. L., Patton D. R., Mendel J. T., Scudder J. M., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.19624.x)


[418, 2043](http://adsabs.harvard.edu/abs/2011MNRAS.418.2043E)

Ellison S. L., Mendel J. T., Patton D. R., Scudder J. M., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt1562)


[435, 3627](http://adsabs.harvard.edu/abs/2013MNRAS.435.3627E)

[Fabian A. C., 1999, MNRAS, 308, L39](http://dx.doi.org/10.1046/j.1365-8711.1999.03017.x)

Fey A., Gordon G., Jacobs C., eds, 2009, The Second Realization of the International Celestial Reference Frame by VLBI, IERS Technical Notes
35. Verlad des Bundesamts fur Kartographie und Geodasie, Frankfurt

am Main

[Gaensler B. M., Hunstead R. W., 2000, PASA, 17, 72](http://dx.doi.org/10.1071/AS00072)

[Gaspari M., Ruszkowski M., Oh S. P., 2013, MNRAS, 432, 3401](http://dx.doi.org/10.1093/mnras/stt692)
Gibson S. J., Taylor A. R., Higgs L. A., Brunt C. M., Dewdney P. E., 2005,

[ApJ, 626, 195](http://dx.doi.org/10.1086/429870)
Gregory P. C., Vavasour J. D., Scott W. K., Condon J. J., 1994, [ApJS,](http://dx.doi.org/10.1086/191862) [90,](http://adsabs.harvard.edu/abs/1994ApJS...90..173G)

[173](http://adsabs.harvard.edu/abs/1994ApJS...90..173G)

Gupta N., Srianand R., Petitjean P., Bergeron J., Noterdaeme P., Muzahid
[S., 2012, A&A, 544, A21](http://dx.doi.org/10.1051/0004-6361/201219159)

Gupta N., et al., 2016, in Proceedings of MeerKAT Science: On the
Pathway to the SKA. 25-27 May, 2016 Stellenbosch, South Africa
[(MeerKAT2016). p. 14 (arXiv:1708.07371)](http://arxiv.org/abs/1708.07371)
[Gupta N., et al., 2018, MNRAS, 476, 2432](http://dx.doi.org/10.1093/mnras/sty384)
[Hardcastle M. J., Evans D. A., Croston J. H., 2007, MNRAS, 376, 1849](http://dx.doi.org/10.1111/j.1365-2966.2007.11572.x)

[Hay S. G., O’Sullivan J. D., 2008, Radio Sci., 43, 6](http://dx.doi.org/10.1029/2007RS003798)


MNRAS **000**, 1–16 (2017)

_Cold gas feeding an interacting young radio galaxy_ 15



Healey S. E., Romani R. W., Taylor G. B., Sadler E. M., Ricci R., Murphy
[T., Ulvestad J. S., Winn J. N., 2007, ApJS, 171, 61](http://dx.doi.org/10.1086/513742)
[Heckman T. M., Best P. N., 2014, ARA&A, 52, 589](http://dx.doi.org/10.1146/annurev-astro-081913-035722)
[Heiles C., Troland T. H., 2003, ApJ, 586, 1067](http://dx.doi.org/10.1086/367828)
Helfer T. T., Thornley M. D., Regan M. W., Wong T., Sheth K., Vogel S. N.,
[Blitz L., Bock D. C.-J., 2003, ApJS, 145, 259](http://dx.doi.org/10.1086/346076)
Henkel C., Jethava N., Kraus A., Menten K. M., Carilli C. L., Grasshoff M.,

[Lubowich D., Reid M. J., 2005, A&A, 440, 893](http://dx.doi.org/10.1051/0004-6361:20052816)
[Heyer M., Dame T. M., 2015, AR&A, 53, 583](http://dx.doi.org/10.1146/annurev-astro-082214-122324)
[Heyer M., Krawczyk C., Duval J., Jackson J. M., 2009, ApJ, 699, 1092](http://dx.doi.org/10.1088/0004-637X/699/2/1092)
Holt J., Tadhunter C., Morganti R., Bellamy M., González Delgado R. M.,
[Tzioumis A., Inskip K. J., 2006, MNRAS, 370, 1633](http://dx.doi.org/10.1111/j.1365-2966.2006.10604.x)
[Holt J., Tadhunter C. N., Morganti R., 2008, MNRAS, 387, 639](http://dx.doi.org/10.1111/j.1365-2966.2008.13089.x)
[Hopkins P. F., Hernquist L., 2006, ApJS, 166, 1](http://dx.doi.org/10.1086/505753)
[Hopkins P. F., Hernquist L., Cox T. J., Kereš D., 2008, ApJS, 175, 356](http://dx.doi.org/10.1086/524362)
[Hotan A. W., et al., 2014, Publ. Astron. Soc. Aust., 31, e041](http://dx.doi.org/10.1017/pasa.2014.36)
[Hurley-Walker N., et al., 2017, MNRAS, 464, 1146](http://dx.doi.org/10.1093/mnras/stw2337)
[Intema H. T., Jagannathan P., Mooley K. P., Frail D. A., 2017, A&A, 598,](http://dx.doi.org/10.1051/0004-6361/201628536)

[A78](http://adsabs.harvard.edu/abs/2017A%26A...598A..78I)

[Ishibashi W., Fabian A. C., 2012, MNRAS, 427, 2998](http://dx.doi.org/10.1111/j.1365-2966.2012.22074.x)

Ishwara-Chandra C. H., Dwarakanath K. S., Anantharamaiah K. R., 2003,

[J. Astrophys. Astron., 24, 37](http://dx.doi.org/10.1007/BF03012190)
[Jacobs D. C., et al., 2011, ApJ, 734, L34](http://dx.doi.org/10.1088/2041-8205/734/2/L34)
[Jahnke K., Macciò A. V., 2011, ApJ, 734, 92](http://dx.doi.org/10.1088/0004-637X/734/2/92)
Jarvis M. J., et al., 2017, preprint, [(arXiv:1709.01901)](http://arxiv.org/abs/1709.01901)
[Jauncey D. L., et al., 2003, Publ. Astron. Soc. Aust., 20, 151](http://dx.doi.org/10.1071/AS03023)
[Johnston H. M., Hunstead R. W., Cotter G., Sadler E. M., 2005, MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2004.08468.x)


[356, 515](http://adsabs.harvard.edu/abs/2005MNRAS.356..515J)

[Johnston S., et al., 2007, PASA, 24, 174](http://dx.doi.org/10.1071/AS07033)
Johnston H. M., Broderick J. W., Cotter G., Morganti R., Hunstead R. W.,
[2010, MNRAS, 407, 721](http://dx.doi.org/10.1111/j.1365-2966.2010.16950.x)
[Jones T. W., Ryu D., Engel A., 1999, ApJ, 512, 105](http://dx.doi.org/10.1086/306772)
[Kanekar N., 2011, ApJL, 728, L12](http://dx.doi.org/10.1088/2041-8205/728/1/L12)
[Kanekar N., Briggs F. H., 2004, New Astron. Rev., 48, 1259](http://dx.doi.org/10.1016/j.newar.2004.09.030)
[Kanekar N., et al., 2005, Physical Review Letters, 95, 261301](http://dx.doi.org/10.1103/PhysRevLett.95.261301)
Kanekar N., Langston G. I., Stocke J. T., Carilli C. L., Menten K. M., 2012,

[ApJL, 746, L16](http://dx.doi.org/10.1088/2041-8205/746/2/L16)
[Kanekar N., Gupta A., Carilli C. L., Stocke J. T., Willett K. W., 2014, ApJ,](http://dx.doi.org/10.1088/0004-637X/782/1/56)

[782, 56](http://adsabs.harvard.edu/abs/2014ApJ...782...56K)

[Kanekar N., et al., 2015, MNRAS, 448, L104](http://dx.doi.org/10.1093/mnrasl/slu206)
[Kanekar N., Ghosh T., Chengalur J. N., 2018, Physical Review Letters, 120,](http://dx.doi.org/10.1103/PhysRevLett.120.061302)
[061302](http://adsabs.harvard.edu/abs/2018PhRvL.120f1302K)

[Kardashev N. S., 1962, Soviet Ast., 6, 317](http://adsabs.harvard.edu/abs/1962SvA.....6..317K)

[Kauffmann G., Heckman T. M., 2009, MNRAS, 397, 135](http://dx.doi.org/10.1111/j.1365-2966.2009.14960.x)

[Kauffmann G., et al., 2003, MNRAS, 346, 1055](http://dx.doi.org/10.1111/j.1365-2966.2003.07154.x)
[Kauffmann G., et al., 2007, ApJS, 173, 357](http://dx.doi.org/10.1086/516647)
[Kellermann K. I., Pauliny-Toth I. I. K., 1981, ARA&A, 19, 373](http://dx.doi.org/10.1146/annurev.aa.19.090181.002105)
[Kennicutt Jr. R. C., 1998, ApJ, 498, 541](http://dx.doi.org/10.1086/305588)
[Kewley L. J., Geller M. J., Jansen R. A., 2004, AJ, 127, 2002](http://dx.doi.org/10.1086/382723)
King E., 1994, PhD thesis, Univ. Tasmania, Hobart
[King A., 2003, ApJL, 596, L27](http://dx.doi.org/10.1086/379143)
[Kormendy J., Ho L. C., 2013, AR&A, 51, 511](http://dx.doi.org/10.1146/annurev-astro-082708-101811)
[Krumholz M. R., McKee C. F., Tumlinson J., 2009, ApJ, 693, 216](http://dx.doi.org/10.1088/0004-637X/693/1/216)
LaMassa S. M., Heckman T. M., Ptak A., Urry C. M., 2013, [ApJL,](http://dx.doi.org/10.1088/2041-8205/765/2/L33) [765,](http://adsabs.harvard.edu/abs/2013ApJ...765L..33L)

[L33](http://adsabs.harvard.edu/abs/2013ApJ...765L..33L)

[Lane W. M., Briggs F. H., Smette A., 2000, ApJ, 532, 146](http://dx.doi.org/10.1086/308578)
Large M. I., Mills B. Y., Little A. G., Crawford D. F., Sutton J. M., 1981,
[MNRAS, 194, 693](http://adsabs.harvard.edu/abs/1981MNRAS.194..693L)

[Larson R. B., 1981, MNRAS, 194, 809](http://dx.doi.org/10.1093/mnras/194.4.809)
[Li Y., Bryan G. L., 2014, ApJ, 789, 153](http://dx.doi.org/10.1088/0004-637X/789/2/153)
[Lim J., Ao Y., Dinh-V-Trung 2008, ApJ, 672, 252](http://dx.doi.org/10.1086/523664)
[Liu X., Song H.-G., Cui L., 2009, Astronomische Nachrichten, 330, 145](http://dx.doi.org/10.1002/asna.200811142)
López-Caniego M., González-Nuevo J., Herranz D., Massardi M., Sanz
[J. L., De Zotti G., Toffolatti L., Argüeso F., 2007, ApJS, 170, 108](http://dx.doi.org/10.1086/512678)
[Maccagni F. M., Morganti R., Oosterloo T. A., Mahony E. K., 2014, A&A,](http://dx.doi.org/10.1051/0004-6361/201424334)

[571, A67](http://adsabs.harvard.edu/abs/2014A%26A...571A..67M)
Maccagni F. M., Morganti R., Oosterloo T. A., Geréb K., Maddox N., 2017,

[A&A, 604, A43](http://dx.doi.org/10.1051/0004-6361/201730563)


MNRAS **000**, 1–16 (2017)



Maccagni F. M., Morganti R., Oosterloo T. A., Oonk J. B. R., Emonts
[B. H. C., 2018, A&A, 614, A42](http://dx.doi.org/10.1051/0004-6361/201732269)

Marx-Zimmer M., Herbstmeier U., Dickey J. M., Zimmer F., Staveley[Smith L., Mebold U., 2000, A&A, 354, 787](http://adsabs.harvard.edu/abs/2000A%26A...354..787M)

[Massardi M., et al., 2008, MNRAS, 384, 775](http://dx.doi.org/10.1111/j.1365-2966.2007.12751.x)

Mauch T., Murphy T., Buttery H. J., Curran J., Hunstead R. W., Piestrzynski
[B., Robertson J. G., Sadler E. M., 2003, MNRAS, 342, 1117](http://dx.doi.org/10.1046/j.1365-8711.2003.06605.x)

[McConnell D., Sadler E. M., Murphy T., Ekers R. D., 2012, MNRAS, 422,](http://dx.doi.org/10.1111/j.1365-2966.2012.20726.x)
[1527](http://cdsads.u-strasbg.fr/abs/2012MNRAS.422.1527M)

[McConnell D., et al., 2016, PASA, 33, e042](http://dx.doi.org/10.1017/pasa.2016.37)

McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, ASP Conf. Ser. Vol. 376, Astronomical
Data Analysis Software and Systems XVI. Astron. Soc. Pac., San Francisco, p. 127
[McNamara B. R., et al., 2014, ApJ, 785, 44](http://dx.doi.org/10.1088/0004-637X/785/1/44)
[Meidt S. E., et al., 2014, ApJ, 788, 144](http://dx.doi.org/10.1088/0004-637X/788/2/144)
Moffet A. T., 1975, in Sandage A., Sandage M., Kristian J., eds, Stars
and Stellar Systems Vol. 9, Galaxies and the Universe. University of
Chicago Press, Chicago, p. 211
[Moore C. B., Carilli C. L., Menten K. M., 1999, ApJ, 510, L87](http://dx.doi.org/10.1086/311818)
Moreno J., Bluck A. F. L., Ellison S. L., Patton D. R., Torrey P., Moster
[B. P., 2013, MNRAS, 436, 1765](http://dx.doi.org/10.1093/mnras/stt1694)

Morganti R., Oosterloo T., 2018, preprint, [(arXiv:1807.01475)](http://arxiv.org/abs/1807.01475)
[Morganti R., Tadhunter C. N., Oosterloo T. A., 2005, A&A, 444, L9](http://dx.doi.org/10.1051/0004-6361:200500197)
Morganti R., Sadler E. M., Curran S., 2015, in Bourke T., Braun R., Fender
R. P., et al. eds, Advancing Astrophysics with the Square Kilometre
[Array (AASKA14). Proc. Sci., p. 134 (arXiv:1501.01091)](http://arxiv.org/abs/1501.01091)
[Moss V. A., et al., 2017, MNRAS, 471, 2952](http://dx.doi.org/10.1093/mnras/stx1679)

Mukherjee D., Bicknell G. V., Wagner A. Y., Sutherland R. S., Silk J., 2018,

[MNRAS,](http://dx.doi.org/10.1093/mnras/sty1776)

[Muller S., et al., 2013, A&A, 551, A109](http://dx.doi.org/10.1051/0004-6361/201220613)

[Muller S., et al., 2014, A&A, 566, A112](http://dx.doi.org/10.1051/0004-6361/201423646)

[Murgia M., 2003, Publ. Astron. Soc. Aust., 20, 19](http://dx.doi.org/10.1071/AS02033)
Murphy M. T., Webb J. K., Flambaum V. V., Drinkwater M. J., Combes F.,
[Wiklind T., 2001, MNRAS, 327, 1244](http://dx.doi.org/10.1046/j.1365-8711.2001.04843.x)

[Murphy M. T., Flambaum V. V., Muller S., Henkel C., 2008, Science, 320,](http://dx.doi.org/10.1126/science.1156352)
[1611](http://adsabs.harvard.edu/abs/2008Sci...320.1611M)

Murray C. E., Stanimirovic S., Goss W. M., Heiles C., Dickey J. M., Babler
B., Kim C.-G., 2018, preprint, [(arXiv:1806.06065)](http://arxiv.org/abs/1806.06065)
[Nulsen P. E. J., Fabian A. C., 2000, MNRAS, 311, 346](http://dx.doi.org/10.1046/j.1365-8711.2000.03038.x)

[O’Dea C. P., 1998, PASP, 110, 493](http://dx.doi.org/10.1086/316162)

Oosterloo T., Verheijen M. A. W., van Cappellen W., Bakker L., Heald G.,
Ivashina M., 2009, in Torchinsky S. A., van Ardenne A., van den BrinkHavinga T., van Es A. J. J., Faulkner A. J., eds, Wide Field Astronomy and Technology for the Square Kilometre Array. Proc. Sci., p. 70
[(arXiv:0912.0093)](http://arxiv.org/abs/0912.0093)
Oosterloo T., Raymond Oonk J. B., Morganti R., Combes F., Dasyra K.,
[Salomé P., Vlahakis N., Tadhunter C., 2017, A&A, 608, A38](http://dx.doi.org/10.1051/0004-6361/201731781)

[Orienti M., Dallacasa D., Stanghellini C., 2010, MNRAS, 408, 1075](http://dx.doi.org/10.1111/j.1365-2966.2010.17179.x)
[Ostorero L., et al., 2010, ApJ, 715, 1071](http://dx.doi.org/10.1088/0004-637X/715/2/1071)
Papadopoulos P. P., Kovacs A., Evans A. S., Barthel P., 2008, [A&A,](http://dx.doi.org/10.1051/0004-6361:200810513) [491,](http://adsabs.harvard.edu/abs/2008A%26A...491..483P)

[483](http://adsabs.harvard.edu/abs/2008A%26A...491..483P)

[Planck Collaboration VII 2011, A&A, 536, A7](http://dx.doi.org/10.1051/0004-6361/201116474)

Purll D. J., Lobb D. R., Barnes A. R., Talbot R. G., Rolt S., Robertson
D. J., Closs M. F., te Plate M., 2017, in Society of Photo-Optical
Instrumentation Engineers (SPIE) Conference Series. p. 105650J,
[doi:10.1117/12.2309221](http://dx.doi.org/10.1117/12.2309221)

Ramos Almeida C., Tadhunter C. N., Inskip K. J., Morganti R., Holt J.,
[Dicken D., 2011, MNRAS, 410, 1550](http://dx.doi.org/10.1111/j.1365-2966.2010.17542.x)

[Ramos Almeida C., et al., 2012, MNRAS, 419, 687](http://dx.doi.org/10.1111/j.1365-2966.2011.19731.x)

Reynolds J., 1994, AT Technical Document AT/39.3/040
Ricci R., Prandoni I., Gruppioni C., Sault R. J., de Zotti G., 2006, [A&A,](http://dx.doi.org/10.1051/0004-6361:20053797)

[445, 465](http://cdsads.u-strasbg.fr/abs/2006A%26A...445..465R)

Russell H. R., McNamara B. R., Edge A. C., Hogan M. T., Main R. A.,
[Vantyghem A. N., 2013, MNRAS, 432, 530](http://dx.doi.org/10.1093/mnras/stt490)
[Russell H. R., et al., 2016, MNRAS, 458, 3134](http://dx.doi.org/10.1093/mnras/stw409)

[Salomé P., et al., 2006, A&A, 454, 437](http://dx.doi.org/10.1051/0004-6361:20054745)

16 _J. R. Allison et al._


Sanders D. B., Soifer B. T., Elias J. H., Madore B. F., Matthews K., Neuge[bauer G., Scoville N. Z., 1988, ApJ, 325, 74](http://dx.doi.org/10.1086/165983)
Sault R. J., Teuben P. J., Wright M. C. H., 1995, in Shaw R. A., Payne
H. E., Hayes J. J. E., eds, ASP Conf. Ser. Vol. 77, Astronomical Data
Analysis Software and Systems IV. Astron. Soc. Pac., San Francisco,
[p. 433 (arXiv:astro-ph/0612759)](http://arxiv.org/abs/astro-ph/0612759)
Schawinski K., Thomas D., Sarzi M., Maraston C., Kaviraj S., Joo S.-J., Yi
[S. K., Silk J., 2007, MNRAS, 382, 1415](http://dx.doi.org/10.1111/j.1365-2966.2007.12487.x)
[Schlegel D. J., Finkbeiner D. P., Davis M., 1998, ApJ, 500, 525](http://dx.doi.org/10.1086/305772)
[Serra P., et al., 2012, MNRAS, 422, 1835](http://dx.doi.org/10.1111/j.1365-2966.2012.20219.x)
Shabala S. S., Deller A., Kaviraj S., Middelberg E., Turner R. J., Ting Y. S.,
[Allison J. R., Davis T. A., 2017, MNRAS, 464, 4706](http://dx.doi.org/10.1093/mnras/stw2536)
[Shankar F., Weinberg D. H., Miralda-Escudé J., 2009, ApJ, 690, 20](http://dx.doi.org/10.1088/0004-637X/690/1/20)
Siemiginowska A., Sobolewska M., Migliori G., Guainazzi M., Hardcastle
[M., Ostorero L., Stawarz Ł., 2016, ApJ, 823, 57](http://dx.doi.org/10.3847/0004-637X/823/1/57)
[Silk J., 2013, ApJ, 772, 112](http://dx.doi.org/10.1088/0004-637X/772/2/112)
[Silk J., Rees M. J., 1998, A&A, 331, L1](http://adsabs.harvard.edu/abs/1998A%26A...331L...1S)
Simpson C., Clements D. L., Rawlings S., Ward M., 1993, MNRAS, [262,](http://adsabs.harvard.edu/abs/1993MNRAS.262..889S)

[889](http://adsabs.harvard.edu/abs/1993MNRAS.262..889S)

[Skrutskie M. F., et al., 2006, AJ, 131, 1163](http://dx.doi.org/10.1086/498708)
Snellen I. A. G., Schilizzi R. T., de Bruyn A. G., Miley G. K., Rengelink
[R. B., Roettgering H. J., Bremer M. N., 1998, A&AS, 131, 435](http://dx.doi.org/10.1051/aas:1998281)
Sofia U. J., Lauroesch J. T., Meyer D. M., Cartledge S. I. B., 2004, [ApJ,](http://dx.doi.org/10.1086/382592)

[605, 272](http://adsabs.harvard.edu/abs/2004ApJ...605..272S)
[Solomon P. M., Rivolo A. R., Barrett J., Yahil A., 1987, ApJ, 319, 730](http://dx.doi.org/10.1086/165493)
Srianand R., Gupta N., Rahmani H., Momjian E., Petitjean P., Noterdaeme
[P., 2013, MNRAS, 428, 2198](http://dx.doi.org/10.1093/mnras/sts190)
Stanghellini C., Bondi M., Dallacasa D., O’Dea C. P., Baum S. A., Fanti R.,
[Fanti C., 1997, A&A, 318, 376](http://adsabs.harvard.edu/abs/1997A%26A...318..376S)
Tengstrand O., Guainazzi M., Siemiginowska A., Fonseca Bonilla N., Labi[ano A., Worrall D. M., Grandi P., Piconcelli E., 2009, A&A, 501, 89](http://dx.doi.org/10.1051/0004-6361/200811284)
Tingay S. J., Jauncey D. L., King E. A., Tzioumis A. K., Lovell J. E. J.,
[Edwards P. G., 2003, PASJ, 55, 351](http://adsabs.harvard.edu/abs/2003PASJ...55..351T)
[Tingay S. J., et al., 2013, PASA, 30, e007](http://dx.doi.org/10.1017/pasa.2012.007)
[Tingay S. J., et al., 2015, AJ, 149, 74](http://dx.doi.org/10.1088/0004-6256/149/2/74)
[Treister E., Schawinski K., Urry C. M., Simmons B. D., 2012, ApJL, 758,](http://dx.doi.org/10.1088/2041-8205/758/2/L39)

[L39](http://adsabs.harvard.edu/abs/2012ApJ...758L..39T)

[Tremblay G. R., et al., 2016, Nature, 534, 218](http://dx.doi.org/10.1038/nature17969)
[Tribble P. C., 1993, MNRAS, 261, 57](http://dx.doi.org/10.1093/mnras/261.1.57)
Tuthill J., Hampson G., Bunton J., Brown A., Neuhold S., Bateman
T., de Souza L., Joseph J., 2012, in Int. Conf. on Electromagnetics in Advanced Applications (ICEAA). IEEE, pp 1067–1070,
[doi:10.1109/ICEAA.2012.6328788](http://dx.doi.org/10.1109/ICEAA.2012.6328788)

[Ueda Y., Akiyama M., Ohta K., Miyaji T., 2003, ApJ, 598, 886](http://dx.doi.org/10.1086/378940)
[Umemura M., 2001, ApJL, 560, L29](http://dx.doi.org/10.1086/324063)
[Uson J. M., Bagri D. S., Cornwell T. J., 1991, Phys. Rev. Lett., 67, 3328](http://dx.doi.org/10.1103/PhysRevLett.67.3328)
Van Kempen T. A., et al., 2014, ALMA Memo 599
[Vermeulen R. C., et al., 2003, A&A, 404, 861](http://dx.doi.org/10.1051/0004-6361:20030468)
[Wagner A. Y., Bicknell G. V., Umemura M., 2012, ApJ, 757, 136](http://dx.doi.org/10.1088/0004-637X/757/2/136)
Wall J. V., Shimmins A. J., Bolton J. G., 1975, Aust. J. Phys. Astrophys.
[Suppl., 34, 55](http://adsabs.harvard.edu/abs/1975AuJPA..34...55W)
[Wiklind T., Combes F., 1994, A&A, 286](http://adsabs.harvard.edu/abs/1994A%26A...286L...9W)

[Wiklind T., Combes F., 1995, A&A, 299, 382](https://ui.adsabs.harvard.edu/#abs/1995A&A...299..382W)

[Wiklind T., Combes F., 1996a, A&A, 315, 86](http://adsabs.harvard.edu/abs/1996A%26A...315...86W)

[Wiklind T., Combes F., 1996b, Nature, 379, 139](http://dx.doi.org/10.1038/379139a0)

[Wiklind T., Combes F., 1997, A&A, 328, 48](http://adsabs.harvard.edu/abs/1997A%26A...328...48W)
[Wiklind T., Combes F., 1998, ApJ, 500, 129](http://dx.doi.org/10.1086/305701)
Wiklind T., Combes F., Kanekar N., 2018, preprint,
[(arXiv:1804.05377)](http://arxiv.org/abs/1804.05377)
[Wild V., Heckman T., Charlot S., 2010, MNRAS, 405, 933](http://dx.doi.org/10.1111/j.1365-2966.2010.16536.x)

[Wolfe A. M., Gawiser E., Prochaska J. X., 2005, ARA&A, 43, 861](http://dx.doi.org/10.1146/annurev.astro.42.053102.133950)
Wolfire M. G., McKee C. F., Hollenbach D., Tielens A. G. G. M., 2003,

[ApJ, 587, 278](http://dx.doi.org/10.1086/368016)
[Wolfire M. G., Hollenbach D., McKee C. F., 2010, ApJ, 716, 1191](http://dx.doi.org/10.1088/0004-637X/716/2/1191)
[Wright A. E., Griffith M. R., Burke B. F., Ekers R. D., 1994, ApJS, 91, 111](http://dx.doi.org/10.1086/191939)
[Wright E. L., et al., 2010, AJ, 140, 1868](http://dx.doi.org/10.1088/0004-6256/140/6/1868)
Yan T., Stocke J. T., Darling J., Momjian E., Sharma S., Kanekar N., 2016,

[AJ, 151, 74](http://dx.doi.org/10.3847/0004-6256/151/3/74)



[Young L. M., et al., 2011, MNRAS, 414, 940](http://dx.doi.org/10.1111/j.1365-2966.2011.18561.x)
[de Vries W. H., Barthel P. D., O’Dea C. P., 1997, A&A, 321, 105](http://adsabs.harvard.edu/abs/1997A%26A...321..105D)

de Vries N., Snellen I. A. G., Schilizzi R. T., Mack K.-H., Kaiser C. R.,

[2009, A&A, 498, 641](http://dx.doi.org/10.1051/0004-6361/200811145)

[van de Voort F., et al., 2018, MNRAS, 476, 122](http://dx.doi.org/10.1093/mnras/sty228)


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–16 (2017)


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[0]",
  "value": "What are the kinematic and physical properties of the cold molecular and atomic gas feeding the distant interacting young radio galaxy PKS B1740-517, and what is the spectral age and triggering history of the radio AGN?",
  "failed_quote": "We have used the Atacama Large Millimetre Array (ALMA) to detect a rare example of redshifted 12CO (2-1) absorption in PKS B1740 − 517, a young (t ∼ 1.6 × 10^3 yr) and luminous... radio galaxy at z = 0.44"
 },
 {
  "path": "data.bands.evidence[0]",
  "value": "Band 4 (around 146-160 GHz)",
  "failed_quote": "We centred one baseband on the expected frequency of 159.9 GHz for the redshifted 12CO (2-1) line... These were centred at sky frequencies of 146, 148, and 158 GHz"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "One baseband centred at 159.9 GHz with 3840 x 0.488 MHz channels (effective resolution ~1.8 km/s after Hanning smoothing); three continuum basebands centred at 146, 148, and 158 GHz each with 128 channels across 1875 MHz bandwidth",
  "failed_quote": "We centred one baseband on the expected frequency of 159.9 GHz for the redshifted 12CO (2-1) line, with 3840 × 0.488 MHz channels (∆v ≈ 0.9 km s−1) spanning rest-frame radial velocities in the range v ≈± 1760 km s−1."
 },
 {
  "path": "data.time_on_source.evidence[0]",
  "value": "23 mins",
  "failed_quote": "PKS B1740 − 517 was observed for a total of 23 mins, in three scans each bracketed by 30 sec observations of a nearby phase calibrator (J1753 − 5015)."
 },
 {
  "path": "processing.calibration.pipeline_or_manual.evidence[0]",
  "value": "pipeline",
  "failed_quote": "Data importing, flagging and calibration were carried out using version 4.5.3 of the CASA package (McMullin et al. 2007) and the standard ALMA science pipeline tools."
 },
 {
  "path": "processing.calibration.casa_version.evidence[0]",
  "value": "4.5.3",
  "failed_quote": "Data importing, flagging and calibration were carried out using version 4.5.3 of the CASA package (McMullin et al. 2007)"
 },
 {
  "path": "processing.imaging.smoothing.evidence[0]",
  "value": "Hanning smoothing to effective resolution 1.8 km/s; 10 km/s bins for emission search",
  "failed_quote": "After Hanning smoothing the effective resolution is twice the channel spacing, ∆v ≈ 1.8 km s−1."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "3.1 per cent per 2 km s^-1 (absorption spectrum); 1.98 mJy beam^-1 per 2 km s^-1 (towards continuum source); 2.10 mJy per 10 km s^-1 (extracted 1.75 arcsec emission spectrum)",
  "failed_quote": "detected above the RMS noise level of 3.1 per cent per 2 km s−1"
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "ASKAP observing and data reduction strategy (self-calibration, continuum subtraction, imaging with MIRIAD)",
  "failed_quote": "We used the same observing strategy as described by A15... Further self-calibration, continuum-subtraction and imaging of the target field were carried out using the MIRIAD package (Sault et al. 1995) as described by A15"
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "weighting = natural; velocity resolution = 2 km/s; 1st-order polynomial continuum fit",
  "failed_quote": "imaged the visibilities at the full 2 km s−1 velocity resolution. Since the continuum source is not resolved with uniform weighting we used natural weighting... We fitted a 1st-order polynomial to the continuum"
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Evaluated 5-sigma integrated flux density upper limit (including absorbing region correction)",
  "failed_quote": "giving a 5-σ detection limit for the line integrated flux density of 279 mJy km s−1. However, the detected absorption will act to disguise any possible emission... giving an upper limit for undetected emission of int S CO dv < 579 mJy km s−1."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "ALMA data importing, flagging, calibration, and imaging (UVSUB, UVCONTSUB3)",
  "failed_quote": "Data importing, flagging and calibration were carried out using version 4.5.3 of the CASA package (McMullin et al. 2007) and the standard ALMA science pipeline tools."
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Self-calibration, continuum-subtraction (UVLIN), and imaging of ASKAP data",
  "failed_quote": "Further self-calibration, continuum-subtraction and imaging of the target field were carried out using the MIRIAD package (Sault et al. 1995) as described by A15"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Integrated 12CO (2-1) optical depth lower limit = 4.78 km s^-1",
  "failed_quote": "we obtain a lower limit for the integrated optical depth of int τ CO dv ≳ 4.78 ± 0.47 km s−1."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Integrated 12CO (2-1) line flux density upper limit = 579 mJy km s^-1",
  "failed_quote": "giving an upper limit for undetected emission of int S CO dv < 579 mJy km s−1."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "Cold molecular gas is present in a circumnuclear reservoir (M_H2 ~ 0.9-60 x 10^7 Msun) likely distributed in a disc or ring within 2 kpc of the AGN.",
  "failed_quote": "We have used the Atacama Large Millimetre Array (ALMA) to detect a rare example of redshifted 12CO (2-1) absorption in PKS B1740 − 517... The coincident H I 21-cm and molecular absorption have very similar line profiles and reveal a reservoir of cold gas"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Jet-driven gas outflow rejected for the narrow HI component because the line width (∆v FWHM < 5 km/s) is much too narrow to be accelerated by a jet to >100 km/s.",
  "failed_quote": "However, the line width (∆v FHWM < 5 km s−1) is inconsistent with jet-driven gas outflows that are typically associated with young radio sources... It is unlikely that the gas could be accelerated by the jet to more than 100 km s−1 and retain such a low dispersion."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[1]",
  "value": "Mass estimates are based on pencil-beam absorption measurements and simple disc geometry assumptions, and source age estimate assumes equipartition and uniform magnetic fields.",
  "failed_quote": "We note this estimate of the source age involves several assumptions, including magnetic field uniformity, equipartition, and electron mixing... and should therefore be considered a useful order of magnitude measurement of the source age."
 }
]
```
