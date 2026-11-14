# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024AJ....167...72D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version June 28, 2023
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Episodic** **Accretion** **in** **Protostars** **-** **An** **ALMA** **Survey** **of** **Molecular** **Jets** **in** **the** **Orion** **Molecular** **Cloud**


Somnath Dutta, [1] [Chin-Fei](http://orcid.org/0000-0002-3024-5864) Lee, [1] Doug [Johnstone](http://orcid.org/0000-0002-6773-459X), [2, 3] [Jeong-Eun](http://orcid.org/0000-0003-3119-2087) Lee, [4] Naomi [Hirano](http://orcid.org/0000-0001-9304-7884), [1]

James Di Francesco, [2, 3] Anthony Moraghan, [1] Tie [Liu](http://orcid.org/0000-0002-5286-2564), [5] Dipen [Sahu](http://orcid.org/0000-0002-4393-3463), [6, 7] [Sheng-Yuan](http://orcid.org/0000-0003-4603-7119) Liu, [1]

Ken’ichi [Tatematsu](http://orcid.org/0000-0002-8149-8546), [8, 9] Chang Won Lee, [10, 11] [Shanghuo](http://orcid.org/0000-0003-1275-5251) Li, [10] David Eden, [12] Mika [Juvela](http://orcid.org/0000-0002-5809-4834), [13]

Leonardo [Bronfman](http://orcid.org/0000-0002-9574-8454), [14] Shih-Ying Hsu, [1] [Kee-Tae](http://orcid.org/0000-0003-2412-7092) Kim, [10, 11] Woojin Kwon, [15, 16] Patricio [Sanhueza](http://orcid.org/0000-0002-7125-7685), [17, 9]


10
Jes´us Alejandro L´opez-V´azquez, [1] Qiuyi Luo, [5] and [Hee-Weon](http://orcid.org/0000-0003-0537-5461) Yi


1 _Institute_ _of_ _Astronomy_ _and_ _Astrophysics,_ _Academia_ _Sinica,_ _Roosevelt_ _Rd,_ _Taipei_ _10617,_ _Taiwan,_ _R.O.C._
2 _National_ _Research_ _Council_ _of_ _Canada,_ _Herzberg,_ _Astronomy_ _and_ _Astrophysics_ _Research_ _Centre,_ _5071_ _West_ _Saanich_ _Road,_ _V9E_ _2E7_
_Victoria_ _(BC),_ _Canada_
3 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Victoria,_ _Victoria,_ _BC_ _V8P_ _5C2,_ _Canada_
4 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _Seoul_ _National_ _University,_ _1_ _Gwanak-ro,_ _Gwanak-gu,_ _Seoul_ _08826,_ _Korea_
5 _Shanghai_ _Astronomical_ _Observatory,_ _Chinese_ _Academy_ _of_ _Sciences,_ _80_ _Nandan_ _Road,_ _Shanghai_ _200030,_ _China_
6 _Physical_ _Research_ _laboratory,_ _Navrangpura,_ _Ahmedabad,_ _Gujarat_ _380009,_ _India_
7 _Academia_ _Sinica_ _Institute_ _of_ _Astronomy_ _and_ _Astrophysics,_ _11F_ _of_ _AS/NTU_ _Astronomy-Mathematics_ _Building,_ _No.1,_ _Sec._ _4,_ _Roosevelt_
_Rd,_ _Taipei_ _10617,_ _Taiwan,_ _R.O.C._
8 _Nobeyama_ _Radio_ _Observatory,_ _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _National_ _Institutes_ _of_ _Natural_ _Sciences,_ _462-2_ _Nobeyama,_
_Minamimaki,_ _Minamisaku,_ _Nagano_ _384-1305,_ _Japan_
9 _Department_ _of_ _Astronomical_ _Science,_ _SOKENDAI_ _(The_ _Graduate_ _University_ _for_ _Advanced_ _Studies),_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_
_181-8588,_ _Japan_
10 _Korea_ _Astronomy_ _and_ _Space_ _Science_ _Institute_ _(KASI),_ _776_ _Daedeokdae-ro,_ _Yuseong-gu,_ _Daejeon_ _34055,_ _Republic_ _of_ _Korea_
11 _University_ _of_ _Science_ _and_ _Technology,_ _Korea_ _(UST),_ _217_ _Gajeong-ro,_ _Yuseong-gu,_ _Daejeon_ _34113,_ _Republic_ _of_ _Korea_
12 _Astrophysics_ _Research_ _Institute,_ _Liverpool_ _John_ _Moores_ _University,_ _IC2,_ _Liverpool_ _Science_ _Park,_ _146_ _Brownlow_ _Hill,_ _Liverpool,_ _L3_
_5RF,_ _UK_
13 _Department_ _of_ _Physics,_ _P.O.Box_ _64,_ _FI-00014,_ _University_ _of_ _Helsinki,_ _Finland_
14 _Departamento_ _de_ _Astronom´ıa,_ _Universidad_ _de_ _Chile,_ _Casilla_ _36-D,_ _Santiago,_ _Chile_
15 _Department_ _of_ _Earth_ _Science_ _Education,_ _Seoul_ _National_ _University,_ _1_ _Gwanak-ro,_ _Gwanak-gu,_ _Seoul_ _08826,_ _Republic_ _of_ _Korea_
16 _Korea_ _Astronomy_ _and_ _Space_ _Science_ _Institute,_ _776_ _Daedeokdae-ro,_ _Yuseong-gu,_ _Daejeon_ _34055,_ _Republic_ _of_ _Korea_
17 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _National_ _Institutes_ _of_ _Natural_ _Sciences,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_


(Received ...., 2023; Revised ..., 2023)


Submitted to ApJS


ABSTRACT


Protostellar outflows and jets are almost ubiquitous characteristics during the mass accretion phase,
and encode the history of stellar accretion, complex-organic molecule (COM) formation, and planet
formation. Episodic jets are likely connected to episodic accretion through the disk. Despite the importance, there is a lack of studies of a statistically significant sample of protostars via high-sensitivity
and high-resolution observations. To explore episodic accretion mechanisms and the chronologies of
episodic events, we investigated 42 fields containing protostars with ALMA observations of CO, SiO,
and 1.3 mm continuum emission. We detected SiO emission in 21 fields, where 19 sources are driving
confirmed molecular jets with high abundances of SiO. Jet velocities, mass-loss rates, mass-accretion
rates, and periods of accretion events are found to be dependent on the driving forces of the jet (e.g.,
bolometric luminosity, envelope mass). Next, velocities and mass-loss rates are positively correlated
with the surrounding envelope mass, suggesting that the presence of high mass around protostars increases the ejection-accretion activity. We determine mean periods of ejection events of 20 _−_ 175 years
for our sample, which could be associated with perturbation zones of _∼_ 2 _−_ 25 au extent around the pro

Corresponding author: Somnath Dutta

sdutta@asiaa.sinica.edu.tw

2 Dutta et al.


tostars. Also, mean ejection periods are anti-correlated with the envelope mass, where high-accretion
rates may trigger more frequent ejection events. The observed periods of outburst/ejection are much
shorter than the freeze-out time scale of the simplest COMs like CH 3 OH, suggesting that episodic
events largely maintain the ice-gas balance inside and around the snowline.


_Keywords:_ Star formation(1569), Protostars(1302), Stellar jets(1607), Stellar winds(1636), Stellar accretion(1578), Submillimeter astronomy(1647)



1. INTRODUCTION


Together, jets and outflows are very intriguing phenomena that appear during the star formation process.
They encode the history of accretion onto the protostar through the disk (e.g., Arce et al. 2007; Audard
et al. 2014; Frank et al. 2014; Lee 2020; Fischer et al.
2022) and the formation of complex organic molecules
(COMs), in terms of sublimating icy grain mantles with
increasing central luminosity (e.g., Jørgensen et al. 2015;
Taquet et al. 2016; Jørgensen et al. 2022). Low-density
mass ejections are usually referred to as “outflows”, typically exhibiting low velocities ( _∼_ 1 to a few tens km s _[−]_ [1]

) and wide angles, and are commonly traced by the [12] CO
(2 _−_ 1) emission line. In contrast, high-density ejections
along the flow axis are referred to as “jets”. Jets typically exhibit high-velocities ( _∼_ 30 to a few hundred
km s _[−]_ [1] ) and narrow-angle collimation, mostly concentrated around the flow axis, and are commonly traced by
high-density tracers like higher transitions of SiO (e.g.,
J = 5 _−_ 4, 8 _−_ 7), [12] CO (e.g., J = 2 _−_ 1, 3 _−_ 2) or SO (e.g.,
J = 8 _−_ 7). For context, the critical density for CO (J
= 2 _−_ 1) is n cr _,_ CO _∼_ (1.0 _−_ 1.2 ) _×_ 10 [4] cm _[−]_ [3] for temperature T = 150 K (our assumed temperature of jet
gas) to 50 K (our assumed temperature of outflow gas),
respectively (see Table 1). The critical density of SiO (J
= 5 _−_ 4) at a temperature of 150 K in the jet is n cr _,_ SiO _∼_
1.7 _×_ 10 [6] cm _[−]_ [3], a factor of 100 times higher than CO.
Protostellar jets driven by accreting protostars are often observed as episodic (see reviews by Arce et al. 2007;
Audard et al. 2014; Frank et al. 2014; Fischer et al.
2022). Since mass ejection originates from the disk surface and/or inner envelope during accretion, any changes
in the accretion will arguably lead to corresponding variability in the ejection phenomena. Indeed, dense knots
or extended bow shocks in the observed jets are often
discrete and clumpy, likely due to a discontinuous accretion process. In this picture, the typical duration between consecutive knots is interpreted as being due to
periods between short episodes of the ejection, possibly
driven by episodic accretion bursts. Observed periods
of ejection events range from one year to a few hundred
years (e.g., Plunkett et al. 2015; Jhan et al. 2022). Sometimes one object exhibits more than one episode, potentially originating from distinct perturbation distances in



the disk (e.g., Lee 2020, and references threin). A recent
study by Nony et al. (2020) with ALMA at 2600 au resolution found mean periods between ejection episodes of
_∼_ 500 [+300] _−_ 100 [yr] [in] [the] [W43-MM1] [protocluster,] [corrected]
for a uniform inclination angle of 57.6 _[◦]_ . Investigating
ejection events can therefore help probe the corresponding perturbation or accretion shock zones in the disk
and the associated increase in the central luminosity,
and enable explorations of the changes in ice lines and
molecular synthesis from icy grain mantles.
The JCMT Transient Survey (Herczeg et al. 2017) has
been monitoring Class 0 and I protostars in submillimeter continuum for over four years, with monthly cadence
(Johnstone et al. 2018; Lee et al. 2021). Eighteen out
of 83 protostars, 20%, are variable, all of which show
long-term, many years, secular trends. Among these
variables, the Class I source EC 53 in Serpens Main (also
known as V371 Serp) reveals a clear 18 month periodicity (Yoo et al. 2017; Lee et al. 2020), also seen in the
near-IR (Hodapp et al. 2012). The periodicity of EC 53
allows for physically modeling the location, _<_ 0 _._ 4 _R_ _⊙_,
and strength of the inner accretion disk instability (Lee
et al. 2020). The Class I source V1647 Ori, an FUOrlike system (Connelley & Reipurth 2018) with repetitive
outbursts (Ninan et al. 2013), is also seen to vary in the
submillimeter (Lee et al. 2021), along with four Class 0
sources HOPS383 (see also Safron et al. 2015), HOPS373
(Yoon et al. 2022), HOPS356, and NGC 1333 West40.
In the mid-infrared, 6.5 years of six-month cadence
NEOWISE all-sky monitoring reveals that 55% of the
735 Class 0/I protostars within the Gould Belt are variable (Park et al. 2021). Submillimeter variability primarily correlates with envelope temperature changes
produced by varying accretion luminosity whereas both
luminosity and line of sight extinction variations lead to
mid-IR variability (Johnstone et al. 2013; MacFarlane
et al. 2019a,b; Baek et al. 2020). Irregular variability
therefore dominates the mid-IR light curve classification; however, over similar observing windows the fraction of secular, long-term trending, light curves in the
mid-IR, 20% (Park et al. 2021), agrees with the submillimeter result.

Episodic accretion could significantly impact the star
formation process by modulating radiative feedback. In

Episodic Molecular Jets 3



**Table** **1.** Line Properties targeted in this study


Transition Frequency _[(a)]_ E up _[(a)]_ log 10 ( _A_ _ij_ ) _[(a)]_ Temp _[(b)]_ n _cr_


(GHz) (K) (s _[−]_ [1] ) (K) (cm _[−]_ [3] )


SiO (5 _−_ 4) 217.104919 31.26 _−_ 3.28 150 1.7E+6
CO (2 _−_ 1) 230.538000 16.60 _−_ 6.16 150 1.1E+4
CO (2 _−_ 1) 230.538000 16.60 _−_ 6.16 50 1.2E+4
C [18] O (2 _−_ 1) 219.560354 15.81 _−_ 6.22 20 1.9E+4


Notes: (a) Molecular transition parameters are adopted from CDMS
database (M¨uller et al. 2001). (b) The critical densities are calculated for these temperatures using the collisional rate coefficients
from Balan¸ca et al. (2018, SiO) and Yang et al. (2010, CO, C [18] O).
In the case of CO, a change in temperature from 50 K to 150 K
reduces n _cr_ by only _∼_ 8.5%.


the case of a continuous accretion process, for example, radiative feedback could suppress fragmentation by
maintaining a warm environment in the surrounding
disk or cloud core (Offner et al. 2009; Krumholz et al.
2014; Yıldız et al. 2015). On the other hand, episodic
accretion can weaken this effect by allowing this disk
to sufficiently cool during the quiescent phase and engendering its fragmentation (Stamatellos et al. 2012).
Thus, episodic accretion may affect the formation of binary/multiple systems, planets, and initial mass function of protostars (Stamatellos et al. 2011; Mercer &
Stamatellos 2017; Riaz et al. 2018). Furthermore, variations in stellar luminosity and the corresponding changes
in the surrounding temperature of the disk and envelope can affect the chemical composition and gas-ice
balance (Cieza et al. 2016; Wiebe et al. 2019; Hsieh
et al. 2019; Jørgensen et al. 2022). Taquet et al. (2016)
suggested that during the accretion phase, higher order COMs (e.g., CH 3 OCH 3, CH 3 OCHO, C 2 H 5 OCH 3,
C 2 H 5 OC 2 H 5, C 2 H 5 OCHO) could be formed via gas
phase reactions around snowlines of the simpler COMs
(e.g., CH 3 OH), i.e., in the hot regions where T ≳ 100
K. While cooling down during the more quiescent phase,
CH 3 OH or water may freeze-out into ice at _∼_ 100 - 120 K
more quickly than the higher-order COM species (T _∼_
70 K), due to relatively low binding energies of higherorder COMs than CH 3 OH, water. Hence, the abundance of higher-order species could be higher than those
of simpler COMs around the snowlines. Therefore, accretion intervals may reveal the effects of radiative feedback on the COMs and planet formation process.
After the first discovery of the protostellar outflow
by Snell et al. (1980), several observational studies
have been performed to characterize outflows (Cabrit



& Bertout 1992; Bontemps et al. 1996; Lee et al. 2013;
Dunham et al. 2014; Yıldız et al. 2015; Kim et al. 2019).
Due to limitation of the observations, most of the previous studies were with single dish telescopes with lowresolution, large scale, and poor sensitivity. Recently,
Podio et al. (2021) have investigated a sample of 30
sources (classified as 25 Class 0, 4 Class I, one continuum) with IRAM-PdBI as a part of CALYPSO survey. Their study reveals that most of the jets are possibly dust-free winds launched from inside the dustsublimation radius and the ejection rate decreases as the
source evolves and accretion fades. It is time to enlarge
the statistics with higher sensitivity and unbiased samples with similar environmental effects (e.g., all sources
in a single molecular cloud).
In this paper, we describe ALMA observations of a
statically significant sample of protostars in the Orion
molecular cloud. Their location in common puts them
at a similar distance ( _∼_ 400 pc) and in a similar environment, minimizing the effects of environmental differences on the observed parameters. First, we probe
the morphology of the jet using the most efficient tracers of molecular jets to investigate driving mechanisms
(e.g., whether the outflowing material is jet-driven or
wind-driven), shock structure and chemistry. Second,
we seek to understand the origin of gas phase SiO in
the jet, following the increasing evidence of SiO in the
jet. Third, we probe accretion mechanisms based on the
distribution of ejected material, especially the episodic
knots. Finally, these data allow us to address important
questions like: Is there any direct or indirect correlation
between episodic jets and COMs formation in the disk?
What would be the possible impact of episodic accretion
on the emerging planets? In a subsequent investigation
these same outflow data will be analysed using channel maps and position-velocity diagrams and compared
with the theoretical unified jet-wind model developed by
Shang et al. (2023).
We describe the sample selection in Section 2.1 and
the ensuing observations in Section 2.2. Section 3 describes the results of continuum and line data analyses.
In section 4, we discuss the jet morphology and its connection to the accretion process. Section 5 summarizes
the work. In the Appendices, we discuss the properties
of individual objects including maps and spectra of each.


2. SAMPLE SELECTION AND OBSERVATIONS


2.1. _Sample_


During ALMA cycle 6, we initiated a survey-type
project (ALMASOP: ALMA Survey of Orion PGCCs)
to investigate systematically the fragmentation of dense
cores into protostars (Dutta et al. 2020). We se

4 Dutta et al.



30


25


20



20





10

15


10

0


5


-10


-20


-20 -10 0 10 20


(")


**Figure** **1.** Example image of ALMA 1.3 mm continuum
emission detected toward protostar G203.21-11.20W2. The
typical beam size of _∼_ 7 _[′′]_ _._ 52 _×_ 5 _[′′]_ _._ 52 (80 _[◦]_ _._ 7) is shown in red
in the lower left. The contours are at 3 _×_ (1, 2, 4, 8, 12) _σ_,
where the sensitivity _σ_ = 0.4 mJy beam _[−]_ [1] . The cross mark
indicates the continuum centre at high-resolution, adopted
from Dutta et al. (2020). The blue dashed line indicates the
outflow/jet axis, determined from the SiO emission. A scale
bar is also shown for context.


lected 72 extremely cold young dense cores from the
Planck Galactic Cold Cores (PGCC) catalogue, including both candidate starless and protostellar core candidates, therefore, unbiased to any spectral “Class” of the
protostar. The PGCCs are, however, biased to sources
with cold dense material around them - so potentialy
significantly young! From these observations, we detected 70 substructures within 48 detected dense cores,
which include five candidate prestellar cores with centrally dense structures of roughly 2000 au scale where
the core shows substructure within the dense portion
(Sahu et al. 2021), and several hot corinos (Hsu et al.
2020, 2022). Furthermore, some sources were revealed
to be multiple systems (Luo et al. 2022). The observations also revealed one of the oldest (G205.46-14.56S3;
Dutta et al. 2022a) and one of the youngest protostars
(G208.89-20.04Walma; Dutta et al. 2022b) with a bipolar molecular jet in SiO emission. Interestingly, a few
protostars were also found to exhibit monopolar SiO jets
(Jhan et al. 2022).
After removing the candidate prestellar cores from the
sample, we selected from Dutta et al. (2020) 66 substructures in 42 observing fields containing one or more protostars to investigate outflow and jet characteristics. We
identified 42 outflows detected in CO emission. The rest
were likely not detected due to insufficient sensitivity or



their outflows could not be separated from the ambient cloud emission. Out of 42 outflows, SiO emission
was detected in 21. Such SiO emission could trace vari
ous shocked regions, e.g., knots or bow shocks, collision
zones of adjacent outflows, or collision zones of outflows
on surrounding molecular clouds. We investigate 39 outflows with CO emission in this paper, of which 18 fields
are also associated with SiO emission. The results for

the remaining three ALMASOP protostellar objects are
adopted from previously published literature i.e., Dutta
et al. (2022a, G205.46-14.56S3 and G206.93-16.61W2)
and Dutta et al. (2022b, G208.89-20.04Walma). The 39
outflow objects have bolometric luminosities L _bol_ _∼_ 0.4
to 180 L _⊙_ and bolometric temperatures of T _bol_ _∼_ 15 to
180 K, though some have undetermined L _bol_ and T _bol_
due to lack of infrared data. Based on the object selection criteria, this sample is one of the youngest, coldest,
unbiased protostellar samples within a the molecular environment of the Orion cloud, all located at a similar
distance. These features make this sample one of the
most suitable samples for investigating variations of the
outflow/jet morphology in a consistent manner.


2.2. _Observations_


In this paper we make use of the ALMASOP data
observed in Band 6. Details of the observations and
data reduction were presented by Dutta et al. (2020).
In brief, we generated 1.3 mm continuum images using
low-resolution ACA observations of typical beam size
7 _[′′]_ _._ 6 _×_ 4 _[′′]_ _._ 1 to probe large-scale envelope emission. The
datacubes of CO(2 _−_ 1), SiO(5 _−_ 4), and C [18] O(2 _−_ 1) line
emission are generated using high-resolution observations of typical beam size _∼_ 0 _[′′]_ _._ 38 _×_ 0 _[′′]_ _._ 35 to explore the
jet/outflow structures. Here, we combined data from
three configurations (TM1, TM2, and ACA) to improve
the sensitivity of the line cubes. The final maps have a
primary beam (PB) size _∼_ 40 _[′′]_, smaller than the ACA
PB size _∼_ 60 _[′′]_ . Some of the outflows/jets extend beyond the TM1 PB area, whereas the ACA data are more
suitable for sampling more extended outflow/jet emission. We present, however, the high-sensitivity, combined TM1+TM2+ACA cubes to characterize outflow
cavity walls and shock/knot structure within the jet
more precisely. We also compare our results with those
from ACA-only observations. We binned the velocity
channels to a resolution of 2 km s _[−]_ [1] to improve the sensitivity further.


3. RESULTS


3.1. _1.3 mm_ _Continuum_


The low-resolution ACA 1.3 mm continuum image of
the source G203.21-11.20W2 is shown in Figure 1. The

Episodic Molecular Jets 5



10


5


0

|Col1|Class0<br>Class1<br>All|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Class0<br>Class1<br>All|Col17|Col18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||



0.0 0.8 1.6 2.4 3.2 4.0 4.8 5.6 6.4 7.2 8.0 8.8


M Env (M )


**Figure** **2.** Histogram of envelope masses estimated using
1.3 mm emission at a resolution of _∼_ 7 _[′′]_ _._ 6 _×_ 4 _[′′]_ _._ 1.


remaining images are presented in the Appendices B
(objects with confirmed molecular jet), C (objects with
complex SiO emission morphology and not considered
for jet parameter estimation in this text), D (objects
with no SiO emission but well defined CO outflow) and
E (objects with no SiO emission and no well-defined
CO outflow). To determine the properties of the continuum sources, we fit the emission above the 3 _σ_ contour
using CASA _imfit_ task with one or more 2-dimension
Gaussians for one or more, respectively visually identified peaks. Integrated fluxes were obtained from the
‘flux’ component in the output file of _imfit_ task. All deconvolved Gaussian parameters for each source are listed

in Table 2.

For an extremely young protostar, the 1.3 mm emission could be optically thick, especially in the central
core region. Hence, this emission may represent a lower
limit to the total dust column density from the inner
envelope around the protostars. For simplicity, however, we assume the emission is optically thin to infer
the lower limit of inner envelope mass (M Env ) following
the equation:

_M_ _Env_ _∼_ _D_ [2] _F_ _ν_ ( _ν_ ) (1)
_B_ _ν_ ( _T_ _dust_ ) _κ_ _ν_


The assumed dust mass opacity is _κ_ _ν_ _∼_ 0.00899( _ν_ /231
GHz) _[β]_ cm [2] g _[−]_ [1], assuming a gas-to-dust mass ratio of
100 (e.g., Lee et al. 2018). We also assume a dust opacity spectral index _β_ _∼_ 1.5. It is worth noting that _β_
could be higher than this value at early protostellar
stages due to smaller dust grains, and could be _<_ 1.0
for more evolved Class 0 or in Class I objects where dust
grains have grown (Draine 2006). Following Dutta et al.
(2020), we adopt slightly different distances _D_ for the
sources in Orion A ( _∼_ 389 _±_ 3 pc), Orion B (404 _±_ 5
pc), and _λ_ -Ori (404 _±_ 4 pc). _F_ _ν_ ( _ν_ ) is the measured



flux density. _B_ _ν_ ( _T_ dust ) represents the Planck blackbody
function at a dust temperature of _T_ dust .
We assume an optimal _T_ dust _∼_ 15 K for all the inner envelopes (e.g., Dutta et al. 2022b). The resulting
masses are also listed in Table 2. Errors are estimated

based only on uncertainties in the flux. The value of
_T_ dust could vary from as small as 10 K in the younger
protostars to 30 K in the evolved protostars. For an increase of +15 K in temperature, the derived mass will
decrease by 60%, and a decrease of _−_ 5 K will increase
the derived mass by 85%. The histogram of all derived
masses is shown in Figure 2, including Class 0, Class I
and some unclassified cores detected with ACA emission. The masses peak at _∼_ 0.1 M _⊙_, where most protostars in this sample have a 1.3 mm masses _<_ 1.2 M _⊙_ .
The mean masses of Class 0 and Class I sources are 1.4

M _⊙_ and 0.65 M _⊙_, respectively. The masses _>_ 1 M _⊙_ are
mostly associated with multiple systems (see Appendix
for comments on the individual objects).


3.2. _Systemic_ _Velocity_ _from_ _C_ [18] _O_


The systemic velocities ( _V_ _sys_ ) of the sources were estimated from the C [18] O emission observed at the continuum peak in high-resolution maps, where C [18] O is most
likely tracing the disk/envelope emission around the protostars. It could, however, also trace envelope material
entrained by outflow along the boundary wall. Figure 3
shows an example of such C [18] O spectra around the central protostar. The C [18] O spectra of other objects are
shown in panels ‘ _b_ ’ of Figures in Appendix B, C, D and
E. In most cases, C [18] O spread only over 2-3 channels
(one channel corresponding to velocity resolution _∼_ 2.0
km s _[−]_ [1] ), making it challenging to get a reasonable Gaussian fit. Therefore, we chose the velocity of the peak
emission as the _V_ _sys_ (Figure 3) or we average the velocities of the 1st and 2nd brightest velocity-channels from
the spectra in cases where the peak emission spanned
over more than one channel (as in case G208.89-20.04E
in Figure B6). All these determined _V_ _sys_ values were
checked by eye against the spectra. The respective _V_ _sys_
values are listed in Table 2.


3.3. _Physical_ _Structure_ _of_ _outflow_


To assess outflow morphologies, we analyzed the CO

_−_
(2 1) emission. We first investigated each velocity channel and spectra along the putative flow axis to identify bipolar emission. We found three kinds of such
emission, likely due to outflow inclination angle: (i)
the blueshifted and redshifted emissions are well separated on the sky on both sides of the systemic velocity;
(ii) there are instances where blueshifted and redshifted
emission partially overlap; and (iii) blueshifted and redshifted emission almost entirely overlap. To explore such

6 Dutta et al.



|Col1|Col2|C18O|Col4|
|---|---|---|---|
|0<br>5<br>10<br>15<br><br>Flux (mJy beam<br>1)||||
|0<br>5<br>10<br>15<br><br>Flux (mJy beam<br>1)||||


10 0 10 20 30

Velocity (km s 1 )


**Figure** **3.** The C [18] O spectrum of G203.21-11.20W2 extracted from high-resolution maps. The vertical line indicates the systemic velocity of the object determined from
the spectrum at _V_ _sys_ = 10 km s _[−]_ [1] .


different kinds of outflow features, we estimated inclination angles _i_ a using the low-velocity CO emission above

3 _σ_ .
Figure 4a presents the integrated CO (2 _−_ 1) line emission map of the source G203.21-11.20W2. A schematic
diagram describing the possible structure of the outflow is shown in Appendix A (Figure A1a). The outermost shell of the outflow is observed to have a parabolic
structure. We assume that the molecular CO outflow
shell is a radially expanding parabolic shell of the underlying wide-angle wind, and then accordingly fit a
parabolic shape to the moment zero map of CO emission using Equation A1 to obtain the curvature ( _c_ ) at
the launching point. Using the same _c_ values, we fit another parabola in the PV diagram. Since CO emission
may trace the outflow shell along with jet and ambient
cloud emission, the fitting depends on the correct assumption of the outflow shell from other components.
The likely ambient material near the systemic velocity
is distinguished after visually inspecting individual velocity channels in the data cube. Similarly, high-density
axial emission and high-velocity emission are considered
as likely jet emission. If the objects exhibit high-velocity
jets blended with the low-velocity outflow emission, we
distinguish the outflow shell by comparing the CO PV
diagram with that of SiO emission (Figure 5), assuming
SiO traces mostly jet components. In Figure 4a, fitting the parabola to the outermost contour of the out


where the factor _f_ _ia_ is the correction factor for the inclination of the system in the plane of the sky. The
inclination corrected _F_ CO values are listed in Table 3.



flow yields c = 0.5 arcsec _[−]_ [1] for both the Southern and
Northern lobes. Using these _c_ values, we fitted parabolas to the “outflow” emission in PV space as shown in
Figure 4b with Equation A3 to create a complete 3D
paraboloid structure, where the fitting equations include
the inclination of the structure in the plane-of-sky (see
Appendix A, for details). For example, the inclination
angle for G203.21-11.20W2 is estimated to be _i_ _∼_ 20 [+5] _−_ 5
degree. In the _c_ and _d_ panels of Figures in Appendices
B, C, D and E, we present all the fitted parabolas in
integrated emission as well as in PV diagrams. A total
of 20 outflows are fit and the inclinations have been estimated from this model. Some of the outflows are not fit
due to indistinguishable outflow shells. The inclination
angles are listed in Table 3 for all the objects. Here, we
note that this model is suitable only for those objects
that have well-defined outflow shells, i.e., outflow walls
that are well distinguished from the ambient material or
outflows of multiple sources.


3.4. _Outflow_ _Force_


Outflow force _F_ CO is the mean rate of momentum _P_
of outflowing material, derived by estimating the outflow momentum over the dynamical time _T_ _dyn,out_ of the
outflow where _T_ _dyn,out_ is the length of the jet divided by
the velocity of the outflow. Outflow force _F_ CO was calculated from the beam-averaged CO emission across the
whole velocity range above 3 _σ_ on each lobe (blue and
red) separately. To avoid contamination from ambient
material, we removed a few channels near the systemic
velocity after inspecting channel maps. First, outflow
emission above 3 _σ_ in the whole data cube is converted

into mass. For example, the k-th channel has an outflow
mass of _M_ _k_ :



_M_ _k_ = _µ_ _H_ 2 _m_ _H_ _A_ � _l_ _[N]_ _[CO][,][l]_ (2)

_X_ _CO_



where the beam-averaged CO column density _N_ _CO_ is
summed over outflow pixels _l_ on the k-th channel and
each pixel has an area of _A_ . We assumed a CO-to-H 2
abundance ratio of X _CO_ _∼_ 10 _[−]_ [4] in the outflow for a
excitation temperature of _T_ _ex_ _∼_ 50 K. In the next step,

the estimated masses are converted into momentum _P_

_∼_ _M_ _k_ _V_ _k_, for a mass of _M_ _k_ on k-th channel with the
central velocity of _V_ _k_ = _| V_ obs _−_ _V_ sys _|_ . Finally for a
total outflow extension of _R_ _CO_ with maximum outflow
velocity _V_ _CO,max_, _F_ _CO_ is expressed as:



_F_ _CO_ = _P_ = _f_ _ia_ _V_ _CO,max_ � _k_ _[M]_ _[k]_ _[V]_ _[k]_ (3)
_T_ _dyn,out_ _R_ _CO_

Episodic Molecular Jets 7





**Figure** **4.** (a) High-resolution ALMA map of G203.21-11.20W2 in CO emission integrated from _−_ 50 km s _[−]_ [1] to +50 km s _[−]_ [1] .
The contours are over plotted at 3 _×_ (1, 2, 3, 4, 6, 8, 12) _σ_, where sensitivity _σ_ = 4.8 K km s _[−]_ [1] . The synthesized beam size _∼_
0 _[′′]_ _._ 41 _×_ 0 _[′′]_ _._ 34 is shown in the lower left. CO emission is extended in the North-West to South-East direction with a position
angle of _∼_ 122 _[◦]_ . The cyan (blueshifted) and red (redshifted) parabolas are best fits assuming a proportionality constant c = 0.5
arcsec _[−]_ [1] . (b) Position Velocity (PV) diagram along the jet axis of [12] CO(2 _−_ 1) emission. The black contours are at 3 _×_ (1, 2, 3, 4,
5, 6) _σ_, where sensitivity _σ_ = 0.11 K. The beam sizes are shown in the lower left (in red) emission. The red and cyan parabolas
here are for inclination angle, _i_ = 20 _[◦]_ . Cyan and red represent the North-West and South-East direction, respectively, in panel
(a). The magenta cross mark in each panel is the location of the continuum peak.





**Figure** **5.** (a) High-resolution ALMA map of G203.21-11.20W2 in SiO emission integrated from _−_ 50 km s _[−]_ [1] to +50 km s _[−]_ [1]

with sensitivity _σ_ = 4.6 K km s _[−]_ [1] . The CO contours are over-plotted from Figure 4a. The synthesized beam size _∼_ 0 _[′′]_ _._ 41 _×_ 0 _[′′]_ _._ 34
is shown in the lower left. The jet axis is shown in a yellow dashed line. (b) Position-Velocity (PV) diagram along the jet axis
of SiO emission with sensitivity _σ_ = 0.15 K km s _[−]_ [1] . The CO contours are the same as in Figure 4b. The beam sizes are shown
in the lower left (in red). The dashed lines at velocity = 33 km s _[−]_ [1] are the mean jet velocity, V _j_ (uncorrected for inclination).
The knot location is marked in B1, B2, ..... and R1, R2, .... in blue and redshifted lobes, respectively. The magenta cross mark
in each panel denotes the location of the continuum peak.

8 Dutta et al.









0
0.0 0.2 0.4 0.6 0.8 1.0

Sin(i)


**Figure** **6.** Inclination corrected mean iet velocities _V_ _j,cor_ =
sin _V_ _j_ _i_ [are] [shown] [as] [a] [function] [of] [sin] _[ i]_ [,] [where] _[i]_ [is] [the] [measured]
inclination angle. The mean value of _V_ _j,cor_ = 113km s _[−]_ [1] is
also shown. Monopolar and bipolar jets are shown as circles
and squares.


Here we note that we do not cover the full outflow extents within the TM1/TM2 primary beam ( _∼_ 40 _[′′]_ ). If,
however, we increase the FOV (as for ACA maps), the
outflow mass and dynamical time, may both increase,
and so _F_ CO measurements are not expected to change
drastically. We also compared the present _F_ CO values
with those derived from ACA maps (FOV _∼_ 60 _[′′]_ ), and
we see only changes by factors of 1 to 1.5 from the
smaller primary beam values. In addition, we could
not recover the whole outflow emission from the ACA
maps due to their relatively poor sensitivity compared
with the combined high-resolution maps. Therefore, we
present only the _F_ CO measurements derived from the
high-sensitivity combined maps.
Errors of _F_ CO estimation depend on the amount of
missing flux in interferometric observations, the lack of
coverage of the full length of the outflow lobe, calibration, the optical depth of CO, the temperature variation
of the outflow, and errors in the inclination angle measurements. Since the above information could not be

recovered simultaneously from the present observations,
we assume a conservative error of 40% in all plots in the
subsequent sections.


3.5. _Molecular_ _jet_ _detection_ _and_ _episodes_ _of_ _accretion_


To assess the high-density jets associated with protostars within the outflow cavities, we searched the CO
and SiO data cubes at velocities both blue- and red
shifted from the _V_ _sys_ . Given its higher critical density
and an expected increase in SiO from dust grains shattered in shocks, the SiO emission is more suitable for
detecting the high-density material and shocks in the
jets, where as the CO traces both high-density jet as
well as low-density outflow structures. As shown in Figure 5 for G203.21-11.20W2, SiO is clearly observed along



the flow axis, where CO is seen more widely i.e., within
and surrounding the SiO emission along the flow axis,
and in the CO outflow shell. In the red lobe, four knots
(R1, R2, R3, and R4) are consistent in both SiO and
CO emission, another knot (R5?) is possibly detected
in CO emission but not detected in SiO emission. In the
blue lobe, two knots (B1 and B5) are detected in both
SiO and CO emission, whereas the CO peaks at B2?,
B3?, and B4? are not detected with SiO emission. For
the other outflows, the CO and SiO integrated maps and
their respective PV diagrams are are presented in Appendices B (objects with confirmed molecular jet) and
C (objects with complex SiO emission morphology and
not considered for jet parameter estimation in this text).
We observed 18 fields with SiO emission, out of which
14 have confirmed protostellar jets. Three (G200.3410.97N and G205.46-14.56M2, G205.46-14.56N2) exhibit extended SiO emission along the jet axis, which
could be the bow-shocks of jets or collision zones between outflow and ambient material. SiO in one field
within G209.55-19.68N1 is clearly a collision zone between two outflows. In the case of G205.46-14.56M2,
the driving source of SiO is not clearly identified, and
it could be emission from other molecules in this linerich source (e.g., a hot corino) that mimics SiO emission. It is difficult to conclude the existence of a jet in
this particular source from the present observations. All
the SiO emission integrated maps and PV diagrams are
shown in Figures B1-11 and C1-6. Six of the sources exhibit monopolar or nearly-monopolar SiO jets (G203.2111.20W2, G191.90-11.20S, G205.46-14.56M1, G205.4614.56S1, G209.55-19.68S2, G211.47-19.27S ~~B~~ ). In some
cases, CO traces both sides of the jet but SiO is monopolar, such as the blue-shifted component of G203.2111.20W2. In some monopolar cases, like the source
G209.55-19.65S2, there is no jet emission detected in
the blue-shifted lobe with SiO as well as in the CO.

The mean of the velocity of the brightest peak knot
emission is considered to be the observed jet-velocity
_V_ _j_, and these are listed in Table 3. A histogram of measured mean jet velocity corrected for inclination angle,
i.e., V _j,cor_ (= sin _[V]_ _[j]_ _i_ [) is shown in Figure][ 6][.] [Jet velocities are]

distributed over a large range from _∼_ 50 km s _[−]_ [1] to 290
km s _[−]_ [1], where most ( _∼_ 60%) are less than 100 km s _[−]_ [1] .
Proper motion studies of jet knots of the object HH 212
study also reveal the jet velocity could be as small as _∼_
50 km s _[−]_ [1] (Lee et al. 2022). The mean of all corrected jet
velocities are estimated to be _V_ = 113 km s _[−]_ [1] .
_j,cormean_
We note that a few of the outflows have very small inclination angles (close to edge-on), but some inclinations
could not be derived accurately from present observations of outflow shells. In those cases, the jet velocities

Episodic Molecular Jets 9



could change significantly with only a few degrees of
change in inclination angle given the error bars in the
measured inclination angles, as shown in Figure 6 (see
also Table 3). For sources G205.46-14.56S1 ~~A~~ (V _j,cor_
= 80.22 km s _[−]_ [1] ) and G208.89-20.04E (V _j,cor_ = 114.60
km s _[−]_ [1] ) in particular, the inclination angles could be
_<_ 1 _[◦]_, and so a significant change in velocity could be
expected given improved inclination measurements.
The mean timescales between knots are measured as
_T_ _knot_ = _[δR]_ _V_ j [tan(] _[i]_ [),] [where] _[δ]_ [R] [is] [the] [mean] [distance] [be-]

tween two consecutive knots. The values are listed in

Table 3. The derived _T_ _knot_ values range from _∼_ 20 years
to 175 years for different jet knot pairs.


3.6. _Jet_ _Mass-Loss_ _Rate_ _and_ _Kinetic_ _Luminosity_

The jet mass-loss rates _M_ ˙ _j_ were derived from the CO
integrated emission. First, we disentangled the most
likely jet emission from the outflow shell by considering
SiO emission as being representative for the jet. Figure
5b shows the SiO emission of G203.21-11.20W2. Such
emission is also found at high-velocity ( _>_ 15 km s _[−]_ [1] ).
Therefore, we consider the jet velocity range to extend
from minimum SiO velocity to the maximum available
CO (or SiO) velocity. This particular object is moderately inclined ( _i_ _∼_ 20 _[◦]_ ). For a highly inclined object
like G191.90-11.20S (close to edge-on; Figure B1 in Appendix B.1), however, the SiO emission does not extend
to the high-velocity range, so here we consider the whole
velocity range of SiO emission as jet, independent of
higher-velocity consideration.
Next, nearest to the continuum we choose the peak
emission from the knots in CO maps integrated over
likely jet velocities. These knots are expected to be less
distorted by flow into the ambient medium than farther
away knots. The peak emission is converted into beamaveraged CO column density _N_ _CO_ assuming a specific
excitation temperature of _T_ _ex_ _∼_ 150 K within the jet.
_N_ _CO_ is utilized to obtain the H 2 column density _N_ _H_ 2 for
a CO abundance ratio, X _CO_ = _N_ _CO_ / _N_ _H_ 2 ( _∼_ 4 _×_ 10 _[−]_ [4],
Glassgold et al. 1991). We consider the molecular jet
to be flowing through a uniform cylinder at a constant
density at constant speed along the transverse beam direction. Since the jet widths are not spatially resolved
evensize _b_ at _m_ isthetakenhightospatialbe theresolutionjet width.achieved,Thus, _M_ ˙the _j_ canbeambe
expressed as:


˙ _N_ _CO_
_M_ _j_ = [1] _V_ _j,cor_ _b_ _m_ _,_ (4)

3 _[µ]_ _[H]_ [2] _[m]_ _[H]_ _X_ _CO_


where _µ_ _H_ 2 = 2.8 is the mean molecular weight and _m_ _H_
is the mass of a hydrogen atom. _V_ _j,cor_ is the mean deprojected jet velocity (i.e., _V_ _j_ /sin( _i_ )). The knots observed















**Figure** **7.** A schematic diagram based on observations that
illustrates general morphologies of the 1.3 mm continuum,
and the C [18] O, CO and SiO line emission. The 1.3 mm continuum and C [18] O emission trace the disk and envelope. CO
emission delineates the outflow shell and whole knot structure including a CO emission forward front, a SiO+CO emission middle shock front, and a CO emission backward front.


in this spatial resolution likely delineate the internal bow
shocks or gas that has been highly compressed by shocks.
Since the knots are not resolved, we assume a compression factor of 1 _/_ 3 following Lee et al. (2007a,b). The jet
kinetic luminosity is defined asThe inclination corrected _M_ ˙ _j_ and _L_ _j,kin_ _L_ _j,kin_ = (1values are listed _/_ 2) _×M_ [˙] _j_ _V_ _j,cor_ [2] [.]
in Table 3.

Given that CO abundances could be as small as X _CO_
_M∼_ ˙ _j_ 10and _[−]_ [4] instead of the present assumption, the tabulated _L_ _j,kin_ values could be higher. Therefore, we
consider our measured values to be lower limits to the

mass loss rates. The error bars of these measurements

also depend on various factors in flux measurements, as
discussed above in section 3.4. With these complications,measuredwe assumed _M_ ˙ _j_ values.a conservative error of 40% for the


4. DISCUSSION


4.1. _Which_ _emission_ _traces_ _Which_ _component?_


The schematic diagram in Figure 7, drawn based on
the observations, describes various components of protostars traced by the 1.3 mm continuum and the C [18] O

10 Dutta et al.

















**Figure** **8.** A schematic diagram illustrating a monopolar jet. (a) Each knot consists of three observed layers: a forward CO
emission front (in red), a middle SiO+CO front (in green), and a backward CO emission front (in blue). (b) close up view of a
knot in the redshifted lobe. The colours are the same as in panel- _a_ . An additional compressed layer is highlighted between the
forward CO front and middle SiO+CO front. (c) The possible temperature distribution of the knot of the panel- _b_ is plotted,
following the simulation results by Lee et al. (2001). Layers- _iii_ and _iv_ have the highest temperature and layer- _i_ is cooler than
_iii_ and _iv_ . Layer- _ii_, however, exhibits a temperature discontinuity or is much cooler than other layers. The density of layer- _ii_
is maximum than other layers. For the redshifted lobe, an observer can see the middle SiO+CO (layer- _iii_ ) and backward CO
layers (layer- _iv_ ). For the blue-shifted lobe, the scenario is opposite, where an observer can see only a forward CO emission front
(layer _i_ ). Emission from layers- _iii_ and _iv_ might be shielded by the compressed and coolest layer- _ii_ . In that case, only CO jet
can be observed in blueshifted emission. If layer- _i_ is not dense enough, then even CO emission can not detect the jet in the
blueshifted lobe.



(2-1), CO (2-1), SiO (5-4) lines. The continuum maps at
140 au and 2200 au resolution delineate the thermal dust

emission from the disk and inner envelope, and inner to
moderate-scale envelope emission, respectively. At 140
au resolution, C [18] O emission likely traces the disk and
inner envelope. In a few cases, we may have resolved
the larger disks but the velocity resolution of our observations is not sufficient to probe their kinematics and

geometry.
As shown in Table 1, the SiO emission has a higher
critical density ( _n_ _cr_ _∼_ 1.66 _×_ 10 [6] cm _[−]_ [3] ) than that of
CO ( _n_ _cr_ _∼_ 1.06 _×_ 10 [4] cm _[−]_ [3] ). We estimated the optical depth for SiO ( _τ_ _SiO_ ) and CO ( _τ_ _CO_ ) emission from
the peak emission within the knots, assuming a temperature _T_ _ex_ _∼_ 150 K, and find that the SiO emission is
optically thicker than that of CO ( _τ_ _SiO_ _>_ _τ_ _CO_ ) within
the knots. So, CO emission arises from deeper layers
within the knots than does the SiO emission. In the AL
MASOP sample, we observe that CO emission is tracing the low-density outflow shell. The shock regions or
knots of higher density along the jet axis are detected



in both SiO and CO emission, and we expect the latter to trace more interior parts of the knots due to its
lower optical depths. We also see CO emission forward
and in front of the SiO+CO emission boundary in some
knots, which could consist of relatively lower-density and
cooler material than the SiO+CO shock regions. Another layer of CO emission in a back was also seen in
a few knots, which could be the slower-moving material
of the shock (see G191.90-11.20S in Figure B1d and f of
the Appendix). In a bow-shock type of knot, we indeed
usually see an angular offset in CO and SiO emission
(e.g., G191.90-11.20S in Figure B1f, G208.89-20.04E in
Figure B6f, G209.55-19.68S1 in Figure B7f). Such bowshocks exhibit successively a CO forward front, SiO peak
emission and then CO peak emission (see also Figure
8). The backward shock detected in CO could be due
to either optical depth effects or slower-moving material
(discussed later).


4.1.1. _Monopolar_ _Molecular_ _jet_


Some SiO jets are observed to be only monopolar, or
have bright red-shifted knots but faint blueshifted knots.

Episodic Molecular Jets 11



Examples of such asymmetric jets include G203.2111.20W2, G191.90-11.20S, G205.46-14.56M1, G205.4614.56S1, G209.55-19.68S2, and G211.47-19.27S ~~B~~ . In
these cases, the redshifted SiO emission can be observed prominently and the blueshifted emission is either
fainter, is missing, or has fewer knots. As an example,
in G203.21-11.20W2 (Figure 5) the blueshifted CO jet
is visible and SiO is not detected in most of the CO
knot locations (only fainter B1 and B5). In the case
of G209.55-19.68S2, however, the blueshifted jet is completely missing in both CO and SiO emission (Figure B8
in the Appendix).
A possible scenario for the monopolar jet is illustrated
in Figure 8. In most knots, we observe an SiO forward
peak and a CO backward peak, and additionally the
whole SiO+CO peaks are surrounded by a less bright
CO front in both space and velocity. Therefore, we
have divided the observed emission in the knots into
three sub-layers: layer-(i), a forward CO front (in red),
which is possibly slow-moving, dense, cooler material;
layer-(iii), a middle SiO+CO front (in green), which
could be the faster moving, denser, and warmer part
of the knots; and layer-(iv) a backward CO front (in
blue) which is relatively slow, less dense, and cooler than
middle-front. Now, following simulation results by Lee
et al. (2001), we introduce another sub-layer layer-(ii):, a
compressed layer (black and white lines) between layers(i) and (iii), which could be the fastest moving, densest,
and coolest layer but one which is not detected in our observations. As predicted by Lee et al. (2001), the density
and temperature profiles of different layers are shown in
panel (c). In the general scenario of shock processing, a
slow-moving layer-(i) collides with a faster-moving layer, e.g., (ii)+(iii), and as a result, a very high-density compressed layer-(ii) is originated. Since radiative cooling
is inversely proportional to density (e.g., Blondin et al.
1990), layer-(ii) should cool faster than the other layers and produce a temperature discontinuity, as shown
in panel (c). Layer-(iii) is the transition region between
the compressed layer and the slow-moving CO layer-(iv).
It could be detected if it reaches the critical density of
the SiO. Layer-(iv) is the slow-moving trail of layers(ii)+(iii).
In the redshifted lobe, an observer can see layers( _iii_ )+( _iv_ ) in SiO and CO emission, and the forward
CO front at layer-( _i_ ) could be shielded by the layer(ii) of high density and low temperature. In the blueshifted lobe, the scenario is opposite to that of a redshifted lobe, where an observer can only see the forward CO material front from layer-(i), as in the case of
G203.21-11.20W2. Emission from layers-(iii) and (iv)
might be shielded in the compressed layer-(ii) of the



highest-density and coolest material, therefore, only the
CO jet can be observed in the blueshifted lobe. If the
forward front (layer-i) is not dense enough and the compressed layer (layer-ii) is highly dense and cool, then the
jet can remain undetected even with CO emission, as in
the case of the blueshifted lobe of G209.55-19.68S2 (Figure B8) where the jet component is completely missing
in both the SiO emission as well as in the CO emission.

The above scenario can explain most of the redshifted SiO monopolar jets in the ALMASOP sample. Another source NGC 1333-IRAS2A from CALYPSO IRAM _−_ PdBI survey exhibits blueshifted jet
only Codella et al. (2014). G205.46-14.56M1 (Figure
B2) also exhibits one bright blueshifted knot but fainter
redshifted SiO emission in the knot location. Indeed,
such behaviour scenario is difficult to explain with the
above schematic diagram. Therefore, we also suggest
that there could be further unknown intrinsic properties driving monopolar jets.


4.1.2. _Molecular_ _jets_ _and_ _protostellar_ _evolutionary_ _phase_


Class 0 protostars are observationally defined as being
in the youngest phase of star formation, with bolometric
temperature _T_ _bol_ _<_ 70 K and infrared spectral index of
_α_ _IR_ _>_ 0.3 (Furlan et al. 2016). Class 0 sources exhibit
typically very high accretion and mass-loss rates ( _∼_ 10 _[−]_ [6]

- 10 _[−]_ [7] M _⊙_ yr _[−]_ [1] ) onto the protostar, which could produce high-density jets (5 _−_ 10 _×_ 10 [6] cm _[−]_ [3] ; Ellerbroek
et al. 2013; Lee 2020). The higher transitions of SiO
are the most commonly observed tracer of such highdensity material (Lee et al. 2014; Podio et al. 2015;
Lee et al. 2017a; Podio et al. 2021). While the protostar evolves from Class 0 through Class I and on to the
Class II phase, both the accretion and mass-loss rates
typically decrease. Therefore, SiO should be a better
tracer of jets in the earlier phases of protostars than the
later phases and the detection of SiO emission in jets
more likely indicates protostars in a younger phase and
at a higher mass-loss rate.
Molecular jets with SiO emission have been detected
in many of the Class 0 protostars, e.g., B 335 (Imai
et al. 2019; Bjerkeli et al. 2019), HH 212 (Lee et al.
2017a,b), L1157 (Tafalla et al. 2015; Podio et al. 2016),
HH 211 (Jhan & Lee 2016; Lee et al. 2018), and
IRAS 04166+2706 (Santiago-Garc´ıa et al. 2009; Tafalla
et al. 2017). One Class I multiple system, SVS13A, composed of VLA4A and VLA4B, was also found with SiO
knots (Bachiller et al. 2000; Lef`evre et al. 2017), where
VLA4B is identified as the base of the jet (Lef`evre et al.
2017). In this case, however, the spectral classification
of the components based on infrared observations could
be largely affected by the multiplicity. For example, no

12 Dutta et al.



SiO jet has been previously detected from an isolated
Class I object. On the other hand, SiO jets also have
not been detected in extremely young objects, such as
the candidate first hydrostatic cores (e.g., Per-Bolo 45,
Barnard1b-S, Cha-MM1, CB-17 MMS; see Dutta et al.
2022b, for more details). Recently, the outflow of a very
young object, L1451-mm object, which was previously
believed to be a candidate FHSC, has been detected in
SiO (3-2) emission from a region very close to the source
( _<_ 1000 AU) by Wakelam et al. (2022). Successive knotlike structures in the jet axis are yet to be confirmed
with detections of emission from higher-critical density
tracers like SiO (5-4) and SiO (8-7).
In the ALMASOP sample, most SiO jet sources are in
their Class 0 phase. The source G208.89-20.04Walma is
one of the youngest known objects with a SiO jet (Dutta
et al. 2022b). Nevertheless, G205.46-14.56S3 (see Dutta
et al. 2022a, for more details) and G208.89-20.04E are
two Class I objects from the ALMASOP sample with
SiO molecular jets observed. The objects with SiO jets
exhibit small to high bipolar mass-loss rates ranging
from (0.08 - 5.5) _×_ 10 _[−]_ [6] M _⊙_ yr _[−]_ [1] (including both blue
and redshifted lobes).
These results challenge previous thinking about the
jet launching timescale and sustainability of jets in the
molecular phase. Two-dimensional ideal magnetohydrodynamic (MHD) simulations have showed that the outflow is driven by the first core or isothermal core after the
first collapse (Larson 1969). After a few hundred years,
the central temperature reaches _∼_ 2000 K, and a second
collapse occurs and a rotationally supported Keplerian
disk forms around the protostars (Machida & Hosokawa
2013; Machida & Basu 2019). The high-velocity jets
are believed to be launched from the deep gravitational
potential near this second core (or more plainly the actual protostellar core) with high velocity corresponding
to the escape velocity of the protostars. These jets are
detectable with molecular transitions. Such molecular

jets detected with SiO emission continue up to the end
of their Class 0 life cycle or the early stage of Class I
phase. Then the increased central luminosity in evolved
protostars may photodissociate the molecular jets, but
the density of jets is also decreased due to reduced mass
loss rates. As a result, jets in more evolved protostars
are mostly detected with ionized emission. In the ALMASOP sample, a large fraction of Class 0 protostars do
not exhibit molecular jets (Appendix D and E), these
could be relatively evolved protostars with reduced accretion/ejection activity. Nevertheless, they might have
high-density jet components and be optically thick to
SiO (5-4) and CO (2-1) emission, higher-transition SiO



10 1


10 2


10 3


M obs (M yr 1 )


**Figure** **9.** SiO-to-CO abundance ratios, X _SiO_ /X _CO_ =
N _SiO_ /N _CO_, are plotted as a function of observed jet mass loss
rate ( _M_ [˙] _j_ ). The error bars in the abundance ratios represent
the lower limit since SiO is optically thicker than CO. The
abundance ratios of HH 212 (in red) and HH 211 (in blue) are
calculated from the column densities in the published literature: (HH 212, Lee et al. 2007a) and (HH 211, Jhan & Lee
2021). Asymptotic abundance ratios (grey lines) are adopted
from (Tabone et al. 2020) estimated using the Paris-Durham
shock code designed to model irradiated environments and
a laminar 1D disk wind model. The model considered a

streamline launched at R 0 = 0.15 AU with Temperature =
1000 K in the disk for dust-free models (dust-to-gas mass ratio, Q = 0) and dust-poor models (Q = 6 _×_ 10 _[−]_ [6], 6 _×_ 10 _[−]_ [5]

and 6 _×_ 10 _[−]_ [4] ) as well as for different values of wind mass
loss rates ( _M_ [˙] _w_ ) referring to theoretical models that account
for the origin of jets. The ISM Q ( _∼_ 10 _[−]_ [2] ) is indicated to be
much higher than the present plotting range (green). The
shaded region indicates the location of most of the observed
data.


(e.g, J = 8-7) and CO (e.g., J = 3-2) observations could
confirm the absence of a jet.


4.2. _Jet-driven_ _or_ _wind-driven_ _outflow_


Whether outflowing material is jet or wind-driven is a
long-standing issue with no clear conclusion yet due to
a lack of a statistically significant observational sample. We take the opportunity of the large ALMASOP dataset to explore this question while studying this
unique sample of protostars with high-resolution and
high-sensitivity observations with simultaneous observations of jet and winds (or outflow). In the ALMASOP
sample, we observe four different types of jet and outflow ejection: (i) a narrow CO wind shell but no SiO
jet, (ii) a narrow CO wind shell and a SiO jet, and (iii)
wide-angle CO wind shell but no SiO jet (iv) wide-angle
CO wind shell and a SiO jet. We note that SiO (5-4)
and CO (2-1), both of which could be optically thick
towards the innermost region of the knots, could be de


10 [0]

Episodic Molecular Jets 13



tected with higher density tracers like SiO (8-7) and CO
(3-2).
If we accept that outflow is jet-driven, then the SiO
jets with CO outflow can be straightforwardly explained
(cases _ii_ and _iv_ ). For objects with no SiO jet and narrow CO wind shell (case _i_ ), the outflow could be winddriven. On the other hand, those objects with a wide
angle CO shell and no SiO-jet (case _iii_ ) could be evolved
protostars and their jets could be detected with ionized jet tracers. ALMASOP sample, however, consists
of mostly very young Class 0 systems that should drive
high-density jets which may not have been detected with
the lower transition of SiO and CO (as discussed in section 4.1.2). It is also possible these outflows, indeed, do
not associate with any jet or no strong jet that could
entrain outflow material, which could possibly indicate
that outflows are wind-driven.


4.3. _Origin_ _of_ _gas-phase_ _SiO_


SiO emission has been frequently reported in previous studies as originating in the the shock regions along
protostellar jets in their earliest phases. As discussed
earlier, we observe 21 fields with SiO emission in the
ALMASOP sample (18 in this study, three previously
published in Dutta et al. (2022a,b)). Of these, 16 protostars are confirmed to have SiO emission along the
jet axis. Three other objects display bow-shock-like extended SiO emission along their jet axes, which could
be associated with jets but their small velocity ranges
or insufficient velocity information make it difficult to
be sure. One source exhibits SiO in the collision zone

between two outflows and another the driving source of
SiO emission is unclear. So far, the precise origin of SiO
in the jet is still not constrained due to the lack of significant observations at high resolution and sensitivity.
There are two competing scenarios in the literature describing the mechanism of SiO formation. In the “grainsputtering” scenario, SiO could originate at the shock
region within the jet itself through grain sputtering due
to ion-neutral decoupling (Schilke et al. 1997; Panoglou
et al. 2012). In the “dust-sublimation zone” scenario, if
the jet is launched from the base or within the dust sublimation radius (R sub _∼_ 0.15 au _×_ ~~�~~ _L_ _bol_ _/L_ _⊙_ ; Yvart
et al. 2016), the stellar far-ultraviolet (FUV) emission
there can sublimate the silicate dust grains and release
Si [+] into the gas phase, which later recombines with oxygen to produce SiO. On the other hand, the presence of
FUV excess emission can also lead to the photodissociation of molecules and cause a dramatic decrease in SiO
and CO abundances (Schilke et al. 1997). Tabone et al.
(2020), however, suggest in their laminar dust-free disk
model that if the jet is launched from the dust sublima


tion zone at high temperature ( _>_ 800 K), SiO and CO
could be abundant within the launching material.
Assuming optically thin CO and SiO emission, we
measure the X _SiO_ /X _CO_ for all the SiO emitting jet
sources from the innermost knots (B1 and R1 knots)
and plot thse values as a function of jet mass-loss rate
in Figure 9. We note that SiO (5-4) could be optically
thicker towards the dense shock than CO (2-1) in the
same region. Therefore the SiO emission is likely the
lower limit and the X _SiO_ /X _CO_ is the lower limit in this
case. From our observations, we see that SiO jets tend to
have X _SiO_ /X _CO_ in the range _∼_ 5 _×_ 10 _[−]_ [4] to 10 _[−]_ [2] . We
also plotted two well known Class 0 objects with SiO
jets, HH 211 from Jhan & Lee (2021) and HH212 from
Lee et al. (2007a), for comparison with the ALMASOP
sample. We then compare this sample to the tracks for
different dust-to-gas mass ratios (Q) of Tabone et al.
(2020) (solid curves). We see that all the SiO jets are
possibly dust-poor and hence SiO could have originated
from within the dust sublimation zone of its associated

protostars.
Detectable SiO (5-4) emission within the jet needs
very high-density material, given that transition’s highcriticalSOP sourcesdensityhave(Tablemass-loss1). Theratesmajority _M_ ˙ _j_ _<_ of10 _[−]_ the [6] MALMA- _⊙_ yr _[−]_ [1]

(73% sources within 0.1 - 0.4 _×_ 10 _[−]_ [6] M _⊙_ yr _[−]_ [1] ). Such
small _M_ [˙] _j_ may not create enough dense material to reach
up to the critical density of SiO. Glassgold et al. (1991)
estimated X _SiO_ /X _CO_ _<_ 5 _×_ 10 _[−]_ [9] for a collimated and
accelerated wind and a typical mass-loss rate of M [˙] _j_ _∼_
0.3 _×_ 10 _[−]_ [6] M _⊙_ year _[−]_ [1] (see their Figure 8). From the
ALMASOP sample, we observe SiO-to-CO abundances
X _SiO_ /X _CO_ _∼_ 5 _×_ 10 _[−]_ [4] to 10 _[−]_ [2], which could be much
higher if we consider that SiO is optically thicker than
CO (indicated as the lower limit of error bars in Figure 9). For a typical mass-loss rate of M [˙] _j_ _∼_ 3 _×_ 10 _[−]_ [6]

M _⊙_ year _[−]_ [1], X _SiO_ /X _CO_ could be enhanced to _∼_ 5 _×_
10 _[−]_ [2] (see Figure 6 in Glassgold et al. 1991), then our
observational findings could be compared with that of
the model prediction. One possible explanation for such
high observed SiO abundances than predicted by models is that Glassgold et al. (1991) considered mass-loss
to be spatially extended as a wide ‘wind’. On the other
hand, we estimate the jet mass-loss rate from the innermost part of the outflowing cavity, i.e., along the jet
axis. Hence, the mass-loss rates along the inner jetaxis in this study could have underestimated the actual
mass-loss rates (see Figure 3 offore, our _M_ ˙ _j_ values estimated alongShu et al. 1995the jet axis). There-could
be biased too low to compare accurately with Glassgold
et al. (1991).

14 Dutta et al.



10 [0]


10 1


10 2





10 [0]


10 1


10 2





10 [2]


|b)|Col2|Col3|
|---|---|---|
|b)|||
|b)|||
|b)|||


|(a)|Col2|Col3|Col4|
|---|---|---|---|
|(a)||||



10 [0] 10 [1] 10 [2]


L bol (L )



10 [0] 10 [1]


M Env (M )



**Figure** **10.** (a) Jet velocities (V _j_ ) are plotted as a function of bolometric luminositiy (L _bol_ ) in panel (a) and envelope mass
(Mrate _Env_ ( _M_ ) [˙] _j_ estimated/ _M_ [˙] _acc_ ), wherefrom ACAthe masscontinuumaccretionin panelrates _M_ (b).˙ _acc_ Thewerecolorestimatedbar indicatesfor a protostellarthe ratio betweenmass ofmass0.1 Mejection _⊙_ and ratetotaltoluminosityaccretion
using Equation 6. Objects with increasing trends are marked with ellipse to guide the eye.



10 5


10 6


10 7



10 [0] 10 [1] 10 [2]


L bol (L )





10 [0]


10 1


10 2













10 [0]


10 1


10 2



10 [0] 10 [1]


M Env (M )



**Figure** **11.** (a) Jet mass-loss rates ( _M_ [˙] _j_ ) are plotted as a function of bolometric luminosity (L _bol_ ) in panel (a) and envelope
mass M _Env_ in panel (b). The color bar indicates the ratio between mass-loss rate to accretion rate ( _M_ [˙] _j_ / _M_ [˙] _acc_ ). Stars in panel
(a) are data points for different well-known SiO-jet objects adopted from the literature. The triangles in panel (b) are multiple
sources within a common envelope.



Another possibility to explain the high SiO-to-CO
ratios is that the efficiency of CO production is less
than SiO if the SiO and CO within the jet originate by
the same process. Following Draine & Salpeter (1979);
Nozawa et al. (2006); and Hu et al. (2019), the dust
sputtering time-scale can be defined as


_a_
_t_ _sput_ _≡_ 3 _n_ _H_ _Y_ _tot_ _,_



_−_ 1

_,_
�



( _da/dt_ ) _/n_ _H_ is adopted from Nozawa et al. (2006). For
thermal sputtering, Y _tot_ depends on the temperature of
the region and grain sputtering occurs above _∼_ 10 [5] K.
For non-thermal sputtering, the jet velocity should be
above _∼_ 30 km s _[−]_ [1] . In the jets observed here, the temperatures are much smaller than the thermal sputtering
limit. Non-thermal sputtering, however, could occur at
a high jet velocity. We estimate the typical critical density _n_ _cr,sio_ _∼_ 10 [6] cm _[−]_ [3] is needed to excite SiO in the
shocks (section 1), which could be also considered as
a typical post-shock density in the jet. Therefore, the
pre-shock density is expected to be smaller than n _cr,sio_
along the jet direction, i.e., less than _<_ 10 [6] cm _[−]_ [3] . For
a mean jet velocity of _∼_ 50 km s _[−]_ [1], we estimate sput


_a_
_≈_ 0 _._ 33 _Myr_
� _µm_



�� _cmn_ _H_ _[−]_ [3]



� _−_ 1 � 10 _[−]_ [6] _µmY_ _tot_ _yr_ _[−]_ [1] _cm_ [3]



(5)
where grain size is denoted by _a_ and hydrogen number density of the gas is _n_ _H_ . The erosion rate _Y_ _tot_ _≡_

Episodic Molecular Jets 15



tering time scales of 2.75 - 275 years for silicate dust
and 5.4 - 540 years in the case of carbon dust, for preshock densities _∼_ 10 [6] to 10 [4] cm _[−]_ [3], respectively. So for
high pre-shock density and high-velocity jets, sputtering
is a plausible mechanism to form SiO and CO, even in
the nearest knots with dynamical time scales less than
100 years. The erosion rate of carbonaceous dust grains
(producing CO) is smaller than silicate dust grains (producing SiO) for the same jet velocity (Nozawa et al.
2006). Therefore, equation 5 suggests that the SiO formation time-scale is half that of CO formation for the

same pre-shock density, which could be the reason for
higher SiO to CO ratios in the knots. CO, however, can
easily sublimate from grain mantles at temperatures of
_∼_ 20 _−_ 25 K, where sputtering is not necessary. Therefore, it is unlikely that the majority of the CO is formed
later than SiO.

The dust-sublimation zone scenario is well applicable to the objects with SiO emission in the knots
close to the source (e.g., G205.46-14.56M1, G205.4614.56S1, G205.46-14.56S3, G206.12-15.76, G206.9316.61W2, G208.68-19.20N3, G208.89-20.04E, G208.8920.04Walma, G209.55-19.68S1, G209.55-19.68S2,
G210.37-19.53S, G211-19.27S ~~B~~ G215.87-17.62M). Although the dynamical time scales of the nearest knots
could not be measured due to the poor spatial resolution of our observations, in most cases it is likely
less than 100 years. Such short time scales are long
enough to produce the high X _SiO_ /X _CO_ ratios observed
in this sample, except in case where the preshock density is very high ( _∼_ 10 [6] cm _[−]_ [3] ). As an example, for
G191.90-11.20S (Figure B1f), the jet emitting zone is
uncertain, since the nearest knot (R1) is very faint and
brightest knots (e.g., R2) are far away from the source,
and the grain-sputtering scenario could be a possible
mechanism to form SiO within the jet even for a low
preshock density ( _∼_ 10 _[−]_ [4] cm _[−]_ [3] ). A few other objects
also exhibit SiO emission in the outflow direction such
as G192.32-11.88N, G200.34-10.97N, G205.46-14.56M2,
G209.55-19.68N1. Meanwhile, SiO emission in the field
of G209.55-19.68N1 is clearly in the collision zone between two outflows. The SiO emission in the remaining
three cases could be processed in the location through
grain-sputtering or collision between the outflow material with ambient clouds.

To summarize, we suggest that most of the SiO is originating within the dust sublimation zone near the base
of the source. We can not, however, exclude the grainsputtering mechanism from the present state observations. Further high-sensitivity and high-velocity resolution observations could provide more constrain on the
SiO formation scenario. Such observations could provide



a more stringent view of the nearby knots, and allow
measurement of jet rotation that can in turn constrain
the jet-launching radius (Lee et al. 2017a).


4.4. _Accretion_ _and_ _Ejection_ _Process_


The ejected material along the jet can carry vital information about the present evolutionary status, history
ofprotostar.the accretionThe propertiesprocess, andof thefinaljetmass( _V_ _j,cor_ budget, _M_ ˙ _j_, _L_ of _j,kin_ the,
_T_ knot ) are possibly associated with the driving internal
properties of the protostars and physical structure of
the surrounding materials. In this section, we explore
the inter-correlation of the jet ejection with the intrinsic properties of the protostars and their disks and envelopes.theWetotalestimatedjet mass-lossmass accelerationrates _M_ ˙ _j_, bolometricrates _M_ ˙ acc luminositybased on
_L_ _bol_, the total kinetic luminosity of both the blueshifted
and redshifted lobes _L_ _j,kin_, as presented in the Table 3.
The accretion rate is defined as,


˙
_M_ _acc_ _∼_ [(] _[L]_ _[bol]_ [ +] _[ L]_ _[j,][kin]_ [)] _[R]_ _[∗]_ _M_ _⊙_ _yr_ _[−]_ [1] (6)

_GM_ _∗_


assuming that both the bolometric and kinetic luminosity originate entirely from accretion. For these calculations, we assume a stellar radius of R _∗_ _∼_ 2R _⊙_ (Stahler
1988). The jet-ejecting protostars consists of mostly
Class 0 and two early Class I objects. Therefore, we assume the stellar cores have not evolved much so that

their central objects are in the low mass range of _M_ _∗_
= 0.05 _−_ 0.30 M _⊙_ (Simon et al. 2000; Yen et al. 2017).
Specifically,M _M_ sections,˙ _⊙_ acc for/ _M_ ˙ j allwerangesthewediscussobjectsconsiderfromhow0.003toantheseestimateaverageto 2.1. _M_ ˙ _acc_ _M_ mass˙In _acc_ valuesthe. ofThesubsequentareM _∗_ ratiocorre-= 0.1of
lated with the central driving force of the jet and explore possible implications on the chemical composition
of the disk and planet formation.


4.4.1. _Jet_ _velocity:_ _dependence_ _on_ _luminosity_ _and_ _envelope_

_mass_


Figure 10 shows the jet velocity of the ALMASOP
objects as a function of luminosity in panel (a) and envelope mass in panel (b). In panel (a), most of the objects (marked with ellipse) exhibit a correlation between
_V_ _j,cor_ and _L_ _bol_ . Large error bars of two objects beyond
thecorrelationellipse possiblyzone. _M_ ˙restrict _j_ / _M_ ˙ _acc_ themratio toalsolocatelikelywithindecreasesthe
with bolometric luminosity from _L_ _bol_ _∼_ 0.2 to 10 L _⊙_ .
With increasing luminosity, the protostellar core is expected to be more evolved. Ejection-to-accretion activity will also decrease. Similar correlations of ejection-to

16 Dutta et al.



accretion activity were also reported in Ellerbroek et al.
(2013); and Lee (2020) (see their _M_ [˙] _j_ versus _M_ [˙] _acc_ plots).
In panel (b), most of the _V_ _j,cor_ values are correlate
with the mass of the envelope _M_ _Env_ . A linear fit is
consistent with the equation:


log( _V_ j _,_ cor ) = (0 _._ 21 _±_ 0 _._ 14) log( _M_ Env ) + (2 _._ 0 _±_ 0 _._ 06) _._ (7)


We do not see any clear dependence on _M_ ˙ _j_ / _M_ ˙ _acc_ for
such a correlation. Higher envelope masses may increase
the accretion rates given the larger local mass reservoir.
In addition, larger protostellar masses have higher gravitational potentials from which high-velocity jets are ultimately powered. At evolved protostellar phases, however, the jets become ionized and accretion rates also
decrease, but the jet will be still in high velocity due to
the higher mass of the central protostars. A consistent
measurement of the protostellar masses from kinematics
will be more helpful to illustrate this scenario.


4.4.2. _Jet_ _mass-loss:_ _dependence_ _on_ _luminosity_ _and_
_envelope_ _mass_


Figure 11a shows the observed mass ejection rates _M_ [˙] _j_
as a function of the bolometric luminosity of the objects.
WeSiO comparejet objectsALMASOPfrom the objectsliterature.withThesome _M_ ˙ _j_ well-knownand _M_ ˙ _acc_
of B 335 is comparable to low-luminosity sources. The
objects L 1157, HH 212, HH 211, and L 1448C share similar properties with ALMASOP objects of _L_ _bol_ _∼_ 3 - 10
L _⊙_ . Objects with low _M_ [˙] _j_ / _M_ [˙] _acc_ (bluish colours) exhibit
lowerobjects _M_ [˙] with _j_ rates with increases in central luminosity.high _M_ ˙ _j_ / _M_ ˙ _acc_ (green, yellow, orange, Theand
red colours), however, do not show any obvious correlation.
Figure 11b shows the _M_ ˙ _j_ values as a function of envelope mass, as estimated from the ACA continuum.
Although large scatter in the data points, we see a correlation of jet mass loss rate with envelope mass. Further, we do not see any obvious effect of multiplicity on
the mass accretion and ejection phenomena. A linear fit
reveals a correlation as,


log( _M_ [˙] j ) = (0 _._ 47 _±_ 0 _._ 27) log( _M_ Env ) _−_ (6 _._ 27 _±_ 0 _._ 11) (8)


Therebelow theare fivefitting-linesourceswith(bluelowerdata _M_ points˙ _j_ / _M_ ˙ _acc_ in, Figurethose could11b)
be more evolved sources. The sources above the fittingline mostly exhibit higher _M_ [˙] _j_ / _M_ [˙] _acc_, which could be due
to then being much younger sources with high ejectionto-accretion activity.


4.4.3. _Episodic_ _ejection:_ _dependence_ _on_ _luminosity_ _and_
_envelope_ _mass_



As discussed earlier, all of the SiO jets are discrete
clumpy knot-like or bow-shock-like structures. Some are
roughly equally spaced and may trace a quasi-periodic
ejection. We estimated the mean periods between knots
in the range of _∼_ 20 _−_ 175 years, with the error bars
based on the uncertainties in the inclination angle, jet
velocity, and knot spacing. These discontinuous structures may be produced due to the temporal variations in
the jet velocity and density. Although the mechanisms
that drive the variations in jet density and velocity are
still not well understood, the general consensus is that
they are driven by the quasi-periodic perturbations of
the underlying accretion in the disks. A few potential
mechanisms have been proposed which could produce
variations of accretion. e.g., (Audard et al. 2014; Lee
2020; Fischer et al. 2022): (i) accretion driven by binary
interaction where the variations are modulated by the
orbital timescale; (ii) gravitational instabilities governed
by envelope accretion; (iii) planetesimal accretion onto
the central protostar; and (iv) gravitational instabilities
produced at dust sublimation zones.
In a few cases, episodes have been reported in the
jets of objects such as HH 34 (270 yrs and 1400 yrs;
Raga et al. 2002), HH 111 (60 yrs and 950 yrs; Raga
et al. 2002), and HH 212 (1 yr, 60 yrs and 605 yrs; Zinnecker et al. 1998). Different periods in a single system could be linked to different periodic perturbations
of the underlying accretion in the disk. Further evidence
for short timescales comes from monitoring of protostars at mid-infrared through submm wavelengths. The
JCMT Transient Survey (Herczeg et al. 2017) has uncovered submm brightness variability with what appear
to be decades long timescales from many deeply embedded protostars (Lee et al. 2021) and a curious 18-month
periodicity for one particular source (Lee et al. 2020).
Similarly an analysis of mid-infrared monitoring of over
5000 YSOs by NEOWISE recovered a similar large percentage (20%) of long-term secular variables among the
most deeply embedded members of the sample (Park
et al. 2021).
In our observations with relatively small fields-ofview, we observe mostly single periods or quasi-periodic
knots/bow-shocks. As a result, we estimate only mean
periods of events. The corresponding orbital radii for
those periods can be estimated from Kepler’s third law
of orbital motion following equation:



where _T_ = _T_ knot is the mean episodes of ejection and _M_ _∗_
is the mass of the central protostars, which is assumed to
be 0.05 _−_ 0.30 M _⊙_ . The Keplerian radius corresponding



_GM_ _∗_ _T_ 2
_a_ =
� 4 _π_ [2]



1 _/_ 3 _M_ _∗_

=
� � _M_ _⊙_



� 1 _/_ 3 � _yrT_



2 _/_ 3
_AU,_ (9)
�

Episodic Molecular Jets 17



350 [(][a)]


300


250


200


150


100


50





10 5


10 6



|(b) Single|Col2|Col3|
|---|---|---|
|Single<br>Multiple|||
|Single<br>Multiple|||
|Single<br>Multiple|||


10 [0] 10 [1]

M Env (M )



10 5


10 6



0

|Col1|Col2|
|---|---|
|||
|||

10 [0] 10 [1] 10 [2]

L bol (L )



**Figure** **12.** Mean ejection periods ( _T_ knot ) are plotted as a function of bolometric luminosity (L _bol_ in panel (a) and envelope
masses (M _env_ ) in panel (b). Single and multiple sources are shown in circles and triangles, respectively. The colour scale
indicates the mass-accretion rate ( _M_ [˙] _acc_ ). Straight line panel (b) is the linear fit to the data points.



25


20


15


10



10 5


10 6

















5

|Col1|Col2|Multiple|Col4|Col5|
|---|---|---|---|---|
||||||
||||100<br>101<br>MEnv (M<br>)|100<br>101<br>MEnv (M<br>)|



**Figure** **13.** Keplerian radius corresponding the observed
mean periods of episodic events are plotted as a function of
envelope masses. A stellar mass M _∗_ = 0.1 M _⊙_ is assumed
for all protostars. All the notations are same as Figure 12b.


to the episodes are estimated to be 2.0 _−_ 25 au (including errorbars) for different objects (Table 4). We estimated two sets of radii for two masses. In the absence

of studies on large-scale episodes beyond our fields-ofview and without confirmations of binary components
within those perturbation zones, it is difficult to link
accretion perturbation with any particular mechanism.
Since ALMASOP sample contains mostly Class 0 and
early Class I, most sources are expected to have small
or intermediate disks, and so the perturbation may have
originated within the disk or in the outskirts of the disk.
Further studies of disk size and large scale periodicity
could confirm the origins of the accretion variability.
We plotted _T_ knot as a function of bolometric luminosity or envelope mass in Figure 12a and b, respectively.
Although the data points in Figure 12a exhibit considerable scatter, objects with lower luminosity and lower
mass-loss rates (bluish points) have mostly longer pe


**Figure** **14.** CH3OH icelines (R _CH_ 3 _OH_ ) of the known Hot
Corinos are plotted as function of bolometric luminosity
(L _bol_ . Observed CH 3 OH radius are adopted from (Hsu et al.
2022). The slanting lines indicate iceline radius at 100 K for
luminosity L _bol_ = 1, 10, 70 and 100 L _⊙_, respectively.


riods. The lack of a clear trend with luminosity may
be due to variable accretion. The observed luminosity
could represent the true evolutionary sequence of the
protostars. In Figure 12b there is a mild anti-correlation
between the _T_ knot and M _Env_ . A linear least square fit
provides:


log( _T_ knot ) = ( _−_ 0 _._ 14 _±_ 0 _._ 19) log( _M_ Env ) _−_ (1 _._ 71 _±_ 0 _._ 08) _._
(10)
In Figure 13 the Keplerian perturbation radius corresponding to the periods of ejection is plotted as a function of envelope mass, assuming the same protostellar
mass M _∗_ = 0.1 M _⊙_ . For protostars with lower envelope masses, the perturbation radii tend to be larger.
There are three wide binary systems with separations
_>_ 100 au in the plots. None have separations matching

18 Dutta et al.



the Keplerian perturbation radius. Hence, it is unlikely
these respective accretion/ejection events are driven by
binary orbital dynamics.


4.4.4. _Episodic_ _ejection:_ _Implication_ _to_ _Complex_ _Organic_
_Molecule_ _and_ _Planet_ _formation_


During each episodic outburst, the central luminosity increases to a maximum _L_ _max_ . Subsequently, the
surrounding disk temperatures increase and the various snowlines shift outwards. After each outburst, during the quiescent phase, the luminosity decreases exponentially with time to a minimum _L_ _min_, the surrounding disk temperatures decrease and the snowlines shift
inward. Therefore episodic outbursts affect the variation of temperature within the disk. When the temperature increases, more molecular ices on grains convert to the gas phase, which increases the possibility
of complex molecule formation through gas-phase reactions (Taquet et al. 2016; Lee et al. 2019b; Jørgensen
et al. 2022). During the post-outburst quiescent phase,
gas-phase molecules could recondense to ice. Following
Charnley et al. (2001) and Rodgers & Charnley (2003),
the freeze-out rate for a neutral molecule, _X_, can be

estimated as



envelope at a given luminosity (black line) has been calculated by the equation in Bisschop et al. 2007. Most
of the sources have much larger R _CH_ 3 _OH_ than what is
expected from their current luminosities. The dashed
lines show R(100K) when the luminosity is enhanced by
a certain factor. The R _CH_ 3 _OH_ of many sources is consistent with the enhancement factor of 10. G210WA and

G211S seem to be in their burst phases since R _CH_ 3 _OH_
_∼_ R(100K), and their L _bol_ s are much larger than typical
protostars. The large discrepancy between the methanol
emission size, R _CH_ 3 _OH_ and the R(100) estimated from
the current luminosity suggests that all sources had prior
accretion bursts, and the freeze-out timescale should be
longer than the time interval between episodes.
The NEOWISE photometric data in the Orion clouds
has been extensively detected the variable stars in the
region (Park et al. 2021). A majority of the jets ejecting
objects are observed to be photometric variable.
Since there is growing evidence of grain-growth and
planet formation in the early phase (e.g., Harsono et al.
2018), the emerging planet’s chemical composition, especially in the outer disk, will be largely impacted by
the repetitive outbursts. Evidence of the role of episodic
outbursts on the evolution of disks and chemical composition of planets was also reported for a young Class 0 binary system NGC 1333-IRAS2A (Jørgensen et al. 2022).


4.5. _Correlation_ _between_ _outflow_ _force_ _with_ _luminosity_
_and_ _envelope_ _mass_


Correlations between outflow force _F_ _CO_ and source
properties have long been investigated e.g., with bolometric luminosity and envelope mass (Bontemps et al.
1996). We compare the ALMASOP sample with other
candidate first hydrostatic cores, very low luminosity
Objects (VeLLOs), and known young stars. Figure 15a
shows _F_ _CO_ as a function of _L_ _bol_ . Despite the limiting
values in our estimation, we found that the ALMASOP
sample is located between the well-known Class 0/I sample, and the candidate FHSCs and VeLLOs. Linear fitting to all the young sources provides a correlation:


log( _F_ CO ) = (1 _._ 03 _±_ 0 _._ 09) log( _L_ bol ) _−_ (5 _._ 70 _±_ 0 _._ 15) _._ (12)


Figure 15a contains mostly Class 0 objects with a few
Class I (three from ALMASOP sample) objects. This
slope in Equation 12 is similar to those found in other
independent studies of Class 0 samples from Skretas &
Kristensen (2022) (slope _∼_ 1.02 _±_ 0.26) and Bontemps
et al. (1996) (slope _∼_ 0.90 _±_ 0.15).
Figure 15b shows the outflow force as a function of
envelope mass. A correlation of _F_ _CO_ with _M_ _env_ is seen
for all sources, given by the linear fit equation:


log( _F_ CO ) = (2 _._ 02 _±_ 0 _._ 89) log( _M_ env ) _−_ (5 _._ 20 _±_ 0 _._ 31) _._ (13)



_T_
_λ_ ( _X_ ) = 2 _._ 3 _×_ 10 _[−]_ [18] [�]
_m_ ( _X_ )



0 _._ 5
_n_ _H_ 2 ( _s_ _[−]_ [1] ) (11)
�



To explore variations of chemistry in these systems, we
assume a mean grain radius of 0.1 _µ_ m, and a grain
abundance of 10 _[−]_ [12] at the protostellar envelope outside the hot corino. _T_ is the temperature of the gas in
Kelvin, _m_ ( _X_ ) is the molecular weight of the molecule
_X_, and n _H_ 2 is the molecular hydrogen density in cm _[−]_ [3] .
CH 3 OH is one of the simplest COMs, which could produce CH 3 OCH 3, CH 3 OCHO, C 2 H 5 OCH 3, C 2 H 5 OC 2 H 5,
and C 2 H 5 OCHO through gas-phase reactions (Taquet
et al. 2016). In the case of CH 3 OH, for an approximate
ice-evaporation temperature _T_ _∼_ 100 K and a density of
n _H_ 2 _∼_ 10 [7] cm _[−]_ [3] in the outer disk hot-core boundary region, the freeze-out time scale becomes _∼_ 780 years (710
years for a maximum temperature of 120 K or 930 years
for 70 K evaporation temperature of CH 3 OH). Based
on ejection periods, the outburst time scales of 17 _−_ 530
years for the present ALMASOP objects are less than
the freeze-out time scale. Therefore, each episode of outburst will maintain the outer disk temperature and allow the further formation of complex organic molecules
through gas-phase reactions.
Some of the studied objects have been classified as
“hot corinos” by Hsu et al. (2022) due to detection
of several COMs around them. We have adopted the
CH 3 OH radius from that work and plotted it in Figure 14. The water sublimation radius R(100) in the

Episodic Molecular Jets 19



10 2





10 [0] 10 [1]

|Single (b) ALMASOP<br>Multiple|Col2|Col3|
|---|---|---|
|(b) ALMASOP<br>Single<br>Multiple|||



M env (M )



10 3


10 4


10 5


10 6


10 7


10 8







10 [2]


70


30













L bol (L )



**Figure** **15.** (a) F CO is plotted as a function of L bol . ALMASOP observations are shown in grey square symbols. Blue, green,
brown, and magenta points represent YSOs, VeLLOs, proto-BDs, and candidate FHSCs, respectively. Proto-BDs are also in the
VeLLOs category. These data points have been adopted from Palau et al. (2014); Hsieh et al. (2016); Dutta et al. (2022b). Open
squares indicate single-dish observations. A linear fit of the whole sample (ALMASOP and literature) is shown in the black line.
(b) F _CO_ is shown as a function of M _Env_ . The filled circles are single systems. Tringles indicate binary or other multiple systems.
Colors are for bolometric temperature (T _bol_ ), where T _bol_ _>_ 70 K are condered as Class I objects. The black-filled circles with
red open squares do not have T _bol_ estimation.



This slope is significantly higher than that of Skretas & Kristensen (2022) and Bontemps et al. (1996).
Among four Class I sources ( _T_ _bol_ _>_ 70 K), three show
higher values of _F_ _CO_ than for Class 0 sources of similar
_M_ _env_ . Due to the absence of a significant Class I sample, we can not derive separate correlations for Class 0
and Class I sources. Four multiple sources (three Class 0
and one Class I) exhibit _F_ _CO_ _∼_ (0.4 - 1.1) _×_ 10 _[−]_ [6]

M _⊙_ km s _[−]_ [1] yr _[−]_ [1] . We do not observe any special deviation in the _F_ _CO_ of multiple sources from those of single

sources.


5. SUMMARY


We have analysed 42 outflow fields to investigate protostellar outflows and jets with ALMA observations of
SiO (5-4), CO (2-1), C [18] O, and 1.3 mm continuum.
(i) Observations of SiO emission mostly trace the
dense knots and bow-shock regions within jets. SiO
emission also traces the shocks in the collision zone be
tween two outflows or between outflows and the ambient
cloud. On the other hand, CO emission traces both the
outflow shell and the jet component. The CO emission is less optically thick than SiO within the dense
knots, therefore it is expected to reveal deeper structures within the knots than SiO can.
(ii) To understand the morphologies of the various
outflow or wind components, we fit simple analytical
models assuming a parabolic distribution of the outflow
shell and determined inclination angles from the best
fits. In general, if CO emission is available on both sides



of the velocity axis in the PV diagram, the object is
closer to being seen where the disk is edge-on. When
the CO emission is well separated on both sides of the
velocity axis, i.e., no emission in the positive velocity
quadrant in the blue-shifted lobe or vice versa, then the
object is closer to being seen where the disk is face-on
or alternatively, the outflow is being viewed pole-on.
(iii) A significant fraction of the jets are observed to be
monopolar in SiO emission, with only redshifted components in most cases. We suggest that a specific structure
of knots and shocks is responsible for such monopolar
jets.
(iv) We estimated higher SiO-to-CO abundances in
the knots than predicted in the model by Glassgold et al.
(1991). The knots in the jets are likely dust poor in
general. The knots closest to the YSO are not evolved
enough ( _<_ 100 years) to produce SiO rich jets. Therefore, the SiO emission could originate in the base of the
source or within the dust sublimation zone.
(v) From our limited sample, we do not observe any
clear correlation between the jet velocities and internal
luminosity. Objects with lower _M_ [˙] _j_ / _M_ [˙] _acc_, however, ratio
tend to have smaller jet velocities. Furthermore, there
isrounding(v)a clearMassenvelopecorrelationloss ratesmasses,between _M_ ˙ _j_ doirrespectivenotthe showjet velocitiesofany _M_ ˙ clear _j_ / _M_ and˙ _acc_ corre-.surlation with L _bol_ . In most cases, objects of higher luminosity and smaller _M_ [˙] _j_ / _M_ [˙] _acc_ tend to exhibit smaller _M_ [˙] _j_ .
As with jet velocity, _M_ [˙] _j_ is clearly correlated with M _env_ .

20 Dutta et al.



(vi) The episodes of knots do not show any clear dependencenosity sourceson Ltend _bol_ . Into havemost lowercases, _M_ ˙however, _j_ / _M_ ˙ _acc_ andlowlongerlumiperiods. Episodes are explicitly anti-correlated with the
M _Env_, which could be due to some underlying mechanism that slows down YSO rotation by the envelope

masses.
(vii) Episodes are usually more frequent than the
freeze-out time scales of complex organic molecules.
Episodic ejection could significantly impact the gas-ice
balance in the disk. Therefore, it will affect the COM



formation within the disk and likely the chemical compositions of the forming planets.
(viii) Outflow forces for different types of protostars
and candidate FHSCs are correlated with the bolometric

luminosity and envelope masses.
More detailed studies are needed with high-resolution
and high-sensitivity multiwavelength observations (e.g.,
in sub-millimetre with ALMA and infrared with JWST)
to characterize the ice features and disk-jet connection.
Such studies would allow a more precise investigation of
the direct/indirect effect of jets on the COMs and planet
formation.

Episodic Molecular Jets 21

22 Dutta et al.

Episodic Molecular Jets 23

24 Dutta et al.

Episodic Molecular Jets 25

26 Dutta et al.

Episodic Molecular Jets 27



**Table** **4.** Perturbed (Keplerian) radius in the
disk-plane for the knots in the jet


~~Source~~ ~~Keplerian~~ ~~Radius~~ ~~(AU)~~
(0.05 M _⊙_ ) (0.30 M _⊙_ )


G191.90-11.21S 7.9 [+3] _−_ 5 _[.]_ _._ [0] 2 14.4 [+5] _−_ 9 _[.]_ _._ [4] 5
G203.21-11.20W2 6.3 [+1] _−_ 1 _[.]_ _._ [1] 2 11.5 [+2] _−_ 2 _[.]_ _._ [1] 2
G205.46-14.56M1 7.9 [+2] _−_ 3 _[.]_ _._ [5] 1 14.4 [+4] _−_ 5 _[.]_ _._ [5] 7
G205.46-14.56S1 3.9 [+8] _−_ 1 _[.]_ _._ [9] 4 7.0 [+16] _−_ 2 _._ 6 _[.]_ [2]
G205.46-14.56S3 5.3 [+1] _−_ 1 _[.]_ _._ [8] 4 9.6 [+3] _−_ 2 _[.]_ _._ [3] 5
G206.12-15.76 3.6 [+2] _−_ 0 _[.]_ _._ [4] 8 6.5 [+4] _−_ 1 _[.]_ _._ [4] 5
G206.93-16.61W2 2.4 [+2] _−_ 1 _[.]_ _._ [4] 1 4.4 [+4] _−_ 2 _[.]_ _._ [3] 0
G208.68-19.20N3 6.9 [+2] _−_ 2 _[.]_ _._ [9] 4 12.5 [+5] _−_ 4 _[.]_ _._ [3] 4
G208.89-20.04E 5.1 [+5] _−_ 1 _[.]_ _._ [5] 9 9.3 [+10] _−_ 3 _._ 5 _[.]_ [1]
G208.89-20.04Walma 11.6 [+6] _−_ 7 _[.]_ _._ [9] 6 21.0 [+12] _−_ 13 _[.]_ _._ [5] 9
G209.55-19.68S2 2.9 [+1] _−_ 0 _[.]_ _._ [0] 6 5.3 [+1] _−_ 1 _[.]_ _._ [9] 0
G210.37-19.53S 3.0 [+1] _−_ 0 _[.]_ _._ [4] 9 5.4 [+2] _−_ 1 _[.]_ _._ [5] 7
G210.49-19.79W 6.7 [+4] _−_ 1 _[.]_ _._ [0] 0 12.2 [+7] _−_ 1 _[.]_ _._ [2] 7
G215.87-17.62M 6.0 [+1] _−_ 1 _[.]_ _._ [7] 6 10.9 [+3] _−_ 3 _[.]_ _._ [1] 0



_Facility:_ ALMA


_Software:_ Astropy (Astropy Collaboration et al.
2013), APLpy (Robitaille & Bressert 2012), Matplotlib
(Hunter 2007), CASA (McMullin et al. 2007)


APPENDIX



A. INCLINATION ANGLE FROM CO OUTFLOW SHELL


The molecular CO outflow shell is assumed to be a radially expanding parabolic shell generated by the underlying
wide-angle wind. By following the simple analytical model proposed by Lee et al. (2000), the inclination angle ( _i_ ) of
the sources in the plane-of-sky can be derived from the physical structure of the wind/outflow shell as observed in
CO emission. Figure A1a provides a schematic diagram that depicts the integrated outflow emission (here, CO zeroth
moment map). The outflow system lies in the _xyz_ plane, which is inclined at an angle _i_ to the plane-of-sky plane,
_x_ _[′]_ _y_ _[′]_ _z_ _[′]_ . The outflow shells could be expressed in a cylindrical coordinate system:


_z_ = _cR_ [2] (A1)


, where _R_ (= � _x_ [2] + _y_ [2] ) denotes the radial distance of the shell from the outflow axis _z_, and _c_ is the curvature of the
parabola near the origin of the outflow or launching zone. The transformations between the two coordinate systems
are _x_ = _x_ _[′]_, _y_ _[′]_ = _y_ cos _i_ + _z_ sin _i_, _z_ _[′]_ = _z_ cos _i −_ _y_ sin _i_ . For a radially expanding shell with a velocity proportional to the
radial distance _v_ _R_ = _R/t_ 0, where _t_ 0 is the dynamical time of expansion. In the case of only expansion, the observed
velocity ( _v_ _obs_ ) in the sky with a coordinate system ( _x_ _[′]_, _z_ _[′]_ ) can be expressed as _y_ _[′]_ = _−v_ _obs_ _t_ 0 . By substituting these
values into equation A1, we obtain:


_z_ _[′]_ cos _i −_ _v_ _obs_ _t_ 0 sin _i_ = _c_ [ _x_ _[′]_ [2] + ( _−v_ _obs_ _t_ 0 cos _i −_ _z_ _[′]_ sin _i_ ) [2] ] (A2)


In a narrow position-velocity (PV) cut along the jet-axis, _y_ _[′]_ (velocity) and _z_ _[′]_ (position) become the variables and,
the emission along _x_ _[′]_ (or x) is essentially zero. The schematic diagram in Figure A1b displays a PV diagram with an
outflow shell and jet (knots). Under these conditions, equation A2 simplifies to:


_z_ _[′]_ cos _i −_ _v_ _obs_ _t_ 0 sin _i_ = _c_ [( _−v_ _obs_ _t_ 0 cos _i −_ _z_ _[′]_ sin _i_ ) [2] ] (A3)


The curvature _c_ is determined from fitting to the integrated emission (zeroth moment) maps (see equation A1). By
varying _i_ and _t_ 0 we can obtain a parabolic fit of the PV diagram.
For the observed set of velocity (v _[′]_ ) and distance along the flow axis (l _[′]_ ) the inclination correction terms are v =
v _[′]_ /sin _i_, l = l _[′]_ /cos _i_ .

28 Dutta et al.













**Figure** **A1.** (a) Schematic Diagram of outflow-jet system. The system lies in the _xyz_ plane, which is inclined at an angle _i_
to the plane-of-sky plane, _x_ _[′]_ _y_ _[′]_ _z_ _[′]_ . The blue color indicates the blue-shifted lobe and the red color indicates red-shifted lobe. (b)
PV diagram along the flow axis of panel- _a_ . The blue-shifted outflow shell and knots are depicted in blue, while the red-shifted
outflow shell and knots are depicted in red. The system is inclined at an angle _i_ along the _z_ _[′]_ position axis. The typical velocities
of the knots are represented by red and blue circular patches. These assume that all knots are equidistant and have equal
velocities in one case study.


B. OBJECTS WITH CONFIRMED MOLECULAR JET


B.1. _G191.90-11.20S_


Figure B1 presents the low-resolution ACA 1.33 mm continuum map (panel _a_ ), high-resolution C [18] O spectra (panel
_b_ ), CO map integrated over the whole velocity dispersion (panel _c_ ), position-velocity (PV) of CO along flow-axis
(panel _d_ ), SiO map integrated over whole velocity dispersion (panel _e_ ), and SiO PV diagram cut along flow axis of
G191.90 _−_ 11.20S. The observed object is a Class 0 _−_ I transition protostar with T _bol_ _∼_ 69 _±_ 17 K and L _bol_ _∼_ 0.4 _±_ 0 _._ 2
L _⊙_ . It has an envelope mass of the _∼_ 0.51 _±_ 0.1 M _⊙_ .
The protostar drives a CO outflow with a well-defined cavity wall and dense jet along the flow axis detected with
both SiO and CO. The source is nearly edge-on (i _∼_ 7 [+8] _−_ 3 [degree).] [The] [velocity] [dispersion] [of] [CO] [emission] [and] [SiO]
emission is nearly identical. A mean jet velocity V _j_ = 6 _±_ 3 km s _[−]_ [1] was observed. Due to the edge-on orientation, the
jet velocity appears small. The nearest knot at the redshifted lobe ( _R_ 1) is faint. The brightest knot at _R_ 2 resembles
a bow-shock kind of structure. The other two redshifted knots ( _R_ 3 and _R_ 4) do not show a dense structure, but closer
inspection of the SiO PV diagram confirms the presence of separate knots. The SiO emission is primarily observed in
the redshifted lobe. Only one faint SiO knot (B1) was detected in the blue-shifted lobe positioned 10 _−_ 12 _[′′]_ ( _∼_ 4000
_−_ 4800 AU) away from the central source. The mean episodic intervals were estimated to be _T_ _knot_ _∼_ 140 [+167] _−_ 60 [years,]
corresponding to a Keplerian radius in the range _∼_ 7.0 to 30 AU (including estimated error) for a mass range of 0.05
to 0.30 M _⊙_ . Therefore, the instabilities causing episodic accretion and ejection possibly originated in the disk or its

Episodic Molecular Jets 29


˙ ˙
outskirts. The objects exhibit a very high _M_ _j_ / _M_ _acc_ ratio of _∼_ 2.1, indicating it is a highly active ejection/accretion
object.


B.2. _G205.46-14.56M1_ _(HOPS_ _317)_


The observations of the continuum, C [18] O, CO, and SiO emissions for G205.46 _−_ 14.56M1 are shown in Figure B2,
following the same order as in Figure B1. The system comprises two sources, A and B, separated by _∼_ 6.14 _[′′]_ ( _∼_ 2460
AU). Source ‘A’ aligns with the position of HOPS 317 (Tobin et al. 2020), a Class 0 object with T _bol_ _∼_ 47 _±_ 12 K, L _bol_
_∼_ 4.8 _±_ 2.1 L _⊙_ . This binary system possesses a combined envelope mass M _env_ _∼_ 5.77 _±_ 0.88 M _⊙_ . G205.46-14.56M1 ~~B~~,
brighter in 1.3 mm continuum is located at the envelope’s center.
Source G205.46-14.56M1 ~~A~~ exhibits a small north-east outflow lobe, with the south-western lobe potentially blended
with the outflow from G205.46-14.56M1 ~~B~~ . However, from our current velocity resolution, we were unable to confirm
the presence of an outflow from G205.46-14.56M1 ~~B~~ or discern between the outflow components of the sources. The
presence of episodic shells in the blue-shifted lobe similar to the episodic Wide-angle Outflow of HH 46/47 (Zhang et al.
2019), is a possibility. When calculating F _CO_ from the south-west lobe of G205.46-14.56M1 ~~A~~, we consider all the
observed CO emissions from the lobe. The southern component (blueshifted lobe) of the source G205.46-14.56M1 ~~_A_~~
reveals a single SiO knot ( _B_ 1), which is corroborated by CO emission. A CO knot-like structure ( _R_ 1?) is visible in
the redshifted lobe, although it is undetected in SiO emission. The mean jet velocity derived from peak SiO emission
is V _j_ _∼_ 88 _±_ 10 km s _[−]_ [1] . With an inclination of i _∼_ 75 [+5] _−_ 15 [degrees,] [the] [source] [is] [closer] [to] [face-on] [orientation.] [The]
mean episodic intervals of the nearest knots are approximately _T_ _knot_ _∼_ 100 [+50] _−_ 53 [years,] [yielding] [a] [Keplerian] [radius] [of]
perturbation between˙ ˙ _∼_ 4 to 18 AU. The objects exhibit significant accretion/ejection phenomena, as indicated by the
high _M_ _j_ / _M_ _acc_ ratio of _∼_ 0.67.


B.3. _G205.46-14.56S1_ _(HOPS_ _358)_


Various components of the observations of G205.46-14.56S1 are displayed in Figure B3 following the same sequence
as in Figure B1. This system comprises a wide binary with a separation of 13.37 _[′′]_ ( _∼_ 5349 AU). Source G205.4614.56S1 A drives a nearly north-south outflow and jet, while the outflow of G205.46-14.56S1 ~~B~~ is blended with the
redshifted lobe (southern lobe) of G205.46-14.56S1 ~~A~~ . In this paper, we discuss the outflow of G205.46-14.56S1 ~~A~~,
which is identified as HOPS 358 in Tobin et al. (2020). It is a Class 0 source with T _bol_ = 44 _±_ 19, L _bol_ = 22 _±_ 8 L _⊙_, and
the envelope mass of G205.46-14.56S1 ~~A~~ is 0.88 _±_ 0.14 M _⊙_ .
The outflow from G205.46-14.56S1 ~~A~~ demonstrates a narrow inner section and a suddenly widening outflow lobe.
The thick envelope likely suppresses the outflow opening near the source, allowing it to abruptly expand beyond the
envelope. The CO outflow kinematics suggest that the object is nearly edge-on with an inclination _i_ _∼_ 5 [+5] _−_ 4 [degrees.]
Notably, the source exhibits strong SiO emission in the southern (redshifted) lobe, whereas the northern (blueshifted)
lobe only has faint SiO emission near the source, resembling a monopolar SiO jet. Owing to edge-on orientation the
observed mean V _j_ is quite small _∼_ 1.4 _±_ 4.0. The error bar indicates the jet velocity could become negative, implying
the redshifted lobe might transform into a blueshifted one, and due to edge-on view, the redshifted and blueshifted
velocities could be reliably defined. Several knots are detected in the southern part (R1, R2, ..... R14). Here, it is
important to note that knots are identified based on peak emission, and we were unable to determine whether they form
part of the forward and backward components of a single bow shock. The average episodic intervals of the knots knots
were estimated to be _T_ _knot_ _∼_ 170 [+163] _−_ 136 [years,] [which] [corresponds] [to] [a] [Keplerian] [radius] [ranging] [from] _[∼]_ [5.0] [to] [31] [AU]
(including estimated error, for a mass range of 0.05 to 0.30 M _⊙_ ). The objects exhibit intermediate accretion/ejection
phenomena ( _M_ [˙] _j_ / _M_ [˙] _acc_ _∼_ 0.09).


B.4. _G206.12-15.76_ _(HOPS_ _400)_


Figure B4 shows different components of the G206.12-15.76 system following the same order as Figure B1. This
system, HOPS 400 Karnath et al. (2020); Tobin et al. (2020), is a close binary, although our observed resolution and
sensitivity were not sufficient to resolve the two components. It is a Class 0 system with T _bol_ = 35 _±_ 9 K and L _bol_ =
3.0 _±_ 1.4 L _⊙_ . The combined envelope mass was estimated at M _env_ _∼_ 2.44 _±_ 0.37 M _⊙_ .
The length of the CO outflow is relatively small (L _red_ _∼_ 16 _[′′]_ _._ 0 _≡_ 6400 AU; L _blue_ _∼_ 10 _[′′]_ _._ 0 _≡_ 4000 AU). Both the CO
and SiO emission have a similar range of velocity dispersion, making it difficult to distinguish outflow shells from jet
components. Assuming low-velocity CO emission is solely a wind/outflow component, we estimated the inclination
angle to be _i ∼_ 15 [+20] _−_ 5 [degrees.] [Both SiO and CO exhibit high- and low-velocity components.] [A few knots are identified]

30 Dutta et al.


along the jet axis. From the high-velocity knots, the mean observed jet velocity is estimated as V _j_ _∼_ 40 _±_ 15 km s _[−]_ [1] .
The mean episodes of the knots are _T_ _knot_ _∼_ 30 [+35] _−_ 10 [years,] [corresponding] [to] [a] [Keplerian] [radius] [of] [perturbation] [zone]
between 3 _−_ 11 AU (including estimated error, for a mass range of 0.05 to 0.30 M _⊙_ ). This object exhibits intermediate
ejection phenomena relative to accretion with _M_ [˙] _j_ / _M_ [˙] _acc_ _∼_ 0.3. The object could be at a very young phase of protostellar
evolution with a dynamical age of _T_ _DynAge,blue_ _∼_ 203 [+329] _−_ 70 years for the blueshifted lobe and _T_ _DynAge,red_ _∼_ 127 [+205] _−_ 44
years for the redshifted lobe (Both estimated ages corrected for inclination angle). Thus, we suggest this system to be
less than 1000 years of old, as a conservative estimate.


B.5. _G208.68-19.20N3_


The details of different observed components are shown in Figure B5 in the same order of Figure B1. There are
three sources in the field, suggesting the presence of a multiple system. The source G208.68-19.20N3 ~~A~~ is located
at _∼_ 16 _[′′]_ away from the close binary system (G208.68-19.20N3 ~~B~~ and G208.68-19.20N3 ~~C~~ ). In this paper, we focus
on the outflow/jet of G208.68-19.20N3 ~~A~~ . Neither T _bol_ nor L _bol_ for this source are available in the literature. The
envelope mass of the object is estimated to be M _env_ _∼_ 2.08 _±_ 0.34 M _⊙_ . The location of G208.68-19.20N3 ~~B~~ and
G208.68-19.20N3 ~~C~~ align with HOPS 92. The outflows of this close binary system are blended together and situated
on the edge of primary beam, thus, we exclude this source from our study.
The velocity dispersion of SiO and CO are nearly identical. Based on the position-velocity diagrams, it is challenging
to differentiate between wind/outflow and jet components, leading to a poor fit of the parabola to the CO shell. We
assumed that the majority of low-velocity components originate from the wind, and are likely wind components. The
inclination angle is measured to be _i ∼_ 35 [+15] _−_ 15 [degrees.] [The mean jet velocity is V] _[j]_ _[∼]_ [35] _[±]_ [15.] [There are a few knot-like]
structures appearing in both the outflow lobes. Although ‘R1’ appears to be double-headed, it does not present itself
as˙ a single knot with a bow-shock structure in the PV diagrams. The system exhibits a high total mass loss rate of
_M_ _j_ _∼_ 1.3 _×_ 10 _[−]_ [6] M _⊙_ yr _[−]_ [1] . The mean ejection episodes were estimated to be _T_ _knot_ _∼_ 137 [+56] _−_ 39 [years,] [corresponding] [to]
a perturbation zone of Keplerian radius _∼_ 4.5 _−_ 18 AU. The dynamical age of the blueshifted lobe is _T_ _DynAge,blue_ _∼_
228 [+160] _−_ 110 [years] [and] _[T]_ _[DynAge,red]_ _[∼]_ [190] _−_ [+133] 91 years for the redshifted lobe, with both adjusted for the inclination angle.
We propose that the system is less than 1000 years old (a conservative estimate). The smaller dynamical age, higher
jet mass ejection rate, and presence of an SiO jet indicate that the source is in an extremely young phase of protostellar
evolution.


B.6. _G208.89-20.04E_


The details of continuum and emission components of the G208.89-20.04E system are depicted in Figure B6, and
arranged similarly to Figure B1. It is a Class I system having T _bol_ _∼_ 108 _±_ 25 K and L _bol_ _∼_ 2.2 _±_ 1.0 L _⊙_ . The envelope
mass of the source is M _env_ _∼_ 0.28 _±_ 0.06 M _⊙_ . The elliptical structure of the inner part of the continuum emission, and
a small extension along one side (western part) as compared to the other (north-east and eastern part), suggest that
this object could be a highly inclined system.
The structure of the CO outflow is complex and irregularly shaped. The redshifted lobe (south-western) appears
wider than the blueshifted (north-east) lobe. The redshifted lobe is possibly attached to an ambient cloud or outflow
of an unknown source. The redshifted lobe is smaller than the blueshifted lobe, but scattered emission is noticeable
along the redshifted lobe in both CO and SiO emissions. PV diagrams with CO and SiO indicate that the source is
likely nearly edge-on. We measured the inclination angle to be _i_ _∼_ 10 [+10] _−_ 5 [degrees.] [Due] [to] [its] [edge-on] [orientation,] [the]
blueshifted and redshifted wind/outflow components are difficult to distinguish. Based on the peak emission of CO
and SiO, we defined the blue and redshifted velocity components. We estimated the mean jet velocity to be V _j_ _∼_
2.0 _±_ 2.0 km s _[−]_ [1] (negative error bar leads to zero velocity, indicating a fully edge-on orientation). Different knots are
identified from the SiO emission with mean episodes of _T_ _knot_ _∼_ 523 [+557] _−_ 263 [years.] [The] [Keplerian] [radius] [for] [a] [potential]
perturbation zone is _∼_ 15 - 70 AU, which is a slightly larger range than that of Class 0 sources.
The ALMASOP sample includes two Class I molecular jets with SiO emission along the flow axis. One Class I
source, G205.46-14.56S3, was reported with very high-velocity SiO emission (Dutta et al. 2022a). Another molecular
jet detected with SiO emission is the G208.89-20.04E source. This is a Class I source, or could be in the transition
phase from Class 0 to Class I. The jet velocity for this source is very low, potentially due to its edge-on orientation.


B.7. _G209.55-19.68S1_ _(HOPS_ _11)_


The details of different continuum and emission components of G209.55-19.68S1 are illustrated in Figure B7, following
the same order as Figure B1. This source coincides with the HOPS 11 source (Tobin et al. 2020) and has T _bol_ _∼_ 50 _±_ 15

Episodic Molecular Jets 31


K and L _bol_ _∼_ 9.1 _±_ 3.6 L _⊙_ . The mass of the envelope is estimated to be M _env_ _∼_ 1.09 _±_ 0.17 M _⊙_ . The 1.33 mm emission is
extended along the outflow direction, potentially implying that there is entrained envelope material along the outflow
wall driven by the outflow.
The CO outflow’s northern part (redshifted lobe) bends towards the north-west from the flow axis, and the southern
outflow CO emission appears very wide. The CO and SiO PV diagrams along the flow axis suggest that the source
is not an edge-on object. The outflow shells are challenging to distinguish for this source, so the exact fitting is not
shown. A tentative fitting to the blueshifted lobe of the CO outflow shells suggests an inclination angle _i_ _∼_ 45 [+15] _−_ 15
degrees. A few SiO knots were observed along the flow axis, and the mean jet velocities are estimated to be V _j_ _∼_ 27 _±_ 8
km s _[−]_ [1] . The mean ejection periods are _T_ _knot_ _∼_ 300 [+125] _−_ 80 years, corresponding to a perturbation˙ ˙ zone at a Keplerian
radius of _∼_ 13 - 38 AU (including error bars). The objects exhibit a smaller ratio of _M_ _j_ / _M_ _acc_ _∼_ 0.03, indicating that
it could be at a relatively evolved phase of protostellar evolution. Due to the unreliable inclination measurement, this
source is not included in the statistical analyses in the main text.


B.8. _G209.55-19.68S2_ _(HOPS_ _10)_


The continuum and different emission components of G209.55-19.68S2 are displayed in Figure B8 in the same order
as Figure B1. The object’s location coincides with HOPS 10 (Tobin et al. 2020). The source has a T _bol_ _∼_ 48 _±_ 11 K
and a L _bol_ _∼_ 3.4 _±_ 1.4 L _⊙_ . The envelope mass is estimated to be M _env_ _∼_ 0.61 _±_ 0.12 M _⊙_ . The peak of the continuum is
shifted towards north-east from the envelope’s centre. Such continuum emission could be due to an edge-on orientation
of the object.
The wind/outflow component in CO emission is well separated from the high-velocity jet component. The object
exhibits a redshifted monopolar jet, detectable with both SiO and CO, making it one of the most beautiful highvelocity monopolar jets discovered to date. The inclination angle is measured to be _i_ _∼_ 15 [+15] _−_ 5 [degree.] [The] [observed]
jet velocity is V _j_ _∼_ 50 _±_ 5 km s _[−]_ [1] . Several knots are detected in the redshifted lobe, with ejection episodes estimated
to be _T_ _knot_ _∼_ 16 [+19] _−_ 6 [years.] [This] [corresponds] [to] [a] [perturbation] [zone] [at] [a] [Keplerian] [radius] _[∼]_ [1.7] [-] [7.2] [AU.]


B.9. _G210.37-19.53S_ _(HOPS_ _164)_


Figure B9 shows the continuum, C [18] O spectra, integrated CO and SiO maps, and PV diagrams of G210.37-19.53S
in the same order as Figure B1. This source has T _bol_ _∼_ 39 _±_ 10 K and L _bol_ _∼_ 0.6 _±_ 0.3 L _⊙_, making it one of the very low
luminosity objects. The location of this object matches with HOPS 164 (Tobin et al. 2020). The surrounding envelope
mass is estimated to be _∼_ M _env_ _∼_ 0.54 _±_ 0.08 M _⊙_ .
The SiO knots are considered to delineate the jet axis or flow axis. The CO emission is asymmetrically distributed
on both sides of the flow axis. We calculated an inclination angle of _i_ _∼_ 25 [+15] _−_ 10 [degrees.] [Several] [knots] [are] [detected]
from integrated maps and PV diagrams of SiO and CO, close to the source on both the blueshifted ( _R_ 1, _R_ 2, _R_ 3)
and redshifted ( _B_ 1, _B_ 2, _B_ 3) lobes. Knots _R_ 1, _R_ 2 and _R_ 3 appear to represent different components of bow shock
(forward shock, backward shock) in a single knot from the SiO PV diagram, even though integrated maps do not
present a bow shock-like appearance. Given the present sensitivity and velocity resolution of our observations, it is
difficult to determine whether it is really a single knot or three different knots. We estimated a mean velocity of V _j_ _∼_
36 _±_ 5 km s _[−]_ [1] . The mean episode of the ejection events is _T_ _knot_ _∼_ 23 [+18] _−_ 10 [years.] [The] [perturbation] [zone] [for] [the] [episodic]
accretion could be at a Keplerian radius of _∼_ 2 - 8 AU. The relatively higher ratio of _M_ [˙] _j_ / _M_ [˙] _acc_ _∼_ 0.3 exhibited by this
object indicates that it might be at a relatively younger phase of protostellar evolution.


B.10. _G210.49-19.79W_ _(HOPS_ _168)_


Figure B10 shows various components of the continuum and emission in the same order as Figure B1. High-resolution
maps ( _∼_ 140 AU) reveal two continuum peaks, G210.49-19.79W ~~A~~ and G210.49-19.79W ~~B~~ (Dutta et al. 2020). The
fainter continuum peak of G210.49-19.79W ~~B~~ is yet to be confirmed as a protostar. The location of G210.49-19.79W ~~A~~
coincides with HOPS 168 (Tobin et al. 2020). It has a T _bol_ _∼_ 51 _±_ 20 K and a L _bol_ _∼_ 60 _±_ 24 L _⊙_ . The envelope mass is
calculated to be M _env_ _∼_ 1.4 _±_ 0.35 M _⊙_ . The envelope material is possibly entrained by an outflow and extends towards
the southwest along the boundary wall of the redshifted outflow. The inclination angle is measured to be _i_ _∼_ 45 [+10] _−_ 10
degrees from the outermost CO shell.
A close look at the CO emission near the source suggests a twisted CO shell at its base. The SiO emission does not
align along a particular axis (as marked in the SiO integrated map). One SiO knot is observed in the north-east of the
jet axis in the blue-shifted lobe. In the redshifted lobe, one SiO knot close to the source appears to be shifted to the

32 Dutta et al.


southwest. All SiO knots form an ‘S’-shaped structure, possibly due to wiggling of the jet. Similar wiggling structures
have also been reported in molecular jets from other protostars, such as HH 211 in (Lee et al. 2010; Moraghan et al.
2016). We measure the mean jet velocity _V_ _j_ _∼_ 5 _±_ 4 km s _[−]_ [1] (V _j,cor_ _∼_ _V_ _j_ /sin _i_ ). This small velocity range is not in
agreement with the SiO emission in the jet if we consider a dust-sputtering scenario. SiO emission is plausible if it
originates at the dust sublimation zone. Otherwise, there could be an undetected close binary with two jets originating
at two different position angles.
Another possible explanation could be the scenario of episodic CO shells and SiO knots launched at different times,
as in the case of the episodic wide-angle outflow in HH 46/47 (Zhang et al. 2019). The CO PV diagram in Figure B10d
and f also hints at such episodic shell occurrences (marked with thicker blue and red curves in CO PV diagram). Now
consider a cloud core contracting along the magnetic field lines toward the midplane (equatorial plane) and forming
a flattened envelope or pseudo-disk. In this scenario, the flattened envelope is warped because of the contraction
direction of the cloud core and thus the minor axis of the flattened envelope is changed gradually from parallel to
the magnetic field axis in the outer region to parallel to the rotation axis in the inner region (Hirano & Machida
2019; Lee et al. 2019a). Therefore, the position angle of the jet axis is also expected to be rotated according to the
rotation direction of the disk. The SiO jet could be launched at different orientations of the jet at different timescales.
Then the inclination angle measured above could not be a true value from a single outermost CO shell but rather a
combination of multiple episodic shells. The orientation ( _i_ ) of those shells could be much smaller (towards the edge-on)
than estimated above. Considering the inclination angle and estimated jet velocities of other jets in our ALMASOP
sample, we assume an inclination angle of _i_ _∼_ 10 [+10] _−_ 9 [degrees] [for] [this] [object.] [We] [recommend] [further] [investigation] [of]
this source with higher-angular, higher-velocity resolution, and higher-sensitivity observations to better understand its

true nature.


B.11. _G215.87-17.62M_


Figure B11 shows the continuum and different components of emissions for G215.87-17.62M in the same order as
Figure B1. Currently, there are no available measurements of T _bol_ and L _bol_ for this source in the literature. The
envelope mass is estimated to be M _env_ _∼_ 0.3 _±_ 0.07 M _⊙_ . The 1.3 mm continuum is extended along the north-east
to south-west direction, possibly representing the entrained material along the outflow cavity wall. However, the
continuum emission is extended beyond the length of the outflow/jet, thus it is not clear whether the entirety of the
extended continuum emission is due to the entrained material or if there is some other mechanism involved.

The CO and SiO velocity dispersion and spatial extensions are relatively similar. From position-velocity diagrams,
it is difficult to separately identify the wind/outflow and jet components. Assuming that most of the low-velocity
material is from wind/outflow shell, the inclination angle is estimated to be _i_ _∼_ 30 [+10] _−_ 10 [degree.] [The] [SiO] [emission] [is]
extended from low velocity to high velocity, making it difficult to measure the jet velocity. The mean jet velocity is
V _j_ _∼_ 30 _±_ ˙10 km s _[−]_ [1] . A few knot-like structures appear in both the outflow lobes. It exhibits a relatively low mass
loss rate _M_ _j_ _∼_ 3.2 _×_ 10 _[−]_ [7] M _⊙_ yr _[−]_ [1] . The mean episodes of the ejection are _T_ _knot_ _∼_ 66 [+30] _−_ 25 [years,] [corresponding] [to] [a]
perturbation zone of Keplerian radius _∼_ 4.5 _−_ 14 AU. The dynamical age of blueshifted lobe is _T_ _DynAge,blue_ _∼_ 219 [+99] _−_ 81
years, and for redshifted lobe it is _T_ _DynAge,red_ _∼_ 292 [+133] _−_ 108 [years,] [each] [corrected] [for] [inclination] [angle.] [We] [estimate]
that this system is less than 1000 years old, a conservative value. A smaller spatial extension, smaller dynamical age,
lower jet mass ejection rate, and presence of a brighter SiO jet suggest that this source could be a very low-mass and
low-luminosity object in an extremely early stage of protostellar evolution.


C. OBJECTS WITH COMPLEX SIO EMISSION MORPHOLOGY AND NOT CONSIDERED FOR JET

PARAMETER ESTIMATION


C.1. _G192.32-11.88N_


Figure C1 shows different components of the studied continuum and emission maps in the same order as Figure B1.
No T _bol_ and L _bol_ estimations are currently available for this object in the literature. The envelope mass deduced from
1.3 mm continuum is estimated to be _∼_ 1.2 _±_ 0.18 M _⊙_ .
CO integrated map shows that the outflow shell structure is blended with ambient molecular cloud in the southeast
(blueshifted) lobe. Therefore, to probe the outflow shell, we consider high-velocity components, represented by the
higher contours in the CO integrated map. The redshifted lobe appears to be much shorter in length than the
blueshifted lobe, possibly due to the presence of the ambient cloud in the blueshifted lobe, forming an extended blended
structure. We measured the average inclination angle to be _∼_ _i_ _∼_ 50 [+10] _−_ 10 [degree.] [In] [the] [SiO] [integrated] [emission,] [a]

Episodic Molecular Jets 33


bright SiO emission is evident at the tip of the blueshifted lobe, but absent in the redshifted lobe. Scattered SiO
emission is also observed along the whole blueshifted lobe. The SiO PV diagram shows SiO emission along the outflow
axis, close to the systemic velocity of the source. If this emission originates from the jet, then the jet velocity would
be V _j_ _∼_ 2 _±_ 2 km s _[−]_ [1], where V _j,cor_ = V _j_ /sin _i_ . Such a low velocity is unlikely to synthesize a high-density SiO jet.
Therefore, we suggest that the SiO emission at the tip of the blueshifted lobe could be the interaction zone between
two outflows and the ambient material, as in the case of G208.89-20.04Walma (Dutta et al. 2022b). To confirm the
origin of the SiO emission - subsectionG192.32-11.88N Figure C1 shows different components of our studied continuum
and emission maps in the same order as Figure B1. No T _bol_ and L _bol_ estimations are available for this object in the
literature. The envelope mass from 1.3 mm continuum is estimated to be _∼_ 1.2 _±_ 0.18 M _⊙_ .
CO integrated map shows that the outflow shell structure is blended with ambient molecular cloud in the south-east
(blueshifted) lobe. Therefore, we consider high-velocity components to probe the outflow shell, that is the higher
contours in the CO integrated map. The redshifted lobe appears to be much shorter in length than the blueshifted
lobe, which is possibly due to the presence of ambient cloud in the blueshifted lobe, making it an extended blended
structure. We measured the average inclination angle to be _∼_ _i_ _∼_ 50 [+10] _−_ 10 [degree.] [In] [the] [SiO] [integrated] [emission,] [a]
bright SiO emission is seen in the tip of the blueshifted lobe, but no emission in the redshifted lobe. Scattered SiO
emission is also observed along the whole blueshifted lobe. The SiO PV diagram shows SiO emission along the outflow
axis close to the systemic velocity of the source. If it is originating due to jet, then the jet would have a velocity V _j_
_∼_ 2 _±_ 2 km s _[−]_ [1], where V _j,cor_ = V _j_ /sin _i_, which is too small to synthesize a high-density SiO jet. Therefore, we suggest
that the SiO emission at the tip of the blueshifted lobe could be the interaction zone between two outflows and the
ambient material as in the case of G208.89-20.04Walma (Dutta et al. 2022b). To confirm the origin of the SiO emission
- whether it is indeed a jet or a collision zone - further high-sensitivity observations are required.


C.2. _G200.34-10.97N_


Figure C2 shows the continuum, C [18] O, CO and SiO emission of the object G200.34-10.97N in the same order as
Figure B1. The object is a Class 0 source with T _bol_ _∼_ 43 _±_ 10 K and L _bol_ _∼_ 1.5 _±_ 0.6 L _⊙_ . The envelope mass is estimated
to be M _env_ _∼_ 0.51 _±_ 0.08 M _⊙_ .
The outflow opening near the source is narrow, however, as we move outward, the outflow appears wider. One
possible explanation for this could be that the thick envelope near the source compresses the outflow opening and
upon moving away from the envelope, the outflow suddenly opens up and becomes wide-angle. Another possibility
is that the outflow is blending with the ambient cloud, so it appears wider as a combination of outflow and ambient
cloud. Higher spatial resolution and higher-velocity resolution observations would be beneficial to study the kinematics
and disentangle these components. We are not able to find a good fit for the outer shell to determine the inclination
angle. A tentative fitting suggests that the inclination could be _i_ _∼_ 40 [+15] _−_ 10 [degrees.]
The SiO emission along the jet axis appears bow-shock like, with no dense knot-like structure appearing in this
observation. The SiO emission is not at a very high-velocity range. The mean SiO velocity is V _j_ _∼_ 4 _±_ 2 km s _[−]_ [1], where
V _j,cor_ = V _j_ /sin _i_ . This suggests the SiO emission may not be associated with the jet, but could rather be from the
collision zone between the outflow and the ambient cloud. Further higher velocity and higher sensitivity could help to
disentangle these two scenarios.


C.3. _G205.46-14.56M2_ _(HOPS_ _387_ _and_ _HOPS_ _386)_


Figure C3 displays the 1.3 mm continuum (panel _a_ ), C [18] O spectra (panel _b_ ), integrated CO map (panel _c_ ), and
integrated SiO map (panel _d_ ) of the G205.46-14.56M2 system. It contains five sources, of which, G205.46-14.56M2 ~~A~~,
B, C, D are in a common envelope of mass M _env_ _∼_ 1.04 _±_ 0.19 M _⊙_ . Sources A and B form part of the Class I system
HOPS 387, while sources C and D are components of another Class I system HOPS 386 (Tobin et al. 2020).
From the CO map, the outflow components from different sources are not clearly identified. The outflow direction
of ‘B’ can be determined, but the outflow components from different sources are not distinguishable. A knot-like
emission in the SiO emission is observed, which could be a jet component of source D or C. Alternatively, it could be
possible that sources C and/or D are the line-rich akin to hot-corinos. As such, the detected emission is mimicking
like SiO emission, however, it could actually represent other line emissions emanating from the hot-corinos near the
source. The possibility of another unidentified origin is also viable. From the present status of the observations, it is
not possible to conclusively determine the origin of this emission.

34 Dutta et al.


C.4. _G205.46-14.56N2_ _(HOPS_ _401)_


Figure C4 shows the continuum and emission components of G205.46-14.56N2 in the same order as Figure C3. This
is a Class 0 source with T _bol_ _∼_ 32 _±_ 8 K and L _bol_ _∼_ 0.8 _±_ 0.3 L _⊙_, has an envelope mass of M _env_ _∼_ 0.85 _±_ 0.13 M _⊙_ . The
source also coincides with the location of HOPS 401 (Karnath et al. 2020; Tobin et al. 2020).
The outflow seen in the CO map is difficult to distinguish from the ambient cloud. We detected SiO emission in the
tip of the eorth-eastern lobe of the outflow, which could either be a bow-shock structure of the jet, or a collision zone
between the outflow and ambient cloud. Unfortunately, due to the low sensitivity in both the SiO and CO maps, we
were unable to determine the outflow and jet parameters for this source.


C.5. _G209.55-19.68N1_ _(HOPS_ _12)_


Figure C5 shows different continuum and emission components of G209.55-19.68N1 in the same order as Figure
B1. G209.55-19.68N1 is a multiple system, where source ‘A’ is responsible for driving the largest outflow. Two other
sources, ‘B’ and ‘C’ form a close system that drives a smaller-scale outflow. High-resolution maps of G209.55-19.68N1
reveal that ‘A’ is itself a close binary system, and ‘B-C’ is a single source (HOPS 12 Dutta et al. 2020). In the ACA
resolution, all three sources are within the same common envelope of mass M _env_ _∼_ 1.98 _±_ 0.3 M _⊙_ . In this paper, we
consider T _bol_ _∼_ 47 _±_ 13 K and L _bol_ _∼_ 9.0 _±_ 3.7 L _⊙_ for the main outflow source ‘A’.
The northern component of the outflow shell from source ‘A’ appears wider than the southern part. Within the
northern outflow shell, there is a secondary outflow from the ‘B’ or/and ‘C’ system. The interaction between that two
outflows creates a shock region, which is faintly detected with SiO emission. This SiO emission is not located along
the jet axis. Due to the presence of the secondary source and blending with the ambient cloud, the northern outflow
appears wider than the southern component. A similar outflow collision zone was reported for another protostellar
system BHR 71 (Zapata et al. 2018). The southern component of CO emission (redshifted) is narrower than the
northern lobe. Here, we visually checked each channel to identify the likely outflow shell. In the northern lobe, we
chose a CO emission width close to the source and, in the southern lobe, we consider up to 2 _σ_ to define the outflow
shell. We measured the average inclination angle from the CO shell to be _∼_ _i_ _∼_ 27 [+15] _−_ 10 [degrees.] [The] [tiny] [knot-like]
structure in SiO emission (PV diagram) could not be confirmed as a real knot from the current observations.


C.6. _G211.47-19.27S_ _(HOPS_ _288)_


Figure C6 shows the continuum and emission components of G211.47-19.27S in the same order as Figure C3. From
the CO velocity channel maps, we have detected three distinct outflow sources, all of which are within a common
envelope of mass M _env_ _∼_ 3.37 _±_ 0.52 M _⊙_ . The location of the system coincides with HOP 288. The combined system
has T _bol_ _∼_ 49 _±_ 21 K and L _bol_ _∼_ 180 _±_ 70 L _⊙_ . Such a high bolometric luminosity and temperature suggest that the
system is in the Class I phase, however, disentangling the nature of individual components within this multiple source
system is challenging due to the low-resolution infrared observations.
The properties of the three CO outflows could not be separated based on the current state of our observations.
Bright monopolar SiO emission is observed along the jet axis of source ‘B’. The SiO emission is in the redshifted
outflow lobe of ‘B’ with a mean velocity _V_ _j_ _∼_ 5 _±_ 2 km s _[−]_ [1] . The source ‘A’ is possibly a line-rich ‘hot-corino’ object
(Hsu et al. 2022). Given that the outflow/jet components for the different sources could not be differentiated, the
outflow/jet parameters have not been estimated.


D. OBJECTS WITH NO SIO EMISSION BUT WELL-DEFINED CO OUTFLOW


D.1. _G192.12-11.10_


Figure D1 shows the 1.3 mm continuum (panel _a_ ), C [18] O spectra (panel _b_ ), integrated CO map (panel _c_ ), and CO
position-velocity diagram (panel _d_ ) of G192.12 _−_ 11.20. It is a Class 0 source with T _bol_ _∼_ 44 _±_ 15 K, L _bol_ _∼_ 9.5 _±_ 4.0
L _⊙_, and a envelope mass of M _env_ _∼_ 1.21 _±_ 0.18 M _⊙_ . Although the source is in the Class 0 phase, we do not observe
any jet-like components along the flow-axis in either SiO or CO. However if the jet is very high-density and optically
thicker for SiO (5-4) and CO(2-1), then the jet components could be detected in higher transitions, such as SiO (8-7)
and CO(3-2). The object appears to be orientated nearly edge-on with an inclination angle of _i_ _∼_ 15 [+10] _−_ 5 [degrees.]


D.2. _G196.92-10.37_


G196.92-10.37 (Figure D2; in the same sequence as Figure D1) is a wide multiple system, where the strongest outflow
is driven by source ‘A’ along northeast to southwest direction. T _bol_ and L _bol_ of the source ‘A’ are currently unknown.

Episodic Molecular Jets 35


The outflows from sources ‘B’ and ‘C’ are less spatially extended following a north-south direction and they blend with
the blueshifted lobe from source ‘A’. There is no way to disentangle the outflow components from different sources
from the present data set. Assuming minimal contamination from the outflows of ‘B’ and ‘C’ to the ‘A’ outflow, we
have estimated the outflow force for source ‘A’. The envelope mass for source ‘A’ is M _env_ _∼_ 0.71 _±_ 0.12 M _⊙_ . It is
possibly highly inclined, close to face-on (i _∼_ 70 [+10] _−_ 10 [degree).] [There] [is] [no] [detection] [of] [SiO] [emission] [in] [this] [target] [field.]


D.3. _G203.21-11.20W1_


Figure D3 shows various components of G203.21-11.20W1 in the same sequence as Figure D1. An outflow is
emanating from the source, which has an envelope mass of M _env_ _∼_ 0.54 _±_ 0.11 M _⊙_ . Notably, there is no reported
infrared emission for this source in the literature. The outflow is characterized by a narrow angle and has a welldefined cavity wall. No jet-like high-velocity component has been detected in either SiO or CO. We measured the
average inclination angle to be _∼_ _i_ _∼_ 20 [+10] _−_ 5 [degrees.]


D.4. _G208.68-19.20S_ _(HOPS_ _84)_


G208.68-19.20S (HOPS 84; Figure D4) is a close binary system with T _bol_ _∼_ 96 _±_ 25 K, L _bol_ _∼_ 49 _±_ 18 L _⊙_, and the
envelope mass is M _env_ _∼_ 1.55 _±_ 0.3 M _⊙_ . The outflow is likely being driven by the source ‘A’. The CO PV diagram
suggests the object is nearly edge-on with an inclination angle of _∼_ _i_ _∼_ 10 [+10] _−_ 5 [degrees.] [No] [SiO] [emission] [was] [detected]
in this target field.


D.5. _G211.01-19.54N_


Figure D5 shows the observed components of G211.01-19.54N (also known as HOPS 153) in the same sequence as
Figure D1. It is catagorised as a Class 0 system with T _bol_ _∼_ 39 _±_ 12 K and L _bol_ _∼_ 4.5 _±_ 1.8 L _⊙_ . The envelope mass
is M _env_ _∼_ 0.81 _±_ 0.16 M _⊙_ . Continuum emission extends along the same direction as the blueshifted CO outflow,
suggesting that this could represent envelope material being entrained by the outflow.
No SiO emission was detected in this target field. The blueshifted outflow shell in the PV diagram is difficult to
distinguish from the ambient cloud. We assumed the likely shell structure from near-source emission and fitted it with
a parabolic equation, which provides an inclination angle of _∼_ _i_ _∼_ 50 [+10] _−_ 20 [degrees.]


D.6. _G211.01-19.54S_


Figure D6) depicts G211.01-19.54S (also known as HOPS 152), a Class 0 system with T _bol_ _∼_ 52 _±_ 8 K, and L _bol_ _∼_
0.9 _±_ 0.4 L _⊙_ . This is one of the very low-luminosity objects. It possesses an envelope with a mass of M _env_ _∼_ 0.21 _±_ 0.04
M _⊙_ . Only a redshifted (southern) outflow shell is detected with CO-integrated emission. This could be a monopolar
outflow source unless the northern outflow is blended with the ambient cloud. In the PV diagram, the emission in the
blueshifted (northern) part is likely tracing ambient material. The outflow shell, even in the redshifted section, could
not be distinguished in the PV diagram. Consequently, the inclination angle measurement for this source is highly
biased due to the unreliable outflow shell consideration. No SiO emission is detected in this observed field.


D.7. _G212.84-19.45N_


G212.84-19.45N (HOPS 224; Figure D7) is a Class 0 system with T _bol_ _∼_ 50 _±_ 13 K, L _bol_ _∼_ 3.0 _±_ 1.2 L _⊙_, and envelope of
mass M _env_ _∼_ 0.52 _±_ 0.09 M _⊙_ . In the CO-integrated emission of this system, the redshifted outflow appears wider than
the blueshifted lobe. We have estimated an average inclination angle _∼_ _i ∼_ 25 [+15] _−_ 10 [degrees.] [Interstingly, a high-velocity]
CO component can be observed in the redshifted lobe, which may be indicative of a jet. However, no SiO emission
has been detected in this field.


E. OBJECTS WITH NO SIO EMISSION AND NO WELL-DEFINED CO OUTFLOW


In some identified sources, CO outflows were detected, however, due to poor signal-to-noise, deriving the PV diagram
along the outflow axis was not possible. These sources include G201.52-11.08 (a Class I source; Figure E2), G205.4614.56S2 (a class source HOPS 385; Figure E4), G210.82-19.47S (a class source HOPS 156, Figure E8; Outflow driven by
G210.82-19.47S, not by secondary source G210.82-19.47S ~~0~~ 2), G211.16-19.33N2 (a transition Class 0 to Class I source
HOPS 133; Figure E10), G211.47-19.27N (a Class 0 close binary source HOPS 290; Figure E11), and G212.10-19.15S
(a class 0 source; HOPS 247; Figure E13).
CO emission is observed in the field of a few other sources, however, in these cases the flow direction can not
be resolved due to poor sensitivity. These sources are G192.32-11.88S (a Class I source; Figure E1; and source _♯_ 02

36 Dutta et al.


is the same of G192.32-11.88N), G205.46-14.56N1 (a Class 0 protostar HOPS 402; Figure E3), G206.93-16.61E2 (a
class I multiple system HOPS 298; Figure E5), G207.36-19.82N1 (a binary system, outflow driven bu source ‘A’; Figure
E6), G208.68-19.20N1 (a Class 0 system HOPS 87; Figure E7), G210.97-19.33S2 (a wide binary system source ‘A’ or
HOPS 377 and ‘B’ or HOPS 144; Figure E9, G212.10-19.15N2 (a close binary system source ‘A’ or HOPS 263 and ‘B’
or HOPS 262; Figure E12), and G215.87-17.62N (a Class II system; Figure E14).
High-sensitivity observations with other molecular transitions and higher transitions of CO and SiO could be beneficial for studying the outflow/jet morphology of these objects. For instance, 208.68-19.20N1 (HOPS 87) exhibits a
compact outflow in HCN (4-3) and CO (3-2), reported in (Takahashi & Ho 2012).


REFERENCES



Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, in

Protostars and Planets V, ed. B. Reipurth, D. Jewitt, &

K. Keil, 245. [https://arxiv.org/abs/astro-ph/0603071](https://arxiv.org/abs/astro-ph/0603071)


Astropy Collaboration, Robitaille, T. P., Tollerud, E. J.,

et al. 2013, A&A, 558, A33,

doi: [10.1051/0004-6361/201322068](http://doi.org/10.1051/0004-6361/201322068)

Audard, M., Abrah´am, [´] P., Dunham, M. M., et al. 2014, in

Protostars and Planets VI, ed. H. Beuther, R. S. Klessen,

C. P. Dullemond, & T. Henning, 387,

doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch017)~~ 780816531240-ch017


Bachiller, R., Gueth, F., Guilloteau, S., Tafalla, M., &

Dutrey, A. 2000, A&A, 362, L33.

[https://arxiv.org/abs/astro-ph/0009439](https://arxiv.org/abs/astro-ph/0009439)


Baek, G., MacFarlane, B. A., Lee, J.-E., et al. 2020, ApJ,

895, 27, doi: [10.3847/1538-4357/ab8ad4](http://doi.org/10.3847/1538-4357/ab8ad4)


Balan¸ca, C., Dayou, F., Faure, A., Wiesenfeld, L., &

Feautrier, N. 2018, MNRAS, 479, 2692,

doi: [10.1093/mnras/sty1681](http://doi.org/10.1093/mnras/sty1681)


Bjerkeli, P., Ramsey, J. P., Harsono, D., et al. 2019, A&A,

631, A64, doi: [10.1051/0004-6361/201935948](http://doi.org/10.1051/0004-6361/201935948)


Blondin, J. M., Fryxell, B. A., & Konigl, A. 1990, ApJ, 360,

370, doi: [10.1086/169128](http://doi.org/10.1086/169128)


Bontemps, S., Andre, P., Terebey, S., & Cabrit, S. 1996,

A&A, 311, 858


Cabrit, S., & Bertout, C. 1992, A&A, 261, 274


Charnley, S. B., Rodgers, S. D., & Ehrenfreund, P. 2001,

A&A, 378, 1024, doi: [10.1051/0004-6361:20011193](http://doi.org/10.1051/0004-6361:20011193)


Cieza, L. A., Casassus, S., Tobin, J., et al. 2016, Nature,

535, 258, doi: [10.1038/nature18612](http://doi.org/10.1038/nature18612)


Codella, C., Maury, A. J., Gueth, F., et al. 2014, A&A,

563, L3, doi: [10.1051/0004-6361/201323024](http://doi.org/10.1051/0004-6361/201323024)


Connelley, M. S., & Reipurth, B. 2018, ApJ, 861, 145,

doi: [10.3847/1538-4357/aaba7b](http://doi.org/10.3847/1538-4357/aaba7b)


Draine, B. T. 2006, ApJ, 636, 1114, doi: [10.1086/498130](http://doi.org/10.1086/498130)


Draine, B. T., & Salpeter, E. E. 1979, ApJ, 231, 77,

doi: [10.1086/157165](http://doi.org/10.1086/157165)


Dunham, M. M., Arce, H. G., Mardones, D., et al. 2014,

ApJ, 783, 29, doi: [10.1088/0004-637X/783/1/29](http://doi.org/10.1088/0004-637X/783/1/29)



Dutta, S., Lee, C.-F., Liu, T., et al. 2020, ApJS, 251, 20,

doi: [10.3847/1538-4365/abba26](http://doi.org/10.3847/1538-4365/abba26)

Dutta, S., Lee, C.-F., Johnstone, D., et al. 2022a, ApJ, 925,

11, doi: [10.3847/1538-4357/ac3424](http://doi.org/10.3847/1538-4357/ac3424)

Dutta, S., Lee, C.-F., Hirano, N., et al. 2022b, ApJ, 931,

130, doi: [10.3847/1538-4357/ac67a1](http://doi.org/10.3847/1538-4357/ac67a1)

Ellerbroek, L. E., Podio, L., Kaper, L., et al. 2013, A&A,

551, A5, doi: [10.1051/0004-6361/201220635](http://doi.org/10.1051/0004-6361/201220635)

Fischer, W. J., Hillenbrand, L. A., Herczeg, G. J., et al.

2022, arXiv e-prints, arXiv:2203.11257.

[https://arxiv.org/abs/2203.11257](https://arxiv.org/abs/2203.11257)

Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars

and Planets VI, ed. H. Beuther, R. S. Klessen, C. P.

Dullemond, & T. Henning, 451,

doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch020)~~ 780816531240-ch020

Furlan, E., Fischer, W. J., Ali, B., et al. 2016, ApJS, 224, 5,

doi: [10.3847/0067-0049/224/1/5](http://doi.org/10.3847/0067-0049/224/1/5)

Glassgold, A. E., Mamon, G. A., & Huggins, P. J. 1991,

ApJ, 373, 254, doi: [10.1086/170045](http://doi.org/10.1086/170045)

Harsono, D., Bjerkeli, P., van der Wiel, M. H. D., et al.

2018, Nature Astronomy, 2, 646,

doi: [10.1038/s41550-018-0497-x](http://doi.org/10.1038/s41550-018-0497-x)

Herczeg, G. J., Johnstone, D., Mairs, S., et al. 2017, ApJ,

849, 43, doi: [10.3847/1538-4357/aa8b62](http://doi.org/10.3847/1538-4357/aa8b62)

Hirano, S., & Machida, M. N. 2019, MNRAS, 485, 4667,

doi: [10.1093/mnras/stz740](http://doi.org/10.1093/mnras/stz740)

Hodapp, K. W., Chini, R., Watermann, R., & Lemke, R.

2012, ApJ, 744, 56, doi: [10.1088/0004-637X/744/1/56](http://doi.org/10.1088/0004-637X/744/1/56)

Hsieh, T.-H., Lai, S.-P., Belloche, A., & Wyrowski, F. 2016,

ApJ, 826, 68, doi: [10.3847/0004-637X/826/1/68](http://doi.org/10.3847/0004-637X/826/1/68)

Hsieh, T.-H., Murillo, N. M., Belloche, A., et al. 2019, ApJ,

884, 149, doi: [10.3847/1538-4357/ab425a](http://doi.org/10.3847/1538-4357/ab425a)

Hsu, S.-Y., Liu, S.-Y., Liu, T., et al. 2020, ApJ, 898, 107,

doi: [10.3847/1538-4357/ab9f3a](http://doi.org/10.3847/1538-4357/ab9f3a)
—. 2022, ApJ, 927, 218, doi: [10.3847/1538-4357/ac49e0](http://doi.org/10.3847/1538-4357/ac49e0)

Hu, C.-Y., Zhukovska, S., Somerville, R. S., & Naab, T.

2019, MNRAS, 487, 3252, doi: [10.1093/mnras/stz1481](http://doi.org/10.1093/mnras/stz1481)

Hunter, J. D. 2007, Computing in Science and Engineering,

9, 90, doi: [10.1109/MCSE.2007.55](http://doi.org/10.1109/MCSE.2007.55)

Episodic Molecular Jets 37





**Figure** **B1.** G191.90-11.20S: (a) 1.3 mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 4 to +8] km s _[−]_ [1] with sensitivity 6.48 K km s _[−]_ [1] with
similar symbols and contour from Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contour
as Figure 4b. (e) SiO emission integrated over [ _−_ 10 to +18] km s _[−]_ [1] with sensitivity 3.7 K km s _[−]_ [1] with similar symbols and
contours as Figure 5a. (f) SiO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as Figure 5b.

38 Dutta et al.







**Figure** **B2.** G205.46-14.56M1 (HOPS 317): (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] .
The symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and
V _sys_ = 10 km s _[−]_ [1] . All symbols are the same as Figure 3. (c) CO emission maps integrated over [ _−_ 18 to _−_ 2] and [+2 to +12]
km s _[−]_ [1] with sensitivity 7.4 K km s _[−]_ [1] with similar symbols and contours as Figure 4a. (d) CO PV diagram with sensitivity 0.11
_K_ with similar symbols and contours as Figure 4b. (e) SiO emission integrated over [ _−_ 102 to _−_ 28] and [+4 to +12] km s _[−]_ [1]

with sensitivity 3.7 K km s _[−]_ [1] with similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity 0.16 _K_ with
similar symbols and contour of Figure 5b.

Episodic Molecular Jets 39








|Ambient<br>Cloud?|Col2|Col3|Col4|
|---|---|---|---|
|Ambient<br>Cloud ?||||
|||||



**Figure** **B3.** G205.46-14.56S1 (HOPS 358): (a) 1.3 mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] .
The symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_
= 11 km s _[−]_ [1] . All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 20 to _−_ 4] and [+2 to +20] km s _[−]_ [1] with
sensitivity _σ_ _∼_ 14.8 K km s _[−]_ [1] with similar symbols are Figure 4a. The contours are at (3, 9, 18, 36, 72) _×_ _σ_ . (d) CO PV
diagram with sensitivity 0.11 _K_ with similar symbols and contours as Figure 4b. (e) SiO emission integrated over [ _−_ 20 to +20]
km s _[−]_ [1] with sensitivity 3.4 K km s _[−]_ [1] with similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity 0.14
_K_ with similar symbols and contours as Figure 5b.

40 Dutta et al.





**Figure** **B4.** G206.12-15.76: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 6.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 8 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 4 to +8] km s _[−]_ [1] with sensitivity _σ_ _∼_ 4.63 K km s _[−]_ [1]

with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as Figure
4b. (e) SiO emission integrated over [ _−_ 52 to +42] km s _[−]_ [1] with sensitivity 4.6 K km s _[−]_ [1] with similar symbols and contours as
Figure 5a. (f) SiO PV diagram emission with sensitivity 0.14 _K_ with similar symbols and contours as Figure 5b.

Episodic Molecular Jets 41





**Figure** **B5.** G208.68-19.20N3: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 10.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 12 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 12 to +12] km s _[−]_ [1] with sensitivity _σ_ _∼_ 9.65 K km s _[−]_ [1]

with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as Figure
4b. (e) SiO emission inetgrated over [ _−_ 66 to +58] km s _[−]_ [1] with sensitivity 4.6 K km s _[−]_ [1] with similar symbols and contours as
Figure 5 (f) SiO PV diagram with sensitivity 0.15 _K_ with similar symbols and contours as Figure 5b.

42 Dutta et al.





**Figure** **B6.** G208.89 _−_ 20.04E: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.2 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 9 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 4, and +2 to +6] km s _[−]_ [1] with sensitivity _σ_ _∼_ 1.52
K km s _[−]_ [1] with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as
Figure 4b. (e) SiO emission integrated over [ _−_ 4 to +4] km s _[−]_ [1] with sensitivity 1.7 K km s _[−]_ [1] with similar symbols and contours
as Figure 5a. (f) SiO PV diagram with sensitivity 0.32 _K_ with similar symbols and contours as Figure 5b.

Episodic Molecular Jets 43





**Figure** **B7.** G209.55-19.68S1 (HOPS 11): (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] .
The symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and
V _sys_ = 8 km s _[−]_ [1] . All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 8 to _−_ 4 and, +4 to +8] km s _[−]_ [1]

with sensitivity _σ_ _∼_ 6.6 K km s _[−]_ [1] with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar
symbols and contours as Figure 4b. (e) SiO emission integrated over [ _−_ 60 to +60] km s _[−]_ [1] with sensitivity 8.0 K km s _[−]_ [1] with
similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity 0.15 _K_ with similar symbols and contours as
Figure 5b.

44 Dutta et al.





**Figure** **B8.** G209.55-19.68S2 (HOPS 10): (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.0 mJy beam _[−]_ [1] .
The symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and
V _sys_ = 8 km s _[−]_ [1] . All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 4 to _−_ 2 and +2 to +4] km s _[−]_ [1]

with sensitivity _σ_ _∼_ 5.8 K km s _[−]_ [1] with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.21 _K_ with similar
symbols and contours as Figure 4b. (e) SiO emission integrated over [+40 to +58] km s _[−]_ [1] with sensitivity 2.5 K km s _[−]_ [1] with
similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity 0.21 _K_ with similar symbols and contours as
Figure 5b.

Episodic Molecular Jets 45





**Figure** **B9.** G210.37-19.53S (HOPS 164): (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.0 mJy beam _[−]_ [1] .
The symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and
V _sys_ = 8 km s _[−]_ [1] . All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 6 to _−_ 2 and 0 to +4] km s _[−]_ [1]

with sensitivity _σ_ _∼_ 5.8 K km s _[−]_ [1] with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.21 _K_ with similar
symbols and contours as Figure 4b. (e) SiO emission integrated over [ _−_ 46 to _−_ 24 and, +30 to +48] km s _[−]_ [1] with sensitivity 2.5
K km s _[−]_ [1] with similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity 0.21 _K_ with similar symbols and
contours as Figure 5b.

46 Dutta et al.






|Shell?|Shell?|Col3|Col4|
|---|---|---|---|
|Shell?||Shell?||







**Figure** **B10.** G210.49-19.79W (HOPS 168): (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] .
The symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_
= 7 km s _[−]_ [1] . All symbols are the same as Figure 3. (c) CO emission map integrated over [-45 to +55] km s _[−]_ [1] with sensitivity
6.0 K km s _[−]_ [1] with similar symbols and contours as Figure 4a. (d) CO PV diagram with sensitivity 0.15 _K_ with similar symbols
and contours as Figure 4b. The additional likely episodic shells are marked with thick blue and red lines in the blueshifted
and redshifted lones, respectively. (e) SiO map integrated over [ _−_ 20 to +20] km s _[−]_ [1] with sensitivity 1.9 K km s _[−]_ [1] with similar
symbols and contours as Figure 5a. The knots shifted from jet-axis are marked. (f) SiO PV diagram with sensitivity _σ_ = 0.15
_K_ with similar symbol of Figure 5b.

Episodic Molecular Jets 47





**Figure** **B11.** G215.87-17.62M: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) CO emission integrated over [ _−_ 10 to _−_ 4 and, +2 to +10] km s _[−]_ [1] with sensitivity
_σ_ _∼_ 5.8 K km s _[−]_ [1] with similar symbols are Figure 4a. (d) CO PV diagram with sensitivity 0.21 _K_ with similar symbols and
contours as Figure 4b. (e) SiO emission integrated over [ _−_ 40 to +38] km s _[−]_ [1] with sensitivity 2.5 K km s _[−]_ [1] with similar symbols
and contours as Figure 4a. (f) SiO emission with sensitivity 0.13 _K_ with similar symbols and contours as Figure 4b.

48 Dutta et al.





**Figure** **C1.** G192.32-11.88N: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.9 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 12 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 6.4 K km s _[−]_ [1] with similar symbols and contours
as Figure 4a. (d) CO PV diagram with sensitivity 0.13 _K_ with similar symbols and contours as Figure 4b. (e) Integrated SiO
emission with sensitivity 2.7 K km s _[−]_ [1] with similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity _σ_
= 0.47 _K_ with similar symbol of Figure 5b. The SiO contour labels are at (1.5, 2, 3, 4) _×_ _σ_ .

Episodic Molecular Jets 49






|Col1|Col2|Ambient<br>Cloud?|Col4|Col5|
|---|---|---|---|---|
|||Ambient<br>Cloud ?|Ambient<br>Cloud ?|Ambient<br>Cloud ?|



**Figure** **C2.** G200.34-10.97N: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 14 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) CO map integrated over [-20 to +12] km s _[−]_ [1] with sensitivity 9.9 K km s _[−]_ [1] with similar
symbols and contours as Figure 4a. (d) CO PV diagram with sensitivity 0.14 _K_ with similar symbols and contours as Figure
4b. (e) SiO emission map integrated over [-10 to +10] km s _[−]_ [1] emission with sensitivity 3.7 K km s _[−]_ [1] with similar symbols and
contours as Figure 5a. (f) SiO PV diagram with sensitivity _σ_ = 0.12 _K_ with similar symbol of Figure 5b. The SiO contour
labels are at (2, 3, 4) _×_ _σ_ .

50 Dutta et al.




|Col1|HOPS386|HOPS387|Col4|Col5|Col6|
|---|---|---|---|---|---|
||HOPS 386|HOPS 387||||



**Figure** **C3.** G205.46-14.56M2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 4.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 14 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 6.15 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a. (d) Integrated SiO emission with sensitivity 2.1 K km s _[−]_ [1] with similar symbols and contours as Figure
5a.

Episodic Molecular Jets 51





**Figure** **C4.** G205.46-14.56N2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.8 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 4.5 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a. (d) Integrated SiO emission with sensitivity 1.15 K km s _[−]_ [1] with similar symbols and contours as Figure
5a.



Imai, M., Oya, Y., Sakai, N., et al. 2019, ApJL, 873, L21,


doi: [10.3847/2041-8213/ab0c20](http://doi.org/10.3847/2041-8213/ab0c20)


Jhan, K.-S., & Lee, C.-F. 2016, ApJ, 816, 32,


doi: [10.3847/0004-637X/816/1/32](http://doi.org/10.3847/0004-637X/816/1/32)


—. 2021, ApJ, 909, 11, doi: [10.3847/1538-4357/abd6c5](http://doi.org/10.3847/1538-4357/abd6c5)


Jhan, K.-S., Lee, C.-F., Johnstone, D., et al. 2022, ApJL,


931, L5, doi: [10.3847/2041-8213/ac6a53](http://doi.org/10.3847/2041-8213/ac6a53)


Johnstone, D., Hendricks, B., Herczeg, G. J., & Bruderer, S.


2013, ApJ, 765, 133, doi: [10.1088/0004-637X/765/2/133](http://doi.org/10.1088/0004-637X/765/2/133)


Johnstone, D., Herczeg, G. J., Mairs, S., et al. 2018, ApJ,


854, 31, doi: [10.3847/1538-4357/aaa764](http://doi.org/10.3847/1538-4357/aaa764)


Jørgensen, J. K., Kuruwita, R. L., Harsono, D., et al. 2022,


Nature, 606, 272, doi: [10.1038/s41586-022-04659-4](http://doi.org/10.1038/s41586-022-04659-4)



Jørgensen, J. K., Visser, R., Williams, J. P., & Bergin, E. A.


2015, A&A, 579, A23, doi: [10.1051/0004-6361/201425317](http://doi.org/10.1051/0004-6361/201425317)


Karnath, N., Megeath, S. T., Tobin, J. J., et al. 2020, ApJ,


890, 129, doi: [10.3847/1538-4357/ab659e](http://doi.org/10.3847/1538-4357/ab659e)


Kim, G., Lee, C. W., Maheswar, G., et al. 2019, ApJS, 240,


18, doi: [10.3847/1538-4365/aaf889](http://doi.org/10.3847/1538-4365/aaf889)


Krumholz, M. R., Bate, M. R., Arce, H. G., et al. 2014, in


Protostars and Planets VI, ed. H. Beuther, R. S. Klessen,


C. P. Dullemond, & T. Henning, 243–266,


doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch011)~~ 780816531240-ch011


Larson, R. B. 1969, MNRAS, 145, 271,


doi: [10.1093/mnras/145.3.271](http://doi.org/10.1093/mnras/145.3.271)

52 Dutta et al.





**Figure** **C5.** G209.55-19.68N1: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 7 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 7.8 K km s _[−]_ [1] with similar symbols and contours
as Figure 4a. (d) CO PV diagram with sensitivity 0.12 _K_ with similar symbols and contours as Figure 4b. (e) Integrated SiO
emission with sensitivity 2.6 K km s _[−]_ [1] with similar symbols and contours as Figure 5a. (f) SiO PV diagram with sensitivity _σ_
= 0.15 _K_ with similar symbol of Figure 5b.

Episodic Molecular Jets 53





**Figure** **C6.** G211.47-19.27S: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 4 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 8.6 K km s _[−]_ [1] with similar symbols and contours
as Figure 4a. (d) CO PV diagram with sensitivity 0.15 _K_ with similar symbols and contours as Figure 4b. (e) Integrated SiO
emission with sensitivity 1.9 K km s _[−]_ [1] with similar symbols and contours as Figure 5a.

54 Dutta et al.





**Figure** **D1.** G192.12-11.10: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 11.5 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as Figure 4b.



Lee, C.-F. 2020, A&A Rv, 28, 1,

doi: [10.1007/s00159-020-0123-7](http://doi.org/10.1007/s00159-020-0123-7)


Lee, C.-F., Hasegawa, T. I., Hirano, N., et al. 2010, ApJ,

713, 731, doi: [10.1088/0004-637X/713/2/731](http://doi.org/10.1088/0004-637X/713/2/731)


Lee, C.-F., Ho, P. T. P., Hirano, N., et al. 2007a, ApJ, 659,

499, doi: [10.1086/512540](http://doi.org/10.1086/512540)


Lee, C.-F., Ho, P. T. P., Li, Z.-Y., et al. 2017a, Nature

Astronomy, 1, 0152, doi: [10.1038/s41550-017-0152](http://doi.org/10.1038/s41550-017-0152)


Lee, C.-F., Ho, P. T. P., Palau, A., et al. 2007b, ApJ, 670,

1188, doi: [10.1086/522333](http://doi.org/10.1086/522333)


Lee, C.-F., Li, Z.-Y., Hirano, N., et al. 2018, ApJ, 863, 94,

doi: [10.3847/1538-4357/aad2da](http://doi.org/10.3847/1538-4357/aad2da)


Lee, C.-F., Li, Z.-Y., Ho, P. T. P., et al. 2017b, Science

Advances, 3, e1602935, doi: [10.1126/sciadv.1602935](http://doi.org/10.1126/sciadv.1602935)



Lee, C.-F., Li, Z.-Y., Shang, H., & Hirano, N. 2022, ApJL,

927, L27, doi: [10.3847/2041-8213/ac59c0](http://doi.org/10.3847/2041-8213/ac59c0)


Lee, C.-F., Mundy, L. G., Reipurth, B., Ostriker, E. C., &

Stone, J. M. 2000, ApJ, 542, 925, doi: [10.1086/317056](http://doi.org/10.1086/317056)


Lee, C.-F., Rao, R., Ching, T.-C., et al. 2014, ApJL, 797,

L9, doi: [10.1088/2041-8205/797/1/L9](http://doi.org/10.1088/2041-8205/797/1/L9)


Lee, C.-F., Stone, J. M., Ostriker, E. C., & Mundy, L. G.

2001, ApJ, 557, 429, doi: [10.1086/321648](http://doi.org/10.1086/321648)


Lee, C.-F., Kwon, W., Jhan, K.-S., et al. 2019a, ApJ, 879,

101, doi: [10.3847/1538-4357/ab2458](http://doi.org/10.3847/1538-4357/ab2458)


Lee, C. W., Kim, M.-R., Kim, G., et al. 2013, ApJ, 777, 50,

doi: [10.1088/0004-637X/777/1/50](http://doi.org/10.1088/0004-637X/777/1/50)


Lee, J.-E., Lee, S., Baek, G., et al. 2019b, Nature

Astronomy, 3, 314, doi: [10.1038/s41550-018-0680-0](http://doi.org/10.1038/s41550-018-0680-0)

Episodic Molecular Jets 55





**Figure** **D2.** G196.92-10.37: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.2 mJy beam _[−]_ [1] . The symbols and
contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 11 km s _[−]_ [1] . All
symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 9.6 K km s _[−]_ [1] with similar symbols and contours
as Figure 4a. (d) CO PV diagram with sensitivity 0.1 _K_ with similar symbols and contours as Figure 4b.



Lee, Y.-H., Johnstone, D., Lee, J.-E., et al. 2020, ApJ, 903,


5, doi: [10.3847/1538-4357/abb6fe](http://doi.org/10.3847/1538-4357/abb6fe)


—. 2021, ApJ, 920, 119, doi: [10.3847/1538-4357/ac1679](http://doi.org/10.3847/1538-4357/ac1679)


Lef`evre, C., Cabrit, S., Maury, A. J., et al. 2017, A&A, 604,


L1, doi: [10.1051/0004-6361/201730766](http://doi.org/10.1051/0004-6361/201730766)


Luo, Q.-y., Liu, T., Tatematsu, K., et al. 2022, ApJ, 931,


158, doi: [10.3847/1538-4357/ac66d9](http://doi.org/10.3847/1538-4357/ac66d9)


MacFarlane, B., Stamatellos, D., Johnstone, D., et al.


2019a, arXiv e-prints, arXiv:1906.01960.


[https://arxiv.org/abs/1906.01960](https://arxiv.org/abs/1906.01960)


—. 2019b, MNRAS, 1508, doi: [10.1093/mnras/stz1570](http://doi.org/10.1093/mnras/stz1570)


Machida, M. N., & Basu, S. 2019, ApJ, 876, 149,


doi: [10.3847/1538-4357/ab18a7](http://doi.org/10.3847/1538-4357/ab18a7)



Machida, M. N., & Hosokawa, T. 2013, MNRAS, 431, 1719,

doi: [10.1093/mnras/stt291](http://doi.org/10.1093/mnras/stt291)


McMullin, J. P., Waters, B., Schiebel, D., Young, W., &

Golap, K. 2007, Astronomical Society of the Pacific

Conference Series, Vol. 376, CASA Architecture and

Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127


Mercer, A., & Stamatellos, D. 2017, MNRAS, 465, 2,

doi: [10.1093/mnras/stw2714](http://doi.org/10.1093/mnras/stw2714)


Moraghan, A., Lee, C.-F., Huang, P.-S., & Vaidya, B. 2016,

MNRAS, 460, 1829, doi: [10.1093/mnras/stw1089](http://doi.org/10.1093/mnras/stw1089)


Ninan, J. P., Ojha, D. K., Bhatt, B. C., et al. 2013, ApJ,

778, 116, doi: [10.1088/0004-637X/778/2/116](http://doi.org/10.1088/0004-637X/778/2/116)


Nony, T., Motte, F., Louvet, F., et al. 2020, A&A, 636,

A38, doi: [10.1051/0004-6361/201937046](http://doi.org/10.1051/0004-6361/201937046)

56 Dutta et al.





**Figure** **D3.** G203.21-11.20W1: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 3.36 mJy beam _[−]_ [1] . The
symbols and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10
km s _[−]_ [1] . All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 5.14 K km s _[−]_ [1] with similar symbols
and contours as Figure 4a. (d) CO PV diagram with sensitivity 0.11 _K_ with similar symbols and contours as Figure 4b.



Nozawa, T., Kozasa, T., & Habe, A. 2006, ApJ, 648, 435,


doi: [10.1086/505639](http://doi.org/10.1086/505639)


Offner, S. S. R., Klein, R. I., McKee, C. F., & Krumholz,


M. R. 2009, ApJ, 703, 131,


doi: [10.1088/0004-637X/703/1/131](http://doi.org/10.1088/0004-637X/703/1/131)


Palau, A., Zapata, L. A., Rodr´ıguez, L. F., et al. 2014,


MNRAS, 444, 833, doi: [10.1093/mnras/stu1461](http://doi.org/10.1093/mnras/stu1461)


Panoglou, D., Cabrit, S., Pineau Des Forˆets, G., et al. 2012,


A&A, 538, A2, doi: [10.1051/0004-6361/200912861](http://doi.org/10.1051/0004-6361/200912861)


Park, W., Lee, J.-E., Contreras Pe˜na, C., et al. 2021, ApJ,


920, 132, doi: [10.3847/1538-4357/ac1745](http://doi.org/10.3847/1538-4357/ac1745)


Plunkett, A. L., Arce, H. G., Mardones, D., et al. 2015,


Nature, 527, 70, doi: [10.1038/nature15702](http://doi.org/10.1038/nature15702)



Podio, L., Codella, C., Gueth, F., et al. 2015, A&A, 581,

A85, doi: [10.1051/0004-6361/201525778](http://doi.org/10.1051/0004-6361/201525778)


—. 2016, A&A, 593, L4, doi: [10.1051/0004-6361/201628876](http://doi.org/10.1051/0004-6361/201628876)


Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648,

A45, doi: [10.1051/0004-6361/202038429](http://doi.org/10.1051/0004-6361/202038429)


Raga, A. C., Vel´azquez, P. F., Cant´o, J., & Masciadri, E.

2002, A&A, 395, 647, doi: [10.1051/0004-6361:20021180](http://doi.org/10.1051/0004-6361:20021180)


Riaz, R., Vanaverbeke, S., & Schleicher, D. R. G. 2018,

A&A, 614, A53, doi: [10.1051/0004-6361/201732076](http://doi.org/10.1051/0004-6361/201732076)


Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical

Plotting Library in Python, Astrophysics Source Code

Library, record ascl:1208.017. [http://ascl.net/1208.017](http://ascl.net/1208.017)


Rodgers, S. D., & Charnley, S. B. 2003, ApJ, 585, 355,

doi: [10.1086/345497](http://doi.org/10.1086/345497)

Episodic Molecular Jets 57





**Figure** **D4.** G208.68-19.20S: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 10 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 1.5 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as Figure 4b.



Safron, E. J., Fischer, W. J., Megeath, S. T., et al. 2015,


ApJL, 800, L5, doi: [10.1088/2041-8205/800/1/L5](http://doi.org/10.1088/2041-8205/800/1/L5)


Sahu, D., Liu, S.-Y., Liu, T., et al. 2021, ApJL, 907, L15,


doi: [10.3847/2041-8213/abd3aa](http://doi.org/10.3847/2041-8213/abd3aa)


Santiago-Garc´ıa, J., Tafalla, M., Johnstone, D., & Bachiller,


R. 2009, A&A, 495, 169,


doi: [10.1051/0004-6361:200810739](http://doi.org/10.1051/0004-6361:200810739)


Schilke, P., Walmsley, C. M., Pineau des Forets, G., &


Flower, D. R. 1997, A&A, 321, 293


Shang, H., Liu, C.-F., Krasnopolsky, R., & Wang, L.-Y.


2023, ApJ, 944, 230, doi: [10.3847/1538-4357/aca763](http://doi.org/10.3847/1538-4357/aca763)


Shu, F. H., Najita, J., Ostriker, E. C., & Shang, H. 1995,


ApJL, 455, L155, doi: [10.1086/309838](http://doi.org/10.1086/309838)



Simon, M., Dutrey, A., & Guilloteau, S. 2000, ApJ, 545,

1034, doi: [10.1086/317838](http://doi.org/10.1086/317838)


Skretas, I. M., & Kristensen, L. E. 2022, A&A, 660, A39,

doi: [10.1051/0004-6361/202141944](http://doi.org/10.1051/0004-6361/202141944)


Snell, R. L., Loren, R. B., & Plambeck, R. L. 1980, ApJL,

239, L17, doi: [10.1086/183283](http://doi.org/10.1086/183283)


Stahler, S. W. 1988, ApJ, 332, 804, doi: [10.1086/166694](http://doi.org/10.1086/166694)


Stamatellos, D., Whitworth, A. P., & Hubber, D. A. 2011,

ApJ, 730, 32, doi: [10.1088/0004-637X/730/1/32](http://doi.org/10.1088/0004-637X/730/1/32)


—. 2012, MNRAS, 427, 1182,

doi: [10.1111/j.1365-2966.2012.22038.x](http://doi.org/10.1111/j.1365-2966.2012.22038.x)


Tabone, B., Godard, B., Pineau des Forˆets, G., Cabrit, S.,

& van Dishoeck, E. F. 2020, A&A, 636, A60,

doi: [10.1051/0004-6361/201937383](http://doi.org/10.1051/0004-6361/201937383)

58 Dutta et al.





**Figure** **D5.** G211.01-19.54N: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2 mJy beam _[−]_ [1] . The symbols and
contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 6 km s _[−]_ [1] . All
symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 6.3 K km s _[−]_ [1] with similar symbols and contours
as Figure 4a. (d) CO PV diagram with sensitivity 0.16 _K_ with similar symbols and contours as Figure 4b.



Tafalla, M., Bachiller, R., Lefloch, B., et al. 2015, A&A,


573, L2, doi: [10.1051/0004-6361/201425255](http://doi.org/10.1051/0004-6361/201425255)


Tafalla, M., Su, Y. N., Shang, H., et al. 2017, A&A, 597,


A119, doi: [10.1051/0004-6361/201629493](http://doi.org/10.1051/0004-6361/201629493)


Takahashi, S., & Ho, P. T. P. 2012, ApJL, 745, L10,


doi: [10.1088/2041-8205/745/1/L10](http://doi.org/10.1088/2041-8205/745/1/L10)


Taquet, V., Wirstr¨om, E. S., & Charnley, S. B. 2016, ApJ,


821, 46, doi: [10.3847/0004-637X/821/1/46](http://doi.org/10.3847/0004-637X/821/1/46)


Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020,


ApJ, 890, 130, doi: [10.3847/1538-4357/ab6f64](http://doi.org/10.3847/1538-4357/ab6f64)


Wakelam, V., Coutens, A., Gratier, P., Vidal, T. H. G., &


Vaytet, N. 2022, A&A, 666, A191,


doi: [10.1051/0004-6361/202243459](http://doi.org/10.1051/0004-6361/202243459)



Wiebe, D. S., Molyarova, T. S., Akimkin, V. V., Vorobyov,


E. I., & Semenov, D. A. 2019, MNRAS, 485, 1843,


doi: [10.1093/mnras/stz512](http://doi.org/10.1093/mnras/stz512)


Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C.


2010, ApJ, 718, 1062,


doi: [10.1088/0004-637X/718/2/1062](http://doi.org/10.1088/0004-637X/718/2/1062)


Yen, H.-W., Koch, P. M., Takakuwa, S., et al. 2017, ApJ,


834, 178, doi: [10.3847/1538-4357/834/2/178](http://doi.org/10.3847/1538-4357/834/2/178)


Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al.


2015, A&A, 576, A109,


doi: [10.1051/0004-6361/201424538](http://doi.org/10.1051/0004-6361/201424538)


Yoo, H., Lee, J.-E., Mairs, S., et al. 2017, ApJ, 849, 69,


doi: [10.3847/1538-4357/aa8c0a](http://doi.org/10.3847/1538-4357/aa8c0a)

Episodic Molecular Jets 59





**Figure** **D6.** G211.01-19.54S: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.4 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 6 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 2.21 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a. (d) CO PV diagram with sensitivity 0.13 _K_ with similar symbols and contours as Figure 4b.



Yoon, S.-Y., Herczeg, G. J., Lee, J.-E., et al. 2022, ApJ,
929, 60, doi: [10.3847/1538-4357/ac5632](http://doi.org/10.3847/1538-4357/ac5632)

Yvart, W., Cabrit, S., Pineau des Forˆets, G., & Ferreira, J.

2016, A&A, 585, A74, doi: [10.1051/0004-6361/201525915](http://doi.org/10.1051/0004-6361/201525915)

Zapata, L. A., Fern´andez-L´opez, M., Rodr´ıguez, L. F.,
et al. 2018, AJ, 156, 239, doi: [10.3847/1538-3881/aae51e](http://doi.org/10.3847/1538-3881/aae51e)



Zhang, Y., Arce, H. G., Mardones, D., et al. 2019, ApJ,


883, 1, doi: [10.3847/1538-4357/ab3850](http://doi.org/10.3847/1538-4357/ab3850)


Zinnecker, H., McCaughrean, M. J., & Rayner, J. T. 1998,


Nature, 394, 862, doi: [10.1038/29716](http://doi.org/10.1038/29716)

60 Dutta et al.




|Col1|Col2|j e t ?|
|---|---|---|
||||



**Figure** **D7.** G212.84-19.45N: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 4 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 1.24 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a. (d) CO PV diagram with sensitivity 0.12 _K_ with similar symbols and contours as Figure 4b.

Episodic Molecular Jets 61







**Figure** **E1.** G192.32-11.88S: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 3.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 6.6 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a.

62 Dutta et al.





**Figure** **E2.** G201.52-11.08: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.5 mJy beam _[−]_ [1] . The symbols and
contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 9 km s _[−]_ [1] . All
symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 1.4 K km s _[−]_ [1] with similar symbols and contours
as Figure 4a.

Episodic Molecular Jets 63





**Figure** **E3.** G205.46-14.56N1: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 9.2 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a.

64 Dutta et al.





**Figure** **E4.** G205.46-14.56S2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.7 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 6.0 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a.

Episodic Molecular Jets 65





**Figure** **E5.** G206.93-16.61E2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 12 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 37.5 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a.

66 Dutta et al.





**Figure** **E6.** G207.36-19.82N1: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 2.5 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 12 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 6.13 K km s _[−]_ [1] with similar symbols and
contours as Figure 4a.

Episodic Molecular Jets 67





**Figure** **E7.** G208.68-19.20N1: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 18 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 11 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 31.6 K km s _[−]_ [1] with similar symbols are Figure
4a. The contours are at (3, 5) _×_ 31.6 K

68 Dutta et al.





**Figure** **E8.** G210.82-19.47S: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.2 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 6 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 0.8 K km s _[−]_ [1] with similar symbols are Figure
4a.

Episodic Molecular Jets 69





**Figure** **E9.** G210.97-19.33S2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.7 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 3.0 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 8.0 K km s _[−]_ [1] with similar symbols are Figure
4a.

70 Dutta et al.





**Figure** **E10.** G211.16-19.33N2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.1 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 4.0 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 1.6 K km s _[−]_ [1] with similar symbols are Figure
4a.

Episodic Molecular Jets 71





**Figure** **E11.** G211.47-19.27N: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.15 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 4.0 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 2.5 K km s _[−]_ [1] with similar symbols are Figure
4a.

72 Dutta et al.






|(HOPS262)<br>(HOPS263)|Col2|
|---|---|
|||



**Figure** **E12.** G212.10-19.15N2: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.0 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 4.0 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 2.14 K km s _[−]_ [1] with similar symbols are Figure
4a.

Episodic Molecular Jets 73





**Figure** **E13.** G212.10-19.15S: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 1.1 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 4.0 km s _[−]_ [1] .
All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 1.85 K km s _[−]_ [1] with similar symbols are Figure
4a.

74 Dutta et al.





**Figure** **E14.** G215.87-17.62N: (a) 1.3mm continuum map at ACA resolution with sensitivity _∼_ 0.7 mJy beam _[−]_ [1] . The symbols
and contour levels are the same as Figure 1. (b) The C [18] O spectra extracted from high-resolution maps, and V _sys_ = 10.0
km s _[−]_ [1] . All symbols are the same as Figure 3. (c) Integrated CO emission with sensitivity 5.21 K km s _[−]_ [1] with similar symbols
are Figure 4a.


</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[5].what.evidence[0]",
  "value": "Equation for water sublimation radius R(100K) in the envelope",
  "failed_quote": "The water sublimation radius R(100) in the envelope at a given luminosity (black line) has been calculated by the equation in Bisschop et al. 2007."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Fit 1.3 mm ACA continuum emission above the 3sigma contour with one or more 2D Gaussians using CASA imfit task and compute lower limit of inner envelope mass from integrated flux using Planck blackbody equation.",
  "failed_quote": "For simplicity, however, we assume the emission is optically thin to infer the lower limit of inner envelope mass (M Env ) following the equation: M Env ∼ D 2 F ν ( ν ) B ν ( T dust ) κ ν (1)"
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Low-velocity CO emission above 3sigma",
  "failed_quote": "To explore such different kinds of outflow features, we estimated inclination angles i a using the low-velocity CO emission above 3 σ ."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Convert beam-averaged CO emission above 3sigma in each velocity channel (excluding channels near V_sys) into channel mass M_k, sum momentum P = sum(M_k V_k), and divide by dynamical time T_dyn,out = R_CO / V_CO,max with inclination correction f_ia.",
  "failed_quote": "Finally for a total outflow extension of R CO with maximum outflow velocity V CO,max , F CO is expressed as: F CO = P T dyn,out = f ia V CO,max R CO ∑ k M k V k (3)"
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Search CO and SiO data cubes and PV diagrams along the flow axis to identify discrete knots; take mean velocity of brightest peak knot emission as V_j, deproject via V_j,cor = V_j / sin(i), compute mean timescale between consecutive knots as T_knot = (delta_R / V_j) tan(i), and convert T_knot to Keplerian orbital radius via Kepler's third law.",
  "failed_quote": "The mean timescales between knots are measured as T knot = δR V j tan( i ), where δ R is the mean distance between two consecutive knots."
 },
 {
  "path": "analysis_steps[4].method.evidence[2]",
  "value": "Search CO and SiO data cubes and PV diagrams along the flow axis to identify discrete knots; take mean velocity of brightest peak knot emission as V_j, deproject via V_j,cor = V_j / sin(i), compute mean timescale between consecutive knots as T_knot = (delta_R / V_j) tan(i), and convert T_knot to Keplerian orbital radius via Kepler's third law.",
  "failed_quote": "The corresponding orbital radii for those periods can be estimated from Kepler’s third law of orbital motion following equation: a = ( GM ∗ T 2 4 π 2 ) 1 / 3 = ( M ∗ M ⊙ ) 1 / 3 ( T yr ) 2 / 3 AU, (9)"
 },
 {
  "path": "analysis_steps[6].method.evidence[0]",
  "value": "Calculate non-thermal dust sputtering timescale using Equation 5 for silicate and carbon dust grains, and calculate neutral molecule freeze-out timescale for CH3OH using Equation 11 to compare with observed ejection periods.",
  "failed_quote": "Following Draine & Salpeter (1979); Nozawa et al. (2006); and Hu et al. (2019), the dust sputtering time-scale can be defined as t sput ≡ a 3 n H Y tot , ≈ 0 . 33 Myr ( a µm ) ( n H cm − 3 ) − 1 ( Y tot 10 − 6 µm yr − 1 cm 3 ) − 1 , (5)"
 },
 {
  "path": "analysis_steps[6].method.evidence[1]",
  "value": "Calculate non-thermal dust sputtering timescale using Equation 5 for silicate and carbon dust grains, and calculate neutral molecule freeze-out timescale for CH3OH using Equation 11 to compare with observed ejection periods.",
  "failed_quote": "Following Charnley et al. (2001) and Rodgers & Charnley (2003), the freeze-out rate for a neutral molecule, X , can be estimated as λ ( X ) = 2 . 3 × 10 − 18 ( T m ( X ) ) 0 . 5 n H 2 ( s − 1 ) (11)"
 },
 {
  "path": "analysis_steps[6].assumptions[0].evidence[0]",
  "value": "Mean jet velocity ~ 50 km s^-1 and pre-shock density ~ 10^4 to 10^6 cm^-3 for sputtering",
  "failed_quote": "For a mean jet velocity of ∼ 50 km s − 1 , we estimate sputtering time scales of 2.75 - 275 years for silicate dust and 5.4 - 540 years in the case of carbon dust, for preshock densities ∼ 10 6 to 10 4 cm − 3 , respectively."
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Mean periods between ejection events (T_knot) = 20 - 175 years",
  "failed_quote": "We determine mean periods of ejection events of 20 − 175 years for our sample, which could be associated with perturbation zones of ∼ 2 − 25 au extent around the protostars."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Keplerian perturbation zone radius range = 2.0 - 25 au",
  "failed_quote": "The Keplerian radius corresponding to the episodes are estimated to be 2.0 − 25 au (including errorbars) for different objects (Table 4)."
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Ratio of mass-loss to mass-accretion rate (Mdot_j / Mdot_acc) = 0.003 to 2.1 dimensionless",
  "failed_quote": "The ratio of ˙ M j / ˙ M acc ranges from 0.003 to 2.1."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Binary orbital dynamics driving the accretion/ejection episodes was rejected for the wide binary systems because their separations (> 100 au) do not match the derived Keplerian perturbation radii (2 - 25 au).",
  "failed_quote": "There are three wide binary systems with separations > 100 au in the plots. None have separations matching the Keplerian perturbation radius. Hence, it is unlikely these respective accretion/ejection events are driven by binary orbital dynamics."
 }
]
```
