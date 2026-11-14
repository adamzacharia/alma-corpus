# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...909..130R\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
D RAFT VERSION M ARCH 30, 2021
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Ultra-faint [C** **II** **] emission in a redshift = 2 gravitationally-lensed metal-poor dwarf galaxy**


M. R [YBAK](http://orcid.org/0000-0002-1383-0746), [1] E. DA [C](http://orcid.org/0000-0001-9759-4797) UNHA, [2, 3] B. G [ROVES](http://orcid.org/0000-0002-9768-0246), [2, 4] [J. A. H](http://orcid.org/0000-0001-6586-8845) ODGE, [1] M. A [RAVENA](http://orcid.org/0000-0002-6290-3198), [5] M. M [ASEDA](http://orcid.org/0000-0003-0695-4414), [1] L. B [OOGAARD](http://orcid.org/0000-0002-3952-8588), [1] [D. B](http://orcid.org/0000-0002-4153-053X) ERG, [6]

S. C [HARLOT](http://orcid.org/0000-0003-3458-2275), [7] R. D [ECARLI](http://orcid.org/0000-0002-2662-8803), [8] D. [K.](http://orcid.org/0000-0001-9714-2758) E RB, [9] E. N [ELSON](http://orcid.org/0000-0002-7524-374X), [10] C. P ACIFICI, [11] K. B. S [CHMIDT](http://orcid.org/0000-0002-3418-7251), [12] F. W [ALTER](http://orcid.org/0000-0003-4793-7880), [13, 14] AND A. VAN [DER](http://orcid.org/0000-0002-5027-0135) W EL [15, 13]


1 _Leiden Observatory, Niels Bohrweg 2, 2333CA Leiden, The Netherlands_
2 _International Centre for Radio Astronomy Research (ICRAR), University of Western Australia, 35 Stirling Hwy, Crawley, WA 6009, Australia_
3 _ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D)_
4 _Research School of Astronomy and Astrophysics, Australian National University, Canberra, ACT 2611, Australia_
5 _N´ucleo de Astronom´ıa, Facultad de Ingenier´ıa y Ciencias, Universidad Diego Portales, Av. Ej´ercito 441, Santiago, Chile_
6 _Department of Astronomy, The University of Texas at Austin, 2515 Speedway Blvd Stop C1400, Austin, TX 78712, USA_
7 _Sorbonne Universit´e, UPMC-CNRS, UMR7095, Institut d’Astrophysique de Paris, F-75014, Paris, France_
8 _INAF — Osservatorio di Astrofisica e Scienza dello Spazio, via Gobetti 93/3, I-40129, Bologna, Italy_
9 _The Leonard E. Parker Center for Gravitation, Cosmology and Astrophysics, Department of Physics, University of Wisconsin-Milwaukee, 3135 N Maryland_
_Avenue, Milwaukee, WI 53211, USA_
10 _Department of Astrophysical and Planetary Sciences, University of Colorado, Boulder, CO 80309, USA_
11 _Space Telescope Science Institute, 3700 San Martin Drive, Baltimore, MD 21218, USA_
12 _Leibniz-Institut f¨ur Astrophysik Potsdam (AIP), An der Sternwarte 16, 14482 Potsdam, Germany_
13 _Max-Planck Institut f¨ur Astronomie, K¨onigstuhl 17, D-69117, Heidelberg, Germany_
14 _National Radio Astronomy Observatory, Pete V. Domenici Array Science Center, P.O. Box O, Socorro 87801, USA_
15 _Sterrenkundig Observatorium, Department of Physics and Astronomy, Ghent University, Belgium_


(Received 13th September 2020; Revised 4th January 2020; Accepted 5th January 2020)


Submitted to ApJ


ABSTRACT


Extreme emission-line galaxies (EELGs) at redshift _z_ = 1 _−_ 2 provide a unique view of metal-poor, starburst
sources that are the likely drivers of the cosmic reionization at _z_ _≥_ 6. However, the molecular gas reservoirs
of EELGs - the fuel for their intense star-formation - remain beyond the reach of current facilities. We present
ALMA [C II ] and PdBI CO(2–1) observations of a _z_ = 1 _._ 8, strongly lensed EELG SL2S 0217, a bright Lyman_α_ emitter with a metallicity 0.05 _Z_ _⊙_ . We obtain a tentative ( _∼_ 3-4 _σ_ ) detection of the [C II ] line and set an upper
limit on the [C II ]/SFR ratio of _≤_ 1 _×_ 10 [6] _L_ _⊙_ /( _M_ _⊙_ yr _[−]_ [1] ), based on the synthesized images and visibility-plane
analysis. The CO(2–1) emission is not detected. Photoionization modelling indicates that up to 80% of the [C II ]
emission originates from neutral or molecular gas, although we can not rule out that the gas is fully ionized. The
very faint [C II ] emission is in line with both nearby metal-poor dwarfs and high-redshift Lyman _α_ emitters,
and predictions from hydrodynamical simulations. However, the [C II ] line is 30 _×_ fainter than predicted by the
De Looze et al. [C II ]-SFR relation for local dwarfs, illustrating the danger of extrapolating locally-calibrated
relations to high-redshift, metal-poor galaxies.


_Keywords:_ Dwarf galaxies (416) – Lyman-alpha galaxies (978) – High-redshift galaxies (734) – Submillimeter
astronomy (1647)



1. INTRODUCTION


The Epoch of Reionization (EoR) is one of the main frontiers of present-day astrophysics. Recent results suggest that


Corresponding author: Matus Rybak

[mrybak@strw.leidenuniv.nl](mailto: mrybak@strw.leidenuniv.nl)



the reionization is likely driven by low-metallicity, dwarf
( _M_ _⋆_ ≲ 10 [9] _M_ _⊙_ ) galaxies with intense star formation rates;
due to their low gas and dust content, a large fraction of UV
photons will be able to escape and reionize the neutral intergalactic medium (e.g., Robertson et al. 2010, 2015; Atek
et al. 2015; Stark 2016). These metal-poor, dwarf galaxies
contribute significantly to the cosmic star-forming rate (SFR)

2 R YBAK ET AL .



at _z_ _≥_ 3 (e.g., Bouwens et al. 2009). Consequently, characterizing the star-forming processes in _z_ _≥_ 6 dwarf galaxies
presents a crucial step towards understanding the evolution
of galaxies at early cosmic times. However, these faint, highredshift dwarf galaxies remain elusive due to the limitations
of current facilities (mainly the _Hubble Space Telescope_ and
the _Spitzer Space Telescope_ ), along with the fact that for the
most distant targets the diagnostic-rich optical emission is
shifted to the near-IR regime and thus currently unobservable
- a situation that will be soon remedied by the _James_ _Webb_
_Space_ _Telescope_ . Consequently, large uncertainties remain
on the physical mechanisms of galaxy-led reionization, such
as the actual fraction of ionizing photons that escape their interstellar medium (ISM), their star formation efficiency, and
feedback processes at play.
An alternative to studying directly the _z_ _≥_ 6 dwarf galaxies is to target the intermediate-redshift ( _z_ _∼_ 2) extreme
emission line galaxies (EELGs; van der Wel et al. 2011;
Atek et al. 2011; Maseda et al. 2013, 2014; Amor´ın et al.
2015), which are likely analogues of primordial galaxies
at the EoR and can be studied much more efficiently, particularly in emission and absorption lines. EELGs have
been identified through extremely high equivalent widths
(EWs) of optical emission lines such as [O III ] 5007 A [˚]
(with rest-frame EW exceeding 500 A), [˚] via excess emission in HST/WFC3 broad-band filters (van der Wel et al.
2011), and through HST/WFC3 grism spectroscopy (Maseda
et al. 2018). Spectroscopic and photometric follow-up confirm that these are low-mass ( _M_ _⋆_ _∼_ 10 [8] _−_ 10 [9] _M_ _⊙_ ), lowmetallicity ( _Z_ _<_ 0 _._ 30 _Z_ _⊙_ ) dwarf galaxies with high SFRs
( _∼_ 10 _−_ 100 _M_ _⊙_ yr _[−]_ [1] ), likely undergoing an intense but
short-lived burst of star formation (e.g., Maseda et al. 2013,
2014; Masters et al. 2014; Tang et al. 2019).
While rest-frame UV and optical studies of high-redshift
star-forming dwarfs have primarily targeted the ionized ISM,
their intense star formation must be fueled by cold neutral
gas. In particular, measuring the cold gas reservoirs of highredshift dwarfs is crucial for understanding the timescales
on which their high-mass star formation can be maintained.
However, direct observations of the cold ISM phase in these
faint, metal-poor sources are extremely challenging, even at

_z_ _∼_ 1 _−_ 2.

Our best bet for probing the molecular gas content of this
metal-poor galaxies is the [C II ] 158- _µ_ m line, thanks to
its low critical density and large intrinsic brightness. At
_z_ _∼_ 2, _Herschel_ and ALMA Band 9 [C II ] observations
have been instrumental in probing the gas content of _M_ _⋆_ =
10 [9] _−_ 10 [11] _M_ _⊙_ galaxies (e.g., Stacey et al. 2010; Brisbin et al.
2015; Schaerer et al. 2015; Zanella et al. 2018). Crucially,
for the EoR sources, the [C II ] line is easily observable with
ALMA and has become the chief probe of cool gas in early
galaxies (e.g., Maiolino et al. 2005, 2015; Knudsen et al.



2016; Bradaˇc et al. 2017; Matthee et al. 2019; see Hodge
& da Cunha 2020 for a recent review). At the same time, the

[C II ] emission in high-redshift galaxies has been explored by
a number of cosmological (e.g., Olsen et al. 2017; Lagache
et al. 2018) and zoom-in simulations (e.g., Vallini et al. 2015;
Katz et al. 2017; Pallottini et al. 2019; Lupi & Bovino 2020).
In this paper, we attempt to study the neutral ISM in
a strongly gravitationally lensed _z_ _∼_ 2 SL2S 0217, targeting the [C II ] line with Atacama Large Millimetre/submillimetre Array (ALMA), and CO(2–1) with the Plateau de
Bure Interferometer (PdBI). Thanks to its large magnification, SL2S 0217 provides a unique opportunity to detect the
neutral ISM in a high-redshift EELG with a stellar mass of
just 10 [8] _M_ _⊙_ - 1 dex lower than any previous _z_ _∼_ 2 study.
This paper is structured as follows: § 2 presents our ALMA
and PdBI observations, data combination and imaging procedures; § 3 presents the derivation of the source-plane upper
limits on the [C II ] and CO(2–1) luminosities. In § 4, we
compare our [C II ] non-detection to the expectations photoionization modelling (§ 4.1), various empirical and theoretical [C II ]-SFR relationships (§ 4.2) as well as local and highredshift observations (§ 4.3). Finally, we discuss the fate of
the molecular gas in SL2S 0217 (§ 4.4) and the prospects of
detecting the [C II ] emission from SL2S 0217-like dwarfs in
the Epoch of Reionization (§ 4.5).


2. OBSERVATIONS AND IMAGING


2.1. _Target description_


SL2S 021737–051329 (henceforth SL2S 0217, J2000 02h
17m 37.237s -05d13m29.7s) is a redshift _z_ = 1 _._ 844 EELG,
strongly gravitationally lensed by a _z_ = 0 _._ 6459 elliptical
galaxy. SL2S 0217 was serendipitously discovered by Geach
et al. (2007, source ID SXDF-iS-170569). Thanks to its position under the cusp of the lensing caustic, SL2S 0217 is
lensed into a brilliant, 2.5-arcsec long Einstein arc, with a
fainter counter-image. The lens system includes a second,
doubly-imaged background source SL2S 0217.X at _z_ = 2 _._ 29
(Brammer et al. 2012).
The stellar content of SL2S 0217 was studied by Brammer
et al. (2012, B12) using HST GRISM spectroscopy and Berg
et al. (2018, B18) using Keck/LRIS optical spectroscopy.
Pixellated lens modelling of SL2S 0217 based on the HST
data [1] was performed by Cooray et al. (2011), B18 and Erb
et al. (2019); in the B18 model, the HST F606W continuum
is magnified by a factor of _∼_ 17, with a source-plane UV
half-light radius of _∼_ 0 _._ 35 kpc. We adopt the source-plane
properties listed in Table 1, based on the B18 lens model. The
_Z_ = 0 _._ 05 _Z_ _⊙_ metallicity of SL2S 0217 is typical of _z_ _∼_ 6
galaxies with the same stellar mass (c.f. F IRST L IGHT sim

1 see also Tu et al. (2009) and B12 for parametric lens models.

[CII] EMISSION IN SL2S 0217 3



**Table 1.** SL2S 0217: intrinsic (de-lensed) properties adapted from
Berg et al. (2018, B18) and Erb et al. (2019, E19), with the [C II ]
and CO(2–1) upper limits derived assuming the _R ≤_ 3 kpc aperture
from the 1-arcsec taper images (Fig. 1) and a magnification factor
_µ_ = 16. For the solar metallicity, we adopt the Asplund et al.
(2009) value of 12+log(O/H)=8.69. Molecular gas mass _M_ H 2 is
derived from the [C II ] luminosity using the Madden et al. (2020)
conversion factor.


Reference

_z_ spec 1.844 B18
M _⋆_ [ _M_ _⊙_ ] (1 _._ 8 _±_ 0 _._ 4) _×_ 10 [8] B18
SFR [ _M_ _⊙_ yr _[−]_ [1] ] 23 _±_ 2 B18

_µ_ UV 17.3 _±_ 1.2 B18

12+log(O/H) 7.5 B18
_R_ 1 [UV] _/_ 2 [kpc [2] ] 1.0 _×_ 0.5 E19

_L_ [CII] [ _L_ _⊙_ ] _≤_ 2 _._ 1 _×_ 10 [7] (3.2 _σ_ ) _[a]_ § 3.1
_L_ _[′]_ [CII] [K km s _[−]_ [1] pc [2] ] _≤_ 1 _×_ 10 [8] (3.2 _σ_ ) § 3.1
_S_ 160 _µ_ m mJy _≤_ 0 _._ 23 (3 _σ_ ) § 3.1
_L_ CO(2 _−_ 1) [ _L_ _⊙_ ] _≤_ 1 _._ 3 _×_ 10 [5] (3 _σ_ ) § 3.1
_L_ _[′]_ CO(2 _−_ 1) [K km s _[−]_ [1] pc [2] ] _≤_ 4 _×_ 10 [8] (3 _σ_ ) § 3.1
_M_ H [[CII]] 2 [ _M_ _⊙_ ] _≤_ 2 _._ 1 _×_ 10 [9] (3.2 _σ_ ) § 4.4

_a_ Based on our tentative image-plane detection, see Fig. 2.


ulations, Langan et al. 2020), underlining its suitability as a
EoR analogue.
The spatial distribution of the Ly _α_ emission in SL2S 0217
was studied by Erb et al. (2019, E19) using narrow-band HST
imaging. This revealed a 0.6-kpc offset between Ly _α_ and the
UV continuum, indicating a varying column density of neutral hydrogen across the source, with the bulk of the Ly _α_ photons escaping along a low column density channel. The longwavelength spectral energy distribution of SL2S 0217 is only
poorly sampled, with a single detection in the Spitzer/MIPS
24- _µ_ m imaging (B12; 7.3–9.1 _µ_ m rest-frame, including the
7.7 and 8.6 _µ_ m PAH bands) which indicates a significant hotdust and/or PAH emission. In this paper, we extend this comprehensive dataset to the far-infrared and mm-wave regime,
targeting the [C II ] 158 _µ_ m line.
We assume a flat ΛCDM cosmology, with Ω _m_ = 0 _._ 315
and _H_ 0 = 67 _._ 4 km s _[−]_ [1] Mpc _[−]_ [1] (Planck Collaboration et al.
2020). At _z_ = 1 _._ 844, this translates to a luminosity distance
_D_ _L_ = 14460 Mpc; 1 arcsec corresponds to a physical distance of 8.65 kpc (Wright 2006).


2.2. _ALMA Band 9 observations and imaging_


We combine deep ALMA Band 9 observations of the [C II ]
line ( _f_ 0 =1900.539 GHz) and the underlying rest-frame 160_µ_ m continuum from the ALMA projects #2016.1.00142.S
and #2016.1.00776.S.

The ALMA programme #2016.1.00142.S (PI: da Cunha)
observations were carried out in two array configurations:



C43-1 (2018 July 6) and C43-2 (2018 August 16). The baseline length ranged between 15 and 314 m (C43-1) and 15
to 479 m (C43-2). Forty 12-m antennas were used on both
dates. The primary beam FWHM was 9.0 arcsec at 680 GHz.
The precipitable water vapour (pwv) ranged between 0.4 and
0.5 mm. The total observing time was 2.7 hours, with a total
on-source time of 67 minutes.

The spectral setup consisted of four spectral windows
(SPWs) with 480 channels of 3.906 MHz each, giving a total
bandwidth of 2.0 GHz per SPW. The individual SPWs were
centered at 667.61, 669.53, 649.91 and 648.03 GHz.
As the ALMA pipeline products suffered from calibration
issues, we calibrated the data manually by completely flagging antennas with high system temperature: C43-1 configuration: DA62, DA44, DA50, DV09, DV24; C43-2: DA62.
We used DV07 as the reference antenna due to its low system
temperature, good bandpass stability, and central position in
the array.
We supplemented these data by observations from the
ALMA programme #2016.1.00776.S (PI: Cooray). These
were taken in two array configurations: C43-2 with fortyseven 12-m antennas (2018 October 19) and C43-6 with fiftyone 12-m antennas (2016 October 1 and 14). The baseline
length ranged between 15 and 3145 m (C43-6) and baselines 15 and 484 m (C43-2), pwv ranged between 0.55 and
0.80 mm. The on-source time was 47.0 min for each configuration. The spectral setup consisted of four SPWs configured
with 128 15.625-MHz-wide channels (2.0 GHZ bandwidth
per SPW), with central frequencies of 664.95, 666.64, 668.34
and 670.03 GHz. For the C43-6 configuration, we manually
flagged antennas DA43, DV14, DV17. This reduced the total

number of antennas to 48.

For the imaging, we concatenate the visibilities from both
ALMA programmes to maximize the S/N; the total on-source
time is 160 min. For the C43-6 configuration, we discard all
baselines longer than 1000 k _λ_, as adding the long baselines
significantly reduces the surface brightness sensitivity of the
combined dataset. The resulting (u,v)-plane coverage provides sensitivity to spatial scales between 0.21 and 6.2 arcsecs; given the arc length of 2.5 arcsec, we do not expect any

structure to be resolved out.

We produce dirty images of the concatenated dataset using natural weighting, at the full angular resolution and using a 0.5 and 1.0-arcsec Gaussian taper. For the [C II ] line,
we create several dirty-image cubes using different (u,v)plane tapers (no taper, 0.5 and 1.0-arcsec taper) and channel
width (∆ _f_ = 50-500 MHz, equivalent to 25-225 km s _[−]_ [1] ).
The _σ_ rms levels in the resulting images match the expected
ALMA sensitivity within 10%.
For the continuum image, we combine all the SPWs, flagging the channels affected by atmospheric lines. The resulting beam sizes and rms sensitivity for the [C II ] and

4 R YBAK ET AL .



**Table** **2.** ALMA Band 9 synthesized beam size, position angle
and rms sensitivity for the [C II ] line (measured at 668 GHz over
250 MHz bandwidth) and the rest-frame 160- _µ_ m continuum as a
function of (u,v)-taper.

|taper|beam FWHM (PA) σ ([CII]) σ (cont .)<br>[arcsec deg] [mJybeam−1] [mJybeam−1]<br>,|
|---|---|
|full-res<br>0.5 arcsec<br>1.0 arcsec|0.26_×_0.23 (57)<br>1.28<br>0.23<br>0.65_×_0.57 (-9)<br>1.44<br>0.29<br>1.01_×_0.92(-9)<br>1.91<br>0.44|



Band 9 continuum imaging are listed in Table 2. With a sensitivity of _σ_ rms = 1 _._ 3 mJy/beam over 250 MHz bandwidth
(3.7 mJy/beam over 10 km s _[−]_ [1] ), the combined dataset ranks
among the deepest ALMA Band 9 observations to-date.
Figures 1 presents the resulting synthesised images. We
do not find any significant ( _≥_ 5 _σ_ ) [C II ] or rest-frame 160_µ_ m continuum emission. However, the [C II ] images show
a suggestive 2-3 _σ_ emission along the main Einstein arc (see
discussion below). In addition, we obtain a tentative (2-4 _σ_ )
detection of the rest-frame 140- _µ_ m continuum from the secondary lensed source SL2S 0217.X ( _z_ = 2 _._ 29, B12).
The ALMA data were reduced and imaged using the Common Astronomy Software Applications package (C ASA, McMullin et al. 2007), versions 5.1 and 5.4.


2.3. _PdBI Band 1 observations and imaging_


In addition to the ALMA observations of the [C II ] 158_µ_ m line, we target the CO(2–1) line using the Plateau de
Bure Interferometer (PdBI) with the WideX correlator (programme X037, PI: Aravena). The PdBI data were taken between 2013 June 15 and 2013 September 14 in a total of 16
successful tracks. The total on-source time was 29.6 hours

(5-antennas equivalent); the total observing time was 40 h.
All observations were carried our in the most compact Dconfiguration, with five 15-meter antennas. The baseline
length ranged between 15 and 97 m, resulting in a synthesized beam FWHM = 7 arcsec; the source is thus completely
unresolved. The observations covered a frequency range of
79.6 - 83.2 GHz with a spectral resolution of 2 MHz. The
resulting rms sensitivity at the expected frequency of the
CO(2–1) line is 0.28 mJy beam _[−]_ [1] over 100 km s _[−]_ [1] bandwidth. The data were reduced using the G ILDAS /C LIC package (http://www.iram.fr/IRAMFR/GILDAS).


3. RESULTS


3.1. _[CII] line and 160-µm continuum_

3.1.1. _Searching for signal in the image plane_


To convert the image-plane [C II ] flux to source-plane (intrinsic) flux, we need to account for the gravitational lensing. The magnification of the extended source depends on



its surface brightness distribution and the lensing geometry.
Although we could simply assume that the [C II ] emission
is co-spatial with the HST continuum, resolved observations
of high-redshift galaxies have revealed kpc-scale offsets between the rest-frame UV and [C II ] emission (e.g., Maiolino
et al. 2015; Carniani et al. 2017) and very extended [C II ]
reservoirs (e.g., Carniani et al. 2018; Matthee et al. 2019;
Carniani et al. 2020). If [C II ] is significantly offset from the
UV continuum, the [C II ] might be less magnified the UV,
increasing the source-plane _L_ [CII] upper limit.
We consider three circular source-plane apertures centered
on the UV-continuum peak, with a radius _R_ =1.0, 2.0 and
3.0 kpc; the latter is comparable to the largest [C II ] reservoirs observed in (much more massive) _z_ _∼_ 6 galaxies (Carniani et al. 2020). We project these into the sky-plane using
the Cooray et al. (2011) lens model for the lensing galaxy. To
maximize the S/N, we consider only the part of the sky-plane
aperture corresponding to the main arc (Figure 1); as the arc
accounts for 95% of the total flux. The magnification factor
is _µ_ = 43, 25 and 16 for the _R_ =1, 2 and 3-kpc apertures,
respectively.
We note that in the synthesis imaging, the area under a
dirty beam integrates to zero for large aperture sizes, unlike for a classical point-spread function. Consequently, flux
measurements extracted from _dirty_ images over extended areas might be biased, particularly in presence of strong positive or negative sidelobes. However, the dirty beams corresponding to the Fig. 1 images are well-described by a central
Gaussian with only very small sidelobes ( _≤_ 5%) within the
apertures considered here. Our flux limits should therefore

be robust.

Figure 2 shows the spectra extracted from within these
apertures, at 100 MHz resolution, which reveal an excess flux
at 667.9 GHz. The excess signal is unlikely to be caused by
e.g. continuum contamination or phase errors. At 250 MHz
binning (110 km s _[−]_ [1] ), the excess is detected at 3 _._ 2 _−_ 4 _._ 3 _σ_
significance, depending on the taper and aperture used.
No continuum signal is detected at _≥_ 3 _σ_ significance; we
therefore put a conservative 3 _σ_ upper limit on the rest-frame
160- _µ_ m flux _S_ 160 _µ_ m _≤_ 0 _._ 23 mJy, based on the 1.0-arcsec
taper images and the _R ≤_ 3 kpc aperture.


3.1.2. _Searching for signal in the (u,v) plane_


As the spatial filtering by the incomplete (u,v)-plane coverage might decrease the sensitivity to extended emission in
the synthesized images, we try to confirm our tentative detection of the [C II ] line in the (u,v)-plane. How bright can
the [C II ] emission be to be still consistent with the observed

visibilities?

We use the following approach by adapting the (u,v)plane lens-modelling technique from Rybak et al. (2015);
Rybak (2017). First, we extract the visibility data (real and

[CII] EMISSION IN SL2S 0217 5


**Figure 1.** ALMA Band 9 imaging: dirty naturally-weighted images of the [C II ] line ( _upper_ ) and continuum ( _lower_ ) at full resolution and 0.5
and 1.0 arcsec taper, overlayed with the HST F606W imaging (Brammer et al. 2012, white contours). The [C II ] emission is integrated over
250 MHz (110 km s _[−]_ [1] ) bandwidth centered at 667.97 GHz; this part of the spectrum shows the tentative 2-3 _σ_ extended emission. The black
contours start at _±_ 2 _σ_ and increase in steps of 1 _σ_ . The HST contours are drawn at 5, 10, 20, 40, 60 and 80% of the surface brightness maximum.
The dashed line ( _left_ ) indicates the _R_ = 3 kpc aperture used to extract the upper limits (see § 3.1). No continuum emission from the main
source is detected; the second lensed source (SL2S 0217.X, _z_ = 2 _._ 29) is tentatively detected at 2-4 _σ_ significance in each image.


imaginary parts) at 669.970 _±_ 0.125 GHz (same bandwidth
as used for the image-plane analysis). The noise on the
real/imaginary visibilities is estimated by taking the rms of
visibilities for a given baseline for each individual scan. As
the noise per polarization might differ, we do not combine
the XX and YY polarizations into the Stokes _I_ . We then calculate the expected signal _V_ ( _u, v_ ) [model] for each visibility as


_V_ ( _u, v_ ) [model] = � _B_ ( _l, m_ ) _I_ ( _l, m_ ) _e_ [2] _[πi]_ [(] _[ul]_ [+] _[vm]_ [)] _,_ (1)

_l,m_



**Figure 2.** ALMA Band 9 spectrum of SL2S 0217 at 100 MHz (45
km s _[−]_ [1] ) resolution, extracted for the full-resolution and 1.0 arcsec
taper images, and the three source-plane apertures. The shaded regions indicate _σ_ rms for each channel. We obtain a tentative (3-4 _σ_ )

[C II ] 158- _µ_ m detection at 667.97 GHz (offset from the systemic
velocity by _∼_ 50 km s _[−]_ [1] ) .



where _B_ is the primary beam response (approximated by a
Gaussian), _I_ the input sky brightness distribution, and _m, l_
the sky-plane coordinates. We consider the following skyplane [C II ] surface brightness distributions: HST F606W
arc (see Fig. 1) and the _R_ _≤_ 1, 2 and 3 kpc apertures;
the total flux varies between 0 and 50 mJy. We calculate
the log-likelihood value log _L_ _∝−_ [�] _i_ [(] _[V]_ [ (] _[u]_ _[i]_ _[, v]_ _[i]_ [)] [model] _[−]_

_V_ ( _u_ _i_ _, v_ _i_ ) [data] ) [2] _/σ_ ( _u_ _i_ _, v_ _i_ ) [2] . As a control test, we perform
the same analysis for a “line-free” part of the spectrum
(680.000 _±_ 0.125 GHz).
Figure 3 shows the derived probability distribution function (PDF) for _S_ [CII] . For the _R_ _≤_ 2 kpc and _R_ _≤_ 3 kpc
apertures, the PDF peaks around _S_ [CII] = 15 mJy, whereas
for the HST-based aperture, the PDF peaks at 0 mJy. Reassuringly, the PDF for the “line-free” part of the spectrum

6 R YBAK ET AL .


**Figure 4.** PdBI spectrum of SL2S 0217 with 100 km s _[−]_ [1] frequency
bins. The shaded region indicates the _σ_ rms for each channel. We do
not detect any significant CO(2–1) emission from SL2S 0217.



**Figure** **3.** (u,v)-plane analysis of the ALMA [C II ] 158- _µ_ m observations: Probability distribution function (PDF) of the sky-plane

[C II ] flux for a 250 MHz bandwidth (see Fig 1), assuming different surface brightness distributions and compared to the sky-plane
limit (21 mJy). Colored dashed lines indicate sky-flux PDFs for a
“line-free” part of the data (i.e., where no signal is expected). Although the [C II ] PDF peaks around 15 mJy for _R_ _≤_ 2, 3 kpc apertures, this solution is not strongly preferred over the null hypothesis
( _S_ [CII] = 0 mJy) and is below the sky-plane limit. This result does
not depend on the noise model used. We therefore adopt an upper
limit on _S_ [CII] =21 mJy based on image-plane analysis.


peaks near _S_ [CII] = 0 mJy (dashed lines) for all apertures.
Tweaking the noise calculation (e.g., by combining the polarizations, calculating the rms over several scans) does not
substantially change the PDFs. This might be indicative of
an extended [C II ] emission in SL2S 0217. However, the
_S_ [CII] = 15 mJy solution is not strongly preferred over the
_S_ [CII] = 0 mJy, our null hypothesis.
Consequently, we adopt a [C II ] upper limit of _S_ [CII] _≤_
21 mJy over 250 MHz (110 km s _[−]_ [1] ) bandwidth, measured
for the 1.0-arcsec uv-taper and _R_ _≤_ 3 kpc source-plane
aperture (3.2 _σ_ significance). The 1.0-arcsec taper maximizes the surface-brightness sensitivity, while large aperture
size accounts for a potentially very extended [C II ] emission. This line flux corresponds to a sky-plane luminosity
of _L_ [CII] _≤_ 3 _._ 4 _×_ 10 [8] _L_ _⊙_ ; after de-lensing ( _µ_ = 16), we set a
source-plane upper limit of _L_ [CII] _≤_ 2 _._ 1 _×_ 10 [7] _L_ _⊙_ . The line
width adopted here is comparable to the typical line FWHM
of _∼_ 120 km _[−]_ [1] of _z_ _∼_ 2 EELGs (Maseda et al. 2014).


3.2. _CO(2–1) line_


As shown in Figure 4, we do not detect any significant
CO(2–1) line emission towards SL2S 0217; the PdBI spectrum is consistent with pure noise. Assuming the same aperture and 110 km s _[−]_ [1] linewidth as for the [C II ] line (see Figure 1), we set a 3 _σ_ upper limit on _L_ CO(2 _−_ 1) _≤_ 1 _._ 3 _×_ 10 [5] _L_ _⊙_,
_L_ _[′]_ CO(2 _−_ 1) _[≤]_ [4] _[ ×]_ [ 10] [8] [ K km s] _[−]_ [1] [ pc] [2] [ (source-plane).]



4. DISCUSSION


4.1. _Photoionization modelling_


With an ionization energy of 11.3 eV, the [C II ] 158- _µ_ m
emission [2] can arise from all ISM phases: molecular (H 2 ),
neutral (H), and ionized (H [+] ). Although studies of nearby
galaxies have shown that at _Z_ _≤_ 0 _._ 25 _Z_ _⊙_ almost all [C II ]
emission arises from the neutral ISM (Croxall et al. 2017;
Sutter et al. 2019), the large ionizing flux and limited selfshielding due to low metallicity in SL2S 0217 might cause
the ionized component to dominate its _L_ [CII] (Ferrara et al.
2019). In SL2S 0217, the semi-forbidden C II ]2325 A emis- [˚]
sion line and the C II absorption line detected in the Keck
spectra (B18) confirm the presence of at least some C [+] in
the ionized ISM. But _can_ the ionized gas account for the entire [C II ] 158- _µ_ m emission?
We address this question by using photoionization modelling to predict the [C II ] 158- _µ_ m emission from the ionized
ISM using the M APPINGS V photoionization code (Allen
et al. 2008; Groves & Allen 2010). We focus on the

[C II ] 158 _µ_ m far-IR line and the rest-frame UV C II ] 2325 A [˚]
line and the C III ] 1909 A [˚] doublet [3] . The photoionization
modelling provides a lower limit on _L_ [CII], as the contribution of [C II ] 158 _µ_ m from photon-dominated regions
(PDRs) (e.g., Hollenbach & Tielens 1997) is not included

in the M APPINGS models. Due to the lack of constraints

on the PDR phase (just our [C II ] 158- _µ_ m and a very weak
CO(2–1) upper limits, we refrain from modelling the neu
tral/molecular ISM.


2 In this section, we explicitly state the wavelengths of individual emission
lines for clarity.
3 Here, we treat the ISM as uniform. However, as shown by E19, the UV
spectral slope varies considerably across the source; the C II ], [C II ] and
C III ] lines are thus likely not co-spatial on sub-kiloparsec scales., which
are all predicted by M APPINGS V

[CII] EMISSION IN SL2S 0217 7



The semi-forbidden C III ] 1909 A doublet originates in the [˚]
H II regions (e.g., Jaskot & Ravindranath 2016; Kewley et al.
2019; Vallini et al. 2020), and - thanks to its brightness - is a
convenient tracer of ionized gas in the EoR (Stark et al. 2015,
2017; Zitrin et al. 2015); the C II ] 2325 A line traces the outer [˚]
layers of H II regions, which also emit the [C II ] 158 _µ_ m
line. Based on our upper limits and B18 spectroscopy, the
observed ratios are [C II ] 158 _µ_ m / C II ] 2325 A [˚] _≤_ 4.7, [C II ]
158 _µ_ m / C III ] 1909 A [˚] _≤_ 0.8 and C III ] 1909 A / C [˚] II ] 2325 A [˚]
= 6.2 _±_ 0.5 (in W m _[−]_ [2] units). Using C II ] instead of any of the
other UV lines detected in the Keck spectrum by B18 avoids
systematic uncertainties related to the carbon abundance and

ionization state.

To set the ionizing radiation field, we use the S TAR  
BURST 99 stellar population models [4] (Leitherer et al. 1999,
2010), including also the effects of stellar rotation on the
emitted spectra of massive stars, as described in Levesque
et al. (2012).
Following the B18 modelling of the UV spectrum, we set
the model metallicity to 0 _._ 05 _Z_ _⊙_ and assume an instantaneous starburst. We explore models with electron densities between _n_ _e_ =10 and 100 cm _[−]_ [3], since the C II ] 2325 A/ [˚]

[C II ] 158 _µ_ m flux ratio is very sensitive to density due to
the low critical density of the [CII] 158 _µ_ m line in ionised gas
( _n_ _e_ =50 cm [3] ). We vary the ionization parameter _U_ (defined as
the ratio of the _≥_ 13 _._ 6 eV photon number density and the gas
density _n_ ) and the age of the ionizing star cluster (in steps of
0.5 Myr). We adopt a one-dimensional plane-parallel geometry as appropriate for the expected geometry in SL2S 0217:
a screen of ionized ISM on front of an ionizing cluster. Figure 5 shows the predicted [C II ] 158 _µ_ m / C II ] 2325 A [˚] and
C III ] 1909 A / C [˚] II ] 2325 A ratios for each realization. [˚]
The C III ] 1909 A/C [˚] II ] 2325 A [˚] ratio depends both on the
ionisation parameter (impacting both the gas temperature and
ionization state) and the age of the starburst (affecting the relative number of C [+] ionizing photons, _>_ 24.4 eV, to C [0] ionizing photons, _>_ 11.3 eV). See Jaskot & Ravindranath (2016);
Kewley et al. (2019) for other examples, and the color axes
in Fig. 5.
As the [C II ] 158 _µ_ m and C II ] 2325 A [˚] lines arise only
from a single species and ionisation state, their ratio is purely
dependent upon the electron density and temperature, which

drive the relative collisional rates. Because of the low critical
density for [C II ] 158 _µ_ m ( _n_ _e_ _≃_ 50 cm _[−]_ [3] ) and high excitation energy of the C II ] 2325 A line, the [C [˚] II ] 158 _µ_ m / C II ]
2325 A [˚] ratio depends strongly on both electron density and

temperature.


4 For the case considered here, the predicted line intensities differ only
marginally ( _≤_ 0 _._ 1 dex) between the different stellar model libraries. See
D’Agostino et al. 2019 for a detailed comparison.



We find that, for _n_ _e_ = 100 cm _[−]_ [3] (the value assumed by
B18), M APPINGS predicts log( _L_ [ion] [CII]158 _µ_ m _[/L]_ CII]2325A ˚ [)] _[∼]_

_−_ 0 _._ 5 _±_ 0 _._ 5 (Figure 5). For _n_ _e_ = 10 cm _[−]_ [3], the ratio is typically 0.5 dex higher, as the critical density for [C II ] 158 _µ_ m
is lower than for C II ]2325 A. [˚] Therefore, we conservatively
assume that log( _L_ [ion] [CII]158 _µ_ m _[/L]_ CII]2325A ˚ [)] [=] [0] _[±]_ [1.] [Given] [the]

C II ]2325 A flux of [˚] 1 _._ 11 _×_ 10 _[−]_ [17] erg s _[−]_ [1] cm _[−]_ [2] (flux of the
brightest line in the C II ] triplet, measured by B18; this is the
line predicted by M APPINGS ), we estimate an on-sky [C II ]
158 _µ_ m line luminosity _L_ [ion] [CII]158 _µ_ m _[∼]_ [7] _[.]_ [3] _[ ×]_ [ 10] [7] _[ L]_ _[⊙]_ [.]
This estimate is approximately 5 _×_ lower than our

[C II ] 158 _µ_ m upper limit ( _L_ [sky] [CII]158 _µ_ m _[≤]_ [3] _[.]_ [4] _[×]_ [10] [8] _[ L]_ _[⊙]_ [)]
although the lack of _n_ _e_ constraints implies a _∼_ 1 dex uncertainty in the predicted flux ratio.
For most of the _n_ _e_, _U_ models considered here, our [C II ]
158 _µ_ m upper limit is higher than the contribution from the
ionized ISM; the neutral/molecular ISM can account for up
to 80% of the [C II ] 158 _µ_ m line flux, similar to the _z_ = 0
low-metallicity galaxies (Croxall et al. 2017; Cormier et al.
2019). However, in the low-density, high-ionization regime
( _n_ _e_ = 10 cm _[−]_ [3], log _U_ _≥−_ 3 _._ 5), the predicted [C II ] 158- _µ_ m
luminosity exceeds our upper limits. In such case, the ISM
in SL2S 0217 will be fully ionized.


4.2. _Comparison with empirical models and simulations_


We now compare SL2S 0217 to predictions for [C II ] luminosity from various empirical models and hydrodynamical
simulations. Thanks to the stream of high-redshift [C II ] detections from ALMA (Hodge & da Cunha 2020), the [C II ]
emission from high-redshift galaxies has been extensively
studied by a number of high-resolution hydrodynamical simulations. Our tentative [C II ] detection in a _Z_ = 0 _._ 05 _Z_ _⊙_
dwarf allows us to validate these models in the poorly explored high-SFR, low-metallicity regime.
Namely, we consider the following [C II ]-SFR relations:
the empirical De Looze et al. (2014) relation for nearby lowmetallicity dwarf galaxies, the Herrera-Camus et al. (2015)
calibration for nearby star-forming galaxies, as well as predictions from simulations of Vallini et al. (2015); Olsen et al.
(2017) and Lagache et al. (2018). Table 3 lists the respective [C II ]-SFR relations and the predicted source-plane

[C II ]/SFR ratio for SL2S 0217. Figures 6 and 7 compare

the _L_ and _L_ /SFR in SL2S 0217 with relations from

[CII] [CII]
Table 3, and low- and high-redshift observations (see below)
as a function of SFR and metallicity.
Our upper limit is in agreement with the metallicitydependent relations of Vallini et al. (2015) and Olsen et al.
(2017). On the other hand, the [C II ] emission in SL2S 0217
is at least 30 _×_ fainter than expected from the locallycalibrated De Looze et al. (2014), a _≥_ 4 _σ_ tension. The
Herrera-Camus et al. (2015) relation predicts even higher
_L_ [CII] /SFR with a smaller scatter ( _∼_ 0 _._ 2 dex); this is likely

8 R YBAK ET AL .


Finally, we consider the analytical model of Ferrara et al.
(2019), who investigated low [C II ] luminosities of some of
the high- _z_ UV-selected sources. In the low-metallicity, highΣ SFR regime of SL2S 0217, the [C II ] surface density Σ [CII]
is given by:



Σ = 1 _._ 8 _×_ 10 [7] _n_ gas

[CII]
� _n_ 500



_U_
ln
� � 0 _._ 001



_,_ (2)
�



**Figure 5.** M APPINGS modelling of C [+] /C [2+] emission lines from the
ionized ISM as a function of the starburst age ( _upper_ ) and the ionization parameter _U_ ( _lower_ ). We show the ratios of [C II ] 158 _µ_ m,
C II ] 2325 A [˚] and C III ] 1909 A [˚] luminosities for an instantaneous
star-formation burst, _Z_ = 0 _._ 05 _Z_ _⊙_, _n_ _e_ =10 and 100 cm _[−]_ [3] . The
grey lines connect models with constant _U_ and increasing age. The
shaded area is excluded by the [C II ] 158 _µ_ m / C III ] 1909 A [˚] ratio. The upper limit on _L_ [CII] is consistent with a young ( _<_ 5 Myr)
starburst over a wide range _U_ and allows for a substantial [C II ]
emission from the neutral ISM.


a consequence of a relatively high metallicity of their sample
(12 + log(O/H)=7.7-8.8).
Finally, Lagache et al. (2018) underpredict the SL2S 0217

[C II ] luminosity by a factor of 20; however, given the 0.5 dex
1 _σ_ scatter of the Lagache et al. (2018) trend, our upper limit
is still consistent with it at 2.5 _σ_ level. We note that the La
gache et al. (2018) simulations contain a significant number
of galaxies with SFR, metallicity and _L_ [CII] consistent with
SL2S 0217.

The strong dependence of the _L_ [CII] /SFR ratio on average
gas metallicity is supported by the high-resolution simulations of high- _z_ dwarf galaxies by Lupi & Bovino (2020): for
_Z_ _≤_ 0 _._ 1 _Z_ _⊙_, they find _L_ [CII] /SFR _≤_ 10 [6] _L_ _⊙_ /( _M_ _⊙_ yr _[−]_ [1] ),
consistent with our upper limit.



where _n_ 500 = 500 cm _[−]_ [3] . For SL2S 0217, with an ionization parameter log _U_ = _−_ 1 _._ 5 (B18) and assuming that

[C II ] is co-spatial with the UV continuum, Eq. (2) matches
our Σ [CII] upper limit for _n_ gas _≃_ 150 cm _[−]_ [3] ( _n_ gas decreases
further if [C II ] is more extended than the UV continuum).
As the Ferrara et al. model directly sets _U_ _∝_ Σ SFR _/_ Σ [2] gas [,]
to reconcile the high _U_ and _⟨_ Σ SFR _⟩_, SL2S 0217 has to be
an extreme starburst, with a gas surface density Σ gas _≃_
3 _._ 5 _×_ 10 [8] _M_ _⊙_ kpc _[−]_ [2] . This roughly agrees with the expectation from the E19 gas column density estimate _N_ HI _≃_
10 [21] _[.]_ [7] cm _[−]_ [3], which predicts Σ gas = _N_ HI _×_ _m_ proton _≃_
8 _×_ 10 [7] _M_ _⊙_ kpc _[−]_ [2] .


4.3. _Comparison with low-metallicity galaxies near and far_


In the present-day Universe, SL2S 0217 can be directly
compared to galaxies from the Dwarf Galaxy Survey (DGS)
(Madden et al. 2013), which span _Z_ = 0.02 - 1.0 _Z_ _⊙_ and SFR
= 0.0005 - 25 _M_ _⊙_ yr _[−]_ [1] ; 48 galaxies from the DGS sample were targeted with _Herschel_ PACS far-IR spectroscopy
by Cormier et al. (2015). Although the DGS sample shows
a broad [C II ]/SFR correlation, the [C II ]/SFR ratio varies
between 10 [5] _[.]_ [0] and 10 [9] _[.]_ [5] _L_ _⊙_ _/_ ( _M_ _⊙_ yr _[−]_ [1] ) (Figure 6). Four
DGS sources have [C II ]/SFR ratios similar or lower than
SL2S 0217. In particular, SBS 0335-052 - which matches

SL2S 0217 in terms of the rest-frame UV line ratios and the
overall SED (E18) - has [C II ]/SFR _≃_ 5 _._ 5 _×_ 10 [5] _L_ _⊙_ /( _M_ _⊙_
yr _[−]_ [1] ), directly comparable to our upper limits.
At _z_ = 1 _−_ 2, the bulk of [C II ] and CO molecular
gas studies have focused on relatively massive galaxies with
_M_ _⋆_ _≥_ 10 [1] 0 _M_ _⊙_ (e.g., Stacey et al. 2010; Brisbin et al.
2015; Zanella et al. 2018). The only exception is the strongly
lensed _M_ _⋆_ _≃_ 2 _._ 5 _×_ 10 [9] _M_ _⊙_ galaxy detected in [C II ] and
CO(3–2) by Schaerer et al. (2015); however, it is still _∼_ 10 _×_

more massive and metal-enriched than SL2S 0217. The

[C II ]/SFR ratio measured by Schaerer et al. (2015) is 10 [7] _L_ _⊙_
/ ( _M_ _⊙_ yr _[−]_ [1] ), 1 dex higher than in SL2S 0217.
At _z_ _≥_ 6, two _z_ = 6 _−_ 7 EELGs lensed by galaxy clusters have been detected in the [C II ] emission by Knudsen
et al. (2016, who also obtained a strong upper limit on another source) and Bradaˇc et al. (2017). Similar to SL2S 0217,
all three sources have [C II ]/SFR _≤_ 3 _×_ 10 [6], significantly
lower that the locally-calibrated De Looze et al. (2014) relation (Figure 6). While the Knudsen et al. (2016) [C II ]detected source has a relatively low SFR and high stellar

[CII] EMISSION IN SL2S 0217 9


**Table 3.** [C II ]-SFR relations referenced in this work, with the expected [C II ]/SFR ratio for SL2S 2017, given the parameters from Table 1.
The [C II ]/SFR ratio in SL2S 0217 is _≤_ 1 _×_ 10 [6] _L_ _⊙_ /( _M_ _⊙_ yr _[−]_ [1] ).


Reference [C II ]-SFR _L_ [CII] /SFR Note

[ _L_ _⊙_ /( _M_ _⊙_ yr _[−]_ [1] )]
De Looze et al. (2014) log _L_ [CII] = 1 _._ 25 log(SFR) + 7 _._ 16 3 _×_ 10 [7] Local dwarf galaxies (Cormier et al. 2015)
Herrera-Camus et al. (2015) log _L_ [CII] = 0 _._ 97 log(SFR) + 7 _._ 66 4 _×_ 10 [7] Local star-forming galaxies
Vallini et al. (2015) log _L_ [CII] = 7 _._ 0 + 1 _._ 2 log(SFR) + 0 _._ 021 log( _Z_ )+ 9 _×_ 10 [5] Zoom-in simulations, _z_ = 6 _._ 6
+0 _._ 012 log(SFR) log( _Z_ ) _−_ 0 _._ 74 log [2] ( _Z_ ) _Z_ = 0 _._ 05 _−_ 1 _Z_ _⊙_, SFR = 1-100 _M_ _⊙_ yr _[−]_ [1]

Olsen et al. (2017) _[a]_ log _L_ [CII] = 7 _._ 17 + 0 _._ 55 log SFR + 0 _._ 23 log _Z_ 1 _._ 8 _×_ 10 [6] Zoom-in simulations, _z_ _∼_ 6,
_M_ _⋆_ = (6 _−_ 80) _×_ 10 [8] _M_ _⊙_,
SFR = 3 _−_ 20 _M_ _⊙_ yr _[−]_ [1], _Z_ = 0 _._ 16 _−_ 0 _._ 45 _Z_ _⊙_
Lagache et al. (2018) _[b]_ log _L_ [CII] = 7 _._ 1 + (1 _._ 4 _−_ 0 _._ 07 _z_ ) log(SFR) _−_ 2 _._ 2 _×_ 10 [7] Semi-analytic models, _z_ = 4 _−_ 7
_−_ 0 _._ 07 _z_ _Z_ = 0 _._ 004 _−_ 4 _._ 4 _Z_ _⊙_

_a_ not correcting for the CMB temperature effects which are negligible at _z_ _∼_ 2 (c.f. Olsen et al. 2018 erratum).


_b_
no metallicity dependence, weak evolution with redshift _z_ .


**Figure** **6.** [C II ] luminosity ( _left_ ) and the [C II ]/SFR ratio versus SFR ( _right_ ) in SL2S 0217, compared to the nearby Dwarf Galaxy Survey
(Cormier et al. 2015, 2019) and A LPINE samples (Schaerer et al. 2020), and _z_ = 2 _−_ 7 observations of low-mass galaxies (Schaerer et al. 2015;
Knudsen et al. 2016; Bradaˇc et al. 2017), colored by 12 + log (O/H). For the A LPINE sources, we use the publicly-available SED-based SFR
estimates from Faisst et al. (2020). The different lines indicate different models from Table 3: Vallini et al. (2015) for _Z_ = 0 _._ 025 (thinnest
line), 0.05, and 0.1 _Z_ _⊙_ (thickest); De Looze et al. (2014) (with 1 _σ_ scatter indicated by shading); Olsen et al. (2017) and Lagache et al. (2018).
We do not show the Herrera-Camus et al. (2015) relation, as it generally predicts higher _L_ [CII] than De Looze et al. (2014) over the SFR range
studied here. The [C II ]/SFR ratio in SL2S 0217 is at least 30 _×_ lower than predicted by the De Looze et al. (2014) relation.



mass ( _M_ _⋆_ _≃_ 3 _×_ 10 [9] _M_ _⊙_ ), the Bradaˇc et al. (2017) source
is very similar to SL2S 0217, with SFR _≃_ 9 _M_ _⊙_ yr _[−]_ [1],
_M_ _⋆_ _≃_ 10 [8] _M_ _⊙_ and _Z_ = 0 _._ 2 _Z_ _⊙_ .
At higher stellar masses ( _M_ _⋆_ = 10 [9] _−_ 10 [11] _M_ _⊙_ ), the
A LPINE ALMA large programme (Le F`evre et al. 2020;
Faisst et al. 2020; B´ethermin et al. 2020) has recently observed the [C II ] line in 189 _z_ = 4 _−_ 6 galaxies with SFR =
1 _−_ 100 _M_ _⊙_ yr _[−]_ [1] (Schaerer et al. 2020). The A LPINE sources
are generally consistent with the De Looze et al. (2014) relation and have higher [C II ]/SFR than SL2S 0217, likely due



to their presumably higher metallicity (23 out of 118 A LPINE
sources are detected in the rest-frame 160- _µ_ m continuum indicating substantial dust masses, B´ethermin et al. 2020).
Finally, Figure 8 compares the [C II ] luminosity and

[C II ]/SFR ratio in SL2S 0217 to the compilation of _z_ = 5 _−_ 7
Ly _α_ emitters (Harikane et al. 2018; Matthee et al. 2019), and
the A LPINE survey (Schaerer et al. 2020). The Ly _α_ EW correlates closely with the Ly _α_ photons escape fraction (e.g.,
Verhamme et al. 2017; Harikane et al. 2018; Matthee et al.
2019); the sources with high Ly _α_ EW are thus expected to

10 R YBAK ET AL .



**Figure 7.** [C II ]/SFR ratio as a function of metallicity: comparison
of SL2S 0217 to the Cormier et al. (2015), Knudsen et al. (2016) and
Bradaˇc et al. (2017) sources (color-coded by SFR), and the different
relations from § 4.2, all for SL2S 0217-like SFR=23 _M_ _⊙_ yr _[−]_ [1] . The

[C II ]/SFR ratio in SL2S 0217 is consistent with the metallicitydependent relations of Vallini et al. (2015) and Olsen et al. (2017),
but much lower than predicted by De Looze et al. (2014) and Lagache et al. (2018).


be depleted in neutral ISM. For SL2S 0217, E19 derived
a photometric EW = 218 _±_ 12 A. [˚] Compared to the _z_ _≥_ 5
Ly _α_ emitters, SL2S 0217 has a low [C II ]/SFR ratio and is
a factor of _∼_ 3 below the Harikane et al. (2020) empirical
Ly _α_ EW - [C II ]/SFR relation. The low [C II ]/SFR ratio in
SL2S 0217 might be driven by its relatively compact size:
its source-plane _R_ 1 [UV] _/_ 2 _[∼]_ [0.35kpc,] [compared] [to] _[∼]_ [1] [kpc] [radii]
for _z_ _∼_ 6 sources (Carniani et al. 2018, 2020; Matthee et al.
2019) which might increase the ionized ISM fraction, suppressing the [C II ] emission.


4.4. _The fate of molecular gas in SL2S 0217_


Given the upper limits on the [C II ] and CO(2–1) luminosity, what can we say about the state of the molecular gas

in SL2S 0217? Does SL2S 0217 still contain a substantial

molecular gas reservoir, or is it at the very end of its starburst
phase, with the ISM depleted and ionized? We briefly discuss three facets of this problem: i) limits on the molecular
gas mass, ii) the possibility of the ISM being fully ionized
and iii) photoevaporation of molecular gas.
First, adopting the conservative magnification factor _µ_ =
16, the CO(2–1) upper limit translates to a (very weak) 3 _σ_
upper limit _M_ H 2 _≤_ 2 _×_ 10 [9] _M_ _⊙_, where we assume _r_ 2 _/_ 1 =
0 _._ 6 (Cormier et al. 2014) and a Galactic _α_ CO = 4 _._ 4 _M_ _⊙_ /(K
km s _[−]_ [1] pc [2] ). However, studies of nearby low-metallicity
dwarfs (e.g., Schruba et al. 2012; Hunt et al. 2015; Shi et al.
2016) found _α_ CO up to 3 dex higher than the Galactic value,
significantly weakening our _M_ gas upper limit.



**Figure** **8.** Upper limits on the [C II ]/SFR ratio in SL2S 0217 versus the Ly _α_ equivalent width (E19), compared to the Harikane et al.
(2018) and Matthee et al. (2019) compilations of _z_ = 5 _−_ 7 Ly _α_
emitters and the _z_ = 4 _._ 4 _−_ 5 _._ 9 A LPINE survey Schaerer et al.
(2020). SL2S 0217 is a factor of 3 below the empirical relation
of Harikane et al. (2020).


Alternatively, we can estimate the molecular gas mass
_M_ H 2 from the [C II ] luminosity, as originally proposed by
Zanella et al. (2018). Due to the very low metallicity of
SL2S 0217, rather than using the Zanella et al. (2018) relation (see below), we use the recently-published relation of
Madden et al. (2020) calibrated on the DGS sample:


_M_ H [[CII]] 2 (M20) = 132 _× L_ [0] [CII] _[.]_ [97] _[,]_ (3)


. which for SL2S 0217 yields _M_ H 2 _≤_ 2 _._ 1 _×_ 10 [9] _M_ _⊙_ . Alternatively, using the Zanella et al. (2018) relation calibrated on
more massive main-sequence galaxies:


_M_ H [[CII]] 2 (Z18) = 30 _× L_ [CII] _,_ (4)


we obtain _M_ H 2 _≤_ 0 _._ 8 _×_ 10 [9] _M_ _⊙_ ; although the extrapolation
of the Zanella et al. (2018) relation to the low- _Z_ regime might
not be straightforward. Both _M_ gas estimates imply a high gas
mass fraction _f_ gas = _M_ gas _/_ ( _M_ gas + _M_ _⋆_ ) _≃_ 0 _._ 8. This is consistent with high gas fractions and dynamical mass estimates
for _z_ = 1 _−_ 2 EELGs (Maseda et al. 2014) and simulations
of high-redshift dwarf galaxies (Ceverino et al. 2018).
A gas mass of _∼_ 10 [8] _M_ _⊙_ is also supported by the expectations from the Ferrara et al. (2019) model and the columndensity estimates from E19 (see § 4.2).
A gas mass of 10 [8] _M_ _⊙_ is further supported by the high
Σ SFR / _U_ ratio in SL2S 0217 (see § 4.2). With SFR=23 _M_ _⊙_
yr _[−]_ [1], SL2S 0217 will deplete its gas in _∼_ 10 Myr (likely
much faster, as some gas might be expelled from the system). This suggests that SL2S 0217 is in a final stage of an

intense starburst.

[CII] EMISSION IN SL2S 0217 11



Second, as indicated in § 4.1, a substantial fraction of the
gas reservoir might be ionized. Namely, the maximum column density proposed by E19 (Σ HI _≤_ 10 [21] _[.]_ [7] cm _[−]_ [2] ) is comparable to the ionized gas column depth of _∼_ 10 [21] _[.]_ [3] cm _[−]_ [2]

predicted by Ferrara et al. (2019) for SL2S 0217-like ionization parameter and metallicity. The fraction of the ionized gas might be further increased due to additional ionizing
sources. In particular, the unusually strong He II emission in
SL2S 0217 cannot be reproduced by standard photoionization models (B18) and requires additional ionization source,
such as radiative shocks (Allen et al. 2008; Plat et al. 2019)
or high-mass X-ray binaries as seen in, e.g., a nearby dwarf
I Zw 18 (Lebouteiller et al. 2017; Schaerer et al. 2019, but
c.f. Plat et al. 2019). This extra ionization would increase
the contribution of the ionized ISM to the [C II ] luminosity
compared to our photoionization models; on the other hand,
strong FUV fields might suppress the [C II ] emission by ionizing C [+] into C [2+] (e.g., Langer & Pineda 2015).
Third, the combination of the strong FUV fields and the
lack of ISM self-shielding at low metallicities can lead to
a rapid ionization and photoevaporation of the molecular
clouds on 1-10 Myr timescales, thus further suppressing the

[C II ] emission (Vallini et al. 2017).
We note that in the very near future, the warm neutral or
molecular gas might be traced at mid-infrared wavelengths
via the PAHs or rotational-vibrational H 2 emission using the
_James Webb Space Telescope_ . Alternatively, the gas mass in
SL2S 0217 can be constrained kinematically (e.g., Calistro
Rivera et al. 2018), using the integrated-field spectroscopy of
the bright C III ] 1909 A line (Maseda et al., in prep.). [˚]


4.5. _Detectability of [CII] emission from metal-poor dwarfs_
_at z_ _≥_ 6


What are the prospects of detecting the [C II ] 158- _µ_ m
emission in SL2S 0217 if it was at _z_ _∼_ 6? Assuming
_L_ [CII] = 2 _._ 6 _×_ 10 [7] _L_ _⊙_, achieving a spatially unresolved
5 _σ_ detection at _z_ = 6 would require _σ_ rms _∼_ 50 _µ_ Jy over
100 km s _[−]_ [1] bandwidth, which corresponds to _∼_ 10 hours of
ALMA on-source time. For comparison, the deepest ALMA
Band 6 observations to-date, delivered by the A SPECS (Walter et al. 2016; Gonz´alez-L´opez et al. 2020) and A LMACAL
(Oteo et al. 2016) projects and the Fujimoto et al. (2016)
compilation, reach sensitivities of _σ_ rms _∼_ 100 _µ_ Jy over the

same bandwidth.

Another promising way of studying the population of
galaxies at high redshift is the line-intensity mapping (e.g.
Gong et al. 2012; Silva et al. 2015). The feasibility of the

[C II ]-intensity mapping measurements depends critically on
the [C II ] luminosity function at _z_ _≥_ 6. A recent [C II ]intensity mapping feasibility study of Yue & Ferrara (2019)
considered several [C II ] luminosity function models. The
detectability of the [C II ] power spectrum is the highest for



the De Looze et al. (2014) dwarf-galaxies relation, and lowest for the Vallini et al. (2015) relation; the predictions for
the expected power-spectrum and shot-noise signal from the
two models differ by a factor of _∼_ 30. Consequently, if the
low [C II ]/SFR ratio in SL2S 0217 can be taken to validate
the Vallini et al. (2015) and Olsen et al. (2017) [C II ] luminosity models, the _z_ _≥_ 6 [C II ] intensity mapping signal will
fall below the detection threshold of the potential ALMA or
single-dish intensity-mapping experiments (e.g., a 1000-hour
programme on the CCAT-p telescope, Stacey et al. 2018).
Our analysis highlights the need to properly account for the
metallicity evolution of galaxies and its impact on the [C II ]

emission.


5. SUMMARY AND CONCLUSIONS


We have presented deep ALMA and PdBI observations of
the [C II ] 158- _µ_ m and CO(2–1) emission in the _z_ = 1 _._ 844
strongly lensed metal-poor dwarf galaxy SL2S 0217. In one
of the deepest ALMA Band 9 observations to-date, we obtain
a tentative 3-4 _σ_ detection of the [C II ] line. No CO(2–1)

emission is detected in the PdBI observations.

Our main conclusions are:


   - We report a tentative (3-4 _σ_ ) detection of the [C II ]
line based on the image-plane spectra; the sourceplane luminosity is _L_ [CII] _≤_ 2 _._ 1 _×_ 10 [7] _L_ _⊙_, derived
from 1.0-arcsec taper imaging, _R ≤_ 3 kpc aperture and
a 250 MHz bandwidth. We do not find strong evidence for [C II ] emission in the (u,v)-plane. The restframe 160- _µ_ m continuum and the CO(2–1) line are not
detected. Our tentative [C II ] detection extends the
molecular gas studies at _z_ _∼_ 2 by 1 dex in stellar mass,
down to the _M_ _⋆_ _≃_ 10 [8] _M_ _⊙_ regime.


   - The upper limit on the _L_ [CII] /SFR ratio in SL2S 0217
is 2 _×_ 10 [6] _L_ _⊙_ /( _M_ _⊙_ yr _[−]_ [1] ), within the range spanned by
nearby dwarf galaxies (Cormier et al. 2015), as well as
_z_ _≥_ 5 lensed dwarf EELGs and Ly _α_ emitters.


   - The [C II ]/ SFR ratio in SL2S 0217 is consistent
with the Vallini et al. (2015) and Olsen et al. (2017)
simulations-based models. However, the [C II ]/SFR
ratio in SL2S 0217 is 30 _×_ lower than predicted by the
locally-calibrated De Looze et al. (2014) relation.


   - We use M APPINGS photoionization modelling to predict the fraction of [C II ] emission arising in the ionized ISM. We find that our upper limit leaves room for
a significant (up to 80%) contribution from the PDRs;
however, we can not exclude that the ISM is fully ionized, particularly for low electron density. The contribution from the ionized ISM might be boosted due
to extra ionizing radiation from e.g., shocks or X-ray

binaries. Future ALMA and JWST observations of

12 R YBAK ET AL .



PDR tracers will allow us to directly probe the neu
tral/molecular ISM.


   - The tentative [C II ] detection and the high Σ SFR
and ionization parameter suggest a gas mass of few
10 [8] _M_ _⊙_ . In this scenario, SL2S 0217 will be in a late
phase of an extreme starburst and deplete its gas reservoir in _<_ 10 Myr. More robust constraints on the gas
mass might be obtained from spatially-resolved spectroscopic observations of the bright rest-frame FUV

lines.


   - If SL2S 0217 is representative of the _z_ _≥_ 6 lowmass galaxies, these will be within reach of deepfield ALMA observations (even without gravitational
lensing). On the other hand, a strong dependence of

[C II ]/SFR ratio on metallicity might strongly suppress
the [C II ] signal in line-intensity mapping experiments.


The large discrepancy between the [C II ]/SFR ratio in
SL2S 0217 and the widely-used De Looze et al. (2014) relation for present-day dwarf galaxies highlights the limitations
of applying locally established relations to high redshift. At
the same time, the good agreement between our tentative

[C II ] detection, high-redshift observations, and simulations
confirms that - though challenging to study - SL2S 0217 remains a powerful analogue of the sources from the Epoch of

Reionization.


ACKNOWLEDGMENTS


We thank the anonymous referee for their careful and constructive review of this manuscript which improved the content and clarity of this paper.


This paper makes use of the following ALMA data:
ADS/JAO.ALMA #2016.1.00142.S and #2016.1.00776.S.

ALMA is a partnership of ESO (representing its member
states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The
Joint ALMA Observatory is operated by ESO, AUI/NRAO

and NAOJ. This work is based on observations carried out

under project number X037 with the IRAM PdBI Interferometer. IRAM is supported by INSU/CNRS (France), MPG
(Germany) and IGN (Spain). We acknowledge assistance
from Allegro, the European ALMA Regional Center node

in the Netherlands.

MR and JAH acknowledge support of the VIDI research programme with project number 639.042.611, which
is (partly) financed by the Netherlands Organisation for
Scientific Research (NWO). MR acknowledges support
from the Leids Kerkhoven-Bosscha Fonds, subsidy number 19.2.075. EdC gratefully acknowledges the Australian



Research Council as the recipient of a Future Fellowship
(project FT150100079) and the ARC Centre of Excellence
for All Sky Astrophysics in 3 Dimensions (ASTRO 3D;
project CE170100013). MA has been supported by the grant

“CONICYT + PCI + INSTITUTO MAX PLANCK DE AS
TRONOMIA MPG190030” and “CONICYT+PCI+REDES

190194.” DKE is supported by the US National Science
Foundation through the Faculty Early Career Development
(CAREER) Program, grant AST-1255591. CP is supported
by the Canadian Space Agency under a contract with NRC
Herzberg Astronomy and Astrophysics.


_Facilities:_ ALMA, IRAM:Interferometer

[CII] EMISSION IN SL2S 0217 13


REFERENCES



Allen, M. G., Groves, B. A., Dopita, M. A., Sutherland, R. S., &

[Kewley, L. J. 2008, ApJS, 178, 20, doi: 10.1086/589652](http://doi.org/10.1086/589652)

Amor´ın, R., P´erez-Montero, E., Contini, T., et al. 2015, A&A, 578,

[A105, doi: 10.1051/0004-6361/201322786](http://doi.org/10.1051/0004-6361/201322786)

Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009,

ARA&A, 47, 481,

[doi: 10.1146/annurev.astro.46.060407.145222](http://doi.org/10.1146/annurev.astro.46.060407.145222)

Atek, H., Siana, B., Scarlata, C., et al. 2011, ApJ, 743, 121,

[doi: 10.1088/0004-637X/743/2/121](http://doi.org/10.1088/0004-637X/743/2/121)

Atek, H., Richard, J., Jauzac, M., et al. 2015, ApJ, 814, 69,

[doi: 10.1088/0004-637X/814/1/69](http://doi.org/10.1088/0004-637X/814/1/69)

Berg, D. A., Erb, D. K., Auger, M. W., Pettini, M., & Brammer,

[G. B. 2018, ApJ, 859, 164, doi: 10.3847/1538-4357/aab7fa](http://doi.org/10.3847/1538-4357/aab7fa)

B´ethermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643,

[A2, doi: 10.1051/0004-6361/202037649](http://doi.org/10.1051/0004-6361/202037649)

Bouwens, R. J., Illingworth, G. D., Franx, M., et al. 2009, ApJ,

[705, 936, doi: 10.1088/0004-637X/705/1/936](http://doi.org/10.1088/0004-637X/705/1/936)

Bradaˇc, M., Garcia-Appadoo, D., Huang, K.-H., et al. 2017, ApJL,

[836, L2, doi: 10.3847/2041-8213/836/1/L2](http://doi.org/10.3847/2041-8213/836/1/L2)

Brammer, G. B., S´anchez-Janssen, R., Labb´e, I., et al. 2012, ApJL,

[758, L17, doi: 10.1088/2041-8205/758/1/L17](http://doi.org/10.1088/2041-8205/758/1/L17)

Brisbin, D., Ferkinhoff, C., Nikola, T., et al. 2015, ApJ, 799, 13,

[doi: 10.1088/0004-637X/799/1/13](http://doi.org/10.1088/0004-637X/799/1/13)

Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863,

[56, doi: 10.3847/1538-4357/aacffa](http://doi.org/10.3847/1538-4357/aacffa)

Carniani, S., Maiolino, R., Pallottini, A., et al. 2017, A&A, 605,

[A42, doi: 10.1051/0004-6361/201630366](http://doi.org/10.1051/0004-6361/201630366)

Carniani, S., Maiolino, R., Amorin, R., et al. 2018, MNRAS, 478,

[1170, doi: 10.1093/mnras/sty1088](http://doi.org/10.1093/mnras/sty1088)

Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499,

[5136, doi: 10.1093/mnras/staa3178](http://doi.org/10.1093/mnras/staa3178)

Ceverino, D., Klessen, R. S., & Glover, S. C. O. 2018, MNRAS,

[480, 4842, doi: 10.1093/mnras/sty2124](http://doi.org/10.1093/mnras/sty2124)

Cooray, A., Fu, H., Calanog, J., et al. 2011, arXiv e-prints,

arXiv:1110.3784. [https://arxiv.org/abs/1110.3784](https://arxiv.org/abs/1110.3784)

Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2014, A&A,

[564, A121, doi: 10.1051/0004-6361/201322096](http://doi.org/10.1051/0004-6361/201322096)

[—. 2015, A&A, 578, A53, doi: 10.1051/0004-6361/201425207](http://doi.org/10.1051/0004-6361/201425207)

Cormier, D., Abel, N. P., Hony, S., et al. 2019, A&A, 626, A23,

[doi: 10.1051/0004-6361/201834457](http://doi.org/10.1051/0004-6361/201834457)

Croxall, K. V., Smith, J. D., Pellegrini, E., et al. 2017, ApJ, 845,

[96, doi: 10.3847/1538-4357/aa8035](http://doi.org/10.3847/1538-4357/aa8035)

D’Agostino, J. J., y, L. J., Groves, B., et al. 2019, ApJ, 878, 2,

[doi: 10.3847/1538-4357/ab1d5e](http://doi.org/10.3847/1538-4357/ab1d5e)

De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568,

[A62, doi: 10.1051/0004-6361/201322489](http://doi.org/10.1051/0004-6361/201322489)

Erb, D. K., Berg, D. A., Auger, M. W., et al. 2019, ApJ, 884, 7,

[doi: 10.3847/1538-4357/ab3daf](http://doi.org/10.3847/1538-4357/ab3daf)



Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247,

[61, doi: 10.3847/1538-4365/ab7ccd](http://doi.org/10.3847/1538-4365/ab7ccd)

Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1,

[doi: 10.1093/mnras/stz2031](http://doi.org/10.1093/mnras/stz2031)

Fujimoto, S., Ouchi, M., Ono, Y., et al. 2016, ApJS, 222, 1,

[doi: 10.3847/0067-0049/222/1/1](http://doi.org/10.3847/0067-0049/222/1/1)

Geach, J. E., Simpson, C., Rawlings, S., Read, A. M., & Watson,

M. 2007, MNRAS, 381, 1369,

[doi: 10.1111/j.1365-2966.2007.12329.x](http://doi.org/10.1111/j.1365-2966.2007.12329.x)

Gong, Y., Cooray, A., Silva, M., et al. 2012, ApJ, 745, 49,

[doi: 10.1088/0004-637X/745/1/49](http://doi.org/10.1088/0004-637X/745/1/49)

Gonz´alez-L´opez, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897,

[91, doi: 10.3847/1538-4357/ab765b](http://doi.org/10.3847/1538-4357/ab765b)

Groves, B. A., & Allen, M. G. 2010, NewA, 15, 614,

[doi: 10.1016/j.newast.2010.02.005](http://doi.org/10.1016/j.newast.2010.02.005)

Harikane, Y., Ouchi, M., Shibuya, T., et al. 2018, ApJ, 859, 84,

[doi: 10.3847/1538-4357/aabd80](http://doi.org/10.3847/1538-4357/aabd80)

Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93,

[doi: 10.3847/1538-4357/ab94bd](http://doi.org/10.3847/1538-4357/ab94bd)

Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015,

[ApJ, 800, 1, doi: 10.1088/0004-637X/800/1/1](http://doi.org/10.1088/0004-637X/800/1/1)

Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science,

[7, 200556, doi: 10.1098/rsos.200556](http://doi.org/10.1098/rsos.200556)

Hollenbach, D. J., & Tielens, A. G. G. M. 1997, ARA&A, 35, 179,

[doi: 10.1146/annurev.astro.35.1.179](http://doi.org/10.1146/annurev.astro.35.1.179)

Hunt, L. K., Garc´ıa-Burillo, S., Casasola, V., et al. 2015, A&A,

[583, A114, doi: 10.1051/0004-6361/201526553](http://doi.org/10.1051/0004-6361/201526553)

Jaskot, A. E., & Ravindranath, S. 2016, ApJ, 833, 136,

[doi: 10.3847/1538-4357/833/2/136](http://doi.org/10.3847/1538-4357/833/2/136)

Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017, MNRAS,

[468, 4831, doi: 10.1093/mnras/stx608](http://doi.org/10.1093/mnras/stx608)

Kewley, L. J., Nicholls, D. C., & Sutherland, R. S. 2019, ARA&A,

[57, 511, doi: 10.1146/annurev-astro-081817-051832](http://doi.org/10.1146/annurev-astro-081817-051832)

Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS,

[462, L6, doi: 10.1093/mnrasl/slw114](http://doi.org/10.1093/mnrasl/slw114)

Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130,

[doi: 10.1051/0004-6361/201732019](http://doi.org/10.1051/0004-6361/201732019)

Langan, I., Ceverino, D., & Finlator, K. 2020, MNRAS, 494, 1988,

[doi: 10.1093/mnras/staa880](http://doi.org/10.1093/mnras/staa880)

Langer, W. D., & Pineda, J. L. 2015, A&A, 580, A5,

[doi: 10.1051/0004-6361/201525950](http://doi.org/10.1051/0004-6361/201525950)

Le F`evre, O., B´ethermin, M., Faisst, A., et al. 2020, A&A, 643,

[A1, doi: 10.1051/0004-6361/201936965](http://doi.org/10.1051/0004-6361/201936965)

Lebouteiller, V., P´equignot, D., Cormier, D., et al. 2017, A&A,

[602, A45, doi: 10.1051/0004-6361/201629675](http://doi.org/10.1051/0004-6361/201629675)

Leitherer, C., Ortiz Ot´alvaro, P. A., Bresolin, F., et al. 2010, ApJS,

[189, 309, doi: 10.1088/0067-0049/189/2/309](http://doi.org/10.1088/0067-0049/189/2/309)

Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123,

[3, doi: 10.1086/313233](http://doi.org/10.1086/313233)

14 R YBAK ET AL .



Levesque, E. M., Leitherer, C., Ekstrom, S., Meynet, G., &

Schaerer, D. 2012, ApJ, 751, 67,

[doi: 10.1088/0004-637X/751/1/67](http://doi.org/10.1088/0004-637X/751/1/67)


Lupi, A., & Bovino, S. 2020, MNRAS, 492, 2818,

[doi: 10.1093/mnras/staa048](http://doi.org/10.1093/mnras/staa048)


Madden, S. C., R´emy-Ruyer, A., Galametz, M., et al. 2013, PASP,

[125, 600, doi: 10.1086/671138](http://doi.org/10.1086/671138)


Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643,

[A141, doi: 10.1051/0004-6361/202038860](http://doi.org/10.1051/0004-6361/202038860)


Maiolino, R., Cox, P., Caselli, P., et al. 2005, A&A, 440, L51,

[doi: 10.1051/0004-6361:200500165](http://doi.org/10.1051/0004-6361:200500165)


Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452,

[54, doi: 10.1093/mnras/stv1194](http://doi.org/10.1093/mnras/stv1194)


Maseda, M. V., van der Wel, A., da Cunha, E., et al. 2013, ApJL,

[778, L22, doi: 10.1088/2041-8205/778/1/L22](http://doi.org/10.1088/2041-8205/778/1/L22)


Maseda, M. V., van der Wel, A., Rix, H.-W., et al. 2014, ApJ, 791,

[17, doi: 10.1088/0004-637X/791/1/17](http://doi.org/10.1088/0004-637X/791/1/17)


[—. 2018, ApJ, 854, 29, doi: 10.3847/1538-4357/aaa76e](http://doi.org/10.3847/1538-4357/aaa76e)


Masters, D., McCarthy, P., Siana, B., et al. 2014, ApJ, 785, 153,

[doi: 10.1088/0004-637X/785/2/153](http://doi.org/10.1088/0004-637X/785/2/153)


Matthee, J., Sobral, D., Boogaard, L. A., et al. 2019, ApJ, 881, 124,

[doi: 10.3847/1538-4357/ab2f81](http://doi.org/10.3847/1538-4357/ab2f81)


McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K.

2007, in Astronomical Data Analysis Software and Systems

XVI ASP Conference Series, Vol. 376, proceedings of the

conference held 15-18 October 2006 in Tucson, Arizona, USA.

Edited by Richard A. Shaw, Frank Hill and David J. Bell., p.127,

Vol. 376, 127


Olsen, K., Greve, T. R., Narayanan, D., et al. 2017, ApJ, 846, 105,

[doi: 10.3847/1538-4357/aa86b4](http://doi.org/10.3847/1538-4357/aa86b4)


[—. 2018, ApJ, 857, 148, doi: 10.3847/1538-4357/aabaf9](http://doi.org/10.3847/1538-4357/aabaf9)


Oteo, I., Zwaan, M. A., Ivison, R. J., Smail, I., & Biggs, A. D.

[2016, ApJ, 822, 36, doi: 10.3847/0004-637X/822/1/36](http://doi.org/10.3847/0004-637X/822/1/36)


Pallottini, A., Ferrara, A., Decataldo, D., et al. 2019, MNRAS, 487,

[1689, doi: 10.1093/mnras/stz1383](http://doi.org/10.1093/mnras/stz1383)


Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A,

[641, A6, doi: 10.1051/0004-6361/201833910](http://doi.org/10.1051/0004-6361/201833910)


Plat, A., Charlot, S., Bruzual, G., et al. 2019, MNRAS, 490, 978,

[doi: 10.1093/mnras/stz2616](http://doi.org/10.1093/mnras/stz2616)


Robertson, B. E., Ellis, R. S., Dunlop, J. S., McLure, R. J., &

[Stark, D. P. 2010, Nature, 468, 49, doi: 10.1038/nature09527](http://doi.org/10.1038/nature09527)


Robertson, B. E., Ellis, R. S., Furlanetto, S. R., & Dunlop, J. S.

[2015, ApJL, 802, L19, doi: 10.1088/2041-8205/802/2/L19](http://doi.org/10.1088/2041-8205/802/2/L19)


Rybak, M. 2017, PhD thesis, Ludwig Maximilian University of

Munich.

[https://edoc.ub.uni-muenchen.de/23392/1/Rybak](https://edoc.ub.uni-muenchen.de/23392/1/Rybak_Matus.pdf) ~~M~~ atus.pdf


Rybak, M., McKean, J. P., Vegetti, S., Andreani, P., & White,

[S. D. M. 2015, MNRAS, 451, L40, doi: 10.1093/mnrasl/slv058](http://doi.org/10.1093/mnrasl/slv058)



Schaerer, D., Fragos, T., & Izotov, Y. I. 2019, A&A, 622, L10,

[doi: 10.1051/0004-6361/201935005](http://doi.org/10.1051/0004-6361/201935005)


Schaerer, D., Boone, F., Jones, T., et al. 2015, A&A, 576, L2,

[doi: 10.1051/0004-6361/201425542](http://doi.org/10.1051/0004-6361/201425542)

Schaerer, D., Ginolfi, M., B´ethermin, M., et al. 2020, A&A, 643,

[A3, doi: 10.1051/0004-6361/202037617](http://doi.org/10.1051/0004-6361/202037617)

Schruba, A., Leroy, A. K., Walter, F., et al. 2012, AJ, 143, 138,

[doi: 10.1088/0004-6256/143/6/138](http://doi.org/10.1088/0004-6256/143/6/138)

Shi, Y., Wang, J., Zhang, Z.-Y., et al. 2016, Nature

[Communications, 7, 13789, doi: 10.1038/ncomms13789](http://doi.org/10.1038/ncomms13789)

Silva, M., Santos, M. G., Cooray, A., & Gong, Y. 2015, ApJ, 806,

[209, doi: 10.1088/0004-637X/806/2/209](http://doi.org/10.1088/0004-637X/806/2/209)

Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010,

[ApJ, 724, 957, doi: 10.1088/0004-637X/724/2/957](http://doi.org/10.1088/0004-637X/724/2/957)

Stacey, G. J., Aravena, M., Basu, K., et al. 2018, in Society of

Photo-Optical Instrumentation Engineers (SPIE) Conference

Series, Vol. 10700, Proc. SPIE, 107001M,

[doi: 10.1117/12.2314031](http://doi.org/10.1117/12.2314031)

Stark, D. P. 2016, ARA&A, 54, 761,

[doi: 10.1146/annurev-astro-081915-023417](http://doi.org/10.1146/annurev-astro-081915-023417)

Stark, D. P., Richard, J., Charlot, S., et al. 2015, MNRAS, 450,

[1846, doi: 10.1093/mnras/stv688](http://doi.org/10.1093/mnras/stv688)

Stark, D. P., Ellis, R. S., Charlot, S., et al. 2017, MNRAS, 464,

[469, doi: 10.1093/mnras/stw2233](http://doi.org/10.1093/mnras/stw2233)

Sutter, J., Dale, D. A., Croxall, K. V., et al. 2019, ApJ, 886, 60,

[doi: 10.3847/1538-4357/ab4da5](http://doi.org/10.3847/1538-4357/ab4da5)

Tang, M., Stark, D. P., Chevallard, J., & Charlot, S. 2019, MNRAS,

[489, 2572, doi: 10.1093/mnras/stz2236](http://doi.org/10.1093/mnras/stz2236)

Tu, H., Gavazzi, R., Limousin, M., et al. 2009, A&A, 501, 475,

[doi: 10.1051/0004-6361/200911963](http://doi.org/10.1051/0004-6361/200911963)

Vallini, L., Ferrara, A., Pallottini, A., Carniani, S., & Gallerani, S.

[2020, MNRAS, 495, L22, doi: 10.1093/mnrasl/slaa047](http://doi.org/10.1093/mnrasl/slaa047)

Vallini, L., Ferrara, A., Pallottini, A., & Gallerani, S. 2017,

[MNRAS, 467, 1300, doi: 10.1093/mnras/stx180](http://doi.org/10.1093/mnras/stx180)

Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B.

[2015, ApJ, 813, 36, doi: 10.1088/0004-637X/813/1/36](http://doi.org/10.1088/0004-637X/813/1/36)

van der Wel, A., Straughn, A. N., Rix, H. W., et al. 2011, ApJ, 742,

[111, doi: 10.1088/0004-637X/742/2/111](http://doi.org/10.1088/0004-637X/742/2/111)

Verhamme, A., Orlitov´a, I., Schaerer, D., et al. 2017, A&A, 597,

[A13, doi: 10.1051/0004-6361/201629264](http://doi.org/10.1051/0004-6361/201629264)

Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67,

[doi: 10.3847/1538-4357/833/1/67](http://doi.org/10.3847/1538-4357/833/1/67)

[Wright, E. L. 2006, PASP, 118, 1711, doi: 10.1086/510102](http://doi.org/10.1086/510102)

Yue, B., & Ferrara, A. 2019, MNRAS, 490, 1928,

[doi: 10.1093/mnras/stz2728](http://doi.org/10.1093/mnras/stz2728)

Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481,

[1976, doi: 10.1093/mnras/sty2394](http://doi.org/10.1093/mnras/sty2394)

Zitrin, A., Ellis, R. S., Belli, S., & Stark, D. P. 2015, ApJL, 805,

[L7, doi: 10.1088/2041-8205/805/1/L7](http://doi.org/10.1088/2041-8205/805/1/L7)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Extract real and imaginary visibilities over a 250 MHz bandwidth (keeping XX and YY separate), estimate noise from per-scan baseline rms, forward-model sky brightness distributions (HST F606W arc and R <= 1, 2, 3 kpc apertures) multiplied by a Gaussian primary beam for total fluxes from 0 to 50 mJy, and compute the log-likelihood PDF of S_[CII].",
  "failed_quote": "First, we extract the visibility data (real and imaginary parts) at 669.970 _±_ 0.125 GHz (same bandwidth as used for the image-plane analysis)."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Grid evaluation of Gaussian log-likelihood log L proportional to -sum (V_model - V_data)^2 / sigma^2 over S_[CII] = 0 to 50 mJy.",
  "failed_quote": "We calculate the log-likelihood value log _L_ _∝−_ [] _i_ [(] _[V]_ [ (] _[u]_ _[i]_ _[, v]_ _[i]_ [)] [model] _[−]_ _V_ ( _u_ _i_ _, v_ _i_ ) [data] ) [2] _/σ_ ( _u_ _i_ _, v_ _i_ ) [2] ."
 }
]
```
