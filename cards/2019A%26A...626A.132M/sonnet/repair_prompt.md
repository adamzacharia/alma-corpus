# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...626A.132M\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. aa35497-19 ⃝c ESO 2019
May 30, 2019

## **Molecular analysis of a high-mass prestellar core candidate in** **W43-MM1**


J. Molet [1], N. Brouillet [1], T. Nony [2], A. Gusdorf [3][,][ 4], F. Motte [2][,][ 5], D. Despois [1], F. Louvet [6], S. Bontemps [1], and F. Herpin [1]


1 Laboratoire d’astrophysique de Bordeaux, Univ. Bordeaux, CNRS, B18N, allée Geoffroy Saint-Hilaire, 33615 Pessac, France
2 Université Grenoble Alpes, CNRS, Institut de Planétologie et d’Astrophysique de Grenoble, F-38000 Grenoble, France
3 Laboratoire de Physique de l’École normale supérieure, ENS, Université PSL, CNRS, Sorbonne Université, Université ParisDiderot, Sorbonne Paris Cité, Paris, France
4 LERMA, Observatoire de Paris, PSL Research University, CNRS, Sorbonne Universités, UPMC Univ. Paris 06, 75231 Paris, France
5 AIM Paris-Saclay Département d’Astrophysique, CEA, CNRS, Univ. Paris Diderot, CEA-Saclay, F-91191 Gif-sur-Yvette Cedex,
France
6 Departamento de Astronomia de Chile, Universidad de Chile, Santiago, Chile


Received March 20, 2019; accepted May 13, 2019


**ABSTRACT**


_Context._ High-mass analogues of low-mass prestellar cores are searched for to constrain the models of high-mass star formation.
Several high-mass cores, at various evolutionary stages, have been recently identified towards the massive star-forming region W43MM1 and amongst them a high-mass prestellar core candidate.
_Aims._ We aim to characterise the chemistry in this high-mass prestellar core candidate, referred to as W43-MM1 core #6, and its
environment.
_Methods._ Using ALMA high-spatial resolution data of W43-MM1, we have studied the molecular content of core #6 and a neighbouring high-mass protostellar core, referred to as #3, which is similar in size and mass to core #6. We first subtracted the continuum
emission using a method based on the density distribution of the intensities on each pixel. Then, from the distribution of detected
molecules, we identified the molecules centred on the prestellar core candidate (core #6) and those associated to shocks related to
outflows and filament formation. Then we constrained the column densities and temperatures of the molecules detected towards the

two cores.
_Results._ While core #3 appears to contain a hot core with a temperature of about 190 K, core #6 seems to have a lower temperature
in the range from 20 K to 90 K from a rotational diagram analysis. We have considered different source sizes for core #6 and the
comparison of the abundances of the detected molecules towards the core with various interstellar sources shows that it is compatible
with a core of size 1000 au with _T_ = 20 − 90 K or a core of size 500 au with _T_ ∼ 80 K.
_Conclusions._ Core #6 of W43-MM1 remains one of the best high-mass prestellar core candidates even if we cannot exclude that it is
at the very beginning of the protostellar phase of high-mass star formation.


**Key words.** stars: formation – stars: massive – ISM: abundances – ISM: molecules – radio lines: ISM



**1.** **Introduction**


Understanding high-mass stars ( _M_ - 8 _M_ ⊙ ) is crucial in modern
astrophysics since their energy budget towards the interstellar
medium is the most important contribution coming from stars.
They form in massive dense cores of ∼100 M ⊙ within ∼0.1
pc (Motte et al. 2007; Bontemps et al. 2010), by processes far
less understood than for low-mass stars. Whereas low-mass stars
have clear distinct phases of evolution from prestellar cores to
young stars, we do not know if a prestellar core phase also exists
for high-mass stars. While the UV radiation pressure problem
(Wolfire & Cassinelli 1987) is mostly solved in most recent 3D
modelling, two competitive models remain: the ’core-fed’ model
(e.g. McKee & Tan 2003) and the ’clump-fed’ model (e.g. Bonnell & Bate 2006; Smith et al. 2009; Vázquez-Semadeni et al.
2017). The first model supposes the existence of starless massive dense cores, whereas, for the second one, low-mass prestellar cores can become high-mass protostars by collecting surrounding gas. The observation of a high-mass prestellar core is
challenging due to the lower number of high-mass stars com


pared to the number of low-mass stars (only ∼1% of the Galactic stellar population) and the short duration of the hypothetical
prestellar phase (∼10 [4] − 10 [5] yr; Tigé et al. 2017, and references therein). Motte et al. (2018a) and Louvet (2018) list the
current high-mass prestellar core candidates: CygX-N53-MM2
(Duarte-Cabral et al. 2014), G11.92-0.61-MM2 (Cyganowski
et al. 2014), G11.11-P6-SMA1 (Wang et al. 2014), G028CA9
(Kong et al. 2017), and W43-MM1#6 (Nony et al. 2018). No detailed study about their molecular content has been done so far.
We investigate here the latter one, W43-MM1#6.
The W43-MM1 ridge is a massive molecular cloud of 2 ×
10 [4] M ⊙ contained in 6 pc [2] . It is the main submillimeter fragment of the W43 complex (Motte et al. 2003; Nguyen-Luong
et al. 2013), located at the end of the Galactic bar at a distance of 5.5 kpc from the Sun (Nguyen Luong et al. 2011; Zhang
et al. 2014). W43-MM1 is associated to OH, CH 3 OH, and H 2 O
masers (respectively Braz & Epchtein 1983; Walsh et al. 1998;
Valdettaro et al. 2001), which are high-mass stellar activity signposts (Motte et al. 2003). At 0.05 pc resolution, W43-MM1 appears as a mini-starburst cluster with a high star formation rate of


Article number, page 1 of 18

_A&A proofs:_ manuscript no. aa35497-19



6000 M ⊙ .Myr [−][1] and N1a as the most massive dense core (Louvet
et al. 2014). Louvet et al. (2016) identified a large-scale shock

∼
( 5 pc) along the filament, consistent with numerical models of
a collision of two giant molecular clouds (e.g. Wu et al. 2017),

∼
and intermediate-scale shocks ( 0.2 pc) tracing protostellar outflows. The presence of small-scale shocks due to the collision of
gas inflows on the cores has been suggested but not observed yet
probably because of the limited sensitivity and/or angular resolution. More recently, Motte et al. (2018b) identified a large population of cores with ∼2000 au typical sizes, and numerous highmass cores. This suggests that W43-MM1 is one of the youngest
and richest clusters of high-mass cores in the Milky Way. This
sample is thus excellent to search for a high-mass prestellar core
(Nony et al. 2018).
Two neighbouring cores with the same size and mass have
been studied by Nony et al. (2018). The first core, identified as
core #3, has clear outflows traced by SiO(5-4) and CO(2-1) transitions and a line forest seen over the continuum band, which
qualifies it as a protostellar object. Core #6 in contrast does not
show any outflow and just a few lines are seen in the continuum band; it is thus a good high-mass prestellar core candidate.
During the evolution from the molecular cloud to the formation
of the protostar, the composition of the gas evolves (e.g. Gerner
et al. 2014). The formation and destruction of molecules depends
on the density of the environment, temperature, time, and dynamics. A rise in temperature will allow molecules to desorb
from the grain mantles to the gas phase and thus to be detectable
by rotational spectroscopy. Complex organic molecules (COMs)
have already been detected in both high-mass and low-mass starforming regions. The typical radius of hot corinos, where the
dust temperature is 100 K, is <100 au, while it is a few thousands au for hot cores (e.g. Herbst & van Dishoeck 2009). We
propose here to determine the nature of the W43-MM1 highmass core #6, constraining the physical and chemical conditions
of the core from the observed abundances and excitation temperatures of the detected molecules.
The article is organised as follows. We present the data and
the method used to subtract the continuum in Sect. 2. In Sect.
3, we analyse the molecular content of cores #3 and #6. We
study the distribution of the molecules to select those that are
directly related to core #6 and we estimate their temperature and
column densities. In Sect. 4 we compare our results with other
star-forming regions and discuss the nature of cores #3 and #6.


**2.** **Observations and data reduction**


_2.1._ _Data set_


Observations were carried out in Cycle 2 (project
#2013.1.01365.S) and Cycle 3 (#2015.1.01273.S), with the
ALMA 12 m and ACA 7 m arrays. W43-MM1 was imaged in
band 6 (between 216 and 234 GHz) with a 78"×53" (2.1 pc×1.4
pc) mosaic composed of 33 fields with the 12 m array and 11
fields with ACA. The total bandwidth is 4.8 GHz made of two
continuum bands and seven narrow bands centred on lines of
interest, with a spectral resolution ranging from 122 to 976 kHz
(0.17 to 1.26 km.s [−][1] ) and a spatial resolution of ∼0.44" (∼2400
au) (see Table 1). The continuum band centred on 232.4 GHz
is taken from Cycle 3 data and has a lower spatial resolution
(∼0.57" or ∼3200 au). Data reduction was made with CASA
4.7.2. (McMullin et al. 2007). The cleaning was performed with
a 0.5 Briggs robustness weighting, using the multiscale option
and with a threshold of ∼1σ cropped on a region excluding the
borders of the mosaic to avoid problems of divergence.


Article number, page 2 of 18



**Table 1.** Parameters of the ALMA spectral windows.


Spectral ν _obs_ Bandwidth Resolution rms
windows [GHz] [MHz] [ [′′] × [′′] ] [km.s [−][1] ] [K]
OC [33] S 216.076 234 0.55 × 0.40 0.17 0.37

SiO 217.033 234 0.54 × 0.39 0.34 0.42
H 2 CO 218.150 234 0.54 × 0.39 0.17 0.38
C [18] O 219.488 117 0.53 × 0.39 0.17 0.49

SO 219.877 117 0.54 × 0.39 0.33 0.44

CO 230.462 469 0.52 × 0.38 1.27 0.25

13
CS 231.144 469 0.52 × 0.37 0.32 0.28

Cont. 1 _[a]_ 232.4 1875 0.66 × 0.50 1.26 0.12

Cont. 2 233.4 1875 0.51 × 0.36 1.26 0.22
_a_ spectral window observed in Cycle 3. The other windows were
observed in Cycle 2.


_2.2._ _Continuum subtraction_


Because of the sensitivity of the current instruments, it is now
difficult to find channels with no emission line over all the map
to subtract the continuum in a data cube. In W43-MM1, Motte
et al. (2018b) identify 131 continuum cores with masses ranging from ∼1 M ⊙ to ∼100 M ⊙ and line contamination between
0% and 74%. The analysis of the four bright methyl formate
(CH 3 OCHO) lines detected in the 216 GHz band gives a velocity ranging from 94 to 102 km.s [−][1] for the 11 main continuum
cores. Due to the numerous lines in the various cores and the different velocities of the cores, line emission is present in almost
all channels. It is thus necessary to use a method of continuum
subtraction that handles each pixel independently. We developed
a method similar to the one presented in Jørgensen et al. (2016),
using the density distribution of the channel intensities on each
pixel. The profile of the distribution is composed of a Gaussian
part due to the noise, and a tail towards high intensities associated with the molecular emission. The Gaussian noise distribution peaks on the true continuum value, but the peak of the
observed distribution can be displaced due to the contribution of
the tail. The best way to obtain a correct continuum value with
the density profile method is discussed in Sanchez-Monge et al.
(2017), and the corrected sigma-clipping method (cSCM) seems
to be the most effective using their STATCONT algorithm. To
properly treat the statistical behaviour of the tail, we use the exponentially modified Gaussian (EMG) function (Grushka 1972),
which is the convolution between a Gaussian and an exponential
decay,



π
_f_ _EMG_ ( _x_ ) = _A_ σλ
� 2 _[exp]_ [[][λ] [2][µ][ +][ λσ] 2 [2] [ −] [2] _[x]_



),
2σ




[2] [ −] [2] _[x]_

] _erfc_ ( [µ][ +][ λσ] [2] [ −] _[x]_
2 ~~√~~ 2σ



(1)


where A is the peak amplitude, σ the variance of the Gaussian, λ the relaxation rate of the exponential modifier, µ the centre of the Gaussian, and _erfc_ the complementary error function.
We compared our EMG method with the cSCM from STATCONT, using synthetic spectra with parameters comparable to
our data. Our method is about 20 times faster than STATCONT

and we estimated a relative error on the continuum of ±2% with
the EMG method fit versus ±5% for the cSCM. Figure 1 presents
the estimation of the error depending on the following parameters: the continuum level, the maximum of the molecular emission and the noise level. We find that the EMG method is well
adapted for this kind of molecular distribution. Part of the derived continuum map is presented in Fig. 2. Comparing with the

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1


**Table 2.** Characteristics of the cores located at the tip of the main filament (from Motte et al. 2018b).


Core RA Dec Size FWHM M core n H2 T dust
# [J2000] [J2000] ["×"] [au] [M ⊙ ] [x10 [9] cm [−][3] ] [K]
3 18 [h] 47 [m] 46 [s] .37 -1 [◦] 54 [′] 33 [′′] . 41 0.52×0.47 1200 59±2 7.6±0.3 45±1
6 18 [h] 47 [m] 46 [s] .16 -1 [◦] 54 [′] 33 [′′] . 30 0.55×0.45 1300 56±9 6.6±0.1 23±2
9 18 [h] 47 [m] 46 [s] .48 -1 [◦] 54 [′] 32 [′′] . 54 0.63×0.45 1600 17.8±0.9 1.0±0.1 50±1
18 18 [h] 47 [m] 46 [s] .25 -1 [◦] 54 [′] 33 [′′] . 41 0.93×0.45 2600 28±4 0.4±0.1 23±2


_3.1._ _Molecular content of cores #3 and #6_



15


10



5


4


3



2


5


1


0

5 10 15
C/N ratio


**Fig.** **1.** Estimation of the relative error on the continuum level determination, depending on the molecular/continuum (M/C) ratio and continuum/noise (C/N) ratio. The black lines represent the M/N ratio. The
typical ratios from the core #3 pixels are included in the dashed box.
Each pixel is the average of the errors obtained from 20 synthetic spectra of 1000 channels with 100 random molecular Gaussian lines that
follow a power law comparable to the observed data.


line-contaminated continuum map of Motte et al. (2018b), derived from the integration of the full continuum band without
getting rid of molecular lines, the positions of the cores are the
same but the signal on this map is overestimated on average by
∼20% on continuum cores and up to 60% for cores #1 and #4.
As for the line-free continuum map of Motte et al. (2018b), it is
consistent, within 10%, with the EMG continuum image but it is
1.2 times noisier.


**3.** **Results and analysis**


Out of the 13 high-mass cores with M - 16 M ⊙, identified at
1.3mm by Motte et al. (2018b) in the W43-MM1 protocluster, we focus in this paper on the high-mass cores at the southwestern tip of the main filament (see Fig. 1 of Nony et al. 2018)
and we follow the same nomenclature. Table 2 lists the main
characteristics of the four high-mass cores identified in the continuum map (lower right panel in Fig. 2). The sizes and shapes of
the cores are the same as in Motte et al. (2018b) and Nony et al.
(2018) and do not change in this frequency range. We are interested in particular in the comparison of cores #3 and #6, which
are close (0.08 pc, 16000 au), with a similar size of 1200 au and
mass of ∼60 M ⊙ . We study here their spectra, averaged spatially
over the size of the continuum cores.



Whereas core #3 displays a forest of lines, much fewer lines
are observed towards core #6 (see Figs. A1 and A2, respectively). We first studied the molecular content of core #3. The
25 molecules that we identified in this core, including isotopologues, are listed in Table 3. Out of these molecules, 17 are identified in core #6. The line parameters of the 33 detected transitions towards core #6 are listed in Table A2.


Complex molecules are clearly present in core #6
with the detection of methanol (CH 3 OH) and its isotopologue ( [13] CH 3 OH), acetaldehyde (CH 3 CHO), dimethyl ether
(CH 3 OCH 3 ), and methyl formate (CH 3 OCHO). There is no clear
evidence of the presence of other COMs in core #6, except a tentative detection of the methanol isotopologue CH 3 [18] OH and of
formamide (NH 2 CHO) that only appear when the corresponding
lines are stacked. For CH 3 [18] OH, eight lines are considered as not
contaminated by other species in core #3 and were selected for
core #6. In the same way, five lines were selected for NH 2 CHO.
Some of the molecules detected towards core #6 seem to be directly associated with the continuum core, whereas the others do
not peak at the centre of the core and are being interpreted as
part of the large-scale features.


- Molecules not directly associated to core #6
For seven of the species detected in core #6, the large-scale view
shows that the distribution of these molecules is not only centred on the continuum cores (see Fig. 2). On small scales, those
molecules clearly peak at the north of core #6 (e.g. SiO) or belong to the environment (see DCN map). On large scales, CO
and SiO mainly trace the outflows from core #3 and #9, which
have been already analysed by Nony et al. (2018). SO, H [13] 2 [CO,]
and DCN follow the filament observed in continuum emission.


- Molecules centred on core #6
The other ten identified species are clearly centred on the continuum core (see Fig. 3). This suggests that part of the emission
of these molecules is not associated to the large-scale shocks
expected in a cloud forming though collision or along protostellar outflows, but is directly linked to the presence of the core.
The distribution of these molecules in the neighbouring core #3
is also centred on the continuum peak as shown in Fig. 4. We
used a Gaussian fit to derive a deconvolved size of the molecular emission, which appears to be typically close to the size
of the beam for all ten molecules observed in core #6. The results are comparable for the two cores (see Table 3), except for
the C [18] O emission, which is three times more extended than the
continuum extension of core #3. We note a recurrent small offset
(<0.2", i.e. less than half of the beam) of the molecular emission
with respect to the continuum peak, towards the south for core
#3 and towards the east for core #6 (see Fig. 5).


Article number, page 3 of 18

_A&A proofs:_ manuscript no. aa35497-19


**Table 3.** Excitation temperatures and column densities of the detected molecules towards cores #3 and #6 derived for a core of the beam size.


Core #3 Core #6


Molecule _v_ _dv_ _N_ tot _T_ ex Size _v_ _dv_ _N_ tot _T_ ex Size

[km.s [−][1] ] [km.s [−][1] ] [cm [−][2] ] [K] [ [′′] × [′′] ] [km.s [−][1] ] [km.s [−][1] ] [cm [−][2] ] [K] [ [′′] × [′′] ]
C [18] O - - >1.8(17) * 190 2.36×1.17 - - - - 0.53×0.18
CH 3 OH 97.1±0.1 5.9±0.3 4.7±0.4(17) 320±80 0.55×0.35 95.8±0.2 3.3±0.4 4.2±4.0(17) 55±35 0.54×0.52
13 CH 3 OH 97.0±0.1 5.3±0.3 9.8±2.1(16) 210±40 0.52×0.36 96.5±0.2 5.2±0.5 - - <0.55×0.45
CH 3 CHO 96.6±0.2 5.6±0.7 5.7±0.1(15) 150±40 0.68×0.46 95.6±0.1 2.6±0.4 2.6±1.9(15) 30±15 0.71×0.54
13 CS 97.0±0.1 5.0±0.1 8.9(14) 190 0.94×0.86 95.4±0.1 3.4±0.3 - - 0.73×0.48
CH 3 OCH 3 96.3±0.1 6.7±0.3 9.3±1.4(16) 140±25 0.61×0.53 95.9±0.2 2.3±0.7 - - CH 3 OCHO 97.3±0.3 4.7±0.8 1.0±0.3(17) 250±50 0.51×0.28 95.7±0.2 3.0±0.3 7.0±4.0(15) 50±30 0.62×0.22
OCS 96.5±0.1 5.7±0.1 2.2(16) 190 0.70×0.55 95.7±0.1 3.7±0.2 - - 0.78×0.56
O [13] CS 97.1±0.1 4.0±0.1 3.3(15) 190 0.43×0.34 95.1±0.2 2.1±0.4 - - <0.55×0.45
OC [33] S 96.6±0.1 3.7±0.2 1.4(15) 190 0.49×0.24 95.4±0.3 2.1±0.6 - - <2.1×0.22
SiO _v_ = 0 - - >5.6(14) * 190 - 95.8±0.3 5.1±0.7 - 


SO 97.0±0.1 5.6±0.2 4.1(15) 190 - 96.1±0.1 3.2±0.3 - H 2 CO - - >1.0(16) * 190 - - - - H [13] 2 [CO] 97.2±0.1 4.6±0.2 2.1(15) 190 - 96.0±0.2 2.4±0.6 - HC 3 N 96.6±0.1 5.3±0.1 5.8(14) 190 - 96.3±0.2 4.4±0.5 - DCN 96.8±0.1 5.8±0.3 3.6(14) 190 - 95.6±0.1 1.7±0.3 - CO - - >3.0(18) * 190 - - - - CH [18] 3 [OH] 97.3±0.7 4.8±1.1 1.6±0.8(16) 170±60 


Not centred



13 CH 3 CN 97.1±0.3 5.1±0.7 5.7±1.3(14) 130±60 HC(O)NH 2 97.3±0.4 6.2±0.9 1.7±0.7(15) 260±120 C 2 H 5 OH 97.3±0.4 5.0±1.0 2.4±0.5(16) 85±20 H 2 C [34] S 96.8±0.3 4.9±0.6 1.4(15) 190 CH 3 COCH 3 97.4±0.5 4.7±0.6 2.0(16) 190 C 2 H 3 CN 96.2±0.3 7.2±0.7 2.9(15) 190 C 2 H 5 CN 97.2±0.1 4.9±0.4 4.5±1.5(15) 170±70 


Not detected



_Notes_ : _a_ ( _b_ ) = _a_ ×10 _[b]_ . * Only a lower limit of the column density can be derived for the molecules where the emission is self-absorbed
or filtered by the interferometer.



_3.2._ _Critical density and opacity_


The critical densities are estimated as _n_ crit = _A_ ij / _q_ ij with _A_ ij the
Einstein coefficient and _q_ ij the collision coefficient rates. The
values of the critical densities for the individual transitions of
the molecules, available in the Leiden Atomic and Molecular
Database [1] (Schöier et al. 2005), are indicated in Tables A1 and
A2. We find values between ∼10 [4] and 10 [7] cm [−][3] for our lines,
which are lower than the obtained _n_ H 2 values of the cores (∼10 [9]
cm [−][3], see Table 2). In the following we will hence assume that
LTE conditions are verified.
In general, isotopologues are less likely to be optically thick
than their main isotopologue because of their lower abundances.
Considering a distance of W43-MM1 from the Galactic centre
of 4.5 kpc (Zhang et al. 2014), we take for the isotopic ratios:
12 C/ 13 C = 45±13 (Milam et al. 2005), 32 S/ 33 S = 90±30 (Chin
et al. 1996), and [18] O/ [16] O = 327±32 (Wilson & Rood 1994). The
detection of [13] CH 3 OH in core #6 is important since the methanol
is optically thick. We also preferred to use the available isotopologues of CS and OCS to avoid some underestimations of abundances.


_3.3._ _Temperatures and abundances_


The total column density _N_ tot and the excitation temperature _T_ ex
can be obtained in LTE and optically thin conditions using the


1
`[https://home.strw.leidenuniv.nl/~moldata/](https://home.strw.leidenuniv.nl/~moldata/)` .


Article number, page 4 of 18



relation


_E_ u

_ln_ _[N]_ [u] = _lnN_ tot − _lnQ_ ( _T_ ex ) −, (2)

_g_ u _k_ B _T_ ex


with _N_ u the upper level column density, _g_ u the degeneracy of
the upper state, _Q_ ( _T_ ex ) the partition function, and _E_ u the upper
state energy. We assume here that the filling factor is equal to 1.
In LTE conditions, the excitation temperature is identical to the
kinetic temperature.
For core #3, we could derive the column density and the excitation temperature for ten molecules out of the 25 molecules
detected using rotational diagrams since we detected more than
two transitions for these ten molecules. For core #6, it was only
possible for methanol, acetaldehyde, and methyl formate, which
have enough detected transitions to build a rotational diagram.
The rotational diagrams were performed using the CASSIS [2]
software (Vastel et al. 2015). The derived values are displayed
in Table 3. Despite the significant uncertainties, the temperature seems to be lower for core #6 (15-90 K) than for core #3

∼
( 190 K).
The local density is high enough to reach LTE conditions, so
that we could use the equation (Tielens 2005)



_N_ tot = [1][.][94] _A_ [ ×][ 10] [3] ν ij [2]

ij



_Q_ ( _T_ ex )
� _T_ mb _d_ ν _g_ u exp(− _E_ u / _k_ B _T_ ex ) [,] (3)



where _N_ tot is in cm [−][2], ν ij is the rest frequency in GHz, and the
only parameter coming from the observations is the integrated


2
`[http://cassis.irap.omp.eu](http://cassis.irap.omp.eu)` .

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1


[K km.s [−][1] ]



3


2



1200


900


600


300


0




[K km.s [−][1] ]


40


200



32


24


16


8


0



3


2



30


20


10



1


0


1


2


3



150


100


50


0



1


0


1


2


3







6 4 2 0 2


3


2




[K km.s [−][1] ]


800


120


600

90



6 4 2 0 2


2



1


0


1


2


3




[K km.s [−][1] ]


120

16



12


8


4



90


60


30



1


0


1


2


3





400


200


0





60


30


0



6 4 2 0 2


3


2




[K km.s [−][1] ]


800

32


600

24



0


[K km.s [−][1] ]


160

24



6 4 2 0 2


3


2



18


12


6


0



120


80


40


0



1


0


1


2


3


3


2


1


0


1


2


3







400


200


0



16


8


0



1


0


1


2


3



6 4 2 0 2



800


600


400


200


0




[K km.s [−][1] ]



8


6


4


2


0



6 4 2 0 2


3






[K]
10 [1]


10 [0]


10 [-1]





2


1


0


1


2


3



6 4 2 0 2

Offset RA (")



**Fig.** **2.** Velocity integrated maps of the molecules that do not peak on core #6. The velocity range is indicated on the top of each box. For each
molecule, grey scale images correspond to the large-scale map with large dynamics in intensity, while the colour maps focus on a narrower region
around core #6 with smaller dynamics in intensity (as indicated by the two wedges on the right side of each panel). Temperature is the main beam
brightness temperature _T_ mb . The continuum map obtained from the Cont. 2 spectral window data is plotted in the bottom right panel. The contours
represent the 5-10-20σ continuum emission, with 5σ ≈ 9mJy/beam. The position is relative to the centre of the continuum core #6. The beam is
represented in the bottom left corner of each map. The CO is completely filtered in the 95-97 km/s velocity range around core #6 (see Fig. A2),
but its presence is confirmed by the C [18] O emission.


Article number, page 5 of 18

_A&A proofs:_ manuscript no. aa35497-19


[K km.s [−][1] ]




[K km.s [−][1] ]



10.0


7.5


5.0


2.5


0.0



3


2



600


400


200


0



60


40


20


0



24


18


12


6


0



3


2



1


0


1


2


3



1


0


1


2


3







6 4 2 0 2


3


2



400


200


0




[K km.s [−][1] ]


60

400



6 4 2 0 2


2




[K km.s [−][1] ]



12


9


6


3


0



45


30


15


0



300


200


100


0



1


0


1


2


3



1


0


1


2


3







6 4 2 0 2


3


2




[K km.s [−][1] ]


200


3.2


150


2.4


100

1.6



6 4 2 0 2


2




[K km.s [−][1] ]


60


2.4



1.8


1.2


0.6


0.0



40


20


0



1


0


1


2


3


3


2


1


0


1







50


0



0.8


0.0



1


0


1


2


3



6 4 2 0 2




[K km.s [−][1] ]


60


4



6 4 2 0 2


3


2




[K km.s [−][1] ]


6.0

200



4.5


3.0


1.5


0.0





40


20



6 4 2 0 2





1


0


1


2


3



2


3


6 4 2 0 2

Offset RA (")


**Fig. 3.** Same as Fig. 2 but for molecules centred on core #6.


Article number, page 6 of 18



150


100


50


0



0



3


2


1


0

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1


Core #3































































































Offset RA (")


**Fig. 4.** Velocity integrated intensity map (grey scale) around core #3 for the molecules centred on the continuum core. The velocity range chosen
for the integration is 95-97 km/s, which corresponds to the central emission peak. Temperature is the main beam brightness temperature _T_ mb . The
black contours represent the result of a Gaussian fit to the emission; the levels are 20, 50, and 80% of the maximum. The maps are centred on the
continuum core represented in blue contours (50% of the maximum). The beam is represented on the bottom left corner of each map.


Article number, page 7 of 18

[K km.s [−][1] ]

10.0

1.0




[K km.s [−][1] ]



_A&A proofs:_ manuscript no. aa35497-19


Core #6

[K km.s [−][1] ]
10.0


1.0



1.0


0.5


0.0


0.5


1.0


1.0 0.5 0.0 0.5 1.0



24


18


12


6


0



0.5


0.0


0.5


1.0



7.5


5.0


2.5


0.0

1.0 0.5 0.0 0.5 1.0


[K km.s [−][1] ]



0.5


0.0


0.5


1.0



7.5


5.0


2.5




[K km.s [−][1] ]



1.0


0.5


0.0


0.5


1.0


1.0 0.5 0.0 0.5 1.0



0.0

1.0 0.5 0.0 0.5 1.0


[K km.s [−][1] ]


1.0


4


0.5


3


0.0


2


0.5


1


1.0


0

1.0 0.5 0.0 0.5 1.0


[K km.s [−][1] ]



1.2


0.9


0.6


0.3


0.0



1.0


0.5


0.0


0.5


1.0


1.0 0.5 0.0 0.5 1.0



6.0


4.5


3.0


1.5


0.0



1.0


0.5


0.0


0.5


1.0


1.0 0.5 0.0 0.5 1.0




[K km.s [−][1] ]



80


60


40


20


0



1.0






[K km.s [−][1] ]


12


0.5


9


0.0


6


0.5


3


1.0


0

1.0 0.5 0.0 0.5 1.0



0.5


0.0


0.5


1.0


1.0 0.5 0.0 0.5 1.0


Offset RA (")


**Fig. 5.** Same as Fig. 4 but for source #6.



2.4


1.8


1.2


0.6


0.0



intensity � _T_ mb _d_ ν in K.km.s [−][1] . The spectroscopic parameters
come from the Cologne Database for Molecular Spectroscopy
(CDMS [3] ) and the Jet Propulsion Laboratory (JPL [4] ) catalogue
depending on the molecules (see Tables A1 and A2). When it
was not possible to use a rotational diagram, we assumed an
excitation temperature of 190K for core #3 to derive a column
density with Eq. (3). These results are the inputs for the synthetic spectra in Figs. A1 and A2. Residuals show that only a few
lines are unidentified towards core #3. Since H 2 CO and C [18] O
are self-absorbed and SiO and CO are filtered, only lower limits can be obtained and no correct synthetic spectra can be per

3 http://www.astro.uni-koeln.de/cdms/.
4
http://spec.jpl.nasa.gov/.


Article number, page 8 of 18



formed for these molecules. For the optically thick molecules,
a correction of the column density is made with their observed
isotopologues; the corrected values are in Table 5 for core #3 and
in Table 6 for core #6. The O [13] CS/OC [33] S ratio for core #6 and
the O [13] CS/OC [33] S and [13] CH 3 OH/CH [18] 3 [OH ratios for core #3 are]
consistent with the elemental isotopic ratios mentioned in Sect.
3.2.


The obtained abundances relative to H 2 are displayed in Fig
6. We consider that the depth of the molecular distribution along
the line of sight is equal to the size of the continuum cores, hence
we use column density values _N_ H2 = (2.6 ± 0.1) × 10 [25] cm [−][2] and
_N_ H2 = (1.9 ± 0.3) × 10 [25] cm [−][2] (for core #3 and #6, respectively)
from _n_ H 2 densities in Table 2 for a source size equal to the size of

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1


**Table 4.** List of sources used for comparison with cores #3 and #6.


Source Name Nature of Hot core/ Distance Size Mass _L_ bol Reference
in Fig. 6 the core corino [kpc] [au] [ _L_ ⊙ ]
L134N L134N Prestellar - 0.2 1500 LM 10 [−][2] Ohishi et al. (1992)
B1b-S B1b-S Young protostar Hot corino 0.2 80 LM 10 [−][1] Marcelino et al. (2018)
B1b-N B1b-N FHSC candidate - 0.2 500 LM 10 [−][1] Gerin et al. (2015)
L1544 L1544 Prestellar - 0.1 >4000 LM 10 [0] Vastel et al. (2014, 2018)
L1689B L1689B Prestellar - 0.1 3500 LM 10 [0] Bacmann et al. (2012)
NGC1333 IRAS4 A2 IRAS4A2 Protostellar Hot corino 0.2 250 LM 10 [1] López-Sepulcre et al. (2017)
IRAS 16293-2442 IRAS16293 Protostellar Hot corino 0.1 150 LM 10 [1] Cazaux et al. (2003)
W43-MM1 #6 Core 6 Prestellar ? ? 5.5 1300 HM 10 [1] Nony et al. (2018)
CepE-A CepE-A Protostellar Hot corino 0.7 510 IM 10 [2] Ospina-Zamudio et al. (2018)
NGC 7129 FIRS2 FIRS2 Protostellar Hot core 1.2 1900 IM 10 [2] Fuente et al. (2014)
NGC 2264 CMM3A CMM3A Protostellar Hot core 0.7 200 IM 10 [2] Watanabe et al. (2017)
NGC 7538S MM3 MM3 Prestellar ? ? 1100 IM
MM2 MM2 Protostellar Hot core 2.6 1100 IM 10 [4] _[a]_ Feng et al. (2016)
MM1 MM1 Protostellar Hot core 1100 HM
CygX-N63 hot core N63hc 500 HM _[a]_
Young protostar Hot core 1.4 10 [2] Fechtenbaum (2015)
lukewarm region N63lw 2100 HM
W43-MM1 #3 Core 3 Protostellar Hot core 5.5 1200 HM 10 [3] Nony et al. (2018)
G35.20-0.74N A G35.20 Protostellar Hot core 2.2 1300 HM 10 [4] Allen et al. (2017)
G35.03+0.35 A G35.03 Protostellar Hot core 2.3 1100 HM 10 [4] Allen et al. (2017)
G34.26+015 G34.26 Protostellar Hot core 3.7 3500 HM 10 [4] Mookerjea et al. (2007)

Sutton et al. (1995)
Orion KL KL Protostellar Hot core 0.4 4000 HM 10 [5]
Crockett et al. (2014)
Sgr B2(N2) SgrB2 Protostellar Hot core 8.3 12000 HM 10 [6] Belloche et al. (2016)


_Notes_ : The distance is from the Sun. LM, IM, and HM stand for low-mass ( _M_ < 2 _M_ ⊙ ), intermediate-mass (2 _M_ ⊙ < _M_ < 8 _M_ ⊙ ), and
high-mass ( _M_ - 8 _M_ ⊙ ), respectively. The third column indicates if the protostellar cores harbour a hot core or a hot corino.
_a_ Total value from all the sources mentioned.



**Table 5.** Column densities in core #3 estimated from isotopologues.


Molecule _N_ [cm [−][2] ]
CH 3 OH 5.1±2.7(18)
CS 4.0±1.2(16)
OCS 1.4±0.5(17)
H 2 CO 9.4±2.7(16)
CO >5.3(19)


_Notes_ : _a_ ( _b_ ) = _a_ × 10 _[b]_ . The methanol density is derived from the
rotational diagrams of its isopotologues. For the other molecules,
the densities are obtained using isotopologue column densities at
190 K. The source size is assumed to be equal to the beam.


the beam. Only the molecules centred on the cores are selected
because they are more likely to be directly associated to the core.
We chose to take all the abundances derived at the mean temperature _T_ ex = 190 K for core #3. To investigate the nature of core
#6, we have derived the abundances in the typical range of temperature for star-forming regions ( _T_ ex = 10 − 200 K). The values
observed for various star-forming regions (see Table 5) are plotted for comparison and the nature of the cores are discussed in
the next section.


**4.** **Discussion**


When considering the distribution of the molecules around core
#6, the high density component observed at the north-east of



core #6 may be associated to the heating of the outer envelope
of the core by the interaction with a shock. Core #6 appears to
be in a large-scale shock, traced by the SiO distribution in Fig.
2, and Louvet et al. (2016) showed that the narrow component
of the SiO emission comes from the low-velocity shock spread
along the length of the ridge. We note also that Nony et al. (2018)
showed that an outflow seen in SiO and CO emission comes from
core #18 in this direction.

The lines detected towards core #6 are narrower than towards
core #3, with a mean line width of 3.2±0.1 km/s against 5.2±0.2
km/s. Narrower lines for core #6 are a first clue to propose that it
is less active and thus less evolved than its protostellar neighbour.
The difference in state of evolution cannot be due to the W-R/OB
stars association of W43, which is located ∼ 5 pc away, as the
cores are out of the ionisation front caused by their UV radiation
(Motte et al. 2003; Nguyen-Luong et al. 2017). Furthermore the
cores do not show any inner velocity gradient at the spatial and
spectral resolutions of our observations.
The COMs detected in core #6 are usually detected in hot
cores, where they are formed on grain mantles and then desorbed during the warm-up phase. However, the detection of these
molecules in low-mass prestellar cores (Bacmann et al. 2012;
Cernicharo et al. 2012; Vastel et al. 2014) shows that their presence is not sufficient to determine the nature of the core. Also,
lower abundances of COMs in this core with respect to core #3
is not a direct proof of a prestellar signature since other sources,
like warm carbon chain chemistry sources, are poor in COMs
(Sakai et al. 2008).
Hereafter we compare the abundances observed in core #3
and #6 to those in other sources considering two scenarios. In the


Article number, page 9 of 18

_A&A proofs:_ manuscript no. aa35497-19





200


100


30


0


200


100


30


0





|CH3OH<br>KL<br>MM1 G35.20 SgrB2<br>G34.26<br>G35.03<br>MM2 KL<br>CMM3A N63hc<br>IRAS16293<br>MM3<br>B1b-N<br>L1544<br>L134N N63lw|OCS<br>KL FIRS2<br>KL<br>G34.26<br>MM1<br>MM2<br>IRAS16293<br>N63lw<br>MM3<br>L1544 L134N|G35.20<br>CH3CHO Core 3<br>2400au<br>1000au<br>500au<br>Core6<br>G35.03 2400 au<br>FIRS2 1000 au<br>IRAS4A2 500au<br>τ = 1<br>B1b-S N63hc<br>N6C3elwpE-A CepE-A<br>IRAS16293<br>L1544<br>L1689B L134N|
|---|---|---|
|L1544<br>KL<br>L134N<br>KL<br>CS|L1689B<br>B1b-S<br>IRAS4A2<br>KL<br>CepE-A<br>SgrB2<br>MM1<br>MM2<br>G34.26<br>IRAS16293<br>G35.20<br>CMM3A<br>N63lw<br>N63hc<br>G35.03<br>CH3OCHO|L1689B<br>B1b-S<br>IRAS4A2<br>KL<br>CepE-A<br>MM1<br>MM2<br>G34.26<br>KL<br>IRAS16293<br>G35.20<br>FIRS2<br>CMM3A<br>N63lw<br>N63hc<br>G35.03<br>CH3OCH3|


10 [-11] 10 [-10] 10 [-9] 10 [-8] 10 [-7] 10 [-6] 10 [-5]

















































10 [-11] 10 [-10] 10 [-9] 10 [-8] 10 [-7] 10 [-6] 10 [-5]















10 [-11] 10 [-10] 10 [-9] 10 [-8] 10 [-7] 10 [-6] 10 [-5]



N X /N H 2


**Fig.** **6.** Abundances with respect to H 2 for selected molecules. Results for core #3 (red squares) and core #6 (blue lines) considering different
source sizes (see legend) are from LTE modelling. The temperature _T_ ex = 190 K is fixed for core #3, it varies from 10 to 200 K for core #6. The
blue area represents an error of 50% on the estimation of the abundance, which includes the error on the line area and on the value of _N_ H 2 . The
grey area is the temperature range estimated for core #6 from the rotational diagrams. For a given size, a molecule becomes optically thick below
the black line. The sources listed in Table 5 are represented by a dot for prestellar cores or a star for protostellar cores. The colour code is white
for low-mass, grey for intermediate-mass, and black for high-mass cores. The names refer to column 2 of Table 4.



first one, the size of the region emitting the detected molecules
is taken as equal to the beam; in the second one, we consider
that they are unresolved. The abundances taken in the literature
for the other sources correspond to different source sizes and
are not corrected by the filling factor or the H 2 column density.
Nonetheless the trends remain the same: the molecules are more
abundant in the high-mass hot cores than in hot corinos and even
more than in low-mass prestellar cores. Thus it does not impact
the qualitative discussion that follows.


_4.1._ _Cores sizes similar to the beam_


In this case, we consider no beam dilution. The observed abundances towards core #3 are represented in Fig. 6 by red filled
squares and those towards core #6 by blue solid lines. First of all,
the observed abundances are globally lower than for the other
sources. Indeed we find column densities of the same order as
for other sources but the local densities (∼ 7 × 10 [9] cm [−][3] ) are
huge compared to the usual _n_ H 2 ∼ 10 [5] − 10 [8] cm [−][3] observed in
star-forming regions. Core #3 abundances are at least an order
of magnitude below for OCS and CH 3 OCHO compared to the
other high-mass protostellar cores. However, for CH 3 OH and
CH 3 OCH 3, the core #3 results are more consistent with some hot
cores (G35.20-0.74N A and G35.03+0.35 A). All abundances
derived for core #6 are much lower than other sources at hot core
and hot corino temperatures, except the CH 3 OH value compatible with NGC 2264 CMM3A.

The only sources comparable are cold low-mass prestellar
cores (L1544, L1689B) and the very young low-mass proto

Article number, page 10 of 18



star B1b-N, suggesting a temperature of about 20 K. The envelope on a 2400 au scale would be at the same temperature as
the dust, whose temperature is around 23 K. This means that
there is no internal source of heating (in other terms a protostar),
since such a source would unbalance the two temperatures. At
this low temperature, bright emission of the J=3-2 line of N 2 D+
(ν = 231.32183 GHz, _E_ up = 22.2 K) could be expected (Tobin et al. 2019) but it is not detected, suggesting that the core is
hotter than estimated in this scenario.


_4.2._ _Unresolved cores_


We suppose now that the size of the molecular emission is
smaller than the beam size. The molecular column densities are
corrected by the filling factor assuming a _r_ [−][2] density model for
_n_ H 2 . When considering core sizes smaller than 500 au, all lines
become optically thick in our temperature range and their profiles no longer match with our observations. With a core size
of 500 au, _n_ H 2 = 1.5 × 10 [10] cm [−][3] ( _N_ H 2 = 9.0 × 10 [24] cm [−][2] ) and
_n_ H 2 = 1.3×10 [10] cm [−][3] ( _N_ H 2 = 7.0×10 [24] cm [−][2] ) for cores #3 and #6,
respectively. The abundances are thus enhanced by a factor of 12
with a source size of 500 au compared to a source size of 2400
au. It is also a way to mimic results from a source with the size
of the beam but with a local density of ∼ 10 [8] cm [−][3] compatible
with young protostellar cores.

With a size of 500 au, results from core #3 are more consistent with high-mass protostellar cores for OCS and CH 3 OCHO
(see red empty squares on Fig. 6). However, the brightest lines
become optically thick. Considering a size of 1000 au for core

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1



#3 (pale red filled squares on Fig. 6) seems a better compromise
to match with the observed line profiles and the other core abundances at the same time. The corresponding column densities are
listed in Table A3.


For core #6, with a size of 500 au (blue dotted lines on Fig.
6) the results are comparable to cores at various evolutionary
stages between 20 and 90 K. However, some of the main lines
are optically thick (e.g. [13] CS and OCS) for temperatures lower
than 75 K excluding the scenario of a compact cold core. This
leaves the possibility of a compact core at a high temperature of
80 K, included in the temperature range given by the rotational
diagrams and consistent with sources like the hot corino B1b-S
and the protostellar core NGC 2264 CMM3A. By adjusting the
size of core #6 to 1000 au (blue dashed lines on Fig. 6), most of
the lines become optically thin and low temperatures are possible. In particular, the CH 3 OH and CH 3 CHO abundances match
with L134N values at 20 K with a comparable size. The observed
abundances for core #6 with sizes 500-1000 au are also comparable to the lukewarm region of the young high-mass protostellar
core CygX-N63 (2100 au, Fechtenbaum 2015), but still at least
an order of magnitude below the 500 au N63 hot core values.


NGC 7538 S MM1 is a high-mass protostellar object, more
evolved than the hot molecular core NGC 7538 S MM2 and
NGC 7538 S MM3, which is comparable to prestellar objects because it only exhibits emission of lower excitation lines. While
the core #3 results match with NGC 7538 S MM1, core #6 is
more likely to be similar to NGC 7538 S MM3. Also, B1b-S
displays a spectrum as rich in lines as core #3, and the B1b-N
molecular emission shown in Marcelino et al. (2018) is as poor
as core #6. However, the CH 3 OH emission in B1b-N is associated to a nascent outflow of size 1300 au (Gerin et al. 2015),
unresolved at our beam size, but with abundances comparable to
core #6.


**Table 6.** Column densities in core #6 estimated for different scenarios.


Size 2400 au 1000 au 1000 au 500 au

_T_ ex 20 K 30 K 80 K 80 K
Molecule _N_ [cm [−][2] ]
C [18] O 1.3(16) 4.9(16) 9.4(16) 3.4(17)
CH 3 OH 2.9(17) 1.4(17) 3.0(16) 1.1(17)
13 CH 3 OH 1.4(15) 4.6(15) 1.1(16) 4.0(16)
CH 3 CHO 9.4(14) 1.8(15) 2.1(15) 7.6(15)
13 CS 4.5(13) 1.3(14) 1.7(14) 6.2(14)
CH 3 OCH 3 3.8(15) 8.3(15) 1.4(16) 5.0(16)
CH 3 OCHO 1.3(16) 1.4(16) 7.0(15) 2.5(16)
OCS 2.9(16) 2.3(16) 6.1(15) 2.2(16)
O [13] CS 3.2(15) 3.1(15) 1.0(15) 3.7(15)
OC [33] S 1.8(15) 1.7(15) 5.9(14) 2.1(15)
Column densities estimated from the isotopologues
CH 3 OH 6.3(16) 2.1(17) 5.0(17) 1.8(18)
CS 1.9(15) 5.9(15) 7.7(15) 2.8(16)
OCS 1.5(17) 1.5(17) 4.9(16) 1.8(17)
CO 4.3(18) 1.6(19) 3.1(19) 1.1(20)


_Note_ : _a_ ( _b_ ) = _a_ × 10 _[b]_ .



**5.** **Conclusion**


The study of the molecular content of core #6 is challenging because of the few and weakly observed lines. We have identified
17 molecules in core #6 based on the analysis of its line-rich
neighbour core #3. The distribution of these molecules reveals
that ten are directly associated to core #6 and the others can be
associated to the interaction between its envelope and the lowvelocity shock of the ridge. The determination of the column
densities and the temperatures from rotational diagrams was
only possible for three molecules, methanol (CH 3 OH), methyl
formate (CH 3 OCHO), and acetaldehyde (CH 3 CHO). Because of
the low signal-to-noise ratio and the range of upper energy levels, there is a huge uncertainty on the temperature (15-90 K)
obtained by this method. To better constrain the temperature and
core nature, we have compared our observations to the abundances of different sources including prestellar cores, hot corinos, and hot cores. The conclusion about the nature of core #6
clearly depends on the estimated size of the core :


**–** at the size of the beam, 2400 au, the core is cold ( _T_ ex ≈ _T_ dust )
and may be prestellar or in a transition phase to a protostellar core; however, the non detection of the N 2 D+ emission
suggests that the temperature is greater than 20 K.

**–**
if the core size is 1000 au, it could be at the very beginning
of the protostellar phase at 20-30 K or a young protostellar
core at ∼80 K not active enough to display large outflows;

**–**
considering a size of 500 au, the core still cannot be comparable to hot cores but only to a hot corino with a temperature
of ∼80 K.

**–** the source size is not less than 500 au because the lines would
be optically thick, which is not observed.


Core #6 is not as evolved as core #3, the absence of outflows in
CO and SiO suggests that it does not contain a protostar. From
the molecular study it appears as a good high-mass prestellar
core candidate and deep dedicated line surveys with a higher
spatial resolution are still necessary to investigate whether it harbours a hot corino, like those found towards low-mass class 0
protostars.


_Acknowledgements._ This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2013.1.01365.S, ADS/JAO.ALMA#2015.1.01273.S. ALMA
is a partnership of ESO (representing its member states), NSF (USA), and
NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and
KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work
was supported by the Programme National de Physique Stellaire and Physique
et Chimie du Milieu Interstellaire (PNPS and PCMI) of CNRS/INSU (with
INC/INP/IN2P3).


**References**


Allen, V., van der Tak, F. F. S., Sánchez-Monge, Á., Cesaroni, R., & Beltrán,
M. T. 2017, A&A, 603, A133
Bacmann, A., Taquet, V., Faure, A., Kahane, C., & Ceccarelli, C. 2012, A&A,
541, L12
Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, A&A, 587,
A91

Bonnell, I. A. & Bate, M. R. 2006, MNRAS, 370, 488
Bontemps, S., Motte, F., Csengeri, T., & Schneider, N. 2010, A&A, 524, A18
Braz, M. A. & Epchtein, N. 1983, A&AS, 54, 167
Cazaux, S., Tielens, A. G. G. M., Ceccarelli, C., et al. 2003, ApJ, 593, L51
Cernicharo, J., Marcelino, N., Roueff, E., et al. 2012, ApJ, 759, L43
Chin, Y.-N., Henkel, C., Whiteoak, J. B., Langer, N., & Churchwell, E. B. 1996,
A&A, 305, 960
Crockett, N. R., Bergin, E. A., Neill, J. L., et al. 2014, ApJ, 787, 112
Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2014, ApJ, 796, L2
Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2014, A&A, 570, A1


Article number, page 11 of 18

_A&A proofs:_ manuscript no. aa35497-19


Fechtenbaum, S. 2015, PhD thesis, University of Bordeaux
Feng, S., Beuther, H., Semenov, D., et al. 2016, A&A, 593, A46
Fuente, A., Cernicharo, J., Caselli, P., et al. 2014, A&A, 568, A65
Gerin, M., Pety, J., Fuente, A., et al. 2015, A&A, 577, L2
Gerner, T., Beuther, H., Semenov, D., et al. 2014, A&A, 563, A97
Grushka, E. 1972, Analytical Chemistry, 44, 1733
Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427
Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595,
A117
Kong, S., Tan, J. C., Caselli, P., et al. 2017, ApJ, 834, 193
López-Sepulcre, A., Sakai, N., Neri, R., et al. 2017, A&A, 606, A121
Louvet, F. 2018, in SF2A-2018: Proceedings of the Annual meeting of the French
Society of Astronomy and Astrophysics, 311–317
Louvet, F., Motte, F., Gusdorf, A., et al. 2016, A&A, 595, A122
Louvet, F., Motte, F., Hennebelle, P., et al. 2014, A&A, 570, A15
Marcelino, N., Gerin, M., Cernicharo, J., et al. 2018, A&A, 620, A80
McKee, C. F. & Tan, J. C. 2003, ApJ, 585, 850
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical
Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005,
ApJ, 634, 1126
Mookerjea, B., Casper, E., Mundy, L. G., & Looney, L. W. 2007, ApJ, 659, 447
Motte, F., Bontemps, S., & Louvet, F. 2018a, ARA&A, 56, 41
Motte, F., Bontemps, S., Schilke, P., et al. 2007, A&A, 476, 1243
Motte, F., Nony, T., Louvet, F., et al. 2018b, Nature Astronomy, 2, 478
Motte, F., Schilke, P., & Lis, D. C. 2003, ApJ, 582, 277
Nguyen-Luong, Q., Anderson, L. D., Motte, F., et al. 2017, ApJ, 844, L25
Nguyen-Luong, Q., Motte, F., Carlhoff, P., et al. 2013, ApJ, 775, 88
Nguyen Luong, Q., Motte, F., Hennemann, M., et al. 2011, A&A, 535, A76
Nony, T., Louvet, F., Motte, F., et al. 2018, A&A, 618, L5
Ohishi, M., Irvine, W. M., & Kaifu, N. 1992, in IAU Symposium, Vol. 150,
Astrochemistry of Cosmic Phenomena, ed. P. D. Singh, 171
Ospina-Zamudio, J., Lefloch, B., Ceccarelli, C., et al. 2018, A&A, 618, A145
Sakai, N., Sakai, T., Hirota, T., & Yamamoto, S. 2008, ApJ, 672, 371
Sanchez-Monge, A., Schilke, P., Ginsburg, A., Cesaroni, R., & Schmiedeke, A.
2017, STATCONT: Statistical continuum level determination method for linerich sources, Astrophysics Source Code Library
Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005,
A&A, 432, 369
Smith, R. J., Longmore, S., & Bonnell, I. 2009, MNRAS, 400, 1775
Sutton, E. C., Peng, R., Danchi, W. C., et al. 1995, ApJS, 97, 455
Tielens, A. G. G. M. 2005, The Physics and Chemistry of the Interstellar Medium
Tigé, J., Motte, F., Russeil, D., et al. 2017, A&A, 602, A77
Tobin, J. J., Bourke, T. L., Mader, S., et al. 2019, ApJ, 870, 81
Valdettaro, R., Palla, F., Brand, J., et al. 2001, A&A, 368, 845
Vastel, C., Bottinelli, S., Caux, E., Glorian, J.-M., & Boiziot, M. 2015, in SF2A2015: Proceedings of the Annual meeting of the French Society of Astronomy
and Astrophysics, ed. F. Martins, S. Boissier, V. Buat, L. Cambrésy, & P. Petit,
313–316
Vastel, C., Ceccarelli, C., Lefloch, B., & Bachiller, R. 2014, ApJ, 795, L2
Vastel, C., Quénard, D., Le Gal, R., et al. 2018, MNRAS, 478, 5514
Vázquez-Semadeni, E., González-Samaniego, A., & Colín, P. 2017, MNRAS,
467, 1313
Walsh, A. J., Burton, M. G., Hyland, A. R., & Robinson, G. 1998, MNRAS, 301,
640
Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275
Watanabe, Y., Sakai, N., López-Sepulcre, A., et al. 2017, ApJ, 847, 108
Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191
Wolfire, M. G. & Cassinelli, J. P. 1987, ApJ, 319, 850
Wu, B., Tan, J. C., Christie, D., et al. 2017, ApJ, 841, 88
Zhang, B., Moscadelli, L., Sato, M., et al. 2014, ApJ, 781, 89


Article number, page 12 of 18

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1


**Table A1.** Spectroscopic parameters of the transitions detected towards core #3 and observed line parameters.

|Frequency Molecule Transition E up Sµ2 log(A ij) ncrit Database<br>[MHz] J= [K] [D2] [s−1] [cm−3]|Line width Velocity R T mbd3<br>[kms−1] [kms−1] [Kkms−1]<br>. . . .|
|---|---|
|216109.78<br>CH3OCHO<br>192,18 −182,17 E<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>216115.57<br>CH3OCHO<br>192,18 −182,17 A<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>216147.36<br>OC33S<br>18 −17<br>98.6<br>9.2<br>-4.04<br>1.3(6) _a_<br>CDMS<br>216210.91<br>CH3OCHO<br>191,18 −181,17 E<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>216216.54<br>CH3OCHO<br>191,18 −181,17 A<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>217044.62<br>13CH3OH<br>141,13 −132,12 - -<br>254.3<br>5.8<br>-4.62<br>1.2(7) _a_<br>CDMS<br>217104.98<br>SiO v=0<br>5 −4<br>31.3<br>48.0<br>-3.28<br>4.8(6)<br>CDMS<br>217191.40<br>CH3OCH3<br>224,19 −223,20<br>253.4<br>327.7<br>-4.27<br>-<br>CDMS<br>217238.54<br>DCN<br>3 −2<br>20.9<br>80.5<br>-3.34<br>-<br>CDMS<br>218127.21<br>CH3COCH3<br>202,18 −193,17 EE<br>119.1<br>1200.4<br>-3.66<br>-<br>JPL<br>218199.00<br>O13CS<br>18 −17<br>99.5<br>9.2<br>-4.52<br>4.1(5) _a_<br>CDMS<br>218222.19<br>H2CO<br>30,3 −20,2<br>21.0<br>16.3<br>-3.55<br>2.6(6)<br>CDMS<br>218280.90<br>CH3OCHO<br>173,14 −163,13 E<br>99.7<br>43.6<br>-3.82<br>-<br>JPL<br>218297.89<br>CH3OCHO<br>173,14 −163,13 A<br>99.7<br>43.6<br>-3.82<br>-<br>JPL<br>218324.72<br>HC3N<br>24 −23<br>131.0<br>334.2<br>-3.08<br>1.7(7)<br>CDMS<br>219505.59<br>C2H5CN<br>242,22 −232,21<br>135.6<br>353.2<br>-3.05<br>-<br>JPL<br>219560.35<br>C18O<br>2 −1<br>15.8<br>0.02<br>-6.22<br>9.9(3) _a_<br>CDMS<br>219908.53<br>H213CO<br>31,2 −21,1<br>32.9<br>43.5<br>-3.59<br>2.3(6) _a_<br>CDMS<br>219949.44<br>SO<br>65 −54<br>35.0<br>14.0<br>-3.87<br>2.3(6)<br>CDMS<br>219983.68<br>CH3OH<br>253 −244 E1<br>802.2<br>8.4<br>-4.70<br>-<br>JPL<br>219993.66<br>CH3OH<br>235 −226 E1<br>775.9<br>6.6<br>-4.76<br>-<br>JPL<br>230315.79<br>CH3CHO<br>122,11 −112,10 E<br>81.1<br>147.4<br>-3.38<br>-<br>JPL<br>230368.76<br>CH3OH<br>224 −215 E1<br>682.8<br>6.6<br>-4.68<br>-<br>JPL<br>230487.94<br>C2H3CN<br>241 −231<br>141.2<br>1045.0<br>-2.50<br>-<br>CDMS<br>230538.00<br>CO<br>2 −1<br>16.6<br>0.02<br>-6.16<br>1.1(4)<br>CDMS<br>230672.55<br>C2H5OH<br>132,11 −122,10<br>138.6<br>20.3<br>-3.97<br>-<br>JPL<br>230738.56<br>C2H3CN<br>250 −240<br>145.5<br>1089.8<br>-2.53<br>-<br>CDMS<br>231060.99<br>OCS<br>19 −18<br>110.9<br>9.7<br>-4.45<br>4.9(5)<br>CDMS<br>231220.68<br>13CS<br>5 −4<br>33.3<br>38.3<br>-3.60<br>4.3(6) _a_<br>JPL<br>231269.90<br>CH3CHO<br>126,7 −116,6 E<br>153.4<br>113.9<br>-3.48<br>-<br>JPL<br>231281.11<br>CH3OH<br>102-−93-<br>165.3<br>2.68<br>-4.73<br>2.5(7)<br>JPL<br>231310.42<br>C2H5CN<br>261,25 −251,24<br>153.4<br>383.1<br>-2.98<br>-<br>JPL<br>231467.50<br>CH3CHO<br>124,8 −114,7 E<br>108.4<br>135.0<br>-3.41<br>-<br>JPL<br>231506.29<br>CH3CHO<br>124,9 −114,8 E<br>108.2<br>135.0<br>-3.41<br>-<br>JPL<br>231595.27<br>CH3CHO<br>123,10 −113,9 E<br>92.6<br>142.3<br>-3.39<br>-<br>JPL<br>231686.68<br>CH18<br>3 OH<br>5−0,5 −4−0,4 E<br>46.2<br>16.2<br>-4.27<br>4.5(5) _a_<br>CDMS<br>231724.16<br>CH3OCHO<br>184,14 −174,13 E<br>300.8<br>45.8<br>-3.75<br>-<br>JPL<br>231735.83<br>CH18<br>3 OH<br>5−1,5 −4−1,4 E<br>39.0<br>15.6<br>-4.29<br>5.8(5) _a_<br>CDMS<br>231748.72<br>CH3CHO<br>123,10 −113,9 E<br>92.5<br>141.1<br>-3.39<br>-<br>JPL<br>231758.45<br>CH18<br>3 OH<br>50,5 −40,4 A<br>33.4<br>16.2<br>-4.27<br>4.5(5) _a_<br>CDMS<br>231796.52<br>CH18<br>3 OH<br>53,2 −43,1 A<br>83.5<br>10.3<br>-4.47<br>4.2(5) _a_<br>CDMS<br>231801.47<br>CH18<br>3 OH<br>52,4 −42,3 A<br>70.8<br>13.8<br>-4.34<br>5.4(5) _a_<br>CDMS<br>231826.74<br>CH18<br>3 OH<br>51,4 −41,3 E<br>54.1<br>16.2<br>-4.27<br>5.6(5) _a_<br>CDMS<br>231840.93<br>CH18<br>3 OH<br>52,3 −42,2 A<br>70.9<br>13.8<br>-4.34<br>5.4(5) _a_<br>CDMS<br>231847.58<br>CH3CHO<br>123,9 −113,8 E<br>92.6<br>141.2<br>-3.39<br>-<br>JPL<br>231864.50<br>CH18<br>3 OH<br>52,3 −42,2 E<br>55.8<br>13.4<br>-4.36<br>5.2(5) _a_<br>CDMS<br>231896.06<br>CH3OCHO<br>194,16 −184,15 E<br>309.7<br>48.14<br>-3.75<br>-<br>JPL<br>231903.90<br>CH3OCHO<br>1912,7 −1812,6 A<br>395.1<br>30.46<br>-3.95<br>-<br>JPL<br>231968.39<br>CH3CHO<br>123,9 −113,8 A<br>92.6<br>142.3<br>-3.38<br>-<br>JPL<br>231987.93<br>CH3OCH3<br>130,13 −121,12<br>80.9<br>271.8<br>-4.04<br>-<br>CDMS<br>232034.63<br>C2H5OH<br>185,14 −184,15<br>175.3<br>18.6<br>-4.13<br>-<br>JPL<br>232160.19<br>CH3OCHO<br>199,10 −189,9 E<br>353.3<br>39.3<br>-3.83<br>-<br>JPL<br>232164.44<br>CH3OCHO<br>1910,10 −1810,9 A<br>365.7<br>36.6<br>-3.86<br>-<br>JPL<br>232194.91<br>13CH3CN<br>133 −123<br>142.4<br>757.2<br>-2.99<br>5.2(6) _a_<br>JPL<br>232216.73<br>13CH3CN<br>132 −122<br>106.7<br>390.4<br>-2.98<br>5.2(6) _a_<br>JPL<br>232229.82<br>13CH3CN<br>131 −121<br>85.2<br>397.6<br>-2.97<br>5.2(6) _a_<br>JPL<br>232234.19<br>13CH3CN<br>130 −120<br>78.0<br>399.9<br>-2.97<br>5.2(6) _a_<br>JPL<br>232273.65<br>HC(O)NH2<br>112,10 −102,9<br>78.9<br>139.0<br>-3.05<br>-<br>CDMS<br>232404.81<br>C2H5OH<br>175,13 −174,14<br>160.1<br>17.5<br>-4.14<br>-<br>JPL<br>232418.52<br>CH3OH<br>102+−93+<br>165.4<br>2.68<br>-4.73<br>2.2(7)<br>JPL|3.9±0.1<br>97.2±0.1<br>33.6±1.2<br>4.9±0.1<br>97.3±0.1<br>41.3±1.4<br>3.7±0.2<br>96.6±0.1<br>8.0±0.8<br>4.4±0.1<br>97.2±0.1<br>37.4±1.4<br>5.1±0.2<br>97.4±0.1<br>40.4±2.8<br>3.1±0.2<br>97.6±0.1<br>15.8±2.1<br>65_b_<br>91.3_b_<br>>86 _b_<br>6.5±0.2<br>96.9±0.1<br>42.9±2.0<br>5.8±0.3<br>96.8±0.1<br>51.4±4.5<br>5.6±0.2<br>97.0±0.1<br>16.1±1.2<br>4.0±0.1<br>97.1±0.1<br>19.1±0.9<br>17_b_<br>98.0_b_<br>>52 _b_<br>4.2±0.1<br>97.2±0.1<br>34.5±1.1<br>4.2±0.1<br>97.1±0.1<br>32.9±1.3<br>5.3±0.1<br>96.6±0.1<br>73.0±2.0<br>4.7±0.1<br>96.9±0.1<br>36.0±1.3<br>4_b_<br>96.0_b_<br>>37 _b_<br>4.6±0.2<br>97.2±0.1<br>35.7±2.5<br>5.6±0.2<br>97.0±0.1<br>56.0±2.2<br>4.4±0.2<br>97.3±0.1<br>18.4±1.5<br>4.2±0.3<br>97.6±0.1<br>16.9±1.8<br>5.8±0.3<br>95.6±0.1<br>36.5±2.6<br>5.0±0.2<br>97.6±0.1<br>30.2±2.2<br>8.0±0.6<br>96.2±0.2<br>20.4±2.4<br>85_b_<br>89.5_b_<br>>550 _b_<br>4.5±0.3<br>97.1±0.1<br>12.4±1.8<br>4.9±0.4<br>96.2±0.3<br>16.9±4.3<br>5.7±0.1<br>96.5±0.1<br>129.2±3.5<br>5.0±0.1<br>97.0±0.1<br>78.9±2.8<br>5.0±0.2<br>97.3±0.1<br>15.4±1.1<br>5.4±0.1<br>97.2±0.1<br>74.5±2.1<br>4.9±0.1<br>96.7±0.1<br>48.0±1.5<br>5.3±0.3<br>96.2±0.1<br>11.6±1.0<br>6.0±0.6<br>97.3±0.2<br>17.2±2.7<br>7.0±1.0<br>95.7±0.3<br>9.8±2.3<br>4.6±0.4<br>97.4±0.1<br>7.8±1.2<br>4.0±0.3<br>97.3±0.1<br>7.6±1.0<br>5.2±0.3<br>96.5±0.1<br>11.6±1.2<br>5.7±0.2<br>96.5±0.1<br>12.3±0.9<br>4.7±0.3<br>97.1±0.1<br>9.0±1.1<br>5.4±1.4<br>97.8±0.4<br>8.6±3.4<br>4.2±0.5<br>96.8±0.1<br>8.0±1.4<br>4.5±0.5<br>97.1±0.2<br>6.7±1.2<br>4.2±0.7<br>97.4±0.2<br>6.3±1.5<br>6.2±0.8<br>97.1±0.2<br>13.3±2.7<br>4.0±0.2<br>97.3±0.1<br>6.0±0.7<br>4.5±0.2<br>97.2±0.1<br>8.5±0.7<br>6.4±0.5<br>97.5±0.2<br>8.2±1.1<br>4.8±0.3<br>96.9±0.1<br>12.1±1.3<br>6.8±0.3<br>96.2±0.1<br>57.1±4.7<br>5.4±0.5<br>96.8±0.2<br>6.3±1.2<br>4.7±0.9<br>97.2±0.2<br>9.6±2.8<br>4.6±0.7<br>97.5±0.3<br>12.7±3.0<br>5.1±0.3<br>97.1±0.1<br>17.4±2.1<br>4.9±0.3<br>97.2±0.2<br>14.6±1.9<br>4.2±0.5<br>97.2±0.2<br>13.9±2.5<br>5.2±0.5<br>97.1±0.2<br>17.1±2.8<br>7.3±0.2<br>97.5±0.1<br>13.2±1.1<br>4.5±0.5<br>97.0±0.2<br>6.7±1.2<br>5.4±0.4<br>97.1±0.1<br>38.8±3.5|



Article number, page 13 of 18

_A&A proofs:_ manuscript no. aa35497-19


**Table A1.** continued.

|Frequency Molecule Transition E up Sµ2 log(A ij) ncrit Database<br>[MHz] J= [K] [D2] [s−1] [cm−3]|Line width Velocity R T mbd3<br>[kms−1] [kms−1] [Kkms−1]<br>. . . .|
|---|---|
|232683.93<br>CH3OCHO<br>1910,10 −1810,9 E<br>365.5<br>36.7<br>-3.86<br>-<br>JPL<br>232738.62<br>CH3OCHO<br>198,11 −188,10 E<br>342.0<br>41.6<br>-3.80<br>-<br>JPL<br>232754.71<br>H2C34S<br>71,7 −61,6<br>57.9<br>55.9<br>-3.74<br>2.0(6) _a_<br>CDMS<br>232783.45<br>CH3OH<br>183 + −174+<br>446.54<br>5.46<br>-4.66<br>-<br>JPL<br>232790.02<br>C2H5CN<br>263,24 −253,25<br>161.0<br>380.0<br>-2.98<br>-<br>JPL<br>232836.17<br>CH3OCHO<br>198,12 −188,11 A<br>341.8<br>41.6<br>-3.81<br>-<br>JPL<br>232839.68<br>CH3OCHO<br>198,11 −188,10 A<br>341.8<br>41.6<br>-3.80<br>-<br>JPL<br>232865.05<br>CH3COCH3<br>178,10 −167,9 EE<br>114.8<br>1121.9<br>-3.53<br>-<br>JPL<br>232945.80<br>CH3OH<br>10−3 −11−2 E2<br>190.4<br>3.0<br>-4.67<br>1.6(7)<br>JPL<br>232962.32<br>C2H5CN<br>2610 −2510<br>261.6<br>328.4<br>-3.04<br>-<br>JPL<br>232967.57<br>C2H5CN<br>269 −259<br>240.9<br>339.2<br>-3.03<br>-<br>JPL<br>232975.51<br>C2H5CN<br>2611 −2511<br>285.2<br>316.4<br>-3.06<br>-<br>JPL<br>232998.74<br>C2H5CN<br>268 −258<br>222.0<br>348.9<br>-3.01<br>-<br>JPL<br>233002.70<br>C2H5CN<br>2612 −2512<br>310.7<br>303.3<br>-3.07<br>-<br>JPL<br>233041.09<br>C2H5CN<br>2613 −2513<br>338.3<br>289.1<br>-3.09<br>-<br>JPL<br>233069.37<br>C2H5CN<br>267 −257<br>205.4<br>357.5<br>-3.00<br>-<br>JPL<br>233088.86<br>C2H5CN<br>2614 −2514<br>368.2<br>273.6<br>-3.12<br>-<br>JPL<br>233193.36<br>CH3OCH3<br>222,21 −221,22<br>232.9<br>135.6<br>-4.56<br>-<br>CDMS<br>233226.79<br>CH3OCHO<br>194,16 −184,15 A<br>123.2<br>48.0<br>-3.74<br>-<br>JPL<br>233246.79<br>CH3OCHO<br>1916,3 −1816,2 A<br>281.8<br>14.8<br>-4.25<br>-<br>JPL<br>233268.59<br>CH3OCHO<br>1916,4 −1816,3 E<br>281.8<br>14.8<br>-4.25<br>-<br>JPL<br>233277.94<br>C2H5CN<br>2617 −2517<br>470.6<br>220.7<br>-3.21<br>-<br>JPL<br>233310.12<br>CH3OCHO<br>1915,5 −1815,4 A<br>261.3<br>19.1<br>-4.14<br>-<br>JPL<br>233315.78<br>CH3OCHO<br>1915,4 −1815,3 E<br>261.3<br>19.1<br>-4.14<br>-<br>JPL<br>233331.21<br>CH3OCHO<br>1915,5 −1815,4 E<br>261.3<br>19.1<br>-4.14<br>-<br>JPL<br>233394.66<br>CH3OCHO<br>1914,6 −1814,5 A<br>242.1<br>23.2<br>-4.06<br>-<br>JPL<br>233414.43<br>CH3OCHO<br>1914,6 −1814,5 E<br>242.1<br>23.2<br>-4.06<br>-<br>JPL<br>233443.10<br>C2H5CN<br>265,22 −255,21<br>178.8<br>371.1<br>-2.98<br>-<br>JPL<br>233498.30<br>C2H5CN<br>265,21 −255,20<br>178.9<br>371.1<br>-2.98<br>-<br>JPL<br>233553.24<br>CH3OCHO<br>197,12 −187,11 A<br>332.0<br>43.7<br>-3.78<br>-<br>JPL<br>233571.02<br>C2H5OH<br>135,8 −134,9<br>107.9<br>12.8<br>-4.15<br>-<br>JPL<br>233632.27<br>CH3OCH3<br>255,20 −254,21<br>331.9<br>402.9<br>-4.13<br>-<br>CDMS<br>233649.88<br>CH3OCHO<br>1912,7 −1812,6 E<br>207.6<br>30.5<br>-3.94<br>-<br>JPL<br>233655.34<br>CH3OCHO<br>1912,7 −1812,6 A<br>207.6<br>30.5<br>-3.94<br>-<br>JPL<br>233670.98<br>CH3OCHO<br>1912,8 −1812,7 E<br>207.6<br>30.5<br>-3.94<br>-<br>JPL<br>233727.94<br>CH18<br>3 OH<br>51,4 −41,3 A<br>48.0<br>15.6<br>-4.28<br>5.5(5) _a_<br>CDMS<br>233734.72<br>HC(O)NH2<br>114,8 −104,7<br>114.9<br>124.8<br>-3.03<br>-<br>CDMS<br>233745.61<br>HC(O)NH2<br>114,7 −104,6<br>114.9<br>124.8<br>-3.03<br>-<br>CDMS<br>233753.96<br>CH3OCHO<br>184,14 −174,13 E<br>114.4<br>45.8<br>-3.74<br>-<br>JPL<br>233777.52<br>CH3OCHO<br>184,14 −174,13 A<br>114.4<br>45.8<br>-3.74<br>-<br>JPL<br>233795.67<br>CH3OH<br>183 −−174−<br>446.59<br>5.5<br>-4.66<br>-<br>JPL<br>233845.23<br>CH3OCHO<br>1911,8 −1811,7 E<br>192.4<br>33.7<br>-3.89<br>-<br>JPL<br>233854.29<br>CH3OCHO<br>1911,9 −1811,8 A<br>192.4<br>33.7<br>-3.89<br>-<br>JPL<br>233867.19<br>CH3OCHO<br>1911,9 −1811,8 E<br>192.4<br>33.7<br>-3.89<br>-<br>JPL<br>233896.58<br>HC(O)NH2<br>113,9 −103,8<br>94.1<br>133.1<br>-3.03<br>-<br>CDMS<br>233916.95<br>CH3OH<br>133 −−144−<br>868.5<br>2.5<br>-5.26<br>-<br>JPL<br>233951.12<br>C2H5OH<br>135,9 −134,10<br>107.9<br>12.8<br>-4.15<br>-<br>JPL<br>234011.58<br>13CH3OH<br>51,5 −41,4 ++<br>48.3<br>3.9<br>-4.28<br>1.1(7) _a_<br>CDMS<br>234112.33<br>CH3OCHO<br>1910,9 −1810,8 E<br>178.5<br>36.6<br>-3.85<br>-<br>JPL<br>234124.88<br>CH3OCHO<br>1910,9 −1810,8 A<br>178.5<br>36.6<br>-3.85<br>-<br>JPL<br>234134.60<br>CH3OCHO<br>1910,10 −1810,9 E<br>178.5<br>36.6<br>-3.85<br>-<br>JPL<br>234255.16<br>C2H5OH<br>125,8 −124,9<br>96.9<br>11.6<br>-4.16<br>-<br>JPL<br>234315.50<br>HC(O)NH2<br>113,8 −103,7<br>94.1<br>133.1<br>-3.03<br>-<br>CDMS<br>234336.11<br>CH3OCHO<br>196,14 −186,13 A<br>323.5<br>45.5<br>-3.76<br>-<br>JPL<br>234381.27<br>CH3OCHO<br>195,15 −185,14 A<br>316.4<br>46.9<br>-3.74<br>-<br>JPL<br>234406.45<br>C2H5OH<br>115,6 −114,7<br>86.8<br>10.4<br>-4.17<br>-<br>JPL<br>234423.96<br>C2H5CN<br>264,22 −254,21<br>169.1<br>376.3<br>-2.98<br>-<br>JPL|4.2±0.3<br>97.6±0.1<br>7.8±1.1<br>4.5±0.2<br>97.2±0.1<br>11.0±0.8<br>4.9±0.6<br>96.8±0.3<br>12.0±2.0<br>4.9±0.2<br>97.1±0.1<br>50.4±3.3<br>5.6±0.4<br>97.0±0.1<br>46.5±5.1<br>3.5±0.2<br>97.0±0.1<br>8.5±0.7<br>4.2±0.7<br>97.5±0.3<br>9.5±2.2<br>4.7±0.6<br>97.4±0.5<br>5.0±1.1<br>5.8±0.3<br>97.0±0.1<br>78.7±6.3<br>5.4±0.3<br>97.3±0.1<br>37.3±3.2<br>6.2±0.8<br>97.0±0.3<br>44.2±8.3<br>5.3±0.1<br>96.8±0.1<br>34.4±1.2<br>4.6±0.5<br>97.3±0.2<br>36.7±5.9<br>5.0±0.3<br>97.3±0.1<br>30.3±2.4<br>5.1±0.3<br>97.3±0.1<br>22.8±2.4<br>5.0±0.2<br>96.9±0.1<br>42.6±3.3<br>5.8±0.2<br>97.0±0.1<br>21.0±1.3<br>4.6±0.6<br>96.8±0.2<br>17.1±3.7<br>4.9±0.4<br>97.3±0.2<br>41.1±5.7<br>4.6±0.4<br>96.5±0.2<br>11.0±1.6<br>5.5±0.3<br>97.2±0.1<br>11.4±1.1<br>4.5±0.6<br>97.3±0.2<br>7.7±2.0<br>5.0±0.1<br>97.4±0.1<br>20.1±0.6<br>5.8±0.6<br>97.0±0.2<br>13.2±2.1<br>4.6±0.7<br>97.0±0.3<br>10.1±2.6<br>6.0±0.3<br>98.5±0.1<br>34.9±3.1<br>5.2±0.4<br>97.1±0.1<br>15.7±1.9<br>5.7±0.4<br>97.3±0.1<br>42.4±4.8<br>5.2±0.2<br>97.2±0.1<br>41.5±2.7<br>5.8±0.4<br>97.1±0.1<br>20.1±2.2<br>5.2±0.5<br>97.5±0.2<br>15.5±2.6<br>5.5±0.2<br>97.3±0.1<br>35.1±1.9<br>4.0±0.1<br>97.2±0.1<br>19.6±0.7<br>6.6±0.8<br>97.8±0.4<br>64.6±11.3<br>4.6±0.3<br>97.1±0.1<br>19.5±2.2<br>4.5±0.4<br>97.3±0.2<br>14.8±2.3<br>6.8±0.3<br>96.6±0.1<br>17.4±1.5<br>5.3±0.4<br>97.5±0.1<br>13.5±1.6<br>5.4±0.3<br>97.3±0.1<br>45.4±4.2<br>4.2±0.2<br>97.1±0.1<br>35.3±3.0<br>5.0±0.3<br>96.9±0.1<br>49.2±5.9<br>5.4±0.2<br>97.3±0.1<br>26.4±1.6<br>4.2±0.2<br>97.1±0.1<br>28.6±2.7<br>4.3±0.4<br>96.9±0.2<br>20.6±3.3<br>6.2±0.5<br>97.3±0.2<br>19.8±2.9<br>4.9±0.4<br>97.1±0.2<br>13.3±2.0<br>5.2±0.3<br>97.2±0.1<br>18.3±1.6<br>4.7±0.2<br>96.9±0.1<br>35.3±2.3<br>5.0±0.2<br>97.4±0.1<br>28.2±2.2<br>4.7±0.3<br>96.9±0.1<br>35.5±4.3<br>4.8±0.3<br>97.4±0.1<br>27.6±2.7<br>4.6±0.4<br>97.1±0.2<br>12.2±2.0<br>6.3±0.4<br>96.8±0.2<br>17.4±2.4<br>4.6±0.4<br>97.2±0.2<br>14.5±2.2<br>4.4±0.2<br>97.0±0.1<br>16.9±1.7<br>4.4±0.1<br>97.2±0.1<br>11.2±0.7<br>5.3±0.1<br>97.2±0.1<br>42.9±1.4|



_Notes_ : All observational values are integrated over the continuum core.
_a_ Collision rate value from the main isotopologue.
_b_ The line is self-absorbed or filtered. The values correspond to the zero-base line width, the velocity of the line maximum, and the
integration of the positive _T_ mb values.


Article number, page 14 of 18

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1


**Table A2.** Same as Table A1 but towards core #6.

|Frequency Molecule Transition E up Sµ2 log(A ij) ncrit Database<br>[MHz] J= [K] [D2] [s−1] [cm−3]|Line width Velocity R T mbd3<br>[kms−1] [kms−1] [Kkms−1]<br>. . . .|
|---|---|
|216109.78<br>CH3OCHO<br>192,18 −182,17 E<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>216115.57<br>CH3OCHO<br>192,18 −182,17 A<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>216147.36<br>OC33S<br>18 −17<br>98.6<br>9.2<br>-4.04<br>1.3(6) _a_<br>CDMS<br>216210.91<br>CH3OCHO<br>191,18 −181,17 E<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>216216.54<br>CH3OCHO<br>191,18 −181,17 A<br>109.3<br>49.4<br>-3.83<br>-<br>JPL<br>217104.98<br>SiO v=0<br>5 −4<br>31.3<br>48.0<br>-3.28<br>4.8(6)<br>CDMS<br>217238.54<br>DCN<br>3 −2<br>20.9<br>80.5<br>-3.34<br>-<br>CDMS<br>218199.00<br>O13CS<br>18 −17<br>99.5<br>9.2<br>-4.52<br>4.1(5) _a_<br>CDMS<br>218222.19<br>H2CO<br>30,3 −20,2<br>21.0<br>16.3<br>-3.55<br>2.6(6)<br>CDMS<br>218280.90<br>CH3OCHO<br>173,14 −163,13 E<br>99.7<br>43.6<br>-3.82<br>-<br>JPL<br>218297.89<br>CH3OCHO<br>173,14 −163,13 A<br>99.7<br>43.6<br>-3.82<br>-<br>JPL<br>218324.72<br>HC3N<br>24 −23<br>131.0<br>334.2<br>-3.08<br>1.7(7)<br>CDMS<br>219560.35<br>C18O<br>2 −1<br>15.8<br>0.02<br>-6.22<br>9.9(3) _a_<br>CDMS<br>219908.53<br>H213CO<br>31,2 −21,1<br>32.9<br>43.5<br>-3.59<br>2.3(6) _a_<br>CDMS<br>219949.44<br>SO<br>65 −54<br>35.0<br>14.0<br>-3.87<br>2.3(6)<br>CDMS<br>230315.79<br>CH3CHO<br>122,11 −112,10 E<br>81.1<br>147.4<br>-3.38<br>-<br>JPL<br>230538.00<br>CO<br>2 −1<br>16.6<br>0.02<br>-6.16<br>1.1(4)<br>CDMS<br>231060.99<br>OCS<br>19 −18<br>110.9<br>9.7<br>-4.45<br>4.9(5)<br>CDMS<br>231220.68<br>13CS<br>5 −4<br>33.3<br>38.3<br>-3.60<br>4.3(6) _a_<br>JPL<br>231269.90<br>CH3CHO<br>126,7 −116,6 E<br>153.4<br>113.9<br>-3.48<br>-<br>JPL<br>231281.11<br>CH3OH<br>102-−93-<br>165.3<br>2.68<br>-4.73<br>2.5(7)<br>JPL<br>231467.50<br>CH3CHO<br>124,8 −114,7 E<br>108.4<br>135.0<br>-3.41<br>-<br>JPL<br>231506.29<br>CH3CHO<br>124,9 −114,8 E<br>108.2<br>135.0<br>-3.41<br>-<br>JPL<br>231595.27<br>CH3CHO<br>123,10 −113,9 E<br>92.6<br>142.3<br>-3.39<br>-<br>JPL<br>231748.72<br>CH3CHO<br>123,10 −113,9 E<br>92.5<br>141.1<br>-3.39<br>-<br>JPL<br>231987.93<br>CH3OCH3<br>130,13 −121,12 AE<br>80.9<br>101.9<br>-4.04<br>-<br>CDMS<br>232418.52<br>CH3OH<br>102+−93+<br>165.4<br>2.68<br>-4.73<br>2.2(7)<br>JPL<br>232945.80<br>CH3OH<br>10−3 −11−2 E2<br>190.4<br>3.0<br>-4.67<br>1.6(7)<br>JPL<br>233226.79<br>CH3OCHO<br>194,16 −184,15 A<br>123.2<br>48.0<br>-3.74<br>-<br>JPL<br>233753.96<br>CH3OCHO<br>184,14 −174,13 E<br>114.4<br>45.8<br>-3.74<br>-<br>JPL<br>233777.52<br>CH3OCHO<br>184,14 −174,13 A<br>114.4<br>45.8<br>-3.74<br>-<br>JPL<br>234011.58<br>13CH3OH<br>51,5 −41,4 ++<br>48.3<br>3.9<br>-4.28<br>1.1(7) _a_<br>CDMS|3.2±0.9<br>95.5±0.4<br>2.1±0.5<br>3.8±1.5<br>95.9±0.4<br>2.8±0.8<br>2.1±0.6<br>95.4±0.3<br>1.1±0.3<br>1.8±0.4<br>95.1±0.2<br>1.8±0.4<br>2.4±0.9<br>95.9±0.4<br>1.6±0.5<br>5.1±0.7<br>95.8±0.3<br>20.0±0.6<br>1.7±0.3<br>95.6±0.1<br>3.6±0.4<br>2.1±0.4<br>95.1±0.2<br>2.0±0.3<br>22 _b_<br>94.8 _b_<br>>45 _b_<br>2.8±0.5<br>96.1±0.2<br>2.0±0.4<br>4.0±0.6<br>95.2±0.4<br>2.4±0.4<br>4.4±0.5<br>96.3±0.2<br>10.7±0.9<br>10.5 _b_<br>95.5 _b_<br>>14 _b_<br>2.4±0.6<br>96.0±0.2<br>6.3±1.2<br>3.5±0.3<br>96.1±0.1<br>18.3±1.0<br>2.9±1.1<br>95.3±0.2<br>3.5±1.3<br>-<br>-<br>>25 _b_<br>3.7±0.2<br>95.7±0.1<br>11.6±0.4<br>3.4±0.3<br>95.4±0.1<br>6.6±0.5<br>3.3±1.0<br>96.4±0.3<br>2.7±0.6<br>3.3±0.6<br>95.9±0.3<br>3.2±0.5<br>1.5±0.3<br>95.1±0.1<br>1.4±0.2<br>1.4±0.5<br>95.9±0.2<br>1.1±0.3<br>3.7±0.9<br>95.3±0.5<br>1.4±0.4<br>2.9±1.1<br>95.6±0.5<br>1.4±0.4<br>2.3±0.7<br>95.9±0.2<br>1.5±0.4<br>2.8±0.6<br>96.2±0.3<br>1.3±0.3<br>3.7±0.8<br>95.6±0.5<br>1.9±0.4<br>2.9±1.0<br>95.4±0.6<br>1.8±0.6<br>2.9±1.2<br>96.2±0.6<br>1.7±0.7<br>2.9±0.8<br>96.1±0.4<br>2.3±0.6<br>5.2±0.5<br>96.5±0.2<br>5.2±1.8|



_Notes_ : All observational values are integrated over the continuum core.
_a_ Collision rate value from the main isotopologue.
_b_ The line is self-absorbed or filtered. The values correspond to the zero-base line width, the velocity of the line maximum, and the
integration of the positive _T_ mb values.


Article number, page 15 of 18

_A&A proofs:_ manuscript no. aa35497-19


**Table A3.** Column densities in core #3 estimated for a source size of 1000 au and a temperature of 190 K.


Molecule _N_ [cm [−][2] ]
C [18] O >8.4(17)
CH 3 OH 1.4(18)
13 CH 3 OH 2.8(17)
CH 3 CHO 3.8(16)
13 CS 3.2(15)
CH 3 OCH 3 4.7(17)
CH 3 OCHO 3.8(17)
OCS 1.0(17)
O [13] CS 1.2(16)
OC [33] S 5.5(15)
SiO v=0 >1.9(15)
SO 1.5(16)
H 2 CO >2.0(16)
H [13] 2 [CO] 7.8(15)
HC 3 N 2.4(15)
DCN 1.5(15)
CO >2.1(19)
CH [18] 3 [OH] 8.2(16)
13 CH 3 CN 1.9(15)
HC(O)NH 2 3.9(15)
C 2 H 5 OH 7.2(16)
H 2 C [34] S 4.0(15)
CH 3 COCH 3 9.0(16)
C 2 H 3 CN 8.3(15)
C 2 H 5 CN 1.7(16)
Column densities estimated from the isotopologues
CH 3 OH 2.0(19)
CS 1.4(17)
OCS 5.2(17)
H 2 CO 3.5(17)
CO >3.8(19)


_Note_ : _a_ ( _b_ ) = _a_ × 10 _[b]_ .


Article number, page 16 of 18

J. Molet et al.: Molecular analysis of a high-mass prestellar core candidate in W43-MM1



8.8


4.4


0.0


3


3
216.1 216.2 216.3


17.4


8.7


0.0


3


3


9.9


4.9


0.0


3


3

219.9 219.95


21.6


10.8


0.0


3


3
231.1 231.2 231.3 231.4 231.5



10.5


5.2


0.0


3


3
217.1 217.2


13.5


6.8


0.0


3


3


8


4


0


3


3


7.8


3.9


0.0


3


3



12.6


6.3


0.0


3


3

233 233.5 234

Frequency [GHz]


**Fig. A1.** Observed spectra (in black), synthetic spectra (in red) and residuals (in orange) towards core #3 for all the ALMA bands. The observed
spectra are integrated over the continuum cores (see Table 2). All the molecular lines detected in core #6 (see Table A2) are indicated by black
dotted lines and some of the additional molecular lines detected in core #3 are indicated in grey. The parameters used for the synthetic spectra are
listed in Table 3. The Cycle 3 spectral band Cont. 1, which overlaps with Cycle 2 data Cont. 2, is ignored here.


Article number, page 17 of 18

_A&A proofs:_ manuscript no. aa35497-19



0.7


0.3


0.0


1


1


2


1


0


1


1


4.8


2.4


0.0


1


1
219.9 219.95 220


2.8


1.4


0.0


1


1
231.1 231.2 231.3 231.4 231.5


1.0


0.5


0.0


1


1



2.9


1.4


0.0


1


1
217.1 217.2


5.0


2.5


0.0


1


1
219.55 219.6


3.5


1.7


0.0


1


1


0.6


0.3


0.0


1


1

232 232.5





**Fig. A2.** Same as Fig. A1 but for source #6. The spectra are Hanning smoothed to the same frequency resolution, ∆ _f_ = 0.976 MHz. The synthetic
spectra are calculated for a temperature of 30 K, which corresponds to the very beginning of the protostellar phase.


Article number, page 18 of 18


</paper>

## Items to check

```json
[
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Rotational diagrams",
  "failed_quote": "The rotational diagrams were performed using the CASSIS software (Vastel et al. 2015)."
 }
]
```
