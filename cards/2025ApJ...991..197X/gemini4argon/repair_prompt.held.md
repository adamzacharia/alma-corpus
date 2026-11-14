# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...991..197X\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version August 18, 2025
Typeset using L [A] TEX **default** style in AASTeX7


**SQ-A:** **A** **Collision** **Triggered** **Starburst** **in** **Intra-Group** **Medium** **of** **Stephan’s** **Quintet**


[C. K.](http://orcid.org/0000-0002-1588-6700) Xu, [1, 2] C. [Cheng,](http://orcid.org/0000-0003-0202-0534) [1, 2, 3] [M. S.](http://orcid.org/0000-0001-7095-7543) Yun, [4] P. N. [Appleton,](http://orcid.org/0000-0002-7607-8766) [5] B. H. C. Emonts, [6] J. [Braine,](http://orcid.org/0000-0003-1740-1284) [7] S. C. [Gallagher,](http://orcid.org/0000-0001-6217-8101) [8]

P. [Guillard,](http://orcid.org/0000-0002-2421-1350) [9, 10] U. [Lisenfeld,](http://orcid.org/0000-0002-9471-5423) [11, 12] E. [O’Sullivan,](http://orcid.org/0000-0002-5671-6900) [13] F. [Renaud,](http://orcid.org/0000-0001-5073-2267) [14, 15] P. [Aromal,](http://orcid.org/0009-0001-2178-4022) [8, 16] [P.- A.](http://orcid.org/0000-0003-3343-6284) Duc, [17] A. [Labiano,](http://orcid.org/0000-0002-0690-8824) [18] and

A. [Togi](http://orcid.org/0000-0001-5042-3421) [19]


1 _Chinese_ _Academy_ _of_ _Sciences_ _South_ _America_ _Center_ _for_ _Astronomy,_ _National_ _Astronomical_ _Observatories,_ _CAS,_ _Beijing_ _100101,_ _China_
2 _National_ _Astronomical_ _Observatories,_ _Chinese_ _Academy_ _of_ _Sciences,_ _20A_ _Datun_ _Road,_ _Chaoyang_ _District,_ _Beijing_ _100101,_ _China_
3 _CAS_ _Key_ _Laboratory_ _of_ _Optical_ _Astronomy,_ _National_ _Astronomical_ _Observatories,_ _Chinese_ _Academy_ _of_ _Sciences,_ _Beijing_ _100101,_ _China_
4 _Department_ _of_ _Astronomy,_ _University_ _of_ _Massachusetts,_ _Amherst,_ _MA_ _01003,_ _USA_
5 _Caltech/IPAC,_ _MC_ _314-6,_ _1200_ _E._ _California_ _Blvd.,_ _Pasadena,_ _CA_ _91125,_ _USA._
6 _National_ _Radio_ _Astronomy_ _Observatory,_ _520_ _Edgemont_ _Road,_ _Charlottesville,_ _VA_ _22903,_ _USA_
7 _Observatoire_ _de_ _Bordeaux,_ _UMR_ _5804,_ _CNRS/INSU,_ _BP_ _89,_ _33270_ _Floirac,_ _France_
8 _Institute_ _for_ _Earth_ _and_ _Space_ _Exploration,_ _Western_ _University,_ _1151_ _Richmond_ _St.,_ _London,_ _ON_ _N6A_ _3K7,_ _Canada_
9 _Sorbonne_ _Universit´e,_ _CNRS,_ _UMR_ _7095,_ _Institut_ _d’Astrophysique_ _de_ _Paris,_ _98bis_ _bd_ _Arago,_ _75014_ _Paris,_ _France_
10 _Institut_ _Universitaire_ _de_ _France,_ _Minist`ere_ _de_ _l’Enseignement_ _Sup´erieur_ _et_ _de_ _la_ _Recherche,_ _1_ _rue_ _Descartes,_ _75231_ _Paris_ _Cedex_ _05,_
_France_

11 _Departamento_ _de_ _F´ısica_ _Te´orica_ _y_ _del_ _Cosmos,_ _Universidad_ _de_ _Granada,_ _18071_ _Granada,_ _Spain_
12 _Instituto_ _Carlos_ _I_ _de_ _F´ısica_ _Te´orica_ _y_ _Computacional,_ _Facultad_ _de_ _Ciencias,_ _18071_ _Granada,_ _Spain_
13 _Center_ _for_ _Astrophysics_ _|_ _Harvard_ & _Smithsonian,_ _60_ _Garden_ _Street,_ _Cambridge,_ _MA,_ _02138,_ _USA_
14 _Observatoire_ _Astronomique_ _de_ _Strasbourg,_ _Universit´e_ _de_ _Strasbourg,_ _CNRS_ _UMR_ _7550,_ _F-67000_ _Strasbourg,_ _France_
15 _University_ _of_ _Strasbourg_ _Institute_ _for_ _Advanced_ _Study,_ _5_ _all´ee_ _du_ _G´en´eral_ _Rouvillois,_ _F-67083_ _Strasbourg,_ _France_
16 _Physics_ _and_ _Astronomy_ _department,_ _University_ _of_ _Western_ _Ontario,_ _1151_ _Richmond_ _Street,_ _London,_ _N6A_ _3K7,_ _Ontario,_ _Canada_
17 _Universit´e_ _de_ _Strasbourg,_ _CNRS,_ _Observatoire_ _astronomique_ _de_ _Strasbourg_ _(ObAS),_ _UMR_ _7550,_ _67000_ _Strasbourg,_ _France_
18 _Telespazio_ _UK_ _S.L._ _for_ _the_ _European_ _Space_ _Agency_ _(ESA),_ _ESAC,_ _Spain._
19 _Texas_ _State_ _University,_ _601_ _University_ _Dr,_ _San_ _Marcos,_ _TX_ _78666,_ _USA_


ABSTRACT


We present new observational evidence supporting the hypothesis that SQ-A, a starburst in the
intragroup medium (IGrM) of Stephan’s Quintet (SQ), is triggered by a high-speed collision between
two gas systems, one associated with the IGrM (v _∼_ 6900 km s _[−]_ [1] ) and another with the intruder
galaxy NGC 7318b (v _∼_ 6000 km s _[−]_ [1] ). The new ALMA CO(2-1) dataset has angular resolutions
between 0 _._ 2 _[′′]_ and 7 _._ 0 _[′′]_ and the new VLA HI datacube has an angular resolution of 6 _._ 6 _[′′]_ _×_ 7 _._ 9 _[′′]_ . The
CO maps show that the two gas systems are bridged by another system with an intermediate velocity
of _∼_ 6600 km s _[−]_ [1], whereas the HI data show that the component of v _∼_ 6600 km s _[−]_ [1] fits well into a
gap in the more extended v _∼_ 6000 km s _[−]_ [1] component, albeit with a displacement of _∼_ 5 kpc. Both
the bridge and the complementary distributions between different gas systems are common features
of starbursts triggered by cloud-cloud collision. An analysis of clumps (sizes of 100 – 200 pc) reveals
very diversified star formation (SF) activity in clumps belonging to different kinematic systems, with
the molecular gas depletion time of the v _∼_ 6900 km s _[−]_ [1] clumps more than 10 times longer than that
of the v _∼_ 6600 km s _[−]_ [1] clumps. The results are consistent with a scenario in which the enhanced SF
activity (and the starburst) in the system of v _∼_ 6600 km s _[−]_ [1] is due to gas compression generated in
cloud-cloud collisions, whereas the suppression of SF in the v _∼_ 6900 km s _[−]_ [1] system is due to vortices
(i.e. gas rotation) generated in more complex collisions involving dense clouds and diffuse intercloud
gas accompanied by blast-wave shocks.


Corresponding author: Cong Kevin Xu

2 C.K. Xu et al.


_Keywords:_ Hickson compact group (729); Circumgalactic medium (1879); Intergalactic medium (813);
Interacting galaxies (802); Millimeter astronomy (1061); Galaxy groups (597); Galaxy collisions (585); Shocks (2086); HI line emission (690); Star formation (1569)


1. INTRODUCTION


Starbursts are rarely found in compact groups of galaxies which are aggregates of four to eight galaxies with implied
space densities as high as those in cluster cores (P. Hickson 1982; K. E. Johnson et al. 2007). This is remarkably
different from galaxy mergers where interaction-induced starbursts are very common (D. B. Sanders & I. F. Mirabel
1996; R. C. Kennicutt 1998). Indeed many interacting galaxies in compact groups have their star formation (hereafter
SF) activity quenched rather than enhanced (K. Alatalo et al. 2014). SQ-A, a starburst in the intra-group medium
(IGrM) of the famous compact group Stephan’s Quintet (hereafter SQ), is quite unique. As a prototype of compact
groups, SQ is undergoing a very complex web of interactions between member galaxies and various constituents of the
IGrM (M. Moles et al. 1997; J. W. Sulentic et al. 2001), which in turn have triggered some spectacular activities such
as a _∼_ 40 kpc large scale shock (shown as a large radio and X-ray ridge; R. J. Allen & J. W. Hartsuiker 1972; C. K.
Xu et al. 2003; G. Trinchieri et al. 2003; E. O’Sullivan et al. 2009) and the IGrM starburst SQ-A.
SQ-A was discovered as a bright infrared source by C. Xu et al. (1999) using the Infrared Space Observatory (ISO;
M. F. Kessler et al. 1996). Because of the relatively low resolution ( _∼_ 10 _[′′]_ ) of the ISO observation, SQ-A originally
included the entire region beyond the northern tip of the large scale shock (R. J. Allen & J. W. Hartsuiker 1972; C. K.
Xu et al. 2003; G. Trinchieri et al. 2003; E. O’Sullivan et al. 2009). The SQ-A region, also known as the “northern star
burst region” in the literature (S. C. Gallagher et al. 2001; K. Fedotov et al. 2011), is faint in optical and near-infrared
(NIR) continuum (C. Xu et al. 1999) though relatively bright in H _α_ (H. Arp 1995; M. Moles et al. 1998; J. IglesiasParamo & J. M. Vilchez 2001; C. Mendes de Oliveira et al. 2001; S. Duarte Puertas et al. 2019). In contrast it is very
bright in the ISO 15 _µm_ band, with a peak surface brightness second only to that of the Sy2 nucleus of the NGC 7319
which is the most massive galaxy of SQ. The more recent observations, particularly the optical spectroscopic imaging
observations by S. Duarte Puertas et al. (2019), reveal that the SQ-A region is dominated by a compact starburst
of size _∼_ 5 _[′′]_ ( _∼_ 2 kpc) and a velocity _∼_ 6680 km s _[−]_ [1] (hereafter SQ-A starburst), at the same time it contains many
other star-formation regions of different velocities. According to C. K. Xu et al. (2005), the total SFR of SQ-A is
1.34 M _⊙_ yr _[−]_ [1], comparable to that of the large Sb galaxy NGC 7319 (1.98 M _⊙_ yr _[−]_ [1] ). The very low NIR luminosity
of SQ-A indicates a young age ( _∼_ 10 [7] yr) for the starburst (C. Xu et al. 1999), consistent with the ages of the star
clusters found in the region (S. C. Gallagher et al. 2001; K. Fedotov et al. 2011). Although the general morphology of
the SQ-A region has been reproduced by numerical simulations (F. Renaud et al. 2010; J.-S. Hwang et al. 2012), its
starburst nature has not.
There has been a debate on how the SQ-A starburst is triggered. C. Xu et al. (1999) argued that the starburst is
triggered by a collision of two gas systems, one with system velocity of _∼_ 6600 km s _[−]_ [1] associated with the IGrM and
the other with velocity of _∼_ 6000 km s _[−]_ [1] associated with the intruder galaxy NGC 7318b, because both the HI data
(G. S. Shostak et al. 1984) and H _α_ data (C. Xu et al. 1999; C. Mendes de Oliveira et al. 2001) show overlaps of the two
systems at the position of SQ-A. However, from the beginning, this interpretation has been challenged by a difficult
question: if high speed collision between gas systems can trigger starburst, why is no starburst found in the shock
region associated with the large radio and X-ray ridge? It is well established that the large scale shock is triggered by
an ongoing collision between the IGrM and the intruder NGC 7318b (R. J. Allen & J. W. Hartsuiker 1972; M. Moles
et al. 1997; J. W. Sulentic et al. 2001; C. K. Xu et al. 2003; P. N. Appleton et al. 2006; P. Guillard et al. 2009; M. E.
Cluver et al. 2010; P. N. Appleton et al. 2013; P. Guillard et al. 2022; P. N. Appleton et al. 2023). According to M. E.
Cluver et al. (2010), the shocks and turbulence produced by the high-speed collision are more likely to suppress the SF
rather than trigger a starburst. An alternative model to explain the starburst in SQ-A was proposed by C. Mendes de
Oliveira et al. (2001) who listed the two kinematic systems in SQ-A as two separate tidal dwarf candidates, suggesting
that the SF in SQ-A is tidally induced and the collocation of multiple kinematic components in the region is due to
projection effect.
Can shocks and turbulence powered by high-speed collisions trigger starbursts and at the same time suppress the
SF activity elsewhere in the involved gas systems? What are the physical mechanisms behind these processes? The
answer of these questions may have far-reaching inferences to our understanding of the SF in gas systems, particularly
the triggered SF (B. G. Elmegreen 1998) which may play an important role in the SF activity in interacting galaxy

SQ-A: A Collision Triggered Starburst 3


systems. In this paper, using the new high resolution CO data obtained by ALMA and HI data by B, C & D arrays of
Karl G. Jansky Very Large Array (VLA), we aim to answer these questions. In particular, we re-visit the question: is
SQ-A triggered by a collision of the IGrM and the intruder? Significant progress has been achieved recently in cloudcloud collision (hereafter CCC) theories (A. Habe & K. Ohta 1992; K. Takahira et al. 2014; D. Abe et al. 2021; R.
Maeda et al. 2021, 2024) which can provide powerful tools for our investigation. Encouraged by successful applications
of the CCC models to large extra-galactic SF regions such as the overlap region of Antennae Galaxies and 30 Doradus
in the Large Magellanic Cloud (K. Tsuge et al. 2021a,b; Y. Fukui et al. 2017; K. Tsuge et al. 2024), we are motivated
to find more signatures of collision triggered SF in SQ-A.
The paper is organized as follows: after this introduction, we present the observational datasets used in this work
in Section 2. Our results revealing new evidence for collisions between different gas systems in SQ-A are presented in
Section 3. In Section 4 (and Appendix A) we carry out an analysis on the properties of clumps (size _∼_ 100 – 200 pc)
aiming to probe the cloud-level physical conditions leading to active SF or suppression of it in SQ-A. Section 5 is
devoted to discussions. In Section 6 we present our conclusions. Throughout the paper we assume a distance of 94
Mpc (1” corresponds to 0.45 kpc). The velocities are in the optical redshift convention and the local standard of rest
(LSR) reference frame.


2. OBSERVATIONS


2.1. _ALMA_ _Observations_ _of_ _CO(2-1)_


CO(2-1) data of different angular resolutions and different coverages are utilized in this paper. They are obtained
using ALMA in different configurations. Mosaic observations using the Atacama Compact Array (ACA) cover a region
of _∼_ 10 arcmin [2] that includes all five member galaxies of SQ and most of the IGrM, with a synthetic beam of 8 _._ 0 _[′′]_ _×_ 7 _._ 0 _[′′]_

(see B. H. C. Emonts et al. 2025). We added to this new observations of similar mosaic coverage but higher ( _∼_ 0.6”)
resolution done with the ALMA 12m array in C43-3 configuration from Aug 16 - Sept 5 2024 (ID: 2023.1.00177.S; PI:
Appleton) with a total on-source integration time of 6.4 hours (hereafter TM2 data). These data were calibrated by
the ALMA calibration pipeline version 2023.1.0.124 for Cycle-10 (T. R. Hunter et al. 2023) and delivered as calibrated
MeasurementSets by the North American ALMA Science Center (NAASC). We used the Common Astronomy Software
Applications (CASA) version 6.6.4.34 ( CASA Team et al. 2022) to image the combined pointings of the ALMA and
ACA mosaics that include the SQ-A region (TM2+ACA data). The imaging was done by using a Briggs weighting
with robustness 0.5 (D. S. Briggs 1995) and applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1”
down to a threshold of 3.5 mJy beam _[−]_ [1] . This resulted in a line-data cube with an angular resolution of 1 _._ 0 _[′′]_ _×_ 0 _._ 66 _[′′]_

at position angle (PA) -12.7 _[◦]_, channel width of 15 km s _[−]_ [1], and a root-mean-square (rms) noise of 0.85 mJy beam _[−]_ [1]

in the center of the SQ-A field. A primary beam correction was applied, which increased the rms noise towards the
edges of the field.
Finally, the ALMA data of even higher resolution in a single-pointing field centered on the SQ-A starburst, namely
the “Field 4” of P. N. Appleton et al. (2023), were taken from the ALMA archive (ID: 2015.1.00241.S; PI: P. Guillard)
and reprocessed with CASA using the default script ScriptForPI.py to obtain the calibrated MeasurementSets.
Then we clean the image by TCLEAN with the parameters WEIGHTING = “natural”. The final data cube
reaches an rms of about 0.66 mJy beam _[−]_ [1] and channel width of 4 km s _[−]_ [1], with a beam size of 0 _._ 38 _[′′]_ _×_ 0 _._ 23 _[′′]_ and PA=0.86 degree. Compared to the original Field 4 datacube presented in P. N. Appleton et al. (2023), the reprocessed
cube has the following improvements: (1) a velocity bin-width of 4 km s _[−]_ [1] instead of 20 km s _[−]_ [1] ; (2) a much larger
field of view of size = 38 _[′′]_ (though results outside the 22 _[′′]_ primary beam must be taken with caution). In this work,
we assume a CO conversion factor _α_ CO10 = 1 _._ 0 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] and a CO(2-1) to CO(1-0) luminosity ratio
r 21 = L _[′]_ CO(2 _−_ 1) _[/]_ [L] _[′]_ CO(1 _−_ 0) [= 0] _[.]_ [34] [(][B.] [H.] [C.] [Emonts] [et] [al.] [2025][).] [It] [is] [worth] [noting] [that] [both] _[α]_ [CO10] [and] [r] [21] [are] [quite]
uncertain. A detailed discussion of these uncertainties is given in Section 5.3.


2.2. _VLA_ _Observations_ _of_ _HI_ _21_ _cm_ _Line_


The VLA B-array observations of the 21 cm HI transition were carried out for a total of 40 hours between May 27
and June 5 of 2005 as part of the AY155 program. The spectrometer setup used was identical to the earlier C & D
arrays observations reported by L. Verdes-Montenegro et al. (2001) and B. A. Williams et al. (2002), with a velocity
resolution of 21.5 km sec _[−]_ [1] . A nearby VLA calibrator 2234+282 was observed frequently to track the instrument gain,
and 3C 48 (0134+329) was observed for the bandpass and flux calibration. All of the data were calibrated using the
standard VLA calibration procedure in AIPS and imaged using IMAGR. In order to achieve better UV coverage and

4 C.K. Xu et al.


**Figure** **1.** Contour maps of the HI 21cm emission obtained using the VLA B, C & D arrays (white contours, resolution:
7 _._ 9 _[′′]_ _×_ 6 _._ 7 _[′′]_ ) and the VLA C & D arrays (magenta contours, resolution: 19 _._ 4 _[′′]_ _×_ 18 _._ 6 _[′′]_ ), and that of the CO (2-1) emission
obtained using the ALMA ACA array (yellow contours, resolution: 8 _._ 0 _[′′]_ _×_ 7 _._ 0 _[′′]_ ) overlaid on a three-color image of the UV and
optical emissions (blue: NUV, C. K. Xu et al. 2005; green: deep g-band, P.-A. Duc et al. 2018; red: H _α_, C. Xu et al. 1999).
Note that the ACA CO (2-1) contours in the shock region look orange because of the colored background. The small box
delineated by yellow dashed lines (size=36 _[′′]_ _×_ 30 _[′′]_ ) marks the location of the ”SQ-A region” studied in this paper. The inset in
the upper-right corner is a three-color JWST image (blue: 7.7 _µm_ ; green: 10 _µm_ ; red: 15 _µm_ ) of the SQ-A region.


better sensitivity, we combine these data with those obtained with the VLA C & D arrays (beam = 19 _._ 4 _[′′]_ _×_ 18 _._ 6 _[′′]_ ;
B. A. Williams et al. 2002). The final HI data cube has a synthesized beam of 7 _._ 9 _[′′]_ _×_ 6 _._ 7 _[′′]_ (FWHM) and a velocity
coverage of 5550 – 6885 km s _[−]_ [1] .


2.3. _JWST_ _MIRI_ _images_


Archived images in three MIRI bands of the James Webb Space Telescope (JWST) are downloaded from the Dawn
JWST Archive (DJA) website [20] [21] (F. Valentino et al. 2023). These are F770W, F1000W and F1500W bands centered
at 7.7 _µm_, 10 _µm_ and 15 _µm_ with the angular resolutions of 0 _._ 27 _[′′]_ _,_ 0 _._ 33 _[′′]_ and 0 _._ 49 _[′′]_, respectively (D. Dicken et al. 2024).
The astrometric precision of the MIRI images matches well with that of GAIA DR3 which is on the order of 1 mas
(M. Libralato et al. 2024). The F770W and F1000W data are used only in the inset of Fig. 1 for illustration. The
15 _µm_ image taken from the F1500W data is used in the analysis of clumps (Section 4). The 15 _µm_ emission is
dominated by thermal emission of warm dust heated by massive stars, and therefore is a good SF indicator (C. Xu
et al. 1999). In principle, the 7.7 _µm_ image (dominated by the PAH emission) and 10 _µm_ image (warm dust emission)
may also be used to study SF. They have better angular resolutions than the 15 _µm_ image and are also insensitive to
dust extinction which can be substantial in SQ-A (S. Duarte Puertas et al. 2021). However both F770W and F1000W
are significantly contaminated by shock-excited warm H 2 line emissions and therefore are disfavored: the F770W filter
includes the H2S(4) line at 8.025 _µm_ and the F1000W filter the H2S(3) line at 9.665 _µm_ . Both H 2 lines are bright in


20 [https://s3.amazonaws.com/grizli-v2/JwstMosaics/v4/index.html](https://s3.amazonaws.com/grizli-v2/JwstMosaics/v4/index.html)
21 [https://zenodo.org/records/8370018](https://zenodo.org/records/8370018)

SQ-A: A Collision Triggered Starburst 5


SQ (M. E. Cluver et al. 2010; P. N. Appleton et al. 2023). It is worth noting that the F1500W filter also includes a
bright emission line [NIII] _λ_ 15 _._ 56 _µ_ m which is dominantly associated with SF regions. It may not affect the 15 _µm_ flux
as an SFR indicator significantly if the [NIII] _λ_ 15 _._ 56 _µ_ m-to-continuum ratio is relatively constant.


3. COLLISION OF SYSTEMS ASSOCIATED WITH IGRM AND INTRUDER


In Fig. 1 contours of the VLA HI maps of resolution=7 _._ 9 _[′′]_ _×_ 6 _._ 7 _[′′]_ (white contours) and of resolution=19 _._ 4 _[′′]_ _×_ 18 _._ 6 _[′′]_

(magenta contours), and contours of the ACA CO (2-1) map (yellow contours, resolution = 8 _._ 0 _[′′]_ _×_ 7 _._ 0 _[′′]_ ) are overlaid
on a three-color image of the UV and optical emissions (blue: NUV, C. K. Xu et al. 2005; green: deep g-band, P.-A.
Duc et al. 2018; red: H _α_, C. Xu et al. 1999). A more comprehensive comparison of the CO and HI data in entire
SQ will be presented in a future paper (Cheng et al., in preparation). In this paper we will concentrate on the SQ-A
region, shown by the small yellow box (size=36 _[′′]_ _×_ 30 _[′′]_ ) in the upper-right quadrant of the figure. The inset in the
upper-right corner is a three-color JWST image (blue: 7.7 _µm_ ; green: 10 _µm_ ; red: 15 _µm_ ; K. M. Pontoppidan et al.
2022) of the SQ-A field which reveals the detailed morphology of the SF regions behind the CO and HI contours in
the main figure.


**Figure** **2.** Spectra of the CO (2-1) and the HI (scaled up by a factor of 20) in the SQ-A region.


In Fig. 2, the CO(2-1) and HI spectra extracted from the CO(2-1) cube of ALMA ACA and the HI cube of VLA
B, C & D arrays in the SQ-A region (the yellow box in Fig. 1) are presented. It is worth noting that the two cubes
have very similar angular resolutions (ACA CO(2-1): 8 _._ 0 _[′′]_ _×_ 7 _._ 0 _[′′]_, VLA B, C & D arrays HI: 7 _._ 9 _[′′]_ _×_ 6 _._ 7 _[′′]_ ) and therefore
the comparison between them is robust. The CO spectrum shows clearly three components. Following the literature
(G. S. Shostak et al. 1984; B. A. Williams et al. 2002; C. Cheng et al. 2023), we call them the 6000, 6600 and 6900
components, which are in velocity ranges of 5900 – 6100, 6500 – 6800 and 6800 – 7000 km s _[−]_ [1], respectively. As shown
in Table 1, the 6900 component has the highest molecular gas mass M mol which is 1.9 and 1.5 times the M mol of the
6000 and 6600 component, respectively. For the 6000 and 6600 components the HI is much more abundant than the
molecular gas: M HI is about 10 times higher than M mol for both components. Unfortunately the 6900 component is
not covered by the VLA HI observations. Preliminary results of a new MeerKAT observation of HI emission in SQ
(unpublished) indicate that the HI gas in SQ-A region does have a 6900 component, albeit with an M HI less than half
of that of the 6000 component (private communication with K. Rajpurohit). Together with the data in Table 1, this
suggests that the gas associated with the 6900 component is denser than that associated with the 6000 component
because the former has a M mol -to-M HI ratio _∼_ 4 times higher than the latter. The HI 6900 component seems to be
more extended than the CO counterpart but, given the larger beam of the MeerKAT map ( _∼_ 15 _[′′]_ ) compared to that
of the ACA, caution is needed about any direct comparison at this stage.
The left panel of Fig. 3 shows the spatial distributions of the three kinematic components of **CO** using contours
of their ACA maps, overlaid on a JWST 15 _µm_ image. The 6900 and 6000 components do not overlap with each

6 C.K. Xu et al.


**Figure** **3.** _Left_ : Contours of the ALMA ACA map of CO(2-1) in the SQ-A region, overlaid on a JWST 15 _µm_ image.
The blue, green, and red contours are for the 6000, 6600, and 6900 components, respectively (contour levels: 1.3, 1.4, 1.5, . . .
Jy beam _[−]_ [1] km s _[−]_ [1] ). The three maps have r.m.s. of 0.36, 0.41, 0.39 Jy beam _[−]_ [1] km s _[−]_ [1], respectively. The purple dashed line
near the upper-right corner of the figure shows the boundary of the ACA observation. The inner box delineated by the red
dashed lines marks the locaton of the SQ-A region. _Right_ : Contours of the VLA B, C & D arrays map of HI overlaid on the
JWST 15 _µm_ image. Blue and green contours are for the 6000 and 6600 components, respectively (contour levels at 0.04, 0.05,
0.06, . . . Jy beam _[−]_ [1] km s _[−]_ [1] ). Both maps have the same r.m.s. = 0.01 Jy beam _[−]_ [1] km s _[−]_ [1] . Again the red box delineates the
SQ-A region.


**Table** **1.** Properties of three kinematic components of gas in SQ-A region.


**6000** **6600** **6900**


v range [km s _[−]_ [1] ] : 5900 – 6100 6500 – 6800 6800 – 7000
f CO(2 _−_ 1) [Jy km s _[−]_ [1] ] [(] _[a]_ [)] : 4.8 _±_ 0 _._ 5 6.0 _±_ 0 _._ 6 8.8 _±_ 0 _._ 9
M mol [10 [8] _×_ M _⊙_ ] [(b)] : 0.75 _±_ 0 _._ 38 0.93 _±_ 0 _._ 47 1.4 _±_ 0 _._ 7
v CO [km s _[−]_ [1] ] : 6010 _±_ 32 6719 _±_ 41 6930 _±_ 33
W20 CO [km s _[−]_ [1] ] [(] _[c]_ [)] : 76 132 112
f HI [Jy km s _[−]_ [1] ] [(] _[d]_ [)] : 0.46 _±_ 0 _._ 07 0.65 _±_ 0 _._ 10 —
M HI [10 [9] _×_ M _⊙_ ] : 0.95 _±_ 0 _._ 14 1.35 _±_ 0 _._ 20 —
v HI [km s _[−]_ [1] ] : 6020 _±_ 31 6645 _±_ 63 —
W20 HI [km s _[−]_ [1] ] [(] _[e]_ [)] : 129 280 —
SFR [M _⊙_ yr _[−]_ [1] ] [(f)] : 0.37 0.98 0.07
t dep [10 [8] yr] [(g)] : 2.02 0.95 19.5


**Notes:** [(] _[a]_ [)] Integrated CO(2-1) flux. A 10% calibration uncertainty is assumed which dominates the errors. ( _b_ ) Molecular gas
mass estimated from the CO (2-1) data assuming the CO conversion factor _α_ _CO_ 10 = 1 _._ 0 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] and the CO(2-1)
to CO(1-0) luminosity ratio r 21 = L _[′]_ CO(2 _−_ 1) _[/]_ [L] _[′]_ CO(1 _−_ 0) [= 0] _[.]_ [34] [(][B.] [H.] [C.] [Emonts] [et] [al.] [2025][).] [A] [50%] [uncertainty] [is] [assumed] [for]
_α_ _CO_ 10 which dominates the errors. [(] _[c]_ [)] CO(2-1) line width measured at 20% of peak. [(] _[d]_ [)] Integrated HI flux. A 15% calibration
uncertainty is assumed which dominates the errors. ( _e_ ) HI line width measured at 20% of peak. ( _f_ ) The star formation rate
(SFR) estimated using the extinction-corrected H _α_ luminosities of the H II regions (including only SF dominated regions and
excluding the composite regions) in the SQ-A region (S. Duarte Puertas et al. 2021). [(] _[g]_ [)] Depletion time scale of molecular gas:
t dep = M mol _/_ SFR.

SQ-A: A Collision Triggered Starburst 7


**Figure** **4.** _Left_ : HI maps in the SQ-A region. The blue and green colors are for the 6000 and 6600 components, respectively.
The contour levels are: 0.04, 0.05, 0.06, . . . Jy beam _[−]_ [1] km s _[−]_ [1] . The red star shows the location of the SQ-A starburst (redshift:
6680 km s _[−]_ [1], S. Duarte Puertas et al. 2019). _Right_ : Same as the left panel except for the map of the 6600 component is shifted
eastward by 12 arcsec.


other but are bridged by the the 6600 component. Many SF regions, including the SQ-A starburst that corresponds
to the brightest 15 _µm_ peak near the figure center, are associated with the **CO** **gas** . However, several SF regions in
the upper-right corner of the figure (near the edge of the ACA coverage as shown by the purple dashed line), which
are associated with the 6000 component (S. Duarte Puertas et al. 2019), are not significantly detected by the ACA
observations because their CO emission is only on the 2- _σ_ level ( _σ_ = 0 _._ 39 Jy beam _[−]_ [1] km s _[−]_ [1] ).
The right panel of Fig. 3 presents the HI gas distributions of only the 6000 and 6600 components while the 6900
component is missed by the HI observations. The HI distributions of both components are more extended than their
CO counterparts. Very interestingly, the 6600 HI seems to be located in a gap of the much more extended 6000
HI gas. Fig. 4 demonstrates that, when the 6600 HI map is shifted relative to the 6000 HI map eastwardly by 12 _[′′]_

(corresponding to a linear scale of _∼_ 5 kpc for a distance of 94 Mpc), the maps of the two components become very
“complementary” in the sense that the 6600 map fits nearly perfectly to the gap in the 6000 map. Note that the

_∼_
5 kpc transverse displacement, without which the complementary nature of the distributions of the two components
is not easily recognizable, is the projection of a 3-dimensional relative movement between the two components. This
is consistent with the CCC scenario (see e.g. Fig. 8 of K. Tsuge et al. 2021b). This new piece of supporting evidence
enables us to conclude with high confidence that the multiple kinematic components in SQ-A are colliding with each
other and their collocation in the region is not merely a projection effect.

Y. Fukui et al. (2021) have shown that there are two key common properties in all cases of CCC triggered SF:
(1) gas systems involved in the collision show complementary distributions, with relative displacement explainable by
relative motion and projection effects (as in the case shown in Fig. 4), and (2) a “bridge” (an intermediate velocity
system) lies in between the colliding systems. It appears that kinematic components in SQ-A have both of these
properties (Fig. 3 and Fig. 4). This suggests the following scenario: The SQ-A starburst is triggered by a collision
between the 6900 component (associated with the IGrM) and the 6000 component (associated with the intruder galaxy
NGC 7318b). It appears that only a part of the 6900 component as well as a part of the 6000 component are involved
in the collision. During the collision the 6900 gas, which is likely to be denser and more compact than the 6000 gas,
is decelerated and compressed, and this decelerated and compressed gas becomes the 6600 component in which the
SQ-A starburst (v _∼_ 6680 km s _[−]_ [1] ) is triggered. At the same time, the 6000 gas involved in the collision is swept into
the 6600 component and/or dispersed, leaving a gap in the 6000 map at the place where the 6600 component crashes
through. The displacement shown in Fig. 4, which is _∼_ 5 kpc in linear scale, suggests an age of the collision of a few

8 C.K. Xu et al.


10 [7] years (assuming a transverse relative velocity of a few 100 km s _[−]_ [1] between the colliding systems), consistent with
the estimated time scale for the age of the encounter between the intruder and SQ (J. W. Sulentic et al. 2001). We
will discuss this scenario in more depth in Section 5.1.


**Figure** **5.** Contour maps of the CO (2-1) emissions overlaid on a JWST 15 _µm_ image. Solid contours are for the combined
TM2+ACA data which have a synthetic beam of 1 _._ 0 _[′′]_ _×_ 0 _._ 66 _[′′]_, with the blue contours representing the 6000 component (levels:
0.14, 0.19, 0.24, 0.29 and 0.34 Jy beam _[−]_ [1] km s _[−]_ [1] ), the green contours the 6600 component (levels of 0.16, 0.2, 0.25, 0.3 and
0.35 Jy beam _[−]_ [1] km s _[−]_ [1] ), and the red contours the 6900 component (levels of 0.22, 0.27, 0.32 and 0.37, . . . Jy beam _[−]_ [1] km s _[−]_ [1] ).
These maps have the r.m.s. of 0.048, 0.053 and 0.059 Jy beam _[−]_ [1] km s _[−]_ [1], respectively. Dashed contours (just one level at 1.3
Jy beam _[−]_ [1] km s _[−]_ [1] ) are for the ACA data which have a synthetic beam of 8 _._ 0 _[′′]_ _×_ 7 _._ 0 _[′′]_, again the blue, green and red contours are
for the 6000, 6600 and 6900 components, respectively. The small circles (r = 0 _._ 25 _[′′]_ ) represent the clumps identified in the Field
4 of the high resolution CO (2-1) observations (beam = 0 _._ 38 _[′′]_ _×_ 0 _._ 23 _[′′]_ ), with the colors of white, cyan and yellow representing
the 6000, 6600 and 6900 components, respectively. The black dash-dot line marks the boundary of the primary beam (r = 11 _[′′]_ )
of the high resolution CO (2-1) single-pointing observation.


In Table 1, we present the properties of the three kinematic components. It appears that, among them, the 6600
component has the broadest CO and HI line widths, consistent with the hypothesis that it is formed in the post-shock
gas after the collision between the other two components. The SFR data are adopted from S. Duarte Puertas et al.
(2021) after adjusting the difference between the adopted distances of SQ (they assume a distance of 88.6 Mpc). The
total SFR of SQ and the SFR of SQ-A estimated from extinction-corrected H _α_ luminosities of the H II regions are
both consistent with the UV-and-IR estimated values of C. K. Xu et al. (2005). In addition, S. Duarte Puertas et al.
(2021) provided the velocity information for the SF regions and distinguished composite regions (shock excited) from
SF regions using the BPT diagrams. The 6600 component has the highest SFR, dominated by the starburst. The
6000 component has also a sizable SFR though about a factor of 3 lower than that of 6600 component. The 6900
component has very little SF, its SFR is more than an order of magnitude lower than that of 6600 component.


4. PROPERTIES OF CLUMPS OF MOLECULAR GAS IN SQ-A


4.1. _Clumps_ _Extracted_ _from_ _High_ _Resolution_ _CO(2-1)_ _Datacube_


In order to probe at the cloud level the physical conditions that lead to the conspicuous difference in SF activity
in different kinematic components (Table 1), in this section we study “clumps” extracted from the high resolution
CO(2-1) datacube in the Field 4 (P. N. Appleton et al. 2023), exploiting the algorithm “Fellwalker” developed by D.
Berry (2015). According to C. Li et al. (2020), Fellwalker shows high completeness and accuracy compared to other
clump identification algorithms. Fellwalker works as follows: Firstly, it selects in a 3-D cube all pixels that are above
a certain threshold, which we set at 1- _σ_ above the background level. Secondly, it links each of these pixels to a local

SQ-A: A Collision Triggered Starburst 9


maximum along the steepest gradient. Finally it identifies each individual clump as the collection of all pixels that
end up at a same maximum. Details of the clump identification procedure and definitions of various parameters of the
clumps are presented in Appendix A.


**Figure** **6.** _Left_ : Plot of _σ_ v vs. _R_ _e_ for clumps in SQ-A region, compared with the clumps in the Antennae overlap (G. Krahm
et al. 2024) and clouds in Milky Way disk (M. Heyer et al. 2009). The solid line shows the typical relation for Galactic GMCs
(P. M. Solomon et al. 1987). _Right_ : P e vs. _α_ vir plot of clumps in SQ-A region, where P e is the external pressure and _α_ vir the
virial parameter. The yellow dots represent clumps in the Antennae overlap (G. Krahm et al. 2024).


In total 36 clumps are identified in Field 4. They are listed in Table A1 and plotted in Fig. 5. The figure also shows
contour maps of CO (2-1) overlaid on a JWST 15 _µm_ image. Solid contours are for the combined TM2+ACA data
(beam = 1 _._ 0 _[′′]_ _×_ 0 _._ 66 _[′′]_ ) and dashed contours mark the boundaries of ACA detections (beam = 8 _._ 0 _[′′]_ _×_ 7 _._ 0 _[′′]_ ). There are
good correspondences between locations of the clumps and peaks of the intermediate resolution CO map (TM2+ACA)
for the 6600 and 6900 components. For the 6000 component in the north-western part no clumps are found because
this region is outside the primary beam of the Field 4 (whose boundary is marked by the black dash-dot line) and the
sensitivity becomes too low. Around the SQ-A starburst (v=6680 km s _[−]_ [1] ), there is a cluster of 6600 clumps squeezed
inside a compact configuration in the TM2+ACA map. Interestingly, this 6600 configuration is surrounded by a couple
of low level contours of the 6900 and 6000 components as well as two 6900 clumps, consistent with the hypothesis that
there is an on-going interaction among these components at this location. A couple of 15 _µm_ emission regions near the
figure center are not associated with clumps or peaks in the intermediate resolution CO map. They correspond to the
composite regions #126 (R.A.=22 [h] 35 [m] 58 _._ 6 [s], Dec.=+33 _[d]_ 58 _[m]_ 56 _._ 0 _[s]_, v=6881 km s _[−]_ [1] ) and #131 (R.A.=22 [h] 35 [m] 58 _._ 6 [s],
Dec.=+33 _[d]_ 58 _[m]_ 54 _._ 4 _[s]_, v=6856 km s _[−]_ [1] ) in S. Duarte Puertas et al. (2019), both having broad H _α_ lines and line ratios
consistent with shock excitation (S. Duarte Puertas et al. 2019, 2021). The 15 _µm_ emission asscociated with them
must be unrelated to SF.


4.2. _Dynamical_ _Properties_ _of_ _Clumps_


The left panel of Fig. 6 shows the plot of velocity dispersion _σ_ _v_ (Eq. A4) vs. the effective radius R e (Eq. A5) of the
clumps. They have radii in the range of 45 – 100 pc (with a mean of 72 _±_ 3 pc) and velocity dispersions in the range
of 2 – 20 km s _[−]_ [1] (mean = 7 _._ 4 _±_ 0 _._ 5 km s _[−]_ [1] ). It is worth noting that quite a few clumps have sizes (= 2 _×_ R e ) smaller
than the spatial resolution of the ALMA observation ( _∼_ 120 pc). This is because R e is derived from an effective
area A e which in turn is a flux-weighted summary of all pixels in a clump (Eq. A6). The radius so defined has the
advantage of being insensitive to the clump selection effects, but is vulnerable to the error of the flux (similar to the

10 C.K. Xu et al.


**Figure** **7.** The Kenicutt-Schmidt plot of the clumps in SQ-A region, compared with molecular clouds in some nearby SF
galaxies (A. K. Leroy et al. 2025). The solid line (with a slope of 1.4) represents the trend followed by galaxies (K. Alatalo et al.
2014) and the two dotted lines the _±_ 1 order of magnitude deviations.


error in measurement of the beam size using a point source image). For faint clumps with f CO21 _≤_ 0 _._ 03 Jy km s _[−]_ [1],
corresponding to log(M mol _/_ M _⊙_ ) _≤_ 5 _._ 7, the error of R e is on the order of 25%.
There is no significant difference in either R e or _σ_ _v_ between the three components. When compared with the clouds
in the Milky Way disk (M. Heyer et al. 2009), the SQ-A clumps are in the regime of very large giant molecular clouds
(GMCs). Indeed they fall right on the line of the so called ”Larson Law” (the solid line in the plot) found for the
Galactic GMCs (P. M. Solomon et al. 1987). On the other hand, the clouds in the overlap region of the Antennae
Galaxies (hereafter the Antennae overlap) have significantly higher velocity dispersions, _∼_ 5 _×_ above those of SQ-A
clumps and clouds in the Milky Way disk, indicating different physical conditions in them (G. Krahm et al. 2024).
The right panel of Fig. 6 is a plot of the external pressure P e (Eq. A19) vs. the virial parameter _α_ vir (Eq. A20).
Here again the clumps in different kinematic components are well mixed with each other. All but two of them have
_α_ vir _>_ 2, namely are unbound by gravity. The P e _/_ k B is in the range of 3 _×_ 10 [3] – 10 [6] K cm _[−]_ [3], significantly lower than
that of clumps in the Antennae overlap (G. Krahm et al. 2024). Rather, the P e _/_ k B of SQ-A clumps is similar to that
of the GMCs in the Milk Way and nearby galaxies (M. Heyer et al. 2009; D. Donovan Meyer et al. 2013). Note that
adopting a higher CO conversion factor would increase the value of P e _/_ k B and reduce the value _α_ vir . There is a strong
correlation between P e _/_ k B and _α_ vir (the Spearman correlation coefficient r s = 0 _._ 62 with a significance of p= 6 _×_ 10 _[−]_ [5] ),
indicating that the clumps are mainly confined by the external pressure instead of the self-gravity. The clouds in the
Antennae overlap, which have much higher P e _/_ k B and _α_ vir values, lie slightly (by _∼_ 0 _._ 5 dex) above this correlation.


4.3. _Star_ _Formation_ _Properties_ _of_ _Clumps_


Fig. 7 presents the Σ SFR vs. Σ mol plot (the “Kennicutt-Schmidt plot”) of the clumps. The solid line (with a slope
of 1.4) in the figure represents the trend followed by galaxies (K. Alatalo et al. 2014) and the two dotted lines the _±_ 1
order of magnitude deviations. Clumps of three different kinematic components have similar Σ mol values. In contrast,
their Σ SFR values are stratified over _∼_ 2 orders of magnitude range: 6600 clumps are on the top, 6000 clumps in the
middle, and 6900 clumps at the bottom. The high SFR enhancement of 6600 clumps is consistent with the nature of
the SQ-A starburst which is associated with this kinematic component. The 6000 clumps are also undergoing active
SF, while most of 6900 clumps are clearly suppressed with the Σ SFR about an order of magnitude lower than the
nominal line. In SQ-A clumps, Σ SFR does not depend on Σ mol at all: their Spearman rank correlation coefficient is
r s = _−_ 0 _._ 04 and the significance parameter (i.e. probability of the null hypothesis) p = 0 _._ 82.
The depletion time scale t dep, the inverse of the SFR per unit M mol, is another SF activity indicator. Compared to
Σ SFR, t dep has the advantage of being an intensive physical property and therefore insensitive to the ’rich man effect’
(large clouds having large amount of everything). Panel-a of Fig. 8 presents a plot of t dep vs the virial parameter

SQ-A: A Collision Triggered Starburst 11







**Figure** **8.** _Panel_ _a_ : Plot of depletion time (t dep ) vs virial parameter ( _α_ vir ).The red dashed vertical line at _α_ vir = 2 marks the
boundary separating gravitational bound and unbound clumps. _Panel_ _b_ : Plot of depletion time (t dep ) vs the velocity dispersion
( _σ_ v ). _Panel_ _c_ : Plot of t dep vs S parameter (the absolute value of the projected specific angular momentum vector _[⃗]_ S) . _Panel_
_d_ : Plot of depletion time (t dep ) vs the radial velocity gradient (G v ). _Panel_ _e_ : Plot of Sy (the y component of the projected
specific angular momentum vector _[⃗]_ S) vs the S x (the x component of the vector). It shows no trend for a preferred orientation of
the vector. _Panel_ _f_ : Plot of t dep vs C parameter (the nonrotational-to-rotational energy ratio). The Spearman rank correlation
coefficient r s and the significance parameter p (the probability of the null hypothesis) are listed in each plot, with red characters
indicating significant (p _≤_ 0 _._ 01) or marginally significant correlations (0 _._ 01 _<_ p _≤_ 0 _._ 03).


_α_ vir . There is no significant correlation between these two variables, another evidence for the self-gravity not playing
an important role in regulating the SF activity of the clumps. On the other hand, there is a marginally significant
correlation between t dep and the velocity dispersion _σ_ v (the significance parameter p=0.02, panel-b of Fig. 8). Given
the fact that the clumps have _σ_ v much larger than the sound speed (v sound _∼_ 0 _._ 2 km s _[−]_ [1] for gas of T _∼_ 10 K) and
therefore are dominated by non-thermal motions, the correlation suggests that the gas motion may play a significant
role affecting the SF activity in the clumps.
The non-thermal motions can be in many different forms, including contraction, expansion, rotation, shear, and small
scale turbulent motions. Together with the thermal motion, they form a hierarchy and the energy cascades down from
large scales to small scales. In collision systems, the main energy source is the shock triggered by collision (P. Guillard
et al. 2009, 2022). With a resolution of _∼_ 120 pc, we cannot resolve the small scale turbulence. Therefore we begin by
checking the effects of rotation and shear on t dep . A plot of t dep vs the S parameter (Eq. A7) is presented in the panel-c
of Fig. 8. Being a measure of the specific angular momentum, the S parameter is related to a centrifugal force that
can balance gravity and suppress the SF. Indeed we see a significant correlation between t dep and S with a Spearman

12 C.K. Xu et al.


correlation coefficient of r s = 0 _._ 50 and a significance of p=2 _×_ 10 _[−]_ [3] . There is a trend that kinematic component with
higher average t dep (i.e. low SF activity) has also higher average S value ( _⟨_ log(S) _⟩_ = 1 _._ 96 _±_ 0 _._ 19 _,_ 2 _._ 13 _±_ 0 _._ 13 _,_ 2 _._ 19 _±_ 0 _._ 10
for the 6600, 6000 and 6900 components, respectively). The S values have large scatters within individual components
and clear dependence of t dep on S can be recognized in each of all three components. It should also be noted that the
t dep vs S plot is still stratified in the sense that, for a given S, the 6900 clumps tend to have high t dep and the 6600
clumps low t dep and the 6000 clumps in between. This indicates that some other factors, which may be systematically
different in the different kinematic components, can significantly affect the SF in clumps. J. Braine et al. (2018, 2020)
found a tendency for rotation vectors of molecular clouds in M33 and M51 to align with the galactic disk rotation.
However, for SQ-A clumps no trend is found for the orientation of the 2-D vector _[⃗]_ S (panel-e of Fig. 8). This is
consistent with the rotation being driven by localized torques (presumably associated with the collision) instead of
effects associated with large scale motions (as in the cases of M33 and M51 clouds).
Local torque can be generated by shear motion inside the clump, which in turn can be powered by a shock (particularly an oblique shock). The amplitude of a shear can be measured by velocity gradient. Panel-d of Fig. 8 presents
a plot of t dep vs the radial velocity gradient G v (Eq. A14), which shows no significant correlation between the two
variables. This suggests that shear motion may not have a significant direct impact to the SFR.
Panel-f of Fig. 8 presents a plot of t dep vs the C parameter, the nonrotational-to-rotational energy ratio (Eq. A10).
There is a significant anti-correlation in this plot, with the Spearman correlation coefficient of r s = _−_ 0 _._ 41 and significance p = 0 _._ 01. Here we see an even better separation in C than in the S parameter between the three kinematic
components: on average the 6600 component has the highest C and lowest t dep and the 6900 component the lowest C
and highest t dep . While the correlation between t dep and the S parameter indicates a role of rotation in suppressing
the SFR, the anti-correlation between t dep and the C parameter suggests a positive role for non-rotational motion in
enhancing the SFR. Simulations have shown that collisions can generate compressive turbulence (K. Takahira et al.
2014) which in turn can enhance the SFR (M. R. Krumholz 2014; F. Renaud et al. 2014). It is plausible that the
compressive turbulence, which is included in the non-rotational motion, is the engine that drives the enhanced SFR.
By measuring the rotational support and non-rotational motions at cloud scale, we can estimate the degree of stability
of the molecular structures, and connect it to the star formation activity. However, this reasoning is not sufficient
to explain the starburst nature of these regions, that is why star formation proceeds faster here than in classical
clouds of the same molecular gas mass. F. Renaud et al. (2014) used simulations of interacting galaxies to establish
that the starburst regime is reached when the interstellar turbulence becomes dominantly compressive (as opposed to
solenoidal) as the result of galactic-scale tidal compression. This induces an excess of dense gas which not only allows
for elevated star formation (high SFR) but also fast star formation (short depletion time). The same effect could well
be active in SQ-A, with compression originating from the interaction between the intruder-associated material and
the IGrM, and its energy being converted to compressive turbulence, in turn triggering the observed starburst. While
our result on the anti-correlation between t dep and the C parameter seems to support this hypothesis, it is important
to note that we do not have any direct measure of the turbulent motion. Indeed, the ultimate test of this hypothesis
would require the measurement of turbulent motions within the clouds themselves, which remains out of reach of the
present capacities.
It should also be noted that all the correlations presented in Fig. 8 are quite scattered even when they are significant
(p _≤_ 0 _._ 01) or marginally significant (0 _._ 01 _<_ p _≤_ 0 _._ 03). Although there is a trend that clumps in the more SF active
component tend to have lower S parameters and higher C parameters (e.g. _⟨_ log(S) _⟩_ = 1 _._ 96 _±_ 0 _._ 19 and _⟨_ log(C) _⟩_ =
1 _._ 53 _±_ 0 _._ 32 for those in 6600 component), the differences with those in low SF activity components (e.g. in the
6900 component _⟨_ log(S) _⟩_ = 2 _._ 19 _±_ 0 _._ 10 and _⟨_ log(C) _⟩_ = 1 _._ 09 _±_ 0 _._ 15) are only at 1- _σ_ level between the corresponding
means. The large scatters within the same kinematic component are understandable because many factors which are
not controlled in this analysis can affect the variables. These include the variation of the evolution stages among
the clumps, which strongly affects the estimate of t dep (J. M. D. Kruijssen et al. 2018; J. Kim et al. 2022). The
projection effect and beam smearing effect can affect many parameters such as R e, _σ_ v, S parameter (projected specific
angular momentum), C parameter (nonrotation-to-rotation energy ratio), and the velocity gradient (G v parameter).
The small scale variation of the CO conversion factor, particularly if it is t dep dependent (F. Renaud et al. 2019), can
also add on to the scattering of t dep significantly. Nevertheless, the correlations and non-correlations between t dep and
various parameters may provide important insights to the factors that control the SF activity at the cloud level. In
particular the significant correlation between S and t dep strongly suggests that the rotation may play an important
role in hindering collapse and suppressing the SFR. At the same time, our finding that the t dep distribution is still

SQ-A: A Collision Triggered Starburst 13


stratified among different components for a given S (Fig. 8c) demands other factors which can affect the triggered SF
in clumps, such as the compression of gas hinted at by the significant anti-correlation between C and t dep .


5. DISCUSSION


5.1. _CCC_ _Model_ _and_ _SQ-A_ _Starburst_


Fig. 3 and Fig. 4 provide new supporting evidence for the hypothesis that the SQ-A starburst is triggered by a
collision between two gas systems, one associated with the IGrM (v _∼_ 6900 km s _[−]_ [1] ) and another with the intruder
galaxy NGC 7318b (v _∼_ 6000 km s _[−]_ [1] ) . Here we discuss this hypothesis in the context of the CCC theory. Originally,
the CCC theory was proposed to interpret the triggered SF in Galactic GMCs, particularly the formation of young
massive star clusters (YMCs; A. Habe & K. Ohta 1992; T. Inoue & Y. Fukui 2013; K. Takahira et al. 2014). More
recently, this theory was applied to starbursts in large extra-galactic regions (size up to a few kpc) involved in galaxygalaxy collisions, such as the overlap region of the Antennae Galaxies (K. Tsuge et al. 2021a,b) and 30 Doradus plus
southern ridge of the LMC (Y. Fukui et al. 2017; K. Tsuge et al. 2024). Similar to SQ-A, the Antennae overlap region is
undergoing high SF enhancement due to a direct collision of two gas systems associated with two galaxies, respectively
(B. C. Whitmore & F. Schweizer 1995; C. Xu et al. 2000). However, there are remarkable differences between the two
cases. As shown in Table 1, the kinematic systems in SQ-A are dominated by the HI gas (the M HI -to-M mol ratio _∼_ 10).
And the complementary distributions among the different components are found only in the HI maps, not in the CO
maps (Fig. 3). On the other hand, the collision in the Antennae overlap is happening primarily in the molecular gas
which is much more massive than the HI (C. D. Wilson et al. 2000; J. E. Hibbard et al. 2001), and the complementary
distributions of the colliding systems are found in the CO maps (K. Tsuge et al. 2021a). Also, clouds in the Antennae
overlap have much higher velocity dispersions and external pressures, _∼_ 5 _×_ and _∼_ two orders of magnitude higher
than those in SQ-A clumps, respectively (right panel of Fig. 6). Since the collision velocity in SQ-A is much higher
than that in the Antennae overlap which is _∼_ 100 km s _[−]_ [1] (K. Tsuge et al. 2021a), the low pressure in the former is
suggestive of a much lower pre-collision density than in the latter, given the relation P e _∼_ _ρ_ pre v coll [2] [where] _[ρ]_ [pre] [is] [the]
pre-collision density and v coll the collision velocity.
Indeed, SQ-A may be more comparable to the giant SF regions in 30 Doradus which are produced presumably by
a collision of two HI systems, one associated with the LMC and the other accreted from the Small Magellanic Cloud
(SMC; Y. Fukui et al. 2017; K. Tsuge et al. 2024). It is worth noting that, similar to the LMC, SQ-A has a sub-solar
metallicty of Z _∼_ 0 _._ 5 Z _⊙_ (S. Duarte Puertas et al. 2021), which might be the reason for its high M HI -to-M mol ratio.
In direct GMC-GMC collisions, SF is triggered in the denser and smaller cloud when it crashes into a less dense and
larger cloud (A. Habe & K. Ohta 1992; Y. Fukui et al. 2018). On the other hand, the triggered SF in HI-HI collision
is different. As shown in the simulations of R. Maeda et al. (2021, 2024), high velocity collisions (v c _∼_ _>_ 50 km s _−_ 1 )

of HI gas can trigger the formation of a large amount of dense cores (density _>_ 10 [4] cm _[−]_ [3] ) which in turn form YMCs
in a short time scale comparable to the free-fall time of the dense cores (t ff _∼_ _<_ 10 6 years). In these models, because

of the rapid cooling (t cool _<_ 10 [6] years), the density of the post-shock gas is approximately proportional to the shock
velocity which is about a half of the collision velocity. Assuming a collision velocity of _∼_ 1000km s _[−]_ [1] (as it is in SQ-A)
and an initial density of n 0 = 1 cm _[−]_ [3], the post-shock gas density becomes as high as n _∼_ 350 cm _[−]_ [3] (R. Maeda et al.
2024). This gas is thermally unstable and has a free-fall time scale of t ff _∼_ 2 _×_ 10 [6] yr _×_ (n _/_ 350cm _[−]_ [3] ) _[−]_ [0] _[.]_ [5] . After a few
t ff dense cores will form and the starburst follows. The whole process should occur within a time scale of 10 [7] years,
consistent with the time scale we found for the collision in SQ-A. Results of the clump analysis in Section 4, which
shows a lack of dependence of SFR on density (Fig. 7) and an anti-correlation between t dep and the C parameter
(panel-f of Fig. 8), also support the scenario in which much of the SF in SQ-A is collisionally triggered instead of
gravitationally induced. S. C. Gallagher et al. (2001) and K. Fedotov et al. (2011) found large amount of young stellar
clusters (ages of _≤_ 10 [7] years) in SQ-A, another supporting evidence for collisionally triggered SF in the region given
the tight relation between young clusters and CCC (Y. Fukui et al. 2021). Finally, although in SQ-A the CCC mainly
occurs between HI dominated clouds (i.e. HI-HI collision), HI-GMC and GMC-GMC collisions may also contribute to
the SF enhancement albeit with relatively low significance given the low M mol -to-M HI ratio.


5.2. _Collision_ _of_ _Cloud_ _with_ _Diffuse_ _Gas_ _and_ _Suppression_ _of_ _SFR_


A major challenge for the collisional scenario of the SQ-A starburst is the severely suppressed SF activity in the
large-scale shock region (M. E. Cluver et al. 2010; P. Guillard et al. 2012). Why does a high-speed collision in the
large-scale shock region cause an SF suppression while in SQ-A a starburst?

14 C.K. Xu et al.


There is a stark difference between the collisions in the two regions: in SQ-A both the IGrM and the intruderassociated components have large amount of cold gas. On the other hand, in the shock region, only the CO of
molecular gas of the intruder-associated component (i.e. the 6000 component) is significantly detected (U. Lisenfeld
et al. 2002; P. Guillard et al. 2012; B. H. C. Emonts et al. 2025) whereas no significant CO or HI detection is found
for the IGrM-associated component. J. W. Sulentic et al. (2001) suggested that the reason for the lack of cold IGrM
gas in the shock region is because it has been converted to hot X-ray gas and warm ionized gas after the collision.
This interpretation is unlikely to be true because, as shown in simulations (e.g. R. Maeda et al. 2021), the cooling
time in cloud-cloud collisions is so short that the post-shock gas becomes cold and neutral again soon after collision
(on a timescale of _<_ 10 [6] yrs). It is more likely that the pre-shock IGrM in the shock region is predominantly in the
diffuse warm neutral medium (WNM) or/and the warm ionized medium (WIM; J. Iglesias-P´aramo et al. 2012; M.
Rodr´ıguez-Baras et al. 2014; M. I. Arnaudova et al. 2024). The WNM gas is too diffuse to be detected by VLA but
can be picked-up by sensitive single-dish HI observations. Indeed recent FAST observations of SQ have found more
HI gas in the 6600 components, most likely in the diffuse IGrM (C. K. Xu et al. 2022; C. Cheng et al. 2023). If indeed
the pre-shock IGrM gas in the shock region is diffuse and of low density, the high speed collision between this gas
and the diffuse gas associated with the intruder can produce two blast wave shocks, one propagates in the IGrM and
the other in the system associated with the intruder. The shock ridge shown in the X-ray and the radio continuum
is presumably associated with the post-shock gas between these two shock fronts. From the X-ray data G. Trinchieri
et al. (2003) found a pre-shock gas density on the order of _∼_ 10 _[−]_ [2] cm _[−]_ [3] . Therefore, the process affecting the clouds
in the shock region may be better analyzed using models for interaction of blast wave shock and interstellar clouds
(C. F. McKee & L. L. Kowie 1975; R. Klein et al. 1994; P. Guillard et al. 2009) instead of CCC models. One of
the key findings of R. Klein et al. (1994) is that strong vorticity can be generated at the cloud-intercloud boundary
and in the tail behind the cloud, both by the initial passage of the blast wave shock and by the subsequent flow of
post-shock inter-cloud gas passing-by the cloud. We argue that it is the vortices so generated that suppress the SF in
molecular clouds in the shock region. The vortices can contribute significantly to the solenoidal turbulence which acts
against cloud contraction, and may eventually destroy the cloud (R. Klein et al. 1994). Both theoretical simulations
and observations in literature have shown that, while the compressive turbulence can enhance SFR, the solenoidal
turbulence can suppress SFR (C. Federrath & R. S. Klessen 2012; J. H. Orkisz et al. 2017; R. Rani et al. 2022; M. A.
Petkova et al. 2023).
Similar to clouds in the shock region, clumps of the 6900 component in SQ-A have severely suppressed SF activity.
It is possible that these clumps have avoided cloud-cloud collision, given the fact that they have not been decelerated
significantly. If these clumps are also undergoing interactions with blast wave shocks due to collisions between diffuse
media in SQ-A, the above scenario proposed for clouds in the shock region can apply and explain why the SFR is
suppressed in 6900 component. The significant correlation between t dep and the S parameter, which indicates an
important role of rotation in suppressing SFR, supports this hypothesis. The weak X-ray emission in SQ-A may not
be used as evidence against such an analogy because the X-ray may be affected by absorption (E. O’Sullivan et al.
2009). It is interesting to note that there is a faint stripe of diffuse X-ray emission extending to the east of SQ-A
(E. O’Sullivan et al. 2009), which can also be seen in the VLA 1.4 GHz radio continuum map (C. K. Xu et al. 2003)
and faintly visible in the H _α_ map (Fig. 1). This feature may be shock-excited, providing further evidence for shocks
triggered by the collision between diffuse media in the region around SQ-A.
Unlike the 6000 component which is linked to the intruder galaxy NGC 7318b by a long arm or a partial ring
(B. H. C. Emonts et al. 2025), the origin of the 6900 component in SQ-A is still unknown. It might be related to the
large CO emission region in the north-east of NGC 7319 nucleus which has a system velocity of _∼_ 6900 km s _[−]_ [1] (M. S.
Yun et al. 1997; Y. Gao & C. Xu 2000; B. H. C. Emonts et al. 2025), though no clear link has been detected between
that region and SQ-A in any band. Future high angular resolution and high sensitivity HI observations covering the
velocity range beyond 6800 km s _[−]_ [1] will help resolving this issue.
Our interpretation for the diversified t dep in colliding systems in SQ can have far-reaching inference to theories of
interactinon-induced SF in galaxy mergers, particularly those in early merging stages (e.g. optical-NIR selected pairs).
Given the nearly universal detections of young massive star clusters (YMCs) in merging galaxies (B. C. Whitmore
& F. Schweizer 1995; A. Adamo et al. 2020) and the tight relation between YMCs and collision triggered SF (B. G.
Elmegreen 1998; Y. Fukui et al. 2021), the CCC mechanism must play an important role in the SF activity of galaxy
mergers. Our results for SQ-A indicate that effects of collisions are very complex, can cause either SF enhancement
or SF suppresion depending on the density contrast between the gas systems involved in the collision. In studies of a

SQ-A: A Collision Triggered Starburst 15


sample of K-band selected close major-merger pairs (KPAIR), it has been found that the SF galaxies in spiral-spiral
pairs have strong SF enhancement while those in spiral-elliptical mixed pairs have not (C. K. Xu et al. 2010; C. Cao
et al. 2016; U. Lisenfeld et al. 2019). Simulations predict enhancement of compressive turbulence in early mergers
(F. Renaud et al. 2014) which triggers formartion of large amount of dense cores and results in widely spread SF
enhancement in the disks, consistent with the observations for extended SF enhancement in disks in spiral-spiral pairs
(D. Iono et al. 2005). Why does this mechanism fail to work for SF galaxies in mixed pairs? C. K. Xu et al. (2021)
found that galaxies in mixed pairs are more likely involved in high-inclination orbit and high speed collisions, which
may trigger density waves (as shown by ring-like structures) in the disk. It is plausible that the shocks associated with
density waves may act similarly as the blast wave shock in the model of R. Klein et al. (1994) and suppress the SF of
the gas clouds. As an example, the SFR/M mol (the inverse of t dep ) of the spiral galaxy NGC 2936 in the mixed pair
Arp 142, which has gone through a high-speed and high-inclination collision recently, is significantly lower than the
nominal value for SF regions (C. K. Xu et al. 2021).


5.3. _Uncertainties_ _of_ _CO_ _Conversion_ _Factor_ _and_ r 21


In this paper, we adopt a CO conversion factor _α_ CO10 = 1 _._ 0 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] . This is a factor of 3.2 or 4.3
lower than the Galactic value, depending on whether the contribution of the heavy elements is included (A. D. Bolatto
et al. 2013). Starburst galaxies often have low CO conversion factors ( _α_ CO10 _<_ 1; D. Downes & P. M. Solomon
1998). There is also evidence for molecular gas systems involved in high speed collisions to have low _α_ CO10 . For gas
in the bridge between Taffy Galaxies, J. Braine et al. (2003) and M. Zhu et al. (2007) found a _α_ CO10 4 – 10 times
lower than the Galactic value. Given that SQ-A is also involved in a high speed collision with a collision velocity
comparable to that between Taffy Galaxies, the low _α_ CO10 is justified. On the other hand, the slightly sub-solar
metallicity of SQ-A (Z _∼_ 0 _._ 5Z _⊙_, S. Duarte Puertas et al. 2021) may hint a higher _α_ CO10 (A. D. Bolatto et al. 2013).
Also, the average virial parameter of the SQ-A clumps is _α_ _vir_ _∼_ 3 (see right panel of Fig. 6), indicating that the
virial mass is about 3 times higher than the mass estimated using the adopted _α_ CO10 . However in colliding systems
and starbursts, the virial equilibrium may be broken and virial mass may not be a good estimator of the true mass.
Constraining the M mol using the local thermodynamic equilibrium (LTE) models, G. Krahm et al. (2024) found that
the conversion factor in the Antennae overlap is consistent with X CO = 0 _._ 5 _×_ 10 [20] cm _[−]_ [2] (K km s _[−]_ [1] ) _[−]_ [1], corresponding
to _α_ CO10 = 1 _._ 075 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] (A. D. Bolatto et al. 2013), and that the clouds in the Antennae overlap are
highly super-virial with a mean _α_ _vir_ = 13 _._ 77 _±_ 0 _._ 37. Actually, these authors found that molecular clouds are in general
super-virial in starburst galaxies. In summary, the CO conversion factor in SQ-A is highly uncertain. Future works
involving CO [13] observations and modelings, e.g. using the LTE models or the large velocity gradient (LVG) models
(A. D. Bolatto et al. 2013), may help to resolve this issue.
Also, the adopted CO(2-1) to CO(1-0) luminosity ratio r 21 = 0 _._ 34 is quite uncertain, too, because SQ-A is near the
edge of the primary beam of the CARMA CO(1-0) observations based on which the r 21 value is estimated. In addition,
the 6000 component (associated with the intruder) may have a slightly different value (r 21 = 0 _._ 29; B. H. C. Emonts
et al. 2025).
The uncertainties of _α_ CO10 and r 21 affect the estimate of M mol from the ALMA CO(2-1) data through a combined
factor _α_ CO10 _×_ r 21 . Nevertheless our main conclusions, which are primarily based on gas distributions and correlations
(and lack of them) between various parameters in clumps, are not significantly affected by these uncertainties.


6. CONCLUSIONS


In this paper we aim to achieve two science goals: (1) proving the validity of the hypothesis that the starburst
SQ-A in the IGrM of Stephan’s Quintet (SQ) is triggered by a high-speed collision ( _∼_ 900 km s _[−]_ [1] ) between two
gas systems, one associated with the IGrM (v _∼_ 6900 km s _[−]_ [1] ) and another with the intruder galaxy NGC 7318b
(v _∼_ 6000 km s _[−]_ [1] ); (2) solving the puzzle of why gas clouds in SQ-A and in the large-scale shock region of SQ, which
are both involved in the same high-speed collision between the IGrM and the intruder, can have dramatically different
SFRs. To achieve these goals, we exploit the following data sets: (1) CO(2-1) datacubes with angular resolutions in the
range of 0 _._ 2 _[′′]_ _−_ 7 _._ 0 _[′′]_ obtained using ALMA in various configurations (with adopted distance of 94 Mpc, 1” corresponds
to 0.45 kpc); (2) an HI datacube of angular resolution of 6 _._ 6 _[′′]_ _×_ 7 _._ 9 _[′′]_ obtained using the VLA B, C & D arrays; and
(3) a JWST MIRI image in the 15 _µm_ band. We reach the following conclusions:


**1:** The CO(2-1) data show clearly three kinematic systems in SQ-A that correspond to the 6000, 6600 and 6900
components in the literature (G. S. Shostak et al. 1984; B. A. Williams et al. 2002; C. Cheng et al. 2023), with

16 C.K. Xu et al.


systematic velocities of 6010 _±_ 32, 6719 _±_ 41 and 6930 _±_ 33 km s _[−]_ [1], respectively. As shown in the CO maps
covering the entire SQ (B. H. C. Emonts et al. 2025), both the 6600 and 6900 components in SQ-A are most
likely associated with the IGrM while the 6000 component with the intruder galaxy NGC 7318b. The 6900
component has the highest molecular gas mass (M mol = 1 _._ 4 _±_ 0 _._ 7 10 [8] M _⊙_ ) which is 1.9 and 1.5 times of those
of the 6000 and 6600 components, respectively. The 6900 and 6000 components do not overlap with each other
spatially but are bridged by the 6600 component.


**2:** The 6000 and 6600 components are also detected in new HI data with velocities of 6020 _±_ 31 and 6645 _±_ 63 km s _[−]_ [1],
respectively, slightly different from those of the corresponding components in the CO. The 6900 component is
not observed in the HI because it is outside the frequency coverage of the VLA observations. Both the 6000
and 6600 components show rather high M HI -to-M mol ratios ( _>_ 10). A comparison with an unpublished MeerKat
HI observation indicates a lower M HI -to-M mol ratio for the 6900 component ( _∼_ 4). In the HI map the 6600
component fits well into a gap in the more extended 6000 component, albeit with a displacement of _∼_ 5 kpc.


**3:** The three kinematic components in SQ-A have very different SF activities. The 6600 component has the highest
SFR (0 _._ 98 M _⊙_ yr _[−]_ [1] ), dominated by the starburst (v _∼_ 6680 km s _[−]_ [1] in H _α_ ). The 6000 component has also a
sizable SFR though about a factor of 3 lower than that of 6600 component. The 6900 component has very little
SF, with an SFR more than an order of magnitude lower than that of the 6600 component.


**4:** In order to probe at the cloud level the physical conditions that lead to the conspicuous difference in SFRs of
different kinematic components, we carry out an analysis of CO clumps of sizes of _∼_ 100 – 200 pc, utilizing the
high resolution ALMA data (beam = 0 _._ 38 _[′′]_ _×_ 0 _._ 23 _[′′]_ ) and the clump-finding algorithm “Fellwalker” (D. Berry
2015). The Larson relation between the effective size (R e ) and the velocity dispersion ( _σ_ v ) of these clumps are
similar to that of the large Galactic GMCs. No significant systematic difference is found among the different
kinematic components in various physical parameters including R e, _σ_ v, the virial parameter _α_ vir and the external
pressure P e .


**5:** Correlation analyses of the clumps find no dependence of the SFR surface density Σ SFR and the depletion time of
molecular gas t dep on molecular gas surface density Σ mol nor on the virial parameter _α_ vir, suggesting that the
SFR enhancement (or suppression) is not due to any mechanism associated with the self-gravity. On the other
hand, a marginally significant correlation is found between t dep and _σ_ v, suggesting that the gas motion may play
a role in the SF activity of the clumps. Additional correlation analyses find putatively significant correlation
between t dep and the S parameter (a measure of projected angular momentum) and anti-correlation between
t dep and the C parameter (a measure of nonrotational-to-rotational energy ratio), suggesting that SFR may be
suppressed by the centrifugal force in clumps with strong rotation and enhanced by compressive processes in
clumps with high nonrotational-to-rotational energy ratios. No correlation is found between t dep and the radial
velocity gradient parameter G v, suggesting the share motion may not affect the SFR significantly.


**6:** In analog to the SF enhancement in the 30 Doradus plus southern ridge of the LMC (K. Tsuge et al. 2024), the
following scenario for the triggering of the SQ-A starburst is supported by our results: A high-speed collision
(v coll _∼_ _>_ 900 km s _−_ 1 ) is going on between the IGrM (pre-collision radial velocity _∼_ 6900 km s _−_ 1 ) and a gas

system associated with the intruder galaxy NGC 7319 (pre-collision radial velocity _∼_ 6000 km s _[−]_ [1] ). Only a part
of 6900 component and a part of 6000 component are involved in the collision. During the collision the 6900
gas, which is likely to be denser and more compact than the 6000 gas, is decelerated and compressed, and this
decelerated and compressed gas becomes the 6600 component in which the SQ-A starburst is triggered. At the
same time, the 6000 gas involved in the collision is swept into the 6600 component and/or dispersed, leaving a
gap in the 6000 map at the place where the 6600 component crashes through. The _∼_ 5 kpc displacement shown
in Fig. 4, which is likely the projection of a 3-dimensional movement between the two components, suggests an
age of the collision of a few 10 [7] years (assuming a transverse relative velocity of a few 100 km s _[−]_ [1] between the
colliding systems), consistent with the estimated time scale for the age of the encounter between the intruder
and SQ (J. W. Sulentic et al. 2001). According to simulations of R. Maeda et al. (2021, 2024), the high Σ SFR
and short t dep of clumps in the 6600 component (dominated by HI gas with a M HI -to-M mol ratio _>_ 10) are due
to strong compression in the post-collision gas which triggers the formation of a large amount of star-forming
dense cores (n _>_ 10 [4] cm _[−]_ [3] ).

SQ-A: A Collision Triggered Starburst 17


**7:** Different from the clumps of the 6600 component in SQ-A, the molecular clouds in the large scale shock region and
in the 6900 component in SQ-A show severely suppressed SF activity. These clouds are likely not involved in
any cloud-cloud collision but in more complex collisions involving dense clouds and low density diffuse media. In
this scenario, blast wave shocks (as shown by the radio and X-ray ridge) are triggered by the collision between
diffuse media associated with IGrM and the intruder, respectively. As predicted by the model for interaction of
blast wave shock and dense clouds (R. Klein et al. 1994), strong vorticity at the cloud-intercloud boundary and
in the tail behind a dense cloud can be generated both by the initial passage of the blast wave shock and by the
subsequent flow of post-shock inter-cloud diffuse gas passing-by the cloud. It is the vortices so generated that
suppress the SF in the low SF activity clouds.


ACKNOWLEDGMENTS


We thank K. Rajpurohit for providing useful information from her MeerKAT observations before the publication. This
work is sponsored (in part) by the Chinese Academy of Sciences (CAS) through a grant to the CAS South America
Center for Astronomy. C.C. acknowledges NSFC grant No. 11803044 and 12173045. This work is supported by the
China Manned Space Program with grant no. CMS-CSST-2025-A07. UL acknowledges support by the research grants
PID2020-114414GB-I00 and PID2023-150178NB-I00, financed by MCIU/AEI/10.13039/501100011033 and from the
Junta de Andaluc´ıa (Spain) grant FQM108. P.A. and S.G. thank the Canadian Space Agency and the Natural Science
and Engineering Council for support.
This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00241.S and
ADS/JAO.ALMA#2023.1.00177.S. ALMA is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea),
in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under
cooperative agreement by Associated Universities, Inc.
This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were
obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated
by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST.
Some of the data presented in this paper were obtained from the Mikulski Archive for Space Telescopes
(MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via
[https://doi.org/10.17909/9w9c-f533.](https://doi.org/10.17909/9w9c-f533) STScI is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS5–26555. Support to MAST for these data is provided by the NASA Office of
Space Science via grant NAG5–7584 and by other grants and contracts.
(Some of) The data products presented herein were retrieved from the Dawn JWST Archive (DJA). DJA is an
initiative of the Cosmic Dawn Center (DAWN), which is funded by the Danish National Research Foundation under
grant DNRF140.


REFERENCES



Abe, D., Inoue, T., Inutsuka, S., & Matsumoto, T. 2021

ApJ, 916, 83

Adamo, A., Hollyhead, K., Messa, M., et al. 2020, MNRAS,

499, 3267, doi: [10.1093/mnras/staa2380](http://doi.org/10.1093/mnras/staa2380)

Alatalo, K., Appleton, P. N., Lisenfeld, U., et al. 2014, ApJ,

795, 159, doi: [10.1088/0004-637X/795/2/159](http://doi.org/10.1088/0004-637X/795/2/159)

Allen, R. J., & Hartsuiker, J. W. 1972 Nature, 239, 324

Appleton, P. N., Guillard, P., Boulanger, F., et al. 2013

ApJ, 777, 66

Appleton, P. N., Guillard, P., Emonts, B., et al. 2023 ApJ,

951, 104



Appleton, P. N., Xu, C. K., Reach, W., et al. 2006 ApJL,

639, L51


Arnaudova, M. I., Das, S., Smith, D. J. B., et al. 2024,

MNRAS, 535, 2269, doi: [10.1093/mnras/stae2235](http://doi.org/10.1093/mnras/stae2235)


Arp, H. 1995 ApJ, 183, 411


Berry, D. 2015 A. & C., 10, 22


Berry, D. S., Reinhold, K., Jenness, T., & Economou, F.

2007, in Astronomical Society of the Pacific Conference

Series, Vol. 376, Astronomical Data Analysis Software

and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell,

425

18 C.K. Xu et al.



Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A,
51, 207, doi: [10.1146/annurev-astro-082812-140944](http://doi.org/10.1146/annurev-astro-082812-140944)

Braine, J., Davoust, E., Zhu, M., et al. 2003 A&A, 408, L13

Braine, J., Hughes, A., Rosolowsky, E., et al. 2020 A&A,

663, A17

Braine, J., Rosolowsky, E., Gratier, P., et al. 2018 A&A,

612, A51

Briggs, D. S. 1995, PhD thesis, New Mexico Institute of

Mining and Technology

Cao, C., Xu, C. K., Domingue, D., et al. 2016, ApJS, 222,
16, doi: [10.3847/0067-0049/222/2/16](http://doi.org/10.3847/0067-0049/222/2/16)

CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP,
134, 114501, doi: [10.1088/1538-3873/ac9642](http://doi.org/10.1088/1538-3873/ac9642)

Cheng, C., Xu, C. K., Appleton, P. N., et al. 2023 ApJ,

954, 74

Cluver, M. E., Appleton, P. N., Boulanger, F., et al. 2010

ApJ, 710, 248

Currie, M. J., Berry, D. S., Jenness, T., et al. 2014, in

Astronomical Society of the Pacific Conference Series,

Vol. 485, Astronomical Data Analysis Software and

Systems XXIII, ed. N. Manset & P. Forshay, 391

Dicken, D., Mar´ın, M. G., Shivaei, I., et al. 2024, A&A,

689, A5, doi: [10.1051/0004-6361/202449451](http://doi.org/10.1051/0004-6361/202449451)

Donovan Meyer, D., Koda, J., Momose, R., et al. 2013 ApJ,

772, 107

Downes, D., & Solomon, P. M. 1998 ApJ, 507, 615

Duarte Puertas, S., Iglesias-Paramo, J., Vilchez, J. M.,

et al. 2019 A&A, 629, 102

Duarte Puertas, S., Vilchez, J. M., Iglesias-Paramo, J.,

et al. 2021 A&A, 645, 57

Duc, P.-A., Cuillandre, J.-C., & Renaud, F. 2018 MNRAS,

475, L40

Elmegreen, B. G. 1989 ApJ, 338, 178

Elmegreen, B. G. 1998, in Astronomical Society of the

Pacific Conference Series, Vol. 148, Origins, ed. C. E.

Woodward, J. M. Shull, & H. A. Thronson, Jr., 150,

doi: [10.48550/arXiv.astro-ph/9712352](http://doi.org/10.48550/arXiv.astro-ph/9712352)

Emonts, B. H. C., Appleton, P. N., Lisenfeld, U., et al. 2025

ApJ, 978, 111

Federrath, C., & Klessen, R. S. 2012 ApJ, 761, 156

Fedotov, K., Gallagher, S. C., Konstantopoulos, I. S., et al.

2011 AJ, 142, 42

Fukui, Y., Habe, A., Inoue, T., et al. 2021 PASJ, 73, S1

Fukui, Y., Torii, K., Hattori, Y., et al. 2018 ApJ, 859, 166

Fukui, Y., Tsuge, K., Sano, H., et al. 2017 PASJ, 69, 5

Gallagher, S. C., Charlton, J. C., Hunsberger, S. D., et al.

2001 AJ, 122, 163

Gao, Y., & Xu, C. 2000 ApJL, 542, L83

Guillard, P., Appleton, P. N., Boulanger, F., et al. 2022

ApJ, 925, 63



Guillard, P., Boulanger, F., Forets, G. P. D., et al. 2009

A&A, 502, 515

Guillard, P., Boulanger, F., Pineau des Forˆets, G., et al.

2012, ApJ, 749, 158, doi: [10.1088/0004-637X/749/2/158](http://doi.org/10.1088/0004-637X/749/2/158)

Habe, A., & Ohta, K. 1992 PASJ, 44, 203

Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009

ApJ, 699, 1092

Hibbard, J. E., van der Hulst, J. M., Barnes, J. E., & Rich,

R. M. 2001 AJ, 122, 2969

Hickson, P. 1982, ApJ, 255, 382, doi: [10.1086/159838](http://doi.org/10.1086/159838)

Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023,

PASP, 135, 074501, doi: [10.1088/1538-3873/ace216](http://doi.org/10.1088/1538-3873/ace216)

Hwang, J.-S., Struck, C., Renaud, F., & Appleton, P. N.

2012 MNRAS, 419, 1780

Iglesias-P´aramo, J., L´opez-Mart´ın, L., V´ılchez, J. M.,

Petropoulou, V., & Sulentic, J. W. 2012, A&A, 539,

A127, doi: [10.1051/0004-6361/201118055](http://doi.org/10.1051/0004-6361/201118055)

Iglesias-Paramo, J., & Vilchez, J. M. 2001 ApJ, 550, 204

Inoue, T., & Fukui, Y. 2013 ApJL, 774, 3

Iono, D., Yun, M. S., & Ho, P. T. P. 2005, ApJS, 158, 1,

doi: [10.1086/429093](http://doi.org/10.1086/429093)

Johnson, K. E., Hibbard, J. E., Gallagher, S. C., et al.

2007, AJ, 134, 1522, doi: [10.1086/520921](http://doi.org/10.1086/520921)

Johnson, K. E., Leroy, A. K., Indebetouw, R., et al. 2015

ApJ, 697, 1971

Kennicutt, R. C. 1998 ARA&A, 36, 189

Kessler, M. F., et al. 1996 A&A, 315, L27

Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2022

MNRAS, 516, 3006–3028

Klein, R., McKee, C. F., & Colella, P. 1994 ApJ, 420, 213

Krahm, G., Finn, M. K., Indebetouw, R., et al. 2024 ApJ,

964, 166

Kruijssen, J. M. D., Schruba, A., Hygate, A. P. S., et al.

2018 MNRAS, 479, 1866–1952

Krumholz, M. R. 2014 Phys. Rep., 539, 49

Leroy, A. K., Sun, J., Meidt, S., et al. 2025, arXiv e-prints,

arXiv:2502.04481, doi: [10.48550/arXiv.2502.04481](http://doi.org/10.48550/arXiv.2502.04481)

Li, C., Wang, H. C., Wu, Y. W., et al. 2020 RAA, 20, 031

Libralato, M., Argyriou, I., Dicken, D., et al. 2024, PASP,

136, 034502, doi: [10.1088/1538-3873/ad2551](http://doi.org/10.1088/1538-3873/ad2551)

Lisenfeld, U., Braine, J., Duc, P.-A., et al. 2002 A&A, 394,

823

Lisenfeld, U., Xu, C. K., Gao, Y., et al. 2019, A&A, 627,

A107, doi: [10.1051/0004-6361/201935536](http://doi.org/10.1051/0004-6361/201935536)

Maeda, R., Inoue, T., & Fukui, Y. 2021 ApJ, 908, 2

Maeda, R., Inoue, T., Omukai, K., et al. 2024 ApJ, 971, 62

McKee, C. F., & Kowie, L. L. 1975 ApJ, 195, 715

Mendes de Oliveira, C., Plana, H., Amram, P., et al. 2001

AJ, 121, 2524

SQ-A: A Collision Triggered Starburst 19



Moles, M., Marquez, I., & Sulentic, J. W. 1998 A&A, 334,

473

Moles, M., Sulentic, J. W., & Marquez, I. 1997 ApJL, 485,

69

Orkisz, J. H., Jerome, P., Gerin, M., et al. 2017 A&A, 599,

99

O’Sullivan, E., Giacintucci, S., Vrtilek, J. M., et al. 2009

ApJ, 701, 1560

Petkova, M. A., Kruijssen, J. M. D., Henshaw, J. D., et al.

2023 MNRAS, 525, 962

Pontoppidan, K. M., Barrientes, J., Blome, C., et al. 2022

ApJL, 936, L14

Rani, R., Moore, T. J. T., Eden, D. J., & Rigby, A. J. 2022

MNRAS, 515, 271

Renaud, F., Appleton, P. N., & Xu, C. K. 2010 ApJ, 742, 80

Renaud, F., Bournaud, F., Daddi, E., et al. 2019 A&A, 621,

A104

Renaud, F., Bournaud, F., Kraljic, K., & Duc, P. A. 2014

MNRAS, 442, L33

Rodr´ıguez-Baras, M., Rosales-Ortega, F. F., D´ıaz, A. I.,

S´anchez, S. F., & Pasquali, A. 2014, MNRAS, 442, 495,

doi: [10.1093/mnras/stu851](http://doi.org/10.1093/mnras/stu851)

Sanders, D. B., & Mirabel, I. F. 1996 ARA&A, 34, 749

Shostak, G. S., Sullivan, W. T., & Allen, R. J. 1984 A&A,

139, 15

Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987

ApJ, 319, 730

Sulentic, J. W., Rosado, M., Dultzin-Hacyan, D., et al.

2001 AJ, 122, 2993

Takahira, K., Tasker, E. J., & Habe, A. 2014 ApJ, 792, 63

Trinchieri, G., Sulentic, J., Breitschwerdt, D., et al. 2003

A&A, 401, 173



Tsuge, K., Fukui, Y., Tachihara, K., et al. 2021a PASJ, 73,

S35

Tsuge, K., Sano, H., Tachihara, K., et al. 2024 PASJ, 76,

589

Tsuge, K., Tachihara, K., Fukui, Y., et al. 2021b PASJ, 73,

417

Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023,

ApJ, 947, 20, doi: [10.3847/1538-4357/acbefa](http://doi.org/10.3847/1538-4357/acbefa)

Verdes-Montenegro, L., Yun, M. S., Williams, B. A., et al.

2001 A&A, 377, 812

Whitmore, B. C., & Schweizer, F. 1995 AJ, 109, 960

Williams, B. A., Yun, M. S., & Verdes-Montenegro, L. 2002

AJ, 123, 2471

Wilson, C. D., Scoville, N., Madden, S. C., &

Charmandaris, V. 2000 ApJ, 542, 12

Xu, C., Gao, Y., Mazzarella, J., et al. 2000, ApJ, 541, 644,

doi: [10.1086/309483](http://doi.org/10.1086/309483)


Xu, C., Sulentic, J. W., & Tuffs, R. 1999, ApJ, 512, 178,

doi: [10.1086/306771](http://doi.org/10.1086/306771)

Xu, C. K., Cheng, C., Appleton, P. N., et al. 2022 Nature,

610, 461

Xu, C. K., Domingue, D., Cheng, Y., et al. 2010, ApJ, 713,

330

Xu, C. K., Iglesias-Paramo, J., Burgarella, D., et al. 2005

ApJL, 619, L95

Xu, C. K., Lisenfeld, U., Gao, Y., & Renaud, F. 2021, ApJ,

918, 55, doi: [10.3847/1538-4357/ac0f77](http://doi.org/10.3847/1538-4357/ac0f77)

Xu, C. K., Lu, N., Condon, J. J., et al. 2003 ApJ, 595, 665

Yun, M. S., Verdes-Montenegro, L., del Olmo, A., & Perea,

J. 1997 ApJL, 475, 21

Zhu, M., Gao, Y., Seaquist, E. R., et al. 2007 AJ, 134, 118

20 C.K. Xu et al.


APPENDIX


A. CLUMPS IN FIELD 4


We identified clumps in the CO(2-1) datacube of the ”Field 4” observation of P. N. Appleton et al. (2023) using
the FellWalker clump-finding algorithm via the PyCupid [22], which is a Python wrapper for the Starlink CUPID
package (D. S. Berry et al. 2007; M. J. Currie et al. 2014). The detection parameters were configured as follows:
a detection threshold of 1- _σ_ above the background level, a minimum clump peak height of 2- _σ_ (minheight = 2), a
separation threshold of 1- _σ_ between adjacent clumps (mindip = 1), a maximum step of 8 pixels to search for a higher
neighboring pixel value (maxjump = 8), and a minimum clump size (this size is measured using the sum of all pixels
in the clump without the flux weight) of twice the synthesized beam size in pixel (minpix = 2 Beam FWHM). These
settings ensure detection of resolved, statistically significant structures while mitigating false positives in crowded
molecular environments. Clumps composited by two or more sub-clumps of spatially separated with gaps _≥_ 5 pixels
(1 pixel= 0 _._ 05 _[′′]_ ) are excluded. In total 36 clumps are identified in the field. Table A1 lists various parameters of these
clumps. The parameters for individual clumps are defined as follows:
The position (i.e. R.A. & Dec.) of each clump is specified by that of its mass center whose x and y coordinates (in
the image frame) are:
x = Σ i f i x i _/_ Σ i f i (A1)


y = Σ i f i y i _/_ Σ i f i _,_ (A2)


where x i, _y_ _i_ and f i are the coordinates and the signal of the i th pixel, respectively, and the summation goes through
all pixels in the clump. The parameter r SQA is the distance from a clump to the Field 4 center (at RA = 338 _._ 995333,
Dec = +33 _._ 98074) which is pointed to the SQ-A starburst with a primary beam of 22 _[′′]_ . Two clumps (#35 and #36)
have r SQA _>_ 11 _[′′]_ and therefore are outside the primary beam. They should be treated with caution. The redshift
velocity v and the velocity dispersion _σ_ v of a given clump are estimated as follows:


v = Σ i f i v i _/_ Σ i f i _,_ (A3)


_σ_ v = �Σ i f i (v i _−_ v) [2] _/_ Σ i f i _._ (A4)


The effective radius of a clump is defined as
R e = ~~�~~ A e _/π_ (A5)


where A e is the signal weighted area of the clump in pc [2] :



A e = [a] [p][ix] [Σ] ~~_√_~~ [i] [f] 2 [i] _πσ_ _[/]_ [f] [p] v [eak] _[δ]_ [v]



(A6)



where a pix is the pixel area in pc [2], f peak the peak signal, and _δ_ v the velocity bin width. Here we assume that in the
velocity dimension signals follow a Gaussian distribution characterized by _σ_ = _σ_ v . The M mol is estimated from the
integrated flux f CO21 assuming a CO conversion factor _α_ CO10 = 1 _._ 0 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] . and a CO(2-1) to CO(1-0)
luminosity ratio r 21 = L _[′]_ CO(2 _−_ 1) _[/]_ [L] _[′]_ CO(1 _−_ 0) [= 0] _[.]_ [34 (][B. H. C. Emonts et al. 2025][).] [The surface density Σ] [mol] [= M] [mol] _[/]_ [A] [e] [.]

We define a 2-D vector _[⃗]_ S = S x _[⃗]_ i + S y _[⃗]_ j to represent the contribution of the radial velocity to the projected specific
angular momentum (i.e. the angular momentum per unit mass projected into the plane perpendicular to the line of
sight). Here S x and S y are the x- and y- components and _[⃗]_ i and _[⃗]_ j are unit vectors along the x and y axes, respectively
(the cube is north-up, therefore the x axis directs toward west and y axis toward north). The absolute value of _[⃗]_ S, S,
is a scalar parameter in the units of km s _[−]_ [1] pc:

S = �S [2] x + S [2] y (A7)


where



S x = _−_ d pix Σ i f i (v i _−_ v)(y i _−_ y)

Σ i f i



(A8)



22 [https://github.com/msanchezc/pycupid](https://github.com/msanchezc/pycupid)

SQ-A: A Collision Triggered Starburst 21


Σ i f i (v i _−_ v)(x i _−_ x)
S y = d pix Σ i f i _,_ (A9)


where d pix is the pixel size in pc. We also define a C parameter as follows:


C = (E _−_ E S ) _/_ E S (A10)


where E is a measure of the specific kinematic energy per unit mass:


E = _[σ]_ v [2] (A11)
2


and E s is a measure of the specific rotational energy:


E S = [S] [2] (A12)

2J


where J is a measure of the specific rotational inertia:


pix [Σ] [i] [f] [i] [((x] [i] _[ −]_ [x)] [2] [ + (y] [i] _[ −]_ [y)] [2] [)]
J = [d] [2] _._ (A13)

Σ i f i


By definition E _≥_ E S, therefore C _≥_ 0. Due to projection effects and beam smearing, E and E S are not rigorous
representations of the total kinematic and rotational energies, respectively. Nevertheless C can be used as an indicator
of the nonrotational-to-rotational energy ratio in a clump. When C _<_ 1 the kinematics in the clump is likely dominated
by rotation and when C _>>_ 1 it is dominated by non-rotational motions.
In order to study the effects of shear motion, we define a 2-D vector G _[⃗]_ v = G v _,_ x _[⃗]_ i + G v _,_ y _[⃗]_ j to represent the gradient of
the radial velocity. Its absolute value, G v, is a scalar parameter in the units of km s _[−]_ [1] pc _[−]_ [1] :


G v = ~~�~~ G [2] v _,_ x + G [2] v _,_ y (A14)


where



G v _,_ x = [Σ] [i] [w] [i] [(][v] d [i] _[ −]_ pix [v] Σ [)] i _[/]_ w [(] i [x] [i] _[ −]_ [x][)]



(A15)



G v _,_ y = [Σ] [i] [u] [i] [(][v] d [i] _[ −]_ pix [v] Σ [)] i _[/]_ u [(y] i [i] _[ −]_ [y)] _._ (A16)


In order to avoid run-away errors due to pixels with coordinates too close to those of the mass center of the clump,
we choose the following weights (i.e. w i and u i ) in above summations:


w i = f i (when(x i _−_ x) _>_ 0 _._ 5)


= 0 (when(x i _−_ x) _≤_ 0 _._ 5) (A17)


u i = f i (when(y i _−_ y) _>_ 0 _._ 5)


= 0 (when(y i _−_ y) _≤_ 0 _._ 5) _._ (A18)


The external pressure P e is calculated as follows (B. G. Elmegreen 1989):



P e = [3ΓM] 4 _π_ [mol] R [3] e _[σ]_ v [2]



(A19)



where Γ is the ratio between the density at the edge of a clump and the average density. Following K. E. Johnson
et al. (2015), we assume Γ = 0 _._ 5.
The virial parameter _α_ vir is defined by:

_α_ vir = [5] _[σ]_ v [2] [R] [e] (A20)
M mol G

22 C.K. Xu et al.


where G = 4 _._ 3 _×_ 10 _[−]_ [3] is the gravitational constant in the units of pc (km s _[−]_ [1] ) [2] M _[−]_ _⊙_ [1] [.]
The SFR surface density Σ SFR is estimated using the JWST 15 _µm_ data. Two operational issues make the estimation
of Σ SFR from integrated 15 _µm_ flux over the actual sky area of a clump unfavorable: (1) many clumps are smaller than
the 15 _µm_ beam; (2) on the 2-D image of the 15 _µm_ emission many clumps are blinded with each other. Therefore we
adopt a simpler approach of measuring the peak 15 _µm_ flux of each clump using a fixed aperture of _r_ = 0 _._ 25 _[′′]_ which
is approximately the resolution of the JWST 15 _µm_ image (Section 2.3). The f 15 _µ_ m -to-SFR conversion is calibrated
using the total 15 _µm_ flux in the SQ-A region, which is 6.85 mJy, and the total SFR = 1 _._ 42 M _⊙_ yr _[−]_ [1] (sum of SFRs
of the three components listed in Table 1). This gives a f 15 _µ_ m -to-SFR conversion factor of 0.21 M _⊙_ yr _[−]_ [1] mJy _[−]_ [1] . Then
Σ SFR is estimated using the ratio between the SFR value and the aperture area:


Σ SFR = [SFR] _,_ (A21)

A aper


where A aper is the area of the aperture (r = 0 _._ 25”) in kpc [2] . Note that the SFR estimated from 15 _µm_ flux may be
contaminated by shocked gas emission of the [NIII] _λ_ 15 _._ 56 _µ_ m line (Section 2.3). However since the [NIII] _λ_ 15 _._ 56 _µ_ m
line is rather weak in shocked gas (with [NIII] _/_ [NII] ratio about an order of magnitude lower than that in SF regions,
Appleton et al. in preparation), this contamination may be insignificant. Another uncertainty in using the 15 _µm_
emission as an SFR indicator is due to possible destructions of small grains which may result in underestimate of the
SFR. But, because we use the total SFR of SQ-A derived from extinction corrected H _α_ data (S. Duarte Puertas et al.
2021) instead of the one measured from the 15 _µm_ luminosity, the adopted f 15 _µ_ m -to-SFR ratio should be unbiased
on average. Nevertheless, there can still be substantial clump-to-clump variations of this ratio. Given the multiple
uncertainties listed above, the error of the Σ SFR so estimated is on the order of a factor of 2.
The depletion time scale t dep is another SF activity indicator, defined as follows:


t dep = [Σ] [mol] _._ (A22)

Σ SFR

SQ-A: A Collision Triggered Starburst 23


**Table** **A1.** Properties of individual CO clumps.


(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14) (15) (16) (17)


ID R. A. Dec. _r_ _SQA_ _[a]_ _v_ _[b]_ _σ_ _v_ _[c]_ R [d] e f CO21 [e] log(M mol ) [f] _α_ vir [g] log(P e _/_ k B ) [h] log(Σ mol ) [i] log(S) [j] log(G v ) [k] log(C) [l] log(Σ SFR ) [m] log(t dep ) [n]


(J2000) (J2000) ( _[′′]_ ) (km s _[−]_ [1] ) (km s _[−]_ [1] ) (pc) (Jy km s _[−]_ [1] ) (M _⊙_ ) (K cm _[−]_ [3] ) (M _⊙_ pc _[−]_ [2] ) (km s _[−]_ [1] pc) (km s _[−]_ [1] pc _[−]_ [1] ) (M _⊙_ yr _[−]_ [1] kpc _[−]_ [2] ) (yr)


1 338.99552 +33.98058 0.81 6723 5.13 99.8 0.096 6.18 2.0 4.37 1.68 1.53 -2.05 2.33 -0.17 7.86

2 338.99535 +33.98044 1.11 6717 9.94 76.6 0.076 6.07 7.5 5.18 1.81 1.59 -1.10 2.68 -0.60 8.41

3 338.99496 +33.98070 1.11 6974 7.46 82.9 0.067 6.02 5.1 4.78 1.69 1.91 -1.55 1.77 -1.25 8.94

4 338.99503 +33.98055 1.13 6750 10.72 104.6 0.263 6.61 3.4 5.38 2.08 2.82 -0.70 0.54 -0.70 8.78

5 338.99551 +33.98044 1.22 6736 4.22 63.3 0.023 5.56 3.6 4.17 1.46 1.52 -1.36 1.84 -0.35 7.81

6 338.99507 +33.98044 1.37 6747 6.94 75.7 0.073 6.06 3.7 4.88 1.81 1.61 -1.72 2.30 -0.55 8.36

7 338.99513 +33.98035 1.54 6750 5.47 71.8 0.043 5.82 3.7 4.50 1.62 2.02 -1.34 1.10 -0.84 8.46

8 338.99551 +33.98013 2.30 6909 5.92 59.9 0.024 5.58 6.4 4.56 1.53 1.62 -1.49 1.76 -1.44 8.97

9 338.99466 +33.98030 2.58 6757 8.07 41.7 0.014 5.35 14.0 5.08 1.62 2.69 -0.66 0.10 -1.46 9.08

10 338.99507 +33.98181 3.92 6926 3.36 70.0 0.021 5.51 2.9 3.79 1.33 1.68 -1.57 1.44 -1.92 9.25

11 338.99486 +33.98186 4.23 6951 7.80 53.1 0.035 5.73 7.0 5.11 1.79 2.71 -0.85 -0.08 -1.83 9.62

12 338.99599 +33.98203 5.02 6957 6.16 64.0 0.032 5.69 5.7 4.62 1.59 1.56 -1.27 1.92 -2.13 9.71

13 338.99674 +33.97996 5.06 6665 5.02 75.0 0.047 5.87 3.0 4.41 1.62 1.91 -1.33 1.33 -1.51 9.14

14 338.99471 +33.98206 5.08 6949 11.75 80.2 0.161 6.40 5.2 5.59 2.10 2.19 -1.08 1.62 -1.25 9.35

15 338.99432 +33.98217 5.94 6940 17.12 119.6 0.629 6.99 4.2 5.99 2.34 2.35 -1.57 1.82 -1.08 9.43

16 338.99641 +33.98225 6.29 6908 6.90 56.1 0.045 5.85 4.4 5.05 1.86 2.10 -1.04 0.96 -2.09 9.94

17 338.99532 +33.98261 6.69 6924 7.56 80.4 0.096 6.18 3.6 4.98 1.87 2.73 -0.97 0.24 -1.82 9.69

18 338.99653 +33.98234 6.75 6935 6.65 70.0 0.050 5.89 4.6 4.77 1.71 2.16 -1.34 1.30 -2.11 9.82

19 338.99683 +33.98217 6.79 6919 8.41 87.7 0.126 6.29 3.7 5.08 1.92 2.62 -0.95 0.64 -2.26 10.18

20 338.99553 +33.98278 7.35 6940 8.93 102.3 0.218 6.53 2.8 5.17 2.02 2.47 -1.14 1.17 -1.33 9.35

21 338.99546 +33.98285 7.58 6943 5.17 66.1 0.041 5.80 3.2 4.54 1.67 1.96 -1.62 1.12 -0.91 8.58

22 338.99286 +33.98020 7.65 6033 4.63 98.9 0.074 6.06 2.1 4.18 1.58 2.01 -1.54 1.21 -1.25 8.83

23 338.99572 +33.98288 7.77 6934 12.16 45.1 0.027 5.63 18.3 5.60 1.83 2.73 -0.84 0.28 -1.80 9.63

24 338.99469 +33.98287 7.87 6947 6.22 86.1 0.101 6.20 2.5 4.75 1.83 2.33 -1.34 0.84 -1.87 9.70

25 338.99267 +33.98020 8.20 6011 10.87 56.3 0.071 6.05 7.0 5.63 2.05 2.49 -1.68 1.05 -1.41 9.46

26 338.99569 +33.98305 8.37 6894 13.08 62.4 0.087 6.13 9.1 5.75 2.05 2.68 -0.43 0.60 -1.78 9.83

27 338.99593 +33.98308 8.60 6927 7.10 77.9 0.119 6.27 2.5 5.06 1.99 2.22 -1.70 1.06 -1.99 9.98

28 338.99584 +33.98311 8.63 6930 3.77 58.1 0.027 5.62 2.3 4.25 1.60 0.95 -1.40 3.04 -1.96 9.55

29 338.99253 +33.98010 8.68 6008 6.31 47.6 0.030 5.67 4.7 5.01 1.82 2.40 -0.77 0.31 -1.27 9.09

30 338.99605 +33.98316 8.94 6868 3.09 69.0 0.023 5.55 2.2 3.78 1.38 1.81 -2.15 1.02 -2.02 9.40

31 338.99232 +33.98011 9.28 6011 2.69 73.4 0.026 5.60 1.5 3.63 1.37 1.89 -1.47 0.72 -0.98 8.35

32 338.99617 +33.98324 9.30 6871 6.35 48.1 0.023 5.55 6.4 4.88 1.69 2.55 -0.87 -0.12 -2.01 9.70

33 338.99590 +33.98333 9.45 6903 12.01 72.0 0.159 6.39 4.9 5.75 2.18 2.84 -0.93 0.30 -1.98 10.16

34 338.99596 +33.98334 9.51 6882 7.03 69.3 0.064 6.00 4.0 4.94 1.82 2.25 -1.92 1.04 -2.01 9.84

35 338.99166 +33.98205 11.91 6922 7.04 46.0 0.024 5.57 7.1 5.04 1.75 2.00 -1.20 1.30 -1.74 9.49

36 338.99092 +33.97975 13.64 6006 4.29 66.3 0.073 6.06 1.2 4.63 1.92 1.89 -1.11 1.24 -1.30 9.21


**Notes:** _[a]_ Distance from the center of the SQ-A starburst (RA = 338 _._ 995333, Dec = +33 _._ 98074). _[b]_ Redshift velocity. _[c]_ Velocity
dispersion. _d_ Effective radius. _e_ Integrated CO(2-1) flux, with a _∼_ 15% error dominated by the calibration uncertainty. _f_

Logarithm of M mol, with an error on the order of a factor of _∼_ 2 dominated by the uncertainty of the conversion factor _α_ CO10 .
_g_ Virial parameter. _h_ Logarithm of the external pressure divided by the Boltzmann constant. _i_ Logarithm of the molecular
gas surface density. _[j]_ Logarithm of the S parameter (a measure of the projected specific angular momentum). _[k]_ Logarithm of
the gradient of radial velocity. _l_ Logarithm of the C parameter (a measure of the nonroational-to-rotational energy ratio). _m_

Logarithm of the SFR surface density. _[n]_ Logarithm of the depletion time scale of the molecular gas (t dep = Σ mol _/_ Σ SFR ).


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: observational_alma_primary",
  "failed_quote": "The new ALMA CO(2-1) dataset has angular resolutions between 0.2'' and 7.0'' and the new VLA HI datacube has an angular resolution of 6.6'' x 7.9''."
 },
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: observational_alma_primary",
  "failed_quote": "We added to this new observations of similar mosaic coverage but higher (~0.6'') resolution done with the ALMA 12m array in C43-3 configuration from Aug 16 - Sept 5 2024 (ID: 2023.1.00177.S; PI: Appleton)"
 },
 {
  "path": "science.targets[0].coordinates.evidence[0]",
  "value": "RA = 338.995333, Dec = +33.98074",
  "failed_quote": "Throughout the paper we assume a distance of 94 Mpc (1'' corresponds to 0.45 kpc)."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "94 Mpc",
  "failed_quote": "Throughout the paper we assume a distance of 94 Mpc (1'' corresponds to 0.45 kpc)."
 },
 {
  "path": "data.alma_project_codes[0].evidence[0]",
  "value": "2023.1.00177.S",
  "failed_quote": "We added to this new observations of similar mosaic coverage but higher (~0.6'') resolution done with the ALMA 12m array in C43-3 configuration from Aug 16 - Sept 5 2024 (ID: 2023.1.00177.S; PI: Appleton)"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "CO(2-1); channel width of 15 km s^-1 (TM2+ACA) and 4 km s^-1 (Field 4)",
  "failed_quote": "This resulted in a line-data cube with an angular resolution of 1.0'' x 0.66'' at position angle (PA) -12.7 deg, channel width of 15 km s^-1, and a root-mean-square (rms) noise of 0.85 mJy beam^-1"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[1]",
  "value": "CO(2-1); channel width of 15 km s^-1 (TM2+ACA) and 4 km s^-1 (Field 4)",
  "failed_quote": "The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1, with a beam size of 0.38'' x 0.23'' and PA=0.86 degree."
 },
 {
  "path": "data.arrays.evidence[0]",
  "value": "ACA, ALMA 12m array",
  "failed_quote": "Mosaic observations using the Atacama Compact Array (ACA) cover a region of ~10 arcmin^2 that includes all five member galaxies of SQ and most of the IGrM, with a synthetic beam of 8.0'' x 7.0''"
 },
 {
  "path": "data.arrays.evidence[1]",
  "value": "ACA, ALMA 12m array",
  "failed_quote": "We added to this new observations of similar mosaic coverage but higher (~0.6'') resolution done with the ALMA 12m array in C43-3 configuration from Aug 16 - Sept 5 2024 (ID: 2023.1.00177.S; PI: Appleton)"
 },
 {
  "path": "data.configurations.evidence[0]",
  "value": "C43-3 (for 2023.1.00177.S)",
  "failed_quote": "We added to this new observations of similar mosaic coverage but higher (~0.6'') resolution done with the ALMA 12m array in C43-3 configuration from Aug 16 - Sept 5 2024 (ID: 2023.1.00177.S; PI: Appleton)"
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "8.0'' x 7.0'' (ACA), 1.0'' x 0.66'' (TM2+ACA), 0.38'' x 0.23'' (Field 4)",
  "failed_quote": "Mosaic observations using the Atacama Compact Array (ACA) cover a region of ~10 arcmin^2 that includes all five member galaxies of SQ and most of the IGrM, with a synthetic beam of 8.0'' x 7.0''"
 },
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "8.0'' x 7.0'' (ACA), 1.0'' x 0.66'' (TM2+ACA), 0.38'' x 0.23'' (Field 4)",
  "failed_quote": "This resulted in a line-data cube with an angular resolution of 1.0'' x 0.66'' at position angle (PA) -12.7 deg, channel width of 15 km s^-1, and a root-mean-square (rms) noise of 0.85 mJy beam^-1"
 },
 {
  "path": "data.angular_resolution.evidence[2]",
  "value": "8.0'' x 7.0'' (ACA), 1.0'' x 0.66'' (TM2+ACA), 0.38'' x 0.23'' (Field 4)",
  "failed_quote": "The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1, with a beam size of 0.38'' x 0.23'' and PA=0.86 degree."
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "0.85 mJy beam^-1 per 15 km s^-1 channel (TM2+ACA); 0.66 mJy beam^-1 per 4 km s^-1 channel (Field 4)",
  "failed_quote": "This resulted in a line-data cube with an angular resolution of 1.0'' x 0.66'' at position angle (PA) -12.7 deg, channel width of 15 km s^-1, and a root-mean-square (rms) noise of 0.85 mJy beam^-1"
 },
 {
  "path": "data.sensitivity.evidence[1]",
  "value": "0.85 mJy beam^-1 per 15 km s^-1 channel (TM2+ACA); 0.66 mJy beam^-1 per 4 km s^-1 channel (Field 4)",
  "failed_quote": "The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1, with a beam size of 0.38'' x 0.23'' and PA=0.86 degree."
 },
 {
  "path": "data.observing_dates.evidence[0]",
  "value": "Aug 16 - Sept 5 2024 (2023.1.00177.S)",
  "failed_quote": "We added to this new observations of similar mosaic coverage but higher (~0.6'') resolution done with the ALMA 12m array in C43-3 configuration from Aug 16 - Sept 5 2024 (ID: 2023.1.00177.S; PI: Appleton)"
 },
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "HI 21 cm line observations in B, C & D arrays (beam 7.9'' x 6.7'', velocity coverage 5550 - 6885 km s^-1)",
  "failed_quote": "The final HI data cube has a synthesized beam of 7.9'' x 6.7'' (FWHM) and a velocity coverage of 5550 - 6885 km s^-1."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "Archived MIRI images in F770W (7.7 um), F1000W (10 um), and F1500W (15 um) bands",
  "failed_quote": "Archived images in three MIRI bands of the James Webb Space Telescope (JWST) are downloaded from the Dawn JWST Archive (DJA) website (F. Valentino et al. 2023)."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[1]",
  "value": "Archived MIRI images in F770W (7.7 um), F1000W (10 um), and F1500W (15 um) bands",
  "failed_quote": "These are F770W, F1000W and F1500W bands centered at 7.7 um, 10 um and 15 um with the angular resolutions of 0.27'', 0.33'' and 0.49'', respectively (D. Dicken et al. 2024)."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "CO(2-1) to CO(1-0) luminosity ratio r_21 = 0.34 and ACA CO(2-1) mosaic data",
  "failed_quote": "Mosaic observations using the Atacama Compact Array (ACA) cover a region of ~10 arcmin^2 that includes all five member galaxies of SQ and most of the IGrM, with a synthetic beam of 8.0'' x 7.0'' (see B. H. C. Emonts et al. 2025)."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "CO(2-1) to CO(1-0) luminosity ratio r_21 = 0.34 and ACA CO(2-1) mosaic data",
  "failed_quote": "In this work, we assume a CO conversion factor alpha_CO10 = 1.0 M_sun (K km s^-1 pc^2)^-1 and a CO(2-1) to CO(1-0) luminosity ratio r_21 = L'_CO(2-1)/L'_CO(1-0) = 0.34 (B. H. C. Emonts et al. 2025)."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "VLA C & D arrays HI 21 cm observations",
  "failed_quote": "In order to achieve better UV coverage and better sensitivity, we combine these data with those obtained with the VLA C & D arrays (beam = 19.4'' x 18.6''; B. A. Williams et al. 2002)."
 },
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "Properties of molecular clouds in the Antennae overlap region for comparison",
  "failed_quote": "Left: Plot of sigma_v vs. R_e for clumps in SQ-A region, compared with the clumps in the Antennae overlap (G. Krahm et al. 2024) and clouds in Milky Way disk (M. Heyer et al. 2009)."
 },
 {
  "path": "data.external_data_from_literature[4].what.evidence[0]",
  "value": "Properties of molecular clouds in the Milky Way disk for comparison",
  "failed_quote": "Left: Plot of sigma_v vs. R_e for clumps in SQ-A region, compared with the clumps in the Antennae overlap (G. Krahm et al. 2024) and clouds in Milky Way disk (M. Heyer et al. 2009)."
 },
 {
  "path": "processing.imaging.deconvolver.evidence[0]",
  "value": "multi-scale clean (TM2+ACA)",
  "failed_quote": "The imaging was done by using a Briggs weighting with robustness 0.5 (D. S. Briggs 1995) and applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1'' down to a threshold of 3.5 mJy beam^-1."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "Briggs weighting with robustness 0.5 (TM2+ACA); WEIGHTING = \"natural\" (Field 4)",
  "failed_quote": "The imaging was done by using a Briggs weighting with robustness 0.5 (D. S. Briggs 1995) and applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1'' down to a threshold of 3.5 mJy beam^-1."
 },
 {
  "path": "processing.imaging.cell_size.evidence[0]",
  "value": "0.1'' (TM2+ACA); 0.05'' (Field 4)",
  "failed_quote": "applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1'' down to a threshold of 3.5 mJy beam^-1."
 },
 {
  "path": "processing.imaging.multiscale_scales.evidence[0]",
  "value": "0, 5, 10, 25, and 60 pixels of 0.1'' (TM2+ACA)",
  "failed_quote": "applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1'' down to a threshold of 3.5 mJy beam^-1."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "8.0'' x 7.0'' (ACA); 1.0'' x 0.66'' at PA -12.7 deg (TM2+ACA); 0.38'' x 0.23'' at PA 0.86 deg (Field 4)",
  "failed_quote": "Mosaic observations using the Atacama Compact Array (ACA) cover a region of ~10 arcmin^2 that includes all five member galaxies of SQ and most of the IGrM, with a synthetic beam of 8.0'' x 7.0''"
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "8.0'' x 7.0'' (ACA); 1.0'' x 0.66'' at PA -12.7 deg (TM2+ACA); 0.38'' x 0.23'' at PA 0.86 deg (Field 4)",
  "failed_quote": "This resulted in a line-data cube with an angular resolution of 1.0'' x 0.66'' at position angle (PA) -12.7 deg, channel width of 15 km s^-1, and a root-mean-square (rms) noise of 0.85 mJy beam^-1"
 },
 {
  "path": "processing.imaging.final_beam.evidence[2]",
  "value": "8.0'' x 7.0'' (ACA); 1.0'' x 0.66'' at PA -12.7 deg (TM2+ACA); 0.38'' x 0.23'' at PA 0.86 deg (Field 4)",
  "failed_quote": "The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1, with a beam size of 0.38'' x 0.23'' and PA=0.86 degree."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "0.85 mJy beam^-1 per 15 km s^-1 channel (TM2+ACA); 0.66 mJy beam^-1 per 4 km s^-1 channel (Field 4)",
  "failed_quote": "This resulted in a line-data cube with an angular resolution of 1.0'' x 0.66'' at position angle (PA) -12.7 deg, channel width of 15 km s^-1, and a root-mean-square (rms) noise of 0.85 mJy beam^-1"
 },
 {
  "path": "processing.imaging.final_rms.evidence[1]",
  "value": "0.85 mJy beam^-1 per 15 km s^-1 channel (TM2+ACA); 0.66 mJy beam^-1 per 4 km s^-1 channel (Field 4)",
  "failed_quote": "The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1, with a beam size of 0.38'' x 0.23'' and PA=0.86 degree."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "ACA CO(2-1) observations and CO(2-1)/CO(1-0) luminosity ratio r_21 = 0.34",
  "failed_quote": "Mosaic observations using the Atacama Compact Array (ACA) cover a region of ~10 arcmin^2 that includes all five member galaxies of SQ and most of the IGrM, with a synthetic beam of 8.0'' x 7.0'' (see B. H. C. Emonts et al. 2025)."
 },
 {
  "path": "processing.inherited[0].what.evidence[1]",
  "value": "ACA CO(2-1) observations and CO(2-1)/CO(1-0) luminosity ratio r_21 = 0.34",
  "failed_quote": "In this work, we assume a CO conversion factor alpha_CO10 = 1.0 M_sun (K km s^-1 pc^2)^-1 and a CO(2-1) to CO(1-0) luminosity ratio r_21 = L'_CO(2-1)/L'_CO(1-0) = 0.34 (B. H. C. Emonts et al. 2025)."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Combine ALMA 12m (TM2) and ACA mosaics in CASA using Briggs weighting (robust=0.5) and multi-scale clean; reprocess archival Field 4 data with ScriptForPI.py and image with TCLEAN using natural weighting at 4 km s^-1 channel width.",
  "failed_quote": "The imaging was done by using a Briggs weighting with robustness 0.5 (D. S. Briggs 1995) and applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1'' down to a threshold of 3.5 mJy beam^-1."
 },
 {
  "path": "analysis_steps[0].method.evidence[2]",
  "value": "Combine ALMA 12m (TM2) and ACA mosaics in CASA using Briggs weighting (robust=0.5) and multi-scale clean; reprocess archival Field 4 data with ScriptForPI.py and image with TCLEAN using natural weighting at 4 km s^-1 channel width.",
  "failed_quote": "Then we clean the image by TCLEAN with the parameters WEIGHTING = \"natural\". The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1"
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "robustness = 0.5, scales = 0, 5, 10, 25, 60 pixels of 0.1'', threshold = 3.5 mJy beam^-1, channel width = 15 km s^-1 (TM2+ACA)",
  "failed_quote": "The imaging was done by using a Briggs weighting with robustness 0.5 (D. S. Briggs 1995) and applying a multi-scale clean with scales 0, 5, 10, 25, and 60 pixels of 0.1'' down to a threshold of 3.5 mJy beam^-1."
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "WEIGHTING = \"natural\", channel width = 4 km s^-1, field of view size = 38'' (Field 4)",
  "failed_quote": "Then we clean the image by TCLEAN with the parameters WEIGHTING = \"natural\". The final data cube reaches an rms of about 0.66 mJy beam^-1 and channel width of 4 km s^-1"
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Extract CO(2-1) and HI spectra from the SQ-A region (36'' x 30'' box), divide emission into three velocity components (6000: 5900-6100 km s^-1, 6600: 6500-6800 km s^-1, 6900: 6800-7000 km s^-1), compute integrated fluxes, molecular and HI gas masses, line widths (W20), and compare spatial distributions including a 12 arcsec eastward shift of the 6600 HI component.",
  "failed_quote": "Fig. 4 demonstrates that, when the 6600 HI map is shifted relative to the 6000 HI map eastwardly by 12'' (corresponding to a linear scale of ~5 kpc for a distance of 94 Mpc), the maps of the two components become very \"complementary\""
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "SQ-A box size = 36'' x 30''; velocity ranges: 5900-6100, 6500-6800, 6800-7000 km s^-1",
  "failed_quote": "The small box delineated by yellow dashed lines (size=36'' x 30'') marks the location of the \"SQ-A region\" studied in this paper."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Distance = 94 Mpc (1'' = 0.45 kpc)",
  "failed_quote": "Throughout the paper we assume a distance of 94 Mpc (1'' corresponds to 0.45 kpc)."
 },
 {
  "path": "analysis_steps[1].assumptions[1].evidence[0]",
  "value": "alpha_CO10 = 1.0 M_sun (K km s^-1 pc^2)^-1 and r_21 = 0.34",
  "failed_quote": "In this work, we assume a CO conversion factor alpha_CO10 = 1.0 M_sun (K km s^-1 pc^2)^-1 and a CO(2-1) to CO(1-0) luminosity ratio r_21 = L'_CO(2-1)/L'_CO(1-0) = 0.34 (B. H. C. Emonts et al. 2025)."
 },
 {
  "path": "analysis_steps[1].validation.evidence[0]",
  "value": "Matched angular resolutions between ACA CO(2-1) (8.0'' x 7.0'') and VLA B,C,D HI (7.9'' x 6.7'')",
  "failed_quote": "It is worth noting that the two cubes have very similar angular resolutions (ACA CO(2-1): 8.0'' x 7.0'', VLA B, C & D arrays HI: 7.9'' x 6.7'') and therefore the comparison between them is robust."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Run the FellWalker clump-finding algorithm via PyCupid on the Field 4 CO(2-1) cube, excluding composite clumps separated by spatial gaps >= 5 pixels.",
  "failed_quote": "We identified clumps in the CO(2-1) datacube of the \"Field 4\" observation of P. N. Appleton et al. (2023) using the FellWalker clump-finding algorithm via the PyCupid, which is a Python wrapper for the Starlink CUPID package (D. S. Berry et al. 2007; M. J. Currie et al. 2014)."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Calculate flux-weighted position, velocity, velocity dispersion (sigma_v), effective radius (R_e), molecular mass (M_mol), surface density (Sigma_mol), external pressure (P_e), virial parameter (alpha_vir), projected specific angular momentum (S), radial velocity gradient (G_v), and nonrotational-to-rotational energy ratio (C) for each clump; measure peak JWST 15 um flux in r = 0.25'' apertures to",
  "failed_quote": "Therefore we adopt a simpler approach of measuring the peak 15 um flux of each clump using a fixed aperture of r = 0.25'' which is approximately the resolution of the JWST 15 um image (Section 2.3)."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Calculate flux-weighted position, velocity, velocity dispersion (sigma_v), effective radius (R_e), molecular mass (M_mol), surface density (Sigma_mol), external pressure (P_e), virial parameter (alpha_vir), projected specific angular momentum (S), radial velocity gradient (G_v), and nonrotational-to-rotational energy ratio (C) for each clump; measure peak JWST 15 um flux in r = 0.25'' apertures to",
  "failed_quote": "The f_15um-to-SFR conversion is calibrated using the total 15 um flux in the SQ-A region, which is 6.85 mJy, and the total SFR = 1.42 M_sun yr^-1 (sum of SFRs of the three components listed in Table 1)."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "aperture radius r = 0.25'' for 15 um photometry; f_15um-to-SFR conversion factor = 0.21 M_sun yr^-1 mJy^-1",
  "failed_quote": "Therefore we adopt a simpler approach of measuring the peak 15 um flux of each clump using a fixed aperture of r = 0.25'' which is approximately the resolution of the JWST 15 um image (Section 2.3)."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "aperture radius r = 0.25'' for 15 um photometry; f_15um-to-SFR conversion factor = 0.21 M_sun yr^-1 mJy^-1",
  "failed_quote": "This gives a f_15um-to-SFR conversion factor of 0.21 M_sun yr^-1 mJy^-1."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Gaussian velocity distribution in each clump; Gamma = 0.5 for external pressure; G = 4.3 x 10^-3 pc (km s^-1)^2 M_sun^-1; alpha_CO10 = 1.0 M_sun (K km s^-1 pc^2)^-1; r_21 = 0.34",
  "failed_quote": "Here we assume that in the velocity dimension signals follow a Gaussian distribution characterized by sigma = sigma_v."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[2]",
  "value": "Gaussian velocity distribution in each clump; Gamma = 0.5 for external pressure; G = 4.3 x 10^-3 pc (km s^-1)^2 M_sun^-1; alpha_CO10 = 1.0 M_sun (K km s^-1 pc^2)^-1; r_21 = 0.34",
  "failed_quote": "where G = 4.3 x 10^-3 is the gravitational constant in the units of pc (km s^-1)^2 M_sun^-1."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Python wrapper used to run the FellWalker clump-finding algorithm",
  "failed_quote": "We identified clumps in the CO(2-1) datacube of the \"Field 4\" observation of P. N. Appleton et al. (2023) using the FellWalker clump-finding algorithm via the PyCupid, which is a Python wrapper for the Starlink CUPID package"
 },
 {
  "path": "software[8].used_for.evidence[0]",
  "value": "Clump-finding package containing the FellWalker algorithm",
  "failed_quote": "We identified clumps in the CO(2-1) datacube of the \"Field 4\" observation of P. N. Appleton et al. (2023) using the FellWalker clump-finding algorithm via the PyCupid, which is a Python wrapper for the Starlink CUPID package (D. S. Berry et al. 2007; M. J. Currie et al. 2014)."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Integrated CO(2-1) flux of 6000 component in SQ-A = 4.8 Jy km s^-1",
  "failed_quote": "f_CO(2-1) [Jy km s^-1] (a) : 4.8 +- 0.5 6.0 +- 0.6 8.8 +- 0.9"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Integrated CO(2-1) flux of 6600 component in SQ-A = 6.0 Jy km s^-1",
  "failed_quote": "f_CO(2-1) [Jy km s^-1] (a) : 4.8 +- 0.5 6.0 +- 0.6 8.8 +- 0.9"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Integrated CO(2-1) flux of 6900 component in SQ-A = 8.8 Jy km s^-1",
  "failed_quote": "f_CO(2-1) [Jy km s^-1] (a) : 4.8 +- 0.5 6.0 +- 0.6 8.8 +- 0.9"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Molecular gas mass of 6000 component in SQ-A = 0.75e8 M_sun",
  "failed_quote": "M_mol [10^8 x M_sun] (b) : 0.75 +- 0.38 0.93 +- 0.47 1.4 +- 0.7"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Molecular gas mass of 6600 component in SQ-A = 0.93e8 M_sun",
  "failed_quote": "M_mol [10^8 x M_sun] (b) : 0.75 +- 0.38 0.93 +- 0.47 1.4 +- 0.7"
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Molecular gas mass of 6900 component in SQ-A = 1.4e8 M_sun",
  "failed_quote": "M_mol [10^8 x M_sun] (b) : 0.75 +- 0.38 0.93 +- 0.47 1.4 +- 0.7"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Systemic CO velocity of 6000 component = 6010 km s^-1",
  "failed_quote": "v_CO [km s^-1] : 6010 +- 32 6719 +- 41 6930 +- 33"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Systemic CO velocity of 6600 component = 6719 km s^-1",
  "failed_quote": "v_CO [km s^-1] : 6010 +- 32 6719 +- 41 6930 +- 33"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Systemic CO velocity of 6900 component = 6930 km s^-1",
  "failed_quote": "v_CO [km s^-1] : 6010 +- 32 6719 +- 41 6930 +- 33"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "HI gas mass of 6000 component in SQ-A = 0.95e9 M_sun",
  "failed_quote": "M_HI [10^9 x M_sun] : 0.95 +- 0.14 1.35 +- 0.20 —"
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "HI gas mass of 6600 component in SQ-A = 1.35e9 M_sun",
  "failed_quote": "M_HI [10^9 x M_sun] : 0.95 +- 0.14 1.35 +- 0.20 —"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Mean effective radius R_e of SQ-A clumps = 72 pc",
  "failed_quote": "They have radii in the range of 45 - 100 pc (with a mean of 72 +- 3 pc) and velocity dispersions in the range of 2 - 20 km s^-1 (mean = 7.4 +- 0.5 km s^-1)."
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Mean velocity dispersion sigma_v of SQ-A clumps = 7.4 km s^-1",
  "failed_quote": "They have radii in the range of 45 - 100 pc (with a mean of 72 +- 3 pc) and velocity dispersions in the range of 2 - 20 km s^-1 (mean = 7.4 +- 0.5 km s^-1)."
 },
 {
  "path": "results_numeric[20].evidence[0]",
  "value": "Spearman correlation coefficient between t_dep and S parameter = 0.50 dimensionless",
  "failed_quote": "Indeed we see a significant correlation between t_dep and S with a Spearman correlation coefficient of r_s = 0.50 and a significance of p=2 x 10^-3."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The 6900 and 6000 CO(2-1) kinematic components in SQ-A do not spatially overlap but are bridged by the intermediate-velocity 6600 component.",
  "failed_quote": "The 6900 and 6000 components do not overlap with each other but are bridged by the the 6600 component."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "In the HI maps, shifting the 6600 component eastward by 12'' (~5 kpc) makes it fit into a gap in the extended 6000 component, showing complementary distributions characteristic of cloud-cloud collisions.",
  "failed_quote": "Fig. 4 demonstrates that, when the 6600 HI map is shifted relative to the 6000 HI map eastwardly by 12'' (corresponding to a linear scale of ~5 kpc for a distance of 94 Mpc), the maps of the two components become very \"complementary\""
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "Clumps across the three kinematic components have similar dynamical properties (R_e, sigma_v, alpha_vir, P_e) and are mostly gravitationally unbound (alpha_vir > 2) and pressure-confined.",
  "failed_quote": "All but two of them have alpha_vir > 2, namely are unbound by gravity."
 },
 {
  "path": "findings_qualitative[2].evidence[1]",
  "value": "Clumps across the three kinematic components have similar dynamical properties (R_e, sigma_v, alpha_vir, P_e) and are mostly gravitationally unbound (alpha_vir > 2) and pressure-confined.",
  "failed_quote": "There is a strong correlation between P_e/k_B and alpha_vir (the Spearman correlation coefficient r_s = 0.62 with a significance of p= 6 x 10^-5), indicating that the clumps are mainly confined by the external pressure instead of the self-gravity."
 },
 {
  "path": "findings_qualitative[3].evidence[0]",
  "value": "Star formation surface density Sigma_SFR in SQ-A clumps is stratified by kinematic component over ~2 orders of magnitude and shows no correlation with Sigma_mol or alpha_vir.",
  "failed_quote": "In contrast, their Sigma_SFR values are stratified over ~2 orders of magnitude range: 6600 clumps are on the top, 6000 clumps in the middle, and 6900 clumps at the bottom."
 },
 {
  "path": "findings_qualitative[3].evidence[1]",
  "value": "Star formation surface density Sigma_SFR in SQ-A clumps is stratified by kinematic component over ~2 orders of magnitude and shows no correlation with Sigma_mol or alpha_vir.",
  "failed_quote": "In SQ-A clumps, Sigma_SFR does not depend on Sigma_mol at all: their Spearman rank correlation coefficient is r_s = -0.04 and the significance parameter (i.e. probability of the null hypothesis) p = 0.82."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "Self-gravity does not play an important role in regulating the star formation activity in SQ-A clumps.",
  "failed_quote": "In SQ-A clumps, Sigma_SFR does not depend on Sigma_mol at all: their Spearman rank correlation coefficient is r_s = -0.04 and the significance parameter (i.e. probability of the null hypothesis) p = 0.82."
 },
 {
  "path": "reasoning.why_this_data.evidence[0]",
  "value": "High-resolution ALMA CO(2-1) data (down to 0.38'' x 0.23'', ~120 pc) are needed to resolve individual molecular clumps in SQ-A, while matched-resolution (~7''-8'') ACA CO(2-1) and VLA B+C+D HI cubes allow a robust comparison of atomic and molecular gas kinematics across the colliding systems; JWST 15 um provides an extinction-insensitive star formation tracer free from strong shock-excited H2 line",
  "failed_quote": "However both F770W and F1000W are significantly contaminated by shock-excited warm H_2 line emissions and therefore are disfavored: the F770W filter includes the H2S(4) line at 8.025 um and the F1000W filter the H2S(3) line at 9.665 um."
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "High-resolution ALMA CO(2-1) data (down to 0.38'' x 0.23'', ~120 pc) are needed to resolve individual molecular clumps in SQ-A, while matched-resolution (~7''-8'') ACA CO(2-1) and VLA B+C+D HI cubes allow a robust comparison of atomic and molecular gas kinematics across the colliding systems; JWST 15 um provides an extinction-insensitive star formation tracer free from strong shock-excited H2 line",
  "failed_quote": "It is worth noting that the two cubes have very similar angular resolutions (ACA CO(2-1): 8.0'' x 7.0'', VLA B, C & D arrays HI: 7.9'' x 6.7'') and therefore the comparison between them is robust."
 },
 {
  "path": "reasoning.why_this_method.evidence[1]",
  "value": "FellWalker was chosen for clump identification because it shows high completeness and accuracy compared to other algorithms; peak 15 um flux in a fixed r = 0.25'' aperture was used instead of integrated clump area because many clumps are smaller than the 15 um beam and blended in 2D.",
  "failed_quote": "Two operational issues make the estimation of Sigma_SFR from integrated 15 um flux over the actual sky area of a clump unfavorable: (1) many clumps are smaller than the 15 um beam; (2) on the 2-D image of the 15 um emission many clumps are blinded with each other."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Using JWST MIRI F770W (7.7 um) and F1000W (10 um) bands as star formation indicators, rejected because they are contaminated by shock-excited H2 S(4) and H2 S(3) line emission.",
  "failed_quote": "However both F770W and F1000W are significantly contaminated by shock-excited warm H_2 line emissions and therefore are disfavored: the F770W filter includes the H2S(4) line at 8.025 um and the F1000W filter the H2S(3) line at 9.665 um."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "The VLA HI observations only cover velocities up to 6885 km s^-1, missing the 6900 km s^-1 component.",
  "failed_quote": "The final HI data cube has a synthesized beam of 7.9'' x 6.7'' (FWHM) and a velocity coverage of 5550 - 6885 km s^-1."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "The CO conversion factor alpha_CO10 and the CO(2-1)/CO(1-0) luminosity ratio r_21 are highly uncertain, leading to a factor of ~2 uncertainty in M_mol.",
  "failed_quote": "It is worth noting that both alpha_CO10 and r_21 are quite uncertain. A detailed discussion of these uncertainties is given in Section 5.3."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[1]",
  "value": "The CO conversion factor alpha_CO10 and the CO(2-1)/CO(1-0) luminosity ratio r_21 are highly uncertain, leading to a factor of ~2 uncertainty in M_mol.",
  "failed_quote": "f Logarithm of M_mol, with an error on the order of a factor of ~2 dominated by the uncertainty of the conversion factor alpha_CO10."
 },
 {
  "path": "reasoning.limitations_admitted[4].evidence[0]",
  "value": "Projection effects, beam smearing, clump evolutionary stage variations, and small-scale alpha_CO variations introduce substantial scatter into the clump parameters and correlations.",
  "failed_quote": "The projection effect and beam smearing effect can affect many parameters such as R_e, sigma_v, S parameter (projected specific angular momentum), C parameter (nonrotation-to-rotation energy ratio), and the velocity gradient (G_v parameter)."
 },
 {
  "path": "reasoning.limitations_admitted[5].evidence[0]",
  "value": "The Sigma_SFR estimated from JWST 15 um flux has an uncertainty of about a factor of 2 due to potential [NIII] 15.56 um line contamination, small dust grain destruction, and clump-to-clump variations.",
  "failed_quote": "Given the multiple uncertainties listed above, the error of the Sigma_SFR so estimated is on the order of a factor of 2."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "ALMA datasets ADS/JAO.ALMA#2015.1.00241.S and ADS/JAO.ALMA#2023.1.00177.S are acknowledged; JWST data are public via MAST (doi:10.17909/9w9c-f533) and Dawn JWST Archive (zenodo.org/records/8370018).",
  "failed_quote": "Archived images in three MIRI bands of the James Webb Space Telescope (JWST) are downloaded from the Dawn JWST Archive (DJA) website (F. Valentino et al. 2023)."
 }
]
```
