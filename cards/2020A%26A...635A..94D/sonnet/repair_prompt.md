# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...635A..94D\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
A&A 635, A94 (2020)
[https://doi.org/10.1051/0004-6361/201732243](https://doi.org/10.1051/0004-6361/201732243)
© E. Di Folco et al. 2020


## **Astronom** **y**
#### &
## **Astrophysics**


### **An ALMA/NOEMA study of gas dissipation and dust evolution** in the 5 Myr-old HD 141569A hybrid disc [⋆]

E. Di Folco [1,2], J. Péricaud [1,2], A. Dutrey [1,2], J.-C. Augereau [3], E. Chapillon [4], S. Guilloteau [1,2],
V. Piétu [4], and A. Boccaletti [5]


1 Univ. Bordeaux, LAB, UMR 5804, 33270 Floirac, France
e-mail: `[emmanuel.di-folco@u-bordeaux.fr](mailto:emmanuel.di-folco@u-bordeaux.fr)`
2 CNRS, LAB, UMR 5804, 33270 Floirac, France
3 Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France
4 IRAM, 300 rue de la piscine, 38406 Saint Martin d’Hères, France
5 LESIA, Observatoire de Paris, PSL Research Univ., CNRS, Univ. Paris Diderot, Sorbonne Paris Cité, UPMC Paris 6,
Sorbonne Univ., 5 place Jules Janssen, 92195 Meudon CEDEX, France


Received 6 November 2017 / Accepted 30 October 2019


**ABSTRACT**


_Context._ The study of gas-rich debris discs is fundamental to characterising the transition between protoplanetary discs and debris
discs.
_Aims._ We determine the physical parameters of the brightest gas-rich debris disc orbiting HD 141569A.
_Methods._ We analyse images from the NOrthern Extended Millimeter Array (NOEMA) [1] and the Atacama Large Millimeter/
submillimeter Array (ALMA) in [12] CO, [13] CO _J_ = 2→1, and [13] CO _J_ = 1→0 transitions. We incorporate ALMA archival data of the
12 CO _J_ = 3→2 transition and present continuum maps at 0.87, 1.3, and 2.8 mm. We use simple parametric laws with the Diskfit code
and MCMC exploration to characterise the gas disc parameters and report a first attempt to characterise its chemical content with
IRAM-30 m.
_Results._ The continuum emission is equally shared between a compact (≲50 au) and a smooth, extended dust component (∼350 au).
Large millimetre grains seem to dominate the inner regions, while the dust spectral index is marginally larger in the outer region. The
12 CO is optically thick, while 13 CO is optically thin with τ 13 CO ∼ 0.15 (C 18 O is not detected). The 13 CO surface density is constrained
to be one order of magnitude smaller than around younger Herbig Ae stars, and we derive a gas mass _M_ 12 CO = 10 [−][1] _M_ ⊕ . We confirm
the presence of a small CO cavity ( _R_ CO = 17 ± 3 au), and find a possibly larger radius for the optically thin [13] CO _J_ = 2→1 transition
(35 ± 5 au). We show that the observed CO brightness asymmetry is coincident with the complex ring structures discovered with
VLT/SPHERE in the inner 90 au. The [12] CO temperature _T_ 0 (100 au) ∼ 30 K is lower than expected for a Herbig A0 star, and could be
indicative of subthermal excitation.
_Conclusions._ With the largest amount of dust and gas among hybrid discs, HD 141569A shows coincident characteristics of both protoplanetary discs (central regions), and debris discs at large distance. Together with its morphological characteristics and young age, it
appears to be a good candidate to witness the transient phase of gas dissipation, with an apparently large gas-to-dust ratio ( _G_ / _D_ - 100)
favouring a faster evolution of dust grains.


**Key words.** accretion, accretion disks – methods: observational – techniques: interferometric – protoplanetary disks –
stars: pre-main sequence – radio lines: stars



**1. Introduction**


The evolution of circumstellar discs from the initial reservoir
of the interstellar medium (ISM)–dust and gas mixture towards
planetary systems is governed by the growth and coagulation
of dust grains, viscous spreading and accretion onto the central star (or on proto-planets), and dissipation of the primordial
gas (Williams & Cieza 2011). Although a large amount of
high-resolution images and spectroscopic data have been collected during recent decades, the various stages of disc evolution
remain poorly constrained by observations (Wyatt et al. 2015).
The main accretion phase corresponds to the Class II phases
for T Tauri (TTS) and Herbig Ae (HAe) stars. The final phase
is represented by debris discs, when the primordial reservoir
has been fully dissipated and/or incorporated into planetesimals


⋆ Reduced datacubes and images are only available at the CDS via
anonymous ftp to `[cdsarc.u-strasbg.fr](http://cdsarc.u-strasbg.fr)` ( `[130.79.128.5](ftp://130.79.128.5)` ) or via
```
http://cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/635/A94

```


and planets, and the detected emission from second-generation
dust comes from collisions between the leftovers of planet formation or comet evaporation (Wyatt 2008; Hughes et al. 2018).
Evidence for structural changes has been collected for a large
number of pre-main sequence stars at various stages of the disc
evolution (e.g. Andrews et al. 2018; Avenhaus et al. 2018; Garufi
et al. 2018). This includes the presence of spirals, rings and gaps,
central cavities, or azimuthal asymmetries, where different processes are at play such as the protoplanet(s)–disc gravitational or
hydrodynamical interaction, viscous evolution, grain growth and
opacity change, gas-grain hydrodynamical interaction, the development of vortices and magneto-rotational instabilities, and the
photo-evaporation of gas. Transitional discs with large dust cavities (e.g. Espaillat et al. 2014) were found to represent almost
30% of the millimetre(mm)-bright discs in Taurus and Ophiuchus regions (Andrews et al. 2011). These systems show a lack
of continuum mm emission with dust depletion factors in the
range of 100–1000 in the disc central regions, while a variety


A94, page 1 of 16



[Open Access article, published by EDP Sciences, under the terms of the Creative Commons Attribution License (](http://www.edpsciences.org) `[http://creativecommons.org/licenses/by/4.0](http://creativecommons.org/licenses/by/4.0)` ),
which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.

A&A 635, A94 (2020)



of gas depletion factors have been reported within these cavities (e.g. van der Marel et al. 2016, 2018). They may witness
gravitational interaction between gas and sub-stellar/planetary
companion(s) in the disc cavity, and drag forces between dust
grains and gas may cause the mm grains to be trapped by pressure bumps at large radial distances (e.g. Zhu et al. 2011; Pinilla
et al. 2012).
While the timescale for disc dissipation has been constrained
to about 5 Myr from the fading of infrared (IR)-excess (for dust)
and of accretion tracers or molecular lines (for gas) in young
clusters (Haisch et al. 2001; Fedele et al. 2010), very few systems are known in the transition phase between protoplanetary
and debris discs. A new category of discs has emerged in recent
years, which simultaneously display the typical characteristics
of debris discs (with in particular a weak fractional excess of
IR emission _f_ d = _L_ IR / _L_ ⋆ < 10 [−][2] originating from the optically thin dust component of second-generation grains), and the
presence of gas tracers (mostly CO lines) that reveal a nonnegligible residual gaseous component (Zuckerman et al. 1995;
Moór et al. 2011). Although only a handful of such gas-rich
debris discs were known when we started the present project
(namely HD 21997, 49 Ceti, β Pictoris), this population has now
grown to almost twenty members with typical ages in the range
of 10–40 Myr (e.g. Lieman-Sifry et al. 2016; Moór et al. 2017).
The origin of the remnant gas is still a subject of controversy:
the age of the system must be compared to the lifetime of the
detected molecular species, which itself depends on the UV/
X-ray stellar/interstellar emission and on the (complex) shielding
effects (Kral et al. 2017). Those systems harbouring supposedly primordial gas are called hybrid discs (Kóspál et al. 2013).
The gas-rich debris discs revealed by CO lines simultaneously
display a weak dust mm continuum and an IR excess characteristic of more evolved, optically thin debris discs. These systems
are thought to witness a short-lived transient phase at the interface between proto-planetary and debris discs, when the material
dissipates through photo-evaporation and accretion. In Péricaud
et al. (2017), we reported a correlation between the CO flux
density and the mm continuum emission for a broad variety of
systems including T Tauri, Herbig Ae, transition discs, and even
the proto-typical young debris disc β Pic. The position of hybrid
discs in the diagram, systematically above the correlation line,
suggests a faster evolution of the dust in these systems, leading
to a transient and unusual increase of the gas-to-dust ratio.
In this population, the Herbig B9.5V/A0Ve star HD 141569A
holds a very peculiar and interesting position. The star is located
at 110.6 ± 0.5 pc (Gaia Collaboration 2018), and has two M-stars
companions whose gravitational link remains unclear (Reche
et al. 2009). With an age of about 5 ± 3 Myr (Weinberger
et al. 2000; Merín et al. 2004), it is the youngest debris disc
in this population with an IR brightness twice as large as that
of β Pic. With the new _Gaia_ distance, the stellar luminosity
determined in Merín et al. (2004) turns to 27.0 ± 3.6 _L_ ⊙ . In IR
colour-magnitude diagrams, HD 141569A lies at the exact interface between proto-planetary and debris discs (see, e.g. Wyatt
et al. 2015, and Fig. 1 therein). Its cold molecular content was
discovered through its CO emission line in the spectroscopic survey of Zuckerman et al. (1995), whereas warmer CO gas was
later detected in the inner system by Goto et al. (2006). The
debris disc of HD 141569A ( _L_ IR / _L_ ⋆ = 8.4 × 10 [−][3], Sylvester et al.
1996) revealed by optical/IR dust emission presents a complex
multiple-ring architecture with spirals, arcs, and gaps imaged in
scattered light by the HST (Augereau et al. 1999; Weinberger
et al. 1999; Mouillet et al. 2001; Boccaletti et al. 2003; Clampin
et al. 2003; Konishi et al. 2016). More recently, a series of


A94, page 2 of 16



concentric rings was discovered with VLT/SPHERE with a range
of radii of 40–90 au (Perrot et al. 2016), partially corroborating
the emission detected around 40 au in the _L_ [′] band by Currie et al.
(2016) with Keck/NIRC2.
While the small-grain component has been well studied in
the near-infrared (NIR), a thorough analysis of the larger grains
observed at mm wavelengths and a comparative physical and
morphological analysis of the CO gas distribution is crucial
to understanding its evolution status as well as the nature of
the observed dust and gas components. Our group obtained
observations of HD 141569A in 1999–2000 with the Plateau
de Bure Interferometer (PdBI) of Institut de Radio-Astronomie
Millimétrique (IRAM), where the gas disc was already partly
resolved (briefly reported in Dutrey et al. 2004). These early
observations have motivated the present study, but their quality and sensitivity is outmatched by the current dataset and will
therefore not be presented here. Observations of this system by
the Submilliter Array (SMA), Combined Array for Research in
Millimeter-wave Astronomy (CARMA), and the Atacama Large
Millimeter/submillimeter Array (ALMA) have been reported,
revealing an extended gas disc (from the [12] CO _J_ = 3→2 transition) out to the 250 au main dust ring highlighted in early HST
images, and a dust disc extending out to 56 AU from the 870 µm
continuum observations (White et al. 2016; Flaherty et al. 2016).
The total mass of gas was revised to values much larger than
initially derived thanks to the optically thin line [13] CO _J_ = 2→1
(Miley et al. 2018). From the mm continuum emission, a double component with spectral indices consistent with the range of
values observed in both debris and primordial discs was reported
by White & Boley (2018), and an unresolved dust ring peaking at
220 au was detected from 1.3 mm ALMA observations by Miley
et al. (2018). In this article, we present complementary, multifrequency observations with ALMA and the NOrthern Extended
Millimeter Array (NOEMA) [1] (Sect. 2). We characterise the dust
mm continuum and the gas emission, taking advantage of the
spectral information to derive constraints on the grain growth
and emission lines opacities (Sect. 3). We finally model the
12 CO and 13 CO lines with the radiative transfer code Diskfit
(Piétu et al. 2007) to characterise the temperature and density
laws in this disc (Sect. 4). In Sect. 5, we finally compare the
derived morphology at mm wavelengths with the dust disc seen
in optical/IR domain and use the new constraints on the gas and
dust mass to discuss the origin of the gas and the evolution status
of this peculiar system.


**2. Observations**


_2.1. PdBI/NOEMA observations_


HD 141569 was observed with NOEMA during three runs from
December 2014 to April 2016. The [12] CO _J_ = 2→1 transition at
230.538 GHz was mapped with the 7D and 7C configurations
(7 antennas) of the IRAM array, with an angular resolution of
2.4 [′′] × 1.2 [′′] (baseline lengths from 15 to 192 m; all subsequent
angular resolution values correspond to natural weighting). The
spectral setup used a narrow band (20 MHz bandwidth, resolution 0.20 km s [−][1] ). Excellent conditions are noteworthy for one
track, with precipitable water vapour inferior to 1.5 mm, and a
15 [◦] mean phase rms.
13
In winter 2014/2015, we also obtained CO _J_ = 2→1
(220.399 GHz) observations. The 6C and 7D configuration


1 Based on observations carried out with the IRAM Plateau de Bure
Interferometer. IRAM is supported by INSU/CNRS (France), MPG
(Germany), and IGN (Spain).

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc



antennas were used with a total on-source time of 12.7 h. We
reached a 2.3 [′′] × 1.2 [′′] angular resolution (baseline lengths from
15 to 176 m) and used the same spectral resolution as for
12
CO _J_ = 2→1. For both transitions, 1546+027 and 1508-055
were used for amplitude and phase calibration and we bootstrapped their fluxes using MWC 349 observations (with a flux
model of 1.86 Jy at 219 GHz and 1.91 Jy at 230.5 GHz).
The WIDEX correlator provided 4 GHz bandwidth during
the observations of the [12] CO and [13] CO. Combining the two
observations at 1.3 mm, we obtained a 2.1 [′′] × 1.0 [′′] beam for the
continuum map.


_2.2. ALMA observations_


We obtained ALMA observations of HD 141569 in Band 3
(84−116 GHz). The data were recorded in August 2015 for the
13 18
CO _J_ = 1→0 (110.201 GHz) and C O _J_ = 1→0 (115.271 GHz)
transitions during two runs with 39 and 44 antennas, respectively (project 2013.1.00883, PI. Péricaud). The spatial resolution
was 0.76 [′′] × 0.56 [′′] (baselines up to 1.55 km), and the spectral
resolution 0.2 km s [−][1] . The data were collected with relatively
poor weather conditions (PWV∼ 4 mm). We used Ceres and
1550+054 for the flux and amplitude calibration, 1550+0527 and
1517-2422 for bandpass calibration and 1550+0527 for the phase
calibration.
In addition, we collected archival raw data from the project
2012.1.00698.S (PI. Boley) to complement our analysis in
Band 7 (275−373 GHz), which includes the [12] CO _J_ = 3→2 line
at 345.796 GHz. A preliminary analysis of this data set was
reported in White et al. (2016). Only a subset of the observations could be properly calibrated. The observations carried out
with 32 antennas provide a resolution of 0.43 [′′] × 0.35 [′′] (baselines up to 650 m), and a spectral resolution of 0.8 km s [−][1] . The
flux and amplitude calibrator is Titan, the phase and bandpass
calibrator is 1550+0527. We used the CASA package to calibrate
the ALMA data, and we carried out the imaging and analysis of
all NOEMA and ALMA observations with the GILDAS software. The imaging was performed with natural weighting for
both ALMA and NOEMA.


_2.3. A deep search for extra molecular lines with_
_IRAM-30 m/EMIR_


We also used the EMIR detector on the IRAM 30 m antenna
to investigate the molecular content of this hybrid disc
(Project 049-15). The observations were performed in Summer
2015 with a total time of 20 h on source. Two frequency bands
were used in this project: 87.720–93.500 GHz and 140.520–
148.300 GHz. We used Wobbler switching, resulting in very
flat baselines over the observed bandwidths. The frequency
coverage included lines of HCN _J_ = 1−0, HCO [+] _J_ = 1−0, and
CS _J_ = 3−2 that are usually bright in discs around classical T
Tauri (of order 0.5–1.0 Jy km s [−][1], see Dutrey et al. 1997) but
slightly fainter in Herbig Ae stars (e.g. MWC 480 and AB Aur,
Piétu et al. 2007; Schreyer et al. 2008). No emission was
detected. Assuming a similar line width to that of the CO lines
(7 km s [−][1] _FWHM_ ), the 3σ detection threshold on the integrated
line flux is 45 mJy km.s [−][1] around 90 GHz, and 60 mJy km.s [−][1]
around 145 GHz.


**3. Results**


_3.1. Continuum emission_


The continuum emission is resolved at the three frequencies,
although with some differences due to the different instrumental



**Table** **1.** Continuum results: best-fit parameters for: (i) a single component model (elliptical Gaussian in the _u_, v plane), (ii) and a doublecomponent model (two circular Gaussian functions after deprojection in
the _u_, v plane according to the orientation and inclination determined at
optical wavelength).


0.87 mm 1.3 mm 2.8 mm


_Synthesized beam_
Beam size _FWHM_ ( [′′] ) 0.43 × 0.35 2.1 × 1.0 0.76 × 0.56
Beam size _FWHM_ (au) 47 × 39 231 × 110 84 × 62
Beam PA ( [◦] ) 121 14 57


_Zero-baseline flux_
_F_ ν ( _u_, v ≃ 0, mJy) 6.00 ± 0.25 4.00 ± 0.25 0.70± 0.05
Spectral index [(][∗][)] (β) −0.16 ± 0.29


_Single-component fit_ EGAUSS
_F_ ν (best-fit, mJy) 3.93 ± 0.15 3.76 ± 0.29 0.39 ± 0.02
Semi-major axis _FWHM_ (au) 54 ± 2 253 ± 26 35 ± 4
Semi-minor axis _FWHM_ (au) 41 ± 2 156 ± 13 32 ± 4
Inclination ( [◦] ) 41 ± 5 53 ± 6 24
PA ( [◦] ) 2 ± 7 21 ± 8 20 ± 50


_Double-component fit_ CGAUSS
_F_ ν [tot] [(mJy)] 7.42 ± 1.42 4.20 ± 1.24 0.71 ± 0.09
_F_ ν [int] [(best-fit, mJy)] 3.02 ± 0.16 1.66 ± 0.57 0.32 ± 0.02
_FWHM_ [int] (au) 35 ± 2 _110_ ± _33_ 28 ± 6
Spectral index [(][∗][)] (β [int] ) −0.05 ± 0.07
_F_ ν [out] (best-fit, mJy) 4.4 ± 1.3 2.54 ± 0.67 0.39 ± 0.07
_FWHM_ [out] (au) 322 ± 55 _418_ ± _121_ 407 ± 66
Spectral index [(][∗][)] (β [out] ) 0.17 ± 0.23
_(_ fixed PA = 356 [◦] _, i_ = 53 [◦] _)_


**Notes.** _F_ ν ( _u_, v ≃ 0) corresponds to the maximum flux density measured
at the shortest baseline for each frequency. [(][∗][)] To compute the spectral
index, we add quadratically an arbitrary uncertainty of 10% of the flux
values to account for the instrumental calibration.


resolutions. The images presented in Fig.1 were produced using
the CLEAN deconvolution algorithm with natural weighting.
The emission appears compact, and centrally peaked, with a
possible secondary component which looks more extended in
the NOEMA map only (a low level plateau in the 1.3 mm image).
The coarser resolution of the NOEMA map (231 × 110 au) is
not the only reason: the visibility profiles presented in Fig. 1
clearly show a steep increase at the shortest baselines. This visibility rise at _u_, v distance shorter than 50–100 m (present at the
three frequencies) is characteristic of extended emission (at few
arcsec scales), while the more compact, inner disc component
is resolved at intermediate baselines (e.g. _B_ ∼ 150−400 m at
0.87 mm). The spatial extent and flux values of the continuum
emission were determined by fitting Gaussian functions in the
_u_, v plane. We tested a single and a two-component model. In
Table 1 we present the best-fit parameters for the two models,
and the measured maximum flux density corresponding to
the shortest baseline points (so called zero-baseline flux). The
single-component model is dominated by the compact disc
component (0.3–0.5 [′′] ) at 0.87 and 2.8 mm, while at 1.3 mm
only the broad component (2–3 [′′] ) is constrained. Therefore,
the flux values for this model cannot be used together to
estimate the dust spectral index. Our maximum flux values
from the shortest baselines are consistent with those reported
by single-dish observations or compact arrays (see Table 2). At
1.3 mm, we measure _F_ 230 GHz ( _u_, v ≃ 0) = 4.00 ± 0.25 mJy, in
agreement with the JCMT/SCUBA measurement (5.4 ± 1.0 mJy,


A94, page 3 of 16

A&A 635, A94 (2020)


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **1.** _Left_ _column_ : continuum emission maps, all contours are set with 3σ spacing, _panel_ _a_ : ALMA data at 0.87 mm, σ = 0.051 mJy beam [−][1],
contours; ( _c_ ) NOEMA data at 1.3 mm, σ = 0.078 mJy beam [−][1] ; ( _e_ ) ALMA data at 2.8 mm, σ = 0.008 mJy beam [−][1] . We note that the scale of _panel c_
is changed to include the more extended emission. _Right column_ : real part of the visibility (with spatial binning) as a function of the _u_, v radius in
the Fourier plane, _panels b, d, and f_ : correspond to data in panels a, c, and e, respectively.


A94, page 4 of 16

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc



**Table 2.** Continuum flux comparison.


Instrument Beam ( [′′] ) _F_ ν [tot] [(][mJ][y)] _F_ ν [int] [(][mJ][y)] _F_ ν [out] (mJy) Ref


λ = 0.87 µm
APEX 19.2 12.6 ± 4.6 1

SMA 1.7 × 1.2 8.2 ± 2.4 2

ALMA 0.4 × 0.3 3.8 ± 0.4 3

ALMA 0.4 × 0.3 16.8 ± 1.7 5.8 ± 0.5 11.0 ± 1.2 4

ALMA 0.4 × 0.3 7.4 ± 1.4 3.0 ± 0.2 4.4 ± 1.3 –


λ = 1.3 µm
JCMT 22.0 5.4 ± 1.0 5

ALMA 0.65 1.7 1.7 6

ALMA 1.0 × 1.0 7.0 2.8 4.2 4

NOEMA 2.1 × 1.0 4.2 ± 1.2 1.7 ± 0.6 2.5 ± 0.7 –


λ = 2.8 µm
CARMA 5.1 × 4.2 0.8 ± 0.3 2

ALMA 0.7 × 0.5 0.42 ± 0.05 7

ALMA 0.7 × 0.5 1.25 0.62 0.63 4

ALMA 0.8 × 0.6 0.7 ± 0.1 0.32 ± 0.02 0.39 ± 0.07 –


**References.** (1) Nilsson et al. (2010); (2) Flaherty et al. (2016); (3)
White et al. (2016); (4) White & Boley (2018); (5) Sylvester et al. (2001);
(6) Miley et al. (2018); (7) White et al. (2018); (–) this work: best-fit
values from the two-component model.


Sylvester et al. 2001), but our value is about three times larger
than the ALMA measurement of 1.7 mJy reported in Miley
et al. (2018). Typical calibration uncertainties would amount to
∼10% for both instruments, but cannot justify this discrepancy.
At 2.8 mm (and 0.87 mm resp.) our measurements are consistent
with the CARMA (resp. SMA) values _F_ 110 GHz = 0.78 ±
0.30 mJy (resp. _F_ 230 GHz = 8.2 ± 2.4 mJy, Flaherty et al. 2016).
Because the inner component is very compact, the disc orientation and aspect ratio are only roughly reproduced by the elliptical
Gaussian fit in the single component model (see Table 1). In the
more realistic double component model below, we therefore first
deprojected the visibilities assuming the geometric parameters
derived at optical wavelength (PA= 356 [◦], _i_ = 53 [◦], Augereau
et al. 1999), and then fit in the _u_, v plane with a circular Gaussian
function.
The second model suggests that the emission is about equally
shared between a compact component, which is concentrated
within about 50 au ( _FWHM_ [int] ∼ 30−35 au, a value comparable
to the interferometric beams at 0.87 and 2.8 mm), and a much
broader component that extends out to about 350 au. The _u_, v
plane coverage does not allow precise determination of the outer
radius, and most of the flux of this extended component is filtered by the interferometer at 0.87 and 2.8 mm. It is marginally
detected as a low-level plateau in the 1.3 mm map thanks to
the larger beam (although its shape and radial extent cannot be
fully determined in our data). From higher-resolution ALMA
data (0.65 [′′] beam) at 1.3 mm, Miley et al. (2018) revealed a lowlevel ring-like emission peaking at 220 ± 10 au that cannot be
seen in our NOEMA map. This unresolved ring is different from
the extended component that we report from our analysis of the
_u_, v plane. In our higher-resolution maps at 0.87 and 2.8 mm, no
such ring-like emission is detected. Assuming a spectral index
α mm = 2 (see below), and extrapolating the 220 au ring peak
brightness and our brightness sensitivity at 0.87 mm (0.4 [′′] beam)
and 2.8 mm (0.66 [′′] beam), it would be marginally detectable
at the ∼3 and 5 σ level, respectively. Such a two-component



model was also proposed by White & Boley (2018) from _u_, v
plane fitting, but our results disagree with their total flux values (e.g. _F_ 345 GHz = 16.8 ± 1.7 mJy), which are systematically
larger than both the zero-baseline flux values, and the earlier
SMA, APEX, CARMA or JCMT observations (Flaherty et al.
2016; Nilsson et al. 2010; Sylvester et al. 2001). The observed differences between the flux values summarized in Table 2 can be
explained firstly by the assumed shape of the model components
(Gaussian, uniform discs, rings, power-laws), and the number
of emission components taken into account. Secondly, the veryshort-baseline information is not always taken into account in the
data analysis (e.g. White et al. 2016; Miley et al. 2018). Thirdly,
the _u_, v coverage and the field of view can vary significantly
between instruments, and the signal-to-noise ratio as a function
of ( _u_, v) radius can be very different from one dataset to another
(e.g. at 1.3 mm).
We estimate the dust spectral index β from the slope of
the spectral flux density, and we first add quadratically a typical calibration uncertainty of 10% to the flux density values. The spectral index is defined as β = α − 2, with α =
log( _F_ ν 1 / _F_ ν 2 )/ log(ν 1 /ν 2 ), _F_ ν . A fit to the three frequencies yields
the slope α. We derive the spectral index β in two cases:
(i) for the global disc using the maximum flux values measured
at the shortest baselines ( _u_, v) ∼ 0, (ii) for the double component
model, which provides a more realistic description of the continuum emission than the single-component model. The values
reported in Table 1 suggest that the spectral index is significantly smaller than the canonical ISM value with β ≤ 0.7 at
the 3σ level. Whether this is indicative of grain growth or optically thick emission can only be determined with more resolved
observations. In the disc modelling by Thi et al. (2014), the
dust component is optically thin from optical up to mm wavelength both in the radial and vertical directions, and we therefore
expect the constraints on the spectral index to primarily reflect
a change in grain properties. Radial variations of this spectral
index may also be expected, as already demonstrated in a sample of TTS and HAe stars (Guilloteau et al. 2011; Pérez et al.
2012). The double-component model suggests a larger value of
β for the more extended disc component, although the difference
with the inner 35 au region is not statistically significant. A similar trend has been claimed by White & Boley (2018), although
their spectral index value for the outer component β = 0.28 ±
0.18 may be biased by an overly large flux value at 345 GHz, as
explained above. A dense _u_, v coverage at both short and very
long baselines would be required to firmly establish a change of
dust properties between the inner compact and the extended dust
disc components.


_3.2. CO gas emission_


The [12] CO and [13] CO _J_ = 2→1 transitions are detected with
NOEMA at a high signal-to-noise ratio ( _S_ / _N_ ≳ 150, and _S_ / _N_ ≳
20 respectively), whereas the [13] CO _J_ = 1→0 detection with
ALMA is more marginally significant ( _S_ / _N_ ∼ 5). Integrated
intensities for all CO transitions are presented in Table 3 with
their associated spatial resolution. The intensity we derive for
the ALMA [12] CO _J_ = 3→2 observations 18.4 ± 0.3 Jy km s [−][1]
is slightly larger than (but consistent within 2σ with) the
value reported by White et al. (2016) and by Flaherty et al.
(2016) with the SMA. The intensity maps (zeroth moment)
are displayed in Fig. 2 for the three transitions (natural weighting). The [12] CO emission appears slightly more extended in
the NOEMA map because of the convolution by a larger beam.
The [13] CO _J_ = 2→1 emission appears to be more compact than


A94, page 5 of 16

A&A 635, A94 (2020)


**Table 3.** Summary of CO lines detections and setups.


Line Freq Array Beam size Beam PA CO integrated intensity Noise level
(GHz) ( [′′] ) ( [◦] ) (Jy km s [−][1] ) (mJy beam [−][1] km s [−][1] )


13
CO _J_ = 1→0 110.201 ALMA 0.70 × 0.51 58 0.16 ± 0.03 6.8
C [18] O _J_ = 1→0 109.782 ALMA 0.70 × 0.51 58 <0.05

12
CO _J_ = 1→0 115.271 CARMA [(] _[b]_ [)] 4.8 × 4.1 29 1.6 ± 0.2 [(] _[b]_ [)]


13 CO _J_ = 2→1 220.399 NOEMA 2.30 × 1.20 −172 1.2 ± 0.2 23
C [18] O _J_ = 2→1 219.560 NOEMA 2.30 × 1.20 −172 < 0.10

12
CO _J_ = 2→1 230.538 NOEMA 2.40 × 1.20 11 10 ± 1 31


12 CO _J_ = 3→2 345.796 ALMA [(] _[a]_ [)] 0.43 × 0.33 −58 18.4 ± 0.3 [(] _[a]_ [)] 40


**Notes.** [(] _[a]_ [)] Archival data from project ALMA.1.00698.S. For non detections, we provide 3σ upper limits.
**References.** [(] _[b]_ [)] From Flaherty et al. (2016).


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **2.** Maps of integrated CO emission for the
four detected transitions (the continuum was not
subtracted due to its very low level of emission). _Top_ : NOEMA observations, from left to
right: [12] CO _J_ = 2→1 (first contour at 5σ, second contour at 15σ, then 15σ spacing with σ =
31 mJy beam [−][1] km s [−][1] ), and [13] CO _J_ = 2→1 with
3σ spacing contours, σ = 23 mJy beam [−][1] km s [−][1] .
Dotted lines show negative contours in steps of
3σ. _Bottom_ : ALMA observations, from left to
right: [12] CO _J_ = 3→2 with uniform weighting to
highlight the central gas cavity (3σ spacing, σ =
40 mJy beam [−][1] km s [−][1] ), and [13] CO _J_ = 1→0 1σ
spacing contours starting at 2σ (for positive and
negative contours), σ = 6.8 mJy beam [−][1] km s [−][1] .



the [12] CO _J_ = 2→1 transition which extends beyond 2”, likely
as a result of a difference in opacity since the sensitivity and
resolution are equivalent for these two lines. We also display
the ALMA [12] CO _J_ = 3→2 emission for comparison, using uniform weighting in order to show evidence for the tiny inner gas
cavity which is readily resolved in this high-resolution image.
Given its very low level, the continuum emission was not subtracted in Fig. 2, meaning that this CO cavity cannot artificially
result from over-subtraction of the continuum. The separation of


A94, page 6 of 16



the central emission peaks is about 0.8 [′′], which translates into
a maximum cavity radius of about 45 au. This value is refined
in the subsequent modelling presented in the following sections.
The channel maps in Figs. A.1 and A.2 display the typical velocity pattern of rotating discs. In Fig. 3, the CO integrated area
maps have been superimposed to the scattered light emission
from the HST observations. These figures confirm that most of
the molecular emission is apparently less extended than the optical dust disc. The [13] CO _J_ = 1→0 transition has a rather poor

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc


**4. Modelling**



**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **3.** Integrated intensity of the CO line superimposed on the
HST scattered emission (Clampin et al. 2003). The cross indicates
the position angle and aspect ratio as determined from gas modelling (Sect. 3). _Left_ : [12] CO _J_ = 2→1 emission, the contour spacing
is 6σ, i.e. 5.5 × 10 [−][1] Jy beam [−][1] km s [−][1] . Beam size: 2.48 × 1.45 [′′] .
_Right_ : 13 CO _J_ = 2→1 emission, with a 3σ contour spacing, i.e.
7.8 × 10 [−][2] Jy beam [−][1] km s [−][1] . Beam size: 1.76 × 1.32 [′′] .


sensitivity due to bad weather conditions and a large phase noise
(Fig. A.3), we only use its integrated intensity in the subsequent
analysis. The two transitions C [18] O _J_ = 2→1 (219.560 GHz) and
C [18] O _J_ = 1→0 (109.782 GHz) are not detected in our NOEMA
and ALMA projects respectively, but constraining upper limits
are given in Table 3.


_3.3. Opacity of CO lines_


Using the line ratio of the [12] CO and [13] CO isotopologues for the
same transition level, the line opacity can be estimated with the
following formula:



, (1)
�



ν 12

R 12/13 = _[S]_ [ 12] [CO] =

_S_ 13 CO � ν 13



2 1 − _e_ τ 12
� � 1 − _e_ [τ] [13]



We independently model the [12] CO _J_ = 2→1, [13] CO _J_ = 2→1, and
12
CO _J_ = 3→2 lines with the Diskfit code (Piétu et al. 2007).
We assume power laws for the CO surface density (Σ CO ( _r_ ) =
Σ 0 ( _r_ /100 au) [−] _[p]_ ), the temperature _T_ ex ( _r_ ) = _T_ 0 ( _r_ /100 au) [−] _[q]_, and
the gas velocity _V_ ( _r_ ) = _V_ 0 ( _r_ /100 au) [−] _[a]_ [v] . In this study, we fixed
the velocity exponent so that _a_ v = 0.5 (Keplerian rotation). The
disc is assumed to have a sharp outer edge at _R_ out . The vertical density is assumed to have a Gaussian profile (see Eq. (1),
Piétu et al. 2007), with the scale height being a (free) power law
of radius _H_ ( _r_ ) = _H_ 0 ( _r_ /100 au) [−] _[h]_ . The line emission is computed
assuming a (total) local line width d _V_ independent of the radius
and local thermodynamic equilibrium (LTE; i.e. _T_ 0 represents
the rotation temperature of the level population distribution).
In addition to the above intrinsic parameters, the model also
includes geometric parameters: the source position ( _x_ 0 ; y 0 ), the
inclination _i_, and the position angle (PA) of the rotation axis ; and
the source systemic velocity _V_ sys relative to the local standard of
rest (LSR) frame.
The modelling is done in the _u_, v plane to avoid non-linear
effects due to deconvolution. The minimization is completed by
a Bayesian analysis using a Markov chain Monte Carlo (MCMC)
code, _emcee_ (Foreman-Mackey et al. 2013). Our approach differs from the analysis of White et al. (2016), which did not
include the physical disc parameters in the modelling and
focussed on the geometrical and kinematic description of the
12
CO _J_ = 3→2 emission. Our results are presented in Table 4.
Comparison with observations are shown for the integrated
spectra in Fig. 4, and for the channel maps in Fig. 5.


_4.1. Spatial distribution and kinematics of the CO gas_


The spatial extent of the gas disc is constrained to consistent values around _R_ out = 275 ± 3 au by the two transitions of [12] CO. This
value is slightly larger (within 3σ) than the 224 ± 20 au reported
by Flaherty et al. (2016) from a simultaneous fit to [12] CO _J_ = 3→2
and [12] CO _J_ = 1→0, because these latter authors fixed the density
exponent to a smaller value: _p_ = 1.5. The [13] CO line emission
is slightly more compact with _R_ out = 240 ± 20 au. Although the
discrepancy does not appear to be statistically significant, it may
result from the combination of opacity and sensitivity effects.
More interestingly, an inner cavity is confirmed with a radius
_R_ in = 17 ± 3 au from [12] CO _J_ = 3→2, as first suggested in lowerresolution maps by Flaherty et al. (2016). The spatial resolution
and sensitivity of the NOEMA observations are not sufficient to
provide a robust constraint, but point towards consistent values
of the inner disc edge. The [13] CO _J_ = 2→1 data suggest a larger
value _R_ in = 35 ± 5 au. This discrepancy should be taken with
care because the beam size of these NOEMA data is more than
four to five times larger than the ALMA beam for [12] CO _J_ = 3→2.
If confirmed, this result could be explained by the difference in
opacity between the two isotopologues: since the [12] CO transition is 70 times more optically thick than the [13] CO transition,
a larger inner radius for [13] CO could be indicative of a shallow
increase of the density at the inner disc edge, while a sharp edge
is expected to produce similar inner radii for both lines. A similar
effect has been reported in the 15–70 au gas cavity of transitional
disc J160421.7-213028 (Dong et al. 2017), although the nature of
the two discs is different, because HD 141569A does not show
any sign of having a dust cavity (a compact continuum emission was reported at all frequencies in Sect.3.1). At the reported
resolution, the presence of unresolved gaps in the gas distribution in the central 50 au may also result in a similar discrepancy


A94, page 7 of 16



where τ 12 and τ 13 are the opacity of the [12] CO and [13] CO lines,
respectively. If we further assume that the opacity ratio of
12 CO over 13 CO is equal to the elemental abundance ratio
(Wilson & Rood 1994), then τ 12 /τ 13 = 77 and we can solve for
Eq. (1). For the _J_ = 2→1 transition, we measure from NOEMA
observations a line ratio R 12/13 = 7.1 ± 1.7, and derive τ 12 =
14 ± 4 and τ 13 = 0.18 ± 0.05. It should be noted that here we
derived the CO opacity from the [12] CO / [13] CO flux ratio in velocity channels of 1 km s [−][1] to minimise the smearing effect due
to rotation (Guilloteau et al. 2006) and averaged the results.
The same analysis for the _J_ = 1→0 transition, based on our
new ALMA-Band 3 measurement and the integrated intensity
_S_ ( [13] CO) = 1.6 ± 0.2 Jy km s [−][1] reported by Flaherty et al. (2016)
with CARMA yields τ 12 = 8 ± 2 and τ 13 = 0.11 ± 0.02, in good
agreement with the _J_ = 2→1 transition estimate. Even if these
values could be biased by a factor of a few due to the uncertainties on the [12] C/ [13] C abundance ratio, as discussed in Kóspál
et al. (2013), the [12] CO lines appears to be optically thick and
the [13] CO optically thin. The [13] CO transition is therefore a more
robust gas mass tracer than [12] CO, and this consideration leads
us to reconsider the mass of gas derived by Flaherty et al. (2016)
and White et al. (2016) who assumed optically thin emission
for the [12] CO lines. Within the uncertainties, our upper limit on
C [18] O at 115.271 GHz and 219.560 GHz is consistent with ISM
CO isotopologue abundance ratios.

A&A 635, A94 (2020)


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **4.** Observed line profiles and superposed best models obtained with Diskfit (colour dashed lines) for, _from_ _left_ _to_ _right_ : [12] CO _J_ = 2→1,
13 CO _J_ = 2→1 NOEMA data, and 12 CO _J_ = 3→2 ALMA data.



**Table** **4.** Results of Diskfit modelling for the [12] CO and [13] CO with 1σ
error bars.


12 CO _J_ = 3→2 12 CO _J_ = 2→1 13 CO _J_ = 2→1


_x_ 0 (mas) −43 ± 1 −74 ± 2 −15 ± 33
y 0 (mas) −4 ± 1 −17 ± 4 −19 ± 28
_i_ ( [◦] ) 56.05 ± 0.07 57.7 ± 0.3 57.2 ± 1.4
PA ( [◦] ) 86.60 ± 0.06 85.8 ± 0.2 88 ± 1
_V_ sys (km s [−][1] ) 6.05 ± 0.01 6.07 ± 0.01 5.92 ± 0.02
_R_ out (au) 273 ± 1 277 ± 3 232 ± 11
_R_ in (au) 17 ± 3 _17_ 35 ± 5


_a_ v _0.5_ _0.5_ _0.5_
_V_ 0 (km s [−][1] ) 4.44 ± 0.01 4.4 ± 0.3 4.57 ± 0.05
dv (km s [−][1] ) 0.435 ± 0.003 0.41 ± 0.01 0.29 ± 0.05
_T_ 0 (K) 28.1± 0.2 33 ± 12 15 [+] − [3] 2
_q_ 0.28 ± 0.01 0.10 ± 0.09 0.36 ± 0.30
Σ 0 (CO) (cm [−][2] ) 3.5 ±2.0 × 10 [17] 5.5±0.2. × 10 [16] 4.9 [+] − [2] 1 [.] . [3] 1 [×][ 10] [15]

_p_ 2.7 ±0.5 2.8 ± 0.1 1.8 ± 0.5
_H_ 0 (au) 17 ± 1 17.8 ± 0.5 _9_
_h_ 1.25 1.45 ± 0.05 1.3 ± 0.7


**Notes.** Parameters in italics are fixed. The physical parameters
_T_ 0, Σ 0, _V_ 0, _H_ 0 are scaled at a radial distance of 100 au. The offset values
are given with respect to the phase centres, whose coordinates are RA =
15 : 49 : 57.73, Dec = −03 : 55 : 16.62 for the [12] CO _J_ = 3→2 line, and
RA= 15 : 49 : 57.75, Dec = −03 : 55 : 16.34 for the [12] CO _J_ = 2→1 and
13 CO _J_ = 2→1 data.


between the CO isotopologues. The inner rim value (17 au) for
12 CO is coherent with the spectroscopic detection of warm CO
through IR ro-vibrational lines by van der Plas et al. (2015), with
a modelled distribution of the gas between 14 and 45 au (after
correcting for the revised stellar distance).
The inclination and position angle are found to be in the
range _i_ = 56−58 [◦] and PA = 86 ± 1 [◦] for [12] CO lines, and _i_ =
53 ± 2 [◦] and PA = 90 ± 2 [◦] for [13] CO, which is in good agreement
with the optical values of _i_ = 52.5 ± 4.5 [◦] and PA = 85.4 ± 1 [◦]
respectively (Augereau et al. 1999). The disc is flared, although
the flaring exponent _h_ is not well constrained, a value consistent
with _h_ = 1.25 is found for both [12] CO transitions, while it is naturally not constrained for the optically thin transition of [13] CO.
For [12] CO, a scale height _H_ 0 = 17 au is found at 100 au. This is


A94, page 8 of 16



twice the value of the hydrostatic scale height ( _H_ hydro = 8 au)
for a disc with _T_ 0 = 30 K, as measured from the optically thick
transitions of [12] CO. This is consistent with direct measurements
of the [12] CO layer location in HD 163296 (de Gregorio-Monsalvo
et al. 2013) and the Flying Saucer (Guilloteau et al. 2016), where
CO is located at 2−3 scale heights (Dutrey et al. 2017).
In our preliminary fits, the velocity exponent proved to be
very close to the Keplerian value _a_ v = 0.5, and we adopted this
fixed value for the MCMC exploration reported in Table 4. At
100 au, the rotation velocity is better constrained for [12] CO lines,
with a value _V_ 0 = 4.44 ± 0.01 km s [−][1] that can be converted into
a central stellar mass of 2.22 ± 0.01 _M_ ⊙ . This value is slightly
smaller than the mass of 2.39 ± 0.05 _M_ ⊙ reported by White et al.
(2016), but is very consistent with the spectral analysis of Merín
et al. (2004) that yielded _M_ ⋆ = 2.00 [+] − [0] 0 [.] . [18] 15 _[M]_ [⊙] [. The] [13] [CO analysis]
leads to a slightly larger mass _M_ ⋆ = 2.35 ± 0.05 _M_ ⊙ .


_4.2. Temperature and density laws_


The modelling of the two optically thick transitions
12 12
CO _J_ = 2→1 and CO _J_ = 3→2 provides very consistent
estimates for the excitation temperature, _T_ 0 ∼ 30 K with a
relatively flat radial profile _q_ < 0.4 ( _q_ = 0.28 ± 0.01 for
12 CO _J_ = 3→2 and _q_ = 0.10 ± 0.09 for 12 CO _J_ = 2→1). The
temperature is ill constrained for the optically thin [13] CO transition. A value of 30 K is consistent with the analysis of the
12
CO _J_ = 3→2 detection with SMA by Flaherty et al. (2016,
who used a fixed temperature exponent _q_ = 0.5 and found
_T_ 0 = 33 [+] − [11] 4 [K).] [It] [is] [somewhat] [smaller] [than] [the] [gas] [temperature]
of about 50 K derived from [12] CO line for a similar, albeit
younger and more optically thick disc around the Herbig Ae
star MWC 480 (Piétu et al. 2007). Given the star luminosity of
30 _L_ ⊙, blackbody grains in an optically thin disc are predicted
to have a temperature of 60 K at a distance of 100 au, and
would be much hotter than the detected gas. The derived gas
temperature is also significantly smaller than the range of kinetic
temperatures computed by Thi et al. (2014) with their Prodimo
modelling based on unresolved detections of [OI], C[II] and
12
CO _J_ = 3→2 lines around HD 141569. In their modelling, the
gas is heated by Polycyclic Aromatic Hydrocarbons (PAH) and
cooled by [OI] and CO lines, and the computed temperature
reaches about 100 K at 100 au in the inner disc and drops down
to 40 K at 500 au (i.e. well beyond the outer edge of the emission
we detect with ALMA/NOEMA). The excitation temperature we

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **5.** Results of the modelling showing the channel maps for the transition ( _from_ _left_ _to_ _right_ ) [12] CO _J_ = 2→1, [13] CO _J_ = 2→1 (NOEMA) and
12 CO _J_ = 3→2 (ALMA). In each sub-panel, we present from left to right: the observations, the model (see best-fit parameters in Table 4), and the
residual emission. The latter is obtained by subtraction in the _u_, v plane before imaging and cleaning. Contour spacing is 5σ for the [12] CO transitions
(σ = 16 mJy beam [−][1] for _J_ = 2→1 and σ = 6.3 mJy beam [−][1] for _J_ = 3→2), and 3σ for the [13] CO _J_ = 2→1 transition (σ = 10 mJy beam [−][1] ). Residual
contour spacing is 3σ for all transitions.



derive from [12] CO may still be smaller than the actual gas kinetic
temperature. Low values of the gas temperature (although with
a much more dramatic deviation) have also been reported in
the hybrid disc HD 21997 by Kóspál et al. (2013), where the
excitation temperature derived from CO line ratios drops to
values as low as 6−9 K. Flaherty et al. (2016) propose that this
low gas temperature could be explained by enhanced cooling



from CO (following Hollenbach & Tielens 1999), and/or NLTE
effects (following Matrà et al. 2015).
In the absence of C [18] O emission, we use the more optically thin emission of the [13] CO _J_ = 2→1 line to constrain the
CO surface density. Our modelling yields a best-fit value Σ 0 =
5 [+] − [2] 1 [×][ 10] [15] [ cm] [−][2] [at] [100] [au] [with] [an] [exponent] _[p]_ [=] [1][.][8][ ±][ 0][.][5.] [We]
note that the two other transitions of [12] CO lead to much steeper


A94, page 9 of 16

A&A 635, A94 (2020)



profiles with _p_ ∼ 3 and require a surface density of the order
of 6 × 10 [16] cm [−][2] . These values of the surface density are at least
one order of magnitude smaller than those found for the younger,
gas-rich disc around the Herbig Ae star MWC 480: Piétu et al.
(2007) report, at a distance of 100 au, Σ 0 = 8 × 10 [16] cm [−][2] for
13 18 −2 12
CO and 6 × 10 cm for CO. This system is taken here as
a reference as it is one of the very few where the surface density of [13] CO has been precisely constrained through similar disc
emission modelling.
We derived a total mass of CO gas based on Σ 0 and used
the minimum outer disc edge value _R_ out = 232 au inferred from
the [13] CO line (hence a minimum mass value). Because most
of the mass lies in the inner regions with a power law distribution, the computed value is sensitive to the inner disc
edge, and we take into account the inner cavity detected with
the [12] CO emission in the ALMA high-resolution maps ( _R_ in =
17 au). Assuming a standard isotopic ratio [12] CO/ [13] CO = 77,
these parameters yield _M_ 12 CO = 0.10 [+] − [0] 0 [.] . [05] 02 _[M]_ [⊕] [(][=][4] [×] [10] [23] [ kg),]
where we take into account the uncertainties on _R_ in, _R_ out, Σ 0 and
_p_ . This value is 50 times larger than the CO mass reported by
White et al. (2016) based on the [12] CO emission.
The conversion to a total mass of gas is very uncertain. A low
CO content compared to the dust emission was already noted
in the early detection of CO isotopologues in DM Tau (Dutrey
et al. 1997). Several recent studies (Bergin et al. 2013; Reboussin
et al. 2015) favour much lower values for the [CO/H 2 ] ratio than
the canonical ISM value of 10 [−][4] (see also the discussion on
carbon depletion in e.g. Miotello et al. 2017). We discuss this
point again in Sect. 5.2. Here, in order to compare with other
works, we nevertheless convert this minimum mass of CO into
_M_ H 2 = 71 [+] − [36] 14 _[M]_ [⊕] [or] [0][.][21] [+] − [0] 0 [.] . [11] 04 _[M]_ [Jup] [≃] [2][.][10] [−][4] _[ M]_ [⊙] [using] [the] [stan-]
dard ISM abundance. Using the grid of models developed by
Miotello et al. (2016), which include the effect of isotope selective photodissociation, the luminosity of the [13] CO _J_ = 2→1 line
and the non-detection of C [18] O _J_ = 2→1 favours a total mass in
the range 1−5 × 10 [−][4] _M_ ⊙, in good agreement with the previous
estimate. This is one order of magnitude larger than the value
reported by Flaherty et al. (2016) from the SMA detection of
12
CO _J_ = 3→2, but is in good agreement with the earlier modelling of Thi et al. (2014) and Jonkheid et al. (2006), based on
spatially unresolved observations of the same line, who found
a total gas mass in the range 67−164 _M_ ⊕ . Our value is a factor
of three to five smaller than the total gas mass of 6−9 × 10 [−][4] _M_ ⊙
reported by Miley et al. (2018) based on the integrated flux of the
optically thin transition [13] CO _J_ = 2→1, but these remain in reasonable agreement due to the different methodologies used. This
total gas mass value is clearly on the lower bound of the range of
disc masses found for Herbig Ae stars, and usually derived from
mm dust flux converted to gas mass with an assumed gas-todust ratio of 100 (see, e.g. Williams & Cieza 2011). It is instead
typical of discs around very low-mass TTS (for instance, TTS
disc masses obtained from [13] CO and C [18] O _J_ = 3→2 in Lupus


A94, page 10 of 16



**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **6.** Global scheme of dust and gas distribution in HD 141569 summarizing the most recent
resolved observations.


range between 10 [−][5] and 10 [−][3] _M_ ⊙, based on models assuming isotope selective photo-dissociation and CO freeze-out on
grains Miotello et al. 2017). HD 141569 also harbours one of
the most massive molecular gas components among the gas-rich
debris discs reported in Moór et al. (2017) based on supposedly
optically thin CO isotopologues. Even if we underestimate the
CO mass due to [13] CO optical depth effects or the uncertain

[CO/H 2 ] abundance, such a low mass supports the process of
ongoing gas dissipation in this 5 Myr-old disc.


**5. Discussion**


_5.1. Comparison with optical/NIR emission_


The distribution of matter is strikingly different at optical/NIR
and mm wavelengths. A global sketch summarizing and comparing the respective radial extent of the main disc components
detected at optical/NIR and mm wavelengths is presented in
Fig. 6. The continuum emission at mm wavelength is clearly
much more compact than the 250–400 au broad rings of the
debris disc revealed at optical/NIR wavelengths, and is also more
compact and centrally peaked than the gas emission characterised in the following section. Furthermore, it is coincident
with the innermost component recently reported by various
authors in the NIR domain. Indeed, in the inner 100 au recent
observations with VLT/SPHERE have revealed the presence of
a series of concentric rings and arcs with semi-major axes in
the range 45−90 au (Perrot et al. 2016). The link between the
µm grains responsible for the IR emission and the mm grains
detected with ALMA/NOEMA cannot be clarified because of
the limited resolution of our data. VLT/VISIR observations in
the mid-IR also suggest the presence of an even more internal component (Thi et al. 2014), which was recently detected
at _L_ [′] band with the Keck vortex coronagraph within 70 au
(Mawet et al. 2017) and may extend up to 100 au. According to
the extended scattered-light emission reported with HST/STIS
by Konishi et al. (2016), this inner warm component may also be
spatially associated with the inner rim of the gas disc that our
modelling locates around 15−20 au from [12] CO _J_ = 3→2 maps
(similarly to the warm CO detected in spectroscopy in the
14−60 au region by Goto et al. 2006; van der Plas et al. 2015).
The disc is not classified as a transitional disc because of the
lack of a mm dust cavity. A small cavity of no more than 15 au
in radius is observed in the CO maps, consistent with the earlier
spectroscopic detections of a warm CO ring, but the continuum
emission is strikingly centrally peaked. Inside this gas cavity,
there is probably not much material: VLTI-PIONIER observations in the _H_ -band reported a completely unresolved structure
(Lazareff et al. 2017), which might be dominated by the stellar emission itself (accounting for 86% of the total flux), without
suggestion of an inner ring near the sublimation distance of small
grains.

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** **7.** Montage of the [12] CO _J_ = 3→2 residual emission with the series of concentric rings
detected in NIR scattered light with SPHERE by
Perrot et al. (2016).



The scattered light images show many asymmetries at various spatial scales, with spirals, arcs, and multiple ring structures. The outer limit of the gas disc is precisely coincident
with the so-called “inner ring” near 250 au reported previously.
Among the possible ring formation mechanisms, Takeuchi &
Artymowicz (2001) proposed a complex mechanism based on
the outward migration of small grains at the outer edge of a
gas disc. HD 141569 is the only resolved disc so far that displays this combination of distant dust rings and a gas-rich inner
disc.
Large-scale asymmetries are also suggested in both wavelength domains. In Fig. 7, we superimpose the SPHERE/
_K_ s image on the map of our best-fit residual of [12] CO _J_ =
3→2 ALMA emission. This residual emission, which was
already reported by White et al. (2016), is significant (up to
6σ) at all velocity channels and peaks between 6 and 9 km s [−][1]
(see Fig. 5). We present here the integrated emission, which
extends on the western side with an elliptical shape. It displays
two brightness peaks centred at 60–70 au of deprojected distance at azimuth angles of about 220 [◦] and 290 [◦], in the region
of the three concentric rings detected with SPHERE. Since the
12 CO emission is optically thick and the feature is not detected
in the isotopologues due to insufficient sensitivity and angular
resolution, we cannot disentangle between a local temperature
offset and a density feature. However, the significance of this
12 CO brightness increase, the coincidence with the location of
the inner rings, and the similar brightness asymmetry raise questions about the interplay between gas and dust in this region. Lyra
& Kuchner (2013) proposed a mechanism based on the development of a clumping instability to create eccentric rings from
the coupling of gas and grains, but this appears to be efficient
in a regime of low gas-to-dust ratio, which does not seem to be
favoured in the inner region (see discussion in Sect. 5.2). The
250 au dust ring (and possibly also the outermost 400 au ring)
at the edge of the detectable gaseous component (see Fig. 3)
may instead be an ideal location to reach the necessary very
low value of gas-to-dust ratio ( _G_ / _D_ < 1) for such an instability to develop. So far, no planetary companion candidate has
been reported in the inner 100 au region with a sensitivity limit
of the order of 1−3 _M_ Jup (Perrot et al. 2016). The destruction of
planetesimals (by collision or evaporation) could produce both
large quantities of small grains and release substantial amounts
of gas, as has been suggested by the detection of an asymmetrical emission of CO in β Pictoris (Dent et al. 2014). In
HD 141569, such a collisional event or enhanced planetesimal
evaporation might be more difficult to demonstrate because of
the large residual amount of primordial gas in the region of the
NIR rings.



We obtain values for _M_ dust in the range 0.03−0.52 _M_ ⊕ . This value
is significantly smaller than for other Herbig Ae systems. In order
to compare with dust masses derived for other gas-rich debris
discs reported in Moór et al. (2017), we alternatively used the
same dust opacity (κ ν=230 GHz = 2.3 cm [2] g [−][1] ) and their assumed
temperature ( _T_ d = 50 K), which leads to _M_ _d_ = 0.46 _M_ ⊕, which
makes it the most massive gas-rich debris disc with HD 131488
in this study. With our gas mass estimate, 70 _M_ ⊕, and our first
choice of dust opacity, yielding _M_ dust ∼ 0.03−0.52 _M_ ⊕, we can
obtain a gas-to-dust mass ratio _G_ / _D_ in the range 135−2370.
This is most likely a severe lower limit, since we assumed a
high CO/H 2 abundance ratio to derive the gas mass. In T Tauri
discs, it is in general necessary to invoke an overall depletion
of CO by a factor of ten or so to bring the derived G/D ratio
to the ISM value of 100 (see, Piétu et al. 2007; Williams &
Best 2014), although the warmer discs around HAeBe stars have
higher CO/dust ratios, and can sometimes be directly interpreted
by _G_ / _D_ = 100 and a normal CO/H 2 ratio (e.g. AB Aur Piétu
et al. 2007, or also HD 163296 in Williams & Best 2014). The
estimated gas-to-dust mass ratio appears at least one order of
magnitude larger than the values reported in Miotello et al.
(2017) for a sample of sources in Lupus, where gas mass estimates were also derived from optically thin CO isotopologues


A94, page 11 of 16



_5.2. Gas-to-dust ratio_


The global gas-to-dust mass ratio in the disc is expected to trace
the evolution of the system, but getting an accurate value is challenging because of the numerous assumptions that must be made
especially in the computation of the total gas mass, as discussed
in the previous section. The mass of dust is no less uncertain as
it relies on the unknown value of the dust mass opacity κ ν, and
we will follow the prescription: κ ν = 0.02(λ/1mm) [−][β] cm [2] g [−][1],
which is similar to that adopted by Beckwith et al. (1990) (with
β = 1). _M_ dust can be estimated on the basis of the mm dust flux
( _F_ ν ), which is constrained in our observations at three different frequencies. From the modelling of the SED, earlier models
by Jonkheid et al. (2006) and Thi et al. (2014) showed that the
dust emission is optically thin from optical to mm wavelengths,
meaning that the mm flux can be used to provide a robust estimate of the dust mass. Using the mm dust fluxes reported in
Table 1, the extreme values of β in the range [0,0.7], and typical
values of the temperature for dust grains located at 50–100 au
from this 30 _L_ ⊙ star ( _T_ d = 65−90 K), _M_ dust is computed with the
standard equation:



_M_ _d_ = _[F]_ [ν] _[D]_ [2] _[c]_ [2]

2 _h_ ν [3] κ ν



_h_ ν
exp
� � _k_ B _T_ d



− 1 . (2)
� �

A&A 635, A94 (2020)



(although with more complex models including isotope selective
processes, as mentioned earlier).
This analysis must furthermore be refined because the morphology of the dust and gas components is quite different. The
_G_ / _D_ ratio can obviously display ample radial variations due to
migration of large grains towards the inner disc regions, or local
enhancements of the gas and dust density. The resolved images
of the HD 141569 disc suggest that the bulk of the mm grains
reside in a small disc confined within _R_ out,dust ∼ 100 au, while
the gas reservoir extends between about 20 and 270 au. There
is possible evidence for a second, low-emission component of
dust grains in the lower-resolution NOEMA maps (and concurrent hints at very short ALMA baselines), which could extend
out to the limit of the gas disc and may contribute up to 30%
of the dust emission. We checked however that the spatial variations of _G_ / _D_ do not affect the overall conclusion. Similar large
values of the _G_ / _D_ ratio have also been reported in the 30 Myrold hybrid disc HD 21997 by Kóspál et al. (2013): the authors
quote a CO-to-dust ratio of 0.4−0.9 within _R_ out = 150 au that
converts to 280−630 for H 2 -to-dust. However, the morphology
of the two systems is very different, with a dust cavity within
55 au for HD 21997, but no evidence for a gas cavity. We also
reported in Péricaud et al. (2017) the tendency of gas-rich debris
discs to display a larger ratio of CO to mm continuum flux compared to other Herbig/TTauri systems, which could suggest that
there is a larger gas-to-dust ratio in this transient phase. Beyond
270 au, the abrupt rarefaction of the gas naturally decreases _G_ / _D_,
although neither mm grains nor gas emission are detected in this
cold region. The outermost rings can be regarded as a nascent
debris disc, where the grains detected in scattered light emission
are produced by a collisional cascade from a reservoir of unseen
parent bodies.


_5.3. Origin of the gas_


From the optically thin [13] CO emission, we derived a [12] CO gas
mass in the range 8–15 × 10 [−][2] _M_ ⊕, a factor of 50 larger than the
estimate by White et al. (2016) based on the optically thick [12] CO
transition, and a factor of 2 larger than the gas mass derived by
Miley et al. (2018) based on optically thin [13] CO observations.
The gas disc appears also twice more massive than the C [18] O
mass estimate in the 30 Myr-old hybrid disc HD 21997 (Kóspál
et al. 2013). Based on the typical lifetime for self-shielded CO
molecules and using estimates of CO content and gas production
in solar system comets, these latter authors computed that more
than 6000 Hale-Bopp-like comets would have to be destroyed
each year to reproduce the observed level of CO in HD 21997 if
the gas were of secondary origin. In the hypothesis of an exocometary origin, CO molecules can only be protected through
self-shielding, which is however a more efficient mechanism
for [12] CO than for its isotopologues. We estimate the lifetime
of self-shielded [13] CO molecules from Visser et al. (2009) using
the gas column density derived from our previous analysis and
adopting _T_ ex = 50 K, and we find 860 yr as a maximum value
under the ambient interstellar UV field (the actual lifetime might
even be shorter considering the additional contribution of the
stellar UV field). Using the mass measured for the optically
thin molecule [13] CO and assuming a standard isotopic ratio, the
12 CO production rate required to sustain the observed amount
of [13] CO is 4.7 × 10 [20] kg yr [−][1], and the [12] CO production rate is
3 × 10 [21] kg yr [−][1], a value more than 2000 times larger than the
gas production rate inferred for the β Pic disc by Dent et al.
(2014) and Matrà et al. (2017). In Péricaud et al. (2017), we alternatively calculated the maximum amount of [12] CO that can be


A94, page 12 of 16



locked in comets and planetesimals for a massive Herbig Ae
disc ( _M_ d = 0.1 _M_ ⋆ ), assuming that 10% of the total amount
of available oxygen in the disc can ultimately be evaporated
in the form of CO (an upper limit derived from solar system
comets). We found an upper limit for the initial [12] CO mass in
comets and planetesimals of about 4 × 10 [25] kg, hence a [13] CO
mass of 5.2 × 10 [23] kg, which is 100 times the CO mass value
estimated for HD 141569. With a [13] CO lifetime of about 860 yr,
the observed mass of [13] CO would imply a replenishment rate
of 6 × 10 [18] kg yr [−][1], and hence a maximum lifetime of the initial
13 CO reservoir of less than 10 5 yr. This value is likely an upper
limit because we overestimated the CO content in comets relying
on CO-rich comets only and assumed a very massive disc. It is
however much shorter than the system age of 5 ± 3 Myr (Merín
et al. 2004).
Moreover, the morphology of the CO emission, which continuously extends from 15–20 au out to 275 au favours a primordial origin for the gas, in contrast to the localised emission
detected around β Pic where the gas and dust are likely produced in a planetesimal belt (Matrà et al. 2017). Our modelling
of the CO maps shows that the gas disc is well represented by a
protoplanetary-like disc with a surface density an order of magnitude lower than in the typical 1–2 Myr-old discs around Herbig
Ae stars. The total amount of dust and gas in this system is
similar to the older debris discs around HD 21997, HD 121617,
HD 131488 and HD 131835 (Moór et al. 2017). No large inner
cavity is found in HD 141569 in contrast to HD 21997 or
HD 121617, indicating possible different mechanisms at play. A
possible alternative scenario was recently proposed by Kral et al.
(2017, 2019), in which even the most massive hybrid discs could
be explained by secondary CO gas shielded by accumulated neutral carbon that is a photodissociation product of molecular gas
released by planetesimals. This would require specific (low) values of the viscosity to accumulate a sufficient amount of C [0], and
it is uncertain whether this scenario could efficiently be applied
to such a young system as HD 141569A.
The detection of other molecular species in the gas phase can
provide a complementary diagnosis on the nature of the gas and
reveal the specific chemistry in such a system. Our attempt to find
HCO [+], H 2 CO, HCN, HC 3 N and CS with the IRAM-30 m radio
antenna did not provide any successful detection (see Sect. 2.3).
With our sensitivity limit, we would have been able to detect
HCO [+] _J_ = 1→0 and CS _J_ = 3→2 lines at >20σ if these were as
bright as in the disc of AB Aur (Pacheco-Vázquez et al. 2015).
However, the comparison should account for the smaller size of
the HD 141569 disc, which is 250 au in radius, instead of about
500 au for that of AB Aur, and of the differences in distance. We
therefore conservatively conclude that the average brightness for
these transitions is at least a factor of three below that found
for AB Aur. This may be the result of lower column densities
or lower excitation temperatures. Both possibilities favour a low
gas surface density in HD 141569. The presence of a prominent
OI line (in addition to CII) revealed by _Herschel_ also underlines
the similarity with other Herbig Ae discs, because this feature
is not detected in any of the more evolved, gas-rich debris discs
(Meeus et al. 2012; Moór et al. 2016). The presence of prominent
PAH features is another argument favouring the presence of primordial material in at least some regions of the disc, since such
strong features have not been detected in IR spectra of Vega-like
stars so far (e.g. Chen et al. 2006). This again reinforces its classification as an evolved disc around a Herbig Ae star rather than
a debris disc. The disc is thus likely dominated by primordial
gas in the phase of dissipation, and differs from its less evolved
siblings due to its reduced CO surface density, and most notably

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc



its extremely low continuum which suggests a faster evolution
of the dust component as already highlighted in Péricaud et al.
(2017).


_Acknowledgements._ This work was supported by “Programme National de
Physique Stellaire” (PNPS from INSU/CNRS.) This research made use of
the SIMBAD database, operated at the CDS, Strasbourg, France. This paper
makes use of the following ALMA data: ADS/JAO.ALMA2012.1.00698.S and
ADS/JAO.ALMA.2013.1.00883.S. ALMA is a partnership of ESO (representing
its member states), NSF (USA), and NINS (Japan), together with NRC (Canada),
NSC and ASIAA (Taiwan), and KASI (Republic of Korea) in cooperation with
the Republic of Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO, and NAOJ. This paper is also based on observations carried out
with the IRAM NOEMA interferometer and the IRAM 30-m telescope. IRAM
is supported by INSU/CNRS (France), MPG (Germany), and IGN (Spain). We
thank the anonymous referee for his/her careful reading and useful suggestions
to improve the manuscript.


**References**


[Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42](http://linker.aanda.org/10.1051/0004-6361/201732243/1)
[Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJ, 869, L41](http://linker.aanda.org/10.1051/0004-6361/201732243/2)
[Augereau, J. C., Lagrange, A. M., Mouillet, D., & Ménard, F. 1999, A&A, 350,](http://linker.aanda.org/10.1051/0004-6361/201732243/3)
[L51](http://linker.aanda.org/10.1051/0004-6361/201732243/3)
[Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44](http://linker.aanda.org/10.1051/0004-6361/201732243/4)
[Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924](http://linker.aanda.org/10.1051/0004-6361/201732243/5)
[Bergin, E. A., Cleeves, L. I., Gorti, U., et al. 2013, Nature, 493, 644](http://linker.aanda.org/10.1051/0004-6361/201732243/6)
[Boccaletti, A., Augereau, J.-C., Marchis, F., & Hahn, J. 2003, ApJ, 585, 494](http://linker.aanda.org/10.1051/0004-6361/201732243/7)
[Chen, C. H., Sargent, B. A., Bohac, C., et al. 2006, ApJS, 166, 351](http://linker.aanda.org/10.1051/0004-6361/201732243/8)
[Clampin, M., Krist, J. E., Ardila, D. R., et al. 2003, AJ, 126, 385](http://linker.aanda.org/10.1051/0004-6361/201732243/9)
[Currie, T., Grady, C. A., Cloutier, R., et al. 2016, ApJ, 819, L26](http://linker.aanda.org/10.1051/0004-6361/201732243/10)
[de Gregorio-Monsalvo, I., Ménard, F., Dent, W., et al. 2013, A&A, 557, A133](http://linker.aanda.org/10.1051/0004-6361/201732243/11)
[Dent, W. R. F., Wyatt, M. C., Roberge, A., et al. 2014, Science, 343, 1490](http://linker.aanda.org/10.1051/0004-6361/201732243/12)
[Dong, R., van der Marel, N., Hashimoto, J., et al. 2017, ApJ, 836, 201](http://linker.aanda.org/10.1051/0004-6361/201732243/13)
[Dutrey, A., Guilloteau, S., & Guelin, M. 1997, A&A, 317, L55](http://linker.aanda.org/10.1051/0004-6361/201732243/14)
[Dutrey, A., Lecavelier Des Etangs, A., & Augereau, J. C. 2004, Comets II, eds.](http://linker.aanda.org/10.1051/0004-6361/201732243/15)
M. C. Festou, H. U. Keller, & H. A. Weaver (Tucson, AZ: University of
Arizona Press), 81
[Dutrey, A., Guilloteau, S., Piétu, V., et al. 2017, A&A, 607, A30](http://linker.aanda.org/10.1051/0004-6361/201732243/16)
Espaillat, C., Muzerolle, J., Najita, J., et al. 2014, Protostars [and](http://linker.aanda.org/10.1051/0004-6361/201732243/17) Planets VI

(Tucson, AZ: University of Arizona Press), 497
Fedele, D., van den Ancker, M. E., Henning, T., Jayawardhana, R., & Oliveira,
[J. M. 2010, A&A, 510, A72](http://linker.aanda.org/10.1051/0004-6361/201732243/18)
[Flaherty, K. M., Hughes, A. M., Andrews, S. M., et al. 2016, ApJ, 818, 97](http://linker.aanda.org/10.1051/0004-6361/201732243/19)
[Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125,](http://linker.aanda.org/10.1051/0004-6361/201732243/20)
[306](http://linker.aanda.org/10.1051/0004-6361/201732243/20)
[Gaia Collaboration (Brown, A. G. A., et al.) 2018, A&A, 616, A1](http://linker.aanda.org/10.1051/0004-6361/201732243/21)
[Garufi, A., Benisty, M., Pinilla, P., et al. 2018, A&A, 620, A94](http://linker.aanda.org/10.1051/0004-6361/201732243/22)
[Goto, M., Usuda, T., Dullemond, C. P., et al. 2006, ApJ, 652, 758](http://linker.aanda.org/10.1051/0004-6361/201732243/23)
[Guilloteau, S., Piétu, V., Dutrey, A., & Guélin, M. 2006, A&A, 448, L5](http://linker.aanda.org/10.1051/0004-6361/201732243/24)
[Guilloteau, S., Dutrey, A., Piétu, V., & Boehler, Y. 2011, A&A, 529, A105](http://linker.aanda.org/10.1051/0004-6361/201732243/25)
[Guilloteau, S., Piétu, V., Chapillon, E., et al. 2016, A&A, 586, L1](http://linker.aanda.org/10.1051/0004-6361/201732243/26)
[Haisch, K. E. J., Lada, E. A., & Lada, C. J. 2001, ApJ, 553, L153](http://linker.aanda.org/10.1051/0004-6361/201732243/27)
[Hollenbach, D. J., & Tielens, A. G. G. M. 1999, Rev. Mod. Phys., 71, 173](http://linker.aanda.org/10.1051/0004-6361/201732243/28)
[Hughes, A. M., Duchêne, G., & Matthews, B. C. 2018, ARA&A, 56, 541](http://linker.aanda.org/10.1051/0004-6361/201732243/29)
[Jonkheid, B., Kamp, I., Augereau, J.-C., & van Dishoeck, E. F. 2006, A&A, 453,](http://linker.aanda.org/10.1051/0004-6361/201732243/30)
[163](http://linker.aanda.org/10.1051/0004-6361/201732243/30)



[Konishi, M., Grady, C. A., Schneider, G., et al. 2016, ApJ, 818, L23](http://linker.aanda.org/10.1051/0004-6361/201732243/31)
[Kóspál, Á., Moór, A., Juhász, A., et al. 2013, ApJ, 776, 77](http://linker.aanda.org/10.1051/0004-6361/201732243/32)
[Kral, Q., Matrà, L., Wyatt, M. C., & Kennedy, G. M. 2017, MNRAS, 469, 521](http://linker.aanda.org/10.1051/0004-6361/201732243/33)
[Kral, Q., Marino, S., Wyatt, M. C., Kama, M., & Matra, L. 2019, Turk. J. Phys.,](http://linker.aanda.org/10.1051/0004-6361/201732243/34)
[43, 126](http://linker.aanda.org/10.1051/0004-6361/201732243/34)
[Lazareff, B., Berger, J.-P., Kluska, J., et al. 2017, A&A, 599, A85](http://linker.aanda.org/10.1051/0004-6361/201732243/35)
[Lieman-Sifry, J., Hughes, A. M., Carpenter, J. M., et al. 2016, ApJ, 828, 25](http://linker.aanda.org/10.1051/0004-6361/201732243/36)
[Lyra, W., & Kuchner, M. 2013, Nature, 499, 184](http://linker.aanda.org/10.1051/0004-6361/201732243/37)
[Matrà, L., Pani´c, O., Wyatt, M. C., & Dent, W. R. F. 2015, MNRAS, 447, 3936](http://linker.aanda.org/10.1051/0004-6361/201732243/38)
[Matrà, L., Dent, W. R. F., Wyatt, M. C., et al. 2017, MNRAS, 464, 1415](http://linker.aanda.org/10.1051/0004-6361/201732243/39)
[Mawet, D., Choquet, É., Absil, O., et al. 2017, AJ, 153, 44](http://linker.aanda.org/10.1051/0004-6361/201732243/40)
[Meeus, G., Montesinos, B., Mendigutía, I., et al. 2012, A&A, 544, A78](http://linker.aanda.org/10.1051/0004-6361/201732243/41)
[Merín, B., Montesinos, B., Eiroa, C., et al. 2004, A&A, 419, 301](http://linker.aanda.org/10.1051/0004-6361/201732243/42)
[Miley, J. M., Pani´c, O., Wyatt, M., & Kennedy, G. M. 2018, A&A, 615, L10](http://linker.aanda.org/10.1051/0004-6361/201732243/43)
Miotello, A., van Dishoeck, E. F., Kama, M., & Bruderer, S. 2016, [A&A,](http://linker.aanda.org/10.1051/0004-6361/201732243/44) 594,
[A85](http://linker.aanda.org/10.1051/0004-6361/201732243/44)

[Miotello, A., van Dishoeck, E. F., Williams, J. P., et al. 2017, A&A, 599, A113](http://linker.aanda.org/10.1051/0004-6361/201732243/45)
[Moór, A., Ábrahám, P., Juhász, A., et al. 2011, ApJ, 740, L7](http://linker.aanda.org/10.1051/0004-6361/201732243/46)
[Moór, A., Kóspál, Á., Ábrahám, P., et al. 2016, ApJ, 826, 123](http://linker.aanda.org/10.1051/0004-6361/201732243/47)
[Moór, A., Curé, M., Kóspál, Á., et al. 2017, ApJ, 849, 123](http://linker.aanda.org/10.1051/0004-6361/201732243/48)
[Mouillet, D., Lagrange, A. M., Augereau, J. C., & Ménard, F. 2001, A&A, 372,](http://linker.aanda.org/10.1051/0004-6361/201732243/49)
[L61](http://linker.aanda.org/10.1051/0004-6361/201732243/49)

[Nilsson, R., Liseau, R., Brandeker, A., et al. 2010, A&A, 518, A40](http://linker.aanda.org/10.1051/0004-6361/201732243/50)
[Pacheco-Vázquez, S., Fuente, A., Agúndez, M., et al. 2015, A&A, 578, A81](http://linker.aanda.org/10.1051/0004-6361/201732243/51)
[Pérez, L. M., Carpenter, J. M., Chandler, C. J., et al. 2012, ApJ, 760, L17](http://linker.aanda.org/10.1051/0004-6361/201732243/52)
Péricaud, J., Di Folco, E., Dutrey, A., Guilloteau, S., & Piétu, V. 2017, [A&A,](http://linker.aanda.org/10.1051/0004-6361/201732243/53)
[600, A62](http://linker.aanda.org/10.1051/0004-6361/201732243/53)
[Perrot, C., Boccaletti, A., Pantin, E., et al. 2016, A&A, 590, L7](http://linker.aanda.org/10.1051/0004-6361/201732243/54)
[Piétu, V., Dutrey, A., & Guilloteau, S. 2007, A&A, 467, 163](http://linker.aanda.org/10.1051/0004-6361/201732243/55)
[Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012, A&A, 538, A114](http://linker.aanda.org/10.1051/0004-6361/201732243/56)
[Reboussin, L., Guilloteau, S., Simon, M., et al. 2015, A&A, 578, A31](http://linker.aanda.org/10.1051/0004-6361/201732243/57)
[Reche, R., Beust, H., & Augereau, J.-C. 2009, A&A, 493, 661](http://linker.aanda.org/10.1051/0004-6361/201732243/58)
[Schreyer, K., Guilloteau, S., Semenov, D., et al. 2008, A&A, 491, 821](http://linker.aanda.org/10.1051/0004-6361/201732243/59)
Sylvester, R. J., Skinner, C. J., Barlow, M. J., & Mannings, V. 1996, [MNRAS,](http://linker.aanda.org/10.1051/0004-6361/201732243/60)
[279, 915](http://linker.aanda.org/10.1051/0004-6361/201732243/60)
[Sylvester, R. J., Dunkin, S. K., & Barlow, M. J. 2001, MNRAS, 327, 133](http://linker.aanda.org/10.1051/0004-6361/201732243/61)
[Takeuchi, T., & Artymowicz, P. 2001, ApJ, 557, 990](http://linker.aanda.org/10.1051/0004-6361/201732243/62)
[Thi, W.-F., Pinte, C., Pantin, E., et al. 2014, A&A, 561, A50](http://linker.aanda.org/10.1051/0004-6361/201732243/63)
van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, [A&A,](http://linker.aanda.org/10.1051/0004-6361/201732243/64) 585,
[A58](http://linker.aanda.org/10.1051/0004-6361/201732243/64)
[van der Marel, N., Williams, J. P., Ansdell, M., et al. 2018, ApJ, 854, 177](http://linker.aanda.org/10.1051/0004-6361/201732243/65)
van der Plas, G., van den Ancker, M. E., Waters, L. B. F. M., & Dominik, C.
[2015, A&A, 574, A75](http://linker.aanda.org/10.1051/0004-6361/201732243/66)
[Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323](http://linker.aanda.org/10.1051/0004-6361/201732243/67)
[Weinberger, A. J., Becklin, E. E., Schneider, G., et al. 1999, ApJ, 525, L53](http://linker.aanda.org/10.1051/0004-6361/201732243/68)
Weinberger, A. J., Rich, R. M., Becklin, E. E., Zuckerman, B., & Matthews, K.
[2000, ApJ, 544, 937](http://linker.aanda.org/10.1051/0004-6361/201732243/69)
[White, J. A., & Boley, A. C. 2018, ApJ, 859, 103](http://linker.aanda.org/10.1051/0004-6361/201732243/70)
[White, J. A., Boley, A. C., Hughes, A. M., et al. 2016, ApJ, 829, 6](http://linker.aanda.org/10.1051/0004-6361/201732243/71)
White, J. A., Boley, A. C., MacGregor, M. A., Hughes, A. M., & Wilner, D. J.
[2018, MNRAS, 474, 4500](http://linker.aanda.org/10.1051/0004-6361/201732243/72)
[Williams, J. P., & Best, W. M. J. 2014, ApJ, 788, 59](http://linker.aanda.org/10.1051/0004-6361/201732243/73)
[Williams, J. P., & Cieza, L. A. 2011, ARA&A, 49, 67](http://linker.aanda.org/10.1051/0004-6361/201732243/74)
[Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191](http://linker.aanda.org/10.1051/0004-6361/201732243/75)
[Wyatt, M. C. 2008, ARA&A, 46, 339](http://linker.aanda.org/10.1051/0004-6361/201732243/76)
[Wyatt, M. C., Pani´c, O., Kennedy, G. M., & Matrà, L. 2015, Ap&SS, 357, 103](http://linker.aanda.org/10.1051/0004-6361/201732243/77)
[Zhu, Z., Nelson, R. P., Hartmann, L., Espaillat, C., & Calvet, N. 2011, ApJ, 729,](http://linker.aanda.org/10.1051/0004-6361/201732243/78)
[47](http://linker.aanda.org/10.1051/0004-6361/201732243/78)

[Zuckerman, B., Forveille, T., & Kastner, J. H. 1995, Nature, 373, 494](http://linker.aanda.org/10.1051/0004-6361/201732243/79)


A94, page 13 of 16

A&A 635, A94 (2020)


**Appendix A:** **Channel maps for the** **[12]** **CO and** **[13]** **CO lines**


**[Fig. A.1.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** Channel map for the [12] CO _J_ = 2→1 transition observed with NOEMA, the spatial resolution is 2.5 × 1.4 [′′], the contour spacing is 7σ.


A94, page 14 of 16

E. Di Folco et al.: An ALMA/NOEMA study of HD 141569A hybrid disc


**Fig.** **A.2.** Channel map for the [13] CO _J_ = 2→1 transition observed with NOEMA, the spatial resolution is 1.9 × 1.1 [′′], the contour spacing is 2σ,
same channel selection as for Fig. A.1.


A94, page 15 of 16

A&A 635, A94 (2020)


**[Fig. A.3.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201732243&pdf_id=0)** Channel map for the [13] CO _J_ = 1→0 transition observed with ALMA, the spatial resolution is 0.7 × 0.5 [′′], the contour spacing is 3σ, same
channel selection as for Fig. A.1.


A94, page 16 of 16


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "CO/H2 = 1e-4 ISM abundance",
  "failed_quote": "using the standard ISM abundance"
 }
]
```
