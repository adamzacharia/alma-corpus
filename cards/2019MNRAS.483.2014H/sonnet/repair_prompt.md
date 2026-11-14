# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019MNRAS.483.2014H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–12 (2018) Preprint 5 November 2018 Compiled using MNRAS L [A] TEX style file v3.0

## **Modelling the abundance structure of isocyanic acid** **(HNCO) toward the low-mass solar type protostar** − **IRAS 16293 2422**

### Antonio Hern´andez-G´omez, [1][,][2][⋆] Emna Sahnoun [3][,][4], Emmanuel Caux [2], Laurent Wiesenfeld [4][,][5], Laurent Loinard [1][,][6], Sandrine Bottinelli [2], Kamel Hammami [3], and Karl M. Menten [7]

1 _Instituto_ _de_ _Radioastronom´ıa_ _y_ _Astrof´ısica,_ _Universidad_ _Nacional_ _Aut´onoma_ _de_ _M´exico,_ _Morelia_ _58089,_ _Mexico_
2 _IRAP,_ _Universit´e_ _de_ _Toulouse,_ _CNRS,_ _UPS,_ _CNES,_ _Toulouse,_ _France_
3 _Laboratory_ _of_ _Atomic_ _Molecular_ _Spectroscopy_ _and_ _Applications,_ _Department_ _of_ _Physics,_ _Faculty_ _of_ _Science,_
_University_ _Tunis_ _El_ _Manar,_ _Campus_ _Universities,_ _1060_ _Tunis,_ _Tunisia_
4 _IPAG,_ _Universit´e_ _Grenoble_ _Alpes,_ _CNRS,_ _F-38000_ _Grenoble,_ _France_
5 _Laboratoire_ _Aim´e-Cotton,_ _Universit´e_ _Paris-Saclay,_ _CNRS,_ _Orsay,_ _France_
6 _Instituto_ _de_ _Astronom´ıa,_ _Universidad_ _Nacional_ _Aut´onoma_ _de_ _M´exico,_ _Apartado_ _Postal_ _70-264,_ _CdMx_ _C.P._ _04510,_ _Mexico_
7 _Max-Planck-Institut_ _f¨ur_ _Radioastronomie,_ _Auf_ _dem_ _H¨ugel_ _69,_ _D-53121_ _Bonn,_ _Germany_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
Isocyanic acid (HNCO), the most stable of the simplest molecules containing the four
main elements essential for organic chemistry, has been observed in several astrophysical environments such as molecular clouds, star-forming regions, external galaxies and
comets. In this work, we model HNCO spectral line profiles toward the low-mass solar

−
type protostar IRAS 16293 2422 observed with the ALMA interferometer, the IRAM,
JCMT and APEX single-dish radio telescopes, and the HIFI instrument on board the
Herschel Space Observatory. In star-forming environments, the HNCO emission is not
always in Local Thermodynamical Equilibrium (LTE). A non-LTE radiative transfer
approach is necessary to properly interpret the line profiles, and accurate collisional
rate coefficients are needed. Here, we used the RADEX package with a completely
new set of collisional quenching rates between HNCO and both ortho-H 2 and para-H 2
obtained from quantum chemical calculations yielding a novel potential energy surface in the rigid rotor approximation. We find that the lines profiles toward IRAS
16293−2422 are very well reproduced if we assume that the HNCO emission arises
from a compact, dense and hot physical component associated with the hot corino, a
warm component associated with the internal part of the protostellar envelope, and a
cold and more extended component associated with the outer envelope. The derived
HNCO abundances from our model agree well with those computed with the Nautilus
chemical code.


**Key** **words:** astrochemistry – molecular emission – stars: individual (IRAS 16293
–
2422) techniques: single-dish



**1** **INTRODUCTION**


Isocyanic acid (HNCO) is the most stable of the simplest
molecules containing all four atoms essential for life as
we know it. [1] In consequence, understanding the formation


⋆ E-mail: a.hernandez@irya.unam.mx
1 Cyanic acid (HOCN), fulminic acid (HCNO), and isofulminic
acid (HONC), are all less stable.


© 2018 The Authors



and evolution of this molecule in star-forming environments
might prove relevant to organic chemistry in space. Interstellar HNCO was first reported by Snyder & Buhl (1972)
toward the molecular cloud complex Sgr B2, where its emission was found to be abundant and spatially extended.
Further studies confirmed the high abundance of HNCO
with respect to H 2 toward molecular clouds in the direction of the Galactic center (e.g. Turner 1991; Mart´ın et al.
2008), and revealed its presence in various other environ

2 _Hern´andez-G´omez_ _et_ _al._


ments such as hot molecular cores (e.g. Blake et al. 1987;
van Dishoeck et al. 1995; MacDonald et al. 1996; Helmich
& van Dishoeck 1997; Bisschop et al. 2008), molecular outflows (e.g. Rodr´ıguez-Fern´andez et al. 2010), external galaxies (e.g. Meier & Turner 2005; Mart´ın et al. 2006, 2009) and
comets (e.g. Lis et al. 1997; Crovisier 1998; Biver et al. 2006).
HNCO was proposed to be a tracer of dense gas since it
has been observed in high density regions (e.g. Jackson et
al. 1984), as well as a tracer of shocks since its abundance
appears to be enhanced toward shocked gas regions (e.g.
Rodr´ıguez-Fern´andez et al. 2010). Much effort has been devoted to understanding the chemistry of HNCO in a variety of astrophysical environments (e.g. Quan et al. 2010;
Marcelino et al. 2009, 2010), but it is not yet fully constrained. In an early study, Iglesias (1977) proposed that
the formation pathway of HNCO in Sgr B2 could occur in
the gas phase through the chemical ion-neutral reactions


NCO [+] + H 2 → HNCO [+] + H, (1)

HNCO [+] + H 2 → HNCOH [+] + H, (2)

HNCOH [+] + e [−] → HNCO + H. (3)


Turner (2000) also suggested some neutral-neutral reactions
to form HNCO:


CN + O 2 → NCO + O, (4)


NCO + H 2 → HNCO + H, (5)


where reaction (5) has an activation barrier. More recently,
Marcelino et al. (2009, 2010) proposed a more complete gas
phase model to explain the abundance of HNCO and its
isomers in cold dense cores.
Other studies (e.g. Garrod et al. 2008; Tideswell et al. 2010)
have shown that HNCO could also be formed on dust grain
surfaces through the thermal reaction


NH + CO → HNCO, (6)


(which has no activation barrier according to Garrod et al.
2008) and then be released into the gas phase through desorption. For some time, it was believed that HNCO was directly related with the formation of NH 2 CHO (formamide,
a molecule important in prebiotic chemistry) via hydrogenation on grain surfaces. Recent laboratory experiments, however, have shown that this process is in fact inefficient (e.g.
Fedoseev et al. 2015; Noble et al. 2015). Regardless, both
gas phase and grain surface chemistry need to be taken into
account to correctly model the observed abundances in astrophysical sources of HNCO and other related molecules of
potential exobiological interest.


IRAS 16293-2422 (I16293 hereafter), a Class 0 protostar
located at 141 [+] − [30] 21 [pc] [(][Dzib] [et] [al.] [2018][)] [in] [the] [Ophiuchus]
star-forming region, is particularly interesting in this context. This protostar is often considered a template source for
astrochemistry since it has the richest molecular line spectrum known for low-mass protostars, spanning over a wide
range of frequencies (e.g. Caux et al. 2011; Jørgensen et al.
2016). In interferometric observations, I16293 is found to be
composed of two dense condensations, called A and B, separated by ∼705 AU (at a distance of 141 pc), presumably tracing a newborn binary system (Wootten 1989; Mundy et al.



1992). HNCO has been detected toward the compact sources
A and B (e.g. Bisschop et al. 2008) as well as in the surrounding large-scale envelope (e.g. van Dishoeck et al. 1995).
This makes I16293 an ideal target to study the chemistry of
HNCO at multiple scales in a low-mass star-forming environment (e.g. Bisschop et al. 2008; Marcelino et al. 2010).
Recently, L´opez-Sepulcre et al. (2015) modelled the emission
of HNCO in I16293 with a radiative transfer code, using the
collisional rate coefficients computed by Green (1986) for the
HNCO-He system. They obtained abundances with respect
to H 2 of (5 ± 4)× 10 [−][12] and (6 ± 3)× 10 [−][9] for the regions where
the temperature is, respectively, smaller and higher than 90
K. According to their model, this temperature corresponds
to the threshold for thermal desorption of some species from
icy dust mantles. Once in the gas phase, HNCO will be subject to collisions with other species. Since H 2 is, by far, the
most abundant collider in dense astrophysical environments,
it would be desirable to use coefficients for the HNCO-H 2
system –rather than HNCO-He. Such coefficients recently
became available (Sahnoun et al. 2018) for both forms of
H 2 (ortho and para) as a result of new quantum chemical
calculations (see Section 3.1).
In this work, we make use this new set of collision coefficients to model the HNCO lines profiles observed at different spatial scales with the Atacama Large
Millimeter/submillimeter Array (ALMA) and the singledish telescopes IRAM, the Atacama Pathfinder Experiment
(APEX), the James Clerk Maxwell Telescope (JCMT) and
Herschel Heterodyne Instrument for the Far-Infrared (HIFI,
de Graauw et al. 2010), over a wide range of frequencies. In
Section 2 we describe the observations in detail, while in Section 3 we describe the new HNCO-H 2 collisional coefficients
and the adopted physical model. In Section 4 we discuss our
findings and compare them with a chemical model and previously published results. Section 5 summarises our results.


**2** **OBSERVATIONS**


To study the extended HNCO emission from I16293,
we analysed a set of data obtained with the IRAM30m, JCMT-15m and APEX-12m, ground based single-dish
(sub)millimeter wavelength telescopes, as well as from the
HIFI instrument on board the Herschel Space Observatory
covering a frequency range from 80 GHz to 1 THz. The compact emission from the hot corino was studied with interferometric ALMA observations between 329 and 363 GHz. All

the observations are described in this section.


**2.1** **IRAM-30m** **and** **JCMT-15m** **observations**


First, we use observations that were part of TIMASSS (The
IRAS16293-2422 Millimeter And Submillimeter Spectral
Survey; Caux et al. 2011) conducted with the IRAM-30m
telescope (Granada, Spain) between 80 and 280 GHz and
the JCMT-15m telescope (Mauna Kea, Hawaii) between
328 and 366 GHz with a spectral resolution ranging from
0.51 to 2.25 km s [−][1] . These observations were carried out

between January 2004 and August 2006. For more details
on these observations, see Caux et al. (2011).


In addition, higher spectral resolution observations


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 3



(100 kHz, 0.13 km s [−][1] ) of the HNCO (5 0 5 − 4 0 4 ) transition were carried out with the IRAM-30m telescope between November 1st and 6th 2017 using the broad-band
Eight Mixer Receiver (EMIR) receivers connected to a Fast
Fourier Transform spectrometer (FFTS). The sky emission
was cancelled using the wobbler switching observing mode
and a throw of 150 [′′] . The total observing time for this run
was about 5.6 hours and the observed coordinates were α 2000
= 16 [h] 32 [m] 22 [s] . 64, δ 2000 = −24 [◦] 28 [′] 33 [′′] . 6.


**2.2** **APEX** **observations**


The observations of I16293 in the frequency range 265–
323.5 GHz were performed with the APEX telescope on the
Chajnantor plateau (Chile) during several runs in 2011 and
2012. The observations were carried out using the APEX-1
and APEX-2 receivers in the wobbler switching observing
mode, with a throw of 150 [′′] . A FFTS was connected to the
APEX receivers, providing a spectral resolution of 60 kHz
and a total bandwidth of about 1.5 GHz per tuning. The
on-source integration time was 30 to 60 min per setting,
depending on the frequency, to reach a similar rms noise
level over the complete frequency range observed. The
observed coordinates were α 2000 = 16 [h] 32 [m] 22 [s] . 87, δ 2000 =
−24 [◦] 28 [′] 36 [′′] . 6.


The transitions between 372 and 462 GHz were ob
served during August 2013 under very good weather
conditions using a modified version of the First Light Apex
Submillimeter Heterodyne receiver (FLASH; Heyminck et
al. 2006). The spectral resolution delivered by the backends
was 38.15 kHz corresponding to a velocity resolution of 0.03
(372 GHz), 0.027 (418 GHz) and 0.025 km s [−][1] (462 GHz).
Since I16293 is a very bright sub-millimeter source, the
pointing of the telescope was checked regularly using I16293
itself. Thus, the observed position corresponds to the peak
of the sub-millimeter emission at α 2000 = 16 [h] 32 [m] 22 [s] . 9,
δ 2000 = −24 [◦] 28 [′] 35 [′′] . 6.


The final velocity resolution of all APEX observations
was degraded to ∼ 0.6 km s [−][1] to increase the signal to noise
ratio without losing much information on the line profile.


For both the IRAM November 2017 and the APEX

observations, the data reduction was performed using the
GILDAS/CLASS90 [2] package. The telescopes and receivers
parameters (main-beam efficiency B eff, forward efficiency
F eff, half power beam width HPBW) were taken from the
IRAM and the APEX webpages. The rms noise achieved is
typically 10 mK (T mb ) per 0.6 km s [−][1] velocity channel for
the APEX data, and 3 mK (T mb ) per 0.6 km s [−][1] velocity
channel for IRAM data.


**2.3** **Herschel-HIFI** **observations**


Observations with the HIFI instrument onboard the Her
schel Space Observatory were conducted as part of the
guaranteed-time key program CHESS (Chemical Herschel


2 http://www.iram.fr/IRAMFR/GILDAS/


MNRAS **000**, 1–12 (2018)



Surveys of Star-forming regions, Ceccarelli 2010), whose
goal was to perform spectral surveys in the frequency
range 480 − 1790 GHz with a high spectral resolution (∼
1.1 MHz). The data used in this article are part of a full
spectral coverage of bands 3b (860-960 GHz ; Obs. Id
1342192330) and 4a (950-1060 GHz ; Obs. Id 1342191619),
which were obtained on 19 March, and 3 March 2010,
respectively. The Spectral Scan Double Beam Switch (DBS)
with optimization of the continuum observing mode was
used. A spectral resolution of 1.1 MHz (∼ 0.3 km s [−][1] at 1
THz) was provided by the HIFI acousto-optic Wide Band
Spectrometer (WBS) with an instantaneous bandwidth of
4×1 GHz (Roelfsema et al. 2012). The observed coordinates
were α 2000 = 16 [h] 32 [m] 22 [s] . 64, δ 2000 = −24 [◦] 28 [′] 33 [′′] . 6. The
DBS reference positions were situated approximately 3 [′]

east and west of the source.


To carry out a spectral survey, multiple local oscillator
tunings are used, in order to cover the required frequency
bands. A single local oscillator tuning spectrum consists of
eight separate spectra: four per polarization (horizontal and
vertical) in 4 sub-bands of ∼1 GHz each. Using the HIPE
(Ott 2010) “flagTool” task, we removed the spurs not automatically eliminated by the pipeline. Standing waves and
baselines removal on each sub-band were performed with
the HIPE tasks “fitHifiFringe” and “fitBaseline”. The sideband deconvolution was performed using the HIPE task
“doDeconvolution”, and the resulting deconvolved spectra
observed in both polarizations were averaged to improve
the noise in the final spectra, given that they had similar quality. The task “fitBaseline” was then ran to obtain
the continuum values which are well fitted by order 3 polynomials over the frequency range of the whole sub-bands.
These single side band continuum values were then added to
the spectra at the considered frequencies. Finally, we used
the forward efficiency of 0.96 and the (frequency-dependent)
beam-efficiency given in Table 1 of Roelfsema et al. (2012)
to convert the intensities from antenna to main-beam tem
perature scale.


**2.4** **ALMA** **observations**


PILS, the ALMA Protostellar Interferometric Line Survey
(Jørgensen et al. 2016), reported ALMA observations in
the frequency range [329.15, 362.90] GHz with a ∼0.2 km
s [−][1] channel spacing and a ∼0.5 [′′] spatial resolution. Five
HNCO lines used in this work were observed in this survey,
HNCO (15 0 15 − 14 0 14 ), (15 1 14 − 14 1 13 ), (16 0 16 − 15 0 15 ),
(16 1 16 − 15 1 14 ) and (16 1 16 − 15 1 15 ). These interferometric
observations, not sensible to the extended emission, were
only used to determine some physical parameters of the
hot corino component. As can be seen in Figure 1, the
HNCO (15 0 15 − 14 0 14 ) line integrated intensity is 9 times
larger for A than for B, allowing us to assume in this work
that source A is solely responsible of the hot corino emission.


Table A1 summarises the observation parameters as
well as spectroscopic information for the observed lines
from the Cologne Database for Molecular Spectroscopy [3]


3 https://www.astro.uni-koeln.de/cdms

4 _Hern´andez-G´omez_ _et_ _al._


**Figure** **1.** HNCO 15 0,15 −14 0,14 line emission as observed towards
IRAS16293 in the PILS survey toward source A (red line), and
source B (blue line).


(CDMS, M¨uller et al. 2001, 2005). This database makes use
of spectroscopic data from Kukolich (1971), Hocking (1975),
Niedenhoff (1995) and Lapinov (2007). All line intensities
are expressed in main beam brightness temperature units
(T mb ), after correction of rear-ward losses and main-beam
efficiency and for the atmospheric attenuation for IRAM,
APEX and JCMT observations.


**3** **RESULTS**


To identify and model the relevant HNCO spectral lines, we
used CASSIS [4] (Caux et al. 2011), a software developed at
IRAP-UPS/CNRS which makes use of the CDMS database
(M¨uller et al. 2001, 2005). 35 transitions are present in the
IRAM observations, 16 in the APEX ones and 6 in the
JCMT ones. We also found 47 transitions falling within the
HIFI observations range. Most of these latter lines were not
detected (see Appendix), but the corresponding upper limits were used as constraints in the modelling. The details for
all the transitions used are given in Table A1. We illustrate
in Figure 2 the transitions observed and their corresponding levels as a function of the quantum number K c and the
energy above the ground state.
To model the line profiles we used the statistical equilibrium non-LTE radiative transfer code RADEX (van der
Tak et al. 2007) that uses the escape probability formalism.
The HNCO collisional coefficients are taken from Sahnoun
et al. (2018) and were obtained as we now describe.


**3.1** **HNCO** **collisional** **coefficients**


The main aspects of the collisional coefficients computation
are summarised in this section. The full description can be
found in Sahnoun et al. (2018).


**Potential** **Energy** **Surface**


The Potential Energy Surface (PES) for the HNCO-H 2 van


4 http://cassis.irap.omp.eu



**Figure** **2.** Sketch of the rotational levels of HNCO, labelled by
J K a K c, and energy in Kelvin. Lines connect observable transitions, at frequencies 80 < ν < 1200 GHz. Blue lines indicate
transitions detected in emission; red lines indicate transitions detected in absorption. Light grey lines indicate transitions that
were looked for but not detected, while dashed lines indicate tran
sitions that were not observed.


der Waals system was recently computed by Sahnoun et
al. (2018). This five dimensional PES was computed in the
rigid-rotor approximation. The HNCO and H 2 internuclear
distances are frozen at the experimental average value for
the vibrational ground state (distances in bohr, angles
in degrees). For H 2, we set _r_ HH = 1.4011. The planar
HNCO parameters are set to _r_ HN = 1.9137, _r_ NC = 2.3007,
_r_ CO = 2.2028, α(HNC) = 124.0, α(NCO) = 172.1 (Fusina &
Mills 1981). We computed the PES for distances _R_ between
center of masses from 4.5 to 50 bohr. About 430,000 ab
initio points were computed in the C1 symmetry group
with the CCSD(T)-F12a method using for atomic bases
the standard aug-cc-pVDZ basis set as implemented in the
MOLPRO2011 package (Werner et al. 2012). The basis set
superposition error has been corrected at all geometries
with the counterpoise procedure (Nizam et al. 1988). The
PES has a global minimum of _V_ = −235.26 cm [−][1] located
at _R_ = 7.9 bohr and angles such that the H 2 molecule
is perpendicular to the HNCO plane, and its center is
collinear with the NH bond. This PES presents a very large
anisotropy because of the rod-like geometry of the HNCO
molecule, with the H atom protruding out of the nearly
linear NCO arrangement.


**Rotational** **quenching** **cross** **sections** **and** **rates**


The PES ab initio points were fit in terms of polyspherical harmonic functions in order to be introduced in the
Molscat dynamical code. [5] Computation of the rotational
quenching cross-sections was done within the coupled-states
quantum time-independent formalism for collision energies up to 500 cm [−][1] (719 K), for both ortho-H 2, _J_ H 2 = 1
and para-H 2, _J_ H 2 = 0, 2. The cross sections were averaged using the Maxwell-Boltzmann distribution to calculate
the rate coefficients as a function of the kinetic temperature.


5 ∼
http://ipag.osug.fr/ afaure/molscat/index.html


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 5


All details about the collisional coefficients computation
may be found in a preceding paper, Sahnoun et al. (2018).
It was shown that the quenching rates with ortho-H 2 are
larger than the corresponding ones with para-H 2 . Also, the
rates connecting the _K_ a = 0 levels are somewhat larger than
those corresponding to the _K_ a = 1 levels. Hence, quenching
redistributes the level populations in a manner far from the
black-body distribution.


**3.2** **The** **physical** **model**



Several previous studies have shown that I16293 has a
hot corino revealed by the emission of numerous complex
molecules in both the A and B sources. In addition, a common, extended infalling envelope surrounding the binary
system has also been observed by single-dish telescopes
(e.g. Caux et al. 2011). Crimier et al. (2010) determined
the physical structure of I16293 from single-dish and interferometric continuum observations, assuming a spherical
source, and provided temperature and density profiles
up to R ∼6000 AU. More recently, Jacobsen et al. (2018)
studied the inner envelope of I16293 up to R ∼8000 AU
(∼ 113 [′′] size) with a 3D dust and gas model based on
ALMA observations. By comparing those studies, we noted
that the model of the envelope in Jacobsen et al. (2018)
is fully compatible with Crimier et al. (2010) in the same
radius range. Last, OTF observations of CS (Menten et al.
1987), and CN (Hern´andez-G´omez et al. 2018), have shown
the presence of an extended cold envelope component (size
larger than 100 [′′] ).


We therefore modeled the HNCO lines assuming I16293
can be represented by 3 physical components: a single hot
corino of size 0.5” (see 2.4), a warm envelope (R ≤ 1000 AU)
and a cold, extended envelope (R ≥ 1000 AU), see Figure 3.
In order to constrain the parameters of each of the three
physical components, we have used the 1D physical structure
derived by Crimier et al. (2010), fixing thereby the main H 2
density for all components from their derived density profile.


A fundamental ingredient for the modelling is the
continuum level in the spectra. However, because of the
observing mode at IRAM and JCMT, no continuum was
recovered during those observations. This is not the case
for APEX and HIFI observations. To have a consistent

model taking into account the continuum level for all
lines, we have computed the spectral energy distribution
(SED) for the envelope of I16293 with several instruments
(such as PACS, SPIRE, MIPS, MAMBO2, LABOCA, IRS,
SCUBA2, NIKA2 and HIFI) and derived the expected
continuum from ∼1 mm to ∼70 µm (∼150 GHz to ∼5 THz)
(Bottinelli et al., in prep.). We have checked that the predicted continuum level is consistent with the observations

within an error of about 15%. We subtracted the continuum

for spectra that show continuum and added the predicted
continuum for all lines.


**3.3** **Model** **fitting**


In CASSIS, it is possible to model with RADEX (van
der Tak et al. 2007) an observed spectrum with a set of


MNRAS **000**, 1–12 (2018)



**Figure** **3.** Adopted 3 components physical structure to model
the HNCO emission in I16293.


physical components, each of them defined with six physical
parameters that will serve as input for RADEX: the size of
the component, its density n(H 2 ), its kinetic temperature
T kin, the Full Width at Half Maximum (FWHM) and the
velocity relative to the Local Standard of Rest V LSR of
the lines, and the column density N of the studied specie.
Since our observations have sufficient spectral resolution,
we fixed V LSR of the lines for the warm and cold envelopes
to 4.1 km s [−][1] . Given that the component associated with
the cold envelope has a narrow line width, we have fixed
its FWHM to 0.4 km s [−][1] . The parameters left to vary
during the optimization are therefore the column density
and kinetic temperature for all components, FWHM and
V LSR for the hot corino, and FWHM and size for the warm
envelope. For the hot corino, we adopted an ortho-to-para
H 2 ratio of 3 but we checked that varying this value did
not influence the final results. For both envelope layers, we
assumed that para-H 2 is the dominant form since para-H 2
is more stable at lower temperatures. We have therefore
modelled I16293 in terms of the superposition of three
physical components represented on Figure 3, with a total
of 10 free parameters out of 18 possible.


We used the Monte Carlo Markov Chain (MCMC)
method inside CASSIS (Hastings 1970; Guan et al. 2006)
which explores the space of parameters to find the best
solution by means of χ [2] minimisation, running 1,000 models
with these 10 free parameters randomly chosen. Table 1
shows the best values obtained from the χ [2] minimisation,
and Figure 4 shows observed and simulated spectra of some
of the HNCO transitions, while all spectra are shown in
appendix _B_ 1. In all cases, the predicted emission has been
diluted with the appropriate telescope beam, considering
the frequency of the transitions and the assumed size of the
given physical component.


It should be noted that the observations used in this

6 _Hern´andez-G´omez_ _et_ _al._


study cannot constrain the size of the hot corino, nor that
of the extended envelope, the single-dish beams being either
too big or too small to provide useful information. The
given column-densities and abundances are therefore those
corresponding to the adopted sizes of these components
(0.5 [′′] and 100 [′′], respectively), and should be scaled if other
sizes are used. Only the size of the HNCO emission in
the warm envelope can be correctly constrained with the
observations we have in hands.


**4** **DISCUSSION**


**4.1** **HNCO** **physical** **parameters**


The best results from our model give a temperature for
the HNCO-bearing gas associated with the hot corino of
about 200 K and a column density of (1.9 ± 0.4) × 10 [16]

cm [−][2], which corresponds to an abundance relative to H 2 of
(7.1 ± 0.6) × 10 [−][8] for a fixed size of 0.5 [′′] . This abundance
is in agreement with typical values measured for other hot
cores (e.g. Bisschop et al. 2007). Mart´ın-Dom´enech et al.
(2017) derived the column density of HNCO towards the
hot corino associated with source B in I16293 measuring the
HNC [18] O column density and adopting an isotopic ratio of
16 O/ 18 O = 500. They obtained _N_ (HNCO)= (4.9 ± 1.9) × 10 16

cm [−][2] and an abundance of (1.8 ± 0.7) × 10 [−][9] . Although the
column density for source A computed with our model is
similar to the column density derived by Mart´ın-Dom´enech
et al. (2017) for source B, we predict a higher abundance
for source A. For the warm envelope, we found a column
density of (2.5 ± 0.5)× 10 [13] cm [−][2], a temperature of (31 ± 5) K,
a size of (15.6 ± 2.4) [′′] and an abundance of (1.8 ± 0.4)× 10 [−][11] .
The line widths are smaller (4.9 km s [−][1] ) than those found
for the hot corino (6.2 km s [−][1] ). This behaviour is expected
if we consider that the infall and rotation speeds are larger
toward the center of the envelope. For the cold outer layer
of the envelope, we derive a temperature of about 9 K and
a column density of (5.3 ± 0.6) × 10 [12] cm [−][2] . The resulting
abundance is (9.8 ± 0.3) × 10 [−][12], which is very similar to
that of the warm envelope.


In a previous study, van Dishoeck et al. (1995) derived
a value for the HNCO column density in the envelope
of I16293 based on data obtained with the JCMT and
the CSO (Caltech Submillimeter Observatory located on
Mauna Kea, Hawaii) of (3.4 ± 1.5) × 10 [13] cm [−][2] and an
abundance with respect to H 2 of 1.7×10 [−][10] by using the rotational diagram technique, which assumes LTE conditions
(although no source size for the envelope was derived from
their observed HNCO transitions). The column density
derived by us is consistent with that reported by van
Dishoeck et al. (1995) but our abundance is lower by a
factor of 10. This difference could be related with the
different assumed H 2 column densities. Moreover, assuming
LTE conditions might not be appropriate for the envelope
of I16293. Indeed, L´opez-Sepulcre et al. (2015) already
pointed out this problem. These latter authors computed
the abundances for HNCO using a non-LTE radiative
transfer model together with collision coefficients from
Green (1986) and found abundances between (6±3) × 10 [−][9]



for T> 90 K in the warm envelope and (5±4) × 10 [−][12] for
T< 90 K corresponding to the cold envelope. We argue that
the differences between our abundances and those of L´opezSepulcre et al. (2015) reflect, in part, the different number
of components considered in the different models: while
ours considers three distinct components, L´opez-Sepulcre
et al. (2015) only includes two. Our hot corino component
has a size of 0.5 [′′], corresponding to a radius of 35 AU. This
is significantly more compact that the region (of radius,
fortuitously, 90 AU) where the temperature is higher than
90 K. As a consequence, this latter region in the model
of L´opez-Sepulcre et al. (2015) would correspond in our
model to a mixture of the hot corino region and the warm
envelope component. It is, therefore, not surprising that
the abundance, (6±3) × 10 [−][9], reported by L´opez-Sepulcre
et al. (2015) for this region is intermediate between the
abundances we derive here for the hot corino and the

warm envelope. For the region outside of 90 AU, we
derive an abundance of 1 to 2 × 10 [−][11], which is within a
factor of two of that derived by L´opez-Sepulcre et al. (2015).


**4.2** **Spectral** **modeling**


We see that most of the lines are very well reproduced
by the model based on the physical parameters discussed
above (see Figure 3). However, some of them are underestimated (see the predicted line profiles by the model in the
Appendix; note that in some cases, the predicted emission
could not be computed for some HNCO transitions since
their corresponding collisional rate coefficient was lacking in
the computation of Sahnoun et al. (2018)). For the spectroscopic branch _K_ a = 1, the agreement between the model and
the data is less good for transitions at lowest frequencies
(e.g. _J_ = 4, 5). We have searched for line blending with other
species for these transitions in particular to verify if the
line intensities were affected by this problem but we did not
found a clear contribution from other molecules. For the

transitions belonging to the _K_ a = 2 levels, the problem is
more severe. It could be argued that collision coefficients are
particularly inaccurate for such lines. However, examining
the spectra of similar molecules, like H 2 CO, one sees the
same type of problems. A thorough discussion is given by
Mangum et al. (1993, 2015). Formaldehyde has a rotational
spectra similar to HNCO, with a heavy rod or rod-like
part (NCO vs. CO), and only light H atom(s) breaking the
rod-like symmetry. Both molecules have thus very distinct
_K_ a = 0, 1, 2, . . . branches well separated one from the other.
Other molecules, less abundant, present a very similar type
of spectroscopy (e.g. H 2 CS and l-C 3 H 2 ).


While for H 2 CO the intensities and line-shapes are well
understood for _K_ a ≤ 2 (see methods proposed by Mangum
et al. 1993), this is not always true for the higher lying
_K_ a - 2 branch, very similarly to our case of HNCO. The
higher _K_ a = 2 transitions we observe connect levels which
are not correctly modelled. That is, the levels with high- _J_
and _K_ a = 2 or any level with _K_ a - 2 are not considered
in the computation of the collisional coefficients used in
this paper. These high levels could be populated by specific
excitation, perhaps originating in some hotter photonic
bath or some specific excitation, not properly taken into


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 7


**Table** **1.** Best physical parameters (those with [∗] being fixed) obtained with the χ [2] minimization. The abundance was computed with
respect to H 2 .


Component N T kin FWHM V LSR Size n(H 2 ) X(n HNCO /n H 2 )
(cm [−][2] ) (K) (km s [−][1] ) (km s [−][1] ) ( [′′] ) (cm [−][3] )


Hot corino (1.9 ± 0.4) × 10 [16] 190 ± 50 6.2 ± 0.7 2.9 ± 0.1 0.5 [∗] 3×10 [8] (7.1 ± 0.6) × 10 [−][8]

Warm envelope (2.5 ± 0.5) × 10 [13] 31 ± 5 4.9 ± 0.8 4.1 [∗] 15.6 ± 2.4 5×10 [7] (1.8 ± 0.4) × 10 [−][11]

Cold envelope (5.3 ± 0.6) × 10 [12] 8.7 ± 0.8 0.4 [∗] 4.1 [∗] 100.0 [∗] 3×10 [6] (9.8 ± 0.3) × 10 [−][12]



Frequency (GHz)
219.787 219.795 219.802



Frequency (GHz)
285.707 285.717 285.726









0.53


0.43


0.33



Frequency (GHz)
351.616 351.627 351.639



1.05


0.81


0.57







1.06


0.94


0.82



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
350.316 350.327 350.339



Frequency (GHz)
218.970 218.977 218.985









Frequency (GHz)
284.648 284.657 284.667



1.04


0.97


0.89


0.81





0.75


0.66


0.56



0.42


0.38


0.33



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
923.575 923.606 923.637







Frequency (GHz)
967.126 967.158 967.190



Frequency (GHz)
1010.347 1010.381 1010.415


1.08


0.95


0.82





0.90


0.81


0.72



1.02


0.90


0.78



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



**Figure** **4.** In black, we show some of the observed HNCO line profiles as seen by different telescopes, while in red we show the predicted
profiles from our model with the parameters reported in Table 2.



account.


Note that we have not considered infrared (IR) pumping
to vibrationally excited states of HNCO. For this molecule,
the ν 4, ν 6 and ν 5 fundamental bending vibrations have energies above ground by 1118, 949, and 831 K, respectively
(see, e.g., Yamada 1977). Various rotational lines with _J_ = 4
and 5 from within the ν 5 = 1 and ν 6 = 1 (and possibly the
ν 4 = 1) states have been detected by Belloche et al. (2017)
with ALMA toward the hot core Sgr B2 (N2). These lines intensities are characterized by a source model whose angular
source size and rotational temperature are not too different
from the values used by us for I16293. Some of the lines had
even been detected in an earlier survey with the IRAM 30-m
telescope Belloche et al. (2013). While quite weak for detection by the single dishes employed by us, future ALMA data
could address HNCO excitation in the hot corino in I16293.

Deciding whether vibrational excitation by IR photons or
collisions are both feasible or whether such excitation and


MNRAS **000**, 1–12 (2018)



re-decay to the ground state could influence the intensities of
the _K_ a = 2 lines lies beyond the scope of the present paper.


**4.3** **Comparison** **with** **Green** **collisional** **coefficients**


The new collisional coefficients with respect to those computed by Green (1986) bring three advantages :


(a) More temperatures are considered, 17 with the new set
of coefficients (7, 10, and 20 to 300 K with a step of 20 K)
with respect to 5 for Green coefficients (20, 40, 80, 160 and
320 K).

(b) More collisional transitions are considered (2272 against
2254).

(c) The coefficients are computed separately for collisions
with p-H 2 and o-H 2, allowing to deal with the o/p ratio, an
important factor in cold environments.


While the computed spectra using both set of collisional coefficients are similar for our I16293 three components model at frequencies ≤ 500 GHz, there are some dif

8 _Hern´andez-G´omez_ _et_ _al._


**Figure** **5.** Comparison of the I16293 computed spectrum for
the HNCO (4 1,3 − 4 0,4 ) transition (ν = 902505.9937 MHz, E up
= 53.86 K A ij = 7.85 ×10 [−][3] ) with our 3 components model. Blue
: Green coefficients, Red : new set of coefficients.


ferences at higher frequencies, as can be seen on Figure 5,
justifying the use of this new set for an optimal modelisation.


**4.4** **Chemical** **modelling** **with** **Nautilus**


To further investigate the chemistry of HNCO in the envelope of I16293 and to probe the abundances derived from
our full non-LTE radiative transfer model, we computed the
abundance profiles using the Nautilus chemical code. Nautilus is a three phase gas-grain chemical code that allows us
to compute the chemical composition as a function of time.
The details of the chemical reactions included in the code
are explained in Ruaud et al. (2016). The gas phase network
used by Nautilus is based on kida.uva.2014 (Wakelam et al.
2015), while the grain chemistry is presented in Ruaud et al.
(2015). The modelling is made in two steps: first, we run a
simulation for the parental cloud where the protostar I16293
was formed, and then we take the resulting abundances as
input for the protostar phase, where we use the 1D structure
for the envelope defined by Crimier et al. (2010, i.e., the temperature and density profiles) to compute the corresponding
abundance profile.
For the parental cloud, as Hincelin et al. (2011), we
have used the atomic initial abundances and the following
set of physical parameters, which are typical for cold dense
clouds in the Solar neighbourhood: _n_ = 3 × 10 [4] cm [−][3], T = 10
K, C/O ratio = 0.7, gas to dust ratio = 100 and grain size
= 0.1 µm, UV field _G_ 0 = 1 Habing (1.6 × 10 [−][3] erg cm [−][2]

s [−][1] ), visual extinction A v = 3, cosmic ray ionization rate
ζ = 1.3 × 10 [−][17] s [−][1], evolution time for the cloud to reach the
pre-stellar phase = 2.5×10 [5] years. We ran several simulations
changing the value of A v (from 3 to 30), density (from 3×10 [3]

to 3 × 10 [5] cm [−][3] ), evolution times (from 10 [5] to 5 × 10 [5] years),
C/O ratio (0.7 and 1.2) and cosmic ray ionization rate (from
10 [−][17] to 10 [−][16] s [−][1] ), and found that the only parameters
changing the abundance profiles are the visual extinction
A v and the cosmic ray ionization rate ζ. The abundance
profiles that best reproduces the observations are obtained
with A v = 4 and ζ = 8.0 × 10 [−][17] s [−][1] . Although this value of ζ
is higher that the commonly assumed standard value for the
Solar neighbourhood (1.3 × 10 [−][17] s [−][1] ), the Ophiuchus star


forming region is known to have a high cosmic ionization
rate (e.g. Hunter et al. 1994).


**4.5** **Results** **of** **the** **Nautilus** **chemical** **model** **for**

**HNCO**


Once the final abundances are computed, we use them as
input and run a simulation taking into account the density
and temperature profiles defined by Crimier et al. (2010)
for the envelope of I16293. To do that, we kept the same
visual extinction and cosmic ionization rate used for the

initial cloud. The resulting HNCO radial abundance profile
for different ages of the protostar is shown in Figure 6. The
model for the warm envelope predicts a high abundance
(larger than ∼ 10 [−][9] ) close to the hot corino value (in
agreement with the model described above), while for the
warm envelope radius derived from our non-LTE radiative
transfer model of 7.8 [′′], the abundance varies from 10 [−][12] to
10 [−][10], depending on the age of the protostar. For the external envelope, the abundance profile seems to change more
rapidly with time. At a radius of 30 [′′], where the difference
between the predicted abundances seems to be larger, the
model predicts a smaller abundance for largest age (∼ 10 [−][12]

for 1.4 × 10 [5] yr) and vice-versa (∼ 10 [−][9] for 1.0 × 10 [4] yr).
The final values for the abundance predicted with Nautilus
(although smaller) are closer to the abundance predicted
by the radiative transfer model for younger ages. In fact,
the age of I16293 in the literature is reported to be between
∼ 10 [4] − 10 [5] years. For instance, Qu´enard et al. (2018)
studied the emission of HNCO towards the hot corino

associated with source B and the cold envelope of I16293
using the chemical code UCLCHEM. They compared the
abundance for source B obtained by Mart´ın-Dom´enech
et al. (2017, 1.8 × 10 [−][9] ) and the abundance for the cold
envelope derived by van Dishoeck et al. (1995, 1.7 × 10 [−][10] )
and found an age for the protostar close to ∼(2 − 4) × 10 [4]


years.


From the simulations, we conclude that we cannot
use HNCO as a chemical clock to constrain the age of
the protostar due to the strong dependence on the initial
parameters for the model. If we take an age of about 5.8×10 [4]

years, we observe that the abundance profile, although not
constant, is in good agreement with the abundances derived
directly from the observations with our radiative transfer
model. We also found that the Nautilus input parameters
used to reproduce the HNCO observed abundances are very
similar to those derived by other authors using Nautilus
and single-dish data for other molecules such as HDO
(Coutens et al. 2012), CH (Bottinelli et al. 2014), CH 3 SH
(Majumdar et al. 2016), C 3 H 2 (Majumdar et al. 2017) or
HOCO [+] (Majumdar et al. 2018).


Recently, observations of the ortho- and para-groundstate lines of both H 2 D [+] and D 2 H, deuterated isotopologues
of the fundamental H [+] 3 [ion,] [have] [been] [performed] [toward]
I16293 with the APEX telescope and the Stratospheric Observatory for Infrared Astronomy (SOFIA) (Br¨unken et al.
2014; Harju et al. 2017). Given the observed simple line profiles, their narrow width and LSR velocities, the lines from
these species originate in the extended envelope of I16293.
For both species, their ortho-to-para ratio, OPR, is time

MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 9


**Figure** **6.** HNCO abundance profile computed with Nautilus for the envelope of I16293 assuming a cosmic ionization rate of 8.0 × 10 [−][17]

s [−][1] . The colours of the lines indicate the age of the protostar in years. The light yellow horizontal band represent the predicted abundance
for the warm envelope from our CASSIS-RADEX model (1.8 ± 0.4 × 10 [−][11] ), while the light green colour band represent the predicted
abundance for the cold envelope (9.8 ± 0.3 × 10 [−][12] ). Both bands have a 3σ error width. The black vertical line represents the radius of
the warm envelope of 7.8 [′′] .



dependent. Modelling the observed OPR for H 2 D+ Br¨unken
et al. (2014) derive an age of order 10 [6] yr. This value is
further constrained to 5 × 10 [5] yr by Harju et al. (2017) who
combines the observed values for the H 2 D [+] and D 2 H [+] OPR.
This age is considerably older that the values from Nautilus
modelling. While this might be understandable for the age
of the hot corino, the discrepancy between the age derived
from the H 2 D [+] and HNCO in the extended envelope is difficult to explain.


**5** **CONCLUSIONS**


In this work, we have presented an analysis of isocyanic
acid (HNCO) line emission towards IRAS 16293-2422 as
observed with single-dish telescopes (IRAM, APEX, JCMT
and Herschel/HIFI) over a wide range of frequencies. The
HNCO line profiles are interpreted as the superposition of
three physical components along the line of sight: a dense,
warm and compact source associated with the hot corino
in I16293, a more extended component associated with
the warm part of the envelope, and a cold and extended
component corresponding to the outer layer of the envelope.
We have constrained most of the parameters for each
physical component based on the structure derived by
Crimier et al. (2010).


We used a full non-LTE radiative transfer model in

CASSIS-RADEX to predict the line emission profiles by
using the new HNCO collisional rate coefficients computed
by Sahnoun et al. (2018) from a set of rotational excitation
quenching rates between HNCO and both ortho and para
H 2 . We obtain physical values for the hot corino that are in
very good agreement with what has been found for other hot
cores (e.g. Bisschop et al. 2007). From the derived column
densities, we found that the abundances in both warm and


MNRAS **000**, 1–12 (2018)



cold layers of the envelope are very similar (close to ∼ 10 [−][11] ).


While the transitions on the _K_ a = 0, 1 bands are
well reproduced, the transitions belonging to the upper
rotational band _K_ a = 2 levels are not. We argue that those
levels could be populated by specific excitation due to a
hotter photonic or collisional bath and that the modelling
is not able to take these excitations into account.


We used the three phase chemical gas-grain code Nautilus to compute the chemical composition of the envelope
of I16293 and produce an HNCO radial abundance profile.
We found that the younger ages for the protostar are in
better agreement with our radiative transfer model results.
However, HNCO cannot be used as a reliable chemical clock
due to the high dependence on the initial parameters in our
simulations.


**ACKNOWLEDGEMENTS**


HIFI has been designed and built by a consortium of institutes and university departments from across Europe,
Canada and the United States under the leadership of SRON
Netherlands Institute for Space Research, Groningen, The
Netherlands and with major contributions from Germany,
France and the US. Consortium members are: Canada:

CSA, U.Waterloo; France: CESR, LAB, LERMA, IRAM;
Germany: KOSMA, MPIfR, MPS; Ireland, NUI Maynooth;
Italy: ASI, IFSI-INAF, Osservatorio Astrofisico di ArcetriINAF; Netherlands: SRON, TUD; Poland: CAMK, CBK;
Spain: Observatorio Astron´omico Nacional (IGN), Centro
de Astrobiolog´ıa (CSIC-INTA). Sweden: Chalmers University of Technology - MC2, RSS & GARD; Onsala Space Observatory; Swedish National Space Board, Stockholm University - Stockholm Observatory; Switzerland: ETH Zurich,

10 _Hern´andez-G´omez_ _et_ _al._


FHNW; USA: Caltech, JPL, NHSC.
This work is based on observations carried out under project
number [014-17] with the IRAM 30m telescope. IRAM is
supported by INSU/CNRS (France), MPG (Germany) and
IGN (Spain).
APEX is a collaboration between the Max-Planck-Institut

fur Radioastronomie, the European Southern Observatory,
and the Onsala Space Observatory.
The James Clerk Maxwell Telescope is operated by the East
Asian Observatory on behalf of The National Astronomical Observatory of Japan; Academia Sinica Institute of Astronomy and Astrophysics; the Korea Astronomy and Space
Science Institute; the Operation, Maintenance and Upgrading Fund for Astronomical Telescopes and Facility Instruments, budgeted from the Ministry of Finance (MOF) of
China and administrated by the Chinese Academy of Sciences (CAS), as well as the National Key R&D Program of
China (No. 2017YFA0402700). Additional funding support
is provided by the Science and Technology Facilities Council
of the United Kingdom and participating universities in the
United Kingdom and Canada.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2013.1.00278.S. ALMA is a partnership
of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), MOST and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.
A.H-G., E.C., L.L and S.B. acknowledge the financial
support of the French/Mexico CONACyT – ECOS-Nord
Project ECOS-nord n [◦] : M14U01 : SPECIMEN : **S** tructure
**P** hysiqu **E** et **CI** n´e **M** atiqu **E** d’IRAS 16293 : mol´ecules et
conti **N** uum. A.H-G. and L.L. acknowledge the financial support of DGAPA, UNAM (project IN112417), and CONACyT, Mexico. L.W. and E.S. thank the COST action
CM1401, “Our Astrochemical History” for some travel support.


**REFERENCES**


Belloche A., M¨uller H. S. P., Menten K. M., Schilke P., Comito
C., 2013, A&A, 559, A47
Belloche A., et al., 2017, A&A, 601, A49
Bisschop, S. E., Jørgensen, J. K., van Dishoeck, E. F., & de
Wachter, E. B. M. 2007, A&A, 465, 913
Bisschop, S. E., Jørgensen, J. K., Bourke, T. L., Bottinelli, S., &
van Dishoeck, E. F. 2008, A&A, 488, 959
Biver, N., Bockel´ee-Morvan, D., Crovisier, J., et al. 2006, A&A,
449, 1255
Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G.
1987, ApJ, 315, 621
Bottinelli, S., Wakelam, V., Caux, E., et al. 2014, MNRAS, 441,

1964

Br¨unken S., et al., 2014, Natur, 516, 219
Caux, E., Kahane, C., Castets, A., et al. 2011, A&A, 532, A23
Caux, E., Bottinelli, S., Vastel, C., & Glorian, J. M. 2011, The
Molecular Universe, 280, 120
Ceccarelli C., et al. 2010, A&A, 521, L22
Coutens, A., Vastel, C., Caux, E., et al. 2012, A&A, 539, A132
Ceccarelli, C., Loinard, L., Castets, A., Tielens, A. G. G. M., &
Caux, E. 2000, A&A, 357, L9
Crovisier, J. 1998, Faraday Discussions, 109, 437
Crimier, N., Ceccarelli, C., Maret, S., et al. 2010, A&A, 519, A65



de Graauw, T., Helmich, F. P., Phillips, T. G., et al. 2010, A&A,
518, L6
Dzib, S. A., Ortiz-Le´on, G. N., Hern´andez-G´omez, A., et al. 2018,

arXiv:1802.03234

Fedoseev, G., Ioppolo, S., Zhao, D., Lamberts, T., & Linnartz, H.
2015, MNRAS, 446, 439
Fusina, L., & Mills, I. M. 1981, Journal of Molecular Spectroscopy,
86, 488
Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ,
682, 283-302
Green, S. 1986, NASA Technical Memorandum 87791
Guan Y., Fleißner R., Joyce P., Krone S. M., 2006, Stat Comput,16, 193
Hastings W. K., 1970, Biometrika, 57, 97
Harju J., et al., 2017, ApJ, 840, 63
Helmich, F. P., & van Dishoeck, E. F. 1997, A&AS, 124, 205
Hern´andez-G´omez A., Caux E., Loinard L., et al. 2018, submitted
Heyminck, S., Kasemann, C., G¨usten, R., de Lange, G., & Graf,
U. U. 2006, A&A, 454, L21
Hincelin, U., Wakelam, V., Hersant, F., et al. 2011, A&A, 530,
A61

W. H. Hocking, M. C. L. Gerry, and G. Winnewisser, 1975, Can.
J. Phys. 53, 1869
Hunter, S. D., Digel, S. W., de Geus, E. J., & Kanbach, G. 1994,
ApJ, 436, 216
Iglesias, E. 1977, ApJ, 218, 697
Jackson, J. M., Armstrong, J. T., & Barrett, A. H. 1984, ApJ,
280, 608
Jacobsen, S. K., Jørgensen, J. K., van der Wiel, M. H. D., et al.
2018, A&A, 612, A72
Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016,
A&A, 595, A117
S. G. Kukolich, A. C. Nelson, and B. S. Yamanashi, 1971, J. Am.
Chem. Soc. 93, 6769
Lapinov, G. Yu. Golubiatnikov, V. N. Markov, and A. Guarnieri,
2007, Astron. Lett. 33,121
Lis, D. C., Keene, J., Young, K., et al. 1997, Icarus, 130, 355
L´opez-Sepulcre, A., Jaber, A. A., Mendoza, E., et al. 2015, MNRAS, 449, 2438
MacDonald, G. H., Gibb, A. G., Habing, R. J., & Millar, T. J.
1996, A&AS, 119, 333
Majumdar, L., Gratier, P., Vidal, T., et al. 2016, MNRAS, 458,

1859

Majumdar, L., Gratier, P., Andron, I., Wakelam, V., & Caux, E.
2017, MNRAS, 467, 3525
Majumdar, L., Gratier, P., Wakelam, V., et al. 2018, MNRAS,
477, 525
J.G. Mangum and A. Wootten, 1993, ApJS, 89, 123.
J.G. Mangum and Y.L. Shirley, 2015, PASP, 127, 266.
Marcelino, N., Cernicharo, J., Tercero, B., & Roueff, E. 2009,
ApJ, 690, L27
Marcelino, N., Br¨unken, S., Cernicharo, J., et al. 2010, A&A, 516,
A105

Mart´ın, S., Mauersberger, R., Mart´ın-Pintado, J., Henkel, C., &
Garc´ıa-Burillo, S. 2006, ApJS, 164, 450
Mart´ın-Dom´enech, R., Rivilla, V. M., Jim´enez-Serra, I., et al.
2017, MNRAS, 469, 2230
Mart´ın, S., Requena-Torres, M. A., Mart´ın-Pintado, J., &
Mauersberger, R. 2008, ApJ, 678, 245
Mart´ın, S., Mart´ın-Pintado, J., & Mauersberger, R. 2009, ApJ,
694, 610
Meier, D. S., & Turner, J. L. 2005, ApJ, 618, 259
Menten, K. M., Serabyn, E., Guesten, R., & Wilson, T. L. 1987,
A&A, 177, L57
M¨uller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G.
2001, A&A, 370, L49
M¨uller, H. S. P., Schl¨oder, F., Stutzki, J., & Winnewisser, G.
2005, Journal of Molecular Structure, 742, 215


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 11



Mundy, L. G., Wootten, A., Wilking, B. A., Blake, G. A., & Sargent, A. I. 1992, ApJ, 385, 306
M. Niedenhoff, K. M. T. Yamada, S. P. Belov, and G. Winnewisser, 1995, J. Mol. Spectrosc. 174, 151
Nizam, M., Bouteiller, Y., Silvi, B., et al. 1988, Journal of Physics
C Solid State Physics, 21, 5351
Noble, J. A., Theule, P., Congiu, E., et al. 2015, A&A, 576, A91
Ott, S., 2010, Astronomical Data Analysis Software and Systems
XIX. Proceedings of a conference held October 4-8, 2009 in
Sapporo, Japan. Edited by Yoshihiko Mizumoto, Koh-Ichiro
Morita, and Masatoshi Ohishi. ASP Conference Series, Vol.
434, 139
Quan, D., Herbst, E., Osamura, Y., & Roueff, E. 2010, ApJ, 725,

2101

Qu´enard, D., Jim´enez-Serra, I., Viti, S., Holdship, J., & Coutens,
A. 2018, MNRAS, 474, 2796
Roelfsema, P. R., Helmich, F. P., Teyssier, D., et al. 2012, A&A,
537, A17
Rodr´ıguez-Fern´andez, N. J., Tafalla, M., Gueth, F., & Bachiller,
R. 2010, A&A, 516, A98
Ruaud, M., Loison, J. C., Hickson, K. M., et al. 2015, MNRAS,
447, 4004
Ruaud, M., Wakelam, V., & Hersant, F. 2016, MNRAS, 459, 3756
Sahnoun E., Wiesenfeld L., Hammami K., Jaidane N., 2018, The
Journal of Physical Chemistry A, 122, 3004
Snyder, L. E., & Buhl, D. 1972, ApJ, 177, 619
Tideswell, D. M., Fuller, G. A., Millar, T. J., & Markwick, A. J.
2010, A&A, 510, A85
Turner, B. E. 1991, ApJS, 76, 617
Turner, B. E. 2000, ApJ, 542, 837
van der Tak, F. F. S., Black, J. H., Sch¨oier, F. L., Jansen, D. J.,
& van Dishoeck, E. F. 2007, A&A, 468, 627
van Dishoeck, E. F., Blake, G. A., Jansen, D. J., & Groesbeck,
T. D. 1995, ApJ, 447, 760
Wakelam, V., Loison, J.-C., Herbst, E., et al. 2015, ApJS, 217, 20
Werner H., et al., 2012, University College Cardiff Consultants
Ltd.: Wales, UK
Wootten, A. 1989, ApJ, 337, 858
Yamada K., 1977, JMoSp, 68, 423


MNRAS **000**, 1–12 (2018)



**Table** **A1.** Detected HNCO transitions in all observations and

their main parameters. The negative sign for some transitions
detected with Herschel/HIFI indicate that the line could be
in absorption (after subtracting a baseline), although this is
within the noise. Columns are frequency, quantum numbers, upper level energy, Einstein A value, value and error of the velocityintegrated main-beam brightness temperature. Telescope used :

[87, 245] GHz : IRAM-30m, [260, 320] and [370, 470] GHz : APEX,

[328, 360] GHz : JCMT and [ _>_ 490] GHz : Herschel-HIFI.


Frequency Transition E up A i j ∫ T mb dv
(MHz) (J K a K c ) (K) (s [−][1] ) (K km s [−][1] )


87597.330 4 1 4 − 3 1 3 53.78 8.04×10 [−][6] 0.29(±0.05)
87898.425 4 2 3 − 3 2 2 180.83 6.28×10 [−][6] 0.18(±0.04)
87898.628 4 2 2 − 3 2 1 180.83 6.28×10 [−][6] 0.18(±0.04)
87925.237 4 0 4 − 3 0 3 10.54 8.78×10 [−][6] 0.82(±0.11)
88239.020 4 1 3 − 3 1 2 53.86 8.22×10 [−][6] 0.25(±0.13)
109495.996 5 1 5 − 4 1 4 59.04 1.65×10 [−][5] 0.46(±0.07)
109872.337 5 2 4 − 4 2 3 186.10 1.41×10 [−][5] 0.39(±0.05)
109872.765 5 2 3 − 4 2 2 186.10 1.41×10 [−][5] 0.39(±0.05)
109905.749 5 0 5 − 4 0 4 15.82 1.75×10 [−][5] 0.65(±0.04)
110298.089 5 1 4 − 4 1 3 59.15 1.68×10 [−][5] 0.38(±0.09)
131394.230 6 1 6 − 5 1 5 65.34 2.92×10 [−][5] 0.29(±0.05)
131845.890 6 2 5 − 5 2 4 192.43 2.61×10 [−][5] 0.34(±0.07)
131846.600 6 2 4 − 5 2 3 192.43 2.61×10 [−][5] 0.34(±0.07)
131885.734 6 0 6 − 5 0 5 22.15 3.08×10 [−][5] 1.12(±0.12)
132356.701 6 1 5 − 5 1 4 65.50 2.99×10 [−][5] 0.30(±0.07)
153291.935 7 1 7 − 6 1 6 72.70 4.73×10 [−][5] 0.55(±0.16)
153818.880 7 2 6 − 6 2 5 199.81 4.33×10 [−][5] 0.10(±0.10)
153820.016 7 2 5 − 6 2 4 199.81 4.33×10 [−][5] 0.10(±0.10)
153865.086 7 0 7 − 6 0 6 29.53 4.94×10 [−][5] 1.27(±0.20)
154414.765 7 1 6 − 6 1 5 72.91 4.84×10 [−][5] 0.68(±0.24)
197085.416 9 1 9 − 8 1 8 90.57 1.03×10 [−][4] 0.80(±0.13)
197762.939 9 2 8 − 8 2 7 217.74 9.66×10 [−][5] 0.89(±0.43)
197765.372 9 2 7 − 8 2 6 217.74 9.66×10 [−][5] 0.89(±0.43)
197821.461 9 0 9 − 8 0 8 47.47 1.07×10 [−][4] 2.23(±0.32)
198528.881 9 1 8 − 8 1 7 90.91 1.05×10 [−][4] 0.18(±0.03)
218981.009 10 1 10 − 9 1 9 101.07 1.42×10 [−][4] 0.78(±0.07)
219733.850 10 2 9 − 9 2 8 228.29 1.35×10 [−][4] 1.33(±0.33)
219737.193 10 2 8 − 9 2 7 228.29 1.35×10 [−][4] 1.33(±0.33)
219798.274 10 0 10 − 9 0 9 58.01 1.47×10 [−][4] 2.32(±0.10)
220584.751 10 1 9 − 9 1 8 101.50 1.45×10 [−][4] 0.74(±0.14)
240875.727 11 1 11 − 10 1 10 112.63 1.90×10 [−][4] 1.53(±0.20)
241703.853 11 2 10 − 10 2 9 239.89 1.81×10 [−][4] 0.64(±0.20)
241708.312 11 2 9 − 10 2 8 239.89 1.81×10 [−][4] 0.64(±0.20)
241774.032 11 0 11 − 10 0 10 69.62 1.96×10 [−][4] 2.67(±0.23)
242639.704 11 1 10 − 10 1 9 113.14 1.95×10 [−][4] 2.25(±0.31)
262769.477 12 1 12 − 11 1 11 125.25 2.48×10 [−][4] 0.75(±0.18)
263672.912 12 2 11 − 11 2 10 252.54 2.37×10 [−][4] 1.32(±0.51)
263678.709 12 2 10 − 11 2 9 252.54 2.37×10 [−][4] 1.32(±0.51)
263748.625 12 0 12 − 11 0 11 82.28 2.56×10 [−][4] 0.70(±0.07)
264693.655 12 1 11 − 11 1 10 125.85 2.54×10 [−][4] 0.21(±0.06)
284662.172 13 1 13 − 12 1 12 138.91 3.17×10 [−][4] 0.38(±0.08)
285721.951 13 0 13 − 12 0 12 95.99 3.26×10 [−][4] 0.76(±0.09)
286746.514 13 1 12 − 12 1 11 139.61 3.24×10 [−][4] 0.29(±0.11)


**APPENDIX** **A:** **OBSERVED** **HNCO**

**TRANSITIONS** **PARAMETERS**


In this section, we give the parameters of all the HNCO
observed lines.

12 _Hern´andez-G´omez_ _et_ _al._


**Table** **A1** – _continued_


Frequency Transition E up A i j ∫ T mb dv
(MHz) (J K a K c ) (K) (s [−][1] ) (K km s [−][1] )


306553.733 14 1 14 − 13 1 13 153.62 3.97×10 [−][4] 0.42(±0.09)
307693.905 14 0 14 − 13 0 13 110.76 4.09×10 [−][4] 1.08(±0.20)
308798.184 14 1 13 − 13 1 12 154.43 4.06×10 [−][4] 0.72(±0.15)
328444.054 15 1 15 − 14 1 14 169.38 4.90×10 [−][4] 0.68(±0.21)
329664.367 15 0 15 − 14 0 14 126.58 5.04×10 [−][4] 1.79(±0.19)
330848.569 15 1 14 − 14 1 13 170.31 5.01×10 [−][4] 1.63(±0.40)
350333.059 16 1 16 − 15 1 15 186.20 5.97×10 [−][4] 1.01(±0.06)
351633.257 16 0 16 − 15 0 15 143.45 6.13×10 [−][4] 1.63(±0.12)
352897.581 16 1 15 − 15 1 14 187.24 6.10×10 [−][4] 0.88(±0.09)
372220.660 17 1 17 − 16 1 16 204.06 7.17×10 [−][4] 0.56(±0.10)
373600.448 17 0 17 − 16 0 16 161.38 7.36×10 [−][4] 1.64(±0.24)
417529.351 19 0 19 − 18 0 18 200.41 1.03×10 [−][3] 1.37(±0.12)
419035.477 19 1 18 − 18 1 17 244.41 1.03×10 [−][3] 1.08(±0.15)
461450.213 21 0 21 − 20 0 20 243.65 1.39×10 [−][3] 1.54(±0.22)
493675.710 17 1 17 − 18 0 18 204.06 6.30×10 [−][4] 0.40(±0.06)
517020.943 16 1 16 − 17 0 17 186.20 7.21×10 [−][4] -0.01(±0.001)
540288.323 15 1 15 − 16 0 16 169.38 8.21×10 [−][4] -0.01(±0.002)
563477.534 14 1 14 − 15 0 15 153.62 9.29×10 [−][4] 0.05(±0.02)
586588.183 13 1 13 − 14 0 14 138.91 1.04×10 [−][3] -0.06(±0.01)
609619.927 12 1 12 − 13 0 13 125.25 1.17×10 [−][3] 0.05(±0.01)
632572.365 11 1 11 − 12 0 12 112.63 1.30×10 [−][3] 0.16(±0.04)
655445.310 10 1 10 − 11 0 11 101.07 1.44×10 [−][3] -0.01(±0.004)
678238.267 9 1 9 − 10 0 10 90.57 1.58×10 [−][3] -0.004(±0.01)
700951.182 8 1 8 − 9 0 9 81.11 1.74×10 [−][3] -0.03(±0.01)
723583.635 7 1 7 − 8 0 8 72.70 1.89×10 [−][3] 0.01(±0.01)
746135.382 6 1 6 − 7 0 7 65.34 2.05×10 [−][3] -0.04 (±0.01)
768606.238 5 1 5 − 6 0 6 59.04 2.21×10 [−][3] -0.01(±0.01)
790995.975 4 1 4 − 5 0 5 53.78 2.35×10 [−][3] -0.08(±0.03)
813304.397 3 1 3 − 4 0 4 49.58 2.47×10 [−][3] -0.06(±0.01)
835531.328 2 1 2 − 3 0 3 46.42 2.49×10 [−][3] -0.03(±0.003)
857676.609 1 1 1 − 2 0 2 44.32 2.25×10 [−][3] -0.04(±0.01)
901800.081 1 1 0 − 1 0 1 44.33 7.84×10 [−][3] -0.09(±0.01)
901956.917 2 1 1 − 2 0 2 46.45 7.84×10 [−][3] -0.03(±0.01)
902192.207 3 1 2 − 3 0 3 49.62 7.84×10 [−][3] -0.08(±0.01)
902505.994 4 1 3 − 4 0 4 53.86 7.85×10 [−][3] -0.07(±0.01)
902898.335 5 1 4 − 5 0 5 59.15 7.86×10 [−][3] -0.05(±0.01)
903369.302 6 1 5 − 6 0 6 65.50 7.87×10 [−][3] -0.09(±0.01)
903918.982 7 1 6 − 7 0 7 72.91 7.88×10 [−][3] 0.04(±0.01)
904547.473 8 1 7 − 8 0 8 81.38 7.89×10 [−][3] -0.01(±0.004)
905254.892 9 1 8 − 9 0 9 90.91 7.91×10 [−][3] 0.04(±0.01)
906041.367 10 1 9 − 10 0 10 101.50 7.93×10 [−][3] -0.03(±0.002)
906907.042 11 1 10 − 11 0 11 113.14 7.95×10 [−][3] 0.06(±0.01)
907852.072 12 1 11 − 12 0 12 125.85 7.97×10 [−][3] -0.004(±0.003)
908876.631 13 1 12 − 13 0 13 139.61 7.99×10 [−][3] 0.04(±0.004)
909980.904 14 1 13 − 14 0 14 154.43 8.01×10 [−][3] -0.05(±0.010)
911165.091 15 1 14 − 15 0 15 170.31 8.04×10 [−][3] -0.007(±0.002)
912429.407 16 1 15 − 16 0 16 187.24 8.07×10 [−][3] -0.02(±0.003)
913774.079 17 1 16 − 17 0 17 205.24 8.10×10 [−][3] 0.01(±0.003)
923621.180 1 1 1 − 0 0 0 44.32 5.61×10 [−][3] -0.07(±0.01)
945438.685 2 1 2 − 1 0 1 46.42 5.42×10 [−][3] -0.05(±0.003)
967173.925 3 1 3 − 2 0 2 49.58 5.52×10 [−][3] -0.06(±0.01)
988826.956 4 1 4 − 3 0 3 53.78 5.74×10 [−][3] -0.05(±0.01)
1010397.720 5 1 5 − 4 0 4 59.04 6.01×10 [−][3] -0.02(±0.007)
1031886.200 6 1 6 − 5 0 5 65.34 6.32×10 [−][3] -0.06(±0.001)
1053292.425 7 1 7 − 6 0 6 72.70 6.66×10 [−][3] -0.08(±0.01)
1074616.365 8 1 8 − 7 0 7 81.11 7.03×10 [−][3] -0.17(±0.01)
1095858.058 9 1 9 − 8 0 8 90.57 7.41×10 [−][3] -0.07(±0.01)
1117017.603 10 1 10 − 9 0 9 101.07 7.81×10 [−][3] -0.14(±0.01)
1138095.052 11 1 11 − 10 0 10 112.63 8.23×10 [−][3] 0.06(±0.03)
1159090.494 12 1 12 − 11 0 11 125.25 8.67×10 [−][3] -0.02(± − 0.003)
1180004.039 13 1 13 − 12 0 12 138.91 9.13×10 [−][3] 0.08(±0.02)



**APPENDIX** **B:** **OBSERVED** **AND** **MODELLED**

**HNCO** **TRANSITIONS**


In this section, we show all the HNCO observed line
profiles individually (in black) and the predicted emission/absorption profiles from our model described in Section 3 (in red). We have separated the observations by the
_K_ a quantum number. Some transitions (indicated in each
figure caption) could not be modelled since their collisional
rate coefficients were not computed in the quantum chemical
calculations of Sahnoun et al. (2018).


This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 13


**Figure** **B1.** HNCO K a = 0 transitions. The collision rate coefficient for the 21 0 21 − 20 0 20 transition was lacking and therefore it could
not be modelled.



Frequency (GHz)
87.921 87.924 87.927



Frequency (GHz)
109.900 109.904 109.908



Frequency (GHz)
131.879 131.883 131.888



0.30


0.19


0.08













0.89


0.49


0.10





0.60


0.40


0.20



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
153.857 153.863 153.868



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
197.811 197.818 197.825



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
219.787 219.795 219.802









0.76


0.52


0.29





0.85


0.66


0.47



1.05


0.81


0.57







-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
241.762 241.770 241.778



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
263.735 263.744 263.753



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
285.707 285.717 285.726



2.55


1.64


0.72







0.45


0.36


0.27







0.53


0.43


0.33







-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
307.678 307.689 307.699



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
329.648 329.659 329.670



-10 -5 0 5 10 15

Velocity (km/s)









Frequency (GHz)
351.616 351.627 351.639



1.06


0.85


0.64





0.58


0.49


0.40





1.06


0.94


0.82



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
373.581 373.594 373.607









Frequency (GHz)
417.508 417.522 417.536



Frequency (GHz)
461.427 461.442 461.458



0.95


0.82


0.68


-10 -5 0 5 10 15

Velocity (km/s)


MNRAS **000**, 1–12 (2018)



1.21


1.07


0.93



1.50


1.34


1.18



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)

14 _Hern´andez-G´omez_ _et_ _al._


**Figure** **B2.** HNCO K a = 1 transitions. The 19 1 18 − 18 1 17 transition could not be modelled due to the lack of its collisional rate coefficient.



Frequency (GHz)
87.593 87.596 87.599





Frequency (GHz)
88.234 88.237 88.240



Frequency (GHz)
109.490 109.494 109.498







0.12


0.10


0.08



0.23


0.17


0.12







0.13


0.11


0.09



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
110.293 110.296 110.300



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)









Frequency (GHz)
131.387 131.392 131.397



Frequency (GHz)
132.350 132.355 132.359



0.24


0.18


0.13





0.26


0.23


0.20



0.27


0.24


0.21



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
153.285 153.290 153.294



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
154.407 154.412 154.417



-10 -5 0 5 10 15

Velocity (km/s)









0.38


0.31


0.24



Frequency (GHz)
197.076 197.082 197.089





0.37


0.31


0.25





0.59


0.53


0.47



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
198.519 198.526 198.532









Frequency (GHz)
218.970 218.977 218.985



Frequency (GHz)
220.573 220.581 220.588



0.59


0.53


0.47



0.75


0.66


0.56



0.74


0.65


0.56



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
240.863 240.872 240.880









Frequency (GHz)
242.627 242.636 242.644



0.37


0.32


0.26



Frequency (GHz)
262.756 262.765 262.774



0.95


0.83


0.70



0.94


0.82


0.70



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
264.681 264.689 264.698







Frequency (GHz)
284.648 284.657 284.667



Frequency (GHz)
286.732 286.742 286.751

0.45


0.41


0.37


0.33





0.36


0.32


0.27



0.42


0.38


0.33



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 15


**Figure** **B2** – _continued_



Frequency (GHz)
306.538 306.549 306.559







Frequency (GHz)
328.428 328.439 328.450





Frequency (GHz)
308.783 308.793 308.803



0.89


0.75


0.62





0.51


0.45


0.39



0.56


0.49


0.42



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
350.316 350.327 350.339



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
330.832 330.843 330.854







1.04


0.97


0.89


0.81





Frequency (GHz)
352.880 352.892 352.904


1.09


1.00


0.91


0.82





0.87


0.78


0.68



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
493.651 493.668 493.684



Frequency (GHz)
372.202 372.214 372.227

0.94


0.86


0.78


0.70



1.17


1.05


0.93









Frequency (GHz)
419.015 419.028 419.042



2.61


2.02


1.42





-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
516.995 517.012 517.030









Frequency (GHz)
540.261 540.279 540.297



Frequency (GHz)
563.449 563.468 563.487



0.29


0.25


0.22



0.22


0.19


0.17



0.26


0.23


0.20



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
609.589 609.610 609.630



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
586.559 586.578 586.598







0.36


0.33


0.31


0.28





Frequency (GHz)
632.541 632.562 632.583

0.40


0.37


0.34


0.30





0.31


0.28


0.25



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
655.412 655.434 655.456

0.45









Frequency (GHz)
678.204 678.227 678.249



Frequency (GHz)
700.916 700.939 700.963



0.41


0.37


0.33


-10 -5 0 5 10 15

Velocity (km/s)


MNRAS **000**, 1–12 (2018)



0.46


0.41


0.36



0.48


0.43


0.38



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)

16 _Hern´andez-G´omez_ _et_ _al._


Frequency (GHz)
723.548 723.572 723.596









**Figure** **B2** – _continued_


Frequency (GHz)
746.098 746.123 746.148



Frequency (GHz)
768.568 768.593 768.619

0.65


0.60


0.54


0.48





0.55


0.48


0.41



0.57


0.50


0.42



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
835.490 835.517 835.545



Frequency (GHz)
790.957 790.983 791.009









Frequency (GHz)
813.264 813.291 813.318



0.81


0.74


0.68


0.61





0.67


0.58


0.50



0.68


0.61


0.53



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
857.634 857.662 857.691









Frequency (GHz)
901.755 901.785 901.815



Frequency (GHz)
901.912 901.942 901.972



0.85


0.75


0.65



0.78


0.70


0.62



0.86


0.77


0.68



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
902.461 902.491 902.521



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
902.147 902.177 902.207







0.93


0.81


0.69





0.91


0.84


0.77


0.70





Frequency (GHz)
902.853 902.883 902.913



0.85


0.76


0.66



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
904.502 904.533 904.563



Frequency (GHz)
903.324 903.354 903.384







Frequency (GHz)
903.874 903.904 903.934


0.93


0.86


0.78


0.71





0.93


0.86


0.79


0.72





0.88


0.78


0.68



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
905.209 905.240 905.270





Frequency (GHz)
905.996 906.026 906.056

0.94


0.87


0.79


0.71





Frequency (GHz)
906.861 906.892 906.922

0.96


0.87


0.79


0.70





0.89


0.78


0.68



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


MNRAS **000**, 1–12 (2018)

_Modelling_ _the_ _abundance_ _structure_ _of_ _HNCO_ _toward_ _IRAS_ _16293_ − _2422_ 17


**Figure** **B2** – _continued_



Frequency (GHz)
907.807 907.837 907.867


0.93


0.85


0.78


0.70



0.91


0.81


0.72







Frequency (GHz)
908.831 908.861 908.892


0.96


0.88


0.80


0.72





Frequency (GHz)
909.936 909.966 909.996



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
911.120 911.150 911.180

0.96


0.88


0.79


0.71



0.87


0.78


0.68







Frequency (GHz)
912.384 912.414 912.445


0.93


0.86


0.78


0.71





Frequency (GHz)
913.729 913.759 913.789



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
923.575 923.606 923.637









Frequency (GHz)
945.391 945.423 945.454



Frequency (GHz)
967.126 967.158 967.190



0.90


0.81


0.72



1.01


0.88


0.75



1.02


0.90


0.78



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)



Frequency (GHz)
988.778 988.811 988.844





Frequency (GHz)
1010.347 1010.381 1010.415


1.08


0.95


0.82





Frequency (GHz)
1031.835 1031.869 1031.904


1.12


1.00


0.88





1.08


0.96


0.84



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
1053.240 1053.275 1053.310



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)





Frequency (GHz)
1074.563 1074.598 1074.634


1.25


1.09


0.93





Frequency (GHz)
1095.803 1095.840 1095.876


1.28


1.13


0.97





1.37


1.09


0.82





-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
1116.962 1116.999 1117.036



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
1138.038 1138.076 1138.114



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
1159.033 1159.071 1159.110









1.54


1.23


0.91



1.56


1.24


0.92







1.42





1.19


0.95


-10 -5 0 5 10 15

Velocity (km/s)


MNRAS **000**, 1–12 (2018)



-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)

18 _Hern´andez-G´omez_ _et_ _al._



**Figure** **B2** – _continued_


Frequency (GHz)
1179.945 1179.984 1180.024





1.64





1.27


0.89


-10 -5 0 5 10 15

Velocity (km/s)


**Figure** **B3.** HNCO K a = 2 transitions. In all cases, two transitions very close in frequency are always contained in the same line profile
(see Table 1). The transitions with J ≥ 9 were not modelled due to the lack of their corresponding collisional rate coefficients.



Frequency (GHz)
87.894 87.897 87.900



Frequency (GHz)
109.867 109.870 109.874









0.21


0.17


0.13



Frequency (GHz)
131.839 131.844 131.848





0.13


0.11


0.09





0.26


0.23


0.20





-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)









0.61


0.45


0.29





Frequency (GHz)
197.753 197.760 197.766



Frequency (GHz)
219.722 219.730 219.737



0.74


0.66


0.58


|-10 -5 0 5 10 15 Velocity (km/s) 812 153.817 153.822 Frequency (GHz)|Col2|
|---|---|
|IRAM<br>725 −624|IRAM<br>725 −624|
|||



-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
241.691 241.699 241.707



0.62


0.54


0.46


-10 -5 0 5 10 15

Velocity (km/s)


Frequency (GHz)
263.665 263.674 263.683







1.80


1.26


0.71





0.46


0.35


0.23



-10 -5 0 5 10 15

Velocity (km/s)


MNRAS **000**, 1–12 (2018)





-10 -5 0 5 10 15

Velocity (km/s)



-10 -5 0 5 10 15

Velocity (km/s)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Identify HNCO transitions in all datasets using CASSIS and CDMS",
  "failed_quote": "To identify and model the relevant HNCO spectral lines, we\nused CASSIS (Caux et al. 2011)"
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "Line identification and RADEX MCMC modelling",
  "failed_quote": "we\nused CASSIS (Caux et al. 2011), a software developed at\nIRAP-UPS/CNRS"
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "MCMC chi2 minimisation; priors not stated",
  "failed_quote": "(no quote given)"
 }
]
```
