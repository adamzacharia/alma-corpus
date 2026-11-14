# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021PSJ.....2..105T\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version April 15, 2021
Typeset using L [A] TEX default style in AASTeX63


**Neptune’s** **Spatial** **Brightness** **Temperature** **Variations** **from** **the** **VLA** **and** **ALMA**


Joshua Tollefson, [1] Imke de Pater, [1, 2] Edward M. Molter, [1] Robert J. Sault, [3] Bryan J. Butler, [4]

Statia Luszcz-Cook, [5, 6] and David DeBoer [1]


1 _Astronomy_ _Department,_ _University_ _of_ _California,_ _Berkeley;_ _Berkeley_ _CA,_ _94720,_ _USA_
2 _Faculty_ _of_ _Aerospace_ _Engineering,_ _Delft_ _University_ _of_ _Technology,_ _Delft_ _2629_ _HS,_ _The_ _Netherlands_
3 _School_ _of_ _Physics,_ _University_ _of_ _Melbourne,_ _Victoria,_ _Australia_
4 _National_ _Radio_ _Astronomy_ _Observatory,_ _Socorro,_ _NM,_ _United_ _States_
5 _Department_ _of_ _Astronomy,_ _Columbia_ _University,_ _Pupin_ _Hall,_ _538_ _West_ _120th_ _Street,_ _New_ _York_ _City,_ _NY_ _10027_
6 _Astrophysics_ _Department,_ _American_ _Museum_ _of_ _Natural_ _History,_ _Central_ _Park_ _West_ _at_ _79th_ _Street,_ _New_ _York,_ _NY_ _10024,_ _USA_


ABSTRACT


We present spatially resolved (0 _._ 1 _[′′]_ _−_ 1 _._ 0 _[′′]_ ) radio maps of Neptune taken from the Very Large Array
and Atacama Large Submillimeter/Millimeter Array between 2015 _−_ 2017. Combined, these observations probe from just below the main methane cloud deck at _∼_ 1 bar down to the NH 4 SH cloud at
_∼_ 50 bar. Prominent latitudinal variations in the brightness temperature are seen across the disk. De
_−_
pending on wavelength, the south polar region is 5 40 K brighter than the mid-latitudes and northern
equatorial region. We use radiative transfer modeling coupled to Markov Chain Monte Carlo methods
to retrieve H 2 S, NH 3, and CH 4 abundance profiles across the disk, though only strong constraints can
be made for H 2 S. Below all cloud formation, the data are well fit by 53 _._ 8 [+18] _−_ 13 _[.]_ _._ [9] 4 _[×]_ [ and 3] _[.]_ [9] _−_ [+2] 3 _[.]_ _._ [1] 1 _[×]_ [ protosolar]
enrichment in the H 2 S and NH 3 abundances, respectively, assuming a dry adiabat. Models in which
the radio-cold mid-latitudes and northern equatorial region are supersaturated in H 2 S are statistically
favored over models following strict thermochemical equilibrium. H 2 S is more abundant at the equatorial region than at the poles, indicative of strong, persistent global circulation. Our results imply that
Neptune’s sulfur-to-nitrogen ratio exceeds unity as H 2 S is more abundant than NH 3 in every retrieval.
The absence of NH 3 above 50 bar can be explained either by partial dissolution of NH 3 in an ionic
ocean at GPa pressures or by a planet formation scenario in which hydrated clathrates preferentially
delivered sulfur rather than nitrogen onto planetesimals, or a combination of these hypotheses.


_Keywords:_ Neptune, Atmospheres, Radio Astronomy


1. INTRODUCTION


Neptune is the prototypical ‘ice giant’: a giant planet composed mainly of elements heavier than hydrogen and
helium by mass, such as oxygen, nitrogen, carbon, and sulfur. Within the cold environment of Neptune, the products
expected to form from these elements in the observable atmosphere include: H 2 O, NH 3, CH 4, and H 2 S. These molecules
provide clues to the bulk composition of the planet and so constraining their abundances is crucial for understanding
Neptune’s formation and thermal history.
Bright CH 4 clouds and aerosol hazes pervade throughout Neptune’s upper atmosphere. Optical and near-infrared
wavelengths are sensitive to these components, limiting views in the atmosphere to pressures less than _∼_ 1 bar. H 2 S
and NH 3 condense at higher temperatures and pressures than CH 4, meaning optical and near-infrared observations
are blind to their deep abundances. Radio wavelengths probe beyond these shallow features, resolving the structure of
Neptune’s atmosphere down to _∼_ 50 bar. Thus, NH 3 and H 2 S profiles can be constructed by inverting radio spectra.
While early radio observations could only obtain disk-averaged measurements of Neptune, the observed high brightness
temperatures longward of 10 cm required NH 3, a prominent microwave absorber, to be significantly depleted (de Pater
& Massie 1985). This is possible if an NH 4 SH cloud forms at _∼_ 50 bar and if the H 2 S abundance exceeds that of NH 3,


Corresponding author: Joshua Tollefson

[jtollefs@berkeley.edu](mailto: jtollefs@berkeley.edu)

2


resulting in the complete removal of NH 3 during the cloud’s formation. In such an atmosphere, an H 2 S abundance
between 30 _−_ 60 _×_ solar and an NH 3 abundance of _∼_ 1 _×_ solar are required to fit the disk-averaged data (de Pater et
al. 1991; DeBoer & Steffes 1996). Indeed, the detection of H 2 S spectral features near 1.58 _µ_ m in the tropospheres
of the ice giants implies that their deep bulk S/N ratio is greater than one (Irwin et al. 2018, 2019a).

de Pater et al. (2014) presented centimeter maps of Neptune from 2003, finding that the disk-averaged spectrum
agreed with the abundances obtained from earlier radio observations. In addition, they found that the bright south
polar cap must be significantly depleted in H 2 S down to _∼_ 40 bar in order to match the observed brightness temperature
at wavelengths of 0 _._ 7 _−_ 6 _._ 0 cm. However, this study did not investigate brightness variations at other latitudes, as the
sensitivity and resolution were not good enough to detect significant variations apart from those in the south polar

cap.
In 2011, an upgrade of the VLA was completed. This expansion improved the continuum sensitivity by 5-to-20-fold
and increased the wavelength coverage and bandwidth. This prompted a program to reobserve Neptune at centimeter
wavelengths. The resulting maps, presented in this paper, show clear brightness temperature variations across the
disk akin to that seen in millimeter maps produced from the Atacama Large Submillimeter/Millimeter Array (ALMA)
(Tollefson et al. 2019). The mm and cm probe between _∼_ 1 _−_ 50 bar on Neptune, meaning the most complete picture
of Neptune’s upper atmosphere to date can be reconstructed by synthesizing these data. As NASA and ESA debate
the merits of a next-decade ice giant mission, a firm handle on the uncertainties in the composition and dynamics of
Neptune’s upper atmosphere are critical (Hofstadter et al. 2019). Just how well are the quantities of N, S, C, P,
and O constrained from ground-based observations, in-situ, and orbital measurements, and how does the amount and
distribution of condensibles affect the observed atmospheric dynamics (Atreya et al. 2019; Hueso & S´anchez-Lavega
2019; Fletcher et al. 2020)? Do our uncertainties on these elements necessitate an instrument like _Juno_ ’s Microwave
Radiometer (MWR) (Janssen et al. 2017) on a future spacecraft to Neptune (Rymer et al. 2020)? What bands
and configurations would be most useful for Neptune atmospheric science with the next generation VLA (ngVLA) and
could it replace an MWR equivalent?
This paper is organized as follows. First, we present longitudinal-smeared maps of Neptune taken with the expanded
VLA in 2015 between 0 _._ 9 _−_ 9 _._ 7 cm (Section 2). Next, we outline the structure of Neptune’s upper atmosphere and the
free parameters used in our modeling (Section 3). We then combine these new VLA maps with 2003 VLA and ALMA
observations of Neptune and use a Markov chain Monte Carlo (MCMC) implementation of the radiative transfer
code Radio BErkeley Atmospheric Radiative transfer (Radio-BEAR) to obtain retrievals for the abundance profiles
of Neptune’s condensibles (Section 4). Finally, we compare our findings to prior results (Section 5) and end with a
summary of key takeaways (Section 6).


2. OBSERVATIONS


2.1. _Data_


_−_
This work makes use of two primary data sets: 1) ALMA millimeter observations of Neptune taken from 2016 2017,
described in Section 2 of Tollefson et al. (2019); 2) centimeter observations of Neptune taken with the upgraded VLA
taken in 2015, described below.
We observed Neptune with the expanded VLA, an interferometer located near Socorro, New Mexico, on 1 and 2
September, 2015. Maps were obtained at wavelengths of 0.9 cm (Band Ka), 2.0 cm (Band Ku), 3.0 cm (Band X),
5.1 cm (Band C), and 9.7 cm (Band S). The VLA consists of 27 antennas grouped into three arms of nine antennae
to form a ‘Y’-shape. Every four months, the configuration is changed by moving the antennae along tracks. The
‘A’ configuration is the VLA’s most extended; the length of each arm is _∼_ 21 km, forming a maximum baseline of
_∼_ 36 km. The maximum baseline is inversely related to the angular resolution, i.e. beam size, meaning variations
across Neptune’s disk are most distinct in the A configuration. The observation setup strongly impacts the shape of
the beam. The symmetry of the VLA three-armed track, Neptune’s low declination at the time of the observation,
and extended time on source causing the uv-plane sampling to fill out due to Earth’s rotation all contribute to the
beams’ shapes. [1] Neptune was observed on two days, each for 7 hours divided into many 5 minute scans which rotate
through all wavelength bands. Thus, the degree of longitudinal smearing is high in the resulting maps as we observe


1 Further information on the various VLA configurations can be found in the VLA guides for proposers, Section 2: [https://science.nrao.](https://science.nrao.edu/facilities/vla/docs/manuals/propvla/referencemanual-all-pages)
[edu/facilities/vla/docs/manuals/propvla/referencemanual-all-pages.](https://science.nrao.edu/facilities/vla/docs/manuals/propvla/referencemanual-all-pages) An introduction to radio astronomy fundamentals is available online via the Socorro Imaging Synthesis Workshop at [https://science.nrao.edu/science/meetings/2018/16th-synthesis-imaging-workshop/](https://science.nrao.edu/science/meetings/2018/16th-synthesis-imaging-workshop/16th-synthesis-imaging-workshop-lectures)
[16th-synthesis-imaging-workshop-lectures](https://science.nrao.edu/science/meetings/2018/16th-synthesis-imaging-workshop/16th-synthesis-imaging-workshop-lectures)

3


**Table** **1.** Summary of VLA observations.


Wavelength (cm) Frequency (GHz) Band Beam Size (arcsec [2] ) Resolution (km [2] ) _[a]_ Time on Source (min)


0.9 32.958 Ka 0 _._ 12 _×_ 0 _._ 12 2 _,_ 486 _×_ 2 _,_ 486 156.0

2.0 14.880 Ku 0 _._ 25 _×_ 0 _._ 25 5 _,_ 179 _×_ 5 _,_ 179 136.8

3.0 9.869 X 0 _._ 35 _×_ 0 _._ 26 7 _,_ 251 _×_ 5 _,_ 387 139.8

5.1 5.861 C 0 _._ 56 _×_ 0 _._ 45 11 _,_ 603 _×_ 9 _,_ 324 82.8

9.7 3.096 S 0 _._ 98 _×_ 0 _._ 79 20 _,_ 305 _×_ 16 _,_ 369 82.2


_a_ Resolution at sub-observer location, assuming equatorial and polar radii of 24,766 km and 24,323 km, respectively (Lindal 1992).


Neptune throughout nearly an entire 16.11 hr rotation period (Warwick et al. 1989). Table 1 lists a summary of our
observations.
We supplement these observations with VLA maps in 2003 from de Pater et al. (2014) in order to model Neptune’s
disk-average temperature. These observations were taken in 5 bands for a total of 8 hours in each wavelength, including
calibrators. Three of these bands (2 cm, Ku; 3.6 cm, X; 6 cm, C) were also taken in the ‘A’ configuration while the
other 2 (0.7 cm, Q; 1.3 cm, K) were taken in the ‘BnA’ configuration, which is a hybrid of the B and A configurations,
and was ideal for imaging Neptune at low declination.


2.2. _Calibration_ _and_ _Imaging_


The VLA observations were loaded from the NRAO data archive and converted for use in the MIRIAD software
package (Sault et al. 1995). Flagging, calibration, and imaging were performed within MIRIAD. The calibrators used
were 3C48 (flux density) and J2246-1206 (phase). In addition, self-calibration was performed to correct for short-term
variability in the phases caused by fast atmospheric fluctuations. The self-calibration model used was a limb-darkened
disk that best matched the observations. The limb-darkened profile is represented by the peak brightness temperature
_T_ _b_ multiplied by cos _[k]_ _θ_, where _θ_ is the emission angle and _k_ is a limb-darkening constant. Values for _T_ _b_ and _k_ were found
at each wavelength such that the difference between the limb-darkened model disk and observations were minimized.
Our final longitudinally-smeared maps after subtracting the limb-darkened disk of Neptune are shown in Figure
1. While the images are ‘longitudinally-smeared’, pixel-to-pixel variations are still present on the disk due to the
presence of artifacts on the order of the beam size. Figure 2 plots the observed brightness temperature and residuals
versus latitude along the central meridian of each disk. We divide Neptune into seven regions where the transitions
in the brightness temperature variations are apparent: 90 _[◦]_ S _−_ 66 _[◦]_ S, 66 _[◦]_ S _−_ 50 _[◦]_ S, 50 _[◦]_ S _−_ 36 _[◦]_ S, 36 _[◦]_ S _−_ 12 _[◦]_ S, 12 _[◦]_ S _−_ 4 _[◦]_ N,
4 _[◦]_ N _−_ 20 _[◦]_ N, 20 _[◦]_ N _−_ 50 _[◦]_ N.


2.3. _Error_ _estimation_


The random noise in our VLA maps is calculated by averaging over four regions of the sky with boxes equal to the
diameter of Neptune and taking the root-mean-square (RMS). RMS values range from 0 _._ 4 _−_ 2 _._ 0K and are similar to
the RMS at a given latitude within the disk of a residual map. Table 2 lists our estimated errors in each band. The
RMS does not include systematic effects, such as errors in the bandpass or flux calibration. Uncertainties in the flux
density are estimated at 5% or less in each band so we use this as a conservative estimate for the absolute error in our
disk-averaged temperature data.


3. MODELING


We generate models of Neptune’s brightness temperature using the radiative transfer (RT) code Radio-BEAR [2] .
Radio-BEAR generates synthetic spectra by solving the equation of radiative transfer through a model atmosphere.
For a fuller description of Radio-BEAR, we refer the reader to de Pater et al. (2005), de Pater et al. (2014), and de
Pater et al. (2019), which outline how the model atmosphere is constructed from bottom-up and details the absorption
coefficients and line profiles for the species in this work. A description of the temperature profiles, cloud structure,
and compositions considered in the model atmosphere is given below.


3.1. _Temperature_ _Profile_


2 This code is available at: [https://github.com/david-deboer/radiobear](https://github.com/david-deboer/radiobear) .

4

5



250


225


200


175


150


125


100


75


50







30



20





10


0


10


-90 -75 -60 -45 -30 -15 0 15 30 45
Latitude (deg)


**Figure** **2.** Neptune’s observed brightness temperature (top panel) and residual temperature (bottom panel) versus latitude
along the sub-observer longitude for each wavelength band (colored lines). The residual temperatures are taken from the residual
maps shown in Fig. 1 and are obtained by subtracting the observed brightness temperatures from best-fitting uniform limbdarkened disks, as described in in Section 2.2 Dashed black lines delineate regions where brightness temperature variations are
evident and define the latitude bins used in our modeling. Lines may not extend to 90 _[◦]_ S due to limits in the resolution of the
observation. The bump in the residual temperature at 9.7 cm is due to the poor resolution, as the large beam size impacts the
limb-darkened fit.


Temperature profiles are calculated from deep in the atmosphere upward, assuming either a dry or wet adiabat
such that the profile matches the _Voyager_ 2 temperature of 71.5 K at 1 bar (Lindal 1992). At pressures shallower
than 1 bar, the temperature profile follows that derived from mid-infrared inversions by Fletcher et al. (2014).
Temperatures, pressures, and altitudes are related through hydrostatic equilibrium. We assume that the atmosphere
is in local thermodynamic equilibrium.
Figure 3 plots the wet and dry temperature profiles used in this paper. These are derived from a ‘nominal’ atmosphere
with 30 _×_ protosolar abundances of H 2 S, CH 4, and H 2 O, with 1 _×_ NH 3, no PH 3, ‘intermediate’ H 2 (see: Sec. 3.5),
and 100% relative humidity for each condensible species [3] . Figure 3 also plots the nominal abundances of Neptune’s
condensibles.


3.2. _Cloud_ _Structure_


The condensibles in Neptune’s upper atmosphere are H 2 S, CH 4, H 2 O, and NH 3, all of which may condense to form
clouds. Clouds expected to form on Neptune, from bottom-up, include: an aqueous ammonia solution (H 2 O-NH 3 -H 2 S),
water-ice, ammonium hydrosulfide (NH 4 SH), H 2 S- or NH 3 -ice (whichever is left over after NH 4 SH formation), and CH 4 ice (Weidenschilling & Lewis 1973; Atreya & Wong 2005). The cloud density may affect microwave measurements.


3 We use the protosolar values from Asplund et al. (2009): C/H 2 = 5.90E-4; N/H 2 = 1.48E-4; O/H 2 = 1.07E-3; S/H 2 = 2.89E-5.

6




|Pressure(bar)<br>100 10 0.1<br>0.00 1<br>Normalized a)<br>0.25<br>Weighting 0.50<br>0.75<br>Function<br>9.7 5.1 3.0 2.0 0.9 0.3 0.2 0.1<br>1.00<br>cm cm cm cm cm cm cm cm<br>100 10 0.1<br>10 1<br>8 b)<br>Cloud 10<br>6<br>Density<br>10<br>(g/cc) 4 Solution H2O-ice NH4SH H2S-ice CH4-ice<br>10<br>Cloud<br>2<br>100 10 0.1<br>10 1<br>8 c)<br>10<br>Mixing<br>6<br>10<br>Ratio<br>4<br>10<br>H2O NH3 H2S CH4<br>2|Col2|Pres<br>100<br>10|sure(bar)<br>1|0.1 a)|
|---|---|---|---|---|
|0.00<br>0.25<br>0.50<br>0.75<br>1.00<br>Normalized Weighting Function<br>0.1<br>1<br>10<br>100<br>Pressure (bar)<br>a)<br>0.1 cm<br>0.2 cm<br>0.3 cm<br>0.9 cm<br>2.0 cm<br>3.0 cm<br>5.1 cm<br>9.7 cm<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Cloud Density (g/cc)<br>0.1<br>1<br>10<br>100<br>b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Mixing Ratio<br>0.1<br>1<br>10<br>100<br>c)<br>CH4<br>H2S<br>NH3<br>H2O|||3.0 cm<br>5.1 cm<br>9.7 cm|a)|
|0.00<br>0.25<br>0.50<br>0.75<br>1.00<br>Normalized Weighting Function<br>0.1<br>1<br>10<br>100<br>Pressure (bar)<br>a)<br>0.1 cm<br>0.2 cm<br>0.3 cm<br>0.9 cm<br>2.0 cm<br>3.0 cm<br>5.1 cm<br>9.7 cm<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Cloud Density (g/cc)<br>0.1<br>1<br>10<br>100<br>b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Mixing Ratio<br>0.1<br>1<br>10<br>100<br>c)<br>CH4<br>H2S<br>NH3<br>H2O|||3.0 cm<br>5.1 cm<br>9.7 cm|0.1 cm<br>0.2 cm<br>0.3 cm<br>0.9 cm<br>2.0 cm<br>|
|0.00<br>0.25<br>0.50<br>0.75<br>1.00<br>Normalized Weighting Function<br>0.1<br>1<br>10<br>100<br>Pressure (bar)<br>a)<br>0.1 cm<br>0.2 cm<br>0.3 cm<br>0.9 cm<br>2.0 cm<br>3.0 cm<br>5.1 cm<br>9.7 cm<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Cloud Density (g/cc)<br>0.1<br>1<br>10<br>100<br>b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Mixing Ratio<br>0.1<br>1<br>10<br>100<br>c)<br>CH4<br>H2S<br>NH3<br>H2O||10<br>100|1|1|
|0.00<br>0.25<br>0.50<br>0.75<br>1.00<br>Normalized Weighting Function<br>0.1<br>1<br>10<br>100<br>Pressure (bar)<br>a)<br>0.1 cm<br>0.2 cm<br>0.3 cm<br>0.9 cm<br>2.0 cm<br>3.0 cm<br>5.1 cm<br>9.7 cm<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Cloud Density (g/cc)<br>0.1<br>1<br>10<br>100<br>b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Mixing Ratio<br>0.1<br>1<br>10<br>100<br>c)<br>CH4<br>H2S<br>NH3<br>H2O|||b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud|b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud|
|0.00<br>0.25<br>0.50<br>0.75<br>1.00<br>Normalized Weighting Function<br>0.1<br>1<br>10<br>100<br>Pressure (bar)<br>a)<br>0.1 cm<br>0.2 cm<br>0.3 cm<br>0.9 cm<br>2.0 cm<br>3.0 cm<br>5.1 cm<br>9.7 cm<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Cloud Density (g/cc)<br>0.1<br>1<br>10<br>100<br>b)<br>CH4-ice<br>H2S-ice<br>NH4SH<br>H2O-ice<br>Solution Cloud<br>10<br>8<br>10<br>6<br>10<br>4<br>10<br>2<br>Mixing Ratio<br>0.1<br>1<br>10<br>100<br>c)<br>CH4<br>H2S<br>NH3<br>H2O|c)<br>CH4<br>H2S<br>NH3<br>H2O|c)<br>CH4<br>H2S<br>NH3<br>H2O|c)<br>CH4<br>H2S<br>NH3<br>H2O|c)<br>CH4<br>H2S<br>NH3<br>H2O|
|4<br> atio|4<br> atio|4<br> atio|4<br> atio|4<br> atio|
|10<br>2<br>|10<br>2<br>|10<br>2<br>|10<br>2<br>|10<br>2<br>|


|00|10 00|.1 1 10|
|---|---|---|
||||
|d)<br>Dry Adiabat<br>Wet Adiabat|d)<br>Dry Adiabat<br>Wet Adiabat|d)<br>Dry Adiabat<br>Wet Adiabat|

7


**Table** **2.** Summary of observed and modeled millimeter disk-averaged brightness temperatures.


Center Frequency (GHz) Facility UT Date Observed T _[a]_ b [(][K][)] Wet Disk Model T _[b]_ b [(][K][)] Noise _[c]_ (K)


3.096 VLA 02-Sep-2015 238 _._ 6 _±_ 11 _._ 5 223.8 1.3

4.915 VLA 28-Jun-2003 215 _._ 1 _±_ 10 _._ 8 206.7 –

5.861 VLA 01-Sep-2015 214 _._ 3 _±_ 10 _._ 9 199.6 0.6

8.328 VLA 27-Jun-2003 183 _._ 3 _±_ 9 _._ 2 184.2 –

9.869 VLA 01-Sep-2015 177 _._ 2 _±_ 8 _._ 9 177.7 0.4

14.880 VLA 01-Sep-2015 153 _._ 3 _±_ 7 _._ 7 161.4 0.7

14.990 VLA 26-Jun-2003 169 _._ 7 _±_ 8 _._ 5 161.1 –

23.061 VLA 11-Oct-2003 150 _._ 6 _±_ 7 _._ 5 148.6 –

32.958 VLA 01-Sep-2015 158 _._ 1 _±_ 7 _._ 9 141.7 2.0

42.827 VLA 12-Oct-2003 147 _._ 4 _±_ 7 _._ 4 138.0 –

95.012 ALMA 07-Jul-2017 126 _._ 6 _±_ 6 _._ 3 121.6 0.1

96.970 ALMA 07-Jul-2017 126 _._ 0 _±_ 6 _._ 3 121.0 0.1

107.000 ALMA 07-Jul-2017 120 _._ 5 _±_ 6 _._ 0 117.9 0.2

109.000 ALMA 07-Jul-2017 118 _._ 8 _±_ 6 _._ 0 116.7 0.3

135.986 ALMA 08-Oct-2016 108 _._ 5 _±_ 5 _._ 4 105.8 0.3

137.924 ALMA 08-Oct-2016 108 _._ 0 _±_ 5 _._ 4 105.2 0.2

147.986 ALMA 08-Oct-2016 104 _._ 3 _±_ 5 _._ 2 102.7 0.2

149.986 ALMA 08-Oct-2016 104 _._ 5 _±_ 5 _._ 2 102.3 0.3

223.982 ALMA 24-Oct-2016 93 _._ 4 _±_ 4 _._ 7 92.1 0.4

225.982 ALMA 24-Oct-2016 93 _._ 0 _±_ 4 _._ 7 91.9 0.4

239.981 ALMA 24-Oct-2016 93 _._ 1 _±_ 4 _._ 7 90.0 0.6

241.981 ALMA 24-Oct-2016 92 _._ 8 _±_ 4 _._ 6 89.8 0.6

_a_ The listed errors are the absolute errors, estimated at 5% from the calibrators.
_b_ The model brightness temperatures from the best-fitting wet adiabat MCMC retrievals.
_c_ Random errors defined as the RMS on the sky RMS errors are not available for the VLA 2003 data.


However, little is known about the cloud density on Neptune and clouds have been shown to not affect the microwave
opacity on Jupiter (de Pater et al. 2019). Therefore, we ignore the effect of cloud opacity in our modeling and focus
instead on the effect of gas opacity.


3.3. _Condensible_ _Species_


The gas opacity of the microwave spectrum for gas giant atmospheres is dominated by H 2 S, NH 3, H 2 O, and the
collision-induced absorption (CIA) of H 2 (we include: H 2 -H 2, H 2 -He, and H 2 -CH 4 ) (de Pater & Mitchell 1993). To
form the NH 4 SH cloud, H 2 S and NH 3 are reduced in equal molar quantities until the product of their partial pressures
reaches the equilibrium constant of the reaction forming NH 4 SH. On Uranus and Neptune, the observation that NH 3
is absent while H 2 S is present above the NH 4 SH layer (de Pater et al. 1991; Irwin et al. 2018, 2019a; Molter et
al. 2020) implies that this process takes up all of the NH 3, leaving an excess of H 2 S gas above the layer. Therefore,
while NH 3 and H 2 O are strong microwave absorbers, they are only abundant deeper than _∼_ 40 bar and only impact
Neptune’s radio spectrum significantly at wavelengths longer than 10 cm. This is shown in Figure 3, which plots the
normalized weighting functions at each observed wavelength assuming a nominal atmosphere. Our ALMA and VLA
observations, with wavelengths shorter than 10 cm, are sensitive to pressures between 1 _−_ 50 bar, peaking at altitudes
at and above the aqueous NH 3, H 2 O-ice, and NH 4 SH cloud formations. While NH 3 can not be probed directly with
our wavelength coverage, the chemical connection between H 2 S and NH 3 means its abundance can be inferred. We
therefore allow the NH 3 profile to vary unlike in Tollefson et al. (2019). In our model, the formation of the NH 4 SH
cloud is governed by equilibrium chemistry described in Lewis (1969).
Our forward models allow the ‘deep’ abundances of gaseous H 2 S, NH 3, and CH 4 to vary. We define ‘deep’ as pressures
below the NH 4 SH cloud (forming at _∼_ 50 bar) but above aqueous solution cloud formation ( _P_ _>_ 100 bar). For the
nominal abundances, the solution cloud in full thermochemical equilibrium removes about 5% of the interior H 2 S and
25% of the interior NH 3 . From our retrieved values of ‘deep’ H 2 S and NH 3, we obtain abundances below all cloud

8


formation. We set no _a_ _priori_ restriction on the ‘deep’ H 2 S or NH 3 abundance, meaning either may survive above
NH 4 SH formation. H 2 S or NH 3, whichever persists, will then form an ice cloud and we allow its relative humidity to
vary (see Fig. 3, which shows H 2 S-ice forming, as the ‘deep’ H 2 S abundance is larger than that of NH 3 ).


3.3.1. _Phosphine_ _(PH_ 3 _)_


PH 3 is an important disequilibrium species on giant planets, tracing both chemistry and convective motion. In
the deep atmosphere, PH 3 should oxidize to form P 4 O 6 and dissolve in water (Fegley & Prinn 1986). In the upper
atmosphere, PH 3 is photolyzed and subsequent photochemical reactions may form to produce P 4 or complex polymers
an compounds. Thus, PH 3 must be rapidly uplifted from the deep atmosphere to exist, making it useful as a passive
tracer for both horizontal and vertical motions (Fegley & Prinn 1986; Fletcher et al. 2009).
PH 3 has not been detected on Uranus or Neptune, but if present is an important microwave absorber (DeBoer &
Steffes 1996). The effect is most prominent at the PH 3 (1 _−_ 0) rotation line at 266.9 GHz. The radio observations
analyzed here only reach frequencies as high as 242 GHz (ALMA Band 6), meaning only the wings of the absorption
line are detectable. However, if the abundance of PH 3 is large enough, the pressure-broadened rotation line will be
detectable in our highest frequency data. Thus, upper limits on the uplifted PH 3 abundance can be placed.
Our forward model assumes a constant PH 3 abundance until the temperature and pressure become so low that PH 3
condenses ( _∼_ 1 bar). We also only include PH 3 in our retrievals at latitudes where we expect upwelling and enriched
condensibles, i.e. latitudes with comparatively cold brightness temperatures.


3.4. _ortho/para_ _H_ 2


The ortho-/para-H 2 fraction also influences Neptune’s radio brightness temperature by modifying both the adiabatic
lapse rate and the gas opacity (Trafton 1967; Wallace 1980; de Pater & Massie 1985; de Pater & Mitchell 1993).
The ratio of ortho- to para-hydrogen in equilibrium depends on temperature; however, fast vertical mixing could bring
the ratio of ortho and para states of hydrogen away from equilibrium and toward a “normal” ratio of three parts ortho
to one part para. At latitudes where fast vertical mixing is unlikely, H 2 is presumed to exist in an “intermediate”
state, proposed by Trafton (1967). In this case, the ortho and para states (which define the CIA properties) are
set to the equilibrium value at the local temperature while the specific heat is set near that of “normal” hydrogen.
“Intermediate” hydrogen is discussed further in Massie & Hunten (1982), who provide physical reasons for the choice
of this “intermediate” state. “Normal” hydrogen has been shown to decrease the microwave brightness temperature
relative to “intermediate” hydrogen (de Pater & Mitchell 1993; Luszcz-Cook et al. 2013a; Tollefson et al. 2019).
In our retrievals, we parameterize the state of H 2 as between 0.0 and 1.0, where 0.0 represents the fully “normal”
state while 1.0 is fully “intermediate.” Values in between represent a weighted average of the absorption coefficient
between the two states. The specific heat is always set near to that of “normal” hydrogen, regardless of the parameter

state.


3.5. _Retrievals_


In order to estimate uncertainties in our model parameters, we couple our Radio-BEAR models to Markov Chain
Monte Carlo (MCMC) simulations via a python implementation of the Goodman & Weare (2010) ensemble sampler
called _emcee_ (Foreman et al. 2013). _emcee_ has been used in near-infrared analyses of Uranus’ and Neptune’s hazes (de
Kleer et al. 2015; Luszcz-Cook et al. 2016). We use similar log-likelihood Gaussian function and uniform/log-uniform
priors as these authors; letting _θ_ represent the free parameters in the model, the likelihood function ln _p_ is:



2
+ ln �2 _πσ_ _n_ [2] �
� �



ln _p_ ( _T_ _b_ _|ν, θ, σ_ ) = _−_ 0 _._ 5 �


_ν_ _n_



_T_ _b,n_ _−_ _T_ _b,m_

_σ_ _n_
��



_,_ (1)



where _T_ _b,n_ is the observed brightness temperature, _T_ _b,m_ is the RT modeled brightness temperature, and _σ_ _n_ is the
total uncertainty, all at a given wavelength _ν_ . This approach is in contrast to the methods in Tollefson et al.
(2019) who compared the ALMA data to forward models of Neptune’s atmosphere. From these forward models, they
obtained deep abundances of H 2 S and CH 4 that fit the latitudinally-varying brightness temperatures. A downside to
this approach is that one can only rule out models which are improbable from _χ_ [2] -statistics, meaning uncertainties are
not retrieved.

We use 30 walkers and let MCMC run for between 4000 _−_ 5000 steps. This run length ensured that the autocorrelation
time was sufficiently shorter than the number of steps. All plots and tables show the distributions after burn-in, where

9



20


10


0


10


20


30


40


50


60









40


20


0


20


40


60


80





15


10


5


0


5


10


15






|H2S Deep|Col2|
|---|---|
|0.5x S<br>5.0x S<br>15.0x S<br>50.0x S<br>150.0x S||


|NH3 Deep|Col2|
|---|---|
|0.01x S<br>0.1x S<br>0.5x S<br>5.0x S<br>10.0x S||


|CH4 Deep|Col2|
|---|---|
|0.5x S<br>5.0x S<br>15.0x S<br>50.0x S<br>150.0x S||









15


10


5


0


5


10


15









15


10


5


0


5


10


15







15


10


5


0


5


10


15






|.1 1 10 Wavelength (cm)|Col2|
|---|---|
|H2S Relative Humidity||
|0.1%<br>1.0%<br>10.0%<br>50.0%<br>75.0%||


|1 1 10 Wavelength (cm)|Col2|
|---|---|
|PH3 Mole Fraction||
|1e-10<br>1e-09<br>1e-08<br>1e-07<br>1e-06||


|1 1 10 Wavelength (cm)|Col2|
|---|---|
|H2 State||
|0.0<br>0.25<br>0.5<br>0.75<br>0.9||



0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



**Figure** **4.** The effect of changing modeled parameters on Neptune’s disk-averaged microwave spectrum following a wet adiabat.
Each panel shows how varying only the listed parameter from the nominal atmosphere alters the disk-averaged spectrum. ∆ _T_ _b_
is the difference from the nominal spectrum, with colored lines representing different values of the varied parameter. Positive
∆ _T_ _b_ values mean that the new model is warmer than the nominal model. The deep H 2 S, NH 3, and CH 4 abundances are given
in terms of their protosolar enhancements (top row). The relative humidity of H 2 S at its ice-cloud formation, the mole fraction
of PH 3, and the H 2 state (defined in section 3.4) are also (bottom row). Interesting behavior is seen in the deep H 2 S panel, as
both large and small amounts of H 2 S (0.5 _×_ protosolar, blue vs. 150 _×_ protosolar, yellow) produce negative ∆ _T_ _b_ longward of 1
cm, while only depleted amounts of H 2 S result in positive ∆ _T_ _b_ in the millimeter, relative to the nominal model. These trends
are explained in Section 3.6. The central wavelengths of our maps are plotted with black points. The error bars represent the
calibration errors to give a sense of how important each parameter is in fitting the model to the data.


the range of retrieved values approximately appear like their final probability density. The burn-in phase ends after
50% of the steps have been completed.
Observed and modeled brightness temperatures are obtained in each of the identified latitude bins listed in Section
2.2. One issue with RT models of particular regions on Neptune is that the finite size of the point-spread function (PSF)
results in blurring of the disk. That is, the temperature within a particular latitude bin is a convolution of that latitude
region, nearby latitudes, and sometimes the background sky. This effect is hard to model while conducting MCMC
for two reasons: convolving the whole disk with the PSF is computationally expensive; and the model composition of
the surrounding latitudes must be simultaneously known in order to obtain the exact temperature distribution across
the disk. We circumvent this issue in two steps. First, we generate limb-darkened model disks of the best-fitting
disk-averaged models (see Section 4.1) and then determine the brightness temperature in the region of interest with
and without convolving the disk with the PSF. The ratio of the PSF convolved disk-averaged model temperature to
that without convolution is called the PSF-scale. We multiply each MCMC retrieved model by the PSF-scale to obtain
our final model brightness temperature incorporating the effect of convolution. This model temperature is fed into the
_emcee_ likelihood function. The effect of this scaling is smallest near the center of the disk and largest near the limb.
Second, we add an error term to account for the uncertainty introduced by this approach,


_σ_ _T_ [2] [=] _[ σ]_ _CAL_ [2] [+] _[ σ]_ _P SF_ [2] _[,]_ (2)


where _σ_ _T_ is the total error term used by _emcee_ to calculate the likelihood function, _σ_ _CAL_ is the 5% calibration error
and _σ_ _P SF_ is the error introduced by RT-modeling not accounting for the PSF. In our MCMC retrievals, we define an
additional free parameter, _σ_, that is proportional to _σ_ _P SF_ :

10


_σ_ _P SF_ = _σ · T_ _· S,_ (3)


where _T_ is the observed brightness temperature and _S_ is the product of the beam’s semi-major and semi-minor axes.
Adding an extra free parameter in the uncertainty is general practice in MCMC, as it encompasses unknown sources
of error (for instance, via the introduction of PSF-scale). We find that the maximum retrieved values of _σ_ _P SF_ are
never larger than 5% of the product of _T_ and _S_ at disk center and 15% at the limb.


3.6. _Atmospheric_ _Models_ _and_ _Free_ _Parameters_


We consider four types of atmospheric models for these retrievals, depending on the latitude bin and expected
dynamics, described below. Table 3 lists each of these models and the allowed free parameters. Figure 4 summarizes
the effect of altering these parameters on the disk-averaged microwave spectrum of Neptune relative to the nominal
model. Of note, the first two panels highlight the strong interaction between the deep H 2 S and NH 3 abundances as a
function of wavelength. NH 3 can exceed H 2 S, resulting in NH 3 surviving NH 4 SH cloud formation, by either sufficiently
depleting H 2 S (blue line, 0.5 _×_ S, in the H 2 S deep panel) or enriching NH 3 (yellow line, 10 _×_ S, in the NH 3 deep panel).
The millimeter spectrum becomes brighter, as more NH 3 will reacts with more H 2 S at NH 4 SH formation, thereby
reducing the total amount of H 2 S above it. On the other hand, the centimeter spectrum becomes colder, as NH 3
gas is a stronger microwave absorber than H 2 S gas. All other parameters have the strongest impact at _λ_ _≤_ 1 cm.
Note, however, that our ability to retrieve the deep CH 4 abundance is limited compared to that of H 2 S. This is due
to a combination of having less overall impact on the microwave opacity, lower than our calibration errors, and other
sources like the H 2 S relative humidity, PH 3, and the H 2 state having comparable or stronger effects in the mm. The
considered models are:


1. Enriched Atmosphere: Used for latitude bands which have relatively cold brightness temperatures, where enriched
and upwelling air is expected. The ‘deep’ [4] abundances of of H 2 S, NH 3, and CH 4 are allowed to vary. The NH 4 SH,
H 2 S-ice and CH 4 -ice clouds are allowed to form and the relative humidity of H 2 S is varied. The PH 3 abundance
is allowed to vary; a uniform vertical profile is assumed up to the saturation pressure of PH 3 . The ortho- to paraH 2 fraction is allowed to vary between 0 _._ 0 _−_ 1 _._ 0, representing the range of fully ‘normal’ to fully ‘intermediate’
states. Both dry and wet adiabats are considered.


2. Depleted Atmosphere: Used for latitude bands which have relatively warm brightness temperatures, where
depleted and downwelling air is expected. The ‘deep’ abundance of condensibles is set to that of the enriched
atmosphere at altitudes below the ‘mixing pressure:’ _P_ mix . At shallower altitudes, the abundance of condensibles
is varied by some fraction of the deep abundance. The final profiles for the condensibles look like step functions,
with the transition at _P_ mix . We allow the formation of H 2 S- and NH 3 -ice. Both dry and wet adiabats are
considered.


3. Disk Average: The disk-averaged model for the atmosphere looks like that of the enriched, but we only let
the ‘deep’ abundances of H 2 S, NH 3, and CH 4, and the relative humidity of H 2 S to vary. This model is done to
compare to prior work and so both PH 3 and the H 2 state are not varied. We caution that disk-averaged retrievals
poorly describe the physics within the planet. Both dry and wet adiabats are considered.


4. Standard: At other latitudes not fitting the above prescriptions, we model the atmosphere similar to the
enriched atmosphere as it follows standard cloud formation and thermochemical equilibrium unlike the depleted/downwelling atmosphere. Unlike the ‘Enriched’ model, the PH 3 abundance and ortho/para H 2 state are
not allowed to vary. Both dry and wet adiabats are considered.


4. RESULTS


4.1. _Disk-Averaged_ _Profiles_


We calculate Neptune’s disk-average brightness temperature by totaling the flux density contained within Neptune’s
disk plus the area extending out three times the model beam diameter past the limb. The apparent brightness


4 Again, ‘deep’ is defined as pressures above the H 2 O and aqueous solution clouds and below the NH 4 SH cloud.

11

12

|Disk Average Wet Adiabat<br>,|Col2|Col3|
|---|---|---|
|Parameter|Retrieved values|Protosolar Enhancement (_×_ Solar)|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>H2S _H_rel|6_._3+1_._9<br>_−_1_._2 _×_ 10_−_4<br>_≤_6_._5_ ×_ 10_−_4<br>_≤_1_._6_ ×_ 10_−_2<br>_≤_18%|26_._8+8_._1<br>_−_5_._1<br>_≤_5_._4<br>_≤_33_._3<br>—|
|H2S below all clouds|6_._6+2_._0<br>_−_1_._3 _×_ 10_−_4|28_._2+8_._5<br>_−_5_._4|
|Disk Average, Dry Adiabat|Disk Average, Dry Adiabat|Disk Average, Dry Adiabat|
|Parameter|Retrieved values|Protosolar Enhancement|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>H2S _H_rel|8_._8+2_._0<br>_−_2_._1 _×_ 10_−_4<br>Unconstrained<br>_≤_1_._3_ ×_ 10_−_2<br>_≤_75%|37_._5+9_._4<br>_−_8_._9<br>Unconstrained<br>_≤_27_._1<br>—|
|H2S below all clouds|9_._3+2_._1<br>_−_2_._2 _×_ 10_−_4|39_._4+9_._9<br>_−_9_._4|



**Table** **4.** MCMC fit results for the disk-average models. The listed H 2 S abundances below NH 4 SH cloud formation are the
50th percentile of the posterior distributions with the error bars corresponding to the 16th and 84th percentiles, i.e. the 1 _σ_
uncertainties. NH 3, CH 4, and the relative humidity of H 2 S are not well-constrained in either model and so the 97.5th percentile
value, representing the 2 _σ_ upper limit, is given instead. Abundances below all cloud formation are estimated according to the
discussion in Section 3.3


temperature measured in interferometric imaging is less than the true value by an amount related to the cosmic
microwave background (CMB). The CMB correction is applied following the procedure laid out in Appendix A of de
Pater et al. (2014). These results are combined with measurements of Neptune’s disk-average brightness temperature
from VLA 2003 (de Pater et al. 2014) and ALMA (Tollefson et al. 2019) to form our set of data used in MCMC
retrievals. A summary of this data set is given in Table 2.
Figure 5 plots the best-fitting H 2 S and NH 3 profiles and 500 random retrieved profiles from the posterior distribution
for a wet adiabat. Figure 5 also shows the observed disk-averaged brightness temperatures versus wavelength, likewise
plotting the best-fitting and 100 random retrieved model spectra assuming a wet adiabat. Table 4 lists the retrieved
parameters. H 2 S is more abundant than NH 3 in both the dry and wet thermal profiles. There is also significant positive
correlation between the deep NH 3 and H 2 S abundances. This is expected based on the NH 4 SH cloud chemistry;
retrievals with larger NH 3 require additional H 2 S to remove the NH 3 during the NH 4 SH reaction to match the
observations probing above the NH 4 SH cloud. The dry adiabat permits marginally larger abundances of all condensibles
throughout the upper atmosphere due to the need to increase the opacity in order to offset the higher temperatures.


4.2. _36_ _[◦]_ _S_ _−_ _12_ _[◦]_ _S_ _and_ _90_ _[◦]_ _S_ _−_ _66_ _[◦]_ _S_ _Profiles_


The latitude band between 36 _[◦]_ S _−_ 12 _[◦]_ S is dark in both the VLA maps presented here (Fig. 1) and ALMA residual
maps. Low brightness temperatures imply increased opacity from Neptune’s condensibles. Conversely, Neptune’s
south polar cap, between 90 _[◦]_ S _−_ 66 _[◦]_ S, is warm in both datasets, implying a lower abundance of condensibles. Due to
the lower abundance of condensibles, the peaks of the normalized weighting functions are deeper in the atmosphere
than for the nominal model (Fig. 3), meaning we are more sensitive to abundances of Neptune’s condensibles below
the NH 4 SH cloud at the south pole. As a result, we first obtain retrievals for the mixing pressure _P_ mix and abundances
of condensibles over the south polar cap. The retrieved probability density functions for the condensible abundances
below _P_ mix are then used as priors for the condensible abundance below the NH 4 SH cloud in the cold mid-latitude
band between 36 _[◦]_ S _−_ 12 _[◦]_ S. The atmospheric models and free parameters used for these bands are described in Table 3
and Section 3.6.

The brightness temperatures fed into MCMC are obtained by averaging over all pixels that are within _±_ 60 degrees
of the sub-observer longitude at each latitude band. Likewise, the modeled spectra are obtained using the average
emission angle within this zonal average. The uncertainty is dominated by the flux calibration error. _σ_ PSF is also
added to this uncertainty, though its effect is small compared to the calibration error.

13

























75









75





0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



**Figure** **5.** Top row: Best fitting H 2 S (thick green) and NH 3 (thick yellow) profiles for the disk-average wet (left) and dry (right)
adiabat models. Thin lines are 500 random retrieved profiles. Bottom row: Disk-averaged data from VLA 2003 (de Pater et al.
2014; black circles) and from ALMA and the upgraded VLA (this paper, white circles). The thick red line is the best fitting
spectrum following a wet (left) and dry (right) adiabat. Thin black lines are also plotted, representing 100 random draws from
the posterior.

14

|90◦S −66◦S Wet Adiabat<br>,|Col2|Col3|
|---|---|---|
|Parameter|Retrieved values|Protosolar Enhancement (_×_ Solar)|
|H2S below _P_mix<br>NH3 below _P_mix<br>H2S above _P_mix<br>NH3 above _P_mix<br>_P_mix|0_._3+15_._7<br>_−_0_._3 _×_ 10_−_4<br>2_._5+2_._1<br>_−_2_._1 _×_ 10_−_4<br>2_._7+9_._3<br>_−_2_._7 _×_ 10_−_7<br>3_._3+2_._8<br>_−_2_._2 _×_ 10_−_7<br>41+9<br>_−_7 bar|1_._3+65_._6<br>_−_1_._3<br>2_._1+1_._7<br>_−_1_._8<br>1_._2+3_._9<br>_−_1_._2 _×_ 10_−_2<br>2_._8+2_._3<br>_−_1_._9 _×_ 10_−_3<br>—|
|36_◦_S_−_12_◦_S, Wet Adiabat|36_◦_S_−_12_◦_S, Wet Adiabat|36_◦_S_−_12_◦_S, Wet Adiabat|
|Parameter|Retrieved values|Protosolar Enhancement (_×_ Solar)|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>H2S _H_rel<br>PH3<br>H2 State|8_._3+2_._5<br>_−_2_._3 _×_ 10_−_4<br>1_._9+2_._0<br>_−_1_._7 _×_ 10_−_4<br>_≤_4_._1_ ×_ 10_−_2<br>_≤_57%<br>_≤_8_._2_ ×_ 10_−_7<br>Unconstrained|35_._4+14_._9<br>_−_9_._8<br>1_._6+1_._7<br>_−_1_._4<br>_≤_85_._4<br>—<br>_≤_0_._2<br>—|
|H2S below all clouds<br>NH3 below all clouds|8_._7+2_._6<br>_−_1_._7 _×_ 10_−_4<br>2_._5+2_._7<br>_−_2_._3 _×_ 10_−_4|37_._3+15_._7<br>_−_10_._3<br>2_._1+2_._3<br>_−_1_._9|



**Table** **5.** MCMC results for the simultaneous fit to the 36 _[◦]_ S _−_ 12 _[◦]_ S and 90 _[◦]_ S _−_ 66 _[◦]_ S bands assuming a wet adiabat. The deep
abundances of H 2 S, NH 3, and CH 4, and _σ_ PSF are the same in each region. Otherwise, parameters are varied according to Table
3. The listed values are the 50th percentile of the posterior distributions with the error bars corresponding to the 16th and 84th
percentiles, i.e. the 1 _σ_ uncertainties. Parameters which are poorly constrained have their 97.5th percentile value listed instead,
representing the 2 _σ_ upper limit. Abundances below all cloud formation are estimated according to the discussion in Section 3.3

|90◦S −66◦S Dry Adiabat<br>,|Col2|Col3|
|---|---|---|
|Parameter|Retrieved values|Protosolar Enhancement (_×_ Solar)|
|H2S below _P_mix<br>NH3 below _P_mix<br>H2S above _P_mix<br>NH3 above _P_mix<br>_P_mix|3_._6+25_._4<br>_−_3_._3 _×_ 10_−_4<br>3_._8+2_._2<br>_−_2_._4 _×_ 10_−_4<br>7_._1+5_._9<br>_−_2_._8 _×_ 10_−_6<br>1_._6+3_._1<br>_−_1_._3 _×_ 10_−_7<br>33+6<br>_−_4 bar|15_._3+108_._3<br>_−_8_._9<br>3_._2+1_._8<br>_−_2_._1<br>3_._0+2_._5<br>_−_1_._0 _×_ 10_−_1<br>1_._3+2_._6<br>_−_1_._0 _×_ 10_−_3<br>—|
|36_◦_S_−_12_◦_S, Dry Adiabat|36_◦_S_−_12_◦_S, Dry Adiabat|36_◦_S_−_12_◦_S, Dry Adiabat|
|Parameter|Retrieved values|Protosolar Enhancement (_×_ Solar)|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>H2S _H_rel<br>PH3<br>H2 State|1_._2+0_._4<br>_−_0_._3 _×_ 10_−_3<br>3_._5+1_._9<br>_−_2_._8 _×_ 10_−_4<br>Unconstrained<br>46+31<br>_−_34%<br>_≤_4_._4_ ×_ 10_−_7<br>Unconstrained|51_._1+17_._1<br>_−_12_._7<br>2_._9+1_._6<br>_−_2_._3<br>—<br>—<br>_≤_0_._1<br>—|
|H2S below all clouds<br>NH3 below all clouds|1_._3+0_._4<br>_−_0_._3 _×_ 10_−_3<br>4_._7+2_._5<br>_−_3_._7 _×_ 10_−_4|53_._8+18_._0<br>_−_13_._4<br>3_._9+2_._1<br>_−_3_._1|



**Table** **6.** As Table 5, but assuming a dry adiabat in each region.


Data for Neptune’s latitudinal variations are not available in the VLA 2003 maps apart from those at the south polar
cap. We do not use these data as the temperatures reported in de Pater et al. (2014) are the maximum temperatures
within the south polar cap at each wavelength instead of the average.
Tables 5 and 6 list the 16th/50th/84th percentiles on the gas profile parameters for the simultaneous 36 _[◦]_ S _−_ 12 _[◦]_ S
and 90 _[◦]_ S _−_ 66 _[◦]_ S models. If a parameter is not well constrained, the 97.5th-percentile (2 _σ_ ) upper limit is given instead.
Corner plots showing the covariance and probability distribution for the free parameters are given in Figure 6, assuming
the temperature profile at the south polar cap follows a wet adiabat. As in the disk-average results, there is significant

90°S - 66°S (wet) 36°S - 12°S (wet)



log 10 CH 4



15


log 10 H 2 S RH



log 10 H 2 S
below _P_ _max_



log 10 H 2 S
above _P_ _max_



log 10 NH 3
above _P_ _max_



log 10 H 2 S
above NH 4 SH



log 10 NH 3
below NH 4 SH



log 10 NH 3
below _P_ _max_



log 10 _P_ _max_



log 10 H 2 S
below NH 4 SH



**Figure** **6.** Cornerplots of highlighted parameters that control the abundance profiles of the condensibles. Histograms of the
retrieved distributions are plotted along diagonals, while the covariance between pairs of parameters are plotted on the offdiagonals. Darker regions on the off-diagonal plots indicate a larger density of retrieved solutions. The 90 _[◦]_ S _−_ 66 _[◦]_ S (left) and
36 _[◦]_ S _−_ 12 _[◦]_ S (right) latitude regions are shown, which both assume a wet adiabat. Dashed vertical lines mark the median and
1 _σ_ bounds.


correlation between the deep H 2 S and NH 3 abundances. The presence of additional NH 3 at deep levels will lead
to additional H 2 S at the NH 4 SH layer. However, H 2 S is the primary absorber above the NH 4 SH layer and so our
data are very sensitive to its abundance. Therefore an increased NH 3 abundance requires a compensating increase in
the H 2 S abundance. In addition, our results show that the H 2 S profile is constrained at the cold mid-latitudes but
unconstrained at the south pole. The NH 3 abundance below the NH 4 SH cloud is somewhat constrained at each latitude
band, though a long-tail forms at low abundances for retrievals with less H 2 S. In addition, _P_ mix is well-constrained
at the south polar cap and is inline with the NH 4 SH condensation pressure. The retrievals also indicate a constant
amount of NH 3 above _P_ mix at the south polar cap, though the median values are larger than the 12 ppb abundance
required by de Pater et al. (2014) to best match their own observations.
The deep CH 4 abundance is only weakly constrained as its effect on the radio opacity is small compared to the
calibration uncertainty (see Fig. 4). Moreover, it competes with effects from PH 3, the H 2 state, and the relative
humidity of H 2 S. At 36 _[◦]_ S _−_ 12 _[◦]_ S, we obtain an upper limit of 85 _._ 4 _×_ protosolar or 4 _._ 1% mixing ratio at the 2 _σ_ level,
assuming a wet adiabat globally. These upper limits are consistent with the disk-average amount of CH 4 reported
by Baines et al. (1995) at 2.2%. However, the 4% deep CH 4 abundance favored by Karkoschka & Tomasko (2011)
is similar to our 2 _σ_ upper limit. A global dry adiaba permits larger abundances of each condensible, with the CH 4
abundance completely unconstrained. Our CH 4 results may be reconciled with differences in the assumed thermal
profiles, as the thermal profile assumed by Karkoschka & Tomasko (2011) is slightly warmer than a wet adiabat.
Our results are consistent with no PH 3 with upper limits of _∼_ 0 _._ 4 _−_ 0 _._ 8 ppm, depending on the assumed temperature
model. We are completely insensitive to the ortho/para H 2 state.
The relative humidity of H 2 S is also unconstrained, apart from 2 _σ_ upper limits. As shown in Figure 4, the difference
between relative humidities of a few percent or less on the retrieved spectra are minimal when compared to our
uncertainties; depleting more and more H 2 S has an inconsequential effect on the opacity once enough is removed.
Figures 7 and 8 plot the best fitting abundance profiles for H 2 S and NH 3 between 36 _[◦]_ S _−_ 12 _[◦]_ S and 90 _[◦]_ S _−_ 66 _[◦]_ S
assuming wet and dry adiabat temperature profiles, respectively. Five hundred random profiles sampled from the
burned-in posterior are also plotted, representing the range of allowable profiles. Brightness temperatures are also
plotted, comparing one hundered random retrieved model spectra and data, showing an agreeable fit. A comparison

16





























75













0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



**Figure** **7.** As Figure 5, except at 90 _[◦]_ S _−_ 66 _[◦]_ S (left) and 36 _[◦]_ S _−_ 12 _[◦]_ S (right), assuming a global wet adiabat. Thick green and
yellow lines plot the best-fitting H 2 S and NH 3 profiles, respectively. The thick red line in the brightness spectra correspond to
the best-fitting profiles. The gray box indicates the range of possible cloud top pressures and H 2 S abundances detected by Irwin
et al. (2019a) over the south polar cap, showing that H 2 S is only detectable in our model at 100% or greater relative humidity.


to south polar 2003 VLA data are overplotted as well, showing good agreement. The assumption of a wet adiabat
thermal profile does not produce H 2 S abundances large enough to be detected by Irwin et al. (2019a) (see Fig. 7)
unless H 2 S is supersaturated. For the dry thermal profile, the H 2 S-ice cloud forms at higher altitudes and larger
H 2 S abundances are possible. However, H 2 S needs to be fully saturated or supersaturated to reach detectable upper
atmosphere abundances.


4.3. _Globally-Varying_ _Profiles_ _-_ _Mitigating_ _Systematic_ _Uncertainty_


One shortcoming of the analysis in the previous section is that the calibration error masks the evident brightness
variations across the disk. In this section, we simultaneously model the atmospheric properties matching both the
observed brightness temperature within the 36 _[◦]_ S _−_ 12 _[◦]_ S latitudinal band, and the observed temperature differences be

17



























75







75





0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



**Figure** **8.** As Fig 7, except assuming a global dry adiabat.


tween 36 _[◦]_ S _−_ 12 _[◦]_ S and other latitudes. This approach reveals the cause of spatial trends in the brightness temperature.
The new likelihood function to maximize is:



2
+ log(2 _πσ_ _n_ [2] [)]
� �



_−_ 0 _._ 5 �


_v_ _n_



2
+ _−_ log(2 _πσ_ ∆ [2] _,n_ [)]
� �



ln _p_ ( _T_ _b_ _|ν, θ, σ_ ) = _−_ 0 _._ 5 �


_v_ _n_



_T_ _b,n_ _−_ _T_ _b,m_

_σ_ _n_
��



∆ _T_ _b,n_ _−_ ∆ _T_ _b,m_
�� _σ_ ∆ _,n_



(4)



The first sum on the right-hand side is the same as equation (1) and represents the fit to the observed brightness
temperature at 36 _[◦]_ S _−_ 12 _[◦]_ S with errors dominated by systematic calibration. The second sum represents the brightness
temperature difference between 36 _[◦]_ S _−_ 12 _[◦]_ S and the other latitudinal band:


∆ _T_ _b_ = _T_ 36 _[◦]_ S _−_ 12 _[◦]_ S _−_ _T_ other latitude _._ (5)


Errors in the temperature variation between latitudes at the same wavelength are mainly due to random fluctuations.
The uncertainty _σ_ ∆ is:

18


_σ_ ∆ = (∆ _T_ _b_ _·_ 0 _._ 05) [2] + _σ_ _RMS_ [2] 1 [+] _[ σ]_ _RMS_ [2] 2 [+] _[ σ]_ _P SF_ [2] (6)


The first term on the right-hand side is the difference in brightness temperature between the reference and modeled
latitude band times the 5% calibration error. _σ_ _RMS_ is the random error on the sky divided by the square root of the
number of beams that fit within the reference and modeled latitude bands.
The deep abundances of H 2 S, NH 3, and CH 4 are allowed to vary for each pair of latitudes. Moreover, H 2 S may
either subsaturate or supersaturate. H 2 S may be supersaturated up to a pressure _P_ ss . At altitudes shallower than
_P_ ss, the H 2 S profile follows the saturation curve with 100% relative humidity. At the south polar cap, the abundances
of H 2 S and NH 3 at pressures shallower than _P_ mix are also allowed to vary, as in the previous section. We assume no
PH 3 and fully intermediate H 2 at all latitudes as we do not expect to be sensitive to these parameters given our prior
findings (Table 6).
Tables 7 and 8 list the best-fitting values for 16/50/84th uncertainties for constrained parameters assuming a global
wet and dry adiabat, respectively. Figures 9 and 10 plot randomly-sampled and the best-fitting retrieved trace
gas profiles and residual spectra ∆ _T_ . We obtain good agreement between the observed and modeled temperature
differences. Moreover, the retrieved parameters for the 36 _[◦]_ S _−_ 12 _[◦]_ S band are consistent between model runs to within
uncertainties, indicating this approach is self-consistent.
These results show global variability in Neptune’s NH 3 and H 2 S abundances. NH 3, although overall very much
depleted due to the formation of NH 4 SH, is enriched at the south polar cap above _P_ mix relative to the rest of the
planet. A globally uniform H 2 S abundance below NH 4 SH formation is consistent with our results. However, above
NH 4 SH formation, the H 2 S abundance decreases poleward, mirroring brightness temperature increases poleward (Fig.
1). Differences in the H 2 S relative humidity cause the apparent brightness variations in the short-wavelength maps,
which probe the H 2 S-ice cloud and are coldest / darkest at 36 _[◦]_ S _−_ 12 _[◦]_ S and 4 _[◦]_ N _−_ 20 _[◦]_ N. These regions are also where
supersaturated H 2 S is needed in order to fit the observed temperature variations. This discussion is visually summarized
in Figure 11, which plot the probability density of the retrieved H 2 S mixing ratio in each latitude band relative to
that obtained for 36 _[◦]_ S _−_ 12 _[◦]_ S in the simultaneous fit. These plots demonstrate the magnitude and significance of these
variations at the three pressure regimes discussed: below NH 4 SH formation (100 bar), above H 2 S-ice formation (5
bar), and in-between (20 bar). In the Appendix, we show that latitudinal variations in the thermal profile can only
explain the observations if the temperature variations are localized to the H 2 S-ice formation pressures and are on the
order of _∼_ 8K or greater.
A measure of the improvement in the fit between two models is the Deviance Information Criterion (DIC, Spiegelhalter et al. (2002)). DIC is defined as:


DIC = _D_ ( _θ_ ) + [1] (7)

2 [Var(] _[D]_ [(] _[θ]_ [))]


_θ_ are the free parameters, _D_ ( _θ_ ) is the mean deviance of the retrieved parameters, which in this case is the average
of the log-likelihood _emcee_ probabilities, defined in Eq. (4). The second term on the right hand side is one-half the
variance of these probabilities.
Information criteria like DIC are typically used when analyzing MCMC results in order to select models which
provide a good fit to the data (the first term) and minimize the variance in the retrieved probabilities (the second
term) resulting from model complexity. The difference between two DIC values can be used to determine the better
model assuming the parameters roughly follow a Gaussian distribution. Differences greater than 10 favor the model
with the lower DIC score.

Table 9 lists the DIC score for the global wet and dry adiabat models at each latitude band. The dry adiabat is
statistically favored everywhere, apart from 50 _[◦]_ S _−_ 36 _[◦]_ S where neither thermal profile is favored. We additionally show
in Section 2 of the Appendix that when the lapse rate is allowed to vary with the trace gas abundances, the resulting
retrieved temperature-pressure profiles follow a dry adiabat more closely than a wet adiabat.


5. DISCUSSION


Retrievals of Neptune’s microwave spectrum from radiative transfer modeling require an atmosphere dominant in
H 2 S over NH 3 . In every retrieval, all NH 3 is taken up by the formation of the NH 4 SH cloud around 50 bar, leaving
H 2 S to persist and condense at higher altitudes. The global thermal profile has a moderate impact on the produced
H 2 S and NH 3 profiles. Below all cloud formation, we obtain H 2 S abundances of 8 _._ 7 [+2] _−_ 1 _[.]_ _._ [6] 7 _[×]_ [10] _[−]_ [4] [(37] _[.]_ [3] [+15] _−_ 10 _[.]_ _._ [7] 3 _[×]_ [ protosolar)]

19

20



T (K) b



T (K) b



T (K) b



T (K) b



T (K) b



Pressure (bar)


Pressure (bar)


Pressure (bar)


Pressure (bar)


Pressure (bar)

21

|Col1|Col2|Col3|Col4|Col5|2|
|---|---|---|---|---|---|
|Latitude Bin:|90_◦_S_−_66_◦_S|66_◦_S_−_50_◦_S|50_◦_S_−_36_◦_S|12_◦_S_−_4_◦_N|4_◦_N_−_20_◦_N|
|Free Parameter|Retrieved values - global wet adiabat|Retrieved values - global wet adiabat|Retrieved values - global wet adiabat|Retrieved values - global wet adiabat|Retrieved values - global wet adiabat|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>H2S _H_rel (%)<br>_P_ss (bar)<br>_P_mix (bar)<br>H2S above _P_mix<br>NH3 above _P_mix|9_._5+2_._5<br>_−_2_._3 _×_ 10_−_4<br>0_._9+0_._5<br>_−_0_._4 _×_ 10_−_4<br>_≤_0_._5_ ×_ 10_−_2<br>18+13<br>_−_11<br>not supersat.<br>38+3<br>_−_3<br>1_._4+0_._6<br>_−_0_._3 _×_ 10_−_5<br>9_._0+9_._0<br>_−_3_._9 _×_ 10_−_7|7_._7+2_._1<br>_−_1_._3 _×_ 10_−_4<br>2_._7+2_._2<br>_−_1_._1 _×_ 10_−_4<br>_≤_0_._6_ ×_ 10_−_2<br>49+5<br>_−_3<br>not supersat.<br>—<br>—<br>—|8_._0+1_._3<br>_−_1_._6 _×_ 10_−_4<br>3_._1+1_._3<br>_−_1_._5 _×_ 10_−_4<br>_≤_0_._6_ ×_ 10_−_2<br>80+5<br>_−_5<br>not supersat.<br>—<br>—<br>—|8_._5+1_._4<br>_−_1_._3 _×_ 10_−_4<br>2_._6+1_._0<br>_−_1_._2 _×_ 10_−_4<br>_≤_0_._8_ ×_ 10_−_2<br>76+8<br>_−_3<br>not supersat.<br>—<br>—<br>—|9_._2+2_._4<br>_−_1_._7 _×_ 10_−_4<br>1_._7+1_._6<br>_−_1_._3 _×_ 10_−_4<br>_≤_0_._5_ ×_ 10_−_2<br>_≥_70<br>_≥_7_._9<br>—<br>—<br>—|
|Free Parameter|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>_P_ss (bar)<br>H2S _H_rel (%)<br>_σP SF_ (%)|7_._9+1_._1<br>_−_0_._9 _×_ 10_−_4<br>2_._9+1_._1<br>_−_1_._4 _×_ 10_−_4<br>_≤_4_._0_ ×_ 10_−_2<br>_≥_6_._4<br>_≥_48<br>_≤_6|9_._3+1_._5<br>_−_1_._6 _×_ 10_−_4<br>2_._1+1_._9<br>_−_1_._3 _×_ 10_−_4<br>_≤_1_._3_ ×_ 10_−_2<br>_≥_7_._3<br>_≥_90<br>_≤_1|7_._5+2_._1<br>_−_1_._3 _×_ 10_−_4<br>2_._7+1_._8<br>_−_1_._3 _×_ 10_−_4<br>_≤_0_._9_ ×_ 10_−_2<br>7_._2+0_._3<br>_−_0_._4<br>not subsat.<br>_≤_2|8_._1+1_._7<br>_−_1_._3 _×_ 10_−_4<br>2_._8+1_._6<br>_−_1_._4 _×_ 10_−_4<br>_≤_1_._3_ ×_ 10_−_2<br>6_._9+0_._3<br>_−_0_._3<br>not subsat.<br>_≤_2|9_._1+1_._9<br>_−_1_._3 _×_ 10_−_4<br>1_._3+1_._4<br>_−_1_._0 _×_ 10_−_4<br>_≤_0_._8_ ×_ 10_−_2<br>8_._2+0_._5<br>_−_0_._4<br>not subsat.<br>_≤_6|



**Table** **7.** MCMC retrieved parameters for the simultaneous latitudinal band fitting, matching the observed brightness temperature variations at a given latitude band compared to that at 36 _[◦]_ S _−_ 12 _[◦]_ S, assuming a global wet adiabat. A column in the top
table lists the values of retrieved parameters at the given latitude band, while the corresponding column in the bottom table
lists those obtained at 36 _[◦]_ S _−_ 12 _[◦]_ S in the simultaneous fit (eq. 4). Free parameters marked with a ‘ _−_ _[′]_ were not allowed to vary
at that latitude band. ‘not supersat.’ and ‘not subsat.’ means that supersaturated and subsaturated H 2 S were not obtained
in any final retrievals, respectively. The listed values are the 50th percentile of the posterior distributions with the error bars
corresponding to the 16th and 84th percentiles, i.e. the 1 _σ_ uncertainties. Parameters for which the 16th and 84th percentiles
vary by more than one order of magnitude have the 2.5th/97.5th percentile value listed instead, representing the 2 _σ_ lower/upper
limit. If both supersatured and subsaturated H 2 S are possible in a latitude band, the 2 _σ_ limit is listed for both _P_ ss and H 2 S
_H_ rel .

|Latitude Bin:|90◦S 66◦S<br>−|66◦S 50◦S<br>−|50◦S 36◦S<br>−|12◦S 4◦N<br>−|4◦N 20◦N<br>−|
|---|---|---|---|---|---|
|Free Parameter|Retrieved values - global dry adiabat|Retrieved values - global dry adiabat|Retrieved values - global dry adiabat|Retrieved values - global dry adiabat|Retrieved values - global dry adiabat|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>H2S _H_rel (%)<br>_P_ss (bar)<br>_P_mix (bar)<br>H2S above _P_mix<br>NH3 above _P_mix|_≤_5_._7_ ×_ 10_−_3<br>1_._7+0_._9<br>_−_0_._8 _×_ 10_−_4<br>_≤_3_._1_ ×_ 10_−_2<br>44+9<br>_−_11<br>not supersat.<br>34+3<br>_−_3<br>_≤_4_._5_ ×_ 10_−_4<br>_≤_4_._1_ ×_ 10_−_6|1_._2+0_._4<br>_−_0_._3 _×_ 10_−_3<br>4_._8+3_._3<br>_−_3_._5 _×_ 10_−_4<br>_≤_5_._7_ ×_ 10_−_2<br>53+4<br>_−_3<br>not supersat.<br>—<br>—<br>—|1_._0+0_._3<br>_−_0_._1 _×_ 10_−_3<br>2_._2+2_._3<br>_−_1_._3 _×_ 10_−_4<br>_≤_6_._0_ ×_ 10_−_2<br>78+6<br>_−_4<br>not supersat.<br>—<br>—<br>—|1_._0+0_._5<br>_−_0_._2 _×_ 10_−_3<br>2_._8+3_._3<br>_−_1_._5 _×_ 10_−_4<br>_≤_1_._5_ ×_ 10_−_2<br>78+5<br>_−_4<br>not supersat.<br>—<br>—<br>—|1_._9+0_._5<br>_−_0_._5 _×_ 10_−_3<br>_≤_9_._5_ ×_ 10_−_4<br>_≤_2_._3_ ×_ 10_−_2<br>_≥_61<br>_≥_8_._3<br>—<br>—<br>—|
|Free Parameter|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|Corresponding 36_◦_S_−_12_◦_S retrieved values|
|H2S below NH4SH<br>NH3 below NH4SH<br>CH4<br>_P_ss (bar)<br>H2S _H_rel (%)<br>_σP SF_ (%)|7_._5+2_._5<br>_−_1_._7 _×_ 10_−_4<br>0_._4+1_._4<br>_−_0_._2 _×_ 10_−_4<br>_≤_5_._3_ ×_ 10_−_2<br>6_._2+1_._0<br>_−_0_._4<br>not. subsat<br>_≤_4|1_._4+0_._4<br>_−_0_._5 _×_ 10_−_3<br>3_._2+3_._2<br>_−_1_._8 _×_ 10_−_4<br>_≤_1_._6_ ×_ 10_−_2<br>6_._9+0_._7<br>_−_0_._3<br>not. subsat.<br>_≤_2|1_._1+0_._4<br>_−_0_._4 _×_ 10_−_3<br>1_._2+3_._4<br>_−_0_._6 _×_ 10_−_4<br>_≤_6_._7_ ×_ 10_−_2<br>_≥_5_._9<br>_≥_88<br>_≤_1|9_._8+2_._2<br>_−_2_._3 _×_ 10_−_4<br>3_._0+4_._8<br>_−_0_._8 _×_ 10_−_4<br>_≤_1_._5_ ×_ 10_−_2<br>6_._1+0_._3<br>_−_0_._2<br>not subsat.<br>_≤_2|1_._8+0_._5<br>_−_0_._4 _×_ 10_−_3<br>3_._3+4_._0<br>_−_2_._3 _×_ 10_−_4<br>_≤_2_._7_ ×_ 10_−_2<br>_≥_6_._8<br>_≥_79<br>_≤_9|



**Table** **8.** As Table 7, but assuming a global dry adiabat.

22



Latitude Band

|Adiabat wet dry|Col2|
|---|---|
|||



Latitude Band

|1|S S S N N|
|---|---|
|<br>3<br> <br>3<br>0<br> <br>3<br>|Adiabat<br>wet<br>dry|
|<br>3<br> <br>3<br>0<br> <br>3<br>||



Latitude Band


|1|S S S N N|Col3|
|---|---|---|
|<br>5<br> <br>5<br> <br>5<br> <br>5<br>0<br>|Adiabat<br>wet<br>dry|Adiabat<br>wet<br>dry|
|<br>5<br> <br>5<br> <br>5<br> <br>5<br>0<br>|Adiabat<br>wet<br>dry||
|<br>5<br> <br>5<br> <br>5<br> <br>5<br>0<br>|||

23

|Latitude Bin:|90◦S 66◦S<br>−|66◦S 50◦S<br>−|50◦S 36◦S<br>−|12◦S 4◦N<br>−|4◦N 20◦N<br>−|Total|
|---|---|---|---|---|---|---|
|Wet Adiabat DIC<br>Dry Adiabat DIC<br>Diﬀerence|177<br>151<br>+26|152<br>134<br>+18|145<br>130<br>+15|134<br>116<br>+18|173<br>155<br>+18|781<br>689<br>+95|



**Table** **9.** DIC values for each latitude band comparison per global temperature profile. Differences larger than 10 statistically
favor the model with the lower DIC score, in this case the global dry adbaiat.


for a wet adiabat and 1 _._ 3 [+0] _−_ 0 _[.]_ _._ [4] 3 _[×]_ [ 10] _[−]_ [3] [(53] _[.]_ [8] [+18] _−_ 13 _[.]_ _._ [9] 4 _[×]_ [protosolar)] [for] [a] [dry] [adiabat.] [We] [are] [less] [sensitive] [to] [the] [deep] [NH] [3]
abundance as all contribution functions probe at and above the NH 4 SH cloud. However, we do find a clear positive
correlation between the H 2 S and NH 3 abundances: more deep NH 3 requires more deep H 2 S. We obtain loose bounds
on the NH 3 abundance: 2 _._ 5 [+2] _−_ 2 _[.]_ _._ [7] 3 _[×]_ [10] _[−]_ [4] [(2] _[.]_ [1] [+2] _−_ 1 _[.]_ _._ [3] 9 _[×]_ [ protosolar) for a wet adiabat and 4] _[.]_ [7] _−_ [+2] 3 _[.]_ _._ [5] 7 _[×]_ [10] _[−]_ [4] [(3] _[.]_ [9] [+2] _−_ 3 _[.]_ _._ [1] 1 _[×]_ [ protosolar)]
for a dry adiabat. Models fitting to the brightness temperature variations between latitude bands statistically favor a
globally uniform thermal profile following a dry adiabat.
Using the H 2 S/NH 3 ratio as a proxy for the S/N ratio, we completely rule out observable S/N ratios less than unity.
This is in agreement with earlier radio work on Neptune, although we obtain better constraints on these abundances
(de Pater et al. 1991; DeBoer & Steffes 1996; de Pater et al. 2014; Luszcz-Cook et al. 2013a; Tollefson et al.
2019). Sub-unity S/N is also ruled out on Uranus, suggesting some commonality in the formation history of the ice
giants (Gulkis et al. 1978; de Pater et al. 1991, 2018b; Molter et al. 2020). However, their true bulk S/N ratio may
be much smaller than observed or assumed, due to the potential loss of ammonia in an ionic/superionic water ocean
at 20 GPa (Atreya et al. 2019). Indeed, if CO is uplifted into Neptune troposphere, it implies that the water content
and O/H ratio is several hundred times protosolar (Luszcz-Cook et al. 2013b). An additional way to explain the
absence of N is the preferential delivery of volatiles onto planetesimals via hydrated clathrates (Hersant et al. 2004).
In the cold environment of the outer protoplanetary disk, the N 2 to NH 3 fraction is roughly 10, while S is primarily
in the form of H 2 S. Both H 2 S and NH 3 are readily trapped in hydrated clathrates while N 2 gas is not, meaning the
majority of available N will not be swept into the ice giants. The clathrated hydrates hypothesis also implies that the
O/H ratio within Uranus and Neptune is at least 100 times protosolar.
The differences in brightness temperature between latitude regions reveal prevalent global variations in the H 2 S and
NH 3 profiles. Brightness temperature variations between latitude bands were modeled by comparing the retrieved
spectra to profiles simultaneously fit to the 36 _[◦]_ S _−_ 12 _[◦]_ S region. This approach limits the calibration error, placing tight
constraints on how the trace gas profiles vary latitudinally.
At the south pole, the data can be fit with a downwelling atmosphere, where air depleted in H 2 S and NH 3 species
subsides down to a mixing pressure, _P_ mix, below which the atmosphere becomes well mixed and the trace species
equal their deep values. The best-fit retrieved H 2 S and NH 3 mixing ratios at altitudes above _P_ mix are 4 _._ 4 _×_ 10 _[−]_ [5] and
4 _._ 1 _×_ 10 _[−]_ [7], respectively, for a dry adiabat. This is in broad agreement with south polar models of 2003 VLA data
presented in de Pater et al. (2014), whose best fitting depleted model required 3 _._ 5 _×_ 10 _[−]_ [5] parts H 2 S and 1 _._ 2 _×_ 10 _[−]_ [8]

parts NH 3 above the NH 4 SH cloud.
Below NH 4 SH formation, our results are consistent with homogenous NH 3 and H 2 S. Clear latitudinal trends in the
H 2 S profile, however, must be present at higher altitudes. Just above NH 4 SH cloud formation, the H 2 S abundance is
highest between around the equator and mid-latitudes and diminishes poleward.

Irwin et al. (2019a) tentatively detected 1 _−_ 3 ppm H 2 S at Neptune’s cloud tops between 2 _._ 5 _−_ 3 _._ 5 bar. Their
detection is more robust near the south pole than the equator and both their retrieved cloud top pressures and
abundances increase toward the south pole. Our results assuming a wet adiabat globally are not consistent with their
findings (for instance, see the gray rectangles in Fig. 7). The wet thermal profile is about 7K cooler at 3 bar than the
Irwin et al. (2019a) profile. Only our dry adiabat models at the south pole allow H 2 S gas abundances close to the
values found by Irwin et al. (2019a), as warmer temperatures push the H 2 S cloud base to higher altitudes.
Supersaturated H 2 S between 36 _[◦]_ S _−_ 12 _[◦]_ S and possibly between 4 _[◦]_ N _−_ 20 _[◦]_ N is required to obtain good fits to the
observed brightness temperature variations if the thermal profile is fixed globally. Numerous near-infrared works favor
a two-layer cloud/haze structure featuring a shallow tenuous upper haze and an opaque cloud deck between 2 _−_ 4 bar
(Irwin et al. 2014; Luszcz-Cook et al. 2016; Molter et al. 2019). This lower cloud is presumably H 2 S-ice, supporting
our finding. The ratio of the partial pressure of the condensate in a supersaturated model to the partial pressure
of condensate following its saturation curve, _φ_, is a few hundred percent in our H 2 S supersaturation model. Similar

24


degrees of supersaturation are expected within ammonia plumes on Jupiter (de Pater et al. 2019). However, on Earth
_φ_ does not exceed 10% for water (Young 1993). This is because the timescale of cloud formation is very quick in the
presence of cloud condensation nuclei (CCN). Little is known about the amount of CCNs available on the gas giants.
But, theoretical calculations by Moses et al. (1992) of homogeneous, heterogeneous, and ion-induced nucleation rates
produce large values and ranges for _φ_, depending on the species. They find _φ_ _≥_ 3 _−_ 1000 in order for methane and
photolyzed hydrocarbon aerosols to form in Neptune’s stratosphere. Neptune may lack substantive amounts of CCN
conducive to aerosol formation. Future work should consider both the effect of cloud micro-physics and dynamics on
the trace gas distributions within the ice giants.
The above discussion is synthesized in Figure 12, which shows one potential global H 2 S profile. For each latitudinal
band, we assume the best-fitting H 2 S abundances and relative humidities from Table 8. Broadly, these meridional
trends in gas abundances are related to the global circulation patterns of the planet.
Warm temperatures within Neptune’s south polar cap are detected at mid-infrared and radio wavelengths. In
the mid-infrared, (Hammel et al. 2007) observe a warm south pole explained by prevalent ethane and methane
emission. (Orton et al. 2007) further argue that seasonal warming at the south polar cap may explain the excess of
these molecules in the stratosphere; the warm temperatures would overcome the cold-trapping of methane below its
condensation point at _∼_ 1 bar and allow methane to escape upward, diffuse globally, and form ethane via photolysis.
(Orton et al. 2007) also argue that rising air would be expected given the unexpected high abundances of these species.
However, warm temperatures relative to the rest of the planet seen in the mid-infrared thermal emission (Fletcher et al.

2014) and a lack of widespread, persistent cloud coverage in the near-infrared (e.g., de Pater et al. (2014)) are more
indicative of dry subsiding air. Radio observations, including these, observe high brightness temperatures at Neptune’s
south polar cap (Luszcz-Cook et al. 2013a; de Pater et al. 2014; Tollefson et al. 2019), which we also interpret
as dry, low-opacity, subsiding air. Cloud coverage surrounding the south polar cap and faint, distinct near-infrared
clouds located near, but not at, the south pole might be indicative of vigorous convection (Luszcz-Cook et al. 2010),
analogous to Saturn’s polar activity (Dyudina et al. 2008; Fletcher et al. 2008). This vigorous convection may be a
mechanism to explain all observations across the wavelength spectrum.
The mid-latitudes, defined loosely as between 50 _[◦]_ S _−_ 15 _[◦]_ S and northward of 15 _[◦]_ N, are where Neptune’s brightest
and strongest methane cloud activity is observed in the near-infrared (Martin et al. 2012; Fitzpatrick et al. 2014;
de Pater et al. 2014; Tollefson et al. 2018). In contrast, the equatorial region is nearly featureless. In addition,
the mid-latitudes are colder than the equator and south pole in the mid-infrared (Conrath et al. 1998; Fletcher et
al. 2014). Combining these observations, a global circulation pattern is inferred at altitudes shallower than _∼_ 1
bar (where the near- and mid-infrared probe): cold, enriched methane air rises at the mid-latitudes and travels to
the equator and poles, where the methane-depleted air subsides and warms via adiabatic compression. However, this
picture is complicated by the relative excess of gaseous CH 4 at the equator, which is more consistent with rising air
(Karkoschka & Tomasko 2011; Tollefson et al. 2018; Irwin et al. 2019b). We show in this paper that H 2 S is most
abundant at the equator and southern mid-latitudes, in line with this meridional trend in CH 4 . At altitudes below
methane condensation ( _∼_ 1 bar), the aforementioned circulation scheme is, thus, at odds with the retrieved CH 4 and
H 2 S abundances. Therefore, a more complicated picture of global circulation on Neptune is needed to explain each
multi-wavelength observation. Fletcher et al. (2020) synthesize decades worth of analysis on the ice giants and argue
that vertically-stacked circulation cells are necessary to bridge the observed patterns above and below 1 bar on both
Uranus and Neptune.


6. CONCLUSIONS


We observed Neptune at radio wavelengths with the Very Large Array in five bands between 0 _._ 9 _−_ 9 _._ 7 cm from 1 _−_ 2
September, 2015. The longitude-smeared maps reveal brightness variations across Neptune’s disk. These variations are
alternating dark and bright latitudinal bands. Dark (bright) bands are consistent with high (low) opacity sources and
cold (warm) brightness temperatures. We model Neptune’s brightness temperature distribution using the radiative
transfer code Radio-BEAR coupled to MCMC, varying the abundance profiles of Neptune’s condensibles to obtain
best-fits and retrievals to the observed microwave spectra. Models are fit to data from both the VLA presented in this
work and 1 _−_ 3 mm ALMA maps from Tollefson et al. (2019). Combined, these data probe from 1 bar down to _>_ 50
bar, where the NH 4 SH cloud forms.

25



1


10


100







10 3


10 4


10 5


10 6


10 7


10 8


|Col1|Best Fit H 2S Profiles|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||NH4SH Cloud|NH4SH Cloud|NH4SH Cloud|NH4SH Cloud|NH4SH Cloud|NH4SH Cloud|NH4SH Cloud|NH4SH Cloud|
||||||||||



-90 -75 -60 -45 -30 -15 0 15

Latitude


**Figure** **12.** The best-fitting global H 2 S profile from MCMC retrievals.


- The assumed thermal profile has a moderate impact on the retrieved H 2 S, NH 3, and CH 4 profiles. A global
dry adiabat is preferred over a wet adiabat as a warmer thermal profile is statistically favored in models fitting
brightness temperature variations across the disk. All below results are given for the dry adiabat models.


- The abundances of H 2 S and NH 3 below all cloud formation are 1 _._ 3 [+0] _−_ 0 _[.]_ _._ [4] 3 _[×]_ [10] _[−]_ [3] [(53] _[.]_ [8] [+18] _−_ 13 _[.]_ _._ [9] 4 _[×]_ [protosolar)] [and]
4 _._ 7 _−_ [+2] 3 _[.]_ _._ [5] 7 _[×]_ [ 10] _[−]_ [4] [(3] _[.]_ [9] [+2] _−_ 3 _[.]_ _._ [1] 1 _[×]_ [protosolar).]


- The abundance of CH 4 is unconstrained due to its limited impact on the microwave opacity longward of 1 cm.
In the mm, the CH 4 contribution to the modeled spectra competes with other opacity sources, namely PH 3, the
H 2 state, and the H 2 S relative humidity, dulling its signal in the retrievals.


- The downwelling south polar cap (90 _[◦]_ S _−_ 66 _[◦]_ S) is consistent with depleted H 2 S and NH 3 down to a mixing pressure
_P_ mix around the NH 4 SH cloud formation: _∼_ 33 bar. Only when H 2 S is fully saturated or supersaturated can
retrieved H 2 S abundances exceed 1 ppm at 3.5 bar at the south polar cap, as measured by Irwin et al. (2019a).
Only our dry adiabat model can produce values at pressures close to those detected.


- The observed brightness temperature variations between latitude bins are consistent with decreased H 2 S above
the NH 4 SH cloud deck moving away from 36 _[◦]_ S _−_ 12 _[◦]_ S.


- The observed brightness temperature variations are more consistent with models supersaturating H 2 S between
36 _[◦]_ S _−_ 12 _[◦]_ S, and possibly 4 _[◦]_ N _−_ 20 _[◦]_ N, than with models following thermochemical equilibrium with some subsaturation. Models which do not allow H 2 S to supersaturate require latitudinal variations in the kinetic temperature
on the order of 8K or greater to fit the data. These variations in the thermal profile are localized to H 2 S-ice
formation pressures. Future work is needed to decouple the effects of temperature and gas opacity on Neptune’s
radio spectrum.


- We find no spectral evidence of PH 3 . Our retrievals are consistent with a PH 3 2 _σ_ upper limit of 0.4 ppm ( _≤_ 0 _._ 1 _×_
protosolar).


- We cannot constrain the ortho/para H 2 fraction anywhere on Neptune.

26


Advances in radio astronomy are critical for further constraining the abundance of condensibles in the ice giants.
A next generation VLA (ngVLA) would improve the resolution ten-fold at 20 cm if the longest 1000 km baselines
are utilized (de Pater et al. 2018a; Selina et al. 2018). The resulting high-quality data at long wavelengths would
permit a strong constraint on the NH 3 abundance beneath the NH 4 SH layer and perhaps even on H 2 O. In addition, a
five-fold improvement in the sensitivity would mean vastly shorter integration times to achieve an equivalent RMS to
this work, meaning zonal variations can be detected over a similar observing period and global maps can be obtained.
_Juno_ ’s big advantage over ground-based radio observations of Jupiter is that it flies beneath the synchrotron radiation
belts that dominate longward of 6 cm. This is not an issue on the ice giants. Moreover, the resolution and sensitivity
between the ngVLA and a MWR-like instrument on a potential future Neptune orbiter are quite similar (de Pater et
al. 2020).
The decision to include an MWR-equivalent on a direct mission to the ice giants will have to weigh whether it
competes too heavily with the ground-based capabilities of an optimally running ngVLA. Whatever the choice, it is
clear that the ngVLA or a direct mission to the planet are required to improve our maps of Neptune’s trace species
and elucidate theories regarding the environment in which Neptune formed and evolved.


ACKNOWLEDGMENTS


This paper makes use of the following VLA data from program VLA/15A-118. The National Radio Astronomy Observatory (NRAO) is a facility of NSF operated under cooperative agreement by Associated Universities, Inc. VLA data used in this report are available from the NRAO Science Data Archive at
https://archive.nrao.edu/archive/advquery.jsp.


This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00859.S. ALMA is a partnership of
ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of
the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.
This research was supported by the National Science Foundation, NSF Grant AST-1615004 to the University of
California, Berkeley.
E. Molter was supported in part by NRAO Student Observing Support grant #SOSPA6-006.


APPENDIX


.1. _Globally_ _Uniform_ _Temperature_ _Profiles_


In this section, we address the assumption that the temperature profile is globally uniform at a given pressure level.
We first show that this assumption leads to reasonable wind speeds according to the thermal wind equation, then
demonstrate that not allowing the trace gas abundances to vary meridionally can result in well-modeled spectra only
for nonphysical temperature profiles.
We test the validity of the assumption that the meridional temperature gradient is zero for _P_ _>_ 1 bar using an
order-of-magnitude comparison. The thermal wind equation relates the vertical wind shear to both the meridional
gradient in temperature and composition:



(1)
�



2Ωsin _θ_ _[du]_



_dr_ [=] _[ −]_ _r_ _[g]_



_r_ eq



1 _dT_ _C_ _dq_
� _T_ _dθ_ [+] 1 + _Cq_ _dθ_



Ωis Neptune’s rotation rate (1 _×_ 10 _[−]_ [4] rad s _[−]_ [1] ), _θ_ is the latitude (rad), _u_ is the zonal wind velocity (m s _[−]_ [1] ), _r_ is
altitude (m), _r_ eq is Neptune’s equatorial radius (2 _._ 5 _×_ 10 [7] m), _g_ is Neptune’s gravitational constant (10 m s _[−]_ [2] ), _T_ is the
temperature, _q_ is the molar mass fraction of CH 4 (the most prominent trace gas on Neptune), and _C_ = (1 _−_ _ϵ_ ) _/ϵ_ where
_ϵ_ is the molar mass ratio of CH 4 compared to the ambient atmosphere. For the purpose of this exercise, we assume
that the ambient atmosphere consists of H 2, He, and CH 4 ; H 2 S and NH 3 have comparatively smaller abundances than
CH 4 and are therefore less important to the compositional term. _ϵ_ _≈_ 7 and _C_ _≈−_ 1. At the southern mid-latitudes,
sin _θ_ _≈−_ 0 _._ 5 and the above equation becomes:

27



30


20


10


0


10


20





15


10


5


0


5


10


15





10


5


0


5


10


15





0.1 1 10
Wavelength (cm)


10


5


0


5


10


15



0.1 1 10
Wavelength (cm)


5


0


5


10


15


20



0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



0.1 1 10
Wavelength (cm)



**Figure** **A1.** Residual temperatures as a function of latitude, where the observed temperature at 36 _[◦]_ S-12 _[◦]_ S is subtracted from
the temperature at the given latitude band. Colored lines are example model fits to the data assuming a nominal abundance
profile and the same colored temperature profile given in Fig. A2.



_−_ 1 _×_ 10 _[−]_ [4] _[ du]_ _dr_ _[≈]_ [4] _[ ×]_ [ 10] _[−]_ [7] 1 _−_ 1 _q_ _dθdq_ (2)



From Karkoschka & Tomasko (2011), _q_ is about 0.1 at Neptune’s south pole ( _≤_ 1 _−_ 2% mixing ratio) and 0 _._ 2 toward
the southern mid-latitudes and equator ( _≥_ 2 _−_ 4%). So _dq/d_ ( _θ_ ) _∼_ +0 _._ 1 at the mid-latitudes for 1 _≤_ _P_ _≤_ 3 bar. Thus,
the right hand side is about 5 _×_ 10 _[−]_ [8] and _du/dr_ _≈−_ 0 _._ 5 m s _[−]_ [1] km _[−]_ [1] . The sign and magnitude of this estimate is
similar to that of Tollefson et al. (2018) who observed vertical wind shear at Neptune’s equator by tracking nearinfrared clouds. Therefore, the thermal wind equation alone cannot rule out the assumption of constant meridional

temperatures.
Since the vertical wind shear is relatively unconstrained, especially below 1 bar, meridional kinetic temperature
variations are not precluded from a thermal wind analysis. To test this, we estimate what temperature profile is
needed to model the observed residual brightness temperatures. We fix the trace gas abundances globally to equal the
nominal model (30 _×_ S H 2 S, CH 4, H 2 O and 1 _×_ S NH 3, with no PH 3, ‘intermediate’ H 2, and 100% relative humidity at
all cloud formation). Fig A1 plots the observed and modeled temperature variations versus wavelength, meaning a dry
adiabat model for 36 _[◦]_ S-12 _[◦]_ S is subtracted from the model temperature at each other latitude bin. The temperature
profiles used to create these models are plotted in A2. To fit the residual temperatures, two adjustments to the
dry adiabatic lapse rate are required. If the kinetic temperature were the sole cause of the brightness temperature
variations, then substantial local variations on the order of 8K or greater are required. Interestingly, these peak around
pressures where the H 2 S-ice cloud forms ( _∼_ 10 bar), suggesting that the natural explanation for meridional brightness
variability is due to changes in the H 2 S profile altering the microwave opacity.


.2. _Varying_ _Temperature_ _and_ _Trace_ _Gas_ _Abundances_ _with_ _MCMC_


In the following, we consider a combination of kinetic temperature and trace gas abundance variations that may
explain the observed brightness temperature latitudinal differences. To vary the kinetic temperature in the forward
RT model, we allow the lapse rate to vary:



Γ = _−_ _[dT]_ (3)

_dz_



Assuming hydrostatic equilibrium and the ideal gas law:

28





1


10


100



1


10


100




|Col1|Residual Fitted TP Profile|
|---|---|
||36 S-12 S<br>90 S-66 S<br>66 S-50 S<br>50 S-36 S<br>12 S-4 N<br>4 S-20 N<br>a)|
|||



50 100 150 200 250 300 350
Temperature (K)




|Col1|Col2|ResidualFittedTPProfile|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|||90 <br>66 <br>50 <br>12 <br>4 S<br>b)|90 <br>66 <br>50 <br>12 <br>4 S<br>b)|90 <br>66 <br>50 <br>12 <br>4 S<br>b)|90 <br>66 <br>50 <br>12 <br>4 S<br>b)|S-66 S<br> S-50 S<br> S-36 S<br> S-4 N<br>-20 N|
||||||||
||||||||
|||10<br>20<br>30<br>Temperature Difference From 36 S-12|10<br>20<br>30<br>Temperature Difference From 36 S-12|10<br>20<br>30<br>Temperature Difference From 36 S-12|10<br>20<br>30<br>Temperature Difference From 36 S-12|10<br>20<br>30<br>Temperature Difference From 36 S-12|



**Figure** **A2.** a) Temperature profiles as a function of latitude (colored lines) producing the residual spectra fits plotted in
Fig. A1. b) Residual temperature profile as a function of latitude (colored lines), where the 36 _[◦]_ S-12 _[◦]_ S dry adiabat profile is
subtracted from the temperature at the given latitude band.



Γ = _ρg_ _[dT]_




_[g]_ _dT_

(4)
_RT_ _dP_ _[,]_




_[dT]_ _[PM]_ _[g]_

_dP_ [=] _RT_



where _R_ is the ideal gas constant, _g_ is the gravitational constant for Neptune, and for each layer _P_ is its pressure,
_T_ its kinetic temperature, and _M_ its molecular mass.
The molecular mass of the layer, _M_, is set by the mole fraction abundance of H 2, He, and CH 4 where [He]/[H 2 ]
= 18%, in line with infrared results from Burgdorf al. (2003), and [CH 4 ] = 1.44% (30 _×_ protosolar) at altitudes
deeper than its condensation pressure. Equation (4) is integrated and solved for _T_ ( _P_ ). For this work, _T_ ( _P_ ) is altered
by varying the lapse rate at altitudes shallower than a prescribed boundary pressure. At altitudes deeper than this
boundary pressure, _T_ ( _P_ ) is set to the dry adiabat profile used throughout this paper. We run three models fitting
∆ _T_ _b_ between 66 _[◦]_ S-50 _[◦]_ S and 36 _[◦]_ S-12 _[◦]_ S. Model 1 sets the boundary pressure at the onset of H 2 S-ice formation and
does not allow H 2 S to supersaturate. Model 2 sets the boundary pressure at the onset of NH 4 SH formation and does
not allow H 2 S to supersaturate. Model 3 sets the boundary pressure at the onset of NH 4 SH formation and _does_ allow
H 2 S to supersaturate. Both the lapse rate and condensible profiles are varied independently between latitude bands.
Figures A3 and A4 plot the retrieved gas and temperature profiles and their corresponding residual spectra, respectively, for each of the three models. Table A1 lists the retrieved model parameters, showing that similar NH 3 and
H 2 S profiles are obtained regardless of the chosen boundary pressure, where the lapse rate begins to vary. Figure
A5 plots the _χ_ [2] goodness-of-fit as a function of wavelength for the best fitting spectra in each of the three models
considered. Only when supersaturated is allowed (model 3) can a good fit be obtained at 0.9 cm. Allowing latitudinal
temperature variations without H 2 S supersaturation (models 1 and 2) can not explain all the observed data. In fact,
the retrieved latitudinal differences in the kinetic temperature are consistent with zero, as shown in Figure A6. While
the 0.9 cm datum is just one point of evidence in favor of supersaturated H 2 S, it can not be explained away by an error
in calibration, as discussed in Section 4.3. Figure A3 also shows that the retrieved temperature-pressure profiles are
consistent with a dry adiabat while few retrievals follow the lapse rate of a wet adiabat, consistent with the findings
in Section 4.2. We therefore conclude that latitudinal variations in the opacity due to the condensible species are the
cause of Neptune’s observed brightness temperature distribution, and the current fitting favors supersaturation of H 2 S
at the coldest latitudes.

29

30



66°S - 50°S: Model 1 66°S - 50°S: Model 2 66°S - 50°S: Model 3



10.0


7.5


5.0


2.5


0.0


2.5


5.0


7.5


10.0



10.0


7.5


5.0


2.5


0.0


2.5


5.0


7.5


10.0



10.0


7.5


5.0


2.5


0.0


2.5


5.0


7.5


10.0



**Figure** **A4.** Random retrieved model spectra fitting the observed ∆ _T_ _b_ between 66 _[◦]_ S-50 _[◦]_ S and 36 _[◦]_ S-12 _[◦]_ S for the three types of
models considered in this section. Only model 3, which allows H 2 S supersaturation at its ice cloud, provides a good fit to the
data at 0.9 cm.


Latitude Bin: 66 _[◦]_ S _−_ 50 _[◦]_ S 36 _[◦]_ S _−_ 12 _[◦]_ S

Free Parameter Retrieved values                     - Model 1

H 2 S below NH 4 SH 0 _._ 9 [+0] _−_ 0 _[.]_ _._ [3] 2 _[×]_ [ 10] _[−]_ [3] 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [3] 2 _[×]_ [ 10] _[−]_ [3]

NH 3 below NH 4 SH 2 _._ 6 [+2] _−_ 1 _[.]_ _._ [8] 3 _[×]_ [ 10] _[−]_ [4] 0 _._ 6 [+2] _−_ 0 _[.]_ _._ [5] 3 _[×]_ [ 10] _[−]_ [4]

H 2 S _H_ rel (%) 48 [+3] _−_ 6 91 [+7] _−_ 14
Γ (K/km) 1 _._ 17 [+0] _−_ 0 _[.]_ _._ [04] 06 1 _._ 17 [+0] _−_ 0 _[.]_ _._ [05] 05

Free Parameter Retrieved values                     - Model 2

H 2 S below NH 4 SH 1 _._ 0 [+0] _−_ 0 _[.]_ _._ [2] 3 _[×]_ [ 10] _[−]_ [3] 1 _._ 0 [+0] _−_ 0 _[.]_ _._ [2] 2 _[×]_ [ 10] _[−]_ [3]

NH 3 below NH 4 SH 3 _._ 3 [+2] _−_ 1 _[.]_ _._ [9] 8 _[×]_ [ 10] _[−]_ [4] 0 _._ 4 [+1] _−_ 0 _[.]_ _._ [0] 3 _[×]_ [ 10] _[−]_ [4]

H 2 S _H_ rel (%) 44 [+5] _−_ 6 92 [+6] _−_ 13
Γ (K/km) 1 _._ 11 [+0] _−_ 0 _[.]_ _._ [03] 02 1 _._ 12 [+0] _−_ 0 _[.]_ _._ [03] 03

Free Parameter Retrieved values                     - Model 3

H 2 S below NH 4 SH 1 _._ 0 [+0] _−_ 0 _[.]_ _._ [3] 3 _[×]_ [ 10] _[−]_ [3] 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [3] 3 _[×]_ [ 10] _[−]_ [3]

NH 3 below NH 4 SH 2 _._ 5 [+2] _−_ 1 _[.]_ _._ [7] 7 _[×]_ [ 10] _[−]_ [4] 0 _._ 5 [+1] _−_ 0 _[.]_ _._ [8] 4 _[×]_ [ 10] _[−]_ [4]

H 2 S _H_ rel (%) 51 [+4] _−_ 6 _≥_ 72
_P_ _ss_ (bar) — _≥_ 6 _._ 8
Γ (K/km) 1 _._ 11 [+0] _−_ 0 _[.]_ _._ [02] 03 1 _._ 12 [+0] _−_ 0 _[.]_ _._ [02] 04


**Table** **A1.** Retrieved parameters for each of the three models considered in this section.


REFERENCES



Asplund, M., Grevesse, N., Sauval, A. J., Scott, P., 2009,


Annual Review of Astronomy and Astrophysics, 47, 481


Atreya, S. K. & Wong, A., 2005, Space Sci. Rev. 116, 121


Atreya S. K., Hofstadter M. D., Reh K. R., et al., 2019,


Acta Astronautica, 162, 266


Baines, K. H., Mickelson, M. E., Larson, L. E., Ferguson,


D. W., 1995, Icarus, 114, 328


Burgdorf, M., Orton G. S., Davis G. R., et al . 2003, Icarus,


164, 244.


Conrath, B., Gierasch, P., Ustinov, E. A., 1998, Icarus, 135,


501


DeBoer, D. R. & Steffes, P. G., 1996, Icarus 123, 324


de Kleer, K., Luszcz-Cook S., de Pater, I., et al., 2015,


Icarus, 256, 120



de Pater, I., Fletcher, L. N., Luszcz-Cook, S., et al. 2014,


Icarus, 237, 211


de Pater, I. & Massie, S. T., 1985, Icarus 62, 143


de Pater, I. & Mitchell, D. L., 1993, JGRE, 98, 5471


de Pater, I. & Richmond, M., 1989, Icarus, 80, 1


de Pater, I., Romani, P. N., Atreya, S. K., 1991, Icarus, 91,


220


de Pater, I., DeBoer, D., Marley, M., 2005, Icarus, 173(2),


425


de Pater, I., Butler B., Sault, R., et al. 2018, Science with a


Next Generation Very Large Array: Potential for Solar


System Science with the ngVLA. Astronomical Society of


the Pacific


de Pater, I., 2018. Nature Astronomy, 2, 364

31



10





8


6


4


2


0

0.1 1 10
Wavelength (cm)


**Figure** **A5.** _χ_ [2] goodness-of-fit versus wavelength corresponding to the best fitting residual spectra ∆ _T_ _b_ given in Fig. A4,
showing that a good fit is achieved everywhere only when H 2 S is allowed to supersaturate (Model 3). Varying temperature
without allowing supersaturation (models 1 and 2) does not produce a good fit at the 0.9 cm data point. The total _χ_ [2] for each
model is given in the plot legend.


1.2


1.0


0.8


0.6


0.4


0.2


0.0

1 0 1
Temperature Difference
from 36 S 12 S at 5 bar


**Figure** **A6.** Distribution of retrieved kinetic temperature differences between 66 _[◦]_ S-50 _[◦]_ S and 36 _[◦]_ S-12 _[◦]_ S at 5 bar for model 3.
Differences are consistent with zero and no larger than 1 K.



de Pater, I., Sault, R., Wong, M. H., et al., 2019, Icarus,


322, 168


de Pater, I., Moeckel, C., Tollefson, J., et al., 2020,


Prospects to study the Ice Giants with the ngVLA, A


white paper submitted to the 2023-2032 decadal survey


Dyudina, U. A., Ingersoll, A. P., Ewald, S. P., et al., 2008.


Science, 319, 1801


Fegley, B. Jr. & Prinn R. G., ApJ, 307, 852


Fitzpatrick, P. J., de Pater, I., Luszcz-Cook, S., Wong, M.


H., Hammel, H. B., 2014, Ap&SS, 350, 65


Fletcher, L. N., et al. 2009, Icarus, 202, 543



Fletcher, L. N., Achterberg, R. K., Greathouse, T. K., et al.

2010, Icarus, 208, 337

Fletcher, L. N., de Pater, I., Orton, G. S., et al. 2014,

Icarus, 231, 146

Fletcher, L. N., Irwin, P. G. J., Orton, G. S., et al. 2008.

Science, 319, 79

Fletcher, L. N., de Pater I., Orton G. S., et al. 2020. Space

Science Reviews, 216, 21

Foreman-Mackey, D., Hogg, D. W., Lang, D., and

Goodman, J., 2013, PASP, 125, 306

Goodman, J. & Weare, J., 2010, Commun. Appl. Math.

Comput. Sci, 5, 65

32


Gulkis S., Janssen M. A., Olson E. T., 1978. Icarus, 34 (1),

10

Hammel, H. B., Sitko, M. L., Lynch, D. K., et al. 2007, AJ,

134

Hersant, F., Gautier, D., Lunine J. I., 2004. Planetary and
Space Science, 52 (7), 623

Hofstadter, M., Simon, A., Atreya, S., et al. 2019.

Planetary and Space Science, 177, 104680

Hueso, R. & S´anchez-Lavega, A. 2019. Space Sci. Rev. 215,

52

Irwin P. G., Lellouch E., de Bergh C., et al. 2014. Icarus,

227, 37

Irwin P. G., Toledo, D., Garland, R., et al. 2019. Nature

Astronomy, 2, 420

Irwin, P. G., Toledo, D., Garland, R., et al. 2019. Icarus,

321, 550

Irwin, P. G., Toledo, D., Ashwin B. S., et al. 2019. Icarus,

331, 69

anssen, M. A., Oswald, J. E., Brown, S. T., et al. 2017.

Space Sci. Rev. 213, 139

Karkoschka, E. & Tomasko, M. G., 2011, Icarus, 211, 780

Lewis, J. S., 1969, Icarus, 10, 365

Lindal, G. F., 1992, AJ, 103, 967
Luszcz-Cook, S., de Pater, I., Ad´amkovics, [´] M., et al. 2010,

Icarus, 208, 938

Luszcz-Cook, S., de Pater, I., Wright, M., 2013a, Icarus,

226, 437

Luszcz-Cook, S., de Pater, I. 2013b, Icarus, 222, 379
Luszcz-Cook, S., de Kleer, K., de Pater, I., Ad´amkovics, [´]

M., Hammel, H., 2016, Icarus, 276, 52

Martin, S. C., de Pater, I., Marcus, P., 2012, Ap&SS 337, 65

Massie, S. T. & Hunten, D. M., 1982, Icarus 49, 213

Molter, E., de Pater, I., Luszcz-Cook, S., et al. 2019, Icarus,

321, 324



Molter, E., de Pater, I., Luszcz-Cook, S., et al. 2020,


Planetary Science Journal, in press


Moses J. I., Allen M., Yung Y. K., 1992, Icarus, 99, 318


Orton, G. S., Encrenaz, T., Leyrat, C., Puetter, R.,


Friedson, A. J., 2007, A&A 473, L5


Rymer A., et al., 2020, Neptune Odyssey Flagship Concept


to the Neptune-Triton System. A white paper submitted


to the Planetary Science and Astrobiological Decadal


Survey 2023-2032.


Sault, R. J., Teuben P. J., & Wright M. C. H., in


Astronomical Data Analysis Software and Systems IV,


ed. R. Shaw, H.E. Payne, & J.J.E.Hayes, ASP Conf. Ser.,


77, 433


Selina R. J., Murphy E. J., McKinnon M., et al., 2018,


Science with a Next Generation Very Large Array: The


ngVLA Reference Design. Astronomical Society of the


Pacific.


Spiegelhalter, D. J., Best, N. G., Carlin, B. P., and Van Der


Linde, A., 2002, Journal of the Royal Statistical Society:


Series B (Statistical Methodology), 64, 583


Tollefson, J., de Pater, I., Marcus, P. S., et al. 2018, Icarus,


311, 317


Tollefson, J., de Pater, I., Luszcz-Cook S. C., et al. 2019,


ApJ, 157, 251


Trafton, L. M., 1967, ApJ, 147, 765


Warwick, J. W., et al., 1989., Science, 246, 1498


Wallace, L., 1980., Icarus, 43, 231


Weidenschilling, S. & Lewis, J., 1973, Icarus 20, 465


Young K. C., 1993, Microphysical processes in clouds.


Oxford University Press, New York NY USA.


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Autocorrelation time checked against step count; posterior distributions inspected after 50% burn-in; south polar fit compared against 2003 VLA data",
  "failed_quote": "A comparison to south polar 2003 VLA data are overplotted as well, showing good agreement."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Simultaneously fit absolute brightness temperatures in 36S-12S and temperature differences Delta T_b between 36S-12S and other latitude bands using Eq. 4, allowing H2S subsaturation or supersaturation up to P_ss, and compare wet vs dry adiabats using the Deviance Information Criterion (DIC).",
  "failed_quote": "In this section, we simultaneously model the atmospheric properties matching both the observed brightness temperature within the 36 [◦] S − 12 [◦] S latitudinal band, and the observed temperature differences between 36 [◦] S − 12 [◦] S and other latitudes."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Deep H2S abundance below all clouds (dry adiabat) = 1.3e-3 dimensionless",
  "failed_quote": "Below all cloud formation, we obtain H 2 S abundances of 8 . 7 [+2] − 1 [.] . [6] 7 [×] [10] [−] [4] [(37] [.] [3] [+15] − 10 [.] . [7] 3 [×] [ protosolar)] for a wet adiabat and 1 . 3 [+0] − 0 [.] . [4] 3 [×] [ 10] [−] [3] [(53] [.] [8] [+18] − 13 [.] . [9] 4 [×] [protosolar)] [for] [a] [dry] [adiabat.]"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Deep H2S abundance below all clouds (wet adiabat) = 8.7e-4 dimensionless",
  "failed_quote": "Below all cloud formation, we obtain H 2 S abundances of 8 . 7 [+2] − 1 [.] . [6] 7 [×] [10] [−] [4] [(37] [.] [3] [+15] − 10 [.] . [7] 3 [×] [ protosolar)] for a wet adiabat and 1 . 3 [+0] − 0 [.] . [4] 3 [×] [ 10] [−] [3] [(53] [.] [8] [+18] − 13 [.] . [9] 4 [×] [protosolar)] [for] [a] [dry] [adiabat.]"
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "Neptune's south polar region (90S-66S) is 5-40 K brighter than the mid-latitudes and northern equatorial region depending on wavelength, consistent with subsiding air depleted in H2S and NH3 down to ~33-41 bar.",
  "failed_quote": "Depending on wavelength, the south polar region is 5 40 K brighter than the mid-latitudes and northern equatorial region."
 },
 {
  "path": "reasoning.why_this_method.evidence[2]",
  "value": "Coupling Radio-BEAR to emcee MCMC provides full posterior uncertainty distributions on atmospheric parameters (unlike forward model chi-squared ruling out in Tollefson et al. 2019), PSF-scale avoids expensive 2D disk convolutions at every MCMC step, and fitting differential temperatures Delta T_b mitigates the 5% flux calibration error.",
  "failed_quote": "One shortcoming of the analysis in the previous section is that the calibration error masks the evident brightness variations across the disk. In this section, we simultaneously model the atmospheric properties matching both the observed brightness temperature within the 36 [◦] S − 12 [◦] S latitudinal band, and the observed temperature differences between 36 [◦] S − 12 [◦] S and other latitudes."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "High degree of longitudinal smearing in the maps because Neptune was observed over nearly a full 16.11 hr rotation period.",
  "failed_quote": "Thus, the degree of longitudinal smearing is high in the resulting maps as we observe Neptune throughout nearly an entire 16.11 hr rotation period (Warwick et al. 1989)."
 }
]
```
