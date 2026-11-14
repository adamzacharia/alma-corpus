# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018ApJ...867...43T\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version September 19, 2018

Typeset using L [A] TEX **preprint** style in AASTeX62


The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Perseus Protostars. VI.
Characterizing the Formation Mechanism for Close Multiple Systems


John J. Tobin, [1, 2, 3] Leslie W. Looney, [4] Zhi-Yun Li, [5] Sarah I. Sadavoy, [6]
Michael M. Dunham, [7, 6] Dominique Segura-Cox, [4] Kaitlin Kratter, [8] Claire J. Chandler, [9]
Carl Melis, [10] Robert J. Harris, [4] and Laura Perez [11]


1 _Current_ _address:_ _National_ _Radio_ _Astronomy_ _Observatory,_ _520_ _Edgemont_ _Rd.,_ _Charlottesville,_ _VA_ _22903,_ _USA_
2 _Homer_ _L._ _Dodge_ _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Oklahoma,_ _440_ _W._ _Brooks_ _Street,_ _Norman,_
_OK_ _73019,_ _USA_
3 _Leiden_ _Observatory,_ _Leiden_ _University,_ _P.O._ _Box_ _9513,_ _2300-RA_ _Leiden,_ _The_ _Netherlands_
4 _Department_ _of_ _Astronomy,_ _University_ _of_ _Illinois,_ _Urbana,_ _IL_ _61801_
5 _Department_ _of_ _Astronomy,_ _University_ _of_ _Virginia,_ _Charlottesville,_ _VA_ _22903_
6 _Harvard-Smithsonian_ _Center_ _for_ _Astrophysics,_ _60_ _Garden_ _St,_ _MS_ _78,_ _Cambridge,_ _MA_ _02138_
7 _Department_ _of_ _Physics,_ _State_ _University_ _of_ _New_ _York_ _Fredonia,_ _Fredonia,_ _New_ _York_ _14063,_ _USA_
8 _University_ _of_ _Arizona,_ _Steward_ _Observatory,_ _Tucson,_ _AZ_ _85721_
9 _National_ _Radio_ _Astronomy_ _Observatory,_ _P.O._ _Box_ _O,_ _Socorro,_ _NM_ _87801_
10 _Center_ _for_ _Astrophysics_ _and_ _Space_ _Sciences,_ _University_ _of_ _California,_ _San_ _Diego,_ _CA_ _92093_
11 _Departamento_ _de_ _Astronom´ıa,_ _Universidad_ _de_ _Chile,_ _Camino_ _El_ _Observatorio_ _1515,_ _Las_ _Condes,_ _Santiago,_ _Chile_


ABSTRACT

We present Atacama Large Millimeter/submillimeter Array (ALMA) observations of
multiple protostar systems in the Perseus molecular cloud previously detected by the
Karl G. Jansky Very Large Array (VLA). We observed 17 close ( _<_ 600 AU separation)
multiple systems at 1.3 mm in continuum and five molecular lines (i.e., [12] CO, C [18] O,
13
CO, H 2 CO, SO) to characterize the circum-multiple environments in which these systems are forming. We detect at least one component in the continuum for the 17 multiple systems. In three systems, one companion is not detected, and for two systems the
companions are unresolved at our observed resolution. We also detect circum-multiple
dust emission toward 8 out of 9 Class 0 multiples. Circum-multiple dust emission is
not detected toward any of the 8 Class I multiples. Twelve systems are detected in the
dense gas tracers toward their disks/inner envelopes. For these 12 systems, we use the
dense gas observations to characterize their formation mechanism. The velocity gradients in the circum-multiple gas are clearly orthogonal to the outflow directions in 8
out of the 12 systems, consistent with disk fragmentation. Moreover, only two systems
with separations _<_ 200 AU are _inconsistent_ with disk fragmentation, in addition to the
two widest systems ( _>_ 500 AU). Our results suggest that disk fragmentation via gravitational instability is an important formation mechanism for close multiple systems,
but further statistics are needed to better determine the relative fraction formed via

this method.


1. INTRODUCTION

2 Tobin et al.


Star formation typically occurs within dense clouds of molecular gas in the interstellar medium.
These clouds of dense gas collapse to form stars when their self-gravity dominates over other sources
of support (e.g., thermal pressure, magnetic fields, turbulence, McKee & Ostriker 2007), forming
either a single or multiple star system. Nearly half of Sun-like stars (in terms of stellar mass) are
found in binary or higher-order multiple systems (Duquennoy & Mayor 1991; Raghavan et al. 2010)
with typical separations of _∼_ 50 AU. The frequency of stellar multiplicity strongly depends on stellar
mass. Stars more massive than the Sun have a higher fraction of multiplicity, and stars less massive
than the Sun have a lower degree of multiplicity; see Duchˆene & Kraus (2013) for a recent review.
Thus, it is clear that multiple star formation is a common outcome of star formation at all masses,
and a comprehensive understanding of the star formation process must also account for multiplicity.
There are two favored routes to explain the formation of multiple star systems: disk fragmentation
due to gravitational instability (Adams et al. 1989; Bonnell & Bate 1994; Stamatellos & Whitworth
2009; Kratter et al. 2010) and turbulent fragmentation of the molecular cloud (Padoan & Nordlund
2002; Offner et al. 2010). Disk fragmentation will preferentially result in the formation of close
( _<_ 600 AU) multiple star systems and requires the existence of a rotationally-supported disk around
the primary star. Turbulent fragmentation can result in the formation of both wide and close multiple
systems. The initial protostars form with separations _∼_ 1000 AU (or larger), and depending on their
relative motions and masses they can migrate closer together, remain at wide separations, or drift
further apart (Offner et al. 2010; Sadavoy & Stahler 2017). Previously, it was also thought that
envelope rotation could play a role in binary/multiple formation (e.g., Burkert & Bodenheimer 1993),
but this is no longer favored given the lack of ordered rotation for most star forming cores (Tobin
et al. 2011; Storm et al. 2014; Fern´andez-L´opez et al. 2014) and the apparently random orientations
of angular momenta (traced by outflow directions) for the wide companion protostars (Lee et al.
2016). A key prediction of turbulent fragmentation is that the seeds for multiplicity are produced in
the pre-stellar phase. Early ALMA survey results suggest tentative agreement with these predictions
(Pineda et al. 2015; Dunham et al. 2016; Kirk et al. 2017), but better statistics are still needed.
Despite the excellent statistics offered by studying field stars, the properties of field star multiples
cannot alone reveal the origin of multiplicity. This is because these systems are observed in the present
epoch and represent the culmination of Myr to Gyr of dynamical evolution, and to understand the
origin of multiplicity, it must be characterized during or shortly after the onset of star formation
during the protostellar phase.
Therefore, to gain a more clear picture of multiple star formation, protostars in the earliest phase
of the star formation process, known as the Class 0 phase (Andr´e et al. 1993), must be observed.
During this phase the forming protostar is enshrouded in a dense, infalling envelope of gas and
dust. The high levels of obscuration, however, made searching for multiplicity toward the Class
0 protostars difficult in the infrared, especially at scales less than 1000 AU. Thus, centimeter and
millimeter interferometry were necessary to examine the formation of such systems. Early searches
detected a number of wide multiple systems ( _>_ 600 AU) and a few close ( _<_ 600 AU) multiple systems
(Looney et al. 2000; Rodr´ıguez et al. 1998; Brown et al. 2000). Later surveys aimed to improve
upon the statistics, and Chen et al. (2013) characterized a number of wide systems in the Class 0
phase, finding that most (67%) Class 0 protostars may begin their lives as part of a wide multiple
system. Maury et al. (2010); Tobin et al. (2013, 2015a) aimed to expand the characterization of close
multiples, but samples were still too small to provide statistically significant results.

ALMA Perseus Multiplicity 3


Several efforts were also made to characterize multiplicity in the late protostellar phase (Connelley
et al. 2008; Duchˆene et al. 2007), the so-called Class I protostars (Dunham et al. 2014). However, even
these systems may be too evolved to retain signatures of their formation mechanism given that enough
enshrouding material has been accreted/dispersed to enable their detection in the near-infrared.
The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey (Tobin et al. 2015b, 2016b;
Segura-Cox et al. 2016) unlocked the distribution of protostellar multiples on scales less than 600 AU
(down to _∼_ 20 AU), thereby sampling the peak of the field solar-type separation distribution. This
survey conducted with the NSF’s Karl G. Jansky Very Large Array (VLA) observed all known Class 0
and Class I protostars in the Perseus star forming region, 37 of which are Class 0 protostars (FHSCs
and VeLLOs included), 8 are Class 0/I protostars, and 37 are Class I protostars (flat spectrum
included) (Tobin et al. 2016b). In addition, 12 Class II sources (pre-main sequence stars with disks)
that were bright in the far-infrared were also observed. We adopt a distance of 300 pc as an average
distance for the Perseus molecular cloud (Ortiz-Le´on et al. 2018). There may be a distance gradient
across the cloud (Ortiz-Le´on et al. 2018; Zucker et al. 2018) with the eastern part of the cloud
(IC348) at _∼_ 320 pc, the central part (NGC 1333) at _∼_ 293 pc, and the western part (L1448 and
L1451) at _∼_ 280 pc, but 300 pc is adopted for simplicity because these distances are consistent with
each other when considering the uncertainties of the current Gaia measurements. We note that these
revised distances are in disagreement with the maser parallaxes from Hirota et al. (2008, 2011) which
indicated _∼_ 230 pc. This 230 pc distance was used in Tobin et al. (2016b,a) to determine physical
separations and convert continuum flux density to mass. From this sample, 18 systems were identified
as multiple with companion separations less than 600 AU, and 16 of these were new detections by
the VANDAM survey.
The VANDAM survey greatly increased the detection statistics for protostars on scales less than
600 AU, but the formation mechanism(s) of the multiple systems was difficult to quantify because
the VLA survey was continuum-only. Tobin et al. (2016b) argued that the systems with separations
beyond _∼_ 500 AU most likely formed from turbulent fragmentation (Offner et al. 2016); this conclusion
was further supported by observations of outflow directions by Lee et al. (2016). For the close
multiples detected, disk fragmentation was argued to be the most likely formation mechanism for
17 out of the 18 [1] based on their proximity, circumbinary material around some sources, and the
double-peaked nature of the separation distribution. Nevertheless, it remains a possibility that the
close multiple systems initially formed at wide separations and migrated inward (Offner et al. 2010;
Sadavoy & Stahler 2017). However, definitive evidence in favor of disk fragmentation would be finding
them embedded within a common, circumbinary/multiple structure that has Keplerian rotation. To
search for the presence or lack of such a signature, we observed the sample of 17 (out of 18) close
multiple sources in Perseus with the Atacama Large Millimeter/submillimeter Array (ALMA); an
additional close multiple system (IRAS 03282+3035/Per-emb-5) was discovered after the program
was accepted. ALMA enables simultaneous observation of both dust continuum to look for circummultiple structure and molecular lines to search for rotation signatures in the surrounding gas (e.g.,
Takakuwa et al. 2014, 2015; Tobin et al. 2016a).
The results presented here reveal the circum-multiple environment around each close system, such
as whether or not there is rotation at small-scales and the presence or absence of surrounding material.


1 Only one close companion in the VANDAM sample (NGC 1333 IRAS2A/Per-emb-27) had clearly misaligned
outflows, indicating that formation within a circumbinary disk is unlikely (Tobin et al. 2015b).

4 Tobin et al.


This paper is structured as follows: we discuss the observations and data reduction in Section 2, the
results from dust continuum observations and molecular line mapping in Section 3, the implications
of the observations in Section 4, and present our conclusions in Section 5.


2. OBSERVATIONS AND DATA REDUCTION


The Perseus multiple systems were observed with the ALMA during Cycle 2 on 27 September 2015
with 33 antennas operating and sampling baselines between 32 - 2000 meters. The observations
were executed within a 1.8 hour block and the total time spent on each source was _∼_ 2.9 minutes.
The precipitable water vapor was _∼_ 0.7 mm throughout the observing session. The phase calibrator
was J0319+4130 (3C84), the bandpass calibrator was J0237+2848, and the amplitude and absolute
flux calibrator was the monitored quasar J0238+166. The absolute flux calibration accuracy is
expected to be better than 10%; however, we do not include this uncertainty in our calculations
and utilize statistical uncertainties throughout the paper. The correlator was configured to observe
a 2 GHz continuum band centered at 232.5 GHz and observed in TDM mode with 128 channels.
The three other basebands were allocated to 60 MHz windows with 1960 channels (0.083 km s _[−]_ [1]

velocity resolution) each and centered on the following molecular transitions: 12 CO ( _J_ = 2 _→_ 1),
13 CO ( _J_ = 2 _→_ 1), C 18 O ( _J_ = 2 _→_ 1), SO ( _J_ _N_ = 6 5 _→_ 5 4 ), and H 2 CO ( _J_ = 3 03 _→_ 2 02 ).
The raw visibility data were manually reduced by the North American ARC staff using CASA
version 4.5.0, and we additionally performed self-calibration on the continuum data to increase the
signal to noise ratio. When possible, we performed 2 rounds of phase self-calibration, first with
solution intervals that encompassed the length of an entire on-source scan, then the second round
utilized either 12.1 or 6.05 second solution intervals. The shortest possible solution interval was
6.05 seconds, corresponding to the length of a single integration. Following phase self-calibration,
we performed amplitude self-calibration using the solution normalization option, which normalizes
the amplitude solutions to around the factor 1.0 such that the flux density scaling is not altered.
Following the completion of self-calibration on the continuum, the solutions were also applied to the
spectral line bands. Self-calibration was possible for 16 out of 17 fields observed, only Per-emb-48
could not be self-calibrated due to insufficient S/N. The resultant noise in the 1.3 mm continuum was
_∼_ 0.14 mJy beam _[−]_ [1] and _∼_ 15 mJy beam _[−]_ [1] in 0.25 km s _[−]_ [1] channels for the spectral line observations.
The non-self-calibrated continuum images had a noise level of _∼_ 1 mJy beam _[−]_ [1] .
The data were imaged using the _clean_ task within CASA 4.5.0; the ALMA images shown in Figures
1 and 2 for each target were generated using Briggs weighting with a robust parameter of 0.5.
Within the _clean_ task, we only include data at _uv_ -distances _>_ 50 k _λ_ to mitigate striping in the
images from large-scale emission detected on the shortest baseline that could not be properly imaged.
The [13] CO ( _J_ = 2 _→_ 1) and C [18] O ( _J_ = 2 _→_ 1) images were generated with Natural weighting,
tapering at 500 k _λ_, and also only using the data having _uv_ -distances _>_ 50 k _λ_ . Tapering reduces
the weight of longer baseline data in the deconvolution to facilitate the detection of larger, lower
surface brightness structures. The typical beam sizes of the continuum and molecular line images
are 0 _[′′]_ _._ 27 _×_ 0 _[′′]_ _._ 16 (81 AU _×_ 48 AU) and 0 _[′′]_ _._ 35 _×_ 0 _[′′]_ _._ 25 (108 AU _×_ 76 AU), respectively.
We note that the phase was very unstable during the course of our observations, and the phase
calibrator (J0319+4130) was at _∼_ 10 _[◦]_ lower elevation than our science targets. As such, there are
systematic position offsets in each field up to _∼_ 0 _[′′]_ _._ 1. Thus, the most precisely measured positions for
the observed protostars in Perseus are those listed in Tobin et al. (2016b) from the VLA, despite the
higher S/N offered by the ALMA observations.

ALMA Perseus Multiplicity 5


2.1. _Data_ _Analysis_


With the observed sample of protostellar multiple systems, one of the key observables is the flux
density of the resolved sources and that of the surrounding extended structure. We measured the flux
densities toward the binary and wide companion systems that fell within the primary beam using
Gaussian fitting. First, we fit Gaussians to all compact, individual components that were resolved
and/or marginally resolved in the data. The Gaussians were fit using the _imfit_ task of CASA 4.7.2.
The integrated flux densities and uncertainties, source positions, and Gaussian parameters from _imfit_
are given in Table 1. Some sources have clear non-Gaussian, extended components. In these cases, we
used _casaviewer_ to draw a polygon region encompassing all the extended emission from the sources
(out to _∼_ 2 _[′′]_, where we still recover all flux) and measure the flux density within the polygon; this value
is given as Extended Flux in Table 1. For binary systems, there were many cases where the extended
flux was greater than the combined flux densities of the Gaussian fits to the compact sources. This
indicates that there is a significant amount of emission in extended, non-Gaussian components.
For the observed molecular lines, we made moment maps over the selected channel ranges where
there is spectral line emission. These images are used to assess whether or not there is rotation
around a particular multiple system and if there is an outflow.


3. RESULTS


3.1. _Dust_ _Continuum_ _Imaging_


We detect a wide variety of structures toward the sample of 17 multiple protostar systems observed
by ALMA. The dust continuum images of the Class 0 systems are shown in Figure 1 and the Class
I systems in Figure 2. The ALMA observations had high enough angular resolution to resolve the
companions in 15 out of the 17 systems. The systems with unresolved companions are Per-emb2 and Per-emb-18, which have separations of 0 _[′′]_ _._ 08 ( _∼_ 24 AU). For the 15 systems with resolvable
companions, we detected all known components in 12. The companions were not clearly detected
for Per-emb-40, Per-emb-55, and Per-emb-48. However, toward Per-emb-55, there is emission at the
expected companion position at the 2 _σ_ level, and for Per-emb-40 there is extended emission toward
the companion position that might reflect emission from the companion. Per-emb-48 was among the
faintest sources detected by ALMA and self-calibration was not possible for this field. The increased
noise from phase decorrelation may have prevented the companion from being detected, but we
cannot rule-out that its flux density is below our detection limit.
The Class 0 systems all have some extended emission surrounding the companions. This is demonstrated quantitatively in Table 1, where the total extended flux density (the sum of compact and
extended emission) is greater than the flux density from the compact sources. Per-emb-2, Per-emb-18,
Per-emb-17, L1448 IRS3B, SVS13A, L1448 IRS3C, and L1448 IRS2 all have clear emission surrounding and/or bridging the companion sources. The degree to which the total flux density is greater
varies, sometimes the difference is as small as a few percent (e.g., Per-emb-17), but it can be greater
than a factor of two (e.g., Per-emb-33). This emission could be described as a circumbinary disk
and/or envelope.
The extended structure surrounding the companions is quite prominent in L1448 IRS3B, SVS13A,
Per-emb-18, and Per-emb-2. The extended emission can be described as either spirals or streamers
toward L1448 IRS3B, SVS13A, and Per-emb-2 (Figure 1). The spirals in L1448 IRS3B were previously
reported in Tobin et al. (2016a). Finally, the extended structures surrounding Per-emb-2 and Per

6 Tobin et al.


emb-18 show evidence of being optically thick at 1.3 mm as evidenced by their emission peaks not
being located toward what are assumed protostar positions, but off source, and having smooth surface
brightness profiles across their central regions. In all these sources, the VLA imaging in Tobin et al.
(2016b) detects the peak emission toward what are assumed to be the positions of the individual
protostars, and the ALMA imaging with higher surface brightness sensitivity is able to detect much
more extended dust emission than detected by the VLA. Furthermore, the brightest feature in Peremb-18 is offset to the east; this was a weakly detected feature at 9 mm with the VLA (Tobin et al.
2016b).
Finally, there is less-prominent extended emission toward NGC1333 IRAS2A and L1448 IRS2.
NGC1333 IRAS2A has extended features at low surface brightness, and asymmetric extended emission to the east. Then the extended emission for L1448 IRS2 is also more diffuse and does not have
as well-defined circumbinary structure like some of the others. However, the larger structure surrounding the protostars may be impacted by spatial filtering given that Tobin et al. (2015a) detected
a surrounding structure on larger scales in lower resolution data.
The Class I sources on the whole have little or no extended emission surrounding the components
of these multiple systems. The images show this visually in Figure 2, and Table 1 shows that the
flux densities for the Gaussian fits and the extended emission from a larger area encompassing the
two protostars are comparable. However, some show resolved structure toward one component. Both
NGC 1333 IRAS2B and L1448 IRS1 have at least one component that is dominant, with resolved
structure in their dust emission. The other Class I binaries appear consistent with point sources, and
the components have similar flux densities.
While the close companions were the primary targets, we detected several wide companions in the
observed fields. In the field of SVS13A, we detect several additional sources. One source is RAC1999
VLA20 (Rodr´ıguez et al. 1999), located northeast of SVS13A. This source was previously detected
by the VLA, but has no counterpart at shorter wavelengths (i.e., mid-infrared and far-infrared) and
has been hypothesized to be extragalactic (Tobin et al. 2016b), see Figure 3. The wider companion
to SVS13A, often called VLA3 or SVS13A2, is detected (Figure 3), and appears marginally resolved.
SVS13B is also detected and resolved as shown in Figure 3). VLA 8 mm imaging of SVS13B indicated
that it has a small embedded disk (Segura-Cox et al. 2016), but a larger, resolved structure is detected
in the ALMA 1.3 mm data. We also detected L1448 IRS3A in the field of L1448 IRS3B (Figure 4).
The small-scale structure of L1448 IRS3A appears to be a resolved disk (Figure 4), consistent with
the resolved emission detected in Tobin et al. (2015a). In the field of Per-emb-55 (Figure 5), we
also detected Per-emb-8 which appears to have a large extended disk surrounding it (Figure 5).
Per-emb-21 was detected in the field of Per-emb-18, but appears unresolved (Figure 6).
The resolved structures around Per-emb-8 and L1448 IRS3A were not ideal for fitting a single
Gaussian, so we fit two Gaussians to these sources and list the inner and outer Gaussian fits separately,
referring to them as Inner Disk and Outer Disk, in addition to the fit of a single Gaussian in Tables
1 and 2.


3.2. _Mass_ _Estimates_ _from_ _Dust_ _Continuum_


The mass of material found toward individual components of the multiple systems, as well as
surrounding all components, can be estimated using the flux density of the dust continuum emission.
Under the assumption that the dust emission is optically thin and isothermal, the dust mass can be

calculated with the equation



ALMA Perseus Multiplicity 7


_D_ [2] _F_ _ν_
_M_ _dust_ = (1)
_κ_ _ν_ _B_ _ν_ ( _T_ _dust_ ) _[,]_



where _D_ is the distance ( _∼_ 300 pc), _F_ _ν_ is the observed flux density, _B_ _ν_ is the Planck function, _T_ _dust_
is the dust temperature, and _κ_ _ν_ is the dust opacity at the observed wavelength. _T_ _dust_ is assumed to
be 30 K, consistent with temperature estimates on _∼_ 100 AU scales (Whitney et al. 2003) and _κ_ _ν_ is
0.899, taken from Ossenkopf & Henning (1994), Table 1 column 5. We then multiply the resulting
value of M _dust_ by 100, assuming the canonical dust to gas mass ratio of 1:100 (Bohlin et al. 1978).
We caution that the masses calculated may have systematic uncertainty because opacity will hide
some mass, the dust emission is not isothermal and the dust opacity along with the dust to gas mass
ratio are uncertain and may vary between components within the same system.
The results from the mass calculations are given in Table 2. A number of sources have total masses
greater than 0.1 M _⊙_ . The mass calculations presented here tend to be about 20% higher than the
masses reported for some of the same sources in Tobin et al. (2015a) from observations with CARMA
(taking into account the different distances adopted), despite observing at the same wavelength,
slightly lower resolution (for CARMA), and making the same assumptions for the mass calculation.
The minor discrepancy likely results from a combination of greater absolute flux uncertainty in the
CARMA data, better sensitivity to low-surface brightness emission from ALMA, better uv-coverage
with ALMA, and less decoherence in the self-calibrated ALMA data.
Most of the close companions have large flux density ratios between them, which could be interpreted as a large circumstellar mass ratio; this ratio offers no information as to the mass ratio between
the stellar components and only reflects the compact circumstellar mass. Per-emb-17, EDJ2009-269,
and Per-emb-35 have ratios closest to unity, and L1448 IRS1, L1448 NW, Per-emb-12, Per-emb-22,
Per-emb-27, Per-emb-33, Per-emb-36, Per-emb-40, Per-emb-44, Per-emb-49, and Per-emb-55 all have
circumstellar mass ratios that are less than 0.63. Both Class 0 and Class I systems span a range
of circumstellar mass ratios. We note that several cases with large circumstellar mass ratios are in
hierarchical and/or higher order systems.


3.3. _Spectral_ _Indices_


Because most of the companions are well-enough resolved to enable their 1.3 mm flux densities to
be measured individually, We were able to calculate the spectral index of the emission from 1.3 mm
to 9.1 mm. We calculated the spectral index ( _α_ ) using the equation


_α_ = _[ln]_ [(] _[F]_ _[ν][,]_ [1] _[.]_ [3] _[mm]_ [)] _[ −]_ _[ln]_ [(] _[F]_ _[ν][,]_ [9] _[.]_ [1] _[mm]_ [)] (2)

_ln_ ( _ν_ 1 _._ 3 _mm_ ) _−_ _ln_ ( _ν_ 9 _._ 1 _mm_ )


and the associated uncertainty using the equation



1
_σ_ _α_ [2] [=]
� _ln_ ( _ν_ 1 _._ 3 _mm_ ) _−_ _ln_ ( _ν_ 9 _._ 1 _mm_ )



2 2
_σ_ _ν,_ 1 _._ 3 _mm_ _ν,_ 9 _._ 1 _mm_
+ _[σ]_ [2]
� � _F_ _ν,_ [2] 1 _._ 3 _mm_ _F_ _ν,_ [2] 9 _._ 1 _mm_



(3)
�



following Chiang et al. (2012). We use the 9.1 mm flux densities from Tychoniec et al. (2018b) to
calculate _α_ with respect to the flux densities at 1.3 mm. Because Tychoniec et al. (2018b) attempted
to remove the free-free emission that can contribute to the 9.1 mm flux densities, we calculated _α_
with respect to both the corrected and uncorrected 9.1 mm flux densities. The spectral indices for

8 Tobin et al.


the sources are given in Table 1. The statistical uncertainty on _α_ is generally quite small _∼_ 0.1 due
to the large different in wavelength between the two bands. We do assume a 10% uncertainty in the
flux calibration for each flux density and add this in quadrature to the statistical uncertainty on the
flux density. The uncertainty on _α_ is generally smaller than the range of _α_ from the corrected and
uncorrected flux densities.
Most of the values for _α_ are between 2 and 3; optically thin thermal dust emission, where the
dust opacity spectral index _κ_ _ν_ _∝_ _ν_ _[β]_, is expected to have _α_ = 2+ _β_ . Thus, for thermal dust emission
alone (optically thin or partially optically thin), the spectral indices should be _≥_ 2; the spectral index
would be 2 for optically thick emission. Most of the values of _α_ are _>_ 2 even when the 9.1 mm
emission was not corrected for free-free emission, thus it is likely that the 9.1 mm mostly reflects dust
emission as also found by Tychoniec et al. (2018b). There are some sources for which _α_ _∼_ 2, this
could indicate that either the properties of the dust grains are such that _β_ is quite small, the dust
emission is becoming optically thick, or there is a some amount of free-free emission to the 9.1 mm
flux density that could not be removed. These three possibilities are difficult to disentangle with
the data in-hand, limiting the possible interpretations of these spectral index data. Therefore, the
1.3 mm emission presented here is most likely to _only_ reflect dust emission while the 9.1 mm emission
might reflect dust and free-free emission.


3.4. _Molecular_ _Line_ _Kinematics_


The dust continuum emission provides crucial evidence of the presence or absence of material
surrounding the close binary/multiple stars, which will help with the interpretation of their formation
mechanism. However, the continuum data alone are not enough to fully understand how these
multiple systems formed. Therefore, we also observed five molecular tracers toward each system
along with the dust continuum. We expect that C [18] O will generally trace the kinematics of the dense
circum-multiple material because this line has tended to be the most reliable tracer of protostellar
disks (Ohashi et al. 2014; Yen et al. 2014; Aso et al. 2015). Also, [13] CO should generally trace the
circum-multiple material depending (Takakuwa et al. 2012; Tobin et al. 2012), but we use [13] CO with
caution given that it can also trace outflowing gas. H 2 CO is also expected to trace the circum-multiple
environment because this is a typical high-density tracer (e.g., Mangum & Wootten 1993), and it
has been found to trace the Class 0 disk and inner envelope of L1527 (Sakai et al. 2014). Similarly,
SO has also been found to trace the disk toward some protostars (Sakai et al. 2014; Yen et al. 2014).
However, there are instances where both H 2 CO and SO have been shown to trace outflowing material,
in addition to circumstellar/multiple material (e.g., Wakelam et al. 2005). Finally, [12] CO is expected
to trace the outflow toward most protostars in the sample given their youth, but [12] CO could trace
the disk kinematics of some of the more evolved multiple systems in our sample (e.g., Simon et al.
2000). The figures showing the molecular line detections toward circum-multiple and circumstellar
structures are shown in Figures 7 to 22. The intervals over which the red and blue shifted emission
are integrated are given in Table 3.
Due to the short observations toward each source, the S/N is not very high in each channel for
these high-angular resolution spectral line maps. Thus, we examine the integrated intensity maps
constructed for emission red- and blue-shifted with respect to the line center. The detection rates
for the lines vary from source to source, some only have one line detected, whereas others have
detections in all five lines. We examine the integrated intensity maps of each molecule, relative to
the outflow directions and the extended continuum structure. The larger-scale outflows have previous

ALMA Perseus Multiplicity 9


characterization of their orientations, when possible, from Stephens et al. (2017), therefore we only
show the outflow maps in Appendix A.


3.4.1. _Characterization_ _of_ _Kinematics_ _in_ _Multiples_


We use the red- and blue-shifted integrated intensity maps of each molecule to determine whether
or not the velocity patterns observed toward the multiple systems reflect rotation, outflow, or an
indistinct process. We do this by comparing the orientation of the velocity gradient relative to
the outflow direction (and extended continuum if possible). If there is a velocity gradient in the
circum-multiple structure, that is within 30 _[◦]_ of orthogonal to the outflow direction, we classify it as
being consistent with disk rotation. To quantify the relative orientations of the outflow and velocity
gradient directions, we measure the position angle of the outflow and velocity gradient and then take
the difference. These values are tabulated in Table 4. To measure the outflow position angle, we draw
a line bisecting the outflow and measure its position angle. We follow the same procedure for the
velocity gradients, but measure this from the emission peaks in the blue- and red-shifted integrated
intensity maps tracing rotation, generally C [18] O. The position angles do have uncertainty and we
estimate that this is _±_ 10 _[◦]_ .
Molecular line emission is detected with sufficiently high S/N in 12 systems to characterize the
kinematics as rotation or not. This classification is most firm for the 9 Class 0 systems with the
strongest detections and seven of these Class 0 systems have velocity gradients that indicate rotation
in the circum-multiple gas. If we include those with tentative classifications, we find that 8 out of 12
systems are consistent with the circum-multiple emission tracing rotation orthogonal to the outflow
direction. The systems classified as indistinct generally have disorganized kinematic structure on the
scales and at the sensitivity we observed. Also, certain molecules may better trace different kinematic
components of protostellar systems (Sakai et al. 2014, e.g.,). The detection and characterization of
the molecular line data are summarized in Table 4. Each source is discussed in more detail in Section

4.1 with respect to the data presented in this paper and to interpret previous results in the context
of the new ALMA data.


3.4.2. _Detections_ _of_ _Individual_ _Rotating_ _Disks_


In addition to the kinematic structure of circum-multiple material, we were also able to examine
the kinematic structure of both some individual circumstellar disks either as part of a close multiple
system or as a wide companion. Per-emb-8 shows the clearest example of rotation in all observed
molecular lines; [12] CO interestingly shows a combination of rotation and outflow. L1448 IRS3A also
shows rotation in all molecular lines and is oriented orthogonal to the position angle of L1448 IRS3B.
The individual disks toward Per-emb-35-A and -B appear to have molecular line emission as well,
but the line emission is not well-resolved spatially. Only the H 2 CO appears to have a clear indication
of rotation. The characterization of the observed kinematics from all lines are given in Table 4.


4. DISCUSSION


The ALMA 1.3 mm continuum and molecular line emission observed toward the close multiple
systems in Perseus dramatically increases our knowledge of the spatial and kinematic structure of
dense gas on a few hundred AU scales around these multiple protostar systems. The ALMA dust
continuum traces more tenuous emission surrounding the companions as compared to the previous
VLA observations. While the extended emission is more diffuse than the compact sources detected

10 Tobin et al.


by both the VLA and ALMA, this emission can account for a significant fraction of the mass in
the systems. The molecular maps show the gas motion, revealing how well (or not) the motion of
the extended dense gas surrounding the protostar(s) is organized. The molecular line maps provide
evidence for rotation in several systems, but not universally, as some systems have unclear kinematic
structure with the current S/N of the ALMA data. Nevertheless, these ALMA data now enable us
to better interpret how multiple star systems form on a case-by-case basis and as an ensemble. We
consider each system individually and summarize our findings for the sample as a whole.


4.1. _Individual_ _Systems_

4.1.1. _Class_ _0_ _and_ _0/I_ _Systems_


–
**Per-emb-2** The continuum structure is extended with a very smooth surface brightness distribution, in contrast to the VLA data with a central intensity peak toward the protostars, forming a
binary system with a separation of _∼_ 24 AU. Only C [18] O and [13] CO were detected toward this system,
and we detect a clear velocity gradient orthogonal to the outflow direction, as shown in Figure 7.
The C [18] O emission is not fully coincident with the continuum image, possibly due to dust opacity
and/or spatial filtering of low-velocity emission near line-center. Nevertheless, the C [18] O and [13] CO
kinematics still exhibit evidence for rotation on the scale of the circumbinary continuum.
**Per-emb-12** – Also known as NGC 1333 IRAS4A, this system is the most massive overall in terms
of dust emission out to very large scales. It was also known to be a binary prior to the VANDAM
survey with a separation of _∼_ 549 AU (Looney et al. 2000). The dust emission toward IRAS4A
has significant opacity, which prevents tracing kinematics toward the protostars; only some emission
around the protostars in C [18] O and [13] CO is revealed in Figure 8.

–
**Per-emb-17** There were detections in multiple lines toward Per-emb-17, and the material surrounding the _∼_ 83 AU binary system forms a flattened structure in dust continuum that is similarly
flat in [13] CO and C [18] O. The molecular line emission exhibits velocity gradients orthogonal to the outflow direction, see Figure 9. The rotation center of the system is not clearly centered on a particular
component, so it is unclear which protostar is more massive. H 2 CO and SO, however, seem to be
more associated with the outflow in this source. SO in particular is strong toward the B component
and extended along the outflow.

–
**Per-emb-18** This source has a flattened structure in the dust continuum surrounding the companions separated by _∼_ 26 AU and detections in multiple lines. The continuum might be tracing dust
emission with high optical depth, given that the emission is not very peaked toward the main pair of
protostars. The [13] CO, C [18] O, SO, and H 2 CO trace velocity gradients orthogonal to the outflow direction, see Figure 10. The fact that all molecules have gradients in the same direction lends confidence
to interpreting the kinematics as rotation.
**Per-emb-22** – Also known as L1448 IRS2, this binary system has a separation of _∼_ 225 AU. Continuum emission was mainly detected toward individual components, with some emission in between,
exhibiting an apparent ‘bridge’ between them. The molecular lines have evidence of velocity gradients orthogonal to the outflow (Figure 11), but much of the molecular line emission appears to be
filtered out and/or have very low surface brightness. Tobin et al. (2015a) previously found evidence
for velocity gradients/rotation using combined CARMA and SMA data that had lower resolution, in
addition to a larger circumbinary structure.

ALMA Perseus Multiplicity 11


–
**Per-emb-27** Also known as NGC 1333 IRAS2A, this system does not have much material surrounding the _∼_ 186 AU binary, but there is some extended material associated with the brighter
source. There is weak evidence for a velocity gradient in C [18] O on scales larger than the binary system. SO is associated with the outflow, but H 2 CO is compact toward the brighter component with
a small extension toward the companion, see Figure 12.

–
**Per-emb-33/L1448** **IRS3B** This source was shown in Tobin et al. (2016a) to have clear velocity gradients associated with its extended circumbinary material in [13] CO, C [18] O and H 2 CO. The
separations of the companions from Per-emb-33-A are _∼_ 79 and _∼_ 238 AU. Despite being published
previously, we show this source for the sake of comparison to the full sample (Figure 13).
**L1448** **IRS3C** – The two companions in this system are separated by just _∼_ 75 AU, and they
appear blended in the image. However, the emission toward each component is measured using a two
component Gaussian fit. There is low-level dust continuum emission surrounding the two blended
protostars, and the circumbinary material also shows a velocity gradient in C [18] O orthogonal to the
outflow, see Figure 14.
**Per-emb-44** – Also known as SVS 13A, this binary system has a companion separation of _∼_ 90 AU
and is one of the most prominent protostars within NGC1333. The 1.3 mm continuum also shows
a 1-armed spiral pattern, almost as prominent as that of L1448 IRS3B. Both [13] CO and C [18] O are
detected toward this protostar and exhibit velocity gradients that are at least partially orthogonal
to the outflow, see Figure 15. This source might be viewed more face-on making rotation harder to
distinguish in this complex environment. The C [18] O emission also follows the spiral through multiple
velocity channels. Furthermore, both SO and H 2 CO are detected at smaller radii near the close
pair and may also show a velocity gradient, but it is uncertain due to blending. This protostar was
previously known to have a close companion (Anglada et al. 2004), and the original study indicated
that the disk around the western companion (Per-emb-44-B; VLA 4A) was not very prominent given
its low flux density relative to the eastern component (Per-emb-44-A; VLA 4B) at a wavelength of
7 mm. However, their masses (flux densities) differ by only a factor of 1.6 at 1.3 mm, which may
have more to do with either the amount of large grains and/or variable free-free emission because
Anglada et al. (2004) used data at a wavelength of 7 mm from the VLA. However, Tychoniec et al.
(2018c) also finds that the 9 mm flux densities (with estimated free-free contribution removed) have
a flux ratio of 2.8, and the spectral indices are quite different _∼_ 2.3 for the eastern component and

_∼_
3 for the western component. This could indicate more large grains in the eastern source to explain
the increased flux density, or the 1.3 mm is optically thick and the 8 mm emission is less opaque,
enabling more dust emission to be detected.


4.1.2. _Class_ _I_ _&_ _II_ _Systems_


–
**Per-emb-36** **(NGC** **1333** **IRAS2B)** The two sources detected toward Per-emb-36 are
marginally resolved in the ALMA 1.3 mm data with a separation of _∼_ 93 AU, and it has multiple detected emission lines (Figure 16). However, the line emission does not obviously trace velocity
gradients across the source, and the emission is mainly found west of the protostars rather than
around them.

**Per-emb-35** – These protostars are separated by _∼_ 572 AU, and they are the source of an Sshaped outflow detected by _Spitzer_ (Gutermuth et al. 2008). These sources do not have obvious dust
continuum surrounding the compact continuum sources, but we cannot rule-out diffuse circumbinary
emission below our detection limits. H 2 CO and SO are strongly detected toward both of the protostars

12 Tobin et al.


and may show evidence of velocity gradients orthogonal to their outflow directions (Figure 17).
Furthermore, there appears to be emission in these molecules between the two protostars. Both
protostars are driving outflows, and they appear parallel as observed in the plane of the sky. [13] CO
is detected toward both sources, but it is not obviously tracing rotation, and C [18] O is only weakly
detected, also see Figure 17.

–
**Per-emb-40** Only the primary component of this system is well-detected, but the companion
is tentatively detected. The molecules [13] CO and C [18] O are only weakly detected (Figure 18). [13] CO
does have blue- and red-shifted components, but not obviously tracing rotation.
**L1448** **IRS1** – This protostar appears to be the most evolved source in L1448, and it is detectable
at visible wavelengths. The separation of the two protostars is _∼_ 427 AU. Unlike the other protostellar
systems, the rotation in L1448 IRS1 is traced by [12] CO that is extended toward the companion, see
Figure 19. In this particular case, [12] CO, is not tracing outflowing emission but rather the disk
because of its advanced evolutionary state. We know this because the scattered light nebula from
this source (Foster & Goodman 2006), which is an alternative indicator of the outflow direction, is
oriented orthogonal to the velocity gradient in [12] CO.
**EDJ2009-269** – This system is a likely Class II binary in Perseus, separated by _∼_ 157 AU. Its
only detected emission line is [12] CO toward one of the protostars (Figure 20). In this more-evolved
system, the [12] CO also appears to trace kinematics of gas toward the individual circumstellar disks
rather than outflowing material.
**Per-emb-48,** **Per-emb-49,** **and** **Per-emb-55** – These protostars do not show strong evidence for
molecular line emission surrounding the companion stars, thus we cannot examine whether or not
there are velocity gradients in the circum-multiple emission. These are all Class I systems and may
simply have a much smaller reservoir of circumbinary material, and/or the molecular line emission
could not be detected with our uv-coverage and/or sensitivity. Per-emb-55, however, does appear to
have an outflow associated with it in [12] CO emission, see Appendix Figure 24.


4.1.3. _Wide_ _Companions_ _with_ _Disks_


**L1448** **IRS3A** – This is the wide companion to L1448 IRS3B, separated by 7 _[′′]_ _._ 3 ( _∼_ 2195 AU), and
has extended dust emission with disk-like morphology. The protostar exhibits a weak outflow in
12 CO, but rotation in all the other observed lines, see Figure 21.
**Per-emb-8** – This protostar is clearly detected with extended dust emission that shows signatures of
rotation from the molecular line emission (Figure 22). It is separated from Per-emb-55 by _∼_ 2867 AU.
Per-emb-8 was previously identified as a disk candidate by Segura-Cox et al. (2016), but with a very
different position angle than is observed with ALMA. Since this source appears to have strong,
extended free-free emission (Tychoniec et al. 2018a), the geometric parameters from the VLA data
may not solely trace the dusty disk.


4.2. _The_ _Origin_ _of_ _Close_ _Protostellar_ _Multiples_


The ALMA continuum and molecular line maps are key to determining the most likely origin of the
multiple star systems. Systems that have formed via disk fragmentation are expected to have circummultiple dust emission and this circum-multiple material should be rotating in an organized manner.
Furthermore, if fragmentation happened in a disk, the disk should be larger than the separation of
the companions. Systems that result from turbulent fragmentation have no such expectations for
their circum-multiple emission and may not have well-organized kinematics surrounding the system.

ALMA Perseus Multiplicity 13


We discuss our interpretation on the relative frequency of these mechanisms based on our ALMA

molecular line and continuum data.


4.2.1. _The_ _Likelihood_ _of_ _Disk_ _Fragmentation_


The ALMA observations of close multiple protostar systems reveal several features that were previously unclear from the VLA-only dataset. First, the continuum emission from extended circumbinary
(or triple) material is detected in 9 out of the 18 observed sources. The Class 0s and most deeply
embedded Class Is have the highest tendency for circum-multiple dust continuum. Furthermore, this
circum-multiple continuum emission is almost always extended orthogonal to the outflows (L1448
IRS3B, L1448 IRS3C, L1448 IRS2, Per-emb-12, Per-emb-17, Per-emb-18), barring a few cases that
appear to have inclinations that are nearly face-on (SVS13A, Per-emb-2). Second, the molecular line
emission detected toward these protostars and their circum-multiple disks strongly tends to have velocity gradients orthogonal to the outflow direction (Per-emb-2, L1448 IRS3B, L1448 IRS3C, L1448
IRS2, Per-emb-17, Per-emb-18, SVS13A, L1448 IRS1). The line emission is spatially coincident with
the circum-multiple dust emission (taking into account the possible dust opacity and spatial filtering
in some sources), and the velocity gradients orthogonal to the outflows on these scales are interpreted
as rotation because the mass of the protostar and its disk are dominant at these scales ( _<_ 500 AU)
and do not appear to be significantly confused with large-scale effects in the clouds.
Therefore, it is clear that for many of the youngest multiple systems we have circum-multiple dust
emission oriented in a manner that is consistent with a disk, and we detect molecular line kinematics
that are consistent with rotation on the same scale as the circum-multiple material. We detail the
molecular line detections and their likely kinematic origin for each source in Table 4. The observational results of rotating, circum-multiple gas align with the expectations for companion formation
via disk fragmentation. Direct evidence for the circum-multiple material in only the younger sources
makes sense, because as they evolve, the circum-multiple material is accreted rapidly (Bate 2018).
Thus, about 7 protostars in the sample appear to have recently undergone disk fragmentation (those
listed above with velocity gradients orthogonal to the outflow and extended circum-multiple mass).
Many of the Class I close systems without circum-multiple dust or gas may have formed earlier
and/or consumed/dispersed their surrounding mass. The widest systems that appear convincingly
consistent with disk fragmentation are Per-emb-22 (225 AU) and Per-emb-33 (79, 238 AU) and there
is circum-multiple continuum detected in both cases. L1448 IRS1 is possibly consistent with disk
fragmentation, but the companion is at a wider separation (427 AU) and the disk would have had to
be quite large initially to form the companion, unless there was a three-body interaction that moved
the companion to a larger orbit (Reipurth & Mikkola 2012). This would then require that L1448
IRS1-A has an unresolved companion.
These ALMA observations provide important evidence for the possibility of fragmentation via
gravitational instability in these systems. Additional follow-up with higher S/N will be required to
confirm that these apparent disks are rotationally supported and to determine the outer radius of the
Keplerian disk, ensuring that it encompasses the companion. The short observations presented here
do not have the S/N to robustly fit a rotation curve that can distinguish Keplerian rotation from
other velocity profiles. Therefore, at this point, we can conclude that there is evidence in favor of
these systems forming via fragmentation in a gravitationally unstable disk, like L1448 IRS3B. There
is rotation, circum-multiple dust, and the companions are most often orthogonal to the outflow and
within the circum-multiple material.

14 Tobin et al.


4.2.2. _Evidence_ _for_ _Turbulent_ _Fragmentation_ _in_ _Some_ _Systems_


There are a few systems where disk fragmentation is not obviously consistent with the observations
and turbulent fragmentation is more likely (i.e., Per-emb-27; Tobin et al. 2015b). Per-emb-27 in
particular has some evidence for a velocity gradient in C [18] O but not in other tracers. H 2 CO in fact
appears very centrally peaked toward Per-emb-27-A and may be tracing the hot corino (e.g., Taquet
et al. 2015). Furthermore, the disk toward Per-emb-27-A appears to be very small, _∼_ 10 AU in radius
(Segura-Cox et al. 2018). Thus, Per-emb-27 seems unlikely to have any characteristics that make
disk fragmentation a likely possibility for this system.
The source Per-emb-12 (NGC 1333 IRAS4A) is borderline for consideration as a close companion
with its _∼_ 549 AU separation. We see a significant amount of material surrounding the two sources,
but this is not clearly organized as a disk and is perhaps more likely a circumbinary envelope. The
outflows from these two sources are roughly aligned, indicating that envelope rotation could have
played a role in their formation, but the kinematics are unclear because the line emission is so complex
due to the high opacity and spatial filtering that we cannot clearly say if there is organized rotation
or if the inner envelope kinematics appear random.
The source Per-emb-36 (NGC 1333 IRAS2B) has extended gas emission surrounding it, but not
obvious circum-multiple dust emission. Some of the gas appears off to one side and the companion
is located toward the western side where much of the gas emission tends to originate. The kinematic
structure of this system is unclear and the outflow is quite wide (Plunkett et al. 2013). Thus,
we cannot firmly put this binary system in either category. Given that Per-emb-36 is a Class I
protostar, it is possible that much of the original gas has been accreted and there is no longer a
prominent circum-multiple disk. This could be a case of turbulent fragmentation, but it is hard to
be more definitive with the more-evolved state of Per-emb-36.
Per-emb-35 is another case that is not obviously disk fragmentation given its wide separation
of 572 AU. However, unlike Per-emb-12, it is much less embedded and the continuum emission is
dominated by the compact circumstellar components that may exhibit rotation in some molecular
species (Figure 17). While there is not much evidence for circumbinary material, the outflows (and
possibly rotation axes traced by molecular lines) appear roughly parallel. Furthermore, the outflows
are inclined in the same direction with respect to the plane of the sky. This case is also not obviously
turbulent fragmentation or disk fragmentation. On the other hand the fragmentation mechanism in
this system could be related to the overall rotation of the envelope (e.g., Burkert & Bodenheimer
1993), despite this mechanism not being favored. However, turbulent fragmentation does not rule-out
some outflows being parallel, just that the distribution over a larger sample should be random.


4.2.3. _Which_ _is_ _the_ _Most_ _Common_ _Mechanism?_


In total, we can make reasonably strong statements about the formation mechanisms for 9 out of
the 17 protostars in our sample based on the extended dust emission and gas kinematics. Seven out
of the 9 (Per-emb-2, L1448 IRS3B, L1448 IRS3C, L1448 IRS2, Per-emb-17, Per-emb-18, SVS13A)
appear to be consistent with fragmentation of a gravitationally unstable disk given their observed
morphologies and velocity gradients. There are only two systems (Per-emb-12, Per-emb-27) for which
we can state with reasonable confidence that they are inconsistent with disk fragmentation and that
turbulent fragmentation is more likely. With the caveats of having a large separation and only a hint
of rotation in [12] CO we could add L1448 IRS1 to the disk fragmentation group. Then Per-emb-36 and

ALMA Perseus Multiplicity 15


Per-emb-35 could also be added to the turbulent fragmentation group, bringing the total to 8 systems
likely forming via disk fragmentation to 4 systems likely forming via turbulent fragmentation. The
raw numbers indicate that for multiples on scales _<_ 600 AU, _∼_ 67% form via disk fragmentation and
_∼_ 33% form via turbulent fragmentation. If we only consider systems with _<_ 300 AU separations, more
in line the sizes of disks, then there are a total of 10 systems with only 2 systems inconsistent with
disk fragmentation. The smaller separations systems, further indicates that the closer systems may
be more frequently formed via disk fragmentation. However, these percentages obviously represent
small number statistics making, prohibiting us from making a strong, general conclusion on the
typical origin of close multiple systems.
A dominant contribution from turbulent fragmentation would not necessarily result in the presence
of circumbinary disks within which the companions are embedded, and outflows would not tend to
appear aligned orthogonal to the companion position angles and/or velocity gradients.
There is not currently a clear prediction for the relative fractions from theory/simulations. Offner
et al. (2010) indicate that most close companions should result from turbulent fragmentation because
radiative heating of the protostellar disk should suppress fragmentation. On the other hand, the
simulations from Bate (2018) include radiative feedback and do find disk fragmentation, but a study
of the relative population of companions in different ranges of separations has not been conducted.
However, it should be noted that Offner et al. (2010) and Bate (2012) employ different initial cloud
conditions (turbulence and volume density) and different assumptions for the radiative heating. Both
of these factors are likely to influence the fragmentation on cloud and disk scales in both simulations.
Even in the presence of radiative heating, fragmentation can still occur for systems with total masses
(star+disk) of _>_ 1 M _⊙_ (Kratter et al. 2008, 2010). The Offner et al. (2010) simulations may be
underpredicted disk fragmentation because most of the systems in that simulation were _<_ 1 M _⊙_, and
the different treatment of radiative heating in Bate (2012, 2018) could overpredict fragmentation in
this mass range.
While we suggest that our results favor disk fragmentation as a formation mechanism for these
systems, there is an inescapable caveat. Even if the disks are Keplerian, there remains the possibility
that initially widely separated companions could have migrated closer together (Offner et al. 2010;
Sadavoy & Stahler 2017). In the process, the original disks may have been destroyed and a new disk
reformed around the companions in the same orbital plane. While the outflows could be misaligned
initially (Offner et al. 2016), they could be brought into alignment and appear as a single outflow
as the protostars accrete from the disk surrounding them. However, there is not evidence for past
multiple outflows in different directions for the systems where we would have the possibility of
determining this. But, the timescales over which we could detect remnant outflows might be too
short. Further study of circum-multiple material surrounding systems formed via initially turbulent
fragmentation may provide clues to more uniquely distinguish between primordial disk fragmentation
and turbulent fragmentation with a re-formed disk. Therefore, our main result finding that 8 out of
12 sources are consistent with disk fragmentation could be rephrased to say that 66% is an upper
limit on the frequency disk fragmentation for the production of close multiples.


4.3. _Non-detections_ _of_ _Companions_


In our ALMA follow-up of the VLA-detected close multiples, we detect the companions in 12 out
of 15 multiple systems that we were able to resolve. We left Per-emb-2 and Per-emb-18 out of these
numbers because it is not possible to resolve their companions in these observations. All Class 0

16 Tobin et al.


companions are detected, and only the Class I companions have some non-detections. However, in
the case of the non-detections, we do marginally detect one of the components in Per-emb-40, Peremb-55 has a tentative detection toward the companion position. Finally, Per-emb-48 could also not
be self-calibrated, reducing its likelihood to detect the companion.
The fact that most of the non-detections were more-evolved Class I systems makes sense given that
the VLA is detecting a combination of dust and free-free emission in most cases. The non-detected
component of Per-emb-48 was Per-emb-48-B; Tychoniec et al. (2018) detected Per-emb-48-B with
a declining spectral index from 6.4 cm to 8 mm, consistent with gyro-synchrotron from a stellar
corona. Per-emb-55-B, the very tentative detection, had a spectral index that was rising (0.9) but
more flat than expected from dust emission alone ( _≥_ 2). Assuming a spectral index of 3 (implicitly
assumes a dust opacity spectral index of 1), we extrapolate the 9 mm flux density of 0.07 mJy to
1.3 mm. In order to have a flux density consistent with the observations, a flux density of less than
1 mJy, _∼_ 95% of the 9 mm emission from Per-emb-55-B must be from free-free emission. Tychoniec
et al. (2018b) found that 79% of the 9 mm emission was from free-free emission, this would also
point to the spectral index of the source emission being shallower than 3. Per-emb-40-B was quite
faint and also appeared to have a declining spectral index in 8 mm to 1 cm; the 4.1 cm and 6.4 cm
were much fainter than expected, possibly due to source variability (e.g., Dzib et al. 2013). However,
Per-emb-40-B has extended dust toward it, so it is probably real, but not detected at our level of
sensitivity.
The faintness of companions toward some of these close Class I protostars is consistent with the
results of Harris et al. (2012). While that study examined Class II stellar systems, they found that
the systems with close separations ( _<_ 300 AU) had a factor of 5 lower millimeter emission compared
to single systems and systems with _>_ 300 AU separations. Moreover, the primary was always brighter
than the secondary in the cases where both components of the system were detected at millimeter
wavelengths. Thus, evolution may drive the companion(s) to be significantly fainter than the primary,
and the flux density of close ( _<_ 300 AU) systems to be lower than more widely separated and/or single
systems.
It is also worth discussing the cases of some other companion sources reported toward protostars
in Perseus. A possible new companion source was reported near Per-emb-12 (NGC 1333 IRAS4A),
referred to as A3 in Santangelo et al. (2015), with a 1.3 mm flux density of 187 mJy. This source
A3 is not detected with the VLA in VANDAM nor with our ALMA 1.3 mm data; we only detect
the two known protostars and the extended emission around them. Santangelo et al. (2015) also did
not detect this source at a wavelength of 3 mm. This case of A3 toward Per-emb-12 is very similar
to the case of the companions (denoted MM2 and MM3) around Per-emb-27 (NGC 1333 IRAS2A)
reported by Maury et al. (2014) from PdBI observations. These companions were not detected by the
VLA, CARMA, or the SMA, as detailed in Tobin et al. (2015b) or by the more sensitive ALMA data
presented here. It is most likely that A3 toward Per-emb-12 and MM2 and MM3 toward Per-emb-27
are either artifacts from the deconvolution process and/or additional noise resulting from dynamic
range limitations of the PdBI as was previously discussed in Tobin et al. (2015b).
In a similar vein, there have been hypotheses put forward that some clearly detected continuum
sources were features produced by outflow interactions (Maury et al. 2010, 2012). However, further
study over the past several years has found that, the continuum features that were suggested to be
outflow knots in VLA 1623, are definitively real protostars (Murillo & Lai 2013; Murillo et al. 2013;

ALMA Perseus Multiplicity 17


Sadavoy et al. 2018; Harris et al. 2018). The other cases where continuum sources were suggested
to be outflow features (i.e., L1448-mm, NGC 1333 IRAS2A, NGC 1333 IRAS4A, Maury et al. 2010,
2014; Santangelo et al. 2015) seem to be artifacts in those data given their lack of detection here
with ALMA and in other works at the same and other wavelengths (Tobin et al. 2015b,a).
While it seems unlikely that outflow features are significantly contributing to the detection of
false companions, we note that none of the companions without detections are found along the
outflow direction. Moreover, the host protostars of the three non-detections are not driving prominent
outflows as viewed from the ALMA [12] CO data. Therefore it seems unlikely that companions are being
mimicked by outflow features in our case.
We had an 80% detection rate with ALMA toward the VLA-detected close multiples in Perseus;
100% for the Class 0s and 62.5% for the Class Is. The Class I non-detections based on the VANDAM

survey are likely to be real companions but were below our detection limits. For these sources in
particular, it might be useful to search for their companions in the near-infrared since they are
observed toward sources that are not highly embedded. Thus, we can conclude that VLA-detected
companions are quite robust.


5. CONCLUSIONS


We have conducted ALMA observations toward 17 VLA-detected proto-multiple systems from
the VANDAM survey that are separated by less than 600 AU. We observed these systems in dust
continuum at 1.3 mm and the [12] CO, [13] CO, C [18] O, SO, and H 2 CO molecular lines, enabling us to
examine the circumbinary environments. Our main results are as follows:


_•_ Of the 15 companions that could be resolved in our observations, we detect 12 confidently,
with tentative detections for 2 additional sources. We conclude that the VANDAM multiplicity
detections from Tobin et al. (2016b) had very high reliability. Though they were not the focus
of this study, we also detected all wide companions in the higher-order systems around L1448
IRS3B, Per-emb-55, and Per-emb-44.


_•_ We detect circum-multiple dust emission in 8 out of the 9 deeply embedded Class 0 sources
in the sample, but none in the remaining 8 more-revealed Class I systems. For the sources
that are closer to edge-on, this material is oriented orthogonal to the outflow direction and the
companion stars are embedded within the circum-multiple material. This is consistent with
the expectations for their formation within a circumbinary/multiple disk.


_•_ We detect molecular line emission associated with the circum-multiple material in 12 systems
(all Class 0 systems and 3 out of 8 Class I systems). The molecular lines with discernible
velocity gradients were orthogonal to the outflow directions in 8 out of 12 cases (EDJ2009-269
had too tentative of a detection in [12] CO). Velocity gradients orthogonal to the outflow on these
scales ( _<_ 600 AU) are most likely due to rotation. Therefore, 8/12 systems are consistent with
disk fragmentation and 4/12 appear inconsistent with disk fragmentation. However, the overall
numbers are small and may not reflect a general ratio for the origin of close companions.


_•_ Most of the less-embedded Class I systems in our sample do not show circumbinary dust or
gas emission. These systems are likely near the end point of their evolution where the circummultiple disk is mostly accreted or dispersed.

18 Tobin et al.


_•_ We identified two additional strong disk candidates, L1448 IRS3A and Per-emb-8. Both show
extended dust emission and have molecular line emission that is consistent with rotation. Per
emb-8 now has a better defined position angle compared to what was known previously from
the VLA.


We acknowledge fruitful discussions with D. Harsono, P. Sheehan, P. Hennebelle, and N. Reynolds.
We also thank the anonymous referee for comments that improved the quality of the manuscript.
J.J.T. acknowledges support from NSF grant AST-1814762, the Homer L. Dodge Endowed Chair,
and grant 639.041.439 from the Netherlands Organisation for Scientific Research (NWO). This paper
makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00031.S. Z.-Y.L. is supported
in part by NSF AST-1616636 and AST-1716259 and NASA NNX14AB38G. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The
National Radio Astronomy Observatory is a facility of the National Science Foundation operated
under cooperative agreement by Associated Universities, Inc. This research made use of APLpy,
an open-source plotting package for Python hosted at http://aplpy.github.com. This research made
use of Astropy, a community-developed core Python package for Astronomy (Astropy Collaboration,
2013) http://www.astropy.org.

## Facility: ALMA, Facility: VLA Software: Astropy(http://www.astropy.org;AstropyCollaborationetal.2018;Greenfieldetal.2013),

APLpy(http://aplpy.github.com; Robitaille&Bressert2012),CASA(http://casa.nrao.edu; McMullin
etal.2007),TheIDLAstronomyUser’sLibrary(https://idlastro.gsfc.nasa.gov/)


APPENDIX


A. OUTFLOW OBSERVATIONS


Our observations toward the Perseus multiple systems also encompassed [12] CO, which typically
traces outflowing gas toward protostars. We detected outflow signatures toward 13 out of the 17
protostars observed. These detections are shown in Figures 23, 24, & 25. Of the remaining 4 systems
that do not appear to have outflows traced by [12] CO, rotation in the disk was found toward L1448 IRS1
(Figure 19), two traced the continuum disk without a clear velocity gradient (Per-emb-48, EDJ2009269; Figures 20), and one was not detected (Per-emb-49). In most cases, the close multiples only have
one outflow that is clearly distinguished, there are a few exceptions, however. Per-emb-12 shows two
approximately parallel outflows, Per-emb-27 shows two orthogonal outflows, and Per-emb-35 shows
approximately parallel outflows.


B. COMPANION PROTOSTAR SEPARATION DISTRIBUTIONS


The recently revised distance of _∼_ 300 pc to the Perseus molecular cloud (Zucker et al. 2018;
Ortiz-Le´on et al. 2018) has resulted in the angular separations of the detected multiple systems
corresponding to larger physical separations. We have generated a revised separation distribution
using the updated distance for all the the combined sample, and the classes individually and plot the

ALMA Perseus Multiplicity 19


distributions in Figure 26. We have provided the updated separations in Table 5, 6, and 7. The rest
of the information contained in the tables is the same as in Tobin et al. (2016b).


REFERENCES



Adams, F. C., Ruden, S. P., & Shu, F. H. 1989,
ApJ, 347, 959
Andr´e, P., Ward-Thompson, D., & Barsony, M.
1993, ApJ, 406, 122
Anglada, G., Rodr´ıguez, L. F., Osorio, M., et al.
2004, ApJL, 605, L137
Aso, Y., Ohashi, N., Saigo, K., et al. 2015, ApJ,
812, 27
Astropy Collaboration, Price-Whelan, A. M.,
Sip˝ocz, B. M., et al. 2018, The Astropy Project:
Building an Open-science Project and Status of
the v2.0 Core Package,,, arXiv:1801.02634
Bate, M. R. 2012, MNRAS, 419, 3115
—. 2018, MNRAS, 475, 5618
Bohlin, R. C., Savage, B. D., & Drake, J. F. 1978,
ApJ, 224, 132
Bonnell, I. A., & Bate, M. R. 1994, MNRAS, 269,
L45

Brown, D. W., Chandler, C. J., Carlstrom, J. E.,
et al. 2000, MNRAS, 319, 154
Burkert, A., & Bodenheimer, P. 1993, MNRAS,
264, 798
Chen, X., Arce, H. G., Zhang, Q., et al. 2013,
ApJ, 768, 110
Chiang, H., Looney, L. W., & Tobin, J. J. 2012,
ApJ, 709, 470
Connelley, M. S., Reipurth, B., & Tokunaga,
A. T. 2008, AJ, 135, 2526
Duchˆene, G., Bontemps, S., Bouvier, J., et al.
2007, A&A, 476, 229
Duchˆene, G., & Kraus, A. 2013, ARA&A, 51, 269
Dunham, M. M., Stutz, A. M., Allen, L. E., et al.
2014, Protostars and Planets VI, 195
Dunham, M. M., Offner, S. S. R., Pineda, J. E.,
et al. 2016, ApJ, 823, 160
Duquennoy, A., & Mayor, M. 1991, A&A, 248, 485
Dzib, S. A., Loinard, L., Mioduszewski, A. J.,
et al. 2013, ApJ, 775, 63
Fern´andez-L´opez, M., Arce, H. G., Looney, L.,
et al. 2014, ApJL, 790, L19
Foster, J. B., & Goodman, A. A. 2006, ApJL, 636,
L105

Greenfield, P., Robitaille, T., Tollerud, E., et al.
2013, ascl:1304.002



Gutermuth, R. A., Myers, P. C., Megeath, S. T.,
et al. 2008, ApJ, 674, 336
Harris, R. J., Andrews, S. M., Wilner, D. J., &
Kraus, A. L. 2012, ApJ, 751, 115
Harris, R. J., Cox, E. G., Looney, L. W., et al.
2018, ArXiv e-prints, arXiv:1805.08792
Hirota, T., Honma, M., Imai, H., et al. 2011,
PASJ, 63, 1
Hirota, T., Bushimata, T., Choi, Y. K., et al.
2008, PASJ, 60, 37
Kirk, H., Dunham, M. M., Di Francesco, J., et al.
2017, ApJ, 838, 114
Kratter, K. M., Matzner, C. D., & Krumholz,
M. R. 2008, ApJ, 681, 375
Kratter, K. M., Matzner, C. D., Krumholz, M. R.,
& Klein, R. I. 2010, ApJ, 708, 1585
Lee, K. I., Dunham, M. M., Myers, P. C., et al.
2016, ApJL, 820, L2
Looney, L. W., Mundy, L. G., & Welch, W. J.
2000, ApJ, 529, 477
Mangum, J. G., & Wootten, A. 1993, ApJS, 89,
123
Maury, A., Ohashi, N., & Andr´e, P. 2012, A&A,
539, A130
Maury, A. J., Andr´e, P., Hennebelle, P., et al.
2010, A&A, 512, A40
Maury, A. J., Belloche, A., Andr´e, P., et al. 2014,
A&A, 563, L2
McKee, C. F., & Ostriker, E. C. 2007, ARA&A,
45, 565
McMullin, J. P., Waters, B., Schiebel, D., Young,
W., & Golap, K. 2007, in Astronomical Society
of the Pacific Conference Series, Vol. 376,
Astronomical Data Analysis Software and
Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Murillo, N. M., & Lai, S.-P. 2013, ApJL, 764, L15
Murillo, N. M., Lai, S.-P., Bruderer, S., Harsono,
D., & van Dishoeck, E. F. 2013, A&A, 560,
A103
Offner, S. S. R., Dunham, M. M., Lee, K. I., Arce,
H. G., & Fielding, D. B. 2016, ApJL, 827, L11
Offner, S. S. R., Kratter, K. M., Matzner, C. D.,
Krumholz, M. R., & Klein, R. I. 2010, ApJ, 725,
1485

20 Tobin et al.



Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ,
796, 131
Ortiz-Le´on, G. N., Loinard, L., Dzib, S. A., et al.
2018, ArXiv e-prints, arXiv:1808.03499
Ossenkopf, V., & Henning, T. 1994, A&A, 291,
943
Padoan, P., & Nordlund, [˚] A. 2002, ApJ, 576, 870
Pineda, J. E., Offner, S. S. R., Parker, R. J., et al.
2015, Nature, 518, 213
Plunkett, A. L., Arce, H. G., Corder, S. A., et al.
2013, ApJ, 774, 22
Raghavan, D., McAlister, H. A., Henry, T. J.,
et al. 2010, ApJS, 190, 1
Reipurth, B., & Mikkola, S. 2012, Nature, 492, 221
Robitaille, T., & Bressert, E. 2012, APLpy:
Astronomical Plotting Library in Python,
Astrophysics Source Code Library,,,
ascl:1208.017
Rodr´ıguez, L. F., Anglada, G., & Curiel, S. 1999,
ApJS, 125, 427
Rodr´ıguez, L. F., Reipurth, B., Raga, A. C., &
Cant´o, J. 1998, RMxAA, 34, 69
Sadavoy, S. I., & Stahler, S. W. 2017, MNRAS,
469, 3881
Sadavoy, S. I., Myers, P. C., Stephens, I. W., et al.
2018, ArXiv e-prints, arXiv:1804.05968
Sakai, N., Oya, Y., Sakai, T., et al. 2014, ApJL,
791, L38
Santangelo, G., Codella, C., Cabrit, S., et al.
2015, A&A, 584, A126
Segura-Cox, D. M., Harris, R. J., Tobin, J. J.,
et al. 2016, ApJL, 817, L14
Segura-Cox, D. M., Looney, L. W., Tobin, J. J.,
et al. 2018, ArXiv e-prints, arXiv:1808.10438
Simon, M., Dutrey, A., & Guilloteau, S. 2000,
ApJ, 545, 1034
Stamatellos, D., & Whitworth, A. P. 2009,
MNRAS, 392, 413



Stephens, I. W., Dunham, M. M., Myers, P. C.,
et al. 2017, ApJ, 846, 16
Storm, S., Mundy, L. G., Fern´andez-L´opez, M.,
et al. 2014, ApJ, 794, 165
Takakuwa, S., Kiyokane, K., Saigo, K., & Saito,
M. 2015, ApJ, 814, 160
Takakuwa, S., Saito, M., Lim, J., et al. 2012, ApJ,
754, 52
Takakuwa, S., Saito, M., Saigo, K., et al. 2014,
ApJ, 796, 1
Taquet, V., L´opez-Sepulcre, A., Ceccarelli, C.,
et al. 2015, ApJ, 804, 81


Tobin, J. J., Hartmann, L., Chiang, H.-F., et al.
2012, Nature, 492, 83
—. 2011, ApJ, 740, 45
Tobin, J. J., Bergin, E. A., Hartmann, L., et al.
2013, ApJ, 765, 18
Tobin, J. J., Looney, L. W., Wilner, D. J., et al.
2015a, ApJ, 805, 125
Tobin, J. J., Dunham, M. M., Looney, L. W.,
et al. 2015b, ApJ, 798, 61
Tobin, J. J., Kratter, K. M., Persson, M. V., et al.
2016a, Nature, 538, 483
Tobin, J. J., Looney, L. W., Li, Z.-Y., et al.
2016b, ApJ, 818, 73
Tychoniec, �L., Tobin, J. J., Karska, A., et al.
2018a, ApJ, 852, 18
—. 2018b, ArXiv e-prints, arXiv:1806.02434
—. 2018c, ArXiv e-prints, arXiv:1806.02434
Wakelam, V., Ceccarelli, C., Castets, A., et al.
2005, A&A, 437, 149
Whitney, B. A., Wood, K., Bjorkman, J. E., &
Wolff, M. J. 2003, ApJ, 591, 1049
Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014,
ApJ, 793, 1
Zucker, C., Schlafly, E. F., Green, G. M., et al.
2018, ArXiv e-prints, arXiv:1803.08931

ALMA Perseus Multiplicity 21



33.0


32.0


31.0


+31:13:30.0


15.0


14.0


13.0


+30:45:12.0


05.0


04.0


03.0


+31:16:02.0



0.1200.105
0.090
0.075

0.060


0.045


0.030






|Col1|Col2|0.0|
|---|---|---|
|3:29:11<br>11.2<br>11.3<br>1.4<br>RA (J2000)<br>1.0" (300.0 AU)|3:29:11<br>11.2<br>11.3<br>1.4<br>RA (J2000)<br>1.0" (300.0 AU)|.1<br>0.<br>0.<br>.|
|3:29:11<br>11.2<br>11.3<br>1.4<br>RA (J2000)<br>1.0" (300.0 AU)|||


|10"(3000AU)<br>. .<br>55.7 5 R5.A6 (J2000)3:28:55.5|Col2|0.|
|---|---|---|
|3:28:55.5<br>55.6<br>55.7<br>RA (J2000)<br>1.0" (300.0 AU)|||





49.0


48.0


47.0


+30:49:46.0


32.0


31.0


30.0


+31:18:29.0











04.0


03.0


02.0


+30:13:01.0


38.0


37.0


36.0


+31:14:35.0


36.0


35.0


34.0


+30:45:33.0



0.024


0.1200.1050.090







0.040


0.048


0.042


0.036


0.030


0.024


0.018


0.012


0.006


0.000





0.015



0.080.07



16.0


15.0


14.0


+30:45:13.0




|L1448 IRS3B 1.3 mm|Col2|0.0 0.0 0.0 0.0|
|---|---|---|
|||0.<br>0.<br>0.<br>0.<br>0.<br>0.<br>|
|3<br>36.3<br>36.4<br>RA (J2000)<br>1.0" (300.0 AU)|:25:36|.2<br>0.|
|3<br>36.3<br>36.4<br>RA (J2000)<br>1.0" (300.0 AU)|||


|L1448 IRS3C 1.3 mm|Col2|0.0 0.0 0.0|
|---|---|---|
|||0.<br>0.<br>0.<br>0.<br>0.<br>.|
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>1.0" (300.0 AU)||0.|
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>1.0" (300.0 AU)|||



**Figure** **1.** ALMA images of Class 0 multiple protostar systems in Perseus at 1.3 mm. The white or
black crosses mark the VLA source positions in each image. A 1 _[′′]_ scale bar is also drawn in each panel
denoting 300 AU. The beam of each image is drawn in the lower right corner, corresponding to approximately
0 _[′′]_ _._ 27 _×_ 0 _[′′]_ _._ 17 (81 AU _×_ 51 AU). The noise level in each image is approximately 0.14 mJy beam _[−]_ [1], but this
varies somewhat between sources depending on dynamic range limits. The approximate outflow directions
(when known) are drawn in the lower right corner with the red and blue arrows directions corresponding
to the orientation of the outflow. Note that the outflows apparently originate from the bright continuum
peaks, but the arrows are drawn offset for clarity.

22 Tobin et al.





0.024


0.021


0.018


0.015


0.012


0.009


0.006





0.024


0.021


0.018


0.015


0.012


0.009


0.006


0.003


0.000

|10"(3000AU)|Col2|Col3|
|---|---|---|
|10" (3000 AU)||0.|
|10" (3000 AU)|||
|10" (3000 AU)|||



0.0048


0.0040


0.0032


0.0024


0.0016


0.0008


0.0000


"0.0008



0.14



33.0


32.0


31.0


+31:13:30.0


14:00.0


59.0


58.0


+30:13:57.0


|10"(3000AU)|Col2|
|---|---|
|10" (3000 AU)|0.|
|10" (3000 AU)|8:37.0|
|10" (3000 AU)||



|Per-emb-48 1.3 mm<br>10"(3000AU)|Col2|
|---|---|
|Per-emb-48 1.3 mm<br>10" (3000 AU)|0.<br>0.|
|Per-emb-48 1.3 mm<br>10" (3000 AU)|−0|
|Per-emb-48 1.3 mm<br>10" (3000 AU)||


23.0


22.0


21.0


+30:46:20.0









0.003


0.000



17.0


16.0


15.0


+31:14:14.0


16.0


15.0


14.0


+31:18:13.0



56.0


55.0


54.0


+31:07:53.0


33.0


32.0


31.0


+32:01:30.0


|Per-emb-55 1.3 mm<br>10"(3000AU)|Col2|Col3|
|---|---|---|
|Per-emb-55  1.3 mm<br>10" (3000 AU)||0.|
|Per-emb-55  1.3 mm<br>10" (3000 AU)||"|
|Per-emb-55  1.3 mm<br>10" (3000 AU)|||





0.0035


0.0030


0.0025


0.0020


0.0015


0.0010


0.0005


0.0000


−0.0005



0.024



48.0


47.0


46.0


+30:32:45.0





0.090



0.0075


0.0060


0.0045


0.0030


0.0015


|L1448 IRS1 1.3 mm|0.0 0.0|
|---|---|
|.<br>0" (300.0 AU)|0.0<br>0.0<br>0.0<br>0.0<br>0.0|
|.<br>0" (300.0 AU)||
|.<br>0" (300.0 AU)||
|.<br>0" (300.0 AU)||
|.<br>0" (300.0 AU)|0.0|
|3:25:09.3<br>09.4<br>09.5<br>RA (J2000)||
|3:25:09.3<br>09.4<br>09.5<br>RA (J2000)||


|EDJ2009-269 1.3 mm|Col2|Col3|
|---|---|---|
|.<br>1.0" (300.0 AU)|.<br>1.0" (300.0 AU)|00<br>0.0<br>0.0<br>0.0<br>0.0|
|.<br>1.0" (300.0 AU)||.|
|.<br>1.0" (300.0 AU)||00|
|.<br>1.0" (300.0 AU)||.|
|.<br>1.0" (300.0 AU)||0.0|
|3:30:43.9<br>44.0<br>44.1<br>RA (J2000)|||
|3:30:43.9<br>44.0<br>44.1<br>RA (J2000)|||



**Figure** **2.** Same as Figure 1, except for Class I multiple systems in Perseus.

ALMA Perseus Multiplicity 23



0.024


0.021


0.018


0.015


0.012


0.009


0.006


0.003


0.000

|SVS13A2 (VLA3) 1 .3 mm<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)|||||||||||0.|
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|SVS13A2 (VLA3) 1.3 mm<br>1.0" (300.0 AU)||||||||||||



0.0090


0.0075


0.0060


0.0045


0.0030


0.0015


0.0000



0.040


0.035


0.030


0.025


0.020


0.015


0.010


0.005


0.000

|SVS13 1 .3 mm<br>RAC1999VLA20<br>SVS13A2<br>SVS13B<br>50"(15000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||
|SVS13 1.3 mm<br>SVS13B<br>SVS13A2<br>RAC1999 VLA20<br>5.0" (1500.0 AU)||||||
|||||||
|||||||
|||||||
|||||||



0.040


0.035


0.030


0.025


0.020


0.015


0.010


0.005


0.000





10.0


05.0


16:00.0


55.0


+31:15:50.0


52.5


52.0


51.5


+31:15:51.0





02.5


02.0


01.5


+31:16:01.0


10.0


09.5


09.0


+31:16:08.5




|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|0.0|
|---|---|---|---|---|---|---|---|---|---|
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|||0.<br>0.<br>0.<br>0.<br>0.<br>0.<br>0.<br>.|
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||||||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||||||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||||||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|||||||||0|
|SVS13B  1.3 mm<br>1.0" (300.0 AU)|||||||||.|
|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||||||||
|SVS13B  1.3 mm<br>1.0" (300.0 AU)||||||||||
|03.1<br>RA (J2000)|||||3:|29|0|||
|03.1<br>RA (J2000)||||||||.||
|03.1<br>RA (J2000)||||||||||


|RAC1999 VLA20 1 .3 mm<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.|
|---|---|---|---|---|---|---|---|---|---|---|---|
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|||||||||||0|
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)|||||||||||.|
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|RAC1999 VLA20 1.3 mm<br>1.0" (300.0 AU)||||||||||||
|04.3<br>RA (J2000)||3:|9|:0|2|||||||
|04.3<br>RA (J2000)|||||.|||||||
|04.3<br>RA (J2000)||||||||||||



**Figure 3.** ALMA 1.3 mm images of the SVS13 (Per-emb-44) region. A wide view of the region encompassing
all the sources within the primary beam is shown in the top left and dashed boxes mark the regions zoomed-in
on in the subsequent panels. The northeastern-most source (RAC1999 VLA20) is most likely a background
extragalactic source from the VLA imaging results. The two sources south of SVS13A are SVS13A2 (VLA3)
and SVS13B. We show the zoom-in on SVS13A2 in the top right panel, the zoom-in on SVS13B in the
bottom left panel, and RAC1999 VLA20 in the bottom right panel. SVS13A2 and RAC1999 VLA20 do not
appear highly resolved, while SVS13B is clearly resolved with respect to the beam.

24 Tobin et al.



23.0


22.0


21.0


+30:45:20.0



0.028


0.024


0.020


0.016


0.012


0.008


0.004


0.000



0.028


0.024


0.020


0.016


0.012


0.008


0.004


0.000



36.0


30.0


24.0


18.0


+30:45:12.0






|L1448 IRS3 1.3 mm|Col2|Col3|Col4|Col5|0.0|
|---|---|---|---|---|---|
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|||0.0<br>0.0<br>0.0<br>0.0<br>0.0<br>0.0<br>0.0<br>0.0|
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||
|L1448 IRS3 1.3 mm<br>L1448 IRS3A<br>5.0" (1500.0 AU)||||||
|3:<br>35.5<br>36.0<br>36.5<br>37.0<br>RA (J2000)|25|35|0|||
|3:<br>35.5<br>36.0<br>36.5<br>37.0<br>RA (J2000)|||.|||
|3:<br>35.5<br>36.0<br>36.5<br>37.0<br>RA (J2000)||||||


|L1448 IRS3A 1.3 mm|Col2|Col3|Col4|0.0|
|---|---|---|---|---|
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|||0.<br>0.<br>0.<br>0.<br>0.<br>0.<br>0.|
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|||||
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)||||0.|
|L1448 IRS3A 1.3 mm<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)|||||



**Figure 4.** ALMA 1.3 mm images of the L1448 IRS3 (Per-emb-33) region encompassing all the sources within
the primary beam; the dashed box marks the regions zoomed-in on in the right panel. The observation was
centered on L1448 IRS3B largest and brightest source near the bottom of the image. Nonetheless, L1448
IRS3A is detected, source in the middle-left, and L1448 IRS3C (L1448 NW) is marginally detected in this
image toward the upper right. L1448 IRS3C was also observed with a separate pointing given its large
angular distance from field center. Right: ALMA 1.3 mm zoom-in on L1448 IRS3A showing the resolved
disk structure toward this protostar.



0.028


0.024


0.020


0.016


0.012


0.008


0.004


0.000







39.0


36.0


33.0


30.0


+32:01:27.0





37.0


36.0


35.0


+32:01:34.0




|Per-emb -8/55 1 .3 mm<br>Per-emb-8<br>50"(15000AU)<br>. .|Col2|Col3|Col4|Col5|00<br>.<br>00<br>.<br>00<br>.<br>00<br>.<br>00<br>.<br>00<br>.<br>00<br>.<br>00<br>.|
|---|---|---|---|---|---|
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||
|Per-emb-8/55  1.3 mm<br>Per-emb-8<br>5.0" (1500.0 AU)||||||
|3:44:43.<br>43.4<br>43.6<br>43.8<br>44.0<br>4.2<br>RA (J2000)|2|||||
|3:44:43.<br>43.4<br>43.6<br>43.8<br>44.0<br>4.2<br>RA (J2000)||||||
|3:44:43.<br>43.4<br>43.6<br>43.8<br>44.0<br>4.2<br>RA (J2000)||||||


|Per-emb-8 1.3 mm|Col2|Col3|Col4|0.0|
|---|---|---|---|---|
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|||0.<br>0.<br>0.<br>0.<br>0.<br>0.<br>.|
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|||||
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)||||0.|
|Per-emb-8  1.3 mm<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)|||||



**Figure** **5.** ALMA 1.3 mm image of the Per-emb-8/Per-emb-55 region the two sources within the primary
beam; the dashed box marks the regions zoomed-in on in the right panel. Per-emb-8 is located in the
eastern portion of the image and Per-emb-55 is located in the western portion. Per-emb-8 is clearly resolved
and Per-emb-55 is a binary, but only one component is strongly detected. Right: ALMA 1.3 mm image of
Per-emb-8, an apparently single source with a surrounding disk. The central region of Per-emb-8 is very
prominent with respect to the extended disk.

ALMA Perseus Multiplicity 25



33.0


30.0


27.0


24.0


+31:18:21.0





0.048


0.042


0.036


0.030


0.024


0.018


0.012


0.006


0.000



0.028


0.024


0.020


0.016


0.012


0.008


0.004


0.000



21.0


20.5


20.0


+31:18:19.5




|Per-emb -18-21 1 .3 mm<br>Per-emb-21<br>50"(15000AU)<br>. .|Col2|Col3|0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.|
|---|---|---|---|
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|||
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|||
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|||
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|||
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|||
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)||0.|
|Per-emb-18-21  1.3 mm<br>Per-emb-21<br>5.0" (1500.0 AU)||||
|3<br>10.6<br>10.8<br>11.0<br>11.2<br>11.4<br>RA (J2000)|29:|04||
|3<br>10.6<br>10.8<br>11.0<br>11.2<br>11.4<br>RA (J2000)||.||
|3<br>10.6<br>10.8<br>11.0<br>11.2<br>11.4<br>RA (J2000)||||


|Per-emb -21 1 .3 mm<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.<br>0<br>.|
|---|---|---|---|---|---|---|---|---|---|
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)||||
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)|||||||||0.|
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)||||||||||
|Per-emb-21  1.3 mm<br>1.0" (300.0 AU)||||||||||
|10.7<br>RA (J2000)|||:29|1|6|||||
|10.7<br>RA (J2000)|||||.|||||
|10.7<br>RA (J2000)||||||||||



**Figure** **6.** ALMA 1.3 mm image of the Per-emb-18/Per-emb-21 region encompassing the two protostars
within the primary beam; the dashed box marks the regions zoomed-in on in the right panel. Per-emb-18
is located in the northern portion of the image and Per-emb-21 is located in the southern portion. Right:
ALMA 1.3 mm image zooming-in on Per-emb-21, which appears unresolved.



49.0


48.0


47.0


+30:49:46.0





49.0


48.0


47.0


+30:49:46.0




|Per-emb-2 13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|Per-emb-213CO<br>1.0" (300.0 AU)|Per-emb-213CO<br>1.0" (300.0 AU)|Per-emb-213CO<br>1.0" (300.0 AU)|Per-emb-213CO<br>1.0" (300.0 AU)|
|Per-emb-213CO<br>1.0" (300.0 AU)||||
|Per-emb-213CO<br>1.0" (300.0 AU)||||
|Per-emb-213CO<br>1.0" (300.0 AU)||||
|Per-emb-213CO<br>1.0" (300.0 AU)||||
|Per-emb-213CO<br>1.0" (300.0 AU)||||
|Per-emb-213CO<br>1.0" (300.0 AU)||||
|3<br>17.9<br>18.0<br>RA (J2000)|32:|178||
|3<br>17.9<br>18.0<br>RA (J2000)||.||
|3<br>17.9<br>18.0<br>RA (J2000)||||


|Per-emb-2 C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)|
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)||||
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)||||
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)||||
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)||||
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)||||
|Per-emb-2  C18O<br>1.0" (300.0 AU)|Per-emb-2  C18O<br>1.0" (300.0 AU)||||
|17.9<br>18.0<br>RA (J2000)|3:3|2:|17||
|17.9<br>18.0<br>RA (J2000)|3:3||.||
|17.9<br>18.0<br>RA (J2000)|3:3||||



**Figure** **7.** Integrated intensity maps of [13] CO (left panel) and C [18] O (right panel) toward Per-emb-2. The
integrated intensity maps are displayed as red and blue contours corresponding to the integrated intensity
of line emission red and blue-shifted with respect to the system velocity. The contours are overlaid on the
1.3 mm continuum image. The line emission shows evidence for a velocity gradient consistent with rotation.
The red-shifted contours start at (4,3) _σ_ and increase in (1,1) _σ_ increments, and the blue-shifted contours
start at (3,3) _σ_ and increase in (1,1) _σ_ increments. The values inside the parentheses in the previous sentence
correspond to the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_
and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in Table 3. The beam
in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

26 Tobin et al.





33.0


32.0


31.0


30.0


+31:13:29.0


+31:13:30.0






|IRAS4A C18O<br>U)|Col2|Col3|Col4|
|---|---|---|---|
|IRAS 4A  C18O<br>  U)||||
|IRAS 4A  C18O<br>  U)||||
|IRAS 4A  C18O<br>  U)|3|29:|103|
|IRAS 4A  C18O<br>  U)|||.|
|IRAS 4A  C18O<br>  U)||||


|NGC1333IRAS4A C18O<br>33.0<br>32.0<br>31.0<br>30.0<br>10"(3000AU)<br>. .<br>1:13:29.0<br>10.6 10.5 10.4 3:29:10.3<br>RA(J2000)<br>NGC1333IRAS4A H CO<br>2<br>33.0<br>32.0<br>31.0<br>30.0<br>10"(3000AU)<br>. .<br>1:13:29.0<br>10.6 10.5 10.4 3:29:10.3<br>RA(J2000)|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  C18O<br>1.0" (300.0 AU)<br>3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  H2CO<br>1.0" (300.0 AU)|IRAS 4A  H2CO<br>  U)|IRAS 4A  H2CO<br>  U)|IRAS 4A  H2CO<br>  U)|IRAS 4A  H2CO<br>  U)|
|3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  C18O<br>1.0" (300.0 AU)<br>3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  H2CO<br>1.0" (300.0 AU)|IRAS 4A  H2CO<br>  U)||||
|3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  C18O<br>1.0" (300.0 AU)<br>3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  H2CO<br>1.0" (300.0 AU)|IRAS 4A  H2CO<br>  U)||||
|3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  C18O<br>1.0" (300.0 AU)<br>3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  H2CO<br>1.0" (300.0 AU)|10.4<br>0.5<br> (J2000)|3|29:|103|
|3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  C18O<br>1.0" (300.0 AU)<br>3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  H2CO<br>1.0" (300.0 AU)|10.4<br>0.5<br> (J2000)|||.|
|3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  C18O<br>1.0" (300.0 AU)<br>3:29:10.3<br>10.4<br>10.5<br>10.6<br>RA (J2000)<br>1:13:29.0<br>30.0<br>31.0<br>32.0<br>33.0<br> <br>NGC 1333 IRAS 4A  H2CO<br>1.0" (300.0 AU)|10.4<br>0.5<br> (J2000)||||



**Figure** **8.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-12 (NGC 1333 IRAS4A). The integrated intensity
maps are displayed as red and blue contours corresponding to the integrated intensity of line emission red
and blue-shifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum
image. The line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted
contours start at (3,3,4,3) _σ_ and increase in (3,1,2,3) _σ_ increments, and the blue-shifted contours start at
(3,3,4,3) _σ_ and increase in (3,1,2,3) _σ_ increments. The values inside the parentheses in the previous sentence
correspond to the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_
and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in Table 3. The beam
in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 27



04.0


03.0


02.0


+30:13:01.0








|Col1|Per-emb-17/RNO 15 C18O<br>10"(3000AU)<br>. .|Col3|Col4|Col5|
|---|---|---|---|---|
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)|39|||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)|.|||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
||Per-emb-17/RNO 15  C18O<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|39|||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|.|||
|3:27:39.0<br>39.1<br>39.2<br>RA (J2000)<br>3:01.0<br>02.0<br>03.0<br>04.0<br>Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)|Per-emb-17/RNO 15 H2CO<br>1.0" (300.0 AU)||||



**Figure** **9.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-17. The integrated intensity maps are displayed
as red and blue contours corresponding to the integrated intensity of line emission red and blue-shifted
with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The line
emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at (3,4,3,3) _σ_ and increase in (2,1,2,3) _σ_ increments, and the blue-shifted contours start at (3,3,3,3) _σ_ and
increase in (2,1,2,3) _σ_ increments. The values inside the parentheses in the previous sentence correspond to
the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_ and
velocity ranges over which the line emission was summed can be found in Table 3. The beam in the images
is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

28 Tobin et al.





32.0


31.0


30.0


+31:18:29.0


32.0


31.0


30.0


+31:18:29.0



32.0


31.0


30.0


+31:18:29.0


32.0


31.0


30.0


+31:18:29.0


|Per-emb-18 C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||
|Per-emb-18  C18O<br>1.0" (300.0 AU)||3:|9|1|1|
|Per-emb-18  C18O<br>1.0" (300.0 AU)|||||.|
|Per-emb-18  C18O<br>1.0" (300.0 AU)||||||


|Col1|Per-emb-18 13CO<br>10"(3000AU)<br>. .|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||3:|9|1|1|
||Per-emb-1813CO<br>1.0" (300.0 AU)|||||.|
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
||Per-emb-1813CO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||3:|9|1|1|
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)|||||.|
|3:29:11.1<br>11.2<br>11.3<br>11.4<br>RA (J2000)<br>0<br>0<br>0<br>0<br>Per-emb-18  SO<br>1.0" (300.0 AU)|Per-emb-18  SO<br>1.0" (300.0 AU)||||||


|Per-emb-18 H 2CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|Per-emb-18  H2CO<br>1.0" (300.0 AU)||||||
|11.2<br>11.3<br>1.4<br>RA (J2000)||3:|9|1|1|
|11.2<br>11.3<br>1.4<br>RA (J2000)|||||.|
|11.2<br>11.3<br>1.4<br>RA (J2000)||||||



**Figure** **10.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-18. The integrated intensity maps are displayed
as red and blue contours corresponding to the integrated intensity of line emission red and blue-shifted
with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The line
emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at (3,3,3,3) _σ_ and increase in (2,1,2,2) _σ_ increments, and the blue-shifted contours start at (3,4,3,3) _σ_ and
increase in (2,1,2,2) _σ_ increments. The values inside the parentheses in the previous sentence correspond to
the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_ and
velocity ranges over which the line emission was summed can be found in Table 3. The beam in the images
is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 29



14.5


14.0


13.5


13.0


12.5


+30:45:12.0


14.5


14.0


13.5


13.0


12.5


+30:45:12.0





14.5


14.0


13.5


13.0


12.5


+30:45:12.0


14.5


14.0


13.5


13.0


12.5


+30:45:12.0




|L1448IRS213CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|L1448 IRS213CO<br>1.0" (300.0 AU)||||
|3:25:22.3<br>22.4<br>RA (J2000)||||
|3:25:22.3<br>22.4<br>RA (J2000)||||
|3:25:22.3<br>22.4<br>RA (J2000)||||


|Col1|Col2|Col3|
|---|---|---|
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)|
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|L1448 IRS2 C18O<br>1.0" (300.0 AU)|L1448 IRS2 C18O<br>1.0" (300.0 AU)||
|22.4<br>RA (J2|3:25:22.3<br> 000)||
|22.4<br>RA (J2|3:25:22.3<br> 000)||
|22.4<br>RA (J2|3:25:22.3<br> 000)||


|L1448IRS2 SO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|L1448 IRS2  SO<br>1.0" (300.0 AU)||||
|3:25:22.3<br>22.4<br>RA (J2000)||||
|3:25:22.3<br>22.4<br>RA (J2000)||||
|3:25:22.3<br>22.4<br>RA (J2000)||||


|L1448IRS2 H CO<br>2<br>10"(3000AU)<br>. .|Col2|Col3|
|---|---|---|
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|L1448 IRS2  H2CO<br>1.0" (300.0 AU)|L1448 IRS2  H2CO<br>1.0" (300.0 AU)||
|22.4<br>RA (J2|3:25:22.3<br> 000)||
|22.4<br>RA (J2|3:25:22.3<br> 000)||
|22.4<br>RA (J2|3:25:22.3<br> 000)||



**Figure** **11.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-22 (L1448 IRS2). The integrated intensity maps
are displayed as red and blue contours corresponding to the integrated intensity of line emission red and
blue-shifted with respect to the system velocity. The green contours for the SO emission correspond to
emission integrated across the entire line because there was not a clear velocity gradient in this molecule due
to low S/N. The contours are overlaid on the 1.3 mm continuum image. The line emission shows evidence
for a velocity gradient consistent with rotation. The red-shifted contours start at (3,3,3,4) _σ_ and increase in
(3,3,3,2) _σ_ increments, and the blue-shifted contours start at (3,3,3,4) _σ_ and increase in (3,3,3,2) _σ_ increments.
The values inside the parentheses in the previous sentence correspond to the [13] CO, C [18] O, SO, and H 2 CO
integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_ and velocity ranges over which the line
emission was summed can be found in Table 3. The beam in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

30 Tobin et al.











38.0


37.5


37.0


36.5


36.0


+31:14:35.5


|Col1|3:28:55.5<br>2000)|
|---|---|
|55.6<br>55.7<br>RA (J<br>1:14:35.0<br>36.0<br>37.0<br>38.0<br> <br>Per-emb-27/<br>1.0" (300.0 A|IRAS2A  H2CO<br>  U)|
|55.6<br>55.7<br>RA (J<br>1:14:35.0<br>36.0<br>37.0<br>38.0<br> <br>Per-emb-27/<br>1.0" (300.0 A|3:28:55.5<br> 2000)|



**Figure** **12.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-27 (NGC 1333 IRAS2A). The integrated intensity
maps are displayed as red and blue contours corresponding to the integrated intensity of line emission red
and blue-shifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum
image. The line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted
contours start at (3,3,3,3) _σ_ and increase in (3,1,2,3) _σ_ increments, and the blue-shifted contours start at
(3,3,3,3) _σ_ and increase in (3,1,2,3) _σ_ increments. The values inside the parentheses in the previous sentence
correspond to the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_
and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in Table 3. The beam
in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 31



16.0


15.0


14.0


+30:45:13.0


16.0


15.0


14.0


+30:45:13.0





16.0


15.0


14.0


+30:45:13.0


16.0


15.0


14.0


+30:45:13.0




|L1448IRS3B13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||:2|5:|36|2|
|L1448 IRS3B13CO<br>1.0" (300.0 AU)|||||.|
|L1448 IRS3B13CO<br>1.0" (300.0 AU)||||||


|L1448IRS3BC18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3B C18O<br>1.0" (300.0 AU)|3:2|:36|2|
|L1448 IRS3B C18O<br>1.0" (300.0 AU)|||.|
|L1448 IRS3B C18O<br>1.0" (300.0 AU)||||


|3:25:36.2 36.3 36.4 RA (J2000)|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|
|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|L1448 IRS3B SO<br>1.0" (300.0 AU)|
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|L1448 IRS3B SO<br>1.0" (300.0 AU)||||||
|36.3<br>36.4<br>RA (J2000)||:2|5:|36|2|
|36.3<br>36.4<br>RA (J2000)|||||.|
|36.3<br>36.4<br>RA (J2000)||||||


|3:25:36.2 36.3 36.4 RA (J2000)|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|L1448 IRS3B H2CO<br>1.0" (300.0 AU)|
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3B H2CO<br>1.0" (300.0 AU)||||
|36.3<br>36.4<br>RA (J2000)|3:2|:36|2|
|36.3<br>36.4<br>RA (J2000)|||.|
|36.3<br>36.4<br>RA (J2000)||||



**Figure** **13.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-33 (L1448 IRS3B). The integrated intensity maps
are displayed as red and blue contours corresponding to the integrated intensity of line emission red and
blue-shifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image.
The line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours
start at (4,4,3,3) _σ_ and increase in (1,1,2,2) _σ_ increments, and the blue-shifted contours start at (4,4,3,3) _σ_
and increase in (1,1,2,2) _σ_ increments. The values inside the parentheses in the previous sentence correspond
to the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_
and velocity ranges over which the line emission was summed can be found in Table 3. The beam in the
images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

32 Tobin et al.



36.0


35.0


34.0


+30:45:33.0


+30:45:33.0







36.0


35.0


34.0


+30:45:33.0


36.0


35.0


34.0


+30:45:33.0


|L1448IRS3C 13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C13CO<br>1.0" (300.0 AU)||||


|L1448IRS3C C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||
|L1448 IRS3C  C18O<br>1.0" (300.0 AU)||||


|36.0|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)<br>33.0<br>34.0<br>35.0<br>6.0<br>L1448 IRS3C  SO<br>1.0" (300.0 AU)|L1448 IRS3C  SO<br>1.0" (300.0 AU)||||


|L1448IRS3CH CO<br>2<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|L1448 IRS3C H2CO<br>1.0" (300.0 AU)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)||||
|3:25:35.6<br>35.7<br>35.8<br>RA (J2000)||||



**Figure** **14.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward L1448 IRS3C (L1448 NW). The integrated intensity maps
are displayed as red and blue contours corresponding to the integrated intensity of line emission red and
blue-shifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image.
The line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours
start at (3,4) _σ_ and increase in (2,1) _σ_ increments, and the blue-shifted contours start at (3,3) _σ_ and increase
in (2,1) _σ_ increments. The contours for SO and H 2 CO start (3,3) _σ_ and increase in (2,3) _σ_, respectively for a
single interval. The values for _σ_, _σ_ _red_ and _σ_ _blue_ and velocity ranges over which the line emission was summed
can be found in Table 3. The beam in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 33



05.0


04.5


04.0


03.5


03.0


+31:16:02.5


+31:16:02.5





05.0


04.5


04.0


03.5


03.0


+31:16:02.5


05.0


04.5


04.0


03.5


03.0


+31:16:02.5




|SVS13A 13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||
|SVS13A13CO<br>1.0" (300.0 AU)|||||


|SVS13A SO<br>5.0<br>4.5<br>4.0<br>3.5<br>3.0<br>2.5 1 .0" (300 .0 AU)<br>03.8 3:29:03.7<br>RA(J2000)|SVS13A SO<br>10"(3000AU)<br>. .|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|3:29:03.7<br> 00)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|3:29:03.7<br> 00)|||||
|3:29:03.7<br>03.8<br>RA (J2000)<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>5.0<br>SVS13A  SO<br>1.0" (300.0 AU)|SVS13A  SO<br>1.0" (300.0 AU)|3:29:03.7<br> 00)|||||



**Figure** **15.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-44 (SVS13A). The integrated intensity maps are
displayed as red and blue contours corresponding to the integrated intensity of line emission red and blueshifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The
line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at (4,3,5,5) _σ_ and increase in (2,1,5,5) _σ_ increments, and the blue-shifted contours start at (4,3,5,5) _σ_ and
increase in (2,1,5,5) _σ_ increments. The values inside the parentheses in the previous sentence correspond to
the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_ and
velocity ranges over which the line emission was summed can be found in Table 3. The beam in the images
is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

34 Tobin et al.





17.0


16.5


16.0


15.5


15.0


+31:14:14.5


17.0


16.5


16.0


15.5


15.0


+31:14:14.5





17.0


16.5


16.0


15.5


15.0


+31:14:14.5


17.0


16.5


16.0


15.5


15.0


+31:14:14.5


|IRAS2B C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|IRAS2B  C18O<br>1.0" (300.0 AU)||||
|IRAS2B  C18O<br>1.0" (300.0 AU)||||
|IRAS2B  C18O<br>1.0" (300.0 AU)||||
|IRAS2B  C18O<br>1.0" (300.0 AU)||||
|IRAS2B  C18O<br>1.0" (300.0 AU)||||
|IRAS2B  C18O<br>1.0" (300.0 AU)||||
|IRAS2B  C18O<br>1.0" (300.0 AU)|3|||
|IRAS2B  C18O<br>1.0" (300.0 AU)|.|||
|IRAS2B  C18O<br>1.0" (300.0 AU)||||


|Col1|O|
|---|---|
|IRAS2B  S<br>1.0" (300.0 AU)|IRAS2B  S<br>1.0" (300.0 AU)|
|57.4<br>RA (J2000|3:28:57.3<br> )|


|RA (J2000)|Col2|Col3|Col4|
|---|---|---|---|
|||||
|IRAS2B  H2CO<br>1.0" (300.0 AU)|IRAS2B  H2CO<br>1.0" (300.0 AU)|IRAS2B  H2CO<br>1.0" (300.0 AU)|IRAS2B  H2CO<br>1.0" (300.0 AU)|
|IRAS2B  H2CO<br>1.0" (300.0 AU)||||
|IRAS2B  H2CO<br>1.0" (300.0 AU)||||
|IRAS2B  H2CO<br>1.0" (300.0 AU)||||
|IRAS2B  H2CO<br>1.0" (300.0 AU)||||
|IRAS2B  H2CO<br>1.0" (300.0 AU)||||
|IRAS2B  H2CO<br>1.0" (300.0 AU)||||
|3:28:57<br>57.4<br>RA (J2000)|3|||
|3:28:57<br>57.4<br>RA (J2000)|.|||
|3:28:57<br>57.4<br>RA (J2000)||||



**Figure** **16.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-36 (NGC 1333 IRAS2B). The integrated intensity
maps are displayed as red and blue contours corresponding to the integrated intensity of line emission red
and blue-shifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum
image. The line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted
contours start at (4,3) _σ_ and increase in (2,3) _σ_ increments for [13] CO and SO,respectively, and the blue-shifted
contours start at (3,3,3) _σ_ and increase in (2,3,2) _σ_ increments for [13] CO, SO, and H 2 CO, respectively. The
line-center contours for C [18] O start at 3 _σ_ and increase by 1 _σ_ increments. The values for _σ_ _red_ and _σ_ _blue_ and
velocity ranges over which the line emission was summed can be found in Table 3. The beam in the images
is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 35



33.0


32.0


31.0


+31:13:30.0


33.0


32.0


31.0


+31:13:30.0





33.0


32.0


31.0


+31:13:30.0


33.0


32.0


31.0


+31:13:30.0




|35/IRAS1 13CO<br>AU)|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)|||||
|35/IRAS113CO<br>  AU)||:2|8:|37|
|35/IRAS113CO<br>  AU)||||.|
|35/IRAS113CO<br>  AU)|||||


|Per-emb-35/IRAS1 C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)||:2|8:|37|
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)||||.|
|Per-emb-35/IRAS1  C18O<br>1.0" (300.0 AU)|||||


|.0 Per-emb-35/IRAS1 SO<br>.0<br>.0<br>.0<br>10"(3000AU)<br>. .<br>37.3 37.2 37.1 3:28:37.<br>RA(J2000)|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|35/IRAS1  SO<br>  AU)|35/IRAS1  SO<br>  AU)|35/IRAS1  SO<br>  AU)|35/IRAS1  SO<br>  AU)|
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|35/IRAS1  SO<br>  AU)|||||
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|37.1<br> (J2000)||:2|8:|37|
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|37.1<br> (J2000)||||.|
|3:28:37.<br>37.1<br>37.2<br>37.3<br>RA (J2000)<br>.0<br>.0<br>.0<br>.0<br>Per-emb-35/IRAS1  SO<br>1.0" (300.0 AU)|37.1<br> (J2000)|||||


|Per-emb-35/IRAS1 H 2CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|Per-emb-35/IRAS1  H2CO<br>1.0" (300.0 AU)|||||
|37.1<br>37.2<br>37.3<br>RA (J2000)|||:2|8:|37|
|37.1<br>37.2<br>37.3<br>RA (J2000)|||||.|
|37.1<br>37.2<br>37.3<br>RA (J2000)||||||



**Figure** **17.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-35 (NGC 1333 IRAS1). The integrated intensity
maps are displayed as red and blue contours corresponding to the integrated intensity of line emission red and
blue-shifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image.
The line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours
start at (3,3,3,3) _σ_ and increase in (2,1,2,2) _σ_ increments and the blue-shifted contours start at (3,3,3,3) _σ_ and
increase in (2,1,2,2) _σ_ increments, respectively. The values inside the parentheses in the previous sentence
correspond to the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_
and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in Table 3. The beam
in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

36 Tobin et al.





56.0


55.0


54.0


+31:07:53.0





56.0


55.0


54.0


+31:07:53.0


|Per-emb-40/B1-a 13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|
|---|---|---|---|
|Per-emb-40/B1-a13CO<br>1.0" (300.0 AU)||||
|Per-emb-40/B1-a13CO<br>1.0" (300.0 AU)||||
|Per-emb-40/B1-a13CO<br>1.0" (300.0 AU)||||
|Per-emb-40/B1-a13CO<br>1.0" (300.0 AU)||||
|Per-emb-40/B1-a13CO<br>1.0" (300.0 AU)||||
|Per-emb-40/B1-a13CO<br>1.0" (300.0 AU)||||
|3:33:16.6<br>16.7<br>16.8<br>RA (J2000)||||
|3:33:16.6<br>16.7<br>16.8<br>RA (J2000)||||
|3:33:16.6<br>16.7<br>16.8<br>RA (J2000)||||


|Per-emb-40/B1-a C18O<br>0"(3000AU)<br>. .|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|Per-emb-40/B1-a  C18O<br>.0" (300.0 AU)|||||
|Per-emb-40/B1-a  C18O<br>.0" (300.0 AU)|||||
|Per-emb-40/B1-a  C18O<br>.0" (300.0 AU)|||||
|Per-emb-40/B1-a  C18O<br>.0" (300.0 AU)|||||
|Per-emb-40/B1-a  C18O<br>.0" (300.0 AU)|||||
|Per-emb-40/B1-a  C18O<br>.0" (300.0 AU)|||||
|3:33:16.6<br>16.7<br>6.8<br>RA (J2000)|||||
|3:33:16.6<br>16.7<br>6.8<br>RA (J2000)|||||
|3:33:16.6<br>16.7<br>6.8<br>RA (J2000)|||||



**Figure** **18.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-40 (B1-a). The integrated intensity maps are
displayed as red and blue contours corresponding to the integrated intensity of line emission red and blueshifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The
line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at 3 _σ_ and increase in 2 _σ_ increments, and the blue-shifted contours start at 3 _σ_ and increase in 2 _σ_ increments.
For C [18] O only the line center velocities are plotted, starting at 4 _σ_ and increasing by 1 _σ_ intervals. The values
for _σ_ _red_ and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in Table 3.
The beam in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.



23.0





22.0


21.0


+30:46:20.0

|L1448IRS1 12CO<br>10"(3000AU)<br>. .|Col2|Col3|
|---|---|---|
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|L1448 IRS112CO<br>1.0" (300.0 AU)|L1448 IRS112CO<br>1.0" (300.0 AU)||
|09.4<br>09.5<br>RA (J2000)|3:25:09.|3|
|09.4<br>09.5<br>RA (J2000)|3:25:09.||
|09.4<br>09.5<br>RA (J2000)|3:25:09.||



**Figure** **19.** Integrated intensity maps of [12] CO toward L1448 IRS1. The integrated intensity maps are
displayed as red and blue contours corresponding to the integrated intensity of line emission red and blueshifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The
line emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at 3 _σ_ and increase in 3 _σ_ increments, and the blue-shifted contours start at 3 _σ_ and increase in 3 _σ_ increments.
The values for _σ_ _red_ and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in
Table 3. The beam in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 37


48.0


47.0


46.0



+30:32:45.0





|EDJ2009-269 12CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)|9|||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||
|EDJ2009-26912CO<br>1.0" (300.0 AU)||||||


**Figure** **20.** Integrated intensity maps of [12] CO toward EDJ2009-269. The integrated intensity maps are
displayed as red and blue contours corresponding to the integrated intensity of line emission red and blueshifted with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image.
The line emission shows evidence for a velocity gradient consistent with rotation. The integrated intensity
contours start at 3 _σ_ and increase in 3 _σ_ increments. The values for _σ_ and the velocity range over which the
line emission was summed can be found in Table 3. The beam in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

38 Tobin et al.





23.0


22.0


21.0


+30:45:20.0


23.0


22.0


21.0


+30:45:20.0





23.0


22.0


21.0


+30:45:20.0


23.0


22.0


21.0


+30:45:20.0


|L1448IRS3A 13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||
|L1448 IRS3A13CO<br>1.0" (300.0 AU)|||||


|L1448IRS3A C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)|4|||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||
|L1448 IRS3A  C18O<br>1.0" (300.0 AU)||||||


|L1448IRS3A SO<br>0<br>0<br>0<br>10"(3000AU)<br>0 . .<br>36.6 36.5 3:25:36.4<br>RA(J2000)|L1448IRS3A SO<br>10"(3000AU)<br>. .|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||
|3:25:36.4<br>36.5<br>36.6<br>RA (J2000)<br>0<br>0<br>0<br>0<br>L1448 IRS3A  SO<br>1.0" (300.0 AU)|L1448 IRS3A  SO<br>1.0" (300.0 AU)|||||


|L1448IRS3AH CO<br>2<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|L1448 IRS3A H2CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3A H2CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3A H2CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3A H2CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3A H2CO<br>1.0" (300.0 AU)||||||
|L1448 IRS3A H2CO<br>1.0" (300.0 AU)||||||
|3:25:36.<br>36.5<br>36.6<br>RA (J2000)|4|||||
|3:25:36.<br>36.5<br>36.6<br>RA (J2000)||||||
|3:25:36.<br>36.5<br>36.6<br>RA (J2000)||||||



**Figure** **21.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward L1448 IRS3A. The integrated intensity maps are displayed
as red and blue contours corresponding to the integrated intensity of line emission red and blue-shifted
with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The line
emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at (3,4,3,3) _σ_ and increase in (2,1,2,3) _σ_ increments, and the blue-shifted contours start at (3,3,3,3) _σ_ and
increase in (2,1,2,3) _σ_ increments. The values inside the parentheses in the previous sentence correspond to
the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_ and
velocity ranges over which the line emission was summed can be found in Table 3. The beam in the images
is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 39



37.0


36.0


35.0


+32:01:34.0


37.0


36.0


35.0


+32:01:34.0





37.0


36.0


35.0


+32:01:34.0


+32:01:34.0




|Per-emb-8 13CO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||
|Per-emb-813CO<br>1.0" (300.0 AU)||||||


|Per-emb-8 C18O<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||
|Per-emb-8  C18O<br>1.0" (300.0 AU)|||||


|Per-emb-8 SO<br>10"(3000AU)<br>. .|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|Per-emb-8  SO<br>1.0" (300.0 AU)|Per-emb-8  SO<br>1.0" (300.0 AU)|Per-emb-8  SO<br>1.0" (300.0 AU)|Per-emb-8  SO<br>1.0" (300.0 AU)|Per-emb-8  SO<br>1.0" (300.0 AU)|Per-emb-8  SO<br>1.0" (300.0 AU)|
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|Per-emb-8  SO<br>1.0" (300.0 AU)||||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)||||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)||||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)||||||


|37.0 Per-emb-8 H 2CO<br>36.0<br>35.0<br>34.0<br>10"(3000AU)<br>. .<br>44.1 44.0 3:44:43.9<br>RA(J2000)|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||
|3:44:43.9<br>44.0<br>44.1<br>RA (J2000)<br>34.0<br>35.0<br>36.0<br>37.0<br>Per-emb-8  H2CO<br>1.0" (300.0 AU)|Per-emb-8  H2CO<br>1.0" (300.0 AU)|||||



**Figure** **22.** Integrated intensity maps of [13] CO (top left panel), C [18] O (top right panel), SO (bottom left
panel), and H 2 CO (bottom right panel) toward Per-emb-8. The integrated intensity maps are displayed
as red and blue contours corresponding to the integrated intensity of line emission red and blue-shifted
with respect to the system velocity. The contours are overlaid on the 1.3 mm continuum image. The line
emission shows evidence for a velocity gradient consistent with rotation. The red-shifted contours start
at (3,4,3,3) _σ_ and increase in (2,1,2,2) _σ_ increments, and the blue-shifted contours start at (3,3,3,3) _σ_ and
increase in (2,1,2,2) _σ_ increments. The values inside the parentheses in the previous sentence correspond to
the [13] CO, C [18] O, SO, and H 2 CO integrated intensity maps, respectively. The values for _σ_ _red_ and _σ_ _blue_ and
velocity ranges over which the line emission was summed can be found in Table 3. The beam in the images
is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

40 Tobin et al.









+31:18:29.0


38.0


36.0


34.0


32.0


+30:45:30.0



13:00.0


+30:12:58.0


+31:16:00.0







+30:45:10.0


|Per-emb-17/RNO 15 12CO<br>6.0<br>4.0<br>2.0<br>0.0<br>10"(3000AU)<br>. .<br>8.0<br>39.4 39.2 39.0 3:27:38.8<br>RA(J2000)|Col2|
|---|---|
|3:27:38.8<br>39.0<br>39.2<br>39.4<br>RA (J2000)<br>8.0<br>0.0<br>2.0<br>4.0<br>6.0<br>Per-emb-17/RNO 1512CO<br>1.0" (300.0 AU)|3:27:38.8<br>39.0<br> 2000)|
|03.8<br>04.0<br>RA (J<br>0.0<br>2.0<br>4.0<br>6.0<br>8.0<br>SVS13<br>1.0" (300.0 AU|A12CO<br>  )|
|03.8<br>04.0<br>RA (J<br>0.0<br>2.0<br>4.0<br>6.0<br>8.0<br>SVS13<br>1.0" (300.0 AU|3:29:03.4<br>03.6<br> 2000)|



**Figure** **23.** ALMA [12] CO integrated intensity maps toward all protostars where [12] CO appears to trace
outflowing gas from the protostellar system. The integrated intensity maps are displayed as red and blue
contours corresponding to the integrated intensity of line emission red and blue-shifted with respect to
the system velocity. The contours are overlaid on the 1.3 mm continuum image. The line emission shows
evidence for a velocity gradient consistent with rotation. The red-shifted contours start at X _σ_ and increase
in X _σ_ increments, and the blue-shifted contours start at X _σ_ and increase in X _σ_ increments. The values for
_σ_ _red_ and _σ_ _blue_ and velocity ranges over which the line emission was summed can be found in Table 3. The
beam in the images is approximately 0 _[′′]_ _._ 36 _×_ 0 _[′′]_ _._ 26.

ALMA Perseus Multiplicity 41





18.0


15.0


12.0


09.0


+30:45:06.0


36.0


34.0


32.0


30.0


+31:13:28.0


36.0


34.0


32.0


30.0


+32:01:28.0





40.0


38.0


36.0


34.0


+31:14:32.0


58.0


56.0


54.0


+31:07:52.0


34.0


33.0


32.0


31.0


30.0


29.0


+31:13:28.0



**Figure** **24.** Same as Figure 23.

42 Tobin et al.











24.0


23.0


22.0


21.0


+30:45:20.0



+32:01:33.0



**Figure** **25.** Same as Figure 23.


**Figure** **26.** Histograms of companion frequency versus separation for multiple sources in Perseus; this is an
updated version of the plot shown in Tobin et al. (2016b), but with the average distance to Perseus revised
to 300 pc. The top left panel shows the distribution for all sources in the sample; the top middle and top
right panels break the distribution into sources that are only comprised of Class 0 protostars and Class I
protostars, respectively. The bottom left panel shows only the multiple systems comprised of Class 0 and I
sources, the bottom middle shows the separation distribution of all systems with a Class 0 primary source
and the bottom left panel shows the same, but with a Class I primary. The systems comprised of a Class 0
and Class I protostar are not included in the Class I plot in the bottom right. Note the apparent bi-modal
distribution for the full sample and Class 0 samples and the apparent deficit of wide companions for the
Class I systems. In all plots, the dashed curve is the Gaussian fit to the field star separation distribution
from Raghavan et al. (2010) and the vertical dot-dashed line corresponds to the approximate resolution limit
of 20 AU.

ALMA Perseus Multiplicity 43

44 Tobin et al.


**Table** **2.** Compact Masses vs. Extended Masses


Source Gaussian mass Extended Mass


(M _⊙_ ) (M _⊙_ )


Per-emb-2 0.69 _±_ 0.01 0.68 _±_ 0.04

Per-emb-12 2.3 _±_ 0.04 3.9 _±_ 0.2

Per-emb-12-A 1.8 _±_ 0.04 _· · ·_

Per-emb-12-B 0.53 _±_ 0.02 _· · ·_

Per-emb-17 0.054 _±_ 0.001 0.066 _±_ 0.01

Per-emb-17-A 0.031 _±_ 0.0005 _· · ·_

Per-emb-17-B 0.024 _±_ 0.0007 _· · ·_

Per-emb-18 0.17 _±_ 0.002 0.18 _±_ 0.01

Per-emb-21 0.06 _±_ 0.0005 0.063 _±_ 0.005

Per-emb-22 0.053 _±_ 0.001 0.088 _±_ 0.014

Per-emb-22-A 0.041 _±_ 0.0009 _· · ·_

Per-emb-22-B 0.012 _±_ 0.0002 _· · ·_

Per-emb-27 0.24 _±_ 0.003 0.35 _±_ 0.03

Per-emb-27-A 0.204 _±_ 0.0024 _· · ·_

Per-emb-27-B 0.032 _±_ 0.003 _· · ·_

Per-emb-33 0.33 _±_ 0.003 0.89 _±_ 0.04

Per-emb-33-A 0.009 _±_ 0.001 _· · ·_

Per-emb-33-B 0.04 _±_ 0.002 _· · ·_

Per-emb-33-C 0.2 _±_ 0.002 _· · ·_

L1448NW 0.08 _±_ 0.0009 0.1 _±_ 0.009

L1448NW-A 0.060 _±_ 0.0007 _· · ·_

L1448NW-B 0.018 _±_ 0.0003 _· · ·_

Per-emb-44 0.31 _±_ 0.002 0.48 _±_ 0.02

Per-emb-44-A 0.12 _±_ 0.001 _· · ·_

Per-emb-44-B 0.19 _±_ 0.002 _· · ·_

SVS13B 0.27 _±_ 0.003 0.33 _±_ 0.03

SVS13A2 0.017 _±_ 0.002 0.002 _±_ 0.005

RAC1999 VLA20 0.005 _±_ 0.001 0.003 _±_ 0.002

Per-emb-8 0.15 _±_ 0.003 0.15 _±_ 0.01

Per-emb-8 Inner Disk 0.11 _±_ 0.0009 _· · ·_

Per-emb-8 Outer Disk 0.041 _±_ 0.003 _· · ·_

Per-emb-35-A 0.027 _±_ 0.0005 _· · ·_

Per-emb-35-B 0.020 _±_ 0.0005 _· · ·_

Per-emb-36 0.17 _±_ 0.001 0.17 _±_ 0.005

Per-emb-36-A 0.15 _±_ 0.001 _· · ·_

Per-emb-36-B 0.015 _±_ 0.0009 _· · ·_

Per-emb-40-A 0.019 _±_ 0.0003 _· · ·_

Per-emb-40-B 0.0017 _±_ 0.0002 _· · ·_

Per-emb-48-A 0.005 _±_ 0.0005 0.005 _±_ 0.002

Per-emb-48-B _<_ 0.0005 _· · ·_

Per-emb-49-A 0.022 _±_ 0.0005 _· · ·_

Per-emb-49-B 0.005 _±_ 0.0003 _· · ·_

Per-emb-55-A 0.003 _±_ 0.0007 _· · ·_

Per-emb-55-B 0.0007 _±_ 0.0003 _· · ·_

L1448IRS1-A 0.088 _±_ 0.001 _· · ·_

L1448IRS1-B 0.007 _±_ 0.0009 _· · ·_

L1448IRS3A 0.12 _±_ 0.005 0.13 _±_ 0.01

L1448IRS3A Inner Disk 0.02 _±_ 0.001 _· · ·_

L1448IRS3A Outer Disk 0.1 _±_ 0.004 _· · ·_

EDJ2009-269-A 0.014 _±_ 0.0003 _· · ·_

EDJ2009-269-B 0.01 _±_ 0.0003 _· · ·_

ALMA Perseus Multiplicity 45

46 Tobin et al.

ALMA Perseus Multiplicity 47


**Table** **5.** Class 0 Multiple Systems


Source Separation Separation Flux Difference Type


( _[′′]_ ) (AU) (Log [F 1 /F 2 ])


Per-emb-2 0.080 _±_ 0.006 24.0 _±_ 1.7 0.17 _±_ 0.15 Class 0

Per-emb-18 0.085 _±_ 0.004 25.6 _±_ 1.2 -0.02 _±_ 0.12 Class 0

Per-emb-5 0.097 _±_ 0.006 29.1 _±_ 1.8 0.26 _±_ 0.07 Class 0

L1448NW 0.251 _±_ 0.004 75.3 _±_ 1.7 0.17 _±_ 0.03 Class 0

Per-emb-33 0.264 _±_ 0.008 79.2 _±_ 2.3 0.12 _±_ 0.05 Class 0

Per-emb-17 0.278 _±_ 0.014 83.3 _±_ 4.0 0.75 _±_ 0.08 Class 0

Per-emb-44 0.300 _±_ 0.003 90.0 _±_ 0.9 0.48 _±_ 0.02 Class 0

Per-emb-27 0.620 _±_ 0.003 186.0 _±_ 0.9 0.75 _±_ 0.03 Class 0

Per-emb-22 0.751 _±_ 0.004 225.4 _±_ 1.3 0.51 _±_ 0.05 Class 0

Per-emb-33 0.795 _±_ 0.004 238.4 _±_ 1.3 0.33 _±_ 0.04 Class 0

Per-emb-12 1.830 _±_ 0.002 548.9 _±_ 0.5 1.04 _±_ 0.02 Class 0

Per-emb-11 2.951 _±_ 0.008 885.4 _±_ 2.2 0.93 _±_ 0.08 Class 0

Per-emb-44+SVS13A2 5.314 _±_ 0.004 1594.2 _±_ 1.2 1.78 _±_ 0.03 Class 0/I
Per-emb-32 6.066 _±_ 0.022 1820.0 _±_ 6.5 -0.16 _±_ 0.27 Class 0/I

Per-emb-33+L1448IRS3A 7.317 _±_ 0.004 2195.2 _±_ 1.2 -0.24 _±_ 0.02 Class 0-Class I

Per-emb-26+Per-emb-42 8.104 _±_ 0.005 2431.3 _±_ 1.6 1.97 _±_ 0.03 Class 0-Class I

Per-emb-11 9.469 _±_ 0.025 2840.6 _±_ 7.6 0.76 _±_ 0.13 Class 0

Per-emb-8+Per-emb-55 9.557 _±_ 0.013 2867.2 _±_ 3.8 2.38 _±_ 0.10 Class 0-Class I

Per-emb-37+EDJ2009+235 10.556 _±_ 0.009 3166.7 _±_ 2.9 1.53 _±_ 0.11 Class 0-Class II

Per-emb-13+IRAS4B’ 10.654 _±_ 0.005 3196.2 _±_ 1.6 0.81 _±_ 0.02 Class 0-Class 0

Per-emb-21+Per-emb-18 13.252 _±_ 0.004 3975.7 _±_ 1.3 -0.44 _±_ 0.02 Class 0-Class 0

B1-bS+Per-emb-41 13.957 _±_ 0.014 4187.1 _±_ 4.2 2.08 _±_ 0.09 Class 0-Class 0/I
Per-emb-44+SVS13B 14.932 _±_ 0.002 4479.7 _±_ 0.7 0.40 _±_ 0.01 Class 0/I-Class 0

Per-emb-16+Per-emb-28 16.063 _±_ 0.037 4818.9 _±_ 11.1 -0.05 _±_ 0.17 Class 0-Class 0

B1-bN+B1-bS 17.395 _±_ 0.009 5218.4 _±_ 2.6 0.31 _±_ 0.03 Class 0-Class 0

Per-emb-33+L1448NW 21.503 _±_ 0.004 6450.8 _±_ 1.3 -0.23 _±_ 0.02 Class 0-Class 0

Per-emb-18+Per-emb-49 27.474 _±_ 0.007 8242.3 _±_ 2.0 0.33 _±_ 0.03 Class 0-Class I

Per-emb-12+Per-emb-13 29.739 _±_ 0.002 8921.7 _±_ 0.7 1.04 _±_ 0.01 Class 0-Class 0

Per-emb-36+Per-emb-27 31.420 _±_ 0.001 9426.0 _±_ 0.4 0.15 _±_ 0.01 Class 0-Class I

Per-emb-6+Per-emb-10 31.947 _±_ 0.005 9584.2 _±_ 1.6 -0.28 _±_ 0.03 Class 0-Class 0

Per-emb-37+EDJ2009+233 33.704 _±_ 0.006 10111.3 _±_ 1.7 -0.62 _±_ 0.04 Class 0-Class II

Per-emb-44+SVS13C 34.528 _±_ 0.001 10358.5 _±_ 0.4 -0.21 _±_ 0.01 Class 0/I-Class 0
Per-emb-32+EDJ2009+366 36.605 _±_ 0.010 10981.6 _±_ 3.1 -1.31 _±_ 0.11 Class 0/I-Class II


Note—This table includes Class 0 + Class 0, Class 0 + Class I, and Class 0 + Class II multiple systems.
The flux difference is calculated in the 9 mm band. The distance has been revised to 300 pc for the
physical separation distance.

48 Tobin et al.


**Table** **6.** Class I Multiple Systems


Source Separation Separation Flux Difference


( _[′′]_ ) (AU) (Log [F 1 /F 2 ])


Per-emb-36 0.311 _±_ 0.005 93.4 _±_ 1.6 0.80 _±_ 0.02

Per-emb-49 0.313 _±_ 0.009 93.8 _±_ 2.6 0.46 _±_ 0.11

Per-emb-48 0.346 _±_ 0.019 103.7 _±_ 5.7 0.06 _±_ 0.17

Per-emb-40 0.391 _±_ 0.022 117.4 _±_ 6.7 0.94 _±_ 0.19

Per-emb-55 0.618 _±_ 0.009 185.3 _±_ 2.6 0.14 _±_ 0.07

EDJ2009-183 1.025 _±_ 0.028 307.6 _±_ 8.3 0.45 _±_ 0.13

L1448IRS1 1.424 _±_ 0.015 427.0 _±_ 4.6 1.02 _±_ 0.09

Per-emb-35 1.908 _±_ 0.003 572.3 _±_ 0.9 0.23 _±_ 0.04

EDJ2009-156 3.107 _±_ 0.011 932.1 _±_ 3.3 0.17 _±_ 0.13

Per-emb-58+Per-emb-65 28.878 _±_ 0.023 8663.3 _±_ 6.9 -0.44 _±_ 0.13


Note—This table includes only Class I + Class I multiple systems. The flux
difference is calculated in the 9 mm band. The distance has been revised to
300 pc for the physical separation distance.


**Table** **7.** Class II Multiple Systems


Source Separation Separation Flux Difference


( _[′′]_ ) (AU) (Log [F 1 /F 2 ])


EDJ2009-269 0.524 _±_ 0.007 157.3 _±_ 2.1 0.12 _±_ 0.08

EDJ2009-156 3.107 _±_ 0.011 932.1 _±_ 3.3 0.17 _±_ 0.13


Note—This table includes only Class II + Class II multiple systems. The flux difference is calculated in the 9 mm band. The
distance has been revised to 300 pc for the physical separation
distance.


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Red/blue integrated-intensity moment maps; measure PA of velocity gradient vs outflow; within 30 deg of orthogonal = disk rotation",
  "failed_quote": "that is within 30 _[°]_ of orthogonal to the outflow direction, we classify it as\nbeing consistent with disk rotation."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "PA uncertainty ±10 deg",
  "failed_quote": "we\nestimate that this is _±_ 10 _[°]_"
 }
]
```
