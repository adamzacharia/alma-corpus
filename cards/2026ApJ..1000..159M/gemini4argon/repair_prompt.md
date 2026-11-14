# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1000..159M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version February 3, 2025
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Low** **dust** **mass** **and** **high** **star-formation** **efficiency** **at** _z_ _>_ 12 **from** **deep** **ALMA** **observations**


Ikki [Mitsuhashi,](http://orcid.org/0000-0001-7300-9450) [1, 2, 3] Jorge [A.](http://orcid.org/0000-0002-7051-1100) Zavala, [3] Tom J.L.C. Bakx, [4] Akio K. Inoue, [2, 5] Marco Castellano, [6]

Antonello Calabro, [6] Caitlin M. Casey, [7] Maximilien Franco, [7] Bunyo Hatsukade, [3, 8, 9] Nimish P. Hathi, [10]

Ryota Ikeda, [3, 11] Anton M. [Koekemoer,](http://orcid.org/0000-0002-6610-2048) [10] Jeyhan Kartaltepe, [12] Kirsten K. Knudsen, [13] Paola Santini, [6]

Toshiki Saito, [14] Elena Terlevich, [15, 16, 17] and Roberto Terlevich [15, 16, 17]


1 _Department_ _for_ _Astrophysical_ _&_ _Planetary_ _Science,_ _University_ _of_ _Colorado,_ _Boulder,_ _CO_ _80309,_ _USA_
2 _Waseda_ _Research_ _Institute_ _for_ _Science_ _and_ _Engineering,_ _Faculty_ _of_ _Science_ _and_ _Engineering,_ _Waseda_ _University,_ _3-4-1_ _Okubo,_ _Shinjuku,_
_Tokyo_ _169-8555,_ _Japan_
3 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
4 _Department_ _of_ _Space,_ _Earth_ _and_ _Environment,_ _Chalmers_ _University_ _of_ _Technology,_ _Gothenburg,_ _Sweden_
5 _Department_ _of_ _Physics,_ _School_ _of_ _Advanced_ _Science_ _and_ _Engineering,_ _Faculty_ _of_ _Science_ _and_ _Engineering,_ _Waseda_ _University,_ _3-4-1,_
_Okubo,_ _Shinjuku,_ _Tokyo_ _169-8555,_ _Japan_
6 _INAF_ _-_ _Osservatorio_ _Astronomico_ _di_ _Roma,_ _via_ _di_ _Frascati_ _33,_ _00078_ _Monte_ _Porzio_ _Catone,_ _Italy_
7 _Department_ _of_ _Astronomy,_ _The_ _University_ _of_ _Texas_ _at_ _Austin,_ _2515_ _Speedway_ _Boulevard_ _Stop_ _C1400,_ _Austin,_ _TX_ _78712,_ _USA_
8 _Graduate_ _Institute_ _for_ _Advanced_ _Studies,_ _SOKENDAI,_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
9 _Institute_ _of_ _Astronomy,_ _Graduate_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-0015,_ _Japan_
10 _Space_ _Telescope_ _Science_ _Institute,_ _3700_ _San_ _Martin_ _Drive,_ _Baltimore,_ _MD_ _21218,_ _USA_
11 _Department_ _of_ _Astronomy,_ _School_ _of_ _Science,_ _SOKENDAI_ _(The_ _Graduate_ _University_ _for_ _Advanced_ _Studies),_ _2-21-1_ _Osawa,_ _Mitaka,_
_Tokyo_ _181-8588,_ _Japan_
12 _Laboratory_ _for_ _Multiwavelength_ _Astrophysics,_ _School_ _of_ _Physics_ _and_ _Astronomy,_ _Rochester_ _Institute_ _of_ _Technology,_ _84_ _Lomb_ _Memorial_
_Drive,_ _Rochester,_ _NY_ _14623,_ _USA_
13 _Department_ _of_ _Earth_ _and_ _Space_ _Sciences,_ _Chalmers_ _University_ _of_ _Technology,_ _Onsala_ _Space_ _Observatory,_ _SE-43992_ _Onsala,_ _Sweden_
14 _Faculty_ _of_ _Global_ _Interdisciplinary_ _Science_ _and_ _Innovation,_ _Shizuoka_ _University,_ _836_ _Ohya,_ _Suruga-ku,_ _Shizuoka_ _422-8529,_ _Japan_
15 _Instituto_ _Nacional_ _de_ _Astrof´ısica,_ _´Optica_ _y_ _Electr´onica,Tonantzintla,_ _Puebla,_ _M´exico_
16 _Institute_ _of_ _Astronomy,_ _University_ _of_ _Cambridge,_ _Cambridge,_ _CB3_ _0HA,_ _UK_
17 _Facultad_ _de_ _Astronom´ıa_ _y_ _Geof´ısica,_ _Universidad_ _de_ _La_ _Plata,_ _La_ _Plata,_ _Argentina_


(Received 20, Dec, 2024; Accepted TBD)


Submitted to ApJ


ABSTRACT

We investigate the dust mass build-up and star formation efficiency of two galaxies at _z_ _>_ 12, GHZ2
and GS-z14-0, by combining ALMA and JWST observations with an analytical model that assumes
dust at thermal equilibrium. We obtained 3 _σ_ constraints on dust mass of log _M_ dust _/M_ _⊙_ _<_ 5 _._ 0 and
_<_ 5 _._ 3, respectively. These constraints are in tension with a high dust condensation efficiency in stellar
ejecta but are consistent with models with a short metal accretion timescale at _z_ _>_ 12. Given the young
stellar ages of these galaxies ( _t_ age _∼_ 10 Myrs), dust grain growth via accretion may still be ineffective
at this stage, though it likely works efficiently to produce significant dust in galaxies at _z_ _∼_ 7. The
star formation efficiencies, defined as the SFR divided by molecular gas mass, reach _∼_ 10 Gyr _[−]_ [1] in a
10 Myr timescale, aligning with the expected redshift evolution of ‘starburst’ galaxies with efficiencies
that are _∼_ 0 _._ 5–1 dex higher than those in main-sequence galaxies. This starburst phase seems to be
common in UV-bright galaxies at _z_ _>_ 12 and is likely associated with the unique conditions of the
early phases of galaxy formation, such as bursty star formation and/or negligible feedback from superEddington accretion. Direct observations of molecular gas tracers like [C ii] will be crucial to further
understanding the nature of bright galaxies at _z_ _>_ 12.


_Keywords:_ galaxies: evolution     - galaxies: formation     - galaxies: high-redshift


Corresponding author: Ikki Mitsuhashi [ikki0913astr@gmail.com](mailto: ikki0913astr@gmail.com)

2 Mitsuhashi, Zavala, Bakx et al.



1. INTRODUCTION


Dust and gas are fundamental components of the interstellar medium (ISM). Gas is the primary fuel for star
formation and dust plays a key role in rapidly cooling
this component to facilitate the collapse of gas clouds
into stars. Cosmic dust originates from stellar phenomena, such as the ejecta of asymptotic giant branch
(AGB) stars and rapidly cooling SN ejecta (Dwek &
Scalo 1980; Todini & Ferrara 2001; Nozawa et al. 2007).
The dust produced by stellar activity (“stellar dust”)
grows in the dense ISM through metal accretion and
condensation into dust grains (“ISM dust”, e.g., Draine
1990, 2009; Inoue 2011; Zhukovska 2014). Therefore,
the dust content within galaxies is directly connected
to the star formation history and the metal enrichment

process.
The formation and growth of interstellar dust have
been studied in relation to other galactic properties,
such as the stellar mass, gas mass, and metallicity
(Ciesla et al. 2014; Santini et al. 2014; da Cunha et al.
2015; Mancini et al. 2015). The dust-to-gas mass ratio (D/G) represents the fraction of dust relative to the
ISM, serving as a powerful tool for investigating dust
growth. In the local Universe, D/G has been intensively investigated over the past decades (e.g., Koornneef 1982; Issa et al. 1990; Hirashita et al. 2002; Bendo
et al. 2010; Magrini et al. 2011) and found to be correlated with metallicity across a large dynamical range
(Lisenfeld & Ferrara 1998; Draine et al. 2007; Leroy et al.
2011; R´emy-Ruyer et al. 2014), which may reflect both
chemical evolution and dust grain growth (Dwek 1998;
Galliano et al. 2008; Asano et al. 2013; Popping et al.
2017; Graziani et al. 2020). Constraining D/G at high
redshift is especially important, as the Universe’s young
age limits the contribution of several prominent dust
production processes (e.g., Magdis et al. 2012; Popping
et al. 2023; Valentino et al. 2024; Palla et al. 2024; Ferrara et al. 2024a).
Recent Atacama Large Millimeter/submillimeter Array (ALMA) studies found a substantial amount of dust
at _z_ = 6–8 (Laporte et al. 2017; Tamura et al. 2019; Inami et al. 2022; Witstok et al. 2023a). Several scenarios
have been considered to account for this significant dust
mass at this early epoch, such as high dust condensation efficiency or efficient metal accretion into ISM (Li
et al. 2019; Liu & Hirashita 2019; Graziani et al. 2020;
Dayal et al. 2022; Witstok et al. 2023b; Burgarella et al.
2024). Investigation of the emergence of dust in more
distant galaxies is essential for understanding the rapid
increase in dust mass in the early Universe and identifying the main processes that contribute to this growth
(e.g., Burgarella et al. 2024). The small age of the universe further helps explore the rapid pathways that drive
dust growth.



Beyond relative dust and gas content, the total gas
mass also provides valuable insights, as stars form from
cold gas via various cooling mechanisms including dust
thermal emission. Specifically, the star formation efficiency (SFE), defined as the star formation rate (SFR)
divided by the total (or cold) gas mass, indicates how
galaxies convert gas into stars (see Tacconi et al. 2020,
for review). Observations of cold gas tracers such as
CO and [C ii] lines have shown that galaxies on the
star-forming main sequence (MS) typically exhibit lower
SFE than ‘starburst’ galaxies (e.g., Sanders et al. 1991;
Sargent et al. 2012; Tacconi et al. 2018). For instance,
Dessauges-Zavadsky et al. (2020) reported a weak redshift evolution of the gas-depletion timescale ( _t_ dep _∝_
1 _/_ SFE) in _z_ _∼_ 5 UV-selected galaxies, suggesting moderate star formation activity even at high- _z_ . However,
whether this weak evolution is maintained at _z_ _>_ 12
is entirely unknown, but it could be a key probe to investigate the origin of the overabundance of UV-bright
galaxies at _z_ _>_ 12 (e.g., Castellano et al. 2022; Atek
et al. 2023; Harikane et al. 2023; Finkelstein et al. 2024).
In this paper, we examine the interstellar medium of
two _z_ _>_ 12 galaxies using ultra-deep ALMA observations of the [O iii] emission and the dust continuum.
Our study focuses on two of the highest-redshift galaxies known to date, GHZ2 at _z_ = 12 _._ 3 (Castellano et al.
2024; Zavala et al. 2024a) and GS-z14-0 at _z_ = 14 _._ 2
(Carniani et al. 2024a). Leveraging the gas phase and
stellar metallicities as well as stellar assembly histories
observed at _z_ _>_ 12, which have been available thanks
to the exceptional sensitivity of the _James_ _Webb_ _Space_
_Telescope_ (JWST), we aim to explore dust production,
dust growth, and star formation efficiency in these early
galaxies by exploiting the available deep ALMA observations.
The paper is organized as follows: Section 2 provides
an overview of the datasets used in this work. Section

3 describes the method of dust mass measurements. In
Section 4, we present our constraints and discussions
from the _M_ _∗_ - _M_ dust relations and the gas-phase metallicity _Z_ and dust-to-gas mass relation at _z_ _>_ 12, the dust
production history and the star formation efficiency of
the target galaxies. The conclusions are presented in
Section 5. Throughout this paper, we assume a flat universe with the cosmological parameters of Ω M = 0 _._ 3,
Ω Λ = 0 _._ 7, _σ_ 8 = 0 _._ 8, and _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1] .


2. TARGETS


2.1. _GHZ2_


GHZ2 was originally discovered by JWST photometry as part of the GLASS-JWST Program (Treu et al.
2022) and identified in several studies as a robust candidate of the brightest galaxy at _z_ _>_ 11 (Castellano
et al. 2022; Naidu et al. 2022; Harikane et al. 2023;
Bouwens et al. 2023). Its spectroscopic redshift was confirmed to be _z_ = 12 _._ 3 thanks to the detection of rest

Dust and gas at _z_ _>_ 12 3


**Figure** **1.** JWST NIRCam F444W and ALMA Band-6/8 thumbnails of GHZ2 in the rest-frame 0 _._ 3 _µ_ m, 52 _µ_ m and 88 _µ_ m
continuum (left) and GS-z14-0 in the rest-frame 0 _._ 3 _µ_ m and 88 _µ_ m continuum (right). Contour levels are shown in every 2 _σ_
from _±_ 3 _σ_ . At the positions of the detection in _λ_ rest = 0 _._ 3 _µ_ m, the dust continuum remains undetected for both galaxies.



frame UV/optical emission line with JWST/NIRSpec
(Castellano et al. 2024) and JWST/MIRI (Zavala et al.
2024a). More recently, Zavala et al. (2024b) reported
a detection of [O iii]88 _µ_ m at _∼_ 5 _σ_ level and provided
more accurate redshift ( _z_ = 12 _._ 3327 _±_ 0 _._ 0005). Both
NIRSpec and MIRI constrained its metallicity to be
low ( _Z_ gas _/Z_ _⊙_ _∼_ 0 _._ 1, see also Calabro et al. 2024) and,
across this paper, we will adopt the reported value of
_Z_ gas _/Z_ _⊙_ = 0 _._ 05 _−_ [+0] 0 _[.]_ _._ [12] 03 [from] [Zavala] [et] [al.] [(][2024a][).] [The]
inferred stellar mass changes depending on the SED fitting code and associated assumptions, with a range of
log _M_ _∗_ [ _M_ _⊙_ ] = 8 _._ 3–8.9 (see Appendix in Zavala et al.
2024a) after lens magnification correction of _µ_ = 1 _._ 3 [1]

(Bergamini et al. 2023). Throughout this paper, we
will adopt the star-formation history derived by Bagpipes (Carnall et al. 2018) with a total stellar mass of
log _M_ _∗_ [ _M_ _⊙_ ] = 8 _._ 27 [+0] _−_ 0 _[.]_ _._ [23] 18 [owing to its non-parametric ap-]
proach and good agreement with Prospector (Johnson et al. 2021) results in Harikane et al. (2024, see
Figure 4). Note that despite the rich dataset it is still
unclear whether an active galactic nucleus (AGN) contributes to the UV emission of GHZ2 (see also, Calabro
et al. 2024). And while Zavala et al. (2024b) concluded
that this galaxy is likely dominated by star formation
activity based on the [O iii]88 _µ_ m line width and H _β_ line
luminosity, further observations are necessary to accurately constrain the stellar mass and potential AGN activity in GHZ2.


2.2. _GS-z14-0_


GS-z14-0 was identified in the JADES NIRCam
dataset (Robertson et al. 2024) and spectroscopically
confirmed via a significant detection of the Ly- _α_ break
with NIRSpec/PRISM (Carniani et al. 2024a). Recent
ALMA observations reported successful [O iii]88 _µ_ m detection at _∼_ 6 _._ 6 _σ_ (Carniani et al. 2024b; Schouws et al.


1 While the gravitational lens magnification factor might be up to
_µ ∼_ 1 _._ 6 due to the closest galaxy at _z_ = 1 _._ 678, we adopt _µ_ = 1 _._ 3
throughout this paper following Zavala et al. (2024b).



2024) and confirmed to be _z_ = 14 _._ 1796 _±_ 0 _._ 0007. We
will refer to the star formation history with a stellar
mass of log _M_ _∗_ [ _M_ _⊙_ ] = 8 _._ 84 [+0] _−_ 0 _[.]_ _._ [09] 10 [(after] [magnification]
correction; _µ_ = 1 _._ 17) and the stellar/gas metallicity of
_Z/Z_ _⊙_ = 0 _._ 18 [+0] _−_ 0 _[.]_ _._ [01] 01 [from the][ Prospector][ fitting in][ Car-]
niani et al. (2024b), which is consistent with the metallicity derived in Schouws et al. (2024).


3. DATA AND ANALYSIS


3.1. _ALMA_ _data_


ALMA observations of GHZ2 were obtained in
both Band-6 and Band-8 by two DDT programs
(2021.A.00020.S; PI: Bakx and 2023.A.00017.S; PI:
Zavala), where the spectral setups were designed to
cover the [O iii]88 _µ_ m and the [O iii]52 _µ_ m lines, respectively. GS-z14-0 has also been observed by ALMA as
part of a DDT program (2023.A.00037.S; PI: Schouws)
targeting [O iii]88 _µ_ m emission line in Band-6. The calibration of the ALMA data is described in detail in
Zavala et al. (2024b, see also, Bakx et al. 2023; Carniani et al. 2024b), here we briefly summarize it. The
data were calibrated following standard ALMA pipeline
workflow using CASA version 6.5.1 (CASA Team et al.
2022). After removing channels _±_ 300 km s _[−]_ [1] around the
detected [O iii]88 _µ_ m and expected [O iii]52 _µ_ m line frequencies, we created continuum images with a natural
weighting to maximize the signal-to-noise ratio. We simply used a dirty image without a primary beam correction because the S/Ns of our target lines are not expected to be high enough to require cleaning procedure and we require uniform noise distribution within a
field of view. The achieved r.m.s levels for GHZ2 and
GS-z14-0 data are 3 _._ 4 _µ_ Jy beam _[−]_ [1] and 5 _._ 0 _µ_ Jy beam _[−]_ [1]

with beamsizes of 0 _[′′]_ _._ 51 _×_ 0 _[′′]_ _._ 43 and 0 _[′′]_ _._ 82 _×_ 0 _[′′]_ _._ 66 in Band6 before lens magnification correction, respectively. For
GHZ2, the Band-8 observations have an r.m.s depth of
54 _._ 6 _µ_ Jy beam _[−]_ [1] with a beamsize of 0 _[′′]_ _._ 71 _×_ 0 _[′′]_ _._ 63, which is
much shallower than Band-6 depth and less constraining
on _M_ dust even when taking _T_ dust variation into account.
Figure 1 shows thumbnails in the rest-frame 0 _._ 3 _µ_ m
and 88 _µ_ m (and 52 _µ_ m for GHZ2) taken by JWST and

4 Mitsuhashi, Zavala, Bakx et al.


**Figure** **2.** Dust mass and temperatures, color-coded by the signal-to-noise ratio of the dust continuum that is expected at
the rest-frame 88 _µ_ m for GHZ2 (left) and GS-z14-0 (right). Red solid lines indicate 1 _σ_ and 3 _σ_ upper limits at the rest-frame
88 _µ_ m by assuming a modified black body spectrum after lens magnification correction. The yellow lines on the left panel show
upper limits from the rest-frame 52 _µ_ m which provides a much less stringent constraint than those derived from the rest-frame
88 _µ_ m. The acceptable parameter sets and derived dust extinction obtained by the I20 model with the clumpy dust geometry are
overlayed in black dashed lines and dotted lines, respectively. Our constraints based on I20 model are shown in red diamonds
in the cross-section of 3 _σ_ red solid lines and black dashed lines. We also illustrated the 3 _σ_ upper limit under the assumption
of _T_ dust = 50 K in the pink circles to just demonstrate how I20 model gives tight constraints. Note also that these dust mass
constraints do not agree with the observed _A_ _V_ values (contrary to the values inferred using the I20 model).



ALMA. None of the dust continua were detected even
with ≳ 7 hours on source integrations.


3.2. _M_ dust _measurement_


We constrain the dust mass of these galaxies by applying an analytical model from Inoue et al. (2020, hereafter I20) to the deep ALMA observations. I20 proposed
an algorithm to determine the dust mass ( _M_ dust ) and
temperatures ( _T_ dust ) under the assumption of radiative
equilibrium. In their model, the dust temperature relates to the input radiation source from young stars and
cosmic microwave background (CMB) that are absorbed
by dust. Then, by incorporating dust geometry, we can
calculate the escape probability of UV photons from interstellar media, which results in observable UV luminosities. Among the three available models for the dust
geometry provided in I20 (see also, Imara et al. 2018),
we specifically employed the “clumpy” geometry as it is
considered a reliable approximation for high- _z_ galaxies
(e.g., Fudamoto et al. 2023; Kohandel et al. 2023). Indeed, this ‘clumpy’ geometry provided looser constraints
on _M_ dust than other geometries in I20, i.e., ‘spherical’
or ‘shell’ under the same assumptions, and therefore our
analysis is considered to be conservative. We assumed
the dust to be optically thin with an emissivity index
of _β_ dust = 2 _._ 0 (Casey 2012; da Cunha et al. 2021), a



mass absorption coefficient of _κ_ UV = 5 _._ 0 _×_ 10 [4] cm [2] g _[−]_ [1],
dust emissivity of _κ_ 0 = 30 cm [2] g _[−]_ [1] at 100 _µ_ m, and a
clumpiness parameter of log _ξ_ cl = _−_ 1 _._ 0 following I20
and Fudamoto et al. (2023). The only input from the
observations, beyond the continuum flux density, is the
spatial extent of dust. Here, we adopt the spatial extent
of the stars traced by the NIRCam photometry as those
of the dust emitting regions ( _r_ _e,_ dust = _r_ _e,_ UV, see Table
1). Note that in the case of GHZ2, if we use the effective radius of _r_ _e,_ UV = 39 _±_ 10 pc from Ono et al. (2023)
instead of 105 _±_ 9 pc, the _M_ dust and _M_ gas constraints
become tighter than the fiducial values owing to higher
_T_ dust and smaller _M_ dyn, respectively. Hence, the results
presented here are considered to be conservative.
In Figure 2, we show the resulting _T_ dust and _M_ dust parameter sets acceptable in our calculations based on the
I20 model, with observational constraints corrected for
the gravitational magnification ( _µ_ = 1 _._ 3 and _µ_ = 1 _._ 17
for GHZ2 and GS-z14-0, respectively). The upper limits on _M_ dust are shown at the intersection between the
analytical predictions (thick black dashed line) and the
observational limits (red dashed line). Our calculations
support very high _T_ dust ( _>_ 90 K) due to the compact
distribution and strong UV radiation. A similar high
_T_ dust was also inferred for a _z_ _∼_ 10 galaxy based on
recent ALMA observations (Yoon et al. 2023). Metal

Dust and gas at _z_ _>_ 12 5



**Table** **1.** Physical parameters of two _z_ _>_ 12 galaxies


GHZ2 GS-z14-0 ref


_M_ UV [mag] _−_ 20 _._ 53 _±_ 0 _._ 01 _−_ 20 _._ 81 _±_ 0 _._ 16 (1,2)
_µ_ 1 _._ 3 _[‡]_ 1.17 (1,2)
_r_ _e,_ F200W [pc] 105 _±_ 9 260 _±_ 20 (3,2)
log _M_ _∗_ [M _⊙_ ] 8 _._ 27 [+0] _−_ 0 _[.]_ _._ [23] 18 8 _._ 84 [+0] _−_ 0 _[.]_ _._ [09] 10 (4,2)
log _M_ dyn [M _⊙_ ] 8 _._ 9 _±_ 0 _._ 2 9 _._ 0 _±_ 0 _._ 2 (5,2)
SFR 10Myr [M _⊙_ yr _[−]_ [1] ] 8 _._ 7 [+1] _−_ 1 _[.]_ _._ [4] 9 9 _._ 9 [+2] _−_ 2 _[.]_ _._ [3] 7 (4,6)
SFR 100Myr [M _⊙_ yr _[−]_ [1] ] 1 _._ 4 [+2] _−_ 0 _[.]_ _._ [0] 3 5 _._ 6 [+1] _−_ 1 _[.]_ _._ [2] 3 (4,6)
_S_ 88 _µ_ m [ _µ_ Jy beam _[−]_ [1] ] _[†]_ _<_ 10 _._ 3 (3.4) _<_ 14 _._ 9 (5.0) (7)
_S_ 52 _µ_ m [ _µ_ Jy beam _[−]_ [1] ] _[†]_ _<_ 163 _._ 9 (54.6) - (7)
log _M_ dust [M _⊙_ ] _[¶]_ _<_ 5 _._ 0 _<_ 5 _._ 3 (7)


Note—Every parameter except for the ALMA observational constraints is corrected for magnification shown in the second row.


_‡_ As described in Zavala et al. (2024a), the magnification for GHZ2
might be _∼_ 1 _._ 6 if we take into account the closest galaxy at
_z_ = 1 _._ 682.

_†_ 3 _σ_ upper limits with 1 _σ_ uncertainties, without correcting the
magnification

_¶_ 3 _σ_ upper limits on the dust masses assuming thermal equilibrium
model in I20.
1. Castellano et al. (2024), 2. Carniani et al. (2024a), 3. Yang
et al. (2022), 4. Zavala et al. (2024a), 5. Zavala et al. (2024b),
6. Carniani et al. (2024b), 7. This work


poor ISM conditions in the target galaxies may also
contribute to these elevated dust temperatures (Tamura
et al. 2019; Bakx et al. 2020; Sommovigo et al. 2022a;
Mitsuhashi et al. 2024). As a consequence of the high
dust temperature conditions, our fitting set a tight 3 _σ_
upper limits on the dust masses of log _M_ dust _/M_ _⊙_ _<_ 5 _._ 0
and _<_ 5 _._ 3 for GHZ2 and GS-z14-0, respectively. These
upper limits agree well with the expected dust extinction ( _A_ _V_ ≲ 0 _._ 5 mag) under the ‘clumpy’ dust geometry
in each _M_ dust calculated through the escaped/intrinsic
UV radiation. In addition, the mass constraints are in
good agreement with those obtained by Ferrara et al.
(2024b), where they adopt the SED-based extinction as
a proxy of the dust mass.


4. RESULTS AND DISCUSSION


4.1. _Dust_ _production_ _and_ _evolution_ _at_ _cosmic_ _dawn_


In the left panel of Figure 3, we compare our constraints on the dust mass and stellar mass relation with
previous constraints for galaxies at _z_ = 4–7 (Bakx et al.
2021; Sommovigo et al. 2022a,b; Witstok et al. 2022;
Valentino et al. 2024). Our results indicate a lower
dust content in galaxies at _z_ _>_ 12 compared to those at
_z_ = 4–7, a trend that persists when compared with samples from Fudamoto et al. (2023), which were derived using a similar methodology. This conclusion holds even
when assuming _T_ dust = 50 K (e.g., Sommovigo et al.
2022a,b; Mitsuhashi et al. 2024), implying a dust mass
limit about _∼_ 1 dex larger than our fiducial value, as



shown in Figure 3. A recent study in Burgarella et al.
(2024) suggested a potential decrease of the dust-tostellar mass ratio at _z_ _>_ 10, which is in line with our
conclusion.
The dust-to-stellar mass ratio ( _M_ dust _/M_ _∗_ ) is likely influenced by grain growth within the ISM, which is driven
by the condensation of metals in dense gas and is thus
inversely proportional to gas-phase metallicity (e.g., de
Bennassuti et al. 2014; Burgarella et al. 2024). Given
the positive correlation between stellar mass and gasphase metallicity (i.e., the mass-metallicity relation),
grain growth becomes effective around stellar masses of
log _M_ _∗_ _/M_ _⊙_ ≳ 8 _._ 5 (Mancini et al. 2015). Models that
assume very efficient grain growth due to enhanced gas
condensation do not align closely with the non-detection
of dust continua at _z_ _>_ 12 (Popping et al. 2017; Vijayan
et al. 2019).
In the left panel of Figure 3, we also plot several (semi)analytical models of dust production at _z_ _>_ 6 (Popping
et al. 2017; Imara et al. 2018; Vijayan et al. 2019; Mauerhofer & Dayal 2023; Di Cesare et al. 2023), which predict
dust content evolution due to production by stars, destruction by SNe, and grain growth in clouds. These
models reproduce observed trends and scatter well at
_z_ = 4–7, though most seem to overestimate our measurements at _z_ _>_ 12, potentially because their models
focus on galaxies at _z_ _∼_ 7–9.
Another possible reason for low dust content at _z_ _>_ 12
is that dust is expelled or lifted off by the radiationdriven outflows (Ferrara 2024; Ferrara et al. 2024a). In
their model, the super-Eddington star formation occurs
with significant radiation pressure. In this case, the total dust mass might be underestimated because such
expelled dust is no longer in equilibrium. Indeed, GHZ2
is derived to have specific SFR of log sSFR _∼_ 1 _._ 67 Gyr,
which exceeds a critical sSFR (log sSFR _∼_ 1 _._ 4 Gyr) presented in Ferrara (2024). While GS-z14-0 is expected to
have log sSFR _∼_ 1 _._ 3 Gyr within recent _∼_ 100 Myr based
on its SFH, such a radiation-driven outflow may play an
important role for non-detections of the dust continuum.
In the right panel of Figure 3, we explore the relationship between gas-phase metallicity ( _Z_ gas ) and D/G. The
constraints on D/G at low metallicity values are critical
to disentangle dust growth scenarios. Here, we computed the gas mass by subtracting the magnificationcorrected stellar mass from the dynamical mass ( _M_ gas =
_M_ dyn _−_ _M_ _∗_ ) assuming negligible dark matter contribution within galaxy centers (≲ _r_ _e_ ). For GHZ2 and GSz14-0, the resulting gas masses in our fiducial caluclation are _M_ gas = 5 _._ 8 [+3] _−_ 3 _[.]_ _._ [7] 7 _[×]_ [ 10] [8] _[ M]_ _[⊙]_ [and] _[M]_ [gas] [= 2] _[.]_ [6] _−_ [+5] 2 _[.]_ _._ [2] 6 _[×]_
10 [8] _M_ _⊙_, respectively.
It is worth noting that, the mass of the ionized
gas component ( _M_ ion ) has an insignificant contribution.
Based on _L_ H _β_ _−_ _M_ ion relation presented in Ch´avez et al.
(2014), GHZ2 has _M_ ion = 2 _._ 5 _×_ 10 [6] _−_ 9 _._ 8 _×_ 10 [7] _M_ _⊙_ from
the H _β_ flux of _F_ H _β_ = 0 _._ 9 _±_ 0 _._ 2 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] and

6 Mitsuhashi, Zavala, Bakx et al.


**Figure** **3.** (left) Dust mass as a function of the stellar mass. Our constraints for the galaxies at _z_ _>_ 12 along with the previous
constraints at _z_ = 4–8 (Bakx et al. 2021; Sommovigo et al. 2022a,b; Witstok et al. 2022; Fudamoto et al. 2023; Valentino et al.
2024) and (semi-)analytical models (Popping et al. 2017; Imara et al. 2018; Vijayan et al. 2019; Di Cesare et al. 2023) including
DELPHI model (Mauerhofer & Dayal 2023) are shown in colors corresponding to their redshift. For Popping et al. (2017) and
Vijayan et al. (2019) models, predictions with different dust condensation efficiencies are shown in different line styles. The
markers surrounded by black lines are constraints using the I20 model, whereas those surrounded by gray lines show results
by assuming a modified black body radiation with a typical dust temperature (i.e. _T_ dust = 50 K). (right) Dust-to-gas mass
ratio against the gas-phase metallicity. Our fiducial constraints from _M_ gas = _M_ dyn _−_ _M_ _∗_ are shown in a red star and brown
hexagon, and those from _M_ gas = 0 _._ 1, 0.5, and 0 _._ 9 ( _M_ gas + _M_ _∗_ ) are illustrated in red and brown shaded regions with different
levels of opacity. Observational constraints at _z_ = 2–6 (Magdis et al. 2012; Popping et al. 2023; Valentino et al. 2024) and a
model (Popping et al. 2017) are shown in colors depending on their redshift. The black solid line and circles indicated median
relation and observations at _z_ = 0 (R´emy-Ruyer et al. 2014). The gray lines show models with the power law in the dust size
distribution of _r_ = 4 _._ 5 (dotted), 3.5 (dash-dotted), and 2.5 (dashed), respectively, from Hirashita & Kuo (2011).



electron density of _n_ _e_ = 100 _−_ 4000 cm _[−]_ [3] (Zavala et al.
2024a). GS-z14-0 is expected to have _M_ ion = 3 _._ 0 _×_ 10 [5] _−_
1 _._ 2 _×_ 10 [7] _M_ _⊙_ from _F_ H _β_ = 7 _._ 9 [+0] _−_ 0 _[.]_ _._ [17] 18 _[×]_ [ 10] _[−]_ [19] [ erg s] _[−]_ [1] [ cm] _[−]_ [2]

(Helton et al. 2024), assuming of the same range of electron density as GHZ2. We adopt _M_ ion = 1 _._ 2 _×_ 10 [7] _M_ _⊙_
as the lower limit of _M_ gas for GS-z14-0, as _M_ gas =
_M_ dyn _−_ _M_ _∗_ = 0 is unphysical.
We obtained constraints of D _/_ G ≲ 10 _[−]_ [4] at _Z_ _∼_ 0 _._ 1 _Z_ _⊙_
and D _/_ G ≲ 10 _[−]_ [3] at _Z_ _∼_ 0 _._ 2 _Z_ _⊙_ . As described in Popping et al. (2017), the D/G ratio as a function of metallicity is determined by the balance of the condensation
efficiency ( _f_ cond ) and accretion timescales ( _τ_ acc ) since
both condensation and accretion promote the increase
of the D/G. Among their calculations, models with high
_f_ cond do not align well even in the extreme case with
100% condensation and no accretion (‘no-acc’ model, although their calculations are up to _z_ _∼_ 9). At the metallicity range of _Z_ _<_ 0 _._ 5 _Z_ _⊙_, their fiducial model follows
the fixed accretion timescale _τ_ acc = 100 Myr (‘fix-tau’
model), which is consistent with our constraints. As a
consequence, the inferred upper limits favor a moderate
_f_ cond rather than the high-efficiency model in Popping
et al. (2017).
In the right panel of Figure 3, we compare our target galaxies with local dwarf galaxies, SBS0335-052 and



I Zw 18 (Schneider et al. 2016). These two galaxies show
a dramatic difference in D/G at similar gas-phase metallicity. Schneider et al. (2016) found that ISM density
causes this variety because of the efficient grain growth
in high-density ISM. Further investigation on the ISM
density, such as the molecular gas density (or electron
density as a proxy), might be helpful to confirm the potential inefficient dust grain growth of galaxies at _z_ _>_ 12.
As Liu & Hirashita (2019) suggested, both high _f_ cond
and short _τ_ acc can account for large dust amounts in
massive galaxies at _z_ _∼_ 7 (Hashimoto et al. 2019;
Tamura et al. 2019; Bakx et al. 2020). In their results,
the high _f_ cond model predicts large dust mass at the very
early stage of the galaxy formation (≲ 10 Myr) while the
short _τ_ acc model imply a rapid increase of dust mass at
the age of _∼_ 100 Myr. If our target galaxies at _z_ _>_ 12 are
progenitors of these _z_ _∼_ 7 massive galaxies, our results
support the short _τ_ acc model with _τ_ acc _∼_ 5–100 Myr,
while the high _f_ cond model is unsupported. From another perspective, the models by Hirashita & Kuo (2011)
reveal that dust size distribution and _τ_ acc significantly
affect D/G at metallicities of _Z_ _∼_ 0 _._ 1–2 _Z_ _⊙_ (see also,
Asano et al. 2013). Our results at _Z_ _∼_ 0 _._ 2 _Z_ _⊙_, while
having a large uncertainty, suggest that a moderately
large-size dust distribution with _τ_ acc _∼_ 10 Myr can con

Dust and gas at _z_ _>_ 12 7


**Figure** **4.** Dust and star formation history derived from non-parametric SFH and SN/AGB dust yield models for GHZs (left)
and GS-z14-0 (right). (top) Smoothed exponentially rising star formation history (black) derived from Bagpipes (red, Zavala
et al. 2024a) and Prospector (blue, Carniani et al. 2024b; Harikane et al. 2024). (middle, bottom) Our constraints on the
dust mass with the previous results from the REBELS survey (Topping et al. 2022; Dayal et al. 2022; Ferrara et al. 2022). The
models of the dust production history from SFH are based on Valiante et al. (2009) with the SN dust yield from Bianchi &
Schneider (2007) and Zhukovska et al. (2008), and the AGB dust yield from Ferrarotti & Gail (2006) and ATON code (Dell’Agli
et al. 2019). For Zhukovska et al. (2008) and ATON models, we show ranges with 10 _[−]_ [4] –0 _._ 1 _Z_ _⊙_ with orange and blue shaded
regions. The effect of the initial mass function (IMF) and reverse shock is shown in two arrows. The SN yield by Bianchi &
Schneider (2007) model with 20% dust survival fraction is shown in the orange dashed line.

8 Mitsuhashi, Zavala, Bakx et al.



sistently explain the low D/G observed at low metallicities, as shown in Figure 3.
Here, we emphasize the importance of the direct observations of molecular gas tracers. In the right panel
of Figure 3, we also illustrate the acceptable D/Gs
based on _M_ gas assuming gas mass fractions of _f_ gas =
_M_ gas _/_ ( _M_ gas + _M_ _∗_ ) = 0 _._ 1, 0.5, and 0.9 instead of those
from _M_ dyn _−_ _M_ _∗_ . Nevertheless, it is impossible to disentangle any models with this broad _f_ gas range of 0.1–0.9.
Further ALMA observations targetting [C ii] or CO lines
will be a key to directly constrain _f_ gas and confirm the
gas mass from the dynamical masses. For instance, [C ii]
line can be detected in 3–15 hours source integration in
case of _f_ gas _∼_ 0 _._ 9 based on the calibration of _L_ [CII] _/M_ mol
in Zanella et al. (2018) [2] .
In addition to grain growth, dust destruction can play
a critical role, particularly by SN reverse shocks. Figure
4 shows the evolution of stellar and dust masses from
supernovae (SNe) and asymptotic giant branch (AGB)
stars, based on each galaxy’s SFH derived using Bagpipes or Prospector (Zavala et al. 2024a; Carniani
et al. 2024b; Harikane et al. 2024, see also section 2).
The SFHs are parameterized with an exponential profile (SFR( _t_ ) _∝_ exp( _t/τ_ )), with star formation starting
at _z_ = 20 for GHZ2 and _z_ = 30 for GS-z14-0. Our
predictions are based on a recipe presented in Valiante
et al. (2009, see also, Schneider & Maiolino (2024) for
recent review) with the SN dust yield from Bianchi &
Schneider (2007) and Zhukovska et al. (2008), and the
AGB dust yield from Ferrarotti & Gail (2006) and the
ATON code (Dell’Agli et al. 2019). Given the metalpoor nature of the galaxies at _z_ _>_ 12, we use the dust
yield model with the metallicity of 10 _[−]_ [4] –0 _._ 1 _Z_ _⊙_ . We
integrate the dust yield from stars ranging 0 _._ 1–100 _M_ _⊙_
under a Larson (Larson 1998) IMF with _α_ = 1 _._ 35 and
_M_ ch = 0 _._ 35, which is similar to a Salpeter IMF (Salpeter
1955).
Given the young stellar ages derived from SED fitting
(≲ 150 Myr) and the age of the universe at these redshifts (≲ 300 Myr), dust from SNe dominates the bulk
mass. For GS-z14-0, a high _>_ 80% destruction efficiency
by SN reverse shocks is necessary to reproduce the observed dust-to-stellar mass ratios, while destruction is
not necessarily significant for GHZ2 (see Figure 4). The
surviving dust mass fraction of _<_ (100 _−_ 80) = 20%
in case of GS-z14-0 is actually consistent with theoretical studies (e.g., Nozawa et al. 2007; Biscaro & Cherchneff 2016; Kirchschlager et al. 2019). The expected
significant dust destruction in GS-z14-0 by SN reverse
shock contrasts with that inferred for dust-rich galaxies


2 The calibration in Zanella et al. (2018) do not cover the metallicity range of _Z_ ≲ 0 _._ 2 _Z_ _⊙_ (see also, R´emy-Ruyer et al. 2014).
The estimation of [C ii] line luminosity here may be optimistic as

[C ii] line is likely to be fainter in low- _Z_ galaxies (e.g., Hashimoto
et al. 2019; Harikane et al. 2020; Bakx et al. 2024)



at _z_ _∼_ 7 (Le´sniewska & Micha�lowski 2019). While inefficient dust destruction or high condensation efficiency
may play a more important role in these lower redshift
galaxies (Dayal et al. 2022, see also, Palla et al. 2024), it
is also possible that the large dust content in REBELS
galaxies may be the result of efficient ISM grain growth
given their longer ages of tens to hundreds of Myr compared to our _z_ _>_ 12 systems.
We also found that a lower dust survival rate is necessary to explain the upper limits if the IMF is more topheavy. Specifically, ≲ 4% dust survival rate is required
in GS-z14-0 under _M_ ch = 10 instead of _M_ ch = 0 _._ 35
in the Larson IMF (comparable to the top-heavy IMF),
which is smaller than the expectations from several models (e.g., Marassi et al. 2015). Although some theoretical models predict a much lower dust survival rate (e.g.,
Nozawa et al. 2007; Slavin et al. 2020), it may suggest
that the top-heavy IMF scenario is not preferred to explain the overabundance of UV-bright galaxies at _z_ _>_ 10
from their low dust contents.


4.2. _Star_ _formation_ _efficiency_


In this section, we compare efficiencies of gas consumption at _z_ _>_ 12 with those at _z_ _<_ 9. In our
fiducial calculations, the total gas masses of the target
galaxies are computed as _M_ gas = _M_ dyn _−_ _M_ _∗_ as outlined in section 4.1 and, following Aravena et al. (2024),
we assume the ISM is dominated by the molecular gas
( _M_ gas _≃_ _M_ mol ). As in section 4.1, we also calculate gas
masses assuming _f_ gas = 0 _._ 1–0.9. The caveats associated
with these assumptions will be discussed below. On the
other hand, we calculate the SFRs by averaging the nonparametric SFHs over timescales of 10 Myr and 100 Myr
(Table 1).
Figure 5 illustrates the evolution of the star formation efficiency (SFE), defined as SFR _/M_ mol . For comparison, we plotted data from main-sequence (MS) and
‘starburst’ (SB) galaxies from PHIBSS (Tacconi et al.
2018), lensed DSFGs (Aravena et al. 2016; Jarugula
et al. 2021; Zavala et al. 2022), unlensed DSFGs (Birkin
et al. 2021), ALPINE (Dessauges-Zavadsky et al. 2020)
and REBELS (Aravena et al. 2024). We also show the
scaling relations from Tacconi et al. (2020) and Scoville et al. (2017) at the stellar mass of _M_ _∗_ = 10 [10] _M_ _⊙_ .
While the range of stellar masses at each redshift spreads
log _M_ _∗_ _/M_ _⊙_ = 8–11 (with high redshift galaxies showing
systematically smaller stellar masses), the dependence of
the SFE on the stellar mass is small ( _∝_ 1 _/_ 10 [0] _[.]_ [01] _[−]_ [0] _[.]_ [03] ).
Also, it is worth noting that molecular gas tracers differ across studies (CO in PHIBSS and SMGs, [C ii] in
ALPINE and REBELS), but these variations do not
introduce systematic uncertainties with the dynamical mass-based estimations (Dessauges-Zavadsky et al.
2020; Birkin et al. 2021; Aravena et al. 2024).
For GHZ2, the SFR averaged over 100 Myr,
SFR 100 Myr, is smaller than SFR 10 Myr, owing to its inferred rapidly increasing star formation activity (see Fig

Dust and gas at _z_ _>_ 12 9


**Figure** **5.** Redshift evolution of the star formation efficiency. Our fiducial calculations (red stars and brown hexagons) are
shown based on SFR 10Myr (filled) and SFR 100Myr (open markers), respectively. We also illustrate SFEs based on the gas masses
assuming _f_ gas = 0 _._ 1–0.9 in red and brown shaded regions associated with each marker. Shifts have been added in the x-axis
direction for ease of viewing. Previous studies of the MS galaxies from PHIBSS (blue circles, Tacconi et al. 2018), ALPINE
(blue shades, Dessauges-Zavadsky et al. 2020), and REBELS (green shades, Aravena et al. 2024) as well as SB galaxies from
PHIBSS (orange circles), unlensed DSFGs (brown crosses, Birkin et al. 2021), lensed DSFGs (yellow diamonds, Aravena et al.
2016; Jarugula et al. 2021; Zavala et al. 2022) are also plotted. The predicted evolution in Tacconi et al. (2020, orange solid and
blue dashed lines) and Scoville et al. (2017, yellow solid and green dashed lines).



ure 4). The SFR 100 Myr of GHZ2 is consistent with
the expected evolution of MS galaxies, but the most
recent star-forming episode, represented by SFR 10 Myr
shows a higher efficiency in better agreement with the
so-called “starbursts” systems. In contrast, GS-z14-0
has a comparable high SFE at both 10 Myr and 100 Myr
timescales (given its more smoothly-rising SFH), indicating a relatively longer-term starburst mode. The
SFEs of GHZ2 and GS-z14-0 in 10 Myr timescale are
SFH 10 Myr ≳ 10 Gyr _[−]_ [1] and are in a good agreement
with the expected redshift evolution of starburst galaxies. This contrasts with the UV-bright galaxies at _z_ = 4–
8 selected via the Lyman break method, which has SFEs
of _∼_ 1 Gyr _[−]_ [1] and follows the MS scaling relation or even
prefers a shallower evolution (Dessauges-Zavadsky et al.
2020; Aravena et al. 2024). Indeed, this high SFE in
GHZ2 is in line with the interpretation in Zavala et al.
(2024b), H ii galaxy-like nature of GHZ2.
The timescales over which the star formation is being calculated can be important when comparing our
measurements with those at lower redshifts. In Figure



5, the SFRs of UV-selected galaxies at _z_ = 4–8 (i.e.,
ALPINE/REBELS galaxies) are calculated from restframe UV and IR continuum tracing the average star
formation activity within _∼_ 100 Myr. Indeed, Endsley
et al. (2024) reported that around 10% of _z_ _≈_ 6–9 UVbright galaxies with _M_ UV _∼−_ 20 mag show an order of
magnitude higher SFR in _<_ 10 Myr. Therefore, _∼_ 10%
of the ALPINE/REBELS galaxies may have an order
of magnitude larger SFR within a _<_ 10 Myr timescale,
implying a higher SFR in better agreement with the
SB scaling relation. [3] On the other hand, as described


3 A fraction of galaxies having rising SFHs may increase in galaxies with the small absolute UV magnitude (Endsley et al. 2024;
Asada et al. 2024; Harikane et al. 2024). As the ALPINE
and REBELS galaxies have smaller absolute UV magnitude
( _M_ UV _∼−_ 21– _−_ 22 mag) than those at Endsley et al. (2024,
_M_ UV _∼−_ 20 mag), the fraction of the galaxies lying on the SB
sequence in 10 Myr timescale may be higher than _∼_ 10% in the
ALPINE and REBELS galaxies. However, at least not every
galaxy has like that rising SFHs (Topping et al. 2022; Palla et al.
2024).

10 Mitsuhashi, Zavala, Bakx et al.



above, both GHZ2 and GS-z14-0 are likely under a starburst episode, which may suggest that this ‘starburst’
phase with efficient gas consumption is more ubiquitous
among UV-bright galaxies at _z_ _>_ 12 than at _z_ _∼_ 6.
As described in Carniani et al. (2024b), GS-z14-0 exhibits a smaller gas fraction ( _M_ gas _/_ ( _M_ _∗_ + _M_ gas ) _∼_ 0 _._ 3)
than those at _z_ = 4–8 ( _M_ gas _/M_ _∗_ _∼_ 1 DessaugesZavadsky et al. 2020; Aravena et al. 2024), indicating
small gas reservoir compared with an existing stellar
mass. Approximating _M_ gas _≈_ _f_ _b_ _M_ halo, where _f_ _b_ and
_M_ halo is the cosmic baryon fraction and the host halo
mass, respectively, the stellar-to-halo mass ratio ( _ϵ_ _∗_ =
_M_ _∗_ _/M_ halo ) becomes around 0.5, which is consistent with
recent studies implying high _ϵ_ _∗_ (e.g., Casey et al. 2024;
Shuntov et al. 2024). The high SFE and small gas fraction in GS-z14-0 align also with the feedback-free star
formation model (Dekel et al. 2023; Li et al. 2024). All
these scenarios might be (at least partially) responsible
for the reported overabundance of UV-bright galaxies at
_z_ ≳ 10. We thus hypothesize that GS-z14-0 is converting most of its molecular gas into stars in a recent ‘starburst’, and will run out the molecular gas (or expel the
gas and dust components, see Ferrara 2024), and turn
off their star formation within the next several 10 Myrs.
On the other hand, GHZ2 shows a large fraction
of molecular gas mass within the baryonic content
( _M_ gas _/_ ( _M_ _∗_ + _M_ gas ) _∼_ 0 _._ 7). Its instantaneous high SFE
and high gas fraction may be the result of a bursty star
formation history, which increases the visibility of UVbright galaxies during short and intense bursts of star
formation (e.g., Sun et al. 2023; Kravtsov & Belokurov
2024). Further observations capturing rest-frame optical
stellar continuum will enable us to make more accurate
constraints on the stellar mass, and therefore on the gas
fraction.
One major caveat in using _M_ dyn _−_ _M_ _∗_ as a proxy
of _M_ gas is the uncertain fraction of the molecular gas
within the total gas. However, if the molecular gas fraction is below unity, the derived _M_ mol decreases, and the
SFE increases. Therefore, the adopted molecular gas
fraction does not affect our conclusion. We acknowledge, however, that conducting direct observations of
cold ISM tracers, such as [C ii] or CO lines, is crucial to
put better constraints on the molecular gas mass. As
shown in the shaded boxes in Figure 5, the assumption
of the _f_ gas range of 0.1–0.9 prevents imposing any meaningful constraints on the SFE. The detection experiment
of [C ii] will be an important key to confirm or rule out
our conclusion.


5. SUMMARY


In this paper, we have investigated the dust and gas
content of the brightest galaxies at _z_ _>_ 12, GHZ2,
and GS-z14-0, based on direct ALMA observations that
trace the bulk of the dust mass in these galaxies. From
the combination of ultra-deep ALMA observations and
an analytical thermal equilibrium model, we have found:




  - The 3 _σ_ upper limits on the dust continuum at
_λ_ rest = 88 _µ_ m are 10 _._ 3 _µ_ Jy and 14 _._ 9 _µ_ Jy for Band-6
observations on GHZ2 and GS-z14-0, respectively.
Combining these observations with an analytical
model based on thermal equilibrium and clumpy
dust geometry (Inoue et al. 2020), we derived dust
mass upper limits of log _M_ dust _/M_ _⊙_ _<_ 5 _._ 0 and
_<_ 5 _._ 3, respectively.


  - The comparison of our constraints on _M_ _∗_ – _M_ dust
plane and dust production models at _z_ _>_ 4 do
not imply efficient dust grain growth with extreme condensation efficiency _f_ cond . Assuming
most massive galaxies at _z_ _>_ 12 are potential
progenitors of most massive galaxies at _z_ = 7,
a short accretion timescale scenario is supported
rather than a high _f_ cond scenario in Liu & Hirashita (2019). Initial dust size distributions with
a moderate amount of large-size grains, resulting
in _τ_ acc _∼_ 10 Myr, are preferred in our constraints
on the _Z_ –D/G relation.


  - Given the very young ages of the target galaxies,
dust yield from AGB stars and grain growth are
not likely to be effective. The observed dust-tostellar mass ratios in GS-z14-0 can be naturally
explained by the dust survival rate of _<_ 20% from
the reverse shocks by SN.


  - Based on the gas masses from _M_ gas = _M_ dyn _−_ _M_ _∗_
and SFHs, we inferred star formation efficiencies
within the past 10 Myr, which reach high values
above _∼_ 10 Gyr _[−]_ [1], comparable with the predicted
SFEs’ evolution of starburst galaxies. GHZ2 may
exhibit short starburst-like episodes only for relatively short periods of up to _∼_ 10 Myr, while
GS-z14-0 is likely to have such starburst mode
in a relatively long term of _∼_ 100 Myr. From a
comparison with UV-bright galaxies at _z_ _∼_ 6, we
hypothesize that such ‘starburst’ activity may be
more ubiquitous in UV-bright galaxies at _z_ _>_ 12
than at _z_ _∼_ 6, potentially due to bursty SFHs
(e.g., Sun et al. 2023) and/or negligible feedback
coming from super-Eddington star formation (e.g.,
Dekel et al. 2023).


Our study demonstrates the importance of observing
cold interstellar medium tracers, such as dust continuum
and [C ii] line observations with ALMA to derive the
current and future star formation activity of UV-bright
galaxies. Since our analysis with the thermal equilibrium model predicts very high _T_ dust, further deep ALMA
observations at high frequency to capture near the peak
of dust thermal emission will be useful to identify dust
at _z_ _>_ 12. For instance, _∼_ 30 hours ALMA Band 9 observations covering rest-frame _∼_ 30 _µ_ m allows us to add
tighter constraint on _M_ dust at _T_ dust _>_ 100 K regime.
To further understand the emergence of dust across the

Dust and gas at _z_ _>_ 12 11


Universe, investigating the gas and dust content of most
massive galaxies at _z_ _∼_ 8–11 is necessary to constrain
the grain growth in the ISM. Systematic comparison of
ISM conditions, such as gas/electron density, across the
Universe, might be critical to understanding the origin
of the lack of dust and the potential ‘starburst’ nature
of _z_ _>_ 12 galaxies.


ACKNOWLEDGMENTS


We thank P. Dayal for providing us with data
from their semi-analytical calculation. This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2021.A.00020.S, #2023.A.00017,
#2023.A.00037. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS
(Japan), together with NRC (Canada), MOST and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO, and
NAOJ. IM and AKI acknowledge support from NAOJ
ALMA Scientific Research Grant number 2020-16B. The
authors acknowledge the GLASS and JADES teams led
by Tommaso Treu and Daniel Eisenstein & Nora Luetzgendorf, respectively, for developing their observing
programs. The _JWST_ data presented in this article
were obtained from the Mikulski Archive for Space
Telescopes (MAST) at the Space Telescope Science
Institute. The specific observations analyzed can be
found in the MAST [10.17909/wz7w-2208.](http://dx.doi.org/10.17909/wz7w-2208) Data analysis was in part carried out using the Multi-wavelength
Data Analysis System operated by the Astronomy Data
Center (ADC), National Astronomical Observatory of
Japan. KK acknowledges support from the Knut and
Alice Wallenberg Foundation (KAW 2020.0081). PS
acknowledges INAF Mini Grant 2022 ”The evolution of
passive galaxies through cosmic time”.

12 Mitsuhashi, Zavala, Bakx et al.


REFERENCES



Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016,

MNRAS, 457, 4406

Aravena, M., Heintz, K., Dessauges-Zavadsky, M., et al.

2024, A&A, 682, A24

Asada, Y., Sawicki, M., Abraham, R., et al. 2024, MNRAS,

527, 11372

Asano, R. S., Takeuchi, T. T., Hirashita, H., & Inoue, A. K.

2013, Earth, Planets and Space, 65, 213

Atek, H., Shuntov, M., Furtak, L. J., et al. 2023, MNRAS,

519, 1201

Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020,

MNRAS, 493, 4294

Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021,

MNRAS, 508, L58

Bakx, T. J. L. C., Zavala, J. A., Mitsuhashi, I., et al. 2023,

MNRAS, 519, 5076

Bakx, T. J. L. C., Algera, H. S. B., Venemans, B., et al.

2024, MNRAS, 532, 2270

Bendo, G. J., Wilson, C. D., Warren, B. E., et al. 2010,

MNRAS, 402, 1409

Bergamini, P., Acebron, A., Grillo, C., et al. 2023, ApJ,

952, 84

Bianchi, S., & Schneider, R. 2007, MNRAS, 378, 973

Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021,

MNRAS, 501, 3926

Biscaro, C., & Cherchneff, I. 2016, A&A, 589, A132

Bouwens, R., Illingworth, G., Oesch, P., et al. 2023,

MNRAS, 523, 1009

Burgarella, D., Buat, V., Theul´e, P., et al. 2024, arXiv

e-prints, arXiv:2410.23959

Calabro, A., Castellano, M., Zavala, J. A., et al. 2024,

arXiv e-prints, arXiv:2403.12683

Carnall, A. C., McLure, R. J., Dunlop, J. S., & Dav´e, R.

2018, MNRAS, 480, 4379

Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024a,

Nature, 633, 318

Carniani, S., D’Eugenio, F., Ji, X., et al. 2024b, arXiv

e-prints, arXiv:2409.20533

CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP,

134, 114501

Casey, C. M. 2012, MNRAS, 425, 3094

Casey, C. M., Akins, H. B., Shuntov, M., et al. 2024, ApJ,

965, 98

Castellano, M., Fontana, A., Treu, T., et al. 2022, ApJL,

938, L15

Castellano, M., Napolitano, L., Fontana, A., et al. 2024,

ApJ, 972, 143

Ch´avez, R., Terlevich, R., Terlevich, E., et al. 2014,

MNRAS, 442, 3565



Ciesla, L., Boquien, M., Boselli, A., et al. 2014, A&A, 565,

A128

da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ,

806, 110

da Cunha, E., Hodge, J. A., Casey, C. M., et al. 2021, ApJ,

919, 30

Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, MNRAS,

512, 989

de Bennassuti, M., Schneider, R., Valiante, R., & Salvadori,

S. 2014, MNRAS, 445, 3039

Dekel, A., Sarkar, K. C., Birnboim, Y., Mandelker, N., &

Li, Z. 2023, MNRAS, 523, 3201

Dell’Agli, F., Valiante, R., Kamath, D., Ventura, P., &

Garc´ıa-Hern´andez, D. A. 2019, MNRAS, 486, 4738

Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020,

A&A, 643, A5

Di Cesare, C., Graziani, L., Schneider, R., et al. 2023,

MNRAS, 519, 4632

Draine, B. T. 1990, in Astronomical Society of the Pacific

Conference Series, Vol. 12, The Evolution of the

Interstellar Medium, ed. L. Blitz, 193–205

Draine, B. T. 2009, in Astronomical Society of the Pacific

Conference Series, Vol. 414, Cosmic Dust  - Near and Far,

ed. T. Henning, E. Gr¨un, & J. Steinacker, 453

Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ,

663, 866

Dwek, E. 1998, ApJ, 501, 643

Dwek, E., & Scalo, J. M. 1980, ApJ, 239, 193

Endsley, R., Stark, D. P., Whitler, L., et al. 2024, MNRAS,

533, 1111

Ferrara, A. 2024, A&A, 684, A207

Ferrara, A., Carniani, S., di Mascia, F., et al. 2024a, arXiv

e-prints, arXiv:2409.17223

Ferrara, A., Pallottini, A., & Sommovigo, L. 2024b, arXiv

e-prints, arXiv:2410.19042

Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS,

512, 58

Ferrarotti, A. S., & Gail, H. P. 2006, A&A, 447, 553

Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al.

2024, ApJL, 969, L2

Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2023,

MNRAS, 521, 2962

Galliano, F., Dwek, E., & Chanial, P. 2008, ApJ, 672, 214

Graziani, L., Schneider, R., Ginolfi, M., et al. 2020,

MNRAS, 494, 1071

Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ,

896, 93

Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265,

5

Dust and gas at _z_ _>_ 12 13



Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2024, arXiv

e-prints, arXiv:2406.18352

Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019,

PASJ, 71, 71

Helton, J. M., Rieke, G. H., Alberts, S., et al. 2024, arXiv

e-prints, arXiv:2405.18462

Hirashita, H., & Kuo, T.-M. 2011, MNRAS, 416, 1340

Hirashita, H., Tajiri, Y. Y., & Kamaya, H. 2002, A&A, 388,

439

Imara, N., Loeb, A., Johnson, B. D., Conroy, C., &

Behroozi, P. 2018, ApJ, 854, 36

Inami, H., Algera, H. S. B., Schouws, S., et al. 2022,

MNRAS, 515, 3126

Inoue, A. K. 2011, Earth, Planets and Space, 63, 1027

Inoue, A. K., Hashimoto, T., Chihara, H., & Koike, C.

2020, MNRAS, 495, 1577

Issa, M. R., MacLaren, I., & Wolfendale, A. W. 1990, A&A,

236, 237

Jarugula, S., Vieira, J. D., Weiss, A., et al. 2021, ApJ, 921,

97

Johnson, B. D., Leja, J., Conroy, C., & Speagle, J. S. 2021,

ApJS, 254, 22

Kirchschlager, F., Schmidt, F. D., Barlow, M. J., et al.

2019, MNRAS, 489, 4465

Kohandel, M., Ferrara, A., Pallottini, A., et al. 2023,

MNRAS, 520, L16

Koornneef, J. 1982, A&A, 107, 247

Kravtsov, A., & Belokurov, V. 2024, arXiv e-prints,

arXiv:2405.04578

Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837,

L21

Larson, R. B. 1998, MNRAS, 301, 569

Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ,

737, 12

Le´sniewska, A., & Micha�lowski, M. J. 2019, A&A, 624, L13

Li, Q., Narayanan, D., & Dav´e, R. 2019, MNRAS, 490, 1425

Li, Z., Dekel, A., Sarkar, K. C., et al. 2024, A&A, 690, A108

Lisenfeld, U., & Ferrara, A. 1998, ApJ, 496, 145

Liu, H.-M., & Hirashita, H. 2019, MNRAS, 490, 540

Magdis, G. E., Daddi, E., B´ethermin, M., et al. 2012, ApJ,

760, 6

Magrini, L., Bianchi, S., Corbelli, E., et al. 2011, A&A, 535,

A13

Mancini, M., Schneider, R., Graziani, L., et al. 2015,

MNRAS, 451, L70

Marassi, S., Schneider, R., Limongi, M., et al. 2015,

MNRAS, 454, 4250

Mauerhofer, V., & Dayal, P. 2023, MNRAS, 526, 2196

Mitsuhashi, I., Harikane, Y., Bauer, F. E., et al. 2024, ApJ,

971, 161



Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022,

ApJL, 940, L14

Nozawa, T., Kozasa, T., Habe, A., et al. 2007, ApJ, 666,

955

Ono, Y., Harikane, Y., Ouchi, M., et al. 2023, ApJ, 951, 72

Palla, M., De Looze, I., Rela˜no, M., et al. 2024, MNRAS,

528, 2407

Popping, G., Somerville, R. S., & Galametz, M. 2017,

MNRAS, 471, 3152

Popping, G., Shivaei, I., Sanders, R. L., et al. 2023, A&A,

670, A138

R´emy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014,

A&A, 563, A31

Robertson, B., Johnson, B. D., Tacchella, S., et al. 2024,

ApJ, 970, 31

Salpeter, E. E. 1955, ApJ, 121, 161

Sanders, D. B., Scoville, N. Z., & Soifer, B. T. 1991, ApJ,

370, 158

Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A,

562, A30

Sargent, M. T., B´ethermin, M., Daddi, E., & Elbaz, D.

2012, ApJL, 747, L31

Schneider, R., Hunt, L., & Valiante, R. 2016, MNRAS, 457,

1842

Schneider, R., & Maiolino, R. 2024, A&A Rv, 32, 2

Schouws, S., Bouwens, R. J., Ormerod, K., et al. 2024,

arXiv e-prints, arXiv:2409.20549

Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ,

837, 150

Shuntov, M., Ilbert, O., Toft, S., et al. 2024, arXiv e-prints,

arXiv:2410.08290

Slavin, J. D., Dwek, E., Mac Low, M.-M., & Hill, A. S.

2020, ApJ, 902, 135

Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022a,

MNRAS, 513, 3122

Sommovigo, L., Ferrara, A., Carniani, S., et al. 2022b,

MNRAS, 517, 5930

Sun, G., Faucher-Gigu`ere, C.-A., Hayward, C. C., et al.

2023, ApJL, 955, L35

Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A,

58, 157

Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ,

853, 179

Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ,

874, 27

Todini, P., & Ferrara, A. 2001, MNRAS, 325, 726

Topping, M. W., Stark, D. P., Endsley, R., et al. 2022,

MNRAS, 516, 975

Treu, T., Roberts-Borsani, G., Bradac, M., et al. 2022,

ApJ, 935, 110

14 Mitsuhashi, Zavala, Bakx et al.



Valentino, F., Fujimoto, S., Gim´enez-Arteaga, C., et al.

2024, A&A, 685, A138

Valiante, R., Schneider, R., Bianchi, S., & Andersen, A. C.

2009, MNRAS, 397, 1661

Vijayan, A. P., Clay, S. J., Thomas, P. A., et al. 2019,

MNRAS, 489, 4072

Witstok, J., Jones, G. C., Maiolino, R., Smit, R., &

Schneider, R. 2023a, MNRAS, 523, 3119

Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS,

515, 1751

Witstok, J., Shivaei, I., Smit, R., et al. 2023b, Nature, 621,

267

Yang, L., Morishita, T., Leethochawalit, N., et al. 2022,

ApJL, 938, L17



Yoon, I., Carilli, C. L., Fujimoto, S., et al. 2023, ApJ, 950,

61


Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS,

481, 1976


Zavala, J. A., Casey, C. M., Spilker, J., et al. 2022, ApJ,

933, 242


Zavala, J. A., Castellano, M., Akins, H. B., et al. 2024a,

Nature Astronomy


Zavala, J. A., Bakx, T., Mitsuhashi, I., et al. 2024b, arXiv

e-prints, arXiv:2411.03593


Zhukovska, S. 2014, A&A, 562, A76


Zhukovska, S., Gail, H. P., & Trieloff, M. 2008, A&A, 479,

453


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[1].redshift_or_distance.evidence[0]",
  "value": "z = 14.1796 ± 0.0007",
  "failed_quote": "Recent ALMA observations reported successful [O iii]88 _µ_ m detection at _∼_ 6 _._ 6 _σ_ (Carniani et al. 2024b; Schouws et al. 2024) and confirmed to be _z_ = 14 _._ 1796 _±_ 0 _._ 0007."
 },
 {
  "path": "science.targets[1].distance_source.evidence[0]",
  "value": "Carniani et al. (2024b); Schouws et al. (2024)",
  "failed_quote": "Recent ALMA observations reported successful [O iii]88 _µ_ m detection at _∼_ 6 _._ 6 _σ_ (Carniani et al. 2024b; Schouws et al. 2024) and confirmed to be _z_ = 14 _._ 1796 _±_ 0 _._ 0007."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[2]",
  "value": "GHZ2 gas metallicity Z_gas/Z_sun = 0.05 (+0.12/-0.03), Bagpipes star-formation history, log M* [M_sun] = 8.27 (+0.23/-0.18), SFR_10Myr = 8.7 (+1.4/-1.9) M_sun/yr, SFR_100Myr = 1.4 (+2.0/-0.3) M_sun/yr, F_Hbeta = 0.9 ± 0.2 x 10^-18 erg s^-1 cm^-2, n_e = 100-4000 cm^-3",
  "failed_quote": "GHZ2 has _M_ ion = 2 _._ 5 _×_ 10 [6] _−_ 9 _._ 8 _×_ 10 [7] _M_ _⊙_ from the H _β_ flux of _F_ H _β_ = 0 _._ 9 _±_ 0 _._ 2 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] and electron density of _n_ _e_ = 100 _−_ 4000 cm _[−]_ [3] (Zavala et al. 2024a)."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Compute total gas mass by subtracting magnification-corrected stellar mass from dynamical mass (M_gas = M_dyn - M_*), estimate ionized gas mass from Hbeta luminosity and electron density using Chávez et al. (2014), and combine with M_dust upper limits to constrain D/G vs. gas-phase metallicity.",
  "failed_quote": "Here, we computed the gas mass by subtracting the magnification-corrected stellar mass from the dynamical mass ( _M_ gas = _M_ dyn _−_ _M_ _∗_ ) assuming negligible dark matter contribution within galaxy centers (≲ _r_ _e_ )."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Compute total gas mass by subtracting magnification-corrected stellar mass from dynamical mass (M_gas = M_dyn - M_*), estimate ionized gas mass from Hbeta luminosity and electron density using Chávez et al. (2014), and combine with M_dust upper limits to constrain D/G vs. gas-phase metallicity.",
  "failed_quote": "Based on _L_ H _β_ _−_ _M_ ion relation presented in Ch´avez et al. (2014), GHZ2 has _M_ ion = 2 _._ 5 _×_ 10 [6] _−_ 9 _._ 8 _×_ 10 [7] _M_ _⊙_ from the H _β_ flux of _F_ H _β_ = 0 _._ 9 _±_ 0 _._ 2 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] and electron density of _n_ _e_ = 100 _−_ 4000 cm _[−]_ [3] (Zavala et al. 2024a)."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "n_e = 100 - 4000 cm^-3",
  "failed_quote": "and electron density of _n_ _e_ = 100 _−_ 4000 cm _[−]_ [3] (Zavala et al. 2024a)."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Ionized gas mass M_ion (GHZ2) = 2.5 x 10^6 - 9.8 x 10^7 M_sun",
  "failed_quote": "GHZ2 has _M_ ion = 2 _._ 5 _×_ 10 [6] _−_ 9 _._ 8 _×_ 10 [7] _M_ _⊙_ from the H _β_ flux of _F_ H _β_ = 0 _._ 9 _±_ 0 _._ 2 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] and electron density of _n_ _e_ = 100 _−_ 4000 cm _[−]_ [3] (Zavala et al. 2024a)."
 }
]
```
