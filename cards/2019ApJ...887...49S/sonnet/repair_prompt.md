# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...887...49S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version October 24, 2019
Typeset using L [A] TEX **twocolumn** style in AASTeX62


The Gas-Star Formation Cycle in Nearby Star-Forming Galaxies I. Assessment of Multi-scale Variations


Eva Schinnerer, [1, 2] Annie Hughes, [3, 4] Adam Leroy, [5] Brent Groves, [6, 7] Guillermo A. Blanc, [8, 9] Kathryn Kreckel, [1]

Frank Bigiel, [10] M´elanie Chevance, [11] Daniel Dale, [12] Eric Emsellem, [13, 14] Christopher Faesi, [1] Simon Glover, [15]

Kathryn Grasha, [6] Jonathan Henshaw, [1] Alexander Hygate, [11] J. M. Diederik Kruijssen, [11] Sharon Meidt, [16]

Jerome Pety, [17, 18] Miguel Querejeta, [13, 19] Erik Rosolowsky, [20] Toshiki Saito, [1] Andreas Schruba, [21] Jiayi Sun, [5] and
Dyas Utomo [5]


1 _Max_ _Planck_ _Institute_ _for_ _Astronomy,_ _K¨onigstuhl_ _17,_

_69117_ _Heidelberg,_ _Germany_
2 _Adjunct_ _Scientist,_ _National_ _Radio_ _Astronomy_ _Observatory,_

_520_ _Edgemont_ _Road,_ _Charlottesville,_ _VA_ _22903,_ _U.S.A._
3 _Universit´e_ _de_ _Toulouse,_ _UPS-OMP,_ _31028_ _Toulouse,_ _France_
4 _CNRS,_ _IRAP,_ _Av._ _du_ _Colonel_ _Roche_ _BP_ _44346,_ _31028_ _Toulouse_

_cedex_ _4,_ _France_
5 _Department_ _of_ _Astronomy,_ _The_ _Ohio_ _State_ _University,_

_140_ _West_ _18th_ _Ave,_ _Columbus,_ _OH_ _43210,_ _USA_
6 _Research_ _School_ _of_ _Astronomy_ _and_ _Astrophysics,_ _Australian_

_National_ _University,_ _Canberra,_ _ACT_ _2611,_ _Australia_
7 _International_ _Centre_ _for_ _Radio_ _Astronomy_ _Research,_ _The_

_University_ _of_ _Western_ _Australia,_ _Crawley,_ _WA_ _6009_ _Australia_
8 _The_ _Observatories_ _of_ _the_ _Carnegie_ _Institution_ _for_ _Science,_

_813_ _Santa_ _Barbara_ _Street,_ _Pasadena,_ _CA_ _91101,_ _USA_
9 _Departamento_ _de_ _Astronom´ıa,_ _Universidad_ _de_ _Chile,_

_Casilla_ _36-D,_ _Santiago,_ _Chile_
10 _Argelander-Institut_ _f¨ur_ _Astronomie,_ _Universit¨at_ _Bonn,_

_Auf_ _dem_ _H¨ugel_ _71,_ _53121_ _Bonn,_ _Germany_
11 _Astronomisches_ _Rechen-Institut,_ _Zentrum_ _f¨ur_ _Astronomie_ _der_ _Universit¨at_

_Heidelberg,_ _M¨onchhofstraße_ _12-14,_ _69120_ _Heidelberg,_ _Germany_
12 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Wyoming,_

_Laramie,_ _WY_ _82071,_ _USA_
13 _European_ _Southern_ _Observatory,_ _Karl-Schwarzschild-Strasse_ _2,_

_D-85748_ _Garching_ _bei_ _M¨unchen,_ _Germany_
14 _Univ._ _Lyon,_ _Univ._ _Lyon1,_ _ENS_ _de_ _Lyon,_ _CNRS,_ _Centre_ _de_ _Recherche_

_Astrophysique_ _de_ _Lyon_ _UMR5574,_ _F-69230_ _Saint-Genis-Laval,_ _France_
15 _Instit¨ut_ _f¨ur_ _Theoretische_ _Astrophysik,_ _Zentrum_ _f¨ur_ _Astronomie_ _der_ _Universit¨at_

_Heidelberg,_ _Albert-Ueberle-Strasse_ _2,_ _69120_ _Heidelberg,_ _Germany_
16 _Sterrenkundig_ _Observatorium,_ _Universiteit_ _Gent,_ _Krijgslaan_ _281_ _S9,_ _B-9000_ _Gent,_ _Belgium_
17 _IRAM,_ _300_ _rue_ _de_ _la_ _Piscine,_ _F-38406_ _Saint_ _Martin_ _de_ _H`eres,_ _France_
18 _Sorbonne_ _Universit´e,_ _Observatoire_ _de_ _Paris,_ _Universit´e_ _PSL,_ _´Ecole_ _normale_ _sup´erieure,_

_CNRS,_ _LERMA,_ _F-75005,_ _Paris,_ _France_
19 _Observatorio_ _Astron´omico_ _Nacional_ _(IGN),_
_C/Alfonso_ _XII_ _3,_ _Madrid_ _E-28014,_ _Spain_
20 _4-183_ _CCIS,_ _University_ _of_ _Alberta,_ _Edmonton,_ _Alberta,_ _Canada_
21 _Max-Planck-Institut_ _f¨ur_ _extraterrestrische_ _Physik,_

_Giessenbachstraße_ _1,_ _D-85748_ _Garching,_ _Germany_


ABSTRACT


The processes regulating star formation in galaxies are thought to act across a hierarchy of spatial
scales. To connect extragalactic star formation relations from global and kpc-scale measurements to
recent cloud-scale resolution studies, we have developed a simple, robust method that quantifies the
scale dependence of the relative spatial distributions of molecular gas and recent star formation. In
this paper, we apply this method to eight galaxies with _∼_ 1 _[′′]_ resolution molecular gas imaging from

2 Schinnerer, Hughes, Leroy, Groves & PHANGS


the PHANGS-ALMA and PAWS surveys that have matched resolution, high quality narrowband H _α_
imaging. At a common scale of 140 pc, our massive (log(M _⋆_ [M _⊙_ ]) = 9 _._ 3 _−_ 10 _._ 7), normally starforming (SFR[M _⊙_ yr _[−]_ [1] ] = 0 _._ 3 _−_ 5 _._ 9) galaxies exhibit a significant reservoir of quiescent molecular gas
not associated with star formation as traced by H _α_ emission. Galactic structures act as backbones
for both molecular and H II region distributions. As we degrade the spatial resolution, the quiescent
molecular gas disappears, with the most rapid changes occurring for resolutions up to _∼_ 0.5 kpc. As
the resolution becomes poorer, the morphological features become indistinct for spatial scales larger
than _∼_ 1 kpc. The method is a promising tool to search for relationships between the quiescent or
star-forming molecular reservoir and galaxy properties, but requires a larger sample size to identify
robust correlations between the star-forming molecular gas fraction and global galaxy parameters.


_Keywords:_ galaxies: ISM — ISM: atoms — ISM: molecules



1. INTRODUCTION


The star formation rate of galaxies reflects the interplay of galactic dynamics, violent stellar feedback
(also from active galactic nuclei (AGN) if present), and
gravitational collapse of molecular gas. Accessing these
physics requires high resolution observations spanning
large areas across a diverse sample of galaxies.
Observations at coarse resolution, from _∼_ 1 kpc scales
up to whole galaxies, show a tight correlation between
molecular gas and star formation (e.g., Young et al.
1995; Kennicutt 1998b; Wong & Blitz 2002; Leroy et
al. 2008; Bigiel et al. 2008; Schruba et al. 2011; Saintonge et al. 2011; Leroy et al. 2013; Momose et al. 2013,
among many others). To the extent that galactic morphology remains discernible at these scales, such studies
have typically found that maps of molecular gas and star
formation tracers are very similar.
High resolution observations suggest a more complex
picture. When the resolution approaches the scale of
individual giant molecular clouds (GMCs) and Hii regions, tracers of recent massive star formation and cold
molecular gas appear spatially distinct (e.g., Kawamura
et al. 2009; Schruba et al. 2010; Gratier et al. 2012; Battersby et al. 2017; Kreckel et al. 2018; Querejeta et al.
2019). This separation between the input (GMCs) and
output (Hii regions) of the star formation process has
been interpreted as a sign of destructive feedback and
used to estimate molecular cloud lifetimes (e.g., Kawamura et al. 2009; Schruba et al. 2010; Gratier et al. 2012;
Kruijssen & Longmore 2014; Battersby et al. 2017; Kruijssen et al. 2018, 2019). A related measurement shows
that the scatter in star formation–gas scaling relations
increases with improving spatial resolution (e.g., Bigiel
et al. 2008; Blanc et al. 2009; Schruba et al. 2010; Onodera et al. 2010; Leroy et al. 2013; Kreckel et al. 2018).
This, too, has been interpreted as a signature of evolutionary cycling and/or feedback (e.g., Feldmann et al.
2011; Kruijssen & Longmore 2014; Kruijssen et al. 2018).
Observations at high spatial resolution can potentially



measure the impact of stellar feedback on the gas and
thus lead to a better understanding of the mechanisms
that determine the efficiency of star formation.
High resolution observations also reveal the importance of galactic dynamics. The organization of star
formation by dynamically induced gas flows and dynamical suppression of star formation becomes evident when

observations reach scales smaller than the characteristic
sizes/widths of dynamical features like bars and spiral
arms. As a result, high resolution observations offer insight into how galaxy morphology affects where stars are
born. For example, at high resolution, star-forming regions tend to appear downstream of the arms seen in gas
(e.g., see Schinnerer et al. 2013; Egusa et al. 2017; Schinnerer et al. 2017; Kreckel et al. 2018). Studying M51,
Meidt et al. (2013) and Schinnerer et al. (2013) identified
strong variations in the ratio between the star formation
rate and the molecular gas mass (see also Leroy et al.
2017a). Most strikingly, they found regions in the inner
spiral arms that have immense gas reservoirs but little
star formation. Meidt et al. (2013) attributed these features to dynamical suppression of star formation (which
also manifests in early type galaxies at larger scales, e.g.,
Davis et al. 2014) rather than the absence of high density gas (as confirmed by Querejeta et al. 2019).
To date, most high resolution work has focused on case
studies of individual galaxies. Studies targeting samples
of many galaxies have achieved at best a few hundred
pc to _∼_ kpc resolution, and often treated whole galaxies
as a single unit. A clear next step is to systematically
examine how tracers of massive star formation compare
to tracers of molecular gas at high resolution across a
large sample.
In this paper, we compare CO emission, tracing molecular gas, to H _α_ emission, tracing recent star formation,
across a large area in eight nearby galaxies. Our maps all
have spatial resolution of 140 pc, and often better. This
means that an individual resolution element approaches
the size of a large GMC or Hii region and that we expect

Gas and Star Formation in PHANGS Galaxies 3



only one or a few such regions per beam. Our sample
shows diverse morphologies, including spiral arms, bars,
nuclear starburst rings, and flocculent structure. This
allows a comparative analysis and offers the chance to
identify general and environmental trends, which was
challenging with previous individual-galaxy case stud
ies.

Specifically, we compare the location of H _α_ emission,
a classic tracer of recent massive star formation (e.g.,
reviews by Kennicutt 1998b; Kennicutt & Evans 2012)
to the location of CO emission, a tracer of molecular gas
(e.g., reviews by Fukui, & Kawamura 2010; Bolatto et
al. 2013; Heyer, & Dame 2015). We divide each galaxy
into regions where only CO emission is bright, only H _α_
emission is bright, or both tracers are bright. Then, we
quantify the fraction of lines of sight and the fraction
of emission from each type of region. We repeat this
analysis for each galaxy for a range of spatial resolutions.
We examine the changing statistics and morphology of
the two tracers as a function of scale. Doing so, we
quantify how the coincidence of gas and star formation
observed at low resolution changes as we resolve galaxies
at the scale of an individual star-forming region.
The PHANGS (Physics at High Angular resolution
in Nearby GalaxieS [1] ) collaboration is carrying out high
physical resolution surveys of molecular gas and star
formation tracers in many nearby galaxies. The observations enabling this analysis are _∼_ 1 _[′′]_ resolution CO
line emission maps from the PHANGS-ALMA survey
(Leroy et al. in prep.), which is mapping CO emission
from the disks of _∼_ 80 nearby galaxies with high fidelity
for the first time. This angular resolution matches that
of seeing-limited H _α_ observations and allows ≲ 100 pc
resolution out to distances of up to _∼_ 18 Mpc. For comparison, previous large CO surveys typically achieved
_∼_ 10 _−_ 45 _[′′]_ resolution or targeted only the innermost
parts of galaxies with limited sensitivity.
The paper is organized as follows: The data used are
presented in _§_ 2. We describe our methodology in _§_ 3,
present our results in _§_ 4, and discuss the implications of
our findings in _§_ 5. We summarize our findings in _§_ 6.


2. DATA


We require high spatial resolution imaging of the
molecular gas and a tracer of recent star formation on
scales of ≲100 pc. This ensures that each individual resolution element approaches the size of a giant molecular
cloud (Sanders et al. 1985) or a massive H II region (Oey
et al. 2003; Azimlu et al. 2011).


1 www.phangs.org



To trace recent massive star formation, we use narrowband H _α_ +[N II ] imaging. At the _d_ _<_ 17 Mpc distance
to our targets, seeing-limited images achieve _≈_ 1 _[′′]_ ≲
100 pc resolution. We pair these with _≈_ 1 _[′′]_ resolution
low- _J_ CO line imaging to trace the molecular gas.
We analyze the first seven galaxies targeted by
PHANGS-ALMA (Leroy et al. in prep.), which also
have H _α_ imaging of sufficient quality for our analysis.
Our sample also includes the grand-design spiral galaxy
M 51 using data from the PAWS survey (Schinnerer
et al. 2013). We summarize the final sample of eight
galaxies in Table 1.

4 Schinnerer, Hughes, Leroy, Groves & PHANGS


**Table** **1.** Key Parameters of Sample Galaxies.


Name Distance Inclination _R_ 25 SFR log(M _⋆_ ) A V _,_ MW Metallicity Hubble Type Activity


(Mpc) (degrees) (arcmin) (M _⊙_ yr _[−]_ [1] ) (M _⊙_ ) (mag) log( _H_ _[O]_ [)] [PP04]


NGC 0628 9.8 9 4.9 1.83 10.2 0.192 8.51 Sc-A HII

NGC 3351 10.0 45 3.6 1.30 10.2 0.076 8.80 Sb-B HII; Sbrst

NGC 3627 10.6 55 5.1 3.54 10.6 0.091 8.74 Sb-AB LINER; Sy 2

NGC 4254 16.8 38 2.5 5.44 10.5 0.106 8.68 Sc-A LINER; HII

NGC 4321 15.2 38 3.0 3.81 10.6 0.072 8.71 Sbc-AB LINER; HII

NGC 4535 15.8 41 4.1 2.22 10.4 0.053 8.78 SAB(s)c LINER; HII

NGC 5068 5.2 27 3.7 0.29 9.3 0.281 8.35 Scd-AB –

NGC 5194 8.6 21 6.9 4.91 10.7 0.096 8.70 SA(s)bc pec HII; Sy2.5


Note—The galaxy parameters are adopted from Leroy et al. (2019) where the original references can be found. For NGC 4535,
the Hubble type and activity are taken from NED.

The emission that we identify with H II regions is indicated with a gray contour on the H _α_ maps (see Section 2.2.5). The axes
are in offset arcseconds from the reference position of each map. The black bar in the bottom right corner of each CO intensity
map indicates a spatial scale of 2 kpc.

6 Schinnerer, Hughes, Leroy, Groves & PHANGS

Gas and Star Formation in PHANGS Galaxies 7



2.1. _CO_ _Images_


PHANGS-ALMA imaged the CO(2-1) emission in our
targets using the ALMA 12-m, 7-m, and total power antennas. In this paper, we use a pilot sample observed
during Cycle 1 (project 2012.1.00650.S; NGC 0628) and
Cycle 3 (projects 2013.1.00925.S and 2013.1.00956.S; remaining galaxies except NGC 5194). We chose our target area to match the region of active star formation
indicated by an intensity contour of 1 MJy sr _[−]_ [1] in the
WISE 22 micron image.
We use integrated intensity maps constructed from the
data cubes delivered in PHANGS-ALMA internal data

release 3.3 as our starting point. The construction of
these maps is described in Leroy et al. (in prep.), and
their properties are summarized in Tab. 2. Briefly, these
were imaged in CASA 5.4.0. They should be sensitive
to emission on all spatial scales due to the inclusion of
data from both the 12-m array and the Morita Atacama
Compact Array (ACA). Four of the galaxies (NGC 3627,
NGC 4254, NGC 4321, and NGC 5068) were observed in
two separate large (100+ pointings) mosaics. We match
the beams of the two halves via convolution and com
bined them via linear mosaicking. This results in moderately different noise properties for the two halves of
the map. After calibration and imaging, the resulting data cubes were convolved to have a round beam.
The typical RMS noise in brightness temperature units
is _σ_ _RMS_ _≈_ 0 _._ 17 K per 2.5 km s _[−]_ [1] channel, but varies
slightly between cubes.
We use the integrated intensity maps delivered in the
internal data release v3.3. These are constructed by applying a “broad” signal identification mask to the spectral line cube before summing all valid pixels across the
observed velocity range. Specifically, the broad mask
is the logical union of two signal identification masks,
the first generated from the data cube at the best available resolution and the second from a version of the

cube that has been smoothed to a spatial resolution of
500 pc. In both cases, we identify emission above 3 _._ 5 _σ_
in 3 consecutive channels of the cube, and expand it to
include contiguous regions in ( _x, y, v_ ) space that show
emission above 2 _σ_ over 2 consecutive channels. The

resulting “broad” integrated intensity maps have high
completeness, meaning that they include most CO emission in the cube, even emission present at only modest
signal-to-noise. More quantitatively, the flux recovery
in the v3.3 broad integrated intensity maps (which are
our input maps for the analysis) varies between 93%
(NGC 4321) and 99% (NGC 3627) of the total CO flux
that is present in the input best resolution data cube
(see also discussion in Sun et al. 2018). Sensitivity estimates for these integrated intensity maps are tabulated



in Tab. 2. These are spatial averages of the sensitivity across each map, calculated as _σ_ RMS _×_ _√N_ _×_ ∆ _v_,

where _N_ is the number of channels in the signal identification mask for that sightline, and ∆ _v_ is the channel width. The equivalent inclination-corrected 1 _σ_ integrated molecular mass surface density sensitivity limits
vary between 2.5 and 7.4 M _⊙_ pc _[−]_ [2] across the PHANGS
galaxies, assuming a standard Galactic conversion factor of _α_ CO = 4 _._ 35 M _⊙_ pc _[−]_ [2] (K km s _[−]_ [1] ) _[−]_ [1] (Bolatto et al.
2013) and a [12] CO( _J_ = 2 _→_ 1) to [12] CO( _J_ = 1 _→_ 0)
brightness temperature ratio of _R_ 21 = 0 _._ 7.
For NGC 5194 (M51), we use the 1 _[′′]_ resolution integrated CO(1-0) image from PAWS (PdBI Arcsecond
Whirlpool Survey, Schinnerer et al. 2013). PAWS combined observations from the IRAM PdB interferometer

and 30m single dish telescope, ensuring that the map
includes emission on all spatial scales (see Pety et al.
2013). Details of the observations and data reduction
are presented in Pety et al. (2013). The PAWS map has
an average 1 _σ_ sensitivity of _∼_ 4 _._ 4 K km s _[−]_ [1], corresponding to an integrated mass surface density sensitivity of
_∼_ 19 M _⊙_ pc _[−]_ [2] .


2.2. _Hα_ _Images_


We use narrowband H _α_ imaging to trace recent massive star formation, drawing from a mixture of new
and literature data. For the literature data, we adopt
the image that best matched the following criteria: (i)
field-of-view (FoV) sufficient to cover the CO data, (ii)
angular resolution similar to the CO data, and (iii) a
corresponding R band image observed with the same
telescope under similar conditions. For several galaxies
where no literature data matched our criteria, we obtained new Wide-Field Imager (WFI) narrowband and
R band imaging using the MPG/ESO 2.2m telescope.
Details on the datasets used can be found in Tab. 2.

Specifically, we used data from the SINGS ancillary
survey (Kennicutt et al. 2003) for NGC 0628, NGC 3351,
NGC 4254, NGC 4321, and NGC 5194. Details of the
observations, including the associated R band data used
for continuum subtraction, can be found in the SINGS
fifth delivery document [4] . The continuum R band data
reach a depth of 25 mag/arcsec [2] with a signal-to-noise
of _∼_ 10. The H _α_ narrowband filter data were observed
for 1800 s.

NGC 5068 was observed in the H _α_ narrowband and R

band as part of the Survey for Ionization in Neutral Gas
Galaxies (SINGG; Meurer et al. 2006) at the CTIO.


4 [http://irsa.ipac.caltech.edu/data/SPITZER/SINGS/doc/](http://irsa.ipac.caltech.edu/data/SPITZER/SINGS/doc/sings_fifth_delivery_v2.pdf)
sings fifth ~~d~~ [elivery](http://irsa.ipac.caltech.edu/data/SPITZER/SINGS/doc/sings_fifth_delivery_v2.pdf) v2.pdf

8 Schinnerer, Hughes, Leroy, Groves & PHANGS



NGC 5068 was also observed for 1800 s in the narrow
band, and 360 s in the R band.
For NGC 3627 and NGC 4535, the literature data were
not of sufficient quality to match our criteria. Therefore,
we use data from a new survey of PHANGS targets using
the WFI instrument on the MPG/ESO 2.2-m telescope
at La Silla Observatory. This survey obtained both narrowband H _α_ and Rc band using WFI. The galaxies were
placed in a single CCD, avoiding chip gaps, allowing an
uninterrupted FoV of 16’ _×_ 16’. These data were astrometrically and photometrically calibrated using GAIA
DR2 catalogs cross-matched to all stars in the full FoV
of the WFI images. Full details of this survey, including
observations, reduction, calibration and sky subtraction
can be found in Razza et al. (in prep.).


2.2.1. _Sky_ _subtraction_


We subtract a sky background from the SINGS H _α_
data. To do this, we first mask all bad pixels and bright
sources. Then, we mask all emission that exceeds the
median of the remaining image by _>_ 3 times the rms
noise. We convolve this mask by _∼_ 3 _×_ FWHM to further mask out any diffuse light from bright sources or
the galaxy. We then fit and subtract a plane from the
masked image. In all cases, our targets fill a significant
fraction of the image. In a few cases this caused the
plane fit to fail. In these cases, the sky background was
set to be the median of the masked image. The typical sky brightness was 20-21 mag/arcsec [2] in the R band
images.
For NGC 5068 and our WFI data, the images are already sky subtracted by Meurer et al. (2006) and Razza
et al. (in prep.), respectively. We repeated the above
analysis and confirm that the residuals appear consistent with noise.


2.2.2. _Seeing_ _and_ _astrometry_


After sky subtraction, we fit all point sources in both
the H _α_ and R band images to determine the average
seeing [5] . When the seeing differed significantly between
the R band and H _α_ images ( _>_ 0 _._ 5 pixel), we convolved
the higher resolution data to match the lower resolution.
Typical seeing for the data range from 1 _[′′]_ _._ 2 to 2 _[′′]_ _._ 1 (see
Tab. 2 for individual galaxies).
For the SINGS and SINGG data, the astrometry was
already confirmed by matching stellar sources to the US
Naval Observatory A2.0 database (Monet 1998). Meurer
et al. (2006) matched _∼_ 100 and found an accuracy of
0 _[′′]_ _._ 4, similar to the 0 _[′′]_ _._ 5 found for the SINGS data.


5 This was done using the IDL implementation of the
DAOPHOT routines `APER` and `GETPSF` : [https://idlastro.gsfc.nasa.](https://idlastro.gsfc.nasa.gov/ftp/pro/idlphot/aper.pro)
[gov/ftp/pro/idlphot/aper.pro.](https://idlastro.gsfc.nasa.gov/ftp/pro/idlphot/aper.pro)



We require accurate absolute astrometry to assess spatial offsets between H _α_ and CO emission. Therefore, we
used Gaia DR2 (Gaia Collaboration et al. 2016, 2018)
to further refine the absolute astrometry. We fit _∼_ 50
stars per R band image with an rms of _∼_ 50–60 mas on
the required offsets which we applied. This yielded a
final astrometric accuracy of 0 _[′′]_ _._ 1–0 _[′′]_ _._ 2. The astrometry
of the WFI images was calculated using the Gaia DR2
catalog directly and so already reach this same level of

accuracy.


2.2.3. _Continuum_ _subtraction_


Once the H _α_ and R band images are aligned and at
the same resolution, we determine the scale of the R
band continuum in the H _α_ narrowband image. If the
images are correctly flux calibrated, this scale should be
one. However to confirm this we determine the median
flux ratio of the matched non-saturated stars between
the narrowband and R band images.
Using this flux ratio as a basis, we obtain a first estimate of the H _α_ flux by subtracting the R band image from the narrowband. However, the H _α_ +Nii line
also contributes to the R band data. Therefore, using
the estimated H _α_ +Nii image we determine the H _α_ +Nii
contribution to the R band image. We subtract this estimated line contamination from the R band image and
iterate this process until successive continuum estimates
differ by less than 1%. Then we subtract this continuum
estimate to achieve a flux-calibrated line image.
Note that this approach does not account for a varying continuum slope in the R band. We might expect
some variation in the narrowband continuum to R band

continuum ratio due to, e.g., a variation in the stellar
population across the galaxy disk (Razza et al. in prep.).


2.2.4. _Correction_ _for_ _transmission,_ _[N_ ii _]_ _contamination,_
_and_ _Galactic_ _extinction_


We correct for transmission loss of the H _α_ emis
sion line, which can be red-shifted out of the chosen narrowband filter, and for the contribution of the

[N II ] _λ_ 6548 _,_ 6583 emission lines, which may fall within
the narrowband filters.
To do this, we use an integrated, high signal-to-noise
Hii region spectrum from the MUSE observations of
NGC 0628 presented in Kreckel et al. (2016). We treat
this as a characteristic spectrum for all of our targets.
Our targets are all relatively massive, relatively face-on
spiral galaxies, so we expect the NGC 0628 spectrum
to be reasonably representative of the typical Hii region in our sample. The NGC 0628 template spectrum
has an intrinsic [Nii]/H _α_ ratio of 0.3. This is close to,
but slightly lower than some of the global estimates for
the [Nii]/H _α_ in our targets from, e.g., Kennicutt et al.

Gas and Star Formation in PHANGS Galaxies 9



(2011). We note possible variation in [Nii]/H _α_ as a
source of uncertainty.
We shift this template spectrum to the redshift of each
galaxy. Then, using the transmission curves for the filters listed in the notes of Tab. 2, we calculate the contribution of the H _α_ and [Nii] lines to the narrowband image (see Tab. 2). Based on this calculation, we subtract
the likely contamination by [Nii] to create an H _α_ -only
surface brightness image ( _F_ H _α_ = _F_ line (1 _−_ _f_ [NII] ) _/T_ H _α_ ).
As a final step, we correct all images for foreground Galactic extinction using the map of Schlafly
& Finkbeiner (2011).


2.2.5. _Filtering_ _out_ _emission_ _from_ _diffuse_ _ionized_ _gas_
_(DIG)_


Our analysis uses H _α_ emission to pinpoint the spatial
location of recent high-mass star formation, i.e., we are
specifically interested in H _α_ emission arising from Hii
regions that surround massive stars. In this context,
H _α_ emission arising from diffuse ionized gas (DIG) must
be excluded from the analysis. This H _α_ emission does
not originate from gas that is ionized locally by young
massive stars. Unfortunately, DIG can contribute 50%
or more to the observed H _α_ flux of a galaxy (e.g., review by Haffner et al. 2009). The origin of the ionizing
photons producing the DIG is still debated, with some
or indeed all of these photons originating from massive
young stars (e.g., due to Lyman-continuum leakage from
H II regions; Weilbacher et al. 2018). For our purposes,
the key issue is that the DIG emission is not necessarily
co-spatial with the young stellar population powering
the Hii regions (see, e.g., Kreckel et al. 2016). Instead
DIG generally exhibits a more smooth appearance.
There are two main methods to separate the H _α_ emission arising from Hii regions and the gas associated with
the DIG. The first method, based on morphology, decomposes the H _α_ maps into bright knots and a diffuse
background (e.g., Thilker et al. 2002; Oey et al. 2007)
using for example the software Hiiphot (Thilker et al.
2000). Alternatively, optical spectroscopy can be used
to identify emission arising from DIG, which is warmer
and less dense than the Hii region gas (e.g. Blanc et al.
2009; Haffner et al. 2009; Kaplan et al. 2016; Tomiˇci´c et
al. 2017).
After correcting for Galactic extinction, we attempt
to remove the DIG contribution from our H _α_ maps. We
use the following unsharp masking scheme which is qualitatively similar to the approaches mentioned above. We
implemented a two step approach which is first identifying diffuse emission on scales larger than Hii regions,
and in a second iteration attempting to take into account variations in the strength of the DIG contribution
on the scales of galactic structures such as spiral arms.



The filtering scales and gain represent tuning parameters informed by physical expectations:


1. **Unsharp** **mask** **with** **a** **300** **pc** **kernel:** We
smooth our original image with a Gaussian kernel
with FWHM 300 pc. We choose 300 pc because
we do not expect Hii regions to reach sizes much
larger than that scale (e.g., Oey et al. 2003; Azimlu
et al. 2011; Whitmore et al. 2011). Then, we subtract this smooth version of the image from the
original image. We identify likely Hii regions as
the parts of the map still detected at high signalto-noise in this filtered map.


2. **Subtract** **a** **scaled** **version** **of** **the** **initial** Hii

**regions** **from** **the** **DIG** **map:** We subtract a
scaled version of the Hii regions identified in the
previous step from the original map. The scaling
factor, which is 0 _._ 33, reflects that this is an initial

estimate and that we do not want to oversubtract

at this stage.


3. **Unsharp** **mask** **with** **an** **750** **pc** **kernel:** We
smooth our Hii region subtracted image with a
Gaussian kernel that has FWHM 750 pc. This
scale is large enough to typically encompass galactic structures, such as spiral arms, that might show
higher levels of DIG contribution and clustering
of Hii regions (e.g. Kreckel et al. 2016). Then, we
subtract this smooth version of the image from the
_original_ image. We identify our final set of Hii regions as the parts of the map still detected at high
signal-to-noise in this filtered map.


We proceed by blanking all regions outside the identified Hii regions and treating the masked map as our
best estimate for the location of massive star formation.

The final H _α_ maps used for our analysis are constructed
by applying this mask to the calibrated and corrected
H _α_ map. The flux in this masked map represents our
best estimate of the relative intensity of star formation,
because we expect most of this H _α_ emission to arise
from gas photo-ionized by massive stars (rather than,
e.g., shocks). On average, this process removes _∼_ 50%
of the H _α_ emission from the initial maps.
The tuning parameters that we adopted were optimized to yield a procedure that identifies bright knots
of H _α_ emission, which are likely Hii regions, when applied to our whole sample. Three of the authors independently inspected the resulting masks to confirm that
they indeed isolate the bright knots in each of our H _α_
maps, without subdividing the emission from large Hii
regions. In a few targets, we further confirmed that
our approach agrees sufficiently well with masks based

10 Schinnerer, Hughes, Leroy, Groves & PHANGS



on Hiiphot and with spectroscopic separation of DIG
and Hii regions (Kreckel et al. 2016; Blanc et al. 2009).
We experimented with fixed surface brightness cuts to
separate the H _α_ emission into the DIG and the H II regions, but found the resulting masks to be much less
satisfactory. This is likely linked to the fact that the H _α_
luminosity of Hii regions depends on the exact physical
conditions present in the ionized gas such as ionizing
flux, gas geometry etc. which can vary significantly between and within galaxies at our resolution. Lastly, we
note that the vertical extent of the DIG can be significant reaching typical scale heights of 1 kpc (e.g. Rossa,
& Dettmar 2003; Levy et al. 2019).
We note one important additional caveat about our
strategy for DIG removal. When identifying bright
regions during the unsharp masking steps, we use a
signal-to-noise threshold. Because the noise and native resolution of the input H _α_ data vary, the effective
H _α_ surface brightness threshold applied to our fiducial
maps ranges from _I_ H _α_ [erg s _[−]_ [1] cm _[−]_ [2] sr _[−]_ [1] ] = 2 _._ 21 _×_ 10 _[−]_ [6]

(NGC 4254) to 9 _._ 46 _×_ 10 _[−]_ [6] (NGC 5068), corresponding to SFR surface density limits between 0.0014 and
0.0036 M _⊙_ yr _[−]_ [1] kpc _[−]_ [2] . For a point source at the native
resolution of our data, these sensitivity limits correspond
to H II region luminosities between log 10 _L_ H _α_ [erg s _[−]_ [1] ] =
36 _._ 5 (NGC 4321) and 37.6 (NGC 5194). These limits
are comparable to the peak of the H II region luminosity
function measured by narrowband H _α_ imaging in the
literature (e.g. Bradley et al. 2006; Oey et al. 2007), although the current generation of optical IFUs are able to
detect H II regions with lower luminosities (e.g. Kreckel
et al. 2016; Rousseau-Nepton et al. 2018).


2.2.6. _No_ _correction_ _for_ _internal_ _extinction_


Our final H _α_ line flux images trace emission from H II
regions without any correction for attenuation. We expect our images to do a good job tracing the location
of massive star formation, but the maps may miss the
most heavily extinguished regions. Because our analysis
focuses mostly on the location (rather than the amount)
of recent massive star formation, we expect this to be
a secondary concern. Based on literature work in M 51
(Scoville et al. 2001; Schinnerer et al. 2017), we do not
expect that such highly extinguished regions occupy a
significant fraction of sightlines in the disks of our galaxies. For our analysis based on flux, the underestimation
of flux is likely stronger for the regions co-located with
molecular gas, where dust is likely well-mixed with the
gas, than for regions where no gas is present.


3. METHODOLOGY


We aim to quantify the coincidence of molecular gas,
traced by CO, and high-mass star formation, traced by



H _α_, across a range of spatial scales. To do this, we adopt
the following approach:


1. **Threshold** **the** **H** _α_ **images:** The **removal** **of**
**the** **significant** DIG contribution to the H _α_ images acts as a natural threshold (see _§_ 2.2.5). We
calculate the total flux in the thresholded image
at this stage.


2. **Threshold** **the** **CO** **images:** We clip the CO images at our best matching resolution of 140 pc using a physical threshold of 12.6 M _⊙_ pc _[−]_ [2] (accounting for galaxy inclination) or roughly an A V _≈_ 1.
This corresponds to the equivalent 3 _σ_ mass surface density sensitivity of our CO map with the
lowest sensitivity at this spatial scale (NGC 5194).


3. **Convolve** **to** **coarser** **physical** **resolutions:**
We convolve each thresholded image to a succession of coarser resolutions, ranging from our best
matching resolution of 140 pc to 1 _._ 5 kpc (to match
to previous studies working at coarser resolution).


4. **Clip** **the** **low** **intensity** **emission** **in** **the** **con-**
**volved** **images:** For each convolved image, we
blank the faintest lines of sight that collectively
contribute 2% of the total flux in the image. This
suppresses convolution artifacts.


5. **Measure** **the** **coincidence** **of** **the** **two** **trac-**

**ers** **at** **each** **resolution:** We divide each galaxy
at each resolution into regions with visible CO
only, visible H _α_ only, or both CO and H _α_ emission present. We measure the fraction of sightlines
and the fraction of flux in each region type at each
resolution.


This approach represents a specific application of a
more general methodology, which would be to measure
the joint distribution functions of CO and H _α_ . In the
rest of this section, we motivate the specific choices that
we have made. When describing the results in the next
sections, we use the words ’sightlines’ and ’pixels’ interchangeably.


3.1. _Thresholding_ _and_ _total_ _flux_ _estimation_


We threshold both the CO and H _α_ images before comparing them. This fixes the total flux used in the analysis across scale. It also ensures that we have high confidence that all emission entering the analysis corresponds
to real high-mass star formation or massive concentrations of molecular gas.
The total CO and H _α_ fluxes after thresholding within
the common FoV of our 140 pc resolution images are

Gas and Star Formation in PHANGS Galaxies 11



tabulated in Tab. 2. For H _α_, our threshold is set by
our DIG removal strategy (see _§_ 2.2.5). For CO, we impose a mass surface density threshold that allows us to
work exclusively with securely detected pixels across all
our CO maps. For the CO emission, we do not impose any filtering analogous to what we used to subtract the DIG (from the H _α_ maps). Our reasoning is
that while “diffuse” CO emission has been identified in
galaxies (e.g., Pety et al. 2013; Cald´u-Primo et al. 2015;
Roman-Duval et al. 2016), the physical nature of this
gas remains unclear. Extended CO emission still does
indicate the presence of molecular gas, which may very
well be in marginally bound clouds and available for star
formation. This is not symmetric to the DIG, which represents emission not associated with local massive star

formation. This is an important topic for future exploration, but in the interests of maintaining a simple,
physically-motivated, and reproducible approach, we do
not filter the CO emission.
For reference, our adopted CO threshold is roughly
equivalent to a cut of A V _≈_ 1 mag (e.g., Bohlin et al.
1978). This is close to the limit of A V = 2 mag used
by Heiderman et al. (2010) to define the boundaries of
local molecular clouds in highly resolved maps. That
is, our CO threshold already identifies only pixels where
the emission averaged over a 140 pc beam matches that
seen within highly resolved local GMCs.
Typically, this threshold retains about 75% of the total
flux in the input CO data cube, but this drops to 30%
in the case of the low-mass galaxy NGC 5068.


3.2. _Spatial_ _scales,_ _convolution,_ _and_ _clipping_


We compare the distributions of CO and H _α_ at a series of common spatial resolutions up to 1 _._ 5 kpc. The
best physical resolution shared by our entire sample is
140 pc, which is set by the resolution of our CO map of
NGC4254. We adopt 140 pc as the fiducial measurement
scale for our analysis.
To convolve the data, we smooth the thresholded images using Gaussian convolution kernels. For each convolved map, we sort the map pixels by intensity (from
brightest to faintest), and reject the faintest pixels that
together contribute 2% of the total flux. We verified
that this additional clipping level is sufficient to remove
faint halos that are convolution artifacts. This step sets
a large amount of area to have zero intensity at each
scale without significantly affecting the flux in the analysis. We tested that other reasonable rejection criteria
(between 1 and 5%) do not affect our conclusions.
Finally, we note that while we apply the same methodology to the CO and H _α_ maps, the output depends on
the intrinsic distribution of the emission in the input



map. Faint emission located next to a bright peak in
the input map will tend to be recovered in the lower resolution map, for example, while isolated faint emission
is more likely to fall beneath the 2% clipping threshold
in the lower resolution maps. In this sense, our smoothand-clip strategy is likely to impact our CO and H _α_
maps differently. Our method for DIG removal often
results in high-brightness regions being surrounded by
zero-valued pixels. On the other hand, the mass surface density threshold applied to construct our CO maps
tends to yield contiguous regions of relatively faint emission. We note this as another potential area for improve
ment.


3.3. _Measurements_


Using the pairs of matching resolution CO and H _α_
maps, we classify each pixel into one of four categories:


_•_ _**CO**_ _**only**_ – only CO emission is present, H _α_ emission is not detected at this position and scale.


_•_ _**H**_ _α_ _**only**_ – only H _α_ emission is present, CO emission is not detected at this position and scale.


_•_ _**Overlap**_ – both CO and H _α_ emission are present.


_•_ _**Empty**_ – neither CO nor H _α_ emission are present.


This classification is scale dependent, e.g., a pixel may
be classed as _empty_ at high resolution, _CO_ _only_ at intermediate resolution, and _overlap_ at low resolution. At
high resolution, a non-negligible fraction (on average
around 60-70%) of pixels falls in the last category (see
Fig. 2), indicating that large areas of galaxy disks are not
directly filled with star-forming ISM. At coarse resolution, the number of empty pixels decreases significantly,
giving the impression that the star-forming ISM is ubiquitous. The differences among distributions of empty
pixels among galaxy disks is thus a potentially interesting diagnostic of ISM evolution and galaxy morphology.
In this paper, however, we are most interested in the
impact of host galaxy properties and observing scale on
the relative configuration of the molecular and ionized
gas phases, so we do not analyse the fraction of empty
pixels in detail.
At each spatial scale after removing the empty pixels,
we calculate the fraction of pixels in each of the first
three categories, i.e. with a detection of CO, H _α_ or
both. At fixed scale, these fractions may be plotted as a
pie chart (Section 4.1). The evolution of these fractions
as a function of scale can be illustrated using a bar graph
(Section 4.2).
To assess the uncertainty on our measurements, we repeated our analysis while varying the thresholds for CO

12 Schinnerer, Hughes, Leroy, Groves & PHANGS



**Table** **3.** Line of Sight Fractions at
140 pc Scale.


Name CO only H _α_ only overlap

|Col1|(%) (%) (%)|
|---|---|
|NGC0628<br>NGC3351<br>NGC3627<br>NGC4254<br>NGC4321<br>NGC4535<br>NGC5068<br>NGC5194|4254<br>27<br>1932<br>12<br>3842<br>34<br>1535<br>8<br>6681<br>63<br>1924<br>13<br>4047<br>33<br>1725<br>10<br>4349<br>37<br>5267<br>39<br>1117<br>6<br>3743<br>28<br>4153<br>29<br>2740<br>18<br>3238<br>23<br>4661<br>37<br>2338<br>13<br>3137<br>26<br>27<br>1<br>8690<br>73<br>1220<br>10<br>5559<br>52<br>68<br>4<br>3839<br>35|
|Median<br>Mean|42<br>23<br>37<br>37<br>32<br>31|



Note—Fraction of sightlines with CO
emission only, H _α_ emission only, and both
CO and H _α_ emission. These fractions
represent the numbers corresponding to the
pie charts shown in Fig. 3. The sub- and
super-scripts correspond to the minimum
and maximum values obtained when
different thresholds for positive detection of
CO emission and DIG suppression are used
(see text). The mean (median) values
reported in the final row are the means
(medians) of our fiducial measurements
reported for a given sightline category. Note
that the medians are not re-normalized,
thus the sum will not add up to 100%.


and H _α_ flux. We tested varying the CO threshold between 10 and 15M _⊙_ pc _[−]_ [2] at 140 pc scale, and thresholding at the native resolution of the CO maps using signalto-noise criteria (i.e. 3 and 5 _σ_ cuts in integrated intensity). We also varied the unsharp masking parameters
used for DIG removal, varying the size of the smoothing
kernels by 25%, the gain in the first subtraction step by
25%, and the signal-to-noise threshold of the mask by
_±_ 1 _σ_ . We adopt the minimum and maximum values of
the pixel fractions obtained from this suite of tests as an
indication in the uncertainty of our measurements.


4. RESULTS


Following the methodology in _§_ 3, we measure the fraction of detected sightlines with H _α_ emission, CO emission, or both at each spatial scale. For plots in this section, sightlines with _Hα_ _only_ emission are shaded with
red tones, sightlines with _CO_ _only_ emission are shaded
with dark blue tones, and sightlines with overlapping
CO and H _α_ emission ( _overlap_ ) are shaded with lavender tones.


4.1. _CO_ _and_ _Hα_ _at_ _140_ _pc_ _resolution_


Fig. 2 shows results for all galaxies at 140 pc resolution
in map form. Table 3 summarizes the statistics for these
maps, and Fig. 3 visualizes these statistics as pie charts.



Following _§_ 3, the error bars in Table 3 show the effect
of varying our CO and H _α_ detection thresholds across
their plausible ranges.
At this resolution, emission from one or both of these
tracers is typically present across 50% or more of our survey area. Of the detected sightlines, _CO_ _only_ sightlines
(dark blue) are the most common detections in more
than half of our targets (namely NGC 0628, NGC 4254,
NGC 4321, NGC 4535, NGC 5194). In two targets _Hα_
_only_ sightlines dominate (NGC 3351 and NGC 5068).
NGC 3627 – the most inclined galaxy in our sample with
_i_ _∼_ 55 _[◦]_ – is our only target where sightlines with _over-_
_lapping_ CO and H _α_ emission are the most common.
Across the sample, the median fraction of detected
sightlines that contain _CO_ _only_ emission is _∼_ 40%. This
is comparable to the fraction of _overlap_ sightlines ( _∼_
40%), while the fraction of _Hα_ _only_ sightlines is typically only _∼_ 20%. The clear separation of the CO and
H _α_ emission at our high working resolution (i.e., the
lower overlap fraction compared to sightlines with one
tracer only), and the detection of widespread CO emission above 12.6 M _⊙_ _pc_ _[−]_ [2] without associated H _α_ emission
(typically _CO_ _only_ sightlines are more than 2 _×_ more
abundant than _Hα_ _only_ ones) are two main results of
this paper.
Table 4 (see also Fig. 9) shows the results when we
consider how the CO and H _α_ _fluxes_ (rather than the
number of sightlines) are distributed between different
categories, i.e. instead of the number of pixels in each
category, we consider their respective contribution to the
total CO or H _α_ flux. On average, we find that _∼_ 40% of
the CO flux at 140 pc resolution remains unassociated
with bright H _α_ emission. This is lower than the _∼_ 60%
of _CO_ _only_ sightlines, but implies the same qualitative
conclusion that there is a significant mass fraction of
CO-traced molecular gas without H _α_ emission.
We find a greater discrepancy between the distributions of flux and sightlines for H _α_ . At our fiducial 140 pc
scale, the median _overlap_ fraction for H _α_ emitting sightlines is about two-thirds across our sample. These same
regions contribute a median of _∼_ 80% of the total H _α_
flux. These results indicate that these _overlap_ sightlines, which show both CO and H _α_, tend to have higher
H _α_ intensity than sightlines probing _Hα_ _only_ emission.
This agrees with a visual inspection of the maps. Since
these _overlap_ regions are by definition co-spatial with
CO-emitting molecular gas, they likely suffer from dust
attenuation that we do not account for in the processing of our H _α_ maps (c.f. _§_ 2.2.4 and 2.2.6). The true
flux contribution of these regions is thus probably higher
than the _∼_ 80% that we measure.

tal flux while covering only a few sightlines. Fig. 2 and
Fig. 1 show that the galaxy centers in our sample tend
to have _overlapping_ high intensity CO and H _α_ emission.
In _§_ A, we test the degree to which the centers drive
the discrepancies between our flux- and sightline-based
measurements. To do this, we repeated the calculation
considering only the main galaxy disks, i.e., excluding
the region within a radius of 1 kpc of the reference position listed in Table 1 for all galaxies. For NGC 3351,
we follow Sun et al. (2018) who adopted a larger radius of 1.5 kpc so that the visually distinct inner disk
is entirely inside the central region of NGC 3351. The
regions that we define as central are indicated by yellow
ellipses in Fig. 2. Excluding the central regions from our
analysis improves the agreement between the flux- and
sightline-based measurements for NGC 3351, but does
not significantly alter our results for other galaxies.
_Relation_ _to_ _morphology_ _–_ In most galaxies, the CO
emitting sightlines form coherent, kiloparsec-scale structures such as spiral arms, bars, or rings in the disk. The
sightlines probing H _α_ emission appear more irregular
and patchy than the CO emission, though they generally trace out the same galactic structures as the CO.
_Overlap_ sightlines with both CO and H _α_ emission appear prevalent in the centers of almost all targets (indi


galactic structures traced by CO emission.
In several galaxies with strong spiral arms, we find a
pronounced offset between sightlines probing H _α_ emission and those with _CO only_ . This is most evident along
the spiral arms of NGC 0628, NGC 4321, and NGC 5194,
but the same pattern can be seen in NGC 4254, and
NGC 4535. The sense of the offset is that the sightlines
with H _α_ ( _both_ _overlap_ _and_ _Hα_ _only_ ) tend to lie along
the convex side of the arm, offset from the _CO_ _only_
ones. Assuming that the spiral arms are trailing, this
implies that the _Hα_ _only_ and _overlap_ sightlines appear
offset downstream from the _CO_ _only_ sightlines (when
observing them inside their co-rotation).
The overlap in the central regions appears strong for
the barred galaxies NGC 3351, NGC 3627, NGC 4321,
and NGC 4535. In several of these targets, we see _over-_
_lapping_ CO and H _α_ in the central region, and then again
in the region outside the stellar bar. Along the bar itself, we see predominantly _CO_ _only_ emission, though
this emission is not always present along the full length
of the bar (e.g., see NGC 3351). A similar feature appears in NGC 5194, with _CO_ _only_ sightlines appearing
along segments of the inner spiral arms (features associated with strong streaming motions by Meidt et al.
2013).

14 Schinnerer, Hughes, Leroy, Groves & PHANGS

## **NGC0628 NGC3351 NGC3627 NGC4254** **NGC4321 NGC4535 NGC5068 NGC5194**


**Figure** **3.** Pie charts indicating the fraction of sightlines with CO and H _α_ emission for the 140 pc resolution maps of our eight
galaxies (from _left_ to _right_ : NGC 0628, NGC 3351, NGC 3627 and NGC 4254, _(top_ _row)_ ; ; and NGC 4321, NGC 4535, NGC 5068,
NGC 5194 _(bottom_ _row)_ ). The color coding is dark blue – _CO_ _only_, red – _Hα_ _only_, lavender – _overlap_ .



Here and throughout our analysis, NGC 5068 shows a
distinct morphology: a patchy, incoherent distribution
of CO and H _α_ emitting regions. This galaxy has the
lowest stellar mass, lowest metallicity and latest Hubble type in our sample. It resembles M33, NGC 300 and
the Large Magellanic Cloud, where similar observations
have found tracers of gas and star formation to be incoherent on small scales (Kawamura et al. 2009; Schruba
et al. 2010; Onodera et al. 2010; Gratier et al. 2012; Faesi
et al. 2014). Those studies have postulated that star
formation in dwarf spirals proceeds in a stochastic way,
without any large-scale organization.
_Trend_ _with_ _Galactocentric_ _Radius_ _–_ Visual inspection
of the maps in Figure 2 suggests that many of the _Hα_
_only_ sightlines occur towards the outer edges of our
maps. We quantify this in Figure 4, where we plot
the _CO_ _only_, _Hα_ _only_ and _overlap_ fractions in annuli of
width 0 _._ 2 _R_ 25 . Indeed in all galaxies except NGC 5068,
there is a clear trend for the _Hα only_ fraction to increase
with increasing galactocentric radius. This increase
seems more pronounced in barred galaxies (plotted with
circles and solid lines in Figure 4). At the same time the
radial distribution of the _CO_ sightlines (both _CO_ _only_
and _overlap_ ) shows on average a stronger (decreasing)
trend for barred galaxies than for the three non-barred
ones, however, also with a much wider spread in values. A possible explanation for these trends is the fact



that photoionization bubbles expand more quickly in
low-density media because the Str¨omgren radius scales
as _ρ_ _[−]_ [2] _[/]_ [3], thus larger HII regions are expected at larger
radii where the gas surface density is presumably lower.
Conversely, this decrease in gas surface density should
lead to more isolated patches of molecular gas. As many
other galaxy parameters vary with galactocentric radius,
e.g., metallicity, a secure interpretation of these trends
requires further investigation using a larger sample with
better sampling of galaxy morphological type and stellar

mass.


4.2. _Overlap_ _between_ _CO_ _and_ _Hα_ _as_ _function_ _of_ _spatial_
_scale_


Figs. 5 and 6 illustrate the spatial distribution of CO
and H _α_ emission as we vary the resolution of the maps
(showing maps at 140 pc, 300 pc, 500 pc, and 1000 pc).
In Figs. 7 and 8, we plot the covering fractions of _CO_
_only_, _Hα_ _only_, and _overlap_ regions as a function of spatial scale (from 140 pc up to 1.5 kpc in steps of 100 pc
starting at 200 pc).
_From 140 pc to 500 pc resolution –_ As we blur the maps
from 140 pc to 500 pc resolution, sightlines where CO
and H _α_ emission coincide become more prevalent in all
galaxies. By 500 pc resolution, _overlapping_ (lavender)
sightlines dominate ( _>_ 60%) while _CO_ _only_ sightlines
make up _<_ 25% of the emitting sightlines in all targets.
For most targets, we see a significant slow-down in the

Gas and Star Formation in PHANGS Galaxies 15


**Table** **4.** Line of Sight and Flux Fractions per Tracer at 140 pc Scale.

|Name|ByNumber<br>COSightlines HαSightlines<br>COonly COoverlap Hαonly Hαoverlap<br>(%) (%) (%) (%)|Col3|ByFlux<br>COFlux HαFlux<br>COonly COoverlap Hαonly Hαoverlap<br>(%) (%) (%) (%)|Col5|
|---|---|---|---|---|
|NGC0628<br>NGC3351<br>NGC3627<br>NGC4254<br>NGC4321<br>NGC4535<br>NGC5068<br>NGC5194|52<br>48<br>44<br>56<br>48<br>52<br>58<br>42<br>57<br>43<br>60<br>40<br>16<br>84<br>59<br>41|34<br>66<br>77<br>23<br>29<br>71<br>23<br>77<br>46<br>54<br>43<br>57<br>88<br>12<br>14<br>86|43<br>57<br>21<br>79<br>31<br>69<br>45<br>55<br>38<br>62<br>45<br>55<br>14<br>86<br>43<br>57|18<br>82<br>24<br>76<br>12<br>88<br>11<br>89<br>24<br>76<br>22<br>78<br>73<br>27<br>7<br>93|
|Median<br>Mean|57<br>48<br>49<br>51|43<br>66<br>44<br>56|43<br>62<br>35<br>65|22<br>82<br>24<br>76|



Note—Fraction of CO and H II-associated H _α_ emission in the overlap and non-overlap regions of the maps at
140 pc resolution. The four left columns list the fraction of sightlines (i.e. by number). The remaining columns
list the fraction of the flux in each tracer). **Note** **that** **the** **medians** **are** **not** **re-normalized,** **thus** **the** **sum**
**will** **not** **add** **up** **to** **100%.**


**CO only** **Hα only** **CO + Hα**


**Figure** **4.** Variation of the overlap fraction at 140 pc resolution as a function of galactocentric radius. The _x_ -axis is normalized
by _R_ 25, and the curves are color-coded by increasing stellar mass. Barred galaxies are shown with circles and solid lines,
non-barred galaxies with squares and dashed curves. The classification of Tab. 1 is adopted.



increase of the fraction of _CO_ _only_ sightlines at spatial
scales of _∼_ 150-200 pc. The exceptions are NGC 4254 and
NGC 5194, where the _CO_ _only_ fraction continuously decreases from 140 pc to larger scales.
Most of the evolution of _overlap_ fraction and structure
of _CO_ _only_ emission occurs over this range, 140 _−_ 500 pc.
As the resolution degrades, the detailed morphology visible at high resolution evolves toward a simple, amorphous geometry. Structures that were prominent at
sharper resolution, such as spiral arms and bars, disappear and emission fills in the region between galactic
structures. As this happens, the region covered by _over-_
_lapping_ CO and H _α_ emission grows from patches to form
coherent structures along spiral arms and stellar bars.
Over this range, in all but two galaxies (NGC 3351 and
NGC 5068) the _Hα_ _only_ covering fraction shows less significant evolution than the _CO_ _only_ or _overlap_ fraction.



Three-quarters of our sample show no variation in _Hα_
_only_ covering fraction for scales of 300 pc and larger. In
these cases, the _Hα_ _only_ regions often appear as mostly
isolated, compact regions, often located at large galactocentric radius.

_Beyond 500 pc resolution –_ As we blur the maps to resolutions greater than 500 pc, the _overlap_ sightlines tend
to become unified structures that include the galaxy nucleus. By 1.0 kpc resolution, the _CO_ _only_ (dark blue)
sightlines tend to no longer trace galactic structures,
but rather appear spread across the galaxy. This heavy
overlap between CO and H _α_ emission at coarse resolution agrees with numerous previous studies showing a
tight correlation between these quantities at this resolution (e.g., Bigiel et al. 2008; Leroy et al. 2008; Liu et al.
2011; Leroy et al. 2013; Bolatto et al. 2017).

16 Schinnerer, Hughes, Leroy, Groves & PHANGS

## **140pc 300pc 500pc 1kpc** **NGC0628**

## **NGC3351**

## **NGC3627**

## **NGC4254**


**Figure** **5.** Galaxy maps showing regions with overlapping CO and H _α_ emission (lavender), _CO_ _only_ (dark blue) and _Hα_ _only_
emission CO (red) at spatial resolutions of 140, 300 and 500 and 1000 pc ( _left_ _to_ _right_ ) for NGC 628, NGC 3351, NGC 3627 and
NGC 4254.( _top_ _to_ _bottom_ ).



Overall, the changes in morphology and covering fraction beyond 500 pc resolution appear less pronounced
than those between 140 pc and 500 pc. For the majority
of our sample, the most significant changes in the fraction of _overlapping_ (lavender) sightlines occur between
140 and 500 pc resolution. The fact that this overlap
emerges only after averaging agrees with previous observations of increasing scatter in the correlation between
molecular gas and star formation tracers with decreasing spatial scale (e.g., Bigiel et al. 2008; Schruba et al.
2010; Onodera et al. 2010; Leroy et al. 2013; Kruijssen
et al. 2019).



5. DISCUSSION


We have analyzed a sample of matched resolution,
high completeness, wide area CO and H _α_ maps, which
trace molecular gas and high-mass star formation. Consistent with previous observational studies targeting individual galaxies (e.g. M33 and M51, Schruba et al.
2010; Meidt et al. 2013), we find a large reservoir of
molecular gas not directly associated with high-mass
star formation at high spatial resolution. A significant
non-star-forming molecular gas reservoir in galaxies is
expected from numerical simulations (e.g. Semenov et al.
2017). This component has been almost impossible to

Gas and Star Formation in PHANGS Galaxies 17

## **140pc 300pc 500pc 1kpc** **NGC4321**

## **NGC4535**

## **NGC5068**

## **NGC5194**


**Figure** **6.** Galaxy maps for NGC 4321, NGC 4535, NGC 5068 and NGC 5194 ( _top_ _to_ _bottom_ ). (For details see caption of Fig. 5.)



identify in previous, low resolution surveys because the
apparent overlap between tracers of molecular gas and
star formation increases with degrading resolution. At
the coarsest resolutions that we study, _∼_ 1 _._ 0 _−_ 1 _._ 5 kpc,
CO and H _α_ emission appear almost completely coincident.

We also clearly observe the effects of galactic dynamics in the maps: bars, spiral arms, and central regions
all stand out in our analysis. This dynamically-induced
complexity indicates that the timescales associated with
different steps in the star formation process (e.g. cloud
formation, cloud dispersal) may depend on galactic environment. We thus expect timescale estimates based
on galaxy-wide measurements and simple cycling ar


guments to mask intrinsic variation of star formation
timescales within galaxies.
With this caveat in mind, we derive rough estimates
for the time required for the molecular gas in our sample
galaxies to cycle between a quiescent and actively starforming state (see _§_ 5.2). Our measurements imply that
this timescale is _∼_ 1 to 2 times longer than the characteristic lifetime of an Hii region. This is broadly consistent with estimates for molecular cloud lifetimes, but
much shorter than the global molecular gas depletion
times of _∼_ 2 Gyr observed for nearby galaxies (Leroy et
al. 2008). An investigation of molecular cloud lifetimes
across a subset of PHANGS galaxies using an alternative
formalism is presented by Chevance et al. (subm.).

18 Schinnerer, Hughes, Leroy, Groves & PHANGS


**CO only** **Hα only** **CO + Hα**


**Figure** **7.** Fraction of pixels belonging to the different categories as a function of spatial scale. From left to right, the three
panels show the variation of _CO_ _only_ regions, _Hα_ _only_ regions and regions with _overlapping_ CO and H _α_ emission. As in the
previous figures the pixel fractions are defined using the total number of pixels containing emission from either CO and/or H _α_
(see text for details).


**NGC0628** **NGC3351** **NGC3627** **NGC4254**











**NGC4321** **NGC4535** **NGC5068** **NGC5194**


**Figure** **8.** Bar graphs indicating the fraction of sightlines with CO and H _α_ emission across the range of spatial scales that we
explore. The order of the galaxies and the color code are the same as for Fig. 3. The spatial scales of 140pc, 500pc and 1kpc
are highlighted by a black outline.



5.1. _Quiescent_ _molecular_ _gas_ _at_ _high_ _resolution,_
_overlap_ _at_ _low_ _resolution_


The relative contributions of _CO_ _only_, _Hα_ _only_ and
_overlap_ sightlines vary dramatically with spatial scale.
At _∼_ 140 pc resolution, we find a roughly equal number
of CO-emitting sightlines (at and above our H 2 surface
density threshold of 12 _._ 6 M _⊙_ pc _[−]_ [2] ) with and without associated H _α_ emission in our sample galaxies. The _CO_
_only_ sightlines contribute _∼_ 40% of the total CO flux
above this threshold. This implies the presence of a significant reservoir of quiescent molecular gas.
This apparently quiescent molecular gas could have
several distinct physical origins. This gas may be genuinely non-star-forming, due to large-scale dynamical
effects that stabilize the gas (e.g., Meidt et al. 2013,
subm.) or the disruptive effect of stellar feedback (e.g.
Krumholz, & McKee 2005; Ostriker et al. 2010). Alternatively, it could be forming stars that are not massive



enough to generate the ionizing photons needed for significant H _α_ emission. High-mass stars could be forming
behind a screen of dust that obscures H _α_ photons (see
Table 2). Or the gas could still be in the process of collapsing, reflecting recently formed molecular clouds that
have not yet “ramped up” star formation (e.g., Lee et
al. 2016).
**Quiescent** **gas** **and** **spatial** **scale:** This quiescent
molecular gas is only accessible thanks to the high physical resolution of our data. For our adopted CO and
H _α_ thresholds, the fraction of _CO_ _only_ sightlines decreases from _∼_ 40% at 140 pc resolution to ≲ 15% at
500 pc. Our adopted fiducial scale of 140 pc is a pragmatic choice, not a physical one. For five galaxies in our
sample, the best matching spatial resolution of our data
is 90 pc or better, allowing us to test whether the fraction of _CO_ _only_ sightlines in galaxies is larger at higher
physical resolution. We repeated the analysis described

Gas and Star Formation in PHANGS Galaxies 19



in Section 3 for the CO and H _α_ maps of these galaxies at
90 pc resolution, using a threshold of 19 _._ 5 M _⊙_ pc _[−]_ [2] (i.e.
the 3 _σ_ mass surface density sensitivity of our NGC 5194
data at 90 pc resolution). We find that the fraction of
_CO_ _only_ sightlines in all galaxies shows a relative increase of 5 to 20% as the resolution improves from 140
to 90 pc. The fraction of _Hα_ _only_ sightlines typically
shows a similar relative increase, while the fraction of
_overlap_ sightlines shows a relative decrease of _∼_ 30% as
the resolution improves.
At coarser resolution than 140 pc, the quiescent CO
emission rapidly vanishes as the resolution is degraded.
The rapid decrease in _CO_ _only_ sightlines between 140
and 500 pc resolution is accompanied by a significant
increase in the fraction of _overlap_ sightlines (from _∼_ 30%
to _∼_ 65%) across this range of scales.
For most of our sample, the visible morphology of CO
emission also changes over this spatial range: as the
resolution degrades, the initially sparse, patchy _over-_
_lap_ sightlines become more common, while the _overlap_
regions spread out, replacing the _CO_ _only_ regions and
covering the main morphological features of the galaxy.
Scale-dependent variations in the fraction and spatial
distribution of the _Hα_ _only_ sightlines are less marked in
our current, small sample of galaxies. This is because
the _Hα_ _only_ regions tend to be relatively isolated, distinct regions towards the outer parts of our maps.
At resolution coarser than _∼_ 500 pc, the _overlap_ sightlines cover most of the mapped area in all targets. At
these scales, differences in the morphology of the CO
and H _α_ emission disappear. Even major morphological
features of galaxies (e.g., prominent spiral arms, very
luminous H II regions in outer disks) start to “wash out”
and are mostly indistinguishable on spatial scales above
≳1.0 kpc.
Our results agree with previous observations showing
how star formation scaling relations – i.e. the power
law scaling between the molecular gas and star formation rate (SFR) surface density, where SFR is typically
traced by H _α_ emission – vary with spatial scale. Several studies have demonstrated that the scatter in the

molecular gas depletion time decreases as the spatial
scale of the molecular gas and SFR surface density measurements increases. These works include high resolution studies of individual galaxies (e.g. Blanc et al. 2009;
Schruba et al. 2010; Onodera et al. 2010; Kreckel et al.
2018; Kruijssen et al. 2019) and coarser resolution studies of larger galaxy samples (Bigiel et al. 2008; Leroy et
al. 2013). To our knowledge, our work here represents
the best combination of resolution (140 pc across the
sample) and sample size (8 galaxies) to date.



**Table** **5.** Inferred Relative Gas Cycling
Timescales by Sightlines at Various Scales.

|Name|fscale = fCO−only+foverlap fHα−only+foverlap|
|---|---|
||140 pc<br>300 pc<br>500 pc<br>1000 pc|
|NGC 0628<br>NGC 3351<br>NGC 3627<br>NGC 4254<br>NGC 4321<br>NGC 4535<br>NGC 5068<br>NGC 5194|1.4<br>1.2<br>1.0<br>0.9<br>0.4<br>0.6<br>0.7<br>0.8<br>1.4<br>1.1<br>1.0<br>0.9<br>1.8<br>1.2<br>1.0<br>0.9<br>1.3<br>1.0<br>0.9<br>0.8<br>1.4<br>1.3<br>1.1<br>0.9<br>0.1<br>0.5<br>0.7<br>0.8<br>2.1<br>1.4<br>1.2<br>1.0|
|Median<br>Mean|1.4<br>1.2<br>1.0<br>0.9<br>1.2<br>1.0<br>1.0<br>0.9|



Note— **The** **reported** **values** **are** **derived** **using**
**Eq.** **1** **and** **need** **to** **be** **multiplied** **by** **the**
**assumed** _t_ _Hα_ **,** **i.e.** **the** **time** **an** Hii **region** **is**
**visible** **above** **our** **thresholds.** See text for
discussion of reasonable values for _t_ _Hα_ .


5.2. _Temporal_ _interpretations_


Under the assumption of simple steady-state cycling,
every star-forming unit progresses from a cold gas cloud
that is not yet forming stars ( _CO_ _only_ ) to a cold gas
cloud that is actively forming massive stars ( _overlap_ regions) to a region of massive young stars from which
the cold gas has been entirely dispersed ( _Hα_ _only_ ). In
this case, the covering fractions that we measure are a
reflection of the time spent by a star-forming region in
each of these different evolutionary phases.
Versions of this steady-state cycling heuristic have
been used by Kawamura et al. (2009) to estimate the
lifetimes of molecular clouds in the LMC, and by Gratier
et al. (2012) and Corbelli et al. (2017) to characterize
the cloud life-cycle in M 33. Recently, Battersby et al.
(2017) applied a similar approach to Milky Way observations to determine the timescales for dense molecular gas
structures (i.e. clumps) to evolve from starless to starforming. Schruba et al. (2010) invoked a similar cycling
scenario to explain the scatter and bias in the molecular
gas depletion time measured at high spatial resolution
in M 33. Feldmann et al. (2011) also considered this
phenomenon in terms of the scatter (see also Leroy et
al. 2013). Building on this work, Kruijssen & Longmore
(2014) and Kruijssen et al. (2018) developed a general
formalism to derive the evolutionary timescales of starforming regions from concentric apertures centered on
peaks identified at different wavelengths. This formalism has been applied to CO and H _α_ maps of the spiral
galaxy NGC 300, an M 33 analog, in order to estimate
the typical lifetime of molecular clouds and character

20 Schinnerer, Hughes, Leroy, Groves & PHANGS



istic duration of star formation feedback in that galaxy
(Kruijssen et al. 2019). Analogous arguments have been
used to infer timescales in other fields, including, e.g., to
measure the life cycle of protostars (e.g., see review in
Dunham et al. 2014). All these methods require an externally calibrated fiducial clock, e.g., the time _t_ _Hα_ over
which an Hii region is visible, to translate between population/mass/area statistics and an absolute timescale.
Here we apply a simple version of this approach to
molecular gas that is visible above a fixed surface density threshold, treating individual pixels as discrete starforming units. The lifetime of the cold molecular gas in
a star-forming unit is then


_[f]_ _[overla][p]_
_t_ _gas_ = _t_ _Hα_ _×_ _[f]_ _[CO][−][onl][y]_ [ +] = _t_ _Hα_ _× f_ _scale_ _,_ (1)

_f_ H _α−only_ + _f_ _overlap_


where _f_ _CO_ is the fraction of _CO_ _only_ sightlines, _f_ _Hα_ the
fraction of _Hα_ _only_ sightlines, and _f_ _overlap_ the fraction
of _overlap_ sightlines. Then _f_ _scale_ represents the scaling
factor to translate from the fiducial timescale, here _t_ _Hα_,
to the lifetime for a cold gas structure.


5.2.1. _Timescales_


Table 5 reports the results of Eq. 1 applied to our
sample at various scales using the numbers derived in
_§_ 4. As the resolution improves (i.e., the spatial scale
decreases), regions with _overlapping_ H _α_ and CO emission tend to occupy a diminishing fraction of sightlines
(see Fig. 8). The ratio _f_ _scale_ thus tends to increase for
galaxies where _CO_ _only_ sightlines are prominent, while
it decreases rapidly for galaxies where _Hα only_ sightlines
dominate (i.e., NGC 3351 and NGC 5068). If we were to
improve upon our 140 pc resolution, we would expect
these trends to continue. This highlights some natural
next steps to improve on the current data treatment (see
_§_ 5.5).
For most of our targets, these measurements imply a
median CO visibility timescale of 1 _._ 4 _×_ the H _α_ visibility
timescale _t_ _Hα_ at 140 pc resolution. Typical estimates
for the visibility time of H _α_ are 5 _−_ 10 Myr [6] . Binaries,
extinction, and other effects may complicate the picture,
but taking these numbers at face value, Table 5 suggests
molecular cloud lifetimes of _∼_ 10 _−_ 15 Myr at our best
resolution of 140 pc.
While there is a clear dependence on scale (and
the data have some limitations, see _§_ 5.5), these short


6 Based on population synthesis models, Kennicutt & Evans
(2012) estimate that 90% of emission is emitted within _∼_ 10 Myr
with a mean age of _∼_ 3 Myr for the associated stellar population
(for other estimates, see, e.g. Leroy et al. 2012; Haydon et al.
2018).



timescales are in reasonable agreement with measurements of molecular cloud lifetimes in other galaxies in
the literature (see above). For the specific galaxies in our
sample besides NGC 5068 and NGC 3351, our estimates
also agree within a factor of _∼_ 2 with cloud timescale
estimates obtained by Chevance et al. (subm.) applying
the formalism of Kruijssen et al. (2018) to these systems.
This robustness to adopted methodology suggests that
both sets of results do indeed reflect the true underlying
cycling times.
The order of magnitude of _t_ _gas_ also agrees well with
theoretical estimates of the timescale for star formation.

It is comparable to the crossing or free-fall time for individual molecular clouds (e.g., see Heyer et al. 2009;
Fukui, & Kawamura 2010, for typical cloud properties),
including those in our sample (e.g., see Utomo et al.
2018, for direct estimates). Many models have taken either the crossing time (e.g., Elmegreen 2000) or the freefall time (e.g., Krumholz, & McKee 2005) as the relevant
timescale for star formation. Numerical models find similar results, e.g., based on recent highly resolved simulations of galaxy disks, Semenov et al. (2018) quote star
formation timescales of _∼_ 5-15 Myr. Our measurements
support the idea that the onset of star formation and
dispersal of clouds occurs over roughly this timescale.


5.2.2. _A_ _more_ _dynamic_ _view_


The simple evolutionary sketch underlying Equation
1 may be too simple to capture the evolution of real
regions in the molecular ISM. Recent numerical simulations of galaxies suggest that molecular gas may cycle
in and out of a bound, cloud-like state several times before finally participating in the formation of stars (e.g.
Dobbs et al. 2015; Semenov et al. 2017), and that this
may explain the discrepancy between the molecular gas
depletion times measured for entire galaxies ( _∼_ 2 Gyr,
e.g. Leroy et al. 2008) and individual molecular clouds
(a few hundred Myr, e.g. Evans et al. 2009; Heiderman
et al. 2010). In this case, not every patch of visible CO
emission will form stars in the near future.

Moreover, grouping together CO-bright stellar bars
and H _α_ -bright regions at large galactocentric radius will
not capture local, physical cycling between gas and star
formation. Even in star-forming regions, the visible COH _α_ offsets associated with spiral arms (e.g., prominently
observed in M 51, see e.g. Schinnerer et al. 2013, 2017)
suggest that a one-dimensional flow model (e.g., Meidt
et al. 2015; Dobbs, & Pringle 2013) may be more appropriate than stochastic cycling.
The trends of decreasing _f_ _scale_ with increasing resolution for 6 of our 8 galaxies might also reflect this
more dynamic view. For example, in the Semenov et

Gas and Star Formation in PHANGS Galaxies 21



al. (2017) model, gas cycles in and out of a star-forming
state several times before a fraction of the star-forming
gas is converted into stars. Thus with increasing resolution we start to probe gas cycling between a star-forming
and non-star-forming state which is setting the timescale
_t_ _gas_ we infer. The inverse trend in _f_ _scale_ observed for
especially NGC 5068 and potentially NGC 3351 may be
set by their rather short timescale for _localized_ star formation to occur. This timescale is set by stellar feedback
that quickly removes gas from the star-forming state (see
also, e.g., Kruijssen et al. 2019) and such galaxies are in
the “self-regulation” regime.


5.3. _Visible_ _effects_ _of_ _galactic_ _dynamics_


Our maps show clear signatures of galactic dynamics.
In addition to the high overlap fraction in most galaxy
nuclei, we observe signatures of the suppression of star
formation in bars and offsets between H _α_ and molecular
gas emission along spiral arms.


**Central** **regions:** All our eight galaxies show prominent _overlap_ regions in the central 1 kpc (see Fig. 5).
Close inspection of the CO intensity maps and H _α_ images presented in Fig. 1 suggests that the overlap is arising mainly due to H _α_ emission related to (a) central
star formation mostly distributed in so-called nuclear
star-forming rings (e.g. NGC 3351 and NGC 4321 are
listed in the AINUR catalog of Comer´on et al. 2010) or
along the stellar bar (in NGC 5068) or (b) the presence of
AGN (e.g., as good examples see NGC 3627, NGC 5194)
where the H _α_ emission is coming from the ionized gas
in the narrow line region (e.g. in NGC 5194; Blanc et al.
2009). Thus, unlike the Central Molecular Zone (CMZ)
in our own Galaxy, other nearby galaxies can show significant star formation, especially in the nuclear starforming rings that are typically found in barred galaxies (see also review by Kennicutt 1998b). Our inability to discriminate between H _α_ emission arising from
truly star-forming structures or from a central AGN is
a caveat for the interpretation of our results in galaxy
centers (see _§_ 5.4 for further discussion).


**Stellar** **bars:** Observational and theoretical work on

the role of stellar bars in star formation still draws some
what conflicting conclusions about the roles for these
structures. It is clear that bars help drive material to
the central regions of galaxies, but whether they enhance or suppress star formation along the way remains
debated (e.g., see Meidt et al. 2013; Renaud et al. 2016;
James & Percival 2018). Two of our targets, NGC 3351
and NGC 4535, show strong signatures of suppressed
star formation along a strong stellar bar. Two more,
NGC 3627 and NGC 4321 show some evidence of this

phenomenon.



The signatures are a clear gap between the spiral arms,
where overlapping CO and H _α_ emission appears common, and the center. CO emission remains visible in this
gap, while H _α_ emission appears to be largely absent. In
NGC 3627 particular, the phenomenon is harder to identify because of the brightness of star-forming complexes
at the bar ends (e.g., see Beuther et al. 2017). A similar
depression in star formation has been identified along
the spiral arms in NGC 5194 and attributed to streaming motions along the spiral arms (not a stellar bar) by
Meidt et al. (2013).
In theoretical calculations, the high shear and/or diverging streamlines (caused by changing orbits) present
at the location of the gas lanes along the stellar bar either prevent clouds from forming or tears them apart before star formation can happen (e.g. Athanassoula 1992;
Regan et al. 1997). Observationally, this “star formation desert” (along the stellar bar) is not evident in all
barred galaxies (see e.g. Sheth et al. 2000; James & Percival 2018). This suggests that the exact bar properties
and/or the time evolution of bars may also be important
to the suppression of star formation.
Overall, our data provide support for the idea that
star formation in molecular gas is inhibited along many
stellar bars. Despite the presence of bright CO emission,
Hii regions appear less common in these regions.


**Spiral** **arms:** For several galaxies we find a pronounced spatial offset between CO and H _α_ emission
along spiral arms. In these cases, we observe a general
pattern where _CO only_ sightlines are more prominent on
the concave side, while _overlap_ sightlines are found along
the convex side of a spiral arm, with _Hα_ _only_ sightlines
sitting outside the _overlap_ regions away from the _CO_
_only_ regions.
Figure 2 shows impressive examples of this phenomenon in the grand design spiral galaxies NGC 0628
(particular at smaller galactocentric radii; see also Fig.
1 in Kreckel et al. 2018) and NGC 5194 (e.g. Schinnerer
et al. 2013, 2017). The spiral arms emanating from the
stellar bars in NGC 4321 and NGC 4535 also exhibit offsets along significant arm segments. This suggests that
a similar mechanism causes this offset in grand-design
spirals and spiral arms dynamically linked to stellar
bars. Assuming the spiral arms are trailing, the H _α_
offsets occur on the downstream side consistent with
expectations for a rotating spiral density wave (inside
co-rotation) (for a sketch see, e.g., Fig. 1 of Pour-Imani
et al. 2016).


**Trends** **with** **global** **properties:** We compared the
overlap fraction and amount of apparently quiescent CO
emission to the integrated properties of the host galaxy,
including stellar mass (M star ), star formation rate (SFR)

22 Schinnerer, Hughes, Leroy, Groves & PHANGS



and specific SFR (sSFR _≡_ SFR/M _star_ ). While our sample of 8 galaxies represents a significant improvement
compared to previous work, a much larger sample will
be required to measure quantitative relationships. Still,
some trends are already evident from these first results.
First, targets that have a large fraction of _CO_ _only_
sightlines at 140 pc resolution are all more massive
than log(M _⋆_ [M _⊙_ ]) = 10 _._ 2, tend to have higher SFRs
(SFR[M _⊙_ yr _[−]_ [1] ] _>_ 2), and also tend to lie above the
average stellar mass–SFR relation. Such galaxies tend
to be rich in molecular gas compared to lower mass
and more quiescent galaxies. This result suggests that,
at least at any given moment, a large fraction of the
gas in such galaxies may not be immediately associated
with high mass star formation. We do caution that our
present sample is heavily biased towards such objects.
By contrast, _Hα_ _only_ sightlines are most prominent
in the two lowest mass and lowest SFR galaxies which
also have the latest (NGC 5068) and earliest Hubble type
(NGC 3351) of the sample. Though we do not include
M33 in the analysis, this would appear to be consistent
with the widespread H _α_ and confined CO emission visible in that galaxy (e.g., see Schruba et al. 2010; Druard
et al. 2014; Corbelli et al. 2017). Here, sensitivity, conversion factor effects, and the choice of thresholds will
play an important role, because these are also among
our most quiescent targets.
The one galaxy where _overlap_ sightlines dominate
(NGC 3627) exhibits on average low SFR and sSFR values and is also part of a group currently undergoing a
large-scale interaction.
No trend with the presence or absence of a (largescale) stellar bar is evident. Similarly, we find no clear
trend with the presence or absence of an AGN (all galaxies with log(M _⋆_ (M _⊙_ ) ≳ 10 _._ 4, i.e. 5/8 galaxies, show
evidence for an AGN). This is not surprising given the
small sample size, the relatively low number of sightlines
directly associated with the galaxy center or bar, and the
temporal evolution expected for both phenomena.


**Does** **feedback** **or** **galactic** **dynamics** **drive** **the**
**CO** **morphology?** In a series of recent papers, Semenov et al. (2017, 2018) put forward a star formation
model based on high resolution simulations of gas and
star formation in galaxy disks. Semenov et al. (2018)
distinguish two distinct regimes, which may relate to
the morphology of CO and H _α_ emission seen in our
observations. In the “self-regulation” regime, the lifetime of gas in the star-forming state is limited by consumption via star formation and feedback. A stochastic, patchy appearance might be expected, with the CO
emission shaped by stellar feedback. By contrast, in the
“dynamics-regulation” regime, the lifetime of the star


forming gas is limited by dynamical processes. In this
case, they expect the star formation to reflect the underlying distribution of the cold gas rather than being
shaped by star formation and/or associated feedback.
In our observations, both the star-forming and quiescent molecular gas trace distinct bars, rings, and arms in
most galaxies. In other words, it appears that the star
formation traces the underlying molecular gas distribution, which in turn traces the underlying potential (see
Fig. 4). The patchy stochastic appearance that we might
expect for morphology dominated by self-regulation is
most prominent in the outer disk of NGC 3351 and the
low mass galaxy NGC 5068. This qualitative comparison, as well as the discussion above, demonstrates that
the different dynamical environments and host galaxy
properties do lead to varying conditions for star formation and that a simple assumption of self-regulation by
stellar feedback that results in stochastic, isolated regions is probably too simplistic for many galaxies.


5.4. _Distributions_ _by_ _luminosity_ _vs._ _distributions_ _by_
_area_ _and_ _role_ _of_ _galaxy_ _centers_


For three of our targets, bright CO emission from the
center (see Fig. 1; NGC 3351, NGC 4321, and NGC 4535)
makes a large fractional contribution to the total CO
luminosity (e.g., see flux-weighted histograms in Figure
1 of Sun et al. 2018). When we consider the distribution
of flux, these bright centers exert a large influence on the
fractions of emission associated with _CO_ _only_, _Hα_ _only_,
and _overlap_ regions (see Fig. 9 and Tab. 4). Because they
cover relatively little area, the centers have a weaker
effect on the distributions of covering fraction.
Excluding the centers leads to a slightly better agreement between a flux-weighted approach and a sightlinebased approach. There are still differences between the
two approaches, however. In general, the fraction of
luminosity associated with _overlapping_ CO and H _α_ is
larger than the fraction of _overlapping_ sightlines. This
implies that the intensity of CO emission is higher in
regions that also show H _α_ emission and, similarly, that
the brighter H _α_ emission is associated with regions of
higher CO emission.
Brighter CO emission in regions with H _α_ emission
could be expected if star formation increases the temperature and excitation of the CO gas. This appears
to be the case in a subset of our targets (T. Saito; priv.
comm.). It may also reflect that the molecular gas structure differs between actively star-forming regions and
quiescent regions. This also appears to be the case, with
higher surface density gas being associated with active
regions.

Gas and Star Formation in PHANGS Galaxies 23



5.5. _Impact_ _of_ _methodology_ _and_ _next_ _steps_


We adopt relatively simple methods to identify pixels
tracing CO emission and likely Hii regions that could
bias our results. It also highlights natural next steps as
we apply the method to a larger sample of galaxies.
Our fixed CO threshold leads to variable completeness
across our sample (see Sun et al. 2018). Specifically,
using our fixed threshold, we recover a lower fraction of
the total CO emission in low mass galaxies and outer
disks compared to massive spiral galaxies. Hughes et
al. (2013) showed that molecular clouds in such systems
have lower molecular gas surface densities (see also Sun
et al. 2018; Schruba et al. 2019). This appears strongest
in NGC 5068 and the outer part of NGC 3351, but may
be present at large radii in most of our sample.
A bias against recovering all of the CO emission
present affects the inferred _f_ _scale_, driving the apparent
cycling time to artificially low values. Future work will
need to address that the CO emission in some regions of
our sample is faint compared to our sensitivity. This can
be achieved by using statistical methods that account for
the effects of noise and by informing the measurements
using the known total CO flux from each region of the
galaxy.
Local variations of the CO-to-H 2 conversion factor,
_α_ CO, could also impact our analysis. In this case, our
estimates for CO-emitting fractions “by flux” would no
longer straightforwardly correspond to a mass fraction
of the molecular gas reservoir. Moreover, the meaning of
our adopted threshold would change across the galaxy.
Previous work does not suggest enormous _α_ CO variations across this specific sample. Sandstrom et al. (2013)
derived _α_ CO at _∼_ kpc resolution for five galaxies in our
sample (NGC 0628, NGC 3351, NGC 3627, NGC 4254,
NGC 4321) and saw no significant variations across the
disks or with radius (excluding some central depression
which cover only a small area in our analysis). Similarly, Leroy et al. (2017a) found a basically constant
_α_ CO across the PAWS area in NGC 5194. Nonetheless,
in a preliminary comparison, we do find some modest
differences between molecular cloud properties and CO
excitation in the _CO_ _only_ regions and _overlap_ regions.
Likewise, our identification method for Hii regions in
narrowband H _α_ maps has an impact on our results. If
we insufficiently subtract the DIG, we expect to find an
artifical increase of _Hα_ _only_ sightlines at small scales.
This, in turn, will drive _f_ _scale_ to artificially low values.
Though we inspected our images and verified our algorithm works to first order, adopting a single simple
algorithm to analyze galaxy centers, spiral arms, and
low density flocculent galaxies will likely yield significant biases. Compounding this situation, the H _α_ line



emission is significantly affected by extinction, and both
flux-based approaches and the interpretation of thresholds depend on local, robust extinction corrections.
More sophisticated morphological separation methods
(e.g., newer versions of Hiiphot; Thilker et al. 2000) offer some prospect to improve the situation. The main
hope for improvement here comes from the use of optical
integral field spectroscopy (IFS). IFS allows for simultaneous correction for internal extinction and improved
tools for distinguishing the H _α_ emission from DIG and
shocks or X-ray Dominated Regions (XDRs) associated
with AGN. VLT/MUSE IFS data are currently being
obtained for _∼_ 19 PHANGS targets, which have the
prospect to then act as a training set for improved morphological and multi-wavelength methods for Hii region
identification and extinction corrections. Initial tests
on the MUSE data for four galaxies yield Hii region
masks that are more restricted than those constructed

in _§_ 2.2.5. This suggests that our Hii region identification scheme may bias us to slightly low _f_ _scale_ and thus
shorter CO-emitting region lifetimes.
Despite these caveats, we emphasize that most of our
analysis focuses on the presence or absence of CO or
H _α_ emission, not their exact translation into physical
quantities. We made this choice exactly to minimize
the bias due to uncertain conversions between CO and

H 2 or H _α_ and a local star formation rate.


6. SUMMARY AND CONCLUSIONS


We compare high angular resolution observations of
CO line emission to narrowband H _α_ imaging in eight
nearby star-forming galaxies. We use PHANGS-ALMA
CO (2-1) imaging for seven targets and a PdBI CO (1-0)
map for one target. The H _α_ data come from a mixture
of new and literature sources. Together, the data allow
us to compare the distributions of molecular gas and star
formation at a common spatial scale of 140 pc. This represents roughly an order of magnitude increase in sample
size compared to previous high resolution comparisons
of CO and H _α_ emission, which have mostly compared
highly resolved CO and H _α_ in individual Local Group
galaxies.
We use these data to study the spatial relationship between the cold molecular gas reservoir and H II regions,
which serve as signposts of recent high-mass star formation. We adopt a simple, reproducible methodology
that quantifies overlap between the tracers, in both area
and flux, as a function of scale. We classify each line
of sight at each scale according to its contents: it either
contains _only_ _CO_, _only_ _Hα_, or _overlapping_ CO and H _α_
emission. We measure the fraction of area in each cat

24 Schinnerer, Hughes, Leroy, Groves & PHANGS



egory as a function of the resolution of the data. Our
main findings are:


1. _CO_ _only_ emission (corresponding to H 2 surface
densities of ≳ 12 _._ 6 M _⊙_ pc _[−]_ [2] ) without associated
H _α_ emission (above SFR surface densities of
0.0014 and 0.0036 M _⊙_ yr _[−]_ [1] kpc _[−]_ [2] depending on
the galaxy target) is very common in our sample at 140 pc resolution. Our targets show a
median of _∼_ 40% of detected sightlines in this
category, though this numerical value is specific to
our adopted thresholds for CO and H _α_ emission.
Taken at face value, this implies a large amount of
molecular gas without associated recent high-mass
star formation. This gas may be in the process of
collapsing, may be dynamically unsuited to form
stars, or may already be forming low-mass stars.


2. Lines of sight where CO and H _α overlap_ represent
the next most common category, also accounting
for median _∼_ 40% of the sightlines at 140 pc resolution. That is, H II regions typically coincide with
molecular gas at this resolution. Our lowest mass
target and our earliest Hubble type system represent notable exceptions to this statement. In those
targets, Hii region sightlines are the most common
type of sightline. We note some concerns related
to the impact of completeness, adopted thresholds,
and conversion factor on our results for these tar
gets.


3. The balance between _CO_ _only_, _Hα_ _only_, and _over-_
_lapping_ lines of sight is a strong function of spatial
scale. As we degrade the resolution of our maps,
the fraction of _CO_ _only_ emission – tracing apparently quiescent molecular gas – decreases, while a
steadily increasing fraction of the CO emission becomes associated with _overlapping_ sightlines. By
1 kpc resolution, _∼_ 75% of all sightlines, on average, show overlapping H _α_ and CO emission. At
resolutions coarser than _∼_ 1 kpc, the main morphological features of our sample galaxies are indistinct. Little information about the relative dis
tributions of CO and H _α_ emission or their relation

to galactic morphology remains at these coarse resolutions. This behavior is consistent with litera
ture results that report a decrease in the scatter
of the scaling relations when going from small to
large scales.


4. At 140 pc resolution, the spatial distributions of
both CO emission and H II regions follow galactic
structures such as rings, spiral arms and bars. CO



emission appears to faithfully trace these “backbones” of the underlying galactic potential. This
highlights the role of these stellar structures in organizing the molecular gas reservoir and star formation. H _α_ emission follows these structures as

well, but in a more spotty fashion. Compared to
the CO emission, H _α_ emission appears more localized. This patchy appearance of the H II regions
partially reflects our processing of the H _α_ maps to
remove the DIG contribution, and the sensitivity
of our H _α_ data.


5. Taking the simplest statistical approach, our
galaxy-averaged measurements of the fractions
of sightlines with CO, H _α_ emission or both at
140 pc resolution imply that, on average, molecular gas cycles through a non-star-forming state
to a star-forming state and then is dispersed on a
median timescale that is 1 _._ 4 _×_ longer than the visibility time for H _α_ emission (i.e., _∼_ 10 _−_ 15 Myr).
Considering that the physical resolution of our
data does not yet attain the characteristic size
of molecular clouds and H II regions in the Milky
Way, we expect that this timescale represents a
lower limit.


6. H _α_ emission appears offset from CO in strong spiral arms, in the sense that the H _α_ emission tends
to lie along the convex side of the spiral arm compared to the CO emission. H _α_ emission is weak
or absent along some stellar bars, while sightlines
along the (often linear) gas lanes along strong bars
frequently show _CO_ _only_ emission. Both these results reflect the influence of dynamical features on
the molecular gas distribution and star formation
activity in our galaxies.


7. We find some trend between the _overlap_ fraction
(computed at 140 pc resolution) and the fraction
of recovered total CO flux in the maps. Further
we see some evidence for trends relating stellar
mass, SFR, and sSFR to the overall balance between _CO_ _only_, _Hα_ _only_, and _overlap_ fractions.
The sense of the trends is that massive, highSFR, high-sSFR galaxies tend to show high _CO_
_only_ fractions. Confirming these trends will require analysis of a significantly larger and more
diverse sample.


The methodology presented in this paper can be easily applied to much larger samples, including the full
PHANGS-ALMA and paired H _α_ survey now underway.
This larger sample should allow us to identify potential
trends with global galaxy parameters more robustly. In

Gas and Star Formation in PHANGS Galaxies 25



particular, more sensitive maps of dwarf spirals and the
outer parts of galaxies should help illuminate the nature
of systems like NGC 5068 and NGC 3351 which showed
distinctly different trends from the remaining sample.
Other follow-up studies (utilizing a larger sample) include the detailed investigation of how physical properties of the CO-traced molecular gas vary between starforming and non-star-forming regions, and how galactic
dynamics drives the suppression of star formation.
A straightforward future extension of the methodology is the implementation of a more generalized form
utilizing the information from the cross-distribution of
the CO and H _α_ emission (via calculating cross cumulative distribution functions, xCDFs) without the need to
establish flux thresholds, and compare this information
from xCDFs with those from traditional CDFs. This

kind of analysis offers a robust, rich way to characterize
the joint distributions of CO and H _α_ emission in galaxies, yielding measurements ideally suited for comparison
with simulations. As well as trends with galactocentric radius, comparing the statistics of both traditional
and ’cross’ distributions among different galactic environments should provide further insight on how local
conditions influence star formation and feedback.


This work was carried out as part of the PHANGS
collaboration. We thank the anonymous referee for constructive feedback that helped improve the manuscript.
We thank B. Venemans for help with the absolute astrometric calibration of the H _α_ maps used for analysis. ES, CF, and TS acknowledge funding from the
European Research Council (ERC) under the European Unions Horizon 2020 research and innovation
programme (grant agreement No. 694343). AH acknowledges support by the Programme National Cosmology et Galaxies (PNCG) of CNRS/INSU with INP
and IN2P3, co-funded by CEA and CNES, and by the
Programme National Physique et Chimie du Milieu
Interstellaire (PCMI) of CNRS/INSU with INC/INP
co-funded by CEA and CNES. The work of AKL is
partially supported by the National Science Foundation under Grants No. 1615105, 1615109,and 1653300.
AKL also acknowledges partial support from NASA
ADAP grants NNX16AF48G and NNX17AF39G. BG
gratefully acknowledges the support of the Australian
Research Council as the recipient of a Future Fellowship (FT140101202). KK gratefully acknowledges support from grant KR 4598/1-2 from the DFG Priority Program 1573. FB acknowledges funding from the
European Research Council (ERC) under the European Unions Horizon 2020 research and innovation pro


gramme (grant agreement No. 726384). SG acknowledges support from the Deutsche Forschungsgemeinschaft via the Collaborative Research Centre (SFB 881)
“The Milky Way System” (subprojects B1, B2, and B8)
and from the Heidelberg cluster of excellence EXC 2181
“STRUCTURES: A unifying approach to emergent phenomena in the physical world, mathematics, and complex data” funded by the German Excellence Strategy.
JMDK and MC acknowledge funding from the German
Research Foundation (DFG) in the form of an Emmy
Noether Research Group (grant number KR4801/1-1),
and the DFG Sachbeihilfe (grant number KR4801/21). JMDK acknowledges funding from the European
Research Council (ERC) under the European Unions
Horizon 2020 research and innovation programme via
the ERC Starting Grant MUSTANG (grant agreement
number 714907). JP acknowledges support from the
Programme National Physique et Chimie du Milieu
Interstellaire (PCMI) of CNRS/INSU with INC/INP
co-funded by CEA and CNES. ER acknowledges the
support of the Natural Sciences and Engineering Research Council of Canada (NSERC), funding reference
number RGPIN-2017-03987. The work of JS amd DU

is partially supported by the National Science Foundation under Grants No. 1615105, 1615109, and 1653300.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA #2012.1.00650.S, ADS/JAO.ALMA
#2015.1.00925.S, ADS/JAO.ALMA #2015.1.00956.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together
with NRC (Canada), NSC and ASIAA (Taiwan), and
KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is
operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the
National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This
paper makes use of the PdBI Arcsecond Whirlpool Survey (Schinnerer et al. 2013; Pety et al. 2013). The
IRAM 30m telescope and PdBI are run by IRAM,
which is supported by INSU/CNRS (France), MPG
(Germany) and IGN (Spain). This work has made use
of data from the European Space Agency (ESA) mission _Gaia_ [(https://www.cosmos.esa.int/gaia), processed](https://www.cosmos.esa.int/gaia)
by the _Gaia_ Data Processing and Analysis Consortium
(DPAC, [https://www.cosmos.esa.int/web/gaia/dpac/](https://www.cosmos.esa.int/web/gaia/dpac/consortium)
[consortium).](https://www.cosmos.esa.int/web/gaia/dpac/consortium) Funding for the DPAC has been provided
by national institutions, in particular the institutions
participating in the _Gaia_ Multilateral Agreement.


_Facilities:_ ALMA, IRAM (PdBI and 30m), MPG 2.2m
(WFI)

26 Schinnerer, Hughes, Leroy, Groves & PHANGS


APPENDIX


A. EXCLUDING THE CENTRAL REGIONS OF GALAXIES


About half the galaxies in our sample show a non-neglible difference in the fractions of quiescent and star-forming
molecular gas when these fractions are defined by sightline or by flux (see _§_ 4.1). To test whether CO-bright galaxy
centers are responsible for this difference, we repeat our analysis presented in that section, excluding the central region
from our measurements. For simplicity, we adopt the central region definition used by Sun et al. (2018), i.e. we
define the center as the region within 1 kpc of the galaxy reference position (see Table 1). We follow Sun et al. (2018)
who adopted a larger radius of 1.5 kpc so that the visually distinct inner disk is entirely inside the central region of
NGC 3351. The resulting resulting fractions are listed in Tab. 6 and Tab. 7 and compared in Fig. 9. As can be seen
from the tables and figure, the centers can explain some of the differences between fractions measured by sightline or
by flux for some galaxies, but not in all cases.


**NGC0628** **NGC3351** **NGC3627** **NGC4254**


**A** **B** **C** **D** **E** **F** **G** **H** **I** **J** **A** **B** **C** **D** **E** **F** **G** **H** **I** **J** **A** **B** **C** **D** **E** **F** **G** **H** **I** **J** **A** **B** **C** **D** **E** **F** **G** **H** **I** **J**


**A** **B** **C** **D** **E** **F** **G** **H** **I** **J** **A** **B** **C** **D** **E** **F** **G** **H** **I** **J** **A** **B** **C** **D** **E** **F** **G** **H** **I** **J** **A** **B** **C** **D** **E** **F** **G** **H** **I** **J**


**NGC4321** **NGC4535** **NGC5068** **NGC5194**


**Figure** **9.** Bar graphs summarizing the impact of different assumptions (sightlines vs. flux; full FoV vs. disk only) for the
different fractions of pixels in our sample galaxies. The color coding is dark blue – _CO_ _only_, red – _Hα_ _only_, lavender – _overlap_ .
The bar graphs for each individual galaxy show the following (labels as indicated on the x-axis): relative distribution of _CO_
_only_, _Hα_ _only_ and _overlap_ sightlines for our FoV ( **A**, analoguous to Fig. 3) and disk only ( **B** ); relative distribution of sightlines
tracing CO emission for our FoV ( **C** ) and disk only ( **D** ) vs. distribution of CO flux ( **E** – our FoV, **F** – disk only); and relative
distribution of sightlines tracing H _α_ emission for our FoV ( **G** ) and disk only ( **H** ) vs. distribution of H _α_ flux ( **I** – our FoV, **J** –
disk only).


REFERENCES



Athanassoula, E. 1992, MNRAS, 259, 345


Azimlu, M., Marciniak, R., & Barmby, P. 2011, AJ, 142, 139


Battersby, C., Bally, J., & Svoboda, B. 2017, ApJ, 835, 263


Beuther, H., Meidt, S., Schinnerer, E., Paladino, R., &


Leroy, A. 2017, A&A, 597, A85


Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846


Bigiel, F., Leroy, A. K., Walter, F., et al. 2011, ApJL, 730,


L13


Blanc, G. A., Heiderman, A., Gebhardt, K., Evans, N. J.,


II, & Adams, J. 2009, ApJ, 704, 842



Blanc, G. A., Weinzirl, T., Song, M., et al. 2013, AJ, 145,


138


Bohlin, R. C., Savage, B. D., & Drake, J. F. 1978, ApJ,


224, 132


Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A,


51, 207


Bolatto, A. D., Wong, T., Utomo, D., et al. 2017, ApJ, 846,


159


Bradley, T. R., Knapen, J. H., Beckman, J. E., & Folkes,


S. L. 2006, A&A, 459, L13

Gas and Star Formation in PHANGS Galaxies 27


**Table** **6.** Line of Sight Fractions between Tracers at 140 pc Scale for Disks
Only.


Name CO only H _α_ only overlap

|Col1|(%) (%) (%)|
|---|---|
|NGC0628<br>NGC3351<br>NGC3627<br>NGC4254<br>NGC4321<br>NGC4535<br>NGC5068<br>NGC5194|42<br>20<br>38<br>7<br>76<br>17<br>40<br>17<br>43<br>52<br>11<br>37<br>41<br>29<br>31<br>44<br>25<br>31<br>2<br>87<br>11<br>57<br>7<br>36|
|Median<br>Mean|42<br>25<br>36<br>36<br>34<br>30|



Note—Fraction of sightlines with CO
emission only, H _α_ emission only, and both
CO and H _α_ emission _for_ _disks_ _only_, i.e.
excluding emission arising inside the central
region. This table is analogous to Tab. 3 in
the main text. Note that the medians are
not re-normalized, thus the sum will not
add up to 100%.


**Table** **7.** Line of Sight and Flux Fractions per Tracer at 140 pc Scale.

|Name|ByNumber<br>COSightlines HαSightlines<br>COonly COoverlap Hαonly Hαoverlap<br>(%) (%) (%) (%)|Col3|ByFlux<br>COFlux HαFlux<br>COonly COoverlap Hαonly Hαoverlap<br>(%) (%) (%) (%)|Col5|
|---|---|---|---|---|
|NGC 0628<br>NGC 3351<br>NGC 3627<br>NGC 4254<br>NGC 4321<br>NGC 4535<br>NGC 5068<br>NGC 5194|51<br>49<br>35<br>65<br>38<br>62<br>58<br>42<br>65<br>35<br>63<br>37<br>20<br>80<br>60<br>40|36<br>64<br>74<br>26<br>34<br>66<br>18<br>82<br>40<br>60<br>40<br>60<br>88<br>12<br>17<br>83|42<br>58<br>33<br>67<br>23<br>77<br>43<br>57<br>54<br>46<br>50<br>50<br>17<br>83<br>46<br>54|20<br>80<br>61<br>39<br>14<br>86<br>10<br>90<br>25<br>75<br>24<br>76<br>68<br>32<br>9<br>91|
|Median<br>Mean|55<br>45<br>49<br>51|36<br>64<br>41<br>59|42<br>58<br>39<br>61|20<br>80<br>27<br>73|



Note—Fraction of sightlines with _CO_ _only_ emission, _Hα_ _only_ emission, and both CO and H _α_ _overlapping_
emission _for_ _disks_ _only_, i.e. excluding emission arising from within the central region. This table is analogous to
Tab. 4 in the main text. Note that the medians are not re-normalized, thus the sum will not add up to 100%.



Cald´u-Primo, A., Schruba, A., Walter, F., et al. 2015, AJ,


149, 76


Chandar, R., Whitmore, B. C., Calzetti, D., et al. 2011,


ApJ, 727, 88


Chevance, M., et al. 2019, MNRAS, subm.


Clark, P. C., & Glover, S. C. O. 2015, MNRAS, 452, 2057


Colombo, D., Hughes, A., Schinnerer, E., et al. 2014, ApJ,


784, 3



Comer´on, S., Knapen, J. H., Beckman, J. E., et al. 2010,


MNRAS, 402, 2462


Corbelli, E., Braine, J., Bandiera, R., et al. 2017, A&A,


601, A146


Davis, T. A., Young, L. M., Crocker, A. F., et al. 2014,


MNRAS, 444, 3427


Dobbs, C. L., & Pringle, J. E. 2013, MNRAS, 432, 653

28 Schinnerer, Hughes, Leroy, Groves & PHANGS



Dobbs, C. L., Pringle, J. E., & Duarte-Cabral, A. 2015,

MNRAS, 446, 3608

Druard, C., Braine, J., Schuster, K. F., et al. 2014, A&A,

567, A118

Dunham, M. M., Stutz, A. M., Allen, L. E., et al. 2014,

Protostars and Planets VI, 195

Egusa, F., Mentuch Cooper, E., Koda, J., & Baba, J. 2017,

MNRAS, 465, 460

Elmegreen, B. G. 2000, ApJ, 530, 277

Evans, N. J., Dunham, M. M., Jørgensen, J. K., et al. 2009,

ApJS, 181, 321

Faesi, C. M., Lada, C. J., Forbrich, J., et al. 2014, ApJ,

789, 1, 81

Feldmann, R., Gnedin, N. Y., & Kravtsov, A. V. 2011,

ApJ, 732, 115

Fukui, Y., & Kawamura, A. 2010, ARA&A, 48, 547

Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al.

2016, A&A, 595, A2

Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al.

2018, A&A, 616, A1

Gratier, P., Braine, J., Rodriguez-Fernandez, N. J., et al.

2012, A&A, 542, A108

Haffner, L. M., Dettmar, R.-J., Beckman, J. E., et al. 2009,

Reviews of Modern Physics, 81, 969

Haydon, D. T., Kruijssen, J. M. D., Hygate, A. P. S., et al.

2018, arXiv e-prints, arXiv:1810.10897

Heiderman, A., Evans, N. J., Allen, L. E., et al. 2010, ApJ,

723, 1019

Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583

Heyer, M., Krawczyk, C., Duval, J., et al. 2009, ApJ, 699,

1092

Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73

Hughes, A., Meidt, S. E., Colombo, D., et al. 2013, ApJ,

779, 46

James, P. A., & Percival, S. M. 2018, MNRAS, 474, 3101

Kaplan, K. F., Jogee, S., Kewley, L., et al. 2016, MNRAS,

462, 1642

Kawamura, A., Mizuno, Y., Minamidani, T., et al. 2009,

ApJS, 184, 1

Kennicutt, R. C., Jr. 1998, ApJ, 498, 541

Kennicutt, R. C., Jr. 1998, ARA&A, 36, 189

Kennicutt, R. C., Jr., Armus, L., Bendo, G., et al. 2003,

PASP, 115, 928

Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011,

PASP, 123, 1347

Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531

Knapen, J. H., Stedman, S., Bramich, D. M., Folkes, S. L.,

& Bradley, T. R. 2004, A&A, 426, 1135

Kreckel, K., Blanc, G. A., Schinnerer, E., et al. 2016, ApJ,

827, 103



Kreckel, K., Groves, B., Schinnerer, E., et al. 2013, ApJ,

771, 62

Kreckel, K., Faesi, C., Kruijssen, J. M. D., et al. 2018,

ApJL, 863, L21

Kruijssen, J. M. D., & Longmore, S. N. 2014, MNRAS, 439,

3239

Kruijssen, J. M. D., Pfeffer, J. L., Reina-Campos, M., et al.

2019, MNRAS, 486, 3180

Kruijssen, J. M. D., Schruba, A., Hygate, A. P. S., et al.

2018, MNRAS, 479, 1866

Krumholz, M. R., & McKee, C. F. 2005, ApJ, 630,

Lee, E. J., Miville-Deschˆenes, M.-A., & Murray, N. W.

2016, ApJ, 833, 229

Leroy, A. K., Bigiel, F., de Blok, W. J. G., et al. 2012, AJ,

144, 3

Leroy, A. K., Hughes, A., Schruba, A., et al. 2016, ApJ,

831, 16

Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019,

ApJS, 244, 24

Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2017, ApJ,

846, 71

Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136,

2782

Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ,

146, 19

Leroy, A. K., et al. 2019, XXX, in prep.

Levy, R. C., Bolatto, A. D., S´anchez, S. F., et al. 2019,

ApJ, 882, 84

Liu, G., Koda, J., Calzetti, D., Fukuhara, M., & Momose,

R. 2011, ApJ, 735, 63

Liu, G., Calzetti, D., Kennicutt, R. C., Jr., et al. 2013,

ApJ, 772, 27

Meidt, S. E., et al. 2019, ApJ, subm.

Meidt, S. E., Hughes, A., Dobbs, C. L., et al. 2015, ApJ,

806, 72

Meidt, S. E., Schinnerer, E., Garc´ıa-Burillo, S., et al. 2013,

ApJ, 779, 45

Meurer, G. R., Hanish, D. J., Ferguson, H. C., et al. 2006,

ApJS, 165, 307

Momose, R., Koda, J., Kennicutt, R. C., Jr., et al. 2013,

ApJL, 772, L13

Monet, D. 1998, USNO-A2.0, by Monet, David. [Flagstaff,
AZ] : U.S. Naval Observatory, c1998. . United States

Naval Observatory.,

Oey, M. S., Parker, J. S., Mikles, V. J., & Zhang, X. 2003,

AJ, 126, 2317

Oey, M. S., Meurer, G. R., Yelda, S., et al. 2007, ApJ, 661,

801

Onodera, S., Kuno, N., Tosaki, T., et al. 2010, ApJL, 722,

L127

Gas and Star Formation in PHANGS Galaxies 29



Ostriker, E. C., McKee, C. F., & Leroy, A. K. 2010, ApJ,

721, 975

Pety, J., Schinnerer, E., Leroy, A. K., et al. 2013, ApJ, 779,

Pour-Imani, H., Kennefick, D., Kennefick, J., et al. 2016,

ApJL, 827, L2

Querejeta, M., Schinnerer, E., Schruba, A., et al. 2019,

A&A, 625, A19

Razza, A., et al. 2019, in prep.

Regan, M. W., Vogel, S. N., & Teuben, P. J. 1997, ApJL,

482, L143

Renaud, F., Famaey, B., & Kroupa, P. 2016, MNRAS, 463,

3637

Roman-Duval, J., Heyer, M., Brunt, C. M., et al. 2016,

ApJ, 818, 144

Rossa, J., & Dettmar, R.-J. 2003, A&A, 406, 505

Rousseau-Nepton, L., Robert, C., Martin, R. P., et al. 2018,

MNRAS, 477, 4152

Saintonge, A., Kauffmann, G., Wang, J., et al. 2011,

MNRAS, 415, 61

Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017,

ApJS, 233, 22

Sanders, D. B., Scoville, N. Z., & Solomon, P. M. 1985,

ApJ, 289, 373

Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013,

ApJ, 777, 5

Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779,

42

Schinnerer, E., Meidt, S. E., Colombo, D., et al. 2017, ApJ,

836, 62

Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103

Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ,

883, 2

Schruba, A., Leroy, A. K., Walter, F., Sandstrom, K., &

Rosolowsky, E. 2010, ApJ, 722, 1699



Schruba, A., Leroy, A. K., Walter, F., et al. 2011, AJ, 142,


37


Scoville, N. Z., Polletta, M., Ewald, S., et al. 2001, AJ, 122,


3017


Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2017,


ApJ, 845, 133


Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2018,


ApJ, 861, 4


Sharma, S., Corbelli, E., Giovanardi, C., Hunt, L. K., &


Palla, F. 2011, A&A, 534, A96


Sheth, K., Regan, M. W., Vogel, S. N., et al. 2000, ApJ,


532, 221


Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860,


172


Thilker, D. A., Braun, R., & Walterbos, R. A. M. 2000, AJ,


120, 3070


Thilker, D. A., Walterbos, R. A. M., Braun, R., & Hoopes,


C. G. 2002, AJ, 124, 3118


Tomiˇci´c, N., Kreckel, K., Groves, B., et al. 2017, ApJ, 844,


155


Weilbacher, P. M., Monreal-Ibero, A., Verhamme, A., et al.


2018, A&A, 611, A95


Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ,


850, 208


Whitmore, B. C., Chandar, R., Kim, H., et al. 2011, ApJ,


729, 78


Wong, T., & Blitz, L. 2002, ApJ, 569, 157


Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861,


L18


Young, J. S., Xie, S., Tacconi, L., et al. 1995, ApJS, 98, 219


</paper>

## Items to check

```json
[
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "comparison HII region masks",
  "failed_quote": "agrees sufficiently well with masks based on Hiiphot"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Median f_scale at 140 pc = 1.4 dimensionless",
  "failed_quote": "Median Mean|1.4 1.2 1.0 0.9"
 }
]
```
