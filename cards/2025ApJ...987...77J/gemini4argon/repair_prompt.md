# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...987...77J\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version May 13, 2025
Typeset using L [A] TEX **twocolumn** style in AASTeX631


**Why** **is** **the** **Star** **Formation** **Rate** **Proportional** **to** **Dense** **Gas** **Mass?**


Sihan Jiao, [1] [Fengwei](http://orcid.org/0000-0001-5950-1932) Xu, [2, 3, 4] Hauyu [Baobab](http://orcid.org/0000-0003-2300-2626) Liu, [5, 6] Yuxin Lin, [7] Jingwen Wu, [8, 1] Zhi-Yu Zhang, [9, 10]

Zhiqiang Yan, [9, 10] Di Li, [11, 1] [Chao-Wei](http://orcid.org/0000-0002-9390-9672) Tsai, [1, 12, 8] Yongkun Zhang, [1, 8] Linjing Feng, [1, 8] Ke [Wang](http://orcid.org/0000-0002-7237-3856), [2]

Zheng Zheng, [1, 8] Fanyi Meng, [13, 8] Hao Ruan, [8, 1] Fangyuan Deng, [8, 1] and [Keyun](http://orcid.org/0009-0003-2243-7983) Su 2


1 _National_ _Astronomical_ _Observatories,_ _Chinese_ _Academy_ _of_ _Sciences,_ _20A_ _Datun_ _Road,_ _Chaoyang_ _District,_ _Beijing_ _100012,_ _China_
2 _Kavli_ _Institute_ _for_ _Astronomy_ _and_ _Astrophysics,_ _Peking_ _University,_ _Beijing_ _100871,_ _People’s_ _Republic_ _of_ _China_
3 _Department_ _of_ _Astronomy,_ _School_ _of_ _Physics,_ _Peking_ _University,_ _Beijing,_ _100871,_ _People’s_ _Republic_ _of_ _China_
4 _I._ _Physikalisches_ _Institut,_ _Universit¨at_ _zu_ _K¨oln,_ _Z¨ulpicher_ _Str._ _77,_ _D-50937_ _K¨oln,_ _Germany_
5 _Department_ _of_ _Physics,_ _National_ _Sun_ _Yat-Sen_ _University,_ _No._ _70,_ _Lien-Hai_ _Road,_ _Kaohsiung_ _City_ _80424,_ _Taiwan,_ _R.O.C._
6 _Center_ _of_ _Astronomy_ _and_ _Gravitation,_ _National_ _Taiwan_ _Normal_ _University,_ _Taipei_ _116,_ _Taiwan_
7 _Max-Planck-Institut_ _f¨ur_ _Extraterrestrische_ _Physik,_ _Giessenbachstr._ _1,_ _D-85748_ _Garching_ _bei_ _M¨unchen,_ _Germany_
8 _University_ _of_ _Chinese_ _Academy_ _of_ _Sciences,_ _Beijing_ _100049,_ _China_
9 _School_ _of_ _Astronomy_ _and_ _Space_ _Science,_ _Nanjing_ _University,_ _Nanjing_ _210093,_ _China_
10 _Key_ _Laboratory_ _of_ _Modern_ _Astronomy_ _and_ _Astrophysics,_ _Ministry_ _of_ _Education,_ _Nanjing_ _210093,_ _China_
11 _New_ _Cornerstone_ _Science_ _Laboratory,_ _Department_ _of_ _Astronomy,_ _Tsinghua_ _University,_ _Beijing_ _100084,_ _China_
12 _Institute_ _for_ _Frontiers_ _in_ _Astronomy_ _and_ _Astrophysics,_ _Beijing_ _Normal_ _University,_ _Beijing_ _102206,_ _China_
13 _Department_ _of_ _Astronomy,_ _Tsinghua_ _University,_ _Beijing_ _100084,_ _People’s_ _Republic_ _of_ _China_


ABSTRACT

One of the most profound empirical laws of star formation is the Gao-Solomon relation, a linear
correlation between the star formation rate (SFR) and the dense molecular gas mass. It is puzzling
how the complicated physics in star-formation results in this surprisingly simple proportionality. Using
archival _Herschel_ and Atacama Large Millimeter/submillimeter Array Observations, we derived the
masses of the most massive cores ( _M_ core [max] [) and masses of the gravitationally bound gas (] _[M]_ [ bound] gas ) in the
parent molecular clouds for a sample of low-mass and high-mass star-forming regions. We discovered a
significant correlation log( _M_ core [max] _[/M]_ _[⊙]_ [) = 0] _[.]_ [506 log(] _[M]_ [ bound] gas _/M_ _⊙_ ) _−_ 0 _._ 32. Our discovered _M_ core [max] [-] _[M]_ [ bound] gas
correlation can be approximately converted to the Gao-Solomon relation if there is (1) a constant
30% efficiency of converting _M_ core [max] [to] [the] [mass] [of] [the] [most] [massive] [star] [(] _[m]_ [max] star [),] [and] [(2)] [if] [SFR] [and]
_m_ [max] star [are tightly related through log(SFR] _[/]_ [(] _[M]_ _[⊙]_ [yr] _[−]_ [1] [)) = 2] _[.]_ [04 log(] _[m]_ [max] star _[/M]_ _[⊙]_ [)] _[−]_ [5] _[.]_ [80.] [Intriguingly, both]
requirements have been suggested by previous theoretical studies (c.f. Yan et al. 2017). Based on this
result, we hypothesize that the Gao-Solomon relation is a consequence of combining the following three
non-trivial relations (i) SFR vs. _m_ [max] star [,] [(ii)] _[m]_ [max] star [vs.] _[M]_ [ max] core [,] [and] [(iii)] _[M]_ [ max] core [vs.] _[M]_ [ bound] gas . This finding
may open a new possibility to understand the Gao-Solomon relation in an analytic sense.


_Keywords:_ Star formation(1569) — Initial mass function(796) — Molecular clouds(1072)


1. INTRODUCTION


The Gao-Solomon relation (Gao & Solomon 2004)



_M_ g [dense] as
SFR = 1 _._ 8 _×_ 10 _[−]_ [8]
1 _M_ _⊙_
�



�



_M_ _⊙_ yr _[−]_ [1] _,_ (1)



was first discovered in the spatially unresolved surveys
of the star-formation rates (SFR) and the masses of

2


the dense molecular gas reservoir ( _M_ gas [dense] ) [1] in external
galaxies. This tight linear relation was found to be valid
over an extremely wide range of _M_ gas [dense], which makes it
a broadly applied recipe of star formation in the studies
of galaxy formation and evolution (Schinnerer & Leroy
2024). As unresolved observations on individual galaxies
always cover a large number of star-forming molecular
clouds, the Gao-Solomon relation may be understood
by the central limit theorem (CLT). For example, one
might consider that each unit of _M_ gas [dense] in the molecular
clouds provides an equal chance to randomly sample a
universal stellar initial mass function (IMF) through an
identical process (hereafter referred to as the stochastic
picture).
It became puzzling when resolving a linear correlation
between SFR and _M_ gas [dense] in samples of Galactic molecular gas clumps or clouds (Wu et al. 2005, 2010; Lada
et al. 2012) [2] . It implies that the low-mass (e.g., Taurus
molecular cloud, _∼_ 2 _._ 0 _×_ 10 [4] _M_ _⊙_ ; Goldsmith et al. 2008)
and high-mass (e.g., W49A, _∼_ 2 _._ 0 _×_ 10 [5] _M_ _⊙_ ; Lin et al.
2016) star-forming clouds follow a universal efficiency
to convert their _M_ gas [dense] to the masses of the forming
stellar cluster ( _m_ [cluster] star ), in spite of the very different
stellar mass distribution. In the stochastic picture, the
reason why the Taurus molecular cloud is not forming
O-type stars is explained by its limited _M_ gas [dense] . Since
the IMF has a power-law profile at the high-mass end
(e.g., Kroupa 2001), the low _M_ gas [dense] leads to a very low
probability of obtaining samples from the high-mass end
of the IMF. If it is this case, then observing ten Taurus
mass molecular clouds will still provide a chance to detect a number of forming OB stars that are as massive as
those in W49A; and the overall SFR of the ten low-mass
molecular clouds is the same as the SFR of W49A. At
this moment, the stochastic picture is merely a mathematical implementation of an empirical law, the IMF.
The underlying physics to support this implementation


1 We note that the ordinary Gao-Solomon relation was a correlation between the HCN luminosity and the infrared luminosity.
In the earlier works, HCN was regarded a tracer of high-density
molecular gas (e.g., Evans 1999). However, recent surveys of
star-forming regions suggested that a significant fraction of the
HCN J=1–0 emission originates from low-density regions (e.g.,
Pety et al. 2017; Kauffmann et al. 2017; Evans et al. 2020; Dame
& Lada 2023). In these low-density regions, HCN emissions can
be excited by electron collisions, allowing them to trace UV photons and feedback processes rather than dense gas (Goldsmith &
Kauffmann 2017; Kauffmann et al. 2017; Goicoechea et al. 2022;
Jones et al. 2023; Santa-Maria et al. 2023). Therefore, the ordinary Gao-Solomon relation may be alternatively explained by
feedback-driven HCN emission instead of the correlation between
_M_ gas [dense] and SFR. Nevertheless, in spite of the ambiguity in the
interpretation of HCN luminosity, _M_ gas [dense] and SFR are indeed
correlated (more in Footenote 3; Jiao et al. submitted).

2 Note that Lada et al. (2012) re-scaled the ordinary Gao-Solomon
relation upward to match the star-formation rated derived based
on YSO countings in molecular clouds in the Solar neighborhood.



is not yet clear. Whether or not this picture is realistic
is doubtful.
In this work, we attempt to explain the Gao-Solomon
relation with an alternative picture. Our main hypothesis is that the mass of the most massive core ( _M_ core [max] [) in a]
molecular cloud is determined by the mass of the parent
gravitational bound gas reservoir ( _M_ gas [bound] ). In addition, we hypothesize that the most massive star forms
in the most massive core at an order-unity mass conversion efficiency (i.e., the star-forming efficiency). Finally,
motivated by the studies of Weidner et al. (2013), Yan
et al. (2017), and Yan et al. (2023), we hypothesize that
the star-formation process does not stochastically sample the IMF. Instead, there might be robust correlations
between the stellar mass distribution in a cluster, the
star formation rate, and _m_ [max] star [.] [These] [relations] [repre-]
sent various underlying physical processes that are also
not yet clear but may be investigated in future theoretical studies.
With these hypotheses, the SFR can be linked to
_M_ gas [bound] (and thus _M_ gas [dense] ) through the correlations of (i)
SFR vs. _m_ [max] star [,] [(ii)] _[m]_ [max] star [vs.] _[M]_ [ max] core [,] [and] [(iii)] _[M]_ [ max] core [vs.]
_M_ gas [bound] . The Gao-Solomon relation can be explained if
the combination of these three non-trivial correlations
occurs to yield an approximately linear correlation between SFR and _M_ gas [bound], and if _M_ gas [bound] _∼_ _M_ gas [dense] (Jiao
et al. submitted) [3] .
Our hypothesized scenario was motivated by two previous observational results. First, retrieving 139 young
star clusters, Weidner et al. (2013) have found that
the mass of the most massive star ( _m_ [max] star [)] [of] [a] [cluster]
is too tightly correlated with _m_ [cluster] star to be reconciled
with a stochastic sampling of the IMF. Second, the recent (sub)millimeter dust continuum observations also
showed a positive correlation between massive star immediate gas reservoir _M_ core [max] [and] [parsec-scale] [molecular]
clump mass _M_ clump (Lin et al. 2019; Xu et al. 2024a,b).
To test our hypotheses, we examined the correlation between _M_ core [max] [and] _[M]_ [ bound] gas based on the _Her-_
_schel_ and Atacama Large Millimeter/submillimeter Array (ALMA) observations on a sample of nearby and
distant star-forming molecular clouds. Then, we dis

3 Here, we are pushing forward to use _M_ gasbound to substitute the
concept of _M_ gas [dense] referred in the Gao-Solomon relation (Gao
& Solomon 2004). This is to amend an issue that the ordinary
Gao-Solomon relation vaguely defined how _dense_ the gas needs
to be in order to form stars. As this field is maturing, _M_ gas [dense]
will naturally be replaced by a more specific quantity that is
physically meaningful. Nevertheless, these two quantities are not
unrelated. In many but not all star-forming regions, we found
_M_ gas [bound] _∼_ _M_ gas [dense] if _M_ gas [dense] is measured in the same way as Gao
& Solomon (2004) while _M_ gas [bound] is measured in the say described
in Section 3.2 (Jiao et al. submitted; also see the related discussion in Bonnell et al. 2003; Xu et al. 2023; V´azquez-Semadeni
et al. 2017). With this substitution, our discussion is also not
subject to the ambiguity in the interpretation of the HCN luminosity (see Footnote 1).

-24°00'


30'


-25°00'



Decoding SFR versus _M_ dense relation 3


-17°53'


54'


55'


56'


57'


58'







16 [h] 30 [m] 28 [m] 26 [m] 24 [m]


RA (J2000)



18 [h] 14 [m] 24 [s] 18 [s] 12 [s] 06 [s]


RA (J2000)



**Figure** **1.** The example nearby cloud Ophiuchus (left) and distant cloud G012.80 (right). The background shows the H 2
column density map in logarithmic scale. The parental gravitational bound gas is defined by the green contours, within which
the _M_ gas [bound] is calculated. The extracted dense cores are marked with yellow ellipses and the most massive one is highlighted
in red color. For G012.80, the ALMA-IMF 1.3 mm dust continuum emission is shown in black contours: 0.02, 0.06, and 0.18
Jy beam _[−]_ [1] . The scale bar of 1 pc is shown on the bottom.



cuss how _M_ core [max] [and] _[ M]_ [ bound] gas may be related to the SFR,
and discuss how these relations might be comprehended
by an optimal sampling of the stellar initial mass function (IMF) rather than a stochastic sampling of it (c.f.
Kroupa et al. 2013; Weidner & Kroupa 2004; Schulz
et al. 2015; Yan et al. 2017, 2023). Finally, we discuss the possibility that the core-formation does not randomly sample the core mass function (CMF) of which
the shape is similar with that of the IMF.
The observations are introduced in Section 2. Our
methodology for deriving _M_ core [max] [and] _[M]_ [ bound] gas and their
correlation are described in Section 3. In Section 4.1, we
discuss the links of _M_ core [max] [and] _[M]_ [ bound] gas to the SFR and
the Gao-Solomon relation. A discussion about how the
observed _M_ core [max] [may] [not] [be] [consistent] [with] [randomly]
sampling the CMF, is provided in Section 4.2. Our conclusion is given in Section 5.


2. OBSERVATIONS


2.1. _Herschel_ _dust_ _continuum_ _observation_


We utilized the archival _Herschel_ data to calculate the
mass of the most massive core formed in a gravitationally bound gas structure and its parental gravitationally
bound gas mass.
For the nearby clouds, we retrieved the _Herschel_
Gould Belt survey (HGBS) data that were taken at
70/160 _µ_ m using the PACS instrument (Poglitsch 2010)
and at 250/350/500 _µ_ m using the SPIRE instrument



(Griffin 2010). The HGBS [4] took a census in the nearby
(0.5 kpc) molecular cloud complexes for an extensive
imaging survey of the densest portions of the Gould Belt,
down to a 5 _σ_ column sensitivity of _N_ H2 _∼_ 10 [21] cm _[−]_ [2]

or _A_ V _∼_ 1 (Andr´e et al. 2010). All target fields were
mapped in two orthogonal scan directions at a scanning
speed of 60 _[′′]_ s _[−]_ [1] in parallel mode, acquiring data simultaneously in five bands. The angular resolution in
this observation mode is 7.6 _[′′]_ at 70 _µ_ m, 11.5 _[′′]_ at 160 _µ_ m,
18.2 _[′′]_ at 250 _µ_ m, 25.2 _[′′]_ at 350 _µ_ m, and 36.9 _[′′]_ at 500 _µ_ m.
Data were reduced using _Herschel_ Interactive Processing
Environment (HIPE) version 7.0.
For distant and massive clouds, we retrieved the 70,
160, 250, 350, and 500 _µ_ m images from the _Herschel_ Infrared Galactic plane Survey (Hi-GAL; Molinari et al.
2010). Since we are interested in both compact and
extended structures, we adopt extended emission products, which have been corrected for absolute zero points
based on images taken by the _Planck_ space telescope.


2.2. _ALMA-IMF_ _observation_ _dataset_


To resolve the massive dense cores in distant clouds,
we retrieved the ALMA large project ALMA-IMF


4 Detailed observations and data reductions are available
on the HGBS archives webpage: HTTP://gouldbeltherschel.cea.fr/archives. The reduced SPIRE/PACS maps
for all nearby molecular clouds also are retrieved from the same
website.

4





10 [3]


10 [2]


10 [1]



































10 [0]



|Power-law<br>Spearman<br>95%Confi<br>(Outlierse|Col2|Col3|=0 .289<br>e-07<br>=0214|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|Power-law<br>Spearman<br>95% Confi<br>~~(Outliers e~~|Power-law<br>Spearman<br>95% Confi<br>~~(Outliers e~~|slope: 0.506;<br> cc. 0.83; p=7.8<br> dence Interval<br>~~ xcluded): 0549~~|=0.289<br>  e-07<br>~~  =0214~~|=0.289<br>  e-07<br>~~  =0214~~|=0.289<br>  e-07<br>~~  =0214~~|=0.289<br>  e-07<br>~~  =0214~~|
|<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|~~ .~~<br> cc. 0.96; p=1.9<br> uds<br> uds<br> uds affected by|~~  .~~<br>  e-10<br>  missing flux|Orion<br>~~G00~~<br>G010<br>~~G32729~~<br>G337.92<br>G351.~~7~~7<br>~~W~~|Orion<br>~~G00~~<br>G010<br>~~G32729~~<br>G337.92<br>G351.~~7~~7<br>~~W~~|~~867~~<br>.62<br><br>~~W~~43<br>~~5~~1|
|<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo||||||
|<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|||~~G3~~|~~G3~~|~~G3~~|
|||Cha<br>Lu~~p~~I<br>~~LupIII~~<br>~~L~~upIV<br>P~~i~~pe|~~A~~qui<br>mI<br><br>Ophiuch~~u~~s<br>~~Pe~~rsu<br>Ta~~u~~rus|~~la~~<br>s<br>~~G0~~<br><br>G3|~~1~~2.80<br>~~.~~<br>G32<br>~~G~~333.60<br>G<br>53.41|~~.~~<br>8.25<br>338.93|
|||Cha<br>Lu~~p~~I<br>~~LupIII~~<br>~~L~~upIV<br>P~~i~~pe|~~A~~qui<br>mI<br><br>Ophiuch~~u~~s<br>~~Pe~~rsu<br>Ta~~u~~rus||||
|||~~M~~usca<br>|||||
|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|01<br>102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|


**Figure 2.** The most massive core mass _M_ core [max] [versus its parental gravitational bound gas] _[ M]_ gas [ bound] . The blue stars show the values
as well as the uncertainties in the case of nearby clouds, while the orange hexagons stand for massive and distant clouds. All the
values are listed in Table 1. The black solid line represents the scaling relation for all the cloud sample _M_ gas [bound] _∝_ ( _M_ core [max] [)] [0] _[.]_ [506] [,]
with a Spearman correlation coefficient of 0.83 and p-value _≪_ 0.001. The standard deviation of linear regression residual _σ_ is
0.29 and the gray-shaded region corresponds to the regimes with 95% confidence interval. The _M_ core [max] [measurements] [of] [G327.29,]
G328.25, G351.77, and G353.41 are potentially underestimated due to missing fluxes (Section 3.3). After excluding them, the
power-law index becomes a steeper of 0.55 but the correlation becomes more significant with a Spearman correlation coefficient
of 0.96 and tighter with a standard deviation of the linear regression residual ( _σ_ ) of 0.21.



1.3 mm continuum data [5] (Motte et al. 2022; Ginsburg
et al. 2022). Fifteen massive star-forming regions were
carefully selected: 1) to be massive enough for sampling
the initial mass function; 2) to be located at distances
between 2 and 5.5 kpc for both resolving core-like structures and covering the entire extent of the parsec-size
clouds with ALMA mosaics; 3) to be the representative
protocluster per complex except for two fully covered
cloud complexes W51 and W43; 4) to cover various evolutionary stages from IR-quiet to IR-bright (Motte et al.
2018a).
The ALMA-IMF consortium produces the 1.3 mm
dust continuum images where the free-free contribution
was subtracted based on the H41 _α_ emission (Galv´anMadrid et al. 2024). A caveat is that the hydrogen radio
recombination lines may have maser effect in some regions (Martin-Pintado et al. 1989; Jim´enez-Serra et al.
2013; Zhu et al. 2022), while we assumed that this does


5 [https://www.almaimf.com/](https://www.almaimf.com/)



not significantly bias the intensities of free-free emission
in the regions we analyzed. We used free-free subtracted
images released by ALMA-IMF team [6] . These images
have angular resolution from 0 _[′′]_ _._ 3 to 1 _[′′]_ _._ 5 to obtained a
matched spatial resolution of 2000 AU ( _∼_ 0.01 pc). The
achieved rms noises are 0.03–0.18 mJy beam _[−]_ [1], which
correspond to a comparable point mass sensitivity of
0.15 _M_ _⊙_ at 1.3 mm. The maximum recoverable scale is
up to 0.1–0.2 pc (see Figure 6 in Ginsburg et al. 2022).
For most cases, this is adequate for our core-scale studies. We will discuss the effect of missing flux when it is
relevant.


3. RESULTS


3.1. _The_ _most_ _massive_ _core_


6 [https://dataverse.harvard.edu/dataverse/alma-imf](https://dataverse.harvard.edu/dataverse/alma-imf)

Decoding SFR versus _M_ dense relation 5



We apply a commonly-used source extraction algorithm `SExtractor` [7] (Bertin & Arnouts 1996). For each
image, we extract sources on the background-subtracted
emission maps based on the local threshold set by three
times noise rms maps. For more details, please refer to
Appendix B. As examples, we show the `SExtractor` extracted cores in Ophiuchus (nearby cloud) and G012.80
(distant cloud) in Figure 1.
For nearby clouds, the _N_ H2 images (derived with SED
fitting, Appendix A) were smoothed to a consistent spatial resolution of 0.03 pc. Following the procedure in
Appendix B, the most massive core mass ( _M_ core [max] [)] [can]
be calculated by summing up _N_ H2 from all the pixels
that belongs to the core by



_∼_
from specific dust opacity ( 36%, both from dust opacity and gas-to-dust ratio; Sanhueza et al. 2017), distance
( _∼_ 20%) and temperature (Table 3). The assumed dust
temperature and the derived core mass are listed in Table 1. The most massive core is highlighted with red
color in Figure 1.
We emphasize that in this study, all the core-like
structures in nearby and distant molecular clouds were
extracted using the same procedure and from maps with
the same spatial resolution of 0.03 pc for consistency. As
shown in Table 1, the extracted cores have deconvolved
radii from 0.04 to 0.23 pc, with a median value of 0.1 pc.
We conventionally refer to these extracted structures as
cores hereafter. We note that the spatial resolutions we
are using are coarser than the native resolutions in the
ALMA-IMF and HGBS data. Therefore, our derived
most massive core properties are not necessarily consistent with those found in the previous publications of
those consortia that were based on the native resolutions
(e.g., K¨onyves et al. 2015; Louvet et al. 2024).


3.2. _Parental_ _gravitationally_ _bound_ _gas_


The column density probability distribution function
(N-PDF) is a widely-used diagnosis to quantify the statistical distribution of gas and to identify gravitationally
bound structures in clouds (e.g., Chen et al. 2018; Jiao
et al. 2022b). Observations and numerical simulations
have revealed that the power-law tails of N-PDFs trace
the high column density, self-gravitating dense gas that
is anticipated to collapse to form stars (Kainulainen &
Tan 2013; Lombardi et al. 2015; Schneider et al. 2015).
This work utilizes N-PDF to assess the self-gravitating
mass across a diverse sample of molecular clouds.
By defining the normalized column density on the logarithmic scale,


_η_ = ln( _N_ _H_ 2 _/⟨N_ _H_ 2 _⟩_ ) (4)


the distribution can be written as



_M_ core [max] [=] _[ A][µm]_ [H]



_∈_ core
� _N_ H2 _,_ (2)

pixel



where _µ_ = 2 _._ 8 is the mean molecule weight in the interstellar medium (Kauffmann et al. 2008), _m_ H is the mass
of a hydrogen atom, and _A_ is the area of the pixel.
For distant clouds, we also smoothed the 1.3 mm freefree emission subtracted continuum images to a consistent spatial resolution of 0.03 pc, i.e., an angular resolution of _∼_ 1 _[′′]_ _._ 1 to _∼_ 3 _[′′]_ _._ 1, depending on the distance. Following the same core extraction procedure but with the
intensity map as input, we obtain the flux density of the
most massive cores for the massive cloud sample. Assuming a uniform temperature gray body emission from
dust cores, the total gas mass can be obtained by



_M_ core [max] [=] _[ −]_ _S_ 1 [int] _._ 3mm _[d]_ [2]



_S_ 1 [peak] _._ 2mm



_S_ 1 [int] _._ 3mm _[d]_ [2]

[Ω] [beam] _[B]_ [1] _[.]_ [3mm] [(] _[T]_ [dust] [)]
_κ_ 1 _._ 3mm _B_ 1 _._ 3mm ( _T_ dust ) _[×]_ _S_ [peak]



�



_×_ ln



1 _−_ Ω beam _BS_ 11 [peak] _.._ 3mm3mm ( _T_ dust )

�



�



_._



(3)


Here, _S_ 1 [int] _._ 3mm [is] [the] [integrated] [monochromatic] [flux] [of]
core at 1.3 mm, _d_ is the distance to the cloud, _κ_ 1 _._ 3mm =
0 _._ 01 cm [2] g _[−]_ [1] is the specific dust opacity interpolated to
1.3 mm assuming _β_ = 1 _._ 8 (Ossenkopf & Henning 1994),
_B_ _ν_ ( _T_ dust ) is the Planck function at a given dust temperature _T_ dust . The first term in Equation 3 represents the
optically thin ( _τ_ 1 _._ 3mm _≪_ 1) dust case. Ω beam is the solid
angle of the beam, _S_ 1 [peak] _._ 3mm [is] [the] [monochromatic] [peak]
flux. We tried three different methods to estimate dust
temperature, which are outlined in Appendix C. These
three methods yielded largely consistent results in our
subsequent statistical analyses. We adopted the method
two as the fiducial one, since the other two methods led
to unrealistically large _M_ core [max] [(e.g.,] _[>]_ [10] [3] _[M]_ _[⊙]_ [)] [for] [a] [few]
sources (Table 3). The uncertainty of dust mass comes


7 [https://sextractor.readthedocs.io/](https://sextractor.readthedocs.io)



where _η_ _t_ is the transitional column density in logarithmic normalized units.
Considering the sensitivities, map area, as well as the
requirement for a last closed contour (Alves et al. 2017),
we set an optimal column density cut-off ( _N_ cut ) for each
cloud, which is listed in Table 1. We then fit the N-PDF
of each cloud above this cutoff using the Maximum Likelihood Estimation (MLE; Clauset et al. 2009). This approach avoids the need to pre-bin the observed column
density distributions, thereby circumventing the potential pitfalls associated with binning (Virkar & Clauset
2012). To identify the transitional column density (both
the logarithmic normalized value, _η_ _t_, and the absolute
value, _N_ threshold ) and to estimate the uncertainties of



_p_ _η_ ( _η_ ) =



_M_ (2 _πσ_ _η_ [2] [)] _[−]_ [0] _[.]_ [5] _[e]_ _[−]_ [(] _[η][−][µ]_ [)] [2] _[/]_ [(2] _[σ]_ _η_ [2] [)] ( _η_ _< η_ _t_ )

_,_ (5)

� _Mp_ 0 _e_ _[−][αη]_ ( _η_ _> η_ _t_ )

6


the fitted parameters, we employed a Markov Chain
Monte Carlo (MCMC) approach using the Python package `EMCEE` (Foreman-Mackey et al. 2013). The threshold
column densities are summarized in Table 1 and are presented in Figure 1, 6, 7, and 8.
We evaluated the mass of the parental gravitationally bound gas, _M_ gas [bound], by integrating the mass above
the column density threshold (the turning point between
log-normal and power-law), i.e.,











+ _∞_
_M_ gas [bound] = _M_ ( _N_ ) _dN,_ (6)
� _N_ threshold





which are listed in Table 1.


3.3. _Mass_ _correlation_ _between_ _most_ _massive_ _core_ _and_
_gravitationally_ _bound_ _gas_


As shown in Figure 2, the mass of the most massive core _M_ core [max] [is] [positively] [correlated] [with] [the] [mass]
of the parental gravitationally bound gas _M_ gas [bound] across
three magnitudes of _M_ gas [bound], from 10 [2] to 10 [5] _M_ _⊙_ . The
nearby cloud samples independently depict this correlation while the distant cloud samples populate more
measurements in the range of _M_ gas [bound] =10 [4] –10 [5] _M_ _⊙_ .
With a linear regression of all the cloud sample, one
can obtain the correlation


log( _M_ core [max] _[/M]_ _[⊙]_ [) = 0] _[.]_ [506 log(] _[M]_ [ bound] gas _/M_ _⊙_ ) _−_ 0 _._ 32 _,_ (7)


with a Spearman coefficient of 0.83 and a p-value of 7.8
_×_ 10 _[−]_ [7] that is much lower than 0.001.
We note that the large data scatter exists for the distant cloud samples, which could be partly attributed to
missing flux in the ALMA-IMF images (Section 2.2).
As mentioned by Ginsburg et al. (2022), there are four
fields, G327.29, G328.25, G351.77, and G353.41 with insufficient ( _<_ 5%) short baselines to recover scales larger
than 0.1 pc. We found that by excluding these four
sources from our sample, the power-law index becomes
0.55, which is _∼_ 10% steeper than that derived from
the whole sample; the correlation becomes more robust
with the Spearman correlation coefficient of 0.96 and
the standard deviation of linear regression residual _σ_
becomes even tighter as 0.21. However, missing flux
may not yield underestimates of _M_ core [max] [by] [more] [than] [a]
few times. The large data scatter in the distant cloud
samples is likely largely intrinsic, for example, due to
the more profound or more rapid dynamical evolution
of the massive cores than the low-mass cores (e.g., due
to accretion, fragmentation, and jet/wind driven mass
loss Offner et al. 2014).


4. DISCUSSION


4.1. _Connection_ _to_ _the_ _star_ _formation_ _relation_



M [bound] gas [M ]


**Figure** **3.** The relation between SFR [theory] (c.f. Section
4.1) and _M_ gas [bound] (Section 3.2). The black dashed line shows
a linear regression to all data points, while the blue dashed
line shows a linear regression to the data points with outlier
(e.g., G327.29, G328.25, G351.77, and G353.41) rejection.
The orange line shows the Gao-Solomon relation (Gao &
Solomon 2004), which was adjusted upward by a factor of
2.7 as suggested by Lada et al. (2012).


If we consider that _M_ gas [bound] can approximate the
_M_ gas [dense] in the Gao-Solomon (i.e., SFR- _M_ gas [dense] ) relation
(Gao & Solomon 2004), then a comparison of our observed _M_ core [max] [-] _[M]_ [ bound] gas relation (Section 3.3) and the GaoSolomon relation immediately imply that there is a link
between _M_ core [max] [and] [SFR.] [Intriguingly,] [we] [found] [that]
if assuming a constant star-forming efficiency (SFE) of

_∼_
30%, then this link coincides with the theoretical SFR_m_ [max] star [relation that was derived based on an assumption]
of optimally sampling the IMF (more below; Yan et al.
2017).
For stars with masses less than 100 _M_ _⊙_, we extracted
the theoretical, galactic-scale SFR- _m_ [max] star [relation] [de-]
rived in Yan et al. (2017) by performing linear regression
to the model presented in their Figure 7. We obtained


log(SFR _/_ ( _M_ _⊙_ yr _[−]_ [1] )) = 2 _._ 04 log( _m_ [max] star _[/M]_ _[⊙]_ [)] _[ −]_ [5] _[.]_ [80] _[.]_ [(8)]


For a star-forming cloud, given the measurement of
_M_ gas [bound], the recipe to theoretically infer the SFR [theory]

then follows:


1. Derive _M_ core [max] [based on the observed] _[ M]_ [ max] core [-] _[M]_ [ bound] gas
relation (Equation 7).


2. Assume _m_ [max] star _[∼]_ [0.3] _[×][M]_ [ max] core


3. Apply the SFR- _m_ [max] star [relation] [(Equation] [8][)] [men-]
tioned above.


With this recipe, the measurements of _M_ gas [bound] in our
sample then allow us to infer SFR [theory] (see Appendix D

Decoding SFR versus _M_ dense relation 7


**Table** **1.** Parameters of the parent molecular clouds and the most massive cores


Parental molecular clouds Most massive cores _M_ _>_ 3 _M_ _⊙_ cores


Name Distance _N_ cut / _N_ threshold _M_ gas [bound] RA Dec Radius _M_ core [max] _n_ ( _M_ _>_ 3 _M_ _⊙_ ) _M_ tot


(pc) ( _×_ 10 [21] cm _[−]_ [2] ) ( _×_ 10 [3] _M_ _⊙_ ) (J2000) (J2000) (pc) ( _M_ _⊙_ ) ( _M_ _⊙_ )


Nearby clouds


Aquila 278 _±_ 13 3.55 / 6.69 [+0] _−_ 0 _[.]_ _._ [10] 04 6.43 [+1] _−_ 2 _[.]_ _._ [25] 57 18:29:56.9 -01:58:29.8 0.15 56.5 _±_ 16.9 89 673.0


Cham I 150 _±_ 14 0.63 / 2.94 [+0] _−_ 0 _[.]_ _._ [03] 03 0.48 [+0] _−_ 0 _[.]_ _._ [06] 06 11:06:31.9 -77:23:43.5 0.18 23.0 _±_ 6.9 8 64.2


Lupus I 151 _±_ 10 0.28 / 1.10 [+0] _−_ 0 _[.]_ _._ [20] 00 0.24 [+0] _−_ 0 _[.]_ _._ [04] 00 15:45:28.4 -34:24:02.6 0.12 6.4 _±_ 1.9 10 44.6


Lupus III 197 _±_ 13 0.45 / 1.61 [+0] _−_ 0 _[.]_ _._ [04] 04 0.21 [+0] _−_ 0 _[.]_ _._ [05] 05 16:08:48.1 -39:07:26.9 0.11 6.4 _±_ 1.9 3 16.4


Lupus IV 151 _±_ 10 0.50 / 0.75 [+0] _−_ 0 _[.]_ _._ [01] 01 0.45 [+0] _−_ 0 _[.]_ _._ [13] 10 16:01:34.4 -41:52:10.4 0.20 11.0 _±_ 3.3 4 23.6


Musca 160 _±_ 13 0.63 / 1.58 [+0] _−_ 0 _[.]_ _._ [02] 02 0.25 [+0] _−_ 0 _[.]_ _._ [04] 04 12:25:33.9 -71:42:06.1 0.19 5.4 _±_ 1.6 1 5.4


Ophiuchus 128 _±_ 6 1.41 / 3.25 [+0] _−_ 0 _[.]_ _._ [05] 07 0.96 [+0] _−_ 0 _[.]_ _._ [35] 20 16:26:27.8 -24:23:51.2 0.10 14.9 _±_ 4.5 15 115.7


Orion A 399 _±_ 19 0.71 / 2.05 [+1] _−_ 0 _[.]_ _._ [95] 16 26.58 [+4] _−_ 9 _[.]_ _._ [78] 13 05:35:13.5 -05:23:57.5 0.14 264.1 _±_ 79.2 249 4439.7


Perseus 256 _±_ 12 0.56 / 1.50 [+0] _−_ 0 _[.]_ _._ [01] 01 4.75 [+1] _−_ 0 _[.]_ _._ [18] 99 03:28:39.2 +31:18:40.6 0.15 41.1 _±_ 12.3 124 903.7


Pipe 180 _±_ 9 1.58 / 4.18 [+0] _−_ 0 _[.]_ _._ [01] 01 0.12 [+0] _−_ 0 _[.]_ _._ [04] 02 17:11:21.3 -27:26:17.6 0.08 6.9 _±_ 2.1 6 29.1


Taurus 156 _±_ 7 1.05 / 1.62 [+0] _−_ 0 _[.]_ _._ [03] 05 3.25 [+0] _−_ 0 _[.]_ _._ [65] 65 04:41:26.5 +25:23:57.2 0.23 26.7 _±_ 8.0 48 326.9


Distant and massive clouds


G008.67 3400 _±_ 300 7.9 / 13 _._ 3 [+0] _−_ 0 _[.]_ _._ [2] 2 45 [+13] _−_ 13 18:06:19.1 -21:37:31.45 0.08 70.1 _±_ 34.2 _· · ·_ _· · ·_


G010.62 5000 _±_ 500 11.2 / 18 _._ 7 [+0] _−_ 0 _[.]_ _._ [1] 1 38 [+11] _−_ 11 18:10:28.7 -19:55:49.60 0.12 163.8 _±_ 81.8 _· · ·_ _· · ·_


G012.80 2400 _±_ 200 19.9 / 35 _._ 6 [+0] _−_ 0 _[.]_ _._ [3] 3 17 [+5] _−_ 5 18:14:13.7 -17:55:43.07 0.05 32.1 _±_ 15.6 _· · ·_ _· · ·_


G327.29 2500 _±_ 500 6.3 / 14 _._ 7 [+0] _−_ 0 _[.]_ _._ [4] 4 16 [+5] _−_ 5 15:53:07.8 -54:37:06.31 0.04 67.1 _±_ 40.2 _· · ·_ _· · ·_


G328.25 2500 _±_ 500 6.3 / 14 _._ 4 [+0] _−_ 0 _[.]_ _._ [3] 3 39 [+11] _−_ 11 15:57:59.8 -53:58:00.18 0.05 24.6 _±_ 15.3 _· · ·_ _· · ·_


G333.60 4200 _±_ 700 15.1 / 22 _._ 7 [+0] _−_ 0 _[.]_ _._ [8] 6 23 [+6] _−_ 6 16:22:09.5 -50:05:58.17 0.08 60.2 _±_ 34.5 _· · ·_ _· · ·_


G337.92 2500 _±_ 500 7.1 / 15 _._ 1 [+0] _−_ 0 _[.]_ _._ [4] 3 26 [+7] _−_ 7 16:41:10.5 -47:08:03.61 0.07 115.1 _±_ 68.8 _· · ·_ _· · ·_


G338.93 3900 _±_ 1000 9.9 / 14 _._ 3 [+0] _−_ 1 _[.]_ _._ [4] 7 24 [+13] _−_ 9 16:40:34.2 -45:41:36.58 0.04 50.6 _±_ 35.8 _· · ·_ _· · ·_


G351.77 2000 _±_ 700 6.4 / 16 _._ 1 [+1] _−_ 1 _[.]_ _._ [8] 8 16 [+8] _−_ 8 17:26:42.5 -36:09:17.64 0.05 140.4 _±_ 86.8 _· · ·_ _· · ·_


G353.41 2000 _±_ 700 6.5 / 21 _._ 1 [+0] _−_ 0 _[.]_ _._ [6] 8 17 [+9] _−_ 9 17:30:26.1 -34:41:46.84 0.04 15.3 _±_ 9.5 _· · ·_ _· · ·_


W43 5500 _±_ 400 14.1 / 26 _._ 1 [+0] _−_ 0 _[.]_ _._ [2] 2 99 [+29] _−_ 29 18:47:47.0 -01:54:26.56 0.10 275.0 _±_ 131.0 _· · ·_ _· · ·_


W51 5400 _±_ 300 11.2 / 20 _._ 7 [+1] _−_ 2 _[.]_ _._ [2] 4 82 [+25] _−_ 24 19:23:43.9 +14:30:34.83 0.11 323.8 _±_ 143.7 _· · ·_ _· · ·_


Note—The properties of nearby clouds and distant massive clouds as well as their most massive cores are listed. _N_ cut : the cut

off column density of N-PDF. _N_ threshold : the transitional column density of N-PDF between log-normal and power-law. The

listed uncertainties are derived from the N-PDF fitting. _M_ gas [bound] : the parental gravitational bound gas. RA, Dec: equatorial


coordinates of the most massive core. _M_ core [max] [:] [the] [most] [massive] [core] [mass.] _[n]_ [(] _[M]_ _[>]_ [ 3] _[M]_ _⊙_ [)] [and] _[M]_ tot [(] _[M]_ _[>]_ [ 3] _[M]_ _⊙_ [):] [the] [number]


of cores with mass larger than 3 _M_ _⊙_, and their total mass. These two parameters are only counted for nearby clouds. The


full list of the fitted parameters of the N-PDF are presented and discussed in more detail in Jiao et al. submitted.



for a comparison with the observed SFR) and a relation
between SFR [theory] and _M_ gas [bound], which can be compared
with the Gao-Solomon relation. We remark that all rela


tions in this recipe are independent of the Gao-Solomon
relation, which is a relation between the observationally
constrained SFR and _M_ gas [dense] (approximately, _M_ gas [bound] ).

8


In this work, we followed Lada et al. (2012) to adjust the
ordinary Gao-Solomon relation upward, by multiplying
a constant factor 2.7.
As described in Section 1, we push forward to use
_M_ gas [bound] to substitute the concept of _M_ gas [dense] referred in
the Gao-Solomon relation. We plot the SFR [theory] and
_M_ gas [bound] of our sample in Figure 3. The black dashed line
shows a linear regression of all the data points, yielding a
slope of 1.03 across all clouds. The regression line aligns
well with the Gao-Solomon relation (Gao & Solomon
2004, shown as an orange line), which indicates that the
SFR- _m_ [max] star [relation] [quoted] [in] [our] [recipe] [is] [indeed] [prac-]
tical. We note that the SFR- _m_ [max] star [relation] [quoted] [in]
our recipe was derived for galactic scale star-formation.
It is intriguing to see that it is also applicable on the
spatial scale of molecular clouds. We do not yet have a
good explanation for it. This SFR- _m_ [max] star [may] [be] [more]
essential than it was originally thought although it could
also be a coincidence. To clarify it, it requires a deeper
understanding (or assumption) about the timescales and
efficiency of star formation in a molecular cloud. At this
moment, we can also regard Equation 8 as a relation being empirically constrained by the presented data, while
the theoretical derivation of Yan et al. (2017) is one way
to comprehend this empirical relation. The deeper discussion about the underlying physics of the SFR- _m_ [max] star
relation and its applicability is beyond the scope of our
present work.
For more insight, the linear correlation (e.g., SFR
_∝_ _M_ gas [bound] ) can be obtained from the combination of
_M_ core [max] _[∝]_ [(] _[M]_ [ bound] gas ) [0] _[.]_ [506] (Equation 7), _M_ core [max] _[∝]_ _[m]_ [max] star [,]
and SFR _∝_ ( _m_ [max] star [)] [2] _[.]_ [04] [(Equation] [8][),]


SFR _∝_ ( _m_ [max] star [)] [2] _[.]_ [04]






|3.0|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)|||||||||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)|||||||||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)|||||||||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)|||||||||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)|||||||||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)||<br> <br>|Nearby<br>1 < M <<br>~~ < M <~~|Clouds (<br>  50M<br>: <br>~~  0M~~<br>~~: ~~|Clouds (<br>  50M<br>: <br>~~  0M~~<br>~~: ~~|HGBS)<br>1.34<br>~~090~~|||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)||||<br>|<br>|~~.~~|~~.~~||
|0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>dN/dlog10 (Mcore)|||||||||



_∝_ ( _M_ core [max] [)] [2] _[.]_ [04] (9)

_∝_ (( _M_ gas [bound] ) [0] _[.]_ [506] ) [2] _[.]_ [04] _∝_ ( _M_ gas [bound] ) [1] _[.]_ [03]



2.0 1.5 1.0 0.5 0.0 0.5 1.0 1.5 2.0
log 10 (M core )


**Figure** **4.** CMF for the entire core catalog sample for the
nearby clouds. Two power-law fittings with mass ranges of
1 _< M_ _<_ 50 _M_ _⊙_ and 1 _< M_ _<_ 20 _M_ _⊙_ are adopted.


sults shows a slightly steeper slope of 1 _._ 11 [+0] _−_ 0 _[.]_ _._ [10] 10 [,] [and] [the]
correlation is 30% tighter.


4.2. _Indication_ _of_ _a_ _non-stochastic_ _sampling_ _of_ _core_

_mass_


In the studies of stellar clusters, it was found that
the observed correlation between _m_ [max] star [and] _[m]_ [cluster] star are
too tight to be consistent with the mathematical implementation of randomly sampling the IMF (Kroupa
et al. 2013; Weidner et al. 2013). As an amendment,
an alternative, optimal sampling scheme of the IMF has
been recently postulated (Kroupa et al. 2013; Weidner
et al. 2013; Yan et al. 2023). This new scheme deterministically lists the masses of all stars in a cluster. In
this case, the mass of the most massive star _m_ [max] star [in] [a]
stellar cluster directly depends on the total mass of the
enclosed stellar cluster _m_ [cluster] star .
Extensive studies have found that the shape of the
CMF resembles that of the IMF in both nearby ( _<_ 1
kpc) star-forming regions (Motte et al. 1998; Alves et al.
2007; K¨onyves et al. 2015) and more distant clouds (e.g.
Liu et al. 2018; Kong 2019; Su´arez et al. 2021; Cheng
et al. 2024; Louvet et al. 2024). Specifically, the highmass end ( _M_ _>_ 1 _M_ _⊙_ ) of the CMF can be expressed as
a power-law
_d_ _N_
(10)
_d_ log _M_ _[∝]_ _[M]_ [ Γ] _[,]_


where the power-law index is in the range of [ _−_ 1.35,
_−_ 1.00]. The mass function of the structures we identified (Section 3.1) from the maps of nearby clouds, with
the same spatial resolution of 0.03 pc (Figure 4), still
appears similar to the canonical IMF/CMF. In the highmass end, the power-law indices in various mass ranges
are consistent with the range of [ _−_ 1 _._ 35, _−_ 1] seen in other
previous studies of IMF/CMF. Therefore, we think it is
appropriate to discuss our identified structures in a con


This similarity between our deduced SFR [theory]  _M_ gas [bound] relation and the Gao-Solomon relation supports
the notion that star formation, from individual local
clouds to entire galaxies, is governed by a similar and
straightforward physical principle: the rate at which
molecular gas is converted into stars depends on the
mass of dense gas within the total gas reservoir (e.g.,
Lada et al. 2012; Evans et al. 2014, and Jiao et al. submitted). As the SFR-mass diagram is based on the
_M_ core [max] [-] _[M]_ [ bound] gas relation, the consistency suggests that
the linear correlation (a slope of 1) of the Gao-Solomon
relation may stem from the highly self-regulated starforming process when gravity is dominant.
Finally, we tested the effects of missing flux by rejecting the four potentially affected sources, G327.29,
G328.25, G351.77, and G353.41 (Section 3.3) from our
sample. In Figure 3, the blue dashed line shows the
linear regression to the remaining data points. The re

Decoding SFR versus _M_ dense relation 9








|Col1|Col2|Col3|
|---|---|---|
||Mmax<br>core = 500 M|Mmax<br>core = 500 M|
|101<br>Mmax<br>core [M ]|Cham-I<br>Pipe<br>Ophiuchus<br>Taurus<br>Perseus<br>Aquila<br>~~L~~upus-III<br>Lupus-IV<br>Lupus-I||
|101<br>Mmax<br>core [M ]|||













10 [2] 10 [3] 10 [4]

M gas [bound] [M ]












|Col1|Mm coa rex = 333 M|Col3|
|---|---|---|
||||
|101<br>Mmax<br>core [M ]|Cham-I<br>Pipe<br>Ophiuchus<br>Taurus<br>Perseus<br>Aquila<br>~~L~~upus-III<br>Lupus-IV<br>Lupus-I||
|101<br>Mmax<br>core [M ]|||



10 [2] 10 [3] 10 [4]

M gas [bound] [M ]


**Figure** **5.** The most massive cores from random sampling (Section 4.2). Upper and lower panels show the cases
that the largest possible core masses are artificially limited
to 150 _/_ SFE _M_ _⊙_ and 100 _/_ SFE _M_ _⊙_, respectively, where SFE
was assume to be 30%. The black crosses show the values as

well as the uncertainties for the observations. The blue and

orange violin plots outline the distribution of randomly sampled most massive cores for Γ = -1.00 case and Γ = -1.35 case,
while the median values of _M_ core [max] [from] [the] [mock] [data] [from]

random sampling are marked with blue and orange points.
We did not include the Musca cloud in the random sampling
because only one core with a mass higher than 3 _M_ _⊙_ in this

region.


text that is similar to how ‘cores’ were discussed in the

previous studies.
Enlightened by the aforementioned studies on stellar
clusters, here, we also discuss whether or not the observed _M_ core [max] [can be consistent with the implementation]



of randomly sampling the CMF (e.g., Equation 10). We
focus on the nearby clouds observed by the HGBS, in
which we obtained a complete sample of _>_ 3 _M_ _⊙_ cores
(given by the 3 _σ_ mass sensitivity). For each molecular cloud observed by HGBS, the number of _>_ 3 _M_ _⊙_
cores is denoted by _n_ ( _M_ _>_ 3 _M_ _⊙_ ). Using the following
five steps, we simulated the distribution of _M_ core [max] [assum-]
ing that the star-forming processes randomly sample the
CMF:


1. Generate a Core Sample Pool: We generate a sample of cores with mass distribution following the
CMF (Equation 8) described by a power-law exponent Γ (Γ = _−_ 1.0 and Γ = _−_ 1.35) and a low-mass
cutoff as 3 _M_ _⊙_, yielding a sample set of 10 [6] cores.
This initial pool of samples is denoted as set A.


2. Set A is filtered to retain only cores having mass
smaller than the total core mass of that cloud
and a hypothetical, largest possible core mass. In
this work, we tested the two assumptions: (1) the
largest possible stellar mass ( _m_ up ) is 150 _M_ _⊙_ (c.f.
Koen 2006), and (2) _m_ up is 100 _M_ _⊙_ (c.f. Weidner
& Kroupa 2004); in both cases, the largest probable core mass is assumed to be _m_ up _/_ SFE _M_ _⊙_,
where SFE=30%. This filtered subset is referred
to as set B. This step ensures that no individual
core in the sample exceeds the cloud’s total core

mass.


3. Random Sampling: From set B, we randomly select a subsample of _n_ ( _M_ _>_ 3 _M_ _⊙_ ) cores. The
selected subsample of cores form set C. If the
overall core masses in set C does not exceed
SFE _×M_ gas [bound], we accept set C and proceed to the
next step. Otherwise, we redo this step.


4. Identify the Most Massive Core: From set C, the
mass of the largest core is registered.


5. Repeat and Analyze: By repeating steps 3 and 4
for 5000 times, we can account for the stochastic nature of the random sampling. The resulting
distribution of _M_ core [max] [is] [analyzed] [using] [a] [kernel]
density estimation (KDE) plot (see Figure 5).


For both Γ = _−_ 1.00 and Γ = _−_ 1.35, we found that
the simulations yield broad (vertical) distributions of
_M_ core [max] [(Figure][ 5][).] [Based on this result, if the core forma-]
tion is indeed consistent with a random sampling of the
CMF, one would anticipate a large scatter in the observations of _M_ core [max] [versus] _[M]_ [ bound] gas ; in addition, the degree
of scatter is not sensitive to the assumed value of Γ. In
Figure 5, the standard deviation of the observed points
from a linear regression line is 0.077. However, if we replaced the observed _M_ core [max] [values] [with] [the] [those] [simu-]
lated based on randomly sampling the CMF (see above),
in the case with a maximum possible core mass 150 _/_ SFE
_M_ _⊙_, the mean standard deviation increases to 0.127 for

10


Γ = _−_ 1.00 and 0.139 for Γ = _−_ 1.35; in the case with
a maximum possible core mass 100 _/_ SFE _M_ _⊙_, the mean
standard deviation becomes 0.121 for Γ = _−_ 1.00 and
0.137 for Γ = _−_ 1.35, respectively. In other words, the
implementation of randomly sampling the CMF yielded
a too large scattering of _M_ core [max] [to be consistent with the]
observed values.
Moreover, the observed _M_ core [max] [-] _[M]_ [ bound] gas relation systematically falls below the expected distribution in the
simulations with Γ = _−_ 1.0 and Γ = _−_ 1.35 (Figure 5).
In the following, based on the cases of the Taurus and
Perseus regions, two of the nearest known sites of star
formation, we elaborate on why the implementation of
randomly samping the CMF tend to lead to overestimated _M_ core [max] [.] [From] [the] [HGBS] [observations,] [these] [two]
regions together have 172 cores that are more massive
than 3 _M_ _⊙_ while the mass of the most massive core is
41.1 _M_ _⊙_ . Given the larger number of cores, the _M_ core [max]
from random sampling would significantly exceed the
observed _M_ core [max] [.] [Here, we use a Monte Carlo simulation,]
using 10 [6] iterations, to test the likelihood of a cloud containing so many cores but no cores exceeding 41.1 _M_ _⊙_ .
Assuming a top-heavy CMF (Γ = _−_ 1.00) at the highmass end ( _M_ _>_ 3 _M_ _⊙_ ), and assuming the maximum
possible core mass is 150 _/_ SFE _M_ _⊙_, only 20 out of 10 [6]

clouds have no cores above 41.1 _M_ _⊙_ ; assuming the maximum possible core mass is 100 _/_ SFE _M_ _⊙_, only 21 out
of 10 [6] clouds have no cores above 41.1 _M_ _⊙_ . This indicates that the probability for all cores to be less than
41.1 _M_ _⊙_ is _∼_ 2 _×_ 10 _[−]_ [5] . Assuming the Salpeter CMF
(Γ = _−_ 1.35) case, the probability for all cores to be less
than 41.1 _M_ _⊙_ is 7.7 _×_ 10 _[−]_ [3] in the case that the maximum possible core mass is 150 _/_ SFE _M_ _⊙_, and is 8.1 _×_
10 _[−]_ [3] in the case that the maximum possible core mass
is 100 _/_ SFE _M_ _⊙_ . This test shows that the observed sample of _M_ core [max] [is] [inconsistent] [with] [random] [sampling] [from]
a CMF at a confidence level greater than _>_ 99.1 percent. Instead, we have to view the core-formation in the
Taurus and Perseus regions separately. Each of them is
relatively low-mass clouds that harbor limited numbers
of _>_ 3 _M_ _⊙_ cores and have the correspondingly, specific
values of _M_ core [max] [.] [Extending this argument to observe ten]
molecular clouds, each as massive as the Taurus molecular cloud, would increase the number of _M_ _>_ 3 _M_ _⊙_
cores tenfold. However, the _M_ core [max] [would] [remain] [con-]
stant at the lower mass level, insufficient to form OB
stars, challenging the stochastic picture.
As a summary, observed _M_ core [max] [-] _[M]_ [ bound] gas correlation is
inconsistent with randomly sampling the CMF in two
ways: (1) the observed _M_ core [max] [-] _[M]_ [ bound] gas relation is too
tight to be consistent with the simulation that randomly
sampling the CMF, and (2) the observed _M_ core [max] [-] _[M]_ [ bound] gas
relation systematically falls below the simulated _M_ core [max]
values. The number of _M_ _>_ _M_ threshold cores (with
_M_ threshold = 3 _M_ _⊙_ in our case), _n_ ( _M_ _>_ 3 _M_ _⊙_ ), is uncertain, which can be due to (i) noises (e.g., in the observational data), and (ii) the behavior of the algorithm



(i.e., the definition of cores). Considering random noises
in _n_ ( _M_ _>_ 3 _M_ _⊙_ ) in our simulation will increase the
scattering in the simulated _M_ core [max] [values,] [making] [them]
more inconsistent with the observations. Therefore, it
is only necessary to consider the systematic errors in
_n_ ( _M_ _>_ 3 _M_ _⊙_ ). Suppose that our core-identification algorithm (Section 3.1, Appendix B) yielded a large number of spurious identifications in each cloud such that
_n_ ( _M_ _>_ 3 _M_ _⊙_ ) was systematically overestimated, it may
indeed explain why the observed _M_ core [max] [-] _[M]_ [ bound] gas relation
systematically falls below the simulated _M_ core [max] [values.]
For instance, in the Taurus molecular cloud, we observe
_M_ core [max] [= 26] _[.]_ [7] _[ M]_ _[⊙]_ [while] _[ N]_ [= 48.] [To match the simulated]
median _M_ core [max] [with] [the] [observed] [value] [through] [random]
sampling, the values of _n_ ( _M_ _>_ 3 _M_ _⊙_ ) need to be 6 for
Γ = _−_ 1.0 and 12 for Γ = _−_ 1.35 under the 150 _/_ SFE
_M_ _⊙_ core mass limit case, and to be 6 for Γ = _−_ 1.0
and 13 for Γ = _−_ 1.35 respectively under the 100 _/_ SFE
_M_ _⊙_ core mass limit case. The values are significantly
smaller than the observed _n_ ( _M_ _>_ 3 _M_ _⊙_ ), indicating
that systematic errors in _n_ ( _M_ _>_ 3 _M_ _⊙_ ) alone cannot
fully explain the vertical offset in Figure 5. In addition,
from Figure 5, we can also see that it does little help
reducing the scattering in the simulated _M_ core [max] [.]


5. CONCLUSION


Based on the archival _Hershel_ and ALMA observations, we measured the masses of the most massive cores
( _M_ core [max] [)] [and] [the] [mass] [of] [the] [gravitational] [bound] [gas]
( _M_ gas [bound] ) in the parent molecular clouds from 11 Solar neighborhood clouds and 12 high-mass star-forming
regions. Our main findings are:


1. There exists a significant correlation
log( _M_ core [max] _[/M]_ _[⊙]_ [)] [=] [0] _[.]_ [506 log(] _[M]_ [ bound] gas _/M_ _⊙_ ) _−_ 0 _._ 32
for _M_ gas [bound] =10 [2] –10 [5] _M_ _⊙_ .


2. If we randomly draw samples from a core mass
function that has the same slope as the Salpeter
IMF (Γ = _−_ 1.35) or a top-heavy IMF (Γ = _−_ 1.00)
until there are as many _>_ 3 _M_ _⊙_ cores as any specific Solar neighbor cloud we analyzed, the _M_ core [max]
in the samples we drew will considerably exceed
the _M_ core [max] [observed] [in] [that] [Solar] [neighbor] [cloud,]
and the samples we drew appear too largely scattered to be consistent with the observational data.


3. For the 23 star-forming regions we analyzed, if
we assume a universal 30% efficiency of converting _M_ core [max] [to] [the] [mass] [of] [the] [most] [massive] [star]
( _m_ [max] star [)] [and] [then] [estimate] [the] [star] [formation] [rate]
(SFR) based on the log(SFR/( _M_ _⊙_ yr _[−]_ [1] )) = 2.04
log( _m_ [max] star [/] _[M]_ _[⊙]_ [)] _[−]_ [5.80] [relation] [inferred] [from] [an]
optimal sampling of the stellar IMF (Kroupa &
Weidner 2003; Yan et al. 2017), the derived SFR
will be consistent with the SFR expected from the
Gao-Solomon relation if _M_ [bound] can substitute the
gas

Decoding SFR versus _M_ dense relation 11



dense gas mass ( _M_ gas [dense], e.g., traced by HCN line
observations; Jiao et al. submitted).


Based on points 1 and 2, we hypothesize that clusterformation is a rather deterministic process. There may
be robust correlations between _M_ gas [bound], _M_ core [max] [,] _[M]_ [ max] star [,]
the overall cluster mass, and SFR. The underlying
physics is not yet clear. Intriguingly, we found that
the SFR- _M_ gas [bound] correlation may explain the approximately linear SFR- _M_ gas [dense] relation in the Gao-Solomon
theory. On the sub-galactic scales (e.g., _<_ 1 kpc), the linear Gao-Solomon relation may not be understood by a
combination of the central limit theory and proportionality. Instead, the simple proportionality between SFR
and _M_ gas [dense] may be a consequence of the combination of
multiple correlations, each of which may be understood
in an analytic/deterministic sense. This finding may
open a window to break down the long-lasting puzzles
on star-formation laws into focused and comprehensive
components.



_Facility:_ Herschel, Planck, JCMT, ALMA

_Software:_ CASA, Numpy, APLpy



1


2


3


4


5


6


7


8


9


10


11


12


13


14



We thank the referee for the useful suggestions. We
thank Dr. Eda Gjergo for very insightful discussion. We thank the high-quality ALMA-IMF data
products that have been shared online. Herschel
is an ESA space observatory with science instruments provided by European-led Principal Investigator consortia and with important participation from
NASA. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2017.1.01355.L ALMA is a
partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ.



15

16 S.J. is supported by NSFC grant nos. 11988101

17 and 12041302, by the National Key R&D Program

18 of China No. 2023YFA1608004. F.W.X is sup
19 ported by the National Science Foundation of China

20 (12033005) and funding from the European Union’s

21 Horizon 2020 research and innovation programme under

22 grant agreement No 101004719 (ORP). H.B.L. is sup
23 ported by the National Science and Technology Coun
24 cil (NSTC) of Taiwan (Grant Nos. 111-2112-M-110
25 022-MY3, 113-2112-M-110-022-MY3). We acknowledge

26 National Natural Science Foundation of China (NSFC)

27 under grants 12173016, 12041305. We acknowledge

28 the Program for Innovative Talents, Entrepreneur in

29 Jiangsu. We acknowledge the science research grants

30 from the China Manned Space Project, CMS-CSST
31 2021-A08 and CMS-CSST-2021-A07.



16


17


18


19


20


21


22


23


24


25


26


27


28


29


30


31



A. COLUMN DENSITY MAP



APPENDIX


the input _Herschel_ images at five bands. All the im


We perform pixelwise single-component modified
black-body spectral energy distribution (SED) fitting of

12


ages were convolved to a common angular resolution of
the largest telescope beam (36 _[′′]_ _._ 9) and then were regridded to have the same pixel size (4 _[′′]_ _._ 0). For the modified
black-body assumption, the flux density _S_ _ν_ at a certain
observing frequency _ν_ is given by


_S_ _ν_ = Ω _m_ _B_ _ν_ ( _T_ d )(1 _−_ _e_ _[−][τ]_ _[ν]_ ) _,_ (A1)


where Ω _m_ is the solid angle, _B_ _ν_ ( _T_ d ) is the Planck function at dust temperature _T_ d, and dust opacity _τ_ _ν_ is given
by
_τ_ = _κ_ _ν_ _µm_ H _N_ H2 _/R_ (A2)


where _κ_ _ν_ = 1 _._ 0( _ν/_ 230 GHz) _[β]_ cm [2] g _[−]_ [1] is the dust opacity (Ossenkopf & Henning 1994), _µ_ = 2 _._ 8 is the mean
molecular weight, _m_ H is the mass of a hydrogen atom,
and _N_ H2 is the molecular hydrogen column density. We
adopt a dust emissivity index of _β_ = 1.8 and a gas-todust mass ratio ( _R_ ) of 100. The effect of scattering opacity (cf. Liu 2019) can be safely ignored in our case, given
that we focus on structures on the scale _>_ 10 [3] au scale,
where the averaged maximum grain size is expected to
be well below 100 _µ_ m (Wong et al. 2016).
During the least-square fitting procedure, the five data
points are fitted with a preset weight, which is determined by the measured noise level throughout the image
data. The pixelwise SED fitting results are column density (i.e. _N_ H2 ) maps for the nearby and distant clouds.
Figure 1, Figure 6, Figure 7, and Figure 8 show the
threshold column density (lime contours) and the area
associated with _M_ [bound] for each cloud.
gas


B. CORE EXTRACTION


In this section, we introduce the core extraction algorithm `SExtractor` [8] (Bertin & Arnouts 1996), as well as
the input arguments in the procedure for core extraction
in Section 3.1.
For each image, we first generate the background image as well as the root mean square (rms) noise, by iteratively clipping the local background histogram until
convergence at _±_ 3 _σ_ around its median (see more details in Bertin & Arnouts 1996). The box is 256-pixel
size which corresponds to 12’8, which means background
emission is subtracted with more extended than 12’8.
The background-subtracted images and noise rms maps
serve as the input for extraction algorithm.
When running the algorithm, `nthresh` = 3 is set to
cut out the locally low SNR ( `nthresh` _×_ rms) pixels. The
deblending parameters (number of thresholds for deblending `deblend` ~~`n`~~ `thresh` = 512, deblending contrast
`deblend` ~~`c`~~ `ont` = 10 _[−]_ [5] ), and the parameter to control
the minimum pixels in a core ( `min` ~~`n`~~ `pix`, that is, the
number of pixels in a _Herschel_ or ALMA beam) are set
for the source extraction procedure.


8 [https://sextractor.readthedocs.io/](https://sextractor.readthedocs.io)



As an example shown in Figure 1, the orange ellipses
indicate the extracted dense cores. The basic parameters include core location, angular size, and pixelwise
integration. In the case of nearby clouds, since the column density ( _N_ H2 ) map is given, the integration within
the core mask is equivalent to the core mass as indicated
by Equation 2. In the case of the ALMA-IMF intensity
map, the integration gives the flux density emitted by
the dust, which serves as the input in Equation 3.
To obtain the physical size (deconvolved from the
beam), we follow the method in Rosolowsky et al.
(2010); Contreras et al. (2013), the deconvolved angular
radius is written as,


1 _/_ 4
_θ_ deconv = _η_ �� _σ_ maj [2] _[−]_ _[σ]_ bm [2] �� _σ_ min [2] _[−]_ _[σ]_ bm [2] �� _,_ (B3)


where _σ_ maj and _σ_ min are the dispersion of major and
minor axes. The _σ_ bm is the averaged dispersion size of
the beam (i.e., _θ_ bmaj _/√_ 8 ln 2, where _θ_ bmaj is the FWHM

beam size). _η_ is a factor that relates the dispersion size
of the emission distribution to the determined angular
radius of the object. We have elected to use a value of
_η_ = 2 _._ 4, which is the median value derived for a range of
models consisting of a spherical, emissivity distribution
(Rosolowsky et al. 2010). Therefore, the physical size
of the core is derived from _R_ deconv = _θ_ core _× d_ ( _d_ is the
distance), which is listed in Table 1.
Orion A is located at a distance of 414 pc (Menten
et al. 2007), which is 2–3 times farther than other nearby
clouds. To identify cores with a consistent spatial resolution of _∼_ 0.03 pc, we utilized the 10 _[′′]_ dust column
density map of Orion A from Jiao et al. (2022a) to perform the core extraction.
The final core catalog of nearby clouds is listed in
Table 2.
We remark that the term, ‘core’, has ambiguous meanings. It, to some extent, depends on the behavior of
the core-identification algorithm(s) given specific image
qualities. In the literature, the definition of ‘core’ has
systematically evolved with the angular resolutions of
the major observing facilities. Prior to the ALMA era,
it was common to regard _∼_ 0.1 pc scale gas over-densities
as ‘core’ (e.g., Motte et al. 1998; Williams et al. 2000;
Bergin & Tafalla 2007; Andr´e et al. 2010). The core
sizes we measured are consistent with those earlier studies. In the more recent studies that were based on highresolution ALMA data (e.g., with ≲0.01 pc resolution;
Cheng et al. 2024; Louvet et al. 2024; Molinari et al.
2025; Coletta et al. 2025), ‘core’ referred to gas overdensities with smaller spatial scales. Nevertheless, these
observations, with different resolutions (and the resulting core sizes), mostly report the CMF shapes which
resembled the shape of the IMF. In addition, they also
reported comparable power-law indices at the high-mass
ends of their derived CMFs.
In our present work, based on the images with a
0.03 pc spatial resolution and using a specific core

Decoding SFR versus _M_ dense relation 13


-33°00'

















30'


-34°00'


30'


-70°30'


-71°00'


30'


-72°00'


30'


-27°00'


15'


30'


45'



















16 [h] 13 [m] 12 [m] 11 [m] 10 [m] 09 [m] 08 [m]



16 [h] 04 [m] 02 [m] 00 [m] 15 [h] 58 [m]



RA (J2000)



















17 [h] 13 [m] 12 [m] 11 [m] 10 [m]


RA (J2000)





**Figure** **6.** The threshold column density (lime contours) and the area associated with _M_ gas [bound] for each cloud.



identification algorithm, we found practical relations between _M_ core [max] [,] _[M]_ [ bound] gas, and SFR. Our results have no
dependence on the core-identification in other studies.
Since the sizes of the compact structures we identified
are systematically larger than the sizes of the ‘cores’
report in the recent ALMA studies (e.g., Cheng et al.
2024; Louvet et al. 2024; Molinari et al. 2025; Coletta
et al. 2025), one may wonder whether or not it is appropriate to refer to the compact structures we identified as
‘cores’. We regard this as a terminology issue. For instance, we could have rename the compact structures we
identified as ‘gas halos’ just to distinguish them from the



‘cores’ reported in the previous papers, and refer to the
relation we identified as the _M_ halo [max] [-] _[M]_ [ bound] gas relation. We
do not find it helpful to create a new terminology when
the definition of core remains ambiguous. As shown in
Figure 4, the mass function of the structures we identified in nearby clouds closely resembles the canonical
IMF/CMF. Therefore, we consider it appropriate to discuss these structures within the same conceptual framework as the ’cores’ in previous studies.

14


-54°34'


36'


38'


40'



RA (J2000)









4 [h] 24 [m] 20 [m] 16 [m] 12 [m]


RA (J2000)



18 [h] 06 [m] 48 [s] 36 [s] 24 [s] 12 [s]


RA (J2000)



18 [h] 10 [m] 40 [s] 30 [s] 20 [s] 10 [s]


RA (J2000)





-21°30'


33'


36'


39'


-53°50'


55'


-54°00'


-45°39'


40'


41'


42'


43'


44'







15 [h] 53 [m] 36 [s] 24 [s] 12 [s] 00 [s] 52 [m] 48 [s]


RA (J2000)



15 [h] 58 [m] 40 [s] 20 [s] 00 [s] 57 [m] 40 [s] 20 [s]


RA (J2000)



-19°52'


54'


56'


58'


-20°00'


-50°04'


05'


06'


07'


08'


09'


-36°03'


06'


09'


12'



16 [h] 22 [m] 20 [s] 10 [s] 00 [s] 21 [m] 50 [s]



-47°06'


08'


10'


12'









16 [h] 41 [m] 36 [s] 24 [s] 12 [s] 00 [s] 40 [m] 48 [s]


RA (J2000)



16 [h] 40 [m] 50 [s] 40 [s] 30 [s] 20 [s]


RA (J2000)


**Figure** **7.** (Continued.)



C. TEMPERATURE ESTIMATION OF CORES

WITHIN MASSIVE CLOUDS


We tried three methods of temperature estimation for
these massive dense cores, which are listed below.

_•_ Method One. We cross-match the sources with the
highest flux density (potentially the most massive one)
with the _Herschel_ PACS 70 _µ_ m source catalog (Molinari
et al. 2016). Considering the effects of optical depth, the
internal bolometric luminosity can be obtained from the
70 _µ_ m flux density (Elia et al. 2017),



where _S_ 70 _µ_ m is the integrated 70 _µ_ m flux density of the
source, _d_ is the distance to the clump, and _τ_ is the dust
opacity at 70 _µ_ m. _τ_ dust = _κ_ Σ dust where _κ ≃_ 100 cm [2] /g
at 70 _µ_ m (Ossenkopf & Henning 1994) and Σ dust is typically order of 0.01 g cm _[−]_ [2] for massive cores at the scale
of 2000-6000 AU (Motte et al. 2018b; Xu et al. 2024b).
Now we calculate the mean mass-weighted temperature _T_ dust [mean] within core radius _r_ (Terebey et al. 1993),



_−_ 1 _/_ 3
(C5)
�



_L_ _⊙_ (C4)
�



_L_ int = 25 _._ 6 _S_ 70 _µ_ m
� 10 Jy



_d_
�� 1 kpc



2
_τ_ _ν_
� � 1 _−_ _e_ _[−][τ]_ _[ν]_



1 _/_ 6
_r_
� � _r_ 0



_T_ dust [mean] = 2 [3] _[T]_ [0]



_L_ int
� _L_ 0

-34°35'


40'


45'


50'


17 [h] 30 [m] 40 [s] 20 [s] 00 [s] 29 [m] 40 [s]


RA (J2000)



Decoding SFR versus _M_ dense relation 15


14°34'


-1°58'


59'


32'


-2°00'


30'


01'


02'


28'



18 [h] 47 [m] 42 [s] 36 [s] 30 [s] 24 [s]


RA (J2000)





03'







19 [h] 23 [m] 54 [s] 48 [s] 42 [s] 36 [s] 30 [s]


RA (J2000)



**Figure** **8.** (Continued.)


**Table** **2.** Core catalog of nearby clouds


Cloud ID R.A. Dec. _θ_ maj _θ_ min PA FWHM _M_ core _N_ [peak] (H 2 ) SNR


Aquila 1 18:31:48.70 -04:56:49.86 70.5 48.4 -29.0 0.061 0.432 2.13e+21 6.7


Aquila 2 18:31:27.51 -04:56:03.94 98.2 40.8 -13.7 0.069 0.287 1.58e+21 4.6


Aquila 3 18:31:20.77 -04:55:16.29 129.5 44.4 -75.9 0.089 0.238 1.22e+21 4.0


Aquila 4 18:31:51.47 -04:54:10.59 102.9 71.5 -23.3 0.104 1.661 6.08e+21 20.6


Aquila 5 18:31:41.07 -04:52:39.43 91.9 40.8 76.0 0.066 0.620 3.65e+21 10.4


Aquila 6 18:31:39.63 -04:49:39.78 76.6 29.5 82.0 0.040 0.302 2.14e+21 6.5


Aquila 7 18:30:22.16 -04:48:49.92 65.8 34.2 -88.8 0.040 0.165 1.06e+21 4.2


Aquila 8 18:30:29.77 -04:44:04.07 34.1 29.0 -60.6 _· · ·_ 0.075 9.14e+20 2.9


Aquila 9 18:32:01.66 -04:43:19.26 76.6 37.3 2.1 0.052 0.340 1.87e+21 6.4


Aquila 10 18:32:23.12 -04:42:15.14 37.9 35.9 43.6 _· · ·_ 0.273 3.22e+21 12.5


Note—The properties of cores identified in nearby clouds are listed. Here, only the top ten rows of Aquila are shown. The
complete table will be available online.



where _L_ int is the internal luminosity and _r_ is the core’s
radius which can be obtained from the core extraction algorithm (see Equation B3 in Appendix B). The
reference values are _T_ 0 = 25 K, _L_ 0 = 520 _L_ _⊙_, and
_r_ 0 = 0 _._ 032 pc. The scaling relation above assumes
dust opacity index _β_ = 2 and density profile follows
_ρ_ ( _r_ ) _∝_ _r_ _[−]_ [2] .

_•_ Method Two. All of these massive dense cores are
showing hot molecular species CH 3 OCHO line emission
(Bonfand et al. 2024), which means there should be internal heating sources like OB stars. So in the method
two, we simply assume CH 3 OCHO-bearing cores have a
uniform temperature of 100 K. Bonfand et al. (2024, see
their Section 5.2) also argue that some sources like W51E, W51-IRS2, and G327.29 should contain temperature
as high as 300 K. For example, Ginsburg et al. (2017)
report a peak excitation temperature _>_ 350 K based on
the analysis of CH 3 OH emission lines at 1800-au reso


lution in W51-E. So we use the same convention of 300
K for the case of W51-E, W51-IRS2, and G327.29, as
what Bonfand et al. (2024) did.

_•_ Method Three. Based on the reason discussed in

Method Two, we also test the case where the temperature is also set to 100 K without any exception.
In Figure 9, we present the data points and fitting
results between the most massive core mass _M_ core [max] [ver-]
sus its parental gravitational bound gas _M_ gas [bound] for the
methods one and three. Method two is adopted in Figure 2 for its least data scatter. So it is not shown here
to avoid duplication. Generally speaking, the slope is
around 0.5–0.6 with a systematic uncertainty of 0.07
from method choice. We also list the Spearman correlation coefficient and its corresponding p-value in each
panel. In all of the three cases, the correlation is significant.

16











10 [3]


10 [2]


10 [1]







10 [3]


10 [2]


10 [1]

































































10 [0]



10 [0]


|Power-law<br>Spearman<br>95% Confi|slope: 0 .5<br>cc. 0 .83;<br>dence Inte|75; =0 .334<br>p=1 .3e-06<br>rval|MethodOne<br>W51|
|---|---|---|---|
|~~(Outliers e~~<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|~~ xcluded):~~<br> cc. 0.96;<br> uds<br> uds<br> uds affect|~~  0.612; =0.262~~<br>   p=9.3e-11<br>  ed by missing flux<br>G3<br><br>G3|~~O~~rion<br>G008.67<br>G010.62<br>~~27.29~~<br>G3~~3~~7.92<br>G33893<br>51.~~77~~<br>W43<br>|
||LupII~~I ~~<br>P~~i~~pe|~~A~~quil~~a~~<br>ChamI<br><br> ~~L~~upIV<br>Ophiuch~~u~~s<br>Persus<br>Ta~~u~~rus<br>G~~0~~|12.80<br>G328.25<br>~~G~~33~~3~~.60<br>.<br>~~G3~~53.41|
||L<br>~~M~~u<br>|~~p~~I<br>sca||
|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|


|Power-law<br>Spearman<br>95% Confi|slope: 0 .5<br>cc. 0 .81;<br>dence Inte|54; =0 .361<br>p=2 .6e-06<br>rval|MethodThree<br>W51|
|---|---|---|---|
|~~(Outliers e~~<br>Spearman<br>Nearby clo<br>Distant clo<br>Distant clo|~~ xcluded):~~<br> cc. 0.96;<br> uds<br> uds<br> uds affect|~~  0.592; =0.285~~<br>   p=1.9e-10<br>  ed by missing flux<br><br>G35|Orion<br><br>G010.62<br>~~G~~3~~2~~7.~~29~~<br><br>~~G~~337.92<br>1.~~77~~<br>W43|
||~~LupIII~~<br>~~Pi~~pe|A~~q~~uila<br>ChamI<br><br>~~L~~upIV<br>Ophiuch~~u~~s<br>Persus<br>Ta~~u~~rus<br>G<br>G<br>|~~G~~008.67<br>012.8~~0~~<br>~~G~~328.25<br>333~~.60~~<br>G338.93<br>G353.41|
||Lu<br>~~M~~u<br>|pI<br>sca||
|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|102<br>103<br>104<br>105<br>1<br>Mbound<br>gas<br> [M ]|



**Figure** **9.** The most massive core mass _M_ core [max] [versus] [its] [parental] [gravitational] [bound] [gas] _[M]_ gas [ bound], using the methods one and
three. The method two is adopted for Figure 2, so it is not shown in this figure. The blue stars indicate the nearby clouds and
the orange hexagons indicate the distant massive clouds. Using the other two different temperature estimation methods, _M_ core [max]
have two versions for the power-law fitting. The power-law index is listed with a 1 _σ_ to indicate how the data scatters. The
Spearman correlation coefficient (cc.) and its p-value are to show the significance of the fitting. The 1 _σ_ data scatter and the
gray-shaded region correspond to the regimes with 95% confidence interval.


**Table** **3.** Parameters the most massive cores from three methods


ALMA-IMF Field Method One Method Two Method Three


T dust (K) Mass ( _M_ _⊙_ ) T dust (K) Mass ( _M_ _⊙_ ) T dust (K) Mass ( _M_ _⊙_ )


G008.67 69.7+/- 2.1 101.8+/- 30.7 100.0+/- 16.0 70.1+/- 23.2 100.0+/- 16.0 69.9+/- 23.2


G010.62 91.4+/- 3.1 177.3+/- 56.4 100.0+/- 16.0 163.8+/- 55.9 100.0+/- 16.0 163.4+/- 55.8


G012.80 80.0+/- 2.4 39.9+/- 11.9 100.0+/- 16.0 32.1+/- 10.6 100.0+/- 16.0 32.0+/- 10.5


G327.29 86.9+/- 5.9 264.9+/- 111.7 300.0+/- 32.0 67.1+/- 28.5 100.0+/- 16.0 226.2+/- 98.1


G328.25 86.0+/- 5.8 28.5+/- 12.0 100.0+/- 16.0 24.6+/- 10.7 100.0+/- 16.0 24.5+/- 10.7


G333.60 111.2+/- 6.3 53.0+/- 20.3 100.0+/- 16.0 60.2+/- 24.0 100.0+/- 16.0 60.2+/- 23.9


G337.92 84.8+/- 5.3 136.0+/- 54.9 100.0+/- 16.0 115.1+/- 48.4 100.0+/- 16.0 115.3+/- 48.4


G338.93 75.4+/- 6.5 68.1+/- 33.1 100.0+/- 16.0 50.6+/- 25.1 100.0+/- 16.0 50.4+/- 25.1


G351.77 92.5+/- 6.2 151.5+/- 64.0 100.0+/- 16.0 140.4+/- 60.9 100.0+/- 16.0 141.1+/- 61.6


G353.41 76.6+/- 5.2 20.1+/- 8.5 100.0+/- 16.0 15.3+/- 6.6 100.0+/- 16.0 15.3+/- 6.7


W43-MM1 72.6+/- 1.9 394.7+/- 115.3 100.0+/- 16.0 275.0+/- 88.3 100.0+/- 16.0 274.0+/- 88.1


W43-MM2 60.4+/- 1.5 399.8+/- 116.1 100.0+/- 16.0 228.5+/- 72.9 100.0+/- 16.0 228.2+/- 73.3


W43-MM3 58.7+/- 1.5 235.6+/- 68.5 100.0+/- 16.0 134.5+/- 43.6 100.0+/- 16.0 134.3+/- 43.2


W51-E 98.9+/- 1.9 1222.7+/- 342.8 300.0+/- 32.0 323.8+/- 94.9 100.0+/- 16.0 1223.7+/- 381.5


W51-IRS2 97.0+/- 2.0 1344.5+/- 376.1 300.0+/- 32.0 321.8+/- 94.0 100.0+/- 16.0 1308.8+/- 408.1


Note—The dust temperature estimation and the most massive core mass in three methods. 1 _σ_ uncertainty is listed for uncertainty

calculation.

Decoding SFR versus _M_ dense relation 17



10 −1


10 −2


10 −3


10 −4


10 −5





10 −6 10 −6 10 −5 10 −4 10 −3 10 −2



tion. This section extends the comparison to include the
observationally constrained SFR [observation] .
For nearby clouds, the SFR [observation] is constrained by
counting young stellar objects (YSOs; Evans et al. 2009;
Heiderman et al. 2010). For distant clouds, the SFR is
constrained by the total infrared luminosities. The total
infrared luminosity is calculated according to the prescription in Sanders & Mirabel (1996) based on the four
_IRAS_ flux bands observations. SFR [observation] of distant
clouds are calculated by the relation, SFR _≈_ 2 _×_ 10 _[−]_ [10]

( _L_ IR / _L_ _⊙_ ) _M_ _⊙_ yr _[−]_ [1], following Kennicutt (1998); Gao
& Solomon (2004); Lada et al. (2012). However, as
pointed out by Chomiuk & Povich (2011) and Lada
et al. (2012), the SFRs from far-infrared observations require upward adjustments to match those from the YSO
counting method. We tried adjusting the SFR [observation]

upward by a factor of 2.7 as suggested by Lada et al.
(2012), and a factor of 7.8 based on the measurements
towards Orion A and B clouds (Lada et al. 2012, and
Jiao et al. submitted). Figure 10 shows the comparison between SFR [theory] and SFR [observation] . We found
that, while there is broad agreement between SFR [theory]

and SFR [observation], nearby clouds closely follow the line
of equality, whereas distant clouds deviate significantly.
Since the SFR [observation] of the distant clouds sample
have large intrinsic scattering, the upward adjustments
with the two different factors did not change this conclusion.



SFR [observation] [ M ⊙ yr [−1] ]


**Figure** **10.** Comparison between SFR [observation]

and SFR [theory] . The black dashed line indicates
SFR [observation] =SFR [theory] .


D. COMPARISON BETWEEN SFR [THEORY] AND
SFR [OBSERVATION]


In Section 4.1, we derived the SFRs [theory] for the target
clouds and compared them with the Gao-Solomon rela


REFERENCES



Alves, J., Lombardi, M., & Lada, C. J. 2007, A&A, [462,](http://dx.doi.org/10.1051/0004-6361:20066389) L17


Alves, J., Lombardi, M., & Lada, C. J. 2017, A&A, [606,](http://dx.doi.org/10.1051/0004-6361/201731436) L2


Andr´e, P., Men’shchikov, A., Bontemps, S., et al. 2010,


A&A, [518,](http://dx.doi.org/10.1051/0004-6361/201014666) L102


Bergin, E. A. & Tafalla, M. 2007, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.45.071206.100404) 45, 339


Bertin, E. & Arnouts, S. 1996, A&AS, [117,](http://dx.doi.org/10.1051/aas:1996164) 393


Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202347856)

687, [A163](http://dx.doi.org/10.1051/0004-6361/202347856)


Bonnell, I. A., Bate, M. R., & Vine, S. G. 2003, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2003.06687.x)

343, 413


Chen, H. H.-H., Burkhart, B., Goodman, A., & Collins,

D. C. 2018, ApJ, [859,](http://dx.doi.org/10.3847/1538-4357/aabaf6) 162


Cheng, Y., Lu, X., Sanhueza, P., et al. 2024, arXiv [e-prints,](http://dx.doi.org/10.48550/arXiv.2404.03858)

[arXiv:2404.03858](http://dx.doi.org/10.48550/arXiv.2404.03858)


Chomiuk, L. & Povich, M. S. 2011, AJ, [142,](http://dx.doi.org/10.1088/0004-6256/142/6/197) 197


Clauset, A., Shalizi, C. R., & Newman, M. E. J. 2009,


SIAM [Review,](http://dx.doi.org/10.1137/070710111) 51, 661


Coletta, A., Molinari, S., Schisano, E., et al. 2025, arXiv

e-prints, arXiv:2503.05663


Contreras, Y., Schuller, F., Urquhart, J. S., et al. 2013,


A&A, [549,](http://dx.doi.org/10.1051/0004-6361/201220155) A45


Dame, T. M. & Lada, C. J. 2023, ApJ, [944,](http://dx.doi.org/10.3847/1538-4357/acb438) 197



Elia, D., Molinari, S., Schisano, E., et al. 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx1357)

471, 100


Evans, Neal J., I., Kim, K.-T., Wu, J., et al. 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab8938)

894, 103


Evans, Neal J., I., Dunham, M. M., Jørgensen, J. K., et al.

2009, ApJS, [181,](http://dx.doi.org/10.1088/0067-0049/181/2/321) 321


Evans, II, N. J. 1999, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.37.1.311) 37, 311


Evans, II, N. J., Heiderman, A., & Vutisalchavakul, N.

2014, ApJ, [782,](http://dx.doi.org/10.1088/0004-637X/782/2/114) 114


Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman,

J. 2013, PASP, [125,](http://dx.doi.org/10.1086/670067) 306


Galv´an-Madrid, R., D´ıaz-Gonz´alez, D. J., Motte, F., et al.

2024, arXiv e-prints, [arXiv:2407.07359](http://dx.doi.org/10.48550/arXiv.2407.07359)


Gao, Y. & Solomon, P. M. 2004, ApJ, [606,](http://dx.doi.org/10.1086/382999) 271


Ginsburg, A., Goddi, C., Kruijssen, J. M. D., et al. 2017,


ApJ, [842,](http://dx.doi.org/10.3847/1538-4357/aa6bfa) 92


Ginsburg, A., Csengeri, T., Galv´an-Madrid, R., et al. 2022,


A&A, [662,](http://dx.doi.org/10.1051/0004-6361/202141681) A9


Goicoechea, J. R., Lique, F., & Santa-Maria, M. G. 2022,


A&A, [658,](http://dx.doi.org/10.1051/0004-6361/202142210) A28


Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008,


ApJ, [680,](http://dx.doi.org/10.1086/587166) 428

18


Goldsmith, P. F. & Kauffmann, J. 2017, ApJ, [841,](http://dx.doi.org/10.3847/1538-4357/aa6f12) 25

Griffin, M. J. 2010, in Astronomy and Astrophysics, Vol.

518

Heiderman, A., Evans, Neal J., I., Allen, L. E., Huard, T.,

& Heyer, M. 2010, ApJ, [723,](http://dx.doi.org/10.1088/0004-637X/723/2/1019) 1019

Jiao, S., Lin, Y., Shui, X., et al. 2022a, Science [China](http://dx.doi.org/10.1007/s11433-021-1902-3)

Physics, Mechanics, [and](http://dx.doi.org/10.1007/s11433-021-1902-3) Astronomy, 65, 299511

Jiao, S., Wu, J., Ruan, H., et al. 2022b, Research [in](http://dx.doi.org/10.1088/1674-4527/ac6850)

Astronomy and [Astrophysics,](http://dx.doi.org/10.1088/1674-4527/ac6850) 22, 075016

Jim´enez-Serra, I., B´aez-Rubio, A., Rivilla, V. M., et al.

2013, ApJL, [764,](http://dx.doi.org/10.1088/2041-8205/764/1/L4) L4

Jones, G. H., Clark, P. C., Glover, S. C. O., & Hacar, A.

2023, MNRAS, 520, 1005

Kainulainen, J. & Tan, J. C. 2013, A&A, [549,](http://dx.doi.org/10.1051/0004-6361/201219526) A53

Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I.,

& Lee, C. W. 2008, A&A, [487,](http://dx.doi.org/10.1051/0004-6361:200809481) 993

Kauffmann, J., Pillai, T., Zhang, Q., et al. 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201628088) 603,

[A89](http://dx.doi.org/10.1051/0004-6361/201628088)

Kennicutt, Robert C., J. 1998, ApJ, [498,](http://dx.doi.org/10.1086/305588) 541

Koen, C. 2006, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2005.09739.x) 365, 590

Kong, S. 2019, ApJ, [873,](http://dx.doi.org/10.3847/1538-4357/aaffd5) 31

K¨onyves, V., Andr´e, P., Men’shchikov, A., et al. 2015,


A&A, [584,](http://dx.doi.org/10.1051/0004-6361/201525861) A91

Kroupa, P. 2001, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2001.04022.x) 322, 231

Kroupa, P. & Weidner, C. 2003, ApJ, [598,](http://dx.doi.org/10.1086/379105) 1076

Kroupa, P., Weidner, C., Pflamm-Altenburg, J., et al. 2013,


in Planets, Stars and Stellar Systems. Volume 5: Galactic

Structure and Stellar [Populations,](http://dx.doi.org/10.1007/978-94-007-5612-0_4) ed. T. D. Oswalt &

G. [Gilmore,](http://dx.doi.org/10.1007/978-94-007-5612-0_4) Vol. 5, 115

Lada, C. J., Forbrich, J., Lombardi, M., & Alves, J. F.

2012, ApJ, [745,](http://dx.doi.org/10.1088/0004-637X/745/2/190) 190

Lin, Y., Csengeri, T., Wyrowski, F., et al. 2019, [A&A,](http://dx.doi.org/10.1051/0004-6361/201935410) 631,

[A72](http://dx.doi.org/10.1051/0004-6361/201935410)

Lin, Y., Liu, H. B., Li, D., et al. 2016, ApJ, [828,](http://dx.doi.org/10.3847/0004-637X/828/1/32) 32

Liu, H. B. 2019, ApJL, [877,](http://dx.doi.org/10.3847/2041-8213/ab1f8e) L22

Liu, M., Tan, J. C., Cheng, Y., & Kong, S. 2018, ApJ, 862,

[105](http://dx.doi.org/10.3847/1538-4357/aacb7c)

Lombardi, M., Alves, J., & Lada, C. J. 2015, A&A, [576,](http://dx.doi.org/10.1051/0004-6361/201525650) L1

Louvet, F., Sanhueza, P., Stutz, A., et al. 2024, [A&A,](http://dx.doi.org/10.1051/0004-6361/202345986) 690,

[A33](http://dx.doi.org/10.1051/0004-6361/202345986)

Martin-Pintado, J., Bachiller, R., Thum, C., & Walmsley,

M. 1989, A&A, 215, L13

Menten, K. M., Reid, M. J., Forbrich, J., & Brunthaler, A.

2007, A&A, [474,](http://dx.doi.org/10.1051/0004-6361:20078247) 515

Molinari, S., Swinyard, B., Bally, J., et al. 2010, [PASP,](http://dx.doi.org/10.1086/651314)

122, 314

Molinari, S., Schisano, E., Elia, D., et al. 2016, A&A, 591,

[A149](http://dx.doi.org/10.1051/0004-6361/201526380)

Molinari, S., Schilke, P., Battersby, C., et al. 2025, arXiv

e-prints, arXiv:2503.05555



Motte, F., Andre, P., & Neri, R. 1998, A&A, 336, 150


Motte, F., Bontemps, S., & Louvet, F. 2018a, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-091916-055235) 56,

[41](http://dx.doi.org/10.1146/annurev-astro-091916-055235)


Motte, F., Nony, T., Louvet, F., et al. 2018b, [Nature](http://dx.doi.org/10.1038/s41550-018-0452-x)

[Astronomy,](http://dx.doi.org/10.1038/s41550-018-0452-x) 2, 478


Motte, F., Bontemps, S., Csengeri, T., et al. 2022, [A&A,](http://dx.doi.org/10.1051/0004-6361/202141677)

[662,](http://dx.doi.org/10.1051/0004-6361/202141677) A8


Offner, S. S. R., Clark, P. C., Hennebelle, P., et al. 2014, [in](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch003)

Protostars and Planets VI, [ed.](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch003) H. Beuther, R. S. Klessen,

C. P. [Dullemond,](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch003) & T. Henning, 53


Ossenkopf, V. & Henning, T. 1994, in Astronomy and

Astrophysics, Vol. 291, 943, 959


Pety, J., Guzm´an, V. V., Orkisz, J. H., et al. 2017, [A&A,](http://dx.doi.org/10.1051/0004-6361/201629862)

599, A98


Poglitsch, A. 2010, in Astronomy and Astrophysics, Vol.

518, 2


Rosolowsky, E., Dunham, M. K., Ginsburg, A., et al. 2010,


ApJS, [188,](http://dx.doi.org/10.1088/0067-0049/188/1/123) 123


Sanders, D. B. & Mirabel, I. F. 1996, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.34.1.749) 34, 749


Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa6ff8)

[841,](http://dx.doi.org/10.3847/1538-4357/aa6ff8) 97


Santa-Maria, M. G., Goicoechea, J. R., Pety, J., et al. 2023,


A&A, [679,](http://dx.doi.org/10.1051/0004-6361/202346598) A4


Schinnerer, E. & Leroy, A. K. 2024, arXiv [e-prints,](http://dx.doi.org/10.48550/arXiv.2403.19843)

[arXiv:2403.19843](http://dx.doi.org/10.48550/arXiv.2403.19843)


Schneider, N., Bontemps, S., Girichidis, P., et al. 2015,


MNRAS, 453, L41


Schulz, C., Pflamm-Altenburg, J., & Kroupa, P. 2015,


A&A, [582,](http://dx.doi.org/10.1051/0004-6361/201425296) A93


Su´arez, G., Galv´an-Madrid, R., Aguilar, L., et al. 2021,


ApJ, [921,](http://dx.doi.org/10.3847/1538-4357/ac1bb9) 48


Terebey, S., Chandler, C. J., & Andre, P. 1993, ApJ, [414,](http://dx.doi.org/10.1086/173121)

[759](http://dx.doi.org/10.1086/173121)


V´azquez-Semadeni, E., Gonz´alez-Samaniego, A., & Col´ın,

P. 2017, MNRAS, 467, 1313


Virkar, Y. & Clauset, A. 2012, arXiv [e-prints,](http://dx.doi.org/10.48550/arXiv.1208.3524)

[arXiv:1208.3524](http://dx.doi.org/10.48550/arXiv.1208.3524)


Weidner, C. & Kroupa, P. 2004, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2004.07340.x) 348, 187


Weidner, C., Kroupa, P., & Pflamm-Altenburg, J. 2013,


[MNRAS,](http://dx.doi.org/10.1093/mnras/stt1002) 434, 84


Williams, J. P., Blitz, L., & McKee, C. F. 2000, in

Protostars and Planets IV, [ed.](http://dx.doi.org/10.48550/arXiv.astro-ph/9902246) V. Mannings, A. P. Boss,

& S. S. Russell, 97


Wong, Y. H. V., Hirashita, H., & Li, Z.-Y. 2016, [PASJ,](http://dx.doi.org/10.1093/pasj/psw066) 68,

[67](http://dx.doi.org/10.1093/pasj/psw066)


Wu, J., Evans, Neal J., I., Gao, Y., et al. 2005, [ApJL,](http://dx.doi.org/10.1086/499623) 635,

[L173](http://dx.doi.org/10.1086/499623)


Wu, J., Evans, Neal J., I., Shirley, Y. L., & Knez, C. 2010,


ApJS, [188,](http://dx.doi.org/10.1088/0067-0049/188/2/313) 313

Decoding SFR versus _M_ dense relation 19



Xu, F., Wang, K., Liu, T., et al. 2024a, Research [in](http://dx.doi.org/10.1088/1674-4527/ad3dc3)


Astronomy and [Astrophysics,](http://dx.doi.org/10.1088/1674-4527/ad3dc3) 24, 065011


Xu, F., Wang, K., Liu, T., et al. 2024b, ApJS, 270, 9



Xu, F.-W., Wang, K., Liu, T., et al. 2023, [MNRAS,](http://dx.doi.org/10.1093/mnras/stad012) 520,

[3259](http://dx.doi.org/10.1093/mnras/stad012)

Yan, Z., Jerabkova, T., & Kroupa, P. 2017, A&A, [607,](http://dx.doi.org/10.1051/0004-6361/201730987) A126

Yan, Z., Jerabkova, T., & Kroupa, P. 2023, A&A, [670,](http://dx.doi.org/10.1051/0004-6361/202244919) A151

Zhu, F. Y., Wang, J. Z., Zhu, Q. F., & Zhang, J. S. 2022,


A&A, [665,](http://dx.doi.org/10.1051/0004-6361/202142305) A94


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: archival_reuse",
  "failed_quote": "To resolve the massive dense cores in distant clouds, we retrieved the ALMA large project ALMA-IMF 1.3 mm continuum data (Motte et al. 2022; Ginsburg et al. 2022)."
 },
 {
  "path": "paper_type_evidence[2]",
  "value": "paper type: archival_reuse",
  "failed_quote": "We used free-free subtracted images released by ALMA-IMF team."
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "1.3 mm continuum",
  "failed_quote": "To resolve the massive dense cores in distant clouds, we retrieved the ALMA large project ALMA-IMF 1.3 mm continuum data (Motte et al. 2022; Ginsburg et al. 2022)."
 },
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "0.3'' to 1.5'' (2000 AU / ~0.01 pc native; smoothed to 0.03 pc or ~1.1'' to ~3.1'')",
  "failed_quote": "For distant clouds, we also smoothed the 1.3 mm free-free emission subtracted continuum images to a consistent spatial resolution of 0.03 pc, i.e., an angular resolution of ~1''.1 to ~3''.1, depending on the distance."
 },
 {
  "path": "data.pi_or_archival_as_stated.evidence[1]",
  "value": "archival (ALMA-IMF large project)",
  "failed_quote": "To resolve the massive dense cores in distant clouds, we retrieved the ALMA large project ALMA-IMF 1.3 mm continuum data (Motte et al. 2022; Ginsburg et al. 2022)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "1.3 mm free-free subtracted continuum images from ALMA-IMF",
  "failed_quote": "The ALMA-IMF consortium produces the 1.3 mm dust continuum images where the free-free contribution was subtracted based on the H41α emission (Galván-Madrid et al. 2024)."
 },
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "Theoretical galactic-scale SFR-m_star^max model",
  "failed_quote": "For stars with masses less than 100 M_⊙, we extracted the theoretical, galactic-scale SFR-m_star^max relation derived in Yan et al. (2017) by performing linear regression to the model presented in their Figure 7."
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "Monte Carlo random sampling simulations of the Core Mass Function (CMF) to generate mock distributions of the most massive core mass (M_core^max)",
  "failed_quote": "Using the following five steps, we simulated the distribution of M_core^max assuming that the star-forming processes randomly sample the CMF"
 },
 {
  "path": "processing.calibration.archive_products_used_as_is.evidence[0]",
  "value": "Used free-free subtracted 1.3 mm continuum images released by the ALMA-IMF team",
  "failed_quote": "We used free-free subtracted images released by ALMA-IMF team."
 },
 {
  "path": "processing.imaging.smoothing.evidence[1]",
  "value": "Smoothed to a consistent spatial resolution of 0.03 pc (~1.1'' to ~3.1'' for distant clouds)",
  "failed_quote": "For distant clouds, we also smoothed the 1.3 mm free-free emission subtracted continuum images to a consistent spatial resolution of 0.03 pc, i.e., an angular resolution of ~1''.1 to ~3''.1, depending on the distance."
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "0.3'' to 1.5'' native (2000 AU / ~0.01 pc); ~1.1'' to ~3.1'' after smoothing to 0.03 pc; 36.9'' for Herschel N_H2 maps",
  "failed_quote": "For distant clouds, we also smoothed the 1.3 mm free-free emission subtracted continuum images to a consistent spatial resolution of 0.03 pc, i.e., an angular resolution of ~1''.1 to ~3''.1, depending on the distance."
 },
 {
  "path": "processing.imaging.final_beam.evidence[2]",
  "value": "0.3'' to 1.5'' native (2000 AU / ~0.01 pc); ~1.1'' to ~3.1'' after smoothing to 0.03 pc; 36.9'' for Herschel N_H2 maps",
  "failed_quote": "All the images were convolved to a common angular resolution of the largest telescope beam (36''.9) and then were regridded to have the same pixel size (4''.0)."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "1.3 mm free-free subtracted continuum images from ALMA-IMF",
  "failed_quote": "The ALMA-IMF consortium produces the 1.3 mm dust continuum images where the free-free contribution was subtracted based on the H41α emission (Galván-Madrid et al. 2024)."
 },
 {
  "path": "processing.inherited[0].what.evidence[1]",
  "value": "1.3 mm free-free subtracted continuum images from ALMA-IMF",
  "failed_quote": "We used free-free subtracted images released by ALMA-IMF team."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Convolve Herschel 5-band images (70, 160, 250, 350, 500 um) to a common 36.9'' resolution, regrid to 4.0'' pixel size, and perform pixelwise single-component modified black-body SED fitting.",
  "failed_quote": "All the images were convolved to a common angular resolution of the largest telescope beam (36''.9) and then were regridded to have the same pixel size (4''.0)."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "Common angular resolution = 36.9'', pixel size = 4.0''",
  "failed_quote": "All the images were convolved to a common angular resolution of the largest telescope beam (36''.9) and then were regridded to have the same pixel size (4''.0)."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[1]",
  "value": "Maximum Likelihood Estimation (MLE) on unbinned column density distributions combined with MCMC using EMCEE to identify N_threshold and uncertainties.",
  "failed_quote": "To identify the transitional column density (both the logarithmic normalized value, η_t, and the absolute value, N_threshold) and to estimate the uncertainties of the fitted parameters, we employed a Markov Chain Monte Carlo (MCMC) approach using the Python package EMCEE (Foreman-Mackey et al. 2013)."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Mean molecular weight mu = 2.8; for distant clouds: specific dust opacity at 1.3 mm kappa_1.3mm = 0.01 cm^2 g^-1 (beta = 1.8), uniform dust temperature T_dust = 100 K (or 300 K for W51-E, W51-IRS2, and G327.29 in fiducial Method Two).",
  "failed_quote": "Here, S_1.3mm^int is the integrated monochromatic flux of core at 1.3 mm, d is the distance to the cloud, κ_1.3mm = 0.01 cm^2 g^-1 is the specific dust opacity interpolated to 1.3 mm assuming β = 1.8 (Ossenkopf & Henning 1994), B_ν(T_dust) is the Planck function at a given dust temperature T_dust."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Perform linear regression in log-log space between M_core^max and M_gas^bound for the 23 clouds (and excluding 4 outliers with missing flux); combine with SFE = 30% and the theoretical SFR-m_star^max relation from Yan et al. (2017) to infer SFR^theory and compare with the Gao-Solomon relation and observational SFRs.",
  "failed_quote": "With a linear regression of all the cloud sample, one can obtain the correlation log(M_core^max/M_⊙) = 0.506 log(M_gas^bound/M_⊙) − 0.32"
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Perform linear regression in log-log space between M_core^max and M_gas^bound for the 23 clouds (and excluding 4 outliers with missing flux); combine with SFE = 30% and the theoretical SFR-m_star^max relation from Yan et al. (2017) to infer SFR^theory and compare with the Gao-Solomon relation and observational SFRs.",
  "failed_quote": "For a star-forming cloud, given the measurement of M_gas^bound, the recipe to theoretically infer the SFR^theory then follows: 1. Derive M_core^max based on the observed M_core^max-M_gas^bound relation (Equation 7). 2. Assume m_star^max ~ 0.3 × M_core^max 3. Apply the SFR-m_star^max relation (Equation 8) mentioned above."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Star-forming efficiency SFE = 30% (m_star^max ~ 0.3 * M_core^max); M_gas^bound approximates M_gas^dense; Gao-Solomon relation scaled upward by factor 2.7.",
  "failed_quote": "If we consider that M_gas^bound can approximate the M_gas^dense in the Gao-Solomon (i.e., SFR-M_gas^dense) relation (Gao & Solomon 2004), then a comparison of our observed M_core^max-M_gas^bound relation (Section 3.3) and the Gao-Solomon relation immediately imply that there is a link between M_core^max and SFR. Intriguingly, we found that if assuming a constant star-forming efficiency (SFE) of ~30%, then this link coincides with the theoretical SFR-m_star^max relation"
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Linear regression and Spearman rank correlation test",
  "failed_quote": "With a linear regression of all the cloud sample, one can obtain the correlation log(M_core^max/M_⊙) = 0.506 log(M_gas^bound/M_⊙) − 0.32, with a Spearman coefficient of 0.83 and a p-value of 7.8 × 10^-7 that is much lower than 0.001."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Fit the CMF of nearby clouds at the high-mass end; run Monte Carlo simulations drawing n(M > 3 M_sun) cores from a power-law CMF (pool of 10^6 cores) 5000 times per cloud (and 10^6 iterations for Taurus+Perseus combined), comparing simulated M_core^max distributions and scatter to observations.",
  "failed_quote": "Using the following five steps, we simulated the distribution of M_core^max assuming that the star-forming processes randomly sample the CMF"
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Source extraction of dense cores and background/rms noise estimation",
  "failed_quote": "We apply a commonly-used source extraction algorithm SExtractor (Bertin & Arnouts 1996)."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Markov Chain Monte Carlo (MCMC) fitting of column density probability distribution functions (N-PDFs) to find transitional column density and uncertainties",
  "failed_quote": "To identify the transitional column density (both the logarithmic normalized value, η_t, and the absolute value, N_threshold) and to estimate the uncertainties of the fitted parameters, we employed a Markov Chain Monte Carlo (MCMC) approach using the Python package EMCEE (Foreman-Mackey et al. 2013)."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Slope of log(M_core^max) vs log(M_gas^bound) relation (all clouds, Method Two) = 0.506 dimensionless",
  "failed_quote": "We discovered a significant correlation log(M_core^max/M_⊙) = 0.506 log(M_gas^bound/M_⊙) − 0.32."
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Intercept of log(M_core^max) vs log(M_gas^bound) relation (all clouds, Method Two) = -0.32 dimensionless",
  "failed_quote": "With a linear regression of all the cloud sample, one can obtain the correlation log(M_core^max/M_⊙) = 0.506 log(M_gas^bound/M_⊙) − 0.32"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Slope of SFR^theory vs M_gas^bound relation (outliers excluded) = 1.11 dimensionless",
  "failed_quote": "The results shows a slightly steeper slope of 1.11 +0.10 -0.10, and the correlation is 30% tighter."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "The linear Gao-Solomon relation between SFR and dense gas mass can be explained as the combination of three deterministic relations: SFR vs. m_star^max (slope 2.04), m_star^max vs. M_core^max (30% efficiency), and M_core^max vs. M_gas^bound (slope 0.506), yielding SFR proportional to (M_gas^bound)^1.03.",
  "failed_quote": "Based on this result, we hypothesize that the Gao-Solomon relation is a consequence of combining the following three non-trivial relations (i) SFR vs. m_star^max, (ii) m_star^max vs. M_core^max, and (iii) M_core^max vs. M_gas^bound."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "The linear Gao-Solomon relation between SFR and dense gas mass can be explained as the combination of three deterministic relations: SFR vs. m_star^max (slope 2.04), m_star^max vs. M_core^max (30% efficiency), and M_core^max vs. M_gas^bound (slope 0.506), yielding SFR proportional to (M_gas^bound)^1.03.",
  "failed_quote": "For more insight, the linear correlation (e.g., SFR ∝ M_gas^bound) can be obtained from the combination of M_core^max ∝ (M_gas^bound)^0.506 (Equation 7), M_core^max ∝ m_star^max, and SFR ∝ (m_star^max)^2.04 (Equation 8)"
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "Core formation in nearby molecular clouds is inconsistent with random (stochastic) sampling of a universal Core Mass Function (CMF), because random sampling produces both a much larger scatter and systematically higher M_core^max values than observed.",
  "failed_quote": "As a summary, observed M_core^max-M_gas^bound correlation is inconsistent with randomly sampling the CMF in two ways: (1) the observed M_core^max-M_gas^bound relation is too tight to be consistent with the simulation that randomly sampling the CMF, and (2) the observed M_core^max-M_gas^bound relation systematically falls below the simulated M_core^max values."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "There is a tight, significant power-law correlation between M_core^max and M_gas^bound across 10^2 to 10^5 M_sun.",
  "failed_quote": "With a linear regression of all the cloud sample, one can obtain the correlation log(M_core^max/M_⊙) = 0.506 log(M_gas^bound/M_⊙) − 0.32, with a Spearman coefficient of 0.83 and a p-value of 7.8 × 10^-7 that is much lower than 0.001."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The empirical M_core^max-M_gas^bound relation, when paired with a 30% star formation efficiency and optimal IMF sampling, reproduces the linear proportionality of the Gao-Solomon relation.",
  "failed_quote": "Our discovered M_core^max-M_gas^bound correlation can be approximately converted to the Gao-Solomon relation if there is (1) a constant 30% efficiency of converting M_core^max to the mass of the most massive star (m_star^max), and (2) if SFR and m_star^max are tightly related through log(SFR/(M_⊙ yr^-1)) = 2.04 log(m_star^max/M_⊙) − 5.80."
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "Observed M_core^max values are inconsistent with random sampling of the CMF, supporting a deterministic cluster/core formation picture.",
  "failed_quote": "As a summary, observed M_core^max-M_gas^bound correlation is inconsistent with randomly sampling the CMF in two ways: (1) the observed M_core^max-M_gas^bound relation is too tight to be consistent with the simulation that randomly sampling the CMF, and (2) the observed M_core^max-M_gas^bound relation systematically falls below the simulated M_core^max values."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "Combined Herschel HGBS and Hi-GAL data with ALMA-IMF 1.3 mm data to cover both nearby low-mass clouds and distant massive protoclusters across three orders of magnitude in bound gas mass (10^2 to 10^5 M_sun), using ALMA-IMF to resolve dense cores at 2–5.5 kpc.",
  "failed_quote": "To test our hypotheses, we examined the correlation between M_core^max and M_gas^bound based on the Herschel and Atacama Large Millimeter/submillimeter Array (ALMA) observations on a sample of nearby and distant star-forming molecular clouds."
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "Combined Herschel HGBS and Hi-GAL data with ALMA-IMF 1.3 mm data to cover both nearby low-mass clouds and distant massive protoclusters across three orders of magnitude in bound gas mass (10^2 to 10^5 M_sun), using ALMA-IMF to resolve dense cores at 2–5.5 kpc.",
  "failed_quote": "To resolve the massive dense cores in distant clouds, we retrieved the ALMA large project ALMA-IMF 1.3 mm continuum data (Motte et al. 2022; Ginsburg et al. 2022)."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Hydrogen radio recombination lines (H41alpha) used to subtract free-free emission in ALMA-IMF 1.3 mm images may have maser effects in some regions.",
  "failed_quote": "A caveat is that the hydrogen radio recombination lines may have maser effect in some regions (Martin-Pintado et al. 1989; Jiménez-Serra et al. 2013; Zhu et al. 2022), while we assumed that this does not significantly bias the intensities of free-free emission in the regions we analyzed."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "The spatial resolution used (0.03 pc) is coarser than the native resolutions of ALMA-IMF and HGBS, so extracted 'cores' (radii 0.04–0.23 pc, median 0.1 pc) are larger than cores defined at <= 0.01 pc in recent high-resolution ALMA studies.",
  "failed_quote": "We note that the spatial resolutions we are using are coarser than the native resolutions in the ALMA-IMF and HGBS data. Therefore, our derived most massive core properties are not necessarily consistent with those found in the previous publications of those consortia that were based on the native resolutions (e.g., Könyves et al. 2015; Louvet et al. 2024)."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "Why the theoretical galactic-scale SFR-m_star^max relation from Yan et al. (2017) is applicable on the spatial scale of individual molecular clouds is not yet understood and could be a coincidence.",
  "failed_quote": "We note that the SFR-m_star^max relation quoted in our recipe was derived for galactic scale star-formation. It is intriguing to see that it is also applicable on the spatial scale of molecular clouds. We do not yet have a good explanation for it. This SFR-m_star^max may be more essential than it was originally thought although it could also be a coincidence."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[1]",
  "value": "Publicly available archival datasets from HGBS archive webpage, Hi-GAL, and ALMA-IMF Dataverse repository",
  "failed_quote": "We used free-free subtracted images released by ALMA-IMF team."
 }
]
```
