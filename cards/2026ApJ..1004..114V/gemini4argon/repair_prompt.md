# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1004..114V\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version May 13, 2026
Typeset using L [A] TEX **twocolumn** style in AASTeX631


**JWST’s** **PEARLS:** **A** **clumpy** **ring** **galaxy** **at** _z_ = 4 _._ 0148


David [Vizgan](http://orcid.org/0000-0001-7610-5544), [1] [Ming-Yang](http://orcid.org/0000-0001-5105-2837) Zhuang, [1] Ian [Smail](http://orcid.org/0000-0003-3037-257X), [2] Rogier A. [Windhorst](http://orcid.org/0000-0001-8156-6281), [3] Gibson B. [Bowling](http://orcid.org/0009-0007-0782-0721), [3]

Cheng [Cheng](http://orcid.org/0000-0003-0202-0534), [4, 5] Seth H. [Cohen](http://orcid.org/0000-0003-3329-1337), [3] Christopher [J.](http://orcid.org/0000-0003-1949-7638) Conselice, [6] Jose M. Diego, [7] Brenda [L.](http://orcid.org/0000-0003-1625-8009) Frye, [8]

Norman [A.](http://orcid.org/0000-0001-9440-8872) Grogin, [9] Rolf A. [Jansen](http://orcid.org/0000-0003-1268-5230), [3] Patrick S. [Kamieneski](http://orcid.org/0000-0001-9394-6732), [10] Anton M. [Koekemoer](http://orcid.org/0000-0002-6610-2048), [9]

Rafael [Ortiz](http://orcid.org/0000-0002-6150-833X) III, [3] Massimo [Ricotti](http://orcid.org/0000-0003-4223-7324), [11] [Bangzheng](http://orcid.org/0000-0001-7957-6202) Sun, [12] Hayley [Williams](http://orcid.org/0000-0002-1681-0767), [3] S. P. [Willner](http://orcid.org/0000-0002-9895-5758), [13]

[Haojing](http://orcid.org/0000-0001-7592-7714) Yan, [12] Aadya [Agrawal](http://orcid.org/0009-0008-1965-9012), [1] Manuel [Solimano](http://orcid.org/0000-0001-6629-0379), [14] Zachary Stone, [1] Joaquin [D.](http://orcid.org/0000-0001-7192-3871) Vieira, [1, 15, 16] and
[Chentao](http://orcid.org/0000-0002-8117-9991) Yang 10


1 _Department_ _of_ _Astronomy,_ _University_ _of_ _Illinois,_ _1002_ _West_ _Green_ _Street,_ _Urbana,_ _IL,_ _61801,_ _USA_
2 _Centre_ _for_ _Extragalactic_ _Astronomy,_ _Department_ _of_ _Physics,_ _Durham_ _University,_ _South_ _Road,_ _Durham_ _DH1,_ _3LE,_ _UK_
3 _School_ _of_ _Earth_ _and_ _Space_ _Exploration,_ _Arizona_ _State_ _University,_ _Tempe,_ _AZ_ _85287-6004,_ _USA_
4 _Chinese_ _Academy_ _of_ _Sciences_ _South_ _America_ _Center_ _for_ _Astronomy,_ _National_ _Astronomical_ _Observatories,_ _CAS,_ _Beijing_ _100101,_ _China_
5 _Key_ _Laboratory_ _of_ _Optical_ _Astronomy,_ _NAOC,_ _20A_ _Datun_ _Road,_ _Chaoyang_ _District,_ _Beijing_ _100101,_ _China_
6 _Jodrell_ _Bank_ _Centre_ _for_ _Astrophysics,_ _University_ _of_ _Manchester,_ _Oxford_ _Road,_ _Manchester_ _UK_
7 _Instituto_ _de_ _Fisica_ _de_ _Cantabria_ _(CSIC-UC)._ _Avenida._ _Los_ _Castros_ _s/n,_ _E-39005_ _Santander,_ _Spain_
8 _Department_ _of_ _Astronomy/Steward_ _Observatory,_ _University_ _of_ _Arizona,_ _933_ _N._ _Cherry_ _Avenue,_ _Tucson,_ _AZ_ _85721,_ _USA_
9 _Space_ _Telescope_ _Science_ _Institute,_ _3700_ _San_ _Martin_ _Drive,_ _Baltimore,_ _MD_ _21218,_ _USA_
10 _Department_ _of_ _Space,_ _Earth_ _&_ _Environment,_ _Chalmers_ _University_ _of_ _Technology,_ _412_ _96_ _Gothenburg,_ _Sweden_
11 _Department_ _of_ _Astronomy,_ _University_ _of_ _Maryland,_ _College_ _Park,_ _Maryland_ _20742,_ _USA_
12 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Missouri-Columbia,_ _701_ _S_ _College_ _Ave,_ _Columbia,_ _Missouri_ _65201_
13 _Center_ _for_ _Astrophysics_ _|_ _Harvard_ _&_ _Smithsonian,_ _60_ _Garden_ _Street,_ _Cambridge,_ _MA,_ _02138,_ _USA_
14 _Centro_ _de_ _Astrobiolog´ıa_ _(CAB),_ _CSIC-INTA,_ _Ctra._ _de_ _Ajalvir_ _km_ _4,_ _Torrej´on_ _de_ _Ardoz,_ _E-28850,_ _Madrid,_ _Spain_
15 _Department_ _of_ _Physics,_ _University_ _of_ _Illinois,_ _1110_ _West_ _Green_ _Street,_ _Urbana,_ _IL,_ _61801,_ _USA_
16 _Center_ _for_ _AstroPhysical_ _Surveys,_ _National_ _Center_ _for_ _Supercomputing_ _Applications,_ _1205_ _West_ _Clark_ _Street,_ _Urbana,_ _IL,_ _61820,_ _USA_


ABSTRACT


Ring galaxies are an uncommon class of galaxies whose morphology is closely related to dynamical
processes that govern galaxy evolution. Some ring galaxies, known as “collisional ring galaxies”, are
thought to form as a consequence of head-on collisions between galaxies, and a number of high-redshift
collisional ring galaxies have been discovered and/or studied in the era of the James Webb Space
Telescope (JWST). In this paper, we present HST/ACS, JWST/NIRCam, and JWST/NIRSpec observations of a candidate ring galaxy at _z_ spec = 4 _._ 0148, previously identified as a potential gravitational
lens. The galaxy exhibits a complex morphology, including three bright clumps along an apparent ring
with radius _≈_ 0 _._ 25 _[′′]_ _≃_ 1 _._ 8 kpc. It has a total SFR = 140 [+20] _−_ 30 [M] _[⊙]_ [yr] _[−]_ [1] [and] [log(] _[M]_ _[∗]_ _[/]_ [M] _[⊙]_ [) = 10] _[.]_ [41] [+0] _−_ 0 _[.]_ _._ [11] 13 [,]
making it similar to other high-redshift collisional ring galaxies. Although we argue strongly in favor of
the collisional ring explanation, we cannot entirely rule out a galaxy-galaxy strong lensing explanation
for the system’s morphology, in which a foreground galaxy at _z_ _≃_ 1 _._ 7 lenses a galaxy at _z_ _≃_ 4 _._ 0 into an
Einstein ring-like configuration; to confirm the nature of this source, we require kinematic information
via high spectral resolution observations. We suggest that current and future gravitational lens surveys
should consider high-redshift ring galaxies as possible but significant contaminants.


_Keywords:_ Galaxy evolution (594) – High-redshift galaxies (734) – Ring galaxies (1400) – Strong
gravitational lensing (1643)



1. INTRODUCTION


Astronomers have known for a century that galaxies
exhibit stark differences in morphology (Hubble 1926),
and for decades have studied the inextricable links be
tween morphological features, such as spiral arms and



bars, to galaxy evolution and the processes that govern
it across cosmic time (e.g. de Vaucouleurs 1959; Kormendy & Kennicutt 2004; Buta et al. 2015). Rings are
an uncommon but important morphological feature in
galaxies which appear to be present in _∼_ 20% of spi

2


ral galaxies (e.g. Buta & Combes 1996; Fernandez et al.
2021). Most commonly, rings in galaxies are manifestations of special resonant patterns (such as inner and
outer Lindblad resonances) with density waves that govern spiral structure in galaxies (Buta & Combes 1996;
Buta 1999; Comer´on et al. 2014).
A special case of ring galaxies is the “collisional ring”
galaxy (see Appleton & Struck-Marcell 1996, for review), which accounts for just 0.01% of all galaxies
(Madore et al. 2009). The standard picture of their
formation involves a galaxy collision (Lynds & Toomre
1976; Theys & Spiegel 1977; Binney & Tremaine 2008);
specifically, a smaller galaxy, often likened to a “bullet”
in the literature (Parker et al. 2015; Khoram et al. 2026),
collides head-on with a larger disk (Appleton & StruckMarcell 1996), triggering a density wave propagating
outward across the disk plane. Collisional rings are predicted to be clumpy and short-lived (e.g. Elmegreen &
Elmegreen 2006; Renaud et al. 2018), and both resonant and collisional ring galaxies exhibit enhanced starformation due to the compression of gas along wavefronts (e.g. Appleton & Struck-Marcell 1987).
Recently, ring galaxies have been identified beyond
_z_ _>_ 1 (Yuan et al. 2020; Liu et al. 2023), particularly using JWST (Nestor Shachar et al. 2025; Perna et al. 2025;
Li et al. 2026; Khoram et al. 2026). The majority of
these sources are thought to have formed from collisions
due to the presence of nearby companions, which have
made them compelling laboratories for merger-related
dynamics at high redshift. Their relative rarity in the
early universe is debated; Smirnov & Reshetnikov (2022)
analytically determined that the volume density of collisional ring galaxies should increase with cosmic time,
whereas Elagali et al. (2018) found in simulations that
the collisional ring galaxy formation density rate should
be roughly constant with redshift, a finding inferred by
Yuan et al. (2020) from observations. Collisional ring
galaxies have been proposed as alternative signposts for
galaxy mergers / merger rates across cosmic time (e.g.
Lavery et al. 2004; D’Onghia et al. 2008), though it has
been argued with simulations that collisional ring galaxies could be a biased tracer of mergers across redshift
(Elagali et al. 2018). The merger and galaxy interaction
rate is greater at higher redshifts (Duan et al. 2025), and
thus one might expect ring galaxy number densities to
increase with redshift.

In this paper, we study a high-redshift galaxy near
the galaxy cluster MACS J0416.1-2403, selected from
the Massive Cluster Survey (MACS; Ebeling et al. 2001),
which has been characterized as a complex merging cluster at _z_ = 0 _._ 397 (Mann & Ebeling 2012). Multiple works
(e.g. Jauzac et al. 2014; Diego et al. 2024; Rihtarˇsiˇc



et al. 2025) have used the presence of arcs and multiply
imaged galaxies, due to gravitational lensing, to build
an accurate lens model for this cluster, thanks to highresolution, deep imaging with the Hubble Space Telescope (HST) and James Webb Space Telescope (JWST),
respectively.
The galaxy examined in this work was first cataloged
by Merlin et al. (2016) and further discussed by Diego
et al. (2024), who suggested that it was a high-redshift
gravitational lens candidate. Using multi-band HST
ACS and JWST NIRCam imaging, along with NIRSpec
PRISM observations, we argue in this work that it is
most likely a collisional ring galaxy. If this system is a
natural ring galaxy, and not a galaxy-galaxy scale lens,
then it is the most distant galaxy-scale ring discovered to
date, with a spectroscopic redshift _z_ = 4 _._ 0148. We also

show in this work that this source is similar in several

important aspects to other collisional ring candidates
studied with JWST (e.g. Nestor Shachar et al. 2025;
Perna et al. 2025). We present multi-band imaging and
spectra from HST and JWST in _§_ 2. We describe the
morphology of the source in _§_ 3. We study the photometry, perform spectral energy distribution (SED) fitting
in _§_ 4, and contextualize this galaxy alongside similar
sources in _§_ 5, concluding this work in _§_ 6. Throughout
this work we assume the flat ΛCDM cosmology from the
Planck Collaboration et al. (2020) results; _H_ 0 = 67 _._ 7 km
s _[−]_ [1], Ω 0 = 0 _._ 31, _T_ cmb = 2 _._ 725 K.


2. OBSERVATIONS


The target of this study is a candidate ring galaxy
found on the periphery of the MACS0416 cluster field
at _α_ = 04 [h] 16 [m] 11 _._ 11 [s], _δ_ = _−_ 24 _[◦]_ 05 _[′]_ 24 _._ 9 _[′′]_ and was observed by JWST for the Prime Extragalactic Areas for
Reionization and Lensing Science (PEARLS) project
(Windhorst et al. 2023). The source is cataloged as

[MAC2016] M0416cl 183 by Merlin et al. (2016) with
a photometric redshift _z_ phot = 3 _._ 55 _±_ 0 _._ 17, and is cataloged as CANUCS 3100560 in the CAnadian NIRISS
Unbiased Cluster Survey (Sarrouh et al. 2026) with a
spectroscopic redshift _z_ spec = 4 _._ 0148. For simplicity, we
refer to this source as “the CRG” for the remainder of

the work.

We utilize mosaics generated from multi-observatory
imaging of this source with the HST ACS instrument
(Ford et al. 2003), and the JWST NIRCam instrument
(Rieke et al. 2023). The mosaics were produced as
part of the PEARLS project (Windhorst et al. 2023),
with the HST mosaics produced using the ‘mosaicdrizzle’ pipeline (developed and presented by Koekemoer
et al. 2011), where the HST data came from several
different programs including CLASH (Postman et al.

3


**Figure** **1.** **Left:** 4 arcmin [2] pseudo-RGB image of the MACS0416 cluster, using JWST NIRCam F115W + F150W as blue,
F200W + F277W as green, and F356W + F444W as red. The location of the ring galaxy is indicated in a magenta box. **Right:**
2 _[′′]_ cutout of the candidate ring galaxy in JWST F150W imaging (top) and 2 _[′′]_ re-scaled RGB cutout of the CRG (bottom),
using the F150W, F200W, and F356W filters (corresponding to rest-frame wavelengths of 0.30, 0.40, and 0.71 _µ_ m respectively
at _z_ = 4 _._ 0148). In the top panel, we show the _∼_ 3 _σ_ ALMA detection from the ALCS survey (Fujimoto et al. 2024) as a red
contour. The JWST imaging of the CRG clearly reveals a ring morphology; we have scaled the channels of the RGB cutout to
emphasize the clumpy blue ring surrounding the red center of the system.



2012), Hubble Frontier Fields (HFF; Lotz et al. 2017),
BUFFALO (Steinhardt et al. 2020), in addition to other
public archival data (with the full list of programs being
12459 PI: M. Postman; 13386 PI: S. Rodney; 13459 PI:
T. Treu; 13496 PI: J. Lotz; 14209 PI: B. Siana; 15117 PI:
C. Steinhardt; 15936 PI: P. Kelly; 15940 PI: B. Ribeiro;
16278 PI: P. Kelly, 16729 PI: P. Kelly, 16757 PI: A.
Gonzalez). The HST mosaics were produced from data
calibrated with version caldp.20231201 of the HST calibration software [1], using reference files from HST CRDS [2]

context file 1132.pmap. The JWST mosaics used the
JWST pipeline [3] version 1.13.4 (Bushouse et al. 2024),
calibrated with reference files from JWST CRDS [4] con

1 [https://github.com/spacetelescope/hstcal](https://github.com/spacetelescope/hstcal)

2 [https://hst-crds.stsci.edu](https://hst-crds.stsci.edu)

3 [https://github.com/spacetelescope/jwst](https://github.com/spacetelescope/jwst)

4 [https://jwst-crds.stsci.edu](https://jwst-crds.stsci.edu)



text file 1214.pmap. We make use of the F606W and
F814W bands from HST ACS, and the F090W, F115W,
F150W, F182M, F200W, F277W, F356W, and F444W
bands from JWST NIRCam. The native flux density
units of the mosaics are in nJy, and the pixel size of the
mosaics is 0.02 _[′′]_ . Further details are presented in the
PEARLS overview paper (Windhorst et al. 2023). We
also make use of a publicly available NIRSpec PRISM
spectrum of the source from the CANUCS Data Release
1, as detailed in Sarrouh et al. (2026).
MACS0416 was also observed as part of an ALMA
Large Program (2018.1.00035.L; PI: K. Kohno), the
ALMA Lensing Cluster Survey (ALCS; Fujimoto et al.
2024), using the Band 6 receiver. Reduced data products for the cluster have been made available on the
ALCS website [5] . These data products are constructed


5 [https://www.ioa.s.u-tokyo.ac.jp/ALCS/](https://www.ioa.s.u-tokyo.ac.jp/ALCS/)

4


as a mosaic of the entire cluster; the map uses natural
weighting, with a restoring beam size of 1 _._ 48 _[′′]_ _×_ 0 _._ 86 _[′′]_

and a pixel size of 0.16 _[′′]_ . Dust continuum at an observed
frequency _ν_ obs = 261 _._ 3 GHz is detected at _≈_ 3 _σ_ significance for a flux density rms of 53 _µ_ Jy beam _[−]_ [1] . After
correcting for the beam factor, we obtain a flux density
of 240 _±_ 80 _µ_ Jy for the dust continuum.


3. RESULTS


In Figure 1 we present a pseudo-RGB view of the cluster field, combining six filters of JWST NIRCam imaging, and two zoomed panels showing the ring galaxy in
more detail. The multi-color image of the CRG reveals a
red galaxy that is surrounded by a diffuse blue ring, and
the high-resolution imaging in F150W clearly shows a
ring that is dominated by three bright clumps. We estimate that the ring has a radius of _≈_ 0 _._ 25 _[′′]_ by roughly fitting an ellipse around the ring using the `CARTA` software
(Comrie et al. 2021). This distinct combination of color
and morphology is why Diego et al. (2024) identified
this object as a candidate galaxy-galaxy lens. The system also includes some faint features, namely five faint
companions within a _∼_ 1 _[′′]_ radius, and an apparent tidal
tail extending from the west end of the galaxy towards
the northeast (see Section 4).
The NIRSpec PRISM spectrum covers the center of
the galaxy along with at least one clump. We present
this spectrum in Figure 2. The published redshift of
_z_ = 4 _._ 0148 from Sarrouh et al. (2026) for this source is
derived from the PRISM data, with robust detections of
the H _α_ +[N II ] complex, the [S II ] doublet, the He I line
at 1.083 _µ_ m, [S III ] lines, and faint Ly _α_ . Due to the low
spectral resolution of the NIRSpec data, it is challenging
to accurately constrain line fluxes, or to deblend some
line emission, e.g., the H _α_ flux with the neighboring [N II ]
lines. The resolution in the NIRSpec data, however, is
sufficient to see some structure in the H _α_ +[N II ] complex
that is consistent with normal star-formation and H II

emission. Furthermore, there are no obvious lines that
cannot be explained by the spectrum of a star-forming
galaxy at _z_ = 4.
The faint ALMA detection of dust continuum, along
with its relatively low spatial resolution, makes it difficult to determine whether the bulk of emission arises

from the red component or blue ring. We scale the
1.15mm flux density to an 870 _µ_ m flux density assuming _β_ = 1 _._ 8, yielding _S_ 870 _µ_ m = 0 _._ 7 _±_ 0 _._ 2 mJy, which we
convert into a dust mass using the redshift-independent
scaling relation in Dudzeviˇci¯ut˙e et al. (2020) to obtain
_M_ dust = (9 _±_ 4) _×_ 10 [7] _M_ _⊙_ .
There are three scenarios which sufficiently explain
the measured spectroscopic redshift for the source. The



simplest explanation is that the entire system is a ring
galaxy at _z_ _≈_ 4, making it the farthest such system
ever detected. This explanation is supported by the 2D
PRISM spectrum presented in Figure 2, in which the
emission lines peak at the spatial center of the slit. An
alternative explanation is that the strong lines detected
with NIRSpec are emitted from the “ring” and that the
red central emission comes from a foreground galaxy; in
other words, this is a galaxy-galaxy strong lens system.
We discuss these two scenarios in Section 4. A third

scenario, which we find highly implausible, is that the
foreground galaxy is at _z_ = 4 _._ 0148, and that the blue
emission is coming from a background galaxy. Gravitational lenses beyond _z_ _>_ 2 are exceedingly rare, even in
forecasts of gravitational lens populations in the era of
JWST (e.g. Hogg et al. 2025).


4. ANALYSIS


To determine whether the CRG is a ring galaxy or a
case of gravitational lensing, we employ the `bagpipes`
software (Carnall et al. 2018) to model the SED of
the total galaxy and individual clumps along the ring
using multi-band photometry. For this analysis, we
utilize the HST ACS F606W and F814W bands, and
the JWST NIRCam F090W, F115W, F150W, F200W,
F277W, F356W, and F444W bands. The HST ACS
PSFs were generated from a publicly available repository of pre-prepared PSF models [6] (see also Rhodes et al.
2007), and resampled from a pixel size of 0.03 _[′′]_ to 0.02 _[′′]_ .
For the JWST NIRCam PSFs, we use the `stpsf` (formerly `WebbPSF;` Perrin et al. 2014) Python software
package to generate simulated point-spread functions
(PSFs) for each JWST band, oversampling the PSF to
match a target pixel size of 0.02 _[′′]_ . Because the F444W
band has the lowest spatial resolution, with a FWHM
_∼_ 0 _._ 16 _[′′]_, we create a shared kernel between each respective band’s PSF via the `psf.matching` sub-module in
`photutils` (Bradley et al. 2020) before convolving the
F444W-matched kernel with each band of observations.

We construct four separate apertures for the photometric analysis. One aperture surrounds the red center
of the galaxy, and three of them (A, B, C) are centered
on bright clumps along the ring. These apertures all
have a radius of 0.08 _[′′]_, with the aperture size roughly
corresponding to the lowest resolution element. We additionally apply a wide aperture that covers the entire
size of the system, covering a radius of 0.48 _[′′]_ .
For this analysis, we employ a delayed star-formation
history model in `bagpipes`, consisting of six parameters:


6 [https://astro.dur.ac.uk/](https://astro.dur.ac.uk/~rjm/acs/PSF/) _∼_ rjm/acs/PSF/

5


**Figure** **2.** 2 _[′′]_ cutouts of the ring galaxy as observed by HST ACS (F606W and F814W) and JWST NIRCam (F090W, F115W,
F150W, F200W, F277W, F356W, and F444W) at their native resolutions. The bottom-right cutout panel shows a rescaled
RGB image from the NIRCam data using F277W (red), F150W (green), and F090W (blue) to further highlight the red center
vs. blue ring. The magenta box shows the region from which the NIRSpec PRISM data were taken. These data products (2D
spectrum and integrated 1D spectrum) are shown in the bottom half of the figure. We have scaled the contrast in the cutouts
and 2D spectra to highlight important features, showing a red continuum exhibiting strong emission lines from a source at
_z_ = 4 _._ 0148, with emission lines that appear to encompass the spatial extent of the continuum source. The vertical dashed lines
indicate the location of expected emission lines at _z_ = 4 _._ 0148, and are included with annotations to demonstrate a match with
the spectroscopic redshift of the galaxy.



stellar mass log 10 ( _M_ _⋆_ _/M_ _⊙_ ), star-formation rate (SFR),
dust attenuation ( _A_ _V_ ) as characterized in Calzetti
et al. (2000), the system age, metallicity ( _Z/Z_ _⊙_ ), and
the ionization parameter ( _U_ ) which controls a simple
model of nebular emission. The photometric fitting
is performed using nested sampling, specifically using
`nautilus` (Lange 2023), as implemented in `bagpipes` .
We additionally apply a systematic error of 5% in
quadrature to the photometric measurements before
performing SED modeling.



We first consider a case in which the redshift is allowed to vary from 0 _<_ _z_ _<_ 5. In this scenario, we
find agreement between the fitted redshifts of the clumps
(3 _._ 89 _< z_ _<_ 4 _._ 19), the fitted redshift of the total system
( _z_ phot = 3 _._ 92 [+0] _−_ 0 _[.]_ _._ [10] 07 [),] [and] [the] [spectroscopic] [redshift] [from]
CANUCS ( _z_ spec = 4 _._ 0148). We emphasize that for this
exercise, we have employed a rather simple photometric
model, and as such we cannot place strong constraints
on certain parameters (e.g., age, metallicity). Even so,
this model strengthens the argument for the CRG being
a ring galaxy at _z_ _≈_ 4. We then consider a model where

6


**Figure** **3.** **Top:** 2 _[′′]_ cutouts of HST ACS and JWST NIRCam imaging, after matching the spatial resolution to F444W. The
bottom-right cutout is the RGB image from Figure 1 at native NIRCam resolution. The scale bar in the RGB cutout applies to
all panels. Circles in the RGB panel mark the five apertures used for the multi-band photometry and SED modeling: clumps
A (red), B (blue), and C (green), the center (orange) and the total flux (white, dashed line). The magenta rectangle indicates
the slit for the spectra in Figure 2. **Bottom:** Flux density versus observed wavelength within each aperture, as color coded in
the top panel. A 5% flux uncertainty was multiplied in quadrature to each photometric point before SED fitting. The best-fit
SED models from `bagpipes`, assuming _z_ = 4 _._ 0148 for all apertures, are shown as solid lines, demonstrating excellent agreement
between the photometry and the spectroscopic redshift from CANUCS (Sarrouh et al. 2026).



the redshift is fixed at _z_ = 4 _._ 0148. In this case, we find a
total star-formation rate (SFR) = 140 _−_ [+20] 30 [M] _[⊙]_ [yr] _[−]_ [1] [and]
log 10 ( _M_ _⋆_ _/_ M _⊙_ ) = 10 _._ 41 [+0] _−_ 0 _[.]_ _._ [11] 13 [.] The results of the SED
modeling are shown in Figure 3.
In total, the three main clumps along the ring have
roughly one third the mass of the system’s central emission, but have a higher SFR by over a factor of 2. The
bulk of the stellar mass and SFR comes from the wider

galaxy that is much more prominent in the redder JWST
imaging (i.e., redward of F200W). It is also seen in Figure 3 that the three clumps have different colors; this
is not easily explainable by gravitational lensing without the inclusion of differential dust reddening. While
we again emphasize that `bagpipes` cannot strongly constrain ages, as evidenced by the large uncertainties on
this parameter (Appendix Table 1), the central emission is much older (1 _._ 0 [+0] _−_ 0 _[.]_ _._ [3] 3 [–1] _[.]_ [2] _−_ [+0] 0 _[.]_ _._ [2] 3 [Gyr] [for] [the] [fitted]
vs. fixed-redshift models, respectively) than the clumps



along the ring (≲400 Myr with large uncertainties). If
the CRG is indeed a collisional ring galaxy, the progenitor galaxy would have had to form around _z_ ≳ 9 with
the ring-forming collision taking place around _z_ _≃_ 5 _−_ 6
or later (i.e., _z_ _<_ 5).
We apply a similar modeling approach to the five companions on the outskirts of the system, whose locations
are shown in Figure 4. To figure out where to place apertures, we first remove the foreground light in F277W, using the `GALFIT` software (Peng et al. 2002) to fit a single
S`ersic profile with _R_ _e_ _∼_ 0 _._ 21 _[′′]_, _n_ _∼_ 1 _._ 2, and _b/a_ _∼_ 0 _._ 7
after masking the faint companions. We then extend
the parameter priors in our `bagpipes` model to allow
for low-redshift and high-redshift solutions. Of the five
companions visible in Figure 4, we find that two have
photometric redshifts in agreement with the spectroscopic redshift of the system; both of these lie along an
apparent tidal arm visible in F200W and longer wave

7


**Figure** **4.** **Left:** Best-fit SED models (median and 1 _σ_ error) from photometry of two companions on the outskirts of the CRG
with photometric redshifts that are similar to the spectroscopic redshift of the CRG. **Right:** Model-subtracted, 2 _[′′]_ cutout of
the F277W image. The subtracted emission is modeled as a 2D S´ersic profile. The image scaling is tuned to highlight the
nearby companions and the arm-like tidal feature extending from the edge of the ring. The locations and aperture sizes used
for possible companion galaxies are indicated by the dashed circles. The two clumps with _z_ phot _∼_ 4 are colored red, as in the
right panels, while the other clumps, colored in blue, have _z_ phot _∼_ 1 _._ 0 _−_ 1 _._ 5, and are most likely foreground sources.



length bands. The first companion at the end of this
tail has _z_ phot = 4 _._ 24 [+0] _−_ 0 _[.]_ _._ [07] 07 [,] [log(] _[M]_ _[⋆]_ _[/]_ [M] _[⊙]_ [)] [=] [7] _[.]_ [74] [+0] _−_ 0 _[.]_ _._ [14] 16 [,]
_A_ _V_ = 0 _._ 84 [+0] _−_ 0 _[.]_ _._ [08] 10 [,] [and] [SFR] [=] [0] _[.]_ [5] [+0] _−_ 0 _[.]_ _._ [0] 1 [M] _[⊙]_ [yr] _[−]_ [1] [.] The
second companion, lying in the middle of the tail, has
_z_ phot = 4 _._ 30 [+0] _−_ 0 _[.]_ _._ [11] 11 [,] [log(] _[M]_ _[⋆]_ _[/]_ [M] _[⊙]_ [)] [=] [8] _[.]_ [03] [+0] _−_ 0 _[.]_ _._ [10] 12 [,] _[A]_ _[V]_ =
0 _._ 85 [+0] _−_ 0 _[.]_ _._ [11] 10 [, and SFR = 0] _[.]_ [4] _−_ [+0] 0 _[.]_ _._ [1] 1 [M] _[⊙]_ [yr] _[−]_ [1] [.] [The other three]
sources have photometric redshifts that are consistent
with with _z_ _≃_ 1 _._ 0 _−_ 1 _._ 5. However, to confirm whether
any or all of these companions are part of this system, we
require high-resolution (spectral and spatial) follow-up
observations.


4.1. _Is_ _this_ _system_ _a_ _gravitational_ _lens?_


Until now we have only demonstrated abundant circumstantial evidence pointing to the CRG being a ring
galaxy at _z_ _≃_ 4. However, we do not have the requisite
observational data to prove the ring galaxy hypothesis conclusively. Therefore, in this section we consider
the second possible scenario, where the red center is an
“early type” foreground lens at a lower redshift.
In order to consider the gravitational lensing hypothesis, we first attempt to probe diffuse starlight near the
center of the “lens” with which we can correct photometry for accurate stellar masses and SFR. This requires
us to subtract the ring from the imaging of at least one
band. The F182M filter covers the [O II ] line at restframe 3727A [˚] (assuming emission at _z_ = 4 _._ 0148), and
by assuming that the [O II ] emission mostly arises from
the ring, and that the spatial distribution of the stars
and ionized gas within the ring are morphologically similar, we can attempt to get a view of the central emission
only. We multiply the F182M imaging by a factor of 1.1,



before subtracting it from the F200W imaging, to create
a ring-subtracted image with only central emission plus
a diffuse component remaining; the resulting image is
shown in the right panel of Figure 5. We determine a
corrective factor of 1.87 by comparing the total flux in
the ring subtracted image within a 0 _._ 32 _[′′]_ -radius aperture
to the measured F200W photometry in a 0 _._ 08 _[′′]_ -radius
aperture. We lastly apply this factor to all photometric
measurements within the central component.
With this “corrected” photometry, we then perform an
alternate run of the photometric fitting with `bagpipes` .
We consider a foreground source with a redshift between
0 _._ 1 _<_ _z_ _<_ 2 _._ 0, and an age between 1 Gyr and 5 Gyr,
with other parameters remaining the same. The resulting fit yields _z_ fit = 1 _._ 66 _±_ 0 _._ 01; in this scenario, the
“foreground” galaxy has a log( _M_ _⋆_ _/_ M _⊙_ ) = 9 _._ 14 _±_ 0 _._ 02
and SFR = 3 _._ 2 [+0] _−_ 0 _[.]_ _._ [1] 2 [M] _[⊙]_ [yr] _[−]_ [1] [,] [respectively.] [We] [also] [ob-]
tain a dust extinction of _A_ _V_ _≈_ 1 _._ 94 [+0] _−_ 0 _[.]_ _._ [04] 05 [,] [which] [may]
associate the detection of dust continuum with the lens

in a lensing scenario. In Figure 5 we compare the uncorrected photometric model at _z_ = 1 _._ 66 to the photometric
model determined for the collisional ring galaxy explanation, along with a panel showing the aperture used for
“correcting” the foreground lens for physical parameter
estimation. The former solution generally shows agreement with the photometric data redward of 2 micron,
whereas the bluer wavelength bands show much better
agreement to the ring galaxy explanation. The former
also predicts a strong Pa- _α_ feature at _λ_ obs _≃_ 5 _._ 0 _µ_ m
which does not appear in the NIRSpec PRISM data.

8


**Figure** **5.** **Left:** Flux density versus observed wavelength, plotting photometric points from the two HST and seven JWST
wide-filter images in the green squares. These data are taken from an aperture corresponding to the “center” shown in Figure
3 (and the green circle in the right panel). The orange and blue spectra represent `bagpipes` models of a galaxy clump at
_z_ = 4 _._ 0148 versus a foreground gravitational lens with a best-fit redshift of _z_ = 1 _._ 66. The _z_ _≃_ 4 solution better describes the
photometry, and the predicted source SED at _z_ _≃_ 1 _._ 7 exhibits a number of lines between 3 _._ 2 _−_ 5 _._ 0 _µ_ m that are not found in the
NIRSpec data (see Figure 2). **Right:** A scaled version of F182M imaging subtracted from the F200W imaging; we calculate a
“corrective factor”, accounting for diffuse starlight near the “center” of the galaxy, from the flux enclosed within the magenta
aperture.



To further assess the lensing hypothesis, we do not
attempt to perform detailed gravitational lens modeling, primarily because a lens modeling failure would not
necessarily mean that the system is not a galaxy-galaxy
lens. Instead, we make a simple calculation to assess
the plausibility of the system as a galaxy-galaxy lens.
In the thin lens approximation of gravitational lensing,
the projected mass enclosed within an Einstein ring is
defined as



2 2
_c_
_M_ _E_ = _[θ]_ _[E]_



(1)
_D_ _SL_



_c_ _D_ _S_ _D_ _L_


4 _G_ _D_



( _z_ lens _>_ 1) lenses, with ratios of 0.32 and 0.31 in Shuntov
et al. (2025) ( _z_ lens _∼_ 2 _._ 0) and Adams et al. (2025)
( _z_ lens = 1 _._ 26), respectively. This problem, overall, weakens the case for the CRG being a gravitational lens.
Considering all of the above, we believe that the CRG is
more likely a high-redshift ring galaxy (at _z_ = 4 _._ 0148)
than a gravitationally lensed system.


5. DISCUSSION


5.1. _Comparison_ _to_ _high-redshift_ _ring_ _galaxy_ _candidates_


With the above analysis in mind, we now turn our attention to the small but growing sample of high-redshift
ring galaxies (Yuan et al. 2020; Liu et al. 2023; Nestor
Shachar et al. 2025; Li et al. 2026; Khoram et al. 2026;
Perna et al. 2025) for comparison to this work. With
a radius of _∼_ 0 _._ 25 _[′′]_ = 1 _._ 8 kpc, the galaxy studied in
this work is smaller in size to those studied in previous works, whose characteristic rings vary in radii from
about 3 _−_ 10 kpc. An important similarity between our
work and high-redshift ring galaxies is that these rings
are mostly comprised of several star-forming clumps.
Liu et al. (2023); Nestor Shachar et al. (2025); Perna
et al. (2025) explicitly characterize their rings as clumpy,
and in Li et al. (2026), the “Cosmic Owl” comprised of
two interacting collisional ring galaxies, a starbursting
clump serves as the “beak”. The fact that the system
studied in this work can be characterized as a clumpy
ring does not necessarily mean that the ring was formed
by a collision; it is well known that clumps generally
form due to disk fragmentation driven by gravitational



defining _θ_ _E_ as the Einstein radius, _D_ _S_ _, D_ _L_ as the cosmological distances to the background source and foreground lens, respectively, and _D_ _SL_ as the distance between source and lens. A source redshift _z_ = 4 _._ 0148,
lens redshift _z_ = 1 _._ 66, and Einstein radius _θ_ _E_ = 0 _._ 25 _[′′]_

implies a projected _M_ _E_ = 3 _._ 9 _×_ 10 [10] _M_ _⊙_ .
Dividing the stellar mass determined above ( _M_ _⋆_ =
1.4 _×_ 10 [9] _M_ _⊙_ ) by the projected mass implies a stellarto-total mass ratio _≈_ 0 _._ 04. This is a very low fraction; it has been argued that nearby dwarf galaxies
(i.e., less massive than the source studied in this work)
mostly have systematically large fractions of dark matter across all measured radii (e.g. Oh et al. 2011), albeit
with lower dark matter to total mass fractions ( _∼_ 0 _._ 7)
than in this case (≳ 95%). Estimating a more conservative Einstein radius of 0.2 _[′′]_ does not solve this problem,
yielding a stellar-to-total mass ratio _≈_ 0.06. In both
cases, the stellar-to-total mass ratio is lower than what
has been found in similar JWST-selected high-redshift

9


**Figure** **6.** The star-forming main-sequence (SFMS) for a comparison sample of low-redshift ring galaxies (Shimakawa et al.
2024) and a selected sample of high-redshift ring galaxies (Yuan et al. 2020; Liu et al. 2023; Nestor Shachar et al. 2025; Perna
et al. 2025), including the galaxy studied in this work. We use the parametrized main sequences from Popesso et al. (2023) for
further comparison. We find that observed high-redshift ring galaxies to date have much higher SFR than their lower-redshift
analogs, and lie on or above the SFMS at _z_ = 2 _−_ 4.



instabilities (Toomre 1964), and Dekel et al. (2020) argued that most clumpy rings ( _z_ _<_ 4) do not directly
arise from galaxy mergers in high-redshift galaxy simulations (cf. Elagali et al. 2018). The clumpy nature of
high-redshift rings, nonetheless, is an indicator of gravitational instability along the ring.
An important difference between the CRG and other
high-redshift rings is that the latter generally show clear
evidence for a companion/collider galaxy that could
have triggered ring formation. The system reported by
Liu et al. (2023) is notable in that the ring galaxy is gravitationally lensed, making the search for a companion
difficult (the ring morphology is determined via forward
modeling a gravitational lens model to obtain a source
plane morphology). In the case of the CRG, the nearest galaxy in the MACS0416 field with a spectroscopic
redshift (CANUCS ID 3100641, _z_ = 3 _._ 9978) lies _≈_ 18 _[′′]_

away, corresponding to a physical distance of _≈_ 125 kpc;
as such, it is an unlikely candidate for the dynamical
perturber of the ring galaxy. As for the CRG, we have
henceforth shown in Section 4 and Figure 4 that two
faint companions are aligned with a tidal tail that appears to extend from the CRG. As these candidates are
low-mass (≲ 10 [8] M _⊙_ ) compared to the mass of the ring
galaxy, it is unlikely that these objects triggered ring formation; a typical assumption for collisional ring galaxy
formation is that the ratio of bullet-to-disk mass should
be _∼_ 0 _._ 1 or greater (e.g., D’Onghia et al. 2008). Another
possible candidate for the galaxy bullet, despite its low
mass, is clump “A” (log( _M_ _⋆_ _/_ M _⊙_ ) = 8 _._ 88 [+0] _−_ 0 _[.]_ _._ [10] 12 [),] [whose]
photometry reveals a starkly different and bluer color
compared to the other clumps along the ring. Alternatively, it is possible that line-of-sight effects are hiding



the “bullet” (e.g., the galaxy is behind the CRG) or that
the “bullet” was destroyed or dissipated post-collision.
We lastly attempt to compare the modeled physical
properties of the CRG to the works cited above, and
with a larger sample of local ring galaxies. For the local
galaxy sample, we utilize a catalog of ring galaxies from
the GALAXY CRUISE survey (Shimakawa et al. 2024),
placing a cut on redshift between 0 _._ 07 _<_ _z_ _<_ 0 _._ 2, SFR
_>_ 10 _[−]_ [3] M _⊙_ yr _[−]_ [1], and only selecting galaxies with a ring
probability _p >_ 0 _._ 99. We then crossmatch these galaxies
to the GALEX-SDSS-WISE Legacy Catalog (GSWLC;
Salim et al. 2016, 2018) for SFR and stellar masses derived from `CIGALE` (Boquien et al. 2019), returning a final sample of 1,021 local ring galaxies. We plot the SFR
versus stellar mass (i.e., the star-forming main sequence)
in Figure 6. It is seen that the stellar mass and SFR for
our galaxy are similar to those of other high-redshift ring
galaxies. We compare both samples to parametrized
star-forming main sequences at _z_ = 0 _._ 2 _,_ 2 _._ 0 _,_ 4 _._ 0 using
the functional form from Popesso et al. (2023), corresponding to characteristic redshifts for the local and
high-redshift samples respectively. In the local sample,
many galaxies lie below the star-forming main sequence
at _z_ _≈_ 0 _._ 2; this is not surprising, as it has been argued in
some works (e.g., Kelvin et al. 2018; Smith et al. 2022;
Fernandez et al. 2024) that ring galaxies are overrepresented in the “green valley” compared to other morphological classes of galaxies. The high-redshift ring galaxies (including the CRG), conversely, are shown to lie
on or above the star-forming main sequence at their respective redshifts, although this is most likely a selection
effect.

10


**Figure** **7.** **Left:** Source versus lens redshift for a sample of well-characterized, optically selected strong lensing systems (SLACS,
BELLS, SL2S; Bolton et al. 2008; Brownstein et al. 2012; Sonnenfeld et al. 2013, respectively) as compiled in Tan et al. (2024),
along with a recent release of strong lenses from the AGEL survey (Barone et al. 2026) and JWST-selected lenses in the PEARLS
NEP time domain field (Ferrami et al. 2026). The lensing solution for the CRG is in excellent agreement with the existing
parameter space for strong lenses. **Right:** Einstein radius for SLACS, BELLS, SL2S, PEARLS NEP, and over 400 candidate
gravitationally lensed systems in the COWLS program (Nightingale et al. 2025). Assuming the CRG is not a lens, it cannot be
distinguished from a selection in this parameter space, where it is similar to high-ranked and low-ranked lens candidates.



5.2. _Implications_ _of_ _ring_ _galaxies_ _for_ _future_
_gravitational_ _lens_ _searches_


Finally, we discuss the impact of high-redshift ring
galaxies, such as the one studied in this work, as a
source of contamination in current and future surveys
for gravitational lenses. It is anticipated that _O_ (10 [5] )
galaxy-galaxy scale gravitational lenses will be discovered in future large sky surveys (e.g., Collett 2015).
With the launch of the Euclid mission, early searches
for these systems are already underway with what has
been called the Strong Lensing Discovery Engine (e.g.,
Euclid Collaboration et al. 2025a). It is seen in Euclid
Collaboration et al. (2025b) that a number of highlyranked strong lens candidates, as scored and detected
by a fine-tuned pretrained machine learning model, appear to be candidate ring galaxies. While JWST is not
optimized, by design, to discover many strong lenses, it
has been used to characterize many hundreds of galaxygalaxy scale gravitational lenses in surveys such as the
COSMOS-Web Lens Survey (COWLS; see Nightingale
et al. 2025; Mahler et al. 2025; Hogg et al. 2025).
In Figure 7 we consider how the “lensing” scenario
compares to samples of gravitational lenses from the lit


erature. For this exercise we consider canonical samples
of optical gravitational lenses, such as SLACS (Bolton
et al. 2008), BELLS (Brownstein et al. 2012), and SL2S
(Sonnenfeld et al. 2013), the second data release from
the AGEL survey (Barone et al. 2026), and four gravitational lenses from the PEARLS North Ecliptic Pole
Time Domain Field (Ferrami et al. 2026). The lensing solution for the CRG is perfectly plausible within
the parameter space of source versus lens redshift. We
also compare our lensing scenario to the sample of over
400 galaxy-galaxy gravitational lens candidates from
COWLS, as presented and scored in Nightingale et al.
(2025). Here too, the lensing solution is in excellent agreement with both high-ranking and low-ranking
gravitational lens candidates from the COWLS survey,
which might suggest that some systems in COWLS, like
the CRG, are ring galaxies uncovered by JWST.
Compared to existing optical surveys, JWST is able to
probe lower mass gravitational lenses at higher redshift,
but it does not appear possible to distinguish lenses from
non-lenses based on smaller Einstein radii. From all of

the above, we infer that galaxies dominated by a ring
morphology remain a significant contaminant in searches

for gravitational lenses, which poses challenges to current and future optical and near-infrared surveys.


6. CONCLUSION


In this work, we have performed a follow-up investigation of a gravitational lens candidate on the periphery
of the MACS0416 cluster field (Diego et al. 2024). Our
main findings are:


1. The candidate ring galaxy (CRG) is spectroscopically identified at _z_ = 4 _._ 0148 via NIRSpec PRISM
data from the CANUCS DR1 (Sarrouh et al.
2026). The identification is confirmed due to multiple strong emission line features e.g. Ly _α_, H _α_,
He I 1.083 _µ_ m, [S II ], and [S III ]. The galaxy is characterized by a blue ring surrounding a red center;
the ring is comprised of three main clumps and
has a radius of 0 _._ 25 _[′′]_ . Additionally, there are five
faint companions within 1 _[′′]_ from the center of the
galaxy, and an apparent tidal feature that extends
from the edge of the ring. There is also a faint,
_≈_ 3 _σ_ dust continuum detection of the CRG from

archival ALMA observations.


2. We derive multi-band photometry from two HST
ACS wideband filters (F606W and F814W) and
seven JWST NIRCam wideband filters (F090W
to F444W) for the three main clumps along the
ring, the center of the galaxy, and the whole system. By applying a simple star-formation history
model from `bagpipes` to the photometry, we obtain photometric redshifts for the three clumps
and total emission that are in good agreement
( _z_ _∼_ 3 _._ 89 _−_ 4 _._ 19) with the spectroscopic redshift
from NIRSpec PRISM. When fixing _z_ = 4 _._ 0148
to the photometric fits, we find a (log _M_ _⋆_ _/_ M _⊙_ )
= 10 _._ 41 [+0] _−_ 0 _[.]_ _._ [11] 13 [and] [SFR] [=] [140] [+20] _−_ 30 [M] _[⊙]_ [yr] _[−]_ [1] [for] [the]
CRG.


3. We cannot conclusively rule out a lensing explanation for the CRG, and consider whether the
red central component could be a foreground lensing galaxy. After performing a crude subtraction
of the ring using medium-band JWST data, we
find that a galaxy SED with _z_ phot = 1 _._ 66 _±_ 0 _._ 01,
log _M_ _⋆_ _/_ M _⊙_ = 9 _._ 14 _±_ 0 _._ 02 and SFR = 3 _._ 2 [+0] _−_ 0 _[.]_ _._ [1] 2 [M] _[⊙]_
yr _[−]_ [1] achieves a fit to scaled photometry from the
central emission in the CRG. Such a galaxy would
require a very low stellar mass ratio ( _≈_ 5% of the
projected mass within the Einstein radius), making it a less plausible explanation.


4. Considering the CRG to be a ring galaxy, we
find that its estimated stellar mass, SFR from



11


`bagpipes`, along with the clumpy nature of the
ring, are comparable to other high-redshift (collisional) ring galaxies (e.g. Yuan et al. 2020; Liu
et al. 2023; Perna et al. 2025; Nestor Shachar
et al. 2025; Khoram et al. 2026) at _z_ _>_ 2. Unlike other high-redshift ring galaxies, however, the
CRG lacks an obvious candidate for the “bullet”
(i.e., merger progenitor) that triggered ring formation. We identify several “bullet” candidates, including a spectroscopically confirmed galaxy over
100 kpc away, two companions lying within the
tidal tail, and the brightest companion along the
ring. We find that high-redshift ring galaxies detected with JWST generally lie along or above the
star-forming main sequence (SFMS; e.g. Popesso
et al. 2023), compared to a sample of local ring
galaxies that mostly lie below the SFMS.


We conclude that the CRG is most likely a ring galaxy
at _z_ = 4 _._ 0148, specifically a collisional ring formed in the
aftermath of a merger event. If this is confirmed with
follow-up observations, this system would be the most
distant ring galaxy ever reported in the literature. NIRSpec IFU observations, aiming to spatially resolve the
H _α_ line across the entire galaxy and its nearby environment, would be the most straightforward way to confirm
the nature of the CRG [7] .

As ring galaxies are known to be a contaminant in
ongoing strong lensing surveys (e.g. Euclid Collaboration et al. 2025b), we predict that observatories such as
JWST and Euclid will provide statistically significant
samples of ring galaxies out to high redshifts. Future
studies of unusual galaxy morphologies at high-redshift
should consider that some ringed systems may be real
ring galaxies, and not strong lenses. Larger, more detailed studies are required to determine the true abundances of these galaxies and how they may contaminate
strong lens selections.


ACKNOWLEDGEMENTS


We thank the anonymous referee for their feedback,
which strengthened this work. The JWST data is available at MAST: doi: [10.17909/qydg-zt87.](https://doi.org/10.17909/qydg-zt87) DV thanks
Kedar A. Phadke for providing sample scripts that
helped enable the photometric analysis in this work.
This material is based upon work supported by the Na

7 The [C II ] fine-structure line at 158 _µ_ m would be a natural line
to target in this galaxy using the Atacama Large Millimeter/submillimeter Array (ALMA); however, it would emit at an
observed frequency of 379 GHz, which is outside the frequency
coverage of the Band 7 (275 _−_ 373 GHz) and Band 8 (385 _−_ 500
GHz) receivers on ALMA.

12


tional Science Foundation Graduate Research Fellowship under Grant No. DGE 2146756. [˜] This work is based
in part on observations made with the NASA/ESA/CSA
James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes
at the Space Telescope Science Institute, which is operated by the Association of Universities for Research
in Astronomy, Inc., under NASA contract NAS 503127 for JWST. These observations are associated

with programs# 1176 and 1208. This paper makes
use of the following ALMA data: ADS/JAO.ALMA #
2018.1.00035.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS
(Japan), together with NRC (Canada) and NSC and
ASIAA (Taiwan) in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO, and NAOJ. This research has made
use of NASA’s Astrophysics Data System and Astrophysics Data System Bibliographic Services. This
work made use of the MyFilter web tool (Li 2023)



for data analysis. This research has made use of the
NASA/IPAC Extragalactic Database, which is funded
by the National Aeronautics and Space Administration
and operated by the California Institute of Technology.
This research has made use of the SIMBAD database,
CDS, Strasbourg Astronomical Observatory, France.
I.S. acknowledges support from STFC (ST/X001075/1).
RAW and SHC acknowledge support from NASA
JWST Interdisciplinary Scientist grants NAG5-12460,
NNX14AN10G and 80NSSC18K0200 from GSFC. This
work is sponsored (in part) by the Chinese Academy
of Sciences (CAS) through a grant to the CAS South
America Center for Astronomy. This work is supported
by the China Manned Space Program with grant no.
CMS-CSST-2025-A07. C.C. is supported by Chinese
Academy of Sciences South America Center for Astronomy (CASSACA) Key Research Project E52H540301.
PSK acknowledges financial support from the Knut and
Alice Wallenberg Foundation.



REFERENCES



Adams, N. J., Ferrami, G., Westcott, L., et al. 2025,

MNRAS, 543, 3535, doi: [10.1093/mnras/staf1518](http://doi.org/10.1093/mnras/staf1518)

Appleton, P. N., & Struck-Marcell, C. 1987, ApJ, 312, 566,

doi: [10.1086/164902](http://doi.org/10.1086/164902)

—. 1996, FCPh, 16, 111

Barone, T. M., G. C., K. V., Tran, K.-V., et al. 2026, AJ,

171, 57, doi: [10.3847/1538-3881/ae1f86](http://doi.org/10.3847/1538-3881/ae1f86)

Binney, J., & Tremaine, S. 2008, Galactic Dynamics:

Second Edition

Bolton, A. S., Burles, S., Koopmans, L. V. E., et al. 2008,

ApJ, 682, 964, doi: [10.1086/589327](http://doi.org/10.1086/589327)

Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A,

622, A103, doi: [10.1051/0004-6361/201834156](http://doi.org/10.1051/0004-6361/201834156)

Bradley, L., Sip˝ocz, B., Robitaille, T., et al. 2020,

astropy/photutils: 1.0.0, 1.0.0, Zenodo,
doi: [10.5281/zenodo.4044744](http://doi.org/10.5281/zenodo.4044744)

Brownstein, J. R., Bolton, A. S., Schlegel, D. J., et al. 2012,

ApJ, 744, 41, doi: [10.1088/0004-637X/744/1/41](http://doi.org/10.1088/0004-637X/744/1/41)

Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2024,

JWST Calibration Pipeline, 1.13.4, Zenodo,

doi: [10.5281/zenodo.10569856](http://doi.org/10.5281/zenodo.10569856)

Buta, R. 1999, Ap&SS, 269-270, 79,

doi: [10.1023/A:1017059621651](http://doi.org/10.1023/A:1017059621651)

Buta, R., & Combes, F. 1996, FCPh, 17, 95

Buta, R. J., Sheth, K., Athanassoula, E., et al. 2015, ApJS,

217, 32, doi: [10.1088/0067-0049/217/2/32](http://doi.org/10.1088/0067-0049/217/2/32)

Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ,

533, 682, doi: [10.1086/308692](http://doi.org/10.1086/308692)



Carnall, A. C., McLure, R. J., Dunlop, J. S., & Dav´e, R.

2018, MNRAS, 480, 4379, doi: [10.1093/mnras/sty2169](http://doi.org/10.1093/mnras/sty2169)


Collett, T. E. 2015, ApJ, 811, 20,

doi: [10.1088/0004-637X/811/1/20](http://doi.org/10.1088/0004-637X/811/1/20)


Comer´on, S., Salo, H., Laurikainen, E., et al. 2014, A&A,

562, A121, doi: [10.1051/0004-6361/201321633](http://doi.org/10.1051/0004-6361/201321633)


Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA:

The Cube Analysis and Rendering Tool for Astronomy,

2.0.0, Zenodo, doi: [10.5281/zenodo.3377984](http://doi.org/10.5281/zenodo.3377984)


de Vaucouleurs, G. 1959, Handbuch der Physik, 53, 275,

doi: [10.1007/978-3-642-45932-0](http://doi.org/10.1007/978-3-642-45932-0_7) ~~7~~


Dekel, A., Lapiner, S., Ginzburg, O., et al. 2020, MNRAS,

496, 5372, doi: [10.1093/mnras/staa1713](http://doi.org/10.1093/mnras/staa1713)


Diego, J. M., Adams, N. J., Willner, S. P., et al. 2024,

A&A, 690, A114, doi: [10.1051/0004-6361/202349119](http://doi.org/10.1051/0004-6361/202349119)


D’Onghia, E., Mapelli, M., & Moore, B. 2008, MNRAS,

389, 1275, doi: [10.1111/j.1365-2966.2008.13625.x](http://doi.org/10.1111/j.1365-2966.2008.13625.x)


Duan, Q., Conselice, C. J., Li, Q., et al. 2025, MNRAS,

540, 774, doi: [10.1093/mnras/staf638](http://doi.org/10.1093/mnras/staf638)


Dudzeviˇci¯ut˙e, U., Smail, I., Swinbank, A. M., et al. 2020,

MNRAS, 494, 3828, doi: [10.1093/mnras/staa769](http://doi.org/10.1093/mnras/staa769)


Ebeling, H., Edge, A. C., & Henry, J. P. 2001, ApJ, 553,

668, doi: [10.1086/320958](http://doi.org/10.1086/320958)


Elagali, A., Lagos, C. D. P., Wong, O. I., et al. 2018,

MNRAS, 481, 2951, doi: [10.1093/mnras/sty2462](http://doi.org/10.1093/mnras/sty2462)


Elmegreen, D. M., & Elmegreen, B. G. 2006, ApJ, 651, 676,

doi: [10.1086/507863](http://doi.org/10.1086/507863)

Euclid Collaboration, Walmsley, M., Holloway, P., et al.

2025a, arXiv e-prints, arXiv:2503.15324,

doi: [10.48550/arXiv.2503.15324](http://doi.org/10.48550/arXiv.2503.15324)


Euclid Collaboration, Lines, N. E. P., Collett, T. E., et al.

2025b, arXiv e-prints, arXiv:2503.15326,

doi: [10.48550/arXiv.2503.15326](http://doi.org/10.48550/arXiv.2503.15326)


Fernandez, J., Alonso, S., Mesa, V., & Duplancic, F. 2024,

A&A, 683, A32, doi: [10.1051/0004-6361/202245215](http://doi.org/10.1051/0004-6361/202245215)


Fernandez, J., Alonso, S., Mesa, V., Duplancic, F., &

Coldwell, G. 2021, A&A, 653, A71,

doi: [10.1051/0004-6361/202141208](http://doi.org/10.1051/0004-6361/202141208)


Ferrami, G., Adams, N. J., Westcott, L., et al. 2026,

MNRAS, 545, staf1991, doi: [10.1093/mnras/staf1991](http://doi.org/10.1093/mnras/staf1991)


Ford, H. C., Clampin, M., Hartig, G. F., et al. 2003, in

Society of Photo-Optical Instrumentation Engineers

(SPIE) Conference Series, Vol. 4854, Future EUV/UV

and Visible Space Astrophysics Missions and

Instrumentation., ed. J. C. Blades & O. H. W. Siegmund,

81–94, doi: [10.1117/12.460040](http://doi.org/10.1117/12.460040)


Fujimoto, S., Kohno, K., Ouchi, M., et al. 2024, ApJS, 275,

36, doi: [10.3847/1538-4365/ad5ae2](http://doi.org/10.3847/1538-4365/ad5ae2)


Hogg, N. B., Nightingale, J. W., He, Q., et al. 2025,

MNRAS, 544, 782, doi: [10.1093/mnras/staf1678](http://doi.org/10.1093/mnras/staf1678)


Hubble, E. P. 1926, ApJ, 64, 321, doi: [10.1086/143018](http://doi.org/10.1086/143018)


Jauzac, M., Cl´ement, B., Limousin, M., et al. 2014,

MNRAS, 443, 1549, doi: [10.1093/mnras/stu1355](http://doi.org/10.1093/mnras/stu1355)


Kelvin, L. S., Bremer, M. N., Phillipps, S., et al. 2018,

MNRAS, 477, 4116, doi: [10.1093/mnras/sty933](http://doi.org/10.1093/mnras/sty933)


Khoram, A. H., Belli, S., Nipoti, C., et al. 2026, ApJ, 998,

59, doi: [10.3847/1538-4357/ae23d0](http://doi.org/10.3847/1538-4357/ae23d0)


Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al.

2011, ApJS, 197, 36, doi: [10.1088/0067-0049/197/2/36](http://doi.org/10.1088/0067-0049/197/2/36)


Kormendy, J., & Kennicutt, Jr., R. C. 2004, ARA&A, 42,

603, doi: [10.1146/annurev.astro.42.053102.134024](http://doi.org/10.1146/annurev.astro.42.053102.134024)


Lange, J. U. 2023, MNRAS, 525, 3181,

doi: [10.1093/mnras/stad2441](http://doi.org/10.1093/mnras/stad2441)


Lavery, R. J., Remijan, A., Charmandaris, V., Hayes, R. D.,

& Ring, A. A. 2004, ApJ, 612, 679, doi: [10.1086/422420](http://doi.org/10.1086/422420)


Li, M. 2023, MyFilter: A Web Application for Interactive

Visualization of Astronomical Filter Transmission Curves

(1.0.0), Zenodo, doi: [10.5281/zenodo.1234567](http://doi.org/10.5281/zenodo.1234567)


Li, M., Emonts, B. H. C., Cai, Z., et al. 2026, ApJ, 999, 40,

doi: [10.3847/1538-4357/ae3c10](http://doi.org/10.3847/1538-4357/ae3c10)


Liu, D., F¨orster Schreiber, N. M., Genzel, R., et al. 2023,

ApJ, 942, 98, doi: [10.3847/1538-4357/aca46b](http://doi.org/10.3847/1538-4357/aca46b)


Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837,

97, doi: [10.3847/1538-4357/837/1/97](http://doi.org/10.3847/1538-4357/837/1/97)


Lynds, R., & Toomre, A. 1976, ApJ, 209, 382,

doi: [10.1086/154730](http://doi.org/10.1086/154730)



13


Madore, B. F., Nelson, E., & Petrillo, K. 2009, ApJS, 181,

572, doi: [10.1088/0067-0049/181/2/572](http://doi.org/10.1088/0067-0049/181/2/572)


Mahler, G., Nightingale, J. W., Hogg, N. B., et al. 2025,

MNRAS, 544, L8, doi: [10.1093/mnrasl/slaf088](http://doi.org/10.1093/mnrasl/slaf088)


Mann, A. W., & Ebeling, H. 2012, MNRAS, 420, 2120,

doi: [10.1111/j.1365-2966.2011.20170.x](http://doi.org/10.1111/j.1365-2966.2011.20170.x)


Merlin, E., Amor´ın, R., Castellano, M., et al. 2016, A&A,

590, A30, doi: [10.1051/0004-6361/201527513](http://doi.org/10.1051/0004-6361/201527513)


Nestor Shachar, A., Sternberg, A., Genzel, R., et al. 2025,

ApJ, 988, 182, doi: [10.3847/1538-4357/ade2d0](http://doi.org/10.3847/1538-4357/ade2d0)


Nightingale, J. W., Mahler, G., McCleary, J., et al. 2025,

MNRAS, 543, 203, doi: [10.1093/mnras/staf1253](http://doi.org/10.1093/mnras/staf1253)


Oh, S.-H., de Blok, W. J. G., Brinks, E., Walter, F., &

Kennicutt, Jr., R. C. 2011, AJ, 141, 193,

doi: [10.1088/0004-6256/141/6/193](http://doi.org/10.1088/0004-6256/141/6/193)


Parker, Q. A., Zijlstra, A. A., Stupar, M., et al. 2015,

MNRAS, 452, 3759, doi: [10.1093/mnras/stv1432](http://doi.org/10.1093/mnras/stv1432)


Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002,

AJ, 124, 266, doi: [10.1086/340952](http://doi.org/10.1086/340952)


Perna, M., Arribas, S., Costantin, L., et al. 2025, arXiv

e-prints, arXiv:2512.14874,

doi: [10.48550/arXiv.2512.14874](http://doi.org/10.48550/arXiv.2512.14874)


Perrin, M. D., Sivaramakrishnan, A., Lajoie, C.-P., et al.

2014, in Society of Photo-Optical Instrumentation

Engineers (SPIE) Conference Series, Vol. 9143, Space

Telescopes and Instrumentation 2014: Optical, Infrared,

and Millimeter Wave, ed. J. M. Oschmann, Jr.,

M. Clampin, G. G. Fazio, & H. A. MacEwen, 91433X,

doi: [10.1117/12.2056689](http://doi.org/10.1117/12.2056689)


Planck Collaboration, Aghanim, N., Akrami, Y., et al.

2020, A&A, 641, A6, doi: [10.1051/0004-6361/201833910](http://doi.org/10.1051/0004-6361/201833910)


Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS,

519, 1526, doi: [10.1093/mnras/stac3214](http://doi.org/10.1093/mnras/stac3214)


Postman, M., Coe, D., Ben´ıtez, N., et al. 2012, ApJS, 199,

25, doi: [10.1088/0067-0049/199/2/25](http://doi.org/10.1088/0067-0049/199/2/25)


Renaud, F., Athanassoula, E., Amram, P., et al. 2018,

MNRAS, 473, 585, doi: [10.1093/mnras/stx2360](http://doi.org/10.1093/mnras/stx2360)


Rhodes, J. D., Massey, R. J., Albert, J., et al. 2007, ApJS,

172, 203, doi: [10.1086/516592](http://doi.org/10.1086/516592)


Rieke, M. J., Kelly, D. M., Misselt, K., et al. 2023, PASP,

135, 028001, doi: [10.1088/1538-3873/acac53](http://doi.org/10.1088/1538-3873/acac53)


Rihtarˇsiˇc, G., Bradaˇc, M., Desprez, G., et al. 2025, A&A,

696, A15, doi: [10.1051/0004-6361/202451117](http://doi.org/10.1051/0004-6361/202451117)


Salim, S., Boquien, M., & Lee, J. C. 2018, ApJ, 859, 11,

doi: [10.3847/1538-4357/aabf3c](http://doi.org/10.3847/1538-4357/aabf3c)


Salim, S., Lee, J. C., Janowiecki, S., et al. 2016, ApJS, 227,

2, doi: [10.3847/0067-0049/227/1/2](http://doi.org/10.3847/0067-0049/227/1/2)


Sarrouh, G. T. E., Asada, Y., Martis, N. S., et al. 2026,

ApJS, 282, 3, doi: [10.3847/1538-4365/ae1611](http://doi.org/10.3847/1538-4365/ae1611)

14


Shimakawa, R., Tanaka, M., Ito, K., & Ando, M. 2024,

PASJ, 76, 191, doi: [10.1093/pasj/psae002](http://doi.org/10.1093/pasj/psae002)


Shuntov, M., Jin, S., Mercier, W., et al. 2025, A&A, 696,

L14, doi: [10.1051/0004-6361/202554273](http://doi.org/10.1051/0004-6361/202554273)


Smirnov, D. V., & Reshetnikov, V. P. 2022, MNRAS, 516,

3692, doi: [10.1093/mnras/stac2549](http://doi.org/10.1093/mnras/stac2549)


Smith, D., Haberzettl, L., Porter, L. E., et al. 2022,

MNRAS, 517, 4575, doi: [10.1093/mnras/stac2258](http://doi.org/10.1093/mnras/stac2258)


Sonnenfeld, A., Gavazzi, R., Suyu, S. H., Treu, T., &

Marshall, P. J. 2013, ApJ, 777, 97,

doi: [10.1088/0004-637X/777/2/97](http://doi.org/10.1088/0004-637X/777/2/97)



Steinhardt, C. L., Jauzac, M., Acebron, A., et al. 2020,

ApJS, 247, 64, doi: [10.3847/1538-4365/ab75ed](http://doi.org/10.3847/1538-4365/ab75ed)

Tan, C. Y., Shajib, A. J., Birrer, S., et al. 2024, MNRAS,
530, 1474, doi: [10.1093/mnras/stae884](http://doi.org/10.1093/mnras/stae884)

Theys, J. C., & Spiegel, E. A. 1977, ApJ, 212, 616,
doi: [10.1086/155084](http://doi.org/10.1086/155084)
Toomre, A. 1964, ApJ, 139, 1217, doi: [10.1086/147861](http://doi.org/10.1086/147861)

Windhorst, R. A., Cohen, S. H., Jansen, R. A., et al. 2023,

AJ, 165, 13, doi: [10.3847/1538-3881/aca163](http://doi.org/10.3847/1538-3881/aca163)

Yuan, T., Elagali, A., Labb´e, I., et al. 2020, Nature
Astronomy, 4, 957, doi: [10.1038/s41550-020-1102-7](http://doi.org/10.1038/s41550-020-1102-7)

15


APPENDIX


Here we include a table of three `bagpipes` model results, corresponding to three morphological explanations explored
in this work. The top row of Table 1 employs a blind photometric fit to determine whether the redshift of the ring and
the central emission is the same. The middle row of Table 1 contains the parameters used for analyzing the system
studied in this work as a (collisional) ring galaxy at _z_ = 4 _._ 0148. The bottom row of Table 1 considers the possibility of
the central emission arising from a dusty foreground galaxy between 0 _< z_ _<_ 2. In Table 2 we include the photometry
from HST and JWST to which the `bagpipes` models are fitted.


Aperture _z_ log( _M_ _⋆_ _/_ M _⊙_ ) SFR [M _⊙_ yr _[−]_ [1] ] _A_ _V_ [mag] Age [Myr] _Z/Z_ _⊙_

_z_ phot as free parameter
A 4 _._ 11 [+0] _−_ 0 _[.]_ _._ [05] 08 8 _._ 94 [+0] _−_ 0 _[.]_ _._ [13] 11 6 _._ 6 [+0] _−_ 0 _[.]_ _._ [5] 9 0 _._ 88 [+0] _−_ 0 _[.]_ _._ [07] 09 260 [+180] _−_ 100 0 _._ 74 [+0] _−_ 0 _[.]_ _._ [18] 21
B 4 _._ 19 [+0] _−_ 0 _[.]_ _._ [06] 07 9 _._ 19 [+0] _−_ 0 _[.]_ _._ [12] 11 12 _._ 7 [+0] _−_ 1 _[.]_ _._ [9] 3 1 _._ 44 [+0] _−_ 0 _[.]_ _._ [07] 09 240 [+160] _−_ 80 0 _._ 81 [+0] _−_ 0 _[.]_ _._ [13] 17
C 3 _._ 89 [+0] _−_ 0 _[.]_ _._ [11] 07 8 _._ 70 [+0] _−_ 0 _[.]_ _._ [12] 10 3 _._ 8 [+0] _−_ 0 _[.]_ _._ [3] 6 0 _._ 99 [+0] _−_ 0 _[.]_ _._ [08] 11 260 [+180] _−_ 90 0 _._ 94 [+0] _−_ 0 _[.]_ _._ [05] 09
Center 3 _._ 73 [+0] _−_ 0 _[.]_ _._ [06] 08 9 _._ 76 [+0] _−_ 0 _[.]_ _._ [06] 07 11 _._ 6 [+2] _−_ 1 _[.]_ _._ [5] 9 1 _._ 52 [+0] _−_ 0 _[.]_ _._ [10] 09 1000 [+300] _−_ 300 0 _._ 36 [+0] _−_ 0 _[.]_ _._ [23] 17
Total 3 _._ 92 [+0] _−_ 0 _[.]_ _._ [10] 07 10 _._ 35 [+0] _−_ 0 _[.]_ _._ [11] 11 146 [+14] _−_ 25 1 _._ 34 [+0] _−_ 0 _[.]_ _._ [10] 12 320 [+220] _−_ 110 0 _._ 71 [+0] _−_ 0 _[.]_ _._ [18] 21

_z_ phot = _z_ spec = 4 _._ 0148
A — 8 _._ 88 [+0] _−_ 0 _[.]_ _._ [10] 12 6 _._ 6 [+0] _−_ 0 _[.]_ _._ [4] 5 0 _._ 93 [+0] _−_ 0 _[.]_ _._ [06] 06 210 [+100] _−_ 80 0 _._ 77 [+0] _−_ 0 _[.]_ _._ [16] 19
B — 9 _._ 05 [+0] _−_ 0 _[.]_ _._ [12] 12 12 _._ 2 [+0] _−_ 1 _[.]_ _._ [8] 9 1 _._ 57 [+0] _−_ 0 _[.]_ _._ [05] 07 140 [+90] _−_ 50 0 _._ 84 [+0] _−_ 0 _[.]_ _._ [11] 19
C — 8 _._ 79 [+0] _−_ 0 _[.]_ _._ [13] 12 3 _._ 4 [+0] _−_ 0 _[.]_ _._ [5] 6 0 _._ 88 [+0] _−_ 0 _[.]_ _._ [08] 10 390 [+270] _−_ 150 0 _._ 95 [+0] _−_ 0 _[.]_ _._ [03] 07
Center — 9 _._ 86 [+0] _−_ 0 _[.]_ _._ [04] 05 11 [+2] _−_ 2 1 _._ 36 [+0] _−_ 0 _[.]_ _._ [09] 11 1200 [+200] _−_ 300 0 _._ 24 [+0] _−_ 0 _[.]_ _._ [18] 08
Total — 10 _._ 41 [+0] _−_ 0 _[.]_ _._ [11] 13 140 [+20] _−_ 30 1 _._ 28 [+0] _−_ 0 _[.]_ _._ [08] 10 390 [+240] _−_ 150 0 _._ 80 [+0] _−_ 0 _[.]_ _._ [13] 21

Central emission as speculated foreground lens
Center 1 _._ 66 [+0] _−_ 0 _[.]_ _._ [01] 01 9 _._ 14 [+0] _−_ 0 _[.]_ _._ [02] 02 3 _._ 2 [+0] _−_ 0 _[.]_ _._ [1] 2 1 _._ 94 [+0] _−_ 0 _[.]_ _._ [04] 05 1030 [+50] _−_ 20 0 _._ 99 [+0] _−_ 0 _[.]_ _._ [01] 02


**Table** **1.** Results from `bagpipes` (Carnall et al. 2018) photometric fitting in five apertures applied to the CRG. We target the
three main star-forming clumps (A, B, C) along the ring, the center of the object, and the total emission. **Top** : photometric
redshift is allowed to vary freely. **Middle** : fixed redshift _z_ = 4 _._ 0148 from spectroscopy. **Bottom** : central emission rescaled to
account for faint flux, where photometric redshift is allowed to vary between 0 _< z_ _<_ 2.


Band A [nJy] B [nJy] C [nJy] Center [nJy] Total [nJy]

F606W 18 _._ 50 _±_ 0 _._ 08 6 _._ 64 _±_ 0 _._ 08 10 _._ 01 _±_ 0 _._ 08 9 _._ 91 _±_ 0 _._ 08 147 _._ 0 _±_ 0 _._ 4

F814W 37 _._ 41 _±_ 0 _._ 08 18 _._ 02 _±_ 0 _._ 07 20 _._ 36 _±_ 0 _._ 07 21 _._ 09 _±_ 0 _._ 07 309 _._ 0 _±_ 0 _._ 4

F090W 44 _._ 21 _±_ 0 _._ 07 25 _._ 12 _±_ 0 _._ 06 22 _._ 18 _±_ 0 _._ 06 24 _._ 77 _±_ 0 _._ 06 418 _._ 6 _±_ 0 _._ 3

F115W 53 _._ 06 _±_ 0 _._ 07 34 _._ 27 _±_ 0 _._ 06 26 _._ 51 _±_ 0 _._ 06 34 _._ 61 _±_ 0 _._ 06 514 _._ 7 _±_ 0 _._ 3

F150W 66 _._ 07 _±_ 0 _._ 07 47 _._ 88 _±_ 0 _._ 06 32 _._ 38 _±_ 0 _._ 06 56 _._ 01 _±_ 0 _._ 06 721 _._ 6 _±_ 0 _._ 3

F200W 108 _._ 67 _±_ 0 _._ 07 90 _._ 78 _±_ 0 _._ 07 51 _._ 57 _±_ 0 _._ 06 149 _._ 7 _±_ 0 _._ 08 1402 _._ 6 _±_ 0 _._ 3

F277W 130 _._ 23 _±_ 0 _._ 09 148 _._ 73 _±_ 0 _._ 09 70 _._ 28 _±_ 0 _._ 07 274 _._ 05 _±_ 0 _._ 12 2160 _._ 0 _±_ 0 _._ 4

F356W 175 _._ 76 _±_ 0 _._ 11 201 _._ 35 _±_ 0 _._ 12 97 _._ 86 _±_ 0 _._ 09 365 _._ 90 _±_ 0 _._ 15 3045 _._ 7 _±_ 0 _._ 5

F444W 177 _._ 8 _±_ 0 _._ 7 233 _._ 8 _±_ 0 _._ 8 113 _._ 0 _±_ 0 _._ 6 443 _._ 5 _±_ 1 _._ 0 3418 _±_ 4


**Table** **2.** Aperture photometry for the galaxy analyzed in this work, measured in two _HST_ and seven _JWST_ filters. As the
error on the bulk of the photometry is very small ( _<_ 1 nJy), we apply a systematic uncertainty of 5% to the photometric
measurements in `bagpipes` .


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Six delayed SFH parameters: log10(M_*/M_sun), SFR, A_V, system age, metallicity (Z/Z_sun), ionization parameter (U)",
  "failed_quote": "For this analysis, we employ a delayed star-formation history model in `bagpipes`, consisting of six parameters: stellar mass log 10 ( _M_ _⋆_ _/M_ _⊙_ ), star-formation rate (SFR), dust attenuation ( _A_ _V_ ) as characterized in Calzetti et al. (2000), the system age, metallicity ( _Z/Z_ _⊙_ ), and the ionization parameter ( _U_ )"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[2]",
  "value": "Nested sampling via nautilus in bagpipes; redshift prior 0 < z < 5 for blind fit, or fixed z = 4.0148",
  "failed_quote": "We then consider a model where the redshift is fixed at _z_ = 4 _._ 0148."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Calibrating JWST NIRCam mosaics",
  "failed_quote": "The JWST mosaics used the JWST pipeline [3] version 1.13.4 (Bushouse et al. 2024), calibrated with reference files from JWST CRDS [4] context file 1214.pmap."
 }
]
```
