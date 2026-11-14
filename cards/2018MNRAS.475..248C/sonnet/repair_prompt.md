# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018MNRAS.475..248C\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–9 (2017) Preprint 4 November 2021 Compiled using MNRAS L [A] TEX style file v3.0

## **VALES: IV. Exploring the transition of star formation** **efficiencies between normal and starburst galaxies using** **APEX/SEPIA Band-5 and ALMA at low redshift**

### C. Cheng [1] [,] [2], E. Ibar [1], T. M. Hughes [1] [,] [2] [,] [3] [,] [4], V. Villanueva [1], R. Leiton [1], G. Orellana [1], A. Munoz-Arancibia [1], N. Lu [2], C. K. Xu [2], C. N. A. Willmer [5], J. Huang [2], T. Cao [2], C. Yang [6] [,] [7] [,] [8], Y. Q. Xue [3] [,] [4] and K. Torstensson [6]

1 _Instituto_ _de_ _F´ısica_ _y_ _Astronom´ıa,_ _Universidad_ _de_ _Valpara´ıso,_ _Avda._ _Gran_ _Breta˜na_ _1111,_ _Valpara´ıso,_ _Chile._ _Email:_ _cheng.cheng@uv.cl_
2 _Chinese_ _Academy_ _of_ _Sciences_ _South_ _America_ _Center_ _for_ _Astronomy,_ _China-Chile_ _Joint_ _Center_ _for_ _Astronomy,_
_National_ _Astronomical_ _Observatories,_ _Chinese_ _Academy_ _of_ _Sciences,_ _Beijing_ _100012,_ _China_
3 _CAS_ _Key_ _Laboratory_ _for_ _Research_ _in_ _Galaxies_ _and_ _Cosmology,_ _Department_ _of_ _Astronomy,_ _University_ _of_ _Science_ _and_ _Technology_ _of_ _China,_ _Hefei_ _2_
4 _School_ _of_ _Astronomy_ _and_ _Space_ _Science,_ _University_ _of_ _Science_ _and_ _Technology_ _of_ _China,_ _Hefei_ _230026,_ _China_
5 _Steward_ _Observatory,_ _University_ _of_ _Arizona,_ _933_ _N._ _Cherry_ _Avenue,_ _Tucson,_ _AZ_ _85721,_ _USA_
6 _European_ _Southern_ _Observatory,_ _Alonso_ _de_ _Cordova_ _3107,_ _Casilla_ _19001,_ _Santiago_ _19,_ _Chile_
7 _Purple_ _Mountain_ _Observatory/Key_ _Lab_ _of_ _Radio_ _Astronomy,_ _Chinese_ _Academy_ _of_ _Sciences,_ _Nanjing_ _210008,_ _China_
8 _Institute_ _d’Astrophysique_ _Spatiale,_ _CNRS,_ _Univ._ _Paris-Sud,_ _Universit´e_ _Paris-Saclay,_ _Bˆat._ _121,_ _91405_ _Orsay_ _Cedex,_ _France_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
In this work we present new APEX/SEPIA Band-5 observations targeting the CO
( _J_ = 2–1) emission line of 24 Herschel-detected galaxies at _z_ = 0 _._ 1 _−_ 0 _._ 2. Combining
this sample with our recent new Valpara´ıso ALMA Line Emission Survey (VALES),
we investigate the star formation efficiencies (SFEs = SFR/ _M_ H 2 ) of galaxies at low
redshift. We find the SFE of our sample bridges the gap between normal star-forming
galaxies and Ultra-Luminous Infrared Galaxies (ULIRGs), which are thought to be
triggered by different star formation modes. Considering the SFE _[′]_ as the SFR and
the _L_ _[′]_ CO [ratio,] [our] [data] [show] [a] [continuous] [and] [smooth] [increment] [as] [a] [function] [of]
infrared luminosity (or star formation rate) with a scatter about 0.5 dex, instead of a
steep jump with a bimodal behaviour. This result is due to the use of a sample with a
much larger range of sSFR/sSFR ms using LIRGs, with luminosities covering the range
between normal and ULIRGs. We conclude that the main parameters controlling the
scatter of the SFE in star-forming galaxies are the systematic uncertainty of the _α_ CO
conversion factor, the gas fraction and physical size.


**Key** **words:** galaxies: ISM – submillimetre: galaxies – galaxies: starburst – galaxies:
star formation



**1** **INTRODUCTION**


The star formation efficiency (SFE) of a galaxy, defined as
the ratio between the star formation rate (SFR) and the
amount of gas reservoir, is a crucial parameter to characterise its star formation activity and future evolution. Previous studies have shown that the SFE of normal star-forming
galaxies (SFGs) are systematically lower than that of starburst galaxies, suggesting different mechanisms could be
triggering the star formation (Genzel et al. 2010; Daddi et
al. 2010; Carilli and Walter 2013). This lead to a proposal
of a bimodal SFE for the two types of star forming galaxies.
The first is associated with the “main sequence” (Brinchmann et al. 2004) formed by normal SFGs, where the star


_⃝_ c 2017 The Authors



formation is triggered within disk-like structures, and their
specific SFR (sSFR = SFR / _M_ _∗_ ) slowly decreases with the
increasing stellar mass (Schawinski et al. 2014). The second
is associated with starburst galaxies that have typical sSFR
above the main sequence, and include local Ultra-Luminous
Infrared Galaxies (ULIRGs, Solomon et al. 1997; Lonsdale
et al. 2006). Nevertheless, it is unclear whether the SFE bimodality is caused by a higher gas-to-star conversion rate or
simply by a higher fraction of dense molecular gas capable
of initiating star formation. Galaxies with SFR in between
the ULIRGs and the normal SFGs, e.g., Luminous Infrared
Galaxies (LIRGs, 10 [11] _<L_ IR _/L_ _⊙_ _<_ 10 [12] ), are a critical population to understand the SFE bimodality.


In studying the SFE in LIRGs, one obstacle is how to

2 _C._ _Cheng_ _et_ _al._


measure the molecular hydrogen mass ( _M_ H 2 ). Historically,
CO has become the most popular tracer of interstellar cold
molecular gas. One common method to translate the CO
luminosity into the _M_ H 2 is the adoption of a simple conversion factor _α_ CO = _M_ H 2 _/L_ _[′]_ CO [.] [However,] [it] [is] [challenging]
to accurately define the value of _α_ CO (Carilli and Walter
2013; Bolatto et al. 2013, and references therein). Empirically, the molecular gas clouds in the Milky Way and nearby
galaxies show an _α_ CO of 4 _._ 6 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1], which includes the helium correction (e.g., Solomon & Vanden Bout
2005). If the molecular clouds in SFGs have similar properties such as metallicity, dynamical state, gas density, then
the _α_ CO of SFG shall resemble that seen in local molecular
clouds (Solomon & Vanden Bout 2005). On the other hand,
simulations show that galaxy mergers change the cloud and
inter-cloud properties such as the rising of the velocity dispersion and kinetic temperature, which increases the CO
intensity (Narayanan et al. 2011). Thus the _α_ CO of interacting galaxies should drop by a factor of 2-10 (Narayanan et
al. 2012a). Detailed modelling and observational results suggest _α_ CO = 0 _._ 8 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] (Downes et al. 1998)
as a consistency value to derive _M_ H 2 in ULIRGs.
Papadopoulos et al. (2012a, 2012b) found that the
_α_ CO in LIRGs can change significantly. Previous studies show that the value of _α_ CO in LIRGs can be similar to that in ULIRGs (Solomon et al. 1997; Yao et
al. 2003), where _α_ CO is lower than the Galactic value
(e.g., _α_ CO = 0 _._ 5 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] in VV 114; _α_ CO =
1 _._ 5 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] in NGC 6240: Sliwa et al. 2013;
Tunnard et al. 2015). However, Papadopoulos et al. (2012a,
2012b) also find that the _α_ CO in (U)LIRGs can have values close to those found in the Galaxy (Costagliola et al.
2013; Sandstrom et al. 2013). The kinetic gas components
in LIRGs can mix different star formation activities: gas in
LIRGs may show compact (Xu et al. 2014) as well as ring
structures (Xu et al. 2015). This strongly indicates that the
_α_ CO may not have the same value for all LIRGs.
To explore the changing mechanism of the SFE between
the “main sequence” and the starburst regimes, we observe
a sample of LIRGs at 0.1 _<z<_ 0.2 with the Swedish-ESO PI
receiver for APEX (SEPIA, Billade et al. 2012) targeting
the CO ( _J_ = 2–1) emission line. We assume a cosmological
model with _H_ 0 = 70 km _/_ s _/_ Mpc, Ω m = 0.3, and Ω Λ = 0.7.


**2** **GALAXY** **SAMPLES** **AND** **DATA**


**2.1** **Sample** **selection**


The _Herschel_ Astrophysical Terahertz Large Area Survey
( _H_ -ATLAS Eales et al. 2010) covered 600 deg [2] of the extragalactic sky with the PACS and SPIRE cameras in the 100,
160, 250, 350 and 500 _µm_ bands. We selected targets from
the equatorial _H_ -ATLAS fields covered by the Galaxy And
Mass Assembly survey which has a rich multi-wavelength
broadband coverage (Driver et al. 2016), including NUV
and FUV bands from the GALEX imaging, the optical images and spectroscopy from SDSS or GAMA, near-IR (NIR)
imaging from the VISTA project, mid-IR (MIR) imaging
from WISE and the _Herschel_ far-IR (FIR) photometry.



**Figure** **1.** The specific star formation rate (sSFR = SFR/ _M_ _∗_ ),
normalised to that estimated for the ‘main sequence’ (MS, Elbaz
et al. 2011; Whitaker et al. 2012) as a function of redshift for
different samples of galaxies detected in CO. We use the parameterisation of the MS as log[sSFR(MS _,z, M_ _∗_ )] = _−_ 1 _._ 12 + 1 _._ 14 _z −_
0 _._ 19 _z_ [2] _−_ (0 _._ 3+0 _._ 13 _z_ ) _×_ (log _M_ _∗_ _−_ 10 _._ 5) [Gyr _[−]_ [1] ] (Genzel et al. 2015),
where the dashed lines represent +/- 0.6 dex offsets from this relation for star-forming galaxies. Our VALES data are presented
as blue open circles for ALMA and red solid circles for APEX
observations. The green crosses are the IRS bright local galaxies
(GOALS: Armus et al. 2009); the cyan asterisks are the nearby
MS galaxies (COLDGASS: Saintonge et al. 2011); the light blue
open squares are _z_ = 0 _._ 05 _−_ 0 _._ 5 normal galaxies (EGNoG: Bauermeister et al. 2013); the orange open triangles are the ULIRGs at
intermediate redshifts (Combes et al. 2011; Combes et al. 2013);
the purple diamonds are the MS galaxies at 0.5 _<z<_ 1 (PHIBSS:
Combes et al. 2016). More details about these archive data can be
found in the Fig. 1 of Genzel et al. (2015). The grey shaded region
in this figure shows our target selection within 0.1 _<z<_ 0.2, which
includes the CO ( _J_ = 1–0) ALMA Band-3 detected galaxies and
the CO ( _J_ = 2–1) APEX/SEPIA Band-5 detected galaxies.


Making use of the public _H_ -ATLAS DR1 [1] catalog,
we select sources with reliable optical counterpart, spectroscopic redshift at 0.1 _<z<_ 0.2, and located at the top
of the sSFR distribution ( _M_ _∗_ from GAMA and SFR from
_L_ IR ). These criteria allow weeding out the most intensely
starbursting objects from the sample. Using these targets,
we explore their molecular gas content via their CO emission. These observations complement our recent Valpara´ıso
ALMA Line Emission Survey (VALES, Villanueva et al.
2017; Hughes et al. 2017a; 2017b), which is the largest
CO-detected galaxy sample at _z∼_ 0.15. Fig. 1 shows the
sSFR/sSFR ms of the current CO-detected galaxy sample
with different redshift. There are several parametrisations
of the main sequence galaxies (e.g., Speagle et al. 2014;
Schreiber et al. 2015). As the follow up work of our VALES
project, we adopt the sSFR = sSFR( _M_ _∗_ _, z_ ) given by Genzel
et al. (2015) as the VALES I paper (Villanueva et al. 2017).


1 `[http://www.h-atlas.org/public-data/download](http://www.h-atlas.org/public-data/download)`


MNRAS **000**, 1–9 (2017)

_Transition_ _in_ _galaxy_ _star_ _formation_ _efficiency_ 3


**Figure** **2.** The observed CO ( _J_ = 2–1) spectra for APEX/SEPIA Band-5 observed galaxies centred on spectroscopic redshifts taken
from GAMA. The postage image in the upper left of each spectrum comes from the SDSS colour image with a scale of 25” _×_ 25”. The
scale bar in the optical image denotes a length of 5”. The top 12 galaxies have CO detection with 5 _σ_ . We fit the CO emission by a
single Gaussian profile and show the result as a red line. Typical FWHM is 300 km/s. HATLAS J115849.9-013146 is an isolated galaxy
with fitted FWHM of about 1000 km/s, much larger than that of other galaxies. This galaxy is isolated and located in a group of three
galaxies at _z_ = 0 _._ 147 within 65 kpc ( _≃_ 25 _._ 3 _[′′]_ ). The Petrosian radii of these three galaxies are: 2.99”, 2.63” and 2.89”, corresponding to a
physical Petrosian diameter about 15 kpc.



**2.2** **APEX/SEPIA** **Band-5** **observations**


SEPIA Band-5 is a spectrograph that covers the frequency
range 159-211 GHz, recently mounted at the Atacama
Pathfinder Experiment (APEX). The water absorption line
at 183 GHz is the main feature of the atmosphere at these
frequencies. SEPIA Band-5 is the only instrument that is
able to detect CO ( _J_ = 2–1) at redshifts from 0.1 to
0.2 in the Southern hemisphere. We were awarded 21hrs
of APEX/SEPIA Band-5 observations to target the CO
( _J_ = 2–1) emission of 24 starburst galaxies (APEX programs 097.F-9724(A); 098.F-9712(B), PI: E. Ibar). Each target’s exposure time was about 40min, reaching an rms of
about 0.5 mK at 111 km/s channel width. The measured


MNRAS **000**, 1–9 (2017)



precipitable water vapour during the observations was about
0.8 (in a range between 0.6 and 1.2). The APEX/SEPIA
Band-5 data were reduced with CLASS software Version
1.1. For every target, we trimed the edge (about 3%) of the
spectrum and subtracted the baseline by using a first-order
polynomial. Fig. 2 shows the CO line observations: 16 galaxies have S/N _>_ 3 and were fitted by single Gaussian profile
(the top 12 spectra in Fig. 2 have S/N _>_ 5). 8 galaxies have
no CO detection down to 5 _σ_ in the APEX spectra. In Fig. 2
we also show the SDSS postage image of each target in the
upper-left corner of the CO spectrum.

4 _C._ _Cheng_ _et_ _al._


**Figure** **2.** **continued** : the first 4 targets have lower S/N between 3 and 5. We also fit the CO emission by a single Gaussian profile and
show the result as a red line. The final 8 galaxies have no clear CO emission.



**2.3** **Galaxy** **Sample** **over** 0 _._ 1 _< z_ _<_ 0 _._ 2 **for** **this** **study**


We have combined these new SEPIA Band-5 observa
tions to the VALES sample. We select the 16 galaxies
with APEX/SEPIA Band-5 detections together with the 17
galaxies previously detected by ALMA and shown by Villanueva et al (2017) in the same redshift range. These 33
galaxies between 0 _._ 1 _<_ _z_ _<_ 0 _._ 2 lie in the grey shaded region of Fig. 1. The cosmological timescale within this redshift range ∆ _z_ (0 _._ 1 _−_ 0 _._ 2) is about 1 Gyr, which is about
the typical gas depletion timescale of normal SFGs. Thus
the cosmological evolution of the galaxies in this sample can
be neglected for normal galaxies, although many starburst
cycles could be expected for more active galaxies.
Based on the visual inspection of SDSS images of the
16 APEX galaxies, we identify 7 possibly interacting (mergers) and 9 isolated galaxies. On the other hand, the 17
ALMA CO-detected galaxies include 3 mergers and 14 isolated galaxies. The stellar masses are derived using MAGPHYS (da Cunha et al. 2008) while the SFR( _M_ _⊙_ _/_ yr) =



10 _[−]_ [10] _L_ IR _/L_ _⊙_ (Villanueva et al. 2017) using the _L_ IR (8 _−_
1000 _µ_ m) derived from fitting the broad-band far-IR photometry (assuming a Chabrier IMF, Chabrier2003). We follow the same procedure to derive galaxy properties as Villanueva et al. (2017). We list the main properties of the
APEX observed targets in Table 1. For the targets with no
CO detection, we list the upper limit (5 _σ_ ) of the CO flux.


**3** **RESULTS**


We define SFE _[′]_ = SFR _/L_ CO _[′]_ [and present the observed][ SFE] _[′]_

vs _L_ IR in Fig. 3. The _L_ _[′]_ CO [=] _[L]_ _[′]_ CO ( _J_ =1–0) [is] [defined] [as]
(Solomon & Vanden Bout 2005):


_L_ _[′]_ CO ( _J_ =1–0) [= 3] _[.]_ [25] _[×]_ [10] [7] _[S]_ [CO] [∆] _[v ν]_ obs _[−]_ [2] _[D]_ L [2] [(1+] _[z]_ [)] _[−]_ [3] [[K km s] _[−]_ [1] [ pc] [2] []] _[,]_

(1)


where _S_ CO ∆ _v_ is the velocity-integrated flux density in units
of Jy km s _[−]_ [1], _ν_ obs is the observed frequency of the emission


MNRAS **000**, 1–9 (2017)

_Transition_ _in_ _galaxy_ _star_ _formation_ _efficiency_ 5


**Figure** **3.** The SFE _[′]_ (= SFR _/L_ _[′]_ CO [)] [vs] _[L]_ [IR] [of] [our] [CO] [detected] [sample] [(blue] [and] [red] [dots);] [the] [VALES] [sample] [(purple/blue/red] [dots);]
local spirals (green stars; Leroy et al. 2009) and the local ULIRGs (orange cirlcles; Solomon et al. 1997). The top label shows the SFR
scale. The _L_ IR is derived from the _Herschel_ data fitting as described in Villanueva et al. (2017). The right Y-axis is the gas depletion
time-scale normalised by _α_ CO . The SFE _[′]_ is nearly constant with 0.5 dex scatter at the IR luminosities between 2 _×_ 10 [9] _L_ _⊙_ and _×_ 10 [11] _L_ _⊙_ .
When galaxies are far-IR bright ( _L_ IR _>_ 10 [11] _L_ _⊙_ ), the SFE tend to increase (see Equation 2).


line in GHz, _D_ L is the luminosity distance in Mpc and _z_ is
the redshift. We assume a _L_ CO ( _J_ =2–1) _/L_ CO ( _J_ =1–0) ratio as
0.85, although we reckon this may vary from 0.5 to 1 for
different source cases (Carilli and Walter 2013). We expect
this systematic variation will affect our result by 0.3 dex at

most.
For the “normal” galaxies at 2 _×_ 10 [9] _<_ _L_ IR _<_ 10 [11] _L_ _⊙_,
the SFE _[′]_ is roughly constant with scatter of about 0.5 dex, so
the SFR and the cold molecular gas mass are roughly proportional to each other (Villanueva et al. 2017). The constant
SFE _[′]_ indicates that the gas of the normal spiral galaxies is
just enough to maintain a long depletion time scale.
We fit the scaling relation between SFE _[′]_ and IR luminosity for all the _L_ IR _>_ 10 [11] _L_ _⊙_ galaxies from the VALES including our new SEPIA band-5 detections and local ULIRGs
taken from Solomon et al. (1997):



0 _._ 71 _±_ 0 _._ 01

_._ (2)
�



**Figure** **4.** The effective _α_ CO estimate using different methods: the solid circles stand for the method of _M_ H 2 = _α_ CO _L_ _[′]_ CO
( _α_ CO = 0 _._ 8 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for the mergers and _α_ CO =
4 _._ 6 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for the isolated galaxies); the open triangles stand for the method of _M_ H 2 = _δM_ dust assuming the
_δ_ = 100. The ALMA data at 0.1 _<z<_ 0.2 are represented by blue
markers and those outside the range by purple ones.


MNRAS **000**, 1–9 (2017)



10SFE _[−]_ [9] yr _[′][−]_ [1] [= (2] _[.]_ [8] _[ ±]_ [ 0] _[.]_ [9)] _[ ×]_ � 10 _L_ [11] IR _L_ _⊙_



The quantities SFE _[′]_ and _L_ IR in Eq. 2 are not independent from each other, nevertheless, this scaling relation can
help us to estimate the CO luminosity of low- _z_ LIRGs and
ULIRGs.
Previous studies (Magdis et al. 2014; Sargent et al.
2014) have shown that the SFE _[′]_ of the spirals and ULIRGs

6 _C._ _Cheng_ _et_ _al._


**Figure** **5.** The SFE vs _L_ IR relation. The colour and symbol codes are the same as Fig. 3. We estimate the _M_ H 2 with two methods:
assuming an _α_ CO that depends on the optical morphology (solid circles) and considering a simple gas to dust mass ratio (solid squares).
We adopt the _α_ CO = 4 _._ 6 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for the isolated galaxies and _α_ CO = 0 _._ 8 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for the merging galaxies to
derive the _M_ H 2 from _L_ _[′]_ CO [,] [as] [in] [previous] [papers] [of] [the] [VALES] [series.] [The] _[H]_ [-ATLAS] [data] [allow] [deriving] [the] [galaxy] [dust] [masses,] [which]
can be converted into H 2 mass by assuming the gas-dust ratio _δ_ = _M_ gas _/M_ dust = 100 (Magdis et al. 2012). Typical values for _δ_ are in
the range of 50 to 150, which can be affect the range of _M_ H 2 by 0.3 dex. The SFE of the APEX data nicely bridge the gap between the
normal star forming local galaxies and the local ULIRGs. The shaded region corresponds to that where the SFE transitions occurs.



sample in Fig. 3 are consistent with the CO emission surveys
at _z_ _<_ 0 _._ 3, e.g., COLDGASS, EGNoG and PHIBSS. So we
restrict the sample shown in Fig. 3 to spirals and ULIRGs
for clarity. The SFE _[′]_ in Fig. 3 changes smoothly with the IR
luminosity. We do not see a clear separation of SFR modes
(Daddi et al. 2010). We note that our LIRG sample bridges
the parameter space between the normal SFGs and the local
powerful ULIRGs.


**4** **DISCUSSION**


**4.1** **The** **origin** **of** **the** **SFE** **scatter**


To understand the true SFE distribution of our sample, we
need to tackle the molecular gas content. We use the _M_ H 2 =
_α_ CO _L_ _[′]_ CO [relation as the primary estimator. To maintain con-]
sistency with previous VALES papers in this series, we follow the choice of _α_ CO based on the optical SDSS morphology
as in Villanueva et al. (2007): _α_ = 0 _._ 8 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1]

for merger systems and _α_ = 4 _._ 6 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for isolated disky or bulgy galaxies (Solomon & Vanden Bout 2005;
Bolatto et al. 2013).
The H 2 mass can also be estimated from the gas-to


dust ratio. We assume a constant gas-to-dust ratio _δ_ =
_M_ gas _/M_ dust = 100 (Magdis et al. 2012) where _M_ dust is derived from the MAGPHYS fits. The typical range of the
_M_ dust _∼_ 10 [7] _[.]_ [5] _[−]_ [8] _[.]_ [6] _M_ _⊙_ and the results are listed in Table 1.
The results are illustrated in Fig. 4. Observationally, a typical range of the _δ_ is from about 50 to 150 (Magdis et al.
2012), hence this can change the _M_ H 2 _/L_ CO _[′]_ [from] [0.5] [to] [1.5]
times of the current value. As an independent approach of
estimating the molecular mass, the gas-to-dust ratio method
shows a good agreement with the _α_ CO _L_ _[′]_ CO [estimations] [(see]
also Hughes et al. 2017b).


The SFE results are illustrated in Fig. 5. In this figure, we identify two populations of SFGs: one as an extension of the “main sequence” galaxies with higher SFRs
up to _L_ IR _∼_ 10 [11] _[.]_ [5] _L_ _⊙_ ; the other population has SFE between the “main sequence” and ULIRGs with a clear trend
towards high SFE at higher _L_ IR . The SFE based on the gasto-dust ratio method suggests a population filling the parameter space between the normal spirals and ULIRGs (Fig.
5). Our observations reveal the existence of a wide range of
SFE (specially between _L_ IR _≃_ 10 [11] _[−]_ [12] _L_ _⊙_ ), combining both
star-formation modes: “disk-like” and “starburst” features.


Looking at the scatter of the correlation in Fig. 5, we


MNRAS **000**, 1–9 (2017)

**Figure** **6.** . The radius versus the SFR _/M_ gas [1] _[.]_ [4] [for] [all] [the] [ALMA]
resolved galaxies and the APEX targets. The SFR _/M_ gas [1] _[.]_ [4] [shows] [a]
monotonic relation with SFE. For the ALMA resolved galaxies,
the slope of the correlation is about -0.6 _±_ 0.04. We also show the
-0.8 slope as a dashed line, which is expected from the KennicuttSchmidt law. We do not have enough resolution for the APEX
targets’ CO radius ( _R_ CO ), so we use their SDSS _r_ band Petrosian
radii/1.6 instead (Villanueva et al. 2017). The orange dots show
the lower limits of the radii of ULIRGs sample of the Solomon et
al. (1997).


**Figure** **7.** The SFR-SFE relation as shown in Fig. 11 in Sargent et al. (2014). We employ the normal galaxies case Eq. 4 in
Sargent et al. (2014) to derive the SFE/SFE ms Here we only plot
the representative samples in Sargent et al. (2014) and we show
their result by thick line as well as the uncertainty by the shaded
region. The VALES (blue and purple bullets) and APEX (red
bullets) samples show a large range along the sSFR/sSFR ms and
they are not only consistent with the local normal SFGs at the
low sSFR/sSFR ms end but also transition smoothly between the
normal SFGs and the ULIRGs.


find that the SFE should be anti-correlated with the galaxy
gas radius [2] . Fig. 6 shows the ALMA resolved CO radius


2 The Schmidt-Kennicutt law follows Σ SFR _∝_ Σ 1gas _._ 4 [.] [If] [we] [make]
the rough assumption that the SFR _≃_ Σ SFR _R_ [2] and _M_ gas _≃_
Σ gas _R_ [2], then the Σ SFR _R_ [2] _∝_ Σ [1] gas _[.]_ [4] _[R]_ [2] _[.]_ [8] _[R]_ _[−]_ [0] _[.]_ [8] [.] [So] [SFR] _[/M]_ gas [1] _[.]_ [4] _[∝]_
_R_ _[−]_ [0] _[.]_ [8] . Since the SFR _/M_ gas [1] _[.]_ [4] [is] [monotonic] [with] [SFE,] [if] [the]


MNRAS **000**, 1–9 (2017)



_Transition_ _in_ _galaxy_ _star_ _formation_ _efficiency_ 7


( _R_ CO ) against the SFR _/M_ gas [1] _[.]_ [4] [,] [which] [highlights] [the] [impor-]
tance of the _R_ CO in controlling the SFE. For the more normal SFGs (resolved by ALMA at 3.5”), we find that the
physical sizes of the CO emitting regions tend to be larger for
lower SFE, while compact CO emtters tend to have higher
SFE. For all of the LIRGs observed by APEX (unresolved
in CO), we use the SDSS _r_ band Petrosian radius to estimate the _R_ CO _≃_ _R_ r _/_ 1 _._ 6 following Villanueva et al (2017)
and show the results in Fig. 6. We find that all of the APEX
targets have similar CO radii, which is mainly caused by the
narrow redshift range and the limited spatial resolution of
SDSS.
For normal SFGs, the main sequence shows SFR _∼_ _M_ _∗_ _[β]_ [,]
where _β_ _≃_ 0 _._ 6 for local galaxies (Brinchmann et al. 2004).
The typical gas fractions ( _f_ g = _M_ H 2 _/_ ( _M_ _∗_ + _M_ H 2 )) of local
galaxy samples are of about 10% (Narayanan et al. 2012b). If
the SFR _∝_ _L_ IR, then the combination of these three relations

_β−_ 1

will result in _SFE_ _∝_ (1 _/f_ g _−_ 1) _L_ IR _β_ . The _β_ index describes

the slope of the SFE and _L_ IR relation while the _f_ g accounts
for the Y-axis intercept (the green lines in Fig. 5).
Finally, considering that APEX measured the total CO
flux within a primary beam of _∼_ 35” at _∼_ 200GHz, which is
larger than the typical size of a _z_ _∼_ 0 _._ 1 galaxy, in the case of
merging systems, close counterparts may also contribute to
the CO flux. This may be the case, for example, of HATLAS
J121005.9+002639 where we see a possible broadening of the
CO line emission. This broadening could be due to a close
counterpart which is at the same redshift, as seen in Fig. 2.
We also note that parameters such as _M_ _∗_ could be affected
too. Nevertheless, we estimate that the total stellar mass
within the 35” is no more than _∼_ 2 times larger than the
stellar mass of the central galaxy. Thus the stellar mass will
not significantly affect the main trends we find in our data.


**4.2** **Confronting** **the** **bimodality** **in** **star** **formation**
**efficiencies**


Previous studies have shown that the SFE in SFGs follow a
bimodal behaviour for normal and starburst galaxies (Daddi
et al. 2010; Genzel et al. 2010). Based on the existence
of the ‘main sequence’ followed by normal SFGs, Sargent
et al. (2014) show that this bimodal SFE can be nicely
illustrated by plotting SFE/SFE ms versus sSFR/sSFR ms,
where SFE/SFE ms is the SFE normalised by the SFE of
the main sequence or strongly starbursting galaxies with the
same mass. In Fig. 7 we show our VALES (including the
new APEX/SEPIA Band-5 detections) sample in comparison with other samples taken from the literature, overplotted
over the predictions (solid line) by Sargent et al. (2014). We
find that the steep jump in SFE at sSFR/sSFR ms _>_ 3 is not
as clean as expected. We highlight that our sample covers
a much wider range of sSFRs, with IR luminosities in the
LIRGs range in between of those normal (HERACLES and
COLDGASS) and local ULIRGs. Indeed, it is evident that
Sargent et al. (2014)’s predictions are significantly affected
by low number statistics of the most strongly starbursting
galaxies (specially at sSFR/sSFR ms _>_ 3). Our study clearly
shows that the most ‘starbursty’ galaxies (see VALES range


Kennicutt-Schmidt law is valid for all the galaxies, galaxies with
small gas radii would have higher SFE.

8 _C._ _Cheng_ _et_ _al._


**Table** **1.** Parameters of the APEX Observed CO (2-1) detected targets.


HATLAS ID GAMAID _z_ spec log( _M_ _∗_ _/M_ _⊙_ ) log( _L_ _[′]_ CO [[][Kkm s] _[−]_ [1] [p][c] [2] [])] log( _L_ IR _/L_ _⊙_ ) log( _M_ dust _/M_ _⊙_ ) CO FWHM km/
HATLAS J114039.1-001821 53812 0.1128 10.50 _±_ 0.03 9.70 _±_ 0.09 11.29 _±_ 0.01 8.00 _±_ 0.06 304 _±_ 59

HATLAS J115447.6+012825 219701 0.1497 10.57 _±_ 0.02 9.74 _±_ 0.12 11.86 _±_ 0.02 7.99 _±_ 0.04 233 _±_ 52

HATLAS J115849.9-013146 185275 0.1468 10.37 _±_ 0.03 10.13 _±_ 0.10 11.54 _±_ 0.03 8.03 _±_ 0.03 1102 _±_ 309

HATLAS J120541.4-001420 55305 0.1763 10.20 _±_ 0.03 9.74 _±_ 0.16 11.88 _±_ 0.03 8.44 _±_ 0.03 301 _±_ 60

HATLAS J121005.9+002639 85450 0.1280 10.93 _±_ 0.03 10.04 _±_ 0.06 11.65 _±_ 0.03 8.32 _±_ 0.05 535 _±_ 81

HATLAS J141727.5-002535 568216 0.1226 10.86 _±_ 0.11 9.93 _±_ 0.06 11.51 _±_ 0.02 8.23 _±_ 0.04 354 _±_ 54

HATLAS J142225.2+002649 92214 0.1130 10.53 _±_ 0.03 9.49 _±_ 0.15 11.33 _±_ 0.03 8.07 _±_ 0.06 _<_ 185 _±_ 66

HATLAS J142727.3-005842 544759 0.1623 10.80 _±_ 0.03 10.35 _±_ 0.08 12.14 _±_ 0.05 8.57 _±_ 0.02 375 _±_ 69

HATLAS J142831.9-003636 568985 0.1037 9.80 _±_ 0.12 10.07 _±_ 0.09 11.23 _±_ 0.02 8.24 _±_ 0.06 526 _±_ 137

HATLAS J142948.7+010822 228482 0.1601 10.35 _±_ 0.05 9.95 _±_ 0.15 11.50 _±_ 0.01 8.06 _±_ 0.06 504 _±_ 167

HATLAS J143155.0-005701 545019 0.1217 11.05 _±_ 0.02 9.91 _±_ 0.08 11.62 _±_ 0.03 8.15 _±_ 0.05 450 _±_ 120

HATLAS J143334.2-012559 492771 0.1600 10.37 _±_ 0.03 9.80 _±_ 0.10 11.67 _±_ 0.02 8.05 _±_ 0.04 347 _±_ 88

HATLAS J143953.4+000618 79073 0.1321 10.84 _±_ 0.06 9.49 _±_ 0.17 11.35 _±_ 0.01 8.36 _±_ 0.07 275 _±_ 112

HATLAS J144331.1-001624 64970 0.1417 10.25 _±_ 0.07 9.88 _±_ 0.11 11.34 _±_ 0.01 7.90 _±_ 0.04 810 _±_ 223

HATLAS J144749.4+020209 343741 0.1193 11.05 _±_ 0.10 9.76 _±_ 0.09 11.36 _±_ 0.01 8.09 _±_ 0.10 329 _±_ 62

HATLAS J145008.3+015159 252158 0.1134 10.92 _±_ 0.02 9.79 _±_ 0.08 11.59 _±_ 0.02 8.02 _±_ 0.03 355 _±_ 60

HATLAS J120827.2+005704 99268 0.1591 11.09 _±_ 0.02 _<_ 7.60 11.73 _±_ 0.01 8.30 _±_ 0.03 _−−_

HATLAS J142253.3+014355 319750 0.1104 10.33 _±_ 0.03 _<_ 7.23 11.24 _±_ 0.05 7.83 _±_ 0.04 _−−_

HATLAS J113842.6-023316 123041 0.1050 10.73 _±_ 0.09 _<_ 7.28 11.19 _±_ 0.04 7.85 _±_ 0.05 _−−_

HATLAS J121258.7-012123 145195 0.1042 10.67 _±_ 0.02 _<_ 7.14 11.18 _±_ 0.02 7.89 _±_ 0.04 _−−_

HATLAS J122104.3+000506 71574 0.1071 9.915 _±_ 0.03 _<_ 7.26 11.19 _±_ 0.04 7.75 _±_ 0.05 _−−_

HATLAS J114244.3-005450 534898 0.1076 9.940 _±_ 0.03 _<_ 7.35 11.03 _±_ 0.06 7.79 _±_ 0.06 _−−_

HATLAS J142128.2+014845 319694 0.1604 10.34 _±_ 0.04 _<_ 7.61 11.21 _±_ 0.02 8.41 _±_ 0.11 _−−_

HATLAS J121623.4+010614 24056 0.1552 9.298 _±_ 0.10 _<_ 7.40 10.72 _±_ 0.03 8.49 _±_ 0.10 _−−_



in Fig. 1) present a wide range of SFEs, i.e. not all galaxies
with high sSFR are passing through a dominant starburst
phase. As shown in Fig. 3, there is a smooth transition of
SFEs as a function of IR luminosities, in contradiction with
a bimodal behaviour.

Our evidende is also supported by a recent study
by Lu et al. (2017), using local LIRGs, that shows a
similarly smooth transition in SFEs as analysed by the

[CI]370 _µ_ m/CO(7-6) and C(60 _µ_ m/100 _µ_ m) ratios (Fig. 17,
panel c in their paper). Here we will consider the CO(7-6)
as a proxy for the SFR and [CI]370 _µ_ m for the _M_ H 2 (Jiao et
al. 2017). Lu et al. (2017) suggest that the change in effective
SFE could be correlated to the far-IR colour, i.e. the dust
temperature. On the other hand, a smooth transition of the
SFE is also found by the recent study by Lee et al. (2017)
using a sample of 20 intermediate redshift (0 _._ 25 _< z_ _<_ 0 _._ 65)
LIRGs in the Cosmological Evolution Survey (COSMOS).
We conclude that our findings are consistent with previous
studies of LIRGs at low- and intermediate-redshifts.

We have identified different parameters responsible for
the observed scatter of the SFE in SFGs, nevertheless the
only parameter which most probably causes the appearance
of a bimodal behaviour comes from the bimodal assumption
of the _α_ CO conversion factor. It is well known that _α_ CO is
dependent on the physical properties of the ISM (e.g. metallicity, density, temperature; Solomon & Vanden Bout 2005),
so that making a global assumption for a single _α_ CO value
over the whole galaxy can be significantly affected by complex systematical uncertainties (e.g. Sandstrom et al. 2013).


**5** **CONCLUSION**


Our new APEX/SEPIA Band-5 observations double the
number of sources with CO detections in the ALMA-based

VALES sample at 0 _._ 1 _<_ _z_ _<_ 0 _._ 2, specially covering the pa


rameter space at higher sSFR. In this work we concentrate
in an investigation of the global star formation efficiency
of CO-detected galaxies, including previous low-z surveys
taken from the literature. To avoid the uncertainties on the

_α_ CO conversion factor, we explore the correlation between
the SFR _/L_ CO _[′]_ [ratio] [and] [the] [IR] [luminosity.] [We] [find] [that]
this ratio remains relatively constant up to _L_ IR _∼_ 10 [11] _L_ _⊙_
(a scatter of _∼_ 0.5 dex), although above this value there
is a clear increment in the effective SFE. Benefited by the
large sSFR/sSFR ms of our VALES and APEX sample, we
find a smooth transition of the SFE instead of a steep jump
from the normal SFGs to the ULIRGs. The smooth increment as a function of far-IR luminosity (specially between
10 [11] _[−]_ [12] _L_ _⊙_ ) is consistent with the previous LIRGs study (Lu
et al. 2017; Lee et al. 2017). This suggests that the dominating star-formation mechanism (starburst or disk-like)
smoothly changes between powerful ULIRGs and normal
galaxies. We conclude that the main parameters controlling
the scatter of the global SFE versus LIR correlation are:
the assumed _α_ CO conversion factor, the gas fraction and the
physical size of the galaxies.


**ACKNOWLEDGEMENTS**


This paper benefited from a number of thoughtful comments made by the anonymous referee. This work was
support from the Chinese Academy of Sciences (CAS)
through the CASSACA Postdoc Grant and the Visiting
Scholarship Grant administered by the CAS South America Center for Astronomy (CASSACA), NAOC. E.I. and
T.M.H. acknowledge the CONICYT/ALMA funding Program in Astronomy/PCI Project N _[◦]_ : 31140020. E.I. acknowledges partial support from FONDECYT through
grant N _[◦]_ 1171710. T.M.H. acknowledges the support from
the Chinese Academy of Sciences (CAS) and the National


MNRAS **000**, 1–9 (2017)

Commission for Scientific and Technological Research of
Chile (CONICYT) through a CAS-CONICYT Joint Postdoctoral Fellowship administered by the CAS South America Center for Astronomy (CASSACA) in Santiago, Chile.
R.L. acknowledges the support from Comit´e Mixto ESOGOBIERNO DE CHILE and GEMINI-CONICYT FUND

32130024. G.O. acknowledges the support provided by CONICYT (Chile) through FONDECYT postdoctoral research
grant no 3170942. C.K.X. acknowledges the support of
NSFC-11643003. N.L. acknowledges the support by the
NSFC grant #11673028 and by the National Key R&D
Program of China grant #2017YFA0402704. Y.Q.X. acknowledges the support of NSFC-11473026 and 11421303.
This publication is based on data acquired with the Atacama Pathfinder Experiment (APEX). APEX is a collaboration between the Max-Planck-Institut fur Radioas
tronomie, the European Southern Observatory, and the Onsala Space Observatory. This paper makes use of the following ALMA data: ADS/JAO.ALMA 2012.1.01080.S &
ADS/JAO.ALMA 2013.1.00530.S. ALMA is a partnership
of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), NSC and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.


**REFERENCES**


Armus, L. et al. 2009, PASP, 121, 559
Bauermeister A., et al., 2013, ApJ, 768, 132
Billade, B., 2012, IEEE Trans. Terahertz Science and Technology,
2, 208
Bolatto, A. D.; Wolfire, M.; Leroy, A. K. 2013, ARA&A, 51, 207
Brinchmann, J., et al. 2004, MNRAS, 351, 1151
Combes F., et al., 2011, A&A, 528, A124
Combes F., et al., 2013, A&A, 550, A41
Combes F., the PHIBSS collaboration, 2016, IAUS, 315, 240C
Costagliola et al. 2013, A&A 556, 66
Carilli, C. L.; Walter, F. 2013, ARA&A, 51, 105
Chabrier G., 2003, ApJ, 586, L133
da Cunha, E.; Charlot, S.; Elbaz, D. 2008, MNRAS, 388, 1595D
Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJ, 714, L118
Downes, D.; Solomon, P. M. 1998, ApJ, 507, 615
Driver, Simon P., et al. 2016, MNRAS, 455, 3911
Eales, S., et al. 2010, PASP, 122, 499C
Elbaz, D., et al. 2011, A&A, 533, 119
Genzel, R., et al. 2010, MNRAS, 407, 2091
Genzel, R., et al. 2015, ApJ, 800, 20
Hughes, T. M., et al. 2017a, A&A, 602, 49
Hughes, T. M., et al. 2017b, MNRAS, 468L, 103
Jiao, Qian et al. 2017, ApJL, 840, 18
Lee, N. et al. 2017, MNRAS, 471, 2124
Leroy A. K., et al., 2009, AJ, 137, 4670
Lonsdale, C. J., Farrah, D., & Smith, H. E. 2006, Astrophysics
Update 2 (Chichester: Springer Praxis), 285
Lu, Nanyao et al. 2017, ApJS, 230, 1
Magdis, Georgios E., et al. 2014, ApJ, 796, 63M
Magdis, Georgios E., et al. 2012, ApJ, 760, 6
Narayanan, D., et al. 2011, MNRAS, 418, 664
Narayanan, D., et al. 2012a, MNRAS, 421, 3127N
Narayanan, D.; Bothwell, M.; Dav´e, R., 2012b, MNRAS, 426,

1178N

Papadopoulos, Padelis P., et al., 2012a, MNRAS, 426, 2601
Papadopoulos, Padelis P., et al., 2012b, ApJ, 751, 10P


MNRAS **000**, 1–9 (2017)



_Transition_ _in_ _galaxy_ _star_ _formation_ _efficiency_ 9


Papadopoulos, Padelis P.; Thi, Wing-Fai, 2013, ASSP, 34, 41P
Saintonge A., et al., 2011, MNRAS, 415, 32
Sandstrom, K. M., et al. 2013, ApJ, 777, 5S
Sargent, M. T., et al., 2014, ApJ, 793, 19
Schawinski, Kevin, et al. 2014, MNRAS, 440, 889S
Schreiber, C. et al. 2015, A&A, 575, 74
Sliwa, Kazimierz, et al. 2013, ApJ, 777, 126
Solomon P. M., et al., 1997, ApJ, 478, 144
Solomon, P. M.; Vanden Bout, P. A. 2005, ARA&A, 43, 677
Speagle, J. S. et al. 2014, ApJS, 214, 1
Tunnard, R. et al., ApJ, 815, 114
Valiante E., et al., 2016, MNRAS, 462, 3146
Villanueva et al. 2017, MNRAS, 470, 3775V
Whitaker, Katherine E., et al. 2012, ApJ, 754, 29
Xu, C. K., et al. 2014, 787, 48
Xu, C. K., et al. 2015, ApJ, 799, 11
Yao, L., Seaquist, E. R., Kuno, N., & Dunne, L. 2003, ApJ, 588,

771


This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.


</paper>

## Items to check

```json
[
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "H-ATLAS DR1 catalog public; ALMA projects cited",
  "failed_quote": "Making use of the public H -ATLAS DR1 catalog"
 }
]
```
