# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022MNRAS.510.4998Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–11 (2021) Preprint 30 September 2021 Compiled using MNRAS L [A] TEX style file v3.0

# **ATOMS: ALMA Three-millimeter Observations of Massive Star-forming** **regions -IV. Radio Recombination Lines and evolution of star formation** **efficiencies**


C. Zhang, [1] _[,]_ [2] _[¢]_ Neal J. Evans II, [3] T. Liu, [4] - J.-W. Wu, [5] _[,]_ [6] Ke Wang, [7] H.-L. Liu, [8] F.-Y. Zhu, [4] Z.-Y. Ren, [6]

L. K. Dewangan, [9] Chang Won Lee, [10] _[,]_ [11] Shanghuo Li, [10] L. Bronfman, [12] A. Tej, [13] D. Li, [6] _[,]_ [14]

1 _Department of Physics, Taiyuan Normal University, Jinzhong 030619,China_
2 _Institute of Computational and Applied Physics, Taiyuan Normal University, Jinzhong 030619,China_
3 _Department of Astronomy, The University of Texas at Austin, 2515 Speedway, Stop C1400, Austin, Texas 78712-1205, U.S.A._
4 _Shanghai Astronomical Observatory, Chinese Academy of Sciences, 80 Nandan Road, Shanghai 200030, People’s Republic of China_
5 _University of Chinese Academy of Sciences, BeÚing 100049, PR China_
6 _National Astronomical Observatories, Chinese Academy of Sciences, BeÚing, 100012, People’s Republic of China_
7 _Kavli Institute for Astronomy and Astrophysics, Peking University, 5 Yiheyuan Road, Haidian District, BeÚing 100871, People’s Republic of China_
8 _Department of Astronomy, Yunnan University, Kunming,650091, PR China_
9 _Physical Research Laboratory, Navrangpura, Ahmedabad–380 009, India_
10 _Korea Astronomy and Space Science Institute, 776 Daedeokdaero, Yuseong-gu, Daejeon 34055, Republic of Korea_
11 _University of Science and Technology, Korea, 217 Gajeong-ro, Yuseong-gu, Daejeon 34113, Republic of Korea_
12 _Departamento de Astronomía, Universidad de Chile, Casilla 36-D, Santiago, Chile_
13 _Indian Institute of Space Science and Technology, Thiruvananthapuram 695 547, Kerala, India_
14 _NAOC-UKZN Computational Astrophysics Centre, University of KwaZulu-Natal, Durban 4000, South Africa_


**ABSTRACT**



We report detection of radio recombination line (RRL) H 40 _U_ toward 75 sources, with data obtained from ACA observations
in the ATOMS survey of 146 active Galactic star forming regions. We calculated ionized gas mass and star formation rate
with H 40 _U_ line emission. The mass of ionized gas is significantly smaller than molecular gas mass, indicating that ionized gas
is negligible in the star forming clumps of the ATOMS sample. The star formation rate (SFR H 40 _U_ ) estimated with RRL H 40 _U_
agrees well with that (SFR L bol ) calculated with the total bolometric luminosity (L bol ) when SFR - 5 M ⊙ My _A_ [−][1], suggesting
that millimeter RRLs could well sample the upper part of the initial mass function (IMF) and thus be good tracers for SFR. We


0

also study the relationships between L bol and the molecular line luminosities (L [) of CS J=2-1 and HC] [3] [N J=11-10 for all the]



0

also study the relationships between L146 ATOMS sources. The L bol -L 0 [correlations] bol and the molecular line luminosities (L [of] [both] [the] [CS] [J=2-1] [and] [HC] mol [3] [N][) of CS J=2-1 and HC][J=11-10] [lines] [appear] [3] [N J=11-10 for all the][approximately] [linear]



146and these transitions have success in predicting LATOMS sources. The L bol -L 0 mol [correlations] bol [of] similar to that of more commonly used transitions. The L [both] [the] [CS] [J=2-1] [and] [HC] [3] [N] [J=11-10] [lines] [appear] [approximately] bol -to-L 0 [linear][ratios]



and these transitions have success in predicting L bol similar to that of more commonly used transitions. The L bol -to-L 0 mol [ratios]

or SFR-to-mass ratios (star formation efficiency; SFE) do not change with galactocentric distances (R GC ). Sources with H 40 _U_
emission (or Hii regions) show higher L bol -to-L 0 [than those without H] [40] _[U]_ [emission, which may be an evolutionary effect.]



0 mol [than those without H] [40] _[U]_ [emission, which may be an evolutionary effect.]



**Key words:** ISM: clouds, (ISM:) H II regions, stars: formation, radio lines: ISM



**1** **INTRODUCTION**


Stars are known to form in molecular gas, but recent works suggest
that dense gas, probed by species other than CO, provides a better
predictor of the rate of star formation (Evans 2008; Vutisalchavakul
et al. 2016). On the scale of galaxies, Gao & Solomon (2004) showed
the luminosities of IR emission (L _퐼'_ tracing the SFR) of entire
galaxies have a tighter linear correlation with the HCN (J=1-0) than
with the CO luminosity. This correlation even extends to Galactic
dense clumps undergoing high mass star-formation (Wu et al. 2005).
This so called “dense gas star formation law" suggests that the dense


_¢_ E-mail: zhangchao920610@126.com

- E-mail: liutie@shao.ac.cn


© 2021 The Authors



molecular gas rather than the total molecular gas is the direct fuel
for star formation. Such linear correlations have also been found in
other dense gas tracers (e.g. HCN J=4-3, HCO [+] J=4-3, CS J=7-6,
CS J=2-1) with similar or higher critical densities (Wu et al. 2010;
Lada et al. 2012; Zhang et al. 2014; Liu et al. 2016; Stephens et al.
2016; Tan et al. 2018; Liu et al. 2020b). Evans et al. (2014) compared
various models of star formation to observations of the nearby clouds
and found that the mass of dense gas was the best predictor of the star
formation rate. Most recently, Vutisalchavakul et al. (2016) showed
that a similar result applied to more distant and massive clouds in the
Galactic Plane.


Accurate estimates of SFRs are crucial in studying the dense gas
star formation law. Presently, a wide variety of SFR diagnostics
are used in the literature (e.g., Kennicutt 1998; Kennicutt & Evans

2 _Chao Zhang et al._


2012), each of which has its strengths and shortcomings (Murphy
et al. 2011). Among them, infrared or bolometric luminosity is commonly used in estimating SFRs in both external galaxies and Galactic clumps. Bolometric luminosity comes from heated dust grains
surrounding massive star-forming regions and does not suffer significantly from extinction. While a portion of the bolometric luminosity
will arise from dust heated by older stars (Hirashita et al. 2003; Bendo
et al. 2010; Li et al. 2010) on galaxy scales, that is not significant on
the scale of star formation regions in our Galaxy.

Hii regions are hot ionized gas surrounding exciting central OB
stars, and thus they are ideal tracers for new star formation in giant
molecular clouds. The millimeter recombination lines originating
from low energy levels (n=20–50) that would not be much affected
by potential maser amplification or dust extinction, may be reliable
and quantitative probes of the EUV continuum at 13.6 eV to above
54.6 eV (Scoville & Murchikova 2013). Strong correlation between
the integrated 6 cm radio continuum and millimeter RRL (mm-RRL)
emissions have been revealed in Galactic Hii regions (Kim et al.
2017), indicating that mm-RRLs can trace the same ionized nebula
as centimeter radio continuum. RRLs are therefore optimal tracers
of Hii regions and new star formation. The line luminosities of mmRRLs are directly proportional to the emission measures of their
ionized regions and thus can be related to the star formation rates
(Scoville & Murchikova 2013; Bendo et al. 2015, 2016, 2017; Binder
& Povich 2018a; Michiyama et al. 2020), if the initial mass function
(IMF) is well sampled. In this paper, we test the use of H 40 _U_ RRL
to trace UC Hii regions and star formation rate in Galactic massive
clumps.

We also investigate the “dense gas star formation law" with CS
J=2-1 and HC 3 N J=11-10. Liu et al. (2020b) reported that the star
formation scaling relationships of H [13] CN J=1-0 and H [13] CO [+] J=1-0
lines as well as their corresponding main lines, with data obtained
from ACA observations in the ATOMS survey, appear approximately
linear. Table 1 lists the relevant parameters for the lines studied here
and, for comparison, the lines studied by Liu et al. (2020b). CS J=2-1
and HC 3 N J=11-10 have higher effective excitation densities ( _=_ eff )
than HCN J=1-0 and HCO [+] J=1-0 (Shirley 2015), and similar to
those of the rare isotopologues, H [13] CN and H [13] CO [+] . Therefore, they
could be good tracers of more concentrated dense gas in molecular
clouds. In contrast, the total luminosity of HCN and HCO [+] _퐽_ = 1 − 0
lines can be dominated by low level emission from extended regions
(Evans et al. 2020; Liu et al. 2020a). The HC 3 N J=11-10 line has
an _=_ eff about 10 times that of CS 2-1, and it is a good tracer of
dense cores and filaments in Galactic clouds (Liu et al. 2020a). In
addition, this line as well as other high J transitions of HC 3 N are also
detectable in external galaxies (Lindberg et al. 2011; Aladro et al.
2011; Jiang et al. 2017), indicating that HC 3 N lines are potentially
good tracers for studying the "dense gas star formation law" in both
external galaxies and Galactic clouds.

The dispersion in the ratio of star formation rate to dense gas
mass (or star formation efficiency; SFE) is still substantial. Multiple
feedback mechanisms from formed OB stars can significantly reduce
star formation rates and may play a major role in determining the
star formation efficiency in molecular clouds (Krumholz et al. 2014).
In this paper, we divide 146 ATOMS clumps into two groups, i.e.,
the one with and other without H 40 _U_ emission (or Hii regions),
and investigate how formed OB stars influence the star formation
efficiency in these star forming clumps.

In section 2, we describe the observations. Section 3 presents the
results, focusing on empirical relations between bolometric and line
luminosities. We calculate star formation rates with RRLs, derive
star formation efficiencies and gas depletion times, and provide a


MNRAS **000**, 1–11 (2021)



physical interpretation for the empirical relations in Section 4. We
summarize our main conclusions in Section 5.


**2** **OBSERVATIONS**


**2.1** **The sample**


We made the ALMA observations for 146 active Galactic star form
ing regions as the ATOMS (ALMA Three-millimeter Observations
of Massive Star forming regions) survey. These 146 sources were
selected from the CS J = 2-1 survey of Bronfman et al. (1996), a
complete and homogeneous molecular line survey of ultra compact
(UC) Hii region candidates in the Galactic plane. The sample of 146
targets is complete for proto-clusters with bright CS J = 2-1 emission
(T _1_ _>_ 2 K), indicative of reasonably dense gas. More parameters of
146 targets are shown in Table A of Liu et al. (2020a). Most (139) of
the targets are located in the first and fourth Galactic Quadrants of the
inner Galactic Plane. The distances of the sample clouds range from
0.4 kpc to 13.0 kpc with a mean value of 4.5 kpc. The sample includes
27 distant (d - 7 kpc) sources that are either close to the Galactic
center or mini-starbursts, representing extreme environments for star
formation. The properties of these sources have been described in
detail in Liu et al. (2016, 2020a,b) and Liu et al. (2021).


**2.2** **ALMA ACA observations**


The data on CS J=2-1, HC 3 N J=11-10 and H 40 _U_ RRL were obtained
from the Atacama Compact 7 m Array (ACA; Morita Array) observations in the ATOMS survey. We use only ACA data to obtain a
larger FOV than we would have with the 12-m array data and the
ACA data can match clump-scale luminosity information and better
trace the overall spatial distribution of gas within these star forming
regions. The ACA observations were performed between September
to mid November in 2019 in band 3 (Project ID: 2019.1.00685.S; PI:
Tie Liu). The typical ACA observing time per source is ⇠ 8 minutes.
The angular resolution and maximum recovered angular scale for the
ACA observations are ⇠ 13 [00] _._ 1 - 13 [00] _._ 8 and ⇠ 53 [00] _._ 8 - 76 [00] _._ 2, respectively. The CS J=2-1, HC 3 N J=11-10 and H 40 _U_ are included in three
spectral windows in the upper sideband. The spectral resolution for
CS J = 2-1, HC 3 N J=11-10 and H 40 _U_ is ⇠1.5 km s [−][1] .

Calibration was carried out using CASA software package version
5.6 (McMullin et al. 2007). More details about ALMA observations
can be found in Liu et al. (2020a,b).


**3** **RESULTS**


**3.1** **Extraction of compact objects**


We extracted compact objects from the integrated intensity maps of
the three lines (CS J=2-1, HC 3 N J=11-10 and H 40 _U_ ) using an elliptical Gaussian fit. Figure 1 shows the integrated intensity maps for
two example sources. The objects in molecular line emission can be
easily identified by eye. In total, we detected 177, 185 and 75 sources
in emission from CS J=2-1, HC 3 N J=11-10 and H 40 _U_, respectively.
We also show the 3mm continuum emission for comparison, with
parameters derived by Liu et al. (2020b), in the figure.


⇠
The majority ( 80%) of targeted sources contain only one object in
molecular line emission as illustrated for I13134-6242 in Figure 1. We
identified multiple objects in 28, 32 and 4 targeted sources from CS,
HC 3 N and H 40 _U_ maps, respectively. In such sources, we separately
fit every single object using an elliptical Gaussian fit. The parameters

3
_Radio Recombination Lines and evolution of star formation efficiencies_


**Table 1.** spectral lines (The E _D_ /k and effective excitation density are from Shirley 2015).


Molecule Transition Rest frequency E _D_ /k velocity resolution n eff (15K)
(GHz) (K) (km/s) (cm [−][3] )


CS 2-1 97.980953 7.05 1.5 1.5⇥10 [4]

HC 3 N 11-10 100.07639 28.82 1.5 1.6⇥10 [5]

H _U_ H 40 _U_ 99.022952 1.5
HCN 1-0 88.631847 4.25 0.2 5.6⇥10 [3]

HCO [+] 1-0 89.188526 4.28 0.2 6.4⇥10 [2]

H [13] CN 1-0 86.339918 4.14 0.4 2.2⇥10 [5]

H [13] CO [+] 1-0 86.754288 4.16 0.4 2.7⇥10 [4]



of every single object are summarized in Tables 2 to 4. When we
calculate luminosity of the targeted source, we added all the multiple
objects to obtain the overall clump properties.

The Gaussian fits provided relative coordinates (or offsets), aspect
ratios, effective radii ( _'_ eff ), peak flux densities ( _(_ peak ) and total flux
densities ( _(_ total ). The aspect ratio is defined as the ratio between
de-convolved semi-major size (a) and semi-minor size (b), and _'_ eff
is defined as _'_ eff = ~~p~~ _01_ .



~~p~~



_'_ = _01_ .
eff

For CS, HC 3 N and H 40 _U_, the median values for _(_ peak are 65.6,
22.3 and 46.7 Jy beam [−][1] km s [−][1], respectively. The median values for
_(_ total of CS, HC 3 N and H 40 _U_ lines are 188.9, 49.8 and 53 Jy km s [−][1],
respectively. The _'_ eff of CS ranges from 0.04 pc to 1.40 pc with a
median value of 0.46 pc. The _'_ eff of HC 3 N ranges from 0.03 pc to
1.28 pc with a median value of 0.39 pc. The _'_ eff of H 40 _U_ ranges
from 0.08 pc to 0.91 pc with a median value of 0.33 pc. While the
sources have a range of sizes in each tracer, the median sizes in all
three lines are comparable.



**3.2** **Properties of the Ionized Gas**


For the sources with detections of H 40 _U_, we use the equations in
Appendix A to derive the properties of their ionized gas.

The rates of ionizations (Q 0 ) are listed in the eighth column of Table 4. The median, mean and standard deviation of _&_ 0 are 1.7 ⇥ 10 [48],
9.1 ⇥ 10 [48] and 2.5 ⇥ 10 [49] s [−][1], respectively. The median _&_ 0 corresponds to an O8.5 star, and the mean _&_ 0 corresponds to an O6 star.

The electron density (n _4_ ), calculated according to equations in
Appendix B, is listed in Table 4. The min, max, median, mean and
standard deviation of n _4_ are 543.9, 8968.8, 1465.1, 2190.5 and 1864.6
cm [−][3], respectively. Using n _4_, we could iterate by adjusting _1_ _D_ (the
departure coefficient). However, values for _1_ _D_ vary only by about
15% between _=_ _4_ = 10 [2] and 10 [4] cm [−][3], so the effect is smaller than
other uncertainties.


The masses of ionized gas, computed from equations in Appendix
B are listed in Table 4. The min, max, median, mean, and standard
deviation are 0.14, 200.74, 4.67, 16.12 and 33.71 M ⊙, respectively.


**3.3** **The L** bol **-L** 0 mol **[scaling relations]**


0

The molecular line luminosities (L mol [)] [are] [computed] [from] [the] [ob-]

served line fluxes. For comparison to single-dish work, we provide
line luminositis in K km s [−][1] pc [2], and their logarithmic values are
compiled in Table 5. The line luminosity is calculated by Equation 1
following Solomon et al. (1997):



**Figure 1.** Integrated intensity maps of two molecular lines and RRL are shown
in color images for two example sources. The 1.3 mm continuum emission is
shown in contours. Contours are from 20% to 80% in step of 20% of peak
values. The peak values of 1.3 mm continuum emission for I13080-6229 and
I13134-6242 are 1.52 and 0.15 Jy beam [−][1], respectively. The black ellipses
represent the beams in observations. The integrated intensity maps of the

other sources are available on line.


where, _!_ 0 mol [is the the molecular luminosity in K km/s pc] [2] [,] _[ (]_ [mol] [Δ] _[E]_

is the velocity-integrated flux in Jy km s [−][1], _a_ obs is the line frequency
in GHz, _⇡_ is the distance in kpc. The molecular line luminosities
are listed in Table 5.


The bolometric luminosity (L bol ) has been widely used as a tracer
of the recent star formation rate (Gao & Solomon 2004; Wu et al.
2005, 2010). L bol values for the ATOMS sources are calculated from
integrating the whole SEDs (Faúndez et al. 2004; Urquhart et al.
2018Figure) 2and, we plot the Llisted in the bol seventhas a function of the Lcolumn of Table 0 CS 5. [for the ATOMS] In left panel of

measurements (yellow dots) and literature measurements compiled
by Wu et al. (2010) (black squares). In this paper, all relations are
determined by linear least squares fits in log-log space. Relations
with slopes near unity in logarithmic fits are referred to as linear,
while those with slopes significantly less than unity are referred to as
sub-linear. The fit toward ATOMS data is shown in blue dashed line.
The fit to the Wu et al. (2010) data is shown in green dashed line.
Both indicate that the underlying relations are close to linear (the
slope of the correlation for ATOMS data alone is 0 _._ 98 ± 0 _._ 07), but
the ATOMS data lies mostly above the data from Wu et al. (2010).


MNRAS **000**, 1–11 (2021)



_!_



0 mol [=][ 32] _[.]_ [5] _[a]_ obs [−][2] _[(]_ [mol] [Δ] _[E⇡]_ [2] _[,]_ (1)

4 _Chao Zhang et al._


**Table 2.** Gas clumps identified in CS J=2-1.


IRAS ID Offset r aspect _'_ eff _(_ peak S total


( [00] _,_ [00] ) (pc) (Jy beam [−][1] km s [−][1] ) (Jy km s [−][1] )


I08076-3556 1 (-10.45,10.51) 2.13 0.04 8.83 17.96
I08303-4303 1 (-12.53,4.81) 1.60 0.32 51.08 235.24
I08448-4343 1 (-25.63,11.31) 1.63 0.06 28.06 44.69
2 (-4.87,0.50) 1.63 0.08 50.29 150.51
I08470-4243 1 (-8.87,4.34) 1.59 0.25 79.57 284.97
I09002-4732 1 (-12.60,-10.59) 1.22 0.08 55.45 66.30
2 (22.74,21.83) 2.85 0.13 41.40 122.80
I09018-4816 1 (-3.39,2.86) 1.44 0.36 61.93 289.05


The full catalogue is available on line.


**Table 3.** Gas clumps identified in HC 3 N J=11-10.


IRAS ID Offset r aspect _'_ eff _(_ peak S total


( [00] _,_ [00] ) (pc) (Jy beam [−][1] km s [−][1] ) (Jy km s [−][1] )


I08076-3556 1 (-13.23,15.46) 1.57 0.05 4.77 16.10
I08303-4303 1 (-7.89,6.78) 1.28 0.23 23.39 59.88
I08448-4343 1 (-30.00,15.63) 1.38 0.07 9.27 22.64
2 (-2.87,1.28) 1.95 0.09 7.84 34.30
I08470-4243 1 (-11.47,2.84) 1.84 0.27 12.00 54.28
I09002-4732 1 (-12.29,-9.42) 1.64 0.09 14.75 19.80
2 (22.95,-11.31) 1.59 0.09 8.64 13.21
3 (-11.32,-40.54) 3.36 0.14 6.86 22.13


The full catalogue is available on line.


**Table 4.** Gas clumps identified in H 40 _U_ .


IRAS ID Offset r aspect _'_ eff _(_ peak S total log(Q 0 ) log(n _4_ ) log(M _8>=_ )


( [00] _,_ [00] ) (pc) (Jy beam [−][1] km s [−][1] ) (Jy km s [−][1] ) (s [−][1] ) (cm [−][3] ) (M ⊙ )


I09002-4732 1 (-0.27,-9.30) 1.57 0.08 116.85 112.35 47.91 3.89 -0.35
I12320-6122 1 (2.45,7.31) 1.79 0.20 22.78 17.29 48.01 3.30 0.34
I12326-6245 1 (-2.10,0.43) 1.77 0.28 93.81 75.88 48.91 3.53 1.00
I12383-6128 1 (-3.82,-3.39) 2.39 0.22 3.31 3.14 47.23 2.86 -0.01
I13080-6229 1 (-1.74,-1.62) 1.37 0.33 41.98 63.72 48.67 3.31 0.98
I13291-6229 1 (9.30,14.82) 1.48 0.21 3.47 3.52 47.17 2.86 -0.06
2 (-24.63,-6.96) 2.11 0.17 3.91 2.56 47.04 2.94 -0.27
I13291-6249 1 (1.20,2.00) 1.89 0.52 16.63 15.16 48.65 3.00 1.27
I13471-6120 1 (2.70,5.33) 1.02 0.36 38.19 32.75 48.69 3.26 1.05


The full catalogue is available on line.



This may be due to different source selection in the two samples.
In particular, the ATOMS sample has a higher average bolometric
luminosity than the sample in Wu et al. (2010). In addition, ACA
observations filter out very extended emission and only detect the
dense parts of clumps, an effect that leads to a lower molecular line
luminosity than in single dish observations.


In Figure 2(b), we plot L bol as a function of the L 0 HC 3 N [for] [the]

ATOMS measurements (green dots). The relation also has a slope
near unity (0.96 ± 0.08). It suggests that HC 3 N J=11-10 can also trace
dense gas and be used for studying star formation scaling relations.


MNRAS **000**, 1–11 (2021)



**3.4** **The L** bol **-to-L** 0 mol **[ratios]**



L bol -to-L 0 mol [ratios is often interpreted in terms of the star formation]

efficiency (SFE). In this section, we investigate how L bol -to-L 0



L bol -to-L



efficiency (SFE). In this section, we investigate how L bol -to-L 0 mol

ratios changes in different Galactic environments and how formed
Hii regions affect these ratios.

Figure 3 plots the ratio, L bol -to-L 0 mol [versus] [Galactocentric] [dis-]

tances (R(2019) found SFE traced by L GC, compiled by Liu et al. 2020a bol -to-L 0 [tends to increase with in-] ). Jiménez-Donaire et al.



Figure 3 plots the ratio, L bol -to-L



(2019) found SFE traced by L bol -to-L 0 mol [tends to increase with in-]

creasing R GC in most of their targeted external galaxies. Eden et al.
(2015) also show that ratio of infrared luminosity to the mass of
the clump is enhanced in spiral arms compared to the interarm regions when averaged over kiloparsec scales. However, there is no

5
_Radio Recombination Lines and evolution of star formation efficiencies_


**Figure 2.** L bol - L 0 mol [relations for CS J=2-1 (left panel) and HC] [3] [N J=11-10 (right panel). In panel (a), the data for ATOMS are shown as yellow dots. The black]

cube represent literature measurements compiled by Wu et al. (2010). The linear fit toward ATOMS data is shown in blue dashed line. The slope and offset of
blue dashed line are 0.98 ± 0.07 and 3.83 ± 0.08. The linear fit toward Wu et al. (2010) data is shown in a green dashed line. The slope and offset of green dashed
line are 1.05 ± 0.08 and 3.11 ± 0.15. In panel (b), the data for ATOMS are shown as green dots. The linear fit toward HC 3 N data is shown in black dashed line.
The slope and offset of black dashed line are 0.96 ± 0.08 and 4.45 ± 0.06. The red crosses in both panels show the ATOMS sources that are detected in H 40 _U_
emission.


**Table 5.** Luminosities of sources.



Distance R GC log(L bol ) log(L 0 CS [)] log(L 0 HC 3 N [)]

(kpc) (kpc) (L ⊙ ) (K km/s pc [2] ) (K km/s pc [2] )



0 CS [)] log(L



ID IRAS RA DEC Distance R GC log(L bol ) log(L



1 I08076-3556 08:09:32.39 -36:05:13.2 0.4 8.5 1.20 -2.01 -2.08

2 I08303-4303 08:32:08.34 -43:13:54.0 2.3 9.0 3.83 0.62 0.01

3 I08448-4343 08:46:32.90 -43:54:35.9 0.7 8.4 3.04 -0.49 -1.04

4 I08470-4243 08:48:47.07 -42:54:31.0 2.1 8.8 4.04 0.63 -0.11

5 I09002-4732 09:01:54.24 -47:44:00.8 1.2 8.4 4.59 -0.04 -0.59

6 I09018-4816 09:03:32.84 -48:28:10.0 2.6 8.8 4.72 0.82 0.39

7 I09094-4803 09:11:07.29 -48:15:48.7 9.6 12.7 4.60 1.34 -0.19

8 I10365-5803 10:38:32.46 -58:19:05.9 2.4 8.0 4.28 0.41 0.09

9 I11298-6155 11:32:05.70 -62:12:24.3 10 10.1 5.23 1.49 0.44


The full catalogue is available on line.



clear trend for L bol -to-L 0 mol [ratios] [against] [R] [GC] [in] [our] [study.] [Liu]

et al. (2020b) also showed similar results with J = 1-0 transitions of
H [13] CN, H [13] CO [+], HCN and HCO [+] . We also show these ratios for
tworately.groupsAgain,(withthereandis withoutno clearHtrend 40 _U_ emissionfor L bol -to-Lor Hii 0 regions) [ratios] [against] sepa


clear trend for L bol -to-L



rately. Again, there is no clear trend for L bol -to-L 0 mol [ratios] [against]

R GC whether or not UC Hii regions have formed. A number of other
studies (Eden et al. 2013; Ragan et al. 2018; Urquhart et al. 2021)
also found that the distribution of the dense gas fraction in Galactic
giant molecular clouds is relatively flat across the disc and there is no
evidence of any significant enhancements that might be attributable
to spiral arms.


We present the log(L bol -to-L 0 mol [) distributions of different molec-]

ular line tracers in Figure 4 for two groups of sources, i.e., those with
and without H 40 _U_ emission (or Hii regions). Line luminosities for
the J = 1-0 transitions of H [13] CN, H [13] CO [+], HCN and HCO [+] were
compiled in Liu et al. (2020b). We test whether the log(L bol -to-L 0 [)]



values for clumps with Hii regions or without Hii regions could be
drawn from the same distribution with Kolmogorov–Sminov test.
The p-values from Kolmogorov–Sminov tests are summerized in the
lasttracerscolumnare nearof Tableto zero.6. AllThistheimpliesp-valuethatfor differentL bol -to-Lmolecular 0 [ratios] line [(or]



tracers are near to zero. This implies that L bol -to-L 0 mol [ratios] [(or]

SFE) for sources with and without H 40 _U_ emission are significantly
different.significantly larger LIn other words, bol -to-Lclumps 0 [ratios.] associated with Hii regions show



0 mol [ratios.]



We list the min, max, mean, median, standard deviation (std) of
log(L bol -to-L 0 [)] [for] [different] [tracers] [in] [Table] [6][.] [For] [every] [tracer,]



We present the log(L bol -to-L



log(L bol -to-L 0 mol [)] [for] [different] [tracers] [in] [Table] [6][.] [For] [every] [tracer,]

the first row shows the parameters for all the ATOMS sources. The
second row shows data for sources with H 40 _U_ emission and the
thirdlog(L bol row-to-Lfor 0 sources [) ratios between two samples offset by] without H 40 _U_ emission. The mean [ ⇠][0.5 dex. In] values of



0
mol [)]



log(L bol -to-L 0 mol [) ratios between two samples offset by][ ⇠][0.5 dex. In]

fact, this offset is remarkably constant over all tracers with a mean
value of 0 _._ 52 ± 0 _._ 04. We will discuss physical explanations for these



MNRAS **000**, 1–11 (2021)

6 _Chao Zhang et al._


different distributions for sources with and without H 40 _U_ emission
in Section 4.


**4** **DISCUSSION**


**4.1** **Star formation rates**


Star formation rates in other galaxies are routinely estimated from a
variety of indicators, including the bolometric luminosity and tracers
of ionization by massive stars, such as recombination lines. These
methods rely on models of star formation that extend over a long
period and fully sample the initial mass function. Application of
these models to individual regions of star formation in the Milky
Way is not rigorously justified, but agreement between tracers with
different dependence on the duration and IMF sampling provide
empirical support for their use (e.g., Vutisalchavakul et al. 2016).

Using L bol values listed in the seventh column of Table 5, following Kennicutt & Evans (2012) but converting from M ⊙ yr [−][1] to
M ⊙ Myr [−][1], we can relate L bol to SFR as:


_(퐹'_ _!_ bol
log( [)] [=][ log][(] [) −] [37] _[.]_ [41] (2)

M ⊙ Myr [−][1] ergs s [−][1]


The star formation rates (SFR bol ) derived from the L bol are listed in
the fifth column of Table 7.

Millimeter or submillimter RRLs provide a relatively new way to
estimate star formation rates (SFRs), so far mostly in external galaxies (Yun et al. 2004; Scoville & Murchikova 2013; Bendo et al. 2016,
2017; Michiyama et al. 2020). Here we test their use in Galactic
regions by comparing with SFRs estimated from bolometric luminosities. For the 75 sources with H 40 _U_ line detections, we estimate
their SFRs with H 40 _U_ integrated line flux density ( _(_ Δ _E_ ) using the
equations in the Appendix A. These SFR H 40 _U_ are given in Table 7.

Vutisalchavakul et al. (2016) found a slightly sub-linear correlation (slope 0.8) with SFR of radio continuum data and bolometric
luminosity. The slightly sub-linear correlation can result from the
fact that the radio continuum emission is more sensitive to the upper
end of the IMF, as can be seen from Kennicutt & Evans (2012) and
Vutisalchavakul et al. (2016). H 40 _U_ emission also requires stars producing EUV photons with energy above 13.6 eV. Kim et al. (2017)
has found a strong correlation between the integrated 6 cm radio
continuum and millimeter RRL emission in Galactic Hii regions,
indicating that H 40 _U_ emission could also well trace the upper end of
the IMF.


In addition, L bol also begins to underestimate the SFRs for sources
with SFRs less than about 5 M ⊙ My _A_ [−][1], corresponding to a total
far-infrared luminosity of 10 [4] _[.]_ [5] L ⊙ (Wu et al. 2005; Vutisalchavakul
& Evans 2013; Vutisalchavakul et al. 2016). Wu et al. (2005) found
a rapid drop in SFR below _!_ bol = 10 [4] _[.]_ [5] L ⊙, due to poor sampling
of the upper part of the IMF. Therefore, we use only sources with
SFR H 40 _U_ - 5 M ⊙ My _A_ [−][1] and SFR bol - 5 M ⊙ My _A_ [−][1] for comparison.
We plot the ratio SFR H 40 _U_ /SFR bol versus SFR bol in Figure 5. The
mean, median and std of the log values of SFR H 40 _U_ /SFR bol ratio are
−0 _._ 01, 0.02 and 0.29, respectively. While both estimates of SFR are
uncertain, the excellent agreement suggests that either can provide
an estimate of the SFR. There is no obvious dependence of the ratio
on SFR bol for values above 5 M ⊙ Myr [−][1] .


**4.2** **The differences between sources with and without H** 40 _U_

**emission**


Figure 4 shows that L bol -to-L 0 mol [ratios for sources with and without]

H 40 _U_ emission are significantly different, indicating that the star


MNRAS **000**, 1–11 (2021)



formation efficiency (SFE) of these clumps may be very different.
Recently, Elia et al. (2021) found large difference in the L bol -tomass ratios (also tracing SFEs) between Hii region candidates and
protostellar objects in Hi-GAL compact sources. The masses of HiGAL compact sources are estimated from dust continuum emission.
They find that the median value of log(L bol /mass) for Hii region
candidates is about 20 times larger than that for protostellar objects.
This factor is much larger than what we find here for ATOMS sources.
This is because they include many more evolved Hii regions, some
of which may have broken out of the dense clump. In contrast, the
Hii region candidates in the ATOMS sample are mostly in the ultracompact Hii region phase.


Before exploring the evolutionary explanation, we consider an
alternative explanation. Perhaps a large amount of gas has been ionized or dispersed by formed OB stars (Hii regions) and this gas is no
longer counted in the molecular emission. We can investigate how
much gas has been ionized in the ATOMS sources. The mass of
ionized gas in an Hii region with 27% helium can be estimated with
total flux of H 40 _U_ by equations in Appendix B. The mass of ionized
gas is summarized in Table 4 and Table 7. For the 4 sources with
multiple objects, we add M ion to get the total ionized gas masses.
Then we derive the ionized gas mass to molecular gas mass ratios.
Because neither the molecular lines nor 3 mm continuum emission

in the ATOMS data are well calibrated to determine mass, we use
the masses of molecular gas (M mol or M clump ) compiled by Liu et al.
(2020a), which are estimated from dust continuum observations with
single dishes. The masses of molecular gas (M mol or M clump ) are
shown in the 7th column of Table 7. Left panel in figure 6 shows the
distribution of log(M _8>=_ /M mol ). The min, max, mean, median and
std of the log values of M _8>=_ /M mol are -4.56, -1.90, -2.70, -2.66 and
0.47, respectively. The median mass of ionized gas is a factor of ⇠500
smaller than the median molecular mass, indicating that ionized gas
is negligible for the ATOMS sources.


The next step is to estimate the gas depletion time
_g_ _34?_ =Mass/SFR. We investigate the difference in _g_ _34?_ between
sources with and without Hii regions. Figure 7 shows the correlation between total gas mass of clumps and _g_ _34?_ . We only focus on
sources with SFRavoid the underestimations of SFRs. Middle and right panels in fig- _퐻_ 40 _U_ - 5 M ⊙ My _A_ [−][1] or SFR bol - 5 M ⊙ My _A_ [−][1] to
ure 6 show the distribution of log( _g_ _34?_ ) for sources with and without
H 40 _U_ emission. The median, mean and std of log( _g_ _34?_ /Myr) of all
sources are 2.09, 2.15 and 0.35, respectively. For sources associated
with Hii regions, the median, mean and std of log( _g_ _34?_ /Myr) are
1.98, 2.05 and 0.32, respectively. For sources without Hii regions,
the median, mean and std of log( _g_ _34?_ /Myr) are 2.26, 2.31 and 0.33,
respectively. Thus depletion times are shorter by about 0.25 dex for
sources with Hii regions. Wu et al. (2010) also found a decreasing
trend in _g_ _34?_ (or increasing trend in SFE) from clouds without Hii
regions to those with UC Hii regions to those with compact Hii
regions to those with larger Hii regions.


The shorter _g_ _34?_ or higher SFE for sources with H 40 _U_ emission
is not caused simply by turning molecular gas into ionized gas. The
SFE may be higher in clumps with H 40 _U_ because the IMF is better
sampled and OB stars are needed for ionization. The argument against
this is that H 40 _U_ and L bol predict similar SFR over the whole range
of SFR as long as SFR > 5 M ⊙ My _A_ [−][1] . The most likely explanation
is that the SFE is higher in regions with H 40 _U_ emission simply
because star formation has proceeded further from massive, but not
yet ionizing, protostars to the formation of OB stars. In other word,
this is an evolutionary effect.

7
_Radio Recombination Lines and evolution of star formation efficiencies_



0
mol [) for different tracers. For every tracer, the first row shows the parameters for all the log(L] [bol] [/ L]



**Table 6.** Statistics of log(L bol /L 0 mol [) for different tracers. For every tracer, the first row shows the parameters for all the log(L] [bol] [/ L] 0 mol [) data. The second row for]

data with H 40 _U_ emission and the third row for data without H 40 _U_ emission.



**Table 6.** Statistics of log(L bol /L



Molecule H 40 _U_ min max mean median std p-value


CS(2-1) 2.77 5.67 3.80 3.76 0.49 1.86e-8

Y 3.34 5.67 4.05 3.98 0.45

N 2.77 4.72 3.56 3.53 0.41


HC 3 N(11-10) 2.70 6.64 4.44 4.36 0.55 1.10e-10

Y 3.73 6.64 4.73 4.67 0.50

N 2.70 5.28 4.15 4.17 0.43


H [13] CN(1-0) 3.43 6.63 4.38 4.32 0.50 2.97e-7

Y 3.87 6.63 4.64 4.54 0.49

N 3.43 5.30 4.16 4.16 0.39


H [13] CO [+] (1-0) 3.26 6.53 4.59 4.57 0.52 9.01e-9

Y 4.03 6.53 4.87 4.84 0.49

N 3.26 5.36 4.35 4.30 0.41


HCN(1-0) 2.47 5.53 3.67 3.63 0.53 3.81e-7

Y 3.12 5.53 3.96 3.98 0.47

N 2.47 4.55 3.43 3.39 0.45


HCO [+] (1-0) 2.43 5.57 3.86 3.80 0.53 5.95e-5

Y 3.30 5.57 4.12 4.08 0.48

N 2.43 4.72 3.63 3.62 0.46


**Figure** **3.** L bol -to-L mol ratios as a function of galactocentric distances (R GC ). The red and green dots represent sources with (red) or without (green) H 40 _U_

emission.


MNRAS **000**, 1–11 (2021)

8 _Chao Zhang et al._


**Figure** **4.** Density distributions of L bol -to-L 0 mol [ratios.] [The] [red] [and] [green] [histograms] [represent] [sources] [with] [H] [40] _[U]_ [emission] [and] [without] [H] [40] _[U]_ [emission,]

respectively.


**Table 7.** SFRs and gas masses of ATOMS sources.


ID IRAS R eff log(L H 40 _U_ ) log(SFR bol ) log(SFR H 40 _U_ ) log(M clump ) log(M ion )
(pc) (Jy km/s kpc [2] ) (M ⊙ Myr [−][1] ) (M ⊙ Myr [−][1] ) (M ⊙ ) (M ⊙ )


1 I08076-3556 0.04           - -2.62           - 0.7           
2 I08303-4303 0.16           - 0.00           - 2.4           
3 I08448-4343 0.07           - -0.78           - 1.6           
4 I08470-4243 0.16           - 0.22           - 2.4           
5 I09002-4732 0.12 3.31 0.77 0.79 2.4 -0.35

6 I09018-4816 0.22           - 0.89           - 3.0           
7 I09094-4803 0.70           - 0.78           - 3.1           
8 I10365-5803 0.22           - 0.45           - 2.7           
9 I11298-6155 0.68           - 1.41           - 3.4           

The full catalogue is available on line.



**5** **CONCLUSION**


In this paper, we have studied 146 ATOMS sources using CS J=2-1,
HCand L 3 N J=11-10 and H 0 40 _U_ . We found empirical relations between L bol

mol [. We calculate SFR with H] [40] _[U]_ [, compare relations between]
SFR L bol and SFR H 40 _U_, and derive gas depletion times. Our main
results are summarized as follows:


(i) We extracted 177, 185 and 75 compact sources from CS J=2-1,
HC 3 N J=11-10 and H 40 _U_, respectively.

line(ii)luminositiesThe correlations between LL 0 mol [of] [the] [CS] bol [J=2-1], tracing the SFR, and molecular [and] [HC] [3] [N] [J=11-10] [appear]

linear. Both of these two lines can be used to trace dense gas.

(iii) The L bol -to-L 0 mol [ratios stays constant against R] [GC] [ suggesting]

that SFE at the clump scale does not depend on R GC .


MNRAS **000**, 1–11 (2021)



gions) show higher L(iv) The star forming bol -to-Lclumps 0 [ratios (or SFE) than those without] with H 40 _U_ emission (thus Hii re


gions) show higher L bol -to-L 0 mol [ratios (or SFE) than those without]

H 40 _U_ emission. The mean values of log(L bol -to-L 0 [) ratios between]



H 40 _U_ emission. The mean values of log(L bol -to-L 0 mol [) ratios between]

the two sub-samples are offset by ⇠0.5 dex.


(v) The SFRs calculated from H 40 _U_ RRL and L bol are very similar
to each other on average, encouraging their use.


(vi) The mass of ionized gas is a factor of ⇠500 below the molecular mass, indicating that the higher star formation rate per unit mass
for regions associated with Hii regions is not caused simply by ionizing more gas.


(vii) A plausible explanation for the higher SFEs (or shorter _g_ _34?_ )
for clumps associated with Hii regions is that the SFE is higher simply
because the region is more evolved.

9
_Radio Recombination Lines and evolution of star formation efficiencies_



**Figure 5.** The logarithm of the ratio, SFR _퐻_ 40 _U_ /SFR bol, is plotted versus the
logarithm of SFR bol . The green, yellow and orange lines represent the log
of mean, median and std of SFR _퐻_ 40 _U_ /SFR bol . We use only sources with
SFR H 40 _U_ - 5 M ⊙ My _A_ [−][1] and SFR bol - 5 M ⊙ My _A_ [−][1] for comparison.


**Figure 6.** The Distribution of M ion /M mol and _g_ _34?_ from left to right. The red
represents clumps with H 40 _U_ and green represents the clumps without H 40 _U_
emission, respectively. For the middle and right panels, we use only sources
with SFR H 40 _U_ - 5 M ⊙ My _A_ [−][1] and SFR bol - 5 M ⊙ My _A_ [−][1] .


**ACKNOWLEDGEMENTS**


This work was partially supported by National Natural Science Foundation of China (NSFC) through grants No. 11988101, No.12073061,
and No.12122307. NJE thanks the Department of Astronomy at the
University of Texas at Austin for research support. Tie Liu acknowledges the supports by the international partnership program of Chinese academy of sciences through grant No.114231KYSB20200009,
and Shanghai Pujiang Program 20PJ1415500. C.W.L. is supported
by Basic Science Research Program through the National Research Foundation of Korea (NRF)funded by the Ministry of Education, Science and Technology(NRF-2019R1A2C1010851). J.W.
acknowledge support from National Key RD Program of China grant
No.2017YFA0402600.



**Figure** **7.** The correlation between _g_ _34?_ and mass of molecular cloud add
mass of H 40 _U_ emission area. The red and green crosses represent sources with
H 40 _U_ emission and without H 40 _U_ emission, respectively. We use only sources
with SFR H 40 _U_ - 5 M ⊙ My _A_ [−][1] and SFR bol - 5 M ⊙ My _A_ [−][1] for comparison.


**DATA AVAILABILITY**


The data underlying this article are available in the article and in its
online supplementary material.


**REFERENCES**


Aladro R., Martín-Pintado J., Martín S., Mauersberger R., Bayet E., 2011,

A&A, 525, A89

Bendo G. J., et al., 2010, A&A, 518, L65

Bendo G. J., Beswick R. J., D’Cruze M. J., Dickinson C., Fuller G. A.,


Muxlow T. W. B., 2015, MNRAS, 450, L80

Bendo G. J., Henkel C., D’Cruze M. J., Dickinson C., Fuller G. A., Karim


A., 2016, MNRAS, 463, 252
Bendo G. J., Miura R. E., Espada D., Nakanishi K., Beswick R. J., D’Cruze

M. J., Dickinson C., Fuller G. A., 2017, MNRAS, 472, 1239
Binder B. A., Povich M. S., 2018a, ApJ, 864, 136
Binder B. A., Povich M. S., 2018b, ApJ, 864, 136
Brocklehurst M., 1971, MNRAS, 153, 471
Bronfman L., Nyman L. A., May J., 1996, A&AS, 115, 81
Draine B. T., 2011, Physics of the Interstellar and Intergalactic Medium
Eden D. J., Moore T. J. T., Morgan L. K., Thompson M. A., Urquhart J. S.,

2013, MNRAS, 431, 1587
Eden D. J., Moore T. J. T., Urquhart J. S., Elia D., Plume R., Rigby A. J.,

Thompson M. A., 2015, MNRAS, 452, 289
Elia D., et al., 2021, MNRAS, 504, 2742
Evans N. J. I., 2008, in Knapen J. H., Mahoney T. J., Vazdekis A., eds,

Astronomical Society of the Pacific Conference Series Vol. 390, Pathways
Through an Eclectic Universe. p. 52 ( `arXiv:0706.4116` )
Evans Neal J. I., Heiderman A., Vutisalchavakul N., 2014, ApJ, 782, 114
Evans Neal J. I., Kim K.-T., Wu J., Chao Z., Heyer M., Liu T., Nguyen-Lu’o’ng

Q., Kauffmann J., 2020, ApJ, 894, 103
Faúndez S., Bronfman L., Garay G., Chini R., Nyman L. Å., May J., 2004,

A&A, 426, 97
Gao Y., Solomon P. M., 2004, ApJ, 606, 271
Hirashita H., Buat V., Inoue A. K., 2003, A&A, 410, 83
Jiang X.-J., Wang J.-Z., Gao Y., Gu Q.-S., 2017, A&A, 600, A15
Jiménez-Donaire M. J., et al., 2019, ApJ, 880, 127
Kennicutt Robert C. J., 1998, ApJ, 498, 541
Kennicutt R. C., Evans N. J., 2012, ARA&A, 50, 531


MNRAS **000**, 1–11 (2021)

10 _Chao Zhang et al._


Kim W. J., Wyrowski F., Urquhart J. S., Menten K. M., Csengeri T., 2017,

A&A, 602, A37
Kroupa P., Weidner C., 2003, ApJ, 598, 1076
Krumholz M. R., et al., 2014, in Beuther H., Klessen R. S., Dullemond C. P.,

Henning T., eds, Protostars and Planets VI. p. 243 ( `arXiv:1401.2473` ),
doi:10.2458/azu_uapress_9780816531240-ch011
Lada C. J., Forbrich J., Lombardi M., Alves J. F., 2012, ApJ, 745, 190
Leitherer C., et al., 1999, ApJS, 123, 3
Li Y., Calzetti D., Kennicutt R. C., Hong S., Engelbracht C. W., Dale D. A.,

Moustakas J., 2010, ApJ, 725, 677
Lindberg J. E., Aalto S., Costagliola F., Pérez-Beaupuits J. P., Monje R.,

Muller S., 2011, A&A, 527, A150
Liu T., et al., 2016, ApJ, 829, 59
Liu T., et al., 2020a, MNRAS, 496, 2790

Liu T., et al., 2020b, MNRAS, 496, 2821

Liu H.-L., et al., 2021, MNRAS, 505, 2801
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw

R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
Michiyama T., Iono D., Nakanishi K., Ueda J., Saito T., Yamashita T., Bolatto

A., Yun M., 2020, ApJ, 895, 85
Murphy E. J., et al., 2011, ApJ, 737, 67
Peters T., Longmore S. N., Dullemond C. P., 2012, MNRAS, 425, 2352
Ragan S. E., Moore T. J. T., Eden D. J., Hoare M. G., Urquhart J. S., Elia D.,

Molinari S., 2018, MNRAS, 479, 2361
Scoville N., Murchikova L., 2013, ApJ, 779, 75
Shirley Y. L., 2015, PASP, 127, 299
Solomon P. M., Downes D., Radford S. J. E., Barrett J. W., 1997, ApJ, 478,


144

Stephens I. W., Jackson J. M., Whitaker J. S., Contreras Y., Guzmán A. E.,

Sanhueza P., Foster J. B., Rathborne J. M., 2016, ApJ, 824, 29
Tan Q.-H., et al., 2018, ApJ, 860, 165
Urquhart J. S., et al., 2018, MNRAS, 473, 1059
Urquhart J. S., et al., 2021, MNRAS, 500, 3050
Vutisalchavakul N., Evans Neal J. I., 2013, ApJ, 765, 129
Vutisalchavakul N., Evans Neal J. I., Heyer M., 2016, ApJ, 831, 73
Wu J., Evans Neal J. I., Gao Y., Solomon P. M., Shirley Y. L., Vanden Bout

P. A., 2005, ApJ, 635, L173
Wu J., Evans Neal J. I., Shirley Y. L., Knez C., 2010, ApJS, 188, 313
Yun M., Scoville N., Shukla H., 2004, in Aalto S., Huttemeister S., Pedlar

A., eds, Astronomical Society of the Pacific Conference Series Vol. 320,
The Neutral ISM in Starburst Galaxies. p. 27
Zhang Z.-Y., Gao Y., Henkel C., Zhao Y., Wang J., Menten K. M., Güsten R.,

2014, ApJ, 784, L31
Zhu F.-Y., Zhu Q.-F., Wang J.-Z., Zhang J.-S., 2019, ApJ, 881, 14


**APPENDIX A:** **FROM RADIO RECOMBINATION LINES**

**TO STAR FORMATION RATES**


To derive star formation rates (SFR) from a Radio Recombination
Line (RRL), the following steps are followed. For each step, we note
assumptions and uncertainties.

(i) The total flux density ( _(_ Δ _E_ ) and effective radius _'_ eff are derived from an elliptical Gaussian fit to the integrated intensity image
of H 40 _U_ emission. The linewidth is checked for consistency with
expectations for an Hii region. In ATOMS Paper III (Liu et al. 2021),
we noted that the linewidth of H 40 _U_ line increases with decreasing
size, suggesting that pressure broadening or dynamical motions could
be important in the most compact sources. However the linewidths
were generally consistent with primarily thermal broadening in Hii
regions, and there is no evidence in the linewidths of strong maser
emission.

(ii) The line luminosity is computed from the total flux density


MNRAS **000**, 1–11 (2021)



and the distance:


_!_ (H 40 _U_ ) = 4 _c⇡_ [2] _(_ Δ _E_ (A1)


Uncertainties in distance can introduce major uncertainties because
_!_ / _⇡_ [2] . The distances to sources were taken from Paper I of this series (Liu et al. 2020a). In Paper III (Liu et al. 2021), We recalculated
distances with new kinematic models and found only minor differences, but were able to assess the median uncertainty in distance to
be 7%.


(iii) The total rate of recombinations is computed from _'_ rec =
_=_ _4_ _=_ _?_ _+U_ B, where _+_ is the volume and _U_ B is the Case B total recombination coefficient. We neglect ionizations of helium at this point.
The line luminosity (in frequency units) is _!_ _a_ (H 40 _U_ ) = _=_ _4_ _=_ _?_ _+n_,
where _!_ _a_ (H 40 _U_ ) = _!_ (H 40 _U_ ) _a_ / _2_ and _n_ is the efficiency for producing H 40 _U_ photons per recombination. So, we have

_'_ rec = _!_ _a_ (H 40 _U_ ) _[U]_ _n_ [B] _[,]_ (A2)


At _)_ _4_ = 10 [4] K, _U_ B = 2 _._ 54 ⇥ 10 [−][13] and the dependence on temperature is rather weak (equation 14.6 of 2011piim.book.....D). We
assume _)_ _4_ = 10 [4] K. The efficiency factor is


_n_ = _1_ _D_ _5_ _D_ ( _!)⇢_ ) _퐴_ _D;_ _⌘a_ _D;_ (A3)


where _5_ _D_ ( _!)⇢_ ) is the fractional population of level _D_ in LTE, _1_ _D_
is the departure coefficient, _퐴_ _D;_ is the spontaneous emission coefficient, and _a_ _D;_ is the frequency of the transition. The value of _n_
comes from calculations of excitation including recombination, radiative, and collisional processes. We assume that any maser effects
are weak, so the uncertainties are less than those introduced by the
distance uncertainties. Ideally, we would check other RRLs for signs
of anomalous excitation, but lacking those, we rely on theory. From
various sources, we determine that _1_ _D_ = 0 _._ 7866 (Zhu et al. 2019),

_5_ _D_ ( _!)⇢_ ) = 7 _._ 03 ⇥ 10 [−][19] (Peters et al. 2012), _퐴_ _D;_ = 54 _._ 7973 s [−][1]

(Brocklehurst 1971), and _a_ _D;_ = 99 _._ 023 ⇥ 10 [9] Hz (Liu et al. 2020a),
yielding _n_ = 1 _._ 99 ⇥ 10 [−][32] . _5_ _D_ ( _!)⇢_ ) depends on the electron temperature, _)_ _4_ and _1_ _D_ depends on both _)_ _4_ and _=_ _4_ . We assume _)_ _4_ = 10 [4]

K and _=_ _4_ = 10 [4] cm [−][3] . From figure 1 of Zhu et al. (2019), we estimate variations of about 10% for densities as low as 100 cm [−][3] and

temperatures as low as 5000 K. If the line is masing, the value of _n_
could be much higher. We think this is unlikely to be a major effect
for this transition, but further calculations are underway (J-Z Wang,
personal communication).

(iv) The production rate of ionizing photons is derived from the
_'_ rec by assuming that the rate of ionizations ( _&_ 0 ) equals the rate
of recombinations, ignoring helium ionizations. This is the usual
assumption because steady state is achieved rapidly, with a recombination timescale of _C_ rec = 1 _._ 22 ⇥ 10 [3] / _=_ 2 yr, where _=_ 2 is the density in
units of 100 cm [−][3] . This is much shorter than the dynamical timescale
for expansion, _C_ dyn = _'_ S / _2_ s = 2 _._ 39 ⇥ 10 [5] ⇥ _&_ [1] 0 [/] _,_ 49 [3] [/] _[=]_ 2 [2][/][3] yr, where

_&_ 0 _,_ 49 is the production rate of ionizing photons in units of 1 ⇥ 10 [49]

s [−][1], corresponding to an O6V star. These are equations 15.7 and 15.8
from Draine (2011). For the mean values of _=_ _4_ and _&_ 0, we estimate
_C_ rec = 6 yr and _C_ dyn = 1 _._ 9 ⇥ 10 [6] yr, so the assumption of steady
state seems safe. However, these textbook results can be wrong in
extreme circumstances, especially at very early times or in very inhomogenous environments. Another issue is that some of the ionizing
photons may be absorbed by dust. Binder & Povich (2018b) found
that about 34% of the ionizing photons were absorbed by dust in
their study of 28 massive Galactic regions. Both these effects would
cause an underestimate in the ionization rate.




[1] 0 [/] _,_ 49 [3] [/] _[=]_ 2 [2][/][3]



2 yr, where



_&_ 0 _,_ 49 is the production rate of ionizing photons in units of 1 ⇥ 10 [49]



(v) The production rate of ionizing photons is related to the presence of massive stars. Assuming a well-sampled IMF and a timescale

11
_Radio Recombination Lines and evolution of star formation efficiencies_


long enough that the birth and death of massive stars have reached
steady state, the ionization rate can be related to the SFR. Based
on Starburst99 (Leitherer et al. 1999) models by Binder & Povich
(2018b), using a IMF model from Kroupa & Weidner (2003), we

assume



_(퐹'_ ( _퐻_ 40 _U_ )



(A4)
_n_



M ⊙ Myr 40 [−] _U_ [1] [=][ 7] _[.]_ [5][ ⇥] [10] [−][48] _[&]_ [0] [=][ 7] _[.]_ [5][ ⇥] [10] [−][48] _[!]_ _[a]_ [(][H] [40] _[U]_ [)] _[U]_ _n_ [B]



For the values of frequency and _n_ discussed above, and converting
to observational units of Jy km s [−][1] kpc [2] for _!_ (H 40 _U_ ), we have



(A5)
�



_&_ 0 = 4 _._ 010 ⇥ 10 [44]


and



_!_ (H 40 _U_ )
 Jy km/s kpc [2]



(A6)
�



_(퐹'_ ( _퐻_ 40 _U_ )

[=][ 3] _[.]_ [008][ ⇥] [10] [−][3]
M ⊙ Myr [−][1]



_!_ (H 40 _U_ )
 Jy km/s kpc [2]



where _!_ (H 40 _U_ ) = 4 _c_ ( kpc _[⇡]_ [)] [2] [(] Jy _(_ km Δ _E_ /s [).] [In] [general,] [we] [convert] [from]

_!_ _a_ (H 40 _U_ ) in cgs units to _!_ (H 40 _U_ ) in observer units (Jy km s [−][1] kpc [2] )
via


_!_ _a_ (H 40 _U_ ) = 3 _._ 174 ⇥ 10 [23] _a_ GHz _!_ (H 40 _U_ ) = 3 _._ 143 ⇥ 10 [25] _!_ (H 40 _U_ ) _._


(A7)


While Binder & Povich (2018b) showed that the star formation
rates from their relation agreed well with other measures, they cautioned that they are likely to be underestimates because of dust absorption and young ages, especially for compact sources such as ours.
Our only justification for using either the FIR or the RRL for star
formation rates is that the SFR from the RRL agrees reasonably well
with the SFR from the FIR. Both are likely to be underestimates.


**APPENDIX B:** **DERIVATION OF ELECTRON DENSITY**

**AND IONIZED GAS MASS**


The electron density is readily obtained from the observations under
the assumptions contained in steps 1 through 3 above.



0 _._ 5

_!_ _a_ (H 40 _U_ )

= 3 _._ 582

 _n+_ �



_!_ (H 40 _U_ )
 Jy km/s kpc [2]



� −1 _._ 5



0 _._ 5

=
�



0 _._ 5
_'_ eff
�  pc


(B1)



_=_ _4_ =



_'_ rec
 _U_ B _+_



where the result is in cm [−][3] .


The mass of ionized gas is then computed from



1 _._ 5

(B2)
�



0 _._ 5
_'_ eff
�  pc



_"_ ion = _=_ _?_ _<_ H _`+_ = 0 _._ 471M ⊙



_!_ (H 40 _U_ )
 Jy km/s kpc [2]



where _`_ is the mean mass per proton (1.27 for 27% helium) and we
take _=_ _?_ = _=_ _4_, neglecting ionization of helium.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



MNRAS **000**, 1–11 (2021)


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "Source distances, galactocentric distances (RGC), and clump molecular gas masses (Mmol or Mclump)",
  "failed_quote": "Figure 3 plots the ratio, L bol -to-L 0 mol versus Galactocentric distances (R GC , compiled by Liu et al. 2020a)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Plot Lbol/L'mol against Galactocentric distance RGC and perform Kolmogorov-Smirnov tests on the log(Lbol/L'mol) distributions of clumps with and without H40alpha emission across six molecular tracers (CS 2-1, HC3N 11-10, H13CN 1-0, H13CO+ 1-0, HCN 1-0, HCO+ 1-0).",
  "failed_quote": "Figure 3 plots the ratio, L bol -to-L 0 mol versus Galactocentric distances (R GC , compiled by Liu et al. 2020a)."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "log(SFR / Msun Myr^-1) = log(Lbol / ergs s^-1) - 37.41; SFR(H40alpha) / (Msun Myr^-1) = 3.008 x 10^-3 * [L(H40alpha) / (Jy km/s kpc^2)]; threshold SFR >= 5 Msun Myr^-1",
  "failed_quote": "= 3 . 008 ⇥ 10 −3 ! (H 40 U ) Jy km/s kpc 2 (A6)"
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[2]",
  "value": "Well-sampled Kroupa & Weidner (2003) IMF and steady-state massive star birth/death for SFR >= 5 Msun Myr^-1 (Lbol >= 10^4.5 Lsun); molecular clump masses taken from single-dish dust continuum in Liu et al. (2020a)",
  "failed_quote": "Assuming a well-sampled IMF and a timescale long enough that the birth and death of massive stars have reached steady state, the ionization rate can be related to the SFR."
 },
 {
  "path": "findings_qualitative[4].evidence[1]",
  "value": "Clumps with H40alpha emission show higher Lbol-to-L'mol ratios (by ~0.5 dex) and shorter gas depletion times (by ~0.25 dex) than clumps without H40alpha emission, which is explained as an evolutionary effect.",
  "failed_quote": "(iv) The star forming clumps with H 40 U emission (thus Hii regions) show higher L bol -to-L 0 mol ratios (or SFE) than those without H 40 U emission. The mean values of log(L bol -to-L 0 mol ) ratios between the two sub-samples are offset by ⇠0.5 dex."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "Clump-scale star formation efficiency does not change with Galactocentric distance.",
  "failed_quote": "However, there is no clear trend for L bol -to-L 0 mol ratios against R GC in our study."
 }
]
```
