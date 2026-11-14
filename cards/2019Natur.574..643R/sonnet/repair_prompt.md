# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019Natur.574..643R\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## **A 100-kiloparsec galactic wind feeding the circumgalactic** **medium of a massive compact galaxy**

David S. N. Rupke [1], Alison Coil [2], James E. Geach [3], Christy Tremonti [4], Aleksandar M. Diamond

Stanic [5], Erin R. George [2], Ryan C. Hickox [6], Amanda A. Kepley [7], Gene Leung [2], John Moustakas [8],


Gregory Rudnick [9], Paul H. Sell [4] _[,]_ [10] _[,]_ [11]


1 _Department of Physics, Rhodes College, Memphis, TN, USA; drupke@gmail.com_


2 _Center_ _for_ _Astrophysics_ _&_ _Space_ _Sciences,_ _University_ _of_ _California,_ _San_ _Diego,_ _La_ _Jolla,_ _CA,_


_USA_


3 _Centre for Astrophysics Research, School of Physics, Astronomy & Mathematics, University of_


_Hertfordshire, Hatfield, UK_


4 _Department of Astronomy, University of Wisconsin-Madison, Madison, WI, USA_


5 _Department of Physics and Astronomy, Bates College, Lewiston, ME, USA_


6 _Department of Physics and Astronomy, Dartmouth College, Hanover, NH, USA_


7 _National Radio Astronomy Observatory, Charlottesville, VA, USA_


8 _Department of Physics and Astronomy, Siena College, Loudonville, NY, USA_


9 _Department of Physics and Astronomy, University of Kansas, Lawrence, KS, USA_


10 _Department of Astronomy, University of Florida, Gainesville, FL, USA_


11 _University of Crete, Heraklion, Crete, Greece_


**Ninety per cent of baryons are located outside galaxies, either in the circumgalactic or inter-**


**galactic medium** **[1,2]** **. Theory points to galactic winds as the primary source of the enriched and**


1

**massive circumgalactic medium** **[3–6]** **.** **Winds from compact starbursts have been observed to**


**flow to distances somewhat greater than ten kiloparsecs** **[7–10]** **, but the circumgalactic medium**


**typically extends beyond a hundred kiloparsecs** **[3,4]** **.** **Here we report optical integral field ob-**


**servations of the massive but compact galaxy SDSS J211824.06** + **001729.4. The oxygen [O II]**


**lines** **at** **wavelengths** **of** **3726** **and** **3729** **angstroms** **reveal** **an** **ionized** **outflow** **spanning** **80** **by**


**100 square kiloparsecs, depositing metal-enriched gas at 10,000 kelvin through an hourglass-**


**shaped nebula that resembles an evacuated and limb-brightened bipolar bubble.** **We also ob-**


**serve neutral gas phases at temperatures of less than 10,000 kelvin reaching distances of 20**


**kiloparsecs and velocities of around 1,500 kilometres per second.** **This multi-phase outflow is**


**probably driven by bursts of star formation, consistent with theory** **[11,12]** **.**


The galaxy J211824.06+001729.4 that we study here, which we call Makani (Hawai’ian for


‘wind’), is an example of a merger of two galaxies hosting a galactic wind thought to be powered by


extreme star-formation surface density [13] . At redshift _z_ = 0 _._ 459, Makani is a compact but massive


galaxy, with log( _M_ _⋆_ _/M_ _⊙_ ) = 11 _._ 1( _±_ 0 _._ 2), where _M_ _⋆_ and _M_ _⊙_ are the stellar and solar masses,


respectively (Extended Data Fig. 4). Our Hubble Space Telescope imaging analysis reveals a


highly peaked stellar core (radius 400 pc) framed by two tidal tails of 10–15 kpc so that half of the


galaxy’s light extends to about 2.5 kpc (ref. [14] ; Fig. 1). Its stellar populations include old (more


than a billion years, Gyr), medium-aged (0.4 Gyr), and young ( _<_ 7 million years, Myr) components


(Extended Data Fig. 5), with a current star-formation rate of 100–200M _⊙_ yr _[−]_ [1] . It may contain a


dust-obscured accreting supermassive black hole, or active galactic nucleus (AGN), on the basis


of its X-ray luminosity of log _L_ (2 _−_ 10 keV) = 42 _._ 5 [+0] _−_ 0 _._ _[.]_ 6 [4] [erg s] _[−]_ [1] [(ref.] [14] [),] [its] [mid-infrared] [slope,]


2

and the presence of highly ionized gas like [Ne V] at wavelength _λ_ = 3426 A [˚] (log _L_ = 40 _._ 6 [+0] _−_ 0 _[.]_ _._ [1] 2


erg s _[−]_ [1] ). However, any AGN is not currently energetically dominant [13,14] or radio-loud (G. C.


Petter et al., manuscript in preparation) and the data could be explained by star formation and


shocks. Extremely high-density star formation, like that found in Makani, is capable of powering


fast winds, independent of an AGN [13] .


To study the spatial extent of its outflow, we observed Makani with the Keck Cosmic Web


Imager (KCWI) [15] . The emission from the [O II] lines at _λ_ = 3726 A [˚] and 3729 A [˚] in these data


reveals a nebula with approximate mirror symmetry around the north-south and east-west axes,


extending to radii of 50 kpc north and south of the galaxy nucleus, and 40 kpc east and west (Fig.


1). Its morphology resembles that of a limb-brightened, bipolar bubble, similar to those seen in


other galactic winds [16,17] but on a much larger scale. This nebula is remarkable in the context


of other [O II] emitters. Its area of 4,900 kpc [2] (136 arcsec [2] above a 5 _σ_ surface brightness limit


per spaxel (spectral pixel) of 5 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] arcsec _[−]_ [2] ) makes it the largest [O II] nebula


detected around a single galaxy in the field [18,19] or in galaxy groups [20,21] . Its [O II] luminosity of


3.3 _×_ 10 [42] erg s _[−]_ [1] is several times the break in the galaxy luminosity function, _L_ _∗_, at _z_ _≈_ 0 _._ 45 (ref.


22 ). Its rest-frame equivalent width (40 ˚A), half-light radius (17 kpc), and maximum radial extent


(50 kpc) put it at the top end of [O II] emitters at _z_ _≤_ 0 _._ 6 and radio galaxy nebulae [18,23], perhaps


indicative of the unusual nature of this nebula as a giant galactic wind.


Based on its light distribution alone, the hourglass shape of the nebula strongly suggests a


bipolar galactic wind emerging from its host galaxy. The spatially-resolved gas kinematics confirm


3

this impression and separate the wind cleanly into an outer region with low-velocity gas only and


an inner region containing both low- and high-velocity gas (Fig. 2). The outer region with lower


velocities spans radii 20–50 kpc, while the high-velocity gas is concentrated within a radius of


about 10 kpc. We call these two wind components, and the associated starbursts that are thought to


have produced them, episodes I (0.4 Gyr ago) and II (7 Myr ago). We sort spaxels by the average


maximum blueshifted velocity of _⟨v_ 98% _⟩_ = _−_ 700 km s _[−]_ [1], though sorting by velocity dispersion


_σ_ produces similar results. Episode I then has gas with maximum blueshifted velocities between


_−_ 100 and _−_ 700 km s _[−]_ [1] while episode II has a high-velocity tail of gas to _v_ 98% = _−_ 2 _,_ 100 km s _[−]_ [1] .


Timescale arguments further support the existence of two starburst-driven wind episodes. In the


0.4 Gyr since the episode I starburst, a constant-velocity wind must have travelled at 120 km s _[−]_ [1]


to reach the edge of the nebula (50 kpc); representative velocities at the nebula outskirts are in fact


100–200 km s _[−]_ [1] . In the 7 Myr since the most recent starburst episode began, the speed required to


reach the edge of the bulk of the episode II wind (10 kpc) is 1,400 km s _[−]_ [1], which is also a typical


maximum velocity in the inner nebula. The lack of high-velocity redshifted gas in episode II may


be due to dust in the outflow blocking the far side of the wind, while the lack of high-velocity gas


in the episode I wind is probably due to the dispersal of high-velocity gas to radii exceeding 50 kpc


over 0.4 Gyr or the deceleration of the outflow as predicted by models [11] . Episode I gas also forms


the telltale hourglass shape and has higher typical velocity dispersions (200 km s _[−]_ [1] ) than expected


for tidal features or gravitational motions at large radii [24] .


We find two other gas phases that we associate with the episode II (recent, inner) outflow.


Using the Atacama Large Millimeter Array (ALMA), we detect molecular gas traced by CO(2–


4

1) emission that is outflowing in a compact form, both blueshifted at -500 to -1,500 km s _[−]_ [1] and


redshifted at 500–1,500 km s _[−]_ [1], from the nucleus 10 kpc northward (Fig. 3d). This gas is clearly


part of episode II, given its high velocity and compact scale. Lower-velocity molecular gas, at


_|v|_ _<_ 500 km s _[−]_ [1] and radius _r_ _<_ 20 kpc (Fig. 3c), is also likely to be part of the outflow because


it is much more extended than the stellar disk and correlates spatially with extended, outflowing


ionized gas. It may be gas from episode II that has decelerated after reaching scales of the order


of 10 kpc. Using resonant line emission from Mg II at _λ_ = 2796 A [˚] and 2803 A, [˚] we also detect


neutral gas of temperature _T_ _≈_ 10 [4] K in the velocity range _±_ 500 km s _[−]_ [1] (Fig. 3b). This emission


correlates with some regions of faint, extended CO and [O II] emission. Although these velocities


are modest, resonant emission on 10-kpc scales has so far been detected only in galactic winds, and


because of strong radiation transfer effects such emission is not highly shifted from the redshift of


the Makani galaxy’s centre of mass [25,26] . Blueshifted Fe II absorption is detected in the nuclear


spectrum (Extended Data Fig. 2), but tracing its physical extent requires deeper observations.


Estimates of the mass contained within the wind would complete its portrait. However, the


mass of the ionized gas is uncertain without spatially resolved recombination line measurements.


Bootstrapping from single-aperture H _α_ and H _β_ measurements, we estimate 6( _−_ [+6] 3 [)] _[×]_ [10] [8] [(200 cm] _[−]_ [3] _[/]_ [n] [e] [)] _[M]_ _[⊙]_


of ionized gas in the nebula, with unquantified systematic errors (electron density _n_ _e_ and ioniza

tion state) likely exceeding the measurement error. Although it is confined to the inner 10 kpc, the


mass of the molecular gas in the _|v|_ = 500–1500 km s _[−]_ [1] flow (that is, episode II) is substantial


(2 _._ 4 [+0] _−_ 0 _[.]_ _._ [6] 6 _[×]_ [ 10] [9] _[M]_ _[⊙]_ [), with four times as much in the more extended] _[ ±]_ [500 km s] _[−]_ [1] [component.] [The]


ionized gas plus molecular wind thus contains 1–10% of the galaxy’s baryonic mass, a fraction


5

that will be even larger when all phases are accounted for. The resulting mass flow rate for the


molecular episode II component is _dM/dt_ _≈_ _Mv/r_ = 245M _⊙_ yr _[−]_ [1] for _v_ = 1 _,_ 000 km s _[−]_ [1] and


_r_ = 10 kpc, which is roughly one to two times the star-formation rate. This is consistent with


molecular outflow rates [7,10] from other compact starburst mergers at _z_ _>_ 0 _._ 5.


The huge, metal-enriched outflows in Makani – a key component of the host galaxy’s dynam

ically and chemically evolving circumgalactic medium (CGM) – are consistent with the types of


star-formation or AGN-driven winds that populate and enrich the CGM in theoretical models [11,12] .


A model galaxy forming stars at 100M _⊙_ yr _[−]_ [1] in a baryonic halo of 2 _×_ 10 [11] _M_ _⊙_ and supernova

driven winds propelling gas with initial velocity 1,000 km s _[−]_ [1] produce a 10 [9] _M_ _⊙_ (or 10 [10] _M_ _⊙_ ) shell


at _r_ _≈_ 10 kpc (or 100 kpc) in _t_ _≈_ 10 Myr (or 400 Myr), with velocities at this time of order


1,000 km s _[−]_ [1] (100 km s _[−]_ [1] ) [11] . These numbers bear a striking resemblance to the observations in the


context of the two-episode outflow we propose. The wind will continue to expand, diffuse, and


virialize over longer timescales, as this nebula is denser and more structured than virialized CGM


gas [4,12] and has reached perhaps only about 10% of the virial radius [27] of a log( _M_ _⋆_ _/M_ _⊙_ ) = 11 _._ 1


galaxy at _z_ = 0 _._ 46.


The size of this wind makes it the one of the largest wide-angle, galaxy-scale outflows yet


observed, with scales much larger than in other compact or high- _z_ starbursts [7,9,10] . The morphol

ogy and velocity of the wind in the Teacup AGN make it a cousin of Makani, but on scales five


to ten times smaller [17] . Though the Teacup also hosts diffuse gas over 100 kpc scales, this gas has


a different physical origin than does the gas in Makani [28] . The most comparable system may be a


6

merger with compact star formation at a cosmic distance ten times closer than Makani. NGC 6240


( _z_ = 0 _._ 04) has an ionized outflow that reaches a 40-kpc radius [8] . However, the outflow size rel

ative to the stellar half-light radius (inside which half of the galaxy’s starlight resides) is only


_r/r_ _∗,_ 1 _/_ 2 _≈_ 4 in NGC 6240 (ref. [29] ), versus _r/r_ _∗,_ 1 _/_ 2 _>_ 20 in Makani, and much of the NGC 6240


nebula coincides with stellar tidal features, unlike Makani. Furthermore, the H _α_ luminosity of the


NGC 6240 nebula is four times smaller than in Makani if the core H _α_ emission follows the oxygen


emission at a constant [O II]/H _α_ line ratio.


With a maximum extent of more than twenty times the stellar half-light radius, the oxygen


nebula observed here has propagated well into the galaxy halo, placing it solidly in the CGM. The


cool gas and metals in the flow are thus contributing to the buildup and enrichment of the CGM.


This cool gas can be propelled by hot gas, radiation pressure or cosmic rays. The classic model


of hot gas acceleration faces the problem that cold clouds may be destroyed during acceleration.


These clouds may simply reform after being shredded and mixed in the hot wind [30] or the clouds


may survive the acceleration through fast radiative cooling [31] . The mixing layers in shredded clouds


can also cool hot gas from the halo or CGM, enhancing the amount of cool gas injected into the


CGM [31] . If the cool outflow is accelerated by a hot wind, the existence of [O II]-emitting gas at


all radii argues for either cloud reformation on very short timescales or for cloud survival (coupled


with enhancement from hot gas). The outflow we observe is thus feeding the CGM by directly


depositing gas from the galaxy or by entraining and cooling hot halo and circumgalactic gas.


Connecting the CGM with ongoing galactic winds has been challenging because of the lack


7

of clear evidence for such winds on large enough scales. Previous evidence came from theory [5,6]


and the statistical characteristics of the CGM as measured from single quasar absorption lines


over large galaxy populations [3,4] . We have now observed a single galaxy, with all lines of sight


accounted for, whose wind has entered the CGM. Our measurement provides one of the first direct


windows into the dynamically and chemically evolving, multiphase CGM being created around a


massive galaxy.


**References**


1. Shull, J. M., Smith, B. D. & Danforth, C. W. The Baryon Census in a Multiphase Intergalactic


Medium: 30% of the Baryons May Still be Missing. _Astrophys. J._ **759**, 23 (2012).


2. Tumlinson, J., Peeples, M. S. & Werk, J. K. The Circumgalactic Medium. _Ann. Rev. Astron._


_Astrophys._ **55**, 389–432 (2017).


3. Tumlinson, J. _et_ _al._ The Large, Oxygen-Rich Halos of Star-Forming Galaxies Are a Major


Reservoir of Galactic Metals. _Science_ **334**, 948–952 (2011).


4. Werk, J. K. _et_ _al._ The COS-Halos Survey: Physical Conditions and Baryonic Mass in the


Low-redshift Circumgalactic Medium. _Astrophys. J._ **792**, 8 (2014).


5. Hummels, C. B., Bryan, G. L., Smith, B. D. & Turk, M. J. Constraints on hydrodynamical


subgrid models from quasar absorption line studies of the simulated circumgalactic medium.


_Mon. Not. R. Astron. Soc._ **430**, 1548–1565 (2013).


8

6. Ford, A. B. _et al._ Hydrogen and metal line absorption around low-redshift galaxies in cosmo

logical hydrodynamic simulations. _Mon. Not. R. Astron. Soc._ **432**, 89–112 (2013).


7. Geach, J. E. _et al._ Stellar feedback as the origin of an extended molecular outflow in a starburst


galaxy. _Nature_ **516**, 68–70 (2014).


8. Yoshida, M. _et al._ Giant H _α_ Nebula Surrounding the Starburst Merger NGC 6240. _Astrophys._


_J._ **820**, 48 (2016).


9. Falgarone, E. _et_ _al._ Large turbulent reservoirs of cold molecular gas around high-redshift


starburst galaxies. _Nature_ **548**, 430–433 (2017).


10. Geach, J. E. _et al._ Violent Quenching: Molecular Gas Blown to 1000 km s _[−]_ [1] during a Major


Merger. _Astrophys. J._ **864**, L1 (2018).


11. Lochhaas, C., Thompson, T. A., Quataert, E. & Weinberg, D. H. Fast winds drive slow shells:


a model for the circumgalactic medium as galactic wind-driven bubbles. _Mon. Not. R. Astron._


_Soc._ **481**, 1873–1896 (2018).


12. Hani, M. H., Sparre, M., Ellison, S. L., Torrey, P. & Vogelsberger, M. Galaxy mergers mould

ing the circum-galactic medium - I. The impact of a major merger. _Mon. Not. R. Astron. Soc._


**475**, 1160–1176 (2018).


13. Diamond-Stanic, A. M. _et_ _al._ High-velocity Outflows without AGN Feedback: Eddington

limited Star Formation in Compact Massive Galaxies. _Astrophys. J._ **755**, L26 (2012).


9

14. Sell, P. H. _et al._ Massive compact galaxies with high-velocity outflows: morphological analy

sis and constraints on AGN activity. _Mon. Not. R. Astron. Soc._ **441**, 3417–3443 (2014).


15. Morrissey, P. _et al._ The Keck Cosmic Web Imager Integral Field Spectrograph. _Astrophys. J._


**864**, 93 (2018).


16. Shopbell, P. L. & Bland-Hawthorn, J. The Asymmetric Wind in M82. _Astrophys._ _J._ **493**,


129–153 (1998).


17. Harrison, C. M. _et_ _al._ Storm in a “Teacup”: A Radio-quiet Quasar with _≈_ 10 kpc Radio

emitting Bubbles and Extreme Gas Kinematics. _Astrophys. J._ **800**, 45 (2015).


18. Bridge, J. S. _et al._ Physical and Morphological Properties of [O II] Emitting Galaxies in the


HETDEX Pilot Survey. _Astrophys. J._ **799**, 205 (2015).


19. Yuma, S. _et_ _al._ Systematic Survey for [O II], [O III], and H _α_ Blobs at z = 0.1-1.5: The


Implication for Evolution of Galactic-scale Outflow. _Astrophys. J._ **841**, 93 (2017).


20. Epinat, B. _et al._ Ionised gas structure of 100 kpc in an over-dense region of the galaxy group


COSMOS-Gr30 at z _∼_ 0.7. _Astron. & Astrophys._ **609**, A40 (2018).


21. Johnson, S. D. _et al._ Galaxy and Quasar Fueling Caught in the Act from the Intragroup to the


Interstellar Medium. _Astrophys. J._ **869**, L1 (2018).


22. Zhu, G., Moustakas, J. & Blanton, M. R. The [O II] _λ_ 3727 Luminosity Function at z _∼_ 1.


_Astrophys. J._ **701**, 86–93 (2009).


10

23. Kalfountzou, E., Jarvis, M. J., Bonfield, D. G. & Hardcastle, M. J. Star formation in high

redshift quasars: excess [O II] emission in the radio-loud population. _Mon._ _Not._ _R._ _Astron._


_Soc._ **427**, 2401–2410 (2012).


24. Pulsoni, C. _et_ _al._ The extended Planetary Nebula Spectrograph (ePN.S) early-type galaxy


survey: The kinematic diversity of stellar halos and the relation between halo transition scale


and stellar mass. _Astron. & Astrophys._ **618**, A94 (2018).


25. Rubin, K. H. R. _et al._ Low-ionization Line Emission from a Starburst Galaxy: A New Probe


of a Galactic-scale Outflow. _Astrophys. J._ **728**, 55 (2011).


26. Prochaska, J. X., Kasen, D. & Rubin, K. Simple Models of Metal-line Absorption and Emis

sion from Cool Gas Outflows. _Astrophys. J._ **734**, 24 (2011).


27. Behroozi, P. S., Conroy, C. & Wechsler, R. H. A Comprehensive Analysis of Uncertainties


Affecting the Stellar Mass-Halo Mass Relation for 0 _<_ _z_ _<_ 4. _Astrophys._ _J._ **717**, 379–403


(2010).


28. Villar-Mart´ın, M. _et al._ A 100 kpc nebula associated with the ‘Teacup’ fading quasar. _Mon._


_Not. R. Astron. Soc._ **474**, 2302–2312 (2018).


29. Kim, D. C. _et al._ Hubble Space Telescope ACS Imaging of the GOALS Sample: Quantitative


Structural Properties of Nearby Luminous Infrared Galaxies with L _IR_ _>_ 10 [11] _[.]_ [4] L _⊙_ . _Astrophys._


_J._ **768**, 102 (2013).


30. Thompson, T. A., Quataert, E., Zhang, D. & Weinberg, D. H. An origin for multiphase gas in


galactic winds and haloes. _Mon. Not. R. Astron. Soc._ **455**, 1830–1844 (2016).


11

31. Gronke, M. & Oh, S. P. The growth and entrainment of cold gas in a hot wind. _Mon. Not. R._


_Astron. Soc._ **480**, L111–L115 (2018).


12

### 10 [0] 40 20 0 10 1 20 40

|Col1|100 kpc 17 arcsec|Col3|Col4|
|---|---|---|---|
||100 kpc<br>17 arcsec|||
||100 kpc<br>17 arcsec|||
||100 kpc<br>17 arcsec|||
||100 kpc<br>17 arcsec|||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||


### 40 20 0 20 40 x (kpc)

**Figure** **1** **The** **giant** **galactic** **wind** **surrounding** **the** **massive,** **compact** **galaxy** **Makani,** **ob-**


**served by emission from the [O II] line at** _λ_ **=3726** **A and 3729** **[˚]** **A.** **[˚]** The colour scale and white


contours show observed-frame surface brightness, and the axes are labeled in kilopar

secs from the galaxy nucleus. Contours are 2–16% of peak flux, spaced by factors of 2. A


13

rest-frame _V_ -band image of the galaxy (Hubble Space Telescope/WFC3 F814W filter) is


superimposed on the center of the [O II] image taken with KCWI at the Keck II telescope.


The small circle at the centre illustrates the radius of the compact core (400 pc). North is


up and east is to the left.


14

**Figure 2** **Velocity maps of the galactic wind.** The velocities are from fits to Voronoi-binned


[O II] data and are calculated from the red side of the cumulative velocity distribution


function to specified percentiles as maximum blueshifted velocity _v_ max _≡_ _v_ 98% = _v_ 50% _−_


2 _σ_ ( **a** ) and velocity dispersion _σ_ _≡_ ( _v_ 34% _−_ _v_ 68% ) _/_ 2 ( **b** ). In **a**, the blue colour denotes


velocity. The insets show the deblended and stacked [O II] doublet versus velocity; these


highlight representative bins for each star formation or outflow episode. The black line is


the continuum-subtracted spectrum, and the yellow or red filled profile is the emission line


model. The colour denotes whether the spaxel is part of episode I (yellow) or episode II


(red). The black contours are as in Fig. 1, and the white Hubble Space Telescope contour


represents 1% of the peak stellar continuum flux, accentuating the extended diffuse stellar


emission from tidal forces in the merger. In **b**, the purple colour denotes velocity dispersion


and the yellow and red contours outline regions of specified _v_ max = _v_ 98% to delineate


15

episodes I and II. The spatial separation of the episodes is also reflected in the _σ_ map.


The black contours in **b** outline the inner concentration of ionized gas at velocities _−_ 1 _,_ 500


to _−_ 500 km s _[−]_ [1] (Fig. 3d). We securely detect high-velocity [O II] beyond this inner region


through Voronoi binning.


16

**Figure** **3** **Comparison of the ionized,** **neutral atomic and molecular phases of the galactic**


17

**winds.** The [O II] map from Fig. 1 is replicated in **a**, with the north and east directions


indicated in the lower right. In **b**, a zoomed-in view of the inner 40 kpc, molecular gas


in restored CO(2–1) (green contours) is plotted on top of Mg II emission (colour, with


white contours) in the same velocity range ( _−_ 500 to +500 km s _[−]_ [1] ). Panel **c** compares the


low-velocity molecular (restored CO, green contours) and ionized gas ([O II], colour and


_−_
white contours) over the same velocities ( 300 to +300 km s _[−]_ [1] ). The CO contours are


0.09, 0.14, 0.28, 0.5, 0.8 and 1.2 mJy per beam. Panel **d** is the high-velocity molecular


gas (tapered, bottom right, contours of 0.08, 0.11, 0.122, 0.132, and 0.14 mJy per beam)


on an [O II] channel map showing the brightest regions of high-velocity ionized gas, both


over _−_ 1,500 to _−_ 500 km s _[−]_ [1] . In each zoom box, the inset spectrum is a plot of spatially


_−_
integrated optical line flux versus velocity ( 2,500 to +2,500 km s _[−]_ [1] ), with the linemap


velocity range highlighted in orange.


18

**Methods**


**KCWI observations and data analysis.** SDSS J211824.06+001729.4 was originally selected as


an intermediate-redshift starburst galaxy with broad but spatially unresolved line emission [13,14], part


of a population known to host strong outflows [32] . We observed it with KCWI on the Keck II tele

scope on 6 November 2018 UT (Universal Time) for 40 min. We employed the blue low-dispersion


(BL) grating and medium slicer with KCWI, yielding a resolution of 2.5 A [˚] and wavelength cov

erage of 3435–5525 A. [˚] We chose a central wavelength of 4500 A [˚] and detector binning of 2 _×_ 2.


Conditions were photometric, with 0.6 _[′′]_ seeing. Two exposures were dithered 0.35 _[′′]_ along slices


to subsample the long spatial dimension of the output spaxels (0.69 _[′′]_ _×_ 0.29 _[′′]_ ). The field of view of


the reduced data cube is 15.4 _[′′]_ _×_ 19.4 _[′′]_ .


We reduced the data using the KCWI data reduction pipeline and the IFSRED library [33] . As


the default scattered light subtraction in the pipeline leaves visible residuals, we use a routine


(IFSR ~~K~~ CWISCATSUB) to subtract scattered light by summing the data in 100-pixel increments


along columns (parallel to the dispersion direction) and fitting the least contaminated inter-slice re

gions along rows (parallel to the spatial direction) with low-order polynomials. The default wave

length calibration also produces large root-mean-square (r.m.s.) residuals because of a mismatch


with the pipeline thorium-argon (ThAr) atlas, so we extract a representative spectrum from our data


and find its wavelength solution using IDENTIFY in PyRAF (www.stsci.edu/institute/software ~~h~~ ardware/pyraf).


16/20 lines in the 3500–4000 A and 5000–5600 [˚] A ranges are from Th; the other 38 lines (including [˚]


most of the brightest lines) are from Ar. The resulting r.m.s. residual is 0.18 A. We then input this [˚]


calibrated spectrum as the atlas into the pipeline, yielding a 0.07 A r.m.s.. [˚] Following the pipeline


19

stages, we resample the data (IFSR ~~K~~ CWIRESAMPLE) onto a 0.29 _[′′]_ _×_ 0.29 _[′′]_ spaxel grid; align the


two exposures by fitting the galaxy centroid (IFSR ~~P~~ EAK); and mosaic the data (IFSR ~~M~~ OSAIC).


The resulting stacked and resampled field of view at 5000 A is 53 [˚] _×_ 67 spaxels. The reconstructed


KCWI continuum image (rest-frame near-ultraviolet) is consistent with the Hubble Space Tele

scope WFC3/F814W image (rest-frame _V_ ) when convolved with a 15-pixel Gaussian kernel to


match the measured seeing. Finally, we sum the nebula’s core emission in a 3.0 _[′′]_ circular aperture


to match the Sloan Digital Sky Survey (SDSS) [34] spectrum.


We created initial [O II] linemaps by integrating over [O II] and subtracting nearby contin

uum windows on either side. The wavelength interval of each map is calculated from the doublet


average wavelength at a given velocity. We then used _±_ 300 km s _[−]_ [1] flux and error maps to create


Voronoi bins (where the velocity applies to the centroid of the [O II] doublet; the doublet lines are


2.6 A [˚] apart, which corresponds to 200 km s _[−]_ [1] ). The IDL (www.harrisgeospatial.com/Software

Technology/IDL) routine VORONOI ~~2~~ D ~~B~~ INNING [35] is used to construct the bins, with a target


signal-to-noise ratio of 10 and a threshold signal-to-noise ratio of 1. We fit the core spectrum, the


full data cube, and the Voronoi binned data cube with IFSFIT [36] . Because very few strong stellar


lines arise in our spectra (rest frame 2350–3790 A), we use a scaled continuum derived from the [˚]


fit to the rest-frame 2550–5600 A spectrum [˚] [14] (see below). We fit two velocity components to the


[O II] and [Ne V] lines. If any component falls below 2 _σ_ in a spaxel, the spectrum is re-fit with


fewer components. Allowing the [O II] line ratio to float freely in the narrow component of the core


spectrum results in an [O II]3729 A/[O [˚] II]3726 A ratio of 1.2 (corresponding to [˚] n e _≈_ 200 cm _[−]_ [3] ),


while the broad component ratio is unconstrained. We thus fix the [O II] ratio to 1.2 in all fits.


20

In the core spectrum, Mg I 2852 A, Mg [˚] II 2796, 2803 A, and Fe [˚] II* 2612, 2626 A are tied to the [˚]


same velocity and width and fitted with a single component. The continuum fits to each spaxel


are used to subtract the stellar continuum around [O II] or Mg II to produce the linemaps shown


in Figs. 1–3. The [O II] linemaps have a limiting 1 _σ_ surface brightness per pixel of 1.0 _×_ 10 _[−]_ [18]


erg s _[−]_ [1] cm _[−]_ [2] arcsec _[−]_ [2] . For display purposes only, these maps are interpolated to a grid ten times


finer and the _±_ 300 km s _[−]_ [1] maps are clipped at 1.5% of peak flux (or 4 _σ_ ).


The core spectrum yields detections of [O II], [Ne V] 3426 A, Mg I 2852 [˚] A, Mg II 2796, 2803 [˚] A, [˚]


and Fe II* 2612, 2626 A in emission, and Fe II 2586 [˚] A in absorption. The emission lines break into [˚]


two distinct components: a narrow feature at the systemic velocity of the host galaxy ( _z_ = 0 _._ 45916;


_σ_ = 143 km s _[−]_ [1] in [O II], 197 km s _[−]_ [1] in Mg and Fe emission) and a broad, blueshifted feature that


is outflowing ( _z_ = 0 _._ 45736 _,_ _v_ = _−_ 540 km s _[−]_ [1] _,_ _σ_ = 500 km s _[−]_ [1] in [O II]; _z_ = 0 _._ 45666 _,_ _v_ =


_−_ 750 km s _[−]_ [1] _,_ _σ_ = 392 km s _[−]_ [1] in [Ne V]). We correct upward spatially-integrated line fluxes and


luminosities for a Galactic extinction of _A_ _V_ = 0 _._ 2075 (ref. [37] ), which corresponds to a 22% cor

rection at [O II]. We use the 2018 Planck cosmology [38] to calculate luminosity and angular size


distances. The spatially-integrated [O II] flux is 4 _._ 0( _±_ 0 _._ 2) _×_ 10 _[−]_ [15] erg s _[−]_ [1] cm _[−]_ [2] . From the core


spectrum we measure a Mg II flux of 2 _._ 3( _±_ 0 _._ 1) _×_ 10 _[−]_ [16] erg s _[−]_ [1] cm _[−]_ [2], which corresponds to a


rest-frame equivalent width 2.3 A and a luminosity of [˚] 1 _._ 5 _×_ 10 [41] erg s _[−]_ [1] . The [Ne V] line flux is


4 _._ 3( _±_ 1 _._ 2) _×_ 10 _[−]_ [17] erg s _[−]_ [1] cm _[−]_ [2] .


**Ionized** **and** **neutral** **gas** **properties.** We parameterize the velocity distribution of the [O II]

emitting gas in each spaxel using the cumulative velocity distribution function (CVDF). In spaxels


where only one component is fitted, this is a Gaussian; for two components, the CVDF is the sum


21

of two independent Gaussians. We use the 50th and 98th percentile of the CVDF ( _v_ 50% and _v_ 98%,


as measured from the red side of the line) to represent the mean and most blueshifted (’maximum’)


velocities. We define the width of the CVDF as _σ_ _≡_ ( _v_ 34% _−v_ 68% ) _/_ 2, which for a single component


is the usual Gaussian _σ_ .


We combine our KCWI data with two other spectra to constrain the integrated gas excitation,


reddening, and gas mass. The first is the SDSS spectrum that, along with [O II], covers the


[Ne III] 3869 A, H [˚] _β_, and [O III] 4959 A, 5007 [˚] A emission lines. The second is a spectrum acquired [˚]


with Keck/NIRSPEC, which covers the H _α_, [N II] 6548 A, [˚] 6583 A, [˚] and [S II] 6717 A, [˚] 6731 A [˚]


lines. The latter was observed with a 0.76 _[′′]_ -wide slit at a position angle of 83 _[◦]_ east of north. We


scale the NIRSPEC data to match the SDSS spectrum where they overlap and correct for Galactic


extinction as above. Because of the lower signal-to-noise ratio in these spectra compared to the


KCWI spectrum, we fix the velocities and linewidths of each emission line using the fit to the


KCWI core spectrum. We measure an H _α_ flux of 1 _._ 9( _±_ 0 _._ 1) _×_ 10 _[−]_ [15] erg s cm _[−]_ [2] and an extinction


of _E_ ( _B −_ _V_ ) = 0 _._ 4( _±_ 0 _._ 2) from the Balmer decrement. We then scale this flux upward to account


for the entire nebula, since the [O II] flux within the SDSS aperture is 24% of the total. Using the


estimated gas density of 200 cm _[−]_ [3] from the [O II] flux ratio and correcting upward for extinction


by a factor of four yields an ionized gas mass of 6( _−_ [+6] 3 [)] _[ ×]_ [ 10] [8] [(200] [cm] _[−]_ [3] _[/]_ [n] [e] [)] _[M]_ _[⊙]_ [.] [The] [extinction]


uncertainty drives the 50% error, but unquantified systemic uncertainties in the electron density


and [O II]/H _α_ line ratio (because we do not spatially resolve these quantities) are likely to be


larger than this.


We show rest-frame optical line flux ratios from the unresolved NIRSPEC and SDSS spectra


22

in Extended Data Fig. 1. The narrow component is consistent with photo-ionization by young


stars and a near-solar metallicity, while the broad component is consistent with photo-ionization


by an AGN [39] with ionization parameter _U_ _≈−_ 2 or shock ionization [40] with a velocity of at least


300–400 km s _[−]_ [1] . The higher excitation of the broad, outflowing component is also illustrated in


the increasing [O III]/[O II] ratio with increasing blueshift (Extended Data Fig. 2). Besides the


ionized gas lines, Extended Data Fig. 2 shows the absorption-line outflow in Fe II 2586 A; [˚] the


corresponding Mg II emission that is systemic with a slight red wing (typical for the emission


component of a resonant-line profile in a neutral outflow but without the usual absorption) [25,26] ;


and the broad, high-velocity wings of the CO(2–1) profile.


Other high-ionization lines arise in the observed-frame optical part of the spectrum. Notably,


the [Ne V] emission is spatially unresolved and found only in the outflowing component, with


_v_ 98% = 1 _,_ 500 km s _[−]_ [1] . Whereas [Ne V] is typically used as an AGN indicator [41], its (extincted)


luminosity in Makani, 3 _._ 6( _±_ 1 _._ 0) _×_ 10 [40] erg s _[−]_ [1], is three times lower than the average for typical


[Ne V] emitters detected at _z_ = 0 _._ 6–1 _._ 2 (ref. [42] ); it may therefore be emitted in shocks [40,43] . The


line ratios in the broad component of the core KCWI and SDSS spectra of log([Ne V]/[Ne III]


3869 A) [˚] = _−_ 0 _._ 77 [+0] _−_ 0 _._ _[.]_ 20 [13] [,] [log([O] [II]/[O] [III])] [=] _[−]_ [0] _[.]_ [11] [+0] _−_ 0 _[.]_ _._ [04] 05 [,] [log([Ne] [V]/[O] [II])] [=] _[−]_ [1] _[.]_ [07] [+0] _−_ 0 _[.]_ _._ [11] 15 [,] [and]


log(He II 4686 A/H [˚] _β_ ) _<_ _−_ 0 _._ 87 [+0] _[.]_ [39] are also consistent with either AGN photo-ionization [39] or


ionization in shocks with velocities [40,44,45] of at least 300–400 km s _[−]_ [1] .


**ALMA observations,** **data reduction and analysis.** Makani was observed by the ALMA 12-m


array as part of projects 2016.1.01072.S and 2017.1.01318.S on 11 March 2017, 10 April 2018


and 15 December 2017 in antenna configurations C40-1 (baselines 15–287 m) and C43–3 (base

23

lines 15–500 m) and C43–6 (baselines 15–2517 m) respectively. We used the Band 4 receivers


with a representative frequency of 158.01 GHz to detect CO(2–1) at the redshift of the target.


The total integration time on source was 212 min. The average precipitable water vapour column


during observations was approximately 2.5 mm and the average system temperature was approxi

mately 75 K. The atmospheric, bandpass, pointing, phase and flux calibrators included the sources


J2148+0657, J2134-0153 and Neptune.


We use the quality-checked ALMA pipeline-calibrated products, concatenating the observa

tions into a single measurement set. We image the data using CASA (version 5.1.0-74), producing


three versions of the data cube: naturally weighted, 1 _[′′]_ tapered and 0.6 _[′′]_ restored. The latter uses


a circular Gaussian restoring beam with a full-width at half-maximum (FWHM) of 0.6 _[′′]_ to match


the seeing of the KCWI data. We produce a tapered image in order to maximise sensitivity to


potentially extended but weak CO emission around the target. We produce clean cubes by first


generating dirty cubes and assess the r.m.s. noise per channel in each version. This value is then


used in an iterative cleaning step (CASA clean) where we set a cleaning threshold of 3 _σ_, chosen to


maintain a balance between producing a clean image while ensuring real faint extended structure is


not removed. We use multi-scale cleaning with scales of 0 _[′′]_, 0.4 _[′′]_, 0.8 _[′′]_ and 1.6 _[′′]_ . The FWHM of the


synthesized clean beams in the naturally weighted and tapered images are 0 _._ 39 _[′′]_ _×_ 0 _._ 31 _[′′]_ (position


angle PA = _−_ 73 _[◦]_ east of north) and 1 _._ 15 _[′′]_ _×_ 1 _._ 08 _[′′]_ (PA = _−_ 79 _[◦]_ ) respectively. The beam-restored


image by definition has a circular beam of FWHM 0.6 _[′′]_ . We produce data cubes with a spec

tral resolution of 30 km s _[−]_ [1] (16 MHz), and image the full spectral coverage including basebands


placed to measure continuum emission at 2 mm in line-free regions. The r.m.s. (1 _σ_ ) noise per


24

30 km s _[−]_ [1] channel in the natural, tapered and restored cubes is 0.13 mJy beam _[−]_ [1], 0.20 mJy beam _[−]_ [1]


and 0.15 mJy beam _[−]_ [1] respectively.


After examining the cubes and extracting spectra, we detect a weak 2 mm continuum compo

nent to the observed emission: averaged over 143.5–146.5 GHz, with a total _S_ 2 mm = 26( _±_ 10) mJy.


By collapsing the cube over this frequency range we construct a continuum image that is subtracted


from the channels spanning the CO(2–1) line. CO(2–1) emission is observed out to a high velocity


of _v_ = _±_ 1500 km s _[−]_ [1] in the total spectrum, similar to the maximum velocities in the [O II ] nebula.


Therefore, to measure the line luminosity we first average the tapered cube over _v_ = _±_ 1500 km s _[−]_ [1]


and define a 3 _σ_ mask for the source extent, based on the noise in the channel-averaged map. This


mask is used to integrate the spectrum, measuring _S_ ∆ _V_ across different velocity ranges. We de

fine a second mask where regions with signal exceeding 15 _σ_ in the collapsed tapered image are


excluded, eliminating the contribution from the bright core and eastern tidal arm. The rationale for


this is to provide an estimate of the CO emission associated with extended (possibly outflowing)


material.


Line luminosities are calculated in the conventional radio units of K km s _[−]_ [1] pc [2] as _L_ _[′]_ =


3 _._ 25 _×_ 10 [7] _D_ _L_ [2] [(1 +] _[ z]_ [)] _[−]_ [1] _[ν]_ rest _[−]_ [2] _[S]_ [∆] _[V]_ [,] [where] _[D]_ _[L]_ [is] [the] [luminosity] [distance] [in] [Mpc,] _[ν]_ [rest] [is] [the] [rest-]


frame frequency of the line in GHz and _S_ ∆ _V_ is the integrated line flux in Jy km s _[−]_ [1] . CO line


luminosities are converted to estimates of the molecular gas mas through _M_ H 2 = _αL_ _[′]_ . As in


previous works [7], we adopt _α_ = 0 _._ 34 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1], lower than both the standard Galactic


and ULIRG conversionsbecause high-velocity extended and/or CO emission might be optically


thin if it is tracing molecular gas in a turbulent outflow [46] . This provides a conservative estimate of


25

the molecular gas mass.


**Size measurements.** A S´ersic fit to the Hubble Space Telescope image of Makani yields an effec

tive radius _R_ _e_ = 2 _._ 24 kpc for a S´ersic index of _n_ = 4 [14] . For a pure S´ersic profile, _R_ _e_ is equivalent


to the stellar half-light radius _r_ _∗,_ 1 _/_ 2, or the radius within which half of the stellar light arises [47] . The


substantial extended, asymmetric tidal structure in a merger like Makani will affect the determi

nation of any S´ersic component, although in this case it appears not to be a large effect; a direct


measure of the half-light radius from integration of the stellar light yields _r_ _∗,_ 1 _/_ 2 _≈_ 2 _._ 75 kpc. We


take the average of these estimates, 2.5 kpc, as the half-light radius.


Makani has a peaked core that is well interior of the half-light radius. An estimate of its size


is the radial width at half-maximum of the radial light profile. This measure yields a core radius of


400 pc, within which 10% of the galaxy’s stellar light resides. This radius is comparable to other


starbursts and post-starbursts without extended tidal structure [14] .


For comparison, Extended Data Fig. 3 shows the radial profile of the [O II] nebula, de

termined from azimuthal averages over pixels in bins of radial width 2 kpc. Integrating over the


nebula from the centre outward as a fraction of the total flux within 50 kpc yields a half-light radius


in [O II] of 17 kpc. The short (east-to-west) and long (north-to-south) axis profiles, averaged in the


direction perpendicular to each profile over bins 2 kpc wide, decrease less steeply, with maximum


nuclear distances of about 40 and 50 kpc along the short and long axes, respectively. When dou

bled, these yield the quoted size of 100 kpc _×_ 80 kpc. These measurements approach the size of the


KCWI field of view, implying the nebula could be larger.


26

**Stellar mass estimation.** We estimate the stellar mass of Makani using the Bayesian stellar popu

lation synthesis modeling code Prospector [48] and the Flexible Stellar Population Synthesis (FSPS) [49,50]


models (Extended Data Fig. 4). We assemble the spectral energy distribution at rest-frame wave

lengths between 0.1 _µ_ m and 15 _µ_ m from the Galaxy Evolution Explorer [51], the SDSS [34], the Spitzer


Space Telescope [52] and the Wide-field Infrared Survey Explorer (WISE) [53] . We adopt a Salpeter ini

tial mass function from the range (0.1–100) _M_ _⊙_ and assume a ’delayed _τ_ ’ backbone star-formation


history ( _τ_ is the e-folding star-formation timescale) with a late-time burst of star formation super

posed. We assume a power-law dust attenuation curve (proportional to _λ_ _[−]_ [0] _[.]_ [7] ) and allow differential


attenuation between the light from young stars relative to the diffuse interstellar medium [54] . Finally,


we compute the infrared spectrum using energy balance arguments and basic assumptions about


the re-radiated infrared spectrum [55] . The median value of the marginalized posterior probability


for stellar mass is log( _M_ _∗_ _/M_ _⊙_ ) = 11 _._ 07 with an interquartile range of 10.98–11.14. To account


for systematic uncertainties in the star-formation history and other prior parameters we adopt an


average stellar mass and uncertainty of log( _M_ _∗_ _/M_ _⊙_ ) = 11 _._ 1( _±_ 0 _._ 2).


We assume that the mid-infrared dust emission in Makani arises from star formation in order


to fit the spectral energy distribution. WISE mid-infrared colours—W1 _−_ W2 = 0 _._ 74( _±_ 0 _._ 03) and


W2 _−_ W3 = 3 _._ 64( _±_ 0 _._ 08), in Vega magnitudes [53,56] —place this galaxy in a region occupied partly


by starbursts, but also characteristic of obscured AGN in merging galaxies [57,58] . The present data


do not distinguish between these possibilities.


**Stellar** **continuum** **modeling.** To obtain the best constraints on the young stellar populations in


Makani we fit its rest-frame ultraviolet-optical spectrum with stellar population synthesis models.


27

This fitting is very sensitive to both the quality of the spectrophotometry and the strong stellar ab

sorption lines in the 3700–5000 A range. [˚] Since the KCWI spectrum does not extend redwards of


restframe 3800 A, we use a spectrum obtained with the Blue Channel Spectrograph on the MMT [˚]


with a 1 _[′′]_ slit [14] . To further extend the wavelength coverage, we join the MMT and SDSS spectra


near 4600 A. These spectra have similar spectral resolutions ( [˚] _R ≈_ 1500). The combined spectrum


(Extended Data Fig. 5) matches the SDSS _ugriz_ photometry well, indicating good spectrophoto

metric calibration.


We fit the MMT+SDSS spectrum with a combination of simple stellar population models


and the Salim attenuation curve [59] . We use FSPS to generate simple stellar populations with Padova


2008 isochrones, a Salpeter initial mass function, and a new theoretical stellar library C3K (C. Con

roy et al., manuscript in preparation) with a resolution of _R ≈_ 10 _,_ 000. We utilize solar-metallicity


simple stellar population templates with 42 ages spanning 1 Myr to 7.9 Gyr. We perform the fit


with the Penalized Pixel-Fitting (pPXF) code [60,61] . Because the galaxy is very compact and much


of its dust is likely to be in the outflow, we require all stellar populations to share the same at

tenuation. The best fit model has _z_ = 0 _._ 4590, a stellar velocity dispersion _σ_ = 170 km s _[−]_ [1], and


_E_ ( _B −_ _V_ ) = 0 _._ 19. The spectrum is dominated by a mixture of young and intermediate age stellar


populations, with approximately 50% of the continuum emission at rest-frame 5500 A contributed [˚]


by populations less than 7 Myr old. An additional 40% comes from a 0.4-Gyr-old stellar popula

tion. This implies two major starburst episodes, with the 0.4-Gyr burst perhaps corresponding to


the first passage of the merger and the recent burst to the final coalescence. The 10-Myr-averaged


star-formation rate inferred from the simple stellar population modelling is 175M _⊙_ yr _[−]_ [1], after con

28

verting to a Chabrier initial mass function [62] .


**Data Availability** Raw data generated at the Keck Observatory are available at the Keck Obser

vatory Archive (koa.ipac.caltech.edu) following the standard 18-month proprietary period after the


date of observation. This paper makes use of the ALMA data ADS/JAO.ALMA#2016.1.01072.S


and ADS/JAO.ALMA#2017.1.01318.S, which are available at the ALMA Science Archive (alma

science.nrao.edu/aq/). Some of the data presented here were obtained from the SDSS (www.sdss.org).


The Hubble Space Telescope observations described here were obtained from the Hubble Legacy


Archive (hla.stsci.edu). Derived data supporting the findings of this study are available from the


corresponding author upon request.


**References**


32. Tremonti, C. A., Moustakas, J. & Diamond-Stanic, A. M. The Discovery of 1000 km s _[−]_ [1]


Outflows in Massive Poststarburst Galaxies at z=0.6. _Astrophys. J. Lett._ **663**, L77–L80 (2007).


33. Rupke, D. S. N. IFSRED: Data Reduction for Integral Field Spectrographs. Astrophysics


Source Code Library (2014). [ascl:1409.004.](ascl:1409.004)


34. York, D. G. _et al._ The Sloan Digital Sky Survey: Technical Summary. _Astron. J._ **120**, 1579–


1587 (2000).


35. Cappellari, M. & Copin, Y. Adaptive spatial binning of integral-field spectroscopic data using


Voronoi tessellations. _Mon. Not. R. Astron. Soc._ **342**, 345–354 (2003).


29

36. Rupke, D. S. N. IFSFIT: Spectral Fitting for Integral Field Spectrographs. Astrophysics


Source Code Library (2014). [ascl:1409.005.](ascl:1409.005)


37. Schlafly, E. F. & Finkbeiner, D. P. Measuring Reddening with Sloan Digital Sky Survey Stellar


Spectra and Recalibrating SFD. _Astrophys. J._ **737**, 103 (2011).


38. Planck Collaboration _et al._ Planck 2018 results. VI. Cosmological parameters. _arXiv e-prints_


arXiv:1807.06209 (2018).


39. Groves, B. A., Dopita, M. A. & Sutherland, R. S. Dusty, Radiation Pressure-Dominated


Photoionization. II. Multiwavelength Emission Line Diagnostics for Narrow-Line Regions.


_The Astrophysical Journal Supplement Series_ **153**, 75–91 (2004).


40. Allen, M. G., Groves, B. A., Dopita, M. A., Sutherland, R. S. & Kewley, L. J. The MAPPINGS


III Library of Fast Radiative Shock Models. _The Astrophysical Journal Supplement Series_ **178**,


20–55 (2008).


41. Gilli, R. _et al._ The X-ray to [Ne V]3426 flux ratio: discovering heavily obscured AGN in the


distant Universe. _Astron. & Astrophys._ **519**, A92 (2010).


42. Vergani, D. _et al._ The VIMOS Public Extragalactic Redshift Survey (VIPERS). AGN feedback


in [NeV] emitters. _Astron. & Astrophys._ **620**, A193 (2018).


43. Best, P. N., R¨ottgering, H. J. A. & Longair, M. S. Ionization, shocks and evolution of the


emission-line gas of distant 3CR radio galaxies. _Mon. Not. R. Astron. Soc._ **311**, 23–36 (2000).


30

44. Allen, M. G., Dopita, M. A. & Tsvetanov, Z. I. Ultraviolet Diagnostics for the Emission-Line


Gas in Active Galaxies. _Astrophys. J._ **493**, 571–582 (1998).


45. Reynaldi, V. & Feinstein, C. The fingerprints of photoionization and shock-ionization in two


CSS sources. _Mon. Not. R. Astron. Soc._ **455**, 2242–2252 (2016).


46. Bolatto, A. D. _et al._ Suppression of star formation in the galaxy NGC 253 by a starburst-driven


molecular wind. _Nature_ **499**, 450–453 (2013).


47. Graham, A. W. & Driver, S. P. A Concise Reference to (Projected) S´ersic R [1] _[/n]_ Quantities, In

cluding Concentration, Profile Slopes, Petrosian Indices, and Kron Magnitudes. _Publ. Astron._


_Soc. Aus._ **22**, 118–127 (2005).


48. Leja, J., Johnson, B. D., Conroy, C., van Dokkum, P. G. & Byler, N. Deriving Physical Prop

erties from Broadband Photometry with Prospector: Description of the Model and a Demon

stration of its Accuracy Using 129 Galaxies in the Local Universe. _Astrophys._ _J._ **837**, 170


(2017).


49. Conroy, C., Gunn, J. E. & White, M. The Propagation of Uncertainties in Stellar Population


Synthesis Modeling. I. The Relevance of Uncertain Aspects of Stellar Evolution and the Initial


Mass Function to the Derived Physical Properties of Galaxies. _Astrophys._ _J._ **699**, 486–506


(2009).


50. Conroy, C. & Gunn, J. E. FSPS: Flexible Stellar Population Synthesis. Astrophysics Source


Code Library (2010). [ascl:1010.043.](ascl:1010.043)


31

51. Morrissey, P. _et al._ The Calibration and Data Products of GALEX. _Astrophys. J. Suppl._ **173**,


682–697 (2007).


52. Werner, M. W. _et_ _al._ The Spitzer Space Telescope Mission. _Astrophys._ _J._ _Suppl._ **154**, 1–9


(2004).


53. Lang, D., Hogg, D. W. & Schlegel, D. J. WISE Photometry for 400 Million SDSS Sources.


_Astron. J._ **151**, 36 (2016).


54. Charlot, S. & Fall, S. M. A Simple Model for the Absorption of Starlight by Dust in Galaxies.


_Astrophys. J._ **539**, 718–731 (2000).


55. Draine, B. T. & Li, A. Infrared Emission from Interstellar Dust. IV. The Silicate-Graphite-PAH


Model in the Post-Spitzer Era. _Astrophys. J._ **657**, 810–837 (2007).


56. Stern, D. _et_ _al._ Mid-infrared Selection of Active Galactic Nuclei with the Wide-Field In

frared Survey Explorer. I. Characterizing WISE-selected Active Galactic Nuclei in COSMOS.


_Astrophys. J._ **753**, 30 (2012).


57. Satyapal, S. _et al._ Buried AGNs in Advanced Mergers: Mid-infrared Color Selection as a Dual


AGN Candidate Finder. _Astrophys. J._ **848**, 126 (2017).


58. Blecha, L., Snyder, G. F., Satyapal, S. & Ellison, S. L. The power of infrared AGN selection


in mergers: a theoretical study. _Mon. Not. R. Astron. Soc._ **478**, 3056–3071 (2018).


32

59. Salim, S., Boquien, M. & Lee, J. C. Dust Attenuation Curves in the Local Universe: Demo

graphics and New Laws for Star-forming Galaxies and High-redshift Analogs. _Astrophys. J._


**859**, 11 (2018).


60. Cappellari, M. & Emsellem, E. Parametric Recovery of Line-of-Sight Velocity Distributions


from Absorption-Line Spectra of Galaxies via Penalized Likelihood. _Publ. Astron. Soc. Pac._


**116**, 138–147 (2004).


61. Cappellari, M. Improving the full spectrum fitting method: accurate convolution with Gauss

Hermite functions. _Mon. Not. R. Astron. Soc._ **466**, 798–811 (2017).


62. Chabrier, G. The Galactic Disk Mass Function: Reconciliation of the Hubble Space Telescope


and Nearby Determinations. _Astrophys. J._ **586**, L133–L136 (2003).


63. Kauffmann, G. _et_ _al._ The host galaxies of active galactic nuclei. _Mon._ _Not._ _R._ _Astron._ _Soc._


**346**, 1055–1077 (2003).


64. Kewley, L. J., Groves, B., Kauffmann, G. & Heckman, T. The host galaxies and classification


of active galactic nuclei. _Mon. Not. R. Astron. Soc._ **372**, 961–976 (2006).


**Acknolwedgments** We thank M. Gronke for comments on the manuscript and C. Conroy for providing


the C3K models before publication. D.S.N.R. was supported in part by the J. Lester Crain Chair of Physics


at Rhodes College. J.E.G. is supported by the Royal Society. This material is based upon work supported


by the National Science Foundation (NSF) under a collaborative grant (AST-1814233, 1813299, 1813365,


1814159 and 1813702). We acknowledge support from NASA award number SOF-06-0191 issued by the


33

Universities Space Research Association. Some of the data presented herein were obtained at the W. M.


Keck Observatory, which is operated as a scientific partnership among the California Institute of Technol

ogy, the University of California and NASA. The Observatory was made possible by the generous financial


support of the W. M. Keck Foundation. The authors wish to recognize and acknowledge the very significant


cultural role and reverence that the summit of Mauna Kea has always had within the indigenous Hawaiian


community. We are most fortunate to have the opportunity to conduct observations from this mountain.


ALMA is a partnership of the European Southern Observatory (ESO, representing its member states), NSF


(USA) and the National Institutes of Natural Sciences (Japan), together with the National Research Coun

cil (Canada), the Ministry of Science and Technology and Academia Sinica Institute of Astronomy and


Astrophysics (Taiwan), and the Korea Astronomy and Space Science Institute (Republic of Korea), in co

operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, the Associated


Universities, Inc. (AUI) / National Radio Astronomy Observatory (NRAO) and the National Astronomical


Observatory of Japan. NRAO is a facility of the NSF operated under cooperative agreement by AUI. The


Hubble Legacy Archive is a collaboration between the Space Telescope Science Institute (STScI/NASA), the


Space Telescope European Coordinating Facility (ST-ECF/ESA) and the Canadian Astronomy Data Centre


(CADC/NRC/CSA). Some of the data presented here were obtained at the MMT Observatory, a joint facility


of the University of Arizona and the Smithsonian Institution. Funding for the SDSS and SDSS-II has been


provided by the Alfred P. Sloan Foundation, the Participating Institutions, the NSF, the US Department of


Energy, NASA, the Japanese Monbukagakusho, the Max Planck Society, and the Higher Education Funding


Council for England. The SDSS is managed by the Astrophysical Research Consortium for the Participating


Institutions. The Participating Institutions are the American Museum of Natural History, Astrophysical In

stitute Potsdam, University of Basel, University of Cambridge, Case Western Reserve University, University


of Chicago, Drexel University, Fermilab, the Institute for Advanced Study, the Japan Participation Group,


34

Johns Hopkins University, the Joint Institute for Nuclear Astrophysics, the Kavli Institute for Particle As

trophysics and Cosmology, the Korean Scientist Group, the Chinese Academy of Sciences (LAMOST), Los


Alamos National Laboratory, the Max-Planck-Institute for Astronomy (MPIA), the Max-Planck-Institute


for Astrophysics (MPA), New Mexico State University, Ohio State University, University of Pittsburgh,


University of Portsmouth, Princeton University, the United States Naval Observatory, and the University of


Washington.


**Author Contributions** A.C. and J.E.G. conceived the observations of a sample developed by C.T. A.C.,


G.L., and D.S.N.R performed the KCWI observations, and J.E.G. led the ALMA data acquisition. D.S.N.R.


led data reduction and analysis of the KCWI data, while J.E.G. did so for the ALMA data. C.T. and E.R.G.


fitted ancillary spectra. D.S.N.R. wrote the manuscript, with contributions from A.C. throughout, J.E.G.


contributed to the section on ALMA observations, A.M.D.-S. and J.M. contributed to the section on stellar


mass, and C.T. contributed to the section on stellar populations. D.S.N.R., G.L., E.R.G., J.M., and C.T.


produced the figures, with A.C. and J.E.G. contributing to their design. J.M. performed the spectral energy


distribution modelling, and P.H.S. handled the structural analysis of the Hubble Space Telescope data. All


coauthors provided critical feedback to the text and helped shape the manuscript.


35

**Extended** **Data** **Fig.** **1** **Line** **ratio** **diagrams** **of** **the** **core** **spectrum.** In **a**, the green solid line


demarcates the edge of the _z_ = 0 pure star-formation locus [63] ; in both panels, blue long-dashed lines


denote the limits of young star photo-ionization [64] ; and in **b**, the green short-dashed line separates


Seyfert galaxies (AGNs) from low-ionization nuclear emission-line regions (LINERs) [64] . Error


bars are 1 _σ_ . The red narrow component is consistent with star formation at near-solar metallicity,


while the broad, outflowing component is ionized by either an AGN or high-velocity shocks.


36

10


8





6


4


2


0


-2


-2000 -1000 0 1000 2000
Velocity (km s -1 )


**Extended** **Data** **Fig.** **2** **Comparison** **of** **velocity** **profiles** **among** **gas** **phases.** Tracers are


shown as coloured lines, while the CO(2–1) profile is shaded in grey. The data are


smoothed by thjree pixels and the coloured shadings indicate 1 _σ_ errors on the line fluxes.


The ultraviolet-optical nebular lines are shown with the correct relative fluxes (uncorrected


for reddening in the host galaxy), while the CO(2-1) line is arbitrarily scaled. The spatially


integrated velocity profiles probe different gas phases and spatial scales but show re

markable overall consistency.


37

**Extended** **Data** **Fig.** **3** **[O** **II]** **spatial** **profiles.** Profiles are averaged and then plotted


versus distance from the galaxy nucleus along circular radii (black); the short axis of the


nebula, or east-to-west axis (blue); and the long axis of the nebula, or north-to-south axis


(purple). The averages are taken in directions perpendicular to these: in azimuth around


38

the nucleus; along the long axis; and along the short axis, respectively. The short and


long axis profiles are shifted upward in flux so that the three profiles match in the lowest


distance bin. Errors are standard errors of the mean. Plotted as dashed lines are the


stellar half-light radius (orange), the [O II] half-light radius within 50 kpc (black), and the


[O II] maximum radius along the short and long axes (blue and purple).


39

12


14


16





18


20


22


24

|Col1|P(M)<br>105 110 115<br>. . .<br>log10(M/M⊙)|Col3|
|---|---|---|
||||
||||
||||
||||
||||
||||
|0.1|0.1|1<br>10<br>Observed-Frame Wavelength (_µ_m)|



**Extended** **Data** **Fig.** **4** **Fit to the ultraviolet-to-mid-infrared spectral energy distribution.**


The best-fit model and 1 _σ_ error are shown as a black line and grey shading; observed


fluxes with 1 _σ_ errors (usually smaller than the symbols) are yellow circles; and model


fluxes are open cyan boxes. Flux is given in AB magnitudes and observed-frame wave

lengths in micrometres. The posterior probability _P_ ( _M_ ) for stellar mass _M_ is shown in the


inset.


40

25


20


15


10


5


0



2500 3000 3500 4000 4500 5000 5500
Restframe Wavelength (Å)











**Extended** **Data** **Fig.** **5** **Stellar** **population** **model** **fit.** Spectral data from SDSS and the


MMT and 1 _σ_ errors are shown as the black line and grey shading. SDSS _ugriz_ photometry


and 1 _σ_ errors are the cyan squares and grey vertical bars. The best-fit model is a magneta


line; the stellar population components summed to produce this model are shown as


coloured lines, with ages as shown. SSP, simple stellar population.


41


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: multi_facility_alma_minor",
  "failed_quote": "Here we report optical integral field observations of the massive but compact galaxy SDSS J211824.06 + 001729.4."
 },
 {
  "path": "data.baselines.evidence[0]",
  "value": "C40-1 (15–287 m), C43-3 (15–500 m), C43-6 (15–2517 m)",
  "failed_quote": "C40-1 (baselines 15–287 m) and C43–3 (baselines 15–500 m) and C43–6 (baselines 15–2517 m)"
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "HST morphology, Sersic fit (Re = 2.24 kpc, n=4) and X-ray luminosity",
  "failed_quote": "yields an effective radius Re = 2.24 kpc for a Sérsic index of n = 4 (cite: 14)"
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "CO-to-H2 conversion alpha = 0.34 Msun/(K km/s pc2)",
  "failed_quote": "As in previous works (cite: 7), we adopt α = 0.34 M⊙ (K km s−1 pc2)−1"
 }
]
```
