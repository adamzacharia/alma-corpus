# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...991L..38U\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version September 11, 2025
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**RIOJA.** **JWST** **and** **ALMA** **unveil** **the** **inhomogeneous** **and** **complex** **ISM** **structure** **in** **a**
**star-forming** **galaxy** **at** _z_ = 6 _._ 81


Mitsutaka Usui, [1] Ken [Mawatari,](http://orcid.org/0000-0003-4985-0201) [2, 3, 1, 4] Javier [Alvarez-M´arquez](http://orcid.org/0000-0002-7093-1877) [´], [5] Takuya [Hashimoto,](http://orcid.org/0000-0002-0898-4038) [1, 4] Yuma [Sugahara,](http://orcid.org/0000-0001-6958-7856) [2, 3]

Rui [Marques-Chaves,](http://orcid.org/0000-0001-8442-1846) [6] Akio [K.](http://orcid.org/0000-0002-7779-8677) Inoue, [2, 3] Luis [Colina,](http://orcid.org/0000-0002-9090-4227) [5] [Santiago](http://orcid.org/0000-0001-7997-1640) Arribas, [5] Carmen [Blanco-Prieto,](http://orcid.org/0009-0005-5448-5239) [5]

Yurina [Nakazato,](http://orcid.org/0000-0002-0984-7713) [7] Naoki [Yoshida,](http://orcid.org/0000-0001-7925-238X) [7, 8, 9] Tom J. [L.](http://orcid.org/0000-0002-5268-2221) C. Bakx, [10, 11, 12] Daniel [Ceverino,](http://orcid.org/0000-0002-8680-248X) [13, 14] Luca [Costantin,](http://orcid.org/0000-0001-6820-0015) [5]

Alejandro [Crespo](http://orcid.org/0000-0003-2119-277X) G´omez, [15] Masato [Hagimoto,](http://orcid.org/0000-0001-8083-5814) [11] Hiroshi Matsuo, [16, 17] Wataru Osone, [1] Yi [W.](http://orcid.org/0000-0002-6510-5028) Ren, [3]

Yoshinobu Fudamoto, [18] Takeshi Hashigaya, [19] Miguel [Pereira-Santaella,](http://orcid.org/0000-0002-4005-9619) [20] and Yoichi [Tamura](http://orcid.org/0000-0003-4807-8117) [11]


1 _Division_ _of_ _Physics,_ _Faculty_ _of_ _Pure_ _and_ _Applied_ _Sciences,_ _University_ _of_ _Tsukuba,_ _Tsukuba,_ _Ibaraki_ _305-8571,_ _Japan_
2 _Waseda_ _Research_ _Institute_ _for_ _Science_ _and_ _Engineering,_ _Faculty_ _of_ _Science_ _and_ _Engineering,_ _Waseda_ _University,_ _3-4-1_ _Okubo,_ _Shinjuku,_
_Tokyo_ _169-8555,_ _Japan_
3 _Department_ _of_ _Pure_ _and_ _Applied_ _Physics,_ _School_ _of_ _Advanced_ _Science_ _and_ _Engineering,_ _Faculty_ _of_ _Science_ _and_ _Engineering,_ _Waseda_
_University,_ _3-4-1_ _Okubo,_ _Shinjuku,_ _Tokyo_ _169-8555,_ _Japan_
4 _Tomonaga_ _Center_ _for_ _the_ _History_ _of_ _the_ _Universe_ _(TCHoU),_ _Faculty_ _of_ _Pure_ _and_ _Applied_ _Sciences,_ _University_ _of_ _Tsukuba,_ _Tsukuba,_
_Ibaraki_ _305-8571,_ _Japan_
5 _Centro_ _de_ _Astrobiolog´ıa_ _(CAB),_ _CSIC-INTA,_ _Ctra._ _de_ _Ajalvir_ _km_ _4,_ _Torrej´on_ _de_ _Ardoz,_ _E-28850,_ _Madrid,_ _Spain_
6 _Geneva_ _Observatory,_ _Department_ _of_ _Astronomy,_ _University_ _of_ _Geneva,_ _Chemin_ _Pegasi_ _51,_ _CH-1290_ _Versoix,_ _Switzerland_
7 _Department_ _of_ _Physics,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
8 _Kavli_ _Institute_ _for_ _the_ _Physics_ _and_ _Mathematics_ _of_ _the_ _Universe_ _(WPI),_ _UT_ _Institute_ _for_ _Advanced_ _Study,_ _The_ _University_ _of_ _Tokyo,_
_Kashiwa,_ _Chiba_ _277-8583,_ _Japan_
9 _Research_ _Center_ _for_ _the_ _Early_ _Universe,_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
10 _Department_ _of_ _Space,_ _Earth,_ _&_ _Environment,_ _Chalmers_ _University_ _of_ _Technology,_ _Chalmersplatsen_ _4_ _412_ _96_ _Gothenburg,_ _Sweden_
11 _Department_ _of_ _Physics,_ _Graduate_ _School_ _of_ _Science,_ _Nagoya_ _University,_ _Nagoya_ _464-8602,_ _Japan_
12 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1,_ _Osawa,_ _Mitaka,_ _Tokyo,_ _Japan_
13 _Universidad_ _Autonoma_ _de_ _Madrid,_ _Ciudad_ _Universitaria_ _de_ _Cantoblanco,_ _E-28049_ _Madrid,_ _Spain_
14 _CIAFF,_ _Facultad_ _de_ _Ciencias,_ _Universidad_ _Autonoma_ _de_ _Madrid,_ _E-28049_ _Madrid,_ _Spain_
15 _Space_ _Telescope_ _Science_ _Institute_ _(STScI),_ _3700_ _San_ _Martin_ _Drive,_ _Baltimore,_ _MD_ _21218,_ _USA_
16 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
17 _Graduate_ _University_ _for_ _Advanced_ _Studies_ _(SOKENDAI),_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
18 _Center_ _for_ _Frontier_ _Science,_ _Chiba_ _University,_ _1-33_ _Yayoi-cho,_ _Inage-ku,_ _Chiba_ _263-8522,_ _Japan_
19 _Department_ _of_ _Astronomy,_ _Kyoto_ _University_ _Sakyo-ku,_ _Kyoto_ _606-8502,_ _Japan_
20 _Instituto_ _de_ _F´ısica_ _Fundamental_ _(IFF),_ _CSIC,_ _Serrano_ _123,_ _E-28006,_ _Madrid,_ _Spain_


(Received 2025/July/3; Accepted ??)


Submitted to ApJL


ABSTRACT


We report the discovery of a complex, density-stratified interstellar medium (ISM) in the star-forming
galaxy COS-2987 at _z_ = 6 _._ 81, revealed by the unprecedented synergy between JWST/NIRSpec IFS and
ALMA observations. These observations detect key emission lines, including [O ii] _λλ_ 3727, 3730, [O
iii] 4364, [O iii] _λλ_ 4960, 5008, [O iii] 88 _µ_ m, as well as H _α_ and H _β_ . JWST spectroscopy alone indicates
ISM properties that are typical for galaxies at _z_ _∼_ 7. These include low dust extinction ( _A_ V _≈_ 0 _._ 14
mag), moderate electron density ( _n_ e _≈_ 500 cm _[−]_ [3] ), and low gas-phase metallicity ( _∼_ 10%). However,
the strong far-infrared [O iii] 88 _µ_ m emission detected by ALMA cannot be explained by a singlecomponent ionized medium with uniform electron density and temperature. Instead, a two-component
ISM model, comprising compact, high-temperature, high-density gas components ( _T_ _e_ _≈_ 26 _,_ 000 K;
_n_ _e_ _≈_ 600 cm _[−]_ [3] ) and an extended, cooler, lower-density component ( _T_ _e_ _≈_ 8 _,_ 000 K; _n_ _e_ _≈_ 50 cm _[−]_ [3] ),


Corresponding author: Takuya Hashimoto

[hashimoto.takuya.ga@u.tsukuba.ac.jp](mailto: hashimoto.takuya.ga@u.tsukuba.ac.jp)

2 Usui et al.


successfully reproduces the observed line ratios of [O iii] 88 _µ_ m/[O iii] 5008 [˚] A and [O iii] 4364/[O
iii] 5008 [˚] A, with a volume ratio of 1 : 300 between the two components. Our results demonstrate
that JWST alone probes only a fraction of the ISM and highlight the critical importance of combining
JWST and ALMA to reveal the density-stratified ISM of early galaxies.


_Keywords:_ galaxies: high-redshift, galaxies: ISM, galaxies: star formation



1. INTRODUCTION


Understanding the physical properties of the interstellar medium (ISM) in galaxies is crucial for studying galaxy formation and evolution. With the advent of
the _James Webb Space Telescope_ (JWST; Gardner et al.
2023) and the Atacama Large Millimeter/submillimeter
Array (ALMA; Wootten & Thompson 2009), fundamental physical quantities in H ii regions, such as electron
density ( _n_ e ), electron temperature ( _T_ e ), ionization parameter, and gas-phase metallicity, can now be measured even in galaxies at redshift ( _z_ ) beyond 4 out to
the epoch of reionization ( _z_ ≳ 6) (e.g., Killi et al. 2023;
Isobe et al. 2023; Nakajima et al. 2023; Arribas et al.
2024; Laseter et al. 2024; Alvarez-M´arquez [´] et al. 2025;
Abdurro’uf et al. 2024; Sanders et al. 2024; Zavala et al.
2025).
Recent studies have reported evidence for a densitystratified ISM in high- _z_ galaxies based on emission-line
diagnostics spanning the rest-frame ultraviolet (UV) and
optical wavelengths. Specifically, _n_ e derived from highionization UV lines such as C iii] _λλ_ 1907, 1909 and
N iv] _λλ_ 1483, 1486 [1] often exceed 10 [4] –10 [5] cm _[−]_ [3], while
lower densities (10 [2] –10 [3] cm _[−]_ [3] ) are inferred from optical diagnostics such as [O ii] _λλ_ 3727, 3730 or [S ii] _λλ_
6718, 6733 [2] (e.g., Mingozzi et al. 2022; Ji et al. 2024;
Topping et al. 2025; Alvarez-M´arquez [´] et al. 2025; A.
Crespo G´omez et al., in preparation). This apparent
discrepancy is interpreted as evidence for a densitystratified ISM, in which UV lines such as C iii] and N
iv] trace highly ionized, high-density regions, whereas
optical lines like [O ii] and [S ii] originate from lowerionization, lower-density gas.
A similar trend is also seen in the far-infrared regime.
Based on _Herschel_ /PACS observations of LMC-N11, the
second largest giant H ii region in the LMC after 30 Do

1 C iii] has an ionization potential of 24.4 eV, with critical densities of _∼_ 8 _._ 7 _×_ 10 [4] and _∼_ 2 _._ 8 _×_ 10 [5] cm _[−]_ [3] for _λλ_ 1907, 1909,
respectively. N iv] has a higher ionization potential of 47.5 eV,
and _n_ crit values of _∼_ 1 _._ 5 _×_ 10 [5] and _∼_ 5 _._ 0 _×_ 10 [5] cm _[−]_ [3] for _λλ_ 1483,
1486 (e.g., Osterbrock & Ferland 2006).

2 [O ii] has an ionization potential of 13.6 eV, with critical densities
of _∼_ 1 _._ 4 _×_ 10 [3] and _∼_ 3 _._ 4 _×_ 10 [3] cm _[−]_ [3] for _λλ_ 3727, 3730 respectively.

[S ii] has an ionization potential of 10.4 eV, and _n_ crit values
of _∼_ 1 _._ 5 _×_ 10 [3] and _∼_ 3 _._ 9 _×_ 10 [3] cm _[−]_ [3] for _λλ_ 6718, 6733 (e.g.,
Osterbrock & Ferland 2006).



radus, Lebouteiller et al. (2012) found that [O iii] 88 _µ_ m
emission is spatially extended well beyond the area predicted from the number of massive stars. The emission
requires low-density gas with _n_ e _<_ 16 cm _[−]_ [3], which is
much lower than the values inferred from optical [O ii]
and [S ii] doublets ( _∼_ 100 cm _[−]_ [3] ) or [Cl iii] _λλ_ 5517, 5538
( _∼_ 1700 cm _[−]_ [3] ). They interpreted this as evidence that

[O iii] 88 _µ_ m emission is photoionized by far-UV photons that penetrate into low-density regions due to a
clumpy ISM structure.
Motivated by these findings, we investigate whether a
similar stratification of highly ionized gas can be identified by combining rest-frame optical and far-infrared
(FIR) [O iii] emission lines [3] .
In principle, one can determine both _T_ e and _n_ e of
an H ii region with uniform physical conditions using
emission lines of [O iii]. For example, the flux ratio of

[O iii] 5008 [˚] A/4364 [˚] A depends primarily on _T_ e, whereas
the flux ratio of [O iii] 88 _µ_ m/5008 [˚] A depends on both
_T_ e and _n_ e (e.g., Dinerstein et al. 1985; Osterbrock & Ferland 2006; Kewley et al. 2019; Jones et al. 2020; Yang &
Lidz 2020; Nakazato et al. 2023). This technique has recently been applied to local analogues of high- _z_ galaxies
to investigate ISM properties such as _T_ e, _n_ e, and elemental abundance ratios (e.g., Chen et al. 2023, 2024;
see also Kumari et al. 2024).
At _z_ ≳ 6, the powerful synergy between JWST and
ALMA enables, for the first time, complementary observations of rest-frame optical and FIR [O iii] emission
lines. Fujimoto et al. (2024), Stiavelli et al. (2023), and
Harshan et al. (2024) have estimated _n_ e in _z_ _∼_ 8–9
galaxies based on measurements of _T_ e from optical spectroscopy and the flux ratio of [O iii] 88 _µ_ m/5008 A. How- [˚]
ever, these studies utilized the NIRSpec multi-object
spectroscopy (MOS) mode to observe optical [O iii]
emission lines, which are subject to uncertainties arising from slit-loss corrections and from effects related to
the position angle, particularly when the high- _z_ source
has a clumpy morphology or is elongated along a specific axis. In contrast, ALMA observations are free from
such observational limitations. To accurately character

3 [O iii] has an ionization potential of 35.1 eV, and critical densities
of 3 _._ 0 _×_ 10 [6], 6 _._ 8 _×_ 10 [5], and 510 cm _[−]_ [3] for _λ_ 4364 [˚] A, _λ_ 5008 [˚] A, and
88 _µ_ m, respectively (e.g., Osterbrock & Ferland 2006).

ISM Physical Properties of COS-2987030247 3



ize the global properties of galaxies, a combination of
NIRSpec integral field spectroscopy (IFS; B¨oker et al.
2022) and ALMA observations is a crucial next step (see
e.g., Scholtz et al. 2025; Zavala et al. 2025).
The RIOJA (Reionization and the ISM/Stellar Origins with JWST and ALMA) project (JWST GO1
PID 1840; PIs: J. Alvarez-M´arquez [´] and T. Hashimoto;
Hashimoto et al. 2023; Sugahara et al. 2025; Mawatari
et al. 2025) conducts follow-up observations of 12 ALMA

[O iii] 88 _µ_ m emitters using NIRSpec/IFS and NIRCam. Here, we present a combined analysis of optical and FIR [O iii] emission lines in COS-2987030247
(hereafter COS-2987; Smit et al. 2015; Laporte et al.
2017; Smit et al. 2018; Witstok et al. 2022; Posses et al.
2023; Harikane et al. 2025a; Mawatari et al. 2025), a
star-forming galaxy at _z_ = 6 _._ 81. We find that a simple
homogeneous ISM model cannot reproduce the observed

[O iii] line ratios, suggesting the presence of hidden complexity in the ionized gas structure, such as multiple ionized gas components with distinct physical conditions in
terms of _T_ e and _n_ e .
In a companion paper (Mawatari et al. 2025), we provide an overview of the observations of COS-2987, discuss its stellar populations based on combined JWST
and ALMA data, and present the ISM properties derived from JWST’s spatially-resolved observations.
Throughout this paper, we adopt a ΛCDM cosmology with Ω _m_ = 0 _._ 3, Ω Λ = 0 _._ 7, and _H_ 0 =
70 km s _[−]_ [1] Mpc _[−]_ [1] . We assume a solar luminosity of
_L_ _⊙_ = 3 _._ 839 _×_ 10 [33] erg s _[−]_ [1] and a solar metallicity of
12+log(O _/_ H) _⊙_ = 8 _._ 69 (Asplund et al. 2009). Hereafter,

[O ii] _λλ_ 3727, 3730, [O iii] 4364 [˚] A, [O iii] _λλ_ 4960, 5008
and [O iii] 88 _µ_ m are referred to as [O ii]3727, 3730, [O
iii]4364, [O iii]4960, 5008 and [O iii]88, respectively, unless otherwise specified.


2. OBSERVATIONS AND DATA


2.1. _JWST_ _NIRSpec_ _IFS_ _Data_


The JWST NIRSpec IFS data were obtained as part
of the RIOJA project. The specific observations can
be accessed via the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute: [doi:10.17909/6mmv-2944.](https://doi.org/10.17909/6mmv-2944) Details of the
observations and data reduction procedures are presented in Mawatari et al. (2025). Briefly, we used the
G395H/F290LP grating/filter combination, which provides a high spectral resolution ( _R_ _∼_ 2700) and covers
a wavelength range from 2.87 to 5.27 _µ_ m.
The raw data were processed using the JWST reduction pipeline version 1.14.0 (Bushouse et al. 2024) under
the CRDS context `jwst` `1223.pmap` . We performed the
following custom steps to improve the data quality: (1)



sigma clipping to reject bad pixels and cosmic rays, and
(2) subtraction of the median background from the calibrated images (e.g., Ubler et al. 2023 [¨] ; Perna et al. 2023;
Marshall et al. 2023). The final data cube was combined
using the “drizzle” method, sampled with a pixel size of
0 _[′′]_ _._ 05. To ensure that the line fluxes are measured from
the same spatial region, the point-spread function (PSF)
of the cube was matched to that of the H _α_ emission line,
which corresponds to the longest wavelength among the
detected lines (see Appendix A).
As presented in Mawatari et al. (2025), we detected
multiple emission lines, including [O ii]3727, 3730, H _β_,

[O iii]4364, [O iii]4960, 5008, and H _α_, all at ≳ 4 _σ_ significance in the integrated spectrum. The left panel
of Figure 1 shows the integrated intensity map of the

[O iii]5008 emission, while the spatially integrated onedimentional spectra of [O iii]4364 and [O iii]5008 are
shown in the right panel.
Table 1 shows the line fluxes. The fluxes were obtained by applying Gaussian fitting to each line profile,
where the spectra were extracted from regions with ≳ 2 _σ_
significance in the [O iii]5008 intensity map (Figure 1).
Based on a curve-of-growth analysis, we estimate that
the adopted aperture misses _≈_ 10% of the total flux.
Therefore, we applied a 10% aperture correction to all
line flux values, because we use the PSF-matched data.
This aperture correction does not affect the line ratios
of NIRSpec IFS data, but is required when comparing
NIRSpec IFS and ALMA data.


2.2. _ALMA_ _[O_ iii _]_ _88_ _µm_ _data_


ALMA Band 8 (Sekimoto et al. 2008) [4] observations
targeting [O iii]88 in COS-2987 were conducted as part
of an ALMA Cycle 6 program (ID: 2018.1.00429.S, PI:
R. Smit). Although Witstok et al. (2022) presented the
initial detection and results of the [O iii]88 line, we reanalyzed the data cube to uniformly measure the line flux
of COS-2987 in a manner consistent with other RIOJA

studies.

The data were reduced using the Common Astronomy
Software Applications (CASA; CASA Team et al. 2022)
version 5.6. Imaging was performed with the CASA
`tclean` task, adopting natural weighting to optimize
point-source sensitivity. The final cube has a synthesized beam size of 0 _[′′]_ _._ 80 _×_ 0 _[′′]_ _._ 61 with a positional angle of
86 _[◦]_, consistent with Witstok et al. (2022). The typical
rms noise of the cube is 0 _._ 576 mJy beam _[−]_ [1] per 30 km s _[−]_ [1]

channel.


4 See also Bakx & Conway (2024) for a summary of ALMA receiver
references.

4 Usui et al.


**Figure** **1.** ( _Left_ ) Integrated intensity map of the NIRSpec [O iii]5008 emission. The red contours show the _±_ 2 _[n]_ _σ_ significance
levels ( _n_ = 1 _,_ 2 _,_ 3 _, . . ._ ), where _σ_ = 1 _._ 16 _×_ 10 _[−]_ [20] erg s _[−]_ [1] cm _[−]_ [2] pixel _[−]_ [1] . Positive and negative contours are shown by the solid
and dashed lines, respectively. The orange circle at the bottom left indicates the FWHM of 0 _[′′]_ _._ 21 at the observed wavelength
of H _α_ (5 _._ 125 _µ_ m). ( _Right_ ) One-dimensional spectra of [O iii] 4364, [O iii] 5008, and [O iii] 88, where the horizontal axis is the
velocity relative to the best-fit redshift to the [O iii] 5008 line. In each panel, the red solid histogram and gray shade indicate
the observed flux density and 1 _σ_ uncertainty, respectively. The gray shade is not visible for [O iii]5008 due to its negligible 1 _σ_
uncertainty.



As shown in Figure B.1 in Appendix B, we integrated the emission over the frequency range of
434.2–434.9 GHz, corresponding to a velocity width of
480 km s _[−]_ [1] (i.e., _≈_ 3 times the FWHM of the optical
lines), to generate the integrated intensity (moment-0)
map of the [O iii]88 emission. The noise level of the map
is _σ_ = 82 _._ 6 mJy beam _[−]_ [1] km s _[−]_ [1], and the [O iii]88 line is
detected at a peak significance of 7 _._ 5 _σ_ . We measure an
integrated line flux of 1 _._ 06 _±_ 0 _._ 23 Jy km s _[−]_ [1], corresponding to a flux of (15 _._ 3 _±_ 3 _._ 3) _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2], consistent with the values reported in Witstok et al. (2022)
within uncertainties. The bottom right panel of Figure
1 shows the spectrum of [O iii]88 emission.


3. PROPERTIES OBTAINED FROM NIRSPEC/IFS


3.1. _Integrated_ _Internal_ _Dust_ _Extinction_


We estimate the internal dust extinction ( _A_ _V_ ) of COS2987 to correct the observed emission line fluxes. We
derive _A_ _V_ based on the Balmer decrement of H _α_ /H _β_ as



follows [5] :


2 _._ 5 _× R_ _V_
_A_ _V_ =
_k_ ( _λ_ H _β_ ) _−_ _k_ ( _λ_ H _α_ ) [log] [10]



(H _α/_ H _β_ ) obs
� (H _α/_ H _β_ ) theo



_,_ (1)
�



where _k_ ( _λ_ ) denotes the extinction curve, and _R_ _V_ _≡_
_A_ _V_ _/E_ ( _B −_ _V_ ) is the total-to-selective extinction ratio.
We adopt the SMC extinction curve with _R_ _V_ = 2 _._ 74
(Gordon et al. 2003). (H _α/_ H _β_ ) obs and (H _α/_ H _β_ ) theo represent the observed and theoretical Balmer line ratios,
respectively. We obtain (H _α/_ H _β_ ) obs = 3 _._ 00 _±_ 0 _._ 40 (Table 1).
To account for the dependence of (H _α/_ H _β_ ) theo on
electron density and temperature, we perform an iterative calculation following Welch et al. (2024), who carefully derived ISM properties for two high- _z_ star-forming
galaxies using data from the TEMPLATES JWST Early


5 At the sky position of the target and over the wavelength range of
_∼_ 3–5 _µ_ m, the Galactic extinction is negligible ( _A_ _λ_ _<_ 0 _._ 01 mag;
Schlegel et al. 1998).

ISM Physical Properties of COS-2987030247 5



**Table** **1.** The spatially-integrated properties for COS-2987.


Line fluxes ~~[†]~~ [10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] ]


_F_ [OII]3727 7 _._ 1 _±_ 0 _._ 9
_F_ [OII]3730 7 _._ 6 _±_ 1 _._ 2
_F_ [OIII]4364 1 _._ 8 _±_ 0 _._ 5
_F_ H _β_ 8 _._ 0 _±_ 0 _._ 8

_F_ [OIII]4960 17 _._ 4 _±_ 1 _._ 8
_F_ [OIII]5008 52 _._ 3 _±_ 5 _._ 4

_F_ H _α_ 23 _._ 9 _±_ 2 _._ 4

_F_ [OIII]88 15 _._ 3 _±_ 3 _._ 3

Line Ratios [††]


H _α_ /H _β_ 3 _._ 00 _±_ 0 _._ 40

[O iii]4364/5008 0 _._ 038 [+0] _−_ 0 _[.]_ _._ [010] 011

[O ii]3730/3727 1 _._ 05 _±_ 0 _._ 21

[O ii]3727,3730/H _β_ 1 _._ 99 [+0] _−_ 0 _[.]_ _._ [41] 37

[O iii]4960,5008/H _β_ 8 _._ 64 [+0] _−_ 0 _[.]_ _._ [13] 09

[O iii]88/5008 _[a]_ 0 _._ 22 [+0] _−_ 0 _[.]_ _._ [09] 07

Physical properties


_A_ _V_ /mag 0 _._ 14 [+0] _−_ 0 _[.]_ _._ [32] 14
_T_ e ([O iii])/K 2 _._ 02 [+0] _−_ 0 _[.]_ _._ [30] 28 _[×]_ [ 10] [4]

_T_ e ([O ii])/K _[b]_ 1 _._ 72 [+0] _−_ 0 _[.]_ _._ [21] 20 _[×]_ [ 10] [4]

_n_ e ([O ii])/cm _[−]_ [3] 494 [+546] _−_ 300
12+log(O/H) 7 _._ 67 [+0] _−_ 0 _[.]_ _._ [11] 13

Dust-corrected line luminosity [ _×_ 10 [8] _L_ _⊙_ ]

_L_ [O iii]4364 3 _._ 35 [+2] _−_ 1 _[.]_ _._ [08] 17
_L_ [O iii]5008 88 _._ 5 [+44] _−_ 17 _[.]_ _._ [2] 2
_L_ [O iii]88 21 _._ 4 _±_ 4 _._ 6

_†_ All values before the dust correction.

_††_ All values corrected by dust extinction, except the Balmer
decrement, for which we present the observed value.


_a_
The [O iii]88/5008 ratio includes 10% absolute flux calibration uncertainties for both [O iii]5008 and 88 fluxes (see §
4).


_b_
Scaled from _T_ e ([O iii]) with eq. (2).


Release Science (ERS) program (Rigby et al. 2025) [6] .


6 We first calculate (H _α/_ H _β_ ) theo in Case B recombination, assuming an electron density of _n_ e = 100 cm _[−]_ [3] and an electron temperature of _T_ e = 10 [4] K, using the `PyNeb` `RecAtom` function (Luridiana et al. 2015). We then derive _A_ _V_ from eq. (1), correct the
observed emission line fluxes for dust attenuation, and remeasure
the electron density and temperature from the [O ii]3730/3727
and [O iii]5008/4364 line ratios, respectively. This process is
repeated until the change in temperature between iterations becomes less than 10 K.



To estimate the uncertainty in _A_ _V_, we perform a Monte
Carlo simulation with 10,000 realizations, randomly perturbing the observed H _α_ and H _β_ fluxes within their un
certainties.
We find _A_ _V_ = 0 _._ 14 [+0] _−_ 0 _[.]_ _._ [32] 14 [mag.] This result indicates
that COS-2987 is dust-poor, consistent with the nondetection of dust continuum emission by ALMA (Smit
et al. 2018; Witstok et al. 2022). Hereafter, unless otherwise stated, we base our analysis on the dust-corrected
line ratios in Table 1.


3.2. _Electron_ _Temperature_


We measure the electron temperature of the highly
ionized gas, _T_ e ([O iii]), based on the [O iii]4364/5008
line ratio using the `PyNeb` `getTemDen` function (Luridiana et al. 2015). The uncertainty in _T_ e ([O iii]) is
estimated via a Monte Carlo method, following the
same approach as for _A_ _V_ (§3.1). Based on the measured line ratio of [O iii]4364/5008 = 0 _._ 038 [+0] _−_ 0 _[.]_ _._ [010] 011 [(Ta-]
ble 1), we derive an electron temperature of _T_ e ([O iii]) =
2 _._ 02 [+0] _−_ 0 _[.]_ _._ [30] 28 _[×]_ [10] [4] [ K.] [This] [value] [is] [comparable] [to] [those]
found in other _z_ _∼_ 7 galaxies with similar gas-phase
metallicity to COS-2987 ( _≈_ 10% of the solar metallicity; see § 3.4)z observed by JWST (e.g., Schaerer et al.
2022; Rhoads et al. 2023; Nakajima et al. 2023; Sanders
et al. 2024; Laseter et al. 2024; Morishita et al. 2024;
Curti et al. 2024).
We estimate the electron temperature of the lower ionization gas, _T_ e ([O ii]), using the relation from Campbell
et al. (1986); Stasi´nska (1982):


_T_ e ([O ii]) = 0 _._ 7 _× T_ e ([O iii]) + 3000 K _._ (2)


Applying this relation, we obtain _T_ e ([O ii]) = 1 _._ 72 [+0] _−_ 0 _[.]_ _._ [21] 20 _[×]_
10 [4] K.


3.3. _Electron_ _Density_


We estimate the electron density based on the [O
ii]3730/3727 line ratio, using the `PyNeb` `getTemDen`
function (Luridiana et al. 2015). We adopt _T_ e ([O ii])
derived in §3.2, although the [O ii]3730/3727 ratio has
a weak dependence on electron temperature. The uncertainty in _n_ e ([O ii]) is evaluated using a Monte Carlo
method, following the same procedure as for _A_ _V_ (§3.1).
From the measured line ratio of [O ii]3730/3727 = 1 _._ 05 _±_
0 _._ 21 (Table 1), we derive an electron density of _n_ e ([O
ii]) = 494 _−_ [+546] 300 [cm] _[−]_ [3] [.]
Figure 2 shows the redshift evolution of electron density, where the red star represents _n_ e of COS-2987. The
_n_ e values at _z_ _∼_ 0–3 in Davies et al. (2021) are derived from the [S ii] ratio, while those in Sanders et al.
(2016) are obtained from either [S ii] or [O ii] line ratios. Our measurement is consistent with typical values

6 Usui et al.


4. [O iii] LINE RATIO DIAGNOSTICS COMBINING
JWST AND ALMA



**Figure** **2.** Redshift evolution of the electron density _n_ e .
The red star indicates the electron density of COS-2987, derived from the [O ii] ratio. Literature data at _z_ _∼_ 0–3 are
compiled from Sanders et al. (2016) ([S ii] or [O ii]) and
Davies et al. (2021) ([S ii]), while data at _z_ ≳ 4 are taken
from Isobe et al. (2023), Abdurro’uf et al. (2024), and Marconcini et al. (2024), all based on the [O ii] ratios. Filled
symbols represent measurements for individual galaxies, and
open symbols represent median values for the sample galaxies. The electron density of COS-2987, derived from the [O
ii] ratio, is consistent with the overall redshift evolution trend
indicated by the blue dashed line (Abdurro’uf et al. 2024).


for _z_ _∼_ 5 _−_ 10 galaxies derived from the [O ii] ratio
(Isobe et al. 2023; Abdurro’uf et al. 2024; Marconcini
et al. 2024), and also agrees with the best-fit redshift–
electron density relation shown by the blue dashed line
(Abdurro’uf et al. 2024). We stress that the data point
of COS-2987 nicely fills in the redshift gap ( _z_ _∼_ 6 _−_ 8)
in the previous study of Isobe et al. (2023).


3.4. _Gas-Phase_ _Metallicity_ _based_ _on_ _the_ _direct-T_ e
_method_


We estimate the oxygen abundance, 12 + log(O _/_ H),
as a proxy for gas-phase metallicity using the direct_T_ e method with the `PyNeb` `getIonAbundance` function
(Luridiana et al. 2015). We assume that the total oxygen abundance O/H is the sum of O [++] _/_ H [+] and O [+] _/_ H [+] .
The O [++] _/_ H [+] abundance is estimated from the [O
iii]4960,5008/H _β_ ratio and _T_ e ([O iii]), while the O [+] _/_ H [+]

abundance is derived from the [O ii]3727,3730/H _β_ ratio
and _T_ e ([O ii]) (Table 1).
The uncertainty in 12 + log(O _/_ H) is evaluated using
the same Monte Carlo technique adopted for _A_ _V_ (§3.1).
We obtain a metallicity of 12 + log(O _/_ H) = 7 _._ 67 [+0] _−_ 0 _[.]_ _._ [11] 13 [,]
corresponding to 10 _±_ 2% of the solar metallicity.



One of the major strengths of this study is that we
have four [O iii] emission lines: rest-frame optical emission lines of [O iii]4364, [O iii]4960, 5008 observed with
JWST/NIRSpec IFS, together with the rest-frame FIR
emission line [O iii]88 observed with ALMA. Since these
are emitted from the same ion of oxygen, we can derive
the physical properties of nebulae without assumptions
of abundance ratios.

The left panel of Figure 3 presents a diagnostic diagram of the optical [O iii] line ratio ([O
iii]4364/5008) versus the FIR-to-optical [O iii] line ratio ([O iii]88/5008), overlaid with model grids covering
a wide range of _n_ e and _T_ e values. These model grids
are calculated with `PyNeb` assuming that all [O iii] lines
originate from a homogeneous ionized gas with uniform
electron temperature and density.
The red star in the left panel of Figure 3 shows the
observed [O iii] line ratios for COS-2987, where the [O
iii]88/5008 ratio incorporates a 10% absolute flux calibration uncertainty for both [O iii]5008 (B¨oker et al.
2023 [7] ) and [O iii]88 (ALMA Cycle 6 Proposer’s Guide [8] ).
For comparison, we also plot [O iii] line ratios from
the literature. Black filled symbols represent high_z_ star-forming galaxies. These include COS-3018 at
_z_ = 6 _._ 85 (Smit et al. 2018; Witstok et al. 2022; Scholtz
et al. 2025), SXDF-NB1006-2 at _z_ = 7 _._ 21 (Inoue et al.
2016; Ren et al. 2023; Harikane et al. 2025b; Y. W.
Ren et al. 2025, MNRAS, submitted), J0217-0208 at
_z_ = 6 _._ 20 (Harikane et al. 2020, 2025b), and J1211-0118
at _z_ = 6 _._ 03 (Harikane et al. 2020, 2025b), where [O
iii]4364 and [O iii]5008 were observed using the NIRSpec/IFS mode and [O iii]88 with ALMA. We additionally plot MACS0416-Y1 at _z_ = 8 _._ 38 (Bakx et al.
2020; Tamura et al. 2023; Harshan et al. 2024; Hagimoto
et al. 2025), SMACS0723-04590 at _z_ = 8 _._ 50 (Fujimoto
et al. 2024) and MACS1149-JD1 at _z_ = 9 _._ 11 (Hashimoto
et al. 2018; Tokuoka et al. 2022; Stiavelli et al. 2023),
where [O iii]4364 and [O iii]5008 were observed using
the NIRSpec/MOS [9] mode and [O iii]88 with ALMA.
Black open symbols show local dwarf galaxies, includ

7 See also “Data Calibration Considerations” in the
JWST User Documentation: [https://jwst-docs.stsci.edu/](https://jwst-docs.stsci.edu/depreciated-jdox-articles/jwst-data-calibration-considerations)
[depreciated-jdox-articles/jwst-data-calibration-considerations](https://jwst-docs.stsci.edu/depreciated-jdox-articles/jwst-data-calibration-considerations)

8 [https://almascience.eso.org/documents-and-tools/cycle6/](https://almascience.eso.org/documents-and-tools/cycle6/alma-proposers-guide)
[alma-proposers-guide](https://almascience.eso.org/documents-and-tools/cycle6/alma-proposers-guide)
9 In MACS0416-Y1, the NIRSpec prism mode do not spectrally
resolve [O iii]4364 and H _γ_, but the authors were able to decompose these line fluxes based on the Balmer decrement obtained
from H _α_ and H _β_ .

ISM Physical Properties of COS-2987030247 7


**Figure** **3.** ( _Left_ ) Diagnostic diagram of the [O iii] line ratios overlaid with _T_ e – _n_ e model grids generated using `PyNeb` (Luridiana
et al. 2015). The red star indicates the observed [O iii] line ratios of COS-2987 (Table 1). The gray star shows the ratios dustcorrected on a pixel-by-pixel basis using the _A_ _V_ map shown in the right panel (§ 5.1). Black filled symbols represent high- _z_
star-forming galaxies (Witstok et al. 2022; Stiavelli et al. 2023; Fujimoto et al. 2024; Harshan et al. 2024; Harikane et al. 2025b),
where the optical [O iii] data are obtained from NIRSpec/IFS for COS-2987, COS-3018, SXDF-NB1006-2, J0217-0208, and
J1211-0118, and from NIRSpec/MOS for the remaining galaxies. Open symbols represent local dwarf galaxies (Chen et al.
2023; Kumari et al. 2024; Chen et al. 2024). The [O iii] line ratios of COS-2987 lie outside the model grids, indicating that
they cannot be reproduced by a homogeneous ionized gas with a single set of electron temperature and density. ( _Right_ ) _A_ _V_
map derived from the H _α_ /H _β_ ratio, constructed within the 3 _σ_ regions of both H _α_ and H _β_ integrated intensity maps after
the Voronoi binning (Cappellari & Copin 2003; Cappellari 2009). The gray and cyan contours indicate the [O iii]5008 and [O
iii]4364 integrated intensity maps, respectively, at the 2 _σ_ and 3 _σ_ levels.



ing Mrk 71 at a distance of 3.4 Mpc (Chen et al. 2023),
Pox 186 at _z_ = 0 _._ 0041 (Kumari et al. 2024), and Haro 3
at _z_ = 0 _._ 0032 (Chen et al. 2024), where both the optical
and FIR [O iii] lines were observed with IFS.
In the left panel of Figure 3, the observed ratios for
COS-2987, COS-3018, and J0217-0218 lie outside the
_T_ e – _n_ e model grids, whereas the other high- _z_ galaxies
fall within the grid. Moreover, the high- _z_ data points
from the literature (black filled symbols) suggest _n_ e =
100 _−_ 500 cm _[−]_ [3] while the redshift dependence presented
in Figure 2 indicates typical densities of _n_ e _>_ 500 cm _[−]_ [3] .
Therefore, the lower- _n_ e values from the FIR-to-optical

[O iii] line ratios seem to be common in high- _z_ galaxies
(see also a recent similar conclusion by Harikane et al.
2025b).
We stress that the lower _n_ e values derived from the
FIR-to-optical [O iii] ratios are not limited to high- _z_
galaxies. As noted in § 1, observations of the nearby
massive star-forming region LMC-N11 reveal spatially
extended and bright [O iii]88 emission, which is inconsistent with the _n_ e values inferred from the optical [O ii],

[S ii], or [Cl iii] lines (Lebouteiller et al. 2012). These optical diagnostics have higher critical densities and therefore likely trace more compact regions than [O iii]88.



The results indicate that the [O iii] line ratios of COS2987 cannot be reproduced by a simple model of homogeneous ionized gas with uniform temperature and
density. In §5, we discuss two possible origins for this
discrepancy.


5. DISCUSSION


The FIR-to-optical [O iii] line ratio diagnostics presented in the left panel of Figure 3 demonstrate that
the observed values in COS-2987 cannot be explained
by a homogeneous ionized gas with a single set of electron density and temperature. This discrepancy highlights the need to explore more complex scenarios for
the ISM. In the following subsections, we discuss two
possible origins of this tension: (i) the presence of inhomogeneously distributed dust within the ISM (§ 5.1)
and (ii) a density-stratified ionized ISM structure (§ 5.2
and § 5.3).


5.1. _Inhomogeneously_ _Distributed_ _Dust_


One possibility to explain the observed [O iii] line ratios could be an inhomogeneous dust distribution. This
idea is suggested by ISM studies of local dwarf galax

8 Usui et al.



ies using rest-frame optical to FIR emission lines (e.g.,
Chen et al. 2023; Kumari et al. 2024; Chen et al. 2024).

Chen et al. (2024) analyzed both optical and FIR
emission lines of [O iii] (4364, 5008 [˚] A and 88 _µ_ m) and

[N ii] (5755, 6583 [˚] A and 122 _µ_ m) in Haro 3, to estimate
both electron temperatures and chemical abundance ratios. They found a significant discrepancy between the
N [+] /H [+] and N [+] /O [++] ratios derived from the optical
and FIR [N ii] lines, which they interpreted as evidence
for strong attenuation of optical lines due to inhomogeneously distributed dust.
In Chen et al. (2024), the dust extinction correction was applied using the Balmer decrement measured
from spatially integrated fluxes. However, if dust is distributed inhomogeneously within the galaxy, such integrated measurements would be biased toward regions
with less dust extinction, leading to an underestimation
of the true dust extinction.

If this hypothesis holds for COS-2987, the intrinsic [O iii] 5008 and 4364 fluxes would be underestimated. Equivalently, the intrinsic [O iii]88/5008 and

[O iii]4364/5008 ratio would be overestimated, potentially affecting the derived ISM physical properties. We
test this hypothesis for COS-2987 as follows.
First, we generate an _A_ _V_ map from the PSF-matched
H _α_ /H _β_ ratio map within the 3 _σ_ regions of both lineintensity maps (right panel of Figure 3). We apply
Voronoi pixel binning (Cappellari & Copin 2003; Cappellari 2009) to the integrated intensity maps of H _β_ and
H _α_ in order to optimize the signal-to-noise ratio in each
pixel. The observed [O iii]4364 and [O iii]5008 intensity maps are then corrected for dust extinction on a
pixel-by-pixel basis using the resulting _A_ _V_ map [10] . Outside the region where the _A_ V map is not reliably defined
(i.e., where either H _α_ or H _β_ is not detected above 3 _σ_ ),
we assume _A_ V = 0 for simplicity.
We measure the total dust-corrected [O iii]5008 and

[O iii]4364 fluxes in a similar manner to the observed total fluxes (Section 2.1). We perform isophotal photometry on both dust-corrected line intensity maps, where we
use the 2 _σ_ isophotal aperture defined in the [O iii]5008
map (the outermost gray contour in the right panel of
Figure 3). Then, we applied a 10% aperture correction
(see § 2.1) to both line flux values.


10 We note that the [O iii]4364 detection region (cyan contours in
Figure 3) is smaller than the _A_ V map coverage. The dust extinction correction is applied even to low-significance pixels in the [O
iii]4364 map. This could result in an underestimation of the dustcorrected [O iii]4364 flux, and thus of the [O iii]4364/5008 ratio.
Nevertheless, even if the ratio is underestimated, the true value
would shift upward along the vertical axis in Figure 3, which does
not alter our conclusion.



Finally, we estimate the pixel-by-pixel dust-corrected

[O iii]4364/5008 and [O iii]88/5008 ratios, represented
by a gray star in the left panel of Figure 3. As a result,
we find that the [O iii]4364/5008 and [O iii]88/5008 ratios change by factors of _∼_ 1 _._ 07 and _∼_ 0 _._ 82, respectively.
However, even after this correction, the integrated [O iii]
ratios of COS-2987 still cannot be explained by a homogeneous ionized gas with densities comparable to those
inferred from the [O ii] lines.
We therefore conclude that the integrated [O iii] ratios cannot be reproduced by an ISM characterized by
a single set of electron density and temperature, even
after accounting for the spatial structure of dust attenuation. This supports the view that inhomogeneously
distributed dust is not the primary cause of the observed
discrepancy in the [O iii] line ratios of COS-2987.


5.2. _Evidence_ _for_ _a_ _density-stratified_ _ionized_ _ISM_


A common assumption in deriving nebular physical
parameters is that all emission lines originate from a
homogeneous ionized gas with uniform electron density and temperature (see Kewley et al. 2019 and references therein). However, the critical density of [O iii]88
( _n_ e _,_ crit = 510 cm _[−]_ [3] ) is approximately 3–4 orders of magnitude lower than those of [O iii]4364 (3 _._ 0 _×_ 10 [6] cm _[−]_ [3] )
and [O iii]5008 (6 _._ 8 _×_ 10 [5] cm _[−]_ [3] ) (e.g., Osterbrock & Ferland 2006; Draine 2011). This large difference in critical
densities suggests that the [O iii]88, [O iii]5008, and

[O iii]4364 lines may originate from physically distinct
ionized gas conditions with different densities and tem
peratures.
We tested this possibility by examining the spatial
and kinematic distributions of the [O iii]5008 and [O
iii]88 lines. As shown in Figure B.2 (Appendix B), the
radial profiles of the two lines are consistent within uncertainties, indicating no significant spatial segregation
at the current ALMA resolution. Similarly, Figure C.1
in Appendix C shows that the spectral profiles of the
two lines are broadly consistent, although the [O iii]88
line appears marginally broader. These results do not
provide evidence for spatial or kinematic separation between the emitting regions at the given spatial and spectral resolutions of the current data. Moreover, we do not
find any velocity components that are detected in the

[O iii]88 line but absent in the [O iii]5008 line, which
would otherwise be expected if dust attenuation played
a major role. This further supports our conclusion in
§ 5.1 that inhomogeneously distributed dust is not the
primary cause of the observed discrepancy.
Motivated by the large differences in critical densities,
we explore the possibility that the ionized gas in COS2987 consists of multiple components with different elec

ISM Physical Properties of COS-2987030247 9


**Figure** **4.** ( _Top_ _left_ ) Same as the left panel of Figure 3, but shown with linear scales on both axes. The two squares correspond
to the two gas components: the dark red square indicates component 1, with ( _T_ _e_, _n_ _e_ ) = (26,000 K, 500 cm _[−]_ [3] ), and the orange
square indicates component 2, with ( _T_ _e_, _n_ _e_ ) = (8,000 K, 50 cm _[−]_ [3] ). The observed line ratios of COS-2987 (red star) can be
explained by an ISM composed of these two components, mixed at an appropriate volume ratio and represented by the line
connecting the two squares. ( _Top_ _right_ ) [O iii]88/5008 and [O iii]4364/5008 luminosity ratios as a function of volume ratio
_V_ 1 _/V_ 2 in our two-component model. The black curves show the predicted ratios from the model. The horizontal solid lines and
shaded regions indicate the observed ratios and their 1 _σ_ uncertainties, respectively. The observed values are reproduced when
_V_ 1 : _V_ 2 _∼_ 1 : 300 (vertical dashed lines). ( _Bottom_ ) Schematic illustration of our proposed two-component gas scenario. Hot and
dense H ii regions around young massive stars or clusters (component 1) are surrounded by relatively cool and diffuse H ii regions
(component 2). From the perspective of pressure balance, the component 1 gas is expected to be expanding. The [O iii]4364
and [O iii]88 emission arise primarily from the component 1 and 2 regions, respectively, while both components contribute to
the [O iii]5008 emission.



tron densities and temperatures (i.e., a density-stratified
ionized ISM). Although no significant spatial or kinematic offsets are observed, these findings do not rule
out the presence of physically distinct gas. While comprehensive models for ionized gas with multiple physical
conditions, such as `MULTIGRIS` (Lebouteiller & Ramambason 2022; Ramambason et al. 2022a), are available,
we adopt a simplified two-component toy model that
focuses on three emission lines from doubly ionized oxy


gen: [O iii]4364, [O iii]5008, and [O iii]88. A similar
analysis has been independently conducted for galaxies
at _z_ = 6 to 9 by Harikane et al. (2025b). By limiting
the number of free parameters, our aim is to identify the
key physical conditions responsible for the observed line

ratios.
In a two-component ionized gas model, the luminosity
of a given emission line ( _L_ line, where line refers to [O

10 Usui et al.



iii]4364, [O iii]5008 or [O iii]88) can be expressed as:



_L_ line = _ϵ_ line _,_ 1
� erg s _[−]_ [1] cm _[−]_ [3]



_V_ 1
�� cm [3]



+ _ϵ_ line _,_ 2
� � erg s _[−]_ [1] cm _[−]_ [3]



_V_ 2
�� cm [3]

(3)



_,_
�



We stress again that the specific combination of _T_ e, _n_ e,
and _V_ 1 _/V_ 2 parameters presented above is not a unique
solution. Nevertheless, our two-component model successfully reproduce both the observed [O iii]88/5008
and [O iii]4364/5008 ratios simultaneously, that cannot
be achieved by a commonly assumed homogeneous gas.
We also note that the observed [O ii]3727,3730 emission likely originates from a different ionization phase
not included in our current model. One possible explanation is the presence of a third component with lower
ionization and relatively high density, perhaps located
at the surface of H i gas clouds in the galaxy. Exploring
this additional phase is beyond the scope of the present
work, but it will be an important direction for future
modeling efforts.


5.3. _Interpretation_ _of_ _the_ _the_ _density-stratified_ _ionized_
_ISM_


The bottom panel of Figure 4 provides a schematic illustration of the density-stratified ionized ISM scenario.
In this framework, component 1 corresponds to compact, dense, and high-temperature ionized regions associated with young massive stars or stellar clusters.
Such regions are expected to be more common in high_z_ galaxies (Mingozzi et al. 2022; Topping et al. 2025).
The relatively cool and diffuse gas (component 2) is expected to be surrounding the component 1 regions because their volumes are different by a factor of _∼_ 300.
The diffuse and extended gas component may originate from hydrogen-ionizing photons (i.e., LyC photons) leaking from dense, high-temperature H ii regions
(component 1), resembling the so-called “picket-fence
model” (Heckman et al. 2011; Leitet et al. 2013). This
scenario is supported by observations of nearby massive star-forming regions: _AKARI_ observations of 30Doradus (Kawada et al. 2011) and _Herschel_ /PACS observations of LMC-N11 (Lebouteiller et al. 2012) revealed
spatially extended [O iii]88 emission beyond the regions
expected from the number of massive stars, likely due
to a clumpy, low-density medium that allows ionizing
photons to propagate over large scales. Similarly, modeling of the _Herschel_ Dwarf Galaxy Survey (Cormier
et al. 2015, 2019; Ramambason et al. 2022b) also requires such a high-ionization, low-density component to
reproduce the observed [O iii]88 flux. Such porous conditions would facilitate the leakage of LyC photons into
the surrounding medium, relevant to the study of cosmic reionization (e.g., Cormier et al. 2019; Ramambason
et al. 2022b; Hagimoto et al. 2025).
Indeed, the detection of Ly _α_ emission from COS-2987
at _z_ _∼_ 6 _._ 8 (Laporte et al. 2017), prior to the completion
of cosmic reionization, supports the presence of clear



where _ϵ_ line _,i_ and _V_ _i_ ( _i_ = 1 or 2) are the volume emissivity and the volume of each ionized gas component,
respectively. The emissivity _ϵ_ line _,i_ is given by:



_ϵ_ line _,i_ = Λ line _,i_ ( _n_ e _,i_ _, T_ e _,i_ )
� erg s _[−]_ [1] cm [3]



_n_ e _,i_
�� cm _[−]_ [3]



_n_ O ++ _,i_
�� cm _[−]_ [3]



_,_ (4)
�



where Λ line _,i_ is the cooling rate, and _n_ O ++ _,i_ is the number density of doubly ionized oxygen. We calculate
Λ line _,i_ for each line using `PyNeb` (Luridiana et al. 2015)
by assuming specific values of _n_ e _,i_ and _T_ e _,i_ . We assume
_n_ O ++ _,i_ = _n_ e _,i_ _×_ 10 _[−]_ [4], corresponding to O [++] _/_ H [+] = 10 _[−]_ [4]

(i.e., 12 + log(O [++] _/_ H [+] ) = 8). The aim of this analysis
is not to determine best-fit parameters, but rather to assess whether the observed [O iii] luminosity ratios can be
reproduced within the framework of a density-stratified
ionized ISM.

In principle, the line luminosity ratios predicted by
the two-component model can be expressed as a linear
combination of the ratios corresponding to the individual components. Accordingly, in the top left panel of
Figure 4, which is the same as Figure 3 but shown with
linear scales on both axes, hot and dense gas (component 1) and relatively cool and diffuse gas (component 2)
reside on the model grid representing a homogeneous
ionized medium. The composite (i.e., global) line ratios are therefore expected to lie along the straight line
connecting these two components.
We find that the observed [O iii] line ratios are well
reproduced by a model consisting of component 1 with
( _T_ e _,_ 1 _, n_ e _,_ 1 ) = (26 _,_ 000 K _,_ 500 cm _[−]_ [3] ) and component 2
with ( _T_ e _,_ 2 _, n_ e _,_ 2 ) = (8 _,_ 000 K _,_ 50 cm _[−]_ [3] ). The components 1 and 2 are marked by dark red and orange squares
in the top left panel of Figure 4. As shown in the figure,
the observed line ratios (indicated by the red star) can
be reproduced by a linear combination of the two components with an appropriate volume ratio. We also note
that other sets of physical conditions could reproduce
the observed line ratios, such as a higher _T_ e for component 1 and a higher _n_ e for component 2. The top right
panel of Figure 4 shows the predicted line ratios of the
two-component model as a function of the volume ratio
_V_ 1 _/V_ 2, with _T_ e _,_ 1, _n_ e _,_ 1, _T_ e _,_ 2, and _n_ e _,_ 2 held fixed. By comparing the model predictions with the observed values of

[O iii]88/5008 and [O iii]4364/5008, we derive a volume
ratio of _V_ 1 _/V_ 2 _∼_ 1 _/_ 300. The corresponding mass ratio
of the two gas components is _M_ 1 _/M_ 2 _∼_ 1 _/_ 30, where the
mass of each component is calculated as _M_ i = _n_ e _,_ i _V_ i .

ISM Physical Properties of COS-2987030247 11



sight lines that facilitate LyC escape. We refer readers to the estimate of the LyC photon escape fraction
for COS-2987 presented by Mawatari et al. (2025). Using the analytic prescription of Choustikov et al. (2024),
which incorporates parameters such as the O32 ratio
([O iii]4960,5008/[O ii]3727,3730) and H _β_ luminosity,
Mawatari et al. (2025) obtained a non-zero escape fraction of _f_ esc = 5 [+8] _−_ 5 [%.] [This] [estimate] [is] [consistent] [with]
the high [O iii]88 _µ_ m-to-[C ii]158 _µ_ m luminosity ratio
of _≈_ 6 in COS-2987 (Witstok et al. 2022). Based on
the empirical relation proposed by Ura et al. (2023) [11],
we infer _f_ esc _≈_ 4–14%. Taken together, the results
for COS-2987, along with similar trends in other high_z_ galaxies (Figure 3), may hint that high- _z_ ALMA [O
iii]88 _µ_ m emitters—with potentially porous ionized gas
structures—contributed to cosmic reionization.

To account for the extremely high electron temperature ( _T_ e _∼_ 20 _,_ 000 K) and the resulting strong [O
iii]4364 emission of component 1, we note that one speculative possibility is the presence of an extreme stellar population, such as very massive stars (VMSs with
_M_ ≳ 150 _, M_ _⊙_ ; Crowther et al. 2010; Vink et al. 2015).
Future follow-up observations in the rest-frame UV may
provide useful clues by examining spectral features that
could be indicative of VMSs, such as an enhanced N/O
ratio and a strong He ii 1640 equivalent width (Vink
2023; Upadhyaya et al. 2024; Senchyna et al. 2024).


6. CONCLUSIONS


In this Letter, we investigated the ionized interstellar medium (ISM) of the _z_ = 6 _._ 8 galaxy COS-2987 using JWST/NIRSpec IFS and ALMA spectroscopy. Our
main conclusions are summarized as follows:


(1) JWST/NIRSpec spectra revealed multiple restframe optical emission lines in COS-2987, including [O ii] _λλ_ 3727, 3730, [O iii] 4364, [O
iii] _λλ_ 4960, 5008, [O iii] 88 _µ_ m, as well as H _α_
and H _β_ (Figure 1; Table 1). Using only the
JWST/NIRSpec lines, we derived an electron density of _n_ e _∼_ 500 cm _[−]_ [3] from the [O ii] doublet,
consistent with the redshift evolution trend of _n_ e
reported in previous studies (Figure 2).


(2) From the combination of optical and FIR [O iii]
lines, we constructed a diagnostic diagram based
on the [O iii]88/[O iii]5008 and [O iii]4364/[O


11 Ura et al. (2023) combined two positive correlations: (i) between
the optical O32 ratio and _f_ esc, and (ii) between the optical O32
ratio and the [O iii]88 _µ_ m-to-[C ii]158 _µ_ m luminosity ratio, thereby
obtaining a correlation between the [O iii]88 _µ_ m-to-[C ii]158 _µ_ m
ratio and _f_ esc .



iii]5008 ratios. COS-2987 falls well outside the
grid predicted by homogeneous models computed
with `PyNeb` . Furthermore, a compilation of other
high- _z_ galaxies shows a similar behavior, in which
the _n_ e values inferred from the two combinations
of [O iii], [O iii]88/[O iii]5008 and [O iii]4364/[O
iii]5008, are systematically lower than those derived from optical diagnostics such as [O ii]. This
indicates that the discrepancy is likely a general
trend, and demonstrates that the assumption of
a uniform ionized gas with a single set of electron density and temperature could not be valid
in a large fraction of high- _z_ galaxies with strong

[O iii]88 (Figure 3).


(3) We examined whether inhomogeneously distributed dust could explain the high [O iii]88/[O
iii]5008 ratios. We conclude that a clumpy dust
distribution is not the primary cause of the discrepancy (see § 5.1 and the right panel of Figure 3).


(4) Instead, we showed that the observations can be
reproduced by invoking a density-stratified ionized ISM. A simple two-component ionized-gas toy
model with ( _T_ e _, n_ e ) _∼_ (26 _,_ 000 K _,_ 500 cm _[−]_ [3] ) and
(8 _,_ 000 K _,_ 50 cm _[−]_ [3] ) successfully reproduces the observed [O iii] ratios. We discussed a physical scenario for such stratification: porous ISM conditions in which LyC photons leak from dense regions into a low-density medium, akin to a “picketfence” geometry (§ 5.2 and § 5.3; Figure 4).


In summary, these results highlight the complex ionized gas structure of the star-forming galaxy COS-2987,
which may reflect its clumpy and extended morphology (Mawatari et al. 2025). Given that such clumpy,
multi-component stellar structures are not uncommon
among high-redshift galaxies (e.g., Sugahara et al. 2025;
Harikane et al. 2025a), a future systematic investigation into the ubiquity of density-stratified ionized ISM at
high redshift would be of great interest. A more detailed
modeling of the multi-component ISM in a larger sample of high- _z_ galaxies will be addressed in a forthcoming
paper (Y. Sugahara et al., in preparation). Given their
high critical densities, rest-frame UV emission lines such
as O iii] and C iii] offer a promising avenue for probing density stratification in high- _z_ galaxies. In addition, high-angular-resolution observations with ALMA
are essential for obtaining spatially resolved measurements of electron temperature, electron density, and the

[O iii]88/5008 ratio, thereby enabling constraints on the
structure and physical conditions of density-stratified
ionized ISM.

12 Usui et al.



ACKNOWLEDGMENTS


e are grateful to an anonymous referee for valuable comments that have greatly improved the paper. We thank Masami Ouchi, Yoshiaki Ono, and
Kimihiko Nakajima for providing us with valuable
comments on the presentations of the first author.
We also acknowledge Joris Witstok, Fengwu Sun,
Tohru Nagao, Hide Yajima, Hajime Fukushima, Nario
Kuno, Shunsuke Honda, Asahi Hamada, Yuuki Takagishi, and Yuzuru Terui for insightful discussion.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2018.1.00429.S. ALMA is a partnership of ESO (representing its member states),
NSF (USA), and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work
has made use of data from the European Space
Agency (ESA) mission _Gaia_ [(https://www.cosmos.esa.](https://www.cosmos.esa.int/gaia)
[int/gaia),](https://www.cosmos.esa.int/gaia) processed by the _Gaia_ Data Processing and
Analysis Consortium (DPAC, [https://www.cosmos.esa.](https://www.cosmos.esa.int/web/gaia/dpac/consortium)
[int/web/gaia/dpac/consortium).Funding](https://www.cosmos.esa.int/web/gaia/dpac/consortium) for the DPAC
has been provided by national institutions, in particular the institutions participating in the _Gaia_ Multilateral Agreement. The _Gaia_ data are retrieved
from the JVO portal [(http://jvo.nao.ac.jp/portal)](http://jvo.nao.ac.jp/portal) operated by the NAOJ. This research has made use of
NASA’s Astrophysics Data System. T.H. was supported by Leading Initiative for Excellent Young Researchers, MEXT, Japan (HJH02007) and by JSPS
KAKENHI grant Nos. 22H01258, 23K22529, and
25K00020. K.M. acknowledges financial support from
JSPS through KAKENHI grant No. 20K14516. K.M.
and A.K.I are supported by JSPS KAKENHI grant No.
23H00131. J.A.-M., L.C. and S.A. acknowledge support by grants PIB2021-127718NB-100 from the Spanish Ministry of Science and Innovation/State Agency
of Research MCIN/AEI/10.13039/501100011033 and
by “ERDF A way of making Europe”. J.A.M. and C. B-P acknowledge support by grant
PID2024-158856NA-I00 from the Spanish Ministry of
Science and Innovation/State Agency of Research
MCIN/AEI/10.13039/501100011033 and by “ERDF A
way of making Europe”. Y.N. acknowledges funding from JSPS KAKENHI Grant Number 23KJ0728.
A.C.G. acknowledges support by JWST contract
B0215/JWST-GO-02926. Y.W.R. was supported by
JSPS KAKENHI Grant Number 23KJ2052. Y.F.

acknowledges supports from JSPS KAKENHI Grant



Numbers JP22K21349 and JP23K13149. M.H. was

supported by JSPS KAKENHI Grant No. 22KJ1598.
The project that gave rise to these results received the support of a fellowship from the “la
Caixa” Foundation (ID 100010434). The fellowship code is LCF/BQ/PR24/12050015. L.C. acknowledges support from grants PID2022-139567NBI00 and PIB2021-127718NB-I00 funded by the Spanish Ministry of Science and Innovation/State Agency
of Research MCIN/AEI/10.13039/501100011033 and
by “ERDF A way of making Europe”. D.C.
is supported by research grant PID2021-122603NBC21 funded by the Ministerio de Ciencia, Innovaci´on y Universidades (MI-CIU/FEDER) and
the research grant CNS2024-154550 funded by MICIU/AEI/10.13039/501100011033. C.B.P. acknowledges the support of the Consejer´ıa de Educaci´on,
Ciencia y Universidades de la Comunidad de Madrid
through grants No. PEJ-2021-AI/TIC-21517 and PIPF2023/TEC29505.


_Software:_ scipy, astropy, PyNeb, photutils

ISM Physical Properties of COS-2987030247 13


APPENDIX


A. POINT SPREAD FUNCTION OF THE NIRSPEC IFU DATA CUBE


To ensure that the line fluxes are measured from the same spatial region, we used a point spread function (PSF)matched data cube, as described in Mawatari et al. (2025). Here, we briefly summarize the procedure used to create
the PSF-matched data cube. To obtain an empirical PSF for the data cube, we analyzed observations of the A3V
star 1808347 (2MASS J18083474+6927286) taken during the commissioning program (PID 1128; PI: N. L¨utzgendorf;
B¨oker et al. 2023), using the same grating/filter combination (G395H/F290LP) as for COS-2987. The data reduction
for the standard star was performed with the same JWST pipeline version and CRDS context as for COS-2987.
From the data cube of the A3V star, we generated PSF images at the wavelengths corresponding to the emission lines
detected in COS-2987. We then created convolution kernels to homogenize all PSFs to match the PSF at 5 _._ 125 _µ_ m,
corresponding to the observed wavelength of H _α_ in COS-2987, which has the largest FWHM of 0 _[′′]_ _._ 21 among the
detected lines.


B. RADIAL PROFILES OF [O iii]5008 AND [O iii]88


We examined the spatial distributions of the [O iii]5008 and [O iii]88 emission lines, as shown in Figures B.1 and B.2.
In Figure B.1, we present the integrated intensity maps of both lines, where the [O iii]5008 map has been convolved
to match the ALMA beam size (0 _[′′]_ _._ 8 _×_ 0 _[′′]_ _._ 6). To quantitatively assess the spatial difference, we compare the radial
profiles of [O iii]5008 and [O iii]88 in Figure B.2. The blue and red lines with shaded regions represent the radial
profiles of [O iii]5008 and [O iii]88, respectively. The two emission lines exhibit consistent radial distributions within
the uncertainties, indicating that there is no significant evidence of spatial separation between the two lines at the
current ALMA resolution.

We note, however, that this result does not exclude the possibility that future high-angular-resolution observations
could reveal subtle morphological differences between the [O iii]5008 and [O iii]88 emissions.


**Figure** **B.1.** ( _Left_ ) Integrated intensity map of the NIRSpec [O iii]5008 emission, after convolution to match the ALMA beam
size (0 _[′′]_ _._ 80 _×_ 0 _[′′]_ _._ 61). Red contours show the _±_ 2 _[n]_ _σ_ significance levels ( _n_ = 1 _,_ 2 _,_ 3 _, . . ._ ), where _σ_ = 1 _._ 16 _×_ 10 _[−]_ [20] erg s _[−]_ [1] cm _[−]_ [2] pixel _[−]_ [1] .
The orange circle at the bottom left indicates the FWHM of 0 _[′′]_ _._ 21 at the observed wavelength of H _α_ (5 _._ 125 _µ_ m). ( _Right_ )
Integrated intensity map of the ALMA [O iii]88 emission. White contours show the _±_ (2 _,_ 4 _,_ 6) _σ_ significance levels, where
_σ_ = 82 _._ 6 mJy beam _[−]_ [1] km s _[−]_ [1] . Positive and negative contours are shown by the white solid and dashed lines, respectively. The
white ellipse at the bottom left represents the synthesized beam size of 0 _[′′]_ _._ 80 _×_ 0 _[′′]_ _._ 61.

14 Usui et al.


**Figure** **B.2.** Radial profiles of the [O iii]5008 and [O iii]88 emission lines. The blue and red lines represent the profiles of [O
iii]5008 and [O iii]88, respectively, with shaded regions indicating their corresponding uncertainties.


C. LINE PROFILES OF [O iii]5008 AND [O iii]88


**Figure** **C.1.** Comparison of the velocity profiles of the [O iii]5008 and [O iii]88 emission lines. The blue and red lines represent
the profiles of [O iii]5008 and [O iii]88, respectively, normalized to their peak intensities.


We investigated potential differences in the line profiles between the [O iii]5008 and [O iii]88 emissions. Figure C.1
shows the velocity profiles of [O iii]5008 and [O iii]88, represented by the blue and red lines, respectively. Fitting each
line with a single Gaussian profile and correcting for instrumental broadening, we obtain FWHM 5008 = 146 _±_ 2 km s _[−]_ [1]

and FWHM 88 = 239 _±_ 45 km s _[−]_ [1] . These values are consistent within _∼_ 2 _σ_, although the [O iii]88 line appears
marginally broader.


REFERENCES



Abdurro’uf, Larson, R. L., Coe, D., et al. 2024, ApJ, 973,

47, doi: [10.3847/1538-4357/ad6001](http://doi.org/10.3847/1538-4357/ad6001)
´Alvarez-M´arquez, J., Crespo G´omez, A., Colina, L., et al.

2025, A&A, 695, A250,

doi: [10.1051/0004-6361/202451731](http://doi.org/10.1051/0004-6361/202451731)

Arribas, S., Perna, M., Rodr´ıguez Del Pino, B., et al. 2024,
A&A, 688, A146, doi: [10.1051/0004-6361/202348824](http://doi.org/10.1051/0004-6361/202348824)

Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009,

ARA&A, 47, 481,

doi: [10.1146/annurev.astro.46.060407.145222](http://doi.org/10.1146/annurev.astro.46.060407.145222)



Bakx, T., & Conway, J. 2024, Compilation of Technical


Papers on ALMA Receivers, ALMA Memo Series, 627,


2024, doi: [10.48550/arXiv.2409.02164](http://doi.org/10.48550/arXiv.2409.02164)


Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020,


MNRAS, 493, 4294, doi: [10.1093/mnras/staa509](http://doi.org/10.1093/mnras/staa509)


B¨oker, T., Arribas, S., L¨utzgendorf, N., et al. 2022, A&A,


661, A82, doi: [10.1051/0004-6361/202142589](http://doi.org/10.1051/0004-6361/202142589)


B¨oker, T., Beck, T. L., Birkmann, S. M., et al. 2023, PASP,


135, 038001, doi: [10.1088/1538-3873/acb846](http://doi.org/10.1088/1538-3873/acb846)

ISM Physical Properties of COS-2987030247 15



Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2024,

JWST Calibration Pipeline, 1.14.0, Zenodo,

doi: [10.5281/zenodo.6984365](http://doi.org/10.5281/zenodo.6984365)


Campbell, A., Terlevich, R., & Melnick, J. 1986, MNRAS,

223, 811, doi: [10.1093/mnras/223.4.811](http://doi.org/10.1093/mnras/223.4.811)


Cappellari, M. 2009, arXiv e-prints, arXiv:0912.1303,

doi: [10.48550/arXiv.0912.1303](http://doi.org/10.48550/arXiv.0912.1303)


Cappellari, M., & Copin, Y. 2003, MNRAS, 342, 345,

doi: [10.1046/j.1365-8711.2003.06541.x](http://doi.org/10.1046/j.1365-8711.2003.06541.x)


CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP,

134, 114501, doi: [10.1088/1538-3873/ac9642](http://doi.org/10.1088/1538-3873/ac9642)


Chen, Y., Jones, T., Sanders, R., et al. 2023, Nature

Astronomy, 7, 771, doi: [10.1038/s41550-023-01953-7](http://doi.org/10.1038/s41550-023-01953-7)


Chen, Y., Jones, T., Sanders, R. L., et al. 2024, arXiv

e-prints, arXiv:2405.18476,

doi: [10.48550/arXiv.2405.18476](http://doi.org/10.48550/arXiv.2405.18476)


Choustikov, N., Katz, H., Saxena, A., et al. 2024, MNRAS,

529, 3751, doi: [10.1093/mnras/stae776](http://doi.org/10.1093/mnras/stae776)


Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015,

A&A, 578, A53, doi: [10.1051/0004-6361/201425207](http://doi.org/10.1051/0004-6361/201425207)


Cormier, D., Abel, N. P., Hony, S., et al. 2019, A&A, 626,

A23, doi: [10.1051/0004-6361/201834457](http://doi.org/10.1051/0004-6361/201834457)


Crowther, P. A., Schnurr, O., Hirschi, R., et al. 2010,

MNRAS, 408, 731, doi: [10.1111/j.1365-2966.2010.17167.x](http://doi.org/10.1111/j.1365-2966.2010.17167.x)


Curti, M., Maiolino, R., Curtis-Lake, E., et al. 2024, A&A,

684, A75, doi: [10.1051/0004-6361/202346698](http://doi.org/10.1051/0004-6361/202346698)


Davies, R. L., F¨orster Schreiber, N. M., Genzel, R., et al.

2021, ApJ, 909, 78, doi: [10.3847/1538-4357/abd551](http://doi.org/10.3847/1538-4357/abd551)


Dinerstein, H. L., Lester, D. F., & Werner, M. W. 1985,

ApJ, 291, 561, doi: [10.1086/163096](http://doi.org/10.1086/163096)


Draine, B. T. 2011, Physics of the Interstellar and

Intergalactic Medium


Fujimoto, S., Ouchi, M., Nakajima, K., et al. 2024, ApJ,

964, 146, doi: [10.3847/1538-4357/ad235c](http://doi.org/10.3847/1538-4357/ad235c)


Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023,

PASP, 135, 068001, doi: [10.1088/1538-3873/acd1b5](http://doi.org/10.1088/1538-3873/acd1b5)


Gordon, K. D., Clayton, G. C., Misselt, K. A., Landolt,

A. U., & Wolff, M. J. 2003, ApJ, 594, 279,

doi: [10.1086/376774](http://doi.org/10.1086/376774)


Hagimoto, M., Tamura, Y., Inoue, A. K., et al. 2025, arXiv

e-prints, arXiv:2506.20734,

doi: [10.48550/arXiv.2506.20734](http://doi.org/10.48550/arXiv.2506.20734)


Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ,

896, 93, doi: [10.3847/1538-4357/ab94bd](http://doi.org/10.3847/1538-4357/ab94bd)


Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2025a, ApJ,

980, 138, doi: [10.3847/1538-4357/ad9b2c](http://doi.org/10.3847/1538-4357/ad9b2c)


Harikane, Y., Sanders, R. L., Ellis, R., et al. 2025b, arXiv

e-prints, arXiv:2505.09186,

doi: [10.48550/arXiv.2505.09186](http://doi.org/10.48550/arXiv.2505.09186)



Harshan, A., Tripodi, R., Martis, N. S., et al. 2024, ApJL,

977, L36, doi: [10.3847/2041-8213/ad9741](http://doi.org/10.3847/2041-8213/ad9741)


Hashimoto, T., Laporte, N., Mawatari, K., et al. 2018,

Nature, 557, 392, doi: [10.1038/s41586-018-0117-z](http://doi.org/10.1038/s41586-018-0117-z)

Hashimoto, T., Alvarez-M´arquez, [´] J., Fudamoto, Y., et al.

2023, ApJL, 955, L2, doi: [10.3847/2041-8213/acf57c](http://doi.org/10.3847/2041-8213/acf57c)


Heckman, T. M., Borthakur, S., Overzier, R., et al. 2011,

ApJ, 730, 5, doi: [10.1088/0004-637X/730/1/5](http://doi.org/10.1088/0004-637X/730/1/5)


Inoue, A. K., Tamura, Y., Matsuo, H., et al. 2016, Science,

352, 1559, doi: [10.1126/science.aaf0714](http://doi.org/10.1126/science.aaf0714)


Isobe, Y., Ouchi, M., Nakajima, K., et al. 2023, ApJ, 956,

139, doi: [10.3847/1538-4357/acf376](http://doi.org/10.3847/1538-4357/acf376)

Ji, X., Ubler, [¨] H., Maiolino, R., et al. 2024, MNRAS, 535,

881, doi: [10.1093/mnras/stae2375](http://doi.org/10.1093/mnras/stae2375)


Jones, T., Sanders, R., Roberts-Borsani, G., et al. 2020,

ApJ, 903, 150, doi: [10.3847/1538-4357/abb943](http://doi.org/10.3847/1538-4357/abb943)


Kawada, M., Takahashi, A., Yasuda, A., et al. 2011, PASJ,

63, 903, doi: [10.1093/pasj/63.4.903](http://doi.org/10.1093/pasj/63.4.903)


Kewley, L. J., Nicholls, D. C., Sutherland, R., et al. 2019,

ApJ, 880, 16, doi: [10.3847/1538-4357/ab16ed](http://doi.org/10.3847/1538-4357/ab16ed)


Killi, M., Watson, D., Fujimoto, S., et al. 2023, MNRAS,

521, 2526, doi: [10.1093/mnras/stad687](http://doi.org/10.1093/mnras/stad687)


Kumari, N., Smit, R., Leitherer, C., et al. 2024, MNRAS,

529, 781, doi: [10.1093/mnras/stae252](http://doi.org/10.1093/mnras/stae252)


Laporte, N., Nakajima, K., Ellis, R. S., et al. 2017, ApJ,

851, 40, doi: [10.3847/1538-4357/aa96a8](http://doi.org/10.3847/1538-4357/aa96a8)


Laseter, I. H., Maseda, M. V., Curti, M., et al. 2024, A&A,

681, A70, doi: [10.1051/0004-6361/202347133](http://doi.org/10.1051/0004-6361/202347133)


Lebouteiller, V., & Ramambason, L. 2022, A&A, 667, A34,

doi: [10.1051/0004-6361/202243865](http://doi.org/10.1051/0004-6361/202243865)


Lebouteiller, V., Cormier, D., Madden, S. C., et al. 2012,

A&A, 548, A91, doi: [10.1051/0004-6361/201218859](http://doi.org/10.1051/0004-6361/201218859)


Leitet, E., Bergvall, N., Hayes, M., Linn´e, S., & Zackrisson,

E. 2013, A&A, 553, A106,

doi: [10.1051/0004-6361/201118370](http://doi.org/10.1051/0004-6361/201118370)


Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A,

573, A42, doi: [10.1051/0004-6361/201323152](http://doi.org/10.1051/0004-6361/201323152)


Marconcini, C., D’Eugenio, F., Maiolino, R., et al. 2024,

arXiv e-prints, arXiv:2407.08616,

doi: [10.48550/arXiv.2407.08616](http://doi.org/10.48550/arXiv.2407.08616)


Marshall, M. A., Perna, M., Willott, C. J., et al. 2023,

A&A, 678, A191, doi: [10.1051/0004-6361/202346113](http://doi.org/10.1051/0004-6361/202346113)


Mawatari, K., Costantin, L., Usui, M., et al. 2025, arXiv

e-prints, arXiv:2507.02053,

doi: [10.48550/arXiv.2507.02053](http://doi.org/10.48550/arXiv.2507.02053)


Mingozzi, M., James, B. L., Arellano-C´ordova, K. Z., et al.

2022, ApJ, 939, 110, doi: [10.3847/1538-4357/ac952c](http://doi.org/10.3847/1538-4357/ac952c)


Morishita, T., Stiavelli, M., Grillo, C., et al. 2024, ApJ,

971, 43, doi: [10.3847/1538-4357/ad5290](http://doi.org/10.3847/1538-4357/ad5290)

16 Usui et al.



Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, ApJS, 269,


33, doi: [10.3847/1538-4365/acd556](http://doi.org/10.3847/1538-4365/acd556)


Nakazato, Y., Yoshida, N., & Ceverino, D. 2023, ApJ, 953,


140, doi: [10.3847/1538-4357/ace25a](http://doi.org/10.3847/1538-4357/ace25a)


Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of


gaseous nebulae and active galactic nuclei


Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679,


A89, doi: [10.1051/0004-6361/202346649](http://doi.org/10.1051/0004-6361/202346649)


Posses, A. C., Aravena, M., Gonz´alez-L´opez, J., et al. 2023,


A&A, 669, A46, doi: [10.1051/0004-6361/202243399](http://doi.org/10.1051/0004-6361/202243399)


Ramambason, L., Lebouteiller, V., Bik, A., et al. 2022a,


A&A, 667, A35, doi: [10.1051/0004-6361/202243866](http://doi.org/10.1051/0004-6361/202243866)


—. 2022b, A&A, 667, A35,


doi: [10.1051/0004-6361/202243866](http://doi.org/10.1051/0004-6361/202243866)


Ren, Y. W., Fudamoto, Y., Inoue, A. K., et al. 2023, ApJ,


945, 69, doi: [10.3847/1538-4357/acb8ab](http://doi.org/10.3847/1538-4357/acb8ab)


Rhoads, J. E., Wold, I. G. B., Harish, S., et al. 2023, ApJL,


942, L14, doi: [10.3847/2041-8213/acaaaf](http://doi.org/10.3847/2041-8213/acaaaf)


Rigby, J. R., Vieira, J. D., Phadke, K. A., et al. 2025, ApJ,


978, 108, doi: [10.3847/1538-4357/ad7501](http://doi.org/10.3847/1538-4357/ad7501)


Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy,


N. A., & Brammer, G. B. 2024, ApJ, 962, 24,


doi: [10.3847/1538-4357/ad15fc](http://doi.org/10.3847/1538-4357/ad15fc)


Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2016, ApJ,


816, 23, doi: [10.3847/0004-637X/816/1/23](http://doi.org/10.3847/0004-637X/816/1/23)


Schaerer, D., Marques-Chaves, R., Barrufet, L., et al. 2022,


A&A, 665, L4, doi: [10.1051/0004-6361/202244556](http://doi.org/10.1051/0004-6361/202244556)


Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, ApJ,


500, 525, doi: [10.1086/305772](http://doi.org/10.1086/305772)


Scholtz, J., Curti, M., D’Eugenio, F., et al. 2025, MNRAS,


539, 2463, doi: [10.1093/mnras/staf518](http://doi.org/10.1093/mnras/staf518)


Sekimoto, Y., Iizuko, Y., Satou, N., et al. 2008, in


Ninteenth International Symposium on Space Terahertz


Technology, ed. W. Wild, 253–257


Senchyna, P., Plat, A., Stark, D. P., et al. 2024, ApJ, 966,


92, doi: [10.3847/1538-4357/ad235e](http://doi.org/10.3847/1538-4357/ad235e)



Smit, R., Bouwens, R. J., Franx, M., et al. 2015, ApJ, 801,

122, doi: [10.1088/0004-637X/801/2/122](http://doi.org/10.1088/0004-637X/801/2/122)

Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature,

553, 178, doi: [10.1038/nature24631](http://doi.org/10.1038/nature24631)

Stasi´nska, G. 1982, A&AS, 48, 299

Stiavelli, M., Morishita, T., Chiaberge, M., et al. 2023,
ApJL, 957, L18, doi: [10.3847/2041-8213/ad0159](http://doi.org/10.3847/2041-8213/ad0159)
Sugahara, Y., Alvarez-M´arquez, [´] J., Hashimoto, T., et al.
2025, ApJ, 981, 135, doi: [10.3847/1538-4357/adb02a](http://doi.org/10.3847/1538-4357/adb02a)

Tamura, Y., C. Bakx, T. J. L., Inoue, A. K., et al. 2023,

ApJ, 952, 9, doi: [10.3847/1538-4357/acd637](http://doi.org/10.3847/1538-4357/acd637)

Tokuoka, T., Inoue, A. K., Hashimoto, T., et al. 2022, The

Astrophysical Journal Letters, 933, L19,
doi: [10.3847/2041-8213/ac7447](http://doi.org/10.3847/2041-8213/ac7447)


Topping, M. W., Stark, D. P., Senchyna, P., et al. 2025,
ApJ, 980, 225, doi: [10.3847/1538-4357/ada95c](http://doi.org/10.3847/1538-4357/ada95c)
¨Ubler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, A&A,

677, A145, doi: [10.1051/0004-6361/202346137](http://doi.org/10.1051/0004-6361/202346137)

Upadhyaya, A., Marques-Chaves, R., Schaerer, D., et al.

2024, A&A, 686, A185,

doi: [10.1051/0004-6361/202449184](http://doi.org/10.1051/0004-6361/202449184)

Ura, R., Hashimoto, T., Inoue, A. K., et al. 2023, ApJ, 948,

3, doi: [10.3847/1538-4357/acc530](http://doi.org/10.3847/1538-4357/acc530)

Vink, J. S. 2023, A&A, 679, L9,

doi: [10.1051/0004-6361/202347827](http://doi.org/10.1051/0004-6361/202347827)

Vink, J. S., Heger, A., Krumholz, M. R., et al. 2015,

Highlights of Astronomy, 16, 51,
doi: [10.1017/S1743921314004657](http://doi.org/10.1017/S1743921314004657)

Welch, B., Olivier, G. M., Hutchison, T. A., et al. 2024,

ApJ, 975, 196, doi: [10.3847/1538-4357/ad79ec](http://doi.org/10.3847/1538-4357/ad79ec)

Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS,

515, 1751, doi: [10.1093/mnras/stac1905](http://doi.org/10.1093/mnras/stac1905)

Wootten, A., & Thompson, A. R. 2009, Proceedings of the
IEEE, 97, 1463, doi: [10.1109/JPROC.2009.2017105](http://doi.org/10.1109/JPROC.2009.2017105)

Yang, S., & Lidz, A. 2020, MNRAS, 499, 3417,
doi: [10.1093/mnras/staa3000](http://doi.org/10.1093/mnras/staa3000)

Zavala, J. A., Castellano, M., Akins, H. B., et al. 2025,

Nature Astronomy, 9, 155,
doi: [10.1038/s41550-024-02397-3](http://doi.org/10.1038/s41550-024-02397-3)


</paper>

## Items to check

```json
[
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Combining JWST NIRSpec IFS and ALMA avoids the slit-loss and position-angle uncertainties of NIRSpec MOS and provides four [O III] transitions from the same ion with vastly different critical densities, enabling nebular diagnostics independent of abundance ratio assumptions.",
  "failed_quote": "To accurately characterize the global properties of galaxies, a combination of NIRSpec integral field spectroscopy (IFS; B¨oker et al. 2022) and ALMA observations is a crucial next step (see e.g., Scholtz et al. 2025; Zavala et al. 2025)."
 }
]
```
