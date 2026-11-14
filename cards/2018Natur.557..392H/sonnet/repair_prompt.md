# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018Natur.557..392H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## The onset of star formation 250 million years after the Big **Bang**

Takuya Hashimoto _[∗][,]_ [1] _[,]_ [2], Nicolas Laporte [3] _[,]_ [4], Ken Mawatari [1], Richard S. Ellis [3], Akio. K. Inoue [1],


Erik Zackrisson [5], Guido Roberts-Borsani [3], Wei Zheng [6], Yoichi Tamura [7], Franz E. Bauer [8] _[,]_ [9] _[,]_ [10],


Thomas Fletcher [3], Yuichi Harikane [11] _[,]_ [12], Bunyo Hatsukade [13], Natsuki H. Hayatsu [12] _[,]_ [14], Yuichi


Matsuda [2] _[,]_ [15], Hiroshi Matsuo [2] _[,]_ [15], Takashi Okamoto [16], Masami Ouchi [11] _[,]_ [17], Roser Pell´o [4], Claes-Erik


Rydberg [18], Ikkoh Shimizu [19], Yoshiaki Taniguchi [20], Hideki Umehata [13] _[,]_ [20] _[,]_ [21], Naoki Yoshida [12] _[,]_ [17]


1 _Department_ _of_ _Environmental_ _Science_ _and_ _Technology,_ _Faculty_ _of_ _Design_ _Technology,_ _Osaka_


_Sangyo University, 3-1-1, Nagaito, Daito, Osaka 574-8530, Japan_


2 _National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan_


3 _Department of Physics & Astronomy, University College London, Gower Street, London WC1E_


_6BT, UK_


4 _IRAP, Universit´e de Toulouse, CNRS, UPS, CNES, 14, avenue Edouard Belin, F-31400 Toulouse,_


_France_


5 _Department of Physics and Astronomy, Uppsala University, Box 516, SE-751 20 Uppsala, Swe-_


_den_


6 _Department of Physics & Astronomy,_ _Johns Hopkins University,_ _3400 N Charles St,_ _Baltimore,_


_MD 21218 USA_


7 _Division of Particle and Astrophysical Science, Graduate School of Science, Nagoya University,_


_Furo-cho, Chikusa-ku, Nagoya 464-8602,Japan_


8 _Instituto de Astrof´ısica and Centro de Astroingenier´ıa, Facultad de F´ısica, Pontificia Universidad_


1

_Cat´olica de Chile, Casilla 306, Santiago 22, Chile_


9 _Millennium_ _Institute_ _of_ _Astrophysics_ _(MAS),_ _Nuncio_ _Monse˜nor_ _S´otero_ _Sanz_ _100,_ _Providencia,_


_Santiago, Chile_


10 _Space Science Institute, 4750 Walnut Street, Suite 205, Boulder, Colorado 80301_


11 _Institute_ _for_ _Cosmic_ _Ray_ _Research,_ _The_ _University_ _of_ _Tokyo,_ _5-1-5_ _Kashiwanoha,_ _Kashiwa,_


_Chiba 277-8582, Japan_


12 _Department_ _of_ _Physics,_ _Graduate_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_


_Bunkyo, Tokyo, 113-0033, Japan_


13 _Institute of Astronomy, The University of Tokyo, 2-21-1 Osawa, Mitaka, Tokyo 181-0015, Japan_


14 _European Southern Observatory, Karl-Schwarzschild-Str._ _2, 85748 Garching bei M¨unchen, Ger-_


_many_


15 _Department of Astronomical Science, School of Physical Sciences, The Graduate University for_


_Advanced Studies (SOKENDAI), 2-21-1, Osawa, Mitaka, Tokyo 181-8588, Japan_


16 _Department_ _of_ _Cosmosciences,_ _Graduates_ _School_ _of_ _Science,_ _Hokakido_ _University,_ _N10_ _W8,_


_Kitaku, Sapporo 060-0810, Japan_


17 _Kavli Institute for the Physics and Mathematics of the Universe (WPI), Todai Institutes for Ad-_


_vanced Study, The University of Tokyo, 5-1-5 Kashiwanoha, Kashiwa, Chiba 277-8583, Japan_


18 _Universit¨at Heidelberg, Zentrum f¨ur Astronomie, Institut f¨ur Theoretische Astrophysik, Albert-_


_Ueberly-Str._ _2, D-69120 Heidelberg, Germany_


19 _Theoretical_ _Astrophysics,_ _Department_ _of_ _Earth_ _&_ _Space_ _Science,_ _Osaka_ _University,_ _1-1_


_Machikaneyama, Toyonaka, Osaka 560-0043, Japan_


2

20 _The Open University of Japan, 2-11 Wakaba, Mihama-ku, Chiba 261-8586, Japan_


21 _The_ _Institute_ _of_ _Physical_ _and_ _Chemical_ _Research_ _(RIKEN),_ _2-1_ _Hirosawa,_ _Wako-shi,_ _Saitama_


_351-0198, Japan_


**A** **fundamental** **quest** **of** **modern** **astronomy** **is** **to** **locate** **the** **earliest** **galaxies** **and** **study** **how**


**.**
**they influenced the intergalactic medium a few hundred million years after the Big Bang** **[1–3]**


**The** **abundance** **of** **star-forming** **galaxies** **is** **known** **to** **decline** **[4,5]** **from** **redshifts** **of** **about** **6** **to**


**10, but a key question is the extent of star formation at even earlier times, corresponding to**


**the period when the first galaxies might have emerged.** **Here we present spectroscopic obser-**


**vations of MACS1149-JD1** **[6]** **, a gravitationally lensed galaxy observed when the Universe was**


**less than four per cent of its present age.** **We detect an emission line of doubly ionized oxygen**


**at a redshift of 9.1096** _±_ **0.0006, with an uncertainty of one standard deviation.** **This precisely**


**determined redshift indicates that the red rest-frame optical colour arises from a dominant**


**stellar component that formed about 250 million years after the Big Bang, corresponding to a**


**redshift of about 15.** **Our results indicate the it may be possible to detect such early episodes**


**of star formation in similar galaxies with future telescopes.**


Between March 2016 and April 2017 we performed observations of MACS1149-JD1 at the


Atacama Large Millimeter/submillimeter Array (ALMA), targeting the far-infrared oxygen line,


[O III ] 88 _µ_ m, and dust continuum emission over a broad wavelength range consistent with its


photometric redshift range ( _z_ = 9 _._ 0 _−_ 9 _._ 8) [4,7–9] . The [O III ] line is clearly detected at a redshift


_z_ = 9 _._ 1096 _±_ 0 _._ 0006 with a peak intensity 129 _._ 8 _±_ 17 _._ 5 mJy km s _[−]_ [1] beam _[−]_ [1] corresponding to the


significance level of 7 _._ 4 _σ_ (Figure 1, Table 1). The spatial location is coincident with the rest-frame


3

ultraviolet (UV) continuum emission detected by _HST_ indicating that the [O III ] line arises from


a star forming galaxy. The line has a luminosity of (7 _._ 4 _±_ 1 _._ 6) _×_ 10 [7] _×_ (10 _/µ_ ) _L_ _⊙_, where, for


the lensing magnification, we adopt a fiducial value of _µ_ = 10 (See Methods). Its full width at


half maximum (FWHM) is 154 _±_ 39 km s _[−]_ [1] representative of that seen in other high _z_ galaxies [10] .


The [O III ] emission is spatially resolved, and its deconvolved size is (0 _[′′]_ _._ 82 _±_ 0 _[′′]_ _._ 25) _×_ (0 _[′′]_ _._ 30 _±_


0 _[′′]_ _._ 14). The corresponding intrinsic size is (3 _._ 7 _±_ 1 _._ 1) _/_ _[√]_ _µ_ [kpc] _×_ (1 _._ 4 _±_ 0 _._ 9) _/_ _[√]_ _µ_ [kpc] under the


assumption that lensing effects are equal for the major and minor axes. Assuming that MACS1149

JD1 is a dispersion-dominated system, we derive the dynamical mass of (4 _±_ 3) _×_ (10 _/µ_ ) [0] _[.]_ [5] _×_ 10 [9]


_M_ _⊙_ .


No dust continuum is detected above a 3 _σ_ upper limit of _S_ _ν,_ 90 _µm_ _<_ 5 _._ 3 _×_ (10 _/µ_ ) _µ_ Jy beam _[−]_ [1],


where _S_ _ν,_ 90 _µm_ corresponds to the flux density at the rest-frame wavelength of 90 _µ_ m. For a dust


temperature _T_ d = 40 K and emissivity index _β_ d = 1 _._ 5, the total infrared luminosity is _<_ 7 _._ 7 _×_


10 [9] _×_ (10 _/µ_ ) _L_ _⊙_ after correcting the contribution of the cosmic-microwave-background (CMB) [11] .


Assuming a representative dust mass absorption coefficient [12], we derive a 3 _σ_ upper limit on the


dust mass of 5 _._ 3 _×_ 10 [5] _×_ (10 _/µ_ ) _M_ _⊙_ .


The spectral energy distribution (SED) of MACS1149-JD1 has a prominent excess signal in


the _Spitzer_ IRAC channel 2 band at 4.5 microns [6] . Previous spectroscopic studies of such ‘IRAC

excess’ sources [13–15] have claimed that such an excess likely arises from intense [O III ] 5007 A line [˚]


emission. However, the origin of the IRAC-excess of MACS1149-JD1 remained unclear due to


the inaccuracy of the photometrically estimated redshift [6,7,16] . Our precisely-determined redshift of


4

_z_ = 9 _._ 1 now rules out the [O III ] 5007 A line as the source of the excess since the line is at a wave- [˚]


length with _<_ 1% transmission in the IRAC channel 2 bandpass. Given recent evidence that [O III ]


88 _µ_ m may not be an accurate indication of the systemic velocity of distant star-forming galaxies [17],


we also present more tentative evidence for Lyman- _α_ (Ly _α_ ) emission from MACS1149-JD1 us

ing the X-shooter [18] spectrograph at the European Southern Observatory’s Very Large Telescope


using 6.5 hours of data taken between February and April 2017. A 4 _σ_ significant detection at


_λ_ = 12 _,_ 271 _._ 51 A [˚], corresponding to Ly _α_ at _z_ = 9 _._ 0942 _±_ 0 _._ 0019, provides a further valuable


constraint on the source redshift.


Our detailed analysis (see Methods) shows that strong H _β_ + [O III ] 4959 A [˚] lines in IRAC


channel 2 cannot reproduce the excess within the likely source redshift range because, for the


required young ages, the IRAC channel 1 flux would also be significantly boosted by strong nebular


continuum emission and [O II ] 3727 A line emission. [˚] Such young models are further disfavoured


given additional constraints from the measured UV continuum slope and the ALMA upper limit on


the dust attenuation. We conclude therefore, that the IRAC excess can only arise from the stellar


continuum around the Balmer break at _∼_ 4000 A. [˚]


Despite the fact MACS1149-JD1 is elongated by the effects of gravitational lensing, there


is some evidence of two components in the _HST_ image (Figure 1), so it is conceivable the IRAC


4.5 micron excess originates from a separate source. The peak of the ALMA [O III ] emission is


coincident with the brighter component (Figure 1), whereas the less well-located Ly _α_ emission


and IRAC flux could arise in either component. However, the wide wavelength coverage of the


5

SED enables us to reject the possibility that a low redshift interloper contributes to the 4.5 micron


excess (see Methods for detailed analyses).


Independently of the SED, the ALMA [O III ] emission line flux provides a valuable measure


of the star formation rate (SFR) at the epoch of observation [10,19] . To reproduce the SED and the


size of the Balmer break, it is necessary to consider star formation histories extending _≃_ 300


Myr earlier, corresponding to the onset of galaxy formation at redshifts _z_ _≃_ 15 (Figures 2 and


3). Our fiducial model has a dominant old component whose SFR declined, thereby reproducing


the Balmer break, with a much younger component which reproduces the strength of both Ly _α_


and [O III ] 88 _µ_ m emission. Although the detailed parameters of these two components cannot


be uniquely determined with the current data, we demonstrate in the Methods that a dominant


earlier phase of star formation whose activity subsequently declined is an inescapable conclusion


necessary to reproduce the Balmer break. Indeed, the bulk of the stellar mass of MACS1149-JD1


observed at _z_ = 9 _._ 1 is contributed by this early component ( _≃×_ 10 [9] _×_ (10 _/µ_ ) _M_ _⊙_, Figure 3). Its


onset at _z_ = 15 _._ 4 [+2] _−_ 2 _._ _[.]_ 0 [7] [thus represents the logical epoch of formation of MACS1149-JD1] [6] [.]


During this dominant first episode of star formation, feedback processes will likely weaken


or even terminate star formation activity, leading to a quiescent phase until a second episode when


gaseous inflow can rejuvenate star formation at _z_ = 9 _._ 1 leading to the detection of [O III ] 88


_µ_ m emission. Intense UV radiation from this early generation of massive stars may create an


ionised bubble [20–22] surrounding MACS1149-JD1 displacing the damping wing of Ly _α_ absorption


by intergalactic neutral hydrogen blueward by _≃_ 500 km s _[−]_ [1], facilitating transmission through the


6

predominantly neutral IGM. Although somewhat speculative given its tentative nature, inflowing


gas may then provide an explanation for the blueshift of Ly _α_ with respect to [O III ] 88 _µ_ m by


several hundred km s _[−]_ [1] [23,24] (see Methods).


MACS1149-JD1 is already a well-established galaxy. Although we are observing a sec

ondary episode of star formation at _z_ = 9 _._ 1, the galaxy formed the bulk of its stars at a much


earlier epoch. Our results indicate it may be feasible to directly detect the earliest phase of galaxy


formation, beyond the redshift range currently probed with _HST_, with future facilities such as


the _James_ _Webb_ _Space_ _Telescope_ . In addition, our observations demonstrate the great power of


ALMA [19] to spectroscopically identify galaxies at _z_ _>_ 9, showing that ALMA will also play a


central role in investigating the first-generation galaxies.


7

Redshift


9.17 9.15 9.13 9.11 9.09 9.07


334 335 336 337



47.0"


46.5"


46.0"


45.5"


45.0"


+22°24'44.5"



33.65s 33.60s 33.55s 11h49m33.50s


RA (J2000)



1.5


1.0


0.5


0.0



Observed frequency [GHz]


**Figure** **1** _|_ **ALMA** **[O** III **]** **contours** **and** **spectrum** **of** **MACS1149-JD1.** (a) Zoom on an _HST_ image


(F160W) with the ALMA [O III ] contours overlaid. Contours are drawn at 1 _σ_ intervals from _±_ 3 to +6 _σ_


where _σ_ = 17 _._ 5 mJy km s _[−]_ [1] beam _[−]_ [1] . Negative contours are shown by the dashed line. Ellipse at the lower


left corner indicates the synthesized beam size of ALMA. (b) ALMA [O III ] 88 _µ_ m spectrum in frequency


space with a resolution of _∼_ 42 km s _[−]_ [1] .


8

[OIII] 88 flu


Dust continuum



ퟦ


ퟤ


ퟢ


ퟧퟢ



ퟣퟢ [ퟢ]


ퟣퟢ [−ퟣ]





ퟥퟢ


ퟢ

|Rest−frame wavelength [m]|Col2|Col3|
|---|---|---|
|<br>ퟣ<br>ퟢ.ퟤ<br>ퟢ.ퟥ<br>ퟢ.ퟦ<br>ퟢ|<br>ퟣ<br>ퟢ.ퟤ<br>ퟢ.ퟥ<br>ퟢ.ퟦ<br>ퟢ|.ퟧ<br>ퟢ|
|=ퟣퟢퟢ Myr<br>ퟤ=ퟤ.ퟪ<br>Age =ퟤퟫퟢ Myr<br>young<br>old<br>total<br>a|=ퟣퟢퟢ Myr<br>ퟤ=ퟤ.ퟪ<br>Age =ퟤퟫퟢ Myr<br>young<br>old<br>total<br>a|=ퟣퟢퟢ Myr<br>ퟤ=ퟤ.ퟪ<br>Age =ퟤퟫퟢ Myr<br>young<br>old<br>total<br>a|
|Obs<br>|erved wavelength [m]<br>ퟤ<br>ퟥ<br>ퟦ<br>ퟧ<br>|erved wavelength [m]<br>ퟤ<br>ퟥ<br>ퟦ<br>ퟧ<br>|



**Figure 2** _|_ **The Spectral Energy Distribution of MACS1149-JD1.** The [O III ] flux provides a constraint on


the star formation rate at the epoch of observation, while the Spectral Energy Distribution (SED) provides


valuable evidence of its earlier star formation history. The model shown involves a burst of star formation of


duration _τ_ =100 Myr within the interval 12 ≲ _z_ ≲ 15 and reproduce the required excess flux at 4.5 _µ_ m. A


much younger component reproduces the strength of [O III ] emission observed at _z_ _≃_ 9. (a) Black squares


show the observations: F125W, F140W, and F160W data from _HST_ [7], a 2 _σ_ upper limit for the _K_ s _−_ band


from VLT/HAWK-I [16], and 3 _._ 6 _µ_ m and 4 _._ 5 _µ_ m fluxes from _Spitzer_ /IRAC [7] . Horizontal and vertical error bars


show the wavelength range of the filters and 1 _σ_ measurement uncertainties, respectively. The red solid line


9

indicates the SED model and the corresponding magnitudes are shown via yellow crosses. Blue and black


lines represent the contributions from the young and old component, respectively. (b) The black square


is the observed [O III ] emission line flux and its 1 _σ_ uncertainty, while the yellow cross indicates the model


prediction. (c) The black square shows the 2 _σ_ upper limit for the dust continuum flux density, and the yellow


cross the model prediction.


10

300


100


30


10


3


1


9.5


9


8.5


8


7.5


7


2.5



Redshift







2


1.5

|8 15 12 10|9|
|---|---|
|Obs<br>**a**||
|Obs<br>**b**||
|Obs<br>**c**<br>τ=100Myr (Fiducial)<br>τ=200Myr<br>τ=10Myr||



220 300 400 500 600


Age of the Universe [Myr]


**Figure 3** _|_ **Demonstration of how a dominant phase of early star formation is necessary to reproduce**


**the** **SED** **of** **MACS1149-JD1.** We show the star formation rate (a), stellar mass assembly (b) and Balmer


break (c) as a function of redshift for three possible models. _F_ 4500 and _F_ 3600 indicate the flux densities at


the rest-frame wavelengths of 4 _,_ 500 A and [˚] 3 _,_ 600 A, respectively. [˚] In each panel, the blue dot-dashed, green


dashed, and red solid lines correspond to the models with star formation bursts of duration 10, 100, and 200


Myr, respectively. Each is capable of reproducing the Balmer break observed at _z_ = 9 _._ 1 (shown by the black


data point). The full SED fits shown in Figure 2 corresponds to our fiducial model corresponding to a burst


of duration 100 Myr. The bulk of the stellar mass in MACS1149-JD1 observed at _z_ = 9 _._ 1 was produced


within a short period corresponding to the redshift interval 12 _< z_ _<_ 16. Further details of these models and


other assumptions are provided in the Methods.


11

**Table 1** _|_ **Properties of MACS1149-JD1.**


Parameters Values


RA 11 : 49 : 33 _._ 58


Dec +22 : 24 : 45 _._ 7


Redshift _z_ 9 _._ 1096 _±_ 0 _._ 0006

[OIII]


[O III ] line width FWHM [OIII] (km s _[−]_ [1] ) 154 _±_ 39


[O III ] luminosity _L_ [OIII] (10 [7] _L_ _⊙_ ) (7 _._ 4 _±_ 1 _._ 6) _×_ (10 _/µ_ ) _[a]_


90 _µ_ m continuum flux ( _µ_ Jy beam _[−]_ [1] ) _<_ 5 _._ 3 _×_ (10 _/µ_ ) _[a]_ (3 _σ_ )


Star formation rate ( _M_ _⊙_ yr _[−]_ [1] ) 4 _._ 2 [+0] _−_ 1 _[.]_ _._ [8] 1 _[×]_ [ (10] _[/µ]_ [)] _[a]_


Stellar mass (10 [9] _M_ _⊙_ ) 1 _._ 08 [+0] _−_ 0 _[.]_ _._ [53] 18 _[×]_ [ (10] _[/µ]_ [)] _[a]_


Dust mass (10 [5] _M_ _⊙_ ) _<_ 5 _._ 2 _×_ (10 _/µ_ ) _[a]_ (3 _σ_ ) _[b]_


Dynamical mass (10 [9] _M_ _⊙_ ) (4 _±_ 3) _×_ (10 _/µ_ ) [0] _[.]_ [5] _a,c_


Redshift _z_ Ly _α_ 9 _._ 0944 _±_ 0 _._ 0019


Velocity offset ∆ _v_ Ly _α_ (km s _[−]_ [1] ) _−_ 450 _±_ 60


Ly _α_ line width FWHM Ly _α_ (km s _[−]_ [1] ) 144 _±_ 56


Ly _α_ luminosity _L_ Ly _α_ (10 [7] _L_ _⊙_ ) (12 _._ 4 _±_ 3 _._ 2) _×_ (10 _/µ_ ) _[a]_

_a_ _µ_ is the lensing magnification


_b_ We assume dust temperature _T_ d = 40 K, spectral index _β_ d = 1 _._ 5, and the dust emitting


region of a single beam size


_c_ The value under the assumption that lensing effects are equal for the major and minor


axes


12

**Acknowledgements** We thank K. Umetsu for a discussion of gravitational lensing models, K. Nakan

ishi, F. Egusa, and K. Saigo for discussions in handling with ALMA data, S. Kikuchihara for support

ing MOSFIRE observations, H. Yajima and A. Zitrin for helpful discussions. We acknowledge support


from: NAOJ ALMA Scientific Research Grant Number 2016-01A (T.H.and A.K.I.); European Research


Council Advanced Grant FP7/669253 (N.L. and R.S.E.) and 339177 (C.E.R.); KAKENHI grants 26287034


and 17H01114 (K.M. and A.K.I.), 17H06130 (Y.Tamura), 17H04831 (Y.M.), 16H01085 (T.O.), 16H02166


(Y.Taniguchi), 15K17616 (B.H.), 17K14252 (H.U.), JP17H01111 (I.S.), 16J03329 (Y.H.), and 15H02064


(M.O.); the grant CONICYT-Chile Basal-CATA PFB-06/2007, FONDECYT Regular 1141218 (F.E.B.);


NAOJ Visiting Fellow Program (N.H.H.). ALMA is a partnership of ESO (representing its member states),


NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Re

public of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by


ESO, AUI/NRAO and NAOJ. This work incorporates with observations with ESO Telescopes at the La Silla


Paranal Observatory. This work is also in part based on observations made with the _Spitzer_ Space Telescope,


which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with


NASA, as well as the NASA/ESA _Hubble_ Space Telescope, obtained at the Space Telescope Science Insti

tute (STScI), which is operated by the Association of Universities for Research in Astronomy, Inc. under


NASA contract NAS 5-26555.


**Author Contributions** T.H., N.L., R.S.E., and A.K.I. wrote the paper. T.H. and Y.Tamura reduced and


analyzed ALMA data. T.H. produced Figs. 1 and 2 and Extended Data Figs. 1, 3-5. N.L. reduced and


analyzed X-Shooter data, and produced Extended Data Figs. 2 and 7. K.M. and E.Z. performed SED fitting


analyses. K.M. produced Fig. 3 and Extended Data Fig. 6. W.Z. carried out the astrometry analysis on


_HST_ and IRAC data. N.L. and C.E.R. performed lensing analyses. H.M., I.S., T.O., N.Y., Y.Taniguchi,


13

B.H., H.U., Y.M. contributed to the ALMA observational strategy. N.H.H. independently inspected the


ALMA data. G.R.B., T.F., R.P. inspected independently the X-Shooter spectra. G.R.B. contributed to


the observations. F.E.B. contributed to the X-Shooter observational strategy. Y.H. and M.O. performed


MOSFIRE observations and analysed the archival and our own MOSFIRE data. All authors discussed the


results and commented on the manuscript.


**Author Information** Preprints and permissions information is available at www.nature.com/reprints. The


authors declare no competing financial interests. Readers are welcome to comment on the online version of


the paper. Correspondence and requests for materials should be addressed to T.H. (thashimoto@est.osaka

sandai.ac.jp).


14

**Methods**


**Cosmological model.** The adopted cosmological parameters are _H_ 0 = 70 _._ 4 km s _[−]_ [1] Mpc _[−]_ [1], Ω m =


0 _._ 272, Ω b = 0 _._ 045, and Ω Λ = 0 _._ 728 [25] .


**ALMA observations and data reduction.** We observed MACS1149-JD1 with ALMA in Band 7


with a configuration C40-3 (ID 2015.1.00428.S, PI: A. K. Inoue). To cover the uncertainty derived


from the photometric redshift analysis [4,6–9], we used four setups with contiguous frequencies la

beled as T3, T4, T5, and T6 encompassing the frequency range 314 _._ 4 _−_ 340 _._ 5 GHz and the redshift


range _z_ = 9 _._ 0 _−_ 9 _._ 8. In each setup, a total bandwidth of 7 _._ 5 GHz was used, split into four spectral


windows (SPWs) each with a 1 _._ 875 GHz bandwidth in the Frequency Division Mode (FDM). Each


SPW has a 7 _._ 8125 MHz resolution, corresponding to a velocity resolution of _∼_ 7 km s _[−]_ [1] . The total


observation times are 75 _._ 6, 35 _._ 3, 119 _._ 4, and 42 _._ 3 minutes, for T3, T4, T5, and T6, respectively.


The T3, T4, T5, and T6 data were reduced using the CASA pipeline version 4.7.0, 4.5.2, 4.7.2,


and 4.6.0, respectively, with a standard calibration script provided by the ALMA observatory. We


then produced final images and cubes with the CLEAN task using natural weighting to maximize


point-source sensitivity. The spatial resolution is 0 _[′′]_ _._ 62 _×_ 0 _[′′]_ _._ 52 (FWHM) and the beam position


angle was PA = _−_ 8 _._ 9 _[◦]_ . A quasar, J1229+0203, was used for bandpass and flux calibrations, for


which a flux uncertainty is estimated to be ≲ 10%.


**[O** III **]** 88 _µ_ **m line.** To search for a line, we created a data cube, six native channels of which are


binned, resulting in a velocity resolution of _∼_ 42 km s _[−]_ [1] . In the T5 setup at _∼_ 335 GHz, we


found a _>_ 3 _._ 0 _σ_ signal in five continuous binned-channels, where 1 _σ_ is the local noise estimated


15

with the CASA task imstat. This frequency region is free from atmospheric absorption features.


We then created a velocity-integrated intensity image between 335 _._ 5 and 335 _._ 8 GHz. The peak


intensity of MACS1149-JD1 is 129 _._ 8 _±_ 17 _._ 5 mJy km s _[−]_ [1] beam _[−]_ [1] corresponding to a significance


level of 7 _._ 4 _σ_, where 1 _σ_ error values in this paper denote the 1 _σ_ rms or standard deviation unless


otherwise specified.


The spatial centroid of the emission line is in good positional agreement with that of the UV


continuum emission observed by _HST_ (Figure 1). Both images are similarly elongated along the


imfit to be
gravitational lensing shear. We measured the integrated line flux using the CASA task


0 _._ 229 _±_ 0 _._ 048 Jy km s _[−]_ [1] . To obtain the redshift, we extracted the 1D-spectrum from the region with


_>_ 3 _σ_ signals in the velocity-integrated intensity image. As can be seen, the [O III ] line is detected


at around 335 _._ 6 GHz (or 893 _._ 2 _µ_ m) in the Solar system barycentric frame. Applying a Gaussian fit


to the line, and with a rest-frame [O III ] frequency 3393.006244 GHz, we obtain a redshift _z_ [OIII]


= 9 _._ 1096 _±_ 0 _._ 0006 and FWHM of 154 _±_ 39 km s _[−]_ [1], which is reasonable for a low mass galaxy [26] .


The integrated flux and redshift leads to an observed luminosity of (7 _._ 4 _±_ 1 _._ 6) _×_ (10 _/µ_ ) _×_ 10 [7] _L_ _⊙_,


where _µ_ is the magnification factor (see later sections for the choice of _µ_ =10).


With the CASA task imfit, we obtained the deconvolved size of (0 _[′′]_ _._ 82 _±_ 0 _[′′]_ _._ 25) _×_ (0 _[′′]_ _._ 30 _±_


0 _[′′]_ _._ 14). Assuming that lensing effects are equal for the major and minor axes, the intrinsic size is


(3 _._ 7 _±_ 1 _._ 1) _/_ _[√]_ _µ_ [kpc] _×_ (1 _._ 4 _±_ 0 _._ 9) _/_ _[√]_ _µ_ [kpc].


**Upper** **limits** **on** **dust** **continuum** **emission,** **the** **total** **infrared** **luminosity,** **and** **the** **dust** **mass.**


To create a dust continuum image, we collapsed all four setup data in the frequency range from


16

314 _._ 4 to 340 _._ 5 GHz. In this procedure, we excluded the frequency around the [O III ] line, _±_ 3 _×_


_FWHM_ [OIII] . With the CASA task imstat, the rms noise level for the continuum image is 17 _._ 7


_µ_ Jy beam _[−]_ [1] . The panel (a) of Extended Data Figure 1 shows ALMA dust continuum contours of


MACS1149-JD1 overlaid on the _HST_ F160W image. In the continuum image, we do not detect any


signal above 3 _σ_, placing a stringent upper limit on dust continuum emission _S_ _ν,_ 90 _µm_ _<_ 5 _._ 3 _×_ (10 _/µ_ )


_µ_ Jy beam _[−]_ [1] .


We estimate the total infrared luminosity by integrating the modified-black body radiation


over 8 _−_ 1 _,_ 000 _µ_ m with the emissivity index of _β_ d = 1 _._ 5 and the dust temperature of _T_ d = 30–


60 K similarly to previous studies [27–30] . The results corrected for the CMB effects [11,31] are listed


in Extended Data Table 1. Assuming a dust mass absorption coefficient _κ_ = _κ_ 0 ( _ν/ν_ 0 ) _[β]_ [d], where


_κ_ 0 = 10 cm [2] g _[−]_ [1] at 250 _µ_ m [12], we obtain the 3 _σ_ dust mass upper limit of 5 _._ 3 _×_ 10 [5] _×_ (10 _/µ_ ) _M_ _⊙_


for the case of 40 K. The dust mass upper limit is increased if the dust temperature is lowered (see


Extended Data Table 1). In this estimation, we have assumed the dust emitting region size to be


a single beam size following other high- _z_ null detection cases [10,31–33] . If, instead, we assume the


same size as that of the [O III ] emitting region, roughly 3 times larger than the beam size, the upper



limits can be relaxed by a factor of _√_



3 compared with the values listed in Extended Data Table 1.



**VLT/X-Shooter observations and results.** We performed the X-Shooter observations in Febru

ary and April 2017 (098.A-0534, PI: N. Laporte) for 4.25 and 4 hours, respectively. We adopted


a nodding offset of 4”.0 so that a bright galaxy entered the slit every other exposure. By detecting


the continuum in these half exposures, we confirmed that MACS1149-JD1 was correctly acquired.


The chosen slit orientation (+15 _[◦]_ ) encompasses both the bright galaxy and the elongated shape of


17

the lensed target (Extended Data Figure 2). In order to maximise efficiency, we used 900s, 810s,


740s exposures in the NIR, VIS and UVB arms respectively.


The data were reduced using ESO Reflex tool [34] (v2.8) with the latest version of the X

Shooter pipeline (v 2.9.3). The final spectrum was obtained by combining all reduced exposures


using both EsoReflex and a master flat derived from all the data, and the IRAF imcombine


task on the individual observing blocks. Both methods give similar results. No emission line


was found in the UVB and VIS arm spectra. Visual inspection of the NIR arm shows a possible


emission line at 12,267.4 A with an integrated flux of 4.3 [˚] _±_ 1.1 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] . Based upon


the rms measured in similar sized adjacent apertures, the emission line has a formal significance


of 4 _σ_ . Taking into account air refraction and the motion of the observatory, we deduce a vacuum


wavelength in the barycentric system : 12,271.51 _±_ 2.27 A [˚] corresponding to Ly _α_ at a redshift


of 9 _._ 0942 _±_ 0 _._ 0019. We rule out other identifications (e.g. [O II], H _β_, [O III] and H _α_ ) since


further emission lines would be seen given our wide wavelength coverage and typical line ratios


seen in other star forming sources. Within the likely wavelength range where Ly _α_ might be found,


the ratio of resolution elements with positive and negative deviations above a signal/noise ratio


of 4 exceeds 5, emphasising that the detection cannot be dismissed as a fluctuation in the noise


variation. Although there is some Keck MOSFIRE data for MACS1149-JD1 both within the Keck


archive and from a recent campaign, it has insufficient additional exposure time to strengthen the


signal/noise of the X-shooter detection.


The redshifts obtained from [O III ] and Ly _α_ are slightly different, corresponding to a velocity


offset of ∆ _v_ Ly _α_ = _−_ 450 _±_ 60 km s _[−]_ [1] (Extended Data Figure 3). For a single galaxy emitting both


18

[O III ] and Ly _α_, inflowing gas with a high neutral hydrogen column density, log _N_ HI _/_ (cm _[−]_ [2] ) _≃_


20 _−_ 21 would lead to Ly _α_ becoming blue-shifted [23,24] and similar offsets have been seen at


_z_ _∼_ 2 _−_ 3 [35] . Such inflowing gas would rejuvenate MACS1149-JD1, causing a secondary burst after


a relatively inactive phase as indicated by our SED analyses. The Ly _α_ line profile would also be


affected by the surrounding intergalactic medium (IGM). Since our SED analysis indicates a domi

nant phase of earlier star formation, we may expect a large ionised bubble around MACS1149-JD1.


Assuming a simple model [20–22], the Str¨omgren radius can be estimated as _R_ s = (3 _N_ ion _/_ 4 _π⟨n_ H _⟩_ ) [1] _[/]_ [3],


where _N_ ion is the total ionizing photon number emitted by the early stellar component and _⟨n_ H _⟩_


is the mean hydrogen density at _z_ = 9 _._ 1. From the SED analyses, _N_ ion is estimated to be


_≃_ 1 _×_ 10 [70] _×_ (10 _/µ_ ) regardless of the star formation history. Assuming an escape fraction of


20%, we obtain a Str¨omgren radius of 0 _._ 4 _×_ ( _f_ esc _/_ 0 _._ 2) [1] _[/]_ [3] (10 _/µ_ ) [1] _[/]_ [3] Mpc, corresponding to a ve

locity offset _≃_ 500 _×_ ( _f_ esc _/_ 0 _._ 2) [1] _[/]_ [3] (10 _/µ_ ) [1] _[/]_ [3] km s _[−]_ [1], where _f_ esc corresponds to the escape fraction


of ionizing photons from galaxies to the intergalactic medium.


Alternatively, it is possible that MACS1149-JD1 comprises two _z_ = 9 _._ 1 galaxies separated


kinematically by 450 km s _[−]_ [1] . In this case, the IRAC excess could be associated with either galaxy


but, regardless, the Ly _α_ emitting component would lie within the ionized bubble. Indeed, we note


a _z_ = 7 _._ 1 galaxy has Ly _α_, [O III ], and [C II ] each offset spatially and in velocity space [17] . This


galaxy shows a _∼_ 500 km s _[−]_ [1] blue-shifted Ly _α_ with respect to [O III ].


**Astrometry.** Several studies have demonstrated that there are, in some cases, spatial offsets be

tween ALMA-detected sources and their _HST_ -counterparts [29,36] . We took advantage of a dusty


spiral galaxy, CLASH 2882 [37–39], in our ALMA field-of-view to examine possible astrometric off

19

sets. The panel (b) of Extended Data Figure 1 shows ALMA dust continuum contours of CLASH


2882 overlaid on the _HST_ F160W image. Dust continuum is clearly detected at the exact position


of the NIR counterpart of CLASH 2882 at the significance level of _≃_ 10 _σ_ (where 1 _σ_ = 16 _._ 0 _µ_ Jy


beam _[−]_ [1] ). The centroids of ALMA and _HST_ are consistent within 0 _[′′]_ _._ 1.


As can be seen from the _HST_ morphology shown on Figure 1 and the panel (a) of Extended


Data Figure 1 MACS1149-JD1 is elongated and may be formed by two components at _z_ = 9 _._ 1


separated by 0”.33. To determine the exact position of the Ly _α_ emitting region, we collapsed the


final 2D spectrum in wavelength direction, and measured the separation between Ly _α_ and the con

tinuum of the reference galaxy. Within the positional uncertainty _≃_ 0” _._ 7, the Ly _α_ emitting region


is consistent with arising in either component. As revealed in Figures 2 and 3, the strong excess


in IRAC 4.5 _µ_ m is a prominent feature of MACS1149-JD1. To determine from which component


the IRAC 4.5 _µ_ m emission arises, we first checked the astrometry between _HST_ and IRAC 4.5 _µ_ m


with bright point source stars. Within the 1 _σ_ uncertainty _≃_ 0” _._ 3 and the resolution of the IRAC


camera, the centroid of the 4.5 _µ_ m channel is consistent with emission from either of the two _HST_


counterparts.


**Magnification factor.** With our new spectroscopic redshift, we revisited the magnification calcu

lations using all the mass models released in the framework of the Frontier Fields survey [40–46] . The


magnification values range from _µ_ =4.9 [+0] _−_ 0 _[.]_ _._ [4] 5 [(Diego] [v4.1)] [to] [89.0] [+192] _−_ 40 _._ 8 _[.]_ [7] [(CATS] [v4.1)] [with] [a] [mean]


value of _⟨µ⟩_ =21.8 [+260] _−_ 17 _._ 4 _[.]_ [0] [.] [However, if we remove the most extreme values, the mean magnification]


factor decreases to _⟨µ⟩_ =11.7 [+80] _−_ 5 _._ 1 _[.]_ [1] [,] [where the error bar takes into account the dispersion of values]


from all the Frontier Fields models. For simplicity we assume a fiducial value for the magnification


20

factor of 10 in this study.


**Spectral energy distribution modeling.** We built the SED of our target by combining data from


the 3 deep _HST_ images obtained within the framework of the Frontier Fields survey [7], the deep K _s_


image obtained with VLT/HAWK-I [16] as well as the deep _Spitzer_ /IRAC 3.6 and 4.5 _µ_ m data [7] . In


addition, we use our deep upper limit on dust continuum emission as well as our measurement of


the [O III ] flux described above.


We use our own SED fitting code [47] . Briefly, the stellar population synthesis model of


GALAXEV [48] including nebular continuum and emission lines [49] is used. The [O III ] line flux is


estimated from metallicity and SFR using semi-empirical models [10,19] . The ionizing photon es

cape fraction is fixed to zero. A Calzetti’s law [50] is assumed for dust attenuation, and empirical dust


emission templates [51] are adopted. The Chabrier initial mass function [52] at 0 _._ 1 _−_ 100 _M_ _⊙_ is adopted,


and a mean IGM model is applied [53] . The model parameters and their steps are summarized in Ex

tended Data Table 2. To estimate the best-fit parameters, we use the least _χ_ [2] formula [54] including


an analytic treatment of upper limits for the non-detection. Uncertainties on the parameters are


estimated based on a Monte Carlo technique.


In a first attempt, we adopted a single exponentially declining star formation history (SFH).


The panel (a) of Extended Data Figure 4 shows the best-fit SED obtained with a reduced _χ_ [2] _ν_ _[≃]_ [6] _[.]_ [9]


and a stellar age of _≃_ 300Myr. Although the stellar age is comparable to that obtained by previous


studies [7,16], this model could not reproduce the [O III ] line flux observed with ALMA. The situation


is worse if we assume a constant SFH which has _χ_ [2] _ν_ _[≃]_ [11] _[.]_ [4][ leading to a stellar age of] _[ ≃]_ [500][ Myr]


21

(the panel (b) of Extended Data Figure 4).


We next considered a two stellar component SED comprising a young starburst and an old


population. In order to reproduce the observed SED with as small a number of parameters as pos

sible, we assumed constant SFRs for both components. Extended Data Figure 5 gives a schematic


picture of our models. If one assumes an exponentially declining (rising) SFH for the old com

ponent, there is always an equivalent constant SFH model with a lower (higher) age of the popu

lation. We adopted several star formation durations for the old component, namely _τ_ = 10, 100,


200, 300, and 400 Myr. In these two component models, we can reproduce the observations with


_χ_ [2] _ν_ _[∼]_ [2] _[.]_ [8] _[ −]_ [3] _[.]_ [0][.] [Models] [with] _[τ]_ [=][300] [and] [400] [Myr] [lead] [to] [a] [stellar] [age] _[>]_ [400] [Myr] [at] _[z]_ [=][9.1,]


similar to the age of the Universe at this redshift, which we consider physically unacceptable. The


other three models give a similar quality fit and ages for the old stellar population ranging from


230 to 320 Myr. Due to the similarity of the physical and statistical results produced by the three


remaining models, we cannot easily discriminate one over the other. For this reason, we select


the _τ_ = 100 Myr model as our fiducial case but include uncertainties which reflect the standard


deviation caused by the choice of a _τ_ = 10 or 200 Myr model (Extended Data Table 3). The panels


(c) and (d) of Extended Data Figure 4 show the two best-fit SEDs for _τ_ = 10 and 200 Myr.


Although we can exclude contamination of the IRAC channel 2 from the [O III ] 5007 A line [˚]


at the [O III ] redshift _z_ = 9 _._ 1096 (and the lower Ly _α_ redshift), conceivably there is contamination


from intense H _β_ and [O III ] 4959 A [˚] [13] . Our nebular emission line model [49] already accounts for


such contributions up to a rest-frame equivalent width (H _β_ +[O III ] 4959 A) of [˚] _∼_ 1550 A in young [˚]


metal-poor cases. Nevertheless, Extended Data Figure 6 show that such young metal-poor models


22

cannot reproduce the red IRAC colour because of the contribution of strong nebular continuum


and [O II ] 3727 A line emission in the IRAC channel 1. [˚] Such an explanation for the IRAC excess


is further disfavoured by e.g, the observed dust emission upper limit (panel (c) of Extended Data


Figure 6).


**Dynamical** **mass.** We derive the dynamical mass, _M_ dyn, of MACS1149-JD1 following analyses


at _z_ _∼_ 2 [55] . Because MACS1149-JD1 does not show a velocity gradient in [O III ], we assume


that MACS1149-JD1 is dispersion-dominated. In this case, the dynamical mass can be obtained



as _M_ dyn = 6 _._ 7 _σ_ line [2] _[r]_ [ 1]




[1] [the] [half] [light] [radius,]

2 [is]




[where] _[σ]_ [line] [is] [the] [line] [velocity] [dispersion,] _[r]_ [1]
2 _[/G]_ [,] 2



and _G_ is the gravitational constant. Taking the lensing effect into account, the intrinsic half light


radius becomes (1 _._ 9 _±_ 0 _._ 6) _/_ _[√]_ _µ_ with an uncertainty of a factor 1 _/_ _[√]_ _µ_ depending on the direction


of elongation. We thus obtain _M_ dyn = (4 _±_ 3) _×_ (10 _/µ_ ) [0] _[.]_ [5] _×_ 10 [9] _M_ _⊙_ . Therefore, the dynamical


mass is comparable to or larger than the stellar mass, (1 _._ 1 _±_ 0 _._ 5) _×_ (10 _/µ_ ) _×_ 10 [9] _M_ _⊙_ .


**Predictions for future** _**JWST**_ **observations.** The star formation history deduced from the SED

fits allows us to trace the earlier luminosity evolution of MACS1149-JD1 as a function of cosmic


age. Accordingly, we computed the SED from _z_ = 15 to 9 _._ 1 and find that the source would have


been as bright as _m_ 1500 =26 AB at _z_ = 12 (corrected for magnification; Extended Data Figure 6).


Such a source would be easily detectable by the _JWST_ . Between _z_ _∼_ 12 and _z_ _≤_ 15, it would


be detected with NIRCam at 10 _σ_ within 20 minutes. Furthermore and according to NIRSpec


sensitivity the UV continuum and a significant Ly _α_ break of MACS1149-JD1 analogues will be


detectable at a 5 _σ_ level in less than an hour (Extended Data Figure 7).


23

**Code availability.** The ALMA data were reduced using the CASA pipeline versions 4.7.0, 4.5.2,


4.7.2, and 4.6.0, for the T3, T4, T5, and T6 data, respectively. Our SED fitting code is our cus

tom one, which is available at https://www.astr.tohoku.ac.jp/ _∼_ mawatari/KENSFIT/KENSFIT.html


with instructions.


**Data availability.** This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00428.S,


available at https://almascience.nao.ac.jp/aq/?project ~~c~~ ode=2015.1.00428.S. This paper is also based


on observations made with ESO Telescopes at the La Silla Paranal Observatory under programme


ID 098.A-0534, available at http://archive.eso.org/wdb/wdb/eso/sched ~~r~~ ep ~~a~~ rc/query?progid=098.A

0534(A). _HST_ and _Spitzer_ as well as VLT/HAWK-I photometry data that support our finding are


available in the IOPscience repository with the identifiers DOI: 10.3847/1538-4357/aa5d55 [7] and


DOI: 10.3847/1538-4357/aaa9c2 [16], respectively. The datasets generated during and/or analysed


during the current study are available from the corresponding author on reasonable request.


24

+22°24'44.5"





34.50s 34.45s 34.40s 11h49m34.35s


RA (J2000)



46.5"


46.0"


45.5"


45.0"


44.5"


+22°24'44.0"



**Extended** **Data** **Figure** **1** _|_ **ALMA** **dust** **contours** **of** **MACS1149-JD1** **and** **a** **serendipitous** **continuum**


**object.** (a) ALMA dust contours of MACS1149-JD1 overlaid on the _HST_ F160W image. Contours are


drawn at _±_ 2 _σ_, where _σ_ = 17 _._ 7 _µ_ Jy beam _[−]_ [1] . Negative contours are shown by the dashed line. Ellipse at


the lower left corner indicates the synthesized beam size of ALMA. (b) Dust continuum of a dusty galaxy at


_z_ = 0 _._ 99 in our ALMA field-of-view, overlaid on the _HST_ F160W image. Contours are drawn at ( _−_ 2, 2, 4,


6, 8, 9 _._ 5) _×σ_, where 1 _σ_ = 16 _._ 0 _µ_ Jy beam _[−]_ [1] .


25

**Extended Data Figure 2** _|_ **X-Shooter observations and the Ly** _α_ **spectra of MACS1149-JD1.** (a) Orienta

tion of the X-Shooter slit (white dashed rectangle) demonstrating the successful acquisition of MACS1149

JD1 via the alignment of the slit to follow its lensed elongation as well as the inclusion of a bright foreground


galaxy. (b) X-Shooter 2D spectra of MACS1149-JD1 with the position of Ly _α_ marked with a green arrow,


and the two negative counterparts with red arrows. Sky lines are highlighted by blue rectangles. (c) 1D


extracted spectra in a 0”.8 aperture. Ly _α_ is indicated in yellow, 2 _σ_ is in grey and the sky lines are marked


by blue rectangles.


26

ퟣ.ퟧ


ퟣ.ퟢ


ퟢ.ퟧ


ퟢ.ퟢ


ퟣ.ퟧ


ퟣ.ퟢ





ퟢ.ퟧ


ퟢ.ퟢ

|Col1|[OIII] ퟪퟪm|
|---|---|
|||
|Ly|Ly|
|Velocity [km s−ퟣ]<br>−ퟧퟢퟢ<br>ퟢ<br>ퟧퟢퟢ|Velocity [km s−ퟣ]<br>−ퟧퟢퟢ<br>ퟢ<br>ퟧퟢퟢ|



**Extended Data Figure 3** _|_ **ALMA [O** III **]** 88 _µ_ **m and X-Shooter Ly** _α_ **spectra in velocity space.** [O III ] and


Ly _α_ are shown with a resolution of _∼_ 42 km s _[−]_ [1] and 15 km s _[−]_ [1], respectively. The values are normalized by


the peak flux densities. The velocity zero point corresponds to the [O III ] redshift _z_ = 9 _._ 1096 (red dashed


line) and the Ly _α_ offset is _≃_ 450 km s _[−]_ [1] (blue dashed line). Grey rectangles show regions contaminated by


night sky emission. The data at around _−_ 100 to 0 km s _[−]_ [1] is removed from the analysis because the night


sky emission is too strong. The black solid lines indicate the 1 _σ_ noise level for the velocity resolutions.


27

**Extended** **Data** **Figure** **4** _|_ **Best-fit** **SEDs** **of** **MACS1149-JD1** **with** **various** **star** **formation** **histories.**


Panels (a) and (b) show the best-fit SED with a single stellar component assuming an exponentially declining


and constant SFHs, respectively. Panels (c) and (d) show the best-fit SEDs with two stellar components


assuming a constant SFH. The star formation durations of the old component are _τ_ = 10 and 200 Myr.


The reduced _χ_ [2] value, _χ_ [2] _ν_ [, and the best-fit stellar age for each model is shown in the upper left corner.] [The]


meanings of the symbols are the same as those in Figure 2.


28

Schematic picture of two-comp SFH






|CommonAv<br> (fixed) Common Z<br>Age1<br>Age2<br>SFR1<br>SFR2|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
| (fixed)<br>SFR1<br>Age1<br>Age2<br>SFR2<br>Common Av<br>Common Z|||||
| (fixed)<br>SFR1<br>Age1<br>Age2<br>SFR2<br>Common Av<br>Common Z|Age1|Age2<br>SFR2|Age2<br>SFR2|Age2<br>SFR2|
| (fixed)<br>SFR1<br>Age1<br>Age2<br>SFR2<br>Common Av<br>Common Z|Age1|Age2<br>SFR2|||
|Age of the Universe<br>z=9.|Age of the Universe<br>z=9.|Age of the Universe<br>z=9.|Age of the Universe<br>z=9.|1 Obs.|



**Extended Data Figure 5** _|_ **Schematic picture of star formation histories of our two components models.**


The Red and blue rectangles show the old and young stellar components with constant SFRs, respectively.


The old components stops its star formation activity after a fixed duration of _τ_ . The black vertical dashed


line indicates the observation at _z_ = 9 _._ 1 (the Universe age _≃_ 550 Myr). Each component is described


with Age and SFR parameters. For simplicity, both components have a common dust attenuation _A_ v and


metallicity _Z_ .


29

**Extended** **Data** **Figure** **6** _|_ **Comparisons** **of** **constant** **SFH** **models** **and** **observational** **constraints.** We


show the (a) _χ_ [2] _ν_ [,] [(b)] [IRAC] [colour,] [and] [(c)] [dust] [emission,] [plotted] [against] [stellar] [age.] [All] [model] [grids] [are]


shown with small grey dots, while the best-fit models at given stellar ages are indicated with red circles. In


panel (b), the black horizontal dashed line indicates the observed value and the yellow shaded region its 1 _σ_


uncertainty. In panel (c) the black horizontal dashed line refers to the 2 _σ_ upper limit. Panels (d) - (f) show


the best-fit SEDs at ages of 1, 10 and 100 Myr indicated by the blue squares in panel (a). Inset figures show


the dust continuum flux density ( _µ_ Jy) and [O III ] 88 _µ_ m flux (10 _[−]_ [18] erg cm _[−]_ [2] s _[−]_ [1] ). Panel (d) demonstrates


that a strong nebular continuum plus [O II ] 3727 A [˚] emission counteracts intense _Hβ_ plus [O III ] 4959 A [˚]


emission producing an ‘inverse Balmer break’ for very young metal-poor cases.


30

**Extended Data Figure 7** _|_ **Evolution of the UV luminosity of MACS1149-JD1 as a function of redshift.**


For each redshift bin (∆z=1), we extrapolated the magnitude by assuming a constant Star Formation Rate


over the redshift interval (blue curve). We over-plotted the sensitivity of NIRCAM filters (pink and grey)


covering the _λ_ 1500 A rest-frame (10 [˚] _σ_ in _≈_ 20 minutes) and the NIRSpec sensitivity (dashed black line) at


the same wavelength (10 _σ_ in 3 hours).


31

_T_ d _β_ d _L_ TIR _M_ d


(K) (10 [9] _L_ _⊙_ ) (10 [5] _M_ _⊙_ )


30 1 _._ 5 _<_ 6 _._ 0 _×_ (10 _/µ_ ) _<_ 20 _._ 0 _×_ (10 _/µ_ )


40 1 _._ 5 _<_ 7 _._ 7 _×_ (10 _/µ_ ) _<_ 5 _._ 3 _×_ (10 _/µ_ )


50 1 _._ 5 _<_ 11 _._ 4 _×_ (10 _/µ_ ) _<_ 2 _._ 3 _×_ (10 _/µ_ )


60 1 _._ 5 _<_ 17 _._ 3 _×_ (10 _/µ_ ) _<_ 1 _._ 3 _×_ (10 _/µ_ )


**Extended Data Table 1** _|_ **Upper limits on the infrared luminosity and dust mass.**


Upper limits represent the 3 _σ_ limits. The total luminosity, _L_ TIR, is estimated by integrating


the modified-black body radiation at 8 _−_ 1 _,_ 000 _µ_ m. We use dust temperatures ranging


from _T_ d = 30 K to 60 K and the emissivity index _β_ d = 1 _._ 5. The dust mass, _M_ d, is


estimated with a dust mass absorption coefficient _κ_ = _κ_ 0 ( _ν/ν_ 0 ) _[β]_ [d], where _κ_ 0 = 10 cm [2] g _[−]_ [1]


at 250 _µ_ m (Ref. [12] ).


32

**Single stellar component**


Star formation history Exponential ( _τ_ = _±_ 0 _._ 03 _,_ 0 _._ 06 _,_ 0 _._ 1 _,_ 0 _._ 3 _,_ 0 _._ 6 _,_ 1 _._ 0 and 10 Gyr)


Age [Myr] 0 _._ 1 _−_ 550 (age of the Universe)


Dust _A_ V [mag] 0 _−_ 1


Metallicity _Z_ = 0 _._ 0001 _,_ 0 _._ 0004 _,_ 0 _._ 004 _,_ 0 _._ 008, and 0 _._ 02


Star formation rate [ _M_ _⊙_ yr _[−]_ [1] ] arbitrary (amplitude)


**Two stellar components** **(Constant** + **shut down)**


Age1 [Myr] 0 _._ 1 _−_ 550 (age of the Universe)


Age2 [Myr] 0 _._ 1 _−_ 550 (age of the Universe)


Common Dust _A_ V 1 = _A_ V 2 [mag] 0 _−_ 1


Common Metallicity _Z_ 1 = _Z_ 2 _Z_ = 0 _._ 0001 _,_ 0 _._ 0004 _,_ 0 _._ 004 _,_ 0 _._ 008, and 0 _._ 02


Total Star formation rate [ _M_ _⊙_ yr _[−]_ [1] ] arbitrary (amplitude)


SFR ratio _f_ SFR0 _≡_ (SFR2/SFR1) _z_ =9 _._ 1 10 _[−]_ [4] _−_ 10 [4]


**Extended Data Table 2** _|_ **Summary of our SED parameters.** In single component


models, three SFHs of constant, exponentially-declining, and exponentially-rising SFR


are considered. In two components models, a constant SFH with star formation


durations of _τ_ = 10 _,_ 100 _,_ 200 _,_ 300 _,_ and 400 are used for the old component (see Extended


Data Figure 4 for a schematic picture of our models). The parameter _f_ SFR0 defines the


SFR ratio of the two components at the observation ( _z_ = 9 _._ 1). In all models, dust


attenuation steps are ∆ _A_ V = 0 _._ 1, and age steps follow the original 36 steps in


GALEXEV [48] between 0 _._ 1 _−_ 550 Myr. The SFR ratio steps are ∆log( _f_ SFR0 ) = 0 _._ 1. The


metallicity value is in the absolute unit with a Solar metallicity of33 0 _._ 02.

Parameters Values


_χ_ [2] 5 _._ 52


_ν_ 2


_χ_ [2] _ν_ 2 _._ 76


Age old [Myr] 290 [+190] _−_ 120


Age young [Myr] 3 [+2] _−_ 1


Metallicity 0 _._ 004 [+0] _−_ 0 _[.]_ _._ [004] 004


_A_ _V_ [mag] 0 _._ 0 [+0] _−_ 0 _[.]_ _._ [1] 0


Stellar mass [10 [9] _M_ _⊙_ ] 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [5] 2 _[×]_ [ (10] _[/µ]_ [)]


Star formation rate [ _M_ _⊙_ yr _[−]_ [1] ] 4 _._ 2 [+0] _−_ 1 _[.]_ _._ [8] 1 _[×]_ [ (10] _[/µ]_ [)]


_f_ _SFR_ 0 4 [+76] _−_ 3


_N_ ion _,_ max [10 [70] ] _≃_ 1 _×_ (10 _/µ_ )


_R_ s _,_ max [Mpc] _≃_ 0 _._ 7 _×_ (10 _/µ_ ) [1] _[/]_ [3]


Velocity shift max [km s _[−]_ [1] ] _≃_ 900 _×_ (10 _/µ_ ) [1] _[/]_ [3]


_t_ inact [Myr] 180 [+20] _−_ 60


_z_ f _,_ old 15 _._ 4 [+2] _−_ 2 _[.]_ _._ 0 [7]
**Extended Data Table 3** _|_ **Summary of SED fits in our fiducial model.** Summary of the


best-fit results with our fiducial SED model. The uncertainties reflect any standard


deviation caused by the choice of a _τ_ = 10 or 200 Myr model. The best-fit SED is shown


in Figure 2, and its SFH is shown in red in Figure 3. _N_ ion _,_ max, _R_ s _,_ max, and Velocity shift max


denote the maximum numbers of ionizing photons, Str¨omgren radius, and the shift of the


Ly _α_ damping wing, respectively. _t_ inact is a duration of the inactive phase, and _z_ f _,_ old is the


formation redshift of the old component. 34

**References**


1. Robertson, B., Ellis, R., Furlanetto & S., Dunlop, J. Cosmic Reionization and Early Star

forming Galaxies: A Joint Analysis of New Constraints from Planck and the Hubble Space


Telescope. _Astrophys. J. Lett._ **802L**, 19 (2015)


2. Bouwens, R. et al. Reionization After Planck: The Derived Growth of the Cosmic Ionizing


Emissivity Now Matches the Growth of the Galaxy UV Luminosity Density. _Astrophys._ _J._


**811**, 140 (2015)


3. Stark, D. Galaxies in the First Billion Years After the Big Bang. _Annual Review of Astronomy_


_and Astrophysics._ **54**, 761-803 (2016)


4. McLeod, D., McLure, R. & Dunlop, J. The _z_ = 9 _−_ 10 galaxy population in the Hubble


Frontier Fields and CLASH surveys: the _z_ = 9 luminosity function and further evidence for


a smooth decline in ultraviolet luminosity density at _z_ _≥_ 8. _Mon._ _Not._ _R._ _Astron._ _Soc._ **459**,


3812-3824 (2016).


5. Oesch, P. et al. The Dearth of _z_ _∼_ 10 Galaxies in all HST Legacy Fields – The Rapid Evolution


of the Galaxy Population in the First 500 Myr _arXiv_ https://arxiv.org/abs/1710.11131


6. Zheng, W. et al. A magnified young galaxy from about 500 million years after the Big Bang.


_Nature_ **489**, 406-408 (2012).


7. Zheng, W. et al. Young Galaxy Candidates in the Hubble Frontier Fields. IV. MACS


J1149.5+2223. _Astrophys. J._ **836**, 210, doi:10.3847/2041-8213/aa794f (2017).


35

8. Huang, K. et al. Spitzer UltRa Faint SUrvey Program (SURFS UP). II. IRAC-Detected Lyman

Break Galaxies at 6 _<_ _z_ _<_ 10 Behind Strong-Lensing Clusters. _Astrophys._ _J._ _Lett._ **817**, 11


(2016).


9. Kawamata, R. et al. Precise Strong Lensing Mass Modeling of Four Hubble Frontier Field


Clusters and a Sample of Magnified High-redshift Galaxies. _Astrophys. J._ **819**, 114 (2016).


10. Inoue A. K. et al. Detection of an oxygen emission line from a high-redshift galaxy in the


reionization epoch. _Science_ **352**, 1559-1562 (2016).


11. da Cunha, E. et al. On the Effect of the Cosmic Microwave Background in High-redshift (Sub

)millimeter Observations. _Astrophys. J._ **766**, 13 (2013).


12. Hildebrand, R. H. The Determination of Cloud Masses and Dust Characteristics from Submil

limetre Thermal Emission. _Quarterly J. R. Astron. Soc._ **24**, 267 (1983).


13. Smit, R. et al. High-precision Photometric Redshifts from Spitzer/IRAC: Extreme [3.6] - [4.5]


Colors Identify Galaxies in the Redshift Range _z_ _∼_ 6 _._ 6 _−_ 6 _._ 9. _Astrophys. J._ **801**, 122 (2015).


14. Roberts-Borsani, G. et al. _z_ _≥_ 7 Galaxies with Red Spitzer/IRAC [3.6]-[4.5] Colors in the Full


CANDELS Data Set: The Brightest-Known Galaxies at _z_ _∼_ 7 _−_ 9 and a Probable Spectro

scopic Confirmation at _z_ = 7 _._ 48. _Astrophys. J._ **823**, 143 (2016).


15. Stark, D. et al. Ly _α_ and C III] emission in _z_ = 7 _−_ 9 Galaxies: accelerated reionization around


luminous star-forming systems? _Mon. Not. R. Astron. Soc._ **464**, 469-479 (2017).


36

16. Hoag, A. et al. HST Grism Observations of a Gravitationally Lensed Redshift 9 _._ 5 Galaxy.


_Astrophys. J._ **854**, 39, doi:10.3847/1538-4357/aaa9c2 (2018).


17. Carniani, S. et al. Extended ionised and clumpy gas in a normal galaxy at _z_ = 7 _._ 1 revealed by


ALMA. _Astron. Astrophys._ **605**, 42 (2017).


18. Vernet, J. et al. X-shooter, the new wide band intermediate resolution spectrograph at the ESO


Very Large Telescope. _Astrophys. J._ **536**, A105 (2011).


19. Inoue, A. K. et al. ALMA Will Determine the Spectroscopic Redshift _z_ _>_ 8 with FIR [O III ]


Emission Lines. _Astrophys. J. Lett._ **780**, L18 (2014).


20. Cen, R. & Haiman, Z. Quasar Str¨omgren Spheres Before Cosmological Reionization. _Astro-_


_phys. J._ **542**, L75-L78 (2000).


21. Haiman, Z. The Detectability of High-Redshift Ly _α_ Emission Lines prior to the Reionization


of the Universe. _Astrophys. J._ **576**, L1-L4 (2002).


22. Hu, E. et al. An Ultraluminous Ly _α_ Emitter with a Blue Wing at _z_ = 6 _._ 6. _Astrophys. J. Lett._


**825**, L7 (2016).


23. Dijkstra, M., Haiman, Z. & Spaans, M. Ly _α_ Radiation from Collapsing Protogalaxies. II.


Observational Evidence for Gas Infall. _Astrophys. J._ **649**, 14-36 (2006).


24. Verhamme, A. et al. Using Lyman _−α_ to detect galaxies that leak Lyman continuum. _Astron._


_Astrophys._, **578**, A7 (2015).


37

25. Komatsu, E. et al. Seven-year Wilkinson Microwave Anisotropy Probe (WMAP) Observa

tions: Cosmological Interpretation. _Astrophys. J._ **192**, 18 (2011).


26. Hashimoto, T. et al. A Close Comparison between Observed and Modeled Ly _α_ Lines for


_z_ _∼_ 2 _._ 2 Ly _α_ Emitters. _Astrophys. J._ **812**, 157 (2015).


27. Watson, D. et al. A dusty, normal galaxy in the epoch of reionization. _Nature_ **519**, 327-330


(2015).


28. Knudsen, K. K. et al. A merger in the dusty, _z_ = 7 _._ 5 galaxy A1689-zD1? _Mon. Not. R. Astron._


_Soc._ **466**, 138-146 (2017).


29. Laporte, N. et al. Dust in the Reionization Era: ALMA Observations of a _z_ = 8 _._ 38 Gravita

tionally Lensed Galaxy. _Astrophys. J._ **837**, L21 (2017).


30. Faisst, A. K. et al. Are High-redshift Galaxies Hot? Temperature of _z_ _>_ 5 Galaxies and


Implications for Their Dust Properties. _Astrophys. J._ **847**, 21 (2017).


31. Ota, K et al. ALMA Observation of 158 _µ_ m [C II] Line and Dust Continuum of a _z_ = 7


Normally Star-forming Galaxy in the Epoch of Reionization. _Astrophys. J._ **792**, 34 (2014).


32. Ouchi, M. et al. An Intensely Star-forming Galaxy at _z_ _∼_ 7 with Low Dust and Metal Content


Revealed by Deep ALMA and HST Observations. _Astrophys. J._ **778**, 102 (2013).


33. Schaerer, D. et al. New constraints on dust emission and UV attenuation of _z_ = 6 _._ 5 _−_ 7 _._ 5


galaxies from millimeter observations. _Astron. Astrophys._ **574**, A19 (2015).


38

34. Freudling, W. et al. Automated data reduction workflows for astronomy. The ESO Reflex


environment. _Astrophys. J._ **559**, A96 (2013).


35. Trainor, R., Steidel, C., Strom, A., & Rudie, G. The Spectroscopic Properties of Ly _α_ -Emitters


at _z_ _∼_ 2 _._ 7: Escaping Gas and Photons from Faint Galaxies. _Astrophys. J._ **809**, 89 (2015).


36. Gonz´alez-L´opez, J. et al. The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections


in Abell 2744, MACS J0416.1 _−_ 2403 and MACS J1149.5+2223. _Astron. Astrophys._ **597**, A41


(2017).


37. Dwek, E. et al. Dust Formation, Evolution, and Obscuration Effects in the Very High-redshift


Universe. _Astrophys. J._ **788**, L30 (2014).


38. Dwek, E. et al. Submillimeter Observations of CLASH 2882 and the Evolution of Dust in this


Galaxy. _Astrophys. J._ **813**, 119 (2015).


39. Zavala, J. A. et al. Early science with the Large Millimeter Telescope: dust constraints in a


_z_ _∼_ 9 _._ 6 galaxy. _Mon. Not. R. Astron. Soc._ **453**, L88-L92 (2015).


40. Richard, J. et al. Mass and magnification maps for the Hubble Space Telescope Frontier Fields


clusters: implications for high-redshift studies. _Mon. Not. R. Astron. Soc._ **444**, 268-289 (2014).


41. Johnson, T. L. et al. Lens Models and Magnification Maps of the Six Hubble Frontier Fields


Clusters. _Astrophys. J._ **797**, 48 (2014).


42. Ishigaki, M. et al. Hubble Frontier Fields First Complete Cluster Data: Faint Galaxies at _z_ _∼_


5 _−_ 10 for UV Luminosity Functions and Cosmic Reionization. _Astrophys. J._ **799**, 12 (2015).


39

43. Keeton, C. R. On modeling galaxy-scale strong lens systems. _General Relativity and Gravita-_


_tion_ **42**, 2151-2176 (2010).


44. Liesenborgs, J., De Rijcke, S. & Dejonghe, H. A genetic algorithm for the non-parametric


inversion of strong lensing systems. _Mon. Not. R. Astron. Soc._ **367**, 1209-1216 (2006).


45. Diego, J. M., Protopapas, P., Sandvik, H. B. & Tegmark, M. Non-parametric inversion of


strong lensing systems. _Mon. Not. R. Astron. Soc._ **360**, 477-491 (2005).


46. Merten, J. et al. Creation of cosmic structure in the complex galaxy cluster merger Abell 2744.


_Mon. Not. R. Astron. Soc._ **417**, 333-347 (2011).


47. Mawatari, K. et al. Possible identification of massive and evolved galaxies at _z_ _≃_ 5. _Publ._


_Astron. Soc. Jpn._ **68**, 46 (2016).


48. Bruzual, G. & Charlot, S. Stellar population synthesis at the resolution of 2003. _Mon. Not. R._


_Astron. Soc._ **344**, 1000-1028 (2003).


49. Inoue, A. K. Rest-frame ultraviolet-to-optical spectral characteristics of extremely metal-poor


and metal-free galaxies. _Mon. Not. R. Astron. Soc._ **415**, 2920-2931 (2011).


50. Calzetti, D. et al. The Dust Content and Opacity of Actively Star-forming Galaxies. _Astrophys._


_J._ **533**, 682-695 (2000).


51. Rieke, H. et al. Determining Star Formation Rates for Infrared Galaxies. _Astrophys._ _J._ **692**,


556-573 (2009).


40

52. Chabrier, G. Galactic Stellar and Substellar Initial Mass Function. _Pub. Astron. Soc. Pac._ **115**,


763-795 (2003).


53. Inoue, A. K. et al. An updated analytic model for attenuation by the intergalactic medium.


_Mon. Not. R. Astron. Soc._ **442**, 1805-1820 (2014).


54. Sawicki, M. SEDfit: Software for Spectral Energy Distribution Fitting of Photometric Data.


_Pub. Astron. Soc. Pac._ **124**, 1208 (2012).


55. F¨orster Schreiber, M. et al. The SINS Survey: SINFONI Integral Field Spectroscopy of _z_ _∼_ 2


Star-forming Galaxies. _Astrophys. J._ **706**, 1364-1428 (2009).


41


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "CLEAN with natural weighting; bin six channels to ~42 km/s; search for >3σ signal in five consecutive channels",
  "failed_quote": "we found a > 3 . 0 σ signal in five continuous binned-channels, where 1 σ is the local noise estimated with the CASA task imstat"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "mu=10 fiducial",
  "failed_quote": "For simplicity we assume a fiducial value for the magnification factor of 10 in this study."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Gaussian line fit",
  "failed_quote": "(no quote given)"
 }
]
```
