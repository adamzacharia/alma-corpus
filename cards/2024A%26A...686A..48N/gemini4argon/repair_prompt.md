# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A..48N\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. clean ©ESO 2024
April 26, 2024

## **CON-quest**

### II. Spatially and spectrally resolved HCN/HCO [+] line ratios in local luminous and **ultraluminous infrared galaxies**


Y. Nishimura [1][,][ 2][,][ 3], S. Aalto [4], M. D. Gorski [4], S. König [4], K. Onishi [4], C. Wethers [4], C. Yang [4], L. Barcos-Muñoz [5],
F. Combes [6], T. Díaz-Santos [7][,][ 8], J. S. Gallagher [9][,][ 10], S. García-Burillo [11], E. González-Alfonso [12], T. R. Greve [13][,][ 14],
N. Harada [3][,][ 15], C. Henkel [16][,][ 17], M. Imanishi [3], K. Kohno [2], S. T. Linden [18], J. G. Mangum [5], S. Martín [19][,][ 20], S. Muller [4],
G. C. Privon [5][,][ 21][,][ 22], C. Ricci [23][,][ 24], F. Stanley [26], P. P. van der Werf [27], and S. Viti [27][,][ 28]


_(A_ ffi _liations can be found after the references)_


Received October 20, 2023 / Accepted February 23, 2023


**ABSTRACT**


_Context._ Nuclear regions of ultraluminous and luminous infrared galaxies (U/LIRGs) are powered by starbursts and/or active galactic nuclei
(AGNs). These regions are often obscured by extremely high columns of gas and dust. Molecular lines in the submillimeter windows have the
potential to determine the physical conditions of these compact obscured nuclei (CONs).
_Aims._ We aim to reveal the distributions of HCN and HCO [+] emission in local U/LIRGs and investigate whether and how they are related to galaxy
properties.
_Methods._ Using the Atacama Large Millimeter/submillimeter Array (ALMA), we have conducted sensitive observations of the HCN _J_ =3–2 and
HCO [+] _J_ =3–2 lines toward 23 U/LIRGs in the local Universe ( _z_ < 0.07) with a spatial resolution of ∼0.3 [′′] (∼50–400 pc).
_Results._ We detected both HCN and HCO [+] in 21 galaxies, only HCN in one galaxy, and neither in one galaxy. The global HCN/HCO [+] line
ratios, averaged over scales of ∼0.5–4 kpc, range from 0.4 to 2.3, with an unweighted mean of 1.1. These line ratios appear to have no systematic
trend with bolometric AGN luminosity or star formation rate. The line ratio varies with position and velocity within each galaxy, with an average
interquartile range of 0.38 on a spaxel-by-spaxel basis. In eight out of ten galaxies known to have outflows and/or inflows, we found spatially and
kinematically symmetric structures of high line ratios. These structures appear as a collimated bicone in two galaxies and as a thin spherical shell
in six galaxies.
_Conclusions._ Non-LTE analysis suggests that the high HCN/HCO [+] line ratio in outflows is predominantly influenced by the abundance ratio.
Chemical model calculations indicate that the enhancement of HCN abundance in outflows is likely due to high-temperature chemistry triggered
by shock heating. These results imply that the HCN/HCO [+] line ratio can aid in identifying the outflow geometry when the shock velocity of the
outflows is sufficiently high to heat the gas.


**Key words.** galaxies: evolution – galaxies: nuclei – galaxies: ISM – ISM: molecules – ISM: jets and outflows



**1.** **Introduction**


Luminous infrared galaxies (LIRGs; _L_ IR (8−1000 µm) = 10 [11] –
10 [12] _L_ ⊙ ) and ultraluminous infrared galaxies (ULIRGs:
_L_ IR ≥ 10 [12] _L_ ⊙ ; see e.g., Sanders & Mirabel 1996; Pérez-Torres
et al. 2021, for reviews) emit most of their energy at infrared
wavelengths and are powered by nuclear starbursts and/or active
galactic nuclei (AGNs) in their central regions. Observational
and theoretical studies have both proposed that gas-rich galaxy
mergers are one of the most important mechanisms to trigger
starbursts and fuel supermassive black holes (SMBHs), namely
by funneling large amounts of gas and dust into the nuclei (e.g.,
Sanders et al. 1988; Hopkins et al. 2006). These studies have
also pointed out that the central SMBHs are deeply embedded
by high columns of obscuring material during the process
of mass accretion and that U/LIRGs eventually evolve into
optically visible quasars when nuclear feedback (i.e., outflow)
disperses the surrounding material. Hence, the evolution of
U/LIRGs is of key importance to account for the large number
of luminous quasars at high redshift, as merger events are
considered to have been more frequent in the early Universe
(e.g., Romano et al. 2021).



There is currently mounting evidence that U/LIRGs
often host compact (≲100 pc) and highly enshrouded
( _N_ H 2 ≳ 10 [24] cm [−][2] ) nuclei (e.g., Sakamoto et al. 2013; Martín
et al. 2016; Aalto et al. 2019; Ricci et al. 2021). These compact
obscured nuclei (CONs) exhibit bright emission of rotational
transition of HCN, which is vibrationally excited by the midinfrared continuum emitted from dust (henceforth referred to as
HCN-vib; e.g., Sakamoto et al. 2010; Costagliola et al. 2013;
Imanishi & Nakanishi 2013; Aalto et al. 2015b, 2019). Using
HCN-vib emission, Falstad et al. (2021, hereafter Paper I)
conducted a systematic survey of CONs, and revealed that
∼50% of the ULIRGs and ∼20% of the LIRGs host CONs.


Because of the high obscuration by dust, it is often difficult for observations at many wavelengths to probe the embedded nuclear activities in the center of U/LIRGs (e.g., Lutz et al.
1996). In particular for CON-host galaxies, we need probes free
from severe extinction to know the physical properties of the
nuclear regions, such as, if and how much the buried AGNs
contribute to the total energy of the source. Molecular lines at
(sub)millimeter wavelengths are less affected by dust extinction
and thus have been explored for useful diagnostic methods. As a


Article number, page 1 of 52

_A&A proofs:_ manuscript no. clean



best practice, enhanced HCN/HCO [+] line ratios [1] (≳1) have been
proposed as being characteristic of the AGN-dominated galaxies (e.g., Kohno et al. 2001; Krips et al. 2008; Imanishi et al.
2009). The high HCN/HCO [+] line ratio was at first interpreted
as a high abundance of HCN due to X-ray ionization in the
close vicinity of an AGN (Lepp & Dalgarno 1996). However,
there are some composite and starburst-dominated galaxies that
show line ratios comparable to or higher than those of AGNdominated galaxies, suggesting that not only X-ray irradiation
but also other processes, such as optical depths, can elevate the
line ratios (Costagliola et al. 2011; Privon et al. 2015). Highresolution observations toward nearby AGN-host galaxies have
revealed that the HCN/HCO [+] line ratios vary within a few hundred parsec of circumnuclear disks around the AGNs and peak
at off-centered locations in the disks (NGC 1068: García-Burillo
et al. 2014; Viti et al. 2014; Izumi et al. 2016; NGC 1097: Martín
et al. 2015). There are also some cases where the elevated line
ratio is totally unrelated to the AGNs (NGC 3256: Harada et al.
2018; NGC 4194: König et al. 2018), implying that there are
several mechanisms that can elevate the line ratios in the disks.
Given these observational facts, further investigation is needed
regarding how to use this line ratio as a diagnostic tool for hidden nuclear activities.

There has been extensive discussion on the possible mechanisms for enhancing HCN abundances. As mentioned earlier,
the effect of X-ray ionization was first served as a reason for
HCN enhancements in AGNs (Lepp & Dalgarno 1996). Subsequent studies, however, have painted a more complex picture that
would likely take place in the centers of active galaxies. Chemical models developed by Meijerink & Spaans (2005) have explored a wide range of physical conditions in X-ray dominated
regions (XDRs, Maloney et al. 1996) and photon dominated regions (PDRs, Tielens & Hollenbach 1985). Based on these models, Meijerink et al. (2007) noted that the high HCN/HCO [+] line
ratio is not exclusively seen in XDRs, and thus AGN contribution
may be hard to recognize only by the HCN/HCO [+] line ratio. Furthermore, Viti et al. (2014) pointed out that the observed molecular line ratios in the center of NGC 1068, including species other
than HCN and HCO [+], could not be reproduced by a single model
per region.
Chemical models have also suggested that another important
chemical process would be high-temperature gas-phase chemistry that can form HCN via the reaction CN + H 2 → HCN + H
with an activation barrier of 820 K (Harada et al. 2010, 2013).
A high temperature can be generated by Coulomb heating in
regions affected by XDRs, PDRs, and cosmic-ray dominated
regions (CRDRs) with electrons produced by X-ray, UV, and
cosmic-ray ionization, respectively, as well as mechanical heating by shocks in the vicinity of a nucleus. Indeed, shock heating can reasonably explain the bright HCN emission in the line
wings (i.e., the outflowing components) of Mrk 231 (Aalto et al.
2015a; Lindberg et al. 2016). Such bright HCN emission in
the outflow has also been reported for the western nucleus of
Arp 220 (Barcos-Muñoz et al. 2018).
Not only chemical processes regarding molecules but the
elemental abundance ratio is also a matter of concern for the
HCN/HCO [+] line ratio. Bayet et al. (2008) modeled molecular
abundances in hot cores with different initial elemental abundances and showed that the abundance of HCN, along with
other nitrogen-bearing species such as HNC, tends to be roughly


1 Throughout this paper, “line ratio” refers to the line intensity ratio
or, equivalently, the line luminosity ratio. The line luminosity _L_ [′] is expressed in units of K km s [−][1] pc [2] .


Article number, page 2 of 52



scaled with total nitrogen abundance. Observations toward lowmetallicity molecular clouds also showed that the elemental
N/O ratio crucially affects the HCN/HCO [+] abundance ratio
in nitrogen-poor subsolar-metallicity galaxies (e.g., Nishimura
et al. 2016a,b; Braine et al. 2017). This scaling effect, however,
has not been fully examined for solar- and supersolar-metallicity
galaxies where the elemental N/O ratio can be elevated by differential galactic winds (e.g., Vincenzo et al. 2016).
To enhance the HCN/HCO [+] line ratio, the excitation condition also plays an important role. Because HCN and HCO [+]
have different excitation properties, the HCN/HCO [+] line ratio
can be a function of local gas density and temperature. Several
studies have highlighted that the higher critical density required
for HCN excitation compared to that of HCO [+] could contribute
to the high line ratios in denser regions (e.g., Krips et al. 2008;
Costagliola et al. 2011; Privon et al. 2015; Imanishi et al. 2019).
However, relying only on the traditional definition of critical
density may lead to inaccuracies. Factors that have been suggested to affect line emission include radiative trapping in dense
regions (Shirley 2015) and weak extended emission in diffuse
regions (e.g., Kauffmann et al. 2017; Nishimura et al. 2017; Pety
et al. 2017). It is also crucial to account for other excitation
mechanisms, such as collision with free electrons (Goldsmith &
Kauffmann 2017) and mid-infrared pumping (Aalto et al. 2007).
This is the second paper of a series named “CON-quest,”
whose aim is to understand the evolution of infrared luminous galaxies, in particular those that host CONs. In this paper, we present the results of the HCN _J_ =3–2 and HCO [+]
_J_ =3–2 line observations toward 23 U/LIRGs using the Atacama Large Millimeter/submillimeter Array (ALMA), focusing
on how the HCN and HCO [+] line fluxes are related to galaxy
properties. Specifically, we tackle the following questions: Can
the HCN/HCO [+] line ratio by itself be used as a diagnostic tool
for the AGN strength in moderate-resolution (several tens to
hundreds of parsec) observations? What are the determining factors of the HCN/HCO [+] line ratio? Which of these factors are
most important for the line ratio, and in what condition?
The paper is organized as follows. We introduce the sample
in Sect. 2 and describe the ALMA observations and data reduction in Sect. 3. The results are presented in Sect. 4 and 5, where
we focus on the line emission and the line ratios, respectively.
In Sect. 6, we discuss the line ratios in terms of excitation conditions and abundances of molecules. The main conclusions of

this work are summarized in Sect. 7.


**2.** **Sample**


The sample of this study consists of eight ULIRGs and 15 LIRGs
in the local Universe ( _z_ < 0.07), as listed in Table 1. This is a
subset of galaxies from the parent sample presented in Paper I
with six additional galaxies. The scope of this paper is limited
to the newly obtained data from dedicated ALMA observations
(project ID: 2017.1.00759.S and 2018.1.01344.S). We do not address the sub-LIRGs ( _L_ IR = 10 [10] –10 [11] _L_ ⊙ ) included in the parent
sample, and the results of the HCN and HCO [+] observations for
these galaxies will be published in a separate paper (Onishi et
al., in prep.). This sample selection was done to ensure that the
source properties could be compared properly by only studying
sources that have HCN and HCO [+] data with similar sensitivities and spatial resolutions. In addition to the targeted galaxies described above, our sample contains another six galaxies:
IRAS F05189−2524, IRAS F10565+2448, IRAS 19542+1110,
ESO 148−IG002, NGC 6240, and UGC 11763. These galaxies
were also observed in the same ALMA projects but were not in

Y. Nishimura et al.: CON-quest



cluded in the sample of Paper I because they did not meet the
selection criteria for Paper I due to the slightly larger distances.
Inclusion of these galaxies does not change the range of the infrared luminosity of the sample as a whole but breaks the completeness of the sample held in Paper I.
In Table 1, we list the main properties of the sample galaxies: redshift, luminosity distance, and infrared luminosity. All
of these quantities are calculated consistently with Paper I, as
detailed in the footnotes of Table 1. Additionally, we compiled
several galaxy properties from the literature that are of particular interest in the context of the evolution of U/LIRGs: bolometric AGN fraction, merger stage, and presence of CONs and
molecular in- and outflow. For the bolometric AGN fraction, we
employed the relative AGN contribution to the bolometric total luminosity calculated by Díaz-Santos et al. (2017) based on
_Spitzer_ /IRS spectroscopic data. Díaz-Santos et al. (2017) combined up to five mid-infrared diagnostics, depending on the availability of data: the [Ne v] 14.3 /[Ne ii] 12.8 and [O iv] 25.9 /[Ne ii] 12.8
line ratio, the equivalent width (EQW) of the 6.2 µm polycyclic
aromatic hydrocarbons (PAH), the _S_ 30 / _S_ 15 dust continuum ratio,
and the Laurent diagram (Laurent et al. 2000). They then applied
corrections to derive the bolometric AGN fraction (Veilleux et al.
2009). We used these values as best estimates while keeping
in mind the limitations of mid-infrared diagnostics when dealing with obscured nuclei. For instance, the [Ne v] and [O iv]
line fluxes tend to be smaller for deeply buried AGNs (Yamada
et al. 2019). In addition, the 6.2 µm PAH EQW diagnostics may
overestimate the AGN fraction for starburst galaxies due to the
brighter continuum used as a baseline value (Privon et al. 2020).
For the merger stage, we adopted the visual classification by
Stierwalt et al. (2013) based on _Spitzer_ /IRAC 3.6 µm images.
The existence of a CON is based on the HCN-vib surface density measured by Paper I. For the galaxies not covered in Paper I,
the assessment of CON was not conducted in the same method.
For IRAS F10565+2448, IRAS 19542+1110, ESO 148−IG002,
and UGC 11763, we found no feature of HCN-vib emission, suggesting that they are most likely classified as non-CONs. While
IRAS F05189−2524 shows faint HCN-vib emission, it does not
meet the criteria for CON classification in the earlier work (Falstad et al. 2019). For NGC 6240, the broad line width of the
neighboring HCO [+] emission complicates its evaluation. Alternative methods to evaluate the existence of a CON would be necessary for NGC 6240. The presence of outflows and inflows was
inferred from far-infrared spectroscopy of the OH lines and/or
(sub)millimeter interferometry of the CO lines. We note that
these tables are just a compilation of published information. The
unlisted galaxies may have hitherto unknown outflows and inflows.


**3.** **Observations and data reduction**


The HCN 3–2 and HCO [+] 3–2 line observations were carried out
with ALMA using the band 6 receivers during Cycle 6 and 7 as
two projects: 2017.1.00759.S and 2018.1.01344.S (PI: S. Aalto).
Here, we outline the fundamental properties of each program.
_2017.1.00759.S:_ The nine U/LIRGs IRAS 17208−0014,
IRAS 09022−3615, IRAS 13120−5453, IRAS F14378−3651,
IRAS F05189−2524, IRAS 19542+1110, ESO 148−IG002,
NGC 6240, and UGC 11763 were observed in September 2018
with the array configuration C43-5. The baseline lengths span
between 15 m and 2 km, resulting in an angular resolution of
∼0.3 [′′] and a maximum recoverable scale (MRS) of ∼3–4 [′′] .
_2018.1.01344.S:_ As part of this project, the 14
U/LIRGs IRAS F10565+2448, IRAS F17138−1017,



IRAS 17578−0400, ESO 173−G015, NGC 3110, IC 4734,
NGC 5135, ESO 221−IG10, IC 5179, UGC 2982, NGC 2369,
ESO 286−G035, ESO 320−G030, and NGC 5734 were observed between October 2018 and October 2019 with the array
configurations C43-4 and C43-5. The baseline lengths span
between 15 m and 2.5 km, resulting in an angular resolution of
∼0.3 [′′] and an MRS of ∼3–4 [′′] .

In both projects, the total integration time per field was ≲2
hours. Bright quasars were used as bandpass and flux calibrators, ensuring flux accuracy better than 10% at Band 6. Fainter
quasars close to each target were used for phase calibration. We
used a single pointing with a field of view of ∼20 [′′] for each target. While the nominal MRS for the employed array configuration is ∼9 [′′], as mentioned above, the effective MRS can be as
small as ∼3–4 [′′] in our observations, depending on antenna availability. Given that the LIRG sample is located at smaller distances compared to the ULIRG sample, the potential impact of
interferometric missing flux may be systematically more significant for the LIRG samples. This issue could affect galaxy-togalaxy comparisons, as discussed in Sect. 4.4. At this moment,
single-dish measurements are not homogeneously available for
all sample galaxies to calibrate this missing flux issue. Nevertheless, we acknowledge the importance of addressing this problem
in future studies.

The correlator setup was the same for all targets: Two spectral windows of 1.875 GHz width were placed in the upper sideband with native channel widths of 3.9 MHz, centered at each
of HCN _J_ =3–2 (rest frequency 265.886 GHz) and HCO [+] _J_ =3–2
(rest frequency 267.558 GHz). Two more spectral windows were
placed in the lower sideband for better continuum identification.
Calibration of the interferometric data was done with CASA [2]
(CASA Team et al. 2022, version 5.4.0). The continuum subtraction was performed using the CASA “uvcontsub” task, except for IRAS 17578−0400. For IRAS 17578−0400, it is hard
to find line-free channels due to the large number of emission
lines and the complex line profiles; hence, the continuum was
not subtracted. The imaging of the calibrated visibility sets was
also performed in CASA using the “tclean” task with a natural weighting. The synthesized beams are ∼0.3 [′′], corresponding
to spatial scales of ∼50–400 pc for the range of the target distances, as detailed in Table 2. The data cubes were smoothed to
a velocity resolution of 20 km s [−][1] . The resulting rms noise levels
are given in Table 2. For further analysis, the data cubes were
exported in FITS format.

We analyzed the exported cubes with our own codes, making
use of the following Python packages: astropy [3] (Astropy Collaboration et al. 2013, 2018), spectral-cube, [4] and pvextractor. [5]
In the analysis, we adopted galaxy kinematics roughly estimated
from the velocity field seen outside of the most nuclear region
derived from either HCN or HCO [+] lines. The parameters are
summarized in Table 2, although these may not be robust enough
for a more detailed kinematic analysis. More accurate parameters could be found in the literature and/or derived from alternative molecular tracers such as CO emission. However, at this
moment, such datasets are not homogeneously available for all
target galaxies. Kinematic modeling that takes into account vertical components and non-circular motions is planned for future
studies.


2 `[http://casa.nrao.edu/](http://casa.nrao.edu/)`
3 `[http://www.astropy.org](http://www.astropy.org)`
4 `[https://spectral-cube.readthedocs.io](https://spectral-cube.readthedocs.io)`
5 `[https://pvextractor.readthedocs.io](https://pvextractor.readthedocs.io)`


Article number, page 3 of 52

**4.** **Line emission**


_4.1._ _Spectra_



_A&A proofs:_ manuscript no. clean


minor-axis direction was also found (Yang et al. 2023, Yang et
al., in prep).



To obtain an overview of the HCN and HCO [+] line emission in
each galaxy, we extracted spectra from two kinds of apertures: an
aperture the size of the synthesized beam (hereafter “resolved”)
and an elliptical aperture 10 × 10 times the size of the synthesized beam (hereafter “global”). Both are centered at the position listed in Table 2. The extracted spectra are presented in
Appendix A. The resolved aperture corresponds to the physical
scale of ∼200–400 pc for ULIRGs and ∼50–100 pc for LIRGs.
Consequently, the global aperture corresponds to ∼2–4 kpc for
ULIRGs and ∼0.5–1 kpc for LIRGs. The global aperture covers
all, or nearly all, of the line-emitting regions of each galaxy in
most cases (Sect. 4.2), but it should be noted that a considerable fraction of emission can also be seen outside of the aperture in NGC 6240 (Fig. A.9); IRAS 17578−0400 (Fig. A.11);
ESO 173−G015 (Fig. A.12); IC 4734 (Fig. A.15); NGC 5135
(Fig. A.16); and NGC 2369 (Fig. A.20).
In the spectra, we confirmed a large number of line detections. Toward all galaxies but UGC 11763, UGC 2982 and
NGC 5734, we detected both HCN and HCO [+] lines at more
than 5σ significance regardless of the aperture size for spectral extraction. For UGC 11763, the HCN and HCO [+] lines
were marginally detected at ∼3σ and ∼5σ significance, respectively, only on the velocity-integrated intensity extracted from
the resolved aperture (Fig. A.13). For NGC 5734, HCN was
clearly detected, but HCO [+] is totally absent (Fig. A.23). Neither HCN nor HCO [+] was detected in UGC 2982 (Fig. A.19).
We note that these non-detections are in the sources with the
lowest _L_ IR in our sample. In addition to HCN and HCO [+],
other molecular species were detected in several sources: HC 3 Nvib (v 7 =2, _J_ =29–28, _l_ =2 _e_ ; 265.462 GHz); CH 2 NH (4 1,3 –3 1,2 ;
266.270 GHz); HCN-vib (v 2 =1, _J_ =3–2; 267.199 GHz); CH 3 OH
(5 2 –4 1 E1; 266.838 GHz); and HOC [+] ( _J_ =3–2; 268.451 GHz).
Detailed analysis of these molecular species is beyond the scope
of this paper and would need to be presented in dedicated works
(as in Gorski et al. 2023, for CH 2 NH).
In most target galaxies, the HCN and HCO [+] lines exhibit
complex line profiles that cannot be properly fitted by a single Gaussian, similar to what has been reported in other studies (e.g., Martín et al. 2016; Imanishi et al. 2019). Among them,
there are several galaxies with asymmetric double-peaked profiles. Such features are more clearly seen in the resolved spectra
than the global ones. Although we cannot exclude the possibility
that these features are caused by clumpy and non-axisymmetric
circumnuclear disks, the double-peaked profiles are more likely
to be absorption features resulting from self-absorbing gas near
the nuclei (i.e., outflows or inflows), as explained below. The absorption peak was found to be slightly blueshifted relative to the
systemic velocity in IRAS 17208−0014 and IRAS 17578−0400
(Fig. A.1 and Fig. A.11, respectively), while it is redshifted in
ESO 173−G015 and ESO 320−G030 (Fig. A.12 and Fig. A.22,
respectively).
The absorption features more blueshifted than about
−50 km s [−][1] can be interpreted as signposts of outflows (e.g.,
Veilleux et al. 2013). For IRAS 17208−0014 (Fig. A.1), it is
consistent with the fact that molecular outflows are found by interferometric observations of the CO line (García-Burillo et al.
2015). For IRAS 17578−0400 (Fig. A.11), the low-velocity
elongation of the HCN and HCO [+] emission along its kinematic
minor axis would be indicative of an outflow, as pointed out in
Paper I (see Fig. 8 of Paper I). In higher-resolution observations
of the same HCN and HCO [+] transitions, an elongation in the


Article number, page 4 of 52



On the other hand, the redshifted absorption features
could be indicative of inflowing motions. In ESO 173−G015
(Fig. A.12), the absorption peaks are redshifted to ∼50 km s [−][1]
in the resolved spectra (extracted from the 51 × 47 pc elliptical aperture) and are at near the systemic velocity in the global
spectra (510 × 470 pc). Regarding ESO 173−G015, it does not
have any published evidence of inflow (nor outflow), but detection of HCN-vib has been reported in its center, although not
bright enough to be categorized as a CON (Paper I). The nuclear properties and the gas kinematics of this galaxy would be
worth investigating in more detail. The absorption features in
ESO 320−G030 (Fig. A.22) are clearly seen in the resolved spectra (62 × 53 pc) but are only marginally seen in the global spectra
(620 × 530 pc). This is reasonably understood considering that
the inflows take place on smaller scales (130 pc and 230–460 pc;
González-Alfonso et al. 2021), while outflows are present on a
much larger scale (∼2500 pc; Pereira-Santaella et al. 2016) in
ESO 320−G030.


_4.2._ _Moment maps_


The integrated intensity (moment 0), velocity field (moment 1),
and velocity dispersion (moment 2) maps of the HCN and HCO [+]
lines for all targets are presented in Appendix A. The velocity
ranges we considered in order to derive the moment maps are
listed in Table 3. These ranges were determined through visual
inspection of the global spectra, and we examined the velocity
at which the intensity drops below the noise level. We did not
correct for potential line overlapping. As the lines of CH 2 NH,
HC 3 N-vib, and HCN-vib sit close to the HCN and HCO [+] lines
(separations are <500 km s [−][1] ), the moment maps of a line-rich
source may be affected by the neighboring lines when the velocity range exceeds about ±300 km s [−][1] . No clipping was applied
for the integrated intensity maps in order to salvage the faint
emission, while we used a 3σ threshold clipping to properly derive the velocity field and the dispersion. The velocity dispersion
was plotted as the square root of the intensity-weighted second
moment of the spectrum. To help identify the kinematic center
and compare panels, the kinematic major and minor axes are
drawn in each panel.


4.2.1. Integrated intensity maps


The integrated intensity maps show that the HCN and HCO [+] line
emission mostly emerges from a central region in each galaxy.
The apparent size of the line-emitting region is typically 1–3 kpc
in the ULIRGs and 0.5–1 kpc in the LIRGs. Thus, the global
aperture covers the major line-emitting region in each galaxy.
The most remarkable exceptions are NGC 5135 and NGC 2369,
as NGC 5135 shows a spiral arm-like structure extended over
∼2 kpc from the center (Fig. A.16), and NGC 2369 shows an
edge-on disk with a ∼2 kpc radius (Fig. A.20). Attention should
also be paid to four other galaxies: NGC 6240 (Fig. A.9);
IRAS 17578−0400 (Fig. A.11); ESO 173−G015 (Fig. A.12); and
IC 4734 (Fig. A.15), which show significant emission outside of
the global aperture. We may have failed to recover the emission
extended beyond the MRS because of the lack of short baseline
in interferometric observations. The MRS is ∼3–4 [′′], which corresponds to ∼2–3 kpc and ∼0.6–1.5 kpc on average for ULIRGs
and LIRGs, respectively. Hence the LIRGs at relatively smaller

Y. Nishimura et al.: CON-quest



distances could be affected by the missing fluxes. We further infer this from line luminosities in Sect. 4.4.


4.2.2. Velocity field and dispersion maps


The velocity field and dispersion maps clearly indicate that
the rotating motions are dominant in the sample galaxies, although some galaxies exhibit indications of irregular motions

− −
(e.g., IRAS 09022 3615 (Fig. A.2); ESO 148 IG002 (Fig. A.8);
IRAS F17138−1017 (Fig. A.10); NGC 5135 (Fig. A.16); and
NGC 2369 (Fig. A.20)). Considerably disordered motion was
found in NGC 6240 (Fig. A.9), which is a merger hosting two
AGNs separated by ∼1.7 [′′] (projected; e.g., Komossa et al. 2003).
For NGC 6240, the moment maps of HCN and HCO [+] are overall similar to those of CO _J_ =2–1 (Treister et al. 2020; Saito et al.
2018) and [C i] [3] P 1 – [3] P 0 (Cicone et al. 2018), indicating the ubiquity of HCN and HCO [+] in the molecular gas and the complex
nature of the gas kinematics in the system.
While the velocity fields derived from HCN and HCO [+]
are generally similar to each other, subtle differences are
found in certain galaxies. Specifically, in the central regions of
IRAS 13120−5453 (Fig. A.3); IRAS F14378−3651 (Fig. A.4);
IRAS F05189−2524 (Fig. A.5); IRAS F10565+2448 (Fig. A.6);
IRAS 19542+1110 (Fig. A.7); and ESO 320−G030 (Fig. A.22),
the velocity dispersion of HCN is slightly larger than that
of HCO [+] . Remarkably, all of these galaxies are known to
have molecular outflows, as listed in Table 1. In these galaxies, the superposition of the outflow velocities may be responsible for the increased dispersion of HCN because the
abundance of HCN can be enhanced in the outflows, as dis
−
cussed in Sect. 5.4 and 6.2. Conversely, for IRAS 17208 0014,

−
NGC 6240, and IRAS 17578 0400, where outflows are known,
the line-broadening effect for HCN is not as evident when compared with HCO [+] (Fig.A.1, Fig.A.9, and Fig.A.11, respectively).
This is likely due to the distorted velocity field of HCO [+] caused
by the neighboring HCN-vib line in IRAS 17208−0014 and
IRAS 17578−0400, resulting in the inaccurate measurement of
the dispersion of HCO [+] . However, a different explanation may
be considered for the outflow in NGC 6240, where the shock velocity is relatively small (∼10 km s [−][1] ; Meijerink et al. 2013) and
the HCN abundance is not enhanced in the outflow. This point is
discussed in Sect. 6.2.


_4.3._ _Line luminosities_


Based on the extracted spectra (Sect. 4.1), we derived the resolved and global luminosities of HCN and HCO [+] used in this
study, and we list them in Table 3. These luminosities were
calculated in units of K km s [−][1] pc [2] following the equation from
Solomon & Vanden Bout (2005): _L_ [′] = 3.25×10 [7] _S_ ∆v ν obs [−][2] _[D]_ L [2] [(1][+]
_z_ ) [−][3], where _S_ ∆v is the velocity-integrated line flux density in
Jy km s [−][1], ν obs is the observed frequency in GHz, and _D_ L is
the luminosity distance in Mpc. The ranges for velocity integration are the same as those used to derive the moment
maps, as listed in Table 3. Due to blending with the neighboring CH 2 NH (−432 km s [−][1] wrt. HCN), HC 3 N-vib (+480 km s [−][1]
wrt. HCN), and HCN-vib (+402 km s [−][1] wrt. HCO [+] ) lines, the
HCN and HCO [+] line flux density may be overestimated. For
simplicity, we took into account all channels within the integration range and did not apply any correction for line blending. Hence, the values should be taken with caution, particularly
for the galaxies with broad line profiles (≳300 km s [−][1] ), namely,
IRAS 17208−0014 (Fig. A.1); IRAS 09022−3615 (Fig. A.2);



IRAS 13120−5453 (Fig. A.3); and NGC 6240 (Fig. A.9). Partic
−
ularly, the resolved spectra of IRAS 17208 0014 and the global
spectra of NGC 6240 exhibit broad and complex line shapes
that prevented us from obtaining precise measurement of the
line luminosities. For a more accurate estimation excluding line
blending effects, we suggest consulting references such as the
CO line profiles detailed in García-Burillo et al. (2015) for
IRAS 17208−0014 and in Saito et al. (2018) for NGC 6240. We
note that the values for IRAS 17578−0400 have large uncertainties because we could not identify line-free channels, and continuum subtraction was done by assuming continuum levels of
0.02 Jy and 0.07 Jy for the resolved and global spectra, respectively, based on the lowest intensity channels (Fig. A.11).


_4.4._ _Correlation with infrared luminosity_


A correlation between infrared luminosity ( _L_ IR ) and molecular
line luminosity ( _L_ mol [′] [)] [was] [found] [by] [early] [studies] [(e.g.,] [Kenni-]
cutt 1998; Gao & Solomon 2004), and interpreted as a relation
between star formation rate (SFR) and molecular gas content, as
proposed earlier by Schmidt (1959). The observations were extensively conducted toward nearby galaxies (e.g., Graciá-Carpio
et al. 2008; Privon et al. 2015; Zhang et al. 2014; JiménezDonaire et al. 2019; Israel 2023) as well as toward high-redshift
systems (e.g., Oteo et al. 2017). The observed relation was found
to be the power-law form of _L_ IR ∝ _L_ mol [′] _[N]_ [,] [where] [the] [index] _[N]_ [de-]
pends on the molecular transition (e.g., Bussmann et al. 2008;
Juneau et al. 2009). The indices for commonly observed transitions of CO, HCN, and HCO [+] have been quantitatively predicted
by simulations (e.g., Krumholz & Thompson 2007; Narayanan
et al. 2008).
In Fig. 1, we present the relation between the global HCN
and HCO [+] luminosities ( _L_ HCN [′] [and] _[L]_ HCO [′] [+] [as] [calculated] [in]
Sect. 4.3) and _L_ IR (calculated from IRAS fluxes taken from
Sanders et al. (2003); see Sect. 2 and Table 1 for details) for our
sample. Both _L_ HCN [′] [and] _[L]_ HCO [′] [+] [appear to correlate well with] _[L]_ [IR]
(Pearson correlation coefficients _r_ = 0.85 and 0.90, respectively).
If the _L_ IR is corrected for the AGN contribution by (1−α AGN ) _L_ IR,
the correlations are not largely changed ( _r_ = 0.86 for both _L_ HCN [′]
and _L_ [′]
HCO [+] [), implying that the contribution from AGN to the total]
_L_ IR is rather limited. Thus, the correlations would basically reflect the relation between the SFR and the line luminosities. We
also note that if we use a much larger aperture for spectral extraction, for instance 15 [′′] (corresponds to 2.5–20 kpc for our sample),
to include the emission outside the global aperture (Sect. 4.2.1),
the observed trend is not significantly changed.
The fitting results of the _L_ mol [′] [–] _[L]_ [IR] [relations] [are] [log] _[ L]_ [IR] [=]
(0.53 ± 0.03) log _L_ HCN [′] [+] [(7][.][5] [±] [0][.][3)] [and] [log] _[ L]_ [IR] [=] [(0][.][61] [±]
0.03) log _L_ HCO [′] [+] [ +][(6][.][9][±][0][.][2), as plotted by solid lines in Fig. 1. As]
reference, we also plot the fitting results for single-dish measurements of the _J_ =3–2 transitions in nearby galaxies with a range
of 10 [10] _L_ ⊙ < _L_ IR < 10 [12][.][5] _L_ ⊙ reported by Juneau et al. (2009).
Our indices (i.e., the best-fit slopes) are slightly smaller than the
fitting results of Juneau et al. (2009) (0.70±0.09 for HCN 3–2
and 0.81±0.21 for HCO [+] 3–2) and the model prediction (∼0.7
for HCN 3–2; Narayanan et al. 2008).
As an explanation for the smaller slopes in our fitting results,
we note that we may systematically underestimate the line flux
in the LIRGs at smaller distances. Given that the LIRG sample is chosen to have smaller distances than the ULIRG sample, the limited aperture size for spectral extraction (∼3 [′′] ) and
the interferometric missing flux from the extended gas components (≳3–4 [′′] ) could lead to the underestimation of the line
flux in the LIRG sample. The MRS of the observation of ∼3–


Article number, page 5 of 52

_A&A proofs:_ manuscript no. clean



4 [′′] corresponds to a physical scale of ∼0.6–1.5 kpc and ∼2–3 kpc
on average for LIRGs and ULIRGs, respectively. For more accurate measurements of the galaxy-integrated _L_ mol [′] [, observations of]
a larger sample with a single-dish telescope would be essential.
Alternatively, the lower gas temperature and/or the lower mean

                                      density in our LIRG sample could be responsible for the ineffi
cient excitation of HCN and HCO [+] resulting in the lower _L_ HCN [′]
and _L_ [′]
HCO [+] [.]


**5.** **HCN/HCO** [+] **line ratio**


_5.1._ _Global and resolved line ratio_


We calculated the HCN/HCO [+] line ratio ( _L_ HCN [′] [/] _[L]_ HCO [′] [+] [),] [based]
on the line luminosities extracted from the global and resolved
apertures (Sect. 4.3). The results are listed in Table 4. The global
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [ranges] [from] [0.4] [to] [2.3] [among] [the] [detected] [sam-]
ple, with an unweighted mean of 1.1. This range is roughly
comparable to that observed in the local U/LIRGs (e.g., Privon
et al. 2015, for the 1–0 transitions). The resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is]
slightly higher than the global one in most cases (16 of 20 detected cases), ranging from 0.4 to 2.7, with an unweighted mean
of 1.2. This may indicate that HCN would be increased and/or
more efficiently excited in the central regions compared to the
galaxy average. However, we note that a high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is]
also found in other parts of galaxies and is not uniquely associated with the central regions (e.g., the case of ESO 320-G030,
Fig. A.22). Depending on the galaxy inclination, even the resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [can be a reflection of multiple velocity com-]
ponents along the line of sight. As detailed in Sect. 5.3, spectrally
resolved analysis would be helpful to disentangle the nuclear region from the surrounding disk regions.


_5.2._ _Comparison with galaxy properties_


To consider whether _L_ HCN [′] [/] _[L]_ HCO [′] [+] [would be influenced by galaxy]
properties such as AGN dominance and star formation activity,
we compared the global and resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [with] [mid-]
and far-infrared diagnostics available in the literature. As indicators of AGN dominance and strength, we used the bolometric
AGN fraction (α AGN ; as listed in Table 1) and the bolometric
AGN luminosity ( _L_ AGN [bol] [;] [calculated] [as] _[L]_ AGN [bol] [=][ α] [AGN] _[L]_ [bol] [,] [where]
_L_ bol = 1.15 _L_ IR is assumed; Veilleux et al. 2009). We emphasize
that α AGN was inferred from mid-infrared diagnostics, and this
estimation should be treated with caution, particularly in the case
of heavily obscured nuclei. The star formation activity was basically inferred from _L_ IR and quantified as SFR in units of _M_ ⊙ yr [−][1]
via the relation SFR = (1 − α AGN ) × 10 [−][10] _L_ IR on the same assumption as Sturm et al. (2011), that is, the SFR– _L_ IR relation
calibrated by Kennicutt (1998) but using a Chabrier initial mass
function.
In addition, we considered the possible influence by the
dust temperature and the elemental N/O ratio. As a proxy of
the temperature of the warm dust component, we used the
IRAS 60 µm/100 µm flux density ratio ( _S_ 60 / _S_ 100 ; taken from
Sanders et al. 2003). The _S_ 60 / _S_ 100 color ratio of our sample
ranges from 0.4 to 1.2, roughly corresponding to a dust temperature from 30 to 50 K (assuming dust emissivity proportional
to (wavelength) [−][1] ; e.g., Helou et al. 1988). For the elemental
N/O ratio, we used the far-infrared fine-structure line ratio of

[N ii] 122 /[O iii] 88 (calculated from galaxy-integrated line fluxes;
taken from Díaz-Santos et al. 2017) as a rough estimator. We
note that the [N ii] 122 /[O iii] 88 line ratio is roughly scaled by the
elemental N/O abundance ratio, but it would highly depend on


Article number, page 6 of 52



the ionization parameter and the effective temperature of the ionizing source (e.g., Pereira-Santaella et al. 2017; Herrera-Camus
et al. 2018). We only considered 12 galaxies in which both the

[N ii] 122 and [O iii] 88 lines are detected with good significance,
and hence the sample size is smaller than the parent sample in
this work.

We performed a Spearman rank correlation analysis for the
six above-mentioned quantities with each of the global and resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [using] `[pymccorrelation]` [6] [(Privon] [et] [al.]
2020), which implements Monte Carlo-based methods of uncertainty estimation introduced by Curran (2014). The galaxies in
which either HCN or HCO [+] was not detected (i.e., UGC 11763,
UGC 2982, and NGC 5734) were excluded in the analysis. The
coefficients and p-values are summarized in Table 5. Correlation plots are shown in Fig. 2 and Fig. 3 for the global and resolved _L_ [′]
HCN [/] _[L]_ HCO [′] [+] [, respectively. We found no apparent correla-]
tions between _L_ HCN [′] [/] _[L]_ HCO [′] [+] [and any of the galaxy properties.]


5.2.1. Uncorrelated AGN strength


The Spearman test suggests that AGN dominance (α AGN ) does
not correlate with either the global _L_ HCN [′] [/] _[L]_ HCO [′] [+] [or the resolved]
one (Table 5). The same analysis for AGN strength itself ( _L_ AGN [bol] [)]
also showed no clear correlation with the global ratio nor the
resolved one. Based on the p-values, we cannot reject the null
hypothesis that the line ratio and AGN strength are uncorrelated
in our sample.
Whether _L_ HCN [′] [/] _[L]_ HCO [′] [+] [correlates] [with] [AGN] [dominance] [has]
been a controversial issue (e.g., Graciá-Carpio et al. 2008; Privon
et al. 2015; Imanishi et al. 2019). Our results are qualitatively
consistent with Privon et al. (2020), for example, who found
no correlation between the line ratio and X-ray measurements
of AGN. The HCN enhancement by X-ray ionization from the
AGN, if any, does not seem to significantly contribute to elevated _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in][ ≳][100 pc apertures when multiple gas com-]
ponents with different physical and chemical conditions are laid
along the line of sight.


5.2.2. Uncorrelated star formation activity


Based on the Spearman test, we found no evidence for a correlation between _L_ IR and the global _L_ HCN [′] [/] _[L]_ HCO [′] [+] [or between] _[ L]_ [IR] [ and]
the resolved one (Table 5). The result is the same as for the SFR
corrected for the AGN contribution with the global ratio and with
the resolved one. Although both _L_ HCN [′] [and] _[ L]_ HCO [′] [+] [themselves are]
correlated with _L_ IR (Sect. 4.4), _L_ HCN [′] [/] _[L]_ HCO [′] [+] [shows no clear trend]
with _L_ IR or the SFR. The variation of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [among galax-]
ies on ≳100 pc scales cannot be accounted for by the difference
in star formation activity. This result is consistent with the findings of Tan et al. (2018) and Israel (2023), who studied samples
including galaxies with lower _L_ IR .


5.2.3. Uncorrelated dust temperature


The Spearman test showed that the _S_ 60 / _S_ 100 color ratio does not
correlate with the global _L_ HCN [′] [/] _[L]_ HCO [′] [+] [or the resolved one (Table]
5). The large p-values suggest that _L_ HCN [′] [/] _[L]_ HCO [′] [+] [ may be unrelated]
to the dust temperature on ≳100 pc scales. We note that Tan et al.
(2018) also found a qualitatively similar result.


6 `[https://github.com/privong/pymccorrelation](https://github.com/privong/pymccorrelation)`

Y. Nishimura et al.: CON-quest



5.2.4. Marginally correlated N/O abundance ratio


According to the Spearman test, the [N ii] 122 /[O iii] 88 line ratio may moderately correlate with the global _L_ HCN [′] [/] _[L]_ HCO [′] [+]
(ρ=+0.50 [+] − [0] 0 [.] . [25] 32 [,] [p-value][=][0][.][10] [+] − [0] 0 [.] . [42] 09 [),] [although] [the] [p-value] [indi-]
cates that the two quantities may be uncorrelated with a probability of ∼10%. The correlation appears less significant when tested
with the resolved line ratio (ρ=+0.38 [+] − [0] 0 [.] . [26] 32 [,] [p-value][=][0][.][21] [+] − [0] 0 [.] . [46] 19 [).]
Considering that the [N ii] 122 /[O iii] 88 line ratio is the galaxyaveraged value and both line ratios would be affected by the
line optical depths, it would be reasonable that the correlation
is weaker for the resolved _L_ [′]
HCN [/] _[L]_ HCO [′] [+] [.]
The suggested possible correlation is consistent with the
fact that in subsolar-metallicity dwarf galaxies, _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is]
smaller than that of solar-metallicity galaxies (e.g., Nishimura
et al. 2016b,a; Braine et al. 2017). Considering that _L_ HCN [′] [/] _[L]_ HCO [′] [+]
can also be affected by the molecular chemistry, depending on
the local physical conditions, this would imply that we should
take into account the different elemental N/O abundances for the
galaxies with different metallicities in order to highlight the peculiar molecular chemistry in specific regions. More accurate
measurements of elemental abundances with a similar spatial
resolution to molecular observations would be important for a
robust and deeper understanding.


_5.3._ _Spectrally resolved line ratio_


The challenges in studying the kinematics of galaxies using
molecular lines lie in limited spatial resolution and the faintness
of the line emission. The situation has greatly improved with
the advent of ALMA, as demonstrated by earlier studies (e.g.,
García-Burillo et al. 2014; Martín et al. 2015; Saito et al. 2018).
These studies are, however, often restricted to individual sources
and may lack sufficient spatial and/or spectral resolution to resolve the gas morphology. Our current study stands out due to its
unique combination of homogeneously high sensitivity and a relatively large sample size. Leveraging this advantage, our aim is
to investigate _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in a spatially and spectrally resolved]

manner.
To explore the variation of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [across di][ff][erent po-]
sitions and different velocities within each galaxy, we generated
cubes of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [and] [conducted] [analyses] [in] [both] [a] [spec-]
trally integrated manner (pixel-by-pixel analysis) and a spectrally resolved manner (spaxel-by-spaxel analysis). Each pixel
and spaxel has dimensions of 0.05 [′′] ×0.05 [′′] and 0.05 [′′] ×0.05 [′′] ×20
km s [−][1], respectively, for all galaxies.
For a pixel-by-pixel analysis, we initially performed spectral
integration followed by applying a 3σ threshold clipping. In the
spaxel-by-spaxel analysis, we first adopted a 3σ threshold clipping to both HCN and HCO [+] cubes and then calculated the ratio
only for the spaxels where line emission from both species is detected with a greater than 3σ significance. The adoption of the
3σ threshold clipping for the spaxels was primarily to reduce the
contamination by the random Gaussian noise. We note, however,
that faint but real emission contained in spaxels with a less than
3σ significance may be ignored by the clipping.
Table 6 summarizes the key statistical features, including
the mean, the 25th-50th-75th and 90th percentiles, and the
interquartile range for both the pixel-by-pixel and spaxel-byspaxel analyses. Figure 4 visualizes the same quantities for 20
galaxies significantly detected in both HCN and HCO [+] emission
(i.e., all the sample galaxies excluding UGC 11763, UGC 2982,
and NGC 5734). In general, the spectrally resolved (spaxel-byspaxel) ratio tends to exhibit a wider range of values than the



spectrally integrated (pixel-by-pixel) ratio within each galaxy.
This broadening of the range is most significant and toward
larger values in eight galaxies with known molecular outflows
except for NGC 6240 (seven in the left-most side and one in the
right-most side of Fig.4).
In some galaxies, the high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions] [show] [spa-]
tially and kinematically symmetric structures. The characteristic structure clearly emerged when we picked out the spaxels
with _L_ HCN [′] [/] _[L]_ HCO [′] [+] [higher than the 90th percentile from all spax-]
els in both HCN and HCO [+] in each galaxy. In Figs. 5–8, we
present visualization of spaxels with _L_ HCN [′] [/] _[L]_ HCO [′] [+] [exceeding the]
90th percentile in the position-position-velocity (ppV) space for
10 galaxies with known molecular out- and/or inflows (See Table 1). Indeed, symmetric morphology can be found in eight
galaxies shown in Figs. 5–7. The morphology can be roughly
categorized into two types: a filled bicone (IRAS 17208−0014
and IRAS 13120−5453; Fig. 5) and a thin spherical shell
(IRAS 09022−3615, IRAS F14378−3651, IRAS F05189−2524,
IRAS F10565+2448, IRAS 19542+1110, and ESO 320−G030;
Figs. 6 and 7). For NGC 6240 and IRAS 17578-0400 (Fig. 8),
the spaxels with a high line ratio appear randomly in the ppV
space, likely in part because of the unsubtracted continuum in
IRAS 17578-0400. For simplicity, we used the 90th percentile as
a threshold for all galaxies. Through visual inspection, we found
the 90th percentile generally produces suitable results to extract
characteristic structures, as compared to the other neighboring
values such as the 85th and 95th percentile. Understanding the
underlying physics that make this threshold effective could be an
interesting theme for future studies.
For reference, the ppV plots for the entire set of spaxels as
well as for those spaxels that exceed the 90th percentile within
individual galaxies for all galaxies in our sample are presented in
Appendix B. We note that the symmetry is rather distorted, but
it is marginally seen in ESO 148−IG002 and ESO 173−G015.
In the other galaxies, such symmetry is not noticeable, as we
discuss in Appendix C.


_5.4._ _Relation to outflows and inflows_


As mentioned in the previous section, symmetric structures of
high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [are] [present] [in] [some] [of] [our] [sample] [(Figs.] [5–]
7). Notably, such symmetric structures are predominantly found
in galaxies with molecular outflows and/or inflows previously
found by CO and/or OH line observations. For a descriptive
comparison with key parameters of out- and inflows found in
the literature, we encourage readers to refer to Appendix C. If
we consider that the high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions] [are] [associated]
with the gas shocked by the out- and/or inflowing materials, plotting _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in the ppV space could be a useful method to]
look for out- and inflows and study their geometry independently
from kinematic modeling.
In our sample, symmetrically enhanced HCN is frequently
seen in ULIRGs and is rare in LIRGs. Our results may
suggest that nuclear feeding and feedback are predominantly
taking place in IR-brighter galaxies. However, fast shocks
(v shock ≳ 20 km s [−][1] ) may be required for the prominent enhancement of HCN (see Sect. 6.2 for details), and thus we cannot rule
out the presence of out- and inflows with slower shocks or no
shock in our sample galaxies.


**6.** **Discussion**


As presented in Figs. 4 and B.1, _L_ HCN [′] [/] _[L]_ HCO [′] [+] [varies] [greatly]
from galaxy to galaxy and from position to position within each


Article number, page 7 of 52

_A&A proofs:_ manuscript no. clean



galaxy. In a galaxy-to-galaxy comparison, _L_ HCN [′] [/] _[L]_ HCO [′] [+] [shows]
no clear correlation with galaxy properties such as AGN dominance, but it might be marginally scaled by the elemental N/O
ratio (Sect. 5.2). On the other hand, the variation of _L_ HCN [′] [/] _[L]_ HCO [′] [+]
in the ppV space of each galaxy seems to be related to outand inflows. In this section, we try to figure out the most critical factor for the elevation of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in out- and inflows.]
We discuss _L_ HCN [′] [/] _[L]_ HCO [′] [+] [with] [regard] [to] [molecular] [abundances]
and excitation conditions, by non-LTE radiative transfer calculations (Sect. 6.1). We also consider the excitation by collision
with electrons, which could be effective for HCN in a moderately dense condition (Goldsmith & Kauffmann 2017). With
constraints on the molecular abundances obtained from the nonLTE analysis, we ran chemical models and tested if shocks can
reproduce the line ratio observed in out- and inflows (Sect. 6.2).


_6.1._ _Excitation conditions_


To inspect the molecular abundances and excitation conditions
for the observed _L_ [′]
HCN [/] _[L]_ HCO [′] [+] [, we made calculations to study the]
line ratios as functions of gas density in various physical conditions. Given that both HCN and HCO [+] are likely to be subthermally excited (see Sect. 4.4), we adopted the non-local thermal
equilibrium (non-LTE) radiative transfer model, assuming uniform sphere geometry with a large velocity gradient (LVG, see
e.g., Goldreich & Kwan 1974). Practically, we used a publicly
available code, RADEX [7] (van der Tak et al. 2007), to predict the
line intensity. RADEX requires five input parameters: the background temperature, the column density of the molecular species
in question, the line width, the kinetic temperature, and the H 2
density. In all of our calculations, the background temperature
was fixed to be the temperature of the cosmic microwave background (i.e., 2.7 K). We note that the background temperature
could be higher in the nuclear region, but this fixed temperature
assumption is acceptable for a large part of each outflow when
considering that the continuum emission is much more compact
(e.g., Pereira-Santaella et al. 2021). We implemented the molecular column density as a product of the H 2 column density ( _N_ H 2 )
and a fractional abundance of the species ( _X_ mol ). For _N_ H 2, we
considered three plausible values for U/LIRGs: 10 [22], 10 [23], and
10 [24] cm [−][2] . We varied _X_ HCN to cover a wide range of values:
1 × 10 [−][8], 5 × 10 [−][8], 1 × 10 [−][7], 3 × 10 [−][7], and 5 × 10 [−][7] . On the
other hand, _X_ HCO [+] was fixed to the reference value 10 [−][8] . The validity of these fractional abundances are discussed in Sect. 6.2.
The line width (∆v) was set to be 50 km s [−][1] . This value is somewhat smaller than the observed values, but we can consider the
emission as arising from an ensemble of such clouds. We explored three values for the kinetic temperature ( _T_ kin ): 20, 50, and
100 K. The H 2 density ( _n_ H 2 ) was set to 100 values logarithmically spaced in a range from 10 [1] cm [−][3] to 10 [9] cm [−][3] . The collisional rate coefficients are taken from Dumouchel et al. (2010)
for HCN and from Denis-Alpizar et al. (2020) for HCO [+] .
As partners for collisional excitation, we additionally took
into account free electrons. This was motivated by the indication from Goldsmith & Kauffmann (2017) that electron excitation can be more significant for HCN compared to HCO [+] when
the electron fractional abundance is ≳10 [−][5] and the gas density is ≲10 [5][.][5] cm [−][2] (Goldsmith & Kauffmann 2017). In addition
to the case without collision with electrons, we explored cases
with fractional abundances of electrons ( _X_ _e_ [−] ) of 10 [−][5] and 10 [−][4],
which could be achieved if the cosmic-ray ionization rate is high
(ζ ≳ 10 [−][15] s [−][1] ), such as in the vicinity of supernova remnants


7 `[https://home.strw.leidenuniv.nl/~moldata/radex.html](https://home.strw.leidenuniv.nl/~moldata/radex.html)`


Article number, page 8 of 52



(Ceccarelli et al. 2011). This type of high cosmic-ray ionization
rate is indeed reported for the nearby starburst galaxy NGC 253
(Harada et al. 2021; Holdship et al. 2022). We note that the electron abundance was implemented into RADEX calculations in
the form of a volume density of electrons ( _n_ _e_ [−] = _n_ H 2 _X_ _e_ [−] ). The
collisional rate coefficients for the HCN are taken from Faure
et al. (2007). For HCO [+], the published collisional rate coefficients are only available for _J_ ≤3 levels (Faure & Tennyson 2001;
Singh 2021). As pointed out by Goldsmith & Kauffmann (2017),
these rate coefficients are comparable to those of HCN and consistent with scaling with the square of the dipole moment (µ [2] ).
We provisionally employed the rate coefficients for _J_ ≥3 levels
generated by scaling with µ [2] based on the rate coefficients for
HCN provided by Faure et al. (2007). For a robust discussion
in the future, more accurate rate coefficients for HCO [+] will be

necessary.
We ran RADEX with all combinations of parameters described above and calculated _L_ HCN [′] [/] _[L]_ HCO [′] [+] [as] [a] [function] [of] _[n]_ [H] [2] [.]
The results are plotted in Fig. 9. Each of the nine panels correspond to a different pairing of _N_ H 2 and _T_ kin . The different colors
and line styles in the figure are employed to represent the varying values of _X_ HCN, _X_ HCO [+], and _X_ _e_ [−] . Consistent with such studies
as Butterworth et al. (2022) and Imanishi et al. (2023), Fig. 9 indicates that _L_ HCN [′] [/] _[L]_ HCO [′] [+] [increases as] _[ X]_ [HCN] [/] _[X]_ [HCO] [+] [increases for]
any pairings of _N_ H 2 and _T_ kin . As also noted in Yamada et al.
(2007) and Izumi et al. (2016), for example, _X_ HCN / _X_ HCO [+] ≳ 10 is
necessary to get _L_ HCN [′] [/] _[L]_ HCO [′] [+] [ ≳] [1 unless the density is very high]
(≳10 [6] cm [−][3] ).
The H 2 density also plays an important role in regulating
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [In] [the] [cases] [with] [low] _[N]_ [H] [2] [(left] [panels] [in] [Fig.] [9),]
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [becomes larger at higher densities. This is because]
HCO [+] emission is brightest at densities slightly above its effective critical H 2 density and is a bit less bright at the highest densities, while HCN emission behaves similarly but with a larger
intensity at a higher density. This trend is less pronounced as
_N_ H 2 increases because HCN and HCO [+] emission becomes similarly bright when they are thermalized at high density. In cases
with _X_ HCN - 10 [−][7], bumps of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [are seen in the density]
range of 10 [2] –10 [5] cm [−][3] . These bumps are attributed to the different effective critical density between HCN and HCO [+] (for reference: 2.5×10 [4] cm [−][3] for _N_ HCN = 10 [14] cm [−][2] and 2.6×10 [3] cm [−][3] for
_N_ HCO [+] = 10 [14] cm [−][2], both for _T_ kin = 50 K; Shirley 2015). Because
of radiative trapping, the effective critical density is roughly
scaled by the inverse of _N_ mol . As _N_ HCN increases, the effective
critical density of HCN decreases, and hence the bump tends
to appear at a lower density and becomes more pronounced.
With _X_ HCN / _X_ HCO [+] = 10 (green curves in Fig. 9), which results
in _L_ HCN [′] [/] _[L]_ HCO [′] [+] [of][ ∼][1, the e][ff][ective critical densities of HCN and]
HCO [+] become quite similar, and thus the _L_ HCN [′] [/] _[L]_ HCO [′] [+] [curves]
are almost flat around the critical density. We also tested different reference abundances of HCO [+], such as _X_ HCO [+] = 10 [−][7], and
found qualitatively similar trends.

Another notable feature is that a contribution from electron excitation significantly increases _L_ HCN [′] [/] _[L]_ HCO [′] [+] [at] [moderate]
H 2 densities (∼10 [3] –10 [5] cm [−][3] ). The effect is especially noticeable when the electron abundance is highest ( _X_ _e_ [−] = 10 [−][4] ) and the
HCN abundance is also high ( _X_ HCN - 1 × 10 [−][7] ), in which case
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [can be more than twice as much as the ratio with-]
out electron excitation.
In the case with _N_ H 2 = 10 [24] cm [−][2] and _T_ kin = 50 and 100 K
(lower two panels on the right side of Fig. 9), there are spikes at
_n_ H 2 ∼ 10 [5] –10 [7] cm [−][3], which are caused by population inversion
between the _J_ =2 and 3 levels of HCN. Because these variations

Y. Nishimura et al.: CON-quest



are only seen for a very limited range of parameters, we consider the influence of such population inversion to be negligible
in most observations.
In summary, our one-zone models indicate that _L_ HCN [′] [/] _[L]_ HCO [′] [+]
can attain high values (>1) when _X_ (HCN)/ _X_ (HCO [+] ) exceeds
10 for a significant range of densities. _L_ HCN [′] [/] _[L]_ HCO [′] [+] [will] [be]
further enhanced if electron abundance is considerably high
( _X_ _e_ [−] = 10 [−][4] ).


_6.2._ _Chemical pathways to the enhancement of HCN_


Formation and destruction processes of molecules can be influenced by physical conditions. Galactic outflows and inflows can
be distinguished from other parts of the galaxy by chemistry
induced by shocks. Shock heating affects both gas-phase and
grain-surface reactions and releases species in the icy grain mantles into the gas phase (e.g., Bachiller et al. 2001). Non-thermal
desorption, such as sputtering, also helps in mantle release (e.g.,
Bachiller et al. 2001). In addition, outflows can induce turbulence at the interface between molecular clouds, enabling a continuous exposure of the gas to X-ray, UV, and/or cosmic-ray radiation at the surface. This process can lead to an effective ionization and, in turn, a refreshment of the molecular composition
(García-Burillo et al. 2017).
The enhancement of HCN abundances in shocked regions
is well known for protostellar outflows (e.g., L1157; Bachiller &
Pérez Gutiérrez 1997), and many chemical models have been developed to reproduce the observed abundances (e.g., Burkhardt
et al. 2019). Those chemical models consider the physical conditions as representative of protostellar outflows: the gas density
is set to be as high as ∼10 [5] cm [−][3] . Under such density conditions,
HCN abundances in the gas phase are enhanced immediately
after the passage of shocks (post-shock time of <10 [2] yr) up to
_X_ HCN ∼10 [−][5] due to the release of the ice population by grain heating and sputtering (see e.g. Fig. 4 of Burkhardt et al. 2019). This
enhancement mechanism of HCN could be applied to the case
of galactic outflows and could be able to account, at least in part,
for the observed line ratios in our sample. However, given that
the majority of the gas is in a density range of ∼10 [3] –10 [4] cm [−][3] in
the beam of extragalactic observations, it is essential to consider
the chemistry in the moderately-dense regime.
To examine how shocks affect the chemistry in the
moderately-dense gas (∼10 [3] –10 [4] cm [−][3] ), we experimentally ran
the time-dependent gas-grain chemical code, UCLCHEM [8]
(Holdship et al. 2017), which is publicly available. We adopted
the “C-shock” model of UCLCHEM, which is based on the parameterization of C-type shocks by Jiménez-Serra et al. (2008).
For details, we refer to Viti et al. (2014), García-Burillo et al.
(2017), and Holdship et al. (2017), where models similar to ours
were computed. Here, we provide a concise overview of the most
critical aspects. The model was run in two phases: the pre-shock
and post-shock phases. As a pre-shock condition, we considered
the typical condition of “standard” molecular gas with Galactic elemental abundances. The pre-shock abundances follow the
method employed by Harada et al. (2019): all physical conditions were kept constant at standard Galactic values (H 2 density
10 [3] cm [−][3], temperature 10 K, visual extinction 2 mag, radiation
field 1 Habing, cosmic ionization rate 1.3 × 10 [−][17] s [−][1] ; we note
that these values are provisional and should be better calibrated
for U/LIRGs in future works). The evolution of the molecular
abundances in the gas phase and on the grain surfaces were calculated as a function of time using rate equations. The chemical


8 `[https://uclchem.github.io](https://uclchem.github.io)`



evolution was followed for 10 [5] yr in the pre-shock phase to reproduce realistic molecular abundances observed on cloud scales
(>10 pc; Harada et al. 2019). In the post-shock phase, we tested
four values of shock velocity: 10, 20, 30, and 40 km s [−][1] . During
this phase, the density, temperature, and velocity profile were
varied as a function of time, following the parameterizations of
the shock model. Our model maintained constant values for the
radiation field and the cosmic-ray ionization rate, but it is worth
noting that these parameters would also fluctuate in a real molecular cloud.
In Fig. 10, the evolution of the gas temperature and density
as well as the abundances of HCN, HCO [+], and the electrons are
shown as a function of post-shock time. As shown in Fig. 10, the
HCN abundance is enhanced by a factor of ∼10–100 at ∼10 [3] –
10 [5] yr after the shock, depending on the shock velocity. On the
other hand, the HCO [+] and electron abundances are decreased
during the HCN enhancement. It appears that the HCN abundance falls back to the pre-shock abundance at a post-shock time
of ∼10 [5] yr. This timescale is roughly comparable to the dynamical time of outflows (calculated as _R_ out /v out ).
In our model, unlike the chemistry under the high density
conditions, thermal desorption or sputtering do not contribute to
the HCN enhancement because HCN ice is almost absent in preshock conditions. Instead, the enhancement of HCN is mainly
due to the gas-phase production via the high-temperature reaction: CN+H 2 → HCN+H. Because the rate coefficient of this reaction is a function of temperature ( _k_ = α( _T_ /300 K) [β] exp(−γ/ _T_ )
where α = 4 × 10 [−][13], β = 2.87, γ = 820 K, and _T_ is temperature; Harada et al. 2010), the degree of HCN enhancement
depends on the heating. Consequently, the shock velocity affects
the degree of HCN enhancement. As shown in Fig. 10, shock velocities of 30 and 40 km s [−][1] can reproduce our HCN and HCO [+]
abundances, accounting for the observed line ratio, while 10 and
20 km s [−][1] shocks seem to be insufficient. As mentioned in Appendix C, the HCN enhancement was not found in NGC 6240,
and it might be because the shock velocity is too small to enhance the HCN abundance (Meijerink et al. 2013). However,
considering the results of a high-resolution study in the CO _J_ =2–
1 line, which highlighted the existence of very high-velocity outflows (Saito et al. 2018), NGC 6240 deserves further investigation.
The key reaction (CN + H 2 → HCN + H) suggests that HCN
abundance increases at the expense of CN abundance. Considering that Mrk 231 has an outflow that is notably bright in both
CN (Cicone et al. 2020) and HCN (Aalto et al. 2015a; Lindberg
et al. 2016), it is likely that CN abundance is maintained by the
high ionization rate in the outflow. In environments where C [+] is
abundant, CN can be rapidly formed. A similar rationale can be
applied to the CCH-bright outflow in NGC 1068, as discussed
in García-Burillo et al. (2017). We also note that CN emission
is less affected by electron excitation than HCN (Goldsmith &
Kauffmann 2017). This would provide an additional support for
the enhancement of HCN abundance in outflows.


**7.** **Summary and conclusions**


We conducted observations of the HCN and HCO [+] _J_ =3–2 lines
toward 23 U/LIRGs in the local Universe ( _z_ < 0.07). The spatial resolution was ∼0.3 [′′], which corresponds to ∼50–400 pc
at the distance of each target. The obtained dataset allowed
us to explore the HCN/HCO [+] line ratio ( _L_ HCN [′] [/] _[L]_ HCO [′] [+] [)] [of] [each]
galaxy in a spatially and spectrally resolved manner. We analyzed _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in] [relation] [to] [the] [galaxy] [properties] [such] [as]
AGN dominance and star formation activity, and we found the


Article number, page 9 of 52

_A&A proofs:_ manuscript no. clean



presence of outflows and/or inflows to have the most crucial influence. Non-LTE radiative transfer analysis and chemical models suggest that a higher HCN abundance in shocked regions is
likely to be responsible for a high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in] [out-] [and] [in-]
flows.
The main results and key points from the analysis are the
following:


**–** _Spectra_ _and_ _moment_ _maps_ . The line emission of HCN and
HCO [+] was successfully detected with a signal-to-noise ratio
of >5 σ in 21 out of the 23 galaxies. The line profiles of HCN
and HCO [+] are often complex and cannot be fitted by a single
Gaussian. The HCN and HCO [+] emission is mostly emitted
from a central region of each galaxy. The apparent size of the
line-emitting region is typically 1–3 kpc in ULIRGs and 0.5–
1 kpc in LIRGs. In almost all the galaxies with known molecular outflows, the velocity dispersion of the HCN emission is
higher than that of HCO [+] .
**–** _Correlation between line luminosity and infrared luminosity_ .
We found _L_ HCN [′] [and] _[L]_ HCO [′] [+] [correlate well with] _[L]_ [IR] [(correla-]
tion coefficients of 0.85 and 0.90, respectively). These relations are quantitatively consistent with previous observations
and model predictions. The _L_ HCN [′] [–] _[L]_ [IR] [ and] _[ L]_ HCO [′] [+] [–] _[L]_ [IR] [ slopes]
of ∼0.5–0.6 suggest that HCN and HCO [+] are ubiquitously
distributed in the molecular gas with a wide range of densities, and most of them are subthermally excited.
**–** _Line_ _ratio_ _and_ _its_ _correlation_ _with_ _galaxy_ _properties_ . The
velocity-integrated _L_ HCN [′] [/] _[L]_ HCO [′] [+] [extracted from a large aper-]
ture (∼3 [′′] ) in each galaxy is in the range of 0.4–2.3. The unweighted mean is 1.1. Although the HCN/HCO [+] has been
proposed as AGN/starburst diagnostics in the literature, we
found no evidence for correlations of _L_ [′]
HCN [/] _[L]_ HCO [′] [+] [ with AGN]
dominance, star formation activity, or dust temperature. The
elemental N/O ratio potentially moderately correlates with
_L_ [′]
HCN [/] _[L]_ HCO [′] [+] [, although p-values suggest that those quantities]
may be uncorrelated, with a probability of ∼10%.

**–**
_Spatially and spectrally resolved line ratios_ . We explored the
variation of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in] [the] [ppV] [space] [of] [each] [galaxy.]
As a result, _L_ HCN [′] [/] _[L]_ HCO [′] [+] [considerably varies from spaxel to]
spaxel, even within a galaxy. We found spatially and kinematically symmetric structures of high line ratio (the highest
10th percentile on a spaxel-by-spaxel basis) in some galaxies. Such structures are predominantly found in galaxies with
molecular outflows previously found by CO and/or OH line
observations.

**–** _Non-LTE_ _radiative_ _transfer_ _analysis_ . One-zone non-LTE
radiative transfer calculations were made to investigate
the excitation conditions and molecular abundances in the
gas phase in our sample galaxies. They revealed that
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [depends] [on] [many] [parameters,] [such] [as] [the]
HCN/HCO [+] abundance ratio, H 2 volume density, and electron abundances. Taking all factors into consideration, the
observed high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [(][>][1) in outflows and inflows are]
essentially caused by a high HCN/HCO [+] abundance ratio,
and this can be further enhanced by electrons.
**–** _Key_ _chemical_ _process_ _to_ _enhance_ _HCN_ _abundance_ . Chemistry induced by shocks characterizes the molecular abundances in outflows and inflows. As reported by previous studies, thermal and non-thermal release of HCN ice mostly contributes to the enhancement of HCN in the gas phase under high density conditions (∼10 [5] cm [−][3] ). In the moderatelydense gas, which accounts for a larger fraction of the total gas, the HCN abundance is mainly enhanced by a hightemperature gas-phase reaction: CN + H 2 → HCN + H. The


Article number, page 10 of 52



post-shock time of HCN enhancement is roughly comparable to the dynamical time of the outflow (∼10 [5] yr).


Finally, we emphasize the advantages of analyzing
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [in a spatially and spectrally resolved manner. Con-]
sidering that the mass of the regions influenced by outflows
and/or inflows is smaller than the total mass of the galaxy, spatial or spectral integration may make it difficult to distinguish
shocked regions from others. Our results imply that the spatially
and spectrally resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [helps] [identify] [the] [geome-]
try of outflows and inflows, at least in some cases, when the
shock velocity of the outflows is sufficiently high to heat the gas.
To develop line diagnostics for the characterization of physical
properties of U/LIRGs, further exploration of molecular compositions and more detailed modeling of the kinematic structure of
a galaxy should be investigated in future studies.


_Acknowledgements._ We thank the anonymous referee for a constructive report
that significantly contributed to the improvement of this paper. We thank Niklas
Falstad for valuable discussions and for the earlier work on CON-quest. YN
gratefully acknowledges support by JSPS KAKENHI grant No. JP23K13140,
JP18K13577, and NAOJ ALMA Scientific Research Grant No. 2017-06B. SA
and SK gratefully acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No 789410). SA and MG also acknowledge
support from Swedish Research Council grant 621-2011-4143. J.S.G. thanks
the University of Wisconsin College of Letters and Science for partial support of this research. E.G-A thanks the Spanish MICINN for support under
projects PID2019-105552RB-C41 and PID2022-137779OB-C41. KK acknowledges the support by JSPS KAKENHI Grant Number JP17H06130 and the
NAOJ ALMA Scientific Research Grant No. 2017-06B. M.I. is supported by
JSPS KAKENHI grant No. JP21K03632. CR acknowledges support from Fondecyt Regular grant 1230345 and ANID BASAL project FB210003. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00759.S
and ADS/JAO.ALMA#2018.1.01344.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ.

Y. Nishimura et al.: CON-quest


**Table 1.** Main properties of the sample galaxies.


ID Galaxy _z_ _D_ _L_ _L_ IR α AGN Merger CON Outflow Inflow
(Mpc) (10 [11] _L_ ⊙ ) stage
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10)
1 IRAS 17208−0014 0.0428 183 ± 12 25 ± 3 0.05 ± 0.03 d � i α

2 IRAS 09022−3615 0.0596 253 ± 17 18 ± 2 0.19 ± 0.06 d vi
3 IRAS 13120−5453 0.0311 135 ± 9 18 ± 2 0.04 ± 0.02 d ii, iii, vi, vii
4 IRAS F14378−3651 0.0682 295 ± 20 14 ± 2 0.05 ± 0.02 d vi, vii
5 IRAS F05189−2524 _[*]_ 0.0427 176 ± 12 13 ± 2 0.60 ± 0.07 d ii, vi, vii
6 IRAS F10565+2448 _[*]_ 0.0431 184 ± 12 11 ± 1 0.04 ± 0.01 d iv, vi, vii
7 IRAS 19542+1110 _[*]_ 0.0626 264 ± 18 10 ± 1 0.08 ± 0.04 N vi
8 ESO 148−IG002 _[*]_ 0.0446 185 ± 12 10 ± 1 0.19 ± 0.03 c
9 NGC 6240 _[*]_ 0.0243 106 ± 7 7 ± 1 0.11 ± 0.02 d iv, vi
10 IRAS F17138−1017 0.0173 77.3 ± 5.2 2.6 ± 0.3 0.07 ± 0.04 d
11 IRAS 17578−0400 0.0134 60.0 ± 4.1 2.3 ± 0.3 0.03 ± 0.02 b � β
12 ESO 173−G015 0.0100 32.7 ± 2.3 2.2 ± 0.3 0.03 ± 0.02 N
13 UGC 11763 _[*]_ 0.0633 265 ± 18 2.2 ± 0.5   - · · N

14 NGC 3110 0.0169 74.3 ± 5.0 2.0 ± 0.3 0.10 ± 0.06 a

15 IC 4734 0.0156 67.8 ± 4.5 1.9 ± 0.3 0.07 ± 0.02 N

16 NGC 5135 0.0137 52.6 ± 3.5 1.5 ± 0.2 0.24 ± 0.06 N

17 ESO 221−IG10 0.0105 59 ± 11 1.5 ± 0.6 0.07 ± 0.04 N

18 IC 5179 0.0113 47.3 ± 3.2 1.5 ± 0.2 0.10 ± 0.07 N

19 UGC 2982 0.0177 70.6 ± 4.7 1.4 ± 0.2 0.11 ± 0.08 d

20 NGC 2369 0.0108 44.6 ± 3.0 1.3 ± 0.2 0.10 ± 0.06 N

21 ESO 286−G035 0.0174 73.2 ± 4.9 1.3 ± 0.2 0.06 ± 0.04 a
22 ESO 320−G030 0.0103 36 ± 2.5 1.1 ± 0.2 0.03 ± 0.02 N � v γ
23 NGC 5734 0.0136 60.2 ± 4.0 1.1 ± 0.2 0.14 ± 0.07 a


**Notes.** [(] _[*]_ [)] Not included in the sample of Paper I. (1) Identification number used in this paper. (2) Galaxy name. (3) Redshift. (4) Luminosity
distance calculated from redshift following the same procedure as Sanders et al. (2003). (5) Infrared luminosity based on IRAS fluxes taken from
Sanders et al. (2003) and calculated with the same methods used by Sanders & Mirabel (1996). Only for UGC 11763 are fluxes taken from Sanders
et al. (1989). (6) Bolometric AGN fraction (α AGN = _L_ AGN / _L_ bol ) calculated from mid-infrared diagnostics by Díaz-Santos et al. (2017). See Sect. 2
for detail. (7) Merger stage visually determined by Stierwalt et al. (2013). N = nonmerger, a = pre-merger, b = early-stage merger, c = mid-stage
merger, and d = late-stage merger. (8) Presence of CON found by HCN-vib observations. Details are presented in Paper I. (9) Presence of molecular
outflow found by CO and/or OH observations. References are (i) García-Burillo et al. (2015); (ii) Fluetsch et al. (2019); (iii) Lutz et al. (2020); (iv)
Cicone et al. (2014); and (v) Pereira-Santaella et al. (2016) for CO observations and (vi) Veilleux et al. (2013) and (vii) González-Alfonso et al.
(2017) for OH observations. (10) Presence of molecular inflow found by CO and/or OH observations. References are (α) Veilleux et al. (2013)
and (β) Falstad et al. (2021) for OH observations and (γ) González-Alfonso et al. (2021) for CO and OH observations.


Article number, page 11 of 52

_A&A proofs:_ manuscript no. clean


**Table 2.** Parameters of ALMA observations and adopted kinematics for analyses.


ALMA observations Adopted kinematics
ID Galaxy Beam (PA) Resolution Sensitivity α [center] J2000 δ [center] J2000 PA v sys
( [′′] × [′′] ( [◦] )) (pc×pc) (mJy beam [−][1] ) (h:m:s) ( [◦] : [′] : [′′] ) ( [◦] ) (km s [−][1] )
1 IRAS 17208−0014 0.35 × 0.32 (74) 298 × 272 0.680 17:23:21.96 −00:17:00.9 105 12321
2 IRAS 09022−3615 0.33 × 0.28 (64) 382 × 324 0.145 09:04:12.71 −36:27:01.9 10 16847
3 IRAS 13120−5453 0.36 × 0.32 (18) 225 × 200 0.730 13:15:06.32 −55:09:22.8 95 9037
4 IRAS F14378−3651 0.29 × 0.26 (66) 388 × 347 0.194 14:40:59.01 −37:04:31.9 30 19143
5 IRAS F05189−2524 0.42 × 0.27 (81) 343 × 220 0.244 05:21:01.40 −25:21:45.3 90 12257
6 IRAS F10565+2448 0.33 × 0.22 (−1) 281 × 187 0.227 10:59:18.13 +24:32:34.5 90 12387
7 IRAS 19542+1110 0.34 × 0.29 (−53) 423 × 360 0.175 19:56:35.78 +11:19:05.0 45 17678
8 ESO 148−IG002 0.40 × 0.31 (31) 344 × 267 0.236 23:15:46.75 −59:03:15.5 0 12793
9 NGC 6240 0.32 × 0.26 (58) 161 × 130 0.281 16:52:58.89 +02:24:03.4 40 7129
10 IRAS F17138-1017 0.38 × 0.29 (−76) 139 × 106 0.576 17:16:35.81 −10:20:39.0 5 5113
11 IRAS 17578−0400 0.36 × 0.29 (−65) 102 × 82 0.512 18:00:31.84 −04:00:53.5 110 3981
12 ESO 173−G015 0.33 × 0.30 (−7) 51 × 47 0.434 13:27:23.77 −57:29:22.0 165 2963
13 UGC 11763 0.35 × 0.31 (51) 397 × 351 0.206 21:32:27.82 +10:08:19.2 - · · 17859
14 NGC 3110 0.40 × 0.27 (56) 142 × 96 0.384 10:04:02.09 −06:28:29.5 170 4973
15 IC 4734 0.38 × 0.29 (28) 126 × 96 0.525 18:38:25.70 −57:29:25.2 105 4606
16 NGC 5135 0.33 × 0.27 (85) 83 × 68 0.630 13:25:43.99 −29:49:60.0 15 4052
17 ESO 221−IG10 0.34 × 0.31 (−57) 95 × 87 0.582 13:50:56.94 −49:03:19.2 40 3113
18 IC 5179 0.28 × 0.23 (68) 63 × 52 0.391 22:16:09.13 −36:50:37.0 50 3350
19 UGC 2982 0.36 × 0.30 (126) 117 × 98 0.359 04:12:22.67 +05:32:49.1 - · · 5200
20 NGC 2369 0.28 × 0.25 (7) 59 × 53 0.511 07:16:37.68 −62:20:36.6 50 3187
21 ESO 286−G035 0.29 × 0.26 (52) 101 × 90 0.409 21:04:11.12 −43:35:35.8 20 5129
22 ESO 320−G030 0.34 × 0.29 (69) 62 × 53 0.453 11:53:11.72 −39:07:49.1 130 3049
23 NGC 5734 0.31 × 0.30 (35) 89 × 86 0.417 14:45:09.04 −20:52:13.5 40 4029


**Notes.** “Beam” refers to the synthesized beam obtained after cleaning with natural weighting. “Resolution” is the projected physical size corresponding to the synthesized beam at the distance of the galaxy. “Sensitivity” is 1σ rms per beam in 20 km s [−][1] velocity channels calculated from
flux-free parts. The adopted galaxy kinematics were roughly estimated from the velocity field seen outside the most nuclear region. The systemic
velocity v sys is given in radio convention with respect to the LSRK.


Article number, page 12 of 52

Y. Nishimura et al.: CON-quest


**Table 3.** Results of the HCN 3–2 and HCO [+] 3–2 line measurements: resolved and global line luminosities.


Resolved Global
ID Galaxy Range _L_ HCN [′] _L_ HCO [′] [+] _L_ HCN [′] _L_ HCO [′] [+]
(km s [−][1] ) (10 [7] K km s [−][1] pc [2] ) (10 [7] K km s [−][1] pc [2] ) (10 [7] K km s [−][1] pc [2] ) (10 [7] K km s [−][1] pc [2] )
1 IRAS 17208−0014 ±500 20.5 ± 0.1 11.8 ± 0.1 94.5 ± 1.2 64.6 ± 1.2

2 IRAS 09022−3615 ±500 5.12 ± 0.04 6.46 ± 0.05 26.0 ± 0.5 46.9 ± 0.5

3 IRAS 13120−5453 ±500 8.52 ± 0.07 3.19 ± 0.07 77.2 ± 0.7 45.2 ± 0.7

4 IRAS F14378−3651 ±250 6.25 ± 0.06 4.72 ± 0.06 29.4 ± 0.6 25.8 ± 0.6

5 IRAS F05189−2524 ±250 7.44 ± 0.03 4.56 ± 0.03 20.6 ± 0.3 13.4 ± 0.3

6 IRAS F10565+2448 ±250 1.78 ± 0.03 1.35 ± 0.03 19.1 ± 0.3 21.8 ± 0.3

7 IRAS 19542+1110 ±300 9.39 ± 0.05 5.25 ± 0.05 28.3 ± 0.5 15.5 ± 0.5

8 ESO 148−IG002 ±200 0.87 ± 0.03 1.95 ± 0.03 3.0 ± 0.3 7.8 ± 0.3

9 NGC 6240 ±500 0.90 ± 0.02 1.30 ± 0.02 21.1 ± 0.2 30.4 ± 0.2

10 IRAS F17138-1017 ±150 0.06 ± 0.01 0.10 ± 0.01 7.2 ± 0.1 1.2 ± 0.1

11 IRAS 17578−0400 _[a]_ ±250 3.613 ± 0.006 2.697 ± 0.007 13.82 ± 0.07 10.74 ± 0.07

12 ESO 173−G015 ±250 0.297 ± 0.002 0.262 ± 0.002 3.38 ± 0.02 3.91 ± 0.02

13 UGC 11763 ±200 0.15 ± 0.05 0.21 ± 0.04 < 1.5 1.4 ± 0.4

14 NGC 3110 ±200 0.056 ± 0.006 0.036 ± 0.007 1.15 ± 0.07 1.10 ± 0.08

15 IC 4734 ±200 0.394 ± 0.008 0.367 ± 0.009 5.79 ± 0.08 5.45 ± 0.09

16 NGC 5135 ±150 0.048 ± 0.005 0.047 ± 0.005 1.00 ± 0.05 0.91 ± 0.05

17 ESO 221−IG10 ±150 0.035 ± 0.006 0.046 ± 0.006 0.80 ± 0.06 1.23 ± 0.06

18 IC 5179 ±200 0.015 ± 0.003 0.026 ± 0.003 0.37 ± 0.03 0.44 ± 0.03

19 UGC 2982 ±150 < 0.014 < 0.016 < 0.14 < 0.16

20 NGC 2369 ±300 0.111 ± 0.004 0.074 ± 0.005 1.27 ± 0.04 1.12 ± 0.04

21 ESO 286−G035 ±200 0.033 ± 0.007 0.050 ± 0.008 0.49 ± 0.07 0.84 ± 0.08

22 ESO 320−G030 ±300 0.798 ± 0.002 0.341 ± 0.002 5.67 ± 0.02 2.52 ± 0.02

23 NGC 5734 ±150 0.032 ± 0.004 < 0.013 0.31 ± 0.04 < 0.13


**Notes.** The spectra were extracted from the beam-sized aperture and the elliptical aperture of 10 × 10 times the beam for the resolved and global
luminosity, respectively, and both were centered at the position listed in Table 2. Line flux densities were integrated over the range with respect to
the systemic velocity given in Table 2. Uncertainties and upper limits correspond to 1σ and 3σ statistical errors, respectively.
( _a_ ) Continuum subtraction was done after spectral extraction assuming continuum levels of 0.02 Jy and 0.07 Jy for the resolved and global spectra,
respectively.


Article number, page 13 of 52

_A&A proofs:_ manuscript no. clean


**Table 4.** Measured _L_ HCN [′] [/] _[L]_ HCO [′] [+] [for the resolved and global apertures.]


ID Galaxy Resolved Global
1 IRAS 17208−0014 1.738 ± 0.019 1.464 ± 0.032

2 IRAS 09022−3615 0.793 ± 0.009 0.555 ± 0.011

3 IRAS 13120−5453 2.671 ± 0.064 1.706 ± 0.031

4 IRAS F14378−3651 1.323 ± 0.022 1.140 ± 0.035

5 IRAS F05189−2524 1.630 ± 0.012 1.534 ± 0.038

6 IRAS F10565+2448 1.320 ± 0.035 0.878 ± 0.017

7 IRAS 19542+1110 1.789 ± 0.018 1.825 ± 0.063

8 ESO 148−IG002 0.445 ± 0.015 0.387 ± 0.035

9 NGC 6240 0.691 ± 0.015 0.693 ± 0.007

10 IRAS F17138-1017 0.629 ± 0.123 0.587 ± 0.093

11 IRAS 17578−0400 _[a]_ 1.340 ± 0.004 1.283 ± 0.011

12 ESO 173−G015 1.132 ± 0.010 0.865 ± 0.006

13 UGC 11763 0.728 ± 0.283 < 1.1

14 NGC 3110 1.490 ± 0.330 1.044 ± 0.093

15 IC 4734 1.076 ± 0.033 1.063 ± 0.022

16 NGC 5135 1.028 ± 0.147 1.100 ± 0.083

17 ESO 221−IG10 0.771 ± 0.164 0.651 ± 0.057

18 IC 5179 0.564 ± 0.127 0.842 ± 0.087

19 UGC 2982  - · ·  - · ·

20 NGC 2369 1.489 ± 0.110 1.133 ± 0.057

21 ESO 286−G035 0.666 ± 0.178 0.587 ± 0.098

22 ESO 320−G030 2.344 ± 0.018 2.254 ± 0.023

23 NGC 5734  - 2.5  - 2.4
average (excl. 13, 19, 23) 1.216 1.080


**Notes.** [(] _[a]_ [)] Continuum was not subtracted.


**Table 5.** Spearman rank coefficients and p-values.


Quantities ρ p-value
Global _L_ HCN [′] [/] _[L]_ HCO [′] [+] [vs.]
α AGN −0.17 [+] − [0] 0 [.] . [24] 23 0.38 [+] − [0] 0 [.] . [41] 31
log( _L_ AGN [bol] [/][erg s] [−][1] [)] +0.00 [+] − [0] 0 [.] . [27] 26 0.44 [+] − [0] 0 [.] . [38] 34
log( _L_ IR / _L_ ⊙ ) +0.11 [+] − [0] 0 [.] . [25] 26 0.42 [+] − [0] 0 [.] . [39] 33
log(SFR/ _M_ ⊙ yr [−][1] ) +0.09 [+] − [0] 0 [.] . [24] 26 0.44 [+] − [0] 0 [.] . [38] 33
_S_ 60 / _S_ 100 +0.02 [+] − [0] 0 [.] . [25] 25 0.47 [+] − [0] 0 [.] . [36] 34

[N ii] 122 /[O iii] 88 +0.50 [+] − [0] 0 [.] . [25] 32 0.10 [+] − [0] 0 [.] . [42] 09
Resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [vs.]
α AGN −0.22 [+] − [0] 0 [.] . [23] 22 0.31 [+] − [0] 0 [.] . [44] 26
log( _L_ AGN [bol] [/][erg s] [−][1] [)] +0.05 [+] − [0] 0 [.] . [24] 25 0.47 [+] − [0] 0 [.] . [36] 34
log( _L_ IR / _L_ ⊙ ) +0.23 [+] − [0] 0 [.] . [23] 25 0.29 [+] − [0] 0 [.] . [45] 25
log(SFR/ _M_ ⊙ yr [−][1] ) +0.23 [+] − [0] 0 [.] . [22] 25 0.29 [+] − [0] 0 [.] . [45] 25
_S_ 60 / _S_ 100 +0.07 [+] − [0] 0 [.] . [24] 24 0.47 [+] − [0] 0 [.] . [35] 34

[N ii] 122 /[O iii] 88 +0.38 [+] − [0] 0 [.] . [26] 32 0.21 [+] − [0] 0 [.] . [46] 19


**Notes.** We performed Spearman rank correlation analyses using the
Monte Carlo perturbation plus bootstrapping method as implemented
by `pymccorrelation` (Privon et al. 2020, see Sect. 5.2 for detail). Correlation coefficients ρ and p-values are the median and range of the 16
and 84 percentiles. Corresponding plots are shown in Figs. 2 and 3.


Article number, page 14 of 52

Y. Nishimura et al.: CON-quest


**Table 6.** _L_ HCN [′] [/] _[L]_ HCO [′] [+] [on a pixel-by-pixel basis and on a spaxel-by-spaxel basis.]


Spectrally integrated (pixel-by-pixel basis) Spectrally resolved (spaxel-by-spaxel basis)
ID Galaxy Mean 25th–50th–75th (IQR) 90th Mean 25th–50th–75th (IQR) 90th
1 IRAS 17208−0014 1.253 1.012–1.224–1.513 (0.501) 1.689 1.517 1.147–1.447–1.812 (0.664) 2.173
2 IRAS 09022−3615 0.561 0.433–0.539–0.648 (0.215) 0.788 0.641 0.482–0.607–0.754 (0.272) 0.928
3 IRAS 13120−5453 1.395 1.056–1.301–1.609 (0.553) 2.109 1.590 1.046–1.440–2.024 (0.977) 2.560
4 IRAS F14378−365 1.129 1.004–1.154–1.255 (0.251) 1.355 1.169 0.980–1.142–1.305 (0.325) 1.507
5 IRAS F05189−252 1.452 1.246–1.524–1.633 (0.387) 1.752 1.589 1.409–1.547–1.717 (0.308) 2.022
6 IRAS F10565+244 0.801 0.667–0.792–0.918 (0.251) 1.068 0.871 0.660–0.825–1.023 (0.364) 1.258
7 IRAS 19542+1110 1.718 1.532–1.736–1.873 (0.342) 2.127 1.724 1.544–1.697–1.848 (0.304) 2.124
8 ESO 148−IG002 0.402 0.345–0.394–0.437 (0.093) 0.510 0.442 0.377–0.424–0.478 (0.101) 0.544
9 NGC 6240 0.674 0.613–0.679–0.736 (0.123) 0.792 0.748 0.635–0.736–0.835 (0.200) 0.954
10 IRAS F17138-101 0.767 0.591–0.698–0.886 (0.295) 1.076 0.815 0.675–0.802–0.939 (0.264) 1.060
11 IRAS 17578−0400 _[a]_ 1.208 1.038–1.215–1.336 (0.298) 1.514 1.237 1.081–1.238–1.383 (0.302) 1.513
12 ESO 173−G015 0.792 0.685–0.783–0.884 (0.199) 1.004 0.858 0.694–0.830–0.979 (0.285) 1.143
13 UGC 11763  - · ·  - · ·  - · ·  - · ·  - · ·  - · ·
14 NGC 3110 1.289 1.032–1.176–1.538 (0.506) 1.802 1.147 0.932–1.090–1.324 (0.392) 1.572
15 IC 4734 1.053 0.957–1.046–1.121 (0.164) 1.222 1.042 0.905–1.024–1.159 (0.254) 1.319
16 NGC 5135 1.237 1.029–1.189–1.405 (0.376) 1.677 1.105 0.850–1.038–1.280 (0.430) 1.594
17 ESO 221−IG10 0.792 0.656–0.772–0.906 (0.250) 1.034 0.755 0.596–0.715–0.886 (0.290) 1.054
18 IC 5179 0.985 0.804–0.980–1.145 (0.341) 1.357 0.887 0.698–0.865–1.054 (0.357) 1.227
19 UGC 2982  - · ·  - · ·  - · ·  - · ·  - · ·  - · ·
20 NGC 2369 1.100 0.876–1.049–1.294 (0.418) 1.517 1.133 0.841–1.055–1.343 (0.502) 1.663
21 ESO 286−G035 0.778 0.680–0.755–0.854 (0.174) 0.960 0.790 0.638–0.758–0.922 (0.284) 1.072
22 ESO 320−G030 2.068 1.647–2.073–2.336 (0.689) 2.791 2.156 1.735–2.064–2.450 (0.716) 2.998
23 NGC 5734  - · ·  - · ·  - · ·  - · ·  - · ·  - · ·
average (excl. 13, 19, 23) 1.073 0.895–1.054–1.216 (0.321) 1.407 1.111 0.896–1.067–1.276 (0.380) 1.514


**Notes.** We examined pixels and spaxels within the global aperture (see Sect. 4.1) and within the velocity range listed in Table 3. For pixel-by-pixel
analysis, we first performed a spectral integration followed by a 3σ threshold clipping. Each pixel has a size of 0.05 [′′] × 0.05 [′′] . In the spaxelby-spaxel analysis, we focused solely on spaxels where HCN and HCO [+] were both detected with >3σ significance. Each spaxel has a size of
0.05 [′′] × 0.05 [′′] × 20 km s [−][1] . We note that pixels and spaxels within a beam are correlated. IQR stands for the interquartile range.
( _a_ ) Continuum was not subtracted.


Article number, page 15 of 52

_A&A proofs:_ manuscript no. clean



**References**


Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2015a, A&A, 574, A85
Aalto, S., Martín, S., Costagliola, F., et al. 2015b, A&A, 584, A42
Aalto, S., Muller, S., König, S., et al. 2019, A&A, 627, A147
Aalto, S., Spaans, M., Wiedner, M. C., & Hüttemeister, S. 2007, A&A, 464, 193
Astropy Collaboration, Price-Whelan, A. M., Sip˝ocz, B. M., et al. 2018, AJ, 156,
123
Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558,
A33
Bachiller, R. & Pérez Gutiérrez, M. 1997, ApJ, 487, L93
Bachiller, R., Pérez Gutiérrez, M., Kumar, M. S. N., & Tafalla, M. 2001, A&A,
372, 899
Barcos-Muñoz, L., Aalto, S., Thompson, T. A., et al. 2018, ApJ, 853, L28
Bayet, E., Viti, S., Williams, D. A., & Rawlings, J. M. C. 2008, ApJ, 676, 978
Braine, J., Shimajiri, Y., André, P., et al. 2017, A&A, 597, A44
Burkhardt, A. M., Shingledecker, C. N., Le Gal, R., et al. 2019, ApJ, 881, 32
Bussmann, R. S., Narayanan, D., Shirley, Y. L., et al. 2008, ApJ, 681, L73
Butterworth, J., Holdship, J., Viti, S., & García-Burillo, S. 2022, A&A, 667,
A131
CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501
Ceccarelli, C., Hily-Blant, P., Montmerle, T., et al. 2011, ApJ, 740, L4
Cicone, C., Maiolino, R., Aalto, S., Muller, S., & Feruglio, C. 2020, A&A, 633,
A163
Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21
Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018, ApJ, 863, 143
Costagliola, F., Aalto, S., Rodriguez, M. I., et al. 2011, A&A, 528, A30
Costagliola, F., Aalto, S., Sakamoto, K., et al. 2013, A&A, 556, A66
Curran, P. A. 2014, Monte Carlo error analyses of Spearman’s rank test
Denis-Alpizar, O., Stoecklin, T., Dutrey, A., & Guilloteau, S. 2020, MNRAS,
497, 4276
Díaz-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32
Dumouchel, F., Faure, A., & Lique, F. 2010, MNRAS, 406, 2488
Falstad, N., Aalto, S., König, S., et al. 2021, A&A, 649, A105
Falstad, N., Hallqvist, F., Aalto, S., et al. 2019, A&A, 623, A29
Faure, A. & Tennyson, J. 2001, MNRAS, 325, 443
Faure, A., Varambhia, H. N., Stoecklin, T., & Tennyson, J. 2007, MNRAS, 382,
840
Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586
Gao, Y. & Solomon, P. M. 2004, ApJS, 152, 63
García-Burillo, S., Combes, F., Usero, A., et al. 2015, A&A, 580, A35
García-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125
García-Burillo, S., Viti, S., Combes, F., et al. 2017, A&A, 608, A56
Goldreich, P. & Kwan, J. 1974, ApJ, 189, 441
Goldsmith, P. F. & Kauffmann, J. 2017, ApJ, 841, 25
González-Alfonso, E., Fischer, J., Spoon, H. W. W., et al. 2017, ApJ, 836, 11
González-Alfonso, E., Pereira-Santaella, M., Fischer, J., et al. 2021, A&A, 645,
A49
Gorski, M. D., Aalto, S., König, S., et al. 2023, A&A, 670, A70
Graciá-Carpio, J., García-Burillo, S., Planesas, P., Fuente, A., & Usero, A. 2008,
A&A, 479, 703
Hagiwara, Y., Baan, W. A., & Klöckner, H.-R. 2011, AJ, 142, 17
Harada, N., Herbst, E., & Wakelam, V. 2010, ApJ, 721, 1570
Harada, N., Martín, S., Mangum, J. G., et al. 2021, ApJ, 923, 24
Harada, N., Nishimura, Y., Watanabe, Y., et al. 2019, ApJ, 871, 238
Harada, N., Sakamoto, K., Martín, S., et al. 2018, ApJ, 855, 49
Harada, N., Thompson, T. A., & Herbst, E. 2013, ApJ, 765, 108
Helou, G., Khan, I. R., Malek, L., & Boehmer, L. 1988, ApJS, 68, 151
Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 94
Holdship, J., Mangum, J. G., Viti, S., et al. 2022, ApJ, 931, 89
Holdship, J., Viti, S., Jiménez-Serra, I., Makrymallis, A., & Priestley, F. 2017,
AJ, 154, 38
Hopkins, P. F., Somerville, R. S., Hernquist, L., et al. 2006, ApJ, 652, 864
Imanishi, M., Baba, S., Nakanishi, K., & Izumi, T. 2023, ApJ, 950, 75
Imanishi, M. & Nakanishi, K. 2013, AJ, 146, 91
Imanishi, M., Nakanishi, K., & Izumi, T. 2019, ApJS, 241, 19
Imanishi, M., Nakanishi, K., Tamura, Y., & Peng, C.-H. 2009, AJ, 137, 3581
Israel, F. P. 2023, A&A, 671, A59
Izumi, T., Kohno, K., Aalto, S., et al. 2016, ApJ, 818, 42
Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2019, ApJ, 880, 127
Jiménez-Serra, I., Caselli, P., Martín-Pintado, J., & Hartquist, T. W. 2008, A&A,
482, 549
Juneau, S., Narayanan, D. T., Moustakas, J., et al. 2009, ApJ, 707, 1217
Kauffmann, J., Goldsmith, P. F., Melnick, G., et al. 2017, A&A, 605, L5
Kawana, Y., Saito, T., Okumura, S. K., et al. 2022, ApJ, 929, 100
Kennicutt, Robert C., J. 1998, ApJ, 498, 541
Kohno, K., Matsushita, S., Vila-Vilaró, B., et al. 2001, in Astronomical Society
of the Pacific Conference Series, Vol. 249, The Central Kiloparsec of Starbursts and AGN: The La Palma Connection, ed. J. H. Knapen, J. E. Beckman,
I. Shlosman, & T. J. Mahoney, 672


Article number, page 16 of 52



Komossa, S., Burwitz, V., Hasinger, G., et al. 2003, ApJ, 582, L15
König, S., Aalto, S., Muller, S., et al. 2018, A&A, 615, A122
Krips, M., Neri, R., García-Burillo, S., et al. 2008, ApJ, 677, 262
Krumholz, M. R. & Thompson, T. A. 2007, ApJ, 669, 289
Laurent, O., Mirabel, I. F., Charmandaris, V., et al. 2000, A&A, 359, 887
Lepp, S. & Dalgarno, A. 1996, A&A, 306, L21
Lindberg, J. E., Aalto, S., Muller, S., et al. 2016, A&A, 587, A15
Lutz, D., Genzel, R., Sternberg, A., et al. 1996, A&A, 315, L137
Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134
Maloney, P. R., Hollenbach, D. J., & Tielens, A. G. G. M. 1996, ApJ, 466, 561
Martín, S., Aalto, S., Sakamoto, K., et al. 2016, A&A, 590, A25
Martín, S., Kohno, K., Izumi, T., et al. 2015, A&A, 573, A116
Meijerink, R., Kristensen, L. E., Weiß, A., et al. 2013, ApJ, 762, L16
Meijerink, R. & Spaans, M. 2005, A&A, 436, 397
Meijerink, R., Spaans, M., & Israel, F. P. 2007, A&A, 461, 793
Montoya Arroyave, I., Cicone, C., Makroleivaditi, E., et al. 2023, arXiv e-prints,
arXiv:2302.06629
Narayanan, D., Cox, T. J., Shirley, Y., et al. 2008, ApJ, 684, 996
Nishimura, Y., Shimonishi, T., Watanabe, Y., et al. 2016a, ApJ, 829, 94
Nishimura, Y., Shimonishi, T., Watanabe, Y., et al. 2016b, ApJ, 818, 161
Nishimura, Y., Watanabe, Y., Harada, N., et al. 2017, ApJ, 848, 17
Oteo, I., Zhang, Z. Y., Yang, C., et al. 2017, ApJ, 850, 170
Pereira-Santaella, M., Colina, L., García-Burillo, S., et al. 2016, A&A, 594, A81
Pereira-Santaella, M., Colina, L., García-Burillo, S., et al. 2021, A&A, 651, A42
Pereira-Santaella, M., Rigopoulou, D., Farrah, D., Lebouteiller, V., & Li, J. 2017,
MNRAS, 470, 1218
Pérez-Torres, M., Mattila, S., Alonso-Herrero, A., Aalto, S., & Efstathiou, A.
2021, A&A Rev., 29, 2
Pety, J., Guzmán, V. V., Orkisz, J. H., et al. 2017, A&A, 599, A98
Privon, G. C., Aalto, S., Falstad, N., et al. 2017, ApJ, 835, 213
Privon, G. C., Herrero-Illana, R., Evans, A. S., et al. 2015, ApJ, 814, 39
Privon, G. C., Ricci, C., Aalto, S., et al. 2020, ApJ, 893, 149
Ricci, C., Privon, G. C., Pfeifle, R. W., et al. 2021, MNRAS, 506, 5935
Romano, M., Cassata, P., Morselli, L., et al. 2021, A&A, 653, A111
Saito, T., Iono, D., Ueda, J., et al. 2018, MNRAS, 475, L52
Sakamoto, K., Aalto, S., Costagliola, F., et al. 2013, ApJ, 764, 42
Sakamoto, K., Aalto, S., Evans, A. S., Wiedner, M. C., & Wilner, D. J. 2010,
ApJ, 725, L228
Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003,
AJ, 126, 1607
Sanders, D. B. & Mirabel, I. F. 1996, ARA&A, 34, 749
Sanders, D. B., Phinney, E. S., Neugebauer, G., Soifer, B. T., & Matthews, K.
1989, ApJ, 347, 29
Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325, 74
Schmidt, M. 1959, ApJ, 129, 243
Shirley, Y. L. 2015, PASP, 127, 299
Singh, J. 2021, MNRAS, 504, 1531
Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677
Stierwalt, S., Armus, L., Surace, J. A., et al. 2013, ApJS, 206, 1
Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJ, 733, L16
Tan, Q.-H., Gao, Y., Zhang, Z.-Y., et al. 2018, ApJ, 860, 165
Tielens, A. G. G. M. & Hollenbach, D. 1985, ApJ, 291, 722
Treister, E., Messias, H., Privon, G. C., et al. 2020, ApJ, 890, 149
van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck,
E. F. 2007, A&A, 468, 627
Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27
Veilleux, S., Rupke, D. S. N., Kim, D. C., et al. 2009, ApJS, 182, 628
Vincenzo, F., Belfiore, F., Maiolino, R., Matteucci, F., & Ventura, P. 2016, MNRAS, 458, 3466
Viti, S., García-Burillo, S., Fuente, A., et al. 2014, A&A, 570, A28
Yamada, M., Wada, K., & Tomisaka, K. 2007, ApJ, 671, 73
Yamada, S., Ueda, Y., Tanimoto, A., et al. 2019, ApJ, 876, 96
Yang, C., Aalto, S., König, S., et al. 2023, arXiv e-prints, arXiv:2307.07641
Zhang, Z.-Y., Gao, Y., Henkel, C., et al. 2014, ApJ, 784, L31


1 Department of Astronomy, The University of Tokyo, 7-3-1, Hongo,
Bunkyo, Tokyo 113-0033, Japan
e-mail: `nishimura@astron.s.u-tokyo.ac.jp`
2 Institute of Astronomy, The University of Tokyo, 2-21-1, Osawa,
Mitaka, Tokyo 181-0015, Japan
3 National Astronomical Observatory of Japan, 2-21-1, Osawa, Mitaka, Tokyo 181-8588, Japan
4 Department of Space, Earth and Environment, Onsala Space Observatory, Chalmers University of Technology, SE-439 92 Onsala,
Sweden
5 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903, USA

Y. Nishimura et al.: CON-quest





10 [12]


10 [11]





10 [12]


10 [11]































**Fig.** **1.** _L_ IR as a function of ( _left_ ) global _L_ HCN [′] [and] [(] _[right]_ [)] [global] _[L]_ HCO [′] [+] [.] [In] [both] [panels,] [the] [numbers] [indicate] [the] [galaxy] [ID] [as] [defined] [in] [Table]
1. Small yellow dots, crosses, and open circles indicate the presence of CONs, outflows, and inflows, respectively. The solid lines are the fitting
results: log _L_ IR = 0.53 log _L_ HCN [′] [+][ 7][.][5 and log] _[ L]_ [IR] [=][ 0][.][61 log] _[ L]_ HCO [′] [+] [ +][ 6][.][9. As reference, the dashed lines are the best-fit relations taken from Juneau]
et al. (2009).



6 Observatoire de Paris, LERMA, Collège de France, CNRS, PSL
University, Sorbonne Université, Paris, France
7 Institute of Astrophysics, Foundation for Research and TechnologyHellas (FORTH), Heraklion, 70013, Greece
8 School of Sciences, European University Cyprus, Diogenes street,
Engomi, 1516 Nicosia, Cyprus
9 Department of Astronomy, University of Wisconsin-Madison, 5534
Sterling, 475 North Charter Street, Madison WI 53706, USA
10 Department of Physics and Astronomy, Macalester College, 1600
Grand Abe, St. Paul, MN 55105 USA
11 Observatorio Astronómico Nacional (OAN-IGN)-Observatorio de
Madrid, Alfonso XII, 3, 28014-Madrid, Spain
12 Universidad de Alcalá, Departamento de Física y Matemáticas,
Campus Universitario, E-28871 Alcalá de Henares, Madrid, Spain


13 DTU-Space, National Space Institute, Technical University of Denmark, Elektrovej 327, DK-2800 Kgs. Lyngby, Denmark
14 Cosmic Dawn Center (DAWN), DTU-Space, Technical University
of Denmark, Elektrovej 327, DK-2800 Kgs. Lyngby; Niels Bohr Institute, University of Copenhagen, Juliane Maries Vej 30, DK-2100
Copenhagen
15 Astronomical Science Program, Graduate Institute for Advanced
Studies, SOKENDAI, 2-21-1 Osawa, Mitaka, Tokyo 181-1855,
Japan
16 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69,
53121, Bonn, Germany
17 Astron. Dept., King Abdulaziz University, P.O. Box 80203, 21589
Jeddah, Saudi Arabia
18 Steward Observatory, University of Arizona, 933 N. Cherry Ave.,
Tucson, AZ 85721, USA
19 European Southern Observatory, Alonso de C ordova 3107, Vitacura
763 0355, Santiago, Chile
20 Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura 763
0355, Santiago, Chile
21 Department of Astronomy, University of Florida, P.O. Box 112055,
Gainesville, FL 32611, USA



22 Department of Astronomy, University of Virginia, 530 McCormick
Road, Charlottesville, VA 22904, USA
23 Núcleo de Astronomía de la Facultad de Ingeniería, Universidad
Diego Portales, Av. Ejército Libertador 441, Santiago, Chile
24 Kavli Institute for Astronomy and Astrophysics, Peking University,
Beijing 100871, China
25 George Mason University, Department of Physics & Astronomy, MS
3F3, 4400 University Drive, Fairfax, VA 22030, USA
26 Institut de Radioastronomie Millimétrique (IRAM), 300 Rue de la
Piscine, F-38400 Saint-Martin-d’Hères, France
27 Leiden Observatory, Leiden University, PO Box 9513, 2300 RA Leiden, The Netherlands
28 Department of Physics and Astronomy, University College London,
Gower Street, London WC1E 6BT, UK


Article number, page 17 of 52

2.5


2.0


1.5


1.0


0.5


0.0


2.5


2.0


1.5


1.0


0.5


0.0



10 [1] 10 [2]

SFR (M yr [1] )







_A&A proofs:_ manuscript no. clean


2.5





0.6 0.8 1.0 1.2

S 60 /S 100











2.5


2.0


1.5


1.0


0.5


0.0


2.5


2.0


1.5


1.0


0.5

















































10 [2] 10 [1] 10 [0]


AGN



2.0


1.5


1.0


0.5


0.0


2.5


2.0


1.5


1.0


0.5


0.0



10 [43] 10 [44] 10 [45]

L AGN [bol] [ (erg s] [1] [)]



10 [11] 10 [12]


L IR (L )





























































0.0

0.0 0.5 1.0

[NII] 122 /[OIII] 88



**Fig. 2.** Comparison of global _L_ HCN [′] [/] _[L]_ HCO [′] [+] [with (] _[top, from left to right]_ [) AGN fraction, bolometric AGN luminosity, infrared luminosity, (] _[bottom]_ [)]
star formation rate, IRAS 25 µm/60 µm flux density ratio, and the [N ii] 122 /[O iii] 88 line ratio. In all panels, the numbers refer to IDs as defined
in Table 1. Symbols are as in Fig. 1. Uncertainties are 1σ. For the [N ii] 122 /[O iii] 88 line ratios, uncertainties are not available. Corresponding
Spearman rank coefficients and p-values are listed in Table 5.


Article number, page 18 of 52

3.0


2.5


2.0


1.5


1.0


0.5


0.0


3.0


2.5


2.0


1.5


1.0


0.5


0.0



10 [1] 10 [2]







Y. Nishimura et al.: CON-quest


3.0



0.6 0.8 1.0 1.2

S 60 /S 100















3.0


2.5


2.0


1.5


1.0


0.5


0.0


3.0


2.5


2.0


1.5


1.0


0.5





















































10 [2] 10 [1] 10 [0]


AGN



2.5


2.0


1.5


1.0


0.5


0.0


3.0


2.5


2.0


1.5


1.0


0.5


0.0



10 [43] 10 [44] 10 [45]

L AGN [bol] [ (erg s] [1] [)]



10 [11] 10 [12]


L IR (L )



















































0.0

0.0 0.5 1.0

[NII] 122 /[OIII] 88


Article number, page 19 of 52



SFR (M yr [1] )


**Fig. 3.** Same as Fig. 2 but for resolved _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.]

_A&A proofs:_ manuscript no. clean



4.0


3.5


3.0


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

|Col1|Col2|90th<br>75th<br>50th IQR<br>mean<br>25th|
|---|---|---|
|IRAS 17208-0014<br>IRAS 09022-3615<br>IRAS 131|20-5453<br>IRAS F14378-3651<br>IRAS F05189-2524<br>IRAS F10565+2448<br>IRAS 19542+1110<br>ESO 148-IG002<br>NGC 6240<br>IRAS F17138-1017<br>IRAS 17578-0400<br>ESO 173-G015<br>NGC 3110<br>IC 4734<br>NGC 5135<br>ESO 221-IG10<br>IC 5179<br>NGC 2369<br>ESO 286-G035<br>ESO 32|0-G030|
|mean<br>90th<br>75th<br>50th<br>25th<br>IQR|mean<br>90th<br>75th<br>50th<br>25th<br>IQR|mean<br>90th<br>75th<br>50th<br>25th<br>IQR|



**Fig. 4.** Violin plots for _L_ HCN [′] [/] _[L]_ HCO [′] [+] [on a pixel-by-pixel basis (] _[top]_ [) and on a spaxel-by-spaxel basis (] _[bottom]_ [). Mean, 50th, and 90th percentiles are]
denoted by a cross, dot, and a short horizontal bar, respectively, with the IQR displayed as a white bar. Corresponding numerical values are listed
in Table 6. See Sect. 5.3 for details.


Article number, page 20 of 52

IRAS 17208-0014



Y. Nishimura et al.: CON-quest


IRAS 13120-5453



400


200


0


200


400



0.5


0.0


0.5


400


200


0


200


400


400


200


0


200


400



1.0


0.5


0.0


0.5


1.0


400


200


0


200


400


400


200


0


200


400



100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)



100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)



400


200


0


200


400



1.0



1.0



1.0
0.5

0.0

0.5

1.0



1.0 2.0 3.0

L HCN /L HCO [+]



1.0
0.5

0.0

0.5

1.0



0.5



0.0



0.0



0.5


0.5



0.0



0.5



0.5



0.5



IRAS 17208-0014



IRAS 13120-5453



400


200


0


200


400



0.5


0.5



400


200


0


200


400



1.0
0.5

0.0

0.5

1.0



0.0



0.0



0.5



0.5



1.0 2.0 3.0

L HCN /L HCO [+]



**Fig. 5.** Visualizations of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [exceeding the 90th percentile (see Table 6) with projections onto the RA-Dec, RA-velocity, and Dec-velocity]
planes. The two 3D plots represent the same data from different angles. Displayed galaxies are IRAS 17208-0014 and IRAS 13120-5453.


Article number, page 21 of 52

IRAS 09022-3615



_A&A proofs:_ manuscript no. clean


IRAS F14378-3651



1.0


0.5


0.0


0.5


1.0



100 pc



0.5


0.0


0.5


400


200


0


200


400


400


200


0


200


400


1.0


0.5


0.0


0.5


1.0



100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)


100 pc



1.0

0.5

0.0

0.5



0.5



400


200


0


200


400


1.0



400


200


0


200


400


400


200


0


200


400



0.5



0.0



1.0 0.5 0.0 0.5 1.0

(arcsec)



0.0



0.0



0.5


0.5



0.5



0.5



1.0



1.0



IRAS 09022-3615



400


200


0


200


400



IRAS F14378-3651



400


200


0


200


400


1.0

0.5

0.0

0.5



1.0

0.5

0.0

0.5



0.5


0.5



100 pc



1.0 0.5 0.0 0.5 1.0

(arcsec)



400


200


0


200


400



400


200


0


200


400



0.5



0.0



0.0



0.5



1.0



1.0



100 pc



1.0 2.0 3.0

L HCN /L HCO [+]


IRAS F10565+2448



1.0 0.5 0.0 0.5 1.0

(arcsec)



0.5



400


200


0


200


400



0.5


0.0


0.5


400


200


0


200


400


400


200


0


200


400



100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)



1.0



1.0



1.0
0.5

0.0

0.5

1.0



1.0 2.0 3.0

L HCN /L HCO [+]



1.0 2.0 3.0

L HCN /L HCO [+]


IRAS F05189-2524


0.5



0.5



0.0



0.0



0.0



0.5



0.5



0.5



1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)



IRAS F05189-2524



IRAS F10565+2448



400


200


0


200


400



0.5


0.5



400


200


0


200


400



1.0
0.5

0.0

0.5

1.0



400


200


0


200


400


400


200


0


200


400



1.0
0.5

0.0

0.5

1.0



0.0



0.0



0.5



0.5



1.0 2.0 3.0

L HCN /L HCO [+]



**Fig. 6.** Same as Fig. 5 but for IRAS 09022-3615, IRAS F14378-3651, IRAS F05189-2524, and IRAS F10565+2448.


Article number, page 22 of 52

Y. Nishimura et al.: CON-quest



IRAS 19542+1110



ESO 320-G030



400


200


0


200


400



0.5


0.0


0.5


400


200


0


200


400


400


200


0


200


400



1.0


0.5


0.0


0.5


1.0


400


200


0


200


400


400


200


0


200


400


1.0


0.5


0.0


0.5


1.0



100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)


100 pc


0.5 0.0 0.5

(arcsec)



400


200


0


200


400



1.0



1.0



1.0
0.5

0.0

0.5

1.0



1.0
0.5

0.0

0.5

1.0



0.5



0.0



0.0



0.5


0.5



0.0



0.5



0.5



0.5



IRAS 19542+1110



ESO 320-G030



400


200


0


200


400



0.5


0.5



400


200


0


200


400



1.0
0.5

0.0

0.5

1.0



0.0



0.0



0.5



0.5



1.0 2.0 3.0

L HCN /L HCO [+]



**Fig. 7.** Same as Fig. 5 but for IRAS 19542+1110 and ESO 320-G030.


NGC 6240



1.0 2.0 3.0

L HCN /L HCO [+]


IRAS 17578-0400



1.5


1.0


0.5


0.0


0.5


1.0


1.5



100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc


1.0 0.5 0.0 0.5 1.0

(arcsec)


100 pc



0.5



400


200


0


200


400


1.0



1.5
1.0
0.5
0.0
0.5
1.0
1.5



1.5



400


200


0


200


400


1.5

1.0



100 pc



0.5



0.5



1.5 1.0 0.5 0.0 0.5 1.0 1.5

(arcsec)



1.0

0.5

0.0

0.5



0.0

0.5



0.0



1.0 0.5 0.0 0.5 1.0

(arcsec)



1.0



1.0



1.0



NGC 6240



400


200


0


200


400



IRAS 17578-0400



400


200


0


200


400



400


200


0


200


400


1.5
1.0
0.5
0.0
0.5
1.0
1.5



1.5
1.0
0.5
0.0
0.5
1.0
1.5



1.0

0.5

0.0

0.5



100 pc



100 pc



1.5 1.0 0.5 0.0 0.5 1.0 1.5

(arcsec)



400


200


0


200


400


1.0

0.5

0.0

0.5



1.0 0.5 0.0 0.5 1.0

(arcsec)



400


200


0


200


400



400


200


0


200


400



1.0



1.0



100 pc



100 pc



1.0 2.0 3.0

L HCN /L HCO [+]



1.0 2.0 3.0

L HCN /L HCO [+]



1.5 1.0 0.5 0.0 0.5 1.0 1.5

(arcsec)



1.0 0.5 0.0 0.5 1.0

(arcsec)



**Fig. 8.** Same as Fig. 5 but for NGC 6240 and IRAS 17578-0400. We note that the continuum has not been subtracted for IRAS 17578-0400.


Article number, page 23 of 52

_A&A proofs:_ manuscript no. clean


(relative to H 2 )















10 [2] 10 [3] 10 [4] 10 [5] 10 [6] 10 [7] 10 [8]

|NH2 = 1022 cm 2, Tkin = 20 K NH2 = 1023 cm 2, Tkin = 20 K N<br>6<br>HCO +<br>4<br>HCN/L<br>2 L<br>0<br>NH2 = 1022 cm 2, Tkin = 50 K NH2 = 1023 cm 2, Tkin = 50 K N<br>6<br>HCO +<br>4<br>HCN/L<br>2 L<br>0<br>NH2 = 1022 cm 2, Tkin = 100 K NH2 = 1023 cm 2, Tkin = 100 K N<br>6<br>HCO +<br>4<br>HCN/L<br>2 L<br>0<br>2 3 4 5 6 7 8 2 3 4 5 6 7 8 2|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**|**NH2 = 1022 cm** **2, Tkin = 20 K**|**NH2 = 1022 cm** **2, Tkin = 20 K**|**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**|**H2 = 1024 cm** **2, Tkin**|** = 20 K**|** = 20 K**|
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||**NH2 = 1022 cm** **2, Tkin = 50 K**|**NH2 = 1022 cm** **2, Tkin = 50 K**|**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**|**H2 = 1024 cm** **2, Tkin**|** = 50 K**|** = 50 K**|
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||<br>||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||**NH2 = 1022 cm** **2, Tkin = 100 K**|**NH2 = 1022 cm** **2, Tkin = 100 K**|**NH2 = 1023 cm** **2, Tkin = 100 K**<br>**N**|**H2 = 1024 cm** **2, Tkin**|** = 100 K**|** = 100 K**|
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||
|0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 20 K**<br>**NH2 = 1023 cm** **2, Tkin = 20 K**<br>**N**<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 50 K**<br>**NH2 = 1023 cm** **2, Tkin = 50 K**<br>**N**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>0<br>2<br>4<br>6<br>L HCN/L HCO +<br>**NH2 = 1022 cm** **2, Tkin = 100 K**<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>**NH2 = 1023 cm** **2, Tkin = 100 K**<br>2<br>**N**||||||||



Volume density (cm [3] )









10 [2] 10 [3] 10 [4] 10 [5] 10 [6] 10 [7] 10 [8]


Volume density (cm [3] )



10 [2] 10 [3] 10 [4] 10 [5] 10 [6] 10 [7] 10 [8]


Volume density (cm [3] )



**Fig.** **9.** One-zone non-LTE calculation of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [as] [a] [function] [of] [H] [2] [volume] [density.] [Gas] [kinetic] [temperatures] [of] [20,] [50,] [and] [100] [K] [and]
H 2 column densities of 10 [22], 10 [23], and 10 [24] cm [−][2] were considered. The line width was fixed to be 50 km s [−][1] for all models. Different color
curves represent various fractional abundances of HCN and HCO [+] as indicated in the legend. Solid curves correspond to models without electron
excitation, while dashed and dotted curves take into account excitation by electrons of different fractional abundances. Spikes seen in the lower
right panels are caused by the population inversion of HCN. The gray shades indicate the range of 0.4–2.3, corresponding to the global _L_ HCN [′] [/] _[L]_ HCO [′] [+]
found in the sample galaxies. See Sect. 6.1 for details.


Article number, page 24 of 52

Y. Nishimura et al.: CON-quest







10 [10]

|00<br>00<br>0<br>04<br>03<br>0 5<br>0 7<br>0 9<br>0 5<br>0 7<br>0 9<br>0 6<br>0 8<br>10|Temperature<br>vshock = 40 km s 1<br>vshock = 30 km s 1<br>vshock = 20 km s 1<br>vshock = 10 km s 1|
|---|---|
|0<br>00<br>00<br>03<br>04<br>0 9<br>0 7<br>0 5<br>0 9<br>0 7<br>0 5<br> 10<br>0 8<br>0 6|Density|
|0<br>00<br>00<br>03<br>04<br>0 9<br>0 7<br>0 5<br>0 9<br>0 7<br>0 5<br> 10<br>0 8<br>0 6|HCN|
|0<br>00<br>00<br>03<br>04<br>0 9<br>0 7<br>0 5<br>0 9<br>0 7<br>0 5<br> 10<br>0 8<br>0 6|HCO +|
|0<br>00<br>00<br>03<br>04<br>0 9<br>0 7<br>0 5<br>0 9<br>0 7<br>0 5<br> 10<br>0 8<br>0 6|e|



10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5] 10 [6] 10 [7]


Postshock time (yr)


**Fig. 10.** Chemical model predictions to simulate gas temperature, density, and fractional abundances of HCN, HCO [+], and electrons under
moderately-dense conditions ( _n_ H 2 ∼10 [3] –10 [4] cm [−][3] ). C-type shocks with
shock velocities of 10, 20, 30, and 40 km s [−][1] are considered. The preshock H 2 density is assumed to be 10 [3] cm [−][2] for all cases. More details
on the other assumed parameters are described in Sect. 6.2.



Article number, page 25 of 52

_A&A proofs:_ manuscript no. clean



**Appendix A:** **Spectra and moment maps**


In Figs. A.1–A.23, we present the basic figures, the resolved and
global spectra and moment maps of the HCN 3–2 and HCO [+] 3–2
lines, as well as the maps of the velocity-integrated line ratio.


**Appendix B:** **Line ratio in the ppV space**


In Sect. 5.3, we discussed the spatially and kinematically symmetric structures characterized by _L_ HCN [′] [/] _[L]_ HCO [′] [+] [exceeding] [the]
90th percentile in each galaxy. This appendix provides a visualization of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in] [the] [ppV] [space] [for] [all] [galaxies] [in]
which both HCN and HCO [+] are significantly detected, namely,
nearly the whole sample except for UGC 11763, UGC 2982, and
NGC 5734.
Figure B.1 presents the ppV plots for all spaxels where both
HCN and HCO [+] are detected with greater than 3σ significance.
Based on this figure, the sample appears to roughly split into
two groups: one comprising cases where the velocity dispersion
equals or exceeds any velocity gradient and another where the
gas forms a low dispersion sheet exhibiting a velocity gradient.
The former is predominantly found in merger cases, whereas the
latter is characteristic of non-mergers (See Table 1 for merger
stages).
Figure B.2 presents the ppV plots from the same angle as
Fig. B.1 but includes only the spaxels with the line ratios higher
than the 90th percentile. As discussed in the Sect. 5.3, the spatially and kinematically symmetric structures appear as a filled
bicone or a thin spherical shell in the galaxies with molecular
out- and/or inflows previously found by CO and/or OH line observations. Some other galaxies also (marginally) exhibit symmetric structures, possibly suggesting the presence of out- or inflows. (see Appendix C for details).


**Appendix C:** **Notes on individual galaxies**


We briefly summarize previous reports of out- and inflows and
discuss how they are related to the high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions]
(Fig. B.2) in individual galaxies:


1. _IRAS 17208_ − _0014:_ García-Burillo et al. (2015) identified
molecular outflows by interferometric CO 2–1 line observations and subsequent kinematic modeling. According to
them, the CO outflow is likely to be a collimated conical
shape elongating in the SE(blueshifted)-NW(redshifted) direction (see Fig. 18 of García-Burillo et al. 2015). In our
analysis, the high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [structure] [appears] [to] [be] [a]
filled biconical shape whose direction of elongation is consistent with the CO results (García-Burillo et al. 2015). Inflows, as indicated by the redshifted OH absorption feature
(+51 km s [−][1] Veilleux et al. 2013), could also contribute to
elevating _L_ HCN [′] [/] _[L]_ HCO [′] [+] [near that velocity.]
2. _IRAS 09022_ − _3615:_ The presence of outflows in this galaxy
is suggested by the OH absorption line. The OH 119 µm absorption is shallow (∼10% relative to the continuum), possibly indicating that the outflow is significantly collimated
(González-Alfonso et al. 2017). The high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [struc-]
ture ambiguously appears to be a spherical shell, but its morphology seems asymmetric. It is uncertain if HCN enhancement is associated with the OH outflow.
3. _IRAS 13120_ − _5453:_ In this galaxy, outflows have been found
using the CO emission (Fluetsch et al. 2019; Lutz et al. 2020)
and the OH absorption (Veilleux et al. 2013; GonzálezAlfonso et al. 2017). The outflow parameters derived from


Article number, page 26 of 52



these observations moderately disagree, probably due to limited signal-to-noise ratios, adopted morphology of the outflow, and excitation conditions for each molecular transition.
In addition, Privon et al. (2017) reports line wings in the
HCN 4–3 line as evidence for a high-velocity outflow. In
our _L_ HCN [′] [/] _[L]_ HCO [′] [+] [plots, enhancement of] _[L]_ HCN [′] [/] _[L]_ HCO [′] [+] [is seen]
in the central region at a wide range of velocities (roughly
spanning [−300, +300] km s [−][1] ), possibly in the form of a collimated and nearly pole-on outflow. The high line ratio structure shows velocity reversals, which may suggest the outflow
is precessing. We did not see the high-velocity components
(>300 km s [−][1] ) detected in the OH absorption, possibly due
to the faintness of the HCN and HCO [+] emission.
4. _IRAS F14378_ − _3651:_ Molecular outflows have been detected
through the blueshifted absorption feature in the far-infrared
OH lines (Veilleux et al. 2013; González-Alfonso et al.
2017). According to the model by González-Alfonso et al.
(2017), the OH outflows are at velocities of 250 km s [−][1] and
600 km s [−][1], located 200–300 pc away from the center. As for
the CO observations, Lutz et al. (2020) found a slight flux
excess at ∼250 km s [−][1] in the 1–0 transition, although it is not
significant enough to be robust evidence for outflows. Our
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [images] [show] [an] [enhancement] [in] [a] [wide-angle]
thin shell with a ∼250 pc radius, with the maximum velocity of ∼200 km s [−][1] (uncorrected for inclination). The location of the HCN enhancement seems to be associated with
the lower-velocity OH outflow. On the other hand, we did
not see emission from the higher-velocity (600 km s [−][1] ) outflow in our data. To detect the higher-velocity component,
higher sensitivity may be required.
5. _IRAS F05189_ − _2524:_ Similar to the case of
IRAS F14378−3651, IRAS F05189−2524 shows an enhancement of _L_ [′] [in] [the] [form] [of] [a] [thin] [spherical]
HCN [/] _[L]_ HCO [′] [+] [,]
shell in the ppV space. In terms of velocity, the HCNenhanced shell agrees with the lower-velocity OH outflow
at 200 km s [−][1] reported by González-Alfonso et al. (2017).
The presence of the higher-velocity (≳500 km s [−][1] ) outflows
is also known by the OH absorption González-Alfonso et al.
(2017) and the CO 3–2 emission (Fluetsch et al. 2019).
In our observations, the line profiles of HCN and HCO [+]
emission show small bumps near the velocity of the fast
outflow (Figs. A.5). However, the morphology of bumps are
asymmetric and are likely to be affected by emission from
other molecular species. Thus, the high-velocity component
is not confirmed in our data.
6. _IRAS F10565_ + _2448:_ The high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions] [appear]
to be a thin spherical shell with an ambiguous filled bicone.
The highest _L_ HCN [′] [/] _[L]_ HCO [′] [+] [ is seen at velocities of][ ∼][250 km s] [−][1] [,]
which is consistent with the outflow velocity measured by
OH absorption (Veilleux et al. 2013; González-Alfonso et al.
2017). While CO line wings in the velocity range of 300–
600 km s [−][1] indicate the presence of faster components (Cicone et al. 2014), we did not detect emission of HCN or
HCO [+] in that velocity range. Higher sensitivity observations
would be necessary to trace the fast components.
7. _IRAS 19542_ + _1110:_ Molecular outflows in this galaxy have
been found through a blueshifted OH absorption feature at
the velocity of −93 km s [−][1] (Veilleux et al. 2013). In our analysis, _L_ HCN [′] [/] _[L]_ HCO [′] [+] [appears to be high in a thin spherical shell]
with a radius of ∼500 pc and in a velocity range of about

[−200, 200] km s [−][1] . Little is known about the morphology
of the outflow so far, but the structure of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [sug-]
gests that the outflow shape could be a thin shell with a wide
opening angle.

Y. Nishimura et al.: CON-quest


IRAS 17208-0014 Moment 0 [-500, +500] km s [1]


|CH2NH|HC3N-vib|
|---|---|
|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>2303<br>.<br>1<br>s<br>1792 km<br>.<br>(Jy<br>1280 intensity<br>.<br>768<br>.<br>grated<br>256<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|+ HOC|HCN-vib CH3OH|
|---|---|
|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|300<br>200 1)<br>s<br>100 (km<br>0<br>Velocity<br>-100<br>200<br>-<br>300<br>-|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|CH2NH|HC3N-vib|
|---|---|
|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|200 1)<br>s<br>(km<br>150<br>dispersion<br>100<br>Velocity<br>50|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|IRAS 17208-0014|(global) HCO+ 3-2|
|---|---|
|HOC +|CH3OH<br>HCN-vib|
|||



Right Ascension (J2000)



30


20


10


0


30


20


10


0


125


100


75


50


25


0


125


100


75


50


25


0



IRAS 17208-0014 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 17208-0014 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 17208-0014 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


1000 500 0 500 1000

Velocity (km s [1] )







-0°17'00"


01"


02"



17 [h] 23 [m] 22.0 [s] 21.9 [s]


Right Ascension (J2000)



(5,10,20,40,80,120,160,200,240)

× 0.096 Jy km s [1] beam [1]



IRAS 17208-0014 Moment 1


-0°17'00"


01"


02"


17 [h] 23 [m] 22.0 [s] 21.9 [s]


Right Ascension (J2000)


IRAS 17208-0014 Moment 2


-0°17'00"


01"


02"


17 [h] 23 [m] 22.0 [s] 21.9 [s]


Right Ascension (J2000)


IRAS 17208-0014 HCN/HCO [+] [-500, +500] km s [1]



0



-0°17'00"









**Fig.** **A.1.** HCN 3–2 and HCO [+] 3–2 for IRAS 17208−0014. _Left_ _panels_ : ( _Top_ _two_ _panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±500 km s [−][1] (moment 0). Contours are (5, 10,
20, 40, 80, 120, 160, 200, 240) ×σ, where σ is 0.096 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of
±50 km s [−][1] . ( _Third from top_ ) Velocity dispersion (moment 2). Contours are in steps of 20 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 27 of 52

_A&A proofs:_ manuscript no. clean


IRAS 09022-3615 Moment 0 [-500, +500] km s [1]


|CH2NH|HC3N-vib|
|---|---|
|||


|+ HOC|HCN-vib CH3OH|
|---|---|
|||


|IRAS 09022-3615|(global) HCN 3-2|
|---|---|
|CH2NH|HC3N-vib|
|||


|IRAS 09022-3615|(global) HCO+ 3-2|
|---|---|
|HOC +|CH3OH<br>HCN-vib|
|||



9 [h] 04 [m] 12.8 [s] 12.7 [s] 12.6 [s]


Right Ascension (J2000)



IRAS 09022-3615 Moment 1


9 [h] 04 [m] 12.8 [s] 12.7 [s] 12.6 [s]


Right Ascension (J2000)


IRAS 09022-3615 Moment 2









6


4


2


0


6


4


2



IRAS 09022-3615 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 09022-3615 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


1000 500 0 500 1000

Velocity (km s [1] )


1000 500 0 500 1000

Velocity (km s [1] )



-36°27'00"


01"


02"


03"


-36°27'00"


01"


02"


03"


-36°27'00"







9 [h] 04 [m] 12.8 [s] 12.7 [s] 12.6 [s]


Right Ascension (J2000)



(5,10,20,40,80,120,160,200)

× 0.020 Jy km s [1] beam [1]







0


40





30


20





10


0









40


30



01"


02"


03"


9 [h] 04 [m] 12.8 [s] 12.7 [s] 12.6 [s]


Right Ascension (J2000)


IRAS 09022-3615 HCN/HCO [+] [-500, +500] km s [1]


-36°27'00"







20


10


0



01"


02"


03"





**Fig.** **A.2.** HCN 3–2 and HCO [+] 3–2 for IRAS 09022−3615. _Left_ _panels_ : ( _Top_ _two_ _panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±500 km s [−][1] (moment 0). Contours are (5, 10,
20, 40, 80, 120, 160, 200) ×σ, where σ is 0.020 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of ±50
km s [−][1] . ( _Third_ _from_ _top_ ) Velocity dispersion (moment 2). Contours are in steps of 20 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 28 of 52

Y. Nishimura et al.: CON-quest


IRAS 13120-5453 Moment 0 [-500, +500] km s [1]


|IRAS 13120-5453|(resolved) HCN 3-2|
|---|---|
|CH2NH|HC3N-vib|
|||


|IRAS 13120-5453|(resolved) HCO+ 3-2|
|---|---|
|HOC +|CH3OH<br>HCN-vib|
|||


|CH2NH|HC3N-vib|
|---|---|
|||


|+ HOC|HCN-vib CH3OH|
|---|---|
|||



13 [h] 15 [m] 06.6 [s] 06.4 [s] 06.3 [s] 06.2 [s] 06.1 [s]


Right Ascension (J2000)



30


20


10


0


30


20


10



1000 500 0 500 1000

Velocity (km s [1] )


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 13120-5453 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 13120-5453 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



IRAS 13120-5453 Moment 1


-55°09'21"


22"


23"


24"


25"


13 [h] 15 [m] 06.6 [s] 06.4 [s] 06.3 [s] 06.2 [s] 06.1 [s]


Right Ascension (J2000)


IRAS 13120-5453 Moment 2


-55°09'21"


22"


23"


24"


25"


13 [h] 15 [m] 06.6 [s] 06.4 [s] 06.3 [s] 06.2 [s] 06.1 [s]


Right Ascension (J2000)


IRAS 13120-5453 HCN/HCO [+] [-500, +500] km s [1]









-55°09'21"


22"


23"


24"


25"


13 [h] 15 [m] 06.6 [s] 06.4 [s] 06.3 [s] 06.2 [s] 06.1 [s]


Right Ascension (J2000)





(5,10,20,40,80,120,160)
× 0.103 Jy km s [1] beam [1]







0


250





200


150





100


50





0


250


200







150


100


50


0



-55°09'21"


22"


23"


24"


25"









**Fig.** **A.3.** HCN 3–2 and HCO [+] 3–2 for IRAS 13120−5453. _Left_ _panels_ : ( _Top_ _two_ _panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±500 km s [−][1] (moment 0). Contours are (5,
10, 20, 40, 80, 120, 160) ×σ, where σ is 0.103 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of ±50
km s [−][1] . ( _Third_ _from_ _top_ ) Velocity dispersion (moment 2). Contours are in steps of 20 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 29 of 52

IRAS F14378-3651 (resolved) HCN 3-2


8


6


4


2


0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS F14378-3651 (resolved) HCO [+] 3-2



_A&A proofs:_ manuscript no. clean


IRAS F14378-3651 Moment 0 [-250, +250] km s [1]





-37°04'31"


32"


33"

|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>253<br>.<br>1<br>s<br>197 km<br>.<br>(Jy<br>141 intensity<br>.<br>084<br>.<br>grated<br>028<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



14 [h] 40 [m] 59.1 [s] 59.0 [s] 58.9 [s]


Right Ascension (J2000)





(5,10,20,40,60,80,100,120,140)

× 0.019 Jy km s [1] beam [1]



8


6


4


2


0


40


30


20


10


0


40


30


20


10


0


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|150<br>100 1)<br>s<br>50 (km<br>0<br>Velocity<br>-50<br>-100<br>-150|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



1000 500 0 500 1000

Velocity (km s [1] )


IRAS F14378-3651 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS F14378-3651 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



IRAS F14378-3651 Moment 1


-37°04'31"


32"


33"


14 [h] 40 [m] 59.1 [s] 59.0 [s] 58.9 [s]


Right Ascension (J2000)


IRAS F14378-3651 Moment 2


-37°04'31"


32"


33"

|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|1)<br>75<br>s<br>(km<br>dispersion<br>50<br>25 Velocity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



14 [h] 40 [m] 59.1 [s] 59.0 [s] 58.9 [s]


Right Ascension (J2000)


IRAS F14378-3651 HCN/HCO [+] [-250, +250] km s [1]



|500pc|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
|500 pc|||
|500 pc|||
|500 pc|||


14 [h] 40 [m] 59.1 [s] 59.0 [s] 58.9 [s]


Right Ascension (J2000)



0



-37°04'31"


32"


33"





**Fig. A.4.** HCN 3–2 and HCO [+] 3–2 for IRAS F14378−3651. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±250 km s [−][1] (moment 0). Contours are (5, 10,
20, 40, 60, 80, 100, 120, 140) ×σ, where σ is 0.019 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±25
km s [−][1] . ( _Third_ _from_ _top_ ) Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 30 of 52

IRAS F05189-2524 (resolved) HCN 3-2


25


20


15


10


5


0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS F05189-2524 (resolved) HCO [+] 3-2


25


20


15


10


5


0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS F05189-2524 (global) HCN 3-2

80


60


40


20


0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS F05189-2524 (global) HCO [+] 3-2

80


60


40


20


0


1000 500 0 500 1000

Velocity (km s [1] )



Y. Nishimura et al.: CON-quest


IRAS F05189-2524 Moment 0 [-250, +250] km s [1]


|HCN 3 -2|Col2|HCO+ 3 -2|500pc|Col5|bea<br>885<br>.<br>1<br>s<br>688 km<br>.<br>(Jy<br>491 intensity<br>.<br>295<br>.<br>grated<br>098<br>.|
|---|---|---|---|---|---|
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||


|HCN 3 -2|Col2|HCO+ 3 -2|500pc|Col5|150<br>100 1)<br>s<br>50 (km<br>0<br>Velocity<br>-50<br>-100<br>-150|
|---|---|---|---|---|---|
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||


|HCN 3 -2|Col2|HCO+ 3 -2|500pc|Col5|1)<br>75 s<br>(km<br>dispersion<br>50<br>25 Velocity|
|---|---|---|---|---|---|
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||HCO+ 3-2|500 pc|||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||
|HCN 3-2||||||



|44"<br>45"<br>46"|Col2|Col3|Col4|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|---|---|
|44"<br>45"<br>46"||500 pc|500 pc|500 pc|


5 [h] 21 [m] 01.5 [s] 01.4 [s] 01.3 [s]


Right Ascension (J2000)



-25°21'44"


45"


46"









5 [h] 21 [m] 01.5 [s] 01.4 [s] 01.3 [s]


Right Ascension (J2000)



(5,10,20,40,80,160,240,320,400)

× 0.024 Jy km s [1] beam [1]



0



-25°21'44"


45"


46"



IRAS F05189-2524 Moment 1



5 [h] 21 [m] 01.5 [s] 01.4 [s] 01.3 [s]


Right Ascension (J2000)


IRAS F05189-2524 Moment 2



-25°21'44"





45"


46"


5 [h] 21 [m] 01.5 [s] 01.4 [s] 01.3 [s]


Right Ascension (J2000)


IRAS F05189-2524 HCN/HCO [+] [-250, +250] km s [1]



-25°21'44"





**Fig. A.5.** HCN 3–2 and HCO [+] 3–2 for IRAS F05189−2524. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±250 km s [−][1] (moment 0). Contours are (5, 10,
20, 40, 80, 160, 240, 320, 400) ×σ, where σ is 0.024 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of
±25 km s [−][1] . ( _Third from top_ ) Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 31 of 52

IRAS F10565+2448 (resolved) HCN 3-2


6


4


2


0

|CH2NH|HC3N-vib|
|---|---|
|||



1000 500 0 500 1000

Velocity (km s [1] )



_A&A proofs:_ manuscript no. clean


IRAS F10565+2448 Moment 0 [-250, +250] km s [1]

24°32'37"


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>174<br>.<br>1<br>s<br>135 km<br>.<br>(Jy<br>097 intensity<br>.<br>058<br>.<br>grated<br>019<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



IRAS F10565+2448 Moment 1


24°32'37"


36"


35"


34"


33"

|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|150<br>100 1)<br>s<br>50 (km<br>0<br>Velocity<br>-50<br>-100<br>-150|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



10 [h] 59 [m] 18.3 [s] 18.2 [s] 18.1 [s] 18.0 [s]


Right Ascension (J2000)


IRAS F10565+2448 Moment 2


24°32'37"


36"


35"


34"


33"

|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|1)<br>s<br>(km<br>50<br>dispersion<br>25<br>Velocity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



10 [h] 59 [m] 18.3 [s] 18.2 [s] 18.1 [s] 18.0 [s]


Right Ascension (J2000)


IRAS F10565+2448 HCN/HCO [+] [-250, +250] km s [1]

24°32'37"





36"


35"


34"


33"


10 [h] 59 [m] 18.3 [s] 18.2 [s] 18.1 [s] 18.0 [s]


Right Ascension (J2000)





(5,10,20,30,40,50,60,70,80)

× 0.023 Jy km s [1] beam [1]



6


4


2


0


80


60


40


20


0


80


60


40


20


0


|RAS F10565+2448|(resolved) HCO+ 3-|
|---|---|
|HOC +|CH3OH<br>HCN-vib|
|||



1000 500 0 500 1000

Velocity (km s [1] )


IRAS F10565+2448 (global) HCN 3-2

|CH2NH|HC3N-vib|
|---|---|
|||



1000 500 0 500 1000

Velocity (km s [1] )


IRAS F10565+2448 (global) HCO [+] 3-2

|+ HOC|HCN-vib CH3OH|
|---|---|
|||



1000 500 0 500 1000

Velocity (km s [1] )



36"


35"


34"


33"

|500pc|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
|500 pc|||
|500 pc|||
|500 pc|||



10 [h] 59 [m] 18.3 [s] 18.2 [s] 18.1 [s] 18.0 [s]


Right Ascension (J2000)



0





**Fig. A.6.** HCN 3–2 and HCO [+] 3–2 for IRAS F10565+2448. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±250 km s [−][1] (moment 0). Contours are (5, 10,
20, 30, 40, 50, 60, 70, 80) ×σ, where σ is 0.023 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of ±25
km s [−][1] . ( _Third_ _from_ _top_ ) Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 32 of 52

IRAS 19542+1110 (resolved) HCN 3-2


12.5


10.0


7.5


5.0


2.5


0.0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 19542+1110 (resolved) HCO [+] 3-2


12.5


10.0


7.5


5.0


2.5


0.0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 19542+1110 (global) HCN 3-2


30


20


10


0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 19542+1110 (global) HCO [+] 3-2


30


20


10


0


1000 500 0 500 1000

Velocity (km s [1] )



Y. Nishimura et al.: CON-quest


IRAS 19542+1110 Moment 0 [-300, +300] km s [1]


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>508<br>.<br>1<br>s<br>395 km<br>.<br>(Jy<br>282 intensity<br>.<br>169<br>.<br>grated<br>056<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|200<br>150<br>100 1)<br>s<br>50 (km<br>0<br>Velocity<br>-50<br>-100<br>-150<br>200<br>-|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|100 1)<br>s<br>(km<br>75<br>dispersion<br>50<br>Velocity<br>25|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



|500pc|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
|500 pc|||
|500 pc|||
|500 pc|||


19 [h] 56 [m] 35.8 [s] 35.7 [s]


Right Ascension (J2000)



(5,10,20,40,80,160,240)
× 0.019 Jy km s [1] beam [1]





11°19'06"


05"


04"



19 [h] 56 [m] 35.8 [s] 35.7 [s]


Right Ascension (J2000)



IRAS 19542+1110 Moment 1


11°19'06"


05"


04"


19 [h] 56 [m] 35.8 [s] 35.7 [s]


Right Ascension (J2000)


IRAS 19542+1110 Moment 2


11°19'06"


05"


04"


19 [h] 56 [m] 35.8 [s] 35.7 [s]


Right Ascension (J2000)


IRAS 19542+1110 HCN/HCO [+] [-300, +300] km s [1]



0



11°19'06"


05"


04"





**Fig.** **A.7.** HCN 3–2 and HCO [+] 3–2 for IRAS 19542+1110. _Left_ _panels_ : ( _Top_ _two_ _panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±300 km s [−][1] (moment 0). Contours are (5,
10, 20, 40, 80, 160, 240) ×σ, where σ is 0.019 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of ±25
km s [−][1] . ( _Third_ _from_ _top_ ) Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 33 of 52

_A&A proofs:_ manuscript no. clean


ESO 148-IG002 Moment 0 [-200, +200] km s [1]


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>204<br>.<br>1<br>s<br>158 km<br>.<br>(Jy<br>113 intensity<br>.<br>068<br>.<br>grated<br>023<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|140<br>120<br>100<br>80 1)<br>60<br>s<br>40 (km<br>20<br>0<br>Velocity<br>20<br>-<br>-40<br>60<br>-<br>80<br>-<br>-100<br>-120<br>-140|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3 -2|HCO+ 3 -2|Col3|70<br>1)<br>60 s<br>(km<br>50<br>dispersion<br>40<br>30<br>20 ocity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|500pc|Col2|
|---|---|
|500 pc||
|500 pc||
|500 pc||



23 [h] 15 [m] 46.9 [s] 46.7 [s] 46.6 [s]


Right Ascension (J2000)



(5,10,20,40,60,80,100)
× 0.021 Jy km s [1] beam [1]





8


6


4


2


0


8


6


4


2


0


30


20


10


0


30


20


10


0



ESO 148-IG002 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 148-IG002 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 148-IG002 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 148-IG002 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



-59°03'14"


15"


16"


17"



15"


16"


17"





23 [h] 15 [m] 46.9 [s] 46.7 [s] 46.6 [s]


Right Ascension (J2000)



10


0



-59°03'14"


15"


16"


17"



ESO 148-IG002 Moment 1



23 [h] 15 [m] 46.9 [s] 46.7 [s] 46.6 [s]


Right Ascension (J2000)


ESO 148-IG002 Moment 2



-59°03'14"


15"


16"


17"





23 [h] 15 [m] 46.9 [s] 46.7 [s] 46.6 [s]


Right Ascension (J2000)


ESO 148-IG002 HCN/HCO [+] [-200, +200] km s [1]


-59°03'14"









**Fig. A.8.** HCN 3–2 and HCO [+] 3–2 for ESO 148−IG002. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two_
_panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±200 km s [−][1] (moment 0). Contours are (5,
10, 20, 40, 60, 80, 100) ×σ, where σ is 0.019 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of ±10
km s [−][1] . ( _Third_ _from_ _top_ ) Velocity dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 34 of 52

Y. Nishimura et al.: CON-quest


NGC 6240 Moment 0 [-500, +500] km s [1]



|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>427<br>.<br>1<br>s<br>332 km<br>.<br>(Jy<br>237 intensity<br>.<br>142<br>.<br>grated<br>047<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


(5,10,20,40,60,80,100)
× 0.040 Jy km s [1] beam [1]





6


4


2


0


6


4


2


0


150


100


50


0


150


100


50


0



NGC 6240 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 6240 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 6240 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 6240 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



2°24'06"


05"


04"


03"


02"


01"


2°24'06"


05"


04"


03"


02"


01"


2°24'06"


05"


04"


03"


02"


01"


|NGC 6240|Moment 1|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc||-300<br>-200<br>-100<br>0<br>100<br>200<br>300<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|NGC 6240|Moment 2|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc||50<br>100<br>150<br>Velocity dispersion (km s 1)|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



01"



16 [h] 52 [m] 59.0 [s] 58.8 [s] 58.7 [s]


Right Ascension (J2000)



16 [h] 52 [m] 59.0 [s] 58.8 [s] 58.7 [s]


Right Ascension (J2000)



0



16 [h] 52 [m] 59.0 [s] 58.8 [s] 58.7 [s]


Right Ascension (J2000)


NGC 6240 HCN/HCO [+] [-500, +500] km s [1]


2°24'06"


05"


04"


03"


02"



|500pc|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
|500 pc|||
|500 pc|||
|500 pc|||


16 [h] 52 [m] 59.0 [s] 58.8 [s] 58.7 [s]


Right Ascension (J2000)



**Fig. A.9.** HCN 3–2 and HCO [+] 3–2 for NGC 6240. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±500 km s [−][1] (moment 0). Contours are (5, 10, 20,
40, 60, 80, 100) ×σ, where σ is 0.040 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of ±50 km s [−][1] .
( _Third from top_ ) Velocity dispersion (moment 2). Contours are in steps of 20 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ )
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent]
the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners. Yellow crosses
show the positions of two nuclei taken from Hagiwara et al. (2011).

Article number, page 35 of 52

IRAS F17138-1017 (resolved) HCN 3-2


3


2


1


0


1000 500 0 500 1000

Velocity (km s [1] )


IRAS F17138-1017 (resolved) HCO [+] 3-2



_A&A proofs:_ manuscript no. clean


IRAS F17138-1017 Moment 0 [-150, +150] km s [1]



|HCN 3 -2|HCO+ 3 -2|Col3|bea<br>054<br>.<br>1<br>s<br>042 km<br>.<br>(Jy<br>030 intensity<br>.<br>018<br>.<br>ed|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


(5,10)
× 0.045 Jy km s [1] beam [1]





17 [h] 16 [m] 36.0 [s] 35.8 [s] 35.6 [s]


Right Ascension (J2000)



IRAS F17138-1017 Moment 1

|HCN 3 -2|HCO+ 3 -2|Col3|100<br>80<br>60 1)<br>40 s<br>20 (km<br>0<br>Velocity<br>20<br>-<br>-40<br>60<br>-<br>80|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||



17 [h] 16 [m] 36.0 [s] 35.8 [s] 35.6 [s]


Right Ascension (J2000)


IRAS F17138-1017 Moment 2

|HCN 3 -2|HCO+ 3 -2|Col3|1)<br>s<br>(km<br>20 dispersion<br>10<br>ocity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||



17 [h] 16 [m] 36.0 [s] 35.8 [s] 35.6 [s]



0



3


2


1


0


40


30


20


10


0


40


30


20


10


0



Velocity (km s [1] )


IRAS F17138-1017 (global) HCN 3-2


Velocity (km s [1] )


IRAS F17138-1017 (global) HCO [+] 3-2



-10°20'36"


38"


40"


42"


44"



-10°20'36"


38"


40"


42"


44"


-10°20'36"


38"


40"


42"


44"


-10°20'36"


38"


40"


42"


44"



Right Ascension (J2000)


IRAS F17138-1017 HCN/HCO [+] [-150, +150] km s [1]


|Col1|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
||||
||||



17 [h] 16 [m] 36.0 [s] 35.8 [s] 35.6 [s]


Right Ascension (J2000)




|0|Col2|Col3|
|---|---|---|
|||HOC +|
|1000<br>500<br>0<br>Velocity (k<br>|1000<br>500<br>0<br>Velocity (k<br>|1000<br>500<br>0<br>Velocity (k<br>|



**Fig. A.10.** HCN 3–2 and HCO [+] 3–2 for IRAS F17138−1017. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±150 km s [−][1] (moment 0). Contours are (5,
10) ×σ, where σ is 0.045 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ )
Velocity dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color]
scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic
major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 36 of 52

Y. Nishimura et al.: CON-quest


IRAS 17578-0400 Moment 0 [-250, +250] km s [1]


|CH2NH|HC3N-vib|
|---|---|
|||
|||


|HCO+ 3 -2|500pc|Col3|bea<br>3725<br>.<br>1<br>s<br>2897 km<br>.<br>(Jy<br>2069 intensity<br>.<br>1242<br>.<br>grated<br>414<br>.|
|---|---|---|---|
|HCO+ 3-2|500 pc|||


|+|H b|
|---|---|
|HOC +|CH3OH<br>HCN-vi|
|||
|||


|HCO+ 3-2|Col2|Col3|Col4|
|---|---|---|---|
|HCO+ 3-2|500 pc||-150<br>-100<br>-50<br>0<br>50<br>100<br>150<br>Velocity (km s 1)|
|HCO+ 3-2|500 pc|||
|HCO+ 3-2|500 pc|||
|HCO+ 3-2|500 pc|||


|HCO+ 3-2|Col2|Col3|75 100 125 ion (km s 1|
|---|---|---|---|
||500 pc||25<br>50<br>75<br>Velocity dispers|
||500 pc|||


|IRAS 17578-0400|(global) HCO+ 3-2|
|---|---|
|HOC +|CH3OH<br>HCN-vib|
|||
|||



18 [h] 00 [m] 31.9 [s] 31.8 [s]


Right Ascension (J2000)



80


60


40


20


0


80


60


40


20


0


250


200


150


100


50


0


250


200


150


100


50


0



IRAS 17578-0400 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 17578-0400 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IRAS 17578-0400 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


1000 500 0 500 1000

Velocity (km s [1] )







-4°00'52"


53"


54"


55"


-4°00'52"


53"


54"


55"


-4°00'52"



18 [h] 00 [m] 31.9 [s] 31.8 [s]


Right Ascension (J2000)



(5,10,20,40,80,160,320,480,640,800)

× 0.051 Jy km s [1] beam [1]



IRAS 17578-0400 Moment 1


18 [h] 00 [m] 31.9 [s] 31.8 [s]


Right Ascension (J2000)


IRAS 17578-0400 Moment 2



0



53"


54"


55"


18 [h] 00 [m] 31.9 [s] 31.8 [s]


Right Ascension (J2000)


IRAS 17578-0400 HCN/HCO [+] [-250, +250] km s [1]


-4°00'52"



53"


54"


55"









**Fig. A.11.** HCN 3–2 and HCO [+] 3–2 for IRAS 17578−0400. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower_
_two panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. Horizontal dashed lines are the assumed continuum level. _Right_ _panels_ : ( _Top_ ) Integrated
intensity over ±250 km s [−][1] (moment 0). Contours are (5, 10, 20, 40, 80, 160, 320, 480, 640, 800) ×σ, where σ is 0.051 Jy km s [−][1] beam [−][1] . ( _Second_
_from top_ ) Velocity field (moment 1). Contours are in steps of ±25 km s [−][1] . ( _Third from top_ ) Velocity dispersion (moment 2). Contours are in steps
of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is from 0.285 to 3.5. Overlaid ellipses represent]
the apertures used for spectral extraction. Solid and dashed lines represent the kinematic major and minor axes, respectively. The synthesized beam
is indicated by hatched ellipses in the lower right corners. Note that continuum is not subtracted.

Article number, page 37 of 52

_A&A proofs:_ manuscript no. clean


ESO 173-G015 Moment 0 [-250, +250] km s [1]


|HCN 3 -2|HCO+ 3 -2<br>100pc|Col3|bea<br>944<br>.<br>1<br>s<br>734 km<br>.<br>(Jy<br>524 intensity<br>.<br>315<br>.<br>grated<br>105<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||


|HCN 3 -2|HCO+ 3 -2<br>100pc|Col3|150<br>100 1)<br>s<br>50 (km<br>0<br>Velocity<br>-50<br>-100<br>-150|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||


|Col1|Col2|Col3|75|
|---|---|---|---|
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc||25<br>50<br>75<br>Velocity dispersion (km s 1)|
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||
|HCN 3-2|HC~~O~~+ 3-2<br>100 pc|||


|100pc|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
|100 pc|||
|100 pc|||
|100 pc|||



13 [h] 27 [m] 24.2 [s] 23.8 [s] 23.6 [s] 23.4 [s] 23.2 [s]


Right Ascension (J2000)









25


20


15


10


5


0


25


20


15


10


5


0


300


200


100


0


300


200


100


0



ESO 173-G015 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 173-G015 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 173-G015 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 173-G015 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



-57°29'18"


20"


22"


24"


26"



22"


24"


26"



13 [h] 27 [m] 24.2 [s] 23.8 [s] 23.6 [s] 23.4 [s] 23.2 [s]


Right Ascension (J2000)



(5,10,20,40,80,120,160,200,240)

× 0.043 Jy km s [1] beam [1]



0



-57°29'18"


20"


22"


24"


26"



ESO 173-G015 Moment 1



13 [h] 27 [m] 24.2 [s] 23.8 [s] 23.6 [s] 23.4 [s] 23.2 [s]


Right Ascension (J2000)


ESO 173-G015 Moment 2



-57°29'18"


20"


22"


24"


26"





13 [h] 27 [m] 24.2 [s] 23.8 [s] 23.6 [s] 23.4 [s] 23.2 [s]


Right Ascension (J2000)


ESO 173-G015 HCN/HCO [+] [-250, +250] km s [1]


-57°29'18"


20"







**Fig. A.12.** HCN 3–2 and HCO [+] 3–2 for ESO 173−G015. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two_
_panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±250 km s [−][1] (moment 0). Contours are (5, 10,
20, 40, 80, 120, 160, 200, 240) ×σ, where σ is 0.043 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of
±25 km s [−][1] . ( _Third from top_ ) Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 38 of 52

Y. Nishimura et al.: CON-quest


UGC 11763 Moment 0 [-200, +200] km s [1]


|UGC 11763|3 Moment 1|Col3|150|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2||-100<br>-50<br>0<br>50<br>100<br>150<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2|||




[s]



Right Ascension (J2000)



0.5


0.4


0.3


0.2


0.1


0.0


0.5


0.4


0.3


0.2


0.1


0.0


6


4


2


0

[+]



6


4


2


0



UGC 11763 (resolved) HCN 3-2


UGC 11763 (global) HCN 3-2


UGC 11763 (global) HCO [+] 3-2



10°08'20"


19"


18"


21 [h] 32 [m] 27.9 [s] 27.8 [s]









10°08'20"


19"


18"


21 [h] 32 [m] 27.9 [s] 27.8 [s]


Right Ascension (J2000)





(5)
× 0.018 Jy km s [1] beam [1]



UGC 11763 Moment 1


10°08'20"


19"


18"


21 [h] 32 [m] 27.9 [s] 27.8 [s]


Right Ascension (J2000)


UGC 11763 Moment 2


10°08'20"


19"


18"


21 [h] 32 [m] 27.9 [s] 27.8 [s]


Right Ascension (J2000)


UGC 11763 HCN/HCO [+] [-200, +200] km s [1]







-150















**Fig.** **A.13.** HCN 3–2 and HCO [+] 3–2 for UGC 11763. _Left_ _panels_ : ( _Top_ _two_ _panels_ ) Spectra extracted from the resolved aperture. ( _Lower_ _two_
_panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±200 km s [−][1] (moment 0). Contours are (5) ×σ,
where σ is 0.018 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±25 km s [−][1] . ( _Third from top_ ) Velocity
dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is]
from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic major and
minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 39 of 52

_A&A proofs:_ manuscript no. clean


-6°28'28"


|NGC 3110 Moment|0 [-200, +200] km s 1|Col3|m 1)|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2||0.15<br>0.26<br>0.36<br>0.46<br>ed intensity (Jy km s 1 bea|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|CH2NH<br>1000 500|CH2NH|HC3N-vib|
|---|---|---|
|1000<br>500<br><br><br><br><br><br>CH2NH|CH2NH|500<br>100|


|HCN 3-2|NGC 3110|HCO+ 3-2  Moment 1|Col4|140|
|---|---|---|---|---|
|HCN 3-2||HCO+ 3-2||-80<br>-60<br>-40<br>-20<br>0<br>20<br>40<br>60<br>80<br>100<br>120<br>140<br>Velocity (km s 1)|
|HCN 3-2||HCO+ 3-2|||
|HCN 3-2||HCO+ 3-2|||
|HCN 3-2||HCO+ 3-2|||
|HCN 3-2||HCO+ 3-2|||
|HCN 3-2||HCO+ 3-2|||


|+<br>HOC<br>1000 500<br>Velocity|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br><br>Velocity<br><br><br><br><br>HOC +|HOC +|0<br>500<br>1000<br> (km s 1)|


|0 5 CH2NH|HC3N-vib|
|---|---|
||H|
|1000<br>500<br><br>|500<br>1000<br> 1|



10 [h] 04 [m] 02.1 [s] 02.0 [s]


Right Ascension (J2000)



(5,10)
× 0.034 Jy km s [1] beam [1]





1.5


1.0


0.5


0.0


1.5


1.0


0.5


0.0


25


20


15


10


5


0


25


20


15


10


5


0



NGC 3110 (resolved) HCN 3-2


Velocity (km s [1] )


NGC 3110 (resolved) HCO [+] 3-2


NGC 3110 (global) HCN 3-2


Velocity (km s [1] )


NGC 3110 (global) HCO [+] 3-2


Velocity (km s [1] )



29"


30"


-6°28'28"


29"


30"


-6°28'28"


29"


30"



10 [h] 04 [m] 02.1 [s] 02.0 [s]


Right Ascension (J2000)



10 [h] 04 [m] 02.1 [s] 02.0 [s]


Right Ascension (J2000)


NGC 3110 Moment 2



-100

-140











10 [h] 04 [m] 02.1 [s] 02.0 [s]


Right Ascension (J2000)


NGC 3110 HCN/HCO [+] [-200, +200] km s [1]

-6°28'28"













**Fig. A.14.** HCN 3–2 and HCO [+] 3–2 for NGC 3110. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±200 km s [−][1] (moment 0). Contours are (5, 10) ×σ,
where σ is 0.034 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ ) Velocity
dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is]
from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic major and
minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 40 of 52

Y. Nishimura et al.: CON-quest


IC 4734 Moment 0 [-200, +200] km s [1]


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>265<br>.<br>1<br>s<br>206 km<br>.<br>(Jy<br>147 intensity<br>.<br>088<br>.<br>grated<br>029<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|IC 4734 M|Moment 1|Col3|150|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc||-100<br>-50<br>0<br>50<br>100<br>150<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|1)<br>s<br>50 (km<br>dispersion<br>25<br>Velocity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|500pc|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
|500 pc|||
|500 pc|||
|500 pc|||



18 [h] 38 [m] 26.0 [s] 25.6 [s] 25.4 [s]


Right Ascension (J2000)



15


10


5


0


15


10


5


0


125


100


75


50


25


0


125


100


75


50


25


0



IC 4734 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IC 4734 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IC 4734 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IC 4734 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



-57°29'22"


24"


26"


28"



-57°29'22"


24"


26"


28"









18 [h] 38 [m] 26.0 [s] 25.6 [s] 25.4 [s]


Right Ascension (J2000)


IC 4734 Moment 1



-150


0



-57°29'22"


24"


26"


28"





18 [h] 38 [m] 26.0 [s] 25.6 [s] 25.4 [s]


Right Ascension (J2000)


IC 4734 Moment 2



-57°29'22"


24"


26"


28"





(5,10,20,30,40,50,60)
× 0.047 Jy km s [1] beam [1]



18 [h] 38 [m] 26.0 [s] 25.6 [s] 25.4 [s]


Right Ascension (J2000)


IC 4734 HCN/HCO [+] [-200, +200] km s [1]







**Fig. A.15.** HCN 3–2 and HCO [+] 3–2 for IC 4734. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±200 km s [−][1] (moment 0). Contours are (5, 10, 20, 30, 40,
50, 60) ×σ, where σ is 0.047 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±25 km s [−][1] . ( _Third from top_ )
Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color]
scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic
major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 41 of 52

_A&A proofs:_ manuscript no. clean


NGC 5135 Moment 0 [-150, +150] km s [1]



|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>112<br>.<br>1<br>s<br>087 km<br>.<br>(Jy<br>062 intensity<br>.<br>037<br>.<br>grated<br>012<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


(5,10,15,20,25)
× 0.049 Jy km s [1] beam [1]





13 [h] 25 [m] 44.2 [s] 43.8 [s]


Right Ascension (J2000)



5


4


3


2


1


0


5


4


3


2


1


0


80


60


40


20


0


80


60


40


20


0



NGC 5135 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 5135 (resolved) HCO [+] 3-2


Velocity (km s [1] )


NGC 5135 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 5135 (global) HCO [+] 3-2


Velocity (km s [1] )



-29°49'56"


58"


50'00"


02"


04"


-29°49'56"


58"


50'00"


02"


04"


-29°49'56"


58"


50'00"


02"


04"


|NGC 5135|Moment 1|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc||-100<br>-80<br>-60<br>-40<br>-20<br>0<br>20<br>40<br>60<br>80<br>100<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|NGC 5135|Moment 2|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc||10<br>20<br>30<br>Velocity dispersion (km s 1)|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||



50'00"


02"


04"



13 [h] 25 [m] 44.2 [s] 43.8 [s]


Right Ascension (J2000)



0



13 [h] 25 [m] 44.2 [s] 43.8 [s]


Right Ascension (J2000)


NGC 5135 HCN/HCO [+] [-150, +150] km s [1]


-29°49'56"


58"


|Col1|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
||||
||||



13 [h] 25 [m] 44.2 [s] 43.8 [s]


Right Ascension (J2000)





**Fig. A.16.** HCN 3–2 and HCO [+] 3–2 for NGC 5135. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±150 km s [−][1] (moment 0). Contours are (5, 10, 15, 20,
25) ×σ, where σ is 0.049 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ )
Velocity dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color]
scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic
major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 42 of 52

Y. Nishimura et al.: CON-quest


ESO 221-IG10 Moment 0 [-150, +150] km s [1]


|CH2NH|HC3N-vib|
|---|---|
|||


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>047<br>.<br>1<br>s<br>036 km<br>.<br>(Jy<br>026 intensity<br>.<br>016<br>.<br>grated<br>005<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3 -2|HCO+ 3 -2|Col3|100<br>80<br>60 1)<br>40 s<br>20 (km<br>0<br>Velocity<br>20<br>-<br>-40<br>60<br>-|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|HCN 3 -2|HCO+ 3 -2|Col3|30 1)<br>s<br>(km<br>20 dispersion<br>10<br>y|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||



13 [h] 50 [m] 57.1 [s] 56.9 [s] 56.8 [s]


Right Ascension (J2000)



4


3


2


1


0


4


3


2


1


0


60


40


20


0


60


40


20


0



ESO 221-IG10 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 221-IG10 (resolved) HCO [+] 3-2


Velocity (km s [1] )


ESO 221-IG10 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 221-IG10 (global) HCO [+] 3-2

|+<br>HOC<br>1000 500|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br><br><br><br><br><br>HOC +|HOC +|0<br>500<br>100|



Velocity (km s [1] )



-49°03'18"


19"


20"


21"



(5,10)
× 0.045 Jy km s [1] beam [1]



-49°03'18"


19"


20"


21"


13 [h] 50 [m] 57.1 [s] 56.9 [s] 56.8 [s]


Right Ascension (J2000)





ESO 221-IG10 Moment 1


-49°03'18"


19"


20"


21"


13 [h] 50 [m] 57.1 [s] 56.9 [s] 56.8 [s]


Right Ascension (J2000)


ESO 221-IG10 Moment 2


-49°03'18"


19"


20"


21"


13 [h] 50 [m] 57.1 [s] 56.9 [s] 56.8 [s]


Right Ascension (J2000)


ESO 221-IG10 HCN/HCO [+] [-150, +150] km s [1]



-80















**Fig. A.17.** HCN 3–2 and HCO [+] 3–2 for ESO 221−IG10. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two_
_panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±150 km s [−][1] (moment 0). Contours are (5,
10) ×σ, where σ is 0.045 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ )
Velocity dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color]
scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic
major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 43 of 52

_A&A proofs:_ manuscript no. clean


|IC 5179 Moment 0|[-200, +200] km s 1|Col3|m 1)|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2||0.12<br>0.21<br>0.29<br>0.37<br>ed intensity (Jy km s 1 bea|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|HCN 3 -2|HCO+ 3 -2|Col3|140<br>120<br>100<br>80 1)<br>60<br>s<br>40 (km<br>20<br>0<br>Velocity<br>20<br>-<br>-40<br>60<br>-<br>80<br>-<br>100|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|+<br>HOC<br>1000 500|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br><br><br><br><br><br><br>HOC +|HOC +|500<br>100|


|HCN 3 -2|HCO+ 3 -2|Col3|1)<br>s<br>30 (km<br>dispersion<br>20<br>10 ity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|CH2NH<br>1000 500|CH2NH|HC3N-vib|
|---|---|---|
|1000<br>500<br><br><br><br><br><br>CH2NH|CH2NH|500<br>100|


|Col1|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
||||



22 [h] 16 [m] 09.2 [s] 09.1 [s]


Right Ascension (J2000)



(5,10)
× 0.035 Jy km s [1] beam [1]


-140


0





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


30


20


10


0


30


20


10


0



IC 5179 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


IC 5179 (resolved) HCO [+] 3-2


Velocity (km s [1] )


IC 5179 (global) HCN 3-2


Velocity (km s [1] )


IC 5179 (global) HCO [+] 3-2

|+<br>HOC<br>1000 500|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br><br><br><br><br><br>HOC +|HOC +|500<br>100|



Velocity (km s [1] )



-36°50'36"


37"


38"


-36°50'36"


37"


38"


-36°50'36"


37"


38"



22 [h] 16 [m] 09.2 [s] 09.1 [s]


Right Ascension (J2000)



IC 5179 Moment 1


22 [h] 16 [m] 09.2 [s] 09.1 [s]


Right Ascension (J2000)


IC 5179 Moment 2



22 [h] 16 [m] 09.2 [s] 09.1 [s]


Right Ascension (J2000)


IC 5179 HCN/HCO [+] [-200, +200] km s [1]



-36°50'36"


37"


38"





**Fig. A.18.** HCN 3–2 and HCO [+] 3–2 for IC 5179. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±200 km s [−][1] (moment 0). Contours are (5, 10) ×σ,
where σ is 0.035 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ ) Velocity
dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is]
from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic major and
minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 44 of 52

Y. Nishimura et al.: CON-quest


UGC 2982 Moment 0 [-150, +150] km s [1]


5°32'51"


|HCN 3 -2|HCO+ 3 -2<br>500pc|Col3|bea<br>010<br>.<br>1<br>s<br>008 km<br>.<br>(Jy<br>006 intensity<br>.<br>003<br>.<br>grated<br>001<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3-2 UGC 2982|HCO+ 3-2  Moment 1|Col3|100|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>500 pc||-100<br>-80<br>-60<br>-40<br>-20<br>0<br>20<br>40<br>60<br>80<br>100<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||
|HCN 3-2|HCO+ 3-2<br>500 pc|||


|HCN 3-2 UGC 2982|HCO+ 3-2  Moment 2|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2||ocity dispersion (km s 1)|
|HCN 3-2|HCO+ 3-2|||



4 [h] 12 [m] 22.8 [s] 22.7 [s] 22.6 [s]


Right Ascension (J2000)



8


6


4


2


0


8


6


4


2


0


12.5


10.0


7.5


5.0


2.5


0.0


12.5


10.0


7.5


5.0


2.5


0.0



UGC 2982 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


UGC 2982 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


UGC 2982 (global) HCN 3-2



(-)
× 0.028 Jy km s [1] beam [1]



50"


49"


48"


4 [h] 12 [m] 22.8 [s] 22.7 [s] 22.6 [s]


Right Ascension (J2000)





0



5°32'51"


50"


49"


48"





4 [h] 12 [m] 22.8 [s] 22.7 [s] 22.6 [s]


Right Ascension (J2000)



5°32'51"


50"


49"


48"





4 [h] 12 [m] 22.8 [s] 22.7 [s] 22.6 [s]


Right Ascension (J2000)


UGC 2982 HCN/HCO [+] [-150, +150] km s [1]


5°32'51"



50"


49"


48"









**Fig. A.19.** HCN 3–2 and HCO [+] 3–2 for UGC 2982. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected

|5|H|Col3|
|---|---|---|
||CH2NH|CH2NH|
|1000<br>500<br>0<br>Velocity (k<br><br><br><br><br><br><br>HOC +<br>UGC 2982 (glob|1000<br>500<br>0<br>Velocity (k<br><br><br><br><br><br><br>HOC +<br>UGC 2982 (glob|1000<br>500<br>0<br>Velocity (k<br><br><br><br><br><br><br>HOC +<br>UGC 2982 (glob|
|1000<br>500<br>0<br>Velocity (k<br><br><br><br><br><br><br>HOC +<br>UGC 2982 (glob||HOC +|
|1000<br>500<br>0<br>Velocity (k<br><br> HCN 3–2 and HCO+ 3<br>tracted from the global|1000<br>500<br>0<br>Velocity (k<br><br> HCN 3–2 and HCO+ 3<br>tracted from the global|1000<br>500<br>0<br>Velocity (k<br><br> HCN 3–2 and HCO+ 3<br>tracted from the global|

species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±150 km s [−][1] (moment 0). No emission is found above
5σ threshold. ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ ) Velocity dispersion (moment 2).
Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is from 0.285 to 3.5. Overlaid]
ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic major and minor axes, respectively. The
synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 45 of 52

_A&A proofs:_ manuscript no. clean


NGC 2369 Moment 0 [-300, +300] km s [1]



|HCN 3 -2|HCO+ 3 -2<br>100pc|Col3|bea<br>196<br>.<br>1<br>s<br>152 km<br>.<br>(Jy<br>109 intensity<br>.<br>065<br>.<br>grated<br>022<br>.|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||


(5,10,15,20,25,30,35)
× 0.056 Jy km s [1] beam [1]





6


4


2


0


6


4


2


0


60


40


20


0


60


40


20


0



NGC 2369 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 2369 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 2369 (global) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


NGC 2369 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


|NGC 2369|Moment 1|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>100 pc||-200<br>-150<br>-100<br>-50<br>0<br>50<br>100<br>150<br>200<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||


|NGC 2369|Moment 2|Col3|Col4|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2<br>100 pc||25<br>50<br>75<br>Velocity dispersion (km s 1)|
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||
|HCN 3-2|HCO+ 3-2<br>100 pc|||



-62°20'34"


36"


38"


40"



-62°20'34"


36"


38"


40"


-62°20'34"


36"


38"


40"


-62°20'34"


36"


38"


40"



7 [h] 16 [m] 38.0 [s] 37.6 [s] 37.4 [s] 37.2 [s]


Right Ascension (J2000)



7 [h] 16 [m] 38.0 [s] 37.6 [s] 37.4 [s] 37.2 [s]


Right Ascension (J2000)



0



7 [h] 16 [m] 38.0 [s] 37.6 [s] 37.4 [s] 37.2 [s]


Right Ascension (J2000)


NGC 2369 HCN/HCO [+] [-300, +300] km s [1]


|Col1|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
||||
||||



7 [h] 16 [m] 38.0 [s] 37.6 [s] 37.4 [s] 37.2 [s]


Right Ascension (J2000)





**Fig. A.20.** HCN 3–2 and HCO [+] 3–2 for NGC 2369. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±300 km s [−][1] (moment 0). Contours are (5, 10, 15, 20, 25,
30, 35) ×σ, where σ is 0.056 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±25 km s [−][1] . ( _Third from top_ )
Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color]
scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic
major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 46 of 52

Y. Nishimura et al.: CON-quest


ESO 286-G035 Moment 0 [-200, +200] km s [1]


|HCN 3 -2|HCO+ 3 -2|Col3|bea<br>049<br>.<br>1<br>s<br>038 km<br>.<br>(Jy<br>027 intensity<br>.<br>016<br>.<br>d|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|Col1|CH2NH|HC3N-vib|
|---|---|---|
|1000<br>500<br> <br>|1000<br>500<br> <br>|0<br>500<br>1000<br>|


|ESO 286-G03|35 Moment 1|Col3|Col4|150|
|---|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||-100<br>-50<br>0<br>50<br>100<br>150<br>Velocity (km s 1)|
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||


|+<br>HOC<br>1000 500|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br> <br><br><br><br><br>HOC +|HOC +|0<br>500<br>1000<br> 1|


|HCN 3 -2|HCO+ 3 -2|Col3|Col4|1)<br>s<br>(km<br>dispersion<br>25<br>locity|
|---|---|---|---|---|
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||
|HCN 3-2|HCO+ 3-2||||


|Col1|CH2NH|HC3N-vib|
|---|---|---|
|1000<br>500<br><br>|1000<br>500<br><br>|0<br>500<br>1000<br>|



37"

|Col1|Col2|30<br>.<br>HCO +<br>20<br>. HCN/L<br>L<br>10<br>.|
|---|---|---|
||||
||||



21 [h] 04 [m] 11.3 [s] 11.2 [s] 11.1 [s] 11.0 [s]


Right Ascension (J2000)



(5,10)
× 0.037 Jy km s [1] beam [1]







1.5


1.0


0.5


0.0


1.5


1.0


0.5


0.0


25


20


15


10


5


0


25


20


15


10


5


0



ESO 286-G035 (resolved) HCN 3-2


Velocity (km s [1] )


ESO 286-G035 (resolved) HCO [+] 3-2


Velocity (km s [1] )


ESO 286-G035 (global) HCN 3-2


Velocity (km s [1] )


ESO 286-G035 (global) HCO [+] 3-2

|Col1|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br>|1000<br>500<br>|0<br>500<br>1000|



Velocity (km s [1] )



-43°35'34"


35"


36"


37"



21 [h] 04 [m] 11.3 [s] 11.2 [s] 11.1 [s] 11.0 [s]


Right Ascension (J2000)



-43°35'34"


35"


36"


37"



ESO 286-G035 Moment 1



-150


0



21 [h] 04 [m] 11.3 [s] 11.2 [s] 11.1 [s] 11.0 [s]


Right Ascension (J2000)


ESO 286-G035 Moment 2





-43°35'34"


35"


36"


37"





21 [h] 04 [m] 11.3 [s] 11.2 [s] 11.1 [s] 11.0 [s]


Right Ascension (J2000)


ESO 286-G035 HCN/HCO [+] [-200, +200] km s [1]


-43°35'34"


35"


36"





**Fig. A.21.** HCN 3–2 and HCO [+] 3–2 for ESO 286−G035. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two_
_panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±200 km s [−][1] (moment 0). Contours are (5,
10) ×σ, where σ is 0.037 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±25 km s [−][1] . ( _Third from top_ )
Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color]
scale is from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic
major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 47 of 52

_A&A proofs:_ manuscript no. clean


ESO 320-G030 Moment 0 [-300, +300] km s [1]


|CH2NH|HC3N-vib|
|---|---|
|||


|+ HOC|HCN-vib CH3OH|
|---|---|
|||


|ESO 320-G030|(global) HCN 3-2|
|---|---|
|CH2NH|HC3N-vib|
|||


|+ HOC|HCN-vib CH3OH|
|---|---|
|||



11 [h] 53 [m] 11.9 [s] 11.7 [s] 11.6 [s]


Right Ascension (J2000)











60


40


20


0


60


40


20



ESO 320-G030 (resolved) HCN 3-2


1000 500 0 500 1000

Velocity (km s [1] )


ESO 320-G030 (resolved) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )


1000 500 0 500 1000

Velocity (km s [1] )


ESO 320-G030 (global) HCO [+] 3-2


1000 500 0 500 1000

Velocity (km s [1] )



-39°07'47"


48"


49"


50"


51"



-39°07'47"


48"


49"


50"


51"



11 [h] 53 [m] 11.9 [s] 11.7 [s] 11.6 [s]


Right Ascension (J2000)



(5,10,20,40,80,160,240,320,400)

× 0.050 Jy km s [1] beam [1]





ESO 320-G030 Moment 1









0


400



11 [h] 53 [m] 11.9 [s] 11.7 [s] 11.6 [s]


Right Ascension (J2000)


ESO 320-G030 Moment 2







300


200







100


0



-39°07'47"


48"


49"


50"


51"







11 [h] 53 [m] 11.9 [s] 11.7 [s] 11.6 [s]


Right Ascension (J2000)


ESO 320-G030 HCN/HCO [+] [-300, +300] km s [1]


-39°07'47"





400


300





200


100


0



48"


49"


50"


51"







**Fig. A.22.** HCN 3–2 and HCO [+] 3–2 for ESO 320−G030. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two_
_panels_ ) Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially
detected species are indicated by vertical dotted lines. _Right panels_ : ( _Top_ ) Integrated intensity over ±300 km s [−][1] (moment 0). Contours are (5, 10,
20, 40, 80, 160, 240, 320, 400) ×σ, where σ is 0.050 Jy km s [−][1] beam [−][1] . ( _Second_ _from_ _top_ ) Velocity field (moment 1). Contours are in steps of
±25 km s [−][1] . ( _Third from top_ ) Velocity dispersion (moment 2). Contours are in steps of 10 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping.
( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [.] [Color] [scale] [is] [from] [0.285] [to] [3.5.] [Overlaid] [ellipses] [represent] [the] [apertures] [used] [for] [spectral] [extraction.] [Solid] [and] [dashed]
lines represent the kinematic major and minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 48 of 52

Y. Nishimura et al.: CON-quest


NGC 5734 Moment 0 [-150, +150] km s [1]


|HCN 3 -2|HCO+ 3 -2|Col3|bea<br>031<br>.<br>1<br>s<br>024 km<br>.<br>(Jy<br>017 intensity<br>.<br>010<br>.<br>ed|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|CH2NH<br>1000 500|CH2NH|HC3N-vib|
|---|---|---|
|1000<br>500<br><br><br><br><br><br><br>CH2NH|CH2NH|0<br>500<br>1000|


|HCN 3 -2|HCO+ 3 -2|Col3|100<br>80<br>60 1)<br>40 s<br>20 (km<br>0<br>Velocity<br>20<br>-<br>-40<br>60<br>-<br>80<br>-|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|Col1|+ HOC|HCN-vib CH3OH|
|---|---|---|
|1000<br>500<br><br>Velocity<br>|1000<br>500<br><br>Velocity<br>|0<br>500<br>1000<br> (km s 1)|


|HCN 3 -2|HCO+ 3 -2|Col3|30 1)<br>s<br>(km<br>dispersion<br>20<br>10 ocity|
|---|---|---|---|
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||
|HCN 3-2|HCO+ 3-2|||


|Col1|CH2NH|HC3N-vib|
|---|---|---|
|1000<br>500<br><br>Velocity<br><br>|1000<br>500<br><br>Velocity<br><br>|0<br>500<br>1000<br> (km s 1)<br>|



14 [h] 45 [m] 09.1 [s] 09.0 [s] 08.9 [s]


Right Ascension (J2000)



(5,10)
× 0.032 Jy km s [1] beam [1]





14 [h] 45 [m] 09.1 [s] 09.0 [s] 08.9 [s]


Right Ascension (J2000)



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


20


15


10


5


0


20


15


10


5


0



NGC 5734 (resolved) HCN 3-2


Velocity (km s [1] )


NGC 5734 (resolved) HCO [+] 3-2


NGC 5734 (global) HCN 3-2


NGC 5734 (global) HCO [+] 3-2



-20°52'12"


13"


14"


15"


-20°52'12"


13"


14"


15"


-20°52'12"


13"


14"


15"



-20°52'12"


13"


14"


15"



NGC 5734 Moment 1


14 [h] 45 [m] 09.1 [s] 09.0 [s] 08.9 [s]


Right Ascension (J2000)


NGC 5734 Moment 2



0



14 [h] 45 [m] 09.1 [s] 09.0 [s] 08.9 [s]


Right Ascension (J2000)


NGC 5734 HCN/HCO [+] [-150, +150] km s [1]









**Fig. A.23.** HCN 3–2 and HCO [+] 3–2 for NGC 5734. _Left panels_ : ( _Top two panels_ ) Spectra extracted from the resolved aperture. ( _Lower two panels_ )
Spectra extracted from the global aperture. Velocities are relative to the systemic velocity. The corresponding velocities of potentially detected
species are indicated by vertical dotted lines. _Right_ _panels_ : ( _Top_ ) Integrated intensity over ±150 km s [−][1] (moment 0). Contours are (5, 10) ×σ,
where σ is 0.026 Jy km s [−][1] beam [−][1] . ( _Second from top_ ) Velocity field (moment 1). Contours are in steps of ±10 km s [−][1] . ( _Third from top_ ) Velocity
dispersion (moment 2). Contours are in steps of 4 km s [−][1] . Moment 1 and 2 were derived with 3σ clipping. ( _Bottom_ ) _L_ HCN [′] [/] _[L]_ HCO [′] [+] [. Color scale is]
from 0.285 to 3.5. Overlaid ellipses represent the apertures used for spectral extraction. Solid and dashed lines represent the kinematic major and
minor axes, respectively. The synthesized beam is indicated by hatched ellipses in the lower right corners.


Article number, page 49 of 52

_A&A proofs:_ manuscript no. clean



IRAS 17208-0014



IRAS 09022-3615



IRAS 13120-5453



IRAS F14378-3651



400


200


0


200


400



400


200


0


200


400

1.0
0.5 [0.0]
1.0







400


200


0


200


400


400


200


0


200


400



0.5
1.0



1.0 0.5 0.0 0.5 1.0



1.0



0.5



0.0
0.5







IRAS F05189-2524



1.00.50.00.51.0



IRAS F10565+2448



IRAS 19542+1110



ESO 148-IG002



0.5





1.0 0.5 [0.0] 0.5 1.0



400


200


0


200


400



400


200


0


200


400


400


200


0


200


400


400


200


0


200


400


400


200


0


200


400


400


200


0


200


400



0.5



400


200


0


200


400



0.5 0.0 0.5









0.0
0.5





0.5



0.5



NGC 6240


400


200


0


200


400


NGC 3110


400


200


0



IRAS F17138-1017



IRAS 17578-0400



400


200


0


200


400


1.0



0.5
1.0



ESO 173-G015


2.01.51.00.50.00.51.01.52.02.01.5 [1.00.50.00.51.01.52.0]


ESO 221-IG10



400


200


0


200


400

1.0
0.5 [0.0]
1.0



1.0 0.5 0.0 0.5 1.0





0.5



1.0



2



1.0
0.5

0.51.01.0 0.5 0.0 0.5 1.0


ESO 320-G030



NGC 5135


2 1 0 1 2



400


200


0


200


400



IC 4734


1.51.00.50.0 0.5 1.0 1.5



400


200


0


200


400


1.5 [1.00.5]



0.5
0.0
0.5



0.5 0.0 0.5



200


400


400


200


0


200


400





IC 5179


0.0

0.5



NGC 2369



ESO 286-G035



0.5
1.0



1.0 0.5 [0.0] 0.5 1.0



400


200


0


200


400

1.0
0.5 [0.0]
1.0



1.00.50.00.51.0









400


200


0


200


400





0.5



1.0 2.0 3.0

L HCN /L HCO [+]


**Fig.** **B.1.** Visualization of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in] [the] [position-position-velocity] [space.] [The] [whole] [sample] [except] [for] [UGC 11763,] [UGC 2982,] [and]
NGC 5734 are presented. Each spaxel has a size of 0.05 [′′] × 0.05 [′′] × 20 km s [−][1] . A 3σ threshold clipping for both HCN and HCO [+] was applied. We
only consider spaxels with the global aperture (see Sect. 4.1) and with the velocity range listed in Table 4.3. The colors represent _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in]
the range from 0.285 (blueish) to 3.5 (red-pinkish).



8. _ESO 148_ − _IG002:_ Our data show that _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is] [rela-]
tively low throughout the galaxy (∼0.4 on average and ∼1 at
the maximum; see Table 6). Although no molecular out- or
inflows are known in this galaxy so far, the highest 10th percentile in _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is in the form of a thin spherical shell]
with a radius of ∼500 pc and in a velocity range of about


Article number, page 50 of 52



±20 km s [−][1], possibly suggesting the presence of a symmetrically shaped non-circular motion.
9. _NGC 6240:_ Due to the interaction between the two nuclei,
the kinematic structure of NGC 6240 appears to be quite
complicated. The presence of outflows launched from each
of the two nuclei was revealed by a detailed analysis of CO
and [C i] lines (Cicone et al. 2014, 2018; Saito et al. 2018)

Y. Nishimura et al.: CON-quest



IRAS 17208-0014



IRAS 09022-3615



IRAS 13120-5453



IRAS F14378-3651



400


200


0


200


400



400


200


0


200


400

1.0
0.5 [0.0]
1.0







400


200


0


200


400


400


200


0


200


400



0.5
1.0



1.0 0.5 0.0 0.5 1.0



1.0



0.5



0.0
0.5







IRAS F05189-2524



1.00.50.00.51.0



IRAS F10565+2448



IRAS 19542+1110



ESO 148-IG002



0.5





1.0 0.5 [0.0] 0.5 1.0



400


200


0


200


400



400


200


0


200


400


400


200


0


200


400


400


200


0


200


400


400


200


0


200


400


400


200


0


200


400



0.5



400


200


0


200


400



0.5 0.0 0.5









0.0
0.5





0.5



0.5



NGC 6240


400


200


0


200


400


NGC 3110


400


200


0



IRAS F17138-1017



IRAS 17578-0400



400


200


0


200


400


1.0



0.5
1.0



ESO 173-G015


2.01.51.00.50.00.51.01.52.02.01.5 [1.00.50.00.51.01.52.0]


ESO 221-IG10



400


200


0


200


400

1.0
0.5 [0.0]
1.0



1.0 0.5 0.0 0.5 1.0





0.5



1.0



2



1.0
0.5

0.51.01.0 0.5 0.0 0.5 1.0


ESO 320-G030



NGC 5135


2 1 0 1 2



400


200


0


200


400



IC 4734


1.51.00.50.0 0.5 1.0 1.5



400


200


0


200


400


1.5 [1.00.5]



0.5
0.0
0.5



0.5 0.0 0.5



200


400


400


200


0


200


400





IC 5179


0.0

0.5



NGC 2369



ESO 286-G035



0.5
1.0



1.0 0.5 [0.0] 0.5 1.0



400


200


0


200


400

1.0
0.5 [0.0]
1.0



1.00.50.00.51.0









400


200


0


200


400





0.5



1.0 2.0 3.0

L HCN /L HCO [+]


**Fig. B.2.** Same as Fig. B.1 but presenting spaxels with _L_ HCN [′] [/] _[L]_ HCO [′] [+] [above the 90th percentile.]



and an OH absorption feature (Veilleux et al. 2013). The
high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions are, however, rather randomly dis-]
tributed over the entire system. We think this could be because of the disturbance by the merger.


The CO and H 2 line analysis (Meijerink et al. 2013) revealed that a large fraction of the gas traced by the CO
_J_ =4–3 through 13–12 lines is affected by slow shocks,
while only ≲1% traced by the H 2 v=1–0 _S_ (1) and v=2–
1 _S_ (1) lines is exposed to the high-velocity shocks (∼17–



47 km s [−][1] ). Hence the shock velocity is slow (≲10 km s [−][1] ) in
the greater part of the system, no matter whether the shock
is caused by a merger and/or the outflows. The shock velocity of ≲10 km s [−][1] is insufficient for HCN enhancement (see
Sect. 6.2 for dependencies of HCN enhancement on shock
velocity).


10. _IRAS F17138_ − _1017:_ No dedicated study of the molecular
gas distribution and kinematics was found for this galaxy.
The spatial distribution of HCO [+] and HCN appears to be


Article number, page 51 of 52

_A&A proofs:_ manuscript no. clean



highly asymmetric and different between these two species.
While the HCO [+] emission has a second peak ∼700 pc to the
south of the kinematic center, the HCN emission does not.
Our results suggest that there are multiple components that
have different chemical compositions in the system, although
we cannot specify the physical origin of the chemical diversity.
11. _IRAS 17578_ − _0400:_ For this galaxy, the analysis of the
OH line profile suggests the presence of inflowing gas at
∼30 km s [−][1] (Paper I). The elongation of the HCN and HCO [+]
emission at low velocity may hint at an outflow along its
kinematic minor axis (Paper I; Yang et al. 2023), as mentioned in Sect. 4.1. Because of the difficulty in continuum
subtraction due to the line forest, it is hard to quantitatively
discuss _L_ HCN [′] [/] _[L]_ HCO [′] [+] [on] [a] [spaxel-by-spaxel] [basis.] [We] [ten-]
tatively analyzed _L_ HCN [′] [/] _[L]_ HCO [′] [+] [without] [continuum] [subtrac-]
tion, but it is difficult to robustly conclude that the high
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions are related to the out- and][/][or inflows. To]

−
further investigate the kinematics of IRAS 17578 0400, we
have conducted higher spatial resolution observations with
ALMA. The detailed analysis of this observation will be presented in another paper (Yang et al., in prep.).
12. _ESO 173_ − _G015:_ Although we did not find any publication
on the presence of out- or inflows in this galaxy, the high
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions were found in a symmetric shape. If we]
pick up the spaxels with ratios higher than the 97th percentile
(>1.402), they appear more distinctly in a thin shell. Conducting a more detailed kinematic analysis would be worthwhile in order to see if there are any outflows.
13. _UGC 11763:_ No publication on outflow signatures was
found for this galaxy. The HCN and HCO [+] emission is too
faint and compact to inspect the line ratio on a spaxel-byspaxel basis. The linewidths of the HCN and HCO [+] lines
seem to be much narrower than that of the CO 2–1 line (e.g.,
Montoya Arroyave et al. 2023, the galaxy is referred to as
PG2130+099), suggesting that higher sensitivity and higher
spatial resolution would be needed to grasp the molecular
composition in the extended diffuse gas.
14. _NGC 3110:_ The presence of a large-scale (≳ a few kiloparsecs) inflow is suggested by CO line observations (Kawana
et al. 2022), but it is on much larger scales and not comparable to the HCN and HCO [+] line-emitting region of our data.
We note that _L_ HCN [′] [/] _[L]_ HCO [′] [+] [shows] [some] [variation] [in] [the] [ppV]
space, but its structure is not very symmetrical.
15. _IC 4734:_ We did not find any published out- or inflow signatures. _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is distributed rather uniformly throughout]
the galaxy.
16. _NGC 5135:_ There are no known molecular out- or inflows in
this galaxy. High _L_ HCN [′] [/] _[L]_ HCO [′] [+] [can] [be] [seen] [in] [some] [limited]
small regions, but it is hard to characterize their geometry.
17. _ESO 221_ − _IG10:_ No out- or inflow signature is known for this
galaxy. A slight enhancement of _L_ HCN [′] [/] _[L]_ HCO [′] [+] [can be seen in]
the central region, but it is only present on the blueshifted
side. Higher sensitivity observations and detailed analysis of
kinematics would be advisable.
18. _IC 5179:_ For this galaxy, we found no published signature of
out- or inflows. There are some spots where _L_ HCN [′] [/] _[L]_ HCO [′] [+] [is]
elevated, but they appear rather random.
19. _UGC 2982:_ No publication on an out- or inflow signature
was found. The HCN and HCO [+] emission is too faint to
make any meaningful discussion.
20. _NGC 2369:_ Although there is no published out- or inflow signature, the high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions] [are] [concentrated] [in] [a]
few 100 pc regions at the center of the galaxy. It would be
worth investigating the origin of this concentration.


Article number, page 52 of 52



21. _ESO 286_ − _G035:_ We did not find any publication on outflows
in this galaxy. Moreover, _L_ HCN [′] [/] _[L]_ HCO [′] [+] [does] [not] [vary] [much]
and is almost uniformly distributed throughout the galaxy.
22. _ESO 320_ − _G030:_ In this galaxy, a high-velocity (450 km s [−][1] )
molecular outflow was identified by high spatial resolution observation of the CO 2–1 line (Pereira-Santaella et al.
2016). The kinematic analysis of the cited study showed
that the outflow has a size of 2.5 kpc and that its blue- and
redshifted regions lie in the northeast and southwest of the
nucleus, respectively. Furthermore, González-Alfonso et al.
(2021) found a molecular inflow associated with the nuclear
bar, which is traced by the CO 2–1 line at the radius of 230–
460 pc. They also pointed out that OH absorption features
indicate the presence of inflowing gas at radii of 100–150 pc.
We note that _L_ HCN [′] [/] _[L]_ HCO [′] [+] [largely] [varies] [over] [the] [galaxy] [in]
the form of a characteristic structure. Most notably, the high
_L_ HCN [′] [/] _[L]_ HCO [′] [+] [regions] [shape] [a] [thin] [spherical] [shell] [with] [a] [ra-]
dius of ∼100 pc. The velocity of the structure is roughly consistent with the inflows traced by the OH lines, indicating
that HCN enhancement could be associated with these inflows. On the other hand, the high-velocity outflow found by
Pereira-Santaella et al. (2016) is not obvious in _L_ HCN [′] [/] _[L]_ HCO [′] [+]
in a spectrally resolved manner, but this is simply because we
cannot calculate the ratio due to the faintness of the HCO [+]
line at high velocities. In the velocity-integrated ratio map,
we may have got a hint of the enhanced _L_ HCN [′] [/] _[L]_ HCO [′] [+] [in the]
outflow (Fig. A.22). The northeastern part of the outflow exhibits a considerably high _L_ HCN [′] [/] _[L]_ HCO [′] [+] [(][≳][3), and the south-]
western part also shows a moderately enhanced line ratio.
Our subsequent ALMA observation with higher sensitivity
and higher spatial resolution has clearly revealed the signature of outflow in the HCN line, and it will be presented in
another paper (Gorski in prep.).
23. _NGC 5734:_ No published out- or inflow signature was found.
We cannot discuss _L_ HCN [′] [/] _[L]_ HCO [′] [+] [due] [to] [the] [faintness] [of] [the]
HCO [+] emission over the galaxy.


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "Pre-shock: n_H2 = 10^3 cm^-3, T = 10 K, A_V = 2 mag, radiation field = 1 Habing, cosmic-ray ionization rate = 1.3 x 10^-17 s^-1, duration = 10^5 yr; Post-shock: v_shock = 10, 20, 30, 40 km s^-1",
  "failed_quote": "The chemical evolution was followed for 10 [5] yr in the pre-shock phase to reproduce realistic molecular abundances observed on cloud scales (>10 pc; Harada et al. 2019). In the post-shock phase, we tested four values of shock velocity: 10, 20, 30, and 40 km s [−][1] ."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "Global and resolved HCN/HCO+ line ratios show no statistically significant correlation with AGN fraction, bolometric AGN luminosity, infrared luminosity, star formation rate, or dust temperature.",
  "failed_quote": "We found no apparent correlations between L HCN [′] [/] [L] HCO [′] [+] [and any of the galaxy properties."
 }
]
```
