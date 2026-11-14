# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...706A..27S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2025
December 11, 2025

## **Probing jet base emission of M87* with the 2021** **Event Horizon Telescope observations**


Saurabh 1, Hendrik Müller 2, Sebastiano D. von Fellenberg 3, 1, Paul Tiede 4, 5, Michael Janssen 6, 1, Lindy Blackburn 4, 5, Avery E. Broderick 7, 8, 9,
Erandi Chavez [4], Boris Georgiev 10, Thomas P. Krichbaum 1, Kotaro Moriyama 11, 12, Dhanya G. Nair 25, 1, Iniyan Natarajan 4, 5, Jongho Park 13, 14,
Andrew Thomas West [10], Maciek Wielgus 15

The Event Horizon Telescope Collaboration
Kazunori Akiyama 16, 17, 5, Ezequiel Albentosa-Ruíz 18, Antxon Alberdi 15, Walter Alef 1, Juan Carlos Algaba 19, Richard Anantua 20, 21, 5, 4, Keiichi
Asada 14, Rebecca Azulay 18, 22, 1, Uwe Bach 1, Anne-Kathrin Baczko 23, 1, David Ball 10, Mislav Balokovi´c 24, Bidisha Bandyopadhyay 25, John
Barrett 16, Michi Bauböck 26, Bradford A. Benson 27, 28, Dan Bintley 29, 30, Raymond Blundell 4, Katherine L. Bouman 31, Geoffrey C.
Bower 29, 30, 32, 33, Michael Bremer 34, Roger Brissenden 4, Silke Britzen 1, Dominique Broguiere 34, Thomas Bronzwaer 6, Sandra Bustamante 35,
Douglas F. Carlos 36, John E. Carlstrom 37, 28, 38, 39, Andrew Chael 40, Chi-kwan Chan 10, 41, 42, Dominic O. Chang 4, 5, Koushik Chatterjee 43, 5, 4, Shami
Chatterjee 44, Ming-Tang Chen 32, Yongjun Chen ( `陈永军` ) 45, 46, Xiaopeng Cheng 47, Paul Chichura 38, 37, Ilje Cho 47, 48, 15, Pierre Christian 49,
Nicholas S. Conroy 50, 4, John E. Conway 23, Thomas M. Crawford 28, 37, Geoffrey B. Crew 16, Alejandro Cruz-Osorio 51, 11, Yuzhu Cui ( `崔玉竹` ) 52,
Brandon Curd 20, 5, 4, Rohan Dahale 15, Jordy Davelaar 53, 54, Mariafelicia De Laurentis 55, 56, Roger Deane 57, 58, 59, Gregory Desvignes 1, 60, Jason
Dexter 61, Vedant Dhruv 26, Indu K. Dihingia 62, Sheperd S. Doeleman 4, 5, Sergio A. Dzib 1, Ralph P. Eatough 63, 1, Razieh Emami 4, Heino
Falcke 6, Joseph Farah 64, 65, Vincent L. Fish 16, Edward Fomalont 66, H. Alyson Ford 10, Marianna Foschi 15, Raquel Fraga-Encinas 6, William T.
Freeman [67][,][ 68], Per Friberg 29, 30, Christian M. Fromm 69, 11, 1, Antonio Fuentes 15, Peter Galison 5, 70, 71, Charles F. Gammie 26, 50, 72, Roberto García 34,
Olivier Gentaz 34, Ciriaco Goddi 36, 73, 74, 75, Roman Gold 76, 77, 78, Arturo I. Gómez-Ruiz 79, 80, José L. Gómez 15, Minfeng Gu ( `顾敏峰` ) 45, 81, Mark
Gurwell 4, Kazuhiro Hada 82, 12, Daryl Haggard 83, 84, Ronald Hesper 85, Dirk Heumann 10, Luis C. Ho ( `何子山` ) 86, 87, Paul Ho 14, 30, 29, Mareki
Honma 12, 88, 89, Chih-Wei L. Huang 14, Lei Huang ( `黄磊` ) 45, 81, David H. Hughes 79, Shiro Ikeda 17, 90, 91, 92, C. M. Violette Impellizzeri 93, 66, Makoto
Inoue 14, Sara Issaoun 4, 54, David J. James 94, 95, Buell T. Jannuzi 10, Britton Jeter 14, Wu Jiang ( `江悟` ) 45, Alejandra Jiménez-Rosales 6, Michael D.
Johnson 4, 5, Svetlana Jorstad 96, Adam C. Jones 28, Abhishek V. Joshi 26, Taehyun Jung 47, 97, Ramesh Karuppusamy 1, Tomohisa Kawashima 98,
Garrett K. Keating 4, Mark Kettenis 99, Dong-Jin Kim 100, Jae-Young Kim 101, Jongsoo Kim 47, Junhan Kim 102, Motoki Kino 17, 103, Jun Yi
Koay 104, 14, Prashant Kocherlakota 5, 4, Yutaro Kofuji 12, 89, Patrick M. Koch 14, Shoko Koyama 104, 14, Carsten Kramer 34, Joana A. Kramer 1, Michael
Kramer 1, Cheng-Yu Kuo 105, 14, Noemi La Bella 6, Deokhyeong Lee 106, Sang-Sung Lee 47, Aviad Levis 31, Shaoliang Li 29, 30, Zhiyuan Li ( `李志`
`远` ) 107, 108, Rocco Lico 109, 15, Greg Lindahl 110, Michael Lindqvist 23, Mikhail Lisakov 111, Jun Liu ( `刘俊` ) 1, Kuo Liu 45, 46, Elisabetta Liuzzo 112,
Wen-Ping Lo 14, 113, Andrei P. Lobanov 1, Laurent Loinard 114, 5, 115, Colin J. Lonsdale 16, Amy E. Lowitz 10, Ru-Sen Lu ( `路如森` ) 45, 46, 1, Nicholas R.
MacDonald 1, Jirong Mao ( `毛基荣` ) 116, 117, 118, Nicola Marchili 112, 1, Sera Markoff 119, 120, Daniel P. Marrone 10, Alan P. Marscher 96, Iván
Martí-Vidal 18, 22, Satoki Matsushita 14, Lynn D. Matthews 16, Lia Medeiros 121, Karl M. Menten 1, 122⋆, Hugo Messias 123, 124, Izumi Mizuno 29, 30,
Yosuke Mizuno 62, 125, 11, Joshua Montgomery 84, 28, James M. Moran 4, 5, Monika Moscibrodzka 6, Wanga Mulaudzi 119, Cornelia Müller 1, 6,
Alejandro Mus 73, 109, 126, 127, Gibwa Musoke 119, 6, Ioannis Myserlis 128, Hiroshi Nagai 17, 88, Neil M. Nagar 25, Masanori Nakamura 129, 14, Gopal
Narayanan 35, Antonios Nathanail 130, 11, Santiago Navarro Fuentes 128, Joey Neilsen 131, Chunchong Ni 8, 9, 7, Michael A. Nowak 132, Junghwan Oh 99,
Hiroki Okino 12, 89, Héctor Raúl Olivares Sánchez 133, Tomoaki Oyama 12, Feryal Özel 134, Daniel C. M. Palumbo 5, 4, Georgios Filippos Paraschos 1,
Harriet Parsons 29, 30, Nimesh Patel 4, Ue-Li Pen 14, 7, 3, 135, 136, Dominic W. Pesce 4, 5, Vincent Piétu 34, Alexander Plavin 5, 4, 1, Aleksandar PopStefanija 35,
Oliver Porth 119, 11, Ben Prather 26, Giacomo Principe 137, 138, 109, Dimitrios Psaltis 134, Hung-Yi Pu 139, 140, 14, Alexandra Rahlin 28, Venkatessh
Ramakrishnan 25, 141, 142, Ramprasad Rao 4, Mark G. Rawlings 143, 29, 30, Luciano Rezzolla 11, 144, 145, Angelo Ricarte 5, 4, Luca Ricci 146, Bart
Ripperda 3, 147, 135, 7, Jan Röder 15, Freek Roelofs 6, Cristina Romero-Cañizales 14, Eduardo Ros 1, Arash Roshanineshat 10, Helge Rottmann 1, Alan L.
Roy 1, Ignacio Ruiz 128, Chet Ruszczyk 16, Kazi L. J. Rygl 112, León D. S. Salas 119, Salvador Sánchez 128, David Sánchez-Argüelles 79, 80, Miguel
Sánchez-Portal 128, Mahito Sasada 148, 12, 149, Kaushik Satapathy 10, Tuomas Savolainen 150, 142, 1, F. Peter Schloerb 35, Jonathan Schonfeld 4,
Karl-Friedrich Schuster 34, Lijing Shao 87, 1, Zhiqiang Shen ( `沈志强` ) 45, 46, Sasikumar Silpa 25, Des Small 99, Randall Smith 4, Bong Won
Sohn 47, 97, 48, Jason SooHoo 16, Kamal Souccar 35, Joshua S. Stanway 151, He Sun ( `孙赫` ) 152, 153, Fumie Tazaki 154, Alexandra J. Tetarenko 155,
Remo P. J. Tilanus 10, 6, 93, 156, Michael Titus 16, Kenji Toma 157, 158, Pablo Torne 128, 1, Teresa Toscano 15, Efthalia Traianou 15, 1, Tyler Trent 10, Sascha
Trippe 159, 160, Matthew Turk 50, Ilse van Bemmel 161, Huib Jan van Langevelde 99, 93, 162, Daniel R. van Rossum 6, Jesse Vos 163, Jan Wagner 1, Derek
Ward-Thompson 151, John Wardle 164, Jasmin E. Washington 10, Jonathan Weintroub 4, 5, Robert Wharton 1, Kaj Wiik 165, 141, 142, Gunther Witzel 1,
Michael F. Wondrak 6, 166, George N. Wong 167, 40, Jompoj Wongphexhauxsorn 146, 1, Qingwen Wu ( `吴庆文` ) 168, Nitika Yadlapalli 31, Paul
Yamaguchi 4, Aristomenis Yfantis 6, Doosoo Yoon 119, André Young 6, Ziri Younsi 169, 11, Wei Yu ( `于威` ) 4, Feng Yuan ( `袁峰` ) 170, Ye-Fei Yuan ( `袁业`
`飞` ) 171, Ai-Ling Zeng ( `曾艾玲` ) 15, J. Anton Zensus 1, Shuo Zhang 172, Guang-Yao Zhao 1, 15, and Shan-Shan Zhao ( `赵杉杉` ) 45


_(A_ ffi _liations can be found after the references)_


December 11, 2025


**ABSTRACT**


We investigate the presence and spatial characteristics of the jet base emission in M87* at 230 GHz, enabled by the significantly enhanced
( _u_, v) coverage in the 2021 Event Horizon Telescope (EHT) observations. The integration of the 12−m Kitt Peak Telescope (USA) and NOEMA

−
(France) stations into the array introduces two critical intermediate-length baselines to SMT (USA) and IRAM 30 m (Spain), providing sensitivity
to emission structures at spatial scales of ∼ 250 µas and ∼ 2500 µas (∼ 0.02 pc and ∼ 0.2 pc). Without these new baselines, previous EHT
observations of the source in 2017 and 2018 lacked the capability to constrain emission on large scales, where a “missing flux" of order ∼ 1 Jy


Article number, page 1

_A&A proofs:_ manuscript no. main


is expected to reside. To probe these scales, we analyzed closure phases—robust against station-based gain calibration errors—and model the jet
base emission using a simple Gaussian component offset from the compact ring emission at spatial separations > 100 µas. Our analysis revealed
a Gaussian feature centered at (∆R.A. ≈ 320 µas, ∆Dec. ≈ 60 µas), projected separation of ≈ 5500 AU, with an estimated flux density of only

∼
60 mJy, implying that most of the missing flux identified in previous EHT studies had to originate from different, larger scales. Brighter emission
at the relevant spatial scales is firmly ruled out, and the data do not favor more complex models. This component aligns with the inferred position of
the large-scale jet and is therefore physically consistent with the emission of the jet base. While our findings point to detectable jet base emission at
230 GHz, the limited coverage provided by only two intermediate baselines limits our ability to robustly reconstruct its morphology. Consequently,
we treated the recovered Gaussian as an upper limit on the jet base flux density. Future EHT observations with expanded intermediate baseline
coverage will be essential to constrain the structure and nature of this component with higher precision.


**Key words.** accretion: accretion disks, black hole physics, galaxies: individual: M87*, gravitation, relativistic process, galaxies: jets



**1.** **Introduction**


The giant elliptical galaxy Messier 87 (M87) serves as a cornerstone for understanding active galactic nuclei (AGNe), primarily due to its prominent relativistic jet powered by a supermassive black hole (SMBH) M87* at its center. This largescale jet is visible across the electromagnetic spectrum, including the infrared (Röder et al. 2025), optical (Perlman et al.
2011), X-ray (Marshall et al. 2002), and gamma-ray regime
(Abramowski et al. 2012). In the radio regime, the jet in M87
and its dynamics have been monitored at multiple wavelengths
and spatial scales (e.g. Walker et al. 2018; Lister et al. 2018;
Kim et al. 2018, 2023; Cui et al. 2023; Lu et al. 2023). At milliarcsecond scales, the jet displays hints of triple-peaked helical
dynamics (Asada et al. 2016; Hada 2017; Nikonov et al. 2023),
likely connected to precession (Cui et al. 2023). The envelope of
the jet limb shows a quasi-parabolic profile over a wide range
of spatial scales (Asada & Nakamura 2012; Hada et al. 2013;
Nakamura & Asada 2013; Nakamura et al. 2018; Walker et al.
2018; Lister et al. 2018), which appears to persist down to just
a few gravitational radii, as observed in the very long baseline interferometry (VLBI) observations from the Global Millimetre VLBI Array (GMVA) (Kim et al. 2018; Lu et al. 2023;
Kim et al. 2025) and space VLBI (Kim et al. 2023).


The Event Horizon Telescope (EHT) captured the first resolved image of the M87 nucleus at event horizon scales
(EHTC et al. 2019a,b,c,d,e,f), revealing a ring with a central
brightness depression interpreted as the shadow of the SMBH.
Subsequent EHT studies examined this feature in linearly and
circularly polarized light (EHTC et al. 2021a,b; EHTC et al.
2023) and found the ring to be persistent between 2017 and 2018
(EHTC et al. 2024). Wielgus et al. (2020) used model-fitting on
proto-EHT data at 230 GHz to study the ring evolution in the
years prior to the first resolved images.


A recent polarimetric analysis of EHT data spanning three
epochs—2017, 2018, and 2021—studied the dynamics across
years of M87* (EHTC et al. 2025). It was found that the ring
stays remarkably stable in total intensity (i.e., the ring diameter and thickness), with varying brightness asymmetry over
the years; but the linear polarization fractions and polarization patterns vary drastically between the years. Although the
milliarcsecond-scale jet has been studied extensively over the
years (Walker et al. 2018; Cui et al. 2023), its direct connection
to the jet base and the inner accretion flow is not well constrained
(e.g., Hada et al. 2024). A major step forward was made through
86 GHz GMVA imaging (Lu et al. 2023), which revealed a ringlike structure with northern and southern components linking to
a collimated, edge-brightened jet base. However, a central ridgeline present in the images may be an artifact from the deconvolution procedure (Kim et al. 2025). In this work, we aim to build
on these findings and constrain the resolved, extended emission


Article number, page 2



associated with the jet base at 230 GHz using the 2021 EHT observations.

In general, interferometric observations can only constrain
spatial scales corresponding to baseline lengths present in a
given array (e.g., Thompson et al. 2017). Very long baselines
(thousands of kilometers) resolve the finest angular scales, such
as the ∼ 40 µas ring. So-called trivial intra-site baselines (a few
hundred meters) are sensitive to arcsecond-scale structure but
provide no resolution near the black hole (Georgiev et al. 2025).
Intermediate-length or short baselines (a few hundred to a few
thousand kilometers) probe angular scales of hundreds to thousands of microarcseconds, making them particularly important
for studying the connection between the accretion flow and the
jet base.
While the presence of the large-scale jet at 230 GHz is evident in Atacama Large Millimeter/submillimeter Array (ALMA)
observations (Goddi et al. 2021), detecting and imaging this
emission with VLBI at 230 GHz is challenging for 2017 and
2018 EHT datasets lacking short or intermediate length baselines. This challenge results in a missing flux—flux density on
the order of ∼ 1.0 − 1.4 Jy detected on trivial baselines from colocated stations (ALMA/APEX, JCMT/SMA)—that compact
ring-only models (flux density ∼ 0.5 − 1.0 Jy depending on
the imaging approach) cannot fully explain (EHTC et al. 2019d,
2024). Although a robust detection was impossible due to the
lack of short and intermediate length baselines, some hints of extended emission, particularly to the southwest of the ring, in the
pre-2021 EHT data were reported in Broderick et al. (2022) and
EHTC et al. (2024) and through independent inspections of the
residual maps in Carilli & Thyagarajan (2022) and Arras et al.
(2022).
The EHTC’s data analysis methodology applied various
tools to deal with the missing flux issue, validated across datasets
(EHTC et al. 2019d, 2024, 2025). All methods have been explicitly validated using synthetic data generated with the 2021 coverage [1], in order to assess any potential systematic biases in the reconstructions. We refer to the synthetic data tests in EHTC et al.
(2025) for more details.
The regularized maximum likelihood (RML) methods typically deal with the missing flux problem by rescaling the flux
density at intra-site baseline spacings. `DoG-HIT` attempts to recover the image from closure quantities only (in arbitrary units)
and scales the whole image structure globally to a flux density
that minimizes the χ [2] of the amplitudes. CLEAN methods add a
large-scale Gaussian to account for the missing large-scale flux
density. `Comrade` and Themis apply similar strategies, but typically with more degrees of freedom for the large-scale component. The Hybrid-Themis framework (Broderick et al. 2020b)


1 That is, images of a variety of simple geometric structures, physically motivated structures, as well as simulations of accretion flow
(EHTC et al. 2025).

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations


**Fig. 1.** ( _u_, v) coverage of the EHT and representative ring image obtained by `DoG-HIT` (EHTC et al. 2025) in 2017, 2018, and 2021. Upper panels:
( _u_, v) with the SMT-KP (red) and PV-NOEMA baselines (green) highlighted. These are used to constrain the jet base emission. Middle panels: a
zoomed-in view of the ( _u_, v) coverage, highlighting the short and intermediate baselines. We also highlight the ( _u_, v) coordinates related to spatial
scales of 1000 µas and 200 µas, corresponding to the expected range for extended emission. Bottom panels: `DoG-HIT` image of the central ring
obtained from these data (EHTC et al. 2025).



incorporates the model-fitting of a narrow ring, allowing more
emission to be placed as jet base emission (Broderick et al.
2022).
The 2021 EHT observations offer the best ( _u_, v)-coverage to
date, providing a new opportunity to detect the faint, extended
emission associated with the jet. In particular, this is aided by the
addition of two new stations; the NOrthern Extended Millimeter
Array (NOEMA) in France and the Kitt Peak 12-m telescope
(KP) in the USA. These stations add intermediate baselines of
∼ 1100 km and ∼ 100 km to the IRAM 30-m telescope on Pico



Veleta (PV) in Spain and the Submillimeter Telescope (SMT) in
the USA, respectively. The corresponding angular scales of these
two baseline pairs are ∼ 250 µas and ∼ 2500 µas, i.e., these baselines are in principle sensitive to extended emission that could
not be detected by the EHT in previous years. However, each
baseline only probes a narrow range of spatial frequencies. Due
to the limited number of baselines sensitive to intermediate angular scales, the ( _u_, v) coverage is too sparse to directly image
the faint, extended structure. It would require several interme

Article number, page 3

_A&A proofs:_ manuscript no. main



13 14 15 16 17 18 19 20 21
GMST (h)



diate baselines with resolving power of a few hundred µas to
robustly image the jet base region.
As a consequence, much like in the case of other very sparse
VLBI data sets (e.g., Wielgus et al. 2020), we resort to a geometric model-fitting approach to constrain the presence of extended emission in the 2021 EHT data. For this purpose, we
used closure phases, which are the sum of the visibility phases
on a closed loop of three baselines (a triangle). This quantity is
powerful because it is immune to station-dependent atmospheric
and instrumental phase errors, making it a robust observable
in VLBI (Thompson et al. 2017; Blackburn et al. 2020). Therefore, we use closure triangles of the baselines of interest, formed
with the most sensitive station in the array, ALMA. On the relatively short baselines that make up these triangles, the compact
≈ 40 µas ring is only marginally resolved. While these baselines
individually have limited resolving power for such small-scale
structures, closure phases remain sensitive to asymmetries in the
overall brightness distribution. For a point source or a symmetric ring, the closure phases on these triangles are expected to be
zero. However, when we compare the observed closure phases
with those predicted by image reconstructions, we find non-zero
residuals. This indicates that the observed phase structure cannot be fully explained by the ring alone— even when intrinsic
asymmetries in the ring are included—and instead points to the
presence of additional, extended and asymmetric emission on
angular scales probed by the intermediate baselines.
To test this interpretation, we model the extended emission
using an offset Gaussian component in addition to the compact ring. Varying the position of the Gaussian component, we
found that the most plausible location for this excess emission
is to the South-West of the ring (i.e., the direction of the largescale jet), consistent with the conclusions reached by, for e.g.,
Broderick et al. (2022).
The analysis presented in this manuscript builds on the success of previous EHT studies, explicitly fitting a large-scale
component, and does not question the validity of the recovered
compact-scale images. As a complement to the compact-scale
studies, we present a deeper analysis of emission features of the
jet base at intermediate spatial scales (∼ 250 − 2500 µas).


**2.** **EHT observations of M87* in 2021**


In this section, we summarize the main data properties and results, with details provided in the companion paper (EHTC et al.
2025). The data were correlated with DiFX (Deller et al. 2007,
2011) using the output bands mode, a spectral window width
of 58 MHz, and a bandwidth of 1856 MHz per band. For
this analysis, we used band 3 and band 4 data, centered on
227.1 GHz and 228.1 GHz, respectively. The data were converted from linear to circular polarization feed basis using PolConvert (Martí-Vidal et al. 2016). Fringe-fitting was done using rPICARD (Janssen et al. 2019, 2022; von Fellenberg et al.
2025). The 2021 EHT observing campaign (April 9 − 19) consisted of M87* observations on April 9, 13, 14, 17 and 18. Since
April 14 and 17 were relatively shorter tracks and NOEMA did
not participate in April 13, we used only April 18. In 2021,
NOEMA and KP joined the array for the first time, providing
intermediate-length baselines that may be sensitive to the extended jet base emission (see Figure 1).
In EHTC et al. (2025), the data were analyzed by seven
teams using different imaging algorithms. The robustness of
the reconstruction was demonstrated via cross-validation. Two
teams used `Difmap` (Shepherd 1997), in combination with
the AIPS task LPCAL (Leppanen et al. 1995) and GPCAL


Article number, page 4



15 °


8 °


0 °


_−_ 8 °


_−_ 155 °°


2 °


0 °


_−_ 2 °


_−_ 5 °


0 °


_−_ 2 °


_−_ 5 °


_−_ 8 °


_−_ 10 °







**Fig. 2.** ALMA-APEX-PV (top) closure phases of M87* as observed in
2017, 2018 and 2021. The ALMA-PV-NOEMA (middle) and ALMASMT-KP (bottom) closure phases on M87* observed on April 18, 2021
(figure is adapted from EHTC et al. (2025)) are shown together with
ring-image models obtained with different imaging algorithms (see text
for details). The top panel shows an example of a trivial closure phase
triangle, where two stations are co-located, see Georgiev et al. (2025)
for details. The image models are discrepant with the observed data by
a few degrees, which may be attributable to intermediate-scale emission
observed on the PV-NOEMA and SMT-KP baselines.


(Park et al. 2021, 2023a,b). The other teams used the RML
methods `DoG-HIT` (Müller & Lobanov 2022, 2023b,a), `ehtim`
(Chael et al. 2016, 2018), and `MOEA/D` (Müller et al. 2023;
Mus et al. 2024b,a), as well as the Bayesian imaging techniques
Themis (Broderick et al. 2020a) and `Comrade` (Tiede 2022). Although these imaging algorithms rely on different assumptions,
they converge on a consistent recovered image structure on event
horizon scales (EHTC et al. 2025). We show a representative image from this analysis obtained by `DoG-HIT` in the bottom panels
of Figure 1. The 2021 observations of M87* are well represented
by a ring structure with an asymmetry oriented to the southwest.
Although the total-intensity images are very consistent across
years and methods, there is some significant evolution of the polarized structure over the years (for more details, we refer the
reader to EHTC et al. 2025). In this work, we focused on total intensity and leave the discussion of polarization of extended
components for future work.


**3.** **Jet base emission**


_3.1._ _Bump and offset in closure phases_


We show the ( _u_, v) coverage of the EHT in 2017, 2018, and 2021
in Figure 1 and highlight two new baselines introduced in 2021.
The PV-NOEMA baseline is ∼ 1100 km in length, corresponding to on-sky spatial scales ∼ 250 µas; the SMT-KP baseline is
∼ 100 km in length, corresponding to ∼ 2500 µas scales. These
intermediate baselines are sensitive to jet base emission, if it exists and is bright and compact enough to be detectable. However,
each of these spatial scales is probed by a single baseline with a

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations





















10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]



5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5












|F0 = 0 .07 Jy F0 = 0<br>200 µas (a)|Col2|.08 Jy F0 = 0<br>(b)|.09 Jy F0 = 0<br>(c)|.11 Jy<br>(d)|
|---|---|---|---|---|
|AA-PV-NN|AA-PV-NN||||
||||||
|AA-SMT-KP|AA-SMT-KP||||
||||||
|(e)<br>_x_pos = -260 _µ_as<br>_x_pos =|(e)<br>_x_pos = -260 _µ_as<br>_x_pos =|(f)<br> -180 _µ_as<br>_x_pos =|(g)<br> -60 _µ_as<br>_x_pos =|(h)<br> 180 _µ_as|
||||||
||||||
||||||
||||||
|(i)<br>_y_pos = -90 _µ_as<br>_y_pos =|(i)<br>_y_pos = -90 _µ_as<br>_y_pos =|(j)<br>-80 _µ_as<br>_y_pos =|(k)<br>60 _µ_as<br>_y_pos =|(l)<br>180 _µ_as|
||||||
||||||
||||||
||||||
|(m)<br>fwhms = 128 _µ_as<br>fwhms|(m)<br>fwhms = 128 _µ_as<br>fwhms|(n)<br>= 110 _µ_as<br>fwhms|(o)<br>= 60 _µ_as<br>fwhms|(p)<br>= 20 _µ_as|
||||||
||||||
||||||
||||||
|3<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>17<br>19<br>21<br>UTC(hr)<br>13<br>15<br>1<br>UT|7<br>19<br>21<br>C(hr)|



**Fig.** **3.** Symmetric Gaussian component with varying parameters over
the reconstructed `DoG-HIT` image as represented in Figure 1 represented
in log scale. Different rows correspond to changes in the values of different parameters (see text for details). The solid lines represents the
corresponding complete model (ring + Gaussian) closure phases on the
respective triangles.


limited track length. Because of that, self-calibration techniques
may inadvertently introduce or suppress extended emission if
calibrated against a ring-only image or central point sources
(e.g., Carilli & Thyagarajan 2022). To overcome this problem,
we analyze data that were not self-calibrated, and use closure
phases that are insensitive to station-based gain errors (e.g.,
Blackburn et al. 2020) to probe the jet base emission at scales
accessible with SMT-KP and PV-NOEMA.


Three stations are required to construct closure phases.
Because no other intermediate-length baselines are available,
the closure triangles formed necessarily also probe small-scale
structures. However, we can choose triangles that are particularly useful, i.e., show low variations during the track (indicating that the long baseline contribution is small or canceled), are
long in duration, and have high signal-to-noise ratio (S/N). The
high-sensitivity station ALMA satisfies all these requirements



for both baselines of interest. We thus focused on the ALMASMT-KP and ALMA-PV-NOEMA triangles in this analysis.
Since the small-scale information of the long ALMA
baselines in those triangles cannot be disentangled from the
intermediate-scale information, the jet base information has to
be derived from the difference between the data and the ringonly image. In Figure 2 we show the closure phases on various
triangles. The top panel displays an example triangle containing
the ALMA-APEX baseline across the three years. The middle
and bottom panels display the triangles of interest obtained for
the small-scale ring images for different methods—one representative image is chosen for each framework— `Difmap` (CLEAN),
`DoG-HIT` (RML) and `Comrade` (Bayesian). None of the imaging
methods (marked by solid lines) can fully recover the closure
phases with the compact ring image alone on these triangles.
However, we note that the different imaging algorithms applied
and validated various strategies to mitigate the effect of jet base
emission on the ring images. These include the addition of largescale Gaussian components that are not used to create the fits in
Figure 2. Figure 2 displays the image fits without these additional factors, focusing solely on the compact ring feature.
In particular, the ALMA-PV-NOEMA triangle features a
‘bump’ that is not well captured by the ring images, and, similarly, ALMA-SMT-KP has a visible ‘offset’. Due to the high
sensitivity on those triangles, the difference is significant despite
its small magnitude.
One plausible explanation for this residual of a few degrees
in the closure phase is a faint but measurable emission on intermediate spatial scales sensed by PV-NOEMA and SMT-KP.


_3.2._ _Model_


In the following, we motivate a simple model to explain the observed closure phase residuals on the two selected triangles. The
triangle that includes the longer baseline PV-NOEMA features
a bump with a period of a few hours. Conversely, the ALMASMT-KP triangle does not have a beating but a simple offset
from the ring-image models. This suggests that the relevant spatial scales may be on the order of, or slightly larger than, the PVNOEMA scale, as any larger structure would introduce a beating
on the ALMA-SMT-KP triangle as well. Moreover, it needs to be
located close to the image center. Such a closure phase signature
is characteristic of a “binary model”; in our case it consists of the
ring, which is not resolved by either of the two baselines, and an
extra component.
Based on these simple considerations, we propose the following source model: the compact ring emission as seen on long
baselines, with an additional, faint, Gaussian component located
at scales 100 − 2000 µas from the center of the ring emission.
This model gives four additional degrees of freedom, the _x_ and
y positions, the brightness _F_ 0, and the full width at half maximum (fwhm) of the Gaussian component. The model is selected
to be as simple as possible to restrict the number of degrees of
freedom, which is a necessary assumption for the model fitting
due to the limited information on jet base emission present in
the data. Because the PV-NOEMA and SMT-KP baselines are
sensitive to two different spatial scales, they are not necessarily described by the same model component. Thus the model’s
complexity can be trivially extended by allowing for an elliptical
Gaussian component or even a second Gaussian component.
Deriving from these simple initial considerations, we can set
approximate limits for the expected parameters of the additional
Gaussian component. The size should be such that it is probed
by the PV-NOEMA and SMT-KP baselines, creating a beating


Article number, page 5

_A&A proofs:_ manuscript no. main


|ALMA-PV-NOEMA - 2 =1.29|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|.|.|.|.|.|.|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||


|ALMA-SMT-KP -|Col2|Col3|Col4|2 =1.10|Col6|
|---|---|---|---|---|---|
|||||.|.|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||


|Combined - 2 =1.20|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|.|.|.|.|.|.|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||



400 200 0 200 400

Relative RA ( as)



400


200


0


200


400



8


6


4


2



400


200


0


200


400



400 200 0 200 400

Relative RA ( as)



10


8


6


4


2



7


6


5


4


3


2



400 200 0 200 400

Relative RA ( as)



400


200


0


200


400



**Fig. 4.** χ [2] ν [achieved with the Gaussian model for a fixed width and brightness ratio, but varying position. The left and middle panels show the][ χ] [2] ν
for the ALMA-PV-NOEMA and the ALMA-SMT-KP triangles, respectively, and the right panel shows the combined χ [2] ν [.] [The] [contours] [indicate]
the position of the best-fit model.



on the former within just two hours. Hence, it does not describe
extended emission but most likely jet base emission with spatial
scales similar to the ring diameter.
We refer to detailed analysis of the total flux density of
the ring feature in EHT observations presented in EHTC et al.
(2024). Although for the arcsecond scale structure in M87*
typically flux densities between 1.0 Jy and 2.0 Jy were measured (Bower et al. 2015; Wielgus et al. 2020), for the milliarcsecond and microarcesond structure usually flux densities
between 0.5 and 1.0 Jy have been reported (Doeleman et al.
2012; Akiyama et al. 2015; Kim et al. 2018; Wielgus et al. 2020;
Lu et al. 2023), consistent with the values found by the EHT
(EHTC et al. 2019d, 2024, 2025). The discrepancy between the
ring image and the flux density detected with ALMA alone of
about 1 Jy is due to the existence of an (as of yet) undetectable
large-scale jet. The additional Gaussian component fitted in this
manuscript is likely to explain some, but not necessarily all, of
the missing flux. This sets an approximate upper limit of 0.5 Jy
for the flux of the Gaussian component, preferably less.


**4.** **Localization of the emission region**


_4.1._ _Impact of the model parameters_


In the following analysis, we examine the impact of jet base
emission when modeled as a Gaussian component. We base our
analysis on a `DoG-HIT` reconstruction: since the algorithm separates small and large scale emission naturally, it is optimized to
fit to the closure phases and closure amplitudes in the 2021 data.
However, we note that the black hole shadow images obtained by
various algorithms have similar characteristics on the ALMAPV-NOEMA and ALMA-SMT-KP triangles with respect to the
bump and the offset, see Figure 2.

Figure 3 shows the ring image obtained by `DoG-HIT` with
an additional Gaussian added on top, varying some of the parameters described in Section 3.2. The upper part of the panels
display the recovered central region with an additional Gaussian
component in logarithmic scale. Panels e, f, h, and i show the observed closure phases (black markers) and model closure phases
(solid lines) on the ALMA-PV-NOEMA triangle (AA-PV-NN)
and ALMA-SMT-KP triangle (AA-MG-KP).
The addition of a Gaussian component creates a periodic
modulation – a beating – on the PV-NOEMA baseline. There
are locations (primarily to the east and west of the ring, see Figure 3) where the beating is broadly aligned with the data, and


Article number, page 6



locations where it misaligns and worsens the fit to the closure
phase (primarily to the north). On the ALMA-SMT-KP triangle,
the component produces a closure phase offset, which matches
the data for some locations (good fits primarily to the West). The
brightness of the component scales the amplitude of the beating
and offset on the respective triangles. An overly bright Gaussian
component overestimates the beating and the correction of the
offset, while a too dim component underestimates the necessary
corrections (first row of Figure 3). Finally, an overly compact
component causes large-magnitude swings in the closure phase,
while for a larger feature it is too smooth (fourth row in Figure 3).
These findings are summarized in Figure 4. In the left panel
we show an example of reduced χ [2] (χ [2] ν [)] [of] [the] [ALMA-PV-]
NOEMA triangle as a function of the location of the Gaussian component with a fixed flux density of 60 mJy and a size
of 180 µas. Locations 200 µas to the west or the east of the
ring are preferred. Similarly, the middle panel shows the χ [2] ν [for]
the ALMA-SMT-KP triangle, with the preferred location to the
southwest. In the right panel we show the combined χ [2] ν [and a pre-]
ferred region to the southwest, roughly 300 µas to the West and
100 µas to the South of the ring. However, the presence of multiple regions with low χ [2] ν [indicates that the current model remains]
weakly constrained and degenerate.


_4.2._ _Symmetric Gaussian component_


To obtain the maximum posterior position for a Gaussian component, we use the Markov chain Monte Carlo (MCMC) sampler emcee (Foreman-Mackey et al. 2013). We adopt uniform
priors for the flux ( _F_ 0 ∈ [0, 0.2] Jy), the location ( _x_, y ∈

[−500, 500] µas), and the width (fwhm s ∈ [50, 250] µas). The
maximum posterior parameters are given in Table 1. The corner
plots are shown in Appendix A (Figure A.1). The best fit component has a flux density of ∼ 60 mJy and is located towards the
Southwestern portion of the ring.
We show the obtained ring image as well as the ring image
with an additional Gaussian component in Figure 5. The respective fits of the Gaussian components to the ALMA-PV-NOEMA
and ALMA-SMT-KP closure phases are shown in the panels e,
f, h, and i. We highlighted notable improvements in the fitting
quality of the closure phases visible from panel h and i. Despite
the simplicity of the model, the χ [2] ν [is] [1][.][29] [for] [the] [bump] [(com-]
pared to 2.73 without the jet base emission), and 1.12 for the

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations



**Table** **1.** Parameter estimates for the different Gaussian model fits described in Section 4.2, Section 4.3 and Section 4.4.

|Parameter|Symmetric Asymmetric Double|
|---|---|
|_F_0 (mJy)<br>_x_1 (µas)<br>y1 (µas)<br>fwhm1(µas)|70+10<br>−10<br>60+20<br>−20<br>50+30<br>−30<br>−304+38<br>−38<br>−300+37<br>−37<br>−297+46<br>−46<br>−68+12<br>−12<br>−63+12<br>−12<br>−68+18<br>−18<br>169+27<br>−27<br>180+35<br>−35<br>150+56<br>−56|
|R1<br>Φ1 (◦)|−<br>0.7+0.3<br>−0.3<br>0.6+0.5<br>−0.5<br>−<br>14+119<br>−119<br>23+101<br>−101|
|_F_2 (mJy)<br>_x_2 (µas)<br>y2 (µas)<br>fwhm2 (µas)<br>R2<br>Φ2 (◦)|−<br>−<br>20+20<br>−20<br>−<br>−<br>−291+96<br>−96<br>−<br>−<br>117+126<br>−126<br>−<br>−<br>150+56<br>−56<br>−<br>−<br>0.5+0.3<br>−0.3<br>−<br>−<br>1+120<br>−120|



offset (compared to 2.52). The component has almost negligible
impact on all other triangles; the χ [2] ν [over] [all] [triangles] [improves]
from 1.5 to 1.39. The χ [2] ν [does not increase for any triangle, see]
Appendix B for further details. In Figure B.2, we show the impact of the additional Gaussian component on the amplitudes for
different baselines. Amplitudes on baselines longer than ∼ 2 _G_ λ
stay mostly unaffected by the additional Gaussian component.
This is reflected by the fit to the self-calibrated amplitudes shown
in panel g and j in Figure 5 and the left panel in Figure B.2. The
effect of the Gaussian component can be completely absorbed
into the amplitude self-calibration.
Finally, synthetic data tests were performed in EHTC et al.
(2025). These tests also include the validation of a ring image with an extended jet component. The results of this test for
all seven imaging techniques are described in Appendix D3 of
that paper. We reprint the main result of this validation in Appendix B, Figure B.1. We note that all techniques were able
to recover the ring emission correctly with exceptionally high
cross-correlation > 0.995 for the total-intensity 2021 data.
We conclude that the addition of the Gaussian model does
not worsen the otherwise excellent fit to the data obtained in
EHTC et al. (2025) with the black hole shadow images only.
Vice versa, the Gaussian component only leaves a significant effect on the ALMA-PV-NOEMA and ALMA-SMT-KP triangles,
exhibiting a small effect on the overall fitting statistics. Hence,
based on the success of the fitting in the aforementioned study,
and the synthetic data tests that were performed in EHTC et al.
(2025), we have no reason to question the validity of the ring
emission presented in EHTC et al. (2025).


_4.3._ _Asymmetric Gaussian component_


To explore the possibility of asymmetry of the jet base emission we extend the model by two additional parameters: the ratio of fwhm maj and fwhm min (R) and the rotation angle of the
asymmetric Gaussian component Φ, see Appendix C for additional details. We again use uniform priors (R ∈ [0, 1], and
Φ ∈ [−180 [◦], 180 [◦] ]). Neither the flux density nor the position
change significantly; however, the model prefers to be symmet


ric, and hence the rotation angle is poorly constrained. The χ [2] ν
values are 1.28 for the bump and 1.10 for the offset, i.e., there
is no significant improvement to the fit. The best-fit values are
provided in Table 1, we show the best-fit model in the left panel
of Figure 6.


_4.4._ _Two Gaussians_


For completeness, we explore the possibility of a secondary
Gaussian component in the fit. However, given the complexity
of the model and limitations of the data, we constrain the second component in the positive y direction, that is, we allow the y
position to vary only within [0, 500µas]. In this way, we test the
presence of the second component in the northern region, but allow all parameters to vary (12 parameters). The flux density of
the first southern Gaussian is _F_ 1 = 50 [+] − [30] 20 [mJy. The second Gaus-]
sian has a flux density of _F_ 2 = 20 [+] − [20] 10 [mJy. The first component is]
smaller in size compared to the previous modeling, but the positions do not vary significantly. The second, northern, component
is relatively fainter. Since, the rotation angle for this component
is poorly constrained, it prefers to be symmetric as well. The χ [2] ν
values are 1.29 for the bump and 1.10 for the offset. Thus, there
is no statistical evidence for the inclusion of a secondary Gaussian component.
The Gaussian fit parameters are provided in Table 1, and the
corner plot is provided in Appendix A. The third image in Figure 6 (right panel) represents the best-fit model consisting of two
Gaussian components.


**5.** **Alternative fitting scenarios**


Due to the limited number of data points on the two chosen closure triangles, multiple plausible emission features may exist.
In the previous section, we demonstrated that adding a simple
Gaussian component to the compact emission provides a good
fit to the data; the emission is most likely located southwest of
the ring emission.
In this section, we discuss alternative models that may fit the
data and discuss their validity. This list is not complete and focuses on some physically-motivated emission structures instead.
Hence, we cannot rule out that alternative emission scenarios exist.


_5.1._ _GMVA jet structure_


At 86 GHz, Lu et al. (2023) imaged a ring-like feature together
with the innermost jet in M87* with the GMVA complemented
by the ALMA and the Greenland Telescope (GLT). Here, we discuss whether this jet structure would be able to fit the respective
triangles. To this end, we need to extract the jet component of
the GMVA image from the ring feature observed at 86 GHz, and
stack this jet feature to the ring feature observed at 230 GHz.
Specifically, Kim et al. (2025) presented a reanalysis of this
data set, among others, with `DoG-HIT` . In `DoG-HIT`, the image
structure is represented in multiple spatial scales by wavelets Ψ _i_ :


_I_ = � Ψ _i_ ∗ ω _i_ . (1)

_i_


The smallest-scale wavelets describe the ring (the small-scale
feature), and the largest spatial scales describe the jet emission.
In this way, the image is naturally decomposed into the compact ring structure and the jet base emission across different spatial scales. We use this natural decomposition to study whether


Article number, page 7

_A&A proofs:_ manuscript no. main



5


0


5


5


0


5



1.2


1.0


0.8


0.6


0.4


0.2



1.2


1.0


0.8


0.6


0.4


0.2



3.5 3.0 2.5 2.0 1.5 1.0 0.5

log 10 (mJy/ as [2] )


(g) Amplitudes



3.5 3.0 2.5 2.0 1.5 1.0 0.5

log 10 (mJy/ as [2] )


(j) Amplitudes



5


0


5


5


0


5



0.0 0.1 0.2 0.3 0.4 0.5 0.6

mJy/ as [2]


(e) ALMA-PV-NOEMA


(f) ALMA-SMT-KP



0.0 0.1 0.2 0.3 0.4 0.5 0.6

mJy/ as [2]


(h) ALMA-PV-NOEMA


(i) ALMA-SMT-KP



11 13 15 17 19 21

UTC



0.0

0 2 4 6 8 10
uvdist [G ]



11 13 15 17 19 21

UTC



0.0

0 2 4 6 8 10
uvdist [G ]



**Fig.** **5.** Ring-only `DoG-HIT` image (panel a: linear scale, panel b: logarithmic scale) compared to the `DoG-HIT` ring image with an additional
Gaussian (panel c and d). In the bottom row, we show the fit to the bump and offset in closure phases and the fit to the amplitudes for `DoG-HIT`
(panels e,f,g) and for `DoG-HIT` with the symmetric Gaussian component added (panels h,i,j).



_χ_ [2] bump [= 1] _[.]_ [28] _[, χ]_ [2] offset [= 1] _[.]_ [12]


_−_ 7 _−_ 6 _−_ 5 _−_ 4 _−_ 3
Intensity [Jy _/µ_ as [2] ]



_χ_ [2] bump [= 1] _[.]_ [29] _[, χ]_ [2] offset [= 1] _[.]_ [10]


_−_ 7 _−_ 6 _−_ 5 _−_ 4 _−_ 3
Intensity [Jy _/µ_ as [2] ]



cial model presented in Section 4.2. This is likely a limitation of
our attempt to scale the 86 GHz image, rather than an indication
that the 86 GHz and 230 GHz emission structures are inherently
different.


_5.2._ _Imaging with weakened assumption on compactness_


Next, we check whether we can find an alternative way of fitting the data, including the offset and the bump utilizing the
`DoG-HIT` imaging algorithm. `DoG-HIT` represents the recovered
image by a dictionary of wavelet functions Ψ _i_ and images at spatial sub-bands as described by Eq. 1. `DoG-HIT` utilizes a sparsityconstraining approach, effectively defining multiresolution support, i.e., a set of statistically-significant wavelet coefficients
to describe the image. As demonstrated in Müller & Lobanov
(2023a), the multiresolution support encodes two constraints: the
location of the emission and the spatial scales needed to explain
the emission at these locations. The latter relates to the ( _u_, v) coverage, i.e., which spatial scales are measured.
This way, `DoG-HIT` allows for three alternative approaches to
fit the bump and the offset. In the first approach, we investigate
whether large spatial scales can account for the observed deviations without a constraint on the emission location or its spatial
scale. In the second approach, we focus on localized emission
in the ring. In the third approach, we constrain the location and
spatial scales. For each approach, we take the ring-only image
from `DoG-HIT` and try to improve the fit quality to the closure
phases only, using a gradient descent approach with a small step
size.


5.2.1. Fit without spatial scale and localization constraints


First, we do this fit without any mask on the spatial scales or the
location of the emission, allowing every pixel to vary (labeled
unmasked Figure 8, right column). The unmasked image fits the



**Fig. 6.** Images for the best fits with an asymmetric Gaussian component
(left) and two Gaussian components (right) in log scale.

.


the jet observed by the GMVA provides a good fit: we filter out
the ‘ring-components’ in the 86 GHz image by setting all smallscale wavelets to zero, then we add the 230 GHz EHT ring image and the jet emission at 86 GHz seen by the GMVA. Motivated by the findings in Section 4.1, the GMVA jet image is
rescaled to add a flux density between 0.0 Jy and 0.2 Jy to match
the 230 GHz ring image. We grid-search for the best flux density
in this interval and find the best χ [2] at an additional flux density of
0.06 Jy, consistent with the findings in Section 4.2. The results
are shown in Figure 7. We note that we can absorb the largescale jet component completely in the amplitude gains, providing a good fit to the self-calibrated amplitudes in both cases. The
fit to the offset and the bump is improved by including the jet
component. However, our model of the 86 GHz jet is not able
to provide a good fit, performing worse than the simpler fidu

Article number, page 8

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations



5


0


5


5


0


5



1.2


1.0


0.8


0.6


0.4


0.2



1.2


1.0


0.8


0.6


0.4


0.2



5 4 3 2 1

log 10 (mJy/ as [2] )


(g) Amplitudes



5 4 3 2 1

log 10 (mJy/ as [2] )


(j) Amplitudes



5


0


5


5


0


5



0.0 0.1 0.2 0.3 0.4 0.5 0.6

mJy/ as [2]


(e) ALMA-PV-NOEMA


(f) ALMA-SMT-KP



0.0 0.1 0.2 0.3 0.4 0.5 0.6

mJy/ as [2]


(h) ALMA-PV-NOEMA


(i) ALMA-SMT-KP



11 13 15 17 19 21

UTC



0.0

0 2 4 6 8 10
uvdist [G ]



11 13 15 17 19 21

UTC



0.0

0 2 4 6 8 10
uvdist [G ]



**Fig. 7.** Ring-only `DoG-HIT` image(first panel, top row: linear scale, second-panel first row: logarithmic scale) compared to the `DoG-HIT` ring image
stacked with the jet observed with the GMVA (third and fourth panel, top row). In the bottom row, we show the fit to the bump and offset in closure
phases and the fit to the amplitudes for `DoG-HIT` (left panels) and for `DoG-HIT` with the GMVA jet added (right panels).



bump and also shows a much-improved fit to the offset. Moreover, improving the fits in the direction of the closure phases
does not violate the match to the amplitudes. The recovered ring
image shows no significant variation. However, comparing the
unmasked image with the original image, which was masked in
spatial scale and localization (Figure 8, left column), on a logarithmic scale, we observe that the improved precision has been
achieved by fitting a ‘waffle-like pattern’ associated with the PVNOEMA and SMT-KP baselines, which is nonphysical.


5.2.2. Fit with localization constraint


Here, we add a constraint on the emission location by performing
the same gradient descent fit to the closure phases but only allowing the pixels on the ring to vary, defined by the 1% intensity
contour in the `DoG-HIT` imagesy. The resulting reconstructions
and model closure phases are shown in Figure 9.
In this case, we can fit the bump reasonably well but have
issues fitting the offset. A closer inspection of the structures that
fit the bump in the top right panel of Figure 9 indicates that this
fitting is achieved by asymmetries in the ring itself through a
number of components. Each component exhibits structure significantly smaller than the resolution limit of roughly 20 µas.


5.2.3. Fit with localization and spatial constraints


Finally, we constrain the emission both by its localization and its
spatial scale, as imprinted in the wavelet approach of `DoG-HIT` .
The respective fitting quality is shown in the left columns of Figure 8 and Figure 9. Even if we fit for the ALMA-PV-NOEMA
and ALMA-KP-SMT closure phases alone with a gradientdescent approach, restricted by the localization and spatial constraints imprinted by the wavelet dictionary, we remain limited
in our potential to fit the bump or the offset.



**Fig. 8.** Reconstruction of the ring and potential jet base emission, when
restricted to spatial scales determined by `DoG-HIT` in the compact emission region (left panels, called masked), and completely unmasked
(right panels, called unmasked).


This suggests that the model mismatch results from limiting
the imaging to ring-scale emission only. This further supports
the view that the bump and the offset are signatures of jet base
emission, rather than artifacts from the imaging procedure being
imprecise in its representation of the ring.


Article number, page 9



5


0


5


5


0


5



5


0


5


5


0


5



5 4 3 2 1

log 10 (mJy/ as [2] )


ALMA-PV-NOEMA


ALMA-SMT-KP



5 4 3 2 1

log 10 (mJy/ as [2] )


ALMA-PV-NOEMA


ALMA-SMT-KP



11 13 15 17 19 21

UTC



11 13 15 17 19 21

UTC

_A&A proofs:_ manuscript no. main


2017, Chile-LMT-SMT Triangle



2018, Chile-LMT-SMT Triangle



5


0


5


5


0


5



0


20


40


60


80


100



0


20


40


60


80


100







2 3 4 5 6 7 8


0.2


0.1



26 27 28 29 30 31 32


0.2


0.1



0.026 27 28 29 30 31 32

Time [UTC]



5


0


5


5


0


5



0.00 0.25 0.50 0.75 1.00 1.25 1.50

mJy/ as [2]



0.00 0.25 0.50 0.75 1.00 1.25 1.50

mJy/ as [2]



0.02 3 4 5 6 7 8

Time [UTC]



11 13 15 17 19 21

UTC



11 13 15 17 19 21

UTC



**Fig. 9.** Reconstruction of the ring and potential jet base emission when
restricted to spatial scales determined by `DoG-HIT` in the compact emission region (left panels, called masked), and when restricted to the ring
emission, but flexible in spatial scale (right panels, called unmasked).


5.2.4. Data corruptions and systematic errors


Both the bump and offset are formally significant relative to a 0 [◦]

closure phase, assuming the thermal errorbars are reliable. However, it is likely that the thermal errorbars underestimate the true
error, as they do not account for non-closing errors such as polarization leakage (e.g., Broderick & Pesce 2020). Therefore, imaging methods add a fractional systematic Gaussian uncertainty
to the errors of ∼ 2% of the visibility amplitudes (EHTC et al.
2019c). In Appendix D we demonstrate that leakage cannot account for the bump or the offset. Nevertheless, we cannot rule
out the possibility that other unknown sources of systematic error may corrupt the data.


_5.3._ _Impact on previous EHT observations_


The information about jet base emission has been derived primarily from the KP-SMT and PV-NOEMA baselines in this
manuscript. These baselines are unique to the 2021 EHT data,
as this was the first year in which the Kitt Peak telescope and
NOEMA participated in EHT observations (EHTC et al. 2025).
In 2017 and 2018, LMT formed a baseline with the SMT of
∼ 1.3 Gλ (compared to 0.8 Gλ for PV-NOEMA in 2021), making it the shortest baseline between two stations that are not
co-located (ALMA/APEX and SMA/JCMT) during these years.
However, LMT did not participate in the 2021 observations.
Here, we examine whether the jet base component derived in
this manuscript – based on the enhanced coverage of the EHT
in 2021 – would have a significant impact on data taken in 2017
and 2018. In other words, does our knowledge of an extended
component influence the black hole shadow reconstructions presented in EHTC et al. (2019a, 2024, 2025)?
In Figure 10, we show the closure phases observed in 2017
(left panel) and 2018 (right panel) with the LMT-SMT baseline (black data points), and their respective fit to the `DoG-HIT`
model of that year presented in EHTC et al. (2025) (red line).


Article number, page 10



**Fig.** **10.** Closure triangle formed by Chilean stations (ALMA/APEX),
LMT, and SMT in 2017 (left panel) and 2018 (right panel). The LMTSMT baseline is the shortest baseline between non-co-located stations

in EHT observations of 2017 and 2018. Black markers: observed closure phases. Red line: fit to the `DoG-HIT` reconstruction in 2017 (left
panel) and 2018 (right panel). Dark blue line: fit to the `DoG-HIT` reconstruction (ring) with an additional Gaussian model component determined from 2021 data as it would appear in 2017 (left panel) and 2018
(right panel). The line has been offset by a time offset of 0.1 hours to
make it visible. In the bottom panels, we show the significance of the
difference between the `DoG-HIT` model and the `DoG-HIT` model with
additional Gaussian component, measured by the difference in Ψ _C_ divided by the closure phase error. In both years, the effect of the additional Gaussian component on the Chile-LMT-SMT closure phases is
an order of magnitude smaller than the respective noise.


The closure phases undergo a swing of almost 80 [◦] over the full
duration of the observing track. This swing is completely explained by the ring models recovered by `DoG-HIT` . There is no
additional feature visible that would motivate the fitting of an
additional component in these years from the LMT-SMT baseline. In addition, we show with a blue dotted line the closure
phases of the `DoG-HIT` model with the additional Gaussian component obtained from our analysis in 2021. In the bottom panels, we show the difference between the predicted closure phases
with and without the additional Gaussian component compared
to the noise level. The difference in closure phase introduced
by our model on the LMT-SMT baseline is negligible. We conclude that, due to the lack of short baselines, the data obtained in
2017 and 2018 by the EHT are fully fitted by ring-only emission.
Additionally, the Gaussian component identified in this work is
not detectable on any baseline in the EHT longer than the PVNOEMA baseline, and thus was not detectable/had no measurable impact on observations conducted in 2017 and 2018. Moreover, the component fitted here is relatively faint, only 60 mJy.
Any significantly brighter component would introduce effects in
ALMA-PV-NOEMA and ALMA-KP-SMT triangles larger than
a few degrees, setting a robust upper limit for the amount of resolved jet emission in EHT observations to date.


**6.** **Discussion**


Broderick et al. (2022) found a component roughly 50 µas to the
south and 50 µas to the West of the black hole shadow by modeling a narrow ring component to describe the black hole ring
feature in the 2017 EHT observations (EHTC et al. 2019a). This
result is consistent with similar findings reported in Arras et al.
(2022); Carilli & Thyagarajan (2022), although a robust detection could not be claimed by either study due to the lack of short
and intermediate baselines in the 2017 EHT observations.

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations





3.0


3.5


4.0


4.5


5.0


5.5



17 15 13 11 9 7

log2 (Jy/pixel)


**Fig. 11.** Fiducial ring structure of the M87* black hole shadow (green
contour) with a single Gaussian component (solid blue contours) corresponding to the best-fit parameters found in Section 4.2 (Table 1, first
set) and double Gaussian components (dashed contours) corresponding
to the best-fit parameters found in Section 4.4 (Table 1, second set),
overplotted on the jet in M87* observed at 86 GHz (heatmap) with the
GMVA (Lu et al. 2023; Kim et al. 2025). The green dotted line shows
the jet orientation.


Broderick et al. (2022) demonstrated that the feature aligns
well with the southern arm of the edge brightened jet observed
at 86 GHz (Kim et al. 2018) when taking into account the expected core shift between 230 and 86 GHz. Recently Lu et al.
(2023) observed the innermost jet in M87* at 86 GHz with the
GMVA expanded by ALMA. They found a ring-like feature with
an edge-brightened jet base. In Figure 11 we present the EHT
results (green-colored contours) on top of the GMVA image (in
virdis colormap). To this end, we use the intensity map reported
by Kim et al. 2025 (a reanalysis of results reported in Lu et al.
2023) due to its improved resolution. The images are stacked by
aligning the ring features observed at 230 and 86 GHz. By visual
inspection, the jet base Gaussian component studied here aligns
to first order with the southern arm of the edge-brightened jet
observed with the GMVA. The second Gaussian component in
the two-Gaussian model would align with the northern arm, but
most likely represents a degeneracy in the posterior.
The jet collimation profile at sub-milliarcsecond scales is
parabolic. Kim et al. (2018) found a jet width profile _W_ ∝ _z_ [0][.][5]

(where _z_ is the projected distance from the core), also in agreement with observations at milliarcsecond scales (Hada et al.
2013, 2016; Hada 2017). This parabolic shape is consistent
with a jet driven either by black hole spin via the BlandfordZnajek mechanism (Blandford & Znajek 1977; Nakamura et al.
2018) or by the differential rotation of the accretion flow via the
Blandford-Payne mechanism (Blandford & Payne 1982). The
preference for a southwestern component in our model over a
northwestern component is consistent with a rapidly rotating
jet structure near the black hole (Broderick et al. 2022), however the scope for interpretation remains limited due to the limited amount of information. Lu et al. (2023) reported a deviation
from the parabolic shape near the core (≤ 0.2 mas). This profile flattening may be a powerful indicator of the jet launching



mechanism, potentially requiring an additional emission component, for example by non-thermal electrons in gravitationally unbound, non-relativistic winds (Nakamura et al. 2018; Park et al.
2019; Lu et al. 2023). While this is an anticipated observable for
the EHT and its successors to connect the jet dynamics to the
black hole and study jet launching mechanisms (EHTC 2024),
we note that the jet base component found in this study is too
far out to make reliable conclusions about the physics of the jet
within the first ten Schwarzschild radii.


**7.** **Conclusions**


We used the improved intermediate baseline coverage of the
2021 EHT campaign to search for resolved jet base emission
around M87*. We found evidence for a faint offset component
on angular scales accessible to the PV-NOEMA and KP-SMT
baselines. Fitting a simple geometric model – a single offset
Gaussian – yields a flux density of ∼ 60 mJy at a location
≈ (−60, −320) µas relative to the ring center. The Gaussian component has fwhm ≈ 180 µas.
Introducing the Gaussian component into the source model
reduces the closure phase residuals on the ALMA-PV-NOEMA
and ALMA-KP-SMT triangles. For the ALMA-PV-NOEMA triangle the χ [2] ν [falls from 2][.][73 to 1][.][29, and for the ALMA-KP-SMT]
triangle from 2.52 to 1.12; the χ [2] ν [for all triangles improves from]
1.50 to 1.39; and it is improved on every single triangle, albeit
the improvement is insignificant for most. This demonstrates that
a compact, faint asymmetry at intermediate scales is an economical explanation for the observed closure phase structure in the
2021 data.

The recovered component’s position and scale are consistent
with the southern/southwestern arm of the edge-brightened jet
seen in the 86 GHz GMVA image. Stacking the component over
the GMVA jet indicates a preference for an additional flux density of ∼ 60mJy to match the EHT closure phases. However, the
data do not statistically favor more complex models (an elliptical Gaussian component or a two-component component model)
over the single Gaussian model.
We emphasize two important caveats. First, while our modeling improves the data-minus-model residuals, the limited number of intermediate baselines and the single-baseline sensitivity at the relevant spatial frequencies restrict a robust morphological reconstruction: other mathematically viable structures,
including imaging artifacts consistent with the measured ( _u_, v)
sampling, cannot be fully excluded. Second, single-baseline or
small-triangle measurements are susceptible to non-closing systematics. While we rule out polarization leakage as the origin
of the signal and have performed imaging and synthetic data
checks, unknown systematic errors cannot be completely ruled
out. For these reasons, we conservatively treat the recovered
Gaussian flux density as an upper limit on resolved jet base emission at spatial scales probed by the PV–NOEMA and KP–SMT
baselines.

Finally, the presence of this faint component does not conflict
with earlier EHT reconstructions from 2017, 2018, and 2021.
The arrays in earlier years lacked the intermediate baselines required to detect emission at the spatial scales we probe here,
so ring-only models adequately describe the earlier epochs. Excellent fitting quality, synthetic data tests, and the negligible effect of the Gaussian model on baselines longer than PV-NOEMA
also indicate the robustness of the ring-only images obtained in
2021. The detection (or upper limit) reported here therefore complements earlier results and constrains where the EHT missing


Article number, page 11

_A&A proofs:_ manuscript no. main



flux cannot reside: resolved, brighter emission ∼ 100 − 300 µas
southeast and northeast relative to the ring is firmly ruled out by
these closure triangles.
In summary, the 2021 EHT data provide the first constraints
at 230 GHz on faint, asymmetric emission at intermediate scales
near M87*, locating a plausible component southwest of the ring
with a flux density < 0.1 Jy. Although this result is robust under the assumptions and tests performed, definitive confirmation
and more precise constraints will require future EHT observations with higher sensitivity and improved intermediate-baseline
coverage via additional stations and expanded frequency range.


**References**


Abramowski, A., Acero, F., Aharonian, F., et al. 2012, ApJ, 746, 151
Akiyama, K., Lu, R.-S., Fish, V. L., et al. 2015, ApJ, 807, 150
Arras, P., Frank, P., Haim, P., et al. 2022, Nature Astronomy, 6, 259
Asada, K. & Nakamura, M. 2012, ApJ, 745, L28
Asada, K., Nakamura, M., & Pu, H.-Y. 2016, ApJ, 833, 56
Blackburn, L., Pesce, D. W., Johnson, M. D., et al. 2020, ApJ, 894, 31
Blandford, R. D. & Payne, D. G. 1982, MNRAS, 199, 883
Blandford, R. D. & Znajek, R. L. 1977, MNRAS, 179, 433
Bower, G. C., Dexter, J., Markoff, S., et al. 2015, ApJ, 811, L6
Broderick, A. E., Gold, R., Karami, M., et al. 2020a, ApJ, 897, 139
Broderick, A. E. & Pesce, D. W. 2020, ApJ, 904, 126
Broderick, A. E., Pesce, D. W., Gold, R., et al. 2022, ApJ, 935, 61
Broderick, A. E., Pesce, D. W., Tiede, P., Pu, H.-Y., & Gold, R. 2020b, ApJ, 898,
9
Carilli, C. L. & Thyagarajan, N. 2022, ApJ, 924, 125
Chael, A. A., Johnson, M. D., Bouman, K. L., et al. 2018, ApJ, 857, 23
Chael, A. A., Johnson, M. D., Narayan, R., et al. 2016, ApJ, 829, 11
Cui, Y., Hada, K., Kawashima, T., et al. 2023, Nature, 621, 711
Deller, A. T., Brisken, W. F., Phillips, C. J., et al. 2011, PASP, 123, 275
Deller, A. T., Tingay, S. J., Bailes, M., & West, C. 2007, PASP, 119, 318
Doeleman, S. S., Fish, V. L., Schenck, D. E., et al. 2012, Science, 338, 355
EHTC. 2024, arXiv e-prints, arXiv:2410.02986
EHTC, Akiyama, K., Alberdi, A., et al. 2024, A&A, 681, A79
EHTC, Akiyama, K., Alberdi, A., et al. 2023, The Astrophysical Journal Letters,
957, L20
EHTC, Akiyama, K., Alberdi, A., et al. 2019a, ApJ, 875, L1
EHTC, Akiyama, K., Alberdi, A., et al. 2019b, ApJ, 875, L2
EHTC, Akiyama, K., Alberdi, A., et al. 2019c, ApJ, 875, L3
EHTC, Akiyama, K., Alberdi, A., et al. 2019d, ApJ, 875, L4
EHTC, Akiyama, K., Alberdi, A., et al. 2019e, ApJ, 875, L5
EHTC, Akiyama, K., Alberdi, A., et al. 2019f, ApJ, 875, L6
EHTC, Akiyama, K., Alberdi, A., et al. 2025, ApJ
EHTC, Akiyama, K., Algaba, J. C., et al. 2021a, ApJ, 910, L12
EHTC, Akiyama, K., Algaba, J. C., et al. 2021b, ApJ, 910, L13
Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125,
306
Georgiev, B., Tiede, P., & von Fellenberg, Sebastiano D., a. e. 2025, The location
of the missing intrasite flux in M87*
Goddi, C., Martí-Vidal, I., Messias, H., et al. 2021, ApJ, 910, L14
Hada, K. 2017, Galaxies, 5, 2
Hada, K., Asada, K., Nakamura, M., & Kino, M. 2024, A&A Rev., 32, 5
Hada, K., Kino, M., Doi, A., et al. 2016, ApJ, 817, 131
Hada, K., Kino, M., Doi, A., et al. 2013, ApJ, 775, 70
Janssen, M., Goddi, C., van Bemmel, I. M., et al. 2019, A&A, 626, A75
Janssen, M., Radcliffe, J. F., & Wagner, J. 2022, Universe, 8, 527
Kim, J.-S., Müller, H., Nikonov, A. S., et al. 2025, Imaging a ring-like structure
and the extended jet of M87 at 86 GHz
Kim, J. Y., Krichbaum, T. P., Lu, R. S., et al. 2018, A&A, 616, A188
Kim, J.-Y., Savolainen, T., Voitsik, P., et al. 2023, ApJ, 952, 34
Leppanen, K. J., Zensus, J. A., & Diamond, P. J. 1995, AJ, 110, 2479
Lister, M. L., Aller, M. F., Aller, H. D., et al. 2018, ApJS, 234, 12
Lu, R.-S., Asada, K., Krichbaum, T. P., et al. 2023, Nature, 616, 686
Marshall, H. L., Miller, B. P., Davis, D. S., et al. 2002, ApJ, 564, 683
Martí-Vidal, I., Roy, A., Conway, J., & Zensus, A. J. 2016, A&A, 587, A143
Müller, H. 2024, A&A, 689, A299
Müller, H. & Lobanov, A. P. 2022, A&A, 666, A137
Müller, H. & Lobanov, A. P. 2023a, A&A, 673, A151
Müller, H. & Lobanov, A. P. 2023b, A&A, 672, A26
Müller, H., Mus, A., & Lobanov, A. 2023, A&A, 675, A60
Mus, A., Müller, H., & Lobanov, A. 2024a, A&A, 688, A100
Mus, A., Müller, H., Martí-Vidal, I., & Lobanov, A. 2024b, A&A, 684, A55
Nakamura, M. & Asada, K. 2013, ApJ, 775, 118
Nakamura, M., Asada, K., Hada, K., et al. 2018, ApJ, 868, 146


Article number, page 12



Nikonov, A. S., Kovalev, Y. Y., Kravchenko, E. V., Pashchenko, I. N., &
Lobanov, A. P. 2023, MNRAS, 526, 5949
Park, J., Asada, K., & Byun, D.-Y. 2023a, ApJ, 958, 27
Park, J., Asada, K., & Byun, D.-Y. 2023b, ApJ, 958, 28
Park, J., Asada, K., Nakamura, M., et al. 2021, ApJ, 922, 180
Park, J., Hada, K., Kino, M., et al. 2019, ApJ, 871, 257
Perlman, E. S., Adams, S. C., Cara, M., et al. 2011, ApJ, 743, 119
Pordes, R., Petravick, D., Kramer, B., et al. 2007, in 78, Vol. 78, J. Phys. Conf.
Ser., 012057
Röder, J., Wielgus, M., Jensen, J. B., Anand, G. S., & Tully, R. B. 2025, Astron.
Astrophys., 701, L12
Sfiligoi, I., Bradley, D. C., Holzman, B., et al. 2009, in 2, Vol. 2, 2009 WRI World
Congress on Computer Science and Information Engineering, 428–432
Shepherd, M. C. 1997, in Astronomical Society of the Pacific Conference Series,
Vol. 125, Astronomical Data Analysis Software and Systems VI, ed. G. Hunt
& H. Payne, 77
Thompson, A. R., Moran, J. M., & Swenson, Jr., G. W. 2017, Interferometry and
Synthesis in Radio Astronomy, 3rd Edition
Tiede, P. 2022, The Journal of Open Source Software, 7, 4457
von Fellenberg, S. D., García, R., Janssen, M., et al. 2025, Research Notes of the
American Astronomical Society, 9, 134
Walker, R. C., Hardee, P. E., Davies, F. B., Ly, C., & Junor, W. 2018, ApJ, 855,
128
Wielgus, M., Akiyama, K., Blackburn, L., et al. 2020, ApJ, 901, 67


1 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69,
D-53121 Bonn, Germany
2 Jansky Fellow of National Radio Astronomy Observatory, 1011
Lopezville Rd, Socorro, NM 87801, USA
3 Canadian Institute for Theoretical Astrophysics, University of
Toronto, 60 St. George Street, Toronto, ON M5S 3H8, Canada
4 Center for Astrophysics | Harvard & Smithsonian, 60 Garden
Street, Cambridge, MA 02138, USA
5 Black Hole Initiative at Harvard University, 20 Garden Street,
Cambridge, MA 02138, USA
6 Department of Astrophysics, Institute for Mathematics, Astrophysics and Particle Physics (IMAPP), Radboud University, P.O.
Box 9010, 6500 GL Nijmegen, The Netherlands
7 Perimeter Institute for Theoretical Physics, 31 Caroline Street
North, Waterloo, ON N2L 2Y5, Canada
8 Department of Physics and Astronomy, University of Waterloo,
200 University Avenue West, Waterloo, ON N2L 3G1, Canada
9 Waterloo Centre for Astrophysics, University of Waterloo, Waterloo, ON N2L 3G1, Canada
10 Steward Observatory and Department of Astronomy, University of
Arizona, 933 N. Cherry Ave., Tucson, AZ 85721, USA
11 Institut für Theoretische Physik, Goethe-Universität Frankfurt,
Max-von-Laue-Straße 1, D-60438 Frankfurt am Main, Germany
12 Mizusawa VLBI Observatory, National Astronomical Observatory
of Japan, 2-12 Hoshigaoka, Mizusawa, Oshu, Iwate 023-0861,
Japan
13 School of Space Research, Kyung Hee University, 1732,
Deogyeong-daero, Giheung-gu, Yongin-si, Gyeonggi-do 17104,
Republic of Korea
14 Institute of Astronomy and Astrophysics, Academia Sinica, 11F
of Astronomy-Mathematics Building, AS/NTU No. 1, Sec. 4,
Roosevelt Rd., Taipei 106216, Taiwan, R.O.C.
15 Instituto de Astrofísica de Andalucía-CSIC, Glorieta de la Astronomía s/n, E-18008 Granada, Spain
16 Massachusetts Institute of Technology Haystack Observatory, 99
Millstone Road, Westford, MA 01886, USA
17 National Astronomical Observatory of Japan, 2-21-1 Osawa,
Mitaka, Tokyo 181-8588, Japan
18 Departament d’Astronomia i Astrofísica, Universitat de València,
C. Dr. Moliner 50, E-46100 Burjassot, València, Spain
19 Department of Physics, Faculty of Science, Universiti Malaya,
50603 Kuala Lumpur, Malaysia
20 Department of Physics & Astronomy, The University of Texas at
San Antonio, One UTSA Circle, San Antonio, TX 78249, USA
21 Physics & Astronomy Department, Rice University, Houston, TX
77005-1827, USA
22 Observatori Astronòmic, Universitat de València, C. Catedrático

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations



José Beltrán 2, E-46980 Paterna, València, Spain
23 Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, SE-43992 Onsala,
Sweden
24 Yale Center for Astronomy & Astrophysics, Yale University, 52
Hillhouse Avenue, New Haven, CT 06511, USA
25 Astronomy Department, Universidad de Concepción, Casilla
160-C, Concepción, Chile
26 Department of Physics, University of Illinois, 1110 West Green
Street, Urbana, IL 61801, USA
27 Fermi National Accelerator Laboratory, MS209, P.O. Box 500,
Batavia, IL 60510, USA
28 Department of Astronomy and Astrophysics, University of
Chicago, 5640 South Ellis Avenue, Chicago, IL 60637, USA
29 East Asian Observatory, 660 N. A’ohoku Place, Hilo, HI 96720,
USA
30 James Clerk Maxwell Telescope (JCMT), 660 N. A’ohoku Place,
Hilo, HI 96720, USA
31 California Institute of Technology, 1200 East California Boulevard,
Pasadena, CA 91125, USA
32 Institute of Astronomy and Astrophysics, Academia Sinica, 645 N.
A’ohoku Place, Hilo, HI 96720, USA
33 Department of Physics and Astronomy, University of Hawaii at
Manoa, 2505 Correa Road, Honolulu, HI 96822, USA
34 Institut de Radioastronomie Millimétrique (IRAM), 300 rue de la
Piscine, F-38406 Saint Martin d’Hères, France
35 Department of Astronomy, University of Massachusetts, Amherst,
MA 01003, USA
36 Instituto de Astronomia, Geofísica e Ciências Atmosféricas,
Universidade de São Paulo, R. do Matão, 1226, São Paulo, SP
05508-090, Brazil
37 Kavli Institute for Cosmological Physics, University of Chicago,
5640 South Ellis Avenue, Chicago, IL 60637, USA
38 Department of Physics, University of Chicago, 5720 South Ellis
Avenue, Chicago, IL 60637, USA
39 Enrico Fermi Institute, University of Chicago, 5640 South Ellis
Avenue, Chicago, IL 60637, USA
40 Princeton Gravity Initiative, Jadwin Hall, Princeton University,
Princeton, NJ 08544, USA
41 Data Science Institute, University of Arizona, 1230 N. Cherry
Ave., Tucson, AZ 85721, USA
42 Program in Applied Mathematics, University of Arizona, 617 N.
Santa Rita, Tucson, AZ 85721, USA
43 Department of Physics, University of Maryland, 7901 Regents
Drive, College Park, MD 20742, USA
44 Cornell Center for Astrophysics and Planetary Science, Cornell
University, Ithaca, NY 14853, USA
45 Shanghai Astronomical Observatory, Chinese Academy of Sciences, 80 Nandan Road, Shanghai 200030, People’s Republic of
China
46 Key Laboratory of Radio Astronomy and Technology, Chinese
Academy of Sciences, A20 Datun Road, Chaoyang District,
Beijing, 100101, People’s Republic of China
47 Korea Astronomy and Space Science Institute, Daedeok-daero
776, Yuseong-gu, Daejeon 34055, Republic of Korea
48 Department of Astronomy, Yonsei University, Yonsei-ro 50,
Seodaemun-gu, 03722 Seoul, Republic of Korea
49 WattTime, 490 43rd Street, Unit 221, Oakland, CA 94609, USA
50 Department of Astronomy, University of Illinois at UrbanaChampaign, 1002 West Green Street, Urbana, IL 61801, USA
51 Instituto de Astronomía, Universidad Nacional Autónoma de
México (UNAM), Apdo Postal 70-264, Ciudad de México,
México
52 Institute of Astrophysics, Central China Normal University, Wuhan
430079, People’s Republic of China
53 Department of Astrophysical Sciences, Peyton Hall, Princeton
University, Princeton, NJ 08544, USA
54 NASA Hubble Fellowship Program, Einstein Fellow
55 Dipartimento di Fisica “E. Pancini”, Università di Napoli “Federico II”, Compl. Univ. di Monte S. Angelo, Edificio G, Via



Cinthia, I-80126, Napoli, Italy
56 INFN Sez. di Napoli, Compl. Univ. di Monte S. Angelo, Edificio
G, Via Cinthia, I-80126, Napoli, Italy
57 Wits Centre for Astrophysics, University of the Witwatersrand,
1 Jan Smuts Avenue, Braamfontein, Johannesburg 2050, South
Africa
58 Department of Physics, University of Pretoria, Hatfield, Pretoria
0028, South Africa
59 Centre for Radio Astronomy Techniques and Technologies,
Department of Physics and Electronics, Rhodes University,
Makhanda 6140, South Africa
60 LESIA, Observatoire de Paris, Université PSL, CNRS, Sorbonne
Université, Université de Paris, 5 place Jules Janssen, F-92195
Meudon, France
61 JILA and Department of Astrophysical and Planetary Sciences,
University of Colorado, Boulder, CO 80309, USA
62 Tsung-Dao Lee Institute, Shanghai Jiao Tong University, Shengrong Road 520, Shanghai, 201210, People’s Republic of China
63 National Astronomical Observatories, Chinese Academy of
Sciences, 20A Datun Road, Chaoyang District, Beijing 100101,
PR China
64 Las Cumbres Observatory, 6740 Cortona Drive, Suite 102, Goleta,
CA 93117-5575, USA
65 Department of Physics, University of California, Santa Barbara,
CA 93106-9530, USA
66 National Radio Astronomy Observatory, 520 Edgemont Road,
Charlottesville, VA 22903, USA
67 Department of Electrical Engineering and Computer Science,
Massachusetts Institute of Technology, 32-D476, 77 Massachusetts
Ave., Cambridge, MA 02142, USA
68 Google Research, 355 Main St., Cambridge, MA 02142, USA
69 Institut für Theoretische Physik und Astrophysik, Universität
Würzburg, Emil-Fischer-Str. 31, D-97074 Würzburg, Germany
70 Department of History of Science, Harvard University, Cambridge,
MA 02138, USA
71 Department of Physics, Harvard University, Cambridge, MA
02138, USA
72 NCSA, University of Illinois, 1205 W. Clark St., Urbana, IL
61801, USA
73 Dipartimento di Fisica, Università degli Studi di Cagliari, SP
Monserrato-Sestu km 0.7, I-09042 Monserrato (CA), Italy
74 INAF - Osservatorio Astronomico di Cagliari, via della Scienza 5,
I-09047 Selargius (CA), Italy
75 INFN, sezione di Cagliari, I-09042 Monserrato (CA), Italy
76 Institute for Mathematics and Interdisciplinary Center for Scientific Computing, Heidelberg University, Im Neuenheimer Feld
205, Heidelberg 69120, Germany
77 Institut für Theoretische Physik, Universität Heidelberg,
Philosophenweg 16, 69120 Heidelberg, Germany
78 CP3-Origins, University of Southern Denmark, Campusvej 55,
DK-5230 Odense, Denmark
79 Instituto Nacional de Astrofísica, Óptica y Electrónica. Apartado
Postal 51 y 216, 72000. Puebla Pue., México
80 Consejo Nacional de Humanidades, Ciencia y Tecnología, Av.
Insurgentes Sur 1582, 03940, Ciudad de México, México
81 Key Laboratory for Research in Galaxies and Cosmology, Chinese
Academy of Sciences, Shanghai 200030, People’s Republic of
China
82 Graduate School of Science, Nagoya City University, Yamanohata
1, Mizuho-cho, Mizuho-ku, Nagoya, 467-8501, Aichi, Japan
83 Department of Physics, McGill University, 3600 rue University,
Montréal, QC H3A 2T8, Canada
84 Trottier Space Institute at McGill, 3550 rue University, Montréal,
QC H3A 2A7, Canada
85 NOVA Sub-mm Instrumentation Group, Kapteyn Astronomical
Institute, University of Groningen, Landleven 12, 9747 AD
Groningen, The Netherlands
86 Department of Astronomy, School of Physics, Peking University,
Beijing 100871, People’s Republic of China
87 Kavli Institute for Astronomy and Astrophysics, Peking University,


Article number, page 13

_A&A proofs:_ manuscript no. main



Beijing 100871, People’s Republic of China
88 Department of Astronomical Science, The Graduate University for
Advanced Studies (SOKENDAI), 2-21-1 Osawa, Mitaka, Tokyo
181-8588, Japan
89 Department of Astronomy, Graduate School of Science, The
University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033,
Japan
90 The Institute of Statistical Mathematics, 10-3 Midori-cho,
Tachikawa, Tokyo, 190-8562, Japan
91 Department of Statistical Science, The Graduate University for
Advanced Studies (SOKENDAI), 10-3 Midori-cho, Tachikawa,
Tokyo 190-8562, Japan
92 Kavli Institute for the Physics and Mathematics of the Universe,
The University of Tokyo, 5-1-5 Kashiwanoha, Kashiwa, 277-8583,
Japan
93 Leiden Observatory, Leiden University, Postbus 2300, 9513 RA
Leiden, The Netherlands
94 ASTRAVEO LLC, PO Box 1668, Gloucester, MA 01931, USA
95 Applied Materials Inc., 35 Dory Road, Gloucester, MA 01930,
USA
96 Institute for Astrophysical Research, Boston University, 725
Commonwealth Ave., Boston, MA 02215, USA
97 University of Science and Technology, Gajeong-ro 217, Yuseonggu, Daejeon 34113, Republic of Korea
98 National Institute of Technology, Ichinoseki College, Takanashi,
Hagisho, Ichinoseki, Iwate, 021-8511, Japan
99 Joint Institute for VLBI ERIC (JIVE), Oude Hoogeveensedijk 4,
7991 PD Dwingeloo, The Netherlands
100 CSIRO, Space and Astronomy, PO Box 76, Epping, NSW 1710,
Australia
101 Department of Physics, Ulsan National Institute of Science and
Technology (UNIST), Ulsan 44919, Republic of Korea
102 Department of Physics, Korea Advanced Institute of Science
and Technology (KAIST), 291 Daehak-ro, Yuseong-gu, Daejeon
34141, Republic of Korea
103 Kogakuin University of Technology & Engineering, Academic
Support Center, 2665-1 Nakano, Hachioji, Tokyo 192-0015, Japan
104 Graduate School of Science and Technology, Niigata University,
8050 Ikarashi 2-no-cho, Nishi-ku, Niigata 950-2181, Japan
105 Physics Department, National Sun Yat-Sen University, No. 70,
Lien-Hai Road, Kaosiung City 80424, Taiwan, R.O.C.
106 Department of Astronomy, Kyungpook National University, 80
Daehak-ro, Buk-gu, Daegu 41566, Republic of Korea
107 School of Astronomy and Space Science, Nanjing University,
Nanjing 210023, People’s Republic of China
108 Key Laboratory of Modern Astronomy and Astrophysics, Nanjing
University, Nanjing 210023, People’s Republic of China
109 INAF-Istituto di Radioastronomia, Via P. Gobetti 101, I-40129
Bologna, Italy
110 Common Crawl Foundation, 9663 Santa Monica Blvd. 425,
Beverly Hills, CA 90210 USA
111 Instituto de Física, Pontificia Universidad Católica de Valparaíso,
Casilla 4059, Valparaíso, Chile
112 INAF-Istituto di Radioastronomia & Italian ALMA Regional
Centre, Via P. Gobetti 101, I-40129 Bologna, Italy
113 Department of Physics, National Taiwan University, No. 1, Sec. 4,
Roosevelt Rd., Taipei 106216, Taiwan, R.O.C
114 Instituto de Radioastronomía y Astrofísica, Universidad Nacional
Autónoma de México, Morelia 58089, México
115 David Rockefeller Center for Latin American Studies, Harvard
University, 1730 Cambridge Street, Cambridge, MA 02138, USA
116 Yunnan Observatories, Chinese Academy of Sciences, 650011
Kunming, Yunnan Province, People’s Republic of China
117 Center for Astronomical Mega-Science, Chinese Academy of
Sciences, 20A Datun Road, Chaoyang District, Beijing, 100012,
People’s Republic of China
118 Key Laboratory for the Structure and Evolution of Celestial Objects, Chinese Academy of Sciences, 650011 Kunming, People’s
Republic of China
119 Anton Pannekoek Institute for Astronomy, University of Amster

Article number, page 14



dam, Science Park 904, 1098 XH, Amsterdam, The Netherlands
120 Gravitation and Astroparticle Physics Amsterdam (GRAPPA)
Institute, University of Amsterdam, Science Park 904, 1098 XH
Amsterdam, The Netherlands
121 Center for Gravitation, Cosmology and Astrophysics, Department
of Physics, University of Wisconsin–Milwaukee, P.O. Box 413,
Milwaukee, WI 53201, USA
122 Deceased
123 Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura
763-0355, Santiago, Chile
124 European Southern Observatory, Alonso de Córdova 3107,
Vitacura, Casilla 19001, Santiago, Chile
125 School of Physics and Astronomy, Shanghai Jiao Tong University,
800 Dongchuan Road, Shanghai, 200240, People’s Republic of
China
126 SCOPIA Research Group, University of the Balearic Islands, Dept.
of Mathematics and Computer Science, Ctra. Valldemossa, Km
7.5, Palma 07122, Spain
127 Artificial Intelligence Research Institute of the Balearic Islands
(IAIB), Palma 07122, Spain
128 Institut de Radioastronomie Millimétrique (IRAM), Avenida
Divina Pastora 7, Local 20, E-18012, Granada, Spain
129 National Institute of Technology, Hachinohe College, 16-1 Uwanotai, Tamonoki, Hachinohe City, Aomori 039-1192, Japan
130 Research Center for Astronomy, Academy of Athens, Soranou
Efessiou 4, 115 27 Athens, Greece
131 Department of Physics, Villanova University, 800 Lancaster
Avenue, Villanova, PA 19085, USA
132 Physics Department, Washington University, CB 1105, St. Louis,
MO 63130, USA
133 Departamento de Matemática da Universidade de Aveiro and
Centre for Research and Development in Mathematics and
Applications (CIDMA), Campus de Santiago, 3810-193 Aveiro,
Portugal
134 School of Physics, Georgia Institute of Technology, 837 State St
NW, Atlanta, GA 30332, USA
135 Dunlap Institute for Astronomy and Astrophysics, University of
Toronto, 50 St. George Street, Toronto, ON M5S 3H4, Canada
136 Canadian Institute for Advanced Research, 180 Dundas St West,
Toronto, ON M5G 1Z8, Canada
137 Dipartimento di Fisica, Università di Trieste, I-34127 Trieste, Italy
138 INFN Sez. di Trieste, I-34127 Trieste, Italy
139 Department of Physics, National Taiwan Normal University, No.
88, Sec. 4, Tingzhou Rd., Taipei 116, Taiwan, R.O.C.
140 Center of Astronomy and Gravitation, National Taiwan Normal
University, No. 88, Sec. 4, Tingzhou Road, Taipei 116, Taiwan,
R.O.C.
141 Finnish Centre for Astronomy with ESO, University of Turku,
FI-20014 Turun Yliopisto, Finland
142 Aalto University Metsähovi Radio Observatory, Metsähovintie
114, FI-02540 Kylmälä, Finland
143 Gemini Observatory/NSF NOIRLab, 670 N. A’oh¯ok¯u Place, Hilo,
HI 96720, USA
144 Frankfurt Institute for Advanced Studies, Ruth-Moufang-Strasse
1, D-60438 Frankfurt, Germany
145 School of Mathematics, Trinity College, Dublin 2, Ireland
146 Julius-Maximilians-Universität Würzburg, Fakultät für Physik
und Astronomie, Institut für Theoretische Physik und Astrophysik, Lehrstuhl für Astronomie, Emil-Fischer-Str. 31, D-97074
Würzburg, Germany
147 Department of Physics, University of Toronto, 60 St. George
Street, Toronto, ON M5S 1A7, Canada
148 Department of Physics, Tokyo Institute of Technology, 2-12-1
Ookayama, Meguro-ku, Tokyo 152-8551, Japan
149 Hiroshima Astrophysical Science Center, Hiroshima University,
1-3-1 Kagamiyama, Higashi-Hiroshima, Hiroshima 739-8526,
Japan
150 Aalto University Department of Electronics and Nanoengineering,
PL 15500, FI-00076 Aalto, Finland
151 Jeremiah Horrocks Institute, University of Central Lancashire,

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations


Preston PR1 2HE, UK
152 National Biomedical Imaging Center, Peking University, Beijing
100871, People’s Republic of China
153 College of Future Technology, Peking University, Beijing 100871,
People’s Republic of China
154 Tokyo Electron Technology Solutions Limited, 52 Matsunagane,
Iwayado, Esashi, Oshu, Iwate 023-1101, Japan
155 Department of Physics and Astronomy, University of Lethbridge,
Lethbridge, Alberta T1K 3M4, Canada
156 Netherlands Organisation for Scientific Research (NWO), Postbus
93138, 2509 AC Den Haag, The Netherlands
157 Frontier Research Institute for Interdisciplinary Sciences, Tohoku
University, Sendai 980-8578, Japan
158 Astronomical Institute, Tohoku University, Sendai 980-8578,
Japan
159 Department of Physics and Astronomy, Seoul National University,
Gwanak-gu, Seoul 08826, Republic of Korea
160 SNU Astronomy Research Center, Seoul National University,
Gwanak-gu, Seoul 08826, Republic of Korea
161 ASTRON, Oude Hoogeveensedijk 4, 7991 PD Dwingeloo, The
Netherlands
162 University of New Mexico, Department of Physics and Astronomy,
Albuquerque, NM 87131, USA
163 Centre for Mathematical Plasma Astrophysics, Department of
Mathematics, KU Leuven, Celestijnenlaan 200B, B-3001 Leuven,
Belgium
164 Physics Department, Brandeis University, 415 South Street,
Waltham, MA 02453, USA
165 Tuorla Observatory, Department of Physics and Astronomy,
University of Turku, FI-20014 Turun Yliopisto, Finland
166 Radboud Excellence Fellow of Radboud University, Nijmegen,
The Netherlands
167 School of Natural Sciences, Institute for Advanced Study, 1
Einstein Drive, Princeton, NJ 08540, USA
168 School of Physics, Huazhong University of Science and Technology, Wuhan, Hubei, 430074, People’s Republic of China
169 Mullard Space Science Laboratory, University College London,
Holmbury St. Mary, Dorking, Surrey, RH5 6NT, UK
170 Center for Astronomy and Astrophysics and Department of
Physics, Fudan University, Shanghai 200438, People’s Republic of
China
171 Astronomy Department, University of Science and Technology of
China, Hefei 230026, People’s Republic of China
172 Department of Physics and Astronomy, Michigan State University,
567 Wilson Rd, East Lansing, MI 48824, USA



Article number, page 15

_F_ 0 (Jy)



_x_ ( _µ_ as)



_y_ ( _µ_ as)



_A&A proofs:_ manuscript no. main


_σ_ ( _µ_ as)



_F_ 1 (Jy)



_F_ 2 (Jy)



_x_ 1 ( _µ_ as)



_x_ 2 ( _µ_ as)



_y_ 1 ( _µ_ as)



_y_ 2 ( _µ_ as)



_σ_ 1 ( _µ_ as)



_σ_ 2 ( _µ_ as)



Φ 2 ( _[◦]_ )



_R_ 1



_R_ 2



Φ 1 ( _[◦]_ )



**Fig. A.1.** Corner plot showcasing our estimates for the location ( _x_, y in
units of µ as), flux ( _F_ 0 in units of Jy), and width (σ in units of µ as) of
the Gaussian toy model.



**Fig. A.3.** Same as Figure A.1 but for two asymmetric Gaussian toy models. See Section 4.4 for more details.



**Low Pol v.s. Truth**

1.000


0.995


0.990


0.985


1.0


0.9


0.8


0.7


0.6


0.5


2017 2018 2021



**Low Pol v.s. High Pol**


2017 2018 2021



GPCal

DoG-HiT

ehtim
MOEA/D
Comrade

Themis



_F_ 0 (Jy)



_x_ ( _µ_ as)



_y_ ( _µ_ as)



_σ_ ( _µ_ as)



_R_



Φ( _[◦]_ )



**Fig.** **A.2.** Same as Figure A.1 but with two additional parameters: R,
the ratio of fwhm maj and fwhm min, and Φ, the rotation angle, of the
asymmetric Gaussian toy model. See Section 4.3 for more details.


**Appendix A:** **Corner plots**


In the following, we show the MCMC corner plots of the three
model fits that we performed. Figure A.1 displays the corner plot
of the four-parameter Gaussian model, Figure A.2 displays the
corner plot of the six-parameter Gaussian model, and Figure A.3
displays the fit with a twelve-parameter double Gaussian model.


Article number, page 16



**Fig.** **B.1.** Figure D3 of EHTC et al. (2025). Cross-correlation between
the recovered ring model and synthetic ground truth model for seven
different imaging techniques in 2017, 2018, and 2021. The synthetic
data included a large-scale jet component. Upper panels show the crosscorrelation in total intensity, lower panels in polarization. Despite the
synthetic data containing a large scale jet component, the black hole
shadow has been recovered for all methods and all years with exceptional accuracy, achieving cross-correlations - 0.995 in total intensity
in 2021.


**Appendix B:** **Effect on visibility amplitude**


In Figure B.1 we show the evaluation of the synthetic data
test performed with an extended jet component in EHTC et al.
(2025). In Figure B.2 we show the amplitudes of the ring model,
the fiducial model, and the difference between the two models as
a function of the projected baseline length.

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations





















10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]





**Fig.** **B.2.** Left panel: comparison of the predicted amplitudes for the
`DoG-HIT` ring-only image (red markers), the `DoG-HIT` image with additional Gaussian component (blue markers), and the self-calibrated visibility amplitudes (green markers) as a function of projected baseline
length. Right panel: the difference between the predicted visibilities for
the `DoG-HIT` model and `DoG-HIT` with the additional Gaussian component as a function of projected baseline length. The plot demonstrates
that the additional Gaussian component has no sizeable effect on baselines longer than PV-NOEMA.


**Appendix C:** **Parameter exploration for 6 parameter**
**Gaussian model**


We demonstrate the effect of adding two additional degrees of
freedom to the model with an asymmetric Gaussian component
that can be rotated around its axis. In Figure B.3 we show that
these parameters can be constrained in the extreme case of a
very asymmetric Gaussian component. However, these parameters are poorly constrained.


**Appendix D:** **Impact of non-closing errors**


Because the phase signature of the offset Gaussian component(s)
is small, we cannot completely rule out systematic effects as an
origin. Here, we assess the impact of one known non-closing error: polarization leakage. Polarization leakage causes signal dispersion from one correlation of polarization handedness (e.g.,
_RR_ ) to another (e.g., _LL_ ), and is baseline-based in nature (e.g.,
Müller 2024). One data-driven test to rule out leakage as the
cause of the bump and offset is to compare the phase-residuals
of the _RR_ − _LL_ closure phases on the respective triangles (Figure D.1). Under the assumptions that there is no significant leakage and that circular polarization is −→ 0, the difference between
the parallel hands closure phases is zero. While there is a small
offset on the ALMA-PV-NOEMA triangle, neither the bump nor
the offset can be explained by a difference between the parallel hands, and we thus conclude that the signal is not caused by
polarization leakage. The difference in the ALMA-PV-NOEMA
triangle may be caused by either intrinsic circular polarization of
the source or by leakage, and we thus place a limit on this type
of non-closing error of ∼ 1 [◦] .


**Appendix E:** **Acknowledgments**


_Acknowledgements._ We thank the anonymous reviewer for their insightful comments and suggestions. Saurabh received financial support for this research from
the International Max Planck Research School (IMPRS) for Astronomy and Astrophysics at the Universities of Bonn and Cologne. This work was supported
by the M2FINDERS project funded by the European Research Council (ERC)
under the European Union’s Horizon 2020 Research and Innovation Programme
(Grant Agreement No. 101018682). SDvF gratefully acknowledges the support
of the Alexander von Humboldt Foundation through a Feodor Lynen Fellowship and thanks CITA for their hospitality and collaboration. The Event Horizon


|F0 = 0 .07 Jy<br>200 µas (a)|Col2|F0 = 0 .08 Jy F0 = 0<br>(b)|Col4|.09 Jy F0 = 0 .<br>(c)|11 Jy<br>(d)|Col7|
|---|---|---|---|---|---|---|
|AA-PV-NN|AA-PV-NN||||||
||||||||
|AA-SMT-KP|AA-SMT-KP||||||
||||||||
|(e)<br>_R_ = 1.3|(e)<br>_R_ = 1.3|(f)<br>_R_ = 1.1<br>_R_ = 0.|(f)<br>_R_ = 1.1<br>_R_ = 0.|(g)<br>8<br>_R_ = 0.|(h)<br>4||
||||||||
||||||||
||||||||
||||||||
|(i)<br>Φ = -22 _◦_|(i)<br>Φ = -22 _◦_|(j)<br>Φ = -10 _◦_<br>Φ = -5|(j)<br>Φ = -10 _◦_<br>Φ = -5|(k)<br> _◦_<br>Φ = 20|(l)<br> _◦_||
||||||||
||||||||
||||||||
||||||||
|(m)<br>_x_pos = -260 _µ_as|(m)<br>_x_pos = -260 _µ_as|(n)<br>_x_pos = -180 _µ_as<br>_x_pos =|(n)<br>_x_pos = -180 _µ_as<br>_x_pos =|(o)<br> -60 _µ_as<br>_x_pos =|(p)<br> 180 _µ_as||
||||||||
||||||||
||||||||
||||||||
|(q)<br>_y_pos = -90 _µ_as|(q)<br>_y_pos = -90 _µ_as|(r)<br>_y_pos = -80 _µ_as<br>_y_pos =|(r)<br>_y_pos = -80 _µ_as<br>_y_pos =|(s)<br>60 _µ_as<br>_y_pos =|(t)<br>180 _µ_as||
||||||||
||||||||
||||||||
||||||||
|(u)<br>_σ_s = 128 _µ_as|(u)<br>_σ_s = 128 _µ_as|(v)<br>_σ_s = 110 _µ_as<br>_σ_s = 60|(v)<br>_σ_s = 110 _µ_as<br>_σ_s = 60|(w)<br> _µ_as<br>_σ_s = 20|(x)<br> _µ_as||
||||||||
||||||||
||||||||
||||||||
|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|3<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>17<br>19<br>21<br>UTC(h)<br>13<br>15<br>1<br>UT|



**Fig. B.3.** Same as Figure 3, but with asymmetry and position angle as
additional parameters.


Telescope Collaboration thanks the following organizations and programs: the
Academia Sinica; the Research Council of Finland (project 362572); the Agencia Nacional de Investigación y Desarrollo (ANID), Chile via NCN19_058 (TI

Article number, page 17



5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5


5

0


_−_ 5


0


_−_ 5

_A&A proofs:_ manuscript no. main



**Fig. D.1.** Comparison of the _RR_ (orange) and _LL_ (green) closure phases
on the ALMA-NOEMA-PV (top) and ALMA-KP-SMT triangles (bottom). The red line indicates the `DoG-HIT` ring model, the magenta line
indicates the `DoG-HIT` model with an additional Gaussian component.


TANs), Fondecyt 1221421 and BASAL FB210003; the Alexander von Humboldt Stiftung (including the Feodor Lynen Fellowship); an Alfred P. Sloan Research Fellowship; Allegro, the European ALMA Regional Centre node in the
Netherlands, the NL astronomy research network NOVA and the astronomy institutes of the University of Amsterdam, Leiden University, and Radboud University; the ALMA North America Development Fund; the Astrophysics and
High Energy Physics programme by MCIN (with funding from European Union
NextGenerationEU, PRTR-C17I1); the Black Hole Initiative, which is funded
by grants from the John Templeton Foundation (60477, 61497, 62286) and the
Gordon and Betty Moore Foundation (Grant GBMF-8273) - although the opinions expressed in this work are those of the author and do not necessarily reflect the views of these Foundations; the Brinson Foundation; the Canada Research Chairs (CRC) program; Chandra DD7-18089X and TM6-17006X; the
China Scholarship Council; the China Postdoctoral Science Foundation fellowships (2020M671266, 2022M712084); ANID through Fondecyt Postdoctorado
(project 3250762); Conicyt through Fondecyt Postdoctorado (project 3220195);
Consejo Nacional de Humanidades, Ciencia y Tecnología (CONAHCYT, Mexico, projects U0004-246083, U0004-259839, F0003-272050, M0037-279006,
F0003-281692, 104497, 275201, 263356, CBF2023-2024-1102, 257435); the
Colfuturo Scholarship; the Consejo Superior de Investigaciones Científicas
(grant 2019AEP112); the Delaney Family via the Delaney Family John A.
Wheeler Chair at Perimeter Institute; Dirección General de Asuntos del Personal
Académico-Universidad Nacional Autónoma de México (DGAPA-UNAM,
projects IN112820 and IN108324); the Dutch Research Council (NWO) for
the VICI award (grant 639.043.513), the grant OCENW.KLEIN.113, and the
Dutch Black Hole Consortium (with project No. NWA 1292.19.202) of the research programme the National Science Agenda; the Dutch National Supercomputers, Cartesius and Snellius (NWO grant 2021.013); the EACOA Fellowship awarded by the East Asia Core Observatories Association, which consists of the Academia Sinica Institute of Astronomy and Astrophysics, the
National Astronomical Observatory of Japan, Center for Astronomical MegaScience, Chinese Academy of Sciences, and the Korea Astronomy and Space
Science Institute; the European Research Council (ERC) Synergy Grant “BlackHoleCam: Imaging the Event Horizon of Black Holes” (grant 610058) and
Synergy Grant “BlackHolistic: Colour Movies of Black Holes: Understanding
Black Hole Astrophysics from the Event Horizon to Galactic Scales” (grant
10107164); the European Union Horizon 2020 research and innovation programme under grant agreements RadioNet (No. 730562), M2FINDERS (No.
101018682); the European Research Council for advanced grant “JETSET:
Launching, propagation and emission of relativistic jets from binary mergers
and across mass scales” (grant No. 884631); the European Horizon Europe staff
exchange (SE) programme HORIZON-MSCA-2021-SE-01 grant NewFunFiCO


Article number, page 18



(No. 10108625); the Horizon ERC Grants 2021 programme under grant agreement No. 101040021; the FAPESP (Fundação de Amparo á Pesquisa do Estado de São Paulo) under grant 2021/01183-8; the Fondes de Recherche Nature et Technologies (FRQNT); the Fondo CAS-ANID folio CAS220010; the
Generalitat Valenciana (grants APOSTD/2018/177 and ASFAE/2022/018) and
GenT Program (project CIDEGENT/2018/021); the Gordon and Betty Moore
Foundation (GBMF-3561, GBMF-5278, GBMF-10423); the Institute for Advanced Study; the ICSC – Centro Nazionale di Ricerca in High Performance
Computing, Big Data and Quantum Computing, funded by European Union –
NextGenerationEU; the Istituto Nazionale di Fisica Nucleare (INFN) sezione
di Napoli, iniziative specifiche TEONGRAV; the International Max Planck Research School for Astronomy and Astrophysics at the Universities of Bonn
and Cologne; the Italian Ministry of University and Research (MUR)– Project
CUP F53D23001260001, funded by the European Union – NextGenerationEU;
Deutsche Forschungsgemeinschaft (DFG) research grant “Jet physics on horizon
scales and beyond” (grant No. 443220636) and DFG research grant 443220636;
Joint Columbia/Flatiron Postdoctoral Fellowship (research at the Flatiron Institute is supported by the Simons Foundation); the Japan Ministry of Education,
Culture, Sports, Science and Technology (MEXT; grant JPMXP1020200109);
the Japan Society for the Promotion of Science (JSPS) Grant-in-Aid for JSPS
Research Fellowship (JP17J08829); the Joint Institute for Computational Fundamental Science, Japan; the Key Research Program of Frontier Sciences, Chinese Academy of Sciences (CAS, grants QYZDJ-SSW-SLH057, QYZDJSSWSYS008, ZDBS-LY-SLH011); the Leverhulme Trust Early Career Research Fellowship; the Max-Planck-Gesellschaft (MPG); the Max Planck Partner Group
of the MPG and the CAS; the MEXT/JSPS KAKENHI (grants 18KK0090,
JP21H01137, JP18H03721, JP18K13594, 18K03709, JP19K14761, 18H01245,
25120007, 19H01943, 21H01137, 21H04488, 22H00157, 23K03453); the
MICINN Research Projects PID2019-108995GB-C22, PID2022-140888NBC22; the MIT International Science and Technology Initiatives (MISTI) Funds;
the Ministry of Science and Technology (MOST) of Taiwan (103-2119-M001-010-MY2, 105-2112-M-001-025-MY3, 105-2119-M-001-042, 106-2112M-001-011, 106-2119-M-001-013, 106-2119-M-001-027, 106-2923-M-001005, 107-2119-M-001-017, 107-2119-M-001-020, 107-2119-M-001-041, 1072119-M-110-005, 107-2923-M-001-009, 108-2112-M-001-048, 108-2112-M001-051, 108-2923-M-001-002, 109-2112-M-001-025, 109-2124-M-001-005,
109-2923-M-001-001, 110-2112-M-001-033, 110-2124-M-001-007 and 1102923-M-001-001); the National Science and Technology Council (NSTC) of
Taiwan (111-2124-M-001-005, 112-2124-M-001-014, 112-2112-M-003-010MY3, and 113-2124-M-001-008); the Ministry of Education (MoE) of Taiwan Yushan Young Scholar Program; the Physics Division, National Center for Theoretical Sciences of Taiwan; the National Aeronautics and Space
Administration (NASA, Fermi Guest Investigator grant 80NSSC23K1508,
NASA Astrophysics Theory Program grant 80NSSC20K0527, NASA NuSTAR
award 80NSSC20K0645); NASA Hubble Fellowship Program Einstein Fellowship; NASA Hubble Fellowship grants HST-HF2-51431.001-A, HST-HF251482.001-A, HST-HF2-51539.001-A, HST-HF2-51552.001A awarded by the
Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS526555; the National Institute of Natural Sciences (NINS) of Japan; the National
Key Research and Development Program of China (grant 2016YFA0400704,
2017YFA0402703, 2016YFA0400702); the National Science and Technology
Council (NSTC, grants NSTC 111-2112-M-001 -041, NSTC 111-2124-M001-005, NSTC 112-2124-M-001-014); the US National Science Foundation
(NSF, grants AST-0096454, AST-0352953, AST-0521233, AST-0705062, AST0905844, AST-0922984, AST-1126433, OIA-1126433, AST-1140030, DGE1144085, AST-1207704, AST-1207730, AST-1207752, MRI-1228509, OPP1248097, AST-1310896, AST-1440254, AST-1555365, AST-1614868, AST1615796, AST-1715061, AST-1716327, AST-1726637, OISE-1743747, AST1743747, AST-1816420, AST-1935980, AST-1952099, AST-2034306, AST2205908, AST-2307887, AST-2407810); NSF Astronomy and Astrophysics
Postdoctoral Fellowship (AST-1903847); the Natural Science Foundation of
China (grants 11650110427, 10625314, 11721303, 11725312, 11873028,
11933007, 11991052, 11991053, 12192220, 12192223, 12273022, 12325302,
12303021); the Natural Sciences and Engineering Research Council of Canada
(NSERC); the National Research Foundation of Korea (the Global PhD Fellowship Grant: grants NRF-2015H1A2A1033752; the Korea Research Fellowship
Program: NRF-2015H1D3A1066561; Brain Pool Program: RS-2024-00407499;
Basic Research Support Grant 2019R1F1A1059721, 2021R1A6A3A01086420,
2022R1C1C1005255, RS-2022-NR071771, 2022R1F1A1075115); the POSCO
Science Fellowship of the POSCO TJ Park Foundation; NOIRLab, which
is managed by the Association of Universities for Research in Astronomy
(AURA) under a cooperative agreement with the National Science Foundation; Onsala Space Observatory (OSO) national infrastructure, for the provisioning of its facilities/observational support (OSO receives funding through
the Swedish Research Council under grant 2017-00648); the Perimeter Institute for Theoretical Physics (research at Perimeter Institute is supported
by the Government of Canada through the Department of Innovation, Science and Economic Development and by the Province of Ontario through

Saurabh et al.: Jet base emission of M87* in 2021 EHT Observations



the Ministry of Research, Innovation and Science); the Portuguese Foundation for Science and Technology (FCT) grants (Individual CEEC program
– 5th edition, CIDMA through the FCT Multi-Annual Financing Program
for R&D Units UID/04106, CERN/FIS-PAR/0024/2021, 2022.04560.PTDC);
the Princeton Gravity Initiative; the Spanish Ministerio de Ciencia, Innovación y Universidades (grants PID2022-140888NB-C21, PID2022-140888NBC22, PID2023-147883NB-C21, RYC2023-042988-I); the Severo Ochoa grant
CEX2021-001131-S funded by MICIU/AEI/10.13039/501100011033; The European Union’s Horizon Europe research and innovation program under grant
agreement No. 101093934 (RADIOBLOCKS); The European Union “NextGenerationEU”, the Recovery, Transformation and Resilience Plan, the CUII of
the Andalusian Regional Government and the Spanish CSIC through grant
AST22_00001_Subproject_10; “la Caixa” Foundation (ID 100010434) through
fellowship codes LCF/BQ/DI22/11940027 and LCF/BQ/DI22/11940030; the
University of Pretoria for financial aid in the provision of the new Cluster
Server nodes and SuperMicro (USA) for a SEEDING GRANT approved toward these nodes in 2020; the Shanghai Municipality orientation program of
basic research for international scientists (grant no. 22JC1410600); the Shanghai Pilot Program for Basic Research, Chinese Academy of Science, Shanghai Branch (JCYJ-SHFY-2021-013); the Simons Foundation (grant 00001470);
the Spanish Ministry for Science and Innovation grant CEX2021-001131-S
funded by MCIN/AEI/10.13039/501100011033; the Spinoza Prize SPI 78-409;
the South African Research Chairs Initiative, through the South African Radio Astronomy Observatory (SARAO, grant ID 77948), which is a facility
of the National Research Foundation (NRF), an agency of the Department of
Science and Innovation (DSI) of South Africa; the Swedish Research Council (VR); the Taplin Fellowship; the Toray Science Foundation; the UK Science and Technology Facilities Council (grant no. ST/X508329/1); the US
Department of Energy (USDOE) through the Los Alamos National Laboratory (operated by Triad National Security, LLC, for the National Nuclear Security Administration of the USDOE, contract 89233218CNA000001); and
the YCAA Prize Postdoctoral Fellowship. This work was also supported by
the National Research Foundation of Korea (NRF) grant funded by the Korea government(MSIT) (RS-2024-00449206). We acknowledge support from
the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior (CAPES)
of Brazil through PROEX grant number 88887.845378/2023-00. We acknowledge financial support from Millenium Nucleus NCN23_002 (TITANs) and
Comité Mixto ESO-Chile. We thank the staff at the participating observatories, correlation centers, and institutions for their enthusiastic support. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00841.V
and ADS/JAO.ALMA#2019.1.01797.V. ALMA is a partnership of the European
Southern Observatory (ESO; Europe, representing its member states), NSF, and
National Institutes of Natural Sciences of Japan, together with National Research Council (Canada), Ministry of Science and Technology (MOST; Taiwan),
Academia Sinica Institute of Astronomy and Astrophysics (ASIAA; Taiwan),
and Korea Astronomy and Space Science Institute (KASI; Republic of Korea),
in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, Associated Universities, Inc. (AUI)/NRAO, and the National Astronomical Observatory of Japan (NAOJ). The NRAO is a facility of the NSF
operated under cooperative agreement by AUI. This research used resources of
the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. Department of
Energy under contract No. DE-AC05-00OR22725; the ASTROVIVES FEDER
infrastructure, with project code IDIFEDER-2021-086; the computing cluster of
Shanghai VLBI correlator supported by the Special Fund for Astronomy from
the Ministry of Finance in China; We also thank the Center for Computational
Astrophysics, National Astronomical Observatory of Japan. This work was supported by FAPESP (Fundacao de Amparo a Pesquisa do Estado de Sao Paulo)
under grant 2021/01183-8. APEX is a collaboration between the Max-PlanckInstitut für Radioastronomie (Germany), ESO, and the Onsala Space Observatory (Sweden). The SMA is a joint project between the SAO and ASIAA and is
funded by the Smithsonian Institution and the Academia Sinica. The JCMT is operated by the East Asian Observatory on behalf of the NAOJ, ASIAA, and KASI,
as well as the Ministry of Finance of China, Chinese Academy of Sciences, and
the National Key Research and Development Program (No. 2017YFA0402700)
of China and Natural Science Foundation of China grant 11873028. Additional
funding support for the JCMT is provided by the Science and Technologies Facility Council (UK) and participating universities in the UK and Canada. The
LMT is a project operated by the Instituto Nacional de Astrófisica, Óptica, y
Electrónica (Mexico) and the University of Massachusetts at Amherst (USA).
The IRAM 30 m telescope on Pico Veleta, Spain and the NOEMA interferometer on Plateau de Bure, France are operated by IRAM and supported by CNRS
(Centre National de la Recherche Scientifique, France), MPG (Max-PlanckGesellschaft, Germany), and IGN (Instituto Geográfico Nacional, Spain). The
SMT is operated by the Arizona Radio Observatory, a part of the Steward Observatory of the University of Arizona, with financial support of operations from
the State of Arizona and financial support for instrumentation development from
the NSF. Support for SPT participation in the EHT is provided by the National



Science Foundation through award OPP-1852617 to the University of Chicago.
Partial support is also provided by the Kavli Institute of Cosmological Physics
at the University of Chicago. The SPT hydrogen maser was provided on loan
from the GLT, courtesy of ASIAA. This work used the Extreme Science and
Engineering Discovery Environment (XSEDE), supported by NSF grant ACI1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383,
and DBI-1743442. XSEDE Stampede2 resource at TACC was allocated through
TG-AST170024 and TG-AST080026N. XSEDE JetStream resource at PTI and
TACC was allocated through AST170028. This research is part of the Frontera computing project at the Texas Advanced Computing Center through the
Frontera Large-Scale Community Partnerships allocation AST20023. Frontera
is made possible by National Science Foundation award OAC-1818253. This research was done using services provided by the OSG Consortium (Pordes et al.
2007; Sfiligoi et al. 2009), which is supported by the National Science Foundation award Nos. 2030508 and 1836650. Additional work used ABACUS2.0,
which is part of the eScience center at Southern Denmark University, and the
Kultrun Astronomy Hybrid Cluster (projects Conicyt Programa de Astronomia
Fondo Quimal QUIMAL170001, Conicyt PIA ACT172033, Fondecyt Iniciacion
11170268, Quimal 220002). Simulations were also performed on the SuperMUC
cluster at the LRZ in Garching, on the LOEWE cluster in CSC in Frankfurt, on
the HazelHen cluster at the HLRS in Stuttgart, and on the Pi2.0 and Siyuan
Mark-I at Shanghai Jiao Tong University. The computer resources of the Finnish
IT Center for Science (CSC) and the Finnish Computing Competence Infrastructure (FCCI) project are acknowledged. This research was enabled in part by
support provided by Compute Ontario (http://computeontario.ca), Calcul Quebec (http://www.calculquebec.ca), and the Digital Research Alliance of Canada
(https://alliancecan.ca/en). The EHTC has received generous donations of FPGA
chips from Xilinx Inc., under the Xilinx University Program. The EHTC has benefited from technology shared under open-source license by the Collaboration for
Astronomy Signal Processing and Electronics Research (CASPER). The EHT
project is grateful to T4Science and Microsemi for their assistance with hydrogen masers. This research has made use of NASA’s Astrophysics Data System.
We gratefully acknowledge the support provided by the extended staff of the
ALMA, from the inception of the ALMA Phasing Project through the observational campaigns of 2017 and 2018. We would like to thank A. Deller and W.
Brisken for EHT-specific support with the use of DiFX. We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for
the CLEAN imaging results presented in this paper. We acknowledge the significance that Maunakea, where the SMA and JCMT EHT stations are located, has
for the indigenous Hawaiian people.


Article number, page 19


</paper>

## Items to check

```json
[
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "Synthetic EHT 2021 visibility data generated from ground truth models containing a ring image with a large-scale extended jet component (from EHTC et al. 2025).",
  "failed_quote": "All methods have been explicitly validated using synthetic data generated with the 2021 coverage, in order to assess any potential systematic biases in the reconstructions."
 },
 {
  "path": "processing.imaging.deconvolver.evidence[0]",
  "value": "DoG-HIT (multi-scale wavelet RML algorithm), along with Difmap (CLEAN), ehtim, MOEA/D, Themis, and Comrade in companion study",
  "failed_quote": "Two teams used Difmap (Shepherd 1997), in combination with the AIPS task LPCAL (Leppanen et al. 1995) and GPCAL (Park et al. 2021, 2023a,b)."
 },
 {
  "path": "processing.imaging.masking.evidence[0]",
  "value": "Multiresolution support (wavelet scale and localization mask) in DoG-HIT; tested unmasked and 1% intensity contour ring mask",
  "failed_quote": "DoG-HIT utilizes a sparsity-constraining approach, effectively defining multiresolution support, i.e., a set of statistically-significant wavelet coefficients to describe the image."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Test (1) stacking the wavelet-filtered 86 GHz GMVA jet structure onto the 230 GHz EHT ring and grid-searching its rescaled flux density, (2) gradient-descent closure-phase fitting with DoG-HIT under three masking regimes (unmasked, 1% ring-contour localized, and wavelet scale+localization constrained), (3) forward-modeling the 2021 Gaussian onto 2017/2018 Chile-LMT-SMT closure phases, and (4) chec",
  "failed_quote": "we filter out the ‘ring-components’ in the 86 GHz image by setting all small-scale wavelets to zero, then we add the 230 GHz EHT ring image and the jet emission at 86 GHz seen by the GMVA."
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "CLEAN image reconstruction of the compact ring compared against observed closure phases",
  "failed_quote": "Two teams used Difmap (Shepherd 1997), in combination with the AIPS task LPCAL (Leppanen et al. 1995) and GPCAL (Park et al. 2021, 2023a,b)."
 },
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Used in combination with Difmap for polarization calibration/imaging in EHTC et al. (2025)",
  "failed_quote": "Two teams used Difmap (Shepherd 1997), in combination with the AIPS task LPCAL (Leppanen et al. 1995) and GPCAL (Park et al. 2021, 2023a,b)."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Used in combination with Difmap for calibration/imaging in EHTC et al. (2025)",
  "failed_quote": "Two teams used Difmap (Shepherd 1997), in combination with the AIPS task LPCAL (Leppanen et al. 1995) and GPCAL (Park et al. 2021, 2023a,b)."
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Reduced chi-square on ALMA-PV-NOEMA triangle (ring-only vs symmetric Gaussian) = 1.29 (from 2.73 without jet base emission) dimensionless",
  "failed_quote": "Despite the simplicity of the model, the χ2ν is 1.29 for the bump (compared to 2.73 without the jet base emission), and 1.12 for the offset (compared to 2.52)."
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Reduced chi-square on ALMA-SMT-KP triangle (ring-only vs symmetric Gaussian) = 1.12 (from 2.52 without jet base emission) dimensionless",
  "failed_quote": "Despite the simplicity of the model, the χ2ν is 1.29 for the bump (compared to 2.73 without the jet base emission), and 1.12 for the offset (compared to 2.52)."
 },
 {
  "path": "findings_qualitative[3].evidence[1]",
  "value": "The faint intermediate-scale Gaussian component has a negligible impact on baselines longer than ~2 Glambda and did not affect the 2017 and 2018 EHT ring reconstructions.",
  "failed_quote": "Additionally, the Gaussian component identified in this work is not detectable on any baseline in the EHT longer than the PV-NOEMA baseline, and thus was not detectable/had no measurable impact on observations conducted in 2017 and 2018."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "A faint offset component southwest of the ring, aligned with the southern arm of the 86 GHz GMVA jet, explains the closure phase residuals; due to sparse intermediate-baseline coverage, its flux density is treated as an upper limit on resolved jet base emission.",
  "failed_quote": "Despite the simplicity of the model, the χ2ν is 1.29 for the bump (compared to 2.73 without the jet base emission), and 1.12 for the offset (compared to 2.52)."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "Brighter emission at intermediate scales is firmly ruled out, implying that most of the missing flux originates on larger spatial scales.",
  "failed_quote": "The detection (or upper limit) reported here therefore complements earlier results and constrains where the EHT missing flux cannot reside: resolved, brighter emission ∼ 100 − 300 µas southeast and northeast relative to the ring is firmly ruled out by these closure triangles."
 },
 {
  "path": "claims[3].evidence[0]",
  "value": "The faint intermediate-scale component does not conflict with or alter compact ring reconstructions from 2017, 2018, or 2021.",
  "failed_quote": "Additionally, the Gaussian component identified in this work is not detectable on any baseline in the EHT longer than the PV-NOEMA baseline, and thus was not detectable/had no measurable impact on observations conducted in 2017 and 2018."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Stacking the rescaled 86 GHz GMVA jet structure onto the 230 GHz ring: improves the fit to the bump and offset (best at 0.06 Jy) but performs worse than the simple symmetric Gaussian model.",
  "failed_quote": "The fit to the offset and the bump is improved by including the jet component. However, our model of the 86 GHz jet is not able to provide a good fit, performing worse than the simpler fiducial model presented in Section 4.2."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Unmasked DoG-HIT gradient-descent imaging of closure phases: fits the bump and offset but produces a nonphysical 'waffle-like pattern' corresponding to the PV-NOEMA and SMT-KP baseline frequencies.",
  "failed_quote": "However, comparing the unmasked image with the original image, which was masked in spatial scale and localization (Figure 8, left column), on a logarithmic scale, we observe that the improved precision has been achieved by fitting a ‘waffle-like pattern’ associated with the PV-NOEMA and SMT-KP baselines, which is nonphysical."
 }
]
```
