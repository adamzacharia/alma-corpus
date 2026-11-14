# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.535..729P\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–19 (2024) Preprint 4 October 2024 Compiled using MNRAS L [A] TEX style file v3.0

## **The spatially resolved relation between dust, gas, and metal abundance** **with the TYPHOON survey**


Hye-Jin Park, [1] _[,]_ [2] _[★]_ Andrew J. Battisti, [1] _[,]_ [2] Emily Wisnioski, [1] _[,]_ [2] Luca Cortese, [2] _[,]_ [3] Mark Seibert, [4]

Kathryn Grasha, [1] _[,]_ [2] _[,]_ [5] -, Barry F. Madore, [4] _[,]_ [6] Brent Groves, [2] _[,]_ [3] Jeff A. Rich, [4] Rachael L. Beaton, [4] _[,]_ [7] Qian-Hui Chen ( `陈千惠` ), [1] _[,]_ [2] Marcie Mun, [1] _[,]_ [2] Naomi M. McClure-Griffiths, [1] W.J.G. de Blok, [8] _[,]_ [9] _[,]_ [10]

Lisa J. Kewley 11 _,_ 1 _,_ 2

1 _Research School of Astronomy and Astrophysics, Australian National University, Cotter Road, Weston Creek, ACT 2611, Australia_
2 _ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Australia_
3 _International Centre for Radio Astronomy Research, The University of Western Australia, 35 Stirling Highway, Crawley, Perth, WA 6009, Australia_
4 _The Observatories, Carnegie Institution for Science, 813 Santa Barbara Street, Pasadena, CA 91101, USA_
5 _Visiting Fellow, Harvard-Smithsonian Center for Astrophysics, 60 Garden Street, Cambridge, MA 02138, USA_
6 _Department of Astronomy and Astrophysics, University of Chicago, Chicago, IL, USA_
7 _Department of Astrophysical Sciences, 4 Ivy Lane, Princeton University, Princeton, NJ 08544, USA_
8 _ASTRON, the Netherlands Institute for Radio Astronomy, Oude Hoogeveensedĳk 4, 7991 PD Dwingeloo, the Netherlands_
9 _Department of Astronomy, University of Cape Town, Private Bag X3, Rondebosch 7701, South Africa_
10 _Kapteyn Astronomical Institute, University of Groningen, PO Box 800, 9700 AV Groningen, The Netherlands_
11 _Institute for Theory and Computation, Harvard-Smithsonian Center for Astrophysics, Cambridge, MA 02138, USA_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

We present the spatially resolved relationship between the dust-to-gas mass ratio (DGR) and gas-phase metallicity ( _𝑍_ gas or
12+log(O/H)) (i.e., DGR– _𝑍_ gas relation) of 11 nearby galaxies with a large metallicity range (1.5 dex of 12+log(O/H)) at (sub-)kpc
scales. We used the large field-of-view (≳ 3 [′] ) optical pseudo-Integral Field Spectroscopy data taken by the TYPHOON/PrISM
survey, covering the optical size of galaxies, combining them with multi-wavelength data (far-UV to far-IR, CO, and Hi 21 cm
radio). A large scatter of DGR in the intermediate metallicity galaxies (8.0 _<_ 12+log(O/H) _<_ 8.3) is found, which is in line
with dust evolution models, where grain growth begins to dominate the mechanism of dust mass accumulation. In the lowest
metallicity galaxy of our sample, Sextans A (12+log(O/H) _<_ 7.6), the star-forming regions have significantly higher DGR values
(by 0.5–2 dex) than the global estimates from literature at the same metallicity but aligns with the DGR values from metal
depletion method from Damped Lyman Alpha systems and high hydrogen gas density regions of Sextans A. Using dust evolution
models with a Bayesian MCMC approach suggests: 1) a high SN dust yield and 2) a negligible amount of photofragmentation
by UV radiation, although we note that our sample in the low-metallicity regime is limited to Sextans A. On the other hand, it is
also possible that while metallicity influences DGR, gas density also plays a role, indicating an early onset of dust grain growth
in the dust mass build-up process despite its low metallicity.


**Key words:** ISM: dust, extinction – galaxies: ISM – ISM: abundances – galaxies: abundances



**1** **INTRODUCTION**


Interstellar dust plays an important role in the interstellar medium
(ISM) of galaxies and understanding this role is fundamental to improving our theories of galaxy evolution. Despite its small mass
fraction out of the total baryon mass (≤ 1% in a typical late-type
galaxy; Galliano et al. 2018), interstellar dust has a disproportionate
effect on a galaxy’s ISM, including: being catalysts of chemical reac

_★_ E-mail: hyejin.park@anu.edu.au

- ARC DECRA Fellow

- Hubble Fellow


© 2024 The Authors



tions on the surface of dust grains, such as the formation of molecular
hydrogen (H 2 ) (Hollenbach & Salpeter 1971; Hollenbach & Tielens
1997) and being major coolants of the interstellar medium (ISM) by
shielding them from the interstellar radiation field, aiding the collapse of the giant molecular clouds (GMC) into forming new stars.
Dust accretes and removes chemical elements from the gas phase,
known as ‘metal [1] depletion.’ The _selective_ depletion of elements
onto dust, known as ‘fractionation,’ impacts the gas phase, changing the observed gas abundances and removing potential coolants.
In addition, dust significantly affects the spectral energy distribution


1 Heavy elements compared to hydrogen and helium.

2 _H.-J. Park et al._


(SED) of galaxies and introduces uncertainties in derived physical
properties, such as the star formation rate (SFR) and stellar mass
( _𝑀_ _★_ ) (Conroy 2013). Specifically, the starlight emitted from young
massive (O/B-type) stars at short wavelengths is absorbed by interstellar dust and re-emitted at longer wavelengths. Generally speaking,
roughly 30 - 50 % of the light from young stellar populations is lost
at wavelengths from far-UV to near-IR and re-emitted at mid-IR to
sub-mm wavelengths (Galliano et al. 2018).
The dust-to-gas mass ratio (DGR),


_𝐷𝐺𝑅_ ≡ _𝑀_ dust / _𝑀_ gas = _𝑀_ dust /( _𝑀_ atom + _𝑀_ mol ) _,_ (1)


can represent how much a region is enriched, in the form of dust
mass ( _𝑀_ dust ) at a given amount of gas mass (the sum of atomic
gas mass and molecular gas mass, _𝑀_ gas = _𝑀_ atom + _𝑀_ mol ). This mass
ratio is a reflection of various sources contributing to dust growth
and destruction. Assuming the equilibrium between timescales of
dust formation and dust destruction within galaxies, a tight linear
relationship between the DGR and the gas-phase metallicity ( _𝑍_ gas or
12+log(O/H) in this study) of galaxies is expected (e.g., Inoue 2011;
Asano et al. 2013), and it has been observed in many metal-rich
galaxies ( _𝑍_ gas _>_ 0.45 _𝑍_ ⊙ or 12+log(O/H) _>_ 8.3; e.g., Issa et al. 1990,
De Vis et al. 2017, De Vis et al. 2019).
The linear DGR– _𝑍_ gas relation is a useful tool itself in estimating
gas masses of massive (and metal-rich) high-redshift ( _𝑧_ ) galaxies
via _𝑀_ dust because measuring _𝑀_ dust via dust continuum in RayleighJeans (RJ) tail (e.g., Casey et al. 2014) and converting it to gas
mass is more observationally efficient compared to measuring gas
mass directly from the CO or Hi observations. For example, Scoville
et al. (2014) and Scoville et al. (2016) have developed a calibration for _𝑀_ gas estimation using the dust continuum for 107 galaxies
with high stellar mass ( _𝑀_ _★_ ∼ 10 [11] _𝑀_ ⊙ ) in the COSMOS field at the
_𝑧_ = 0 _._ 2−2 _._ 5. They constructed the calibrations by assuming constant
DGR values at solar metallicity. More recently, Tacconi et al. (2018)
provided an updated calibration to estimate gas mass using the empirical trend of a linearly increasing DGR with gas-phase metallicity
for 12+log(O/H) _>_ 8.0. However, these calibrations are often widely
used across a range of high- _𝑧_ galaxies (e.g., Liu et al. 2019) despite it
being unclear how reliable these extrapolations are down to the low
mass/metallicity regime.

Rémy-Ruyer et al. (2014) studied the relationship between galaxyintegrated DGR and _𝑍_ gas ( _global_ _DGR–𝑍_ gas _relation_ hereafter) using 126 nearby galaxies from two surveys, Key Insights on Nearby
Galaxies: A Far-Infrared Survey with Herschel (KINGFISH; Kennicutt et al. 2011) and Dwarf Galaxy Survey (DGS; Madden et al.
2013) of 7.14 _<_ 12+log(O/H) _<_ 9.10 (with metallicity diagnostic using _𝑅_ 23 ratio [2] of Pilyugin & Thuan 2005; PT05). They found that
the observed global DGR– _𝑍_ gas relation is better described with a
broken power law rather than a single power law, with a steeper slope
and a larger scatter at low metallicity galaxies (12+log(O/H)≲ 8.0).
They suggested that the break at 12+log(O/H)∼8 _._ 0 implies that the
balance of timescales of dust formation/growth and destruction is
not preserved in low metallicity systems. However, more recently
De Vis et al. (2019) with 466 DustPedia late-type galaxies (Davies
et al. 2017) found that a single power law better describes the DGR
trend with _𝑍_ gas over the broken model, redirecting the exact shape of
DGR– _𝑍_ gas relation on the debate.
Theoretical approaches, on the other hand, show the steeper slope
of the DGR– _𝑍_ gas relation at lower metallicity (e.g. Zhukovska 2014,


2 _𝑅_ 23 = ([O II] _𝜆_ 3726,3729 + [O III] _𝜆_ 4959,5007) / H _𝛽_ )


MNRAS **000**, 1–19 (2024)



Feldmann 2015, De Vis et al. 2017, and Galliano et al. 2021), implying the non-equilibrium between dust formation and destruction
timescales and different mechanisms on the dust mass build-up. In
particular, Asano et al. (2013) suggested ‘critical metallicity’ where
the dominant mechanism of dust mass increase is changed and this
value can vary with the star formation timescale of a system. They
further divide the metallicity ( _𝑍_ ) into three regimes:


  - Low-metallicity regime (starburst regime; _𝑍<_ 0.05 _𝑍_ ⊙ ): dust
formation or evolution is slow as dust grains are mainly condensed
in stellar ejecta (stellar wind or SNe).


  Intermediate-metallicity regime (critical metallicity regime;
0.05–0.3 _𝑍_ ⊙ ): dust mass build-up starts to be efficient as grain growth
in the ISM comes into play as a dominance.

  - High-metallicity regime (ISM growth regime; _𝑍>_ 0.3 _𝑍_ ⊙ ):
grain growth dominates, showing a linear relation of DGR ∝ _𝑍_,
consistent with many previous observational studies in the highmetallicity regime.


The spatially resolved study on the DGR– _𝑍_ gas relation is important
as _𝑀_ dust measurement at galaxy-integrated scale, as probed in the
most earlier works, can be underestimated in SED modelling due to
the resolution effect (also known as Matryoshka effect; Galliano et al.
2011 and Galliano et al. 2018). This is because hot dust components
can dilute the luminosity of colder components due to cold dust’s
weak luminosity (e.g., modified black body) at a coarse resolution.
In terms of accurate _𝑀_ dust measurement of a system, this effect is
crucial as cold dust constitutes a substantial fraction of the total _𝑀_ dust .
This can lead to a systematically underestimated total _𝑀_ dust by up
to 50 % when it is derived in a galaxy-integrated way (e.g., Galliano
et al. 2011, Galliano et al. 2018, Appendix D of Roman-Duval et al.
2014, Aniano et al. 2012, and Aniano et al. 2020).
Owing to the development of optical IFS, it has become possible to
derive the DGR– _𝑍_ gas relation in a spatially resolved manner ( _resolved_
_DGR–𝑍_ gas _relation_ hereafter). However, most resolved DGR– _𝑍_ gas
relations have been derived with a fixed metallicity gradient for individual galaxies and are mostly focused on high-metallicity regimes
with smaller Field-of-View (FoV) only covering the central region of
galaxies. For example, Sandstrom et al. (2013) explored the spatially
resolved DGR analysis (at ∼ kpc scale) for 26 nearby galaxies with a
metallicity range of 8.2 _<_ 12+log(O/H) (PT05) _<_ 8.75. The metallicity values of each region rely on the metallicity gradient from a small
part of galaxies rather than the entire galaxy (Moustakas et al. 2010).
More recently, several studies such as Vílchez et al. (2019), Relaño
et al. (2018), and Chiang et al. (2018) explored the resolved DGR– _𝑍_ gas relation in nearby spiral galaxies in a similar way (i.e. fixed
metallicity gradient). However, assuming a metallicity gradient of
galaxies can overlook the locally varying metal abundances in galaxies, which can be related to the age of the stellar cluster, molecular
gas surface density, dust column density, and electron density (e.g.,
Kreckel et al. 2019; Groves et al. 2023). This indicates that fully spatially resolved studies on this relation are required to mitigate these
effects.

In this study, we explore the DGR– _𝑍_ gas relationship by examining
_both_ of DGR and _𝑍_ gas in a fully spatially resolved way using a sample
of 11 nearby galaxies from the TYPHOON survey that spans a broad
range in metallicity (7.1 _<_ 12+log(O/H) (Scal) _<_ 8.6).
The outline of this paper consists of as follows. We describe our
galaxy sample, the datasets, and data processing in Section 2. In
Section 3, we present the method for the measurements of ISM
parameters for resolved regions. We show the derived global and
resolved DGR– _𝑍_ gas relation and several ISM scaling relations in
Section 4. In Section 5, we discuss the tension in the DGR– _𝑍_ gas

relationship and comparison to dust/chemical evolution models. We
then summarize our conclusions in Section 6. Throughout the paper,
we assumes the flat Λ-CDM cosmological model with _𝐻_ 0 = 70
km s [−][1] Mpc [−][1], Ω _𝑀_ = 0.3, and Ω Λ = 0.7.


**2** **SAMPLE AND DATA**


**2.1** **TYPHOON Survey**


The TYPHOON/PrISM survey [3] (Carnegie Observatories, TYPHOON Programme PI: Barry F. Madore) provides pseudo-IFS data
with a large Field-of-View (FoV) size for 44 nearby galaxies (D ≲
35 Mpc) with a wide range in morphological types such as dwarf irregulars, spirals, ring, and AGN/Seyfert. This survey used the Widefield CCD imaging spectrograph of the du Pont 2.5m telescope at
Las Campanas Observatory in Chile. The data are obtained with a

∼
high physical resolution ( 100 pc/spaxel at a distance of 12.5 Mpc
derived from a spatial resolution of ∼ 1.65 [′′] ) and a spectral resolution of R ∼ 850 at 7000 Å. The Progressive Integral Step Method
(PrISM) is a ‘stepped-slit’ technique to create 3D data cubes. The
observations have a large FoV of approximately 18 [′] × (1.65 [′′] ×N),
where N represents the number of stepped slits. This enables coverage of nearly the entire optical disk of very nearby galaxies (e.g.,
Poetrodjojo et al. 2019, Grasha et al. 2022, Chen et al. 2023, and
Siebert et al., in prep). This dataset offers a unique opportunity to
gain a comprehensive understanding of the distributions of physical
and chemical properties across the extended source and also allows
us to explore many galaxy evolution studies such as the metallicity
gradient and bar effect (e.g., Grasha et al. 2022 and Chen et al. 2023).
The target galaxies of the TYPHOON survey were selected from
the sample of The 11 Mpc Halpha and Ultraviolet Galaxy Survey
(11HUGS) and the Local Volume Legacy (LVL) surveys. The TYPHOON parent sample galaxies are located on the declination of
_<_ +10 deg and have low to moderate inclination and a surface
brightness brighter than 21.1 AB mag arcsec [−][2] in the B band. For
this study, we select our sample galaxies based on the availability of
ancillary data ( _Herschel_ far-IR, CO (1-0) or CO (2-1), and Hi 21 cm).
The physical properties of the 11 TYPHOON galaxies that satisfy
these ancillary data requirements are summarised in Table 1. Further
details on the individual characteristics of the galaxies are presented
in Appendix D.
We provide a brief description of the TYPHOON data in this paper
(please refer to the forthcoming project description paper, Seibert et
al. in prep., for detailed information on the data and its reduction
process). The final data cubes, obtained after data reduction, have
the following characteristics: (1) wavelength coverage ranging from
3650–8150 Å, (2) spectral resolution of Δ _𝜆_ ∼ 3.5 Å (FWHM of
8.24 Å), corresponding to R ∼ 850 at 7000 Å and (3) spatial resolution of 1.65 [′′], which corresponds to a physical scale of 40 pc at
a representative distance of 5 Mpc. The emission line fluxes of the
spaxels are fitted using `lzifu` (Ho et al. 2016; Battisti et al. in prep).
After modelling and subtracting the stellar continuum from each
observed spectra, `lzifu` fits a single Gaussian to the emission line
and measures its flux. The following emission lines are extracted:

[O II] _𝜆_ 3726, 3729, H _𝛿_, H _𝛾_, [O III] _𝜆_ 4363, H _𝛽_, [O III] _𝜆_ 5007, H _𝛼_,

[N II] _𝜆_ 6583, [S II] _𝜆_ 6716, 6731.


3 `[https://typhoon.datacentral.org.au](https://typhoon.datacentral.org.au)`



_Resolved dust evolution in nearby galaxies_ 3


_2.1.1_ _Dust extinction correction_


We correct the dust extinction effect for the extracted emission lines

for the subsequent analysis, using the Balmer decrement and its
conversion to _𝐸_ ( _𝐵_ − _𝑉_ ) using the following equation:



where H _𝛼_ /H _𝛽_ (intrinsic) is 2.86 for case B recombination (Osterbrock 1989) at _𝑇_ e = 10,000 K and _𝑛_ e of 100 cm [−][3] . The _𝑘_ (H _𝛼_ ) and
_𝑘_ (H _𝛽_ ) represent the amount of extinction at the wavelengths of H _𝛼_
and H _𝛽_, respectively, assuming _𝑅_ ( _𝑉_ ) to be 3.1 based on the Milky
Way (MW) extinction curve (Fitzpatrick 1999). The _𝑘_ ( _𝜆_ ) is derived
from _𝑘_ ( _𝜆_ ) = _𝐴_ ( _𝜆_ )/ _𝐸_ ( _𝐵_ − _𝑉_ ).


**2.2** **Ancillary data**


Together with the optical IFU data, we collect archival ancillary
multi-wavelength data obtained from various surveys for each galaxy.
In the subsequent sections, we describe the data collected specifically
for this study.


_2.2.1_ _H_ i _and CO data_


We obtain Hi 21 cm and carbon monoxide (CO) radio observation
data from various surveys or individual galaxy studies to explore
the gas distribution of sample galaxies. The names of the surveys or
telescopes are listed in Table 2. The Hi 21cm hyperfine transition
observation enables us to trace the neutral hydrogen in galaxies.
The observations for CO (1-0) or (2-1) rotational transition lines are
commonly used to trace molecular hydrogen (H 2 ) in galaxies, as CO
molecules can be easily excited in cold molecular clouds.
The Hi 21 cm data is retrieved from surveys such as The Hi Nearby
Galaxy Survey (THINGS [4] ; Walter et al. 2008), VLA Imaging of
Virgo in Atomic Gas (VIVA [5] ; Chung et al. 2009) survey, Local
Irregulars That Trace Luminosity Extremes, The Hi Nearby Galaxy
Survey (LITTLE THINGS [6] ; Hunter et al. 2012), Local Volume Hi
Survey (LVHIS [7] ; Koribalski et al. 2018), The Wide-field ASKAP Lband Legacy All-sky Blind surveY (WALLABY [8] ; Koribalski et al.
2020) and individual galaxy observation (NGC 6822; de Blok &
Walter 2000). We use the flux density map (moment 0 map) derived
from natural-weighted Hi data cubes extracted by the survey teams.
For NGC 625, NGC 1705 and NGC 5253, the spatial resolution of the
natural-weighted cube is larger than one of the final resolutions of this
study (25 [′′] at SPIRE 350 _𝜇_ m; see Section 2.3) and thus, we instead
use robust-weighted data cube. For NGC 1566 and NGC 6822, we
extract moment 0 maps from the data cubes using `3D-Barolo` (Di
Teodoro & Fraternali 2015) only allowing sources having signal-tonoise ratio (S/N) _>_ 3 (see Appendices of Verheĳen & Sancisi 2001
and Lelli et al. 2014 for noise map calculation).
We search for either CO (1-0) or CO (2-1) data for individual
galaxies based on their availability. For five of the sample galaxies, the CO (2-1) images are provided by Physics at High Angular resolution in Nearby Galaxies (PHANGS [9] ) team as part of the


4 `[https://www2.mpia-hd.mpg.de/THINGS/Overview.html](https://www2.mpia-hd.mpg.de/THINGS/Overview.html)`
5 `[http://www.astro.yale.edu/viva/](http://www.astro.yale.edu/viva/)`
6 `[https://science.nrao.edu/science/surveys/littlethings](https://science.nrao.edu/science/surveys/littlethings)`
7 `www.atnf.csiro.au/research/LVHIS`
8 `[https://wallaby-survey.org/](https://wallaby-survey.org/)`
9 `[https://sites.google.com/view/phangs/home](https://sites.google.com/view/phangs/home)`


MNRAS **000**, 1–19 (2024)



_𝐻𝛼_ / _𝐻_ _𝛽_ (observed)
_𝐸_ ( _𝐵_ − _𝑉_ ) = log � _𝐻𝛼_ / _𝐻𝛽_ (intrinsic)



�



(2)
0 _._ 4 × ( _𝑘_ ( _𝐻𝛽_ ) − _𝑘_ ( _𝐻𝛼_ )) _[,]_

4 _H.-J. Park et al._


Name RA DEC Dist. _𝑧_ Phys. Resol. _𝑟_ 25 P.A. Incl. log _𝑀_ _★_ log SFR A(V) MW [∗]

(J2000) (J2000) (Mpc) (kpc) (arcsec) (deg) (deg) ( _𝑀_ ⊙ ) ( _𝑀_ ⊙ yr [−][1] ) (mag)


NGC 625 01h35m04.63s -41d26m10.3s 3.5 _[𝑎]_ 0.001321 0.424 172.7 106 [1] 64 [1] 8.48 [6] -1.40 [6] 0.0437
NGC 1512 04h03m54.28s -43d20m55.9s 18.8 _[𝑏]_ 0.002995 2.279 267.4 261.9 [2] 42.5 [2] 10.57 [5] -0.12 [5] 0.0282
NGC 1566 04h20m00.42s -54d56m16.1s 17.7 _[𝑐]_ 0.005017 2.145 249.6 214.7 [2] 29.5 [2] 10.67 [5] 0.65 [5] 0.0242
NGC 1705 04h54m13.50s -53d21m39.8s 5.5 _[𝑎]_ 0.002112 0.667 57.2 50 [1] 45 [1] 8.07 [5] -1.29 [5] 0.0213
NGC 3521 11h05m48.58s -00d02m09.1s 13.2 _[𝑑]_ 0.002672 1.600 329.0 343 [2] 68.8 [2] 10.83 [5] 0.42 [5] 0.153
NGC 4536 12h34m27.05s +02d11m17.3s 16.3 _[𝑒]_ 0.006031 1.976 227.6 305.6 [2] 66 [2] 10.19 [5] 0.47 [5] 0.0487
NGC 5236 13h37m00.95s -29d51m55.5s 4.9 _[𝑒]_ 0.001711 0.594 386.5 225 [2] 24 [2] 10.41 [5] 0.63 [5] 0.1770
NGC 5253 13h39m55.96s -31d38m24.4s 3.5 _[𝑎]_ 0.001358 0.424 150.4 21 [1] 42 [1] 8.57 [5] -0.32 [5] 0.1481
NGC 6822 19h44m57.74s -14d48m12.4s 0.5 _[𝑎]_ -0.00019 0.200 464.7 10 [3][†] 67 [3][†] 7.90 [6] -2.15 [6] 0.6174
NGC 7793 23h57m49.83s -32d35m27.7s 3.6 _[𝑒]_ 0.000767 0.436 280.0 290 [2] 50 [2] 9.25 [5] -0.60 [5] 0.0518
Sextans A 10h11m00.80s -04d41m34.0s 1.4 _[𝑎]_ 0.001081 0.200 176.7 41 [4] 33.5 [4] 8.04 [5] -2.18 [5] 0.1198


**Table 1.** Characteristics of sample galaxies. The coordinates and redshifts are from NED. The chosen physical resolution of each galaxy in this study after data
processing (convolution and resampling) is presented in units of kpc at the given distance. The optical radius _𝑟_ 25 is from de Vaucouleurs et al. (1991).
Distance references: (a) Tully et al. (2013) (b) Anand et al. (2021) (c) Kourkchi & Tully (2017) (d) Tully et al. (2016) (e) Tully et al. (2009)
References for position angle (P.A.), inclination (Incl.), _𝑀_ _★_ and SFR: (1) Koribalski et al. (2018) (2) Lang et al. (2020) (3) Mateo (1998) (4) Hunter et al. (2012)
(5) Leroy et al. (2019) (6) Madden et al. (2013)

- This galaxy has an optical PA (of its stellar bar) notably different from the Hi disk.
∗ The MW extinction value is adopted from the Schlafly & Finkbeiner (2011) dust maps (see Section 2.2.2).



PHANGS-ALMA collaboration, an Atacama Large Millimeter/submillimetre Array (ALMA) large program (Leroy et al. 2021a; Leroy
et al. 2021b). This project has extensively mapped the CO J 2→1 transition at a scale of approximately 100 pc using the ALMA main array
(12m), Morita Atacama Compact Array (ACA) (7m), and the Total
Power (TP) for 90 nearby galaxies. For NGC 5236 CO (2-1) data,
the initial data collection has been made by separate ALMA projects
(Project code: 2015.1.00121.S and 2016.1.00386.S, PI: Sakamoto)
and run by PHANGS-ALMA pipeline. We obtain the CO (2-1) moment 0 maps of the five galaxies from the PHANGS data archive [10] .
Another five galaxies in our sample have CO data in the ALMA
archive [11] . This includes three galaxies, NGC 625, NGC 1705, and
NGC 5253, from Hunt et al. (2023) from ALMA 12m and ACA 7m
CO (1-0) observations (Program code: 2018.1.00219.S, PI: Hunt)
and NGC 6822 from ALMA 7m (Program code: 2019.2.00110.S,
PI: Kohno; Program code: 2021.1.00330.S, PI: Tosaki). The CO (10) data cubes for these four galaxies were obtained in a primary
beam-corrected format initially. We extract the moment 0 maps from
the cubes without primary beam correction done using `3D-Barolo`,
ensuring a consistent and well-defined noise level across each channel map. Following the moment 0 map extraction, we subsequently
implemented the primary beam correction on these maps. An exception is that the NGC 7793 CO (2-1) moment 0 map has been made
separately using the ALMA 12m data cube observed by the ALMALEGUS survey (Grasha et al. 2018; Finn et al. 2024) (Program code:
2015.1.00782.S, PI: Johnson).
For Sextans A, which has the lowest metallicity (12+log(O/H) of

∼
7.5), there have been several attempts to map CO emissions using
ALMA. Unfortunately, robust observations of CO emissions in this
galaxy using the interferometer have not yet been successful. For
molecular gas information of this galaxy, we find the mass sensitivity
limit from the observation implemented on two main star-forming
regions of Sextans A using ALMA (Program code: 2018.1.01783.S;
PI: Meyer). We obtain the rms maps using the `3D-Barolo` for the


10 `[https://www.canfar.net/storage/list/phangs/RELEASES/](https://www.canfar.net/storage/list/phangs/RELEASES/PHANGS-ALMA/)`

```
PHANGS-ALMA/
```

11 `[https://almascience.nrao.edu/aq/](https://almascience.nrao.edu/aq/)`


MNRAS **000**, 1–19 (2024)



two native data cubes and multiply by three (i.e., 3 S/N) to construct
a _CO(1-0) emission sensitivity map_ .
The observation of NGC 6822’s Hi and CO data cubes are affected

by the presence of diffuse MW cirrus emission features, which pose
significant challenges to the accurate assessment of NGC 6822’s
Hi and CO emissions within specific velocity ranges. Specifically,
the Hi emission encounters severe contamination when the systemic
velocity lies between -14 km s [−][1] and -3 km s [−][1] (as shown in de
Blok & Walter 2006; Namumba et al. 2017; Park et al. 2022), while
the CO emission faces similar challenges between 4 km s [−][1] and
10 km s [−][1] (Gratier et al. 2010). To address this issue and minimize the
interference caused by the MW cirrus feature, we extract moment 0
maps solely from channels with systemic velocities below -14 km s [−][1]

for Hi and below 4 km s [−][1] for CO data. Notably, this selected velocity
range does not impact our spatially resolved analysis, given that the
central velocity of NGC 6822, where most H II regions are situated,
remains near -55 km s [−][1] .


_2.2.2_ _UV, optical, and IR photometric images_


Most of the photometric UV, optical, and IR data for individual
galaxies are retrieved from NED [12] . The far-UV and near-UV data
for all sample galaxies are obtained as part of the Galaxy Evolution
Explorer (GALEX) Nearby Galaxy Survey (NGS; Gil de Paz et al.
2007). For the optical wavelength photometric data, we use images
taken by various telescopes depending on the availability, including
Cerro Tololo Inter-American Observatory (CTIO) 0.9m/1.0m/1.5m,
the Kitt Peak National Observatory (KPNO) 2.1m, and the Sloan Digital Sky Survey (SDSS) 2.5m telescopes. We use near-IR and mid-IR
images observed with the Two Micron All Sky Survey (2MASS),
_Spitzer_ -IRAC/MIPS cameras at wavelengths of 3.5, 4.5, 5.7, 7.8, and
23.7 _𝜇_ m, and/or the Wide-field Infrared Survey Explorer (WISE) at
wavelengths of 3.4, 4.6, 11.6, and 22.1 _𝜇_ m. For the far-IR images,
we use data from _Herschel_ -PACS at wavelengths of 70, 100, and
160 _𝜇_ m, as well as from _Herschel_ -SPIRE at wavelengths of 250 and


12 `[https://ned.ipac.caltech.edu/](https://ned.ipac.caltech.edu/)`

_Resolved dust evolution in nearby galaxies_ 5


Name Hi source CO source

Survey (telescope) Beam (major × minor) Survey (telescope) Beam (major × minor)


NGC 625 LVHIS (ATCA) [1] 25 [′′] × 25 [′′] – (ALMA 12m) [8] 2.08 [′′] × 1.49 [′′]

NGC 1512 LVHIS (ATCA) [2] 15 [′′] × 15 [′′] PHANGS (ALMA 12m+7m+TP) [9] 1.03 [′′] × 1.03 [′′]

NGC 1566 WALLABY (ASKAP) [3] 42 [′′] × 35 [′′] PHANGS (ALMA 12m+7m+TP) [9] 1.25 [′′] × 1.25 [′′]

NGC 1705 LVHIS (ATCA) [1] 25 [′′] × 25 [′′] – (ALMA 12m) [8] 2.49 [′′] × 1.82 [′′]

NGC 3521 THINGS (VLA) [4] 14.14 [′′] × 11.15 [′′] PHANGS (ALMA 12m+7m+TP) [9] 1.33 [′′] × 1.33 [′′]

NGC 4536 VIVA (VLA) [5] 18.04 [′′] × 16.18 [′′] PHANGS (ALMA 12m+7m+TP) [9] 1.48 [′′] × 1.48 [′′]

NGC 5236 THINGS (VLA) [4] 15.16 [′′] × 10.40 [′′] PHANGS (ALMA 12m+7m+TP) [9] 2.14 [′′] × 2.14 [′′]

NGC 5253 LVHIS (ATCA) [1] 25 [′′] × 25 [′′] – (ALMA 12m) [8] 2.68 [′′] × 2.41 [′′]

NGC 6822 – (ATCA) [6] 42.40 [′′] × 12 [′′] – (ALMA 7m) (upper) 17.14 [′′] × 9.55 [′′]

(middle) 17.11 [′′] × 8.96
(lower) 15.57 [′′] × 9.33 [′′]

NGC 7793 THINGS (VLA) [4] 15.60 [′′] × 10.85 [′′] – (ALMA 12m) [10] 0.724 [′′] × 0.724 [′′]

Sextans A LITTLE THINGS (VLA) [7] 7.6 [′′] × 6.5 [′′] – –


**Table 2.** Radio data (Hi 21 cm and CO) references (1) Koribalski et al. (2018) (2) Koribalski & López-Sánchez (2009) (3) Elagali et al. (2019) (4) Walter et al.
(2008) (5) Chung et al. (2009) (6) de Blok & Walter (2000) (7) Hunter et al. (2012) (8) Hunt et al. (2023) (9) Leroy et al. (2021b) (10) Grasha et al. (2018)



350 _𝜇_ m. In Table C1, we provide a comprehensive list of the instruments, band names, effective wavelengths, and PSF/beam sizes. In
addition, a list of the ancillary data of each sample and their references are available in Table C2. All photometric data are extinction
corrected for foreground MW dust using dust reddening maps [13] from
Schlafly & Finkbeiner (2011) and assuming the MW extinction curve
of Fitzpatrick et al. (2019).


**2.3** **Image processing**


For a region-by-region analysis, we ensure that all multi-wavelength
images have the same spatial resolution as the coarsest image, which
in this study is the Herschel-SPIRE 350 _𝜇_ m image with a resolution
of approximately 25 [′′] for the majority of our sample galaxies (except
for NGC 1566, NGC 6822, and Sextans A; see Section 2.3.3). We
note that the SPIRE 500 _𝜇_ m images were not considered in this
study. The SPIRE 500 _𝜇_ m band is sensitive to the massive, cold
dust components. However, excluding these images still allows us
to reliably estimate the interstellar _𝑀_ dust of a system, with < 30%
of error from the dust mass estimated using far-IR bands including
500 _𝜇_ m (Aniano et al. 2012). Additionally, it is important to note
that the SPIRE 500 _𝜇_ m image has a considerably coarse resolution of
37.5 [′′], thus excluding it allows us to obtain more pixels with reliable
_𝑀_ dust at the same time.
In the following sections, we describe the image processing steps
applied to all data being used in this work for region-by-region analysis. The units of the images at wavelengths from far-UV to far-IR
(photometry images hereafter) are converted to Jy pix [−][1] at the end of
the image process (i.e., after image convolution and resampling are
completed) to match with the unit required to run the SED modelling
code `MAGPHYS` (see Section 3.1).


_2.3.1_ _Sky background subtraction_


The photometry images have been sky background subtracted. While
many survey images are already sky background subtracted through
their data reduction pipelines, some may not have undergone this
process. For such images, we build sky background maps using an


13 `[https://irsa.ipac.caltech.edu/applications/DUST/](https://irsa.ipac.caltech.edu/applications/DUST/)`



IDL tool ‘sky’ [14] . We apply a 3- _𝜎_ clipping method to remove sources
from the image and derive a median value of the background levels of
a given box size. Subsequently, the measured sky background images
are subtracted from the original images.


_2.3.2_ _Foreground star removal_


It is crucial to address the impact of bright foreground stars on galaxy
images, particularly for low-luminosity, dwarf galaxies. These stars
can introduce significant contamination and affect measurements of
intrinsic _𝑀_ _★_ or SFR, making it challenging to get reliable SED
modelling, especially for galaxies located along the line-of-sight of
the MW disk. To mitigate this effect, similar to the approach employed
by Clark et al. (2018) and Verstocken et al. (2020) carried out for
the DustPedia project (Davies et al. 2017), we utilize the `PTS-7/8` [15]

(Verstocken et al. 2020) software, the Python toolkit associated to the
SKIRT radiative transfer code (Camps & Baes 2015; Camps & Baes
2020). We remove the foreground stars from the GALEX far-UV up
to _Spitzer_ 24 _𝜇_ m images. The `PTS-7/8` software retrieves the source
catalogue from the 2MASS All-Sky Catalog of Point Sources (Cutri
et al. 2003), identifies point sources in the input image, and performs
interpolation using the surrounding pixels within a region defined by
the FWHM of each point source. The contaminated pixels are then
replaced through interpolation.

                                        Given NGC 6822’s wide span across the sky with its central 12 [′]
wide stellar bar and its closeness to the MW plane, we include an
additional step in the foreground source removal process. NGC 6822
is very close to us with a distance of ∼ 0.50 Mpc, such that the stars
within the galaxy are also in the 2MASS Catalog of Point Sources
with severe contamination from MW foreground stars. To distinguish
stars belonging to NGC 6822 from the MW foreground stars, we combine two source catalogues provided by Hirschauer et al. (2020) and
Gaia DR3 catalogue (Gaia Collaboration et al. 2016; Gaia Collaboration et al. 2023). We initially run the `PTS-7/8` through the far-UV
to mid-IR multi-wavelength images of NGC 6822, to detect and compile a catalogue of all identified point sources for subsequent masking
purposes. To distinguish Milky Way/main sequence (MW/MS) stars
within NGC 6822, we perform a cross-match of coordinates between


14 `[https://idlastro.gsfc.nasa.gov/ftp/pro/idlphot/sky.pro](https://idlastro.gsfc.nasa.gov/ftp/pro/idlphot/sky.pro)`
15 `[https://github.com/SKIRT/PTS](https://github.com/SKIRT/PTS)`


MNRAS **000**, 1–19 (2024)

6 _H.-J. Park et al._


the categorized MW/MS sources (from colour-magnitude diagram
by Hirschauer et al. 2020) and the Gaia DR3 source. Allowing a
maximum separation of 1 [′′] between corresponding sources in both
catalogues enables us to classify MW stars located along the line of
sight of NGC 6822, effectively isolating MS stars within NGC 6822.
Subsequently, we remove the stars identified as likely belonging to
NGC 6822 from the source catalogue found earlier by `PTS-7/8`, preserving solely the MW point sources for eventual removal from the
input images.


_2.3.3_ _Image convolution and resampling_


As the next step, we perform image convolution for all images including TYPHOON emission line maps, the photometric images,
and the CO and Hi flux density maps to match with the resolution
of SPIRE 350 _𝜇_ m band (25 [′′] ). Since each instrument has its unique
point spread function (PSF), the choice of individual kernels for the
convolution process depends on the characteristics of both the initial
PSF and the desired PSF. To facilitate the convolution process, we
utilize a set of kernels provided by Aniano et al. (2011) [16], along with
the corresponding IDL code. This enables us to readily implement
convolution on the given images to achieve the desired resolution.
For the cases of NGC 1566 and NGC 6822, the final beam size is
set to larger than the other galaxies as the coarsest resolution among
the used multi-wavelength data is not SPIRE 350 _𝜇_ m, but Hi data
(see Table 2 and Table C1). Considering the major beam sizes of
NGC 1566 and NGC 6822 Hi data are 42 [′′] and 42.4 [′′], respectively,
we set 43 [′′] as their final resolution. In the convolution process, we
use the closest desired resolution of 41 [′′] using kernels provided by
Aniano et al. (2011).
Once the convolution process is complete, we resample the images using `SWARP` [17] (Bertin et al. 2002), ensuring that the pixel scale
matches the PSF of the coarsest image, which has a spatial resolution of 25 [′′], or 43 [′′] for NGC 1566. Resampling the final pixel to be
comparable with the PSF size of the SPIRE 350 _𝜇_ m ensures that our
regions can be considered independent.
For the cases of NGC 6822 and Sextans A, as an exception,
we resample the convolved multi-wavelength images including TYPHOON data into the physical resolution of 200 pc per pixel (i.e.,
82.5 [′′] and 29.7 [′′], respectively). This is to ensure reliable dust masses,
which occur for regions with log _𝑀_ dust _>_ 3 (see Figure 10 of Smith
& Hayward 2018). This threshold is exceeded for the regions in
NGC 6822 and Sextans A considered in this work.


_2.3.4_ _Photometric uncertainty measurement_


The photometric uncertainty associated with each pixel in the given
image is determined by the standard combination of the Poisson
error, the scatter in the sky values, and the uncertainty in the mean
sky. The calculation of the uncertainty is expressed as follows:



area of the sky apertures in native pixels squared. _𝑠𝑘𝑦_ and _𝐴_ ( _𝑠𝑘𝑦_ )
values are measured using sky.pro, an IDL photometry tool. The
unit conversion, image convolution, and resampling processes are
also applied to these uncertainty maps as implemented for the flux
density maps.


**3** **METHOD**


In this section, we describe the method we employ to measure the
physical parameters including the _𝑀_ dust using a SED modelling tool,
gas-phase metallicity, and gas masses (Hi and H 2 components) of
each region in individual galaxies.


**3.1** **SED modelling: MAGPHYS**


We use the `MAGPHYS` (Multi-wavelength Analysis of Galaxy Physical
Properties) framework (da Cunha et al. 2008; Battisti et al. 2019)
to perform spectral energy distribution (SED) modelling and derive
various physical properties in a spatially resolved manner, including
the _𝑀_ _★_, SFR, and _𝑀_ dust . `MAGPHYS` is a powerful tool designed to analyze and interpret the observed UV to the sub-mm luminosity of a
given sample by constructing optical and infrared emission libraries
that account for both stellar and dust components. The code builds
optical libraries assuming the Chabrier initial mass function (IMF;
Chabrier 2003), the stellar population synthesis model from Bruzual
& Charlot (2003), and metallicity range from 0.2 _<_ _𝑍_ / _𝑍_ ⊙ _<_ 2 at the
given redshift. The star formation history (SFH) is modelled with a
combination of an underlying continuous model and randomly superimposed starbursts to approximate more realistic SFHs. The dust
attenuation effect is accounted for by considering two components:
the birth cloud (age less than 10 Myr) and the surrounding ISM
(age more than 10 Myr), using the prescription from Charlot & Fall
(2000). To construct the infrared libraries, `MAGPHYS` assumes that the
attenuated stellar emission by dust is re-emitted at mid-IR through
far-IR wavelengths, thereby maintaining energy balance. The infrared
libraries are built with a sum of three components: Polycyclic aromatic hydrocarbons (PAHs), warm dust components ( _𝑇_ dust of 30–70
K), and cold dust components ( _𝑇_ dust of 15–25 K). The code then compares the modelled SED with the observed SED, calculates _𝜒_ [2], and
finds the best-fit combination of models. The probability distribution
functions (PDFs) are calculated for individual physical parameters
based on the likelihood distribution from the Bayesian approach.
Unlike conventional usage where integrated fluxes of entire galaxies are considered, we focus on characterizing properties at a smaller
scale, which would likely be smaller compared to integrated measurements. To take this into account, we adjust the posterior range
of several physical parameters in the `MAGPHYS` code. Specifically, we
modify the code to allow lower _𝑀_ _★_ (5 _<_ log _𝑀_ _★_ / _𝑀_ ⊙ _<_ 11), SFR (-5
_<_ log SFR/ _𝑀_ ⊙ yr [−][1] _<_ 1.5), dust luminosity (5 _<_ log _𝐿_ dust / _𝐿_ ⊙ _<_
10), and _𝑀_ dust (2 _<_ log _𝑀_ dust / _𝑀_ ⊙ _<_ 7). Figure 1 shows an example
of the SED fit result derived by `MAGPHYS` for a spaxel of NGC 3521.
We exclude pixels with calculated _𝜒_ [2] values larger than _𝜇_ ( _𝜒_ [2] ) +
3 × _𝜎_ ( _𝜒_ [2] ), where _𝜇_ ( _𝜒_ [2] ) and _𝜎_ ( _𝜒_ [2] ) are the median and standard
deviation, of the obtained _𝜒_ [2] distributions of individual galaxies.
Additionally, we remove pixels with _𝑀_ dust probability distribution
that spreads out over a wide range, as this indicates unreliable median
_𝑀_ dust values. To achieve this, we calculate the ratio between the
median _𝑀_ dust and the standard deviation (averaging the 16% and
84% percentiles) and exclude pixels with a ratio smaller than 1.



_𝜎_ =



√︄



_𝑓_ ( _𝜆_ ) + _𝐴_ ( _𝑎𝑝_ ) × _𝑠𝑘𝑦_ [2] + _[𝐴]_ [(] _[𝑎]_ _[𝑝]_ [)] [2] [ ×] _[ 𝑠𝑘]_ _[𝑦]_ [2] _,_ (3)

_𝐴_ ( _𝑠𝑘𝑦_ )



where f( _𝜆_ ) indicates the number of photons received at a given wavelength (i.e., Poisson error), _𝐴_ ( _𝑎𝑝_ ) denotes the area of the galaxy’s
aperture measured in pixels squared, _𝑠𝑘𝑦_ corresponds to the standard
deviation of the sky values per native pixel, and _𝐴_ ( _𝑠𝑘𝑦_ ) represents the


16 `[https://www.astro.princeton.edu/~draine/Kernels.html](https://www.astro.princeton.edu/~draine/Kernels.html)`
17 `[https://www.astromatic.net/software/swarp/](https://www.astromatic.net/software/swarp/)`


MNRAS **000**, 1–19 (2024)

_Resolved dust evolution in nearby galaxies_ 7





































**Figure 1.** Example of SED fit results derived by `MAGPHYS` for a spaxel in NGC 3521. The top half panel presents the best-fit attenuated SED model (black solid
line) and the unattenuated SED model (green solid line) for the given pixel coordinate, along with measured photometry (blue squares) and their errors. The
spectroscopic redshift and _𝜒_ [2] value are shown in the top right corner. The lower portion displays the residuals between the model and observed luminosities.
The bottom half panels show the likelihood distributions of key parameters: _𝑀_ _★_, SFR, specific star formation rate (sSFR), dust luminosity ( _𝐿_ dust ), _𝑀_ dust, cold
dust temperature in the ambient ISM ( _𝑇_ C [ISM] ), and warm dust temperature in the ISM ( _𝑇_ W [ISM] ). The numbers in the top right of each panel represent the median
values, while the 16% (‘-’) and 84% (‘+’) symbols indicate the standard deviation.



**3.2** **Gas-phase metallicity: Scal**


Oxygen is the most abundant element in the universe following hydrogen and helium and does not undergo significant depletion onto
dust grains (Draine 2011). Thus, the relative abundance of oxygen to
hydrogen in _gas-phase_, commonly represented as 12+log(O/H), can
serve as a proxy for the overall metal abundance in the ISM (Kewley et al. 2019). Oxygen abundances are most accurately obtained
using temperature-sensitive auroral lines that rely on direct electron temperature measurements. However, in low-excitation, oxygenrich regions, these lines are often too weak to be detected. Consequently, numerous studies have attempted to empirically derive the
gas phase metallicity through various combinations of strong emission lines (i.e., ‘strong-line’ methods), such as R 23 (Pagel et al. 1979),
N2H _𝛼_ (Storchi-Bergmann et al. 1994), and Scal (Pilyugin & Grebel
2016). Theoretical approaches (e.g., N2O2 – Kewley & Dopita 2002;
N2S2H _𝛼_ – Dopita et al. 2016) and combinations of empirical and theoretical methods (e.g., O3N2 – Pettini & Pagel 2004; N2 –Denicoló
et al. 2002) have also been developed to determine gas-phase metallicity.


For our analysis, we choose the Scal metallicity diagnostic (Pilyugin & Grebel 2016). Among the many popular metallicity tracers, we
exclude diagnostics that rely on [O II] _𝜆_ 3726, _𝜆_ 3729 emission lines.
These lines are located at the blue wavelength end of TYPHOON
spectra, where the sensitivity is notably lower relative to the red
end. The Scal calibration has been shown to agree with _𝑇_ e -based
abundances within ∼ 0.1 dex over a wide metallicity range (7.0 _<_
12+log(O/H) _<_ 8.6; Pilyugin & Grebel 2016). Also, this calibration
shows relatively low sensitivity towards variation in gas pressure or
ionization parameters. Moreover, as described in De Vis et al. (2017),
this diagnostic is one of the most reliable metallicity calibrations for
low-metallicity sources.



We note that the lines used here are dust extinction corrected using
Equation 2. Throughout the subsequent sections, we use the terms
gas-phase metallicity ( _𝑍_ gas ) and 12+log(O/H) interchangeably.
However, it is well known that the different metallicity diagnostic
provides large discrepancies in absolute oxygen abundances from
one another diagnostic, which can vary up to 0.7 dex (e.g., Kewley &
Ellison 2008; Poetrodjojo et al. 2019; Groves et al. 2023). Although
this is out of the scope of this study, we present our main analysis
with different metallicity diagnostics in Appendix A.


**3.3** **Gas mass**


Hi 21 cm emission lines are often assumed to be optically thin,
allowing us to directly convert the observed Hi 21 cm flux density to


MNRAS **000**, 1–19 (2024)



The Scal calibration uses the following three ratios:


N 2 = ([N II] _𝜆_ 6548 + 6583)/H _𝛽,_


S 2 = ([S II] _𝜆_ 6716 + 6731)/H _𝛽,_


R 3 = ([O III] _𝜆_ 4959 + 5007)/H _𝛽,_


and divides lower and higher branches defined by log N 2 . We apply
the intrinsic [N II] and [O III] intensity ratio fixed to the ratio given
by quantum mechanics (Storey & Zeippen 2000), as their ratios are
independent of physical conditions ([N II] _𝜆_ 6583 / [N II] _𝜆_ 6548 =
3.05 and [O III] _𝜆_ 5007 / [O III] _𝜆_ 4959 = 2.98). The oxygen abundance
at the lower branch which has log N 2 ≤− 0.6 is described as



12 + log(O/H) L

= 8 _._ 072 + 0 _._ 789 log(R 3 /S 2 ) + 0 _._ 751logN 2

+ (1 _._ 069 − 0 _._ 170log(R 3 /S 2 ) + 0 _._ 022 logN 2 ) × logS 2 _,_



(4)



while the oxygen abundance at the higher branch (log N 2 _>_ − 0.6)
can be calculated as



12 + log(O/H) H

= 8 _._ 424 + 0 _._ 030 log(R 3 /S 2 ) + 0 _._ 751 logN 2

+ (−0 _._ 349 + 0 _._ 182 log(R 3 /S 2 ) + 0 _._ 508 logN 2 ) × logS 2 _._



(5)

8 _H.-J. Park et al._



the Hi gas mass ( _𝑀_ HI ) using the following equation (Roberts 1962):
M HI = 2 _._ 36 × 10 [5] D 2 [�] S [HI] int (1 + z) [−][2] _,_ (6)
� M ⊙ � � Mpc � Jy kms [−][1] �

where _𝐷_ is the distance of the galaxy, _𝑆_ int [HI] [is the integrated Hi flux,]
and _𝑧_ is the redshift. We use the redshift to calculate the luminosity
distance, to maintain consistency when comparing and combining
Hi gas mass measurements with other physical properties ( _𝑀_ _★_ and
_𝑀_ dust ) derived from `MAGPHYS` SED fit. We note that the distance
terms cancel out in the DGR or other parameters regarding mass
ratios of ISM tracers.

Due to the lack of a dipole moment in molecular hydrogen, a direct
measurement of H 2 molecular gas mass is challenging. Therefore,
many studies resort to using [12] CO (1-0) observations as a proxy,
as CO is the next most abundant molecule after H 2 and tends to
trace similar regions. [12] CO (2-1) rotational transition is widely used
alternatively thanks to its relatively cheaper observations (∼ 2–4
times faster than mapping [12] CO (1-0) to the same mass surface
density, sensitivity, and angular resolution; Leroy et al. 2021b). With
the [12] CO (2-1) observations, we convert the measured [12] CO (2-1)
intensity to [12] CO (1-0) first using the intensity ratio between two
lines ( _𝑅_ 21 ), and then to H 2 surface density using the conversion
factor ( _𝛼_ CO ) using following empirical relations.

_𝐼_ 12 CO(1−0) = _𝑅_ 21 [−][1] [×] _[ 𝐼]_ [12] CO(2−1) _[,]_ (7)


where _𝑅_ 21 is assumed as 0.63 (Leroy et al. 2021b; den Brok et al.
2021). den Brok et al. (2021) found the luminosity-weighted mean
_𝑅_ 21 = 0 _._ 63±0 _._ 09, which is included in the uncertainty measurement.
The derived [12] CO (1-0) is converted into Σ mol (Σ _𝐻_ 2 × 1.36 to
correct Helium abundance) under the assumption of optically thick
12 CO (1-0) emission.



�



D
= 2 _._ 36 × 10 [5]
� � Mpc



2 [�] S [HI]
int
� Jy kms [−][1]





(1 + z) [−][2] _,_ (6)



1.0


|Kauffmann et al 2003<br>.<br>Kewley et al 2001<br>.|Col2|
|---|---|
|.0<br>1.5<br>1.0<br>0.5<br>log10([NII]/H )|0.0<br>0.<br>|



cos ( _𝑖_ ) (1 + _𝑧_ ) [−][1] _,_ (8)
�



_𝛼_ _𝐶𝑂_
Σ mol =
� _𝑀_ ⊙ _𝑝𝑐_ [−][2]



_𝐼_ 12 _𝐶𝑂_ (1−0)
�� _𝐾𝑘𝑚𝑠_ [−][1]



0.5


0.0


0.5


1.0


1.5


**Figure** **2.** The BPT diagram for all regions in sample galaxies. The filled
circles are colour-coded by galaxy. The black dashed line indicates the criteria
defined by Kewley et al. (2001). In this study, we use Kauffmann et al. (2003)
criteria to be conservative for star-forming H II region selection. Grey circles
present regions where affected by other sources than star-forming activity.


licity diagnostics in Section 3.2 rely on physical conditions that are
typical for star-forming H II regions. Hence, it is crucial to exclude
pixels heavily affected by active galactic nuclei (AGN) or shocks. To
achieve this, we employ the Baldwin-Phillips-Terlevich (BPT) diagram introduced by Baldwin et al. (1981). To ensure the accuracy
of our metallicity measurements in Section 3.2, we adopt the Kauffmann et al. (2003) separation (blue solid line) to focus solely on
genuine star-forming regions. The star-forming H II regions used in
our resolved analysis are shown in black dots.


**4** **RESULT**


**4.1** **The global DGR–** _𝑍_ gas **relation**


As a sanity check on our methodology before examining spatially resolved relationships, we first investigate the relationship between the
dust-to-gas mass ratio (DGR) and the gas-phase metallicity ( _𝑍_ gas ) of
our sample galaxies on a global scale. To obtain the galaxy-integrated
physical parameters such as _𝑀_ dust, _𝑀_ gas ( _𝑀_ atom and _𝑀_ mol ) and
_𝑀_ _★_ for individual galaxies, we sum up the measured quantity of each
parameter of pixels within the optical radius ( _𝑟_ 25 ) listed in Table 1.
We measure the global metallicity (with Scal calibration) of the
individual galaxies based on integrated emission line ratios of starforming H II regions within each galaxy. Specifically, we sum up
the emission line fluxes required for the metallicity diagnostic from
star-forming H II regions within _𝑟_ 25 . We then calculate emission line
ratios using the metallicity diagnostic equations (Equation 5). We
highlight that the wide FoV of TYPHOON data allows us to measure
reliable _𝑍_ gas, encompassing the bulk of SF regions and ISM. The
DGR values assuming _𝛼_ CO _,_ Z tend to be smaller than those with
_𝛼_ CO _,_ MW aligning with expectations since _𝛼_ CO _,_ Z increases at lower
metallicity. However, we observed minimal deviation between the
two DGR measurements, with a median discrepancy of less than 0.1
dex.

Figure 3 illustrates the relationship between global DGR and _𝑍_ gas,



where _i_ is the inclination of the galaxy. For NGC 625, NGC 1705,
NGC 5253, and NGC 6822, as we use [12] CO (1-0) intensities, we
directly convert the observed [12] CO (1-0) intensity to the molecular
gas surface density (Σ _𝑚𝑜𝑙_ ) without applying _𝑅_ 21 . The molecular gas
mass ( _𝑀_ mol ) is calculated from the estimated Σ mol .
There have been many studies investigating its dependency on the
metallicity of galaxies or regions, finding that it tends to increase
as the metallicity decreases (e.g., Amorín et al. 2016, Chiang et al.
2023). Amorín et al. (2016) explored this relationship in 21 blue compact dwarf galaxies and proposed a metallicity-dependent conversion
factor described by the equation:


log ( _𝛼_ CO _,_ Z ) = 0 _._ 68 − 1 _._ 45 × (12 + log(O/H) − 8 _._ 7) _._ (9)


This equation highlights a possible underestimation of _𝑀_ mol when
using the constant _𝛼_ CO _,_ MW value, which is measured as 4.35
_𝑀_ ⊙ pc [−][2] (K km s [−][1] ) [−][1] (Strong & Mattox 1996). However, the accuracy of the _𝛼_ CO is still under debate (Bolatto et al. 2013) thus we
mainly focus on the _𝛼_ CO _,_ MW . which is measured from the MW for
further analysis. (Bolatto et al. 2013). We note that these factors are
helium abundance corrected (36 %). The total gas mass of the region
is measured by summing the _𝑀_ HI and _𝑀_ mol as _𝑀_ gas = 1.36 × _𝑀_ HI +
_𝑀_ mol . The helium contribution is also corrected for the Hi gas mass
by multiplying a factor of 1.36.


**3.4** **H II region selection: BPT diagram**


To ensure accurate measurements of the metallicity in specific regions, we exclusively consider star-forming regions, as our metal

MNRAS **000**, 1–19 (2024)

Name 12+log(O/H) log 10 DGR
Calibration Scal _𝛼_ CO _,_ MW _𝛼_ CO _,_ Z   - Scal


NGC 625 8.167 ± 0.005 -2.48 ± 0.04 -2.51 ± 0.06

NGC 1512 8.567 ± 0.010 -2.82 ± 0.01 -2.83 ± 0.01

NGC 1566 8.549 ± 0.005 -2.53 ± 0.03 -2.62 ± 0.03

NGC 1705 8.087 ± 0.005 -2.94 ± 0.12 -2.96 ± 0.16

NGC 3521 8.573 ± 0.003 -2.30 ± 0.01 -2.34 ± 0.01

NGC 4536 8.503 ± 0.006 -2.32 ± 0.01 -2.41 ± 0.01

NGC 5236 8.591 ± 0.002 -2.20 ± 0.01 -2.36 ± 0.01

NGC 5253 8.199 ± 0.003 -2.37 ± 0.02 -2.41 ± 0.02

NGC 6822 8.191 ± 0.012 -2.87 ± 0.05 -2.87 ± 0.03

NGC 7793 8.354 ± 0.006 -2.32 ± 0.01 -2.42 ± 0.01


_>_ -4.33± 0.09
Sextans A 7.536 ± 0.022 _>_ -4.27 ± 0.09
( _>_ -4.96)


**Table** **3.** Measurements of 12+log(O/H) (Scal) and DGR ( _𝛼_ CO _,_ MW and
_𝛼_ CO _,_ Z ) within optical radius ( _𝑟_ 25 ). The uncertainty is calculated from the error propagation, taking into account each pixel’s uncertainty. For Sextans A,
we present the DGR from _𝑀_ mol limit using _𝛼_ CO _,_ MW, _𝛼_ CO _,_ Z, and [C II]-based
_𝑀_ mol in parenthesis.


showing data points colour-coded by galaxy. Our DGR measurements
incorporate _𝑀_ mol estimations derived from the constant _𝛼_ CO _,_ MW
(star-shaped points) and the metallicity-dependent _𝛼_ CO _,_ Z (circular
points). We show the DGR measurement for Sextans A as an open
circle to show an upper limit as only the _𝑀_ atom is considered. Additionally, we present two lower bounds of the DGR in the embedded
panel based on the _𝑀_ mol mass limit derived from its CO (1-0) emission sensitivity map (see Section 2.2.1), by integrating noise values
of pixels in the aperture size chosen in this study (i.e., _𝑟_ 25 ). The plus
symbol shows the DGR lower bound obtained using _𝛼_ CO _,_ Z and the
filled circle shows that using _𝛼_ CO _,_ MW . We note that the _𝑀_ mol limit
from _𝛼_ CO _,_ MW plays a negligible role in DGR measurements, making the lower bound of DGR hardly seen (overlapping with the open
circle). The open diamond symbol connected to the circle presents
the ‘conservative’ DGR values calculated from the _𝑀_ H 2 / _𝑀_ HI of 4
from [C II] 158 _𝜇_ m measurement in Cigan et al. (2021). We discuss
this more in Section 5.1.2.

The grey-shaded region shows the density map of data from Galliano et al. (2021) of ∼800 DustPedia and DGS galaxies. In their work,
they derived global DGR ( _𝛼_ CO _,_ MW = 4.35 _𝑀_ ⊙ pc [−][2] (Kkm s [−][1] ) [−][1] )
and _𝑍_ gas (Scal) values. We also show their 4th polynomial fit result
and the 1 _𝜎_ uncertainty (black and grey dashed lines, respectively;
equations 8 and 9 in Galliano et al. 2021). It is important to note a
caveat in this comparison: for some low-metallicity galaxies in their
sample, the _𝑀_ mol values were estimated using a scaling relation between _𝑀_ atom / _𝑀_ _★_ and _𝑀_ mol / _𝑀_ atom (see Equation 5 of Casasola et al.
2020) due to the non-detection of CO.
The global DGR– _𝑍_ gas relationship for TYPHOON galaxies aligns
well with the literature trend, falling within 1 _𝜎_ (see circles for a fair
comparison in terms of the same calibrations used). Two galaxies,
Sextans A and NGC 1512, are noticeable with their offset from the
reference trend. NGC 1512 deviates from the general trend towards
lower DGR by ∼ 0.6 dex. It is attributed to its unique Hi distribution,
with most of the Hi located at larger radii about ∼ 4 times the optical
disk (Koribalski & López-Sánchez 2009; also see Figure D1).


**4.2** **The resolved ISM scaling relations**


In the following analysis of the ISM scaling relations, we only show
the resolved _𝑀_ mol or resolved DGR values calculated using the



5


6


12+log(O/H) (Scal)


**Figure** **3.** The global DGR– _𝑍_ gas relationship. The x-axis shows the oxygen
abundance (i.e., _𝑍_ gas ) derived using the Scal calibration. The DGR values of
each galaxy are from _𝑀_ mol both _𝛼_ CO _,_ MW and _𝛼_ CO _,_ Z and are shown with the
circles and pluses. The top x-axis presents the metallicity in a unit of solar
metallicity converted from the oxygen abundance with an assumption of _𝑍_ ⊙
= 8.69 (Asplund et al. 2009) and the composition ratio of other chemical
elements is the same as the sun. The cyan open circle presents Sextans A
whose _𝑀_ gas only considers the detected _𝑀_ atom and the mass sensitivity limit
from the CO rms map. The cyan open diamond symbol connected to the open
circle shows the application of the conservative molecular gas amount from

[C II] emission. The grey background density map shows the literature trend
(Galliano et al. 2021, applicable only for any comparison with DGR _𝛼_ CO _,_ MW ).
The sub-plot focusing on Sextans A presents the DGR lower limit from the
assumption of _𝛼_ CO _,_ MW (filled circle, not visible due to its similar value with
DGR value without _𝑀_ mol ; shown as the open circle) and _𝛼_ CO _,_ Z (filled plus)
for _𝑀_ mol using the CO sensitivity map. The black and grey dashed lines
represent the fourth polynomial fit from the literature and the 1 _𝜎_ uncertainty,
respectively. The colour-coded symbols are the same as previous figures.


_𝛼_ CO _,_ MW to reduce any uncertainty that could be raised by employing

_𝛼_ CO _,_ Z .
_𝑀_ mol _/𝑀_ atom _–𝑀_ atom _/𝑀_ _★_ _relation_ : We probe the resolved relation
between _𝑀_ atom / _𝑀_ _★_ and _𝑀_ mol / _𝑀_ atom, which will give us a hint of
how much _𝑀_ mol would reside in resolved regions in Sextans A (for
the similar approach at global scale, see Casasola et al. 2022; De Vis
et al. 2019; Galliano et al. 2021). In Figure 4, the literature trend
from 245 DustPedia late-type galaxies by Casasola et al. (2020) is
shown with a dashed line [18] . The dark red solid line shows the best-fit

linear relation:


log 10 ( _𝑀_ atom / _𝑀_ _★_ ) = −0 _._ 40 log 10 ( _𝑀_ mol / _𝑀_ atom − 1 _._ 02) (10)


with the extrapolated line towards lower _𝑀_ mol / _𝑀_ atom region.
Some of the higher mass/metallicity galaxies are moderately consistent with the literature trend (global; Casasola et al. 2020). How

18 The original relation in their paper is _𝑦_ = −0 _._ 57 _𝑥_ − 1 _._ 18. As their scaling
relation does not consider helium abundance to _𝑀_ mol and _𝑀_ atom, we adjusted
their relation by adding a helium abundance correction factor of 1.36 in this
figure. This changes the y-intercept of the relation increased by ∼ 0.133
(= log 10 1 _._ 36).


MNRAS **000**, 1–19 (2024)



_Resolved dust evolution in nearby galaxies_ 9


Z/Z (metallicity)
1 0
10 10



2


3


4

10 _H.-J. Park et al._


2

#### Sextans A

1


0


1


2



This work

Casasola et al. 2020



3



8 6 4 2 0 2
log 10 M mol /M atom ( CO, MW [)]



**Figure 4.** The scaling relation between the atomic gas to stellar mass fraction
( _𝑀_ atom / _𝑀_ _★_ ) as a function of the molecular gas fraction ( _𝑀_ mol / _𝑀_ atom ) in a
spatially resolved scale. The _𝑀_ mol is from the constant _𝛼_ CO _,_ MW . The dark-red
solid line presents the linear fit from this study with the extension towards the
lower _𝑀_ mol / _𝑀_ atom as a dotted line. The black dashed line shows the global
measurements from Casasola et al. (2020). The cyan stripe indicates where
the resolved _𝑀_ atom / _𝑀_ _★_ of Sextans A belongs. The colour-coded symbols and
the reference are the same as previous figures.


ever, when considering our resolved measurement extending down to
_𝑀_ mol / _𝑀_ atom of 10 [−][4], we find a shallower slope. For dwarf galaxies
such as NGC 625, NGC 1705, NGC 5253, and NGC 6822, the correlation between these two parameters is less evident, displaying a
broader scatter compared to larger galaxies with higher _𝑀_ mol / _𝑀_ atom
values. We show the _𝑀_ atom / _𝑀_ _★_ range for regions within Sextans A,
denoted by a cyan stripe. The _𝑀_ mol / _𝑀_ atom range predicted from the
linear fit extrapolation corresponds to −6∼−5 in the logarithmic unit,
implying these regions are highly dominated by atomic gas.
_DGR–𝑀_ gas _/𝑀_ _★_ _relation_ : In Figure 5, we show how the DGR of
regions in our sample galaxies varies as a function of the specific gas
mass (= _𝑀_ gas / _𝑀_ _★_ ), which can be a tracer of galaxy evolution in the
way of more gas in the region being consumed to form stars, decreasing the specific gas mass. We note that the different assumption of
_𝛼_ CO for DGR values shows only a minor difference, which is hinted
in the global DGR– _𝑍_ gas relationship in Figure 3. As applied to the
galaxy-integrated measurement, for Sextans A, we include the _𝑀_ mol
from the CO sensitivity map for the resolved DGR. Also, including
_𝑀_ mol mass limit ( _𝛼_ CO _,_ MW ) has little to no effect on the DGR for this
galaxy. In addition, the uncertainties in _𝑀_ dust and _𝑀_ HI measurements
are larger than the anticipated range of DGR variations derived from
the CO sensitivity map.
The grey density map in the background shows the literature trend
with DustPedia+DGS galaxies from Galliano et al. (2021). An anticorrelation between the two parameters has been shown, suggesting
that when there are more stars per gas (inverse specific gas mass),
it is easier for the gas to be enriched in dust (also in metal). The
vertically extended DGR feature at a specific gas mass of ∼ 0.1 is
predominantly populated by early-type galaxies.
As in the literature, an anti-correlation is also observed in the
resolved specific gas mass and DGR. Another noticeable feature is


MNRAS **000**, 1–19 (2024)



Galliano et al. 2021 (N = 798; Scal, CO, MW [)]


2


3


4


5


6

2 1 0 1 2
Specific gas mass, M gas /M ( CO, MW [)]


**Figure 5.** The scaling relation between the DGR as a function of the specific
gas mass ( _𝑀_ gas / _𝑀_ _★_ ) in a spatially resolved scale. The background density
map shows DustPedia+DGS galaxies studied by Galliano et al. (2021). The
colour-coded symbols are the same as previous figures.


that the more massive galaxies have shallower/flat trends than lower
mass galaxies (NGC 1705 and Sextans A). This is possibly consistent
with the stochastic star-forming activities in dwarf galaxies. A smaller
galaxy has a low average SFR, but the rate fluctuates widely between
bursts and quiescent levels as cells individually and in small groups
experience star formation.


**4.3** **The resolved DGR–** _𝑍_ gas **relation**


Figure 6 presents the resolved DGR– _𝑍_ gas relationship of TYPHOON
galaxies, which generally follows the global trend (except for regions
in Sextans A). The scatter is large in both DGR and _𝑍_ gas as we can
capture fluctuations at (sub-)kpc scale. One of the most notable features from our measurements is that the several star-forming regions
in Sextans A have DGR values of 0.5-2 dex higher than the literature values at fixed metallicity. Additionally, while the resolved _𝑍_ gas
values of this galaxy are spread across ∼ 1 dex, implying chemical
inhomogeneity within the galaxy, DGR values are relatively homogeneous given that the DGR varies only within ∼ 0.5 dex. The wide
range of _𝑍_ gas (7.1 _<_ 12+log(O/H) _<_ 7.7) can be interpreted with a few
distinguishable H II regions having different star formation histories
in Sextans A investigated by Gerasimov et al. (2022): northeast (NE)
and southwest (SW) regions; see Figure **??** for metallicity spatial
distribution. The two regions have different metallicity ranges such
as 7.3 _<_ 12+log(O/H) _<_ 8.1 and 7.0 _<_ 12+log(O/H) _<_ 7.2 for NE
and SW regions, respectively. Regarding star formation history, the
NE region has had the most energetic star formation activities in the
galaxy since ∼ 200 Myr ago and already started to be enriched in
metal abundance presenting a higher 12+log(O/H). In contrast, for
the SW region, star-forming activity has likely started very recently

∼
( 20 Myr ago), having a lower 12+log(O/H) (Boyer et al. 2009).
A large scatter stands out at the intermediate or critical metallicity
regime (0.05–0.3 _𝑍_ / _𝑍_ ⊙ ; 7.5 _<_ 12+log(O/H) (Scal) _<_ 8.2), agreeing
with the chemical evolution models (e.g., Asano et al. 2013 and De
Vis et al. 2017). In the theoretical view, the DGRs in this regime are

### 2 3



_Resolved dust evolution in nearby galaxies_ 11

## Z/Z (metallicity)

1 0
### 10 10


Galliano et al. 2021 (global)

De Cia et al. 2016 - DLAs

This work (2nd polynomial, Equation 12)

This work (Dust evolution model)

Schneider et al. 2016 (global)


SBS 0335-052


### 4 5

I Zw 18

### 6 7.0 7.5 8.0 8.5
## 12+log(O/H) (Scal)


**Figure 6.** The resolved DGR– _𝑍_ gas relationship of TYPHOON galaxies (colour-coded by galaxy) and the global relationship from references: The 4th polynomial
fit for nearby DustPedia+DGS galaxies from Galliano et al. (2021) (black dashed line). The DGR from depletion methods with DLAs at higher- _𝑧_ is from De
Cia et al. (2016) (grey cross symbols). The red solid line presents the best fit for resolved TYPHOON galaxies. The blue-shaded area shows the dust evolution
model ( `BEDE` ) runs with dust-related parameters at 16-84th probability distribution. The blue dashed line presents the 4th polynomial fit for the models. Green
plus symbols are the global DGR measurements for dwarf galaxies with different gas densities studied in Schneider et al. (2016). The colour-coded symbols are
the same as previous figures.



predicted to rapidly increase as a function of metallicity compared
to those in the high-/low- metallicity regimes. Specifically, in this
critical metallicity regime, the dust evolution mechanism starts to be
more efficient, as the dust growths in the ISM begin to contribute.
The critical metallicity of a system can vary and be determined by
the system’s characteristics, such as star-formation timescale at a
given time (t), _𝜏_ SF = _𝑀_ ISM (t) /SFR (t). If the _𝜏_ SF is short, rapid
star formation processes lead to early-stage metallicity increases,
thereby accelerating the enrichment of dust with metals compared to
scenarios with longer _𝜏_ SF (Asano et al. 2013; Feldmann 2015).
We provide a best-fit model that describes the observed resolved
DGR– _𝑍_ gas relation by applying the n-th polynomial models. We increase ‘n’ by up to 5 and to find what degree of polynomial fit best
describes the observed DGR– _𝑍_ gas relation, we employ Bayesian Information Criteria (BIC). With an assumption of Gaussian posterior
probability, the BIC can be described below:


_𝐵𝐼𝐶_ = _𝜒_ [2] + _𝑘_ ln( _𝑛_ ) _,_ (11)


where _𝜒_ [2] is the sum of squares of residuals from maximum likelihood, k is the number of model parameters, and n is the sample size
(in our case, n = 346). In the process of calculating _𝜒_ [2], we use the



Orthogonal Distance Regression (ODR) to find the best-fit model at
a given degree of polynomial fit, taking the uncertainties for both the
x-axis (12+log(O/H)) and y-axis (DGR) into account. The derived
best-fit model is shown as a dark red solid line in Figure 6. The
derived best fit for this study (Scal, _𝛼_ CO _,_ MW ) is expressed as below:


log 10 DGR = −1 _._ 1381 _𝑍_ gas [2] [+][ 19] _[.]_ [6996] _[ 𝑍]_ [gas] [−] [85] _[.]_ [4377] _[.]_ (12)


**5** **DISCUSSION**


**5.1** **Understanding the DGR–** _𝑍_ gas **relationship**


_5.1.1_ _Emission vs. absorption line methods_


Recently, many studies have reported tension on the global DGR–
_𝑍_ gas relationship, contrasting emission line-based methods (utilizing
far-IR, Hi, CO, and optical emission line observations) with absorption line-based methods (employing metal depletion measurements
from DLAs) (e.g., De Cia et al. 2016; Roman-Duval et al. 2022a).
Emission line studies often show a change in slope at a certain metallicity, indicating a different mechanism of dust formation. In contrast, absorption line studies show a constant increase of DGR with


MNRAS **000**, 1–19 (2024)

12 _H.-J. Park et al._


_𝑍_ gas through the large range of _𝑍_ gas . Figure 6 shows the DGR– _𝑍_ gas
relation derived from both methods: 1) emission line observations
(global DGR– _𝑍_ gas relation; Galliano et al. 2021) and 2) absorption
line-based depletion method (De Cia et al. 2016).
Numerous factors contribute to this tension such as uncertain
ties both in emission and absorption line-based measurements as
discussed in Roman-Duval et al. (2022a) and Roman-Duval et al.
(2022b). Emission line-based studies possess uncertainties such as
biases in _𝑀_ dust measurements due to different assumptions on the
far-IR opacity of dust in SED modelling. Plus, _𝑀_ dust can be underestimated when it is measured in galaxy-integrated scale (the
‘Matryoshka’ effect that is introduced in Galliano et al. (2018);
also see Section 1). Separating cold regions from warmer regions
can be achieved at the finer resolution, resulting in systematically
higher _𝑀_ dust (by up to 50% higher than galaxy-integrated photometry method) as cold/large dust grains occupy the most _𝑀_ dust obtained.
This has been observed in several studies, for example, in Galliano
et al. (2011), Galametz et al. (2012), Roman-Duval et al. (2014), and
Aniano et al. (2020). The systematic offset disappears when probed at
a few tens parsec scale, which means this high resolution is required
for better capturing the cold _𝑀_ dust . Our spatially resolved measurements, while still limited by resolution (SPIRE 350 _𝜇_ m or Hi-21 cm),
mitigate this effect, providing relatively accurate _𝑀_ dust with a median
physical resolution of 0.594 kpc ranging from 0.200 kpc (NGC 6822
and Sextans A) to 2.279 kpc (NGC 1512). However, `MAGPHYS` (and
most SED modelling codes) assume a fixed dust emissivity index
(i.e., the slope of the RJ tail), and this can introduce systematic biases on the resulting _𝑀_ dust values in the absence of longer wavelength
data (Galliano et al. 2018).
The aperture size chosen is also an important factor in uncertainties of emission line-based methods when it is galaxy-integrated
studies, given different distributions of ISM phases (Leroy et al.
2008; Muñoz-Mateos et al. 2009) (not only the DGR– _𝑍_ gas relation
but also other ISM scaling relations). Typically, stars, dust, molecular
gas, and metals are concentrated within the optical radius ( _𝑟_ 25 ) in
star-forming galaxies, while atomic gas is extended further, up to 2-4
times the optical radius (Hunter 1997; Wang et al. 2013; also see
Figure **??** - **??** ). Therefore, characterizing a galaxy’s atomic gas mass
for global DGR– _𝑍_ gas relationships and other ISM scaling relations
often involves spatially resolved _𝑀_ HI maps from interferometric radio observations and sum up the _𝑀_ HI within the chosen aperture size
(De Vis et al. 2017; De Vis et al. 2019) or an indirect estimation of
_𝑀_ HI within the optical radius from integrated Hi spectra from singledish radio telescopes (Casasola et al. 2020; Li et al. 2023 [19] ). This
effect becomes more noticeable in dwarf irregular galaxies such as
NGC 6822 and Sextans A of our sample, where the Hi gas morphology differs from the distribution of metals, stars, and molecular gas
components. However, this issue is less pronounced at the spatially
resolved scale due to the criteria ensuring reliable mass measurements with _𝑆_ / _𝑁_ ≥ 3.
There are also uncertainties in absorption line-based methods.
Many DGR and metallicity measurements from the depletion pattern investigation using absorption lines are carried out outside the
MW (e.g., Large/Small Magellanic Cloud), but are still based on the
MW depletion pattern. However, this assumption may not always
hold (see Section 3.3.2 in Galliano et al. 2018). The depletion methods for the DGR measurements assume metal depletion onto dust


19 Using observational evidence of the similar shapes in the radial profile of
Hi surface density normalised by Hi radius, _𝑅_ HI and the Hi size-mass relation
(e.g., Wang et al. 2014; Wang et al. 2020)


MNRAS **000**, 1–19 (2024)



and abundance ratios, which are highly uncertain. In particular, the
depletion measurements of carbon and oxygen are challenging because their UV transitions are easily saturated or too weak. Due to
the limited measurements of C and O depletion outside the MW, the
depletion method to estimate the DGRs of the system relies on the
MW relation between the depletion of Fe and C (or O) (De Cia et al.
2016; Péroux & Howk 2020; Roman-Duval et al. 2022a). Additionally, the dust depletion factor [Zn/Fe] is frequently used to measure
dust abundance, given that Zn is a volatile and Fe is a refractory
element. However, this assumption is still debated (see Section 4.1
in Roman-Duval et al. 2022b and references therein).
Given these uncertainties in play, some of which are addressed in
this study, our resolved DGR– _𝑍_ gas relationship seems aligned with
findings from the depletion method for DLAs. Particularly in the
low metallicity range, areas within Sextans A show DGR values
similar to those determined by the depletion method. Nonetheless,
the fact that molecular gas has not been factored into the total _𝑀_ gas
for these regions and that only one galaxy has been considered can be
problematic when concluding. In the subsequent section, we discuss
more on the DGR values in the low metallicity range.


_5.1.2_ _Low metallicity regime - Sextans A_


Detection of CO lines in radio has rarely been successful in low
metallicity systems. They can be simply Hi-dominant systems but
at the same time it could be because they tend to favour CO-dark
or CO-free molecular gas (Bolatto et al. 2013). In such systems,
the more effective penetration of high-energy UV photons through
the low-metal/dust environment can consequently lead to the photodissociation of CO molecules. CO observations thus fail to trace

molecular gas components optimally in the low metallicity systems.
Also for this reason, the metallicity dependant _𝛼_ CO (i.e., _𝛼_ CO _,_ Z ) has
been suggested for the past several years but the uncertainty on it is
still substantial (e.g., Madden et al. 2012; Bolatto et al. 2013 for a
review).
The reliable molecular mass measurement is challenging in the
case of Sextans A among our sample. To handle this issue, many
studies including Rémy-Ruyer et al. (2014), Casasola et al. (2020)
and Galliano et al. (2021) used the ISM scaling relations. The relation
between global _𝑀_ atom / _𝑀_ _★_ and _𝑀_ mol / _𝑀_ atom suggested by Casasola
et al. (2020) has been used for low metallicity DGS galaxies in De
Vis et al. (2019) and Galliano et al. (2021) to infer their global _𝑀_ mol
within the optical radius of low-metallicity galaxies. We thus adopt
this scaling relation but in a resolved scale (see Figure 4). Given the
_𝑀_ atom / _𝑀_ _★_ range of individual regions in Sextans A, the _𝑀_ mol / _𝑀_ atom
is inferred and applied to the DGR of the corresponding regions. We
see only a negligible change in DGRs for regions in Sextans A, far
smaller than the error itself thus we do not show them in the figure.
It should be noted that the _𝑀_ mol / _𝑀_ atom we derived for other galaxies
are derived from the _𝛼_ CO _,_ MW, which might possess a possibility for
_𝑀_ mol being underestimated.
In Cigan et al. (2016), they used one of the far-IR fine spectral lines,

[C II] 158 _𝜇_ m to estimate the _𝑀_ mol in the ISM under an assumption
that [C II], as an important coolant of the ISM in such low-metallicity
systems, can trace the H 2 in photodissociation regions (PDRs). More
recently, Cigan et al. (2021) has inferred that the _𝑀_ mol / _𝑀_ atom for
Sextans A is ∼ 4, from the [C II] line detected in this galaxy. We
consider this molecular gas fraction and estimate the ‘conservative’
gas masses and DGRs of all regions in Sextans A. DGR values after
applying _𝑀_ mol / _𝑀_ atom of ∼ 4 are naturally much lower (by 0.7 dex).
However, the DGR values from [C II] line may be overestimated
because [C II] lines trace molecular gas in PDRs, including diffuse

_Resolved dust evolution in nearby galaxies_ 13



atomic and diffuse molecular gas, which are more extended than
star-forming dense molecular gas regions we probe in this relation.
Considering the conservative _𝑀_ mol for regions in Sextans A returns
that the DGRs of a few regions (decreased by 0.7 dex) agree well with
the literature trend from global trend (Galliano et al. 2021), however,
the DGR values of most Sextans A regions still show being large (up
to ∼ 1 dex than the literature).
The high DGR values observed in Sextans A can be attributed
to the intrinsic large scatter of DGR in low-metallicity regimes.
One of the factors is the gas density, which has been reported in
Schneider et al. (2016) for two galaxies, SBS 0335-052 (12+log(O/H)
∼ 7.27) and I Zw 18 (12+log(O/H) ∼ 7.18). SBS 0335-052 has a
significantly higher global DGR up to 3 dex than I Zw 18 even at
similar metallicity (see green plus symbols in Figure 6). Schneider
et al. (2016) interpret this discrepancy as a result of differences in
gas densities of the two galaxies, suggesting that the high molecular
gas density in SBS 0335-052 ( _𝑛_ mol ∼ 1500 cm [−][3] ) enables grain
growth process in the ISM, which is more efficient dust mass buildup compared to condensation in SNe, despite its low metallicity. On
the other hand, I Zw 18 has a very low gas density ( _𝑛_ mol ∼ 91 cm [−][3] ),
20 times lower than SBS 0335-052. Schneider et al. (2016) hint
that the factor that determines the DGR of a system is not only
the metallicity but also the gas density. This agrees with Chiang
et al. (2018) where the increasing trend of dust-to-metal mass ratio
(DMR ≡ _𝑀_ dust / _𝑀_ metals ) as a function of molecular gas fraction has
been shown in M 101. Furthermore, the argument is supported by the
depletion method in recent work by Hamanowicz et al. (2024), where
they found a trend of DGR values increasing with the higher hydrogen
column density, N(H), in several absorption lines of a few sight-lines
towards Sextans A. They found that at high N(H) ( _>_ 10 [21] cm [−][2] ), the
DGR values are in line with the high DGR values from our work,
whereas at N(H) ∼ 10 [20] cm [−][2], the DGRs are reduced by 1 dex,
reaching the low value found by the literature we are referring to
(Galliano et al. 2021).
Other factors are possible to explain the high DGR values in the
low-metallicity regime, such as higher dust yield from SNe, a minor fraction of dust destruction by SNe, or being affected less by
photofragmentation, which will be covered by model fitting in Section 5.2.


_5.1.3_ _Broken vs. single power law_


We briefly explore the optimal shape of the observed DGR– _𝑍_ gas
relation, contrasting single- (De Vis et al. 2019) or broken- power
laws (Rémy-Ruyer et al. 2014). It should be highlighted that different
authors use different metallicity calibrations so a fair comparison is
challenging. With this caveat in mind, we compare the broken-power
law relation by Rémy-Ruyer et al. (2014), where PT05 metallicity
calibration is used (see Section 1) and the single-power law relation
by De Vis et al. (2019), where Scal is used. To more fairly compare
both relations, we also calculate the resolved DGR– _𝑍_ gas relation with
PT05 metallicity calibration for our galaxies (see the rightmost panel
in Figure A1).
In Figure 7, we show the deviation between the literature DGRs and
the observed DGRs at a fixed _𝑍_ gas, including the median difference
and its standard deviation. Our resolved DGRs are systematically
higher than the two galaxy-integrated studies, hinting that the effect
on the chosen aperture size when deriving the ISM masses is mitigated in our study. The broken power law proposed by Rémy-Ruyer
et al. (2014) has a smaller residual and standard deviation than the
single power law by De Vis et al. (2019).
This finding aligns with similar studies by Vílchez et al. (2019) on



0.5


0.0


0.5


1.0


1.5


7.0 7.5 8.0 8.5
12+log(O/H)


**Figure 7.** The residual of DGR values between the two reference models using
the consistent metallicity calibration: the residuals with the single power law
from De Vis et al. (2019) (Scal; green) and those with the broken power law
from Rémy-Ruyer et al. (2014) (PT05; orange). Each median difference of
DGRs is indicated as dotted and dash-dotted lines, respectively.


Parameter Description Prior range


_𝑆𝑁_ red Factor dust yields for SNe are reduced by 1–5
_𝑘_ frag Photofragmentation of dust grains 0.003–0.5
_𝑘_ gg _,_ cloud Grain growth in the clouds 1000–16000
_𝑓_ dif Maximum dust-to-metal ratio in diffuse ISM 0.2–0.4


_𝑀_ destr _𝑀_ dust destructed per SN 15
_𝑘_ gg _,_ dif Grain growth in the diffuse ISM 5


**Table 4.** Dust-related parameters and their prior range used in this study. We
fixed the _𝑀_ destr and _𝑘_ gg _,_ dif to the reference values from De Vis et al. (2021)
as they are found not to significantly change DGR values.


M 101 and NGC 628 at a spatially resolved scale, where the broken
power-law has been suggested for describing the DGR– _𝑍_ gas relation.
However, it is difficult to make a definitive conclusion about which
functional form better explains the measurements due to the limited
number of low-metallicity regions and the lack of _𝑀_ mol information
in those systems. When considering dust evolution models proposed
in previous studies (e.g., Asano et al. 2013; Feldmann 2015), and to
be discussed in Section 5.2, there is a preference for higher-order relationships over linear functions. On the other hand, given the smaller
residuals of the broken power law compared to the single power law
in intermediate-to-high metallicity regimes (12+log(O/H) _>_ ∼8.0),
the inclusion of molecular gas information for Sextans A would still
support deviations from the single linear relation.


**5.2** **Dust evolution models**


We implement a grid-based chemical evolution model to analyse
the observed resolved DGR– _𝑍_ gas relationship. We utilize a Bayesian
Monte Carlo Markov Chain (MCMC) based one-zone dust evolution
model, `BEDE` [20], developed by De Vis et al. (2021) (also see Rowlands
et al. 2014 and De Vis et al. (2017) for the initial approach). We
fit the model to the entire resolved data points from all galaxies
simultaneously.


20 `[https://github.com/zemogle/chemevol](https://github.com/zemogle/chemevol)`


MNRAS **000**, 1–19 (2024)



1.5


1.0

14 _H.-J. Park et al._



Parameter Probability (50th [84th] 16th [)]


_𝑆𝑁_ red 1.50 [+] − [0] 0 _[.]_ _._ [80] 40
_𝑘_ frag 0.07 [+] − [0] 0 _[.]_ _._ [09] 06
_𝑘_ gg _,_ cloud 4131.81 [+] − [6562] 2550 _[.]_ _._ [80] 28
_𝑓_ dif 0.32 [+] − [0] 0 _[.]_ _._ [00] 00


**Table 5.** The MCMC run result for dust-related parameters with the 16, 50,
and 84th percentile of the probability.


Bayesian MCMC approach. For the full description of the models,
we refer readers to De Vis et al. (2021).
The model DGR value of a system from the model runs is calculated by ( _𝑀_ dust / _𝑀_ gas ; Equation 1), and _𝑍_ gas, or 12+log(O/H) is
measured by the equation following De Vis et al. (2017) and De Vis
et al. (2021) as below:



SN red



k frag



k gg, cloud



f dif



_,_ (13)
�



**Figure 8.** Probability distribution for the MCMC run for dust-related parameters. Each dashed line from the left shows the distribution’s 16th, 50th and
84th percentile. The probability distribution is well constrained generally, but
_𝑘_ frag shows a feature reached to the lower bound (see Section 5.2.2). The
values for each percentile are presented in Table 5.


_5.2.1_ _Model setting_


`BEDE` integrates various factors governing the evolution of gas, stars,
metals, dust, and SFR over time, assuming user-defined basic parameters (e.g., total mass, stellar IMF, star formation history, metal
yields, inflow/outflow rate). We create a grid of total mass ( _𝑀_ tot )
with a range of 8 _<_ log _𝑀_ tot / _𝑀_ ⊙ _<_ 10 with a step size of 0.5 in log
space, and fix the following: 1) stellar IMF to Chabrier (2003) IMF
for consistency with the SED fitting approach (see Section 3.1), 2)
star formation history to have a continuous increase of star formation efficiency (SFE) at an intermediate pace (SFE 0 = 10 [−][9] yr [−][1] in
Equation 9 of De Vis et al. 2021). 3) The metal yield tables for SNe
and AGB stars are set to Limongi & Chieffi (2018) with a stellar
rotational velocity of 150 km s [−][1], and Karakas et al. (2018) with
high mass loss rates. The inflow rate is set to half of the _𝑀_ tot which
means the system has half of the _𝑀_ tot at the beginning of its evolution and the other half amount is accreted from outside. The age
grid of each modelled system starts from 0 to 13.8 Gyr with steps
of 0.3 Gyr. `BEDE` is based on the THEMIS dust model (Jones et al.
2013; Köhler et al. 2015; Jones et al. 2017), taking the dust grains
made up of the mixture of carbon and silicate and allowing the grain
size variation. For consistency with the observed dust mass from
`magphys`, we increase the dust mass from models by 1.075 (De Vis
et al. 2019).
We mainly focus on parameters whose variation affects the shape
of the DGR– _𝑍_ gas relation noticeably. The dust abundance in the
model run is regulated by six parameters, which we term ‘dustrelated parameters’, including _𝑆𝑁_ red, _𝑘_ gg _,_ cloud, _𝑘_ frag, _𝑓_ dif, _𝑀_ destr
and _𝑘_ gg _,_ dif . In this study, we only tune the first four parameters as the
others marginally change the DGR– _𝑍_ gas relation (see Figure 6 in De
Vis et al. 2021), and at the same time disregarding two parameters
reduces the computational time significantly. Table 4 presents the
dust-related parameters and their prior range. We briefly present the
general form of dust mass evolution in Appendix B. Additionally, we
use the statistical frameworks outlined in De Vis et al. (2021) for a


MNRAS **000**, 1–19 (2024)



( _𝑀_ O − 0 _._ 238 × _𝑀_ dust )/16
12 + log(O/H) = 12 + log
� _𝑀_ gas /1 _._ 36



where _𝑀_ O is the total oxygen mass in the system, and 0.238 is to
subtract the oxygen content in the dust component. 16 is the atomic
weight of Oxygen, and 1.36 is to subtract the helium abundance of
the gas. The initial value of each parameter is chosen uniformly from
the prior range. We use 50 walkers and let them move 1000 steps.
We disregard the first 50 steps as burn-in walks. [21] Figure 8 shows
the probability maps of each combination of parameters after the
MCMC run. The median (50%), 84th percentile, and 16th percentile
are presented in Table 5.


_5.2.2_ _Interpretations and comparison with other studies_


In Figure 6, we show the `BEDE` results with a blue shaded region, run
with 16%-84% of each parameter. The non-dust-related parameters
are set the same as in Section 5.2.1. We provide the 4-th polynomial
fit to the best-fit models on the resolved DGR– _𝑍_ gas relation as below,
for a convenient comparison with Galliano et al. (2021) where the
same order of polynomial fit is suggested for the galaxy-integrated
properties of local galaxies.


log 10 DGR = 0 _._ 4426 Z [4] gas [−] [14] _[.]_ [7297 Z] [3] gas [+][ 183] _[.]_ [02 Z] [2] gas (14)
− 1004 _._ 77 Z gas + 2050 _._ 49


In `BEDE`, the relationship between DGR and metallicity is characterized by a metallicity threshold at around 12+log(O/H) of 7.7-8.2.
Above this threshold, dust formation and destruction processes reach
equilibrium so that a linear relation between DGR and metallicity is
expected.


  - Out of the four dust-related parameters, _𝑓_ dif is related to the
DMR of the system, indicating the available amount of metals to
build up dust (DMR; ≠ _𝑓_ dif ) [22], and it determines the DGR range
above the metallicity threshold. In our model run, we found that the


21 To ensure the step size is enough for the walkers to cover the entire prior
range, we estimate the integrated autocorrelation time and acceptance fraction
using the `emcee` packages. They are estimated as 14, and 0.445, respectively,
which means the model run provides a good fit.
22 DMR definition varies in different references. Our paper defines DMR as
_𝑀_ dust / _𝑀_ metals . The _𝑓_ dif corresponds to _𝑀_ dust /( _𝑀_ metals + _𝑀_ dust ).

model runs well converged to _𝑓_ dif = 0 _._ 32. This value is greater than
the _𝑓_ dif found in De Vis et al. (2021), where dust evolution modelling
is carried out on 340 late-type galaxies from the DustPedia, HIGH,
and HAPLESS surveys De Vis et al. (2021). They found _𝑓_ dif of 0.204,
agreeing with the observations (= 0 _._ 214) from the DustPedia galaxies
in De Vis et al. (2019). Our run of the dust evolution model suggests a
maximum DMR of 0.47, which agrees with the theoretical maximum
metal amounts locked in dust investigated by Palla et al. (2024) (see
Appendix A within). The _𝑓_ dif hardly affects DGR values below the
metallicity threshold, as at lower metallicity or early stage of galaxy
evolution, a negligible amount of metals in the ISM contributes to
dust mass.


Below the metallicity threshold in the models (i.e., 12+log(O/H)
≤ 7.7-8.2), the other three dust-related parameters, _𝑆𝑁_ red, _𝑘_ gg _,_ cloud,
and _𝑘_ affect the dust abundance as below:
frag


  - _𝑘_ gg _,_ cloud is the scaling factor that reduces the timescale of dust
grain growth in the dense ISM, implying that the higher _𝑘_ gg _,_ cloud the
faster the system reaches the metallicity threshold (Asano et al. 2013;
De Vis et al. 2017). The best fit for _𝑘_ gg _,_ cloud is 4131.81, consistent
with other studies with DustPedia galaxies in galaxy-integrated scale.
For instance, De Vis et al. (2021) found 3820 as the median with
large uncertainties (16/84th percentile of _>_ 1500), and Galliano et al.
(2021) showed that median _𝑘_ gg _,_ cloud of 4485 (16/84th percentile of
∼ 20) describes the observed quantities of galaxies the best. The
dust grain growth timescale spans 940 Myr in the low-metallicity
system (at 12+log(O/H) ∼ 7.08) and 10 Myr at 12+log(O/H)∼ 8.66,
indicating a faster grain growth at near solar metallicity.

  - _𝑘_ frag regulates the photofragmentation of large grains by UV
radiation, impacting dust destruction in the diffuse ISM in the system.
Higher values of _𝑘_ frag decrease the photofragmentation timescale
of large a-C:H/a-C [23] grains. Silicate grains are excluded from the
models due to their resistance to photofragmentation.The median
_𝑘_ frag (0.07) is found low from the parameter space, which agrees with
the model run for the galaxy-integrated scale (0.03 in De Vis et al.
2021). This low _𝑘_ frag implies that photo-fragmentation marginally
affects the dust grain destruction in the observed regions. It is also
observed that the distribution seems to have reached a lower bound

at 0. It will be outside the allowable range if it falls below this value.

  - _𝑆𝑁_ red is another dust-related parameter that scales down the
dust yield for SNe (see Todini & Ferrara 2001 or Table 5 in Galliano
et al. 2021). This parameter has a substantial impact on DGR values,
particularly in low-metallicity systems where stardust is the primary
dust production mechanism; higher _𝑆𝑁_ red leads to lower DGR values.
The lower bound of this parameter, where _𝑆𝑁_ red = 1 means 100%
of the produced dust from the SNe is preserved and contributes to
the dust abundance in the system. Our model runs find _𝑆𝑁_ red =
1 _._ 50 [+] − [0] 0 _[.]_ _._ [80] 40 [, corresponding to 43-91% of SN dust yield (or, 0.43-0.91]
_𝑀_ ⊙ /SN when the star mass is 25 _𝑀_ ⊙ following Todini & Ferrara
2001 dust yield table) is survived to build up the dust mass in the
low-metallicity regions. This contrasts with Galliano et al. (2021),
where a very low dust yield from SNe (∼ 0.025 _𝑀_ ⊙ /SN) is found.
However, our run has generally agreed with other studies such as in
De Vis et al. (2021) ( _𝑆𝑁_ red of 2.01), or Nanni et al. (2020) ( _>_ 25% of
dust condensation fraction from SNe). Also, De Looze et al. (2020)
has retrieved high SN dust yields, similar to Nanni et al. (2020).


23 Amorphous carbon with partial hydrogenation



_Resolved dust evolution in nearby galaxies_ 15


_5.2.3_ _Caveats on our dust evolution modelling_


This model comparison has caveats such as the dust evolution model
we utilized assumes one-zone chemical and dust evolution. Thus, it
may not be suitable for spatially resolved studies as the chemical/dust
evolution can differ depending on the regions as they have different
environments in terms of spiral/bar structure, or inflow/outflow regions.
Several degeneracies have been reported in De Vis et al. (2021),
such as the assumed IMF, recycling fraction, and SN yield tables.
Also, it is worthwhile to note that the DGR values in the lowmetallicity systems are regularised by _𝑘_ frag and _𝑆𝑁_ red at the same
time, which can lead to another degeneracy.
The combination of low _𝑘_ frag and _𝑆𝑁_ red can reproduce the DGR
range of Sextans A. However, we found the _𝑘_ frag reaches the lower
bound, implying other parameters should also be considered. For
example, in this model, the grain growth timescale in the dense
clouds in such a low-metallicity regime is too long to contribute
to dust abundance spontaneously. In reality, it could not always be
the case given that several studies suggest that high gas density can
trigger grain growth in the ISM in the early stage of galaxy evolution.
However, we are cautious given that only one galaxy (Sextans A)
in the low-metallicity system is probed in this study, the best-fit
parameter range found could be biased toward this galaxy.


**6** **SUMMARY**


In this study, we probed the DGR– _𝑍_ gas relationship with 11 nearby
galaxies from the TYPHOON survey in a spatially resolved manner at
(sub-)kpc scale. With the large FoV of TYPHOON data, we map the
gas-phase metallicity for ≳ 1 optical size of galaxies. We derived the
DGR from the spatial resolution-matched multi-wavelength datasets
(from far-UV to far-IR, CO and Hi radio). With these datasets, we
investigate the resolved DGR– _𝑍_ gas relationship. We summarise the
result as follows:


  - The global DGR– _𝑍_ gas relationship of TYPHOON galaxies follows well with the literature (e.g., De Vis et al. 2019; Galliano et al.
2021), except for the lowest metallicity galaxy, Sextans A.

  - The resolved DGR– _𝑍_ gas relationship is explored, focusing on
Scal metallicity calibration and _𝛼_ CO _,_ MW . The resolved relationship
shows a scattered distribution around each galaxy’s global measurement. The observed trend prefers the broken power law, agreeing with
the previously studied resolved DGR– _𝑍_ gas relation in other nearby
galaxies, for example, M 101 and NGC 628 (Vílchez et al. 2019).

  - The high DGR values (up to ∼ 2 dex than the literature) for the
resolved regions in Sextans A are observed, and the large span of
_𝑍_ gas (up to 1 dex). These values are comparable with the DGRs from
the depletion method for DLAs.


  We run the dust evolution modelling with the Bayesian MCMC
approach, `BEDE` (De Vis et al. 2021), varying the SN dust yield,
photofragmentation factor of dust grains, grain growth in the dense
clouds, and maximum dust-to-metal ratio in the diffuse ISM. We
then find the best parameter sets that describe the observed resolved
DGR– _𝑍_ gas relationship of TYPHOON galaxies.


  From the model fitting, we showed that high SN dust yield (43-91%) is preserved and an ineffective photofragmentation of dust
grains can explain the observed high DGR values of Sextans A.
We note that the two parameters controlling the two effects (SN
dust yield and photofragmentation) have reached the bound of each
prior range, indicating that other dust production parameters can be
considered. A previous study on the global DGR– _𝑍_ gas relation for


MNRAS **000**, 1–19 (2024)

16 _H.-J. Park et al._


two low-metallicity dwarf galaxies (Schneider et al. 2016) has shown
that the two galaxies with comparable metallicity but different gas
densities have large differences in DGR. Given this, it is possible that
the DGR values can be regulated not only by the metallicity but also
by the gas density of the systems.


  We found a large scatter for the parameter that controls the grain
growth timescale in dense clouds, which is consistent with the global
studies (e.g., De Vis et al. 2021). However, we also attribute it to the
lack of sample points in the metallicity range where the parameter
causes variance of DGR. Additionally, a high maximum dust-tometal ratio in diffuse ISM is found (DMR _<_ 0.47), which agrees with
the theoretical view.


A major limitation of this study is that only one very low metallicity
galaxy is available with the required data. An avenue to improve this
is to use the Hi-KIDS survey [24], which has conducted observations
of over 80 dwarf galaxies using the KOALA IFU instrument at the
Anglo-Australian Telescope (AAT), where all of these galaxies have
ancillary Hi data and 12 of them have _Herschel_ far-IR observations
with sufficient S/N for characterising both (atomic) gas and dust
mass. Furthermore, an extension program with AAT/KOALA (PID:
A/2024A/13; PI: Park) has observed 4 more dwarf galaxies with Hi
and _Herschel_ far-IR data. We plan to probe the resolved DGR– _𝑍_ gas in
these galaxies, for a more comprehensive study on the low-metallicity
regime in a future study.


**ACKNOWLEDGEMENTS**


The authors thank the anonymous referee who has provided constructive and helpful comments to improve our paper. H-JP thanks Bärbel
Koribalski for providing LVHIS ATCA Hi data cubes for NGC 625,
NGC 1512, NGC 1705, and NGC 5253. H-JP thanks Kelsey Johnson
and Molly Finn for providing the NGC 7793 ALMA data cube and
the moment 0 map. H-JP thanks WALLABY teams (P.I. Tobias Westmeier) for providing the NGC 1566 Hi data from the Early Science
data products.
LC acknowledges support from the Australian Research Council Discoverty Project funding scheme (DP210100337). KG is supported by the Australian Research Council through the Discovery
Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government. BFM
thanks The Observatories of the Carnegie Institution for Science
for believing in and supporting this decades-long programme at the
duPont telescope at Las Campanas, Chile.
Parts of this research were supported by the Australian Research
Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013.
Most of the photometric UV, optical, and IR data for individual
galaxies are retrieved from the NASA/IPAC Infrared Science
Archive (IRSA) and the NASA/IPAC Extragalactic Database (NED),
both of which are funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology.
The Australia Telescope Compact Array is part of the Australia Telescope National Facility ( `[https://ror.org/05qajvd42](https://ror.org/05qajvd42)` ) which is
funded by the Australian Government for operation as a National
Facility managed by CSIRO. This scientific work uses data obtained
from Inyarrimanha Ilgari Bundara / the Murchison Radio-astronomy
Observatory. We acknowledge the Wajarri Yamaji People as the
Traditional Owners and native title holders of the Observatory site.


24 `[https://hikids.datacentral.org.au/](https://hikids.datacentral.org.au/)`


MNRAS **000**, 1–19 (2024)



CSIRO’s ASKAP radio telescope is part of the Australia Telescope
National Facility ( `[https://ror.org/05qajvd42](https://ror.org/05qajvd42)` ). Operation of
ASKAP is funded by the Australian Government with support from
the National Collaborative Research Infrastructure Strategy. ASKAP
uses the resources of the Pawsey Supercomputing Research Centre.
The establishment of ASKAP, Inyarrimanha Ilgari Bundara, the
CSIRO Murchison Radio-astronomy Observatory and the Pawsey
Supercomputing Research Centre are initiatives of the Australian
Government, with support from the Government of Western Australia
and the Science and Industry Endowment Fund. This study makes use
of the following ALMA data: ADS/JAO.ALMA#2013.1.01161.S,
ADS/JAO.ALMA#2015.1.00121.S,
ADS/JAO.ALMA#2015.1.00782.S,
ADS/JAO.ALMA#2015.1.00925.S,
ADS/JAO.ALMA#2015.1.00956.S,
ADS/JAO.ALMA#2016.1.00386.S,
ADS/JAO.ALMA#2017.1.00392.S,
ADS/JAO.ALMA#2017.1.00886.L,
ADS/JAO.ALMA#2018.1.00219.S,
ADS/JAO.ALMA#2018.1.01651.S,
ADS/JAO.ALMA#2018.1.01783.S,
ADS/JAO.ALMA#2019.2.00110.S,
ADS/JAO.ALMA#2021.1.00330.S, ALMA is a partnership of
ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic
of Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ. The National Radio Astronomy Observatory
is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc. This work has
made use of data from the European Space Agency (ESA) mission
_Gaia_ ( `[https://www.cosmos.esa.int/gaia](https://www.cosmos.esa.int/gaia)` ), processed by the
_Gaia_ Data Processing and Analysis Consortium (DPAC, `[https:](https://www.cosmos.esa.int/web/gaia/dpac/consortium)`
`[//www.cosmos.esa.int/web/gaia/dpac/consortium](https://www.cosmos.esa.int/web/gaia/dpac/consortium)` ). Funding for the DPAC has been provided by national institutions, in
particular the institutions participating in the _Gaia_ Multilateral
Agreement.
This work made use of Astropy: [25] a community-developed core
Python package and an ecosystem of tools and resources for astronomy (Astropy Collaboration et al. 2013, 2018, 2022). This work
also used Numpy (Harris et al. 2020), Matplotlib (Hunter 2007), and
Scipy (Virtanen et al. 2020).
This research was conducted on Ngunnawal Indigenous land.


**DATA AVAILABILITY**


The TYPHOON optical IFS datacubes will be made publicly available in a forthcoming release by Seibert et al. (in prep.) through Data
Central [26] . The emission line data products can be made available
upon reasonable request by emailing A. Battisti.


**REFERENCES**


[Amorín R., Muñoz-Tuñón C., Aguerri J. A. L., Planesas P., 2016, A&A, 588,](http://dx.doi.org/10.1051/0004-6361/201526397)

[A23](https://ui.adsabs.harvard.edu/abs/2016A&A...588A..23A)

[Anand G. S., et al., 2021, MNRAS, 501, 3621](http://dx.doi.org/10.1093/mnras/staa3668)


25 http://www.astropy.org
26 `[https://datacentral.org.au/](https://datacentral.org.au/)`

Aniano G., Draine B. T., Gordon K. D., Sandstrom K., 2011, [PASP,](http://dx.doi.org/10.1086/662219) [123,](https://ui.adsabs.harvard.edu/abs/2011PASP..123.1218A)

[1218](https://ui.adsabs.harvard.edu/abs/2011PASP..123.1218A)

[Aniano G., et al., 2012, ApJ, 756, 138](http://dx.doi.org/10.1088/0004-637X/756/2/138)
[Aniano G., et al., 2020, ApJ, 889, 150](http://dx.doi.org/10.3847/1538-4357/ab5fdb)
[Asano R. S., Takeuchi T. T., Hirashita H., Inoue A. K., 2013, Earth, Planets](http://dx.doi.org/10.5047/eps.2012.04.014)
[and Space, 65, 213](http://dx.doi.org/10.5047/eps.2012.04.014)
[Asplund M., Grevesse N., Sauval A. J., Scott P., 2009, ARA&A, 47, 481](http://dx.doi.org/10.1146/annurev.astro.46.060407.145222)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
[Astropy Collaboration et al., 2022, ApJ, 935, 167](http://dx.doi.org/10.3847/1538-4357/ac7c74)
[Baldwin J. A., Phillips M. M., Terlevich R., 1981, PASP, 93, 5](http://dx.doi.org/10.1086/130766)
[Battisti A. J., et al., 2019, ApJ, 882, 61](http://dx.doi.org/10.3847/1538-4357/ab345d)
[Bendo G. J., et al., 2012, MNRAS, 419, 1833](http://dx.doi.org/10.1111/j.1365-2966.2011.19735.x)

Bertin E., Mellier Y., Radovich M., Missonnier G., Didelon P., Morin B.,
2002, in Bohlender D. A., Durand D., Handley T. H., eds, Astronomical
Society of the Pacific Conference Series Vol. 281, Astronomical Data
Analysis Software and Systems XI. p. 228
Bigiel F., Leroy A., Seibert M., Walter F., Blitz L., Thilker D., Madore B.,
[2010, ApJ, 720, L31](http://dx.doi.org/10.1088/2041-8205/720/1/L31)
[Bolatto A. D., Wolfire M., Leroy A. K., 2013, ARA&A, 51, 207](http://dx.doi.org/10.1146/annurev-astro-082812-140944)
Boyer M. L., Skillman E. D., van Loon J. T., Gehrz R. D., Woodward C. E.,
[2009, ApJ, 697, 1993](http://dx.doi.org/10.1088/0004-637X/697/2/1993)
[Brown M. J. I., et al., 2014, ApJS, 212, 18](http://dx.doi.org/10.1088/0067-0049/212/2/18)
[Bruzual G., Charlot S., 2003, MNRAS, 344, 1000](http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x)
[Camps P., Baes M., 2015, Astronomy and Computing, 9, 20](http://dx.doi.org/10.1016/j.ascom.2014.10.004)
[Camps P., Baes M., 2020, Astronomy and Computing, 31, 100381](http://dx.doi.org/10.1016/j.ascom.2020.100381)
[Casasola V., et al., 2020, A&A, 633, A100](http://dx.doi.org/10.1051/0004-6361/201936665)

[Casasola V., et al., 2022, A&A, 668, A130](http://dx.doi.org/10.1051/0004-6361/202245043)
[Casey C. M., Narayanan D., Cooray A., 2014, Phys. Rep., 541, 45](http://dx.doi.org/10.1016/j.physrep.2014.02.009)
[Chabrier G., 2003, PASP, 115, 763](http://dx.doi.org/10.1086/376392)
[Charlot S., Fall S. M., 2000, ApJ, 539, 718](http://dx.doi.org/10.1086/309250)
Chen Q.-H., Grasha K., Battisti A. J., Kewley L. J., Madore B. F., Seibert M.,
[Rich J. A., Beaton R. L., 2023, MNRAS, 519, 4801](http://dx.doi.org/10.1093/mnras/stac3790)
Chiang I.-D., Sandstrom K. M., Chastenet J., Johnson L. C., Leroy A. K.,
[Utomo D., 2018, ApJ, 865, 117](http://dx.doi.org/10.3847/1538-4357/aadc5f)
[Chiang I.-D., et al., 2023, MNRAS, 520, 5506](http://dx.doi.org/10.1093/mnras/stad373)
Chung A., van Gorkom J. H., Kenney J. D. P., Crowl H., Vollmer B., 2009,

[AJ, 138, 1741](http://dx.doi.org/10.1088/0004-6256/138/6/1741)
[Cigan P., et al., 2016, AJ, 151, 14](http://dx.doi.org/10.3847/0004-6256/151/1/14)
[Cigan P., et al., 2021, AJ, 162, 83](http://dx.doi.org/10.3847/1538-3881/abfd2e)
[Clark C. J. R., et al., 2018, A&A, 609, A37](http://dx.doi.org/10.1051/0004-6361/201731419)
[Cohen M., Wheaton W. A., Megeath S. T., 2003, AJ, 126, 1090](http://dx.doi.org/10.1086/376474)
[Conroy C., 2013, ARA&A, 51, 393](http://dx.doi.org/10.1146/annurev-astro-082812-141017)
[Cook D. O., et al., 2014, MNRAS, 445, 881](http://dx.doi.org/10.1093/mnras/stu1580)
Cutri R. M., et al., 2003, 2MASS All Sky Catalog of point sources.
Cutri R. M., et al., 2021, VizieR Online Data Catalog: AllWISE Data Release
(Cutri+ 2013), VizieR On-line Data Catalog: II/328. Originally published
in: IPAC/Caltech (2013)
[Dale D. A., et al., 2009, ApJ, 703, 517](http://dx.doi.org/10.1088/0004-637X/703/1/517)
[Davies J. I., et al., 2017, PASP, 129, 044102](http://dx.doi.org/10.1088/1538-3873/129/974/044102)
De Cia A., Ledoux C., Mattsson L., Petitjean P., Srianand R., Gavignaud I.,
[Jenkins E. B., 2016, A&A, 596, A97](http://dx.doi.org/10.1051/0004-6361/201527895)

[De Looze I., et al., 2020, MNRAS, 496, 3668](http://dx.doi.org/10.1093/mnras/staa1496)

[De Vis P., et al., 2017, MNRAS, 471, 1743](http://dx.doi.org/10.1093/mnras/stx981)

[De Vis P., et al., 2019, A&A, 623, A5](http://dx.doi.org/10.1051/0004-6361/201834444)

[De Vis P., Maddox S. J., Gomez H. L., Jones A. P., Dunne L., 2021, MNRAS,](http://dx.doi.org/10.1093/mnras/stab1604)


[505, 3228](https://ui.adsabs.harvard.edu/abs/2021MNRAS.505.3228D)

[Denicoló G., Terlevich R., Terlevich E., 2002, MNRAS, 330, 69](http://dx.doi.org/10.1046/j.1365-8711.2002.05041.x)

[Di Teodoro E. M., Fraternali F., 2015, MNRAS, 451, 3021](http://dx.doi.org/10.1093/mnras/stv1213)

[Doi M., et al., 2010, AJ, 139, 1628](http://dx.doi.org/10.1088/0004-6256/139/4/1628)
[Dopita M. A., Kewley L. J., Sutherland R. S., Nicholls D. C., 2016, Ap&SS,](http://dx.doi.org/10.1007/s10509-016-2657-8)

[361, 61](https://ui.adsabs.harvard.edu/abs/2016Ap&SS.361...61D)
Draine B. T., 2011, Physics of the Interstellar and Intergalactic Medium
[Elagali A., et al., 2019, MNRAS, 487, 2797](http://dx.doi.org/10.1093/mnras/stz1448)
[Feldmann R., 2015, MNRAS, 449, 3274](http://dx.doi.org/10.1093/mnras/stv552)
[Ferreras I., Silk J., 2000, ApJ, 532, 193](http://dx.doi.org/10.1086/308547)
[Finn M. K., et al., 2024, arXiv e-prints, p. arXiv:2401.01450](http://dx.doi.org/10.48550/arXiv.2401.01450)
[Fitzpatrick E. L., 1999, PASP, 111, 63](http://dx.doi.org/10.1086/316293)



_Resolved dust evolution in nearby galaxies_ 17


Fitzpatrick E. L., Massa D., Gordon K. D., Bohlin R., Clayton G. C., 2019,

[ApJ, 886, 108](http://dx.doi.org/10.3847/1538-4357/ab4c3a)
[Gaia Collaboration et al., 2016, A&A, 595, A1](http://dx.doi.org/10.1051/0004-6361/201629272)

[Gaia Collaboration et al., 2023, A&A, 674, A1](http://dx.doi.org/10.1051/0004-6361/202243940)

[Galametz M., et al., 2012, MNRAS, 425, 763](http://dx.doi.org/10.1111/j.1365-2966.2012.21667.x)

[Galliano F., et al., 2011, A&A, 536, A88](http://dx.doi.org/10.1051/0004-6361/201117952)

[Galliano F., Galametz M., Jones A. P., 2018, ARA&A, 56, 673](http://dx.doi.org/10.1146/annurev-astro-081817-051900)

[Galliano F., et al., 2021, A&A, 649, A18](http://dx.doi.org/10.1051/0004-6361/202039701)

Gerasimov I. S., Egorov O. V., Lozinskaya T. A., Moiseev A. V., Oparin D. V.,
[2022, MNRAS, 517, 4968](http://dx.doi.org/10.1093/mnras/stac3002)
[Gil de Paz A., et al., 2007, ApJS, 173, 185](http://dx.doi.org/10.1086/516636)
[Grasha K., et al., 2018, MNRAS, 481, 1016](http://dx.doi.org/10.1093/mnras/sty2154)

[Grasha K., et al., 2022, ApJ, 929, 118](http://dx.doi.org/10.3847/1538-4357/ac5ab2)
Gratier P., Braine J., Rodriguez-Fernandez N. J., Israel F. P., Schuster K. F.,
[Brouillet N., Gardan E., 2010, A&A, 512, A68](http://dx.doi.org/10.1051/0004-6361/200911722)

[Griffin M. J., et al., 2010, A&A, 518, L3](http://dx.doi.org/10.1051/0004-6361/201014519)

[Groves B., et al., 2023, MNRAS, 520, 4902](http://dx.doi.org/10.1093/mnras/stad114)

[Hamanowicz A., et al., 2024, arXiv e-prints, p. arXiv:2402.18733](http://dx.doi.org/10.48550/arXiv.2402.18733)
[Harris C. R., et al., 2020, Nature, 585, 357](http://dx.doi.org/10.1038/s41586-020-2649-2)

Hirschauer A. S., Gray L., Meixner M., Jones O. C., Srinivasan S., Boyer
[M. L., Sargent B. A., 2020, ApJ, 892, 91](http://dx.doi.org/10.3847/1538-4357/ab7b60)
[Ho I. T., et al., 2016, Ap&SS, 361, 280](http://dx.doi.org/10.1007/s10509-016-2865-2)
[Hollenbach D., Salpeter E. E., 1971, ApJ, 163, 155](http://dx.doi.org/10.1086/150754)
[Hollenbach D. J., Tielens A. G. G. M., 1997, ARA&A, 35, 179](http://dx.doi.org/10.1146/annurev.astro.35.1.179)
[Hunt L. K., et al., 2023, arXiv e-prints, p. arXiv:2305.03443](http://dx.doi.org/10.48550/arXiv.2305.03443)
[Hunter D., 1997, PASP, 109, 937](http://dx.doi.org/10.1086/133965)

[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
[Hunter D. A., Elmegreen B. G., Ludka B. C., 2010, AJ, 139, 447](http://dx.doi.org/10.1088/0004-6256/139/2/447)
[Hunter D. A., et al., 2012, AJ, 144, 134](http://dx.doi.org/10.1088/0004-6256/144/5/134)

[Inoue A. K., 2011, Earth, Planets and Space, 63, 1027](http://dx.doi.org/10.5047/eps.2011.02.013)
[Issa M. R., MacLaren I., Wolfendale A. W., 1990, A&A, 236, 237](https://ui.adsabs.harvard.edu/abs/1990A&A...236..237I)

Jarrett T. H., Chester T., Cutri R., Schneider S. E., Huchra J. P., 2003, [AJ,](http://dx.doi.org/10.1086/345794)


[125, 525](https://ui.adsabs.harvard.edu/abs/2003AJ....125..525J)

Jones A. P., Fanciullo L., Köhler M., Verstraete L., Guillet V., Bocchio M.,

[Ysard N., 2013, A&A, 558, A62](http://dx.doi.org/10.1051/0004-6361/201321686)

Jones A. P., Köhler M., Ysard N., Bocchio M., Verstraete L., 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201630225)


[602, A46](https://ui.adsabs.harvard.edu/abs/2017A&A...602A..46J)

Karakas A. I., Lugaro M., Carlos M., Cseh B., Kamath D., García-Hernández
[D. A., 2018, MNRAS, 477, 421](http://dx.doi.org/10.1093/mnras/sty625)

[Kauffmann G., et al., 2003, MNRAS, 346, 1055](http://dx.doi.org/10.1111/j.1365-2966.2003.07154.x)

[Kennicutt Robert C. J., et al., 2003, PASP, 115, 928](http://dx.doi.org/10.1086/376941)

[Kennicutt R. C., et al., 2011, PASP, 123, 1347](http://dx.doi.org/10.1086/663818)
[Kewley L. J., Dopita M. A., 2002, ApJS, 142, 35](http://dx.doi.org/10.1086/341326)
[Kewley L. J., Ellison S. L., 2008, ApJ, 681, 1183](http://dx.doi.org/10.1086/587500)
Kewley L. J., Dopita M. A., Sutherland R. S., Heisler C. A., Trevena J., 2001,

[ApJ, 556, 121](http://dx.doi.org/10.1086/321545)
[Kewley L. J., Nicholls D. C., Sutherland R. S., 2019, ARA&A, 57, 511](http://dx.doi.org/10.1146/annurev-astro-081817-051832)
[Köhler M., Ysard N., Jones A. P., 2015, A&A, 579, A15](http://dx.doi.org/10.1051/0004-6361/201525646)
[Koribalski B. S., López-Sánchez Á. R., 2009, MNRAS, 400, 1749](http://dx.doi.org/10.1111/j.1365-2966.2009.15610.x)
[Koribalski B. S., et al., 2018, MNRAS, 478, 1611](http://dx.doi.org/10.1093/mnras/sty479)
[Koribalski B. S., et al., 2020, Ap&SS, 365, 118](http://dx.doi.org/10.1007/s10509-020-03831-4)
[Kourkchi E., Tully R. B., 2017, ApJ, 843, 16](http://dx.doi.org/10.3847/1538-4357/aa76db)
[Kreckel K., et al., 2019, ApJ, 887, 80](http://dx.doi.org/10.3847/1538-4357/ab5115)
[Kuchinski L. E., et al., 2000, ApJS, 131, 441](http://dx.doi.org/10.1086/317371)
[Lang P., et al., 2020, ApJ, 897, 122](http://dx.doi.org/10.3847/1538-4357/ab9953)
[Lelli F., Verheĳen M., Fraternali F., 2014, MNRAS, 445, 1694](http://dx.doi.org/10.1093/mnras/stu1804)
Leroy A. K., Walter F., Brinks E., Bigiel F., de Blok W. J. G., Madore B.,
[Thornley M. D., 2008, AJ, 136, 2782](http://dx.doi.org/10.1088/0004-6256/136/6/2782)
[Leroy A. K., et al., 2019, ApJS, 244, 24](http://dx.doi.org/10.3847/1538-4365/ab3925)
[Leroy A. K., et al., 2021a, ApJS, 255, 19](http://dx.doi.org/10.3847/1538-4365/abec80)
[Leroy A. K., et al., 2021b, ApJS, 257, 43](http://dx.doi.org/10.3847/1538-4365/ac17f3)
[Li F., Wang J., Xu F., Kong X., Chen X., Lin Z., Wang S., 2023, ApJ, 950, 84](http://dx.doi.org/10.3847/1538-4357/accbc0)
[Limongi M., Chieffi A., 2018, ApJS, 237, 13](http://dx.doi.org/10.3847/1538-4365/aacb24)
[Liu D., et al., 2019, ApJ, 887, 235](http://dx.doi.org/10.3847/1538-4357/ab578d)
Madden S. C., Rémy A., Galliano F., Galametz M., Bendo G., Cormier
D., Lebouteiller V., Hony S., 2012, in Tuffs R. J., Popescu C. C.,
eds, IAU Symposium Vol. 284, The Spectral Energy Distribu

MNRAS **000**, 1–19 (2024)

18 _H.-J. Park et al._


tion of Galaxies   - SED 2011. pp 141–148 ( `[arXiv:1205.1332](http://arxiv.org/abs/1205.1332)` ),
[doi:10.1017/S1743921312008939](http://dx.doi.org/10.1017/S1743921312008939)

[Madden S. C., et al., 2013, PASP, 125, 600](http://dx.doi.org/10.1086/67113810.48550/arXiv.1305.2628)

[Mateo M. L., 1998, ARA&A, 36, 435](http://dx.doi.org/10.1146/annurev.astro.36.1.435)

[Morrissey P., et al., 2007, ApJS, 173, 682](http://dx.doi.org/10.1086/520512)
Moustakas J., Kennicutt Robert C. J., Tremonti C. A., Dale D. A., Smith
[J.-D. T., Calzetti D., 2010, ApJS, 190, 233](http://dx.doi.org/10.1088/0067-0049/190/2/233)
[Muñoz-Mateos J. C., et al., 2009, ApJ, 701, 1965](http://dx.doi.org/10.1088/0004-637X/701/2/1965)
[Namumba B., Carignan C., Passmoor S., de Blok W. J. G., 2017, MNRAS,](http://dx.doi.org/10.1093/mnras/stx2256)

[472, 3761](https://ui.adsabs.harvard.edu/abs/2017MNRAS.472.3761N)

[Nanni A., Burgarella D., Theulé P., Côté B., Hirashita H., 2020, A&A, 641,](http://dx.doi.org/10.1051/0004-6361/202037833)
[A168](https://ui.adsabs.harvard.edu/abs/2020A&A...641A.168N)

Osterbrock D. E., 1989, Astrophysics of gaseous nebulae and active galactic

nuclei

Pagel B. E. J., Edmunds M. G., Blackwell D. E., Chun M. S., Smith G., 1979,

[MNRAS, 189, 95](http://dx.doi.org/10.1093/mnras/189.1.95)

[Palla M., et al., 2024, MNRAS, 528, 2407](http://dx.doi.org/10.1093/mnras/stae160)

Park H.-J., Oh S.-H., Wang J., Zheng Y., Zhang H.-X., De Blok W. J. G.,
[2022, AJ, 164, 82](http://dx.doi.org/10.3847/1538-3881/ac7c1b)

[Péroux C., Howk J. C., 2020, ARA&A, 58, 363](http://dx.doi.org/10.1146/annurev-astro-021820-120014)
[Pettini M., Pagel B. E. J., 2004, MNRAS, 348, L59](http://dx.doi.org/10.1111/j.1365-2966.2004.07591.x)
[Pilyugin L. S., Grebel E. K., 2016, MNRAS, 457, 3678](http://dx.doi.org/10.1093/mnras/stw238)
[Pilyugin L. S., Thuan T. X., 2005, ApJ, 631, 231](http://dx.doi.org/10.1086/432408)
Poetrodjojo H., D’Agostino J. J., Groves B., Kewley L., Ho I. T., Rich J.,
[Madore B. F., Seibert M., 2019, MNRAS, 487, 79](http://dx.doi.org/10.1093/mnras/stz1241)

[Relaño M., et al., 2018, A&A, 613, A43](http://dx.doi.org/10.1051/0004-6361/201732347)
[Rémy-Ruyer A., et al., 2014, A&A, 563, A31](http://dx.doi.org/10.1051/0004-6361/201322803)
[Roberts M. S., 1962, AJ, 67, 437](http://dx.doi.org/10.1086/108752)

[Roman-Duval J., et al., 2014, ApJ, 797, 86](http://dx.doi.org/10.1088/0004-637X/797/2/86)
[Roman-Duval J., et al., 2022a, ApJ, 928, 90](http://dx.doi.org/10.3847/1538-4357/ac5248)
[Roman-Duval J., et al., 2022b, ApJ, 935, 105](http://dx.doi.org/10.3847/1538-4357/ac7713)
Rowlands K., Gomez H. L., Dunne L., Aragón-Salamanca A., Dye S., Maddox
[S., da Cunha E., van der Werf P., 2014, MNRAS, 441, 1040](http://dx.doi.org/10.1093/mnras/stu605)
[Sandstrom K. M., et al., 2013, ApJ, 777, 5](http://dx.doi.org/10.1088/0004-637X/777/1/5)
[Schaller G., Schaerer D., Meynet G., Maeder A., 1992, A&AS, 96, 269](https://ui.adsabs.harvard.edu/abs/1992A&AS...96..269S)
[Schlafly E. F., Finkbeiner D. P., 2011, ApJ, 737, 103](http://dx.doi.org/10.1088/0004-637X/737/2/103)
[Schneider R., Hunt L., Valiante R., 2016, MNRAS, 457, 1842](http://dx.doi.org/10.1093/mnras/stw114)

[Scoville N., et al., 2014, ApJ, 783, 84](http://dx.doi.org/10.1088/0004-637X/783/2/8410.48550/arXiv.1401.2987)
[Scoville N., et al., 2016, ApJ, 820, 83](http://dx.doi.org/10.3847/0004-637X/820/2/83)
[Sheth K., et al., 2010, PASP, 122, 1397](http://dx.doi.org/10.1086/657638)
[Smith D. J. B., Hayward C. C., 2018, MNRAS, 476, 1705](http://dx.doi.org/10.1093/mnras/sty311)
[Storchi-Bergmann T., Calzetti D., Kinney A. L., 1994, ApJ, 429, 572](http://dx.doi.org/10.1086/174345)
[Storey P. J., Zeippen C. J., 2000, MNRAS, 312, 813](http://dx.doi.org/10.1046/j.1365-8711.2000.03184.x)
[Strong A. W., Mattox J. R., 1996, A&A, 308, L21](https://ui.adsabs.harvard.edu/abs/1996A&A...308L..21S)
[Tacconi L. J., et al., 2018, ApJ, 853, 179](http://dx.doi.org/10.3847/1538-4357/aaa4b4)
[Todini P., Ferrara A., 2001, MNRAS, 325, 726](http://dx.doi.org/10.1046/j.1365-8711.2001.04486.x)

Tully R. B., Rizzi L., Shaya E. J., Courtois H. M., Makarov D. I., Jacobs
[B. A., 2009, AJ, 138, 323](http://dx.doi.org/10.1088/0004-6256/138/2/323)

[Tully R. B., et al., 2013, AJ, 146, 86](http://dx.doi.org/10.1088/0004-6256/146/4/86)
[Tully R. B., Courtois H. M., Sorce J. G., 2016, AJ, 152, 50](http://dx.doi.org/10.3847/0004-6256/152/2/50)
[Verheĳen M. A. W., Sancisi R., 2001, A&A, 370, 765](http://dx.doi.org/10.1051/0004-6361:20010090)
[Verstocken S., et al., 2020, A&A, 637, A24](http://dx.doi.org/10.1051/0004-6361/201935770)

Vílchez J. M., Relaño M., Kennicutt R., De Looze I., Mollá M., Galametz

[M., 2019, MNRAS, 483, 4968](http://dx.doi.org/10.1093/mnras/sty3455)

[Virtanen P., et al., 2020, Nature Methods, 17, 261](http://dx.doi.org/10.1038/s41592-019-0686-2)

Walter F., Brinks E., de Blok W. J. G., Bigiel F., Kennicutt Robert C. J.,
[Thornley M. D., Leroy A., 2008, AJ, 136, 2563](http://dx.doi.org/10.1088/0004-6256/136/6/2563)
[Wang J., et al., 2013, MNRAS, 433, 270](http://dx.doi.org/10.1093/mnras/stt722)
[Wang J., et al., 2014, MNRAS, 441, 2159](http://dx.doi.org/10.1093/mnras/stu649)
Wang J., Catinella B., Saintonge A., Pan Z., Serra P., Shao L., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab68dd)

[890, 63](https://ui.adsabs.harvard.edu/abs/2020ApJ...890...63W)

Yates R. M., Henriques B. M. B., Fu J., Kauffmann G., Thomas P. A., Guo
[Q., White S. D. M., Schady P., 2021, MNRAS, 503, 4474](http://dx.doi.org/10.1093/mnras/stab741)
[Zhukovska S., 2014, A&A, 562, A76](http://dx.doi.org/10.1051/0004-6361/201322989)

[da Cunha E., Charlot S., Elbaz D., 2008, MNRAS, 388, 1595](http://dx.doi.org/10.1111/j.1365-2966.2008.13535.x)
[de Blok W. J. G., Walter F., 2000, ApJ, 537, L95](http://dx.doi.org/10.1086/312777)
[de Blok W. J. G., Walter F., 2006, AJ, 131, 343](http://dx.doi.org/10.1086/497829)


MNRAS **000**, 1–19 (2024)



de Vaucouleurs G., de Vaucouleurs A., Corwin Herold G. J., Buta R. J., Paturel
G., Fouque P., 1991, Third Reference Catalogue of Bright Galaxies
[den Brok J. S., et al., 2021, MNRAS, 504, 3221](http://dx.doi.org/10.1093/mnras/stab859)


**APPENDIX A:** **THE DGR–** _𝑍_ gas **RELATIONSHIP WITH**
**DIFFERENT METALLICITY CALIBRATIONS**


We show the resolved DGR– _𝑍_ gas relationship using different gasphase metallicity diagnostics, N2S2H _𝛼_, O3N2, and R 23 (Figure A1).
We argue that the user should be aware that each calibration shows a
different DGR– _𝑍_ gas relation, especially at a low-metallicity system.
Note that the DGR measurements include molecular gas estimation
using _𝛼_ CO _,_ MW .
_N2S2H𝛼_ : The N2S2 _𝛼_ calibration (Dopita et al. 2016)
uses combination of emission lines in the form of

[N II] _𝜆_ 6583/[S II] _𝜆𝜆_ 6717,6731 and [N II] _𝜆_ 6583/H _𝛼_ . This
calibration is one of the most popular diagnostics since the lines
are close enough, allowing us to ignore the dust extinction effect.
Additionally, the N2S2H _𝛼_ method is insensitive to the ionization
parameter and the ISM pressure (P) within the range of 4 _<_ log(P/k)
_<_ 7. Moreover, Yates et al. (2021) presented that the gas-phase
metallicity for low-mass galaxies obtained by the N2S2H _𝛼_ calibration is in good agreement with the direct _𝑇_ e method. At the same
time, the diagnostic derives super-solar gas-phase metallicity for
very massive sources.
_O3N2_ : The gas-phase metallicity from O3N2 (Pettini & Pagel
2004) has a very small systematic discrepancy from other calibrations (Kewley & Ellison 2008. It uses the line combinations of
([O III] _𝜆_ 5007/H _𝛽_ )/([N II] _𝜆_ 6584/H _𝛼_ ).
_R_ 23 : The R 23 -based metallicity diagnostics ( _𝑅_ 23 =
([O II] _𝜆𝜆_ 3727,3729 + [O III] _𝜆𝜆_ 4959,5007)/H _𝛽_ ) are one of
the commonly used calibrations due to its insensitivity with
ionisation parameter. We use the calibration investigated by
Pilyugin & Thuan (2005). However, the independence only holds at
12+log(O/H) _>_ 8.5 (Kewley et al. 2019).


**APPENDIX B:** **DESCRIPTION ON THE DUST EVOLUTION**

**MODEL (** `BEDE` **)**


This section specifies how the selected variables (dust-related parameters) contribute to the dust mass build-up/destruction over time.
The generic equation for the dust mass evolution in this model is
as follows (Equation 10 in De Vis et al. 2021):



dust _𝑚_ _𝑈_

=
_𝑑𝑡_ ∫ _𝑚_



_𝑑𝑀_ dust



([ _𝑚_ − _𝑚_ _𝑅_ ( _𝑚_ ) ] _𝑍_ ( _𝑡_ − _𝜏_ m ) + _𝑚𝑝_ Z )
_𝑚_ _𝑡_



× _𝐶_ dust ( _𝑚_ ) × _𝜓_ ( _𝑡_ − _𝜏_ m ) _𝜙_ ( _𝑚_ ) _𝑑𝑚_


+ _𝐷𝐺𝑅_ _𝐼_ _𝐼_ ( _𝑡_ ) − _𝐷𝐺𝑅_ ( _𝑡_ )( _𝑂_ ( _𝑡_ ) + _𝜓_ ( _𝑡_ )) + _𝑅_ _𝑀_ dust ( _𝑡_ )

+ _𝑓_ c _𝑓_ dis _𝑀_ dust _𝜏_ gg [−][1] _,_ cloud [+ (][1][ −] _[𝑓]_ [c] [)] _[𝑀]_ [dust] _[𝜏]_ gg [−][1] _,_ dif

−(1 − _𝑓_ c ) _𝑀_ dust _𝜏_ dest [−][1]
−(1 − _𝑓_ c )(1 − _𝑓_ Si ) _𝑀_ dust _𝜏_ frag [−][1] _[.]_

(B1)


The integral form presents the _𝑀_ dust expelled by stars and SNe,
which ranges from _𝑀_ _𝑡_, the lowest mass at a star’s end of life at time
_𝑡_, to _𝑀_ _𝑈_, the upper mass limit of the star (= 120 _𝑀_ ⊙ ). Specifically,
_𝑚_ _𝑅_ ( _𝑚_ ) is the remnant mass of a star (Ferreras & Silk 2000), and
_𝜏_ m is the lifetime of stars with initial mass _𝑚_, which is derived from
Schaller et al. (1992). _𝑍_ in this question means the metal mass fraction

_Resolved dust evolution in nearby galaxies_ 19



1.5


2.0


2.5


3.0


3.5


4.0


4.5



1.5


2.0


2.5


3.0


3.5


4.0


4.5



1.5


2.0


2.5


3.0


3.5


4.0


4.5



Z/Z 10 1 (metallicity) 10 0


DGR - Z gas (Scal)


Pearson R = 0.69



Z/Z 10 1 (metallicity) 10 0


DGR - Z gas (Scal)


Pearson R = 0.66



Z/Z 10 1 (metallicity) 10 0


DGR - Z gas (Scal)


Pearson R = 0.61



5.0

7.0 7.5 8.0 8.5 9.0
12+log(O/H) (N2S2H )



5.0

7.0 7.5 8.0 8.5 9.0
12+log(O/H) (O3N2)



5.0

7.0 7.5 8.0 8.5 9.0
12+log(O/H) (R 23 )



**Figure A1.** The resolved DGR– _𝑍_ gas relationship with different metallicity diagnostics (N2S2H _𝛼_ ; Dopita et al. 2016, O3N2; Pettini & Pagel 2004; R 23 or PT05;
Pilyugin & Thuan 2005). The molecular gas mass has been measured in an assumption of _𝛼_ CO _,_ MW for the resolved DGR values. The background grey dots
present the relationship with Scal adopted in this study for reference.



over gas mass. The _𝑚𝑝_ Z presents the metal yield from SN or AGB.
The second term ( _𝐶_ dust ( _𝑚_ )) indicates the condensation efficiency of
_𝑀_ dust, from low-to-intermediate mass stars ( _𝑚<_ 8 _𝑀_ ⊙ ; set to 0.15
following the experiment in De Vis et al. (2021) where it is shown
that its change has a negligible effect on the model) and SNe. For
_𝑚>_ 8 _𝑀_ ⊙, the SN dust yield table (Todini & Ferrara 2001; Rowlands
et al. 2014) is used and the _𝑆𝑁_ red factors it as


_𝐶_ dust ( _𝑚>_ 8 _𝑀_ ⊙ ) = 1/ _𝑆𝑁_ red × _𝐶_ dust _,_ SN [ _𝑀_ ⊙ / _𝑆𝑁_ ] _._ (B2)


_𝜓_ is the star formation rate, and the _𝜏_ m represents the lifetime of
stars with initial mass _𝑚_ . The third term reflects the inflow, outflow
and recycled dust components from the outflow. _𝐷𝐺𝑅_ _𝐼_ stands for
the DGR of the inflows, and we set it to zero. _𝐷𝐺𝑅_ _𝑂_ is the DGR
value of the outflows at the time _𝑡_ . We take only into account the lowvelocity ( _𝑉_ out < 150 km s [−][1] ) outflow components for the recycled
_𝑀_ dust, _𝑅_ _𝑀_ dust .
The fourth row of Equation B1 brings the grain growth from dense
clouds and diffuse clouds individually. The _𝑓_ c is the mass fraction of
cold dense clouds out of total ISM mas, and _𝑓_ dis is the factor of dust
from grain growths surviving from gas cloud dissociation. The grain
growth timescale of each dense/diffuse cloud is described below. De
Vis et al. (2021)):



**APPENDIX C:** **MULTI-WAVELENGTH PHOTOMETRIC**

**DATA**


**APPENDIX D:** **RADIAL PROFILE OF ISM SURFACE**

**DENSITY, DGR, AND 12+log(O/H) AND QUANTITY MAPS**


We construct a radius map of each galaxy using the following equation:



_𝑅_ ( _𝑥, 𝑦_ ) = √︁


where



c _𝑜𝑠_ [2] _𝜃_ + s _𝑖𝑛_ [2] _𝜃,_



_,_ (B3)
�



_𝜏_ gg _,_ dif = _𝑘_ gg _,_ dif _𝑍_ 0



_𝑀_ dust
�1 − _𝑀_ metals × _𝑓_ dif



_,_ (B4)
�



cos _𝜃_ = −( _𝑥_ − _𝑥_ _𝑐_ ) × s _𝑖𝑛_ ( _𝑃𝐴_ ) + ( _𝑦_ − _𝑦_ _𝑐_ ) × c _𝑜𝑠_ ( _𝑃𝐴_ ) _,_


and


sin _𝜃_ = (−( _𝑥_ − _𝑥_ _𝑐_ ) × c _𝑜𝑠_ ( _𝑃𝐴_ ) + ( _𝑦_ − _𝑦_ _𝑐_ ) × s _𝑖𝑛_ ( _𝑃𝐴_ )/c _𝑜𝑠_ ( _𝑖_ ) _,_

(D1)


where _𝑅_ represents the radius, _𝑥_ and _𝑦_ are the pixel coordinates,
_𝑥_ _𝑐_ and _𝑦_ _𝑐_ are the centre of the galaxy in pixel locations, _𝑃𝐴_ is
the position angle, and _𝑖_ is the inclination of the galaxy, as listed
in Table 1. The inclination effect has been corrected for the ISM

surface density maps and radial profiles of each galaxy using the
information in Table 1. The radius is normalized by _𝑟_ 25 and binned
into several bins with a step size of 0.2 _𝑟_ 25 and the radial profile of
each parameter is shown by choosing the median value of physical
parameters within the defined radius range with dashed lines. The
error bars of the radial profile are from the standard deviation of the
quantity at each radius bin. We note that the Hi mass and H 2 gas mass
have been corrected for the helium abundance. The H 2 gas surface
density is derived using the constant _𝛼_ CO _,_ MW as is DGR. Figure D1
provides the radial profiles of each ISM component as an example.
Other galaxies are available in the online version of this article.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–19 (2024)



_𝑆𝐹𝑅_
_𝜏_ gg _,_ cloud = _𝑘_ gg _,_ cloud _𝑍_ 0 _𝑀_ _𝑔𝑎𝑠_



_𝑀_ dust
�1 − _𝑀_ metals × _𝑓_ cloud



where _𝑘_ gg _,_ cloud and _𝑘_ dif controls the grain growth timescale in the
dense and diffuse clouds, respectively. The _𝑍_ 0 is the normalised
metallicity by MW metallicity. In our model run, we fix the _𝑘_ gg _,_ dif
to 5, and the _𝑘_ gg _,_ cloud is allowed to vary.
The dust destruction term by SN shocks can be described below:


_𝜏_ destr [−][1] [=][ 135] _[𝑀]_ gas [−][1] _[𝑅]_ SN _[𝑀]_ destr _[,]_ (B5)


where _𝑅_ SN is the SN rate, and we set the _𝑀_ destr to 15 _𝑀_ ⊙ per
SN in our model run. _𝑘_ frag, which regulates the timescale of the
photofragmentation of a-C:H/a-C grains by UV radiation and given

as:


_𝜏_ frag [−][1] [=] _[𝑘]_ [frag] _[𝑆𝑆𝐹𝑅,]_ (B6)


where SSFR represents the diffuse UV radiation field.

20 _H.-J. Park et al._





2


1


0


1


2


3







0.0 0.2 0.4 0.6 0.8 1.0

R/r 25



2.5


2.0


1.5


1.0


0.5



1.2


1.0


0.8


0.6


0.4


0.2



2.3


2.4


2.5


2.6


2.7



**0.0** **0.2** **0.4** **0.6** **0.8** **1.0**


R/r 25


8.6


1.5


8.5


2.0


8.4


2.5


8.3


3.0



1.25


1.00


0.75


0.50


0.25


0.00


0.25



**Figure D1.** Radial profile of ISM surface density (Σ ISM ), DGR, and Z _𝑔𝑎𝑠_ of NGC 1512 (upper panels). Upper left panel: Radial profiles of Σ _★_ (green), Σ H 2
(blue), Σ HI (red), Σ dust (orange) in log scale Upper right panel: Radial profiles of 12+log(O/H) (Scal; olive) and DGR (brown) in log scale. For the radius bin
with no more than one pixel, we show the profile with dots and connect them using dashed lines. Lower panels: The quantity maps of each parameter with the
r 25 presented with a black solid line. The radial profiles and the quantity maps for other galaxies are available in the online version of the article.


MNRAS **000**, 1–19 (2024)

Instrument Band _𝜆_ eff Pixel width (optical)
/ Resolution FWHM


GALEX FUV 152.8 nm 4.3 [′′]
GALEX NUV 256.6 nm 5.2 [′′]
CTIO 0.9m/1.0m/1.5m U 365.0 nm 0.4 [′′] /0.3 [′′] /0.2 [′′]
CTIO 0.9m/1.0m/1.5m B 445.0 nm 0.4 [′′] /0.3 [′′] /0.2 [′′]
CTIO 0.9m/1.0m/1.5m V 464.9 nm 0.4 [′′] /0.3 [′′] /0.2 [′′]
CTIO 0.9m/1.0m/1.5m R 551.0 nm 0.4 [′′] /0.3 [′′] /0.2 [′′]
CTIO 0.9m/1.0m/1.5m I 658.0 nm 0.4 [′′] /0.3 [′′] /0.2 [′′]
KPNO 0.9m U 364.5 nm 0.43 [′′]
KPNO 0.9m B 431.2 nm 0.43 [′′]
KPNO 0.9m V 543.3 nm 0.43 [′′]
KPNO 0.9m R 645.8 nm 0.43 [′′]
KPNO 0.9m I 833.3 nm 0.43 [′′]
SDSS u 353.1 nm 1.3 [′′]
SDSS g 462.7 nm 1.3 [′′]
SDSS r 614.0 nm 1.3 [′′]
SDSS i 746.7 nm 1.3 [′′]
SDSS z 888.7 nm 1.3 [′′]
2MASS J 1.24 _𝜇_ m 2.0 [′′]
2MASS H 1.66 _𝜇_ m 2.0 [′′]
2MASS K s 2.16 _𝜇_ m 2.0 [′′]
WISE W1 3.4 _𝜇_ m 6.1 [′′]
IRAC I1 3.6 _𝜇_ m 1.66 [′′]
IRAC I2 4.5 _𝜇_ m 1.72 [′′]
WISE W2 4.6 _𝜇_ m 6.4 [′′]
IRAC I3 5.8 _𝜇_ m 1.88 [′′]
IRAC I4 8.0 _𝜇_ m 1.98 [′′]
WISE W3 12 _𝜇_ m 6.5 [′′]
WISE W4 22 _𝜇_ m 6.5 [′′]
MIPS M1 24 _𝜇_ m 6 [′′]
PACS Blue 70 _𝜇_ m 9 [′′]
PACS Green 100 _𝜇_ m 10 [′′]
PACS Red 160 _𝜇_ m 13 [′′]
SPIRE PSW 250 _𝜇_ m 18 [′′]
SPIRE PMW 350 _𝜇_ m 25 [′′]


**Table** **C1.** Main characteristics of multi-wavelength data used
for this study. GALEX: Morrissey et al. (2007); CTIO: `[https:](https://noirlab.edu/science/programs/ctio)`
`[//noirlab.edu/science/programs/ctio](https://noirlab.edu/science/programs/ctio)` ; KPNO: `[https://noirlab.](https://noirlab.edu/science/index.php/programs/kpno/filters/wiyn-09)`
`[edu/science/index.php/programs/kpno/filters/wiyn-09](https://noirlab.edu/science/index.php/programs/kpno/filters/wiyn-09)` ;
SDSS: Doi et al. (2010); 2MASS: Cohen et al. (2003); WISE:
`[https://wise2.ipac.caltech.edu/docs/release/allsky/expsup](https://wise2.ipac.caltech.edu/docs/release/allsky/expsup)` ;
IRAC: `[https://irsa.ipac.caltech.edu/data/SPITZER/docs/](https://irsa.ipac.caltech.edu/data/SPITZER/docs/irac/iracinstrumenthandbook/IRAC_Instrument_Handbook.pdf)`
`[irac/iracinstrumenthandbook/IRAC_Instrument_Handbook.pdf](https://irsa.ipac.caltech.edu/data/SPITZER/docs/irac/iracinstrumenthandbook/IRAC_Instrument_Handbook.pdf)` ;
MIPS: `[https://irsa.ipac.caltech.edu/data/SPITZER/docs/](https://irsa.ipac.caltech.edu/data/SPITZER/docs/mips/mipsinstrumenthandbook/MIPS_Instrument_Handbook.pdf)`
`[mips/mipsinstrumenthandbook/MIPS_Instrument_Handbook.pdf](https://irsa.ipac.caltech.edu/data/SPITZER/docs/mips/mipsinstrumenthandbook/MIPS_Instrument_Handbook.pdf)` ;
PACS: `[https://www.cosmos.esa.int/documents/12133/996891/](https://www.cosmos.esa.int/documents/12133/996891/PACS+Explanatory+Supplement/)`
`[PACS+Explanatory+Supplement/](https://www.cosmos.esa.int/documents/12133/996891/PACS+Explanatory+Supplement/)` SPIRE: Griffin et al. (2010)



_Resolved dust evolution in nearby galaxies_ 21


MNRAS **000**, 1–19 (2024)

22 _H.-J. Park et al._


Galaxy Ancillary data _[𝑎]_ Ref. _[𝑏]_


NGC 625 FN, UBVR, JHK, W1/2/3/4, I1/2/3/4, P1/2/3, S1/2 D09, Co14, Cu13, J03, M13
NGC 1512 FN, BVRI, JHK, W1/2/3/4, M1, P1/2/3, S1/2 G07, Ke03, Co14, Cu13, J03, D09, Ke11
NGC 1566 FN, BVRI, JHK, W1/2/3/4, I1/2/3/4, M1, P1/2/3, S1/2 G07, Ke03, J03, Cu13, Ke03, Cl13
NGC 1705 FN, BVRI, JHK, W1/2/3/4, I1/2/3/4, M1, P1/2/3, S1/2 G07, Co14, J03, Cu13, D09, M13
NGC 3521 FN, ugriz, JHK, W1/2/3/4, I1/2, P1/2/3, S1/2 G07, Br14, J03, Cu13, D09, Ke11
NGC 4536 FN, ugriz, JHK, W1/2/3/4, I1/2, P1/2/3, S1/2 G07, Br14, H03, J03, Cu13, S10, Ke11
NGC 5236 FN, UBVR, JHK, W1/2/3/4, I1/2/3/4, M1, P1/3, S1/2 Bi10, Ku00, J03, Cu13, Be11
NGC 5253 FN, UBVR, JHK, W1/2/3/4, I1/2/3/4, P1/2/3, S1/2 G07, Co14, J03, D09, M13
NGC 6822 FN, UBV, JHK, W1/2/3/4, I1/2/3/4, M1, P1/2/3, S1/2 H10, Ke03, J03, Cu13, M13
NGC 7793 FN, UBVR, JHK, W1/2/3/4, I1/2/3/4, M1, P1/2/3, S1/2 G07, Co14, J03, Cu13, D09, Ke11
Sextans A FN, UBVR, JHK, I1/2, M1, P1/2/3, S1/2/3 G07, Co14, D09, J03, Cl13


**Table C2.** Ancillary multi-wavelength data used in this study.
_𝑎_ FN = _𝐺𝐴𝐿𝐸𝑋_ Far/Near-UV, UBVRI = _𝐶𝑇𝐼𝑂_ / _𝐾𝑃𝑁𝑂_ U/B/V/R/I bands, ugriz = _𝑆𝐷𝑆𝑆_ u/g/r/i/z bands, JHK = 2 _𝑀𝐴𝑆𝑆_ J/H/K bands, W1/2/3/4 = _𝑊𝐼𝑆𝐸_
3.4/4.6/12/22 _𝜇_ m, I1/2/3/4 = _𝑆𝑝𝑖𝑡𝑧𝑒𝑟_ − _𝐼𝑅𝐴𝐶_ 3.6/4.5/5.8/8.9 _𝜇_ m, M1 = _𝑆𝑝𝑖𝑡𝑧𝑒𝑟_ − _𝑀𝐼𝑃𝑆_ 24 _𝜇_ m, P1/2/3 = _𝐻𝑒𝑟𝑠𝑐ℎ𝑒𝑙_ − _𝑃𝐴𝐶𝑆_ 70/100/160 _𝜇_ m, S1/2 =
_𝐻𝑒𝑟𝑠𝑐ℎ𝑒𝑙_ − _𝑆𝑃𝐼𝑅𝐸_ 250/350 _𝜇_ m.
_𝑏_ Reference: D09 = Dale et al. (2009), Co14 = Cook et al. (2014), Cu13 = Cutri et al. (2021), J03 = Jarrett et al. (2003), M13 = Madden et al. (2013), G07 = Gil
de Paz et al. (2007), K03 = Kennicutt et al. (2003), K11 = Kennicutt et al. (2011), Br14 = Brown et al. (2014), S10 = Sheth et al. (2010), Bi10 = Bigiel et al.
(2010), Ku00 = Kuchinski et al. (2000), Be11 = Bendo et al. (2012), H10 = Hunter et al. (2010), Cl13 = Clark et al. (2018)


MNRAS **000**, 1–19 (2024)


</paper>

## Items to check

```json
[
 {
  "path": "data.alma_project_codes[2].evidence[0]",
  "value": "2015.1.00782.S",
  "failed_quote": "An exception is that the NGC 7793 CO (2-1) moment 0 map has been made separately using the ALMA 12m data cube observed by the ALMA-LEGUS survey (Grasha et al. 2018; Finn et al. 2024) (Program code: 2015.1.00782.S, PI: Johnson)."
 },
 {
  "path": "data.other_facilities[9].provided.evidence[0]",
  "value": "Far-IR images at 70, 100, 160, 250, and 350 um",
  "failed_quote": "For the far-IR images, we use data from Herschel -PACS at wavelengths of 70, 100, and 160 𝜇 m, as well as from Herschel -SPIRE at wavelengths of 250 and 350 𝜇 m."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Colour-magnitude diagram source catalogue for NGC 6822",
  "failed_quote": "To distinguish Milky Way/main sequence (MW/MS) stars within NGC 6822, we perform a cross-match of coordinates between the categorized MW/MS sources (from colour-magnitude diagram by Hirschauer et al. 2020) and the Gaia DR3 source."
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "PHANGS-ALMA CO(2-1) data processing and moment 0 maps",
  "failed_quote": "For five of the sample galaxies, the CO (2-1) images are provided by Physics at High Angular resolution in Nearby Galaxies (PHANGS [9] ) team as part of the PHANGS-ALMA collaboration, an Atacama Large Millimeter/submillimetre Array (ALMA) large program (Leroy et al. 2021a; Leroy et al. 2021b)."
 },
 {
  "path": "processing.inherited[4].what.evidence[0]",
  "value": "ALMA-LEGUS CO(2-1) data cube for NGC 7793",
  "failed_quote": "An exception is that the NGC 7793 CO (2-1) moment 0 map has been made separately using the ALMA 12m data cube observed by the ALMA-LEGUS survey (Grasha et al. 2018; Finn et al. 2024) (Program code: 2015.1.00782.S, PI: Johnson)."
 },
 {
  "path": "processing.inherited[6].what.evidence[0]",
  "value": "Statistical framework and one-zone dust evolution modelling in BEDE",
  "failed_quote": "Additionally, we use the statistical frameworks outlined in De Vis et al. (2021) for a Bayesian MCMC approach. For the full description of the models, we refer readers to De Vis et al. (2021)."
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Use archival moment 0 maps where available, or extract moment 0 maps from HI and non-primary-beam-corrected CO cubes using 3D-Barolo (applying PB correction afterwards); exclude MW cirrus velocity channels for NGC 6822; construct 3-sigma CO sensitivity map for Sextans A",
  "failed_quote": "We obtain the rms maps using the 3D-Barolo for the two native data cubes and multiply by three (i.e., 3 S/N) to construct a CO(1-0) emission sensitivity map ."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Correct photometry for MW foreground extinction, subtract sky background using IDL sky.pro, remove foreground stars from FUV to 24 um using PTS-7/8 (with Gaia DR3 and CMD cross-matching for NGC 6822), convolve all maps using Aniano et al. (2011) kernels, resample with SWARP, and compute pixel uncertainty maps",
  "failed_quote": "For such images, we build sky background maps using an IDL tool ‘sky’ [14] . We apply a 3- 𝜎 clipping method to remove sources from the image and derive a median value of the background levels of a given box size."
 },
 {
  "path": "software[1].used_for.evidence[2]",
  "value": "Extracting HI and CO moment 0 maps and CO rms sensitivity maps from data cubes",
  "failed_quote": "We obtain the rms maps using the 3D-Barolo for the two native data cubes and multiply by three (i.e., 3 S/N) to construct a CO(1-0) emission sensitivity map ."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Sky background subtraction and measuring sky standard deviation and aperture area for photometric uncertainty maps",
  "failed_quote": "For such images, we build sky background maps using an IDL tool ‘sky’ [14] ."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Metallicity-dependent CO-to-H2 conversion factor alpha_CO,Z (computed for comparison in global relation, but main resolved analysis uses constant alpha_CO,MW to reduce uncertainty)",
  "failed_quote": "In the following analysis of the ISM scaling relations, we only show the resolved 𝑀 mol or resolved DGR values calculated using the 𝛼 CO , MW to reduce any uncertainty that could be raised by employing 𝛼 CO , Z ."
 }
]
```
