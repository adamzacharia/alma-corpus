# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...909...12G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
D RAFT VERSION J ANUARY 13, 2021
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Systematic difference between ionized and molecular gas velocity dispersion in** _z_ _∼_ 1 _−_ 2 **disks and local analogues**


M. G [IRARD](http://orcid.org/0000-0002-8583-2521), [1, 2] D. B. [F](http://orcid.org/0000-0003-0645-5260) ISHER, [1, 2] A. D. B OLATTO, [3] R. A [BRAHAM](http://orcid.org/0000-0002-4542-921X), [4] R. B [ASSETT](http://orcid.org/0000-0001-9760-7519), [1, 2] K. G [LAZEBROOK](http://orcid.org/0000-0002-3254-9044), [1, 2] R. H [ERRERA](http://orcid.org/0000-0002-2775-0595) -C AMUS, [5]

E. J [IMENEZ](http://orcid.org/0000-0003-2517-4931) ´, [6, 2] L. L [ENKIC](http://orcid.org/0000-0003-4023-8657) ´, [3] AND D. O [BRESCHKOW](http://orcid.org/0000-0002-1527-0762) [6]


1 _Centre for Astrophysics and Supercomputing, Swinburne University of Technology, P.O. Box 218, Hawthorn, VIC 3122, Australia_
2 _ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Australia_
3 _University of Maryland 1113 PSC Bldg., 415 College Park, MD 20742-0001, USA_
4 _Department of Astronomy & Astrophysics, University of Toronto, 50 St._ _George Street, Toronto, ON M5S 3H4, Canada_
5 _Astronomy Department, Universidad de Concepci´on, Barrio Universitario, Concepci´on, Chile_
6 _International Centre for Radio Astronomy Research (ICRAR), M468, University of Western Australia, 35 Stirling Hwy., Crawley, WA 6009, Australia_


(Received xxx; Revised yyy; Accepted zzz)


ABSTRACT


We compare the molecular and ionized gas velocity dispersion of 9 nearby turbulent disks, analogues to highredshift galaxies, from the DYNAMO sample using new ALMA and GMOS/Gemini observations. We combine
our sample with 12 galaxies at _z_ _∼_ 0.5-2.5 from the literature. We find that the resolved velocity dispersion is
systematically lower by a factor 2 _._ 45 _±_ 0 _._ 38 for the molecular gas compared to the ionized gas, after correcting
for thermal broadening. This offset is constant within the galaxy disks and indicates the co-existence of a thin
molecular and thick ionized gas disks. This result has a direct impact on the Toomre _Q_ and pressure derived in
galaxies. We obtain pressures _∼_ 0 _._ 22 dex lower on average when using the molecular gas velocity dispersion,
_σ_ 0 _,mol_ . We find that _σ_ 0 _,mol_ increases with gas fraction and star formation rate. We also obtain an increase
with redshift and show that the EAGLE and FIRE simulations overall overestimate _σ_ 0 _,mol_ at high redshift. Our
results suggest that efforts to compare the kinematics of gas using ionized gas as a proxy for the total gas may
overestimate the velocity dispersion by a significant amount in galaxies at the peak of cosmic star formation.
When using the molecular gas as a tracer, our sample is not consistent with predictions from constant efficiency
star formation models, even when including transport as a source of turbulence. Feedback models with variable
star formation efficiency, _ϵ_ _ff_, and/or feedback efficiency, _p_ _∗_ _/m_ _∗_, better predict our observations.


_Keywords:_ galaxies: evolution – galaxies: kinematics and dynamics – galaxies: star formation



1. INTRODUCTION


The majority of the stellar mass in the Universe was built
up around _z_ _∼_ 2, when the cosmic star formation rate density reached its maximum (Madau & Dickinson 2014). Many
surveys have therefore targeted galaxies at this epoch to study
their morphology and kinematic properties to gain information on the processes driving galaxy evolution (e.g., Stott
et al. 2013; Wisnioski et al. 2015; Swinbank et al. 2017).
Important differences between local and high-redshift
galaxies have been reported from these surveys. The distant systems present a clumpy morphology (e.g. Elmegreen
& Elmegreen 2005; Genzel et al. 2011) and show a higher
gas fraction than local galaxies (e.g. Tacconi et al. 2013;


Corresponding author: Marianne Girard

[mgirard@swin.edu.au](mailto: mgirard@swin.edu.au)



Dessauges-Zavadsky et al. 2015). Moreover, most of the
_z_ _∼_ 1 _−_ 2 galaxies show rotating disks (e.g. F¨orster Schreiber
et al. 2009; Wisnioski et al. 2015; Stott et al. 2016), similarly
to local disk galaxies, but they also have a much higher velocity dispersion on average with values of _σ_ 0 _∼_ 50 km s _[−]_ [1]

(e.g. Johnson et al. 2018; Girard et al. 2018b; Ubler [¨] et al.
2019). This high velocity dispersion has been interpreted as
turbulence in the disk of galaxies and could possibly be the
result of star formation feedback (e.g. Lehnert et al. 2009;
Green et al. 2010). Gravitational instabilities in the disk of
gas-rich galaxies could also play a major role (e.g. Bournaud
et al. 2010; Ceverino et al. 2010). White et al. (2017) found
a relationship between the kinematic properties and gas fraction of galaxies consistent with predictions from the Toomre
disk instability theory ( _Q_ _∼_ 1). Fisher et al. (2017a) also
found that the clump properties in these turbulent disks are
in good agreement with this theory. Recent models combin

2 G IRARD ET AL .



ing stellar feedback and gravitational instabilities have also
successfully predicted the relation between the velocity dispersion and star formation rate at this epoch (Krumholz et al.
2018; Ubler et al. 2019 [¨] ).
Most of these studies used strong emission lines, which
trace the ionized gas, to obtain the galaxy kinematics. They,
therefore, assumed that this component shows similar kinematic properties to the molecular gas, more difficult to detect
in distant galaxies. It is now possible to resolve the CO emission and obtain the molecular gas kinematics in some galaxies at _z_ _>_ 1 with ALMA, often with the help of gravitational
lensing (e.g., Swinbank et al. 2011; Barro et al. 2017; Calistro
Rivera & Hodge 2018; Ubler et al. 2018 [¨] ; Girard et al. 2019;
Molina et al. 2019). The molecular and ionized gas kinematics have been compared in only a few objects. Ubler [¨] et al.
(2018) reported a galaxy at _z_ _∼_ 1 _._ 4 with similar velocity
dispersion for the molecular and ionized gas ( _σ_ 0 _∼_ 15 _−_ 30
km s _[−]_ [1] ). Girard et al. (2019) also found similar velocity dispersions for one galaxy at _z_ _∼_ 1 ( _σ_ 0 _∼_ 19 km s _[−]_ [1] ), but they
also obtained a discrepancy for a spiral galaxy at _z_ _∼_ 1 with
a lower molecular velocity dispersion ( _σ_ 0 _,mol_ _∼_ 11 km s _[−]_ [1]

and _σ_ 0 _,ion_ _∼_ 54 km s _[−]_ [1] ). More observations are needed to
establish the relation between the molecular and ionized gas
velocity dispersion at _z_ _∼_ 1 _−_ 2.
In this work, we use DYNAMO (Green et al. 2014; Fisher
et al. 2017a), a sample of rare nearby galaxies at 0 _._ 075 _< z_ _<_
0 _._ 2 showing similar physical properties to _z_ _∼_ 1 _−_ 2 main
sequence galaxies, to probe the molecular and ionized gas
kinematics. By combining our new ALMA observations with
our GMOS/Gemini observations, we compare the molecular
and ionized gas velocity dispersion of 9 galaxies at a spatial
resolution of _∼_ 1 _._ 2 kpc.
The paper is organized as follows. Section 2 describes the
sample selection, observations and analysis. In Sect. 3 and 4,
we present our results and discussion on the relation between
the kinematics properties and other physical properties of the
galaxies. We finally present a summary in Sect. 5.
In this paper, we adopt a Λ-CDM cosmology with _H_ 0 =
67 km s _[−]_ [1] Mpc _[−]_ [1], Ω _M_ = 0 _._ 31, and Ω Λ = 0 _._ 69. We adopt
a Kroupa (2001) initial mass function (IMF) and convert to
this IMF when appropriate.


2. SAMPLE SELECTION, OBSERVATIONS AND

ANALYSIS


2.1. _Sample_


The original sample of 67 DYNAMO galaxies in Green
et al. (2010, 2014) includes a heterogenous mix of targets.
This sample has been down-selected to a sample of _∼_ 10
targets in which a wide range of properties are shown to
match with _z_ _≈_ 1 _._ 5 main-sequence galaxies. The subset



of these “ _z_ = 1 _._ 5 analogues” galaxies is presented in this
work and Fisher et al. (2017a, 2019). Our sample includes
galaxies at redshift 0 _._ 075 _<_ _z_ _<_ 0 _._ 2 with a stellar mass of
1 _×_ 10 [10] _<_ _M_ _⋆_ [ _M_ _⊙_ ] _<_ 9 _×_ 10 [10] and star formation rate
of 1 _<_ SFR [M _⊙_ yr _[−]_ [1] ] _<_ 60. These galaxies have therefore a similar specific star formation rate to main-sequence
galaxies at _z_ _∼_ 1 _−_ 2. They also have a high gas fraction
_f_ _gas_ _∼_ 0 _._ 1 _−_ 0 _._ 8 (Fisher et al. 2014; White et al. 2017; Fisher
et al. 2017a) and a clumpy morphology (Fisher et al. 2017b),
typical of galaxies at _z_ _∼_ 1 _−_ 2 (e.g. Tacconi et al. 2013;
Dessauges-Zavadsky et al. 2015; Tacconi et al. 2018). The
kinematic properties of the DYNAMO galaxies also present
similarities with high-redshift galaxies. DYNAMO galaxies show a rotating disk, but are also turbulent, with a high
ionized gas velocity dispersion _σ_ 0 _,ion_ _∼_ 20 _−_ 100 km s _[−]_ [1]

(Green et al. 2014; Bassett et al. 2014; Bekiaris et al. 2016;
Oliva-Altamirano et al. 2018). They also have a low angular
momentum (Obreschkow et al. 2015), as found for galaxies
with similar mass at _z_ _∼_ 1 _−_ 2 (Swinbank et al. 2017).
To study the molecular gas and ionized gas of the galaxies presented in this paper, we use ALMA observations for
all 9 galaxies and GMOS/Gemini observations for 7 galaxies
(Bassett et al. 2014) as well as SPIRAL/AAT observations
for the two other (Green et al. 2014).


2.2. _Observations_


ALMA observations were carried out in 2018 (project
2017.1.00239.S - PI: D. B. Fisher). The total on-source time
varies between 5 min and 22 min for the CO(3-2) line at a frequency of 290-310 GHz and between 20 min and 107 min for
the CO(4-3) line at a frequency of 390-420 GHz. The data
reduction was performed using the standard pipeline from
the ALMA facility. The final beam sizes are 0.8” _×_ 0.9” and
0.6” _×_ 0.75” (or 1.8 _×_ 2.0 kpc and 1.3 _×_ 1.7 kpc), and the spectral resolutions are _∼_ 15 km s _[−]_ [1] and _∼_ 11 km s _[−]_ [1] for the

CO(3-2) and CO(4-3) lines, respectively.
We also use in this work deep CO(3-2) data of the galaxies G04-1, G08-5, and G14-1 obtained in 2019 (project
#2019.1.00447.S - PI: R. Herrera-Camus). The total onsource time was between 83 and 94 min. Similarly to our
previous data, we use the standard pipeline from the ALMA
facility for the data reduction. The final beam size is about
0 _._ 37” _×_ 0 _._ 31” with a spectral resolution of _∼_ 8 km s _[−]_ [1] .

Observations from GMOS/Gemini were carried out in

2011-2012. The average seeing for these observations is
_∼_ 0 _._ 5 _[′′]_ and the spectral resolution is _σ_ = 24 km s _[−]_ [1] . The
physical distance resolution is _∼_ 1 _._ 1 kpc. For more details on
the observations and data reduction see Bassett et al. (2014).


2.3. _Measurements_


2.3.1. _Gas mass_

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 3


**Table 1.** Galaxy properties


Galaxy z _M_ _⋆_ SFR _f_ _gas_ _a_ _υ_ _rot,ion_ _b,c_ _υ_ _rot,mol_ _c_ _σ_ 0 _,ion_ _b_ _σ_ 0 _,mol_ Reference


[10 [10] _M_ _⊙_ ] [M _⊙_ yr _[−]_ [1] ] [km s _[−]_ [1] ] [km s _[−]_ [1] ] [km s _[−]_ [1] ] [km s _[−]_ [1] ]


C13-1 0.07876 3.58 5 _._ 1 _±_ 0 _._ 5 0 _._ 06 _±_ 0 _._ 02 223 234 26 _±_ 4 8 _±_ 2 This work

C22-2 0.07116 2.19 3 _._ 2 _±_ 0 _._ 2 0 _._ 18 _±_ 0 _._ 03 191 208 35.5 _±_ 5 9.5 _±_ 3 This work

D13-5 0.07535 5.38 17 _._ 5 _±_ 0 _._ 5 0 _._ 36 _±_ 0 _._ 02 175 190 39.5 _±_ 5 12 _±_ 3 This work

D15-3 0.06712 5.42 8 _._ 3 _±_ 0 _._ 4 0 _._ 17 _±_ 0 _._ 04 244 230 25 _±_ 5 8 _±_ 2 This work

G04-1 0.12981 6.47 21 _._ 3 _±_ 1 0 _._ 33 _±_ 0 _._ 04 274 248 30 _±_ 5 13 _±_ 3 This work

G08-5 0.13217 1.73 10 _._ 0 _±_ 1 0 _._ 30 _±_ 0 _._ 05 214 227 36 _±_ 7 15 _±_ 4 This work

G14-1 0.13233 2.23 6 _._ 9 _±_ 0 _._ 5 0 _._ 77 _±_ 0 _._ 08 149 160 71 _±_ 9 27 _±_ 5 This work

G20-2 0.14113 2.16 18 _._ 2 _±_ 0 _._ 4 0 _._ 21 _±_ 0 _._ 05 151 160 36 _±_ 5 9 _±_ 4 This work

SDSS 013527-1039 0.127 7.08 25 _._ 3 _±_ 2 _._ 5 0 _._ 33 _±_ 0 _._ 04 172 206 49 _±_ 7 12.5 _±_ 4 This work

SMM J2315-0102 2.32 2.01 268 0 _._ 88 _±_ 0 _._ 10 - 320 - 40 _±_ 10 Swinbank et al. (2011)

HLS115 1.58 2.63 120 _±_ 6 0 _._ 75 _±_ 0 _._ 15 218 - 80 _±_ 10 - Girard et al. (2018a)



Cosmic Snake 1.036 2.51 19 _±_ 6 0 _._ 29 _±_ 0 _._ 05 225 - 18.5 _±_ 7 19.5 _±_ 6



Patr´ıcio et al. (2018),
Girard et al. (2019)



Patr´ıcio et al. (2018),

A521 1.044 3.41 9 _._ 4 _±_ 3 _._ 0 - 130 - 54 _±_ 11 11 _±_ 8 Girard et al. (2019)


SHiZELS-19 1.486 2.12 13 _._ 8 _±_ 2.0 0 _._ 82 _±_ 0 _._ 16 106 121 107 _±_ 13 91 _±_ 6 Molina et al. (2019)
G3 ~~1~~ 0098 0.66 13.4 53 0 _._ 19 - - - 39 _._ 8 _±_ 15 _._ 6 PHIBSS _[d]_


G4 ~~2~~ 1351 0.73 8.45 85 0 _._ 32 - - - 19 _._ 5 _±_ 5 _._ 8 PHIBSS _[d]_



EGS ~~1~~ 3035123 1.12 16.8 85 0 _._ 32 - 193 - 20 _._ 4 _±_ 5 _._ 2 PHIBSS _[d]_


EGS ~~1~~ 2007881 1.17 5.33 106 0 _._ 54 - 220 - 22 _._ 9 _±_ 5 _._ 8 PHIBSS _[d]_


EGS ~~1~~ 3003805 1.23 16.9 212 0 _._ 48 - 384 - 30 _._ 2 _±_ 8 _._ 3 PHIBSS _[d]_


EGS4 ~~2~~ 4985 1.4 8.45 106 0 _._ 37 - - - 19 _._ 0 _±_ 7 _._ 0 PHIBSS _[d]_


EGS ~~1~~ 3011166 1.53 13.4 423 0 _._ 65 - 342 - 33 _._ 1 _±_ 7 _._ 6 PHIBSS _[d]_


N OTE —

_a_ Values from Fisher et al. (2017a), White et al. (2017) and Fisher et al. (2019) for the DYNAMO galaxies.
_b_ We do not have GMOS/Gemini data for C13-1 and D15-3. The ionized gas kinematic properties for these targets were taken from Bekiaris et al. (2016)
which used a very similar kinematic modeling method. Their data is however at lower resolution.
_c_ _−_ 1
Uncertainty on the rotation velocity of the ionized gas, _υ_ _rot,ion_, and molecular gas, _υ_ _rot,mol_, of the DYNAMO galaxies is _∼_ 15 km s .
_d_ The properties of the PHIBSS galaxies have been taken from Genzel et al. (2010),Tacconi et al. (2010, 2013), Freundlich et al. (2013), Genzel et al. (2015),
Tacconi et al. (2018), Ubler et al. [¨] (2018, 2019), and Freundlich et al. (2019).



The total gas mass and gas fraction of each galaxy were
derived in Fisher et al. (2014), White et al. (2017), and
Fisher et al. (2017a, 2019) using CO(1-0) observations from
Plateau de Bure. The molecular gas mass was obtained using
_M_ _mol_ = _α_ _CO_ _L_ _CO_ (1 _−_ 0), where _L_ _CO_ (1 _−_ 0) is the CO(1-0) luminosity and _α_ _CO_ is the CO-to-H 2 conversion factor of 4.36,
which includes a factor 1.36 for helium. We define the gas
fraction as _f_ _gas_ = _M_ _mol_ _/_ ( _M_ _mol_ + _M_ _⋆_ ) in this work.


2.3.2. _Star formation rate_


The star formation rates have also been derived in previous
DYNAMO papers using the H _α_ flux corrected for attenuation
(Green et al. 2017; Fisher et al. 2019), where SFR [M _⊙_ yr _[−]_ [1] ]
= 5 _._ 53 _×_ 10 _[−]_ [42] _L_ _Hα_ [erg s _[−]_ [1] ] (Hao et al. 2011). Values are
shown in Table 1 and assume a Kroupa IMF (Kroupa 2001).



2.3.3. _Kinematics_


We obtain the moment 1 and 2 maps from CO(3-2) and
CO(4-3) using the _immoments_ routine in CASA with a 3 _σ_
threshold parameter above the noise level. To obtain the kinematic maps from the ionized gas, we use the same method as
described in Bassett et al. (2014) and perform Gaussian fits
on H _α_ or H _β_ in individual spaxel to obtain the flux, velocity
and velocity dispersion maps. The instrumental broadening,
_σ_ _instr_ = 24 km s _[−]_ [1], was subtracted in quadrature to every
spaxel of the velocity dispersion maps. The kinematic maps
are shown in Figure 6.

4 G IRARD ET AL .


**Figure 1.** Velocity dispersion corrected for beam-smearing as a function of the distance from the kinematic center averaged in bins of 300 pc.
The H _α_ or H _β_ velocity dispersion profiles obtained from GMOS/Gemini observations are shown as blue triangles. The CO(4-3) and CO(3-2)
velocity dispersions obtained from ALMA observations are shown as dark orange circles and black squares, respectively. The dashed and dotted
horizontal lines indicate the intrinsic velocity dispersion obtained with GalPak [3D] for the molecular and ionized gas, respectively. Uncertainty
on the ionized and molecular gas velocity dispersion are 5-10 km s _[−]_ [1] and 3-5 km s _[−]_ [1], respectively, on average in each bin.

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 5



We model the galaxy kinematics using GalPaK [3D][ 1]

(Bouch´e et al. 2015), a 3D galaxy disk modeling code that
fits directly a model on the datacubes using a Markov-Chain
Monte Carlo method. The model is convolved with the pointspread function (PSF) and line-spread function (LSF). In this
way, the beam-smearing effect is directly taken into account
during the fitting. We adopt an arctan function to model the
velocity (Courteau 1997) and an exponential profile for the
radial flux profile. The disc inclinations are fixed using the
SDSS r-band photometry, similarly to Bekiaris et al. (2016).
This model assumes a constant velocity dispersion over the
galaxy disk. The galaxy center, disk half-light radius, the
flux, the position angle, the turnover radius, the maximum rotation velocity, and the intrinsic velocity dispersion are then
free to vary. We use both CO(3-2) and CO(4-3) datacubes
to model the molecular gas kinematics, except for C13-1 and
G08-5 for which only CO(3-2) was available and D15-3 for
which only CO(4-3) was available. We obtain similar velocity dispersion values for both CO transitions ( _±_ 2 km s _[−]_ [1] ).
For the ionized gas, we fit the H _β_ line, except for SDSS13527 for which we use H _α_ . Table 1 shows the intrinsic ve
locity dispersion, _σ_ 0, and the inclination-corrected rotation
velocity, _υ_ _rot_, obtained from GalPaK [3D] . No GMOS/Gemini
data were available for C13-1 and D15-3. For these two

galaxies, we take the values from Bekiaris et al. (2016) that
use a very similar modeling method with observations from
AAT (Green et al. 2014).
To obtain beam-smearing corrected velocity dispersion
profiles of each galaxy, we subtract in quadrature the unresolved velocity shear obtained from our models with
GalPak [3D] to the observed velocity dispersion map, already
corrected for instrumental broadening (Epinat et al. 2012;
Bassett et al. 2014; Green et al. 2014; Levy et al. 2018). This
correction affects mostly the central part of the profile, where
the velocity gradient is at its steepest. We note that adopting
a different beam-smearing correction could make the central
part of the dispersion profile flatter or steeper, but this would
not affect significantly the values in the disk. Fig. 1 presents
the velocity dispersion profiles of the 7 galaxies for which
both the ionized and molecular gas maps were available.
The intrinsic velocity dispersions obtained from
GalPaK [3D], also shown in Fig. 1, are in good agreement
with measurements taken on the major axis in the outer
region on the velocity dispersion maps, where the beamsmearing is known to be negligible (Burkert et al. 2016;
Johnson et al. 2018). The values are consistent at _±_ 3 km s _[−]_ [1]

and _±_ 5 km s _[−]_ [1] on average for the molecular and ionized
gas, respectively. Our ionized gas velocity dispersions are
also in good agreement ( _±_ 5 km s _[−]_ [1] ) with previous results


1 [http://www.ascl.net/1501.014](http://www.ascl.net/1501.014)



obtained for the ionized gas by Bassett et al. (2014) and
Bekiaris et al. (2016) using a very similar technique to model

the kinematics.


3. RESULTS AND DISCUSSION


In this section, we compare the molecular and ionized gas
velocity dispersion. We explore the correlations of the velocity dispersion with gas fraction and redshift.


3.1. _Difference between σ_ 0 _,ion_ _and σ_ 0 _,mol_ _and correlation_
_with gas fraction_


Table 1 shows the main kinematic properties obtained for
the ionized and molecular gas of the DYNAMO galaxies. We
find that the rotation velocity of the molecular gas is systematically higher than that of ionized gas with an average difference of 10-15 km s _[−]_ [1] . We do note that the uncertainty
in our measurement of the rotation velocity is _∼_ 15 km s _[−]_ [1] .

Nonetheless this offset is similar to what is found in local

spiral galaxies from the EDGE-CALIFA survey (Levy et al.
2018).
Fig. 1 presents the velocity dispersion profiles and the
intrinsic velocity dispersion values obtained from our kinematic models. We find that the dispersion profiles for both
the molecular and ionized gas are relatively flat in the galaxy
disks. We also see an increase in the center of the galaxies,
potentially due to the presence of a small bulge (Bassett et al.
2014).
We find that at all radii, in all galaxies the molecular gas
velocity dispersion is systematically lower than that of ionized gas, with _σ_ 0 _,mol_ _∼_ 8 _−_ 27 km s _[−]_ [1] and _σ_ 0 _,ion_ _∼_ 25 _−_
71 km s _[−]_ [1] for the molecular and ionized gas, respectively.
The ionized gas velocity dispersion is expected to be higher
due to thermal broadening and the expansion of HII regions.
These two effects together can account for _σ_ _th_ _∼_ 15 km s _[−]_ [1]

(Shields 1990; Krumholz & Burkhart 2016; Krumholz et al.
2018). After correcting in quadrature for this component, we
find that the ionized gas dispersion is still higher by a factor
2-3 compared to the molecular gas dispersion and that the
difference varies between 12-42 km s _[−]_ [1] in the sample. We
also find that the difference does not change within a galaxy
for radii outside the central region, meaning that there is no
correlation between the difference in velocity dispersion and
Σ _SF R_, Σ _mol_ and Σ _∗_ .
The gas disk thickness can be estimated using _σ_ 0 _/υ_ _rot_ _≈_
_H/R_, where _H_ is the height and _R_ is the radius of the disk
(Genzel et al. 2011; White et al. 2017). In DYNAMO galaxies, we find that _R_ 1 _/_ 2 _,H_ _α_ = (1 _._ 1 _±_ 0 _._ 2) _R_ 1 _/_ 2 _,CO_ . This suggests that the molecular gas disk of our DYNAMO sample
is thinner than the ionized gas disk since the radius of the
molecular and ionized gas disks are similar in these galaxies. Girard et al. (2019) also found the co-existence of a thin
molecular gas disk and thick ionized gas disk in lensed galax
ies at _z_ _∼_ 1.

6 G IRARD ET AL .


**Figure 2.** Intrinsic velocity dispersion, _σ_ 0, as a function of gas fraction, _f_ _gas_ and redshift, _z_ . The ionized gas velocity dispersion is corrected
for thermal broadening using _σ_ 0 _,ion_ - _th_ = ( _σ_ 0 [2] _,ion_ _[−]_ _[σ]_ _th_ [2] [)] [1] _[/]_ [2] [, where] _[ σ]_ _[th]_ [= 15][ km s] _[−]_ [1] [.] [The squares represent the DYNAMO galaxies from this]
work and from Fisher et al. (2019). We also present galaxies at _z_ _>_ 1 from Swinbank et al. (2011), Girard et al. (2018a), Molina et al. (2019),
and Girard et al. (2019) and the PHIBSS survey (Genzel et al. 2010; Tacconi et al. 2010, 2013; Freundlich et al. 2013; Genzel et al. 2015;
Tacconi et al. 2018; Ubler [¨] et al. 2018, 2019; Freundlich et al. 2019). We show local galaxies from the THINGS-HERACLES survey (Leroy
et al. 2008, 2009; Mogotsi et al. 2016), GHASP (Dunne et al. 2000; Leroy et al. 2005; Epinat et al. 2010; Torres-Flores et al. 2011) and nearby
galaxies at _z_ _∼_ 0 _._ 2 from Cortese et al. (2017). The molecular gas is represented in dark orange and the ionized gas in blue. The gas fractions
of all galaxies are computed assuming a conversion factor _α_ _co_ = 4 _._ 36. The blue and dark orange lines in the left panel represents a fit to the
data of log( _σ_ 0 )=0.87 _×f_ _gas_ + _b_ with _b_ = 1 _._ 29 and _b_ = 0 _._ 90 for the ionized and molecular gas, respectively. The black and light blue dashed
lines in the right panel represent results from the FIRE (Hung et al. 2019) and EAGLE simulations. The grey and light blue area encloses 68%
of the data of the simulated galaxies. The purple area indicates the results from TNG50 (Pillepich et al. 2019). The upper and lower limits are
the values for 10.5 _<_ log( _M_ _⋆_ / _M_ _⊙_ ) _<_ 11.0 and 10.0 _<_ log( _M_ _⋆_ / _M_ _⊙_ ) _<_ 10.5 without a thermal contribution.



Fig. 2 (left panel) shows that the ratio between the ionised
and molecular velocity dispersion is nearly constant across
a large range in gas fractions. The ionized velocity dispersions presented in this plot have been corrected in quadrature for the thermal broadening and HII regions expansion
( _σ_ _th_ _∼_ 15 km s _[−]_ [1] ). We also plot DYNAMO galaxies
from Fisher et al. (2019), samples of local galaxies from
THINGS-HERACLES (Leroy et al. 2008, 2009; Mogotsi
et al. 2016), GHASP (Dunne et al. 2000; Leroy et al. 2005;
Epinat et al. 2010; Torres-Flores et al. 2011), nearby galaxies
from Cortese et al. (2017), and high-redshift galaxies from
lensed studies (Swinbank et al. 2011; Girard et al. 2018a,
2019), from Molina et al. (2019), and from PHIBSS (Genzel
et al. 2010; Tacconi et al. 2010, 2013; Freundlich et al. 2013;
Genzel et al. 2015; Tacconi et al. 2018; Ubler [¨] et al. 2018,
2019; Freundlich et al. 2019).
The gas fraction for all the galaxies was computed using
the Galactic CO-H 2 conversion factor _α_ _co_ = 4 _._ 36, except
for the PHIBSS sample where they also corrected _α_ _CO_ for
metallicity by adopting the geometric mean of the prescrip


tions presented in Bolatto et al. (2013) and Genzel et al.
(2012). However, the metallicity in massive galaxies at
_z_ _∼_ 1 _−_ 2 is not low enough (estimated to _>_ 0 _._ 8 times the
solar value for these galaxies) to have a significant effect on
_α_ _CO_ (Tacconi et al. 2013, 2020). On the other hand, the
galaxies with a high baryonic surface density could possibly
have a lower conversion factor (Narayanan et al. 2012; Bolatto et al. 2013), but the relation we present here shows a relatively constant offset between the velocity dispersion, which
would be unaffected by the conversion factor. The choice of
the conversion factor _α_ _CO_ here is therefore not critical.
We obtain a strong correlation between the molecular velocity dispersion and gas fraction with a Spearman rank correlation coefficient of 0.76. The increase of the velocity dispersion with gas fraction is observed for both the ionized and
molecular gas and agrees with the picture of more turbulent,
gas-rich galaxies at high-redshift (e.g., Tacconi et al. 2013;
Wisnioski et al. 2015; Johnson et al. 2018). When fitting the
whole sample, we obtain a fit of log( _σ_ 0 /km s _[−]_ [1] ) = _a×f_ _gas_ + _b_
with _a_ = 0 _._ 98 _±_ 0 _._ 17 and _a_ = 0 _._ 76 _±_ 0 _._ 11 for the molecu

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 7



lar and ionised gas, respectively, and _a_ = 0 _._ 87 _±_ 0 _._ 13 when
combining both molecular and ionized gas values. We fit the
same relation with a fixed slope of _a_ = 0 _._ 87 on both gas
component separately and obtain



_σ_ 0 _,mol_
log = 0 _._ 87 _× f_ _gas_ + (0 _._ 90 _±_ 0 _._ 03) (1)
� km s _[−]_ [1] �



for the molecular gas, and



_σ_ 0 _,ion_   - _th_
log = 0 _._ 87 _× f_ _gas_ + (1 _._ 29 _±_ 0 _._ 03) (2)
� km s _[−]_ [1] �



sition. We also show the results for the H _β_ line using the
same method for comparison in Fig. 3.
Another possible explanation could be that multiple components are present in the ionized gas. If we interpret the
molecular gas as being representative of a narrow component to the gas emission this implies that there is a secondary
component heating the ionized gas. There is evidence for
this in the literature. Ho et al. (2014) carried out multi Gaus
_∼_
sian fits to spiral galaxies with R 5000 spectra. They found
that second components with _σ_ _∼_ 40 km s _[−]_ [1] are common.
Based on line ratios they argued that the ionized gas is heated
by both shocks and photoionization. We cannot say from our
data if the wider H _β_ profiles have similar lines ratios in DYNAMO galaxies, though we note the dispersion is similar.
More work at high spectral resolution is needed to determine
the nature of the wide emission lines in DYNAMO galaxies.

Hollenbach & McKee (1980) also argued that the presence
of fast shocks with _υ_ _shock_ _>_ 25 km s _[−]_ [1] could dissociate the
H 2 molecules (or _υ_ _shock_ _>_ 50 km s _[−]_ [1] in low density environment). This could leave a highly turbulent gas component
that is not traced by the molecular gas. Wong & Blitz (2002)
suggested that the formation of the molecular gas could be
limited to the midplane only due to low pressure or low dust
abundance outside this region. Clearly, more studies on the
molecular gas kinematics in the limit of high gas surface densities, similar to DYNAMO and high-redshift galaxies, are
needed to establish the nature of this important difference.


3.2. _Redshift evolution of σ_ 0 _,mol_


Fig. 2 (right panel) shows the molecular gas velocity dispersion as a function of redshift for the same sample presented in the left panel. We find that the molecular gas velocity dispersion is higher in high-redshift galaxies, similarly to

¨Ubler et al. (2019).
We compare our observations to the results from three
different simulations: FIRE (Hung et al. 2019), TNG50
(Pillepich et al. 2019), and EAGLE (Jimenez et al. in prep).
The grey area shows the results from the FIRE simulation,
presented in Table 1 of Hung et al. (2019), and encloses 68%
of their data. They studied only star-forming galaxies and
defined the velocity dispersion as the minimum value across
10 [4] viewing angles (equivalent to a face-on viewing angle
for disk galaxies) of the SFR-weighted standard deviation of
the velocity distribution of the gas particles. The blue area
encloses 68% of the data of the EAGLE simulation. EA
GLE includes both star-forming and quenched galaxies with
log( _M_ _⋆_ / _M_ _⊙_ ) _>_ 9. In this simulation, the velocity dispersion
is defined as the mass-weighted vertical velocity dispersion
of the star-forming gas, without any thermal contribution.
We use measurements without a thermal component since
we compare to cold molecular gas observations. Finally, we
show in purple the velocity dispersion from TNG50 (Fig. 12



for the ionized gas (corrected for the thermal broadening).
We find a zero offset between the molecular and ionized gas
velocity dispersion of 0 _._ 39 _±_ 0 _._ 06 dex, which is equivalent to
a factor 2 _._ 45 _±_ 0 _._ 38.
We also find a mean value of _σ_ 0 _,ion_ - _th_ _/σ_ 0 _,mol_ = 2 _._ 44 _±_
1 _._ 01 when combining all the galaxies of this sample for
which both ionised and molecular gas velocity dispersion are
available. This includes galaxies with 0 _._ 06 _<_ _f_ _gas_ _<_ 0 _._ 82
and 0 _._ 8 _<_ SFR [M _⊙_ yr _[−]_ [1] ] _<_ 25 from DYNAMO, Cortese
et al. (2017), Girard et al. (2019) and Molina et al. (2019). We
find that _σ_ 0 _,ion_ - _th_ _/σ_ 0 _,mol_ does not correlate with gas fraction
(Spearman coefficient of 0.10) and star formation rate (Spearman coefficient of 0.22).

Cald´u-Primo et al. (2013) suggested that deep data are necessary to trace a broader component of the molecular gas velocity dispersion. In Fig. 3 we carry out a similar experiment
on DYNAMO galaxies, but find this does not account for the
difference between ionized and molecular gas dispersions.
We use deep ALMA CO(3-2) data of the galaxies G04-1,
G08-5 and G14-1 obtained in 2019 (PI: R. Herrera-Camus) to
compare with the shallower data. To trace a potential broader
component, we average spectra from the outer regions of the
galaxies for our deep and shallow data (similar method to
Ianjamasimanana et al. 2012). To take account of the different velocities in each spaxel, we use the first moment to
shift each spectrum to the same velocity. After stacking, we
perform a Gaussian fit to the two final spectra to determine
the velocity dispersion. Using the Bayesian information criterion (BIC), we also find that a single Gaussian fits is more
adequate than a two Gaussian component for these spectra
(difference of BIC higher than 10). The deep CO stacked
data does not show a broader component compared to the
shallower stacked CO data, which is different than what is
found in local spirals. This suggests that our sample of turbulent, gas-rich galaxies do not have an additional thicker
molecular gas disk. We note however that the galaxy sample
in Cald´u-Primo et al. (2013) is different. They targeted local
spirals from THINGS, which have a primary velocity dispersion of 5-10 km s _[−]_ [1] and a broad secondary component of
_∼_ 10-20 km s _[−]_ [1] . The broad component of the THINGS sample is closer to the main component of what we measure in
DYNAMO. They also observe the CO(2-1) or CO(1-0) tran

8 G IRARD ET AL .


**Figure 3.** Stacked spectra of the H _β_ (in blue) and CO(3-2) lines in the outer regions of G04-1, G08-5 and G14-1 for the deep (in black) and
shallow data (in dark orange). The solid lines represent a Gaussian fit to the spectra from which we determined the velocity dispersion. The
velocity dispersion indicated is corrected for instrumental broadening.



of Pillepich et al. 2019) without a thermal term for a stellar
mass between 10.0 _<_ log( _M_ _⋆_ / _M_ _⊙_ ) _<_ 11.0. In their work, they
include only star-forming galaxies and defined the velocity
dispersion as the unweighted mean pixel-based (0.5 kpc) velocity dispersion of the star-forming gas. We note that the
star-forming gas traces both molecular and ionized gas without distinguishing between them, but we do not include here
the thermal contribution to compare with the cold gas component. They measured the dispersion on face-on galaxies and
average only pixels in the outer region of the galaxies that are
on the kinematic major axis, where the rotation curve is flat.
We find that the results from the simulations are overall
higher than our molecular gas observations. The values from
TNG50 are however lower than FIRE and EAGLE, and more

similar to our observations. This could be due to the different

methods used to determine the velocity dispersion in the simulations. FIRE and EAGLE include the velocity dispersion
from the center of the galaxies and weight their values using
the mass or SFR, while TNG50 only average the dispersion
of the pixels in the outer region. From our DYNAMO galaxies, we find that the velocity dispersion is on average 5-10
km s _[−]_ [1] higher when we include the center of galaxies and
weight with SFR. This could also be due to different physical processes included in the simulations and the way they are
implemented. In TNG50, unlike FIRE, the stellar feedback
is hydrodynamically decoupled from the interstellar medium
(Pillepich et al. 2019; Ubler et al. 2020 [¨] ). The AGN feedback
in TNG50 is however directly coupled to the gas. FIRE does
not have any AGN feedback. More details about what drives



the differences in velocity dispersion in the simulations will
be provided in Jimenez et al. (in prep).


3.3. _Impact on Toomre Q_


The Toome _Q_ stability parameter (Toomre 1964) for the
gas component can be expressed as _Q_ _gas_ = _σ_ 0 _κ/πG_ Σ _g_,
where _κ_ is the epicyclic frequency and Σ _g_ is the gas surface density. We derive _Q_ in three different ways: (1) with
_σ_ 0 _,ion_ and assuming a fixed _α_ _CO_ = 4 _._ 36; (2) with _σ_ 0 _,mol_
and a fixed _α_ _CO_ = 4 _._ 36; (3) with _σ_ 0 _,mol_ and a variable
_α_ _CO_ (Σ _CO_ ). To determine _α_ _CO_ (Σ _CO_ ), we use eq. 31 in
Bolatto et al. (2013) assuming a solar metallicity. We use
_α_ _CO_ = 4 _._ 36 to initially estimate Σ _CO_, and then recalculate
Σ _CO_ with the new estimate of _α_ _CO_ until we get a value of
_α_ _CO_ that does not vary by more than 0.1. We obtain a mean
Toomre Q of 0 _._ 94 _±_ 0 _._ 48, 0 _._ 38 _±_ 0 _._ 21, and 0 _._ 48 _±_ 0 _._ 24 for
methods (1), (2) and (3), respectively. The error is the stan
dard deviation.

Typical values for the local Universe are higher than one
and suggest that galaxies have a stable disk dominated by
pressure and rotation. A value of _Q_ _∼_ 1, or _Q_ _∼_ 0 _._ 7 for
thick disks (Kim & Ostriker 2007; Dekel et al. 2009; Romeo
& Wiegert 2011) expected in turbulent galaxies at high redshift (Genzel et al. 2011; Elmegreen et al. 2017; Girard et al.
2019), indicates a quasi-stable disk, where the gravity starts
dominating and could cause the fragmentation of the disk.
The values derived from the ionized gas in this work agree
with galaxies with a quasi-stable disk ( _Q_ _gas_ _∼_ 0 _._ 7 _−_ 1), similarly to the recent work from White et al. (2017). Simulations
agree with this picture by predicting a value of _Q ∼_ 1 at highredshift and _Q ∼_ 2 _−_ 3 in the local Universe (Kim & Ostriker

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 9


**Figure 4.** Intrinsic velocity dispersion of the molecular gas, _σ_ 0 _,mol_ (in dark orange), and ionized gas corrected for thermal broadening, _σ_ 0 _,ion_ - _th_
(in blue), as a function of star formation rate. The same data as in Fig. 2 are presented. The left and right panels present the feedback model
with _ϵ_ _ff_ fixed and free to vary and the model with feedback and gravitational instabilities (transport) from Krumholz et al. (2018), respectively,
using the same fiducial values.



2007; Hopkins et al. 2011; Ceverino et al. 2010). Meng et al.
(2019) found slightly lower values of _Q_ _∼_ 0 _._ 5 _−_ 1. Smaller
values than unity ( _Q_ _gas_ _∼_ 0 _._ 6 _−_ 0 _._ 8) have been found in
clumpy galaxies using the ionized gas as a kinematic tracer
and have been interpreted as clumps being the results of an
unstable disk (Fisher et al. 2014). Values as low as 0.2 have
been observed in star-forming clump regions (Genzel et al.
2011, 2014; Fisher et al. 2017a).
Our values derived from the molecular gas dispersion are
lower than the theoretical predictions, which suggest that
galaxies self-regulate with _Q_ _∼_ 0 _._ 7 _−_ 1 (Dekel et al. 2009;
Krumholz et al. 2018). A Toomre _Q_ parameter lower than
one (or _∼_ 0 _._ 7 for a thick disk) indicates unstable disks and
that galaxies should collapse due to gravitation or that gravitational instabilities are not the main effect regulating galaxies. When using a variable _α_ _CO_ with a _σ_ 0 _,mol_ the derived
values of _Q_ are still low, but the scatter is within the range of

the critical value of 0.7 for thick disks.


4. EFFECT OF USING MOLECULAR GAS

DISPERSION ON COMPARISONS TO STAR

FORMATION THEORIES


In this section, we explore the relation between the velocity
dispersion and star formation rate in addition to the relation
between the star formation rate surface density and pressure.
We also compare our observations to simulations and galaxy

evolution and stellar feedback models.


4.1. _Correlation of σ_ 0 _with star formation rate_



We explore the relationship between the velocity dispersion and the star formation rate in Fig. 4. We find a strong
correlation with a Spearman coefficient of 0.71 for the molecular gas. This means that the most gas-rich, turbulent disk
galaxies of our sample are also more star-forming. A relation
between _σ_ 0 and SFR could be seen if our sample selection
is biased to the brightest objects at high redshift and to less
star-forming galaxies in the local Universe since highly starforming local galaxies are rare. However, this is unlikely
since our sample includes lensed main-sequence galaxies at
_z_ _∼_ 1 with lower SFR (Girard et al. 2019) and nearby galaxies from DYNAMO with a higher SFR (Fisher et al. 2017a).
These galaxies fall very well on the relation and show similar dispersion as other galaxies with the same SFR. This also
suggests that the processes that convert the gas into stars are
independent of redshift.
One scenario that has been suggested to explain the turbulence in the disk is the star formation feedback, which
includes all the energy that is released in the interstellar
medium from the stellar formation (stellar winds, supernovae, etc.). It is now well established that feedback only
models, with traditional assumptions about feedback efficiency, do not produce a strong correlation between the
star formation rate and the dispersion. Ostriker & Shetty
(2011) and Shetty & Ostriker (2012) predict values between
_σ_ 0 _∼_ 3 _−_ 12 km s _[−]_ [1] that barely vary with SFR. Krumholz
et al. (2018) found similar results for a model with fixed
star formation efficiency per free fall time, _ϵ_ _ff_ (see Fig. 4,
left panel). Some models also predicted higher velocity dispersion of _σ_ 0 _>_ 50 km s _[−]_ [1], when including non-standard

10 G IRARD ET AL .


assumptions, such as boosting of feedback from clustering
of supernova (Gatto et al. 2015; Hopkins et al. 2011; Gentry et al. 2017; Fielding et al. 2018). Overall, with fiducial
assumptions, the models predict that the maximum velocity
dispersion that the feedback can sustain is about 15 km s _[−]_ [1] .
Even though the molecular gas dispersion is lower, it is still
true that fixed-efficiency feedback-only models do no produce high enough dispersions.



Krumholz et al. (2018) suggested that the discrepancy at
high star formation rate could be alleviated by gravitational
instabilities (or transport). In this model, the turbulence in the
rotating galaxies depends on two main drivers, the feedback
and the energy loss from gravitationally driven gas flows.
They found that this model predicts values consistent with
the ionized gas velocity dispersion obtained in several surveys. ¨Ubler et al. (2019) also found that their ionized gas
observations from KMOS [3D] are in good agreement with this
model. In this work, we find that taking the recommended
prescriptions for those models over predicts the molecular
gas velocity dispersion, as seen in Fig. 4 (right panel). The
SFR of high-redshift galaxies is a factor _∼_ 10 higher than
the predictions from the model at a fixed dispersion. We note
here that this result is obtained from the SFR and velocity
dispersion, two quantities that do not depend on the CO-toH 2 conversion factor, _α_ _CO_ .

Faucher-Gigu`ere et al. (2013) and Krumholz et al. (2018)
also presented a stellar feedback model with _ϵ_ _ff_ free to vary
(see Fig. 4, left panel). This model predicts an increase
of the velocity dispersion with SFR with a dependence in
SFR _∝_ _σ_ [2] . This model poorly reproduces values from the
ionized gas, though it does seem to model the molecular gas
relation quite well. Overall, the predicted velocity dispersion from the model are slightly higher than the molecular
gas velocity dispersion of the most star-forming galaxies of
our sample, but this model better describes our observations
from the molecular gas than models assuming fixed _ϵ_ _ff_ or
including gravitational instabilites.


4.2. _Correlation of_ Σ _SF R_ _with pressure_


In this section, we investigate the relationship between the
SFR surface density, Σ _SF R_, and pressure in the galaxies. We
report in this work new pressure measurements derived using
the molecular gas velocity dispersion for high-pressure systems. A correlation between these two quantities have been
predicted by theoretical models and simulations (Ostriker &
Shetty 2011; Kim et al. 2013). Observations have also shown
that there is a clear correlation (Leroy et al. 2008; HerreraCamus et al. 2017; Sun et al. 2020), but the observed relation
does not always agree with predictions from the models, especially for the most star-forming galaxies in which the pressure is high (Fisher et al. 2019). A correlation between these



**Figure 5.** SFR surface density as a function of the midplane hydrostatic pressure, _P_ _H_ . We include the measurements from the same
sample as presented in previous figures when the different quantities were available. The measurements obtained using the molecular
and ionized gas dispersion are indicated with dark orange and blue
empty symbols, respectively. The dashed lines indicates the relationship obtained from Kim et al. (2013) using simulations, and the
shaded area indicates the fits obtained by Fisher et al. (2019) using
ionized gas dispersion. The typical error on the values is indicated
at the bottom. The symbols and orange lines indicate the values of
_P_ _H_ obtained assuming _α_ _CO_ = 4 _._ 36 and _α_ _CO_ (Σ _CO_ ) using eq. 31
from Bolatto et al. (2013), respectively.


two properties suggests that the pressure in galaxies is regulated by stellar feedback processes.
First we estimate the total midplane hydrostatic pressure
using the equation from Elmegreen (1989):



(3)
�



_P_ _H_ = _[πG]_

2 [Σ] _[g]_



Σ _g_ + _[σ]_ _[g]_ [Σ] _[⋆]_
� _σ_ _⋆_



where Σ _g_ and Σ _⋆_ are the gas (molecular and neutral) and
stellar mass surface densities and _σ_ _g_ and _σ_ _⋆_ are the gas and
stellar velocity dispersion.
We also estimate the dynamical equilibrium pressure using
the following equation (Kim et al. 2011):


_P_ _DE_ _≈_ _[πG]_ 2 [Σ] _g_ [2] [+ Σ] _[g]_ [(2] _[Gρ]_ _[SD]_ [)] [1] _[/]_ [2] _[σ]_ _[g]_ (4)

where the total midplane density _ρ_ _SD_ = Σ _⋆_ _/_ (4 _h_ _z_ ) +
( _υ_ _rot_ _/R_ _disk_ ) [2] _/_ (4 _πG_ ) (Leroy et al. 2008; Ostriker & Shetty
2011). The first term represents the stellar component, where
_h_ _z_ is the stellar scale height, and the second term represents

the contribution from dark matter.

To obtain Σ _SF R_, Σ _mol_ and Σ _⋆_ for the DYNAMO galaxies,
we derive the half-light radius, _R_ 1 _/_ 2, by fitting an exponential profile to the H _α_, CO(3-2) or CO(4-3), and F125W/HST

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 11



maps when available. We obtain that _R_ 1 _/_ 2 _,H_ _α_ = (1 _._ 1 _±_ 0 _._ 2)
_R_ 1 _/_ 2 _,CO_ and _R_ 1 _/_ 2 _,H_ _α_ = (0 _._ 8 _±_ 0 _._ 2) _R_ 1 _/_ 2 _,⋆_ in the DYNAMO
sample. To estimate the total gas mass density, Σ _g_, we assume a HI gas surface density of 5 _M_ _⊙_ pc _[−]_ [2] (Bigiel et al.
2008). We find that assuming a larger value of 15 _M_ _⊙_ pc _[−]_ [2]

could lead to a difference of 0.1 dex for the pressure in the
DYNAMO galaxy with the lower pressure. The difference
is typically 0.02-0.03 dex for the other DYNAMO galaxies.

This is taken into account in the error.

In Fig. 5, we also present measurements for other galaxies from the same sample shown in Figs. 2 and 4. For the
HERACLES (or THINGS) galaxies, we derive the HI gas
mass density from the HI masses available in Leroy et al.
(2008). We also use _R_ 1 _/_ 2 _,SF R_, _R_ 1 _/_ 2 _,CO_ and _R_ 1 _/_ 2 _,⋆_ for
each corresponding surface density and the molecular velocity dispersion derived in Mogotsi et al. (2016). For the
high-redshift galaxies presented in this figure, we assume the
same HI gas surface density of 5 _M_ _⊙_ pc _[−]_ [2] used for the DYNAMO galaxies and that _R_ 1 _/_ 2 _,SF R_ _≈_ _R_ 1 _/_ 2 _,CO_ _≈_ _R_ 1 _/_ 2 _,⋆_
as found in several studies (e.g. Tacconi et al. 2013; Bolatto
et al. 2015). We note that assuming _R_ 1 _/_ 2 _,H_ _α_ = 1 _._ 1 _R_ 1 _/_ 2 _,CO_
and _R_ 1 _/_ 2 _,CO_ = 0 _._ 8 _R_ 1 _/_ 2 _,⋆_, as found in this work for DYNAMO galaxies, could increase the pressure by a factor 1.52.0. (0.2-0.35 dex) for the PHIBSS galaxies.
To determine the stellar dispersion, we use the approximation _σ_ _⋆_ _≈_ 0 _._ 5 _[√]_ _πGl_ _⋆_ Σ _⋆_, where _l_ _⋆_ is the disk scale
length. The disk scale length can be determined from _l⋆_ =
_R_ 1 _/_ 2 _,⋆_ _/_ 1 _._ 76. We find a good agreement between the values
obtained from this estimation with the values derived for two

DYNAMO galaxies by Bassett et al. (2014). We also use the
equation _σ_ _⋆_ = 2 _._ 45 _× σ_ 0 _,mol_ + 15 to estimate the stellar velocity dispersion (Fisher et al. 2019). We find a maximum
difference of _∼_ 0 _._ 05 dex for the pressure using this method.
To determine the dynamical equilibrium pressure, _P_ _DE_,
one needs to assume the stellar scale height, _h_ _z_, of the
galaxies. Local galaxies typically have a scale height of
_∼_ 100 pc while high-redshift galaxies have a thicker disk
of 500 _−_ 1000 pc (Elmegreen & Elmegreen 2005; Bassett
et al. 2014; Elmegreen et al. 2017). Elmegreen et al. (2017)
found on average a scale height of 630 _±_ 240 pc for galaxies
at _z_ _∼_ 2. In this work, we therefore assume a value of 100 pc
and 630 pc for local and high-redshift or DYNAMO galaxies, respectively. We find that assuming 500 pc and 1000 pc
instead of 630 pc for the high-redshift and DYNAMO galax
ies could lead to differences of 0.02 dex. We note that our

results suggest that the molecular gas disk thickness is much

lower than the ionized and stellar disk thickness.

Fig. 5 presents the midplane hydrostatic pressure measurements from the ionized gas (blue empty symbols) and molecular gas (dark orange symbols). We find that at high Σ _SF R_,
pressure derived using molecular gas velocity dispersion is
still on average an order of magnitude larger than expecta


tions from theory and simulation. We find median and mean

differences between the values measured from the ionized

and molecular gas of the DYNAMO galaxies of 0.24 dex and
0.22 dex, respectively. This means that pressure measurements derived using the ionized gas as a tracer can be overestimated by about _∼_ 0 _._ 22 dex. We only show _P_ _H_ in Fig. 5
since _P_ _H_ and _P_ _DE_ are very similar (difference of 0 _._ 03 dex
and 0 _._ 06 dex for DYNAMO and the whole sample, respectively). The values are presented in Table 2.
We find a strong correlation with a Spearman coefficient
of 0.92 for the molecular gas. This suggests that the pressure
in both low and high SFR density environments is regulated
by stellar feedback processes. We fit a linear relation using
the molecular dispersion measurements and obtain a slope
of 0 _._ 70 _±_ 0 _._ 07. We also show values of _P_ _H_ assuming that
_α_ _CO_ varies with Σ _CO_ in Fig. 5 (orange line). As described
previously in Sect. 3.3, we derive _α_ _CO_ (Σ _CO_ ) following eq.
31 from Bolatto et al. (2013). We find that the pressures are
lower by 0.21 dex on average for the DYNAMO galaxies. We
fit again a linear relation using the whole sample and obtain
a slope of 0 _._ 83 _±_ 0 _._ 08, consistent with the results previously
obtained by Fisher et al. (2019) of 0 _._ 76 _±_ 0 _._ 06 with a similar sample. Sun et al. (2020) also found a sublinear slope of
0 _._ 84 _±_ 0 _._ 01 from their observations of local galaxies at kpcscales. This means that observations are in agreement with
sublinear slopes and are lower than predictions from simulations and theoretical derivations, which estimate a slope of
_∼_ 1 _−_ 1 _._ 2 (Ostriker et al. 2010; Kim et al. 2011, 2013; Muratov et al. 2015). This indicates that the pressure in high SFR
density galaxies is higher than predicted by feedback models.

Fisher et al. (2019) suggested that this could be due to the
variation of the feedback momentum injected into the interstellar medium, _p_ _∗_ _/m_ _∗_, with the local environments. One
possible candidate is that supernova clustering leads to more
efficient feedback (Gentry et al. 2020). Alternatively, mech
anisms other than feedback from stars could also drive tur
bulence in the most star-forming galaxies. Krumholz et al.
(2018) suggested that gravitational instabilities (or transport),
in addition to feedback, could drive more turbulence and lead
to higher pressure. However, from Fig. 4 (right panel) we
find that this model overestimates the molecular gas velocity
dispersion observed in the most star-forming galaxies.


5. SUMMARY


We present resolved ALMA and GMOS/Gemini observations of 9 galaxies from DYNAMO, a sample of rare galaxies
at 0 _._ 075 _<_ _z_ _<_ 0 _._ 2 showing similar physical and kinematic
properties to _z_ _∼_ 1 _−_ 2 main-sequence galaxies. We combine
our sample with 12 galaxies at _z_ _∼_ 0 _._ 5 _−_ 2 _._ 5 and find that the
molecular gas velocity dispersion is systematically lower by
a factor of 2 _._ 45 _±_ 0 _._ 38 compared to the ionized gas velocity
dispersion, after correcting for thermal broadening and HII

12 G IRARD ET AL .



region expansion. This difference does not depend on gas

fraction and indicates the co-existence of a thin molecular

gas disk and thick ionized gas disk in these galaxies. The
nature of this difference remains unclear. One possible explanation could be the presence of fast shocks that dissociate
the molecular gas.
We find a strong correlation between _σ_ 0 and _f_ _gas_ and obtain a fit of log( _σ_ 0 _,mol_ _/_ km s _[−]_ [1] ) = 0 _._ 87 _×f_ _gas_ +(0 _._ 90 _±_ 0 _._ 03)
and log( _σ_ 0 _,ion_ - _th_ _/_ km s _[−]_ [1] ) = 0 _._ 87 _× f_ _gas_ + (1 _._ 29 _±_ 0 _._ 03),
with a zero-offset of 0 _._ 39 _±_ 0 _._ 06 dex between the ionized

and molecular gas. We also find that _σ_ 0 _,mol_ is higher in highredshift galaxies and show that the EAGLE and FIRE simulations overall predict higher values. TNG50 better predicts
the observations. We obtain Toomre Q values of 0 _._ 94 _±_ 0 _._ 48,
0 _._ 38 _±_ 0 _._ 21, and 0 _._ 48 _±_ 0 _._ 24 on average for the DYNAMO
sample when assuming _α_ _CO_ = 4 _._ 36 and _σ_ 0 = _σ_ 0 _,ion_,
_α_ _CO_ = 4 _._ 36 and _σ_ 0 = _σ_ 0 _,mol_, and _α_ _CO_ (Σ _CO_ ) and _σ_ 0 =
_σ_ 0 _,mol_, respectively. Our estimations using the molecular gas
velocity dispersion are typically lower than predictions from
gravitational instability theory of _Q ∼_ 0 _._ 7 _−_ 1 _._ 0.
We obtain a strong correlation between the molecular velocity dispersion and the star formation rate. When comparing our results to predictions from analytical star formation
models, we find that stellar feedback models assuming a constant _ϵ_ _ff_ are not able to reproduce the higher molecular gas
velocity dispersion of the more star-forming galaxies. We
also find that models that include both stellar feedback and
gravitational instabilities (or transport), and that were previously found to predict well the ionized gas velocity dispersion, overestimate the molecular velocity dispersion. However, stellar feedback models with _ϵ_ _ff_ free to vary predict
values similar to our observations.

We explore the correlation between SFR surface density,
Σ _SF R_, and pressure and find that both the total midplane hydrostatic pressure, _P_ _H_, and dynamical equilibrium pressure,
_P_ _DE_, derived using the molecular gas velocity dispersion are
lower by _∼_ 0 _._ 22 dex compared to the values derived using
the ionized gas velocity dispersion. When assuming a variable _α_ _CO_, we find that the pressure is lower by _∼_ 0 _._ 21 dex
in the DYNAMO galaxies. We find a sublinear relation of
0 _._ 70 _±_ 0 _._ 07 and 0 _._ 83 _±_ 0 _._ 08 for _α_ _CO_ = 4 _._ 36 and a variable
_α_ _CO_ (Σ _CO_ ), in agreement with previous results from Fisher
et al. (2019), but lower than predictions from stellar feedback

models.

The disagreement between predictions from feedback
models and the pressure and turbulence observed in the DYNAMO galaxies and other high-redshift galaxies could indicate that another mechanism drives these quantities. Another
possibility is that the star formation efficiency, _ϵ_ _ff_, and/or
the feedback efficiency, _p_ _∗_ _/m_ _∗_, vary in galaxies, and are
higher in the densest environments. Clearly, more studies
on the molecular gas kinematics in high-redshift galaxies are



needed to better understand the nature of the turbulence and

high pressure in these galaxies.


ACKNOWLEDGMENTS


MG and DBF acknowledge support from Australian Research Council (ARC) DP grant DP160102235 and Future Fellowship FT170100376. RB acknowledges support

from the Australian Research Council Centre of Excellence

for All Sky Astrophysics in 3 Dimensions (ASTRO 3D)
through project number CE170100013. EJ acknowledges
the support of the University of Western Australia through
a Scholarship for International Research Fees and a CoFunded Postgraduate Award. DO is a recipient of an Australian Research Council Future Fellowship (FT190100083)
funded by the Australian Government. We are grateful to
Hannah Ubler [¨] and the PHIBSS team for sharing information. This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2017.1.00239.S and ADS/JAO.ALMA#
2019.1.00447.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ.


_Facilities:_ ALMA, Gemini

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 13


APPENDIX


A. KINEMATIC MAPS


Figure 6 shows the HST F125W images, the flux maps, the observed velocity maps and the observed velocity dispersion maps
of ALMA and GMOS/Gemini data of each galaxy from the DYNAMO sample. We also present the observed rotation curves, the
modeled rotation curves and the dispersion profiles of each galaxy.


B. GALAXY PROPERTIES


Table 2 presents the H _α_, CO and stellar half-light radii derived for the DYNAMO sample. We also show the values from the
literature for the high-redshift and local galaxy samples. We show the derived values of _P_ _H_ using the ionised and molecular
gas velocity dispersion assuming _α_ _CO_ = 4 _._ 36, _P_ _H_ ( _α_ _CO_ ) using the molecular gas velocity dispersion and assuming a variable
_α_ _CO_ (Σ _CO_ ) following the prescription of Bolatto et al. (2013), and _P_ _DE_ using the molecular gas velocity dispersion and _α_ _CO_ =
4 _._ 36.

14 G IRARD ET AL .


**Figure 6.** HST F125W images, the flux maps, the observed velocity maps and the velocity dispersion maps of each galaxy from the DYNAMO
sample. The white lines in the velocity and dispersion maps indicate the kinematic major axis. In the right panels, we present the rotation
curves (circle) and dispersion profiles (triangle) extracted on the major axis of the observed velocity and dispersion maps and the rotation
curves extracted on the major axis of the velocity maps from the kinematic models (solid line). The intrinsic rotation curves corrected for
inclination and intrinsic velocity dispersion from the models are indicated with a dashed line and dotted line, respectively. The molecular and
ionised gas are in orange and blue, respectively.

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 15


**Figure 6.** Continued.

16 G IRARD ET AL .


**Figure 6.** Continued.


REFERENCES



Barro, G., Kriek, M., P´erez-Gonz´alez, P. G., et al. 2017, ApJL,

[851, L40, doi: 10.3847/2041-8213/aa9f0d](http://doi.org/10.3847/2041-8213/aa9f0d)

Bassett, R., Glazebrook, K., Fisher, D. B., et al. 2014, MNRAS,

[442, 3206, doi: 10.1093/mnras/stu1029](http://doi.org/10.1093/mnras/stu1029)

Bekiaris, G., Glazebrook, K., Fluke, C. J., & Abraham, R. 2016,

[MNRAS, 455, 754, doi: 10.1093/mnras/stv2292](http://doi.org/10.1093/mnras/stv2292)

Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846,

[doi: 10.1088/0004-6256/136/6/2846](http://doi.org/10.1088/0004-6256/136/6/2846)

Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51,

[207, doi: 10.1146/annurev-astro-082812-140944](http://doi.org/10.1146/annurev-astro-082812-140944)

Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2015, ApJ, 809,

[175, doi: 10.1088/0004-637X/809/2/175](http://doi.org/10.1088/0004-637X/809/2/175)



Bouch´e, N., Carfantan, H., Schroetter, I., Michel-Dansac, L., &


[Contini, T. 2015, AJ, 150, 92, doi: 10.1088/0004-6256/150/3/92](http://doi.org/10.1088/0004-6256/150/3/92)


Bournaud, F., Elmegreen, B. G., Teyssier, R., Block, D. L., &


Puerari, I. 2010, MNRAS, 409, 1088,


[doi: 10.1111/j.1365-2966.2010.17370.x](http://doi.org/10.1111/j.1365-2966.2010.17370.x)


Burkert, A., F¨orster Schreiber, N. M., Genzel, R., et al. 2016, ApJ,


[826, 214, doi: 10.3847/0004-637X/826/2/214](http://doi.org/10.3847/0004-637X/826/2/214)


Cald´u-Primo, A., Schruba, A., Walter, F., et al. 2013, AJ, 146, 150,


[doi: 10.1088/0004-6256/146/6/150](http://doi.org/10.1088/0004-6256/146/6/150)


Calistro Rivera, G., & Hodge, J. 2018, The Messenger, 173, 33,


[doi: 10.18727/0722-6691/5096](http://doi.org/10.18727/0722-6691/5096)

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 17


**Table 2.** Galaxy properties


Galaxy R 1 _/_ 2 _,SF R_ _a_ R 1 _/_ 2 _,CO_ _a_ R 1 _/_ 2 _,⋆_ _a_ P _H,ion_ _/k_ _B_ P _H,mol_ _/k_ _B_ P _H,mol_ ( _α_ _CO_ ) _/k_ _B_ P _DE,mol_ _/k_ _B_ Reference for the radius


[kpc] [kpc] [kpc] [log(cm _[−]_ [3] _K_ )] [log(cm _[−]_ [3] _K_ )] [log(cm _[−]_ [3] _K_ )] [log(cm _[−]_ [3] _K_ )]


C13-1 4.2 3.3 - 5.42 _±_ 0 _._ 22 5.13 _±_ 0 _._ 24 5.12 _±_ 0 _._ 24 5.10 _±_ 0 _._ 25 This work

C22-2 3.4 1.9 - 6.03 _±_ 0 _._ 14 5.78 _±_ 0 _._ 15 5.76 _±_ 0 _._ 15 5.75 _±_ 0 _._ 17 This work

D13-5 2.0 1.9 2.5 6.82 _±_ 0 _._ 13 6.56 _±_ 0 _._ 12 6.34 _±_ 0 _._ 13 6.50 _±_ 0 _._ 16 This work

D15-3 2.2 1.7 3.0 6.63 _±_ 0 _._ 12 6.47 _±_ 0 _._ 11 6.23 _±_ 0 _._ 11 6.44 _±_ 0 _._ 13 This work

G04-1 2.8 2.4 3.3 6.95 _±_ 0 _._ 13 6.84 _±_ 0 _._ 12 6.49 _±_ 0 _._ 12 6.82 _±_ 0 _._ 14 This work

G08-5 1.8 1.7 2.3 6.50 _±_ 0 _._ 15 6.32 _±_ 0 _._ 14 6.17 _±_ 0 _._ 14 6.28 _±_ 0 _._ 15 This work

G14-1 1.1 1.1 2.7 6.95 _±_ 0 _._ 15 6.75 _±_ 0 _._ 13 6.48 _±_ 0 _._ 13 6.73 _±_ 0 _._ 15 This work

G20-2 2.1 2.1 2.2 6.15 _±_ 0 _._ 16 5.77 _±_ 0 _._ 18 5.77 _±_ 0 _._ 18 5.69 _±_ 0 _._ 19 This work

SDSS 013527-1039 1.6 1.7 - 7.87 _±_ 0 _._ 14 7.62 _±_ 0 _._ 12 7.07 _±_ 0 _._ 12 7.56 _±_ 0 _._ 13 This work

SMM J2315-0102 - 1 _._ 5 - - 8.58 _±_ 0 _._ 19 7.72 _±_ 0 _._ 17 8.55 _±_ 0 _._ 20 Swinbank et al. (2011)

Cosmic Snake 6.0 _±_ 1 _._ 2 0.75 _±_ 0 _._ 03 - 7.84 _±_ 0 _._ 16 7.84 _±_ 0 _._ 18 7.09 _±_ 0 _._ 17 7.85 _±_ 0 _._ 19 Girard et al. (2019)

SHiZELS-19 1.80 _±_ 0 _._ 16 1.68 _±_ 0 _._ 03 - 8.54 _±_ 0 _._ 14 8.52 _±_ 0 _._ 16 7.77 _±_ 0 _._ 14 8.46 _±_ 0 _._ 17 Molina et al. (2019)
G3 ~~1~~ 0098 - - 8.5 - 5.33 _±_ 0 _._ 28 5.32 _±_ 0 _._ 28 - PHIBSS _[b]_


G4 ~~2~~ 1351 - - 7.9 - 5.30 _±_ 0 _._ 27 5.30 _±_ 0 _._ 27 - PHIBSS _[b]_


EGS ~~1~~ 3035123 - - 9.1 - 5.59 _±_ 0 _._ 27 5.58 _±_ 0 _._ 27 5.62 _±_ 0 _._ 28 PHIBSS _[b]_


EGS ~~1~~ 2007881 - - 6.0 - 6.02 _±_ 0 _._ 20 5.94 _±_ 0 _._ 20 6.02 _±_ 0 _._ 20 PHIBSS _[b]_


EGS ~~1~~ 3003805 - - 5.6 - 6.91 _±_ 0 _._ 20 6.58 _±_ 0 _._ 19 6.90 _±_ 0 _._ 20 PHIBSS _[b]_


EGS4 ~~2~~ 4985 - - 4.9 - 6.19 _±_ 0 _._ 19 6.08 _±_ 0 _._ 19 - PHIBSS _[b]_


EGS ~~1~~ 3011166 - - 6.9 - 6.90 _±_ 0 _._ 20 6.54 _±_ 0 _._ 19 6.90 _±_ 0 _._ 21 PHIBSS _[b]_


NGC628 4.2 4.2 4.0 - 4.62 _±_ 0 _._ 15 4.62 _±_ 0 _._ 15 4.76 _±_ 0 _._ 16 Leroy et al. (2008)

NGC925 7.2 - 7.2 - 3.72 _±_ 0 _._ 15 3.72 _±_ 0 _._ 15 3.92 _±_ 0 _._ 16 Leroy et al. (2008)

NGC2976 1.4 2.1 1.6 - 3.62 _±_ 0 _._ 19 3.62 _±_ 0 _._ 19 3.71 _±_ 0 _._ 20 Leroy et al. (2008)

NGC3184 4.9 5.1 4.2 - 4.41 _±_ 0 _._ 16 4.41 _±_ 0 _._ 16 4.61 _±_ 0 _._ 16 Leroy et al. (2008)

NGC3351 3.2 4.4 3.9 - 4.21 _±_ 0 _._ 18 4.21 _±_ 0 _._ 18 4.42 _±_ 0 _._ 19 Leroy et al. (2008)

NGC4736 1.6 1.4 1.9 - 5.35 _±_ 0 _._ 18 5.35 _±_ 0 _._ 18 5.44 _±_ 0 _._ 18 Leroy et al. (2008)

NGC5055 5.5 5.5 5.6 - 5.11 _±_ 0 _._ 16 5.11 _±_ 0 _._ 16 5.29 _±_ 0 _._ 17 Leroy et al. (2008)

NGC6946 4.8 3.4 4.4 - 5.50 _±_ 0 _._ 15 5.49 _±_ 0 _._ 15 5.61 _±_ 0 _._ 15 Leroy et al. (2008)


N OTE —

_a_ Typical uncertainty on the radius of the DYNAMO galaxies is 15%. We assume a similar error on the radius of other galaxies when the uncertainty was unavailable.
_b_ PHIBSS refers to Tacconi et al. (2013), Tacconi et al. (2018), Genzel et al. (2015), and Freundlich et al. (2019). The radius was measured in the rest-frame optical.



Ceverino, D., Dekel, A., & Bournaud, F. 2010, MNRAS, 404,


[2151, doi: 10.1111/j.1365-2966.2010.16433.x](http://doi.org/10.1111/j.1365-2966.2010.16433.x)


Cortese, L., Catinella, B., & Janowiecki, S. 2017, ApJL, 848, L7,


[doi: 10.3847/2041-8213/aa8cc3](http://doi.org/10.3847/2041-8213/aa8cc3)


Courteau, S. 1997, AJ, 114, 2402


Dekel, A., Sari, R., & Ceverino, D. 2009, ApJ, 703, 785,


[doi: 10.1088/0004-637X/703/1/785](http://doi.org/10.1088/0004-637X/703/1/785)


Dessauges-Zavadsky, M., Zamojski, M., Schaerer, D., et al. 2015,


[A&A, 577, A50, doi: 10.1051/0004-6361/201424661](http://doi.org/10.1051/0004-6361/201424661)


Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115,


[doi: 10.1046/j.1365-8711.2000.03386.x](http://doi.org/10.1046/j.1365-8711.2000.03386.x)


[Elmegreen, B. G. 1989, ApJ, 338, 178, doi: 10.1086/167192](http://doi.org/10.1086/167192)



Elmegreen, B. G., & Elmegreen, D. M. 2005, ApJ, 627, 632,


[doi: 10.1086/430514](http://doi.org/10.1086/430514)


Elmegreen, B. G., Elmegreen, D. M., Tompkins, B., & Jenks, L. G.


[2017, ApJ, 847, 14, doi: 10.3847/1538-4357/aa88d4](http://doi.org/10.3847/1538-4357/aa88d4)


Epinat, B., Amram, P., Balkowski, C., & Marcelin, M. 2010,


[MNRAS, 401, 2113, doi: 10.1111/j.1365-2966.2009.15688.x](http://doi.org/10.1111/j.1365-2966.2009.15688.x)


Epinat, B., Tasca, L., Amram, P., et al. 2012, A&A, 539, A92,


[doi: 10.1051/0004-6361/201117711](http://doi.org/10.1051/0004-6361/201117711)


Faucher-Gigu`ere, C.-A., Quataert, E., & Hopkins, P. F. 2013,


[MNRAS, 433, 1970, doi: 10.1093/mnras/stt866](http://doi.org/10.1093/mnras/stt866)


Fielding, D., Quataert, E., & Martizzi, D. 2018, MNRAS, 481,


[3325, doi: 10.1093/mnras/sty2466](http://doi.org/10.1093/mnras/sty2466)

18 G IRARD ET AL .



Fisher, D. B., Bolatto, A. D., White, H., et al. 2019, ApJ, 870, 46,

[doi: 10.3847/1538-4357/aaee8b](http://doi.org/10.3847/1538-4357/aaee8b)


Fisher, D. B., Glazebrook, K., Bolatto, A., et al. 2014, ApJL, 790,

[L30, doi: 10.1088/2041-8205/790/2/L30](http://doi.org/10.1088/2041-8205/790/2/L30)


Fisher, D. B., Glazebrook, K., Damjanov, I., et al. 2017a, MNRAS,

[464, 491, doi: 10.1093/mnras/stw2281](http://doi.org/10.1093/mnras/stw2281)


Fisher, D. B., Glazebrook, K., Abraham, R. G., et al. 2017b, ApJL,

[839, L5, doi: 10.3847/2041-8213/aa6478](http://doi.org/10.3847/2041-8213/aa6478)


F¨orster Schreiber, N. M., Genzel, R., Bouch´e, N., et al. 2009, ApJ,

[706, 1364, doi: 10.1088/0004-637X/706/2/1364](http://doi.org/10.1088/0004-637X/706/2/1364)


Freundlich, J., Combes, F., Tacconi, L. J., et al. 2013, A&A, 553,

[A130, doi: 10.1051/0004-6361/201220981](http://doi.org/10.1051/0004-6361/201220981)


[—. 2019, A&A, 622, A105, doi: 10.1051/0004-6361/201732223](http://doi.org/10.1051/0004-6361/201732223)


Gatto, A., Walch, S., Low, M. M. M., et al. 2015, MNRAS, 449,

[1057, doi: 10.1093/mnras/stv324](http://doi.org/10.1093/mnras/stv324)


Gentry, E. S., Krumholz, M. R., Dekel, A., & Madau, P. 2017,

[MNRAS, 465, 2471, doi: 10.1093/mnras/stw2746](http://doi.org/10.1093/mnras/stw2746)


Gentry, E. S., Madau, P., & Krumholz, M. R. 2020, MNRAS, 492,

[1243, doi: 10.1093/mnras/stz3440](http://doi.org/10.1093/mnras/stz3440)


Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS,

[407, 2091, doi: 10.1111/j.1365-2966.2010.16969.x](http://doi.org/10.1111/j.1365-2966.2010.16969.x)


Genzel, R., Newman, S., Jones, T., et al. 2011, ApJ, 733, 101,

[doi: 10.1088/0004-637X/733/2/101](http://doi.org/10.1088/0004-637X/733/2/101)


Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69,

[doi: 10.1088/0004-637X/746/1/69](http://doi.org/10.1088/0004-637X/746/1/69)


Genzel, R., F¨orster Schreiber, N. M., Lang, P., et al. 2014, ApJ,

[785, 75, doi: 10.1088/0004-637X/785/1/75](http://doi.org/10.1088/0004-637X/785/1/75)


Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20,

[doi: 10.1088/0004-637X/800/1/20](http://doi.org/10.1088/0004-637X/800/1/20)


Girard, M., Dessauges-Zavadsky, M., Combes, F., et al. 2019,

[A&A, 631, A91, doi: 10.1051/0004-6361/201935896](http://doi.org/10.1051/0004-6361/201935896)


Girard, M., Dessauges-Zavadsky, M., Schaerer, D., et al. 2018a,

[A&A, 619, A15, doi: 10.1051/0004-6361/201833533](http://doi.org/10.1051/0004-6361/201833533)


[—. 2018b, A&A, 613, A72, doi: 10.1051/0004-6361/201731988](http://doi.org/10.1051/0004-6361/201731988)


Green, A. W., Glazebrook, K., Gilbank, D. G., et al. 2017,

[MNRAS, 470, 639, doi: 10.1093/mnras/stx1119](http://doi.org/10.1093/mnras/stx1119)


Green, A. W., Glazebrook, K., McGregor, P. J., et al. 2010, Nature,

[467, 684, doi: 10.1038/nature09452](http://doi.org/10.1038/nature09452)


[—. 2014, MNRAS, 437, 1070, doi: 10.1093/mnras/stt1882](http://doi.org/10.1093/mnras/stt1882)


Hao, C.-N., Kennicutt, R. C., Johnson, B. D., et al. 2011, ApJ, 741,

[124, doi: 10.1088/0004-637X/741/2/124](http://doi.org/10.1088/0004-637X/741/2/124)


Herrera-Camus, R., Bolatto, A., Wolfire, M., et al. 2017, ApJ, 835,

[201, doi: 10.3847/1538-4357/835/2/201](http://doi.org/10.3847/1538-4357/835/2/201)


Ho, I. T., Kewley, L. J., Dopita, M. A., et al. 2014, MNRAS, 444,

[3894, doi: 10.1093/mnras/stu1653](http://doi.org/10.1093/mnras/stu1653)


Hollenbach, D., & McKee, C. F. 1980, ApJL, 241, L47,

[doi: 10.1086/183358](http://doi.org/10.1086/183358)


Hopkins, P. F., Quataert, E., & Murray, N. 2011, MNRAS, 417,

[950, doi: 10.1111/j.1365-2966.2011.19306.x](http://doi.org/10.1111/j.1365-2966.2011.19306.x)



Hung, C.-L., Hayward, C. C., Yuan, T., et al. 2019, MNRAS, 482,

[5125, doi: 10.1093/mnras/sty2970](http://doi.org/10.1093/mnras/sty2970)


Ianjamasimanana, R., de Blok, W. J. G., Walter, F., & Heald, G. H.

[2012, AJ, 144, 96, doi: 10.1088/0004-6256/144/4/96](http://doi.org/10.1088/0004-6256/144/4/96)


Johnson, H. L., Harrison, C. M., Swinbank, A. M., et al. 2018,

[MNRAS, 474, 5076, doi: 10.1093/mnras/stx3016](http://doi.org/10.1093/mnras/stx3016)


Kim, C.-G., Kim, W.-T., & Ostriker, E. C. 2011, ApJ, 743, 25,

[doi: 10.1088/0004-637X/743/1/25](http://doi.org/10.1088/0004-637X/743/1/25)


Kim, C.-G., Ostriker, E. C., & Kim, W.-T. 2013, ApJ, 776, 1,

[doi: 10.1088/0004-637X/776/1/1](http://doi.org/10.1088/0004-637X/776/1/1)


Kim, W.-T., & Ostriker, E. C. 2007, ApJ, 660, 1232,

[doi: 10.1086/513176](http://doi.org/10.1086/513176)


Kroupa, P. 2001, MNRAS, 322, 231,

[doi: 10.1046/j.1365-8711.2001.04022.x](http://doi.org/10.1046/j.1365-8711.2001.04022.x)


Krumholz, M. R., & Burkhart, B. 2016, MNRAS, 458, 1671,

[doi: 10.1093/mnras/stw434](http://doi.org/10.1093/mnras/stw434)


Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M.

[2018, MNRAS, 477, 2716, doi: 10.1093/mnras/sty852](http://doi.org/10.1093/mnras/sty852)


Lehnert, M. D., Nesvadba, N. P. H., Le Tiran, L., et al. 2009, ApJ,

[699, 1660, doi: 10.1088/0004-637X/699/2/1660](http://doi.org/10.1088/0004-637X/699/2/1660)


Leroy, A., Bolatto, A. D., Simon, J. D., & Blitz, L. 2005, ApJ, 625,

[763, doi: 10.1086/429578](http://doi.org/10.1086/429578)


Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782,

[doi: 10.1088/0004-6256/136/6/2782](http://doi.org/10.1088/0004-6256/136/6/2782)


Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670,

[doi: 10.1088/0004-6256/137/6/4670](http://doi.org/10.1088/0004-6256/137/6/4670)


Levy, R. C., Bolatto, A. D., Teuben, P., et al. 2018, ApJ, 860, 92,

[doi: 10.3847/1538-4357/aac2e5](http://doi.org/10.3847/1538-4357/aac2e5)


Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415,

[doi: 10.1146/annurev-astro-081811-125615](http://doi.org/10.1146/annurev-astro-081811-125615)


Meng, X., Gnedin, O. Y., & Li, H. 2019, MNRAS, 486, 1574,

[doi: 10.1093/mnras/stz925](http://doi.org/10.1093/mnras/stz925)


Mogotsi, K. M., de Blok, W. J. G., Cald´u-Primo, A., et al. 2016,

[AJ, 151, 15, doi: 10.3847/0004-6256/151/1/15](http://doi.org/10.3847/0004-6256/151/1/15)


Molina, J., Ibar, E., Smail, I., et al. 2019, MNRAS, 487, 4856,

[doi: 10.1093/mnras/stz1643](http://doi.org/10.1093/mnras/stz1643)


Muratov, A. L., Kereˇs, D., Faucher-Gigu`ere, C.-A., et al. 2015,

[MNRAS, 454, 2691, doi: 10.1093/mnras/stv2126](http://doi.org/10.1093/mnras/stv2126)


Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L.

2012, MNRAS, 421, 3127,

[doi: 10.1111/j.1365-2966.2012.20536.x](http://doi.org/10.1111/j.1365-2966.2012.20536.x)


Obreschkow, D., Glazebrook, K., Bassett, R., et al. 2015, ApJ, 815,

[97, doi: 10.1088/0004-637X/815/2/97](http://doi.org/10.1088/0004-637X/815/2/97)


Oliva-Altamirano, P., Fisher, D. B., Glazebrook, K., et al. 2018,

[MNRAS, 474, 522, doi: 10.1093/mnras/stx2797](http://doi.org/10.1093/mnras/stx2797)


Ostriker, E. C., McKee, C. F., & Leroy, A. K. 2010, ApJ, 721, 975,

[doi: 10.1088/0004-637X/721/2/975](http://doi.org/10.1088/0004-637X/721/2/975)


Ostriker, E. C., & Shetty, R. 2011, ApJ, 731, 41,

[doi: 10.1088/0004-637X/731/1/41](http://doi.org/10.1088/0004-637X/731/1/41)

I ONIZED VS MOLECULAR GAS VELOCITY DISPERSION IN GALAXIES 19



Patr´ıcio, V., Richard, J., Carton, D., et al. 2018, MNRAS, 477, 18,

[doi: 10.1093/mnras/sty555](http://doi.org/10.1093/mnras/sty555)

Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 2024,

[doi: 10.1093/mnras/stz2338](http://doi.org/10.1093/mnras/stz2338)

Romeo, A. B., & Wiegert, J. 2011, MNRAS, 416, 1191,

[doi: 10.1111/j.1365-2966.2011.19120.x](http://doi.org/10.1111/j.1365-2966.2011.19120.x)

Shetty, R., & Ostriker, E. C. 2012, ApJ, 754, 2,

[doi: 10.1088/0004-637X/754/1/2](http://doi.org/10.1088/0004-637X/754/1/2)

Shields, G. A. 1990, ARA&A, 28, 525,

[doi: 10.1146/annurev.aa.28.090190.002521](http://doi.org/10.1146/annurev.aa.28.090190.002521)

Stott, J. P., Sobral, D., Bower, R., et al. 2013, MNRAS, 436, 1130,

[doi: 10.1093/mnras/stt1641](http://doi.org/10.1093/mnras/stt1641)

Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS,

[457, 1888, doi: 10.1093/mnras/stw129](http://doi.org/10.1093/mnras/stw129)

Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020, ApJ, 892, 148,

[doi: 10.3847/1538-4357/ab781c](http://doi.org/10.3847/1538-4357/ab781c)

Swinbank, A. M., Papadopoulos, P. P., Cox, P., et al. 2011, ApJ,

[742, 11, doi: 10.1088/0004-637X/742/1/11](http://doi.org/10.1088/0004-637X/742/1/11)

Swinbank, A. M., Harrison, C. M., Trayford, J., et al. 2017,

[MNRAS, 467, 3140, doi: 10.1093/mnras/stx201](http://doi.org/10.1093/mnras/stx201)

Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, arXiv e-prints,

arXiv:2003.06245. [https://arxiv.org/abs/2003.06245](https://arxiv.org/abs/2003.06245)



Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781,

[doi: 10.1038/nature08773](http://doi.org/10.1038/nature08773)

Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74,

[doi: 10.1088/0004-637X/768/1/74](http://doi.org/10.1088/0004-637X/768/1/74)

Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853,

[179, doi: 10.3847/1538-4357/aaa4b4](http://doi.org/10.3847/1538-4357/aaa4b4)

[Toomre, A. 1964, ApJ, 139, 1217, doi: 10.1086/147861](http://doi.org/10.1086/147861)

Torres-Flores, S., Epinat, B., Amram, P., Plana, H., & Mendes de

Oliveira, C. 2011, MNRAS, 416, 1936,

[doi: 10.1111/j.1365-2966.2011.19169.x](http://doi.org/10.1111/j.1365-2966.2011.19169.x)
¨Ubler, H., Genzel, R., Tacconi, L. J., et al. 2018, ApJL, 854, L24,

[doi: 10.3847/2041-8213/aaacfa](http://doi.org/10.3847/2041-8213/aaacfa)

¨Ubler, H., Genzel, R., Wisnioski, E., et al. 2019, ApJ, 880, 48,

[doi: 10.3847/1538-4357/ab27cc](http://doi.org/10.3847/1538-4357/ab27cc)

¨Ubler, H., Genel, S., Sternberg, A., et al. 2020, arXiv e-prints,

arXiv:2008.05486. [https://arxiv.org/abs/2008.05486](https://arxiv.org/abs/2008.05486)

White, H. A., Fisher, D. B., Murray, N., et al. 2017, ApJ, 846, 35,

[doi: 10.3847/1538-4357/aa7fbf](http://doi.org/10.3847/1538-4357/aa7fbf)

Wisnioski, E., F¨orster Schreiber, N. M., Wuyts, S., et al. 2015,

[ApJ, 799, 209, doi: 10.1088/0004-637X/799/2/209](http://doi.org/10.1088/0004-637X/799/2/209)

[Wong, T., & Blitz, L. 2002, ApJ, 569, 157, doi: 10.1086/339287](http://doi.org/10.1086/339287)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[3].provided.evidence[0]",
  "value": "F125W images used to derive stellar half-light radii",
  "failed_quote": "To obtain Σ SF R , Σ mol and Σ ⋆ for the DYNAMO galaxies, we derive the half-light radius, R 1 / 2 , by fitting an exponential profile to the H α , CO(3-2) or CO(4-3), and F125W/HST maps when available."
 },
 {
  "path": "analysis_steps[1].validation.evidence[2]",
  "value": "CO(3-2) and CO(4-3) give consistent dispersions within ±2 km s^-1; GalPaK3D dispersions agree with outer major-axis map values within ±3 km s^-1 (molecular) and ±5 km s^-1 (ionized), and with Bassett et al. (2014) and Bekiaris et al. (2016) within ±5 km s^-1.",
  "failed_quote": "Our ionized gas velocity dispersions are also in good agreement ( ± 5 km s − 1 ) with previous results obtained for the ionized gas by Bassett et al. (2014) and Bekiaris et al. (2016) using a very similar technique to model the kinematics."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Subtract thermal broadening and HII expansion (σ_th = 15 km s^-1) in quadrature from σ_0,ion, compute the ratio and log-linear fits against f_gas, and compute Spearman rank correlations with f_gas and SFR.",
  "failed_quote": "When fitting the whole sample, we obtain a fit of log( σ 0 /km s − 1 ) = a×f gas + b with a = 0 . 98 ± 0 . 17 and a = 0 . 76 ± 0 . 11 for the molecular and ionised gas, respectively, and a = 0 . 87 ± 0 . 13 when combining both molecular and ionized gas values."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Fit exponential profiles to Hα, CO, and HST F125W maps to obtain R_1/2; compute Toomre Q = σ_0 κ / (π G Σ_g), midplane hydrostatic pressure P_H, and dynamical equilibrium pressure P_DE under three tracer/α_CO assumptions, and fit the log(Σ_SFR)-log(P_H) relation.",
  "failed_quote": "To obtain Σ SF R , Σ mol and Σ ⋆ for the DYNAMO galaxies, we derive the half-light radius, R 1 / 2 , by fitting an exponential profile to the H α , CO(3-2) or CO(4-3), and F125W/HST maps when available."
 }
]
```
