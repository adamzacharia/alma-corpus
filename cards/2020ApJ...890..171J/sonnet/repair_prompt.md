# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...890..171J\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version January 22, 2020
Typeset using L [A] TEX **twocolumn** style in AASTeX62


The redshift and star formation mode of AzTEC2: a pair of massive galaxies at _z_ = 4 _._ 63


E. F. [Jim´enez-Andrade,](http://orcid.org/0000-0002-2640-5917) [1, 2] J. A. [Zavala,](http://orcid.org/0000-0002-7051-1100) [3] B. [Magnelli,](http://orcid.org/0000-0002-6777-6490) [2] C. M. Casey, [3] D. [Liu,](http://orcid.org/0000-0001-9773-7479) [4] E. [Romano-D´ıaz,](http://orcid.org/0000-0002-0071-3217) [2] E. [Schinnerer,](http://orcid.org/0000-0002-3933-7677) [4]

K. [Harrington,](http://orcid.org/0000-0001-5429-5762) [2] I. [Aretxaga,](http://orcid.org/0000-0002-6590-3994) [5] A. [Karim,](http://orcid.org/0000-0002-8414-9579) [2] J. [Staguhn,](http://orcid.org/0000-0002-8437-0433) [6, 7] A. D. Burnham, [3] A. [Monta˜na,](http://orcid.org/0000-0003-4229-381X) [8] V. Smolˇci´c, [9] M. [Yun,](http://orcid.org/0000-0001-7095-7543) [10]

F. [Bertoldi,](http://orcid.org/0000-0002-1707-1775) [2] and D. Hughes [5]


1 _National_ _Radio_ _Astronomy_ _Observatory,_ _520_ _Edgemont_ _Road,_ _Charlottesville,_ _VA_ _22903,_ _USA_
2 _Argelander_ _Institute_ _for_ _Astronomy,_ _University_ _of_ _Bonn,_ _Auf_ _dem_ _H¨ugel_ _71,_ _D-53121_ _Bonn,_ _Germany_
3 _Department_ _of_ _Astronomy,_ _The_ _University_ _of_ _Texas_ _at_ _Austin,_ _2515_ _Speedway_ _Blvd_ _Stop_ _C1400,_ _Austin,_ _TX_ _78712,_ _USA_
4 _Max_ _Planck_ _Institut_ _f¨ur_ _Astronomie,_ _K¨onigstuhl_ _17,_ _D-69117,_ _Heidelberg,_ _Germany_
5 _Instituto_ _Nacional_ _de_ _Astrof´ısica,_ _´Optica_ _y_ _Electr´onica_ _(INAOE),_ _Luis_ _Enrique_ _Erro_ _1,_ _Sta._ _Ma._ _Tonantzintla,_ _Puebla,_ _M´exico_
6 _The_ _Henry_ _A._ _Rowland_ _Department_ _of_ _Physics_ _and_ _Astronomy,_ _Johns_ _Hopkins_ _University,_ _3400_ _North_ _Charles_ _Street,_ _Baltimore,_ _MD_
_21218,_ _USA_
7 _Observational_ _Cosmology_ _Lab,_ _Code_ _665,_ _NASA_ _Goddard_ _Space_ _Flight_ _Center,_ _Greenbelt,_ _MD_ _20771,_ _USA_
8 _CONACyT_ _-_ _Instituto_ _Nacional_ _de_ _Astrof´ısica,_ _´Optica_ _y_ _Electr´onica,_ _Luis_ _E._ _Erro_ _1,_ _Tonantzintla,_ _Puebla,_ _M´exico_
9 _Faculty_ _of_ _Science,_ _University_ _of_ _Zagreb,_ _Bijeniˇcka_ _c._ _32,_ _10002_ _Zagreb,_ _Croatia_
10 _Department_ _of_ _Astronomy,_ _University_ _of_ _Massachusetts,_ _Amherst,_ _MA_ _01003,_ _USA_


(Received October, 2019; Accepted January, 2020)


ABSTRACT


We combine observations from the Atacama Large Millimeter/submillimeter Array (ALMA) and
the NOrthern Extended Millimeter Array (NOEMA) to assess the redshift and to study the star
formation conditions in AzTEC2: one of the brightest sub-millimeter galaxies (SMGs) in the COSMOS
field ( _S_ 1 _._ 1mm = 10 _._ 5 _±_ 1 _._ 4 mJy). Our high-resolution observations confirm that AzTEC2 splits into
two components (namely AzTEC2-A and AzTEC2-B) for which we detect [C II] and [12] CO(5 _→_ 4) line
emission, implying a redshift of 4 _._ 626 _±_ 0 _._ 001 (4 _._ 633 _±_ 0 _._ 001) for AzTEC2-A (AzTEC2-B) and ruling out
previous associations with a galaxy at _z_ _∼_ 1. We use the [12] CO(5 _→_ 4) line emission and adopt typical
SMG-like gas excitation conditions to estimate the molecular gas mass, which is _M_ gas ( _α_ CO _/_ 2 _._ 5) =
2 _._ 1 _±_ 0 _._ 4 _×_ 10 [11] _M_ _⊙_ for AzTEC2-A, and a factor four lower for AzTEC2-B. With the infrared-derived
star formation rate of AzTEC2-A (1920 _±_ 100 _M_ _⊙_ yr _[−]_ [1] ) and AzTEC2-B (710 _±_ 35 _M_ _⊙_ yr _[−]_ [1] ), they both

_−_
will consume their current gas reservoir within (30 200) Myr. We find evidence of a rotation-dominated

[C II] disk in AzTEC2-A, with a de-projected rotational velocity of _v_ rot ( _i_ = 39 _[◦]_ ) = 660 _±_ 130 km s _[−]_ [1],
velocity dispersion ≲ 100 km s _[−]_ [1], and dynamical mass of _M_ dyn ( _i_ = 39 _[◦]_ ) = 2 _._ 6 [+1] _−_ 0 _[.]_ _._ [2] 9 _[×]_ [ 10] [11] _[ M]_ _[⊙]_ [.] [We]
propose that an elevated gas accretion rate from the cosmic web might be the main driver of the
intense levels of star formation in AzTEC2-A, which might be further enhanced by gravitational
torques induced by its minor companion (AzTEC2-B). These results strengthen the picture whereby
the population of single-dish selected SMGs is rather heterogeneous, including a population of pairs of
massive, highly-active galaxies in a pre-coalescence phase.


_Keywords:_ galaxies: distances and redshifts – galaxies: high-redshift – galaxies: formation – galaxies:
evolution – galaxies: starburst – galaxies: ISM



1. INTRODUCTION


Empirical and theoretical evidence indicate that the
global production of stars in galaxies is mainly regu

Corresponding author: E. F. Jim´enez-Andrade
[ejimenez@nrao.edu](mailto: ejimenez@nrao.edu)



lated by the steady accretion of gas from the intergalactic medium (IGM, e.g., Dekel et al. 2009b; L´Huillier
et al. 2012; Hayward et al. 2012; Bouch´e et al. 2013),
which drives widespread star formation in galactic disks
over Gigayear (Gyr) time-scales (e.g., Daddi et al.
2010a; Genzel et al. 2010; Tacchella et al. 2016; Jim´enezAndrade et al. 2019). Such a process of galaxy evolution,

2 Jim´enez-Andrade et al.



known as the “cold gas accretion mode” of star formation, differs from the more intense production of stars
during occasional starburst episodes of ten to few hundred Megayears (Myr) length (e.g., Daddi et al. 2010a;
Genzel et al. 2010; Rodighiero et al. 2011). This is often
due to major/minor mergers providing the energetic
and baryonic input to abruptly enhance the star formation rate (SFR) of galaxies (e.g., Narayanan et al. 2010;
L´Huillier et al. 2012; Ellison et al. 2013). Whereas
both regimes of star formation have been widely explored out to intermediate redshifts ( _z_ _∼_ 2; e.g., Genzel
et al. 2010; Wuyts et al. 2011; Magnelli et al. 2012, 2014;
Daddi et al. 2015; Elbaz et al. 2018; Jim´enez-Andrade
et al. 2019), the relative role of the cold gas accretion
and merger mode in driving the intense production of
stars in galaxies at higher redshifts ( _z_ ≳ 3) remains
an open issue (e.g., Carilli et al. 2010; Hayward et al.
2012; Hodge et al. 2012; Hayward et al. 2018; Jim´enezAndrade et al. 2018; Tadaki et al. 2018).


Exploring such early cosmic epochs has been possible thanks to a strong, negative K-correction that
makes high-redshift star-forming galaxies (SFGs) easier to detect at sub-millimeter (sub-mm) wavelengths
(e.g., Blain et al. 2002; Casey et al. 2014). These submm selected galaxies (SMGs) are, in general, massive
star-bursting systems with SFR up to _∼_ 2000 _M_ _⊙_ yr _[−]_ [1]

and stellar masses ( _M_ _⋆_ ) of log( _M_ _⋆_ _/M_ _⊙_ ) ≳ 10 _._ 5 (e.g.,
Barger et al. 2012; Smolˇci´c et al. 2015; G´omez-Guijarro
et al. 2018; Harrington et al. 2018; Jim´enez-Andrade
et al. 2018; Lang et al. 2019). SMGs have acquired
particular relevance to probe the merger and cold gas
accretion mode in the yet unexplored _z_ ≳ 3 regime (e.g.,
Carilli et al. 2010; Hayward et al. 2012). Although the
“canonical” formation scenario of these massive starbursts involves major gas-rich mergers (e.g., Tacconi
et al. 2006, 2008; Engel et al. 2010; Bothwell et al. 2010;
Narayanan et al. 2010; Ivison et al. 2012; Bothwell et al.
2013), recent observational (and theoretical) evidence
indicates that highly active star-forming disks can also
lead to SMG-like luminosities (e.g., Dav´e et al. 2010;
Hodge et al. 2012, 2016; Narayanan et al. 2015; Hayward et al. 2018; Tadaki et al. 2018; Hodge et al. 2019).


A heterogeneous SMG population, i.e., secular disks
and major mergers, could also explain the diversity of
quiescent massive galaxies at _z_ _∼_ 2 _−_ 3 (e.g., Gobat
et al. 2012; Toft et al. 2012, 2017). Whereas the structure and dynamics of most of those quiescent systems
seem to be a result of compact, merger-driven SMGs at
_z_ _>_ 3 (Toft et al. 2014; Ikarashi et al. 2015; Fudamoto
et al. 2017; G´omez-Guijarro et al. 2018), the progeni


tors of quiescent disk galaxies at _z_ _∼_ 2 (Newman et al.
2012; Toft et al. 2017) might have hosted enhanced star
formation distributed across a massive rotating disk.


Despite the necessity to characterize the properties of
_z_ _>_ 3 massive, star-forming disks, only limited/small
samples of such galaxies exist (e.g., Hodge et al.
2012; De Breuck et al. 2014; Jones et al. 2017; Shao
et al. 2017). For instance, out of the 118 SFGs at
4 _<_ _z_ _<_ 6 in the recent ALPINE [C II] survey, no
more than 15% of them are rotating disks (Le F`evre
et al. 2019). Among the hundreds of SMGs across the
two square degree COSMOS field (e.g., Casey et al.
2013; Brisbin et al. 2017), only AzTEC1 ( _z_ = 4 _._ 341),
AzTEC/C159 ( _z_ = 4 _._ 569), J1000+0234 ( _z_ = 4 _._ 542),
and Vd _−_ 17871 ( _z_ = 4 _._ 622) exhibit convincing evidence for gas-dominated rotating disks (Jones et al.
2017; Tadaki et al. 2018). Consequently, these systems
emerge as key laboratories to investigate the role of cold
gas accretion in driving star formation at _z_ _∼_ 4 _._ 5, which
is the cosmic epoch when the cosmological gas accretion
rate onto galaxies is expected to be maximal (e.g., Kereˇs
et al. 2005).


Here, we use high-resolution observations of the Atacama Large Millimeter Array (ALMA) and NOrthern
Extended Millimeter Array (NOEMA) to unveil the redshift and conditions for star formation in AzTEC2. This

source is one of the brightest SMGs in the COSMOS
field, which is composed by a massive, star-forming disk
and a smaller companion galaxy at _z_ = 4 _._ 63. We use

[C II] and [12] CO(5 _→_ 4) line observations to probe the
gas content, star formation efficiency, and gas dynamics of AzTEC2 within the context of cold gas accretion
and merger-driven star formation in the early Universe.
This manuscript is organized as follows. In _§_ 2, we introduce the AzTEC2 source, while in _§_ 3, we describe the
observations and data reduction. In _§_ 4, we present the
analysis and results. The implications of this work are
discussed in _§_ 5. We adopt a flat ΛCDM cosmology with
_h_ 0 = 0 _._ 7, Ω _M_ = 0 _._ 3, and Ω Λ = 0 _._ 7.


2. AZTEC2: A BRIGHT, MULTI-COMPONENT
SMG


AzTEC2 was originally identified in the two surveys
undertaken with the camera AzTEC at 1.1 mm over
an area of _∼_ 0 _._ 5 degs [2] in the COSMOS field (Scott
et al. 2008; Aretxaga et al. 2011). In the first survey, obtained with the camera AzTEC mounted at
the James Clerk Maxwell Telescope (JCMT), it was
identified as the second brightest source in the survey:
AzTEC2 (Scott et al. 2008). Later, with the cam

The nature of the puzzling SMG AzTEC2 3



























ALMA Band 7/887 _µ_ m (green; this study) and VLA Band S/10 cm (blue; Smolˇci´c et al. 2017) contours overlaid on top the
_HST_ /ACS F814W image. All contour levels are above three times the noise r.m.s. The zoomed-in image ( _right_ _panel_ ) shows
two foreground sources: a massive elliptical galaxy at _z_ = 0 _._ 34 and a SFG at _z_ = 1 _._ 12. ALMA and VLA imaging at sub-arcsec
resolution reveal two optically-undetected components at _z_ _∼_ 4 _._ 63, labeled as AzTEC2-A and AzTEC2-B.



era AzTEC on the Atacama Submillimeter Telescope
Experiment (ASTE), it was identified as AzTEC/C3,
i.e., the third brightest source in the survey (Aretxaga
et al. 2011). This bright SMG was also detected in
the deep Herschel/HerMES survey (250-500 _µ_ m maps)
and SCUBA-2 at both 450 _µ_ m and 850 _µ_ m (Casey et al.
2013). AzTEC2 was recently cataloged as the second
brightest SMG in the IRAM/GISMO 2 mm deep survey (over _∼_ 250 arcmin [2] _,_ Magnelli et al. 2019) and as
the brightest galaxy in the ALMA 2 mm mosaic in the
COSMOS field (with an area of _∼_ 155 arcmin [2] ; Casey
et al. in prep.; Zavala et al. in prep.).


Recent imaging with ALMA (Brisbin et al. 2017) revealed that AzTEC2 is composed of two components
separated by 3 arcsec (see Fig. 1): namely component
AzTEC2-A and AzTEC2-B. Both sources were also
detected with signal-to-noise ratio (SNR) _>_ 10 in the
3 GHz radio continuum imaging with the Very Large
Array (VLA) at 0 _._ 75 arcsec resolution (Miettinen et al.
2017). Neither of the two components have a robust
optical/near-infrared (IR) counterpart (Fig. 1; Laigle
et al. 2016), hindering the redshift determination of
the AzTEC2 complex. While a spectroscopic redshift
solution of _z_ = 1 _._ 12 has been adopted for AzTEC2
in past studies (e.g., Smolˇci´c et al. 2012, 2017; Miettinen et al. 2015, 2017; Brisbin et al. 2017), recent
optical/near-IR spectroscopy revealed that such a redshift value corresponds to a bright foreground SFG at



only 1.5 arcsec to the south of AzTEC2 (Casey et al.
2017, see Fig. 1). High-resolution observations at submm/mm wavelengths (probing the cold star-forming interstellar medium) are hence crucial to unambiguously
constrain the redshift of AzTEC2-A and AzTEC2-B, as
well as to investigate the conditions for star formation
in these bright SMGs.


3. OBSERVATIONS AND DATA REDUCTION


ALMA Band 7 observations (project 2015.1.00568.S,
PI: C. Casey) were conducted on April 23 and September 1, 2016. The 12 m main array was used in two
different configurations to obtain sub-arcsecond angular resolution without losing sensitivity at larger scales
(maximum recoverable angular scale of _∼_ 4 _._ 7 arcsec).
The spectral setup, originally designed to only detect
dust continuum emission, covered the frequency ranges
of 335.5 _−_ 339.5 GHz and 347.5 _−_ 351.5 GHz. Data re
duction and imaging were performed following the standard steps of the ALMA reduction pipeline scripts with
CASA. During the imaging process, a Briggs weighting
(robust=0.5) was used since it provided a good compromise between angular resolution and noise. We reached
a final sensitivity of 1 _σ_ _≃_ 1 mJy beam _[−]_ [1] for a 50 MHz
channel width (corresponding to _∼_ 50 km s _[−]_ [1] ) and a
median restoring beam of 0 _._ 23 _×_ 0 _._ 18 arcsec [2] (PA=51 _[◦]_ ).
These observations allow us to pinpoint the emission
from the different sources in this crowded field, and to

4 Jim´enez-Andrade et al.



spatially resolve the emission of AzTEC2-A.


A preliminary analysis of the ALMA data revealed a
serendipitous line detection at the edge of our spectral
windows, which was associated with [C II] at _z_ _∼_ 4 _._ 6
(see details in _§_ 4). To confirm the redshift, we then
analyzed observations taken with the Redshift Search
Receiver (RSR; Erickson et al. 2007) on the Large Millimeter Telescope. AzTEC2 was targeted as part of
the Early Science Phase observations between 2014 and
2015 with a 32-m antenna (projects YUNM020 and
HUGD024, PIs: M. Yun and D. Hughes, respectively).
A total on-source time of 5 hrs led to a noise r.m.s of
_≈_ 1.0 mJy beam _[−]_ [1] per channel, with a spectral resolution of _∼_ 31 MHz/100 km s _[−]_ [1] and spatial resolution of
_∼_ 25 arcsec. Data reduction was performed in a similar
way as described in Zavala et al. (2015, 2018). The final
spectrum, covering the frequency range 73 _−_ 111 GHz,
revealed a tentative detection of the [12] CO(5 _→_ 4) line
emission at _z_ _∼_ 4 _._ 6. Although its low SNR ( _∼_ 2) prevented us from firmly confirming the redshift, this tentative line detection allowed us to request further obser
vations.


Follow-up observations were hence taken with NOEMA
in Band 1 over two tracks on January 26 and 29, 2019
(project W18EU, PI: E.F. Jim´enez-Andrade). A total observing time of 3.3 hours was reached using 10
antennas in A-configuration. We used the PolyFix correlator to cover the frequency range 84.9 – 92.7 GHz
and 100.2–108.0 GHz, targeting the [12] CO(5 _→_ 4) line
at _z_ _∼_ 4 _._ 6. The data reduction was performed with the
software `GILDAS` using the NOEMA standard pipeline,
while imaging was done with the package `mapping` using natural weighting. The achieved spatial resolution of
1 _._ 7 _×_ 0 _._ 9 arcsec (PA = _−_ 163 _[◦]_ ) suffices to resolve the two
components of AzTEC2 separated by _∼_ 3 arcsec (Fig.
1). The spectral data cube was smoothed to a _∼_ 34 MHz
resolution (i.e., _∼_ 100 km s _[−]_ [1] ), reaching a sensitivity of
0.13 mJy beam _[−]_ [1] per channel.


4. DATA ANALYSIS AND RESULTS


4.1. _Gravitational_ _lensing_ _magnification_


Although there are no clear indications of gravitational amplification in our high-resolution ALMA data
(Fig. 2), there are two foreground galaxies which could
magnify the emission of both AzTEC2 components (Fig.
1). We use the `Visilens` code (Spilker et al. 2016) to
estimate the gravitational amplification factor ( _µ_ ) as
follows. We model each foreground source separately,
adopting a lens mass profile parameterized as an isother


mal ellipsoid and assuming the Einstein mass to be
2 _._ 5 _M_ _⋆_ (Auger et al. 2009). Given the relatively large
offset between the foreground and background galaxies
(≳ 1 _._ 5 arcsec), second-order parameters of the lens mass
profiles such as shape and ellipticity are found to be
not relevant for the analysis. At the position of both
AzTEC2-A and AzTEC2-B, the foreground galaxy at
_z_ = 1 _._ 1 produces a negligible amplification while using
a stellar mass upper limit of log( _M_ _⋆_ _/M_ _⊙_ ) = 9 _._ 6. On
the other hand, the amplification produced by the more
massive, elliptical galaxy (log( _M_ _⋆_ _/M_ _⊙_ ) = 11; Laigle
et al. 2016) at _z_ = 0 _._ 34 is estimated to be _µ_ A = 1 _._ 5
( _µ_ B = 1 _._ 35) at the position of AzTEC2-A (AzTEC2B). We adopt these magnification factors throughout the
rest of the paper.


4.2. 12 _CO(5→4)_ _and_ _[CII]_ _line_ _detections_ _in_ _AzTEC2_
_at_ _z_ = 4 _._ 6


The NOEMA spectrum reveals emission at the
position of AzTEC2-A and AzTEC2-B peaking at
_∼_ 102 _._ 5 GHz. By collapsing the data cube within the
frequency range 102.2 _−_ 102.7 GHz, which encompasses
the full emission line, we derive the intensity map shown
in the upper-right panel of Fig. 2. A 2D Gaussian fit
indicates that AzTEC2-A is resolved by our observations, with a deconvolved full width at half maximum
of _[√]_ _µ_ A FWHM = 1 _._ 2 _±_ 0 _._ 4 arcsec along the major axis.
We use an aperture that is a factor 1.5 larger than the
convolved FWHM of AzTEC2-A to retrieve most of
the emission and extract the [12] CO(5 _→_ 4) line spectrum. Since AzTEC2-B appears as a point-like (unresolved) source, we integrate emission across a region
that equals the size of the synthesized beam to obtain the spectrum (lower-right panel of Fig. 2). We
identify a broad (FWHM _∼_ 800 km s _[−]_ [1] ), double-peaked
emission line centered at 102 _._ 43 _±_ 0 _._ 03 GHz associated

with AzTEC2-A. Through a least-squares algorithm
(Levenberg-Marquardt), we find that a model with two
Gaussian components describes better the line profile
than a single Gaussian curve (yielding a reduced _χ_ [2]

of 2.0 and 2.6, respectively). We thus adopt the former model and derive an integrated flux density of
_µ_ A _S_ CO(5 _→_ 4) = 1070 _±_ 60 mJy km s _[−]_ [1] . We also identify
an 8 _._ 4 _σ_ line detection at the locus of AzTEC2-B that

is centered at 102 _._ 30 _±_ 0 _._ 02 GHz. A single Gaussian
model (reduced _χ_ [2] = 1 _._ 2) leads to an integrated flux
density of _µ_ B _S_ CO(5 _→_ 4) = 260 _±_ 30 mJy km s _[−]_ [1] (Table 1).


By averaging line-free channel maps in the [12] CO(5 _→_
4) data cube, we also detect dust continuum emission
from both components (peak SNR≳10) at the observed
wavelength of 2924 _µ_ m. A 2D Gaussian fitting gives a

The nature of the puzzling SMG AzTEC2 5


**[CII] with ALMA** **12** **CO(5→4) with NOEMA**



Jy beam _[−]_ [1] km s _[−]_ [1]
0 _._ 00 0 _._ 75 1 _._ 00 1 _._ 25 - 1 _._ 50



Jy beam _[−]_ [1] km s _[−]_ [1]
0 _._ 000 0 _._ 002 0 _._ 003 0 _._ 004 - 0 _._ 005



- 1 0 000 0 002 0 003 0 


15


14


13


12


11


+2 : 26 : 10


20


10


0


20


10


0



14


12


+2 : 26 : 10



08 _._ 1 08 _._ 0 07 _._ 9 10 : 00 : 07 _._ 8

RA (J2000)



|0.10 0.15 0.20 −1 km s−1 eam−1 km s−1|Col2|
|---|---|
|><br>0004<br>0005<br>|><br>0004<br>0005<br>|
|_._<br>_._|_._<br>_._|
|||
|||
|2 arcsec - 13 kpc||


08 _._ 2 08 _._ 1 08 _._ 0 07 _._ 910 : 00 : 07 _._ 8

RA (J2000)







































**Figure** **2.** _Upper_ _panels:_ Velocity-integrated intensity map ([ _−_ 600 _,_ +1100] km s _[−]_ [1] ) of the [C II] and [12] CO(5 _→_ 4) line emission
detected with ALMA and NOEMA, respectively, of AzTEC2-A and AzTEC2-B. The contours indicate the [3 _σ_, 5 _σ_, 8 _σ_, 13 _σ_ ]
levels. The black diamonds mark the position of AzTEC2-A and AzTEC2-B inferred from high-resolution far-infrared and radio
continuum imaging with ALMA and the VLA (Brisbin et al. 2017; Smolˇci´c et al. 2017). The center of the foreground SFG at
_z_ = 1 _._ 1235 is marked by the black square. The synthesized beam is shown in the lower-left corner, while the dashed ellipses
illustrate the aperture used to extract the spectra. _Lower_ _panels:_ Spectra of the [C II] and [12] CO(5 _→_ 4) line emission detected
with ALMA and NOEMA, respectively, of AzTEC2-A and AzTEC2-B. The red solid line represents the model with one (two)
Gaussian component(s) that reproduce the [C II] and [12] CO(5 _→_ 4) line profile in AzTEC2-B (AzTEC2-A). The gray line shows a
Gaussian model to fit the [12] CO(5 _→_ 4) line profile of AzTEC2-A. The vertical lines mark the central frequency of the [C II] and
12 CO(5 _→_ 4) line profiles; in the case of AzTEC2-A, this is derived from a model with two (in red) and one (in gray) Gaussian
component(s). The velocities displayed in the spectra are relative to the central frequency of the [12] CO(5 _→_ 4) line emission in
AzTEC2-A.

6 Jim´enez-Andrade et al.



total flux density of 0 _._ 33 _±_ 0 _._ 05 mJy and 0 _._ 09 _±_ 0 _._ 02 mJy
for AzTEC2-A and AzTEC2-B, correspondingly (Table
1). Limited by our 1 _._ 7 _×_ 0 _._ 9 arcsec resolution, the dust
continuum emission of both components is not spatially
resolved by these NOEMA observations.


Significant line emission is detected at _∼_ 338 GHz towards both AzTEC2 components in the ALMA data
cube (upper-left panel of Fig. 2). The velocityintegrated intensity map shows that these sources are
resolved. AzTEC2-A, in particular, exhibits extended
emission distributed across _∼_ 5 spatial resolution elements. A 2D Gaussian fit indicates a deconvolved
FWHM of _[√]_ _µ_ A FWHM = 0 _._ 70 _±_ 0 _._ 12 arcsec along
the major axis for AzTEC2-A, and _[√]_ _µ_ B FWHM =
0 _._ 53 _±_ 0 _._ 18 arcsec for AzTEC2-B (Table 1). To extract
the line spectra we use an aperture that is a factor 1 _._ 5
larger than the measured FWHM, allowing us to recover
most of the extended line emission. As illustrated in the

lower-left panel of Fig. 2, these ALMA line detections
lie at the edges of the spectral windows used in our
observations, preventing us from recovering/inspecting
their total line profiles. There is tentative evidence,
however, of a double-peaked line profile in AzTEC2-A
as that observed at _∼_ 103 GHz with NOEMA. Dur
ing the fitting procedure, the relative amplitude and
FWHM of the two peaks from this ALMA [CII] line
detection are fixed to the values of the [12] CO(5 _→_ 4)
line emission. The fit indicates a total integrated flux
density of _µ_ A _S_ [C II] = 10 _._ 9 _±_ 1 _._ 2 Jy km s _[−]_ [1] and central
frequency of 337 _._ 8 _±_ 0 _._ 2 GHz. On the other hand, we use
the FWHM of our _∼_ 103 GHz line detection as a prior
to model the profile of that at _∼_ 338 GHz in AzTEC2-B
(reduced _χ_ [2] = 0 _._ 9), which gives a total integrated flux
density of _µ_ B _S_ [C II] = 4 _._ 2 _±_ 0 _._ 9 Jy km s _[−]_ [1] and central
frequency of 337 _._ 4 _±_ 0 _._ 2 GHz.


Finally, we average line-free channel maps in the [C II]
data cube and detect dust continuum emission for both
AzTEC2 sources (peak SNR≳13) at the observed wavelength of 887 _µ_ m (see Fig. 1). By fitting a 2D Gaussian
model we derive a total flux density of 13 _._ 3 _±_ 0 _._ 5 mJy
and 4 _._ 5 _±_ 0 _._ 5 mJy for AzTEC2-A and AzTEC2-B, correspondingly (Table 1). The model also indicates that
the dust continuum emission of both components is
spatially resolved by these ALMA observations, with a
deconvolved FWHM of _[√]_ _µ_ FWHM _≃_ 0 _._ 35 _±_ 0 _._ 03 arcsec
(Table 1).


By combining the line detections towards AzTEC2A at _∼_ 102.5 GHz and 337.5 GHz, we can unambiguously associate them with [12] CO(5 _→_ 4) and [C II], re


spectively, leading to a redshift solution of _z_ = 4 _._ 626 _±_
0 _._ 001. Similarly, for AzTEC2-B we estimate a redshift of _z_ = 4 _._ 633 _±_ 0 _._ 001, implying a velocity offset
of +375 _±_ 50 km s _[−]_ [1] with respect to AzTEC2-A. These
robust line detections and counterpart association rule
out the preliminary redshift solution of _z_ = 1 _._ 1235 for
AzTEC2 adopted in past studies (e.g., Smolˇci´c et al.
2012, 2017; Miettinen et al. 2015; Brisbin et al. 2017;
Miettinen et al. 2017).


4.3. _Molecular_ _gas_ _content_ _and_ _star_ _formation_ _rate_ _of_
_AzTEC2_


We use the [12] CO(5 _→_ 4) line detections to estimate
the [12] CO(1 _→_ 0) line luminosity, _L_ _[′]_ CO(1 _→_ 0) [,] [and] [hence]
infer the molecular gas mass in the AzTEC2 complex.
We first consider that due to the higher temperature
of the CMB at _z_ = 4 _._ 6, the intrinsic value of the
12 CO(5 _→_ 4) line, _S_ CO(5intrinsic _→_ 4) [,] [is] [a] [factor] [[1/0.8]] [higher]
(da Cunha et al. 2013) than the one measured from
our observations. In using this factor, we assume that
both AzTEC2-A and AzTEC2-B harbor a dense interstellar medium (ISM) with elevated gas kinetic temperature ( _T_ kin _∼_ 40 K) – as the majority of SMGs (e.g.,
Magnelli et al. 2012; Ca˜nameras et al. 2018). Therefore, we find that _µ S_ CO(5 [intrinsic] _→_ 4) [is] [1340] _[ ±]_ [ 100 mJy km s] _[−]_ [1]

(325 _±_ 40 mJy km s _[−]_ [1] ) for AzTEC2-A (AzTEC2-B).
The corresponding line luminosity is subsequently derived following Carilli & Walter (2013, Sect. 2.4). We
adopt typical SMG-like gas excitation conditions to
convert the [12] CO(5 _→_ 4) line luminosity, _L_ _[′]_ CO(5 _→_ 4) [,] [to]
_L_ _[′]_ CO(1 _→_ 0) [.] [Then,] _[ L]_ _[′]_ CO(1 _→_ 0) [= [1] _[/]_ [0] _[.]_ [32]] _[ ×]_ _[L]_ _[′]_ CO(5 _→_ 4) [(e.g.,]
Bothwell et al. 2013; Carilli & Walter 2013), which gives
_µ L_ _[′]_ CO(1 _→_ 0) [=] [12] _[.]_ [8] _[ ±]_ [ 2] _[.]_ [4] _[ ×]_ [ 10] [10] [ K km s] _[−]_ [1] [ pc] [2] [and] [3] _[.]_ [1] _[ ±]_
0 _._ 7 _×_ 10 [10] K km s _[−]_ [1] pc [2] for AzTEC2-A and AzTEC2B, respectively (see Table 1). Finally, the molecular
gas mas, _M_ gas, can be inferred through the CO-to-H 2
( _α_ CO ) conversion factor: _M_ gas = _α_ CO _L_ _[′]_ CO(1 _→_ 0) [.] [The]
value of _α_ CO depends on the physical and chemical conditions of the ISM (e.g., Papadopoulos et al. 2012a,b).
While low values ( _α_ CO = 0 _._ 8 _M_ _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2] ) are
consistent with the turbulent and extreme ISM con
ditions of, for example, ultra-luminous infrared galaxies (ULIRGs; e.g., Downes & Solomon 1998), higher
vales ( _α_ CO = 4 _._ 3 _M_ _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2] ) are consistent
with a self-gravitating gas configuration as observed in
star-forming disks (e.g., Magnelli et al. 2012). Here
we adopt a mean _α_ CO = 2 _._ 5 _M_ _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2][1] to
better compare AzTEC2-A and AzTEC2-B with the


1 We refer the reader to _§_ 5.2 where we discuss in more detail
the nature of _α_ CO

The nature of the puzzling SMG AzTEC2 7



heterogeneous population of _z_ _∼_ 4 _−_ 5 SMGs, which includes both mergers and star-forming disks (e.g., Hayward et al. 2018). We find a molecular gas mass of
_µ_ A _M_ gas ( _α_ CO _/_ 2 _._ 5) = 3 _._ 2 _±_ 0 _._ 6 _×_ 10 [11] _M_ _⊙_ in AzTEC2-A,
and a factor four lower in AzTEC2-B (see Table 1).
The lensing-corrected gas mass budget of AzTEC2-A,
_M_ gas ( _α_ CO _/_ 2 _._ 5) = 2 _._ 1 _±_ 0 _._ 4 _×_ 10 [11] _M_ _⊙_, is consistent with
the massive gas reservoir of others _z_ _∼_ 4 _−_ 5 SMGs
like AzTEC1, AzTEC3, AzTEC/C159, J1000+0234,
and GN20 (Schinnerer et al. 2008; Carilli et al. 2010;
Riechers et al. 2010; Hodge et al. 2012; Yun et al. 2015;
Jim´enez-Andrade et al. 2018; Tadaki et al. 2018), for
which the median _M_ gas ( _α_ CO _/_ 2 _._ 5) is _∼_ 2 _×_ 10 [11] _M_ _⊙_ .


We derive the infrared luminosity ( _L_ IR, integrated
over the wavelength range of 8 _−_ 1000 _µ_ m) and dust
mass ( _M_ dust ) of the AzTEC2 complex by fitting its
mid-IR–to–mm SED. This is done by following the
SED fitting procedure presented by Liu et al. (2018),
and by combining our dust continuum measurements at
887 _µ_ m and 2.92 mm with information from the COSMOS photometric catalog compiled by Jin et al. (2018)
and Liu et al. (2018). In the case of AzTEC2, this
catalog includes photometric measurements at (see Table 1): 24 _µ_ m (Le Floc’h et al. 2009), 100 _µ_ m, 160 _µ_ m
(Lutz et al. 2011), 250 _µ_ m, 350 _µ_ m, 500 _µ_ m (Oliver et al.
2012), 850 _µ_ m (Geach et al. 2016), 1 _._ 1 mm (Aretxaga
et al. 2011), 10 cm (Schinnerer et al. 2010) and 21 cm
(Smolˇci´c et al. 2017). The photometric measurement at
2 mm recently obtained with the GISMO-2 bolometer
camera (Magnelli et al. 2019) is also included in the
analysis.


Since most photometric data towards the AzTEC2
complex do not have sufficient resolution to deblend
the emission of AzTEC2-A and AzTEC2-B (Table 1),
we use the combined monochromatic flux densities of
both components even if high-resolution observations
are available. We then fit the SED with five components: a stellar template from the Bruzual & Charlot
(2003) models, an active galactic nuclei (AGN) template
from Mullaney et al. (2011), warm and cold dust templates from Draine & Li (2007). The fifth component
is a radio power law tailored to the dust IR luminosity with _q_ IR = 2 _._ 4, where _q_ IR is the median value for
the ratio between far-infrared and radio luminosity of
SFGs (e.g., Magnelli et al. 2015; Delhaize et al. 2017).
The fitting is performed through Monte Carlo sampling (with _N_ = 15000, following Liu et al. (2018)),
from which the _χ_ [2] distribution and uncertainties are
obtained. Our analysis indicates that a model with
no AGN component provides the best fit to our data



points, albeit more photometric information is needed
to confirm the (apparently) negligible AGN activity in
AzTEC2. Finally, we derive a total infrared luminosity of log( _µL_ IR _/L_ _⊙_ ) = 13 _._ 59 _±_ 0 _._ 02 and dust mass of
log( _µM_ dust _/M_ _⊙_ ) = 9 _._ 64 _±_ 0 _._ 10 for the AzTEC2 complex.


To disentangle the contribution of AzTEC2-A and
AzTEC2-B to the total _L_ IR and _M_ dust, we use
our high-resolution photometric data at 887 _µ_ m and
2924 _µ_ m. These observations independently trace the
peak and Rayleigh-Jeans regime of the SED of both
components (Table 1), allowing us to infer the contribution of AzTEC2-A and AzTEC2-B to the to
tal IR SED. Then, since the ratio between the IR
flux density of the two components at 887 _µ_ m and
2924 _µ_ m is _S_ AzTEC2 [IR] _−_ A _[/S]_ AzTEC2 [IR] _−_ B _[≃]_ [3,] [we] [estimate]
log( _µ_ A _L_ IR _/L_ _⊙_ ) = 13 _._ 46 _±_ 0 _._ 02 and log( _µ_ A _M_ dust _/M_ _⊙_ ) =
9 _._ 51 _±_ 0 _._ 10 for AzTEC2-A. For AzTEC2-B we derive
log( _µ_ B _L_ IR _/L_ _⊙_ ) = 12 _._ 98 _±_ 0 _._ 02 and log( _µ_ B _M_ dust _/M_ _⊙_ ) =
9 _._ 03 _±_ 0 _._ 10.


We note that the above reasoning assumes that the
intrinsic SED of AzTEC2-A and AzTEC2-B are similar.

While this is supported by the consistent flux density
ratios at 887 _µ_ m and 2924 _µ_ m, the properties that have
been inferred from the scaled SEDs are subject to a high
degree of uncertainty. Therefore, to add an independent constraint on the _L_ IR of AzTEC2-A and AzTEC2B that is not affected by source blending, we use their

[C II] line luminosity ( _L_ [C II] ) to estimate _L_ IR via the
empirical _L_ [C II] _/L_ IR luminosity ratio (e.g., Maiolino,
R. et al. 2009; Lagache et al. 2018). We assume that
the physical properties of AzTEC2-A and AzTEC2-B
are similar to the ones of bright SMGs at similar redshifts (4 _<_ _z_ _<_ 5), for which _L_ [C II] _/L_ IR = 7 [+4] _−_ 2 _[×]_ [ 10] _[−]_ [4]

(see compilation in Table B.1 of Lagache et al. 2018).
With log( _µ_ A _L_ [C II] _/L_ _⊙_ ) = 10 _._ 49 _±_ 0 _._ 05, we estimate
log( _µ_ A _L_ IR _/L_ _⊙_ ) = 13 _._ 48 _±_ 0 _._ 14 for AzTEC2-A. Likewise,
for AzTEC2-B we find log( _µ_ B _L_ [C II] _/L_ _⊙_ ) = 10 _._ 07 _±_ 0 _._ 10
and log( _µ_ B _L_ IR _/L_ _⊙_ ) = 13 _._ 07 _±_ 0 _._ 17. Although here we
neglect possible differences in the _L_ [C II] _/L_ IR ratio of
AzTEC2-A and AzTEC2-B arising from distinct physical conditions of the ISM (e.g., ultraviolet radiation
field and/or metal enrichment; Katz et al. 2017; Rybak
et al. 2019), these new and independent _L_ IR estimates
corroborate those derived via SED fitting.


We infer the SFR of both components following the
calibration from Kennicutt (1998): SFR[ _M_ _⊙_ yr _[−]_ [1] ]=
10 _[−]_ [10] _L_ IR [ _L_ _⊙_ ]. Assuming a Chabrier Initial Mass Function, we derive _µ_ A SFR = 2880 _±_ 140 _M_ _⊙_ yr _[−]_ [1] for
AzTEC2-A, while for AzTEC2-B we find _µ_ B SFR =

8 Jim´enez-Andrade et al.


10 [2]





10 [1]


10 [0]


10 [-1]


10 [-2]

|A TEC2<br>z|Col2|
|---|---|
|101|102<br>103<br>104<br>105<br>Observed wavelength [µm]|



**Figure** **3.** Broadband SED of AzTEC2. The monochromatic flux densities (blue circles) used in the fit correspond to the total
emission from both components (see values in Table 1). The best fit model is given by the black thick line. The dashed red
(dash-doted orange) line shows the model of the warm (cool) dust emission. The stellar emission is shown by the dotted green
line, while the radio continuum emission is represented by the dashed blue line.



960 _±_ 45 _M_ _⊙_ yr _[−]_ [1] . The lensing-corrected SFR of
AzTEC2-B (710 _±_ 35 _M_ _⊙_ yr _[−]_ [1] ) is consistent with the
average for SMGs at similar redshifts ( _∼_ 800 _M_ _⊙_ yr _[−]_ [1] ;
e.g., Smolˇci´c et al. 2015; G´omez-Guijarro et al.
2018; Jim´enez-Andrade et al. 2018; Magnelli et al.
2019). The extreme IR-based SFR of AzTEC2-A
(SFR=1920 _±_ 100 _M_ _⊙_ yr _[−]_ [1] ) is comparable to those of
the massive, star-forming disks GN20 and AzTEC1 at
_z_ _∼_ 4 _._ 5 (Carilli et al. 2010; Magnelli et al. 2012; Tadaki
et al. 2018).


On the other hand, we use our _M_ dust estimates
to infer the molecular gas mass of AzTEC2-A and
AzTEC2-B. We assume that these SMGs have solar

metallicity and, consequently, that they harbor a gasto-dust ratio of _δ_ GDR _∼_ 100 (following the _δ_ GDR –
metallicity relation derived by Leroy et al. (2011)).
Then, log( _µ_ A _M_ gas _/M_ _⊙_ ) _≃_ log( _µδ_ GDR _M_ dust _/M_ _⊙_ ) =
11 _._ 5 _±_ 0 _._ 1 for AzTEC2-A and log( _µ_ B _M_ gas _/M_ _⊙_ ) =
11 _._ 0 _±_ 0 _._ 1 for AzTEC2-B. These values are in good
agreement with the _M_ gas estimates derived from our
12
CO(5 _→_ 4) line observations assuming a mean _α_ CO of
2.5 _M_ _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2], which are log( _µ M_ gas _/M_ _⊙_ ) =
11 _._ 50 _±_ 0 _._ 05 and 10 _._ 90 _±_ 0 _._ 05 for AzTEC2-A and

AzTEC2-B, correspondingly.



4.4. _Mode_ _of_ _star_ _formation_ _in_ _AzTEC2_


The _L_ IR _/L_ _[′]_ CO(1 _→_ 0) [ratio] [gives] [an] [indication] [of] [how]
efficient the production of stars in galaxies is for a given
molecular gas reservoir. We estimate a _L_ IR _/L_ _[′]_ CO(1 _→_ 0)
ratio of 220 _±_ 50 _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for AzTEC2-A
and 300 _±_ 85 _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] for AzTEC2-B (see
Table 1). The star formation efficiency of AzTEC2-A
is larger than those of nearby and _z_ _∼_ 2 star-forming
disks (20 _−_ 100 _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] ; Daddi et al. 2010a;
Genzel et al. 2010), but it is in agreement with the
_L_ IR _/L_ _[′]_ CO(1 _→_ 0) [ratio] [of] _[z]_ _[∼]_ [4] _[.]_ [5] [star-forming] [disks] [like]
GN20 and AzTEC/C159 (180 _−_ 220 _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] ;
Hodge et al. 2012; Jim´enez-Andrade et al. 2018).


To better compare the star formation efficiency
of AzTEC2-A and AzTEC2-B with respect to the
overall SFG’s population, in Fig. 4 we present the
_L_ FIR _−_ _L_ _[′]_ CO(1 _→_ 0) [relation] [for] [star-forming] [disks] [and]
merger-driven starbursts derived by Genzel et al. (2010).
For this exercise, we estimate the far-IR (FIR) luminosity ( _L_ FIR ) of the AzTEC2 complex by integrating the
total IR SED (Fig. 3) over the wavelength range 42.5
– 122.5 _µ_ m (following Helou et al. 1985). Then, the
_L_ FIR of AzTEC2-A and AzTEC2-B are inferred from
the relative ratio of their dust-continuum flux density

The nature of the puzzling SMG AzTEC2 9


at 887 _µ_ m and 2924 _µ_ m (as done for _L_ IR in _§_ 4.3). We estimate log( _µ_ A _L_ FIR _/L_ _⊙_ ) = 13 _._ 08 _±_ 0 _._ 02 for AzTEC2-A,
and log( _µ_ B _L_ FIR _/L_ _⊙_ ) = 12 _._ 60 _±_ 0 _._ 02 for AzTEC2-B (see
Table 1). Combining these values with our _L_ _[′]_ CO(1 _→_ 0) [es-]
timates, we plot the locus of AzTEC2-A and AzTEC2-B
in the _L_ FIR _−_ _L_ _[′]_ CO(1 _→_ 0) [plane.] [We also include compila-]
tions of nearby normal and starburst galaxies (Solomon
et al. 1997; Gao & Solomon 2004), _z_ _∼_ 1 _._ 5 star-forming
disks (Daddi et al. 2010a; Geach et al. 2011; Magnelli
et al. 2012), SMGs (Bothwell et al. 2013), and massive star-forming disks at _z_ _∼_ 4 _._ 5 (Carilli et al. 2010;
Hodge et al. 2012; Jones et al. 2017; Jim´enez-Andrade
et al. 2018; Tadaki et al. 2018). This comparison indicates that most of the reported SMGs, like AzTEC2B, lie on/above the empirical _L_ FIR _−_ _L_ _[′]_ CO(1 _→_ 0) [rela-]
tion for mergers. Despite being at the high-end of the
_L_ FIR _−_ _L_ _[′]_ CO(1 _→_ 0) [plane,] [AzTEC2-A] [(as] [well] [as] [GN20]
and AzTEC1) approaches the relation of normal, starforming disk galaxies (see Fig. 4; e.g., Genzel et al.
2010).



Another indicator of star formation efficiency is the
_L_ IR _/L_ _[′]_ CO(5 _→_ 4) [ratio] [(e.g.,] Daddi et al. 2015), which
traces the dense, warm molecular gas ( _n_ _>_ 10 [4] cm _[−]_ [3] )
that is closely linked to massive star formation. We find
that AzTEC2-A (AzTEC2-B) exhibits a ratio that is 1.6
(2.5) larger than local star-forming and _z_ _∼_ 1 _._ 5 main
sequence (MS) galaxies (e.g., Liu et al. 2015). This
suggests that AzTEC2-A consumes its star-forming gas
faster than secular star-forming disks, but at a more
moderate rate than typical SMGs like AzTEC2-B.


Given their available gas reservoir, AzTEC2-A
(AzTEC2-B) will be able to sustain their current SFR
for a period of _∼_ 110 Myr (80 Myr) (assuming a mean
_α_ CO = 2 _._ 5 _M_ _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2] ). The gas depletion
time-scale ( _τ_ gas ) of AzTEC2-A, in particular, exhibit a
mild excess with respect to the average for SMGs at
similar redshifts ( _τ_ gas _∼_ 45 Myr; Aravena et al. 2016),
but resembles the one of the massive, star-forming disk
galaxies GN20, AzTEC/C159 and AzTEC1 at _z_ _∼_ 4 _._ 5
(Hodge et al. 2012; Jim´enez-Andrade et al. 2018; Tadaki
et al. 2018).


Overall, the properties of AzTEC2-A and AzTEC2-B
are consistent with the intense star formation activity
observed in bright SMGs at _z_ _∼_ 4 (Schinnerer et al.
2008; Riechers et al. 2010; Yun et al. 2015; Jim´enezAndrade et al. 2018; Tadaki et al. 2018). AzTEC2-A
resembles –to some extent– the properties of massive,
star-forming disks at lower and similar redshifts (e.g.,
Daddi et al. 2010a; Genzel et al. 2010; Hodge et al. 2012),



**Figure** **4.** FIR luminosity as a function of [12] CO(1 _→_ 0) line
luminosity for local and high-redshift SFGs. The squares represent nearby normal and starburst galaxies reported by Gao
& Solomon (2004), while stars correspond to low-redshift
ULIRGs in the sample of Solomon et al. (1997). The circles show _z_ _∼_ 1 _._ 5 star-forming disks presented in Daddi
et al. (2010a); Geach et al. (2011) and Magnelli et al. (2012).
The diamonds represent the parameter space covered by the
SMGs reported in Bothwell et al. (2013). Large symbols correspond to the SMGs studied here and the massive, rotating
disk galaxies at _z_ _∼_ 4 _._ 5: GN20, AzTEC1, and AzTEC/C159
(Carilli et al. 2010; Hodge et al. 2012; Jones et al. 2017;
Jim´enez-Andrade et al. 2018; Tadaki et al. 2018). In the
case of AzTEC2-A and AzTEC2-B, we use lensing-corrected
luminosities. If only _L_ IR measurements are available in the
literature, we convert _L_ IR into _L_ FIR by considering that
_⟨_ log( _L_ IR ) _⟩_ = 0 _._ 3 + _⟨_ log( _L_ FIR ) _⟩_ (e.g., Delhaize et al. 2017).
The dashed and dotted lines show the best-fitting relation for
MS and starburst galaxies, respectively, reported by Genzel
et al. (2010).


which form stars through the cold gas accretion mode
of star formation.


4.5. _A_ _rapidly_ _rotating,_ _massive_ _disk_ _in_ _AzTEC2-A_


Predictions from numerical simulations (e.g., Kohandel et al. 2019) and observations of high-redshift galaxies
(e.g., Jones et al. 2017) have suggested that a doublepeaked [C II] line profile, like that of AzTEC2-A (Fig.
2), can be consistent with a rotating disk galaxy. We
then use the high-resolution [C II] line observations to
explore the kinematics of AzTEC2-A, for which the high
SNR of the detection enables us to derive the velocity
field and velocity dispersion of the gas. As observed

RA (J2000)


**Figure** **5.** Velocity field ( _left_ _panel_ ) and velocity dispersion ( _central_ _panel_ ) of the gas in AzTEC2-A ( _z_ = 4 _._ 626), derived from

[CII] line observations with ALMA. Note that the velocity channels above 200 km s _[−]_ [1] are not available in the data set (see Fig.
2). The contour levels are at [ _−_ 350 _, −_ 300 _, −_ 250 _, −_ 100 _,_ 0 _,_ 100 _,_ 150] km s _[−]_ [1] and [25 _,_ 75 _,_ 100 _,_ 150 _,_ 200] km s _[−]_ [1] for the velocity field
and velocity dispersion maps, respectively. The synthesized beam is shown in the lower-left corner. The pv diagram ( _right_
_panel_ ) has been extracted using a 0.3 arcsec width aperture along the galaxy’s major-axis (position angle of _−_ 40 _[◦]_ ; black dashed
line). The blue-dashed line is a simple arctan model to describe the rotation curve of AzTEC2-A. The contour levels are at 3,
5 and 8 times the rms noise. The gray shaded region shows the velocity range that is not available in the current data set. The
horizontal bar shows the major axis of the synthesized beam.



in Fig. 5, AzTEC2-A exhibits a smooth velocity gradient that appears to be consistent with rotationally
dominated kinematics. ~~To~~ ~~parameterize~~ ~~its~~ ~~motion,~~
we derive the position-velocity (pv) diagram (Fig. 5)
along the major-axis of the [C II] line emission using a
0.3 arcsec width aperture.


There exist several parameterizations (or models)
that can describe the rotation curves of galaxies, including the basic 2-parameter arctan function, the more
elaborate “multi-parameter function” (Courteau 1997),
and the “universal rotation curve” (Persic et al. 1996).
The empirically motivated arctan model is given by
_v_ ( _r_ ) = (2 _/π_ ) _v_ asym arctan( _r/r_ t ) (e.g., Courteau 1997;
Willick 1999), where _v_ asym is the asymptotic rotational
velocity and _r_ t is the transition radius between the rising
and flat part of the rotation curve. With only two free
parameters, the arctan function provides an adequate
description to rotation curves of low- and high-redshift
galaxies (Courteau 1997; Willick 1999; Miller et al. 2011;
Swinbank et al. 2012; De Breuck et al. 2014; Drew et al.
2018), while avoiding strong covariances between the
fitted parameters of more complex models (Courteau
1997).


We thus adopt the arctan model to fit the rotation
curve of AzTEC2-A. As observed in Fig. 5, this function



offers a reasonable description of the observed portion
of the PV diagram. Our fit, limited by the lack of veloc~~ity channels above +200 km s~~ ~~_[−]_~~ ~~[1]~~ ~~, suggests a~~ n asymptotic
velocity of 415 _±_ 70 km s _[−]_ [1] and _µ_ A _r_ t = 0 _._ 7 _±_ 0 _._ 1 kpc. To
derive the intrinsic (de-projected) rotational velocity,
_v_ rot [int] [=] _[ v]_ [rot] _[/]_ [ sin(] _[i]_ [),] [we] [need] [to] [infer] [the] [disk] [inclination]
( _i_ ). This can be derived from the apparent ellipticity of
the galaxy: i.e., _i_ = arcsin(FWHM minor _/_ FWHM major ),
where the respective FWHM values can be derived from
the surface brightness distribution of the [C II] line.
However, as observed in Fig. 5, the absence of velocity
channels above +200 km s _[−]_ [1] biases the spatial distribution of the [C II] line emission. Assuming a co-spatial
distribution of interstellar dust and gas, the inclination
of the [C II] disk can be approximated from the ellipticity of the dust continuum emission revealed by our
high-resolution ALMA observations ( _§_ 4.2). We then
derive _i_ = arcsin(0 _._ 23 _±_ 0 _._ 02 _/_ 0 _._ 36 _±_ 0 _._ 02) = 39 _±_ 3 _[◦]_,
which leads to an intrinsic rotational velocity of
_v_ rot [int] [=] _[v]_ [asym] [=] [660] _[±]_ [130 km s] _[−]_ [1] [.] Such a high rotational speed is consistent with the one of the rapidly
spinning, star-forming disks GN20, AzTEC/C159 and
J1000+0234 at _z_ _∼_ 4 _._ 5 (≳ 500 km s _[−]_ [1] ; Carilli et al.
2010; Hodge et al. 2012; Jones et al. 2017).


To evaluate the rotational-to-dispersion support
( _v_ rot _/σ_ ) of the disk, we inspect the line-of-sight ve

The nature of the puzzling SMG AzTEC2 11



locity dispersion ( _σ_ ) map in Fig. 5. We anticipate that
at the innermost region of the galaxy, the measured _σ_
is highly enhanced by “beam smearing” [2] (e.g., Davies
et al. 2011; Stott et al. 2016). Since such a contribution is expected to be modest at the outermost radii,
we adopt 100 km s _[−]_ [1] (from the contour levels in the
map, Fig. 5) as an upper limit for the intrinsic velocity dispersion of the gas in the disk. Then, we derive
_v_ rot _/σ_ ≳ 5, indicating that AzTEC2-A is rather an unperturbed, rotation-dominated disk that resembles the
_v_ rot _/σ_ ratio of more evolved disk galaxies at _z_ _∼_ 1 (e.g.,
Di Teodoro et al. 2016, and references therein). This
finding, therefore, provides more evidence of kinematically mature disks that can be found at even _z_ _∼_ 4 _._ 5,
such as GN20 (Hodge et al. 2012), ALESS 73.1 (De
Breuck et al. 2014), AzTEC/C159, J1000+0234, (Jones
et al. 2017; Jim´enez-Andrade et al. 2018) and AzTEC1
(Tadaki et al. 2018).


Finally, by assuming that the kinematics of the
disk is mainly dominated by the gravitational potential of AzTEC2-A, its dynamical mass ( _M_ dyn ) can
be estimated through the relation: _M_ dyn sin [2] ( _i_ ) =
_Rv_ ( _R_ ) [2] _/G_, where _v_ ( _R_ ) is the rotation velocity at radius _R_ and _G_ is the gravitational constant. Using
_R_ = 0 _._ 5 arcsec that encompasses the full extent of
the [C II] line emission, and that equals the size of
the aperture used to obtain the spectrum, we find
_M_ dyn ( _i_ = 39 _[◦]_ ) = 2 _._ 6 [+1] _−_ 0 _[.]_ _._ [2] 9 _[×]_ [ 10] [11] _[M]_ _[⊙]_ [.] [This] [mass] [bud-]
get roughly agrees with that expected for the molecular gas mass ([0 _._ 7 _,_ 3 _._ 7] _×_ 10 [11] _M_ _⊙_ ), indicating that
AzTEC2-A is a massive gas-rich disk possibly assembled through an enhanced accretion of gas from the
cosmic web (e.g., Bournaud & Elmegreen 2009; Dekel
et al. 2009a,b; Romano-D´ıaz et al. 2014). A post-merger
scenario, however, can not be excluded, given that disks
could survive or re-form rather quickly after a gas-rich
merger (e.g., Springel & Hernquist 2005; Hammer et al.
2009; Hopkins et al. 2009). Simulated disk galaxies that
formed via gas-rich mergers can resemble the observed
properties (kinematics, SFR, gas surface density) of
_z_ _∼_ 2 disks (Robertson & Bullock 2008). Furthermore,
a coarse PSF (like ours, ≳ 1 kpc) diminishes the contrast
between disturbed kinematics and rotation-dominated
disks (Hung et al. 2016). Deeper [CII] line observations
with sub-kpc scale resolution are thus needed to accurately derive the kinematic properties of AzTEC2-A
and, hence, to isolate the formation scenario of its ro

2 At the innermost region of galaxies, the measured line width is
boosted by large-scale motions occurring within the region traced
by a relatively coarse (finite) Point Spread Function (PSF).



tating gas disk.


5. IMPLICATIONS FOR GALAXY EVOLUTION AT

HIGH REDSHIFT


The redshift identification and subsequent dynamical characterization of AzTEC2-A add new evidence on

the existence of massive vigorously star-forming disks
in the early Universe. By including AzTEC2-A, the
sample of SMGs at 4 _<_ _z_ _<_ 5 with robust evidence of
rotation has now increased to seven sources: AzTEC2A, AzTEC/C159, AzTEC1, Vd-17871, J1000+0234,
ALESS 73.1, and GN20 (Carilli et al. 2010; Hodge et al.
2012; De Breuck et al. 2014; Jones et al. 2017; Tadaki
et al. 2018). The former galaxies represent more than
half the population of spectroscopically confirmed _z_ _>_ 4
SMGs within the two square degrees of the COSMOS
field (Smolˇci´c et al. 2012, 2015). Here, we discuss the
implications of these findings within the context of cold
gas accretion and merger-driven star formation in massive, high-redshift galaxies.


5.1. _A_ _heterogeneous_ _SMG_ _population_


The enhanced production of stars in SMGs has been
largely attributed to gas-rich galaxy mergers (e.g., Tacconi et al. 2008; Younger et al. 2010; Engel et al. 2010;
Riechers et al. 2011; Iono et al. 2016), which is compatible with the merger-driven starbursts in local ULIRGs
(e.g., Sanders & Mirabel 1996). In the case of AzTEC2,
and as observed in Fig. 1, our current ALMA dust
continuum imaging does not reveal clear signs of disturbance/interaction between AzTEC2-A and AzTEC2B (e.g., strong tidal tails and/or bridges). Although
this could be a result of the surface brightness limit of
these observations, the clear spatial separation between
AzTEC2-A and AzTEC2-B ( _∼_ 20 kpc) and the relative
velocity offset of 350 km s _[−]_ [1] suggest that these galaxies
undergo a pre-coalescence (first approach) phase (e.g.,
Calder´on-Castillo et al. 2019). This might indicate
that the vigorous SFR in AzTEC2-A is not dominated
by merging activity. Instead, the gas velocity fields,
_L_ FIR _/L_ _[′]_ CO(1 _→_ 0) [,] [and] _[L]_ [IR] _[/L]_ _[′]_ CO(5 _→_ 4) [ratio] [point] [towards]
a smoother mode of star formation that drives a massive, star-forming disk (e.g., Dekel et al. 2009a,b; Carilli
et al. 2010; Hodge et al. 2012; Romano-D´ıaz et al. 2014).
Certainly, the properties of AzTEC2 resemble those of
the well-characterized star-forming disk GN20 at similar
redshift (Carilli et al. 2010; Hodge et al. 2012).


These results strengthen the scenario in which singledish selected SMGs are a heterogeneous population (e.g.,

12 Jim´enez-Andrade et al.



Hayward et al. 2011, 2013), including major mergers
(e.g., Engel et al. 2010; Riechers et al. 2014), isolated
disk galaxies and pairs of (likely infalling) galaxies that
are blended into a single sub-mm source as observed in
AzTEC2. As discussed by Hayward et al. (2011), this
heterogeneity is linked to the SMG selection function.
Since sub-mm surveys lead to flux ( _∝_ SFR) limited samples of galaxies (e.g., Scott et al. 2008; Aretxaga et al.
2011), at high redshift ( _z_ ≳ 3), only SFGs harboring a
SFR≳ 300 _M_ _⊙_ yr _[−]_ [1] can be selected with typical singledish surveys (e.g., Magnelli et al. 2019). Therefore, this
selection function tends to identify the extreme and massive end of the SFG population at high redshifts, including both merger-driven and massive star-forming disks
that sustain vigorous star formation activity leading to
SMG-like IR luminosities (e.g., Hayward et al. 2012).


5.2. _The_ _cold_ _gas_ _accretion_ _and_ _merger_ _mode_ _of_ _star_
_formation_ _at_ _z_ _>_ 3


The evidence of rotation-dominated, gas-rich, starforming disks at _z_ _>_ 4 (e.g., Carilli et al. 2010; Hodge
et al. 2012; De Breuck et al. 2014; Jones et al. 2017;
Tadaki et al. 2018) indicates that high-redshift SMGs
are not only merging, strongly perturbed systems (Tacconi et al. 2008; Younger et al. 2010; Engel et al. 2010;
Riechers et al. 2011; Men´endez-Delmestre et al. 2014;
Chen et al. 2015; Jones et al. 2017; Chang et al. 2018).
High-resolution (0.07 arcsec) dust continuum imaging
with ALMA has even shown evidence for spiral arms,
bars, and rings in _z_ ≳ 2 SMGs (Hodge et al. 2019).
The remaining question is what are the mechanisms
leading to the intense production of stars in such massive, star-forming disks in the early Universe. We thus
infer the locus of AzTEC2-A (and AzTEC2-B) in the
Kennicutt-Schmidt plane (Fig. 6) and use them as an
observational diagnostic for constraining the global conditions for star formation in these systems.


We use the spatial extent of the dust continuum
emission from our ALMA observations (see _§_ 4.2)
to infer the galaxy-averaged SFR surface density:
Σ SFR _≡_ SFR _/_ (2 _πR_ eff [2] [).] The effective radius containing half of the total emission, _R_ eff, is approximated as
_R_ eff _∼_ FWHM _/_ 2 _._ 430 (Murphy et al. 2017), assuming
an exponentially declining surface brightness distribution as observed in disk galaxies. In order to approximate the galaxy-averaged molecular gas surface density
(Σ gas _≡_ _M_ gas _/_ (2 _πR_ eff [2] [)), we use our] _[ M]_ [gas] [ estimate based]
on _L_ _[′]_ CO(1 _→_ 0) [(] _[§]_ [4.3][) and] _[ α]_ [CO] [= 2] _[.]_ [5 M] _[⊙]_ [K] _[−]_ [1] [ km] _[−]_ [1] [ s pc] _[−]_ [2] [.]
Although the rotation-dominated gas disk of AzTEC2A favors a higher _α_ CO value (e.g., Papadopoulos
et al. 2012a,b; Jim´enez-Andrade et al. 2018), we re








2.5 3.0 3.5 4.0 4.5 5.0

log(Σ gas [M ⊙ pc [−][2] ])


**Figure** **6.** AzTEC2-A and AzTEC2-B in the KennicuttSchmidt (Σ SFR _−_ Σ gas ) plane. For comparison, the massive, star-forming disks at _z_ _∼_ 4 _._ 5 GN20 (Carilli et al.
2010; Hodge et al. 2012), AzTEC/C159 (Jones et al. 2017;
Jim´enez-Andrade et al. 2018), and AzTEC1 (Tadaki et al.
2018) are also shown, along with a compilation of typical
SFGs over 1 ≲ _z_ ≲ 2 _._ 5 and SMGs over 1 ≲ _z_ ≲ 3 _._ 5
(Genzel et al. 2010, and references therein). In estimating
Σ SFR and Σ gas of _z_ _∼_ 4 _._ 5 star-forming disks we use their
effective radius from dust continuum emission and adopt
_α_ CO = 2 _._ 5 M _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2], except for AzTEC/C159
for which _α_ CO = 4 M _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2] has been previously constrained. The horizontal error bars also take
into account the Σ gas range given by an _α_ CO varying over
0 _._ 8 _−_ 4 _._ 3 M _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2] . The solid blue (dashed red)
line illustrates the KS relation for typical SFGs (mergers)
over the redshift range 1 ≲ _z_ ≲ 3 derived by Genzel et al.
(2010). The gray diagonal lines show the Σ SFR required to
consume the available gas reservoirs within a gas depletion
time-scale ( _τ_ gas ) of 10 Myr (upper), 100 Myr (middle), and
1000 Myr (lower). The gray shaded regions illustrate the
_τ_ gas range for galaxies with (from top-to-bottom) high-tolow SFE.


quire more robust constraints (e.g., dynamical mass,
metallicity, excitation conditions) to validate this scenario. We thus consider the uncertainties of Σ gas associated to the unknown _α_ CO value by illustrating in
Fig. 6 the Σ gas range given by _α_ CO varying from 0.8 to
4 _._ 3 M _⊙_ K _[−]_ [1] km _[−]_ [1] s pc _[−]_ [2] . We also recall that in deriving
_L_ _[′]_ [and] [hence] _[M]_ [gas] [,] [we] [have] [assumed] [typical]
CO(1 _→_ 0) [,]
SMG-like gas excitation conditions, as previously ob

The nature of the puzzling SMG AzTEC2 13



served in other massive, highly star-forming rotating
disks like GN20 and AzTEC/C159 (Carilli et al. 2010;
Hodge et al. 2012; Jim´enez-Andrade et al. 2018). By
combining our Σ gas and Σ SFR estimates we find that
AzTEC2-A lies at the upper end of the KennicuttSchmidt relation for typical SFGs (Fig. 6 Genzel et al.
2010). This is consistent with the properties of the
massive, star-forming disks GN20 (Carilli et al. 2010;
Hodge et al. 2012) and AzTEC/C159 (Jones et al. 2017;
Jim´enez-Andrade et al. 2018) at similar redshift. These
systems arise as scaled (more active) versions of starforming disks at lower redshifts (1 ≲ _z_ ≲ 2 _._ 5 e.g.,
Daddi et al. 2010a,b; Genzel et al. 2010, and references
therein). Qualitatively, this is in agreement with the
systematically higher gas fractions (e.g., Genzel et al.
2015; Schinnerer et al. 2016; Tacconi et al. 2018; Liu
et al. 2019) and enhanced specific SFR of galaxies with
increasing redshift (e.g., Karim et al. 2011; Speagle
et al. 2014; Schreiber et al. 2015; Lehnert et al. 2015).


Fig. 6 also suggests that massive, star-forming disks
like AzTEC2-A, GN20, and AzTEC/C159 seem to harbor a systematically lower gas depletion time-scale than
their analogs at lower redshifts; which is compatible
with the redshift evolution of _τ_ gas of massive MS galaxies (e.g., Saintonge et al. 2013; Schinnerer et al. 2016;
Tacconi et al. 2018; Liu et al. 2019). Such an efficient regime of star formation, that approaches that of
merger-driven starbursts (Fig. 6), could be explained by
the turbulent ISM and rapid dynamical evolution that
characterize high-redshift disks (e.g., F¨orster Schreiber
et al. 2009; Bournaud et al. 2012; Swinbank et al. 2012).
In this context, the enhanced stellar birth rate of early
star-forming disks is a result of their inherent large gas
reservoirs and –to some extent– a higher star formation
efficiency ( _≡_ 1 _/τ_ gas ). Numerical simulations predict
that at _z_ _>_ 4 the enhanced gas accretion from the cosmic web can maintain a gravitationally unstable gas-rich
disk, which breaks into giant clumps and forms stars at
a high rate (Bouch´e et al. 2007; Hodge et al. 2012;
Romano-D´ıaz et al. 2014). Additionally, star formation
in AzTEC2-A might be further enhanced due gravitational interaction (torques) with its (minor) companion
galaxy, AzTEC2-B, during the ongoing pre-coalescence
phase – as inferred from hydrodynamic merger simulations (e.g., Cox et al. 2008; Moreno et al. 2015)
and observations of galaxy pairs (Scudder et al. 2012).
Although evidence of such tidal interactions could be
inferred from an asymmetric (perturbed) velocity field
of the gas (e.g., Kronberger et al. 2007), the incomplete
coverage of the [C II] velocity field of AzTEC2-A pre


vent us from confirming this scenario.


6. SUMMARY


We have used multi-wavelength spectroscopic and
photometric data to constrain the redshift and conditions for star formation in AzTEC2: the second brightest SMG (at 1.1 and 2 mm) in the COSMOS field. Our
results are listed below:


_•_ AzTEC2 splits into two components (AzTEC2-A
and AzTEC2-B) for which we detect [12] CO(5 _→_ 4)
and [CII] line emission, leading to a redshift of
4 _._ 626 _±_ 0 _._ 001 and 4 _._ 633 _±_ 0 _._ 001 for AzTEC2-A and

AzTEC2-B, respectively;


_•_ The emission of AzTEC2-A and AzTEC2-B is

mildly magnified by a foreground, massive elliptical galaxy at _z_ = 0 _._ 34 located at _∼_ 4 arcsec to
the south of AzTEC2-A,B. We estimate a magnification factor of _µ_ A = 1 _._ 5 and _µ_ B = 1 _._ 35 for
AzTEC2-A and AzTEC2-B, respectively;


_•_ Based on the [12] CO(5 _→_ 4) line emission of AzTEC2A we have derived _µ_ A _L_ _[′]_ CO(1 _→_ 0) = (12 _._ 8 _±_
2 _._ 4) _×_ 10 [10] K km s _[−]_ [1] pc [2], implying a molecular
gas mass of _µ_ A _M_ gas = (1 _._ 0 _−_ 5 _._ 5) _×_ 10 [11] _M_ _⊙_ .
The FIR luminosity of AzTEC2-A leads to
_µ_ A SFR = (2880 _±_ 140) _M_ _⊙_ yr _[−]_ [1], _L_ IR _/L_ _[′]_ CO(1 _→_ 0)
ratio of 220 _±_ 50 _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1], and _τ_ gas =
(35 _−_ 190) Myr;


_•_ Correspondingly, for AzTEC2-B we have found
that _µ_ B _L_ _[′]_ CO(1 _→_ 0) [= (3] _[.]_ [1] _[±]_ [0] _[.]_ [7)] _[×]_ [10] [10] [ K km s] _[−]_ [1] [ pc] [2] [,]
_µ_ B _M_ gas = (0 _._ 25 _−_ 1 _._ 3) _×_ 10 [11] _M_ _⊙_, _µ_ B SFR =
960 _±_ 45 _M_ _⊙_ yr _[−]_ [1], _L_ IR _/L_ _[′]_ CO(1 _→_ 0) = 310 _±_
80 _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1], and _τ_ gas = (25 _−_ 140) Myr;


_•_ We have revealed a rotation-dominated [CII] disk
in AzTEC2-A, with an intrinsic (de-projected)
rotational velocity of _v_ rot ( _i_ = 39 _[◦]_ ) = 660 _±_
130 km s _[−]_ [1], velocity dispersion of _σ_ ≲ 100 km s _[−]_ [1]

and dynamical mass of _M_ dyn ( _i_ = 39 _[◦]_ ) = 2 _._ 6 [+1] _−_ 0 _[.]_ _._ [2] 9 _[×]_
10 [11] _M_ _⊙_ .


Our results indicate that AzTEC2-A hosts a massive,
rotation-dominated disk where star formation occurs at

intense levels. This indicates that even disk galaxies,
that harbor vast gas reservoirs, could sustain intense
star formation activity that resembles that of mergerdriven SMGs. This supports the emerging consensus
whereby the population of single-dish selected SMGs
is rather heterogeneous, including both interacting systems and galaxies that form stars through a smoother

14 Jim´enez-Andrade et al.



mode of star formation sustained by cold gas accretion.
A more systematic study of high-redshift star-forming
disks is required to verify this scenario, allowing us to
probe their properties within the framework of the cold
and merger mode of star formation in the early Universe.


We thank the reviewer for their careful reading of
the manuscript and their constructive comments. We
thank Justin Spilker for assistance with the gravitational
lens modeling. E.F.J.A, B.M., E.R.D., A.K., K.C.H.,
and F.B. acknowledge support of the Collaborative Research Center 956, subproject A1 and C4, funded by
the Deutsche Forschungsgemeinschaft (DFG). CMC
thanks the National Science Foundation for support
through grants AST-1714528 and AST-1814034, and
acknowledges support from the Research Corporation
for Science Advancement from a 2019 Cottrell Scholar
Award sponsored by IF/THEN, an initiative of Lyda
Hill Philanthropies. CMC and JAZ also thank the University of Texas at Austin College of Natural Sciences
for support. DL acknowledges support and funding from
the European Research Council (ERC) under the Euro


pean Union’s Horizon 2020 research and innovation program (grant agreement No. 694343). I.A. acknowledges
support from the CONACyT projects FDC-2016-1828
and CB-2016-281948. A.M. acknowledges support from
the CONACyT project A1-S-45680. This paper makes
use of the following ALMA data: ADS/JAO.ALMA
2015.1.00568.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO, and
NAOJ. This work is based on observations carried out

under project number W18EU with the IRAM NOEMA
Interferometer. IRAM is supported by INSU/CNRS
(France), MPG (Germany) and IGN (Spain). The National Radio Astronomy Observatory is a facility of the
National Science Foundation operated under cooperative agreement by Associated Universities, Inc.


_Facilities:_ Atacama Large Millimeter Array (ALMA),
NOrthern Extended Millimeter Array (NOEMA)



APPENDIX


A. PROPERTIES OF AZTEC2

The nature of the puzzling SMG AzTEC2 15


**Table** **1.** Properties of AzTEC2


**Properties** **Units** **AzTEC2-A** **AzTEC2-B**


12 12
CO(5 _→_ 4) [CII] CO(5 _→_ 4) [CII]


FWHM km s _[−]_ [1] 890 _±_ 150 . . . 650 _±_ 150 . . .


Peak flux mJy/beam 1.2 _±_ 0.2 13 _±_ 1 0.4 _±_ 0.1 6 _±_ 2

_µ_ Integrated flux Jy km s _[−]_ [1] 1.07 _±_ 0.06 _[a]_ 10 _._ 9 _±_ 1 _._ 2 0.26 _±_ 0.03 _[a]_ 4 _._ 2 _±_ 0 _._ 9


Central frequency GHz 102.43 _±_ 0.03 337 _._ 8 _±_ 0 _._ 2 102.30 _±_ 0.02 337 _._ 4 _±_ 0 _._ 2


_z_ _[b]_ _. . ._ 4.626 _±_ 0.001 4.633 _±_ 0.001


_µ_ _. . ._ 1.5 1.35


RA, Dec hh:mm:ss.sss, dd:mm:ss.ss 10:00:08.042 +02:26:12.19 10:00:07.842 +02:26:13.32
~~_√_~~ _µ_ FWHM major[CII] _−_ axis arcsec/kpc 0 _._ 70 _±_ 0 _._ 12/4 _._ 6 _±_ 1 _._ 0 0 _._ 53 _±_ 0 _._ 18/3 _._ 4 _±_ 1 _._ 2
~~_√_~~ _µ_ FWHM 12 majorCO(5 _−_ axis _→_ 4) arcsec/kpc 1 _._ 2 _±_ 0 _._ 4/7 _._ 8 _±_ 2 _._ 6 _. . ._
major _−_ axis
~~_√_~~ _µ_ FWHM dust arcsec/kpc 0 _._ 36 _±_ 0 _._ 02/2 _._ 3 _±_ 0 _._ 1 0 _._ 35 _±_ 0 _._ 04/2 _._ 3 _±_ 0 _._ 3

_µ L_ IR _L_ _⊙_ (2 _._ 88 _±_ 0 _._ 13) _×_ 10 [13] (9 _._ 60 _±_ 0 _._ 45) _×_ 10 [12]

_µ L_ FIR _L_ _⊙_ (1 _._ 20 _±_ 0 _._ 06) _×_ 10 [13] (0 _._ 40 _±_ 0 _._ 02) _×_ 10 [13]

_µ L_ [CII] _L_ _⊙_ (3 _._ 09 _±_ 0 _._ 37) _×_ 10 [10] (1 _._ 17 _±_ 0 _._ 30) _×_ 10 [10]


_c_
_µ L_ _[′]_ CO(5 _→_ 4) K km s _[−]_ [1] pc [2] (4 _._ 1 _±_ 0 _._ 2) _×_ 10 [10] (1 _._ 0 _±_ 0 _._ 1) _×_ 10 [10]

_µ L_ _[′]_ CO(1 _→_ 0) K km s _[−]_ [1] pc [2] (12 _._ 8 _±_ 2 _._ 4) _×_ 10 [10] (3 _._ 1 _±_ 0 _._ 7) _×_ 10 [10]

_L_ IR _/L_ _[′]_ CO(1 _→_ 0) _L_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] 220 _±_ 50 310 _±_ 80

_µ_ SFR _M_ _⊙_ yr _[−]_ [1] 2880 _±_ 140 960 _±_ 45


_µ M_ gas ( _α_ CO = 0 _._ 8 _, α_ CO = 4 _._ 3) _M_ _⊙_ (1 _._ 0 _±_ 0 _._ 2 _,_ 5 _._ 5 _±_ 1 _._ 0) _×_ 10 [11] (0 _._ 25 _±_ 0 _._ 05 _,_ 1 _._ 3 _±_ 0 _._ 3) _×_ 10 [11]

_µ M_ dust _M_ _⊙_ (3 _._ 2 _±_ 0 _._ 1) _×_ 10 [9] (1 _._ 07 _±_ 0 _._ 03) _×_ 10 [9]


_τ_ gas ( _α_ CO = 0 _._ 8 _, α_ CO = 4 _._ 3) Myr (35 _±_ 7 _,_ 190 _±_ 33) (25 _±_ 6 _,_ 140 _±_ 30)


_µ S_ 21cm _[d]_ mJy 0 _._ 045 _±_ 0 _._ 03 0 _._ 039 _±_ 0 _._ 02


_µ S_ 10cm _[e]_ mJy 0 _._ 035 _±_ 0 _._ 06 0 _._ 025 _±_ 0 _._ 06


_µ S_ 2924 _µ_ m mJy 0 _._ 33 _±_ 0 _._ 05 0 _._ 09 _±_ 0 _._ 02
_µ S_ 2000 _[f]_ _µ_ m mJy 1 _._ 09 _±_ 0 _._ 22
_µ S_ 1100 _[g]_ _µ_ m mJy 11 _._ 5 _±_ 1 _._ 4
_µ S_ 887 _µ_ m mJy 13 _._ 3 _±_ 0 _._ 5 4 _._ 5 _±_ 0 _._ 5
_µ S_ 850 _[h]_ _µ_ m mJy 15 _._ 8 _±_ 1 _._ 6
_µ S_ 500 _[i]_ _µ_ m mJy 37 _._ 5 _±_ 3 _._ 7
_µ S_ 350 _[i]_ _µ_ m mJy 30 _._ 9 _±_ 3 _._ 5
_µ S_ 250 _[i]_ _µ_ m mJy 24 _._ 9 _±_ 2 _._ 5
_µ S_ 160 _[j]_ _µ_ m mJy 17 _._ 3 _±_ 7 _._ 1
_µ S_ 100 _[j]_ _µ_ m mJy 6 _._ 79 _±_ 2 _._ 50
_µ S_ 24 _[k]_ _µ_ m mJy 0 _._ 195 _±_ 0 _._ 019


Note— _[a]_ These observed flux densities will increase by a factor [1/0.8] when considering the effect of the CMB. We use the
corrected value, i.e., _µ S_ CO(5 [intrinsic] _→_ 4) [= 1] _[.]_ [34] _[ ±]_ [ 10 Jy km s] _[−]_ [1] [and] [325] _[ ±]_ [ 40 mJy km s] _[−]_ [1] [for] [AzTEC2-A] [and] [AzTEC2-B,] [respectively.] _[b]_

Redshift derived from [12] CO(5 _→_ 4) line measurements. _[c]_ The effect of the CMB is considered when deriving this value (see
_§_ 4.3). _[d]_ Schinnerer et al. (2010) _[e]_ Smolˇci´c et al. (2017) _[f]_ Magnelli et al. (2019) _[g]_ Aretxaga et al. (2011) _[h]_ Geach et al. (2016)
_i_ Oliver et al. (2012) _j_ Lutz et al. (2011) _k_ Le Floc’h et al. (2009).

16 Jim´enez-Andrade et al.


REFERENCES



Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016,

MNRAS, 457, 4406. https:

[//academic.oup.com/mnras/article/457/4/4406/2589079](https://academic.oup.com/mnras/article/457/4/4406/2589079)


Aretxaga, I., Wilson, G. W., Aguilar, E., et al. 2011,

MNRAS, 415, 3831. http:

[//mnras.oxfordjournals.org/content/415/4/3831.abstract](http://mnras.oxfordjournals.org/content/415/4/3831.abstract)


Auger, M. W., Treu, T., Bolton, A. S., et al. 2009, ApJ,

705, 1099.

[http://dx.doi.org/10.1088/0004-637X/705/2/1099](http://dx.doi.org/10.1088/0004-637X/705/2/1099)


Barger, A. J., Wang, W.-H., Cowie, L. L., et al. 2012, ApJ,

761, 89. [http://stacks.iop.org/0004-637X/761/i=2/a=89](http://stacks.iop.org/0004-637X/761/i=2/a=89)


Blain, A. W., Smail, I., Ivison, R. J., Kneib, J.-P., &

Frayer, D. T. 2002, Phys. Rep., 369, 111.

[https://www.sciencedirect.com/science/article/abs/pii/](https://www.sciencedirect.com/science/article/abs/pii/S0370157302001345?via%3Dihub)

[S0370157302001345?via%3Dihub](https://www.sciencedirect.com/science/article/abs/pii/S0370157302001345?via%3Dihub)


Bothwell, M. S., Chapman, S. C., Tacconi, L., et al. 2010,

MNRAS, 405, 219.

[https://doi.org/10.1111/j.1365-2966.2010.16480.x](https://doi.org/10.1111/j.1365-2966.2010.16480.x)


Bothwell, M. S., Aguirre, J. E., Chapman, S. C., et al.

2013, ApJ, 779, 67.

[http://dx.doi.org/10.1088/0004-637X/779/1/67](http://dx.doi.org/10.1088/0004-637X/779/1/67)


Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013,

MNRAS, 429, 3047. https:

[//academic.oup.com/mnras/article/429/4/3047/1011515](https://academic.oup.com/mnras/article/429/4/3047/1011515)


Bouch´e, N., Murphy, M. T., Kacprzak, G. G., et al. 2013,

Science, 341, 50. http:

[//science.sciencemag.org/content/341/6141/50.abstract](http://science.sciencemag.org/content/341/6141/50.abstract)


Bouch´e, N., Cresci, G., Davies, R., et al. 2007, ApJ, 671,

303. [http://stacks.iop.org/0004-637X/671/i=1/a=303](http://stacks.iop.org/0004-637X/671/i=1/a=303)


Bournaud, F., & Elmegreen, B. G. 2009, ApJL, 694, L158.


[http://dx.doi.org/10.1088/0004-637X/694/2/L158](http://dx.doi.org/10.1088/0004-637X/694/2/L158)


Bournaud, F., Juneau, S., Floc’h, E. L., et al. 2012, ApJ,

757, 81. https:

[//doi.org/10.1088%2F0004-637x%2F757%2F1%2F81](https://doi.org/10.1088%2F0004-637x%2F757%2F1%2F81)


Brisbin, D., Miettinen, Oskari, Aravena, Manuel, et al.

2017, A&A, 608, A15.

[https://doi.org/10.1051/0004-6361/201730558](https://doi.org/10.1051/0004-6361/201730558)


Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000.


[http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x](http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x)


Ca˜nameras, R., Yang, C., Nesvadba, N. P. H., et al. 2018,

A&A, 620, A61.

[https://doi.org/10.1051/0004-6361/201833625](https://doi.org/10.1051/0004-6361/201833625)


Calder´on-Castillo, P., Nagar, N. M., Yi, S., et al. 2019,

A&A, in press., arXiv:1904.09300


Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105.


[https://www.annualreviews.org/doi/10.1146/](https://www.annualreviews.org/doi/10.1146/annurev-astro-082812-140953)

[annurev-astro-082812-140953](https://www.annualreviews.org/doi/10.1146/annurev-astro-082812-140953)



Carilli, C. L., Daddi, E., Riechers, D., et al. 2010, ApJ, 714,

1407. [http://iopscience.iop.org/article/10.1088/](http://iopscience.iop.org/article/10.1088/0004-637X/714/2/1407/meta)
[0004-637X/714/2/1407/meta](http://iopscience.iop.org/article/10.1088/0004-637X/714/2/1407/meta)

Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys.
Rev, 541, 45. [https://www.sciencedirect.com/science/](https://www.sciencedirect.com/science/article/abs/pii/S0370157314000477?via%3Dihub)
[article/abs/pii/S0370157314000477?via%3Dihub](https://www.sciencedirect.com/science/article/abs/pii/S0370157314000477?via%3Dihub)

Casey, C. M., Chen, C.-C., Cowie, L. L., et al. 2013,

MNRAS, 436, 1919.

[http://dx.doi.org/10.1093/mnras/stt1673](http://dx.doi.org/10.1093/mnras/stt1673)

Casey, C. M., Cooray, A., Killi, M., et al. 2017, ApJ, 840,
101. [http://stacks.iop.org/0004-637X/840/i=2/a=101](http://stacks.iop.org/0004-637X/840/i=2/a=101)

Chang, Y.-Y., Ferraro, N., Wang, W.-H., et al. 2018, 865,
103. [http://dx.doi.org/10.3847/1538-4357/aadd18](http://dx.doi.org/10.3847/1538-4357/aadd18)

Chen, C.-C., ALESS, & ALMA-S2CLSconsortia. 2015, in

Revolution in astronomy with ALMA: the third year, ed.

D. Iono, K. Tatematsu, A. Wootten, & L. Testi, Vol. 499.

[http://aspbooks.org/custom/publications/paper/](http://aspbooks.org/custom/publications/paper/499-0013.html)

[499-0013.html](http://aspbooks.org/custom/publications/paper/499-0013.html)

Courteau, S. 1997, AJ, 114, 2402. http:

[//articles.adsabs.harvard.edu/full/1997AJ....114.2402C](http://articles.adsabs.harvard.edu/full/1997AJ....114.2402C)

Cox, T. J., Jonsson, P., Somerville, R. S., Primack, J. R., &

Dekel, A. 2008, MNRAS, 384, 386

da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766,

13. [http://stacks.iop.org/0004-637X/766/i=1/a=13](http://stacks.iop.org/0004-637X/766/i=1/a=13)

Daddi, E., Bournaud, F., Walter, F., et al. 2010a, ApJ, 713,

686. [http://stacks.iop.org/0004-637X/713/i=1/a=686](http://stacks.iop.org/0004-637X/713/i=1/a=686)

Daddi, E., Elbaz, D., Walter, F., et al. 2010b, ApJ, 714,

L118. [http://dx.doi.org/10.1088/2041-8205/714/1/L118](http://dx.doi.org/10.1088/2041-8205/714/1/L118)

Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577,

A46. [https://www.aanda.org/articles/aa/abs/2015/05/](https://www.aanda.org/articles/aa/abs/2015/05/aa25043-14/aa25043-14.html)
[aa25043-14/aa25043-14.html](https://www.aanda.org/articles/aa/abs/2015/05/aa25043-14/aa25043-14.html)

Dav´e, R., Finlator, K., Oppenheimer, B. D., et al. 2010,

MNRAS, 404, 1355.

[http://dx.doi.org/10.1111/j.1365-2966.2010.16395.x](http://dx.doi.org/10.1111/j.1365-2966.2010.16395.x)

Davies, R., Schreiber, N. M. F., Cresci, G., et al. 2011,

ApJ, 741, 69. https:

[//doi.org/10.1088%2F0004-637x%2F741%2F2%2F69](https://doi.org/10.1088%2F0004-637x%2F741%2F2%2F69)

De Breuck, C., Williams, R. J., Swinbank, M., et al. 2014,

A&A, 565, A59.

[http://dx.doi.org/10.1051/0004-6361/201323331](http://dx.doi.org/10.1051/0004-6361/201323331)

Dekel, A., Sari, R., & Ceverino, D. 2009a, ApJ, 703, 785.


[http://stacks.iop.org/0004-637X/703/i=1/a=785](http://stacks.iop.org/0004-637X/703/i=1/a=785)

Dekel, A., Birnboim, Y., Engel, G., et al. 2009b, Nature,
457, 451. [http://dx.doi.org/10.1038/nature07648](http://dx.doi.org/10.1038/nature07648)

Delhaize, J., Smolˇci´c, V., Delvecchio, I., et al. 2017, A&A,

602, A4. [https://doi.org/10.1051/0004-6361/201629430](https://doi.org/10.1051/0004-6361/201629430)

Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016,

A&A, 594, A77.

[https://doi.org/10.1051/0004-6361/201628315](https://doi.org/10.1051/0004-6361/201628315)

The nature of the puzzling SMG AzTEC2 17



Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615.


[http://stacks.iop.org/0004-637X/507/i=2/a=615](http://stacks.iop.org/0004-637X/507/i=2/a=615)

Draine, B. T., & Li, A. 2007, ApJ, 657, 810.


[http://stacks.iop.org/0004-637X/657/i=2/a=810](http://stacks.iop.org/0004-637X/657/i=2/a=810)

Drew, P. M., Casey, C. M., Burnham, A. D., et al. 2018,

ApJ, 869, 58.

[https://doi.org/10.3847%2F1538-4357%2Faaedbf](https://doi.org/10.3847%2F1538-4357%2Faaedbf)

Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616,
A110. [https://doi.org/10.1051/0004-6361/201732370](https://doi.org/10.1051/0004-6361/201732370)

Ellison, S. L., Mendel, J. T., Scudder, J. M., Patton, D. R.,

& Palmer, M. J. D. 2013, MNRAS, 430, 3128.

[https://doi.org/10.1093/mnras/sts546](https://doi.org/10.1093/mnras/sts546)

Engel, H., Tacconi, L. J., Davies, R. I., et al. 2010, ApJ,

724, 233.

[http://stacks.iop.org/0004-637X/724/i=1/a=233;http:](http://stacks.iop.org/0004-637X/724/i=1/a=233; http://adsabs.harvard.edu/abs/2010ApJ...724..233E)
[//adsabs.harvard.edu/abs/2010ApJ...724..233E](http://stacks.iop.org/0004-637X/724/i=1/a=233; http://adsabs.harvard.edu/abs/2010ApJ...724..233E)

Erickson, N., Narayanan, G., Goeller, R., & Grosslein, R.

2007, in Astronomical Society of the Pacific Conference

Series, Vol. 375, From Z-Machines to ALMA:

(Sub)Millimeter Spectroscopy of Galaxies, ed. A. J.

Baker, J. Glenn, A. I. Harris, J. G. Mangum, & M. S.
Yun, 71. [http://aspbooks.org/custom/publications/](http://aspbooks.org/custom/publications/paper/375-0071.html)
[paper/375-0071.html](http://aspbooks.org/custom/publications/paper/375-0071.html)

F¨orster Schreiber, N. M., Genzel, R., Bouch´e, N., et al.

2009, ApJ, 706, 1364.

[http://dx.doi.org/10.1088/0004-637X/706/2/1364](http://dx.doi.org/10.1088/0004-637X/706/2/1364)

Fudamoto, Y., Ivison, R. J., Oteo, I., et al. 2017, MNRAS,

472, 2028. [http://dx.doi.org/10.1093/mnras/stx1956](http://dx.doi.org/10.1093/mnras/stx1956)

Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271.


[https://doi.org/10.1086%2F382999](https://doi.org/10.1086%2F382999)

Geach, J. E., Smail, I., Moran, S. M., et al. 2011, ApJL,

730, L19. [https://iopscience.iop.org/article/10.1088/](https://iopscience.iop.org/article/10.1088/2041-8205/730/2/L19)
[2041-8205/730/2/L19](https://iopscience.iop.org/article/10.1088/2041-8205/730/2/L19)

Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2016, ArXiv

e-prints, arXiv:1607.03904

Geach, J. E., Narayanan, D., Matsuda, Y., et al. 2016, ApJ,
832, 37. [http://stacks.iop.org/0004-637X/832/i=1/a=37](http://stacks.iop.org/0004-637X/832/i=1/a=37)

Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010,

MNRAS, 407, 2091. https:

[//academic.oup.com/mnras/article/407/4/2091/998428](https://academic.oup.com/mnras/article/407/4/2091/998428)

Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800,

20. [https://iopscience.iop.org/article/10.1088/](https://iopscience.iop.org/article/10.1088/0004-637X/800/1/20)
[0004-637X/800/1/20](https://iopscience.iop.org/article/10.1088/0004-637X/800/1/20)

Gobat, R., Strazzullo, V., Daddi, E., et al. 2012, ApJL, 759,

L44. [http://stacks.iop.org/2041-8205/759/i=2/a=L44](http://stacks.iop.org/2041-8205/759/i=2/a=L44)

G´omez-Guijarro, C., Toft, S., Karim, A., et al. 2018, ApJ,

856, 121.

[http://stacks.iop.org/0004-637X/856/i=2/a=121](http://stacks.iop.org/0004-637X/856/i=2/a=121)

Hammer, F., Flores, H., Puech, M., et al. 2009, A&A, 507,

1313. [https://doi.org/10.1051/0004-6361/200912115](https://doi.org/10.1051/0004-6361/200912115)



Harrington, K. C., Yun, M. S., Magnelli, B., et al. 2018,

MNRAS, 474, 3866.

[http://dx.doi.org/10.1093/mnras/stx3043](http://dx.doi.org/10.1093/mnras/stx3043)


Hayward, C. C., Jonsson, P., Kereˇs, D., et al. 2012,

MNRAS, 424, 951.

[http://dx.doi.org/10.1111/j.1365-2966.2012.21254.x](http://dx.doi.org/10.1111/j.1365-2966.2012.21254.x)


Hayward, C. C., Kereˇs, D., Jonsson, P., et al. 2011, ApJ,

743, 159.

[http://stacks.iop.org/0004-637X/743/i=2/a=159](http://stacks.iop.org/0004-637X/743/i=2/a=159)


Hayward, C. C., Primack, J. R., Moreno, J., et al. 2013,

MNRAS, 434, 2572.

[https://doi.org/10.1093/mnras/stt1202](https://doi.org/10.1093/mnras/stt1202)


Hayward, C. C., Bremer, M. N., Chen, C.-C., et al. 2018,

MNRAS, 476, 2278.

[https://doi.org/10.1093/mnras/sty304](https://doi.org/10.1093/mnras/sty304)


Helou, G., Soifer, B. T., & Rowan-Robinson, M. 1985,

ApJL, 298, 7


Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ,

760, 11. [http://stacks.iop.org/0004-637X/760/i=1/a=11](http://stacks.iop.org/0004-637X/760/i=1/a=11)


Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016,

ApJ, 833, 103.

[http://stacks.iop.org/0004-637X/833/i=1/a=103](http://stacks.iop.org/0004-637X/833/i=1/a=103)


Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876,

130. [http://dx.doi.org/10.3847/1538-4357/ab1846](http://dx.doi.org/10.3847/1538-4357/ab1846)


Hopkins, P. F., Cox, T. J., Younger, J. D., & Hernquist, L.

2009, ApJ, 691, 1168.

[http://stacks.iop.org/0004-637X/691/i=2/a=1168](http://stacks.iop.org/0004-637X/691/i=2/a=1168)


Hung, C.-L., Hayward, C. C., Smith, H. A., et al. 2016,

ApJ, 816, 99.

[http://dx.doi.org/10.3847/0004-637X/816/2/99](http://dx.doi.org/10.3847/0004-637X/816/2/99)


Ikarashi, S., Ivison, R. J., Caputi, K. I., et al. 2015, ApJ,

810, 133.

[http://stacks.iop.org/0004-637X/810/i=2/a=133](http://stacks.iop.org/0004-637X/810/i=2/a=133)


Iono, D., Yun, M. S., Aretxaga, I., et al. 2016, ApJL, 829,

L10. [http://stacks.iop.org/2041-8205/829/i=1/a=L10](http://stacks.iop.org/2041-8205/829/i=1/a=L10)


Ivison, R. J., Smail, I., Amblard, A., et al. 2012, MNRAS,

425, 1320.

[https://doi.org/10.1111/j.1365-2966.2012.21544.x](https://doi.org/10.1111/j.1365-2966.2012.21544.x)


Jim´enez-Andrade, E. F., Magnelli, B., Karim, A., et al.

2018, A&A, 615, A25.

[https://doi.org/10.1051/0004-6361/201732186](https://doi.org/10.1051/0004-6361/201732186)


Jim´enez-Andrade, E. F., Magnelli, B., Karim, A., et al.

2019, A&A, 625, A114.

[https://doi.org/10.1051/0004-6361/201935178](https://doi.org/10.1051/0004-6361/201935178)


Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56.


[http://dx.doi.org/10.3847/1538-4357/aad4af](http://dx.doi.org/10.3847/1538-4357/aad4af)


Jones, G. C., Carilli, C. L., Shao, Y., et al. 2017, ApJ, 850,

180. [http://stacks.iop.org/0004-637X/850/i=2/a=180](http://stacks.iop.org/0004-637X/850/i=2/a=180)

18 Jim´enez-Andrade et al.



Karim, A., Schinnerer, E., Mart´ınez-Sansigre, A., et al.

2011, ApJ, 730, 61.

[http://stacks.iop.org/0004-637X/730/i=2/a=61](http://stacks.iop.org/0004-637X/730/i=2/a=61)


Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017,

MNRAS, 468, 4831.

[https://doi.org/10.1093/mnras/stx608](https://doi.org/10.1093/mnras/stx608)


Kennicutt, J. R. C. 1998, ARA&A, 36, 189


Kereˇs, D., Katz, N., Weinberg, D. H., & Dav´e, R. 2005,

MNRAS, 363, 2.

[http://dx.doi.org/10.1111/j.1365-2966.2005.09451.x](http://dx.doi.org/10.1111/j.1365-2966.2005.09451.x)


Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019,

MNRAS, 487, 3007.

[https://doi.org/10.1093/mnras/stz1486](https://doi.org/10.1093/mnras/stz1486)


Kronberger, T., Kapferer, W., Schindler, S., & Ziegler, B.

L. 2007, A&A, 473, 761.

[https://doi.org/10.1051/0004-6361:20077696](https://doi.org/10.1051/0004-6361:20077696)


Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609,

A130. [https://doi.org/10.1051/0004-6361/201732019](https://doi.org/10.1051/0004-6361/201732019)


Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJSS,

224, 24. [http://stacks.iop.org/0067-0049/224/i=2/a=24](http://stacks.iop.org/0067-0049/224/i=2/a=24)


Lang, P., Schinnerer, E., Smail, I., et al. 2019, ApJ, 879, 54.


[http://dx.doi.org/10.3847/1538-4357/ab1f77](http://dx.doi.org/10.3847/1538-4357/ab1f77)


Le F`evre, O., B´ethermin, M., Faisst, A., et al. 2019,

submitted to A&A, arXiv:1910.09517


Le Floc’h, E., Aussel, H., Ilbert, O., et al. 2009, ApJ, 703,

222. [http://dx.doi.org/10.1088/0004-637X/703/1/222](http://dx.doi.org/10.1088/0004-637X/703/1/222)


Lehnert, M. D., van Driel, W., Le Tiran, L., Di Matteo, P.,

& Haywood, M. 2015, A&A, 577, A112.

[https://doi.org/10.1051/0004-6361/201322630](https://doi.org/10.1051/0004-6361/201322630)


Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ,

737, 12. [http://stacks.iop.org/0004-637X/737/i=1/a=12](http://stacks.iop.org/0004-637X/737/i=1/a=12)


L´Huillier, B., Combes, F., & Semelin, B. 2012, A&A, 544,

A68. [https://doi.org/10.1051/0004-6361/201117924](https://doi.org/10.1051/0004-6361/201117924)


Liu, D., Gao, Y., Isaak, K., et al. 2015, ApJ, 810, L14.


[http://dx.doi.org/10.1088/2041-8205/810/2/L14](http://dx.doi.org/10.1088/2041-8205/810/2/L14)


Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853,

172. [http://dx.doi.org/10.3847/1538-4357/aaa600](http://dx.doi.org/10.3847/1538-4357/aaa600)


Liu, D., Schinnerer, E., Groves, B., et al. 2019, submitted

to ApJ, arXiv:1910.12883


Lutz, D., Poglitsch, A., Altieri, B., et al. 2011, A&A, 532,

A90. [https://doi.org/10.1051/0004-6361/201117107](https://doi.org/10.1051/0004-6361/201117107)


Magnelli, B., Saintonge, A., Lutz, D., et al. 2012, A&A, 548,

A22. [http://dx.doi.org/10.1051/0004-6361/201220074](http://dx.doi.org/10.1051/0004-6361/201220074)


Magnelli, B., Lutz, D., Saintonge, A., et al. 2014, A&A,

561, A86. [https://doi.org/10.1051/0004-6361/201322217](https://doi.org/10.1051/0004-6361/201322217)


Magnelli, B., Ivison, R. J., Lutz, D., et al. 2015, A&A, 573,

A45. [https://doi.org/10.1051/0004-6361/201424937](https://doi.org/10.1051/0004-6361/201424937)


Magnelli, B., Karim, A., Staguhn, J., et al. 2019, ApJ, 877,

45. [http://dx.doi.org/10.3847/1538-4357/ab1912](http://dx.doi.org/10.3847/1538-4357/ab1912)



Maiolino, R., Caselli, P., Nagao, T., et al. 2009, A&A, 500,

L1. [https://doi.org/10.1051/0004-6361/200912265](https://doi.org/10.1051/0004-6361/200912265)


Men´endez-Delmestre, K., Blain, A. W., Swinbank, M.,

et al. 2014, in XIV Latin American Regional IAU

Meeting, ed. A. Mateus, J. Gregorio-Hetem, &

R. Cid Fernandes, Vol. 44, 85.

[http://www.astroscu.unam.mx/rmaa/RMxAC..44/PDF/](http://www.astroscu.unam.mx/rmaa/RMxAC..44/PDF/RMxAC..44_GAL_menendez-delmestre.pdf)

RMxAC..44 ~~G~~ AL ~~m~~ [enendez-delmestre.pdf](http://www.astroscu.unam.mx/rmaa/RMxAC..44/PDF/RMxAC..44_GAL_menendez-delmestre.pdf)


Miettinen, O., Smolˇci´c, V., Novak, M., et al. 2015, A&A,

577, A29. [https://doi.org/10.1051/0004-6361/201425032](https://doi.org/10.1051/0004-6361/201425032)


Miettinen, O., Delvecchio, I., Smolˇci´c, V., et al. 2017, A&A,

597, A5. [https://doi.org/10.1051/0004-6361/201628128](https://doi.org/10.1051/0004-6361/201628128)


Miller, S. H., Bundy, K., Sullivan, M., Ellis, R. S., & Treu,

T. 2011, ApJ, 741, 115. https:

[//doi.org/10.1088%2F0004-637x%2F741%2F2%2F115](https://doi.org/10.1088%2F0004-637x%2F741%2F2%2F115)


Moreno, J., Torrey, P., Ellison, S. L., et al. 2015, MNRAS,

448, 1107. [http://dx.doi.org/10.1093/mnras/stv094](http://dx.doi.org/10.1093/mnras/stv094)


Mullaney, J. R., Alexander, D. M., Goulding, A. D., &

Hickox, R. C. 2011, MNRAS, 414, 1082.

[https://doi.org/10.1111/j.1365-2966.2011.18448.x](https://doi.org/10.1111/j.1365-2966.2011.18448.x)


Murphy, E. J., Momjian, E., Condon, J. J., et al. 2017, ApJ,

839, 35. [http://stacks.iop.org/0004-637X/839/i=1/a=35](http://stacks.iop.org/0004-637X/839/i=1/a=35)


Narayanan, D., Hayward, C. C., Cox, T. J., et al. 2010,

MNRAS, 401, 1613. http:

[//mnras.oxfordjournals.org/content/401/3/1613.abstract](http://mnras.oxfordjournals.org/content/401/3/1613.abstract)


Narayanan, D., Turk, M., Feldmann, R., et al. 2015,

Nature, 525, 496. [http://dx.doi.org/10.1038/nature15383](http://dx.doi.org/10.1038/nature15383)


Newman, S. F., Genzel, R., F¨orster-Schreiber, N. M., et al.

2012, ApJ, 761, 43.

[http://stacks.iop.org/0004-637X/761/i=1/a=43](http://stacks.iop.org/0004-637X/761/i=1/a=43)


Oliver, S. J., et al. 2012, MNRAS, 424, 1614


Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak,

K. G., & Gao, Y. 2012a, ApJ, 751, 10.

[http://stacks.iop.org/0004-637X/751/i=1/a=10](http://stacks.iop.org/0004-637X/751/i=1/a=10)


Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M.,

et al. 2012b, MNRAS, 426, 2601.

[http://dx.doi.org/10.1111/j.1365-2966.2012.21001.x](http://dx.doi.org/10.1111/j.1365-2966.2012.21001.x)


Persic, M., Salucci, P., & Stel, F. 1996, MNRAS, 281, 27


Riechers, D. A., Hodge, J., Walter, F., Carilli, C. L., &

Bertoldi, F. 2011, ApJL, 739, L31.

[http://stacks.iop.org/2041-8205/739/i=1/a=L31](http://stacks.iop.org/2041-8205/739/i=1/a=L31)


Riechers, D. A., Capak, P. L., Carilli, C. L., et al. 2010,

ApJL, 720, L131.

[http://stacks.iop.org/2041-8205/720/i=2/a=L131](http://stacks.iop.org/2041-8205/720/i=2/a=L131)


Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014,

ApJ, 796, 84.

[http://stacks.iop.org/0004-637X/796/i=2/a=84](http://stacks.iop.org/0004-637X/796/i=2/a=84)


Robertson, B. E., & Bullock, J. S. 2008, ApJL, 685, L27.


[http://stacks.iop.org/1538-4357/685/i=1/a=L27](http://stacks.iop.org/1538-4357/685/i=1/a=L27)

The nature of the puzzling SMG AzTEC2 19



Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011,

ApJL, 739, L40.

[http://stacks.iop.org/2041-8205/739/i=2/a=L40](http://stacks.iop.org/2041-8205/739/i=2/a=L40)

Romano-D´ıaz, E., Shlosman, I., Choi, J.-H., & Sadoun, R.

2014, ApJL, 790, L32.

[http://stacks.iop.org/2041-8205/790/i=2/a=L32](http://stacks.iop.org/2041-8205/790/i=2/a=L32)

Rybak, M., Rivera, G. C., Hodge, J. A., et al. 2019, ApJ,

876, 112.

[https://doi.org/10.3847%2F1538-4357%2Fab0e0f](https://doi.org/10.3847%2F1538-4357%2Fab0e0f)

Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2.

[https://doi.org/10.1088%2F0004-637x%2F778%2F1%2F2](https://doi.org/10.1088%2F0004-637x%2F778%2F1%2F2)

Sanders, D. B., & Mirabel, I. F. 1996, ARA&A, 34, 749.


[https://www.annualreviews.org/doi/abs/10.1146/](https://www.annualreviews.org/doi/abs/10.1146/annurev.astro.34.1.749?journalCode=astro)

[annurev.astro.34.1.749?journalCode=astro](https://www.annualreviews.org/doi/abs/10.1146/annurev.astro.34.1.749?journalCode=astro)

Schinnerer, E., Carilli, C. L., Capak, P., et al. 2008, ApJL,

689, L5. [http://stacks.iop.org/1538-4357/689/i=1/a=L5](http://stacks.iop.org/1538-4357/689/i=1/a=L5)

Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010,

ApJSS, 188, 384.

[http://dx.doi.org/10.1088/0067-0049/188/2/384](http://dx.doi.org/10.1088/0067-0049/188/2/384)

Schinnerer, E., Groves, B., Sargent, M. T., et al. 2016, ApJ,

833, 112.

[http://stacks.iop.org/0004-637X/833/i=1/a=112](http://stacks.iop.org/0004-637X/833/i=1/a=112)

Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A,

575, A74. [https://doi.org/10.1051/0004-6361/201425017](https://doi.org/10.1051/0004-6361/201425017)

Scott, K. S., et al. 2008, MNRAS, 385, 2225. https:

[//academic.oup.com/mnras/article/385/4/2225/1036374](https://academic.oup.com/mnras/article/385/4/2225/1036374)

Scudder, J. M., Ellison, S. L., Torrey, P., Patton, D. R., &

Mendel, J. T. 2012, MNRAS, 426, 549.

[https://doi.org/10.1111/j.1365-2966.2012.21749.x](https://doi.org/10.1111/j.1365-2966.2012.21749.x)

Shao, Y., Wang, R., Jones, G. C., et al. 2017, ApJ, 845,
138. [http://stacks.iop.org/0004-637X/845/i=2/a=138](http://stacks.iop.org/0004-637X/845/i=2/a=138)

Smolˇci´c, V., Novak, M., Bondi, M., et al. 2017, A&A, 602,

A1. [https://doi.org/10.1051/0004-6361/201628704](https://doi.org/10.1051/0004-6361/201628704)

Smolˇci´c, V., Aravena, M., Navarrete, F., et al. 2012, A&A,

548, A4.

[http://dx.doi.org/10.1051/0004-6361/201219368](http://dx.doi.org/10.1051/0004-6361/201219368)

Smolˇci´c, V., Karim, A., Miettinen, O., et al. 2015, A&A,

576, A127.

[http://dx.doi.org/10.1051/0004-6361/201424996](http://dx.doi.org/10.1051/0004-6361/201424996)

Smolˇci´c, V., Miettinen, O., Tomiˇci´c, N., et al. 2017, A&A,

597, A4. [https://doi.org/10.1051/0004-6361/201526989](https://doi.org/10.1051/0004-6361/201526989)

Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett,

J. W. 1997, ApJ, 478, 144.

[https://iopscience.iop.org/article/10.1086/303765](https://iopscience.iop.org/article/10.1086/303765)

Speagle, J. S., Steinhardt, C. L., Capak, P. L., &

Silverman, J. D. 2014, ApJSS, 214, 15.

[http://stacks.iop.org/0067-0049/214/i=2/a=15](http://stacks.iop.org/0067-0049/214/i=2/a=15)



Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016,

ApJ, 826, 112.

[http://dx.doi.org/10.3847/0004-637X/826/2/112](http://dx.doi.org/10.3847/0004-637X/826/2/112)


Springel, V., & Hernquist, L. 2005, ApJL, 622, L9.


[http://stacks.iop.org/1538-4357/622/i=1/a=L9](http://stacks.iop.org/1538-4357/622/i=1/a=L9)


Stott, J. P., Swinbank, A. M., Smail, I., et al. 2016,

MNRAS, 457, 1888.

[https://doi.org/10.1093/mnras/stw129](https://doi.org/10.1093/mnras/stw129)


Swinbank, A. M., Sobral, D., Smail, I., et al. 2012,

MNRAS, 426, 935.

[https://doi.org/10.1111/j.1365-2966.2012.21774.x](https://doi.org/10.1111/j.1365-2966.2012.21774.x)


Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016,

MNRAS, 457, 2790.

[http://dx.doi.org/10.1093/mnras/stw131](http://dx.doi.org/10.1093/mnras/stw131)


Tacconi, L. J., Neri, R., Chapman, S. C., et al. 2006, ApJ,

640, 228.

[http://stacks.iop.org/0004-637X/640/i=1/a=228](http://stacks.iop.org/0004-637X/640/i=1/a=228)


Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680,

246. [http://stacks.iop.org/0004-637X/680/i=1/a=246](http://stacks.iop.org/0004-637X/680/i=1/a=246)


Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ,

853, 179.

[http://stacks.iop.org/0004-637X/853/i=2/a=179](http://stacks.iop.org/0004-637X/853/i=2/a=179)


Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560,

613. [https://doi.org/10.1038/s41586-018-0443-1](https://doi.org/10.1038/s41586-018-0443-1)


Toft, S., Gallazzi, A., Zirm, A., et al. 2012, ApJ, 754, 3.


[http://stacks.iop.org/0004-637X/754/i=1/a=3](http://stacks.iop.org/0004-637X/754/i=1/a=3)


Toft, S., Smolˇci´c, V., Magnelli, B., et al. 2014, ApJ, 782,

68. [http://stacks.iop.org/0004-637X/782/i=2/a=68](http://stacks.iop.org/0004-637X/782/i=2/a=68)


Toft, S., Zabl, J., Richard, J., et al. 2017, Nature, 546, 510.


[http://dx.doi.org/10.1038/nature22388](http://dx.doi.org/10.1038/nature22388)


Willick, J. A. 1999, ApJ, 516, 47.


[https://doi.org/10.1086%2F307108](https://doi.org/10.1086%2F307108)


Wuyts, S., Schreiber, N. M. F., van der Wel, A., et al. 2011,

ApJ, 742, 96.

[http://stacks.iop.org/0004-637X/742/i=2/a=96](http://stacks.iop.org/0004-637X/742/i=2/a=96)


Younger, J. D., Fazio, G. G., Ashby, M. L. N., et al. 2010,

MNRAS, 407, 1268.

[http://dx.doi.org/10.1111/j.1365-2966.2010.16984.x](http://dx.doi.org/10.1111/j.1365-2966.2010.16984.x)


Yun, M. S., et al. 2015, MNRAS, 454, 3485. https:

[//academic.oup.com/mnras/article/454/4/3485/992500](https://academic.oup.com/mnras/article/454/4/3485/992500)


Zavala, J. A., et al. 2015, MNRAS, 452, 1140. https:

[//academic.oup.com/mnras/article/452/2/1140/1059247](https://academic.oup.com/mnras/article/452/2/1140/1059247)


Zavala, J. A., Monta˜na, A., Hughes, D. H., et al. 2018,

Nature Astronomy, 2, 56.

[https://doi.org/10.1038/s41550-017-0297-8](https://doi.org/10.1038/s41550-017-0297-8)


</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "inclination = 39 deg",
  "failed_quote": "= 39 ± 3 ◦"
 }
]
```
