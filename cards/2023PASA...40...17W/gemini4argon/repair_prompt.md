# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023PASA...40...17W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Publications of the Astronomical Society of Australia_ (2022), 1–25


**ARTICLE TYPE**

## **VERTICO V: The environmentally driven evolution of the inner cold** **gas discs of Virgo cluster galaxies**


Adam B. Watts, [1,2] Luca Cortese, [1,2] Barbara Catinella, [1,2] Toby Brown, [3] Christine D. Wilson, [4] Nikki Zabel, [5] Ian D. Roberts, [6] Timothy A. Davis, [7] Mallory Thorp, [8] Aeree Chung, [9] Adam R.H. Stevens, [1,2] Sara L. Ellison, [8] Kristine Spekkens, [10] Laura C. Parker, [4] Yannick M. Bahé, [6] Vicente Villanueva, [11] María Jiménez-Donaire, [12,13] Dhruv Bisaria, [14] Alessandro Boselli, [15] Alberto D. Bolatto, [11]

and Bumhyun Lee [16]


1 International Centre for Radio Astronomy Research, The University of Western Australia, Crawley, WA, Australia
2 ARC Centre of Excellence for All-Sky Astrophysics in 3 Dimensions (ASTRO3D), Australia
3 Herzberg Astronomy and Astrophysics Research Centre, National Research Council of Canada, 5071 West Saanich Rd., Victoria, BC V9E 2E7, Canada
4 Department of Physics & Astronomy, McMaster University, 1280 Main Street W, Hamilton, ON, L8S 4M1, Canada
5 Department of Astronomy, University of Cape Town, Private Bag X3, Rondebosch 7701, South Africa
6 Leiden Observatory, Leiden University, PO Box 9513, NL-2300 RA Leiden, The Netherlands
7 Cardiff Hub for Astrophysics Research & Technology, School of Physics & Astronomy, Cardiff University, Queens Buildings, Cardiff, CF24 3AA, UK
8 Department of Physics & Astronomy, University of Victoria, Finnerty Road, Victoria, BC V8P 1A1, Canada
9 Department of Astronomy, Yonsei University, 50 Yonsei-ro, Seodaemun-gu, Seoul 03722, Republic of Korea
10 Department of Physics and Space Science, Royal Military College of Canada, PO Box 17000, Station Forces, Kingston, Ontario, Canada, K7K 7B4
11 Department of Astronomy, University of Maryland, College Park, MD 20742, USA
12 Observatorio Astronómico Nacional (IGN), C/Alfonso XII, 3, E-28014 Madrid, Spain
13 Centro de Desarrollos Tecnológicos, Observatorio de Yebes (IGN), 19141 Yebes, Guadalajara, Spain
14 Department of Physics, Engineering Physics, and Astronomy, Queen’s University, Kingston, ON K7L 3N6, Canada
15 Aix-Marseille Université, CNRS, CNES, LAM, Marseille, France
16 Korea Astronomy and Space Science Institute, 776 Daedeokdae-ro, Daejeon 34055, Republic of Korea
**Author for correspondence:** Adam B. Watts, Email: adam.watts@uwa.edu.au.


**Abstract**


The quenching of cluster satellite galaxies is inextricably linked to the suppression of their cold interstellar medium (ISM) by environmental
mechanisms. While the removal of neutral atomic hydrogen (H I) at large radii is well studied, how the environment impacts the remaining gas
in the centres of galaxies, which are dominated by molecular gas, is less clear. Using new observations from the Virgo Environment traced in
CO survey (VERTICO) and archival H I data, we study the H I and molecular gas within the optical discs of Virgo cluster galaxies on 1.2-kpc
scales with spatially resolved scaling relations between stellar ( Σ _⋆_ ), H I ( Σ H I ), and molecular gas ( Σ mol ) surface densities. Adopting H I deficiency
as a measure of environmental impact, we find evidence that, in addition to removing the H I at large radii, the cluster processes also lower the
average Σ H I of the remaining gas even in the central 1.2 kpc. The impact on molecular gas is comparatively weaker than on the H I, and we
show that the lower Σ mol gas is removed first. In the most H I-deficient galaxies, however, we find evidence that environmental processes
reduce the typical Σ mol of the remaining gas by nearly a factor of 3. We find no evidence for environment-driven elevation of Σ H I or Σ mol in
H I-deficient galaxies. Using the ratio of Σ mol -to- Σ H I in individual regions, we show that changes in the ISM physical conditions, estimated
using the total gas surface density and midplane hydrostatic pressure, cannot explain the observed reduction in molecular gas content. Instead,
we suggest that direct stripping of the molecular gas is required to explain our results.


**Keywords:** galaxies: clusters: individual: Virgo – galaxies: clusters: intracluster medium – galaxies: evolution – galaxies: ISM, radio lines: galaxies – techniques:
interferometric



**1.** **Introduction**


Galaxies experience different evolutionary processes depending on the environment in which they live, leading to variation
in their observed properties as a function of environment. In
particular, galaxies in denser environments contain a systematically lower mass of cold, gaseous interstellar medium (ISM)
than isolated systems (e.g., Haynes & Giovanelli, 1984; Giovanelli & Haynes, 1985; Solanes et al., 2001; Fumagalli et al.,
2009; Cortese et al., 2011; Catinella et al., 2013; Brown et al.,
2017; Zabel et al., 2019; Stevens et al., 2019b, 2021). As this
cold gas is the fuel for star formation (e.g., Schmidt, 1959;
Kennicutt, 1989; Leroy et al., 2008; Bacchini et al., 2019; Saintonge & Catinella, 2022), completing our understanding of



the physics of galaxy evolution requires understanding how
environmental mechanisms impact their cold gas content.
Galaxy clusters are one of the densest environments in
the Universe, where galaxies are subject to numerous environmental mechanisms (e.g. Boselli & Gavazzi, 2006). Their
deep gravitational potentials cause tidal stripping of satellite
galaxies near the cluster center (Byrd & Valtonen, 1990; Fujita,
1998), and give galaxies large relative velocities (> 500 km s [–1],
Girardi et al., 1993; Struble & Rood, 1999), causing them to
undergo fast gravitational interactions such as galaxy harassment (Moore et al., 1996; Mihos, 2004). Additionally, clusters are permeated by a hot (> 10 [7] K) intra-cluster medium
(ICM, e.g., Sarazin, 1986; Mohr et al., 1999; Boselli & Gavazzi,
2006; Frank et al., 2013). Interaction with this ICM results in

2 Adam B. Watts _et al._



galaxies undergoing hydrodynamical processes such as thermal
evaporation of the ISM (Cowie & Songaila, 1977), turbulent
stripping by viscous momentum transfer between the ICM
and ISM (Nulsen, 1982), and/or ram-pressure stripping (RPS,
Gunn & Gott, 1972). As the removal of gas results in the future cessation of star formation, the action of these numerous
environmental processes is often invoked to explain the large
fractions of quenched galaxies hosted by clusters (Dressler,
1980; Kauffmann et al., 2004; Peng et al., 2010; Woo et al.,
2013). While the timescale for quenching depends on the gas
removal mechanism and the circularity of the in-fall orbit
(Font et al., 2008; Jung et al., 2018), cluster satellites are consistent with their star formation being significantly reduced
before or at first pericentre passage (e.g., Crowl & Kenney,
2008; Ciesla et al., 2016; Boselli et al., 2016a; Vulcani et al.,
2020; Werle et al., 2022), suggesting a fast gas removal process
(e.g., Boselli & Gavazzi, 2006; Fossati et al., 2018; Boselli et al.,
2020; Upadhyay et al., 2021; Wright et al., 2019, 2022).
Indeed, there is significant evidence that hydrodynamical
stripping is a dominant mechanism for removing gas from
cluster galaxies (see the reviews by Cortese et al., 2021; Boselli
et al., 2022). In the canonical outside-in picture of stripping,
the circumgalactic medium is first removed and cuts galaxies
off from further accretion (Larson et al., 1980), before progressing to strip the ISM directly (e.g., Kenney et al., 2004;
Chung et al., 2007; Cortese et al., 2010). Further, cometary
tails of stripped gas from the ISM have been observed with
multi-wavelength tracers from the X-rays to the radio continuum (e.g. Sivanandam et al., 2014; Jáchym et al., 2014, 2017;
Moretti et al., 2020b; Longobardi et al., 2020; Roberts et al.,
2021; Ignesti et al., 2022), and reproduced in controlled and
cosmological simulations of galaxy evolution (e.g. Tonnesen
& Bryan, 2010; Marasco et al., 2016; Yun et al., 2019).
Most of our understanding of how environmental processes impact the cold gas in galaxies comes from observations
of the 21-cm emission line from neutral atomic hydrogen (H I),
as its large radial extent makes it a sensitive tracer of external
environmental mechanisms. In the case of hydrodynamical
stripping, galaxies exhibit clear truncation of their H I distribution at a radius that depends on the strength of the ram pressure
(Gunn & Gott, 1972; Cayatte et al., 1990; Roediger & Hensler,
2005; Tonnesen & Bryan, 2009; Abramson et al., 2011; Yoon
et al., 2017; Reynolds et al., 2021, 2022). The impact of these
environmental processes on the molecular hydrogen (H 2 ) is
less clear; however, truncation of the star formation in stripped
galaxies (e.g., Koopmann & Kenney, 2004; Boselli et al., 2006;
Cortese et al., 2012; Fossati et al., 2013, 2018) indicates that the
H 2 is also affected once stripping proceeds within the stellar
disc. Further, the presence of star formation inside this truncation radius means that some gas can survive the stripping
process. Whether the environment has also influenced this
surviving gas, which would also affect the timescale for star
formation to halt (e.g. Boselli et al., 2014; Cortese et al., 2021),
remains unknown. As this surviving gas is often dominated
by H 2 (Boselli et al., 2014; Cortese et al., 2016; Loni et al.,
2021), understanding the impact of environmental processes
on the molecular ISM in galaxies is essential to completing our



picture of galaxy evolution in dense environments.
Under most ISM conditions, however, H 2 cannot be directly observed as it is a symmetric molecule without a permanent dipole. Instead, most of our understanding of the
molecular ISM (from here, ‘molecular gas’ or subscript ‘mol’)
comes from observing the rotational transitions of CO and
its isotopologues (Bolatto et al., 2013; Saintonge et al., 2017).
These observations have revealed that molecular gas is not
affected by environmental processes as strongly as H I. This
resistance is primarily because a large fraction of molecular
gas exists in giant molecular clouds (GMCs), and it is typically
more centrally concentrated where the gravitational restoring
force is stronger, making it more resistant to direct stripping
than the H I (e.g., Engargiola et al., 2003; Bolatto et al., 2008;
Yamagami & Fujita, 2011; Stevens et al., 2021). Instead, environmental processes typically lower the molecular gas content
in the outskirts of galaxies first (Lee et al., 2020; Brown et al.,
2021; Zabel et al., 2022), while significant reduction of the
molecular gas mass of galaxies is only observed once galaxies
have lost a large fraction of their total H I mass (Fumagalli et al.,
2009; Boselli et al., 2014).
Although this picture is consistent with the outside-in stripping scenario, there is growing evidence that it is more complicated than just radial truncation. Simulations have shown that
the multi-phase nature of the ISM allows the ICM to stream
through low-density regions of the surviving gas inside the H I
truncation radius, allowing environmental processes to affect
the cold gas across the disc (Tonnesen & Bryan, 2009; Choi
et al., 2022). Disturbed molecular gas morphologies in cluster
galaxies can resemble the H I (e.g., Lee et al., 2017), and highresolution studies of individual objects have shown GMCs decoupled from large plumes of trailing gas (e.g., Cramer et al.,
2020). Further, the mass of molecular gas detected in the tails
of stripped gas trailing behind cluster galaxies requires some
level of mass-loading from the ISM (e.g., Sivanandam et al.,
2010; Moretti et al., 2018; Lee & Chung, 2018; Jáchym et al.,
2019), and there is evidence for the direct stripping of cold ISM
from dust observations (e.g., Crowl et al., 2005; Longobardi
et al., 2020). Alternately, stripping of the molecular gas may
not be a dominant process, and the reduction of molecular gas
mass could be due to the preferential removal of H I across the
disc, leaving insufficient fuel to maintain efficient molecule
formation (Fumagalli et al., 2009; Tonnesen & Bryan, 2009;
Zabel et al., 2022; Villanueva et al., 2022). To further complicate the picture, there is evidence for increased molecular
gas formation efficiency due to gas compression during the
ICM-ISM interaction (e.g., Tonnesen & Bryan, 2009; Moretti
et al., 2020a,b). Clearly, our picture of how the environment
impacts the molecular gas in galaxies is incomplete.
In this work, we present a new analysis of the cold gas properties within the stellar components of Virgo cluster galaxies
using observations from the Virgo Environment Traced in
CO(2-1) (VERTICO, Brown et al., 2021) ALMA ACA [a] large
program. The Virgo cluster is an excellent target for further

a Atacama Large Millimetre/Sub-millimetre Array and Atacama Compact
Array

_Publications of the Astronomical Society of Australia_ 3



ing our understanding of the environment’s impact on galaxies’
cold gas content. At a distance of 16.5 Mpc (Mei et al., 2007)
it is close, allowing for detailed studies of individual galaxies,
and it has been observed comprehensively across nearly the
entire electromagnetic spectrum (York et al., 2000; Chung
et al., 2009; Davies et al., 2010; Urban et al., 2011; Boselli et al.,
2011, 2018a). The presence of infalling sub-structures also
means that there are populations of galaxies at various stages of
infall, and thus environmental impact (Gavazzi et al., 1999; Mei
et al., 2007; Kim et al., 2016; Yoon et al., 2017). Additionally,
the VERTICO sample was selected from the VLA Imaging of
Virgo galaxies in Atomic gas survey (VIVA, Chung et al., 2009)
of H I emission. Together, these data enable us to study how
the environmental processes influence the cold gas properties
of galaxies in the Virgo cluster on _∼_ 1.2-kpc scales.
We present our study using the framework of spatially
resolved scaling relations (e.g., Bigiel et al., 2008; Morselli
et al., 2020; Ellison et al., 2021a,b; Pessa et al., 2022; Abdurro’uf
et al., 2022a,b; Baker et al., 2022), in particular those between
stellar, H I, and molecular gas mass surface densities. While
azimuthally averaged radial profiles are useful for increasing
sensitivity to faint emission, in this work, we focus on the
bright emission within the optical components of galaxies.
Thus, comparing the physical quantities of kpc-scale regions
within galaxies increases our statistics, and reduces the effects
of averaging over larger areas that include many different
physical regions. For analyses of how the environment impacts
the radial profiles of cold gas content in VERTICO galaxies,
we refer the reader to the works of Brown et al. (2021); Zabel
et al. (2022), and Villanueva et al. (2022).
This paper is structured as follows. In §2 we describe our
VERTICO sample, control sample, the homogenisation of
the data, and ancillary data products. In §3 we investigate
the resolved scaling relations with all galaxies combined and
discuss some of the caveats of this approach. We present our
main results in §4, where we study how the environment
impacts the spatially resolved H I and molecular gas content of
galaxies across their stellar discs and within the truncation of
their gas discs. In §5 we investigate the physical mechanisms
responsible for our observations, and in §6 we summarise our
results.
As described in Brown et al. (2021), all physical quantities
used in this work were computed using a Kroupa (2001) stellar
initial mass function, a Λ CDM cosmology with _h_ = 0.7, Ω M =
0.3 and Ω Λ = 0.7, and we adopt a constant distance for Virgo
galaxies of 16.5 Mpc (Mei et al., 2007).


**2.** **Datasets**

_**2.1**_ _**VERTICO sample**_
We selected our main galaxy sample from the VERTICO survey (Brown et al., 2021), which obtained CO(2-1) observations [b] for 51 Virgo cluster galaxies extracted from the VIVA
survey. We refer the reader to Brown et al. (2021) for a detailed


b The CO(2-1) data are publicly available at [https://www.canfar.net/](https://www.canfar.net/storage/list/VERTICO)
[storage/list/VERTICO](https://www.canfar.net/storage/list/VERTICO)



description of the parent sample selection and data reduction.
In this work, we focus on massive ( log ( _M_ _⋆_ /M _⊙_ ) _≥_ 10) galaxies
to minimise metallicity-dependent uncertainties in tracing the
molecular gas content of galaxies with CO(2-1) emission, and
we enforce an optical inclination cut of _i_ _≤_ 70 _[◦]_ to avoid large
de-projection uncertainties. We also removed two galaxies
that met these criteria, NGC 4772 and NGC 4698, as they are
passive, early-type discs that have recently accreted their H I
gas (Haynes et al., 2000; Cortese & Hughes, 2009; Yoon et al.,
2017), and thus their H I and molecular gas properties do not
reflect the action of the Virgo environment on their cold gas
content. Our final VERTICO sample consists of 18 galaxies,
and the properties of the galaxies used in this work are summarised in Table 1, along with their sources and derivations
that are also described below.
The native spatial resolution of VERTICO data is _∼_ 8arcsec, and data products with 9-arcsec and 15-arcsec resolution were also created using the IMSMOOTH routine of the
Common Astronomy Software Applications package (CASA,
McMullin et al., 2007). We used the coarser 15-arcsec data
products sampled with 8-arcsec spaxels, which are closer to the
spatial resolution of the H I data. The VIVA H I data used in
this work were re-imaged by author A. Chung to circularise
the synthesised beam and match the VERTICO data products
as closely as possible, resulting in datacubes with 8 arcsec spaxels and synthesised beams varying from 15.2–20 arcsec, with
an average of 17 arcsec. At the assumed 16.5 Mpc distance
to Virgo, the 15/8-arcsec beam/spaxels of the VERTICO data
correspond to a 1200/650 pc physical resolution.
Signal masks were created for the CO(2-1) and H I datacubes as described in Brown et al. (2021, but see also Sun
et al. 2018 and Leroy et al. 2021), and moment 0 maps created
for each galaxy. The H I mass in each spaxel was calculated
assuming optically thin emission (e.g., Meyer et al., 2017),


_M_ H I [M _⊙_ ] = 2.35 _×_ 10 [5] _D_ L [2] [(1 +] _[ z]_ [)] [–2] _[S]_ [H I] [,] (1)


where _D_ L is the luminosity distance to the object (assumed
to be 16.5 Mpc for all VERTICO galaxies), _z_ is the redshift,
and _S_ H I is the velocity-integrated spectral flux density (in
Jy km s [–1] ). Unless otherwise specified, we do not correct our
H I masses for the Helium abundance. The velocity-integrated
CO(2-1) flux density ( _S_ CO ) was used to calculate the total
CO(2-1) luminosity using the method of Solomon & Vanden Bout (2005),


_L_ CO [K km s [–1] pc [–2] ] = 3.25 _×_ 10 [7] ν [–2] _D_ L [2] [(1 +] _[ z]_ [)] [–3] _[ S]_ CO [,] [(2)]


where ν is the observed frequency. The molecular gas mass
was then computed using


_M_ mol [M _⊙_ ] = [α] [CO] _L_ CO, (3)

_R_ 21


where _R_ 21 is the integrated flux ratio of the CO(2-1) and
CO(1-0) lines and α CO is the molecular gas mass to CO(1-0)
luminosity correction factor. We used a constant _R_ 21 = 0.8,
as derived by Brown et al. (2021), and a constant α CO =

4 Adam B. Watts _et al._


**Table 1.** Properties of the galaxies used in this work. VERTICO galaxies are contained in the top section, while the HERACLES control sample is in the bottom
segment.


Galaxy _D_ L [Mpc] PA [deg] _i_ [deg] _R_ 25 [arcmin] log _M_ _⋆_ [ M _⊙_ ] log SFR [M _⊙_ yr [–1] ] def-H I [dex] _⟨_ log Σ _⋆_ _⟩_ H I [ M _⊙_ pc [–2] ]


VERTICO


NGC4254 16.5 243 39 2.68 10.52 0.70 –0.10 0.24


NGC4293 16.5 239 67 2.81 10.50 –0.27 2.25 2.74


NGC4298 16.5 132 52 1.62 10.11 –0.26 0.41 1.36


NGC4321 16.5 280 32 3.70 10.71 0.54 0.35 1.15


NGC4380 16.5 158 61 1.74 10.11 –0.77 1.13 1.69


NGC4394 [a] 16.5 312 32 1.82 10.34 –0.79 0.62 1.13


NGC4450 16.5 170 51 2.62 10.70 –0.55 1.17 2.35


NGC4457 16.5 256 36 1.35 10.42 –0.49 0.92 1.99


NGC4501 16.5 320 65 3.46 11.00 0.43 0.58 1.64


NGC4535 16.5 11 48 3.54 10.49 0.31 0.41 0.44


NGC4548 16.5 318 37 2.68 10.65 –0.28 0.82 1.52


NGC4567 [a] 16.5 251 49 1.48 10.25 0.03 0.13 1.57


NGC4568 16.5 211 70 2.29 10.47 0.29 0.38 1.25


NGC4569 16.5 203 69 4.78 10.86 0.16 1.47 1.95


NGC4579 16.5 273 40 2.94 10.92 0.08 0.95 1.88


NGC4651 16.5 75 53 1.99 10.31 –0.10 –0.30 0.04


NGC4654 16.5 300 61 2.45 10.26 0.31 0.12 0.79


NGC4689 16.5 341 38 2.13 10.16 –0.29 0.68 1.49


HERACLES


NGC0628 9.8 207 29 4.92 10.24 0.23 –0.12   

NGC3184 13.0 224 13 3.70 10.37 0.13 0.09   

NGC3351 10.0 193 41 3.60 10.28 0.07 0.38   

NGC3627 10.6 351 59 5.14 10.67 0.50 0.79   

NGC5055 8.9 284 63 5.93 10.72 0.28 –0.06   

NGC5194 8.6 235 25 3.85 10.73 0.65 –0.08   

NGC5457 7.0 213 31 11.99 10.39 0.54 –0.13   

NGC6946 7.7 250 36 5.70 10.50 0.79 –0.64   

a VERTICO data are 7-m array only, the rest have 7-m and Total Power array data
Columns: 1) Galaxy name; 2) Luminosity distance (Mei et al., 2007; Walter et al., 2008); 3) Position angle (Brown et al., 2021); 4) inclination (Brown et al.,
2021); 5) _B_ -band optical radius (Chung et al., 2009; Walter et al., 2008); 6) log 10 integrated stellar mass (Leroy et al., 2019); 7) log 10 integrated star-formation
rate (Leroy et al., 2019); 8) H I deficiency parameter (Chung et al., 2009, this work); 9) average log Σ _⋆_ at the H I -radius Σ H I = 1 M _⊙_ pc [–2] (this work).



4.35 M _⊙_ pc [–2] based on observations of the Milky Way disc by
Bolatto et al. (2013), which includes a 36 per cent contribution
from Helium. The H I and molecular gas mass of spaxels
were converted to surface densities Σ H I and Σ mol in units of
M _⊙_ pc [–2] using the 650-pc physical pixel size.

Global stellar masses were drawn from the _z_ = 0 Multiwavelength Galaxy Synthesis ( _z_ 0MGS, Leroy et al., 2019)
sample, a collection of GALEX (Galaxy Evolution Explorer,
Martin et al., 2005), and WISE (Wide-field Infrared Survey
Explorer, Wright et al., 2010) data for _∼_ 11 000 galaxies with
_D_ < 50 Mpc and brighter than _M_ B = –18 mag. Stellar-mass
estimates were computed from WISE band-1 observations
using the WISE band-1 and -3 colour to determine the massto-light ratio, as described in Leroy et al. (2019). The same
prescriptions were applied on a pixel-by-pixel basis to create
resolved maps of stellar surface density ( Σ _⋆_ ) at the same resolution as the H I and molecular gas data. Photometric position
angles (PA) and inclinations ( _i_ ) for each galaxy were calculated



by fitting Kron apertures to SDSS [c] _r_ -band images (Brown
et al., 2021) and assuming an intrinsic axial ratio of _q_ = 0.2,
and _B_ -band 25 [th] mag arcsec [–2] optical radii ( _R_ 25 ) were sourced
from Chung et al. (2009). All surface densities used in this
work were de-projected to face-on values using a factor of
cos ( _i_ ).
To quantify the impact of the environment on VERTICO
galaxies, we used the type-independent H I deficiency parameter (def-H I) for each galaxy from Chung et al. (2009), which
compares the observed H I content to the average content in
isolated galaxies with the same optical size. It is defined as


def-H I = log Σ H I – log Σ H I, obs (4)


where Σ H I, obs = S H I /(2 _R_ 25 ) [2] is the mean surface density
within the optical disc. Following Chung et al. (2009), this


c Sloan Digital Sky Survey (York et al., 2000; Abazajian et al., 2009)

_Publications of the Astronomical Society of Australia_ 5



definition uses S H I in units of Jy km s [–1] and _R_ 25 in arcminutes,
and log Σ H I = 0.37 is the average type-independent value of
log ( _M_ H I / _D_ 25 [2] [) from][ Haynes & Giovanelli][ (][1984][,] [Table 4, 6.81)]
after a unit conversion from M _⊙_ kpc [–2] . A larger def-H I value
corresponds to a smaller H I mass compared to isolated galaxies,
and the typical scatter in the def-H I distribution for isolated
galaxies is _∼_ 0.2 – 0.3 dex (Haynes & Giovanelli, 1984; Jones
et al., 2018, thus automatically encapsulating the variations in
the spatial distribution of H I surface density observed in isolated galaxies). In this work, we define ‘H I-deficient’ galaxies
as those with def-H I _≥_ 0.3 dex, namely, a factor of ≳ 2 more
H I-poor than expected.


We are primarily interested in the properties of the gas
within the optical disc of galaxies, so we masked each galaxy
to only include pixels/spaxels within the _B_ -band _R_ 25, where
the radius of each spaxel was calculated from the photometric
PA and inclination. While this allows us to study the impact
of the environment across the discs of galaxies, we are also
interested in how the environment impacts the _surviving_ cold
gas disc. The extent of the H I gas is a good tracer of the gas
truncation radius, outside of which stripping is usually assumed
to be effective. As our analysis uses the relationships between
Σ _⋆_, Σ H I, and Σ mol, it is useful to quantify the size of the H I
reservoir in terms of Σ _⋆_ .


We computed radial profiles of log Σ H I and log Σ _⋆_ using
4 arcsec annuli, which we found gave the best consistency
with the Chung et al. (2009) VIVA measurements. Defining
the H I truncation radius ( _R_ H I ) to be where the radial average
Σ H I = 1 M _⊙_ pc [–2] (e.g., Wang et al., 2014, 2016; Stevens et al.,
2019a), we used the value of log Σ _⋆_ at this radius to determine
the average log Σ _⋆_ at _R_ H I, _⟨_ log Σ _⋆_ _⟩_ H I . In the most H I-rich
galaxies, _R_ H I can fall outside of the _B_ -band _R_ 25, but this does
not affect any of our results as these galaxies are not the focus
of our analysis. Further, in all galaxies, less than 5 per cent
of spaxels with Σ _⋆_ _≥⟨_ log Σ _⋆_ _⟩_ H I have radius > _R_ H I, meaning
trends with higher (lower) Σ _⋆_ trace trends with smaller (larger)
galactocentric radius. We also note here that while the H I
observations cover the optical disc of each galaxy, the size of
the VERTICO CO(2-1) observation footprints were based on
the _R_ H I of each target. Subsequently, there is some variation
in the physical coverage of the molecular gas in galaxies (0.44–
1 _×_ _R_ 25 ), and we accounted for this in our analysis of the
molecular gas content.


While the VERTICO sample contains some H I-normal
systems, environmental processes can begin to impact galaxies
before they become H I-deficient. Thus, we chose to draw our
control sample from a different survey to ensure that we had
an H I-normal reference that was as free from environmental
effects as possible. We include the H I-normal VERTICO
systems in some of our figures (Figs. 1, 3, and 6) and discuss
them briefly in §4, but the main focus of our analysis is the
H I-deficient galaxies.



_**2.2**_ _**HERACLES control sample**_
We extracted a control sample of galaxies from the HERA [d]

CO(2-1) Legacy Survey (HERACLES, Leroy et al., 2009).
HERACLES targeted the CO(2-1) emission line in 33 galaxies
from The H I Nearby Galaxy Survey (THINGS, Walter et al.,
2008), a sample of nearby ( _D_ < 15 Mpc), late-type galaxies
spanning from dwarfs to massive spirals. After excluding nondetections and five galaxies that overlap with VERTICO, there
are 25 HERACLES galaxies with public data (for more details
see Brown et al., 2021). Physical quantities for HERACLES
galaxies were calculated using the same methods and sources
as described for VERTICO, and _B_ -band _R_ 25 were drawn from
Walter et al. (2008). We did not compute _⟨_ log Σ _⋆_ _⟩_ H I for HERACLES galaxies as the _R_ H I was nearly always outside _R_ 25 .
The HERACLES native resolution datacubes have a synthesised beam-width of 13 arcsec, while the THINGS data
are more varied depending on the VLA configuration. Before
calculating physical quantities, the HERACLES and THINGS
data were smoothed using the IMSMOOTH routine of CASA to
match the _physical_ spaxel size and resolution of the VERTICO
data, and circularise the synthesised beam. As the distances
to HERACLES sample galaxies vary, this left 11 galaxies that
could be matched to a 1200-pc physical resolution in both
CO(2-1) and H I.
To ensure that our HERACLES control sample is a reasonable representation of star-forming galaxies, we restricted
this sample to galaxies more star-forming than 1 σ below the
star-forming main-sequence using the parametrisation from
the _z_ 0MGS sample ( σ = 0.36, with star-formation rates (SFR)
from the same catalogue, Leroy et al., 2019). After the stellar mass and inclination selection cuts, our final HERACLES
control sample consists of eight galaxies, listed in Table 1.
We compared the integrated properties of the final control
sample galaxies to a subset of star-forming galaxies from the
xCOLD GASS [e] (Saintonge et al., 2017) sample, selected using the same SFR threshold. While the HERACLES galaxies
lie on or slightly above (< 1 σ ) the locus of the star-forming
main-sequence, they span the same range in log _M_ H I / _M_ _⋆_ and
log _M_ MG / _M_ _⋆_ as the xCOLD GASS sample, indicating that
there is no bias toward H I- or molecule-rich systems in our
control sample.
Last, we briefly mention the detection limits of each dataset
after the homogenisation of the spatial resolutions and the
masking procedures. The HERACLES:THINGS data are shallower than the VERTICO:VIVA data in both H I ( Σ H I _≥_ 1 –
3 M _⊙_ pc [–2] within _B_ -band _R_ 25 compared to Σ H I _≥_ 1 M _⊙_ pc [–2] )
and molecular gas ( Σ mol _≥_ 1–3 M _⊙_ pc [–2] compared to Σ mol _≥_
0.4–1 M _⊙_ pc [–2] ). Given that we are interested in environmentdriven reductions in both H I and molecular gas surface densities, the fact that the VERTICO:VIVA data are deeper ensures
that our findings are not due to differences in sensitivity between the two datasets. The shallower nature of HERACLES

means that it can have an increased fraction of non-detected
spaxels near the edge of the disc, and we account for this in


d Heterodyne Receiver Array (Schuster et al., 2004)
e eXtended CO Legacy Database for GASS

6 Adam B. Watts _et al._



1


0 0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0 3.5



1


0 0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0 3.5



1.0

0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0 3.5
log [M pc 2 ]



2.5


2.0


1.5


1.0


0.5


0.0


0.5



2.5


2.0


1.5


1.0


0.5


0.0


0.5



HERACLES: THINGS

VERTICO: VIVA


HI [ non-detection]



HERACLES

VERTICO: VIVA


mol [ non-detection]



1.0

0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0 3.5
log [M pc 2 ]



HI


2.5


2.0


1.5


1.0


0.5


0.0


0.5


0 ~~1.0~~ 2

PDF



mol


2.5


2.0


1.5


1.0


0.5


0.0


0.5


0 ~~1.0~~ 1

PDF



**Figure 1.** Spatially resolved Σ H I – and Σ mol – Σ _⋆_ scaling relations for the combined samples. The lef panel shows log Σ H I vs log Σ _⋆_, the resolved H I –
stellar mass scaling relation, and the right panel shows log Σ H I vs log Σ _⋆_, the resolved molecular gas–stellar mass scaling relation. Contours for both samples enclose 5, 16, 50, 84, and 95 per cent of the H I or molecular gas detected spaxels, while non-detected spaxels are shown with downward triangles at
log ( Σ H I /M _⊙_ pc [–2] ) = log ( Σ mol /M _⊙_ pc [–2] ) = –0.5 . Density-normalised histograms of log Σ _⋆_, log Σ H I, and log Σ mol are shown opposite their respective axes,
with filled histograms representing H I - or molecular gas-detected spaxels while open histograms represent non-detections. The HERACLES Σ _⋆_ histogram
for H I non-detections uses 0.25 dex bins compared to the 0.1 dex used for VERTICO as it has fewer points (331 compared to 5717). Compared to HERACLES,
the combined VERTICO sample has fewer Σ H I detected spaxels, particularly at lower log Σ _⋆_, and a lower average log Σ H I . Similarly, but less clearly, the
combined VERTICO sample has fewer Σ mol detections at lower Σ _⋆_, while the histogram of detected Σ mol has a larger tail toward lower values.



our analysis.


**3.** **Combined** Σ **H** I **–** Σ _⋆_ **and** Σ **mol** **–** Σ _⋆_ **relations**
In the left panel of Fig. 1 we plot Σ H I against Σ _⋆_, in other
words, the resolved H I–stellar mass (rH ISM) relation. Detected spaxels for HERACLES (blue) and VERTICO (red)
are shown with contours enclosing 5, 16, 50, 84, and 95
per cent of the population, and non-detections are shown at
log ( Σ H I /M _⊙_ pc [–2] ) = –0.5 with downward triangles. Densitynormalised histograms of log Σ _⋆_ and log Σ H I are shown opposite to their respective axes, computed with 0.25 dex bins.
Filled histograms show detected spaxels, while the open histograms on the Σ _⋆_ axis show the histogram of log Σ _⋆_ for H I
non-detected spaxels.
Focusing on HERACLES galaxies, the rH ISM relation of
H I-normal systems occupies a _∼_ 0.75 dex range in Σ H I across
the _∼_ 2.5 dex in Σ _⋆_ . H I is detected across the whole Σ _⋆_ range,
with non-detected spaxels having preferentially lower Σ _⋆_ compared to detections, also shown in the Σ _⋆_ histograms. This distribution of HERACLES points reflects the known result that
H I surface densities typically saturate around _∼_ 10 M _⊙_ pc [–2]

within the stellar components of galaxies (Martin & Kennicutt, 2001; Krumholz et al., 2009; Bigiel et al., 2008; Bigiel
& Blitz, 2012). Focusing now on VERTICO, it is clear that
the VERTICO combined rH ISM relation inhabits a different region of the parameter space compared to HERACLES.
First, there is a decreased number of H I-detected spaxels across
the range of Σ _⋆_, but preferentially at lower Σ _⋆_ . This change
is also visible in the Σ _⋆_ histograms where both the average
VERTICO detected and non-detected spaxels are shifted to
higher Σ _⋆_ compared to HERACLES. Second, the typical Σ H I



of VERTICO galaxies is lower. It is missing the largest Σ H I
values, there is a cloud of red points at log ( Σ _⋆_ /M _⊙_ pc [–2] ) > 1.5
with log ( Σ H I /M _⊙_ pc [–2] ) _∼_ 0 – 0.5 that does not exist in HERACLES, and the log Σ H I histogram of VERTICO galaxies is
broader, extending to lower Σ H I . The median detected spaxel
has log ( Σ H I /M _⊙_ pc [–2] ) = 0.58 for VERTICO galaxies, while
HERACLES has log ( Σ H I /M _⊙_ pc [–2] ) = 0.93, and a two-sample
Kolmogorov-Smirnov (K-S) test rejects the null hypothesis
that the two Σ H I distributions are drawn from the same parent
distribution with high significance ( _p_ < 10 [–4] ).
Given that the VERTICO sample spans a range of def-H I
values (–0.3 – 2.25 dex ) and Σ _⋆_ increases toward the centres of
galaxies, these changes are broadly consistent with galaxies undergoing ram-pressure stripping from the ICM. Namely, the
ISM at large radii is affected first, while lowering the average
gas surface density within the central regions where the gas
is more gravitationally bound requires stronger stripping that
has proceeded within the stellar disc (Roediger & Brüggen,
2007; Fumagalli et al., 2009; Steinhauser et al., 2016; Yoon
et al., 2017), and these two effects clearly emerge in this figure.
How are these differences reflected in the molecular gas
surface density of galaxies? In the right panel of Fig. 1, we
show the resolved molecular gas–stellar mass (rMGSM) relation [f] for the combined HERACLES and VERTICO samples
using the same colouring and non-detection labelling as the
rH ISM relation. Unlike Σ H I, Σ mol shows a positive correlation with Σ _⋆_, and differences between the combined rMGSM
relation of HERACLES and VERTICO are less distinct. Non

f Often called the ‘resolved molecular gas main sequence’ in other works
(Lin et al., 2019; Ellison et al., 2021b; Pessa et al., 2021).

_Publications of the Astronomical Society of Australia_ 7



2.0


1.5


1.0


0.5


0.0


0.5


3


2


1


0


1



~~N~~ GC3351
NGC5457
NGC3627
NGC5194


0 1 2 3
log [M pc 2 ]


~~N~~ GC3351
NGC5457
NGC3627
NGC5194


0 1 2 3
log [M pc 2 ]



~~N~~ GC0628
NGC3184
NGC5055
NGC6946


0 1 2 3
log [M pc 2 ]


~~N~~ GC0628
NGC3184
NGC5055
NGC6946


0 1 2 3
log [M pc 2 ]



Unweighted median
Weighted median
16 [th] & 84 [th] percentile


0 1 2 3
log [M pc 2 ]


Unweighted median
Weighted median
16 [th] & 84 [th] percentile


0 1 2 3
log [M pc 2 ]



~~U~~ nweighted
Weighted


0 2

PDF


~~U~~ nweighted
Weighted


1.9
2.1


0.0 0.5

PDF



**Figure 2.** Resolved Σ H I – and Σ mol – Σ _⋆_ relations for HERACLES control galaxies. Lef two panels: The combined rH I SM relation (top) and rMGSM (bottom)
are shown with grey points in the background, the median relation in bins of log Σ _⋆_ for each galaxy is shown with thick, coloured lines, and the 16 [th] – 84 [th]

percentiles are shaded in the same colour, which matches the coloured name of each galaxy in the top lef corner. Galaxies are coloured from red through to
black increasing integrated molecular gas mass and alternate between panels for better visual separation. Third panel: The combined rH I SM relation (top)
and rMGSM (bottom) are shown with grey points in the background, overlaid are the medians (solid lines) and 16 [th] –84 [th] percentiles (dashed lines) treating all
points equally (unweighted, blue) andeach galaxy equally (weighted, red). The rightmost panels show the density-normalised histograms for theunweighted
and weighted treatments. _The key message of this Figure_ is that galaxies lie along well-defined, individual sequences within the rH I SM and rMGSM relations.
As the location of an individual sequence is best described by global galaxy properties, we choose to weight each galaxy equally. HERACLES galaxies do not
show a large difference between the weighted and unweighted statistics, as they are restricted to the star-forming regime.



detected spaxels in both samples exist preferentially at lower Σ _⋆_,
although the typical Σ _⋆_ of VERTICO non-detected spaxels is
larger than HERACLES.
The clearest difference, however, is that the VERTICO
contours extend to lower Σ mol at all Σ _⋆_, and this is true even at
higher Σ _⋆_ where all Σ mol are above the detection limit. This
difference is also visible in the VERTICO Σ mol histogram,
which extends to lower Σ mol . Quantitatively, the median detected VERTICO spaxel has log ( Σ mol /M _⊙_ pc [–2] ) = 0.73, lower
than the HERACLES value of log ( Σ mol /M _⊙_ pc [–2] ) = 0.85, and
we can exclude that the distributions are drawn from the same
parent sample ( _p_ < 10 [–4] ). Some of these differences will be due
to the shallower HERACLES detection limit (causing more
non-detections at lower Σ _⋆_ ) and the smaller spatial coverage of
VERTICO galaxies with smaller H I discs (causing an undersampling of lower Σ _⋆_ ). However, they also suggest that the



molecular gas is being lost preferentially at lower Σ _⋆_ (at least
to our detection threshold), while the remaining, detectable
molecular gas has lower surface density. However, the magnitude of these effects appears to be much smaller, and the
affected region(s) are less well defined compared to the rH ISM
relation.

How, then, do we extract the comparatively weaker signal (if any) of the impact of environmental processes on the
rMGSM relation? Using a sample of galaxies from the ALMaQUEST survey (ALMA-MaNGA QUEnching and STar
Formation, Lin et al., 2020) with similar _M_ _⋆_ and SFR ranges
to our VERTICO sample, Ellison et al. (2021a,b) showed that,
to first order, the scatter within the rMGSM relation is not
determined by the properties of individual spaxels. Instead,
galaxies form well-defined individual sequences in the parameter space, and their scatter from the median relation is best

8 Adam B. Watts _et al._


def-HI



1.5 -0.30 NGC4651 1.5



1.5 -0.10 NGC4254 1.5



1.5 0.12 NGC4654 1.5



1.5 0.13 NGC4567



1.0


0.5


0.0


0.5

0 1 2 3



0 1 2 3



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



0 1 2 3



0 1 2 3



1.5 0.41 NGC4535



1.5 0.41 NGC4298 1.5



1.5


1.0


0.5


0.0



0.35 NGC4321 1.5



1.5 0.38 NGC4568 1.5



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



0.5

0 1 2 3



1.0


0.5


0.0


0.5



0 1 2 3



0 1 2 3



0 1 2 3



1.5 0.58 NGC4501 1.5



1.5 0.62 NGC4394 1.5



1.5 0.68 NGC4689 1.5



1.5 0.82 NGC4548



1.0


0.5


0.0


0.5

0 1 2 3



0 1 2 3



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



0 1 2 3



0 1 2 3



1.5 1.13 NGC4380 1.5



1.5 1.17 NGC4450



1.5


1.0


0.5


0.0



0.92 NGC4457 1.5



1.5 0.95 NGC4579 1.5



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



0.5

0 1 2 3



1.0


0.5


0.0


0.5



0 1 2 3



0 1 2 3
log [M pc 2 ]


HERACLES median


16 [th] -84 [th] percentile



0.0


0.5


1.0


1.5


2.0



1.5 1.47 NGC4569 1.5 2.25 NGC4293



0 1 2 3
log [M pc 2 ]


VERTICO


HI [ non-detection]



1.0


0.5


0.0


0.5



1.0


0.5


0.0


0.5



0 1 2 3
log [M pc 2 ]



0 1 2 3
log [M pc 2 ]



Median & 16 [th] -84 [th] percentile

R HI : log HI



**Figure 3.** Individual rH I SM relations for VERTICO galaxies, with the galaxy name given in the top-right of each panel. The panels are ordered in rows by def-H I
(noted in the top-lef corner), which also sets the colour of each panel, and a colour bar is displayed on the right-hand side. Solid points indicate detected
spaxels, while downward triangles at log ( Σ H I /M _⊙_ pc [–2] ) = –0.5 indicate non-detections. The median rH I SM for each galaxy computed in 0.25 dex Σ _⋆_ bins
is shown with large white markers, where downward triangles indicate the median is a non-detection, and error bars show the 16 [th] and 84 [th] percentiles
of the log Σ H I distribution in each bin. The HERACLES control sample is shown with thick (median) and thin (16 [th] and 84 [th] percentiles), and the vertical
dashed, coloured lines show _⟨_ log Σ _⋆_ _⟩_ H I, the average log Σ _⋆_ at the H I truncation radius ( _R_ H I ). The two galaxies marked with stars are interacting, and their
H I observations are partially confused. The impact of the Virgo cluster on the rH I SM relation is two-fold. As def-H I increases there are more non-detected
spaxels and _⟨_ log Σ _⋆_ _⟩_ H I moves to larger values; and there is an increasing reduction of the typical Σ H I within _⟨_ log Σ _⋆_ _⟩_ H I .



described with global galaxy properties (e.g., the location of
an individual rMGSM is best described by specific SFR, Ellison
et al., 2021a). We show these individual sequences for both
the rH ISM and rMGSM relations of our HERACLES control
sample in the left panel of Fig. 2, ordered from red to black
by increasing total molecular gas mass. The distribution of
HERACLES points is shown in the background, with the median relation (thick coloured lines) and 16 [th] – 84 [th] percentiles
(coloured, shaded regions) for each galaxy in bins of log Σ _⋆_
overlaid. Clearly, the galaxy-galaxy variation is larger than
the scatter within individual objects, and this is particularly
evident in the higher Σ _⋆_ regions of the rH ISM relation, where
galaxies might have a central H I depression.


As the VERTICO sample contains both H I-normal and
H I-deficient galaxies, combining the entire sample into one



relation acts to wash out the signature of environmental effects, particularly in the molecular gas. Thus, to understand
how environmental processes impact the resolved properties
of galaxies, we need to control for their global properties. Further, we must also ensure that any histograms and statistics
we compute are not biased toward larger galaxies and galaxies that are less affected by the environment, as these systems
contain more spaxels. To do this, whenever we compute a
histogram such as log Σ H I or log Σ mol we weight each spaxel
by 1/( _N_ sp _N_ G ), where _N_ sp is the number of spaxels contributed
by it’s host galaxy and _N_ G the number of contributing galaxies.
Under this definition, the sum of the weights is always 1, and
it ensures that each galaxy contributes to the histogram (and
any subsequently computed statistics) equally. All statistics
presented in this paper from now on are weighted values.

_Publications of the Astronomical Society of Australia_ 9


**Table 2.** Weighted median log Σ H I (Fig. 4) and log Σ mol (Fig. 7) for the control sample, and the moderate and large def-H I samples, in bins of log Σ _⋆_ . The
Σ _⋆_ range used to select spaxels are given in the first column, the second to fourth columns use all spaxels, while the remaining columns use only detected
spaxels for each gas phase. Uncertainties are calculated with bootstrap re-sampling using 10 [4] iterations where entire galaxies are selected in each subsample
to maintain equal weighting.


median log Σ H I median detected log Σ H I

log Σ _⋆_ bin [ M _⊙_ pc [–2] ] Control def-H I= [0.3, 0.7) def-H I _≥_ 0.7 Control def-H I= [0.3, 0.7) def-H I _≥_ 0.7

[0, 0.75) 0.75 _±_ 0.35 –0.50 [a] _±_ 0.45 –0.50 [a] _±_ 0.00 0.75 _±_ 0.12 –0.08 _±_ 0.32         
[0.75, 1.25) 0.83 _±_ 0.09 –0.50 [a] _±_ 0.41 –0.50 [a] _±_ 0.00 0.83 _±_ 0.05 0.20 _±_ 0.16 0.03 _±_ 0.00

[1.25, 1.75) 0.95 _±_ 0.05 0.33 _±_ 0.15 –0.50 [a] _±_ 0.01 0.95 _±_ 0.05 0.39 _±_ 0.12 0.10 _±_ 0.08

[1.75, 2.25) 0.95 _±_ 0.06 0.56 _±_ 0.06 –0.14 _±_ 0.26 0.95 _±_ 0.06 0.57 _±_ 0.06 0.22 _±_ 0.05


_≥_ 2.25 0.85 _±_ 0.10 0.49 _±_ 0.15 –0.50 [a] _±_ 0.31 0.85 _±_ 0.10 0.51 _±_ 0.07 0.32 _±_ 0.06


median log Σ mol median detected log Σ mol

log Σ _⋆_ bin [ M _⊙_ pc [–2] ] Control def-H I= [0.3, 0.7) def-H I _≥_ 0.7 Control def-H I= [0.3, 0.7) def-H I _≥_ 0.7

[1.25, 1.75) 0.45 _±_ 0.15 0.39 [b] _±_ 0.17 –0.50 [a] _±_ 0.26 0.65 _±_ 0.05 0.47 _±_ 0.10 0.12 _±_ 0.16

[1.75, 2.25) 1.04 _±_ 0.05 0.92 [b] _±_ 0.07 0.41 _±_ 0.15 1.04 _±_ 0.06 0.92 [b] _±_ 0.06 0.45 _±_ 0.09

_≥_ 2.25 1.33 _±_ 0.11 1.45 [b] _±_ 0.12 1.00 _±_ 0.11 1.34 _±_ 0.11 1.45 [b] _±_ 0.10 1.00 _±_ 0.11


a Median is a non-detection b Median consistent with control sample within uncertainty



In the middle panels of Fig. 2 we compare the weighted
(red) and unweighted (blue) median (solid line), and 16 [th] and
84 [th] percentiles (dashed lines) [g], of the rH ISM relation and
rMGSM relation for the HERACLES control sample. The
rightmost panels show the weighted and unweighted histograms of log Σ H I and log Σ mol across all Σ _⋆_ . The advantage of this weighting is clear in Σ mol at log ( Σ _⋆_ /M _⊙_ pc [–2] ) ≲
1.5, where the HERACLES data begin to reach their detection threshold. While the unweighted statistics become nondetections, the weighted statistics better trace the relation as
the typical galaxy is still detected. However, to avoid biasing
our statistics, we will restrict some of our quantitative Σ mol
comparisons to log ( Σ _⋆_ /M _⊙_ pc [–2] ) _≥_ 1.25, as this is the typical Σ _⋆_ where the HERACLES galaxies transition to being
dominated by non-detections. At these higher Σ _⋆_, and at all
Σ _⋆_ for Σ H I, there are negligible differences between the two
weighting methods. This is expected as our control sample is
defined to be star-forming systems, which exhibit less galaxyto-galaxy variation in their spatially resolved cold gas scaling
relations (Ellison et al., 2021a). As we see below, this variation
is much larger for VERTICO galaxies.


**4.** **Impact of environment on the spatially resolved cold**
**gas properties of galaxies**
Environmental effects on the H I content of galaxies are a wellstudied topic, though many previous works have focused on
the gas at large radii due to the extended nature of H I. In §4.1,
we present an analysis of the H I content in the central regions
of galaxies using the framework of the spatially resolved scaling relations. Not only does this present a new view of how
environmental processes impact the resolved H I content of


g For _N_ data points _x_ _i_ with weights _w_ _i_, the weighted percentile _p_ is the data
point _x_ _j_ for which the cumulative sum of the weights of the ascending-sorted

_x_ _i_ is equal to _p_ . i.e., [�] _[j]_ _i_ _[w]_ _[i]_ _[≤]_ _[p]_ [ and] [ �] _[N]_ _j_ _[w]_ _[i]_ _[≤]_ [(1 –] _[ p]_ [).] [To compute the median,]
_p_ = 0.5.



galaxies, but it is also useful to outline the visualisations and
techniques that we apply to the molecular gas in §4.2.


_**4.1**_ _**Atomic hydrogen**_
In Fig. 3, we present the rH ISM relations of VERTICO galaxies in individual panels. H I-detected spaxels are shown with
coloured points and non-detections with downward triangles.
The median log Σ H I in 0.25 dex bins of Σ _⋆_ (which are combined with adjacent bins if they contain less than 10 points) is
shown with white, bordered symbols, where a circle denotes
a median detection and a downward triangle denotes that the
median is a non-detection. The median (thick, grey line) and
16 [th] and 84 [th] percentiles (thin, grey lines) of the HERACLES
control sample are shown in the background, and the average log Σ _⋆_ measured at _R_ H I ( _⟨_ log Σ _⋆_ _⟩_ H I, as calculated in §2.1)
is shown with a vertical dashed line. Panels are ordered in
rows from left to right by increasing def-H I (the numerical
value is displayed in the top left of each panel, in-line with
the galaxy name), which also determines the colour of the
individual points (with a colour bar on the right). Fig. 3 is rich
in physical information, and we dissect this in the following
analysis.
We first focus on the top row, which contains VERTICO
galaxies considered to be H I-normal based on their def-H I
(–0.3 < def-H I [dex] < 0.3). Three galaxies are consistent with
the HERACLES control sample, while NGC 4567 appears to
be a slight outlier, particularly at lower Σ _⋆_ . NGC 4567 is interacting with NGC 4568 (row 2, column 2) and the galaxies
cannot be separated in velocity space (Chung et al., 2009),
causing an overlap of the rH ISM relation of each galaxy and
meaning that it has experienced some environmental mechanisms.
The rH ISM relations of individual galaxies show two clear
trends as a function of increasing def-H I that occur distinctly
at lower and higher Σ _⋆_ . First, the value of _⟨_ log Σ _⋆_ _⟩_ H I (measuring _R_ H I, vertical dashed lines), on average, increases with

10 Adam B. Watts _et al._



increasing def-H I. In other words, the H I is stripped (at least to
our sensitivity limit) to smaller radii within the disc as def-H I
increases. Second, inside _R_ H I, the individual rH ISM relations
increasingly fall below the median and then the 16 [th] (lower)
percentile of the HERACLES control sample at fixed Σ _⋆_ . That
is, there is an increasing reduction of the typical Σ H I within
the _R_ H I of galaxies as def-H I increases. This effect is largest in
the highest def-H I systems, but several moderate def-H I galaxies also begin to show evidence for this reduction (NGC 4321,
NGC 4501, NGC 4535). These trends show that the impact
of environmental processes on the H I is two-fold: not only
is the H I stripped from the outskirts, but the typical surface
density of the remaining gas is also reduced. Additionally, we
observe no evidence for an environment-driven enhancement
of Σ H I, at least at the 1.2-kpc spatial scale that we trace.
To quantify these effects, and because this is a complex
parameter space, we use two different strategies for computing and comparing log Σ H I histograms of VERTICO galaxies to the control sample. In all comparisons, we split the
VERTICO galaxies into two bins of global def-H I [h], def-H I
= [0.3, 0.7) dex and def-H I _≥_ 0.7 dex, which we refer to
these as the ‘moderate’ and ‘large’ def-H I samples, respectively.
These thresholds were defined as approximately 1 and 2 times
the scatter in the def-H I of isolated galaxies ( σ =0.3 dex), with
a slight adjustment to ensure an equal number of galaxies in
each sample. Histograms are computed by weighting each
galaxy equally (see §3), and we also computed weighted medians for each def-H I sample and the control sample, which are
presented in Table 2.
In our first comparison, shown in Fig. 4, we divide the
rH ISM relation into 0.5 dex bins of log Σ _⋆_ and compute the
histogram of log Σ H I in each bin. The control sample is shown
as a grey, solid histogram, the moderate def-H I population as
a blue, open histogram, and the large def-H I as a red, open
histogram. All H I non-detected spaxels are included in the bin
located at log ( Σ H I /M _⊙_ pc [–2] ) = –0.5, and if the value of this
bin exceeds the figure limits, its value is written in the top left.
Fig. 4 again highlights the trends seen in Fig. 3. First, both
def-H I samples show a larger fraction of non-detected H I spaxels than the control sample, and the fraction of non-detected
spaxels is higher in the larger def-H I galaxies. Namely, the radius at which H I is below the detection limit gets closer to the
galaxy centre as def-H I increases. This increased fraction of
non-detections is also evident in Table 2, where the weighted
median for detections only is often different to the value for all
points in both def-H I samples. Second, at all Σ _⋆_, the typical
detected Σ H I is also lower as def-H I increases. Table 2 shows
that the moderate def-H I sample has a weighted median for
detected Σ H I spaxels that is 0.34 – 0.83 dex lower than the
control sample, while it is 0.53 – 0.85 dex lower for the large
def-H I sample, and these differences are greater than the estimated uncertainties. Last, neither def-H I sample shows higher


h As mentioned in §2.1, our def-H I bins are wide enough to fully encapsulate any small, second-order correlation of Σ H I and def-H I due to the
variation of Σ H I profiles in galaxies, guaranteeing that our analysis is tracing
environmentally-related processes.



5


4


3


2


1







5


4


3


2


1







5


4


3


2


1







5


4


3


2


1







5


4


3


2


1


0



|100<br>.<br>73<br>.|Col2|log =[000075)<br>., .<br>control<br>def -HI=[0 .3,0 .7)<br>def -HI 0 .7|
|---|---|---|
|7.3<br>~~1~~0.0|||
|0<br>5.7<br>~~9~~.9|.5|0.0<br>0.5<br>1.0<br>1.5<br>log<br>=[0.75,1.25)|
|0<br>5.7<br>~~9~~.9|||
|0<br>~~8~~.4|.5|0.0<br>0.5<br>1.0<br>1.5<br>log<br>=[1.25,1.75)|
|0<br>~~8~~.4|||
|0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>log<br>=[1.75,2.25)|0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>log<br>=[1.75,2.25)|0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>log<br>=[1.75,2.25)|
|0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>log<br>=[1.75,2.25)|||
|0<br>~~5~~.7|.5|0.0<br>0.5<br>1.0<br>1.5<br>log<br>2.25|
|0<br>~~5~~.7|||


0.5 0.0 0.5 1.0 1.5
log HI [ [M] pc 2 ]



**Figure 4.** log Σ H I histograms in bins of log Σ _⋆_ . Each panel shows densitynormalised histograms of log Σ H I for spaxels in the Σ _⋆_ range quoted in the
top right corner. HERACLES control sample galaxies are shown with a grey,
filled histogram, VERTICO moderate def-H I galaxies with a blue, open histogram, and large def-H I galaxies with a red, open histogram. Non-detected
spaxels are included in the bin centered at log ( Σ H I /M _⊙_ pc [–2] ) = –0.5, and if
the value of this bin exceeds the y-axis limit then its value is quoted in the
top-lefofthepanelinthesamecolourasitshistogram. Atfixed Σ _⋆_, galaxies
with larger def-H I have a higher fraction of non-detected spaxels and their
detected spaxels have lower Σ H I . The difference is larger at lower Σ _⋆_ .

_Publications of the Astronomical Society of Australia_ 11



Σ H I than the control sample, highlighting that we observe no
environment-driven enhancement of Σ H I .
We note that there is some overlap between the 1 σ scatter
in the Σ H I distributions. For example, in the highest Σ _⋆_ bin
the 16 [th] percentile of the control sample (0.42) is smaller than
the 84 [th] percentiles of both the moderate (0.73) and large
(0.49) def-H I samples. As we do not expect environmental
mechanisms to operate across the whole gas disc with the same
magnitude (e.g., the centre or the trailing edge will be less
affected), some overlap between the distributions is expected.
Nevertheless, in all Σ _⋆_ bins we find that the two distributions
cannot be drawn from the same sample [i] ( _p_ < 10 [–4] ), confirming
that we are witnessing the effect of environmental processes
already in the moderate def-H I regime.
Considering the K-S test results, Fig. 4 also contains interesting insights into how environmental processes change the
distribution of Σ H I in the remaining gas. While the bins with
log ( Σ _⋆_ /M _⊙_ pc [–2] ) < 1.25 are dominated by non-detections, in
the higher log Σ _⋆_ bins, the log Σ H I histogram of the moderate
def-H I galaxies (blue) is similar to the control sample. Namely,
there is a peak at higher Σ H I and a tail toward lower surface
densities. The main difference is a decrease in the average
Σ H I, while the increase in non-detections comes from the
low surface density tail falling below the detection limit. The
large def-H I galaxies show a larger decrease in Σ H I values,
but also, the shape of the log Σ H I histogram becomes more
gaussian rather than skewed. This change in shape suggests
that in addition to the decrease in the typical surface density,
the densest H I regions are no longer present.
In our second comparison, we consider only H I within the
_R_ H I of each galaxy. For both def-H I samples, we used all spaxels with log Σ _⋆_ _≥⟨_ log Σ _⋆_ _⟩_ H I to compute equally-weighted
density-normalised log Σ H I histograms. Achieving a fair comparison with the control sample required an extra step, however, as the _⟨_ log Σ _⋆_ _⟩_ H I of each galaxy is different. For each
VERTICO galaxy, we computed a unique, equally-weighted
control sample histogram using all spaxels from each control
galaxy with log Σ _⋆_ _≥⟨_ log Σ _⋆_ _⟩_ H I . The control histograms for
each galaxy in a given def-H I sample were then stacked and
re-normalised using the same procedure [j] . This dependence
on _⟨_ log Σ _⋆_ _⟩_ H I results in slightly different control samples for
each def-H I sample [k] and is visible when comparing the grey
histograms in the two panels of Fig. 5. Weighted medians for
these histograms are listed in Table 3.
In Fig. 5, we compare histograms of log Σ H I for spaxels
within _R_ H I between the control sample (grey, solid), the moderate def-H I sample (top panel, blue) and large def-H I sample


i As we are using weighted data, we used a weighted K-S test, and our
[implementation can be found here.](https://github.com/awattsup/astro-functions/blob/d340fb20301294671c5eaa0857e613c59945f239/astro_functions.py#L430)
j This was done by introducing an additional factor of 1/ _D_ to the weight
for each spaxel in each unique control sample histogram, where _D_ is the
number of galaxies in the def-H I sample.
k We tested a different approach of combining all spaxels from the control
galaxies and found the same results for the H I using this method. This is
because Σ H I is essentially flat with Σ _⋆_, so there is little dependence on the Σ _⋆_
range covered. The same is not true for the molecular gas, so for consistency,
we use the same approach for both gas phases.



**Figure** **5.** Histograms of log Σ H I within the _R_ H I of galaxies. We compare density-normalised histograms of log Σ H I for spaxels with log Σ _⋆_ _≥_
_⟨_ log Σ _⋆_ _⟩_ H I for galaxies with moderate def-H I (top panel; blue, open histogram) and large def-H I (bottom panel; red, open histogram) to their
matched HERACLES control samples (both panels, grey filled histogram). As
def-H I increases, the fraction of non-detected spaxels within _R_ H I increases,
and the typical detected Σ H I is lower. In galaxies with the largest def-H I
the histogram of detected log Σ H I is gaussian, rather than skewed, indicating that the densest H I is no longer present. Neither def-H I sample shows
evidence for elevated Σ H I compared to the control sample.


(bottom panel, red). Here, we can see the impact of environmental processes on the remaining H I gas that has not been
removed. The moderate def-H I galaxies have median detected
log ( Σ H I /M _⊙_ pc [–2] ) = 0.52 _±_ 0.07, while their matched control
sample has log ( Σ H I /M _⊙_ pc [–2] ) = 0.95 _±_ 0.02, indicating that
the typical Σ H I is 0.43 dex lower (Table 3). The difference
is larger in the large def-H I galaxies, which have a median
log ( Σ H I /M _⊙_ pc [–2] ) = 0.28 _±_ 0.06 that is 0.66 dex lower than the
median of their matched control sample, log ( Σ H I /M _⊙_ pc [–2] ) =
0.94 _±_ 0.02. We also see the same changes in the shape of the
Σ H I histogram described above in Fig. 4, and we can rule out
the control and def-H I samples being drawn from the same
parent distribution ( _p_ < 10 [–4] ). Thus, when considering the
remaining gas inside _R_ H I, environmental processes typically
lower the average Σ H I of moderate def-H I galaxies, while
large def-H I galaxies can no longer support the densest H I

gas.
Our results so far have provided a unique view of how
environmental mechanisms impact the resolved H I content
of galaxies, and agree with results from previous studies (e.g.
Vollmer et al., 2001; Tonnesen & Bryan, 2009; Chung et al.,
2009; Yoon et al., 2017; Cortese et al., 2021; Boselli et al., 2022;
Lee et al., 2022). However, how these mechanisms impact



3


2


1







3


2


1


0



0.5 0.0 0.5 1.0 1.5
log HI [ [M] pc 2 ]

12 Adam B. Watts _et al._


**Table 3.** Weighted median log Σ H I (Fig. 5) and log Σ mol (Fig. 8) within _R_ H I for the moderate and large def-H I samples, and their matched control samples.
As the control sample histogram is constructed by selecting spaxels with log Σ _⋆_ _≥⟨_ log Σ _⋆_ _⟩_ H I in each galaxy, the two def-H I samples have unique control
samples, and thus unique weighted control sample medians. The first column gives the def-H I sample, the second and third columns the control sample and
def-H I sample medians using all spaxels, and the remaining columns use detected spaxels only. Uncertainties are calculated using jackknife re-sampling and
rejecting an entire galaxy in each iteration.


Sample Control median log Σ H I Sample median log Σ H I Control median detected log Σ H I Sample median detected log Σ H I


def-H I= [0.3, 0.7) 0.95 _±_ 0.02 0.50 _±_ 0.07 0.95 _±_ 0.02 0.52 _±_ 0.07


def-H I _≥_ 0.7 0.94 _±_ 0.02 0.19 _±_ 0.14 0.94 _±_ 0.02 0.28 _±_ 0.06


Sample Control median log Σ mol Sample median log Σ mol Control median detected log Σ mol Sample median detected log Σ mol

def-H I= [0.3, 0.7) 0.88 _±_ 0.03 0.77 _±_ 0.08 0.95 _±_ 0.02 0.80 _±_ 0.07


def-H I _≥_ 0.7 1.15 _±_ 0.04 0.70 _±_ 0.09 1.16 _±_ 0.04 0.71 _±_ 0.09



the molecular gas in galaxies on these spatial scales has so far
remained unquantified, and is discussed next.


_**4.2**_ _**Molecular hydrogen**_
In Fig. 6, we present the individual rMGSM relations of VERTICO galaxies in the same way as the rH ISM relations. Focusing first on the top row of H I-normal galaxies, aside from
NGC 4567 (interacting, as discussed in §4.1), NGC 4651 seems
to be molecule-poor for an H I-normal galaxy. The kinematic
position angles of the H I inside and outside the optical disc of
NGC 4651 are different (Chung et al., 2009), and it has stellar
and H I tidal features (Chung et al., 2009; Martínez-Delgado
et al., 2010; Morales et al., 2018), suggesting that much of its
H I disc could have been recently accreted. Thus, the molecular gas content likely does not reflect that of an H I-normal
galaxy. NGC 4254 appears slightly molecule-rich at fixed Σ _⋆_ .
There is evidence that it recently underwent a fly-by interaction (Vollmer et al., 2005; Haynes et al., 2007; Boselli et al.,
2018b), and it has a molecular bar and asymmetric spiral arms
containing dense molecular gas (Sofue et al., 2003). These
differences between the control sample and NGC 4651 and
NGC 4254 highlight how environmental mechanisms can
influence galaxies before they become significantly H I-poor,
and the importance of selecting a control sample from field
galaxies.
Before dissecting Fig. 6, it is useful to point out some
interesting features. First, the median rMGSM relation of four
galaxies (NGC 4298, NGC 4689, NGC 4457, NGC 4450)
transition from detections to non-detections coincidently with
_R_ H I, _⟨_ log Σ _⋆_ _⟩_ H I, indicating that these galaxies show co-spatial
H I and molecular gas truncation. Second, several galaxies
show changes in the slope of their rMGSM relation. Some
of these changes are close to _R_ H I and are likely the signature
of the environment (e.g. NGC 4298, NGC 4689). Other
galaxies show changes in their more central regions, such as
the superposition of two slopes in NGC 4535, a flattening
and then upturn in NGC 4548, or the zig-zag structure of
NGC 4579. These are not solely due to changes in the Σ mol
content but also reflect changes in the central stellar structure
of galaxies. NGC 4535 and NGC 4548 are barred with central
bulges, causing a steeper Σ _⋆_ – Σ mol relation in their centres
and bar regions and a flatter relation in the disc. NGC 4579
has a bar and a ring, causing an alternation between elevated



Σ mol and Σ _⋆_ in the centre, lowered Σ mol in a higher Σ _⋆_ region
between the centre and the ring, and higher Σ mol in a lower
Σ _⋆_ region in the ring and disc. Beyond having interesting
effects on the shape of the rMGSM relation, this suggests that
we must use caution when comparing Σ mol properties at fixed
Σ _⋆_, particularly in the ranges where stellar structures could be
important.
Comparing the rMGSM relations of VERTICO galaxies to
the control sample, there is less difference as a function of defH I than was visible for the rH ISM relation. In the second and
third rows, namely at moderate def-H I, the rMGSM relations
of individual galaxies typically agree well with the median of
the control sample, though there are some small signatures of
deviation near _R_ H I in some galaxies. Instead, it is primarily
the largest def-H I systems (the bottom two rows) where the
individual rMGSM relations begin to deviate below the control
sample median and occasionally below the 16 [th] percentile, at
fixed Σ _⋆_ . These differences are largest at lower Σ mol and closer
to _R_ H I, though there is galaxy-galaxy variation and at high
Σ _⋆_ some galaxies are consistent with the control sample (e.g.
NGC 4457, NGC 4569), while others show reduced Σ mol (e.g.
NGC 4380, NGC 4450).
These results imply that the Σ mol at lower Σ _⋆_ (outer parts
of the disc) is more strongly impacted than at higher Σ _⋆_ (the
inner regions). Further, as Σ mol is typically lower at lower Σ _⋆_,
the environmental processes preferentially impact the lower
surface density molecular gas within galaxies. Interestingly,
this can begin even at moderate def-H I (e.g. NGC 4298 and
its Σ mol slope-change and Σ mol truncation) and effectively
changes the slope of the individual rMGSM relations, making
them steeper. These results agree with previous studies, which
found steeper radial profiles of Σ mol in galaxies with more
disturbed H I morphology and larger def-H I (Fumagalli et al.,
2009; Zabel et al., 2022; Villanueva et al., 2022). Additionally,
like Σ H I we observe no environment-driven elevation of Σ mol
at the spatial scale that we are sensitive to.
In Fig. 7 we compare the log Σ mol histograms of VERTICO galaxies to the control sample in 0.5 dex log Σ _⋆_ bins.
We do not expect stellar structures, as mentioned above, to
cause any biases in these histograms as they are primarily contained in the log ( Σ _⋆_ /M _⊙_ pc [–2] ) _≥_ 2.25 bin. These histograms
reflect the smaller offsets between the individual VERTICO
rMGSM relations and the control sample.

_Publications of the Astronomical Society of Australia_ 13


def-HI



3 3
-0.30 NGC4651



0.12 NGC4654 3


2


1


0


1



2


1


0



-0.10 NGC4254 3


2


1


0


1



1

0 1 2 3



2


1


0


1



0 1 2 3



3


2


1


0



0 1 2 3



0.35 NGC ~~43~~ 21 3


2


1


0



0.41 NGC4298 3


2


1


0


1



1

0 1 2 3



0 1 2 3



1



0.38 NGC4568 3


2


1


0


1



3 0 1 2 3 3
0.58 NGC4501



0 1 2 3



3



0.68 NGC4689 3


2


1


0


1



2


1


0



0.62 NGC4394 3


2


1


0


1



1

0 1 2 3



2


1


0


1



0 1 2 3



3


2


1


0



0 1 2 3



0.92 NGC4457 3


2


1


0



1.13 NGC4380 3


2


1


0


1



0.13 NGC4567


0 0.41 1 2 NGC4535 3


0 0.82 1 2 NGC4548 3


0 1.17 1 2 NGC4450 3


0 1 2 3
log [M pc 2 ]


HERACLES median


16 [th] -84 [th] percentile



0.0


0.5


1.0


1.5


2.0



1

0 1 2 3



1



3 0 1 2 3 3
1.47 NGC4569



3



2


1


0


1



2


1


0


1



0.95 NGC4579 3


2


1


0


1


0 2.25 1 2 NGC4293 3


0 1 2 3
log [M pc 2 ]



0 1 2 3
log [M pc 2 ]


VERTICO


mol [ non-detection]



Median & 16 [th] -84 [th] percentile

R HI : log HI



0 1 2 3
log [M pc 2 ]



**Figure 6.** Individual rMGSM relations for VERTICO galaxies, presented in the same way as Fig. 3. As def-H I increases, the clearest deviation of Σ mol from the
HERACLES control sample occurs at lower Σ _⋆_, typically close to or outside of _R_ H I ( _⟨_ log Σ _⋆_ _⟩_ H I ). Only some of the galaxies with the largest def-H I have reduced
Σ mol at higher Σ _⋆_ and within their _R_ H I (e.g., NGC 4579 NGC 4380, NGC 4450).



Moderate def-H I galaxies (blue) show little differences
from the control sample, except in the lowest Σ _⋆_ bin that has a
significant contribution from non-detections. In this bin, the
relatively larger number of non-detected spaxels in the control
sample is due to the shallower detection limit of HERACLES.
Overall, the main difference between the control sample and
moderate def-H I sample is the presence of a slightly more
extended tail toward lower Σ mol . This tail imprints on the
median detected Σ mol being up to _∼_ 0.18 dex lower than the
control sample, but the distributions peak in similar locations
and in the two higher Σ _⋆_ bins the medians are consistent
within their estimated uncertainties (Table 2). The presence
of this tail, however, is sufficient to rule out the control sample and moderate def-H I sample being drawn from the same
distribution in all Σ _⋆_ bins ( _p_ < 4 _×_ 10 [–4] ).
In the large def-H I sample (red), the impact of environmental processes is stronger. Non-detections dominate the
smallest Σ _⋆_ bin, and despite the VERTICO data being deeper,
the relative number of non-detected spaxels is larger than the
control sample in this bin. Considering the detected spaxels,



the weighted median log Σ mol is 0.34 – 0.59 dex lower than
the control sample across all log Σ _⋆_ bins, all of which are significant considering their uncertainties (Table 2), and we can
exclude that the distributions are drawn from the same parent
sample ( _p_ < 10 [–4] ).
These results support the interpretation that it is primarily
the lower surface density molecular gas at lower Σ _⋆_ that is
affected by the environment, although as galaxies become
significantly H I-deficient ( ≳ 0.7), the impact is larger and can
also affect the gas at higher Σ _⋆_ . Further, in the histograms
of Fig. 7 we see no evidence for any environment-driven
elevation of Σ mol, although in the largest Σ _⋆_ bin the moderate
def-H I sample appears to show slightly higher Σ mol . However,
the medians are consistent within the uncertainties, and this
enhancement disappears if we instead consider spaxels with
log ( Σ _⋆_ /M _⊙_ pc [–2] ) _≥_ 2 or log ( Σ _⋆_ /M _⊙_ pc [–2] ) = [2, 2.5), meaning
that it is due to the slightly different Σ _⋆_ coverage of galaxies
in this bin.
In Fig. 8, we compare the histograms of log Σ mol within
_R_ H I for moderate def-H I galaxies (top, blue) and large def

14 Adam B. Watts _et al._



1.5


1.0


0.5





1.5


1.0


0.5





1.5


1.0


0.5


1.5


1.0


0.5





1.5


1.0


0.5


0.0



1 0 1 2 3
log mol [ [M] pc 2 ]



0.0



1 0 1 2 3
log mol [ [M] pc 2 ]



**Figure 7.** Histograms of log Σ mol in bins of Σ _⋆_, presented in the same way
as Fig. 4. At fixed Σ _⋆_, moderate def-H I galaxies have a similar range of detected Σ mol to HERACLES galaxies, with a slight extension to lower Σ mol,
while large def-H I galaxies show a lower typical Σ mol .


H I galaxies (bottom, red) to their respective control sample
log Σ mol histograms [l] (grey, solid). The Σ mol histogram of
moderate def-H I galaxies is similar to the control sample,
and the median detected Σ mol is 0.15 dex lower (a factor of
_∼_ 1.4, Table 3), which is significant considering the uncertainty. Much like Fig. 7, the main difference is the tail toward
lower Σ mol values, and there is also a reduction of spaxels with
surface densities near the peak of the histogram. The control
sample has slightly more non-detected spaxels due to the shallower detection limit, and we verified that the result remains
if consider only spaxels with log ( Σ _⋆_ /M _⊙_ pc [–2] ) _≥_ 1.5. We also
note that the tail is primarily driven by NGC 4394, which sits
below the control sample rMGSM relation at all Σ _⋆_ . We recomputed the log Σ mol histogram with NGC 4394 excluded
and found that a smaller tail toward lower surface density Σ mol


l As the molecular gas observations of some galaxies do not extend to
_R_ H I (e.g., NGC 4321, NGC 4535), we picked the minimum Σ _⋆_ of each
VERTICO galaxy (used to select control sample spaxels) to be the largest out
of _⟨_ log Σ _⋆_ _⟩_ H I, log ( Σ _⋆_ /M _⊙_ pc [–2] ) = 1.25 (see §3), and the minimum log Σ _⋆_
for the galaxy. In this way, only the observed Σ _⋆_ range is used to compute
the weighted control sample.



**Figure 8.** Histograms of log Σ mol within the _R_ H I of galaxies, presented in
the same way as Fig. 5. Inside the _R_ H I of moderate def-H I galaxies, environmental processes affect primarily the molecular gas with low surface density, while in large def-H I galaxies even the typical Σ mol is reduced.


still remains.
The log Σ mol histogram of the large def-H I galaxies shows
a different behaviour. Unlike the moderate def-H I galaxies,
there is no extended tail of lower Σ mol, but instead, it has a similar shape to the control sample, only shifted to a lower average
Σ mol . The weighted median detected spaxel is 0.45 dex lower
(a factor of 2.8 or 64 per cent) than the control sample and
significant considering the uncertainties (Table 3), reflecting
a larger change, which would be expected in larger def-H I
galaxies. Thus, in the largest def-H I galaxies, environmental
processes act to lower the typical Σ mol within _R_ H I . These
results support the interpretation that at moderate def-H I, the
lower surface density molecular gas within _R_ H I is impacted,
while at large def-H I the typical Σ mol is lowered.
To summarise, _we have presented clear evidence that environ-_
_mental_ _processes_ _impact_ _the_ _molecular_ _gas_ _content_ _of_ _galaxies_ _on_
_1.2-kpc physical scales, even within the H_ I _truncation radius._ The
effect is primarily on the lower surface density molecular gas
and can begin even at moderate def-H I, while in the largest
def-H I systems, the denser molecular gas shows a reduction
in the average molecular gas surface density.


**5.** **Physical drivers of** Σ **mol** **reduction**

The observed reduction of Σ mol at fixed Σ _⋆_ suggests that cluster environmental processes are impacting the molecular gas
in VERTICO galaxies. This reduction could be due to direct
stripping of the molecular gas, similar to the H I (e.g., Moretti

_Publications of the Astronomical Society of Australia_ 15



et al., 2018; Cramer et al., 2020). Alternately, it could result
from inefficient molecule formation caused by a change in the
ISM physical conditions due to the stripping of the H I (e.g.,
Blitz & Rosolowsky, 2006; Krumholz et al., 2009; Fumagalli
et al., 2009). In this case, the suppressed molecular gas content
is due to consumption by star formation and the lack of cold
ISM replenishment (akin to strangulation/starvation). However, for this last scenario to work requires the assumption that
the ISM in a galaxy is able to respond to any changes on a
timescale equal to, or shorter than, the stripping timescale of
the H I ( ≲ 200 Myr; Vollmer et al., 2001; Roediger & Brüggen,
2007; Tonnesen & Bryan, 2009; Choi et al., 2022). Indeed,
this might be expected due to the short lifetimes of GMCs
( ≲ 30 Myr, Chevance et al., 2020b). In this case, VERTICO
galaxies should follow the scaling relations used to interpret
the resolved molecular-to-atomic gas mass ratio ( Σ mol / Σ H I ) in
normal galaxies, which is sensitive to the physical conditions
within the ISM. Instead, we show here that these scaling relations break down when applied to VERTICO galaxies, and
they cannot describe their Σ mol / Σ H I, suggesting that changes
to the ISM physical conditions alone cannot explain the observed reduction of Σ mol .
More detailed modelling of the physical state of the cold
gas reservoir, and its relationship to Σ mol / Σ H I, is outside the
scope of this work and will be investigated in future VERTICO papers. For an analysis of Σ mol / Σ H I across the discs of
VERTICO galaxies using radial profiles, we refer the reader to
Villanueva et al. (2022), who found elevated ratios in galaxies
with perturbed and truncated H I morphologies. Here, we
compare Σ mol / Σ H I in individual spaxels to two parameterisations of the ISM physical conditions to try and understand
what physics might be responsible for the reduction in molecular gas content of the VERTICO galaxies. To be consistent
with previous works, in this section, we correct our H I masses
for a 36 per cent contribution from Helium. Our analysis is
restricted to detected spaxels only, and we also only consider
spaxels with log Σ _⋆_ _≥_ 1.25 so that we only study the ISM
parameterisations where the control sample is dominated by
detected spaxels. We also denote the total cold gas surface
density as Σ gas = Σ H I + Σ mol .
It is also useful to quantify how the removal of H I alone
manifests in the scaling relations that we will investigate. To do
this, we computed the offset between the median log Σ H I of
each VERTICO galaxy and the median of the control sample
at fixed Σ _⋆_ . We then subtracted this offset (as a function of Σ _⋆_ )
from the spaxels of each HERACLES galaxy to create mock
‘H I-stripped’ galaxies. Using these mocks, we re-computed
weighted histograms and statistics to estimate how the HERACLES control sample would shift if it had experienced H I
reduction equal to what is observed for each VERTICO galaxy.
We use these mock galaxies in the following analysis to
show where deviations from the ISM scaling relations can be
explained by H I-only removal, and where we also require
extra reduction of the molecular gas content. Indeed, it is our
ability to perform this kind of spatially resolved analysis that
allows us to identify these small differences, which are on the
order of 0.1–0.2 dex, that would likely be washed out in studies



considering only integrated quantities such as global H I and
molecular gas deficiencies. For conciseness, we only show
individual scaling relations for a subset of VERTICO galaxies
in this section. Individual relations for all VERTICO galaxies,
and the combined VERTICO and HERACLES relations are
shown in Appendix 1.
First, we use a proxy for the hydrostatic pressure at the
midplane of the disc, which was predicted to determine the
molecular gas fraction by Elmegreen (1993, but see also Blitz
& Rosolowsky 2006 and Leroy et al. 2008). We adopt the
prescription from Blitz & Rosolowsky (2006), which we estimate as Σ [0.5] _⋆_ [Σ] [gas] [.] [Σ] _[⋆]_ [and] [ Σ] [gas] [are the dominant terms in the]
Blitz & Rosolowsky (2006) prescription, with the stellar scale
height and gas velocity dispersion having minor contributions.
If this prescription is an accurate predictor of physics determining Σ mol / Σ H I, then we might expect that stripping of the
ISM (predominantly H I) would reduce the pressure and cause
Σ mol / Σ H I to decrease correspondingly.

In Fig. 9, we show Σ mol / Σ H I as a function of Σ [0.5] _⋆_ [Σ] [gas] [for]
two moderate def-H I galaxies (left two panels) and two large
def-H I galaxies (right two panels), presented similarly to Fig. 3
and Fig. 6. We also show, with red lines, how the HERACLES
control sample median would shift if it had experienced H I reduction equal to what is observed for the displayed VERTICO
galaxy. All four VERTICO galaxies have larger Σ mol / Σ H I than
expected at fixed Σ [0.5] _⋆_ [Σ] [gas] [showing that, despite a reduction]
in pressure due to the stripping of the H I, the Σ mol / Σ H I is
_larger_ . Thus, internal hydrostatic pressure cannot explain the
Σ mol / Σ H I ratio in these VERTICO galaxies, suggesting that
stripping of the gas (at least of the H I) is more dominant than
the hydrostatic pressure, at least over the timescale traced by
VERTICO galaxies. Further, there are regions within Fig. 9
where the mock H I-stripped control sample over-estimates the
Σ mol / Σ H I of VERTICO galaxies. This over-estimation is typically larger at lower pressures (corresponding to larger radii)
and in the larger def-H I galaxies, which are the regions and
galaxies where we observed molecular gas reduction in §4.2.
Thus, changes in the hydrostatic pressure plus H I removal
alone cannot explain the observed molecular gas reduction in
these galaxies.

In Fig. 10, we show that the story told by these four galaxies holds for our whole VERTICO sample, using normalised
histograms of log ( Σ mol / Σ H I ) in two bins of log Σ [0.5] _⋆_ [Σ] [gas] [.] [The]
blue and red empty histograms correspond to the moderate
and large def-H I samples, and the solid grey histogram shows
the Σ mol / Σ H I histogram for the control sample. The solid
blue and red histograms show the mock H I-stripped control
samples, matched to the moderate and large def-H I samples
respectively. In both bins, the VERTICO galaxies have elevated Σ mol / Σ H I compared to the HERACLES control sample;
but not so elevated that they match with the histograms of the
mock H I-stripped control samples.

Quantitatively, in the lowest Σ [0.5] _⋆_ [Σ] [gas] [bin, an H I-only re-]
moval scenario would result in Σ mol / Σ H I distributions with
medians of 0.24 _±_ 0.03 dex and 0.65 _±_ 0.03 dex for the moderate and large def-H I populations, which over-estimate their

16 Adam B. Watts _et al._



2


1


0


1



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]









**Figure** **9.** Ratio of molecular-to-atomic gas mass of individual spaxels as a function of the midplane pressure proxy Σ [0.5] _⋆_ [Σ] [gas] [for] [four] [VERTICO] [galaxies,]
coloured and ordered by def-H I . Galaxies are presented in the same format as in Fig. 3 and Fig. 6, with the lef two belonging to the moderate def-H I sample
and the right two to the large def-H I sample. The red lines show how the median and 16 [th] and 84 [th] percentiles of the HERACLES control sample would shif
if it had experienced the same magnitude of H I reduction at fixed Σ _⋆_ as each VERTICO galaxy. At fixed midplane pressure, VERTICO galaxies have a larger
Σ mol / Σ H I than expected for the same pressure in a control sample galaxy. However, this difference is not as large as the H I -only removal scenario, particularly
at lower pressures and larger def-H I .



3


2


1









3


2


1


0



1.5 1.0 0.5 0.0 0.5 1.0 1.5
log mol [/] HI



**Figure 10.** Histograms of log ( Σ mol / Σ H I ) in bins of midplane pressure, presented in the same way as Fig. 4 and Fig. 7. Additionally, solid blue and red
histograms show how the log ( Σ mol / Σ H I ) histogram of the control sample
would move if it had experienced H I removal of equal magnitude as the
moderate and large def-H I samples, respectively. Moderate and large defH I galaxies have systematically larger Σ mol / Σ H I than control sample galaxies at fixed Σ [0.5] _⋆_ [Σ] [gas] [.] [Further, the H] [ I] [-only removal scenario over-estimates]
the observed Σ mol / Σ H I, except in moderate def-H I galaxies in the largest
Σ [0.5] _⋆_ [Σ] [gas] [ bin.]


observed values of 0.09 _±_ 0.07 dex and 0.31 _±_ 0.04 dex by
0.15 dex and 0.34 dex, respectively. In the highest Σ [0.5] _⋆_ [Σ] [gas]
bin, the large def-H I galaxies similarly show 0.2 dex smaller
Σ mol / Σ H I elevation (median 0.61 _±_ 0.04 dex) than expected
from H I removal alone (0.81 _±_ 0.04 dex). A K-S test between
the def-H I samples and their respective mock control sam


ples rules out that they are drawn from the same distribution
( _p_ < 10 [–4] ). Conversely, the moderate def-H I sample in this
bin matches its mock control sample, which is reflected in the
expected and observed Σ mol / Σ H I medians of 0.47 _±_ 0.03 dex
and 0.48 _±_ 0.04 dex, respectively. This match between the
mock control sample and the moderate def-H I sample agrees
with our results in §4.2, where no reduction in Σ mol was observed in these galaxies. Further, we can rule out that the
elevated Σ mol / Σ H I is due to ram pressure providing additional
pressure support and increasing the conversion rate of H I to
molecular gas, as we found no evidence for elevated molecular
gas content in any of our VERTICO galaxies (at least at our
1.2-kpc spatial scale). All these points indicate that some reduction in Σ mol is required to explain the Σ mol / Σ H I of VERTICO
galaxies, but this parameterisation with hydrostatic pressure
alone does not provide a physical explanation.


An alternate scenario based on ISM physics is that, due
to the removal of H I, there is insufficient fuel to form new
molecular gas. We test this hypothesis using the total gas
surface density ( Σ gas ), suggested by Krumholz et al. (2009,
see also Fumagalli et al. 2009) to be the primary regulator of
Σ mol / Σ H I with metallicity and the interstellar radiation field
playing secondary roles. If the stripping of the ISM lowers the
total surface density such that the formation of molecular gas
is inefficient, we would expect VERTICO galaxies to lie along
the same relation between Σ mol / Σ H I and Σ gas as the control
sample, as claimed in Fumagalli et al. (2009). In Fig. 11, we
show Σ mol / Σ H I as a function of Σ gas in the same style as shown
in Fig. 9 for the pressure relation. The displayed moderate (left
two panels) and large (right two panels) def-H I galaxies do
not lie along the same relation as the control sample. Further,
the removal of H I alone would over-estimate the observed
Σ mol / Σ H I at fixed Σ gas, particularly in lower Σ gas regions.

This trend remains for the whole sample, and in Fig. 12,
we show histograms of Σ mol / Σ H I in two bins of log Σ gas in
the same style as Fig. 10. In the lower Σ gas bin, the expected
median Σ mol / Σ H I from H I-only removal scenarios, 0.17 _±_
0.04 dex and 0.63 _±_ 0.04 dex, over-estimate the observed values

_Publications of the Astronomical Society of Australia_ 17



2


1


0


1

















0 1 2

2
log gas [ [M] [pc] ]



0 1 2

2
log gas [ [M] [pc] ]



0 1 2

2
log gas [ [M] [pc] ]



0 1 2

2
log gas [ [M] [pc] ]



**Figure 11.** Ratio of molecular-to-atomic gas mass of individual spaxels as a function of Σ gas for the same galaxies as Fig. 9. The Σ mol / Σ H I of VERTICO galaxies
is systematically larger than in control sample galaxies at fixed Σ gas, but not as large as the H I -only removal scenario shown with the red lines.



3


2


1











3


2


1


0



1.5 1.0 0.5 0.0 0.5 1.0 1.5
log mol [/] HI



**Figure** **12.** Histograms of log ( Σ mol / Σ H I ) in bins of total cold gas surface
density, presented in the same way as Fig. 10. Moderate and large def-H I
galaxieshavesystematicallylarger Σ mol / Σ H I thanexpectedifmoleculargas
formation was set primarily by Σ gas . The H I -only removal scenario overestimates Σ mol / Σ H I, except at large Σ gas in moderate def-H I galaxies.


of 0.05 _±_ 0.07 dex 0.47 _±_ 0.03 dex for the moderate and large defH I samples by 0.12 dex and 0.16 dex respectively. In the higher
Σ gas bin, the elevation in Σ mol / Σ H I of the large def-H I sample
is smaller by 0.11 dex, with an expected median 0.74 _±_ 0.03 dex
compared to 0.63 _±_ 0.04 dex observed, while the moderate
def-H I galaxies agree more closely with their mock control
sample, having 0.38 _±_ 0.03 dex expected and 0.41 _±_ 0.05 dex
observed. We also can exclude that both def-H I samples are
drawn from the same parent distribution as their respective
mock control samples ( _p_ < 10 [–4] ). Thus, in VERTICO galaxies
it is not Σ gas that sets Σ mol / Σ H I, and explaining the observed
Σ mol / Σ H I requires a reduction in their molecular gas content



that is not related to insufficient fuel or an inefficient conversion
of H I into molecular gas.
We must also consider if there are any systematic differences between how molecular gas is traced in VERTICO and
HERACLES. As the data have been homogenised and both use
the same constant _R_ 21 and α CO to convert CO(2-1) luminosity to molecular gas mass, this scenario is unlikely. Although
_R_ 21 and α CO have their own uncertainties, this homogenisation means that our results are actually re-scaled differences
between the observed CO(2-1) emission in our samples. Thus,
to explain the difference between the typical Σ mol inside the
_R_ H I of large def-H I galaxies would require VERTICO galaxies to preferentially have CO(2-1)-dark gas such that the observed CO(2-1) luminosity under-estimates the actual amount
of molecular gas present by a factor of 2.8 (0.45 dex).
Metallicity variations cannot explain a reduction in CO(21) emission, as while at smaller metallicities there is more CO(21) dark gas, cluster galaxies show similar or elevated metallicity
over isolated systems (e.g., Skillman et al., 1996; Gupta et al.,
2018; Franchetto et al., 2020). Changes to the UV radiation
field due to reduction in star formation also are unlikely to
cause any differences in CO(2-1) emission. VERTICO galaxies
show reduced SFR surface densities up to _∼_ 1 dex compared
to star-forming galaxies at fixed Σ _⋆_ (Brown et al., in prep);
however, in the same regions, we observe reduced H I and
molecular gas densities with similar magnitude, which reduces
the gas column’s ability to self-shield. Thus, any changes
in the UV field are likely balanced by changes in the gas
density (Krumholz et al., 2009). VERTICO galaxies also show
similar _R_ 21 values to normal galaxies from xCOLD GASS
(Brown et al., 2021), suggesting that there is no significant
difference in the CO(2-1) excitation that could under-estimate
the amount of molecular gas. Additionally, Smith et al. (2014)
and Glover & Smith (2016) found that CO(2-1)-dark gas is
typically diffuse and low surface density, making it prone to
turbulent compression and gravitational collapse and thus less
likely to exist in the central regions of galaxies that we have
studied.
Further evidence that VERTICO galaxies do not have substantial CO(2-1)-dark gas comes from studies of the KennicuttSchmidt (Schmidt, 1959; Kennicutt, 1998) star formation law.
If the CO(2-1) emission line underestimated the total molecu

18 Adam B. Watts _et al._



lar gas mass, then galaxies would deviate from the KennicuttSchmidt law and appear to have elevated SFR at fixed molecular
gas mass. However, VERTICO galaxies show similar galaxyto-galaxy variation in their resolved Kennicutt-Schmidt relations to what is observed in star-forming galaxies (Vollmer
et al., 2012; Jiménez-Donaire et al., 2022). This consistency
with unperturbed systems implies that the physics of star formation, and by extension the ISM physical conditions giving
rise to the CO(2-1) emission, do not show sufficient difference
between VERTICO galaxies and the control sample to explain
our results. Thus, we need to invoke a process that is unrelated
to the ISM physical conditions and can reduce molecular gas
content on timescales similar to the H I gas. Direct stripping
of the molecular gas meets this requirement.


There is evidence that not all molecular gas in galaxies
resides in bound GMCs, with 20 – 50 per cent (Polk et al.,
1988; Wilson & Walker, 1994; Pety et al., 2013; Roman-Duval
et al., 2016; Chevance et al., 2020a; Saintonge & Catinella,
2022) existing in a more diffuse phase or a molecular thick disc
that has velocity dispersion similar to the H I (e.g. Caldú-Primo
et al., 2013, 2015; Mogotsi et al., 2016), making it much easier
to strip than GMC gas. Our data cannot differentiate between
diffuse and dense gas; however, the 64 per cent reduction (§4.2)
in the typical molecular gas content within _R_ H I observed in
our large def-H I galaxies is greater than the ‘typical’ diffuse
gas fractions mentioned above. This is interesting, as there is
also evidence that GMCs can be disrupted by the ICM. Cramer
et al. (2020) found that only 12 per cent of the molecular gas
on the leading edge of NGC 4402 exists in GMCs that have
the survived the ongoing stripping, while the remaining gas
exists in a trailing plume with lower surface density. The
authors suggest that this large fraction of lower surface density
molecular gas implies that an indirect stripping process, by
which GMCs are converted to lower surface density molecular
gas or H I before being directly stripped, could be taking place.


This interpretation is also supported by simulations, which
have shown that the multi-phase structure of the ISM allows
stripping to affect gas within the truncation radius (e.g., Quilis
et al., 2000; Tonnesen & Bryan, 2009). Further, momentumtransfer from the ICM to the ISM through turbulent mixing
can effectively ablate the dense, cold ISM into warmer phases
(e.g., Gronke & Oh, 2018; Sparre et al., 2019) and accelerate
it out of the galaxy (Tonnesen & Bryan, 2021; Choi et al.,
2022). The typical ICM pressures expected for Virgo galaxies
are within the ranges used in these simulations (e.g., Vollmer
et al., 2001; Roediger & Brüggen, 2007; Chung et al., 2007;
Abramson et al., 2011), making stripping of the molecular gas
the most feasible explanation for our observed molecular gas
reduction. However, future work with higher spatial resolution observations is needed to allow quantification of how the
diffuse and dense phases of the ISM are impacted by the Virgo
environment, and search for signatures of direct stripping of
the molecular gas.



**6.** **Summary**
In this paper, we used spatially resolved scaling relations between Σ _⋆_, Σ H I, and Σ mol to study how cluster environmental
processes impact the cold gas content within the optical extent
of massive ( log ( _M_ _⋆_ /M _⊙_ ) _≥_ 10) galaxies on 1.2-kpc scales. We
presented a new view of how the H I gas distribution changes
with increasing H I deficiency, and we have shown, statistically,
how environmental processes impact the spatial distribution of
the molecular gas, the distribution of Σ mol, and molecular-toatomic gas mass ratio using observations from the VERTICO
survey (Brown et al., 2021). Our main results are as follows:


 - While the stripping of gas from galaxies impacts the H I
gas at large radii, it has the additional effect of lowering the
average H I surface density of the remaining gas within
the H I-stripping radius, _R_ H I . This reduction in surface
density increases as the gas removal proceeds inward until
the densest H I regions can no longer form (Figs. 3, 4, 5).

 - Some galaxies show co-spatial truncation of their H I and
molecular gas (Fig. 6), indicating that environmental processes can effectively remove both phases on similar timescales
in the same spatial region.

 - Overall, the molecular gas is less affected than the H I,
and we find evidence that environmental mechanisms first
reduce the lower surface density molecular gas that exists
preferentially at lower Σ _⋆_ (and thus typically larger radii) in
galaxies (Fig. 7). However, we find that once the removal
of H I proceeds sufficiently far within the optical disc, the
average surface density of the remaining molecular gas
within _R_ H I is reduced (Fig. 8).

 - At the spatial scales we are sensitive to, we see no evidence
for environment-driven elevation of the H I or molecular
gas surface density outside the ranges observed in starforming galaxies (Figs. 4, 7).

 - VERTICO galaxies have systematically larger molecularto-atomic gas mass ratios in individual regions compared to
the control sample, but smaller values than expected from
the removal of H I alone (Figs. 9, 11). Using proxies for the
physical conditions in the ISM, we showed that changes to
the physical state of the gas could not explain the observed
molecular-to-atomic gas mass ratios (Figs. 10, 12). Thus,
ablation and/or stripping of the molecular gas on a similar
timescale as the H I in a given 1.2-kpc region is the best
explanation for the reduction of molecular gas content in
VERTICO galaxies.


Our results agree with, and extend upon, previous literature focused on gas stripping and environmental effects in
cluster galaxies (Cortese et al., 2021; Boselli et al., 2022). Combined with the recent, complementary studies from the VERTICO team (Brown et al., 2021; Villanueva et al., 2022; Zabel
et al., 2022), a coherent evolutionary scenario for Virgo cluster galaxies begins to emerge. Compared to isolated systems,
statistically, Virgo galaxies have normal molecular gas content
(Boselli et al., 2014; Cortese et al., 2016) and elevated molecularto-atomic gas mass ratios (Mok et al., 2016; Villanueva et al.,
2022) when considering their integrated properties only. Subsequently, there is poor correlation between H I and molecular

_Publications of the Astronomical Society of Australia_ 19



gas deficiency measurements (Zabel et al., 2022), but this does
not mean that the molecular gas is not affected by environmental processes. Instead, major changes in the _integrated_ molecular
gas mass occur only once a significant fraction of the cold gas
within the stellar disc has been affected.
Our analysis reveals how the molecular gas content of
galaxies is affected by cluster environmental processes in a
spatially-resolved way. We have shown that the reduction of
molecular gas begins at the edge of the stellar disc even in
moderately H I-deficient galaxies, while in the highest H Ideficiency systems the molecular gas becomes significantly
reduced across the disc. While this result has been shown using
integrated measurements and radial profiles (Villanueva et al.,
2022; Zabel et al., 2022), our approach allows us to quantify
this effect as a function of Σ _⋆_ with exquisite detail, and has
allowed us to disentangle between environmentally-driven
and secular/internal processes.
Interestingly, previous works have found evidence for the
compression of molecular gas due to the ICM–ISM interaction
(e.g., Lee et al., 2017; Moretti et al., 2020a,b), particularly in the
early stages of infall. We find no evidence for elevated H I or
molecular gas surface densities, suggesting that in our sample,
which spans a larger (and later) range of infall stages and at
the 1.2-kpc scales we are sensitive to, environment-driven
elevation of cold gas content is not significant.
Our results also emphasise that the gas removal process
is more complex than a simple outside-in stripping scenario,
and it is clear that the environmental processes affect both the
H I and molecular gas within the H I truncation radius (see
also Lee et al., 2022), which is typically assumed to be the
boundary of where stripping is efficient. Even at moderate
H I deficiency, we find that the average surface density of
H I remaining within the disc is reduced, indicating that the
environment does not just affect the H I gas in the outskirts.
This result can be understood as the multi-phase ISM enabling
the ICM to stream through low-density regions and affect
the gas across the disc (e.g., Tonnesen & Bryan, 2009; Lee
et al., 2020). However, we have also shown that the molecular
gas is affected similarly, although it requires a stronger ICM–
ISM interaction (as traced by more H I lost). Thus, the ICM
can ablate and strip gas across the entire discs of galaxies and
does not discriminate which phase is affected so long as the
interaction is strong enough (e.g., Tonnesen & Bryan, 2021;
Choi et al., 2022). Indeed, this agrees well with observations
of larger molecular gas masses in the cometary tails of stripped
galaxies when the associated H α emission is brighter or the
stripping is more advanced (Moretti et al., 2018). In these
cases, it is likely that the stronger stripping has led to a larger
mass-loading of the outflowing gas. Future work with larger
samples of field and cluster galaxies, but in particular, higher
resolution observations that can separate dense and diffuse
CO(2-1) emission will be key to understanding the details of
gas suppression in cluster galaxies.
Last, these results have interesting implications for the
quenching of star formation in cluster galaxies. In particular, the reduction of molecular gas within the inner regions of
galaxies will cause star formation to shut down earlier, and with



a different distribution, than just radial truncation. Comparison to deep H α observations of VERTICO galaxies from the
VESTIGE (A Virgo Environmental Survey Tracing Ionised
Gas Emission, Boselli et al., 2018a) survey would enable the
study of changes to recent, massive star formation in regions
where molecular gas is reduced. Further, future observations
with sensitive optical integral-field spectroscopic instruments
such as MUSE (Multi Unit Spectroscopic Explorer, Bacon et al.,
2017) will allow the study of the physics of galaxy quenching
in unprecedented detail, including the additional impact of
feedback from active galactic nuclei (e.g., Boselli et al., 2016b;
George et al., 2019; Peluso et al., 2022). In particular, employing spectro-photometric fitting techniques (e.g., Fossati
et al., 2018) will enable high spatial resolution studies of star
formation and star-formation history reconstruction across
the discs of Virgo cluster galaxies. These results can then be
connected to cold gas reduction on sub-kpc scales where ISM
physics operates.


**Acknowledgement**

We thank the referee for their useful comments that improved
this paper, and Aaron Robotham for useful conversations. We
wish to acknowledge the custodians of the land on which
much of this work was undertaken, the Wadjuk (Perth region) people of the Nyoongar nation, and their Elders past,
present and future. Part of this work was conducted on the
unceded territory of the Lekwungen and Coast Salish peoples. We acknowledge and respect the Songhees, Esquimalt,
WSÁNEĆ and T’Sou-ke Nations whose historical relationships with the land continue to this day. L.C. and A.B.W
acknowledge support from the Australian Research Council
Discovery Project funding scheme (DP210100337). L.C. is the
recipient of an Australian Research Council Future Fellowship
(FT180100066) funded by the Australian Government. TB
acknowledges support from the National Research Council of
Canada via the Plaskett Fellowship of the Dominion Astrophysical Observatory. C.D.W. acknowledges support from the
Natural Sciences and Engineering Research Council of Canada
and the Canada Research Chairs program. The financial assistance of the National Research Foundation (NRF) towards
this research is hereby acknowledged by N.Z. Opinions expressed and conclusions arrived at, are those of the author and
are not necessarily to be attributed to the NRF. N.Z. is supported through the South African Research Chairs Initiative of
the Department of Science and Technology and National Research Foundation. I.D.R acknowledges support from the ERC
Starting Grant Cluster Web 804208. T.A.D. acknowledges
support from the UK Science and Technology Facilities Council through grants ST/S00033X/1 and ST/W000830/1. A.C.
acknowledges the support from the National Research Foundation grant No. 2018R1D1A1B07048314. A.R.H.S. acknowledges receipt of the Jim Buckee Fellowship at ICRAR-UWA.
K.S. and L.C.P. acknowledge support from the Natural Sciences and Engineering Research Council of Canada (NSERC).
Y.M.B. gratefully acknowledges funding from the Netherlands
Organization for Scientific Research (NWO) through Veni

20 Adam B. Watts _et al._



grant number 639.041.751. V.V. acknowledges support from
the scholarship ANID-FULBRIGHT BIO 2016 - 56160020
and funding from NRAO Student Observing Support (SOS)
- SOSPA7-014. A.D.B. and V.V., acknowledge partial support from NSF-AST2108140. BL acknowledges the support
from the Korea Astronomy and Space Science Institute grant
funded by the Korea government (MSIT) (Project No. 20221-840-05). Parts of this research were supported by the Australian Research Council Centre of Excellence for All Sky
Astrophysics in 3 Dimensions (ASTRO 3D), through project
number CE170100013. This work was carried out as part of
the VERTICO collaboration. This paper makes use of the
following ALMA data:
[ADS/JAO.ALMA #2019.1.00763.L,](https://almascience.nrao.edu/asax/?result_view=observation&projectCode=%222019.1.00763.L%22)
[ADS/JAO.ALMA #2017.1.00886.L,](https://almascience.nrao.edu/asax/?result_view=observation&projectCode=%222017.1.00886.L%22)
[ADS/JAO.ALMA #2016.1.00912.S,](https://almascience.nrao.edu/asax/?result_view=observation&projectCode=%222016.1.00912.S%22)
[ADS/JAO.ALMA #2015.1.00956.S.](https://almascience.nrao.edu/asax/?result_view=observation&projectCode=%222015.1.00956.S%22)
ALMA is a partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC (Canada),
MOST and ASIAA (Taiwan), and KASI (Republic of Korea),
in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and NAOJ. The
National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.


**References**
Abazajian, K. N., Adelman-McCarthy, J. K., Agüeros, M. A., et al. 2009, ApJS,
182, 543
Abdurro’uf, Lin, Y.-T., Hirashita, H., et al. 2022a, Astrophys. J., 926, 81
—. 2022b, Astrophys. J., 935, 98
Abramson, A., Kenney, J. D. P., Crowl, H. H., et al. 2011, AJ, 141, 164
Bacchini, C., Fraternali, F., Iorio, G., & Pezzulli, G. 2019, A&A, 622, A64
Bacon, R., Conseil, S., Mary, D., et al. 2017, Astron. Astrophys., 608, A1
Baker, W. M., Maiolino, R., Bluck, A. F. L., et al. 2022, MNRAS, 510, 3622
Bigiel, F., & Blitz, L. 2012, ApJ, 756, 183
Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846
Blitz, L., & Rosolowsky, E. 2006, ApJ, 650, 933
Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008,
Astrophys. J., 686, 948
Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013, Natur, 499, 450
Boselli, A., Boissier, S., Cortese, L., et al. 2006, Astrophys. J., 651, 811
Boselli, A., Cortese, L., Boquien, M., et al. 2014, A&A, 564, A67
Boselli, A., Fossati, M., & Sun, M. 2022, Astron Astrophys Rev, 30, 3
Boselli, A., & Gavazzi, G. 2006, PASP, 118, 517
Boselli, A., Boissier, S., Heinis, S., et al. 2011, Astron. Astrophys., 528, A107
Boselli, A., Roehlly, Y., Fossati, M., et al. 2016a, Astron. Astrophys., 596, A11
Boselli, A., Cuillandre, J. C., Fossati, M., et al. 2016b, A&A, 587, A68
Boselli, A., Fossati, M., Ferrarese, L., et al. 2018a, Astron. Astrophys., 614,
A56

Boselli, A., Fossati, M., Cuillandre, J. C., et al. 2018b, Astron. Astrophys., 615,
A114

Boselli, A., Fossati, M., Longobardi, A., et al. 2020, Astron. Astrophys., 634,
L1

Brown, T., Catinella, B., Cortese, L., et al. 2017, MNRAS, 466, 1275
Brown, T., Wilson, C. D., Zabel, N., et al. 2021, ApJS, 257, 21
Byrd, G., & Valtonen, M. 1990, ApJ, 350, 89
Caldú-Primo, A., Schruba, A., Walter, F., et al. 2015, Astron. J., 149, 76
—. 2013, Astron. J., 146, 150



Catinella, B., Schiminovich, D., Cortese, L., et al. 2013, MNRAS, 436, 34
Cayatte, V., van Gorkom, J. H., Balkowski, C., & Kotanyi, C. 1990, Astron.
J., 100, 604
Chevance, M., Madden, S. C., Fischer, C., et al. 2020a, Mon. Not. R. Astron.
Soc., 494, 5279
Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020b, Mon. Not.
R. Astron. Soc., 493, 2872
Choi, W., Kim, C.-G., & Chung, A. 2022, Astrophys. J., 936, 133
Chung, A., van Gorkom, J. H., Kenney, J. D. P., Crowl, H., & Vollmer, B.
2009, AJ, 138, 1741
Chung, A., van Gorkom, J. H., Kenney, J. D. P., & Vollmer, B. 2007, ApJL,
659, L115
Ciesla, L., Boselli, A., Elbaz, D., et al. 2016, Astron. Astrophys., 585, A43
Cortese, L., Catinella, B., Boissier, S., Boselli, A., & Heinis, S. 2011, MNRAS,

415, 1797

Cortese, L., Catinella, B., & Smith, R. 2021, Publ. Astron. Soc. Aust., 38, e035
Cortese, L., & Hughes, T. M. 2009, Mon. Not. R. Astron. Soc., 400, 1225
Cortese, L., Davies, J. I., Pohlen, M., et al. 2010, Astron. Astrophys., 518, L49
Cortese, L., Boissier, S., Boselli, A., et al. 2012, Astron. Astrophys., 544, A101
Cortese, L., Bekki, K., Boselli, A., et al. 2016, Mon. Not. R. Astron. Soc., 459,

3574

Cowie, L. L., & Songaila, A. 1977, Natur, 266, 501
Cramer, W. J., Kenney, J. D. P., Cortes, J. R., et al. 2020, Astrophys. J., 901,
95

Crowl, H. H., & Kenney, J. D. P. 2008, Astron. J., 136, 1623
Crowl, H. H., Kenney, J. D. P., van Gorkom, J. H., & Vollmer, B. 2005,
Astron. J., 130, 65
Davies, J. I., Baes, M., Bendo, G. J., et al. 2010, Astron. Astrophys., 518, L48
Dressler, A. 1980, ApJ, 236, 351
Ellison, S. L., Lin, L., Thorp, M. D., et al. 2021a, MNRAS, 502, L6
—. 2021b, MNRAS, 501, 4777
Elmegreen, B. G. 1993, Astrophys. J., 411, 170
Engargiola, G., Plambeck, R. L., Rosolowsky, E., & Blitz, L. 2003, Astrophys.
J. Suppl. Ser., 149, 343
Font, A. S., Bower, R. G., McCarthy, I. G., et al. 2008, Mon. Not. R. Astron.
Soc., 389, 1619
Fossati, M., Gavazzi, G., Savorgnan, G., et al. 2013, Astron. Astrophys., 553,
A91

Fossati, M., Mendel, J. T., Boselli, A., et al. 2018, A&A, 614, A57
Franchetto, A., Vulcani, B., Poggianti, B. M., et al. 2020, Astrophys. J., 895,
106

Frank, K. A., Peterson, J. R., Andersson, K., Fabian, A. C., & Sanders, J. S.
2013, Astrophys. J., 764, 46
Fujita, Y. 1998, ApJ, 509, 587
Fumagalli, M., Krumholz, M. R., Prochaska, J. X., Gavazzi, G., & Boselli, A.
2009, Astrophys. J., 697, 1811
Gavazzi, G., Boselli, A., Scodeggio, M., Pierini, D., & Belsole, E. 1999, Mon.
Not. R. Astron. Soc., 304, 595
George, K., Poggianti, B. M., Bellhouse, C., et al. 2019, Mon. Not. R. Astron.
Soc., 487, 3102
Giovanelli, R., & Haynes, M. P. 1985, Astrophys. J., 292, 404
Girardi, M., Biviano, A., Giuricin, G., Mardirossian, F., & Mezzetti, M. 1993,
ApJ, 404, 38
Glover, S. C. O., & Smith, R. J. 2016, Mon. Not. R. Astron. Soc., 462, 3011
Gronke, M., & Oh, S. P. 2018, Mon. Not. R. Astron. Soc., 480, L111

Gunn, J. E., & Gott, III, J. R. 1972, ApJ, 176, 1
Gupta, A., Yuan, T., Torrey, P., et al. 2018, Mon. Not. R. Astron. Soc., 477,
L35

Haynes, M. P., & Giovanelli, R. 1984, AJ, 89, 758
Haynes, M. P., Giovanelli, R., & Kent, B. R. 2007, Astrophys. J., 665, L19
Haynes, M. P., Jore, K. P., Barrett, E. A., Broeils, A. H., & Murray, B. M.
2000, Astron. J., 120, 703
Ignesti, A., Vulcani, B., Poggianti, B. M., et al. 2022, Astrophys. J., 937, 58

_Publications of the Astronomical Society of Australia_ 21



Jáchym, P., Combes, F., Cortese, L., Sun, M., & Kenney, J. D. P. 2014,
Astrophys. J., 792, 11
Jáchym, P., Sun, M., Kenney, J. D. P., et al. 2017, Astrophys. J., 839, 114
Jáchym, P., Kenney, J. D. P., Sun, M., et al. 2019, Astrophys. J., 883, 145

Jiménez-Donaire, M. J., Brown, T., Wilson, C. D., et al. 2022, VERTICO III:
The Kennicutt-Schmidt Relation in Virgo Cluster Galaxies
Jones, M. G., Espada, D., Verdes-Montenegro, L., et al. 2018, A&A, 609, A17
Jung, S. L., Choi, H., Wong, O. I., et al. 2018, Astrophys. J., 865, 156
Kauffmann, G., White, S. D. M., Heckman, T. M., et al. 2004, Mon. Not. R.
Astron. Soc., 353, 713
Kenney, J. D. P., van Gorkom, J. H., & Vollmer, B. 2004, AJ, 127, 3361
Kennicutt, Robert C., J. 1998, ApJ, 498, 541
Kennicutt, Jr., R. C. 1989, Astrophys. J., 344, 685
Kim, S., Rey, S.-C., Bureau, M., et al. 2016, Astrophys. J., 833, 207
Koopmann, R. A., & Kenney, J. D. P. 2004, Astrophys. J., 613, 866
Kroupa, P. 2001, Mon. Not. R. Astron. Soc., 322, 231
Krumholz, M. R., McKee, C. F., & Tumlinson, J. 2009, ApJ, 693, 216
Larson, R. B., Tinsley, B. M., & Caldwell, C. N. 1980, ApJ, 237, 692
Lee, B., & Chung, A. 2018, Astrophys. J., 866, L10

Lee, B., Chung, A., Tonnesen, S., et al. 2017, Mon. Not. R. Astron. Soc., 466,
1382

Lee, J., Kimm, T., Katz, H., et al. 2020, Astrophys. J., 905, 31
Lee, S., Sheen, Y.-K., Yoon, H., Jaffé, Y., & Chung, A. 2022, Mon. Not. R.
Astron. Soc., 517, 2912
Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782
Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670
Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJ, 244, 24
Leroy, A. K., Hughes, A., Liu, D., et al. 2021, Astrophys. J. Suppl. Ser., 255,
19

Lin, L., Pan, H.-A., Ellison, S. L., et al. 2019, Astrophys. J., 884, L33
Lin, L., Ellison, S. L., Pan, H.-A., et al. 2020, ApJ, 903, 145
Longobardi, A., Boselli, A., Fossati, M., et al. 2020, Astron. Astrophys., 644,
A161

Loni, A., Serra, P., Kleiner, D., et al. 2021, Astron. Astrophys., 648, A31
Marasco, A., Crain, R. A., Schaye, J., et al. 2016, MNRAS, 461, 2630
Martin, C. L., & Kennicutt, Jr., R. C. 2001, Astrophys. J., 555, 301
Martin, D. C., Fanson, J., Schiminovich, D., et al. 2005, ApJL, 619, L1
Martínez-Delgado, D., Gabany, R. J., Crawford, K., et al. 2010, Astron. J.,
140, 962
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, 376,
127

Mei, S., Blakeslee, J. P., Côté, P., et al. 2007, Astrophys. J., 655, 144
Meyer, M., Robotham, A., Obreschkow, D., et al. 2017, PASA, 34,
doi:10.1017/pasa.2017.31

Mihos, J. C. 2004, in Clust. Galaxies Probes Cosmol. Struct. Galaxy Evol., 277
Mogotsi, K. M., de Blok, W. J. G., Caldú-Primo, A., et al. 2016, Astron. J.,
151, 15
Mohr, J. J., Mathiesen, B., & Evrard, A. E. 1999, Astrophys. J., 517, 627
Mok, A., Wilson, C. D., Golding, J., et al. 2016, Mon. Not. R. Astron. Soc.,
456, 4384

Moore, B., Katz, N., Lake, G., Dressler, A., & Oemler, A. 1996, Natur, 379,

613

Morales, G., Martínez-Delgado, D., Grebel, E. K., et al. 2018, Astron. Astrophys., 614, A143
Moretti, A., Paladino, R., Poggianti, B. M., et al. 2018, MNRAS, 480, 2508
—. 2020a, Astrophys. J., 889, 9
—. 2020b, Astrophys. J., 897, L30
Morselli, L., Rodighiero, G., Enia, A., et al. 2020, Mon. Not. R. Astron. Soc.,
496, 4606
Nulsen, P. E. J. 1982, MNRAS, 198, 1007
Peluso, G., Vulcani, B., Poggianti, B. M., et al. 2022, Astrophys. J., 927, 130
Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010, ApJ, 721, 193



Pessa, I., Schinnerer, E., Belfiore, F., et al. 2021, Astron. Astrophys., 650, A134
Pessa, I., Schinnerer, E., Leroy, A. K., et al. 2022, Astron. Astrophys., 663,
A61

Pety, J., Schinnerer, E., Leroy, A. K., et al. 2013, Astrophys. J., 779, 43
Polk, K. S., Knapp, G. R., Stark, A. A., & Wilson, R. W. 1988, Astrophys. J.,
332, 432

Quilis, V., Moore, B., & Bower, R. 2000, Science, 288, 1617
Reynolds, T. N., Westmeier, T., Elagali, A., et al. 2021, MNRAS, 505, 1891
Reynolds, T. N., Catinella, B., Cortese, L., et al. 2022, Mon. Not. R. Astron.
Soc., 510, 1716
Roberts, I. D., van Weeren, R. J., McGee, S. L., et al. 2021, Astron. Astrophys.,
652, A153
Roediger, E., & Brüggen, M. 2007, Mon. Not. R. Astron. Soc., 380, 1399
Roediger, E., & Hensler, G. 2005, Astron. Astrophys., 433, 875
Roman-Duval, J., Heyer, M., Brunt, C. M., et al. 2016, Astrophys. J., 818, 144
Saintonge, A., & Catinella, B. 2022, Annu. Rev. Astron. Astrophys., 60, 319
Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22
Sarazin, C. L. 1986, Rev. Mod. Phys., 58, 1
Schmidt, M. 1959, ApJ, 129, 243
Schuster, K.-F., Boucher, C., Brunswig, W., et al. 2004, Astron. Astrophys.,
423, 1171
Sivanandam, S., Rieke, M. J., & Rieke, G. H. 2010, Astrophys. J., 717, 147
—. 2014, Astrophys. J., 796, 89
Skillman, E. D., Kennicutt, Jr., R. C., Shields, G. A., & Zaritsky, D. 1996,
Astrophys. J., 462, 147
Smith, R. J., Glover, S. C. O., Clark, P. C., Klessen, R. S., & Springel, V. 2014,
Mon. Not. R. Astron. Soc., 441, 1628
Sofue, Y., Koda, J., Nakanishi, H., & Hidaka, M. 2003, Publ. Astron. Soc.
Jpn., 55, 75
Solanes, J. M., Manrique, A., García-Gómez, C., et al. 2001, Astrophys. J.,
548, 97

Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677
Sparre, M., Pfrommer, C., & Vogelsberger, M. 2019, Mon. Not. R. Astron.
Soc., 482, 5401
Steinhauser, D., Schindler, S., & Springel, V. 2016, Astron. Astrophys., 591,
A51

Stevens, A. R. H., Diemer, B., Lagos, C. d. P., et al. 2019a, MNRAS, 490, 96
—. 2019b, MNRAS, 483, 5334
Stevens, A. R. H., Lagos, C. d. P., Cortese, L., et al. 2021, MNRAS, 502, 3158
Struble, M. F., & Rood, H. J. 1999, ApJS, 125, 35
Sun, J., Leroy, A. K., Schruba, A., et al. 2018, Astrophys. J., 860, 172
Tonnesen, S., & Bryan, G. L. 2009, Astrophys. J., 694, 789
—. 2010, Astrophys. J., 709, 1203
—. 2021, Astrophys. J., 911, 68
Upadhyay, A. K., Oman, K. A., & Trager, S. C. 2021, Astron. Astrophys.,
652, A16
Urban, O., Werner, N., Simionescu, A., Allen, S. W., & Böhringer, H. 2011,
Mon. Not. R. Astron. Soc., 414, 2101
Villanueva, V., Bolatto, A. D., Vogel, S., et al. 2022, arXiv e-prints
Vollmer, B., Cayatte, V., Balkowski, C., & Duschl, W. J. 2001, ApJ, 561, 708
Vollmer, B., Huchtmeier, W., & van Driel, W. 2005, Astron. Astrophys., 439,
921

Vollmer, B., Soida, M., Braine, J., et al. 2012, Astron. Astrophys., 537, A143
Vulcani, B., Poggianti, B. M., Tonnesen, S., et al. 2020, Astrophys. J., 899, 98
Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563
Wang, J., Koribalski, B. S., Serra, P., et al. 2016, MNRAS, 460, 2143
Wang, J., Fu, J., Aumer, M., et al. 2014, MNRAS, 441, 2159
Werle, A., Poggianti, B., Moretti, A., et al. 2022, Astrophys. J., 930, 43
Wilson, C. D., & Walker, C. E. 1994, Astrophys. J., 432, 148
Woo, J., Dekel, A., Faber, S. M., et al. 2013, MNRAS, 428, 3306
Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868
Wright, R. J., del P Lagos, C., Power, C., et al. 2022, Mon. Not. R. Astron.
Soc., doi:10.1093/mnras/stac2042

22 Adam B. Watts _et al._


Wright, R. J., Lagos, C. d. P., Davies, L. J. M., et al. 2019, Mon. Not. R.
Astron. Soc., 487, 3740
Yamagami, T., & Fujita, Y. 2011, Publ. Astron. Soc. Jpn., 63, 1165
Yoon, H., Chung, A., Smith, R., & Jaffé, Y. L. 2017, ApJ, 838, 81
York, D. G., Adelman, J., Anderson, John E., J., et al. 2000, AJ, 120, 1579
Yun, K., Pillepich, A., Zinger, E., et al. 2019, MNRAS, 483, 1042
Zabel, N., Davis, T. A., Smith, M. W. L., et al. 2019, Mon. Not. R. Astron.
Soc., 483, 2251
Zabel, N., Brown, T., Wilson, C. D., et al. 2022, Astrophys. J., 933, 10


**Appendix 1.** **Combinedandindividual** Σ **mol** / Σ **H** I **relations**

_Publications of the Astronomical Society of Australia_ 23































|Col1|2<br>gas<br>PDF<br>0|Col3|Col4|Col5|
|---|---|---|---|---|
|0.5<br>gas|0.5<br>gas|0.5<br>gas|gas|gas|
|HERACLES<br>VERTICO<br>5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>3.5<br>2.0<br>1.5<br>1.0<br>0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>2.0|mol/<br>HI|20<br>1.5<br>1.0<br>0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>2.0<br>log<br>mol/<br>HI<br>|HERACLES<br>VERTICO<br>0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>2.0<br>1.5<br>1.0<br>0.5<br>0.0<br>0.5<br>1.0<br>1.5<br>2.0|mol/<br>HI|


0.5 1.0 1.5 2.0 2.5 3.0 3.5
log( 0.5 gas [) [M] [1.5] [pc] 3 ]





0.5 1.0 1.5 2.0 2.5 0 1
log gas [ [M] [pc] 2 ] PDF



0 1

PDF



**Figure 13.** Combined versions of the spatially resolved Σ mol / Σ H I relations as a function of two proxies for the ISM physical conditions. The lef panel shows
Σ mol / Σ H I vs the midplane-pressure proxy log Σ [0.5] _⋆_ [Σ] [gas] [, and the right panel vs the total gas surface density][ Σ] [gas] [. Contours levels for both samples enclose the]
5, 16, 50, 84, and 95 per cent of the sample. Density-normalised histograms of log ( Σ mol / Σ H I ), log Σ [0.5] _⋆_ [Σ] [gas] [, and][ log][ Σ] [gas] [ are shown opposite their respective]

axes.

24 Adam B. Watts _et al._


def-HI



2 2
-0.30 NGC4651



0.12 NGC4654 2


1


0



1


0



-0.10 NGC4254 2


1


0



1

1 2 3



1


0


1


2



1 2 3



2



1


2



1 2 3



1


2



0.41 NGC4298


1


0



0.38 NGC4568


1


0



1


0



0.35 NGC4321


1


0



1

1 2 3



1


2



1 2 3



2 1 2 3 2
0.58 NGC4501



1


2



1 2 3



1


2



0.68 NGC4689


1


0



1


0



0.62 NGC4394


1


0



1

1 2 3



1


0


1


2



1 2 3



0.13 NGC4567


0.41 1 2 N ~~G~~ 3 C4 ~~5~~ 35


0.82 1 2 NGC4548 3


1.17 1 2 NGC4450 3



2



1


2



1 2 3



1


2



1.13 NGC4380


1


0


1



1


0



0.92 NGC4457


1


0



1

1 2 3



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



1



0.95 NGC4579


1


0


1



2 1 2 3
1.47 NGC4569



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



0.0


0.5


1.0


1.5


2.0



1


0


1



VERTICO


Median & 16 [th] -84 [th] percentile



HERACLES median


16 [th] -84 [th] percentile

Mock HI-only removal



1 2 3
log( 0.5 gas [) [M] [1.5] [pc] 3 ]



**Figure 14.** Individual log ( Σ mol / Σ H I ) – log Σ [0.5] _⋆_ [Σ] [gas] [ relations for VERTICO galaxies, with the galaxy name given in the top-right of each panel. The panels are]
ordered in rows by def-H I (noted in the top-lef corner), which also sets the colour of each panel, and a colour bar is displayed on the right-hand side. The
median relation for each galaxy computed in 0.25 dex log Σ _⋆_ bins are shown with large white markers, and error bars show the 16 [th] and 84 [th] percentiles of
the log ( Σ mol / Σ H I ) distribution in each bin.. The HERACLES control sample is shown with thick (median) and thin (16 [th] and 84 [th] percentiles). The shif in the
HERACLES median that would be expected from the observed reduction in Σ H I at fixed Σ _⋆_ for each galaxy is shown with a solid red line. The two galaxies
marked with stars are interacting, and their H I observations are partially confused.

_Publications of the Astronomical Society of Australia_ 25


def-HI



2 2
-0.30 NGC4651



0.13 NGC4567



0.12 NGC4654 2


1


0


1



1


0



-0.10 NGC4254 2


1


0


1



1

0 1 2



1


0


1



2 0 1 2



2



2 0 1 2



2 0 1 2



0.41 NGC4298


1


0


1



0.41 ~~N~~ G ~~C~~ 4535



1


0



0.35 NGC4 ~~3~~ 21


1


0



1

0 1 2



0 1 2



2



1



0.38 NGC4568


1


0


1



2 0 1 2 2
0.58 NGC4501



2 0 1 2



2 0 1 2



0.68 NGC4689


1


0


1



0.82 NGC4548



1


0



0.62 NGC4394


1


0


1



1

0 1 2



1


0


1



2 0 1 2



2



2 0 1 2



2 0 1 2



1.13 NGC4380


1


0


1



1.17 NGC4450



0.0


0.5


1.0


1.5


2.0



1


0



0.92 NGC4457


1


0



1

0 1 2



1



0.95 NGC4579


1


0


1



2 0 1 2
1.47 NGC4569



0 1 2

2
log gas [ [M] [pc] ]



0 1 2

2
log gas [ [M] [pc] ]


HERACLES median


16 [th] -84 [th] percentile

Mock HI-only removal



1


0


1


0 1 2

2
log gas [ [M] [pc] ]



0 1 2

2
log gas [ [M] [pc] ]



VERTICO


Median & 16 [th] -84 [th] percentile



**Figure 15.** The same as Fig. 14, but for the individual log ( Σ mol / Σ H I ) – log Σ gas relations.


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: large_program_or_survey",
  "failed_quote": "In this work, we present a new analysis of the cold gas properties within the stellar components of Virgo cluster galaxies using observations from the Virgo Environment Traced in CO(2-1) (VERTICO, Brown et al., 2021) ALMA ACA large program."
 },
 {
  "path": "data.arrays.evidence[0]",
  "value": "ALMA ACA (7-m array and Total Power array; NGC4394 and NGC4567 are 7-m array only)",
  "failed_quote": "using observations from the Virgo Environment Traced in CO(2-1) (VERTICO, Brown et al., 2021) ALMA ACA large program."
 },
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "Milky Way disc CO(1-0) conversion factor alpha_CO = 4.35 M_sun pc^-2",
  "failed_quote": "and a constant α CO = 4.35 M ⊙ pc –2 based on observations of the Milky Way disc by Bolatto et al. (2013), which includes a 36 per cent contribution from Helium."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "VERTICO parent sample selection, ALMA CO(2-1) data reduction, signal masking, moment 0 map creation, R_21 = 0.8, and SDSS Kron aperture fitting for PA and inclination",
  "failed_quote": "We refer the reader to Brown et al. (2021) for a detailed description of the parent sample selection and data reduction."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "R_21 = 0.8, alpha_CO = 4.35 M_sun pc^-2, intrinsic axial ratio q = 0.2",
  "failed_quote": "We used a constant R 21 = 0.8, as derived by Brown et al. (2021), and a constant α CO = 4.35 M ⊙ pc –2 based on observations of the Milky Way disc by Bolatto et al. (2013), which includes a 36 per cent contribution from Helium."
 },
 {
  "path": "analysis_steps[3].validation.evidence[1]",
  "value": "Tested combining all control spaxels without <log Sigma_*>_HI matching for H I; tested excluding NGC 4394 from moderate def-H I Sigma_mol within R_HI; tested alternative high Sigma_* bin boundaries ([2, 2.5) and >= 2).",
  "failed_quote": "We recomputed the log Σ mol histogram with NGC 4394 excluded and found that a smaller tail toward lower surface density Σ mol still remains."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Observed median log(Sigma_mol/Sigma_HI) in low midplane pressure bin (moderate def-H I) = 0.09 dex",
  "failed_quote": "medians of 0.24 ± 0.03 dex and 0.65 ± 0.03 dex for the moderate and large def-H I populations, which over-estimate their observed values of 0.09 ± 0.07 dex and 0.31 ± 0.04 dex by 0.15 dex and 0.34 dex, respectively."
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Observed median log(Sigma_mol/Sigma_HI) in low midplane pressure bin (large def-H I) = 0.31 dex",
  "failed_quote": "medians of 0.24 ± 0.03 dex and 0.65 ± 0.03 dex for the moderate and large def-H I populations, which over-estimate their observed values of 0.09 ± 0.07 dex and 0.31 ± 0.04 dex by 0.15 dex and 0.34 dex, respectively."
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "Observed median log(Sigma_mol/Sigma_HI) in low Sigma_gas bin (moderate def-H I) = 0.05 dex",
  "failed_quote": "In the lower Σ gas bin, the expected median Σ mol / Σ H I from H I-only removal scenarios, 0.17 ± 0.04 dex and 0.63 ± 0.04 dex, over-estimate the observed values of 0.05 ± 0.07 dex 0.47 ± 0.03 dex for the moderate and large defH I samples by 0.12 dex and 0.16 dex respectively."
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Observed median log(Sigma_mol/Sigma_HI) in low Sigma_gas bin (large def-H I) = 0.47 dex",
  "failed_quote": "over-estimate the observed values of 0.05 ± 0.07 dex 0.47 ± 0.03 dex for the moderate and large defH I samples by 0.12 dex and 0.16 dex respectively."
 }
]
```
