# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...688A...3H\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. aanda ©ESO 2024
May 6, 2024

### **High-mass star formation across the Large Magellanic Cloud**

#### **I. Chemical properties and hot molecular cores observed with ALMA at 1.2 mm**


Roya Hamedani Golshan [1,][⋆], Álvaro Sánchez-Monge [2][,][ 3], Peter Schilke [1], Marta Sewiło [4][,][ 5][,][ 6], Thomas Möller [1], V. S.
Veena [1][,][ 7] and Gary A. Fuller [1][,][ 8]


1 I. Physikalisches Institut, Universität zu Köln, Zülpicher Straße 77, 50937 Cologne, Germany
2 Institut de Ciències de l’Espai (ICE, CSIC), Carrer de Can Magrans s/n, E-08193, Bellaterra, Barcelona, Spain
3 Institut d’Estudis Espacials de Catalunya (IEEC), Barcelona, Spain
4 Exoplanets and Stellar Astrophysics Laboratory, NASA Goddard Space Flight Center, Greenbelt, MD 20771, USA
5 Center for Research and Exploration in Space Science and Technology, NASA Goddard Space Flight Center, Greenbelt, MD 20771,
USA
6 Department of Astronomy, University of Maryland, College Park, MD 20742
7 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, D-53121 Bonn, Germany
8 Jodrell Bank Centre for Astrophysics, Department of Physics & Astronomy, The University of Manchester, Oxford Road, Manchester M13 9PL, UK


**ABSTRACT**


_Context._ The formation of massive stars passes through a so-called hot molecular core phase, where the temperature of molecular gas
and dust rises to above 100 K within a size scale of approximately 0.1 pc. The hot molecular cores are rich in chemical compounds
found in the gas phase, which are a great probe of ongoing star formation.
_Aims._ To study the impact of the initial effects of metallicity (i.e., the abundance of elements heavier than helium) on star formation
and the formation of different molecular species, we searched for hot molecular cores in the sub-solar metallicity environment of the
Large Magellanic Cloud (LMC).
_Methods._ We conducted Atacama Large Millimeter/submillimeter Array (ALMA) Band 6 observations of 20 fields centered on young
stellar objects (YSOs) distributed over the LMC in order to search for hot molecular cores in this galaxy.
_Results._ We detected a total of 65 compact 1.2 mm continuum cores in the 20 ALMA fields and analyzed their spectra with XCLASS
software. The main temperature tracers are CH 3 OH and SO 2, with more than two transitions detected in the observed frequency
ranges. Other molecular lines with high detection rates in our sample are CS, SO, H [13] CO [+], H [13] CN, HC [15] N, and SiO. More complex
molecules, such as HNCO, HDCO, HC 3 N, CH 3 CN, and NH 2 CHO, and multiple transitions of SO and SO 2 isotopologues showed
tentative or definite detection toward a small subset of the cores. According to the chemical richness of the cores and high temperatures
from the XCLASS fitting, we report the detection of four hot cores and one hot core candidate. With one new hot core detection in
this study, the number of detected hot cores in the LMC increases to seven.
_Conclusions._ Six out of seven hot cores detected in the LMC to date are located in the stellar bar region of this galaxy. These six
hot cores show emission from complex organic molecules (COMs), such as CH 3 OH, CH 3 CN, CH 3 OCHO, and CH 3 OCH 3 . The only
known hot core in the LMC with no detection of COMs is located outside the bar region. The metallicity in the LMC presents a
shallow gradient increasing from outer regions toward the bar. Various studies emphasize the interaction between the LMC and the
Small Magellanic Cloud, which resulted in the mixing and inhomogeneity of the interstellar medium of the two galaxies. These
interactions triggered a new generation of star formation in the LMC. We suggest that the formation of hot molecular cores containing
COMs ensues from the new generation of stars forming in the more metal-rich environment of the LMC bar.


**Key words.** Astrochemistry, Galaxies: Magellanic Clouds, star formation, ISM: molecules, Stars: protostars, Radio lines: ISM



**1.** **Introduction**


Hot molecular cores are compact (d ≤ 0.1 pc) and dense (≥ 10 [6]
cm [−][3] ) regions that are heated up to temperatures above 100 K,
either internally or externally, in the immediate surroundings of
formation sites of massive stars (e.g. Qin et al. 2022). At these
temperatures, the molecules that are formed and developed in the
ice mantles on the surfaces of dust grains are released into the gas
due to thermal evaporation or sputtering with shock waves, UV
photons, or cosmic rays. Once in the gas phase, more complex
chemical compounds can be formed (e.g., Garrod et al. 2008).
This results in the formation and development of complex or

⋆ rhgolshan@ph1.uni-koeln.de



ganic molecules (COMs, molecules with six or more atoms including carbon; Herbst & van Dishoeck 2009). Eventually, most
complex molecules are dissociated by strong UV radiation from
the newly formed massive stellar object(s) and the associated
Hii region. In the time between the evaporation of the ice mantels to the destruction of the complex molecular species in the
gas phase, the rich molecular gas chemistry is accompanied by
the excitation of a plethora of rotational transitions observable at
(sub)millimeter wavelengths (e.g. Belloche et al. 2013; Möller
et al. 2023).


The development, chemical richness, and molecular composition of hot molecular cores may be affected by environmental
conditions. One important environmental factor is the metallic

Article number, page 1 of 90

_A&A proofs:_ manuscript no. aanda



ity of the gas where stars are forming. Metallicity is the abundance of elements heavier than helium, and it is known to increase over cosmic time with every new generation of stars due
to the nucleosynthesis processes in the stellar interiors, supernova explosions, and neutron star mergers. This triggers a fundamental question in astrochemistry regarding how the difference
in the elemental abundances influences the formation, survival,
and destruction of molecular species. To answer this question,
searching for the sites of rich chemistry in different (e.g., subsolar) metallicity conditions is a crucial step, and hot molecular
cores are prominent candidates for providing a complete molecular inventory in the gas phase. Thanks to the high sensitivity and
resolving power of the Atacama Large Millimeter/submillimeter
Array (ALMA), detecting and pinpointing massive star-forming
regions and hot molecular cores down to sub-parsec scales at
1 mm is feasible for relatively short integration times in our
Galaxy and the immediate galactic neighborhood (i.e., the Magellanic Clouds). In this work, we aim to search for and characterize hot molecular cores in the lower metallicity gas of the Large
Magellanic Cloud (LMC).
The LMC is a nearby dwarf galaxy at a distance of _D_ ≈
49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzy´nski
et al. 2019). This galaxy, with an average metallicity [1] of Z LMC ∼
0.38 Z ⊙ is one of the closest laboratories to study the physics
and chemistry of a low-metallicity environment. Low metallicity
means less dust and hence diminished shielding effects, allowing UV radiation to penetrate deeper into clouds. The UV field
strength in the LMC is ten to 100 times larger than in the Milky
Way (MW, e.g., Welty et al. 2006). As a result, the dust temperature is expected to be higher, likely affecting the development
of the more complex molecular species. Moreover, the metallicity has been found to vary across the LMC, showing a moderate
gradient that increases toward the bar region in this galaxy (e.g.,
Choudhury et al. 2021).
The development of ALMA enabled the detection of the first
hot molecular cores in the LMC in recent years. The six hot cores
detected so far (see Shimonishi et al. 2016b; Sewiło et al. 2018;
Shimonishi et al. 2020; Sewiło et al. 2022) present a picture of
a diverse chemistry. While metallicity-scaled abundances for detected COMs in four hot cores are comparable to those observed
in the Galaxy, COMs are either absent or underabundant in the
remaining two hot cores. Hot cores in the N 113 star-forming region show emission from molecules containing up to nine atoms,
with abundances that match the lower end of Galactic values after scaling for metallicity (Sewiło et al. 2018). The two bona fide
hot cores in the N 105 star-forming region (Sewiło et al. 2022)
also exhibit a rich chemistry, with abundances that follow the
trend of the ones in N 113, although with lower values. On the
COM-poor side, a hot core with CH 3 OH and CH 3 CN molecular
lines but no larger molecules has been detected by Shimonishi
et al. (2020). This hot core, which shows an underabundance of
complex species compared to Galactic hot cores, is associated
with the massive young stellar object (YSO) ST16. Even more
extreme is the hot core associated with the YSO ST11 (Shimonishi et al. 2016b). There are no emission lines from COMs in this
source, and the temperature above 100 K is obtained from SO 2
and its isotopologues. Shimonishi et al. (2016b) have suggested
high dust temperatures that prohibit effective freeze-out and sub

1 Different works have estimated the metallicity of the LMC to be between 0.3 and 0.5 of the metallicity in the Solar neighborhood interstellar gas (Z ⊙ ). In this work, we use the recent estimate by Choudhury
et al. (2021), who derives [Fe/H] = −0.42 dex, with [Fe/H] = log � _ZZ_ g⊙al �),
and results in Z LMC ∼ 0.38 Z ⊙ .


Article number, page 2 of 90



sequent hydrogenation of CO on the dust surface to be the likely
cause of the suppression of CH 3 OH formation, the building
block for more complex COMs (e.g. Garrod et al. 2008). The
existence of hot cores with metallicity-scaled COM abundances
similar to the Galactic values shows that higher dust temperatures in the cold collapse phase are not ubiquitous in the LMC
and may exist only in specific regions. Based on these results,
a statistically significant sample needs to be analyzed to better
characterize the hot cores in the LMC and their relation to environmental conditions (e.g., proximity to star-forming regions
having higher UV radiation levels or variations in metallicity).
To expand the search for hot molecular cores from the LMC
to other sub-solar metallicity environments, recent works have
studied objects in the outer regions of the MW (e.g. Shimonishi
et al. 2021; Fontani et al. 2022) as well as in the Small Magellanic Cloud (SMC Shimonishi et al. 2023). The Galaxy’s outer
regions harbor an interstellar medium with a diminished metallicity compared to the inner Galactic regions (e.g., ArellanoCórdova et al. 2021) as well as more quiescent radiation fields.
Studies in the outer Galaxy are crucial, as they can bridge
our knowledge of the higher metallicity (and more active) starforming environment of the inner Galaxy to the low metallicities
of the LMC and SMC. Recently, a hot molecular core has been
discovered in the outskirts of the MW in the WB 89−789 starforming region at a distance of 10.7 kpc (galactocentric distance
of 19 kpc) (Shimonishi et al. 2021). The metallicity at this position is estimated to be Z ∼ 0.25 Z ⊙ . Interestingly, the chemical
composition of the hot core in WB 89−789 resembles that of hot
cores in the inner Galactic regions and not of those in the LMC.
On the other hand, the SMC is a star-forming dwarf galaxy at a
distance of 62.1 ± 1.9 kpc (Graczyk et al. 2014) and has the lowest metallicity in the nearby universe where we are able to search
for hot cores with currently available facilities. The metallicity is
Z ∼ 0.2 Z ⊙, with a shallow but significant gradient (Choudhury
et al. 2018). Shimonishi et al. (2023) have reported the detection
of two hot cores in the SMC, S07 and S09, coinciding with the
position of two massive YSOs. Notably, SO 2 traces the hot compact (∼ 0.1 pc) component with temperatures higher than 100 K
in these two hot cores, while CH 3 OH is extended (∼ 0.2–0.3 pc)
and much cooler (≤ 40 K for S07).
In summary, the detection of hot cores in the LMC, the SMC,
and the outskirts of the MW, added to the multiple Galactic examples, suggests that the development of hot molecular cores is
common during the formation of stars in the Z = 0.2–1 Z ⊙ metallicity range (Shimonishi et al. 2023). Despite this, the first studies in low-metallicity environments have found a diverse population of objects with molecular abundances sometimes consistent with Galactic-like metallicity environments and others with
lower abundances. Furthermore, some hot cores appear to be
poor in COMs abundance, while others have abundances similar to those in the MW disk. All in all, it is noticeable that a
larger sample of sources observed and analyzed with a common
methodology is still necessary to provide insight into the formation and properties of hot cores in low-metallicity regions.
With this in mind, we studied 20 different fields in the LMC, the
largest sample to date, in order to search for hot cores and improve our current understanding of the physics and chemistry of
high-mass star-forming cores in this nearby dwarf galaxy.
This is the first paper of a series that is accompanied by
a publication by Hamedani Golshan et al. (2024, hereafter Paper II). Paper II presents the observed sample and studies the
dense cores and star-forming clusters identified in the observed
regions. In the current paper, we focus on the chemical content of the identified cores and their connection to the LMC’s

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud



Table 1: Coordinates and names of our target fields.


Field Target ID Alternative
Number (Gruendl & Chu 2009) name

1 053941.12-692916.8 ST6 _[a]_

2 045640.79-663230.5 ST10 _[a]_

3 052343.48-680033.9
4 051912.27-690907.3 ST16 _[a,b]_

5 045358.57-691106.7
6 050953.89-685336.7 N105-2 E _[c,d]_

7 052423.39-693904.7

8 044854.41-690948.3

9 054248.90-694446.3

10 051916.87-693757.5

11 045100.16-691934.4

12 050355.87-672045.1

13 053952.11-710930.7

14 052333.40-693712.2

15 051344.99-693510.6

16 054629.32-693514.2

17 054826.21-700850.2

18 045622.61-663656.9

19 045406.43-664601.4

20 052210.08-673459.6


**Notes.** [(] _[a]_ [)] Shimonishi et al. (2016a)
( _b_ ) Shimonishi et al. (2020)
( _c_ ) Sewiło et al. (2022)
( _d_ ) Henize (1956)


global metallicity trend and large-scale properties. In Section 2
we introduce the sample and the observations. In Section 3, we
present the results and main analysis procedures. We discuss the
results in the context of our knowledge about the hot cores in the
LMC, SMC, and MW in Section 4. Several appendixes show our
dataset or elaborate on specific concepts or methodologies.


**2.** **Observations and sample**


_2.1._ _Sample selection_


We selected 20 massive YSOs identified with Spitzer (e.g., Gruendl & Chu 2009) distributed throughout the LMC to be observed with ALMA (see Table 1 for their names and coordinates
and see Fig. 1 for their distribution across the LMC). We selected
YSOs without ice features or strong fine-structure lines in their
Spitzer IRS spectra (Seale et al. 2009) and with _Herschel_ counterparts at submillimeter wavelengths (Seale et al. 2014) to maximize the chance of selecting the evolutionary stage of hot cores
and not earlier or later evolutionary stages. These sources are
located away from prominent massive star-forming sites (based
on the absence of strong Hα emission in the Hα image from
the MCELS survey, Smith et al. 2000), making the cold initial
conditions (which favor methanol formation) more likely. The
selected sources are all bright at 160 µm to ensure the presence
of large amounts of dust and large column densities, favoring the
detection of molecular lines. We also added two regions centered
on the YSOs ST6 and ST10, for which Shimonishi et al. (2016a)
detected methanol ice. A more detailed description of the sample and its properties, including the continuum images and the
compact sources detected with ALMA can be found in Paper II.



_2.2._ _ALMA observations_


The sample of 20 regions (see Fig. 1) in the LMC was observed
with the ALMA 12-m Array during its Cycle 5 between November 11 and December 3, 2018 (project number 2017.1.00696.S).
The observations were carried out as single pointings centered at
the coordinates listed in Table 1 with a duration of about 19 minutes on-source per field. The observations were executed during eight different execution blocks that were later merged to
reach the requested sensitivity. We used the main array of ALMA
with the 12-m antennas in two configurations (C43-4 and C435) and baselines ranging from 15 to 1400 m, which resulted in
an angular resolution of ≈ 0 [′′] . 4 (corresponding to ∼ 0.09 pc at
the distance of the LMC) and a maximum recoverable angular
scale of ≈ 5 [′′] (corresponding to ∼ 1.2 pc at the distance of the
LMC). This maximum recoverable scale, although not enough to
map large extended structures, allowed us to detect dense cores
and clumps with typical sizes ≤ 0.5 pc. The total field of view
(or primary beam) of the ALMA observations is ∼ 44 [′′] (corresponding to ∼ 10 pc). The spectral setup (see Table 2) covered four spectral windows, including a 469 MHz-wide band
centered at 241.6 GHz and three 1875 MHz-broad bands centered at 244.6, 257.6, and 259.5 GHz. All four spectral windows
have 3840 channels, resulting in channel widths of 0.122 MHz
and 0.488 MHz, respectively. Throughout the paper, we refer to
these four spectral windows as 241, 244, 257, and 259 GHz.
The data were calibrated using the ALMA pipeline in CASA
(Common Astronomy Software Applications; McMullin et al.
2007) version 5.4.0-68. The amplitude-bandpass calibrator was
chosen to be J0635−7516 or J0519-4546 in different execution
blocks, with the complex gains being corrected with the calibrators J0529−7245 or J0601−7036. Continuum subtraction, determined from line-free channels, was done in the u,v-domain using
the CASA task `uvcontsub` . The images were produced with the
CASA task `tclean`, using a standard gridding and the _Briggs_
weighting with the robust parameter set to 0.5 as a compromise
between sensitivity and resolution. The final images, both continuum and spectral data cubes, have been primary beam corrected using the `impbcor` task in CASA. Typical errors for the
continuum images are about 65 µJy beam [−][1] (10 mK) and about
1.92 mJy beam [−][1] (0.23 K) for the cubes (see Table 2). More details on the observations and the continuum images can be found
in Paper II. As an example, Fig. 2 shows the 1.2 mm ALMA
continuum emission toward four fields.


**3.** **Results and analysis**


A total of 65 compact sources were identified in the continuum
images of the 20 fields in the LMC, defined by the 50% intensity contour level around well-defined intensity peaks (see Paper II). These objects have peak continuum fluxes above five
times the image rms noise and constitute clear detections of compact sources. We used the temperatures estimated in the current
paper to calculate the dust and gas mass of each core, assuming that the 1.2 mm continuum emission originates in optically
thin dust with an opacity of 1.04 cm [2] g [−][1] (for dust grains coated
by thin ice mantels after 10 [5] yr of coagulation in a hydrogen
density of 10 [6] cm [−][3], Ossenkopf & Henning 1994) and a gasto-dust mass ratio of 316 (Sewiło et al. 2022). The cores have
masses [2] in the range of 20–1000 M ⊙, H 2 densities in the range
1.2 × 10 [5] –4.0 × 10 [6] cm [−][3], and H 2 column densities ranging from


2 According to the tentative detection of radio recombination lines toward one of the cores (see Section 3.1), we note that there might be a
certain level of contamination from thermal free-free emission in the


Article number, page 3 of 90

2006), and HERITAGE/SPIRE 350 µm (red, Meixner et al. 2013) images. The positions of the 20 ALMA fields are marked with
white circles 15 times larger than the field of view of our ALMA observations and the field number. The color-composite images of
the fields with hot core detection combining the VMC K-band (blue, Cioni et al. 2011), ALMA CS (5–4) peak intensity (green, this
work), and 1.2 mm ALMA continuum (red, this work and Paper II) images are shown as insets. The hot cores reported in this paper,
4A (ST16; Shimonishi et al. 2020), 6A (N105-2 B; Sewiło et al. 2022), 6B (N105-2 A; Sewiło et al. 2022), and 14A are highlighted
in the insets images.



6.0 × 10 [22] –1.5 × 10 [24] cm [−][2] . In this paper, we focus on the chemical properties of these 65 compact objects. In Section 3.1, we
describe the spectral analysis performed toward these sources,
while in Section 3.2 we analyze their spectral properties, such as
temperature, line width, and chemical content.


1.2 mm continuum fluxes for at least the most massive core. Therefore,
the higher-end value of the masses, H 2 column, and volume densities
may be overestimated.


Article number, page 4 of 90



_3.1._ _Spectral analysis of the continuum cores_


In this section, we present the steps to analyzing the extracted
spectra from the 65 compact sources identified in the ALMA
1.2 mm continuum images (see Paper II). The spectra of each
source were extracted from the primary beam corrected cube
images of the four spectral windows (see Table 2). The average
spectra were computed using the `spectral-cube` python package (Robitaille et al. 2016) with the pixels enclosed within the

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Table 2: Spectral cube parameters for primary beam corrected images.


Spectral Frequency range _[a]_ Synthesized beam (Θ _B_ ) _[a]_ Channel width Cube rms _[a,b]_

window (GHz) (" × ") (MHz / kms [−][1] ) (mJy beam [−][1] / K)

241 GHz 241.37–241.84 0.497 × 0.436 0.122 / 0.15 2.58 / 0.28
244 GHz 243.67–245.54 0.421 × 0.362 0.488 / 0.6 1.50 / 0.21
257 GHz 256.72–258.59 0.405 × 0.347 0.488 / 0.6 1.61 / 0.22
259 GHz 258.76–260.63 0.405 × 0.360 0.488 / 0.6 2.01 / 0.25



**Notes.** [(] _[a]_ [)] The average value for the 20 fields.
( _b_ ) The rms noise per channel width is estimated in a line-free channel.


1.0


0.8





4 [h] 56 [m] 41.5 [s] 41.0 [s] 40.5 [s]


Right Ascension


5 [h] 19 [m] 13.0 [s] 12.5 [s] 12.0 [s] 11.5 [s]


Right Ascension



-69°29'14"


16"


18"


20"



-66°32'28"


30"


32"


34"


-69°09'04"


06"


08"


10"


12"







0.8


0.6


0.4


0.2


0.0


3.0


2.5


2.0


1.5


1.0


0.5


0.0



5 [h] 39 [m] 42.0 [s] 41.5 [s] 41.0 [s] 40.5 [s]


Right Ascension



0.6


0.4


0.2


0.0


1.2


1.0


0.8


0.6


0.4


0.2


0.0



-68°00'32"


34"


36"


38"


40"



5 [h] 23 [m] 44.0 [s] 43.5 [s] 43.0 [s]


Right Ascension



Fig. 2: Examples of the 1.2 mm continuum emission toward four regions of the LMC sample. The contours show the three, six, and
nine times the σ _rms_ . The identified compact cores are highlighted with white contours at 50% of the peak emission. The synthesized
beam of the images and a scale bar are shown in the bottom-left and bottom-right corners of each panel, respectively. See Paper II
for more details on the 20 fields observed across the LMC (see Table 1).



50% peak-intensity contour of the 1.2 mm continuum emission
maps. Figure 3 shows an example spectrum (see Appendix A for
the rest of the spectra).


As a first step in the analysis of the extracted spectra, we
identified the molecular lines toward the most chemically rich
sources (i.e., spectra with the largest number of line detections;
see Fig. 3 for an example) using the CDMS catalog (Cologne
Database for Molecular Spectroscopy; Müller et al. 2005). For
this, we estimated the noise level (σ rms ) in each spectrum (i.e., for



each source and spectral window) by performing a sigma clipping analysis. Based on this noise-level determination and the intensity of each spectral line feature, we sorted the detected lines.
We considered the lines as a definite detection if their peak value
exceeded 5σ rms and as tentative features if the line strength is
between 3 and 5σ rms . The definite and tentative detections are respectively labeled with black and gray in Fig. 3 and Figures A.1
to A.20. With a complete set of molecules presented in Table 3,
including definite and tentative detections, we fit the spectra us

Article number, page 5 of 90

_A&A proofs:_ manuscript no. aanda


Field 14: 052333.40-693712.1 - A (14A)





2.0


1.5


1.0


0.5


0.0



0.5

241.6 241.7 241.8 241.9 242.0


10


8


6


4


2


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


6


5


4



3





2


1


0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


2.0


1.5


1.0


0.5


0.0


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


Fig. 3: ALMA Band 6 observed spectra toward source 14A overlaid with the best-fit XCLASS model. Molecular transitions with
definite detections (S/N - 5) are represented by solid black lines, while those with tentative detections (3 < S/N < 5) are denoted
by dotted gray lines. Dotted red lines indicate transitions of molecules for which abundance upper limits are provided.



ing the XCLASS toolbox [3] (eXtended CASA Line Analysis Software Suite; Möller et al. 2017, 2023, with additional extensions,


3 `[https://xclass.astro.uni-koeln.de/](https://xclass.astro.uni-koeln.de/)`


Article number, page 6 of 90



T. Möller, priv. comm.). XCLASS solves the radiative transfer
equation in one dimension in local thermodynamic equilibrium
(LTE) or non-LTE based on the request. It can solve the radiative

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud



Table 3: Definite and tentative detections of molecular species
along with the corresponding number of sources exhibiting these
emissions.


Molecular Number Molecular Number
species of sources _[a]_ species of sources _[a]_

CS 58 / – HC [15] N 6 / 3
SO 43 / 2 H 2 CS 23 / 7
33 SO 3 / – HNCO 3 / 1
SiO 8 / 12 HDCO – / 1
SO 2 16 / 11 HC 3 N – / 3
33 SO 2 1 / 1 CH 3 OH 45 / 2
34 SO 2 1 / 2 CH 3 CN 4 / 1
H [13] CO [+] 32 / 3 NH 2 CHO – / 1
H [13] CN 15 / 8


**Notes.** [(] _[a]_ [)] Definite / tentative detection(s)


transfer equation for an unlimited number of molecules simultaneously, taking line blending into account and producing modeled spectra. XCLASS provides the basis for finding the best-fit
model to the observed spectra by encompassing a large set of
fitting algorithms available within the MAGIX interface (Möller
et al. 2013). The fitting procedure works with the χ [2] minimization. The contribution of a certain molecule can be described
by more than one component. This is useful when the detected
molecular emission line may come from different unresolved
structures with different sizes, temperatures, or even distances to
the observer. Each component is described by source size, temperature, column density, line width, and velocity offset. These
can be fixed or free to vary to get the best-fit spectra and the best
set of parameters.
Using XCLASS, we analyzed the spectra assuming that all
the considered molecular species are located within a core layer
at the position of the source (i.e., we did not consider foreground
clouds located between the source and the observer). In the absence of optically thick transitions, column density and source
size are degenerate and cannot be determined separately. Therefore, we fixed the source size for all the molecules to a very
large value to impose a beam-filling factor of one. [4] The temperature, column density, line width, and velocity shift are in general
free parameters to fit. While parameters such as line width and
velocity shift can be determined from Gaussian fits to the detected spectral lines, a good determination of the temperature requires the detection of several transitions from the same molecular species. Based on this, we grouped the molecules into two
different categories: molecules with more than two transitions
detected within the four spectral windows and molecules with
only one or two transitions. The first group includes CH 3 OH,
SO 2, and CH 3 CN, and we fit the temperature for them using
XCLASS when multiple transitions were detected.
Out of 65 sources, CH 3 OH was detected in 48, while 37
sources show clear detections of three or more transitions. One

or two transitions were detected toward the other 11 sources.
Seventeen sources have no CH 3 OH features with line intensities higher than 3σ _rms_ . In the first iteration, we fit CH 3 OH using
an LTE approximation, which resulted in low temperatures (5–
17 K; see Table B.1) and some line features to be underfit or
overfit (see Fig. B.1). Based on these inaccuracies, we switched
to non-LTE for fitting CH 3 OH, which resulted in better fits. In


4 We note that a smaller source size results in higher column densities.



the non-LTE description, we have two additional parameters to
consider: the ratio of A and E CH 3 OH and the collision partner [5]
volume density. We fixed the A to E CH 3 OH ratio to one and
fit the collision partner density in the cores with more than two
CH 3 OH lines. The fit collision partner densities are ≈ 10 [6] cm [−][3]
for most of the cores and about ≈ 10 [7] cm [−][3] for those cores with
bright CH 3 OH lines. For the sources with one or two CH 3 OH
lines, we fixed the density of collision partners to the median
value of the rest of the cores: 2.0 × 10 [6] cm [−][3] . With this, we then

                                      fit the temperature, column density, line width, and velocity off
set. The derived gas kinetic temperatures for CH 3 OH with the
non-LTE description are generally in the range of 20–60 K (see
Table B.2). Finally, for those sources with no CH 3 OH detection,
we fixed the temperature to the median value of the other cores
and the line width and velocity offset to values derived for CS, if
this was detected, and we derived an upper limit for the CH 3 OH
column density.
We found SO 2 to be present in 12 sources with enough lines
for temperature determination under LTE conditions. However,
only in five sources were there enough SO 2 lines to fit the spectra using non-LTE. For these sources, we compared the LTE and
non-LTE fits, finding no major differences in the output temperatures and fit quality. Therefore, we fit SO 2 for all the fields using
an LTE approach. For the rest of the molecular species, we fixed
the temperature to the best-fit value for CH 3 OH. If CH 3 OH was
not detected or properly fit in the spectra of a source, we fixed
the temperature of other molecules to the median of the best-fit
value for CH 3 OH from other sources.
For four sources (4A, 6A, 6B, and 14A), a one-component
model for CH 3 OH and SO 2 did not give satisfactory results. A
two-layered morphology with a hot central component and a
colder envelope as the foreground provided the most convincing results. The core component’s source size was fixed to a
sub-beam size (not beam filling), while the foreground component was set to fill the beam. In these sources, we detected several transitions of CH 3 CN with a high enough S/N, which provided an additional temperature estimate. As done for the other
sources in the sample, for the rest of the molecules, we fixed
the temperature to what was derived from the hot component
of CH 3 OH. Moreover, some isotopologues were also detected
in these sources. We used the flexibility of XCLASS to link the
isotopologues to the main species, giving them the same temperature and velocity profile to fit the isotopologue ratio from
the ratio of column densities. We also detected HNCO and tentatively detected HDCO, HC 3 N, and NH 2 CHO in one or more
cores among these four cores. Furthermore, we estimated an upper limit for HDCO, NH 2 CO, CH 3 CHO, and CH 3 OCH 3 in these
four cores when they appeared in the spectra, but they were not
fit properly due to having a low S/N (S/N < 3). To this purpose,
we fixed the temperature and line width and velocity shift to the
hot component of CH 3 OH. These transitions are marked with
red in the figures of the corresponding spectra. In addition, we
searched for hydrogen recombination lines (RLs) in all sources.
Within the four observed spectral ranges, there are two potentially detectable RLs (H36β and H41γ). However, we only found
one tentative detection of H36β toward source 3A (see Fig. A.3).
We used XCLASS to fit the RL emission. For the fit, we fixed the
electron temperature to 10 [4] K (e.g. Selier & Heydari-Malayeri
2012; Jin et al. 2023) and fit the other three parameters, obtaining an emission measure estimate of 2.5 × 10 [6] pc cm [−][6], a line


5 XCLASS uses a similar prescription as RADEX (van der Tak et al.
2007) for its non-LTE fitting. The collision parameters are from the Leiden Atomic and Molecular Database (LAMDA, Schöier et al. 2005).


Article number, page 7 of 90

250


200


150


100


50


0


250


200


150



_A&A proofs:_ manuscript no. aanda


Mass (T CH 3 OH, M )
17 18 21 24 26 28 32 33 34 34 35 35 36 36 38 41 44 46 47 49 52 55 56 58 60 65 68 70 71 72 72 74 74

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
|~~hot SO~~2|||||||||
||||||||||
||||||||||



12D 13H 13F 12B 2F 2D 17B 16A 10B 2C 8B 14B 11D 10C 13K 19D 12C 13A 19B 13B 3D 11A 10D 19C 1A 15C 3C 18B 8C 16B 9A 18C 13G

Source


Mass (T CH 3 OH, M )

75 81 99 105 112 122 138 141 143 144 147 148 156 157 205 216 216 217 253 254 275 301 306 356 383 402 547 633 662 875 941 1004



100


50


0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
|~~hot SO~~2|||||||||
||||||||||
||||||||||


7B 7C 19A 13C 15B 20A 17A 6E 2A 13D 12A 14A 11B 15A 18A 6D 5B 13E 2B 7A 2E 6F 8A 6C 10A 6B 6A 4A 3B 5A 11C 3A

Source


Fig. 4: Best-fit XCLASS temperature for different molecular tracers. In case of definite detection in more than two transitions,
CH 3 OH, SO 2, and CH 3 CN were free for fitting (for more details, see Section 3.1). There is an uncertainty of 40%–60% for the
temperatures. The sources are ordered by increasing mass (from Paper II), calculated with the temperature of the CH 3 OH (cold)
component to account for the total mass in the core. The hot cores are highlighted with yellow bars.



width of 18.2 km s [−][1], and a velocity offset of 284.4 km s [−][1], consistent with the velocity derived for the molecular species.
The fitting procedure in XCLASS uses an algorithm chain
from the MAGIX interface, including the genetic algorithm as a
global minimizer and the Levenberg-Marquart algorithm as a local minimizer. We also ran XCLASS with a Markov chain Monte
Carlo (MCMC) algorithm on a few spectra to estimate typical
errors on the different fitting parameters. The error values range
from 40%-60% for the temperatures, 20%-40% for the column
densities, and 10%-30% for the line widths and velocity shifts.
In the non-LTE solution, there is a degeneracy in defining the
temperature, column density, and collision partner density that
makes it hard to agree on an error value. The outcome of the
fitting procedure is shown as modeled spectra (in black) overlaid on observed spectra (in colors) in Fig. 3 and Figures. A.1
to A.20. The best-fit parameters are listed in Table B.2, and the
upper-limit estimations are marked with a less than (<) sign.


_3.2._ _Results from spectral analysis_


3.2.1. Temperature of compact cores


As discussed in Section 3.1, we fit the temperature for three
molecular tracers, CH 3 OH, SO 2, and CH 3 CN, when there were
firm detections. This resulted in 47 sources with a temperature
determination using CH 3 OH, 12 sources with SO 2, and only four
sources with CH 3 CN-derived temperatures. Figure 4 shows the
derived temperatures for the different molecular tracers for all


Article number, page 8 of 90



65 compact cores. The cores are ordered based on their mass (as
determined in Paper II).
As stated earlier, out of the 65 cores, only four have a reliable temperature determined using CH 3 CN, and it is only for
these four cores that we needed more than one component to
fit SO 2 and CH 3 OH (see Table B.2). Furthermore, we only obtained temperatures above 100 K for the hottest component of
these four sources, with the temperature remaining consistently
below 60 K for the rest of the sources. Based on the definition of
a hot molecular core to have a temperature higher than 100 K, we
can classify these four sources (4A, 6A, 6B, and 14A) as such.
These hot cores are likely embedded in a colder envelope with
temperatures about 30–40 K, similar to the temperatures derived
for the other cores in the sample.


3.2.2. Line-width of different molecules


The line width of a molecular species provides useful information about the kinematics of the gas. Figure 5 compares the
line widths derived for different molecular species from fitting
the Gaussian line profile with XCLASS (see Section 3.1). Six
molecules, including the ubiquitous ones, CS, SO, CH 3 OH, and
two other abundant species, SO 2 and H [13] CO [+], together with the
shock tracer SiO were utilized. The line widths vary between 1
and 35 km s [−][1], with methanol having the lowest value in 49% of
the cores. In this plot, we present the line width value for the hot
component of SO 2 and CH 3 OH when there are two temperature

10


8


6


4


2


0


37.5


35.0


32.5


12


10


8


6



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Line Width of Species at FWHM from XCLASS Fitting


12D 13H 13F 12B 2F 2D 17B 16A 10B 2C 8B 14B 11D 10C 13K 19D 12C 13A 19B 13B 3D 11A 10D 19C 1A 15C 3C 18B 8C 16B 9A 18C 13G


Sources







4


2


0


7B 7C 19A 13C 15B 20A 17A 6E 2A 13D 12A 14A 11B 15A 18A 6D 5B 13E 2B 7A 2E 6F 8A 6C 10A 6B 6A 4A 3B 5A 11C 3A

Sources


Fig. 5: Best-fit XCLASS line width (full width at half maximum, FWHM) for different molecular species. The line width of 5 km/s
is marked with a dashed line as a reference. There is an uncertainty of 10%–30% for the line widths. The sources are ordered by
increasing mass (from Paper II) with the temperature of CH 3 OH (cold) component to account for the whole mass in the core. The
hot cores are highlighted with yellow bars.



components. A value of 5 km s [−][1] is shown with a dashed line as
a reference. The number of cores with line-width values larger
than 5 km/s for at least one of the molecular species is 16. In
nine of these sources, SiO is one of the molecules with a large
line width suggesting the presence of molecular outflows, which
will be studied in a forthcoming paper. Among them, we can
identify the four cores (4A, 6A, 6B, and 14A) with temperatures
higher than 100 K (see Section 3.2.1 and Fig. 4).


3.2.3. Chemical contents of the cores


Several molecular lines were detected in the spectra of each core.
Among all the species, methanol was detected toward 74% of
the cores (48/65). Among 17 cores with no-CH 3 OH line detection, seven cores showed no emission lines at all (8B, 11A, 13B,
14B, 16A, 17B, and 19B). Other molecular species with high
detection rates include CS, SO, SO 2, H [13] CO [+], H [13] CN, HC [15] N,
H 2 CS, and SiO, while more complex molecules, such as HDCO,
HNCO, HC 3 N, and CH 3 CN or isotopologues of SO and SO 2,
were detected only toward a small subset of objects (about 8%
of the sample). We also report a tentative detection of NH 2 CHO
in one of the cores (6A). Moreover, CH 3 OCHO or CH 3 OCH 3
emerged in the modeled spectra after fitting an upper limit column density for them toward the cores 4A, 6B, and 14A. In addition, a hydrogen RL, H36β, was detected tentatively toward the
most massive core in our sample (3A). In addition, H41γ is also
in the observed bands, and we mark it with red on the spectra
of this core, as it was detected with an S/N less than three. The



detection of this RL suggests the presence of Hii regions that
likely contribute to the 1.2 mm continuum emission. Preliminary
data at 6 GHz obtained with ATCA (Hamedani Golshan, priv.
communication) favors this interpretation. The mass derived for
this source is likely overestimated in the current analysis. Interestingly, we have a tentative detection of CH 3 CN towards the
source 3A. The detection of CH 3 CN, which is only clearly detected toward the four cores 4A, 6A, 6B, and 14A in the sample
(see Section 4), together with the detection of RLs (likely related
to an Hii region) in 3A suggests the presence of a hot core near
an expanding Hii region, a scenario that is commonly found in
several hot cores of the MW (e.g., Kurtz et al. 2000; SánchezMonge et al. 2013a; Cesaroni et al. 2017).
We compared the abundances of different molecules in all
the sources. The abundances were derived by dividing the column density of every molecule by the molecular hydrogen
column density (N(H 2 ), derived in Paper II). For this purpose, we assumed that the dust and gas at the position of the
source are well mixed and have the same temperature as derived from the XCLASS fits (see Table B.2). Figure 6 shows
the abundance of the molecules with the highest detection rate
for all the cores, whereas in Figures 7 to 10, the molecules
are grouped into three different groups: S-bearing species (SO,
SO 2 ) and SiO; N-bearing species (H [13] CN, HC [15] N, and HNCO)
and (HC 3 N, CH 3 CN, and NH 2 CHO); and O-bearing species
(HDCO, CH 3 OCHO, CH 3 OCH 3 ). We ordered the cores based
on their mass, but we did not see any clear correlation between
mass and abundance for any of the species. When comparing


Article number, page 9 of 90

_A&A proofs:_ manuscript no. aanda


Mass (T CH 3 OH, M )
17 18 21 24 26 28 32 33 34 34 35 35 36 36 38 41 44 46 47 49 52 55 56 58 60 65 68 70 71 72 72 74 74



10 6


10 7


10 8


10 9


10 10


10 11


10 12


10 13


10 6


10 7


10 8


10 9


10 10


10 11


10 12


10 13







12D 13H 13F 12B 2F 2D 17B 16A 10B 2C 8B 14B 11D 10C 13K 19D 12C 13A 19B 13B 3D 11A 10D 19C 1A 15C 3C 18B 8C 16B 9A 18C 13G

Source


Mass (T CH 3 OH, M )

75 81 99 105 112 122 138 141 143 144 147 148 156 157 205 216 216 217 253 254 275 301 306 356 383 402 547 633 662 875 941 1004







7B 7C 19A 13C 15B 20A 17A 6E 2A 13D 12A 14A 11B 15A 18A 6D 5B 13E 2B 7A 2E 6F 8A 6C 10A 6B 6A 4A 3B 5A 11C 3A

Source


Fig. 6: Abundances of molecular species with a high detection rate in our sample. There is an uncertainty of 20%–40% on the
column densities. The sources are ordered by increasing mass (from Paper II) with the temperature of CH 3 OH (cold) component to
account for the whole mass in the core. The hot cores are highlighted with yellow bars. The arrows show an upper-limit estimation.



the different groups of molecules, we observed that S-bearing
species are, on average, more abundant than N- and O-bearing
species.
Finally, comparing all the abundance plots, it was evident
that four sources show a rich chemistry with the presence of
various molecular species. These sources would classify as hot
molecular cores based on their chemistry, as well as their temperatures, since these objects are the only cores with temperatures
above 100 K and average line widths above 5 km s [−][1] . Interestingly, these four sources are those with the largest SO 2 abundances, thus supporting the interpretation by Shimonishi et al.
(2023) that bright SO 2 lines are a good tracer of hot molecular
cores in the low-metallicity environment of the LMC and SMC.


**4.** **Discussion**


_4.1._ _Hot cores in our survey_


Based on the spectral analysis of the 65 continuum sources, we
report the detection of four hot molecular cores and one hot
core candidate from the ALMA observations of 20 fields hosting
YSOs in the LMC. As highlighted in Section 3, four cores (4A,
6A, 6B, and 14A) have temperatures above 100 K, large line
widths, and the highest chemical richness among all the cores in
the sample. This, together with the fact that the spatial size of
these cores where the emission reaches half of the peak value in
the continuum map, Ω obs (Ω deconv ), is between 0.12 (0.08) and
0.14 (0.11) pc (see Paper II) suggest that they are in the hot
molecular core phase. This result confirms the previous detec

Article number, page 10 of 90



tion of hot cores in ST16 YSO (Shimonishi et al. 2020) and two
hot cores N105-2 A and N105-2 B in the N105 star-forming region (Sewiło et al. 2022). In addition, we present a new hot core

−
detection in field 14: 0523333.40 693712.1, 14A. With this new
detection, the number of known hot cores in the LMC increases

to seven.


Isotopologues of SO and SO 2 were detected toward the hot
cores in our sample. The hot cores 4A and 6A show emission
lines from [33] SO, [33] SO 2, and [34] SO 2 . Hot core 6B contains [33] SO
and [34] SO 2 but no [33] SO 2, and the core 14A shows no reliable
detection of these isotopologues. We derived the isotopic ratios
of [32] S/ [33] S and [32] S/ [34] S toward hot cores 4A and 6A and found
them to vary between 12 and 21 and 9 and 19. These values
can be compared with previous estimates in the LMC and other
galaxies. Gong et al. (2023) used the APEX 12-m telescope to
measure sulfur isotopic ratios in the LMC and compiled a set
of measurements toward the LMC, different regions of the MW,
and starburst galaxies (see their Table 2). For the LMC, Gong
et al. (2023) found the ratios of [32] SO/ [33] SO and [32] SO/ [34] SO to
range between 27 and 53 and 15 and 19, respectively. Combined
with our results, which are similar to or slightly lower than previous estimates, the range for these isotopic ratios increases to
12 to 53 for [32] SO/ [33] SO and 9 to 19 for [32] SO/ [34] SO. The sulfur
isotopic ratios in the LMC are lower than in different regions
throughout the MW but more consistent with measurements in
starburst galaxies. Gong et al. (2023) suggest that the low values in the LMC might be attributed to a combination of age, low
metallicity, and star-formation history.

10 7


10 8


10 9


10 10


10 11


10 12


10 13


10 14


10 7


10 8


10 9


10 10


10 11


10 12


10 13


10 14



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Mass (T CH 3 OH, M )
17 18 21 24 26 28 32 33 34 34 35 35 36 36 38 41 44 46 47 49 52 55 56 58 60 65 68 70 71 72 72 74 74



SO, H [13] CO [+], and H 2 CS show faint elongation in the north-south

|Col1|H2CS<br>SO|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|Col27|Col28|Col29|Col30|Col31|Col32|Col33|Col34|Col35|Col36|Col37|Col38|Col39|Col40|Col41|Col42|Col43|Col44|Col45|Col46|Col47|Col48|Col49|Col50|Col51|Col52|Col53|Col54|Col55|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|2<br>SiO|
||||||||||||||||||||||||||||||||||||||||||||||||||||||||
||||||||||||||||||||||||||||||||||||||||||||||||||||||||
||||||||||||||||||||||||||||||||||||||||||||||||||||||||
|12D 13H 1<br>H2<br>~~SO~~<br>Si<br>75<br>81<br>9|12D 13H 1<br>H2<br>~~SO~~<br>Si<br>75<br>81<br>9|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|3F 12B<br>2F<br>2D 17B 16A 10<br>CS<br>2<br>O<br>9<br>105 112 122 138 141 1|B<br>2<br>43 1|C<br>8B<br>14B <br>44 147 14|C<br>8B<br>14B <br>44 147 14|C<br>8B<br>14B <br>44 147 14|11D 10C 13K <br>8 156 157 20<br>Mas|11D 10C 13K <br>8 156 157 20<br>Mas|11D 10C 13K <br>8 156 157 20<br>Mas|11D 10C 13K <br>8 156 157 20<br>Mas|19<br><br>5 <br>s|D 12C <br>Sourc<br> 216 2<br> (TCH3|D 12C <br>Sourc<br> 216 2<br> (TCH3|D 12C <br>Sourc<br> 216 2<br> (TCH3|13<br>e<br>16 <br>OH|A <br><br> 2<br>,|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|19B 13B 3D 11A 10D 19C<br>1<br>17 253 254 275 301 306 35<br> M )|A<br>6|1<br> 38|5C<br>3|3C<br>1<br> 402 5|3C<br>1<br> 402 5|8B<br>8C<br>1<br>47 633 66|8B<br>8C<br>1<br>47 633 66|8B<br>8C<br>1<br>47 633 66|8B<br>8C<br>1<br>47 633 66|8B<br>8C<br>1<br>47 633 66|6B<br>2||9<br>87|A<br><br>5|A<br><br>5|1<br>94|8C 13G<br>1 1004|8C 13G<br>1 1004|8C 13G<br>1 1004|
||||||||||||||||||||||||||||||||||||||||||||||||||||||||
||||||||||||||||||||||||||||||||||||||||||||||||||||||||
||||||||||||||||||||||||D<br>ou<br>     ri<br>.<br>n <br>wo<br>u<br>er<br>wi<br>f <br>CH<br>mo<br>he<br>n <br>ng<br>n<br>ng<br>o<br>u<br>y <br>b<br>n<br>f<br>i<br>O<br>b<br>o|5<br>rc<br>     n<br>1.<br> a<br>r<br>sl<br>v<br>th<br> s<br>3<br><br>l<br> e<br> th<br> t<br>d <br> <br>m<br>r <br> a<br>un<br>ce<br> S<br>O<br> <br>un<br>ss|B<br>e<br>     g<br>2. <br>dd<br>k, <br>y<br>at<br> t<br>p<br>C<br>Sh<br>ec<br> m<br>e <br>h<br> S<br> un<br>p<br>st<br> f<br>d<br> i<br> hi<br> ar<br>sh<br>d<br>ib|1<br><br>     sp<br> C<br>it<br> t<br> b<br>io<br> ho<br>ec<br>N<br>i<br>ul<br> b<br> d<br>e <br>O<br> c<br>on<br>u<br>ac<br>a<br> n<br> m<br> e<br>o<br>a<br>le|3E<br>     ec<br>o<br>io<br>he<br> ee<br>na<br> s<br>ie<br>,<br>mo<br>ar<br> ed<br>et<br> ad<br>2 <br> er<br>e<br>dy<br>to<br>nc<br> th<br> o<br> sl<br>w <br>nc<br> d|2<br>     ie<br>m<br>n <br> o<br> n<br>l <br> e i<br>s <br> H<br>n<br> c<br> d<br>ec<br>o<br>ha<br> ta<br>nt <br>, <br>r <br>es<br> e<br> ni<br> ig<br> lo<br>e <br> e|B<br>     s<br>p<br> t<br>t<br> id<br> d<br> n<br> d<br> N<br>is<br>o<br> e<br>ti<br>pt<br>v<br> in<br> o<br>an<br> o<br> f<br>  g<br> sh<br> h<br>w<br> fo<br> ge|7<br>    ,<br>ar<br>o <br>he<br> e<br>at<br>  t<br>et<br> C<br>hi<br>re<br> d h<br>o<br>e<br>e <br> ti<br>f <br>d <br>f <br> ro<br>  as<br> i<br> tly<br>e<br>r <br> n|A<br>2E<br>6<br>      H2CS, S<br>ison of<br>14A, w<br>r three <br> ntifed i<br>asets. I<br>  he litera<br>ected t<br> O, H13C<br> et al. <br> based <br> igh-ma<br>n of the <br>d nome<br> the sam<br> es (see F<br> both sp<br> the der<br>1.5. The<br> m the t<br>  -to-dust<br> et al. (2<br>  higher<br>r abund<br> CH3CN<br> eracy b|F<br> O<br> h<br>hi<br> h<br>  n<br>n <br>  tu<br>ow<br>O<br> (<br>on<br> ss<br> s<br>nc<br>e <br>  i<br>ec<br>iv<br> t<br>  wo<br>  m<br>  02<br>  in<br>an<br> <br> et|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|8<br> 2,<br> ot<br>c<br>ot <br>  ot<br>th<br>  re<br>a<br>+ <br>20<br> <br>  i<br>a<br>la<br> t<br>  g.<br>i<br>e<br>o<br> <br>  a<br>  0<br>   t<br>c<br>in<br> w|

direction. Moreover, HNCO and HDCO show a very faint emission, offset from the hot core, and H 2 CS emission also peaks
offset to the hot core, where the HNCO emission peaks.



6 Shimonishi et al. (2020) assumed a dust-to-gas mass ratio of 0.0027
for ST16, which corresponds to a factor 1.15 lower compared to the
value we use. In order to compare the abundances, we applied this factor
to the molecular abundances reported by Shimonishi et al. (2020).


Article number, page 11 of 90

10 9


10 10


10 11


10 12


10 13


10 9


10 10


10 11


10 12


10 13



_A&A proofs:_ manuscript no. aanda


Mass (T CH 3 OH, M )
17 18 21 24 26 28 32 33 34 34 35 35 36 36 38 41 44 46 47 49 52 55 56 58 60 65 68 70 71 72 72 74 74

|Col1|H13CN|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|Col27|Col28|Col29|Col30|Col31|Col32|Col33|Col34|Col35|Col36|Col37|Col38|Col39|Col40|Col41|Col42|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||HC15N<br>~~HNCO~~|HC15N<br>~~HNCO~~||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|12D 13H 13F 12B<br>75<br>81<br>99<br>105|12D 13H 13F 12B<br>75<br>81<br>99<br>105|12D 13H 13F 12B<br>75<br>81<br>99<br>105|12D 13H 13F 12B<br>75<br>81<br>99<br>105|2<br> 1|F<br>2D 17B 16A 10B<br>12 122 138 141 143|F<br>2D 17B 16A 10B<br>12 122 138 141 143|F<br>2D 17B 16A 10B<br>12 122 138 141 143|2<br>|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|C<br>8B<br>14B 11D 10C 13K 19D 12C <br>Sourc<br>144 147 148 156 157 205 216 2<br>Mass (TCH3|1<br>e<br>16 <br>O|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|3A 19B 13B 3D 11A 10D 19C<br><br><br> 217 253 254 275 301 306 35<br>H, M )|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1A<br>15C<br>3C<br>18B<br>8C<br><br>6 383 402 547 633|1<br>66|6B<br><br>2 8|9A<br>18C 13G<br>75 941 1004|9A<br>18C 13G<br>75 941 1004|9A<br>18C 13G<br>75 941 1004|
||~~H13CN~~|~~H13CN~~||||||||||||||||||||||||||||||||||||||||
||HC15N<br>~~HNCO~~|HC15N<br>~~HNCO~~||||||||||||||||||||||||||||||||||||||||
||HC15N<br>~~HNCO~~|HC15N<br>~~HNCO~~||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||



7B 7C 19A 13C 15B 20A 17A 6E 2A 13D 12A 14A 11B 15A 18A 6D 5B 13E 2B 7A 2E 6F 8A 6C 10A 6B 6A 4A 3B 5A 11C 3A

Source


Fig. 8: Same as Fig. 6 but for N-bearing species, H [13] CN, HC [15] N, and HNCO.



the spectral data, suggesting that these two sets of parameters
can reproduce the observed lines. Further observations can help
in better constraining both the temperature and density for this
hot core. Sewiło et al. (2022) found two hot cores, N105-2 A
and N105-2 B, from Cycle 7 Band 6 observations of three fields
in the N105 star-forming region. We note that the hot cores 6B
and 6A in the current study correspond to the objects N105-2 A
and N105-2 B, respectively. The temperature estimations are in
good agreement for each pair of sources (see Fig. 12, middleand bottom-left panels), with larger variations happening for the
cold components of CH 3 OH and SO 2 in 6B compared to N1052 A. The middle- and bottom-right panels of Fig. 12 compare
the abundances from the two studies. Sewiło et al. (2022) assumed a gas-to-dust mass ratio of 316, very close to the value
we use, 320. The abundances of nearly all the molecules in 6A
compared to N105-2 B fall in the same range except CH 3 OH and
CH 3 CN, which are slightly higher in N105-2 B. Similar results
were obtained for 6B and N105-2 A, with abundances falling in
the same range. However CH 3 OH, HNCO and H [13] CO [+] show
abundances approximately two to five times lower in 6B (this
work). The observed differences are likely due to the slightly
different temperatures used to calculate the column densities in
both studies. Finally, we searched for detections of other species,
such as HDCO, CH 2 CO, and NH 2 CHO, that had been previously
detected by Sewiło et al. (2022). We could not confirm their detection because the expected brightness of the species is less than
the sensitivity of the current dataset. Only a tentative feature was
seen for NH 2 CHO toward source 6A (see Fig. A.6).


Overall, the differences in the molecular abundances between the different works are within a factor of less than five.


Article number, page 12 of 90



This factor is acceptable considering all possible errors and uncertainties in the analysis process. For example, different interferometric filtering during the observations as well as weather
conditions or calibration effects, procedures followed to extract
the spectra, or methodology used for fitting the lines may affect
the derived temperatures and abundances by factors commonly
in the range of two to ten. Therefore, we consider that our derived abundances are in agreement with previous studies, and
we used them in the following discussion.


_4.2._ _Properties of hot cores in the LMC_


4.2.1. Comparison of the hot cores in the LMC


Apart from the four hot cores discussed in the previous section,
three more have been reported in the LMC. Sewiło et al. (2018)
discovered the first two chemically rich hot cores in the N113
star-forming region, N113 A1 and N113 B3, with COMs with
up to nine atoms being detected in extra-galactic hot cores for
the first time. The abundance of the molecular species for these
objects, after scaling for metallicity, falls on the lower end of
the Galactic values. In contrast, the hot core ST11 reported by
Shimonishi et al. (2016b) was detected based on the presence of
hot SO 2, although no reliable COMs were detected. The absence
of COMs in this hot core was explained by a hot dust temperature resulting in inefficient CO hydrogenation to form CH 3 OH
(Shimonishi et al. 2016b).

Figure 13 shows a comparison of the molecular abundances
in the seven hot molecular cores detected to date in the LMC
after scaling to the gas-to-dust mass ratio used in the current

10 9


10 10


10 11


10 12


10 13


10 9


10 10


10 11


10 12


10 13



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Mass (T CH 3 OH, M )
17 18 21 24 26 28 32 33 34 34 35 35 36 36 38 41 44 46 47 49 52 55 56 58 60 65 68 70 71 72 72 74 74

|Col1|HC N|Col3|
|---|---|---|
||3<br>CH3CN<br>~~NH2CHO~~||
||||
||||
||||
||||



12D 13H 13F 12B 2F 2D 17B 16A 10B 2C 8B 14B 11D 10C 13K 19D 12C 13A 19B 13B 3D 11A 10D 19C 1A 15C 3C 18B 8C 16B 9A 18C 13G

Source


Mass (T CH 3 OH, M )

75 81 99 105 112 122 138 141 143 144 147 148 156 157 205 216 216 217 253 254 275 301 306 356 383 402 547 633 662 875 941 1004

|Col1|HC N|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|3<br>CH3CN<br>~~NH2CHO~~|
|||||||||||||
|||||||||||||
|||||||||||||



7B 7C 19A 13C 15B 20A 17A 6E 2A 13D 12A 14A 11B 15A 18A 6D 5B 13E 2B 7A 2E 6F 8A 6C 10A 6B 6A 4A 3B 5A 11C 3A

Source


Fig. 9: Same as Fig. 6 but for N-bearing species, HC 3 N, CH 3 CN, and NH 2 CHO.



paper (see Section 4.1.2). Each bar stands for one hot core,
with error bars and upper limits also depicted in the plot. The
non-detections of CH 3 CN, HNCO, H [13] CO [+], and SO toward
N113 A and N113 B are due to a lack of bright transitions of
these species in the observational setup, whereas the upper limits for ST11 show the absence or underabundance of this species,
which was in the observed frequency ranges but not detected.
The methanol abundance varies between 3.6 × 10 [−][9] for 4A and
6A and 5.3 × 10 [−][8] for N113 A1, where it is detected. The abundance of SO 2 varies between 5.0 × 10 [−][9] for 6B and 2.1 × 10 [−][8]
for 4A and ST11.

The abundances shown in Fig. 13 reveal some trends for the
hot cores in the LMC. We found an ascending pattern of an order of magnitude in the abundance of CH 3 OH from the ST11
to N113 region, while the abundance of SO 2 shows small variations among the hot cores. At a second level, there seems to exist a correlation between CH 3 OH and SiO. If SiO is produced in
shocks, likely associated with molecular outflows (e.g. Schilke
et al. 1997; Sánchez-Monge et al. 2013b), this correlation may
suggest that the higher abundance of CH 3 OH for some sources
may have a shock origin. These correlations will be explored in
a forthcoming work evaluating the spatial correlation of multiple
molecular species.


4.2.2. Comparison with chemical models


The presence of hot SO 2 in ST11 has been taken as a signature
of a hot core, with the absence of COMs in this source strengthening the idea of a warm dust chemistry in the LMC (see e.g.
Shimonishi et al. 2016b). Although only one hot core of this



kind has been detected in the LMC, we took advantage of the
hot core models by Acharyya & Herbst (2018) to investigate how
the warm dust hypothesis for low-metallicity environments compares to the current observations of hot cores in the LMC.


Acharyya & Herbst (2018) simulated the stages of star formation leading to hot cores and their lower-mass counterparts,
hot corinos, under the conditions of the LMC (and the SMC).
They used a gas-to-dust mass ratio of 175, a cosmic-ray ionization rate of 1.3 × 10 [−][17] s [−][1], and a radiation field strength similar to the Galactic values. The star formation was modeled in
three stages. The first stage is an isothermal cloud collapse under free fall with fixed gas and dust temperatures of 10, 15, 20,
and 25 K and a visual extinction _A_ v of 1.64 mag. The collapse
is stopped when the density reaches 10 [7] cm [−][3], a process that
lasts 9.3 × 10 [5] yr, during which _A_ v increases up to ≈ 450 mag.
In the second stage, the density is fixed at 10 [7] cm [−][3], while the
temperature increases linearly with time up to 100 or 200 K, resembling the temperature of hot cores. Two different times for
the heating process are considered, reproducing expected conditions for high-mass (5 × 10 [4] yr) and low-mass (10 [6] yr) star
formation. Once 100 or 200 K is reached, the warm-up ceases,
and the newly formed hot core is allowed to evolve until a final
total time of 10 [7] yr. This model does not include the effects of
shocks in the chemical evolution.


Figure 14 shows the time evolution of SO 2, CH 3 OH, and
CH 3 CN abundances for the hot core model described above for
the 100 and 200 K final temperatures (for other molecules see
Figures C.1 and C.2). The observed abundances for the seven hot
cores in the LMC are overlaid as horizontal lines in each panel
following the same color scheme as in Fig. 14. Interestingly, only


Article number, page 13 of 90

_A&A proofs:_ manuscript no. aanda


Mass (T CH 3 OH, M )
17 18 21 24 26 28 32 33 34 34 35 35 36 36 38 41 44 46 47 49 52 55 56 58 60 65 68 70 71 72 72 74 74



10 9


10 10


10 11


10 12


10 13


10 14


10 15


10 9


10 10


10 11


10 12


10 13


10 14


10 15





12D 13H 13F 12B 2F 2D 17B 16A 10B 2C 8B 14B 11D 10C 13K 19D 12C 13A 19B 13B 3D 11A 10D 19C 1A 15C 3C 18B 8C 16B 9A 18C 13G

Source


Mass (T CH 3 OH, M )

75 81 99 105 112 122 138 141 143 144 147 148 156 157 205 216 216 217 253 254 275 301 306 356 383 402 547 633 662 875 941 1004




|HDCO|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||



7B 7C 19A 13C 15B 20A 17A 6E 2A 13D 12A 14A 11B 15A 18A 6D 5B 13E 2B 7A 2E 6F 8A 6C 10A 6B 6A 4A 3B 5A 11C 3A

Source


Fig. 10: Same as Fig. 6 but for O-bearing species, CH 3 OCH 3, CH 3 OCHO, and HDCO.



the models where the initial dust temperature is assumed to be
between 10 and 20 K reproduce the observed molecular abundances. The chemical model with an initial highest dust temperature of 25 K results in molecular abundances that are much
lower than the observed ones. Based on the comparison with the
chemical models of Acharyya & Herbst (2018), a high initial
dust temperature does not seem to be a reason for a possible lack
of COMs in the hot cores of the LMC since chemical models
with initial dust temperatures in the range 10 to 20 K (similar to
star-forming regions in the MW) can better reproduce the molecular abundances observed in the LMC.


_4.3._ _Hot cores in the LMC, SMC, and MW_


A logical next step when studying the chemistry in lowmetallicity environments is to compare the molecular abundances from the hot cores in the LMC, SMC, and outer Galaxy
to those found in star-forming regions in the inner Galaxy.
To achieve this goal, we collected a sample of Galactic hot
cores studied in the literature and added them to the seven
hot cores found in the LMC (see Section 4.2), the two hot
cores recently discovered in the SMC (Shimonishi et al. 2023),
and the WB 89−789 SMM1 hot core found in the outer regions of the Galaxy (Shimonishi et al. 2021). In the case of
WB 89−789 SMM1, we used the abundances calculated for a
source with a size of 0.1 pc (from Table 4 of Shimonishi et al.
(2021)). In the interest of matching spatial scales, we focused on
single-dish observations of Galactic hot cores. In particular, we
considered the Orion Hot Core (Sutton et al. 1995), Sgr B2(N)
(Nummelin et al. 2000) and W3(H 2 O) (Helmich & van Dishoeck


Article number, page 14 of 90



1997) to represent the standard conditions and properties of hot
cores in the MW.

In Fig. 15, we present a comparison of the abundances of
four molecular species corresponding to the selected list of hot
cores. For the LMC hot cores, we first applied a correction factor
to account for the different gas-to-dust mass ratio every study
assumes (see Section 4.1.2). Then we applied a correction factor
of 5, 2.6, and 4 to the abundances of the hot cores in the SMC,
LMC, and extreme outer Galaxy [7] to account for differences in
metallicity. The original values are shown with single color bars
in Fig. 15, while the scaled values are depicted as an excess with
dotted patterns.
The methanol abundances vary by an order of magnitude
among the hot cores in the LMC, except for ST11, for which
only an upper limit is estimated. While the methanol abundances
show an ascending trend from the low metallicity of the SMC
to the LMC and to the inner regions of the MW, the only hot
core in the outer region of the Galaxy, with a factor of four
lower metallicity, shows the highest methanol abundance. We
note that CH 3 CN was not detected in all the hot cores, making
the comparison less robust. However, one can see that the abundance of CH 3 CN in the hot core in the outskirts of the Galaxy is
higher than those in the LMC. In contrast to higher abundances
of CH 3 OH and CH 3 CN in the outer Galaxy compared to the
LMC and SMC, SO 2 and SiO are less abundant. This raises the


7 We adopted Z Gal /Z SMC = 5, Z Gal /Z LMC = 2.6, Z Gal /Z ExtOutGal = 4. We
note that metallicity decreases with the Galactocentric radius in the
MW, resulting in varying metallicities across the outer Galaxy (e.g.,
Arellano-Córdova et al. 2021). The metallicity value we present for the
outer Galaxy corresponds to the position of WB 89-789.

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


18









-69°37'30"


32"



-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"



34"


36"



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension









-69°37'30"


32"



34"


36"


-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"





5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension









5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



16


14


12


10


8


8


7


6


5


4


8


7


6


5


4


20.0


17.5


15.0


12.5


10.0


7.5


5.0



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



14


13


12


11


10


9


8


50


40


30


20


10


35


30


25


20


15


10


5


13


12


11


10


9


8


7


6


5



-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"


-69°37'30"


32"


34"


36"



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



12


11


10


9


8


7


6


8


7


6


5


4


14


12


10


8


6


4


8.0


7.5


7.0


6.5


6.0


5.5


5.0


4.5


4.0









5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



5 [h] 23 [m] 38.0 [s] 37.5 [s] 37.0 [s] 36.5 [s]


Right Ascension



Fig. 11: Peak-intensity images of the molecular species detected toward hot core 14A. The maps are ordered based on the frequency
of the transition from left to right, top to bottom. The 1.2 mm continuum contours with contour levels of three, six, and nine times
the σ _rms_ and the 50% 1.2 mm continuum contour are overlaid in each image for reference. Top is north and right is west.



question of whether the abundance of different molecular species
is only a function of metallicity. We note that the outskirts of
the Galaxy are more quiescent due to the low star-formation activity, while the star-forming regions of the LMC and the SMC
are more active. While comparisons of the chemistry in different
conditions still need better observational statistics, we acknowledge the necessity of chemical modeling to further investigate
the effect of metallicity, strength of UV radiation, cosmic ioniza


tion rate, and shock chemistry on the observed molecular abundances.


Shimonishi et al. (2020) classified the LMC hot cores as
"organic-poor" and "organic-rich" based on the comparison of
only four hot cores in the LMC. Sewiło et al. (2022) placed
N105-2 A and N105-2 B in the organic-rich class, suggesting a
larger sample to verify this classification. We also acknowledge
the necessity of larger samples for a better understanding of hot
core chemistry in the LMC. At the same time, we revise the clas

Article number, page 15 of 90

_A&A proofs:_ manuscript no. aanda



sification of organic-poor and organic-rich based on the findings
of this study. Shimonishi et al. (2020) classified ST11 and ST16
as organic-poor and N113 A1 and N113 B3 as organic-rich hot
cores to emphasize the detection of more complex compounds
with comparable scaled abundances to the Galactic hot cores.
Our survey study, however, demonstrates a different picture. All
the hot cores in our sample show comparable chemical complexity. A slightly different chemistry may relate to the evolutionary
stage of the hot core and surrounding gas. For example, we detected isotopologues of SO 2, [33] SO 2, and [34] SO 2 in the hot core
4A but had no detection of deuterated molecules. In contrast,
hot core 14A shows emission lines from HDCO but no emission
from SO 2 isotopologues. The common association of deuterated
species with early evolutionary stages (e.g. Fontani et al. 2011;
Treviño-Morales et al. 2014) and the connection of SO 2 with the
presence of shocks and ionized gas (e.g. Minh et al. 2016; Gieser
et al. 2021) suggest that different evolutionary stages and physical conditions are likely relevant factors of the chemical content
of the hot cores in the LMC. Within this picture from the hot
cores in the LMC, the only organic-poor hot core that remains is
ST11.
In Fig. 16, we present pair-wise comparisons of the abundances of CH 3 CN, CH 3 OH, SO 2, SO, and SiO. Based on these
comparisons, we observed that the hot cores in the LMC appear
to show lower abundances of CH 3 CN relative to CH 3 OH compared to hot cores in the MW but higher abundances of SO 2 relative to SO. Although this study should be extended to a larger
sample of targets and evolutionary effects may play a role in
the observed abundances, the first results favor the idea that hot
cores in the LMC may be brighter in SO 2 lines compared to other
molecular species commonly found in hot cores. The comparison and correlation between CH 3 OH and SO 2 with SiO suggest
that shocks may play an important role in the observed abundances of these species.


_4.4._ _Location of hot cores in the LMC_


In Fig. 17, we show the location of all the detected hot cores
in the LMC. So far, all the hot cores associated with COMs are
located in the central region of the galaxy, which is known as

∼
the LMC bar. This region has a mildly higher ( 2%) metallicity
compared to the surrounding regions, as suggested by narrowband near-IR observations (Choudhury et al. 2021). Inspection
of the atomic(Kim et al. 1998; Smith et al. 2000), molecular gas
(e.g. Fukui et al. 1999), and dust maps (Meixner et al. 2013)
of the LMC revealed that the dense cold gas and dust are located within a zigzag shape in the bar region and surrounded by
bubbles of dispersed dust and gas (known as Hi holes; StaveleySmith et al. 2003). This implies that expanding material from
different sides results in compressed material into this zigzag region. Based on this observational evidence, we speculate that
star formation in the bar must have been triggered at some point
when the interstellar medium in the bar was enriched and the
metallicity was increased relative to other areas of the LMC.
This might explain the preferential detection of hot cores with
complex chemistry only toward the LMC bar.
For this scenario to be plausible, one needs to consider if the
ignition of the new generation of stars that resulted in the currently detected hot cores took place after the chemical enrichment of the interstellar medium of the LMC bar. Different works
in the literature explore the origin of the current distribution of
gas and dust in the bar region as well as the existence of possible
events in the history of the LMC that may have caused an increase of metallicity in the bar and the triggering of a new gener

Article number, page 16 of 90



ation of stars. In the following, we summarize the main findings
and connect them to the presence of hot cores in the LMC bar.
Hydrodynamic simulations (Tenorio-Tagle et al. 1986) infer the creation of Hi holes and shells as a result of the interaction between high-velocity clouds and the galactic disk. At the
same time, the study of the morphology and kinematics of stellar
populations and Hi gas in the LMC, SMC, Magellanic Bridge
(MB), and the Leading Arm (LA) suggests the interaction between the LMC and SMC (e.g. Zivick et al. 2019, and references
therein). Furthermore, numerical simulations of the evolution of
the Magellanic Clouds favor the sporadic replenishment of lowmetallicity gas from the SMC to the LMC’s disk over the last
2 Gyr as a result of their tidal interaction (known as Magellanic
Squall; Bekki & Chiba 2007). This stripped high-velocity gas
can be responsible for some of the Hi holes observable in the
LMC. Bekki & Chiba (2007) argues that the triggering of the
star formation could be a direct impact of clouds of the SMC interacting with those of the LMC. In addition, numerical models
of Besla et al. (2012) investigate the history of interaction between the SMC, LMC, and MW. Besla et al. (2012) argue that
the off-center warped stellar bar of the LMC and its one-armed
spiral can be explained by a recent direct collision with the SMC.
Given the uncertainties of the model parameters, the exact time
of the collision and its impact on star formation cannot be strictly
defined. However, a time range from 100 to 300 Myr seems a
reasonable approximation (Besla et al. 2012). Analysis of the
proper motions of stars from Gaia data supports the direct collision and suggests that this event was not a grazing interaction but
that the SMC went directly through the LMC, allowing the interstellar medium of both galaxies to interact (Zivick et al. 2019).
Furthermore, Choudhury et al. (2021) presumed that the mixing
of the metallicity of the two galaxies, caused by tidal interaction, could be a reason for the asymmetry metallicity distribution
observed in the LMC. With all this, and given the timescale of
formation of hot molecular cores (∼ 10 [5] yr, Wilner et al. 2001;
Furuya et al. 2005; Herbst & van Dishoeck 2009), the detected
hot cores in the LMC bar region have most likely been formed
in the inhomogeneous and slightly metallicity-richer interstellar
gas that emerged after the severe interactions of the LMC and
the SMC.


**5.** **Conclusions**


We have observed 20 star-forming sites distributed throughout
the LMC with ALMA in four frequency ranges between 241 and
260 GHz and at an angular resolution of ≈ 0 [′′] . 35 (corresponding
to 0.08 pc). We detected a total of 65 continuum cores whose
physical properties (e.g., mass, density, size) are presented in
Paper II. In this work, we have studied the chemical content of
these compact cores. The main findings are summarized as follows:


1. The extracted spectra at the location of the cores show different levels of chemical complexity in the cores. There are
cores with no molecular line emission and cores with singleline detection of dense or warm gas tracers, such as CS, SO,
or H [13] CO [+] . These include 28% of all the cores. In addition,
other cores contain CH 3 OH. These cores can be put into
two distinct groups: cores with emission lines from simple
molecules, such as SO 2,H 2 CS, H [13] CN, HC [15] N, and SiO, and
sources with detection of simple species and COMs, such as
CH 3 CN, or tentative detection of NH 2 CHO, CH 3 OCHO, and
CH 3 OCH 3 .

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud



2. The detection of multiple transitions from a single molecule
allowed for the determination of the temperature. The
CH 3 OH molecule, detected in 72% of the cores, is our main
temperature tracer in this study. We estimated the temperature with both LTE and non-LTE assumptions and compared
the two temperatures with the SO 2 temperature, where it was
reliably detected. Our temperature determination was further
confirmed by estimating the CH 3 CN temperature where it
was detected.
3. Molecular line width is a tracer of the gas kinematics. We
investigated the line width of different molecular species (fit
with XCLASS), and CH 3 OH showed the lowest line width
value in 51% of the cores. However, only a small sample of
cores showed an average line width above 5 km/s.
4. Comparing the abundance of different molecular species in
the 65 cores showed that S-bearing molecules are in general
more present and abundant than N- and O-bearing species.
Therefore, the detection of N- and O-bearing species, especially the COMs, needs higher sensitivity in future observations.
5. Four hot molecular cores were detected in this study, confirmed by their size (∼ 0.1pc), chemical richness, temperatures above 100 K, and high abundances of CH 3 OH and
SO 2 .


The four hot cores in our sample reveal the detection of one
new hot core, bringing the number of hot cores in the LMC to
seven. Shimonishi et al. (2023) suggest SO 2 as a tracer of hot
cores in a low-metallicity environment. Our survey study supports this suggestion by detecting strong lines of SO 2 and its
isotopologues only in the hot cores. We note that (six out of
the seven) hot cores with detections of methanol or other COMs
are preferentially located in the LMC bar. The metallicity-scaled
abundances of different molecular species in these hot cores
are comparable with those in the MW. Shimonishi et al. (2020)
have suggested the initial high dust temperature to be responsible for the lower abundances of COMs in the low metallicity
of the LMC. However, comparisons of our observed abundances
with the LMC hot core chemical models of Acharyya & Herbst
(2018) do not support high initial dust temperatures.


_Acknowledgements._ R.HG. acknowledges the German Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) for supporting this research through project SCHI 561/1-1. A.S.-M. acknowledges support from the
RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and
by the European Union ‘Next GenerationEU’/PRTR, as well as the program
Unidad de Excelencia María de Maeztu CEX2020-001058-M, and support from
the PID2020-117710GB-I00 (MCI-AEI-FEDER, UE). The material is based
upon work supported by NASA under award number 80GSFC21M0002 (M.S.).
G.A.F. gratefully acknowledges the Collaborative Research Center 1601 (SFB
1601 sub-project A1) funded by the DFG – 500700252. The authors acknowledge the comments provided by the anonymous referee which helped to improve
the manuscript.


**References**


Acharyya, K. & Herbst, E. 2018, ApJ, 859, 51
Arellano-Córdova, K. Z., Esteban, C., García-Rojas, J., & Méndez-Delgado, J. E.
2021, MNRAS, 502, 225
Bekki, K. & Chiba, M. 2007, MNRAS, 381, L16
Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013,
A&A, 559, A47
Besla, G., Kallivayalil, N., Hernquist, L., et al. 2012, MNRAS, 421, 2109
Cesaroni, R., Sánchez-Monge, Á., Beltrán, M. T., et al. 2017, A&A, 602, A59
Choudhury, S., de Grijs, R., Bekki, K., et al. 2021, MNRAS, 507, 4752
Choudhury, S., Subramaniam, A., Cole, A. A., & Sohn, Y. J. 2018, MNRAS,
475, 4279
Cioni, M. R. L., Clementini, G., Girardi, L., et al. 2011, A&A, 527, A116



Fontani, F., Colzi, L., Bizzocchi, L., et al. 2022, A&A, 660, A76
Fontani, F., Palau, A., Caselli, P., et al. 2011, A&A, 529, L7
Fukui, Y., Abe, R., Hara, A., et al. 1999, in New Views of the Magellanic Clouds,
ed. Y. H. Chu, N. Suntzeff, J. Hesser, & D. Bohlender, Vol. 190, 61
Furuya, R. S., Cesaroni, R., Takahashi, S., et al. 2005, ApJ, 624, 827
Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ, 682, 283
Gieser, C., Beuther, H., Semenov, D., et al. 2021, A&A, 648, A66
Gong, Y., Henkel, C., Menten, K. M., et al. 2023, A&A, 679, L6
Graczyk, D., Pietrzy´nski, G., Thompson, I. B., et al. 2014, ApJ, 780, 59
Gruendl, R. A. & Chu, Y.-H. 2009, ApJS, 184, 172
Helmich, F. P. & van Dishoeck, E. F. 1997, A&AS, 124, 205
Henize, K. G. 1956, ApJS, 2, 315
Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427
Jin, Y., Sutherland, R., Kewley, L. J., & Nicholls, D. C. 2023, ApJ, 958, 179
Kim, S., Staveley-Smith, L., Dopita, M. A., et al. 1998, ApJ, 503, 674
Kurtz, S., Cesaroni, R., Churchwell, E., Hofner, P., & Walmsley, C. M. 2000,
in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell,
299–326
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical
Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Meixner, M., Gordon, K. D., Indebetouw, R., et al. 2006, AJ, 132, 2268
Meixner, M., Panuzzo, P., Roman-Duval, J., et al. 2013, AJ, 146, 62
Minh, Y. C., Liu, H. B., & Galva´n-Madrid, R. 2016, ApJ, 824, 99
Möller, T., Bernst, I., Panoglou, D., et al. 2013, A&A, 549, A21
Möller, T., Endres, C., & Schilke, P. 2017, A&A, 598, A7
Möller, T., Schilke, P., Sánchez-Monge, Á., Schmiedeke, A., & Meng, F. 2023,
A&A, 676, A121
Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of
Molecular Structure, 742, 215
Nummelin, A., Bergman, P., Hjalmarson, Å., et al. 2000, ApJS, 128, 213
Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943
Pietrzy´nski, G., Graczyk, D., Gallenne, A., et al. 2019, Nature, 567, 200
Qin, S.-L., Liu, T., Liu, X., et al. 2022, MNRAS, 511, 3463
Robitaille, T., Ginsburg, A., Beaumont, C., Leroy, A., & Rosolowsky, E. 2016,
spectral-cube: Read and analyze astrophysical spectral data cubes, Astrophysics Source Code Library, record ascl:1609.017
Sánchez-Monge, Á., Kurtz, S., Palau, A., et al. 2013a, ApJ, 766, 114
Sánchez-Monge, Á., López-Sepulcre, A., Cesaroni, R., et al. 2013b, A&A, 557,
A94
Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A,
321, 293
Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005,
A&A, 432, 369
Seale, J. P., Looney, L. W., Chu, Y.-H., et al. 2009, ApJ, 699, 150
Seale, J. P., Meixner, M., Sewiło, M., et al. 2014, AJ, 148, 124
Selier, R. & Heydari-Malayeri, M. 2012, A&A, 545, A29
Sewiło, M., Cordiner, M., Charnley, S. B., et al. 2022, ApJ, 931, 102
Sewiło, M., Indebetouw, R., Charnley, S. B., et al. 2018, ApJ, 853, L19
Shimonishi, T., Dartois, E., Onaka, T., & Boulanger, F. 2016a, A&A, 585, A107
Shimonishi, T., Das, A., Sakai, N., et al. 2020, ApJ, 891, 164
Shimonishi, T., Izumi, N., Furuya, K., & Yasui, C. 2021, ApJ, 922, 206
Shimonishi, T., Onaka, T., Kawamura, A., & Aikawa, Y. 2016b, ApJ, 827, 72
Shimonishi, T., Tanaka, K. E. I., Zhang, Y., & Furuya, K. 2023, ApJ, 946, L41
Smith, C., Leiton, R., & Pizarro, S. 2000, in Astronomical Society of the Pacific
Conference Series, Vol. 221, Stars, Gas and Dust in Galaxies: Exploring the
Links, ed. D. Alloin, K. Olsen, & G. Galaz, 83
Staveley-Smith, L., Kim, S., Calabretta, M. R., Haynes, R. F., & Kesteven, M. J.
2003, MNRAS, 339, 87
Sutton, E. C., Peng, R., Danchi, W. C., et al. 1995, ApJS, 97, 455
Tenorio-Tagle, G., Bodenheimer, P., Rozyczka, M., & Franco, J. 1986, A&A,
170, 107
Treviño-Morales, S. P., Pilleri, P., Fuente, A., et al. 2014, A&A, 569, A19
van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck,
E. F. 2007, A&A, 468, 627
Welty, D. E., Federman, S. R., Gredel, R., Thorburn, J. A., & Lambert, D. L.
2006, ApJS, 165, 138
Wilner, D. J., De Pree, C. G., Welch, W. J., & Goss, W. M. 2001, ApJ, 550, L81
Zivick, P., Kallivayalil, N., Besla, G., et al. 2019, ApJ, 874, 78


Article number, page 17 of 90

_A&A proofs:_ manuscript no. aanda



300


250


200


150


100


50


0


200


150


100


50


0


200


150


100


50


0



|Rotational Temperatures for 4A / ST16|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
|||||CH3OH<br>~~SO~~2<br>CHCN|CH3OH<br>~~SO~~2<br>CHCN|CH3OH<br>~~SO~~2<br>CHCN|
||||||3<br>~~Hot CH~~3~~OH~~<br>Hot SO2||
||||||||
||||||||
||||||||


this paper Shimonishi+20

Source

|Rotational Temperatures for 6A / N105-2B|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|CH3OH<br>SO2<br>CHCN|
|||||||3<br>Hot CH3OH<br>Hot SO2||
|||||||||
|||||||||
|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|o+22|



Source

|Rotational Temperatures for 6B / N105-2A|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||
|||||||||||~~CH~~3~~OH~~<br>SO2<br>CHCN|||
||||||||||3<br>Hot CH3OH<br>Hot SO2|3<br>Hot CH3OH<br>Hot SO2|3<br>Hot CH3OH<br>Hot SO2||
||||||||||||||
||||||||||||||
||||||||||||||
|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|this paper<br>Sewi|o+22|



Source



10 7


10 8


10 9


10 10


10 11


10 7


10 8


10 9


10 10


10 11


10 7


10 8


10 9


10 10


10 11



|Molecular Abundances for 4A / ST16|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|~~Shimonishi+20~~|
|this paper|this paper|this paper|this paper|this paper|this paper|this paper|this paper|this paper|
||||||||||
||||||||||
|CH3<br>|OH CH3<br>Molecu|CN<br>HN<br>lar Ab|CO H13C<br>Mole<br> undanc|O +<br>SO<br>cule<br> es for|2<br>S<br>  6A / N|O<br>Si<br>   105-2B|O<br>Si<br>   105-2B|O<br>|
|||||||~~Sewi o+~~|~~Sewi o+~~|~~ 22~~|
|||||||this pap|this pap|er|
||||||||||
||||||||||
||||||||||
|CH3<br>|OH CH3<br>Molecu|CN<br>HN<br>lar Ab|CO H13C<br>Mole<br> undanc|O +<br>SO<br>cule<br> es for|2<br>S<br>  6B / N|O<br>Si<br>   105-2A|O<br>Si<br>   105-2A|O<br>|
|||||||||~~ 22~~|
|||||||~~Sewi~~|~~ o+~~|~~ 22~~|
|||||||this pap|this pap|er|
||||||||||
||||||||||
||||||||||


CH 3 OH CH 3 CN HNCO H [13] CO [+] SO 2 SO SiO

Molecule



Fig. 12: Comparisons of the derived temperatures (left) and abundances (right) from the current study and the literature. The top
panels show a comparison of 4A and ST16 (Shimonishi et al. 2020), the middle panels show 6A and N105-2B, and the bottom
panels show 6B and N105-2A (Sewiło et al. 2022). An error range of 40% is depicted for the temperatures and column densities
from the current paper.


Article number, page 18 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Molecular Abundances for LMC's Hot Cores



10 8


10 9





10 10


10 11


paper.











10 [6]










|Col1|Col2|Col3|Col4|Col5|Col6|Col7|ST11 4A 6A|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||6B<br>14A<br>N113 A1<br>N113 B3|6B<br>14A<br>N113 A1<br>N113 B3|
||||||||||
||all the <br>          16a), 4<br>on. An <br> Tempe|H13CO +<br>Molecule<br>known hot c<br>           A, 6A, 6B a<br> error range <br> rature = 1|H13CO +<br>Molecule<br>known hot c<br>           A, 6A, 6B a<br> error range <br> rature = 1|H13CO +<br>Molecule<br>known hot c<br>           A, 6A, 6B a<br> error range <br> rature = 1|H13CO +<br>Molecule<br>known hot c<br>           A, 6A, 6B a<br> error range <br> rature = 1|H13CO +<br>Molecule<br>known hot c<br>           A, 6A, 6B a<br> error range <br> rature = 1|SO<br>S<br> scaling to the ga<br>                   N113 A1 and N<br>e abundances fr|SO<br>S<br> scaling to the ga<br>                   N113 A1 and N<br>e abundances fr|
||||||||||
||||||||||
||||||||||
||106<br>  105<br> Tempe|Time (yr)<br> rature = 2|Time (yr)<br> rature = 2|Time (yr)<br> rature = 2|Time (yr)<br> rature = 2|Time (yr)<br> rature = 2|106<br>5<br>Time (yr)|106<br>5<br>Time (yr)|
||||||||||
||||||||||
||||||||||





9 × 10 [5] 2 × 10 [6]
10 [6]


Time (yr)





Fig. 14: Comparisons of abundances for SO 2, CH 3 OH, and CH 3 CN from observations of the seven hot cores detected in this
galaxy and the LMC hot core models for the final hot core temperature of 100 K ( _top_ ) and 200 K ( _bottom_ ). The black curves show
abundances over time for an initial dust temperature of 10 (dotted curve), 15 (dashed curve), 20 (larger dashed curve), and 25 K
(the solid curve). The horizontal colored line shows the single abundance value for each hot core and follows the same color code
as Fig. 13 (see the text for more details).


Article number, page 19 of 90

_A&A proofs:_ manuscript no. aanda


Molecular Abundances for a sample of hot cores in the SMC, LMC and MW



10 6


10 7


10 8


10 9


10 10


10 11





10 12


CH 3 OH CH3CN SO 2 SiO

Molecule


Fig. 15: Abundances of CH 3 OH, CH 3 CN, SO 2, and SiO for all known hot cores in the SMC and LMC and for a selection of Galactic
hot cores. The SMC hot cores are included, S07 and S09 (Shimonishi et al. 2023). The LMC hot cores are ST11 (Shimonishi et al.
2016a), 4A, 6A, 6B and 14A (this work), and N113 A1 and N113 B (Sewiło et al. 2022). We selected four Galactic hot cores: an
outer Galaxy hot core (Shimonishi et al. 2020), Orion Hot Core (HC) (Sutton et al. 1995), Sgr B2(N) (Nummelin et al. 2000), and
W3(H 2 O) (Helmich & van Dishoeck 1997). The extent of each bar with a dotted pattern represents the abundances scaled to the
Galactic metallicity.


Article number, page 20 of 90

10 5



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


10 6









10 7


10 8


10 9







10 5


10 6


10 7


10 8


10 9


10 10













10 10 11 13 10 11 10 9 10 7


N(SiO)/N(H 2 )





Fig. 17: Three color composite image of the LMC combining 3.6
µm (blue), 4.5 µm (green), and 5.8 µm (red Meixner et al. 2006)
images to highlight the position of the stellar bar. The dashed
ellipse marks the bar region. The 20 ALMA fields from the current study are overlaid with white circles 15 times larger than
the field of view of our ALMA observations. The fields accommodating hot cores are highlighted in yellow, including the YSO
ST16 and N105 star-forming region. The field marked with a
star shows the position of the new hot core detected in our survey. The location of the hot cores in N105 (Sewiło et al. 2022)
and N113 (Sewiło et al. 2018) are marked with yellow rectangles. The hot cores ST11 (Shimonishi et al. 2016b) and ST16
(Shimonishi et al. 2020) are shown with yellow plus signs. The
hot core ST11 with no COMs is the only hot core detected out
of the LMC bar.


Article number, page 21 of 90



Fig. 16: Comparisons of the abundances of CH 3 OH and CH 3 CN
and SO 2 and SO for the hot cores in the SMC (open green circles), LMC (red rectangles), and MW (black triangles for inner
Galactic hot cores and gray triangle for outer Galactic hot core).
Dashed lines show abundance relations of 1:1 for the top-right
panel and 1:100 for the other panels. The dotted lines show a
variation of a factor of ten above and below the relations described by the dashed lines.

_A&A proofs:_ manuscript no. aanda


**Appendix A:** **Spectra and XCLASS fits for 1.2 mm continuum cores**


Figures A.1 to A.20 show the ALMA Band 6 spectra observed toward the all cores with identified molecular lines (except the core
14B) in the 20 fields observed throughout the LMC. The observed spectra with line detections were fit using the XCLASS software
(see Section 3.1), and the results are shown as a black solid line on top of the observed spectra. The molecular species detected in
the spectra are marked in black, while the tentative detections are marked in gray.


Article number, page 22 of 90

1.50


1.25



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 1: 053941.12-692916.8 - A (1A)



1.00


0.75


0.50


0.25


0.00


0.25


0.50
241.6 241.7 241.8 241.9 242.0


7


6


5


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


3.0


2.5


2.0


1.5


1.0


0.5


0.0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


1.0


0.8


0.6


0.4


0.2


0.0


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.1: ALMA Band 6 observed spectra toward source 1A overlaid with the best-fit XCLASS model. Molecular transitions with
definite detections (S/N > 5) are represented by solid black lines, while those with tentative detections (3 < S/N < 5) are denoted by
dotted gray lines. Dotted red lines indicate transitions of molecules for which abundance upper limits are provided. (See Section 3.1
for more details.)

Article number, page 23 of 90

0.6


0.4


0.2


0.0


0.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2


0.6


0.4


0.2


0.0


0.2


0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3



|Field 2: 045640.79-663230.5 - A (2A)|Col2|
|---|---|
|SO2<br>CH3OH<br>ALMA observation<br>XCLASS fit|SO2<br>CH3OH<br>ALMA observation<br>XCLASS fit|
|241.6<br>241.7<br>241.8|241.9<br>242.0|
|SO2<br>CS|SO2<br>CS|


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.2: Same as Fig. A.1 but for source 2A.



_A&A proofs:_ manuscript no. aanda



Article number, page 24 of 90

2.0


1.5


1.0


0.5


0.0


4


3


2


1


0


2.5


2.0


1.5


1.0


0.5


0.0


0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.2



|Field 2: 045640.79-663230.5 - B (2B)|Col2|
|---|---|
|SO2<br>CH3OH<br>ALMA observation<br>XCLASS fit|SO2<br>CH3OH<br>ALMA observation<br>XCLASS fit|
|241.6<br>241.7<br>241.8|241.9<br>242.0|
|CH3OH<br>H2CS<br>SO2<br>SO2<br>CS|CH3OH<br>H2CS<br>SO2<br>SO2<br>CS|


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.2: Same as Fig. A.1 but for source 2B.


Article number, page 25 of 90



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud

1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2


3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3


0.2


0.1


0.0


0.1


0.2



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.2: Same as Fig. A.1 but for source 2C.



_A&A proofs:_ manuscript no. aanda


Field 2: 045640.79-663230.5 - C (2C)



Article number, page 26 of 90

0.6


0.4


0.2


0.0


0.2


2.5


2.0


1.5


1.0


0.5


0.0


0.2


0.1


0.0


0.1



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 2: ST10 - D (2D)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.2

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.4


0.3


0.2


0.1


0.0


0.1


0.2



0.3



259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(d)


Fig. A.2: Same as Fig. A.1 but for source 2D.


Article number, page 27 of 90

0.6


0.4


0.2


0.0


0.2


1.0


0.8


0.6


0.4


0.2


0.0


0.3


0.2


0.1


0.0


0.1


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(e)


Fig. A.2: Same as Fig. A.1 but for source 2E.



_A&A proofs:_ manuscript no. aanda


Field 2: 045640.79-663230.5 - E (2E)



Article number, page 28 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 2: 045640.79-663230.5 - F (2F)



0.2


0.1


0.0


0.1


0.2


0.3


0.3


0.2


0.1


0.0


0.1


0.2


0.2


0.1


0.0


0.1


0.2


0.3


0.2


0.1


0.0


0.1


0.2



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(f)


Fig. A.2: Same as Fig. A.1 but for source 2F.


Article number, page 29 of 90

1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2



_A&A proofs:_ manuscript no. aanda


Field 3: 052343.48-680033.9 - A (3A)



241.6 241.7 241.8 241.9 242.0



5


4


3


2


1


0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


1.0


0.8


0.6


0.4


0.2


0.0


0.2



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.3: Same as Fig. A.1 but for source 3A.



Article number, page 30 of 90

0.6



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 3: 052343.48-680033.9 - B (3B)



0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.2
241.6 241.7 241.8 241.9 242.0


1.50


1.25


1.00


0.75


0.50


0.25


0.00


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.8


0.6


0.4


0.2


0.0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.3: Same as Fig. A.1 but for source 3B.


Article number, page 31 of 90

0.8



_A&A proofs:_ manuscript no. aanda


Field 3: 052343.48-680033.9 - C (3C)



0.6


0.4


0.2


0.0


0.2


241.6 241.7 241.8 241.9 242.0


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2
244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.15


0.10


0.05


0.00


0.05


0.10


0.15


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.3: Same as Fig. A.1 but for source 3C.



Article number, page 32 of 90

0.8



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 3: 052343.48-680033.9 - D (3D)



0.6


0.4


0.2


0.0


0.2


241.6 241.7 241.8 241.9 242.0


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2
244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(d)


Fig. A.3: Same as Fig. A.1 but for source 3D.


Article number, page 33 of 90

_A&A proofs:_ manuscript no. aanda


Field 4: 051912.27-690907.3 - A (4A)



3.0


2.5


2.0


1.5


1.0


0.5


0.0







0.5

241.6 241.7 241.8 241.9 242.0


8


6


4


2


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


10


8


6





4


2


0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0



257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.4: Same as Fig. A.1 but for source 4A.



Article number, page 34 of 90

0.4


0.3


0.2


0.1


0.0


0.1



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 5: 045358.57-691106.7 - A (5A)



0.2
241.6 241.7 241.8 241.9 242.0


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2

244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.3


0.2


0.1


0.0


0.1


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.4


0.3


0.2


0.1


0.0


0.1



0.2

258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.5: Same as Fig. A.1 but for source 5A.


Article number, page 35 of 90

1.0


0.8


0.6


0.4


0.2


0.0


0.2



_A&A proofs:_ manuscript no. aanda


Field 5: 045358.57-691106.7 - B (5B)



0.4
241.6 241.7 241.8 241.9 242.0


6


5


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


2.5


2.0


1.5


1.0


0.5


0.0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.6


0.4


0.2


0.0


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.5: Same as Fig. A.1 but for source 5B.



Article number, page 36 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 6: 050953.89-685336.7 - A (6A)



3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.5


14


12


10


8


6


4


2


0


15.0


12.5


10.0


7.5


5.0


2.5


0.0


4


3


2


1


0







241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75





257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.6: Same as Fig. A.1 but for source 6A.


Article number, page 37 of 90

_A&A proofs:_ manuscript no. aanda





2.0


1.5


1.0


0.5


0.0



0.5


10


8


6


4


2


0

|Field 6: 050953.89-685336.7 - B (6B)|Col2|
|---|---|
|HNCO<br>CH3OCH3<br>34SO2<br>CH3OH<br>SO2<br>ALMA observation<br>XCLASS fit|HNCO<br>CH3OCH3<br>34SO2<br>CH3OH<br>SO2<br>ALMA observation<br>XCLASS fit|
|241.6<br>241.7<br>241|.8<br>241.9<br>242.0|



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


7


6


5


4



3


2


1


0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.5





257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.6: Same as Fig. A.1 but for source 6B.



Article number, page 38 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 6: 050953.89-685336.7 - C (6C)





2.0


1.5


1.0


0.5


0.0



0.5
241.6 241.7 241.8 241.9 242.0


12


10


8


6


4


2


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


2.5


2.0


1.5


1.0


0.5


0.0


0.5
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


1.0


0.8


0.6


0.4


0.2


0.0


0.2


0.4


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.6: Same as Fig. A.1 but for source 6C.


Article number, page 39 of 90

5


4


3


2


1


0


10


8


6


4


2


0


2.0


1.5


1.0


0.5


0.0


0.5


1.00


0.75


0.50


0.25


0.00


0.25


0.50


0.75



_A&A proofs:_ manuscript no. aanda


Field 6: 050953.89-685336.7 - D (6D)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(d)


Fig. A.6: Same as Fig. A.1 but for source 6D.



Article number, page 40 of 90

5


4


3


2


1


0


10


8


6


4


2


0


2.5


2.0


1.5


1.0


0.5


0.0


0.6


0.4


0.2


0.0


0.2



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 6: Y050953.89-685336.7 - E (6E)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(e)


Fig. A.6: Same as Fig. A.1 but for source 6E.


Article number, page 41 of 90

1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


1.2


1.0


0.8


0.6


0.4


0.2


0.0



_A&A proofs:_ manuscript no. aanda


Field 6: 050953.89-685336.7 - F (6F)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.2

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.6


0.4


0.2


0.0


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(f)


Fig. A.6: Same as Fig. A.1 but for source 6F.



Article number, page 42 of 90

1.75


1.50


1.25


1.00


0.75


0.50


0.25


0.00



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 7: 052423.39-693904.7 - A (7A)



0.25

241.6 241.7 241.8 241.9 242.0


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


1.75


1.50


1.25


1.00


0.75


0.50


0.25


0.00


0.25
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.8


0.6


0.4


0.2


0.0


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.7: Same as Fig. A.1 but for source 7A.


Article number, page 43 of 90

_A&A proofs:_ manuscript no. aanda


Field 7: 052423.39-693904.7 - B (7B)





0.4


0.2


0.0


0.2


0.4


0.6


0.4


0.2


0.0


0.2


0.2


0.1


0.0


0.1


0.2


0.3


0.2


0.1


0.0


0.1


0.2


0.3



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.7: Same as Fig. A.1 but for source 7B.



Article number, page 44 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 7: 052423.39-693904.7 - C (7C)



0.3





0.2


0.1


0.0


0.1


0.2


241.6 241.7 241.8 241.9 242.0


0.8


0.6


0.4


0.2


0.0


0.2
244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.15


0.10


0.05


0.00


0.05


0.10


0.15
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.7: Same as Fig. A.1 but for source 7C.


Article number, page 45 of 90

_A&A proofs:_ manuscript no. aanda


Field 8: 044854.41-690948.3 - A (8A)





2.5


2.0


1.5


1.0


0.5


0.0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


2.0


1.5


1.0


0.5


0.0


0.3


0.2


0.1


0.0


0.1



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



0.2

258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.8: Same as Fig. A.1 but for source 8A.



Article number, page 46 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 8: 044854.41-690948.3 - C (8C)





2.5


2.0


1.5


1.0


0.5


0.0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2


0.2


0.1


0.0


0.1


0.2



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.8: Same as Fig. A.1 but for source 8C.


Article number, page 47 of 90

_A&A proofs:_ manuscript no. aanda


Field 9: 054248.90-694446.3 - A (9A)





2.5


2.0


1.5


1.0


0.5


0.0



0.5
241.6 241.7 241.8 241.9 242.0


5


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


1.0


0.8


0.6


0.4


0.2


0.0


0.2
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.4


0.3


0.2


0.1


0.0


0.1



0.2

258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.9: Same as Fig. A.1 but for source 9A.



Article number, page 48 of 90

1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 10: 051916.87-693757.5 - A (10A)



0.2

241.6 241.7 241.8 241.9 242.0


3.0


2.5


2.0


1.5


1.0


0.5


0.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.8


0.6


0.4


0.2


0.0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.6


0.5


0.4


0.3


0.2


0.1


0.0


0.1


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.10: Same as Fig. A.1 but for source 10A.


Article number, page 49 of 90

_A&A proofs:_ manuscript no. aanda


Field 10: 051916.87-693757.5 - B (10B)



0.4


0.2


0.0


0.2


0.4





0.6
241.6 241.7 241.8 241.9 242.0


1.5


1.0


0.5


0.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.3


0.2


0.1


0.0


0.1


0.2


0.3


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.4


0.2


0.0


0.2


0.4


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.10: Same as Fig. A.1 but for source 10B.



Article number, page 50 of 90

1.0


0.8



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 10: Y051916.87-693757.5 - C (10C)



0.6


0.4


0.2


0.0


0.2


0.4
241.6 241.7 241.8 241.9 242.0


1.75


1.50


1.25


1.00


0.75


0.50


0.25


0.00


0.25
244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.15


0.10


0.05


0.00


0.05


0.10


0.15


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.10: Same as Fig. A.1 but for source 10C.


Article number, page 51 of 90

1.0


0.8


0.6


0.4


0.2


0.0


0.2



_A&A proofs:_ manuscript no. aanda


Field 10: 051916.87-693757.5 - D (10D)



0.4
241.6 241.7 241.8 241.9 242.0



1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2


0.2


0.1


0.0


0.1


0.2


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(d)


Fig. A.10: Same as Fig. A.1 but for source 10D.



Article number, page 52 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 11: 045100.16-691934.4 - B (11B)





5


4


3


2


1


0


6


5


4


3


2


1


0


2.0


1.5


1.0


0.5


0.0


0.2


0.1


0.0


0.1


0.2



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.11: Same as Fig. A.1 but for source 11B.


Article number, page 53 of 90

1.0


0.8


0.6


0.4


0.2


0.0



_A&A proofs:_ manuscript no. aanda


Field 11: 045100.16-691934.4 - C (11C)



0.2
241.6 241.7 241.8 241.9 242.0



1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.3


0.2


0.1


0.0


0.1


0.25


0.20


0.15


0.10


0.05


0.00


0.05


0.10



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.11: Same as Fig. A.1 but for source 11C.



Article number, page 54 of 90

4.0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 11: 045100.16-691934.4 - D (11D)



0.5
241.6 241.7 241.8 241.9 242.0


6


5


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.11: Same as Fig. A.1 but for source 11D.


Article number, page 55 of 90

1.2


1.0


0.8


0.6


0.4


0.2


0.0



_A&A proofs:_ manuscript no. aanda



0.2


2.5


2.0


1.5


1.0


0.5


0.0

|Field 12: 050355.87-672045.1 - A (12A)|Col2|
|---|---|
|CH3OH<br>ALMA observation<br>XCLASS fit|CH3OH<br>ALMA observation<br>XCLASS fit|
|2416<br>2417<br>2418|2419<br>2420|



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.8


0.6


0.4


0.2


0.0


0.2


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.3


0.2


0.1


0.0


0.1


0.2



0.3



259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.12: Same as Fig. A.1 but for source 12A.



Article number, page 56 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 12: 050355.87-672045.1 - B (12B)



0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3


0.4


0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3


0.4


0.2


0.0


0.2





241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.4

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.12: Same as Fig. A.1 but for source 12B.


Article number, page 57 of 90

_A&A proofs:_ manuscript no. aanda


Field 12: 050355.87-672045.1 - C (12C)



0.4


0.3


0.2


0.1


0.0


0.1


0.2





0.3
241.6 241.7 241.8 241.9 242.0


1.0


0.8


0.6


0.4


0.2


0.0


0.2


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.3


0.2


0.1


0.0


0.1


0.2


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


0.2


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.12: Same as Fig. A.1 but for source 12C.



Article number, page 58 of 90

1.0


0.8


0.6


0.4


0.2


0.0


0.2



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 12: 050355.87-672045.1 - D (12D)



0.4
241.6 241.7 241.8 241.9 242.0


1.0


0.8


0.6


0.4


0.2


0.0


0.2


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.3


0.2


0.1


0.0


0.1


0.2


0.3
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.3


0.2


0.1


0.0


0.1


0.2


0.3


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(d)


Fig. A.12: Same as Fig. A.1 but for source 12D.


Article number, page 59 of 90

3.0


2.5


2.0


1.5


1.0


0.5


0.0


5


4


3


2


1


0


1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0



_A&A proofs:_ manuscript no. aanda


Field 13: 053952.11-710930.7 - A (13A)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.2

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.4


0.3


0.2


0.1


0.0


0.1


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.13: Same as Fig. A.1 but for source 13A.



Article number, page 60 of 90

4.0


3.5



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 13: Y053952.11-710930.7 - C (13C)



3.0


2.5


2.0


1.5


1.0


0.5


0.0


241.6 241.7 241.8 241.9 242.0


6


5


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.2
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.25


0.20


0.15


0.10


0.05


0.00


0.05


0.10


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.13: Same as Fig. A.1 but for source 13C.


Article number, page 61 of 90

_A&A proofs:_ manuscript no. aanda


Field 13: 053952.11-710930.7 - D (13D)



0.8


0.6


0.4


0.2


0.0


0.2


0.4


0.6


3.0


2.5


2.0


1.5


1.0


0.5


0.0





241.6 241.7 241.8 241.9 242.0



0.5

244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


2.0


1.5


1.0


0.5


0.0


0.5

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.6


0.4


0.2


0.0


0.2


0.4


0.6


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.13: Same as Fig. A.1 but for source 13D.



Article number, page 62 of 90

0.6


0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.2


1.6


1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.125


0.100


0.075


0.050


0.025


0.000


0.025


0.050


0.075


0.10


0.05


0.00


0.05


0.10



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 13: 051916.87-693757.5 - E (13E)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(d)


Fig. A.13: Same as Fig. A.1 but for source 13E.


Article number, page 63 of 90

3.0


2.5


2.0


1.5


1.0


0.5


0.0


5


4


3


2


1


0


1.0


0.8


0.6


0.4


0.2


0.0



_A&A proofs:_ manuscript no. aanda


Field 13: 051916.87-693757.5 - F (13F)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.2

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(e)


Fig. A.13: Same as Fig. A.1 but for source 13F.



Article number, page 64 of 90

2.0


1.5


1.0


0.5


0.0


2.0


1.5


1.0


0.5


0.0


0.6


0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 13: 051916.87-693757.5 - G (13G)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(f)


Fig. A.13: Same as Fig. A.1 but for source 13G.


Article number, page 65 of 90

1.0


0.8



_A&A proofs:_ manuscript no. aanda


Field 13: 051916.87-693757.5 - H (13H)



0.6


0.4


0.2


0.0


0.2


0.4
241.6 241.7 241.8 241.9 242.0


1.50


1.25


1.00


0.75


0.50


0.25


0.00


0.25
244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.15


0.10


0.05


0.00


0.05


0.10


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(g)


Fig. A.13: Same as Fig. A.1 but for source 13H.



Article number, page 66 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 13: 051916.87-693757.5 - K (13K)



0.2


0.1


0.0


0.1


0.2


0.8


0.6


0.4


0.2


0.0


0.10


0.05


0.00


0.05


0.10


0.15


0.10


0.05


0.00


0.05


0.10


0.15





241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75



258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(h)


Fig. A.13: Same as Fig. A.1 but for source 13K.


Article number, page 67 of 90

_A&A proofs:_ manuscript no. aanda


Field 14: 052333.40-693712.1 - B (14B)



0.4


0.2


0.0


0.2


0.4


0.6





241.6 241.7 241.8 241.9 242.0


0.3


0.2


0.1


0.0


0.1


0.2


0.3


0.4


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.3


0.2


0.1


0.0


0.1


0.2


0.3


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.14: ALMA Band 6 observed spectra toward source 14B with no emission line detections. (See Section 3.1 for more details.)


Article number, page 68 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud





1.25


1.00


0.75


0.50


0.25


0.00


0.25


0.50


7


6


5


4


3


2


1


0





1

|Field 15: 051344.99-693510.6 - A (15A)|Col2|
|---|---|
|SO2<br>CH3OH<br>ALMA observation<br>XCLASS fit|SO2<br>CH3OH<br>ALMA observation<br>XCLASS fit|
|241.6<br>241.7<br>24|1.8<br>241.9<br>242.0|
|CS|CS|



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.5


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


1.5


1.0


0.5


0.0


0.5


1.0


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.15: Same as Fig. A.1 but for source 15A.


Article number, page 69 of 90

2.5


2.0


1.5


1.0


0.5


0.0


4.0


3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.8


0.6


0.4


0.2


0.0



_A&A proofs:_ manuscript no. aanda


Field 15: 051344.99-693510.6 - B (15B)



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.2
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.3


0.2


0.1


0.0


0.1


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.15: Same as Fig. A.1 but for source 15B.



Article number, page 70 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 15: 051344.99-693510.6 - C (15C)



0.3





0.2


0.1


0.0


0.1


0.2


0.3
241.6 241.7 241.8 241.9 242.0


1.50


1.25


1.00


0.75


0.50


0.25


0.00


0.25
244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.15: Same as Fig. A.1 but for source 15C.


Article number, page 71 of 90

1.2


1.0



_A&A proofs:_ manuscript no. aanda


Field 16: 054629.32-693514.2 - B (16B)



0.8


0.6


0.4


0.2


0.0


0.2


0.4
241.6 241.7 241.8 241.9 242.0


1.50


1.25


1.00


0.75


0.50


0.25


0.00


0.25

244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.4


0.3


0.2


0.1


0.0


0.1


0.2

257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.2


0.1


0.0


0.1


0.2


258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.16: Same as Fig. A.1 but for source 16B.



Article number, page 72 of 90

2.5


2.0


1.5


1.0


0.5


0.0



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 17: 054826.21-700850.2 - A (17A)



0.5
241.6 241.7 241.8 241.9 242.0


8


7


6


5


4


3


2


1


0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


2.5


2.0


1.5


1.0


0.5


0.0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.4


0.3


0.2


0.1


0.0


0.1


0.2

258.75 259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.17: Same as Fig. A.1 but for source 17A.


Article number, page 73 of 90

2.0


1.5


1.0


0.5


0.0



_A&A proofs:_ manuscript no. aanda


Field 18: 045622.61-663656.9 - A (18A)



0.5
241.6 241.7 241.8 241.9 242.0



5


4


3


2


1


0


1.50


1.25


1.00


0.75


0.50


0.25


0.00



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75



0.25
257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.2


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.18: Same as Fig. A.1 but for source 18A.



Article number, page 74 of 90

1.0


0.8


0.6


0.4


0.2


0.0


0.2



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 18: 045622.61-663656.9 - B (18B)



241.6 241.7 241.8 241.9 242.0



4


3


2


1


0


0.4


0.3


0.2


0.1


0.0


0.1


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.18: Same as Fig. A.1 but for source 18B.


Article number, page 75 of 90

1.0


0.8


0.6


0.4


0.2


0.0


0.2



_A&A proofs:_ manuscript no. aanda


Field 18: 045622.61-663656.9 - C (18C)



241.6 241.7 241.8 241.9 242.0



2.0


1.5


1.0


0.5


0.0


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.15


0.10


0.05


0.00


0.05


0.10


0.15



244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.18: Same as Fig. A.1 but for source 18C.



Article number, page 76 of 90

5


4


3


2


1


0


7


6


5


4


3


2


1


0


2.0


1.5


1.0


0.5


0.0


0.3


0.2


0.1


0.0


0.1


0.2


0.3



241.6 241.7 241.8 241.9 242.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.19: Same as Fig. A.1 but for source 19A.


Article number, page 77 of 90



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 19: 045406.43-664601.4 - A (19A)

_A&A proofs:_ manuscript no. aanda


Field 19: 045406.43-664601.4 - C (19C)



0.3





0.2


0.1


0.0


0.1


0.2


0.3
241.6 241.7 241.8 241.9 242.0


0.5


0.4


0.3


0.2


0.1


0.0


0.1


0.2

244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(b)


Fig. A.19: Same as Fig. A.1 but for source 19C.



Article number, page 78 of 90

1.50


1.25


1.00


0.75


0.50


0.25


0.00



Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Field 19: 045406.43-664601.4 - D (19D)



0.25
241.6 241.7 241.8 241.9 242.0


2.5


2.0


1.5


1.0


0.5


0.0


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.8


0.6


0.4


0.2


0.0


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.20


0.15


0.10


0.05


0.00


0.05


0.10


0.15


0.20


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(c)


Fig. A.19: Same as Fig. A.1 but for source 19D.


Article number, page 79 of 90

_A&A proofs:_ manuscript no. aanda


Field 20: 052210.08-673459.6 - A (20A)



0.15


0.10


0.05


0.00


0.05


0.10


0.15





241.6 241.7 241.8 241.9 242.0


0.20


0.15


0.10


0.05


0.00


0.05


0.10


244.00 244.25 244.50 244.75 245.00 245.25 245.50 245.75


0.10


0.05


0.00


0.05


0.10


257.00 257.25 257.50 257.75 258.00 258.25 258.50 258.75


0.10


0.05


0.00


0.05


0.10


259.00 259.25 259.50 259.75 260.00 260.25 260.50

Frequency (GHz)


(a)


Fig. A.20: Same as Fig. A.1 but for source 20A.



Article number, page 80 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


**Appendix B:** **XCLASS fits parameters**


In Table B.1, we list the parameters assuming LTE conditions for the CH 3 OH, and Table B.2 collects the fit parameters for CH 3 OH
in non-LTE. We used the non-LTE temperature for methanol to fit other molecules. Therefore, the fit parameters for other molecules
are only presented in Table B.2. (For more details, see Section 3.1.) Figure B.1 compares the LTE and non-LTE fit for two methanol
lines at 241.767 and 241.792 for two sources, 2C and 14A. While methanol is fit with one component in 2C, 14A gets the best-fitting
results with two components for methanol, where the cold foreground component (the envelope) is assumed to be in non-LTE.



1.5


1.0


0.5


0.0


1.0


0.5


0.0



1.2


1.0


0.8


0.6


0.4


0.2


0.0


0.50


0.25


0.00



Field 2: 045640.79-663230.5 - C (2C)



Field 14: 052333.40-693712.1 - A (14A)


|ALMA observation<br>LTE CH3OH<br>nonLTE CH3OH|Col2|Col3|Col4|
|---|---|---|---|
|ALMA observation<br>LTE CH3OH<br>nonLTE CH3OH|ALMA observation<br>LTE CH3OH<br>nonLTE CH3OH|||
|LTE CH3OH<br>nonLTE CH3OH|LTE CH3OH<br>nonLTE CH3OH|||
|||||


|Col1|ALMA observation<br>LTE envelope CH3OH<br>nonLTE envelope CH3OH|
|---|---|
||LTE envelope CH3OH<br>nonLTE envelope CH3OH|
|||



241.75 241.76 241.77 241.78 241.79 241.80 241.81

Frequency (GHz)



241.75 241.76 241.77 241.78 241.79 241.80 241.81

Frequency (GHz)



Fig. B.1: Comparisons of the LTE and non-LTE fit for two CH 3 OH lines at 241.767 and 241.791 GHz.


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )

1A CH 3 OH [⋆] 58 1.16 × 10 [14] 2.6 224.8 6.34 × 10 [−][10] 4.9 × 10 [6]

SO 2 35 8.40 × 10 [13] 2.8 224.5 4.59 × 10 [−][10]

H 2 CS 58 [†] 3.55 × 10 [13] 3.8 224.5 1.94 × 10 [−][10]

CS " 1.06 × 10 [14] 4.0 225.4 5.79 × 10 [−][10]

HC [15] N " 1.42 × 10 [12] 5.4 224.5 7.76 × 10 [−][12]

SO " 2.61 × 10 [14] 4.6 225.7 1.43 × 10 [−][9]

H [13] CN " 2.02 × 10 [12] 6.3 224.0 1.10 × 10 [−][11]

H [13] CO [+] " 1.37 × 10 [12] 4.0 225.5 7.48 × 10 [−][12]

SiO " 2.07 × 10 [12] 3.7 226.5 1.13 × 10 [−][11]


2A CH 3 OH [⋆] 23 2.09 × 10 [13] 1.3 269.1 3.10 × 10 [−][11] 2.0 × 10 [6]

SO 2 23 [†] 3.12 × 10 [13] 3.5 268.8 4.63 × 10 [−][11]

CS " 1.30 × 10 [13] 3.4 269.6 1.93 × 10 [−][11]

SO " 4.65 × 10 [13] 2.5 269.4 6.90 × 10 [−][11]


2B CH 3 OH [⋆] 22 1.70 × 10 [14] 1.8 268.7 4.33 × 10 [−][10] 3.7 × 10 [6]

SO 2 23 7.33 × 10 [13] 2.2 269.0 1.87 × 10 [−][10]

H 2 CS 22 [†] 1.63 × 10 [13] 3.7 270.0 4.15 × 10 [−][11]

CS " 5.96 × 10 [13] 3.5 269.8 1.52 × 10 [−][10]

HC [15] N " 5.13 × 10 [11] 4.7 271.5 1.31 × 10 [−][12]

SO " 2.88 × 10 [14] 3.3 270.0 7.34 × 10 [−][10]

H [13] CN " 2.08 × 10 [12] 4.1 268.6 5.30 × 10 [−][12]

H [13] CO [+] " 4.41 × 10 [11] 3.1 270.3 1.12 × 10 [−][12]

SiO " 1.25 × 10 [12] 6.8 268.3 3.18 × 10 [−][12]


2C CH 3 OH [⋆] 67 5.56 × 10 [13] 2.1 267.8 6.87 × 10 [−][10] 6.2 × 10 [5]


Continued ...


Article number, page 81 of 90

_A&A proofs:_ manuscript no. aanda


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )


H 2 CS 67 [†] 4.11 × 10 [13] 5.2 266.9 5.08 × 10 [−][10]

CS " 4.52 × 10 [13] 3.5 268.4 5.59 × 10 [−][10]

SO " 3.10 × 10 [13] 3.5 268.6 3.83 × 10 [−][10]

H [13] CN " 1.35 × 10 [12] 9.6 271.9 1.67 × 10 [−][11]


2D CH 3 OH [⋆] 55 1.91 × 10 [13] 1.4 269.3 2.81 × 10 [−][10] 2.0 × 10 [6]

CS 55 [†] 2.82 × 10 [13] 3.3 270.4 4.15 × 10 [−][10]

SO " 1.69 × 10 [13] 4.0 271.4 2.49 × 10 [−][10]


2E CH 3 OH [⋆] 11 7.80 × 10 [13] 1.8 268.4 2.07 × 10 [−][10] 2.0 × 10 [6]

CS 11 [†] 3.14 × 10 [13] 2.8 270.1 8.33 × 10 [−][11]

SO " 1.54 × 10 [14] 2.9 271.2 4.08 × 10 [−][10]


2F CH 3 OH [⋆] 27 [‡] < 8.28 × 10 [12] 2.8 [≡] 270.9 [≡] < 1.11 × 10 [−][10]

CS " 3.31 × 10 [12] 2.8 270.9 4.46 × 10 [−][11]

H [13] CN " 2.68 × 10 [12] 13.1 276.0 3.61 × 10 [−][11]


3A CH 3 OH [⋆] 35 2.46 × 10 [14] 3.9 285.2 1.83 × 10 [−][10] 9.0 × 10 [6]

SO 2 43 1.06 × 10 [14] 4.7 285.0 7.89 × 10 [−][11]

H 2 CS 35 [†] 2.59 × 10 [13] 4.3 285.5 1.93 × 10 [−][11]

CS " 8.60 × 10 [13] 4.8 285.8 6.40 × 10 [−][11]

CH 3 CN " 2.97 × 10 [12] 2.9 284.1 2.21 × 10 [−][12]

HC [15] N " 6.82 × 10 [11] 4.0 286.4 5.08 × 10 [−][13]

SO " 3.66 × 10 [14] 4.5 286.3 2.73 × 10 [−][10]

H [13] CN " 1.00 × 10 [12] 3.8 284.3 7.45 × 10 [−][13]

H [13] CO [+] " 8.83 × 10 [11] 4.0 286.5 6.57 × 10 [−][13]

SiO " 1.79 × 10 [12] 8.9 288.7 1.33 × 10 [−][12]


3B CH 3 OH [⋆] 13 6.50 × 10 [13] 1.7 284.6 8.08 × 10 [−][11] 4.9 × 10 [6]

CS 13 [†] 4.29 × 10 [13] 4.0 285.9 5.33 × 10 [−][11]

SO " 2.79 × 10 [14] 3.7 286.2 3.47 × 10 [−][10]

H [13] CO [+] " 2.60 × 10 [11] 3.4 285.5 3.23 × 10 [−][13]


3C CH 3 OH [⋆] 51 2.38 × 10 [13] 1.8 286.2 3.77 × 10 [−][10] 2.0 × 10 [6]

CS 51 [†] 1.45 × 10 [13] 3.4 287.4 2.30 × 10 [−][10]

SO " 1.48 × 10 [13] 3.2 287.2 2.34 × 10 [−][10]

H [13] CO [+] " 1.74 × 10 [11] 3.0 288.3 2.76 × 10 [−][12]


3D CH 3 OH [⋆] 37 3.25 × 10 [13] 1.5 286.3 4.48 × 10 [−][10] 1.3 × 10 [6]

CS 37 [†] 1.28 × 10 [13] 3.5 287.1 1.77 × 10 [−][10]

SO " 1.22 × 10 [13] 3.2 287.4 1.68 × 10 [−][10]


4A CH 3 OH 151 1.29 × 10 [15] 3.2 264.3 3.55 × 10 [−][9]

CH 3 OH [⋆] 26 1.25 × 10 [14] 4.5 264.3 4.86 × 10 [−][11] 4.6 × 10 [7]

SO 2 249 4.47 × 10 [15] 7.1 265.5 2.06 × 10 [−][8]

42 8.07 × 10 [14] 5.0 264.3 5.57 × 10 [−][10]

33 SO 2 249 3.73 × 10 [14] 7.1 265.5 1.72 × 10 [−][9]

42 6.72 × 10 [13] 5.0 264.3 4.63 × 10 [−][11]

34 SO 2 249 5.05 × 10 [14] 7.1 265.5 2.33 × 10 [−][9]

42 9.10 × 10 [13] 5.0 264.3 6.28 × 10 [−][11]

SO 151 [†] 2.01 × 10 [15] 6.0 265.7 5.55 × 10 [−][9]

33 SO " 1.68 × 10 [14] 6.0 265.7 4.62 × 10 [−][10]

CH 3 CN 88 1.02 × 10 [13] 3.9 265.3 1.57 × 10 [−][11]

CS 151 [†] 2.60 × 10 [14] 5.0 265.1 7.15 × 10 [−][10]

H 2 CS " 8.29 × 10 [13] 3.6 264.0 2.28 × 10 [−][10]


Continued ...


Article number, page 82 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )


H [13] CO [+] " 1.20 × 10 [13] 5.1 265.6 3.30 × 10 [−][11]

SiO " 1.88 × 10 [13] 5.8 265.7 5.16 × 10 [−][11]

H [13] CN " 1.20 × 10 [13] 6.0 264.0 3.31 × 10 [−][11]

HC [15] N " 6.48 × 10 [12] 5.7 264.8 1.79 × 10 [−][11]

HNCO " 2.71 × 10 [13] 2.6 264.1 7.47 × 10 [−][11]

HC 3 N " 6.62 × 10 [12] 8.0 264.9 1.82 × 10 [−][11]

HDCO " < 4.17 × 10 [9] 3.2 [≡] 264.3 [≡] < 1.15 × 10 [−][14]

NH 2 CHO " < 5.60 × 10 [10] " " < 1.54 × 10 [−][13]

H 2 CCO " < 5.23 × 10 [12] " " < 1.44 × 10 [−][11]

CH 3 CHO " < 1.20 × 10 [12] " " < 3.31 × 10 [−][12]

CH 3 OCHO " < 5.35 × 10 [13] " " < 1.47 × 10 [−][10]

CH 3 OCH 3 " < 5.07 × 10 [8] " " < 1.40 × 10 [−][15]


5A CH 3 OH [⋆] 15 3.16 × 10 [13] 2.7 246.0 2.12 × 10 [−][11] 1.1 × 10 [6]

CS 15 [†] 2.91 × 10 [13] 4.2 246.6 1.95 × 10 [−][11]

SO " 9.08 × 10 [13] 3.9 246.3 6.08 × 10 [−][11]

H [13] CN " 1.07 × 10 [12] 10.0 248.4 7.17 × 10 [−][13]

H [13] CO [+] " 3.84 × 10 [11] 3.9 246.0 2.57 × 10 [−][13]

SiO " 5.64 × 10 [12] 20.0 245.3 3.78 × 10 [−][12]


5B CH 3 OH [⋆] 19 9.76 × 10 [13] 2.1 242.2 1.53 × 10 [−][10] 5.4 × 10 [6]

SO 2 38 7.48 × 10 [13] 3.0 242.0 1.17 × 10 [−][10]

H 2 CS 19 [†] 3.94 × 10 [13] 3.8 242.3 6.18 × 10 [−][11]

CS " 1.27 × 10 [14] 3.7 243.3 1.99 × 10 [−][10]

HC [15] N " 9.31 × 10 [11] 7.1 241.9 1.46 × 10 [−][12]

SO " 3.92 × 10 [14] 3.7 243.3 6.15 × 10 [−][10]

H [13] CN " 1.76 × 10 [12] 10.0 239.2 2.76 × 10 [−][12]

H [13] CO [+] " 6.35 × 10 [11] 3.5 243.4 9.96 × 10 [−][13]


6A CH 3 OH 149 1.46 × 10 [15] 5.7 242.4 3.60 × 10 [−][9]

CH 3 OH [⋆] 36 2.62 × 10 [14] 3.7 242.9 1.38 × 10 [−][10] 1.3 × 10 [7]

SO 2 161 5.28 × 10 [15] 12.5 245.5 1.42 × 10 [−][8]

44 9.75 × 10 [14] 7.1 243.7 6.50 × 10 [−][10]

33 SO 2 161 2.55 × 10 [14] 12.5 245.5 6.88 × 10 [−][10]

44 4.74 × 10 [13] 7.1 243.7 3.16 × 10 [−][11]

34 SO 2 161 2.80 × 10 [14] 12.5 245.5 7.55 × 10 [−][10]

44 5.19 × 10 [13] 7.1 243.7 3.46 × 10 [−][11]

SO 149 [†] 4.58 × 10 [15] 9.5 244.9 1.13 × 10 [−][8]

33 SO " 2.23 × 10 [14] 9.5 244.9 5.50 × 10 [−][10]

CH 3 CN 77 2.46 × 10 [13] 6.8 243.7 3.04 × 10 [−][11]

CS 149 [†] 4.99 × 10 [14] 5.5 243.6 1.23 × 10 [−][9]

H 2 CS " 2.05 × 10 [14] 5.3 242.8 5.07 × 10 [−][10]

H [13] CO [+] " 1.32 × 10 [13] 4.9 244.3 3.25 × 10 [−][11]

SiO " 8.80 × 10 [13] 11.5 246.0 2.17 × 10 [−][10]

H [13] CN " 2.13 × 10 [13] 9.8 243.6 5.27 × 10 [−][11]

HC [15] N " 1.31 × 10 [13] 7.5 244.7 3.25 × 10 [−][11]

HNCO " 8.35 × 10 [13] 5.8 242.8 2.06 × 10 [−][10]

HC 3 N " 1.24 × 10 [13] 4.7 245.1 3.07 × 10 [−][11]

NH 2 CHO " 4.09 × 10 [13] 4.8 241.5 1.01 × 10 [−][10]

HDCO " < 6.74 × 10 [12] 5.7 [≡] 242.4 [≡] < 1.66 × 10 [−][11]

H 2 CCO " < 5.00 × 10 [8] " " < 1.23 × 10 [−][15]

CH 3 CHO " < 5.02 × 10 [8] " " < 1.24 × 10 [−][15]

CH 3 OCHO " < 5.03 × 10 [8] " " < 1.24 × 10 [−][15]

CH 3 OCH 3 " < 8.51 × 10 [8] " " < 2.10 × 10 [−][15]


Continued ...


Article number, page 83 of 90

_A&A proofs:_ manuscript no. aanda


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )

6B CH 3 OH 181 1.60 × 10 [15] 2.9 243.1 5.50 × 10 [−][9]

CH 3 OH [⋆] 50 3.25 × 10 [14] 4.4 241.6 2.83 × 10 [−][10] 2.8 × 10 [7]

SO 2 175 1.53 × 10 [15] 6.0 243.0 5.03 × 10 [−][9]

34 2.68 × 10 [14] 3.3 241.7 1.49 × 10 [−][10]

34 SO 2 175 1.30 × 10 [14] 6.0 243.0 4.28 × 10 [−][10]

34 2.28 × 10 [13] 3.3 241.7 1.27 × 10 [−][11]

SO 181 [†] 1.39 × 10 [15] 5.2 243.2 4.75 × 10 [−][9]

33 SO " 7.48 × 10 [13] 5.2 243.2 2.56 × 10 [−][10]

CH 3 CN 132 4.86 × 10 [13] 8.7 243.4 1.19 × 10 [−][10]

CS 181 [†] 3.85 × 10 [14] 5.0 242.4 1.32 × 10 [−][9]

H 2 CS " 4.10 × 10 [14] 5.2 241.5 1.41 × 10 [−][9]

H [13] CO [+] " 1.08 × 10 [13] 4.0 242.9 3.72 × 10 [−][11]

SiO " 1.51 × 10 [13] 5.8 243.5 5.19 × 10 [−][11]

H [13] CN " 2.65 × 10 [13] 5.6 242.1 9.08 × 10 [−][11]

HC [15] N " 1.46 × 10 [13] 4.3 243.7 4.99 × 10 [−][11]

HNCO " 3.64 × 10 [13] 2.5 242.3 1.25 × 10 [−][10]

HC 3 N " 1.41 × 10 [13] 4.5 243.9 4.83 × 10 [−][11]

HDCO " < 1.64 × 10 [10] 2.9 [≡] 243.1 [≡] < 5.61 × 10 [−][14]

NH 2 CHO " < 2.77 × 10 [9] " " < 9.49 × 10 [−][15]

H 2 CCO " < 3.45 × 10 [13] " " < 1.18 × 10 [−][10]

CH 3 CHO " < 4.60 × 10 [13] " " < 1.58 × 10 [−][10]

CH 3 OCHO " < 1.67 × 10 [14] " " < 5.71 × 10 [−][10]

CH 3 OCH 3 " < 2.39 × 10 [14] " " < 8.19 × 10 [−][10]


6C CH 3 OH [⋆] 30 2.38 × 10 [14] 3.6 241.9 3.23 × 10 [−][10] 5.3 × 10 [6]

SO 2 30 [†] 4.90 × 10 [13] 2.2 241.3 6.66 × 10 [−][11]

H 2 CS " 7.05 × 10 [13] 3.6 241.7 9.58 × 10 [−][11]

CS " 2.34 × 10 [14] 4.1 242.5 3.18 × 10 [−][10]

SO " 2.56 × 10 [14] 4.2 242.7 3.48 × 10 [−][10]

H [13] CN " 1.25 × 10 [12] 2.3 242.6 1.70 × 10 [−][12]

H [13] CO [+] " 9.47 × 10 [11] 3.8 243.0 1.29 × 10 [−][12]

SiO " 8.50 × 10 [12] 18.9 238.2 1.16 × 10 [−][11]


6D CH 3 OH [⋆] 46 5.08 × 10 [14] 3.4 242.1 1.54 × 10 [−][9] 2.1 × 10 [6]

H 2 CS 46 [†] 8.41 × 10 [13] 3.9 242.7 2.55 × 10 [−][10]

CS " 1.88 × 10 [14] 5.2 243.0 5.69 × 10 [−][10]

SO " 2.47 × 10 [14] 5.5 242.8 7.48 × 10 [−][10]

H [13] CO [+] " 8.91 × 10 [11] 4.0 241.8 2.70 × 10 [−][12]

SiO " < 7.51 × 10 [12] 15.6 246.3 2.27 × 10 [−][11]


6E CH 3 OH [⋆] 38 5.19 × 10 [14] 2.6 243.0 1.28 × 10 [−][9] 3.3 × 10 [6]

H 2 CS 38 [†] 7.75 × 10 [13] 4.2 243.0 1.91 × 10 [−][10]

CS " 1.82 × 10 [14] 4.2 243.7 4.48 × 10 [−][10]

SO " 1.92 × 10 [14] 3.8 244.0 4.73 × 10 [−][10]

H [13] CN " 1.78 × 10 [12] 4.6 242.4 4.38 × 10 [−][12]

H [13] CO [+] " 5.54 × 10 [11] 3.4 244.5 1.36 × 10 [−][12]

SiO " 8.59 × 10 [11] 4.9 238.1 2.12 × 10 [−][12]


6F CH 3 OH [⋆] 27 5.82 × 10 [13] 1.9 241.2 1.33 × 10 [−][10] 1.0 × 10 [6]

SO 2 27 [†] 3.54 × 10 [13] 2.9 240.9 8.08 × 10 [−][11]

CS " 4.22 × 10 [13] 3.4 241.9 9.63 × 10 [−][11]

SO " 1.08 × 10 [14] 3.3 242.1 2.47 × 10 [−][10]

H [13] CO [+] " 6.01 × 10 [11] 3.1 242.1 1.37 × 10 [−][12]


7A CH 3 OH [⋆] 29 9.92 × 10 [13] 1.8 252.8 3.05 × 10 [−][10] 2.4 × 10 [6]


Continued ...


Article number, page 84 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )

SO 2 22 3.25 × 10 [13] 1.6 253.1 9.98 × 10 [−][11]

H 2 CS 29 [†] 1.40 × 10 [13] 3.3 253.3 4.30 × 10 [−][11]

CS " 4.91 × 10 [13] 3.4 253.8 1.51 × 10 [−][10]

SO " 1.36 × 10 [14] 3.1 254.1 4.18 × 10 [−][10]

H [13] CN " 8.42 × 10 [11] 7.2 255.4 2.59 × 10 [−][12]

H [13] CO [+] " 8.17 × 10 [11] 3.6 254.2 2.51 × 10 [−][12]


7B CH 3 OH 27 [‡] < 1.00 × 10 [10] 2.8 [≡] 252.4 [≡] < 8.11 × 10 [−][14]

CS " 5.83 × 10 [12] 2.8 252.4 4.73 × 10 [−][11]


7C CH 3 OH 27 [‡] < 2.20 × 10 [13] 2.9 [≡] 255.0 [≡] < 1.74 × 10 [−][10]

CS 27 [†] 9.13 × 10 [12] 2.9 255.0 7.24 × 10 [−][11]

H [13] CO [+] " 2.19 × 10 [11] 3.2 255.3 1.74 × 10 [−][12]


8A CH 3 OH [⋆] 25 2.14 × 10 [14] 2.0 238.0 6.30 × 10 [−][10] 7.3 × 10 [6]

SO 2 36 4.00 × 10 [13] 3.1 237.9 1.18 × 10 [−][10]

H 2 CS 25 [†] 1.68 × 10 [13] 4.0 237.4 4.94 × 10 [−][11]

CS " 5.23 × 10 [13] 3.8 238.6 1.54 × 10 [−][10]

SO " 2.33 × 10 [14] 3.6 239.0 6.86 × 10 [−][10]

H [13] CN " 5.13 × 10 [11] 3.1 237.5 1.51 × 10 [−][12]

H [13] CO [+] " 1.55 × 10 [11] 5.3 238.2 4.56 × 10 [−][13]


8B [§]


8C CH 3 OH [⋆] 27 2.08 × 10 [14] 2.8 239.9 1.13 × 10 [−][9] 2.0 × 10 [6]

CS 27 [†] 5.67 × 10 [13] 4.2 240.8 3.09 × 10 [−][10]

SO " 1.21 × 10 [14] 3.7 240.8 6.59 × 10 [−][10]


9A CH 3 OH [⋆] 50 1.53 × 10 [14] 1.8 241.6 1.16 × 10 [−][9] 1.9 × 10 [6]

H 2 CS 50 [†] 2.08 × 10 [13] 3.4 241.3 1.57 × 10 [−][10]

CS " 7.34 × 10 [13] 3.7 242.4 5.55 × 10 [−][10]

SO " 6.96 × 10 [13] 3.4 242.6 5.26 × 10 [−][10]

H [13] CN " 8.95 × 10 [11] 2.5 241.2 6.77 × 10 [−][12]

H [13] CO [+] " 4.01 × 10 [11] 3.1 242.5 3.03 × 10 [−][12]


10A CH 3 OH [⋆] 26 1.20 × 10 [14] 2.9 239.0 3.48 × 10 [−][10] 2.5 × 10 [6]

SO 2 30 2.19 × 10 [13] 2.3 239.4 6.36 × 10 [−][11]

H 2 CS 26 [†] 9.92 × 10 [12] 3.4 239.3 2.88 × 10 [−][11]

CS " 4.20 × 10 [13] 4.0 240.4 1.22 × 10 [−][10]

HC [15] N " 2.97 × 10 [11] 4.5 239.0 8.62 × 10 [−][13]

SO " 1.01 × 10 [14] 4.1 240.5 2.93 × 10 [−][10]

H [13] CN " 8.44 × 10 [11] 7.2 241.2 2.45 × 10 [−][12]

H [13] CO [+] " 5.35 × 10 [11] 3.4 240.6 1.55 × 10 [−][12]

SiO " 1.13 × 10 [12] 4.7 240.7 3.28 × 10 [−][12]


10B CH 3 OH 27 [‡] < 6.25 × 10 [13] 3.6 [≡] 240.7 [≡] < 3.43 × 10 [−][10]

CS " 2.21 × 10 [13] 3.6 240.7 1.21 × 10 [−][10]

H [13] CO [+] " 5.72 × 10 [11] 5.1 241.7 3.14 × 10 [−][12]

SiO " 2.01 × 10 [12] 4.7 241.5 1.10 × 10 [−][11]


10C CH 3 OH [⋆] 39 3.35 × 10 [13] 1.5 238.9 5.54 × 10 [−][10] 2.5 × 10 [6]

CS 39 [†] 1.96 × 10 [13] 3.4 240.0 3.24 × 10 [−][10]

H [13] CO [+] " 1.88 × 10 [11] 2.4 240.4 3.11 × 10 [−][12]


10D CH 3 OH [⋆] 22 4.59 × 10 [13] 5.9 240.7 3.99 × 10 [−][10] 2.0 × 10 [6]


Continued ...


Article number, page 85 of 90

_A&A proofs:_ manuscript no. aanda


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )


CS 22 [†] 1.55 × 10 [13] 3.1 240.7 1.35 × 10 [−][10]


11A


11B CH 3 OH [⋆] 24 6.28 × 10 [14] 2.0 236.0 1.87 × 10 [−][9] 2.0 × 10 [7]

H 2 CS 24 [†] 4.05 × 10 [13] 3.9 236.3 1.21 × 10 [−][10]

CS " 8.37 × 10 [13] 3.3 236.7 2.49 × 10 [−][10]

SO " 2.56 × 10 [14] 3.8 237.1 7.63 × 10 [−][10]

H [13] CN " 5.41 × 10 [11] 2.6 236.1 1.61 × 10 [−][12]

H [13] CO [+] " 2.19 × 10 [11] 5.4 237.1 6.52 × 10 [−][13]


11C CH 3 OH [⋆] 10 1.21 × 10 [14] 1.5 235.6 2.11 × 10 [−][10] 4.9 × 10 [6]

CS 10 [†] 6.58 × 10 [13] 3.3 236.5 1.15 × 10 [−][10]

SO " 3.48 × 10 [14] 3.5 236.8 6.06 × 10 [−][10]

H [13] CO [+] " 4.70 × 10 [11] 3.6 236.4 8.18 × 10 [−][13]


11D CH 3 OH [⋆] 22 3.74 × 10 [14] 2.2 235.6 2.97 × 10 [−][9] 3.9 × 10 [6]

H 2 CS 22 [†] 2.42 × 10 [13] 4.8 235.5 1.92 × 10 [−][10]

CS " 1.06 × 10 [14] 4.4 236.1 8.41 × 10 [−][10]

SO " 1.40 × 10 [14] 3.6 236.6 1.11 × 10 [−][9]


12A CH 3 OH [⋆] 19 7.88 × 10 [13] 1.6 267.9 1.91 × 10 [−][10] 7.5 × 10 [6]

H 2 CS 19 [†] 2.35 × 10 [13] 2.7 268.2 5.70 × 10 [−][11]

CS " 4.35 × 10 [13] 3.5 268.9 1.06 × 10 [−][10]

SO " 1.08 × 10 [14] 3.4 269.1 2.62 × 10 [−][10]

H [13] CN " 1.44 × 10 [12] 10.0 269.4 3.49 × 10 [−][12]

H [13] CO [+] " 3.04 × 10 [11] 4.2 269.4 7.38 × 10 [−][13]


12B CH 3 OH 27 [‡] < 7.99 × 10 [12] 2.4 [≡] 271.4 [≡] < 5.84 × 10 [−][11]

CS " 3.73 × 10 [12] 2.4 271.4 2.73 × 10 [−][11]


12C CH 3 OH 27 [‡] < 3.33 × 10 [12] 2.8 270.7 < 2.85 × 10 [−][11]

CS " 9.99 × 10 [12] 2.8 270.7 8.55 × 10 [−][11]

SO " 2.61 × 10 [13] 3.4 271.0 2.23 × 10 [−][10]


12D CH 3 OH [⋆] 38 1.85 × 10 [13] 1.3 270.2 3.06 × 10 [−][10] 2.0 × 10 [6]

CS 38 [†] 1.02 × 10 [13] 3.1 271.0 1.69 × 10 [−][10]


13A CH 3 OH [⋆] 49 1.71 × 10 [14] 1.8 227.0 9.63 × 10 [−][10] 2.6 × 10 [6]

SO 2 49 [†] 2.32 × 10 [13] 1.2 227.0 1.31 × 10 [−][10]

H 2 CS " 1.75 × 10 [13] 3.8 227.5 9.86 × 10 [−][11]

CS " 7.01 × 10 [13] 3.4 227.9 3.95 × 10 [−][10]

SO " 7.19 × 10 [13] 2.5 227.9 4.05 × 10 [−][10]

H [13] CN " 4.80 × 10 [11] 2.7 227.5 2.70 × 10 [−][12]

H [13] CO [+] " 3.49 × 10 [11] 3.0 228.0 1.97 × 10 [−][12]

SiO " 7.28 × 10 [11] 4.9 226.7 4.10 × 10 [−][12]


13B [§]


13C CH 3 OH [⋆] 27 3.91 × 10 [14] 3.0 227.3 1.26 × 10 [−][9] 1.4 × 10 [6]

SO 2 27 [†] 2.86 × 10 [13] 2.3 227.1 9.18 × 10 [−][11]

H 2 CS " 2.61 × 10 [13] 5.3 227.2 8.38 × 10 [−][11]

CS " 1.03 × 10 [14] 4.1 228.2 3.31 × 10 [−][10]

SO " 1.50 × 10 [14] 4.0 228.1 4.82 × 10 [−][10]

H [13] CN " 1.01 × 10 [12] 4.8 228.5 3.24 × 10 [−][12]


Continued ...


Article number, page 86 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )


H [13] CO [+] " 3.18 × 10 [11] 4.5 229.1 1.02 × 10 [−][12]

SiO " 3.92 × 10 [12] 20.0 216.8 1.26 × 10 [−][11]


13D CH 3 OH 27 [‡] < 8.62 × 10 [13] 4.3 [≡] 230.7 [≡] < 3.04 × 10 [−][10]

SO 2 " 9.27 × 10 [13] 3.8 229.8 3.27 × 10 [−][10]

H 2 CS " 1.94 × 10 [13] 4.0 229.6 6.85 × 10 [−][11]

CS " 4.98 × 10 [13] 4.3 230.7 1.76 × 10 [−][10]

SO " 2.68 × 10 [14] 4.5 230.2 9.46 × 10 [−][10]


13E CH 3 OH [⋆] 19 2.06 × 10 [13] 1.6 225.6 8.11 × 10 [−][11] 2.0 × 10 [6]

CS 19 [†] 2.41 × 10 [13] 3.6 226.5 9.49 × 10 [−][11]

SO " 1.64 × 10 [13] 3.5 227.3 6.46 × 10 [−][11]


13F CH 3 OH [⋆] 42 2.09 × 10 [14] 2.1 227.6 2.51 × 10 [−][9] 1.9 × 10 [6]

SO 2 42 [†] 2.23 × 10 [13] 1.7 227.3 2.68 × 10 [−][10]

H 2 CS " 1.06 × 10 [13] 3.2 227.2 1.27 × 10 [−][10]

CS " 6.38 × 10 [13] 3.7 228.5 7.65 × 10 [−][10]

SO " 7.82 × 10 [13] 3.5 228.6 9.38 × 10 [−][10]

H [13] CO [+] " 1.45 × 10 [11] 2.5 228.9 1.74 × 10 [−][12]


13G CH 3 OH [⋆] 19 1.22 × 10 [14] 1.7 226.0 6.38 × 10 [−][10] 6.4 × 10 [6]

CS 19 [†] 3.00 × 10 [13] 3.4 226.9 1.57 × 10 [−][10]

SO " 8.09 × 10 [13] 3.4 227.1 4.23 × 10 [−][10]

H [13] CO [+] " 2.51 × 10 [11] 4.3 227.7 1.31 × 10 [−][12]


13H CH 3 OH [⋆] 40 3.41 × 10 [13] 1.5 227.2 4.75 × 10 [−][10] 2.0 × 10 [6]

CS 40 [†] 1.82 × 10 [13] 3.5 228.1 2.54 × 10 [−][10]


13K CH 3 OH 27 [‡] < 1.27 × 10 [13] 3.3 [≡] 227.4 [≡] < 1.68 × 10 [−][10]

CS " 8.86 × 10 [12] 3.3 227.4 1.17 × 10 [−][10]


14A CH 3 OH 163 1.79 × 10 [15] 4.9 249.8 1.06 × 10 [−][8]

CH 3 OH [⋆] 50 2.63 × 10 [14] 3.1 248.1 4.38 × 10 [−][10] 1.6 × 10 [7]

SO 2 138 1.48 × 10 [15] 8.0 250.6 7.36 × 10 [−][9]

19 1.32 × 10 [14] 2.8 248.8 6.77 × 10 [−][11]

SO 163 1.40 × 10 [15] 7.3 250.1 8.26 × 10 [−][9]

CH 3 CN 42 1.78 × 10 [13] 4.2 249.9 2.42 × 10 [−][11]

CS 163 [†] 3.70 × 10 [14] 5.4 249.2 2.18 × 10 [−][9]

H 2 CS " 1.19 × 10 [14] 4.0 248.2 7.04 × 10 [−][10]

H [13] CO [+] " 5.46 × 10 [12] 4.2 249.6 3.23 × 10 [−][11]

SiO " 6.57 × 10 [13] 34.9 256.4 3.88 × 10 [−][10]

HDCO " 2.54 × 10 [13] 4.0 247.5 1.50 × 10 [−][10]

H [13] CN " 1.77 × 10 [13] 6.8 249.4 1.04 × 10 [−][10]

HC [15] N " 1.01 × 10 [13] 5.8 250.8 5.97 × 10 [−][11]

HNCO " 7.35 × 10 [13] 4.6 249.5 4.34 × 10 [−][10]

NH 2 CHO " < 5.09 × 10 [8] 4.9 [≡] 249.8 [≡] < 3.00 × 10 [−][15]

H 2 CCO " < 5.10 × 10 [8] " " < 3.01 × 10 [−][15]

CH 3 CHO " < 5.09 × 10 [8] " " < 3.00 × 10 [−][15]

CH 3 OCHO " < 9.43 × 10 [13] " " < 5.57 × 10 [−][10]

CH 3 OCH 3 " < 1.18 × 10 [14] " " < 6.97 × 10 [−][10]


14B [§]


15A CH 3 OH [⋆] 38 1.47 × 10 [14] 6.0 235.5 2.77 × 10 [−][10] 2.0 × 10 [6]

SO 2 38 [†] 1.11 × 10 [14] 2.4 236.0 2.09 × 10 [−][10]


Continued ...


Article number, page 87 of 90

_A&A proofs:_ manuscript no. aanda


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )


CS " 1.10 × 10 [14] 4.2 236.7 2.08 × 10 [−][10]

SO " 2.99 × 10 [14] 4.5 237.1 5.64 × 10 [−][10]

H [13] CO [+] " 1.42 × 10 [12] 3.5 236.4 2.68 × 10 [−][12]

SiO " 1.49 × 10 [13] 19.3 229.3 2.81 × 10 [−][11]


15B CH 3 OH [⋆] 33 1.42 × 10 [14] 2.2 238.5 7.48 × 10 [−][10] 1.7 × 10 [6]

SO 2 33 [†] 9.49 × 10 [12] 1.6 238.0 5.00 × 10 [−][11]

H 2 CS " 1.33 × 10 [13] 3.4 238.7 7.00 × 10 [−][11]

CS " 5.30 × 10 [13] 4.0 239.4 2.79 × 10 [−][10]

SO " 6.85 × 10 [13] 3.8 239.4 3.61 × 10 [−][10]

H [13] CO [+] " 3.39 × 10 [11] 3.8 239.8 1.79 × 10 [−][12]

SiO " 3.25 × 10 [12] 20.0 234.9 1.71 × 10 [−][11]


15C CH 3 OH 27 [‡] < 1.29 × 10 [13] 3.1 [≡] 238.6 [≡] < 1.02 × 10 [−][10]

CS " 1.78 × 10 [13] 3.1 238.6 1.41 × 10 [−][10]

H [13] CO [+] " 1.58 × 10 [11] 2.3 239.0 1.25 × 10 [−][12]

SiO " 1.04 × 10 [12] 4.3 241.4 8.25 × 10 [−][12]


16A [§]


16B CH 3 OH [⋆] 19 7.37 × 10 [13] 2.1 236.1 4.49 × 10 [−][10] 3.7 × 10 [6]

SO 2 19 [†] 1.36 × 10 [13] 1.1 236.5 8.28 × 10 [−][11]

CS " 2.34 × 10 [13] 3.4 236.9 1.43 × 10 [−][10]

SO " 6.18 × 10 [13] 3.4 237.1 3.76 × 10 [−][10]

H [13] CN " 8.00 × 10 [11] 4.4 243.1 4.87 × 10 [−][12]

SiO " 2.78 × 10 [12] 7.8 229.4 1.69 × 10 [−][11]


17A CH 3 OH [⋆] 31 2.76 × 10 [14] 2.8 221.3 4.93 × 10 [−][10] 5.1 × 10 [6]

SO 2 28 7.08 × 10 [13] 3.9 221.4 1.26 × 10 [−][10]

H 2 CS 31 [†] 5.60 × 10 [13] 4.2 221.8 9.99 × 10 [−][11]

CS " 1.30 × 10 [14] 4.6 222.4 2.32 × 10 [−][10]

SO " 2.82 × 10 [14] 4.4 222.5 5.03 × 10 [−][10]

H [13] CN " 4.49 × 10 [11] 2.3 221.8 8.01 × 10 [−][13]

H [13] CO [+] " 3.92 × 10 [11] 3.7 222.9 7.00 × 10 [−][13]

SiO " 2.48 × 10 [12] 18.1 221.6 4.43 × 10 [−][12]


17B [§]


18A CH 3 OH [⋆] 26 1.21 × 10 [14] 2.0 278.9 3.05 × 10 [−][10] 4.7 × 10 [6]

SO 2 26 [†] 1.46 × 10 [13] 2.2 278.6 3.67 × 10 [−][11]

H 2 CS " 1.58 × 10 [13] 2.7 278.8 3.98 × 10 [−][11]

CS " 6.62 × 10 [13] 3.6 279.9 1.67 × 10 [−][10]

SO " 1.53 × 10 [14] 3.6 280.3 3.85 × 10 [−][10]

H [13] CO [+] " 4.66 × 10 [11] 3.2 280.1 1.17 × 10 [−][12]


18B CH 3 OH [⋆] 33 5.11 × 10 [13] 2.3 279.6 4.66 × 10 [−][10] 2.1 × 10 [6]

H 2 CS 33 [†] 2.36 × 10 [13] 10.0 275.6 2.15 × 10 [−][10]

CS " 4.99 × 10 [13] 3.7 280.4 4.55 × 10 [−][10]

SO " 2.65 × 10 [13] 3.2 281.0 2.42 × 10 [−][10]

H [13] CO [+] " 1.58 × 10 [11] 3.5 281.6 1.44 × 10 [−][12]


18C CH 3 OH [⋆] 23 3.80 × 10 [13] 1.6 280.6 3.96 × 10 [−][10] 2.0 × 10 [6]

H 2 CS 23 [†] 1.96 × 10 [13] 7.5 280.1 2.04 × 10 [−][10]

CS " 2.93 × 10 [13] 3.3 281.5 3.06 × 10 [−][10]


Continued ...


Article number, page 88 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Table B.2: Parameters of the best-fit model for all detected molecules and their abundances.


Source Species, X T N(X) ∆v FWHM v LSR N(X)/N(H 2 ) n col [∗]

(K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] ) (cm [−][3] )

19A CH 3 OH [⋆] 25 6.73 × 10 [14] 2.7 274.4 1.89 × 10 [−][9] 4.1 × 10 [6]

SO 2 25 [†] 6.59 × 10 [13] 2.2 274.6 1.85 × 10 [−][10]

H 2 CS " 4.32 × 10 [13] 3.5 273.9 1.22 × 10 [−][10]

CS " 1.23 × 10 [14] 4.4 274.8 3.46 × 10 [−][10]

SO " 2.53 × 10 [14] 4.0 275.6 7.12 × 10 [−][10]

SiO " 1.67 × 10 [12] 5.2 277.1 4.70 × 10 [−][12]


19B [§]


19C CH 3 OH 27 [‡] < 3.07 × 10 [12] 4.4 [≡] 274.1 [≡] < 2.39 × 10 [−][11]

CS " 7.51 × 10 [12] 4.4 274.1 5.86 × 10 [−][11]

SO " 2.81 × 10 [13] 8.1 273.2 2.19 × 10 [−][10]


19D CH 3 OH [⋆] 42 6.23 × 10 [13] 1.4 274.0 8.66 × 10 [−][10] 1.3 × 10 [6]

SO 2 42 [†] 1.75 × 10 [13] 3.1 274.1 2.43 × 10 [−][10]

H 2 CS " 1.87 × 10 [13] 8.6 278.2 2.60 × 10 [−][10]

CS " 2.79 × 10 [13] 3.5 274.8 3.88 × 10 [−][10]

SO " 5.19 × 10 [13] 3.4 275.2 7.21 × 10 [−][10]


20A CH 3 OH 27 [‡] < 5.32 × 10 [12] 3.0 [≡] 284.5 [≡] < 5.36 × 10 [−][11]

CS " 1.99 × 10 [12] 3.0 284.5 2.00 × 10 [−][11]


**Notes.** N(H 2 ) was derived in Paper II with the temperatures derived in the current paper and assuming all of the 1.3 mm continuum emission
originated in optically thin dust with an opacity of 1.04 cm [2] gr [−][1] and a gas-to-dust mass ratio of 320. We consider that the error values range from
40% to 60% for the temperatures, 20% to 40% for the column densities, and 10% to 30% for the line widths and velocity shifts.
(∗) The collision partner number density.
(⋆) The fit parameters were derived with the non-LTE assumption.
(†)
We adopted this value from the temperature for the CH 3 OH. Where there were two components, the temperature we adopted was from the hot
component.
(‡)
The median value of the fit temperature for CH 3 OH from all the sources, where we could fit.
(<) The upper limit estimations.
(≡) The upper limit on column density and abundance was estimated by fixing the line width and line shift. In the case of estimating the upper
limits for CH 3 OH, we used the best-fit parameters for CS, and for the other molecules, we used the best-fit parameters for CH 3 OH.
(§) No emission line is detected.


**Appendix C:** **Comparisons of molecular abundances in hot cores with chemical models**


Section 4.2.2 discusses how the observed abundances of the hot cores in the LMC compare with the only hot core modeling for
LMC’s condition (Acharyya & Herbst 2018). We present the comparisons for three molecules (CH 3 OH, SO 2, and CH 3 CN) in
Section 4.2.2, and we expand this comparison in this appendix. Figures C.1 and C.2 show the comparisons of observed abundance
for the seven hot cores in the LMC with the chemical models for the final hot core temperature of 100 and 200 K, respectively. It
is evident from the plots that the solid curve representing the warm dust initial condition (T _d_ = 25 K) does not appear in any of the
subplots. The only exception is SiO, for which a sharp increase in the model at a time of ≈10 [6] yr could also reproduce the observed
abundances. As the modelings do not include shocks, this increase in the SiO is not reliable. Moreover, the observed abundance
of HNCO could not be reproduced by models; the peak abundance of the models is smaller by more than an order of magnitude.
The underestimation of abundances is also apparent in the case of SO 2 and SO. These three species (HNCO, SO 2, and SO) are also
commonly found to be associated with shocks in star-forming regions. The higher observed abundances could imply the presence
of shocks in the hot cores of the LMC, which is not included in the modelings.


Article number, page 89 of 90

_A&A proofs:_ manuscript no. aanda


Final Temperature = 100 K


|10 8|Col2|10 8|Col4|
|---|---|---|---|
|10<br>10<br>10<br>9<br>nCS/nH<br>106<br>Time<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH||10<br>9<br>10<br>8<br>nSO/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>nSiO/nH<br> (yr)<br>106<br>Time (yr)<br>10<br>12<br>10<br>11<br>10<br>10<br>10<br>9<br>nHNCO/nH<br>10<br>12<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nNH2CHO/nH||
|10<br>10<br>10<br>9<br>nCS/nH<br>106<br>Time<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH||||



Fig. C.1: Comparisons of abundances for CS, SO, SiO, H 2 CS, HNCO, and NH 2 CHO from observations of the seven hot cores
detected in the LMC and the LMC hot core models for the final hot core temperature of 100 K. The black curves show abundances
over time for initial dust temperatures of 10 (dotted line), 15 (dashed curve), 20 (larger dashed curve), and 25 K (solid curve; this
curve does not necessarily appear in the range of abundances in the plot). The horizontal colored line shows the single abundance
value for each hot core and follows the same color code as Fig. 13 (see the text for more details).


Final Temperature = 200 K






















|10 8|Col2|Col3|10 8|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||10<br>9<br>10<br>8<br>nSO/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>nSiO/nH<br>106<br>10<br>12<br>10<br>11<br>10<br>10<br>10<br>9<br>nHNCO/nH<br>10<br>12<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nNH2CHO/nH|10<br>9<br>10<br>8<br>nSO/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>nSiO/nH<br>106<br>10<br>12<br>10<br>11<br>10<br>10<br>10<br>9<br>nHNCO/nH<br>10<br>12<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nNH2CHO/nH||<br> <br> <br>|
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||||||
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||||||
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||||10 K<br>15 K<br>20 K<br>25 K|10 K<br>15 K<br>20 K<br>25 K|
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||||||
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||||||
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|||||||
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH|106|106|106|106|106|106|
|10<br>10<br>10<br>9<br>nCS/nH<br>10<br>11<br>10<br>10<br>10<br>9<br>10<br>8<br>nH2CS/nH||Time|(yr)|Time (yr)|Time (yr)|Time (yr)|



Fig. C.2: Same as Fig. C.1 but for the LMC hot core models for the final hot core temperature of 200 K.


Article number, page 90 of 90

Hamedani Golshan et al.: High-mass star formation across the Large Magellanic Cloud


Table B.1: Parameters of the LTE fits for CH 3 OH.


T N(X) ∆v FWHM v LSR
Source (K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] )


1A 16 2.09 × 10 [14] 4.3 224.8
2A 12 5.29 × 10 [13] 1.3 269.2
2B 12 3.48 × 10 [14] 1.8 268.7
2C 9 3.50 × 10 [14] 2.1 267.8
2D 16 4.51 × 10 [13] 3.5 268.4
2E 10 1.09 × 10 [14] 2.0 269.0
3A 16 3.72 × 10 [14] 3.9 285.2
3B 11 9.17 × 10 [13] 1.8 284.7
3C 10 1.15 × 10 [14] 2.1 286.3
3D 10 1.39 × 10 [14] 1.6 286.3
4A 144 4.88 × 10 [15] 3.17 264.3
20 1.35 × 10 [14] 4.49 264.2
5A 5 1.11 × 10 [15] 2.0 246.1
5B 15 1.41 × 10 [14] 2.3 242.3
6A 170 6.56 × 10 [15] 5.74 242.3
19 4.17 × 10 [14] 3.80 242.9
6B 228 9.15 × 10 [15] 3.21 243.3
33 3.27 × 10 [14] 3.47 241.2
6C 12 5.35 × 10 [14] 3.7 242.0
6D 8 5.36 × 10 [15] 2.7 242.1
6E 12 1.54 × 10 [15] 2.5 243.0
6F 9 2.39 × 10 [14] 1.8 241.3
7A 10 3.84 × 10 [14] 1.7 252.8
8A 15 4.04 × 10 [14] 1.9 238.0
8C 10 7.57 × 10 [14] 2.6 239.9
9A 11 5.31 × 10 [14] 1.8 241.6
10A 10 3.77 × 10 [14] 2.9 239.3
10C 11 1.08 × 10 [14] 1.6 239.3
10D 10 8.89 × 10 [13] 2.8 239.3
11B 17 8.15 × 10 [14] 1.9 236.0
11C 10 1.15 × 10 [14] 1.6 235.5
11D 11 9.39 × 10 [14] 2.0 235.7
12A 14 1.17 × 10 [14] 1.6 267.9
12D 12 5.28 × 10 [13] 1.6 270.3
13A 12 4.64 × 10 [14] 1.8 227.1
13C 8 3.19 × 10 [15] 2.6 227.3
13E 14 3.25 × 10 [13] 1.5 225.7
13F 10 8.35 × 10 [14] 2.5 227.0
13G 10 3.03 × 10 [14] 3.0 226.8
13H 10 1.27 × 10 [14] 1.6 226.8
14A 160 6.48 × 10 [15] 4.70 250.0
26 2.96 × 10 [14] 3.03 248.0
15A 16 2.70 × 10 [14] 5.5 235.4
15B 10 5.80 × 10 [14] 2.2 238.5
16B 12 1.48 × 10 [14] 2.0 236.1
17A 14 5.11 × 10 [14] 2.9 221.4
18A 12 2.61 × 10 [14] 2.0 279.0
18B 11 1.62 × 10 [14] 2.6 279.8
18C 10 1.26 × 10 [14] 1.7 280.7
19A 10 3.01 × 10 [15] 2.3 274.5
19D 10 2.61 × 10 [14] 1.4 274.1


**Notes.** The final best-fit models for CH 3 OH are listed in Table B.2 (see Section 3.1 for more details).


Article number, page 91 of 90


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "49.59 ± 0.09 (statistical) ± 0.54 (systematic) kpc",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[0].distance_source.evidence[0]",
  "value": "Pietrzyński et al. 2019",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[1].coordinates.evidence[1]",
  "value": "05:19:12.27 -69:09:07.3",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[1].redshift_or_distance.evidence[1]",
  "value": "49.59 kpc",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[1].distance_source.evidence[1]",
  "value": "Pietrzyński et al. 2019",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[2].coordinates.evidence[1]",
  "value": "05:09:53.89 -68:53:36.7",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[2].redshift_or_distance.evidence[1]",
  "value": "49.59 kpc",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[2].distance_source.evidence[1]",
  "value": "Pietrzyński et al. 2019",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[3].coordinates.evidence[1]",
  "value": "05:23:33.40 -69:37:12.2",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[3].redshift_or_distance.evidence[1]",
  "value": "49.59 kpc",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[3].distance_source.evidence[1]",
  "value": "Pietrzyński et al. 2019",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[4].coordinates.evidence[1]",
  "value": "05:23:43.48 -68:00:33.9",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[4].redshift_or_distance.evidence[1]",
  "value": "49.59 kpc",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "science.targets[4].distance_source.evidence[1]",
  "value": "Pietrzyński et al. 2019",
  "failed_quote": "The LMC is a nearby dwarf galaxy at a distance of D ≈ 49.59 ± 0.09 (statistical) ±0.54 (systematic) kpc (Pietrzyński et al. 2019)."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Identify 65 compact cores using the 50% peak-intensity contour around intensity peaks (>5 sigma_rms) on 1.2 mm continuum maps (in Paper II), and extract average spectra from primary beam corrected cubes over enclosed pixels.",
  "failed_quote": "The average spectra were computed using the spectral-cube python package (Robitaille et al. 2016) with the pixels enclosed within the 50% peak-intensity contour of the 1.2 mm continuum emission maps."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Solve 1D radiative transfer equation with XCLASS. Fit CH3OH in non-LTE (and LTE for comparison), SO2 and CH3CN in LTE when >2 transitions detected, and fix T for remaining molecules to the CH3OH temperature (or median 27 K). Use a two-layer model (sub-beam hot core + beam-filling cold envelope) for hot cores 4A, 6A, 6B, and 14A.",
  "failed_quote": "With a complete set of molecules presented in Table 3, including definite and tentative detections, we fit the spectra using the XCLASS toolbox"
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Calculate dust and gas masses and H2 column densities from 1.2 mm continuum using XCLASS temperatures (in Paper II), then divide molecular column densities N(X) by N(H2) to obtain fractional abundances.",
  "failed_quote": "We used the temperatures estimated in the current paper to calculate the dust and gas mass of each core, assuming that the 1.2 mm continuum emission originates in optically thin dust with an opacity of 1.04 cm^2 g^-1 (for dust grains coated by thin ice mantels after 10^5 yr of coagulation in a hydrogen density of 10^6 cm^-3, Ossenkopf & Henning 1994) and a gas-to-dust mass ratio of 316 (Sewiło et al. 2022)."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "Dust opacity = 1.04 cm^2 g^-1; gas-to-dust mass ratio = 316 (or 320); metallicity scaling factors: 5 (SMC), 2.6 (LMC), 4 (outer Galaxy)",
  "failed_quote": "assuming that the 1.2 mm continuum emission originates in optically thin dust with an opacity of 1.04 cm^2 g^-1 (for dust grains coated by thin ice mantels after 10^5 yr of coagulation in a hydrogen density of 10^6 cm^-3, Ossenkopf & Henning 1994) and a gas-to-dust mass ratio of 316 (Sewiło et al. 2022)."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "Dust opacity = 1.04 cm^2 g^-1; gas-to-dust mass ratio = 316 (or 320); metallicity scaling factors: 5 (SMC), 2.6 (LMC), 4 (outer Galaxy)",
  "failed_quote": "Then we applied a correction factor of 5, 2.6, and 4 to the abundances of the hot cores in the SMC, LMC, and extreme outer Galaxy to account for differences in metallicity."
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Extracting average spectra from primary beam corrected spectral cubes within the 50% continuum peak-intensity contour",
  "failed_quote": "The average spectra were computed using the spectral-cube python package (Robitaille et al. 2016) with the pixels enclosed within the 50% peak-intensity contour of the 1.2 mm continuum emission maps."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "1D LTE and non-LTE radiative transfer modeling and spectral line fitting",
  "failed_quote": "With a complete set of molecules presented in Table 3, including definite and tentative detections, we fit the spectra using the XCLASS toolbox (eXtended CASA Line Analysis Software Suite; Möller et al. 2017, 2023, with additional extensions, T. Möller, priv. comm.)."
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Mass range of continuum cores = 20–1000 M_sun",
  "failed_quote": "The cores have masses in the range of 20–1000 M_⊙, H2 densities in the range 1.2 × 10^5–4.0 × 10^6 cm^-3, and H2 column densities ranging from 6.0 × 10^22–1.5 × 10^24 cm^-2."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "H2 volume density range of continuum cores = 1.2e5–4.0e6 cm^-3",
  "failed_quote": "The cores have masses in the range of 20–1000 M_⊙, H2 densities in the range 1.2 × 10^5–4.0 × 10^6 cm^-3, and H2 column densities ranging from 6.0 × 10^22–1.5 × 10^24 cm^-2."
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "H2 column density range of continuum cores = 6.0e22–1.5e24 cm^-2",
  "failed_quote": "The cores have masses in the range of 20–1000 M_⊙, H2 densities in the range 1.2 × 10^5–4.0 × 10^6 cm^-3, and H2 column densities ranging from 6.0 × 10^22–1.5 × 10^24 cm^-2."
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Emission measure of H36beta in source 3A = 2.5e6 pc cm^-6",
  "failed_quote": "We used XCLASS to fit the RL emission. For the fit, we fixed the electron temperature to 10^4 K (e.g. Selier & Heydari-Malayeri 2012; Jin et al. 2023) and fit the other three parameters, obtaining an emission measure estimate of 2.5 × 10^6 pc cm^-6, a line width of 18.2 km s^-1, and a velocity offset of 284.4 km s^-1"
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "S-bearing molecules are on average more present and abundant than N- and O-bearing species across the 65 LMC cores, and the four hot cores exhibit the largest SO2 abundances.",
  "failed_quote": "When comparing the different groups of molecules, we observed that S-bearing species are, on average, more abundant than N- and O-bearing species."
 },
 {
  "path": "findings_qualitative[3].evidence[0]",
  "value": "Comparisons with LMC chemical models indicate that initial dust temperatures of 10 to 20 K reproduce the observed hot core abundances, whereas warm initial dust (25 K) underpredicts them.",
  "failed_quote": "Interestingly, only the models where the initial dust temperature is assumed to be between 10 and 20 K reproduce the observed molecular abundances. The chemical model with an initial highest dust temperature of 25 K results in molecular abundances that are much lower than the observed ones."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Possible thermal free-free emission contamination in the 1.2 mm continuum flux for at least the most massive core (3A, where H36beta is tentatively detected), causing core mass, H2 column density, and H2 volume density to be overestimated.",
  "failed_quote": "According to the tentative detection of radio recombination lines toward one of the cores (see Section 3.1), we note that there might be a certain level of contamination from thermal free-free emission in the 1.2 mm continuum fluxes for at least the most massive core. Therefore, the higher-end value of the masses, H2 column, and volume densities may be overestimated."
 }
]
```
