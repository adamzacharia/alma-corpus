# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023ApJ...952...48H\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version June 16, 2023
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Big** **Three** **Dragons:** **Molecular** **Gas** **in** **a** **Bright** **Lyman-Break** **Galaxy** **at** _z_ = 7 _._ 15


Takuya [Hashimoto,](http://orcid.org/0000-0002-0898-4038) [1] Akio [K.](http://orcid.org/0000-0002-7779-8677) Inoue, [2, 3] Yuma [Sugahara,](http://orcid.org/0000-0001-6958-7856) [3, 4] Yoshinobu Fudamoto, [3, 4] Seiji [Fujimoto,](http://orcid.org/0000-0001-7201-5066) [5, 6]

K.K. [Knudsen,](http://orcid.org/0000-0002-7821-8873) [7] Hiroshi Matsuo, [4, 8] Yoichi [Tamura,](http://orcid.org/0000-0003-4807-8117) [9] Satoshi [Yamanaka,](http://orcid.org/0000-0002-7738-5290) [10] Yuichi [Harikane,](http://orcid.org/0000-0002-6047-430X) [11, 12] Nario Kuno, [1]

[Yoshiaki](http://orcid.org/0000-0001-9011-7605) Ono, [11] [Dragan](http://orcid.org/0000-0002-3848-1757) Salak, [13, 14] and Nozomi Ishii [1]


1 _Tomonaga_ _Center_ _for_ _the_ _History_ _of_ _the_ _Universe_ _(TCHoU),_ _Faculty_ _of_ _Pure_ _and_ _Applied_ _Sciences,_ _University_ _of_ _Tsukuba,_ _Tsukuba,_
_Ibaraki_ _305-8571,_ _Japan_
2 _Department_ _of_ _Physics,_ _School_ _of_ _Advanced_ _Science_ _and_ _Engineering,_ _Waseda_ _University,_ _3-4-1,_ _Okubo,_ _Shinjuku,_ _Tokyo_ _169-8555_
3 _Waseda_ _Research_ _Institute_ _for_ _Science_ _and_ _Engineering,_ _Faculty_ _of_ _Science_ _and_ _Engineering,_ _Waseda_ _University,_ _3-4-1,_ _Okubo,_
_Shinjuku,_ _Tokyo_ _169-8555,_ _Japan_
4 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
5 _Cosmic_ _Dawn_ _Center_ _(DAWN),_ _Copenhagen,_ _Denmark_
6 _Niels_ _Bohr_ _Institute,_ _University_ _of_ _Copenhagen,_ _Jagtvej_ _128,_ _DK-2200_ _Copenhagen_ _N,_ _Denmark_
7 _Department_ _of_ _Space,_ _Earth_ _and_ _Environment,_ _Chalmers_ _University_ _of_ _Technology,_ _Onsala_ _Space_ _Observatory,_ _SE-43992_ _Onsala,_ _Sweden_
8 _Graduate_ _University_ _for_ _Advanced_ _Studies_ _(SOKENDAI),_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
9 _Department_ _of_ _Physics,_ _Graduate_ _School_ _of_ _Science,_ _Nagoya_ _University,_ _Nagoya_ _464-8602,_ _Japan_
10 _General_ _Education_ _Department,_ _National_ _Institute_ _of_ _Technology,_ _Toba_ _College,_ _1-1,_ _Ikegami-cho,_ _Toba,_ _Mie_ _517-8501,_ _Japan_
11 _Institute_ _for_ _Cosmic_ _Ray_ _Research,_ _The_ _University_ _of_ _Tokyo,_ _5-1-5_ _Kashiwanoha,_ _Kashiwa,_ _Chiba_ _277-8582,_ _Japan_
12 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _College_ _London,_ _Gower_ _Street,_ _London_ _WC1E_ _6BT,_ _UK_
13 _Institute_ _for_ _the_ _Advancement_ _of_ _Higher_ _Education,_ _Hokkaido_ _University,_ _Kita_ _17_ _Nishi_ _8,_ _Kita-ku,_ _Sapporo,_ _Hokkaido_ _060-0817,_ _Japan_
14 _Department_ _of_ _Cosmosciences,_ _Graduate_ _School_ _of_ _Science,_ _Hokkaido_ _University,_ _Kita_ _10_ _Nishi_ _8,_ _Kita-ku,_ _Sapporo,_ _Hokkaido_
_060-0810,_ _Japan_


(Received 2022 Mar 4; Accepted 2023 Jun 11)


Submitted to ApJ


ABSTRACT


We report ALMA Band 3 observations of CO(6-5), CO(7-6), and [Ci](2-1) in B14-65666 (“Big Three
Dragons”), one of the brightest Lyman-Break Galaxies at _z_ _>_ 7 in the rest-frame ultraviolet continuum,
far-infrared continuum, and emission lines of [Oiii] 88 _µ_ m and [Cii] 158 _µ_ m. CO(6-5), CO(7-6), and

[Ci](2-1), whose 3 _σ_ upper limits on the luminosities are approximately 40 times fainter than the [Cii]
luminosity, are all not detected. The _L_ [CII] / _L_ CO(6 _−_ 5) and _L_ [CII] / _L_ CO(7 _−_ 6) ratios are higher than the
typical ratios obtained in dusty star-forming galaxies or quasar host galaxies at similar redshifts, and
they may suggest a lower gas density in the photodissociated region in B14-65666. By using the (1)

[Cii] luminosity, (2) dust mass-to-gas mass ratio, and (3) a dynamical mass estimate, we find that the
molecular gas mass ( _M_ mol ) is (0 _._ 05 _−_ 11) _×_ 10 [10] _M_ _⊙_ . This value is consistent with the upper limit
inferred from the nondetection of mid- _J_ CO and [Ci](2-1). Despite the large uncertauinty in _M_ mol, we
estimate a molecular gas-to-stellar mass ratio ( _µ_ gas ) of 0 _._ 65 _−_ 140 and a gas depletion time ( _τ_ dep ) of
2 _._ 5 _−_ 550 Myr; these values are broadly consistent with those of other high-redshift galaxies. B14-65666
could be an ancestor of a passive galaxy at _z_ ≳ 4 if no gas is fueled from outside the galaxy.


_Keywords:_ galaxies: high-redshift, galaxies: ISM, galaxies: star formation,



1. INTRODUCTION


Corresponding author: Takuya Hashimoto

[hashimoto.takuya.ga@u.tsukuba.ac.jp](mailto: hashimoto.takuya.ga@u.tsukuba.ac.jp)



Understanding the properties of molecular gas
through cosmic time is an important topic in galaxy
formation and evolution, as molecular gas is the fuel for
star formation. The molecular gas mass, _M_ mol, is often determined from the luminosity of carbon monoxide
( [12] C [16] O; hereafter written as simply “CO”; e.g. Bo

2 Hashimoto et al.



latto et al. 2013), dust mass (e.g. Magdis et al. 2012),
and radiation from cold dust sensitive to dust mass (e.g.
Scoville et al. 2016). Based on _M_ mol estimates, previous studies have shown that high-redshift ( _z_ ≳ 2) starforming galaxies (SFGs) have (1) higher molecular gasto-stellar mass ratios ( _µ_ gas _≡_ _M_ mol _/M_ _∗_ ) and (2) shorter
molecular gas depletion times ( _τ_ dep _≡_ _M_ mol _/_ SFR) than
local galaxies (e.g. Tacconi et al. 2020).
Low- _J_ CO transitions probe the cold and diffuse
molecular gas, whereas mid- _J_ transitions [1] probe the
warm and dense regions of the molecular gas. Based on
zoom-in cosmological hydrodynamical simulations implementing radiative transfer calculations, Vallini et al.
(2019) have shown that galaxies in the epoch of reionization (EoR; _z_ ≳ 6) have high gas excitation conditions with CO luminosity peaks at an upper rotational level ( _J_ u ) _≈_ 6 _−_ 7 as a result of their high starformation surface density and the resulting higher temperature of the giant molecular clouds. These authors
show that the sensitivity of the Atacama Large Millimeter/Submillimeter Array (ALMA) telescope is sufficient
to detect these mid- _J_ CO transitions in a reasonable

amount of integration time.
Observations of the low- _J_ CO transitions in galaxies in the EoR are challenging because these transitions
are redshifted to longer radio wavelengths, where instruments are less sensitive. Furthermore, at high redshift,
the cosmic microwave background (CMB) has a significant impact upon the CO line emission (e.g. Sakamoto
1999; Combes et al. 1999; Papadopoulos et al. 2000;
Obreschkow et al. 2009; da Cunha et al. 2013; Zhang
et al. 2016; Tunnard & Greve 2016). Firstly, the increased CMB heating leads to a greater population of
high rotational levels, thereby boosting higher- _J_ CO
luminosities. Secondly, the CMB serves as a stronger
background, particularly at the wavelength of the lower_J_ transitions. As a result, it becomes challenging to observe low- _J_ CO compared to the mid- _J_ transitions at
high redshift. Hence, to efficiently detect the molecular
gas component, we target the brighter mid- _J_ transitions,
which can be observed far more efficiently with sub-/mm
facilities.
The [Ci] [3] _P_ 1 _→_ [3] _P_ 0 and [Ci] [3] _P_ 2 _→_ [3] _P_ 1 lines could be
more reliable tracers of the bulk of cold gas than midand even low- _J_ transitions, particularly under certain
conditions (e.g. high cosmic ray flux, low metallicity).
For example, Weiß et al. (2005); Offner et al. (2014),
and Glover et al. (2015) show that [Ci] is optically thin
and traces the surfaces of molecular clouds in a range of


1 Hereafter, we refer to CO( _J_ = 6 _→_ 5) and CO( _J_ = 7 _→_ 6) as
the mid- _J_ transitions.



environments (e.g. Papadopoulos et al. 2018; Shimajiri
et al. 2013; Jiao et al. 2019).
To date, CO line observations in the EoR were mainly
focused on dusty star-forming galaxies (DSFGs) and
quasar host galaxies that both have high IR luminosities
( _L_ IR ≳ 10 [12] _−_ 10 [13] _L_ _⊙_ ) and large SFRs ≳ 100 _−_ 1000 _M_ _⊙_
yr _[−]_ [1] . Among the DSFGs at _z_ _>_ 5, seven sources were
detected in the low- _J_ CO line ( _J_ up = 1, 2) (Combes et al.
2012; Rawle et al. 2014; Pavesi et al. 2018; Riechers et al.
2013, 2020, 2021; Zavala et al. 2022), and more than 11
sources were detected in the mid- _J_ CO line ( _J_ up _∼_ 6 _−_ 7)
(Combes et al. 2012; Rawle et al. 2014; Vieira et al. 2013;
Riechers et al. 2013, 2017, 2020; Strandet et al. 2016,
2017; Apostolovski et al. 2019; Zavala et al. 2018; Casey
et al. 2019; Jin et al. 2019; Jarugula et al. 2021; Vieira
et al. 2022; Asboth et al. 2016). Among the quasar host
galaxies at _z_ ≳ 6, at least eight sources were detected in
the low- _J_ CO line (Venemans et al. 2017a; Wang et al.
2010, 2011a, 2016; Stefan et al. 2015; Shao et al. 2019),
and more than 25 sources were detected in the mid- _J_ CO
line (e.g. Novak et al. 2019; Venemans et al. 2017a,b;
Decarli et al. 2022; Yang et al. 2019; Riechers et al. 2009;
Wang et al. 2019; Li et al. 2020; Walter et al. 2003; Carilli & Walter 2013; Wang et al. 2016, 2011b). In contrast, among “normal” SFGs at _z_ _∼_ 6, only one source
was detected in the low- _J_ CO line (Pavesi et al. 2019),
and two sources were detected in the CO( _J_ = 6 _→_ 5)
line (D’Odorico et al. 2018; Vieira et al. 2022).
It is therefore of interest to investigate the nature
of the molecular gas in B14-65666 (“Big Three Dragons” [2] ) at _z_ = 7 _._ 1520. This galaxy shows no clear signs
of active galactic nucleus (AGN) activity; nonetheless,
it is one of the brightest LBGs at _z_ ≳ 6 in the restframe ultraviolet (UV) continuum, far-infrared (FIR)
continuum, and FIR emission lines of [Oiii] 88 _µ_ m and

[Cii] 158 _µ_ m (Bowler et al. 2014; Furusawa et al. 2016;
Hashimoto et al. 2019; Sugahara et al. 2021). The large
IR and [Cii] luminosities imply the presence of a significant amount of dust and neutral gas, respectively, effectively shielding CO from the UV radiation. Previous
studies have also shown that B14-65666 is an example of
the highest- _z_ starburst galaxies owing to a major merger
event (Bowler et al. 2017; Hashimoto et al. 2019). Thus,
a detailed study of the molecular gas in B14-65666 may
provide information on the connection between mergers,
starbursts, the emergence of quasars, and quenching of
star formation at high redshift (e.g. Hopkins et al. 2008).


2 “Big Three Dragons” is a hand in a Mahjong game with triplets
or quads of all three dragons.

Molecular Gas Properties of “Big Three Dragons” 3



**Table** **1.** Summary of Previous Measurements


Parameters Measurements Ref.


_L_ UV [ _L_ _⊙_ ] 2 _._ 0 _×_ 10 [11] B17
_L_ [OIII] [ _L_ _⊙_ ] (3 _._ 4 _±_ 0 _._ 4) _×_ 10 [9] H19
_L_ [CII] [ _L_ _⊙_ ] (1 _._ 1 _±_ 0 _._ 1) _×_ 10 [9] H19
_L_ TIR ( _T_ d = 40 K, _β_ = 2 _._ 0) [ _L_ _⊙_ ] 4 _._ 0 _×_ 10 [11] S21
_L_ TIR ( _T_ d = 80 K, _β_ = 1 _._ 0) [ _L_ _⊙_ ] 12 _._ 6 _×_ 10 [11] S21
_L_ FIR ( _T_ d = 40 K, _β_ = 2 _._ 0) [ _L_ _⊙_ ] 3 _._ 1 _×_ 10 [11] _L_ FIR ( _T_ d = 80 K, _β_ = 1 _._ 0) [ _L_ _⊙_ ] 5 _._ 3 _×_ 10 [11] 

Note— The upper limit is 3 _σ_ . The total-infrared luminosity, _L_ TIR, and FIR luminosity, _L_ FIR, are estimated by integrating the modified blackbody radiation at 8 _−_ 1000 and
42 _._ 5 _−_ 122 _._ 5 _µ_ m, respectively. Following Sugahara et al.
(2021), we consider two combinations of ( _T_ d, _β_ ) = (40 K,
2.0) and (80 K, 1.0). B17, H19, and S21 refer to the studies
by Bowler et al. 2017, Hashimoto et al. 2019, and Sugahara
et al. 2021, respectively.


Herein, we present new ALMA Band 3 observations
of B14-65666. Our observational setup efficiently covers
CO( _J_ = 6 _→_ 5), CO( _J_ = 7 _→_ 6), and [Ci] [3] _P_ 2 _→_ [3] _P_ 1 .

[Ci] is highly complementary to mid- _J_ CO; it could trace
the bulk of the cold molecular gas component without
the need for low- _J_ CO observations.

The rest of this paper is structured as follows. In
§2, we introduce the target galaxy, B14-65666. In §3,
we describe our ALMA Band 3 data. In §4, we calculate the line luminosities and estimate the molecu
lar gas mass in the galaxy. In §5, we compare B1465666 with other high- _z_ objects in terms of the luminosity ratios and interstellar medium (ISM) properties.
§6 presents discussions in the context of _µ_ gas and _τ_ dep .
Finally, §7 presents our conclusions. Throughout this
paper, magnitudes are given in the AB system (Oke &
Gunn 1983), and we assume a ΛCDM cosmology with
Ω _m_ = 0 _._ 272, Ω _b_ = 0 _._ 045, Ω Λ = 0 _._ 728, and _H_ 0 = 70 _._ 4
km s _[−]_ [1] Mpc _[−]_ [1] (Komatsu et al. 2011). The solar luminosity, _L_ _⊙_, is 3 _._ 839 _×_ 10 [33] erg s _[−]_ [1] . Hereafter, we denote
CO( _J_ = 6 _→_ 5), CO( _J_ = 7 _→_ 6), and [Ci] [3] _P_ 2 _→_ [3] _P_ 1
as CO(6-5), CO(7-6), and [Ci](2-1), respectively.


2. OUR TARGET: “BIG THREE DRAGONS”


Table 1 summarizes previous observations of the target. The galaxy was discovered by Bowler et al. (2014)
based on wide-field imaging data of the UltraVISTA survey (e.g. McCracken et al. 2012). The galaxy has a UV
absolute magnitude of _M_ UV _≈−_ 22 _._ 4, which is _∼_ 3 _−_ 4
times brighter than the characteristic UV magnitude at
_z_ = 7, _M_ UV _[∗]_ _[≈−]_ [21] _[.]_ [0] [(e.g.] [Bouwens] [et] [al.] [2021][).] [Subse-]



quently, a high-angular-resolution image taken with the
_Hubble_ _Space_ _Telescope_ ( _HST_ ) revealed that B14-65666
comprises two spatially distinct clumps in the rest-frame
UV, indicating that the target is experiencing a merger
event (Bowler et al. 2017).
The spectroscopic redshift of B14-65666 was obtained
with the Faint Object Camera and Spectrograph (FOCAS) on Subaru at _z_ = 7 _._ 17 with Ly _α_ (Furusawa et al.
2016). We performed ALMA spectroscopy of [Oiii] 88
_µ_ m and [Cii] 158 _µ_ m and determined its spectroscopic
redshift at 7 _._ 1520 _±_ 0 _._ 0003 (Hashimoto et al. 2019). Notably, Hashimoto et al. (2019) supported the merger interpretation by showing that [Oiii] and [Cii] can be spatially decomposed into two components associated with
the two UV clumps that are kinematically separated by
_≈_ 150 km s _[−]_ [1] . Furthermore, our team (Hashimoto et al.
2019; Sugahara et al. 2021) and Bowler et al. (2018,
2022) used ALMA to detect the dust continuum emission at _λ_ rest _≈_ 90, 120, and 160 _µ_ m with ALMA Band
8, 7, and 6, respectively.
With this large set of multiwavelength line and continuum measurements, B14-65666 has a well-sampled
dust spectral energy distribution (SED). With modified
blackbody radiation models for the dust continuum radiation, Sugahara et al. (2021) constrained the totalinfrared luminosity ( _L_ TIR ; integrated at 8 _−_ 1000 _µ_ m)
to be 4.0 and 12.6 _×_ 10 [11] _L_ _⊙_ with a parameter set of ( _T_ d,
_β_ ) = (40 K, 2.0) and (80 K, 1.0), respectively, where _T_ d
and _β_ are the dust temperature and emissivity index,
respectively. In the calculation of _L_ TIR, the effect of the
CMB is corrected following da Cunha et al. (2013).


3. ALMA OBSERVATIONS AND DATA

REDUCTION


We performed ALMA Band 3 observations during Sep
17 _−_ 22, 2019, as a Cycle 6 program (ID: 2018.1.01673.S,
PI: T. Hashimoto). We used 41 _−_ 45 antennas with baseline lengths of 15 _−_ 2954 m, resulting in a maximum recoverable scale of _∼_ 6 _[′′]_ . Four spectral windows were set
at central frequencies of 85.00, 86.88, 97.15, and 98.95
GHz, referred to as SPW1, SPW2, SPW3, and SPW4,
respectively. The CO(6-5) line was observed in SPW1,
and the CO(7-6) and [Ci](2-1) lines were observed in
SPW3. Continuum emission was observed in SPW2

and SPW4. The total on-source exposure time was 3.75
hrs. The quasar J1008+0029 was used for complex gain
calibration. Two quasars, J0854+2006 and J1037-2934,
were used for bandpass calibration. The flux was scaled
using J0854+2006 and J1037-2934, yielding an absolute
accuracy below 5% in ALMA Band 3.
The data were reduced and calibrated with the Common Astronomy Software Application (CASA; Mc

4 Hashimoto et al.



**Table** **2.** ALMA Band 3 Data


Data Sensitivity Beam FWHM BPA


( _µ_ Jy beam _[−]_ [1] ) ( _[′′]_ ) ( _[◦]_ )


**without** _uv_ **-taper**

Continuum 4.6 0.46 _×_ 0.41 61

CO(6-5) 96 0.52 _×_ 0.43 66
CO(7-6) and [Ci](2-1) 78 0.43 _×_ 0.37 66

_uv_ **-tapered**

Continuum 5.3 0.82 _×_ 0.72 82

CO(6-5) 107 0.78 _×_ 0.68 78
CO(7-6) and [Ci](2-1) 93 0.78 _×_ 0.68 78


Note—In _uv_ -tapered data, we adopt taper values of 0 _[′′]_ _._ 45, 0 _[′′]_ _._ 40,
and 0 _[′′]_ _._ 45 for the continuum map, CO(6-5) cube, and CO(7-6)
cube, respectively. The cube sensitivity is per 50 km s _[−]_ [1] .


Mullin et al. 2007) pipeline version 5.6.1-8. By using
the `tclean` task, we produced maps and cubes with a
natural weighting to optimize the point-source sensitivity. Table 2 summarizes the resulting resolution and
sensitivity of the data.
Continuum maps were created using all channels that
were expected to be line-free. The synthesized beam has
a size of 0 _[′′]_ _._ 46 _×_ 0 _[′′]_ _._ 41 in the full-width at half-maximum
(FWHM) and a positional angle (BPA) of 61 _[◦]_ with a
rms value of 4.6 _µ_ Jy beam _[−]_ [1] . The beam size is smaller
than the beam-deconvolved size of the target for the
dust continuum and [Cii] emitting region ( _∼_ 0 _[′′]_ _._ 8 _×_ 0 _[′′]_ _._ 4
in FWHM, see Hashimoto et al. 2019). Therefore, we
also created dust continuum maps using a Gaussian taper with a width ranging from 0 _[′′]_ _._ 0 to 1 _[′′]_ _._ 0. We adopted
a taper value of 0 _[′′]_ _._ 45 because the resultant beam size
(0 _[′′]_ _._ 82 _×_ 0 _[′′]_ _._ 72) fully covers the dust continuum emitting
region.
The data probe the dust continuum emission at
_λ_ rest _≈_ 400 _µ_ m. The left panel of Fig. 1 shows the nondetection, and by using the _uv_ -tapered image, we place
a 3 _σ_ upper limit of 15.9 _µ_ Jy on the continuum flux density. The current data is not deep enough to obtain a
meaningful constraint on the dust emissivity index.
As the dust continuum was undetected in ALMA

Band 3, we created line cubes without performing continuum subtraction. The cubes were rebinned to a velocity resolution of 50 km s _[−]_ [1] . For SPW1 (SPW3) targeting CO(6-5) [CO(7-6) and [Ci](2-1)], we also created
a _uv_ -tapered data cube by using a Gaussian taper with a
width of 0 _[′′]_ _._ 40 (0 _[′′]_ _._ 45). This cube has a synthesized beam
size of 0 _[′′]_ _._ 78 _×_ 0 _[′′]_ _._ 68 (0 _[′′]_ _._ 78 _×_ 0 _[′′]_ _._ 68) and a typical sensi


tivity of 107 (93) _µ_ Jy beam _[−]_ [1] . Hereafter, we use the
_uv_ -tapered maps and cubes unless otherwise specified.
We have searched for the presence of emission lines in
the cubes at the position of the target. At _z_ = 7 _._ 1520,
the CO(6-5), CO(7-6), and [Ci](2-1) emission lines are
expected to be at observed frequencies of 84.82, 98.95,
and 99.28 GHz, respectively. Figure 1 also shows the integrated intensity maps (i.e., moment 0 maps) of CO(65), CO(7-6), and [Ci](2-1). In these maps, we integrate the velocity range from _−_ 200 to +200 km s _[−]_ [1] with
the CASA task `immoments`, which is comparable to the
FWHM of [Oiii] and [Cii] (Hashimoto et al. 2019) [3] . Figure 2 shows the spectra obtained in a 1 _[′′]_ _._ 5-diameter aperture centered on the target, where the large aperture
size is adopted to capture possible spatially extended
CO emission (Cicone et al. 2021). We conclude that the
CO(6-5), CO(7-6), and [Ci](2-1) lines are undetected.


4. DERIVED PROPERTIES


4.1. _CO_ _and_ _[C_ i _]_ _line_ _fluxes_


From the integrated intensity maps, we obtain the
3 _σ_ upper limits on the velocity-integrated flux, _S_ line ∆ _v_,
as 0.0581, 0.0546, and 0.0542 Jy km s _[−]_ [1] for CO(6-5),
CO(7-6), and [Ci](2-1), respectively. Here we assumed
that the size of the CO emitting region should not exceed that of the [Cii] emission, which is a better tracer
of more extended and multi-phase gas. To obtain the intrinsic line fluxes, we correct for the impact of the CMB.
Following Eq. (32) of da Cunha et al. (2013), the fraction of the intrinsic line flux observed against the CMB
is written as




[against] [CMB]]
where _S_ _[J]_ [u] [[intrinsic]] and _S_ _[J]_ [u] [[obs] represent the
_ν/_ (1+z) _ν/_ (1+z)
intrinsic and observed flux density of the transition of
_J_ u, respectively. _T_ CMB ( _z_ ) = (1+ _z_ ) _×_ 2 _._ 73 K is the CMB
temperature at _z_, and _T_ exc is the excitation temperature
in units of K. _B_ _ν_ (T) is the Planck function. _f_ CMB can
be estimated under the assumptions of the local thermal
equilibrium (LTE) of molecular clouds and the thermal
equilibrium of dust and gas (Goldsmith 2001). In this
case, we can assume _T_ exc = _T_ kin = _T_ dust, where _T_ kin is
the gas kinetic temperature. We estimate _f_ CMB to be
_∼_ 0 _._ 6 _−_ 0 _._ 9 using the dust temperature, _T_ dust _∼_ 40 _−_ 80
K, in the target (Sugahara et al. 2021). In the non-LTE
case, _f_ CMB depends on a variety of parameters such as


3 Several studies show that CO(6-5) and [Cii] have similar FWHMs
(e.g. Wang et al. 2013, 2016; Strandet et al. 2017; Venemans et al.
2017b; Zavala et al. 2018).




[against] [CMB]]
_S_ _[J]_ [u] [[obs]
_f_ CMB = _ν/_ (1+z)



_,_ (1)
_B_ _ν_ [ _T_ exc ]



1+z)

= 1 _−_ _[B]_ _[ν]_ [[] _[T]_ [CMB] [(] _[z]_ [)]]
_S_ _[J]_ [u] [[intrinsic]] _B_ _ν_ [ _T_ exc ]
_ν/_ (1+z)

Molecular Gas Properties of “Big Three Dragons” 5



dust at 400 m



CO(6-5) CO(7-6) [CI](2-1)



55.0


54.0


53.0


52.0


+1:54:51.0


40.8 40.7 10:01:40.6


RA (ICRS)


**Figure** **1.** From left to right, 5 _[′′]_ _._ 0 _×_ 5 _[′′]_ _._ 0 cutout images of dust continuum map and integrated intensity maps of CO(6-5),
CO(7-6), and [Ci](2-1). In each panel, red contours illustrate the morphology in the _HST_ /WFC3 F140W band that probes the
rest-frame UV continuum emission. Black contours are drawn at ( _±_ 2, _±_ 3) _×σ_, where the _σ_ values are _≈_ 5.3 _µ_ Jy for the dust
continuum map, and 14.9, 14.0, and 13.9 mJy beam _[−]_ [1] km s _[−]_ [1] for the CO(6-5), CO(7-6), and [Ci](2-1) maps, respectively. The
black dashed circle at the center shows the 1 _[′′]_ _._ 5-diameter aperture used to extract the spectra in Fig. 2. No significant emission
has been detected.



1.0


0.5


0.0


1.0


0.5


0.0


0.5

1.0


0.5


0.0



Redshift


7.13 7.15 7.17



**Table** **3.** Summary of Measurements


Parameters CO(6-5) CO(7-6) [Ci](2-1)


(1) (2) (3) (4)



_S_ line ∆ _v_ _<_ 0.0581 _<_ 0.0546 _<_ 0.0542
_S_ line ∆ _v_ (corr.) _<_ [0] _[.]_ [0581] _<_ [0] _[.]_ [0546] _<_ [0] _[.]_ [0542]




[0] _[.]_ [0581] _<_ [0] _[.]_ [0546]

_f_ CMB _f_ CMB




[0] _[.]_ [0546] _<_ [0] _[.]_ [0542]

_f_ CMB _f_ CMB



0.5
1000 500 0 500 1000


Velocity [km/s]


**Figure** **2.** Top, middle, and bottom panel shows the spectrum of CO(6-5), CO(7-6), and [Ci], respectively (unit:
mJy), as extracted from the 1 _[′′]_ _._ 5-diameter aperture indicated
by the black dashed circle in Fig. 1. The black dotted curve
shows the noise spectrum. The vertical dashed line shows
the velocity range from _−_ 200 to +200 km s _[−]_ [1] that is used
to create the integrated intensity maps in Fig. 1, where the
velocity zero-point is defined at _z_ = 7 _._ 152 (Hashimoto et al.
2019). The velocity width is set to 50 km s _[−]_ [1] .


_T_ kin ; number density of H 2 molecules, _n_ H 2 ; and number
density of CO molecules (da Cunha et al. 2013). Because
the number of CO collisions with H 2 becomes small at
low _n_ H 2, the mid- to high- _J_ CO transitions with higher
critical densities depart from the LTE case. This leads
to _T_ CMB _∼_ _T_ exc _<_ _T_ kin, and it could lead to _f_ CMB as
small as 0.1 in the case of _T_ exc = 23 K (see Fig. 8



Note— The limits correspond to 3 _σ_ . _S_ line ∆ _v_ is the line flux
in units of Jy km s _[−]_ [1] . _L_ line and _L_ _[′]_ line [are] [the] [line] [luminosities]
in units of 10 [7] _L_ _⊙_ and 10 [9] K km s _[−]_ [1] pc [2], respectively. The
CMB-corrected values are shown with “(corr.)”, where _f_ CMB
ranges from 0.1 to 0.9 (see the main text).


in Combes et al. 1999). In summary, _f_ CMB is highly
uncertain, ranging from _∼_ 0 _._ 1 _−_ 0 _._ 9 at _T_ exc = 23 _−_ 80 K.


4.2. _Upper_ _limits_ _on_ _CO_ _and_ _[C_ i _]_ _line_ _luminosities_


We obtain the 3 _σ_ upper limits on two types of line luminosities (Solomon et al. 1992; Carilli & Walter 2013),
which are summarized in Table 3. The first one, _L_ line in
units of _L_ _⊙_, is written as


_L_ line = 1 _._ 04 _×_ 10 _[−]_ [3] _× S_ line ∆ _vD_ L [2] _[ν]_ [obs] _[,]_ (2)



_f_ CMB _f_ CMB _f_ CMB


_L_ line _<_ 2.70 _<_ 2.96 _<_ 2.95
_L_ line (corr.) _<_ _f_ 2 CMB _._ 70 _<_ _f_ 2 CMB _._ 96 _<_ _f_ 2 CMB _._ 95
_L_ _[′]_ line _<_ 2.55 _<_ 1.77 _<_ 1.74
_L_ _[′]_ line [(corr.)] _<_ _f_ 2 CMB _._ 55 _<_ _f_ 1 CMB _._ 77 _<_ _f_ 1 CMB _._ 74
_L_ [OIII] / _L_ line _>_ 125 _>_ 115 _>_ 115
_L_ [OIII] / _L_ line (corr.) _>_ 125 _f_ CMB _>_ 115 _f_ CMB _>_ 115 _f_ CMB
_L_ [CII] / _L_ line _>_ 41 _>_ 37 _>_ 37
_L_ [CII] / _L_ line (corr.) _>_ 41 _f_ CMB _>_ 37 _f_ CMB _>_ 37 _f_ CMB

6 Hashimoto et al.



where _S_ line ∆ _v_ is the velocity-integrated flux in units of
Jy km s _[−]_ [1], _D_ L is the luminosity distance in Mpc, and
_ν_ obs is the observed frequency in GHz. The second one,
_L_ _′_ line [,] [corresponds] [to] [the] [area-integrated] [brightness] [in]
units of K km s _[−]_ [1] pc [2], and it is written as


_L_ _′_ line [= 3] _[.]_ [25] _[ ×]_ [ 10] [7] _[ ×][ S]_ [line] [∆] _[v]_ _D_ L [2] _._ (3)
(1 + _z_ ) [3] _ν_ obs [2]


With _S_ line ∆ _v_ (Table 3), the 3 _σ_ upper limits on _L_ line
( _L_ _′_ line [) are] _f_ 2 CMB _._ 70 [,] _f_ 2 CMB _._ 96 [, and] _f_ 2 CMB _._ 95 _[×]_ [10] [7] _[L]_ _[⊙]_ [(] _f_ [2] CMB _[.]_ [55] [,] _f_ 1 CMB _._ 77 [,]

and _f_ 1 CMB _._ 74 _[×]_ [10] [9] [K] [km] [s] _[−]_ [1] [pc] [2] [)] [for] [CO(6-5),] [CO(7-6),]
and [Ci](2-1), respectively.


4.3. _Molecular_ _gas_ _mass_ _estimates_


We estimate the molecular gas mass of B14-65666. In
light of the rich dataset, we adopt five techniques as
summarized in Table 4.


4.3.1. _Estimates_ _with_ _CO(6-5)_ _and_ _CO(7-6)_


The molecular gas mass is estimated with CO lines as

_MM_ mol [CO] _⊙_ = _α_ CO _r_ _J_ _[−]_ 1 [1] _[L]_ _′_ CO _J→J−_ 1 _[,]_ (4)


where _α_ CO is the CO-to-H 2 conversion factor in units of
_M_ _⊙_ (K km s _[−]_ [1] ) _[−]_ [1], and _r_ _J_ 1 is the excitation correction
factor defined as



gas-phase metallicity of B14-65666 is estimated to be
0 _._ 4 [+0] _−_ 0 _[.]_ _._ [4] 2 _[Z]_ _[⊙]_ [based] [on] [SED] [fits] [by] [taking] [into] [account]
the multiwavelength data ranging from rest-frame UV
to FIR (Hashimoto et al. 2019). With a broad range of
0 _._ 2 _−_ 0 _._ 8 _Z_ _⊙_ (i.e., 12+log(O/H) = 8 _._ 0 _−_ 8 _._ 6), _α_ CO _≈_ 5 _−_ 25
_M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] .
With _α_ CO = 25 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] and the 3 _σ_
upper limit on _L_ _′_ CO _J_ =1 _→_ 0 [, we estimate the molecular gas]
mass to be _M_ mol [CO] _[<]_ [3] _[.]_ _f_ [0] CMB _[×]_ [10] [11] _M_ _⊙_ (3 _σ_ ). With _f_ CMB _∼_

0 _._ 1 _−_ 0 _._ 9, the 3 _σ_ upper limit becomes _∼_ (4 _−_ 30) _×_ 10 [11]

_M_ _⊙_ . Similarly, we obtain the 3 _σ_ upper limit of (3 _−_
25) _×_ 10 [11] _M_ _⊙_ from CO(6-5).


4.3.2. _Estimate_ _with_ _[C_ i _](2-1)_


The neutral carbon mass, _M_ CI, can be obtained from
the [Ci] luminosity and _T_ exc . We estimate _M_ CI following
Weiß et al. (2003) as



_M_ CI



_′_

[1] [CI](2 _−_ 1)

5 _[e]_ [62] _[.]_ [5] _[/T]_ [exc] _[ L]_



_,_ (6)
_f_ CMB



_M_ CI

= 4 _._ 566 _×_ 10 _[−]_ [4] _Q_ ( _T_ exc ) [1]
_M_ _⊙_ 5



_′_

CO _J→J−_ 1
_r_ _J_ 1 = _[L]_ _′_ = _[I]_ [CO] _[J][→][J][−]_ [1]
_L_ CO1 _→_ 0 _I_ CO1 _→_ 0



1
_J_ [2] _[.]_ (5)



We use Eq. (19) of Narayanan & Krumholz (2014),
who have shown that the CO excitation ladders can

be parametrized with Σ SFR based on simulations of
disc galaxies combined with CO line radiative transfer calculations. With Σ SFR = 20 _._ 6 [+11] _−_ 7 _._ 6 _[.]_ [4] _M_ _⊙_ yr _[−]_ [1]

kpc _[−]_ [2] obtained for the target [4], _r_ 61 = 0 _._ 28 [+0] _−_ 0 _[.]_ _._ [04] 02 [and]
_r_ 71 = 0 _._ 17 _−_ [+0] 0 _[.]_ _._ [02] 02 [.] With the upper limit on the CO(76) luminosity (Table 3), we obtain _L_ _′_ CO _J_ =1 _→_ 0 _[<]_ [1] _[.]_ _f_ [2] CMB _[×]_ [10] [10]

K km s _[−]_ [1] pc [2] (3 _σ_ ).
Previous observational studies (e.g. Leroy et al. 2011;
Shi et al. 2016) as well as theoretical ones (e.g. Wolfire
et al. 2010; Narayanan et al. 2012) show that _α_ CO increases at lower gas-phase metallicity as a result of increased CO photodissociation. In this study, we adopt
the conversion factor of Tacconi et al. (2018) (their Eq.
(2)) that is a function of the gas-phase metallicity. The


4 The target has SFR = 200 [+82] _−_ 32 _[M]_ _[⊙]_ [yr] _[−]_ [1] [and] [the] [[O][iii][]] [beam-]
deconvolved size of (3 _._ 8 _±_ 0 _._ 5) _×_ (2 _._ 2 _±_ 0 _._ 6) kpc [2] in FWHM
(Hashimoto et al. 2019). The Σ SFR value is calculated as 2SFR _πr_ [2] [,]
where _r_ is the half-light radius.



where _Q_ ( _T_ exc ) = 1 + 3 _e_ _[−][T]_ [1] _[/T]_ [exc] + 5 _e_ _[−][T]_ [2] _[/T]_ [exc] is the [Ci]
partition function, and _T_ 1 = 23.6 K and _T_ 2 = 62.5 K
is the temperature of each transition from the ground
state. By using _f_ CMB _∼_ 0 _._ 1 _−_ 0 _._ 9 at _T_ exc _∼_ 23 _−_ 80
K and the CMB-corrected luminosity of [Ci](2-1), we
obtain _M_ CI _<_ (2 _._ 2 _−_ 59) _×_ 10 [6] _M_ _⊙_ (3 _σ_ ). Assuming
the abundance ratio of _X_ [Ci]/ _X_ [H 2 ] _∼_ 1 _._ 6 _×_ 10 _[−]_ [5] as
obtained in _z_ _∼_ 1 main-sequence galaxies (Valentino
et al. 2018), the [Ci](2-1)-based molecular gas mass is
_M_ mol [[CI]] _[<]_ [ (3] _[.]_ [0] _[ −]_ [82)] _[ ×]_ [ 10] [10] _[M]_ _[⊙]_ [(3] _[σ]_ [),] [where] [the] [contribu-]
tion of helium is included. Heintz & Watson (2020) have
revealed that the mass conversion factor of the [Ci](1_′_
0) transition, _α_ [CI](1 _−_ 0) _≡_ _M_ mol _/L_ [CI](1 _−_ 0) [,] [depends] [on]
the metallicity based on observations of [Ci]( _J_ = 1) [5] absorption lines in the rest-frame UV toward a sample of
gamma-ray burst (GRB) and quasar absorption systems
at _z_ _∼_ 1 _._ 9 _−_ 3 _._ 4. _α_ [CI](1 _−_ 0) becomes approximately 10
times higher at 0 _._ 2 _Z_ _⊙_ than at _Z_ _⊙_ . If we assume that
the mass conversion factor of [Ci](2-1) similarly changes
with metallicity, our upper limits can be higher by a
factor of 10, _M_ mol [[CI]] [≲] [(3] _[.]_ [0] _[ −]_ [82)] _[ ×]_ [ 10] [11] _[M]_ _[⊙]_ [(3] _[σ]_ [)] [(Table]
4).


4.3.3. _Estimate_ _with_ _[C_ ii _]_ _158_ _µm_


The [Cii] 158 _µ_ m line can also be used to probe the
molecular gas mass (Zanella et al. 2018; Madden et al.
2020; Dessauges-Zavadsky et al. 2020 and references


5 _J_ refers to the total angular momentum quantum number for this
transition.

Molecular Gas Properties of “Big Three Dragons” 7



therein). We use the conversion factor _α_ [CII] of Madden et al. (2020) (see their Eq. (5)) that is appropriate
for metal-poor galaxies.
We apply two corrections to the [Cii] luminosity.
First, we remove the [Cii] contribution originating from
the Hii region, although it becomes negligible in galaxies
with, for example, low- _Z_ (e.g. Croxall et al. 2017). From
the metallicity of the target and Fig. 9 of Cormier et al.
(2019), we estimate the contribution from the Hii region
to be _≈_ 30%. Second, we correct for the CMB impact
to [Cii]. Based on semi-analytical model of galaxy formation combined with photoionization modelling, Lagache et al. (2018) have shown that the [Cii] luminosity
can be reduced by 0.3 dex ( _f_ CMB = 0 _._ 5) at _z_ = 7 (see
their Figure 4) in the case of a photodissociated region
(PDR) with the hydrogen nuclei density of log( _n_ (H))
= 2 _._ 4 irradiated by the incident FUV radiation field
of 3 _._ 2 _×_ 10 [3] _G_ 0, where _G_ 0 is the Habing Field in unit,
1 _._ 6 _×_ 10 _[−]_ [3] erg cm _[−]_ [2] s _[−]_ [1] (Habing 1968). These PDR
parameters are similar to those obtained in _z_ _∼_ 3 _−_ 4
DSFGs (e.g. Wardlow et al. 2017), and are not improbable for B14-65666. Similarly, based on the cosmological hydrodynamic simulations combined with radiative transfer calculations, Vallini et al. (2015) have also
modeled the [Cii] emission at _z_ _∼_ 7 taking the CMB
effect into account. These authors find that the [Cii]
emission from the PDR is not severely impacted by the
CMB effect, only up to 20% (see similar results in Kohandel et al. 2019). Given the uncertainty, we assume
_f_ CMB = 0 _._ 5 _−_ 1 _._ 0 in B14-65666. The intrinsic [Cii] luminosity from the molecular gas is _≈_ (7 _._ 7 _−_ 17) _×_ 10 [8] _L_ _⊙_ .
We thus obtain _M_ mol [[CII]] _[≈]_ [(5] _[.]_ [4] _[−]_ [23)] _[×]_ [10] [10] _[M]_ _[⊙]_ [, where we]
include the helium contribution and take into account a

standard deviation of 0.14 dex in the relation.


4.3.4. _Estimate_ _with_ _dust_ _continuum_


We estimate the gas mass based on _M_ d and the
metallicity-dependent dust-to-gas ratio (DGR; R´emyRuyer et al. 2014; Li et al. 2019). With the prescription
of Li et al. (2019) derived from cosmological hydrodynamical simulations implementing the process of dust
production, growth, and destruction (see their Eq. (9)),
we obtain DGR _≈_ (1 _._ 8 _−_ 53) _×_ 10 _[−]_ [4] at the metallicity
of the target. Combined with the dust mass of the target, log( _M_ dust _/M_ _∗_ ) _≈_ 6 _._ 4 _−_ 7 _._ 5 (Sugahara et al. 2021),
we estimate the (molecular + atomic) gas mass to be
_M_ gas [dust] _≈_ (0 _._ 05 _−_ 17) _×_ 10 [10] _M_ _⊙_ . If we assume that gas
is predominantly in the molecular phase (Riechers et al.
2013), this can be regarded as the molecular gas mass.


4.3.5. _Upper_ _limit_ _with_ _dynamical_ _mass_


We calculate an upper limit on _M_ mol from the dynamical mass, _M_ dyn, subtracted by the stellar mass



**Table** **4.** Molecular Gas Mass


Method _M_ mol


10 [10] _M_ _⊙_


CO(6-5) _<_ (40 _−_ 300)
CO(7-6) _<_ (30 _−_ 250)

[Ci](2-1) _<_ (30 _−_ 820)

[Cii] 158 _µ_ m 5 _._ 4 _−_ 23

dust 0 _._ 05 _−_ 17

dynamical mass _<_ 11


Note— The estimates based on
mid- _J_ CO and [Ci](2-1) are 3 _σ_ upper limits, where the values in the
parenthesis reflect the uncertainty
in the CMB correction. The es
timate based on the dynamical
mass ( _M_ dyn ) provides the upper
limit.


contribution. Hashimoto et al. (2019) obtained _M_ dyn
of two individual clumps of B14-65666 based on the
line width and beam-deconvolved size of [Cii] 158 _µ_ m
under the assumption of the virial theorem. The dynamical mass of the whole system is estimated to be
_M_ dyn = (8 _._ 8 _±_ 1 _._ 9) _×_ 10 [10] _M_ _⊙_, where the error only
considers the measurement uncertainties. With a stellar
mass obtained from SED fitting ( _M_ _∗_ = 7 _._ 7 [+1] _−_ 0 _[.]_ _._ [0] 8 _[×]_ [10] [8]

_M_ _⊙_ ; Hashimoto et al. 2019), we obtain a conservative
upper limit on _M_ mol to be _∼_ 11 _×_ 10 [10] _M_ _⊙_ .
To summarize, by combining the _M_ mol estimates from
the [Cii] luminosity, dust mass, and dynamical mass, we
obtain _M_ mol = (0 _._ 05 _−_ 11) _×_ 10 [10] _M_ _⊙_, which is consistent with the upper limits on _M_ mol inferred from the
nondetections of mid- _J_ CO and [Ci](2-1). Although the
Band 3 observations were conducted to constrain _M_ mol
in B14-65666, we note that the tightest constraint on
_M_ mol comes from the previous observations of dust and

[Cii] 158 _µ_ m, not from mid- _J_ CO or [Ci](2-1), due to
the insufficient sensitivity of the Band 3 observations.
Future deeper Band 3 observations are crucial to better
constrain _M_ mol with mid- _J_ CO or [Ci](2-1).


5. RESULTS


5.1. _Luminosity_ _comparisons_


5.1.1. _mid-J_ _CO_ _and_ _[C_ i _]_ _vs._ _far-infrared_ _luminosity_


In the local universe, a compiled sample of SFGs,
AGNs, and U/LIRGs observed by _Herschel_ /SPIRE
shows a positive correlation between the mid- _J_ CO and
the [Ci](2-1) line luminosities and FIR luminosity, _L_ FIR
(e.g. Kamenetzky et al. 2016). Figure 3 shows a compar

8 Hashimoto et al.


CO(6-5) CO(7-6) [CI](2-1)



14.0


13.5


13.0


12.5


12.0


11.5


11.0


10.5


10.0







9.5
7 8 9 10 11 12



7 8 9 10 11 12 7 8 9 10 11 12



log L ′ [K km s 1 pc 2 ]


**Figure** **3.** Far-infrared luminosity defined in the range of 42 _._ 5 _−_ 122 _._ 5 _µ_ m plotted against the line luminosity. The red circle,
cyan squares, blue squares, and orange circles show the data points of B14-65666, _z_ _>_ 5 DSFGs, quasar host galaxies, and
normal SFGs (see the text for the details of the literature sample), respectively, where the upper limits correspond to 3 _σ_ . For
the detections at _z_ _>_ 5, the typical significance levels are 7, 6, and 4 for CO(6-5), CO(7-6), and [Ci](2-1), corresponding to the
line luminosity uncertainties of 0.1, 0.1, and 0.2 dex, respectively. The line luminosities are before the CMB correction. The
black arrow in the left panel shows the impact of CMB at _T_ exc = 40 K; it shifts the data points toward higher line luminosities
by _∼_ 0 _._ 2 dex at _z_ = 7. Small open circles show a compilation of local objects, including SFGs, AGNs, and U/LIRGs observed
with _Herschel_ /SPIRE (Kamenetzky et al. 2016), where objects with _>_ 3 _σ_ detections are plotted.



ison of B14-65666 with the local objects (Kamenetzky
et al. 2016). The FIR luminosity of B14-65666 is calculated by integrating the modified blackbody radiation
at 42 _._ 5 _−_ 122 _._ 5 _µ_ m, where the CMB effect is corrected
following da Cunha et al. (2013) (Table 1). _z_ _∼_ 5 _−_ 7 DSFGs (Jarugula et al. 2021; Riechers et al. 2013; Zavala
et al. 2018; Casey et al. 2019; Vieira et al. 2022; Apostolovski et al. 2019; Riechers et al. 2017, 2020; Combes
et al. 2012), quasar host galaxies (Novak et al. 2019;
Venemans et al. 2017a,b; Decarli et al. 2022; Yang et al.
2019; Riechers et al. 2009; Wang et al. 2019), as well
as _z_ _∼_ 6 normal SFGs (D’Odorico et al. 2018; Vieira
et al. 2022) are also plotted, where the lensing magnification is corrected when necessary. Note that the number of data points differs in each transition. Although
we show the line luminosities not corrected for the im
pact of the CMB, it shifts the line luminosities toward
higher values by 0.2 dex at _T_ exc = 40 K at _z_ = 7, as
indicated by a black arrow in the left panel. Figure 3
shows that high- _z_ sources also seem to follow the correlations. This might imply that the CMB effect may
not be severe even at high redshift, although this could
be due to a bias towards bright DSFGs and quasar host
galaxies with higher _T_ exc .
The data points of B14-65666 for the first time place
constraints on the line luminosities at log( _L_ FIR / _L_ _⊙_ ) _<_
12 _._ 0 at _z_ _>_ 6. Nevertheless, the upper limits are loose at
a given _L_ FIR, especially when the CMB impact is taken
into account. This indicates that the nondetection of



the lines can be explained by the insufficient sensitivity
of the observations.


5.1.2. _mid-J_ _CO_ _and_ _[C_ i _]_ _vs._ _[C_ ii _]_ _158_ _µm_ _luminosity_


Figure 4 shows plots of _L_ [CII] / _L_ CO(6 _−_ 5),
_L_ [CII] / _L_ CO(7 _−_ 6), and _L_ [CII] / _L_ [CI](2 _−_ 1) against _L_ FIR . It
also shows plots of DSFGs, quasar host galaxies, and
normal SFGs at _z_ _>_ 5, with the luminosity measurements as in Fig. 3. The luminosities are before the
CMB correction.
B14-65666 has line luminosity ratios ≳ 40 (3 _σ_ ). If we
focus on _L_ [CII] / _L_ CO(7 _−_ 6), the lower limit is three times
higher than the predicted value of _∼_ 13 for a simulated
galaxy at _z_ = 6 in Vallini et al. (2019), namely, “Althæa,” for which _M_ _∗_ _≈_ 10 [10] _M_ _⊙_, SFR _≈_ 100 _M_ _⊙_ yr _[−]_ [1],
and _Z_ _∼_ 0 _._ 5 _Z_ _⊙_ . B14-65666 has similar SFR and metallicity values; however, its stellar mass is approximately
one order of magnitude lower than that of Althæa. Although only five (three) objects have _L_ [CII] / _L_ CO(6 _−_ 5)
( _L_ [CII] / _L_ CO(7 _−_ 6) ) measurements higher than B14-65666,
its interpretation is complicated owing to the large uncertainty in _f_ CMB . If B14-65666 has low _n_ H 2 and/or gas
temperature compared with those of DSFGs or quasar
host galaxies at similar redshifts, _f_ CMB in B14-65666 becomes small, making the lower limits of B14-65666 more
consistent with the typical values in high- _z_ DSFGs and
quasar host galaxies. Because a large fraction of the
data points in Figure 4 comes from quasar host galaxies,
the difficulty in measuring their stellar mass, size, and

Molecular Gas Properties of “Big Three Dragons” 9



2.2


2.0


1.8


1.6


1.4


1.2


1.0



|CO(6-5)|CO(7-6)|[CI](2-1)|
|---|---|---|
|z>5 DSFGs<br>z>5 QSOs<br>z~6 normal SFGs<br> <br>CMB (Texc = 40 K)|||
|z>5 DSFGs<br>z>5 QSOs<br>z~6 normal SFGs<br>|z>5 DSFGs<br>z>5 QSOs<br>z~6 normal SFGs<br>|z>5 DSFGs<br>z>5 QSOs<br>z~6 normal SFGs<br>|


11.5 12.0 12.5 13.0 13.5



11.5 12.0 12.5 13.0 13.5 11.5 12.0 12.5 13.0 13.5



log L FIR [L ]


**Figure** **4.** From left to right, _L_ [CII] / _L_ CO(6 _−_ 5), _L_ [CII] / _L_ CO(7 _−_ 6), and _L_ [CII] / _L_ [CI](2 _−_ 1) are plotted against _L_ FIR . The red circle,
cyan squares, blue squares, and orange circles show the data points of B14-65666, _z_ _>_ 5 DSFGs, quasar host galaxies, and
normal SFGs, respectively, where the upper limits correspond to 3 _σ_ . The line luminosities are before the CMB correction. The
black arrow in the left panel shows the impact of the CMB on the lines at _T_ exc = 40 K; it shifts the data points toward lower
line luminosity ratios by _∼−_ 0 _._ 2 dex at _z_ = 7.



SFR surface densities also prevents us to further examine the physical origins of the higher luminosity ratios in
B14-65666 than other EoR sources. The situation will

be improved by _the_ _James_ _Webb_ _Space_ _Telescope_ that
provides these measurements in quasar host galaxies.
In summary, the current data is insufficient to examine
the difference in the CMB-corrected _L_ [CII] _/L_ line in B1465666 and other high- _z_ objects. The results also imply
that care must be taken when comparing the luminosity
ratios of galaxies in the EoR.


5.2. _PDR_ _modelling_


The luminosity ratios are useful to examine properties of the interstellar medium (ISM: e.g. Kaufman et al.
2006; Pound & Wolfire 2008), although the impact of the
CMB makes the interpretation complicated, as stated in
§5.1.2. The _L_ [CII] / _L_ [CI](2 _−_ 1) luminosity ratio is sensitive
to the heating source of the ISM (Meijerink et al. 2007).
The high ratio, ≳ 40, excludes the possibility that the
lines are heated by the X-ray dominated regions, where
_L_ [CII] / _L_ [CI](2 _−_ 1) ≲ 6 is expected. We thus compare the
line ratios of B14-65666 to the model predictions of PDR
Toolbox (version wk2020) to place constraints on the
physical properties of the PDRs. The model assumes
a geometry of infinite plane slabs of hydrogen characterized by the hydrogen nuclei density, _n_ (H), and the
strength of the incident FUV radiation field, _G_, normalized to the Habing Field in units of _G_ 0 = 1 _._ 6 _×_ 10 _[−]_ [3]

erg cm _[−]_ [2] s _[−]_ [1] . In a more realistic geometry of spherical clouds, the optically thin emission would be detected
from both the front and back sides of the cloud, whereas



the optically thick emission would be detected only from
the front side (Yang et al. 2019). We therefore divide
the luminosities of optically thin emission by a factor of
two. We also assume that the [Cii] contribution from
the PDR is 70% (§4.3.3). We adopt the line ratios before the correction of the CMB and discuss its impact

later.

In Figure 5, the overlapped region of the four luminosity ratios is log( _n_ (H)/cm _[−]_ [3] ) _∼_ 1 _−_ 5 with a moderate FUV radiation field _∼_ 10 [2] _−_ 10 [3] _G_ 0 . The high
_L_ [CII] / _L_ CO(6 _−_ 5) and _L_ [CII] / _L_ CO(7 _−_ 6) ratios exclude the
possibility of log( _n_ (H)/cm _[−]_ [3] ) _>_ 5. The strength of the
incident FUV radiation field in B14-65666 is comparable to those in local (U)LIRGs and high- _z_ DSFGs that
have _∼_ 10 [2] _−_ 10 [4] _G_ 0, as indicated by the grey box in Fig.
5 (Hughes et al. 2017; Wardlow et al. 2017), but lower
than that of a _z_ _∼_ 6 DSFG, G09.83808, with a FUV
radiation field _∼_ 10 [4] _G_ 0 (cyan ellipse, Rybak et al. 2020).
The gas density in B14-65666 is barely constrained, although is lower than that obtained in some _z_ _∼_ 6 _−_ 7
quasar host galaxies (blue square: Shao et al. 2019).
The CMB effect makes the intrinsic _L_ [CII] / _L_ CO(6 _−_ 5),
_L_ [CII] / _L_ CO(7 _−_ 6), and _L_ [CII] / _L_ [CI](2 _−_ 1) ratios lower because [Cii] is less affected by the CMB compared to
CO(6-5), CO(7-6), and [Ci]. The net effect is that the
constraints on _n_ (H) and _G_ become weaker. The high
luminosity ratios _>_ 40 (3 _σ_ ) (Fig. 4) may imply that the
nondetection of the lines in B14-65666 could be partly
due to its low _n_ (H) compared to that of other high- _z_
objects; however, the CMB effect prevents us from obtaining a conclusion.

10 Hashimoto et al.



6


5


4









3


2


1


0


1 2 3 4 5 6 7
log _n_ (H) [cm _[−]_ [3] ]


**Figure** **5.** The FUV radiation field, _G_, and the hydrogen gas density, _n_ (H), in B14-65666 as estimated using PDRToolbox (Pound & Wolfire 2008). The red line
with a shaded region indicates the parameter space allowed
by _L_ [CII] / _L_ FIR and its uncertainty. The orange, blue, and
black lines with arrows show the permitted ranges of parameters given by the 3 _σ_ lower limits on _L_ [CII] / _L_ CO(6 _−_ 5),
_L_ [CII] / _L_ CO(7 _−_ 6), and _L_ [CII] / _L_ [CI](2 _−_ 1), respectively. The allowed parameter space of B14-65666 corresponds to the red
line and shaded region left of the blue and yellow lines. B1465666 has log( _n_ (H)/cm _[−]_ [3] ) _∼_ 1 _−_ 5 and _∼_ 10 [2] _−_ 10 [3] _G_ 0 . The
results of other DSFGs at _z_ = 1 _−_ 5 (Wardlow et al. 2017),
a DSFG at _z_ = 6 _._ 0 (Rybak et al. 2020), and three IR-bright
quasar host galaxies at _z_ _∼_ 6 (Shao et al. 2019) are also
shown.


5.3. _Gas_ _fractions_ _and_ _depletion_ _timescales_


Despite the large uncertainty in _M_ mol (§4.3), we examine two physical quantities related with the molecular gas. The first one is the gas depletion time,
_τ_ dep _≡_ _M_ mol _/_ SFR. With _M_ mol and SFR = 200 [+82] _−_ 38
_M_ _⊙_ yr _[−]_ [1] from SED fitting (Hashimoto et al. 2019), we
obtain _τ_ dep _≈_ 2 _._ 5 _−_ 550 Myr. The second one is the
molecular gas-to-stellar mass ratio, _µ_ gas _≡_ _M_ mol _/M_ _∗_ .
With _M_ mol = (0 _._ 05 _−_ 11) _×_ 10 [10] _M_ _⊙_ and the stellar
mass obtained from SED fitting (Hashimoto et al. 2019),
_M_ _∗_ = 7 _._ 7 _−_ [+1] 0 _[.]_ _._ [0] 8 _[×]_ [ 10] [8] _[M]_ _[⊙]_ [,] [we] [obtain] _[µ]_ [mol] _[≈]_ [0] _[.]_ [65] _[ −]_ [140.]
The left panel in Fig. 6 shows a comparison of _τ_ dep
of B14-65666 with other high- _z_ objects shown in Fig. 3
when the quantities are available. For the 12 data points
of _z_ _>_ 5 DSFGs, we adopt _τ_ gas in the literatures if available. If not, we compute them from _M_ mol and SFRs.
For the 10 quasar host galaxies in Decarli et al. (2022),
the width of the box plot corresponds to their redshift



range, whereas the height corresponds to the 84 percentile of _τ_ gas . We also individually plot the _z_ = 7 _._ 54
quasar (Novak et al. 2019) and three _z_ _∼_ 7 quasars
(Venemans et al. 2017b), where _τ_ gas values are computed based on the combinations of CO-based _M_ mol and
SFR. We also plot normal SFGs on the main-sequence
at 4 _<_ _z_ _<_ 6 (Dessauges-Zavadsky et al. 2020) and an
individual value of the _z_ _∼_ 5 _._ 7 LBG, HZ10 (Pavesi et al.
2019). From the figure, we find that B14-65666 is consistent with other high- _z_ sources and the extrapolations
of the scaling relation in Tacconi et al. (2020) (black
lines).
The right panel in Fig. 6 shows a comparison of _µ_ gas .
In _z_ _>_ 5 DSFGs, the values are taken from the literatures if available. If not, we compute them from the
stellar and gas mass estimates. We do not include _z_ _>_ 5
quasar host galaxies because their stellar masses are not
well constrained. Again, B14-65666 is consistent with
other high- _z_ sources and the extrapolations of the scaling relation in Tacconi et al. (2020).


6. DISCUSSION


We obtain _τ_ dep of 2.5 and 550 Myr in the case of
_M_ mol = 0.05 and 11 _×_ 10 [10] _M_ _⊙_, respectively. In the
case of _τ_ dep = 550 (2.5) Myr, the galaxy will consume
the molecular gas as early as _z_ _≈_ 4.5 (7), if the galaxy is
not fueled by further accretion, whose final stellar mass
is approximately 1 _×_ 10 [11] (1 _×_ 10 [9] ) _M_ _⊙_ . This implies that
B14-65666 can evolve into a passive galaxy at _z_ ≳ 4. To
further examine this hypothesis, we compare the volume
number density of galaxies like B14-65666 with that of
_z_ _∼_ 3 _−_ 4 passive galaxies. The number density of galaxies like B14-65666 ( _M_ UV = _−_ 22 _._ 4) is _∼_ 1 _×_ 10 _[−]_ [6] Mpc _[−]_ [3]

based on the bright-end of the UV luminosity function
at _z_ _∼_ 7 (Bowler et al. 2017; Harikane et al. 2022). The
observed number density of _z_ _∼_ 3 _−_ 4 passive galaxies
was recently compiled by Valentino et al. (2020); it is
_O_ (10 _[−]_ [6] ) _−O_ (10 _[−]_ [5] ) Mpc _[−]_ [3] at _M_ _∗_ _≥_ 4 _×_ 10 [10] _M_ _⊙_ . These
authors have also derived the number density by analyzing the _Illustris_ TNG cosmological simulation public release data (e.g. Springel et al. 2018). In the simulation,
the volume number density of _z_ = 3 _._ 7 passive galaxies is
estimated to be _O_ (10 _[−]_ [6] ) Mpc _[−]_ [3] at _M_ _∗_ _≥_ 4 _×_ 10 [10] _M_ _⊙_ .
A broad agreement in the number densities may support
the idea that moderate starburst galaxies at _z_ _>_ 7, such
as B14-65666 could be ancestors of _z_ _∼_ 3 _−_ 4 passive
galaxies (c.f., Valentino et al. 2020).


7. CONCLUSION


We have presented results of ALMA Band 3 observations of CO(6-5), CO(7-6), and [Ci](2-1) in B14-65666
(“Big Three Dragons”). The target was previously detected in Ly _α_, [Oiii] 88 _µ_ m, [Cii] 158 _µ_ m, and the dust

4 _._ 0 4 _._ 5 5 _._ 0 5 _._ 5 6 _._ 0 6 _._ 5 7 _._ 0 7 _._ 5


_z_



4 _._ 0 4 _._ 5 5 _._ 0 5 _._ 5 6 _._ 0 6 _._ 5 7 _._ 0 7 _._ 5


_z_



**Figure** **6.** Evolution of the gas depletion time ( _τ_ dep ) and gas fraction ( _M_ mol _/M_ _∗_ ) at _z_ = 4 _−_ 7 _._ 5. (Left) The _τ_ dep value of
B14-65666, indicated by the red circle, is compared against the values in 12 DSFGs at _z_ _>_ 5 (cyan squares), 10 quasar host
galaxies at _z_ _∼_ 5 _−_ 6 _._ 5 (blue box regions), four quasar host galaxies at _z_ _∼_ 7 (blue squares), a normal SFG at _z_ _∼_ 6 (orange
circle), and main-sequence galaxies at _z_ _∼_ 4 _._ 5 _−_ 6 _._ 0 (grey box regions). The solid and dashed lines indicate the scaling relations
derived by Tacconi et al. (2020) for the main-sequence (log(SFR/SFR MS ) = 0) and starburst galaxies (log(SFR/SFR MS ) = 1 _._ 2)
at log( _M_ _∗_ _/M_ _⊙_ ) = 10, respectively, extrapolated to _z_ _∼_ 7. (Right) Comparisons of _M_ mol _/M_ _∗_ in B14-65666 with those in high- _z_
objects indicated by the same symbols as in the left panel.



continuum in the EoR (Hashimoto et al. 2019), and it is
one of the brightest LBGs at _z_ _>_ 7 without gravitational
lensing (Table 1).


  - We do not detect CO(6-5), CO(7-6), and [Ci](2-1)
(Figs. 1 and 2). The 3 _σ_ upper limit on the line
luminosity is _≈_ (2 _._ 7 _−_ 3 _._ 0) _×_ 10 [7] _L_ _⊙_ [i.e., (1 _._ 7 _−_
2 _._ 6) _×_ 10 [9] K km s _[−]_ [1] pc [2] ], which is approximately
40 times fainter than the [Cii] 158 _µ_ m luminosity
before the CMB correction.


  - By comparing the line luminosity upper limits
with _z_ _>_ 5 sources such as DSFGs and quasar
host galaxies, we find that the nondetections are
likely due to (1) the insufficient sensitivity of the
observations (Fig. 3) or (2) possibly low hydrogen gas density in the PDR (Fig. 4), although the
uncertainty in the CMB impact makes the interpretation complicated.


  - We have estimated the molecular gas mass, _M_ mol,
of B14-65666 based on five techniques: (1) mid- _J_
CO luminosity, (2) [Ci](2-1) luminosity, (3) [Cii]
158 _µ_ m luminosity, (4) dust mass and a DGR, and
(5) dynamical mass. From three methods, namely,

[Cii], dust mass, and dynamical mass, we obtain
_M_ mol = (0 _._ 05 _−_ 11) _×_ 10 [10] _M_ _⊙_, which is consistent
with its upper limit inferred from the nondetection
of mid- _J_ CO and [Ci](2-1) (Table 4).


  - By comparing the observed luminosities to the
model predictions of the PDR, we find that B14


65666 has log( _n_ (H)/cm _[−]_ [3] ) _∼_ 1 _−_ 5 with a moderate FUV radiation field of _∼_ 10 [2] _−_ 10 [3] _G_ 0 . These
values are broadly consistent with those obtained
in local (U)LIRGs and high- _z_ DSFGs/quasar host
galaxies, although the constraints on _n_ (H) and _G_
can be weaker if the CMB effect is significant (Fig.
5).


- We estimate a molecular gas-to-stellar mass ratio
( _µ_ gas ) of 0 _._ 65 _−_ 140 and a gas depletion time ( _τ_ dep )
of 2 _._ 5 _−_ 550 Myr; these values are consistent with
those of other high- _z_ objects and the extrapolations of the scaling relations to _z_ _∼_ 7 (Fig. 6).


- If the galaxy is not fueled by further accretion, we
conjecture that B14-65666 could be an ancestor
of _z_ ≳ 4 passive galaxies; this is supported by
the broad agreement of the number volume density
of galaxies like B14-65666 and _z_ _∼_ 3 _−_ 4 passive
galaxies.

12 Hashimoto et al.


ACKNOWLEDGMENTS


We thank an anonymous referee for valuable comments that have greatly improved the paper. TH was
supported by Leading Initiative for Excellent Young
Researchers, MEXT, Japan (HJH02007) and by JSPS
KAKENHI Grant Numbers (20K22358 and 22H01258).
AKI, YS, and YF are supported by NAOJ ALMA Scientific Research Grant Numbers 2020-16B. AKI acknowledges support from JSPS KAKENHI Grant Number
23H00131. YT acknowledges support from JSPS KAKENHI Grant Number 22H04939. KK acknowledges support from the Knut and Alice Wallenberg Foundation.
We thank Yoshito Shimajiri for support in analyzing
ALMA data. We appreciate Hajime Fukushima, Shigeki
Inoue, Satoshi Kikuta, Masami Ouchi, Hidenobu Yajima, and Atsuhi Yasuda for discussion. We would
like to thank Editage (www.editage.com) for English
language editing. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01673.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together
with NRC (Canada), MOST and ASIAA (Taiwan), and
KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The _HST_ data
used in this work are obtained through the data archive
at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in
Astronomy, Inc. under NASA contract NAS 5-26555.


_Facilities:_ ALMA

Molecular Gas Properties of “Big Three Dragons” 13


REFERENCES



Apostolovski, Y., Aravena, M., Anguita, T., et al. 2019,
A&A, 628, A23, doi: [10.1051/0004-6361/201935308](http://doi.org/10.1051/0004-6361/201935308)

Asboth, V., Conley, A., Sayers, J., et al. 2016, MNRAS,
462, 1989, doi: [10.1093/mnras/stw1769](http://doi.org/10.1093/mnras/stw1769)

Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A,
51, 207, doi: [10.1146/annurev-astro-082812-140944](http://doi.org/10.1146/annurev-astro-082812-140944)

Bouwens, R. J., Oesch, P. A., Stefanon, M., et al. 2021, AJ,

162, 47, doi: [10.3847/1538-3881/abf83e](http://doi.org/10.3847/1538-3881/abf83e)

Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure,

R. M., & McLeod, D. J. 2018, ArXiv e-prints.

[https://arxiv.org/abs/1802.05720](https://arxiv.org/abs/1802.05720)

Bowler, R. A. A., Cullen, F., McLure, R. J., Dunlop, J. S.,

& Avison, A. 2022, MNRAS, 510, 5088,

doi: [10.1093/mnras/stab3744](http://doi.org/10.1093/mnras/stab3744)

Bowler, R. A. A., Dunlop, J. S., McLure, R. J., & McLeod,

D. J. 2017, MNRAS, 466, 3612,

doi: [10.1093/mnras/stw3296](http://doi.org/10.1093/mnras/stw3296)

Bowler, R. A. A., Dunlop, J. S., McLure, R. J., et al. 2014,

MNRAS, 440, 2810, doi: [10.1093/mnras/stu449](http://doi.org/10.1093/mnras/stu449)

Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105,

doi: [10.1146/annurev-astro-082812-140953](http://doi.org/10.1146/annurev-astro-082812-140953)

Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ,
887, 55, doi: [10.3847/1538-4357/ab52ff](http://doi.org/10.3847/1538-4357/ab52ff)

Cicone, C., Mainieri, V., Circosta, C., et al. 2021, A&A,

654, L8, doi: [10.1051/0004-6361/202141611](http://doi.org/10.1051/0004-6361/202141611)

Combes, F., Maoli, R., & Omont, A. 1999, A&A, 345, 369.


[https://arxiv.org/abs/astro-ph/9902286](https://arxiv.org/abs/astro-ph/9902286)

Combes, F., Rex, M., Rawle, T. D., et al. 2012, A&A, 538,

L4, doi: [10.1051/0004-6361/201118750](http://doi.org/10.1051/0004-6361/201118750)

Cormier, D., Abel, N. P., Hony, S., et al. 2019, A&A, 626,
A23, doi: [10.1051/0004-6361/201834457](http://doi.org/10.1051/0004-6361/201834457)

Croxall, K. V., Smith, J. D., Pellegrini, E., et al. 2017, ApJ,
845, 96, doi: [10.3847/1538-4357/aa8035](http://doi.org/10.3847/1538-4357/aa8035)

da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766,

13, doi: [10.1088/0004-637X/766/1/13](http://doi.org/10.1088/0004-637X/766/1/13)

Decarli, R., Pensabene, A., Venemans, B., et al. 2022,

A&A, 662, A60, doi: [10.1051/0004-6361/202142871](http://doi.org/10.1051/0004-6361/202142871)

Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020,
A&A, 643, A5, doi: [10.1051/0004-6361/202038231](http://doi.org/10.1051/0004-6361/202038231)

D’Odorico, V., Feruglio, C., Ferrara, A., et al. 2018, ApJL,
863, L29, doi: [10.3847/2041-8213/aad7b7](http://doi.org/10.3847/2041-8213/aad7b7)

Furusawa, H., Kashikawa, N., Kobayashi, M. A. R., et al.
2016, ApJ, 822, 46, doi: [10.3847/0004-637X/822/1/46](http://doi.org/10.3847/0004-637X/822/1/46)

Glover, S. C. O., Clark, P. C., Micic, M., & Molina, F.

2015, MNRAS, 448, 1607, doi: [10.1093/mnras/stu2699](http://doi.org/10.1093/mnras/stu2699)
Goldsmith, P. F. 2001, ApJ, 557, 736, doi: [10.1086/322255](http://doi.org/10.1086/322255)

Habing, H. J. 1968, BAN, 19, 421

Harikane, Y., Ono, Y., Ouchi, M., et al. 2022, ApJS, 259,

20, doi: [10.3847/1538-4365/ac3dfc](http://doi.org/10.3847/1538-4365/ac3dfc)



Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019,

PASJ, 71, 71, doi: [10.1093/pasj/psz049](http://doi.org/10.1093/pasj/psz049)

Heintz, K. E., & Watson, D. 2020, ApJL, 889, L7,

doi: [10.3847/2041-8213/ab6733](http://doi.org/10.3847/2041-8213/ab6733)

Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereˇs, D. 2008,

ApJS, 175, 356, doi: [10.1086/524362](http://doi.org/10.1086/524362)

Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, A&A,
602, A49, doi: [10.1051/0004-6361/201629588](http://doi.org/10.1051/0004-6361/201629588)

Jarugula, S., Vieira, J. D., Weiss, A., et al. 2021, ApJ, 921,
97, doi: [10.3847/1538-4357/ac21db](http://doi.org/10.3847/1538-4357/ac21db)

Jiao, Q., Zhao, Y., Lu, N., et al. 2019, ApJ, 880, 133,

doi: [10.3847/1538-4357/ab29ed](http://doi.org/10.3847/1538-4357/ab29ed)

Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887,
144, doi: [10.3847/1538-4357/ab55d6](http://doi.org/10.3847/1538-4357/ab55d6)

Kaasinen, M., Walter, F., Novak, M., et al. 2020, ApJ, 899,

37, doi: [10.3847/1538-4357/aba438](http://doi.org/10.3847/1538-4357/aba438)

Kamenetzky, J., Rangwala, N., Glenn, J., Maloney, P. R.,

& Conley, A. 2016, ApJ, 829, 93,
doi: [10.3847/0004-637X/829/2/93](http://doi.org/10.3847/0004-637X/829/2/93)

Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006,

ApJ, 644, 283, doi: [10.1086/503596](http://doi.org/10.1086/503596)

Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019,

MNRAS, 487, 3007, doi: [10.1093/mnras/stz1486](http://doi.org/10.1093/mnras/stz1486)

Komatsu, E., Smith, K. M., Dunkley, J., et al. 2011, ApJS,
192, 18, doi: [10.1088/0067-0049/192/2/18](http://doi.org/10.1088/0067-0049/192/2/18)

Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609,
A130, doi: [10.1051/0004-6361/201732019](http://doi.org/10.1051/0004-6361/201732019)

Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ,
737, 12, doi: [10.1088/0004-637X/737/1/12](http://doi.org/10.1088/0004-637X/737/1/12)

Li, J., Wang, R., Riechers, D., et al. 2020, ApJ, 889, 162,
doi: [10.3847/1538-4357/ab65fa](http://doi.org/10.3847/1538-4357/ab65fa)

Li, Q., Narayanan, D., & Dav´e, R. 2019, MNRAS, 490,
1425, doi: [10.1093/mnras/stz2684](http://doi.org/10.1093/mnras/stz2684)

Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A,
643, A141, doi: [10.1051/0004-6361/202038860](http://doi.org/10.1051/0004-6361/202038860)

Magdis, G. E., Daddi, E., B´ethermin, M., et al. 2012, ApJ,
760, 6, doi: [10.1088/0004-637X/760/1/6](http://doi.org/10.1088/0004-637X/760/1/6)

McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al.

2012, A&A, 544, A156,

doi: [10.1051/0004-6361/201219507](http://doi.org/10.1051/0004-6361/201219507)

McMullin, J. P., Waters, B., Schiebel, D., Young, W., &

Golap, K. 2007, in Astronomical Society of the Pacific

Conference Series, Vol. 376, Astronomical Data Analysis

Software and Systems XVI, ed. R. A. Shaw, F. Hill, &

D. J. Bell, 127

Meijerink, R., Spaans, M., & Israel, F. P. 2007, A&A, 461,
793, doi: [10.1051/0004-6361:20066130](http://doi.org/10.1051/0004-6361:20066130)

Narayanan, D., & Krumholz, M. R. 2014, MNRAS, 442,
1411, doi: [10.1093/mnras/stu834](http://doi.org/10.1093/mnras/stu834)

14 Hashimoto et al.



Narayanan, D., Krumholz, M. R., Ostriker, E. C., &

Hernquist, L. 2012, MNRAS, 421, 3127,

doi: [10.1111/j.1365-2966.2012.20536.x](http://doi.org/10.1111/j.1365-2966.2012.20536.x)


Novak, M., Ba˜nados, E., Decarli, R., et al. 2019, ApJ, 881,

63, doi: [10.3847/1538-4357/ab2beb](http://doi.org/10.3847/1538-4357/ab2beb)


Obreschkow, D., Heywood, I., Kl¨ockner, H. R., & Rawlings,

S. 2009, ApJ, 702, 1321,

doi: [10.1088/0004-637X/702/2/1321](http://doi.org/10.1088/0004-637X/702/2/1321)


Offner, S. S. R., Bisbas, T. G., Bell, T. A., & Viti, S. 2014,

MNRAS, 440, L81, doi: [10.1093/mnrasl/slu013](http://doi.org/10.1093/mnrasl/slu013)


Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713,

doi: [10.1086/160817](http://doi.org/10.1086/160817)


Papadopoulos, P. P., Bisbas, T. G., & Zhang, Z.-Y. 2018,

MNRAS, 478, 1716, doi: [10.1093/mnras/sty1077](http://doi.org/10.1093/mnras/sty1077)


Papadopoulos, P. P., R¨ottgering, H. J. A., van der Werf,

P. P., et al. 2000, ApJ, 528, 626, doi: [10.1086/308215](http://doi.org/10.1086/308215)


Pavesi, R., Riechers, D. A., Faisst, A. L., Stacey, G. J., &

Capak, P. L. 2019, ApJ, 882, 168,

doi: [10.3847/1538-4357/ab3a46](http://doi.org/10.3847/1538-4357/ab3a46)


Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ,

864, 49, doi: [10.3847/1538-4357/aacb79](http://doi.org/10.3847/1538-4357/aacb79)


Pound, M. W., & Wolfire, M. G. 2008, in Astronomical

Society of the Pacific Conference Series, Vol. 394,

Astronomical Data Analysis Software and Systems XVII,

ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654


Rawle, T. D., Egami, E., Bussmann, R. S., et al. 2014, ApJ,

783, 59, doi: [10.1088/0004-637X/783/1/59](http://doi.org/10.1088/0004-637X/783/1/59)


R´emy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014,

A&A, 563, A31, doi: [10.1051/0004-6361/201322803](http://doi.org/10.1051/0004-6361/201322803)


Riechers, D. A., Walter, F., Bertoldi, F., et al. 2009, ApJ,

703, 1338, doi: [10.1088/0004-637X/703/2/1338](http://doi.org/10.1088/0004-637X/703/2/1338)


Riechers, D. A., Bradford, C. M., Clements, D. L., et al.

2013, Nature, 496, 329, doi: [10.1038/nature12050](http://doi.org/10.1038/nature12050)


Riechers, D. A., Leung, T. K. D., Ivison, R. J., et al. 2017,

ApJ, 850, 1, doi: [10.3847/1538-4357/aa8ccf](http://doi.org/10.3847/1538-4357/aa8ccf)


Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ,

895, 81, doi: [10.3847/1538-4357/ab8c48](http://doi.org/10.3847/1538-4357/ab8c48)


Riechers, D. A., Nayyeri, H., Burgarella, D., et al. 2021,

ApJ, 907, 62, doi: [10.3847/1538-4357/abcf2e](http://doi.org/10.3847/1538-4357/abcf2e)


Rybak, M., Zavala, J. A., Hodge, J. A., Casey, C. M., &

Werf, P. v. d. 2020, ApJL, 889, L11,

doi: [10.3847/2041-8213/ab63de](http://doi.org/10.3847/2041-8213/ab63de)


Sakamoto, S. 1999, ApJ, 523, 701, doi: [10.1086/307741](http://doi.org/10.1086/307741)


Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83,

doi: [10.3847/0004-637X/820/2/83](http://doi.org/10.3847/0004-637X/820/2/83)


Shao, Y., Wang, R., Carilli, C. L., et al. 2019, ApJ, 876, 99,

doi: [10.3847/1538-4357/ab133d](http://doi.org/10.3847/1538-4357/ab133d)


Shi, Y., Wang, J., Zhang, Z.-Y., et al. 2016, Nature

Communications, 7, 13789, doi: [10.1038/ncomms13789](http://doi.org/10.1038/ncomms13789)



Shimajiri, Y., Sakai, T., Tsukagoshi, T., et al. 2013, ApJL,

774, L20, doi: [10.1088/2041-8205/774/2/L20](http://doi.org/10.1088/2041-8205/774/2/L20)


Solomon, P. M., Downes, D., & Radford, S. J. E. 1992,

ApJL, 398, L29, doi: [10.1086/186569](http://doi.org/10.1086/186569)


Springel, V., Pakmor, R., Pillepich, A., et al. 2018,

MNRAS, 475, 676, doi: [10.1093/mnras/stx3304](http://doi.org/10.1093/mnras/stx3304)


Stefan, I. I., Carilli, C. L., Wagg, J., et al. 2015, MNRAS,

451, 1713, doi: [10.1093/mnras/stv1108](http://doi.org/10.1093/mnras/stv1108)


Strandet, M. L., Weiss, A., Vieira, J. D., et al. 2016, ApJ,

822, 80, doi: [10.3847/0004-637X/822/2/80](http://doi.org/10.3847/0004-637X/822/2/80)


Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017,

ApJL, 842, L15, doi: [10.3847/2041-8213/aa74b0](http://doi.org/10.3847/2041-8213/aa74b0)


Sugahara, Y., Inoue, A. K., Hashimoto, T., et al. 2021,

ApJ, 923, 5, doi: [10.3847/1538-4357/ac2a36](http://doi.org/10.3847/1538-4357/ac2a36)


Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A,

58, 157, doi: [10.1146/annurev-astro-082812-141034](http://doi.org/10.1146/annurev-astro-082812-141034)


Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ,

853, 179, doi: [10.3847/1538-4357/aaa4b4](http://doi.org/10.3847/1538-4357/aaa4b4)


Tunnard, R., & Greve, T. R. 2016, ApJ, 819, 161,

doi: [10.3847/0004-637X/819/2/161](http://doi.org/10.3847/0004-637X/819/2/161)


Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ,

869, 27, doi: [10.3847/1538-4357/aaeb88](http://doi.org/10.3847/1538-4357/aaeb88)


Valentino, F., Tanaka, M., Davidzon, I., et al. 2020, ApJ,

889, 93, doi: [10.3847/1538-4357/ab64dc](http://doi.org/10.3847/1538-4357/ab64dc)


Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue,

B. 2015, ApJ, 813, 36, doi: [10.1088/0004-637X/813/1/36](http://doi.org/10.1088/0004-637X/813/1/36)


Vallini, L., Tielens, A. G. G. M., Pallottini, A., et al. 2019,

MNRAS, 490, 4502, doi: [10.1093/mnras/stz2837](http://doi.org/10.1093/mnras/stz2837)


Venemans, B. P., Walter, F., Decarli, R., et al. 2017a, ApJ,

837, 146, doi: [10.3847/1538-4357/aa62ac](http://doi.org/10.3847/1538-4357/aa62ac)


—. 2017b, ApJ, 845, 154, doi: [10.3847/1538-4357/aa81cb](http://doi.org/10.3847/1538-4357/aa81cb)


Vieira, D., Riechers, D. A., Pavesi, R., et al. 2022, ApJ,

925, 174, doi: [10.3847/1538-4357/ac403a](http://doi.org/10.3847/1538-4357/ac403a)


Vieira, J. D., Marrone, D. P., Chapman, S. C., et al. 2013,

Nature, 495, 344, doi: [10.1038/nature12001](http://doi.org/10.1038/nature12001)


Walter, F., Bertoldi, F., Carilli, C., et al. 2003, Nature, 424,

406, doi: [10.1038/nature01821](http://doi.org/10.1038/nature01821)


Wang, F., Wang, R., Fan, X., et al. 2019, ApJ, 880, 2,

doi: [10.3847/1538-4357/ab2717](http://doi.org/10.3847/1538-4357/ab2717)


Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714,

699, doi: [10.1088/0004-637X/714/1/699](http://doi.org/10.1088/0004-637X/714/1/699)


Wang, R., Wagg, J., Carilli, C. L., et al. 2011a, ApJL, 739,

L34, doi: [10.1088/2041-8205/739/1/L34](http://doi.org/10.1088/2041-8205/739/1/L34)


—. 2011b, AJ, 142, 101, doi: [10.1088/0004-6256/142/4/101](http://doi.org/10.1088/0004-6256/142/4/101)


—. 2013, ApJ, 773, 44, doi: [10.1088/0004-637X/773/1/44](http://doi.org/10.1088/0004-637X/773/1/44)


Wang, R., Wu, X.-B., Neri, R., et al. 2016, ApJ, 830, 53,

doi: [10.3847/0004-637X/830/1/53](http://doi.org/10.3847/0004-637X/830/1/53)


Wardlow, J. L., Cooray, A., Osage, W., et al. 2017, ApJ,

837, 12, doi: [10.3847/1538-4357/837/1/12](http://doi.org/10.3847/1538-4357/837/1/12)

Molecular Gas Properties of “Big Three Dragons” 15



Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A,

409, L41, doi: [10.1051/0004-6361:20031337](http://doi.org/10.1051/0004-6361:20031337)

Weiß, A., Walter, F., & Scoville, N. Z. 2005, A&A, 438,

533, doi: [10.1051/0004-6361:20052667](http://doi.org/10.1051/0004-6361:20052667)

Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ,

716, 1191, doi: [10.1088/0004-637X/716/2/1191](http://doi.org/10.1088/0004-637X/716/2/1191)

Yang, J., Venemans, B., Wang, F., et al. 2019, ApJ, 880,
153, doi: [10.3847/1538-4357/ab2a02](http://doi.org/10.3847/1538-4357/ab2a02)

Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS,
481, 1976, doi: [10.1093/mnras/sty2394](http://doi.org/10.1093/mnras/sty2394)



Zavala, J. A., Monta˜na, A., Hughes, D. H., et al. 2018,


Nature Astronomy, 2, 56, doi: [10.1038/s41550-017-0297-8](http://doi.org/10.1038/s41550-017-0297-8)


Zavala, J. A., Casey, C. M., Spilker, J., et al. 2022, ApJ,


933, 242, doi: [10.3847/1538-4357/ac7560](http://doi.org/10.3847/1538-4357/ac7560)


Zhang, Z.-Y., Papadopoulos, P. P., Ivison, R. J., et al.


2016, Royal Society Open Science, 3, 160025,


doi: [10.1098/rsos.160025](http://doi.org/10.1098/rsos.160025)


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[0]",
  "value": "Investigate the nature and mass of the molecular gas in the bright Lyman-break galaxy B14-65666 at z = 7.1520 using ALMA Band 3 observations of CO(6-5), CO(7-6), and [CI](2-1) and multiwavelength constraints.",
  "failed_quote": "It is therefore of interest to investigate the nature of the molecular gas in B14-65666 (“Big Three Dragons”) at z = 7.1520."
 },
 {
  "path": "processing.calibration.pipeline_or_manual.evidence[0]",
  "value": "pipeline",
  "failed_quote": "The data were reduced and calibrated with the Common Astronomy Software Application (CASA; McMullin et al. 2007) pipeline version 5.6.1-8."
 },
 {
  "path": "processing.calibration.casa_version.evidence[0]",
  "value": "5.6.1-8",
  "failed_quote": "The data were reduced and calibrated with the Common Astronomy Software Application (CASA; McMullin et al. 2007) pipeline version 5.6.1-8."
 },
 {
  "path": "processing.calibration.pipeline_version.evidence[0]",
  "value": "5.6.1-8",
  "failed_quote": "The data were reduced and calibrated with the Common Astronomy Software Application (CASA; McMullin et al. 2007) pipeline version 5.6.1-8."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "r_61 = 0.28 +0.04/-0.02, r_71 = 0.17 +0.02/-0.02",
  "failed_quote": "With ΣSFR = 20.6+11.4−7.6 M⊙ yr−1 kpc−2 obtained for the target, r61 = 0.28+0.04−0.02 and r71 = 0.17+0.02−0.02."
 },
 {
  "path": "analysis_steps[2].key_parameters[1].evidence[0]",
  "value": "alpha_CO = 25 M_sun (K km s^-1 pc^2)^-1 (range 5 - 25 for Z = 0.2 - 0.8 Z_sun)",
  "failed_quote": "With αCO = 25 M⊙ (K km s−1 pc2)−1 and the 3σ upper limit on L′COJ=1→0, we estimate the molecular gas mass to be M COmol < 3.0fCMB × 1011 M⊙ (3σ)."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "Data reduction, calibration, imaging (tclean), and moment 0 map creation (immoments)",
  "failed_quote": "The data were reduced and calibrated with the Common Astronomy Software Application (CASA; McMullin et al. 2007) pipeline version 5.6.1-8."
 }
]
```
