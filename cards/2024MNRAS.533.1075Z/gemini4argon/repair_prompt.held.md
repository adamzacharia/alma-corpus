# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.533.1075Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–20 (2023) Preprint 30 July 2024 Compiled using MNRAS L [A] TEX style file v3.0

## **Filamentary mass accretion towards the high-mass protobinary system** − **G11.92 0.61 MM2**


S. Zhang ( `张遂楠` ), [1] _[,]_ [2] _[★]_ C. J. Cyganowski, [1] J. D. Henshaw, [3] _[,]_ [4] C. L. Brogan, [5] T. R. Hunter, [5] R. Friesen, [6]

I. A. Bonnell, [1] and S. Viti [7]

1 _SUPA, School of Physics and Astronomy, University of St Andrews, St Andrews, Fife, Scotland_
2 _Shanghai Astronomical Observatory, Chinese Academy of Sciences, 80 Nandan Road, Shanghai 200030, P. R. China_
3 _Astrophysics Research Institute, Liverpool John Moores University, 146 Brownlow Hill, Liverpool L3 5RF, UK_
4 _Max Planck Institute for Astronomy, Konigstuhl 17, D-69117 Heidelberg, Germany_
5 _National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903, USA_
6 _University of Toronto, Toronto, ON, Canada_
7 _Leiden Observatory, Leiden University, P.O. Box 9513, NL-2300 RA Leiden, the Netherlands_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

∼
We present deep, sub-arcsecond ( 2000 AU) resolution ALMA 0.82 mm observations of the former high-mass prestellar core
candidate G11.92-0.61 MM2, recently shown to be an ∼500 AU-separation protobinary. Our observations show that G11.92-0.61
MM2, located in the G11.92-0.61 protocluster, lies on a filamentary structure traced by 0.82 mm continuum and N 2 H [+] (4-3)
emission. The N 2 H [+] (4-3) spectra are multi-peaked, indicative of multiple velocity components along the line of sight. To
analyse the gas kinematics, we performed pixel-by-pixel Gaussian decomposition of the N 2 H [+] spectra using SCOUSEPY and
hierarchical clustering of the extracted velocity components using ACORNS. Seventy velocity- and position-coherent clusters
(called "trees") are identified in the N 2 H [+] -emitting gas, with the 8 largest trees accounting for _>_ 60% of the fitted velocity
components. The primary tree, with ∼20% of the fitted velocity components, displays a roughly north-south velocity gradient
along the filamentary structure traced by the 0.82 mm continuum. Analysing a ∼0.17 pc-long substructure, we interpret its
velocity gradient of ∼10.5 km s [−][1] pc [−][1] as tracing filamentary accretion towards MM2 and estimate a mass inflow rate of
∼1.8×10 [−][4] to 1.2×10 [−][3] M ⊙ yr [−][1] . Based on the recent detection of a bipolar molecular outflow associated with MM2, accretion
onto the protobinary is ongoing, likely fed by the larger-scale filamentary accretion flows. If 50% of the filamentary inflow
reaches the protostars, each member of the protobinary would attain a mass of 8 M ⊙ within ∼ 1 _._ 6×10 [5] yr, comparable to the
combined timescale of the 70 _𝜇_ m- and MIR-weak phases derived for ATLASGAL-TOP100 massive clumps using chemical

clocks.


**Key words:** stars: formation – stars: protostars – ISM: kinematics and dynamics – ISM: molecules



**1** **INTRODUCTION**


How mass aggregation proceeds during the formation of high-mass
stars (M ZAMS ≥ 8 M ⊙ ) is a key open question in studies of star
formation and the interstellar medium (ISM). In particular, whether
and how the large-scale (≳ 1 pc) environments of young high-mass
stars affect their mass collection remains unclear: from what spatial
scales do high-mass stars assemble their masses? How does the scale
of the gas reservoir impact the final stellar mass of a high-mass star?
Core accretion models (e.g. McKee & Tan 2002; McKee & Tan
2003) propose that the earliest phase of high-mass star formation is
the high-mass prestellar core: a massive, gravitationally bound, centrally condensed, starless core with a radius ≤0.1 pc. High-mass
prestellar cores are predicted to be self-contained gas reservoirs
nearly in internal virial equilibrium, and initially in pressure equi

_★_ Contact e-mail: sz57@st-andrews.ac.uk


© 2023 The Authors



librium with their environment; they are then expected to undergo
relatively ordered collapse to form single high-mass stars or small
multiple systems (see the review of Tan et al. 2014 and references
therein). However, cores with masses larger than the critical mass
(i.e., the Jeans mass) are expected to fragment (e.g., Dobbs et al.
2005). It thus remains a challenge for the core accretion theory to
explain how a high-mass prestellar core (with ∼10 [2] Jeans masses) is
supported against fragmentation (Tan et al. 2014).


Many numerical simulations have been carried out of the collapse of massive prestellar cores, both with and without magnetic
fields. Radiation-hydrodynamic simulations have demonstrated that
the radiation pressure barrier problem can be overcome by disc accretion and flashlight effects due to outflow cavities (e.g. Krumholz
et al. 2009, Cunningham et al. 2011, Kuiper et al. 2015, Rosen et al.
2019), with gas channelled to the star-disc system by gravitational
and Rayleigh-Taylor instabilities (e.g. Krumholz et al. 2009, Rosen
et al. 2016). Radiation-magnetohydrodynamic (RMHD) simulations

2 _S. Zhang et al._


(e.g. Commerçon et al. 2011, Myers et al. 2013, Rosen & Krumholz
2020, Mignon-Risse et al. 2021) have shown that the combined effects of magnetic fields and radiation can effectively suppress the
initial fragmentation of massive dense cores by increasing the magnetic and thermal Jeans mass of the collapsing gas, contributing to
the formation of massive stars. Recent RMHD simulations of the col
lapse of massive prestellar cores (M = 150 M ⊙, r = 0.1 pc) including
isotropic stellar winds show that accretion onto massive protostars
with masses ≥30 M ⊙ is impeded by their wind feedback, suggesting
that larger-scale dynamical effects are required to form >30 M ⊙ stars
(Rosen 2022).
Searching for high-mass prestellar cores in observations has, however, identified very few candidates in the past decades. Many initially
promising candidates have been ruled out by subsequent observations
that revealed signs of active star formation and/or resolved low-mass
cores. G028C1-S, initially discovered to contain ∼60 M ⊙ within
∼0.09 pc by Tan et al. (2013), has been resolved into two protostars
driving outflows (Tan et al. 2016). Kong et al. (2017) reveal that
G028C9A (∼80 M ⊙ within ∼0.05 pc) actually consists of two lowermass cores. In addition, though identified as one of the best high-mass
prestellar core candidates (∼25 M ⊙ within ∼0.025 pc, Bontemps et al.
2010), CygXN53-MM2 is located close to CygXN53-MM1, a protostar driving outflows, making it difficult to distinguish if CygXN53MM2 is not associated with any outflow (Duarte-Cabral et al. 2013,
Duarte-Cabral et al. 2014). The most promising high-mass prestellar
core candidates identified to date are G11P6-SMA1 (∼30 M ⊙ within
∼0.02 pc, Wang et al. 2014), W43-MM1 core 6 (∼37 M ⊙, ∼1800 AU,
Nony et al. 2018, Molet et al. 2019), AG354 (∼39 M ⊙, Redaelli et al.
2021), and G028.37+00.07 C2c1a (∼23-31 M ⊙, Barnes et al. 2023)
In contrast, in competitive accretion models (e.g. Bonnell et al.
2001, Bonnell et al. 2003) high-mass star formation is closely connected to cluster formation (e.g., Bonnell et al. 2004). The fragmentation of turbulent molecular clouds produce low-mass cores as seeds
of protostars (Bonnell et al. 2003). Protostars that are located near
the centres of protoclusters are more likely to become massive stars,
as these protostars have the advantage in being fed by gas infalling
into the large-scale gravitational potential well of the cluster (e.g.,
Bonnell & Bate 2006). In this picture, the precursors of massive stars
are predicted to accrete gas widely from their large-scale environments, in which case self-contained gas reservoirs (i.e. high-mass
prestellar cores) do not necessarily exist. In numerical simulations
spanning a range of initial conditions – from idealised spheres or
cylinders of turbulent molecular clouds (e.g. Bonnell et al. 2004,
Bonnell et al. 2008, Smith et al. 2009, Maschberger et al. 2010) to
more realistic spiral arm dynamics (e.g. Bonnell et al. 2013, Smilgys
& Bonnell 2016, Smilgys & Bonnell 2017) – and included physics
(such as photoionisation, e.g. Dale & Bonnell 2011, Dale et al. 2012,
and photoionisation plus radiation forces, e.g. Kuiper & Hosokawa
2018), high-mass stars form via significant accretion from r≳0.2 10 pc spatial scales. More recently, by considering supernova-driven
turbulence in magnetohydrodynamic (MHD) simulations of Giant
Molecular Clouds (GMCs), Padoan et al. (2020) found that massive
stars accumulate mass via inertial gas flows from parsec-scale filaments. Additionally, simulations of GMCs formed by supersonic
convergent flows of warm diffuse atomic gas have led to the development of the global hierarchical collapse (GHC) scenario, in which
multi-scale collapse takes place within GMCs and (sub)structures at
all scales (i.e., clouds, clumps, cores) accrete from their larger-scale
environments via non-isotropic gas inflows (e.g. Vázquez-Semadeni
et al. 2007, Gómez & Vázquez-Semadeni 2014, Vázquez-Semadeni
et al. 2017, Vázquez-Semadeni et al. 2019).
Many studies of the accretion reservoirs of forming high-mass



**Figure** **1.** _Spitzer_ GLIMPSE three-colour image (red 8.0 _𝜇_ m, green 4.5
_𝜇_ m, blue 3.6 _𝜇_ m) overlaid with contours of the ALMA Cycle 2 1.05 mm
continuum emission (cyan: [5,15,100] × 0.35 mJy beam [−][1], Cyganowski et al.
2017) and SMA blue- and red-shifted [12] CO (3-2) line emission (blue: [4,6,9]
× 1.0 Jy km s [−][1], red: [4,6,9,12,15,18] × 1.0 Jy km s [−][1], Cyganowski et al.
2014, 2017). The magenta + and black � mark the locations of Class i and
Class ii CH 3 OH masers, respectively, from Cyganowski et al. (2009) and the
black star in MM1 marks the H 2 O maser from Breen & Ellingsen (2011). The
dashed white circle indicates the 50% response level of the primary beam for
our ALMA Band 7 observations. The synthesised beam of the ALMA Cycle
2 1.05 mm continuum image is shown at bottom right.


stars have focused on Infrared Dark Clouds (IRDCs), identified as
extinction features against the Galactic mid-infrared (MIR) background (Butler & Tan 2009, Butler & Tan 2012). IRDCs have been
found to harbour the early phases of high-mass star and cluster formation (e.g., Rathborne et al. 2006, Jackson et al. 2010, Peretto &
Fuller 2010, Kauffmann & Pillai 2010, Miettinen 2012a,b, Ragan
et al. 2012, Kainulainen et al. 2013, Henshaw et al. 2013, Busquet
et al. 2013, Peretto et al. 2013). They often display filamentary morphologies (e.g., Jackson et al. 2010, Henshaw et al. 2013, Beuther
et al. 2015, André et al. 2016), with kinematic features of dense gas
in IRDCs indicating gas flows along filaments (e.g., Zernickel et al.
2013, Tackenberg et al. 2014, Henshaw et al. 2014, Zhang et al. 2015,
Chen et al. 2019). Multiple filaments can merge near the centre of
a molecular cloud to form a hub, a phenomenon referred to as a
"hub-filament system" (e.g. Myers 2009, Schneider et al. 2012, Hennemann et al. 2012). Observations over the past decade have pointed
to hub-filament systems playing a key role in shaping high-mass star
and cluster formation (e.g., Peretto et al. 2013, Peretto et al. 2014,
Henshaw et al. 2017, Tigé et al. 2017, Dewangan et al. 2017, Yuan
et al. 2018, Hacar et al. 2018, Williams et al. 2018, Keown et al.
2019, Treviño-Morales et al. 2019, Chen et al. 2019, Dewangan et al.
2020, Kumar et al. 2020, Wang et al. 2020, Anderson et al. 2021,
Liu et al. 2023, Zhou et al. 2023, Mookerjea et al. 2023), with recent kinematic studies suggesting that hub-filament systems serve
as the parsec-scale gas reservoirs feeding embedded young stars via
filamentary gas flows (e.g., Zhou et al. 2022, Xu et al. 2023).
To investigate the properties of a candidate high-mass prestellar
core and its relationship to its environment, we proposed ALMA Cycle 3-5 observations of G11.92-0.61 MM2 targeting H 2 D [+] (1 1 _,_ 0 -1 1 _,_ 1 )
and N 2 H [+] (4-3), which trace dense and depleted gas (Ceccarelli et al.

























MNRAS **000**, 1–20 (2023)

_Filamentary mass accretion towards G11.92 MM2_ 3



2014) and are commonly observed towards low-mass prestellar cores
(Caselli et al. 2003, van der Tak et al. 2005, Vastel et al. 2006, Caselli
et al. 2008, Friesen et al. 2014, Miettinen 2020, Koumpia et al. 2020,
Redaelli et al. 2021, 2022, Kong et al. 2023). G11.92-0.61 MM2
(hereafter MM2) is one of three massive millimetre cores associated
with the GLIMPSE Extended Green Object (EGO; Cyganowski et al.
2008) G11.92−0.61, which were first detected with the Submillimeter
Array (SMA) and the Combined Array for Research in Millimetrewave Astronomy (CARMA) by Cyganowski et al. (2011a). Subsequent ALMA observations revealed 16 additional low-mass cores
and showed that the G11.92−0.61 protocluster hosts ongoing, simultaneous high- and low-mass star formation (Cyganowski et al. 2017).
MM2 is the second-brightest mm source in the G11.92−0.61 protocluster. The brightest, MM1, has been resolved into a Keplerian
disc around a proto-O star that is forming a binary system via disc
fragmentation (Ilee et al. 2016, 2018).
Located ∼0.12 pc from MM1, MM2 was considered to be a promising high-mass prestellar core candidate because it was a strong and
compact dust continuum source that had no molecular line emission
or other star formation indicators in SMA and VLA observations

(Cyganowski et al. 2014, and references therein). In addition to its
remarkable lack of (sub)mm line emission (no lines detected across
∼24 GHz of bandwidth observed with the SMA at 1.3, 1.1, 0.8 mm;
Cyganowski et al. 2014), no CH 3 OH or H 2 O masers, molecular outflows, or cm continuum emission indicative of ionised gas had been
detected in VLA and SMA imaging covering the G11.92−0.61 region (Hofner & Churchwell 1996; Cyganowski et al. 2009; Breen
& Ellingsen 2011; Cyganowski et al. 2011a,b, 2014; Hunter et al.
2015). The physical properties inferred by Cyganowski et al. (2014)
based on their SMA and VLA data were extreme: M≳30 M ⊙ within
R _<_ 1000 AU and _𝑛_ _𝐻_ 2 _>_ 10 [9] cm [−][3], with _𝑇_ _𝑑𝑢𝑠𝑡_ ∼17-19 K and _𝐿_ ∼57 L ⊙ from submillimeter SED fitting. Based on gas-grain astrochemical modeling using MONACO (Vasyunin et al. 2009), Cyganowski
et al. (2014) found that the lack of line emission observed with
the SMA could be explained with standard chemistry under cold
( _𝑇_ _𝑑𝑢𝑠𝑡_ _<_ 20 K) and very dense ( _𝑛_ _𝐻_ 2 ≫ 10 [8] cm [−][3] ) conditions. Deuterium fractionation is expected to take place at _<_ 20 K, increasing
the abundance of H 2 D [+] (e.g. Caselli & Ceccarelli 2012, Redaelli
et al. 2021). With most C- and O-bearing species frozen out onto
dust grain surfaces, N 2 H [+] becomes abundant as this molecule forms
from the protonation of N 2 in cold environments and is destroyed
mainly by reactions with CO (e.g. Öberg et al. 2005, van ’t Hoff et al.
2017). The expectation of extreme depletion motivated our targeting
H 2 D [+] (1 1 _,_ 0 -1 1 _,_ 1 ) and N 2 H [+] (4-3) in our ALMA Band 7 observations.
Recent high-resolution (≲160 AU) ALMA 1.3 mm observations
targeting MM1 have changed the picture of MM2, revealing that
MM2 is in fact a 505 AU-separation protobinary system (Cyganowski
et al. 2022). The members of the protobinary have 1.3 mm brightness temperatures of 68.4 K and 64.6 K, indicative of internal heating; thus, MM2 is not a high-mass prestellar core but rather hosts
the very early stages of high-mass binary formation (Cyganowski
et al. 2022). Intriguingly, the discovery of a low-velocity asymmetric
bipolar molecular outflow associated with MM2 in our deep ALMA
Band 7 observations (traced by CH 3 OH (4 −1 _,_ 3 -3 0 _,_ 3 ), reported in
Cyganowski et al. 2022) indicates that accretion onto the protobinary
system is ongoing.
In this paper, we present our ALMA Band 7 continuum, H 2 D [+] and
N 2 H [+] observations towards MM2, with a focus on the gas kinematics around MM2 traced by the N 2 H [+] (4-3) emission. In Section 2,
we provide details of the observations. In Section 3, we show the
results for the dust continuum and molecular line emission. In Sec
tion 4, we describe the procedure used to perform Gaussian decom


position on the N 2 H [+] data cube and in Section 5, we describe the
hierarchical clustering analysis. Section 6 presents our analysis of
the physical properties of the filamentary accretion flows, which are
further discussed in Section 7. Section 8 summarises our main con
clusions. Throughout this work, we assume that MM2 is located at
the same distance as MM1 and adopt MM1’s maser parallax distance
of 3.37 [+] − [0] 0 _[.]_ _._ [39] 32 [kpc (][Sato et al. 2014][).]


**2** **ALMA OBSERVATIONS**


We observed G11.92-0.61 MM2 at 0.82 mm with the ALMA 12-m ar
ray in Cycles 3-5 (project codes 2015.1.00827.S and 2017.1.01373.S,
PI C. Cyganowski). The phase centre of the single-pointing observations was 18 [h] 13 [m] 57 [s] .8599 −18 [◦] 54 [′] 13 [′′] _._ 958 (ICRS); at 0.82 mm, the
full width half power (FWHP) size of the primary beam is ∼17 [′′] (see
Figure 1). Additional observational parameters, including observing
dates, configurations, and calibrators, are listed in Table 1. The projected baselines of the combined dataset range from ∼14–583 k _𝜆_,
corresponding to a largest angular scale (LAS) [1] of ∼4 [′′] _._ 5 (∼0.07 pc

∼
15200 AU at D=3.37 kpc).
The correlator setup included four spectral windows
(spws): three narrow spws tuned to cover H 2 D [+] (1 1 _,_ 0 –
1 1 _,_ 1 ) ( _𝜈_ rest =372.421 GHz, _𝐸_ _𝑢𝑝𝑝𝑒𝑟_ =104.2 K), N 2 H [+] (43) ( _𝜈_ rest =372.672 GHz, _𝐸_ _𝑢𝑝𝑝𝑒𝑟_ =44.7 K), and DCO [+] (5-4)
( _𝜈_ rest =360.170 GHz, _𝐸_ _𝑢𝑝𝑝𝑒𝑟_ =51.9 K) [2], and a wide spw, centred at ∼358.02 GHz, for continuum sensitivity. The observed
bandwidths and spectral resolutions (accounting for online Hanning
smoothing and channel averaging) were 117.2 MHz (∼94 km s [−][1] )
and 0.122 MHz (∼0.098 km s [−][1] ) for H 2 D [+], 58.6 MHz (∼47 km s [−][1] )
and 0.061 MHz (∼0.049 km s [−][1] ) for N 2 H [+], 243.4 MHz (∼195
km s [−][1] ) and 0.141 MHz (∼0.117 km s [−][1] ) for DCO [+], and 1875 MHz
(∼1570 km s [−][1] ) and 1.129 MHz (∼0.945 km s [−][1] ) for the wide spw.
The data were calibrated using the CASA 5.4.0 version of the
ALMA science pipeline. Line-free channels were identified using the
approach of Brogan et al. (2016); Cyganowski et al. (2017) and used
to construct a pseudo-continuum data set, which has an aggregate
continuum bandwidth of ∼0.44 GHz. These continuum data were

iteratively self-calibrated, and the solutions were then applied to the
line data. The final continuum image, made using multi-frequency
synthesis, multiscale clean, and Briggs weighting with a robust parameter R = 0.5, has an rms noise level of 1 _𝜎_ =0.5 mJy beam [−][1] and
a synthesised beam size of 0.575 [′′] × 0.431 [′′] (P.A.=−80 [◦] ), equivalent to ∼1940 AU × 1450 AU at D=3.37 kpc. In this paper, we
consider only the continuum, N 2 H [+], and H 2 D [+] data; images of the
CH 3 OH (4 −1 _,_ 3 -3 0 _,_ 3 ) line, included in the wide spw, were presented
in Cyganowski et al. (2022) (see also Section 1). The N 2 H [+] line
data were imaged with multiscale clean, Briggs weighting with a
robust parameter R=0.5, and a velocity resolution Δv=0.2 km s [−][1] .
The resulting N 2 H [+] (4-3) image cube has a synthesised beam size
of 0.651 [′′] × 0.442 [′′] (P.A.=−79 [◦] ) and an rms noise level of 1 _𝜎_ =5.9
mJy beam [−][1] . To maximise sensitivity, the H 2 D [+] line data were imaged with multiscale clean, Briggs weighting with a robust parameter R=2, and a velocity resolution Δv=0.4 km s [−][1] . The resulting
H 2 D [+] (1 1 _,_ 0 –1 1 _,_ 1 ) image cube has a synthesised beam size of 0 [′′] _._ 762
× 0 [′′] _._ 551 (P.A. −75 [◦] ) and an rms noise level of 1 _𝜎_ =2.7 mJy beam [−][1] .


1 Estimated from the fifth percentile shortest baseline using the analysisUtils
(Hunter et al. 2023) task `au.estimateMRS` .
2 Line rest frequencies are from CDMS (Müller et al. 2001, 2005), accessed
via the Splatalogue NRAO spectral line catalogue ( `[https://splatalogue.](https://splatalogue.online/)`
`[online/](https://splatalogue.online/)` ).


MNRAS **000**, 1–20 (2023)

4 _S. Zhang et al._


**Table 1.** Summary of ALMA 0.82 mm observations.


Project code Observing date Configuration Number of antennas Time on-source Calibrators
Gain Bandpass Flux
2015.1.00827.S 2016 April 9 _[𝑎]_ C36-2/3 43 2× 42.5 min J1733-1304 J1924-2914 J1924-2914, Titan
2015.1.00827.S 2017 April 22 C40-3 41 42.5 min J1733-1304 J1924-2914 Titan
2015.1.00827.S 2017 April 26 C40-3 41 42.5 min J1733-1304 J1924-2914 Titan
2017.1.01373.S 2018 July 10 C43-1 46 46.5 min J1911-2006 J1924-2914 J1924-2914
2017.1.01373.S 2018 August 16 C43-2 43-44 3× 46.5 min J1911-2006 J1924-2914 J1924-2914


_𝑎_ Due to a tuning issue, the correlator setup on this date did not cover N 2 H + (4-3).



All measurements were made from images corrected for the primary
beam response.


**3** **RESULTS**


**3.1** **ALMA 0.82 mm continuum emission**


The ALMA 0.82 mm continuum image is shown in Figure 2 (in
colourscale in (a) and as contours in (b) and (c)). As expected, the
0.82 mm continuum emission displays a broadly similar morphology
to the ALMA 1.05 mm continuum emission observed with similar an
gular resolution and sensitivity by Cyganowski et al. (2017) (1.05 mm
_𝜃_ syn =0 [′′] _._ 49 × 0 [′′] _._ 34, _𝜎_ =0.35 mJy beam [−][1] ). In the 0.82 mm continuum
image, MM2 is located on a filamentary structure that extends to the
north and southeast of MM2; this structure encompasses the MM8,
MM10, and MM16 cores identified by Cyganowski et al. (2017). To
the southeast, the extended 0.82 mm continuum emission "bridges"
MM2 and the proto-O star MM1 (Ilee et al. 2016, 2018). To the east
of MM2, ∼ 5 _𝜎_ extended emission also connects the dust continuum
sources MM3 and MM5 (Cyganowski et al. 2017, see Figure 1) to
the main north-southeast dust filament, with the extended emission
joining the main filamentary structure to the northeast of MM2. The
MM7/MM9/MM13/MM17 group of mm sources (Cyganowski et al.
2017, Figure 1), located north of MM2, is also detected in 0.82 mm
continuum emission (see Figure 2).
At the ∼0 [′′] _._ 5-resolution of our 0.82 mm image, MM2 appears
as a strong, compact source of submillimetre continuum emission
within the larger filamentary structure. To estimate the 0.82 mm
properties of MM2, we fit a one-component two-dimensional Gaussian model to its 0.82 mm continuum emission using the CASA
task `imfit` . From this one-component Gaussian fit, the fitted peak
intensity of MM2 is I peak =158.3±0.6 mJy beam [−][1] and its fitted
integrated flux density is S 0 _._ 82mm =390±2 mJy. The fitted position of MM2 is 18 [h] 13 [m] 57 [s] _._ 86094±0 [s] _._ 00009, −18 [◦] 54 [′] 14 [′′] _._ 023±0 [′′] _._ 001
(J2000) and its deconvolved size is 614(±5) mas × 584(±4) mas
(P.A.=87 [◦] ±8 [◦] ), equivalent to ∼ 2070 AU × 1970 AU at D=3.37 kpc.
Notably, the single-component fit underestimates the peak intensity
of MM2’s 0.82 mm continuum emission: the residual image has a
∼27 mJy beam [−][1] peak, which is _<_ 0 [′′] _._ 02 from the fitted centroid
position, surrounded by a negative ring. This indicates that a singlecomponent Gaussian does not fully represent the emission, and points
to the presence of additional substructure(s). This is consistent with
the results from higher-resolution ALMA observations, where MM2
is resolved to be a protobinary system with a projected separation
of ∼500 AU (Cyganowski et al. 2022, see also Section 1). To check
the robustness of the integrated flux density measurement from the
Gaussian fit, we also use the CASA task `imstat` to measure the integrated flux density within the 30 _𝜎_ contour around MM2 and within
a 2 [′′] _._ 0×1 [′′] _._ 0 ellipse centred on its fitted position. These methods yield
integrated flux density estimates of 401±40 mJy and 327±33 mJy,


MNRAS **000**, 1–20 (2023)



respectively, [3] within _<_ 3%-16% of the value from the Gaussian fit.
This comparison suggests that the single-component Gaussian fit
provides a reasonably robust estimate for the 0.82 mm integrated
flux density of MM2, though we note that all estimates potentially
include a contribution from the background filament emission (see
also Section 6.2).


**3.2** **Molecular lines**


_3.2.1_ _H_ 2 _D_ [+] _(1_ 1 _,_ 0 _-1_ 1 _,_ 1 _)_


H 2 D [+] (1 1 _,_ 0 -1 1 _,_ 1 ) is undetected towards MM2 in our observations,
to a 4 _𝜎_ limit of 10.8 mJy beam [−][1] (equivalent to a 4 _𝜎_ brightness
temperature limit of 0.23 K). The nondetection of H 2 D [+] towards
MM2 is unsurprising, since MM2 is now known to host a protobinary system with two internally-heated protostars (Cyganowski et al.
2022, see Section 1). H 2 D [+] is destroyed by gas-phase reactions with
CO, which evaporates from grains at temperatures _>_ 20 K; thus,
H 2 D [+] (1 1 _,_ 0 -1 1 _,_ 1) emission is only expected in the pre-stellar phase
(e.g. Redaelli et al. 2021). Indeed, the few reported interferometric
(ALMA) detections of H 2 D [+] (1 1 _,_ 0 -1 1 _,_ 1) in high-mass star-forming
regions in the literature are towards very quiescent, MIR-dark clumps
and regions of IRDCs (e.g. Redaelli et al. 2021; Kong et al. 2023). In
the more evolved cluster environment of G11.92−0.61, where there
are many protostars heating the gas (including the MIR-bright massive protostars MM1 and MM3), H 2 D [+] emission would only have
been expected towards the cold, dense interior of a massive starless

core.


_3.2.2_ _N_ 2 _H_ [+] _(4-3)_


As shown in Figure 2, extensive N 2 H [+] (4-3) emission is detected
around MM2 in our ALMA observations. Notably, the morphology
of the integrated N 2 H [+] (4-3) emission differs markedly from that
of the 0.82 mm continuum (see Figure 2a), with the peaks of the
integrated N 2 H [+] emission clearly offset from the continuum peak of
MM2. The integrated N 2 H [+] (4-3) emission surrounding MM2 peaks
to its northwest and southwest, at offsets of ∼0 [′′] _._ 9 (∼3000 AU) and
∼1 [′′] _._ 2 (∼4000 AU) from the continuum peak, respectively. Other than
the peaks near MM2, the most significant feature in the N 2 H [+] (43) integrated intensity map is a bow-like structure located towards
the red-shifted lobe of the high-velocity bipolar molecular outflow
driven by MM1 (Figure 1, see also Cyganowski et al. 2011a, 2017).
This intriguing feature, which may be associated with bow shocks
caused by protostellar feedback from the proto-O star MM1, will be
discussed in detail in a separate publication. The bow-like feature is


3 Uncertainties are estimated using Equation (1) of Thwala et al. (2019),
assuming 10% absolute flux calibration uncertainty for ALMA in Band 7
(Cortes et al. 2023).

_Filamentary mass accretion towards G11.92 MM2_ 5


**Figure 2.** (a): ALMA 0.82 mm continuum (colourscale) overlaid with contours of integrated N 2 H [+] (4-3) emission (velocity range: 27.0 - 42.0 km s [−][1] ; levels:
0.06 Jy km s [−][1] × [-2,5,10,15,20], negative contours shown as dashed lines). The arrow marks the bow-like feature discussed in Section 3.2.2 and the synthesised
beams of the 0.82 mm continuum image and N 2 H [+] cube are shown at bottom left (in cyan) and right (in black), respectively. (b): ALMA N 2 H [+] peak intensity
map (colourscale) overlaid with 0.82 mm continuum contours. (c): N 2 H [+] (4-3) moment 1 map (colourscale) overlaid with 0.82 mm continuum contours. In the
moment 1 map, pixels with line emission _<_ 4 × _𝜎_ npb, where _𝜎_ npb =4.7mJy beam [−][1] is the rms of the N 2 H [+] cube before primary beam correction, are masked and
shown in grey. _𝑣_ LSR (MM1)= 35.2±0.4 km s [−][1] (from compact molecular line emission observed with the SMA; Cyganowski et al. 2011a); Cyganowski et al.
(2022) estimate _𝑣_ LSR (MM2)∼37 km s [−][1] based on the velocity of the peak CH 3 OH emission from the filament at the protobinary position. The ALMA images
shown here have not been corrected for the primary beam response; all measurements were made from corrected images and corrected images are shown in
Figure 3. In (b) and (c), the 0.82 mm continuum contour levels are _𝜎_ npb =0.48 mJy beam [−][1] × [-2,4,16,40,160,280], where _𝜎_ npb =0.48 mJy beam [−][1] is the rms of
the 0.82 mm continuum image before primary beam correction. In all panels, the edge of the colourscale corresponds to the 20% response level of the ALMA
primary beam.



also visible in the N 2 H [+] (4-3) peak intensity map in Figure 2b, which
shows that the strongest N 2 H [+] emission (543 mJy beam [−][1], SNR∼92)
is detected towards the filamentary structure to the southeast of MM2.


The intensity-weighted velocity (moment 1) map of the N 2 H [+] (43) emission is shown in Figure 2c; however, examination of the data
cube indicates that the spectra are in general too complex for the gas
kinematics to be captured by a moment analysis. This complexity
is illustrated by the sample spectra presented in Figure 3. As shown
by panels A-C, the line profiles of the N 2 H [+] (4-3) emission display
significant spatial variation across the mapped region. In addition
to negative bowls associated with missing short-spacing information
(panel D, see also Section 2), N 2 H [+] (4-3) absorption is detected
against the submillimetre continuum towards MM2 (Figure 3 panel
B). As noted above and shown in Figure 3, the N 2 H [+] spectra are
in general complex, with multiple emission peaks and/or absorption
features. N 2 H [+] (4-3) has 38 hyperfine structures (hfs) components
spaced over ≲ 4 _._ 3 km s [−][1] (Pagani et al. 2009). To assess the potential
contribution of the hfs to the observed line profiles, we calculate
the relative line strengths of the hfs components using the methods
described in Daniel et al. (2006), and plot them in Panel D of Figure 3.
The strongest hfs components (with relative line strengths _>_ 0.1) are
tightly grouped within ≲0.2 km s [−][1] (i.e. within one channel in our
image cube, which has Δv=0.2 km s [−][1] ; Section 2). We therefore
argue that while the hfs will have some effect on the line profiles
(as discussed further in Section 7.3), the multiple emission peaks
observed in the spectra are predominantly caused by multiple velocity
components present along the line of sight in the N 2 H [+] -emitting gas
surrounding MM2.


We note that these observations are, to our knowledge, the first
reported interferometric detection of N 2 H [+] (4-3) in a high-mass
star-forming region. N 2 H [+] (4-3) has been detected with ALMA in a



protoplanetary disc (where this transition was used to trace the CO
snowline; Qi et al. 2013) and towards low-mass cores in Ophiuchus
(Friesen et al. 2014). Interferometric observations of this transition
are, however, relatively uncommon, as it is more challenging to observe than lower-frequency N 2 H [+] transitions (see also Section 7.3),
which likely accounts for the lack of previous detections in highmass star-forming regions. With single dish telescopes, N 2 H [+] (4-3)
has been detected towards many low- and high-mass star-forming
regions, with beams corresponding to physical resolutions of ∼2000

- 86000 AU (e.g. van Dishoeck et al. 1992, Blake et al. 1995, Stark
et al. 1999, Friesen et al. 2010, Pillai et al. 2012, Ma et al. 2013, Kong
et al. 2016, Miettinen 2020, Koumpia et al. 2020). For N 2 H [+] (4-3)
detections in nearby regions, the physical scale of the JCMT beam
is similar to that of the synthesised beam of our ALMA data. The
observations of Ophiuchus B2, L1544 and L1521f by Friesen et al.
(2010) and Koumpia et al. (2020), for example, have a resolution of
∼2000 AU and 1 _𝜎_ rms noise of ∼0.03-0.06 K (compared to _𝜎_ _𝑇_ _𝑏_ ∼
0.19 K for our data). Interestingly, in these observations, while N 2 H [+]

is generally detected towards regions with submillimetre continuum
emission, the strongest N 2 H [+] (4-3) emission is found offset from the
submillimetre continuum peaks (Friesen et al. 2010; Koumpia et al.
2020), as we observe in G11.92−0.61. Friesen et al. (2014) also report an offset between the N 2 H [+] (4-3) and submillimetre continuum
peaks in their ALMA study of low-mass cores in Ophiuchus, though
these observations probe much smaller spatial scales ( _<_ 200 AU) and
the authors note that the observations are significantly affected by
self-absorption and missing short spacing data.


MNRAS **000**, 1–20 (2023)

6 _S. Zhang et al._


**Figure 3.** Top left: ALMA N 2 H [+] (4-3) integrated intensity map (integrated over v = 27.0 - 42.0 km s [−][1], colourscale and white contours, levels 0.066 Jy km s [−][1] ×

[-2,5,10,15,20], negative contours shown as dashed lines) overlaid with contours of the ALMA 0.82 mm continuum emission (black, levels: 0.5 mJy beam [−][1] ×

[5,15,40,160,280]), both corrected for the primary beam response. The edge of the colourscale corresponds to the 20% response level of the ALMA primary
beam and the synthesised beams of the N 2 H [+] cube and the 0.82 mm continuum image are shown at bottom left (unfilled ellipse) and right (filled black ellipse),
respectively. Panels labelled with letters show the N 2 H [+] spectra extracted from the primary-beam-corrected image cube at the corresponding labelled locations
on the integrated intensity map. Location A is the local peak of the integrated N 2 H [+] emission to the north of MM2, B is the 0.82 mm continuum peak of MM2,
C is the local peak of the integrated N 2 H [+] emission to the south of MM2, and D is a representative negative bowl. The red vertical lines overlaid in Panel D
indicate the relative line strengths of the 38 hyperfine components of the N 2 H [+] (4-3) transition (see Section 3.2.2) for _𝑣_ lsr =35.0 km s [−][1] .



**4** **GAUSSIAN DECOMPOSITION ON THE N** 2 **H** [+] **(4-3) CUBE**


**4.1** **Gaussian Decomposition with SCOUSEPY**


To study the gas kinematics in the vicinity of MM2, we first apply Gaussian Decomposition to the N 2 H [+] (4-3) cube using the
SCOUSEPY package (Henshaw et al. 2016, Henshaw et al. 2019).
SCOUSEPY is a Python implementation of the Semi-Automated
multi-COmponent Universal Spectral-line fitting Engine (SCOUSE),
designed to apply Gaussian Decomposition to large volumes of complex spectra in a semi-automated way. The SCOUSEPY version used
in this work can be downloaded from github [4] . The workflow consists
of four stages, as outlined below.


4 `[https://github.com/jdhenshaw/scousepy/tree/delta](https://github.com/jdhenshaw/scousepy/tree/delta)`


MNRAS **000**, 1–20 (2023)



In stage 1), SCOUSEPY generates Spectral Averaging Areas
(SAAs) and the spectra of SAAs based on spectral complexity. A
5 _𝜎_ mask (∼ 54 mJy beam [−][1] ) was first applied to remove emissionfree regions from the analyses that follow. As this dataset exhibits
strong spatial variation, we chose a conservative SAA size of 20 pix
∼
els ( 5300 AU) with a filling factor of 0.6 [5] . The velocity range and
pixel range are set to include the whole data cube. Other parameters
are kept at their default values. With these parameters applied to the
N 2 H [+] data cube, SCOUSEPY generates 452 SAAs along with their
spectra; as they are Nyquist sampled, each SAA overlaps with neigh

5 This filling factor selects SAAs with significant emission in more than 60%
of the enclosed pixels; see SCOUSEPY documentation (linked from github)
and Henshaw et al. (2016) for additional details.

_Filamentary mass accretion towards G11.92 MM2_ 7



**Table** **2.** Summary of tolerance levels used in stage 3 of the Gaussian Decomposition using SCOUSEPY.


Parameter version 0 version 1 version 2

_𝑇_ 0 2.0 2.0 2.0
_𝑇_ 1 3.0 3.0 3.0
_𝑇_ 2 1.0 1.0 1.0
_𝑇_ 3 2.5 4.0 2.5
_𝑇_ 4 2.5 2.5 1.0
_𝑇_ 5 0.5 0.5 0.5


bouring SAAs. In the area covered by SAAs, the program identifies a
total of 48141 individual spectra (corresponding to individual pixels
in the data cube) to be analysed.
In stage 2), SCOUSEPY applies Gaussian Decomposition to the
452 spectra of SAAs generated in stage 1). The SCOUSEPY version
used in this work has introduced derivative spectroscopy (Lindner
et al. 2015, Riener et al. 2019) to assist with multi-component Gaussian fitting. The program will first filter spectra with Gaussian kernels
and then calculate derivatives of the smoothed spectra up to the fourth
order. The derivative spectroscopy technique measures the locations
of spectral components by searching for “bumps”, which mathematically means the local minimum of negative curvature in the filtered
spectra (i.e. second derivative _<_ 0, third derivative = 0, and fourth
derivative _>_ 0, see details in Lindner et al. 2015). SCOUSEPY first
fits the spectra with initial guesses adopted from the measurements of
derivative spectroscopy. The fitting is controlled by two input parameters: the Signal-to-Noise Ratio (SNR) and the standard deviation
of the Gaussian kernel ( _𝜎_ ker ) used for filtering. We vary the SNR
from 3 to 5 and the _𝜎_ ker from 1 to 3 channels to obtain satisfying fits
for ≳ 96% of the SAA spectra; for an additional four SAA spectra,
increasing the SNR to 7-9 yields reasonable fits. For the remaining
SAA spectra, we use the manual fitting option of SCOUSEPY to fit
the spectra "by hand" to obtain physically reasonable fits. In some
cases, for example, derivative spectroscopy fits artificially broad redshifted components; we manually fit multiple weak components to
the red tails of these spectra to obtain physically reasonable fits. There
is only one spectrum (out of the 452 SAA spectra) which cannot be
fitted well either by the derivative spectroscopy fitting or manual
fitting. We flag the corresponding SAA at the end of stage (2) so that
the problematic fit is not used to provide initial guesses for fits to
individual spectra. The problematic SAA overlaps with neighbouring
SAAs, so SCOUSEPY fits the spectra of the pixels within the flagged
SAA based on the fits for the surrounding SAAs.
Stage 3) uses the fits for the spectra of SAAs as initial guesses to
conduct Gaussian Decomposition for the 48141 individual spectra.
SCOUSEPY adopts the fits from stage (2) as initial guesses and applies automated Gaussian Decomposition to the individual spectra
within each SAA. To control the process of automated Gaussian Decomposition, users set tolerance levels using six parameters: _𝑇_ 0, _𝑇_ 1,
_𝑇_ 2, _𝑇_ 3, _𝑇_ 4 and _𝑇_ 5 . _𝑇_ 0 is newly introduced to the SCOUSEPY version
used here. It limits the maximum difference between the number

of fitted components for spatially averaged spectra and individual
spectra. _𝑇_ 1 sets the threshold for amplitude, below which weak components are discarded before subsequent analyses. _𝑇_ 2 and _𝑇_ 3 control
the full width at half-maximum (FWHM) of fitted components; _𝑇_ 4
limits the centroid velocity. _𝑇_ 5 sets the minimum separation in centroid velocity between two adjacent Gaussian components. Detailed
descriptions of these parameters can be found in Henshaw et al.
(2016).
In the final stage, SCOUSEPY selects the best-fitting models with
Akaike information criterion (AIC) for the 48141 individual spectra.



As SAAs are Nyquist sampled, each of the individual spectra may
hold multiple solutions of Gaussian Decomposition. The program
identifies locations with multiple models and chooses the models
with the lowest AIC values as the best-fitting ones.
We first run SCOUSEPY with default tolerance levels in stage 3:
we refer to these results as "version 0". This version generates reasonable fits for ∼ 80% of the spectra. However, given the complicated
spectral structure and significant spatial variation of this dataset, the
automated fitting could miss or overfit components at certain regions.
For example, in version 0 SCOUSEPY identifies two adjacent peaks
as a single velocity component a few pixels to the north of MM2.
Therefore, a single set of tolerance levels may not be ideal for the
whole dataset. To test the performance of automated fitting, we run
stage 3) with another two sets of tolerance levels labelled as version
1 and version 2. In version 1, we relax the _𝑇_ 3 constraint on the maximum velocity dispersion of fitted components by 60% compared
with version 0; in version 2, we tighten the _𝑇_ 4 constraint on the fitted
centroid velocity to 40% of the value in version 0 (see Table 2). We
compile all the results from the three versions and select the models
with the lowest AIC values as the best-fitting ones. More than 79%
of the final best-fitting models are adopted from version 0; while 8%
are taken from version 1 and 3% from version 2. For ∼ 9 _._ 7% of the

pixels within the mask applied in stage 1, SCOUSEPY could not find
best-fitting models which satisfy all the conditions mentioned above.
The tolerance levels applied in each version are summarized in Table
2. The contribution of each version to the final results is shown in
the left panel of Fig 4. Examples of the SCOUSEPY fits to the N 2 H [+]

spectra are shown in Fig. A1.
We note that SCOUSEPY is not designed to reproduce absorption and that Gaussian Decomposition is applied only to the N 2 H [+]

emission. The analyses described below also focus only on the N 2 H [+]

emission features.


**4.2** **Results and basic statistics**


We obtain best-fitting models for 43079 spectra, and a total of 96157
Gaussian velocity components. This corresponds to an average of
∼ 2 _._ 2 components per pixel. Indeed, more than 66% of the spectra
are fitted with models containing multiple velocity components. The
right panel of Figure 4 shows the distribution of the number of
velocity components at each pixel. Pixels with zero components do
not have accepted models (see Section 4.1). SCOUSEPY fits from 1
to 6 components to individual spectra (with no maximum number of
components imposed), with a median number of components of 2.
As illustrated by the right-hand panel of Figure 4, the complexity of
the velocity structure varies spatially. The vicinity of MM2 is among
the regions with the most complex spectra: to the north of MM2, the
median number of components/pixel reaches 4, and to the south of
MM2 the median number of components/pixel is 3.
The top panel of Figure 5 presents a histogram of the centroid velocities of the best-fit components. The centroid velocities range from
27.6 to 42.1 km s [−][1], with a mean of 35.7 km s [−][1], a standard deviation
of 1.8 km s [−][1], and an interquartile range of 2.7 km s [−][1] . The velocity
histogram deviates from a Gaussian-like distribution in having two
main groups of peaks, at ∼ 34 _._ 5 and ∼ 37 km s [−][1], possibly indicative
of large-scale velocity gradients across the region. Sharp spikes and
shoulders are also visible, reflecting complex velocity substructures
on small spatial scales. The bottom panel of Figure 5 plots amplitude
against centroid velocity for all fitted components. The fitted amplitudes range from ∼12.5 mJy beam [−][1] to ∼539.4 mJy beam [−][1], with a
median of ∼ 93.3 mJy beam [−][1] . The strongest components generally


MNRAS **000**, 1–20 (2023)

8 _S. Zhang et al._


**Figure** **4.** Left: the version of the best-fitting model employed in the final compiled solution for each of the 48141 individual spectra. The numbers on the
colourbar correspond to the versions described in Section 4.1. Right: distribution of the number of velocity components in the best-fitting models. Red circles
mark the locations of the 10 spectra selected for hyperfine structure fitting (see Section 7.3). ALMA 0.82 mm continuum contours (white, levels: 0.5mJy beam [−][1] ×

[5,15,40,160,280]) are overlaid in both panels.



fall within the interquartile range in velocity, while the components
on the tails of velocity distribution are generally weaker.


The fitted velocity dispersion ranges from 0.1 to 4.6 km s [−][1], with
a median of 0.4 km s [−][1] and an interquartile range of 0.3 km s [−][1] . As
shown in Figure 6, the histogram of _𝜎_ _𝑣_ is highly asymmetric, with
a tail extending to 12× the median value. This asymmetry is also reflected in a positive skewness of ∼ 2 _._ 6. We therefore present median
and interquartile values instead of mean and standard deviation values to better describe the concentration and dispersion of _𝜎_ _𝑣_ . Investigating the spatial distribution of the high-velocity-dispersion tail,
we find that the highest-dispersion components (99.9th percentile,
_𝜎_ _𝑣_ - 2.5 km s [−][1] ), shown as green crosses in Figure 7, are associated with the protostellar outflows from MM7/9 and from MM1
and/or MM3 (Cyganowski et al. 2011a, 2014, 2017). As shown in
Figure 7, many components with 1.3 km s [−][1] < _𝜎_ _𝑣_ < 2.5 km s [−][1]

(99th to 99.9th percentile, shown as yellow crosses) are also spatially
associated with the outflows from MM1/3/7/9 or with MM2’s out
flow, though some broad components are also distributed along the
north-southeast filamentary structure near MM2. (We focus here on
high-dispersion points within the FWHP extent of the ALMA primary beam, where the data are most sensitive, see Fig. 7.) The spatial
correlation between many high-velocity-dispersion components and
known protostellar outflows indicates that we are observing the imprint of protostellar feedback on the dense molecular gas, which


MNRAS **000**, 1–20 (2023)



will be discussed in detail, in conjunction with the bow-like feature
mentioned in Section 3.2.2, in a separate publication.


**5** **HIERARCHICAL CLUSTERING OF VELOCITY**

**COMPONENTS**


**5.1** **Hierarchical clustering with ACORNS**


To further analyse the velocity structure within the N 2 H [+] -emitting
gas, we conduct hierarchical clustering of the velocity components
extracted in Section 4 using ACORNS [6] (Agglomerative Clustering
for Organising Nested Structures, Henshaw et al. 2019). ACORNS
is designed to characterise the hierarchical structure within discrete spectroscopic data (e.g. data points in position-position-velocity
space) based on the hierarchical agglomerative clustering technique.
A comprehensive description of the philosophy and parameters of
this package can be found in Henshaw et al. (2019) Appendix B.
Before running the ACORNS clustering, we perform a cleaning
of the velocity components extracted by SCOUSEPY. We discard

∼
all pixels without fits ( 5% of the total SCOUSEPY data), remove
components with peak intensities _<_ 3 _𝜎_ (where _𝜎_ is the rms, measured


6 ACORNS is a publicly available Python package, and can be downloaded
from https://github.com/jdhenshaw/acorns.

_Filamentary mass accretion towards G11.92 MM2_ 9















**Figure 5.** Top: histogram of centroid velocities for the best-fitting components
(bin size: 0.25 km s [−][1] ). Bottom: fitted amplitudes of velocity components
versus centroid velocity.


**Figure** **6.** Histogram of velocity dispersion for the best-fitting components
(bin size: 0.06 km s [−][1] ).


individually for each spectrum), and remove components where either the peak intensity or the velocity dispersion is smaller than its
associated uncertainty. We then conduct the ACORNS clustering
only on the remaining velocity components, which represent ∼94%
of the total number of extracted components.
We first perform ACORNS clustering of the SCOUSEPY fits in
position-position-velocity space, with parameters based on the spatial
and spectral resolution of our N 2 H [+] data. The minimum radius of
a cluster is set to 4× the pixel size to ensure that the minimum
number of data points in a cluster is comparable to the number of
pixels in a synthesised beam (∼52). The minimum height above



**Figure 7.** Spatial distribution of fitted velocity components with high velocity dispersions: yellow crosses mark 1.3 km s [−][1] < _𝜎_ _𝑣_ < 2.5 km s [−][1] and
green crosses mark _𝜎_ _𝑣_ - 2.5 km s [−][1], where 1.3 km s [−][1] and 2.5 km s [−][1] are
the 99 _[𝑡ℎ]_ and 99.9 _[𝑡ℎ]_ percentile of the velocity dispersion distribution. Contours show the ALMA 0.82 mm continuum (black, levels: 0.5mJy beam [−][1] ×

[5,15,40,160,280]), SMA blue- and red-shifted [12] CO (3-2) line emission
from Cyganowski et al. (2014, 2017) (blue: [4,6,9] × 1.0 Jy km s [−][1], red:

[4,6,9,12,15,18] × 1.0 Jy km s [−][1] ), and ALMA blue- and red-shifted CH 3 OH
(4 −1 _,_ 3 -3 0 _,_ 3 ) line emission from Cyganowski et al. (2022) (cyan: [4,7,10,15]
× _𝜎_ = 5.5 mJy km s [−][1], magenta: [4,7] × _𝜎_ = 3.3 mJy km s [−][1] ). Contours
are from images corrected for the primary beam response. The dashed black
circle shows the FWHP (50% response) level of the ALMA primary beam,
and the ALMA images are masked at its 20% response level.


the merge level is set to be 3× the mean rms and the maximum
absolute velocity difference between two components identified as
linked is set to 0.2 km s [−][1], the channel width of the N 2 H [+] image
cube (Section 2). We add an additional clustering criterion based on
the velocity dispersion, requiring the absolute difference in velocity
dispersion between two linked components to be smaller than 0.2
km s [−][1] . With these parameters, ACORNS identifies a total of 198
clusters, which contain ∼ 95% of the input velocity components.
To investigate the sensitivity of the ACORNS results to the choice
of input parameters, we performed additional clustering runs varying
the peak intensity cutoff and the relaxation of linking lengths. In
these tests, we found that applying a 5 _𝜎_ (rather than 3 _𝜎_ ) threshold
to the velocity components excluded a significant amount of data

∼
( 23%) and so did not reflect the extended structure of clusters. We
then tested the clustering criteria for position, velocity, and velocity
dispersion with different relaxation levels of linking lengths, relaxing
the linking criteria by 20% and 50% to enable clusters to grow. These
tests showed that the clustering results are relatively robust against
relaxation: the percentage of data points assigned to clusters grew
by only ∼0.3% and ∼0.8% in the 20% and 50% relaxed versions
respectively, indicating that the vast majority of pixels are clustered
without the need for relaxing the criteria. Based on these results, we
adopt the original clustering run described above, with a 3 _𝜎_ cutoff
and without relaxing the linking criteria, for the remainder of our
analysis.


MNRAS **000**, 1–20 (2023)

10 _S. Zhang et al._


**Figure 8.** Dendrogram of the hierarchical system in the N 2 H [+] (4-3)-emitting gas identified by ACORNS, referred to a “forest”. The forest consists of 70 trees,
which are position- and velocity-coherent clusters. ∼23% (16/70) of the trees have branches or leaves (i.e. substructure). The 8 most dominant trees (Section 5.2)
are plotted in colour. Substructure is indicated by short horizontal lines and the highest points of the leaves represent their peak intensities.



**5.2** **Results and statistics**


Figure 8 shows the hierarchical system (referred to as a “forest”)
identified by the ACORNS PPV clustering. In general, a dendrogram
"forest" consists of a number of "trees"; each tree may have substructure(s), which are referred to as “branches” if they have further
substructure(s), or “leaves” if they do not (see e.g Rosolowsky et al.
2008; Goodman et al. 2009). Trees with no substructure are also
categorised as leaves. Our ACORNS PPV clustering identifies a total

∼
of 70 trees, of which 16 ( 23%) have substructure, i.e. branches or
leaves. Eight of the identified trees together comprise ≳60% of the
data points used for the clustering analysis. These trees, shown in
colour in Figure 8, are designated Tree 0, Tree 17, Tree 1, Tree 4,


MNRAS **000**, 1–20 (2023)



Tree 9, Tree 7, Tree 30, Tree 57 (listed in order of decreasing number
of assigned data points). In this paper, we focus our analysis on Tree
0, the dominant feature of the hierarchical system. Tree 9 will also
be discussed in Section 6.3 as supporting evidence for the physical
scenario proposed in this work. Analysis of other trees and their
substructures will be presented in separate publications focusing on
different scientific topics.


Tree 0 contains ≈ 20% of the total velocity components, the most of
any tree, and the components with the highest peak intensity. Figure 9
shows maps of the spatial distribution of the peak intensities, centroid velocities, and velocity dispersions of the velocity components
in Tree 0. The maximum peak intensity in Tree 0 is 539.4 mJy beam [−][1]

and the median peak intensity is 122.7 mJy beam [−][1] . The centroid

_Filamentary mass accretion towards G11.92 MM2_ 11


**Figure 9.** Left: distribution of peak intensities of the velocity components of Tree 0. Middle: centroid velocity map of Tree 0. Right: velocity dispersion map of
Tree 0. ALMA 0.82 mm continuum contours (black, levels: 0.5mJy beam [−][1] × [5,15,40,160,280]) are overlaid in all panels.


velocities of the components in Tree 0 span a relatively narrow range
of 35.0 km s [−][1] to 38.8 km s [−][1], compared to the range of 27.6
km s [−][1] to 42.1 km s [−][1] for all fitted components (see Section 4.2).
The median velocity of Tree 0, which is 37.0 km s [−][1], falls within
the higher-velocity of the two main peaks seen in Figure 5. The median velocity dispersion of Tree 0 agrees with that of the full dataset
(∼0.4 km s [−][1] ), but Tree 0 lacks the high-dispersion tail seen in Figure 6, with a maximum velocity dispersion of 1.5 km s [−][1] . Spatially,
Tree 0 appears to trace the major features in the moment 8 map
(Fig. 2b), including the main north-southeast filamentary structure
and the extended emission that lies to the west of the southern end of

the main filament. The strongest emission in Tree 0 is located in the
filamentary structure to the southeast of MM2 (see Fig. 9). Notably,
the centroid velocity map of Tree 0 (shown in the middle panel of
Fig. 9) reveals a roughly north-south velocity gradient along the main
filamentary structure, which we consider further in Section 6.1. The
most notable feature of the velocity dispersion map (right panel of
Fig. 9) is an area of enhanced velocity dispersion (∼ 50-70%) around
MM2, within a radius of ∼3 [′′] .



Figure 10 shows the Probability Distribution Function (PDF) of
the centroid velocities of the components in Tree 0. As illustrated by
Figure 10, the velocity PDF is not well-represented by a Gaussian
model, with excesses at ∼36.3 km s [−][1] and ∼37.8 km s [−][1], and moderation in the tails. The kurtosis of the velocity PDF of Tree 0 is estimated to be 2.3; a value _<_ 3 (the kurtosis of the Gaussian distribution)
implies lighter tails, consistent with the features of the PDF. While
simulations of turbulence suggest Gaussian-like velocity PDFs (e.g.
Federrath 2013), observations do not always agree (e.g. Federrath
et al. 2016; Henshaw et al. 2019). In their study of the Galactic Centre molecular cloud G0.253+0.016, Federrath et al. (2016) interpret
double-peaked deviations from a Gaussian distribution as the result
of a large-scale velocity gradient, and note that observational noise,
the excitation of the molecular tracer, and smaller-scale systematic
motions may also contribute to deviations from a Gaussian model
(see also Henshaw et al. 2019). We suggest that the double-peak
feature in the Tree 0 velocity PDF may be caused by the large-scale
velocity gradient seen in Figure 9, similar to the case in Federrath
et al. (2016).



**Figure 10.** Probability Distribution Function (PDF) of the centroid velocities
of the components in Tree 0 (filled circles), overlaid with the best-fit Gaussian
model to the velocity PDF (dashed line).


**6** **FILAMENTARY ACCRETION FLOWS**


**6.1** **Velocity gradient**


As discussed in Section 5.2, the centroid velocity map of Tree 0
shows a ∼north-south velocity gradient, consistent with this tree’s
double-peaked velocity PDF. As shown in Figure 9 (middle panel),
this velocity gradient goes through MM2 and extends to MM1 to the
south and to the MM7/MM9/MM13/MM17 group of sources to the
north of MM2. To analyse the gas kinematics in the surroundings
of MM2, we select a position- and velocity-coherent substructure (a
“branch”) of Tree 0 that encompasses the immediate environment
of MM2, designated Branch 8. The centroid velocity map of this


MNRAS **000**, 1–20 (2023)

12 _S. Zhang et al._


km/s
36.0 36.5 37.0 37.5 38.0 38.5 39.0


-18:54:10.0


15.0


20.0



km/s
36.5 37.0 37.5 38.0 38.5 39.0




|Col1|Col2|
|---|---|
|Centroid Velocity of Branch 8<br>8mm continuum<br>3mm continuum|Centroid Velocity of Branch 8<br>8mm continuum<br>3mm continuum|







**Figure 11.** Left: centroid velocity map of Branch 8. Top right: map of best-fit velocity gradient; its direction is indicated by the black arrow. Bottom right: residual
map, generated by subtracting the best-fitting velocity gradient from the observations. In all panels, ALMA 0.8 mm continuum contours (black; contour levels:
0.5 × [5,15,40,160,280] mJy beam [−][1] ) and ALMA 1.3 mm continuum contours from Ilee et al. (2018) (green; contour levels: 0.06 × [10,50,150] mJy beam [−][1] )
are overlaid. The synthesised beams of the 0.8 mm and 1.3 mm data are shown in the left-hand panel, at bottom left and right, respectively.



branch is shown in Figure 11. On the plane of the sky, Branch 8
is ∼0.17 pc long and ∼0.05 pc wide. It hosts the brightest velocity
components of Tree 0 (with a peak intensity of 539.4 mJy beam [−][1] ),
and has a median intensity of 209.1 mJy beam [−][1], which is higher
than the median intensity of Tree 0 by a factor of ∼1.7. The centroid
velocities in Branch 8 range from 35.9 km s [−][1] to 38.6 km s [−][1] with
a median value of 37.3 km s [−][1], covering ∼71% of the velocity range
of Tree 0. Branch 8 also contains the broadest velocity components
of Tree 0, with a maximum velocity dispersion of 1.5 km s [−][1] and a
median of 0.5 km s [−][1] .

We measure the magnitude and direction of the velocity gradient
of Branch 8 using the methods proposed by Goodman et al. (1993).
A linear gradient of centroid velocities is described by the equation


_𝑣_ = _𝑣_ 0 + _𝑎_ Δ _𝛼_ + _𝑏_ Δ _𝛿,_ (1)


where Δ _𝛼_ and Δ _𝛿_ are the variations in right ascension and declination
in units of radians; _𝑎_ and _𝑏_ are the projections of the velocity gradient
per radian on the axes of right ascension and declination, respectively;
and _𝑣_ 0 is the systemic velocity. The magnitude of the velocity gradient
|∇ _𝑣_ | is given by



_𝑎_ [2] + _𝑏_ [2]

_,_ (2)
_𝐷_



FIT [7] . The uncertainties associated with the centroid velocities from

SCOUSEPY are included to constrain the fitting. We estimate the velocity gradient exhibited by Branch 8 to be 10.5±0.2 km s [−][1] pc [−][1] in
a direction of ∼18.9 [◦] (east of north) over a spatial scale of ∼0.17 pc.
The best-fitting model is shown in the top right panel of Figure 11,
with the black arrow indicating the direction of the fitted velocity gradient. The bottom right panel of Figure 11 shows the residual map,
calculated by subtracting the best-fitting model from the centroid
velocity map. The residuals range from −1.3 km s [−][1] to 1.2 km s [−][1] .
In other filamentary high-mass star-forming regions, the magnitudes of velocity gradients measured along (sub)filaments vary by
an order of magnitude, with a trend of larger velocity gradients at
smaller spatial scales: ∼0.2-0.9 km s [−][1] pc [−][1] at _>_ 1-8 pc scales (e.g.,
Bally et al. 1987, Peretto et al. 2014, Tackenberg et al. 2014, Zhang
et al. 2015, Hacar et al. 2017, Yuan et al. 2018, Chen et al. 2019,
Treviño-Morales et al. 2019, Hu et al. 2021, Beltrán et al. 2022),
∼0.7-0.8 km s [−][1] pc [−][1] at ∼1 pc scales (e.g., Henshaw et al. 2014,
Fernández-López et al. 2014), and ≳1-20 km s [−][1] pc [−][1] at ∼0.1-0.5 pc
scales (Henshaw et al. 2013, Liu et al. 2016, Williams et al. 2018,
Hacar et al. 2018, Li et al. 2022). This finding is reinforced by a
recent systematic study of the gas kinematics of a large sample of
filaments using ALMA H [13] CO [+] data, where the magnitude of the
velocity gradients increases from a few × ∼ 1 km s [−][1] pc [−][1] to a few
× ∼ 10 km s [−][1] pc [−][1] as the extent over which the velocity gradients
are measured decreases from ∼1 pc to ∼0.1 pc (Zhou et al. 2022).

Zhou et al. (2022) argue that the smaller velocity gradients at


7 LMFIT is a Python package designed for non-linear least-squares minimisation and curve-fitting based on scipy.optimize. The package is publicly
available via `[https://github.com/lmfit/lmfit-py](https://github.com/lmfit/lmfit-py)` .



|∇ _𝑣_ | =



√



where _𝐷_ is the distance to the source (3.37 kpc, Section 1). The
direction of increasing velocity (east of north) is



Θ = arctan( _[𝑎]_ (3)

_𝑏_ [)] _[.]_


We estimate the values of _𝑎_ and _𝑏_ by fitting a first-degree bivariate
polynomical to the centroid velocity map of Branch 8 using LM

MNRAS **000**, 1–20 (2023)

_Filamentary mass accretion towards G11.92 MM2_ 13



larger scales are likely caused by pressure-driven inertial inflows
shaped by either turbulence or gravity at large spatial scales, while the
larger velocity gradients at smaller scales are likely attributable to the
gravity of dense structures (e.g., cores and/or the hubs of hub-filament
systems). The latter scenario agrees well with our measurements for
Branch 8 (∼10.5 km s [−][1] pc [−][1] over ∼0.17 pc). For comparison,
we also estimate the velocity gradient of Tree 0 using the same
technique, which gives 9.3±0.1 km s [−][1] pc [−][1] in a direction of ∼34.7 [◦]

(east of north) over ∼0.47 pc. The magnitude of the velocity gradient
increases moderately (1.2 km s [−][1] pc [−][1], ∼13%) when the spatial
scale decreases by 0.3 pc (∼60%). We note that the variation in
observed velocity gradients along filaments may also be influenced
by projection effects: the observed magnitude of the velocity gradient
along a filament will be smaller if the orientation of the filament is
closer to the plane of sky.
Simulations and observations suggest that gravity is dynamically
more important at higher densities and smaller spatial scales (e.g.
Smilgys & Bonnell 2016; Chen et al. 2019). Williams et al. (2018)
find that _>_ 60% of the dense cores in the IRDC SDC13 are associated

with the peaks of velocity gradients traced by NH 3, which is interpreted as a signature of cores accreting material from their parental
filaments. We note that the southeast end of Branch 8 reaches the

160 _𝜎_ 0.8 mm continuum contour around the proto-O star MM1,
roughly ∼1700 AU from the centre of MM1. The gravity of MM1
(with an enclosed mass of ∼40 M ⊙, Ilee et al. 2018) is expected
to dominate over pressure support in its local (≲0.1-0.6 pc) environment (Williams et al. 2018, Chen et al. 2019). As a test of
minimising the effects of MM1, we measured the velocity gradient
adopting the southern end of the 15 _𝜎_ contour extending from MM2
to MM1 as a boundary, and obtain a value of 8.4±0.2 km s [−][1] pc [−][1] in
the direction of ∼14 [◦] (east of north). This suggests that introducing
an artificial boundary has a limited (∼20%) effect on the velocity gradient measurement. The Global Hierarchical Collapse model
(Vázquez-Semadeni et al. 2017, 2019) also suggests that global collapse driven by the large-scale gravitational potential well and local
collapse driven by small-scale overdensities take place concurrently.
In this scenario, the observed velocity gradient of Branch 8 would
most likely be caused by a combination of large-scale gas flows towards the centre of the massive cluster and small-scale gas flows
towards both MM1 and MM2 (as seen in Peretto et al. 2014). In this
context, it would be difficult to define a physically meaningful boundary within a continuity of gas flows. We thus adopt the measurement
using the full extent of Branch 8 in our analysis.


**6.2** **Mass inflow rate**


Velocity gradients along filaments are commonly interpreted as signatures of longitudinal gas flows (e.g., Kirk et al. 2013, Peretto et al.
2014, Liu et al. 2016, Lu et al. 2018, Yuan et al. 2018, Chen et al.
2019, Treviño-Morales et al. 2019, Chen et al. 2020b, Hu et al. 2021).
If the filamentary structure observed in G11.92−0.61 is oriented such
that its southeast end is further from the observer than its northwest

end, the observed velocity gradient in Branch 8 is consistent with
accelerating accretion flows towards MM2 [8] .


8 Henshaw et al. (2014) interpret the symmetrical velocity gradients (with
a mean magnitude of ∼2.5 km s [−][1] pc [−][1] ) towards the SW core in IRDC
G035.39-00.33 as either accretion flows along filaments towards the SW
core, or an expanding shell of dense gas driven by protostellar outflows and/or
stellar winds. The expanding shell scenario is supported by the detection of
8 and 24 _𝜇_ m emission (indicative of the presence of young stars) and a



Based on the hypothesis of filamentary accretion flows, we can
derive the mass inflow rate using the velocity gradient and mass of
Branch 8 following the procedure in Kirk et al. (2013). We estimate
the gas mass of Branch 8 from its 0.82 mm integrated flux density,
which is measured by integrating the intensity within the boundary of
Branch 8 using the CASA task `imstat`, under the simple assumptions
of optically thin, isothermal dust emission as (see e.g Cyganowski
et al. 2011a, 2017):

_𝑀_ gas (M ⊙ ) = [4] _[.]_ [79][ ×][ 10] _𝐵_ [−] ( [14] _𝜈,𝑇_ _[𝑅𝑆]_ dust _[𝜈]_ [(] ) [J] _𝜅_ [y] _𝜈_ [)] _[𝐷]_ [2] [(][k][p][c][)] _,_ (4)


where _𝑅_ is the gas-to-dust mass ratio (assumed to be 100), _𝑆_ _𝜈_ is the
integrated flux density, and _𝐷_ is the distance to G11.92−0.61. We
adopt _𝜅_ 0 _._ 82 mm = 2 _._ 3 cm [2] g [−][1], based on linear interpolation of the
Ossenkopf & Henning (1994) values for MRN grains with thick ice
mantles and _𝑛_ H 2 = 10 [6] cm [−][3] (column 7 of their Table 1), and a dust
temperature range _𝑇_ dust =15–25 K. Our adopted dust temperature
range is informed by clump-scale NH 3 temperature measurements
for G11.92−0.61 (T kin ∼26 K from single-component fitting and
T kin ∼14 K and 54 K from two-component fitting, where the 54 Kcomponent is attributable to the immediate environment of MM1;
Cyganowski et al. 2013) and by temperature maps derived from VLA
NH 3 observations of other EGOs (e.g. Brogan et al. 2011, their Figure
3). With our adopted parameters, we estimate the mass of Branch 8
as ∼30-65 M ⊙ . For a simple cylindrical model with a length of _𝐿_, a
mass of _𝑀_, a velocity gradient observed along the main axis of the
filament of ∇ _𝑣_, and an inclination angle to the plane of sky of _𝛼_, the
rate of mass flow _𝑀_ [�] is given by (Kirk et al. 2013):


�
_𝑀_ = [|][∇] _[𝑣]_ [|] _[𝑀]_ (5)
tan( _𝛼_ ) _[,]_


where |∇ _𝑣_ | is the magnitude of the velocity gradient. Based on our
estimates of the branch mass and velocity gradient (above and Section 6.1) and considering a range of plausible inclination angles, we
derive mass accretion rates of 1 _._ 8 × 10 [−][4] M ⊙ yr [−][1] (for _𝑇_ dust =25 K
and an inclination angle _𝛼_ =60 [◦] ) to 1 _._ 2 × 10 [−][3] M ⊙ yr [−][1] ( _𝑇_ dust =15 K
and _𝛼_ =30 [◦] ).
We note that in addition to the uncertainties in inclination angle
and dust temperature reflected in the range quoted above, our estimates of _𝑀_ [�] are also affected by other sources of uncertainty in our
mass estimates. We estimate a factor of ∼2 systematic uncertainty,
encompassing the uncertainties in the adopted _𝜅_ and gas-to-dust mass
ratio and the uncertainty associated with the isothermal assumption
(see also e.g. Brogan et al. 2009; Beuther et al. 2021). While assuming optically thin dust emission can lead to underestimating masses
on core scales (e.g. Cyganowski et al. 2014; Brogan et al. 2016), the
optically thin assumption is likely to be valid over the vast majority
of the area of Branch 8, which has a mean brightness temperature [9]

of only 0.35 K (see also e.g. Beuther et al. 2018). We also note
that we have not attempted to impose a boundary between 0.82 mm


high-velocity redshifted wing traced by CO (1-0) (indicative of protostellar
outflows) towards the SW core. As introduced in Section 1, G11.92-0.61
MM2 hosts an early-stage high-mass protobinary system that drives a lowvelocity bipolar outflow. Compared with the SW core, MM2 is on an earlier
evolutionary stage; its protostellar feedback is thus less likely to drive an
expanding shell of dense gas with a velocity gradient of ∼10.5 km s [−][1] pc [−][1],
which is higher than that reported by Henshaw et al. (2014) by a factor of
∼4. In addition, the observed ∼south-north velocity gradient in Branch 8 is
unlikely to be caused by the ∼west-east bipolar outflow associated with MM2
(see Figure 7).
9 Measured from the brightness temperature map computed using the beamsize and the `tt.brightnessImage` function of `toddTools` .


MNRAS **000**, 1–20 (2023)

14 _S. Zhang et al._


continuum emission associated with the filament and with the MM2

core. The integrated flux density reported for MM2 in Section 3.1 is
a fit to the total emission at the core position, so includes a contribution from the background filament, and our measurement of the
integrated flux density of Branch 8 includes the area of the compact

core.

Reported mass accretion rates along filaments vary by two orders
of magnitude, from ∼ 10 [−][5] M ⊙ yr [−][1] (e.g., Kirk et al. 2013, Peretto
et al. 2014, Henshaw et al. 2014, Treviño-Morales et al. 2019, Li
et al. 2022) to ∼ 10 [−][4] M ⊙ yr [−][1] (e.g., Chen et al. 2019, Lu et al.
2018, Yuan et al. 2018) to ∼ 10 [−][3] M ⊙ yr [−][1] (e.g., Liu et al. 2016,
Hu et al. 2021). This range is likely attributable to the different total
masses of these star-forming regions (e.g., low-mass or high-mass)
combined with variations in velocity gradient measurements (e.g.,
tracer, spatial scale), mass calculations (e.g., based on molecular
line or dust emission, clump mass or filament mass), and inclinationangle assumptions. Our estimated _𝑀_ � of 1 _._ 8 × 10 [−][4] M ⊙ yr [−][1] to
1 _._ 2×10 [−][3] M ⊙ yr [−][1] is higher than the values reported in early studies
of filamentary accretion flows in high-mass IRDCs (∼(2.5-7)×10 [−][5]

M ⊙ yr [−][1], e.g. Henshaw et al. 2014; Peretto et al. 2014). The typical
accretion rates of (0.5-3.5) ×10 [−][4] M ⊙ yr [−][1] found by Lu et al. (2018)
in their study of NH 3 filaments in high-mass star-forming clouds also
fall at the low end of our estimated range. We note that our estimated
velocity gradient is also higher (∼ 10.5 km s [−][1] pc [−][1] compared to ∼
1 - 2.5 km s [−][1] pc [−][1] for the clouds studied by Henshaw et al. 2014;
Peretto et al. 2014; Lu et al. 2018), which would naturally lead to
higher estimated accretion rates for filaments of roughly comparable
mass (equation 5). Liu et al. (2016) report a similarly large velocity
gradient (∼10 km s [−][1] pc [−][1] ) in filaments identified in NH 3 (1,1) in the
high-mass cluster-forming region AFGL 5142. Adopting the clump
mass as a lower limit to the total mass of filaments, Liu et al. (2016)
derive a filamentary mass accretion rate of ∼ 2 _._ 1 × 10 [−][3] M ⊙ yr [−][1],
within a factor of 2 of the high end of our estimates for G11.92−0.61
MM2.


**6.3** **Multiple filamentary accretion flows**


In addition to Tree 0, Tree 9 also displays a velocity gradient along
the main filamentary structure in a ∼north-south direction. Figure 12
shows maps of the spatial distribution of the peak intensities, centroid
velocities, and velocity dispersions of the velocity components in
Tree 9 (as shown for Tree 0 in Figure 9). The maximum peak intensity
in Tree 9 is 252.1 mJy beam [−][1] and the median is 75.0 mJy beam [−][1] .
The centroid velocities of the components in Tree 9 fall within the
lower-velocity of the two main peaks in Figure 5, ranging from 32.7
km s [−][1] to 35.2 km s [−][1] with a median of 34.0 km s [−][1] (in contrast to
Tree 0, see Section 5.2). The maximum velocity dispersion in Tree
9 is 1.4 km s [−][1] and the median is 0.5 km s [−][1] . Though the brightest
components of Tree 0 are about a factor of two stronger than those
of Tree 9, the maximum and median velocity dispersions of the two
trees are similar. Notably, the distinct centroid velocity ranges of the
two trees (32.7 km s [−][1] to 35.2 km s [−][1] for Tree 9 and 35.0 km s [−][1] to
38.8 km s [−][1] for Tree 0) suggest that they are kinematically separate
structures. We measure the velocity gradient of Tree 9 following the
procedure described in Section 6.1, and obtain a velocity gradient
with a magnitude of ∼9.0 km s [−][1] pc [−][1] and a direction of ∼149 [◦]

(east of north). If the structure traced by Tree 9 is oriented such
that its northern end is further from the observer than its southern

end, the observed velocity gradient is consistent with a stream of gas
flowing towards MM2. The distinct ranges of centroid velocities and
the comparable velocity dispersions of Tree 0 and Tree 9 suggest
a scenario in which MM2 is fed by multiple filamentary gas flows


MNRAS **000**, 1–20 (2023)



that partially overlap along the line of sight. This implies that the
filamentary structure seen in the 0.82 mm dust continuum contains
multiple kinematic substructures.
Velocity-coherent substructures within filaments (often known
as "fibres") have been identified in other high-mass star-forming
regions, including Orion (where Hacar et al. 2018 identified 55
position- and velocity-coherent fibres within the integral-shaped filament (ISF) using N 2 H [+] (1-0)), NGC 6334 (Shimajiri et al. 2019b, Li
et al. 2022) and the DR21 ridge in Cygnus X (Cao et al. 2022). Hydrodynamic simulations with turbulence can reproduce filament substructures similar to those seen in observations, and demonstrate that
they play a crucial role in channelling mass onto star-forming cores
embedded within filaments (e.g., Smith et al. 2014, Smith et al. 2016,
Clarke et al. 2020). However, simulation-based studies of the correspondence between fibres identified in Position-Position-Velocity
space and coherent substructures in Position-Position-Position space
have also emphasised the need for caution in interpreting observed
filament substructures due to line-of-sight confusion and projection
effects (e.g., Zamora-Avilés et al. 2017 and Clarke et al. 2018, with
the latter analysing synthetic C [18] O observations).


**7** **DISCUSSION**


**7.1** **Mass inflow feeding the protobinary**


Our analysis of the gas kinematics in the surroundings of MM2
reveals position- and velocity-coherent substructures in the N 2 H [+] emitting gas that we interpret as tracing filamentary accretion flows
onto MM2 (Section 6). As MM2 is now known to host a young protobinary system undergoing ongoing accretion (Section 1, see also
Cyganowski et al. 2022), we can use our estimates of the filamentary
mass inflow rate to consider the timescales for filament-fed growth
of the embedded protostars. Cyganowski et al. (2022) estimate the
current protostellar masses of the binary members to be ∼1M ⊙ each.
If the overall efficiency factor for transporting the gas carried by
the filamentary inflows onto the protostars is 50%, the members of
the protobinary will double their masses in ∼3.3×10 [3] to ∼2.2×10 [4]

yr (where the range corresponds to the range in our estimated filamentary accretion rate: 1 _._ 8 × 10 [−][4] M ⊙ yr [−][1] to 1 _._ 2 × 10 [−][3] M ⊙
yr [−][1], Section 6.2), comparable to the dynamical timescale of the
CH 3 OH outflow ( _𝑡_ dyn ∼4600 yr and 12,100 yr for the blue and red
lobes, respectively; Cyganowski et al. 2022). Similarly, the time for
each member of the protobinary to reach a mass of 8 M ⊙ would
be ∼2.3×10 [4] to ∼1.6×10 [5] yrs, and the time for each member of
the protobinary to reach 10 M ⊙ would be ∼3.0×10 [4] to ∼2.0×10 [5]

yrs. Interestingly, using chemical clocks, Sabatini et al. (2021) derive timescales of ∼ 5 × 10 [4] yr for the 70 _𝜇_ m-weak phase and of
∼ 1 _._ 2×10 [5] yr for the subsequent MIR-weak phase in the evolutionary
stages of the ATLASGAL-TOP100 sample of massive star-forming
clumps (König et al. 2017). While the uncertainties are considerable,
we note that the combined timescale of the 70 _𝜇_ m-weak and MIRweak phases (∼ 1.7×10 [5] yr) is comparable to our upper estimates of
the timescale for the binary members to become massive protostars
(M≳8M ⊙ ).
We note that the timescale estimates above consider mass aggregation processes involving multiple spatial scales: a) from filaments
to cores and b) from cores to stars. The efficiencies of both processes are poorly constrained. Analysis of the relationship between
the prestellar core population and the column density shows that only
a small fraction of dense gas is contained in prestellar cores, for example, ∼15% in the Aquila Cloud Complex (André et al. 2014) and

_Filamentary mass accretion towards G11.92 MM2_ 15


**Figure 12.** Left: distribution of peak intensities of the velocity components of Tree 9. Middle: centroid velocity map of Tree 9. Right: velocity dispersion map
of Tree 9. ALMA 0.82 mm continuum contours (black, levels: 0.5mJy beam [−][1] × [5,15,40,160,280]) are overlaid in all panels.



∼
22% in Orion B (Könyves et al. 2020). In the Global Hierarchical
Collapse (GHC) scenario, filaments themselves are assembling mass
from their surroundings while they transport material onto embedded star-forming cores (Vázquez-Semadeni et al. 2017, 2019). The
efficiency of the mass transport from filaments to cores will depend
on the dynamical timescales of the two structures.


**7.2** **Velocity gradient across filament**


The direction of the best-fitting velocity gradient for the centroid
velocity map of Branch 8 is ∼19 [◦] east of north, offset by ∼40 [◦] from
the main axis of Branch 8 (see top right panel of Fig. 11). This offset
suggests that the observed velocity gradient consists of a component
that is aligned parallel to the main axis of Branch 8 (∼southeast
∼
northwest) and a perpendicular component ( southwest-northeast).
As discussed above, the parallel component is most likely associated
with longitudinal filamentary accretion flows towards MM2. Velocity
gradients that are perpendicular to the main axes of filamentary structures have been observed in (sub)filaments in nearby (Palmeirim et al.
2013, Kirk et al. 2013, Fernández-López et al. 2014, Dhabal et al.
2018, Dhabal et al. 2019, Chen et al. 2020a, Chen et al. 2020b) and
high-mass (Schneider et al. 2010, Beuther et al. 2015, Williams et al.
2018, Zhou et al. 2021) star-forming regions. These perpendicular
velocity gradients have been interpreted as signatures of asymmetric mass accretion flows onto (sub)filaments (Palmeirim et al. 2013,
Chen et al. 2020b), which can be induced by the compression of
shocked gas (Shimajiri et al. 2019a, Dhabal et al. 2018, Chen et al.
2020a), as direct results of compression flows (Schneider et al. 2010,
Williams et al. 2018, Dhabal et al. 2019, Zhou et al. 2021), and as
the combined result of mergers/collisions of velocity-coherent subfilaments and the accretion and rotation of filaments (Beuther et al.
2015).
As G11.92-0.61 is a young embedded massive protocluster where
UCHII and H ii regions have not yet developed (Ilee et al. 2016) and
is located ∼1 pc away from the ultra-compact HII region G11.9400.62 (Churchwell et al. 1992), the kinematics of dense filamentary
structures in G11.92-0.61 will not yet be shaped by the feedback
from either internal or external expanding H ii regions. Branch 8 has
a mass of ∼30-65 M ⊙ and a length of ∼0.17pc, yielding a mass per



unit length of _𝑀_ line ≈174-380 M ⊙ pc [−][1] . These values are higher than
the thermal critical values _𝑀_ line _,_ crit calculated with Equation (11) of
Kirk et al. (2013) for T∼15-25 K by a factor of ∼4-15, suggesting
that thermal pressure is insufficient to support Branch 8 against gravitational collapse. Branch 8 thus is likely to undergo radial collapse,
which, if asymmetric, can also contribute to the observed perpendicular velocity gradient. We speculate that the perpendicular velocity
gradient could be the combined result of the radial collapse, mass accretion and rotation of the filamentary structure, while accretion may
dominate over rotation as it evolves (e.g., Kirk et al. 2013). This is a
picture consistent with the GHC scenario (Vázquez-Semadeni et al.
2017, 2019), where the mass aggregation processes of filaments and
of the cores within them take place concurrently. In this scenario, gas
is accreted onto filaments and then continuously flows along them,
as posited by Chen et al. (2020b) based on their NH 3 observations
of NGC 1333.


**7.3** **Limitations and Future Work**


We note that the line profiles in the N 2 H [+] (4-3) data cube are shaped
by three main factors: multiple velocity components, hyperfine structure (hfs), and missing short spacing information. In addition, selfabsorption might also affect the line profiles in the densest region.
In this work, we have used Gaussian Decomposition to disentangle
the multiple velocity components and study the gas kinematics. Of
the remaining factors, we can quantitatively investigate the effects of
hfs and self-absorption using our existing data, while missing short
spacings are an area for future work, as discussed below.
As noted in Section 3.2.2, the hfs of the N 2 H [+] (4-3) transition can
contribute to shaping the line profile (see also Pagani et al. 2009) and
Friesen et al. (2010) found that Gaussian fitting overestimated the intrinsic N 2 H [+] line width by ∼10%-25%. To quantify this effect in our
data, we carry out multi-component hfs fitting for a selection of 10
spectra using pyspeckit (Ginsburg & Mirocha 2011, Ginsburg et al.
2022). The spectra were selected to span a range in the number of
fitted Gaussian components (from 1 to 5); their locations are marked
in the right-hand panel of Figure 4. The pyspeckit package applies
a uniform excitation temperature (T _𝑒𝑥_ ) to all fitted hyperfine lines.
A one-component hfs fit thus has four free parameters: the centroid


MNRAS **000**, 1–20 (2023)

16 _S. Zhang et al._


**Figure 13.** Examples of one-component (left) and two-component (right) N 2 H [+] (4-3) hyperfine structure fits (red) overlaid on the observed spectra (black). The
individual hyperfine components are shown in blue. The best-fit parameters are listed at top right in each panel.



velocity, the velocity dispersion, T _𝑒𝑥_, and the optical depth _𝜏_ . An
example of a one-component hfs fit is shown in Figure 13. Since
the number of fitted parameters in a multi-component hfs fit is 4×
the number of velocity components, we use the best-fitting Gaussian
models as initial guesses for the centroid velocity and the velocity
dispersion to better constrain the hfs fitting. This approach achieves
good fits for spectra with one or two velocity components identified
by Gaussian decomposition, but T _𝑒𝑥_ and _𝜏_ are poorly constrained for
many components in more complex spectra. To obtain reasonable fits
for these more complex cases, we fix T _𝑒𝑥_ for poorly constrained components to the mean value from the initial good fits (14 K). Figure 14
presents a comparison of the results of our Gaussian Decomposition
and hyperfine structure fitting for the selected spectra. In this limited
sample, we find that in our data Gaussian Decomposition can overestimate the line width by 37% on average, while the fitted centroid
velocities are consistent to within 0.1%.

The hfs fits can also be used to investigate the optical depth of
the N 2 H [+] emission, and so the potential effects of self-absorption.
Inspecting the aforementioned initial good hfs fits, we see no indications of self-absorption in the line profiles for components with
moderate optical depths _>_ 1 (e.g., the components with _𝜏_ ∼2-4 in
Figure 13). As the multi-component hfs fits are in general poorly
constrained, we use the radiative transfer code RADEX (van der
Tak et al. 2007) to estimate the optical depth for all velocity components fit in our SCOUSEPY analysis. We use the molecular data
and collisional rate coefficients for N 2 H [+] from the Leiden Atomic
and Molecular Database (LAMDA, Schöier et al. 2005); the collisional rate coefficients are for N 2 H [+] (including hfs) in collisions
with H 2 for a temperature range of 5 - 2000 K, and are extrapolated and scaled from those for N 2 H [+] in collisions with He (Daniel
et al. 2005). The other required inputs to RADEX are the H 2 density
_𝑛_ H 2, the gas kinetic temperature T _𝑘𝑖𝑛_, the line width (FWHM), the
molecular column density _𝑁_ (N 2 H [+] ), and the background temperature T _𝑏𝑔_ . The mean gas density of Branch 8 is estimated to be _𝑛_ H 2
∼(1−3)×10 [6] cm [−][3] assuming a cylinder with a height of ∼0.17 pc, a
diameter of ∼0.05 pc, and a mass of ∼30-65 M ⊙ (see Section 6). The
N 2 H [+] column density is estimated following equation A4 in Caselli
et al. (2002), using the integrated intensity of each fitted velocity
component and T _𝑒𝑥_ = 14 K (see the previous paragraph). The par

MNRAS **000**, 1–20 (2023)



tition function for T _𝑒𝑥_ = 14 K is interpolated using values from the
Cologne Database for Molecular Spectroscopy (CDMS, Müller et al.
2001, 2005). We estimate the optical depth for each fitted velocity
component using the N 2 H [+] column density estimated as described
above, the fitted velocity dispersion converted to FWHM line width,
_𝑛_ H 2 =10 [6] cm [−][3], T _𝑏𝑔_ =2.73 K, and T _𝑘𝑖𝑛_ =15 − 25 K (see Section 6.2)
using the Python package SpectralRadex [10] (Holdship et al. 2021).
From this analysis, we find that the optical depth of the hyperfine line
( _JF_ 1 _F_ ) = (456 − 345), the strongest hyperfine line with the largest
optical depth, ranges from 0.02 to 1.5 for T _𝑘𝑖𝑛_ =15 K and from 0.03
to 2.2 for T _𝑘𝑖𝑛_ =25 K. The total optical depth of the N 2 H [+] (4-3)
transition ranges from 0.1 to 7.2 for T _𝑘𝑖𝑛_ =15 K, with ∼99% of fitted
components having _𝜏<_ 4, and from 0.2 to 11 for for T _𝑘𝑖𝑛_ =25 K, with
∼93% of fitted components having _𝜏<_ 4. We emphasise that the optical depths estimated from our RADEX modelling are sensitive to the
assumed T _𝑘𝑖𝑛_ and _𝑛_ H 2 and to the column density, which depends on
the assumed T _𝑒𝑥_ (for example, for the single-component spectrum
shown in the left-hand panel of Fig. 13, our RADEX modelling yields
a total optical depth of 3.0 for T _𝑘𝑖𝑛_ =15 K and 4.8 for T _𝑘𝑖𝑛_ =25 K,
compared to 2.4 from the hfs fit) and that T _𝑒𝑥_, T _𝑘𝑖𝑛_, and _𝑛_ H 2 are
physically expected to vary spatially, which we cannot constrain with
our ALMA data. Notably, the number of fitted velocity components
does not track the strength of the N 2 H [+] emission (compare Fig. 2b
and 4), e.g. the number of fitted components is higher to the north
of MM2, while the N 2 H [+] (4-3) emission is strongest to the south.
Combined with the generally moderate optical depths, this suggests
that self-absorption is not a major contributor to the observed line
profiles.
The effects of missing short-spacing information cannot be quantified with existing data (since no short-spacing N 2 H [+] (4-3) observations are available) and this is a limitation of the present study. Hacar
et al. [11] have shown that missing short- and zero-spacings can affect


10 `https://spectralradex.readthedocs.io`
11 Hacar, A., The need for data combination in the ALMA era, EAS2020
- SS13a: Eight years of ALMA ground-breaking results: A joint venture
between the ALMA user community and the ALMA Regional Centres, June
29 - July 3, 2020.

_Filamentary mass accretion towards G11.92 MM2_ 17


(i) MM2, which appears as a strong, compact source of 0.82 mm
continuum emission, lies on a ∼north-south filamentary structure
within the G11.92−0.61 massive protocluster. The filament is traced
by both 0.82 mm continuum and N 2 H [+] (4-3) emission, but there are
differences in the morphologies of the two tracers, with the peaks
of the integrated N 2 H [+] emission offset by 0 [′′] _._ 9 and 1 [′′] _._ 2 (∼3000 and
4000 AU) from the 0.82 mm continuum peak.


(ii) H 2 D [+] is undetected towards MM2, to 4 _𝜎_ limits of 10.8
mJy beam [−][1] / 0.23 K. The non-detection of H 2 D [+] is likely due to
internal heating from the recently-discovered protobinary system.


(iii) The N 2 H [+] spectra are complex, with multiple emission peaks
and, towards the MM2 core, absorption features. The complexity and
spatial variation of the N 2 H [+] spectra indicate that multiple velocity
components are present along the line of sight.



**Figure** **14.** Comparison of fitted parameters from Gaussian Decomposition
(black circles) and hyperfine structure fitting (red squares) for selected spectra
(see Section 7.3).


the line profiles and relative intensities of the hyperfine components
for N 2 H [+] (1-0), and that the effects are highly non-linear. However,
these effects have not been investigated for N 2 H [+] (4-3), and the impacts may be lessened by the much higher E upper and critical density
of the (4-3) transition: E upper =44.7 K and n crit =2.8×10 [6] cm [−][3] at 20 K
for N 2 H [+] (4-3) compared to E upper =4.5 K and n crit =4.1×10 [4] cm [−][3]

at 20 K for N 2 H [+] (1-0).
The most straightforward way to address the lack of short spacing data in this study, and a possible area for future work, would
be additional observations of N 2 H [+] (4-3) towards G11.92−0.61, e.g.
Atacama Compact Array (ACA) and Total Power (TP) observations.
N 2 H [+] (4-3) observations are, however, challenging and observationally expensive, as the poor atmospheric transmission at the line frequency means that observations require excellent weather and/or very
large amounts of observing time. The N 2 H [+] (4-3) observations presented here total 4.52 hrs of on-source ALMA 12-m time, for a single
pointing (Table 1), and ACA 7-m observations suitable for combining
with the existing data would require _>_ 20 hours on-source [12] . Alternately, high-spatial-dynamic-range observations of the G11.92−0.61
region in other lines known to trace filamentary accretion flows (e.g.
lower-J transitions of N 2 H [+] or lines of NH 3 or H [13] CO; Hacar et al.
2018; Chen et al. 2020b; Cao et al. 2022) may offer a more practical
path to confirming our results with additional observations and further investigating kinematics and multi-scale mass accretion in the
G11.92−0.61 region.


**8** **CONCLUSIONS**


We have observed the former high-mass prestellar core candidate
G11.92-0.61 MM2, which has recently been revealed to host a protobinary system driving a low-velocity CH 3 OH outflow. Our deep,

∼
sub-arcsecond ( 2000 AU) resolution ALMA observations targeted
the dense and depleted gas tracers H 2 D [+] (1 1 _,_ 0-1 1 _,_ 1) and N 2 H [+] (4-3).
Our main findings are summarised below.


12 Based on the time multipliers in the ALMA Cycle 10 Proposer’s Guide,
`[https://almascience.eso.org/proposing/proposers-guide](https://almascience.eso.org/proposing/proposers-guide)` .



(iv) Our analysis of the N 2 H [+] gas kinematics, using pixel-by-pixel
Gaussian decomposition with SCOUSEPY and hierarchical clustering of the extracted velocity components with ACORNS, reveals
a hierarchical system in the N 2 H [+] -emitting gas comprised of 70
velocity- and position-coherent clusters, known as "trees". The eight
largest trees describe _>_ 60% of the fitted velocity components, with

∼
20% of fitted velocity components in the largest (primary) tree.


(v) The primary tree exhibits a ∼north-south velocity gradient
along the filamentary structure traced by the 0.82 mm continuum
emission. Analysing a ∼0.17 pc-long substructure within this tree
to focus on gas kinematics around MM2, we find a best-fit velocity
gradient of ∼10.5 km s [−][1] pc [−][1] . Interpreting this velocity gradient
as tracing filamentary accretion flows towards MM2, we estimate a
mass inflow rate of ∼1.8×10 [−][4] to ∼ 1.2 ×10 [−][3] M ⊙ yr [−][1] .


Our analysis of the dense gas kinematics in the surroundings of
MM2 indicates that rather than being an isolated core, MM2 is connected to its larger-scale environment. In particular, the ongoing
accretion onto the protobinary system – indicated by its outflow activity – is likely fed by the larger-scale filamentary accretion flows. If
50% of the mass inflow estimated above reaches the protostars, each
will reach a mass of 8 M ⊙ within ∼1.6×10 [5] yrs, which is intriguingly
comparable to the combined timescale of the 70 _𝜇_ m-weak+MIR-weak
phases of high-mass star formation estimated from chemical clocks
(e.g. Sabatini et al. 2021). In addition to the primary tree that is the
focus of our analysis, we also identify a velocity gradient consistent
with a filamentary accretion flow onto MM2 in a second tree, which
is kinematically distinct but partially overlaps the primary tree on
the plane of the sky. This finding suggests that the filamentary dust
continuum structure contains multiple kinematic substructures, and
that MM2 may be fed by multiple filamentary accretion flows. Additional observations of the G11.92−0.61 region, including in lower-J
and more easily observed N 2 H [+] transitions, are needed to explore
this possibility and expand the investigation of mass accretion in
G11.92−0.61 to larger spatial scales.


**ACKNOWLEDGEMENTS**


We thank J. D. Ilee for helpful discussions and for providing the ALMA 1.3 mm continuum image from Ilee et al.
(2018). We also thank K. Öberg, T. P. Robitaille, and C. M.
Koepferl for their input at an early stage of this project. The
National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement
by Associated Universities, Inc. This work made use of the
following ALMA data: ADS/JAO.ALMA#2015.1.00827.S, and
ADS/JAO.ALMA#2017.1.01373.S. ALMA is a partnership of ESO


MNRAS **000**, 1–20 (2023)

18 _S. Zhang et al._


(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile. The
Joint ALMA Observatory is operated by ESO, AUI/ NRAO and
NAOJ. S.Z. is funded by the China Scholarship Council-University
of St Andrews Scholarship (PhD programmes, No. 201806190010).
C.J.C. acknowledges support from the University of St Andrews
Restarting Research Funding Scheme (SARRF), which is funded
through the SFC grant reference SFC/AN/08/020. J.D.H gratefully
acknowledges financial support from the Royal Society (University Research Fellowship; URF\R1\221620). This work made use
of NASA Astrophysics Data System Bibliographic Services and
Python packages NumPy (an array programming library, Harris et al.
(2020)), SciPy (an open-source scientific computing library, Virtanen et al. (2020)), Astropy (an open-source package with commonlyneeded functionality to the astronomical community, Astropy Collaboration et al. (2022)), Matplotlib (a 2D graphics package, Hunter
(2007)), APLpy (an open-source plotting package for Python, Robitaille & Bressert (2012)) and analysisUtils (Hunter et al. 2023).


**DATA AVAILABILITY**


The ALMA 0.82 mm continuum image and N 2 H [+] (4-3) and
H 2 D [+] (1 1 _,_ 0 -1 1 _,_ 1 ) line cubes are available at `[https://doi.org/10.](https://doi.org/10.5281/zenodo.12640479)`
`[5281/zenodo.12640479](https://doi.org/10.5281/zenodo.12640479)` .


**REFERENCES**


[Anderson M., et al., 2021, MNRAS, 508, 2964](http://dx.doi.org/10.1093/mnras/stab2674)
André P., Di Francesco J., Ward-Thompson D., Inutsuka S. I., Pudritz R. E.,
Pineda J. E., 2014, in Beuther H., Klessen R. S., Dullemond C. P., Henning T., eds, Protostars and Planets VI. pp 27–51 ( `[arXiv:1312.6232](http://arxiv.org/abs/1312.6232)` ),
[doi:10.2458/azu_uapress_9780816531240-ch002](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch002)
[André P., et al., 2016, A&A, 592, A54](http://dx.doi.org/10.1051/0004-6361/201628378)
[Astropy Collaboration et al., 2022, ApJ, 935, 167](http://dx.doi.org/10.3847/1538-4357/ac7c74)
[Bally J., Langer W. D., Stark A. A., Wilson R. W., 1987, ApJ, 312, L45](http://dx.doi.org/10.1086/184817)
[Barnes A. T., et al., 2023, A&A, 675, A53](http://dx.doi.org/10.1051/0004-6361/202245668)

Beltrán M. T., Rivilla V. M., Kumar M. S. N., Cesaroni R., Galli D., 2022,


[A&A, 660, L4](http://dx.doi.org/10.1051/0004-6361/202243361)
Beuther H., Ragan S. E., Johnston K., Henning T., Hacar A., Kainulainen
[J. T., 2015, A&A, 584, A67](http://dx.doi.org/10.1051/0004-6361/201527108)

[Beuther H., et al., 2018, A&A, 617, A100](http://dx.doi.org/10.1051/0004-6361/201833021)

[Beuther H., et al., 2021, A&A, 649, A113](http://dx.doi.org/10.1051/0004-6361/202040106)
Blake G. A., Sandell G., van Dishoeck E. F., Groesbeck T. D., Mundy L. G.,
[Aspin C., 1995, ApJ, 441, 689](http://dx.doi.org/10.1086/175392)
[Bonnell I. A., Bate M. R., 2006, MNRAS, 370, 488](http://dx.doi.org/10.1111/j.1365-2966.2006.10495.x)
Bonnell I. A., Bate M. R., Clarke C. J., Pringle J. E., 2001, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2001.04270.x) [323,](https://ui.adsabs.harvard.edu/abs/2001MNRAS.323..785B)
[785](https://ui.adsabs.harvard.edu/abs/2001MNRAS.323..785B)

Bonnell I. A., Bate M. R., Vine S. G., 2003, Mon. Not. [Roy.](http://dx.doi.org/10.1046/j.1365-8711.2003.06687.x) Astron. Soc.,
343, 413
Bonnell I. A., Vine S. G., Bate M. R., 2004, Mon. Not. [Roy.](http://dx.doi.org/10.1111/j.1365-2966.2004.07543.x) Astron. Soc.,
349, 735

[Bonnell I. A., Clark P., Bate M. R., 2008, MNRAS, 389, 1556](http://dx.doi.org/10.1111/j.1365-2966.2008.13679.x)

[Bonnell I. A., Dobbs C. L., Smith R. J., 2013, MNRAS, 430, 1790](http://dx.doi.org/10.1093/mnras/stt004)
[Bontemps S., Motte F., Csengeri T., Schneider N., 2010, A&A, 524, A18](http://dx.doi.org/10.1051/0004-6361/200913286)
[Breen S. L., Ellingsen S. P., 2011, MNRAS, 416, 178](http://dx.doi.org/10.1111/j.1365-2966.2011.19020.x)
Brogan C. L., Hunter T. R., Cyganowski C. J., Indebetouw R., Beuther H.,
[Menten K. M., Thorwirth S., 2009, ApJ, 707, 1](http://dx.doi.org/10.1088/0004-637X/707/1/1)
Brogan C. L., Hunter T. R., Cyganowski C. J., Friesen R. K., Chandler C. J.,
[Indebetouw R., 2011, ApJ, 739, L16](http://dx.doi.org/10.1088/2041-8205/739/1/L16)
Brogan C. L., Hunter T. R., Cyganowski C. J., Chandler C. J., Friesen R.,
[Indebetouw R., 2016, ApJ, 832, 187](http://dx.doi.org/10.3847/0004-637X/832/2/187)
[Busquet G., et al., 2013, ApJ, 764, L26](http://dx.doi.org/10.1088/2041-8205/764/2/L26)
[Butler M. J., Tan J. C., 2009, ApJ, 696, 484](http://dx.doi.org/10.1088/0004-637X/696/1/484)


MNRAS **000**, 1–20 (2023)



[Butler M. J., Tan J. C., 2012, ApJ, 754, 5](http://dx.doi.org/10.1088/0004-637X/754/1/5)
[Cao Y., Qiu K., Zhang Q., Li G.-X., 2022, ApJ, 927, 106](http://dx.doi.org/10.3847/1538-4357/ac4696)
[Caselli P., Ceccarelli C., 2012, A&ARv, 20, 56](http://dx.doi.org/10.1007/s00159-012-0056-x)

Caselli P., Walmsley C. M., Zucconi A., Tafalla M., Dore L., Myers P. C.,
[2002, ApJ, 565, 344](http://dx.doi.org/10.1086/324302)
[Caselli P., van der Tak F. F. S., Ceccarelli C., Bacmann A., 2003, A&A, 403,](http://dx.doi.org/10.1051/0004-6361:20030526)

[L37](https://ui.adsabs.harvard.edu/abs/2003A&A...403L..37C)

Caselli P., Vastel C., Ceccarelli C., van der Tak F. F. S., Crapsi A., Bacmann
[A., 2008, A&A, 492, 703](http://dx.doi.org/10.1051/0004-6361:20079009)

Ceccarelli C., Caselli P., Bockelée-Morvan D., Mousis O., Pizzarello S.,

Robert F., Semenov D., 2014, in Beuther H., Klessen R. S., Dullemond C. P., Henning T., eds, Protostars and Planets VI. p. 859
( `[arXiv:1403.7143](http://arxiv.org/abs/1403.7143)` [), doi:10.2458/azu_uapress_9780816531240-ch037](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch037)
[Chen H.-R. V., et al., 2019, ApJ, 875, 24](http://dx.doi.org/10.3847/1538-4357/ab0f3e)
[Chen C.-Y., Mundy L. G., Ostriker E. C., Storm S., Dhabal A., 2020a, MN-](http://dx.doi.org/10.1093/mnras/staa960)
[RAS, 494, 3675](http://dx.doi.org/10.1093/mnras/staa960)

[Chen M. C.-Y., et al., 2020b, ApJ, 891, 84](http://dx.doi.org/10.3847/1538-4357/ab7378)
[Churchwell E., Walmsley C. M., Wood D. O. S., 1992, A&A, 253, 541](https://ui.adsabs.harvard.edu/abs/1992A&A...253..541C)
Clarke S. D., Whitworth A. P., Spowage R. L., Duarte-Cabral A., Suri S. T.,
[Jaffa S. E., Walch S., Clark P. C., 2018, MNRAS, 479, 1722](http://dx.doi.org/10.1093/mnras/sty1675)

[Clarke S. D., Williams G. M., Walch S., 2020, MNRAS, 497, 4390](http://dx.doi.org/10.1093/mnras/staa2298)

[Commerçon B., Hennebelle P., Henning T., 2011, ApJ, 742, L9](http://dx.doi.org/10.1088/2041-8205/742/1/L9)
Cortes P., et al., 2023, ALMA Cycle 10 Technical Handbook,
[doi:10.5281/zenodo.7822943.,](http://dx.doi.org/10.5281/zenodo.7822943. ) `[https://doi.org/10.5281/zenodo.](https://doi.org/10.5281/zenodo.7822943)`

```
  7822943

```

Cunningham A. J., Klein R. I., Krumholz M. R., McKee C. F., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/740/2/107)

[740, 107](https://ui.adsabs.harvard.edu/abs/2011ApJ...740..107C)

[Cyganowski C. J., et al., 2008, AJ, 136, 2391](http://dx.doi.org/10.1088/0004-6256/136/6/2391)
[Cyganowski C. J., Brogan C. L., Hunter T. R., Churchwell E., 2009, ApJ, 702,](http://dx.doi.org/10.1088/0004-637X/702/2/1615)
[1615](https://ui.adsabs.harvard.edu/abs/2009ApJ...702.1615C)

Cyganowski C. J., Brogan C. L., Hunter T. R., Churchwell E., Zhang Q.,
[2011a, ApJ, 729, 124](http://dx.doi.org/10.1088/0004-637X/729/2/124)
Cyganowski C. J., Brogan C. L., Hunter T. R., Churchwell E., 2011b, [ApJ,](http://dx.doi.org/10.1088/0004-637X/743/1/56)

[743, 56](https://ui.adsabs.harvard.edu/abs/2011ApJ...743...56C)

Cyganowski C. J., Koda J., Rosolowsky E., Towers S., Donovan Meyer J.,
[Egusa F., Momose R., Robitaille T. P., 2013, ApJ, 764, 61](http://dx.doi.org/10.1088/0004-637X/764/1/61)
[Cyganowski C. J., et al., 2014, ApJ, 796, L2](http://dx.doi.org/10.1088/2041-8205/796/1/L2)
Cyganowski C. J., Brogan C. L., Hunter T. R., Smith R., Kruĳssen J. M. D.,
[Bonnell I. A., Zhang Q., 2017, MNRAS, 468, 3694](http://dx.doi.org/10.1093/mnras/stx043)
Cyganowski C. J., Ilee J. D., Brogan C. L., Hunter T. R., Zhang S., Harries
[T. J., Haworth T. J., 2022, ApJ, 931, L31](http://dx.doi.org/10.3847/2041-8213/ac69ca)
[Dale J. E., Bonnell I., 2011, MNRAS, 414, 321](http://dx.doi.org/10.1111/j.1365-2966.2011.18392.x)

[Dale J. E., Ercolano B., Bonnell I. A., 2012, MNRAS, 424, 377](http://dx.doi.org/10.1111/j.1365-2966.2012.21205.x)

Daniel F., Dubernet M. L., Meuwly M., Cernicharo J., Pagani L., 2005,

[MNRAS, 363, 1083](http://dx.doi.org/10.1111/j.1365-2966.2005.09542.x)

[Daniel F., Cernicharo J., Dubernet M. L., 2006, ApJ, 648, 461](http://dx.doi.org/10.1086/505738)
[Dewangan L. K., Ojha D. K., Baug T., 2017, ApJ, 844, 15](http://dx.doi.org/10.3847/1538-4357/aa79a5)
Dewangan L. K., Ojha D. K., Sharma S., Palacio S. d., Bhadari N. K., Das
[A., 2020, ApJ, 903, 13](http://dx.doi.org/10.3847/1538-4357/abb827)
[Dhabal A., Mundy L. G., Rizzo M. J., Storm S., Teuben P., 2018, ApJ, 853,](http://dx.doi.org/10.3847/1538-4357/aaa76b)
[169](https://ui.adsabs.harvard.edu/abs/2018ApJ...853..169D)

Dhabal A., Mundy L. G., Chen C.-y., Teuben P., Storm S., 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab15d3) [876,](https://ui.adsabs.harvard.edu/abs/2019ApJ...876..108D)

[108](https://ui.adsabs.harvard.edu/abs/2019ApJ...876..108D)

[Dobbs C. L., Bonnell I. A., Clark P. C., 2005, MNRAS, 360, 2](http://dx.doi.org/10.1111/j.1365-2966.2005.08941.x)

Duarte-Cabral A., Bontemps S., Motte F., Hennemann M., Schneider N.,
[André P., 2013, A&A, 558, A125](http://dx.doi.org/10.1051/0004-6361/201321393)

Duarte-Cabral A., Bontemps S., Motte F., Gusdorf A., Csengeri T., Schneider
[N., Louvet F., 2014, A&A, 570, A1](http://dx.doi.org/10.1051/0004-6361/201423677)

[Federrath C., 2013, MNRAS, 436, 1245](http://dx.doi.org/10.1093/mnras/stt1644)

[Federrath C., et al., 2016, ApJ, 832, 143](http://dx.doi.org/10.3847/0004-637X/832/2/143)
[Fernández-López M., et al., 2014, ApJ, 790, L19](http://dx.doi.org/10.1088/2041-8205/790/2/L19)
Friesen R. K., Di Francesco J., Myers P. C., Belloche A., Shirley Y. L., Bourke
[T. L., André P., 2010, ApJ, 718, 666](http://dx.doi.org/10.1088/0004-637X/718/2/666)
Friesen R. K., Di Francesco J., Bourke T. L., Caselli P., Jørgensen J. K.,
[Pineda J. E., Wong M., 2014, ApJ, 797, 27](http://dx.doi.org/10.1088/0004-637X/797/1/27)
Ginsburg A., Mirocha J., 2011, PySpecKit: Python Spectroscopic Toolkit
(ascl:1109.001)

_Filamentary mass accretion towards G11.92 MM2_ 19



Ginsburg A., Sokolov V., de Val-Borro M., Rosolowsky E., Pineda J. E.,
[Sipőcz B. M., Henshaw J. D., 2022, AJ, 163, 291](http://dx.doi.org/10.3847/1538-3881/ac695a)
[Gómez G. C., Vázquez-Semadeni E., 2014, ApJ, 791, 124](http://dx.doi.org/10.1088/0004-637X/791/2/124)
[Goodman A. A., Benson P. J., Fuller G. A., Myers P. C., 1993, ApJ, 406, 528](http://dx.doi.org/10.1086/172465)
Goodman A. A., Rosolowsky E. W., Borkin M. A., Foster J. B., Halle M.,
[Kauffmann J., Pineda J. E., 2009, Nature, 457, 63](http://dx.doi.org/10.1038/nature07609)

[Hacar A., Alves J., Tafalla M., Goicoechea J. R., 2017, A&A, 602, L2](http://dx.doi.org/10.1051/0004-6361/201730732)

Hacar A., Tafalla M., Forbrich J., Alves J., Meingast S., Grossschedl J.,
[Teixeira P. S., 2018, A&A, 610, A77](http://dx.doi.org/10.1051/0004-6361/201731894)

[Harris C. R., et al., 2020, Nature, 585, 357](http://dx.doi.org/10.1038/s41586-020-2649-2)

[Hennemann M., et al., 2012, A&A, 543, L3](http://dx.doi.org/10.1051/0004-6361/201219429)

Henshaw J. D., Caselli P., Fontani F., Jiménez-Serra I., Tan J. C., Hernandez

[A. K., 2013, MNRAS, 428, 3425](http://dx.doi.org/10.1093/mnras/sts282)

Henshaw J. D., Caselli P., Fontani F., Jiménez-Serra I., Tan J. C., 2014,


[MNRAS, 440, 2860](http://dx.doi.org/10.1093/mnras/stu446)

[Henshaw J. D., et al., 2016, MNRAS, 457, 2675](http://dx.doi.org/10.1093/mnras/stw121)

[Henshaw J. D., et al., 2017, MNRAS, 464, L31](http://dx.doi.org/10.1093/mnrasl/slw154)

[Henshaw J. D., et al., 2019, MNRAS, 485, 2457](http://dx.doi.org/10.1093/mnras/stz471)

[Hofner P., Churchwell E., 1996, A&AS, 120, 283](https://ui.adsabs.harvard.edu/abs/1996A&AS..120..283H)

[Holdship J., et al., 2021, A&A, 654, A55](http://dx.doi.org/10.1051/0004-6361/202141233)
[Hu B., et al., 2021, ApJ, 908, 70](http://dx.doi.org/10.3847/1538-4357/abd03a)
[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
Hunter T. R., Brogan C. L., Cyganowski C. J., Schnee S., 2015, in EAS
[Publications Series. pp 285–286, doi:10.1051/eas/1575057](http://dx.doi.org/10.1051/eas/1575057)
Hunter T. R., Petry D., Barkats D., Corder S., Indebetouw R., 2023, analy[sisUtils, Zenodo, doi:10.5281/zenodo.7502160](http://dx.doi.org/10.5281/zenodo.7502160)

Ilee J. D., Cyganowski C. J., Nazari P., Hunter T. R., Brogan C. L., Forgan
[D. H., Zhang Q., 2016, MNRAS, 462, 4386](http://dx.doi.org/10.1093/mnras/stw1912)
Ilee J. D., Cyganowski C. J., Brogan C. L., Hunter T. R., Forgan D. H.,
[Haworth T. J., Clarke C. J., Harries T. J., 2018, ApJ, 869, L24](http://dx.doi.org/10.3847/2041-8213/aaeffc)
Jackson J. M., Finn S. C., Chambers E. T., Rathborne J. M., Simon R., 2010,

[ApJ, 719, L185](http://dx.doi.org/10.1088/2041-8205/719/2/L185)
[Kainulainen J., Ragan S. E., Henning T., Stutz A., 2013, A&A, 557, A120](http://dx.doi.org/10.1051/0004-6361/201321760)
[Kauffmann J., Pillai T., 2010, ApJ, 723, L7](http://dx.doi.org/10.1088/2041-8205/723/1/L7)
[Keown J., et al., 2019, ApJ, 884, 4](http://dx.doi.org/10.3847/1538-4357/ab3e76)
Kirk H., Myers P. C., Bourke T. L., Gutermuth R. A., Hedden A., Wilson
[G. W., 2013, ApJ, 766, 115](http://dx.doi.org/10.1088/0004-637X/766/2/115)
[Kong S., et al., 2016, ApJ, 821, 94](http://dx.doi.org/10.3847/0004-637X/821/2/94)
Kong S., Tan J. C., Caselli P., Fontani F., Liu M., Butler M. J., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/834/2/193)

[834, 193](https://ui.adsabs.harvard.edu/abs/2017ApJ...834..193K)

Kong S., Arce H. G., Tobin J. J., Zhang Y., Maureira M. J., Kratter K. M.,
[Pillai T. G. S., 2023, ApJ, 950, 187](http://dx.doi.org/10.3847/1538-4357/acd252)
[König C., et al., 2017, A&A, 599, A139](http://dx.doi.org/10.1051/0004-6361/201526841)
[Könyves V., et al., 2020, A&A, 635, A34](http://dx.doi.org/10.1051/0004-6361/201834753)
Koumpia E., Evans L., Di Francesco J., van der Tak F. F. S., Oudmaĳer R. D.,
[2020, A&A, 643, A61](http://dx.doi.org/10.1051/0004-6361/202038457)

Krumholz M. R., Klein R. I., McKee C. F., Offner S. S. R., Cunningham A. J.,
[2009, Science, 323, 754](http://dx.doi.org/10.1126/science.1165857)

[Kuiper R., Hosokawa T., 2018, A&A, 616, A101](http://dx.doi.org/10.1051/0004-6361/201832638)
[Kuiper R., Yorke H. W., Turner N. J., 2015, ApJ, 800, 86](http://dx.doi.org/10.1088/0004-637X/800/2/86)
[Kumar M. S. N., Palmeirim P., Arzoumanian D., Inutsuka S. I., 2020, A&A,](http://dx.doi.org/10.1051/0004-6361/202038232)


[642, A87](https://ui.adsabs.harvard.edu/abs/2020A&A...642A..87K)

[Li S., et al., 2022, ApJ, 926, 165](http://dx.doi.org/10.3847/1538-4357/ac3df8)
[Lindner R. R., et al., 2015, AJ, 149, 138](http://dx.doi.org/10.1088/0004-6256/149/4/138)

[Liu T., et al., 2016, ApJ, 824, 31](http://dx.doi.org/10.3847/0004-637X/824/1/31)
[Liu H.-L., et al., 2023, MNRAS, 522, 3719](http://dx.doi.org/10.1093/mnras/stad047)

[Lu X., et al., 2018, ApJ, 855, 9](http://dx.doi.org/10.3847/1538-4357/aaad11)
[Ma Y., Zhou J., Esimbek J., Ji W., Wu G., Yuan Y., 2013, Ap&SS, 345, 297](http://dx.doi.org/10.1007/s10509-013-1405-6)
[Maschberger T., Clarke C. J., Bonnell I. A., Kroupa P., 2010, MNRAS, 404,](http://dx.doi.org/10.1111/j.1365-2966.2010.16346.x)
[1061](https://ui.adsabs.harvard.edu/abs/2010MNRAS.404.1061M)

[McKee C. F., Tan J. C., 2002, Nature, 416, 59](http://dx.doi.org/10.1038/416059a)

[McKee C. F., Tan J. C., 2003, ApJ, 585, 850](http://dx.doi.org/10.1086/346149)
[Miettinen O., 2012a, A&A, 540, A104](http://dx.doi.org/10.1051/0004-6361/201118552)

[Miettinen O., 2012b, A&A, 542, A101](http://dx.doi.org/10.1051/0004-6361/201219144)

[Miettinen O., 2020, A&A, 634, A115](http://dx.doi.org/10.1051/0004-6361/201936730)

[Mignon-Risse R., González M., Commerçon B., 2021, A&A, 656, A85](http://dx.doi.org/10.1051/0004-6361/202141648)
[Molet J., et al., 2019, A&A, 626, A132](http://dx.doi.org/10.1051/0004-6361/201935497)



Mookerjea B., Veena V. S., Güsten R., Wyrowski F., Lasrado A., 2023,

[MNRAS, 520, 2517](http://dx.doi.org/10.1093/mnras/stad215)

[Müller H. S. P., Thorwirth S., Roth D. A., Winnewisser G., 2001, A&A, 370,](http://dx.doi.org/10.1051/0004-6361:20010367)

[L49](https://ui.adsabs.harvard.edu/abs/2001A&A...370L..49M)

Müller H. S. P., Schlöder F., Stutzki J., Winnewisser G., 2005, [Journal](http://dx.doi.org/10.1016/j.molstruc.2005.01.027) of

[Molecular Structure, 742, 215](http://dx.doi.org/10.1016/j.molstruc.2005.01.027)
[Myers P. C., 2009, ApJ, 700, 1609](http://dx.doi.org/10.1088/0004-637X/700/2/1609)
Myers A. T., McKee C. F., Cunningham A. J., Klein R. I., Krumholz M. R.,
[2013, ApJ, 766, 97](http://dx.doi.org/10.1088/0004-637X/766/2/97)
[Nony T., et al., 2018, A&A, 618, L5](http://dx.doi.org/10.1051/0004-6361/201833863)
Öberg K. I., van Broekhuizen F., Fraser H. J., Bisschop S. E., van Dishoeck
[E. F., Schlemmer S., 2005, ApJ, 621, L33](http://dx.doi.org/10.1086/428901)
[Ossenkopf V., Henning T., 1994, A&A, 291, 943](https://ui.adsabs.harvard.edu/abs/1994A&A...291..943O)
[Padoan P., Pan L., Juvela M., Haugbølle T., Nordlund Å., 2020, ApJ, 900, 82](http://dx.doi.org/10.3847/1538-4357/abaa47)
[Pagani L., Daniel F., Dubernet M. L., 2009, A&A, 494, 719](http://dx.doi.org/10.1051/0004-6361:200810570)
[Palmeirim P., et al., 2013, A&A, 550, A38](http://dx.doi.org/10.1051/0004-6361/201220500)
[Peretto N., Fuller G. A., 2010, ApJ, 723, 555](http://dx.doi.org/10.1088/0004-637X/723/1/55510.48550/arXiv.1009.0716)
[Peretto N., et al., 2013, A&A, 555, A112](http://dx.doi.org/10.1051/0004-6361/201321318)

[Peretto N., et al., 2014, A&A, 561, A83](http://dx.doi.org/10.1051/0004-6361/201322172)
Pillai T., Caselli P., Kauffmann J., Zhang Q., Thompson M. A., Lis D. C.,
[2012, ApJ, 751, 135](http://dx.doi.org/10.1088/0004-637X/751/2/135)
[Qi C., et al., 2013, Science, 341, 630](http://dx.doi.org/10.1126/science.1239560)
[Ragan S. E., Heitsch F., Bergin E. A., Wilner D., 2012, ApJ, 746, 174](http://dx.doi.org/10.1088/0004-637X/746/2/174)
[Rathborne J. M., Jackson J. M., Simon R., 2006, ApJ, 641, 389](http://dx.doi.org/10.1086/500423)
Redaelli E., Bovino S., Giannetti A., Sabatini G., Caselli P., Wyrowski F.,
[Schleicher D. R. G., Colombo D., 2021, A&A, 650, A202](http://dx.doi.org/10.1051/0004-6361/202140694)

Redaelli E., Bovino S., Sanhueza P., Morii K., Sabatini G., Caselli P., Giannetti
[A., Li S., 2022, ApJ, 936, 169](http://dx.doi.org/10.3847/1538-4357/ac85b4)
Riener M., Kainulainen J., Henshaw J. D., Orkisz J. H., Murray C. E., Beuther
[H., 2019, A&A, 628, A78](http://dx.doi.org/10.1051/0004-6361/201935519)
Robitaille T., Bressert E., 2012, APLpy: Astronomical Plotting Library
in Python, Astrophysics Source Code Library, record ascl:1208.017
(ascl:1208.017)
[Rosen A. L., 2022, ApJ, 941, 202](http://dx.doi.org/10.3847/1538-4357/ac9f3d)
[Rosen A. L., Krumholz M. R., 2020, AJ, 160, 78](http://dx.doi.org/10.3847/1538-3881/ab9abf)

[Rosen A. L., Krumholz M. R., McKee C. F., Klein R. I., 2016, MNRAS, 463,](http://dx.doi.org/10.1093/mnras/stw2153)

[2553](https://ui.adsabs.harvard.edu/abs/2016MNRAS.463.2553R)

[Rosen A. L., Li P. S., Zhang Q., Burkhart B., 2019, ApJ, 887, 108](http://dx.doi.org/10.3847/1538-4357/ab54c6)
[Rosolowsky E. W., Pineda J. E., Kauffmann J., Goodman A. A., 2008, ApJ,](http://dx.doi.org/10.1086/587685)

[679, 1338](https://ui.adsabs.harvard.edu/abs/2008ApJ...679.1338R)

[Sabatini G., et al., 2021, A&A, 652, A71](http://dx.doi.org/10.1051/0004-6361/202140469)
[Sato M., et al., 2014, ApJ, 793, 72](http://dx.doi.org/10.1088/0004-637X/793/2/72)
Schneider N., Csengeri T., Bontemps S., Motte F., Simon R., Hennebelle P.,
[Federrath C., Klessen R., 2010, A&A, 520, A49](http://dx.doi.org/10.1051/0004-6361/201014481)

[Schneider N., et al., 2012, A&A, 540, L11](http://dx.doi.org/10.1051/0004-6361/201118566)

Schöier F. L., van der Tak F. F. S., van Dishoeck E. F., Black J. H., 2005,


[A&A, 432, 369](http://dx.doi.org/10.1051/0004-6361:20041729)
Shimajiri Y., André P., Palmeirim P., Arzoumanian D., Bracco A., Könyves
[V., Ntormousi E., Ladjelate B., 2019a, A&A, 623, A16](http://dx.doi.org/10.1051/0004-6361/201834399)
Shimajiri Y., André P., Ntormousi E., Men’shchikov A., Arzoumanian D.,
[Palmeirim P., 2019b, A&A, 632, A83](http://dx.doi.org/10.1051/0004-6361/201935689)
[Smilgys R., Bonnell I. A., 2016, MNRAS, 459, 1985](http://dx.doi.org/10.1093/mnras/stw791)
[Smilgys R., Bonnell I. A., 2017, MNRAS, 472, 4982](http://dx.doi.org/10.1093/mnras/stx2396)
[Smith R. J., Longmore S., Bonnell I., 2009, MNRAS, 400, 1775](http://dx.doi.org/10.1111/j.1365-2966.2009.15621.x)
[Smith R. J., Glover S. C. O., Klessen R. S., 2014, MNRAS, 445, 2900](http://dx.doi.org/10.1093/mnras/stu1915)

[Smith R. J., Glover S. C. O., Klessen R. S., Fuller G. A., 2016, MNRAS, 455,](http://dx.doi.org/10.1093/mnras/stv2559)

[3640](https://ui.adsabs.harvard.edu/abs/2016MNRAS.455.3640S)

[Stark R., van der Tak F. F. S., van Dishoeck E. F., 1999, ApJ, 521, L67](http://dx.doi.org/10.1086/312182)
[Tackenberg J., et al., 2014, A&A, 565, A101](http://dx.doi.org/10.1051/0004-6361/201321555)
[Tan J. C., Kong S., Butler M. J., Caselli P., Fontani F., 2013, ApJ, 779, 96](http://dx.doi.org/10.1088/0004-637X/779/2/96)
Tan J. C., Beltrán M. T., Caselli P., Fontani F., Fuente A., Krumholz M. R.,

McKee C. F., Stolte A., 2014, in Beuther H., Klessen R. S., Dullemond C. P., Henning T., eds, Protostars and Planets VI. pp 149–172
( `[arXiv:1402.0919](http://arxiv.org/abs/1402.0919)` [), doi:10.2458/azu_uapress_9780816531240-ch007](http://dx.doi.org/10.2458/azu_uapress_9780816531240-ch007)
[Tan J. C., Kong S., Zhang Y., Fontani F., Caselli P., Butler M. J., 2016, ApJ,](http://dx.doi.org/10.3847/2041-8205/821/1/L3)

[821, L3](https://ui.adsabs.harvard.edu/abs/2016ApJ...821L...3T)
[Thwala S. A., Shafi N., Colafrancesco S., Govoni F., Murgia M., 2019, MN-](http://dx.doi.org/10.1093/mnras/stz347)
[RAS, 485, 1938](http://dx.doi.org/10.1093/mnras/stz347)


MNRAS **000**, 1–20 (2023)

20 _S. Zhang et al._


[Tigé J., et al., 2017, A&A, 602, A77](http://dx.doi.org/10.1051/0004-6361/201628989)
[Treviño-Morales S. P., et al., 2019, A&A, 629, A81](http://dx.doi.org/10.1051/0004-6361/201935260)
Vastel C., Caselli P., Ceccarelli C., Phillips T., Wiedner M. C., Peng R., Houde
[M., Dominik C., 2006, ApJ, 645, 1198](http://dx.doi.org/10.1086/504371)
Vasyunin A. I., Semenov D. A., Wiebe D. S., Henning T., 2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/691/2/1459) [691,](https://ui.adsabs.harvard.edu/abs/2009ApJ...691.1459V)
[1459](https://ui.adsabs.harvard.edu/abs/2009ApJ...691.1459V)

Vázquez-Semadeni E., Gómez G. C., Jappsen A. K., Ballesteros-Paredes J.,
[González R. F., Klessen R. S., 2007, ApJ, 657, 870](http://dx.doi.org/10.1086/510771)
Vázquez-Semadeni E., González-Samaniego A., Colín P., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stw3229)

[467, 1313](https://ui.adsabs.harvard.edu/abs/2017MNRAS.467.1313V)
Vázquez-Semadeni E., Palau A., Ballesteros-Paredes J., Gómez G. C.,
[Zamora-Avilés M., 2019, MNRAS, 490, 3061](http://dx.doi.org/10.1093/mnras/stz2736)

[Virtanen P., et al., 2020, Nature Methods, 17, 261](http://dx.doi.org/10.1038/s41592-019-0686-2)
[Wang K., et al., 2014, MNRAS, 439, 3275](http://dx.doi.org/10.1093/mnras/stu127)
Wang J.-W., Koch P. M., Galván-Madrid R., Lai S.-P., Liu H. B., Lin S.-J.,
[Pattle K., 2020, ApJ, 905, 158](http://dx.doi.org/10.3847/1538-4357/abc74e)
Williams G. M., Peretto N., Avison A., Duarte-Cabral A., Fuller G. A., 2018,


[A&A, 613, A11](http://dx.doi.org/10.1051/0004-6361/201731587)

[Xu F.-W., et al., 2023, MNRAS, 520, 3259](http://dx.doi.org/10.1093/mnras/stad012)
[Yuan J., et al., 2018, ApJ, 852, 12](http://dx.doi.org/10.3847/1538-4357/aa9d40)
[Zamora-Avilés M., Ballesteros-Paredes J., Hartmann L. W., 2017, MNRAS,](http://dx.doi.org/10.1093/mnras/stx1995)


[472, 647](https://ui.adsabs.harvard.edu/abs/2017MNRAS.472..647Z)

[Zernickel A., Schilke P., Smith R. J., 2013, A&A, 554, L2](http://dx.doi.org/10.1051/0004-6361/201321425)
[Zhang Q., Wang K., Lu X., Jiménez-Serra I., 2015, ApJ, 804, 141](http://dx.doi.org/10.1088/0004-637X/804/2/141)
[Zhou J.-W., et al., 2021, MNRAS, 508, 4639](http://dx.doi.org/10.1093/mnras/stab2801)

[Zhou J.-W., et al., 2022, MNRAS, 514, 6038](http://dx.doi.org/10.1093/mnras/stac1735)

[Zhou J.-W., et al., 2023, MNRAS, 519, 2391](http://dx.doi.org/10.1093/mnras/stac3559)
[van Dishoeck E. F., Phillips T. G., Keene J., Blake G. A., 1992, A&A, 261,](https://ui.adsabs.harvard.edu/abs/1992A&A...261L..13V)

[L13](https://ui.adsabs.harvard.edu/abs/1992A&A...261L..13V)

[van der Tak F. F. S., Caselli P., Ceccarelli C., 2005, A&A, 439, 195](http://dx.doi.org/10.1051/0004-6361:20052792)

van der Tak F. F. S., Black J. H., Schöier F. L., Jansen D. J., van Dishoeck

[E. F., 2007, A&A, 468, 627](http://dx.doi.org/10.1051/0004-6361:20066820)

van ’t Hoff M. L. R., Walsh C., Kama M., Facchini S., van Dishoeck E. F.,

[2017, A&A, 599, A101](http://dx.doi.org/10.1051/0004-6361/201629452)


**APPENDIX A:** **EXAMPLES OF N** 2 **H** [+] **(4-3) SPECTRA**
**FITTED WITH SCOUSEPY**


Figure A1 shows a sample of the N 2 H [+] (4-3) spectra that are extracted around the local peak in the integrated N 2 H [+] emission to the
north of MM2 (i.e. location A in Fig. 3). The observed spectra are
overlaid with the SCOUSEPY fits obtained following the procedures
described in Section 4.1.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–20 (2023)

_Filamentary mass accretion towards G11.92 MM2_ 21







0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45

km/s



0.3


0.2


0.1


0.0


0.3


0.2


0.1


0.0


0.3


0.2


0.1


0.0


0.3


0.2


0.1


0.0


0.3


0.2


0.1


0.0





25 30 35 40 45



0.4


0.3


0.2


0.1


0.0


0.4


0.3


0.2


0.1


0.0



25 30 35 40 45



0.4


0.3


0.2


0.1


0.0


0.4


0.3


0.2


0.1


0.0



25 30 35 40 45



0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45

km/s









25 30 35 40 45



25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45

km/s





25 30 35 40 45





25 30 35 40 45





25 30 35 40 45

km/s



25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45


0.2


0.1


0.0


25 30 35 40 45

km/s



**Figure A1.** N 2 H [+] (4-3) spectra extracted around the local peak in the integrated N 2 H [+] emission to the north of MM2 (i.e. location A in Fig. 3). The observed
N 2 H [+] spectra are shown in black, overlaid with individual best-fitting Gaussian components (blue), total best-fitting models (red), and residuals (green). Each
panel is labelled with the pixel coordinates where the spectrum was extracted; the spectrum extracted at location A is additionally labelled with “A”.


MNRAS **000**, 1–20 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Cleaning: peak intensity >= 3 sigma, peak intensity and velocity dispersion > associated uncertainties (~94% of components retained)",
  "failed_quote": "We discard ∼ all pixels without fits ( 5% of the total SCOUSEPY data), remove components with peak intensities < 3 𝜎 (where 𝜎 is the rms, measured individually for each spectrum), and remove components where either the peak intensity or the velocity dispersion is smaller than its associated uncertainty."
 },
 {
  "path": "analysis_steps[2].key_parameters[1].evidence[0]",
  "value": "Min cluster radius = 4 x pixel size, min height above merge level = 3 x mean rms, max velocity difference = 0.2 km/s, max velocity dispersion difference = 0.2 km/s",
  "failed_quote": "The minimum radius of a cluster is set to 4× the pixel size to ensure that the minimum number of data points in a cluster is comparable to the number of pixels in a synthesised beam (∼52). The minimum height above the merge level is set to be 3× the mean rms and the maximum absolute velocity difference between two components identified as linked is set to 0.2 km s [−][1], the channel width of the N 2 H [+] image cube (Section 2). We add an additional clustering criterion based on the velocity dispersion, requiring the absolute difference in velocity dispersion between two linked components to be smaller than 0.2 km s [−][1] ."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Fit a first-degree bivariate polynomial (linear velocity gradient model of Goodman et al. 1993) to centroid velocity maps using LMFIT",
  "failed_quote": "We estimate the values of 𝑎 and 𝑏 by fitting a first-degree bivariate polynomical to the centroid velocity map of Branch 8 using LMFIT [7] ."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Non-linear least-squares minimisation using LMFIT, weighted by centroid velocity uncertainties from SCOUSEPY",
  "failed_quote": "We estimate the values of 𝑎 and 𝑏 by fitting a first-degree bivariate polynomical to the centroid velocity map of Branch 8 using LMFIT [7] . The uncertainties associated with the centroid velocities from SCOUSEPY are included to constrain the fitting."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "Optically thin, isothermal dust emission; gas-to-dust ratio = 100; cylindrical filament geometry; 50% efficiency of mass transport onto protostars",
  "failed_quote": "For a simple cylindrical model with a length of 𝐿, a mass of 𝑀, a velocity gradient observed along the main axis of the filament of ∇ 𝑣, and an inclination angle to the plane of sky of 𝛼, the rate of mass flow 𝑀 [] is given by (Kirk et al. 2013):"
 },
 {
  "path": "analysis_steps[5].assumptions[0].evidence[2]",
  "value": "Uniform T_ex across hyperfine lines; LAMDA collisional rates for N2H+ with H2 scaled from He; CDMS partition function interpolated at T_ex = 14 K",
  "failed_quote": "The partition function for T 𝑒𝑥 = 14 K is interpolated using values from the Cologne Database for Molecular Spectroscopy (CDMS, Müller et al. 2001, 2005)."
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Fitting a first-degree bivariate polynomial to centroid velocity maps to measure velocity gradients",
  "failed_quote": "We estimate the values of 𝑎 and 𝑏 by fitting a first-degree bivariate polynomical to the centroid velocity map of Branch 8 using LMFIT [7] ."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "H2D+ (1_1,0 - 1_1,1) and N2H+ (4-3) trace cold, dense, and CO-depleted gas expected in high-mass prestellar cores at sub-arcsecond (~2000 AU) resolution.",
  "failed_quote": "To investigate the properties of a candidate high-mass prestellar core and its relationship to its environment, we proposed ALMA Cycle 3-5 observations of G11.92-0.61 MM2 targeting H 2 D [+] (1 1 , 0 -1 1 , 1 ) and N 2 H [+] (4-3), which trace dense and depleted gas (Ceccarelli et al. 2014)"
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[1]",
  "value": "Continuum flux and mass estimates for MM2 and Branch 8 do not separate the compact core emission from the background filament, and mass inflow rates have a factor of ~2 systematic uncertainty plus inclination and temperature uncertainties.",
  "failed_quote": "We also note that we have not attempted to impose a boundary between 0.82 mm continuum emission associated with the filament and with the MM2 core."
 }
]
```
