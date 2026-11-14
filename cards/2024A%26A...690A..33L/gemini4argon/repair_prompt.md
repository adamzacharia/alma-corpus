# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690A..33L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. CMF-in-ALMA-IMF ©ESO 2024
July 29, 2024

## **ALMA-IMF**

### **XV The core mass function in the high-mass star-formation regime**


F. Louvet [1][,][ 2], P. Sanhueza [3][,][ 4], A. Stutz [5], A. Men’shchikov [6], F. Motte [1], R. Galván-Madrid [7], S. Bontemps [8], Y. Pouteau [1],
A. Ginsburg [9], T. Csengeri [8], J. Di Francesco [10], P. Dell’Ova [11], M. González [6], P. Didelon [6], J. Braine [8], N. Cunningham [1],
B. Thomasson [1], P. Lesaffre [11], P. Hennebelle [6], M. Bonfand [25], A. Gusdorf [11][,][ 12], R. H. Álverez-Gutiérrez [5], T. Nony [7], G.
Busquet [13][,][ 14][,][ 15], F. Olguin [16], L. Bronfman [2], J. Salinas [5], M. Fernandez-Lopez [17], E. Moraux [1], H.L. Liu [18], X. Lu [19], V.
Huei-Ru [16], A. Towner [26], M. Valeille-Manet [8], N. Brouillet [8], F. Herpin [8], B. Lefloch [8], T. Baug [21], L. Maud [22], A.
Lopez-Sepulcre [1][,][ 23], and B. Svodoba [24]


_(A_ ffi _liations can be found after the references)_


Received January 25, 2023; accepted July 25, 2024


**ABSTRACT**


The stellar initial mass function (IMF) is critical to our understanding of star formation and the effects of young stars on their environment. On
large scales, it enables us to use tracers such as UV or Hα emission to estimate the star formation rate of a system and interpret unresolved star
clusters across the universe. So far, there is little firm evidence of large-scale variations of the IMF, which is thus generally considered "universal".
Stars form from cores and it is now possible to estimate core masses and compare the core mass function (CMF) with the IMF, which it presumably
produces. The goal of the ALMA-IMF large program is to measure the core mass function at high linear resolution (2700 au) in 15 typical Milky
Way protoclusters spanning a mass range of 2.5×10 [3] to 32.7×10 [3] _M_ ⊙ . In this work, we used two different core extraction algorithms to extract
≈680 gravitationally bound cores from these 15 protoclusters. We adopt per core temperature using the temperature estimate from the PPMAP
Bayesian method. A power-law fit to the CMF of the sub-sample of cores above the 1.64 _M_ ⊙ completeness limit — 330 cores — through the
maximum likelihood estimate technique yields a slope of 1.97 ± 0.06, significantly flatter than the 2.35 Salpeter slope. Assuming a self-similar
mapping between the CMF and the IMF, this result implies that these 15 high-mass protocluster will generate atypical IMFs. This sample is the
largest to date produced and analysed self-consistently, derived at matched physical resolution, with per-core temperature estimates and cores as
massive as 150 _M_ ⊙ . We provide the raw source extraction catalogues and the source derived size, temperature, mass, and spectral indices in the 15
protoclusters.


**Key words.** Stars: formation – Infrared: ISM – Submillimeter: ISM – Methods: data analysis – Techniques: image processing



**1.** **Introduction**


In 1955, Edwin Salpeter reported that the high-mass tail of the
initial mass function of stars, the IMF, could be represented by a
power law in the form d [d] _M_ _[N]_ [∝] _[M]_ [−][α] [with] [α] [=] [2][.][35.] [Since] [then,]

numerous studies reported its universality (see the review by
Bastian et al. 2010), and studied its origin (e.g. Hennebelle &
Chabrier 2008). To investigate the origin of the IMF, astronomers
studied the fragmentation of molecular clouds, in the form of
small substructures (≲0.03 pc) — the cores — and the link between the core mass function (CMF) and the IMF (e.g. Motte
et al. 1998; Fiorellino et al. 2021). Because of observational limitations, until 2018 these studies focused mostly on nearby clouds
(∼140-400 pc), which mainly form low- and intermediate-mass
stars; they all reported CMF slopes at the high-mass end compatible with the slope of the IMF, suggesting that the IMF directly
inherits its shape from the CMF (e.g. Alves et al. 2007; Könyves
et al. 2010).


In 2018, taking advantage of the angular resolution and
sensitivity of the Atacama Large Millimetre/submillimetre Array (ALMA), Motte et al. (2018) studied the high-mass protocluster W43-MM1, at a distance of ≃5.5 kpc. They reported a
CMF with a high-mass tail flatter than the canonical IMF, with
α=1.96±0.13. Since then, other teams reported similar results in
other high-mass protoclusters but often using single pointing ob


servations, thus narrow fields not imaging pc-scale clouds (e.g.
Liu et al. 2018; Cheng et al. 2018; Kong 2019; O’Neill et al.
2021). These results cast doubt on the universality of the IMF or
on the direct link between the CMF and the IMF, or even on both.
However, the comparison of core samples between these studies — which are captured at different evolutionary stages — becomes complex or impossible when the observations are carried
out at disparate physical resolutions and/or sensitivities. Thus, it
became imperative to obtain a sample of high-mass protoclusters
representative of the Milky Way observed homogeneously.

To directly address this, we present in this article the results
of the ALMA-IMF Large Program (PIs: F. Motte, A. Ginsburg,
F. Louvet, P. Sanhueza). ALMA-IMF observed 15 high-mass
protoclusters at comparable sensitivity and physical resolution.
The main driver of the protocluster selection is a mass criteria,
first choosing protoclusters with inner parts of at least 500 _M_ ⊙,
as described in detail in the Sect. 2.1 of Motte et al. (2022). A
second criteria is the distance of the protoclusters. Not too close
by (> 2 kpc) to permit imaging a large area with mosaic observations and not too far (< 6 kpc) to prevent for excessive integration time. Our final sample consists of 15 protoclusters that were
observed with continuum sensitivity below 60 mK at 1.3 mm,

∼
and at similar physical resolution ( 2 kau).

In this article, we determine and analyse the combined CMF
of all 15 protosclusters from ALMA-IMF. We show the 1.3 and


Article number, page i of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



3 mm continuum images in Sect. 2, first presented in Ginsburg
et al. (2022). We describe the source extraction in Sect. 3. We
describe the source selection and core mass derivation in Sect. 4,
paying special attention to freefree emission and temperature of
the cores. We present the global CMF for all 15 fields. We discuss our results regarding the current knowledge about CMF in
Sect. 6, and we summarize our conclusions in Sect. 7.


**2.** **Observations**


The data were taken from the ALMA-IMF large program
(Project ID: 2017.1.01355.L), entitled _ALMA_ _transforms_ _our_
_view of the origin of stellar masses_ . Motte et al. (2022), hereafter
referred to as Paper I, described the project, its choice of targets, datasets, objectives and first results. Ginsburg et al. (2022),
hereafter referred to as Paper II, described the reduction pipeline
for the continuum emission maps at 1.3 mm and 3 mm in the
ALMA-IMF sample. Paper II presented two versions of the continuum maps: the bsens and the cleanest. The bsens maps were
constructed using the full range of the continuum spectral windows — which may include significant molecular emission, especially toward hot cores. The cleanest maps were constructed
flagging all channels contaminated by molecular emission (see
Fig. 3 in Paper II). Since we wish to assemble the most reliable
sample of cores, we use the cleanest continuum maps, publicly
available on the ALMA-IMF website [1] . Table 1 lists the fifteen
regions investigated by ALMA-IMF together with observational
characteristics, taken from Papers I and II, relevant to the present
paper. We refer to Paper I for an in depth description of the 15
regions.


**3.** **Source extraction**


_3.1._ _Extraction tools_


To extract sources in the continuum emission maps, we used
two extraction tools: _getsf_ (v210414, Men’shchikov 2021b) and
_GExt2D_ (v210603, Bontemps et al., in prep.). This approach
permits us to assess the biases inherent to our source extraction
algorithms.
The multi-scale, multi-wavelength source and filament extraction method _getsf_ supersedes the previous algorithms _get-_
_sources_, _getfilaments_, and _getimages_ (Men’shchikov et al. 2012;
Men’shchikov 2013, 2017, respectively). The _getsf_ method separates the structural components of sources, filaments, and background in the observations into independent images of the different components. Source and filament extraction are done with
their respective images, where the contributions of the other
components are largely removed. For more details on _getsf_,
illustrations of its applications, quantitative extraction performance, and comparisons with _getsources_, readers are referred
to Men’shchikov (2021a,b).
_GExt2D_ is based on the same idea as the _cutex_ tool (Molinari et al. 2011). It uses as a first step the second derivative
of the maps to identify the locations of maximum curvature as
indicative of compact sources. It starts from the strongest curvatures down to fainter and shallower fluctuations close to the
ones expected from measured local noise. The second step involves source boundaries identification and removal of background emission as the interpolated values in the map inside the
boundaries. The third step corresponds to automated Gaussian
fitting at each locations of compact sources after subtracting the
derived background.


1 `[https://www.almaimf.com/](https://www.almaimf.com/)`


Article number, page ii of xlix



_3.2._ _Source extraction at native angular resolutions_


With both _getsf_ and _GExt2D_, the source extraction strategy has
the same two steps. Firstly, we detected source candidates in the
continuum images at 1.3 mm (Band 6) without primary beam
correction. These images have a homogeneous noise level across
the entire field. This choice permits the detection of sources with
a constant signal-to-noise ratio threshold. Secondly, we measured the sources’ fluxes and sizes in the continuum maps at
1.3 mm and 3 mm (Band 3) after primary beam correction. This
way, the fluxes we obtained account for any attenuation resulting from being farther from the phase centre of the fields. This
strategy replicates that applied in Pouteau et al. (2022), hereafter
referred to as Paper III, dedicated to the W43-MM2 and W43MM3 protoclusters. Considering all 15 protoclusters together,
we extracted 820 sources with _getsf_, and 930 with _GExt2D_ .
_GExt2D_ detects the sources in the observed image, while _getsf_
decomposes the image first and requires detecting a source in
successive scales to validate its detection. Hence _getsf_ is more
conservative and extracts fewer sources than _GExt2D_ .
The distances of the protoclusters range from 2.5 to 5.5 kpc
(see Table 1 in Paper I). The ALMA-IMF large program aimed
to image the 15 protoclusters with the same spacial resolution
of 2100 au, requesting the corresponding angular resolution for
each field. Despite this effort, the available antenna configurations at the observatory led to variations in the spacial resolutions
by up to a factor of two (see Table 1 and Paper I). These variations in physical scale impact the size and mass of the sources
one may extract. Indeed, Louvet et al. (2021) performed convolution tests on projected density cubes obtained from hydrodynamical simulations, plus column density maps created from
_Herschel_ observations, and showed that the sizes and integrated
fluxes of extracted sources closely follow the size of the linear
scale. The left panel of Fig. 1 shows a linear dependency between the mean source size and the linear resolution. To obtain
a homogeneous sample of sources the data must be smoothed to
a matched spatial resolution.


_3.3._ _Source extraction at matched physical resolution_


To extract a spatially homogeneous core sample, we smoothed
the 1.3 and 3 mm maps to the lowest native resolution of
≃2700 au. We convolved each map with a Gaussian kernel whose
width, θ conv, is calculated as:



θ conv =



2700 au
�� _D_



2
− θ native [2] (1)
�



where _D_ is the distance to the target expressed in parsecs, and
θ native is the native angular resolution of the map. Table 2 lists
the angular resolution of each field after smoothing. We present
the smoothed continuum emission maps at 1.3 mm in Fig. 2.
We adopted the same strategy as explained in Sect. 3.2 to
extract sources in the smoothed maps. In total, we retrieve about
680 sources with _getsf_, and 1020 with _GExt2D_ [2] . Table 2 lists
the number of sources extracted per field with both algorithms,
Fig. 2 shows the sources extracted with _getsf_ and Fig. C.1 shows
the sources extracted with both algorithms. The right panel of
Fig. 1 shows the sizes of the sources we extracted with _getsf_


2
One can download the extraction catalogues from both _getsf_ and
_GExt2D_, at the native and smoothed angular resolutions on the website
of the ALMA-IMF Large Program ( `[https://www.almaimf.com/](https://www.almaimf.com/)` ),
[and on CDS in a machine readable format.](http://cdsportal.u-strasbg.fr/)

F. Louvet et al.: ALMA-IMF


Table 1: General properties of the ALMA-IMF fields.


Protocluster Phase center Evolutionary _D_ ν 1.3 mm θ Scale max σ 1.3 mm ν 3 mm σ 3 mm
cloud name RA[J2000] DEC[J2000] stage [pc] [GHz] [ [′′] ] [au] [ [′′] ] [mK] [GHz] [mK]
(1) (1) (1) (1) (2) (3) (4) (5) (6) (2) (6)


G327.29 15:53:08.130 −54:37:08.60 Young 2500 229.507 0.66 1650 8.3 25 101.776 5
G328.25 15:57:59.680 −53:57:57.43 Young 2500 227.575 0.55 1365 7.1 35 101.500 3
G337.92 16:41:10.620 −47:08:02.90 Young 2700 227.503 0.55 1475 6.6 15 101.602 23
G338.93 16:40:34.420 −45:41:40.60 Young 3900 229.226 0.54 2100 5.8 15 100.882 10
W43-MM1 18:47:47.000 −01:54:26.00 Young 5500 229.680 0.45 2470 12.0 26 99.759 17
W43-MM2 18:47:36.610 −02:00:51.10 Young 5500 227.597 0.47 2580 8.1 15 101.017 23
W43-MM3 18:47:41.460 −02:00:27.60 Intermediate 5500 228.931 0.49 2685 11.5 9 100.911 17

W51-E 19:23:44.180 14:30:29.50 Intermediate 5400 228.918 0.31 1650 4.5 60 101.426 26

G351.77 17:26:42.620 −36:09:22.47 Intermediate 2000 227.991 0.78 1560 8.9 21 100.228 16

G353.41 17:30:26.280 −34:41:51.67 Intermediate 2000 229.431 0.80 1600 9.1 14 100.547 9

G008.67 18:06:21.072 −21:37:14.84 Intermediate 3400 228.732 0.67 2270 9.1 22 100.526 14

G010.62 18:10:28.840 −19:55:48.30 Evolved 4950 229.268 0.47 2310 6.4 14 100.704 23

G012.80 18:14:13.370 −17:55:47.17 Evolved 2400 229.080 0.90 2155 9.5 20 100.680 21

G333.60 16:22:09.360 −50:06:00.87 Evolved 4200 229.062 0.56 2335 11.8 22 100.756 24

W51-IRS2 19:23:39.810 14:31:03.50 Evolved 5400 228.530 0.48 2575 7.0 13 101.263 24


**Notes.** (1) Phase center, evolutionary stage and distance to the region taken from Tables 1 and 4 of Paper I. (2) Central frequencies in Band 6
(≃1.3 mm) and in Band 3 (≃3.0 mm) taken from Table D.1 of Paper II. (3) Angular resolution in Band 6 (geometric average over the major and
minor axis of the beam). (4) Spatial resolution on source in Band 6. (5) Largest angular scale recovered in Band 6. (6) Standard deviations of the
noise level in Band 6 and in Band 3.


Fig. 1: Scatter plots of the source size (black dots), extracted with _getsf_, before (left) and after (right) smoothing the maps to a
homogeneous spatial resolution of 2700 au. The blue triangles display the beam sizes. The orange diamonds display the mean sizes
of sources. On the left panel, the _y-axis_ is the linear scale (beam × distance) of the maps in Band 6, and the orange line shows
the fit to the mean source sizes distribution for each field. On the right panel, the orange line shows the mean core size of all 15
protoclusters and the red crosses illustrate the cores exceeding 25 _M_ ⊙ .


for each field. The mean size is similar for each field with _L_ = **4.** **Results**
3840 ± 270 au. [3]

_4.1._ _Getsf versus GExt2D extraction methods_


In total, we retrieve 677 sources with _getsf_, and 1020 with
_GExt2D_ . We see a good agreement between these extractions as
∼80 % of the sources found by _getsf_ are also found by _GExt2D_
(Table 2). To compare the source flux measurements, we con

3 A similar figure for _GExt2D_ extractions is shown in Appendix B.1.


Article number, page iii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Table 2: Resolutions, noise levels, and sources extracted after smoothing to a linear scale of 2700 au.


Protocluster θ [(1)] σ [(2)] σ [(3)] _getsf_ _GExt2D_ Common [(4)]

cloud name [ [′′] ] [mJy.beam [−][1] ] [ _M_ ⊙ ]


G327.29 1.08 0.30 0.03 32 49 28 Table D.1

G328.25 1.08 0.19 0.02 11 26 9 Table D.2

G337.92 1.00 0.09 0.01 22 42 19 Table D.3

G338.93 0.69 0.12 0.03 42 50 31 Table D.4

W43-MM1 0.49 0.09 0.01 71 94 62 Table D.6

W43-MM2 0.49 0.11 0.06 40 34 27 Table D.9

W43-MM3 0.49 0.08 0.04 38 21 20 Table D.9

W51-E 0.50 0.06 0.03 31 75 22 Table D.10

G351.77 1.35 0.28 0.02 19 40 18 Table D.11

G353.41 1.35 0.19 0.02 46 68 39 Table D.12

G008.67 0.79 0.25 0.05 20 30 16 Table D.14

G010.62 0.55 0.12 0.03 50 59 37 Table D.15

G012.80 1.13 0.52 0.05 57 125 57 Table D.17

G333.60 0.64 0.24 0.07 95 175 64 Table D.19

W51-IRS2 0.50 0.12 0.03 109 136 94 Table D.22


Total [(5)] 677 1020 539


**Notes.** (1) Angular resolution after smoothing Band 3 and 6 images to a matched spatial resolution of 2700 au. (2) Standard deviation of the noise
level in Band 6. (3) Equivalent mass to the standard deviation in Band 6, using Eq. 4, assuming _S_ 1 [peak] .3 mm [/] �Ω [1][.][3 mm] × _B_ (20 K, ν)� → 1. (4) Number
of sources in common between the _getsf_ and _gext2d_ extractions. (5) The total number of sources differs from the direct sum per field because
two pairs of fields host sources in common. In the _getsf_ extractions, sources number 3, 20, 30, and 31 in W51-E correspond to sources 3, 22, 38,
and 108 in W51-IRS2, respectively; sources number 10 and 46 in W43-MM2 correspond to sources 2 and 37 in W43-MM3, respectively. In the
_GExt2D_ extractions, sources number 29, 32, and 46 in W51-E correspond to sources 21, 11, and 28 in W51-IRS2, respectively; source number 14
in W43-MM2 corresponds to source number 4 in W43-MM3.



structed the source flux functions (SFFs) and complementary
cumulative SFFs for both algorithms (Fig. 3). The first function
shows that the source fluxes range between 10 mJy and 10 Jy for
both algorithms, with a similar median value at ≃12 mJy. It also
shows that the additional sources found by _GExt2D_ are low and
intermediate flux sources from ∼30 mJy to 200 mJy. The complementary SFF permits to estimate the slope of the high-flux
end of the SFF. We fit the cumulative SFF with a power law
from the median value of the samples, that is 12 mJy, up to the
flux at which the number of cores is below ten [4] . The fitted highflux slopes are similar for both catalogues, with ζ [′] ≃ 0.85. These
exponents, adjusted onto the complementary cumulative SFFs,
correspond to power-laws with exponents ζ = ζ [′] + 1 ≃ 1.85.
This analysis proves that the overall statistics of source flux is
independent of the two extraction algorithms we employed. In
the following, we choose to focus on the extractions performed
by _getsf_ since it is more conservative than _GExt2D_, which is
confirmed by the large fraction of _getsf_ sources confirmed with
_GExt2D_ . Comparing the sources extracted at the native angular resolutions (see Sect. 3.2) to the sources extracted in the
smoothed maps (see Sect. 3.3), there is better agreement between
the _getsf_ catalogues than between _GExt2D_ catalogues. Indeed,
≃95% of the sources extracted in the smoothed maps were also
extracted at the native angular resolutions with the _getsf_ algorithm. This fraction drops to ≃75% in the case of the _GExt2D_
extractions.


4 We illustrate the cumulative complementary SFFs with constant logarithm flux interval. This method introduces a constant weight for each
bin, whatever the number of sources constituting the bin. Therefore it
artificially creates a bias for relatively unpopulated bins. For this reason,
we ignored the last 10 sources from the fit.


Article number, page iv of xlix



_4.2._ _From source flux to core mass_


4.2.1. Removing contaminated sources


The integrated fluxes comprise thermal dust emission and potentially free-free emission for the more evolved sources. In
the following, we filter the sources that are arguably contaminated by free-free emission. To do so, we used the integrated
flux measurements at 1.3 and 3 mm, when available, to compute
their spectral index. To correct from the source size differences
between 1.3 and 3 mm extractions, we adjusted the integrated

fluxes at 3 mm linearly: _S_ 3 mm [int][∗] [=] _[S]_ [ int] 3 mm [×] � ΘΘ [1] _A_ [.][3 mm][3 mm] _A_ ××ΘΘ [3 mm][1] _BB_ [.][3 mm] �, where

Θ _A_ and Θ _B_ are the major and minor axes of the sources, respectively, at 1.3 or 3 mm. This operation corrects the 3 mm fluxes
by 17 % in average. This flux rescaling replicates the method we
used in Paper III. This rescaling works both for an optically thick
emission and for an optically thin emission of an isothermal protostellar envelope with a density profile ρ( _r_ ) ∝ _r_ [−][2], where _r_ is
the radius of the envelope. We then compute the spectral index

as:


log � _S_ 1 [int] .3 mm [/] _[S]_ [ int] 3 mm [∗] �
γ = (2)

log (ν 1.3 mm /ν 3 mm )


where ν 1.3 mm and ν 3 mm are the central frequencies of the ALMA
Band 6 and Band 3 respectively (see Table 1). We remove 68
sources with γ < 2, which are presumably contaminated by freefree emission. These sources are represented by the pink ellipses
in Fig. 4.
To investigate the ≃500 sources that lack measurements at
3 mm, we built the spectral index map for each field, using Eq. 2
on a pixel-by-pixel basis by replacing _S_ 1 [int] .3 mm [and] _[ S]_ [ int] 3 mm [with the]
pixel intensities. We point out that the angular resolutions and
pixel sizes of the images at 1.3 mm equal that of the images at

F. Louvet et al.: ALMA-IMF


Fig. 2: The 15 ALMA-IMF protoclusters as traced by their continuum emission at 1.3 mm at a matched spatial resolution of 2700 au.
The ellipses locate all the cores found by _getsf_ . The name of the field is indicated in the top left corner of each panel and the beam
size is shown in the bottom left corner. For each protocluster, the center coordinates are those specified in Table 1.



3 mm. We show the spectral index maps in Fig. 4. The red areas (γ - 2) represent pixels with thermal dust emission, those
in green (0 < γ < 2) pixels contaminated by free-free emission,
and those in blue (γ < 0) pixels dominated by free-free emission. We manually selected all the sources lying over free-free
emission areas (γ < 2, see yellow ellipses in Fig. 4). For the
sources undetected at 3 mm we estimate their flux, _S_ 3 mm [upper] [, using]
the integrated flux in the aperture corresponding to the footprint
of the source detected at 1.3 mm. We emphasise that although
_getsf_ did not detect these 1.3 mm sources as compact sources at
3 mm they do have a background emission above 3σ at 3 mm, by
definition of the spectral index maps. We use this upper limit to



compute an upper limit on their spectral index as:


log � _S_ 1 [int] .3 mm [/] _[S]_ [ upper] 3 mm �
γ = (3)

log (ν 1.3 mm /ν 3 mm )


and we rejected the 16 sources with spectral index below 1, those
for which free-free emissions could substantially contribute to
the emission.

These filtering rejected 84 of the 677 sources extracted by
_getsf_ . The degree of rejection depends on the evolutionary stages
of the regions: ≃ 0.5% in the young regions, ≃ 10% in the intermediate regions, and ≃ 25% in the evolved regions. Table 3
lists, for each field, the number of sources rejected when applying these two levels of filtering.


Article number, page v of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. 2: Continuum emission maps (continued).



4.2.2. Core temperatures


Following the pilot study by Motte et al. (2018), we used the
Bayesian procedure _PPMAP_ (Marsh et al. 2015; Dell’Ova et al.
2024) to build the temperature maps of the ALMA-IMF protoclusters. The procedure uses several continuum emission maps
to compute a cube of column densities as a function of dust temperature. Our _PPMAP_ algorithm takes, along with the ALMA
data in Band 6 decontaminated from free-free emission (GalvánMadrid et al. subm.), the following maps as input:


**–** SOFIA/HAWC+ data at 214 µm with an angular resolution
of 19.0 [′′] (only for G012.80, G351.77, W51-E and W51IRS2, Vaillancourt 2016; Pillai & Simplifi Team 2023).
**–** Herschel/PACS and Herschel/SPIRE data at 70, 160, 250,
350, 500 µm with angular resolutions of 5.6, 10.7, 17.6, 23.9
and 35.2 [′′], respectively (Molinari et al. 2010; Motte et al.
2010).


Article number, page vi of xlix



**–** APEX/SABOCA data at 350 µm with an angular resolution
of 7.8 [′′] (Lin et al. 2019).
**–** APEX/LABOCA data at 870 µm with an angular resolution
of 19.2 [′′] (Schuller et al. 2009).


We refer to Dell’Ova et al. (2024) for an in-depth description
of the method. Finally, we obtain a unique temperature for each ′′
core at an angular resolution of 2.5 . The derived temperatures
vary from 19.4 to 62.8 K (see Tables D.14 to D.22). The error
associated with _PPMAP_ derivation is ≈5 K; to account for potential systematic contributions, we adopt a 25% error on the
_PPMAP_ temperature estimates [5] .
We adopted the PPMAP temperatures for all cores except
for the hot core candidates for which we adopted the method
proposed in Bonfand et al. (2024): we cross-correlated the position of continuum sources (see Sect. 3.3) with methyl formate


5 We adopt an uncertainty of 5 K for sources below 20 K.

F. Louvet et al.: ALMA-IMF


Fig. 2: Continuum emission maps (continued).



(CH 3 OCHO) emission maps that were observed by ALMA-IMF.
Methyl formate forms at the surface of dust grains in lukewarm
(30-40 K) regions, and is then released in the gas phase when the
temperature reaches ∼100 K (e.g. Garrod et al. 2009). Methyl
formate can be used as a proxy to trace regions where heating
is present and dust surface products have started to sublimate.
Following the method discussed in Bonfand et al. (2024), we set
100±50 K to the 49 sources whose position corresponds to the
peaks of extended methyl formate emission; these sources are
classified as hot core candidates.


Additionally, we set 300±100 K to sources n [◦] 1, n [◦] 2, and
n [◦] 1 in W51-IRS2, W51-E and G327.29 respectively, following
their detailed modelling by Ginsburg et al. (2017), Goddi et al.
(2020), and the adopted temperature in Bonfand et al. (2024),
respectively. These three sources are associated with strong and



extended emission structures in the methyl formate emission
maps. [6]


4.2.3. Core mass and boundedness


We converted the measured integrated flux at 1.3 mm, _S_ 1 [int] .3 mm [,]
into a mass using the formula presented in Paper III that includes
a first order correction for the optical thickness:



6 Bonfand et al. (2024) report 6 sources with temperatures estimated at
300±100 K. The 3 additional sources with respect to ours are either classified as freefree contaminated (source W51-E-MF1) or not matching
our continuum extractions (sources W51-E-MF2 and W51-IRS2-MF3).


Article number, page vii of xlix



_S_ [peak]
1 − 1.3 mm
 Ω [1] beam [.][3 mm] _B_ ( _T_, ν)



_D_ [2]
_M_ core = −Ω [1] beam [.][3 mm]

κ 1.3 mm



_S_ [int]
1.3 mm ln
_S_ [peak]
1.3 mm



(4)


_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. 2: Continuum emission maps (continued).



where _D_ is the distance to the target, κ 1.3 mm =
0.1 (ν/1000 GHz) [β] cm [2] g [−][1] is the dust opacity per unit mass
(dust + gas), with an opacity index β = 1.5 typical of cold and
dense environment (Ossenkopf & Henning 1994), and _B_ ( _T_, ν)
is the Planck function computed at the representative frequency
of the observations in Band 6 with the dust temperature _T_ (see
Table 1 for central frequencies and distances, and Tables D.14
to D.22 for source temperature).
Errors on the masses mostly arise from the uncertainties on
the opacity index β and on the dust temperature, _T_ . Masses
would be a factor of two smaller using β = 2 instead of β = 1.5.
As for the temperature, a 25 % difference leads to a mass shift
by ≲40 %.
To address the boundedness of cores, we computed the ratio
_M_ BE / _M_ core where _M_ core is the core mass and _M_ BE is the mass
of the critical Bonnor-Ebert sphere (Bonnor 1956) whose size
matches that of the core: _M_ BE = 2.4 × _R_ × σ [2] th [/] _[G]_ [.] [Here,] _[R]_ [is]


Article number, page viii of xlix



1
the equivalent core radius, estimated as _R_ = ( _a_ × _b_ [2] ) 3 × _D_ [7],
where _a_ and _b_ are the major and minor axis of the source ellipse, respectively. Moreover, σ th is the thermal broadening of
lines, as σ th = [�] γ _k_ B _T_ /(µ × _m_ p ) where γ = 1 is the adiabatic
index (isothermal), _k_ _B_ is the Boltzmann constant, µ = 2.4 is the
mean molecular weight per free particle, and _m_ p is the mass of
a proton. We consider that the sources are gravitationally bound
if _M_ BE / _M_ source < 2 (see e.g. Louvet et al. 2021). As listed in
Table 3, this filter excludes no sources. We note that this is a
first-order check of the boundedness of cores. A more accurate
determination would require computing the equilibrium of each
source taking into account its turbulence, external pressure, and
magnetic field support in addition to the thermal support. Unfortunately, we lack all these pieces of information at the moment.


7 We stress that choosing 3D oblate core shape ( _V_ ∝ _a_ 2 × _b_ ) has no
effect on the boundedness of the cores.

F. Louvet et al.: ALMA-IMF


Fig. 3: The left panel displays the source flux functions (SFFs) of the sources extracted by _getsf_, in grey, and by _GExt2D_ in blue. The
vertical blue and grey lines indicate the median values for each source catalogues, which differ by ≃5 %. The right panel displays
the complementary cumulative SFFs from the _getsf_ source extraction (in grey) and from the _GExt2D_ source extraction (in blue).
The grey and blue lines display the best fits from linear regressions on the complementary cumulative SFFs from the median value
at 12 mJy up to the flux at which the number of cores is less than 10. The corresponding ζ power-law indexes are indicated in the
top right corner.


Table 3: Evolution of the core sample through the selection process


Protocluster All [(1)] γ < 2 [(2)] _S_ 3 mm [theo] [< σ] [(3)] 3 mm Unbound [(4)] Bound [(5)] _M_ _low_ [(6)] _M_ - _M_ _low_ [(7)] _M_ - 1.64 _M_ ⊙ [(8)]

[ _M_ ⊙ ]


G327.29 32 0 0 0 32 1.53 26 25

G328.25 11 0 0 0 11 1.53 7 7

G337.92 22 0 0 0 22 1.13 14 11

G338.93 42 0 0 0 42 1.41 31 29

W43-MM1 71 1 0 0 70 1.54 53 49

W43-MM2 40 0 0 0 40 1.60 24 24

W43-MM3 36 1 0 0 37 1.33 16 12

W51-E 31 7 1 0 23 3.86 20 20

G351.77 19 1 0 0 18 0.80 11 6

G353.41 46 1 0 0 45 1.18 23 17

G008.67 20 1 0 0 19 1.53 15 14

G010.62 50 8 0 0 42 0.96 29 22

G012.80 57 9 4 0 44 1.30 30 25

G333.60 95 34 7 0 54 1.28 30 23

W51-IRS2 109 6 4 0 99 1.64 67 66


Total [(9)] 677 68 16 0 593 393 350 [(10)]


**Notes.** (1) Number of sources extracted by _getsf_ . (2) Number of sources contaminated by freefree. (3) Number of sources whose emission
could be contaminated by freefree. (4) Number of sources not gravitationnally bound. (5) Number of sources gravatiationnally bound. (6) Mass
completeness limit in the field. (7) Number of gravitationnally bound cores exceeding the field’s completeness level (see Sect. 5.1). (8) Number
of gravitationnally bound cores exceeding the global completeness level (see Sect. 5.1). (9) The total number of sources differs from the direct
sum per field because two pairs of fields host sources in common (see Table 2). (10) The total number of sources reduces to 330 when discarding
W51-E.



In Figs. 2 we show the thermal-dust cores for each field. The
Tables D.1 to D.24 list all the sources detected by the _getsf_ extraction algorithm in each field. The first group of sources in
each table corresponds to thermal dust cores that are gravitationally bound, and the second group corresponds to sources whose
fluxes are arguably contaminated by free-free emission. For each



source, the last column indicates whether it was also detected by
_GExt2D_, which is true for 80 % of the extracted sources.


Article number, page ix of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. 4: The maps display the spectral index in the fifteen ALMA-IMF fields. We chose the colours such that red traces dust thermal
emission, blue traces free-free emission and green likely traces a mixture of dust and free-free emissions. The maps display the
spectral index value only where the 3 mm intensity exceeds 3 σ. The black ellipses display the sources extracted by _getsf_ .



**5.** **Core mass function**


_5.1._ _Completeness tests_


In order to draw a coherent sample gathering cores from the 15
ALMA-IMF protoclusters, we need to ascertain that the core extractions are complete at the selected lower mass limit. To do
so, we performed completeness tests in each protocluster: we injected synthetic cores on top of their background emission (i.e.
the emission subtracted from each source). The synthetic cores
are injected in the form of 2D circular Gaussian with a FWHM
corresponding to 3840 au — the mean core size (see Sect. 3.3).
We inject these synthetic sources randomly, provided the centre
of the cores are separated by more than 2.5 [′′] . We forbid the injection of sources within 5 [′′] of the border of the maps, where the


Article number, page x of xlix



noise increases due to the primary beam correction (see Fig. 2).
The flux of the synthetic sources ranges from equivalent masses
of 0.5 to 5 _M_ ⊙ in all fields for gas at 20 K, except in W51-E where
we adopted a mass range of 1 to 10 _M_ ⊙ . The fluxes are equally
split into ten bins of flux. From these fluxes, we compute the
mass of the synthetic cores when adopting the mean temperature
of the cores extracted in the corresponding region. We then extract the synthetic cores with the _getsf_ method (see Sect. 3.1).
To obtain a good statistics in each bin of mass, we repeated this
procedure four times per field. Cumulating the four draws we
obtain ≃3800 cores in total in each field (or ≃380 per bin) and
we probe ≃80 % of the background area. We plot the percentage of synthetic cores extracted as a function of their mass in
Fig. A.1. Following Paper III, we consider reaching the com

F. Louvet et al.: ALMA-IMF


Fig. 4: Spectral index maps (continued). The ellipses in pink highlight sources automatically flagged due to their spectral index;
those in yellow display the sources whose spectral index were further checked manually (see Eq. 2).



pleteness limit when 90 % of the synthetic cores are extracted.
The mass completeness varies from 0.80 to 1.64 _M_ ⊙ with a mean
value of 1.34 _M_ ⊙ and a standard deviation of 0.2 _M_ ⊙ . These numbers exclude W51-E, for which we find completeness as high as
3.9 _M_ ⊙ . We exclude W51-E from the analysis of the global CMF
(see Sect. 6.1) and we restrict the core samples to cores exceeding 1.64 _M_ ⊙ to fit the high-mass tail of the CMF.


_5.2._ _Fitting core mass functions_


5.2.1. Method


The representation of a distribution in the form of histograms,
as in Fig. 3, further fitted through linear regression may give
inaccurate results (Clauset et al. 2009). In addition, the representation in the form of a CMF in log-log scales prohibits esti


mating the fit uncertainty since the noise is not Gaussian. Moreover, the choice of the bin width induces a free parameter that
thwarts any uncertainty estimate. The representation in the form
of a cumulative CMF, however, prevents the estimation of the
uncertainty as the data are not independent. To circumvent these
issues, we choose to fit the high-mass end of the CMF using
maximum likelihood estimates (MLE). We follow the procedure
presented by Clauset et al. (2009), and use its implementation in
the python package `powerlaw` presented by Alstott et al. (2014).
If we assume that the CMF can be represented by a power-law
_p_ ( _x_ ) = _Cx_ [−][α], where _C_ is a constant, there must be some lower
mass value, _x_ min, from which the power-law fit is accurate, and
prevents the divergence of _p_ when _x_ → 0. After normalisation


Article number, page xi of xlix

(imposing that � _x_ + min ∞ _[p]_ [(] _[x]_ [)] _[ dx]_ [ =][ 1) it comes:]



_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. 4: Spectral index maps (continued).


where _O_ is the mathematical notation for: not negligible in front
of.



−α

(5)
�



_p_ ( _x_ ) = [α][ −] [1]

_x_ min



_x_
� _x_ min



When _x_ min is known, the MLE gives an estimate of the exponent of the power-law as:



The originality of the method by Clauset et al. (2009) is to
propose a method to determine the best parameters _x_ min and α
using the Kolmogorov-Smirnov (KS) distance. First, the method
computes α for _x_ min taking successively each mass value of the
core sample. Then it computes the maximal distance — the KS
distance, _KS_ D — between the observational CMF for all elements whose mass exceeds _x_ min and the synthetic CMF following a probability distribution function as defined by Eq. 5. The
best value for the parameters _x_ min and α is that which minimizes the _KS_ D . Figure 5 shows the evolution of α and _KS_ D
for all _x_ min values. In our case, we need to select the highest
value between the _x_ min that minimizes the _KS_ D and our completeness limit (see Sect. 5.1). The first minimum in the _KS_ _D_ is
met for _x_ min =1.40 _M_ ⊙, below our completeness level at 1.64 _M_ ⊙ .



_x_ min



α = 1 + _n_







_n_
�



� ln _x_ _[x]_ _[i]_

_i_ =1



−1

(6)





where _x_ _i_ is the mass of the core _i_ (provided _x_ _i_ ≥ _x_ min ), and the
uncertainty on α reads:



1
σ = [α][ −] [1] + _O_
~~√~~ _n_ � _n_



(7)
�



Article number, page xii of xlix

F. Louvet et al.: ALMA-IMF


Fig. 4: Spectral index maps (continued).



We, therefore, select _x_ min = 1.64 _M_ ⊙, which corresponds to a
core sample of 330 elements (excluding W51-E). From that subsample, we obtain a power-law index fit α = 2.11 ± 0.06 [8] . We
put forward that 330 cores above the completeness limit convey
a statistical conclusive sample. Clauset et al. (2009) report stable index values when the sample exceeds ≈50 elements above
the completeness limits. Consistently, Louvet et al. (2021) report stable index values when the sample exceeds ≈40 elements
above the completeness limits.


8 We note that _x_ min = 1.40 _M_ ⊙ corresponds to α = 2.07 ± 0.06, compatible with the α associated with _x_ min = 1.64 _M_ ⊙ .



5.2.2. Uncertainty of the fit


As pointed out in Sect. 4.2.3, errors in the mass estimates arise
primarily from the uncertainties on the opacity index and core
temperature. To study how these uncertainties affect the slope of
the CMF, we performed a Monte Carlo simulation on our 330
cores by allowing their opacity index, their temperature as well
as their source flux to vary simultaneously. About the latter, we
used the Gaussian error associated with the flux measurement.
Koen & Kondlo (2009) showed that including such errors on the
fluxes flattens the distribution. However, since our relative uncertainty diminishes for brighter sources, we expect this effect
to be marginal on the high-mass end of our CMF. In our Monte
Carlo simulation, the opacity index β can take random normal
values with a mean value of 1.5 (Ossenkopf & Henning 1994)


Article number, page xiii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Fig. 5: Convergence towards the best fit of a power-law through
MLE and KS _D_ method for the global _getsf_ bound core catalogue without the free-free sources. The left vertical dashed
line highlights the first minimal KS _D_ (in blue), occurring at
_x_ min = 1.40 _M_ ⊙ . The right vertical dashed line highlights the
completeness limits at _x_ min = 1.64 _M_ ⊙ . The orange curve shows
the exponent of the power law fit of the high-mass tail of the
CMF as a function of _x_ min .


and a standard deviation of 0.2 for each core. In parallel, we
allow the core temperature to take random normal values with
the mean and standard deviation as described in Sect. 4.2.2. We
show the resulting cumulative CMFs generated from 10 [3] trials in
Fig. 6. Each draw is fitted via MLE (see Sect. 5.2.1), fixing _x_ min
to 1.64 _M_ ⊙ . We obtain a mean exponent value for the slope of the
CMF of 1.97±0.06, where the uncertainty is the quadratic sum
of the statistical uncertainty from Eq. 7 (σ ≃ 0.06) and from the
uncertainties on the temperature, opacity index, and flux measurement uncertainties (σ ≃ 0.02). We show in Appendix E.1
the results of the 10 [3] trials for a power-law fit.


5.2.3. Comparison with the Salpeter-slope


The ALMA-IMF large program aims to test if the high-mass
slope of the CMF differs from the high-mass slope of the canonical IMF (α = 2.35 when fitted by a power-law, Salpeter 1955).
To see if our sample of 330 cores (with _M_ - _x_ min = 1.64 _M_ ⊙ )
permits such a claim, we selected 330 sources from a perfect
mass distribution with an exponent of 2.35 and fitted the slope
of its high-mass tail through the MLE. We repeated the operation 10 [5] times. Figure 7 shows the probability of retrieving an
exponent α when the parental distribution has a slope α=2.35.
With 330 cores, the probability of retrieving a slope compatible
with ALMA-IMF, α = 1.97 ± 0.06, is lower than 1% (σ ≈ 2.4).
Therefore, we report that the CMF in the protoclusters studied by
ALMA-IMF is flatter than, and cannot reasonably be reconciled
with the Salpeter-IMF slope to a 2.4σ level [9] .


9
σ refers to a confidence interval of a Gaussian distribution.


Article number, page xiv of xlix



Fig. 6: The grey curves show the complementary cumulative
CMFs (ccCMFs) of the 10 [3] core samples obtained by including flux measurement uncertainties, varying core temperatures,
and applying opacity index variations on a per-regions basis (see
Sect. 5.2.2), overlaid with the average fit by a power-law (in
blue) and the best fit with a power-law of index 2.35.


Fig. 7: The figure illustrates the power-law exponents α retrieved
when sorting 330 cores from a synthetic core sample whose
CMF has a power-law exponent of 1.97 (in blue) and 2.35 (in
orange).


**6.** **Discussion**


_6.1._ _A global top-heavy core mass function_


In Sects. 5.2.1 and 5.2.2, we presented the best fit to the highmass tail of the CMF by a power law. The best-fit yields α =
1.97 ± 0.06. This result, based on 330 cores, confirms the many
investigations led in recent years that reported top-heavy CMFs
in high-mass protoclusters (e.g. Motte et al. 2018; Cheng et al.
2018; Sanhueza et al. 2019; Kong 2019; Moser et al. 2020). We
show that this slope cannot be reconciled, at the 2.4 σ level, with
the canonical IMF slope (α = 2.35, see Sect. 5.2.3) even after
the inclusion of all known uncertainties.

Observing top-heavy CMFs in high-mass protoclusters contrasts with nearby low-mass star-forming regions where a highmass tail compatible with Salpeter is consistently found (see,

F. Louvet et al.: ALMA-IMF



e.g., Table 6 of Fiorellino et al. 2021 for all CMF exponents from
the Herschel Gould Belt Survey).


_6.2._ _From the CMF to the IMF_


To link the CMF to the IMF, one must assume that cores constitute the mass reservoir for the accretion of protostars. One also
assumes a fragmentation cascade and a mass transfer efficiency
ϵ from cores to protostars. Regarding the latter, the common
assumption is that one core will give birth to one star — and
therefore assumes no sub-fragmentation — and that ϵ remains
constant whatever the mass of the cores. If we adopt these assumptions, since our massive protoclusters display a top-heavy
CMF they shall engender a top-heavy IMF with a high-mass
slope equals to that of the CMF: α ≃ 1.97. Meanwhile, Bontemps et al. (2010), Louvet et al. (2014) and Csengeri et al.
(2017) showed that ϵ actually depends almost linearly on the local density. As a matter of facts, the massive cores — >25 _M_ ⊙ —
spread equally over the observed size range and are therefore, on
average, denser than low- and intermediate-mass cores (see red
crosses in Figure 1). This suggests that massive cores will convert gas into stars more efficiently than low- and intermediatemass cores, giving birth to a flatter IMF than the parental CMF.
In the past ten years some examples of top-heavy IMFs have
been reported in young massive clusters in and out of our Galaxy
(see for example Lu et al. 2013; Schneider et al. 2018). As a
consequence, we speculate that the ALMA-IMF protoclusters
might the precursors of star-clusters whose IMF is top-heavy.
From another perspective, we now observe more regularly starforming regions with at top-heavy CMF than star clusters with a
top-heavy IMF. To reconcile these two observables, we hypothesise that some of the star-forming regions hosting a top-heavy
CMF will evolve to produce a Salpeter-like IMF.


_6.3._ _Limitations and perspectives_


We recognize two limitations in our study:


 - Free-free emission: in Sect. 4.2, we rejected all sources that
are arguably contaminated by free-free emission from our
core sample. We ended up rejecting 84 sources (see Table 3). Galván-Madrid et al. subm. gives estimates of the
free-free contribution, based on the H 41α recombination lines
collected by ALMA-IMF. This characterization will allow us
to correct and re-introduce these sources in the core sample.
These sources, with free-free emission, arise from massive
young stellar objects and would steepen our CMF even further. Therefore, our conclusions will stay unchanged by the
inclusion of the free-free contaminated cores.

 - Sub-fragmentation: we probed the cores at a spatial resolution of 2700 au. Recent observations in the high-mass protostellar core G335 showed that a binary system, and perhaps even a triple system, could take place below 1000 au
(Olguin et al. 2021, 2022). Similar results were obtain by
Izquierdo et al. (2018) in W33A. However, other works
reported no fragmentation in G336.01-0.82 (Olguin et al.
2023) or HH80-81 (Girart et al. 2018). At present date, it
is thus uncertain how will be the multiplicity in the ALMAIMF fields. A straightforward path would consist in conducting observations at a yet higher angular resolution to reach a
spatial resolution of ≃200 au, the typical scale of Solar-type
proto-planetary disks (e.g. Louvet et al. 2018). The main difficulty consists in obtaining high sensitivities with an optically thin tracer at the scale of protoclusters.



**7.** **Conclusions**


We present the core catalogues of the 15 high-mass protoclusters observed by the ALMA-IMF large programme. At a homogeneous sensitivity and spatial resolution (2700 au), we collected about 680 sources. Rejecting sources arguably contaminated by free-free emission, we analysed a core sample of
≃600 elements. We performed completeness tests and found
the matched-physical resolution core catalogues to be complete
down to 1.64 _M_ ⊙, with the exception of the W51-E protocluster
whose cores were discarded from the CMF analysis. In total, we
analysed 330 cores with masses above the completeness limit of
1.64 _M_ ⊙ and with little to no free-free contamination.
We fit the high-mass slope of the core mass function (CMF)
with the maximum likelihood estimate technique and found a
best-fit power law probability distribution function (PDF) d [d] _M_ _[N]_ [∝]

_M_ [−][α] with α = 1.97 ± 0.06. Such an exponent is flatter than,
and cannot be reconciled with, the Salpeter-IMF slope of α ≃
2.35. We confirm that the CMF in a representative sample of
high-mass Galactic protoclusters is shallower than the Salpeter
slope. We suggest that these massive protoclusters will give birth
to top-heavy stellar clusters, or, in order to reconcile with the
Universal IMF, the CMF needs to evolve and become Salpeterlike at latter stages of the cluster formation.
Together with this article, we provide the core catalogues
for the 15 protoclusters at both the native (1300 to 2700 au) and
smoothed (2700 au) linear resolutions. These catalogues include,
among other, the sources position, size (in arcsec and in au), peak
and integrated fluxes at both 1.3 and 3 mm, their temperature estimates from PPMAP and their estimated mass.


_Acknowledgements._ This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2017.1.01355.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ. This paper also use the following ALMA data:
ADS/JAO. ALMA#2013.1.01365.S and ADS/JAO.ALMA#2015.1.01273.S. FL
acknowledges support by the Marie Curie Action of the European Union (project
_MagiKStar_, Grant agreement number 841276). FM acknowledges the support of
the French Agence Nationale de la Recherche (ANR) under reference ANR20-CE31-009, of the Programme National de Physique Stellaire and Physique
et Chimie du Milieu Interstellaire (PNPS and PCMI) of CNRS/INSU (with
INC/INP/IN2P3). AG acknowledges support from the NSF under grants AST
2008101 and CAREER 2142300. PS was supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of the Japan
Society for the Promotion of Science (JSPS). P.S. and H.-L.L. gratefully acknowledge the support from the NAOJ Visiting Fellow Program to visit the National Astronomical Observatory of Japan in 2019, February. SB acknowledges
support by the French Agence Nationale de la Recherche (ANR) through the
project _GENESIS_ (ANR-16-CE92-0035-01). T. Cs. has received financial support from the French State in the framework of the IdEx Université de Bordeaux
Investments for the future Program. RG-M and TN acknowledge support from
UNAM-PAPIIT project IN108822 and from CONACyT Ciencia de Frontera
project ID: 86372. AS gratefully acknowledges support by the Fondecyt Regular
(project code 1220610), and ANID BASAL project FB210003. LB gratefully acknowledges support by the ANID BASAL projects ACE210002 and FB210003.
NC acknowledges funding from the ERC under the European Union’s Horizon 2020 research and innovation programme (ECOGAL, grant agreement no.
855130). GB acknowledges funding from the State Agency for Research (AEI)
of the Spanish MCIU through the AYA2017-84390-C2-2-R grant. GB and ALS
acknowledges funding from the European Research Council (ERC) under the
European Union’s Horizon 2020 research and innovation programme, for the
Project "The Dawn of Organic Chemistry" (DOC), grant agreement No 741002.
TB acknowledges the support from S. N. Bose National Centre for Basic Sciences under the Department of Science and Technology, Govt. of India. MB is
a postdoctoral fellow in the University of Virginia’s VICO collaboration and is
funded by grants from the NASA Astrophysics Theory Program (grant number 80NSSC18K0558) and the NSF Astronomy & Astrophysics program (grant
number 2206516). The project leading to this publication has received support
from ORP, that is funded by the European Union’s Horizon 2020 research and
innovation programme under grant agreement No 101004719.


Article number, page xv of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



**References**


Alstott, J., Bullmore, E., & Plenz, D. 2014, PLoS ONE, 9, e85777
Alves, J., Lombardi, M., & Lada, C. J. 2007, A&A, 462, L17
Bastian, N., Covey, K. R., & Meyer, M. R. 2010, ARA&A, 48, 339
Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, arXiv e-prints,
arXiv:2402.15023
Bonnor, W. B. 1956, MNRAS, 116, 351
Bontemps, S., Motte, F., Csengeri, T., & Schneider, N. 2010, A&A, 524, A18
Cheng, Y., Tan, J. C., Liu, M., et al. 2018, ApJ, 853, 160
Clauset, A., Shalizi, C. R., & Newman, M. E. J. 2009, SIAM Review, 51, 661
Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, L10
Dell’Ova, P., Motte, F., Gusdorf, A., et al. 2024, arXiv e-prints,
arXiv:2407.07610
Fiorellino, E., Elia, D., André, P., et al. 2021, MNRAS, 500, 4257
Garrod, R. T., Vasyunin, A. I., Semenov, D. A., Wiebe, D. S., & Henning, T.
2009, ApJ, 700, L43
Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022, A&A, 662, A9
Ginsburg, A., Goddi, C., Kruijssen, J. M. D., et al. 2017, ApJ, 842, 92
Girart, J. M., Fernández-López, M., Li, Z. Y., et al. 2018, ApJ, 856, L27
Goddi, C., Ginsburg, A., Maud, L. T., Zhang, Q., & Zapata, L. A. 2020, ApJ,
905, 25
Hennebelle, P. & Chabrier, G. 2008, ApJ, 684, 395
Izquierdo, A. F., Galván-Madrid, R., Maud, L. T., et al. 2018, MNRAS, 478,
2505
Koen, C. & Kondlo, L. 2009, MNRAS, 397, 495
Kong, S. 2019, ApJ, 873, 31
Könyves, V., André, P., Men’shchikov, A., et al. 2010, A&A, 518, L106
Lin, Y., Csengeri, T., Wyrowski, F., et al. 2019, A&A, 631, A72
Liu, M., Tan, J. C., Cheng, Y., & Kong, S. 2018, ApJ, 862, 105
Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120
Louvet, F., Hennebelle, P., Men’shchikov, A., et al. 2021, A&A, 653, A157
Louvet, F., Motte, F., Hennebelle, P., et al. 2014, A&A, 570, A15
Lu, J. R., Do, T., Ghez, A. M., et al. 2013, ApJ, 764, 155
Marsh, K. A., Whitworth, A. P., & Lomax, O. 2015, MNRAS, 454, 4282
Men’shchikov, A. 2013, A&A, 560, A63
Men’shchikov, A. 2017, A&A, 607, A64
Men’shchikov, A. 2021a, A&A, 654, A78
Men’shchikov, A. 2021b, A&A, 649, A89
Men’shchikov, A., André, P., Didelon, P., et al. 2012, A&A, 542, A81
Molinari, S., Schisano, E., Faustini, F., et al. 2011, A&A, 530, A133
Molinari, S., Swinyard, B., Bally, J., et al. 2010, PASP, 122, 314
Moser, E., Liu, M., Tan, J. C., et al. 2020, ApJ, 897, 136
Motte, F., Andre, P., & Neri, R. 1998, A&A, 336, 150
Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8
Motte, F., Nony, T., Louvet, F., et al. 2018, Nature Astronomy, 2, 478
Motte, F., Zavagno, A., Bontemps, S., et al. 2010, A&A, 518, L77
Olguin, F. A., Sanhueza, P., Chen, H.-R. V., et al. 2023, ApJ, 959, L31
Olguin, F. A., Sanhueza, P., Ginsburg, A., et al. 2022, ApJ, 929, 68
Olguin, F. A., Sanhueza, P., Guzmán, A. E., et al. 2021, ApJ, 909, 199
O’Neill, T. J., Cosentino, G., Tan, J. C., Cheng, Y., & Liu, M. 2021, ApJ, 916, 45
Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943
Pillai, T. & Simplifi Team. 2023, in American Astronomical Society Meeting Abstracts, Vol. 55, American Astronomical Society Meeting Abstracts, 308.03
Pouteau, Y., Motte, F., Nony, T., et al. 2022, arXiv e-prints, arXiv:2203.03276
Salpeter, E. E. 1955, ApJ, 121, 161
Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102
Schneider, F. R. N., Sana, H., Evans, C. J., et al. 2018, Science, 359, 69
Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415
Vaillancourt, J. 2016, Characterizing the FIR polarization spectrum in Galactic
Clouds, SOFIA Proposal, Cycle 5, ID. 05_0038


1
Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France. email: `fabien.louvet@univ-grenoble-alpes.fr`
2 DAS, Universidad de Chile, 1515 camino el observatorio, Las Condes, Santiago, Chile
3 National Astronomical Observatory of Japan, National Institutes of
Natural Sciences, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan
4 Department of Astronomical Science, SOKENDAI (The Graduate
University for Advanced Studies), 2-21-1 Osawa, Mitaka, Tokyo
181-8588, Japan
5 Departamento de Astronomía, Universidad de Concepción, Casilla
160-C, 4030000 Concepción, Chile
6 Université Paris-Saclay, Université Paris Cité, CEA, CNRS, AIM,
91191 Gif-sur-Yvette, France
7 Instituto de Radioastronomía y Astrofísica, Universidad Nacional
Autónoma de México, Morelia, Michoacán 58089, México


Article number, page xvi of xlix



8 Laboratoire d’astrophysique de Bordeaux, Univ. Bordeaux, CNRS,
B18N, allée Geoffroy Saint-Hilaire, 33615 Pessac, France
9 Department of Astronomy, University of Florida, PO Box 112055,
USA
10 Herzberg Astronomy and Astrophysics Research Centre, National
Research Council of Canada, 5071 West Saanich Road, Victoria,
BC CANADA V9E 2E7
11 Laboratoire de Physique de l’École Normale Supérieure, ENS, Université PSL, CNRS, Sorbonne Université, Université de Paris, Paris,
France
12 Observatoire de Paris, PSL University, Sorbonne Université,
LERMA, 75014, Paris, France
13 Departament de Física Quàntica i Astrofísica (FQA), Universitat de
Barcelona (UB), c. Martí i Franquès, 1, 08028 Barcelona, Spain
14 Institut de Ciències del Cosmos (ICCUB), Universitat de Barcelona
(UB), c. Martí i Franquès, 1, 08028 Barcelona, Spain
15 Institut d’Estudis Espacials de Catalunya (IEEC), 08340, Barcelona,
Catalonia, Spain
16 Institute of Astronomy, National Tsing Hua University, Hsinchu
30013, Taiwan
17 Instituto Argentino de Radioastronomía (CCT-La Plata, CONICET;
CICPBA), C.C. No. 5, 1894, Villa Elisa, Buenos Aires, Argentina
18 Department of Astronomy, Yunnan University, Kunming, 650091,
PR China
19 Shanghai Astronomical Observatory, Chinese Academy of Sciences,
80 Nandan Road, Shanghai 200030, People’s Republic of China
20 Department of Astronomy, The University of Tokyo, 7-3-1 Hongo,
Bunkyo, Tokyo 113-0033, Japan
21 S. N. Bose National Centre for Basic Sciences, Block JD, Sector III,
Salt Lake, Kolkata 700106, India
22 ESO Headquarters, Karl-Schwarzchild-Str 2 D-85748 Garching
23 Institut de Radioastronomie Millimétrique (IRAM), 300 rue de la
Piscine, 38406 Saint-Martin-D’Hères, France
24 National Radio Astronomy Observatory, PO Box O, Socorro, NM
87801 USA
25 Departments of Astronomy and Chemistry, University of Virginia,
Charlottesville, VA 22904, USA
26 Steward Observatory, University of Arizona, 933 North Cherry Avenue, Tucson, AZ 85721, USA
27 Université Paris Cité, Université Paris-Saclay, CEA, CNRS, AIM,
F-91190 Gif-sur-Yvette, France

F. Louvet et al.: ALMA-IMF


**Appendix A:** **Core completeness tests in ALMA-IMF**
**observations**


We display the completeness tests for each of the 15 ALMAIMF fields. We define the completeness as the mass limit above
which more than 90 % of the synthetic cores get extracted.


**Appendix B:** **Effect of the smoothing on the** _**GExt2D**_
**extractions**


We show the effect of smoothing the maps on the source sizes derived by _GExt2D_ . Figure B.1 shows the scatter plot of all source
sizes before (left panel) and after (right panel) smoothing the
maps to a match spacial scale of 2700 au.


**Appendix C:** **Continuum maps overlaid by both**
**getsf and GExt2D sources**


In this Appendix, we display for each field the sources extracted
by _getsf_ and by _GExt2D_ . In Fig. C.1, we show the sources
extracted by _getsf_ only with blue ellipses, those extracted by
_GExt2D_ only with green ellipses, and those extracted by both
algorithms with black ellipses.


**Appendix D:** **Table of sources, after smoothing the**

**maps**


In this Appendix, we show the core catalogues for each of the
15 protoclusters. The first group of sources in each table corresponds to thermal dust cores that are gravitationally bound,
and the second group corresponds to sources whose fluxes
are arguably contaminated by free-free emission. All the tables are available on the ALMA-IMF website ( `[https://www.](https://www.almaimf.com/)`
`[almaimf.com/](https://www.almaimf.com/)` [), and on CDS.](http://cdsportal.u-strasbg.fr/)



Article number, page xvii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. A.1: Core completeness tests on the ALMA-IMF fields. The curve shows the percentage of synthetic cores extracted as a
function of their mass. The green line shows the 90 % threshold.


Article number, page xviii of xlix

F. Louvet et al.: ALMA-IMF


Fig. A.1: Completeness tests (continued).



Article number, page xix of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. A.1: Completeness tests (continued).


Fig. B.1: Same as Fig. 1 for the sources extracted by GExt2D.



Article number, page xx of xlix

F. Louvet et al.: ALMA-IMF


Fig. C.1: Continuum emission maps at 1.3 mm for the 15 ALMA-IMF fields with a spatial resolution of 2700 au. The ellipses locate
all the cores found by _getsf_ in blue, by _GExt2D_ in green, and by both algorithms in black. The field name is indicated in the top left
corner of each panel, its evolutionary stage next to the field name, and the beam size in the bottom left corner.


Article number, page xxi of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. C.1: Continuum emission maps at 1.3 mm. Continued.



Article number, page xxii of xlix

F. Louvet et al.: ALMA-IMF


Fig. C.1: Continuum emission maps at 1.3 mm. Continued.



Article number, page xxiii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF


Fig. C.1: Continuum emission maps at 1.3 mm. Continued.



Article number, page xxiv of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxv of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xxvi of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxvii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xxviii of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxix of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xxx of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxxi of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xxxii of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxxiii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article numb r, page xxxiv of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxxv of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xxxvi of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxxvii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xxxviii of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xxxix of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xl of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xli of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xlii of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xliii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xliv of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xlv of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xlvi of xlix

F. Louvet et al.: ALMA-IMF



Article number, page xlvii of xlix

_A&A proofs:_ manuscript no. CMF-in-ALMA-IMF



Article number, page xlviii of xlix

F. Louvet et al.: ALMA-IMF


Fig. E.1: The plot shows the probability density function for a
power-law on the 10 [3] draws to estimate the fit error on the CMF
(see Sect. 5.2).


**Appendix E:** **Monte Carlo simulations for fitting the**
**slope of the CMF**


In this Appendix we display in Fig. a:incertitudes the functional
parameters retrieved when adjusting a power-law (in blue), an
exponential (in green), or a log-normal (in orange) with the MLE
technique (see Sect. 5.2.1.



Article number, page xlix of xlix


</paper>

## Items to check

```json
[
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "CH3OCHO",
  "failed_quote": "we cross-correlated the position of continuum sources (see Sect. 3.3) with methyl formate (CH 3 OCHO) emission maps that were observed by ALMA-IMF."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Checked that the mean extracted source size after smoothing is uniform across all 15 fields (L = 3840 ± 270 au, Fig. 1 right panel).",
  "failed_quote": "The right panel of Fig. 1 shows the sizes of the sources we extracted with _getsf_ for each field. The mean size is similar for each field with _L_ = 3840 ± 270 au."
 },
 {
  "path": "analysis_steps[5].method.evidence[2]",
  "value": "Inject synthetic 2D circular Gaussian cores (FWHM = 3840 au) onto the source-subtracted background maps in 10 mass bins across 4 draws (~3800 synthetic cores per field), re-extract with getsf, and find the 90% recovery mass limit.",
  "failed_quote": "Following Paper III, we consider reaching the completeness limit when 90 % of the synthetic cores are extracted."
 },
 {
  "path": "analysis_steps[6].key_parameters[0].evidence[1]",
  "value": "x_min = 1.64 M_sun; n = 330 cores; 10^3 Monte Carlo trials with β ~ N(1.5, 0.2), T ~ N(T_core, σ_T), and Gaussian flux errors; 10^5 Salpeter synthetic trials.",
  "failed_quote": "In our Monte Carlo simulation, the opacity index β can take random normal values with a mean value of 1.5 (Ossenkopf & Henning 1994) and a standard deviation of 0.2 for each core."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "Smoothing to a matched physical resolution is required and successfully produces a spatially homogeneous core sample.",
  "failed_quote": "The right panel of Fig. 1 shows the sizes of the sources we extracted with _getsf_ for each field. The mean size is similar for each field with _L_ = 3840 ± 270 au."
 }
]
```
