# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021Sci...372.1201T\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#### **Spiral morphology in an intensely star-forming disk galaxy more than 12** **billion years ago**

Takafumi Tsukui [1,2] *, Satoru Iguchi [1,2 ]


**Affiliations:**


1 Department of Astronomical Science, SOKENDAI (The Graduate University for Advanced
Studies), 2-21-1 Osawa, Mitaka, Tokyo, Japan.


2 National Astronomical Observatory of Japan, National Institute of Natural Sciences, 2-21-1
Osawa, Mitaka, Tokyo, Japan.


*Corresponding author. Email: t.tsukui@grad.nao.ac.jp


**Abstract:**


Spiral galaxies have distinct internal structures including a stellar bulge, disk and spiral arms. It


is unknown when in cosmic history these structures formed. We analyze observations of BRI


1335-0417, an intensely star-forming galaxy in the distant Universe, at redshift 4.41. The [C II ]


gas kinematics show a steep velocity rise near the galaxy center and have a two-armed spiral


morphology that extends from about 2 to 5 kiloparsecs in radius. We interpret these features as


due to a central compact structure, such as a bulge, a rotating gas disk and either spiral arms or


tidal tails. These features had been formed within 1.4 billion years after the Big Bang, long


before the peak of cosmic star formation.


1

Spiral galaxies contain distinct internal structures: a stellar bulge; a flat, extended rotating disk;


and spiral arms that extend through the disk. Observations have established that the total star


formation rate in the Universe rises steeply after the Big Bang, reaches a peak at redshift _z_


between 1.5 and 3, and declines steadily since then ( _1_ ). Optical observations provide evidence


that stellar bulges are already formed in some massive galaxies by _z_ of 0.5 to 2.5 ( _2_ ). Spiral


structure has been reported in galaxies at redshifts of _z_ =2.18 ( _3_ ), _z_ =2.01 ( _4_ ) and _z_ =2.54 ( _5_ ).


Observations with the Atacama Large Millimeter/submillimeter Array (ALMA) have shown


spiral structure in two galaxies at _z_ =2.32 and _z_ =2.67 ( _6_ ), dynamically cold disks in galaxies at


redshift _z_ ~ 4 ( _7_ – _10_ ) and compact central structures, like a bulge, at _z_ of 4 to 5 ( _7_, _10_ ). It is


currently unclear whether the later appearance of spiral structure is due to different formation


times or observational limitations.


BRI 1335-0417 (QSO J1338-0432), a galaxy at redshift _z_ = 4.4074 ± 0.0015 ( _11_ ), 1.4 Gyr after


the Big Bang. It is classified as a Hyper Luminous InfraRed Galaxy (HyLIRG) with a luminosity


of 3.1 ´ 10 [13] _L_ ⊙ ( _L_ ⊙ is the luminosity of the Sun) at far-infrared wavelengths ( _12_ ) and a high


star formation rate of 5 ± 1 ´ 10 [3] _M_ ⊙ yr [-1] ( _M_ ⊙ is the mass of the Sun), estimated from modeling


the spectral energy distribution ( _13_ ).


We analyze archival ALMA observations of BRI 1335-0417 in the gas emission line [C II ] (rest


frame frequency of 1900.5369 GHz, redshifted to around 351 GHz in the observed frame). The


data were produced using standard procedures ( _14_ ). [C II ] line emission from this object was


detected in previous observations at lower spatial resolution, insufficient to determine the gas


2

distribution and kinematics ( _15_ ). Figure 1A-B shows the ALMA [C II ] intensity and velocity


images, with a spatial resolution of of 0.20" × 0.16" full width half maximum (FWHM), which is


equivalent to ~ 1.33 × 1.11 kiloparsecs (kpc) at this redshift. Figure 1C shows the dust


continuum image at a central frequency of 1863 GHz in rest frame with spatial resolution of


0.17" × 0.14" (~ 1.16 × 0.95 kpc). The root mean square noise in each velocity channel (width of


20 km s [-1] ) is about 0.35 millijansky per beam (mJy beam [-1] ), while that of the dust continuum


map is about 0.036 mJy beam [-1] . Figure 1D shows a composite image of the gas velocities,


produced from [C II ] velocity channel maps (Fig. 2) that show the [C II ] line intensity images at


each velocity.


The [C II ] line and dust continuum images show a central compact structure surrounded by more


extended emission which could indicate a disk. A spiral morphology is apparent in Fig. 1D, with


northern and southern arms extending from 2 to 5 kpc in radius. This spiral morphology is more


apparent in the [C II ] velocity channel maps (Fig. 2). We compare these maps to previously

published CO ( _J_ =2→1) line images (where _J_ is the rotational quantum number) which showed


different spatial distribution depending on the antenna configuration used for the observations.


One CO image showed a structure with a bright central component and a weaker northern


component ( _16_ ), while the another showed a complex structure with multiple components ( _17_ ).


These multiple CO components correspond (in position and velocity) to the northern spiral


feature, southern spiral feature and central disk seen in the [C II ] images. [C II ] line emission


arises from multiple phases of the interstellar medium, including ionized gas, atomic gas and


molecular gas, while CO ( _J_ =2→1) line emission traces only dense molecular gas ( _18_ ). The


difference in [CII] and CO distributions is also caused by the difference in sensitivity and spatial


3

frequency coverage between their observations. In addition, in [C II ] line emission, we could not


find any evidence of bipolar outflow which is reported in CO ( _J_ =7→6) line ( _14_ ).


The [C II ] line velocity rises steeply in the center of the galaxy, reaching about 240-260 km s [-1],


indicating the presence of a centrally concentrated mass distribution. The velocity is


approximately constant at 70-110 km s [-1] in the outer parts of the galaxy along the kinematic


major axis, as seen in a position-velocity diagram (PVD; Fig. 1E). A steeply rising and/or


constant velocity curve has been measured in other high redshift galaxies ( _7_, _8_, _10_ ). Such a


velocity curve has been observed in nearby spiral galaxies, produced by the gravitational


potential of the internal structures ( _19_ ). The [C II ] PVD of BRI 1335-0417 indicates the presence


of a central compact structure, such as a stellar bulge, and an extended disk. The rise in velocity


appears to be steeper on the northern side than the southern side. The decrease in velocity until a


radius of 0.3" is seen in the southern side, while the slight increase with radius is seen in the


northern side. These features could be due to streaming motions along spiral arms, warping of


the disk, recent gas accretion ( _10_ ) and/or a lopsided central gas distribution. These disturbed


features are common in nearby galaxies, and have also been found in high-redshift galaxies at _z_ ~


4 ( _8_, _10_ ). Figure 1F shows the velocity dispersions extracted at each position along the kinematic


major axis. The velocity dispersions in the outer parts are consistent with a constant ~ 70 km s [-1],


but increase up to ~ 140 km s [-1] in the center. Such central increases are known to be affected by


the beam smearing effect ( _20_ ): because the spatial resolution is not sufficient to resolve the


intrinsic velocity gradient, it is averaged over the beam width, so the observed velocity


#14 -1

dispersion increases. We estimate an intrinsic velocity dispersion 𝜎 𝑣 of 71 -11 km s (Fig. 1F)


4

using a method ( _21_ ) that extracts the velocity dispersions at the outer region of the disk, where


the beam smearing is less severe.


We used Fourier analysis ( _3_ ) to decompose the [C II ] intensity image (Fig. 1A) into logarithmic


spirals with _m_ arms (Fig. 3A) ( _14_ ). The best-fitting model is a two-armed spiral morphology with


+4.1

a pitch angle of 26.7 -1.6 ° (95% confidence level). Figure 3B shows this model overlain on the


[C II ] line intensity image after correction for the inclination angle of 37.8° (i.e. de-projected to


be viewed as face-on). The disk inclination was estimated from the axis ratio of the dust


continuum image (Table S1) ( _14_ ). The amplitude of the _m_ =2 signal is 6.0 times the noise, while


the other modes _m_ =1, 3, 4 are have signal-to-noise ratios of 4.0, 2.5 and 2.4 respectively (Fig.


3A). The _m_ = 1 mode corresponds to a one-arm spiral or lopsided morphology. The broad signal


in _m_ = 1 mode (Fig. 3A) is due to the difference in length of two arms (Fig. 3B). The _m_ = 3 and 4


modes correspond to a triangular and boxy shape respectively, which could be produced by a


stellar bar structure.


+25 -1

We estimate the inclination-corrected rotational velocity _v_ rot is 179 -18 km s at radius of 0.3",


calculated using the flat part of the PVD (Fig. 1E). The ratio of _v_ rot to the intrinsic velocity


dispersion 𝜎 𝑣 quantifies the rotational support of the disk ( _20_ ). Our estimated ratio _v_ rot /𝜎 𝑣 of


+0.6

2.5 -0.4 indicates that the [C II ] gas disk of this galaxy is rotation-dominated. Similar values have


been found for other galaxies observed at _z_ ~ 4 ( _8_, _9_ ). Higher ratios have also been reported at


redshift of 4 to 5 ( _7_, _10_ ). Additional evidence of rotating disk is symmetric velocity field across


5

the kinematic minor axis, seen in this object (Fig. 1B). Ordered rotation has been found in


kinematic data of several galaxies at redshift ~ 4 ( _22_ ), with such symmetric velocity fields.


We estimate the mass distribution by modeling gas motions under a gravitational potential


composed of a central compact structure and an extended, rotating disk ( _14_ ). The best-fitting


effective radius of the compact structure _R_ e is less than 1.3kpc (at 95% confidence interval) and


its mass is 5.2 × 10 [9] to 3.0 × 10 [10] _M_ ⨀ depending on the value of _R_ e . These results are compatible


with the typical effective radius and mass of stellar bulges in nearby galaxies ( _23_ ). The modeled


+1.7 10 10

mass of the disk 4.9 -2.5 × 10 _M_ ⨀ is consistent with the molecular gas mass of 5.1 × 10 _M_ ⨀


( _16_ ) estimated from the CO ( _J_ =2→1) luminosity (assuming that BRI 1335-0417 has metal


abundance of the sun). We computed the Toomre parameter _Q_ of the gas disk, which describes


the gravitational stability of the disk against perturbations ( _14_ ). We find _Q_ is less than 1


throughout the outer part of the disk (Fig. S6), indicating the gas disk is susceptible to


gravitational collapse, star formation ( _7_ – _9_ ) and spontaneous formation of spiral structure ( _3_, _24_ ).


Studies of nearby galaxies have shown that bulges and supermassive black holes coexist in


massive galaxies, and that there is a strong correlation between their properties ( _25_ ). The mass of


the central black hole in BRI 1335-0417 has previously been estimated as _M_ BH ~ 6 ´ 10 [9] _M_ ⨀


( _26_ ), although there are systematic effects that could bias this value ( _27_ ). Our modeled compact


structure mass 5.2 × 10 [9] -3.0 × 10 [10] _M_ ⨀ is consistent with the estimated _M_ BH . The ratio black


hole mass to the compact structure mass is 1-0.2, which is higher than the black hole to bulge


mass ratio of 0.001 to 0.002 observed in nearby galaxies ( _25_ ) and includes the possibility of a


6

supermassive black hole without a bulge. There is tentative evidence that the black hole-bulge


mass ratio in high redshift galaxies could be higher than at low redshift, but the data are


inconclusive ( _28_ ).


Dusty starburst galaxies like BRI 1335-0417 are the progenitors of present-day massive elliptical


galaxies, which are dominated by old stellar populations ( _7_ ). This transformation requires


contraction of the disk by angular momentum transport through gravitational torques driven by


non-axisymmetric structures ( _29_ ). The spiral morphology in BRI 1335-0417 is present at _z_ =


4.41, long before the peak of cosmic star formation. Spiral structure could influence the


evolution of this galaxy: the angular momentum could be redistributed, triggering gas inflow into


the center of the galaxy and driving intense star formation there ( _29_ ). Such gas inflow could not


be directly detected in our data due to the limited signal to noise ratio.


The two-armed spiral morphology observed in BRI 1335-0417 can be induced in the disk


through tidal interactions ( _3_, _24_ ). Because this galaxy has a rotating disk and a compact structure


at its center, sufficient time for their formation is likely to have passed after the major merger


event. Cosmological simulations at redshift of 6 ( _30_ ) show that spiral structure on a rotating disk


can appear when the disk is relaxed after a merger event. The two-armed spiral morphology in


BRI 1335-0417 extends out to 5kpc (Fig. 1A), is connected to the galaxy center (Fig. 1D) and


associated with the rotating disk spatially and in velocity (Fig. 2 and Fig. 1E). Tidal-tail features


in a galaxy merger are expected occur on larger scales (>10kpc) ( _6_, _31_ ). We therefore disfavor,


but cannot completely rule out, a tidal-tail origin for the observed spiral morphology.


Alternatively, a stellar bar structure may play a role to form two-armed spiral structure ( _24_, _32_ )


7

in this object. Figures 1A and 1C show non-axisymmetric structures, which could be due to a


stellar bar, and the spiral arms appear to begin from the edge of this bar structure, as seen in


nearby disk galaxies and numerical simulation ( _32_ ).


The high star formation rates of _z_ >4 galaxies like BRI 1335-0417 are commonly explained as the


result of major mergers, which could produce distorted galactic kinematics. We find that BRI


1335-0417 has only slightly disturbed, rotation dominated kinematics, which can be well


described by a rotating disk model ( _14_ ). This suggests that the high star formation rate must have


been maintained long enough for the disk to form after any major merger event. The _Q_ parameter


shows the outer disk of BRI 1335-0417 is unstable, which could be caused by gas accretion


along large-scale filaments of the cosmic web ( _29_, _33_ ), and/or minor mergers with the accreting


satellites ( _30_ ).


8

**References and Notes:**


1. P. Madau, M. Dickinson, Cosmic Star-Formation History. _Annu. Rev. Astron. Astrophys._
**52**, 415–486 (2014).


2. S. Tacchella _et al._, Evidence for mature bulges and an inside-out quenching phase 3 billion
years after the Big Bang. _Science_ . **348**, 314–317 (2015).


3. D. R. Law _et al._, High velocity dispersion in a rare grand-design spiral galaxy at redshift z =
2.18. _Nature_ . **487**, 338–340 (2012).


4. S. Dawson _et al._, Optical and Near-Infrared Spectroscopy of a High-Redshift Hard X-Rayemitting Spiral Galaxy. _Astron. J._ **125**, 1236–1246 (2003).


5. T. Yuan _et al._, The Most Ancient Spiral Galaxy: A 2.6-Gyr-old Disk with a Tranquil
Velocity Field. _Astrophys. J._ **850**, 61 (2017).


6. J. A. Hodge _et al._, ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in
High-redshift Submillimeter Galaxies. _Astrophys. J._ **876**, 130 (2019).


7. F. Rizzo _et al._, A dynamically cold disk galaxy in the early Universe. _Nature_ . **584**, 201–204
(2020).


8. M. Neeleman, J. X. Prochaska, N. Kanekar, M. Rafelski, A cold, massive, rotating disk
galaxy 1.5 billion years after the Big Bang. _Nature_ . **581**, 269–272 (2020).


9. K. Tadaki _et al._, The gravitationally unstable gas disk of a starburst galaxy 12 billion years
ago. _Nature_ . **560**, 613–616 (2018).


10. F. Lelli _et al._, A massive stellar bulge in a regularly rotating galaxy 1.2 billion years after

the Big Bang. _Science_ . **371**, 713–716 (2021).


11. S. Guilloteau, A. Omont, R. G. McMahon, P. Cox, P. Petitjean, The second detection of CO

at redshift larger than 4. _Astron. Astrophys._ **328**, L1 (1997).


12. C. L. Carilli _et al._, High-Resolution Imaging of Molecular Line Emission from High
Redshift QSOs. _Astron. J._ **123**, 1838–1846 (2002).


13. J. Wagg _et al._, Karl G. Jansky Very Large Array Observations of Cold Dust and Molecular

Gas in Starbursting Quasar Host Galaxies at z ~ 4.5. _Astrophys. J._ **783**, 71 (2014).


14. Materials and methods are available as supplementary materials.


15. J. Wagg _et al._, [CII] line emission in BRI 1335-0417 at z = 4.4. _Astron. Astrophys._ **519**, L1

(2010).


16. G. C. Jones _et al._, New constraints on the molecular gas in the prototypical HyLIRGs BRI

1202–0725 and BRI 1335–0417. _Astrophys. J._ **830**, 1–12 (2016).


9

17. D. A. Riechers, F. Walter, C. L. Carilli, F. Bertoldi, E. Momjian, Formation of a Quasar

Host Galaxy through a Wet Merger 1.4 Billion Years after the Big Bang. _Astrophys. J. Lett._
**686**, L9 (2008).


18. J. L. Pineda, W. D. Langer, T. Velusamy, P. F. Goldsmith, A Herschel [C ii] Galactic plane

survey. I. The global distribution of ISM gas components. _Astron. Astrophys._ **554**, A103
(2013).


19. Y. Sofue, J. Koda, H. Nakanishi, S. Onodera, The Virgo High-Resolution CO Survey: II.

Rotation Curves and Dynamical Mass Distributions. _Publ. Astron. Soc. Jpn._ **55**, 59–74
(2003).


20. A. Burkert _et al._, The Angular Momentum Distribution and Baryon Content of Star-forming

Galaxies at z ∼ 1-3. _Astrophys. J._ **826**, 214 (2016).


21. A. W. Green _et al._, High star formation rates as the origin of turbulence in early and modern

disk galaxies. _Nature_ . **467**, 684–686 (2010).


22. G. C. Jones _et al._, Dynamical Characterization of Galaxies at z ˜ 4-6 via Tilted Ring Fitting

to ALMA [C II] Observations. _Astrophys. J._ **850**, 180 (2017).


23. D. A. Gadotti, Structural properties of pseudo-bulges, classical bulges and elliptical

galaxies: a Sloan Digital Sky Survey perspective. _Mon. Not. R. Astron. Soc._ **393**, 1531–
1552 (2009).


24. C. Dobbs, J. Baba, Dawes Review 4: Spiral Structures in Disc Galaxies. _Publ. Astron. Soc._

_Aust._ **31**, e035 (2014).


25. J. Kormendy, L. C. Ho, Coevolution (Or Not) of Supermassive Black Holes and Host

Galaxies. _Annu. Rev. Astron. Astrophys._ **51**, 511 (2013).


26. G. A. Shields, K. L. Menezes, C. A. Massart, P. Vanden Bout, The Black Hole-Bulge

Relationship for QSOs at High Redshift. _Astrophys. J._ **641**, 683–688 (2006).


27. J. E. Mejía-Restrepo, P. Lira, H. Netzer, B. Trakhtenbrot, D. M. Capellupo, The effect of

nuclear gas distribution on the mass determination of supermassive black holes. _Nat._
_Astron._ **2**, 63–68 (2018).


28. A. Schulze, L. Wisotzki, Accounting for selection effects in the BH-bulge relations: no

evidence for cosmological evolution. _Mon. Not. R. Astron. Soc._ **438**, 3422–3433 (2014).


29. A. Dekel, A. Burkert, Wet disc contraction to galactic blue nuggets and quenching to red

nuggets. _Mon. Not. R. Astron. Soc._ **438**, 1870–1879 (2014).


30. M. Kohandel _et al._, Kinematics of z ≥ 6 galaxies from [C II] line emission. _Mon. Not. R._

_Astron. Soc._ **487**, 3007–3020 (2019).


10

31. J. Ren _et al._, Long Tidal Tails in Merging Galaxies and Their Implications. _Mon. Not. R._

_Astron. Soc._ **499**, 3399–3409 (2020).


32. J. Baba, Short-term dynamical evolution of grand-design spirals in barred galaxies. _Mon._

_Not. R. Astron. Soc._ **454**, 2954–2964 (2015).


33. A. Dekel _et al._, Cold streams in early massive hot haloes as the main mode of galaxy

formation. _Nature_ . **457**, 451–454 (2009).


34. C. L. Bennett, D. Larson, J. L. Weiland, G. Hinshaw, The 1% Concordance Hubble

Constant. _Astrophys. J._ **794**, 135 (2014).


35. S. Iguchi, Radio Interferometer Sensitivities for Three Types of Receiving Systems: DSB,

SSB, and 2SB Systems. _Publ. Astron. Soc. Jpn._ **57**, 643 (2005).


36. A. Remijan _et al._, ALMA Cycle 7 Technical Handbook (2019),

doi:10.5281/zenodo.4511522.


37. J. P. McMullin, B. Waters, D. Schiebel, W. Young, K. Golap, in _Astronomical Data_

_Analysis Software and Systems XVI_, R. A. Shaw, F. Hill, D. J. Bell, Eds., vol. 376 of
_Astronomical Society of the Pacific Conference Series_ (Astronomical Society of the Pacific,
2007), p. 127.


38. D. S. Briggs, High Fidelity Interferometric Imaging: Robust Weighting and NNLS

Deconvolution. _Bull. Am. Astron. Soc._ **27**, 1444 (1995).


39. T. M. Dame, Optimization of Moment Masking for CO Spectral Line Surveys.

_ArXiv11011499 Astro-Ph_ (2011) (available at http://arxiv.org/abs/1101.1499).


40. T. A. Davis, M. Bureau, M. Cappellari, M. Sarzi, L. Blitz, A black-hole mass measurement

from molecular gas kinematics in NGC4526. _Nature_ . **494**, 328–330 (2013).


41. D. Krajnović, M. Cappellari, P. T. De Zeeuw, Y. Copin, Kinemetry: A generalization of

photometry to the higher moments of the line-of-sight velocity distribution. _Mon. Not. R._
_Astron. Soc._ **366**, 787–802 (2006).


42. C. Y. Peng, L. C. Ho, C. D. Impey, H.-W. Rix, Detailed Decomposition of Galaxy Images.

II. Beyond Axisymmetric Models. _Astron. J._ **139**, 2097–2129 (2010).


43. R. Lange _et al._, Galaxy And Mass Assembly (GAMA): M_star - R_e relations of z = 0

bulges, discs and spheroids. _Mon. Not. R. Astron. Soc._ **462**, 1470–1500 (2016).


44. S. P. Driver _et al._, The Millennium Galaxy Catalogue: morphological classification and

bimodality in the colour-concentration plane. _Mon. Not. R. Astron. Soc._ **368**, 414–434
(2006).


45. S. van der Walt _et al._, scikit-image: image processing in Python. _PeerJ_ . **2**, e453 (2014).

doi:10.7717/peerj.453


11

46. I. Puerari, H. A. Dottori, Fourier analysis of structure in spiral galaxies. _Astron. Astrophys._

_Suppl. Ser._ **93**, 469 (1992).


47. M. D. Smith _et al._, WISDOM project - IV. A molecular gas dynamical measurement of the

supermassive black hole mass in NGC 524. _Mon. Not. R. Astron. Soc._ **485**, 4359–4374
(2019).


48. S. M. Kent, Dark matter in spiral galaxies. I. Galaxies with optical rotation curves. _Astron._

_J._ **91**, 1301 (1986).


49. Y. Sofue, M. Honma, T. Omodaka, Unified Rotation Curve of the Galaxy -- Decomposition

into de Vaucouleurs Bulge, Disk, Dark Halo, and the 9-kpc Rotation Dip --. _Publ. Astron._
_Soc. Jpn._ **61**, 227–236 (2009).


50. R. Genzel _et al._, Strongly baryon-dominated disk galaxies at the peak of galaxy formation

ten billion years ago. _Nature_ . **543**, 397–401 (2017).


51. N. M. Förster Schreiber _et al._, The SINS Survey: SINFONI Integral Field Spectroscopy of z

~ 2 Star-forming Galaxies. _Astrophys. J._ **706**, 1364–1428 (2009).


52. S. Wuyts _et al._, KMOS3D: Dynamical Constraints on the Mass Budget in Early Star
forming Disks. _Astrophys. J._ **831**, 149 (2016).


53. P. Lang _et al._, Bulge Growth and Quenching since z = 2.5 in CANDELS/3D-HST.

_Astrophys. J._ **788**, 11 (2014).


54. V. A. Bruce _et al._, The bulge-disc decomposed evolution of massive galaxies at 1 < z < 3 in

CANDELS. _Mon. Not. R. Astron. Soc._ **444**, 1001 (2014).


55. G. de Vaucouleurs, Recherches sur les Nebuleuses Extragalactiques. _Ann. d’Astrophys._ **11**,

247 (1948).


56. A. W. Graham, S. P. Driver, A Concise Reference to (Projected) Sérsic R1/n Quantities,

Including Concentration, Profile Slopes, Petrosian Indices, and Kron Magnitudes. _Publ._
_Astron. Soc. Aust._ **22**, 118–127 (2005).


57. J. Binney, S. Tremaine, _Galactic Dynamics_ : Second Edition. (Princeton. Univ. Press,

Princeton, NJ, 2008).


58. E. Noordermeer, The rotation curves of flattened Sérsic bulges. _Mon. Not. R. Astron. Soc._

**385**, 1359–1364 (2008).


59. N. Katz, J. E. Gunn, Dissipational Galaxy Formation. I. Effects of Gasdynamics. _Astrophys._

_J._ **377**, 365 (1991).


60. R. Genzel _et al._, The SINS/zC-SINF Survey of z ~ 2 Galaxy Kinematics: Evidence for

Gravitational Quenching. _Astrophys. J._ **785**, 75 (2014).


12

61. A. Burkert _et al._, High-redshift Star-forming Galaxies: Angular Momentum and Baryon

Fraction, Turbulent Pressure Effects, and the Origin of Turbulence. _Astrophys. J._ **725**, 2324
(2010).


62. K. C. Freeman, On the Disks of Spiral and S0 Galaxies. _Astrophys. J._ **160**, 811 (1970).


63. A. Zanella _et al._, The [C II] emission as a molecular gas mass tracer in galaxies at low and

high redshifts. _Mon. Not. R. Astron. Soc._ **481**, 1976–1999 (2018).


64. B. Gullberg _et al._, The Dust and [C ii] Morphologies of Redshift ~ 4.5 Sub-millimeter

Galaxies at ~ 200 pc Resolution: The Absence of Large Clumps in the Interstellar Medium
at High-redshift. _Astrophys. J._ **859**, 12 (2018).


65. E. Wisnioski _et al._, The KMOS3D Survey: Design, First Results, and the Evolution of

Galaxy Kinematics from 0.7 <= z <= 2.7. _Astrophys. J._ **799**, 209 (2015).


66. P. Lang _et al._, Falling Outer Rotation Curves of Star-forming Galaxies at 0.6 ≲ z ≲ 2.6

Probed with KMOS3D and SINS/zC-SINF. _Astrophys. J._ **840**, 92 (2017).


67. D. Foreman-Mackey, D. W. Hogg, D. Lang, J. Goodman, emcee: The MCMC Hammer.

_Publ. Astron. Soc. Pac._ **125**, 306–312 (2013).


68. R. C. E. Van Den Bosch, G. Van De Ven, Recovering the intrinsic shape of early-type

galaxies. _Mon. Not. R. Astron. Soc._ **398**, 1117–1128 (2009).


69. E. V. North _et al._, WISDOM project - V. Resolving molecular gas in Keplerian rotation

around the supermassive black hole in NGC 0383. _Mon. Not. R. Astron. Soc._ **490**, 319–330
(2019).


70. M. Mitzkus, M. Cappellari, C. J. Walcher, Dominant dark matter and a counter-rotating

disc: MUSE view of the low-luminosity S0 galaxy NGC 5102. _Mon. Not. R. Astron. Soc._
**464**, 4789 (2017).


71. T. A. Davis _et al._, WISDOM Project - II. Molecular gas measurement of the supermassive

black hole mass in NGC 4697. _Mon. Not. R. Astron. Soc._ **468**, 4675–4690 (2017).


72. N. Lu _et al._, CO (7-6), [C I] 370 μm, and [N II] 205 μm Line Emission of the QSO BRI

1335-0417 at Redshift 4.407. _Astrophys. J._ **864**, 38 (2018).


73. J. S. Spilker _et al._, Ubiquitous Molecular Outflows in z > 4 Massive, Dusty Galaxies. I.

Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc Scales.
_Astrophys. J._ **905**, 85 (2020).


74. A. Toomre, On the gravitational stability of a disk of stars. _Astrophys. J._ **139**, 1217–1238

(1964).


75. P. Goldreich, D. Lynden-Bell, I. Gravitational stability of uniformly rotating disks. _Mon._

_Not. R. Astron. Soc._ **130**, 97 (1965).


13

76. M. Cappellari, Improving the full spectrum fitting method: accurate convolution with

Gauss–Hermite functions. _Mon. Not. R. Astron. Soc._ **466**, 798–811 (2017).


**Acknowledgments:**


We thank K. Tadaki, Y. Matsuda, Y. Harikane, D. Iono, I. Mitsuhashi and S. Fujimoto for


discussions about high redshift submillimeter galaxies, K. Onishi and D. Nguyen for discussions


on the gas dynamics in galaxies, and H. Mikami, J. Ueda and H. Nagai for support of the ALMA


data reduction. ALMA is a partnership of ESO (representing its member states), NSF (USA) and


NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (South


Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by


ESO, AUI/NRAO and NAOJ. Data analysis was in part carried out on the common-use data


analysis computer system at the East Asian ALMA Regional Center (EA ARC) and the


Astronomy Data Center (ADC) of the National Astronomical Observatory of Japan (NAOJ).


**Funding:** T.T was partially supported by Overseas Travel Fund for Students (2019) of the


Department of Astronomical Science, the Graduate University for Advanced Studies,


SOKENDAI. **Author contributions:** T.T. led the data analysis. T.T. and S.I. discussed the


interpretation of the results and wrote the manuscript. **Competing interests:** We declare no


competing interests. **Data and materials availability:** The ALMA pipeline calibrated data and


raw data are available at http://almascience.nrao.edu/aq/ under project code ADS/JAO.ALMA


#2017.1.00394.S. Part of the ALMA data were retrieved from the JVO portal


(http://jvo.nao.ac.jp/portal/) operated by ADC/NAOJ. Supplementary data files contain the


observed [CII] data cube cutout used for dynamical modeling (data S1), model [CII] data cube


from K IN MS (data S2), observed full [CII] data cube used for displaying a spectrum (data S3),


and observed dust continuum image (data S4). Our derived model values are listed in Tables S1


and S2.


14

**Supplementary Materials:**


Materials and Methods


Figures S1-S6


Tables S1-S2


References ( _34-76_ )


Data S1 to S4



15

**A** **B**


[C II ] [C II ] velocity Major axis











**E**



**C** **D**


**F**







**Fig. 1. Morphology and kinematics of [C** **II** **] line and dust continuum emission in BRI 1335-**


**0417.** ( **A** ) and ( **B** ) the ALMA [C II ] line maps of intensity (moment 0) and intensity-weighted


velocity (moment 1). The kinematic major and minor axes are shown in panel B by black solid


and dotted lines, respectively. ( **C** ) the ALMA dust continuum map at a rest-frame frequency of


1863 GHz. ( **D** ) a composite color image showing in red the redshifted gas emission with velocity


of 30 to 150 km s [-1], in yellow gas at the systemic velocity of -30 to 30 km s [-1], and in blue the


16

blueshifted gas with velocity of -150 to -30 km s [-1] . The FWHM of the synthesized beam is 0.20"


× 0.16" in (A), (B) and (D), and 0.17" × 0.14" in (C), which are shown by an ellipse in the


bottom left corners. The RA and Dec offsets are given relative to the position (J2000)


13 [h] 38 [m] 03 [s] .416, -4°32'35”.02 throughout this paper. ( **E** ) PVD of the observed [C II ] line emission,


extracted along the kinematic major axis shown in panel B, which has a position angle of 4.5°


(Table S1). Data were averaging over one beam width (three pixels). ( **F** ) the velocity dispersion


measured from the line profile at each position of PVD. The error bars correspond to the sum in


quadrature of the profile fitting uncertainty (95% confidence level) and the velocity channel


width. The red dashed line shows the estimated intrinsic velocity dispersion of 71 #-1114 km s -1 .


Positive position in panels (E) and (F) is the direction toward the north along the kinematic major


axis in (B).


17

**Fig. 2. Velocity channel maps of the [C** **II** **] line emission, showing the spiral structure.** Each


panel shows an image at each velocity of the [C II ] line emission, labelled in the top left. Overline


with white lines is the best-fitting two-armed logarithmic spiral model, which has a pitch angle a


18

= 26.7° ( _14_ ). The images have been de-projected to be viewed as face-on using a position angle of


4.5° and inclination of 37.8° (Table S1) ( _14_ ). The FWHM of the synthesized beam is shown by


the white ellipse in the left bottom of each panel.


19

### **A B**

**Fig. 3. Fourier analysis of the [C** **II** **] line emission.** ( **A** ) Fourier spectra ( _14_ ) of model logarithmic


spirals with _m_ armes and pitch angles _α_ . The black solid lines show normalized amplitude as a


function of the dimensionless parameter _p_ = - _m_ /tan(a). The blue shaded region indicates the


estimated noise level ( _14_ ). The _m_ = 2 mode has the strongest peak at a pitch angle of 26.7 +4.1-1.6 °


(dashed vertical line). ( **B** ) the [C II ] line intensity image (de-projected version of Fig. 1A) overlaid


with the best-fitting two-armed logarithmic spiral (white line, same as in Fig. 2). The FWHM of


the synthesized beam is shown by an ellipse in the left bottom corner. The inner and outer dotted


lines indicate the boundaries of the region used in the Fourier analysis ( _14_ ).


20

Supplementary Materials for


Spiral morphology in an intensely star-forming disk galaxy more than 12 billion years ago


Takafumi Tsukui*, Satoru Iguchi


Correspondence to: t.tsukui@grad.nao.ac.jp

**This PDF file includes:**


Materials and Methods
Figs. S1 to S6
Tables S1 to S2
Captions for Data S1 to S4

**Other Suplementary Materials for this manuscript includes the following:**

Data S1 to S4


21

**Materials and Methods**
Cosmology
The conversion from the angular size (arcsec) to the physical size (kpc) is based on a concordance, flat lambda cold
dark matter (ΛCDM) cosmology with density parameter of pressureless matter, W m = 0.286 and present-day Hubble
constant, _H_ 0 = 69.6 km s [-1] Mpc [-1] ( _34_ ), providing the spatial scale of 6.808 kpc arcsec [-1] .

ALMA observation
The rest frame frequency of the [C II ] line is 1900.5369 GHz. Because the highest observing frequency of the ALMA
is 950 GHz, the [C II ] line emission is not detectable from local galaxies. In the distant galaxies ( _z_ - 1), however, [C II ]
line is redshifted to the frequency range which can be observed with ALMA. At the redshift for BRI 1335-0417 of _z_
= 4.4074 ( _11_ ), the [C II ] line of 1900.5369 GHz is shifted to 351.470 GHz and can be observed with ALMA Band 7
(275 – 373 GHz) that has two single sideband (2SB) receiver systems ( _35_ ), providing upper sideband (USB) and lower
sideband (LSB) simultaneously with the intermediate frequency (IF) bandwidth of 4-8 GHz. We retrieved archival
ALMA observations obtained on 2018 January 21 in the observing frequency range of 337.434 GHz -341.433 GHz
(LSB) and 349.705 GHz -353.271 GHz (USB), so the USB contains the redshifted [C II ] line emission. The LSB
consists of two spectral windows, each of which has 128 frequency channels with the widths of 15.625 MHz, while
USB consists of two spectral windows, each of which has 1920 frequency channels with the widths of 977 kHz. The
total bandwidths of LSB and USB were 4 GHz and 3.75 GHz respectively. The observation was executed in the C435 array configuration with baseline lengths of 15 m to 1398 m. The 5th percentile shortest baseline of the configuration
was 70 m, providing the maximum recoverable scale of 2.47 arcsecond at 351.47 GHz [( _36_ ) their equation 7.7]. Total
observing time was 2.0 h including on-source time of 1.0 h and the other 1.0 h for calibration sources and overhead.
QSO B1334-127 (VCS1 J1337-1257) was utilized as a flux and bandpass calibrator and NGC 5232 (VCS1 J13360829) as a phase calibrator.

Data analysis and imaging
We performed data reduction using version 5.1.1 of the Common Astronomy Software Applications (C ASA ) ( _37_ )
pipeline. We first imaged the dust continuum emission shown in Fig. 1C using the line-free channels (with a 4.75 GHz
total bandwidth over both side bands at a central frequency of 345 GHz in the observed frame corresponding to 1863
GHz in the rest frame) using the task tclean in C ASA . We identified the line-free channels using the hif_findcont task
in C ASA and additionally removed channels which show a dip feature around ~ 352.3 GHz due to atmospheric
absorption. The visibility data were weighted by the Briggs scheme with a robust parameter of 0.0 which provides a
trade-off between resolution and sensitivity ( _38_ ), resulting in a synthesized beam with FWHM 0.17" × 0.14" (~1.16
kpc × 0.95 kpc in physical scale) at a position angle of 86° and a root mean square noise of 0.036 mJy beam [-1] . Secondly,
we imaged the [C II ] line emission shown in Fig. 1 (A and B) and Fig. S1 (A and D). We measured the flux density of
the dust continuum emission by fitting a linear function to the line-free channels and subtracted its emission
components from the visibility data using the task uvcontsub in C ASA . After continuum subtraction, we imaged two
spectral windows of the USB to produce a data cube with the three dimensions of right ascension, declination and
velocity using the task tclean in C ASA . The velocity channel resolution was 20 km s [-1] (=23.4 MHz) after binning by
24 frequency channels of 977 kHz, to improve the signal to noise ratio. The visibility data were weighted by the
Briggs scheme with a robust parameter of 0.5, resulting in a synthesized beam with FWHM 0.20" × 0.16"
(~1.33 kpc × 1.11 kpc in physical scale) at a position angle of 80°. The synthesized beam (i.e. point spread function)
is shown in Fig S2; there are negligible side lobes, due to the broad uv coverage of this data. The root mean square
noise of each velocity channel with a width of
20 km s [-1 ] is about 0.35 mJy beam [-1] . The clean threshold was set to 1.5 times the rms noise for the dust continuum
image, and 1.0 times rms noise for [C II ] line image, to maximize the flux in the cleaned model. The clean mask was
drawn closely around the areas of source emission. For both dust continuum and [C II ] line images, the cellsize was
chosen to be roughly one third of the minor synthesized beam width. Primary beam correction was performed, which
was smaller than 1% at the edge of the images. Figures 1 (A and B) and Figures S1 (A and D) show images of the
integrated flux and line-of-sight velocity respectively. Figures 1B and Figures S1D were made by the masked moment
method ( _39_ ). The observed data cube was smoothed by convolving with a uniform filter spatially (1.5 times the beam
size) and spectrally (4 times the channel width), then the mask area was determined by the intensity threshold (7.5
times the root mean square noise in the smoothed cube) and applied to the original observed cube. Finally, these
velocity images (Moment 1) were created from the masked cube using plotting code in K IN MS package ( _40_ ). The
filter size and threshold of the mask were selected so the mask covered the [C II ] line emission area.


22

The size and inclination of the disk
Both the dust continuum and [C II ] line intensity distributions of BRI 1335-0417 include complex structures which
may indicate a disk and spiral arms. The position angle of the disk was estimated by using P A F IT Package ( _41_ ) from
the [C II ] line velocity image (Moment 1), which shows the regular rotation and kinematic position angle. The central
0.5" region in [C II ] line velocity image was utilized for measuring position angle, as this region features sufficient
signal to noise ratio. The estimated position angle is 4.5 ± 3.7° (95% confidence interval). We also derived the position
angle of the disk from the gas dynamical modeling (see below), finding 7.6 +7.-7.13 ° at 95% confidence level. To estimate



angle of the disk from the gas dynamical modeling (see below), finding 7.6 +7.-7.13 ° at 95% confidence level. To estimate

the axis ratio of the disk with the estimated position angle, we fitted 2-dimensional (2D) Sérsic functions to the dust
continuum image (see Fig 1C) and the [C II ] line intensity image (Fig. 1A and Fig. S1A), using G ALFIT code ( _42_ ).
While fitting these images, the synthesized beam was taken into account. From the estimated axis ratio ( _q_ ) of the dust
continuum image, the inclination of the disk _i_ = 37.8 +2.4-3.3 ° was calculated with equation _q_ = cos( _i_ ) and the confidence



continuum image, the inclination of the disk _i_ = 37.8 +2.4-3.3 ° was calculated with equation _q_ = cos( _i_ ) and the confidence

interval was estimated from the uncertainty of the measured position angle. This estimated inclination was used as a
prior in our MCMC sampling (see below), where the gas dynamical modeling finds 37.3 +3.0-3.1 ° at 95% confidence level.



prior in our MCMC sampling (see below), where the gas dynamical modeling finds 37.3 +3.0-3.1 ° at 95% confidence level.

As G ALFIT outputs, the measured Sérsic index is _n_ = 0.87 ± 0.02 (close to exponential _n_ =1) from the [C II ] line intensity
distribution, while it is _n_ = 2.48 ± 0.05 from the distribution of the dust continuum emission. These indicate that the

[C II ] line distribution has shallow and near exponential profile like a typical disk ( _23_, _43_ ), while the dust continuum
distribution has centrally concentrated profile with high Sérsic index ( _n_ - 2) compatible with that of a typical galaxy
with a bulge ( _44_ ). We therefore fitted a 2D exponential function to the [C II ] line intensity image, resulting in a diskscale radius _R_ d = 1.83 ± 0.04 kpc. The physical parameters derived in this section are listed in Table S1.

Spiral structure
To quantitatively measure the degree of the spiral structure, we decomposed the [C II ] line intensity distribution of
BRI 1335-0417 into _m_ -armed logarithmic spirals, which is expressed as



_ρ_ = _ρ_ 0 exp (


_mp_ [(] _[φ]_ [+] _[φ]_ [0] [)) ] (S1)



in polar coordinates (r, j). _p_ is a variable related to the pitch angle a by _p_ = - _m_ /tan(a), and r 0 and j 0 are arbitrary
constants. We first deprojected the [C II ] line intensity image to be viewed as face-on using the position angle 4.5°
and inclination 37.8° measured above (Table S1). The image rotation and stretching for the deprojection were
performed using SCIKIT - IMAGE package ( _45_ ), in which mapping the original pixels onto a new pixel grid was done by
Bi-linear spline interpolation. From the deprojected image, we then calculated the Fourier amplitude _A_ ( _3_, _46_ ), which
indicates the magnitude of the _m_ -armed logarithmic spirals. It follows that



_A_ ( _p_, _m_ ) =



_D_ 1 [∑] N _j_ =1 _f_ _j_ exp $- _i_ $ _pu_ _j_ + _mφ_ _j_ % % (S2)



where _D_ = ∑ N _j_ = 0 _f_ j is the sum of the flux _f_ _j_ of the pixel _j_ in the image, _u_ _j_ is the logarithmic radius from the center of the

image and j _j_ is the polar angle. We excluded the central region of 1.6 kpc and the region outside of 7.2 kpc (see Fig.
3B) for the calculation of _A_ ( _p_, _m_ ) to avoid the effects of unresolved components and noise. The center of the polar
coordinate was defined as the pixel which has a peak intensity in the [C II ] line image.

Figure 3A shows the Fourier amplitude _A_ ( _p_, _m_ ) as a function of _p_ for _m_ = 1, 2, 3, 4. Its underlying noise level
was estimated by applying equation (S2) on 300 noise maps extracted from the emission line region of the data cube
and computing their 84 [th] percentile. The strongest peak is seen in _m_ = 2 at _p_ = - 4.0 +0.6-0.3, corresponding to spiral arms



N

_j_ = 0 _f_ j is the sum of the flux _f_ _j_ of the pixel _j_ in the image, _u_ _j_ is the logarithmic radius from the center of the



and computing their 84 [th] percentile. The strongest peak is seen in _m_ = 2 at _p_ = - 4.0 +0.6-0.3, corresponding to spiral arms

+4.1

with a pitch angle of _α_ = 26.7 -1.6 ° at the 95% confidence level. The confidence interval was estimated from the



+4.1

with a pitch angle of _α_ = 26.7 -1.6 ° at the 95% confidence level. The confidence interval was estimated from the

uncertainties of the position angle and inclination of the disk. Figure 3B shows the deprojected [C II ] line intensity
image by using the derived inclination and position angle. The two-armed logarithmic spirals ( _m_ = 2) is plotted using
equation (S1) with r 0 = 2.2 kpc and j 0 = 55° in Fig 2 and Fig. 3B (a white solid line).

Gas dynamical modeling
We used the K IN MS code ( _40_ ) to produce a gas dynamical model cube which has the same beam size and velocity
resolution as those in the observed cube (i.e. beam smearing effect was taken into account for the model cube). It
requires a set of gas particles which approximates the distribution of gas intensity in physical space (right ascension,
declination and distance along the line of sight), and then the line-of-sight velocity of each particle is calculated by
taking a circular velocity of the galaxy as an input. The S KYSAMPLER code ( _47_ ) was used to generate gas particles that



23

reproduce the [C II ] line intensity profile of BRI 1335-0417 by using the de-convolved CLEAN components that were
provided by a task of tclean in C ASA . Then, it transformed the distribution of gas particles from the sky plane into the
physical space using the inclination and position angle of the galactic disk.
In general, the structure of disk galaxies consists of a central black hole, a centrally concentrated bulge, an
extended disk and a dark matter halo ( _48_ – _50_ ). The circular velocity _v_ circ ( _r_ ) of the galaxy can be expressed by

_v_ circ ( _r_ ) [2] = _v_ BH ( _r_ ) [2] + _v_ bulge ( _r_ ) [2] + _v_ disk ( _r_ ) [2] + _v_ DM ( _r_ ) [2] (S3),
where _r_ denotes the radial distance from the galaxy center, and _v_ BH ( _r_ ), _v_ bulge ( _r_ ), _v_ disk ( _r_ ) and _v_ DM ( _r_ ) are the circular
velocity of a test particle at _r_ due to the gravitational potential of the central black hole, bulge, disk, and dark matter,
respectively. The sphere of influence of the black hole _R_ SOI = _GM_ BH /𝜎 ⋆& = 0.02" where the _G_ is the gravitational

constant, _M_ BH is the mass of the black hole and 𝜎 ⋆ is the stellar velocity dispersion, was calculated for a mass of 6 ´
10 [9] 𝑀 ⨀, which was estimated using the virial theorem in a previous study ( _26_ ), assuming the local relationship
between black hole mass and stellar velocity dispersion ( _25_ ). Because estimated _R_ SOI is much smaller than our spatial
resolution, we cannot measure the circular velocity of black hole _v_ BH ( _r_ ) and bulge _v_ bulge ( _r_ ) separately. We thus included
the black hole mass in the bulge. In this case, _v_ bulge ( _r_ ) is equal to _v_ BH ( _r_ ) in the limit that the size of the bulge goes to 0,
allowing a possibility of a black hole without a bulge. The mass contribution of dark matter is typically smaller than
that of the baryonic structure such as the bulge and disk within the radius of < 10 kpc, which are suggested by the
recent observation for high redshift galaxy ( _50_ – _52_ ). In this object, the [C II ] line emission is detected only up to 5 kpc,
which is not sufficient to measure the mass distribution of the dark matter using the kinematics. We therefore excluded
the dark matter mass distribution from our dynamical model. A circular velocity _v_ circ ( _r_ ) of the galaxy is then
approximated by

_v_ circ ( _r_ ) [2] = _v_ bulge ( _r_ ) [2] + _v_ disk ( _r_ ) [2] (S4).

Bulge model
In the PVD shown in Fig. 1E, there is a steep rise of [C II ] line velocity reaching about 240 to 260 km s [-1] in the galactic
center, indicating a centrally concentrated mass distribution such as a bulge. Observations of nearby galaxies ( _23_, _43_ )
and distant galaxies (2 < _z_ < 3) ( _53_, _54_ ) indicate that the observed surface brightness distributions of a bulge can be
approximated by de Vaucouleurs profile ( _55_ ). Assuming the bulge has the same mass profile as its brightness profile,
we can express the surface mass density distribution using the de Vaucouleurs profile:



_Σ_ bulge (R)= _Σ_ e exp{- _κ_ [ $



_R_

_R_ e ~~[%]~~



_R_



1
4 -1]} (S5),



where k ~ 7.6695 ( _56_ ), _R_ is the projected radius on the plane of the sky and 𝛴 ( is the surface mass density at the
effective radius _R_ e in which the enclosed mass becomes half of the total mass of the bulge _M_ bulge . The total mass of
the bulge is then given by _M_ bulge ~ 22.665 _R_ e [2] S e ( _49_ ). In the case of a spherical bulge, the circular velocity of the bulge
_v_ bulge ( _r_ ) at _r_ can be determined by two parameters: the total mass of the bulge _M_ bulge and the effective radius _R_ e . It
follows that ( _57_, _58_ )



_l_ =0 _r_ [ ∫ _R_ ∞= _l_ bul d _R_ ge + _R_ d [2] _R_ - _l_ [2] _[l]_ [2] []d] _[l]_ (S6).



_v_ 2bulge ( _r_ )=


4 _G_



_r_ [∫] _l_ =0 [ ∫



d _Σ_ bulge ( _R_ )



d _R_



d _R_



The circular velocity of spherical structure differs from that of non-spherical one. In the case of a non-spherical
structure with an axial ratio greater than 0.6, however, the difference between them is less than 8 percent, allowing us
to use spherical assumption for simplicity.

Disk model
An exponential disk profile is predicted by the theory of galactic disk formation ( _59_ ) and observed in nearby galaxies
( _23_, _43_ ) and distant galaxies ( _z_ ~ 2-3) ( _52_ – _54_, _60_ ). In addition, the exponential profile has been widely used for disk
mass distribution in modeling the galactic dynamics including the Milky Way ( _49_, _50_, _61_ ). A surface mass density
distribution of an exponential disk is given by

S disk ( _R_ ) = S 0 exp(- _R_ / _R_ d ) (S7),
where _R_ d is a disk-scale radius and S 0 is the central surface mass density. The circular velocity of the disk can be
determined from two parameters: the disk-scale radius _R_ d and the total mass of the disk _M_ disk = 2pS 0 _R_ d [2] . It follows
that ( _62_ )

_v_ disk ( _r_ ) [2] = 4p _G_ S 0 _R_ d _y_ [2] [I 0 ( _y_ )K 0 ( _y_ )-I 1 ( _y_ )K 1 ( _y_ )] (S8),


24

where _y_ = _r_ /(2 _R_ d ). I 0, K 0, I 1 and K 1 are modified Bessel functions. Several studies suggest that the [C II ] line is a good
tracer of the total gas mass ( _63_, _64_ ). The [C II ] intensity distribution of this object is well matched by the exponential
profile. We therefore used _R_ d = 1.83 kpc measured by the G ALFIT code (Table S1).

Rotation velocity of pressurized galactic disk
The PVD in Fig.1E shows that BRI 1335-0417 has velocity dispersions of ~70 km s [-1] in the outer parts. The intrinsic
velocity dispersion averaged for galaxies at _z_ ~ 2.3 is 50 km s [-1] but there are a wide range of values up to ~ 80 km s [-1],
and for galaxies at _z_ ~ 0.9 is 25 km s [-1] ( _65_ ). The pressure in the gas disk is proportional to the square of the velocity
dispersions of the gas, which is not negligible for the gas dynamical modeling ( _61_ ). The pressure gradient causes a
radial force that balances part of the gravitational force, resulting in the reduction of the rotational velocity of the gas.
Under hydrostatic equilibrium, the rotational velocity _v_ rot ( _r_ ) for the exponential gas distribution is given by ( _20_, _61_ )



_v_ rot ( _r_ ) [2] = _v_ circ ( _r_ ) [2] + 2𝜎,

= _v_ circ ( _r_ ) [2]     - 2𝜎,



2 ×



dln _Σ_ gas

dln _r_ [(] _[r]_ [) ]



2 × (



_Rr_ d [) ] (S9),



where 𝜎, is the intrinsic velocity dispersion of the gas, and S gas ( _r_ ) is the surface density distribution of the gas disk,
which was assumed to be exponential with the disk-scale radius _R_ d (Table S1). Because the velocity dispersion is
constant over this galaxy except in the central region [Fig. 1 (E and F) and Fig. S1(G and H)], we adopted an isotropic
and spatially uniform velocity dispersion. This is consistent with previous works ( _20_, _50_, _66_ ). Given the high velocity
dispersion, we considered the disk thickness of _h_ ~ (𝜎, / _v_ rot ( _R_ d ))´1.68 _R_ d ( _50_ ), correcting equation (S8) ( _58_ ).

MCMC fitting
We determined best-fitting model parameters and their associated confidence intervals with a Markov Chain Monte
Carlo (MCMC) sampling using the EMCEE code ( _67_ ), that is an implementation of affine invariant MCMC ensemble
sampler. We directly compared the observed cube with the model cube, then derived the following eight physical
parameters: the position angle and inclination of disk (G, _i_ ), the masses of the central compact structure and the disk
( _M_ bulge, _M_ disk ), the effective radius of the compact structure ( _R_ _e_ ) and the offsets between the observed and model cubes
in right ascension, declination and velocity (D _x_, D _y_, D _v_ ). Following the Bayesian framework, the posterior probability
distribution of a set of these physical parameters 𝜃 on the data is

_P_ (q|data) µ _P_ (q) ´ _P_ (data|q) (S10),
where _P_ (q) is the assumed prior probability distribution of the physical parameters, and _P_ (data|q) is the likelihood
that is the probability of obtaining the data on the given parameters q. Because the inclination of the disk _i_ was
estimated with G ALFIT above (Table S1), the prior distribution was set to be a Gaussian, characterized by the estimated
central value and the associated uncertainty. We used log uniform prior distribution for the mass of the bulge _M_ bulge
and disk _M_ disk to cover the multiple orders of magnitude, while uniform prior distribution for the other 5 parameters.
The range was set to values much larger than expected from the data. The likelihood can be written as



_P_ (data|q) µ exp(-c(q) [2] /2) (S11)
_χ_ ( _θ_ ) [2] = Σ _Ni_ =0 [( _I_ data, _i_ – _I_ model, _i_ ( _θ_ ) ) [2] ]



_Ni_ =0 [(



_I_ data, _i_ – _I_ model, _i_ ( _θ_ )



_σ_ rmsmodel, _i_ ) [2] ] (S12),



where _I_ data, _i_ and _I_ model, _i_ (q) are the intensity of the pixel _i_ in the observed cube and model cube respectively. s rms is the
root mean square noise of 0.35 mJy beam [-1 ] that was measured using the pixels of only line-free channels in the
observed cube under the assumption that it is constant over the cube. The likelihood was computed using the observed
cube over the velocity range from
-390 km s [-1] to +370 km s [-1] with the velocity center 0 km s [-1] matched to the frequency of 351.470 GHz in barycentric
frame.

In the standard c [2] statistic, the 68% confidence interval corresponds to Dc [2 ] = c [2]    - c min [2] = 1. A variance of this
distribution is 2( _N_ - _O_ ) where _N_ is the number of constraints and _O_ is the number of inferred parameters. In our data
( _N_ ~ 4 ´ 10 [4] and _O_ = 8), it becomes 2 _N_ and yields an unrealistically small confidence interval due to the large number
of constraints in fitting the observed cube. We used a method of scaling the standard Dc [2] by a factor of,(2 _N_ ) ( _68_ ).
The scaled loglikelihood by 1/,(2 _N_ ), or equivalently the scaled root mean square noise s rms by, 4 (2 _N_ ), was used in

the previous works ( _47_, _69_, _70_ ) with the Bayesian framework, giving the same effect by scaling Dc [2] . The modified
likelihood can be written as

_P_ (data|q) µ exp(-c(q) [2] /2) (S13)


25

_χ_ ( _θ_ ) [2] = Σ _Ni_ =0 [(



_I_ data, _i_ – _σI_ rmsmodel, _i_ ( _θ_ ) ) [2] /,(2 _N_ )] (S14)



For our data, we find that MCMC sampling of the posterior distribution converges using this procedure. The correction
by the inverse covariance matrix for the pixel to pixel correlations ( _71_ ) in the observed data cube is not taken into
account, because it is negligible compared to the effect by scaling the logarithmic likelihood.

Results of the gas dynamical modeling
We run the MCMC fitting with 180 walkers and 4000 steps. Because the first 600 steps are not converged to the
posterior distribution (a burn-in phase) by MCMC sampling, these first steps were excluded from the analysis. The
outcomes of MCMC sampling are shown in Fig S3, including the one-dimensional histogram of each physical
parameter and the covariance maps of the pairs of physical parameters. The best fitting values (median of the
marginalized distribution) and their associated 95% confidence intervals are summarized in Table S2. Our gas
dynamical modeling provides agreement between the observed cube and the model cube (compared in Fig. S1, A to
F). The model PVD is compared to the observed PVD in Fig. S1G, where both PVDs are extracted along the kinematic
major axis (Fig. 1B and Fig. S1, D to F). Figure. S1H shows the comparison between the observed velocity dispersion
and model velocity dispersion, measured at each position of PVD. The central increase of the observed velocity
dispersion is reproduced by the dynamical model under the assumption of the spatially uniform intrinsic velocity.
In Figure 1A and Figure S1A, we can see a spiral morphology in the [C II ] line intensity image, but we
assumed that the mass distribution of a disk is axisymmetric. This does not affect our mass measurement of the central
compact structure because the amplitude of the spiral component is only about 15% of the peak emission at maximum.
The two-armed spiral morphology is extended from the radius of 2 kpc to 5 kpc, far from the center. Therefore, the
contributions of these two arms to the gravitational potential are small in the center of the galaxy. The two arms are
located symmetrically with respect to the galaxy center, so these contributions cancel each other out.
We also consider the possibility that the radiation from active galactic nuclei (AGN) could influence the

[C II ] intensity distribution, which could bias our estimation of the disk scale radius and our dynamical modeling result.
Because the [C II ] profile is matched by an exponential profile which is typical to the disk, the influence of the AGN
is small. If AGN radiation influenced the [C II ] emission, the [C II ] emission would become more concentrated, our
size estimate of the disk would become smaller and the true disk scale radius would be larger than our estimate. We
investigated the dependence of _M_ bulge and _M_ disk on the disk scale radius _R_ d using several different values of _R_ d . To
compare with them, we also derived _M_ bulge and _M_ disk by adding the disk scale radius as a free parameter in our MCMC
fitting. This analysis confirmed that the derived masses of _M_ bulge is not sensitive to the disk scale radius (see Fig. S4).

CO ( _J_ =7→6) outflow
A possible bipolar outflow has been reported in CO ( _J_ =7→6) observations of this galaxy, reaching the velocity of 500
~ 600 km s [-1] ( _72_ ). Figure S5 shows the integrated spectrum of [C II ] line emission within a circular aperture with the
diameter of 2". We defined noise level in the spectrum (σ) by measuring the standard deviation of the line free channels
of the integrated spectrum (
-990 km s [-1] to -490 km s [-1] and 490 km s [-1] to 990 km s [-1] ), resulting in the 1σ noise level of 0.033 Jy beam [-1] . The
integrated spectrum is fitted with a single Gaussian (Fig. S5A). In the residual (Fig. S5B), redshifted 1.5σ to 2.5σ
emission can be seen over 3 channels (270 km s [-1] to 330 km s [-1] ). When these channels were imaged, a peak is seen on
the image. On the other hand, the other moderate emissions in the residual (1 to 2σ) are consistent with noise when
viewed on the image plane. Because the position of the redshifted emissions in the image plane coincides with the
redshifted part of the disk rotation, corresponding to the peak velocity of the PVD (Fig. 1E and Fig. S1G at about 0.1”
and 270 to 330 km s [-1] ), the redshifted emissions are likely to originate from a gas clump in the receding part of the
rotating disk in the center. We could not find any evidence of bipolar outflow in [C II ] line emission, but this does not
exclude the bipolar outflow seen in CO ( _J_ =7→6) line emission because the [C II ] line may not be strongly emitted
from the outflowing material. For example, outflow is seen in OH line absorption but not in [C II ] line emission in
some other high redshift galaxies at _z_ ~ 4 ( _73_ ). Therefore, we did not consider the outflow kinematics in the gas
dynamical modeling.

Toomre _Q_ parameter
The dynamical stability of the disk is quantified using the Toomre _Q_ parameter. For a gas disk, the parameter is given
by ( _74_, _75_ )


26

_Q_ =



π _GΣ_ - !gas _κ_ (S15),



where 𝜅 is the epicyclic frequency, _Σ_ gas is the surface density of the gas, and 𝜎, is intrinsic velocity dispersion of the



gas. 𝜅 is given by 2
/ ~~$~~



_v_ 2rot



d _v_ rot

d _r_ ~~[%]~~ [ (] _[57]_ [). When ] _[Q]_ [ < 1, the disk is unstable against the perturbations because the self-]



_r_ [2] [+]



_v_ rot


_r_



gravity of the gas overwhelms the local pressure forces due to the turbulent motion and the differential rotation ( _74_,
_75_ ). Because the total gas mass is traced by the [C II ] line ( _63_, _64_ ), we estimated the surface density of the gas _Σ_ gas by
using the total molecular gas mass ( _M_ gas = 5 ´ 10 [10] 𝑀 ⨀ ) ( _16_ ) and the [C II ] line distribution we observed. The rotation
velocity was derived from our gas dynamical modeling. Using these parameters, we derived Toomre _Q_ parameter for
each spatial pixel (Fig. S6, A and B). The error bars in Fig. S6B reflect the uncertainty of the model rotation velocity
at 95% confidence interval.


27

**D** **E** **F**


Data Velocity Major axis Model Velocity





**G**



**H**



**Fig. S1. Morphology and kinematics of [C** **II** **] line in BRI 1335-0417 and their comparisons with gas dynamical**
**models.** (A) and (D) are the respective ALMA [C II ] line maps of intensity (moment 0), intensity-weighted velocity
(moment 1), same as Figs. 1A and B respectively. (B) and (E) are the dynamical model maps with the central compact
mass and disk taken into consideration, which are corresponding to (A) and (D). (C) and (F) are the residual maps
between the observed [C II ] line maps of (A) and (D) and the dynamical model maps of (B) and (E), respectively. The
masked moment method ( _39_ ) was used to produce map (D). The same mask was applied to (E) for a fair comparison.
Plotting symbols in (A-F) are the same as Figs. 1A and B. (G) shows the observed PVD of [C II ] line emission (color,
same as Fig. 1E) and model PVD (white contours: every 4s rms from 3s rms to 23s rms, where s rms is the root mean square
noise of 0.35 mJy beam [-1] ). The model PVD was extracted along the kinematic major axis [see black solid line in (E)].
(H) shows velocity dispersion, which were measured by fitting a Gaussian with third and fourth order Gauss-Hermite
parameters _h_ 3 and _h_ 4 ( _76_ ) to the line profile at each position of PVD (black points and error bars, same as Fig. 1F).
This fitting used the pixels where [C II ] line emission has signal to noise ratio SNR > 4 in at least 4 velocity channels.
(H) also shows velocity dispersion extracted from the model PVD in the same way (gray shade, showing 95%
confidence intervals). The red dashed line is same as Fig. 1F.


28

**Fig. S2 Synthesized beam of the ALMA observation.** The synthesized beam (i.e. point spread function) is shown.
The side lobes of the synthesized beam are < 13%. The influence of this side lobe was removed from the images by
the deconvolution process with a task of tclean in C ASA .


29

**Fig. S3. Posterior probability distributions of the eight model parameters using MCMC sampling of our gas**
**dynamical model.** The posterior probability distributions for the respective parameters were marginalized, and then
the results are shown as the respective histograms along the diagonal panels. The dashed vertical lines in these
histograms are the 2.5 [th], 50 [th], and 97.5 [th] percentiles (95% confidence interval). The derived values of eight model
parameters are indicated above the histogram, summarized in Table S2. The other panels show the covariances
between all model parameters (contour levels are equivalent to 68%, 95% and 99.7% confidence intervals for the 2D
Gaussian distribution).


30

**Fig. S4. The dependency of derived physical parameters on the disk radius.** Best fitting values of _M_ bulge and _M_ disk
were derived using several values of the disk scale radius, shown normalized by our estimated value of _R_ d =1.83 kpc
(see Table S1). The disk scale radius was added as a free parameter in the MCMC fitting with the uniform prior range
shown in brackets. The derived _M_ bulge is not sensitive to the disk scale radius.


31

|Col1|A|
|---|---|
|||
|||
|||
|||
|||
|||
||**B**|
|||


**Fig. S5. Integrated spectrum of the [C** **II** **] line emission of BRI 1335-0417.** (A) is the [C II ] spectrum (black solid
line) extracted using circular aperture with the diameter of 2", which roughly corresponds to the region shown in Fig.
S1, A to F. The velocity is relative to the frequency of 351.470 GHz in barycentric frame. A Gaussian model fitted to
the spectrum is shown in blue solid line. (B) shows the residual (data – Gaussian model, black solid line). The noise
level in the spectrum was estimated by measuring the standard deviation of the line free channels of the integrated
spectrum (-990 km s [-1] to -490 km s [-1] and 490 km s [-1] to 990 km s [-1] ), resulting in the 1σ noise level of 0.033 Jy beam [-1] .
In (A) and (B), the 3σ and 1σ noise levels are indicated by the black dotted line and gray shaded region respectively.
The black solid line indicates the zero flux level.


32

## **A B**

**Fig. S6. The Toomre parameter** _**Q**_ **for the gas disk of BRI 1335-417.** Spatial distribution of Toomre parameter _Q_
for the gas disk is shown in (A). The Q was derived using rotation velocity, intrinsic velocity dispersion and the surface
density of the gas. The radial distribution of _Q_ is shown in (B), where each pixel in (A) is plotted in radial distance
deprojected to a disk plane. Over the outer part of the disk (at the radius of _R_ - 0.2"), _Q_ is < 1, implying that the gas
disk is unstable against the perturbations. The error bars reflect the uncertainty of the 95% confidence interval of the
dynamical model. This measurement only used pixels where the [C II ] line emission is detected at SNR > 4 in at least
4 velocity channels.


33

**Table S1.**
**Physical parameter derived by P** **A** **F** **IT** **Package and G** **ALFIT** **.** The position angle of the disk was estimated from the

[C II ] line kinematics using the P A F IT package. The inclination of the disk _i_ was estimated from the axis ratio measured
by fitting Sérsic profile to the dust continuum image using the G ALFIT code. The reduced chi square _χ_ & _υ_ of the fitting



by fitting Sérsic profile to the dust continuum image using the G ALFIT code. The reduced chi square _χ_ & _υ_ of the fitting

is 1.592, where the degree of freedom is 4090. Disk scale radius _R_ d was estimated by fitting exponential profile to the

[C II ] line image using the G ALFIT code. The reduced chi square _χ_ & _υ_ is 0.956, where the degree of freedom is 4091.



& is 0.956, where the degree of freedom is 4091.



Disk position angle G (°) 4.5 ± 3.7


Disk inclination _i_ (°) 37.8 +2.4-3.3


Disk scale radius _R_ d (kpc) 1.83 ± 0.04


34

**Table S2.**
**Best fit summary of our gas dynamical model.** Column 1 shows the parameters and their units in our dynamical
model. Column 2 shows the symbol used for each parameter. Column 3 shows the prior distributions used in our
MCMC sampling, in which the values in brackets indicate the upper and the lower boundary of the uniform prior
distribution, while the values in parentheses indicate the mean and standard deviation of the Gaussian prior. Columns
4 and 5 show the medians of posterior distribution, their associated 95% confidence intervals respectively. The upper
limit on the effective radius _R_ e of the central compact mass, is reported in parentheses. The reduced chi square _χ_ & _υ_ in

our MCMC fitting is 1.69 under the degree of freedom of 42400.


**95% confidence**
**Parameters (unit)** **Symbols** **Priors** **Medians**

**Interval**


Galactic Mass model:


Central compact mass (10 [.] 𝑀 ⨀ ) _M_ bulge [10 [-9], 10 [4] ] 8.9 -3.7, +20.9


Disk mass (10 [/0] 𝑀 ⨀ ) _M_ disk [10 [-10], 10 [3] ] 4.9 -2.5, +1.7


Central compact mass effective [0.001,
_R_ e                - (<1.33)
radius (kiloparsec) 1.625]


Orientation of [C II ] gas disk:


Position angle (degree) G [-20, 20] 7.6 -7.1, +7.3


Inclination angle (degree) _i_ (37.8, ±1.6) 37.3 -3.1, +3.0


Nuisance parameters:


[C II ] center velocity offset (km s [-1] ) D _v_ [-60, 60] 23.6 ±8.5


[C II ] center RA offset (arcsecond) D _x_ [-0.15, 0.15] - 0.00 ±0.03


[C II ] center Dec offset (arcsecond) D _y_ [-0.15, 0.15] 0.05 ±0.02


35

**Captions for Data**
**S1 Observed [C** **II** **] data cube cutout used for dynamical modeling. File in Flexible Image Transport System**
**(FITS) format.**
**S2 Model [C** **II** **] data cube from K** **IN** **MS. File in FITS format.**
**S3 Observed full [C** **II** **] data cube used for displaying a spectrum. File in FITS format.**
**S4 Observed dust continuum image. File in FITS format.**


36


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "Molecular gas mass M_gas = 5.1 x 10^10 M_sun (or 5 x 10^10 M_sun) from CO (J=2->1)",
  "failed_quote": "The modeled mass of the disk 4.9 -2.5 × 10 _M_ ⨀ is consistent with the molecular gas mass of 5.1 × 10 _M_ ⨀ ( _16_ ) estimated from the CO ( _J_ =2→1) luminosity"
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "Method for extracting intrinsic velocity dispersion from outer disk region",
  "failed_quote": "We estimate an intrinsic velocity dispersion 𝜎 𝑣 of 71 -11 km s (Fig. 1F) using a method ( _21_ ) that extracts the velocity dispersions at the outer region of the disk, where the beam smearing is less severe."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Peak finding in Fourier spectrum A(p, m); uncertainties from PA and inclination uncertainties",
  "failed_quote": "The strongest peak is seen in _m_ = 2 at _p_ = - 4.0 +0.6-0.3, corresponding to spiral arms with a pitch angle of _α_ = 26.7 -1.6 ° at the 95% confidence level. The confidence interval was estimated from the uncertainties of the position angle and inclination of the disk."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Generate gas particles from CLEAN components using SkySampler, build 3D dynamical model cubes in KinMS with a spherical de Vaucouleurs bulge + thick pressure-supported exponential disk gravitational potential, and fit directly to the observed cube via MCMC using emcee.",
  "failed_quote": "The S KYSAMPLER code ( _47_ ) was used to generate gas particles that reproduce the [C II ] line intensity profile of BRI 1335-0417 by using the de-convolved CLEAN components that were provided by a task of tclean in C ASA ."
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "Generating gas particles from deconvolved CLEAN components to approximate the [C II] intensity profile for KinMS",
  "failed_quote": "The S KYSAMPLER code ( _47_ ) was used to generate gas particles that reproduce the [C II ] line intensity profile of BRI 1335-0417 by using the de-convolved CLEAN components that were provided by a task of tclean in C ASA ."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Rotational-to-dispersion ratio (v_rot / sigma_v) = 2.5 dimensionless",
  "failed_quote": "Our estimated ratio _v_ rot /𝜎 𝑣 of 2.5 -0.4 indicates that the [C II ] gas disk of this galaxy is rotation-dominated."
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Spiral pitch angle (m = 2 mode) = 26.7 degree",
  "failed_quote": "The best-fitting model is a two-armed spiral morphology with a pitch angle of 26.7 -1.6 ° (95% confidence level)."
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Fourier parameter p for m = 2 mode = -4.0 dimensionless",
  "failed_quote": "The strongest peak is seen in _m_ = 2 at _p_ = - 4.0 +0.6-0.3, corresponding to spiral arms with a pitch angle of _α_ = 26.7 -1.6 ° at the 95% confidence level."
 },
 {
  "path": "results_numeric[13].evidence[1]",
  "value": "Disk mass (M_disk) = 4.9 10^10 M_sun",
  "failed_quote": "The modeled mass of the disk 4.9 -2.5 × 10 _M_ ⨀ is consistent with the molecular gas mass of 5.1 × 10 _M_ ⨀"
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "Spiral arms (or tidal features), a rotating disk, and a central compact structure had already formed within 1.4 billion years after the Big Bang.",
  "failed_quote": "The best-fitting model is a two-armed spiral morphology with a pitch angle of 26.7 -1.6 ° (95% confidence level)."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The gas disk is rotation-dominated and gravitationally unstable in the outer parts, making it susceptible to star formation and spontaneous spiral structure formation.",
  "failed_quote": "Our estimated ratio _v_ rot /𝜎 𝑣 of 2.5 -0.4 indicates that the [C II ] gas disk of this galaxy is rotation-dominated."
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "The kinematics require a central compact mass compatible with local stellar bulges or the previously estimated ~6 x 10^9 M_sun black hole, alongside a gas disk whose dynamical mass matches the CO-derived molecular gas mass.",
  "failed_quote": "The modeled mass of the disk 4.9 -2.5 × 10 _M_ ⨀ is consistent with the molecular gas mass of 5.1 × 10 _M_ ⨀ ( _16_ ) estimated from the CO ( _J_ =2→1) luminosity"
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Previous [C II] observations had insufficient spatial resolution to determine the gas distribution and kinematics, whereas the archival Band 7 C43-5 data resolve the galaxy at ~1.3 kpc.",
  "failed_quote": "[C II ] line emission from this object was detected in previous observations at lower spatial resolution, insufficient to determine the gas distribution and kinematics ( _15_ )."
 }
]
```
