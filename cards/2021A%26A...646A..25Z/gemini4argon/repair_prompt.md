# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...646A..25Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. hmsc ©ESO 2021
November 3, 2021

## H ii **regions and high-mass starless clump candidates**

### II. Fragmentation and induced star formation at ∼ 0 . 025 pc scale: An ALMA **continuum study**


S. Zhang [1], A. Zavagno [1][,][ 2], A. López-Sepulcre [3][,][ 4], H. Liu [5][,][ 6][,][ 7], F. Louvet [8], M. Figueira [9], D. Russeil [1], Y. Wu [10], J. Yuan [11],
and T. G. S. Pillai [12][,][ 13]


1 Aix Marseille Univ, CNRS, CNES, LAM, Marseille, France
e-mail: `sijuzhangastro@gmail.com`
2 Institut Universitaire de France (IUF)
3 Univ. Grenoble Alpes, CNRS, Institut de Planétologie et d’Astrophysique de Grenoble (IPAG), 38000 Grenoble, France
4 Institut de Radioastronomie Millimétrique (IRAM), 300 rue de la Piscine, 38406 Saint-Martin-D’Hères, France
5 Department of Astronomy, Yunnan University, Kunming, 650091, China
6 CASSACA, China-Chile Joint Center for Astronomy, Camino El Observatorio #1515, Las Condes, Santiago, Chile
7 Departamento de Astronomía, Universidad de Concepción, Av. Esteban Iturra s/n, Distrito Universitario, 160-C, Chile
8 Departmento de Astronomia de Chile, Universidad de Chile, Santiago, Chile
9 National Centre for Nuclear Research, ul. Pasteura 7, 02-093, Warszawa
10 Department of Astronomy, Peking University, 100871 Beijing, China
11 National Astronomical Observatories, Chinese Academy of Sciences, 20A Datun Road, Chaoyang District, Beijing 100012, China
12 Institute for Astrophysical Research, 725 Commonwealth Ave, Boston University Boston, MA 02215, USA
13 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany


Received May 1, 2020; Accepted November, 24, 2020


**ABSTRACT**


_Context._ The ionization feedback from H ii regions modifies the properties of high-mass starless clumps (HMSCs, of several hundred
to a few thousand solar masses with a typical size of 0.1-1 pc), such as dust temperature and turbulence, on the clump scale. The
question of whether the presence of H ii regions modifies the core-scale (∼ 0.025 pc) fragmentation and star formation in HMSCs
remains to be explored.
_Aims._ We aim to investigate the difference of 0.025 pc-scale fragmentation between candidate HMSCs that are strongly impacted
by H ii regions and less disturbed ones. We also search for evidence of mass shaping and induced star formation in the impacted
candidate HMSCs.
_Methods._ Using the ALMA 1.3 mm continuum, with a typical angular resolution of 1.3 [′′], we imaged eight candidate HMSCs,
including four impacted by H ii regions and another four situated in the quiet environment. The less-impacted candidate HMSCs are
selected on the basis of their similar mass and distance compared to the impacted ones to avoid any possible bias linked to these
parameters. We carried out a comparison between the two types of candidate HMSCs. We used multi-wavelength data to analyze the
interaction between H ii regions and the impacted candidate HMSCs.
_Results._ A total of 51 cores were detected in eight clumps, with three to nine cores for each clump. Within our limited sample, we
did not find a clear difference in the ∼ 0.025 pc-scale fragmentation between impacted and non-impacted candidate HMSCs, even
though H ii regions seem to affect the spatial distribution of the fragmented cores. Both types of candidate HMSCs present a thermal
fragmentation with two-level hierarchical features at the clump thermal Jeans length λ [th] J,clump [and] [0.3][λ] [th] J,clump [.] [The] [ALMA] [emission]
morphology of the impacted candidate HMSCs AGAL010.214-00.306 and AGAL018.931-00.029 sheds light on the capacities of
H ii regions to shape gas and dust in their surroundings and possibly to trigger star formation at ∼ 0.025 pc-scale in candidate
HMSCs.
_Conclusions._ The fragmentation at ∼ 0.025 pc scale for both types of candidate HMSCs is likely to be thermal-dominant, meanwhile
H ii regions probably have the capacity to assist in the formation of dense structures in the impacted candidate HMSCs. Future ALMA
imaging surveys covering a large number of impacted candidate HMSCs with high turbulence levels are needed to confirm the trend
of fragmentation indicated in this study.


**Key** **words.** Stars: formation – Stars: massive – ISM: H ii regions – ISM: structure – Submillimeter: ISM – Techniques: interferometric



**1.** **Introduction**


The formation process behind high-mass stars (> 8 M ⊙ ) is still a
matter of debate due to the unsolved questions coming from both
the observational and theoretical sides. Apart from the mechanisms that lead to the formation of high-mass stars, the role of



the environment and its impact on the future star-formation properties are still poorly known.
Observationally, high-mass star-formation (HMSF) regions
are often situated at further distances (several kpc) and deeply
embedded in the molecular clouds. In these regions, the study
of embedded structures smaller than 0.1 pc commonly requires


Article number, page 1 of 30

_A&A proofs:_ manuscript no. hmsc



high-resolution interferometric (sub)millimeter or centimeter
observations.

Theoretically, the two widely discussed HMSF models,
namely, monolithic collapse (MC) and competitive accretions
(CA), propose a different initial mass for the cores embedded in
the massive clumps (Zinnecker & Yorke 2007). The MC model
proposes that massive stars form by disk accreting masses from
the hosted turbulent massive cores. This picture is qualitatively
similar to the scale-up version of low-mass star formation (McKee & Tan 2003; Krumholz et al. 2009). The CA model proposes
that the massive clumps fragment into a number of cores with
Jeans mass, around one to a few solar masses, in the thermaldominant case. Furthermore, the cores located in the gravitational potential well center of the hosted massive clumps are
expected to more easily accrete masses to form massive stars
(Bonnell et al. 2001, 2004). There are a number of the Atacama
Large Millimeter/submillimeter Array (ALMA) results that have
proven to be consistent with the CA model (Cyganowski et al.
2017; Fontani et al. 2018).
One of the key methods in differentiating the mechanism of
initial HMSF is to study the fragmentation of massive clumps
(typical size of 0.1 to 1 pc) at their earliest evolution stage.
Whether prestellar cores (typical size of 0.01-0.03 pc) with several dozen solar masses exist and whether the cores hosted in
the high-mass starless clumps (HMSCs) have a mass significantly larger than the Jeans mass have been investigated by
many studies. Louvet et al. (2019) summarized the only five
high-mass prestellar core candidates that had been detected
up to the publication of their paper, namely CygX-N53-MM2
(Duarte-Cabral et al. 2014), G11.92-0.61-MM2 (Cyganowski
et al. 2014), G11.11-P6-SMA1 (Wang et al. 2014), G028CA9
(Kong et al. 2017), and W43-MM1-#6 (Nony et al. 2018; Molet et al. 2019). These sources would favour the existence of
high-mass prestellar cores, although a more specific check to
see whether they are driving outflows is needed. Anyhow, the
scarcity of high-mass prestellar cores is still significant, suggesting that the MC is not likely to be the common path leading to the
formation of high-mass stars. Recent observations with ALMA
and Submillimeter Array (SMA) toward 70 µm quiet massive
clumps (> 300 M ⊙ ) show that most of the fragmented cores
(0.02 pc scale) are low- to intermediate-mass objects (Li et al.
2019; Sanhueza et al. 2019; Svoboda et al. 2019). For example,
Sanhueza et al. (2019) identified a total of 294 cores in 12 candidate HMSCs (600 M ⊙ to a few thousand M ⊙ ) and 210 of them
are probably prestellar candidates, whereas only eight cores (two
prestellar candidates + six protostellar candidates) have masses
of > 10 M ⊙ .
Both the MC and CA models of HMSF are expected to be
merged into a consistent and unified picture with the progress of
observations and theories. The evolutionary scenario proposed
by Motte et al. (2018) suggests that the large-scale (∼ 0.1 pc)
gas reservoirs, known as starless massive dense cores (MDCs) or
starless clumps, could replace the high-mass analogs of prestellar cores (about 0.01 to 0.03 pc). The phase of high-mass prestellar core could be skipped because massive reservoirs concentrate
their mass into high-mass cores at the same time the stellar embryos are accreting. Louvet et al. (2019) tested this recent scenario by observing nine 70 µm quiet MDCs (0.1 pc, ∼ 100 M ⊙ )
in NGC 6334 using ALMA, with a resolution of 0.03 pc. They
reveal a lack of high-mass prestellar cores in these MDCs; therefore, this result supports the “skipped” prestellar phase and the
scenario proposed by Motte et al. (2018).
We are interested in the impact of H ii regions on the formation of high-mass stars. In particular, we want to study how


Article number, page 2 of 30



these regions impact and modify future (high-mass) star formation that occurs in their immediate surroundings. Previous studies showed that at least 30% of HMSF in the Galaxy are located at the edges of the H ii regions (Deharveng et al. 2010;
Kendrew et al. 2016; Palmeirim et al. 2017). In our first paper
(hereafter Paper I, Zhang et al. 2020), we investigated the feedback of H ii regions on candidate HMSCs that are quiet from
∼ 1 µm to 70 µm and without any star-formation signposts (Yuan
et al. 2017). Higher resolution interferometric observations show
that many of these candidate HMSCs are not absolutely starless
because low- to intermediate-mass protostellar objects usually
exist there (Feng et al. 2016; Traficante et al. 2017; Contreras
et al. 2018; Sanhueza et al. 2019; Svoboda et al. 2019; Pillai
et al. 2019; Li et al. 2019). Using single-dish data observed by
the _Herschel_ and the Atacama Pathfinder EXperiment (APEX),
Paper I explored how H ii regions modify the candidate HMSCs
properties on clump scale (0.1 to 1 pc). The results presented
in Paper I show that more than 60% of the candidate HMSCs
are associated with H ii regions and 30% to 50% of these associated HMSCs show the impacts from H ii regions. The heating, compression, and turbulence injection by H ii regions make
the impacted candidate HMSCs have a higher dust temperature
( _T_ dust, increment is 3 to 6 K), a higher ratio of bolometric luminosity to envelope mass ( _L_ / _M_, from ≲ 0.5 L ⊙ /M ⊙ increases to
≳ 2 L ⊙ /M ⊙ ), a steeper profile of radial column density _N_ H 2 ∝ _r_ [α]
(power-law index α at ∼−0.12 decreases to ∼−0.27), and a
higher turbulence (from supersonic to hypersonic).
We consider whether these differences, created by H ii regions, could modify the early HMSF in massive clumps. The
findings of Paper I suggest that higher turbulence and steeper
clump radial density profile probably favour the formation of
massive fragments by limiting fragmentation (for the effect of
turbulence, we refer to Mac Low & Klessen 2004; for the effect
of clump density profile, we refer to Girichidis et al. 2011; Palau
et al. 2014). In this paper, we study the properties of fragmentation at a typical scale of ∼ 0.025 pc in the candidate HMSCs
under different environments (impacted or non impacted by an
H ii region) to see whether differences exist or not. We take advantage of the candidate HMSCs studied in Paper I. In order to
limit the distance and mass biases (similar distance and mass for
the pair of impacted and non-impacted candidate HMSCs), we
have compiled a relatively low number of sources for this study,
as explained in Sect. 2.
This paper is presented as follows: Section 2 describes the
sample selection including a short description of the previous
studies for each source. Section 3 presents the ALMA continuum data. We analyze the fragmentation in Sect. 4. In Sect. 5,
we explore the signposts of mass shaping exerted by H ii regions
on candidate HMSCs with the ALMA data. In Sects. 6 and
7, we discuss and summarize the results. This paper mainly
presents the ALMA continuum results. The spectral analyses
will be presented in a forthcoming paper.


**2.** **Sample selection**


_2.1._ _Sample selection_


Through a process of cross-matching with star formation indicators such as infrared point sources from ∼ 1 µm to 70 µm,
Yuan et al. (2017) identified 463 candidate HMSCs in the inner
Galactic plane (| _l_ | < 60 [◦], | _b_ | < 1 [◦] ) with 870 µm images from
the APEX Telescope Large Area Survey of the GALaxy (ATLASGAL, Schuller et al. 2009). In Paper I, we cross-matched

S. Zhang et al.: H ii regions and high-mass starless clump candidates



H ii regions and these candidate HMSCs (90% of them are more
massive than 100 M ⊙ ) according to two main criteria: (1) The
projected separation between the center of H ii region and HMSC
is less than double radii of H ii region. (2) The velocity difference
|∆ v _lsr_ | between the H ii region and HMSC is < 7 km s [−][1], which
is derived from the standard deviation of the velocity difference
between H ii regions and HMSCs (see details in Section 4 of Paper I). More than 60% of the candidate HMSCs are associated
with H ii regions and termed as **AS** **candidate** **HMSCs** or **AS** .
For the candidate HMSCs faraway from H ii regions, they are
simply termed as **NA** **(Non-Associated)** **candidate** **HMSCs** or
**NA** .

We made use of the ALMA data observed in ALMA Cycle
4 by project 2016.1.01346.S [1] (PI: Thushara Pillai, project title:
Galactic census of all massive starless cores within 5 kpc).
This project, covering the entire inner Galactic plane, surveyed
the Galactic massive starless core candidates within 5 kpc.
Their selected candidates are dark from near IR to 70 µm. We
cross-matched candidate HMSCs in Paper I and sources for
which their ALMA data are public. A total of four AS candidate
HMSCs impacted by H ii regions were extracted. To have a basis
for a comparison with the non-impacted candidate HMSCs,
we **tentatively** searched for additional four NA candidate
HMSCs in the same ALMA observing project source pool.
To limit the bias and independent variables, these NA are
required to have the most similar single-dish derived clump
mass ( _M_ clump ), column density ( _N_ H 2 ), size (FWHM), ellipticity
( _e_ ), and distance ( _D_ ) compared to AS counterparts in the same
ALMA project. Other single-dish derived properties, such as
_T_ dust, _L_ / _M_, turbulence (line width), density profile (power-law
index α), and virial ratio are not considered when searching for
the possible counterparts. The reason is that the modifications
of these physical properties made by the impacts of nearby
H ii regions have been proven in Paper I. The environment
and single-dish properties of the selected candidate HMSCs
are shown and listed in Figs. 1, 2, and Table 1, respectively.
The clump mass of the sample is approximately equal to the
necessary clump mass to form at least one high-mass star with a
mass of 8 M ⊙, which is 260 M ⊙ to 320 M ⊙, derived by Sanhueza
et al. (2017, 2019), using the initial mass function of Kroupa
(2001) and a star formation efficiency of 30% (Alves et al. 2007).


_2.2._ _Single-dish derived properties and environment_


Compared to the selected NA, the selected AS are warmer, more
luminous, steeper in density profile, more turbulent, and probably less gravitationally bounded as indicated by Table 1. These
differences are in line with the interpretations in Paper I, which
assert the compression and energy injection by H ii regions play
a role in modifying the clump-scale properties.
Pair 1: AS1 is located at the edge of IR dust bubble N1 (Deharveng et al. 2010). N1 bubble is very close to the populous star
cluster W 31-CL hosted in the W 31 giant H ii region (see Fig. 1).
The age of W 31-CL is about 0.5 ± 0.5 Myr derived with near-IR
data by Bianchin et al. (2019). With MAGPIS 20 cm continuum
(Helfand et al. 2006) and H ii region expansion model of Tremblin et al. (2014), the estimated age of N1 is about 0.4 ± 0.2 Myr
with a pressure of about (7 ± 2) × 10 [−][10] dyne cm [−][2] . NA1 has
a similar single-dish mass and beam-averaged _N_ H 2 to AS1. The
FWHM of AS1 (20 [′′] ) is close to the resolution of ATLASGAL


1 `[http://almascience.eso.org//aq/?project_code=2016.1.](http://almascience.eso.org//aq/?project_code=2016.1.01346.S)`
```
01346.S

```


(19.2 [′′] ). The smallest size, the highest surface density Σ, and
small α clearly reflect the more compact nature of AS1 compared to others.
Pair 2: AS2 is hosted in a filamentary cloud at the edge of
an open H ii region mainly created by an O8.5 star (Tackenberg
et al. 2013). The question of whether triggered star formation
is happening in this clump has been explored by the single-dish
studies of Tackenberg et al. (2013). Their research reveals the
possible existence of gas shocked by the H ii region. These authors did not find the features of compression in the density profile with a resolution of 37 [′′] . The appearance of the “champagne
flows” in the H ii region prevents us from validly applying the
expansion model of Tremblin et al. (2014) on age estimation of
the H ii region. Alternatively, the ionized gas pressure on the
interacting filament is estimated with the electron density _n_ e derived from 20 cm continuum integrated flux (Martín-Hernández
et al. 2005). The pressure is ≲ (4.5 ± 0.5) × 10 [−][10] dyne cm [−][2] .
A 24 µm bright source is in the neighborhood of NA2 (see
Fig. 1). This IR bright source is probably an H ii region considering the tight relation between 24 µm hot dust emission and centimeter free-free continuum (Ingallinera et al. 2014; Makai et al.
2017). No significant emission of MAGPIS 6 and 20 cm continuum is detected toward this 24 µm bright source. Furthermore,

−
the associated exciting OB star BD 15 4928 has a Gaia parallax
distance of 1.6 kpc (0.6148 mas, Gaia Collaboration et al. 2018).
Therefore, we propose that the 24 µm bright source is just a projected contamination.
Pair 3: AS3 is associated with H ii region G022.495-00.261
(Anderson et al. 2014) and only very weak (1 to 3 rms) radio continuum is detected towards this region. Dust temperature _T_ dust of
AS3 is similar to its NA counterpart. As a result, AS3 is probably only weakly affected by the H ii region. We note that AS3 is
probably not a starless clump owing to a 24 µm point source situated at an off-center position (see Fig. A.2 in Appendix). Svoboda et al. (2016) identified it as a protostellar clump whereas
Yuan et al. (2017) and ALMA project of Pillai identified it as a
starless candidate. With ALMA imaging, we are able to check
the protostellar properties of AS3.
A bright MAGPIS 90 cm continuum source is located near
NA3 with a separation of ∼ 2 pc. The limited size (< 0.3 pc) and
the detection of CH 3 OH maser (Avison et al. 2016) reveal that
the centimeter bright source is an UCH ii region thus it does not
have significant impacts on distant NA3.
Pair 4: AS4 is likely located in a bright rimmed structure
traced by 8 µm PAH [2] emission (see Fig. 2). AS4 is in the giant
molecular cloud - massive star formation complex G333.0-0.5,
which hosts many bubbles and pillars. The SUMSS 35 cm
continuum shows that AS4 is adjacent to two interacting H ii regions located on both western and eastern sides (Bock et al.
1999). NA4 is probably located in the hub of three converging
filaments far away from any H ii regions. NA4 is more massive
than AS4 by a factor of 1.5, whereas their deconvolved surface
density is quite similar.


**3.** **ALMA dust continuum**


_3.1._ _ALMA band 6 data_


We made use of the ALMA band 6 data (225 GHz, equal to
1.33 mm) of 12 m main array and 7 m Atacama Compact Array


2 Polycyclic aromatic hydrocarbon (PAH) commonly exits in the photodissociation region (PDR) (Fleming et al. 2010).


Article number, page 3 of 30

_−_ 0 _[◦]_ 16 _[′]_


17 _[′]_


18 _[′]_


19 _[′]_


20 _[′]_


+0 _[◦]_ 00 _[′]_


_−_ 0 _[◦]_ 01 _[′]_


02 _[′]_


03 _[′]_


04 _[′]_



15 _[′]_ 14 _[′]_ 13 _[′]_ 12 _[′]_ 10 _[◦]_ 11 _[′]_

Galactic Longitude


58 _[′]_ 57 _[′]_ 56 _[′]_ 55 _[′]_ 18 _[◦]_ 54 _[′]_

Galactic Longitude



_A&A proofs:_ manuscript no. hmsc


_−_ 0 _[◦]_ 20 _[′]_


21 _[′]_


22 _[′]_


23 _[′]_



59 _[′]_ 58 _[′]_ 57 _[′]_ 56 _[′]_ 9 _[◦]_ 55 _[′]_

Galactic Longitude


32 _[′]_ 31 _[′]_ 30 _[′]_ 29 _[′]_ 15 _[◦]_ 28 _[′]_

Galactic Longitude





24 _[′]_


_−_ 0 _[◦]_ 23 _[′]_


24 _[′]_


25 _[′]_


26 _[′]_


27 _[′]_



**Fig.** **1.** Environment of candidate HMSCs. Each panel shows ATLASGAL 870 µm contours (blue, levels are

[0.2, 0.3, 0.4, 0.5, 0.7, 0.9, 1.3, 1.8, 2.5, 4] Jy Beam [−][1] ) overlaid on RGB images constructed from _Spitzer_ 24 µm (in red), 8 µm (in green),
and 4.5 µm (in blue) images. The candidate HMSCs are indicated by white crosses. Red contours indicate radio continuum emission, which
are MAGPIS 20 cm for most of the regions except for NA3 and AS4 (MAGPIS 90 cm and SUMSS 35 cm, respectively; see Fig. 2.). The
root mean square (rms) of the radio images are indicated in the bottom center of each panel. The radio contour levels are the radio image
rms × [3, 4, 6, 8, 10, 15, 20, 30, 40, 60, 80]. The beams of radio and ATLASGAL images are shown in bottom left by red and blue ellipses,
respectively. The used survey data include the: Galactic Legacy Infrared Mid-Plane Survey Extraordinaire (GLIMPSE, Churchwell et al. 2009);
Multiband Imaging Photometer Galactic Plane Survey (MIPSGAL, Carey et al. 2009); Multi-Array Galactic Plane Imaging Survey (MAGPIS,
Helfand et al. 2006), and Sydney University Molonglo Sky Survey (SUMSS, Bock et al. 1999).



(ACA) in the ALMA Cycle 4 project 2016.1.01346.S. Table 2
lists the main ALMA observing parameters. The sources were
observed between March 2017 and June 2018 for the 12 m
array, and between May and August 2017 for the 7 m array.
The typical precipitable water vapor (PWV) is similar for all
sources, except for the main array observation of AS3, which
is twice as large. The time on source for each clump is 0.81
minutes for the main array and 3.53 to 6.05 minutes for the ACA.


_3.2._ _ALMA data reduction_


The data reductions were conducted using the same versions of
Common Astronomy Software Applications (CASA, McMullin


Article number, page 4 of 30



et al. 2007) as those used in the QA2 pipeline products [3] . The
band 6 receiver is equipped with lower and upper sidebands centering at around 217.83 GHz and 232.00 GHz, respectively. The
total used continuum bandwidth is around 7.2 GHz.

The 12 m main array and 7 m ACA data are combined by
CASA task CONCAT in order to create the 12 m + 7 m array
combined continuum images (referred to as combined images or
combined continuum, hereafter). The line-contaminated single
polarization (XX) continuum is regridded to a channel width of
9 MHz in the frequency axis to accelerate the data process. The
CASA task TCLEAN is then performed on the line-free channels to finally obtain the cleaned images. The pixel size “cell”
in the cleaned image is set to be 0.3 [′′], which is about one fifth
of the synthesized beam ≃ 1.3 [′′] . A deconvolver using multi-term


3 `[https://almascience.eso.org/processing/](https://almascience.eso.org/processing/science-pipeline)`
```
science-pipeline

```

S. Zhang et al.: H ii regions and high-mass starless clump candidates





















**Fig. 2.** Environment of candidate HMSCs. The same as Fig. 1, but for another four candidate HMSCs.



(multi-scale) multi-frequency synthesis is applied. The Briggs
weighting with a robust of 0.5 is chosen. The threshold for stopping clean process is set to be 0.4 mJy Beam [−][1], about 2 to 3 rms
noise. Self-calibrations are not applied because the strongest
emission is just around a few dozen rms. The rms measured in
the 7 m + 12 m combined cleaned continuum images is around
0.15 mJy Beam [−][1] (for NA2, AS3, and NA3) to 0.55 mJy Beam [−][1]
(AS1), with a median value of 0.16 mJy Beam [−][1] . The imaged
field is down to 20% power point of the primary beam. The spatial resolution for each source is about 0.018 pc (∼ 3800 AU for

∼
NA2) to 0.029 pc ( 6100 AU for NA3) with a median value of
∼ 0.025 pc.

Considering the larger synthesized beam (∼ 5.5 [′′] ) of the
7 m ACA observations, we created 7 m ACA continuum images
(written as 7 m images or 7 m continuum hereafter) to more
clearly show potential larger structures. The 7 m images are processed in a way similar to the combined images. The pixel size
and threshold for stopping clean process in task TCLEAN are
set to be 1 [′′] and 4 mJy Beam [−][1], respectively. Other TCLEAN
parameters are similar to those for combined images. The rms
noise in the final cleaned 7 m images is around 1.5 mJy Beam [−][1] .

The information about ALMA observations is listed in
Table 2. At 225 GHz, 12 m array and 7 m ACA have a primary
beam of 25.2 [′′] and 44.6 [′′], sensitive to the structure smaller than



11 [′′] and 19 [′′], respectively. Interferometric observations lose the
emission from larger-scale structures. Assuming a dust emissivity spectral index β ≃ 1.5, we estimate the missed 1.3 mm flux
in 7 m + 12 m array observations by comparing with single-dish
ATLASGAL 870 µm flux in the ALMA imaged field. Our 7 m
+ 12 m combined ALMA data set recovers 10–20% of the
single-dish integrated flux (minimum is 10% for NA2, NA3, and
AS4, maximum is 19% for NA4). This value range is similar
to other ALMA observations toward HMSC candidates such as
Contreras et al. (2018); Beuther et al. (2018b); Sanhueza et al.
(2019), which resulted in a value from 10% to 30%. Most of
the large-scale emission detected in single-dish telescope is lost
by interferometer, which implies that most of the masses in the
earliest high-mass clump are more likely to be in large-scale
diffuse envelope rather than in compact cores.


_3.3._ _Core extraction and physical properties_


We extracted the cores in the cleaned 7 m + 12 m combined
continuum images with the technique of Astrodendrograms [4]
(Rosolowsky et al. 2008). Astrodendrogram algorithm uses a



4 `[https://dendrograms.readthedocs.io/en/stable/](https://dendrograms.readthedocs.io/en/stable/)`


Article number, page 5 of 30

_A&A proofs:_ manuscript no. hmsc


**Table 1.** Single-dish derived properties of HMSC candidates.


Source FWHM _[(a)]_ _r_ _[(a)]_ Distance _[(b)]_ _M_ clump _[(c)]_ _N_ H 2 _(c,d)_ Σ _[(e)]_ _T_ dust _[(c)]_ _L_ / _M_ α _[(f)]_ δv _[(g)]_ virial ratio

′′ pc kpc M ⊙ 10 [22] cm [−][2] g cm [−][2] K L ⊙ /M ⊙ km s [−][1]

AGAL010.214-00.306 (AS1) 20 0.13 3.1±0.2 310±90 6.6±1.6 1.29 16.6 2.1±0.8 −0.21±0.18 3.6±0.2 [S][−][C] [18] [O] 0.8 ±0.3

AGAL009.951-00.366 (NA1) 31 0.36 3.1±0.2 330±90 5.9±1.5 0.16 12.0 0.3±0.1 −0.11±0.06 1.6±0.4 [S][−][C] [18] [O] 0.4±0.3

AGAL018.931-00.029 (AS2) 42 0.60 3.3±0.2 330±90 3.2±0.8 0.06 18.2 4.2±1.9 −0.14±0.08 3.6±0.4 [F][−][C] [18] [O] 3.6±1.7

AGAL015.503-00.419 (NA2) 38 0.51 3.1±0.4 320±110 3.7±0.9 0.08 14.0 0.8±0.3 −0.12±0.08 2.8±0.8 [F][−][C] [18] [O] 1.8±1.6

AGAL022.531-00.192 (AS3) 31 0.60 5.0±0.6 900±300 5.2±1.3 0.17 12.4 0.4±0.1 −0.15±0.19 5.2±1.3 [F][−][C] [18] [O] 2.5±2.0

AGAL018.801-00.297 (NA3) 34 0.66 4.9±0.3 1160±330 7.0±1.8 0.18 12.3 0.3±0.1 −0.12±0.06 2.7±1.1 [F][−][C] [18] [O] 0.6±0.5

AGAL333.016-00.751 (AS4) 33 0.44 3.4±0.4 240±80 3.8±0.9 0.08 15.6 1.3±0.5 −0.25±0.25 3.8±0.7 [H] [13] [CO] [+] 4.0±3.0

AGAL029.556+00.186 (NA4) 31 0.53 4.5±0.3 360±100 3.3±0.8 0.08 12.8 0.4±0.1 −0.14±0.08 2.8±0.2 [F][−] [13] [CO] 1.8±0.7


_(a)_ FWHM is measured with ATLASGAL 870 µm continuum by Csengeri et al. (2014). _r_ is derived from FWHM and distance but deconvolved with the beam of
ATLASGAL image (19.2 [′′] ). See details in Yuan et al. (2017) and Paper I.
_(b)_ Distance is taken from Paper I.
_(c)_ Clump mass _M_ clump, H 2 column density _N_ H 2, and dust temperature _T_ dust are derived by fitting SED pixel-by-pixel to _Herschel_ 160, 250, 350, 500 µm, and
ATLASGAL 870 µm by Yuan et al. (2017) but updated with the new distance by Paper I.
_(d)_ _N_ H 2 is the beam-averaged H 2 column density taken from SED fitting resulted maps with a beam of 36.4 ′′ .
_(e)_ Surface density Σ is derived by the clump mass divided by π × _r_ 2 . The _r_ is the deconvolved radius in the third column.
_(f)_ α is the power-law index of H 2 column density radial profile _N_ H 2 ( _r_ ) ∝ _r_ α, see details in Paper I.
_(g)_ The FWHM line widths for the same pair of sources are taken from the same survey as possible as much. The abbreviation “S − C 18 O” means SEDIGISM C 18 O
_J_ = 2 − 1 transition (Structure, Excitation, and Dynamics of the Inner Galactic InterStellar Medium survey, Schuller et al. 2017). “F − [13] CO” and “F − C [18] O”
represent FUGIN [13] CO _J_ = 1 − 0 and C [18] O _J_ = 1 − 0 transitions, respectively (FOREST Unbiased Galactic plane Imaging survey with the Nobeyama 45 m
telescope, Umemoto et al. 2017). “H [13] CO [+] ” is MALT90 H [13] CO [+] _J_ = 1 − 0 transition (Millimetre Astronomy Legacy Team 90 GHz, Jackson et al. 2013).


**Table 2.** Information about the ALMA observations in this work.


Source rms _[(a, c)]_ mass rms _[(a, d)]_ Beam _[(a)]_ Resolution _[(a)]_ Config. Baseline _[(b)]_ Antennas _[(b)]_ Time _[(b, e)]_ Observation period _[(b)]_ PWV _[(b)]_ Main array calibrators _[(f)]_

mJy Beam [−][1] M ⊙ Beam [−][1] ′′ × ′′ pc × pc m minute MM/YYYY mm Flux & Phase


C: 0.55 C: 0.15 C: 1.80×0.99 C: 0.027×0.015 M: 15–314 M: 46 M: 0.81 M: 05/2018 M: 1.0
AS1 C43-2 Titan & J1832-2039
A: 2.0 A: 0.55 A: 6.76×3.90 A: 0.102×0.059 A: 9–49 A: 8–11 A: 6.05 A: 07&05/2017 A: 0.9


C: 0.20 C: 0.09 C: 1.98×0.98 C: 0.030×0.015 M: 15–314 M: 46 M: 0.81 M: 05/2018 M: 1.0
NA1 C43-2 Titan & J1832-2039
A: 1.0 A: 0.45 A: 6.98×3.96 A: 0.106×0.060 A: 9–49 A: 8–11 A: 6.05 A: 07&05/2017 A: 0.9


C: 0.16 C: 0.04 C: 1.46×1.02 C: 0.023×0.016 M: 15–314 M: 47 M: 0.81 M: 05/2018 M: 1.1
AS2 C43-2 Titan & J1832-1035
A: 1.7 A: 0.43 A: 6.39×4.73 A: 0.102×0.076 A: 9–48 A: 8–10 A: 5.04 A: 08/2017 A: 0.9


C: 0.15 C: 0.05 C: 1.44×1.02 C: 0.022×0.015 M: 15–314 M: 47 M: 0.81 M: 05/2018 M: 1.1
NA2 C43-2 Titan & J1832-1035
A: 1.2 A: 0.40 A: 6.35×4.70 A: 0.097×0.072 A: 9–48 A: 8–10 A: 5.04 A: 08/2017 A: 0.9


C: 0.15 C: 0.16 C: 1.29×1.04 C: 0.031×0.025 M: 15–314 M: 46 M: 0.81 M: 06/2018 M: 1.1
AS3 C43-2 Titan & J1832-1035
A: 1.5 A: 1.6 A: 7.48×4.07 A: 0.183×0.099 A: 9–49 A: 9–12 A: 4.03 A: 07/2017 A: 0.8


C: 0.15 C: 0.15 C: 1.48×1.04 C: 0.035×0.025 M: 15–314 M: 47 M: 0.81 M: 05/2018 M: 1.1
NA3 C43-2 Titan & J1832-1035
A: 1.2 A: 1.2 A: 6.36×4.75 A: 0.151×0.113 A: 9–48 A: 8–10 A: 5.04 A: 08/2017 A: 0.9


C: 0.20 C: 0.07 C: 1.63×1.31 C: 0.027×0.022 M: 15–287 M: 45 M: 1.01 M: 03/2017 M: 2.7
AS4 C40-2 Titan & J1603-4904
A: 1.0 A: 0.35 A: 6.19×4.55 A: 0.102×0.075 A: 8–44 A: 10–12 A: 3.53 A: 05/2017 A: 1.8


C: 0.16 C: 0.13 C: 1.36×1.06 C: 0.030×0.023 M: 15–314 M: 46 M: 0.81 M: 06/2018 M: 1.1
NA4 C43-2 Titan & J1832-1035
A: 1.2 A: 0.98 A: 7.18×4.26 A: 0.157×0.093 A: 9–49 A: 9–12 A: 4.03 A: 07/2017 A: 0.8

_(a)_ “C” and “A” in the second to fifth columns represent the information derived from cleaned continuum images of 12 m + 7 m combined data and 7 m data, respectively.
_(b)_ “M” and “A” in the seventh to eleventh columns represent the observational information of 12 m main array and 7 m ACA, respectively.
_(c)_ The rms noise in the cleaned continuum images, see Sect. 3.2.
_(d)_ The rms mass sensitivity is estimated with the rms noise in cleaned continuum images, using Equation 1.
_(e)_ Time on source. It is estimated by the CASA Analysis Utilities task “TimeOnSource”, see details in `[https://casaguides.nrao.edu/index.php?title=TimeOnSource](https://casaguides.nrao.edu/index.php?title=TimeOnSource)` .
_(f)_ The 7 m ACA calibrators are different for different observations. **Flux calibrators:** Titan, Neptune, and J1733-1304 for AS1 and NA1; Neptune and J1733-1304 for AS2, NA2, AS3,
NA3, and NA4; Titan, Callisto, and Ganymede for AS4. **Phase** **calibrators:** J1833-210B and J1832-2039 for AS1 and NA1; J1833-210B and J1733-1304 for AS2, NA2, and NA3;
J1851+0035 for AS3 and NA4; J1650-5044 for AS4.



tree diagram to describe the hierarchical structures over a range
of scales. The cores we extracted correspond to the “leaves” in
the dendrogram, which means that there are no substructures for
these leaves. We set the minimum emission to be considered in
the dendrogam as 3 rms and the steps to differentiate the leaves
as 1 rms. The minimum size considered as an independent leaf is
set to be half of the synthesized beam. Table A.1 lists the primary
beam corrected properties of the cores identified with Astrodendrogram.


Article number, page 6 of 30



Assuming that the dust continuum emission is optically thin,
core mass is estimated with (Hildebrand 1983):

_F_ ν _D_ [2]
_M_ core = _R_ gd (1)

κ ν _B_ ν ( _T_ dust ) [,]


where _F_ ν, κ ν, and _B_ ν ( _T_ dust ) are the measured integrated flux corrected by primary beam, dust opacity per gram, and the Planck
function at the frequency ν. The gas-to-dust mass ratio _R_ gd is assumed to be 100 in this work. The κ ν is set to be 0.9 cm [2] g [−][1], corresponding to the opacity of the dust grains with thin ice mantles
at a gas density of ∼ 10 [6] cm [−][3] (Ossenkopf & Henning 1994).

S. Zhang et al.: H ii regions and high-mass starless clump candidates



The uncertainties of _F_ ν are derived by multiplying image rms
noise with the area of the core. Distance uncertainties are taken
from Table 1, which stem from the uncertainties in the distance
estimator developed by Reid et al. (2016). The combined uncertainties of _R_ gd /κ ν are around 30% according to the estimations
of Sanhueza et al. (2019).
The uncertainties of _T_ dust should be carefully treated. A unified _T_ dust for all cores embedded in one HMSC, which normally
comes from single-dish clump-scale observations, is not solid
due to _T_ dust gradients of the clump and different evolutionary
stages of the cores. Dust temperature is expected to decline towards the center of starless clump (Guzmán et al. 2015; Svoboda et al. 2020; Zhang et al. 2020). The temperature could drop
to ≲ 10 K for the starless center (Lin et al. 2020). Besides,
protostellar cores or clumps are warmer than starless counterparts. The high-mass clumps which have mid-IR emission but
for which the embedded H ii region has not developed yet, have
an average _T_ dust of 18.6 ± 0.2 K, about 2 K higher than that of
the high-mass clumps quiet in mid-IR (Guzmán et al. 2015). In
the absence of _T_ dust measurement at high resolution (∼ 1 [′′] ), we
simply set three _T_ dust values, which are single-dish derived _T_ dust
and _T_ dust ±3 K. A difference of 3 K is estimated from Guzmán
et al. (2015) and the _T_ dust difference between candidate HMSCs
close to and faraway from H ii regions in Paper I. The core mass
for lower and higher _T_ dust is estimated ( _M_ core [cold] [and] _[M]_ core [warm] [).] [The]
differences between _M_ core and _M_ core [cold] [or] _[ M]_ core [warm] [could reach a level]
of about 30–50%.
With spherical assumption, we calculate the core mass surface density Σ core by _M_ core /π _r_ [2] . Further assuming a molecular
weight per hydrogen molecule of µ H 2 = 2.8 (Kauffmann et al.
2008), the H 2 number density ( _n_ H 2 ) and column density ( _N_ H 2 )
are also estimated. All resulted physical parameters are listed in
Table A.2 in Appendix. The identified cores and their mass are
shown in the middle panels of Figs. 3 and 4.


**4.** **Fragmentation at** ∼ **0** . **025** **pc scale**


_4.1._ _Calculation_


Fragmentation is a multi-scale process existing in the interstellar medium from ∼ 10 kpc-scale spiral arm of the galaxy to
∼ 100 AU-scale protostellar system (Efremov & Elmegreen
1998). Taking advantage of the ALMA spatial resolution of
∼ 0.025 pc, in this work, we explore how the pc scale candidate
HMSCs fragment into ∼ 0.025 pc-scale dense cores.
In the simplest case, fragmentation is dominated by thermal
support in a non-magnetic, isothermal, homogeneous, and selfgravitating clump. Without turbulence, HMSCs are expected to
fragment into cores with a mass around thermal Jeans mass ( _M_ J [th] [)]
and a core separation around thermal Jeans length (λ [th] J [)] [(][Jeans]
1902; Mac Low & Klessen 2004):



The mean molecular weight per free particle µ is set to be 2.37
because σ th is governed by H 2 and He (see Appendix B). The
sound speed _c_ s = σ th in this case.
In the case that takes into account both thermal and nonthermal motions, σ th is replaced by the total velocity dispersion
σ tot which is derived from the non-thermal velocity dispersion
of the observed lines σ nth,line and the sound speed _c_ s by


σ tot = (σ [2] nth,line [+] _[ c]_ s [2] [)] [1][/][2] [,] (5)

2019where). σHere, nth,line σ=is (derivedσ [2] − σ [2] th from,line [)] 1/ the 2 (Palauobservedet al.line2015width; Li δetv al.in

dispersionTable 1 by σof =theδvobserved/(8ln2) [1][/] line [2] . Theσ th σ,lineth,line = is the thermal velocity� µ mole _k_ B _Tm_ H � 1/2 . For µ mole,
the weight for different molecules, is 29 for [13] CO and 30 for
C [18] O and H [13] CO [+] .

The corresponding Jeans parameters are (Palau et al. 2015):



σ tot [3]

_M_ J [tot] = [π] [5] 6 [/][2] ~~�~~ _G_ [3] ρ, λ [tot] J [=][ σ] [tot]



π
� _G_ ρ



1/2
. (6)
�



More specifically, considering the cases that the compression
of large scale supersonic flow creates density enhancement by
a factor of Mach number square, M [2], the corresponding Jeans
parameters are (Mac Low & Klessen 2004; Palau et al. 2015):



_M_ [com][,][flow] = [π] [5][/][2]
J 6



σ [3]
nth,line, λ [com] J [,][flow] = σ nth,line
� _G_ [3] ρ eff



π
� _G_ ρ eff



1/2
, (7)
�







3
= [π] [5][/][2]




[5][/][2] σ th [3]

, (2)
6 ~~�~~ _G_ [3] ρ



where ρ eff is the effective density ρ eff = ρM [2] and M is equal to
v flow / _c_ s = √3σ nth,line / _c_ s .

The comparison between _M_ core and Jeans mass is probably
more straightforward than that between core separations _S_ core
and Jeans length. The actual separations are longer than or equal
to those separations derived from the images owing to the projection effect, which is the main uncertainty when using separations to analyze the fragmentation. On average, the projected
separations are shorter than the actual separations by a factor of
2/π (see math derivations in Appendix B). A unified clump-scale
_T_ dust derived from the SED fitting for each core embedded in the
clump is a loose approximation for _M_ core . Some cores have already presented molecular emission, such as the outflow tracer
SiO _J_ = 5 − 4 (see Sect. 4.5), indicating star-forming activities.
As a result, these cores are actually warmer and the core mass
derived at the clump-scale _T_ dust is an upper limit. The warm core
mass _M_ core [warm] [is probably more appropriate for these cores. Both]
core mass and separation estimations have pros and cons and
therefore we analyze the fragmentation by combining both _M_ J [th]
and λ [th] J [to attain a more consistent conclusion.]
We derived the nearest neighbouring separations for all
cores in each clump using the minimum spanning tree (MST)
method. It works by connecting a set of points with a set
of straight lines and ending up with a minimum sum of line
lengths. The MST is frequently used in the research of the
spatial distribution of star-forming objects, such as YSOs
(Panwar et al. 2019; Pandey et al. 2020a,b) and dense cores (Dib
& Henning 2019; Sanhueza et al. 2019). In particular, Clarke
et al. (2019) have demonstrated that MST is able to robustly
detect the characteristic fragmentation scales. We plot the core
MST for each clump in the middle panels of Figs. 3 and 4.


Article number, page 7 of 30



_M_ J [th] [=] [4][π] 3 [ρ]



λ [th]
J
 2



1/2
, (3)
�



λ [th] J [=][ σ] [th]



π
� _G_ ρ



where ρ is the mass density and σ th is the thermal velocity dispersion:



1/2

_k_ B _T_
σ th = . (4)
� µ _m_ H �

_A&A proofs:_ manuscript no. hmsc
























|−0◦18′06′′<br>12′′<br>GalacticLatitude<br>18′′<br>24′′<br>30′′<br>36′′<br>01<br>.<br>06′′ 13′00′′ 54′′ 48′′ 42′′ 10◦1<br>−0◦21′42′′<br>48′′<br>GalacticLatitude<br>54′′<br>22′00′′<br>06′′<br>−<br>12′′<br>01<br>.<br>18′′ 12′′ 06′′ 57′00′′ 54′′ 9◦56<br>−0◦01′30′′<br>36′′<br>GalacticLatitude<br>42′′<br>48′′<br>54′′<br>02′00′′ −<br>01<br>.<br>06′′ 56′00′′ 54′′ 48′′ 42′′ 18◦5<br>−0◦24′54′′<br>25′00′′<br>GalacticLatitude<br>06′′<br>12′′<br>18′′<br>24′′<br>01<br>.<br>24′′ 18′′ 12′′ 06′′ 30′00′′ 15◦2<br>GalacticLongitude|Col2|
|---|---|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|pc<br>0.1 pc<br>0<br>2<br>4<br>6<br>8<br>Flux (mJy Beam_−_1)|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|2_′_36_′′_<br>10_◦_12_′_36_′′_<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>50_′′_<br>13_′_00_′′_<br>10_′′_|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|pc<br>0.1 pc<br>0_._5<br>0_._0<br>0_._5<br>1_._0<br>Flux (mJy Beam_−_1)|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|_′_48_′′_<br>9_◦_56_′_48_′′_<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>57_′_00<br>10_′′_<br>20_′′_|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|pc<br>0.1 pc<br>0_._5<br>0_._0<br>0_._5<br>1_._0<br>Flux (mJy Beam_−_1)|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|5_′_36_′′_<br>18_◦_55_′_36_′′_<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>50_′′_<br>56_′_00_′′_<br>10_′′_|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|pc<br>0.1 pc<br>0<br>1<br>2<br>3<br>4<br>Flux (mJy Beam_−_1)|
|10_◦_1<br>42_′′_<br>48_′′_<br>54_′′_<br>13_′_00_′′_<br>06_′′_<br>36_′′_<br>30_′′_<br>24_′′_<br>18_′′_<br>12_′′_<br>_−_0_◦_18_′_06_′′_<br>Galactic Latitude<br>0.1 <br>9_◦_56<br>54_′′_<br>57_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>22_′_00_′′_<br>54_′′_<br>48_′′_<br>_−_0_◦_21_′_42_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>18_◦_5<br>42_′′_<br>48_′′_<br>54_′′_<br>56_′_00_′′_<br>06_′′_<br>02_′_00_′′_<br>54_′′_<br>48_′′_<br>42_′′_<br>36_′′_<br>_−_0_◦_01_′_30_′′_<br>Galactic Latitude<br>0.1 <br>_−_<br>15_◦_2<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>24_′′_<br>18_′′_<br>12_′′_<br>06_′′_<br>25_′_00_′′_<br>_−_0_◦_24_′_54_′′_<br>Galactic Latitude<br>0.1|9_′_54_′′_<br>15_◦_29_′_54_′′_<br>30_′_00_′′_<br>06_′′_<br>12_′′_<br>18_′′_<br>24_′′_<br>Galactic Longitude<br>10_′′_<br>20_′′_<br>Galactic Long|



**Fig.** **3.** 7 m + 12 m combined 1.3 mm continuum. The presented images are uncorrected for the primary beam for displaying a homogeneous
noise background. Four rows of panels show AS1, NA1, AS2, and NA2, respectively. ALMA emission (grayscale) is overlaid with the colorfilled contours starting from 3 rms to 21 rms with a step of 1 rms. Each row has three panels. _Left panel:_ The extracted cores (blue ellipses) and
their Astrodendrogram “leaves” (red contours). Green dashed contours show the negative emission starting from −3 rms with a step of −1 rms.
ATLASGAL emission contours (black) are the same as Fig. 1. The synthesized beam (black ellipse) is shown in the bottom left. _Central panel:_
Core mass is shown by the orange circle whose area is in proportion to mass. The numbers close to cores are core indexes ranking from the highest
to the lowest mass. The highest and the lowest masses are indicated in the bottom left. MST short and long separations are shown in red and green
lines, respectively, see more in Fig. 5. Blue lines indicate λ [th] J,clump [. Magenta arrows show the impacted direction.] _[ Right panel:]_ [ ALMA 1.3 mm color]
contours overlaid on GLIMPSE 8 µm background. See Sect. 5.1 for the meanings of yellow stars, crosses, triangles, and associated circles.


Article number, page 8 of 30

S. Zhang et al.: H ii regions and high-mass starless clump candidates























































**Fig. 4.** 7 m + 12 m combined 1.3 mm continuum. The meanings of lines and marks are similar to those in Fig. 3 but for AS3, NA3, AS4, and NA4.



_4.2._ _General trend shown by combined images_


We show the core MST separations and mass scaled by clump
thermal Jeans parameters in Fig. 5. Most of the scaled core mass
( _M_ core / _M_ J [th],clump [,] [the] [ratio] [of] [core] [mass] [to] [clump] [thermal] [Jeans]
mass) are less than one except for the most massive cores and



AS1, suggesting the dominant role of the thermal motions in the
fragmentation. Similar trend is also implied by the scaled core
MST separations ( _S_ core /λ [th] J,clump [,] [the] [ratio] [of] [core] [separation] [to]
clump thermal Jeans length), which are less than one for most
sources except for AS1.


Article number, page 9 of 30

_A&A proofs:_ manuscript no. hmsc



The distribution of _S_ core /λ [th] J,clump [presents] [a] [bimodal] [profile]
with _S_ core /λ [th] J,clump [peaked] [at] [∼] [0][.][3] [and] [∼] [0][.][8] [in] [our] [limited]
sample. Svoboda et al. (2019) found a similar bimodal distribution peaking at around 0.3 and 1 when surveying twelve
candidate HMSCs (400 M ⊙ to 3600 M ⊙ with a median mass of
800 M ⊙ ) by ALMA Band 6 observations. The physical scale
they studied (0.015 pc in 0.5 pc-scale clump) is similar to our
cases. Their bimodal profiles that are corrected and uncorrected
for projection effects are shown in Fig. 5. By checking with
7 m + 12 m combined images in Figs. 3 and 4, the reason for
the bimodal profile could be the hierarchical fragmentation at
two scales ≳ 0.1 pc and ≲ 0.05 pc. The most significant case
is AS2, which shows four groups of cores with a separation
of 0.1-0.2 pc and each group contains two to three cores with
separations of ≲ 0.05 pc, corresponding to the double peaks in
the bimodal profile.


_4.3._ _Hierarchical fragmentation shown by 7 m data_


To confirm the hierarchical nature of fragmentation, the
7 m + 12 m combined continuum overlaid with 7 m ACA continuum contours are presented in Fig. 6. It is obvious that a number
of very close cores are hosted in the same 7 m iso-contours, indicating the sub-fragmentation from structures outlined by isocontours to cores. Here we term these 7 m ACA emission structures as “ensembles”. We first identify “leaves” within Astrodendro in 7 m images uncorrected for the primary beam. The criteria
of Astrodendro are looser than those used in the combined images (minimum emission = 2.5 rms, step = 1 rms, and minimum
size = half of the 7 m ACA synthesized beam). The information
of all identified 7 m image “leaves” could be found in Figs. A.3,
A.4, and Table A.3 in Appendix. These 7 m image “leaves” are
possible candidate ensembles, however, we classify the “ensembles” in a more rigorous way here:
First, if the identified 7 m “leaves” have a major-to-minor
ratio less than 2.5, they are directly selected as ensembles. The
ensemble mass and density are calculated in a manner that is
similar to that in Equation 1.
Next, for the identified 7 m “leaves”, which present a prolonged shape (the major-to-minor ratio > 2.5), they are probably
made of more than two individual candidate ensembles if the ensemble peaks are too similar to be differentiated by Astrodendro.
We carefully check the 7 m ACA continuum contours to search
for the peak and subpeak for these prolonged “leaves” and then
simply assume that these peaks and subpeaks are the positions of
the candidate ensembles. Taking into account the roughly equal
peaks, we directly use the density of the “leaves” as the estimated
density of each ensemble.
Lastly, we note that some 7 m ACA emission structures are
not identified in Astrodendero due to their low signal-to-noise
ratio (S/N), whereas they host one or few low-mass cores
detected in the 7 m + 12 m combined images, such as the
candidate ensemble W1 in NA2. We mark these weak structures
by eye and assume that they are also candidate ensembles. The
mass and density are not calculated due to their low S/N.


All the identified ensembles, their density, and thermal Jeans
parameters are listed in Table 3. With regard to the calculation
and NA3 are special because a number of their cores are nearlyof the ensemble thermal Jeans length, λ [th] J,ens [, we can see that AS3]
equally spaced in a prolonged leaf, invoking the cylindrical fragmentation. For an isothermal gas “cylinder”, it could fragment


Article number, page 10 of 30



into equally spaced cores under gravitational instability. The typical separation and mass in the case of cylindrical thermal fragmentation is:

λ [th] J,cylinder [=][ 22][σ] [th] [ (4][π] _[G]_ [ρ] _[c]_ [)] [−][1][/][2] [,] _[ M]_ J [th],cylinder [=] π [22] [1][/][2] �σ _G_ th [3][3] ρ c, (8)


where ρ _c_ is the density at the center of the “cylinder” in virial
equilibrium (Chandrasekhar & Fermi 1953; Jackson et al. 2010;
Wang et al. 2014). We corrected the λ [th] J,ens [of AS3 main leaf ac-]
cording to Equation 8. The ρ _c_ is assumed to be the minimum
density of the cores embedded in the filament, which is about
one magnitude larger than the filament average density, a result
that is similar to other methods of estimations in studies of filament fragmentation, such as in Jackson et al. (2010); Wang et al.
(2014); Lu et al. (2018).
Ensemble identification is not clear for NA3. The identified
7 m leaf has a major-to-minor axis ratio of - 2.5 but the presented three subpeaks _E2-S1?_, _E2-S2?_, and _E2-S3?_ cannot cover
all cores (see Fig. 6). NA3 is the most distant source in our sample (4.9 kpc compared to 3.1–3.4 kpc of other sources) except for
AS3. In addition, the major axis of 7 m image synthesized beam
roughly aligns with the filament. This evidence may shed light
on the possibility that its longer core separations correspond to
separations between ensembles rather than to core separations
in the same ensembles. To cover all possibilities, we considered two cases for NA3: (1). The identified 7 m image “leaf”
is merged by few ensembles and, thus, it represents the fragmentation from clump to ensemble. (2). The “leaf” is just one
filamentary ensemble and, therefore, it represents the fragmentation from ensemble (filament) to core. In the second case, we
apply the calculation ofFigure 7 (a) shows λthe [th] J,ens core [that is corrected with Equation] separations scaled by ensem- [ 8][.]
ble thermal Jeans length ( _S_ core /λ [th] J,ens [)] [for] [the] [cores] [in] [the] [same]
ensembles. The median _S_ core /λ [th] J,ens [is] [around] [1] [to] [1.5.] [The]
_S_ core /λ [th] J,ens [for AS3 and NA3 is significantly reduced from][ >][ 2 to]
< 2 in the case of cylindrical fragmentation. A maximum factor
of 1.5λ [th] J [means] [that] [there] [is] [a] [non-thermal] [velocity] [dispersion,]
σ nth, playing a role equivalent to thermal dispersion, σ th . Even if
the ensemble-scale (< 0.1 pc) line measurement is not presented
in this continuum study, other studies toward embedded structures with similar scale in HMSCs reveal a line dispersion of
≳ 0.5–2 km s [−][1], which is twice larger than σ th at least (Li et al.
2019). Another potential bias is that the mass and density of most
massive 7 m “leaves” are likely overestimated due to the existing
star-formation activities (see Sect. 4.5). A dust temperature improvement of 3 K in ensemble mass calculation could reduce the
derived mass and density by one third, leading to a new thermal
Jeanstions arelengthmoreλ J [th],ens [,] e [warm] ffective> ~~[√]~~ in3/sub-fragmentation2λ [th] J,ens [.] [Therefore,] [the] from [thermal] ensembles [mo-]
to cores although other effects such as turbulence and magnetic
field may play a limited assistant role in the sub-fragmentation

process.
Figure 7 (b) shows ensemble separations scaled by clump
thermal Jeans length ( _S_ ens /λ [th] J,clump [).] [The] [median] [value] [of]
_S_ ens /λ [th] J,clump [is] [around] [1.] [Nearly] [all] _[S]_ [ ens] [/λ] [th] J,clump [are] [less] [than]
1.5 except for AS1 and NA1, confirming the dominance of the
thermal motions in fragmentation from clumps to ensembles
for most candidate HMSCs. The mass of NA1 ensembles is in
low-mass range (1–3 M ⊙ ), similarly to _M_ J [th],clump [.] [The] [turbulent]
fragmentation model is inappropriate for most HMSCs because
both ensemble mass and separations are significantly smaller
than _M_ J [tot],clump [and][ λ] [tot] J,clump [. Taking the compression of supersonic]

S. Zhang et al.: H ii regions and high-mass starless clump candidates


**Table 3.** Jeans parameters for clumps and ensembles.


[l] [l]




[l] _M_ J [tot],clump [l]

_M_ J [th],clump



λ [com] J,clum [,][f][l][ow] p _M_ [th] [l]
λ [th] J,clump J,clump




[l] _MM_ J [com] J [th],clum,clump [,][f][l][ow] p Ens. _[(a)]_ Subfrag. _[(b)]_ Ens. _n_ H 2 _(c)_ _M_ ens _(c)_ λ [th] J,ens _M_ J [th],ens Cores _[(d)]_ 7 m Leaves _[(e)]_




[l] [l]

Source λ [th]
J,clump



λ [tot] J,clump [l] [l]
λ [th] J,clump




[l] [l]


pc M ⊙ 10 [6] cm [−][3] M ⊙ pc M ⊙ ALMA _n_ ACA _n_




[l] [l]


E1 N 3.6




[l] [l]


0.013±0.003 0.3±0.1 2 1




[l] [l]


AS1 0.034±0.007 6.8 0.58 0.8±0.3 311 26


NA1 0.14±0.03 2.7 0.58 2.2±0.8 19 3.5


AS2 0.36±0.07 5.7 0.58 8.6±2.9 181 18


NA2 0.25±0.07 5.7 0.58 4.6±1.8 182 18


AS3 0.18±0.05 10.7 0.58 2.9±1.1 1216 65


NA3 0.18±0.04 6.8 0.58 2.9±1.0 320 26




[l] [l]


E2 N 4.1 ≲ 7 0.012±0.002 0.3±0.1 1 2


W1 N − − − 3 −




[l] [l]


E1 Y 0.50




[l] [l]


0.030±0.006 0.5±0.2 1, 3 1




[l] [l]


E2 N 0.52 0.029±0.006 0.5±0.2 2 2

∼ 2.5

E3 N 0.98 0.021±0.005 0.3±0.1 − 3


E4 N 0.66 0.026±0.006 0.4±0.2 4 4




[l] [l]


E1 Y 0.51




[l] [l]


0.036±0.007 0.9±0.3 1, 3 1




[l] [l]


E2 Y 0.34 0.044±0.010 1.1±0.4 2, 8, 9 2

∼ 3.5




[l] [l]


E3-S1 Y 0.27 0.049±0.012 1.2±0.5 4, 6 3


E3-S2 Y 0.27 0.049±0.012 1.2±0.5 5, 7 3




[l] [l]


E1 Y 0.53




[l] [l]


0.031±0.007 0.6±0.2 1, 3 1




[l] [l]


E2 N 0.65 ≲ 4.9 0.028±0.007 0.5±0.2 − 2


W1 N − − 2 −




[l] [l]


E1-S1 Y 0.41




[l] [l]


0.034±0.007 0.6±0.2 1, 3, 4, 6, 8, 9 1




[l] [l]


E1-S2 N 0.41 0.034±0.007 0.6±0.2 7 1

≲ 13

E2-S1 N 0.25 0.043±0.010 0.7±0.3 2 2


E2-S2 N 0.25 0.043±0.010 0.7±0.2 5 2




[l] [l]


E2-S1? −




[l] [l]


1?




[l] [l]


E2-S2? − 2?

0.65 − 0.043±0.01 0.7±0.2 2




[l] [l]


E2-S3? − 3, 4?


E2-U? − 6, 7?


E1 Y 0.2 0.054±0.012 1.1±0.4 1, 2, 4, 5, 6, 7, 8 1
AS4 0.24±0.07 9.4 0.58 5.0±2.0 819 50 ∼ 5

W1 N − − − 3 −




[l] [l]


E1-S1 Y 0.37




[l] [l]


0.036±0.007 0.6±0.2 2,3,5,7 1




[l] [l]


NA4 0.24±0.05 6.3 0.58 4.0±1.4 251 22




[l] [l]


E1-S2 Y 0.37 ∼ 15 0.036±0.007 0.6±0.2 4, 6 1




[l] [l]


E1-S3 N 0.49 0.031±0.007 0.5±0.2 1 2


_(a)_ Candidate ensembles. The nomenclature: (1) E _n_ . Candidate ensemble shown by 7 m image leaf ACA _n_ in Table A.3 of Appendix. (2) E _n_ -S _m_ . Subpeak _m_ of 7 m image
leaf ACA _n_ in Table A.3. (3) W _n_ . Weak-emission ensemble. See details about three types of ensembles in Sect. 4.3. _E2-S1?_, _E2-S2?_, and _E2-S3?_ are uncertain subpeaks
for NA3, as explained in Sect. 4.3. _E2-U?_ is just a potential candidate because of the existence of two close cores ALMA 6 and 7, but this candidate is highly uncertain.
_(b)_ Whether sub-fragmentation is detected.
_(c)_ Estimated ensemble number density and average mass, see details in Sect. 4.3.
_(d)_ Embedded cores identified in combined images. The “?” following the core index for NA3 means the association between cores and ensembles is uncertain, see Sect. 4.3.
_(e)_ 7 m image “leaves”, listed in Table A.3, correspond to candidate ensembles.




[l] [l]


flow into account, the resulting λ [com] J,clump [,][flow] [,] [which] [is] [even] [smaller]
than λ [th] [gives] [a] [more] [contradictory] [picture] [than] [the] [one]
J,clump [,]
given by the thermal fragmentation.


As a result, the early-stage fragmentation in the high-mass
clumps probably takes place in a hierarchical fashion: clumps
fragment into ensembles with separations around clump thermal
Jeans length, λ [th] J,clump [, and then some of these ensembles contin-]
uously sub-fragment into cores with separations slightly larger
than ensemble Jeans length, λ [th] J,ens [.]


_4.4._ _Considering possible differences between AS and NA_


In this limited statistic, there is no clear overall trend that fragmentation between AS and NA has a significant difference. The
_S_ core /λ [th] J,clump [,] _[ S]_ [ ens] [/λ] J [th],clump [,] _[ S]_ [ core] [/λ] J [th],ens [in Figs.][ 5][ and][ 7][ only show]




[l] [l]


a slight difference between AS and NA. The median values of
_M_ core / _M_ J [th],clump [in Fig.][ 5][ indicate that the cores in NA are proba-]
bly more massive than AS, but we note that AS2 has much more
low-mass cores than NA2. The nine cores of AS2 in the lowmass end could be the reason for which the cores in type AS
have a lower median _M_ core / _M_ J [th],clump [when compared to those in]
NA.

For thermal fragmentation, a higher _T_ dust results in a larger
_M_ J [th] [and][ λ] [th] J [if density][ ρ][ is roughly kept constant. A higher] _[ T]_ [dust]
(3–6 K) and a similar ρ for AS, as compared to NA, have been
revealed with the single-dish results in Paper I. Taking advantage
of 58 candidate HMSCs located in the 3–5 kpc range given in
Paper I, the expected _M_ J [th],clump [and][ λ] [th] J,clump [for strongly impacted]
AS (S-type AS, 31 in total, see Paper I) and non-impacted NA
HMSCs (27 in total) are shown in Fig. 8. The peak of _M_ J [th],clump
distribution shifts from about 2 M ⊙ for NA to 6 M ⊙ for AS. If
most AS and NA HMSCs follow thermal fragmentation, the


Article number, page 11 of 30

_A&A proofs:_ manuscript no. hmsc



|Col1|Col2|Col3|(a). Length Ratio|Col5|
|---|---|---|---|---|
|0<br>2<br>4<br>6<br>8<br>10<br>Number|||corrected<br>uncorrected||
|0<br>2<br>4<br>6<br>8<br>10<br>Number|||||


10


8


6



0 _._ 0 0 _._ 5 1 _._ 0 1 _._ 5 2 _._ 0 2 _._ 5 3 _._ 0 3 _._ 5 4 _._ 0
_S_ core _/λ_ [th] J _,_ clump

(b). Mass Ratio



4


2


0

|Col1|Col2|AS1<br>NA1<br>AS2<br>NA2<br>AS3<br>NA3<br>AS4<br>NA4|
|---|---|---|
||||


10 _[−]_ [2] 10 _[−]_ [1] 10 [0] 10 [1]

_M_ core _/M_ J [th] _,_ clump


**Fig.** **5.** Core separations and mass scaled by clump thermal Jeans parameters. Histograms with different colors represent different candidate
HMSCs. _Panel (a)_ shows the scaled core separations _S_ core /λ [th] J,clump [. The]
hatched histograms indicate short separations that two cores are in the
same ensembles (see Sect. 4.3). Black and red solid lines represent the
distributions derived from Svoboda et al. (2019) by multiplying their
probability density functions (PDFs) with the total number of cores in
our cases. Black and red lines show the projected nearest neighbor separations and the projection-corrected nearest neighbor separations, respectively, see details in Svoboda et al. (2019). Blue and red dash lines
are median values of short separations for NA and AS, respectively.
Similarly, dash-dotted lines indicate median values of long separations.
_Panel (b)_ shows the scaled mass _M_ core / _M_ J [th],clump [. The red and blue lines]
indicate median values for AS and NA, respectively.


fragmented cores in AS are expected to be more massive than
NA on average. The study of eight candidate HMSCs in this
paper is a pilot and tentative exploration due to the very limited
sample. An ALMA survey covering several dozens of AS and
NA candidates observed with the similar spatial resolution is
crucial to resolving the trend suggested in this work.


_4.5._ _Diversity of fragmentation_


In this section, we discuss in greater detail more the fragmentation of the candidate HMSCs, presenting diverse properties
besides the general hierarchical fragmentation found. A scaled
separation _S_ core /λ [th] J,clump [of] [∼] [3] [suggests] [that] [cores] [in] [AS1]
probably result from not only thermal motions. Meanwhile,
massive cores probably exist in some candidate HMSCs. The


Article number, page 12 of 30



most massive cores in AS1, AS3, NA3, and NA4 have a
scaled mass _M_ core / _M_ J [th],clump [of] [20,] [6,] [3,] [and] [3,] [respectively.] [As]
mentioned in Sect. 3.3, the evolutionary stage of cores is an
important source of uncertainty when estimating _M_ core because
a large scaled mass could be due to an underestimated _T_ dust .


**Notable case AS1:** AS1 fragments into three massive cores
with mass from 10-17 M ⊙ and a separation of ≃ 0.1 pc. Both
_M_ J [th],clump [and] [λ] [th] J,clump [show] [that] [its] [fragmentation] [cannot] [be] [ex-]
plained by thermal motions alone. The turbulent Jeans parameters in total support case ( _M_ J [tot],clump [and] [λ] [tot] J,clump [)] [are] [much] [larger]
than the observed parameters, whereas taking compressible flow
into account gives a closer _M_ J [com],clump [,][flow] (∼ 20 M ⊙ ) with a more con
tradict λ [com] J,clump [,][flow] (∼ 1/2λ [th] J,clump [).] [It] [implies] [that] [turbulence] [alone]
is equally insufficient to fully explain AS1 fragmentation. Introducing more physical factors, such as magnetic field support, and
considering a different relative significance for each factor in the
fragmentation process could probably lead to the building of a
more suitable scenario to explain this process (Tang et al. 2019).
A potential bias is that the worse rms mass sensitivity
(0.15 M ⊙ Beam [−][1] ) of AS1 combined image compared to that of
other candidate HMSCs would make us leave out more low-mass
cores. We image AS1 continuum with only 12 m array dataset,
resulting in an image rms of 0.2–0.3 mJy Beam [−][1], which is better than combined image of AS1 (0.55 mJy Beam [−][1] ) and close
to combined images of other candidate HMSCs. Using the same
Astrodendro parameter, the number of identified cores in AS1
12 m image is the same as the one in the combined image. Therefore, we propose that the number of missed cores in AS1 is likely
at a level similar to other candidate HMSCs.
High-velocity components (> 20 km s [−][1] ) of outflow tracer
SiO _J_ = 5 − 4 (Louvet et al. 2016; Matsushita et al. 2019)
are detected within our data set toward cores ALMA1 and
ALMA2, indicating the stars are forming and still accreting
mass there. Meanwhile, thermal methanol lines CH 3 OH 4(2,
2)-3(1, 2)-E at 218.44 GHz (E _u_ = 45.46 K), which probably
trace the shocked gas (Zapata et al. 2012; Johnston et al. 2014),
are also detected toward both two cores. When taking the warm
mass _M_ core [warm] as core mass, the scaled mass _M_ core [warm] [/] _[M]_ J [th],clump [is]
still around 8-13. Combining it with the mass accretion and
very early evolutionary stage of AS1 (70 µm dark), AS1 cores
probably have the potential to form high-mass stars. The highest
clump surface density compared to other candidate HMSCs,
1.3 g cm [−][2], also meets the high-mass star formation density
criterion of 1 g cm [−][2] suggested by Krumholz & McKee (2008).


**Star** **formation** **and** **warm** **gas** **indicators:** A check on
whether massive cores show star formation signposts is beneficial to understand the overestimated mass and whether highmass prestellar cores exist. We will present a complete spectral
study of this ALMA data set in a forthcoming paper. Here we
only describe a few cases of significant spectral detection in our
regridded spectra.
Recent studies show that H 2 CO mainly traces denser and
warmer gas (≳ 30 K, ∼ 10 [5] cm [−][3] ), such as warm gas in OMC-1
(Tang et al. 2018) and cometary globule (bright-rimmed cloud
impacted by H ii regions, Mookerjea et al. 2019). The detection
of H 2 CO is also related to shock chemistry corresponding to outflow (Contreras et al. 2018; Gieser et al. 2019). The most massive ensemble E1 in AS2 (see Fig. 6), containing cores ALMA1
and ALMA3, is just in front of the PDR traced by PAH 8 µm
emission, showing the gas and dust distribution shaped by the

_−_ 0 _[◦]_ 18 _[′]_ 06 _[′′]_


12 _[′′]_


18 _[′′]_


24 _[′′]_


30 _[′′]_


36 _[′′]_


_−_ 0 _[◦]_ 01 _[′]_ 30 _[′′]_


36 _[′′]_


42 _[′′]_


48 _[′′]_


54 _[′′]_


02 _[′]_ 00 _[′′]_


_−_ 0 _[◦]_ 11 _[′]_ 18 _[′′]_


24 _[′′]_


30 _[′′]_


36 _[′′]_


42 _[′′]_


48 _[′′]_


_−_ 0 _[◦]_ 44 _[′]_ 48 _[′′]_


54 _[′′]_


45 _[′]_ 00 _[′′]_


06 _[′′]_


12 _[′′]_


18 _[′′]_



S. Zhang et al.: H ii regions and high-mass starless clump candidates





|0.1 pc|Col2|
|---|---|
|0.1 pc||
|0.1 pc||


18 _[′′]_ 12 _[′′]_ 06 _[′′]_ 57 _[′]_ 00 _[′′]_ 54 _[′′]_ 9 _[◦]_ 56 _[′]_ 48 _[′′]_

Galactic Longitude


Galactic Longitude

|0.1 pc|Col2|
|---|---|
|0.1 pc||


|0.1 pc|Col2|
|---|---|
|0.1 pc||
|0.1 pc||
|0.1 pc||



36 _[′′]_ 30 _[′′]_ 24 _[′′]_ 18 _[′′]_ 12 _[′′]_ 29 _[◦]_ 33 _[′]_ 06 _[′′]_

Galactic Longitude



|0.1 pc|Col2|
|---|---|
|0.1 pc||
|0.1 pc||
|0.1 pc||
|0.1 pc||
|0.1 pc||
|0.1 pc||


06 _[′′]_ 13 _[′]_ 00 _[′′]_ 54 _[′′]_ 48 _[′′]_ 42 _[′′]_ 10 _[◦]_ 12 _[′]_ 36 _[′′]_

Galactic Longitude


Galactic Longitude

|0.1 pc|Col2|
|---|---|
|0.1 pc||
|0.1 pc||
|0.1 pc||



06 _[′′]_ 32 _[′]_ 00 _[′′]_ 54 _[′′]_ 48 _[′′]_ 42 _[′′]_ 22 _[◦]_ 31 _[′]_ 36 _[′′]_

Galactic Longitude



9


8


7


6


5


4


3


2


1


0


_−_ 1


_−_ 2


1


0


4


3


2


1


0


1


0


_−_ 1



_−_ 0 _[◦]_ 24 _[′]_ 54 _[′′]_


25 _[′]_ 00 _[′′]_


06 _[′′]_


12 _[′′]_


18 _[′′]_


24 _[′′]_


_−_ 0 _[◦]_ 17 _[′]_ 36 _[′′]_


18 _[′]_ 00 _[′′]_


11 _[′]_ 00 _[′′]_


+0 _[◦]_ 10 _[′]_ 54 _[′′]_



1


0


5


4


3


2


1


0


2


1


0


3


2


1


0



|0.1 pc|Col2|
|---|---|
|0.1 pc||
|0.1 pc||
|0.1 pc||


333 _[◦]_ 01 _[′]_ 18 _[′′]_ 12 _[′′]_ 06 _[′′]_ 00 _[′′]_ 00 _[′]_ 54 _[′′]_ 48 _[′′]_ 42 _[′′]_

Galactic Longitude



**Fig.** **6.** Hierarchical fragmentation. Grayscale shows the primary beam uncorrected 7 m + 12 m combined images, overlaid with primary beam uncorrected 7 m ACA continuum in black (positive) and green (negative) contours with levels of ± 7 m image rms ×

[3, 3 [1][.][25], 3 [1][.][50], 3 [1][.][75], 3 [2][.][0], 3 [2][.][25], 3 [2][.][50], 3 [2][.][75], 3 [3][.][0] ]. Blue ellipses and yellow contours show the “leaves” and their shapes derived by Astrodendro. Large
and small triangles mark the positions of candidate ensembles and cores, respectively. Green and red lines are MST core separations the same as
those in Figs. 3 and 4. Blue lines indicate the clump thermal Jeans length, λ [th] J,clump [.]

Article number, page 13 of 30

_A&A proofs:_ manuscript no. hmsc



(a). Cores in Ensembles


3 _._ 5


3 _._ 0


2 _._ 5


2 _._ 0


1 _._ 5


1 _._ 0


0 _._ 5


0 _._ 0

0 _._ 00 0 _._ 02 0 _._ 04 0 _._ 06 0 _._ 08 0 _._ 10 0 _._ 12 0 _._ 14 0 _._ 16 0 _._ 18
Separations for Cores in the Same Ensemble _S_ core (pc)



0 _._ 00 0 _._ 05 0 _._ 10 0 _._ 15 0 _._ 20 0 _._ 25 0 _._ 30 0 _._ 35
Ensemble Separation _S_ ens (pc)



3 _._ 5


3 _._ 0


2 _._ 5


2 _._ 0


1 _._ 5


1 _._ 0


0 _._ 5


0 _._ 0



(b). Ensemble & Long separation



**Fig. 7.** Thermal dominant fragmentation. Red and blue filled stars represent the median values for AS and NA, except for AS3 and NA3, while
the stars with blank facecolor represent the median values for all AS and NA. The labels near the data points mark the ALMA cores (in the same
ensembles) or ensembles making up the separations. _Panel_ _(a)_ shows the separations for the cores in the same ensembles, scaled by ensemble
thermalrecalculations in the case of cylindrical fragmentation for AS3 and NA3, respectively.Jeans length λ [th] J,ens [.] [The] [color-coding] [for] [di][ff][erent] [clumps] [is] [similar] [to] [that] [of] _Panel (b)_ [Fig.] [5][.] [The] shows the ensemble MST separations scaled by [circles] [with] [cyan] [and] [blue] [facecolors] [are] [the]
clump thermal Jeans length λ [th] J,clump [.]



H ii region. This structure will be discussed in more detailed
in Sects. 5.2 and 6.3. The small organic molecular thermometer
H 2 CO is only detected toward this ensemble while there is no detection for other ensembles in AS2, suggesting that ALMA1 and
ALMA3 are in a warmer environment. H 2 CO is also detected in
the most massive cores of NA2 (ALMA1, _M_ core ≃ 6 M ⊙ ), NA3
(ALMA1, _M_ core ≃ 10.3 M ⊙ ; ALMA2, _M_ core ≃ 6.9 M ⊙ ), indicating shocked gas or warmer gas, or both. As a result, the mass of
these massive cores could be overestimated.


There are high-velocity components (≳ 10 km s [−][1] ) of
SiO _J_ = 5 − 4 detected toward the most massive core of NA4
(ALMA1, _M_ core ∼ 13 M ⊙ ) meanwhile c-H 2 COCH 2 (Ethylene
Oxide, hot core tracer, see Ikeda et al. 2001) is detected towards
ALMA2 ( _M_ core ∼ 10 M ⊙ ), showing that massive cores of NA4
are already at the protostellar stage.


AS3 presents a filamentary structure in ALMA 1.3 mm;
H 2 CO is detected towards ALMA1, 3, 4, 8, and 9, indicating
that the shocked gas or warm gas is present along the filament.
Meanwhile, SiO _J_ = 5 − 4 is detected towards ALMA1. AS3 has
been identified as a 70 µm quiet clump with single-dish (sub)mm
images by Yuan et al. (2017); Traficante et al. (2018); Urquhart
et al. (2018), and the ALMA project of Pillai but a comparison
between ALMA image, MIPSGAL 24 µm (Beam∼ 6 [′′], Carey
et al. 2009), and _Herschel_ 70 µm (Beam∼ 8.5 [′′], Molinari et al.
2010) reveals that ALMA1 ( _M_ core / _M_ J [th],clump [∼] [6) is probably asso-]
ciated with an IR source at 24 µm (20.984 mJy, FWHM≃ 6.24 [′′],
Gutermuth & Heyer 2015) and 70 µm (278 mJy, FWHM≃10.1 [′′],
Molinari et al. 2016) with an offset of 2.5 [′′] and 3.8 [′′], respectively, as shown in Fig. 9. The possible reason for ignoring the
far IR source for these authors could be the significant offset between the IR source and the single-dish (sub)mm emission peak
(see Fig. A.2 in Appendix).


Article number, page 14 of 30



To sum up, the fragmentation in most of the candidate
HMSCs in our sample is thermal-dominated except for AS1
which shows that only thermal motions or turbulence cannot
fully explain its fragmentation. The most massive cores ( _M_ core 8 M ⊙ ) in our candidate HMSCs commonly present star-forming
signposts, implying that there is no high-mass prestellar core in
our sample. Besides, we see that a large part (≳ 60%) of cores
with _M_ core - _M_ J [th],clump [may already show star-forming signposts.]
One possible reason could be the evolutionary bias that the
protostellar cores accrete more mass with evolution; another
reason is that the _T_ dust of these star-forming cores is likely to be
inaccurate that is, in this case, underestimated and leads to an
overestimation of the core mass.


**5.** **Mass distribution shaping revealed by ALMA**


In the work discussed up through the last section, we did not
find a clear difference of fragmentation between AS and NA at
∼ 0.025 pc scale in our limited sample. However, this does not
mean that there is no implication of the impacts of H ii regions
on dense ensembles or cores. In this section, we use multi
wavelength data to search for signs of impacts from H ii regions
and compare these with ALMA 1.3 mm emission.


_5.1._ _Morphology of cores and clumps_


Compared to millimeter interferometric observation, which is
only sensitive to compact emission, single-dish observation
could detect more diffuse and larger-scale emission from clump
envelope. ALMA observations recover 10–20% of the corresponding single-dish flux (see Sect. 3.2), showing that most

0 _._ 5


0 _._ 4


0 _._ 3


0 _._ 2


0 _._ 1


0 _._ 0


1 _._ 5


1 _._ 0


0 _._ 5



10 12 14 16 18 20
_T_ dust (K)



S. Zhang et al.: H ii regions and high-mass starless clump candidates


_−_ 0 _[◦]_ 11 _[′]_ 10 _[′′]_



20 _[′′]_


30 _[′′]_




|′<br>′<br>20<br>′ 15<br>10<br>′<br>5<br>′<br>0 .1 pc<br>10′′ 32′00′′ 50′′ 40′′ 22◦31′30′′|Col2|Col3|Col4|Col5|ALMA flux S/N|
|---|---|---|---|---|---|
|22_◦_31_′_30_′′_<br>40_′′_<br>50_′′_<br>32_′_00_′′_<br>10_′′_<br>_′_<br>_′_<br>_′_<br>_′_<br>_′_<br>0.1 pc<br>5<br>10<br>15<br>20|0.1 pc<br>5<br>10<br>15<br>20|0.1 pc<br>5<br>10<br>15<br>20|0.1 pc<br>5<br>10<br>15<br>20|0.1 pc<br>5<br>10<br>15<br>20|0.1 pc<br>5<br>10<br>15<br>20|
|22_◦_31_′_30_′′_<br>40_′′_<br>50_′′_<br>32_′_00_′′_<br>10_′′_<br>_′_<br>_′_<br>_′_<br>_′_<br>_′_<br>0.1 pc<br>5<br>10<br>15<br>20|0.1 pc<br>5<br>10<br>15<br>20|22_◦_31_′_30_′′_<br>40_′′_<br>50_′′_<br>32_′_00_′′_|22_◦_31_′_30_′′_<br>40_′′_<br>50_′′_<br>32_′_00_′′_|22_◦_31_′_30_′′_<br>40_′′_<br>50_′′_<br>32_′_00_′′_|22_◦_31_′_30_′′_<br>40_′′_<br>50_′′_<br>32_′_00_′′_|



0 _._ 0


_−_ 0 _._ 5


_−_ 1 _._ 0


10 12 14 16 18 20 22
_T_ dust (K)


**Fig.** **8.** Expected λ [th] J,clump [and] _[M]_ J [th],clump [for] [58] [candidate] [HMSCs] [located]
in the 3–5 kpc distance range. Red and blue contours show the distributions of _M_ J [th],clump [and][ λ] [th] J,clump [for all strongly impacted AS (31 S-type]
AS, see details in Paper I) and all NA (27), respectively. Contours with
a heavier color mean a larger number of points. Red and blue stars mark
the peaks of corresponding distributions. _Panel (a)_ shows the distributions of λ [th] J,clump [.] [The] [triangles,] [crosses,] [and] [circles] [represent] [ensemble]
MST separations, core short MST separations, and core long MST separations for the ALMA sources in this paper, respectively. _Panel_ _(b)_
shows the distributions of _M_ J [th],clump [. Circles and triangles represent core]
mass and average ensemble mass for the ALMA sources in this paper,
respectively.


masses of 70 µm quiet high-mass clumps exist in the envelope
rather than in the compact structures. Due to its lower density,
the clump envelope is expected to be more easily modified by
the compression of H ii regions. Zhang et al. (2019) studied a
sample of eight impacted high-mass protocluster clumps with a
mass and resolution similar to the ones in our study. These authors proposed that the affected clumps present a morphology
for which the embedded compact structures observed by interferometer are expected to be closer to the interface of interaction
because the clump envelope is compressed more distinctly towards the interface.

The ATLASGAL flux peak, flux weighted clump center, and
the ATLAGSAL pointing error are shown in the right panels of
Figs. 3 and 4 with yellow crosses, triangles, and circles (radius



40 _[′′]_


50 _[′′]_


Galactic Longitude


**Fig. 9.** AS3 24 µm and 70 µm emission. Green contours, star, and circle
indicate the 70 µm emission, its peak and beam, respectively. Background shows 24 µm emission with a peak at the red star. The beam of
24 µm image is shown in white circle. Color-filled contours show 7 m +
12 m combined 1.3 mm emission with levels similar to those in Fig. 4.


= 4 [′′], Schuller et al. 2009), respectively. The uncertainty in pixel
flux makes the flux peak taken from the sole pixel not reliable
as the flux weighted center. AS2 and AS4, which are deeply impacted by the H ii regions, present an asymmetrical morphology
as shown by the systematic offset between flux weighted clump
center and mass weighted core center (yellow stars in the right
panels of Figs. 3 and 4). The reason why deeply impacted AS1
does not present a clear such offset could be the density improvement due to the clump evolution (the densest clump in eight candidate HMSCs) overwhelming the density structure modified by
the compression of H ii region. AS3 is an exceptional case where
the compact structures are faraway from the interaction interface.
AS3 is only weakly affected as described in Sect. 2.2 therefore
no significant compression of the clump envelope is seen. The
3D distribution of the envelope may bias the conclusion by projection effect, which could be found for the irregular center positions for some NA sources.

Single-dish H 2 column density _N_ H 2 maps are shown with
pink contours in Figs. 10, 11, and 12 for AS1, AS2, and AS4,
respectively. The _N_ H 2 is derived from SED fitting of Hi-GAL 70,
160, 250, 350, and 500 µm emission (Herschel Infrared Galactic
Plane Survey, Molinari et al. 2010) with the techniques of point
process mapping (PPMAP) by Marsh et al. (2016), which utilize
the full instrumental point source functions to reach a spatial resolution of 12 [′′] (Marsh et al. 2015, 2017). The Hi-GAL PPMAP
column density contours suggest that AS1 and AS2 probably
have an asymmetrical mass distribution while this asymmetry
is not clearly seen in the column density profiles cut along the
direction of the interaction (see panels named as “PPMAP Normalized _N_ H 2 ” in Figs. 10, 11, and 12). The PPMAP column density peak and column density weighted clump center are marked
in Figs. 10, 11, and 12 and they show a similar trend that AS2
and AS4 core centers are closer to the interaction interference
compared to the weighted clump center.
The PPMAP column densities are equally spaced in log
space between 8 K and 50 K (see panels named as “Multi

Article number, page 15 of 30

_A&A proofs:_ manuscript no. hmsc



_T_ dust Normalized _N_ H 2 ” in Figs. 10, 11, and 12). Cold dust
( _T_ dust < 21 K) normally shows a density profile similar to
that of the cumulative density of all dust temperature. Warm
dust ( _T_ dust ≳ 21 K) profile presents a characteristic dip at the
clump center and a peak close to H ii regions. Warm dust at
20–30 K is located in the PDR surrounding the H ii regions
(Marsh & Whitworth 2019), thus, the asymmetrical warm dust
distributions suggest stronger photodissociation, which is as
expected from the incoming radiation from ionizing stars.


_5.2._ _Shaping structures in candidate HMSCs at_ ∼ 0.025 _pc_
_scale_


Among the four AS clumps of our sample, AS1 and AS2 are
probably most deeply impacted by H ii regions, according to
the clump and cm free-free continuum morphology. The lack of
high-resolution cm continuum data for AS4 environment does
not allow for a detailed analysis of its associated ionized gas.


**Evidence** **for** **gas** **and** **dust** **shaping** **in** **AS1:** The 7 m +
12 m combined 1.3 mm emission of AS1 likely emerges on a
dip of 20 cm continuum emission as shown in Fig. 10b. The
20 cm continuum of H ii region is optically thin and dominated
by free-free emission of the ionized gas. Therefore, this dip is
not due to the extinction. To highlight the ionized gas and cold
dust distribution, we created a map of normalized 20 cm continuum intensity minus normalized combined 1.3 mm intensity, as
presented in the color scale in Fig. 13. It clearly shows an overpressured ionized front (IF) that surrounds more than half of the
compact ALMA 1.3 mm emission, meanwhile, a morphology
of cometary globule with short tail following the interacting direction is clearly presented by 7 m data in Fig. 13 (Lefloch &
Lazareff 1994; Tremblin et al. 2012). The 20 cm continuum profile in Fig. 10e reveals that an intensity plateau (with a width of

∼
three beams) of 20 cm continuum profile appears on the interface, implying that the expanding ionized gas is jammed on the
clump envelope. A small fraction of ionized gas continues to leak
into the envelope but stops at more compact inner regions traced
by combined 1.3 mm emission. A blue shift peak and strong blue
wing of MALT90 optically thick HCO [+] _J_ = 1 − 0 (beam ∼ 38 [′′] )
are detected as shown in Fig. 14. The blue component may trace
the gas shocked by H ii regions or potential infalling envelope
of AS1 (Mardones et al. 1997; Evans 1999; Zhang et al. 2016;
Traficante et al. 2017).


We test whether AS1 is formed through the collect and collapse (C&C) mechanism, which describes a scenario in which
the supersonic expansion drives a shock front (SF) in front of the
IF and then a shell is collected between SF and IF. When the shell
is too dense to be gravitational stable, the shell fragments into
several clumps (Elmegreen & Lada 1977; Zavagno et al. 2007).
The gravitational fragmentation of the collected shell is expected
to happen at time _t_ frag = 1.56 _C_ 0 [7] . [/] 2 [11] _[N]_ 49 [−][1][/][11] _n_ [−] 3 [5][/][11] Myr, where _C_ 0.2
is the sound speed inside the shell in unit of 0.2 km s [−][1], which
is set as AS1 sound speed 0.24 km s [−][1] . _N_ 49 and _n_ 3 are the ionizing photon flux in unit of 10 [49] s [−][1] and the initial H number
density in unit of cm [−][3], respectively (Whitworth et al. 1994; Liu
et al. 2016). Taking the same _N_ 49 and _n_ 3 as those used in the
estimations of bubble age and pressure, _t_ frag ≃ 0.9 Myr. The
_t_ frag is larger than bubble age ≃ 0.4 Myr, revealing that AS1 is
a pre-existing clump rather than a C&C triggered clump. Taken
as a whole, AS1, presenting a cometary globule morphology, is
likely to be a pre-existing massive clump under the feedback of


Article number, page 16 of 30



bubble N1. Additional pressure from ionized gas possibly accelerates the formation of protostellar cores in AS1.
**Evidence for gas and dust shaping in AS2:** AS2 and its associated several-pc scale filament are proposed to be pre-existing
structures by Tackenberg et al. (2013). Whether triggered star
formation is happening in AS2 is not clearly revealed by the
single-dish research of Tackenberg et al. (2013). Our ALMA
mapping shows that the most massive core, ALMA1, is exactly
located in front of the PDR traced by PAH 8 µm emission as
shown in Fig. 11b and g. We also note that several ALMA cores
are situated close to the PDR edge such as ALMA3, 4, 6, and 7.
These cores and ALMA1 reside in a wall-like morphology (indicated by the connected lines in Fig. 11b and d) whose shape resembles the IF. The shape of the IF is indicated by the smoothed
contour of 20 cm continuum with a level of 3.3 rms in Fig. 11.
Considering the consistency between the IF shape and the walllike structure, the rapid decline of PAH 8 µm emission towards
ALMA1 is not only due to the IR extinction but also the dense
photodissociation region situated at the interface between the
H ii region and AS2.
Noisy 20 cm continuum (S/N ≲ 4) prevents us from detecting tiny structures of the ionized gas surrounding the clump as
observed in Fig. 13. The profile of 20 cm continuum intensity cut
along the interaction direction does not present a clear plateau or
rapid decline at the interface between H ii region and clump. The
smoothly decreasing intensity profile, without significant fluctuation, is explained with the leaking ionization radiation by Luisi
et al. (2019). Leaking ionization radiation is the possible formation mechanism for the two PDR layers indicated by 8 µm emission in Fig. 11a. The ionization radiation leaked from the closer
layer and then acted on further layer. These two layers have an
average velocity difference of 1 to 2 km s [−][1], suggesting the possible kinematic difference driven by the feedback of H ii region.
The strongest 8 µm emission surrounding ALMA1 may
reveal the strongest impact of the H ii region on ALMA1, which
is also suggested by the sole significant detection of warm or
shocked gas tracer H 2 CO in ALMA1. We check the 7 m + 12 m
combined 1.3 mm continuum in a slightly extended field of
view by lowering the cut limit of the primary beam from 20% to
10% power point, as shown by the black circles in Fig. 11b and
d. The rms mass sensitivity in 20% to 10% power point of the
primary beam is around 0.2 M ⊙ Beam [−][1] to 0.4 M ⊙ Beam [−][1] . The
minimum core mass that could be identified by Astrodendro is
∼ 0.6 M ⊙ . No new structure is found in the extended field of
view, which means that the potential undetected structures in
front of the most massive core, ALMA1, should be smaller than
0.6 M ⊙ . Therefore, we propose that ALMA1 and the other cores
in the wall-like structure are probably the closest to the IF. In
combining all the evidence, some of the cores in the wall-like
structure are likely to have a triggered origin, especially for the
most massive core, ALMA1.


**6.** **Discussion**


_6.1._ _Fragmentation mechanism_


In our limited sample, a large population (> 70%) of cores are
low-mass objects with a mass < 2 M ⊙, meanwhile, the most massive cores (> 8 M ⊙ ) in candidate HMSCs commonly present
star formation activities. The absence of high-mass prestellar
cores in candidate HMSCs is fully revealed by a series of studies
with similar sampled scale of 0.02 pc to 0.03 pc, for example,
Sanhueza et al. (2017); Contreras et al. (2018); Sanhueza et al.

S. Zhang et al.: H ii regions and high-mass starless clump candidates


Jy/Beam
0 _._ 000 0 _._ 002 0 _._ 004 0 _._ 006 0 _._ 008 0 _._ 010

1 _._ 0



PPMAP

ALMA


20 cm

ALMA



_−_ 0 _[◦]_ 16 _[′]_


17 _[′]_


18 _[′]_


19 _[′]_


20 _[′]_


_−_ 0 _[◦]_ 18 _[′]_ 00 _[′′]_


12 _[′′]_


24 _[′′]_


36 _[′′]_


48 _[′′]_



15 _[′]_ 14 _[′]_ 13 _[′]_ 12 _[′]_ 10 _[◦]_ 11 _[′]_

Galactic Longitude


12 _[′′]_ 13 _[′]_ 00 _[′′]_ 48 _[′′]_ 36 _[′′]_ 10 _[◦]_ 12 _[′]_ 24 _[′′]_

Galactic Longitude



0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0


1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0


1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0



8 K, 0.09

9.5 K, 0.11

11.2 K, 0.16

13.2 K, 0.32

15.6 K, 1.08

18.4 K, 6.31

21.7 K, 60.48

25.7 K, 110.56

30.3 K, 3.15

35.8 K, 0.0

42 K, 0.0



_−_ 1 _._ 00 _−_ 0 _._ 75 _−_ 0 _._ 50 _−_ 0 _._ 25 0 _._ 00 0 _._ 25 0 _._ 50 0 _._ 75 1 _._ 00
Distance (arcmin)



**Fig.** **10.** Impacted candidate HMSC AS1. _Panel_ _(a)_ shows the large-scale 20 cm continuum overlaid with the Hi-GAL PPMAP _N_ H 2 contours
starting from 10 [22] cm [−][2] with a step of 10 [22] cm [−][2] . The red bar indicates the pixels used to create intensity profile. _Panel (b)_ is a closer view of the
black box in _Panel (a)_, overlaid with 7 m +12 m combined 1.3 mm emission contours (white) starting from 3 rms with a step of 1 rms. The 20 cm
continuum is indicated by red contours starting from 3 rms with a step of 1 rms. The black dashed circle indicates the field of view (20% power
point) of the 1.3 mm image. The white bar indicates the pixels used for ALMA intensity profile. The yellow star, cross, and triangle are similar to
those in Figs. 3 and 4, but for the PPMAP _N_ H 2 . Yellow circles and white ellipse indicate the PPMAP and cm continuum beams, respectively. _Panel_
_(c)_ shows the normalized PPMAP _N_ H 2 and the 7 m + 12 m combined 1.3 mm intensity profiles cut along the direction indicated in _Panel (a)_ and
_(b)_ . The gray region highlights the ALMA imaging field. _Panel (d)_ shows the normalized profiles of _N_ H 2 with different _T_ dust derived by PPMAP.
The numbers after _T_ dust values in the legend are the S/N of the corresponding profiles. The S/N is set to be zero when < 0.01. _Panel (e)_ shows the
20 cm emission profile. The H ii region, interface, and plateau are indicated by different labels.



(2019); Svoboda et al. (2019); Louvet et al. (2019). It is not only
core mass, but also core separations that present a hierarchical
thermal fragmentation, favouring the CA model for high-mass
star formation. The pc-scale candidate HMSCs fragment into
several ensembles with separations of clump Jeans length λ [th] J,clump
and then some of the ensembles continue to fragment into cores
with separations of ensemble Jeans length, λ [th] J,ens [.]
Even if the core spatial distributions present a diverse morphology, from cluster-like (AS1 and AS4) to filamentary (AS3



and NA3) or simply irregular (AS2 and NA4), a common pattern
between the core and ensemble separations seems to exist within
the diverse morphology. The typical ensemble separation _S_ ens is
∼ 0.18 pc within a range of about 0.1 to 0.3 pc meanwhile the
typical core separation _S_ core in the ensemble is ∼ 0.06 pc within
a range about 0.04 to 0.08 pc, as shown in Fig. 7. It casts light
on the typical thermal Jeans length ratio of ensemble to clump
λ [th]
J,ens [/][λ] [th] J,clump [is][ ≲] [1][/][3.]


Article number, page 17 of 30

_A&A proofs:_ manuscript no. hmsc



Article number, page 18 of 30

S. Zhang et al.: H ii regions and high-mass starless clump candidates



PPMAP

ALMA


8 K, 0.08

9.5 K, 0.1

11.2 K, 0.15

13.2 K, 0.34

15.6 K, 1.38

18.4 K, 7.5

21.7 K, 28.22

25.7 K, 7.34

30.3 K, 0.0

35.8 K, 0.0

42 K, 0.0


8 _µ_ m

ALMA



_−_ 0 _[◦]_ 43 _[′]_


44 _[′]_


45 _[′]_


46 _[′]_


47 _[′]_


_−_ 0 _[◦]_ 44 _[′]_ 36 _[′′]_


48 _[′′]_


45 _[′]_ 00 _[′′]_


12 _[′′]_


24 _[′′]_



DN

50 60 70 80 90 100 110


03 _[′]_ 02 _[′]_ 01 _[′]_ 333 _[◦]_ 00 _[′]_ 332 _[◦]_ 59 _[′]_

Galactic Longitude


24 _[′′]_ 12 _[′′]_ 01 _[′]_ 00 _[′′]_ 48 _[′′]_ 333 _[◦]_ 00 _[′]_ 36 _[′′]_

Galactic Longitude



1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0


1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0


1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0



_−_ 1 _._ 00 _−_ 0 _._ 75 _−_ 0 _._ 50 _−_ 0 _._ 25 0 _._ 00 0 _._ 25 0 _._ 50 0 _._ 75 1 _._ 00
Distance (arcmin)



**Fig. 12.** Impacted candidate HMSC AS4. _Panel (a)_ shows the 8 µm emission overlaid with PPMAP _N_ H 2 contours with levels similar to Fig. 10.
The red bar shows the pixels used to create the profile. _Panel (b)_ is a closer view of _Panel (a)_, overlaid with 7 m + 12 m combined 1.3 mm contours
with levels starting from 3 rms with a step of 1 rms. _Panels (c)_ to _(e)_ are similar to those in Fig. 10.



We collect the information from previous 7 m + 12 m combined band 6 observations toward 31 high-mass clumps at 3–
5 kpc (Contreras et al. 2018; Sanhueza et al. 2019; Svoboda
et al. 2019), which are quiet from ∼ 1 µm to 70 µm and have
a mass from 240 M ⊙ to 5200 M ⊙ with a median of 760 M ⊙ . The
resolution is around 0.01 to 0.03 pc. The sensitivity and coverage of these observations are all different. Contreras et al. (2018)
and Sanhueza et al. (2019) are mosaic observations covering full
clump with a sensitivity of ∼ 0.1 mJy Beam [−][1] whereas Svoboda
et al. (2019) and our data are single pointing observations with a
sensitivity of ∼ 0.05 mJy Beam [−][1] and ∼ 0.15 mJy Beam [−][1], respectively. This data collection is statistically significant for obtaining a universal fragmentation mechanism for candidate HMSCs. Notably, nearly all collected candidate HMSCs are NA besides the AS sample in this paper and G341.039-00.114 from
Sanhueza et al. (2019) because these authors usually set an upper limitation on _T_ dust, causing a bias of preference selection of
NA.


Figure 15 shows the number distribution for total 363 MST
core separations scaled by clump thermal Jeans length λ [th] J,clump [of]



the collected sources. More than 70% of MST separations are
less than λ [th] [The] [maximum] [and] [sub-maximum] [are] [peaked]
J,clump [.]
at around 0.38λ [th] J,clump [and 0.9][λ] [th] J,clump [, respectively. Firstly, the as-]
sumption of the unimodal distribution is excluded for Fig. 15, by
applying Hartigan’s Dip test (Hartigan & Hartigan 1985). Then
we test multimodal distributions by ACR methods (see details
about ACR in Ameijeiras-Alonso et al. 2016) using the “modetest” function in the R package “multimode” [5] . The test’s results support the assumption that the bimodal distribution is the
most likely distribution in the scaled separation range of 0 to 1
in Fig. 15 and therefore prove the reliability of maximum and
sub-maximum marked in Fig. 15. Similar bimodal fragmentation nature presented in Fig. 15 for the samples of Svoboda et al.
(2019), Sanhueza et al. (2019), and this paper reveals that different coverage and sensitivity of ALMA observations do not
largely impact on the result of the bimodal fragmentation nature. Although some low-mass cores could be lost in our single

5 See more details on the “multimode” package in Ameijeiras-Alonso
et al. (2018).


Article number, page 19 of 30

_A&A proofs:_ manuscript no. hmsc



Long Separation

Short Separation

Total & Larger Bin
Sanhueza et al. (2019)


Svoboda et al. (2019)


Contreras et al. (2018)

This Paper



_−_ 0 _[◦]_ 18 _[′]_ 10 _[′′]_


20 _[′′]_



0 _._ 6


0 _._ 4


0 _._ 2



60


50


40



0 _._ 0


30 _[′′]_


_−_ 0 _._ 2


40 _[′′]_


10 _[◦]_ 13 _[′]_ 10 _[′′]_ 00 _[′′]_ 12 _[′]_ 50 _[′′]_ 40 _[′′]_


Galactic Longitude


**Fig.** **13.** Normalized intensity of AS1. This map shows the value of
normalized 20 cm intensity minus normalized 7 m + 12 m combined
1.3 mm continuum. White contours start from 3 rms with a step of
1 rms. The gray curve indicates the IF or the interface of interaction.
Red and black contours represent the 7 m + 12 m combined and 7 m
alone 1.3 mm continuum with the levels similar to Figs. 3 and 6, respectively.


**Fig.** **14.** Single-dish spectra of AS1. Red and black spectra show the
single-dish optically thick MALT90 HCO [+] _J_ = 1 − 0 and optically thin
MALT90 H [13] CO [+] _J_ = 1 − 0 transitions, respectively. The spatial and
velocity resolutions are 38 [′′] and 0.11 km s [−][1], respectively. To improve
the depiction, the spectra have been regridded to 0.45 km s [−][1] . Green
lines are fitted Gaussian and its center.


pointing, slightly more noisy observation, the bimodal nature of
fragmentation revealed here is reliable.
As a result, most of the NA clumps fragment in a hierarchical and thermal way, consistent with several studies of the
high-mass clumps at a later evolutionary stage. Klaassen et al.
(2018) analyzed nine hypercompact H ii regions with ALMA at
a resolution of ≲ 0.01 pc and found that the embedded cores are
in line with the consequences of thermal fragmentation. This re

Article number, page 20 of 30



30


20


10


0


0 _._ 0 0 _._ 5 1 _._ 0 1 _._ 5 2 _._ 0 2 _._ 5 3 _._ 0 3 _._ 5
MST _S_ core _/λ_ [th] J _,_ clump


**Fig.** **15.** Statistics of core MST separations for 31 candidate HMSCs.
The data have been taken from Contreras et al. (2018); Svoboda et al.
(2019); Sanhueza et al. (2019), and from the sources in this paper.
Clump properties for the candidate HMSCs in the single pointing mapping of Svoboda et al. (2019) are taken from Paper I when possible, to
improve the consistency of the data. Therefore, the number distributions
for the sources of Svoboda et al. (2019) here are slightly different from
the raw ones. There are a total of 363 separations. The size of the bin is
set to be 0.075 (color-filled histogram) and 0.15 (black-edge histogram)
to avoid bias. Red and blue lines mark the two peaks of the distribution.


sult coincides with that revealed in the CORE program (Beuther
et al. 2018a), which surveyed 20 young high-mass star-forming
regions containing high-mass protostellar objects (HMPOs) and
revealed that turbulent fragmentation is less effective than thermal fragmentation at a resolution of ≲ 0.01 pc.
With the assumption that most of the candidate HMSCs are
dominated by thermal fragmentation, candidate HMSCs with a
similar density ρ but higher _T_ dust are expected to fragment to
cores with a higher mass and longer separation. In our limited
sample, it is only AS1 that obviously deviates from thermal fragmentation. The core separations and mass are at least three times
larger than the determined thermal values. Compared to other
candidate HMSCs, AS1 is probably the most evolved considering that its clump surface density Σ ∼ 1 g cm [−][2] is one magnitude
larger than others (∼ 0.1 g cm [−][2] ). A higher core mass is probably due to evolutionary effects. An observational comparison
between high-mass prestellar clumps and high-mass protostellar clumps with ALMA at a resolution of 0.02 pc shows that
the fraction of total mass in cores to clump mass increases from
≲ 0.1 to ≳ 0.2 (Neupane et al. 2020), agreeing with the simulations of Molinari et al. (2019). Notably, core separations in
AS1 are similar to that in NA1 or other candidate HMSCs, at a
scale of ≲ 0.1 pc, therefore the plausible conclusion of multifactors dominated fragmentation in AS1 derived from equations
in Sect. 4.1 is probably biased. AS1 contracts more significantly
due to the pressure of H ii regions or the evolution, increasing
clump Σ to reduce the derived λ [th] J,clump [, making it quite di][ff][erent]
from λ [th] J,clump [at an earlier stage. Even if] _[ T]_ [dust] [also increases with]

S. Zhang et al.: H ii regions and high-mass starless clump candidates



feedback of H ii region or evolution, the change fraction is only
∼ 30% to 50%, much smaller than the increase in Σ. It is possible that AS1 had a thermal fragmentation when observed at an
earlier stage.


_6.2._ _Transition of fragmentation mechanism_


Fragmentation is a process that is determined by a multitude of
factors. The relative importance between gravity, thermal motion, magnetic field, and turbulence can lead to a different fragmentation (Tang et al. 2019). The dynamics of 70 µm quiet massive clumps are believed to change from turbulent to gravitydominant when they approach a critical Σ of ∼ 0.1 g cm [−][2] (Traficante et al. 2020). One problem is that the turbulence level of AS
is obviously increased by the feedback of H ii regions, as shown
in Paper I. Therefore Σ needs to be higher for AS in order to
keep thermal fragmentation effective. AS2 and AS4 still present
a thermal fragmentation when the turbulence level increases by
less than 60% (traced by line width, see Table 1), compared to
their counterparts NA2 and NA4, which implies that turbulent
fragmentation at ∼ 0.025 pc scale requires huge energy injection
from H ii regions.

Rebolledo et al. (2020) likely found the transition from thermal fragmentation to turbulent fragmentation under the effect of
H ii regions by comparing a pair of pc-scale massive star forming clumps in the Carina region, one is severely impacted by
the H ii region and the other is less disturbed. Mach number
M derived from ALMA + ATLASGAL combined images with
the techniques of densities probability distributions (N-PDF) are
1.37 (supersonic) and 0.81 (subsonic) for impacted one and less
disturbed one, respectively. The 0.02 pc-scale fragmented cores
in the more impacted clump are less numerous and five times
more massive than the cores in the less disturbed clump. The
differences are explained with the different fragmentation mechanisms (turbulent and thermal) by Rebolledo et al. (2020).
Notably, our previous single-dish spectral analyses in Paper I
suggest that most of candidate HMSCs tend to be supersonic
while the impacted ones prefer a hypersonic status (M ≳ 5). At
this stage, it is not clear whether this turbulence increment could
change a fragmentation from thermal-dominated to turbulentdominated. The fragmentation at 0.01 pc scale in the most massive star-forming clump (M ∼ 4) impacted by the H ii region
RCW 120 (Kirsanova et al. 2019; Zavagno et al. 2020) is investigated by Figueira et al. (2018) and they suggested that turbulent
fragmentation is dominant due to the H ii region feedback. Even
for the cases where the fragmentation at around 0.02 pc scale in
the clumps is still thermal-dominated under the vigorous feedback of H ii regions, the fragments could be more massive or
less numerous (Liu et al. 2017).
Magnetic fields make the fragmentation more complex. The
presence of filamentary structure in candidate HMSCs such as
AS3 may arise from a highly magnetised environment according
to Fontani et al. (2016, 2018). Some studies have revealed the
important role of the magnetic field in the evolution of clumps
impacted by H ii regions, such as in bright rimmed clouds (Soam
et al. 2017, 2018). Eswaraiah et al. (2020) studied the _B_ fields
of massive clumps located at the waist of the bipolar H ii region
S201. These authors found that the _B_ fields of clumps are compressed and enhanced by the impact of the H ii region, leading
to a status characterized by the magnetic pressure dominating
over the turbulent and thermal pressure. Busquet et al. (2016)
explored the fragmentation of twin filament hubs at a scale of
0.03 pc. These two hubs are similar in mass, density, turbulence,
and even temperature (2 K difference). The hub more impacted



by the H ii region shows a lower fragmentation level compared
to the less impacted one. Busquet et al. (2016) explained it as
a stronger magnetic field suppressing the fragmentation in the
more impacted hub.


To summarize, the fragmentation of candidate HMSCs at
∼ 0.025 pc scale is dominated by thermal fragmentation. Turbulent or magnetic fragmentation (or both) may happen only
in some AS HMSCs that are highly impacted by H ii regions.
A specific follow-up ALMA survey towards AS HMSCs with
broad single-dish line widths, which imply an extremely turbulent status, is needed to answer whether H ii regions drive a turbulent fragmentation at ∼ 0.025 pc scale. Besides, ALMA observations of polarized dust emission are also needed to ascertain
the role of magnetic field in the fragmentation of AS HMSCs
(Beuther et al. 2018b; Dall’Olio et al. 2019; Cortes et al. 2019).


_6.3._ _Considering induced star formation in HMSCs at_
∼ 0.025 _pc scale_


AS1 and AS2 clearly show how the H ii regions shape the morphology of dense material distribution in pre-existing candidate
HMSCs. The cometary globule morphology of ALMA dense
emission of AS1 that is located just at the edge of the H ii region
probably reveals the classical triggered star-formation mechanism, with radiation driven implosion (RDI) at work here. The
RDI presents a picture where the UV photons ionize the surface
of a pre-existing clump to form an overpressured ionized layer
and then help the clump to collapse (Lefloch & Lazareff 1994;
Kessel-Deynet & Burkert 2003; Miao et al. 2009). The young
associated bubble N1 (∼ 0.4 ± 0.2 Myr) likely came across AS1
during the expansion and then the ionized gas of the bubble interacted with the recently ionized clump surface to form the ionized
layer observed in Fig. 13. Additional pressure from the ionized
layer probably promotes the collapse. IR-quiet AS1 is expected
to have an age of 0.05–0.1 Myr according to the statistical summary of the starless MDCs by Motte et al. (2018). We assume
that the IF of the bubble just propagated beyond half of AS1 with
an averaged bubble expanding velocity of ≲ 2 km s [−][1], which is
estimated from bubble size divided by age. The interaction time
between the H ii region and AS1 is around 0.04–0.13 Myr. This
roughly agrees with the expected age of AS1. Following all the
evidence found here, we suggest that the cores in AS1 probably
have a triggered origin.
AS2 presents an impacted morphology different from AS1.
H ii region is shaping a pre-existing 2–3 pc scale filament. The
alignment between IF and dense gas from several-pc-scale filament, one-pc clumps to 0.02 pc-scale cores, reveals the multiscale shaping effect of the H ii region. All cores in AS2 are lowmass cores (≲ 2 M ⊙ ). Tackenberg et al. (2013) found that AS2
single-dish H [13] CO [+] spectra have two velocity components with
a shift of ∼ 2 km s [−][1] (see Fig. 11 in their paper) and suggested
that these two components are emission from pre-existing clump
gas and shocked gas, respectively. The intensity ratio between
the two components indicates that the shock does not propagate
beyond the single-dish density peak of AS2. The stopped shock
is explained by Tackenberg et al. (2013) with the resistance of
the highest density region. With ALMA images, the shock probably has propagated beyond the wall-like structure and stopped
at the further ensemble of cores shown in Fig. 11. We propose
that some of the cores in wall-like structure probably have an induced origin. Follow-up ALMA spectral mapping towards these
cores would help us to determine the evolutionary stage of each
core and, thus, to demonstrate their triggered origin. For exam

Article number, page 21 of 30

_A&A proofs:_ manuscript no. hmsc



ple, if the cores in the wall-like structure are more evolved than
other less impacted cores such as ALMA 2, 8, and 9, which may
indicate that the impacted cores formed earlier under the impacts
of H ii regions.
In short, ALMA data of AS1 and AS2 reveal that H ii regions
are able to modify the dense structures at ∼ 0.025 pc scale in
candidate HMSCs, which may help the formation of stars in this
kind of early stage clumps.


**7.** **Conclusion**


Our study is based on an ALMA continuum investigation of the
ionization feedback on ∼ 0.025 pc-scale fragmentation in candidate high-mass starless clumps (HMSCs), in which we explored
four pairs of candidate HMSCs, including four clumps affected
by H ii regions (referred to as AS HMSCs) and another four that
were located in quiet environment (referred to as NA HMSCs).
The AS and NA in each pair are required to be similar in mass
and distance to avoid any possible bias related to these quantities. Using the ALMA 1.3 mm continuum, with a resolution of
∼ 0.025 pc, we drew the following conclusions:


1. We did not find a clear difference in the fragmented ALMA
core mass and separations between AS HMSCs and NA HMSCs in our limited sample, although H ii regions seem to affect the morphology of the cores’ spatial distribution.
2. At ∼ 0.025 pc scale, thermal Jeans fragmentation with hierarchical nature dominates the fragmentation of most of the
parsec-scale candidate HMSCs. The candidate HMSCs fragment into ensembles with separations of clump Jeans length,
λ [th] [and] [then] [some] [of] [the] [ensembles] [continue] [to] [ther-]
J,clump [,]
mally fragment into cores with separations of about one third
of the λ [th]
J,clump [.]
3. AGAL010.214-00.306 (AS1), which is affected by the
H ii region, is the only candidate HMSC in our eight sources
where other factors beside thermal motions could play an
important role in the fragmentation process. The fragmented
core mass (10-17 M ⊙ ) and separations (∼ 0.1 pc) are at least
three times larger than the thermal-determined values.
4. H ii regions are able to modify the dense material distributions embedded in candidate HMSCs, which probably helps the formation of next-generation stars. AS1 and
AGAL018.931-00.029 (AS2) are the two most-likely cases
in our sample which indicate signs of impact from the
H ii region. ALMA continuum reveals that AS1 presents a
cometary globular morphology meanwhile the fragmented
cores in AS2 show a spatial distribution aligned with the ionization front.


Figure 16 tentatively draws a picture of hierarchical, thermaldominated fragmentation for candidate HMSCs under the impacts of H ii regions. Future ALMA polarized imaging toward
a large sample of highly-turbulent candidate HMSCs (with the
broadest lines in single-dish spectra) that are strongly impacted
by H ii regions will ascertain the role of thermal fragmentation in
candidate HMSCs and shed light on whether turbulent or magnetic fragmentation could take over in extreme cases.


_Acknowledgements._ SZ thanks to the funding of ALMA Region Center Grenoble and IRAM. AZ thanks the support of the Institut Universitaire de France.
TGSP gratefully acknowledges support by the National Science Foundation under grant No. AST-2009842. We want to thank the anonymous referee for the
constructive comments that helped to improve the quality of the paper. _Herschel_
Hi-GAL data processing, map production and source catalogue generation is the
result of a multi-year effort thanks to Contracts I/038/080/0 and I/029/12/0 from
ASI (Agenzia Spaziale Italiana). This paper makes use of the following ALMA


Article number, page 22 of 30









**Fig.** **16.** Proposed scenario for ∼ 0.025 pc-scale fragmentation in the
impacted candidate HMSCs. Σ clump and ρ clump are the clump surface
density and volume density, respectively, while Σ ens and ρ ens are the
corresponding values for ensemble. Clump and ensemble thermal Jeans
lengths are λ [th] J,clump [and] [λ] [th] J,ens [,] [respectively.] [Whether] [and] [how] [induced]
star formation and turbulent or magnetic fragmentation take place in
extremely impacted HMSCs need more studies.


data: ADS/JAO.ALMA#2016.1.01346.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ.


**References**


Alves, J., Lombardi, M., & Lada, C. J. 2007, A&A, 462, L17
Ameijeiras-Alonso, J., Crujeiras, R. M., & Rodríguez-Casal, A. 2016, arXiv eprints, arXiv:1609.05188
Ameijeiras-Alonso, J., Crujeiras, R. M., & Rodríguez-Casal, A. 2018, arXiv eprints, arXiv:1803.00472
Anderson, L. D., Bania, T. M., Balser, D. S., et al. 2014, ApJS, 212, 1
Avison, A., Quinn, L. J., Fuller, G. A., et al. 2016, MNRAS, 461, 136
Beuther, H., Mottram, J. C., Ahmadi, A., et al. 2018a, A&A, 617, A100
Beuther, H., Soler, J. D., Vlemmings, W., et al. 2018b, A&A, 614, A64
Bianchin, M., Lima, E. F., Bica, E., et al. 2019, PASA, 36, e044
Bock, D. C. J., Large, M. I., & Sadler, E. M. 1999, AJ, 117, 1578
Bonnell, I. A., Bate, M. R., Clarke, C. J., & Pringle, J. E. 2001, MNRAS, 323,
785
Bonnell, I. A., Vine, S. G., & Bate, M. R. 2004, MNRAS, 349, 735
Busquet, G., Estalella, R., Palau, A., et al. 2016, ApJ, 819, 139
Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, PASP, 121, 76
Chandrasekhar, S. & Fermi, E. 1953, ApJ, 118, 116
Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213
Clarke, S. D., Williams, G. M., Ibáñez-Mejía, J. C., & Walch, S. 2019, MNRAS,
484, 4024
Contreras, Y., Sanhueza, P., Jackson, J. M., et al. 2018, ApJ, 861, 14
Cortes, P. C., Hull, C. L. H., Girart, J. M., et al. 2019, ApJ, 884, 48
Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75
Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2014, ApJ, 796, L2
Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2017, MNRAS, 468, 3694
Dall’Olio, D., Vlemmings, W. H. T., Persson, M. V., et al. 2019, A&A, 626, A36
Deharveng, L., Schuller, F., Anderson, L. D., et al. 2010, A&A, 523, A6
Dib, S. & Henning, T. 2019, A&A, 629, A135
Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2014, A&A, 570, A1
Efremov, Y. N. & Elmegreen, B. G. 1998, MNRAS, 299, 588
Elmegreen, B. G. & Lada, C. J. 1977, ApJ, 214, 725
Eswaraiah, C., Li, D., Samal, M. R., et al. 2020, ApJ, 897, 90
Evans, Neal J., I. 1999, ARA&A, 37, 311
Feng, S., Beuther, H., Zhang, Q., et al. 2016, A&A, 592, A21
Figueira, M., Bronfman, L., Zavagno, A., et al. 2018, A&A, 616, L10
Fleming, B., France, K., Lupu, R. E., & McCandliss, S. R. 2010, ApJ, 725, 159

S. Zhang et al.: H ii regions and high-mass starless clump candidates



Fontani, F., Commerçon, B., Giannetti, A., et al. 2016, A&A, 593, L14
Fontani, F., Commerçon, B., Giannetti, A., et al. 2018, A&A, 615, A94
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1
Gieser, C., Semenov, D., Beuther, H., et al. 2019, A&A, 631, A142
Girichidis, P., Federrath, C., Banerjee, R., & Klessen, R. S. 2011, MNRAS, 413,
2741
Gutermuth, R. A. & Heyer, M. 2015, AJ, 149, 64
Guzmán, A. E., Sanhueza, P., Contreras, Y., et al. 2015, ApJ, 815, 130
Hartigan, J. A. & Hartigan, P. M. 1985, Ann. Statist., 13, 70
Helfand, D. J., Becker, R. H., White, R. L., Fallon, A., & Tuttle, S. 2006, AJ,
131, 2525
Hildebrand, R. H. 1983, QJRAS, 24, 267
Ikeda, M., Ohishi, M., Nummelin, A., et al. 2001, ApJ, 560, 792
Ingallinera, A., Trigilio, C., Umana, G., et al. 2014, MNRAS, 437, 3626
Jackson, J. M., Finn, S. C., Chambers, E. T., Rathborne, J. M., & Simon, R. 2010,
ApJ, 719, L185
Jackson, J. M., Rathborne, J. M., Foster, J. B., et al. 2013, PASA, 30, e057
Jeans, J. H. 1902, Philosophical Transactions of the Royal Society of London
Series A, 199, 1
Johnston, K. G., Beuther, H., Linz, H., et al. 2014, A&A, 568, A56
Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I., & Lee, C. W. 2008,
A&A, 487, 993
Kendrew, S., Beuther, H., Simpson, R., et al. 2016, ApJ, 825, 142
Kessel-Deynet, O. & Burkert, A. 2003, MNRAS, 338, 545
Kirsanova, M. S., Pavlyuchenkov, Y. N., Wiebe, D. S., et al. 2019, MNRAS, 488,
5641
Klaassen, P. D., Johnston, K. G., Urquhart, J. S., et al. 2018, A&A, 611, A99
Kong, S., Tan, J. C., Caselli, P., et al. 2017, ApJ, 834, 193
Kroupa, P. 2001, MNRAS, 322, 231
Krumholz, M. R., Klein, R. I., McKee, C. F., Offner, S. S. R., & Cunningham,
A. J. 2009, Science, 323, 754
Krumholz, M. R. & McKee, C. F. 2008, Nature, 451, 1082
Lefloch, B. & Lazareff, B. 1994, A&A, 289, 559
Li, S., Zhang, Q., Pillai, T., et al. 2019, ApJ, 886, 130
Lin, S.-J., Pagani, L., Lai, S.-P., Lefèvre, C., & Lique, F. 2020, A&A, 635, A188
Liu, H.-L., Li, J.-Z., Wu, Y., et al. 2016, ApJ, 818, 95
Liu, T., Lacy, J., Li, P. S., et al. 2017, ApJ, 849, 25
Louvet, F., Motte, F., Gusdorf, A., et al. 2016, A&A, 595, A122
Louvet, F., Neupane, S., Garay, G., et al. 2019, A&A, 622, A99
Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9
Luisi, M., Anderson, L. D., Liu, B., Anish Roshi, D., & Churchwell, E. 2019,
ApJS, 241, 2
Mac Low, M.-M. & Klessen, R. S. 2004, Reviews of Modern Physics, 76, 125
Makai, Z., Anderson, L. D., Mascoop, J. L., & Johnstone, B. 2017, ApJ, 846, 64
Mardones, D., Myers, P. C., Tafalla, M., et al. 1997, ApJ, 489, 719
Marsh, K. A., Ragan, S. E., Whitworth, A. P., & Clark, P. C. 2016, MNRAS,
461, L16
Marsh, K. A. & Whitworth, A. P. 2019, MNRAS, 483, 352
Marsh, K. A., Whitworth, A. P., & Lomax, O. 2015, MNRAS, 454, 4282
Marsh, K. A., Whitworth, A. P., Lomax, O., et al. 2017, MNRAS, 471, 2730
Martín-Hernández, N. L., Vermeij, R., & van der Hulst, J. M. 2005, A&A, 433,
205
Matsushita, Y., Takahashi, S., Machida, M. N., & Tomisaka, K. 2019, ApJ, 871,
221
McKee, C. F. & Tan, J. C. 2003, ApJ, 585, 850
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127
Miao, J., White, G. J., Thompson, M. A., & Nelson, R. P. 2009, ApJ, 692, 382
Molet, J., Brouillet, N., Nony, T., et al. 2019, A&A, 626, A132
Molinari, S., Baldeschi, A., Robitaille, T. P., et al. 2019, MNRAS, 486, 4508
Molinari, S., Schisano, E., Elia, D., et al. 2016, A&A, 591, A149
Molinari, S., Swinyard, B., Bally, J., et al. 2010, PASP, 122, 314
Mookerjea, B., Sandell, G., Güsten, R., et al. 2019, A&A, 626, A131
Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41
Neupane, S., Garay, G., Contreras, Y., Guzmán, A. E., & Rodríguez, L. F. 2020,
ApJ, 890, 76
Nony, T., Louvet, F., Motte, F., et al. 2018, A&A, 618, L5
Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943
Palau, A., Ballesteros-Paredes, J., Vázquez-Semadeni, E., et al. 2015, MNRAS,
453, 3785
Palau, A., Estalella, R., Girart, J. M., et al. 2014, ApJ, 785, 42
Palmeirim, P., Zavagno, A., Elia, D., et al. 2017, A&A, 605, A35
Pandey, A. K., Sharma, S., Kobayashi, N., Sarugaku, Y., & Ogura, K. 2020a,
MNRAS, 492, 2446
Pandey, R., Sharma, S., Panwar, N., et al. 2020b, ApJ, 891, 81
Panwar, N., Samal, M. R., Pandey, A. K., Singh, H. P., & Sharma, S. 2019, AJ,
157, 112
Pillai, T., Kauffmann, J., Zhang, Q., et al. 2019, A&A, 622, A54
Rebolledo, D., Guzmán, A. E., Contreras, Y., et al. 2020, ApJ, 891, 113



Reid, M. J., Dame, T. M., Menten, K. M., & Brunthaler, A. 2016, ApJ, 823, 77
Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ,
679, 1338
Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102
Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97
Schuller, F., Csengeri, T., Urquhart, J. S., et al. 2017, A&A, 601, A124
Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415
Soam, A., Maheswar, G., Lee, C. W., Neha, S., & Andersson, B. G. 2017, MNRAS, 465, 559
Soam, A., Maheswar, G., Lee, C. W., Neha, S., & Kim, K.-T. 2018, MNRAS,
476, 4782
Svoboda, B., Shirley, Y., Battersby, C., Beuther, H., & Traficante, A. 2020, in
The 35th Annual New Mexico Symposium, 15
Svoboda, B. E., Shirley, Y. L., Battersby, C., et al. 2016, ApJ, 822, 59
Svoboda, B. E., Shirley, Y. L., Traficante, A., et al. 2019, ApJ, 886, 36
Tackenberg, J., Beuther, H., Plume, R., et al. 2013, A&A, 550, A116
Tang, X. D., Henkel, C., Menten, K. M., et al. 2018, A&A, 609, A16
Tang, Y.-W., Koch, P. M., Peretto, N., et al. 2019, ApJ, 878, 10
Traficante, A., Fuller, G. A., Billot, N., et al. 2017, MNRAS, 470, 3882
Traficante, A., Fuller, G. A., Duarte-Cabral, A., et al. 2020, MNRAS, 491, 4310
Traficante, A., Fuller, G. A., Smith, R. J., et al. 2018, MNRAS, 473, 4975
Tremblin, P., Anderson, L. D., Didelon, P., et al. 2014, A&A, 568, A4
Tremblin, P., Audit, E., Minier, V., Schmidt, W., & Schneider, N. 2012, A&A,
546, A33
Umemoto, T., Minamidani, T., Kuno, N., et al. 2017, PASJ, 69, 78
Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059
Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275
Whitworth, A. P., Bhattal, A. S., Chapman, S. J., Disney, M. J., & Turner, J. A.
1994, MNRAS, 268, 291
Yuan, J., Wu, Y., Ellingsen, S. P., et al. 2017, ApJS, 231, 11
Zapata, L. A., Loinard, L., Su, Y. N., et al. 2012, ApJ, 744, 86
Zavagno, A., André, P., Schuller, F., et al. 2020, A&A, 638, A7
Zavagno, A., Pomarès, M., Deharveng, L., et al. 2007, A&A, 472, 835
Zhang, C.-P., Csengeri, T., Wyrowski, F., et al. 2019, A&A, 627, A85
Zhang, S., Zavagno, A., Yuan, J., et al. 2020, A&A, 637, A40
Zhang, S.-J., Wu, Y., Li, J. Z., et al. 2016, MNRAS, 458, 4222
Zinnecker, H. & Yorke, H. W. 2007, ARA&A, 45, 481


Article number, page 23 of 30

_A&A proofs:_ manuscript no. hmsc


**Appendix A:** **Supplementary data**


Figures A.1 and A.2 present GLIMPSE 8 µm, MIPSGAL
24 µm and Hi-GAL 70 µm emission of the candidate HMSCs’
region. The cores identified with Astrodendro and the derived
physical parameters are listed in Table A.1 and A.2, respectively.
Figures A.3 and A.4 show the 7 m array continuum and Astrodendro leaves extracted in the 7 m images. The parameters of
leaves are listed in Table A.3.


**Appendix B:** **Math derivations**


_Appendix B.1:_ _Mean ratio of projected separation to actual_
_separation (Sanhueza et al. 2019)_


Setting α as the angle between actual separation _S_ actu and projected separation _S_ proj, we have


_S_ actu × _cos_ (α) = _S_ proj .


The mean ratio is



_S_ proj / _S_ actu = _cos_ (α) = [1]

π



π

2
� − [π]



− [π]



2

_cos_ ( _x_ ) _dx_ = [2]

[π] π

2



π [.]



_Appendix B.2:_ _Molecular weight per hydrogen molecule_ µ H 2
_and mean molecular weight per free particle_ µ
_(Kauffmann et al. 2008)_


Assuming a mass ratio of M(H)/M ≈ 0.71, M(He)/M ≈ 0.27,
M(Z)/M ≈ 0.02 for hydrogen, helium, and metals, respectively,
where M = M(H) + M(He) + M(Z). The molecular weight per
hydrogen molecule is:


M M
µ H 2 =
_m_ H × N(H 2 ) [=] _m_ H × [1] 2 [N(H)]


2M 2M
= _m_ H × N(H) [=] M(H)

≈ 2.8,


where N(H), N(H 2 ), and _m_ H are the numbers of H, H 2, and the
mass of H atoms, respectively.
In the calculation of thermal velocity dispersion, σ th is related to the number of free particles, thus, we need to calculate
the mean molecular weight per free particle, which is:


M M
µ = _m_ H × N [≈] _m_ H × N(H 2 ) + _m_ H × N(He)


M

=

1
2 [M][(H)][ +] _[ m]_ [H] [ ×][ N(He)]


M

=

1 [1]
2 [M][(H)][ +] 4 [M][(He)]


≈ 2.37.


Article number, page 24 of 30

S. Zhang et al.: H ii regions and high-mass starless clump candidates



















































31 _[′]_ 00 _[′′]_ 40 _[′′]_ 20 _[′′]_ 30 _[′]_ 00 _[′′]_ 40 _[′′]_ 15 _[◦]_ 29 _[′]_ 20 _[′′]_

Galactic Longitude



31 _[′]_ 00 _[′′]_ 40 _[′′]_ 20 _[′′]_ 30 _[′]_ 00 _[′′]_ 40 _[′′]_ 15 _[◦]_ 29 _[′]_ 20 _[′′]_

Galactic Longitude



31 _[′]_ 00 _[′′]_ 40 _[′′]_ 20 _[′′]_ 30 _[′]_ 00 _[′′]_ 40 _[′′]_ 15 _[◦]_ 29 _[′]_ 20 _[′′]_

Galactic Longitude



**Fig.** **A.1.** IR emission of candidate HMSCs’ region. Each row shows 8 µm, 24 µm, and 70 µm emission for each source. ATLASGAL 870 µm
emission is shown with black contours with levels the same as Fig. 1. The black circles indicate the beam size of IR images, except for 8 µm
images, owing to their small beam size (≃ 2 [′′] ).


Article number, page 25 of 30

_A&A proofs:_ manuscript no. hmsc



















_−_ 0 _[◦]_ 44 _[′]_ 20 _[′′]_


40 _[′′]_


45 _[′]_ 00 _[′′]_


20 _[′′]_


40 _[′′]_





















46 _[′]_ 00 _[′′]_





12 _[′]_ 00 _[′′]_


40 _[′′]_


20 _[′′]_


11 _[′]_ 00 _[′′]_


40 _[′′]_


+0 _[◦]_ 10 _[′]_ 20 _[′′]_









20 _[′′]_ 34 _[′]_ 00 _[′′]_ 40 _[′′]_ 20 _[′′]_ 33 _[′]_ 00 _[′′]_ 40 _[′′]_ 29 _[◦]_ 3 **2** 0 _[′]_ 20 _[′′]_ _[′′]_



0 _[′]_ 20 _[′′]_ _[′′]_ 34 _[′]_ 00 _[′′]_ 40 _[′′]_ 20 _[′′]_ 33 _[′]_ 00 _[′′]_ 40 _[′′]_ 29 _[◦]_ 32 _[′]_ 2020 _[′]_ _**[′]**_ _[′]_




_[′]_ 2020 _[′]_ _**[′]**_ _[′]_ 34 _[′]_ 00 _[′′]_ 40 _[′′]_ 20 _[′′]_ 33 _[′]_ 00 _[′′]_ 40 _[′′]_ 29 _[◦]_ 32 _[′]_ 20 _[′′]_



Galactic Longitude



Galactic Longitude



Galactic Longitude



**Fig. A.2.** IR emission of candidate HMSCs’ region. The meanings of each panel are similar to Fig. A.1 but for different HMSCs.


Article number, page 26 of 30

S. Zhang et al.: H ii regions and high-mass starless clump candidates


**Table A.1.** Astrodendrogram results for the combined images.


Clump Core _[(a)]_ _l_ _b_ major _[(b)]_ minor _[(b)]_ PA _R_ _[(b)]_ _F_ _[(c)]_ _F_ 1 ~~[p]~~ _(d)_ _F_ 2 ~~[p]~~ _(d)_ S/N
( [◦] ) ( [◦] ) ( [′′] ) ( [′′] ) ( [◦] ) ( [′′] ) (mJy) (mJy) (mJy Beam [−][1] )



AGAL010.214-00.306
(AS1)


AGAL009.951-00.366
(NA1)


AGAL018.931-00.029
(AS2)


AGAL015.503-00.419
(NA2)


AGAL022.531-00.192
(AS3)


AGAL018.801-00.297
(NA3)


AGAL333.016-00.751
(AS4)


AGAL029.556+00.186
(NA4)



ALMA1 10.2134 -0.3049 1.66 0.96 90.8 1.26 49.80 ± 8.13 0.59 ± 0.026 13 ± 0.59 6.1

ALMA2 10.2153 -0.3057 1.39 1.00 64.6 1.18 42.32 ± 6.39 0.48 ± 0.027 11 ± 0.60 6.6

ALMA3 10.2153 -0.3038 1.75 1.13 142.5 1.41 38.34 ± 8.89 0.28 ± 0.033 6.3 ± 0.74 4.3


ALMA1 9.9503 -0.3671 1.29 0.62 80.7 0.90 4.96 ± 1.01 0.081 ± 0.009 2.0 ± 0.22 4.9

ALMA2 9.9525 -0.3660 1.07 0.63 54.5 0.82 4.00 ± 0.92 0.063 ± 0.010 1.5 ± 0.23 4.3

ALMA3 9.9496 -0.3670 0.68 0.42 118.0 0.54 1.36 ± 0.37 0.041 ± 0.009 1.0 ± 0.23 3.7

ALMA4 9.9481 -0.3633 0.45 0.27 70.4 0.35 0.98 ± 0.28 0.067 ± 0.015 1.6 ± 0.37 3.5


ALMA1 18.9312 -0.0246 0.80 0.47 154.5 0.61 9.12 ± 1.30 0.27 ± 0.025 5.1 ± 0.47 7.0

ALMA2 18.9287 -0.0326 1.02 0.63 82.5 0.80 6.51 ± 1.45 0.12 ± 0.019 2.3 ± 0.35 4.5

ALMA3 18.9317 -0.0248 0.40 0.24 -150.8 0.31 2.02 ± 0.32 0.17 ± 0.023 3.1 ± 0.43 6.3

ALMA4 18.9339 -0.0297 0.67 0.32 73.3 0.46 1.87 ± 0.43 0.087 ± 0.014 1.6 ± 0.26 4.3

ALMA5 18.9323 -0.0289 0.54 0.49 104.6 0.51 1.81 ± 0.37 0.064 ± 0.010 1.2 ± 0.18 4.8

ALMA6 18.9344 -0.0302 0.50 0.38 93.4 0.44 1.54 ± 0.42 0.085 ± 0.017 1.6 ± 0.33 3.7

ALMA7 18.9326 -0.0283 0.61 0.33 166.5 0.45 1.32 ± 0.29 0.057 ± 0.010 1.1 ± 0.20 4.5

ALMA8 18.9296 -0.0329 0.44 0.22 119.1 0.31 0.87 ± 0.25 0.071 ± 0.018 1.3 ± 0.33 3.5

ALMA9 18.9289 -0.0318 0.32 0.23 74.7 0.27 0.63 ± 0.15 0.066 ± 0.014 1.2 ± 0.26 4.1


ALMA1 15.5040 -0.4184 0.99 0.73 47.2 0.85 16.62 ± 1.41 0.43 ± 0.009 7.9 ± 0.17 11.7

ALMA2 15.5014 -0.4190 0.51 0.44 179.1 0.48 1.44 ± 0.28 0.073 ± 0.009 1.4 ± 0.16 5.1

ALMA3 15.5033 -0.4179 0.48 0.22 58.3 0.32 0.54 ± 0.14 0.041 ± 0.009 0.76 ± 0.17 4.0


ALMA1 22.5327 -0.1928 1.03 0.54 61.8 0.74 15.97 ± 1.02 0.34 ± 0.010 5.8 ± 0.18 15.7

ALMA2 22.5284 -0.1931 0.66 0.55 171.6 0.60 3.46 ± 0.65 0.12 ± 0.012 2.0 ± 0.20 5.3

ALMA3 22.5315 -0.1921 0.46 0.35 83.3 0.40 2.14 ± 0.24 0.13 ± 0.009 2.2 ± 0.16 9.0

ALMA4 22.5318 -0.1928 0.54 0.19 -147.0 0.32 1.24 ± 0.14 0.094 ± 0.009 1.6 ± 0.16 8.8

ALMA5 22.5305 -0.1942 0.70 0.26 58.4 0.43 0.99 ± 0.26 0.046 ± 0.010 0.77 ± 0.17 3.8

ALMA6 22.5333 -0.1929 0.23 0.21 -178.6 0.22 0.77 ± 0.08 0.12 ± 0.012 2.0 ± 0.20 9.1

ALMA7 22.5296 -0.1906 0.38 0.30 -149.6 0.34 0.73 ± 0.20 0.055 ± 0.012 0.93 ± 0.20 3.7

ALMA8 22.5307 -0.1924 0.47 0.23 -144.1 0.33 0.70 ± 0.12 0.058 ± 0.009 0.98 ± 0.15 5.6

ALMA9 22.5302 -0.1919 0.40 0.30 75.1 0.35 0.69 ± 0.17 0.049 ± 0.009 0.83 ± 0.16 4.2


ALMA1 18.8000 -0.2954 1.18 0.87 158.2 1.01 9.62 ± 1.63 0.14 ± 0.010 2.7 ± 0.19 5.9

ALMA2 18.8008 -0.2971 0.79 0.68 100.1 0.73 6.43 ± 0.78 0.19 ± 0.008 3.7 ± 0.15 8.2

ALMA3 18.8025 -0.2989 0.53 0.39 -164.5 0.45 1.56 ± 0.32 0.074 ± 0.010 1.4 ± 0.19 4.9

ALMA4 18.8022 -0.2982 0.51 0.38 -150.5 0.44 1.44 ± 0.28 0.073 ± 0.009 1.4 ± 0.17 5.1

ALMA5 18.7989 -0.2967 1.25 0.43 95.1 0.73 1.25 ± 0.36 0.038 ± 0.009 0.74 ± 0.18 3.5

ALMA6 18.7992 -0.2943 0.49 0.28 112.4 0.37 1.24 ± 0.30 0.075 ± 0.014 1.5 ± 0.28 4.1

ALMA7 18.7988 -0.2941 0.40 0.21 115.1 0.29 0.80 ± 0.22 0.076 ± 0.017 1.5 ± 0.32 3.7

ALMA8 18.8018 -0.2962 0.51 0.23 128.0 0.34 0.47 ± 0.13 0.041 ± 0.009 0.79 ± 0.17 3.6


ALMA1 -26.9824 -0.7504 1.20 0.53 57.1 0.80 4.23 ± 0.64 0.07 ± 0.008 1.9 ± 0.22 6.6

ALMA2 -26.9834 -0.7510 0.82 0.53 83.4 0.66 2.01 ± 0.47 0.051 ± 0.008 1.4 ± 0.20 4.3

ALMA3 -26.9861 -0.7511 0.92 0.52 76.1 0.69 1.98 ± 0.54 0.054 ± 0.010 1.5 ± 0.27 3.7

ALMA4 -26.9834 -0.7493 0.86 0.31 60.0 0.52 1.66 ± 0.27 0.064 ± 0.008 1.7 ± 0.22 6.3

ALMA5 -26.9838 -0.7502 0.47 0.38 147.8 0.42 1.09 ± 0.19 0.053 ± 0.008 1.4 ± 0.20 5.8

ALMA6 -26.9829 -0.7489 0.45 0.37 170.8 0.41 1.08 ± 0.22 0.054 ± 0.009 1.4 ± 0.24 4.8

ALMA7 -26.9831 -0.7522 0.66 0.45 48.0 0.55 1.07 ± 0.30 0.037 ± 0.008 0.98 ± 0.22 3.6

ALMA8 -26.9821 -0.7515 0.54 0.37 115.6 0.45 1.01 ± 0.23 0.046 ± 0.008 1.2 ± 0.23 4.4


ALMA1 29.5567 0.1826 0.83 0.61 62.7 0.71 15.34 ± 1.65 0.49 ± 0.015 8.9 ± 0.27 9.3

ALMA2 29.5590 0.1847 0.84 0.50 50.4 0.65 11.48 ± 1.26 0.36 ± 0.016 6.5 ± 0.29 9.1

ALMA3 29.5597 0.1839 0.77 0.32 47.7 0.50 6.13 ± 0.92 0.25 ± 0.024 4.5 ± 0.43 6.6

ALMA4 29.5575 0.1870 0.69 0.48 152.9 0.57 3.91 ± 0.58 0.13 ± 0.011 2.3 ± 0.20 6.8

ALMA5 29.5580 0.1856 0.56 0.30 89.8 0.41 0.97 ± 0.25 0.053 ± 0.011 0.96 ± 0.21 3.9

ALMA6 29.5581 0.1872 0.33 0.29 135.1 0.31 0.94 ± 0.18 0.078 ± 0.013 1.4 ± 0.24 5.1

ALMA7 29.5580 0.1850 0.38 0.30 165.0 0.34 0.71 ± 0.20 0.049 ± 0.012 0.88 ± 0.21 3.5



_(a)_ Cores are ranked with their mass, e.g., ALMA1 is the most massive core while ALMA2 is the second massive core.
_(b)_ Major, minor semi-axes, and equivalent radius, respectively.
_(c)(d)_ Primary beam corrected integrated flux and its error. Primary beam corrected pixel maximum flux and its error. The units are mJy and mJy Beam −1 for _F_ 1 [p] [and] _[ F]_ 2 [p] [, respectively.]



Article number, page 27 of 30

_A&A proofs:_ manuscript no. hmsc


**Table A.2.** Physical parameters of cores.


Clump Core _M_ core _[(]_ [α] _[)]_ _M_ core [cold] _(_ β _)_ _M_ core [warm] _(_ β _)_ _r_ _[(]_ [γ] _[)]_ Σ _N_ H 2 _n_ H 2
(M ⊙ ) (M ⊙ ) (M ⊙ ) (AU) (g cm [−][2] ) (10 [23] cm [−][2] ) (10 [6] cm [−][3] )



AGAL010.214-00.306
(AS1, _T_ dust = 16.6 K)


AGAL009.951-00.366
(NA1, _T_ dust = 12.0 K)


AGAL018.931-00.029
(AS2, _T_ dust = 18.2 K)


AGAL015.503-00.419
(NA2, _T_ dust = 14.0 K)


AGAL022.531-00.192
(AS3, _T_ dust = 12.4 K)


AGAL018.801-00.297
(NA3, _T_ dust = 12.3 K)


AGAL333.016-00.751
(AS4, _T_ dust = 15.6 K)


AGAL029.556+00.186
(NA4, _T_ dust = 12.8 K)



ALMA1 14.1 ± 5.4 18.6 ± 7.2 11.3 ± 4.3 3940 2.57 ± 0.92 5.47 ± 1.96 6.96 ± 2.54

ALMA2 12.0 ± 4.5 15.8 ± 6.0 9.6 ± 3.6 3700 2.51 ± 0.89 5.35 ± 1.89 7.30 ± 2.63

ALMA3 10.9 ± 4.5 14.4 ± 6.0 8.7 ± 3.6 4400 1.58 ± 0.63 3.38 ± 1.33 3.85 ± 1.54


ALMA1 2.2 ± 0.9 3.6 ± 1.4 1.6 ± 0.7 2800 0.81 ± 0.31 1.73 ± 0.66 3.10 ± 1.19

ALMA2 1.8 ± 0.8 2.9 ± 1.2 1.3 ± 0.6 2600 0.77 ± 0.30 1.65 ± 0.65 3.22 ± 1.29

ALMA3 0.6 ± 0.3 1.0 ± 0.4 0.4 ± 0.2 1700 0.62 ± 0.26 1.32 ± 0.55 3.97 ± 1.68

ALMA4 0.4 ± 0.2 0.7 ± 0.3 0.3 ± 0.1 1100 1.07 ± 0.46 2.28 ± 0.97 10.58 ± 4.58


ALMA1 2.6 ± 0.9 3.3 ± 1.2 2.1 ± 0.8 2000 1.78 ± 0.62 3.80 ± 1.33 9.48 ± 3.36

ALMA2 1.8 ± 0.7 2.3 ± 0.9 1.5 ± 0.6 2700 0.73 ± 0.28 1.56 ± 0.61 2.94 ± 1.16

ALMA3 0.6 ± 0.2 0.7 ± 0.3 0.5 ± 0.2 1000 1.53 ± 0.55 3.26 ± 1.16 15.98 ± 5.77

ALMA4 0.5 ± 0.2 0.7 ± 0.3 0.4 ± 0.2 1500 0.64 ± 0.25 1.36 ± 0.54 4.46 ± 1.77

ALMA5 0.5 ± 0.2 0.7 ± 0.3 0.4 ± 0.2 1700 0.50 ± 0.19 1.06 ± 0.40 3.13 ± 1.20

ALMA6 0.4 ± 0.2 0.6 ± 0.2 0.4 ± 0.2 1400 0.59 ± 0.25 1.25 ± 0.52 4.34 ± 1.83

ALMA7 0.4 ± 0.2 0.5 ± 0.2 0.3 ± 0.1 1500 0.48 ± 0.19 1.02 ± 0.40 3.45 ± 1.36

ALMA8 0.2 ± 0.1 0.3 ± 0.1 0.2 ± 0.1 1000 0.64 ± 0.28 1.37 ± 0.59 6.64 ± 2.87

ALMA9 0.2 ± 0.1 0.2 ± 0.1 0.2 ± 0.1 900 0.64 ± 0.26 1.36 ± 0.55 7.70 ± 3.11


ALMA1 6.0 ± 2.5 8.7 ± 3.6 4.6 ± 1.9 2700 2.38 ± 0.79 5.08 ± 1.68 9.53 ± 3.36

ALMA2 0.5 ± 0.2 0.8 ± 0.3 0.4 ± 0.2 1500 0.66 ± 0.25 1.40 ± 0.53 4.69 ± 1.85

ALMA3 0.2 ± 0.1 0.3 ± 0.1 0.2 ± 0.1 1000 0.53 ± 0.22 1.13 ± 0.46 5.57 ± 2.37


ALMA1 17.9 ± 7.1 27.7 ± 11 13.1 ± 5.2 3700 3.60 ± 1.17 7.67 ± 2.50 10.26 ± 3.54

ALMA2 3.9 ± 1.7 6.0 ± 2.6 2.8 ± 1.2 3000 1.20 ± 0.44 2.55 ± 0.95 4.22 ± 1.64

ALMA3 2.4 ± 1.0 3.7 ± 1.5 1.8 ± 0.7 2000 1.67 ± 0.56 3.55 ± 1.20 8.83 ± 3.16

ALMA4 1.4 ± 0.6 2.2 ± 0.9 1.0 ± 0.4 1600 1.53 ± 0.52 3.27 ± 1.11 10.25 ± 3.67

ALMA5 1.1 ± 0.5 1.7 ± 0.8 0.8 ± 0.4 2100 0.68 ± 0.28 1.45 ± 0.60 3.38 ± 1.45

ALMA6 0.9 ± 0.4 1.3 ± 0.5 0.6 ± 0.3 1100 2.06 ± 0.70 4.40 ± 1.49 20.35 ± 7.26

ALMA7 0.8 ± 0.4 1.3 ± 0.6 0.6 ± 0.3 1700 0.79 ± 0.33 1.69 ± 0.71 4.95 ± 2.14

ALMA8 0.8 ± 0.3 1.2 ± 0.5 0.6 ± 0.3 1700 0.80 ± 0.29 1.70 ± 0.62 5.10 ± 1.95

ALMA9 0.8 ± 0.4 1.2 ± 0.6 0.6 ± 0.3 1700 0.72 ± 0.29 1.53 ± 0.61 4.41 ± 1.84


ALMA1 10.3 ± 4.0 16.1 ± 6.2 7.5 ± 2.9 5000 1.19 ± 0.43 2.53 ± 0.92 2.56 ± 0.94

ALMA2 6.9 ± 2.5 10.7 ± 3.9 5.0 ± 1.8 3600 1.52 ± 0.52 3.25 ± 1.11 4.55 ± 1.58

ALMA3 1.7 ± 0.7 2.6 ± 1.0 1.2 ± 0.5 2200 0.95 ± 0.36 2.03 ± 0.77 4.57 ± 1.76

ALMA4 1.5 ± 0.6 2.4 ± 1.0 1.1 ± 0.5 2100 0.95 ± 0.36 2.02 ± 0.76 4.71 ± 1.79

ALMA5 1.3 ± 0.6 2.1 ± 0.9 1.0 ± 0.4 3600 0.30 ± 0.13 0.63 ± 0.27 0.88 ± 0.38

ALMA6 1.3 ± 0.6 2.1 ± 0.9 1.0 ± 0.4 1800 1.13 ± 0.45 2.40 ± 0.97 6.60 ± 2.68

ALMA7 0.9 ± 0.4 1.3 ± 0.6 0.6 ± 0.3 1400 1.18 ± 0.50 2.53 ± 1.06 8.84 ± 3.74

ALMA8 0.5 ± 0.2 0.8 ± 0.4 0.4 ± 0.2 1700 0.50 ± 0.21 1.06 ± 0.45 3.17 ± 1.36


ALMA1 1.6 ± 0.7 2.1 ± 0.9 1.2 ± 0.5 2700 0.59 ± 0.21 1.27 ± 0.45 2.35 ± 0.88

ALMA2 0.7 ± 0.3 1.0 ± 0.5 0.6 ± 0.3 2200 0.42 ± 0.16 0.89 ± 0.35 1.98 ± 0.82

ALMA3 0.7 ± 0.3 1.0 ± 0.4 0.6 ± 0.3 2400 0.37 ± 0.16 0.79 ± 0.33 1.68 ± 0.73

ALMA4 0.6 ± 0.3 0.8 ± 0.4 0.5 ± 0.2 1800 0.55 ± 0.20 1.18 ± 0.42 3.36 ± 1.27

ALMA5 0.4 ± 0.2 0.5 ± 0.2 0.3 ± 0.1 1400 0.55 ± 0.20 1.17 ± 0.42 4.06 ± 1.56

ALMA6 0.4 ± 0.2 0.5 ± 0.2 0.3 ± 0.1 1400 0.58 ± 0.22 1.24 ± 0.47 4.47 ± 1.79

ALMA7 0.4 ± 0.2 0.5 ± 0.3 0.3 ± 0.2 1900 0.32 ± 0.14 0.68 ± 0.29 1.84 ± 0.81

ALMA8 0.4 ± 0.2 0.5 ± 0.2 0.3 ± 0.1 1500 0.45 ± 0.18 0.96 ± 0.38 3.18 ± 1.31


ALMA1 13.1 ± 4.7 19.8 ± 7.2 9.7 ± 3.5 3200 3.60 ± 1.21 7.67 ± 2.59 12.01 ± 4.13

ALMA2 9.8 ± 3.6 14.8 ± 5.4 7.2 ± 2.6 2900 3.24 ± 1.10 6.91 ± 2.34 11.87 ± 4.09

ALMA3 5.2 ± 2.0 7.9 ± 3.0 3.9 ± 1.5 2200 2.97 ± 1.05 6.34 ± 2.24 14.25 ± 5.13

ALMA4 3.3 ± 1.3 5.1 ± 1.9 2.5 ± 0.9 2600 1.42 ± 0.50 3.03 ± 1.07 5.91 ± 2.12

ALMA5 0.8 ± 0.4 1.3 ± 0.5 0.6 ± 0.3 1800 0.69 ± 0.29 1.48 ± 0.61 4.06 ± 1.69

ALMA6 0.8 ± 0.3 1.2 ± 0.5 0.6 ± 0.2 1400 1.17 ± 0.44 2.50 ± 0.93 9.00 ± 3.42

ALMA7 0.6 ± 0.3 0.9 ± 0.4 0.4 ± 0.2 1500 0.74 ± 0.32 1.59 ± 0.68 5.27 ± 2.27



_(_ α _)_ Core mass and its error at clump dust temperature _T_ dust .
_(_ β _)_ Warm ( _T_ dust +3 K) and cold ( _T_ dust −3 K) core masses and their errors.
_(_ γ _)_ Core radius.


Article number, page 28 of 30

S. Zhang et al.: H ii regions and high-mass starless clump candidates




|Col1|Col2|
|---|---|
|0.3 pc<br>1<br>2<br>3<br>4|0.3 pc<br>1<br>2<br>3<br>4|


|Col1|Col2|
|---|---|
||0.3 pc<br>_−_2<br>0<br>2<br>4<br>6|



























**Fig.** **A.3.** 7 m ACA continuum images uncorrected for primary beam. ATLASGAL 870 µm emission is shown with black contours
with levels the same as Fig. 1. Red (positive) and green (negative) contours show the 7 m ACA emission with levels of ±rms ×

[3, 3 [1][.][25], 3 [1][.][50], 3 [1][.][75], 3 [2][.][0], 3 [2][.][25], 3 [2][.][50], 3 [2][.][75], 3 [3][.][0] ]. Blue ellipses and orange contours indicate the leaves and their pixels derived by Astrodendro, respectively. The red numbers mark the ranking of leaves’ mass in Table A.3.


**Table A.3.** Astrodendrogram results for 7 m ACA images.


Clump Leaves _[(]_ [α] _[)]_ _l_ _b_ major _[(]_ [β] _[)]_ minor _[(]_ [β] _[)]_ PA _R_ _[(]_ [β] _[)]_ _F_ _[(]_ [γ] _[)]_ _F_ _[p(]_ [γ] _[)]_ S/N _r_ _[(]_ [β] _[)]_ _M_ _M_ [cold] _M_ [warm]
( [◦] ) ( [◦] ) ( [′′] ) ( [′′] ) ( [◦] ) ( [′′] ) (mJy) (mJy) pc M ⊙ M ⊙ M ⊙
AS1 ACA1 10.2151 -0.3053 1.47 1.10 58.2 1.27 26.08 ± 1.44 1.4 ± 0.068 18.2 0.02 7.4 ± 2.6 9.8 5.9

AS1 ACA2 10.2135 -0.3049 1.39 0.99 72.1 1.17 23.49 ± 1.25 1.5 ± 0.069 18.8 0.02 6.6 ± 2.3 8.8 5.3

NA1 ACA1 9.9499 -0.3669 2.55 1.52 -167.4 1.97 8.55 ± 1.76 0.24 ± 0.033 4.9 0.03 3.9 ± 1.6 6.1 2.8

NA1 ACA2 9.9525 -0.3661 2.34 1.41 -178.1 1.81 6.91 ± 1.54 0.22 ± 0.033 4.5 0.03 3.1 ± 1.3 4.9 2.2

NA1 ACA3 9.9566 -0.3638 1.48 1.05 -144.5 1.24 4.21 ± 1.28 0.26 ± 0.061 3.3 0.02 1.9 ± 0.9 3.0 1.4

NA1 ACA4 9.9485 -0.3629 1.47 1.01 51.0 1.22 2.67 ± 0.83 0.17 ± 0.041 3.2 0.02 1.2 ± 0.6 1.9 0.9

AS2 ACA1 18.9316 -0.0247 3.04 1.72 -166.4 2.29 25.95 ± 5.73 0.58 ± 0.073 4.5 0.04 7.3 ± 2.9 9.3 6.0

AS2 ACA2 18.9286 -0.0320 2.55 1.98 176.8 2.25 16.47 ± 4.31 0.36 ± 0.062 3.8 0.04 4.6 ± 2.0 5.9 3.8

AS2 ACA3 18.9338 -0.0295 3.13 1.06 -159.4 1.82 7.07 ± 2.34 0.2 ± 0.057 3.0 0.03 2.0 ± 0.9 2.5 1.6

NA2 ACA1 15.5041 -0.4182 2.69 2.23 -157.7 2.45 21.86 ± 3.45 0.58 ± 0.038 6.3 0.04 7.9 ± 3.4 11.4 6.1

NA2 ACA2 15.4999 -0.4242 1.82 1.09 157.0 1.41 5.13 ± 1.66 0.23 ± 0.061 3.1 0.02 1.9 ± 1.0 2.7 1.4

AS3 ACA1 22.5322 -0.1926 4.93 1.74 -142.6 2.93 38.95 ± 6.26 0.66 ± 0.046 6.2 0.07 43.6 ± 18.5 67.6 31.9

AS3 ACA2 22.5295 -0.1936 3.20 1.29 -143.0 2.03 7.87 ± 2.26 0.22 ± 0.046 3.5 0.05 8.8 ± 4.3 13.7 6.4

NA3 ACA1 18.8052 -0.3043 2.00 1.80 52.4 1.90 28.99 ± 5.83 0.99 ± 0.11 5.0 0.05 31.0 ± 12.4 48.4 22.6

NA3 ACA2 18.8004 -0.2961 4.63 1.82 49.2 2.90 22.22 ± 4.85 0.3 ± 0.038 4.6 0.07 23.8 ± 9.7 37.1 17.3

AS4 ACA1 -26.9832 -0.7496 4.30 2.67 -137.0 3.39 27.63 ± 5.36 0.27 ± 0.033 5.2 0.06 10.1 ± 4.5 13.7 8.0

NA4 ACA1 29.5586 0.1853 5.42 1.59 55.4 2.94 32.93 ± 5.41 0.48 ± 0.041 6.1 0.06 28.0 ± 10.7 42.5 20.7

NA4 ACA2 29.5566 0.1827 3.18 1.53 59.0 2.20 18.43 ± 3.19 0.47 ± 0.04 5.8 0.05 15.7 ± 6.1 23.8 11.6


_(_ α _)_ Leaves are ranked with their mass, e.g., ACA1 is the most massive leaf while ACA2 is the second massive leaf.
_((_ βγ _))_ Major, minor semi-axes, and equivalent radius, respectively. _F_ is the primary beam corrected integrated flux. _F_ _p_ is the primary beam corrected pixel maximum flux. The unit has been transformed from mJy Beam −1
to mJy by dividing the flux in the unit of mJy Beam [−][1] with the beam size in the unit of pixel.


Article number, page 29 of 30

_A&A proofs:_ manuscript no. hmsc














|−0◦11′12′′<br>24′′<br>Latitude<br>36′′ Galactic<br>48′′<br>12′00′′<br>12′′ 32′00′′<br>Galacti<br>−0◦44′36′′<br>48′′<br>Latitude<br>45′00′′<br>Galactic<br>12′′<br>24′′<br>333◦01′24′′ 12′′ 0<br>Galacti|−0◦17′24′′<br>20<br>36′′ 8<br>15 6<br>Beam−1)<br>10 48′′ 4<br>2 (mJy<br>5 Flux<br>18′00′′ 0<br>0 −2<br>12′′ −4<br>0 .3 pc 0 .3 pc<br>48′′ 36′′ 22◦31′24′′ 24′′ 12′′ 48′00′′ 48′′ 18◦47′36′′<br>c Longitude Galactic Longitude<br>36′′<br>8<br>125<br>.<br>24′′<br>6 100<br>.<br>Beam−1)<br>75<br>4 .<br>12′′<br>50<br>. 2 (mJy<br>25<br>. Flux<br>0 11′00′′<br>00<br>.<br>−2 −2 .5<br>48′′ −5 .0<br>0 .3 pc 0 .3 pc<br>+0◦10′36′′<br>0′′ 00′48′′ 36′′ 48′′ 36′′ 24′′ 12′′ 29◦33′00′′<br>c Longitude Galactic Longitude|Col3|Col4|
|---|---|---|---|
|32_′_00_′′_<br>12_′′_<br>Galacti<br>12_′_00_′′_<br>48_′′_<br>36_′′_<br>24_′′_<br>_−_0_◦_11_′_12_′′_<br>Galactic Latitude<br>0<br>12_′′_<br>333_◦_01_′_24_′′_<br>Galacti<br>24_′′_<br>12_′′_<br>45_′_00_′′_<br>48_′′_<br>_−_0_◦_44_′_36_′′_<br>Galactic Latitude|22_◦_31_′_24_′′_<br>36_′′_<br>48_′′_<br>c Longitude<br>0.3 pc<br>18_◦_47_′_36_′′_<br>48_′′_<br>48_′_00_′′_<br>12_′′_<br>24_′′_<br>Galactic Longitude<br>12_′′_<br>18_′_00_′′_<br>48_′′_<br>36_′′_<br>_−_0_◦_17_′_24_′′_<br>0.3 pc<br>36_′′_<br>00_′_48_′′_<br>0_′′_<br>c Longitude<br>0.3 pc<br>29_◦_33_′_00_′′_<br>12_′′_<br>24_′′_<br>36_′′_<br>48_′′_<br>Galactic Longitude<br>+0_◦_10_′_36_′′_<br>48_′′_<br>11_′_00_′′_<br>12_′′_<br>24_′′_<br>36_′′_<br>0.3 pc<br>0<br>5<br>10<br>15<br>20<br>Flux (mJy Beam_−_1)<br>_−_4<br>_−_2<br>0<br>2<br>4<br>6<br>8<br><br>_−_2<br>0<br>2<br>4<br>6<br>8<br>Flux (mJy Beam_−_1)<br>_−_5_._0<br>_−_2_._5<br>0_._0<br>2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>|_−_4<br>_−_2<br>0<br>2<br>4<br>6<br>8<br>|_−_4<br>_−_2<br>0<br>2<br>4<br>6<br>8<br>|
|32_′_00_′′_<br>12_′′_<br>Galacti<br>12_′_00_′′_<br>48_′′_<br>36_′′_<br>24_′′_<br>_−_0_◦_11_′_12_′′_<br>Galactic Latitude<br>0<br>12_′′_<br>333_◦_01_′_24_′′_<br>Galacti<br>24_′′_<br>12_′′_<br>45_′_00_′′_<br>48_′′_<br>_−_0_◦_44_′_36_′′_<br>Galactic Latitude|22_◦_31_′_24_′′_<br>36_′′_<br>48_′′_<br>c Longitude<br>0.3 pc<br>18_◦_47_′_36_′′_<br>48_′′_<br>48_′_00_′′_<br>12_′′_<br>24_′′_<br>Galactic Longitude<br>12_′′_<br>18_′_00_′′_<br>48_′′_<br>36_′′_<br>_−_0_◦_17_′_24_′′_<br>0.3 pc<br>36_′′_<br>00_′_48_′′_<br>0_′′_<br>c Longitude<br>0.3 pc<br>29_◦_33_′_00_′′_<br>12_′′_<br>24_′′_<br>36_′′_<br>48_′′_<br>Galactic Longitude<br>+0_◦_10_′_36_′′_<br>48_′′_<br>11_′_00_′′_<br>12_′′_<br>24_′′_<br>36_′′_<br>0.3 pc<br>0<br>5<br>10<br>15<br>20<br>Flux (mJy Beam_−_1)<br>_−_4<br>_−_2<br>0<br>2<br>4<br>6<br>8<br><br>_−_2<br>0<br>2<br>4<br>6<br>8<br>Flux (mJy Beam_−_1)<br>_−_5_._0<br>_−_2_._5<br>0_._0<br>2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>|_−_4<br>_−_2<br>0<br>2<br>4<br>6<br>8<br>|18_◦_47_′_36_′′_<br>48_′′_<br>48_′_00_′′_<br>actic Longitude<br>0.3 pc|
|32_′_00_′′_<br>12_′′_<br>Galacti<br>12_′_00_′′_<br>48_′′_<br>36_′′_<br>24_′′_<br>_−_0_◦_11_′_12_′′_<br>Galactic Latitude<br>0<br>12_′′_<br>333_◦_01_′_24_′′_<br>Galacti<br>24_′′_<br>12_′′_<br>45_′_00_′′_<br>48_′′_<br>_−_0_◦_44_′_36_′′_<br>Galactic Latitude|22_◦_31_′_24_′′_<br>36_′′_<br>48_′′_<br>c Longitude<br>0.3 pc<br>18_◦_47_′_36_′′_<br>48_′′_<br>48_′_00_′′_<br>12_′′_<br>24_′′_<br>Galactic Longitude<br>12_′′_<br>18_′_00_′′_<br>48_′′_<br>36_′′_<br>_−_0_◦_17_′_24_′′_<br>0.3 pc<br>36_′′_<br>00_′_48_′′_<br>0_′′_<br>c Longitude<br>0.3 pc<br>29_◦_33_′_00_′′_<br>12_′′_<br>24_′′_<br>36_′′_<br>48_′′_<br>Galactic Longitude<br>+0_◦_10_′_36_′′_<br>48_′′_<br>11_′_00_′′_<br>12_′′_<br>24_′′_<br>36_′′_<br>0.3 pc<br>0<br>5<br>10<br>15<br>20<br>Flux (mJy Beam_−_1)<br>_−_4<br>_−_2<br>0<br>2<br>4<br>6<br>8<br><br>_−_2<br>0<br>2<br>4<br>6<br>8<br>Flux (mJy Beam_−_1)<br>_−_5_._0<br>_−_2_._5<br>0_._0<br>2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>|0.3 pc<br>_−_5_._0<br>_−_2_._5<br>0_._0<br>2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>|0.3 pc<br>_−_5_._0<br>_−_2_._5<br>0_._0<br>2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>|



**Fig. A.4.** 7 m ACA continuum images uncorrected for primary beam. The meanings of lines and marks are similar to Fig. A.3 but for another four
candidate HMSCs.


Article number, page 30 of 30


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: archival_reuse",
  "failed_quote": "We made use of the ALMA data observed in ALMA Cycle 4 by project 2016.1.01346.S (PI: Thushara Pillai, project title: Galactic census of all massive starless cores within 5 kpc)."
 },
 {
  "path": "data.alma_project_codes[0].evidence[0]",
  "value": "2016.1.01346.S",
  "failed_quote": "We made use of the ALMA data observed in ALMA Cycle 4 by project 2016.1.01346.S (PI: Thushara Pillai, project title: Galactic census of all massive starless cores within 5 kpc)."
 },
 {
  "path": "data.alma_project_codes[0].evidence[1]",
  "value": "2016.1.01346.S",
  "failed_quote": "We made use of the ALMA band 6 data (225 GHz, equal to 1.33 mm) of 12 m main array and 7 m Atacama Compact Array (ACA) in the ALMA Cycle 4 project 2016.1.01346.S."
 },
 {
  "path": "data.bands.evidence[0]",
  "value": "Band 6 (1.33 mm, 225 GHz)",
  "failed_quote": "We made use of the ALMA band 6 data (225 GHz, equal to 1.33 mm) of 12 m main array and 7 m Atacama Compact Array (ACA) in the ALMA Cycle 4 project 2016.1.01346.S."
 },
 {
  "path": "data.arrays.evidence[0]",
  "value": "12 m main array and 7 m ACA",
  "failed_quote": "We made use of the ALMA band 6 data (225 GHz, equal to 1.33 mm) of 12 m main array and 7 m Atacama Compact Array (ACA) in the ALMA Cycle 4 project 2016.1.01346.S."
 },
 {
  "path": "data.pi_or_archival_as_stated.evidence[0]",
  "value": "Archival public data (PI: Thushara Pillai)",
  "failed_quote": "We made use of the ALMA data observed in ALMA Cycle 4 by project 2016.1.01346.S (PI: Thushara Pillai, project title: Galactic census of all massive starless cores within 5 kpc)."
 },
 {
  "path": "data.other_facilities[7].provided.evidence[0]",
  "value": "Parallax distance to OB star BD-15 4928",
  "failed_quote": "Furthermore, the associated exciting OB star BD 15 4928 has a Gaia parallax distance of 1.6 kpc (0.6148 mas, Gaia Collaboration et al. 2018)."
 },
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "24 um and 70 um point source fluxes and FWHMs toward AS3",
  "failed_quote": "ALMA1 ( M core / M J th,clump ∼ 6) is probably associated with an IR source at 24 µm (20.984 mJy, FWHM≃ 6.24 ′′, Gutermuth & Heyer 2015) and 70 µm (278 mJy, FWHM≃10.1 ′′, Molinari et al. 2016)"
 },
 {
  "path": "processing.calibration.pipeline_or_manual.evidence[0]",
  "value": "QA2 pipeline calibration followed by manual concatenation and imaging",
  "failed_quote": "The data reductions were conducted using the same versions of Common Astronomy Software Applications (CASA, McMullin et al. 2007) as those used in the QA2 pipeline products ."
 },
 {
  "path": "processing.calibration.casa_version.evidence[0]",
  "value": "Same versions as those used in the QA2 pipeline products (specific version numbers not stated)",
  "failed_quote": "The data reductions were conducted using the same versions of Common Astronomy Software Applications (CASA, McMullin et al. 2007) as those used in the QA2 pipeline products ."
 },
 {
  "path": "processing.imaging.deconvolver.evidence[0]",
  "value": "multi-term (multi-scale) multi-frequency synthesis",
  "failed_quote": "A deconvolver using multi-term (multi-scale) multi-frequency synthesis is applied."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Run Astrodendrograms on primary beam uncorrected 7 m + 12 m combined continuum images to extract leaves as cores, and on 7 m ACA continuum images to extract larger leaves and classify candidate ensembles (splitting elongated leaves with major/minor > 2.5 by contour peaks/subpeaks and adding weak structures hosting combined cores).",
  "failed_quote": "We extracted the cores in the cleaned 7 m + 12 m combined continuum images with the technique of Astrodendrograms (Rosolowsky et al. 2008)."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Compute core and ensemble masses from primary beam corrected integrated 1.3 mm flux using optically thin isothermal dust emission equation (Eq. 1), and calculate surface density, H2 column density, and H2 number density assuming spherical geometry.",
  "failed_quote": "Assuming that the dust continuum emission is optically thin, core mass is estimated with (Hildebrand 1983): M core = R gd F ν D 2 / κ ν B ν ( T dust ) ,"
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Checked regridded ALMA spectra for star formation and warm/shocked gas tracers (SiO J=5-4, CH3OH, H2CO, c-H2COCH2) and cross-matched with 24 um/70 um catalogs to identify cores where T_dust is underestimated.",
  "failed_quote": "A check on whether massive cores show star formation signposts is beneficial to understand the overestimated mass and whether high-mass prestellar cores exist."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Calculate thermal, turbulent (total support), compressible flow, and cylindrical Jeans masses and lengths for clumps and ensembles; measure nearest neighbor separations among cores and ensembles using Minimum Spanning Tree (MST); test modality of scaled core separations combined with literature samples using Hartigan's Dip test and ACR test.",
  "failed_quote": "The typical separation and mass in the case of cylindrical thermal fragmentation is: λ th J,cylinder = 22σ th (4π G ρ c ) −1/2, M J th,cylinder = 22 π 1/2 σ G th 3 3 ρ c,"
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Calculate thermal, turbulent (total support), compressible flow, and cylindrical Jeans masses and lengths for clumps and ensembles; measure nearest neighbor separations among cores and ensembles using Minimum Spanning Tree (MST); test modality of scaled core separations combined with literature samples using Hartigan's Dip test and ACR test.",
  "failed_quote": "Firstly, the assumption of the unimodal distribution is excluded for Fig. 15, by applying Hartigan’s Dip test (Hartigan & Hartigan 1985). Then we test multimodal distributions by ACR methods (see details about ACR in Ameijeiras-Alonso et al. 2016) using the “modetest” function in the R package “multimode” ."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Statistical modality testing using Hartigan's Dip test and ACR method (modetest)",
  "failed_quote": "Firstly, the assumption of the unimodal distribution is excluded for Fig. 15, by applying Hartigan’s Dip test (Hartigan & Hartigan 1985). Then we test multimodal distributions by ACR methods (see details about ACR in Ameijeiras-Alonso et al. 2016) using the “modetest” function in the R package “multimode” ."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "Data reduction, visibility concatenation (CONCAT), and continuum imaging (TCLEAN)",
  "failed_quote": "The data reductions were conducted using the same versions of Common Astronomy Software Applications (CASA, McMullin et al. 2007) as those used in the QA2 pipeline products ."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Extracting dense cores in 7 m + 12 m combined continuum images and leaves/ensembles in 7 m ACA continuum images",
  "failed_quote": "We extracted the cores in the cleaned 7 m + 12 m combined continuum images with the technique of Astrodendrograms (Rosolowsky et al. 2008)."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Testing multimodal distributions of scaled MST core separations using the modetest function (ACR method)",
  "failed_quote": "Then we test multimodal distributions by ACR methods (see details about ACR in Ameijeiras-Alonso et al. 2016) using the “modetest” function in the R package “multimode” ."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "Fragmentation in both AS and NA candidate HMSCs is dominated by two-level hierarchical thermal Jeans fragmentation, where clumps fragment into ensembles at ~lambda_J,clump^th and ensembles sub-fragment into cores at ~0.3 lambda_J,clump^th (~1 to 1.5 lambda_J,ens^th).",
  "failed_quote": "The candidate HMSCs fragment into ensembles with separations of clump Jeans length, λ th J,clump, and then some of the ensembles continue to thermally fragment into cores with separations of about one third of the λ th J,clump ."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "Fragmentation from pc-scale clumps to ~0.025 pc cores occurs via two-level hierarchical thermal Jeans fragmentation, favouring competitive accretion over monolithic collapse.",
  "failed_quote": "As a result, the early-stage fragmentation in the high-mass clumps probably takes place in a hierarchical fashion: clumps fragment into ensembles with separations around clump thermal Jeans length, λ th J,clump, and then some of these ensembles continuously sub-fragment into cores"
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Astrodendrograms capture hierarchical structures across scales, Minimum Spanning Tree (MST) robustly detects characteristic fragmentation scales, and combining core mass and separation comparisons mitigates individual uncertainties from projection effects and core dust temperatures.",
  "failed_quote": "Astrodendrogram algorithm uses a tree diagram to describe the hierarchical structures over a range of scales."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[1]",
  "value": "Turbulent Jeans fragmentation (both total support and supersonic compressible flow models) was tested and rejected for most clumps because observed ensemble/core masses and separations are much smaller than turbulent Jeans predictions, and compressible flow Jeans lengths are too small.",
  "failed_quote": "Taking the compression of supersonic flow into account, the resulting λ com J,clump ,flow, which is even smaller than λ th J,clump, gives a more contradictory picture than the one given by the thermal fragmentation."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Unimodal distribution of scaled core separations across 31 candidate HMSCs was tested and rejected using Hartigan's Dip test and ACR multimodal testing in favor of a bimodal distribution.",
  "failed_quote": "Firstly, the assumption of the unimodal distribution is excluded for Fig. 15, by applying Hartigan’s Dip test (Hartigan & Hartigan 1985)."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[1]",
  "value": "Interferometric filtering misses 80-90% of the single-dish flux, and single-pointing observations with ~0.15 mJy Beam^-1 rms may miss outer or very low-mass cores.",
  "failed_quote": "Although some low-mass cores could be lost in our single-pointing, slightly more noisy observation, the bimodal nature of fragmentation revealed here is reliable."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Public in the ALMA Science Archive under project 2016.1.01346.S",
  "failed_quote": "We made use of the ALMA data observed in ALMA Cycle 4 by project 2016.1.01346.S (PI: Thushara Pillai, project title: Galactic census of all massive starless cores within 5 kpc)."
 }
]
```
