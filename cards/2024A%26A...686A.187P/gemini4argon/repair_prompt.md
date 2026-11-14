# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A.187P\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy_ _&_ _Astrophysics_ manuscript no. pozzi24 ©ESO 2024
March 21, 2024

## **The ALPINE-ALMA [CII] Survey: Dust emission effective** **radius to 3 in the Universe** **up kpc Early**


F. Pozzi [1] _[,]_ [ 2], F. Calura [2], Q. D’Amato [1] _[,]_ [ 3], M. Gavarente [1], M. Bethermin [4] _[,]_ [ 5], M. Boquien [6], V. Casasola [7], A.
Cimatti [1], R. Cochrane [8] _[,]_ [ 9], M. Dessauges-Zavadsky [10], A.Enia [2], F. Esposito [1], A.L. Faisst [11], R. Gilli [2], M.
Ginolfi [12] _[,]_ [ 3], R. Gobat [13], C. Gruppioni [2], C. C. Hayward [9], E. Ibar [14], A.M. Koekemoer [15], B. C. Lemaux [16] _[,]_ [ 17], G.
E. Magdis [18] _[,]_ [ 19] _[,]_ [ 20], J. Molina [14], M. Talia [1], L. Vallini [2], D. Vergani [2], G. Zamorani [2]


1 Dipartimento di Fisica e Astronomia, Universitá di Bologna, via Gobetti 93/2, 40129, Bologna, Italy, email:
f.pozzi@unibo.it
2 INAF – Osservatorio di Astrofisica e Scienza dello Spazio di Bologna, via Gobetti 93/3, 40129, Bologna, Italy
3 INAF – Osservatorio Astrofisico di Arcetri Firenze, via Largo Enrico Fermi 5, Firenze, Italy
4 Université de Strasbourg, CNRS, Observatoire astronomique 414 de Strasbourg, UMR 7550, 67000 Strasbourg,
France
5 Aix Marseille Univ, CNRS, CNES, LAM, Marseille, France
6 Université Côte d’Azur, Observatoire de la Côte d’Azur, CNRS, Laboratoire Lagrange, 06000, Nice, France
7 INAF – Istituto di Radioastronomia Bologna, via Gobetti 111, 40129, Bologna, Italy
8 Department of Astronomy, Columbia University, New York, NY 10027, USA
9 Center for Computational Astrophysics, Flatiron Institute, 162 Fifth Avenue, New York, NY 10010, USA
10 Department of Astronomy, University of Geneva, Chemin Pegasi 51, 1290 Versoix, Switzerland
11 Infrared Processing and Analysis Center, California Institute of Technology, Pasadena, CA 91125, USA
12 Dipartimento di Fisica e Astronomia, Università degli Studi di 470 Firenze, Via G. Sansone 1,I-50019, Sesto
Fiorentino, Firenze, Italy 471
13 Instituto de Física, Pontificia Universidad Católica de Valparaíso, Casilla 4059, Valparaíso, Chile
14 Instituto de Física y Astronomía, Universidad de Valparaíso, Avda. Gran Bretaña 1111, Valparaíso, Chile
15 Space Telescope Science Institute, Baltimore, MD 21218, USA
16 Department of Physics and Astronomy, University of California 454, Davis, One Shields Avenue, Davis, CA 95616,
USA 455
17 Cosmic Dawn Center (DAWN), Jagtvej 128, DK2200 Copenhagen 456 N, Denmark
18 DTU-Space, Technical University of Denmark, Elektrovej 327, 458 DK2800 Kgs. Lyngby, Denmark 459
19 Niels Bohr Institute, University of Copenhagen, Jagtvej 128, DK- 460 2200 Copenhagen N, Denmark


Received December 18, 2023; accepted March 20, 2024


**ABSTRACT**


_Aims._ Measurements of the size of dust continuum emission are an important tool for constraining the spatial extent of
star formation and hence the build-up of stellar mass. Compact dust emission has generally been observed at Cosmic
Noon ( _z_ _∼_ 2 _−_ 3). However, at earlier epochs, toward the end of the Reionization ( _z_ _∼_ 4 _−_ 6), only the sizes of a handful
of IR-bright galaxies have been measured. In this work, we derive the dust emission sizes of main-sequence galaxies at
_z_ _∼_ 5 from the ALPINE survey.
_Methods._ We measure the dust effective radius _r_ _e,F IR_ in the uv-plane in Band 7 of ALMA for seven ALPINE galaxies
with resolved emission and we compare it with rest-frame UV and [CII]158 _µ_ m measurements. We study the _r_ _e,F IR_ _−_ L _IR_
scaling relation by considering our dust size measurements and all the data in literature at _z_ _∼_ 4 _−_ 6. Finally, we compare
our size measurements with predictions from simulations.
_Results._ The dust emission in the selected ALPINE galaxies is rather extended ( _r_ _e,F IR_ _∼_ 1 _._ 5 _−_ 3 kpc), similar to

[CII]158 _µ_ m but a factor of _∼_ 2 larger than the rest-frame UV emission. Putting together all the measurements at _z_ _∼_ 5,
spanning 2 decades in luminosity from L _IR_ _∼_ 10 [11] L _⊙_ to L _IR_ _∼_ 10 [13] L _⊙_, the data highlight a steeply increasing trend
of the _r_ _e,F IR_ _−_ L _IR_ relation at L _IR_ _<_ 10 [12] L _⊙_, followed by a downturn and a decreasing trend at brighter luminosities.
Finally, simulations that extend up to the stellar masses of the ALPINE galaxies considered in the present work predict
a sub-set of galaxies ( _∼_ 25 % at 10 [10] M _⊙_ _<_ M _⋆_ _<_ 10 [11] M _⊙_ ) with sizes as large as those measured.


**Key** **words.** galaxies: high-redshift — galaxies: ISM — ISM: dust



**1.** **Introduction**


The size of dust continuum emission in the far-IR (FIR)
rest-frame regime gives key information on the spatial extension of the dust-obscured star formation within galax


ies, hence providing important constraints on their stellar
build-up.


Nowadays, thanks to the Atacama Large
Millimeter/Sub-millimeter array (ALMA), a significant
number of studies of the far-IR emission sizes have been


Article number, page 1 of 8

_A&A_ _proofs:_ manuscript no. pozzi24



performed at the Cosmic Noon ( _z_ _∼_ 2) pointing towards
compact dust emission (effective radius _r_ _e,F IR_ _<_ 1 _−_ 2
kpc), typically more compact than the rest-frame optical/UV imaging (e.g. Barro et al. 2016; Tadaki et al. 2017,
Talia et al. 2018, Franco et al. 2020). The compaction
of the dust continuum sizes has been interpreted as a
sign of dust-obscured build-up of a central dense stellar
component, either through the secular funneling of gas
towards the center (e.g. Dekel et al. 2013) or through
gas-rich mergers (e.g. Puglisi et al. 2021). These studies
focus mainly on dusty, massive and FIR-bright galaxies
while there are some hints that at fainter luminosities dust
emission is more extended (e.g. Rujopakarn et al. 2016,
Cheng et al. 2020).
At very high redshift, measuring the dust emission size
is very challenging due to limited spatial resolution and
sensitivity. Few studies are available for sources emerging
shortly after the Epoch of Reionization (4 _< z_ _<_ 6). These
studies include Gómez-Guijarro et al. (2022a), who studied 6 sources in the GOODS-ALMA 2.0 survey at 1.1 mm;
Jin et al. (2022) who considered 6 galaxies from the superdeblended catalogues in COSMOS and GOODS-North (Jin
et al. 2018, Liu et al. 2018) and Cooke et al. (2018),
where the dust continuum sizes of 6 stacked luminous SubMillimeter Galaxies have been presented. These works support the very compact dust continuum sizes found at lower
redshifts, however the samples still rely on poor statistics
and only the bright IR tail of galaxies has been probed
(L _IR_ (8 _−_ 1000 _µ_ m) - 10 [12] L _⊙_ ). An exception is the recent
work from Witstok et al. (2022), which presented the properties of the ISM of 5 Lyman Break Galaxies (LBGs) at
very high _z_ ( _z_ _∼_ 7), characterised by moderate IR luminosity (L _IR_ _∼_ 10 [11] L _⊙_ ).
We aim to improve our understanding of the dust emission sizes at high _z_ (4 _< z_ _<_ 6) by taking advantage of the
completed ALMA Large program to INvestigate [CII] at
Early times (ALPINE, see Le Fèvre et al. 2020, Béthermin
et al. 2020, Faisst et al. 2020). The goal of this program
was to observe the prominent [CII] 158 _µ_ m line and farIR continuum emission for 118 UV-selected normal starforming galaxies at _z_ _∼_ 4 _._ 4 _−_ 5 _._ 8. The present study increases the number of sources with measured dust continuum sizes at very high _z_ and, given the lower IR luminosity
range spanned by the ALPINE galaxies, better constrains
the _r_ _e,F IR_ -L _IR_ scaling relation.
The paper is organised as follows. In Sect. 2 we describe
our data analysis. We then present our result in Sect. 3.
Finally, we discuss them and conclude in Sect. 4. Throughout the paper, we assume a flat ΛCDM cosmology with
Ω _m_ = 0 _._ 3, Ω _λ_ = 0 _._ 7 and _h_ 0 = 0 _._ 7.


**2.** **Sample,** **observations** **and** **data** **analysis**


The parent sample of galaxies analysed in this paper is
the subset of 23 objects with a _∼_ 158 _µ_ m continuum detection in the ALPINE survey (Béthermin et al. 2020). The
ALPINE survey aimed to study the _∼_ 158 _µ_ m [CII] and the
rest-frame FIR continuum emission of 118 Main-Sequence
(MS) rest-frame UV selected galaxies at _z_ _∼_ 4 _._ 4 _−_ 5 _._ 9, in
the COSMOS (Scoville et al. 2007) and ECDFS (Giacconi
et al. 2002) fields. For an overall description of the survey
we refer to Le Fèvre et al. (2020); for the data reduction
we refer to Béthermin et al. (2020); for the description of
the ancillary spectra and photometric data and the physi

Article number, page 2 of 8



**Fig.** **1.** SFR versus M _⋆_ for the ALPINE targets (red circles indicate galaxies with a FIR size measurement from the present
work) and for our compilation of dust continuum measured sizes
from literature in a similar redshift range 4 _<_ _z_ _<_ 6 (blue circles: COSMOS/GOODS-North galaxies from super-deblended
catalogues (Jin et al. 2022, ; cyan circles: galaxies from the
GOODS-ALMA 2.0 survey (Gómez-Guijarro et al. 2022a); red
empty squares: galaxies from the CRISTAL survey (Mitsuhashi
et al. 2023). For the CRISTAL sources not belonging to the
ALPINE survey, we use the SFR and M _⋆_ values as reported in
Table 1 from Mitsuhashi et al. (2023). The violet shaded region
represents the 1 _σ_ range of the MS relation found by Cole et al.
(2023) in the redshift range closer to the data (4 _._ 5 _< z_ _<_ 5) and
obtained using the SFR values derived by averaging the star formation histories over 100 Myrs timescales (see Table 2 in Cole
et al. 2023); the pink shaded region represents the MS relation
and its 1 _σ_ dispersion found by Speagle et al. (2014) and computed, for consistency, at _z_ = 4 _._ 75

.


cal properties obtained from the UV-to-optical SED-fitting,
we refer to Faisst et al. (2020). The stellar masses (M _⋆_ )
and the star formation rates (SFR) of the ALPINE galaxies are in the range M _⋆_ = 10 [8] _[.]_ [4] _−_ 10 [11] M _⊙_ and 1 _._ 5 _−_ 270
M _⊙_ /yr, respectively. The stellar masses M _⋆_ are from Table
A1 of Faisst et al. (2020) and derived from the SED-fitting;
as SFR we consider SFR _UV_ + _IR_, i.e. the sum of the unobscured (SFR _UV_ ) and obscured (SFR _IR_ ) star formation. We
derive SFR _UV_ from the UV luminosity at 1500 Å (Faisst
et al. 2020) uncorrected for dust, and SFR _IR_ from the IR
luminosity reported in Béthermin et al. (2020).
In Fig. 1 we report the ALPINE galaxies on the
SFR _−M_ _⋆_ plane. For the galaxies not detected in continuum, following Dessauges-Zavadsky et al. (2020), we consider only SFR _UV_ . As found by Schaerer et al. (2020) by
studying the UV-continuum slope, this assumption can underestimate the total SFR by a factor of 2. In Fig. 1,
together with the ALPINE targets, we report the galaxies with measured continuum sizes in the redshift range
4 _< z_ _<_ 6 (see Gómez-Guijarro et al. 2022a, Jin et al. 2022).
Moreover, as a reference, we report the MS relation from
Cole et al. (2023), recently derived using JWST data from
Cosmic Evolution Early Release Science (CEERS, Finkelstein et al. 2022, Bagley et al. 2023) and consistent, within

F. Pozzi, F. Calura et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe



1 _σ_ with the pre _−_ JWST derivation from Speagle et al.
(2014). Over the 23 ALPINE continuum sources, 3 galaxies
are classified in the continuum images as multi-components
objects (VC_5101209780,VE_530029038, DC_881725, see
Béthermin et al. 2020 ). These systems can indicate the
presence of a merger or a very patchy and disturbed galaxy
where can be quite difficult to constrain a center of the system and the determination of the size. For this reason, we
choose to remove these galaxies from our analysis. Therefore, our sample consists of 20 ALPINE galaxies. Among
these sources, 18 over 20 are detected in [CII], while for 2
sources only upper limits in [CII] are available.


_2.1._ _Size_ _measurement_


In order to measure the continuum sizes of the targets, we
adopted the procedure outlined in Fujimoto et al. (2020)
to measure the sizes of the [CII] emission of the ALPINE
targets. First of all, we remove from the visibility data the
channels containing the [CII] emission. We then produce
the continuum maps with the CASA [1] (CASA Team et al.
2022) task TCLEAN and we run in CASA the task IMFIT
to achieve a first guess of the target’s properties (positions,
fluxes and sizes). These outputs, obtained in the imageplane, are used as first guess for the proper size measurements in the uv-plane, where we assume a 2-dimensional
Gaussian model for the intensity profile and we measure
the sizes with the CASA task UVMODELFIT. The latter returns the de-convolved FWHM along the major and
minor axis (FWHM _maj_, FWHM _min_ ) that we circularise as
FWHM _circ_ = �FWHM _min_ _×_ FWHM _maj_ ). The effective radius _r_ _e_, which represents the radius that encloses half of the
total light, is then derived as _r_ _e_ =FWHM _circ_ /2 (see Voigt
& Bridle 2010 for a Gaussian profile corresponding to a
Sérsic index _n_ =0.5). Fujimoto et al. (2020) describe how
a Gaussian profile return an effective radius _r_ _eff_ consistent at a 5% level with a more reliable exponential shape
(corresponding to a Sérsic index _n_ =1). We applied the described procedure to sources detected in the continuum at
_S/N_ _>_ 4 _._ 5 to obtain reliable measurements. Given this cut
in _S/N_, our final sample is composed of 12 galaxies. All
but one of the 12 galaxies have continuum _S/N_ _>_ 4 _._ 5 (see
Table 1), and this gives us confidence of meaningful size
measurements (Fujimoto et al. 2020).
In Table 1 we report our size measurements. For 7
sources the fitting procedure returns a de-convolved FWHM
along the minor and major axes, and we obtain a circularized effective radius ( _r_ _e,F IR_ ). We also visually check the
observed, model and residual maps in the image plane to
exclude multi-components below the scale of the beam (see
Fig. 2). We note that for source DC_818760, constituted
by three galaxies (see Jones et al. 2020 and Devereaux et al.
2023), we measure and report the size of the central galaxy.
For the remaining sources, since the fitting procedure reports de-convolved FWHM uncertainties larger or similar
to the de-convolved FWHM measures, we estimate the size
upper limit from the formula by Martí-Vidal et al. (2012)
considering for the likelihood _λ_ _c_ a value equal to 9 corresponding to a 3 _σ_ cut-off. We note that 3 resolved sources
(DC_818760, DC_848185, DC_873756) are in common
with the recent results from the CRISTAL survey (Mit

1 Common Astronomy Software Application. `[https://casa.](https://casa.nrao.edu/)`
```
nrao.edu/

```


suhashi et al. 2023) and the size measurements are consistent within 1 _σ_ . Among the 5 unresolved sources, 2 sources
(DC_683613, VC_5100822662) have a measured size in the
CRISTAL sample consistent with our upper limits. The
sources in common are highlighted in Table 1. In Table
1 along with _r_ _e,F IR_, we report the circularized effective radius of the [CII] line emission ( _r_ _e,_ [ _CII_ ] ) and of the rest-frame
UV emission ( _r_ _e,UV_ ). These radii were derived by Fujimoto
et al. (2020) as follows: the [CII] radius from the ALMA
ALPINE data using the CASA UVMODEL task described
above; the rest-frame UV emission from the F814W HST
map (Koekemoer et al. 2007) and the F160W HST maps
(Koekemoer et al. 2011) using the GALFIT task (Peng
et al. 2010). We only consider reliable size measurements

_−_
(flag=0). Finally, in Table 1 we give the rest frame optical
radius _r_ _e,opt_ derived from the empirical stellar mass _−_ size relation found recently by the JWST CEERS survey (Ward
et al. 2023), given the stellar masses of our galaxies. We
consider the mass _−_ size relation in the redshift range closer
to our data (3 _._ 5 _< z_ _<_ 5, see Table 1 in Ward et al. 2023).


**3.** **Results**


_3.1._ _FIR,_ _[CII]_ _and_ _UV_ _sizes_


In Fig. 3 we report the _r_ _e,F IR_ of the 12 ALPINE targets
considered in this work with a _S/N_ _>_ 4 _._ 5 continuum detection (upper limits for the unresolved sources are displayed
as open circles). In the left panel _r_ _e,F IR_ is presented as a
function of M _⋆_, in the middle panel as a function of the
rest-frame UV sizes _r_ _e,UV_ and of the optical radius _r_ _e,opt_
as derived by the JWST stellar mass _−_ size relation (Ward
et al. 2023), and in the right panel as a function of the [CII]
sizes _r_ _e,_ [ _CII_ ] .
We find the median value to be _r_ _e,F IR_ = (2 _._ 13 _±_ 0 _._ 26)
kpc, and the ratios _r_ _e,UV_ _/r_ _e,F IR_ = (0 _._ 39 _±_ 0 _._ 15) and
_r_ _e,_ [ _CII_ ] _/r_ _e,F IR_ = (1 _._ 29 _±_ 0 _._ 14), calculated considering only
the 7 rest-frame FIR resolved sources and the 5(4) galaxies with measured _r_ _e,UV_ ( _r_ _e,_ [ _CII_ ] . The median ratio of the
dust continuum sizes over the optical ones derived from
the mass _−_ size relation is _r_ _e,opt_ _/r_ _e,F IR_ = 1 _._ 10 _±_ 0 _._ 26. The
_r_ _e,F IR_ sizes are larger than those found for brighter FIR
sources at similar redshifts (see the review from Hodge &
da Cunha 2020 and references therein). They are slightly
smaller than the [CII] sizes, tracing both the atomic and
the molecular gas, and significantly larger (a factor of 2.5)
than the rest-frame UV sizes, opposed to what has been
found by other authors ( _r_ _e,HST_ _/r_ _e,ALMA_ = 1 _._ 6 for galaxies
at 1 _<_ _z_ _<_ 6 taken from the ALMA archive by Fujimoto
et al. 2017; _r_ _e,HST_ _/r_ _e,ALMA_ = 2 _._ 3 for a compilation of massive galaxies at _z_ = 2 _−_ 4 in the GOODS-S by Franco et al.
2020) and in agreement with results from CRISTAL survey (Mitsuhashi et al. 2023). Moreover, our _r_ _e,UV_ _/r_ _e,F IR_
are significant smaller (up to a factor of 5-10) than the
values predicted by the hydrodynamical cosmological simulations from Popping et al. (2022) and extrapolated at
the stellar masses of our galaxies. This suggests that the
model from Popping et al. (2022) could predict too compact FIR dust emission extension. Finally, we find that the
dust continuum sizes are very close to the optical ones,
as predicted from the JWST mass _−_ size relation, pointing
towards a quite extended, disk-like star-formation region
traced by the IR emission, very similar to the region traced
by the rest-frame optical emission. We will discuss in Sect.


Article number, page 3 of 8

_A&A_ _proofs:_ manuscript no. pozzi24


Name _z_ _r_ _e,F IR_ _r_ _e,_ [ _CII_ ] _r_ _e,UV_ _logM_ _⋆_ _SFR_ _S/N_

[kpc] [kpc] [kpc] [log 10 (M/M _⊙_ )] [M _⊙_ /yr]
CG_19 4.500 _<_ 1.40 . . . . . . 9.83 [+0] _−_ 0 _[.]_ _._ [07] 05 66.5 [+13] _−_ 11 _[.]_ _._ [5] 0 5.4
DC_396844 4.540 2.13 _±_ 1.10 2.56 _±_ 0.33 0.58 _±_ 0.20 9.86 [+0] _−_ 0 _[.]_ _._ [14] 19 83.9 [+16] 13 _._ 8 _[.]_ [6] 5.6
DC_488399 5.678 _<_ 1.17 1.32 _±_ 0.16 . . . 10.20 [+0] _−_ 0 _[.]_ _._ [13] 15 89.8 [+14] _−_ 13 _[.]_ _._ [9] 1 9.3
DC_494057 5.540 _<_ 1.16 2.48 _±_ 0.25 0.59 _±_ 0.17 10.15 [+0] _−_ 0 _[.]_ _._ [13] 15 77.8 [+16] _−_ 13 _[.]_ _._ [1] 8 7.1
DC_552206 5.514 3.08 _±_ 1.25 . . . . . . 10.58 [+0] _−_ 0 _[.]_ _._ [14] 16 114.9 [+29] _−_ 23 _[.]_ _._ [6] 3 4.5
DC_683613 _[a]_ 5.536 _<_ 1.65 1.82 _±_ 0.33 0.57 _±_ 0.24 10.17 [+0] _−_ 0 _[.]_ _._ [14] 15 75.6 [+18] _−_ 14 _[.]_ _._ [6] 9 _[|]_ 5.1
DC_818760 _[a]_ 4.554 2.70 _±_ 0.55 2.59 _±_ 0.16 1.07 _±_ 0.21 _[b]_ 10.63 [+0] _−_ 0 _[.]_ _._ [11] 10 235.1 [+28] _−_ 25 _[.]_ _._ [6] 5 9.5
DC_848185 _[a]_ 5.284 1.90 _±_ 0.30 . . . . . . 10.37 [+0] _−_ 0 _[.]_ _._ [08] 19 113.0 [+16] _−_ 14 _[.]_ _._ [0] 3 7.1
DC_873756 _[a]_ 4.548 1.58 _±_ 0.20 2.36 _±_ 0.11 1.08 _±_ 0.43 10.25 [+0] _−_ 0 _[.]_ _._ [08] 10 268.7 [+16] _−_ 15 _[.]_ _._ [7] 5 21.7
VC_5100822662 _[a]_ 4.523 _<_ 1.16 2.59 _±_ 0.37 1.32 _±_ 0.33 10.17 [+0] _−_ 0 _[.]_ _._ [13] 14 60.8 [+10] _−_ 9 _._ 0 _[.]_ [5] 6.5
VC_5101218326 4.568 1.83 _±_ 0.40 2.37 _±_ 0.15 1.46 _±_ 0.32 11.01 [+0] _−_ 0 _[.]_ _._ [07] 05 120.0 [+18] _−_ 15 _[.]_ _._ [0] 6 6.5
VC_5180966608 4.529 2.60 _±_ 0.60 no data 0.59 _±_ 0.24 _[b]_ 10.82 [+0] _−_ 0 _[.]_ _._ [12] 13 96.9 [+19] _−_ 16 _[.]_ _._ [5] 0 5.7
**Table** **1.** Column (1): ALPINE source name. We only list the 12 sources with a _S/N_ of the continuum _>_ 4 _._ 5 (see Béthermin et al.
2020) that are considered in our analysis. The three sources classified in Béthermin et al. (2020) as multi-components objects have
not been considered. The (a) symbol indicates galaxies in common with he CRISTAL sample (Mitsuhashi et al. 2023). Column
(2): spectroscopic redshift from the [CII] line emission. Column (3): dust continumm effective radius (see text for details). Column
(4): [CII] line emission effective radius (Fujimoto et al. 2020). Column (5): rest-frame UV effective radius (Fujimoto et al. 2020).
The (b) symbol indicates that the HST/F160W map has been considered, otherwise the radius from the HST/F814W maps have
been reported. Column (6), Column (7): stellar mass and SFR (see text for details). Column (8): Continuum S/N at 158 _µ_ m from
Béthermin et al. (2020).


**Fig.** **2.** Rest-frame FIR size measurements for the 7 resolved ALPINE sources using the CASA task UVMODELFIT. For every
source, the three panels are, from left to right, the observed, modelled, and residual maps, respectively, all with a 10 _[′′]_ _×_ 10 _[′′]_ size.


Article number, page 4 of 8

F. Pozzi, F. Calura et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe


**Fig.** **3.** Left: Effective radius _r_ _e,F IR_ vs. stellar mass M _⋆_ . Centre: _r_ _e,F IR_ vs. _r_ _e,UV_ . The blue symbols represent the _r_ _e,F IR_ vs.
the optical radius _r_ _e,opt_, with _r_ _e,opt_ from the empirical JWST mass _−_ size relation (Ward et al. 2023) given the stellar masses of
our sources. Right: _r_ _e,F IR_ vs. _r_ _e,_ [ _CII_ ] . The ALPINE galaxies continuum detected at S/N - 4.5 have been considered for the size
analysis. The unresolved sources are reported as empty circles. Both _r_ _e,UV_ and _r_ _e,_ [ _CII_ ] are from Fujimoto et al. (2020) and only
the sources with a reliable measurements (flag=0) have been considered.


3.2 our findings in comparison with other results from literature and predictions from models.


_3.2._ _FIR_ _sizes_ _versus_ _IR_ _luminosity_ _and_ _stellar_ _masses_



The study of scaling relations from infrared data stands as
a cornerstone in astrophysics, offering a comprehensive perspective on the properties of galaxies related to their coldest components, i.e. neutral gas, molecular gas and dust
(Calura et al. 2017; Herrera-Camus et al. 2018; Casasola
et al. 2020; Pastrav 2020). A poorly explored, yet crucial
quantity, is the size of dust emission in high-redshift galaxies. In this work, we aim to leverage this essential parameter
to investigate pivotal scaling relations, i.e. the ones between
size vs luminosity and size vs. stellar mass.
In Fig. 4, we report our measures of _r_ _e,F IR_ as a function of the IR luminosity L _IR_ . Here, L _IR_ has been computed
from the rest-frame 158 _µ_ m emission assuming the Béthermin et al. (2017) SED.
Together with our measurements, we report all the available rest-frame FIR size measurements from the literature
at similar redshifts (4 _<_ _z_ _<_ 6). To avoid bias introduced
by the radial gradient in dust temperature (e.g. Calistro
Rivera et al. 2018; Cochrane et al. 2019), we consider galaxies observed at nearly the same wavelengths of the ALPINE
galaxies (0 _._ 8 _−_ 1 mm): this allows us to sample the restframe continuum emission at the same frequencies, given
the same redshift range. In blue symbols we show the measurements from the GOODS-ALMA 2.0 survey (GómezGuijarro et al. 2022a). The GOODS-ALMA 2.0 survey is
an ALMA blind survey at 1.1 mm covering an area of 72.42
arcmin [2] . The rest-frame FIR sizes were derived with a circular Gaussian model fit in the uv-plane, and combining
the low and high-resolution observations, leading to an average resolution of 0.447 _[′′]_ _×_ 0.418 _[′′]_ . Among the 88 blind detected sources in the GOODS-ALMA 2.0 survey, 4 sources
satisfy our adopted selection criteria (4 _<_ _z_ _<_ 6), with
the redshift _z_ estimated from photometry (Gómez-Guijarro
et al. 2022a). In cyan symbols we report the dust continuum sizes of 6 galaxies from the super-deblended COSMOS
and GOODS-North catalogues, selected for their very high



**Fig.** **4.** Effective radius _r_ _e,F IR_ vs. IR luminosity L _IR_ at
4 _<_ _z_ _<_ 6 for this sample and from the literature. Red circles: ALPINE survey; blue circles: GOODS-ALMA 2.0 survey
(Gómez-Guijarro et al. 2022a); cyan circles: super-deblended
catalogs in the COSMOS and GOODS-North fields (Jin et al.
2022); red open squares: CRISTAL survey (Mitsuhashi et al.
2023).The dark-green shaded region represents the 1 _σ_ range of
the relation found by Fujimoto et al. (2017); the green lines and
the shaded region represent the relation and its 1 _σ_ dispersion
found by Jin et al. (2022). Pink empty squares are simulation
results from Cochrane et al. (2023) in the range 4 _< z_ _<_ 6.


photometric redshift ( _z_ - 6, Jin et al. 2022). Thanks to the
detection of [CI](1-0) and CO transitions, the authors were
able to measure the spectroscopic redshifts and among the
6 sources, 4 sources satisfy our criteria (4 < _z_ < 6). The
dust continuum sizes are derived from 870 _µ_ m and 1 mm
ALMA data.

We also report as red open squares the recent measurements from Mitsuhashi et al. (2023) from the CRISTAL


Article number, page 5 of 8

_A&A_ _proofs:_ manuscript no. pozzi24



survey (see Herrera-Camus et al. in prep. for the survey
paper). The CRISTAL survey is composed by 24 target
galaxies, of which 20 from the ALPINE survey (5 in common with the sample analysed in the present work, see Table 1). This survey has been carried out at the same wavelengths of the ALPINE survey (Band 7: 0 _._ 8 _−_ 1 mm), but
at higher spatial resolution ( _∼_ 0 _._ 3 _[′′]_ ). As clear from Fig.
4, the CRISTAL sample probes the faintest galaxies studied so far, with FIR luminosities down to L _IR_ _∼_ 10 [11] _L_ _⊙_,
while our data probe a luminosity domain scarcely populated by the dataset of Mitsuhashi et al. (2023); in this
regard, the CRISTAL sample and the ALPINE dust continuum resolved sources from the present work are complementary. The analysis of a dataset that probes bright galaxies alongside another one probing fainter counterparts, all
at similar redshifts, provides us with a comprehensive understanding, allowing us to characterise different trends of
the _r_ _e,F IR_ _−_ L _IR_ relation in distinct regimes of luminosity
and size.
In Fig. 4, we report for comparison 2 relations: the one
found by Fujimoto et al. (2017) (dark-green shaded region,
representing the 1 _σ_ dispersion) and the one of Jin et al.
(2022) (green line with its 1 _σ_ dispersion displayed as shaded
region). The result of Fujimoto et al. (2017) is based on a
large sample of galaxies from the ALMA archive. Considering the sources all together (0 _< z_ _<_ 6), these authors find a
positive correlation between _r_ _e,F IR_ and L _IR_ ( _r_ _e,F IR_ _∝_ _L_ _[α]_ _IR_
with _α_ = 0 _._ 28 _±_ 0 _._ 07).
This correlation is confirmed by the authors also in the
highest redshift range considered (2 _<_ _z_ _<_ 4). Fujimoto
et al. (2017) discussed that the origin of the _r_ _e,F IR_ _−_ L _IR_
relation could be related to the formation of stellar disks,
since the IR slope is similar to the slope observed in the
UV band, the latter explained by the predictions of disk
formation models (i.e. van der Wel et al. 2014). On the
other side, the relation from Jin et al. (2022) is based on a
different compilation of measurements at _z_ _>_ 1: the 6 galaxies analysed in their work, the galaxies from the GOODSALMA (Franco et al. 2020; Gómez-Guijarro et al. 2022a)
and a sample of MS galaxies at _z_ = 1 _−_ 2 (Valentino et al.
2020). Opposite to Fujimoto et al. (2017), in the latter work
the authors find an anti-correlation between the dust size
and L _IR_ (log(FWHM size/kpc)= _−_ 0.38 _×_ log (L _IR_ _/_ 10 [10]
L _⊙_ )+1.42), indicating that galaxies with higher luminosities tend to have a more compact dust morphology.
In Fig. 4 we also show as pink empty squares the predictions from high-resolution, cosmological zoom-in simulations in a similar redshift range as sampled by the data
(4 _<_ _z_ _<_ 6). These predictions are drawn from the FIRE
(Hopkins et al. 2018) suite described in Cochrane et al.
(2023) and were generated using the radiative transfer
methods described by Cochrane et al. (2019), but extending
the sample to lower FIR luminosities. To properly compare
the model predictions to the data, we consider the observedframe 850 _µ_ m emission sizes.
Concerning the data, a positive correlation between
_r_ _e,F IR_ and L _IR_ is supported at faint luminosities by the
ALMA-CRISTAL data. On the other hand, across a luminosity range wider than 1 dex and extending from L _IR_ _∼_
10 [11] _[.]_ [5] L _⊙_ to L _IR_ = 2 _×_ 10 [13] L _⊙_, our measurements, together
with the Jin et al. (2022) and Gómez-Guijarro et al. (2022b)
data, support an anti-correlation between _r_ _e,F IR_ and L _IR_
as found by Jin et al. (2022), at odd with the results from
Fujimoto et al. (2017). We are aware of the small number


Article number, page 6 of 8



**Fig.** **5.** Effective radius _r_ _e,F IR_ vs. stellar mass M _⋆_ at 4 _< z_ _<_ 6
for this sample and from the literature. Symbols as in Fig. 4.
Magenta and violet lines (with shaded regions marking the 1 _σ_
scatter) represent the predictions from Popping et al. (2022) for
_z_ = 4 and for _z_ = 5 galaxies, respectively; pink empty squares
are the predictions from Cochrane et al. (2023) in the range
4 _< z_ _<_ 6.


of galaxies with a measured dust continuum size at high_z_ ( _>_ 4) and high-L _IR_ ( _>_ 10 [11] _[.]_ [5] L _⊙_ ); anyway, we caution
the reader of possible observational biases which may affect the Fujimoto et al. (2017) relation, given the sample
inhomogeneity in terms of spatial resolution and sensitivity
and the use of photometric redshift for deriving sizes and
L _IR_ . Moreover, both the Jin et al. (2022) and Fujimoto
et al. (2017) relations are obtained from samples including
galaxies at lower _z_ than the range considered in this work
(4 _<_ _z_ _<_ 6), and are both derived for IR-bright galaxies
(L _IR_ _>_ 10 [11] _[.]_ [4] and _>_ 10 [12] L _⊙_, respectively).
Altogether, our results might suggest a variable trend
of FIR luminosity as a function of size, that ranges from
an increase for faint objects, a downturn at some characteristic luminosity of the order of 10 [12] L _⊙_, followed by a
decreasing trend at brighter luminosities. A similar trend
is shown also by the compilation of measures of Mitsuhashi
et al. (2023), across a wider redshift range (2 _≤_ _z_ _≤_ 6). The
predictions from the zoom-in simulations (Cochrane et al.
2023) cover a broader range in dust continuum sizes than
the data but, as the measurements, they present a characteristic IR luminosity around 10 [12] L _⊙_, above which the
sizes decrease. Understanding the physical reason of this
downturn and accounting for the characteristic luminosity
value at which it occurs will be a major challenge for galaxy
formation models.
In Fig. 5 we report our _r_ _e,F IR_ as a function of the stellar mass M _⋆_ . As in Fig. 4, along with our measurements,
we show the other samples with dust continuum sizes measured in the literature at _z_ _>_ 4, from the GOODS-ALMA
2.0 survey (Gómez-Guijarro et al. 2022a), from the super
deblended catalogues in the COSMOS and GOODS-North
fields (Jin et al. 2022) and from the CRISTAL survey (Mitsuhashi et al. 2023).

F. Pozzi, F. Calura et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe



In Fig. 5 together with the predictions from Cochrane
et al. (2023) (pink empty squares for galaxies in the range
4 _<_ _z_ _<_ 6) we also report the predictions from Popping
et al. (2022) (magenta and violet lines with shaded regions
marking the 1 _σ_ scatter, for _z_ = 4 and _z_ = 5 galaxies, respectively). The predictions from Popping et al. (2022) are
derived from the TNG50 simulations (Nelson et al. 2019;
Pillepich et al. 2019), the highest resolution implementation
of the magnetohydrodynamical cosmological simulation IllustrisTNG (see Springel et al. 2018; Marinacci et al. 2018).
Also for these predictions, we consider the observed-frame
850 _µ_ m emission sizes. Results for galaxy stellar masses up
to _∼_ 10 [10] _[.]_ [4] and _∼_ 10 [11] _[.]_ [4] M _⊙_ have been reported in the Popping et al. (2022) and Cochrane et al. (2019) simulations,
respectively. The stellar mass range of our galaxies is not
sampled in the volume of the Popping et al. (2022) simulation. At masses _<_ 10 [10] M _⊙_, the model from Popping
et al. (2022) predicts compact dust emission sizes ( _<_ 1 _−_ 2
kpc), similar to those observed in some CRISTAL galaxies
(Mitsuhashi et al. 2023).
At masses _>_ 10 [10] M _⊙_, a subset of model sources ( _∼_ 25%
in the range 10 [10] M _⊙_ _<_ M _⋆_ _<_ 10 [11] M _⊙_ ) from Cochrane
et al. (2023) are predicted with large sizes, in the range of
1 _._ 5 _−_ 4 kpc, populating the upper envelope of the distribution and in agreement with the ALPINE galaxies analysed
in the present work.


**4.** **Discussion** **and** **Summary**


Our study of the main-sequence ALPINE galaxies at _z_ _∼_ 5
shows effective radius _r_ _e,F IR_ of 1 _._ 5 _−_ 3 kpc, a factor of two
larger than what is observed in brighter IR sources at similar _z_ . We confirm, in fact, the anti-correlation found by Jin
et al. (2022) between the dust size and the IR luminosity
in the L _IR_ range between _∼_ 10 [11] _[.]_ [5] L _⊙_ and _∼_ 2 _×_ 10 [13] L _⊙_ .
A possible explanation for the anti-correlation is ascribed
to galaxies caught at different phases of their star formation history, all within the scatter of the main-sequence
(e.g. Sommovigo et al. 2021; Gómez-Guijarro et al. 2022b;
Vallini et al. 2024). In this picture, the ALPINE galaxies
are characterised by a mild SFR, a more extended (possibly
disk-like) star formation region, while IR brighter galaxies are characterised by an enhanced SFR, short depletion
time, and high dust temperatures. To validate this scenario,
we consider the depletion times ( _t_ _depl_ ) and the gas fractions ( _f_ _gas_ = _M_ _⋆_ _M_ + _g_ _M_ _asgas_ [)] [for] [the] [ALPINE] [galaxies] [with] [a]
measured dust size, derived by Dessauges-Zavadsky et al.
(2020) from the [CII] luminosities: _t_ _depl_ = (456 _±_ 57) Myrs
and _f_ _gas_ = 0 _._ 6 _±_ 0 _._ 2. These values are in agreement with
those derived from Gómez-Guijarro et al. (2022b) for normal star-forming galaxies with an extended star-forming
region, as opposite to the typical values of starburst galaxies, characterised by a more compact emission, shorter _t_ _depl_
(of the order of 10-100 Myrs, see also Silverman et al. 2015,
Scoville et al. 2023) and lower gas fraction (in the range
0.25-0.5, see Fig. 3 in Gómez-Guijarro et al. 2022b). Our
finding is in line with the recent result obtained by Béthermin et al. (2023) on the Kennicutt-Schmidt (KS) relation
at _z_ _∼_ 4 _._ 5: they analysed 4 galaxies (3 in common with the
present sample) at higher spatial resolution (0 _._ 2 _[′′]_ _−_ 0 _._ 3 _[′′]_ ),
showing how MS galaxies have significantly lower Σ _SF R_, at
a given Σ _gas_, in comparison to high- _z_ starburst galaxies.



On the other hand, in fainter galaxies, the new
CRISTAL sample (Mitsuhashi et al. 2023) supports a positive correlation between IR size and IR luminosity. Altogether, the data samples considered in this work, spanning
2 dex in IR luminosity, highlight a variable trend in the
_r_ _e,F IR_ _−_ L _IR_ relation, ranging from steeply increasing behaviour at L _IR_ _<_ 10 [12] L _⊙_, followed by a downturn and a
decreasing trend at brighter luminosities.
Finally, we compare our dust emission sizes with the cosmological simulations of Cochrane et al. (2023) and Popping
et al. (2022). Their results suggest smaller dust continuum
sizes than our measurements but in Cochrane et al. (2023),
the only simulation that extends up to our stellar masses,
a tail of sizes as large as those observed in the ALPINE
galaxies is predicted.
Future ALMA observations at higher resolution and in
different bands will strengthen this result by enlarging the
sample of galaxies with a measured size and by allowing the
estimate of another key parameter: the dust temperature.
Besides being crucial in the estimate of the dust mass (e.g.
Bianchi 2013; Pozzi et al. 2021), this quantity is critically
sensitive to the optical thickness of the dust-emitting region
(e.g. Jin et al. 2022) and to the source physical area (hence
its size, Gilli et al. 2022). Further elucidating the scaling
relations presented here by means of improved observations
and understanding the underlying physical mechanisms are
important avenues for future investigation, and will provide
fundamental insights in future galaxy evolution studies.


_Acknowledgements._ This paper is dedicated to the memory of Olivier
Le Fèvre, PI of the ALPINE survey. We thank the referee for their insightful comments. We acknowledge support from grant PRIN MIUR
2017- 20173ML3WW_001. FP, VC, FE and FC acknowledge funding from the INAF Mini Grant 2022 program “Face-to-Face with the
Local Universe: ISM’s Empowerment (LOCAL)”. FC acknowledges
support from the INAF main-stream (1.05.01.86.31). EI acknowledges
funding by ANID FONDECYT Regular 1221846.GEM acknowledges
the Villum Fonden research grant 13160 “Gas to stars, stars to dust:
tracing star formation across cosmic time,” grant 37440, “The Hidden Cosmos,” and the Cosmic Dawn Center of Excellence funded
by the Danish National Research Foundation under the grant No.
140. MB acknowledges support from the French government through
the France 2030 investment plan managed by the National Research
Agency (ANR), as part of the Initiative of Excellence of Université
Côte d’Azur under reference number ANR-15-IDEX-01.


**References**


Bagley, M. B., Finkelstein, S. L., Koekemoer, A. M., et al. 2023, ApJ,
946, L12
Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016, ApJ, 827,
L32
Béthermin, M., Accard, C., Guillaume, C., et al. 2023, A&A, 680, L8
Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2
Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89
Bianchi, S. 2013, A&A, 552, A89
Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56
Calura, F., Pozzi, F., Cresci, G., et al. 2017, MNRAS, 465, 54
CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501
Casasola, V., Bianchi, S., De Vis, P., et al. 2020, A&A, 633, A100
Cheng, C., Ibar, E., Smail, I., et al. 2020, MNRAS, 499, 5241
Cochrane, R. K., Hayward, C. C., Anglés-Alcázar, D., et al. 2019,
MNRAS, 488, 1779
Cochrane, R. K., Hayward, C. C., Anglés-Alcázar, D., & Somerville,
R. S. 2023, MNRAS, 518, 5522
Cole, J. W., Papovich, C., Finkelstein, S. L., et al. 2023, arXiv e-prints,
arXiv:2312.10152
Cooke, E. A., Smail, I., Swinbank, A. M., et al. 2018, ApJ, 861, 100
Dekel, A., Zolotov, A., Tweed, D., et al. 2013, MNRAS, 435, 999
Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643,
A5


Article number, page 7 of 8

_A&A_ _proofs:_ manuscript no. pozzi24


Devereaux, T., Cassata, P., Ibar, E., et al. 2023, arXiv e-prints,
arXiv:2311.11493
Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61
Finkelstein, S. L., Bagley, M. B., Arrabal Haro, P., et al. 2022, ApJ,
940, L55
Franco, M., Elbaz, D., Zhou, L., et al. 2020, A&A, 643, A30
Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83
Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900,
1
Giacconi, R., Zirm, A., Wang, J., et al. 2002, ApJS, 139, 369
Gilli, R., Norman, C., Calura, F., et al. 2022, A&A, 666, A17
Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022a, A&A, 658, A43
Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022b, A&A, 659,
A196
Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ,
861, 95
Hodge, J. A. & da Cunha, E. 2020, Royal Society Open Science, 7,
200556
Hopkins, P. F., Wetzel, A., Kereš, D., et al. 2018, MNRAS, 480, 800
Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56
Jin, S., Daddi, E., Magdis, G. E., et al. 2022, A&A, 665, A3
Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491,
L18
Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172,
196
Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS,
197, 36
Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1
Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853, 172
Marinacci, F., Vogelsberger, M., Pakmor, R., et al. 2018, MNRAS,
480, 5113
Martí-Vidal, I., Pérez-Torres, M. A., & Lobanov, A. P. 2012, A&A,
541, A135
Mitsuhashi, I., Tadaki, K.-i., Ikeda, R., et al. 2023, arXiv e-prints,
arXiv:2311.17671
Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234
Pastrav, B. A. 2020, MNRAS, 493, 3580
Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010, AJ, 139,
2097
Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196
Popping, G., Pillepich, A., Calistro Rivera, G., et al. 2022, MNRAS,
510, 3321
Pozzi, F., Calura, F., Fudamoto, Y., et al. 2021, A&A, 653, A84
Puglisi, A., Daddi, E., Valentino, F., et al. 2021, MNRAS, 508, 5217
Rujopakarn, W., Dunlop, J. S., Rieke, G. H., et al. 2016, ApJ, 833, 12
Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3
Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1
Scoville, N., Faisst, A., Weaver, J., et al. 2023, ApJ, 943, 82
Silverman, J. D., Daddi, E., Rodighiero, G., et al. 2015, ApJ, 812, L23
Sommovigo, L., Ferrara, A., Carniani, S., et al. 2021, MNRAS, 503,
4878
Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D.
2014, ApJS, 214, 15
Springel, V., Pakmor, R., Pillepich, A., et al. 2018, MNRAS, 475, 676
Tadaki, K.-i., Genzel, R., Kodama, T., et al. 2017, ApJ, 834, 135
Talia, M., Pozzi, F., Vallini, L., et al. 2018, MNRAS, 476, 3956
Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24
Vallini, L., Witstok, J., Sommovigo, L., et al. 2024, MNRAS, 527, 10
van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788,
28
Voigt, L. M. & Bridle, S. L. 2010, Limitations of model-fitting methods
for lensing shear estimation
Ward, E. M., de la Vega, A., Mobasher, B., et al. 2023, arXiv e-prints,
arXiv:2311.02162
Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751


Article number, page 8 of 8


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[4].what.evidence[0]",
  "value": "Depletion times and gas fractions for ALPINE galaxies derived from [CII] luminosities",
  "failed_quote": "To validate this scenario, we consider the depletion times (t_depl) and the gas fractions (f_gas = M_gas / (M_⋆ + M_gas)) for the ALPINE galaxies with a measured dust size, derived by Dessauges-Zavadsky et al. (2020) from the [CII] luminosities"
 },
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "Dust continuum sizes, SFR, M_*, and L_IR of galaxies at 4 < z < 6 from GOODS-ALMA 2.0",
  "failed_quote": "In blue symbols we show the measurements from the GOODS-ALMA 2.0 survey (Gómez-Guijarro et al. 2022a)."
 },
 {
  "path": "data.external_data_from_literature[6].what.evidence[0]",
  "value": "Dust continuum sizes, SFR, M_*, L_IR, and r_e,FIR - L_IR relation of galaxies from super-deblended COSMOS and GOODS-North catalogues",
  "failed_quote": "In cyan symbols we report the dust continuum sizes of 6 galaxies from the super-deblended COSMOS and GOODS-North catalogues, selected for their very high photometric redshift (z > 6, Jin et al. 2022)."
 },
 {
  "path": "data.external_data_from_literature[7].what.evidence[0]",
  "value": "Dust continuum sizes, SFR, M_*, and L_IR of galaxies from the CRISTAL survey",
  "failed_quote": "We also report as red open squares the recent measurements from Mitsuhashi et al. (2023) from the CRISTAL survey"
 },
 {
  "path": "processing.imaging.task.evidence[0]",
  "value": "CASA TCLEAN",
  "failed_quote": "We then produce the continuum maps with the CASA (CASA Team et al. 2022) task TCLEAN"
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Ancillary spectra, photometric data, and UV-to-optical SED-fitting physical properties",
  "failed_quote": "for the description of the ancillary spectra and photometric data and the physical properties obtained from the UV-to-optical SED-fitting, we refer to Faisst et al. (2020)."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Remove channels containing [CII] emission from the visibility data, produce continuum maps with CASA TCLEAN, and run CASA IMFIT in the image plane to obtain initial guesses for positions, fluxes, and sizes.",
  "failed_quote": "We then produce the continuum maps with the CASA (CASA Team et al. 2022) task TCLEAN and we run in CASA the task IMFIT to achieve a first guess of the target’s properties (positions, fluxes and sizes)."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Fit a 2D Gaussian model in the uv-plane using CASA UVMODELFIT initialized with IMFIT outputs, circularize the deconvolved major and minor axis FWHMs, and compute effective radius r_e,FIR = FWHM_circ / 2. For unresolved sources, compute 3-sigma upper limits using the Marti-Vidal et al. (2012) formula.",
  "failed_quote": "These outputs, obtained in the image-plane, are used as first guess for the proper size measurements in the uv-plane, where we assume a 2-dimensional Gaussian model for the intensity profile and we measure the sizes with the CASA task UVMODELFIT."
 },
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Visual check of observed, model, and residual maps in the image plane to exclude sub-beam multi-components; comparison of 5 overlapping sources with CRISTAL survey measurements showing agreement within 1 sigma.",
  "failed_quote": "We note that 3 resolved sources (DC_818760, DC_848185, DC_873756) are in common with the recent results from the CRISTAL survey (Mitsuhashi et al. 2023) and the size measurements are consistent within 1σ."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Cross-check interpretation using gas depletion times and gas fractions from Dessauges-Zavadsky et al. (2020)",
  "failed_quote": "To validate this scenario, we consider the depletion times (t_depl) and the gas fractions (f_gas = M_gas / (M_⋆ + M_gas)) for the ALPINE galaxies with a measured dust size, derived by Dessauges-Zavadsky et al. (2020) from the [CII] luminosities"
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "Continuum imaging (TCLEAN), initial image-plane fitting (IMFIT), and uv-plane size fitting (UVMODELFIT)",
  "failed_quote": "We then produce the continuum maps with the CASA (CASA Team et al. 2022) task TCLEAN and we run in CASA the task IMFIT to achieve a first guess of the target’s properties (positions, fluxes and sizes)."
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Producing continuum maps after removing [CII] emission channels",
  "failed_quote": "We then produce the continuum maps with the CASA (CASA Team et al. 2022) task TCLEAN"
 },
 {
  "path": "reasoning.how_they_decided_enough.evidence[1]",
  "value": "Applied a continuum threshold of S/N > 4.5 (leaving 12 galaxies) to ensure meaningful size measurements, excluded 3 multi-component sources, visually checked residual maps, and verified 1-sigma consistency for 5 sources overlapping with the higher-resolution CRISTAL survey.",
  "failed_quote": "We note that 3 resolved sources (DC_818760, DC_848185, DC_873756) are in common with the recent results from the CRISTAL survey (Mitsuhashi et al. 2023) and the size measurements are consistent within 1σ."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Small number of galaxies with a measured dust continuum size at high redshift (z > 4) and high IR luminosity (L_IR > 10^11.5 L_sun).",
  "failed_quote": "We are aware of the small number of galaxies with a measured dust continuum size at high-z (> 4) and high-L_IR (> 10^11.5 L_⊙)"
 }
]
```
