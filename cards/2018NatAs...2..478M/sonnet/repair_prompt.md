# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018NatAs...2..478M\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## **The unexpectedly large proportion of high-mass star-** **forming cores in a Galactic mini-starburst**

F. Motte [1][,][2][ ⋆], T. Nony [1][ ⋆], F. Louvet [3][ ⋆], K. A. Marsh [4], S. Bontemps [5], A. P. Whitworth [4], A. Men’shchikov [2],
Q. Nguyen Luong [6][,][7], T. Csengeri [8], A. J. Maury [2], A. Gusdorf [9], E. Chapillon [5][,][10], V. K¨onyves [2], P.
Schilke [11], A. Duarte-Cabral [4], P. Didelon [2] & M. Gaudel [2]


1 _Universit´e_ _Grenoble_ _Alpes,_ _CNRS,_ _Institut_ _de_ _Plan´etologie_ _et_ _d’Astrophysique_ _de_ _Grenoble,_ _F-_
_38000 Grenoble, France_
2 _AIM Paris-Saclay/D´epartement d’Astrophysique, CEA, CNRS, Univ. Paris Diderot, CEA-Saclay,_
_F-91191 Gif-sur-Yvette Cedex, France_
3 _Department of Astronomy, Universidad de Chile, Las Condes, Santiago, Chile_
4 _School_ _of_ _Physics_ _and_ _Astronomy,_ _Cardiff_ _University,_ _Queens_ _Buildings,_ _The_ _Parade,_ _Cardiff_
_CF24 3AA, UK_
5 _OASU/Laboratoire_ _d’Astrophysique_ _de_ _Bordeaux,_ _Univ._ _Bordeaux,_ _CNRS,_ _F-33615_ _Pessac,_
_France_
6 _Korea_ _Astronomy_ _and_ _Space_ _Science_ _Institute,_ _776_ _Daedeok_ _daero,_ _Yuseoung,_ _Daejeon_ _34055,_
_Republic of Korea_
7 _NAOJ_ _Chile_ _Observatory,_ _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1_ _Osawa,_ _Mitaka,_
_Tokyo 181-8588, Japan_
8 _Max-Planck-Institut f¨ur Radioastronomie, Auf dem H¨ugel 69, 53121 Bonn, Germany_
9 _LERMA, Observatoire de Paris, PSL Research University, CNRS, Sorbonne Universit´es, UPMC_
_Univ._ _Paris 06,_ _Ecole normale sup´erieure, F-75005, Paris, France_ _[´]_
10 _Institut de RadioAstronomie Millim´etrique (IRAM), 300 rue de la Piscine, F-38406 Saint Martin_
_d’H`eres, France_
11 _I. Physik._ _Institut, University of Cologne, 50937 K¨oln, Germany_


**Understanding the processes that determine the stellar Initial Mass Function (IMF) is**
**1**
**a critical unsolved problem, with profound implications for many areas of astrophysics** **.** **In**
**molecular** **clouds,** **stars** **are** **formed** **in** **cores,** **gas** **condensations** **which** **are** **su** ffi **ciently** **dense**
**that gravitational collapse converts a large fraction of their mass into a star or small clutch**
**of stars.** **In nearby star-formation regions, the core mass function (CMF) is strikingly similar**
**2–5**
**to the IMF, suggesting that the shape of the IMF may simply be inherited from the CMF** **.**
**Here we present** 1.3 mm **observations, obtained with ALMA, the world’s largest interferom-**
**eter,** **of** **the** **active** **star-formation** **region** **W43-MM1,** **which** **may** **be** **more** **representative** **of**
**6,7**
**the** **Galactic-disk** **regions** **where** **most** **stars** **form** **.** **The** **unprecedented** **resolution** **of** **these**
**observations reveals, for the first time, a statistically robust CMF at high masses, with a slope**
**that is markedly shallower than the IMF. This seriously challenges our understanding of the**
**origin of the IMF.**


1

The IMF, giving the relative numbers of stars born with different masses, between ∼ 0.08 M ⊙
**8,9**
and ∼ 100 M ⊙, appears to be universal, although there are a few claims to the contrary, espe**10,11**
cially in young massive clusters . In nearby star-formation regions, stars with masses between
∼ 0.08 M ⊙ and ∼ 5 M ⊙ are observed to form in cores, and the CMF in these regions has an approx                                imately log-normal shape with a power-law tail at higher masses (∼ M ⊙ ), very similar to the IMF,
**2–5**
but with the peak shifted to higher masses by a factor 1/ϵ ∼ 2.5 ± 1 . This suggests that the shape
of the IMF is determined by the processes that determine the CMF, in which case there must be
an approximately self-similar mapping from core mass to stellar mass, with a very small variance
(see Methods). However, nearby star-formation regions are probably not representative of the re**12**
gions where most stars are formed, _and_ they do not form massive stars (∼ 8 M ⊙ to ∼ 100 M ⊙ ) .
Previous attempts to resolve cores in high-mass star-formation regions have suffered from poor
**13,14** **14–16**
statistics, and therefore have not allowed a critical comparison of the CMF and IMF .


W43-MM1 is a massive cloud (∼ 2 × 10 [4] M ⊙ ) located at the tip of the Galactic bar, a very rich
**6,7,17** **18**
region in terms of cloud concentration and star formation activity, ∼ 5.5 kpc from the Sun .
Shock tracing lines like SiO are detected throughout this cloud, testifying to the prevalance of
**6,19**
inflowing and colliding gas streams . The large densities in W43-MM1, traced at high angular
resolution by millimetre continuum radiation, suggest it will form a massive star cluster in the near
future **7** . We have used ALMA to image the complete W43-MM1 cloud (∼ 3 pc 2 ) at 1.3 mm (see
Supplementary Fig. 1), with unprecedented resolution (∼ 2, 400 AU), and hence to identify a large
sample of individual cores, with a broad and previously unmatched range of masses.


Since the 1.3 mm map of W43-MM1 has a dynamic range of 30 in physical scale, and 4,000
**20**
in flux, we use the _getsources_ algorithm to identify and characterise cores. _getsources_ decomposes cloud emission into a multi-resolution data-cube; two cube dimensions give position on
the sky, and the third dimension is the physical scale of cloud substructure. Cores are identified
at small scales, and their positions, spatial extents (best-fitting ellipses at half-maximum), peak
and integrated fluxes (corrected for local background), masses, and mean densities are computed
(see Supplementary Table 1). Fig. 1 shows the elliptical outlines of the 131 cores returned by
_getsources_, of which 94 are deemed to be very robust (significance, Sig ≥ 7). The cores have diameters ranging from ∼ 1, 300 AU to ∼ 3, 500 AU once deconvolved with the 0.44 [′′] (or ∼ 2, 400 AU)
telescope beam; masses ranging from ∼ 1 M ⊙ to ∼ 100 M ⊙ ; and mean H 2 densities ranging from
∼ 10 [7] cm [−][3] to ∼ 10 [10] cm [−][3] . Monte-Carlo extraction simulations indicate that the sample is 90%
complete down to ∼ 1.6 M ⊙ (see Methods).


The blue histogram in Fig. 2a displays the differential CMF of W43-MM1, _dN_ / _d_ log( _M_ ),
**21**
giving the number of cores in uniformly distributed but variably sized logarithmic bins of mass .
The blue histogram in Fig. 2b displays the cumulative CMF of W43-MM1, _N_ (> log( _M_ )), giving
the number of cores with _M_ core larger than _M_ . If these histograms are truncated below the 90%
completeness limit (∼ 1.6 M ⊙ ), thereby reducing the sample to 105 cores, they can both be fitted


2

with power-laws: _dN_ / _d_ log( _M_ ) ∝ _M_ [γ] [di][ff] with γ diff ≃−0.90 ± 0.06, and _N_ (> log( _M_ )) ∝ _M_ [γ] [cumul] with
γ cumul ≃−0.96 ± 0.02 (red lines on 2a and 2b). For comparison, the magenta lines on Figs. 2a
and 2b show the slope of the IMF at masses larger than ∼ 1 M ⊙, which for both the differential and
**9,22**
cumulative forms of the IMF is −1.35 .The range of core masses from ∼ 1.6 M ⊙ to ∼ 100 M ⊙
corresponds to a range of stellar masses smaller by a factor 1/ϵ ∼ 2.5 (i.e. stellar masses from
                                      ∼ 0.6 M ⊙ to ∼ 40 M ⊙ ), allowing a robust comparison with the higher-mass (∼ M ⊙ ) IMF. The
result is stable against variations in the temperature model, dust emissivity, extraction algorithm,
and reduction technique (see Supplementary Table 2). We conclude that, at masses larger than
∼ 1.6 M ⊙, the CMF in W43-MM1 is markedly flatter than the IMF. This result seriously challenges
the widespread assumption that the shape of the IMF is inherited directly from the CMF.


The main uncertainty on the CMF derives from the estimation of core masses, using their
measured 1.3 mm continuum fluxes (see Methods). For the most massive cores, we use a 1.3 mm

∼
image based on the signal in a narrow composite band ( 65 MHz wide) that is not contaminated
by line emission. For the lower mass cores (the majority), we use an image based on the signal
in the full band (∼ 1.9 GHz wide), since line contamination for low-mass cores is expected to
be negligible (see _C_ line in Supplementary Table 1). Variations in dust emissivity are presumed
to be small among the W43-MM1 cores, since 90% of them have uniformly high mean densities
(¯ _n_ H2 ∼ 3×10 [7] −3×10 [8] cm [−][3] ) and warm temperatures ( _T_ [¯] dust ∼ 23±2 K) (see Supplementary Table 1).
The main source of uncertainty is the dust temperature, since this is critical for converting flux into
mass. Fig. 3 displays the mean dust temperatures used for estimating core masses. A mean line-of**6**
sight dust temperature is estimated using _Herschel_ 70 to 500 µm images, APEX 350 and 870 µm
**18** **7**
images, and mosaics obtained with the ALMA (present data) and IRAM interferometers at
**23**
1.3 and 3 mm respectively. By applying the Bayesian PPMAP procedure, we obtain columndensity maps in different dust-temperature slices. The mean dust temperature in each pixel is
then a column-density weighted average along that line of sight. However, in the vicinity of ten
**24,25**
hot cores (of which three have been identified previously ), the local heating is not properly
traced by the 2.5 [′′] -resolution PPMAP temperature image. Here, we divide the total luminosity
of the W43-MM1 cloud (∼ 2 × 10 [4] L ⊙ ) between the cores in proportion to their associated line
contamination in the wide 1.3 mm band. We then use the individual luminosities, _L_ ⋆ < 10 L ⊙ up to
∼ 10 [4] L ⊙ and PPMAP background temperatures to estimate the core dust temperatures ( _T_ [¯] dust ∼ 20 K
to ∼ 90 K) and their uncertainties (see Supplementary Table 1), using an approximate radiation
**26**
transport model . Monte-Carlo simulations indicate that the mass uncertainties in Supplementary
Table 1 correspond to a 5σ uncertainty of ±0.13 in the slope of the CMF (see Methods and blackhatched area in Fig. 2b).


The fidelity of the CMF also depends on whether we have correctly identified cores, i.e.
structures that (a) are gravitationally bound, and are therefore destined to spawn stars, and (b)
already contain most of the mass that will eventually end up in those stars. Parenthetically, we
note that core masses probably grow with time, due to inflowing gas streams like those observed
**27–29**
towards many massive cores . In respect of criterion (a), studies of gravitational boundedness,


3

using [13] CS (5–4) lines from the present ALMA project to determine internal velocity dispersions,
indicate that W43-MM1 cores with _M_ core - 12 M ⊙ are secure, but the status of lower-mass cores
would benefit from further investigation. In respect of criterion (b), the low luminosity-to-mass
**17** ¯
ratio of the whole region, _L_ bol / _M_ ∼ 5 L ⊙ /M ⊙, and the low mean temperature, _T_ dust ∼ 20 K (see
Fig. 3) imply that the region is young. We note that the two most massive cores may assimilate
further mass from their dense surroundings, and eventually form stars of ∼ 100 M ⊙, with _L_ ⋆ ∼
10 [5] L ⊙ on the Main Sequence. However, currently they are 10 − 50 times less luminous. We
conclude that any protostars embedded within the W43-MM1 cores are at the very beginning of
their accretion phase, and therefore contain only a small fraction of their final stellar mass.


Finally, the fidelity of the CMF depends on the completeness of the core sample. Due to increased source and background confusion in the denser parts of the cloud, the core sample is 90%
complete above ∼ 1.6 M ⊙ outside the main filament, and above ∼ 4.5 M ⊙ within it (see Supplementary Fig. 2). As in previous CMF evaluations, we use the median of the detection thresholds, here
∼ 1.6 M ⊙, but even with the more conservative threshold of ∼ 4.5 M ⊙, the CMF is still markedly
shallower than the IMF (see Supplementary Table 2). The 5σ uncertainty in the fit to the CMF in
Fig. 2b (black-hatched area) reflects the above assumptions, along with contributions from the data
**29**
reduction method, the extraction algorithm, and the effects of source and background confusion
(see Methods).


Due to the high sensitivity and resolution of our ALMA 1.3 mm image of the W43-MM1
cloud, we have been able to obtain, for the first time, a robust CMF covering masses in the range
from ∼ 1.6 M ⊙ to ∼ 100 M ⊙, and hence to conclude that the CMF in W43-MM1 is much shallower
than the higher-mass (∼ - M ⊙ ) IMF, viz. _N_ (> log( _M_ )) ∝ _M_ γ with γ ≃−0.96 ± 0.13 instead of
γ ≃−1.35. This is in stark contrast with previous robust evaluations of the CMF in other regions
**2–5**
and at lower masses, where the CMF appears to be very similar to the IMF . Scenarios that
might explain our result and still allow the shape of the IMF to be inherited from the shape of the
CMF, with an approximately self-similar mapping, fall into two broad categories. [A] W43-MM1
**10,11**
is not representative of the environments in which most low-mass stars form ; to obtain the
complete IMF, stars formed in environments like W43-MM1 must be mixed with stars formed
in environments, which contain a higher proportion of low-mass cores. However, this scenario
is hard to justify, if the local IMF observed in extreme star-formation regions is similar to the
**8**
universal IMF . [B] Massive cores are over-represented in W43-MM1. _Either_ [B1] massive cores
**30** **12**
live significantly longer than lower-mass cores, but current lifetime derivations suggest the
opposite. _Or_ [B2] star formation in regions like W43-MM1 is prolonged, and massive cores and
the stars they spawn only form during a short period (probably near the beginning), whilst lowermass cores and low-mass stars form over a much longer period; this seems unlikely, because it
would require the low-mass period to be nearly ten times longer than the high-mass period, but
it cannot be ruled out. If none of the above scenarios obtains, our results imply that the mapping
from the CMF to the IMF is not statistically self-similar. Either higher-mass cores must convert a
**14**
smaller fraction of their mass into stars than lower-mass cores (which seems unlikely ); or they


4

must spawn more stars, with a wider logarithmic range of masses (which seems more likely); or
some combination of these possibilities. The shape of the IMF, at least at masses greater than
∼ M ⊙, is then not simply inherited from the shape of the CMF and the processes that determine the
IMF remain to be determined.


**Online** **Content.** Methods, along with Supplementary display items, are available in the online
version of the paper. References unique to these sections appear only in the online paper.


**References**


1. Offner, S. S. R. _et al._ The Origin and Universality of the Stellar Initial Mass Function. _Proto-_
_stars and Planets VI_ 53–75 (2014).


2. Motte, F., Andr´e, P. & Neri, R. The initial conditions of star formation in the rho Ophiuchi
main cloud: wide-field millimeter continuum mapping. _A_ & _A_ **336**, 150–172 (1998).


3. Testi, L. & Sargent, A. I. Star Formation in Clusters: A Survey of Compact Millimeter-Wave
Sources in the Serpens Core. _ApJ Lett._ **508**, L91–L94 (1998).


4. Enoch, M. L. _et al._ The Mass Distribution and Lifetime of Prestellar Cores in Perseus, Serpens,
and Ophiuchus. _ApJ_ **684**, 1240–1259 (2008).


5. K¨onyves, V. _et al._ A census of dense cores in the Aquila cloud complex: SPIRE/PACS observations from the Herschel Gould Belt survey. _A_ & _A_ **584**, A91 (2015).


6. Nguyen Luong, Q. _et_ _al._ Low-velocity Shocks Traced by Extended SiO Emission along the
W43 Ridges: Witnessing the Formation of Young Massive Clusters. _ApJ_ **775**, 88 (2013).


7. Louvet, F. _et_ _al._ The W43-MM1 mini-starburst ridge, a test for star formation efficiency
models. _A_ & _A_ **570**, A15 (2014).


8. Bastian, N., Covey, K. R. & Meyer, M. R. A Universal Stellar Initial Mass Function? A
Critical Look at Variations. _ARA_ & _A_ **48**, 339–389 (2010).


9. Kroupa, P. _et al._ The Stellar and Sub-Stellar Initial Mass Function of Simple and Composite
Populations. In Oswalt, T. D. & Gilmore, G. (eds.) _Planets, Stars and Stellar Systems. Volume_
_5:_ _Galactic Structure and Stellar Populations_, 115 (2013).


10. Harayama, Y., Eisenhauer, F. & Martins, F. The Initial Mass Function of the Massive Starforming Region NGC 3603 from Near-Infrared Adaptive Optics Observations. _ApJ_ **675**, 1319–
1342 (2008).


11. Maia, F. F. S., Moraux, E. & Joncour, I. Young and embedded clusters in Cygnus-X: evidence
for building up the initial mass function? _MNRAS_ **458**, 3027–3046 (2016).


5

12. Motte, F., Bontemps, S. & Louvet, F. High-Mass Star and Massive Cluster Formation in the
Milky Way. _ARA_ & _A_ **56** (2018). `ArXive-prints1706.00118` .


13. Andr´e, P. _et al._ From filamentary clouds to prestellar cores to the stellar IMF: Initial highlights
from the Herschel Gould Belt Survey. _A_ & _A_ **518**, L102+ (2010).


14. Bontemps, S., Motte, F., Csengeri, T. & Schneider, N. Fragmentation and mass segregation in
the massive dense cores of Cygnus X. _A_ & _A_ **524**, A18 (2010).


15. Zhang, Q., Wang, K., Lu, X. & Jim´enez-Serra, I. Fragmentation of Molecular Clumps and
Formation of a Protocluster. _ApJ_ **804**, 141 (2015).


16. Cheng, Y. _et al._ The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed
by ALMA. _ApJ_ **853**, 160 (2018).


17. Motte, F., Schilke, P. & Lis, D. C. From Massive Protostars to a Giant H II Region: Submillimeter Imaging of the Galactic Ministarburst W43. _ApJ_ **582**, 277–291 (2003).


18. Nguyen Luong, Q. _et al._ W43: the closest molecular complex of the Galactic bar? _A_ & _A_ **529**,
A41 (2011).


19. Louvet, F. _et al._ Tracing extended low-velocity shocks through SiO emission. Case study of
the W43-MM1 ridge. _A_ & _A_ **595**, A122 (2016).


20. Men’shchikov, A. _et_ _al._ A multi-scale, multi-wavelength source extraction method: getsources. _A_ & _A_ **542**, A81 (2012).


21. Ma´ız Apell´aniz, J. & Ubeda, [´] L. Numerical Biases on Initial Mass Function Determinations
Created by Binning. _ApJ_ **629**, 873–880 (2005).


22. Salpeter, E. E. The Luminosity Function and Stellar Evolution. _ApJ_ **121**, 161 (1955).


23. Marsh, K. A., Whitworth, A. P. & Lomax, O. Temperature as a third dimension in columndensity mapping of dusty astrophysical structures associated with star formation. _MNRAS_ **454**,
4282–4292 (2015).


24. Herpin, F. _et_ _al._ The massive protostar W43-MM1 as seen by Herschel-HIFI water spectra:
high turbulence and accretion luminosity. _A_ & _A_ **542**, A76 (2012).


25. Sridharan, T. K. _et al._ Hot Core, Outflows, and Magnetic Fields in W43-MM1 (G30.79 FIR
10). _ApJ Lett._ **783**, L31 (2014).


26. Motte, F. & Andr´e, P. The circumstellar environment of low-mass protostars: A millimeter
continuum mapping survey. _A_ & _A_ **365**, 440–464 (2001).


27. Hatchell, J. & Fuller, G. A. Star formation in Perseus. IV. Mass-dependent evolution of dense
cores. _A_ & _A_ **482**, 855–863 (2008).


6

28. Swift, J. J. & Williams, J. P. On the Evolution of the Dense Core Mass Function. _ApJ_ **679**,
552–556 (2008).


29. Csengeri, T. _et_ _al._ The ATLASGAL survey: a catalog of dust condensations in the Galactic
plane. _A_ & _A_ **565**, A75 (2014).


30. Clark, P. C., Klessen, R. S. & Bonnell, I. A. Clump lifetimes and the initial mass function.
_MNRAS_ **379**, 57–62 (2007).


**Acknowledgements** This paper makes use of the following ALMA data: #2013.1.01365.S. ALMA is a
partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This project has
received funding from the European Union’s Horizon 2020 research and innovation programme StarFormMapper under grant agreement No 687528. This work was supported by the Programme National de
Physique Stellaire and Physique et Chimie du Milieu Interstellaire (PNPS and PCMI) of CNRS/INSU (with
INC/INP/IN2P3) co-funded by CEA and CNES. A.P.W. gratefully acknowledges the support of a consolidated grant (ST/K00926/1) from the UK Science and Technology Funding Council. T.Cs. acknowledges
support from the Deutsche Forschungsgemeinschaft, DFG via the SPP (priority programme) 1573 ‘Physics
of the ISM’. A.J.M. has received funding from the European Research Council (ERC) under the European
Union’s Horizon 2020 research and innovation programme (MagneticYSOs, grant agreement No 679937).


**Author Contributions** F.M. and F.L. led the project. E.C., T.N., F.M., and A.J.M. reduced the ALMA
data. F.L. ran _getsources_ and the CASA simulator, T.Cs. ran MRE-GaussClumps, and K.A.M. ran PPMAP.
S.B. and A.M. performed the Monte-Carlo simulations. F.M., T.N. and F.L. analysed CMF results. F.M and
A.P.W. wrote the manuscript. F.M, S.B., F.L., Q.N.L., A.J.M. and P.S. contributed to the ALMA proposal.
All authors discussed the results and implications, and commented on the manuscript.


**Competing Interests** The authors declare that they have no competing financial interests.


**Author Information** Reprints and permission information is available at www.nature.com/reprints. Readers are welcome to comment on the online version of the paper. Correspondence and requests for materials
should be addressed to the corresponding authors, F.M. (frederique.motte@univ-grenoble-alpes.fr), T.N.
(thomas.nony@univ-grenoble-alpes.fr), or F.L. (fabien.louvet@gmail.com).


7

trace the column density of gas, revealing high-density filaments and embedded cores. The filled
yellow ellipse on the right represents the angular resolution, and a scale bar is shown. Ellipses
**20**
outline core boundaries (at half-maximum) as defined by the _getsources_ extraction algorithm.
Core masses span the range from ∼ 1 M ⊙ to ∼ 100 M ⊙, and can therefore be expected to spawn
**5**
stars with masses from ∼ 0.4 M ⊙ to > 40 M ⊙ (see Supplementary Table 1). All cores are shown;
hashed ellipses indicate the most robust identifications.


8

Figure 2: **The** **W43-MM1** **core** **mass** **functions:** **(a)** **di** ff **erential** **form;** **(b)** **cumulative** **form,**
**challenging the relation between the CMF and the IMF.** Above the sample 90% completeness
limit, estimated to be _M_ core = 1.6 M ⊙ (black vertical line), the W43-MM1 CMFs (blue histograms)
are well fitted by single power-laws: **(a)** _dN_ / _d_ log( _M_ ) ∝ _M_ [−][0][.][90], and **(b)** _N_ (> log( _M_ )) ∝ _M_ [−][0][.][96] (red
lines and 1σ uncertainties). The error bars on the differential CMF correspond to ~~√~~ _N_ counting



lines and 1σ uncertainties). The error bars on the differential CMF correspond to ~~√~~ _N_ counting

statistics. The cumulative CMF in **(b)** is the more robust, statistically; its 5σ global uncertainty
(±0.13, hatched area) is estimated from Monte-Carlo simulations. The W43-MM1 CMF is clearly
**9,22** −1.35
flatter than the IMF, which in the corresponding mass range has slopes _dN_ / _d_ log( _M_ ) ∝ _M_



9
and _N_ (> log( _M_ )) ∝ _M_ [−][1][.][35] (magenta lines).

Figure 3: **Mean** **estimated** **dust** **temperatures** **for** **cores**, _T_ [¯] dust . Over most of the frame, _T_ [¯] dust is
**23** ′′
the column-density-weighted mean obtained with PPMAP using a 2.5 (or 14, 000 AU) resolution (colour scale). In the vicinity of the ten most luminous sources, the mean core temperature
with 0.44 [′′] (or 4, 200 AU) resolution is calculated using an approximate radiation transport model
**26**
based on their estimated luminosities . The W43-MM1 filaments are located by the 4, 20, and
50 mJy/beam contours of the 1.3 mm continuum map of Fig. 1. The _T_ [¯] dust map shows cloud heating
by the nearby cluster, screening by the W43-MM1 high-density filaments, and strong local heating
by the ten most luminous (30 to 10 [4] L ⊙ ) cores.


10

**Methods**


**Observations and data reduction** The W43-MM1 ALMA observations were carried out between

September 2014 and June 2015 (project #2013.1.01365.S) using the 12 m interferometric array.
With baselines ranging from 13 m to 1045 m, the 1.3 mm image is sensitive to emission on angular
scales from the synthesised beam, 0.37 [′′] ×0.53 [′′] (∼ 2, 400 AU at 5.5 kpc), to the filtering scale of the
interferometer for our observations, 12 [′′] . The W43-MM1 cloud was imaged with a 33-field mosaic
covering its 2.1 pc×1.4 pc extent. The complete dataset contains eight spectral windows, of which
the one most used here is dedicated to the 1.3 mm continuum centred at 233.45 GHz, with 1.9 GHz
bandwidth and 977 kHz channel step. The complementary data taken with the 7 m interferometric
array were not used because of their low signal-to-noise ratio.


Data were reduced with the CASA 4.3.1 software **[(31)]**, applying manual and SelfCalibration
scripts. The SelfCalibration technique improved image quality provided that it started from the
highest-sensitivity map integrated over the complete 1.9 GHz continuum band. We then applied
the Clean algorithm with a robust weight of 0.5 and the MultiScale option **[(32)]**, which minimises
interferometric artefacts associated with missing short spacings. We did not use merged 12 m
and 7 m data, because the MultiScale cleaning of 12 m-only data provides the optimum image
sensitivity for extracting cores. From the residual map of the continuum map integrated over
the complete 1.9 GHz band, we estimate noise levels from ∼0.13 mJy/beam in the outskirts to
∼2.5 mJy/beam towards the main filament. This variation is due to confusion caused by strong,
extended and structured cloud emission **[(33)]** .


**Core** **extraction** Compact sources were extracted using _getsources_ (v1.140127), a multi-scale,
multi-wavelength source-extraction algorithm developed for _Herschel_ CMF studies **[(20; 34)]** . The
main advantage of this algorithm applied to interferometric images is that it can extract sources
in varying backgrounds, from strong filaments to negative areas associated with missing short
spacings. We also used the multi-wavelength design of _getsources_ to simultaneously treat the
highest-sensitivity (1.9 GHz-integrated) and line-free (65 MHz-integrated) 1.3 mm continuum images. During the detection step _getsources_ combines both images and defines a catalogue of
sources with unique positions. At the measurement stage, _getsources_ measures the background
and flux of these sources, on each map independently.


We post-processed the _getsources_ catalogue to remove sources that are too extended, or
whose ellipticity is too large to correspond to cores, or that are not centrally-peaked, through
visual inspection. The final catalogue contains 131 sources with Sig > 5 (reliable), of which 94
cores have Sig - 7 (robust). Core characteristics are measured in the highest-sensitivity continuum
image, except when core fluxes in the highest-sensitivity map are larger than those measured in
the line-free image, due to line contamination. Sources with line contamination are massive cores
harbouring hot cores. Supplementary Table 1 lists the cores detected in W43-MM1, and provides
their significance level (Sig), coordinates, diameters, line contamination ratio, and peak and total
integrated flux (corrected for line contamination and local background). While the Sig variable
reflects the detection significance (equivalent to the signal-to-noise ratio of a source on the scale


11

where it is best detected), flux uncertainties reflect the quality of the flux measurements.


**Core mass estimates** The total mass of a core (gas plus dust), having uniform opacity throughout
its solid angle, is given by



_S_ int
1.3mm
×
 _S_ 1 [peak] .3mm




_[d]_ [2]
_M_ core = − [Ω] [beam] ln

κ 1.3mm



_S_ [peak]
1 − 1.3mm
 Ω beam _B_ 1.3mm ( _T_ dust )



.





_[B]_ [1][.][3mm] [(] _[T]_ [dust] [)]
= − _M_ core [opt thin] × [Ω] [beam] _S_ [peak] ln

1.3mm



_S_ [peak]
1 − 1.3mm
 Ω beam _B_ 1.3mm ( _T_ dust )



Here Ω beam is the solid angle of the beam, _d_ = 5.5 kpc is the distance to the core, κ 1.3 mm is the
dust opacity per unit mass of gas and dust at 1.3 mm, _S_ 1 [peak] .3mm [and] _[S]_ [ int] 1.3mm [are] [the] [peak] [and] [inte-]
grated monochromatic fluxes of the core at 1.3 mm, and _B_ 1.3 mm ( _T_ dust ) is the Planck function at dust
temperature _T_ dust . _M_ core [opt thin] = _S_ 1 [int] .3mm _[d]_ [2] [/][(][κ] [1][.][3mm] _[B]_ [1][.][3mm] [(] _[T]_ [dust] [)) is the core mass in the optically thin]
limit. We have adopted κ 1.3 mm = 0.01 cm [2] g [−][1] **[(35)]** as being most appropriate for high-density, cool
to warm cores. Supplementary Table 1 lists for each core its mass and mean number density **[(36)]** .


The 1.3 mm continuum flux of a core arises mostly from thermal dust emission, which is
optically thin except towards the seven densest, most massive cores. Contamination by free-free
**17**
emission is estimated to be low (< 20% ) for W43-MM1 cores, since none of the embedded
protostars are sufficiently hot and luminous (< 10 [3] L ⊙ for all except three cores) to ionise significant
Hii regions. Line contamination was evaluated by comparing the fluxes measured in the total
1.9 GHz continuum band and in a selection of line-free channels summing up to 65 MHz. The
mass uncertainties are derived from the flux uncertainties measured by _getsources_, and from the
**23**
estimated dust temperature error. We added the ±1 K errors of PPMAP temperatures to the
uncertainty derived from the self-shielding of 0.5 [′′] starless cores and/or the internal heating of
0.5 [′′] protostellar cores lying within the 2.5 [′′] PPMAP resolution **[(26; 37)]** . We estimate the absolute
values of the core masses to be uncertain by a factor of a few, and the relative values between cores
to be uncertain by ∼ 50%.


To estimate the sample completeness, we have performed ten Monte-Carlo simulations that
place 2,000 synthetic cores, having masses in the range 1 to 10 M ⊙, on the worst-sensitivity background image determined by _getsources_ or on the original image containing real cores. Like the
observed cores, the synthetic cores have small sizes, and this reduces confusion by nearby sources
and gives an excellent measurement of the total core mass. We then simulated observation of
these synthetic protoclusters and applied the same core extraction process as for the real data.
Supplementary Fig. 2 shows that the 90% completeness level depends weakly on the background
intensity. It is ∼ 0.8 ± 0.1 M ⊙ in the outskirts of the protocluster, ∼ 1.6 ± 0.1 M ⊙ where most cores
lie, and up to ∼ 4.5 ± 1 M ⊙ on the main filament (see the areas outlined in Supplementary Fig. 1).
The 90% completeness level also depends weakly on the source confusion, with an increase up to
∼ 2.1 ± 0.3 M ⊙ for overlapping sources, relative to the mean value, which remains at ∼ 1.6 M ⊙ (see
Supplementary Fig. 2).


12

**Core** **mass** **functions** We have made numerous tests and Monte-Carlo simulations to prove the
**20**
robustness of the CMF shape against interferometric artefacts, extraction methods ( _getsources_ or
**29**
MRE-GaussClumps ), mass estimates, and CMF representations. In developing the best strategy
to reduce the W43-MM1 ALMA image, the core catalogue steadily improved, with progressively
fewer false cores and more solar-type cores. The 94 robust cores (> 7σ) were detected in almost all
runs. Supplementary Table 2 lists the major tests performed to evaluate the uncertainty of CMF fit.
For statistical reasons, fits are more robust in cumulative form **[(38)]**, with the complete sample of 131
reliable cores, and the complete 1.6 M ⊙ to 100 M ⊙ mass range. However, Supplementary Table 2
shows that the higher-mass part (> 4.5 M ⊙ ) of the W43-MM1 CMF is still always flatter than the
IMF. Monte-Carlo simulations (with 100,000 runs) show that the mass uncertainties correspond to
the slope of the CMF, γ cumul, having a 5σ uncertainty of ±0.13. Building separate mass functions
for cores that do, and cores that do not, contain accreting protostars is not feasible here. First, the
most massive cores all contain young low-luminosity accreting protostars. Second, their outflows
make it very hard to ascertain the precise nature of their lower-mass neighbours (i.e. whether or
not they too already contain accreting protostars).


**Self-similar mapping** A statistically self-similar mapping means that, for example, the probability that a core with mass in the range 1.0 M ⊙ to 1.1 M ⊙ spawns – possibly along with other stars – a
star with mass in the range 0.40 M ⊙ to 0.44 M ⊙ is the same as the probability that a core with mass
in the range 10 M ⊙ to 11 M ⊙ spawns a star with mass in the range 4.0 M ⊙ to 4.4 M ⊙ . A mapping
with small variance is required, because, if the variance were large, the peak of the IMF would be
**5**
noticeably broader than the peak of the CMF, and this does not appear to be the case . (We note
that incompleteness at low core masses can only make the peak of the CMF broader than current
estimates, and thereby strengthen this constraint.)


To compute a notional conversion efficiency (the mean of the total mass of stars subsequently
spawned by a core divided by the core’s mass), we need to determine: (i) the mean factor by
which a core’s mass grows, between when it is measured to determine the CMF, and when it has
finished forming stars, µ map (> 1); and (ii) the mean fraction of this final mass that goes into stars,
η map (< 1). The notional efficiency is then µ map η map, and can in principle exceed unity (which
is why it is ‘notional’). If we also know (iii) the mean number of stars spawned by a single
core, N map, we can compute the upward shift from the peak of the IMF to the peak of the CMF,
1/ϵ = N map /(µ map η map ). Finally, if we know (iv) the logarithmic variance of the mean distribution
of stellar masses spawned by a single core, σ map, this must be convolved with the logarithmic
variance of the CMF to determine the logarithmic variance of the IMF, σ [2] IMF [=] [σ] [2] CMF [+][ σ] [2] map [.] [Since]
σ map is necessarily finite, a self-similar mapping requires σ IMF >σ CMF .


**Data Availability** The data that support the plots within this paper and other findings of this study are
available from the corresponding authors (F.M., T.N., or F.L) upon reasonable request. Requests for materials should be addressed to F.M. (frederique.motte@univ-grenoble-alpes.fr), T.N. (thomas.nony@univgrenoble-alpes.fr), or F.L. (fabien.louvet@gmail.com).


13

**Additional references**


31. McMullin, J. P., Waters, B., Schiebel, D., Young, W. & Golap, K. CASA Architecture and
Applications. In Shaw, R. A., Hill, F. & Bell, D. J. (eds.) _Astronomical_ _Data_ _Analysis_ _Software_
_and Systems XVI_, vol. 376 of _Astronomical Society of the Pacific Conference Series_, 127 (2007).


32. Rau, U. & Cornwell, T. J. A multi-scale multi-frequency deconvolution algorithm for synthesis imaging in radio interferometry. _A_ & _A_ **532**, A71 (2011).


33. Hennemann, M. _et_ _al._ The spine of the swan: a Herschel study of the DR21 ridge and filaments in Cygnus X. _A_ & _A_ **543**, L3 (2012).


34. Men’shchikov, A. A multi-scale filament extraction method: getfilaments. _A_ & _A_ **560**, A63
(2013).


35. Ossenkopf, V. & Henning, T. Dust opacities for protostellar cores. _A_ & _A_ **291**, 943-959 (1994).


36. Tig´e, J. _et_ _al._ The earliest phases of high-mass star formation, as seen in NGC 6334 by
Herschel-HOBYS. _A_ & _A_ **602**, A77 (2017).


37. Bracco, A. _et_ _al._ Probing changes of dust properties along a chain of solar-type prestellar
and protostellar cores in Taurus with NIKA. _A_ & _A_ **604**, A52 (2017).


38. Reid, M. A. & Wilson, C. D. High-Mass Star Formation. III. The Functional Form of the
Submillimeter Clump Mass Function. _ApJ_ **650**, 970-984 (2006).


14

**Supplementary Table 1** — Characteristics of the cores detected at 1.3 mm in W43-MM1.
# RA Dec. Size FWHM Sig _C_ line _S_ 1 [peak] .3mm _S_ 1 [int] .3mm _T_ ¯ dust _M_ core _n_ ¯ H2

[J2000] [J2000] [ [′′] × [′′] ] [AU] [%] [mJy/beam] [mJy] [K] [M ⊙ ] ×10 [7] cm [−][3]

1 18:47:47.02 -1:54:26.86 0.82 × 0.45 2300 1100 45 277 ± 5 592 ± 6 74 ± 2 102 ± 5 210 ± 10

2 18:47:46.84 -1:54:29.30 0.48 × 0.45 1200 670 26 192 ± 5 261 ± 6 59 ± 4 55 ± 6 750 ± 80

3 18:47:46.37 -1:54:33.41 0.52 × 0.47 1200 330 13 109 ± 2 222 ± 2 45 ± 1 59 ± 2 760 ± 30

4 18:47:46.98 -1:54:26.42 0.88 × 0.45 2500 340 74 109 ± 5 312 ± 5 88 ± 7 36 ± 3 57 ± 5

5 18:47:46.76 -1:54:31.21 0.55 × 0.45 1300 170 15 52 ± 4 78 ± 5 47 ± 1 18 ± 1 210 ± 20

6 18:47:46.16 -1:54:33.30 0.55 × 0.45 1300 130 0 46.8 ± 0.8 94 ± 1 23 ± 2 56 ± 9 660 ± 100

7 18:47:47.26 -1:54:29.70 0.48 × 0.45 1200 130 0 47 ± 1 59 ± 1 30 ± 2 23 ± 2 320 ± 30

8 18:47:46.54 -1:54:23.15 0.54 × 0.45 1200 130 0 45 ± 2 61 ± 2 45 ± 5 14 ± 2 190 ± 30

9 18:47:46.48 -1:54:32.54 0.63 × 0.45 1600 110 17 37 ± 2 87 ± 3 50 ± 1 17.8 ± 0.9 97 ± 5

10 18:47:46.91 -1:54:29.99 0.67 × 0.5 2100 91 24 35 ± 4 78 ± 5 51 ± 2 16 ± 1 43 ± 4

11 18:47:46.52 -1:54:24.26 0.52 × 0.45 1200 72 60 16 ± 2 21 ± 2 93 ± 11 2.1 ± 0.3 28 ± 5

12 18:47:46.57 -1:54:32.04 0.72 × 0.45 2000 77 0 30 ± 2 57 ± 2 23 ± 2 31 ± 4 100 ± 10

13 18:47:46.92 -1:54:28.62 0.69 × 0.45 1900 63 0 22 ± 6 22 ± 6 24 ± 2 11 ± 3 40 ± 10

14 18:47:46.97 -1:54:29.66 0.72 × 0.45 2000 57 0 23 ± 6 33 ± 6 22 ± 2 19 ± 4 60 ± 10

15 18:47:44.77 -1:54:45.22 0.66 × 0.54 2200 62 54 9.1 ± 0.8 20 ± 1 50 ± 3 3.9 ± 0.3 8.8 ± 0.8

16 18:47:47.02 -1:54:30.78 0.78 × 0.45 2200 68 0 25 ± 3 58 ± 4 21 ± 2 36 ± 6 90 ± 10

17 18:47:47.10 -1:54:27.07 0.51 × 0.45 1200 46 0 16 ± 6 18 ± 6 35 ± 2 6 ± 2 80 ± 30

18 18:47:46.25 -1:54:33.41 0.93 × 0.45 2600 59 0 22.7 ± 0.8 53 ± 1 23 ± 2 28 ± 4 39 ± 5

19 18:47:46.88 -1:54:25.74 0.45 × 0.45 1200 45 0 16 ± 5 19 ± 5 24 ± 2 9 ± 3 130 ± 40

20 18:47:45.29 -1:54:37.04 0.48 × 0.45 1200 47 0 13.2 ± 0.5 16.4 ± 0.6 23 ± 2 8 ± 1 110 ± 20

21 18:47:46.79 -1:54:16.06 0.47 × 0.45 1200 46 0 15 ± 1 20 ± 1 23 ± 2 10 ± 1 140 ± 20

22 18:47:47.05 -1:54:32.15 0.45 × 0.45 1200 40 0 13 ± 2 13 ± 2 21 ± 2 8 ± 2 100 ± 20

23 18:47:46.90 -1:54:24.30 0.63 × 0.45 1600 44 0 15 ± 5 20 ± 5 22 ± 2 11 ± 3 60 ± 20

24 18:47:46.97 -1:54:32.08 0.63 × 0.45 1600 29 0 10 ± 2 12 ± 2 21 ± 2 7 ± 1 37 ± 8

25 18:47:46.87 -1:54:14.62 0.45 × 0.45 1200 29 0 8 ± 1 8 ± 1 24 ± 2 4.0 ± 0.7 50 ± 10

26 18:47:44.94 -1:54:42.84 0.51 × 0.45 1200 28 0 7.1 ± 0.6 10.5 ± 0.7 23 ± 2 5.2 ± 0.7 70 ± 10

27 18:47:47.03 -1:54:24.91 0.62 × 0.45 1600 25 0 10 ± 5 11 ± 5 26 ± 2 5 ± 2 30 ± 10

28 18:47:44.40 -1:54:41.80 0.81 × 0.45 2300 22 0 5.8 ± 0.7 11.7 ± 0.8 23 ± 2 5.9 ± 0.9 12 ± 2

29 18:47:45.22 -1:54:38.81 0.45 × 0.45 1200 20 0 5.5 ± 0.5 6.6 ± 0.6 24 ± 2 3.1 ± 0.5 43 ± 6

30 18:47:47.18 -1:54:21.56 0.57 × 0.45 1400 19 26 5 ± 2 6 ± 2 62 ± 4 1.0 ± 0.3 10 ± 3

31 18:47:46.73 -1:54:17.53 0.59 × 0.45 1500 19 0 6.6 ± 0.9 8 ± 1 23 ± 2 4.3 ± 0.7 33 ± 6

32 18:47:46.57 -1:54:20.84 0.84 × 0.45 2400 20 0 7 ± 2 15 ± 2 28 ± 2 6 ± 1 11 ± 2

33 18:47:47.08 -1:54:28.80 0.72 × 0.46 2000 24 0 9 ± 4 17 ± 4 22 ± 2 9 ± 3 26 ± 8

34 18:47:46.52 -1:54:28.87 0.64 × 0.45 1700 18 0 6.9 ± 0.9 15 ± 1 25 ± 2 7 ± 1 35 ± 5

35 18:47:46.92 -1:54:31.75 0.73 × 0.46 2100 20 0 7 ± 3 15 ± 3 22 ± 2 8 ± 2 23 ± 5

36 18:47:46.64 -1:54:19.51 0.45 × 0.45 1200 18 0 5.8 ± 0.8 8 ± 1 27 ± 2 3.1 ± 0.5 43 ± 7

37 18:47:46.97 -1:54:12.96 0.73 × 0.45 2000 20 0 5 ± 1 11 ± 1 23 ± 2 5.2 ± 0.9 15 ± 3

38 18:47:47.02 -1:54:22.90 0.45 × 0.45 1200 16 0 5 ± 1 5 ± 2 24 ± 2 2.5 ± 0.8 30 ± 10

39 18:47:44.61 -1:54:42.16 0.47 × 0.45 1200 16 0 3.6 ± 0.6 4.8 ± 0.7 23 ± 2 2.3 ± 0.4 32 ± 6

40 18:47:46.35 -1:54:29.52 0.53 × 0.45 1200 17 0 5.8 ± 0.8 9.4 ± 0.9 24 ± 2 4.3 ± 0.7 59 ± 9

41 18:47:46.96 -1:54:23.87 0.68 × 0.45 1800 15 0 5 ± 3 7 ± 3 22 ± 2 4 ± 2 14 ± 7

42 18:47:44.78 -1:54:38.05 0.45 × 0.45 1200 13 0 3.0 ± 0.4 3.1 ± 0.4 24 ± 2 1.4 ± 0.2 19 ± 3

43 18:47:46.84 -1:54:31.64 0.64 × 0.46 1700 12 0 4 ± 3 5 ± 3 22 ± 2 2 ± 1 11 ± 7

44 18:47:44.76 -1:54:46.76 0.56 × 0.45 1300 15 0 3.2 ± 0.4 5.0 ± 0.4 22 ± 2 2.5 ± 0.4 28 ± 4

45 18:47:46.87 -1:54:36.50 0.45 × 0.45 1200 11 0 4.1 ± 0.9 4.2 ± 0.9 21 ± 2 2.4 ± 0.6 32 ± 8

46 18:47:46.77 -1:54:16.85 0.73 × 0.45 2000 12 0 4.7 ± 0.9 8.3 ± 0.9 21 ± 2 4.6 ± 0.8 14 ± 2

47 18:47:46.65 -1:54:31.90 0.81 × 0.59 2900 21 0 9 ± 2 35 ± 3 22 ± 2 19 ± 3 18 ± 3

48 18:47:46.82 -1:54:26.10 0.66 × 0.45 1700 12 0 5 ± 2 7 ± 2 23 ± 2 4 ± 1 16 ± 6

49 18:47:46.59 -1:54:20.48 0.73 × 0.48 2200 14 0 5 ± 1 9 ± 2 28 ± 2 3.7 ± 0.8 9 ± 2

50 18:47:46.97 -1:54:34.42 0.45 × 0.45 1200 11 0 3 ± 1 3 ± 1 21 ± 2 1.7 ± 0.8 20 ± 10

15

**Supplementary Table 1** — Characteristics of the cores detected at 1.3 mm in W43-MM1 (continued).
# RA Dec. Size FWHM Sig _C_ line _S_ 1 [peak] .3mm _S_ 1 [int] .3mm _T_ ¯ dust _M_ core _n_ ¯ H2

[J2000] [J2000] [ [′′] × [′′] ] [AU] [%] [mJy/beam] [mJy] [K] [M ⊙ ] ×10 [7] cm [−][3]

51 18:47:45.27 -1:54:40.03 0.96 × 0.52 3000 15 0 4.0 ± 0.7 10.2 ± 0.9 24 ± 2 4.8 ± 0.7 4.3 ± 0.6

52 18:47:46.80 -1:54:34.34 0.45 × 0.45 1200 10 0 3 ± 1 3 ± 1 21 ± 2 1.8 ± 0.8 20 ± 10

53 18:47:47.05 -1:54:18.90 0.77 × 0.55 2600 11 0 3.8 ± 0.7 7.5 ± 0.8 22 ± 2 4.0 ± 0.7 5.2 ± 0.9

54 18:47:45.06 -1:54:42.05 0.79 × 0.45 2200 11 0 2.9 ± 0.4 6.0 ± 0.5 23 ± 2 3.0 ± 0.4 7 ± 1

55 18:47:46.96 -1:54:35.42 0.63 × 0.45 1600 9.6 0 3 ± 1 3 ± 1 21 ± 2 2.0 ± 0.8 11 ± 4

56 18:47:47.00 -1:54:20.12 0.58 × 0.45 1400 11 0 3 ± 1 3 ± 1 21 ± 2 1.9 ± 0.9 17 ± 8

57 18:47:46.94 -1:54:19.37 0.45 × 0.45 1200 9.8 0 3 ± 1 3 ± 1 23 ± 2 1.7 ± 0.5 23 ± 8

58 18:47:47.08 -1:54:21.28 0.74 × 0.45 2000 11 0 4 ± 2 7 ± 3 25 ± 2 3 ± 1 8 ± 4

59 18:47:44.77 -1:54:44.17 0.63 × 0.45 1600 9.9 0 2.3 ± 0.9 3 ± 1 23 ± 2 1.4 ± 0.5 8 ± 3

60 18:47:44.76 -1:54:40.46 0.48 × 0.45 1200 10 0 2.4 ± 0.8 3.2 ± 0.9 23 ± 2 1.6 ± 0.5 22 ± 7

61 18:47:46.82 -1:54:35.53 0.7 × 0.53 2300 12 0 4 ± 1 10 ± 1 21 ± 2 6 ± 1 11 ± 2

62 18:47:45.79 -1:54:32.76 0.65 × 0.45 1700 11 0 3.7 ± 0.7 9 ± 1 24 ± 2 4.0 ± 0.6 19 ± 3

63 18:47:47.33 -1:54:12.82 0.47 × 0.45 1200 9.5 0 3.0 ± 0.7 3.8 ± 0.7 21 ± 2 2.1 ± 0.5 29 ± 7

64 18:47:46.99 -1:54:16.85 0.83 × 0.49 2600 10 0 3 ± 1 6 ± 1 22 ± 2 3.2 ± 0.7 5 ± 1

65 18:47:45.41 -1:54:37.44 0.56 × 0.45 1300 8.9 0 2.7 ± 0.6 3.1 ± 0.6 23 ± 2 1.6 ± 0.4 16 ± 4

66 18:47:47.00 -1:54:21.20 0.68 × 0.45 1800 9.0 0 3 ± 2 4 ± 2 22 ± 2 2.3 ± 0.9 9 ± 3

67 18:47:44.09 -1:54:48.89 0.66 × 0.47 1900 9.8 0 1.8 ± 0.3 4.7 ± 0.4 23 ± 2 2.2 ± 0.3 8 ± 1

68 18:47:47.02 -1:54:35.64 0.71 × 0.45 2000 8.7 0 3 ± 1 4 ± 1 21 ± 2 2.2 ± 0.6 7 ± 2

69 18:47:47.15 -1:54:20.05 0.5 × 0.45 1200 9.1 0 3 ± 1 5 ± 1 25 ± 2 2.1 ± 0.6 29 ± 8

70 18:47:47.20 -1:54:17.78 0.79 × 0.48 2400 9.1 0 3.3 ± 0.7 6.8 ± 0.8 23 ± 2 3.4 ± 0.6 6 ± 1

71 18:47:47.35 -1:54:13.46 0.62 × 0.45 1600 8.3 0 2.4 ± 0.6 3.1 ± 0.6 21 ± 2 1.7 ± 0.4 10 ± 2

72 18:47:46.65 -1:54:35.53 0.74 × 0.45 2100 8.2 0 3 ± 1 4 ± 1 20 ± 2 2.3 ± 0.8 6 ± 2

73 18:47:44.84 -1:54:42.95 0.63 × 0.53 2100 11 0 2.5 ± 0.8 6 ± 1 23 ± 2 2.8 ± 0.7 8 ± 2

74 18:47:45.17 -1:54:39.53 0.62 × 0.45 1600 8.0 0 2.2 ± 0.4 2.9 ± 0.5 24 ± 2 1.4 ± 0.3 8 ± 2

75 18:47:46.90 -1:54:35.10 0.73 × 0.45 2000 8.0 0 2 ± 1 3 ± 1 21 ± 2 1.9 ± 0.7 6 ± 2

76 18:47:46.93 -1:54:37.87 0.48 × 0.45 1200 8.0 0 2.8 ± 0.9 3 ± 1 21 ± 2 1.6 ± 0.6 22 ± 8

77 18:47:47.41 -1:54:25.60 0.73 × 0.45 2000 8.9 0 3.3 ± 0.9 6 ± 1 26 ± 2 2.6 ± 0.5 8 ± 2

78 18:47:46.43 -1:54:29.81 0.79 × 0.45 2200 7.7 0 2.3 ± 0.9 4 ± 1 23 ± 2 2.0 ± 0.6 5 ± 1

79 18:47:46.73 -1:54:25.63 0.8 × 0.46 2300 11 0 3 ± 1 7 ± 1 26 ± 2 2.8 ± 0.7 5 ± 1

80 18:47:47.15 -1:54:24.66 0.73 × 0.45 2000 7.2 0 3 ± 1 3 ± 1 22 ± 2 1.6 ± 0.7 5 ± 2

81 18:47:47.24 -1:54:18.47 0.74 × 0.46 2100 8.4 0 2.9 ± 0.6 5.4 ± 0.7 23 ± 2 2.6 ± 0.5 7 ± 1

82 18:47:46.90 -1:54:33.98 0.63 × 0.45 1600 7.7 0 3 ± 1 3 ± 1 21 ± 2 1.9 ± 0.6 10 ± 3

83 18:47:46.71 -1:54:24.19 0.75 × 0.45 2100 7.9 0 3 ± 1 4 ± 1 28 ± 2 1.5 ± 0.6 4 ± 2

84 18:47:46.37 -1:54:21.28 0.78 × 0.45 2200 9.7 0 3.1 ± 0.8 6 ± 1 26 ± 2 2.7 ± 0.5 6 ± 1

85 18:47:46.51 -1:54:26.42 0.7 × 0.5 2200 8.3 0 2.5 ± 0.9 5 ± 1 27 ± 2 1.8 ± 0.5 4 ± 1

86 18:47:46.74 -1:54:20.81 0.58 × 0.45 1400 7.4 0 2.5 ± 0.9 3.1 ± 0.9 26 ± 2 1.3 ± 0.4 11 ± 4

87 18:47:47.24 -1:54:16.06 0.54 × 0.45 1200 7.5 0 2.3 ± 0.6 2.7 ± 0.7 23 ± 2 1.4 ± 0.4 18 ± 5

88 18:47:47.28 -1:54:38.27 0.69 × 0.45 1900 7.4 0 2.5 ± 0.8 3.6 ± 0.8 21 ± 2 2.0 ± 0.5 7 ± 2

89 18:47:46.30 -1:54:28.76 0.68 × 0.45 1800 7.3 0 2.7 ± 0.9 3.6 ± 0.9 26 ± 2 1.5 ± 0.4 6 ± 2

90 18:47:46.39 -1:54:18.14 0.84 × 0.45 2400 7.2 0 2.7 ± 0.7 4.9 ± 0.8 24 ± 2 2.4 ± 0.5 4.4 ± 0.9

91 18:47:46.75 -1:54:33.30 0.63 × 0.45 1600 7.1 0 3 ± 1 3 ± 1 21 ± 2 1.8 ± 0.8 10 ± 4

92 18:47:46.86 -1:54:12.13 0.79 × 0.47 2300 7.9 0 2.5 ± 0.5 4.5 ± 0.5 22 ± 2 2.4 ± 0.4 4.7 ± 0.8

93 18:47:46.96 -1:54:40.86 0.69 × 0.45 1900 7.0 0 2.7 ± 0.7 3.7 ± 0.8 21 ± 2 2.1 ± 0.5 8 ± 2

94 18:47:46.74 -1:54:37.80 0.67 × 0.45 1800 7.0 0 2.7 ± 0.6 3.9 ± 0.7 21 ± 2 2.2 ± 0.5 9 ± 2

95 18:47:46.58 -1:54:25.67 0.72 × 0.45 2000 7.1 0 2.7 ± 0.9 3.1 ± 0.9 28 ± 2 1.2 ± 0.4 4 ± 1

96 18:47:47.08 -1:54:23.54 0.65 × 0.45 1700 7.4 0 3 ± 1 4 ± 1 24 ± 2 2.0 ± 0.6 9 ± 3

97 18:47:47.16 -1:54:10.15 0.72 × 0.45 2000 7.6 0 1.9 ± 0.4 4.1 ± 0.6 21 ± 2 2.3 ± 0.5 7 ± 1

98 18:47:46.40 -1:54:28.37 0.68 × 0.52 2200 7.0 0 2.3 ± 0.9 4 ± 1 27 ± 2 1.5 ± 0.4 3 ± 1

99 18:47:45.39 -1:54:39.13 1.26 × 0.55 3900 8.5 0 1.7 ± 0.6 7.1 ± 0.9 23 ± 2 3.4 ± 0.6 1.4 ± 0.2

100 18:47:45.22 -1:54:40.46 0.7 × 0.47 2100 6.8 0 2.1 ± 0.5 3.1 ± 0.5 24 ± 2 1.4 ± 0.3 4.1 ± 0.8

16

**Supplementary Table 1** — Characteristics of the cores detected at 1.3 mm in W43-MM1 (continued).
# RA Dec. Size FWHM Sig _C_ line _S_ 1 [peak] .3mm _S_ 1 [int] .3mm _T_ ¯ dust _M_ core _n_ ¯ H2

[J2000] [J2000] [ [′′] × [′′] ] [AU] [%] [mJy/beam] [mJy] [K] [M ⊙ ] ×10 [7] cm [−][3]

101 18:47:47.30 -1:54:35.03 0.59 × 0.45 1500 6.8 0 2.8 ± 0.7 4.1 ± 0.8 21 ± 2 2.3 ± 0.6 17 ± 4

102 18:47:47.15 -1:54:33.19 0.7 × 0.45 1900 6.7 0 2 ± 1 2 ± 1 21 ± 2 1.2 ± 0.6 4 ± 2

103 18:47:46.74 -1:54:19.44 0.51 × 0.45 1200 7.0 0 2 ± 1 2 ± 1 26 ± 2 1.1 ± 0.5 15 ± 6

104 18:47:46.80 -1:54:18.43 0.61 × 0.45 1500 6.9 0 2.2 ± 0.8 2.9 ± 0.9 24 ± 2 1.3 ± 0.4 9 ± 3

105 18:47:46.50 -1:54:16.24 0.46 × 0.45 1200 6.9 0 1.9 ± 0.6 1.9 ± 0.6 23 ± 2 1.0 ± 0.3 13 ± 4

106 18:47:46.40 -1:54:36.61 0.63 × 0.45 1600 6.9 0 2.3 ± 0.6 3.6 ± 0.7 21 ± 2 2.0 ± 0.5 11 ± 3

107 18:47:47.24 -1:54:35.60 0.57 × 0.47 1500 6.8 0 2.6 ± 0.7 3.9 ± 0.7 21 ± 2 2.2 ± 0.5 15 ± 3

108 18:47:45.32 -1:54:39.13 0.69 × 0.45 1900 6.6 0 1.9 ± 0.9 2.6 ± 0.9 24 ± 2 1.2 ± 0.5 4 ± 2

109 18:47:46.60 -1:54:18.00 0.67 × 0.45 1800 6.7 0 2.3 ± 0.9 4 ± 1 25 ± 2 1.7 ± 0.5 7 ± 2

110 18:47:47.16 -1:54:11.30 0.65 × 0.45 1700 6.8 0 2.1 ± 0.6 3.4 ± 0.6 21 ± 2 1.9 ± 0.4 9 ± 2

111 18:47:46.80 -1:54:20.16 0.7 × 0.45 1900 6.5 0 2 ± 1 3 ± 1 25 ± 2 1.4 ± 0.6 5 ± 2

112 18:47:46.30 -1:54:37.37 0.66 × 0.45 1800 6.4 0 2.3 ± 0.5 2.7 ± 0.5 22 ± 2 1.5 ± 0.3 7 ± 2

113 18:47:47.03 -1:54:10.58 0.64 × 0.47 1800 6.4 0 1.5 ± 0.5 2.2 ± 0.6 21 ± 2 1.2 ± 0.4 5 ± 2

114 18:47:46.91 -1:54:17.75 0.53 × 0.45 1200 6.4 0 1.9 ± 0.5 2.2 ± 0.5 22 ± 2 1.1 ± 0.3 16 ± 4

115 18:47:46.76 -1:54:12.64 0.77 × 0.57 2700 6.9 0 2.4 ± 0.2 5.3 ± 0.2 22 ± 2 2.8 ± 0.4 3.5 ± 0.5

116 18:47:46.18 -1:54:30.92 0.62 × 0.45 1600 6.4 0 2.2 ± 0.6 3.5 ± 0.7 23 ± 2 1.7 ± 0.4 10 ± 2

117 18:47:46.67 -1:54:23.80 0.97 × 0.47 2800 6.7 0 3 ± 1 6 ± 1 29 ± 2 2.3 ± 0.6 2.6 ± 0.6

118 18:47:47.04 -1:54:14.90 0.72 × 0.45 2000 6.1 0 1.6 ± 0.7 2.5 ± 0.7 23 ± 2 1.2 ± 0.4 4 ± 1

119 18:47:47.37 -1:54:11.81 0.54 × 0.45 1200 6.4 0 1.8 ± 0.5 2.4 ± 0.6 21 ± 2 1.4 ± 0.4 18 ± 5

120 18:47:46.80 -1:54:11.92 0.76 × 0.63 2900 6.2 0 2.5 ± 0.4 5.7 ± 0.4 22 ± 2 3.0 ± 0.5 2.9 ± 0.5

121 18:47:47.00 -1:54:39.53 0.74 × 0.45 2100 6.3 0 1.7 ± 0.8 2.4 ± 0.9 21 ± 2 1.3 ± 0.5 4 ± 1

122 18:47:44.76 -1:54:53.14 0.59 × 0.56 2000 6.7 0 1.3 ± 0.4 3.1 ± 0.6 23 ± 2 1.5 ± 0.3 4.4 ± 0.9

123 18:47:46.99 -1:54:4.90 0.85 × 0.45 2400 6.3 0 1.7 ± 0.4 3.2 ± 0.5 21 ± 2 1.8 ± 0.4 3.3 ± 0.7

124 18:47:47.37 -1:54:21.38 0.84 × 0.45 2300 5.8 0 2.4 ± 0.7 5.0 ± 0.8 25 ± 2 2.2 ± 0.4 4.1 ± 0.8

125 18:47:47.47 -1:54:38.09 0.63 × 0.45 1700 6.3 0 2.2 ± 0.5 3.3 ± 0.6 23 ± 2 1.6 ± 0.4 9 ± 2

126 18:47:44.57 -1:54:39.71 0.83 × 0.53 2700 6.4 0 1.5 ± 0.5 4.3 ± 0.8 23 ± 2 2.1 ± 0.5 2.6 ± 0.6

127 18:47:46.25 -1:54:22.25 1.02 × 0.55 3300 6.2 0 1.9 ± 0.6 5.8 ± 0.9 27 ± 2 2.4 ± 0.4 1.6 ± 0.3

128 18:47:47.29 -1:54:26.32 0.88 × 0.57 3000 5.9 0 1.7 ± 0.9 4 ± 1 23 ± 2 2.0 ± 0.6 1.7 ± 0.5

129 18:47:46.56 -1:54:6.95 0.87 × 0.48 2600 6.1 0 1.5 ± 0.4 3.7 ± 0.5 23 ± 2 1.8 ± 0.3 2.6 ± 0.5

130 18:47:46.37 -1:54:47.74 0.98 × 0.45 2700 5.7 0 1.9 ± 0.4 4.5 ± 0.5 21 ± 2 2.5 ± 0.5 3.0 ± 0.5

131 18:47:46.55 -1:54:16.63 1.11 × 0.5 3300 5.8 0 1.6 ± 0.6 5.1 ± 0.8 23 ± 2 2.6 ± 0.5 1.7 ± 0.3


Notes: RA, right ascension; Dec., declination; Size at half-maximum; FWHM, Size deconvolved with the 0.44 [′′] telescope beam;
Sig, significance level of _getsources_ core extraction; line contamination ratio, _C_ line = [ _S_ [peak] (1.9 GHz) − _S_ [peak] (65 MHz)] / _S_ [peak] (65 MHz)
_S_ [peak] _[T]_ [¯] [dust] [, mean dust temperature]
1.3mm [and] _[ S]_ [ int] 1.3mm [, peak and total integrated flux corrected for line contamination and local background;]
read in Fig. 3; _M_ core, core mass; mean density, _n_ ¯ H2 = 4 _M_ core [, where][ µ][ =][ 2][.][8 is the mean molecular weight per H] [2] [molecule]
3 [π µ] _[ m]_ [H] [ (] _[FWHM]_ [/][2)] [3]
and _m_ H is the hydrogen mass.


17

**Supplementary Figure 1 — High-angular resolution image of the complete W43-MM1 cloud.**
1.3 mm dust continuum emission, observed by the ALMA interferometer, is presumed to trace the
column density of gas, revealing high-density filaments and embedded cores. The filled yellow
ellipse on the left shows the angular resolution, and a scale bar is shown on the right. Contours
correspond to the _S_ 1 [peak] .3mm [=] [4 mJy][/][beam flux level (black) and the 10] [23] [ cm] [−][2] [column density level]
from _Herschel_ (white). Despite the high-sensitivity of the ALMA image, and the high column
densities observed, there appear to be no filaments or cores, with a completeness level of ∼ 0.8 M ⊙,
in the outskirts of the cloud. The core sample is 90% complete down to ∼ 1.6 M ⊙ on average,
outside the main filament (between the two contours); and complete down to ∼ 4.5 M ⊙ within it.


18

**Supplementary Figure 2 — Completeness level of the core sample of Supplementary Table 1.**
We have performed Monte-Carlo simulations to investigate the sample completeness level as a
function of background intensity (red and black curves) and source confusion (blue curve). Synthesized cores are placed (a) on the worst-sensitivity background image, which was determined by
_getsources_ after subtracting cores of Supplementary Table 1 from Fig. 1, for background confusion
tests; and (b) on the original image containing real cores, for source confusion tests. The observations are then simulated and the cores extracted as for the real data. Confusion, due to either a
strong background, or the proximity of bright sources, is minimized by the multi-scale approach
of _getsources_ . Simulations show that the core sample of Supplementary Table 1 is 90% complete
down to ∼ 1.6 ± 0.1 M ⊙ (red curve) and to ∼ 4.5 ± 1 M ⊙ (black curve) in, respectively, the medianand high-background areas outlined in Supplementary Fig. 1. The census of cores overlapping
with others remains 90% complete down to ∼ 2.4 ± 0.2 M ⊙ (blue curve).


19

**Supplementary Table 2** — Tests performed to evaluate the uncertainty of the reference CMF fit of Fig. 2b.

|Col1|Massrange γ|
|---|---|
|**Reference cumulative CMF of all cores extracted by****_ getsources_**<br>**with** 5σ** uncertainty derived from the mass uncertainties**<br>low-mass regime<br>(high-mass regime, 9 cores)<br>with a lower completeness level<br>CMF of the 94 most robust cores|>1.6 M⊙<br>−**0**.**96** ±** 0**.**02**<br>>1.6 M⊙<br>−**0**.**96** ±** 0**.**13**<br>1.6 −20 M⊙<br>−0.93 ± 0.02<br>(>20 M⊙)<br>(−1.3 ± 0.3)<br>>4.5 M⊙<br>−0.99 ± 0.04<br>>1.6 M⊙<br>−0.90 ± 0.02|
|CMF with core masses estimated in the optical thin approximation<br>Diﬀerential CMF with all cores and default assumptions|>1.6 M⊙<br>−0.98 ± 0.04<br>>1.6 M⊙<br>−0.90 ± 0.06|
|CMF built from cores extracted in a classic-cleaned image<br>in a merged (7 m + 12 m) image<br>with MRE-GaussClumps|>1.6 M⊙<br>−1.10 ± 0.05<br>>1.6 M⊙or >5 M⊙<br>−1.10 ± 0.04<br>>1.6 M⊙or >5 M⊙<br>−1.08 ± 0.04|



Notes: CMFs are fitted by power-laws of the form _N_ (> log( _M_ )) ∝ _M_ [γ], except for the differential CMF where
the power-law is _dN_ / _d_ log( _M_ ) ∝ _M_ [γ] . Several mass ranges are used to fit the CMFs of less-constrained core
samples derived from the merged (7 m + 12 m) image and the MRE-GaussClumps algorithm. Except when
specified otherwise, all uncertainties given here are 1σ.


20


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: observational_alma_primary",
  "failed_quote": "Here we present 1.3 mm observations, obtained with ALMA, the world’s largest interferometer, of the active star-formation region W43-MM1"
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "power laws; fitting algorithm not stated",
  "failed_quote": "(no quote given)"
 }
]
```
