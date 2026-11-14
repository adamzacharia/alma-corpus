# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018ApJ...868...75S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version October 4, 2018
Typeset using L [A] TEX **twocolumn** style in AASTeX61


CONCURRENT STARBURSTS IN MOLECULAR GAS DISKS WITHIN A PAIR OF COLLIDING GALAXIES

AT _z_ = 1 _._ 52


J. D. Silverman, [1] E. Daddi, [2] W. Rujopakarn, [3, 4, 5] A. Renzini, [6] C. Mancini, [7, 6] F. Bournaud, [2] A. Puglisi, [2, 6]

G. Rodighiero, [7] D. Liu, [2] M. Sargent, [8] N. Arimoto, [9, 10] M. B´ethermin, [11] J. Fensch, [12] C. C. Hayward, [13]

J. Kartaltepe, [14] D. Kashino, [15] A. Koekemoer, [16] G. Magdis, [17] H.J. McCracken, [18] T. Nagao, [19] K. Sheth, [20]

V. Smolˇci´c, [21] and F. Valentino [22]


1 _Kavli_ _Institute_ _for_ _the_ _Physics_ _and_ _Mathematics_ _of_ _the_ _Universe,_ _The_ _University_ _of_ _Tokyo,_ _Kashiwa,_ _Japan_ _277-8583_ _(Kavli_ _IPMU,_ _WPI)_

2 _Laboratoire_ _AIM,_ _CEA/DSM-CNRS-Universite_ _Paris_ _Diderot,_ _Irfu/Service_ _d’Astrophysique,_ _CEA_ _Saclay_

3 _Department_ _of_ _Physics,_ _Faculty_ _of_ _Science,_ _Chulalongkorn_ _University,_ _254_ _Phayathai_ _Road,_ _Pathumwan,_ _Bangkok_ _10330,_ _Thailand_

4 _National_ _Astronomical_ _Research_ _Institute_ _of_ _Thailand_ _(Public_ _Organization),_ _Don_ _Kaeo,_ _Mae_ _Rim,_ _Chiang_ _Mai_ _50180,_ _Thailand_

5 _Kavli_ _Institute_ _for_ _the_ _Physics_ _and_ _Mathematics_ _of_ _the_ _Universe,_ _Todai_ _Institutes_ _for_ _Advanced_ _Study,_ _the_ _University_ _of_ _Tokyo,_ _Kashiwa,_

_Japan_ _277-8583_ _(Kavli_ _IPMU,_ _WPI)_

6 _Instituto_ _Nazionale_ _de_ _Astrofisica,_ _Osservatorio_ _Astronomico_ _di_ _Padova,_ _v.co_ _dell’Osservatorio_ _5,_ _I-35122,_ _Padova,_ _Italy,_ _EU_

7 _Dipartimento_ _di_ _Fisica_ _e_ _Astronomia,_ _Universita_ _di_ _Padova,_ _vicolo_ _Osservatorio,_ _3,_ _35122,_ _Padova,_ _Italy_

8 _Astronomy_ _Centre,_ _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Sussex,_ _Brighton,_ _BN1_ _9QH,_ _UK_

9 _Astronomy_ _Program,_ _Department_ _of_ _Physics_ _and_ _Astronomy,_ _Seoul_ _National_ _University,_ _599_ _Gwanak-ro,_ _Gwanak-gu,_ _Seoul,_ _151-742,_

_Korea_


10 _Subaru_ _Telescope,_ _650_ _North_ _A’ohoku_ _Place,_ _Hilo,_ _Hawaii,_ _96720,_ _USA_

11 _European_ _Southern_ _Observatory,_ _Karl-Schwarzschild-Str._ _2,_ _85748_ _Garching,_ _Germany_

12 _European_ _Southern_ _Observatory,_ _Karl-Schwarzschild-Str._ _2,_ _85748,_ _Garching_ _bei_ _M¨unchen,_ _Germany_

13 _Center_ _for_ _Computational_ _Astrophysics,_ _Flatiron_ _Institute,_ _162_ _Fifth_ _Avenue,_ _New_ _York,_ _NY_ _10010,_ _USA_

14 _School_ _of_ _Physics_ _and_ _Astronomy,_ _Rochester_ _Institute_ _of_ _Technology,_ _84_ _Lomb_ _Memorial_ _Drive,_ _Rochester,_ _NY_ _14623,_ _USA_

15 _Institute_ _of_ _Astronomy,_ _ETH_ _Z¨urich,_ _Wolfgang-Pauli-Strasse_ _27,_ _CH-8093,_ _Z¨urich,_ _Switzerland_

16 _Space_ _Telescope_ _Science_ _Institute,_ _3700_ _San_ _Martin_ _Drive,_ _Baltimore,_ _MD,_ _21218,_ _USA_

17 _Cosmic_ _DAWN_ _Centre,_ _Niels_ _Bohr_ _Institute,_ _University_ _of_ _Copenhagen,_ _Juliane_ _Mariesvej_ _30,_ _2100,_ _Copenhagen,_ _Denmark_

18 _Institut_ _d’Astrophysique_ _de_ _Paris,_ _CNRS,_ _UMR_ _7095_ _and_ _UPMC,_ _98bis_ _boulevard_ _Arago,_ _F-75014_ _Paris,_ _France_

19 _Graduate_ _School_ _of_ _Science_ _and_ _Engineering,_ _Ehime_ _University,_ _2-5_ _Bunkyo-cho,_ _Matsuyama_ _790-8577,_ _Japan_

20 _NASA_ _Headquaters,_ _300_ _E._ _St_ _SW,_ _Washington_ _DC_ _20546,_ _USA_

21 _University_ _of_ _Zagreb,_ _Physics_ _Department,_ _Bijeniˇcka_ _cesta_ _32,_ _10002,_ _Zagreb,_ _Croatia_

22 _Dark_ _Cosmology_ _Centre,_ _Niels_ _Bohr_ _Institute,_ _University_ _of_ _Copenhagen,_ _Juliane_ _Maries_ _Vej_ _30,_ _DK-2100_ _Copenhagen,_ _Denmark_


(Accepted ApJ; October 1, 2018)


ABSTRACT


We report on the discovery of a merger-driven starburst at _z_ = 1 _._ 52, PACS-787, based on high signal-to-noise
ALMA observations. CO(5-4) and continuum emission (850 _µ_ m) at a spatial resolution of 0.3 _[′′]_ reveal two compact
( _r_ 1 _/_ 2 _∼_ 1 kpc) and interacting molecular gas disks at a separation of 8.6 kpc thus indicative of an early stage in a
merger. With a SFR of 991 M _⊙_ yr _[−]_ [1], this starburst event should occur closer to final coalescence, as usually seen in
hydrodynamical simulations. From the CO size, inclination, and velocity profile for both disks, the dynamical mass is
calculated through a novel method that incorporates a calibration using simulations of galaxy mergers. Based on the
dynamical mass, we measure (1) the molecular gas mass, independent from the CO luminosity, (2) the ratio of the
total gas mass and the CO(1 - 0) luminosity ( _α_ _CO_ _≡_ _M_ _gas_ _/L_ _[′]_ _CO_ 1 _−_ 0 [),] [and] [(3)] [the] [gas-to-dust] [ratio,] [with] [the] [latter]
two being lower than typically assumed. We find that the high star formation, triggered in both galaxies, is caused
by a set of optimal conditions: a high gas mass/fraction, a short depletion time ( _τ_ _depl_ = 85 and 67 Myrs) to convert


[john.silverman@ipmu.jp](mailto: john.silverman@ipmu.jp)

2 Silverman et al.


gas into stars, and the interaction of likely counter-rotating molecular disks that may accelerate the loss of angular
momentum. The state of interaction is further established by the detection of diffuse CO and continuum emission,
tidal debris that bridges the two nuclei and is associated with stellar emission seen by HST/WFC3. This observation
demonstrates the power of ALMA to study the dynamics of galaxy mergers at high redshift.


_Keywords:_ galaxies: ISM — galaxies: high-redshift — galaxies: starburst — galaxies: star formation

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 3



1. INTRODUCTION


Our understanding of the physical properties of the interstellar medium, in galaxies undergoing a merger that
can induce star formation and accretion onto supermassive black holes, is usually based on studies in the local Universe. Representative examples include Arp 220,
the Antennae, and NGC 6240 that belong to a class
of Ultraluminous Infrared Galaxies (ULIRGs; Sanders
& Mirabel 1996) that are unequivocally undergoing an
extreme starburst (with a luminous Active Galactic Nucleus - AGN - in many cases), triggered by a merger
of two massive galaxies (e.g., Di Matteo et al. 2005;
Hopkins et al. 2006; Volonteri et al. 2015). While such
collisions accelerate the growth of galaxies (e.g., Scudder et al. 2012; Ellison et al. 2013), this mechanism appears to have a subdominant effect on the buildup of
the global stellar mass and black hole mass density over
a wide range of cosmic time (Rodighiero et al. 2011).
Although, mergers likely represent a key phase (having
a short duty cycle) through which every massive galaxy
may pass (e.g., Lotz et al. 2008; Lackner et al. 2014).
Moreover, galaxy mergers offer us a specialized laboratory to study the physics of the interstellar medium
including the conversion of molecular gas into stars and
the channeling of such gas to the central regions that
can build up the central stellar bulge.
From seminal studies, local starbursts are characterized as having relatively large amounts of molecular gas
(Sanders et al. 1986; Scoville et al. 1989), hence higher
gas fractions relative to the normal galaxy population
at _z_ _∼_ 0. The majority of the molecular gas is centrally concentrated within a radius of _∼_ 1 kpc (Downes
& Solomon 1998; Wilson et al. 2008), possibly the result of a nuclear inflow induced by the merger. This
has been demonstrated to be a common phenomenon
through hydrodynamic simulations (e.g., Hopkins et al.
2013; Fensch et al. 2017) of the merger of two gas-rich
disk galaxies. Furthermore, starbursts are observed to
have a lower gas content than expected given their high
star formation rates (SFRs) that has been described as
a higher efficiency ( _SFE_ _≡_ _SFR/M_ _gas_ ) to form stars
(Solomon et al. 1997; Saintonge et al. 2012), even seen to
be present at higher redshift (Daddi et al. 2010b; Genzel
et al. 2010; Combes et al. 2013; Tacconi et al. 2018).
Numerous millimeter interferometric studies have presented observations of the molecular gas and dust content of starburst galaxies at high redshift ( _z_ _>_ 1),
usually bright submillimeter galaxies (e.g., Greve et al.
2005; Tacconi et al. 2006, 2008; Engel et al. 2010; Bothwell et al. 2013). For select starbursts, lensing has
enhanced the ability to resolve the emission on subarcsecond scales (e.g., Swinbank et al. 2010; Spilker



et al. 2015). In general, submillimeter galaxies share
many properties with local ULIRGs such as having large
amounts of molecular gas, clear signs of mergers in many
cases (and ordered disk rotation), short gas depletion
times, and characteristic sizes less than a few kiloparsecs
with the central regions being baryon dominated. These
galaxies have been proposed to be the progenitors of local elliptical galaxies (Kormendy & Sanders 1992; Ivison
et al. 1998; Lilly et al. 1999; Genzel et al. 2001) with an
intermediate stage as a compact quiescent galaxy (Toft
et al. 2014). Although, a non-negligible level of contamination from unassociated galaxies is present (Hayward
et al. 2013) due to the large beam size of submillimeterselected sources that is now being mitigated with Atacama Large Millimeter/submillimeter Array (ALMA).
With ALMA, many efforts are extending the aforementioned studies of the molecular gas and dust emission in galaxy mergers and starbursts at _z_ _>_ 1, particularly below the kiloparsec scale due to the large
collecting area and long baselines (e.g., Chen et al.
2017; Barro et al. 2017; Riechers et al. 2017). For
example, Hodge et al. (2016) has measured the effective radius of submillimeter galaxies ( _z_ _∼_ 2 _._ 5), based
on the size of the dust emission at 870 _µ_ m, to be between 1 - 3 kpc and have a disk-like morphology, in contrast to star formation being more extended on galaxywide scales for typical star-forming main sequence (MS
hereafter) galaxies at _z_ _∼_ 2 (Rujopakarn et al. 2016).
While there are signs of ongoing mergers in HST images of these SMGs, the dust emission is slightly more
extended than local ULIRGs while having similar L IR
(10 [12] _[−]_ [13] L _⊙_ ). These results corroborate evidence for
central _∼_ kpc dust-emitting (i.e., star-forming) regions
in high-z SMGs (Simpson et al. 2015) that may indicate a phase where massive galaxies are rapidly forming
their bulges given their high star formation rate surface
density (Σ _SF R_ _∼_ 100 M _⊙_ yr _[−]_ [1] kpc _[−]_ [2] ). However, these
issues are still under debate and will benefit from larger
samples, observed at higher resolution with ALMA, including cases (e.g., PACS-787) with more extreme rates
of star formation as presented here.
Complementary to these studies, we are carrying out
a program with ALMA over multiple cycles to measure
the molecular gas properties, primarily using carbon
monoxide (CO; 2 - 1), of twelve starburst galaxies in the
COSMOS field having star formation rates well-above
(≳ 4 _×_ ) the star-forming MS at _z_ _∼_ 1 _._ 6 (see Silverman
et al. 2015a, 2018). This sample has advantages over
other heterogeneous high-z starburst samples by having a wealth of information including accurate spectroscopic redshifts, metallicities from [NII]/H _α_ (Puglisi et
al. 2017), and stellar masses and SFRs based on mid

4 Silverman et al.



28.10s 28.00s 27.90s 10h02m27.80s


RA (J2000)



28.10s 28.00s 27.90s 10h02m27.80s


RA (J2000)



07.0"


06.0"


05.0"


04.0"


03.0"


+2°10'02.0"



28.10s 28.00s 27.90s 10h02m27.80s


RA (J2000)



28.05s 28.00s 27.95s 27.90s 10h02m27.85s


RA (J2000)



06.0"


05.5"


05.0"


04.5"


04.0"


03.5"


+2°10'03.0"



28.05s 28.00s 27.95s 27.90s 10h02m27.85s


RA (J2000)



**Figure** **1.** Optical-to-infrared imaging of PACS-787. _Top_ _row_ ( _ground −_ _based_ ) : The two left panels show the Subaru/HSC
optical images while the UltraVISTA (McCracken et al. 2012) near-infrared image is on the right. The two galaxies are visible
in each frame. A small red cross indicates the centroid of each component based on the CO(5 - 4) emission that is co-spatial
with the IR but offset with the locations in the bluer images, as typically seen for high-z starbursts (Silverman et al. 2015a) and
more typical high-z galaxies (Cibinel et al. 2017). _Bottom_ _row_ ( _space −_ _based_ ) : HST imaging in the ACS F814W and WFC3
F140W filters with a linear and log scale respectively. The green circle indicates the location of the fiber used to acquire a NIR
spectrum with Subaru/FMOS.



and far-IR observations with _Spitzer_ (Sanders et al.
2007) and _Herschel_ (Lutz et al. 2011), placing them
securely in the starburst class (Rodighiero et al. 2011).
Compared to classical submillimeter galaxies (SMG),
this selection avoids contamination by objects close to
the MS (Magnelli et al. 2012), reduces SED bias compared to SMGs selection (which prefers cold objects),
and is able to pick objects even with relatively moderate
SFR, but much higher above the MS. Based on this sample, we demonstrate that the star formation efficiency
(or gas depletion timescale) increases (decrease) continuously with elevation in SFR above the star-forming MS
(Silverman et al. 2015a, 2018).
Here, we present a study at higher spatial resolution
of the CO(5-4) molecular gas and continuum emission
(rest-frame 500 _µ_ m) of our strongest starburst (PACS787; _z_ _spec_ = 1 _._ 5234; SFR = 991 [+96] _−_ 87 [M] _[⊙]_ [yr] _[−]_ [1] [,] [6.5] _[×]_
greater than the average star-forming galaxy for its stellar mass) from the sample described above, using ALMA
in Cycle 4 (Silverman et al. 2018). With 0 _._ 3 _[′′]_ resolution
in Band 6, we cleanly separate the emission from two
separate galaxies in a major merger. With the resulting maps (CO and continuum) having a high signal


to-noise, we assess the physical characteristics of each
galaxy through a determination of _α_ _CO_ (and the gasto-dust ratio) based on a dynamical mass estimate of
PACS-787. As a novelty, we apply a scale factor to
calculate the dynamical mass based on hydrodynamical simulations of galaxy mergers with similar properties to PACS-787. Subsequently, we determine gas mass
(M _gas_ ), SFR, and star formation efficiency (M _gas_ /SFR)
of each galaxy. To conclude, we argue that PACS-787 is
a classic example of a merger-induced starburst with a
number of contributing factors to its SFR including an
orbital configuration conducive for forming stars at such
a high rate. Throughout this work, we assume an established cosmology ( _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1], Ω Λ = 0 _._ 7,
Ω M = 0 _._ 3), and use a Chabrier IMF for SFRs and stellar

masses.


2. PACS-787: AN EXTREME OUTLIER FROM

THE SF MS


PACS-787 is a starburst galaxy with a high SFR as
compared to the typical star-forming population at fixed
redshift and stellar mass (with details on the determination of these measurements to follow). The galaxy was

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 5



first identified as having strong far-infrared emission, as
detected by _Herschel_ /PACS (Rodighiero et al. 2011),
and a photometric redshift within a targeted redshift
range of 1 _._ 43 _< z_ _<_ 1 _._ 74 to detect the H _α_ emission line
as part of our large near-infrared spectroscopic survey
of star-forming galaxies, FMOS-COSMOS (Silverman et
al. 2015b). Therefore, the object was given priority for
spectroscopic follow up that resulted in a positive detection of both H _α_ and [NII] _λ_ 6584 at z=1.5234 (Appendix A) thus confirming its nature as having a very
high SFR, atypical of star-forming MS galaxies.
In Figure 1, we show image cutouts of PACS-787
in the optical and near-infrared from both the ground
and space that indicate the presence of two galaxies in
close proximity. While the eastern (left-most) component is faint in the optical, it is clearly detected by
Subaru/Hyper Suprime-Cam (HSC) and UltraVISTA
(K _AB_ =22.39 and 20.47 for the East and West galaxies respectively). High spatial resolution HST imaging
with ACS/F814W (Koekemoer et al. 2007; Scoville et
al. 2007) and WFC3/F140W (single-orbit; 40 minute
exposure on-source), with the latter provided through
an unrelated Cycle 25 program (PI J. Silverman; Program #15115), aids in our characterization of the system as an ongoing merger. For instance, the two galaxies are undergoing a strong interaction as indicated by
the presence of tidal features and a stellar bridge between the two nuclei seen in the WFC3 image. The
HST/ACS mosaics and the WFC3 image (Koekemoer
2018, priv. comm) have been reprocessed where the
astrometry is directly tied to the International Celestial Reference Frame (ICRF), thereby eliminating uncertainties from possible offsets in older catalogs previously
used to align HST images. For ACS, this correction resulted in a 5 pixel (0 _._ 15 _[′′]_ ) shift. The new astrometric
solution for both images shows near perfect alignment
between the bright UV and IR emission of the western
galaxy with the ALMA centroid of the CO(5-4) emission as shown in the bottom panels of Figure 1 by the
red crosses. Here, we provide details on the use of the
multi-wavelength photometry available from the COSMOS survey to accurately measure the stellar mass and
SFR, both key quantities required in the analysis of the
ALMA observations, of the individual galaxies.


2.1. _Stellar_ _mass_ _(M_ _stellar_ _)_


The mass, in stars, that have already formed is a
key measurement for insight into the growth history of
galaxies and the current mode of star formation such as
being in a starburst phase, as is the case for PACS-787.
Multiple broad-band images of the COSMOS field, covering the ultraviolet to the infrared, are used to mea


**Figure** **2.** Best-fit stellar population model to opticalinfrared photometry for the eastern (fainter) and western
(brighter) galaxies separately with the respective best-fit
stellar masses and extinction A _V_ as labeled.


sure the stellar mass as done in Laigle et al. (2016).
Since the galaxies are slightly blended, we use GALFIT (Peng et al. 2010) to measure fluxes in seven optical bands (g, r, i, z; Subaru/HSC; Tanaka et al. 2017
and near-infrared (Y, H, Ks; UltraVISTA; McCracken
et al. 2012), for each component separately. To measure
the stellar mass, we fit the photometry using models
(Bruzual & Charlot 2003) that include a mixture of different stellar populations. The code Hyperzmass (i.e.,
a modified version of Hyperz, Bolzonella et al. 2000) is
used to perform the fit while implementing a constant
star formation history (SFH). The stellar mass estimate
accounts for stellar mass loss as described in Pozzetti et
al. (2007). We highlight that degeneracies between parameters such as stellar age, metallicity, and extinction
affect the stellar mass estimates and are accounted for
in the 68% confidence interval based on the _χ_ [2] statistic.
In Figure 2, we show the best-fit model to the spectralenergy distribution for the separate components of
PACS-787. We note that the assumption of a constant SFH will result in lower stellar masses than if as
suming an exponentially declining model with a recent
burst. However, the sum of the two best-fit SEDs gives
mid-IR fluxes which are within 10% of the measured
_Spitzer_ /IRAC fluxes, indicating that the two galaxies
do not contain additional mass that is unaccounted for

by the photometry used for the SED fit. Continuum
emission from the type 2 AGN (Appendix A) in the
western galaxy is negligible thus does not impact the
stellar mass measurements. The stellar masses of each,
with uncertainties based on photometric errors, are reported in Table 2 and shown in Figure 2 assuming a
Chabrier IMF. The galaxies have a stellar mass ratio of

6 Silverman et al.



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [1]


10 [2]


10 [3]


10 [4]


10 [5]


10 [6]







The dust model is expressed by Equation 2 of Magdis
et al. (2012a) with seven free parameters (Ω _∗_, _q_ _P AH_,
_U_ _min_, _U_ _max_, _α_, _γ_, _M_ _dust_ ). The stellar component is approximated by a blackbody ( _T_ _∗_ = 5000 K) with Ω _∗_ being
the solid angle subtended by the stellar photospheres.
The fraction of the dust in PAH grains is expressed as
_q_ _P AH_ . The radiation field is given as _U_ _min_ that illuminates most of the diffuse dust while a smaller fraction
( _γ_ ) is exposed to a higher radiation field up to a value of
10 [6] for _U_ _max_ . An index _α_, fixed at a value of 2, describes
the distribution of the starlight intensity incident on the
dust (d _M_ _dust_ /d _U_ _∝_ _U_ _[−][α]_ ). The best-fit model is found
through a _χ_ [2] minimisation with a goodness-of-fit given
by the reduced _χ_ [2] . From this method, we find a total
dust mass of _log_ _M_ _dust_ = 9 _._ 2 _±_ 0 _._ 06 M _⊙_ based on the fit
shown in Figure 3. Monte Carlo simulations are used to
assess the error on _M_ _dust_ .
From an integral of the best-fit dust model, the total
FIR luminosity is _log L_ = 12 _._ 83 _±_ 0 _._ 04 (units of _L_ _⊙_ ) that
corresponds to a total SFR = 991 _−_ [+96] 87 [M] _[⊙]_ [yr] _[−]_ [1] [, using the]
calibration given in Kennicutt & Evans (2012), which
includes the contribution from both galaxies. This rate
is in good agreement with that derived from the radio
emission (3 and 5 GHz) (Schinnerer et al. 2007; Smolˇci´c
et al. 2017) where the normalization of the power-law
model, shown in Figure 3, is set by the IR-radio correlation with a parameterization from Ivison et al. (2010).


2.3. _Location_ _relative_ _to_ _the_ _star-forming_ _MS_


In Figure 4, we display the location of PACS-787
with respect to the star-forming galaxy population at
1 _._ 4 _<_ _z_ _<_ 1 _._ 7 that delineates the known star-forming
MS (e.g., Speagle et al. 2014; Renzini & Peng 2015). For
this comparison, we measure the stellar masses consistently between both samples to determine, as accurately
as possible, the boost in SFR for PACS-787, at a given
mass, that is used subsequently in our analysis. Starforming galaxies are selected from the COSMOS photometric catalog (Laigle et al. 2016) with 1 _._ 4 _<_ _z_ _<_ 1 _._ 7.
Stellar masses for this reference sample are remeasured,
as described in Puglisi et al. (2017), using the same code,
and assumptions on the equivalent measurements for
PACS-787. The only difference is that for PACS-787
we use the latest Subaru/HSC data. For the comparison sample, SFRs are based on the best-fit stellar population synthesis model. Reassuringly, the locus of the
MS agrees very well with published relations as given in
Daddi et al. (2007) and Kashino et al. (2013). For the
_Herschel_ -detected galaxies (shown in red), the SFRs
are computed based on the FIR-SFR relation (Kennicutt & Evans 2012). Considering here the sum of the
stellar mass for both galaxies, we show the location of





**Figure** **3.** SED of PACS-787 (Total; East + West) with
best-fit dust model (Draine & Li 2007) to the FIR emission. The individual components to the fit are shown in
color (stars: cyan; AGN - yellow; warm dust - red; cool dust

- purple). Blue squares show photometric measurements and
their 1 _σ_ errors. A power law radio spectrum highlights the
agreement between star formation rate indicators.


4.2:1 thus indicative of a marginal major merger. However, when also considering the mass of the molecular
gas (see Section 6.1) the mass ratio becomes _∼_ 2 : 1,
which definitely qualifies the system as a major merger.


2.2. _Star_ _formation_ _rate_ _(SFR)_


Far-infrared (FIR) emission, primarily from cool and
warm dust heated by young massive stars, has been
demonstrated to be an accurate indicator of the SFR
of galaxies (Kennicutt & Evans 2012), particularly starbursts which are heavily enshrouded by dust. Hence,
we measure the total FIR luminosity that is determined
from an integral of a best-fit dust model over the wavelength range 8 - 1000 _µ_ m.
Dust emission is measured using models (Draine &
Li 2007) that fit the observations covering the mid- to
far-infrared wavelengths (e.g., Magdis et al. 2012a). As
shown in Figure 3, continuum emission from PACS-787
is detected by Spitzer/MIPS (24 _µ_ m), Herschel/PACS
(100 and 160 _µ_ m), Herschel/SPIRE (250, 350 and 500
_µ_ m) and ALMA (1.28 mm) that covers the extent of
the FIR spectral-energy distribution (SED). Following
Magdis et al. (2012a), we simultaneously fit the broadband SED using a model with five components: stellar
light, warm and cool dust, an AGN, and radio powerlaw emission. The latter is decoupled from the global fit.
We do not require energy balance between the FIR and
absorbed UV emission since the dust and UV radiation

in starbursts are not co-spatial as the case for PACS-787
and our full starburst sample (Silverman et al. 2015a;
Puglisi et al. 2017).

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 7





10.0"


08.0"


06.0"


04.0"


02.0"


+2°10'00.0"


10.0"











10 [10] 10 [11]
M stellar (M ⊙ ⊙


**Figure** **4.** Location of PACS-787 on the star-forming MS
(SFR versus M _stellar_ ). Both the sum (total) and the individual (East and West) galaxies are indicated by large green circles with the latter based on high-resolution ALMA continuum observations (Section 6.2). Galaxies with 1 _._ 4 _< z_ _<_ 1 _._ 7
in COSMOS are shown for comparison (MS galaxies - grey
dots; red symbols - _Herschel_ -detected). The blue circles
indicate those having CO(2 - 1) observations with ALMA.
Slanted lines indicate the MS (solid; z = 1.5) and a parallel
track at an elevated rate of 4 _×_ (dashed).


PACS-787 at an elevation 6 _._ 5 _×_ higher with respect to
the star-forming MS, thus securely undergoing a starburst event.


3. ALMA OBSERVATIONS AND DATA ANALYSIS


As part of our program to measure the molecular gas
properties of high-z starbursts (Silverman et al. 2015a,
2018), we obtained a low resolution (1.7 _[′′]_ ) observation
of PACS-787 in ALMA Cycle 3 (Project 2015.1.00861.S)
to detect CO(2 - 1) at 91.31 GHz (Band 3). This target has the brightest CO emission of our full sample
with _I_ _CO_ [2 _−_ 1] = 1 _._ 64 _±_ 0 _._ 20 Jy km s _[−]_ [1] . The emission,
reproduced in Figure 5, is indicative of a single source
with marginal evidence of being extended. As shown in
Figure 5 of Silverman et al. (2018), there are signs of
different kinematic components. The CO(2-1) luminosity of PACS-787, based on this observation, is used in
this study (Section 5.5) to measure the ratio of _M_ _gas_ to
_L_ _[′]_ _CO_ 1 _−_ 0 [(] _[α]_ _[CO]_ [)] [with] _[M]_ _[gas]_ [being] [assessed] [independent]
of the CO luminosity.
To determine the nature of this extreme starburst, we
acquired a higher resolution CO(5 - 4) map of PACS-787,
along with two additional starburst galaxies (PACS-830
and PACS-819) elevated above the MS star-forming population at similar redshifts. Here, we report on the ob


08.0"


06.0"


04.0"


02.0"


+2°10'00.0"


28.20s 28.00s 27.80s 10h02m27.60s


RA (J2000)


**Figure** **5.** Low resolution ALMA imaging of PACS-787.
(top) CO(2 - 1) map with contours at 2, 4, 6, 8, 10 _× σ_ _rms_
where _σ_ _rms_ = 0 _._ 085 Jy beam _[−]_ [1] km s _[−]_ [1] . (Bottom) CO(5 4) map with contours at 2, 4, 8, 16, 24 _× σ_ _rms_ where _σ_ _rms_ =
0 _._ 1487 Jy beam _[−]_ [1] km s _[−]_ [1] . The ALMA beamsize is shown
in the lower left of each panel.


servations of PACS-787 by itself since the nature of the
source is distinct from the others with clear evidence for

two gas-rich interacting galaxies at an early stage of the
merger. In Table 1, we list the ALMA observations used
in this study.


3.1. _High_ _resolution:_ _CO(5_ _-_ _4)_ _and_ _continuum_
_emission_ _at_ _1.28_ _mm_


PACS-787 was observed on November 7, 2016 with 43
12m antennas as part of our Cycle 4 program (Proposal
#2016.1.01426.S; PI J. Silverman). The antenna baselines spanned a range of 18.6 m to 1.11 km that resulted
in beam size of 0 _._ 38 _[′′]_ _×_ 0 _._ 34 _[′′]_ and a maximum recoverable scale of 2.98 _[′′]_ . Four spectral windows were assigned
within Band 6 to detect the CO (5 - 4; _ν_ _rest_ = 576.27
GHz) emission line and underlying continuum. The onsource integration time was 19.73 minutes. The calibra

8 Silverman et al.


**Table** **1.** Summary of ALMA observations used in this study


Obs. date Band Spectral Central frequency Band width Channel width Integration time Beam size _σ_ _rms_


(UT) feature (GHz) (GHz) (MHz) (min) ( _[′′]_ ) (mJy beam _[−]_ [1] )


2016Mar04 3 CO(2   - 1) 89.00, **91.00** [a] 1.875, 1.875 1.95, 1.95 6.55 2 _._ 7 _×_ 1 _._ 8 0.085 [b]


101.10,103.00 1.875, 1.875 15.6, 15.6


2016Nov07 6 CO(5   - 4) 226.01, **228.43** [a] 2.0, 1.86 15.62, 3.91 19.73 0 _._ 4 _×_ 0 _._ 3 0 _._ 045 [b]


241.01, 244.01 2.0, 2.0 15.62, 15.62


2017Mar18 6 CO(5   - 4) 226.01, **228.43** [a] 2.0,2.0 15.62, 15.62 10.2 1 _._ 9 _×_ 1 _._ 3 0 _._ 186 [b]


241.01, 244.01 2.0, 2.0 15.62, 15.62


_a_ The central frequency in bold indicates the spectral window for which the CO line falls within.


_b_ rms noise level for a channel width of 600 km s _−_ 1 centered on the CO emission-line



tion targets are J1058+0133 (bandpass, flux, pointing),
and J0948+0022 (phase).
As part of the same program, PACS-787 was reobserved on March 18, 2017 with 42 antennas in a compact configuration having a maximum baseline of 278.9
m thus resulting in a beam size is 1 _._ 9 _[′′]_ _×_ 1 _._ 3 _[′′]_ . The purpose of this observation was to measure the total CO(5
- 4) emission including any component (see Section 7)
that may be undetected on larger scales with the higher
resolution observations. We employed the same four
spectral windows in Band 6 as for the high-resolution
observations. The target was observed for 10.2 minutes (on-source). Observations of standard calibration
sources were taken as mentioned above. In the bottom
panel of Figure 5, we show the low resolution CO(5-4)
image of PACS-787.


3.2. _Emission-line_ _and_ _continuum_ _measurements_


We use Common Astronomy Software Applications
(CASA) to carry out the processing of the ALMA raw
data though the standard pipeline. From the visibility
files, we then generate images using the task ‘clean’ with
a natural weighting scheme of the antenna pattern. The
image cube is collapsed using ‘immoment’ over a velocity range (given as ∆v in Table 2) that encompasses
the CO(5 - 4) line. Continuum images make use of the
full spectral range without channels having CO emission. We perform scientific analysis on the fits images
as described below. Measurements are confirmed using a separate analysis package, GILDAS, and the task
‘uvmodelfit’.


4. OBSERVATIONAL RESULTS


4.1. _Molecular_ _line_ _emission_ _(CO_ _5_ _-_ _4)_


Using the high-resolution data, CO(5  - 4) emission
from PACS-787 is detected at high significance as shown
in Figure 6. As opposed to the single source seen at



lower spatial resolution (Figure 5), we now detect two
distinct galaxies that each have bright CO(5 - 4) emission. The dual nature of the source at long wavelengths
is also evident in the continuum at 1.28 mm (Fig. 6, topright panel) and in the radio (bottom-right panel) at 3
GHz (Smolˇci´c et al. 2017). The galaxies are clearly undergoing an interaction or merger as evidence by their
close proximity both on the sky and along the line of
sight with the two redshifts, based on the centroid of
the CO emission (Figure 7), being very close to each
other ( _z_ _East_ = 1 _._ 5256; _z_ _W est_ = 1 _._ 5240), corresponding to a radial velocity difference of _∼_ 400 km s _[−]_ [1] . In
further support of a merger scenario, we see signs of
low-level extended CO(5 - 4) emission (Section 7) and
diffuse stellar emission in the HST/WFC3 F140W image (Figure 1), both evidence for a likely bridge between
the two galaxies.
We measure the CO properties of each galaxy separately by fitting the spatial distribution of the emission
using the CASA tool ‘imfit’ with an elliptical Gaussian
model. This is carried out on an image of the CO emission, generated with the task ‘immoments’, with a channel (i.e., velocity) width encompassing the full line profile (∆v) for each galaxy as given in Table 2. From the
centroid of each component, the projected separation of
the two galaxies is 1.02” that corresponds to 8.65 kpc
at _z_ = 1 _._ 5249. The half-light radii of the two galaxies are similar and _∼_ 1 kpc based on the size of the
major axis (East: _r_ 1 _/_ 2 = 0.106 _±_ 0 _._ 006 _[′′]_ = 0.90 _±_ 0.05
kpc; West: _r_ 1 _/_ 2 = 0.141 _±_ 0.005 _[′′]_ = 1.19 _±_ 0.04 kpc).
With respect to the strength of the CO emission, the
eastern galaxy has a slightly higher velocity-integrated
flux, I _[east]_ _CO_ [=2.82] _[±]_ [0] _[.]_ [08] [Jy] [km] [s] _[−]_ [1] [(] _[S/N]_ [=] [35)] [as] [com-]
pared to the western galaxy (I _[west]_ _CO_ [=2.03] _[±]_ [0] _[.]_ [10] [Jy] [km]
s _[−]_ [1] ; _S/N_ = 20). Considering the different velocity intervals over which the line is measured (Sec. 4.2), the
specific fluxes are S _[east]_ _CO_ [=3.77] _[±]_ [0.11] [mJy] [for] [the] [eastern]

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 9



28.05s 28.00s 27.95s 27.90s 10h02m27.85s


RA (J2000)


28.05s 28.00s 27.95s 27.90s 10h02m27.85s


RA (J2000)



06.0"


05.5"


05.0"


04.5"


04.0"


03.5"


+2°10'03.0"


+2°10'03.0"



28.05s 28.00s 27.95s 27.90s 10h02m27.85s


RA (J2000)



**Figure** **6.** ALMA imaging of PACS-787 reveals two separate galaxies, both bright in CO (5 - 4; top-left panel) and continuum
(1.28 mm; top-right panel), in the early stages of an interaction given the projected separation of 8.6 kpc. The ALMA beam size
is shown in the lower left corner of the top two panels. HST/ACS imaging (bottom-left panel) only detects diffuse tidal features
and a bright component in the Western galaxy. The blue contours indicate the CO brightness level at 2, 3, 5, 10, 20, 40 _× σ_ _rms_
where _σ_ _rms_ = 0 _._ 039 Jy beam _[−]_ [1] km s _[−]_ [1] . In the bottom right panel, the ALMA continuum emission (aqua blue contours at the
same multiples of _σ_ _rms_ = 2 _._ 037 _×_ 10 _[−]_ [5] Jy beam _[−]_ [1] as the left panel) is in excellent agreement with radio emission at 3 GHz
(Smolˇci´c et al. 2017), indicative of their ongoing star formation. In each panel, North is up and East is to the left.



and S _[west]_ _CO_ [=6.00] _[±]_ [0.30] [mJy] [for] [the] [western] [components.]
Based on these integrated fluxes, the emission-line luminosities are calculated as follows (Carilli & Walter 2013).


_L_ _[′]_ CO(5 _−_ 4) [= 3] _[.]_ [25] _[ ×]_ [ 10] [7] _[S]_ [CO(5] _[−]_ [4)] [∆] _[v]_ _[ν]_ obs _[−]_ [2] _[D]_ _L_ [2] [(1 +] _[ z]_ [)] _[−]_ [3]

(1)


We find high CO luminosities ( _L_ _[′]_ CO 5 _−_ 4 [)] [of] [1] _[.]_ [3] _[ ×]_ [ 10] [10]

(East) and 9 _._ 5 _×_ 10 [9] K km s _[−]_ [1] pc [2] (West). The sum of
the CO(5 - 4) luminosity for both galaxies is close to the
expected value of _L_ _[′]_ CO 5 _−_ 4 [=] [2] _[.]_ [0] _[ ×]_ [ 10] [10] [K] [km] [s] _[−]_ [1] [pc] [2]

based on the relation ( _L_ _CO_ 5 _−_ 4 vs. _L_ _IR_ ) from Daddi et
al. (2015) and the total SFR of 991 M _⊙_ yr _[−]_ [1] .



4.2. _Gas_ _kinematics_


There is much interest in determining the impact of
a major merger on the kinematics of the gas that is
initially confined to molecular disks in isolated gas-rich
galaxies (e.g., Hopkins et al. 2013). PACS-787 provides
an opportunity to study the gas kinematics in an early
stage of such a merger. In fact, we find evidence for the
CO emission-line profile for both galaxies to be consistent with a disk in rotation, especially that of the eastern galaxy with an apparent double horn (Figure 7, top
panel). Furthermore, there is a clear relation between
position and velocity of the CO emission for both galaxies as shown in Figure 8. To quantify the significance

10 Silverman et al.



**Figure** **7.** CO(5-4) emission-line profile for each galaxy. A
best-fit model (in red) is shown for each galaxy based on a
double Gaussian function of fixed velocity width with values
given in the text and Table 2. The vertical line indicates
the line centroid used to determine the redshift of each component. The horizontal line (in green) indicates the fit to
the continuum that is included in the overall fit to the line
profile.


of the offset between position and velocity, we generate
two images for each galaxy in narrow velocity intervals
both redward and blueward of the line center as indi
cated in the top panels of Figure 9. As expected for
resolved emission if undergoing rotation, we find a significant displacement in the spatial location of the blue
and red velocity maps for each galaxy (Fig. 9, bottom
panels). For each galaxy, we measure the offsets between
red and blue components to be ∆ _r_ = 152 _±_ 14 milliarcsec (1 _._ 29 _±_ 0 _._ 12 kpc) and ∆ _r_ = 110 _±_ 16 milliarcsec
(0 _._ 93 _±_ 0 _._ 14 kpc) for the East and West galaxies, respectively. The difference in the location of the blue and red
components for both galaxies indicate a scenario with
the disks likely in counter-rotation (as further discussed
in Section 8).
It is also evident that the CO emission-line profiles of
the two galaxies are noticeably different in width (e.g.,



**Figure** **8.** Position - velocity map of the CO(5 - 4) emission.
The image was constructed using a horizontal spatial region
(i.e., collapsing the image along the declination axis) with a
width of 5 pixels. The velocity scale is set to zero on the
peak of the western source and positive velocities represent
red-shifted emission. Faint continuum emission is seen for

each galaxy across all velocity channels.


Fig. 9); the emission line of the western galaxy is significantly narrower than its eastern counterpart. We perform a fit to the emission line to determine the full-width
velocity at half maximum ( _v_ _F W HM_ ) of each galaxy with
a double Gaussian model of a single fixed velocity width
for each component (Figure 7). The centroid of each
Gaussian component is allowed to vary. For both CO
emission lines, we find acceptable fits to the line profile
in each case (West: _v_ _F W HM_ = 271 _._ 7 _±_ 82 _._ 0 km s _[−]_ [1], East:
_v_ _F W HM_ = 688 _._ 4 _±_ 88 _._ 8 km s _[−]_ [1] ). This leaves little room
for additional components such as due to an outflow.
As discussed in Section 5.1, we attribute the different
velocity widths to be due to a difference in inclination
angle based on the axis ratio of an elliptical Gaussian
fit to the CO surface brightness with the western galaxy
being closer to face-on than the galaxy to the east.


4.3. _Continuum_ _emission_


For both galaxies, we detect the continuum with a
high level of significance (East: _S/N_ = 25; West:
_S/N_ = 17) at the observed wavelength of 1.276 mm
( _ν_ = 235 _._ 0 GHz). In the top-right panel of Figure 6,
we display an image of the two galaxies for which all the
spectral channels, devoid of CO line emission, have been
summed. The continuum emission is co-spatial with the
CO(5 - 4) emission. For the western galaxy, we find
similar fit parameters to the surface brightness using
an elliptical Gaussian model ( _r_ 1 _[W est]_ _/_ 2 = 0 _._ 14 _±_ 0 _._ 02 _[′′]_ ).
The eastern continuum source is unresolved. The inte

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 11













starbursts in general. This is accomplished by considering the contribution to the dynamical mass (within
a half-light radius) from stars, molecular gas, and dark
matter. As a novelty, we incorporate a correction (i.e.,
scale) factor ( _f_ _c_ ) to account for gas motions, out of equilibrium, that can falsely alter the measured dynamical
masses due to turbulence, dispersion, clumpiness, and
inflows/outflows (Sec. 5.2). We measure the dynamical
mass, for each galaxy separately, within a half-light radius ( _r_ 1 _/_ 2 ) for the case of a thin-disk rotator (Neri et al.
2001) as given here:






[(] _[v]_ _[F W HM]_ _[/]_ [2][)] [2]
_M_ dyn ( _r_ _< r_ 1 _/_ 2 ) = _f_ _c_ _×_ _[r]_ [1] _[/]_ [2] _[ ×]_ (2)

_G_ _sin_ [2] _i_





where _v_ _F W HM_ is the observed FWHM of the CO(5 4) line profile and _r_ 1 _/_ 2 is the half-light radius, as reported above and in Table 2. We acknowledge that the
thin-disk approximation may be a poor choice for high
redshift galaxies which are characterized by high velocity dispersion. Therefore, our estimates of _M_ dyn may
be somewhat underestimated, and so would be the gas
mass (though part of this effect is included in the _f_ _c_
factor).


5.1. _Disk_ _inclination_ _angle_



exhibits a double-peaked profile indicative of coherent disk
rotation, likely counter-rotating as illustrated by a comparison of the images of the CO emission both red- and blueward
from the line center as overlaid on the 1.28 mm continuum
image (grey scale; bottom panel). The offsets between the
centroids of the red and blue emission for each galaxy are
highly significant (East: ∆ _r_ = 152 _±_ 14 milliarcsec; West:
∆ _r_ = 110 _±_ 16 milliarcsec).


grated flux density of the East (West) components are
0 _._ 75 _±_ 0 _._ 03 (0 _._ 68 _±_ 0 _._ 04) mJy, respectively. In subsequent
sections, we use the continuum emission to estimate the
dust mass, dust-to-gas ratio, and SFR for each galaxy.


5. MOLECULAR GAS MASS THROUGH A

DYNAMICAL ASSESSMENT


We measure the dynamical mass using a method
widely employed in the literature (e.g., Tacconi et al.
2008; Daddi et al. 2010a; Tan et al. 2014; Tadaki et al.
2017) to assess the molecular gas content, independent
of the CO luminosity or mm continuum. This allows us
to evaluate the value of the factor to convert CO luminosity to molecular gas mass (Section 5.5) that is appropriate for our starburst sample and possibly for high-z



The disk inclination angle _i_ is estimated from the output parameters of an elliptical Gaussian model fit to
the spatial distribution of the CO(5 - 4) emission. We
measure the value of _i_ and its uncertainty from the ratio of the size of the minor to major axis. For example,
the CO emission for the western galaxy has a major axis
(FWHM) of 0 _._ 28 _±_ 0 _._ 02 _[′′]_ and a minor axis of 0 _._ 22 _±_ 0 _._ 02 _[′′]_ .
We find the inclination angles to be 55 [+5] _−_ 6 [(East)] [and]
38 [+7] _−_ 10 [(West)] [degrees] [for] [each] [respective] [galaxy.] We
highlight that these constraints on the inclination angle
are afforded by the high S/N detections of the ALMA
data. As expected, the difference in the inclination angles between the two nuclei concurs with the difference
in the velocity widths of the CO lines with the western
component closer to being face-on than the eastern nuclei. Remarkably, the differences in inclination of the
gas distribution between the two galaxies agrees with
the different shapes of the stellar light from each galaxy
in the HST WFC3 image (Figure 1).


5.2. _Evaluation_ _of_ _f_ _c_ _using_ _hydrodynamic_ _simulations_


We use available simulations of gas-rich galaxy mergers (Fensch et al. 2017) with similar properties to
PACS-787 to determine how well our method to es
timate the dynamical mass represents the true dynamical mass since various physical effects, including turbulence, velocity dispersion, clumpiness, and inflows

12 Silverman et al.



(non-equilibrium effects), may be non-negligible. Our
simulation sample includes several mergers of galaxies,
with initial conditions (dark matter halo concentration,
stellar mass distribution, gas fraction) and interaction
orbits representative of star-forming galaxies at redshift
z = 1 - 2. These simulations have a maximal resolution

of 6 pc, making it possible to model very high-density
gas up to _∼_ 10 [5] _[−]_ [6] cm _[−]_ [3], and to explicitly resolve the
main sites of star formation. While these simulations

predict that the SFR enhancement in gas-rich mergers
at high redshift is, on average, weaker than in gas-poor
low-redshift mergers, they do include phases with substantial SFR enhancements and deviations from the

MS and Kennicutt-Schmidt relation that characterize

isolated star-forming galaxies.
We use this sample of simulations to determine the
difference between the ‘observed’ and ‘true’ dynamical
mass. Specifically, we select 15 snapshots where the
merger has triggered a substantial SFR enhancement
( _>_ 3 _×_ ) and generate 10 random projections for each
snapshot. We exclude projections where the angular
momentum is inclined by less than 20 _[◦]_ or more than 70 _[◦]_

from the line-of-sight, because the observed morphology
of PACS-787 strongly suggest that the system is not observed as being close to edge-on (the spatial distribution
of gas in each galaxy would be highly flattened), and the
observed velocity gradients indicate that the system is
not observed close to being face-on (the projected velocity amplitudes would be substantially lower). The simulated projections are distributed in an isotropic manner
over the allowed range. We post-process the simulation
outputs with a dedicated tool (Bournaud et al. 2015)
that models CO(5 - 4) emission, smoothed to match the
spatial resolution of the ALMA observations, and use
the mock CO emission line to estimate the dynamical
mass as defined in Equation 2. We compare to the dynamical mass encompassed in the same region (which
is directly known in simulations). We find that our dynamical mass estimates are low by a factor of 2.0 (Figure 10). The underestimated value results from projection factors (i.e., the projection angle of PACS-787 is
unknown and the mock data are analyzed without assuming a known projection angle) and physical effects
such as turbulence and non-circular gas motions. We use
the average ratio and dispersion (0.2 in log _M_ _dyn_ _/M_ _real_ )
that encompasses 75% of the trials shown in Figure 10,
as input ( _f_ _c_ ) to our dynamical mass estimate.


5.3. _Likelihood_ _distribution_ _of_ _the_ _dynamical_ _mass_


We calculate the dynamical mass within a half-light
radius, as given in Equation 2, by generating 10k realizations that incorporate all sources of uncertainty



0.40


0.35


0.30


0.25


0.20


0.15


0.10


0.05


0.00

−1.5 −1.0 −0.5 0.0 0.5 1.0
log 10 (M dyn /M real )


**Figure** **10.** Hydrodynamic simulations of high-redshift
galaxy mergers (Fensch et al. 2017). _Top_ : Example simulation of CO-emitting gas in a galaxy merger with similar
properties to PACS-787 at a higher spatial resolution of 0.04”
(350 pc at z = 1.5) than our current data. _Bottom_ : Ratio
of the dynamical mass as measured in Equation 2 compared
to the ‘true’ value from a suite of simulations. The mean

of the distribution of trials indicates that _M_ _dyn_ is typically
underestimated by a factor of 2.


while assuming Gaussian distributions for each parameter with errors (1 _σ_ ) provided in Table 2. For our purpose of using the dynamical mass to assess the amount
of molecular gas mass independent of CO luminosity
(see below), we sum the dynamical masses from both
galaxies to lessen the effect of random errors on individual measurements. The results of this exercise are

shown in Figure 11 _a_ . In addition to the full distribution of trials, we indicate the median dynamical mass
( _M_ _dyn_ ( _r_ _<_ _r_ 1 _/_ 2 ) = 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [6] 4 _[×]_ [ 10] [11] [M] _[⊙]_ [)] [and] [an] [interval]
containing 68% of the realizations.


5.4. _Contribution_ _of_ _gas_ _to_ _the_ _dynamical_ _mass_


The total gas mass ( _M_ _gas_ ), including both galaxies, is derived from the following equation that relates
the different contributions (i.e., _M_ _gas_, _M_ _stellar_, and
_M_ _dark_ _matter_ ) to the dynamical mass ( _M_ _dyn_ ).


_M_ gas = 2 _×_ [ _M_ dyn ( _r_ _< r_ 1 _/_ 2 ) _−_ _M_ _dm_ ( _r_ _< r_ 1 _/_ 2 )] _−_ _M_ _stellar_

(3)

500


400


300


200


100


0



Molecular gas in colliding galaxies at _z_ = 1 _._ 52 13


400





10.2 10.4 10.6 10.8 11.0 11.2 11.4 11.6 11.8
log M dyn (r < r 1/2 )


350


300


250


200


150


100


50


0

0 20 40 60 80 100 120 140 160
M gas /M dust



350


300


250


200


150


100


50


0

8.5 9.0 9.5 10.0 10.5 11.0 11.5 12.0
M
gas


350


300


250


200


150


100


50


0

0 1 2 3 4 5 6 7 8

α co



**Figure** **11.** Dynamical modeling of the total (i.e., sum of both galaxies) CO emission to derive the (a) dynamical mass within
a half-light radius, (b) total gas mass, (c) gas-to-dust ratio, and (d) _α_ _CO_, the ratio of _M_ _gas_ to _L_ _CO_ 1 _−_ 0 . Median values and the
68% regions are indicated by the vertical lines in the top two panels. In the bottom panels, the median value is shown along
with vertical dashed lines that indicate the value for which a percentage of trials, as given, are lower.



_M_ _dyn_ is determined using Equation 2 that is applied to
our data and simulated observations of galaxy mergers
matched to the properties of PACS-787. This ensures
that the distribution of _M_ _gas_ includes unphysical results
that factor into the assessment of the uncertainties. We
assume that the dark matter mass ( _M_ _dm_ ) is equal to
0 _._ 2 _×_ _M_ _dyn_ with a dispersion of 0.05, consistent with
that of local disk galaxies (De Blok et al. 2008; Genzel
et al. 2017). The measurement of the stellar mass is
described in Section 2.1. In Figure 11 _b_, we show 10k
realizations to assess the distribution of _M_ _gas_ that has a
median gas mass and likelihood distribution (i.e., a 68%
confidence interval) of _M_ _gas_ = 7 _._ 5 [+10] _−_ 7 _._ 1 _[.]_ [3] _[×]_ [ 10] [10] [M] _[⊙]_ [.] [The]
large estimate of the lower bound of the confidence interval is due to a non-negligible fraction (14%) of cases that
are unphysical due to a dynamical mass that is smaller
than the stellar mass. Such solutions are primarily the
result of uncertainties on each parameter, in particular,
the inclination of the western galaxy (being closer to
face-on) or a low correction factor _f_ _c_ . Even so, there



are important implications from placing a constraint on
the maximum amount of gas that may be present as
demonstrated below.


5.5. _α_ _CO_


We use the dynamical assessment of _M_ _gas_ for the sum
of both galaxies to estimate the median value and upper
limits on the ratio of _M_ _gas_ to _L_ _[′]_ _CO_ 1 _−_ 0 [(] _[α]_ _[CO]_ [;] [units] [of]
_M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] ), a key conversion factor used
in the literature to derive gas masses from the CO luminosity (see Bolatto, Wolfire & Leroy 2013, for a review). Currently, there are few constraints on _α_ _CO_
at high redshifts. First, we measure the total CO(1
 - 0) luminosity ( _L_ _[′]_ _CO_ 1 _−_ 0 [=] [5] _[.]_ [79] _[±]_ [0] _[.]_ [69] _[×]_ [10] [10] [K] [km]
s _[−]_ [1] pc [2] ) from our estimate of the CO(2 - 1) luminosity, as reported in Silverman et al. (2018), and the
appropriate conversion factor between CO excitation
levels ( _L_ _[′]_ _CO_ 2 _−_ 1 _[/L]_ _[′]_ _CO_ 1 _−_ 0 [=] [0] _[.]_ [85;] [Daddi] [et] [al.] [2015][).]
We confirm that an additional uncertainty ( _∼_ 15%) on
_L_ _CO_ 2 _−_ 1, due to flux calibration, has no impact on the

14 Silverman et al.



results due to the larger uncertainty on _M_ _gas_ . With
10k realizations (Figure 11 _d_ ), we find the median _α_ _CO_
to be 1.3 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] . Due to the significant number of trials for which our procedure fails to
provide a physical result (i.e., a positive gas mass), we
cannot place a reliable lower limit on the value of _α_ _CO_ .
Although, a theoretical lower limit would correspond to
_≈_ 0 _._ 3 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] in the optically-thin case
(Papadopoulos et al. 2012; Bolatto, Wolfire & Leroy
2013). For the upper limit, we find that 84% of the
trials have a value less than 3.1 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1]

as shown in the figure. Furthermore, 92% of the realizations have a value less than 4.36 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1]

that is commonly used (Tacconi et al. 2018). If our stellar mass estimates are in reality higher, the amount of
gas will be effectively lower, as will _α_ _CO_ . Using stellar
masses based on a Salpeter as opposed to a Chabrier
IMF, we find 96% of the trials to have _α_ _CO_ _<_ 4 _._ 36 _M_ _⊙_
(K km s _[−]_ [1] pc [2] ) _[−]_ [1] . Our estimate of _α_ _CO_ given here as
1.3 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] is used for subsequent estimates of the total molecular gas mass for each individual galaxy in PACS-787 and the full sample of starbursts
having CO(2 - 1) luminosities in Silverman et al. (2018).
In Figure 12, we compare our estimate of _α_ _CO_ for
PACS-787 to other measurements in the literature and

derived relations with gas-phase metallicity. We include results based on Local Group galaxies (Leroy et
al. 2011), MS galaxies with _z_ _∼_ 0 _._ 5 _−_ 1 _._ 5 (Magdis
et al. 2012a), high-z SMGs (i.e., GN 20, SMM J21350102, HERMES J105751.1+573027) and local ULIRGs
(Downes & Solomon 1998). The gas-phase metallicities
are based on the calibration of Pettini & Pagel (2004).
In addition, we show analytic relations from Genzel et
al. (2015) and Tacconi et al. (2018). The metallicity
measurement for PACS-787 is based on the [NII]/H _α_
ratio reported in Appendix A. From the Figure, it is evident that PACS-787 has a value of _α_ _CO_ closer to that
of local ULIRGs and dissimilar to the value of 4.36 _M_ _⊙_
(K km s _[−]_ [1] pc [2] ) _[−]_ [1] as expected from published relations
(e.g., Tacconi et al. 2018). As discussed in Appendix A,
there may be an AGN that contributes to the emission
line flux, in particular [NII] thus we have placed an arrow indicating that the metallicity may be lower. This
has no effect on our conclusions since a lower metallicity would result in a further discrepancy with the higher
value of the conversion factor (i.e., 4.36).


5.6. _Dust-to-gas_ _ratio_


Using the total dust mass (Section 2.2), we estimate
the likely value of the gas-to-dust (G/D) ratio to be
35 based on the median of 10k trials (Figure 11 _c_ . On
the upper limit, we find that 84% of the trials have


|Col1|Col2|Col3|Col4|
|---|---|---|---|
|αCO|102|||
|αCO|101|101|101|
|αCO|100|Gen/el+(2015)<br>Ta  oni+(2018)<br>|Gen/el+(2015)<br>Ta  oni+(2018)<br>|
|αCO|11|PACS-787|PACS-787|



**Figure** **12.** _α_ _CO_ as a function of gas-phase metallicity with
PACS-787 indicated in red and all other reference samples
and relations as described in the text.


_G/D_ _<_ 83. Of course, the gas mass, hence G/D,
has considerable uncertainty coming from the difference ( _M_ _dyn_ _−_ _M_ _stellar_ _−_ _M_ _DM_ ) of comparable quantities, each affected by sizable errors. The 10k realizations
are meant to incorporate all known uncertainties. In
any case, this range of the G/D ratio is consistent that
from Magdis et al. (2012a) given its high total stellar
mass that likely indicates a high gas-phase metallicity
based on the M-Z relation at _z_ _∼_ 1 _._ 5 from Kashino et
al. (2017). In fact, the [NII]/H _α_ ratio shown in Figure 16 could provide evidence for high-metallicity gas.
Although, we cannot rule out the influence of a weak
AGN on the line ratio.


6. DERIVED PHYSICAL PROPERTIES FOR EACH

GALAXY


6.1. _Gas_ _masses_


Preferably, the gas mass for each individual galaxy
should be determined from a dynamical assessment
based on their respective CO(5-4) emission. However,
there are limitations with respect to this data set, when
considering each galaxy separately, due to random effects that we are trying to mitigate as discussed above;
thus, for this exercise, we determine the amount of
molecular gas in each individual galaxy based on the
CO emission which is calibrated by an independent analysis through dynamical modeling (Section 5.4) to assess the conversion factor _α_ _CO_ . The total gas mass
( _M_ _gas_ = _α_ _CO_ _×L_ _[′]_ _CO_ 1 _−_ 0 [) is based on the CO(2 - 1) emis-]
sion for the two blended galaxies, the conversion factor





8.0 8.2 8.4 8.6 8.8 9.0 9.2 9.4
Metallicity [12+ log (O/H)]

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 15



to CO(1 - 0) luminosity, and the value of _α_ _CO_ to be 1.3
_M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] . This is equivalent to using the
median total gas mass based on the dynamical argument
given above while assessing the error on _M_ _gas_ to reflect
the error on CO(2-1) luminosity and not on the uncertainty of _α_ _CO_ . The contribution from each galaxy, to the
total gas mass is then determined based on the ratio of
the CO(5 - 4) emission that is cleanly separated between
the two components (Figure 6). This assumes that the
excitation states of the two galaxies are the same. As
reported in Table 2, we find high gas masses for both
galaxies: 4 _._ 4 _±_ 0 _._ 6 _×_ 10 [10] M _⊙_ (East) and 3 _._ 2 _±_ 0 _._ 4 _×_ 10 [10]

M _⊙_ (West). With these gas masses, we further estimate
the gas fraction _f_ _gas_ to be 70 [+8] _−_ 11 [(28] _−_ [+7] 6 [)] [%] [for] [the] [East]
(West) components respectively as given by Equation 4.


|Col1|Col2|Col3|
|---|---|---|
|100<br> Gyr⊙|||
|100<br> Gyr⊙|||



= _M_ _gas_
_f_ _gas_ _M_ _gas_ + _M_ _stellar_



(4)



10 [0] 10 [1] 10 [2] 10 [3]

SFR (M ⊙ yr [−1] ⊙


**Figure** **13.** Gas depletion time ( _τ_ _depl_ = _M_ _gas_ _/SFR_ ) of the
individual galaxies associated with PACS-787 as a function of
their SFR (green symbols) both with 1 _σ_ errors as indicated.
Slanted black line is the best-fit relation from Sargent et al.
(2014). Red (filled) data points mark our other 11 highz starbursts as described in Silverman et al. (2018). The
inverted triangle represents a 3 _σ_ upper limit. Small grey
circles (black triangles) represent SF MS galaxies at _z_ _<_
1 ( _>_ 1) as compiled by Sargent et al. (2014) that include
samples from HERACLES (Leroy et al. 2013), COLD GASS
(Saintonge et al. 2011), THINGS (Walter et al. 2008) and
additional higher redshift studies (e.g., Geach et al. 2011;
Daddi et al. 2010a,b; Magdis et al. 2012b; Tacconi et al.
2013; Magdis et al. 2017). The blue symbols show the local
ULIRGs (crosses; Solomon et al. 1997) and additional high-z
starbursts (filled blue squares).


Recently, Daddi et al. (2015) have demonstrated that
the integrated CO(5 - 4) luminosity can be used as an
indirect tracer of the SFR. As a check on the SFRs measured above, the _L_ _[′]_ CO(5 _−_ 4) [for] [each] [galaxy] [is] [converted]
to SFR through its correlation with _L_ _T IR_ in Equation
4 of the aforementioned paper. We find that SFRs are,
in general, in very good agreement with those reported
above. The western component is essentially the same
while the eastern nucleus is sightly higher by 26%. Each
of these methods based on the ALMA fluxes, either the
integrated line emission or the continuum, indicate high
levels of star formation ( _>_ 300 M _⊙_ yr _[−]_ [1] ) in each galaxy.
Using the SFRs based on total _L_ _T IR_ and the ratio of
the continuum luminosity at 1.28 mm, we plot the location of each galaxy in relation to the star-forming MS
in Figure 4. We find that both nuclei are undergoing
a starburst event having SFRs elevated by ≳ 4 _×_ above
the MS given their stellar mass estimates. In particular, the boost in SFR is notably high (15 _×_ ) for the less



6.2. _Star_ _formation_ _rates_ _and_ _gas_ _consumption_
_timescales_


With each galaxy detected separately by ALMA,
HST, VLA and UltraVISTA, we assess the impact of
the merger on the SFR for the individual components.
We start from the total SFR for both galaxies (991 _−_ [+96] 87
M _⊙_ yr _[−]_ [1] ) based on _Herschel_ photometry (Section 2.2).
We then determine the SFRs for each galaxy separately
(East: 515 _±_ 56 M _⊙_ yr _[−]_ [1] ; West: 476 _±_ 47 M _⊙_ yr _[−]_ [1] )
under the assumption that the ratio (1 _._ 10 _±_ 0 _._ 08) of the
continuum emission at _λ_ _rest_ = 505 _._ 5 _µ_ m, detected by
ALMA, reflects the ratio in SFR. This assumes the dust
species and temperature of both galaxies are the same
thus have similar SEDs.

As an independent check, we measure the SFR from
the radio flux at 3 GHz (Smolˇci´c et al. 2017) that is
observed at spatial resolution sufficient to detect each
galaxy as shown in the bottom right panel of Figure 6.
It is interesting to note that the flux ratio of the 3
GHz emission between the eastern and western galaxy is
1.35, closer to the flux ratio of _L_ CO(5 _−_ 4) (1.39) than the
1.27mm continuum. These differences are small with
respect to the goals of this study so are of not much
concern. Even so, we convert the 3 GHz flux to the
rest-frame luminosity at 1.4 GHz based on a power-law
model with a spectral index _α_ = _−_ 0 _._ 7. Using the radioSFR relation given in Bell (2003) and applying a conversion to a Chabrier IMF, we find SFRs (East: 438 M _⊙_
yr _[−]_ [1] ; West: 323 M _⊙_ yr _[−]_ [1] ) in fairly good agreement with
the estimates given above, including the western galaxy
that may have a weak AGN based on a _Chandra_ Xray detection with very few X-ray counts (Appendix A).
Therefore, we do not find any evidence for the AGN contributing to the radio luminosity.

16 Silverman et al.


+2°10'03.0"


28.10s 28.05s 28.00s 27.95s 27.90s10h02m27.85s


RA (J2000)



28.05s 28.00s 27.95s 27.90s 10h02m27.85s


RA (J2000)



07.0"


06.0"


05.0"


04.0"


03.0"


+2°10'02.0"













**Figure** **14.** Diffuse CO(5-4) emission. (a) ALMA CO(5-4) image generated from the combined low and high resolution data
sets over a velocity interval (667.59 km s _[−]_ [1] ; channels 120 - 185) that encompasses the full extent of the CO line for both galaxies.
The white contours indicate the CO brightness level at 1, 2, 4, 8, 16, 32 _× σ_ _rms_ where _σ_ _rms_ = 4 _._ 67 _×_ 10 _[−]_ [5] Jy beam _[−]_ [1] . (b)
After removing the CO emission from both galaxies (based on a three-component fit - see text for details) with their location
marked by the blue contours, residual emission (i.e., diffuse gas; red contours at 2, 4, 6, 8, 10 _×σ_ _rms_ ) is present with a bright
concentration (i.e., a bridge) between the two nuclei. The diffuse emission supports the scenario that an earlier collision likely
occurred at a smaller physical separation. The underlying HST/WFC3 image, shown in grey with a log scaling, displays stellar
emission between the two galaxies and co-spatial with the diffuse CO emission. (c) Grey scale image of the diffuse component, fit
as a third component, with log scaling, (d) Residual emission after removing all three components (red contours at -2 (dashed),
-1, 1 (solid), 2 _×σ_ _rms_ ). (e) Residual emission after subtracting only two components (both galaxies) based on the two-component
fit. Contours are shown at 2, 3, 4 _× σ_ _rms_ .



massive galaxy, assuming that both galaxies were on the
MS prior to the interaction.
With SFRs and gas masses for each galaxy, we calculate the ratio of these as a star formation efficiency
(SFE; Equation 5) with its inverse usually denoted as a
gas depletion time scale ( _τ_ _depl_ ).



1

_τ_ _depl_ = _[M]_ _[g][as]_ [=]

_SFR_ [;] _[ SFE]_ _τ_ _depl_



(5)



time scale of 85 _±_ 14 (67 _±_ 10) Myrs. Both of these
timescales are shorter than typical MS galaxies at these
SFRs (Figure 13), in agreement with that obtained from
CO(2 - 1) observations of our larger sample of starburst
galaxies (Silverman et al. 2018) with an assumption on
_α_ _CO_ as measured above, and local ULIRGs (Solomon et
al. 1997).


7. DIFFUSE CO EMISSION


We merged the visibilities from the compact and extended ALMA configurations (Band 6), only for this
exercise, to gain sensitivity to extended structure and



For both galaxies, we find short gas depletion time scales
( _<_ 100 Myr). For instance, the Eastern (Western)
galaxy is rapidly depleted its gas reservoir on a mean

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 17



06.0"


05.5"


05.0"


04.5"


04.0"


03.5"


+2°10'03.0"





+2°10'03.0"


28.05s 28.00s 27.95s 27.90s10h02m27.85s


RA (J2000)


**Figure** **15.** Extended continuum emission is present after
removing the contribution from both galaxies using either a
three- (a) or two-component (b) fit for the individual components. Contours levels in red are 3, 5, 7, 9, 11 _×σ_ _rms_ (2,
3, 4, 5 _×σ_ _rms_ ) in panel a (b) where _σ_ _rms_ = 1 _._ 64 _×_ 10 _[−]_ [5] Jy
beam _[−]_ [1] . The HST/WFC3 image is shown in grey. The aqua
blue contours indicate the continuum emission from the in
dividual galaxies at levels given in Figure 6.


better estimate the total flux for our target galaxies.
The combined image (∆v = 667.6 km s _[−]_ [1] ) is shown in
Figure 14 _a_ with overlying contours that give the significance level of the CO emission. A multi-component
fit was performed on the CO(5 - 4) visibility data with
an elliptical Gaussian at the position of each of the two
galaxies. After removing the two components associated
with the galaxies, we found significant residuals with a
5 _σ_ peak, but with substantial extension (hence much
higher significance; Fig. 14 _e_ ), even though each galaxy
may have been over-estimated as shown by the lower
residuals (still positive) under each galaxy indicated by
the blue contours.

With evidence for an extended component, we re-fit
the data allowing for a third Gaussian component and
inspected the residuals after subtracting the two galaxies. This resulted in the very extended signal shown by



the red contours (Fig. 14 _b_ ) and grey scale image (panel
c) with minimal (≲ 2 _σ_ ) residuals after subtracting all
three components (panel d). With a three-component
fit, the significance of the diffuse component is 10 _σ_ based
on the uncertainty of its flux, after marginalizing over
the other parameters. As a result of this exercise, we
claim that the detection of the extended component
of the CO(5-4) emission is robust as further supported
by the existence of an extended component with the
continuum-only visibilities (Figure 15). This extended
component appears to contain _≈_ 20% of the total flux
of the system, both in terms of CO(5 - 4) emission and
continuum. The diffuse gas/dust component is remarkably co-spatial with the stellar emission as seen in the
HST/WFC3 image (Figure 14 _b_ ) with the western component being more extended for both the gas and stars.
The peak emission is located between both galaxies thus
possibly indicative of a bridge connection the two galaxies that may have been tidally stripped during the current or an earlier passage. Furthermore, the strength
and morphology of the diffuse component matches very
well to the simulation shown in the top panel of Fig
ure 10.


8. DISCUSSION AND CONCLUSIONS


With our ALMA observations of PACS-787, we can
address the physical mechanisms or conditions in the
ISM that can produce large enhancements in SFRs since
hydrodynamic simulations (Di Matteo et al. 2007; Fensch et al. 2017) of gas-rich galaxies at high-z generally
tend not to exhibit the extreme levels of enhancement

as seen in PACS-787. This is because the high gas fractions, in isolated galaxies, already induce high levels of
turbulence and the formation of clumps (Bournaud et
al. 2011) hence high levels of SFRs. PACS-787 is likely
an exception that we discovered by selecting, within
our sample, one of the most extreme in SFR above the
MS for its stellar mass. Furthermore, the two starburst
galaxies in PACS-787 are occurring at projected separation of 8.6 kpc. This is unexpected since hydrodynamic
simulations usually have the starburst episodes at close
to final coalescence. Here we discuss the particular characteristics of PACS-787 for which each may contribute
to maximizing the rate of forming stars.


_1._ _High_ _gas_ _content:_ We find large amounts ( _>_ 10 [10]

M _⊙_ ) of molecular gas in each galaxy participating in
the merger. The eastern galaxy actually has a slightly
higher gas mass than stellar mass ( _f_ _gas_ = 70 [+8] _−_ 11 [%)]
while the western galaxy has a higher stellar mass and
lower gas fraction (28 _−_ [+7] 6 [%).] These gas fractions were
likely higher prior to the initial interaction since we find

18 Silverman et al.



_∼_ 20% of the CO emission on larger scales stripped in
the course of the close interaction.


_2._ _Near-equal_ _mass_ _merger:_ The ratio of the masses
(stars + gas) for the two galaxies is 2:1 thus classifying
the system as undergoing a major merger. If only considering their stellar mass, the ratio would be reduced to
4:1. The consideration of not only the stellar mass but
the molecular gas as well is important in assessing the
impact of the merger since hydrodynamical simluations
(e.g., Cox et al. 2008) demonstrate that the boost in
SFR in galaxy mergers is sensitive to the mass ratio.


_3._ _Central_ _gas_ _concentration._ The majority of the
CO-emitting gas is confined to regions within a few kpc.
The eastern and western galaxies have half-light radius
of 0.9 and 1.2 kpc that are similar to local ULIRGs
(Solomon et al. 1997) and continuum observations with
ALMA of high-z submm galaxies (Simpson et al. 2015).


_4._ _High_ _star_ _formation_ _efficiency._ Both galaxies are
highly efficient at forming stars similar to that seen in
local ULIRGs. We find very similar gas depletion times
of _∼_ 70-80 Myrs for the eastern and western galaxies
respectively. These time scales indicate a consumption
of their molecular gas much shorter than typical MS
galaxies at an equivalent SFR (Figure 13).


_5._ _Orbital_ _configuration:_ Even with limited information on the orbital dynamics of the system, we estimate the amount of angular momentum, expressed as
_L_ = _m_ _gas_ _×_ _r_ 1 _/_ 2 _×_ _v_, that may be canceled in the merger
using our measurements in hand for each galaxy: size
( _r_ 1 _/_ 2 ), inclination ( _i_ ), velocity ( _v_ = _v_ _F W HM_ _/_ (2 _×sin i_ )),
and gas mass ( _m_ _gas_ ). In all four possible orientations
for the two disks (counter-rotating vs co-rotating; inclination being positive or negative with respect to the
plane of the sky), the component of the total angular
momentum in the plane of the sky for each individual
galaxy will be opposite to each other. We note that
in the co-rotating case, the disks are essentially perpendicular to each other hence there is no distinction
from co- or counter-rotation. We find that the difference
in angular momentum for the two components (in the



plane of the sky) will be _∼_ 37% of the sum of the angular momentum of both galaxies. This is a considerable
amount of angular momentum that may be lost and
possibly relevant in explaining the high star formation
rates. For this exercise, we neglect to consider the total
angular momentum of the system.
We highlight that these results are derived from a procedure to assess the amount of molecular gas independent of the CO luminosity. The high signal-to-noise detection of CO(5-4) for each galaxy and the survival of the
their kinematic structure as a disk at this stage of the
merger allow us to carry out such an analysis. Whether
this situation is fortuitous or prevalent throughout the
high-z starburst population is yet to be determined. Additional examples are obviously needed given their impact on the use of CO as a tracer of the molecular gas
mass at high redshift. We refer the reader to the discussion in Silverman et al. (2018) on the impact of uncertainties on _α_ _CO_ in measuring the molecular gas content
for high-z starburst galaxies.
To conclude, the observations presented here of a
quintessential starburst induced by the pre-merging interaction of two galaxies at high redshift demonstrate
the remarkable capability of ALMA to study such systems in detail. In particular, the molecular gas and dust
properties are measured for both galaxies at a stage in
the merger prior to final coalescence. As indicative of the
interaction, we detect diffuse CO emission, likely tidallystripped, for the first time at high redshift ( _z_ ≳ 1). With
sufficient spatial and spectral resolution, we were able to
model the kinematics of the system to derive a dynamical mass and account of the mass contribution from the

stellar and gas mass with an assumption on the amount
of dark matter present. For the first time, we use simulations of galaxy mergers to calibrate the estimate of
the dynamical mass which indicate that other attempts
may be off by a factor _∼_ 2. As described above, this
led to constraints on two key parameters ( _α_ _CO_ and the
G/D ratio) that are poorly established at high redshift.
Finally, we expect that future ALMA observations of
PACS-787 at a higher spatial resolution will unveil the
structure of the gas and its velocity structure on scales
( _∼_ 100 pc) of giant molecular cloud complexes



REFERENCES



Barro, G. Kriek, M., Perez-Gonzalez et al. 2017, ApJ, 851,

40

Bell, E. 2003, ApJ, 586, 794

Bolatto, A. D., Wolfire, M., Leroy, A. K. 2013, ARA&A,

51, 207



Bolzonella, M., Miralles, J. -M., Pello, R. 2000, A&A, 363


476


Bothwell, M.S., Smail, I., Chapman, S.C. et al. 2013,


MNRAS, 429, 3047

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 19


**Table** **2.** PACS-787: Properties of individual components


Quantity East West Units Method


RA 10:02:27.995 ( _δ_ = 0 _._ 004 _[′′]_ ) 10:02:27.927( _δ_ = 0 _._ 006 _[′′]_ ) Centroid of the continuum emission


DEC +02:10:04.56 +02:10:04.61


z _CO_ 1.5256 1.5240 Redshift; _δ_ _z_ = 0 _._ 0001


M _stellar_ 1 _._ 9 _−_ [+0] 0 _[.]_ _._ [8] 4 _[×]_ [ 10] [10] 8 _._ 1 [+1] _−_ 1 _[.]_ _._ [9] 7 _[×]_ [ 10] [10] M _⊙_ Chabrier IMF


I _CO_ (5 _−_ 4) 2.82 _±_ 0 _._ 08 2.03 _±_ 0.10 Jy km s _[−]_ [1]

∆v 748.7 338.4 km s _[−]_ [1] Velocity range over which I _CO_ (5 _−_ 4) is measured.

L _[′]_ CO(5 _−_ 4) 1 _._ 3 _×_ 10 [10] 9 _._ 5 _×_ 10 [9] K km s _[−]_ [1] pc [2]

_v_ _F W HM_ 688 _._ 4 _±_ 88 _._ 8 271 _._ 7 _±_ 82 _._ 0 km s _[−]_ [1] CO velocity width at half maximum from Gaussian fit


_r_ 1 _/_ 2 0 _._ 90 _±_ 0 _._ 05 1 _._ 19 _±_ 0 _._ 04 kpc CO; half-light radius

_i_ 55 [+5] _−_ 6 38 [+7] _−_ 10 degrees Disk inclination (CO)


f 1 _._ 3 mm 0.75 _±_ 0.03 0.68 _±_ 0 _._ 04 mJy


f 3 _GHz_ 70.4 _±_ 4.0 52.0 _±_ 3.9 _µ_ Jy


SFR 515 _±_ 56 476 _±_ 47 M _⊙_ yr _[−]_ [1]


_M_ _gas_ 4 _._ 4 _±_ 0 _._ 6 _×_ 10 [10] 3 _._ 2 _±_ 0 _._ 4 _×_ 10 [10] M _⊙_


_f_ _gas_ 70 [+8] _−_ 11 28 [+7] _−_ 6 %


_τ_ _depl_ 85 _±_ 14 67 _±_ 10 Myr



Bournaud, F., Chapon, D., Teyssier, R. et al. 2011, ApJ,

730, 4


Bournaud, F., Daddi, E., Elbaz, D. et al. 2015, A&A, 575,

56


Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000


Carilli, C. L., Walter, F. 2013, ARA&A, 51, 105


Casey, C. M., Chapman, S. C., Neri, R. et al. 2011,

MNRAS, 415, 2723


Chen, C., Hodge, J., Smail, I. et al. 2017, ApJ, 846, 2


Cibinel, A., Daddi, E., Bournaud, F. et al. 2017, MNRAS,

469, 4683


Civano, F., Marchesi, S., Comastri, A. et al. 2016, ApJ,

819, 62


Combes, F., Garc´ıa-Burillo, S., Braine, J., Shinnerer, E.,

Walter, F. Colina, L. 2013, ˚a, 550, A41


Cox, T. J., Jonsson, P., Somerville, R., Primack, J. R.,

Dekel, A. 2008, MNRAS, 384, 386


Daddi, E., Dickinson, M., Morrison. G. et al. 2007, ApJ,

670,156


Daddi, E., Bournaud, F., Walter, F. et al. 2010a, ApJ, 713,

686


Daddi, E., Elbaz, D., Walter, F. et al. 2010b, ApJ, 714,

L118


Daddi, E., Dannerbauer, H., Liu, D. et al. 2015, ˚a, 577, A46



De Blok, W. J. G., Walter, F., Brinks, E. et al. 2008, AJ,

136, 2648

Di Matteo, T., Springel, V., Hernquist, L. 2005, Nature,

433, 7026

Di Matteo, P., Combes, F., Melchior, A. -L. 2007, A&A,

468, 1

Di Matteo, P., Bournaud, F., Matig, M. et al. 2008,A&A,

492, 31

Downes, D., Solomon, P. M. 1998, ApJ, 507, 615

Draine, B. T., Li, A. 2007, ApJ.. 657, 810

Ellison, S. L., Mendel, J. T., Scudder, J. M., Patton, D. R.,

Palmer, M. J. D. 2013, MNRAS, 430, 3128

Engel, H., Tacconi, L. J., Davies, R. I. et al. 2010, ApJ,

724, 233

Fensch, J., Renaud, F., Bournaud, F. et al. 2017, MNRAS,

465, 1934

Geach, J. E., Smail, I., Moran, S. M., et al. 2011, ApJ, 730,

L19

Genzel, R., Tacconi, L. J., Rigopoulou, D., Lutz, D., Tecza,

M. 2001, ApJ, 563, 527

Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010,

MNRAS, 407, 2091

Genzel, R., Tacconi, L., Lutz, D. et al. 2015, ApJ, 800, 20
Genzel, R., Schreiber, N. M. F¨orster, Ubler, [¨] H. et al. 2017,

Nature, 543, 397

20 Silverman et al.



Greve, T. R., Bertoldi, F., Smail, I. et al. 2005, MNRAS,

359, 1165

Hayward, C. H., Behroozi, P., Somerville, R. et al. 2013,

MNRAS, 434, 3

Hodge, J. A., Swinbank, A. M., Simpson, J. M. et al. 2016,

ApJ, 833, 103

Hopkins, P., Hernquist, L., Cox, T. et al. 2006, ApJS, 163, 1

Hopkins, P. F., Cox, T. J., Hernquist, L. et al. 2013,

MNRAS, 430, 1901

Ilbert, O., Arnouts, S., Le Floc’h et al. 2015, A&A, 579, 2

Ivison, R. J., Dunlop, J. S., Hughes, D. H. et al. 1998,

MNRAS, 494, 211

Ivison, R. J., Magnelli, B., Ibar et al. 2010, A&A, 518, 31

Ivison, R. J., Papadopoulos, P. P, Smail, I. et al. 2011,

MNRAS, 412, 1913

Kashino, D., Silverman, J. D., Rodighiero, G. et al. 2013,

ApJL, 777, 8

Kashino, D., Silverman, J. D., Sanders, D. B. et al. 2017,

ApJ, 835, 88

Kennicutt, R. C. 1998, ARA&A, 36, 189

Kennicutt, R. C. Jr., Evans, N. J. 2012, ARA&A, 50, 531

Koekemoer, A., Aussel, H., Calzetti, D. et al. 2007, ApJS,

172, 196

Kormendy, J., Sanders, D. B.1992, ApJ, 390, 53

Lackner, C., Silverman, J., Salvato, M. et al. 2014, ApJ,

148, 137

Laigle, C., McCracken, H. J., Ilbert, O. et al. 2016, ApJS,

224, 24

Lilly, S. J., Eales, S. A., Gear, W. K. P. et al. 1999, ApJ,

518, 641

Leroy, A., Bolatto, A., Gordon, K. et al. 2011, ApJ, 737, 12

Leroy, A. K., Walter, F., Sandstrom, K. et al. 2013, AJ,

146, 19

Lotz, J., Davis, M., Faber, S. M. et al. 2008, ApJ, 672, 177

Lutz, D., Poglitsch, A., Altieri, B. et al. 2011, ˚a, 532, 90

Puglisi, A., Daddi, E., Renzini, A. et al. 2017, ApJL, 838,

18

Magdis, G., Daddi, E.,, Elbaz, D. et al. 2011, ApJ, 740, 15

Magdis, G. E., Daddi, E., B´ethermin, M. et al. 2012a, ApJ,

760, 6

Magdis, G. E., Daddi, E., Sargent, M. et al. 2012b, ApJL,

758, L9

Magdis, G. E., Rigopoulou, D., Daddi, E. et al. 2017, ˚a,

603, A93

Magnelli, B., Lutz, D., Santini, P. et al. 2012, A&A, 539,

A155

Marchesi, S., Civano, F., Elvis, M. et al. 2016, ApJ, 817, 34

McCracken, H. J., Milvang-Jenson, B., Dunlop, J. et al.

2012, ˚a, 544, 156



Narayanan, D., Krumholz, M., Ostiker, E. C., Hernquist, L.

2011, MNRAS, 418, 664

Neri, R., Genzel, R., Ivison, R. et al. 2001, ApJ, 597, L113

Papadopoulos, P. P., Van Der Werf, P. Xilouros, E., Isaak,

K. G., Gao, Y. 2012, ApJ, 751, 10

Peng, C. Y., Ho, L., Impey, C., Rix, H. W. 2010, AJ, 139,

2097

Pettini, M. & Pagel, B. E. J. 2004, MNRAS, 348, L59

Pozzetti, L., Bolzonella, M., Lamareille, F. et al. 2007,

A&A, 474, 443

Puglisi, A., Daddi, E., Renzini, A. et al. 2017, ApJL, 838,

18

Renzini, A. & Peng, Y. 2015, ApJ, 801, 29

Riechers, D. A., Leung, T. K., Ivison, R. J. et al. 2017,

ApJ, 850, 1

Rodighiero, G., Daddi, E., Baronchelli, I. et al. 2011, ApJ,

739, L40

Rujopakarn, W., Dunlop, J. S., Rieke, G. H. et al. 2016,

ApJ, 833, 12

Saintonge, A., Kauffmann, G., Kramer, C., et al. 2011,

MNRAS, 415, 32

Saintonge, A., Tacconi, L., Fabello, S. et al. 2012, ApJ, 758,

73

Sanders, D. B., Scoville, N. Z., Young, J. S. et al. 1986,

ApJ, 305, 45

Sanders, D. B. & Mirabel, I. F. 1996, ARA&A, 34, 749

Sanders, D. B., Salvato, M., Aussel, H. et al. 2007, ApJS,

172, 86

Sargent, M. T., Daddi, E., B´ethermin, M. et al. 2014, ApJ,

793, 19

Schinnerer, E., Smolcic, V., Carilli, C. et al. 2007, ApJS,

1742, 46

Scoville, N. Z., Sanders, D. B., Sargent, A. I., Sifer, B. T.,

Tinney, C. G. 1989, ApJ, 345, 25

Scoville, N., Abraham, R. G., Aussel, H. et al. 2007, ApJS,

172, 38

Scoville, N., Sheth, K., Aussel, H. et al. 2016, ApJ, 824, 63

Scudder, J. M., Ellison, S. L., Torrey, P., Patton, D. R.,

Mendel, J. T. 2012, MNRAS, 426, 549

Semenov, V. A., Kravtsov, A. V., Gnedin, N. Y. 2017, ApJ,

845, 133

Simpson, J. M., Smail, I., Swinbank, A. M. et al 2015, ApJ,

799, 81

Silverman, J. D., Daddi, E., Rodighiero, G. et al. 2015,

ApJ, 812, L23

Silverman, J.D., Kashino, D., Sanders, D.B. et al. 2015,

ApJS, 220, 12

Silverman, J. D., Rujopakarn, W., Daddi, E. et al. 2018,

ApJ in press

Smolˇci´c, V., Novak, M., Bondi, M. et al. 2017, A&A, 602, 1

Molecular gas in colliding galaxies at _z_ = 1 _._ 52 21



Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett,


J. W. 1997, ApJ, 478, 144


Speagle, J. S., Steinardt, C. L., Capak, P. L., Silverman,


J.D. 2014,ApJS, 214, 15


Spilker, J. S., Aravena, M., Marrone, D. P. et al. 2015, ApJ,


811, 124


Swinbank, A. M., Smail, I., Longmore, S. et al. 2010,


Nature, 464, 733


Tacconi, L. J., Neri, R. Chapman, S. C. et al. 2006, ApJ,


640, 228


Tacconi, L., Genzel, R., Smail, I. et al. 2008, ApJ, 680, 246


Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74



Tacconi, L.J., Genzel, R., Saintinge, A. et al. 2018, ApJ,

853, 179

Tadaki, K., Kodama, T., Nelson, E. J. et al. 2017, ApJ,

841, 25

Tanaka, M. Hasinger, G., Silverman, J. et al. 2017,

arXiv:1706.00566

Tan, Q., Daddi, E., Magdis, G. et al. 2014, A&A, 569, A98

Toft, S., Smolcic, V., Karim, A. et al. 2014, ApJ, 782, 2

Volonteri, M., Capelo, P.R., Netzer, H., J. Bellovary, M.

Dotti, F. Governato 2015, MNRAS, 449, 1470

Walter, F., Brinks, E., de Blok, W. J. G. et al. 2008, AJ,

136, 2563

Wilson, C. D., Petitpas, G. R., Iono, D. et al. 2008, ApJS,

178, 189

22 Silverman et al.


**Figure** **16.** Marginal evidence for an accreting supermassive black hole in PACS-787. (Left) Gaussian smoothed (2 pixels)
_Chandra_ X-ray image (2-7 keV). The blue spots (at the center of the image) indicate the location of the two components of
PACS-787. A faint X-ray source may be close to the position of PACS-787. (Right) Subaru/FMOS near-infrared spectrum of
the western galaxy (with the aperture location shown in the bottom right panel of Fig. 1). Grey hatched regions mark those
wavelengths impacted by OH emission. The red curve is a best-fit Gaussian model to the H _α_ and [NII] emission lines.


APPENDIX


A. AGN


PACS-787 may be the host to an Active Galactic Nucleus (AGN), powered by a supermassive black hole. There is
very weak hard (2-7 keV) emission detected by _Chandra_ (Figure 16; left panel). This source was not found in previous
X-ray analysis (Civano et al. 2016) of the COSMOS field, possibly hampered by having only 4 X-ray counts in the 2-7
keV band and at a distance of 11 _[′′]_ to a bright X-ray source to the southeast that has a photometric redshift of 1.27
(Marchesi et al. 2016). Attributing all the X-ray counts within an aperture of 8 _[′′]_ to PACS-787, the AGN would have
_L_ _X_ _∼_ 2 _×_ 10 [43] ergs s _[−]_ [1] that may be responsible for the high ionization state of the interstellar medium as indicated
by the ratio [NII]/H _α_ = 0 _._ 54 _±_ 0 _._ 04 (right panel). Although, we cannot rule out the possibility that PACS-787 has a
high metallicity as opposed to an underlying AGN as the source of photoionization. Whether the X-ray detection is
real or not, there is no impact on the analysis used in this study that would alter our conclusions.


We are grateful for the support from the regional ALMA ARCs. JDS was supported by the ALMA Japan Research
Grant of NAOJ Chile Observatory, NAOJ-ALMA-0127, JSPS KAKENHI Grant Number *JP18H01521*, and the
World Premier International Research Center Initiative (WPI Initiative), MEXT, Japan. CM and AR acknowledge
support from an INAF PRIN 2012 grant. W.R. is supported by Thailand Research Fund/Office of the Higher Education Commission Grant Number MRG6080294 and Chulalongkorn University’s CUniverse. GEM acknowledges
support from the Carlsberg Foundation, the ERC Consolidator Grant funding scheme (project ConTExt, grant
num- ber No. 648179), and a research grant (13160) from Villum Fonden. N.A. is supported by the Brain Pool
Program, which is funded by the Ministry of Science and ICT through the National Research Foundation of Korea (2018H1D3A2000902). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00952.S,
ADS/JAO.ALMA#2015.1.00861.S and ADS/JAO.ALMA#2016.1.01426.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and
KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ.


</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "Stellar mass method as in COSMOS catalog",
  "failed_quote": "are used to measure the stellar mass as done in Laigle et al. (2016)."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Thin-disk Mdyn (Neri 2001) with fc and inclination from axis ratio; 10k realizations; Mgas = 2[Mdyn - Mdm] - Mstellar; alpha_CO=Mgas/L'CO(1-0)",
  "failed_quote": "generating 10k realizations that incorporate all sources of uncertainty while assuming Gaussian distributions for each parameter"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Median dynamical mass (sum) = 1.1e11 Msun",
  "failed_quote": "M dyn ( r < r 1/2 ) = 1.1 [+0] −0 . [6] 4 × 10 [11] M ⊙"
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "Monte Carlo, Gaussian errors",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[6].fitting.evidence[0]",
  "value": "2- and 3-component Gaussian fits",
  "failed_quote": "(no quote given)"
 }
]
```
