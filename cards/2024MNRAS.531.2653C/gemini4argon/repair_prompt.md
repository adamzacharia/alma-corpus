# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.531.2653C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_IRAS 4A outflows_ 1

## **Multiple chemical tracers finally unveil the intricate NGC 1333 IRAS 4A** **outflow system. FAUST XVI**


Layal Chahine, [1] _[★]_ Cecilia Ceccarelli, [1] - Marta De Simone, [2] _[,]_ [1] _[,]_ [3] Claire J. Chandler, [4] Claudio Codella, [3]

Linda Podio, [3] Ana López-Sepulcre, [1] _[,]_ [5] Nami Sakai, [6] Laurent Loinard, [7] _[,]_ [8] Mathilde Bouvier, [9] Paola Caselli, [10]

Charlotte Vastel, [11] Eleonora Bianchi, [12] _[,]_ [1] Nicolás Cuello, [1] Francesco Fontani, [3] _[,]_ [10] _[,]_ [13] Doug Johnstone, [14] _[,]_ [15]

Giovanni Sabatini, [3] Tomoyuki Hanawa, [16] Ziwei E. Zhang, [6] Yuri Aikawa, [17] Gemma Busquet, [18] Emmanuel Caux, [11]

Aurore Durán, [7] Eric Herbst, [19] François Ménard, [1] Dominique Segura-Cox, [10] _[,]_ [20] Brian Svodoba, [4] _[,]_ [21]

Nadia Balucani, [22] Steven Charnley, [23] François Dulieu, [24] Lucy Evans, [25] Davide Fedele, [3] Siyi Feng, [26]

Tetsuya Hama, [27] _[,]_ [28] Tomoya Hirota, [29] Andrea Isella, [30] Izaskun Jímenez-Serra, [31] Bertrand Lefloch, [32]

Luke T. Maud, [2] María José Maureira, [10] Anna Miotello, [2] George Moellenbrock, [4] Hideko Nomura, [33]

Yasuhiro Oba, [34] Satoshi Ohashi, [6] Yuki Okoda, [35] _[,]_ [6] Yoko Oya, [36] _[,]_ [35] Jaime Pineda, [10] Albert Rimola, [37]

Takeshi Sakai, [38] Yancy Shirley, [39] Leonardo Testi, [40] _[,]_ [3] Serena Viti, [9] Naoki Watanabe, [34] Yoshimasa Watanabe, [41]

Yichen Zhang, [6] and Satoshi Yamamoto [42]


1 _Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France_
2 _ESO, Karl Schwarzchild Srt. 2, 85478 Garching bei Munchen, Germany_
3 _INAF, Osservatorio Astrofisico di Arcetri, Largo E. Fermi 5, I-50125, Firenze, Italy_
4 _National Radio Astronomy Observatory, PO Box O, Socorro, NM 87801, USA_
5 _Institut de Radioastronomie Millimétrique (IRAM), 300 rue de la Piscine, 38406 Saint-Martin-d’Hères, France_
6 _RIKEN Cluster for Pioneering Research, 2-1, Hirosawa, Wako-shi, Saitama 351-0198, Japan_
7 _Instituto de Radioastronomía y Astrofísica, Universidad Nacional Autónoma de México, A.P. 3-72 (Xangari), 8701, Morelia, Mexico_
8 _Instituto de Astronomía, Universidad Nacional Autónoma de México, Ciudad Universitaria, A.P. 70-264, Cuidad de México 04510, Mexico_
9 _Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA Leiden, The Netherlands_
10 _Center for Astrochemical Studies, Max-Planck-Institut für extraterrestrische Physik (MPE), Gießenbachstr. 1, D-85741 Garching, Germany_
11 _IRAP, Universitè de Toulouse, CNRS, CNES, UPS, Toulouse, France_
12 _ORIGINS, Excellence Cluster Origins, Boltzmannstrasse 2, D-85748 Garching bei München, Germany_
13 _LERMA, Observatoire de Paris, PSL Research University, CNRS, Sorbonne Université, 92190 Meudon, France_
14 _NRC Herzberg Astronomy and Astrophysics, 5071 West Saanich Road, Victoria, BC, V9E 2E7, Canada_
15 _Department of Physics and Astronomy, University of Victoria, Victoria, BC, V8P 5C2, Canada_
16 _Center for Frontier Science, Chiba University, 1-33 Yayoi-cho, Inage-ku, Chiba 263-8522, Japan_
17 _Department of Astronomy, The University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033, Japan_
18 _Departament de Física Quàntica i Astrofísica, Institut de Ciències del Cosmos, Universitat de Barcelona (IEEC-UB), Martí Franquès, 1, 08028 Barcelona, Spain_
19 _Department of Chemistry, University of Virginia, McCormick Road, PO Box 400319, Charlottesville, VA 22904, USA_
20 _The University of Texas at Austin, 2515 Speedway, Austin, Texas 78712, USA_
21 _Jansky Fellow of the National Radio Astronomy Observatory_
22 _Department of Chemistry, Biology, and Biotechnology, The University of Perugia, Via Elce di Sotto 8, 06123 Perugia, Italy_
23 _Astrochemistry Laboratory, Code 691, NASA Goddard Space Flight Center, 8800 Greenbelt Road, Greenbelt, MD 20771, USA_
24 _CY Cergy Paris Université, Sorbonne Université, Observatoire de Paris, PSL University, CNRS, LERMA, F-95000, Cergy, France_
25 _School of Physics and Astronomy, University of Leeds, Leeds LS2 9JT, UK_
26 _Department of Astronomy, Xiamen University, Xiamen, Fujian 361005, P. R. China_
27 _Komaba Institute for Science, The University of Tokyo, 3-8-1 Komaba, Meguro, Tokyo 153-8902, Japan_
28 _Department of Basic Science, The University of Tokyo, 3-8-1 Komaba, Meguro, Tokyo 153-8902, Japan_
29 _National Astronomical Observatory of Japan, Osawa 2-21-1, Mitaka-shi, Tokyo 181-8588, Japan_
30 _Department of Physics and Astronomy, Rice University, 6100 Main Street, MS-108, Houston, TX 77005, USA_
31 _Centro de Astrobiología (CSIC-INTA), Ctra. de Torrejón a Ajalvir, km 4, 28850, Torrejón de Ardoz, Spain_
32 _Université de Bordeaux – CNRS Laboratoire d’Astrophysique de Bordeaux, 33600 Pessac, France_
33 _Division of Science, National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan_
34 _Institute of Low Temperature Science, Hokkaido University, N19W8, Kita-ku, Sapporo, Hokkaido 060-0819, Japan_
35 _Department of Physics, The University of Tokyo, 7-3-1, Hongo, Bunkyo-ku, Tokyo 113-0033, Japan_
36 _Yukawa Institute for Theoretical Physics, Kyoto University Oiwake-cho, Kitashirakawa, Sakyo-ku, Kyoto-shi, Kyoto-fu 606-8502, Japan_
37 _Departament de Química, Universitat Aut_ ` _𝑜noma de Barcelona, 08193 Bellaterra, Spain_
38 _Graduate School of Informatics and Engineering, The University of Electro-Communications, Chofu, Tokyo 182-8585, Japan_
39 _Steward Observatory, 933 N Cherry Ave., Tucson, AZ 85721 USA_
40 _Dipartimento di Fisica e Astronomia “Augusto Righi” Viale Berti Pichat 6/2, Bologna, Italy_
41 _Materials Science and Engineering, College of Engineering, Shibaura Institute of Technology, 3-7-5 Toyosu, Koto-ku, Tokyo 135-8548, Japan_
42 _SOKENDAI, Shonan Village, Hayama, Kanagawa 240-0193, Japan_



Accepted 2024 May 20. Received 2024 May 20; in original form 2024 February 29



MNRAS **000**, 1–15 (2024)

MNRAS **000**, 1–15 (2024) Preprint 22 May 2024 Compiled using MNRAS L [A] TEX style file v3.0


**ABSTRACT**


The exploration of outflows in protobinary systems presents a challenging yet crucial endeavour, offering valuable insights into
the dynamic interplay between protostars and their evolution. In this study, we examine the morphology and dynamics of jets and
outflows within the IRAS 4A protobinary system. This analysis is based on ALMA observations of SiO(5–4), H 2 CO(3 0 _,_ 3 –2 0 _,_ 3 ),
and HDCO(4 1 _,_ 4 –3 1 _,_ 3 ) with a spatial resolution of ∼150 au. Leveraging an astrochemical approach involving the use of diverse
tracers beyond traditional ones has enabled the identification of novel features and a comprehensive understanding of the broader
outflow dynamics. Our analysis reveals the presence of two jets in the redshifted emission, emanating from IRAS 4A1 and
IRAS 4A2, respectively. Furthermore, we identify four distinct outflows in the region for the first time, with each protostar, 4A1
and 4A2, contributing to two of them. We characterise the morphology and orientation of each outflow, challenging previous
suggestions of bends in their trajectories. The outflow cavities of IRAS 4A1 exhibit extensions of 10 [′′] and 13 [′′] with position
angles (PA) of 0 [◦] and -12 [◦], respectively, while those of IRAS 4A2 are more extended, spanning 18 [′′] and 25 [′′] with PAs of 29 [◦]

and 26 [◦] . We propose that the misalignment of the cavities is due to a jet precession in each protostar, a notion supported by the
observation that the more extended cavities of the same source exhibit lower velocities, indicating they may stem from older
ejection events.


**Key** **words:** ISM: kinematics and dynamics – ISM: jets and outflows – astrochemistry – stars: formation – stars: low-mass –
ISM: individual object: NGC 1333 IRAS 4A



**1** **INTRODUCTION**


It has long been known that the gravitational collapse, at the basis of
the formation of a star and planetary system, is inevitably accompanied by a simultaneous ejection process, mediated by the magnetic
field (e.g. Frank et al. 2014; Bally et al. 2014; Lee 2020). These
ejections form the so-called "outflow systems", in general, constituted by supersonic jets, bow-shocks and cavities, all more or less
delineated and identified by shocked material (see, e.g., Fig. 3 of
Bally 2016; Rivera-Ortiz et al. 2023). Several molecular lines are
generally used for these analyses. Particularly useful are lines from
species that have a very low abundance in molecular clouds because
they are trapped in the interstellar grains, both in the refractory cores
and volatile mantles. The paradigmatic species is SiO, considered a
clear-cut shock hallmark (e.g. Schilke et al. 1997; Caselli et al. 1997;
Gusdorf et al. 2008). Formaldehyde is also a good tracer of material
ejected from the grain mantles, while deuterated formaldehyde traces
the most recent ejected material (e.g. Fontani et al. 2014).
Often, but not always, the outflows have a bipolar structure. Outflows have been the focus of a multitude of studies at the beginning
because they were unexpectedly observed towards protostars before
any sign of collapse was found (e.g. Kwan & Scoville 1976; Bally &
Lada 1983; Frank et al. 2014; Bally 2016). Soon after, it was realised
the huge importance of the outflows in getting rid of the angular
momentum of the protostellar infalling matter, as well as in shaping
and disrupting the protostellar envelope and molecular cloud hosting the protostar. Finally, molecular outflows cause different shocks,
which in one way or another increase the gas chemical complexity (e.g. Bachiller 1996) and are therefore very precious chemical
laboratories (e.g. Codella et al. 2017).
In addition to all the above reasons, the study of outflows in protobinary systems provides a fascinating glimpse into the complexity
of star birth. It sheds light on the genesis and early dynamical interactions of multiple protostars, providing essential insights into their
intertwined evolution. This is particularly true for systems where the


_★_ E-mail: layal.chahine@univ-grenoble-alpes.fr

- E-mail: cecilia.ceccarelli@univ-grenoble-alpes.fr



binary companions are close enough to possibly interact and/or influence each other. In fact, how the presence of a companion affects the
ejection phenomenon is still not elucidated, especially in very young
protobinary systems, where the surrounding envelope can mask and
likely influence the evolution of the outflow itself. It is not by chance
that the best-studied systems, especially when it comes to chemistry,
refer to single outflows (e.g. HH 212; Codella et al. 2007; Lee et al.
2015, L1157-mm Bachiller et al. 1995; Arce et al. 2013; Lefloch
et al. 2017; Codella et al. 2017 and HH 30 Pety et al. 2006; Louvet
et al. 2018 among others).


The advent of high-angular resolution instruments has significantly advanced these studies, improving observational capacities
and allowing for the resolution of smaller-scale features. Outflows in
various multiple systems have now been studied, including but not
limited to BHR 71 (Tobin et al. 2019a), IRAS 16293-2422 (Oya et al.
2021), VLA 1623–2417 (Hsieh et al. 2020; Hara et al. 2021; Ohashi
et al. 2022), Ser-emb 15 (Sato et al. 2023b), OMC-2 FIR 4 (Chahine
et al. 2022; Lattanzi et al. 2023; Sato et al. 2023a), BHB2007 (Hara
et al. 2013; Alves et al. 2019; Zurlo et al. 2021; Evans et al. 2023),
HH 1/2 (e.g. Reipurth et al. 2000; Noriega-Crespo & Raga 2012;
Raga et al. 2015) and the HH 24 complex (e.g. Reipurth et al. 2023).


A specific system that has piqued the interest of many researchers
due to its distinctive features and complex dynamics and chemistry
is IRAS 4A. IRAS 4A is a binary system, harbouring two protostars
IRAS 4A1 and IRAS 4A2 (hereafter 4A1 and 4A2 respectively), located in the star-forming region NGC 1333 within the Perseus molecular cloud, at a distance of 293 ± 22 pc (Zucker et al. 2018). Notably,
the system stands out for its remarkable outflow phenomena, which
have been the subject of numerous studies. Indeed, the outflows
within the IRAS 4A system have been mapped using various molecular tracers, such as CO (e.g. Blake et al. 1995; Girart et al. 1999;
Jørgensen et al. 2007; Yıldız et al. 2012; Santangelo et al. 2015;
Ching et al. 2016; Podio et al. 2021; Chuang et al. 2021), CS (Di
Francesco et al. 2001; Taquet et al. 2020), SiO (e.g. Lefloch et al.
1998; Choi 2001; Santangelo et al. 2015; Koumpia et al. 2017; De
Simone et al. 2022), SO and other sulphur-bearing species (e.g. Santangelo et al. 2015; Taquet et al. 2020; Podio et al. 2021; Chuang
et al. 2021), as well as HCN (e.g. Choi 2001), and H 2 CO (e.g. Di


© 2024 The Authors

Francesco et al. 2001; Su et al. 2019). The presence of more complex molecules (CH 3 OH and CH 3 CHO; De Simone et al. 2022) was
revealed along the outflows, highlighting the rich chemistry of this
region.
The SiO observations at an angular resolution of 2 [′′] (Choi 2005;
Choi et al. 2006) suggested the presence of a bipolar northeastsouthwest outflow driven by 4A2, and a tentative south outflow possibly driven by 4A1, with no distinct northern counterpart being
evident. To determine the outflow direction, Choi (2005) employed
a least-squares fit method based on the positions of compact peaks
near the driving source, identifying a trajectory passing near 4A2.
Similar results were also found with other tracers. Using a higher
angular resolution ∼1 [′′], Santangelo et al. (2015) successfully distinguished the two outflows in the southern blue-shifted emission
and, notably, at extremely high velocities (41 – 55 km/s), they could
resolve the redshifted counterpart of the 4A1 southern outflow for
the first time. The same feature was also observed at similar velocity ranges with other tracers. There is no agreement, however, over
the direction of the redshifted counterpart from 4A1. While the SiO
emission mapped by Santangelo et al. (2015) suggests that the jet is
oriented north-south (N-S), Ching et al. (2016) considered a position angle (PA) of -9 [◦], aligning with the trajectory of the southern
counterpart of the jet. Nonetheless, Ching et al. (2016) have suggested that the northern outflow of IRAS 4A1 is later bent due to
the interaction with the outflow of IRAS 4A2. A recent study using
CO and SO at an angular resolution of 0.3 [′′] suggested the presence
of two northern outflow lobes, one from each protostar, both bent
towards the northeast (Chuang et al. 2021). Another study at similar
angular resolution using H 2 CO suggested that both outflows are oriented north-south (Su et al. 2019). Meanwhile, the morphology of
the southern blueshifted lobes is similar to that seen in previous studies, with the IRAS 4A1 lobe oriented southeast and the IRAS 4A2
lobe directed southwest. It is also worth noting that an abrupt bend at
20 [′′] from 4A1 was also observed in several studies (e.g. Choi 2005;
Yıldız et al. 2012; De Simone et al. 2022). Choi (2005) referred to
this as “directional variability” and proposed that this feature may be
attributed to external medium perturbations, specifically a deflection
resulting from interactions with an external core or cloud, distinct
from the one associated with the IRAS 4A system.
Despite numerous studies on this system, the intricate morphology of the outflows has posed challenges in definitively attributing
them to the respective protostars. Consequently, a comprehensive
understanding of the broader scenario remains elusive. Achieving a
more coherent picture demands advancements in several aspects, including higher spatial and spectral resolution, enhanced sensitivity,
wider field of view coverage, and the use of diverse tracers. In this
paper, we have examined the morphology and kinematics of the jets
and outflows towards the IRAS 4A system, via the study of the line
emission of three standard shock tracers (see above): SiO, H 2 CO
and HDCO. We employ these three tracers because a posteriori and
after a fast check of the maps for this source we found that they offer
complementary insights into the observed dynamics, with H 2 CO and
HDCO playing a crucial role in identifying the cavities and enriching
our understanding of the system’s dynamics. We aimed to conduct a
comprehensive characterisation, pinpointing and associating distinct
features with their respective protostars, using observations from the
Large Program FAUST (Fifty AU STudy of the chemistry in the
disc/envelope system of solar-like protostars; 2018.1.01205.L, PI: S.
Yamamoto; Codella et al. 2021). The present article is structured
as follows. In Sect. 2 we describe the observations. In Sect. 3 we

present the molecular line maps, together with the main results of
the analysis. In Sect. 4 we discuss the structure of the outflows in the



_IRAS 4A outflows_ 3


IRAS 4A protobinary system, as derived by the FAUST observations,
and compare it with the interpretations in previous literature. In Sect.
5 we summarise the conclusions of this work.


**2** **OBSERVATIONS**


The IRAS 4A system was observed at 1.2 mm with ALMA during its
Cycle 6 operations, between October 2018 and September 2019, as
part of the Large Program FAUST. The observations were performed
in Band 6 using the 12-m array (C43-3 and C43-6 configurations,
including 46 and 50 antennas, respectively) and the 7-m Atacama
Compact Array (ACA). The baselines for the 12-m array were between 15.1 m and 3.6 km, probing angular scales from 0 [′′] _._ 03 (∼9 au)
to 8 [′′] _._ 2 (∼2400 au).
The observations were centred at R.A. (J2000) = 03 [h] 29 [m] 10 [s] .539,
Dec. (J2000) = 31 [◦] 13 [′] 30 [′′] _._ 92 and the systemic velocity was set to
V lsr = 7 km s [−][1] . Several spectral windows (spw) were placed within
the spectral range 216–234 GHz and 243–262 GHz. In this work, we
focus on two narrow spws covering the following lines: SiO(5-4) and
H 2 CO(3 0 _,_ 3 –2 0 _,_ 3 ), and one large spw covering HDCO(4 1 _,_ 4 –3 1 _,_ 3 ).
The spectroscopic parameters of each line are reported in Table 1. The
SiO and H 2 CO spws have a bandwidth of 58.6 MHz (∼80.9 km s [−][1]

for SiO and ∼80.5 km s [−][1] for H 2 CO spw) and a channel width of
141 kHz (∼0.2 km s [−][1] for SiO and H 2 CO spw). The window covering HDCO has a bandwidth of 1875 MHz (∼2294.4 km s [−][1] ) and a
channel width of 1.13 MHz (∼1.4 km s [−][1] ).
The quasar J0237+2848 was used for bandpass and flux calibration, while J0336+3218 and J0328+3139 were used for phase calibration. The absolute flux calibration uncertainty is estimated to
be <15%. The data calibration was performed using the standard
ALMA calibration pipeline with the Common Astronomy Software
Applications package 5.6.1-8 (CASA [1], CASA Team et al. 2022). An
additional calibration routine [2] has been used to correct for the _𝑇_ _𝑠𝑦𝑠_
and for spectral data normalisation. The spectrum of IRAS 4A is
particularly rich and the identification of line-free continuum channels had to be done by hand, outside the ALMA pipeline. Line-free
channels were then averaged per-spectral window and used to create a continuum model for each ALMA configuration, and both
amplitude and phase self-calibration were employed to correct for
remaining tropospheric phase fluctuations, position offsets, and amplitude calibration differences between the execution blocks. For
each ALMA configuration, two rounds of phase-only selfcal were
performed, followed by two rounds of amplitude and phase selfcal
once the model was sufficiently complete. The resulting improvement in the continuum dynamic range was typically a factor of 5–7.
The continuum model was then subtracted from the line channels to

produce continuum-subtracted visibilities. A similar self-calibration
technique was then used to align data across configurations. The
visibility data from the 12-m arrays were then combined to produce the continuum-subtracted line cubes. The resulting continuumsubtracted cubes were cleaned using Högbom algorithm (Högbom
1974) and natural weighting in the IRAM-GILDAS software package [3] . The data analysis was performed using the same package. The
resulting beam size and rms are summarised in Table 1. The FWHM
Field of View (FoV) is 29 [′′] for SiO, 28.9 [′′] for H 2 CO, and 25.5 [′′]


1 `[https://casa.nrao.edu/](https://casa.nrao.edu/)`
2 `[https://help.almascience.org/kb/articles/](https://help.almascience.org/kb/articles/what-are-the-amplitude-calibration-issues-caused-by-alma-s)`
```
what-are-the-amplitude-calibration-issues-caused-by-alma-s
```

`-normalization-strategy` ; see also Moellenbrock et al. in preparation
3 http://www.iram.fr/IRAMFR/GILDAS/


MNRAS **000**, 1–15 (2024)

4 _L. Chahine et al._


**Table 1.** Spectral parameters of the SiO, H 2 CO, and HDCO lines observed towards IRAS 4A.


Transition _𝜈_ [(] _[𝑎]_ [)] E up [(] _[𝑎]_ [)] A ij [(] _[𝑎]_ [)] S _𝜇_ [2] [(] _[𝑎]_ [)] Bandwidth dV FWHM FoV Beam (PA) Chan _._ rms
(MHz) (K) (10 [−][4] s [−][1] ) (D [2] ) (MHz) (km s [−][1] ) ′′ ′′ × ′′ ( ◦ ) (mJy beam [−][1] )
SiO(5–4) 217104.98 31.3 5.20 48.8 58.6 0.2 29 0.48 × 0.34 (87.8) 0.81
H 2 CO(3 0 _,_ 3 –2 0 _,_ 3 ) 218222.19 21.0 2.82 16.3 58.6 0.2 28.9 0.46 × 0.32 (-6.6) 0.72
HDCO(4 1 _,_ 4 –3 1 _,_ 3 ) 246924.60 37.6 3.98 20.4 1875 1.4 25.5 0.37 × 0.27 (-17.4) 0.40
( _𝑎_ ) Frequencies and spectroscopic parameters have been extracted from Müller et al. (2013) for SiO, Bocquet et al. (1996); Müller & Lewen (2017) for H 2 CO,
and Bocquet et al. (1999) for HDCO.



for HDCO. The maps shown in the paper are not corrected for the
primary beam attenuation, as we are more interested in the structures’ morphology (rather than the flux) that was not affected by the
primary beam attenuation. By not applying correction for primary
beam attenuation, we ensure that features extending beyond the field
of view, are not inadvertently excluded in our analysis. This approach
allows us to preserve the integrity of the observed structures, facilitating a comprehensive understanding of their spatial distribution
and morphology.


**3** **RESULTS**


We have imaged the emission from SiO, H 2 CO, and HDCO towards
the IRAS 4A system. The comprehensive understanding of the observed dynamics originates from the combined insights derived from
the analysis of the three tracers. For a concise overview of our findings, readers are directed to Section 3.4.


**3.1** **SiO emission**


Figure 1 illustrates a thorough view of the SiO emission in six distinct panels, depicting the spatial and velocity features of the studied
region. The upper left panel shows the SiO(5–4) integrated intensity map (moment 0), the lower left panel shows the SiO velocity
map (moment 1) both integrated between -27 and 35 km s [−][1], and
the remaining four panels show the integrated channel maps, each
representing SiO emission at distinct velocity intervals. The SiO moment 0 map reveals different features, including bow-shocks, jets,
and outflow, alongside the finger-like structures previously reported
by De Simone et al. (2022) in the south. The SiO emission in the
figure spans from -27 km s [−][1] ( _𝛿_ V= -34 km s [−][1] ; V lsr = 7 km s [−][1] ) to
35 km s [−][1] ( _𝛿_ V= +28 km s [−][1] ). The narrow spectral window limits
detection beyond 35 km s [−][1], however, the emission is expected to be
relatively low beyond this velocity threshold. The moment 1 map indicates that features located north of the protostars are characterised
by redshifted velocities, while those situated south exhibit blueshifted
velocities. The integrated channel maps in the figure correspond to
four different velocity intervals, namely the high-velocity 1 (HV1;
_𝛿_ V= -34 (+28) – ±20 km s [−][1] ), high-velocity 2 (HV2; _𝛿_ V= ±12 –
±20 km s [−][1] ), intermediate-velocity (IV; _𝛿_ V= ±4 – ±12 km s [−][1] ), and
low-velocity intervals (LV; _𝛿_ V= ±1 – ±4 km s [−][1] ).


_3.1.1_ _High Velocity (HV1 and HV2)_


**HV1** : In the redshifted HV1 regime, a north-south jet (J1) stemming
from source 4A1 is evident. The jet shows bullet-like structures and
reaches almost ∼5 [′′] (∼1500 au) from the protostar. At distances of
12 [′′] –18 [′′] (∼3500–5300 au) from 4A2, another jet (J2) is visible,
clearly directed towards it, and distinguished by the presence of
identifiable bullets along this feature. A zoom-in onto the innermost
region showing of J1 from J2 is depicted in Fig. A1.


MNRAS **000**, 1–15 (2024)



On the other hand, in the blueshifted emission, we detect a ringlike feature, directed almost N-S, associated with the first blueshifted
outflow cavity of 4A1 (C1-blue).
**HV2** : In the panel corresponding to the HV2 interval, the emission
starts to overlap at the north. Conversely, in the south, the components attributed to 4A1 can be distinguished from those of 4A2. At
∼13 [′′] (∼3800 au) to the south of 4A2, we identify a prominent bowshock structure associated with an outflow cavity of 4A2 (C2-blue).
Additionally, there is observable emission around ∼23 [′′] (∼6700 au)
to the south of 4A2, which is likely associated with another cavity
(C4-blue; See Sect. 3.3).


_3.1.2_ _Intermediate Velocity (IV)_


Transitioning to the redshifted intermediate velocity (IV) regime,
shown in the bottom left panel of Fig. 1, the SiO emission presents
a complex overlap of the structures originating from 4A1 and 4A2,
making interpretation difficult. These features are better discerned in
HDCO and will be discussed further (See Sect. 3.2). However, with
the detection of a bow-shock at ∼18 [′′] (∼5300 au) from 4A2 (Bow2),
which is also perpendicular to the trajectory of its jet 4A2 (J2), we
observe that the extended northeast-southwest outflow cavity wall
(C2-w) reaches Bow2. This observation suggests that we are tracing
the high-velocity component of the 4A2 outflow (C2-red; further
explanation is provided in the subsequent sections). The outflow

∼
shows an S-shape bending within 4 [′′] ( 1200 au) from IRAS 4A2 that
was also observed in previous studies (Santangelo et al. 2015; Chuang
et al. 2021). It is worth noting that Bow2 was present in the CS maps
of Taquet et al. (2020), but was not explicitly identified by the authors.
Additionally, an arc-like feature appears at approximately 20–25 [′′]


∼
( 5900–7300 au) from 4A2 (C4-w). This feature is coincident with
what was interpreted as a sharp bend (also referred to as deflection or
directional variability) by Choi (2005), which has also been observed
by Yıldız et al. (2012); De Simone et al. (2022), as illustrated in Fig.
2.

Initially, this structure was attributed to a deflection of the 4A2
outflow caused by a dense core (Choi 2005). However, we suggest
that it is rather linked with the LV component of the 4A2 outflow (C4red; see Sect. 3.3), being the remnant of its western cavity wall. The
emission of this outflow is better discerned with H 2 CO. Within the
same velocity interval, the blue-shifted emission shows the presence
of two bow-shocks directed towards 4A1, one in the N-S direction
reaching 10 [′′] (∼3000 au) from the protostar and the other with a
PA of ∼-12 [◦] reaching ∼13 [′′] (∼3800) from it. Although less clear
in SiO, the bow-shocks are better observed in the other tracers, and
they illustrate two outflow cavities driven by 4A1 (C1-blue and C3blue). To the south of 4A2, distinguishing the emission becomes
more intricate, and we likely observe two outflows extending ∼13 [′′]

(C2-blue) and ∼23 [′′] (C4-blue) from the protostar. The 4A2 outflow
resembles that of HH 46/47 (Arce et al. 2013) showing a bifurcation
along its eastern wall.

_IRAS 4A outflows_ 5











**Figure** **1.** Integrated intensity (moment 0; top left) map, velocity map (moment 1; bottom left) and channel maps (right panels) of SiO(5-4) towards the
NGC 1333 IRAS 4A system. In the moment 0 and moment 1 panels the SiO emission is integrated between -27 and 35 km s [−][1] and a 5 _𝜎_ threshold cut was
applied [5] ( _𝜎_ = 0.81 mJy beam [−][1] km s [−][1] ). The channel maps correspond to four different velocity intervals: High-Velocity 1 (HV1), High-Velocity 2 (HV2),
Intermediate-Velocity (IV) and Low-Velocity (LV). The intervals and their corresponding labels are shown at the upper right corners of each channel maps panel.
The contour levels are [5, 25, 40, 60, 100] _𝜎_ for the redshifted HV1 regime and at [5, 25, 50, 100] _𝜎_ for the other regimes with _𝜎_ = (1.3 mJy beam [−][1] km s [−][1],
1.5 mJy beam [−][1] km s [−][1], 1.7 mJy beam [−][1] km s [−][1], 0.9 mJy beam [−][1] km s [−][1], respectively). The positions of IRAS 4A1 and IRAS 4A2 are marked with stars. The
jets from each source are marked with arrows. The synthesised beam is depicted in the lower-left corner of the top-left panel. The FWHM of the Field of View
is depicted with a dashed grey circle in the lower-left panel.



_3.1.3_ _Low Velocity (LV)_


In the redshifted low-velocity regime, the emission is dominated by
the components linked with 4A2. Indeed, prominent outflow cavity
walls directed towards 4A2 are distinctly visible towards the west
and the east (i.e. C2-w, C2-e and C4-w) together with the Bow2
bow-shock. We suggest that C2-w, C2-e and Bow2 delineate the HV
component of the 4A2 outflow (C2-red) and that C4-w is linked with
the LV component of the 4A2 outflow cavity wall (C4-red; See Sect.
3.3 for further explanation)

Lastly, it is noteworthy that in the moment 0 map of SiO, a bow-like
feature is discernible to the east of the 4A1 blueshifted outflow (C1blue). This structure was previously identified by De Simone et al.
(2022) at lower angular resolution, where it resembled a finger-like
structure similar to the one observed at the west of the A2 outflow.
The authors proposed these fingers to be formed by a train of shocks



due to an expanding bubble crashing against NGC 1333. The higher
resolution of the ALMA data reveals that the finger-like structure at
the west of the 4A1 outflow has an arc-like shape at its end. However, since there is no apparent association with any specific outflow
emanating from 4A1 or 4A2, we postpone a dedicated investigation
of these fingers to future work.


**3.2** **HDCO emission**


In Fig. 3 we present the moment 0 map of HDCO integrated between
(-3.6 and 20.1 km s [−][1] ). HDCO emission delineates the outflow cavities towards the IRAS 4A system, helping to better discern different
components, particularly to the north of the protostar, despite some
overlap in emission. Notably, HDCO emission reveals, for the first
time, a bow-like feature at ∼10 [′′] from 4A1 (Bow1) perpendicular to


MNRAS **000**, 1–15 (2024)

6 _L. Chahine et al._











**Figure 2.** SiO(2-1) integrated intensity contours from De Simone et al. (2022)
with superimposed SiO(5-4) integrated intensity map from this work in
colours. The outflow cavities emanating from IRAS 4A2 and identified in
this work are represented with solid ellipses. The possible third event ("Hypothetical cavity") emanating from IRAS 4A2 is represented with a dashed
ellipse. The FWHM of the Field of View in our observations is depicted with
a dotted magenta circle. The synthesised beams are depicted in the lower-left

corner.


its N-S jet. Stronger emission contours also show two curved features
(C1-w and C2-w), one aligned with 4A1 and another with 4A2. For
a detailed inspection, we show the channel map of the HDCO redshifted emission towards the north (V = 8.4–17.8 km s [−][1] ; Fig. A2).
We note that C1-w is emanating from A1 and has a higher velocity compared with the other features (including C2-w). This feature
(C1-w) extends up to ∼10 [′′] from 4A1 reaching the bowshock Bow1,
suggesting that Bow1 and C1-w delineate the 4A1 cavity, oriented
in the N-S direction (C1-red). Conversely, C2-w emission extends
beyond 10 [′′] (see also Fig. A2), forming a V-shape emerging from
4A2, together with C2-e (detected in SiO). The overlap between the
SiO and HDCO emission (Fig. 4), shows that these two features and
the Bow2 bow-shock observed in SiO are actually tracing the same
outflow cavity, which we named C2-red, where C2-w is the western
cavity wall and C2-e is the eastern. Further, emission beyond 10 [′′]

from the protostars aligns with the western wall of C2-red, suggesting an association with A2. Notably, while C2-w and C2-e belong to
the same cavity, C2-w exhibits a higher velocity by almost 3 km s [−][1],
indicating possible cavity rotation. Moving southward, an extended
cavity from 4A1 with PA∼-12 [◦] east (C3-blue) and part of the eastern
wall of the cavity from 4A2 can be observed. Intriguingly, within the
4A1 cavity, another “nested” cavity, C1-blue, directed almost N-S,
is noticeable (see Sect. 3.3 for further discussion). It is worth noting
that while C1-blue has C1-red as a redshifted counterpart, C3-blue
lacks a counterpart, suggesting it could be exiting the cloud or hidden
by the emission of the 4A2 cavity.


MNRAS **000**, 1–15 (2024)



**Figure 3.** Moment 0 map of HDCO integrated between -3.6 and 20.1 km s [−][1] .
A 3 _𝜎_ threshold cut was applied ( _𝜎_ = 0.40 mJy beam [−][1] km s [−][1] ). The contour levels are at 30 _𝜎_ with _𝜎_ = 0.40 mJy beam [−][1] km s [−][1] . The positions of

IRAS 4A1 and IRAS 4A2 are marked with stars. The features mentioned in

the text are labelled in grey. The solid ellipses represent the IRAS 4A1 outflow cavities observed in HDCO. The synthesised beam is depicted in the
lower-right corner.


**3.3** **H** 2 **CO emission**


Figure 5 presents the maps of the IRAS 4A system using H 2 CO as a
molecular tracer. The H 2 CO emission is illustrated in six panels, the
upper left panel shows the H 2 CO moment 0 map, and the remaining
five panels show the integrated channel maps. H 2 CO effectively maps
the distribution of the bulk gas within the IRAS 4A system; it also
traces the intricate outflow cavities originating from both the 4A1
and 4A2 sources, as well as the jet from 4A1. The emission in the
figure spans from -16 km s [−][1] ( _𝛿_ V= -23 km s [−][1] ; V lsr = 7 km s [−][1] ) to
35 km s [−][1] ( _𝛿_ V= +28 km s [−][1] ). The channel maps velocity intervals
correspond to five different velocity intervals, the HV2 and IV are as
in Fig. 1, while for the HV1 regime ( _𝛿_ V= -23 (+28) – ±20 km s [−][1] ). To
better illustrate the features of the IV regime, we split it into IV1 and
IV2. We note that the SiO map encompasses a slightly broader range
of velocities compared to H 2 CO, which is indicative of the latter
exhibiting dimmer emissions that remain undetected at the highest
velocities.


_3.3.1_ _High Velocity (HV1 and HV2)_


**HV1:** In the HV1 panel, the H 2 CO emission displays the presence of
the previously identified north-south jet originating from 4A1 (J1).

_IRAS 4A outflows_ 7











**Figure 4.** Left: Moment 0 map of HDCO in colour scale with superimposed SiO contours at 5 _𝜎_ ( _𝜎_ = 0.81 mJy beam [−][1] km s [−][1] ). The positions of IRAS 4A1 and
IRAS 4A2 are marked with stars. The HV component of the 4A2 outflow is represented by a navy blue ellipse. The synthesised beams are depicted in the lower-right
corner. Right: Moment 0 map of HDCO in colour scale with superimposed H 2 CO 5 _𝜎_ and 30 _𝜎_ redshifted LV contours in coral ( _𝜎_ = 1.5 mJy beam [−][1] km s [−][1] ).
The positions of IRAS 4A1 and IRAS 4A2 are marked with stars. The LV component of the 4A2 outflow is represented by a purple ellipse. The synthesised
beams are depicted in the lower-right corner.



**HV2:** In the redshifted HV2 interval, we detected the previously observed curved feature C1-w from 4A1 (i.e. the western wall of the
redshifted cavity), consistent with our HDCO observations. Additionally, we identified another feature oriented northeast-southwest,
pointing towards 4A2 and aligned with the western wall of C2-red
(seen in SiO). Transitioning to the blueshifted regime, we identify a
distinct N-S outflow cavity from 4A1 (C1-blue).


_3.3.2_ _Intermediate Velocities (IV1, IV2)_


Moving further into the blueshifted IV1 regime, as in SiO, clear differentiation emerges between the distinct outflow cavities, attributed
to 4A1 and 4A2. Within the 4A1 cavity across both IV1 and IV2
regimes, akin to HDCO observations, we observe two bow-like features. One is nearly perpendicular to the N-S jet direction (C1-blue),
while the other is tilted about 12 [◦] eastward (C3-blue), affirming the
presence of dual cavities from this source (see also the sketch in Fig.
6). Additionally, the cavities manifest at different velocities; C1-blue
is observable starting from -12.5 km/s, whereas the bowshock of
C3-blue is discernible at -6.9 km/s, with the cavity becoming more
apparent at lower velocities (See Fig A3). To the south of 4A2, at
least one outflow is observed.
The interpretation of the emission in the redshifted regime presents



considerable complexity, as in the other tracers. The 4A1 outflow
cavity (C1-red) is detected. The western lobe (C1-w) extends up to
10 [′′] from 4A1, while we see only 3 [′′] from the eastern lobe. The
features delineating C2-red (i.e. C2-w, Bow2 and C2-e) are also
detected. As in HDCO, the western cavity wall C2-w is observed at
higher velocities, being 7 km s [−][1] faster than eastern C2-e (as shown
in the detailed channel map A4) suggesting a possible cavity rotation.


_3.3.3_ _Low Velocity (LV)_


The redshifted LV regime is primarily characterised by the outflows
originating from 4A2, notably the extended northeast-southwest cavity (C2-red) detected in SiO. Alongside this cavity, denoted as C2red, we identify another structure labelled "C4-w," also observed
in SiO, situated to the west of 4A2. This feature, stemming from
IRAS 4A2, extends approximately ∼25 [′′] from the protostar, coinciding with the distinct directional variability previously documented
by Choi (2005); Yıldız et al. (2012); De Simone et al. (2022). With
H 2 CO, C4-w is detected between ∼8 and 12 km s [−][1] (see the detailed
channel map in Fig. A4). Within this velocity range, we observe
emergence of emission towards the northeast of Bow 2 and the east
of C2-e (Fig. A4). The overlap of the H 2 CO LV contours with the
HDCO moment 0 shows that the emission to the east of C2-e aligns


MNRAS **000**, 1–15 (2024)

8 _L. Chahine et al._













**Figure 5.** Integrated intensity (moment 0; top left) map and channel maps (right panels) of H 2 CO towards the NGC 1333 IRAS 4A system. In the moment 0 the
H 2 CO emission is integrated between -16 and 35 km s [−][1] and a 15 _𝜎_ threshold cut was applied ( _𝜎_ = 0.72 mJy beam [−][1] km s [−][1] ). The channel maps correspond
to five different velocity intervals High-Velocity 1 (HV1), High-Velocity 2 (HV2), Intermediate-Velocity (IV1 and IV2) and Low-Velocity (LV). The intervals
and their corresponding labels are shown at the upper right corners of each channel map panel. The contour levels are at [5, 25] _𝜎_ for HV1, [15, 50, 100] _𝜎_ for
the blueshifted emission in the HV2 and IV1 velocity intervals, [5, 35, 50, 100] _𝜎_ for the redshifted emission in IV1, and [5, 50, 100] _𝜎_ for the others, with
_𝜎_ = 0.9 mJy beam [−][1] km s [−][1], 1.1 mJy beam [−][1] km s [−][1], 1.2 mJy beam [−][1] km s [−][1], 1.0 mJy beam [−][1] km s [−][1], 1.5 mJy beam [−][1] km s [−][1], respectively). The positions of
IRAS 4A1 and IRAS 4A2 are marked with stars. The solid ellipses in the last two panels represent the C2-red and C4-red cavities. The synthesised beam is
depicted in the lower-left corner of the top-left panel.



with the HDCO feature C4-e, extending approximately ∼15 [′′] from
4A2 (see Fig. 4), suggesting that we are tracing the same feature. We
propose that C4-w and C4-e together form an elliptical shape with
a PA of ∼26 [◦], directed towards 4A2, implying they trace a second
outflow system driven by 4A2 (C4-red), where C4-w represents the


MNRAS **000**, 1–15 (2024)



western wall and C4-e is the eastern. Hence, the structure previously
thought to be a sharp bend (directional variability; Choi 2005; Yıldız
et al. 2012; De Simone et al. 2022) is actually part of the western
cavity wall of C4-red. The cavity is not entirely detected, likely due
to filtering. In Fig. 4, we depict the “potential” blue counterpart of

C4-red with a purple dashed ellipse. This ellipse aligns with the SiO
emission observed at 23 [′′] from 4A2, indicating that it may represent
a portion of the counterpart of C4-red. However, it is challenging to
differentiate it clearly from C2-blue, and its western wall is showing
very weak emission (see moment 0 map of H 2 CO).


**3.4** **Overview of the outflows and associated molecules**


To simplify and present a concise overview, we have summarised
the results in the sketch of Fig. 6 and listed the found components
and their major properties in Table 2. A comprehensive figure is also
shown in the appendix (Fig. A5, wherein all the features identified
in this work are overlaid on the molecular integrated velocity maps
of SiO, H 2 CO and HDCO, with corresponding labels.
Overall, our observations reveal the presence of two outflows emanating from 4A1 and another two outflows emanating from 4A2.
As summarised in the introduction, this is the first time that four
outflows are identified in the region: each protostar, 4A1 and 4A2, is
responsible for two of them. This conclusion is built on the various
components detected in our maps in different lines at different velocities, as briefly listed here to guide the reader through their detailed
description in the following sections.


_Jets J1 and J2:_ The high-velocity maps of SiO and H 2 CO reveal the
presence of two red-shifted jets, J1 and J2, north of 4A1 and 4A2,
emanating from 4A1 and 4A2, respectively.


_Bow-shocks_ _Bow1_ _and_ _Bow2:_ The lower velocity maps of H 2 CO
and HDCO show a red-shifted bow-shock, Bow1, associated with
J1, while those of SiO and H 2 CO show another bow-shock, Bow2,
associated with J2.


_A1_ _Cavities_ _C1-red;_ _C1-blue;_ _C3-blue:_ Despite the clear detection
of only one jet, J1, emanating from 4A1, our SiO, H 2 CO and HDCO
maps show the presence of one red-shifted cavity in the north, C1-red,
and two blue-shifted cavities in the south, C1-blue and C3-blue. C1red and C1-blue are aligned almost North-South, indicating that they
are part of the same bipolar outflow system. Likewise, the alignment
of the jet J1, the bow-shock Bow1 and the cavity C1-red suggest that
they all belong to the same ejection event that created them, which
reaches a distance from 4A1 of about 10 [′′] .

A second cavity, labelled C3-blue, extending to the south of 4A1,
is distinctly visible, particularly in the HDCO emission. This cavity
exhibits an eastward tilt in comparison to C1-blue. Notably, it lacks
a corresponding red-shifted counterpart to the north. We suggest
that the absence of a redshifted counterpart might be influenced by
the overlap with the redshifted cavity of 4A2. This overlap could
potentially obscure the cavity associated with 4A1, or even interact
with it, dispersing its emission. As for the prospects of detection, it
is plausible that the redshifted counterpart would be observable at
larger distances, beyond the influence of the 4A2 cavity’s obscuration,
however, more observations would be required to investigate this
point.


_A2 Cavities C2-red, C2-blue, C4-red and C4-blue:_ We identify two
red-shifted cavities emanating from 4A2 in the north, C2-red, C4red, and we associate them with two blue-shifted cavities in the south,
C2-blue and C4-blue, although the separation is less clear. The C2red is visible in the intermediate-velocity maps of SiO, H 2 CO and
HDCO, while the C4-red appears in the low-velocity maps of SiO
and H 2 CO. Both cavities, C2-red and C4-red, have an aligned blueshifted counterpart in the south, C2-blue and C4-blue, respectively.
The C2-red is aligned with the jet emanating from 4A2, J2, with a
position angle (PA) of ∼29 [◦] . While C4-red is slightly tilted with a PA
of ∼26 [◦] . Finally, we notice that, in our interpretation, the emission



_IRAS 4A outflows_ 9


observed in the SiO north of 4A2, previously interpreted as part of a
deflected jet from 4A2 by (Choi 2005), is, in fact, part of the cavity
C4-red.


_Overall comments:_ The structures mentioned earlier are the outcome

of assembling evidence that occasionally manifests in distinct tracers
and at different velocities. Notably, components of the same cavity
may not manifest simultaneously, particularly the eastern segments.


**4** **DISCUSSION**


**4.1** **The different ejection events in the IRAS 4A system**


_4A1 outflow systems:_
Our observations disclose the existence of two discernible outflow
systems (C1-red & C1-blue, and C3-blue) originating from 4A1.
The first (C1-red & C1-blue) is directed N-S, spanning a distance
up to 10 [′′] both to the north and south of the protostar. However,
the detection of the red-shifted eastern wall is somewhat limited,
with only 3 [′′] from it being observed. The cavity walls observed in
this system are delineated by SiO, H 2 CO, and HDCO, exhibiting a
velocity of approximately ∼18 km s [−][1] in red.
The second outflow system (C3-blue), driven by 4A1, is more
extended, reaching nearly 15 [′′] to the south of 4A1. Intriguingly, the
counterpart of the 4A1 southeast cavity is absent in the northern
region, implying its possible escape from the cloud, as in the case
of HH 46/47 (Arce et al. 2013). The blue-shifted lobe moves at a
velocity of ∼15 km s [−][1] . This outflow system is tilted by ∼12 [◦] with
respect to the N-S outflow system of 4A1, suggesting a possible jet
precession.


_4A2 outflow systems:_
Our observations unravel the intricate details of the 4A2 outflow
systems, where two distinct outflow systems (C2-red & C2-blue, and
C4-red & C4-blue) emerge, as detailed in the previous sections. The
first system (C2-red & C2-blue) extends approximately 18 [′′] both to
the north and south of 4A2, though the eastern lobe of the southern
outflow appears less distinct. This outflow system has a PA of ∼29 [◦] .
The cavity walls move at a velocity of ∼16 km s [−][1] in the red, and
they are observed with the three molecular tracers: SiO, H 2 CO, and
HDCO. Notably, we observe a velocity gradient in the red-shifted
cavity walls, with the west wall exhibiting a velocity of approximately
3–7 km s [−][1] red-shifted compared to the east wall. This intriguing
observation hints at a potential rotation of the cavity, adding a layer
of complexity to the dynamics of the 4A2 outflow system. Rotating
outflow cavities have been detected in other objects (e.g. HH 212
Codella et al. 2014, VLA1623 Ohashi et al. 2022). We expect that
if the jet is launched by a magnetic centrifugal mechanism it should
rotate consistently with the disk (e.g. HH 212 Lee et al. 2017) and
transfer the rotational velocity also to the cavities.
The second outflow system stemming from 4A2 (C4-red & C4blue) exhibits a greater extent, reaching almost 25 [′′] both to the north
and 23 [′′] to the south, though with a less distinct boundary in the
southern direction. This system has a PA of ∼26 [◦] . The cavity walls
move at a velocity of approximately 10 km s [−][1] in SiO and H 2 CO,
while HDCO does not exhibit these features. The absence of features

in HDCO could stem from a sensitivity issue (not connected though
to the excitation of the line), particularly considering that C4-red is
the oldest cavity. It is worth noting that HDCO might also be frozen
back onto the ice, further complicating its detection. A comprehensive astrochemical modelling could provide better insights into this

matter.


MNRAS **000**, 1–15 (2024)

Consequently, the two cavities of 4A2 show a slight misalignment of about 3 [◦], indicating a possible precession or rotation of the
ejection. Notably, the cavity of the second, more extended outflow
system displays lower velocities, aligning with the concept of an
older ejection event that has decelerated in the current epoch.


As mentioned in Sect. 3.4, we associated the SiO emission labelled
"C4-w" in Fig. 6 with the cavity wall of the second outflow system
rather than a bend induced by the interaction of the jet with an
obstructing dense core (Choi 2005). The SiO(1–0) emission observed
by Choi (2005) are similar to that of SiO (2–1) observed more recently
by De Simone et al. (2022), and to compare with our results we use
the latter for convenience.


In Fig. 2, we illustrate the SiO map observed by De Simone et al.
(2020a) alongside those from our study, overlaid with two solid ellipses the two ellipses representing the cavities of the aforementioned
two outflow systems. While the second ellipse encompasses "C4-w",
it does not reach the farthest SiO blob observed by Choi (2005); De
Simone et al. (2022) at ∼35 [′′] from 4A2, prompting a discussion on
its nature.


One can speculate that a third event gave rise to a third outflow system, whose bow-shock coincides with the farthest SiO blob observed
at ∼35 [′′] from 4A2. We represent it with a dashed ellipse in Fig. 2.


MNRAS **000**, 1–15 (2024)



This ellipse would be inclined by 31 [◦], slightly deviating from the
orientation of the other two ellipses (also see "Hypothetical cavity"
in Fig. 6). The sequence from the most distant ellipse (corresponding to the oldest ejection event) to the closest (and youngest event)
reads as 31 [◦], 26 [◦], and 29 [◦], suggesting once more a precession or
rotation of the ejections. This hypothesis is further supported by the
morphology of the blue outflow lobe of 4A2, which bears a notable
resemblance to the red lobe of the HH 46/47 outflow, displaying a
V-shape and a subsequent bifurcation in the cavity lobe. As proposed
by Arce et al. (2013), this feature could result from multiple mass
ejections that were not detected in our observations.
It is worth noting that the SiO blob at ∼35 [′′] from 4A2 observed
by Choi (2005); De Simone et al. (2022) is ∼6 [′′] out of our FoV and
was not detected in our observations due to filtering.


_The comparison between 4A1 and 4A2 ejections_

Our data shows that each of the protostars had at least two different
episodic events. However, it is worth noting that the outflow cavities
of 4A2, particularly C4-red, shows a much larger extension and is
detected at lower velocities. This would suggest that 4A2 is older
than 4A1, as previously suggested (e.g. Choi et al. 2007; Choi et al.
2011a; Santangelo et al. 2015; De Simone et al. 2020a).

_IRAS 4A outflows_ 11


**Table 2.** Summary of the components of the outflows emanating from IRAS 4A1 and IRAS 4A2 and detected in the SiO, H 2 CO and HDCO maps presented in
this work. The systemic velocity of the system is V _𝑠𝑦𝑠_ = 7 km s [−][1] (Su et al. 2019).


Present in
Source Component Molecules Extension Velocity Interval (km s [−][1] ) Notes
the maps of


SiO H 2 CO HDCO ′′ SiO H 2 CO HDCO


J1 ✓ ✓ x 5 [+25, +35] [+25, +35] x N-S Jet of 4A1 a, c, d, f, g


Bow1 x ✓ ✓ 10* x [+8, 13] [+8, +13] Bow-shock created by J1 a



4A1


4A2



C1-red ✓ ✓ ✓ 10 [+10, +22.5] [+8.3, +22.5] [+8.3, +19] N-S redshifted outflow cavity of 4A1includes Bow1 and C1-w a, e, g


C1-blue ✓ ✓ ✓ 10 [-24, +4.7] [-14, +6] [-1.2, +5.8] N-S blueshifted outflow cavity of 4A1 a, c, e, f, g


C3-blue ✓ ✓ ✓ 13 [-6.5, +5.5] [-5, +6] [+1, +7] 2 [nd] blueshifted outflow cavity of 4A1, PA −12 [◦] a, d, e


J2 ✓ x x 18* [+23, +35] x x Component connected with the NE-SW Jet of 4A2 a


Bow2 ✓ ✓ x 18* [+7.2, +19] [+8.3, +19] x Bow-shock created by J2 a, f

C2-red ✓ ✓ ✓ 18 [+8, +21] [+8.3, +19] [+8, +13] 1 [st] redshifted outflow cavity of 4A2, PA 29 [◦] a, b, c, d, e, g

includes Bow2, C2-w and C2-e


C2-blue ✓ ✓ ✓ 13 [-11, +6] [-4, +6] [+1, +7] 1 [st] blueshifted outflow cavity of 4A2, PA 29 [◦] a, g



C4-red ✓ ✓ x 25 [+7.2, +12.8] [+8.3, +12.5] x 2 [nd] redshfited outflow cavity of 4A2, PA 26 [◦] a

includes C4-w and C4-e


C4-blue ✓ weak x 23 [-5.5, //] x x 2 [nd] blueshifted outflow cavity of 4A2, PA 26 [◦] a


_**References:**_ (a) This work, (b) Choi (2005), (c) Santangelo et al. (2015), (d) Ching et al. (2016), (e) Su et al. (2019), (f) Taquet et al. (2020),
(g) Chuang et al. (2021).

         - These values represent the location of the feature from the corresponding protostar, rather than the extension.



**4.2** **Comparison with previous studies**


_Outflowing_ _motion_ : As highlighted in the Introduction, extensive
studies have focused on the outflows in the IRAS 4A system. While
the blue-shifted emission from the southern region has been more
clearly discernible when it comes to associating the observed feature
with one of the protostars, the interpretation of the emission to the
north of the protostars has proven to be challenging. This difficulty
arises from the complex overlap between components originating
from 4A1 and 4A2, hindering a clear understanding of the underlying
processes in this region.
In the context of the jets within the IRAS 4A system, our observations have unveiled the previously identified northern jet originating
from 4A1 (Santangelo et al. 2015; Taquet et al. 2020). The enhanced
angular resolution of our data has provided a clearer view of this jet,
allowing us to resolve intricate bullet structures within it. Notably,
our observations have also introduced a new element to the under
standing of the system: a SiO component associated with the primary
jet of 4A2. This component also exhibits bullet-like structures.
Regarding the outflowing motion to the north of the protostars,
previous studies presented different hypotheses regarding its origin.
Some proposed it solely from the 4A2 outflow (Choi 2005), while
others attributed it to the bent outflow of 4A1 (Ching et al. 2016).
Alternatively, certain studies argued for the presence of two extended
bent cavities—one from 4A1 and another from 4A2 (Chuang et al.
2021). Our observations suggest a scenario distinct from these interpretations, as summarised in Table 2. We contend that neither of the
cavities is bent. In fact, the non-detection of the bow-shock Bow1 in
the previous studies has led to uncertainties regarding the extent and
orientation of the cavity associated with 4A1, where it was thought
that it is extended up to ∼17 [′′] and bent to the east. Our observations
propose that the cavity is oriented N-S and does not extend farther
than 10 [′′] from 4A1. It is also somewhat encompassed within that
of 4A2, at least in projection. This N-S outflow cavity of 4A1 has a
blue-shifted counterpart to the south of the protostar, where a second



cavity (C3-blue) is also detected. The latter is misaligned with the
former by ∼12 [◦] . The blueshifted cavities are both present in the SO
maps of Chuang et al. (2021), but only C3-blue was identified.
In 4A2, previous studies suggested the existence of an extended
outflow with a PA of approximately 18.9 [◦], that changes direction
around 20 [′′] (i.e., directional variability) attributed to an interaction
with an obstructing dense core (Choi 2005). Recent higher-resolution
observations have confirmed the presence of an outflow cavity with
a PA ranging from 19 [◦] to 22 [◦] (e.g. Ching et al. 2016; Chuang et al.
2021). However, Marvel et al. (2008) noted that the position angle
of the water maser outflow in IRAS 4A differs from the position
angles associated with the larger-scale outflows originating from the
two sources within the system. Our current data reveal the existence
of a high-velocity outflow cavity originating from 4A2, aligning
closely with the jet observed in our dataset with a PA of ∼29 [◦] .
Furthermore, we distinguish between LV and HV outflow cavities in
4A2, clarifying that what was previously thought to be “directional
variability” of the 4A2 outflow (C4-w) is simply an extension of the
LV component of the western cavity wall.

_Jet_ _precession_ : The misalignment between the outflow systems in
4A1 and those in 4A2, suggests that the jets of the two sources are
actually precessing. To verify that the misalignment is attributed to
a precession rather than the potential shifting position of protostars
over time, we examined the presence of proper motions of this source.
We found no significant proper motion, with the coordinates showing
only minor fluctuations within the uncertainties since their initial determination (Looney et al. 2000; Reipurth et al. 2002), as compared
to recent derivations (De Simone et al. 2020b). While the possibility
of precession in the 4A1 jet has not been proposed before, previous
studies hinted at the precession scenario in 4A2 to explain specific
features observed in the IRAS 4A system (e.g. Choi et al. 2006; Santangelo et al. 2015; Chuang et al. 2021). Choi et al. (2006) referred
to the mechanism as “drifting” rather than precession due to a lack
of evidence for periodic change. In another work, Choi et al. (2011b)
have suggested that the 4A2 jet is rotating within a cone of open

MNRAS **000**, 1–15 (2024)

12 _L. Chahine et al._


ing half-angle ∼3.1 [◦] . The cause of the 4A2 jet’s precession remains
unclear. Several studies suggested that the precession might result
from a close unresolved binary system, with a separation of 30-80 au
(Choi et al. 2006), 32 au (Marvel et al. 2008) or larger than ∼12 au
(Chuang et al. 2021). Alternatively, Chuang et al. (2021) proposed
that a misalignment between the magnetic field and the cloud’s angular momentum vector may induce precession. This scenario may also
apply to IRAS 4A1. Particularly noteworthy is the resemblance of the
blueshifted outflow cavities to the misaligned outflows observed in
HOPS 373, where one cavity is “nested” within the other (Lee et al.
2024). The authors propose that the observed misaligned outflows
may originate from either a single protostar, following a reorientation
of its angular momentum axis, or from a close protostellar binary,
with each outflow linked to a distinct binary component. They further
suggest that, in the first scenario, the reorientation could result from
a change in the angular momentum axis of the accreting gas or from
a misalignment between the rotation axis of the core and the orientation of the global magnetic field (e.g. Machida et al. 2020; Okoda
et al. 2021). With our observations, it is challenging to determine the
origin of the precession of 4A1 and 4A2’ jets, as the identification
of a potential binary companion for each protostar would require
an angular resolution of about 12 au. A reorientation of the system
could be plausible given the misalignment of the magnetic field in
the IRAS 4A envelope with the rotation axis of the circumbinary
envelope (Chuang et al. 2021 and references therein). Further observations with higher angular resolution are needed to resolve the discs
and investigate the possibility of close binaries for each protostar.


_Effect_ _of_ _stellar_ _multiplicity_ : The influence of stellar multiplicity
on outflow activity during the protostellar stage remains inadequately
characterised. One notable effect is the precession of the disc, which
can alter the orientation and morphology of the outflows. Precession
refers to the rotation of the jet axis within a cone, leading to changes
in the direction of the outflow. This process was observed towards
several sources and was linked to the presence of a binary companion
(e.g. HOPS-370 Tobin et al. 2019b; Chahine et al. 2022), or a close
unresolved binary (e.g. L1157 Podio et al. 2016, CepE-A de A.
Schutzer et al. 2022, HOPS-317 in the HH 24 complex Reipurth
et al. 2023, HOPS-373SW Lee et al. 2024) Additionally, binary and
multiple systems may exhibit jet wiggling, where the orientation of
the jet remains constant, but the spatial position of the launching
point varies as the stars orbit each other (e.g. HH 211 Lee et al.
2010, HH 212 Lee et al. 2017, CepE-A de A. Schutzer et al. 2022,
VLA15 in OMC-2 FIR 4 Chahine et al. 2022, SSV63 and Jet C in the
HH 24 complex Reipurth et al. 2023). Furthermore, the disturbance
of the disc due to the presence of a companion can lead to increased
accretion onto the protostars, potentially driving strong outbursts
of outflow activity (e.g. HH 175 Reipurth & Friberg 2021). While
precession has been observed in the IRAS 4A system, potentially
linked to stellar multiplicity, further investigations are warranted,
particularly at the scale of the circumstellar discs. This additional
scrutiny is necessary to discern any signs of disc disturbance or
misaligned accretion onto the protostars.


**5** **CONCLUSIONS**


In this study, we delved into the morphology and kinematics of the
jets and outflows towards the IRAS 4A system using three distinct
tracers: SiO, H 2 CO, and HDCO, at a spatial resolution of ∼150
au. The use of these three tracers proved to be indispensable in
revealing new features, piecing together the intricate puzzle, and
gaining a comprehensive understanding of the larger framework, as


MNRAS **000**, 1–15 (2024)



each tracer contributed a crucial component to the analysis. Our main
conclusions are summarised below.


(i) We have successfully identified two distinct jets in the redshifted emission, originating from 4A1 and 4A2. The jet from 4A1
is oriented in a N-S direction, while that from 4A2, observed for the
first time, exhibits a NE-SW orientation with a PA of 29 [◦] .

(ii) Each protostar has two outflow systems, with 4A1 showcasing
three outflow cavities and 4A2 presenting four. Contrary to prior
studies, we argue that none of the outflows is bent.

(iii) We observe an outflow cavity to the north of IRAS 4A1 and
two cavities to its south. One of these southern cavities aligns with
a N-S direction, while the other exhibits a PA of -12 [◦] without a
corresponding counterpart in the north. The misalignment of these
cavities suggests the possibility of a precession occurring within the
4A1 jet.

(iv) The analysis of the outflows originating from IRAS 4A2 reveals the presence of two cavities in both the northern and southern
directions, albeit with less distinct emission in the south. The cavities
are slightly misaligned, and the more extended is moving at lower
velocities, suggesting it is potentially stemming from an older ejection event. In addition, the cavity moving at higher velocities shows
an indication of rotation


(v) Our study challenges previous interpretations of the directional variability observed in the outflow of IRAS 4A2, suggesting
instead that it represents the remnants of the western wall of the lowvelocity outflow cavity. We speculate on the occurrence of a third
event that was not detected in our data.


In summary, our study underscores the importance of utilising diverse tracers beyond traditional ones, emphasising the significance
of comprehensive studies in unravelling the complexities of outflow

systems.


**ACKNOWLEDGEMENTS**


We gratefully acknowledge Dr. Fabien Louvet for their valuable
contribution to the discussion. This project has received funding from the EC H2020 research and innovation programme
for the project ‘Astro-Chemical Origins’ (ACO; No. 811312)
and the European Research Council (ERC) projects ‘The Dawn
of Organic Chemistry’ (DOC; No.741002), and ‘Stellar-MADE’
(No.101042275). This paper makes use of the following ALMA data
set: ADS/JAO.ALMA#2018.1.01205.L (PI: Satoshi Yamamoto).
ALMA is a partnership of the ESO (representing its member states),
the NSF (USA) and NINS (Japan), together with the NRC (Canada)
and the NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO,
the AUI/NRAO, and the NAOJ. The authors thank the ALMA and
NRAO staff for their support. Part of the data reduction/combination
presented in this paper was performed using the GRICAD infrastructure ( `[https://gricad.univ-grenoble-alpes.fr](https://gricad.univ-grenoble-alpes.fr)` ). ClCo, LP,
and GS acknowledge the PRIN-MUR 2020 BEYOND-2p (Astrochemistry beyond the second period elements, Prot. 2020AFB3FX),
the PRIN MUR 2022 FOSSILS (Chemical origins: linking the fossil
composition of the Solar System with the chemistry of protoplanetary disks, Prot. 2022JC2Y93), the project ASI-Astrobiologia 2023
MIGLIORA (Modeling Chemical Complexity, F83C23000800005),
and the INAF-GO 2023 fundings PROTO-SKA (Exploiting ALMA
data to study planet forming disks: preparing the advent of SKA,
C13C23000770005). LP acknowledges the INAF Mini-Grant 2022

“Chemical Origins” (PI: L. Podio). GS acknowledges the INAFMinigrant 2023 TRIESTE (“TRacing the chemIcal hEritage of our
originS: from proTostars to planEts”; PI: G. Sabatini). ClCo and
LP also acknowledge the financial support under the National Recovery and Resilience Plan (NRRP), Mission 4, Component 2, Investment 1.1, Call for tender No. 104 published on 2.2.2022 by the
Italian Ministry of University and Research (MUR), funded by the
European Union – NextGenerationEU– Project Title 2022JC2Y93
ChemicalOrigins: linking the fossil composition of the Solar System
with the chemistry of protoplanetary disks – CUP J53D23001600006
- Grant Assignment Decree No. 962 adopted on 30.06.2023 by the
Italian Ministry of Ministry of University and Research (MUR). EB
acknowledges support from the Deutsche Forschungsgemeinschaft
(DFG, German Research Foundation) under Germany´s Excellence
Strategy – EXC 2094 – 390783311. M.B. acknowledges support from
the European Research Council (ERC) Advanced Grant MOPPEX
833460. SBC was supported by the NASA Planetary Science Division Internal Scientist Funding Program through the Fundamental
Laboratory Research work package (FLaRe).


**DATA AVAILABILITY**


The raw data are available on the ALMA archive at the end of the

proprietary period (ADS/JAO.ALMA#2018.1.01205.L).


**REFERENCES**


Alves F. O., Caselli P., Girart J. M., Segura-Cox D., Franco G. A. P.,
[Schmiedeke A., Zhao B., 2019, Science, 366, 90](http://dx.doi.org/10.1126/science.aaw3491)
Arce H. G., Mardones D., Corder S. A., Garay G., Noriega-Crespo A., Raga
[A. C., 2013, ApJ, 774, 39](http://dx.doi.org/10.1088/0004-637X/774/1/39)
[Bachiller R., 1996, ARA&A, 34, 111](http://dx.doi.org/10.1146/annurev.astro.34.1.111)
[Bachiller R., Liechti S., Walmsley C. M., Colomer F., 1995, A&A, 295, L51](https://ui.adsabs.harvard.edu/abs/1995A&A...295L..51B)
[Bally J., 2016, ARA&A, 54, 491](http://dx.doi.org/10.1146/annurev-astro-081915-023341)
[Bally J., Lada C. J., 1983, ApJ, 265, 824](http://dx.doi.org/10.1086/160729)
Bally J., Reipurth B., Davis C., 2014, in Beuther H., Klessen R. S., Dullemond C. P., Henning T., eds, Protostars and Planets VI. pp 215–230
( `[arXiv:1403.7143](http://arxiv.org/abs/1403.7143)` )
Blake G. A., Sandell G., van Dishoeck E. F., Groesbeck T. D., Mundy L. G.,
[Aspin C., 1995, ApJ, 441, 689](http://dx.doi.org/10.1086/175392)
[Bocquet R., et al., 1996, Journal of Molecular Spectroscopy, 177, 154](http://dx.doi.org/10.1006/jmsp.1996.0128)
[Bocquet R., et al., 1999, Journal of Molecular Spectroscopy, 195, 345](http://dx.doi.org/10.1006/jmsp.1999.7836)
[CASA Team et al., 2022, PASP, 134, 114501](http://dx.doi.org/10.1088/1538-3873/ac9642)
[Caselli P., Hartquist T. W., Havnes O., 1997, A&A, 322, 296](https://ui.adsabs.harvard.edu/abs/1997A&A...322..296C)
[Chahine L., et al., 2022, A&A, 667, A6](http://dx.doi.org/10.1051/0004-6361/202243799)
[Ching T.-C., Lai S.-P., Zhang Q., Yang L., Girart J. M., Rao R., 2016, ApJ,](http://dx.doi.org/10.3847/0004-637X/819/2/159)

[819, 159](https://ui.adsabs.harvard.edu/abs/2016ApJ...819..159C)
[Choi M., 2001, ApJ, 553, 219](http://dx.doi.org/10.1086/320657)
[Choi M., 2005, ApJ, 630, 976](http://dx.doi.org/10.1086/432113)
Choi M., Hodapp K. W., Hayashi M., Motohara K., Pak S., Pyo T.-S., 2006,

[ApJ, 646, 1050](http://dx.doi.org/10.1086/505037)
[Choi M., Tatematsu K., Park G., Kang M., 2007, ApJ, 667, L183](http://dx.doi.org/10.1086/522116)
[Choi M., Kang M., Tatematsu K., Lee J.-E., Park G., 2011a, Publications of](http://dx.doi.org/10.1093/pasj/63.6.1281)
[the Astronomical Society of Japan, 63, 1281](http://dx.doi.org/10.1093/pasj/63.6.1281)
[Choi M., Kang M., Tatematsu K., 2011b, ApJ, 728, L34](http://dx.doi.org/10.1088/2041-8205/728/2/L34)
[Chuang C.-Y., Aso Y., Hirano N., Hirano S., Machida M. N., 2021, ApJ, 916,](http://dx.doi.org/10.3847/1538-4357/abfdbb)

[82](https://ui.adsabs.harvard.edu/abs/2021ApJ...916...82C)

Codella C., Cabrit S., Gueth F., Cesaroni R., Bacciotti F., Lefloch B., Mc[Caughrean M. J., 2007, A&A, 462, L53](http://dx.doi.org/10.1051/0004-6361:20066800)
[Codella C., et al., 2014, A&A, 568, L5](http://dx.doi.org/10.1051/0004-6361/201424103)

[Codella C., et al., 2017, A&A, 605, L3](http://dx.doi.org/10.1051/0004-6361/201731249)

Codella C., Ceccarelli C., Chandler C., Sakai N., Yamamoto S., FAUST Team
[2021, Frontiers in Astronomy and Space Sciences, 8, 227](http://dx.doi.org/10.3389/fspas.2021.782006)
[De Simone M., et al., 2020a, A&A, 640, A75](http://dx.doi.org/10.1051/0004-6361/201937004)



_IRAS 4A outflows_ 13


[De Simone M., et al., 2020b, ApJ, 896, L3](http://dx.doi.org/10.3847/2041-8213/ab8d41)
[De Simone M., et al., 2022, MNRAS,](http://dx.doi.org/10.1093/mnras/stac083)
Di Francesco J., Myers P. C., Wilner D. J., Ohashi N., Mardones D., 2001,

[ApJ, 562, 770](http://dx.doi.org/10.1086/323854)
[Evans L., et al., 2023, A&A, 678, A160](http://dx.doi.org/10.1051/0004-6361/202346428)
Fontani F., Codella C., Ceccarelli C., Lefloch B., Viti S., Benedettini M.,
[2014, ApJ, 788, L43](http://dx.doi.org/10.1088/2041-8205/788/2/L43)
Frank A., et al., 2014, in Beuther H., Klessen R. S., Dullemond C. P., Henning
T., eds, Protostars and Planets VI. pp 451–474 ( `[arXiv:1402.3553](http://arxiv.org/abs/1402.3553)` ),
[doi:10.2458/azu_uapress_9780816531240-ch020](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch020)
[Girart J. M., Crutcher R. M., Rao R., 1999, ApJ, 525, L109](http://dx.doi.org/10.1086/312345)
[Gusdorf A., Pineau Des Forêts G., Cabrit S., Flower D. R., 2008, A&A, 490,](http://dx.doi.org/10.1051/0004-6361:200810443)

[695](https://ui.adsabs.harvard.edu/abs/2008A&A...490..695G)

[Hara C., et al., 2013, ApJ, 771, 128](http://dx.doi.org/10.1088/0004-637X/771/2/128)
[Hara C., et al., 2021, ApJ, 912, 34](http://dx.doi.org/10.3847/1538-4357/abb810)
[Högbom J. A., 1974, A&AS, 15, 417](https://ui.adsabs.harvard.edu/abs/1974A&AS...15..417H)
Hsieh C.-H., Lai S.-P., Cheong P.-I., Ko C.-L., Li Z.-Y., Murillo N. M., 2020,

[ApJ, 894, 23](http://dx.doi.org/10.3847/1538-4357/ab7b69)
[Jørgensen J. K., et al., 2007, ApJ, 659, 479](http://dx.doi.org/10.1086/512230)
Koumpia E., Semenov D. A., van der Tak F. F. S., Boogert A. C. A., Caux E.,
[2017, A&A, 603, A88](http://dx.doi.org/10.1051/0004-6361/201630160)
[Kwan J., Scoville N., 1976, ApJ, 210, L39](http://dx.doi.org/10.1086/182298)
[Lattanzi V., et al., 2023, A&A, 671, A35](http://dx.doi.org/10.1051/0004-6361/202142736)

[Lee C.-F., 2020, A&ARv, 28, 1](http://dx.doi.org/10.1007/s00159-020-0123-7)
Lee C.-F., Hasegawa T. I., Hirano N., Palau A., Shang H., Ho P. T. P., Zhang
[Q., 2010, ApJ, 713, 731](http://dx.doi.org/10.1088/0004-637X/713/2/731)
[Lee C.-F., Hirano N., Zhang Q., Shang H., Ho P. T. P., Mizuno Y., 2015, ApJ,](http://dx.doi.org/10.1088/0004-637X/805/2/186)

[805, 186](https://ui.adsabs.harvard.edu/abs/2015ApJ...805..186L)
[Lee C.-F., Ho P. T. P., Li Z.-Y., Hirano N., Zhang Q., Shang H., 2017, Nature](http://dx.doi.org/10.1038/s41550-017-0152)
[Astronomy, 1, 0152](http://dx.doi.org/10.1038/s41550-017-0152)
Lee S., Lee J.-E., Johnstone D., Herczeg G. J., Aikawa Y., 2024, [arXiv](http://dx.doi.org/10.48550/arXiv.2401.12449) e[prints, p. arXiv:2401.12449](http://dx.doi.org/10.48550/arXiv.2401.12449)
[Lefloch B., Castets A., Cernicharo J., Loinard L., 1998, ApJ, 504, L109](http://dx.doi.org/10.1086/311581)
Lefloch B., Ceccarelli C., Codella C., Favre C., Podio L., Vastel C., Viti S.,
[Bachiller R., 2017, MNRAS, 469, L73](http://dx.doi.org/10.1093/mnrasl/slx050)
[Looney L. W., Mundy L. G., Welch W. J., 2000, ApJ, 529, 477](http://dx.doi.org/10.1086/308239)
Louvet F., Dougados C., Cabrit S., Mardones D., Ménard F., Tabone B., Pinte
[C., Dent W. R. F., 2018, A&A, 618, A120](http://dx.doi.org/10.1051/0004-6361/201731733)

[Machida M. N., Hirano S., Kitta H., 2020, MNRAS, 491, 2180](http://dx.doi.org/10.1093/mnras/stz3159)
Marvel K. B., Wilking B. A., Claussen M. J., Wootten A., 2008, [ApJ,](http://dx.doi.org/10.1086/590465) [685,](https://ui.adsabs.harvard.edu/abs/2008ApJ...685..285M)
[285](https://ui.adsabs.harvard.edu/abs/2008ApJ...685..285M)

[Müller H. S. P., Lewen F., 2017, Journal of Molecular Spectroscopy, 331, 28](http://dx.doi.org/10.1016/j.jms.2016.10.004)
Müller H. S. P., Spezzano S., Bizzocchi L., Gottlieb C. A., Degli Esposti C.,
[McCarthy M. C., 2013, Journal of Physical Chemistry A, 117, 13843](http://dx.doi.org/10.1021/jp408391f)
[Noriega-Crespo A., Raga A. C., 2012, ApJ, 750, 101](http://dx.doi.org/10.1088/0004-637X/750/2/101)
[Ohashi S., et al., 2022, ApJ, 927, 54](http://dx.doi.org/10.3847/1538-4357/ac4cae)
[Okoda Y., et al., 2021, ApJ, 910, 11](http://dx.doi.org/10.3847/1538-4357/abddb1)
Oya Y., Watanabe Y., López-Sepulcre A., Ceccarelli C., Lefloch B., Favre C.,
[Yamamoto S., 2021, ApJ, 921, 12](http://dx.doi.org/10.3847/1538-4357/ac0a72)
[Pety J., Gueth F., Guilloteau S., Dutrey A., 2006, A&A, 458, 841](http://dx.doi.org/10.1051/0004-6361:20065814)
[Podio L., et al., 2016, A&A, 593, L4](http://dx.doi.org/10.1051/0004-6361/201628876)

[Podio L., et al., 2021, A&A, 648, A45](http://dx.doi.org/10.1051/0004-6361/202038429)
Raga A. C., Reipurth B., Castellanos-Ramírez A., Chiang H.-F., Bally J.,
[2015, AJ, 150, 105](http://dx.doi.org/10.1088/0004-6256/150/4/105)
[Reipurth B., Friberg P., 2021, MNRAS, 501, 5938](http://dx.doi.org/10.1093/mnras/staa3965)
[Reipurth B., Yu K. C., Heathcote S., Bally J., Rodríguez L. F., 2000, AJ, 120,](http://dx.doi.org/10.1086/301510)

[1449](https://ui.adsabs.harvard.edu/abs/2000AJ....120.1449R)

[Reipurth B., Rodríguez L. F., Anglada G., Bally J., 2002, AJ, 124, 1045](http://dx.doi.org/10.1086/341172)
[Reipurth B., et al., 2023, AJ, 165, 209](http://dx.doi.org/10.3847/1538-3881/acadd4)
[Rivera-Ortiz P. R., de A. Schutzer A., Lefloch B., Gusdorf A., 2023, A&A,](http://dx.doi.org/10.1051/0004-6361/202245085)

[672, A116](https://ui.adsabs.harvard.edu/abs/2023A&A...672A.116R)
[Santangelo G., et al., 2015, A&A, 584, A126](http://dx.doi.org/10.1051/0004-6361/201526323)
[Sato A., et al., 2023a, ApJ, 944, 92](http://dx.doi.org/10.3847/1538-4357/aca7c9)
[Sato A., et al., 2023b, ApJ, 958, 102](http://dx.doi.org/10.3847/1538-4357/ad0132)
Schilke P., Walmsley C. M., Pineau des Forets G., Flower D. R., 1997, A&A,

[321, 293](https://ui.adsabs.harvard.edu/abs/1997A&A...321..293S)

Su Y.-N., Liu S.-Y., Li Z.-Y., Lee C.-F., Hirano N., Takakuwa S., Hsieh I. T.,
[2019, ApJ, 885, 98](http://dx.doi.org/10.3847/1538-4357/ab4818)


MNRAS **000**, 1–15 (2024)

14 _L. Chahine et al._


[Taquet V., et al., 2020, A&A, 637, A63](http://dx.doi.org/10.1051/0004-6361/201937072)
[Tobin J. J., et al., 2019a, ApJ, 870, 81](http://dx.doi.org/10.3847/1538-4357/aaef87)
[Tobin J. J., et al., 2019b, ApJ, 886, 6](http://dx.doi.org/10.3847/1538-4357/ab498f)
Yıldız U. A., Kristensen L. E., van Dishoeck E. F., Belloche A., van Kempen
[T. A., Hogerheĳde M. R., Güsten R., van der Marel N., 2012, A&A, 542,](http://dx.doi.org/10.1051/0004-6361/201118368)
[A86](https://ui.adsabs.harvard.edu/abs/2012A&A...542A..86Y)

Zucker C., Schlafly E. F., Speagle J. S., Green G. M., Portillo S. K. N.,
[Finkbeiner D. P., Goodman A. A., 2018, ApJ, 869, 83](http://dx.doi.org/10.3847/1538-4357/aae97c)
Zurlo A., Garufi A., Pérez S., Alves F. O., Girart J. M., Zhu Z., Franco G.
[A. P., Cleeves L. I., 2021, ApJ, 912, 64](http://dx.doi.org/10.3847/1538-4357/abec42)
[de A. Schutzer A., et al., 2022, A&A, 662, A104](http://dx.doi.org/10.1051/0004-6361/202142931)


MNRAS **000**, 1–15 (2024)

_IRAS 4A outflows_ 15



**APPENDIX A:** **MAPS**


In Fig. A1 we show a zoomed view of the SiO emission within the
HV1 velocity interval. In Figs. A2 and A4 we report the channels
maps of HDCO and H 2 CO in the redshifted LV and IV regimes. In
Fig. A3 we present the detailed blueshifted channel map of H 2 CO. In
Fig. A5 we show the integrated intensity maps of the different tracers
used to probe the emission towards IRAS 4A, with superimposed
ellipses and arrows representing all the features identified in this
work.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.







**Figure** **A1.** Zoomed view of the SiO emission within the HV1 velocity
interval. The contours are as in the HV1 panel of Fig. 1. The positions of
IRAS 4A1 and IRAS 4A2 are marked with stars. The jets from each source

are marked with arrows.


MNRAS **000**, 1–15 (2024)

16 _L. Chahine et al._












|C1 -w|Col2|Col3|
|---|---|---|
|||C2-w|
||C2-e<br>Bow1<br>C2-w|C4-e<br>|



**Figure A2.** Channel map of the redshifted emission of HDCO. The contour levels start at 3 _𝜎_ and increase by 3 _𝜎_ step with _𝜎_ = 0.40 mJy beam [−][1] km s [−][1] . The
velocity of each channel is indicated in the upper-right corner of each panel. The features mentioned in the text are labelled in grey. The synthesised beam is
depicted in the lower-left corner of the bottom-left panel.







**Figure A3.** Channel map of the blueshifted emission of H 2 CO between -12.5 and +3 km s [−][1] . The velocity intervals and their corresponding labels are shown
at the upper right corners of each channel map panel. The contour levels start at 5 _𝜎_ and increase by 20 _𝜎_ step with _𝜎_ = 0.75 mJy beam [−][1] km s [−][1] . The features
mentioned in the text are labelled in grey. The positions of IRAS 4A1 and IRAS 4A2 are marked with stars. The synthesised beam is depicted in the lower-left
corner of the bottom-left panel.


MNRAS **000**, 1–15 (2024)

_IRAS 4A outflows_ 17













**Figure A4.** Channel map of the redshifted IV and LV emission of H 2 CO. Each panel displays the integrated velocity range of ±0.6 km s [−][1] centred around the
velocity specified in the upper right corner. The contour levels start at 5 _𝜎_ and increase by 20 _𝜎_ step with _𝜎_ = 0.45 mJy beam [−][1] km s [−][1] . The features mentioned
in the text are labelled in grey. The positions of IRAS 4A1 and IRAS 4A2 are marked with stars. The synthesised beam is depicted in the lower-left corner of the
bottom-left panel.


Hypothetical

Cavity



J2



C4-w



**Bow1**


C4-e C2-w


J1


C1-w

C2-e


C1-red


C1-blue


C3-blue



C2-blue


C4-blue



**Figure A5.** Integrated intensity maps of SiO, H 2 CO and HDCO towards IRAS 4A with overlaid ellipses and arrows representing all the features identified in
this work. The velocity range are as in the main text. The contours of SiO are at 5 _𝜎_ and 150 _𝜎_ ( _𝜎_ = 0.81 mJy beam [−][1] km s [−][1] ), those of H 2 CO are at 5, 20 _𝜎_
and 40 _𝜎_ ( _𝜎_ = 5 mJy beam [−][1] km s [−][1] ) and the ones of HDCO are at 5 _𝜎_ and 25 _𝜎_ ( _𝜎_ = 0.4 mJy beam [−][1] km s [−][1] ). The positions of IRAS 4A1 and IRAS 4A2 are
marked with stars. All the feature identified in this work and summarised in both Fig. 6 and Table. 2 are represented with ellipses and arrows.


MNRAS **000**, 1–15 (2024)


</paper>

## Items to check

```json
[
 {
  "path": "processing.imaging.deconvolver.evidence[0]",
  "value": "Högbom algorithm",
  "failed_quote": "The resulting continuum-subtracted cubes were cleaned using Högbom algorithm (Högbom 1974) and natural weighting in the IRAM-GILDAS software package 3 ."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "natural weighting",
  "failed_quote": "The resulting continuum-subtracted cubes were cleaned using Högbom algorithm (Högbom 1974) and natural weighting in the IRAM-GILDAS software package 3 ."
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Cleaning continuum-subtracted line cubes using Högbom algorithm with natural weighting and performing data analysis",
  "failed_quote": "The resulting continuum-subtracted cubes were cleaned using Högbom algorithm (Högbom 1974) and natural weighting in the IRAM-GILDAS software package 3 ."
 },
 {
  "path": "findings_qualitative[2].evidence[1]",
  "value": "The feature at 20–25'' north of 4A2 previously interpreted as a sharp bend or directional variability is instead the remnant of the western wall of a second, low-velocity outflow cavity (C4-red).",
  "failed_quote": "Our study challenges previous interpretations of the directional variability observed in the outflow of IRAS 4A2, suggesting instead that it represents the remnants of the western wall of the low-velocity outflow cavity."
 }
]
```
