# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A.234Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy_ _&_ _Astrophysics_ manuscript no. aa53996-25 ©ESO 2025
August 5, 2025

## **Noema formIng Cluster survEy (NICE):** **A census of star formation and cold gas properties in massive** **protoclusters at 1.5 < z < 4**


Luwenjia Zhou [1] _[,]_ [ 2], Tao Wang [1] _[,]_ [ 2] _[⋆]_, Emanuele Daddi [3], Rosemary Coogan [3], Hanwen Sun [1] _[,]_ [ 2], Ke Xu [1] _[,]_ [ 2],
Vinodiran Arumugam [4], Shuowen Jin [5] _[,]_ [ 6], Daizhong Liu [10], Shiying Lu [8] _[,]_ [ 9] _[,]_ [ 2], Nikolaj Sillassen [5] _[,]_ [ 6], Sicen Guo [3],
Guillaume Elias [3], Yijun Wang [1] _[,]_ [ 2], Yong Shi [1] _[,]_ [ 2], Zhi-Yu Zhang [1] _[,]_ [ 2], Qinghua Tan [10], Qiusheng Gu [1] _[,]_ [ 2], David
Elbaz [3], Aurelien Henry [3], Benjamin Magnelli [3], Carlos Gómez-Guijarro [3], Chiara d’Eugenio [12] _[,]_ [ 13], Georgios E.
Magdis [5] _[,]_ [ 6] _[,]_ [ 11], Francesco Valentino [14], Zhiyuan Ji [15], Raphael Gobat [18], Ivan Delvecchio [16], Mengyuan
Xiao [17], Veronica Strazzullo [19] _[,]_ [ 20], Alexis Finoguenov [21], Eva Schinnerer [7], R. Michael Rich [22], Jiasheng
Huang [23], Yu Dai [23], Yanmei Chen [1] _[,]_ [ 2], Fangyou Gao [1] _[,]_ [ 2], Tiancheng Yang [1] _[,]_ [ 2], and Qiaoyang Hao [1] _[,]_ [ 2]


_(Affiliations_ _can_ _be_ _found_ _after_ _the_ _references)_


Received –; accepted –


**ABSTRACT**


Massive protoclusters at _z_ _∼_ 1 _._ 5 _−_ 4, the peak of the cosmic star formation history, are key to understanding the formation
mechanisms of massive galaxies in today’s clusters. However, studies of protoclusters at these high redshifts remain limited,
primarily due to small sample sizes and heterogeneous selection criteria. For this work, we conducted a systematic investigation
of the star formation and cold gas properties of member galaxies of eight massive protoclusters in the COSMOS field, using
the statistical and homogeneously selected sample from the Noema formIng Cluster survEy (NICE). Our analysis reveals a steep
increase in the star formation rates per halo mass (Σ SFR _/M_ halo ) with redshifts in these intensively star-forming protoclusters,
reaching values one to two orders of magnitude higher than those observed in the field at _z_ - 2. We further show that instead of an
enhancement of starbursts, this increase is largely driven by the concentration of massive and gas-rich star-forming galaxies in the
protocluster cores. The member galaxies still generally follow the same star-forming main sequence as in the field, with a moderate
enhancement at the low-mass end. Notably, the most massive protocluster galaxies ( _M_ _⋆_ - 8 _×_ 10 [10] M _⊙_ ) exhibit higher _µ_ gas and
_τ_ gas than their field counterparts, while remaining on the star-forming main sequence. These gas-rich, massive, and star-forming
galaxies are predominantly concentrated in the protocluster cores and are likely progenitors of massive ellipticals in the center of
today’s clusters. These results suggest that the formation of massive galaxies in such environments is sustained by substantial gas
reservoirs, which in turn support persistent star formation and drive early mass assembly in forming cluster cores.


**Key** **words.** Galaxy: evolution – galaxies: high-redshift – submillimeter: galaxies – galaxies: clusters: general



**1.** **Introduction**


The environmental influence on the progenitors of massive
galaxies in local clusters is critical for understanding the formation of these galaxies (Peng et al. 2010; Behroozi et al.
2019; van der Burg et al. 2020) . Over the past decade,
extensive studies of massive protoclusters at the peak of
the cosmic star formation history ( _z_ _∼_ 2 _−_ 4), selected
through various methods, have been inconclusive in producing an unambiguous consistent picture of the environmental effects on star formation and cold gas properties
of galaxies in these structures (e.g., Rudnick et al. 2017;
Gómez-Guijarro et al. 2019; Jin et al. 2023, 2024; Bakx
et al. 2024; Pensabene et al. 2024). Specifically, some structures show a prevalence of submillimeter galaxies (SMGs)
or ultra-luminous infrared galaxies (LIRGs), suggesting enhanced star formation in their galaxies as compared to average field environments (e.g., Casey 2016; Wang et al. 2016;
Oteo et al. 2018). Other studies, primarily based on H _α_
emitters in protoclusters, report little to no difference in
the star-forming main sequence (SFMS) compared to their


_⋆_ E-mail: `taowang@nju.edu.cn`



field counterparts (e.g, Valentino et al. 2015; Shimakawa
et al. 2018; Pérez-Martínez et al. 2023). Molecular gas is the
fuel for star formation. The well-established star formation
law (Kennicutt 1998; Gao & Solomon 2004) highlights the
role of internal secular processes in the conversion of cold
gas into stars. Additionally, a bimodal scenario has been
proposed to describe the observed offset between starburst
galaxies and normal star-forming galaxies, where starburst
galaxies show higher star formation efficiency (SFE), which
may result from a higher merger rate or a more compact
distribution of molecular gas, among other factors (Daddi
et al. 2010; Sargent et al. 2014; Liu et al. 2019).
In dense environments, increased interactions can compress gas, thus enhancing SFEs, while cold gas inflows
through filaments connected to protoclusters can replenish
gas reservoirs, thus sustaining high gas fractions. Deep CO
observations of cluster galaxies _z ∼_ 1.6 reveal a consistent
or enhanced gas fraction compared to the field counterparts
(Rudnick et al. 2017; Noble et al. 2017). In the Spiderweb
protocluster at _z_ =2.15, Dannerbauer et al. (2017) identified a massive and extended CO(1-0) disk around the central radio galaxies. Follow-up analysis by Pérez-Martínez


Article number, page 1 of 12

_A&A_ _proofs:_ manuscript no. aa53996-25



et al. (2025) revealed a decreasing gas fraction with increasing stellar mass, showing a particularly steep decline above
log( _M_ _⋆_ /M _⊙_ ) = 10.5. In CL J1001, a starbusting protocluster at _z_ = 2.51, Wang et al. (2018) observed decreasing gas
fractions toward the cluster center, suggesting the imminent formation of a passive core by _z_ _∼_ 2. Tadaki et al.
(2019) found a declining gas fraction and gas depletion
time with increasing stellar mass in galaxies in three protoclusters traced by radio galaxies at _z_ _∼_ 2, and suggested
that gas accretion is accelerated in less massive galaxies
and suppressed in more massive ones. At even higher redshifts ( _z_ ≳ 4), extreme starbusting protocluster cores such
as SPT2349-56 and Distant Red Core (DRC) exhibit lower
gas fractions compared to field SMGs (Long et al. 2020;
Hill et al. 2022). Nevertheless, there is a paucity of protoclusters at high redshift with deep multi-wavelength coverage to comprehensively link the stellar and gas properties
of member galaxies. Such observations are essential for revealing the physical mechanisms driving the formation of
massive galaxies in these dense environments.
The Noema formIng Cluster survEy (NICE, Zhou et al.
2024) is a 159-hour NOEMA Large Program (ID: M21AA,
PIs: E. Daddi and T. Wang) targeting 48 massive protocluster candidates across multiple fields, complemented by
a 40-hour ALMA program (ID: 2021.1.00815.S) focusing on
25 southern candidates. The primary goal of these programs
is to spectroscopically confirm protoclusters at cosmic noon
through CO emission from their member galaxies, significantly expanding the sample size in this field of research.
Notably, eight protoclusters at 1.5 < _z_ < 4 have been confirmed in the COSMOS field (Sillassen et al. 2024). The
COSMOS field provides extensive ancillary data across optical, near-infrared (NIR), far-infrared (FIR), submillimeter, and radio wavelengths (Weaver et al. 2022; Jin et al.
2018; Smolčić et al. 2017), which, combined with the CO
observations from the NICE survey, offer a unique opportunity to investigate the environmental impact on galaxy
evolution.

For this paper we investigated the star formation activity and cold gas content of eight massive protoclusters
in the COSMOS field, identified through the NICE survey (hereafter NICE-COSMOS). Our analysis focuses on
the protoclusters’ central region (within one virial radius),
as detailed in the following sections. We adopt a standard
ΛCDM cosmology with _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1], Ω m = 0.3,
and Ω Λ = 0.7, and a Chabrier (2003) initial mass function.


**2.** **Data**


_2.1._ _NICE-COSMOS_ _protoclusters_


The eight protoclusters in NICE-COSMOS, along with
their member identification, are detailed in Sillassen et al.
(2024). Briefly, the members are selected with | _z_ phot _z_ spec _,_ group | < 0.1(1 + _z_ spec _,_ group ) within a virial projected radius based on the COSMOS2020 catalog (Weaver et al.
2022). The NICE survey selects intensively star-forming
massive protoclusters at 2 ≲ _z_ ≲ 4, which are chosen as overdensities of high- _z_ massive galaxies traced by red IRAC
sources in association with SPIRE-350 _µ_ m peakers that
show intense star formation. We list the selection criteria

here:


Article number, page 2 of 12



(1) Overdensity of red IRAC sources:


[3 _._ 6] _−_ [4 _._ 5] _>_ 0 _._ 1 ;
20 _<_ [4 _._ 5] _<_ 23 ;
Σ _N_ _>_ 5 _σ_ (N = 5 or 10) _._ (1)


[3.6], [4.5] are IRAC magnitudes from COSMOS2020
(Weaver et al. 2022), and Σ _N_ = _π dN_ [2] _N_ [is] [the] [Nth] [closest]
neighbor density estimator, where _d_ _N_ is the distance to the
Nth closest galaxy.
(2) SPIRE-350 _µ_ m peakers:


_S_ 500 _>_ 30 mJy ;
_S_ 350 _/S_ 250 _>_ 1 _._ 06 ;
_S_ 500 _/S_ 350 _>_ 0 _._ 72 _._ (2)


_S_ 250, _S_ 350, and _S_ 500 are the Herschel/ _SPIRE_ fluxes at
250 _µ_ m, 350 _µ_ m, and 500 _µ_ m.
Figure A.1 shows the spatial distribution of all members including CO and continuum detections in the eight
protoclusters in NICE-COSMOS, which are primarily concentrated at the cluster centers. For the following analysis,
we focus on galaxies within one virial radius, 1 _R_ vir, as defined in (Sillassen et al. 2024), as this area is also well covered by the NOEMA and ALMA observations. The virial
radii range from 141 pkpc to 429 pkpc, and the number of
member galaxies per structure varies between 13 and 31.
According to the selection method, the NICE protoclusters are traced by intensively star-forming massive galaxies,
which are likely to undergo a more active formation phase
driven by enhanced gas reservoirs, elevated merger rates, or
other physical processes, compared to protoclusters selected
through alternative methods.


_2.2._ _Stellar_ _masses_ _and_ _star_ _formation_ _rates_


We used stellar masses and star formation rates (SFRs) derived with `LePhare` (Arnouts et al. 2002) in COSMOS2020
(Weaver et al. 2022). For galaxies detected in the FIR,
specifically those in the super-deblended catalog (Jin et al.
2018), we also explored various SFR tracers to obtain accurate measurements.
We first cross-matched the members in the superdeblended catalog (Jin et al. 2018) with a separation smaller
than 1 _[′′]_ . The matches have a median separation of 0.15 _[′′]_ .
Notably, the 3GHz and 24 _µ_ m fluxes are measured directly
at the galaxy positions, hence the risk of misidentification
or flux misattribution is substantially reduced. For galaxies
detected at 3 GHz (Smolčić et al. 2017) with a signal-tonoise ratio (S/N) greater than 3, we calculated the SFR
from _L_ IR (Kennicutt 1998), as derived from the 3 GHz radio emission. This was done using the infrared radio correlation (IRRC, _q_ IR ( _z, M_ _⋆_ ), Delvecchio et al. 2021) and a spectral index of _α_ = -0.8. The high spatial resolution (0.75 _[′′]_ )
of the VLA 3 GHz observations helps mitigate blending issues in crowded regions, which can affect FIR flux measurements. For sources with S/N 3GHz < 3, we computed _L_ IR
from 24 _µ_ m fluxes using the conversion from Wuyts et al.
(2008). The results are listed in Table 1.
As we show in Fig. 1, _SFR_ radio and _SFR_ 24 _µ_ m are consistent. For galaxy 839791 in COSMOS-SBC6, which has
a radio luminosity twice that of the crossover luminosity
described in Wang et al. (2024), the threshold above which

Luwenjia Zhou et al.: NICE-COSMOS: Star Formation and Cold Gas Properties



Fig. 1: Comparison of SFRs derived from radio emission
with those derived using other methods. The comparison
includes SFRs estimated from Wuyts et al. (2008, green)
, deblended FIR fluxes from Jin et al. (2018, red), SFRs
derived with LePhare as in COSMOS2020 (Weaver et al.
2022, blue), and SFRs scaled from overall average SEDs of
the protoclusters to dust continuum (black). Only galaxies
with S/N 3GHz - 3 are shown. The black solid line represents
a 1:1 relation, while the shaded region indicates the 0.2 dex
uncertainties. The dashed colored lines show the median
ratios between _SFR_ radio and the SFRs derived from the
fours different methods, respectively: 0.90, 1.81, 0.37, 1.57.


radio emission is dominated by AGN, we used _SFR_ 24 _µ_ m to
minimize the contamination from AGN-related radio emis
sion.

In addition, we calculated SFRs by scaling the total
_L_ IR derived from the best-fit SED of the integrated FIR
photometry of each protocluster (Sillassen et al. 2024) to
the dust continuum emission of individual members, assuming the same dust temperature for all members. We
find that the scaled SFR is generally 1.6 times higher
than _SFR_ radio ; this is more prominent for those galaxies
with _SFR_ radio _∼_ 100M _⊙_ yr _[−]_ [1], while galaxies with higher
_SFR_ radio have similarly scaled SFRs.
Overall, we conclude that using _SFR_ radio does not
change the conclusion of this paper.


_2.3._ _Gas_ _masses_


The molecular gas mass is converted from the RayleighJeans dust continuum at 850 _µ_ m, _M_ gas [RJ] [,] [as] [calibrated] [with]
the prescription in Hughes et al. (2017). This method leverages dust continuum emission, which is intrinsically associated with gas in the entire cold molecular gas reservoir
(Genzel et al. 2015; Scoville et al. 2016), and offers a much
more sensitive measure than high- _J_ CO emission, which
primarily traces the dense gas phase only (Liu et al. 2015;
Daddi et al. 2015; Valentino et al. 2020a) and has limited
detections due to the narrow line width compared to continuum observations. The dust continuum at 3 mm and



Fig. 2: Comparison of the gas mass derived from CO emission lines and dust continuum. The black line denotes the

one-to-one relation and the dotted lines show the 0.3 dex
uncertainties. The NICE sample are circles, and the median ratio of -0.18 dex is indicated by the dashed line.


2 mm from the NOEMA and ALMA observations of the
NICE survey, closely corresponding to rest-frame 850 _µ_ m
for the cluster galaxies, was used to derive gas masses. The
NOEMA and ALMA observations have average angular resolutions of 4.1 _[′′]_ and 0.7 _[′′]_, respectively. For spatially resolved
sources, we used a Gaussian model to fit the visibilities. Unresolved sources were modeled as point sources.


We also estimated the gas masses from CO(3-2) or
CO(4-3) line emission, _M_ gas [CO] [,] [by] [converting] [them] [to] [the]
ground-state CO(1-0) luminosity, assuming the CO spectral
line energy distribution (CO-SLED) of star-forming galaxies at _z_ = 2.0 - 2.7 from the ASPECS survey (Boogaard et al.
2020). These galaxies exhibit slightly higher CO excitation
compared to main sequence galaxies at _z_ < 2 (Valentino
et al. 2020b), but overall agree, within the uncertainties,
with the average SLEDs of SMGs at _z_ = 1.2 – 4.8 (Birkin
et al. 2021). The conversion factor _α_ CO was derived using
the mass–SFR–metallicity relation from Genzel et al. (2015)
and the metallicity dependence of _α_ CO from Tacconi et al.
(2018) for our sample.


In Fig. 2 we compare the gas masses estimated using
the two methods. The two methods yield consistent results
within 0.3 dex, with _M_ gas [RJ] [approximately] [1.5] [times] [higher]
than _M_ gas [CO] [.] [A] [similar] [comparison] [of] [CO(1–0)] [and] [1.2 mm]
dust continuum measurements in galaxies within the Spiderweb protocluster also shows comparable results, albeit
with large scatters (Zhang et al. 2024). Table 1 lists the
_α_ CO values and gas masses calculated with different tracers. For consistency, in the following we adopt gas masses
estimated from the dust continuum.


Article number, page 3 of 12

_A&A_ _proofs:_ manuscript no. aa53996-25


Table 1: Properties of the CO or continuum-detected galaxies in the massive protoclusters of NICE-COSMOS.


Structure ID _r/R_ vir _z_ spec log 10 _M_ _⋆_ SFR _α_ CO log 10 _M_ gas [RJ] log 10 _M_ gas [CO] _SFR_ radio _SFR_ 24 _µ_ m


[M _⊙_ ] [M _⊙_ yr _[−]_ [1] ] [ M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] ] [M _⊙_ ] [M _⊙_ ] [M _⊙_ yr _[−]_ [1] ] [M _⊙_ yr _[−]_ [1] ]


(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11)


HPC1001 ... _[∗]_ 0.07 3.613 11.2 [+0] _−_ 0 _[.]_ _._ [2] 2 662 [+65] _−_ 66 3.59 11.48 _±_ 0.07 11.30 _±_ 0.04 125 _±_ 41 978 _±_ 883

HPC1001 1272853 1.12 3.604 11.3 [+0] _−_ 0 _[.]_ _._ [1] 2 496 [+290] _−_ 241 3.62 ... 10.87 _±_ 0.10 ... ...

HPC1001 1274387 0.78 3.61 10.3 [+0] _−_ 0 _[.]_ _._ [1] 1 68 [+69] _−_ 20 4.59 11.26 _±_ 0.18 10.84 _±_ 0.10 <159 ...

COS-SBC3 1340799 0.30 2.365 11.5 [+0] _−_ 0 _[.]_ _._ [1] 1 190 [+90] _−_ 61 3.52 11.41 _±_ 0.12 10.84 _±_ 0.07 <138 231 _±_ 13

COS-SBC4 840072 0.04 1.65 11.4 [+0] _−_ 0 _[.]_ _._ [1] 1 100 [+18] _−_ 18 3.54 11.21 _±_ 0.12 ... 165 _±_ 12 252 _±_ 20

COS-SBC6 835289 0.07 2.323 11.1 [+0] _−_ 0 _[.]_ _._ [1] 1 73 [+15] _−_ 19 3.62 10.95 _±_ 0.16 10.99 _±_ 0.05 101 _±_ 20 289 _±_ 17

COS-SBC6 839791 _[∗∗]_ 0.10 2.324 11.0 [+0] _−_ 0 _[.]_ _._ [0] 1 93 [+6] _−_ 6 4.01 11.51 _±_ 0.04 11.03 _±_ 0.05 1143 _±_ 60 195 _±_ 25

COS-SBCX1 1408110 0.29 2.422 11.4 [+0] _−_ 0 _[.]_ _._ [1] 1 156 [+30] _−_ 31 3.54 11.07 _±_ 0.15 11.03 _±_ 0.05 134 _±_ 16 183 _±_ 33

COS-SBCX3 1088927 0.04 3.032 10.5 [+0] _−_ 0 _[.]_ _._ [1] 2 100 [+45] _−_ 90 4.78 11.28 _±_ 0.15 11.09 _±_ 0.05 495 _±_ 56 472 _±_ 76

COS-SBCX3 1088787 0.11 3.03 10.7 [+0] _−_ 0 _[.]_ _._ [1] 1 53 [+40] _−_ 12 4.31 11.17 _±_ 0.19 11.25 _±_ 0.04 490 _±_ 57 284 _±_ 114

COS-SBCX4 1049510 0.07 2.642 11.1 [+0] _−_ 0 _[.]_ _._ [1] 1 257 [+83] _−_ 186 3.62 10.94 _±_ 0.22 10.78 _±_ 0.07 <123 137 _±_ 31

COS-SBCX4 1050531 0.05 2.647 11.2 [+0] _−_ 0 _[.]_ _._ [1] 1 416 [+135] _−_ 265 3.69 11.66 _±_ 0.04 11.43 _±_ 0.02 533 _±_ 37 496 _±_ 51

COS-SBCX4 1049929 0.14 2.648 10.9 [+0] _−_ 0 _[.]_ _._ [2] 2 195 [+120] _−_ 101 3.78 10.80 _±_ 0.31 10.67 _±_ 0.07 <141 ...

COS-SBCX7 392639 0.75 2.413 10.3 [+0] _−_ 0 _[.]_ _._ [1] 1 114 [+25] _−_ 112 4.66 ... 11.00 _±_ 0.12 <84 36 _±_ 17

COS-SBCX7 394944 0.14 2.416 11.1 [+0] _−_ 0 _[.]_ _._ [1] 1 92 [+70] _−_ 25 3.60 11.22 _±_ 0.12 10.89 _±_ 0.06 <87 184 _±_ 16

COS-SBCX7 394609 0.01 2.416 10.8 [+0] _−_ 0 _[.]_ _._ [1] 1 14 [+11] _−_ 4 3.93 11.24 _±_ 0.11 11.03 _±_ 0.05 186 _±_ 24 239 _±_ 17

COS-SBCX7 392257 0.15 2.415 10.7 [+0] _−_ 0 _[.]_ _._ [1] 1 91 [+61] _−_ 49 4.10 10.81 _±_ 0.34 10.86 _±_ 0.07 212 _±_ 25 122 _±_ 17


**Notes.** _Columns_ : (1)–(6) protocluster ID, galaxy ID in COSMOS2020 (Weaver et al. 2022), distance to protocluster center,
redshift, stellar mass, and SFR as given in Sillassen et al. (2024). (7) CO-to-H 2 conversion factor. (8) & (9) Molecular gas masses
from dust continuum and from CO. (10) SFR from 3GHz observations, with 3 _σ_ upper limits for nondetections. (11) SFR from
24 _µ_ m fluxes adopting conversion factors from Wuyts et al. (2008). For details, see Section 2. _[∗]_ : This source could be a blend of
several galaxies (Sillassen et al. 2022). _[∗∗]_ : Radio-loud galaxy.



**3.** **Star** **formation** **and** **cold** **gas** **properties**


_3.1._ _Enhanced_ _Star_ _Formation_ _in_ _Massive_ _Halos_ _in_ _the_ _Early_
_Universe_


The value of Σ SFR _/M_ halo in clusters increases with redshift, following an empirical relation of (1+ _z_ ) _[n]_ (see Alberts
& Noble 2022 for a review). The NICE survey extends such
studies to _z_ >2. We adopted the integrated SFR and best
estimates of halo masses of the eight protoclusters from
(Sillassen et al. 2024) to obtain the total SFR per unit halo
mass (Σ SFR _/M_ halo ). The SFR is from the FIR spectral energy distribution (SED) fitting using the dust templates
in Magdis et al. (2012), and the halo masses are the average results from six methods including stellar mass-to-halo
mass relations, overdensity with galaxy bias, and NFW profile fitting to radial stellar mass density. In Fig. 3 we include the eight massive protoclusters in NICE-COSMOS;
LH-SBC3 at _z_ = 3.95, which is the most distant protocluster identified in the NICE survey (Zhou et al. 2024);
protoclusters RO1001 at _z_ = 2.91 (Kalita et al. 2021) and
CL J1001 at _z_ = 2.51 (Wang et al. 2018), which are prototypes within the NICE survey; and SPT2349-56 at _z_ = 4.3
(Hill et al. 2022) and Distant Red Core at _z_ = 4.0 (Long
et al. 2020), which are starbursting protoclusters similar to
the NICE clusters. We found that Σ SFR _/M_ halo increases by
an order of magnitude from _z_ = 2 to _z_ = 4, following the
evolutionary trend observed in galaxy clusters up to _z_ = 1


Article number, page 4 of 12



(Σ SFR _/M_ halo _∝_ (1+ _z_ ) [5] _[.]_ [4], Webb et al. 2013), which has recently been shown to extend to clusters at _z_ = 1.6–2 ( **?** ).
These values are one to two orders of magnitude higher
than those observed in the field ( _∝_ (1+ _z_ ) [3] _[−]_ [4] Sargent et al.
2012; Ilbert et al. 2013, 2015). This may be due to the
evolution of the SFMS, modulated by the evolution of the
_M_ _⋆,_ tot _/M_ halo relation, and the reduction of the quenched
fraction (Elias et al. in prep.).


_3.2._ _Star-forming_ _main_ _sequence_ _in_ _dense_ _environments_


The SFR and stellar mass of all _UVJ_ -active cluster members (Williams et al. 2009) are shown in Fig. 4. Galaxies at different redshifts are scaled to _z_ = 2.5, following the
SFMS normalization and redshift evolution from Schreiber
et al. (2015). Despite significant scatter, the median values
of these galaxies closely follow the main sequence in the
field, in line with the results from H _α_ emitters in protoclusters at _z_ _∼_ 2.5 (e.g., Spiderweb, Pérez-Martínez et al.
2023).

The CO-detected members, which are among the most
massive with the highest SFRs, may indicate a greater
abundance of gas fueling star formation in these galaxies. However, this trend is not observed in the CO-detected
H _α_ emitters in the Spiderweb protocluster (Pérez-Martínez
et al. 2025), where SFRs are derived from the dust-corrected
H _α_ fluxes, possibly due to the differences in protocluster se

Luwenjia Zhou et al.: NICE-COSMOS: Star Formation and Cold Gas Properties



Fig. 3: Total SFR per unit halo mass as a function of redshift. Shown as red circles are the eight massive protoclusters in the COSMOS field and LH-SBC3 at _z_ = 3.95,
the most distant protocluster identified in the NICE survey (Zhou et al. 2024), as well as two other prototypes
within the NICE survey, RO1001 at _z_ = 2.91 (Kalita et al.
2021) and CL J1001 at _z_ = 2.51 (Wang et al. 2018). Two
other starbursting protoclusters, SPT2349-56 at _z_ = 4.3
(Hill et al. 2022) and Distant Red Core at _z_ = 4.0 (Long
et al. 2020), are shown as a cyan square and diamond,
respectively. CGG-z4, a compact galaxy group at _z_ = 4.3
in the COSMOS field (Brinch et al. 2025), is shown as
a cyan circle. The black dots and the curves show the
(proto)clusters and redshift evolution compiled in Alberts
& Noble (2022). The (proto)cluster data are drawn from
Haines et al. (2013); Santos et al. (2014, 2015); Popesso
et al. (2015a,b); Ma et al. (2015); Alberts et al. (2014, 2016);
Casey (2016); Strazzullo et al. (2018); Smith et al. (2019);
Lacaille et al. (2019). The black dashed line shows a redshift evolution trend _∝_ _z_ [1] _[.]_ [77] (Popesso et al. 2011), while
the green dash-dotted line indicates a _∝_ (1 + _z_ ) [5] _[.]_ [4] relation
(Alberts et al. 2014; Webb et al. 2013; Bai et al. 2009).
The cyan dash-dotted line also follows the _∝_ (1 + _z_ ) [5] _[.]_ [4]
trend, but is scaled from logM 200 /M _⊙_ = 14.5 to 14, assuming ΣSFR/ _M_ halo _∝_ _M_ halo _[−]_ [1] _[.]_ [5] [(][Webb] [et] [al.] [2013][).] [The] [solid]
line shows a steeper evolution of _∝_ (1 + _z_ ) [7] (Cowie et al.
2004; Geach et al. 2006; Biviano et al. 2011), normalized
at _z_ = 0.5. For field galaxies, the gray shaded region represents the redshift evolution trend of _∝_ (1 + _z_ ) [3] _[−]_ [4] based on
Le Floc’h et al. (2005); Rujopakarn et al. (2010); Sargent
et al. (2012); Ilbert et al. (2015).


lection criteria. In contrast, the less massive galaxies display
slightly elevated star formation compared to field galaxies,
a trend similar to that observed in H _α_ emitters within the
young protocluster USS1558-003 at _z_ = 2.53 (Hayashi et al.
2012; Daikuhara et al. 2024).


It is important to note that the cluster members were
primarily selected based on photometric redshifts, which
may include interlopers. This may affect the results shown
in Fig. 4, especially at the low-mass end, where the contamination is most significant. On the other hand, the highmass end is less impacted as it is dominated by CO-detected
galaxies that are spectroscopically confirmed members.



Fig. 4: Star-forming main sequence of galaxy members
in the eight protoclusters within NICE-COSMOS. COdetected and dust continuum-detected members are highlighted with open red circles, while other FIR-detected
galaxies are marked with open red squares. The remaining cluster members are represented as red dots. To enable
comparison, the galaxies are scaled to a common redshift of
_z_ = 2.5, using the SFMS normalization and redshift evolution from Schreiber et al. (2015). The SFRs of FIR-detected
members are derived from 3 GHz radio emission or 24 _µ_ m
fluxes, while the SFRs for the rest are obtained from COSMOS2020 (see Section 2.2 for details). The pink curve represents the median SFR of member galaxies within the NICECOSMOS protoclusters. For reference, the black solid curve
shows the main sequence at _z_ = 2 _._ 5 from Schreiber et al.
(2015), and the dotted curve indicates the starburst regime,
defined as _R_ SB = 4 (Rodighiero et al. 2011). The blue arrow indicates the mass completeness limit of star-forming
galaxies at _z_ =2.5 from COSMOS2020 (Weaver et al. 2022).


_3.3._ _Build-up_ _of_ _massive_ _galaxies_ _in_ _the_ _dense_ _cores_


We analyzed the stellar mass distribution of the cluster
galaxies and found that more massive galaxies are located
closer to the protocluster center (Fig. 5a). The median
stellar mass within 0.1 _R_ _vir_ is _∼_ 10 [10] _[.]_ [6] M _⊙_, compared to
_∼_ 10 [9] _[.]_ [5] M _⊙_ at the outskirts, representing more than 1 dex
difference. This difference in the mass of main sequence
galaxies naturally enhances the overall star formation activities in these protoclusters. Out of the 31 massive galaxies ( _M_ _⋆_ - 3 _×_ 10 [10] M _⊙_ ), 21 are located within 0.3 _R_ _vir_, with
all but one showing detected CO emission. This aligns with
the high fraction of SMGs predicted in protocluster cores
by Araya-Araya et al. (2024) simulations and highlights the
presence of substantial gas reservoirs in these regions. Similarly, a top-heavy stellar mass function has been identified
in the starbursting protocluster CL J1001 (Sun et al. 2024),
suggesting a prevalence of massive galaxy accumulation in
such protoclusters. Although these massive galaxies generally follow the main sequence, those in the cores are on average situated above the main sequence compared to their
counterparts in the outskirts (Fig. 5b).


Article number, page 5 of 12

_A&A_ _proofs:_ manuscript no. aa53996-25



Fig. 5: **Panel** **a:** Stellar mass as a function of distance to
the cluster centers. The symbols are as defined in Fig. 4.
The completeness limits of star-forming galaxies and quiescent galaxies are also shown as references. **Panel** **b:** Starburstiness ( _R_ SB ) of massive galaxies ( _M_ _⋆_ - 3 _×_ 10 [10] M _⊙_ ) as
a function of the distance to the cluster center. The dashed
line shows the field main sequence and the shaded region
shows the uncertainty.


The field of view (FoV) of the NOEMA and ALMA observations, with a full width at half maximum (FWHM) of
_∼_ 30 _[′′]_ and _∼_ 1 _[′]_, respectively, is sufficiently large to encompass the area within the virial radius of the protoclusters.
This indicates that we are witnessing the rapid build-up
of massive galaxies in the cores of these protoclusters at
cosmic noon.


_3.4._ _Gas_ _content_


The gas masses of CO-detected NICE-COSMOS galaxies span the range _M_ gas = 10 [10] _[.]_ [6] _∼_ 10 [11] _[.]_ [7] M _⊙_ . The gasto-stellar mass ratio _µ_ gas = _M_ gas / _M_ _⋆_ and gas depletion
time _τ_ gas = _M_ gas /SFR of NICE protocluster galaxies have
median values of _µ_ gas _,_ NICE = 1.32and _τ_ gas _,_ NICE = 0.78 Gyr.
These values are consistent with those observed in other
protocluster galaxies at similar redshifts (e.g., Tadaki et al.
2019; Pérez-Martínez et al. 2025). However, protoclusters
at higher redshifts ( _z_ ≳ 4), such as SPT2349-56 (Hill et al.
2022) and LH-SBC3 (Zhou et al. 2024), tend to show lower
_µ_ gas and _τ_ gas, while massive galaxies in Distant Red Core
at _z_ =4 (Long et al. 2020) have comparable gas content to
those in protoclusters at _z ∼_ 2.5. For a fair comparison, we
recalculated the gas masses of galaxies in the literature us

Article number, page 6 of 12



ing the same method described in Section 2.3 when CO(1-0)
measurements were unavailable.

To assess the environmental impact on the gas content, we normalized _µ_ gas and _τ_ gas to the corresponding
field levels, accounting for their dependence on stellar mass,
starburstiness, and redshift. This analysis utilized parameterized relations compiled from the A [3] COSMOS project,
based on a systematic mining of ALMA archival data for
CO-observed galaxies in the COSMOS field (Liu et al.
2019). The results are presented in Fig. 6.
The 3 _σ_ detection limit of the NICE observations corresponds to a gas mass of _M_ gas _∼_ 10 [11] M _⊙_ for galaxies at
_z ∼_ 2.5, meaning that our sample predominantly includes
the most massive members and the less massive galaxies
with high starburstiness (Fig. 6c). The most massive ones
( _M_ _⋆_ - 10 [10] _[.]_ [8] M _⊙_ ), which are concentrated in the core regions, are nearly all detected via CO or dust continuum
emission. These massive galaxies generally exhibit higher
gas content ( _∼_ 2 _×_ ) compared to their counterparts in the
field (Fig. 6 a, b). Several of them display significantly elevated gas-to-stellar mass ratios and gas depletion times
relative to field galaxies. However, their SFRs are not correspondingly enhanced, suggesting that they have abundant
gas reservoirs to sustain their growth or their SFRs are
prevented from increasing to starburst levels due to mergerrelated processes or negative feedback.
We also note that the field galaxies (Kaasinen et al.
2019; Boogaard et al. 2020; Frias Castillo et al. 2023),
whose molecular gas content is derived from CO(1–0) emission adopting _α_ CO obtained using the method outlined in
Section 2.3, fall within the field-level range defined by the
A [3] COSMOS project. This is consistent with the findings
from Calvi et al. (2023), who found a correlation between
molecular gas masses of SMGs and the significance of the
associated overdensity.
Most galaxies with lower stellar masses are not detected
in CO or dust continuum, except for the starbursts. However, these starburst galaxies exhibit gas-to-stellar mass ratios and gas depletion times comparable to those of field
galaxies. It remains unclear whether the CO- or dustnondetected cluster members have enhanced or deficient
gas content.
In contrast, three protoclusters traced by Ly _α_ emitters
and/or red galaxies surrounding a radio galaxy (Tadaki
et al. 2019) show the opposite trend, with a declining
gas fraction and gas depletion time as stellar mass increases. This indicates a mass-dependent environmental effect, where gas accretion is accelerated in less massive galaxies, while suppressed in more massive ones. These contrasting trends may reflect different evolutionary stages of the
two protocluster populations.
Interestingly, we find that most of the gas-rich galaxies
belong to protoclusters at _z ∼_ 2.5, whereas massive galaxies
in more distant protoclusters exhibit a declining gas content, though still generally within the uncertainties of field
galaxies (Fig. 6d,e), approximately 2 times at _z_ = 2.5 and
1.2 times at _z_ = 4. Similarly, Calvi et al. (2023) identified a
possible transitioning phase at _z ∼_ 4, with _z_ < 4 protoclusters more populated by dusty galaxies. We speculate that
our observed trend may partly reflect a selection bias in constructing the field sample, which tends to favor the brightest
sources at high redshifts, typically located in dense environments.

Luwenjia Zhou et al.: NICE-COSMOS: Star Formation and Cold Gas Properties


Fig. 6: Gas-to-stellar mass ratio ( _µ_ gas = _M_ gas / _M_ _⋆_ ), gas depletion time ( _τ_ _gas_ = _M_ _gas_ _/SFR_ ), and starburstiness ( _R_ SB )
as a function of stellar mass (left column) and redshift (right column). _µ_ gas and _τ_ gas are scaled relative to field galaxy
levels ( _µ_ gas _,_ scale, _τ_ gas _,_ scale ), accounting for the stellar masses, redshifts, and starburstiness of each galaxy. The red circles
represent galaxies detected in CO or dust continuum in the NICE protoclusters, including the eight in the COSMOS
field (Sillassen et al. 2024), LH-SBC3 (Zhou et al. 2024), RO1001 (Kalita et al. 2021), and CL J1001 (Wang et al. 2018),
while red squares and dots indicate the 3 _σ_ upper limits of those detected in the FIR and the rest of the cluster galaxies.
Two additional starbursting protoclusters at _z_ ≳ 4, SPT2349-56 (Hill et al. 2022) and Distant Red Core (Long et al.
2020), are shown in cyan. Field galaxies from Kaasinen et al. (2019); Boogaard et al. (2020); Frias Castillo et al. (2023)
are represented as green triangles, with the molecular gas content derived from CO(1-0) emission lines. The black dashed
lines denote the positions of field galaxies; the gray shading indicates the uncertainties.



We further checked the overall mean intensity of the radiation field, < _U_ >, of the NICE-COSMOS protoclusters, as
measured from the integrated FIR SED fitting in Sillassen
et al. (2024). < _U_ - can be used to infer the metallicity
weighted star formation efficiency (SFE _≡_ 1/ _τ_ gas ) and is proportional to dust temperature (Magdis et al. 2012, 2017).
The evolution of < _U_ - with redshift for the eight protoclusters generally follows the trend observed in main sequence



galaxies (Béthermin et al. 2015); a few of them show lower
< _U_ >. This is in line with the moderately longer gas depletion time observed in the individual member galaxies and
may indicate a colder dust temperature in these protoclusters.


Article number, page 7 of 12

_A&A_ _proofs:_ manuscript no. aa53996-25


an overabundance of massive star-forming galaxies in these
protocluster cores, which contributes to their elevated
Σ SFR _/M_ halo . This finding aligns with the simulations by
Araya-Araya et al. (2024), which identify an excess of
massive star-forming galaxies undergoing a submillimeterbright phase in protocluster cores, suggesting a downsizing
formation scenario for massive galaxies.



Fig. 7: Evolution of the mean intensity of the radiation
field, < _U_ >, with redshift. The red circles show the overall
< _U_ - of the eight protoclusters in NICE-COSMOS. The
solid curve and dashed line represent the trend of main
sequence galaxies and starbursts, as in Béthermin et al.
(2015).


**4.** **Summary** **and** **discussion**


In this paper we analyzed the star formation and cold gas
properties of eight protoclusters in the COSMOS field, selected through the NICE survey, which targets intensively
star-forming protocluster cores at cosmic noon.
We find that the total SFR per unit halo mass
(Σ SFR _/M_ halo ) in protoclusters at _z_ - 2 increases rapidly
with redshift, scaling as (1+ _z_ ) [5] _[.]_ [4] (Fig. 3). This could be due
to either a higher number of massive star-forming galaxies in massive halos or enhanced star formation in cluster
galaxies. Additionally, we find that the fraction of quiescent
galaxies decreases relative to that observed in lower-redshift
(proto)clusters, and that the streaming mass of the halos
(i.e., the threshold mass delimiting the hot and cold in hot
accretion regimes; see Daddi et al. 2022 and Dekel et al.
2009) is also a good predictor for the quiescent fraction,
making the gas accretion mode a potential explanation for
the quiescent fraction evolution across halos (Elias et al. in
prep.). We also caution that the higher Σ SFR _/M_ halo values
at higher redshifts could also be partly driven by lower halo

masses.
Nevertheless, this rise in star formation activity in protoclusters is not reflected in individual member galaxies.
The SFMS remains comparable to that observed in the field
(Fig. 4), suggesting that the elevated Σ SFR _/M_ halo in protoclusters is not driven by a higher fraction of starburst galaxies in dense environments. We note that the cluster members may be affected by contamination due to photometric
redshift uncertainties (Sillassen et al. 2024). However, the
massive end is dominated by CO-detected and thus spectroscopically confirmed members, making the main sequence
at the high-mass end less susceptible to interlopers.
Using observations from NOEMA and ALMA in
the NICE survey, we investigated the gas content of
cluster galaxies. The CO or dust continuum-detected
galaxies are predominantly massive cluster members
( _M_ _⋆_ - 3 _×_ 10 [10] M _⊙_ ), which preferentially reside in the core
of the protoclusters ( _r_ ≲ 0.3 _R_ _vir_, Fig. 5). This indicates


Article number, page 8 of 12



In terms of stellar-to-gas mass ratio and gas depletion
time, the median values are consistent with field levels.
However, the most massive galaxies ( _M_ _⋆_ - 8 _×_ 10 [10] M _⊙_ ) are
notably more gas-rich than their field counterparts (Fig. 6).
This suggests efficient cold gas accretion in the central regions of these protoclusters, supporting the growth of these
galaxies to higher masses while remaining in the main sequence mode, without triggering starburst phases. For the
less massive galaxies, CO or dust continuum detections are
limited to the most starbursting ones, which follow the scaling relation ( _µ_ gas ( _z_, _M_ _⋆_, _R_ SB ), _τ_ gas ( _z_, _M_ _⋆_, _R_ SB ), Liu et al.
2019) observed in the field galaxies. The moderately higher
_τ_ gas is consistent with the overall mean intensity of the
radiation field in the protoclusters, indicating a generally
cold dust temperature in these dense environments. However, we caution that the NICE survey is biased toward
protoclusters in active star-forming phases. The influence
of such environments on member galaxies may differ from
that observed in protoclusters selected through other methods.


_Acknowledgements._ We thank the anonymous referee for valuable comments. This work was supported by National Natural
Science Foundation of China (Project Nos. 13001103, 12173017
and Key Project No.12141301), National Key R&D Program of
China (grant no. 2023YFA1605600), Scientific Research Innovation Capability Support Project for Young Faculty (Project No.
ZYGXQNJSKYCXNLZCXM-P3), and the China Manned Space Program with grant no. CMS-CSST-2025-A04. L.Z. and Y.S. acknowledges the support from the National Key R&D Program of China No.
2022YFF0503401 and 2018YFA0404502, the National Natural Science
Foundation of China (NSFC grants 12141301, 12121003, 11825302).
Y.S. thanks the support by the New Cornerstone Science Foundation
through the XPLORER PRIZE. Y.J.W. acknowledges support by National Natural Science Foundation of China (Project No. 12403019)
and Jiangsu Natural Science Foundation (Project No. BK20241188).
GEM acknowledges the Villum Fonden research grant 13160 “Gas
to stars, stars to dust: tracing star formation across cosmic time,”
grant 37440, “The Hidden Cosmos,” and the Cosmic Dawn Center of
Excellence funded by the Danish National Research Foundation under the grant No. 140. CGG acknowledges support from CNES. ZJ
acknowledges funding from JWST/NIRCam contract to the University of Arizona NAS5-02015. ID acknowledges funding by the INAF
Minigrant "Harnessing the power of VLBA toward a census of AGN
and star formation at high redshift" and by the European Union –
NextGenerationEU, RRF M4C2 1.1, Project 2022JZJBHM: "AGNsCAN: zooming-in on the AGN-galaxy connection since the cosmic
noon" - CUP C53D23001120006. CdE acknowledges funding from the
MCIN/AEI (Spain) and the “NextGenerationEU”/PRTR (European
Union) through the Juan de la Cierva-Formación program (FJC2021047307-I). SJ is supported by the European Union’s Horizon Europe
research and innovation program under the Marie Skłodowska-Curie
grant agreement No. 101060888. This research used APLpy, an opensource plotting package for Python (Robitaille & Bressert 2012; Robitaille 2019). This work is based on observations carried out under project number M21AA with the IRAM NOEMA Interferometer.
IRAM is supported by INSU/CNRS (France), MPG (Germany) and
IGN (Spain). This research uses data obtained through the Telescope
Access Program (TAP), which is funded by the National Astronomical Observatories, Chinese Academy of Sciences, and the Special Fund
for Astronomy from the Ministry of Finance. This work is based on
observations obtained with WIRCam, a joint project of CFHT, Taiwan, Korea, Canada, France, at the Canada-France-Hawaii Telescope
(CFHT) which is operated by the National Research Council (NRC)
of Canada, the Institute National des Sciences de l’Univers of the Cen

Luwenjia Zhou et al.: NICE-COSMOS: Star Formation and Cold Gas Properties



tre National de la Recherche Scientifique of France, and the University
of Hawaii.


**References**


Alberts, S. & Noble, A. 2022, [Universe,](http://dx.doi.org/10.3390/universe8110554) 8, [554](https://ui.adsabs.harvard.edu/abs/2022Univ....8..554A)
Alberts, S., Pope, A., Brodwin, M., et al. 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt1897) 437, 437
Alberts, S., Pope, A., Brodwin, M., et al. 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/825/1/72) [825,](https://ui.adsabs.harvard.edu/abs/2016ApJ...825...72A) 72
Araya-Araya, P., Cochrane, R. K., Hayward, C. C., et al. 2024, [arXiv](https://ui.adsabs.harvard.edu/abs/2024arXiv240800062A)
[e-prints,](http://dx.doi.org/10.48550/arXiv.2408.00062) [arXiv:2408.00062](https://ui.adsabs.harvard.edu/abs/2024arXiv240800062A)
Arnouts, S., Moscardini, L., Vanzella, E., et al. 2002, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2002.04988.x) [329,](https://ui.adsabs.harvard.edu/abs/2002MNRAS.329..355A)
[355](https://ui.adsabs.harvard.edu/abs/2002MNRAS.329..355A)
Bai, L., Rieke, G. H., Rieke, M. J., Christlein, D., & Zabludoff, A. I.
2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/693/2/1840) 693, 1840
Bakx, T. J. L. C., Berta, S., Dannerbauer, H., et al. 2024, [MNRAS,](http://dx.doi.org/10.1093/mnras/stae1155)

530, 4578
Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, [MN-](http://dx.doi.org/10.1093/mnras/stz1182)
[RAS,](http://dx.doi.org/10.1093/mnras/stz1182) 488, 3143
Béthermin, M., Daddi, E., Magdis, G., et al. 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201425031) 573, [A113](https://ui.adsabs.harvard.edu/abs/2015A&A...573A.113B)
Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa3862) [501,](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501.3926B)
[3926](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501.3926B)
Biviano, A., Fadda, D., Durret, F., Edwards, L. O. V., & Marleau, F.
2011, [A&A,](http://dx.doi.org/10.1051/0004-6361/201016174) 532, A77
Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/abb82f) [902,](https://ui.adsabs.harvard.edu/abs/2020ApJ...902..109B)
[109](https://ui.adsabs.harvard.edu/abs/2020ApJ...902..109B)
Brinch, M., Jin, S., Gobat, R., et al. 2025, arXiv [e-prints,](https://ui.adsabs.harvard.edu/abs/2025arXiv250105288B)
[arXiv:2501.05288](https://ui.adsabs.harvard.edu/abs/2025arXiv250105288B)
Calvi, R., Castignani, G., & Dannerbauer, H. 2023, [A&A,](http://dx.doi.org/10.1051/0004-6361/202346200) 678, A15
Casey, C. M. 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/824/1/36) [824,](https://ui.adsabs.harvard.edu/abs/2016ApJ...824...36C) 36
Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, [ApJ,](http://dx.doi.org/10.3847/1538-4357/acc2bc) [954,](https://ui.adsabs.harvard.edu/abs/2023ApJ...954...31C)
[31](https://ui.adsabs.harvard.edu/abs/2023ApJ...954...31C)
Chabrier, G. 2003, [ApJ,](http://dx.doi.org/10.1086/374879) 586, [L133](https://ui.adsabs.harvard.edu/abs/2003ApJ...586L.133C)
Cowie, L. L., Barger, A. J., Fomalont, E. B., & Capak, P. 2004, [ApJ,](http://dx.doi.org/10.1086/383198)

603, L69
Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201425043) 577, A46
Daddi, E., Elbaz, D., Walter, F., et al. 2010, [ApJ,](http://dx.doi.org/10.1088/2041-8205/714/1/L118) 714, [L118](https://ui.adsabs.harvard.edu/abs/2010ApJ...714L.118D)
Daddi, E., Rich, R. M., Valentino, F., et al. 2022, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ac531f) 926, L21
Daikuhara, K., Kodama, T., Pérez-Martínez, J. M., et al. 2024, [MN-](http://dx.doi.org/10.1093/mnras/stae1243)
[RAS,](http://dx.doi.org/10.1093/mnras/stae1243) 531, 2335
Dannerbauer, H., Lehnert, M. D., Emonts, B., et al. 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201730449) [608,](https://ui.adsabs.harvard.edu/abs/2017A&A...608A..48D)
[A48](https://ui.adsabs.harvard.edu/abs/2017A&A...608A..48D)
Dekel, A., Birnboim, Y., Engel, G., et al. 2009, [Nature,](http://dx.doi.org/10.1038/nature07648) 457, 451
[Delvecchio, I., Daddi, E., Sargent, M. T., et al. 2021, A&A, 647, A123](http://dx.doi.org/10.1051/0004-6361/202039647)
Frias Castillo, M., Hodge, J., Rybak, M., et al. 2023, [ApJ,](http://dx.doi.org/10.3847/1538-4357/acb931) 945, 128
Gao, Y. & Solomon, P. M. 2004, [ApJ,](http://dx.doi.org/10.1086/382999) 606, 271
Geach, J. E., Smail, I., Ellis, R. S., et al. 2006, [ApJ,](http://dx.doi.org/10.1086/506469) 649, 661
Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/800/1/20) [800,](https://ui.adsabs.harvard.edu/abs/2015ApJ...800...20G) 20
[Gómez-Guijarro, C., Riechers, D. A., Pavesi, R., et al. 2019, ApJ, 872,](http://dx.doi.org/10.3847/1538-4357/ab002a)
[117](https://ui.adsabs.harvard.edu/abs/2019ApJ...872..117G)
Haines, C. P., Pereira, M. J., Smith, G. P., et al. 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/775/2/126) 775, 126
Hayashi, M., Kodama, T., Tadaki, K.-i., Koyama, Y., & Tanaka, I.
2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/757/1/15) [757,](https://ui.adsabs.harvard.edu/abs/2012ApJ...757...15H) 15
Hill, R., Chapman, S., Phadke, K. A., et al. 2022, [MNRAS,](http://dx.doi.org/10.1093/mnras/stab3539) 512, 4352
Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, [MNRAS,](http://dx.doi.org/10.1093/mnrasl/slx033) [468,](https://ui.adsabs.harvard.edu/abs/2017MNRAS.468L.103H)
[L103](https://ui.adsabs.harvard.edu/abs/2017MNRAS.468L.103H)
Ilbert, O., Arnouts, S., Le Floc’h, E., et al. 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201425176) [579,](https://ui.adsabs.harvard.edu/abs/2015A&A...579A...2I) A2
Ilbert, O., McCracken, H. J., Le Fèvre, O., et al. 2013, [A&A,](http://dx.doi.org/10.1051/0004-6361/201321100) [556,](https://ui.adsabs.harvard.edu/abs/2013A&A...556A..55I)
[A55](https://ui.adsabs.harvard.edu/abs/2013A&A...556A..55I)
Jin, S., Daddi, E., Liu, D., et al. 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aad4af) [864,](https://ui.adsabs.harvard.edu/abs/2018ApJ...864...56J) 56
Jin, S., Sillassen, N. B., Magdis, G. E., et al. 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202348540) [683,](https://ui.adsabs.harvard.edu/abs/2024A&A...683L...4J) L4
Jin, S., Sillassen, N. B., Magdis, G. E., et al. 2023, [A&A,](http://dx.doi.org/10.1051/0004-6361/202245724) 670, L11
Kaasinen, M., Scoville, N., Walter, F., et al. 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab253b) [880,](https://ui.adsabs.harvard.edu/abs/2019ApJ...880...15K) 15
Kalita, B. S., Daddi, E., D’Eugenio, C., et al. 2021, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ac16dc) 917, L17
Kashino, D., Silverman, J. D., Sanders, D., et al. 2019, [ApJS,](http://dx.doi.org/10.3847/1538-4365/ab06c4) [241,](https://ui.adsabs.harvard.edu/abs/2019ApJS..241...10K) 10
Kennicutt, Robert C., J. 1998, [ApJ,](http://dx.doi.org/10.1086/305588) 498, 541
Lacaille, K. M., Chapman, S. C., Smail, I., et al. 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz1742) [488,](https://ui.adsabs.harvard.edu/abs/2019MNRAS.488.1790L)
[1790](https://ui.adsabs.harvard.edu/abs/2019MNRAS.488.1790L)
Le Floc’h, E., Papovich, C., Dole, H., et al. 2005, [ApJ,](http://dx.doi.org/10.1086/432789) 632, 169
Liu, D., Gao, Y., Isaak, K., et al. 2015, [ApJ,](http://dx.doi.org/10.1088/2041-8205/810/2/L14) 810, L14
Liu, D., Schinnerer, E., Groves, B., et al. 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab578d) 887, 235
Long, A. S., Cooray, A., Ma, J., et al. 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab9d1f) 898, 133
Ma, C. J., Smail, I., Swinbank, A. M., et al. 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/806/2/257) 806, 257
Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/760/1/6) [760,](https://ui.adsabs.harvard.edu/abs/2012ApJ...760....6M) 6
Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201731037) 603, A93
Noble, A. G., McDonald, M., Muzzin, A., et al. 2017, [ApJ,](http://dx.doi.org/10.3847/2041-8213/aa77f3) 842, L21
Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aaa1f1) [856,](https://ui.adsabs.harvard.edu/abs/2018ApJ...856...72O) 72
Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/721/1/193) 721, 193
[Pensabene, A., Cantalupo, S., Cicone, C., et al. 2024, A&A, 684, A119](http://dx.doi.org/10.1051/0004-6361/202348659)



Pérez-Martínez, J. M., Dannerbauer, H., Emonts, B. H. C., et al. 2025,

[A&A,](http://dx.doi.org/10.1051/0004-6361/202450785) 696, [A236](https://ui.adsabs.harvard.edu/abs/2025A&A...696A.236P)
Pérez-Martínez, J. M., Dannerbauer, H., Kodama, T., et al. 2023,

[MNRAS,](http://dx.doi.org/10.1093/mnras/stac2784) 518, 1707
Popesso, P., Biviano, A., Finoguenov, A., et al. 2015a, [A&A,](http://dx.doi.org/10.1051/0004-6361/201424715) [579,](https://ui.adsabs.harvard.edu/abs/2015A&A...579A.132P)
[A132](https://ui.adsabs.harvard.edu/abs/2015A&A...579A.132P)
Popesso, P., Biviano, A., Finoguenov, A., et al. 2015b, [A&A,](http://dx.doi.org/10.1051/0004-6361/201424711) [574,](https://ui.adsabs.harvard.edu/abs/2015A&A...574A.105P)
[A105](https://ui.adsabs.harvard.edu/abs/2015A&A...574A.105P)
Popesso, P., Rodighiero, G., Saintonge, A., et al. 2011, [A&A,](http://dx.doi.org/10.1051/0004-6361/201015672) [532,](https://ui.adsabs.harvard.edu/abs/2011A&A...532A.145P)
[A145](https://ui.adsabs.harvard.edu/abs/2011A&A...532A.145P)
Robitaille, T. 2019, APLpy v2.0: The Astronomical Plotting Library
in Python
Robitaille, T. & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library
Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, [ApJ,](http://dx.doi.org/10.1088/2041-8205/739/2/L40) 739, L40
Rudnick, G., Hodge, J., Walter, F., et al. 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa87b2) [849,](https://ui.adsabs.harvard.edu/abs/2017ApJ...849...27R) 27
[Rujopakarn, W., Eisenstein, D. J., Rieke, G. H., et al. 2010, ApJ, 718,](http://dx.doi.org/10.1088/0004-637X/718/2/1171)
[1171](https://ui.adsabs.harvard.edu/abs/2010ApJ...718.1171R)
Santos, J. S., Altieri, B., Tanaka, M., et al. 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt2376) 438, 2565
Santos, J. S., Altieri, B., Valtchanov, I., et al. 2015, [MNRAS,](http://dx.doi.org/10.1093/mnrasl/slu180) [447,](https://ui.adsabs.harvard.edu/abs/2015MNRAS.447L..65S)
[L65](https://ui.adsabs.harvard.edu/abs/2015MNRAS.447L..65S)
Sargent, M. T., Béthermin, M., Daddi, E., & Elbaz, D. 2012, [ApJ,](http://dx.doi.org/10.1088/2041-8205/747/2/L31)

747, L31
Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/793/1/19) [793,](https://ui.adsabs.harvard.edu/abs/2014ApJ...793...19S) 19
Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201425017) 575, A74
Scoville, N., Sheth, K., Aussel, H., et al. 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/820/2/83) [820,](https://ui.adsabs.harvard.edu/abs/2016ApJ...820...83S) 83
Shimakawa, R., Kodama, T., Hayashi, M., et al. 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx2494) [473,](https://ui.adsabs.harvard.edu/abs/2018MNRAS.473.1977S)
[1977](https://ui.adsabs.harvard.edu/abs/2018MNRAS.473.1977S)
Sillassen, N. B., Jin, S., Magdis, G. E., et al. 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202450760) 690, A55
Sillassen, N. B., Jin, S., Magdis, G. E., et al. 2022, [A&A,](http://dx.doi.org/10.1051/0004-6361/202244661) [665,](https://ui.adsabs.harvard.edu/abs/2022A&A...665L...7S) L7
Smith, C. M. A., Gear, W. K., Smith, M. W. L., Papageorgiou, A., &
Eales, S. A. 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz1090) 486, 4304
Smolčić, V., Novak, M., Delvecchio, I., et al. 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201730685) [602,](https://ui.adsabs.harvard.edu/abs/2017A&A...602A...6S) A6
Strazzullo, V., Coogan, R. T., Daddi, E., et al. 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aacd10) [862,](https://ui.adsabs.harvard.edu/abs/2018ApJ...862...64S) 64
Sun, H., Wang, T., Xu, K., et al. 2024, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ad4986) 967, L34
Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aaa4b4) 853, 179
Tadaki, K.-i., Kodama, T., Hayashi, M., et al. 2019, [PASJ,](http://dx.doi.org/10.1093/pasj/psz005) 71, 40
Valentino, F., Daddi, E., Puglisi, A., et al. 2020a, [A&A,](http://dx.doi.org/10.1051/0004-6361/202038322) 641, [A155](https://ui.adsabs.harvard.edu/abs/2020A&A...641A.155V)
Valentino, F., Daddi, E., Puglisi, A., et al. 2020b, [A&A,](http://dx.doi.org/10.1051/0004-6361/202038322) 641, [A155](https://ui.adsabs.harvard.edu/abs/2020A&A...641A.155V)
Valentino, F., Daddi, E., Strazzullo, V., et al. 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/801/2/132) 801, 132
van der Burg, R. F. J., Rudnick, G., Balogh, M. L., et al. 2020, [A&A,](http://dx.doi.org/10.1051/0004-6361/202037754)

638, [A112](https://ui.adsabs.harvard.edu/abs/2020A&A...638A.112V)
Wang, T., Elbaz, D., Daddi, E., et al. 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/828/1/56) [828,](https://ui.adsabs.harvard.edu/abs/2016ApJ...828...56W) 56
Wang, T., Elbaz, D., Daddi, E., et al. 2018, [ApJ,](http://dx.doi.org/10.3847/2041-8213/aaeb2c) 867, L29
Wang, Y., Wang, T., Liu, D., et al. 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202347787) 685, A79
Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, [ApJS,](http://dx.doi.org/10.3847/1538-4365/ac3078) [258,](https://ui.adsabs.harvard.edu/abs/2022ApJS..258...11W)
[11](https://ui.adsabs.harvard.edu/abs/2022ApJS..258...11W)
Webb, T. M. A., O’Donnell, D., Yee, H. K. C., et al. 2013, [AJ,](http://dx.doi.org/10.1088/0004-6256/146/4/84) [146,](https://ui.adsabs.harvard.edu/abs/2013AJ....146...84W)
[84](https://ui.adsabs.harvard.edu/abs/2013AJ....146...84W)
Williams, R. J., Quadri, R. F., Franx, M., van Dokkum, P., & Labbé,
I. 2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/691/2/1879) 691, 1879
Wuyts, S., Labbé, I., Förster Schreiber, N. M., et al. 2008, [ApJ,](http://dx.doi.org/10.1086/588749) [682,](https://ui.adsabs.harvard.edu/abs/2008ApJ...682..985W)
[985](https://ui.adsabs.harvard.edu/abs/2008ApJ...682..985W)
Zhang, Y. H., Dannerbauer, H., Pérez-Martínez, J. M., et al. 2024,

[A&A,](http://dx.doi.org/10.1051/0004-6361/202451379) 692, A22
Zhou, L., Wang, T., Daddi, E., et al. 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202348351) 684, [A196](https://ui.adsabs.harvard.edu/abs/2024A&A...684A.196Z)


1 School of Astronomy and Space Science, Nanjing University,
Nanjing 210093, China
2 Key Laboratory of Modern Astronomy and Astrophysics
(Nanjing University), Ministry of Education, Nanjing
210093, China
3 AIM, CEA, CNRS, Université Paris-Saclay, Université Paris
Diderot, Sorbonne Paris Cité, F-91191 Gif-sur-Yvette, France


4
IRAM, 300 rue de la piscine, F-38406 Saint-Martin d’Hères,
France
5 Cosmic Dawn Center (DAWN), Jagtvej 128, DK2200 Copenhagen N, Denmark
6 DTU-Space, Technical University of Denmark, Elektrovej
327, 2800 Kgs. Lyngby, Denmark
7 Max-Planck-Institut für Extraterrestrische Physik (MPE),
Giessenbachstrasse 1, 85748 Garching, Germany
8 School of Mathematics and Physics, Anqing Normal University, Anqing 246133, China


Article number, page 9 of 12

_A&A_ _proofs:_ manuscript no. aa53996-25


9 Institute of Astronomy and Astrophysics, Anqing Normal
University, Anqing 246133, China
10 Purple Mountain Observatory, Chinese Academy of Sciences,
10 Yuanhua Road, Nanjing 210023, China
11 Niels Bohr Institute, University of Copenhagen, Jagtvej 128,
DK-2200 Copenhagen N, Denmark
12 Instituto de Astrofísica de Canarias, C. Vía Láctea, s/n,
38205 La Laguna, Tenerife, Spain
13 Universidad de La Laguna, Dpto. Astrofísica, 38206 La Laguna, Tenerife, Spain
14 European Southern Observatory, Karl-Schwarzschild-Str. 2,
D-85748 Garching bei Munchen, Germany
15 Steward Observatory, University of Arizona, 933 N. Cherry
Avenue, Tucson, AZ 85721, USA
16 INAF – Osservatorio di Astrofisica e Scienza dello Spazio di
Bologna, Via Gobetti 93/3, I-40129 Bologna, Italy
17 Department of Astronomy, University of Geneva, Chemin Pegasi 51, 1290 Versoix, Switzerland
18 Instituto de Física, Pontificia Universidad Católica de Valparaíso, Casilla 4059, Valparaíso, Chile
19 INAF - Osservatorio Astronomico di Trieste, Via Tiepolo 11,
34131, Trieste, Italy
20 IFPU - Institute for Fundamental Physics of the Universe,
Via Beirut 2, 34014, Trieste
21 Department of Physics, University of Helsinki, Gustaf Hällströmin katu 2, FI-00014 Helsinki, Finland
22 Department of Physics & Astronomy, University of California
Los Angeles, 430 Portola Plaza, Los Angeles, CA 90095, USA
23 Chinese Academy of Sciences South America Center for Astronomy (CASSACA), National Astronomical Observatories
of China (NAOC), 20A Datun Road


Article number, page 10 of 12

Luwenjia Zhou et al.: NICE-COSMOS: Star Formation and Cold Gas Properties


**Appendix** **A:** **NICE-COSMOS** **images**


Fig. A.1: RGB images of the eight protoclusters in the COSMOS field identified in the NICE survey. The color channels
are R: [4.5], G: _K_ _s_, B: _Y_, except for the two protoclusters covered by COSMOS-Web (Casey et al. 2023), COSMOS-SBC4
and COSMOS-SBCX3, where the color channels are R: F444W, G: F277W, B: F150W. Each image has a size of 1 _[′]_ _×_ 1 _[′]_ .
The red, yellow, and cyan circles highlight the CO-detected members, spectroscopically confirmed members, and all other
members identified by Sillassen et al. (2024), respectively.


Article number, page 11 of 12

_A&A_ _proofs:_ manuscript no. aa53996-25


Fig. A.1: continued.



Article number, page 12 of 12


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "z_spec = 3.604 - 3.613",
  "failed_quote": "HPC1001 ... * 0.07 3.613 11.2 +0 −0. .2 2 662 +65 −66 3.59 11.48 ± 0.07 11.30 ± 0.04 125 ± 41 978 ± 883"
 },
 {
  "path": "science.targets[0].distance_source.evidence[0]",
  "value": "Sillassen et al. (2024)",
  "failed_quote": "HPC1001 ... * 0.07 3.613 11.2 +0 −0. .2 2 662 +65 −66 3.59 11.48 ± 0.07 11.30 ± 0.04 125 ± 41 978 ± 883"
 },
 {
  "path": "data.bands.evidence[0]",
  "value": "3 mm and 2 mm (NOEMA and ALMA)",
  "failed_quote": "The dust continuum at 3 mm and 2 mm from the NOEMA and ALMA observations of the NICE survey, closely corresponding to rest-frame 850 µm for the cluster galaxies, was used to derive gas masses."
 },
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "CO emission and 3 mm / 2 mm dust continuum observations (159-hour Large Program ID: M21AA)",
  "failed_quote": "The dust continuum at 3 mm and 2 mm from the NOEMA and ALMA observations of the NICE survey, closely corresponding to rest-frame 850 µm for the cluster galaxies, was used to derive gas masses."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "COSMOS2020 catalog (IRAC magnitudes, photometric redshifts, stellar masses, SFRs, mass completeness limits)",
  "failed_quote": "Briefly, the members are selected with | z phot - z spec , group | < 0.1(1 + z spec , group ) within a virial projected radius based on the COSMOS2020 catalog (Weaver et al. 2022)."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Select galaxies from COSMOS2020 catalog using photometric/spectroscopic redshifts within 1 R_vir as defined in Sillassen et al. (2024)",
  "failed_quote": "Briefly, the members are selected with | z phot - z spec , group | < 0.1(1 + z spec , group ) within a virial projected radius based on the COSMOS2020 catalog (Weaver et al. 2022)."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "|z_phot - z_spec,group| < 0.1(1 + z_spec,group)",
  "failed_quote": "Briefly, the members are selected with | z phot - z spec , group | < 0.1(1 + z spec , group ) within a virial projected radius based on the COSMOS2020 catalog (Weaver et al. 2022)."
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "log10 M_gas^RJ of HPC1001 central blend = 11.48 log10(M_⊙)",
  "failed_quote": "HPC1001 ... * 0.07 3.613 11.2 +0 −0. .2 2 662 +65 −66 3.59 11.48 ± 0.07 11.30 ± 0.04 125 ± 41 978 ± 883"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "log10 M_gas^CO of HPC1001 central blend = 11.30 log10(M_⊙)",
  "failed_quote": "HPC1001 ... * 0.07 3.613 11.2 +0 −0. .2 2 662 +65 −66 3.59 11.48 ± 0.07 11.30 ± 0.04 125 ± 41 978 ± 883"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "log10 M_gas^RJ of COS-SBC6 ID 839791 = 11.51 log10(M_⊙)",
  "failed_quote": "COS-SBC6 839791 ** 0.10 2.324 11.0 +0 −0. .0 1 93 +6 −6 4.01 11.51 ± 0.04 11.03 ± 0.05 1143 ± 60 195 ± 25"
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "Massive galaxies are strongly concentrated in the protocluster cores and are almost all detected in CO or dust continuum",
  "failed_quote": "Out of the 31 massive galaxies ( M ⋆ > 3 × 10 10 M ⊙ ), 21 are located within 0.3 R vir, with all but one showing detected CO emission."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[1]",
  "value": "Evaluated four alternative SFR tracers (24 µm, deblended FIR, LePhare SED, and protocluster FIR SED scaled by dust continuum) alongside 3 GHz radio SFR; used 24 µm instead of 3 GHz for radio-loud AGN 839791.",
  "failed_quote": "For galaxy 839791 in COSMOS-SBC6, which has a radio luminosity twice that of the crossover luminosity described in Wang et al. (2024), the threshold above which radio emission is dominated by AGN, we used SFR 24 µ m to minimize the contamination from AGN-related radio emission."
 }
]
```
