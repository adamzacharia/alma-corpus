# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...967..164X\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version April 22, 2024
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Maser** **Activity** **of** **Organic** **Molecules** **toward** **Sgr** **B2(N)**


Ci [Xue,](http://orcid.org/0000-0003-2760-2119) [1, 2] [Anthony](http://orcid.org/0000-0001-9479-9287) Remijan, [3] [Alexandre](http://orcid.org/0000-0001-7199-2535) Faure, [4] [Emmanuel](http://orcid.org/0000-0003-3168-5922) Momjian, [5] Todd R. Hunter, [3] Ryan [A.](http://orcid.org/0000-0002-8932-1219) Loomis, [3]

Eric Herbst, [2] and Brett [McGuire](http://orcid.org/0000-0003-1254-4817) [1, 3]


1 _Department_ _of_ _Chemistry,_ _Massachusetts_ _Institute_ _of_ _Technology,_ _Cambridge,_ _MA_ _02139,_ _USA_
2 _Department_ _of_ _Chemistry,_ _University_ _of_ _Virginia,_ _Charlottesville,_ _VA_ _22904,_ _USA_
3 _National_ _Radio_ _Astronomy_ _Observatory,_ _Charlottesville,_ _VA_ _22903,_ _USA_
4 _Universit´e_ _Grenoble_ _Alpes,_ _CNRS,_ _IPAG,_ _F-38000_ _Grenoble,_ _France_
5 _National_ _Radio_ _Astronomy_ _Observatory,_ _Socorro,_ _NM_ _87801,_ _USA_


ABSTRACT


At centimeter wavelengths, single-dish observations have suggested that the Sagittarius (Sgr) B2
molecular cloud at the Galactic Center hosts weak maser emission from several organic molecules,
including CH 2 NH, HNCNH, and HCOOCH 3 . However, the lack of spatial distribution information of
these new maser species has prevented us from assessing the excitation conditions of the maser emission
as well as their pumping mechanisms. Here, we present a mapping study toward Sgr B2 North (N) to
locate the region where the complex maser emission originates. We report the first detection of the
Class I methanol (CH 3 OH) maser at 84 GHz and the first interferometric map of the methanimine
(CH 2 NH) maser at 5.29 GHz toward this region. In addition, we present a tool for modeling and fitting
the unsaturated molecular maser signals with non-LTE radiative transfer models and Bayesian analysis
using the Markov-Chain Monte Carlo approach. These enable us to quantitatively assess the observed
spectral profiles. The results suggest a two-chain-clump model for explaining the intense CH 3 OH Class I
maser emission toward a region with low continuum background radiation. By comparing the spatial
origin and extent of maser emission from several molecular species, we find that the 5.29 GHz CH 2 NH
maser has a close spatial relationship with the 84 GHz CH 3 OH Class I masers. This relationship
serves as observational evidence to suggest a similar collisional pumping mechanism for these maser

transitions.


_Keywords:_ Interstellar masers, Radiative transfer, Galactic center, Spectral line identification



1. INTRODUCTION


Maser emission from molecular species has provided
critical insights into the kinetic properties of young stars
and has even enabled monitoring of their accretion processes (Hunter et al. 2018, and references therein). Energetic events (e.g., outflows and collimated jets) and
infrared radiation surrounding massive protostars provide the energy to overpopulate the upper energy levels
of specific molecular transitions and amplify the molecular emission intensities (Moscadelli et al. 2016; Sanna
et al. 2016). Common species exhibiting maser emission
include, but are not limited to, OH, SiO, H 2 O, H 2 CO,
NH 3, and CH 3 OH. An empirical taxonomy based on
pumping mechanisms classifies molecular masers into


Corresponding author: Ci Xue

cixue@mit.edu



two categories (Batrla et al. 1987; Cyganowski et al.
2009); H 2 O and Class I CH 3 OH masers are most often excited via collisions and tend to reside in shocked
material associated with outflows and expanding H II
regions (e.g. Baudry et al. 1974; Elitzur & Fuqua 1989;
Voronkov et al. 2014; Towner et al. 2017), while OH
and Class II CH 3 OH masers are excited via radiation
and are generally close to young stellar objects and luminous infrared sources (e.g., Sobolev & Deguchi 1994;
Sobolev et al. 1997; Cragg et al. 2002, 2005). The most
extensively studied Class I CH 3 OH masers include the
4 _−_ 1 _−_ 3 0 _E_ transition at 36 GHz and the 7 0 _−_ 6 1 _A_ transition at 44 GHz, while Class II CH 3 OH masers include
the 5 1 _−_ 6 0 _A_ transition at 6 _._ 7 GHz and the 2 0 _−_ 3 _−_ 1 _E_
transition at 12 _._ 2 GHz (e.g. Voronkov et al. 2014; Song
et al. 2022).
By correlating the maser emission from various species
with a sample of star-forming regions at different stages,

2


statistical analyses have also suggested that masers may
help to trace the evolutionary phases of massive stars
(e.g. Figure 6 in Breen et al. 2010). For example, Forster
& Caswell (1989) found that isolated H 2 O masers tend
to appear in sources at earlier evolutionary stages than
OH masers based on a survey toward 74 star-forming
regions. In addition, Class II CH 3 OH masers, which appear exclusively in massive star-forming regions (Breen
et al. 2013; Xu et al. 2008), typically have a significant
overlapping timeline with H 2 O masers and arise before
the OH masers and ultra-compact (UC) H II regions
turn on (Walsh et al. 2003; Szymczak et al. 2005).
However, within the picture of massive star formation,
the position for Class I CH 3 OH masers in an evolutionary sequence is less clear. Initial comparisons of the
mid-infrared properties of the sample of CH 3 OH maser
sources suggested that Class I masers are signposts of
the earliest stage of massive star formation, even prior
to H 2 O masers (Ellingsen 2006). In contrast, detailed
mapping of multiple Class I CH 3 OH maser transitions
toward a luminous young stellar object, IRAS 165474247, led Voronkov et al. (2006) to argue that Class I
CH 3 OH masers can appear earlier than the Class II
masers but also last long enough to coexist with the
OH masers. Subsequent observations toward the massive protocluster G18.67+0.03 further suggested that
the Class I CH 3 OH masers might associate with both
young sites and relatively evolved UC H II regions within
the same protocluster (Cyganowski et al. 2012). In any
case, high angular resolution imaging is essential for determining which protostar(s) within a protocluster currently power these masers (Towner et al. 2017).
Recently, new maser species, such as HNCO and
CH 2 NH, have been discovered to exhibit compelling
roles in inferring fine-scale structures and gas dynamics in the maser region. In particular, the HNCO maser
was found to be associated with accretion flows, which
helped to build an arm-spiral-structure model of one
particular high-mass young stellar object (Chen et al.
2020); and the CH 2 NH maser toward galactic nuclei
helps to probe the inner nuclear processes in extragalactic environments (Gorski et al. 2021). The pumping
mechanism of these new maser species, however, is less
constrained, as is their relation to other common maser
species. Observations of these species in maser-active
regions that contain both known collisionally and radiatively pumped masers are therefore critical as a first step
in understanding their pumping mechanisms.
The high-mass star-forming region Sgr B2 North
(N) displays rich maser activity from a diverse set of
molecules, ranging from common maser species to rare
complex molecules (Morita et al. 1992; McGrath et al.



2004; Hoffman et al. 2007; Qiao et al. 2018; Fujisawa
et al. 2014). The single-dish PRebiotic Interstellar
MOlecular Survey (PRIMOS) project has identified numerous species exhibiting maser activity at centimeter wavelengths. In fact, the discovery of interstellar
carbodiimide (HNCNH) was only achievable due to its
maser emission (McGuire et al. 2012). Radiative transfer calculations have also revealed that most emission
lines of both methyl formate (HCOOCH 3 ) and CH 2 NH
detected in PRIMOS are weak masers amplifying the
background continuum radiation of Sgr B2(N) at cm
wavelengths (Faure et al. 2014, 2018). However, the
large _∼_ 2 _._ 5 _[′]_ _×_ 2 _._ 5 _[′]_ field of view of PRIMOS at C band
( _∼_ 5 GHz) includes both the North and Main components of Sgr B2, complicating the interpretation of the
spectral profiles. Therefore, it is crucial to have interferometric observations to disentangle in detail the various
possible spatial components of maser emission.
In this work, we present a rigorous imaging study of
maser emission from CH 3 OH and CH 2 NH toward Sgr
B2(N). We describe the interferometric observations at
centimeter (cm) and millimeter (mm) wavelengths in
Section 2. A description of the methodology employed
to model maser emission is described in Section 3, which
includes the implementation of a Bayesian inference of
physical characteristics. Section 4 presents both the
spectra and spatial distribution per maser species. Section 5 contains discussions on the metastable states of
maser transitions (Section 5.1), pumping mechanisms
inferred from the spatial correlations (Section 5.2), derived physical conditions of masing gas clumps (Section 5.3), and a caveat on modeling maser intensity (Section 5.4).


2. OBSERVATIONS


The interferometric data used here were acquired
from two data sets involving the Karl G. Jansky Very
Large Array (VLA) in C-band (nominal frequency
coverage 4-8 GHz) and the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 3 (nominal
frequency coverage 84–116 GHz).


_VLA_ _Observations_ — The VLA observations were carried out on 2016 May 27 (project code: 16A-076, P.I.:
B. McGuire) with the C-band receiver. The correlator
was configured to deliver 24 subbands or spectral windows, with bandwidths of 4, 8, and 16 MHz, to target
various spectral lines. Additionally, nine 128 MHz spectral windows were set up to help with calibration, if
needed. The results presented here are based on three
spectral windows that delivered channel widths between
0 _._ 485 km s _[−]_ [1] and 2 _._ 31 km s _[−]_ [1], depending on the corresponding bandwidth and observing frequency. Detailed

observational parameters of each spectral window are
presented in Table 1. The phase center of the observations was targeted toward Sgr B2 (N), with the field
center at _α_ J2000 = 17 [h] 47 [m] 19 [s] _._ 80, _δ_ J2000 = _−_ 28 _[◦]_ 22 _[′]_ 17 _[′′]_ _._ 00.
The bandpass and absolute flux density scale calibrator was 3C286, while the complex gain calibrator was
J1744-3116. The array was in the B configuration with
27 antennas, which covered baselines from 250 m up to
11 km and resulted in the maximum recoverable scale of

37 _[′′]_ at 4 GHz.
The `CASA` software package (version 5.6.1, CASA
Team et al. 2022) was used for data reduction and imaging analysis of the VLA observations. For each spectral
window, the continuum emission was subtracted in the
_uv_ -plane before imaging the spectral cubes. We used the
`tclean` task with the auto-masking algorithm for imaging with the natural weighting scheme and a cell size
of 0 _._ 27 _[′′]_ . The resulting size of the synthesized beam
(FWHM) of each image cube has a median value of
_∼_ 3 _._ 8 _[′′]_ _×_ 1 _._ 5 _[′′]_ . The median of the resultant typical RMS
noise levels is _∼_ 0 _._ 9 mJy beam _[−]_ [1] .


_ALMA_ _Observations_ — The ALMA observational data

were acquired from the ALMA Science Archive of
the survey project entitled “Exploring Molecular
Complexity with ALMA (EMoCA)” (project code:
2011.0.00017.S, P.I.: A. Belloche). A detailed description of the EMoCA data has been presented in Belloche
et al. (2016). In this work, two measurement sets, spectral window 0 of setup S1 and spectral window 0 of
setup S4 (Xue et al. 2019), were used for imaging the
84 GHz and 95 GHz CH 3 OH transitions. Different from
Xue et al. (2019), we used the `tclean` task with the
auto-masking algorithm for the imaging analysis, consistent with the VLA imaging process. The resultant
synthesized beam size is 2 _._ 23 _[′′]_ _×_ 1 _._ 67 _[′′]_ at 84 GHz and
1 _._ 94 _[′′]_ _×_ 1 _._ 49 _[′′]_ at 95 GHz with a median RMS value of
4 mJy beam _[−]_ [1] .


3. ANALYSIS


In order to constrain the excitation conditions quantitatively, we used the `molsim` program to model the
molecular spectra with non-LTE radiative transfer models and to explore the physical parameter space with
the Markov-Chain Monte Carlo (MCMC) approach (Lee
et al. 2023).


3.1. _Non-LTE_ _Radiative_ _Transfer_ _Modeling_


We implemented the `RADEX` non-LTE radiative transfer code (van der Tak et al. 2007) into `molsim` written
in Python. The module was accelerated with `Numba` to
provide the high performance required for MCMC analysis.



3


`RADEX` considers a gas clump consisting of a targeted
molecular species and its collision partners, such as H 2
and e [–] . The gas clump is embedded in a local background radiation field and has a certain geometry (e.g.,
slab, uniform sphere, expanding sphere). With this
physical picture, `RADEX` iteratively solves for the level
population by incorporating an equilibrium with inelastic collisions and the local radiation field. Lastly, it computes the peak optical depth, excitation temperature
and peak intensity of each line based on the level population and the line properties, assuming the local radiation
field as the only source of background continuum emission. The model can be described with physical parameters including kinetic temperatures ( _T_ k ), densities of
collision partners ( _n_ c ), background radiation field temperatures ( _T_ bg ), source velocity ( _V_ lsr ), line widths ( _dV_ ),
and molecular column densities ( _N_ col ).
In our implementation, we construct a modification
and extend it to support a continuum temperature
( _T_ cont ) different from the local radiation field temperature ( _T_ rad [1] ) and allow multiple components aligned perfectly along the line of sight (LOS). In the case of a
population inversion, _T_ cont serves as background radiation that stimulates the maser gain and is amplified by
the foreground gas clump. We assume the continuum
source and the gas components to be spatially distant
from each other such that the continuum radiation is

not included in the excitation analysis and the embedded radiation field of each component is only dominated
by the local radiation field. Detailed justifications for
this assumption will be discussed in Section 5.3. With
this assumption, the level population of each component is computed with a distinct excitation condition using `RADEX` . The frequency-dependent optical depth and
source function of the _i_ -th component are reconstructed
by summing over all lines as follows:


_τ_ _i_ ( _ν_ ) = � _τ_ _i,j_ [peak] _ϕ_ _i_ ( _ν_ ; _ν_ 0 _,j_ ) _,_ (1)

_j_



_,_ (2)
_τ_ _i_



_S_ _i_ ( _ν_ ) =



�



_j_ _[τ]_ [ peak] _i,j_ _ϕ_ _i_ ( _ν_ ; _ν_ 0 _,j_ ) _B_ _ν_ ( _T_ ex _,i,j_ )



_ϕ_ _i_ ( _ν_ ; _ν_ 0 ) = _G_ _ν_ ; _ν_ 0
�



1 _−_ _[V]_ [lsr] _[,][i]_
� _c_



_dV_ _i_
� _,_ ~~_√_~~ 8 ln 2



_,_ (3)
�



_G_ ( _x_ ; _µ, σ_ ) = exp _−_ [(] _[x][ −]_ _[µ]_ [)] [2]
� 2 _σ_ [2]



_._ (4)
�



Here, _τ_ _i,j_ [peak] and _T_ ex _,i,j_ are the optical depth and excitation temperature returned by `RADEX` for the _j_ -th line of


1 In `RADEX`, the local radiation temperature is denoted as _T_ bg .

4



**Table** **1.** Summary of VLA Observation Parameters


Subband Frequency Range Channel Spectral Resolution BWs Synthesized Beam _[∗]_ Targeted


(MHz) Number (kHz _|_ km s _[−]_ [1] ) (MHz) _′′_ _×_ _′′_ Species


5 5282.8 – 5298.8 1024 15.625 _|_ 0.885 16 3 _._ 351 _×_ 1 _._ 292 CH 2 NH
17 4439.8 – 4443.8 256 15.625 _|_ 1.05 4 3.983 _×_ 1.542 CH 2 NH


Note—

_∗_ The synthesized beam size obtained with `Natural` weighting.



the _i_ -th component, _B_ _ν_ is the Planck function, _ϕ_ _i_ is the
line profile for the _i_ -th component using the Gaussian
function _G_, and _τ_ _i_ and _S_ _i_ are the total optical depth
and source function with all lines being accounted for.
Using these definitions, for an _n_ -component model
where the continuum radiation is first processed by the
first component, then the second component and so on,
the final intensity with the continuum subtracted can be
expressed as


_I_ _ν_ = _B_ _ν_ ( _T_ cont ) _×_ ( _e_ _[−]_ [�] _i_ _[n]_ =1 _[τ]_ _[i]_ _−_ 1)



3.2. _MCMC_ _Fitting_


For line fitting, we used a Bayesian approach to compare models with different parameters and calculate
their probability distributions. This approach provides
an inference by conditioning the data on priors and sampling posterior distributions. In practice, we use the
Markov chain Monte Carlo (MCMC) approach to explore parameter space.
We use a logarithmic likelihood distribution with the
formula below:



(8)
�




[1] ( _x_ _i_ _−_ _µ_ _i_ ) [2]

2 _σ_ [2]



_σ_ _i_ [2]



_n_

+ � _S_ _i_ _×_ (1 _−_ _e_ _[−][τ]_ _[i]_ ) _× e_ _[−]_ [�] _j_ _[n]_ = _i_ +1 _[τ]_ _[j]_ _._ (5)


_i_ =1



_l_ = �


_i_



_−_ ln _σ_ _i_ _√_
� �



2 _π_ _−_ [1]
� 2



In the case of two components, the continuumsubtracted intensity is


_I_ _ν_ = _B_ _ν_ ( _T_ cont ) _×_ ( _e_ _[−][τ]_ [1] _[−][τ]_ [2] _−_ 1)


+ _S_ 1 _×_ (1 _−_ _e_ _[−][τ]_ [1] ) _× e_ _[−][τ]_ [2]


+ _S_ 2 _×_ (1 _−_ _e_ _[−][τ]_ [2] ) _._ (6)


It is worthwhile to note that the expressions reduce back
to that of `RADEX` in the case of one component when
the continuum temperature is equal to the local radiation temperature (i.e. _T_ _cont_ = _T_ _rad_ = _T_ _bg_ ). The calculations in `molsim` reproduces the results returned by
`RADEX` down to machine precision when the results are
converged.
In this work, we assume that the local radiation is
contributed by the cosmic microwave background only,
i.e., _T_ rad = 2 _._ 725 K (Mather et al. 1999) and a uniform
spherical geometry. We only consider H 2 as the collision partner, assuming a kinetic temperature-dependent
thermal ortho-to-para ratio (OPR), which can be approximated by:








9 _e_ _[−]_ [170] _[.]_ [6] [K] _[/T]_ [k] if _T_ k _≤_ 150 K _,_



3 if _T_ k _>_ 150 K _._



OPR( _T_ k ) =



_,_ (7)

3 if _T_ k _>_ 150 K _._



where _x_ is the observed spectral line intensity, _µ_ is the
model line intensity, and _σ_ is the uncertainty of the observations including an estimated 10% systematic uncertainty with the standard baseline deviation. The distribution applies to the case where the dataset has a
non-uniform uncertainty, in which case we compute the
uncertainties for each spectral chunk separately.
The resulting corner plots are shown in Appendix B.
A corner plot shows the probability distribution for each
pair of parameters and for each parameter individually.
In the following, the fitted results are represented by
50 _[th]_, 16 _[th]_, and 84 _[th]_ percentile as the representation
value and the range of uncertainty, also known as the
68% confidence interval. This choice is equivalent to
choosing the mean and + _/−_ 1 _σ_ for a normal distribution,
which is the case for most of our posterior distributions.
One of the advantages of the MCMC technique over a
traditional least-squares fit approach is that a larger parameter space can be explored more efficiently. Rather
than only returning the parameters that maximize the
likelihood function (e.g. least-squares fitting [2] ), it returns the actual probability of the parameters, which
can be used to assess whether parameters are highly co

2 When the posteriors deviate from a Gaussian distribution, the
parameters exhibiting the highest likelihood may not necessarily
correspond to the optimal parameters.



We left all the rest as free parameters and allowed them
to be fitted using the MCMC approach as described below.

5



T b (Kelvin)
0 500 1000 1500 2000 2500







17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



T b (Kelvin)
0 5 10 15 20 25


17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



**Figure** **1.** Continuum emission toward the Sgr B2(N) region obtained with the VLA at 6 _._ 8 cm and ALMA at 3 _._ 5 mm. The
cm-wave emission concentrations (K1 – K6, Corby et al. 2015) are indicated by green dashed lines and circle markers whereas
the molecular hot cores identified in millimeter (N1 – N3, Bonfand et al. 2017) are indicated by orange triangle markers. The +
symbols mark the location of Class II CH 3 OH masers in blue, the brightest maser spots are marked in rose for the H 2 O maser
(Walsh et al. 2014), in purple for the OH maser (Argon et al. 2000), and in firebrick for the NH 3 maser (Yan et al. 2022).


**Table** **2.** Investigated Maser Transitions

Molecule Rest Frequency Transition _E_ u _S_ _ij_ _µ_ [2] log 10 _A_ s _[−]_ _ul_ [1] _T_ B _,_ peak _∗_ _T_ ex _τ_
(MHz) (K) (D [2] ) (K) (K)


CH 3 OH 84521.172(12) 5 _−_ 1 _−_ 4 0 _E_ 40.4 12.332 -5.6979 389 _._ 2 _±_ 0 _._ 2 -5.8 _[†]_ -2.44 _[†]_

CH 2 NH 5288.962(3) 1 1 _,_ 0 _−_ 1 1 _,_ 1 _,_ _F_ = 0 _−_ 1 11.1 0.897 -8.8109 _≥_ 121 _._ 8 _±_ 8 _._ 6 -0.62 _[‡]_ -0.008 _[‡]_

5289.712(3) _F_ = 1 _−_ 0 0.897 -9.2881 -0.54 _[‡]_ -0.009 _[‡]_

5289.815(3) _F_ = 2 _−_ 2 3.365 -8.9357 -0.65 _[‡]_ -0.030 _[‡]_

5290.671(3) _F_ = 2 _−_ 1 1.121 -9.4125 -0.55 _[‡]_ -0.011 _[‡]_

5290.828(3) _F_ = 1 _−_ 2 1.122 -9.1908 -0.75 _[‡]_ -0.008 _[‡]_

5291.682(3) _F_ = 1 _−_ 1 0.673 -9.4124 -0.62 _[‡]_ -0.006 _[‡]_


**Notes.** [(] _[∗]_ [)] Peak brightness temperature measured at the brightest emission spot for each molecule. The brightest emission
spot for 84 GHz CH 3 OH Class I maser is located near the K4 core at a _V_ lsr of 58 km s _[−]_ [1] . The brightest emission spot for 5.29
GHz CH 2 NH maser is located in the K6 H II region at a _V_ lsr of 83 km s _[−]_ [1] . The measured _T_ B of CH 2 NH represents a lower limit
to the _T_ B _,_ peak because of the limited angular resolution of the VLA observations. [(] _[†]_ [)] Characteristics of the CH 3 OH foreground
masing clump toward MS1. [(] _[‡]_ [)] Characteristics of the CH 2 NH masing gas toward MS2.

6





25


20


15


10


5


0


10 [0]


10 1



|) ) ) ) ) ) ec(J ec(J ec(J ec(J ec(J ec(J 30" 15" -28°22'00" 30" 15" -28°22'00" 30" 15" -28°22'00" 30" 15" -28°22'00" 30" 15" -28°22'00" 30" 15" -28°22'00"|879km/s (a)<br>.|862km/s (b)<br>.|845km/s (c)<br>.|827km/s (d)<br>.|Col6|
|---|---|---|---|---|---|
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|81.0 km/s<br>(e)|79.3 km/s<br>(f)|77.5 km/s<br>(g)|75.8 km/s<br>(h)|75.8 km/s<br>(h)|
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|74.1 km/s<br>(i)|72.3 km/s<br>(j)|70.6 km/s<br>(k)|68.9 km/s<br>(l)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|74.1 km/s<br>(i)|72.3 km/s<br>(j)|70.6 km/s<br>(k)|68.9 km/s<br>(l)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|74.1 km/s<br>(i)|72.3 km/s<br>(j)|70.6 km/s<br>(k)|68.9 km/s<br>(l)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|74.1 km/s<br>(i)|72.3 km/s<br>(j)|70.6 km/s<br>(k)|68.9 km/s<br>(l)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|67.1 km/s<br>(m)|65.4 km/s<br>(n)|63.7 km/s<br>(o)|61.9 km/s<br>(p)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|67.1 km/s<br>(m)|65.4 km/s<br>(n)|63.7 km/s<br>(o)|61.9 km/s<br>(p)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|67.1 km/s<br>(m)|65.4 km/s<br>(n)|63.7 km/s<br>(o)|61.9 km/s<br>(p)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|67.1 km/s<br>(m)|65.4 km/s<br>(n)|63.7 km/s<br>(o)|61.9 km/s<br>(p)||
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|60.2 km/s<br>(q)|58.5 km/s<br>(r)|56.8 km/s<br>(s)|55.0 km/s<br>(t)|55.0 km/s<br>(t)|
|-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)<br>-28°22'00"<br>15"<br>30"<br>ec (J)|53.3 km/s<br>(u)|51.6 km/s<br>(v)|49.8 km/s<br>(w)|48.1 km/s<br>(x)|48.1 km/s<br>(x)|


17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



**Figure** **2.** Channel maps of the Class I CH 3 OH maser at 84 GHz overlaid on the continuum emission observed at 3 _._ 5 mm.
The contours levels are 4 _._ 0 mJy beam _[−]_ [1] (1 _σ_ ) _×_ (40, 65, 106, 173, 282, 459, 749, 1220). The peak value is 8 _._ 45 Jy beam _[−]_ [1] .

7









Clump













**Figure** **3.** Schematic showing two scenarios of the two-chain-clump model for the 84 GHz CH 3 OH maser, where relatively weak
continuum radiation passes through two velocity-coherent gas clumps along the LOS resulting in accumulated maser gains. In
the double-maser scenario, the continuum radiation is initially amplified by the background masing clump, followed by further
amplification by the foreground masing clump. In the single-maser scenario, however, the foreground masing clump amplifies
the non-inverted line emission from the background clump. The peak brightness temperature ( _T_ _b_ ) and the corresponding optical
depth ( _τ_ ) are annotated in each spectrum.

8


variant with one another. The correlation between parameters manifests itself as non-separable distributions
in the corner plots.


4. RESULTS


We investigate the maser activities of two transitions in this work. The detailed spectroscopic parameters for each maser transition along with the observational results of the corresponding emission features
are summarized in Table 2. For CH 3 OH, we examined the molecular spectra extracted toward two distinct
regions, maser spot 1 (MS1, _α_ J2000 = 17 [h] 47 [m] 19 [s] _._ 730,
_δ_ J2000 = _−_ 28 _[◦]_ 22 _[′]_ 04 _[′′]_ _._ 580) and maser spot 2 (MS2,
_α_ J2000 = 17 [h] 47 [m] 20 [s] _._ 393, _δ_ J2000 = _−_ 28 _[◦]_ 22 _[′]_ 12 _[′′]_ _._ 410). Toward both regions, we performed MCMC analyses with
a two-chained-component model, as presented in Section 4.1.1 for MS1 and 4.1.2 for MS2 respectively. For
CH 2 NH, as there is no detectable signal toward MS1, we
examined its spectrum extracted toward MS2 only and
performed the MCMC analysis with a one-component
model as presented in Section 4.2.
Empirically, a brightness temperature ( _T_ B ) of an emission line much greater than the source physical (kinetic)
temperature is considered as an indication of a maser
emission rather than a thermally-excited line (Voronkov
et al. 2006; Gargaud et al. 2011). As elaborated in the
following sections, our MCMC analyses suggest the _T_ _k_
for the masing clumps in Sgr B2(N) to be _∼_ 29 _−_ 37 K.
In contrast, as summarized in Table 2, the observed
_T_ B values of the molecular emission investigated in this
work ( _>_ 120 K) are significantly higher than the physical
temperatures. Furthermore, we also performed a spectral analysis assuming a single excitation temperature
to equal _T_ _k_ for comparison and found that the observed
spectral profiles deviate substantially from the thermal
model. Additional evidence for maser activities, including the non-Gaussian shape of line profiles, the compact
emitting regions, the negative opacity values, and the
metastable upper-energy levels, will be discussed more
in the following sections. All combine to support the
observed emission of CH 3 OH at 84 GHz toward both
MS1 and MS2 and CH 2 NH at 5.29 GHz toward MS2 to
consist of astronomical (weak) masers.
As a reference for the relative positions, Figure 1
shows the continuum emission from Sgr B2(N) observed
at 6 _._ 8 cm (Left) and 3 _._ 5 mm (Right). The free-free continuum emission concentrations at 6 _._ 8 cm include four

cores, K1 - K4, and the two bow-shaped H II regions, K5
and K6 (Corby et al. 2015, marked in green in Figure 1).
At 3 _._ 5 mm, three main hot cores, N1 - N3, were revealed by their molecular emission (Bonfand et al. 2017,
marked in orange in Figure 1).



4.1. _Class_ _I_ _CH_ _3_ _OH_ _Masers_


Class I CH 3 OH masers are prevalent in massive star
formation regions. In particular, the 44 GHz maser line
was observed toward Sgr B2 at 3 _[′′]_ resolution (Mehringer
& Menten 1997). In contrast, there is limited information about the 5 _−_ 1 _−_ 4 0 _E_ Class I CH 3 OH maser at
84 GHz, a member of the same _J_ +1 _−_ 1 _−J_ 0 _E_ -type transition family along with the 36 GHz line (Breen et al.
2019, and references therein). Interferometric observations of the 84 GHz line in the Milky Way are even rarer
(Voronkov et al. 2006), as recent work has focused on
extragalactic detections (Humire et al. 2022; McCarthy
et al. 2018).
Here, we present the first interferometric ALMA observations of the 84 GHz CH 3 OH masers in a Milky Way
object at a resolution of 1 _._ 5 _[′′]_, as well as the first detection of the 84 GHz maser toward Sgr B2. The spread
of 84 GHz maser spots is manifest in the channel images shown in Figure 2 with velocities ranging from 50
to 86 km s _[−]_ [1] . The brightest maser spot located _∼_ 3 _._ 6 _[′′]_

west of the K4 core with a _V_ lsr of 58 km s _[−]_ [1] (hereafter
referred to as MS1) has a peak _T_ B of 389 _._ 2 _±_ 0 _._ 2 K
(8 _._ 454 _±_ 0 _._ 004 Jy beam _[−]_ [1], Figure 2 ( _q_ )-( _t_ )). In addition
to the brightest spot MS1, another maser knot associated with the K6 H II region is also identified with a
_T_ B of 75 _._ 4 _±_ 0 _._ 4 K (1 _._ 636 _±_ 0 _._ 008 Jy beam _[−]_ [1] ) at a _V_ lsr
of 83 km s _[−]_ [1] (hereafter referred to as MS2), as shown in
Figure 2 ( _b_ )-( _e_ ).
The molecular data file for _E_ -type CH 3 OH was taken
from the Excitation of Molecules and Atoms for Astrophysics (EMAA) database [3], with spectroscopy from the
Cologne Database for Molecular Spectroscopy (CDMS)
catalog [4] (M¨uller et al. 2005) and collision rate coefficients reported by Rabli & Flower (2010) for the rotational excitation of CH 3 OH by para- and ortho-H 2
(hereafter p-H 2 and o-H 2 ). The calculations of Rabli &
Flower (2010) were performed for rotational transitions
within the three first torsional states of CH 3 OH, _ν_ =
0 _,_ 1 _,_ 2, with a CH 3 OH basis including rotational states
_j_ 1 _≤_ 15 for p-H 2 ( _j_ 2 = 0) and _j_ 1 _≤_ 9 for o-H 2 ( _j_ 2 = 1),
where _j_ 1 and _j_ 2 are the rotational quantum numbers.
The coupled-states approximation was used to generate rate coefficients at temperatures 10 _≤_ _T_ _k_ _≤_ 200 K.
Because torsionally inelastic transitions were not considered by Rabli & Flower (2010), the EMAA dataset
for _E_ -CH 3 OH includes rotational transitions within the
ground torsional state ( _ν_ = 0) only. The first excited
state ( _ν_ = 1) of _E_ -CH 3 OH opening at 204.2 cm _[−]_ [1],


3 https://emaa.osug.fr

4 https://www.astro.uni-koeln.de/cdms/catalog

9



_V_ _lsr_ (km _/_ s)

80 70 60 50


10



100 50 0



100 50 0


0 _._ 02


0 _._ 00


_−_ 0 _._ 02

108860 108880



0 _._ 04


0 _._ 02


0 _._ 00


_−_ 0 _._ 02


_−_ 0 _._ 04



100 50 0





8


6


4


2


0



84400 84420



84500 84505



0 _._ 02


0 _._ 00


_−_ 0 _._ 02


_−_ 0 _._ 04
85540 85560



Frequency (MHz)


**Figure** **4.** Observed spectra of the _E_ -type CH 3 OH transitions extracted toward MS1 are shown in black with noise levels
shaded in gray. Quantum numbers are given at the top right of each panel. The synthetic spectra are overlaid in colors for
different scenarios, with the green trace representing the double-maser scenario and the purple trace representing the singlemaser scenario. See Table 3.


**Table** **3.** Summary Statistics of the Marginalized Posterior toward MS1


Two-chain-clump Model _T_ _k_ _n_ _c∗_ _V_ lsr _†_ _dV_ _N_ _col_ _T_ _cont‡_

(K) (cm _[−]_ [3] ) (km s _[−]_ [1] ) (km s _[−]_ [1] ) (10 [16] cm _[−]_ [2] ) (K)


Single-maser Scenario _[§]_ 3 _._ 4 _−_ [+0] 0 _[.]_ _._ [1] 1
Background 29 _._ 2 [+5] _−_ 5 _[.]_ _._ [7] 6 1 _._ 4 [+0] _−_ 0 _[.]_ _._ [6] 4 _[×]_ [ 10] [3] 57 _._ 9 [+0] _−_ 0 _[.]_ _._ [1] 1 8 _._ 1 [+0] _−_ 0 _[.]_ _._ [2] 2 12 _._ 1 [+2] _−_ 1 _[.]_ _._ [6] 3
Foreground 31 _._ 9 [+5] _−_ 4 _[.]_ _._ [8] 4 5 _._ 3 [+2] _−_ 1 _[.]_ _._ [0] 6 _[×]_ [ 10] [4] 58 _._ 5 [+0] _−_ 0 _[.]_ _._ [1] 1 6 _._ 2 [+0] _−_ 0 _[.]_ _._ [2] 2 1 _._ 3 [+0] _−_ 0 _[.]_ _._ [2] 2
Double-maser Scenario _[§]_ 3 _._ 3 [+0] _−_ 0 _[.]_ _._ [2] 1
Background 29 _._ 3 [+11] _−_ 8 _._ 8 _[.]_ [2] 2 _._ 1 [+2] _−_ 0 _[.]_ _._ [1] 8 _[×]_ [ 10] [3] 59 _._ 4 [+0] _−_ 0 _[.]_ _._ [2] 3 5 _._ 8 [+0] _−_ 0 _[.]_ _._ [2] 2 8 _._ 1 [+1] _−_ 1 _[.]_ _._ [5] 3
Foreground 32 _._ 2 [+5] _−_ 4 _[.]_ _._ [9] 8 5 _._ 1 [+2] _−_ 2 _[.]_ _._ [5] 0 _[×]_ [ 10] [4] 57 _._ 3 [+0] _−_ 0 _[.]_ _._ [2] 2 8 _._ 0 [+0] _−_ 0 _[.]_ _._ [3] 3 1 _._ 5 [+0] _−_ 0 _[.]_ _._ [4] 2


**Notes.** The quoted uncertainties represent the 16 _[th]_ and 84 _[th]_ percentile (1 _σ_ for a Gaussian distribution) uncertainties. ( _∗_ ) _n_ _c_
represents the number density of the collision partners, which we take to be _n_ H 2 as hydrogen is assumed to be the dominant
partner. [(] _[†]_ [)] Two velocity components have similar _V_ lsr of _∼_ 58 km s _[−]_ [1] along the LOS. [(] _[‡]_ [)] Continuum temperature for 84-109
GHz band. [(] _[§]_ [)] The MCMC analysis revealed two distinct peaks in the posterior distributions, each representing one of the two
scenarios. Depending on the scenario, the background clump exhibits maser or non-inverted emission, while the foreground
clump always exhibits maser emission.



the highest level of _E_ -CH 3 OH included in the EMAA
dataset is the rotational state 9 _−_ 6 ( _j_ 1 = 9 _, K_ = _−_ 6)
with an energy of 203.9 cm _[−]_ [1] .


4.1.1. _Masers_ _with_ _Dark_ _Continuum_ _Background_ _–_ _MS1_


Four uncontaminated _E_ -type CH 3 OH transitions covered in the collision data were used to constrain the

physical parameters quantitatively using a non-LTE
model and MCMC fitting algorithm. The observed spectra extracted toward the brightest maser spot MS1 are
shown in Figure 4. We first attempted with a singleclump model but found that the observed spectra could
not be reproduced with physically realistic parameters
even after relaxing the constraints on _T_ cont and _T_ rad . In
order to match the bright maser emission at 84.5 GHz,
strong background radiation is needed to stimulate the
maser gain in the single-clump model but it will also in


troduce significant absorption features at both 85.5 and
108.9 GHz.
Moreover, as shown in Figure 2(r), there is no significant mm-wave continuum source at MS1. While this

spot also exhibits a strong CH 3 OH emission at 44 GHz
( _T_ B = 157 K, Mehringer & Menten 1997), it shows no
continuum emission at cm-wavelengths either. The closest continuum source, K4, is offset by _∼_ 3 _._ 6 _[′′]_ which corresponds to _∼_ 0.14 pc at the distance of Sgr B2 (8.2 kpc,
Reid et al. 2019). In addition, as shown in Appendix A,
there are no point sources associated with this maser
spot. The nearest bright infrared source observed with
both the Two Micron All Sky Survey (2MASS) and the
Galactic Legacy Infrared Midplane Survey Extraordinaire (GLIMPSE) program is located at _∼_ 5 _._ 2 _[′′]_ to the
west of the maser spot. Instead, the background radiation stimulating the maser gain may be weak and diffuse,

10


causing it to be resolved out by interferometers, such as
the free-free and dust emission in the Galactic plane.
As illustrated in Figure 3, the model we consider consists of two chained gas clumps overlapping in velocity
along the LOS, where the foreground clump exhibits
maser activity but the background clump can either
be also an inverted maser (i.e. the double-maser scenario) or non-inverted emitting (i.e. the single-maser
scenario). In both scenarios, this model can account for
the strong maser emission with an absence of a bright
and compact continuum source. It is analogous to the
“self-amplification” model of two masing clouds that has
been used to interpret water megamasers observed in circumnuclear disks in active galactic nuclei (Kartje et al.
1999).
A chained two-component model has been constructed
to iteratively generate synthetic spectra, each component being described with five parameters, _T_ _k_, _n_ _c_, _N_ _col_,
_dV_ and _V_ lsr . We assumed the two components have coherent but not identical values of _V_ lsr of _∼_ 58 km s _[−]_ [1]

although spatially separated along the LOS. As such,
two _V_ lsr parameters have the same prior probability distributions but are fit independently. Including both _V_ lsr
values, the priors for the free parameters and the MCMC
analysis are discussed in detail in Appendix B. Posterior
probability distributions for each parameter and their
covariances were generated with 100 walkers with 50000
samples each [5] .
As revealed in the bimodal posterior distributions, the
samples converge toward two distinct peaks, each corresponding to the double-maser and single-maser scenarios, respectively. The statistics of the resulting parameters for each scenario were summarized in Table 3,
which were used to construct the synthetic spectra for
the double-maser scenario shown with the green trace
and the single-maser scenario shown with the purple
trace in Figure 4. Both synthetic profiles well reproduce the observed spectra, capturing both the maser
and the optically thick emission features. Our model,
unfortunately, falls short in matching the low-frequency
side of the emission plateau at 108.87 GHz, corresponding to the 0 0 _−_ 1 _−_ 1 transition at a velocity range of
70 _−_ 90 km s _[−]_ [1] . This divergence from the observed spectrum implies the potential presence of another opticallythick velocity component(s) along the LOS. Because neither of the two scenarios completely reproduces the observed data, it is noteworthy that the uncertainties de

5 Each walker represents a Markov Chain consisting of multiple
samples with each sample being randomly sampled within the
parameter space.



20 40 60 80 100

T k, highvel


2 3 4 5 6

log 10 (n H 2, highvel )


81 82 83 84 85

V lsr, highvel


4 6 8 10

dV highvel


15.0 15.5 16.0 16.5 17.0

log 10 (N col, highvel )


6 7 8 9 10

T cont



20 40 60 80 100

T k, lowvel


2 3 4 5 6

log 10 (n H 2, lowvel )


61 62 63 64 65

V lsr, lowvel


10 12 14

dV lowvel


15.0 15.5 16.0 16.5 17.0

log 10 (N col, lowvel )



**Figure** **5.** Prior and posterior distributions for the MCMC
fit of CH 3 OH _E_ -type transitions toward MS2. The prior
distribution of each parameter is shown in gray. The posterior distributions for the low-velocity component are shown
in blue, whereas those for the high-velocity component are
shown in red. The posterior of _T_ _cont_ is shown in yellow. The
discrepancy of _T_ _cont_ in the posterior relative to the prior
could be be attributed to a certain portion of continuum
flux, especially from extended components, being resolved
out by ALMA.


rived from the MCMC results should be considered as a

lower limit of the uncertainties.

_V_ _lsr_ (km _/_ s)



100 80 60 40


1 _._ 5


1 _._ 0


0 _._ 5


0 _._ 0


84490 84500 84510



100 80 60 40


0 _._ 02


0 _._ 00


_−_ 0 _._ 02


_−_ 0 _._ 04


_−_ 0 _._ 06


85540 85550



0 _._ 05


0 _._ 00


_−_ 0 _._ 05


_−_ 0 _._ 10



11


100 80 60 40


108860 108870 108880



0 _._ 04


0 _._ 02


0 _._ 00


_−_ 0 _._ 02


_−_ 0 _._ 04



100 80 60 40



84390 84400 84410



Frequency (MHz)


**Figure** **6.** Observed spectra of the _E_ -type CH 3 OH transitions extracted toward MS2 are shown in black with noise levels
shaded in gray. Quantum numbers are given at the top right of each panel. The rest frequency for each transition are 84423.769,
84521.172, 85568.131, 108893.945 MHz from left to right. The synthetic spectra are overlaid in colors with the red trace
representing the high-velocity component (83 km s _[−]_ [1] ) and the blue trace representing the low-velocity component (64 km s _[−]_ [1] ).
See Table 4.


**Table** **4.** Summary Statistics of the Marginalized Posterior toward MS2


Molecule _T_ _k_ _n_ _c_ _V_ lsr _∗_ _dV_ _N_ _col_ _T_ _cont_
(K) (cm _[−]_ [3] ) (km s _[−]_ [1] ) (km s _[−]_ [1] ) (cm _[−]_ [2] ) (K)


CH 3 OH 7 _._ 7 [+0] _−_ 0 _[.]_ _._ [1] 1 _†_
30 _._ 7 [+2] _−_ 1 _[.]_ _._ [0] 5 8 _._ 3 [+1] _−_ 1 _[.]_ _._ [5] 6 _[×]_ [ 10] [4] 83 _._ 3 [+0] _−_ 0 _[.]_ _._ [1] 1 6 _._ 6 [+0] _−_ 0 _[.]_ _._ [1] 1 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [1] 1 _[×]_ [ 10] [16]

37 _._ 3 [+6] _−_ 5 _[.]_ _._ [4] 6 6 _._ 6 _−_ [+2] 1 _[.]_ _._ [1] 5 _[×]_ [ 10] [3] 63 _._ 6 [+0] _−_ 0 _[.]_ _._ [1] 2 11 _._ 4 [+0] _−_ 0 _[.]_ _._ [3] 3 1 _._ 2 [+0] _−_ 0 _[.]_ _._ [2] 2 _[×]_ [ 10] [16]

CH 2 NH 2687 _._ 6 [+62] _−_ 62 _[.]_ _._ [4] 4 _‡_

31 _._ 3 [+4] _−_ 4 _[.]_ _._ [3] 3 6 _._ 2 [+3] _−_ 2 _[.]_ _._ [7] 4 _[×]_ [ 10] [4] 83 _._ 5 [+0] _−_ 0 _[.]_ _._ [3] 3 7 _._ 7 [+0] _−_ 0 _[.]_ _._ [5] 5 4 _._ 8 [+1] _−_ 0 _[.]_ _._ [1] 6 _[×]_ [ 10] [14]


**Notes.** Similar to Table 3. ( _∗_ ) Two velocity components are identified along the LOS at a _V_ lsr of 83 km s _−_ 1 and 64 km s _−_ 1

respectively. [(] _[†]_ [)] Continuum temperature for 84-109 GHz band. [(] _[‡]_ [)] Continuum temperature at 5 GHz.



In the double-maser scenario, the _τ_ and _T_ _ex_ of
the 5 _−_ 1 _−_ 4 0 maser transition are found to be _−_ 2.44
and _−_ 5.8 K for the foreground clump and _−_ 0.02 and
_−_ 2027.3 K for the background clump. In the singlemaser scenario, the corresponding _τ_ and _T_ _ex_ values are
_−_ 2.52 and _−_ 6.5 K for the foreground clump and 0.13 and
245.2 K for the background clump. As an _T_ _ex_ of 245.2 K
is significantly higher than the _T_ _k_ value in this case, it is
evident that this transition exhibits strong non-inverted
emission and is on the verge of a population inversion.


4.1.2. _Masers_ _with_ _Bright_ _Continuum_ _Background_ _–_ _MS2_


In contrast to MS1, MS2 is aligned with the K6 H II
region along the LOS, which provides background radiation to be amplified by the stimulated emission (Figure 2d). The spectra extracted toward MS2 are shown
in Figure 6 with two individual velocity components being identified for each of the spectral features. We also
performed the spectral analysis for MS2 with a twocomponent model, where each component has a distinct
_V_ lsr .



The adopted prior and resultant posterior probability distributions for each parameter are depicted respectively in Figure 5. The priors for _V_ lsr were chosen to be Gaussian distributions centering on 83 km s _[−]_ [1]

and 63 km s _[−]_ [1] respectively, based on the difference between the observed sky frequency and the rest frequency.
Meanwhile, the _T_ _cont_ prior also has a Gaussian distribution, based on the measured continuum level of
6 _._ 67 _±_ 0 _._ 52 K. The remaining parameters all have uninformative uniformly distributed priors. Following 100
walkers with 10,000 samples each, all parameters converge to primarily Gaussian-like distributions in our
model. The corresponding corner plot of the posterior
distributions and the parameter covariances are shown
in Appendix B, with the largest covariance observed between H 2 densities and CH 3 OH column densities. This
covariance aligns with the fact that H 2 densities and
CH 3 OH column densities are related through the maser
emission measure, _ξ_ _∝_ _n_ _c_ _× N_ col, which, together with
temperature, determines the overall rate coefficient for
a collisionally-pumped maser transition (Leurini et al.
2016).

12


The posterior medians from the MCMC inference (Table 4) were used to construct the synthetic spectra
shown in Figure 6. If we take the noise level measured
in each passband into account, the synthetic spectral
profiles fit satisfactorily with the observed spectra for
both the maser and optically thick absorption features.
However, the low-velocity component (64 km s _[−]_ [1] ) of the
6 _−_ 2 _−_ 7 _−_ 1 transition fails to match the observed absorption feature at 85.55 GHz. This absorption feature
might be attributed to potential contamination from an
unidentified transition. The excitation temperature and
opacity of the 5 _−_ 1 _−_ 4 0 maser transition were found to be
negative, i.e., _−_ 5 _._ 6 K of _T_ _ex_ and _−_ 2 _._ 52 of _τ_ for the highvelocity component (83 km s _[−]_ [1] ), confirming its maser
activity toward MS2.


4.2. _CH_ _2_ _NH_ _Masers_


The maser activity of the 1 1 _,_ 0 _−_ 1 1 _,_ 1 CH 2 NH transitions at 5 _._ 29 GHz has been revealed toward both the

Galactic Center and external galaxies as point source
emission (Faure et al. 2018; Gorski et al. 2021). With
the VLA observations, we resolve this emission spatially
into three velocity components with a _V_ lsr of 64, 73,
and 83 km s _[−]_ [1] . The peak intensity map for each component is shown in Figure 7 respectively. The 83 km s _[−]_ [1]

and 64 km s _[−]_ [1] components are both associated with the
K6 H II region, while the 73-km s _[−]_ [1] component is concentrated toward the K5 H II region. The brightest
83-km s _[−]_ [1] component displays a more compact distribution than the other two components, with a _T_ B of
121 _._ 8 _±_ 8 _._ 6 K (12 _._ 1 _±_ 0 _._ 85 mJy beam _[−]_ [1] ). This measured
_T_ B represents a lower limit to the peak _T_ B since the
observed emission morphology of the 83-km s _[−]_ [1] component may result from point sources convolved with the
coarse VLA beam. Nevertheless, this component of the
CH 2 NH emission is coherent with that of the 84 GHz
CH 3 OH maser emission both in the velocity domain and
spatial position. Therefore, the significant brightness,
highly compact morphology, and coherence with other
maser emission suggest maser activity in the 83-km s _[−]_ [1]


component.
The molecular data file for CH 2 NH was taken from
the EMAA database. Extended from the calculations
in Faure et al. (2018), we calculated the collisional data
for rotational transitions of CH 2 NH among the first 49
rotational levels, i.e. up to the state 8 2 _,_ 6 at 99.5 cm _[−]_ [1],
and for kinetic temperatures in the range 10 – 150 K.
The detail calculations of the collisional rate coefficients
are presented in Appendix C.
We performed the MCMC analysis with a onecomponent model using the prior probability distributions depicted in Figure B4. The VLA observations



only cover two transitions of CH 2 NH while the other
transition at 4 _._ 44 GHz has no signal over the noise levels. As such, the data are insufficient to simultaneously
constrain the physical characteristics so the CH 2 NH
MCMC analysis requires a confined choice of priors on
some parameters. We opted to use _E_ -type CH 3 OH discussed in Section 4.1.2 for physical constraints, where
the 83 km s _[−]_ [1] components between CH 3 OH and CH 2 NH
are spatially coherent and are both associated with the
K6 H-II region. We therefore extracted the CH 2 NH
spectrum toward the same position of MS2. The posteriors on _T_ _k_ and _n_ H 2 obtained from CH 3 OH (Table 4;
Figure 5; Figure B3) are adopted as MCMC priors for
the CH 2 NH model. The priors for _V_ lsr and _dV_ are chosen
to be Gaussian distributions, informed by the strongest
emission feature (12 _σ_ ) detected in the data. The Gaussian prior for _T_ _cont_ is based on the continuum level of
2687 _±_ 58 K measured by the VLA. Meanwhile, the _N_ _col_
of CH 2 NH has a non-informative uniformly distributed
prior.
As shown in the posterior distributions in Figure B4,
following 10,000 samples with each of the 100 walkers,
the samplers converge at a _N_ _col_ of 4 _._ 76 [+1] _−_ 0 _[.]_ _._ [09] 64 _[×]_ [10] [14] [ cm] _[−]_ [2] [.]
The synthetic line profile is shown in Figure 8, reproducing six hyperfine components of the 1 1 _,_ 0 _−_ 1 1 _,_ 1 transition
within the noise level. The six hyperfine components
have _T_ _ex_ in the range of -0.75 – -0.55 K, _τ_ ’s in the range
of -0.03 – -0.006, and, in particular, the _F_ = 2 _−_ 2 transition has a _T_ _ex_ of -0.65 K and a _τ_ of -0.03.


5. DISCUSSION


5.1. _Metastable_ _Energy_ _Levels_ _of_ _Maser_ _Transitions_


The majority of the molecular lines observed toward
the H II regions in Sgr B2(N) are in absorption (Corby
et al. 2015, and reference therein). In contrast, specific
transitions of certain species toward these regions exhibit emission features (e.g. McGuire et al. 2012; Corby
et al. 2015; Remijan et al. 2022). These transitions
establish population inversions between energy levels
( _n_ _up_ _g_ _low_ _>_ _n_ _low_ _g_ _up_ ), a prerequisite for maser action to
occur. The mechanism of population inversion is conceptualized by spontaneous decay and collisions: spontaneous decay populates the levels determined by the
Einstein coefficients, meanwhile collisions redistribute
molecules due to their specific geometry and rotational
energy level patterns. Figures 9 and 10 show the energylevel structure of spontaneous transitions connected to
the two target maser transitions, with Einstein spontaneous emission coefficients ( _A_ _ij_ ) shown in colors.
In the case of the CH 3 OH 5 _−_ 1 _−_ 4 0 _E_ transition at
84 GHz, the upper-energy level 5 _−_ 1 _E_ is fed by the other
higher levels with strong landing transitions but spon

13



T cont (Kelvin)
0 1000 2000 3000


|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||









12


10


8


6


4



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)



**Figure** **7.** Peak intensity maps for each velocity component of the CH 2 NH maser at 5 _._ 29 GHz superimposed on the continuum
emission observed at 6 _._ 8 cm. The contour levels start at 4 _σ_ and continue up to the peak value with a step size of 2 _σ_ . The
values of _σ_ and peak values for the 83-, 73-, and 64-km s _[−]_ [1] components are 0.80, 0.93, 0.85 mJy beam _[−]_ [1], and 12.1, 8.86,
6.60 mJy beam _[−]_ [1], respectively.





10


5


0


_−_ 5



100


50


0


_−_ 50



5288 5290
Frequency (MHz)


**Figure** **8.** Observed spectrum of the CH 2 NH 1 1 _,_ 0 _−_ 1 1 _,_ 1
masing transition extracted toward MS2 is shown in black
with noise levels shaded in gray. The synthetic spectrum
with hyperfine splitting is overlaid in red for the 83-km s _[−]_ [1]

components. The _F_ = 1 _−_ 0 and _F_ = 2 _−_ 2 hyperfine components are blended. Each hyperfine component is denoted
by a vertical bar, with the red bars corresponding to a _V_ lsr
of 83 km s _[−]_ [1] and the blue bars corresponding to 64 km s _[−]_ [1] in
blue.


taneously decays to the lower-energy level 4 0 _E_ with a
weak escaping transition [6] . 5 _−_ 1 _E_ has a total escaping log 10 _A_ _ij_ _/_ s _[−]_ [1] of _−_ 4 _._ 2139 (equivalent to a lifetime of


6 An escaping transition refers to a transition in which the upperenergy level is the target energy level, while a landing transition
refers to a transition in which the lower-energy level is the target
energy level.



_∼_ 1 _._ 6 _×_ 10 [4] s), which is _∼_ 3.0 orders of magnitude lower
than its total landing _A_ _ij_ . As discussed in Lees (1973)
and Menten (1991), CH 3 OH spontaneously decays more
rapidly within the _K_ = _−_ 1 stack as compared with decaying out of the _K_ = _−_ 1 stack. Specifically, among the
two escaping transitions, 5 _−_ 1 _−_ 4 _−_ 1 _E_ is stronger than
5 _−_ 1 _−_ 4 0 _E_ (Figures 9). In fact, the _K_ = _−_ 1 levels are
the end-points for all spontaneous decay routes (Lees
1973). For example, the lower-energy level of this maser
transition (4 0 _E_ ) decays rapidly to the lower _K_ = _−_ 1
levels.

In addition to the spontaneous decay, collisions redistribute molecules over the vertical stacks of the _K_ = _−_ 1

levels because the ∆ _K_ = 0 collisions are preferred compared with _|_ ∆ _K|_ = 1 and 2 (Menten 1991). In particular, at a _T_ _k_ of 30 K, the total rate coefficient of
the ∆ _K_ = 0 collisions de-populating a _K_ = _−_ 1 level
( _∼_ 1 _×_ 10 _[−]_ [9] cm [3] s _[−]_ [1] ) is almost two orders of magnitudes higher than that of the _|_ ∆ _K|_ = 1 collisions
( _∼_ 5 _×_ 10 _[−]_ [11] cm [3] s _[−]_ [1] ) and the _|_ ∆ _K|_ = 2 collisions
( _∼_ 3 _×_ 10 _[−]_ [11] cm [3] s _[−]_ [1] ).
For CH 2 NH, we sum the hyperfine components of the
14 N splittings and use the sum of _A_ _ij_ as the representative _A_ _ij_ for each transition in Figure 10. In the case
of the CH 2 NH 1 1 _,_ 0 _−_ 1 1 _,_ 1 transition at 5.29 GHz, the
upper-energy level 1 1 _,_ 0 is coupled to the higher levels 2 1 _,_ 1
and 2 2 _,_ 1 with strong spontaneous transitions but to the
lower-energy level 1 1 _,_ 1 with a weak escaping transition.
Compared with the upper-energy level 1 1 _,_ 0, which has
a total escaping log 10 _A_ _ij_ _/_ s _[−]_ [1] of _−_ 4 _._ 2476, (equivalent to
a lifetime of _∼_ 1 _._ 8 _×_ 10 [4] s), the lower-energy level 1 1 _,_ 1

14















2.5


0.0


2.5


5.0

5.7


7.5


10.0


12.5





















14.8

4 3 2 1 0 1 2 3


K


**Figure** **9.** Energy level structure of the connected rotational transitions for the CH 3 OH 5 _−_ 1 _−_ 4 0 _E_ transition. Energy levels
are classified by the _K_ quantum number and ordered by increasing energy but are not drawn to scale. The log 10 s _A_ _[−]_ _i_ [1] _j_ [for] [each]

transition is shown with diverging color schemes, in which the critical middle value is set to be the log 10 s _A_ _[−]_ _i_ [1] _j_ [of] [the] [5] _[−]_ [1] _[ −]_ [4] [0] _[E]_
transition ( _−_ 5 _._ 7). The targeted transitions are shown with gray arrows. Transitions with a smaller _A_ _ij_ are shown as blue dotted
lines while transitions with a larger _A_ _ij_ are shown as red solid lines.



has a slightly stronger escaping log 10 _A_ _ij_ _/_ s _[−]_ [1] of _−_ 4 _._ 0303
(equivalent to a shorter lifetime of _∼_ 1 _._ 1 _×_ 10 [4] s).
Meanwhile, collisions of CH 2 NH exhibit a propensity for the _|_ ∆ _K_ _a_ _|_ = 0 transitions compared with the
inter-stack transitions _|_ ∆ _K_ _a_ _|_ = 1 and 2 (Faure et al.
2018). In particular, the total rate coefficient of the
∆ _K_ _a_ = 0 collisions de-populating a _K_ _a_ = 1 level
( _∼_ 10 _[−]_ [10] cm [3] s _[−]_ [1] ) is one order of magnitude higher than
that of the _|_ ∆ _K_ _a_ _|_ = 1 and 2 collisions at a _T_ _k_ of 30
K. However, the inter-stack transitions from the ground
state 0 0 _,_ 0 complicate this multi-level system. The collisions from 0 0 _,_ 0 more efficiently populate the lower level
1 1 _,_ 1 than the upper level 1 1 _,_ 0, suppressing the inversion.
Therefore, while these energy structures allow the temporary trapping of the population in the metastable 1 1 _,_ 0
level, it only results in a weak population inversion.


5.2. _Spatial_ _Origin_ _and_ _Pumping_ _Mechanism_


The maser activity of several simple species was reported previously toward Sgr B2(N) with precise locations, including CH 3 OH, H 2 O, OH, and NH 3, which are
indicated by + symbols in Figures 1 and 11. The Class II
CH 3 OH maser spot at 6 _._ 7 GHz is spatially associated





2.76


4.00


6.00


8.00


8.81


10.00


12.00







14.00


0 1 2

K a


**Figure** **10.** Energy level structure of the connected
rotational transitions for CH 2 NH 1 1 _,_ 0 _−_ 1 1 _,_ 1 transition at
5288 MHz (thick gray arrow). Similar to Figure 9, but the
critical middle value is set to be the log 10 s _A_ _[−]_ _i_ [1] _j_ [of the 1] [1] _[,]_ [0] _[−]_ [1] [1] _[,]_ [1]
transition ( _−_ 8 _._ 81).

15



with the N3 mm-wave core (Caswell 1996; Caswell et al.
2010). A survey performed with the Australia Telescope
Compact Array (ATCA) characterized 30 H 2 O maser
spots with the majority of them located within the N1K2-K3 region (Walsh et al. 2014). Six OH maser spots
have been identified with a VLA survey of OH masers
with the brightest spot being associated with the K3 cmwave core (Argon et al. 2000; Qiao et al. 2014). In a recent VLA observation, nine NH 3 (9,6) maser spots were
resolved in this region; most of these spots are concentrated in the N1-K2-K3 region, while the brightest spot
is located toward the N3 hot molecular core (Yan et al.
2022). In contrast, the maser emission of the organic
molecular species presented in this work is found to be

located close to the K4 cm-wave core and the K6 H II
region, being spatially offset from the spots of the radiative pumping maser species OH and Class II CH 3 OH.
The 84 GHz CH 3 OH maser displays a bright but extended distribution, centered around MS1 (near the K4
core), and subtending an angular size of _∼_ 15 _[′′]_ . The
emission tapers off rapidly from the center with nonGaussian profiles, a morphology possibly attributed to
maser beaming effects.
We found that MS2, superimposed on the K6 H II
region, harbors maser emission of both Class I CH 3 OH
at 84 GHz and CH 2 NH at 5 _._ 29 GHz (Figure 11). The
83-km s _[−]_ [1] component of the CH 2 NH maser at K6 remarkably resembles that of the Class I CH 3 OH maser.
Their consistent morphology serves as strong evidence
to support a similar collisional pumping mechanism for
the CH 2 NH maser with the Class I CH 3 OH maser as
well as a common physical condition for triggering these
masers. By understanding the conditions that are necessary for maser activities to occur, we can also better understand how they can be used to monitor astronomical
objects. For example, since these masers are pumped by
intense collisions, we can expect them to be good candidates for studying regions with time-dependent gas
dynamics, such as episodic outflows from massive protostars. Future surveys of these new masers in addition
to such objects are needed to determine how frequently
they accompany Class I CH 3 OH masers and how they
might fit into proposed evolutionary timelines of masers
in massive star formation (e.g., Ellingsen et al. 2012).
Alongside our observations of the Class I 84 GHz
CH 3 OH maser, we also examined the CH 3 OH 8 0 _−_ 7 1 _A_ type transition at 95 GHz, which exhibits maser activity toward several famous star-forming regions, e.g.,
Orion–KL (Plambeck & Wright 1988), DR 21 (Plambeck
& Menten 1990), and W51 (Pratap & Menten 1993). A
recent single-dish survey of ATLASGAL clumps shows
that the 84 GHz line is generally weaker than the 95 GHz



17 [h] 47 [m] 21 [s] 20 [s] 19 [s]


RA (J2000)


**Figure** **11.** The 83-km s _[−]_ [1] components of the 84 GHz
Class I CH 3 OH maser and 5.29 GHz CH 2 NH maser are
shown with contours in pink and orange respectively, and
superimposed on the free-free continuum emission at 6.8
cm. Yellow shading indicates the overlap region where the
CH 3 OH emission exceeds 40 _σ_ and the CH 2 NH emission exceed 4 _σ_ . The 84 GHz Class I CH 3 OH maser spots, MS1
and MS2, are marked with + symbols in megenta while the
brightest maser spots of OH, H 2 O, NH 3, and Class II CH 3 OH
masers are marked in other colors (Argon et al. 2000; Caswell
et al. 2010; Walsh et al. 2014; Yan et al. 2022). The K4 core
and arc-like K6 H II region are marked with a green circle
maker and dotted line respectively.


line (Yang et al. 2023). In contrast, we found that the 95
GHz line exhibits weaker emission toward the identified
maser spots in Sgr B2(N) compared to the 84 GHz line.
The spatial distribution for the 95 GHz emission is similar to that for other thermal molecular lines, concentrating toward the N1 mm-wave source. This distribution
may be attributed to either a weak maser or thermal
radiation at different emission spots. It is noteworthy
that Mehringer & Menten (1997) identified both maser
and quasi-thermal emission components toward Sgr B2
in the 44 GHz line, a consecutive transition ( _J_ = 6)
of the ( _J_ + 1) 0 _−_ _J_ 1 _A_ series with the 95 GHz transition ( _J_ = 7). A more detailed analysis of other _A_ -type
CH 3 OH transitions is needed to determine the nature of

the 95 GHz emission.


5.3. _Physical_ _Conditions_ _of_ _Masing_ _Clumps_


The high spatial resolutions of interferometric observations enable us to resolve and segregate compact
molecular emissions in diverse environments. In particular, the rich thermalized emission of CH 3 OH and
CH 2 NH occurs in the hot core regions. In the N1

16


hot core, the ALMA observations reported an _N_ _col_ of
2 _._ 0 _×_ 10 [19] cm _[−]_ [2] for CH 3 OH and 9 _._ 0 _×_ 10 [17] cm _[−]_ [2] for
CH 2 NH at a _T_ _ex_ of 230 K (Motiyenko et al. 2020; Margul`es et al. 2022). In contrast, the bright stimulated
maser emission of these two molecules concentrates in

the less dense masing clumps. The _N_ _col_ of these two
molecules in the masing clumps (Table 3-4) are 2 _−_ 3
orders of magnitudes less abundant than those in the
hot core.

From the MCMC analyses on the CH 3 OH 84 GHz
maser presented in Section 4.1, we found the _T_ _k_ for
the masing clumps to be _∼_ 29 _−_ 37 K. This range of
_T_ _k_ is consistent with the large-scale measurement of the
Sgr B2 envelope from the OCS lines (30-37 K, ArmijosAbenda˜no et al. 2020) as well as the dust temperature
of Sgr B2(N) obtained from _Herschel_ observations ( _∼_ 28
K, Etxaluze et al. 2013). It is also consistent with the
value of _T_ _k_ (30 K) derived from the non-LTE modeling of the weak masers of methyl formate detected in
PRIMOS (Faure et al. 2014).
We also constrain the _n_ H 2 of the masing clumps to be
(5 _−_ 8) _×_ 10 [4] cm _[−]_ [3], a level significantly lower than that
derived for the hot core regions. The _n_ H 2 of the Sgr
B2(N) hot cores are _>_ 10 [7] cm _[−]_ [3], with the N1 core reaching _∼_ (1 _−_ 2) _×_ 10 [9] cm _[−]_ [3] (S´anchez-Monge et al. 2017).
In contrast, the _n_ H 2 of the masing clumps is comparable to the _n_ H 2 of the colder envelope of Sgr B2, which is
estimated to be 10 [3] _−_ 10 [4] cm _[−]_ [3] based on the absorption
molecular lines (Huettemeister et al. 1995; Schmiedeke
et al. 2016). The slight enhancement in physical densities might be attributed to local energetic events occurring in the envelope necessary for a collisionally pumped

maser.

This work presents a quantitative constraint on the
physical conditions characterizing a masing clump of organic molecules. It serves as a reference for the physical conditions sufficient for exciting population inversion and collisionally-pumped masers. These conditions include a _T_ _k_ of _∼_ 30, _n_ H 2 _>_ 5 _×_ 10 [4] cm _[−]_ [3], and
moderate molecular _N_ col ( _>_ 10 [16] cm _[−]_ [2] for CH 3 OH and
_>_ 10 [14] cm _[−]_ [2] for CH 2 NH). The relatively low values
of temperatures and densities indicate that the masing
clumps are situated in the colder and low-density external envelope. The distance from Sgr B2(N) to the
edge of the external envelope is suggested to be approximately 19 pc (Schmiedeke et al. 2016). The continuum
emission from Sgr B2(N) has an angular size of _∼_ 10 _[′′]_,
or 0.4 pc at a distance of 8.34 kpc (Reid et al. 2014),
which subtends a solid angle of 3 _._ 5 _×_ 10 _[−]_ [4] sr to the
envelope. This aligns with our assumption mentioned
in Section 3.1, where background continuum emission
sources are far from masing clumps and, therefore, do



not significantly affect the local energy distribution of
the molecules. Maser activities can manifest themselves

in the presence of either a bright continuum background
radiation or multiple chained masing clumps in the direction of a diffuse and weak background.


5.4. _Caveat_ _on_ _Geometric_ _Effects_


Geometric effects related to the propagation of maser
radiation become increasingly significant as the optical depth becomes lower than -1. Although `RADEX` and
`MOLSIM` support various geometries through escape probability approximation, other effects such as maser beaming are not treated. Such effects are particularly important in the case of unresolved clumps. The models also
assume homogeneous physical conditions (i.e. one-zone
models), which is inappropriate for very negative optical depths. For precisely modeling maser lines with
strong amplification, a non-local treatment of radiation
and level population is required.
Although our current treatment does not provide a
precise solution, it is in principle appropriate for _| τ_ _|≪_ 1
(the case of CH 2 NH) and still offers a reasonable approximation to the first order as _| τ_ _|_ is of the order of unity
(the case of CH 3 OH). Incorporating corrections such as
non-local treatments and other geometric effects would
definitely improve the solution but it would also introduce significant computational costs. This becomes especially infeasible for MCMC calculations. The current
solution represents the best that is achievable with our
current resources, acknowledging that this approach is
subject to future expansions and refinements.


6. SUMMARY


We report interferometric observations of maser activity from organic molecules toward Sgr B2 using the
ALMA and VLA. Enabled by the ALMA observations,
we report the first detection of the Class I CH 3 OH maser
at 84 GHz toward Sgr B2. Multiple 84 GHz CH 3 OH
maser knots are discovered with the brightest spot MS1
located _∼_ 3 _[′′]_ west of the K4 free-free continuum emis
sion core. The peak brightness temperature of MS1
reaches 389 _._ 2 _±_ 0 _._ 2 K at a velocity of 58 km s _[−]_ [1] . In addition, another CH 3 OH maser spot MS2 coexists with
the K6 UC H II region at a velocity of 83 km s _[−]_ [1] . With
the VLA observations, we resolve the 5 _._ 29 GHz CH 2 NH
maser emission into three velocity components. These
three components display distinct fine-scale structures
associated with the K5 and K6 bow-shaped H II regions. The 83 km s _[−]_ [1] component is co-spatial with MS2
and its peak brightness temperature has a lower limit of

121 _._ 8 _±_ 8 _._ 6 K.
We present a tool for modeling and fitting maser
spectra with non-LTE calculations and a Bayesian ap

proach. By leveraging the theoretical calculations on
collisional rate coefficients and cross sections for both _E_ type CH 3 OH and CH 2 NH transitions, this fitting technique enables us to statistically constrain the physical
conditions of the masing regions. In particular, our
analysis suggests a two-chain-clump maser model for explaining the intense CH 3 OH maser activity observed toward a region with weak and diffuse background radiation. This model can reproduce both the maser and the
optically thick emission features of the CH 3 OH spectra
observed toward the brightest maser spot MS1.
Interferometric observations have not only enabled us
to characterize the spatial origin and extent of maser
emission but also helped to constrain the pumping mechanism through direct comparisons of their morphologies.
We found a definite association between the maser emission from complex molecules and the K6 UC H II region.
They are offset from the masing regions of the radiatively pumped maser species and the infrared sources. In
contrast, the spatial correlation between the activities of
the 84 GHz CH 3 OH Class I maser and 5.29 GHz CH 2 NH
maser suggest that the CH 2 NH maser is pumped by intense collisions, analogous to the Class I CH 3 OH maser.
By understanding the nature of the new maser species,
which are pumped by intense collisions, we can better understand how they may serve as good candidates
for studying and monitoring astronomical objects with
time-dependent gas dynamics.


7. DATA ACCESS & CODE


The code used to perform the analysis is part
of the `molsim` open-source package; an archival
version of the code can be accessed at Lee
et al. (2023). The spectroscopic and collisional



17


data for _E_ -CH 3 OH and CH 2 NH can be found
in the EMAA database (https://emaa.osug.fr and
https://dx.doi.org/10.17178/EMAA).


_Facilities:_ ALMA, VLA, GBT


_Software:_ `Molsim` (Lee et al. 2023), `Emcee` (ForemanMackey et al. 2013), `Numba` (Lam et al. 2015), `CASA`
(CASA Team et al. 2022),


ACKNOWLEDGMENTS


B. A. M. and C. X. gratefully acknowledge support
of National Science Foundation grant AST-2205126.
This work was completed in part while C.X. was a
Grote Reber Fellow. C.X. acknowledges support from
the National Science Foundation through the Grote
Reber Fellowship Program administered by Associated Universities, Inc./National Radio Astronomy Observatory and the Virginia Space Grant Consortium.
The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities,
Inc. ALMA is a partnership of ESO (representing its
member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and
NAOJ. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2011.0.00017.S. This research
has made use of spectroscopic and collisional data
from the EMAA database (https://emaa.osug.fr and
https://dx.doi.org/10.17178/EMAA). EMAA is supported by the Observatoire des Sciences de l’Univers de
Grenoble (OSUG).



REFERENCES



Argon, A. L., Reid, M. J., & Menten, K. M. 2000, ApJS,
129, 159, doi: [10.1086/313406](http://doi.org/10.1086/313406)

Armijos-Abenda˜no, J., Banda-Barrag´an, W. E.,

Mart´ın-Pintado, J., et al. 2020, MNRAS, 499, 4918,

doi: [10.1093/mnras/staa3119](http://doi.org/10.1093/mnras/staa3119)

Batrla, W., Matthews, H. E., Menten, K. M., & Walmsley,
C. M. 1987, Nature, 326, 49, doi: [10.1038/326049a0](http://doi.org/10.1038/326049a0)

Baudry, A., Forster, J. R., & Welch, W. J. 1974, A&A, 36,

217

Belloche, A., M¨uller, H. S. P., Garrod, R. T., & Menten,

K. M. 2016, A&A, 587, A91,

doi: [10.1051/0004-6361/201527268](http://doi.org/10.1051/0004-6361/201527268)

Bonfand, M., Belloche, A., Menten, K. M., Garrod, R. T.,

& M¨uller, H. S. P. 2017, A&A, 604, A60,

doi: [10.1051/0004-6361/201730648](http://doi.org/10.1051/0004-6361/201730648)



Breen, S. L., Contreras, Y., Dawson, J. R., et al. 2019,


MNRAS, 484, 5072, doi: [10.1093/mnras/stz192](http://doi.org/10.1093/mnras/stz192)


Breen, S. L., Ellingsen, S. P., Caswell, J. L., & Lewis, B. E.


2010, MNRAS, 401, 2219,


doi: [10.1111/j.1365-2966.2009.15831.x](http://doi.org/10.1111/j.1365-2966.2009.15831.x)


Breen, S. L., Ellingsen, S. P., Contreras, Y., et al. 2013,


MNRAS, 435, 524, doi: [10.1093/mnras/stt1315](http://doi.org/10.1093/mnras/stt1315)


CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP,


134, 114501, doi: [10.1088/1538-3873/ac9642](http://doi.org/10.1088/1538-3873/ac9642)


Caswell, J. L. 1996, MNRAS, 283, 606,


doi: [10.1093/mnras/283.2.606](http://doi.org/10.1093/mnras/283.2.606)


Caswell, J. L., Fuller, G. A., Green, J. A., et al. 2010,


MNRAS, 404, 1029,


doi: [10.1111/j.1365-2966.2010.16339.x](http://doi.org/10.1111/j.1365-2966.2010.16339.x)

18


Chen, X., Sobolev, A. M., Ren, Z.-Y., et al. 2020, Nature

Astronomy, 4, 1170, doi: [10.1038/s41550-020-1144-x](http://doi.org/10.1038/s41550-020-1144-x)


Corby, J. F., Jones, P. A., Cunningham, M. R., et al. 2015,

MNRAS, 452, 3969, doi: [10.1093/mnras/stv1494](http://doi.org/10.1093/mnras/stv1494)


Cragg, D. M., Sobolev, A. M., & Godfrey, P. D. 2002,

MNRAS, 331, 521, doi: [10.1046/j.1365-8711.2002.05226.x](http://doi.org/10.1046/j.1365-8711.2002.05226.x)


—. 2005, MNRAS, 360, 533,

doi: [10.1111/j.1365-2966.2005.09077.x](http://doi.org/10.1111/j.1365-2966.2005.09077.x)


Cyganowski, C. J., Brogan, C. L., Hunter, T. R., &

Churchwell, E. 2009, ApJ, 702, 1615,

doi: [10.1088/0004-637X/702/2/1615](http://doi.org/10.1088/0004-637X/702/2/1615)


Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al.

2012, ApJL, 760, L20, doi: [10.1088/2041-8205/760/2/L20](http://doi.org/10.1088/2041-8205/760/2/L20)


Elitzur, M., & Fuqua, J. B. 1989, ApJL, 347, L35,

doi: [10.1086/185601](http://doi.org/10.1086/185601)


Ellingsen, S. P. 2006, ApJ, 638, 241, doi: [10.1086/498673](http://doi.org/10.1086/498673)


Ellingsen, S. P., Breen, S. L., Voronkov, M. A., et al. 2012,

arXiv e-prints, arXiv:1210.2139,

doi: [10.48550/arXiv.1210.2139](http://doi.org/10.48550/arXiv.1210.2139)


Etxaluze, M., Goicoechea, J. R., Cernicharo, J., et al. 2013,

A&A, 556, A137, doi: [10.1051/0004-6361/201321258](http://doi.org/10.1051/0004-6361/201321258)


Faure, A., Lique, F., & Remijan, A. J. 2018, The Journal of

Physical Chemistry Letters, 9, 3199,

doi: [10.1021/acs.jpclett.8b01431](http://doi.org/10.1021/acs.jpclett.8b01431)


Faure, A., Remijan, A. J., Szalewicz, K., & Wiesenfeld, L.

2014, ApJ, 783, 72, doi: [10.1088/0004-637X/783/2/72](http://doi.org/10.1088/0004-637X/783/2/72)


Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman,

J. 2013, PASP, 125, 306, doi: [10.1086/670067](http://doi.org/10.1086/670067)


Forster, J. R., & Caswell, J. L. 1989, A&A, 213, 339


Fujisawa, K., Sugiyama, K., Motogi, K., et al. 2014, PASJ,

66, 31, doi: [10.1093/pasj/psu015](http://doi.org/10.1093/pasj/psu015)


Gargaud, M., Amils, R., Quintanilla, J. C., et al. 2011,

Encyclopedia of Astrobiology (Springer Berlin
Heidelberg), doi: [10.1007/978-3-642-11274-4](http://doi.org/10.1007/978-3-642-11274-4)


Gorski, M. D., Aalto, S., Mangum, J., et al. 2021, A&A,

654, A110, doi: [10.1051/0004-6361/202141633](http://doi.org/10.1051/0004-6361/202141633)


Hoffman, I. M., Goss, W. M., & Palmer, P. 2007, ApJ, 654,
971, doi: [10.1086/509717](http://doi.org/10.1086/509717)


Huettemeister, S., Wilson, T. L., Mauersberger, R., et al.

1995, A&A, 294, 667


Humire, P. K., Henkel, C., Hern´andez-G´omez, A., et al.

2022, A&A, 663, A33, doi: [10.1051/0004-6361/202243384](http://doi.org/10.1051/0004-6361/202243384)


Hunter, T. R., Brogan, C. L., Bartkiewicz, A., et al. 2018,

in Astronomical Society of the Pacific Conference Series,

Vol. 517, Science with a Next Generation Very Large

Array, ed. E. Murphy, 321


Hutson, J. M., & Green, S. 2012, MOLSCAT: MOLecular

SCATtering, Astrophysics Source Code Library.

[http://ascl.net/1206.004](http://ascl.net/1206.004)



Kartje, J. F., K¨onigl, A., & Elitzur, M. 1999, ApJ, 513,
180, doi: [10.1086/306824](http://doi.org/10.1086/306824)

Lam, S. K., Pitrou, A., & Seibert, S. 2015, in Proc. Second

Workshop on the LLVM Compiler Infrastructure in HPC,

1–6

Lee, K. L. K., Loomis, R. A., Xue, C., El-Abd, S., &

McGuire, B. A. 2023, molsim, Zenodo,

doi: [10.5281/ZENODO.8118192.](http://doi.org/10.5281/ZENODO.8118192)
[https://doi.org/10.5281/zenodo.8118192](https://doi.org/10.5281/zenodo.8118192)
Lees, R. M. 1973, ApJ, 184, 763, doi: [10.1086/152368](http://doi.org/10.1086/152368)

Leurini, S., Menten, K. M., & Walmsley, C. M. 2016, A&A,
592, A31, doi: [10.1051/0004-6361/201527974](http://doi.org/10.1051/0004-6361/201527974)

Margul`es, L., Remijan, A., Belloche, A., et al. 2022, A&A,
663, A132, doi: [10.1051/0004-6361/202243172](http://doi.org/10.1051/0004-6361/202243172)

Mather, J. C., Fixsen, D. J., Shafer, R. A., Mosier, C., &

Wilkinson, D. T. 1999, ApJ, 512, 511,

doi: [10.1086/306805](http://doi.org/10.1086/306805)

McCarthy, T. P., Ellingsen, S. P., Breen, S. L., Voronkov,

M. A., & Chen, X. 2018, ApJL, 867, L4,

doi: [10.3847/2041-8213/aae82c](http://doi.org/10.3847/2041-8213/aae82c)

McGrath, E. J., Goss, W. M., & De Pree, C. G. 2004,

ApJS, 155, 577, doi: [10.1086/424486](http://doi.org/10.1086/424486)

McGuire, B. A., Loomis, R. A., Charness, C. M., et al.

2012, ApJL, 758, L33, doi: [10.1088/2041-8205/758/2/L33](http://doi.org/10.1088/2041-8205/758/2/L33)

Mehringer, D. M., & Menten, K. M. 1997, ApJ, 474, 346,
doi: [10.1086/303454](http://doi.org/10.1086/303454)
Menten, K. M. 1991, in Astronomical Society of the Pacific

Conference Series, Vol. 16, Atoms, Ions and Molecules:

New Results in Spectral Line Astrophysics, ed. A. D.

Haschick & P. T. P. Ho, 119–136

Morita, K.-I., Hasegawa, T., Ukita, N., Okumura, S. K., &

Ishiguro, M. 1992, PASJ, 44, 373
Moscadelli, L., S´anchez-Monge, A., [´] Goddi, C., et al. 2016,
A&A, 585, A71, doi: [10.1051/0004-6361/201526238](http://doi.org/10.1051/0004-6361/201526238)

Motiyenko, R. A., Belloche, A., Garrod, R. T., et al. 2020,
A&A, 642, A29, doi: [10.1051/0004-6361/202038723](http://doi.org/10.1051/0004-6361/202038723)

M¨uller, H. S. P., Schl¨oder, F., Stutzki, J., & Winnewisser,

G. 2005, Journal of Molecular Structure, 742, 215,

doi: [10.1016/j.molstruc.2005.01.027](http://doi.org/10.1016/j.molstruc.2005.01.027)

Plambeck, R. L., & Menten, K. M. 1990, ApJ, 364, 555,

doi: [10.1086/169437](http://doi.org/10.1086/169437)

Plambeck, R. L., & Wright, M. C. H. 1988, ApJL, 330, L61,
doi: [10.1086/185205](http://doi.org/10.1086/185205)

Pratap, P., & Menten, K. 1993, Interferometric

observations of 95 GHz methanol masers., Vol. 412

(Springer Berlin Heidelberg), 211–214

Qiao, H., Li, J., Shen, Z., Chen, X., & Zheng, X. 2014,
MNRAS, 441, 3137, doi: [10.1093/mnras/stu776](http://doi.org/10.1093/mnras/stu776)

Qiao, H.-H., Walsh, A. J., Breen, S. L., et al. 2018, ApJS,

239, 15, doi: [10.3847/1538-4365/aae580](http://doi.org/10.3847/1538-4365/aae580)

Rabli, D., & Flower, D. R. 2010, MNRAS, 406, 95,

doi: [10.1111/j.1365-2966.2010.16671.x](http://doi.org/10.1111/j.1365-2966.2010.16671.x)

Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014,

ApJ, 783, 130, doi: [10.1088/0004-637X/783/2/130](http://doi.org/10.1088/0004-637X/783/2/130)
—. 2019, ApJ, 885, 131, doi: [10.3847/1538-4357/ab4a11](http://doi.org/10.3847/1538-4357/ab4a11)

Remijan, A., Xue, C., Margul`es, L., et al. 2022, A&A, 658,

A85, doi: [10.1051/0004-6361/202142504](http://doi.org/10.1051/0004-6361/202142504)
S´anchez-Monge, A., [´] Schilke, P., Schmiedeke, A., et al. 2017,

A&A, 604, A6, doi: [10.1051/0004-6361/201730426](http://doi.org/10.1051/0004-6361/201730426)

Sanna, A., Moscadelli, L., Cesaroni, R., et al. 2016, A&A,

596, L2, doi: [10.1051/0004-6361/201629544](http://doi.org/10.1051/0004-6361/201629544)

Schmiedeke, A., Schilke, P., M¨oller, T., et al. 2016, A&A,

588, A143, doi: [10.1051/0004-6361/201527311](http://doi.org/10.1051/0004-6361/201527311)

Sobolev, A. M., Cragg, D. M., & Godfrey, P. D. 1997,

A&A, 324, 211

Sobolev, A. M., & Deguchi, S. 1994, A&A, 291, 569

Song, S.-M., Chen, X., Shen, Z.-Q., et al. 2022, ApJS, 258,

19, doi: [10.3847/1538-4365/ac348e](http://doi.org/10.3847/1538-4365/ac348e)

Szymczak, M., Pillai, T., & Menten, K. M. 2005, A&A,

434, 613, doi: [10.1051/0004-6361:20042437](http://doi.org/10.1051/0004-6361:20042437)

Towner, A. P. M., Brogan, C. L., Hunter, T. R., et al. 2017,

ApJS, 230, 22, doi: [10.3847/1538-4365/aa73d8](http://doi.org/10.3847/1538-4365/aa73d8)



19


van der Tak, F. F. S., Black, J. H., Sch¨oier, F. L., Jansen,

D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627,

doi: [10.1051/0004-6361:20066820](http://doi.org/10.1051/0004-6361:20066820)

Voronkov, M. A., Brooks, K. J., Sobolev, A. M., et al. 2006,

MNRAS, 373, 411, doi: [10.1111/j.1365-2966.2006.11047.x](http://doi.org/10.1111/j.1365-2966.2006.11047.x)

Voronkov, M. A., Caswell, J. L., Ellingsen, S. P., Green,

J. A., & Breen, S. L. 2014, MNRAS, 439, 2584,

doi: [10.1093/mnras/stu116](http://doi.org/10.1093/mnras/stu116)

Walsh, A. J., Macdonald, G. H., Alvey, N. D. S., Burton,

M. G., & Lee, J. K. 2003, A&A, 410, 597,

doi: [10.1051/0004-6361:20031191](http://doi.org/10.1051/0004-6361:20031191)

Walsh, A. J., Purcell, C. R., Longmore, S. N., et al. 2014,
MNRAS, 442, 2240, doi: [10.1093/mnras/stu989](http://doi.org/10.1093/mnras/stu989)

Xu, Y., Li, J. J., Hachisuka, K., et al. 2008, A&A, 485, 729,

doi: [10.1051/0004-6361:200809472](http://doi.org/10.1051/0004-6361:200809472)

Xue, C., Remijan, A. J., Burkhardt, A. M., & Herbst, E.
2019, ApJ, 871, 112, doi: [10.3847/1538-4357/aaf738](http://doi.org/10.3847/1538-4357/aaf738)

Yan, Y. T., Henkel, C., Menten, K. M., et al. 2022, A&A,

666, L15, doi: [10.1051/0004-6361/202245024](http://doi.org/10.1051/0004-6361/202245024)

Yang, W., Gong, Y., Menten, K. M., et al. 2023, arXiv

e-prints, arXiv:2305.04264,

doi: [10.48550/arXiv.2305.04264](http://doi.org/10.48550/arXiv.2305.04264)

20


APPENDIX


A. INFRARED OBSERVATIONS ON POSSIBLE ASSOCIATED POINT SOURCES


We searched the point source catalog from both the 2MASS and the GLIMPSE program with the coordinate of MS1
( _α_ J2000 = 17 [h] 47 [m] 19 [s] _._ 73, _δ_ J2000 = _−_ 28 _[◦]_ 22 _[′]_ 04 _[′′]_ _._ 58). As shown in Figure A1, both 2MASS and GLIMPSE observations
show that the nearest infrared source is located at _α_ J2000 = 17 [h] 47 [m] 19 [s] _._ 34, _δ_ J2000 = _−_ 28 _[◦]_ 22 _[′]_ 05 _[′′]_ _._ 70, _∼_ 5 _._ 2 _[′′]_ west of
the maser spot. In addition, GLIMPSE detected another weak point source located toward _α_ J2000 = 17 [h] 47 [m] 19 [s] _._ 60,






|= −28◦22′06′′.82, In|, ∼2.8′′ southwest of the maser ntensity (MJy/sr)|
|---|---|
|100<br>In|150<br>200<br>250<br>tensity (MJy/sr)|
|||


|I<br>200|ntensity (MJy/sr)<br>300 400 500|
|---|---|
|||


|GLIMPSE IRAC4<br>K4|Col2|
|---|---|
|17h47m21s<br>20s<br>RA (J2000)|19s|


|2MASS<br>K4|Col2|
|---|---|
|17h47m21s<br>20s<br>RA (J2000)|19s|



**Figure** **A1.** Infrared sources towards Sgr B2(N) reported by the GLIMPSE IRC 4 Band at 8 _._ 0 _µm_ (Left) and the 2MSAA Ks
Band at 2 _._ 2 _µm_ (Right). The 84 GHz CH3OH maser emission at 58 _._ 5 km s _[−]_ [1] is shown with contours, as in Figure 2( _r_ ).


B. MCMC FITTING DETAILS


_E-type CH_ _3_ _OH_ — There are 11 free parameters in total to be adjusted in the MCMC analyses for _E_ -type CH 3 OH. For the
spectra extracted toward MS1, the adopted prior and resultant posterior probability distributions for each parameter
are depicted in Figure B1. The priors for _V_ lsr of both components are chosen to be a Gaussian distribution centered
at 58 _._ 3 km s _[−]_ [1] with a standard deviation of 2 km s _[−]_ [1] . Since the continuum is weak as evident by the observations, we
opted a uniform prior distribution in the range of 2.725 _−_ 15 K for _T_ cont . Meanwhile, all the remaining parameters
have uninformative uniformly distributed priors. We found that the convergence rate of the `RADEX` algorithm slows
down tremendously at high _N_ col _>_ 10 [17] cm _[−]_ [2] . Therefore, we capped _N_ col at 10 [17] _[.]_ [5] cm _[−]_ [2] and used 50,000 samples per
walker (five times the value used for MS2). At high _N_ col, we observed deviations between the results obtained from
our modified non-LTE algorithm and those from `RADEX` due to results not being converged in the latter.
A corner plot of the parameter covariances and their distribution for the MS1 MCMC fit is shown in Figure B2.
As shown in Figure B1, we found that the optimal set of parameters converge to two peaks, each corresponding to
one of the two scenarios (double-maser and single-maser). In particular, the peak at lower velocity of the foreground

20 40 60 80 100

T k, FG


20 40 60 80 100

T k, BG


5 10 15

T cont



2 3 4 5 6

log 10 (n H 2, FG )


2 3 4 5 6

log 10 (n H 2, BG )



50 55 60 65

V lsr, FG


50 55 60 65

V lsr, BG



4 6 8 10

dV FG


4 6 8 10

dV BG



21


15.5 16.0 16.5 17.0 17.5

log 10 (N col, FG )


15.5 16.0 16.5 17.0 17.5

log 10 (N col, BG )



**Figure** **B1.** Prior and posterior distributions for the MCMC fit of CH 3 OH _E_ -type transitions toward MS1. The prior
distribution of each parameter is shown in gray. The bimodal posterior distributions for the foreground component are shown
in blue, whereas those for the background component are shown in red. The posterior of _T_ _cont_ is shown in yellow.


component, corresponding to the higher velocity peak of the background component, corresponds to the double-maser
scenario, while the other peak corresponds to the single-maser scenario. To better visualize the posteriors, we isolated
the two peaks using _V_ lsr = 58 km s _[−]_ [1] as the criterion and plotted the posteriors separately in Figure B2. The corner
plots with green and purple backgrounds correspond to the double-maser and single-maser scenarios, respectively.
In each corner, the first five parameters belong to the foreground component, while the last five are those of the
background component. The 2D posterior distribution among parameters for the foreground component is shown
in blue, while that for the background component is shown in red. The cross terms between the two components
are shown in brown. The middle parameter is the background continuum temperature and the distribution between
continuum temperature and other parameters is shown in yellow.
A similar MCMC analysis to that for the spectra extracted toward MS1 was carried out for the spectra extracted
toward MS2. In contrast to Figure B1, the optimal set of parameters of MS2 converges to a single peak as shown in
Figure 5. The corresponding corner plot of the parameter covariances and their distribution for the MS2 MCMC fit
are shown in Figure B3. Similar to Figure B2, the parameters of the low-velocity component are shown in blue while
those of the high-velocity component are shown in red. We found that the MCMC analyses yield the consistent results,
regardless of whether the foreground or background velocity component is assigned as the high or low velocity along
the LOS. Furthermore, the brown circular distribution, the cross terms between the two components, reveals that
the two components are completely independent. This independence arises because the two components fit distinct
portions of the spectrum because of their disparate central velocities compared with the line widths. In contrast, the
strong degeneracy of the H 2 density and CH 3 OH column density is revealed for each individual velocity component.


_CH_ _2_ _NH_ — An MCMC analysis with a one-clump model was carried out for the CH 2 NH spectra. The prior and posterior
distributions are shown in Figure B4, while a corner plot of the parameter covariances for the CH 2 NH MCMC fit is
shown in Figure B5.


C. COLLISIONAL RATE COEFFICIENT CALCULATIONS FOR CH 2 NH


A first set of collisional data for CH 2 NH + p-H 2 ( _j_ 2 = 0) was published by Faure et al. (2018) for applications to
cold gas. The calculations of Faure et al. (2018) were performed for rotational transitions among the first 15 rotational
levels of CH 2 NH, i.e. up to the state 2 2 _,_ 0 ( _j_ 1 = 2 _, K_ _a_ = 2 _, K_ _c_ = 0) with an energy of 28.3 cm _[−]_ [1] . The full close-coupling
method was used to generate rate coefficients at temperatures 5 _≤_ _T_ _k_ _≤_ 30 K and hyperfine-resolved rate coefficients
were derived from the rotational rate coefficients using the statistical approximation, see Faure et al. (2018) for full
details.

22



log 10 (N col, FG )
16.0 16.2


16.00 16.25

log 10 (N col, FG )



log 10 (N col, BG )
17.00 17.25



dV FG
6.0 6.5


7.5 8.0 8.5


dV FG



T cont

3.25 3.50


3.0 3.5

T cont



T k, BG
20 40


25 50

T k, BG



log3.0 10 (n H 2, BG 3.5)


3 4

log 10 (n H 2, BG )



V lsr, BG

57.7558.00



59 60

V lsr, BG



dV BG
7.5 8.0 8.5



5.0


4.5


57.5


57.0


8.5


8.0


7.5


16.2


16.0


3.5


3.0


60


40


20


4.0


3.5


3.0


60.0


59.5


59.0


6.0


5.5


17.0


16.8



40


30


20


5.0


4.5


58.6


58.4


58.2


6.5


6.0


16.2


16.0


3.50


3.25


40


20


3.5


3.0


58.00


57.75


8.5


8.0


7.5



20 40

T k, FG



log4.5 10 (n H 2, 5.0 FG )


4.5 5.0

log 10 (n H 2, FG )



V lsr, FG

58.25 58.50


57.0 57.5

V lsr, FG



5.5 6.0

dV BG



**Figure** **B2.** Parameter covariances and marginalized posterior distributions for the MCMC fit of CH 3 OH _E_ -type transitions
toward MS1. The 16 _[th]_, 50 _[th]_, and 84 _[th]_ confidence intervals (corresponding to _±_ 1 sigma for a Gaussian posterior distribution)
are shown as vertical lines. The distribution among the parameters for the foreground component is shown in blue and that for
the background component is shown in red. The distribution among the parameters between the two components is shown in
brown. The distribution between the background continuum temperature and other parameters is shown in yellow. To better
visualize the bimodal posteriors, we isolated the two peaks and plotted separate posteriors for each, with the double-maser and
single-maser scenarios highlighted by green and purple backgrounds respectively, as per the color scheme in Figure 4.

4 _._ 00


3 _._ 75


3 _._ 50


64 _._ 0


63 _._ 5


12


11


16 _._ 2


16 _._ 0


7 _._ 8


7 _._ 6


35


30


25


5 _._ 0


4 _._ 8


83 _._ 4


83 _._ 2


6 _._ 8


6 _._ 6


6 _._ 4


16 _._ 1


16 _._ 0



2


0



2


0



4


2


0


25 30 35

T k _,_ highvel



0 _._ 2


0 _._ 1


0 _._ 0


4 _._ 75 5 _._ 00

log 10 (n H 2 _,_ highvel )



5


0


83 _._ 2 83 _._ 4

V lsr _,_ highvel



4


2


0



6 _._ 50 6 _._ 75

dV highvel



4


2


0



23


10


5


0



20 40

T k _,_ lowvel



0 _._ 050


0 _._ 025


0 _._ 000


3 _._ 5 4 _._ 0

log 10 (n H 2 _,_ lowvel )



63 _._ 5 64 _._ 0

V lsr _,_ lowvel



11 12

dV lowvel



1 _._ 0


0 _._ 5


0 _._ 0


16 _._ 0 16 _._ 2

log 10 (N col _,_ lowvel )



5 _._ 0


2 _._ 5


0 _._ 0


7 _._ 50 7 _._ 75

T cont



**Figure** **B3.** Similar to Figure B2, parameter covariances and marginalized posterior distributions for the MCMC fit of CH 3 OH
_E_ -type transitions toward MS2.


The distribution among the parameters for the low-velocity (64-km s _[−]_ [1] ) component are shown in blue and that for the
high-velocity (83-km s _[−]_ [1] ) component is shown in red. The distribution among the parameters between the two components are
shown in brown. The distribution between background continuum temperature and other parameters is shown in yellow.


In this work, we have extended the calculations of Faure et al. (2018) to higher levels and temperatures and we
have thus considered o-H 2 ( _j_ 2 = 1) as a second collider. Because close-coupling calculations are computationally very
demanding when the temperature increases, we had recourse to the coupled-states approximation. As in Faure et al.
(2018), all calculations were performed with the OpenMP extension [7] of the version 14 of the `MOLSCAT` code (Hutson &


7 http://ipag.osug.fr/ _∼_ faurea/molscat/index.html

24



50 100 150

T k (K)


4 6 8 10

dV (km s 1 )



4 5 6


log 10 (n H 2 (cm 3 ))


14 15 16


log 10 (N col (cm 2 ))



82 84 86

V lsr (km s 1 )


2600 2800 3000 3200

T cont (K)



**Figure** **B4.** Prior and posterior distributions for the MCMC fit of the CH 2 NH transitions toward MS2. The prior distribution
for each parameter is shown in grey, while the priors on _T_ _k_ and _n_ H 2 are from the MCMC posteriors of CH 3 OH in MS2 (Figure 5).
The posterior distributions for the physical characteristics are shown in red while the posterior for _T_ _cont_ is shown in yellow.


0.05


0.00

2


5.0


1


4.5


0



|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||||||||


14.50 14.75


log 10 (N col )



84


83


9


8


7


14.8


14.6


2800


2600



0.0050


0.0025


0.0000



5.0


2.5


0.0



20 40

T k



4.5 5.0

log 10 (n H 2 )



83 84

VLSR



1.0


0.5


0.0


7 8 9

dV



**Figure** **B5.** Parameter covariances and marginalized posterior distributions for the MCMC fit of the CH 2 NH transitions. The
16 _[th]_, 50 _[th]_, and 84 _[th]_ confidence intervals (corresponding to _±_ 1 sigma for a Gaussian posterior distribution) are shown as vertical
lines. The distribution among the parameters for the masing gas are shown in red and the distribution between background
continuum temperature and other parameters is shown in yellow.

25


Green 2012), using the same propagation parameters and rotational basis for CH 2 NH ( _j_ 1 _≤_ 12) and p-H 2 ( _j_ 2 = 0 _,_ 2).
The basis for o-H 2 was restricted to _j_ 2 = 1 and the `MOLSCAT` parameter `EMAX` (used to limit basis functions to CH 2 NH
plus H 2 energies less than `EMAX` ) was set to 1200 cm _[−]_ [1] for p-H 2 and 1318.64 cm _[−]_ [1] for o-H 2 . The coupled-states
calculations were performed for total energies between 2 and 800 cm _[−]_ [1] for p-H 2 and between 120 and 918 cm _[−]_ [1] for
o-H 2 . Rate coefficients were obtained for all rotational transitions among the first 49 levels, i.e. up to the state 8 2 _,_ 6 at
99.5 cm _[−]_ [1], and for kinetic temperatures in the range 10 – 150 K. Hyperfine-resolved rate coefficients were derived using
the statistical approximation, as in Faure et al. (2018). Finally, the collisional dataset was combined with the energy
levels and radiative rates taken from the CDMS catalog (M¨uller et al. 2005) in order to provide an EMAA-formatted
datafile.


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "Molecular data and collisional rate coefficients for E-type CH3OH",
  "failed_quote": "The molecular data file for E -type CH 3 OH was taken from the Excitation of Molecules and Atoms for Astrophysics (EMAA) database 3, with spectroscopy from the Cologne Database for Molecular Spectroscopy (CDMS) catalog 4 (Müller et al. 2005)"
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[1]",
  "value": "Extended collisional rate coefficient calculations for CH2NH + para-H2 and ortho-H2 up to level 8_2,6 (99.5 cm^-1) and Tk = 10-150 K using MOLSCAT",
  "failed_quote": "As in Faure et al. (2018), all calculations were performed with the OpenMP extension 7 of the version 14 of the MOLSCAT code (Hutson & Green 2012),"
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Propagation parameters, rotational basis, and statistical approximation for hyperfine-resolved collisional rate coefficients of CH2NH",
  "failed_quote": "As in Faure et al. (2018), all calculations were performed with the OpenMP extension 7 of the version 14 of the MOLSCAT code (Hutson & Green 2012), using the same propagation parameters and rotational basis for CH 2 NH ( j 1 ≤ 12) and p-H 2 ( j 2 = 0 , 2)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Fit the 5.29 GHz CH2NH 1_1,0 - 1_1,1 hyperfine spectrum toward MS2 with a one-component non-LTE model using MCMC, adopting CH3OH posterior distributions for Tk and nH2 as priors.",
  "failed_quote": "We performed the MCMC analysis with a one-component model using the prior probability distributions depicted in Figure B4."
 },
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Calculating collisional rate coefficients for CH2NH with para- and ortho-H2",
  "failed_quote": "As in Faure et al. (2018), all calculations were performed with the OpenMP extension 7 of the version 14 of the MOLSCAT code (Hutson & Green 2012),"
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "MCMC sampling with a multi-component modified RADEX code explores a larger parameter space more efficiently than least-squares fitting and yields full posterior probability distributions to assess parameter covariances.",
  "failed_quote": "One of the advantages of the MCMC technique over a traditional least-squares fit approach is that a larger parameter space can be explored more efficiently. Rather than only returning the parameters that maximize the likelihood function (e.g. least-squares fitting 2 ), it returns the actual probability of the parameters, which can be used to assess whether parameters are highly covariant with one another."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Single-clump non-LTE maser model for MS1: rejected because strong background continuum needed to stimulate the 84.5 GHz maser introduces unphysical absorption features at 85.5 and 108.9 GHz and no compact continuum source is observed toward MS1.",
  "failed_quote": "We first attempted with a single-clump model but found that the observed spectra could not be reproduced with physically realistic parameters even after relaxing the constraints on T cont and T rad . In order to match the bright maser emission at 84.5 GHz, strong background radiation is needed to stimulate the maser gain in the single-clump model but it will also introduce significant absorption features at both 85.5 and 108.9 GHz."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[1]",
  "value": "The two-chain-clump model for MS1 does not match the low-frequency side of the 108.87 GHz emission plateau (70-90 km s^-1), and the MS2 model does not match the 64 km s^-1 absorption feature at 85.55 GHz; thus MCMC uncertainties are lower limits.",
  "failed_quote": "Because neither of the two scenarios completely reproduces the observed data, it is noteworthy that the uncertainties derived from the MCMC results should be considered as a lower limit of the uncertainties."
 }
]
```
