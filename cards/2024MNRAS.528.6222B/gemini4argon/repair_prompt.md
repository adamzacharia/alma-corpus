# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.528.6222B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–57 (2022) Preprint 3 November 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **Characterisation of Herschel -selected strong lens candidates through HST** **and sub-mm/mm observations**


E. Borsato, [1] _[★]_ L. Marchetti, [2] _[,]_ [3] _[,]_ [36] M. Negrello, [4] E. M. Corsini, [1] _[,]_ [5] D. Wake, [6] A. Amvrosiadis, [7] A. J. Baker, [8] _[,]_ [9]

T. J. L. C. Bakx, [10] _[,]_ [11] A. Beelen, [12] S. Berta, [13] D. L. Clements, [14] A. Cooray, [15] P. Cox, [16] H. Dannerbauer, [17] _[,]_ [18]

G. de Zotti, [5] S. Dye, [19] S. A. Eales, [4] A. Enia, [20] _[,]_ [21] D. Farrah, [22] _[,]_ [23] J. Gonzalez-Nuevo, [24] _[,]_ [25] D. H. Hughes, [26]

D. Ismail, [27] S. Jin, [28] _[,]_ [29] A. Lapi, [30] M. D. Lehnert, [31] R. Neri, [13] I. Pérez-Fournon, [17] _[,]_ [18] G. Rodighiero, [1] _[,]_ [5]

D. Scott, [32] S. Serjeant, [33] F. Stanley, [34] S. Urquhart, [33] P. van der Werf, [35] M. Vaccari, [3] _[,]_ [36] _[,]_ [37] L. Wang, [38] _[,]_ [39]

C. Yang, [34] A. Young [8]


Affiliations are listed at the end of the paper


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

We have carried out _HST_ snapshot observations at 1.1 _𝜇_ m of 281 candidate strongly lensed galaxies identified in the wide-area
extragalactic surveys conducted with the _Herschel_ _space_ _observatory_ . Our candidates comprise systems with flux densities at
500 _𝜇_ m _𝑆_ 500 ≥ 80 mJy. We model and subtract the surface brightness distribution for 130 systems, where we identify a candidate
for the foreground lens candidate. After combining visual inspection, archival high-resolution observations, and lens subtraction,
we divide the systems into different classes according to their lensing likelihood. We confirm 65 systems to be lensed. Of these,
30 are new discoveries. We successfully perform lens modelling and source reconstruction on 23 systems, where the foreground
lenses are isolated galaxies and the background sources are detected in the _HST_ images. All the systems are successfully modelled
as a singular isothermal ellipsoid. The Einstein radii of the lenses and the magnifications of the background sources are consistent
with previous studies. However, the background source circularised radii (between 0.34 kpc and 1.30 kpc) are ∼3 times smaller
than the ones measured in the sub-mm/mm for a similarly selected and partially overlapping sample. We compare our lenses with
those in the SLACS survey, confirming that our lens-independent selection is more effective at picking up fainter and diffuse
galaxies and group lenses. This sample represents the first step towards characterising the near-IR properties and stellar masses
of the gravitationally lensed dusty star-forming galaxies.


**Key words:** gravitational lensing: strong – galaxies: high-redshift – galaxies: photometry



**1** **INTRODUCTION**


The very bright tail of the number counts of galaxies at sub-millimetre
and millimetre wavelengths comprises a mixture of distinct galaxy
populations: low-redshift ( _𝑧_ ∼ _[<]_ 0 _._ 1) late-type galaxies, flat spectrum
radio sources, high-redshift ( _𝑧_ ∼ _[>]_ 1) gravitationally-lensed dusty starforming galaxies (DSFGs), and hyper-luminous infrared galaxies
(HyLIRGs) (Negrello et al. 2007, 2010, 2017; Wardlow et al. 2013;
Vieira et al. 2013; Nayyeri et al. 2016; Rowan-Robinson et al. 2018;
Ward et al. 2022). This distribution allows us to efficiently select
strong gravitational lensing systems by combining a flux density cut
(e.g., _𝑆_ 500 ≥ 100 mJy at 500 _𝜇_ m) with shallow optical and radio
surveys to remove the contaminants. This approach became effective
in the last decade thanks to the wide-area surveys carried out, in
particular, by the _Herschel Space Observatory_ (Pilbratt et al. 2010)
and the South Pole Telescope (SPT; e.g., Vieira et al. 2010; Carlstrom
et al. 2011; Mocanu et al. 2013). Negrello et al. (2017) and then Ward


_★_ E-mail: edoardo.borsato.1@phd.unipd.it


© 2022 The Authors



et al. (2022) identified 80+11 candidate lensed galaxies with _𝑆_ 500 ≥
100 mJy in the _>_ 600 deg [2] of the _Herschel_ -Astrophysical Terahertz
Large Area Survey (H-ATLAS; Eales et al. 2010). Bakx et al. (2018)
extended the selection down to _𝑆_ 500 = 80 mJy by including DSFGs
with photometric redshift _𝑧_ phot _>_ 2, as derived from the sub-mm
colours (the _Herschel_ bright sources – HerBS – sample). At flux
densities _𝑆_ 500 _<_ 100 mJy, the number density of unlensed DSFGs
exponentially increases (see Negrello et al. 2007; Cai et al. 2013 for
details); therefore, the HerBS sample is expected to contain a mixture
of both lensed and unlensed DSFGs, with the latter dominating over
the former at _𝑆_ 500 _𝜇_ m ∼ _[<]_ 100 mJy. Wardlow et al. (2013) identified 42
candidate high- _𝑧_ lensed DSFGs with _𝑆_ 500 ≥ 80 mJy in the 95 deg [2]

of the _Herschel_ Multi-tiered Extragalactic Survey (HerMES, Oliver
et al. 2012), while Nayyeri et al. (2016) published a catalogue of 77
candidate lensed DSFGs with _𝑆_ 500 ≥ 100 mJy in the 300 deg [2] of the
HerMES Large Mode Survey (HeLMS, Oliver et al. 2012) and the
79 deg [2] of the _Herschel_ Stripe 82 Survey (HerS; Viero et al. 2014).
Following a different approach, González-Nuevo et al. (2012, 2019)
lowered the SPIRE flux density cut ( _𝑆_ 350 ≥ 85 mJy at 350 _𝜇_ m and

2 _E. Borsato et al._


_𝑆_ 250 ≥ 35 mJy at 250 _𝜇_ m) constraints on both the Herschel-SPIRE
colours and the presence of close-by near-infrared (near-IR) sources
acting as potential lensing galaxies, increasing the number of strong
lens candidates by a factor of ∼ 5.
Using a similar approach to Negrello et al. (2010) but at mm wavelengths, the SPT collaboration produced a sample of 48 candidate
lensed galaxies with deboosted _𝑆_ 1 _._ 4 ≥ 20 mJy at 1.4 mm over an
area of 2500 deg [2] (Vieira et al. 2013; Spilker et al. 2016; Everett
et al. 2020; Reuter et al. 2020; Cai et al. 2022). Lastly, Cañameras et al. (2015) applied a combination of flux density cut and
colour selection on candidates extracted from the _Planck_ Catalogue
of Compact Sources, identifying 11 lensed DSFGs. Later, Harrington et al. (2016), Berman et al. (2022), and Kamieneski et al. (2023a)
identified 30 strongly lensed galaxies by cross-matching the _Planck_
catalogue, the _WISE_ All-Sky Survey, and the _Herschel_ surveys. Three
and two of these systems were also included in the Wardlow et al.
(2013) and Negrello et al. (2017) samples, respectively.
To confirm whether a sub-mm/mm bright galaxy is gravitationally
lensed, high-resolution follow-up observations are needed. The multiple images of a background source, which are the distinctive features
of lensing, have typical separations of a few arcseconds. They can
not be resolved by either _Herschel_ (FWHM ≃ 18, 24, and 35 arcsec
at 250, 350, and 500 _𝜇_ m, respectively) or SPT (FWHM ≃ 1 arcmin
at 1.4 mm). Because lensed DSFGs emit mostly in the far-IR/submm/mm (Negrello et al. 2014), the best way to detect and characterise
the multiple images is via high-angular resolution observations at
sub-mm/mm wavelengths obtained with interferometers, such as the
Atacama Large Millimetre Array (ALMA), the Submillimetre Array (SMA), and the Northern Extended Millimetre Array (NOEMA)
(e.g., Bussmann et al. 2013; Amvrosiadis et al. 2018). These data
can then be used to reconstruct the intrinsic morphology of the background DSFGs via lens modelling techniques (e.g., Dye et al. 2018;
Maresca et al. 2022), which provide crucial information on the spatial distribution of the gas and dust and on the star-formation rate
surface density in those galaxies (e.g., Cañameras et al. 2017; Yang
et al. 2019; Sun et al. 2021; Jarugula et al. 2021; Dye et al. 2022).
Interestingly, at these wavelengths, the object acting as a lens, which
is usually a massive red-and-dead foreground elliptical galaxy with
very low dust content, remains undetected, thus facilitating the source
reconstruction. However, it is not possible to constrain all the physical properties of the lensed DSFGs with the long wavelength data
alone. Indeed, one parameter that remains elusive is the background
source stellar mass, which is crucial to understand better the evolutionary stage of a galaxy (e.g., Renzini 2009). Constraining the
stellar mass of the background sources requires them to be detected
at optical/near-IR wavelengths, where the emission of the foreground
lens dominates (e.g., Negrello et al. 2014). Hence, careful lens photometric modelling and subtraction are needed to reveal the lensed
background sources in the high-resolution optical/near-IR images.
This analysis represents the first step to constrain the stellar masses
by fitting the background source spectral energy distribution (SED,
Negrello et al. 2014).
So far, high-resolution near-IR follow-up observations of tens of
sub-mm/mm selected candidate lensed galaxies have been obtained
in the near-IR with the _Hubble Space Telescope_ ( _HST_ ; e.g., Negrello
et al. 2014) and with ground-based telescopes exploiting adaptive
optics (e.g., Fu et al. 2012; Calanog et al. 2014; Messias et al. 2014).
These observations are characterised by long integration times (i.e.,
from tens of minutes to hours) and have been mainly aimed at identifying and studying the background source. Instead, we report on
_HST_ snapshot observations of a much larger sample of 281 sub-mm
bright _Herschel_ -selected systems. The primary goal of these short


MNRAS **000**, 1–57 (2022)



observations is to efficiently confirm the gravitational lensing nature
of the sub-mm selected systems either by detecting the characteristic
lensing features, such as arcs or multiple images, or by identifying
massive low- _𝑧_ early-type galaxies (ETGs) located at the position of
the sub-mm emission and thus potentially acting as the lens. These
observations represent the first step to enable more detailed followups to study the background sources and, at the same time, provide
data to study the properties of the lenses.
This paper is organized as it follows. Section 2 presents the full
sample of candidates we have followed up with _HST_ and details the
_HST_ snapshot observations. Section 3 discusses the visual classification of the _HST_ images. In Section 4, we focus on the sub-sample
of systems that show clear evidence of lensing features in the _HST_
images and describe the fitting techniques adopted for modelling the
surface brightness of the lenses. Section 5 presents the lens modelling
we apply and the results for a subsample of candidates. Section 6 discusses our results, focusing on the comparison with the Sloan Lens
ACS Survey (SLACS), while the main conclusions are summarised
in Section 7. In this paper we adopt the values of _𝐻_ 0 = 67 _._ 7 km s [−][1]

Mpc [−][1], Ω 0 _,_ m = 0 _._ 31, and Ω 0 _,_ Λ = 0 _._ 69 from Planck18 cosmology
(see Planck Collaboration VI 2020 [1] for details).


**2** **SAMPLE, OBSERVATIONS, AND DATA REDUCTION**


**2.1** **Sample selection**


Our sample consists of candidate _𝑧_ ∼ _[>]_ 1 (gravitationally lensed and
unlensed) DSFGs extracted from the _Herschel_ wide-area extragalactic surveys (i.e., H-ATLAS, HerMES, HeLMS, and HerS) for which
we obtained the _HST_ snapshot observations described in the following section. Many of our targets are selected from Bussmann
et al. (2013), Wardlow et al. (2013), Calanog et al. (2014), Nayyeri
et al. (2016), Negrello et al. (2017), and Bakx et al. (2018). Due to the
varying quality of _Herschel_ and ancillary data available at the time of
these different works, they could select candidates only in specific sky
areas and applied slightly different selection criteria to identify their
most reliable candidate lensed system. Nevertheless, these selections
generally relied upon a bright flux density cut at 500 _𝜇_ m following
the approach by Negrello et al. (2010). In summary, the objects we
observed with _HST_ were identified as candidate lensing systems by
having either the flux density measured at 500 _𝜇_ m _𝑆_ 500 ∼ _[>]_ 100 mJy
(as done in Wardlow et al. 2013, Nayyeri et al. 2016, Negrello et al.
2017) or by having _𝑆_ 500 ∼ _[>]_ 80 mJy and photometric redshifts of the
potential background source _𝑧>_ 2 (as the candidates presented in
Bakx et al. 2018). Exceptions are the candidates from Calanog et al.
(2014) that were selected by means of their bright ( _𝑆_ 500 ∼ _[>]_ 80 mJy)
SPIRE 500 _𝜇_ m flux densities, but also thanks to multiwavelength
observations and specific source-extraction techniques applied on
deeper _Herschel_ maps available only for the HerMES fields. We refer the reader to Calanog et al. (2014) for more details. As a result,
Calanog et al. (2014) candidates include targets with flux densities at
500 _𝜇_ m below the flux limit used in the other quoted works. For the
candidates in the H-ATLAS survey, we use the flux densities coming
from Harris et al. (2012), Negrello et al. (2017), and Bakx et al.
(2018), when available, if not, we adopt the flux densities published
in the H-ATLAS Data Release 1 (DR1, Valiante et al. 2016) or Data
Release 2 (DR2, Maddox et al. 2018). The candidates belonging to
the other surveys were covered by the catalogues of Wardlow et al.


1 Available in the `astropy.cosmology` package through `astropy` see, Astropy Collaboration et al. 2013, 2018).

(2013), Bussmann et al. (2013, 2015), Calanog et al. (2014), and
Nayyeri et al. (2016).
The goal of our _HST_ observations is to observe as many candidates
as possible to confirm their nature by means of the higher-resolution
_HST_ imaging and thus increase the number of confirmed _Herschel_ selected lensing systems to allow for better statistical studies. Over
the years, we have been awarded _HST_ snapshot time to follow up
on our targets. However, since the time granted was not enough to
observe the full list of _Herschel_ -selected lensing systems candidates,
and because of the filler nature of the snapshot program, which
only guarantees a partial completion rate, we had to prioritise those
candidates with a higher probability of being lensed to maximise
our success rate. This resulted in prioritising the brightest sources at
500 _𝜇_ m (i.e., the higher the flux density, the higher the probability for
the system to be lensed) or those having other multi-wavelength data
and/or redshift information. The success rate of the _HST_ observations

was entirely determined by the _HST_ observing schedule and does
not depend on the candidate properties. In the end, only a fraction
(290 out of 398) of the full sample has been observed, as detailed
in the following section, which is the focus of this paper. Given
that this sub-sample represents a random collection of the entire
candidate population, we limit our focus on presenting the properties
of this sub-sample without drawing any statistical conclusion on the
parent sample, which would otherwise be biased by observational
constraints that were out of our control.


**2.2** _**HST**_ **snapshot observations and data reduction**


Our _HST_ snapshot follow-up observations were carried out in three
different cycles.


 - Proposal ID 12488 (PI M. Negrello) in Cycle 19: 200 targets
were proposed with _𝑆_ 500 ∼ _[>]_ 85 mJy, that were selected from the
preliminary source catalogues of HerMES (63 targets) and H-ATLAS
(137 targets). At the time, the only _Herschel_ data available were for
four of the final five H-ATLAS fields (the three fields on the Celestial
Equator named GAMA09, GAMA12 and GAMA15 and the one
close to the North Galactic Pole named NGP), so the targets were
spread across the Equatorial and Northern sky. The observations
were carried out from October 2011 to August 2013.

 - Proposal ID 15242 (PI L. Marchetti), in Cycle 25: 200 targets
were proposed with _𝑆_ 500 ≥ 100 mJy from the full _Herschel_ coverage,
but in particular from HeLMS and HerS (Nayyeri et al. 2016) and
with _𝑆_ 500 ≥ 80 mJy from the H-ATLAS SGP field near the South
Galactic Pole. The sample also included some of the targets submitted
for observations in the Cycle 19 proposal that had not been observed
or for which the _HST_ data obtained were corrupted due to issues
with the _HST_ tracking system. The observations were carried out
from October 2017 to June 2018.


 - Proposal ID 16015 (PI L. Marchetti) in Cycle 26: this was a
continuation of the Cycle 25 proposal. The observations were carried
out from November 2019 to September 2020.


In summary, a total of 290 candidates were observed as part of these
three snapshot programmes: 173 from H-ATLAS, 60 from HerMES,
42 from HeLMS, and 15 from HerS. Unfortunately, the data of nine
systems are corrupted due to issues with the _HST_ tracking system, so
the final sample with available _HST_ snapshot observations amount to
281 systems. All the _HST_ snapshot proposals share the same observing strategy with short observations of ∼ 4 or ∼ 11 minutes on source
performed with the wide- _YJ_ filter _F110W_ of the Wide Field Camera
3 (WFC3) IR channel (Dressel 2022). The _F110W_ filter has a pivot
wavelength _𝜆_ p = 1153 _._ 4 nm and a passband rectangular width of



_Characterisation of HST confirmed lenses_ 3


443.0 nm, corresponding to a wavelength coverage between 883.2
nm and 1412.1 nm. This observing band was chosen to maximise
the signal-to-noise ratio (SNR) for short exposures and efficiently
cover the stellar emission from the foreground galaxy in the gravitational lensing system, usually an ETG (e.g., Auger et al. 2009).
The IR channel of the WFC3 allows to read out the detector with

different samplings while the exposure accumulates. The sampling
strategy varies depending on the specific scientific case. Our targets
were observed with the `MULTIACCUM` observing mode using either
eight samplings with 10-s sampling intervals linearly spaced between
one another ( `SPARS10` sampling sequence) for a total exposure time
of 251.75 s, or nine samplings with 25-s sampling intervals linearly
spaced between one another ( `SPARS25` sampling sequence) for a total
exposure time of 711.74 s. Due to the filler nature of the snapshot
programmes, the total exposure time was defined according to the
available time slot. Each set of observations is flatfield corrected,
background subtracted, cosmic-ray cleaned, distortion corrected, rotated and drizzled. For drizzling, we use a 4-point sub-pixel dithering
pattern that results in an output pixel size of 0 _._ 064 arcsec, which is
roughly half of the original pixel size. The size of the field of view
(FOV) is 136 arcsec × 123 arcsec. The reduction steps are performed
with the `AstroDrizzle` package (Hoffmann et al. 2021). Additionally, we perform a first-order astrometric correction by matching the
_Gaia_ early Data Release 3 sources (Gaia Collaboration et al. 2021)
with their nearest _HST_ counterparts.


**2.3** **Multiwavelength data**


We use archival ALMA, SMA, and NOEMA high-resolution multiwavelength observations for 77 systems and include them in our
analysis. For the ALMA data, we download the Stokes I continuum
images from the science archive [2] . For the SMA data, we either use
the reduced continuum images from Enia et al. (2018), or we download the UV tables from the science archive [3] and we produce the
continuum images with the Common Astronomy Software Applications [4] ( `CASA` ) software. HerBS-89a is the only source for which we
use NOEMA data. The details of the data reduction are available in

Neri et al. (2020, but see Berta et al. 2021 for a detailed study of this
galaxy). These multiwavelength observations have an angular resolution ranging from 1 to 0 _._ 03 arcsec for ALMA, 0 _._ 5 arcsec for SMA,
and 0 _._ 3 arcsec for NOEMA. More details on the instrumental setup
and references will be given in the source-by-source description in
Sec. 4.3. In addition to these high-resolution observations, we search
both previous literature works and the NASA/IPAC Extragalactic
Database [5] for the lens candidates and/or potential lenses redshifts.
The details on the redshifts and their references are available in the

source-by-source description and Table 3.


**3** **LENS CLASSIFICATION**


We assign each one of the 281 sources in our sample to a class that
describes the likelihood of the source being a strong lensing system:


 - Class A: the source is confirmed to be strongly lensed because
it satisfies one or both of the following criteria: (i) the _HST_ image


2 `[https://almascience.eso.org/aq/?result_view=](https://almascience.eso.org/aq/?result_view=observations)`

`[observations](https://almascience.eso.org/aq/?result_view=observations)` .
3 `[https://lweb.cfa.harvard.edu/cgi-bin/sma/smaarch.pl](https://lweb.cfa.harvard.edu/cgi-bin/sma/smaarch.pl)` .
4 Available at `[https://casa.nrao.edu/](https://casa.nrao.edu/)` .
5 Available at `[https://ned.ipac.caltech.edu/](https://ned.ipac.caltech.edu/)`


MNRAS **000**, 1–57 (2022)

4 _E. Borsato et al._


F110W [ [] [Jy arcsec] 2 ]

0 5 10



F110W [ [] [Jy arcsec] 2 ]

0 25 50 75



F110W [ [] [Jy arcsec] 2 ]

0 5 10



F110W [ [] [Jy arcsec] 2 ]

0 25 50 75



























**Figure 1.** _From left to right panels:_ Examples of sample systems assigned to classes A, B, C, and D, respectively. In each column, the bottom panel shows a
20 arcsec × 20 arcsec cutout of the _HST_ image, while the top panel shows a 12 arcsec × 12 arcsec zoom-in on the central source. The cross marks the position
of the _Herschel_ detection used to identify our targets, while the circle roughly corresponds to the ∼ 20 arcsec full width at half maximum (FWHM) of the
_Herschel_ /SPIRE beam at 250 _𝜇_ m. The images are oriented with N up and E to the left.



shows a near-IR object located close to the position of the _Herschel_
detection, while lensing features (such as arcs and/or multiple images) are visible either before or only after the subtraction of the
near-IR source (supposedly acting as a lens), (ii) lensing features are
clearly detected in high spatial resolution sub-mm/mm ancillary data
described in Sec. 2.3;

 - Class B: a single galaxy or a group of galaxies is visible close
to the position of the _Herschel_ detection, but there is no detection of
lensing features even after the subtraction of the foreground galaxy.
Therefore, this class tags objects that are likely to be a lens, but
the background source is probably too faint to be detected in the
relatively shallow _HST_ data;

 - Class C : no source is detected in the _HST_ image approximately
within the ∼ 20 arcsec SPIRE FWHM at 250 _𝜇𝑚_ of the position
of the _Herschel_ detection. These cases are likely to be either high- _𝑧_
unlensed DSFGs or lensing events where the lens is either at high
redshift or has an intrinsically low luminosity, or both;

 - Class D: the source is a contaminant, e.g., a dusty star, an
unlensed QSO, or a low redshift, sub-mm bright, spiral galaxy (previously misinterpreted as a lens candidate).


The adopted classes are similar to those introduced by Negrello et al.
(2017). The main difference is our use of the information provided
by the _HST_ images after the modelling and subtracting the detected
near-IR source. This mainly affects the definition of class A [criterion
(i)] and class B.
In order to allocate the 281 objects to the four classes, we proceed
by first carrying out a visual inspection of the _HST_ data alone, without performing any galaxy subtraction and without relying on any
multiwavelength ancillary data. Based on this simple visual analysis,
we are able to assign 25 objects to class A, 105 to class B, 146 to


MNRAS **000**, 1–57 (2022)



class C, and 5 to class D. Four examples extracted from the A, B, C
and D classes are shown in Fig 1.
As a second step in the classification, we exploit the available
high spatial resolution sub-mm/mm data to look for evidence of
multiple images and arcs. In this way, we are able to identify 31
more lensed objects (promoting them to A class) that have been
previously classified as B or C and 26 individual unlensed DSFGs
or overdensities of unlensed DSFGs. In summary, after the use of
ancillary data, the number of objects assigned to class A increases
from 25 to 56 and the number of systems in class B and C decreases
to 76 and 120, respectively. In contrast, that of objects in class D
increases from 5 to 29.

Finally, as described in detail in Sec. 4, in the _HST_ images, we
perform, if possible, the modelling of the surface brightness of the
foreground galaxies and subtract it from the _HST_ image to reveal
any lensing feature. In this way, we are able to identify 9 new lensed
galaxies that have been previously assigned to class B.
In conclusion, after the visual inspection of the _HST_ images, use
of ancillary data, and surface brightness modelling, we are able to
assign 65 objects to class A, 67 to class B, 120 to class C, and 29
to class D. The systems classified as A are listed in Table 1, those
classified as D are listed in Table 2, while the rest of the sample is
listed in Table B1.

**Table 1.** Properties of the 65 systems classified as A by visual inspection, through multiwavelength follow-up observations, or after the lens subtraction.


No. IAU name Alt. Name Ref. RA Dec Vis. Class Multiw. Obs. Prev. Classification Ref. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14)


S_1 HATLASJ000330.6 − 321136 HERBS155 Ba18 00:03:31 − 32:11:36.00 A – – – 59 _._ 9 ± 5 _._ 8 94 _._ 2 ± 5 _._ 8 85 _._ 6 ± 7 _._ 2 Ba18
S_2 HATLASJ000912.7 − 300807 SD.v1.70 Zh18 00:09:13 − 30:08:07.00 A – – – 352 _._ 8 ± 5 _._ 4 272 _._ 6 ± 6 _._ 1 156 _._ 1 ± 6 _._ 8 Ne17
S_3 HELMSJ001353.5 − 060200 HELMS31 Na16 00:13:54 − 06:02:00.00 A – – – 178 _._ 0 ± 7 _._ 0 176 _._ 0 ± 6 _._ 0 120 _._ 0 ± 7 _._ 0 Na16
S_4 HELMSJ003619.8 + 002420 HELMS14 Na16 00:36:20 + 00:24:20.00 A – – – 251 _._ 0 ± 6 _._ 0 247 _._ 0 ± 6 _._ 0 148 _._ 0 ± 7 _._ 0 Na16
S_5 HELMSJ005841.2 − 011149 HELMS23 Na16 00:58:41 − 01:11:49.00 A – – – 391 _._ 0 ± 7 _._ 0 273 _._ 0 ± 6 _._ 0 126 _._ 0 ± 8 _._ 0 Na16
S_6 HERSJ011722.3 + 005624 HERS10 Na16 01:17:22 + 00:56:24.00 A – – – 105 _._ 0 ± 6 _._ 0 125 _._ 0 ± 6 _._ 0 117 _._ 0 ± 7 _._ 0 Na16
S_7 HERSJ012620.5 + 012950 HERS5 Na16 01:26:21 + 01:29:50.00 A – – – 268 _._ 0 ± 8 _._ 0 228 _._ 0 ± 7 _._ 0 133 _._ 0 ± 9 _._ 0 Na16
S_8 HERSJ020941.2 + 001558 9io9 Ge15 02:09:41 + 00:15:58.00 A A Lensed Ge15 826 _._ 0 ± 7 _._ 0 912 _._ 0 ± 7 _._ 0 718 _._ 0 ± 8 _._ 0 Na16

HERS1 Na16 Hr16

PJ020941.3 Hr16 Li22

ACT-S J0210 + 0016 Su17

S_9 HERMESJ032637 − 270044 HECDFS05 Wa13 03:26:36 − 27:00:44.00 A – Lensed Ca14 155 _._ 0 131 _._ 0 84 _._ 0 Ca14
S_10 HERMESJ033732 − 295353 HECDFS02 Wa13 03:37:32 − 29:53:53.00 A – Lensed Wa13 133 _._ 0 147 _._ 0 122 _._ 0 Ca14

Ca14

S_11 HATLASJ083051 + 013225 G09v1.97 Bu13 08:30:51 + 01:32:24.87 A A Lensed Bu13 248 _._ 5 ± 7 _._ 5 305 _._ 3 ± 8 _._ 1 269 _._ 1 ± 8 _._ 7 Ne17

HERBS4 Ba18 Ca14

Ne17

Am18

En18

Ya19

Ma22

S_12 HERMESJ100144 + 025709 HCOSMOS01 Ca14 10:01:44 + 02:57:08.62 A A Lensed Ca14 86 _._ 0 ± 6 _._ 0 96 _._ 0 ± 6 _._ 0 71 _._ 0 ± 6 _._ 0 Bu15

Bu15

S_13 HERMESJ103827 + 581544 HLock04 Wa13 10:38:27 + 58:15:43.60 A A Lensed Bu13 190 _._ 0 156 _._ 0 101 _._ 0 Ca14

Wa13

Ca14

S_14 HERMESJ110016 + 571736 HLock12 Ca14 11:00:16 + 57:17:35.92 A – Lensed Ca14 224 _._ 0 159 _._ 0 79 _._ 0 Ca14

Am18

S_15 HATLASJ114638 − 001132 G12v2.30 Bu13 11:46:38 − 00:11:32.00 A A Lensed Bu13 316 _._ 0 ± 6 _._ 6 357 _._ 9 ± 7 _._ 4 291 _._ 8 ± 7 _._ 7 Ne17

HERBS2 Om13

Ca14

Ne17

Am18

S_16 HATLASJ125126 + 254928 HERBS52 Ba18 12:51:26 + 25:49:28.31 A A – – 57 _._ 4 ± 7 _._ 4 96 _._ 8 ± 8 _._ 2 109 _._ 4 ± 8 _._ 8 Ne17
S_17 HATLASJ125760 + 224558 – – 12:58:00 + 22:45:57.82 A – – – 272 _._ 4 ± 7 _._ 3 215 _._ 0 ± 8 _._ 1 137 _._ 8 ± 8 _._ 7 Ne17
S_18 HATLASJ133008 + 245900 NBv1.78 Bu13 13:30:08 + 24:58:59.70 A A Lensed Hs12 271 _._ 2 ± 7 _._ 2 278 _._ 2 ± 8 _._ 1 203 _._ 5 ± 8 _._ 5 Ne17

HERBS12 Ba18 Bu13

Ca14

Ne17

En18

S_19 HATLASJ133846 + 255057 HERBS29 Ba18 13:38:46 + 25:50:56.84 A A Lensed Ne17 159 _._ 0 ± 7 _._ 4 183 _._ 1 ± 8 _._ 2 137 _._ 6 ± 9 _._ 0 Ne17

Am18

S_20 HATLASJ142935 − 002837 G15v2.19 Ca14 14:29:35 − 00:28:37.00 A A Lensed Ca14 801 _._ 8 ± 6 _._ 6 438 _._ 5 ± 7 _._ 5 199 _._ 8 ± 7 _._ 7 Ne17

H1429 − 0028 Me14 Me14

Ne17

Am18

Dy18
S_21 HERMESJ171451 + 592634 HFLS02 Wa13 17:14:51 + 59:26:34.12 A – Lensed Ca14 164 _._ 0 148 _._ 0 87 _._ 0 Ca14
S_22 HERMESJ171545 + 601238 HFLS08 Ca14 17:15:45 + 60:12:38.34 A – Lensed Ca14 86 _._ 0 93 _._ 0 67 _._ 0 Ca14
S_23 HATLASJ225844.7 − 295124 HERBS26 Ba18 22:58:45 − 29:51:25.00 A – – – 175 _._ 4 ± 5 _._ 2 187 _._ 0 ± 5 _._ 9 142 _._ 6 ± 7 _._ 5 Ne17
S_24 HELMSJ232210.3 − 033559 HELMS19 Na16 23:22:10 − 03:35:59.00 A – – – 114 _._ 0 ± 6 _._ 0 160 _._ 0 ± 7 _._ 0 134 _._ 0 ± 8 _._ 0 Na16
S_25 HATLASJ233037.2 − 331217 HERBS123 Ba18 23:30:37 − 33:12:18.00 A – – – 106 _._ 2 ± 5 _._ 9 107 _._ 9 ± 6 _._ 0 90 _._ 0 ± 7 _._ 5 Ba18


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the _Herschel_ detection. Cols. (3) and (4): Alternative name and reference. Cols. (5) and (6): ICRS RA and Dec coordinate (J2000.0) of the _Herschel_ detection. Col. (7): Classification after the visual inspection [criterium
(i)]. Col. (8): Lens classification including the multiwavelength observations. Cols. (9) and (10): Confirmed lensed system and reference. Col. (11), (12), (13), and (14): SPIRE flux density at 250 _𝜇_ m, 350 _𝜇_ m, 500 _𝜇_ m and reference. Following are the abbreviations used for the
references: Al17: Albareti et al. (2017); Am18: Amvrosiadis et al. (2018); Ba18: Bakx et al. (2018); Be21: Berta et al. (2021); Bo06: Borys et al. (2006); Bu13: Bussmann et al. (2013); Bu15: Bussmann et al. (2015); Bu21: Butler et al. (2021); Ca14: Calanog et al. (2014); Co11: Cox
et al. (2011); Dy18: Dye et al. (2018); Dy22: Dye et al. (2022); En18: Enia et al. (2018); Fa17: Falgarone et al. (2017); Ga11: Gavazzi et al. (2011); Ge15: Geach et al. (2015); Gi23: Giulietti et al. (2023); Hs12: Harris et al. (2012); Hr16: Harrington et al. (2016); Ik11: Ikarashi et al.
(2011); Ma19: Ma et al. (2019); Ma22: Maresca et al. (2022); Me14: Messias et al. (2014); Na16: Nayyeri et al. (2016); Na17: Nayyeri et al. (2017); Ne17: Negrello et al. (2017); Om13: Omont et al. (2013); Su17: Su et al. (2017); Sh21: Shirley et al. (2021); Ur22: Urquhart et al.
(2022); Va16: Valiante et al. (2016); Wa13: Wardlow et al. (2013); Ya17: Yang et al. (2017); Ya19: Yang et al. (2019).

**Table 1** – _continued_


No. IAU name Alt. name Ref. RA Dec Vis. class Multiw. class Prev. classification Ref. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14)


_Confirmed after the lens subtraction_


S_26 HELMSJ001626.0 + 042613 HELMS22 Na16 00:16:26 + 04:26:13.00 B A Lensed Am18 130 _._ 0 ± 15 _._ 0 180 _._ 0 ± 18 _._ 0 130 _._ 0 ± 15 _._ 0 Zh18
Dy18
S_27 HATLASJ002624.8 − 341737 HERBS22 Ba18 00:26:25 − 34:17:38.00 B – – – 137 _._ 7 ± 5 _._ 2 185 _._ 9 ± 5 _._ 8 148 _._ 8 ± 6 _._ 8 Ne17
S_28 HELMSJ004723.6 + 015751 HELMS9 Na16 00:47:24 + 01:57:51.00 C A Lensed Am18 398 _._ 0 ± 6 _._ 0 320 _._ 0 ± 6 _._ 0 164 _._ 0 ± 8 _._ 0 Na16
Dy18
S_29 HERSJ012041.6 − 002705 HERS2 Na16 01:20:42 − 00:27:05.00 B – – – 240 ± 6 260 ± 6 189 ± 7 Na16
S_30 HATLASJ085112 + 004934 – – 08:51:12 + 00:49:33.83 B – – – 125 _._ 1 ± 7 _._ 3 118 _._ 3 ± 8 _._ 3 77 _._ 7 ± 8 _._ 8 Va16
S_31 HATLASJ085359 + 015537 G09v1.40 Bu13 08:53:59 + 01:55:37.21 B A Lensed Bu13 396 _._ 4 ± 7 _._ 6 367 _._ 9 ± 8 _._ 2 228 _._ 2 ± 8 _._ 9 Ne17

Ca14

Am18

En18

Bu21

S_32 HERMESJ104549 + 574512 HLock06 Wa13 10:45:49 + 57:45:11.52 B – Lensed Ca14 136 _._ 0 127 _._ 0 96 _._ 0 Ca14
S_33 HERMESJ105551 + 592845 HLock08 Wa13 10:55:51 + 59:28:45.44 B – – – 142 _._ 0 119 _._ 0 84 _._ 0 Ca14
S_34 HERMESJ105751 + 573026 HLSW − 01 Ga11 10:57:51 + 57:30:26.42 B A Lensed Ga11 402 _._ 0 377 _._ 0 249 _._ 0 Ca14

HLock01 Wa13 Wa13

Bu13

Ca14

Am18

S_35 HATLASJ132630 + 334410 NAv1.195 Bu13 13:26:30 + 33:44:09.90 C A Lensed Bu13 190 _._ 6 ± 7 _._ 3 281 _._ 4 ± 8 _._ 2 278 _._ 5 ± 9 _._ 0 Ne17

Am18

En18

S_36 HATLASJ133543 + 300404 NA.v1.489 Na17 13:35:43 + 30:04:03.66 B A Lensed Na17 136 _._ 6 ± 7 _._ 2 145 _._ 7 ± 8 _._ 0 125 _._ 0 ± 8 _._ 5 Ne17

HERBS35 Ba18

S_37 HATLASJ142140 + 000448 HerBS140 Ba18 14:21:40 + 00:04:48.00 B – – – 96 _._ 8 ± 7 _._ 2 98 _._ 5 ± 8 _._ 2 87 _._ 4 ± 8 _._ 7 Ba18
S_38 HERMESJ142824 + 352620 HBootes03 Wa13 14:28:24 + 35:26:19.54 B A Lensed Bo06 323 _._ 0 243 _._ 0 139 _._ 0 Ca14

Bu13

S_39 HATLASJ223753.8 − 305828 HERBS68 Ba18 22:37:54 − 30:58:28.00 B – – – 139 _._ 1 ± 4 _._ 9 144 _._ 9 ± 5 _._ 1 100 _._ 6 ± 6 _._ 2 Ne17
S_40 HATLASJ225250.7 − 313657 HERBS47 Ba18 22:52:51 − 31:36:58.00 B – – – 127 _._ 4 ± 4 _._ 2 138 _._ 7 ± 4 _._ 9 111 _._ 4 ± 5 _._ 9 Ne17
S_41 HELMSJ233441.0 − 065220 HELMS1 Na16 23:34:41 − 06:52:20.00 B A – – 431 _._ 0 ± 6 _._ 0 381 _._ 0 ± 7 _._ 0 272 _._ 0 ± 7 _._ 0 Na16
S_42 HELMSJ233633.5 − 032119 HELMS41 Na16 23:36:34 − 03:21:19.00 B – – – 130 _._ 0 ± 6 _._ 0 131 _._ 0 ± 6 _._ 0 110 _._ 0 ± 7 _._ 0 Na16


_Confirmed through sub-mm/mm follow-up_


S_43 HELMSJ001615.7 + 032435 HELMS13 Na16 00:16:16 + 03:24:35.00 B A Lensed Am18 176 _._ 0 ± 13 _._ 0 210 _._ 0 ± 15 _._ 0 134 _._ 0 ± 11 _._ 0 Zh18
Dy18
S_44 HELMSJ002220.9 − 015524 HELMS29 Na16 00:22:21 − 01:55:24.00 B A – – 66 _._ 0 ± 6 _._ 0 102 _._ 0 ± 6 _._ 0 121 _._ 0 ± 7 _._ 0 Na16
S_45 HELMSJ003814.1 − 002252 HELMS24 Na16 00:38:14 − 00:22:52.00 C A – – 73 _._ 35 ± 5 _._ 55 119 _._ 01 ± 6 _._ 01 122 _._ 87 ± 6 _._ 69 Su17

ACT-S J0038 − 0022 Su17

S_46 HELMSJ003929.6 + 002426 HELMS11 Na16 00:39:30 + 00:24:26.00 C A – – 140 _._ 0 ± 7 _._ 0 157 _._ 0 ± 7 _._ 0 154 _._ 0 ± 8 _._ 0 Na16
S_47 HELMSJ004714.2 + 032454 HELMS8 Na16 00:47:14 + 03:24:54.00 C A Lensed Am18 312 _._ 0 ± 6 _._ 0 244 _._ 0 ± 7 _._ 0 168 _._ 0 ± 8 _._ 0 Na16
Dy18
S_48 HELMSJ005159.4 + 062240 HELMS18 Na16 00:52:00 + 06:22:41.00 B A Lensed Am18 163 _._ 0 ± 13 _._ 0 202 _._ 0 ± 15 _._ 0 142 _._ 0 ± 12 _._ 0 Zh18

En18

Ma22

S_49 HATLASJ005724.2 − 273122 HERBS60 Ba18 00:57:24 − 27:31:22.00 B A – – 73 _._ 3 ± 5 _._ 8 101 _._ 2 ± 6 _._ 1 103 _._ 6 ± 7 _._ 5 Ba18
S_50 HERMESJ021831 − 053131 SXDF1100.001 (Orochi) Ik11 02:18:31 − 05:31:31.00 B A Lensed Bu13 78 _._ 0 ± 7 _._ 0 122 _._ 0 ± 8 _._ 0 99 _._ 0 ± 7 _._ 0 Bu15
HXMM02 Wa13 Bu15

S_51 HERMESJ033211 − 270536 HECDFS04 Wa13 03:32:11 − 27:05:36.00 C A Lensed Bu15 56 _._ 0 ± 6 _._ 0 61 _._ 0 ± 6 _._ 0 55 _._ 0 ± 6 _._ 0 Bu15
S_52 HERMESJ044154 − 540352 HADFS01 Wa13 04:41:54 − 54:03:52.00 B A Lensed Bu15 76 _._ 0 ± 6 _._ 0 100 _._ 0 ± 6 _._ 0 94 _._ 0 ± 6 _._ 0 Bu15
S_53 HATLASJ083932 − 011760 HERBS105 Ba18 08:39:32 − 01:18:00.00 C A – – 73 _._ 8 ± 7 _._ 4 88 _._ 5 ± 8 _._ 1 93 _._ 2 ± 8 _._ 7 Ba18
S_54 HATLASJ091841 + 023048 G09v1.326 Ca14 09:18:41 + 02:30:47.97 B A – – 125 _._ 7 ± 7 _._ 2 150 _._ 7 ± 8 _._ 2 128 _._ 4 ± 8 _._ 7 Ne17

HERBS32 Ba18

S_55 HATLASJ113526 − 014606 G12v2.43 Bu13 11:35:26 − 01:46:06.00 C A Lensed Gi23 278 _._ 8 ± 7 _._ 4 282 _._ 9 ± 8 _._ 2 204 _._ 0 ± 8 _._ 6 Ne17

HERBS10 Ba18

**Table 1** – _continued_


No. IAU name Alt. name Ref. RA Dec Vis. class Multiw. obs. Prev. classification Ref. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14)


S_56 HATLASJ115433.6 + 005042 HERBS177 Ba18 11:54:34 + 00:50:42.30 B A – – 53 _._ 9 ± 7 _._ 4 85 _._ 8 ± 8 _._ 1 83 _._ 9 ± 8 _._ 6 Ba18
S_57 HATLASJ120127.6 − 014043 HERBS61 Ba18 12:01:28 − 01:40:44.00 B A Lensed En18 67 _._ 4 ± 6 _._ 5 112 _._ 1 ± 7 _._ 4 103 _._ 9 ± 7 _._ 7 Ne17
S_58 HATLASJ131611 + 281220 HERBS89 Ba18 13:16:11 + 28:12:20.39 C A Lensed Be21 71 _._ 8 ± 5 _._ 7 103 _._ 4 ± 5 _._ 7 95 _._ 7 ± 7 _._ 0 Ba18
S_59 HATLASJ134429 + 303036 NAv1.56 Bu13 13:44:29 + 30:30:35.77 B A Lensed Bu13 462 _._ 0 ± 7 _._ 4 465 _._ 7 ± 8 _._ 6 343 _._ 3 ± 8 _._ 7 Ne17

HERBS1 Ba18 Fa17

Am18

En18

S_60 HATLASJ141352 − 000027 G15v2.235 Bu13 14:13:52 − 00:00:27.00 B A Lensed Bu13 188 _._ 6 ± 7 _._ 4 217 _._ 0 ± 8 _._ 1 176 _._ 4 ± 8 _._ 7 Ne17

HERBS15 Ba18 Am18

S_61 HATLASJ142414 + 022304 ID 141 Co11 14:24:14 + 02:23:03.62 B A Lensed Co11 112 _._ 2 ± 7 _._ 3 182 _._ 2 ± 8 _._ 2 193 _._ 3 ± 8 _._ 5 Ne17

G15v2.779 Bu13 Bu12

HERBS13 Ba18 Dy18
En18

Dy22
S_62 HERMESJ142826 + 345547 HBootes02 Wa13 14:28:26 + 34:55:47.03 B A Lensed Wa13 159 _._ 0 195 _._ 0 156 _._ 0 Ca14

Bu13

Ca14

S_63 HATLASJ230815.5 − 343801 HERBS28 Ba18 23:08:16 − 34:38:01.00 B A – – 79 _._ 4 ± 5 _._ 4 135 _._ 4 ± 5 _._ 7 140 _._ 0 ± 7 _._ 0 Ne17
S_64 HELMSJ232439.5 − 043936 HELMS7 Na16 23:24:40 − 04:39:36.00 B A Lensed Am18 214 _._ 0 ± 7 _._ 0 218 _._ 0 ± 7 _._ 0 172 _._ 0 ± 9 _._ 0 Na16

Ma22

S_65 HELMSJ233620.8 − 060828 HELMS6 Na16 23:36:21 − 06:08:28.00 B A – – 193 _._ 0 ± 7 _._ 0 252 _._ 0 ± 6 _._ 0 202 _._ 0 ± 8 _._ 0 Na16

8 _E. Borsato et al._


**4** **SURFACE BRIGHTNESS MODELLING**


We group all the systems, for which we are able to identify the
foreground lensing galaxies or a suitable candidate according to the
following configurations:


 - systems in which a clearly isolated galaxy is acting as a lens. In
this case, we model this single object (type 1);

 - systems in which two or three galaxies are probably acting as
lenses (e.g., they are very close to each other or even blended, and
the lensing features are consistent with multiple lenses). In this case,
we model all the galaxies at the same time (type 2);

 - systems in which more than one galaxy is clearly visible in
the foreground, but either they are sufficiently small or distant with
respect to each other that they can be separately modelled (type 3);

 - one system which shows no trace of a lens, likely due to a combi
−
nation of high redshift and obscuration (HATLASJ113526 014606;
see Giulietti et al. 2023 for details). This system will not be included
in the lens surface-brightness modelling.


For the systems confirmed as lensed by multiwavelength data
alone, we use the location of the background sources sub-mm emission to identify the foreground lensing galaxies in the _HST_ observations.

It is worth noticing that for type 2 and type 3 systems, we can not
be sure whether all the galaxies are contributing to the lensing. In
most cases, we do not know the redshift of all the galaxies, so we can
not rule out the possibility that they are unrelated field objects.
We still provide the models of all the galaxies of interest to enable
future studies once all the redshifts are known. In order to best

characterise the galaxies acting as lenses and provide the best-fitting
model of their surface brightness, we use either a parametric or a
non-parametric approach depending on the lens morphology and
configuration of the lensing system.
For the parametric modelling, we adopt the Galaxy Surface
Photometry 2-Dimensional Decomposition algorithm ( `GASP2D` ;
Méndez-Abreu et al. 2008, 2017) to model the type 1 and type 3
lensing systems and the Galaxy Fitting algorithm ( `GALFIT` ; Peng
et al. 2002, 2010) for the type 2 foreground lensing systems. `GASP2D`
has the advantage of automatically setting the initial guess values
needed to fit the galaxy image, whereas `GALFIT` allows us to perform the simultaneous fit of multiple systems. We adopt the nonparametric Isophote Fitting algorithm ( `ISOFIT` ; Ciambur 2015) to
model highly-inclined disk lenses for which `GASP2D` and `GALFIT` fail.
In the following sections, we describe the approaches adopted for the
different cases. We point out in the source-by-source descriptions the
cases for which we made exceptions to the above prescriptions.


**4.1** **Parametric approaches**


Both `GASP2D` and `GALFIT` adopt a set of analytical functions to model
the light distribution of the galaxy components. They derive the bestfitting values of the structural parameters by comparing the model of
the surface brightness distribution with the observed photon counts
of the galaxy in each image pixel with an iterative procedure of
non-linear least-squares minimization. The model surface brightness
is convolved with the point spread function (PSF) measured on the
galaxy image to deal with the smearing effects due to the telescope
optics and instrumental setup. Each image pixel is weighted according to the inverse of the variance of its total photon counts due to the
contribution of both the galaxy and sky, the detector photon-noise
limitation and readout noise are also taken into account. `GASP2D` and


MNRAS **000**, 1–57 (2022)



`GALFIT` are written in `IDL` [6] and `C` [7], respectively. They provide the
best-fitting values of the structural parameters of the galaxy components and their formal errors, as well as the model and residual image
of the galaxy to be compared to the observed one.


_4.1.1_ _Residual sky subtraction_


The sky level provided by the image reduction consists of a global
estimate across the FOV after automatically masking the luminous
sources. This subtraction proves to be unreliable in the analysis of
the faintest lensing features since a residual sky level could still be
present in the image. Therefore, we measure and subtract the residual
sky level as follows.
We start by masking the system as well as the foreground stars,
companion and background galaxies, and lensing features using the
`make_sources_mask` task of the `photutils.background python`
package [8] (Bradley et al. 2021). The source segmentation algorithm
identifies all the above sources and creates their footprints by selecting the _𝑁_ pixel connected pixels with photon counts over a given
threshold _𝜎_ . Then, the algorithm enlarges the available footprints
with binary dilation (e.g. Nadadur & Haralick 2000) through an
_𝑚_ pixel × _𝑚_ pixel matrix to build the pixel mask of all the luminous
sources in the image. We repeat this process twice to identify both
the compact ( _𝑁_ pixel = 5, _𝑚_ = 11, _𝜎_ = 2) and extended ( _𝑁_ pixel = 10,
_𝑚_ = 51, _𝜎_ = 2) sources. In both cases, we reiterate the source identification and footprint dilation of the masked image until no more
pixels are added to the mask. The values of _𝑁_ pixel, _𝑚_, and _𝜎_ are
chosen such that the resulting masks cover most of the sources and,
at the same time, leave some background-dominated regions in the
image. The final pixel mask is the combination of the footprints built
for compact and extended sources, which we visually check and manually edit to remove the spurious sources, such as residual cosmic
rays and bad pixels.
We calculate the residual sky level as the biweight location of
the unmasked pixels. This is an estimator for the central location of
a distribution that is very robust against outliers (e.g. Beers et al.
1990). Then, we subtract it from the image. We derive the standard
deviation rms bkg of the sky-subtracted image through the median absolute deviation of the unmasked pixels using _𝜎_ = _𝑀𝐴𝐷_ /Φ [−][1] (3/4),
where _𝑀𝐴𝐷_ is the median absolute deviation, 1/Φ [−][1] (3/4) ≈ 1 _._ 4826
is the normal inverse cumulative distribution function evaluated at

a probability of 3/4. The biweight location and _𝑀𝐴𝐷_ are available through `astropy.stats` package (Astropy Collaboration et al.
2018). The image of HERSJ012620.5+012950 (HERS5, S_7; Nayyeri et al. 2016) with the pixel mask adopted to estimate the residual
sky level is shown in Fig. 2 (left panel) as an example.


_4.1.2_ _Pixel mask and noise map_


We trim the sky-subtracted images to reduce the computing time
to perform a reliable photometric decomposition. Each galaxy is
centred in an FOV ranging from 200 pixel× 200 pixel (corresponding
to 12 _._ 8 arcsec × 12 _._ 8 arcsec) to 400 pixel × 400 pixel (25 _._ 6 arcsec ×
25 _._ 6 arcsec) to fully cover all the lensing features. We also trim
the pixel mask to the same region. Then, we unmask the pixels


6 `[https://www.l3harrisgeospatial.com/Software-Technology/](https://www.l3harrisgeospatial.com/Software-Technology/IDL)`

```
IDL
```

7 `[https://users.obs.carnegiescience.edu/peng/work/galfit/](https://users.obs.carnegiescience.edu/peng/work/galfit/galfit.html)`
```
galfit.html
```

8 `[https://photutils.readthedocs.io/en/stable/index.html](https://photutils.readthedocs.io/en/stable/index.html)`

_Characterisation of HST confirmed lenses_ 9


**Table 2.** Properties of the 26 systems confirmed to be unlensed by multiwavelength follow-up.


No. Name Alt. Name Ref. RA Dec Multiw. Ref. Nature Ref. _HST_ Counterpart z Ref.

[h m s] [d m s]

(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13)


S_72 HERMESJ003824 − 433705 HELAISS02 Ca14 00:38:24 − 43:37:05.00 ALMA band 7 Bu13 multiple – yes – –
S_86 HERMESJ022022 − 015329 HXMM04 Wa13 02:20:22 − 01:53:29.00 ALMA band 7 Bu15 single Bu15 yes ( 0 _._ 21 ± 0 _._ 14 ) Wa13
S_87 HERMESJ022029 − 064846 HXMM09 Wa13 02:20:29 − 06:48:46.00 ALMA band 7 Bu15 multiple/merger Bu15 no ( 0 _._ 21 ± 0 _._ 09 ) Wa13
S_89 HERMESJ022548 − 041750 HXMM05 Wa13 02:25:48 − 04:17:50.00 ALMA band 7, 8 Le19 single DSFG Le19 no 2.985 Wa13

SMA at 340 GHz Bu13

S_90 HERMESJ045027 − 524126 HADFS08 Ca14 04:50:27 − 52:41:26.00 ALMA band 7 Bu15 merger – yes – –
S_92 HATLASJ084933 + 021443 HerBS8 Ca14 08:49:33 + 02:14:43.14 ALMA band 3 2018.1.01146.S protocluster Iv13 yes 2.41 Bu13

ALMA band 4, 6, 7 Iv13

SMA at 340 GHz Iv13

S_119 HATLASJ222503.7 − 304847 HerBS166 Ba18 22:25:04 − 30:48:48.00 ALMA band 7 Ma19 multiple – yes (4.52 ± 0.62) Ba18
S_140 HATLASJ000455.3 − 330811 HerBS170 Ba18 00:04:55 − 33:08:12.00 ALMA band 6 2018.1.00526.S multiple – no (4.24 ± 0.58) Ba18
S_151 HELMSJ005258.6 + 061319 HELMS10 Na16 00:52:59 + 06:13:19.00 ALMA band 7 2013.1.00749.S multiple – yes ( 3 _._ 2 ± 0 _._ 2 ) Le18
S_156 HATLASJ012335.1 − 314618 HerBS145 Ba18 01:23:35 − 31:46:19.00 ALMA band 6 2018.1.00526.S single/QSO – yes 2.73 Ur22
S_164 HERMESJ021943 − 052433 HXMM20 Ca14 02:19:43 − 05:24:33.00 ALMA band 7 GG19 protocluster GG19 yes 2.602 GG19
S_165 HERMESJ022206 − 070727 HXMM23 Ca14 02:22:06 − 07:07:27.00 ALMA band 7 Bu15 single Bu15 yes – –
S_167 HERMESJ022251 − 032414 HXMM22 Ca14 02:22:51 − 03:24:14.00 ALMA band 7 Bu15 single Bu15 no – –
S_176 HERMESJ043830 − 541832 HADFS02 Ca14 04:38:30 − 54:18:32.00 ALMA band 7 Bu15 multiple/merger Bu15 yes ( 3 _._ 40 ± 0 _._ 70 ) Ag18
S_177 HERMESJ044947 − 525427 HADFS09 Ca14 04:49:47 − 52:54:27.00 ALMA band 7 Bu15 multiple Bu15 yes – –
S_178 HATLASJ083153 + 014014 – – 08:31:53 + 01:40:14.43 ALMA band 3 Pe20 quasar DS21 yes 3.9136 DS21

ALMA band 5 2019.2.00027.S

ALMA band 8 DS21

S_188 HATLASJ091454 − 010357 HerBS142 Ba18 09:14:54 − 01:03:57.00 ALMA band 6 2018.1.00526.S multiple/merger Bu15 yes ( 3 _._ 22 ± 0 _._ 44 ) Ba18
S_193 HERMESJ100057 + 022014 HCOSMOS02 Ca14 10:00:57 + 02:20:13.70 ALMA band 3 Wa18, Ch21 protocluster GG19 yes 2.497 Ca14

ALMA band 4 2019.1.00151.S

ALMA band 6 2013.1.00118.S

ALMA band 6 Ch21

ALMA band 7 2016.1.00463.S

ALMA band 7 2016.1.00478.S

S_201 HATLASJ115521 − 021332 HERBS179 Ba18 11:55:21 − 02:13:32.00 ALMA band 6 2018.1.00526.S single – yes ( 4 _._ 07± 0.56) Ba18
S_207 HATLASJ121812.8 + 011841 HerBS83 Ba18 12:18:13 + 01:18:41.67 ALMA band 6 2018.1.00526.S multiple – no - Co23
S_211 HATLASJ122407.4 − 003247 HerBS161 Ba18 12:24:07 − 00:32:47.00 ALMA band 6 2018.1.00526.S multiple – yes ( 3 _._ 82 ± 0 _._ 52 ) Ba18
S_212 HATLASJ122459.1 − 005647 HerBS150 Ba18 12:24:59 − 00:56:47.00 ALMA band 6 2018.1.00526.S multiple – yes (4.57 ± 0.63) Ba18
S_240 HATLASJ141118 − 010655 HerBS201 Ba18 14:11:18 − 01:06:55.00 ALMA band 6 2018.1.00526.S multiple – no ( 4 _._ 00 ± 0 _._ 55 ) Ba18
S_271 HATLASJ232200.0 − 355622 HerBS118 Ba18 23:22:00 − 35:56:22.00 ALMA band 6 2018.1.00526.S single – yes ( 3 _._ 80 ± 0 _._ 52 ) Ba18
S_278 HATLASJ083345 + 000109 HerBS88 Ba18 08:33:45 + 00:01:09.41 ALMA band 7 2013.1.00358.S single/QSO – yes 2.530596 Al17
S_279 HATLASJ090613.8 − 010042 HerBS165 Ba18 09:06:14 − 01:00:43.00 ALMA band 6 2018.1.00526.S single/QSO – yes - Co23


_Notes_ : Col. (1): Source reference number. The candidates are ordered first by their lens classification and then by their RA. Col. (2): IAU name of the _Herschel_ detection. Cols. (3) and (4): Alternative name and
reference. Cols. (5) and (6): ICRS RA and Dec coordinate (J2000.0) of the _Herschel_ detection. Cols. (7) and (8): Multiwavelength observations and reference. Cols. (9) and (10): Possible nature of the system and
reference. Col. (11): Presence of near-IR counterparts. Cols. (12) and (13): Redshift of the source and reference. Following are the abbreviations used for the references that are not already included in Tables 1 and
3: Ag18: Aguirre et al. (2018); Ch21: Champagne et al. (2021); DS21: Díaz-Santos et al. (2021); GG19: Gómez-Guĳarro et al. (2019); Iv13: Ivison et al. (2013); Le18: Lewis et al. (2018); Le19: Leung et al.
(2019); Pe20: Penney et al. (2020); Wa18: Wang et al. (2018).



corresponding to the source in the central circular region of ∼ 100pixel (6 _._ 4 arcsec) radius. This allows us to set up the final pixel
mask, which we use for the parametric fitting of the source surface
brightness. The trimmed image and final pixel mask that we use
to model the surface brightness distribution of S_7 are shown in
Fig. 2 (right panel). In addition, we build the noise map of the
images by calculating the variance (in units of electrons) of each pixel
as _𝜎_ [2] = (RON [2] + _𝜎_ sky [2] [+] _[ 𝜎]_ gal [2] [)/][GAIN] [2] [,] [where] _[𝜎]_ sky [2] [=] _[𝐼]_ [sky] [·][GAIN]

and _𝜎_ gal [2] [=] _[𝐼]_ [gal] [·][GAIN] [with] _[𝐼]_ [sky] [and] _[𝐼]_ [gal] [the] [surface] [brightness] [of]
the sky and lens in ADU, RON is the detector readout noise (in
ADU) scaled for the number of samplings performed during the
exposure (see Dressel 2022 for details), and GAIN is the detector
gain (in e [−] ADU [−][1] ). Since the sky level that was actually subtracted
during image reduction is not readily available, we use rms [2] bkg [=]

RON [2] + _𝜎_ [2]
sky [. Nevertheless, we estimate the expected variance of the]
sky from the equation above, verifying that _𝜎_ sky _>_ RON.


_4.1.3_ _PSF model_


For each image, we build a PSF model from the non-saturated point
sources with the highest SNR available in the full _WFC3/F110W_
FOV. For each point source, we identify the centroid with the
`find_centroids` task of the `photutils` package and we extract



a cutout of 100 pixel × 100 pixel (6 _._ 4 arcsec × 6 _._ 4 arcsec) corresponding to ∼ 20 FWHM × 20 FWHM. We get the stacked PSF by
summing all the point-source cutouts. Before stacking, we normalise
the total flux of each point source to unity after removing spurious
sources and surface brightness gradient due to nearby bright and
extended sources. The stacked PSF is smoothed using a `python` twodimensional Savitsky-Golay filter [9] (e.g. Ratzlaff & Johnson 1989)
to remove noise. Then, we mask the smoothed PSF model using image segmentation and replace the background pixels with their mean
value. We adopt the resulting stacked, smoothed, and backgroundsubtracted PSF to model the surface brightness distribution of the
source. The average number of point sources we use to build the PSFs
is 2. We show in Fig. 3 the PSF model adopted for the parametric fit
of S_7.


_4.1.4_ _Parametric modelling_


We perform the parametric modelling of the systems following the
steps reported in the flowchart given in Fig. 4 and taking into account
the PSF model, pixel mask, and noise map associated with the image.


9 `[https://github.com/espdev/sgolay2](https://github.com/espdev/sgolay2)`


MNRAS **000**, 1–57 (2022)

10 _E. Borsato et al._



30


25


20


15


10


5


0


**Figure 2.** _Left panel:_ Image of S_7 with the pixel mask (corresponding to the regions with black contours) used to estimate the residual sky level and standard
deviation of the background. The highlighted box marks the FOV of the zoom-in shown in the right panel. _Right panel:_ Trimmed sky-subtracted image and pixel
mask used to fit the surface brightness distribution of the lensing galaxy of S_7.



60


50


40


30


20


10


0


**Figure** **3.** Image of the normalized PSF model adopted to fit the surface
brightness distribution of S_7.


Both `GASP2D` and `GALFIT` algorithms are based on a _𝜒_ [2] minimization. Thus, it is important to adopt initial guesses for the free parameters as close as possible to their actual values. This ensures that the
iteration procedure does not stop on a local minimum of the _𝜒_ [2] distribution. `GASP2D` automatically sets the guess values by performing
a one-dimensional decomposition of the azimuthally-averaged radial
profiles of the surface brightness, ellipticity, and position angle of
the source, which we measured by fitting ellipses to the isophotes
with the `ISOFIT` task (see Sect. 4.2 for details) and adopting the final
pixel mask. For `GALFIT`, we preliminarily fit a de Vaucouleurs law
and adopt for the ellipticity and position angle of the mean values
of the azimuthally-averaged radial profiles. The best-fitting values of
this preliminary decomposition are adopted as guess values for the
actual parametric fitting of the source.
We always start by fitting a single Sérsic component to the source.


MNRAS **000**, 1–57 (2022)



Then, we visually inspect the residual image to look for spurious
sources and/or lensing features. We update the pixel mask to account
for them and repeat the fit. If significant residuals are still visible, we
add a second component and repeat again the fit. We check the new
residual image and iterate the fitting procedure up to a maximum of
three Sérsic extended components and one unresolved nuclear component. The additional luminous components are included to remove
the residual under/over-subtracted structures at scales similar to the

PSF or larger. As a final step, we double-check the best-fitting values
to avoid hitting the boundaries of the allowed ranges for the structural
parameters, for which we adopt the ones implemented in `GASP2D`,
which are [0 _._ 3 _,_ 10] for the Sérsic index and [0 _._ 5 FWHM PSF _,_ +∞)
for the effective radius (see, Méndez-Abreu et al. 2008, 2017, for details). This issue occurs mostly for the Sérsic index of a few luminous
components, which we fix to 0.5, 1, or 4. If the best-fitting effective
radius of the single Sérsic fit is smaller than the PSF FWHM or larger
than the cutout radius, we add a nuclear point source or enlarge the
cutout. When necessary, we mask out the dust patches and lanes as
much as possible to recover a reliable model of the surface brightness
distribution.

The input files adopted by the two algorithms to perform the
surface brightness modelling are listed in Table 4.


_4.1.5_ _Error estimate_


The formal errors on the fitted parameters obtained from the _𝜒_ [2]

minimisation procedure usually underestimate the real errors of the
structural parameters (e.g., Méndez-Abreu et al. 2008). Therefore,
we estimate the errors on the fitted parameters by analysing a sample
of mock galaxies we build through a series of Monte Carlo (MC)
simulations following Dalla Bontà et al. (2018).
To mimic the observational setup, we carry out the MC simulations in two different exposure-time bins, corresponding to 251 s
and 712 s, respectively. For each modelled galaxy (Tables 5 and
A1), we build at least 70 mock galaxies by randomly choosing
each component parameters _𝑝_ _𝑖_ in the range _𝑝_ ˆ _𝑖_ − 0 _._ 3 _𝑝_ ˆ _𝑖_ _<_ _𝑝_ _𝑖_ _<_

**Table** **3.** Redshift of the candidate lenses and background sources of the
confirmed lensing systems.


No. Name _𝑧_ l Ref. _𝑧_ s Ref.
(1) (2) (3) (4) (5) (6)


S_1 HATLASJ000330.6 − 321136 (0.38 ± 0.10) Sh21 3.077 Ur22
S_2 HATLASJ000912.7 − 300807 (0.28 ± 0.08) Sh21 (1.19 ± 0.10) Zh18
S_3 HELMSJ001353.5 − 060200 (0.60 ± 0.18) Na16 1.948 Co23
S_4 HELMSJ003619.8 + 002420 0.257573 Na16 1.617 Co23
S_5 HELMSJ005841.2 − 011149 (0.38 ± 0.08) Na16 1.498 Co23
S_6 HERSJ011722.3 + 005624 (0.87 ± 0.05) Na16 2.469 Co23
S_7 HERSJ012620.5 + 012950 (0.43 ± 0.05) Na16 1.449 Co23
S_8 HERSJ020941.2 + 001558 0.201854 Na16 2.55293 Ge15
S_9 HERMESJ032637 − 270044 – – – –
S_10 HERMESJ033732 − 295353 (0.19 ± 0.05) Sh21 – –
S_11 1 HATLASJ083051 + 013225 1 0.626 Bu13 3.6345 Ya17
S_11 2 HATLASJ083051 + 013225 2 1.002 Bu13 3.6345 Ya17
S_12 HERMESJ100144 + 025709 0.608 Ca14 – –
S_13 HERMESJ103827 + 581544 0.591465 Al17 – –
S_14 HERMESJ110016 + 571736 0.780518 Al17 – –
S_15 HATLASJ114638 − 001132 1.2247 Bu13 3.2596 Y17
S_16 HATLASJ125126 + 254928 (0.62 ± 0.10) Ne17 3.4419 Ba20
S_17 HATLASJ125760 + 224558 0.555449 Al17 (1.53 ± 0.30) Ne17
S_18 HATLASJ133008 + 245860 0.4276 Bu13 3.112 Ca14
S_19 HATLASJ133846 + 255057 (0.42 ± 0.10) Ne17 (2.34 ± 0.40) Ba18
S_20 HATLASJ142935 − 002837 0.21844 Me14 1.0271 Me14
S_21 HERMESJ171451 + 592634 1.236 Sh21 3.17844 HC16
S_22 HERMESJ171545 + 601238 (0.40 ± 0.09) Sh21 2.264 Ca14
S_23 HATLASJ225844.7 − 295124 (0.69 ± 0.21) Sh21 (2.48 ± 0.040) Ba18
S_24 HELMSJ232210.3 − 033559 (0.14 ± 0.09) Na16 4.688 Co23
S_25 1 HATLASJ233037.2 − 331217 1 (0.66 ± 0.17) Sh21 2.170 Ur22
S_25 2 HATLASJ233037.2 − 331217 2 (0.66 ± 0.17) Sh21 2.170 Ur22
S_26 HELMSJ001626.0 + 042613 0.2154 Am18 2.509 Na16
S_27 HATLASJ002624.8 − 341737 (0.93 ± 0.35) Wa22 3.050 Ur22
S_28 HELMSJ004723.6 + 015751 0.3650 Am18 1.441 Na16
S_29 HERSJ012041.6 − 002705 (0.73 ± 0.04) Na16 2.015 Co23
S_30 HATLASJ085112 + 004934 (0.66 ± 0.32) Sh21 (1.77 ± 0.27) MG19
S_31 HATLASJ085359 + 015537 (1.16 ± 0.22) Sh21 2.0925 Ya16
S_32 HERMESJ104549 + 574512 (0.20 ± 0.02) Wa13 2.991 Wa13
S_33 HERMESJ105551 + 592845 (0.38 ± 0.11) Wa13 1.699 [a] Wa13
S_34 HERMESJ105751 + 573026 (0.60 ± 0.04) Ga11 2.9575 Ga11
S_35 HATLASJ132630 + 334410 0.7856 Bu13 2.951 Bu13
S_36 1 HATLASJ133543 + 300404 1 0.9825 St14 2.685 Ca14
S_36 2 HATLASJ133543 + 300404 2 0.9845 St14 2.685 Ca14
S_36 3 HATLASJ133543 + 300404 3 0.9815 St14 2.685 Ca14
S_36 4 HATLASJ133543 + 300404 4 0.9945 St14 2.685 Ca14
S_37 HATLASJ142140 + 000448 (1.11 ± 0.41) Sh21 2.781 Co23
S_38 HERMESJ142824 + 352620 1.034 Bo06 1.325 Bo06
S_39 HATLASJ223753.8 − 305828 (0.54 ± 0.14) Sh21 (2.13 ± 0.38) Wa22
S_40 HATLASJ225250.7 − 313657 (0.69 ± 0.26) Sh21 2.433 Ur22
S_41 HELMSJ233441.0 − 065220 – – 1.905 Co23
S_42 HELMSJ233633.5 − 032119 – – 2.335 Co23
S_43 HELMSJ001615.7 + 032435 0.663 Na16 2.765 Na16
S_44 HELMSJ002220.9 − 015524 (0.90 ± 0.15) Sh21 5.162 As16
S_45 HELMSJ003814.1 − 002252 (0.17 ± 0.08) Na16 4.984 Co23
S_46 HELMSJ003929.6 + 002426 (0.72 ± 0.23) Sh21 2.848 Co23
S_47 HELMSJ004714.2 + 032454 (0.48 ± 0.08) Na16 1.19 Na16
S_48 1 HELMSJ005159.4 + 062240 1 0.60266 Ok21 2.392 Na16
S_48 3 HELMSJ005159.4 + 062240 3 0.59852 Ok21 2.392 Na16
S_49 HATLASJ005724.2 − 273122 (0.89 ± 0.41) Wa22 3.261 Ur22
S_50 HERMESJ021831 − 053131 1.350 Wa13 3.3950 Wa13
S_51 HERMESJ033211 − 270536 – – – –
S_52 HERMESJ044154 − 540352 – – – –
S_53 HATLASJ083932 − 011760 (0.42 ± 0.12) Sh21 2.669 Co23
S_54 1 HATLASJ091841 + 023048 1 (0.91 ± 0.32) Sh21 2.5811 Ha12
S_54 2 HATLASJ091841 + 023048 2 (0.91 ± 0.32) Sh21 2.5811 Ha12
S_55 HATLASJ113526 − 014606 – – 3.1276 Ha12
S_56 HATLASJ115433.6 + 005042 (0.52 ± 0.11) Sh21 (3.90 ± 0.50) Ba20
S_57 HATLASJ120127.6 − 014043 (0.88 ± 0.35) Sh21 (4.06 ± 0.38) MG19
S_58 HATLASJ131611 + 281220 (0.90 ± 0.13) Be21 2.9497 Ne20
S_59 HATLASJ134429 + 303036 0.6721 Bu13 2.3010 Ha12
S_60 1 HATLASJ141352 − 000027 1 0.5478 Bu13 2.4782 Ha12
S_60 3 HATLASJ141352 − 000027 3 0.5494 Bu13 2.4782 Ha12
S_61 1 HATLASJ142414 + 022304 1 0.595 Bu13 4.243 Co11
S_61 2 HATLASJ142414 + 022304 2 0.595 Bu13 4.243 Co11
S_62 HERMESJ142826 + 345547 0.414 Wa13 2.804 Wa13
S_63 HATLASJ230815.5 − 343801 (0.72 ± 0.21) Wa22 (4.03 ± 0.38) MG19
S_64 HELMSJ232439.5 − 043936 (0.67 ± 0.26) Sh21 2.473 Na16
S_65 HELMSJ233620.8 − 060828 0.3958 Na16 3.434 Na16


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the _Herschel_ detection. Cols. (3) and

(4): Redshift of the lens candidate and reference. Cols. (5) and (6): Redshift of the background source
and reference. The bracketed values are photometric redshifts. Following are the abbreviations used
for the references that are not already included in Table 1: As16: Asboth et al. (2016); Ba20: Bakx
et al. (2020); Co23: Cox et al. (2023); HC16: Hernán-Caballero et al. (2016); MG19: Manjón-García

et al. (2019); Ne20: Neri et al. (2020); Ok21: Okido et al. (2021); St14: Stanford et al. (2014); Wa22:

Ward et al. (2022); Ya16: Yang et al. (2016).



_Characterisation of HST confirmed lenses_ 11


**Figure 4.** Flowchart describing the steps of the parametric surface-brightness
modelling.



_𝑝_ ˆ _𝑖_ + 0 _._ 3 _𝑝_ ˆ _𝑖_ where _𝑝_ ˆ _𝑖_ is the best-fitting value. We create more than
7800 mock galaxies in total. The image size of each mock source
range between 200 pixel × 200 pixel (12 _._ 8 arcsec × 12 _._ 8 arcsec) to
400 pixel× 400 pixel (25 _._ 6 arcsec× 25 _._ 6 arcsec) to enclose the largest
fitted lens of that particular magnitude bin. We convolve the mock
galaxies of each magnitude bin with a PSF that was randomly chosen
from those produced to fit the systems of that particular magnitude
bin. We adopt the same pixel scale, detector gain, and readout noise


MNRAS **000**, 1–57 (2022)

12 _E. Borsato et al._


**Table 4.** Input files adopted to perform the surface brightness modelling with the different fitting algorithms used in this work.


Algorithm Noise Map PSF Model Isophote Table Parametric Functions Parameter Guesses Pixel Mask


`GASP2D` yes yes yes yes optional yes
`GALFIT` yes yes no yes yes yes
`ISOFIT+CMODEL` no no yes no no yes



of the real images. In addition, we add a background level corresponding to the median rms bkg measured in the real images of that
particular magnitude bin, and we add the photon noise in order to
match the SNR of the mock and real images.
We run `GASP2D` or `GALFIT` with the appropriate combination of
components to analyse the images of the mock galaxies. We then
group the modelled galaxies according to their component combination (i.e. Sérsic, de Vaucouleurs, Sérsic-Sérsic, etc.). For each
component of each modelled galaxy, we bin the different values of
the mock galaxies in bins of one or two-magnitude width centred
on the magnitude of the best-fitting model component. We study the
distribution of the relative errors on the effective surface brightness
_𝐼_ e, effective radius _𝑅_ e, and Sérsic index _𝑛_ as ( _𝑝_ output / _𝑝_ input − 1) and
of the absolute errors on the position angle PA and axial ratio _𝑞_ as
( _𝑝_ output − _𝑝_ input ). All the distributions appear to be nearly Gaussian
after removing all the systems for which the fit failed, e.g. when
one of the fitted components goes to zero or the model extends significantly more than the cutout. We measure the biweight location
and median absolute deviation of each distribution to detect possible systematic errors and derive the errors on the single parameters,
respectively. We do not identify any systematic error, as all biweight
location values are consistent with zero.


**4.2** **Non-parametric approach**


We use `ISOFIT` to model the surface brightness distribution of the
highly-inclined disk foreground lensing galaxies ( _𝑖>_ 80 [◦] ) for which
`GASP2D` and `GALFIT` fail to recover the structural parameters. `ISOFIT`
models the galaxy isophotes, taking into account deviations from a
perfect elliptical shape. It supersedes the `IRAF` [10] task `ELLIPSE` (Jedrzejewski 1987) by sampling the isophotes according to eccentric
anomaly rather than azimuthal angle and fitting simultaneously all
the higher-order Fourier harmonics. `ISOFIT` provides a table with the
best-fitting parameters of the galaxy isophotes, which can be used
to build the model image through the `IRAF` task `CMODEL` (Ciambur
2015). Before fitting the isophotes, we subtract the residual sky level
and built the pixel mask, as it has been done for the images of the
systems to be fitted with the parametric approach and described in
Sections 4.1.1 and 4.1.2. Since `ISOFIT` models the observed surface

brightness distribution of the galaxy through an isophotal fit and without disentangling the light contribution of its structural components,
we do not need to account for the image PSF and noise map. The input
files needed by `ISOFIT` are listed in Table 4. Unfortunately, we are
not able to model HATLASJ142935−002837 (G15v2.19; S_20) due
to the low SNR of the image, which is heavily obscured by a complex
pattern of dust that is not possible to be successfully masked. For the
analysis of S_20, we refer the reader to Calanog et al. (2014) and
Messias et al. (2014), who managed to model this lens using Keck
and ancillary ALMA observations. As such, the following results are
limited to the 63 systems we could model.


10 `[https://github.com/iraf-community/iraf](https://github.com/iraf-community/iraf)`


MNRAS **000**, 1–57 (2022)



80


60


40


20


0



|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|D|Col23|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||||||
||||||||||||||||||||||C<br>B<br>||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||A|A|
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||


10 [2] 10 [3]



S 500 [mJy]


**Figure 5.** Distribution of the 281 sample systems with _HST_ snapshot observations as a function of the _𝑆_ 500 flux density. The red, pink, light blue and
blue histograms refer to the systems classified as A, B, C, and D, respectively.


**4.3** **Surface brightness modelling results**


After subtracting the foreground lens candidates, we check the residuals for lensing morphology, finding 9 new lensed systems. The
confirmed lenses increase to 65 systems. For 42 of these, we detect the observed-frame near-IR emission of the background source.
As a result, the fraction of confirmed systems increases more than
doubled, from 9% to 23%. The number of B, C, and D systems
becomes 67, 120, and 29, respectively, while their fractions change
to 24%, 43%, and 10%. Figure 5 shows the distribution of the flux
densities at 500 _𝜇_ m of our sample systems divided according to their
classification. Most of the systems have _𝑆_ 500 ≥ 80 mJy, except for
those from Calanog et al. (2014). We note that, as a consequence
of the preliminary nature of the H-ATLAS catalogues used in Negrello et al. (2014), several systems end up having _𝑆_ 500 _<_ 80 mJy in
the final release of the H-ATLAS catalogues (Valiante et al. 2016;
Maddox et al. 2018). We adopt the revised _𝑆_ 500 values in Fig. 5. We
confirm, according to expectations (Negrello et al. 2007; Wardlow
et al. 2013), that the number of A and B systems increases at increasing flux densities, whereas the number of C and D systems peaks at
lower flux densities. Unfortunately, due to the sporadic coverage of
both the multiwavelength follow-ups and _HST_ snapshots, we can not
draw meaningful statistical conclusions on the population of lensed
DSFGs. In Fig. 6, we show the _𝑆_ 350 / _𝑆_ 500 distribution as a function of
the flux density at 500 _𝜇_ m for the A systems. In this case, the different
colors refer to the different classification methods. _HST_ confirmed
systems, both before and after the lens subtraction, tend to have lower
_𝑆_ 350 / _𝑆_ 500 flux density ratios than those of the systems confirmed by
multiwavelength follow-ups. This is consistent with them being at
lower redshifts and sampling redder, less obscured, stellar emission.
Most of the systems have SEDs peaking at 350 _𝜇_ m, as illustrated in
Fig. 7. This should be the case for galaxies with bright _𝑆_ 500 flux densities, which are expected to be located at 1 ∼ _[<]_ _𝑧_ ∼ _[<]_ 4 and potentially
lensed (González-Nuevo et al. 2012). We note that the C and D systems tend to spread over a wider range of flux density ratios than the

2.2


2.0


1.8


1.6


1.4


1.2


1.0


0.8





_Characterisation of HST confirmed lenses_ 13


maps of the systems listed in Table 5, and one system modelled with
`ISOFIT` (S_5). The remaining systems are shown in Fig. A1.
In the rest of this section, we summarise the properties of each
candidate lens we modelled. Table 3 reports the references for the
redshifts of the lens and source mentioned hereafter. We find that
34 of the systems discussed here have already been studied in the
literature. Bussmann et al. (2013, 2015), Enia et al. (2018), Dye et al.
(2018), and Maresca et al. (2022) performed lens modelling and, in
some cases, SED fitting of SMA and/or ALMA observations of 30,
29, 12, 6, and 7 sources, respectively, of these 11, 4, 8, 6, 4 sources
were target candidates of our observations and are thus included in
our analysis. Giulietti et al. (2022) studied the far-IR/radio correlation
of 28 sources, 18 of which are included in our sample. Calanog
et al. (2014) analysed 11 more systems of our sample (Table 1),
and performed the source reconstruction on the lens-subtracted _HST_
images. Cox et al. (2011), Gavazzi et al. (2011), Bussmann et al.
(2012), Fu et al. (2012), Messias et al. (2014), Geach et al. (2015),
Nayyeri et al. (2017), Butler et al. (2021), Liu et al. (2022), Dye
et al. (2022), Giulietti et al. (2023) analysed single sources. None
of these previous works focused on the photometric properties of
the lenses or performed a detailed analysis and modelling of their
surface brightness. Our results thus represent the best reference for
such information. In the following description, we report any relevant
information available for each system from these previous works.


_4.3.1_ _HST confirmed lenses_


**HATLASJ000330.6** − **321136 (HerBS155; S_1)** : We model this type
1 foreground lens at _𝑧_ [phot] l = 0 _._ 38 (Shirley et al. 2021) with two Sérsic
components using `GASP2D` . The background lensed source is located
at _𝑧_ [spec] s = 3 _._ 08, as measured by the BEARS survey (Urquhart et al.
2022). It forms two regular arcs on the SE and NW sides of the lens.
**HATLASJ000912.7** − **300807** **(SD.v1.70;** **S_2)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 28 (Shirley et al. 2021) with
three Sérsic components using `GALFIT` to account for the different
location of their centres. The background lensed source is located
at _𝑧_ [phot] s = 1 _._ 19 (Zhang et al. 2018), and it forms a complex and
multi-component arc-like main image on the SE side of the lens and
a compact irregular secondary image on the NW side.
**HELMSJ001353.5** − **060200** **(HELMS31;** **S_3)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 60 (Nayyeri et al. 2016) with a single Sérsic component and an exponential component using `GASP2D` .
**HELMSJ003619.8** + **002420** **(HELMS14;** **S_4)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 26 (Nayyeri et al. 2016) with
three Sérsic components using `GALFIT` to account for the different
location of their centres. The background lensed source is located at
_𝑧_ [spec] s = 1 _._ 62 (Cox et al. 2023) and forms an almost complete ring
( _𝑟_ ∼ 2 arcsec) consisting of a diffuse component and three brighter
knots located on the SE, SW, and NW sides of the lens. Two additional
faint NE and SW structures are visible close to the ring, but they do
not have a clear lensed morphology.
**HELMSJ005841.2** − **011149 (HELMS23; S_5)** : The foreground
lens is a type 1 edge-on galaxy at _𝑧_ [phot] l = 0 _._ 38 (Nayyeri et al. 2016),
which we model with `ISOFIT` . The background lensed source is
located at _𝑧_ [spec] s = 1 _._ 50 (Cox et al. 2023) and gives rise to two bright
knots along the galaxy minor axis, opposite to each other with respect
to the galaxy nucleus.
**HERSJ011722.3** + **005624** 1 _,_ 2 **(HERS10;** **S_6)** : This type 3 foreground lensing system is formed by a main galaxy (labelled as ‘1’
in Fig. A1) at _𝑧_ [phot] l = 0 _._ 87 (Nayyeri et al. 2016) and possibly a secondary fainter galaxy (labelled as ‘2’), for which the redshift is not


MNRAS **000**, 1–57 (2022)


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||M|~~isua~~<br>ultiw|ave|len|gt|h||
|||||||||L|ens s|ubt|rac|tio|n||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||



10 [2]


S 500 [mJy]


**Figure** **6.** Flux density ratio _𝑆_ 350 / _𝑆_ 500 as function of the flux density at
500 _𝜇_ m for the systems classified as A. The blue, orange, and green colors
marks systems are classified according to visual inspection, multiwavelength
follow-up observations, and after the lens subtraction, respectively. The cross
at the top left corner gives the median measurement error.



3.0


2.5


2.0


1.5



A


B


C



1.0


D


0.5

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||
||||||
||||||
||||||
||||||
||||||
|0.0<br>0.5<br>1<br>S/S|0.0<br>0.5<br>1<br>S/S|0.0<br>0.5<br>1<br>S/S|.0<br>1.5<br>|.0<br>1.5<br>|



**Figure 7.** Distribution of the _Herschel_ sub-mm flux density ratios of the 281
systems with _HST_ snapshot observations, which are color-coded according
to their class. The light grey area marks the region of the systems with the
SED peaking at 350 _𝜇_ m, while the dark grey area indicates the region of the
systems with the SED peaking at 500 _𝜇_ m. The cross at the top left corner
gives the median measurement error.


A or B systems. This is in line with them being mostly contaminants
with a varying range of intrinsic properties. We find that 47 of the 64
systems classified as A (73%) have _𝑆_ 500 _>_ 100 mJy, 12 (19%) have
80 _<_ _𝑆_ 500 _<_ 100 mJy and 5 (8%) have _𝑆_ 500 _<_ 80 mJy.
In the following, we analyse the systems confirmed as strong lenses
(class A). Among the 63 successfully modelled systems, which comprise one or more than one galaxy, we include the surface brightness

∼
distribution of 87 galaxies. A high fraction of these galaxies ( 47%)
show complex surface brightness profiles that often need more than
one component (e.g., two or three Sérsic profiles or a combination of
Sérsic profiles and PSF). For three systems (S_47, S_48, and S_81)
we include spiral arms too. The parameters of the best-fitting models
for four representative systems are given in Table 5. They are three
type 1 lenses, one visually confirmed (S_12) and one with multiwavelength observations (S_50). In addition, there is one type 2 system
(S_11) and one type 3 system (S_8). The remaining systems can be
found in Table A1. In Fig. 8, we show the cutouts of the _HST_ images,
best-fitting models, _HST_ residuals after model subtraction, and SNR

14 _E. Borsato et al._


yet available. This prevents us from being more conclusive about the
lensing nature of the secondary galaxy. We model the two galaxies
with `GASP2D` using one Sérsic and one Gaussian component for the
brighter galaxy and a single Sérsic component for the fainter one. The
background lensed source is located at _𝑧_ [spec] s = 2 _._ 47 (Cox et al. 2023)
and forms an arc on the E side of the lens and a diffuse secondary
image on the NW side.

**HERSJ012620.5** + **012950 (HERS5; S_7)** : We model this type 1
foreground lens at _𝑧_ [phot] l = 0 _._ 43 (Nayyeri et al. 2016) with one Sérsic
and one Gaussian component using `GASP2D` . The background lensed
source is located at _𝑧_ [spec] s = 1 _._ 45 (Cox et al. 2023) and forms two arcs
on the NE and SW sides of the lens. The SW arc shows an additional

diffuse radial component, which extends westward.
**HERSJ020941.2** + **001558** 1 _,_ 2 **(HERS1;** **S_8)** : This type 3 foreground lensing system is formed by a main galaxy (labelled as ‘1’
in Fig. 8) and a second fainter galaxy (labelled as ‘2’), which are
both located at _𝑧_ [spec] l = 0 _._ 20 (Nayyeri et al. 2016; Liu et al. 2022).
We use `GASP2D` to model the brighter galaxy with three Sérsic components and the fainter one with a single Sérsic component. The
background lensed source at _𝑧_ [spec] s = 2 _._ 55 (Geach et al. 2015) forms
a bright extended arc on the SW side of the lens and two knots on
the E and SE sides. This system was studied in detail by Geach et al.
(2015) and Liu et al. (2022), who measured an Einstein radius of
_𝜃_ E = 2 _._ 48 [+] − [0] 0 _[.]_ _._ [02] 01 [arcsec.] [It] [has] [also] [been] [observed] [with] [SMA] [(340]
GHz, Liu et al. 2022), ALMA (Band 7, Liu et al. 2022), VLA (1.4
GHz and 5 GHz, Geach et al. 2015), eMERLIN (1.52 GHz, Geach
et al. 2015) in the sub-mm/mm wavelength range and with _HST_ (1.6
_𝜇_ m, Liu et al. 2022) and Keck/NIRC2 AO ( _H_ and _K_ _𝑠_ band, Liu et al.
2022) in the near-IR. The sub-mm/mm follow-up observations show
no significant difference in morphology with those performed in the

near-IR.

**HERMESJ032637** − **270044 (HECDFS05; S_9)** : We model this
type 1 foreground lens with a single Sérsic component using `GASP2D` .
The background lensed source forms two compact images on the E
and W sides of the lens, which is circled by a fainter incomplete
ring. This system was studied in detail by Calanog et al. (2014), who
measured an Einstein radius of _𝜃_ E = 0 _._ 96 [+] − [0] 0 _[.]_ _._ [02] 03 [arcsec.]
**HERMESJ033732** − **295353 (HECDFS02; S_10)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 19 (Shirley et al. 2021) with three
Sérsic components using `GASP2D` . The background lensed source
forms a bright extended arc (divided into two knots on the NE side of
the lens) and an inner secondary image on the SW side. This system
was studied in detail by Calanog et al. (2014), who measured an
Einstein radius of _𝜃_ E = 1 _._ 65 [+] − [0] 0 _[.]_ _._ [03] 05 [arcsec.]
**HATLASJ083051** + **013225** 1 _,_ 2 **(HerBS4; S_11)** : This type 2 foreground lens is formed by two galaxies, one (labelled as ‘1’ in Fig. 8)
at _𝑧_ [spec] l = 0 _._ 63 and the other (labelled as ‘2’) at _𝑧_ [spec] l = 1 _._ 00 (Bussmann et al. 2013). We deblend them with `GALFIT` by simultaneously
modelling their surface brightness with a single Sérsic component
each. The background lensed source at _𝑧_ [spec] s = 3 _._ 11 (Yang et al.
2017) shows a very complex structure with two intersecting arcs on
the NW side of the lens. This system was studied in detail by Enia
et al. (2018), Yang et al. (2019), and Maresca et al. (2022) who modelled high-resolution SMA (340 GHz, Bussmann et al. 2013), ALMA
(Band 7, Amvrosiadis et al. 2018; and Band 4 Yang et al. 2019) observations. This system was also observed with Keck/NIRC2 AO ( _K_ _𝑠_
band, Calanog et al. 2014). The sub-mm/mm follow-up observations
show a ring around both lenses that splits into two arcs on the SE
and S sides of the system, a third compact image on the N side of the
second galaxy, and a further compact image between the two lenses.

**HERMESJ100144** + **025709** **(HCOSMOS01;** **S_12)** : We model


MNRAS **000**, 1–57 (2022)



this type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 61 (Calanog et al. 2014) with
a single Sérsic component using `GASP2D` . The background lensed
source forms three compact images on the NE, S, and NW sides
of the lens, which is surrounded by a fainter ring. This system was
studied in detail by Calanog et al. (2014), who measured an Einstein
radius of _𝜃_ E = 0 _._ 91 [+] − [0] 0 _[.]_ _._ [01] 01 [arcsec.] [It] [was] [also] [observed] [with] [ALMA]
(Band 7, Bussmann et al. 2015) in the sub-mm/mm wavelength range
and with Keck/NIRC2 AO ( _K_ _𝑠_ band, Calanog et al. 2014) in the nearIR. The sub-mm/mm follow-up observations show only two lensing
features on the NW and SE sides of the lens, with the first one having
an arc-like shape. Bussmann et al. (2015) used the ALMA dataset to
measure an Einstein radius of _𝜃_ E = 0 _._ 956 ± 0 _._ 005 arcsec.

**HERMESJ103827** + **581544** **(HLock04;** **S_13)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 59 (SDSS DR13, Albareti et al.
2017) with two Sérsic components using `GASP2D` . The background
lensed source forms two knots on the SE and NW sides of the lens,
which is also surrounded by other fainter and more extended arcs.
This system was studied in detail by Calanog et al. (2014), who
measured an Einstein radius of _𝜃_ E = 2 _._ 40 [+] − [0] 0 _[.]_ _._ [01] 05 [arcsec] [and] [it] [was]
also observed with SMA (340 GHz, Bussmann et al. 2013). The
sub-mm/mm follow-up observations show no significant difference
in morphology with respect to the near-IR observations, with the
exception of a positional offset. Bussmann et al. (2013) used the
SMA dataset to measure an Einstein radius of _𝜃_ E = 2 _._ 0 ± 0 _._ 2 arcsec.

**HERMESJ110016** + **571736** **(HLock12;** **S_14)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 78 (SDSS DR13, Albareti et al.
2017) with a single Sérsic component using `GASP2D` . The background
lensed source gives rise to an extended arc on the NW side of the
lens and a very faint compact secondary image on the SE side. This
system was studied in detail by Calanog et al. (2014), who measured
an Einstein radius of _𝜃_ E = 1 _._ 14 [+] − [0] 0 _[.]_ _._ [04] 07 [arcsec.]
**HATLASJ114638** − **001132** 1 _,_ 2 **(HerBS2; S_15)** : This type 2 foreground lens is formed by two galaxies at _𝑧_ [spec] s = 1 _._ 22 (Bussmann
et al. 2013), which we deblend by simultaneously modelling them
with `GALFIT` using two Sérsic components each. The background
lensed source at _𝑧_ [spec] s = 3 _._ 26 (Yang et al. 2017) shows a very complex structure with multiple arcs and compact images. This system
was studied in detail by Fu et al. (2012). It was also observed with
ALMA (Band 6, Amvrosiadis et al. 2018), SMA (340 GHz, Fu et al.
2012), PdBI (232 GHz, Omont et al. 2013), and the JVLA ( _Ka_ -band
Fu et al. 2012) in the sub-mm/mm wavelength range and Keck/NIRC2
AO ( _J_ and _K_ _𝑠_ band, Fu et al. 2012) in the near-IR. The sub-mm/mm
follow-up observations show three images: two arcs that both split
into two knots on the S and N sides of the lenses and a compact image
between the two lenses. There is only a partial overlap between the
near-IR and sub-mm/mm observations.

**HATLASJ125126** + **254928** **(HerBS52;** **S_16)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 62 (Negrello et al. 2017), with
a single Sérsic component using `GASP2D` . The background lensed
source at _𝑧_ [spec] s = 3 _._ 44 (Bakx et al. 2020) forms four knots located N,
NE, S, and NW with respect to the lens, three of which are connected
by a fainter arc extending on the N side. This object was also observed with ALMA (Band 6, Prop. ID 2018.1.00526.S, PI I. Oteo).
The sub-mm/mm follow-up observations show the counterparts of
the N, NE, and S images.

**HATLASJ125760** + **224558** **(S_17)** : We model this type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 55 (SDSS DR13, Albareti et al. 2017) with
a single Sérsic component using `GASP2D` . The background lensed
source at _𝑧_ [phot] s = 1 _._ 53 (Negrello et al. 2017) forms a compact ring
and a brighter knot on the NW side of the lens, which is slightly
offset with respect to the ring.

**HATLASJ133008** + **245860** **(HerBS12;** **S_18)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 43 (Bussmann et al. 2013) with
one Sérsic and one Gaussian component using `GASP2D` . The background lensed source at _𝑧_ [spec] s = 3 _._ 11 (Calanog et al. 2014) forms
three compact images on the N, SE, and SW sides of the lens, which
is also surrounded by a fainter incomplete ring. This system was
studied in detail by Calanog et al. (2014), who measured an Einstein radius of _𝜃_ E = 0 _._ 944 [+] − [0] 0 _[.]_ _._ [002] 001 [arcsec.] [It] [was] [also] [observed] [with]
ALMA (Band 7, Prop. ID 2018.1.00966.S, N. Indriolo), SMA (340
GHz, Bussmann et al. 2013), PdBI (240 GHz, Omont et al. 2013),
and NOEMA (283 GHz, Yang et al. 2016) in the sub-mm/mm wavelength range and with Keck/NIRC2 AO ( _K_ _𝑠_ band, Calanog et al.
2014) in the near-IR. The sub-mm/mm follow-up observations show
no significant difference in morphology with respect to the near-IR
observations. Bussmann et al. (2013) used the ALMA dataset to
measure an Einstein radius of _𝜃_ E = 0 _._ 88 ± 0 _._ 02 arcsec.


**HATLASJ133846** + **255057** **(HerBS29;** **S_19)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 42 (Negrello et al. 2017) with
a single Sérsic component using `GASP2D` . The background lensed
source at _𝑧_ [phot] s = 2 _._ 34 (Bakx et al. 2018) forms two extended arcs
with a sharp break on the S and N sides of the lens. This system
was observed with SMA (340 GHz, Bussmann et al. 2013) too. The
sub-mm/mm follow-up observations show no significant difference
in morphology with respect to the near-IR ones.


**HERMESJ171451** + **592634** **(HFLS02;** **S_21)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 1 _._ 24 (Shirley et al. 2021) with
a single de Vaucouleurs component using `GASP2D` . The background
lensed source at _𝑧_ [spec] s = 3 _._ 18 (Hernán-Caballero et al. 2016) forms
two arcs on the NE and SW sides of the lens, which is surrounded
by a fainter ring. This system was studied in detail by Calanog et al.
(2014), who measured an Einstein radius of _𝜃_ E = 0 _._ 87 [+] − [0] 0 _[.]_ _._ [02] 05 [arcsec.]

**HERMESJ171545** + **601238** 1 _,_ 2 **(HFLS08;** **S_22)** : This type 3
foreground lensing system is formed by a main galaxy (labelled
as ‘1’ in Fig. A1) at _𝑧_ [phot] l = 0 _._ 40 (Shirley et al. 2021) and possibly a
secondary unresolved galaxy (labelled as ‘2’), for which the redshift
is not yet available. This prevents us from being more conclusive
about the lensing nature of the secondary galaxy. We used `GASP2D` to
model the brighter galaxy with two Sérsic components and one PSF
and the fainter one with a single Sérsic component. The background
lensed source at _𝑧_ [spec] s = 2 _._ 26 (Calanog et al. 2014) forms an extended
and irregular arc E of the lens and a compact secondary image on its
W side. This system was studied in detail by Calanog et al. (2014),
who measured an Einstein radius of _𝜃_ E = 1 _._ 95 [+] − [0] 0 _[.]_ _._ [05] 04 [arcsec.]

**HATLASJ225844.8** − **295124 (HerBS26; S_23)** : This type 2 configuration is consistent with two blended galaxies at _𝑧_ [phot] l = 0 _._ 69
(Shirley et al. 2021), which we deblend by simultaneously fitting
them with `GALFIT` using one and two Sérsic components, respectively. The background lensed source is located at _𝑧_ [phot] s = 2 _._ 48 (Bakx
et al. 2018). It gives rise to an extended arc encircling the lens on
the SW side but without showing any clear secondary image. This is
likely due to the shear effect caused by the multiple-lens system.


**HELMSJ232210.3** − **033559** 1 _,_ 2 **(HELMS19;** **S_24)** : This type 3
foreground lensing system is formed by a main galaxy (labelled as
‘1’ in Fig. A1) at _𝑧_ [phot] l = 0 _._ 14 (Nayyeri et al. 2016) and possibly a
secondary fainter galaxy (labelled as ‘2’), for which the redshift is not
yet available. This prevents us from being more conclusive about the
lensing nature of the secondary galaxy. We model the two galaxies
with `GASP2D` using two and one Sérsic components, respectively.
The background lensed source is located at _𝑧_ [spec] s = 4 _._ 69 (Cox et al.
2023) and forms an extended irregular arc on the E side of the lens,



_Characterisation of HST confirmed lenses_ 15


a compact secondary image on the SW side, and possibly a third
fainter image on the NW side.
**HATLASJ233037.2** − **331217** 1 _,_ 2 **(HerBS123; S_25)** : This type 3
foreground lensing system is formed by a main galaxy (labelled as
‘1’ in Fig. A1) at _𝑧_ [phot] l = 0 _._ 66 (Shirley et al. 2021) and possibly a
secondary unresolved galaxy (labelled as ‘2’), for which the redshift
is not yet available. We deblend and model the two galaxies with
`GALFIT` by using two Sérsic components and a single unresolved
component, respectively. The background lensed source is located
at _𝑧_ [spec] s = 2 _._ 17, as measured by the BEARS survey (Urquhart et al.
2022). It shows a very complex structure with multiple knots embedded into a main arc and a second inner elongated image on the SE
side. This kind of morphology is indicative of strong shear, supporting the idea of a multiple lensing system.


_4.3.2_ _Lenses confirmed after the lens subtraction_


**HELMSJ001626.0** + **042613** **(HELMS22;** **S_26)** : We model this
type 1 foreground lens at _𝑧_ [spec] s = 0 _._ 22 (Amvrosiadis et al. 2018)
with two Sérsic components using `GASP2D` . The background lensed
source at _𝑧_ [spec] s = 2 _._ 51 (Nayyeri et al. 2016) forms an arc on the
S side of the lens. This system was observed with ALMA (Band
6, Amvrosiadis et al. 2018; Band 7, Prop. ID 2016.1.01188.S, S.
Eales) in the sub-mm/mm wavelength range. The sub-mm morphology shows two compact images on top of the _HST_ arc and a secondary
image closer to the lens on its NE side. This system was studied in
detail by Dye et al. (2018), who measured an Einstein radius of
_𝜃_ E = 0 _._ 98 ± 0 _._ 07 arcsec. The sub-mm/mm follow-up observations
show both the S arc that splits into two images and a fainter secondary
image on the NE side.
**HATLASJ002624.8** − **341737** **(HerBS22;** **S_27)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 93 (Ward et al. 2022) with two
Sérsic components using `GASP2D` . The background lensed source at
_𝑧_ [phot] s = 2 _._ 70 (Zhang et al. 2018) forms an arc on the SW of the lens
and a fainter secondary image on the opposite side. The SW arc is
split into two components: a main one and a fainter one, which are
W and S of the lens, respectively.
**HELMSJ004723.6** + **015751** 1 _,_ 2 **(HELMS9;** **S_28)** : This type 2
foreground lens is formed by two galaxies at _𝑧_ [spec] s = 0 _._ 37
(Amvrosiadis et al. 2018), which we deblend by simultaneously modelling them with `GALFIT` using two Sérsic components for the main
galaxy (labelled as ’1‘ in Table 5) and one de Vaucouleurs component
for the second galaxy (labelled as ’2‘). The background lensed source
at _𝑧_ [spec] s = 1 _._ 44 (Nayyeri et al. 2016) shows a very complex structure
with one confirmed arc on the N side of the lens and possibly multiple compact images. The background lensed source morphology is
likely to be disturbed by additional features possibly related to the
interaction with the two lenses. It was observed with ALMA (Band 6,
Amvrosiadis et al. 2018) in the sub-mm/mm wavelength range. This
system was studied in detail by Dye et al. (2018), who measured an
Einstein radius of _𝜃_ E = 2 _._ 16 ± 0 _._ 10 arcsec. The sub-mm/mm followup observations show clearly the N arc we detected in the _HST_ image
and some hints for further lensed images on the S side of the lens
galaxies.
**HERSJ012041.6** − **002705 (HERS2; S_29)** : We model this type 1
foreground lens at _𝑧_ [phot] l = 0 _._ 73 (Nayyeri et al. 2016) with two Sérsic
components using `GASP2D` . The background lensed source forms an
arc on the NE of the lens, a clump eastward of the arc and a fainter
secondary image on the SW side of the lens.
**HATLASJ085112** + **004934** **(S_30)** : We model this type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 66 (Shirley et al. 2021) with three Sér

MNRAS **000**, 1–57 (2022)

16 _E. Borsato et al._


sic components using `GASP2D` . The background lensed source at
_𝑧_ [phot] s = 1 _._ 77 (Manjón-García et al. 2019) forms three arcs on the
SW, SE, and NE sides of the lens. The SW arc is divided into two
parts by a bright clump. This is likely due to the shear effect caused
by nearby galaxies.

**HATLASJ085359** + **015537** **(G09v1.40;** **S_31)** : We model this
type 1 foreground lens with two Sérsic components using `GASP2D` .
The background lensed source at _𝑧_ [spec] s = 2 _._ 09 (Yang et al. 2016)
forms a ring that splits into two arcs on the E and W sides of
the lens. This system was studied in detail by Bussmann et al.
(2013); Calanog et al. (2014), and Butler et al. (2021) with ALMA
(Band 6, Butler et al. 2021 and Prop. ID 2017.1.00027.S, S. Eales;
Band 7, Amvrosiadis et al. 2018 and Butler et al. 2021), and SMA
(340 GHz Bussmann et al. 2013) in the sub-mm/mm wavelength
range and with Keck/NIRC2 AO ( _K_ _𝑠_ band, Calanog et al. 2014)
in the near-IR, respectively. These works measured an Einstein radius of _𝜃_ E = 0 _._ 56 [+] − [0] 0 _[.]_ _._ [01] 02 [arcsec] [from] [the] [Keck] [observations] [and]
_𝜃_ E = 0 _._ 553±0 _._ 004 arcsec from SMA observations. The sub-mm/mm
follow-up observations show no significant difference in morphology
with respect to the near-IR ones.

**HERMESJ104549** + **574512** **(HLock06;** **S_32)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 20 (Wardlow et al. 2013) with
two Sérsic components using `GASP2D` . The background lensed source
at _𝑧_ [spec] s = 2 _._ 91 (Calanog et al. 2014) forms two images on the NW
and SE sides of the lens. Bussmann et al. (2013) used the SMA
dataset to measure an Einstein radius of _𝜃_ E = 0 _._ 10 ± 0 _._ 03 arcsec.

**HERMESJ105551** + **592845 (HLock08; S_)33** : This type 2 foreground lens is formed by two galaxies (labelled as ‘1’ and ‘2’ in
Fig. A1) at _𝑧_ [phot] l = 0 _._ 38 (Wardlow et al. 2013), which we deblend by
simultaneously modelling them with `GALFIT` using one Sérsic component each. The background lensed source at _𝑧_ [spec] s = 1 _._ 70 (Calanog
et al. 2014) shows a complex morphology with a bright arc and a
faint secondary image SW and NE of the galaxy 1 respectively, and
a possible third image E of the galaxy 2.
**HERMESJ105751** + **573026** 1 _,_ 2 _,_ 3 _,_ 4 _,_ 5 _,_ 6 **(HLock01;** **S_34)** : This
type 2 foreground lens is formed by a group of six galaxies (labelled
from ‘1’ to ‘6’ in Fig. A1) at _𝑧_ [phot] l = 0 _._ 60 (Gavazzi et al. 2011).
We simultaneously model them with `GALFIT` using respectively two
Sérsic components, one de Vaucouleurs and one Sérsic component,
one Sérsic component, one de Vaucouleurs component, one Sérsic
component, and a PSF. With respect to Gavazzi et al. (2011) we divide galaxy 5 into two separate components. The background lensed
source at _𝑧_ [spec] s = 2 _._ 96 (Gavazzi et al. 2011) forms a bright arc on the
NE side of galaxy 1 that splits into two images in the proximity of
galaxy 6, two additional bright compact images on the S and NW of
galaxy 1, and, a faint counter image near the NE side galaxy 1 (which
was predicted but not observed by Gavazzi et al. (2011). This system
was also observed with SMA (340 GHz, Bussmann et al. 2013) and
with Keck/NIRC2 AO ( _K_ _𝑠_ band, Gavazzi et al. 2011).

**HATLASJ132630** + **334410** **(NAv1.195;** **S_35)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 79 (Bussmann et al. 2013) with
one Sérsic component using `GASP2D` . The background lensed source
at _𝑧_ [spec] s = 2 _._ 95 (Bussmann et al. 2013) forms two images on the
NW and SE sides of the lens. This system was observed with ALMA
(Band 3, Berman et al. 2022 and Band 6, Prop. ID 2017.1.01214.S,
Y. Min), and SMA (340 GHz Bussmann et al. 2013). The submm/mm follow-up observations show no significant difference in
morphology with respect to the near-IR ones. Bussmann et al. (2013)
and Kamieneski et al. (2023a) used the SMA and ALMA band 3
datasets to measure an Einstein radius of _𝜃_ E = 1 _._ 80 ± 0 _._ 02 arcsec
and _𝜃_ E = 1 _._ 78 [+] − [0] 0 _[.]_ _._ [21] 14 [arcsec, respectively.]


MNRAS **000**, 1–57 (2022)



**HATLASJ133543** + **300404** 1 _,_ 2 _,_ 3 _,_ 4 (HerBS35; S_36): This type 2
foreground lens is formed by a cluster of galaxies (labelled as ‘1’,
‘2’, ‘3’, and ‘4’ in Fig. A1) at _𝑧_ [spec] l = 0 _._ 98 (Stanford et al. 2014;
Nayyeri et al. 2017), which we deblend by simultaneously modelling
them with `GALFIT` using one Sérsic and one PSF component for
galaxy 1 and one Sérsic component each for the remaining ones.
The background lensed source at _𝑧_ [spec] s = 2 _._ 69 (Nayyeri et al. 2017)
shows a complex morphology with a compact bright arc and a faint
secondary image NE and SW of the galaxy 1, one arc S of the galaxies
1 and 2, and another arc N of the galaxies 3 and 4. This system was
observed with SMA (228 GHz, Nayyeri et al. 2017), the JVLA (4
GHz, Nayyeri et al. 2017), and Keck/NIRC2 AO ( _K_ _𝑠_ and _H_ band,
Nayyeri et al. 2017). The sub-mm/mm follow-up observations show
a complex morphology with various arcs and images that are not
detected in the near-IR observations.


**HATLASJ142140** + **000448** **(HerBS140;** **S_37)** : We model this
type 1 foreground lens at _𝑧_ [PHOT] s = 1 _._ 11 (Shirley et al. 2021) with
a single Sérsic component using `GASP2D` . The background lensed
source is located at _𝑧_ [spec] s = 2 _._ 78 (Cox et al. 2023) and forms a faint
ring that splits on the N and S sides of the lens and a clump slightly
offset of the ring on the NE side of the lens.


**HERMESJ142824** + **352620** **(HBootes03;** **S_38)** : We model this
type 1 foreground lens at _𝑧_ [spec] s = 1 _._ 03 (Borys et al. 2006) with two
Sérsic components using `GASP2D` . The background lensed source at
_𝑧_ [spec] s = 1 _._ 33 (Borys et al. 2006) forms a closer arc on the NE of the
lens and a diffuse secondary image on the SW side of the lens. It was
observed with SMA (340 GHz, Bussmann et al. 2013), and ALMA
(Band 6, Amvrosiadis et al. 2018) in the sub-mm/mm wavelength
range. The sub-mm/mm follow-up observations show no significant
difference in morphology with respect to the near-IR observations.
This system was studied in detail by Bussmann et al. (2013), who
measured an Einstein radius of _𝜃_ E = 2 _._ 46 [+] − [0] 0 _[.]_ _._ [01] 01 [arcsec.]


**HATLASJ223753.8** − **305828** **(HerBS68;** **S_39)** : We model this
type 1 foreground lens with one Sérsic component using `GASP2D` .
The background lensed source at _𝑧_ [phot] s = 2 _._ 13 (Ward et al. 2022) or
_𝑧_ [phot] s = 2 _._ 26 (Manjón-García et al. 2019) forms an arc on the SE side
of the lens and a faint secondary image on the E side. The SE arc
shows a secondary faint farther arc that extends from the N tip of the
main arc.


**HATLASJ225250.7** − **313657** **(HerBS47;** **S_40)** : We model this
type 1 foreground lens with one Sérsic component using `GASP2D` .
The background lensed source at _𝑧_ [phot] s = 2 _._ 70 (Manjón-García et al.
2019) forms a bright arc on the NW side of the lens and a faint
secondary image on the SE side. Both the arc and secondary image
are split into two knots.


**HELMSJ233441.0** − **065220** **(HELMS1;** **S_41)** : We model this
type 1 foreground lens with two Sérsic components using `GASP2D` .
For this case, we first model and subtract the main images of the
background lensed sources. Then, we mask the residual signal of
the source and model the lens. The background lensed source is
located at _𝑧_ [spec] s = 1 _._ 90 (Cox et al. 2023) and forms an arc split into
three bright unresolved images on the S side of the lens and a faint
secondary image on the N side of the lens.


**HELMSJ233633.5** − **032119** 1 _,_ 2 **(HELMS41;** **S_42)** : This type 2
foreground lens is formed by two galaxies, which we deblend by
simultaneously modelling them with `GALFIT` using two Sérsic components for the first galaxy (labelled as ’1‘ in Fig. A1) and one Sérsic
component for the second galaxy (labelled as ’2‘). The background
lensed source is located at _𝑧_ [spec] s = 2 _._ 34 (Cox et al. 2023) and forms
a ring (split into three arcs on the N, E, and W of the lens), as well

as a secondary faint, more distant arc and a more diffuse component,
which are located close to the N arc.


_4.3.3_ _sub-mm/mm confirmed lenses_


**HELMSJ001615.7** + **032435** **(HELMS13;** **S_43)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 66 (Nayyeri et al. 2016) with
one Sérsic component and one Gaussian using `GASP2D` . The background lensed source at _𝑧_ [spec] s = 2 _._ 77 (Nayyeri et al. 2016) is detected
by ALMA (Band 7, Amvrosiadis et al. 2018), and forms a wide arc
on the NE side of the lens. No secondary image is found. This system
was studied in detail by Dye et al. (2018), who measured an Einstein
radius of _𝜃_ E = 2 _._ 79 ± 0 _._ 10 arcsec.
**HELMSJ002220.9** − **015524 (HELMS29; S_44)** : We model this
type 1 foreground lens with one Sérsic component using `GASP2D` .
The background lensed source at _𝑧_ [spec] s = 5 _._ 16 (Asboth et al. 2016)
was detected by ALMA (Band 6, Prop. ID 2015.1.01486.S, PI D.
Riechers; Band 7, Prop. ID 2015.1.01486.S, PI D. Riechers; Band
8, Prop. ID 2015.1.01486.S and 2017.1.00043.S, PI D. Riechers). It
forms a ring split into two brighter knots on the N and S sides of the
lens. _HST_ shows an arc-like structure at ∼ 1 _._ 5 − 2 times the Einstein

radius that is not detected in the sub-mm. We argue that it is part
of the foreground galaxy. This system has also available deeper _HST_
_F105W_ (Prop. ID 14083, PI I. Pérez-Fournon), _F125W_ (Prop. ID
15464, PI A. Long), and _F160W_ observations (Prop. ID 14083, PI I.
Pérez-Fournon). No counterpart is found in the _HST_ after subtracting
the lens.

**HELMSJ003814.1** − **002252 (HELMS24; S_45)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 17 (Nayyeri et al. 2016) with one
PSF using `GASP2D` . The background lensed source at _𝑧_ [spec] s = 4 _._ 98
(Su et al. 2017) is detected by ALMA (Band 7, Ma et al. 2019). It
forms an arc and a closer faint secondary image on the NE and SW
sides of the lens, respectively.
**HELMSJ003929.6** + **002426 (HELMS11; S_46)** : The foreground
lens is a type 1 edge-on galaxy, which we model with `ISOFIT` . The
background lensed source is located at _𝑧_ [spec] s = 2 _._ 85 (Cox et al. 2023)
and was detected by ALMA (Band 7, Ma et al. 2019). It forms a ring
with two brighter knots on the N and S sides of the lens. No _HST_
counterpart is found after subtracting the lens.
**HELMSJ004714.2** + **032454** **(HELMS8;** **S_47)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 48 (Nayyeri et al. 2016) with one
Sérsic component and one exponential component using `GALFIT`
including also the spiral structure. Additional _𝑚_ = 2 _,_ 3 Fourier components are added to the spiral arms in order to model their N-S
asymmetry. The background lensed source at _𝑧_ [spec] s = 1 _._ 19 (Nayyeri
et al. 2016) was detected by ALMA (Band 7, Amvrosiadis et al.
2018). It forms one arc on the S side of the lens and a compact secondary image on the N side. Near-IR counterparts of the background
lensed source are visible only for the S arc. This system was studied
in detail by Dye et al. (2018), who measured an Einstein radius of
_𝜃_ E = 0 _._ 59 ± 0 _._ 03 arcsec.
**HELMSJ005159.4** + **062240** 1 _,_ 2 _,_ 3 **(HELMS18;** **S_48)** : This type
2 foreground lens is formed by a group three galaxies at _𝑧_ [spec] l = 0 _._ 60
(Okido et al. 2021), which we deblend by simultaneously modelling
them with `GALFIT` using two Sérsic components for the first galaxy
(labelled as ‘1’ in Fig. A1), one de Vaucouleurs component for the
second galaxy (labelled as ‘2’), and one exponential profile, a PSF,
and spiral arms for the third galaxy (labelled as ‘3’). The background
lensed source at _𝑧_ [spec] s = 2 _._ 39 (Nayyeri et al. 2016) was detected
by ALMA(Band 6, Prop. ID 2017.1.00027.S, PI S. Eales; Band 7,
Amvrosiadis et al. 2018). It forms an arc on the SW side of galaxy 3,



_Characterisation of HST confirmed lenses_ 17


and a secondary image on the E side of galaxies 1 and 2. This system
was studied in detail by Maresca et al. (2022), who modelled the band
7 observations and measured the Einstein radii to be _𝜃_ E = 3 _._ 80±0 _._ 02
arcsec for the galaxies 1 and 2, and _𝜃_ E = 1 _._ 46 ± 0 _._ 02 arcsec for the
galaxy 3. No _HST_ counterpart is found after subtracting the lens.
**HATLASJ005724.2** − **273122** **(HerBS60;** **S_49)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 89 (Ward et al. 2022) with one
Sérsic component using `GASP2D` . The background lensed source at
_𝑧_ [spec] s = 3 _._ 26 (Urquhart et al. 2022) is detected by ALMA (Band 6,
Prop. ID 2018.1.00526.S, PI I. Oteo). It forms a ring that splits into
two knots on the E and the W side of the lens, respectively. No _HST_
counterpart is found after subtracting the lens.
**HERMESJ021831** − **053131** **(HXMM02;** **S_50)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 1 _._ 35 (Wardlow et al. 2013) with
one Sérsic component using `GASP2D` . The background lensed source
at _𝑧_ [spec] s = 3 _._ 40 (Wardlow et al. 2013) is detected by ALMA (Band
6, Prop. ID 2013.1.00781.S, PI B. Hatsukade; Band 7, Prop. ID
2015.1.01528.S, PI I. Smail; Band 8, Prop. ID 2013.1.00749.S, PI D.
Riechers), and SMA (340 GHz, Bussmann et al. 2013). It forms an arc
that splits into two knots on the N side of the lens, an elongated second
image on the S side of the lens, and a third elongated image on the W
side of the lens. This system was studied in detail by Bussmann et al.
(2013) and Bussmann et al. (2015), who modelled the ALMA band
6 and SMA observations, respectively. They measured an Einstein
radius of _𝜃_ E = 0 _._ 44 ± 0 _._ 02 arcsec and _𝜃_ E = 0 _._ 507 ± 0 _._ 004 arcsec,
respectively. No _HST_ counterpart is found after subtracting the lens.
**HERMESJ033211** − **270536 (HECDFS04; S_51)** : We model this
type 1 foreground lens with one PSF using `GASP2D` . The background
lensed source is detected by ALMA (Band 7, Bussmann et al. 2015).
It forms an arc and a faint secondary image on the S and the NW
sides of the lens, respectively. This system was studied in detail by
Bussmann et al. (2015), who measured an Einstein radius of _𝜃_ E = 0 _._ 5

arcsec.

**HERMESJ044154** − **540352** **(HADFS01;** **S_52)** : We model this
type 1 foreground lens with one Sérsic component using `GASP2D` .
The background lensed source was detected by ALMA (Band 7,
Bussmann et al. 2015). It forms two arcs: one is more extended, splits
into two knots, and is located on the E side of the lens, while the
other is on the W side. This system was studied in detail by Bussmann
et al. (2015), who measured an Einstein radius of _𝜃_ E = 1 _._ 006 ± 0 _._ 004
arcsec. No _HST_ counterpart is found after subtracting the lens.
**HATLASJ083932** − **011760** **(HerBS105;** **S_53)** : The foreground
lens is a type 1 edge-on galaxy, which we model with `ISOFIT` . The
background lensed source is located at _𝑧_ [spec] s = 2 _._ 67 (Cox et al. 2023)
and was detected by ALMA (Band 6, Prop. ID 2018.1.00526.S, PI I.
Oteo). It forms two blended images separated by the disk of the lens.
No _HST_ counterpart is found after subtracting the lens.
**HATLASJ091841** + **023048** 1 _,_ 2 **(HerBS32;** **S_54)** : This type 2
foreground lens is formed by two galaxies which we deblend by
simultaneously modelling them with `GALFIT` using two Sérsic components for first galaxy (labelled as ‘1’ in Fig. A1) and one de Vaucouleurs component for the second one (labelled as ‘2’). The background lensed source at _𝑧_ [spec] s = 2 _._ 58 (Harris et al. 2012) is detected
by ALMA (Band 3, Prop. ID 2017.1.01694.S, PI I. Oteo; and Band
7, Giulietti et al. 2022). It forms an arc on the E side of galaxy 1 and
a secondary image on the W side of galaxy 2. An additional third
ALMA detection is found E of the two galaxies near a _HST_ clump
and shows a faint near-IR counterpart.
**HATLASJ113526** − **014606** **(HerBS10;** **S_55)** : The background
lensed source at _𝑧_ [spec] s = 3 _._ 13 was detected by ALMA (Band 3, 6,
7, and 8, Giulietti et al. 2023). It forms a wide arc on the SE and a
secondary image on the NW. No foreground lens is detected in the


MNRAS **000**, 1–57 (2022)

18 _E. Borsato et al._


near-IR, whereas there is a tentative detection for the background
source. This system was studied in detail by Giulietti et al. (2023),
who measured an Einstein radius of _𝜃_ E = 0 _._ 4241 [+] − [0] 0 _[.]_ _._ [0005] 0005 [arcsec.]
**HATLASJ115433.6** + **005042 (HerBS177; S_56)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 52 (Shirley et al. 2021) with
one Sérsic component using `GASP2D` . The background lensed source
at _𝑧_ [phot] s = 3 _._ 90 (Bakx et al. 2020) is detected by ALMA (Band 7,
Prop. ID 2019.1.01784.S, PI T. Bakx). It forms an arc on the E side
of the lens and a secondary image on the W side. Potential near-IR
counterparts of the background lensed source are visible on the S of
the lens.

**HATLASJ120127.6** − **014043** **(HerBS61;** **S_57)** : We model this
type 1 (or 2) foreground lens at _𝑧_ [phot] l = 0 _._ 88 (Shirley et al. 2021)
with one Sérsic component and one exponential component using
`GASP2D` . The background lensed source at _𝑧_ [phot] s = 4 _._ 06 (ManjónGarcía et al. 2019) is detected by SMA (340 GHz, Enia et al. 2018).
It forms an arc on the NW side of the lens and a bright secondary
image on the SE side. This system was studied in detail by Enia et al.
(2018), who measured an Einstein radius of _𝜃_ E = 0 _._ 82 ± 0 _._ 04 arcsec.
**HATLASJ131611** + **281220** **(HerBS89;** **S_58)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 90 (Berta et al. 2021) with
one Sérsic component using `GASP2D` . The background lensed source
at _𝑧_ [spec] s = 2 _._ 9497 (Neri et al. 2020) was resolved by NOEMA (255
GHz, Berta et al. 2021). It forms an arc on the S side of the lens and a
compact image on the N side. This system was studied and modelled
in detail by Berta et al. (2021), who measured an Einstein radius of
_𝜃_ E = 0 _._ 4832 ± 0 _._ 0006 arcsec. There is a tentative detection of the
background lensed source in _HST_ on the E and W sides of the lens.
**HATLASJ134429** + **303036 (HerBS1; S_59)** : We model this type
1 foreground lens at _𝑧_ [spec] l = 0 _._ 67 (Bussmann et al. 2013) with one
Sérsic component and one exponential component using `GASP2D` .
The background lensed source at _𝑧_ [spec] s = 2 _._ 30 (Harris et al. 2012)
was detected by ALMA (Band 7, Falgarone et al. 2017) and SMA
(340 GHz, Bussmann et al. 2013). It forms an arc on the W side of the
lens and a more distant secondary image on the E side. This system
was studied in detail by Bussmann et al. (2013) with the SMA data.
They measured an Einstein radius of _𝜃_ E = 0 _._ 92 ± 0 _._ 02 arcsec.
**HATLASJ141352** − **000027** 1 _,_ 2 _,_ 3 **(HerBS15;** **S_60)** : This type 3
foreground lens is formed by a cluster of galaxies at _𝑧_ [spec] l = 0 _._ 55
(Bussmann et al. 2013). We model three of the spectroscopically
confirmed members, which are likely contributing to lensing, with
GASP2D using one Sérsic and one exponential component for the
main lens (labelled as ‘1’ in Fig. A1), and one Sérsic component
for the second (labelled as ‘2’) and the third (labelled as ‘3’). The
background lensed source at _𝑧_ [spec] s = 2 _._ 48 (Harris et al. 2012) is
detected by ALMA (Band 3, 6, and 7, Prop. ID, 2018.1.00861.S PI
C. Yang) and forms two arcs, one on the N of the galaxy 3 and the
other on the E side of the galaxy 1. The background lensed source is
only partly detected in _HST_ images.
**HATLASJ142414** + **022304** 1 _,_ 2 **(HerBS13,** **ID** **141;** **S_61)** : This
type 2 foreground lens is formed by two galaxies at _𝑧_ [spec] l = 0 _._ 60
(Bussmann et al. 2012), which we deblend by simultaneously modelling them with `GALFIT` using one Sérsic component and a PSF for
the first galaxy (labelled as ‘1’ in Fig. A1) and one Sérsic component
for the second one (labelled as ‘2’). The background lensed source at
_𝑧_ [spec] s = 4 _._ 24 (Cox et al. 2011) is detected by ALMA (Band 3 and 4,
Dye et al. 2022; Band 5, 6, and 7, Dye et al. 2018; and Band 8 Prop.
ID 2016.1.00284.S, PI J. Bernard-Salas), and SMA (340 GHz, Bussmann et al. 2012; and 880 Ghz, Cox et al. 2011). No _HST_ counterpart
is found after subtracting the lens.
**HERMESJ142826** + **345547 (HBootes02; S_62)** : The foreground


MNRAS **000**, 1–57 (2022)



lens at _𝑧_ [spec] l = 0 _._ 41 (Wardlow et al. 2013) is a type 1 edge-on galaxy
which we model with `ISOFIT` . The background lensed source at
_𝑧_ [spec] s = 2 _._ 41 (Wardlow et al. 2013) was detected by SMA (340 GHz,
Bussmann et al. 2013) and JVLA (7 GHz, Wardlow et al. 2013). It
forms an arc that splits into two knots and is located on the SE side of
the lens, and a fainter secondary image on the NW side of the lens.
No _HST_ counterpart is found after subtracting the lens.
**HATLASJ230815.5** − **343801** **(HerBS28;** **S_63)** : We model this
type 1 foreground lens at _𝑧_ [phot] l = 0 _._ 72 (Ward et al. 2022) with two
Sérsic components using `GASP2D` . The background lensed source
at _𝑧_ [phot] s = 4 _._ 03 (Manjón-García et al. 2019) is detected by ALMA
(Band 6, Prop. ID 2018.1.00526.S, PI I. Oteo). It forms an arc that
splits into two knots and is located on the N side of the lens and a
secondary image on the W side of the lens. No _HST_ counterpart is
found after subtracting the lens.
**HELMSJ232439.5** − **043936** **(HELMS7;** **S_64)** : We model this
type 1 foreground lens with two Sérsic components using `GASP2D` .
The background lensed source at _𝑧_ [spec] s = 2 _._ 47 (Nayyeri et al. 2016)
is detected by ALMA (Band 6, Amvrosiadis et al. 2018; and 7, Prop.
ID 2017.1.00027.S, PI S. Eales). It forms three arcs, two of them
are located close to the lens on its W and E sides, whereas the third
arc is near an _HST_ clump on the E side of the lens. This kind of
morphology is indicative of the presence of multiple lenses, which
possibly are the _HST_ clump and a further clump one on the NW side
of the main lens. This system was studied in detail by Maresca et al.
(2022), who adopted two lenses and measured their Einstein radii to
be _𝜃_ E = 0 _._ 54 ± 0 _._ 01 arcsec and _𝜃_ E = 0 _._ 40 ± 0 _._ 01 arcsec, respectively.
At the position of the second lens, there is no _HST_ detection.
**HELMSJ233620.8** − **060828** **(HELMS6;** **S_65)** : We model this
type 1 foreground lens at _𝑧_ [spec] l = 0 _._ 40 (Nayyeri et al. 2016) with two
Sérsic components using `GASP2D` . The lens is also part of the cluster
that hosts other strong lensing events (see Carrasco et al. 2017 for
details). The background lensed source at _𝑧_ [spec] s = 3 _._ 43 (Nayyeri et al.
2016) was detected by ALMA (Band 6, Prop. ID 2021.1.01116.S,
PI D. Riechers and Amvrosiadis et al. 2018; and Band 8, Prop. ID
2013.1.00749.S, PI D. Riechers). It forms four images: two of them
are on the S side of the lens and are connected by an arc, a third
one is on the W side, and a fourth one is on the NE side. Near-IR
counterparts of the background lensed source are visible only for the
S images.


_4.3.4_ _Uncertain lenses_


**HATLASJ013840.5** − **281855** **(HerBS14;** **S_81** ): It is unclear
whether this source at _𝑧_ [spec] = 3 _._ 78 (Urquhart et al. 2022) is strongly
lensed. It was detected by ALMA (Band 6, Prop. ID 2018.1.00526.S,
PI I. Oteo) and shows one elongated component. Due to the ∼ 0 _._ 6 arcsec resolution, it is not possible to exclude the presence of background
lensed sources with very low angular separation. The candidate lens
is an edge-on spiral galaxy at _𝑧_ [phot] = 0 _._ 61 ± 0 _._ 28 (Ward et al. 2022).
**HERMESJ022017** − **060143** 1 _,_ 2 **(HXMM01;** **S_85)** : This system
is confirmed to be a DSFG pair that is weakly lensed by a pair of
foreground galaxies. This type 3 foreground system is formed by
an edge-on disk galaxy (labelled as ‘1’ in Fig. A1) at _𝑧_ [phot] l = 0 _._ 87
(Nayyeri et al. 2016) and a second rounder and ringed galaxy (labelled
as ‘2’). The sources at _𝑧_ [phot] s = 0 _._ 87 (Fu et al. 2012) were detected by
ALMA (Band 6, Bussmann et al. 2015 and Prop. ID 2015.1.00723.S,
PI I. Oteo; Band 7, Prop. ID 2011.0.00539.S, PI D. Riechers), SMA
(340 GHz Fu et al. 2012), and JVLA (30 GHz Fu et al. 2012) in
the sub-mm/mm and by Keck/NIRC2 AO ( _K_ _𝑠_ Fu et al. 2012) in the

near-IR. The background sources are located between the two lenses,
one on the S side of them and the other on the N side.

**HERMESJ022135** − **062617** **(HXMM03;** **S_88)** : It is unclear
whether this background source at _𝑧_ [spec] s = 2 _._ 72 (Bussmann et al.
2015) is strongly lensed. Wemodelthe brightestcluster galaxy (BCG)
of a candidate lensing cluster at _𝑧_ [spec] l = 0 _._ 31 (Albareti et al. 2017)
with two Sérsic components using `GASP2D` . The source was detected
by ALMA (Band 7, Bussmann et al. 2015). It forms a bright arc and
is located on the E side of the lens. No secondary image was picked
up by ALMA. Unfortunately, the W side of the candidate lens, where
the counter image is expected to be found, is outside the ALMA
Band 7 FOV. A near-IR counterpart of the ALMA arc is clearly visible and shows a complex morphology with multiple knots, while
the secondary image is not found even after subtracting the potential
lens. One possibility is that the source is only weakly lensed by the
foreground structure.
**HERMESJ045058** − **531654 (HADFS03; S_91)** : This system was
proposed to be a group of three weakly lensed DSFGs by a foreground
edge-on disk galaxy (Bussmann et al. 2015). It was detected by
ALMA (Band 7, Bussmann et al. 2015) and forms three compact
clumps near the candidate lens. All the ALMA clumps are on the S
on the candidate lens and, as such, are not consistent with the usual
strong lensing morphology.
**HERMESJ143331** + **345440** **(HBootes01;** **S_116)** : It is unclear
whether this background source at _𝑧_ [spec] = 3 _._ 27 (Wardlow et al. 2013)
is strongly lensed. It was detected by SMA (340 GHz, Bussmann
et al. 2013), and shows one elongated component. Due to the ∼
0 _._ 6 arcsec resolution, it is not possible to exclude the presence of
background lensed sources with very low angular separation. We
model the candidate lensing system at _𝑧_ [phot] = 0 _._ 59 with one Sérsic

component.
**HELMSJ235331.7** + **031717** **(HELMS40;** **S_139)** : It is unclear
whether this source located at _𝑧_ [spec] s = (Cox et al. 2023) is strongly
lensed. The source was detected by ALMA (Band 7, Amvrosiadis
et al. 2018). It forms two pairs of compact sources. The first pair
(on the SE side of the cutout) shows a possible near-IR detection but
no foreground lens candidate. The members of the second pair are
located on the N and S sides of a possible lensing galaxy, respectively,
and they do not show any _HST_ counterpart. We model the candidate
lensing system with two Sérsic components and a Gaussian using
`GALFIT` to account for the different locations of their centres. This
system was studied in detail by Maresca et al. (2022), who modelled
the SE pair and measured an Einstein radius of _𝜃_ E = 0 _._ 21 ± 0 _._ 01
arcsec. We note that the lens redshift adopted by Maresca et al.
(2022) is likely associated with a close-by spiral galaxy on these
sides of the SE pair.
**HATLASJ011014.5** − **314813** **(HerBS160;** **S_153)** : It is unclear
whether this background source at _𝑧_ [spec] = 3 _._ 96 (Urquhart et al.
2022) is strongly lensed. It is detected by ALMA (Band 6, Prop. ID
2018.1.00526.S, PI I. Oteo) and forms an elongated, arc-like structure
near a faint _HST_ counterpart. We find no secondary image.
**HERMESJ023006** − **034153** **(HXMM12;** **S_170)** : This system
was proposed to be a weakly lensed DSFG by a group of foreground
galaxies (Bussmann et al. 2015). It was detected by ALMA (Band
7, Bussmann et al. 2015) and forms an arc-like structure near a faint
_HST_ counterpart. We find no secondary image.
**HERMESJ043341** − **540338** **(HADFS04;** **S_175)** : This system
was proposed to be a system of three DSFGs that is weakly lensed
by a foreground group of galaxies (Bussmann et al. 2015). It was
detected by ALMA in (Band 7, Bussmann et al. 2015), the two DSFGs are located on the SE and NE sides of the foreground galaxy.
This system was studied in detail by Bussmann et al. (2015), who



_Characterisation of HST confirmed lenses_ 19


assumed an Einstein radius of 0.5 arcsec. A near-IR counterpart of
the ALMA southernmost source is visible.

**HATLASJ144556.1** − **004853** **(HERBS46;** **S_249)** : It is unclear
whether this background source is strongly lensed. It was detected
by SMA (340 GHz, Bussmann et al. 2013), and shows one elongated
component near a faint _HST_ counterpart. Due to the ∼ 0 _._ 6 arcsec
resolution, it is not possible to exclude the presence of background
lensed sources with very low angular separation.
**HATLASJ224207.2** − **324159** **(HerBS67;** **S_262)** : It is unclear
whether this background source at _𝑧_ [phot] = 3 _._ 57 (Bakx et al. 2018)
is strongly lensed. It was detected by ALMA (Band 6, Prop. ID
2018.1.00526.S, PI I. Oteo) and shows one elongated component.
Due to the ∼ 0 _._ 6 arcsec resolution, it is not possible to exclude
the presence of background lensed sources with very low angular
separation.


**4.4** **Properties of the lenses**


Since ∼ 47% of the modelled lensing galaxies are composed of
multiple components, it is necessary to use a set of parameters that
describes the global properties of the surface brightness distribution
and does not depend on the number and type of components used
to model the galaxy. We therefore use the total effective radius _𝑅_ 50
(i.e., the radius and surface brightness of the circularised isophote
that contains half of the light of the galaxy), total effective surface
brightness _𝜇_ 50, and total magnitude _𝑚_ _𝐹_ 110 _𝑊_ . For each galaxy, we
sampled 10 [4] different combinations of its components to take into
account the uncertainties of the best-fitting model of the surface
brightness distribution. This is done through a set of truncated normal distributions (one for each component parameter) with central
value being the best-fitting value from the surface brightness model,
standard deviation the uncertainty of the best-fitting value, and ranges

[0 _,_ ∞) ADU pixel [−][1], [0 _,_ ∞) pixel, [0 _._ 3 _,_ 10], [0 _,_ 1], and [0 _,_ 360] deg
for _𝜇_ e, _𝑅_ e, _𝑛_, _𝑞_, and PA, respectively. For all the combinations, we
estimate _𝑅_ 50 by computing the curve of growth (COG) and retrieving
the radius within which half of the total flux is encircled. The _𝜇_ 50
value is derived from the surface brightness profile at _𝑅_ 50, while the
_𝑚_ _𝐹_ 110 _𝑊_ value is obtained by summing the luminosities of all the
components. For each parameter, we calculate the median and the
16% and 84% percentiles from the cumulative distribution function.
Additionally, we estimate the _𝐶_ 31 = _𝑅_ 75 / _𝑅_ 25 concentration index
(e.g. Watkins et al. 2022) in order to compare our results with the
literature. To derive the distributions of _𝑅_ 25 and _𝑅_ 75, which correspond to the radii containing 25% and 75% of the total luminosity,
respectively, we apply the same procedure as done for _𝑅_ 50 .
For the edge-on lenses of S_5, S_46, S_53, and S_62, we run
`ISOFIT` on the model image (Fig. 8) after having deconvolved it
with the PSF, and then we use the result to produce the COG. We
also measure the surface brightness radial profile. We use the COG
to estimate the values of _𝑅_ 25, _𝑅_ 50, and _𝑅_ 75 and to assess their
uncertainties, we build a set of 10 [4] COGs for each galaxy. We sample
the flux within each circularised radius with a Gaussian distribution
centred on the measured flux value and with standard deviation being
the flux Poisson uncertainty. The circularised radius is sampled with
a Gaussian distribution centred on the measured radius value and

with standard deviation being the uncertainty on the ellipticity as
measured by `ISOFIT` . We use the surface radial profile to estimate
the values of _𝜇_ 50, and to assess its uncertainty, we build a set of 10 [4]

surface brightness radial profiles. At each radius, we adopt a Gaussian
distribution centred on the measured value of surface brightness, with
standard deviation being the uncertainty measured by `ISOFIT` .
In Fig. 9, we show the _𝐶_ 31 distribution of our lenses. The peak at


MNRAS **000**, 1–57 (2022)

20 _E. Borsato et al._







40


30


20


10


0

35


30


25


20


15


10


5


0


80


60


40


20


0

30


25


20


15


10


5









14


12


10


8


6


4


2


0






|Col1|HERMESJ100144+025709/HC<br>1arcsec|HERMESJ100144+025709/HC|OSMOS01/No|1arcsec|ALMA band 7<br>1arcsec|3<br>0<br>3<br>3<br>0<br>3<br>3<br>0<br>3<br>3<br>0<br>3<br>3<br>0<br>3|
|---|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ083051+013225/He|HATLASJ083051+013225/He|rBS4/No. S_11|1 arcsec|1 arcsec<br>ALMA band 4|1 arcsec<br>ALMA band 4|
||1 arcsec<br>HERSJ020941.2+001558/Her|HERSJ020941.2+001558/Her|S1/No. S_8<br>1<br>2<br>1 arcsec|1 arcsec|1 arcsec<br>ALMA band 8|1 arcsec<br>ALMA band 8|
||1 arcsec<br>HELMSJ005841.2<br>011149/He|1 arcsec<br>HELMSJ005841.2<br>011149/He|LMS23/No. S_5<br>1 arcsec|1 arcsec|1 arcsec|1 arcsec|
||1 arcsec<br>HERMESJ021831<br>053131/HX|HERMESJ021831<br>053131/HX|MM02/No. S_|1 arcsec|1 arcsec<br>ALMA band 8|1 arcsec<br>ALMA band 8|



**Figure 8.** _From left to right panels:_ Observed _F110W HST_ image, best-fitting lens model, residual, and SNR residual map of five representative lensing systems:
one for each type plus a confirmed one by multiwavelength data only. The remaining sample systems are shown in Fig. A1). The best-fitting lens model and
residual images result from the surface brightness modelling, while the SNR map is the ratio between the residual image and noise map. The contours in the
model images are taken at two levels corresponding to _SNR_ = 5 and 10 (thick curves), and five uniformly spaced levels between the _SNR_ = 10 and the maximum
SNR in the model image (thin curves). The residual map shows the pixel mask (corresponding to the black-shaded regions) adopted for the surface brightness
modelling. The residual maps show the contours of available high-resolution multiwavelength data taken at two levels corresponding to _SNR_ = 5 and 10 (thick
curves), and five uniformly spaced levels between the _SNR_ = 10 and the maximum SNR in the multiwavelength image (thin black curves). The images are
oriented such that N is up and E is to the left.


MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 21


**Table 5.** Structural parameters of four representative confirmed lensing systems obtained from a parametric fit of their surface brightness distributions.


No. IAU Name Type Components _𝜇_ e _𝑅_ e _𝑛_ _𝑞_ _𝑃𝐴_ _𝑚_ PSF _𝐶_ / _𝑇_ _𝜒_ [2] _𝑁_ dof

[mag arcsec [−][2] ] [arcsec] [deg] [mag]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13)


S_12 HERMESJ100144 + 025709 1 Sérsic 21 _._ 74 ± 0 _._ 05 0 _._ 82 ± 0 _._ 02 5 _._ 35 [+] − [0] 0 _[.]_ _._ [11] 10 0 _._ 606 ± 0 _._ 005 71 _._ 89 [+] − [0] 0 _[.]_ _._ [73] 76 – [1] 1.05 43906


HATLASJ083051 + 013225 1 Sérsic 22 _._ 60 [+] − [0] 0 _[.]_ _._ [13] 12 0 _._ 36 ± 0 _._ 02 4 _._ 86 ± 0 _._ 36 0 _._ 84 ± 0 _._ 01 33 _._ 02 [+] − [1] 1 _[.]_ _._ [44] 45 – [1]
S_11 2 1.04 32063

HATLASJ083051 + 013225 2 Sérsic 23 _._ 28 [+] − [0] 0 _[.]_ _._ [15] 13 0 _._ 69 ± 0 _._ 04 1 _._ 34 [+] − [0] 0 _[.]_ _._ [13] 12 0 _._ 48 ± 0 _._ 02 22 _._ 24 [+] − [1] 1 _[.]_ _._ [87] 83 – [1]



HERSJ020941.2 + 001558 1

S_8 3



Sérsic 21 _._ 13 [+] − [0] 0 _[.]_ _._ [19] 16 1 _._ 54 ± 0 _._ 18 5 _._ 11 ± 0 _._ 23 0 _._ 916 ± 0 _._ 004 82 _._ 42 [+] − [0] 0 _[.]_ _._ [93] 99 – 0 _._ 56 [+] − [0] 0 _[.]_ _._ [07] 08
Sérsic 23 _._ 16 [+] − [0] 0 _[.]_ _._ [13] 12 5 _._ 03 ± 0 _._ 13 0 _._ 75 [+] − [0] 0 _[.]_ _._ [07] 06 0 _._ 75 ± 0 _._ 02 81 _._ 91 [+] − [1] 1 _[.]_ _._ [29] 26 – 0 _._ 31 [+] − [0] 0 _[.]_ _._ [06] 05 0.97 121439
Sérsic 22 _._ 28 [+] − [0] 0 _[.]_ _._ [15] 13 2 _._ 10 [+] − [0] 0 _[.]_ _._ [06] 07 0 _._ 47 ± 0 _._ 04 0 _._ 92 ± 0 _._ 02 66 _._ 03 [+] − [3] 3 _[.]_ _._ [11] 18 – 0 _._ 13 [+] − [0] 0 _[.]_ _._ [03] 02



HERSJ020941.2 + 001558 2 Sérsic 20 _._ 49 ± 0 _._ 06 0 _._ 315 [+] − [0] 0 _[.]_ _._ [010] 009 2 _._ 86 ± 0 _._ 07 0 _._ 969 ± 0 _._ 007 156 _._ 46 [+] − [0] 0 _[.]_ _._ [93] 92 – [1] 0.97 124612


S_50 HERMESJ021831 − 053131 1 Sérsic 23 _._ 60 [+] − [0] 0 _[.]_ _._ [13] 12 0 _._ 83 ± 0 _._ 05 5 _._ 12 ± 0 _._ 38 0 _._ 38 ± 0 _._ 01 148 _._ 55 [+] − [1] 1 _[.]_ _._ [47] 43 – [1] 1.07 49835


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the _Herschel_ detection. Indices 1 and 2 refer to the two components of the lens candidate.
Col. (3): Type of the system. Col. (4): Adopted model for the lens component. Col. (5): Effective surface brightness (i.e., the surface brightness at the effective
radius). Col. (6): Effective radius (i.e., the semi-major axis of the isophote containing half of the light of the component). Col. (7): Sérsic index. Col. (8): Axis
ratio. Col. (9): Position angle. Col. (10): Total magnitude of the unresolved component. Col. (11): Luminosity ratio of the component with respect to the galaxy.
Col. (12): Reduced _𝜒_ [2] of the fit. Col. (13): Number of degrees of freedom of the fit. The values in brackets are left fixed in the fit.



_𝐶_ 31 ≃ 7 is due to the systems that we model with a de Vaucouleurs
profile and have all the same concentration. We measure a median
⟨ _𝐶_ 31 ⟩ = 6 _._ 8 ± 0 _._ 4, which is slightly higher than the median value
⟨ _𝐶_ 31 ⟩ = 5 _._ 2 ± 0 _._ 1 measured by Watkins et al. (2022) for a sample of
nearby ETGs observed with _Spitzer_ at 3.6 _𝜇_ m. This finding and the
observed morphology of smooth and featureless elliptical systems
provide further evidence that our lenses are mostly ETGs. Lastly, we
measure the flux densities at 1.1 _𝜇_ m _𝑆_ 1 _._ 1 of the background sources
by taking the aperture photometry in the regions dominated by the
lensing features on the lens subtracted residuals. The uncertainties
_𝜎_ _𝑆_ 1 _._ 1 are computed with _𝜎_ _𝑆_ [2] 1 _._ 1 [=] [�] _𝑖, 𝑗_ _[𝜎]_ _𝑖, 𝑗_ [2] [,] [where] _[𝜎]_ _[𝑖, 𝑗]_ [is] [the] [noise]
map. The values of _𝑆_ 1 _._ 1 and their uncertainties are given in Tables 6
and A2.


For the 68 lensing foreground galaxies with known photometric or
spectroscopic redshift, we convert the size of the total effective radius
from arcsec to kpc through the angular diameter distance and the total
magnitude to absolute magnitude _𝑀_ _𝐹_ 110 _𝑊_ through the luminosity
distance. We also correct the total effective surface brightness for
cosmological dimming by multiplying the _F110W_ fluxes by a factor
of (1 + _𝑧_ ) [4] . This is done for the parameter distributions as derived
before. To take into account the uncertainties on the photometric
redshifts, we sample a truncated normal distribution centred on the
redshift measurement, with standard deviation being the uncertainty
and range [0 _,_ ∞). When more than one potential lens is present (i.e.
for type 2 and 3 systems), we correct for the redshift only if the secondary potential lens has a spectroscopic redshift (S_8, S_11, S_15,
and S_36) or none of the lenses dominates the available photometric
redshift (S_23, S_28, and S_33). To denote the parameters corrected
for the lens redshifts, we add a subscript ‘0’. In Table 6, we list the
measured values of _𝑚_ _𝐹_ 110 _𝑊_, _𝑀_ _𝐹_ 110 _𝑊_, _𝑅_ 50, _𝑅_ 50 _,_ 0, _𝜇_ 50, _𝜇_ 50 _,_ 0, and
_𝐶_ 31 for the five representative systems shown in Fig. 8, while in
Table A2 we show the parameters for the rest of the sample.


Figure 9 shows the distribution of _𝑅_ 50 _,_ 0 in kpc, _𝜇_ 50 _,_ 0 in mag
arcsec [−][2], _𝐶_ 31, _𝑀_ _𝐹_ 110 _𝑊_ in mag, _𝑧_ l and _𝑧_ s . For each parameter, we
stack all the single-system parameter distributions to take into account the varying uncertainties between different systems. We bin
them together and normalised for the total number of realisations
(i.e., 10 [4] for each system).



**Table 6.** Derived properties of five representative lensing systems.


No. IAU Name _𝑚_ _𝐹_ 110 _𝑊_ _𝜇_ 50 _𝑅_ 50 _𝐶_ 31 _𝜇𝑆_ 1 _._ 1

[mag] [mag arcsec [−][2] ] [arcsec] [ _𝜇_ Jy]
_𝑀_ _𝐹_ 110 _𝑊_ _𝜇_ 50 _,_ 0 _𝑅_ 50 _,_ 0

[mag] [mag kpc [−][2] ] [kcp]
(1) (2) (3) (4) (5) (6) (7)

S_12 HERMESJ100144 + 025709 −1920 _._ 17 _._ 17 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [08] _[.]_ 08 _._ [08] 08 2118 _.._ 7496 [+][+] −− [0][0] 00 _[.][.]_ _.._ [05][05] 0505 05 _.._ 6410 [+][+] −− [0][0] 00 _[.][.]_ _.._ [02][13] 0213 9 _._ 37 [+] − [0] 0 _[.]_ _._ [20] 20 [10] _[.]_ [14] [+] − [0] 0 _[.]_ _._ [17] 17

S_11 HATLASJ083051HATLASJ083051 ++ 013225013225 12 −−21221617 _.._ 5405 _.._ 8659 [+][+] −− [+][+] −− [0][0] 00 [0][0] _[.][.]_ 00 _.._ [18][21] _[.][.]_ 1819 _.._ [18][21] 1820 22202320 _...._ 60482827 [+][+][+][+] −−−− [0][0][0][0] 0000 _[.][.][.][.]_ _...._ [13][15][13][15] 12121313 0203 _...._ 30943348 [+][+][+][+] −−−− [0][0][0][0] 0000 _[.][.][.][.]_ _...._ [02][13][03][26] 02130325 83 _.._ 4721 [+][+] −− [0][0] 00 _[.][.]_ _.._ [66][16] 6415 6 _._ 79 +−00 _.._ 1111

S_8 HERSJ020941.2 + 001558 1 −1619 _._ 15 _._ 38 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [18] _[.]_ 17 _._ [18] 17 2120 _.._ 2747 [+][+] −− [0][0] 00 _[.][.]_ _.._ [19][19] 1717 28 _.._ 4847 [+][+] −− [0][0] 00 _[.][.]_ _.._ [13][46] 1240 5 _._ 35 [+] − [0] 0 _[.]_ _._ [45] 47 18 _._ 72 +−00 _.._ 3434

HERSJ020941.2 + 001558 2 −1915 _._ 82 _._ 71 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [09] _[.]_ 09 _._ [09] 09 2019 _.._ 4969 [+][+] −− [0][0] 00 _[.][.]_ _.._ [06][06] 0606 01 _._ 310 _._ 06 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [03][010] 03009 5 _._ 24 [+] − [0] 0 _[.]_ _._ [10] 10

S_5 HELMSJ005841.2 − 011149 [18] −18 _[.]_ [910] _._ 15 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [001] _[.]_ 001 _._ [57] 48 2018 _.._ 2688 [+][+] −− [0][0] 00 _[.][.]_ _.._ [25][02] 0224 02 _._ 478 _._ 54 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [31][005] 35006 3 _._ 05 [+] − [0] 0 _[.]_ _._ [04] 04 [14] _[.]_ [55] [+] − [0] 0 _[.]_ _._ [10] 10

S_50 HERMESJ021831 − 053131 −2118 _._ 55 _._ 89 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [19] _[.]_ 18 _._ [19] 18 2319 _.._ 6089 [+][+] −− [0][0] 00 _[.][.]_ _.._ [13][13] 1212 04 _.._ 4051 [+][+] −− [0][0] 00 _[.][.]_ _.._ [03][27] 0326 8 _._ 95 [+] − [0] 0 _[.]_ _._ [71] 69 _<_ 0 _._ 04


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the
_Herschel_ detection. Indices 1 and 2 refer to the two components of the lens
candidate. Col. (3): Apparent magnitude of the model (first row), absolute
magnitude of the model (second row). Col. (4): Total effective radius in
arcsec (first row) and in kpc (second row). Col. (5): Total effective surface
brightness before (first row) and after correcting for cosmological dimming
(second row). Col. (6): Concentration index of the model.


**5** **LENS MODELLING**


For the 34 systems for which we can confidently identify a galaxy
acting as the main lens and the background source in the _HST_ images, we proceed to estimate the Einstein radius _𝜃_ _𝐸_ from the residual
images. Depending on the morphology of the lensing features, we
define _𝜃_ E as either the radius of the circle centred on the lens that
best fits the Einstein ring (e.g., S_4), or as half of the separation
between the multiple images (e.g., S_2) following the approach of


MNRAS **000**, 1–57 (2022)

22 _E. Borsato et al._



5 10 15

C 31


1 2 3 4 5

z s



14

12

10

8

6

4

2

0


10


8


6


4


2


0



0 5 10 15 20

R 50, 0 [kpc]


20 18 16 14

M [mag]



18 20 22


50, 0 [ [mag arcsec] 2 ]


0.5 1.0 1.5

z l



8


6


4


2


0


12

10

8

6

4

2

0



16

14
12
10
8
6

4
2
0


12

10

8

6

4

2

0



**Figure 9.** Distribution of the total effective radii _𝑅_ 50 _,_ 0 (top left panel), total effective surface brightnesses _𝜇_ 50 _,_ 0 (top central panel), concentrations _𝐶_ 31 (top right
panel), total absolute magnitudes _𝑀_ _𝐹_ 110 _𝑊_ (bottom left panel), redshifts _𝑧_ l of the foreground lenses (bottom central panel), and redshifts _𝑧_ s of the background
sources (bottom right panel). All the foreground lenses and background sources with a measured redshift are included. The orange line corresponds to the
median of the values of _𝐶_ 31 of the ETGs sample of Watkins et al. (2022), while the orange shaded region marks the corresponding ±1 _𝜎_ confidence interval.



Amvrosiadis et al. (2018). For the uncertainty on _𝜃_ E, we adopt the
value corresponding to one-third of the observed width of the lensing feature. We use these rough estimates as priors for proper lens
modelling.
The lens modelling is performed with `PyAutoLens` [11] (Nightingale
et al. 2018, 2021), by using a non-linear search trough `dynesty`
(Speagle 2020) [12] . In order to reduce the complexity of the lens model,
we adopt a singular isothermal ellipsoid (SIE) for the mass model
(see Nightingale et al. 2018 for details). It has five free parameters,
the differences _𝛿𝑥_ SIE and _𝛿𝑦_ SIE of the centre coordinates of the mass
distribution relative to the centre coordinates of the lens surface

brightness, Einstein radius _𝜃_ E, and elliptical components _𝜖_ SIE _,_ 1 =
_𝑓_ SIE sin(2 _𝑃𝐴_ SIE ), _𝜖_ SIE _,_ 2 = _𝑓_ SIE cos(2 _𝑃𝐴_ SIE ), where _𝑓_ SIE = (1 −
_𝑞_ SIE )/(1 + _𝑞_ SIE ), _𝑃𝐴_ SIE is the position angle of the mass profile,
and _𝑞_ SIE is its flattening.
From the lens-subtracted images and noise maps as obtained in
Sec. 4, we set up the inputs for the lens modelling. We crop the
images and we mask the regions that do not include lensing features
in order to reduce the computation time. To this aim we also crop the
PSF to ∼ 5 FWHM × 5 FWHM cutouts. We then mask any residual
from the lens subtraction and non-modelled nearby contaminants. We
estimate the position of the lensing features by locating the brightest
pixel in 5 pixel × 5 pixel boxes encompassing the lensing features.
These estimates are used by `PyAutoLens` to constrain the location
of the background source in the source plane (see Nightingale et al.
2018 for details).
We proceed with the lens modelling with the following approach.
First, we perform a parametric fit by fitting both the mass model and
background source with parametric functions. We use a single Sérsic
component for the parametric background source. This fit has a total
of twelve free parameters: five for the mass model and seven for the
background source. The priors for the mass model are a Gaussian
distribution centred on the cutout centre with _𝜎_ = 0 _._ 1 arcsec for _𝛿𝑥_ SIE
and _𝛿𝑦_ SIE ; a Gaussian distribution centred on the estimated _𝜃_ E with


11 `PyAutoLens` is available from `[https://github.com/Jammy2211/](https://github.com/Jammy2211/PyAutoLens)`

```
PyAutoLens
```

12 `dynesty` is available from `[https://dynesty.readthedocs.io/en/](https://dynesty.readthedocs.io/en/stable/)`

```
stable/

```

MNRAS **000**, 1–57 (2022)



_𝜎_ three times its error; a Gaussian distribution centred on 0 with _𝜎_ =
0 _._ 3 for _𝜖_ SIE _,_ 1 and _𝜖_ SIE _,_ 2, respectively. The priors for the background
source are Gaussian distribution centred on the cutout centre with

_𝜎_ = 0 _._ 3 arcsec for _𝑥_ s and _𝑦_ s ; a log-uniform distribution between
10 [−][6] ADU and 10 [6] ADU for _𝐼_ s _,_ eff ; a uniform distribution between 0
arcsec and 30 arcsec for _𝑅_ s _,_ eff ; a uniform distribution between 0.8 and
5.0 for _𝑛_ s ; a Gaussian distribution centred on 0 with _𝜎_ = 0 _._ 3 for _𝜖_ s _,_ 1
and _𝜖_ s _,_ 2 (defined in a similar way as _𝜖_ SIE _,_ 1 and _𝜖_ SIE _,_ 2 ), respectively.
As position threshold, we use a Gaussian distribution centred on the
previously identified position with _𝜎_ = 0 _._ 5 arcsec for all the systems,
except for S_41. For the latter, we adopt _𝜎_ = 0 _._ 1 due to the small
angular separation of the lensed images. We then use the posteriors
of the mass model obtained in this parametric fit and the priors on the
position of the background sources on the image plane to initialize a
Voronoi pixelization with a constant regularization coefficient _𝜆_ (see
Nightingale et al. 2018 for details). For the pixelization, we use as
priors a uniform distribution between 20 and 45 pixels for the shape
of the pixelization and a log-uniform distribution between 10 [−][6] and
10 [6] for _𝜆_ . We do this pixelized initialization fit by marginalizing the
lens model over the mass model and only fitting the pixelization. In
a similar fashion, we marginalize over the resulting pixelization to fit
the mass model with priors defined by the parametric fit posteriors.
We consider this fit as the best guess for the lens model and source
reconstruction.

In the cases of S_6, S_11, S_22, S_24, S_27, and S_31 the SNR of
the background lensed sources is not high enough to produce reliable
results. S_2, S_5, S_25, and S_41 show very complex and/or clumpy
lensed background source morphologies that needed additional information on what is part of the background source or additional
multiple images. Whereas, S_26 shows residuals related to the lens
subtraction that prevent us from building the model. For S_3, S_19,
S_40, the SIE mass model is not sufficient to correctly reproduce
the observations, so we add a shear component, defined, as for the
mass model, through the elliptical components _𝜖_ shear _,_ 1 and _𝜖_ shear _,_ 2 .
This is done to improve the mass model and not to model an actual
external shear (see Etherington et al. 2023 for details). The priors for
the shear elliptical components are uniform distributions between
−0 _._ 2 and 0 _._ 2.

For each modelled lens, we extract 500 fits from the lens modelling
parameters posteriors, and, for each fit, we compute the regions of

the source plane with _SNR_ _>_ 3. We compute the magnification by
taking the ratio between the fluxes of the regions on the source plane
and the image plane after mapping them back. We measure the sizes
of the source plane by computing the radii of the circularised regions
that we used to compute the magnifications. The distribution of the
physical sizes of our systems is shown in Fig. 10. As before, the
results of the lens modelling for S_7 are shown in Fig. 11, while the
results for the remaining lenses are reported in Table 7 and Fig. C1.



_Characterisation of HST confirmed lenses_ 23


MNRAS **000**, 1–57 (2022)

**Table 7.** Results of the lens modelling.


No. IAU name _𝛿𝑥_ _𝛿𝑦_ _𝜃_ _𝐸_ _𝑞_ _𝑃𝐴_ _𝜖_ _𝑠ℎ𝑒𝑎𝑟,_ 1 _𝜖_ _𝑠ℎ𝑒𝑎𝑟,_ 2 _𝑥_ pix _𝑦_ pix _𝜆_ _𝜇_ _𝑅_ bkg _,_ circ _𝜅_ 0

[arcsec] [arcsec] [arcsec] [arcsec] []
_𝛿𝑥_ 0 _𝛿𝑦_ 0 _𝜃_ _𝐸,_ 0 _𝑅_ bkg _,_ circ _,_ 0 _𝑀_ _𝑀_ / _𝐿_

[kpc] [kpc] [kpc] [kpc] [ 10 [11] M ⊙ ]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14) (15) (16)

S_1 HATLASJ000330.6 − 321136 −−00 _.._ 6513 [+][+] −− [0][0] 00 _[.][.]_ _.._ [19][03] 1602 −−00 _.._ 2405 [+][+] −− [0][0] 00 _[.][.]_ _.._ [08][01] 1202 03 _._ 733 _._ 85 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [61][006] 85009 0 _._ 85 ± 0 _._ 03 80 _._ 11 [+] − [3] 10 _[.]_ [78] _._ 85 – – 39 [+] − [3] 9 33 [+] − [8] 7 0 _._ 0101 [+] − [0] 0 _[.]_ _._ [0011] 0009 5 _._ 48 [+] − [0] 0 _[.]_ _._ [62] 48 00 _._ 052 _._ 41 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [04][006] 03004 01 _.._ 9268 [+][+] −− [0][0] 00 _[.][.]_ _.._ [23][03] 2804 2 _._ 93 – [+] − [1] 0 _[.]_ _._ [65] 98

S_3 HELMSJ001353.5 − 060200 −−00 _._ 038 _._ 26 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [05][004] 04003 00 _._ 066 _._ 45 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [07][004] 08006 04 _._ 658 _._ 56 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [50][004] 74003 0 _._ 85 [+] − [0] 0 _[.]_ _._ [03] 04 −49 _._ 56 [+] − [8] 8 _[.]_ _._ [51] 32 [0] _[.]_ [017] [+] − [0] 0 _[.]_ _._ [008] 010 0 _._ 191 ± 0 _._ 009 40 ± 4 31 ± 9 0 _._ 0084 ± 0 _._ 0006 10 _._ 37 [+] − [0] 0 _[.]_ _._ [47] 56 00 _._ 052 _._ 45 ± ± 0 0 _.._ 02002 11 _.._ 4849 [+][+] −− [0][0] 00 _[.][.]_ _.._ [52][02] 4401 4 _._ 19 – [+] − [3] 1 _[.]_ _._ [00] 48

S_4 HELMSJ003619.8 + 002420 −−00 _.._ 015063 [+][+] −− [0][0] 00 _[.][.]_ _.._ [002][007] 001005 00 _.._ 122504 [+][+] −− [0][0] 00 _[.][.]_ _.._ [001][006] 002008 17 _._ 9349 _._ 977 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [007][0017] 0040008 0 _._ 813 [+] − [0] 0 _[.]_ _._ [001] 003 −79 _._ 38 [+] − [0] 0 _[.]_ _._ [23] 21 – – 36 40 0 _._ 01641 _._ 25 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [06][0009] 070008 5 _._ 15234 _._ 82 ± [+] − 0 [1] 0 _[.]_ _._ _._ [23] 72 001 03 _._ 143 _._ 40 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [68][006] 54008 12 _._ 16 ± 0 _._ 3 –

S_7 HERSJ012620.5 + 012950 −−00 _._ 006 _._ 04 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [08][015] 04007 00 _.._ 7914 [+][+] −− [0][0] 00 _[.][.]_ _.._ [09][01] 1302 0 _._ 7664 _._ 44 ± [+] − [0] 0 0 _[.]_ _._ [28] _._ 32 004 0 _._ 60 [+] − [0] 0 _[.]_ _._ [07] 03 52 _._ 13 [+] − [0] 0 _[.]_ _._ [85] 58 – – 31 [+] − [4] 0 40 [+] − [4] 7 [0] _[.]_ [0114][ ±][ 0] _[.]_ [0006] 5 _._ 19 [+] − [0] 0 _[.]_ _._ [56] 20 01 _._ 142 _._ 23 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [03][003] 08010 11 _.._ 3273 [+][+] −− [0][0] 00 _[.][.]_ _.._ [18][02] 1701 2 _._ 36 – [+] − [0] 0 _[.]_ _._ [73] 54

S_8 HERSJ020941.2 + 001558 −−00 _._ 259 _._ 89 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [02][005] 03010 00 _.._ 159046 [+][+] −− [0][0] 00 _[.][.]_ _.._ [028][008] 006002 82 _.._ 844579 [+][+] −− [0][0] 00 _[.][.]_ _.._ [007][002] 011003 0 _._ 704 [+] − [0] 0 _[.]_ _._ [003] 004 −10 _._ 81 [+] − [0] 0 _[.]_ _._ [55] 21 – – 43 43 0 _._ 0093 ± 0 _._ 0004 7 _._ 29 [+] − [0] 0 _[.]_ _._ [30] 10 01 _._ 158 _._ 30 ± ± 0 0 _.._ 03003 185 _.._ 9961 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ _[.]_ [03] _._ 06 [08] 19 4 _._ 96 – [+] − [0] 0 _[.]_ _._ [95] 77

S_9 HERMESJ032637 − 270044 0 _._ 024 – [+] − [0] 0 _[.]_ _._ [009] 013 −0 _._ 12 – ± 0 _._ 01 0 _._ 981 – [+] − [0] 0 _[.]_ _._ [005] 006 0 _._ 87 ± 0 _._ 01 −40 _._ 54 [+] − [1] 2 _[.]_ _._ [64] 25 – – 42 [+] − [0] 9 [28] [+] − [11] 5 0 _._ 0110 [+] − [0] 0 _[.]_ _._ [0010] 0009 6 _._ 15 [+] − [0] 0 _[.]_ _._ [32] 38 0 _._ 072 ± – 0 _._ 004 3 _._ 01 – [+] − [0] 0 _[.]_ _._ [03] 04 ––


S_10 HERMESJ033732 − 295353 0 _._ 1754 [+] − [0] 0 _[.]_ _._ [0007] 0005 [0] _[.]_ [0576] [+] − [0] 0 _[.]_ _._ [0012] 0008 [1] _[.]_ [9718] [+] − [0] 0 _[.]_ _._ [0003] 0006 [0] _[.]_ [6495] [+] − [0] 0 _[.]_ _._ [0003] 0006 [−][80] _[.]_ [49] [+] − [0] 0 _[.]_ _._ [04] 15 – – 41 38 0 _._ 0057 [+] − [0] 0 _[.]_ _._ [0002] 0003 6 _._ 27 [+] − [0] 0 _[.]_ _._ [50] 05 0 _._ 0801 [+] − [0] 0 _[.]_ _._ [0045] 0002 11 _._ 662 [+] − [0] 0 _[.]_ _._ [004] 007 –
0 _._ 57 [+] − [0] 0 _[.]_ _._ [11] 12 0 _._ 18 [+] − [0] 0 _[.]_ _._ [04] 05 6 _._ 40 [+] − [1] 1 _[.]_ _._ [18] 30 – – –

S_12 HERMESJ100144 + 025709 −−00 _._ 033 _._ 26 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [02][003] 03004 00 _._ 042 _._ 34 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [08][009] 02003 0 _._ 9307 _._ 44 ± [+] − [0] 0 0 _[.]_ _._ [02] _._ 01 002 0 _._ 686 [+] − [0] 0 _[.]_ _._ [006] 008 −16 _._ 66 [+] − [0] 0 _[.]_ _._ [39] 56 – – 33 [+] − [11] 10 [30] [+] − [9] 0 0 _._ 0076 [+] − [0] 0 _[.]_ _._ [0004] 0003 6 _._ 33 – [+] − [0] 0 _[.]_ _._ [15] 17 0 _._ 094 – [+] − [0] 0 _[.]_ _._ [002] 001 2 _._ 63 ± – 0 _._ 02 –


S_13 HERMESJ103827 + 581544 0 _._ 228 [+] − [0] 0 _[.]_ _._ [016] 006 0 _._ 27 ± 0 _._ 01 2 _._ 408 ± 0 _._ 010 0 _._ 582 ± 0 _._ 007 −70 _._ 47 [+] − [0] 0 _[.]_ _._ [76] 47 – – 44 44 0 _._ 025 ± 0 _._ 002 4 _._ 29 [+] − [0] 0 _[.]_ _._ [15] 25 0 _._ 17 [+] − [0] 0 _[.]_ _._ [02] 01 15 _._ 68 ± 0 _._ 4 –
1 _._ 56 [+] − [0] 0 _[.]_ _._ [11] 04 1 _._ 84 [+] − [0] 0 _[.]_ _._ [09] 10 16 _._ 47 ± 0 _._ 07 – – –

S_14 HERMESJ110016 + 571736 −−02 _._ 324 _._ 48 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [05][007] 07009 −−01 _._ 251 _._ 92 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [05][007] 08011 1 _._ 0818 _._ 28 ± [+] − [0] 0 0 _[.]_ _._ [02] _._ 03 003 0 _._ 71 ± 0 _._ 01 11 _._ 63 [+] − [1] 0 _[.]_ _._ [13] 88 – – 32 [+] − [5] 7 42 [+] − [1] 0 0 _._ 0151 [+] − [0] 0 _[.]_ _._ [0008] 0009 2 _._ 43 [+] − [0] 0 _[.]_ _._ [03] 04 01 _._ 211 _._ 84 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [04][004] 06006 35 _._ 56 _._ 39 ± [+] − [0] 0 0 _[.]_ _._ [03] _._ 04 02 1 _._ 95 – [+] − [0] 0 _[.]_ _._ [10] 09

S_16 HATLASJ125126 + 254928 −−02 _._ 40 _._ 75 ± [+] − [0] 0 0 _[.]_ _._ [24] _._ 23 02 00 _._ 056 _._ 38 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [08][009] 09014 17 _._ 133 _._ 94 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [50][016] 66007 0 _._ 58 [+] − [0] 0 _[.]_ _._ [01] 02 20 _._ 05 [+] − [2] 3 _[.]_ _._ [41] 88 – – 39 ± 3 37 [+] − [5] 9 0 _._ 015 ± 0 _._ 002 5 _._ 10 [+] − [0] 0 _[.]_ _._ [37] 67 00 _.._ 05239 ± [+] − [0] 0 0 _[.]_ _._ [006] _._ 005 04 33 _.._ 2073 [+][+] −− [0][0] 00 _[.][.]_ _.._ [45][13] 4604 3 _._ 29 – [+] − [1] 0 _[.]_ _._ [07] 72

S_17 HATLASJ125760 + 224558 00 _._ 104 _._ 69 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [08][012] 04007 −−00 _.._ 4006 [+][+] −− [0][0] 00 _[.][.]_ _.._ [08][01] 3004 04 _._ 681 _._ 52 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [03][005] 04006 0 _._ 70 [+] − [0] 0 _[.]_ _._ [07] 02 60 _._ 10 [+] − [1] 2 _[.]_ _._ [21] 50 – – 38 43 0 _._ 0059 ± 0 _._ 0004 4 _._ 46 [+] − [0] 0 _[.]_ _._ [56] 52 00 _._ 081 _._ 70 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [05][006] 04005 11 _.._ 4341 [+][+] −− [0][0] 00 _[.][.]_ _.._ [22][04] 1303 1 _._ 74 – [+] − [0] 0 _[.]_ _._ [28] 17

S_18 HATLASJ133008 + 245860 00 _._ 037 _._ 21 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [02][003] 06010 −−01 _._ 287 _._ 65 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [06][010] 03005 51 _.._ 037974 [+][+] −− [0][0] 00 _[.][.]_ _.._ [001][009] 002011 0 _._ 616 [+] − [0] 0 _[.]_ _._ [009] 007 −14 _._ 02 [+] − [0] 0 _[.]_ _._ [61] 43 – – 39 [+] − [2] 5 36 [+] − [7] 5 [0] _[.]_ [0084][ ±][ 0] _[.]_ [0006] 12 _._ 31 [+] − [1] 0 _[.]_ _._ [10] 72 00 _._ 055 _._ 43 ± ± 0 0 _.._ 00302 31 _.._ 184990 [+][+] −− [0][0] 00 _[.][.]_ _.._ [009][006] 008005 3 _._ 47 – [+] − [1] 0 _[.]_ _._ [14] 80

S_19 HATLASJ133846 + 255057 0 _._ 09050 _._ 51 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [07][0005] 080028 [−][0] − _[.]_ [1092] 0 _._ 63 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [10][0001] 080008 [0] _[.]_ [6697] 3 _._ 83 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [48][0004] 620002 0 _._ 895 [+] − [0] 0 _[.]_ _._ [002] 011 79 _._ 56 [+] − [0] 0 _[.]_ _._ [59] 58 [0] _[.]_ [281] [+] − [0] 0 _[.]_ _._ [008] 001 [−][0] _[.]_ [0560] [+] − [0] 0 _[.]_ _._ [0024] 0002 42 41 0 _._ 0046 [+] − [0] 0 _[.]_ _._ [0003] 0002 3 _._ 78 [+] − [0] 0 _[.]_ _._ [04] 02 0 _._ 00963 _._ 80 ± [+] − 0 [0] 0 _[.]_ _._ _._ [0006] 0008 03 11 _.._ 70612 ± [+] − [0] 0 0 _[.]_ _._ [012] _._ 002 26 7 _._ 95 – [+] − [3] 2 _[.]_ _._ [82] 14

S_21 HERMESJ171451 + 592634 −−20 _.._ 0123 [+][+] −− [0][0] 00 _[.][.]_ _.._ [39][05] 0901 10 _.._ 8021 [+][+] −− [0][0] 00 _[.][.]_ _.._ [27][03] 0901 08 _._ 976 _._ 35 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [05][006] 06007 0 _._ 72 ± 0 _._ 02 −76 _._ 63 [+] − [1] 0 _[.]_ _._ [34] 90 – – 42 [+] − [1] 6 35 [+] − [5] 2 0 _._ 012 ± 0 _._ 001 8 _._ 40 [+] − [5] 6 _[.]_ _._ [93] 00 00 _._ 053 _._ 41 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [41][053] 07009 4 _._ 14352 _._ 46 ± [+] − [0] 0 0 _[.]_ _._ [02] _._ 01 0008 2 _._ 83 – [+] − [0] 0 _[.]_ _._ [18] 17


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the _Herschel_ detection. Col. (3) and (4): RA and Dec. offsets in arcsec (first row) and kpc (second row). Col. (5): Einstein radius in arcsec (first row)
and kpc (second row). Col. (6): Axis ratio of the mass profile. Col. (7): Position angle of the mass profile. Col. (8) and (9): Shear elliptical components of the mass profile. Col. (10) and (11): Size of the source plane
pixelization. Col. (12): Regularization coefficient. Col. (13): Magnification computed on the regions of the source plane with _SNR >_ 3. Col. (14): Circularised radius equivalent to the regions of the source plane
with _SNR >_ 3. Col. (15): Mass within the Einstein radius. Col. (16): Mass-to-light ratio in _𝐹_ 110 _𝑊_ within the Einstein radius.

**Table 7** – _continued_


No. IAU name _𝛿𝑥_ _𝛿𝑦_ _𝜃_ _𝐸_ _𝑞_ _𝑃𝐴_ _𝜖_ _𝑠ℎ𝑒𝑎𝑟,_ 1 _𝜖_ _𝑠ℎ𝑒𝑎𝑟,_ 2 _𝑥_ pix _𝑦_ pix _𝜆_ _𝜇_ _𝑅_ bkg _,_ circ _𝑘_ 0

[arcsec] [arcsec] [arcsec] [arcsec] []
_𝑑𝑥_ 0 _𝑑𝑦_ 0 _𝜃_ _𝐸,_ 0 _𝑅_ bkg _,_ circ _,_ 0 _𝑀_ _𝑀_ / _𝐿_

[kpc] [kpc] [kpc] [kpc] [ 10 [11] M ⊙ ]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14) (15) (16)

S_29 HERSJ012041.6 − 002705 −−00 _._ 07 _._ 55 ± [+] − [0] 0 0 _[.]_ _._ [08] _._ 09 01 −−00 _.._ 09571 ± [+] − [0] 0 0 _[.]_ _._ [010] _._ 011 08 06 _.._ 92894 ± [+] − [0] 0 0 _[.]_ _._ [005] _._ 006 15 0 _._ 76 [+] − [0] 0 _[.]_ _._ [02] 01 −41 _._ 77 [+] − [2] 2 _[.]_ _._ [16] 17 – – 38 [+] − [5] 6 [35][ ±][ 6] [0] _[.]_ [022][ ±][ 0] _[.]_ [002] 3 _._ 91 [+] − [0] 0 _[.]_ _._ [43] 34 0 _._ 124 – [+] − [0] 0 _[.]_ _._ [008] 006 2 _._ 65 ± – 0 _._ 03 ––


S_30 HATLASJ085112 + 004934 0 _._ 03406 [+] − [0] 0 _[.]_ _._ [00009] 00014 [0] _[.]_ [1967] [+] − [0] 0 _[.]_ _._ [0010] 0002 [1] _[.]_ [24359] [+] − [0] 0 _[.]_ _._ [00004] 00003 [0] _[.]_ [34221] [+] − [0] 0 _[.]_ _._ [00034] 00007 [−][41] _[.]_ [033] [+] − [0] 0 _[.]_ _._ [008] 033 [−][0] _[.]_ [29461] [+] − [0] 0 _[.]_ _._ [00011] 00006 [0] _[.]_ [28098] [+] − [0] 0 _[.]_ _._ [00005] 00043 [44] 44 0 _._ 00112 [+] − [0] 0 _[.]_ _._ [00004] 00005 [27] _[.]_ [80] [+] − [0] 0 _[.]_ _._ [50] 59 [0] _[.]_ [01863] [+] − [0] 0 _[.]_ _._ [00004] 00009 [4] _[.]_ [0578] [+] − [0] 0 _[.]_ _._ [0014] 0003 –
0 _._ 24 [+] − [0] 0 _[.]_ _._ [03] 07 1 _._ 41 [+] − [0] 0 _[.]_ _._ [20] 39 8 _._ 90 [+] − [1] 2 _[.]_ _._ [26] 45 0 _._ 161 [+] − [0] 0 _[.]_ _._ [001] 004 4 _._ 60 [+] − [3] 2 _[.]_ _._ [73] 22 1 _._ 86 [+] − [2] 0 _[.]_ _._ [07] 72

S_32 HERMESJ104549 + 574512 −−10 _.._ 5947 [+][+] −− [0][0] 00 _[.][.]_ _.._ [15][03] 1704 −−00 _.._ 12944 ± [+] − [0] 0 0 _[.]_ _._ [006] _._ 009 04 28 _._ 631 _._ 97 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [67][007] 73012 0 _._ 677 [+] − [0] 0 _[.]_ _._ [005] 003 18 _._ 85 [+] − [0] 0 _[.]_ _._ [69] 23 – – 41 40 ± 4 0 _._ 014 ± 0 _._ 001 8 _._ 63 [+] − [0] 0 _[.]_ _._ [37] 21 00 _._ 108 _._ 85 ± ± 0 0 _.._ 00202 175 _.._ 4523 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ _[.]_ [50] _._ 52 [21] 12 63 _._ 80 – [+] − [12] 10 _[.]_ _._ [97] 76

S_35 HATLASJ132630 + 334410 00 _._ 004 _._ 03 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [03][004] 05006 −−00 _._ 057 _._ 44 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [07][009] 10013 112 _._ 684 _._ 92 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ _[.]_ [005] _._ 004 [04] 03 0 _._ 577 [+] − [0] 0 _[.]_ _._ [008] 006 −47 _._ 54 [+] − [0] 0 _[.]_ _._ [42] 40 – – 42 [+] − [2] 4 [34] [+] − [8] 2 [0] _[.]_ [0095][ ±][ 0] _[.]_ [0006 1] _[.]_ [89][ ±][ 0] _[.]_ [02] [0] 0 _[.]_ [0938] _._ 743 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [063][0079] 0030004 98 _._ 09 _._ 26 ± [+] − [0] 0 0 _[.]_ _._ [03] _._ 02 03 3 _._ 83 – [+] − [0] 0 _[.]_ _._ [20] 19

S_38 HERMESJ142824 + 352620 −−00 _._ 0008 _._ 007 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [054][0065] 0610074 00 _._ 016 _._ 13 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [04][005] 05006 01 _._ 215 _._ 78 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [05][006] 03003 0 _._ 66 [+] − [0] 0 _[.]_ _._ [06] 05 −5 _._ 44 [+] − [5] 8 _[.]_ _._ [95] 75 – – 42 [+] − [1] 8 [25] [+] − [5] 4 0 _._ 0064 [+] − [0] 0 _[.]_ _._ [0006] 0004 2 _._ 64 [+] − [0] 0 _[.]_ _._ [15] 14 00 _.._ 09078 ± [+] − [0] 0 0 _[.]_ _._ [003] _._ 004 03 00 _._ 137 _._ 58 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [04][010] 02005 0 _._ 98 – [+] − [0] 0 _[.]_ _._ [11] 09

S_39 HATLASJ223753.8 − 305828 10 _.._ 2419 [+][+] −− [0][0] 00 _[.][.]_ _.._ [18][02] 2001 −−00 _._ 091 _._ 60 [+] − [+] − [0][0] 00 _[.][.]_ _.._ [11][010] 13017 81 _.._ 2826 [+][+] −− [0][0] 10 _[.][.]_ _.._ [90][02] 3101 0 _._ 54 [+] − [0] 0 _[.]_ _._ [01] 03 65 _._ 49 [+] − [0] 0 _[.]_ _._ [77] 62 – – 44 20 0 _._ 0098 [+] − [0] 0 _[.]_ _._ [0006] 0005 2 _._ 65 [+] − [0] 0 _[.]_ _._ [04] 10 0 _._ 11281 _._ 10 ± [+] − 0 [0] 0 _[.]_ _._ _._ [0032] 0010 03 34 _.._ 5388 [+][+] −− [0][1] 01 _[.][.]_ _.._ [07][15] 0502 4 _._ 00 – [+] − [2] 1 _[.]_ _._ [08] 12


S_40 HATLASJ225250.7 − 313657 0 _._ 182 [+] − [0] 0 _[.]_ _._ [012] 005 0 _._ 08 [+] − [0] 0 _[.]_ _._ [01] 02 0 _._ 605 [+] − [0] 0 _[.]_ _._ [008] 004 0 _._ 633 [+] − [0] 0 _[.]_ _._ [020] 009 −73 _._ 84 [+] − [2] 0 _[.]_ _._ [35] 69 – – 41 [+] − [3] 9 [40] [+] − [4] 14 [0] _[.]_ [0031] [+] − [0] 0 _[.]_ _._ [0002] 0003 3 _._ 44 [+] − [0] 0 _[.]_ _._ [18] 11 0 _._ 078 [+] − [0] 0 _[.]_ _._ [002] 003 1 _._ 09 [+] − [0] 0 _[.]_ _._ [03] 01 –
1 _._ 33 [+] − [0] 0 _[.]_ _._ [17] 27 0 _._ 54 [+] − [0] 0 _[.]_ _._ [14] 18 4 _._ 41 [+] − [0] 0 _[.]_ _._ [51] 89 0 _._ 65 ± 0 _._ 02 1 _._ 12 [+] − [0] 0 _[.]_ _._ [47] 40 4 _._ 89 [+] − [4] 1 _[.]_ _._ [71] 81



S_41 HELMSJ233633.5 − 032119 0 _._ 051 [+] − [0] 0 _[.]_ _._ [001] 005 −0 _._ 0851 [+] − [0] 0 _[.]_ _._ [0106] 0004 [1] _[.]_ [7281] [+] − [0] 0 _[.]_ _._ [0130] 0007 0 _._ 7347 [+] − [0] 0 _[.]_ _._ [0008] 0196 −48 _._ 44 [+] − [1] 0 _[.]_ _._ [47] 11 – – 39 43 0 _._ 0084 [+] − [0] 0 _[.]_ _._ [0005] 0004 [12] _[.]_ [39] [+] − [2] 2 _[.]_ _._ [16] 48 0 _._ 036 [+] − [0] 0 _[.]_ _._ [011] 005 9 _._ 161 [+] − [0] 0 _[.]_ _._ [105] 006 –

– – – 0 _._ 30 [+] − [0] 0 _[.]_ _._ [10] 05 – –

26 _E. Borsato et al._


4


2


0


HATLASJ000330.6 321136/S_1

HELMSJ001353.5 060200/S_3

HELMSJ003619.8+002420/S_4

HERSJ020941.2+001558/S_8

HERMESJ032637 270044/S_9


HERMESJ100144+025709/S_10

HERMESJ103827+581544/S_12

HERMESJ110016+571736/S_13

HATLASJ125126+254928/S_14

HATLASJ125760+224558/S_16

HERMESJ033732 295353/S_17

HATLASJ133846+255057/S_18


HERMESJ171451+592634/S_19

HERSJ012041.6 002705/S_21


HATLASJ085112+004934/S_29


HERMESJ104549+574512/S_30

HATLASJ133008+245860/S_32

HATLASJ132630+334410/S_35


HERMESJ142824+352620/S_38

HATLASJ223753.8 305828/S_39

HATLASJ225250.7 313657/S_40

HELMSJ233633.5 032119/S_42

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||



0.00 0.05 0.10 0.15 0.20

R bkg, circ [arcsec]


**Figure 10.** _Top panel_ : Distribution of the circularised radius of the background
sources from the lens modelling and taking into account the uncertainties
on the radii. _Bottom_ _panel_ : Circularised radius of the background sources
(blues circles) and HWHM of the PSF of the image corrected for the lensing
magnification (pink line).


A comparison between our Einstein radii and those available in the
literature (Bussmann et al. 2013, 2015; Calanog et al. 2014; Geach
et al. 2015; Enia et al. 2018; Dye et al. 2022; Maresca et al. 2022;
Kamieneski et al. 2023a) is shown in Table 8 and in Fig. 12. Our
values are comparable with what is found in the literature, with only
two exceptions: S_38 which Bussmann et al. (2013) did not resolve
with SMA, due to the very low angular separation of the multiple
images and assumed to have Einstein radius of 0 _._ 1 ± 0 _._ 3 arcsec; and
S_10 for which Calanog et al. (2014) fixed the flattening and position
angle of the mass model to be circular and aligned with the lens.


**6** **DISCUSSION**


Consistent with expectations (Perrotta et al. 2002; Lapi et al. 2012;
Negrello et al. 2017) our 65 confirmed lenses mostly comprise systems where the lens is a single galaxy (51). Only 4 are made of
spectroscopically confirmed groups or clusters (S_36, S_48, S_60,
and S_61), and 9 systems have a morphology consistent with a group
(S_6, S_15, S_23, S_25, S_28, S_33, S_34, S_54, and S_63). The
lensing galaxies are nearly all ETGs, with the only exceptions of
S_47 and one of the galaxies in the lensing cluster of S_48. Both
of them show a clear spiral structure. The ETG nature of the lensing galaxies is further confirmed by their concentrations, with 92%
of our sample lenses being more concentrated than expected for an
exponential disk.
The mass within the Einstein radii of the foreground lenses ranges
between 9 _._ 9 × 10 [10] M ⊙ (1-st percentile) and 6 _._ 4 × 10 [11] M ⊙ (99-th
percentile). The mass-to-light ratios in the _F110W_ filter within the
Einstein radius range between 1.25 and 8.86 M ⊙ L [−] ⊙ [1] [.] [The] [back-]
ground sources host a variety of morphologies, including single
compact sources (e.g. S_12), more diffuse sources (e.g. S_18), and
multiple clumps (S_17). We find that 14 out of 22 reconstructed
background sources are single sources, whereas the remaining 8 are
multiple sources. The present analysis alone is not enough to de

MNRAS **000**, 1–57 (2022)



termine whether these morphologies indicate different populations
of DSFGs or variations in the stellar and/or dust distributions. The

physical sizes of the background sources, measured as the circularised radii of the circles equivalent to the regions of the source
plane with SNR _>_ 3, range between 0.34 kpc (1-st percentile) and
1.30 kpc (99-th percentile). We compare our stellar sizes with the
dust ones by Enia et al. (2018), who modelled the SMA sub-mm/mm
emission of a sample of 12 lenses similarly selected and partially
included in our sample. They found dust sizes between 1.52 kpc
(1-st percentile) and 4.07 kpc (99-th percentile). We can understand
this result by considering that the _HST_ observations, by sampling the
optical/near-UV rest-frame emission, are expected to pick up only the
intrinsically brightest and more compact regions of the background
sources whose light can pass through the dust. This is consistent with
an inside-out growth and later inside-out quenching, a scenario where
the central regions of these DSFGs begin to clear out the dust first,
causing the more compact stellar emission to shine through. Interestingly, the _HST_ sizes are comparable to bright nuclei and off-nuclear
knots in local ULIRGs (Surace et al. 1998; Farrah et al. 2001). This
is somewhat in contrast with previous literature (e.g., Pantoni et al.
2021) that argued for the dust emission to be more compact than the
stellar one. Although, recently, Kamieneski et al. (2023b) studied a
_𝑧_ ∼ 2 _._ 3 lensed galaxies with properties similar to those of the lensed
DSFGs in our sample and found rest frame near-UV/optical/near-IR
emitting regions comparable or even slightly smaller in size than
the ones measured in the sub-mm, thus providing evidence for an
inside-out quenching scenario. It is worth noticing that Kamieneski
et al. (2023b) has also considered another possible, but less likely,
explanation related to inclination effects and uneven dust distribution. We also want to point out that the difference in sizes we observe
between the stellar emitting region, as sampled by _HST_, and the dust
emitting region, as probed by SMA, may be affected by the lower
angular resolution of the SMA observations compared to _HST_ data.
In fact, by projecting the half width at half maximum (HWHM) of
the SMA beam to the redshift of the source and then dividing it
by the square root of the total magnification within the _>_ 3 _𝜎_ regions, we get a physical resolution (once averaged over the whole
sample) of 0 _._ 85 kpc, which is larger than what we get for near-IR
size for about 50 per cent of our sample. While Enia et al. (2018)
sources are resolved ( _𝑅_ bkg _,_ circ /PSF HWHM ∼ _[>]_ 1), any emission coming from regions smaller than the projected HWHM would inevitably
be broadened. Moreover, the depth of our observations does not allow
us to exclude that other, more obscured and undetected, star-forming
knots are present throughout the disk, implying that mass buildup
could happen disk-wide.

Finally, it is worth mentioning that the optical/near-IR sizes quoted
in the literature are often measured through the effective radius obtained by fitting a Sérsic profile to the surface brightness distribution
of the background sources. For lensed galaxies, this is usually done
directly during the lens modelling by including a parametric background source (e.g. Calanog et al. 2014). Such an estimate of size
takes into account the concentration of the source and averages out
the surface brightness distribution in the case of clumpy emission.
In comparison, our measure is SNR-dependent and is not affected by
the smoothness of the surface brightness distribution. We remark that
the relation between the observed-frame near-IR sizes and sub-mm

ones is still up to debate and could depend on additional factors we
do not discuss here, like the stellar mass of the galaxy (see, Liu et al.
2023, for details) or its evolutionary stage. At the same time, we find
magnifications ranging between 2.4 (1-st percentile) and 15.8 (99-th
percentile), with a median of 5.5 for our sample. The magnifications
by Enia et al. (2018) range between 3.20 (1-st percentile) and 8.35

|Col1|1 arcsec|1 arcsec<br>1 arcsec|0 .1 arcsec|Col5|
|---|---|---|---|---|
||1 arcsec|1 arcsec|1 arcsec|1 arcsec|



the literature from the sub-mm/mm observations and reference. Col. (8) and (9): Multiwavelength observations and reference.



(99-th percentile) with a median of 5.7. This comparison suggests a
minor, or even negligible, differential magnification.


We compare the properties of our lenses (i.e., total effective radii,
Einstein radii, and total effective surface brightnesses) to those of
the SLACS sample of confirmed lenses (Bolton et al. 2008). This is
the largest available sample of strong lenses followed up by _HST_ and
with lens modelling. The SLACS lensing candidates were identified
from archival SDSS spectroscopic data as all the systems that show
the presence of two separate redshift estimates in the same spectrum:
a lower absorption-line redshift for the foreground lens and a higher
emission-line redshift for the background source. These candidates



were then followed up and confirmed by means of _HST ACS/F814W_
imaging. We consider the 63 confirmed lenses out of 131 candidates, for which Bolton et al. (2008) were able to subtract the surface
brightness distribution of the foreground lens and perform the lens
modelling. They modelled the surface brightness distribution of the
lens, adopting the de Vaucouleurs profile. We perform a K-correction
of the total effective surface brightness of all the galaxies of our and
SLACS samples with available redshifts. As a template for the ETG
SED, we use the 17 local elliptical galaxies available in the Brown
Atlas (Brown et al. 2014). To estimate the _F110W_ magnitude of the
SLACS lenses, we redshift and normalize the template to match the


MNRAS **000**, 1–57 (2022)

28 _E. Borsato et al._



HERSJ020941.2+001558/S_8 ~~This work~~


HERMESJ032637 270044/S_9 ~~Near-IR~~



HERMESJ032637 270044/S_9



HERMESJ033732 295353/S_10


HERMESJ100144+025709/S_12


HERMESJ103827+581544/S_13


HERMESJ110016+571736/S_14


HATLASJ133008+245860/S_18


HERMESJ171451+592634/S_21


HERMESJ104549+574512/S_32


HATLASJ132630+334410/S_35


HERMESJ142824+352620/S_38



6


5




|This w|Col2|work|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|~~This w~~<br>~~Near-I~~|~~This w~~<br>~~Near-I~~|~~ ork~~<br>~~R~~|||||
||subm|m/mm|||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||



0.0 0.5 1.0 1.5 2.0 2.5


E [ [arcsec]]


**Figure** **12.** Comparison between our estimated Einstein radii (blue circles)
and the ones from literature measured either in near-IR (blue triangles) or
sub-mm/mm (red triangles).


_F814W_ magnitude using `PySynphot` package [13] . Then, we compute
the _F110W_ magnitude of each template at _𝑧_ = 0 and at the redshift of
the foreground lenses of both samples. Finally, we adopt the _F110W_
magnitude difference as the K-correction term. This correction does
not take into account possible differences between the SEDs of the
templates and the ones of the lenses. The median K-correction terms
for our sample and SLACS are 0.04 mag and 0.03 mag, respectively.
From Fig. 13, it is possible to see that our sample shows different
_𝑅_ 50 and _𝜃_ _𝐸_ distributions than SLACS. Our selection is able to pick
up more systems with both smaller or larger values of _𝜃_ _𝐸_ . Moreover,
at similar Einstein radii, the effective radii of our lenses are significantly smaller than the SLACS, making our background sources less
contaminated by the emission of the lenses. Figure 14 shows that the
two samples have similar _𝑅_ 50 _,_ 0 and absolute magnitude distributions,
although our lenses show a tail for smaller and fainter galaxies. At
the same time, our lenses have lower _𝜇_ 50 _,_ 0 _,_ K corr for the same radii,
which implies that our lenses either are fainter or more concentrated
than the de Vaucouleurs profiles. The increased scatter we find in
both the _𝑅_ 50 _,_ 0 and _𝑀_ _𝐹_ 110 _𝑊_, and _𝑅_ 50 _,_ 0 and _𝜇_ 50 _,_ 0 _,_ K corr distributions
can be accounted for by considering the variation in concentration
and the wide range of foreground lens redshifts we observed. We can
try to further explain these differences by considering the different
selections of the two samples. The SLACS sample, being constructed
from SDSS spectroscopic data and needing a robust detection of both
the foreground lens and background source, is limited in magnitude
to brighter lenses at lower redshift. In particular, the SLACS spectroscopic selection was done through 3 arcsec diameter fibres and
comprises either local galaxies or massive ETGs at _𝑧_ ≲ 0 _._ 6.


**7** **CONCLUSIONS**


We have carried out a snapshot _HST_ F110W observing campaign to
follow-up 281 _Herschel_ -selected candidate strongly lensed galaxies.
We visually inspect them and classify them according to the presence of the background sources, confirming 25 candidates as strong
lenses. We model all the systems where we identify a suitable lens
candidate exploiting three different surface-brightness modelling algorithms, namely `GASP2D`, `GALFIT`, and `ISOFIT+CMODEL`, based on
the morphology of the foreground lensing galaxies. By combining
the visual inspection, available multi-wavelength follow-ups, and results of the lens subtraction, we are able to confirm as lensed a total
of 65 systems. Lastly, we perform lens modelling and source reconstruction of all the systems for which we can confidently identify


13 `[https://pysynphot.readthedocs.io/en/latest/](https://pysynphot.readthedocs.io/en/latest/)`


MNRAS **000**, 1–57 (2022)



4


3


2


1


0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
|||||Thi<br> len<br>Thi<br> ro<br>SLA|s work<br> s modelling<br>s work<br> ugh estimate<br>CS||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||



0 1 2 3 4 5


E [ [arcsec]]


**Figure 13.** _Top panel_ : Normalised distribution of the values of the Einstein
radius of the lenses in our (blue histogram) and in the SLACS samples (orange
histogram). _Bottom left panel:_ Total effective radius as a function of Einstein
radius of the lenses in our (blue symbols) and in the SLACS sample (orange
circles). The blue circles and crosses correspond to systems for which we
derived the Einstein radius from the lens modelling or the separation between
multiple images, respectively. _Bottom right panel_ Normalised distribution of
the values of the total effective radius of the lenses.


both a galaxy acting as the main lens and the background source in
the _HST_ images (34 systems). We obtain successful results for 23
galaxies. The main results of our analysis are the following:


 - the overall surface brightness distribution of the lenses and their
morphology follows the relations expected for ETGs; however, the
foreground lensing galaxies often needed multiple surface brightness
components, with properties significantly varying from galaxy to
galaxy;

 - most of the lensing systems are consistent with single galaxy
lenses, with only ∼ 7% of them being confirmed as a group or cluster
lenses;

 - the estimated magnifications and Einstein radii are consistent
with previous analysis conducted on data at different wavelengths;
however, the inferred size of the background sources is about 3 times
smaller than the ones measured in the sub-mm/mm with SMA by
Enia et al. (2018) for a similarly selected, and partially overlapping
sample. This difference in size between the stellar and the dustemitting regions is suggestive of an inside-out quenching scenario;

 - the sub-mm selection used to build our sample revealed lensing
systems with fainter lenses and larger Einstein radii than the SLACS

survey.


To conclude, we point out that the _HST_ snapshots alone, even after carefully identifying and subtracting the candidate lenses, might
miss some of the fainter lensed background sources. We argue that
this is due to their dust obscuration and high redshift. This underlines the importance of dedicated, deeper near-IR observations (e.g.,
with _HST_, Keck, _Euclid_ or _JWST_ ) and high-resolution sub-mm observations (e.g., with ALMA and NOEMA) to effectively determine
the nature of the majority of _Herschel_ -selected strong lensing candidates. This work provides the basis for further detailed analysis of the

14


16


18


20


17


18


19


20


21


22


23


0.0 0.2 0.4 0.6 0.8 1.0 1.2 1.4

log 10 (R 50, 0 [kpc])


**Figure 14.** _Top panel:_ Normalized distribution of the total effective radii in
kpc of our (blue histogram) and SLACS samples (orange histogram). _Central_
_left_ _panel:_ Absolute magnitude corrected for _𝐾_ -correction against the total
effective radii in kpc of the two samples. _Central right panel:_ Normalized distribution of the absolute magnitude of the two samples with the _𝐾_ -correction
applied. Our lensing galaxies are color-coded according to their concentration, with purple corresponding to the less-concentrated systems and green

to the most-concentrated ones. White marks the concentration of a de Vau
couleurs profile. _Bottom_ _left_ _panel:_ Kormendy relation of the two samples.
Our lensing galaxies are color-coded according to their concentration. _Bottom_
_right panel:_ Normalized distribution of the total effective surface brightness
of the two samples with the _𝐾_ -correction applied.


background sources by allowing not only more complex lens modelling but also providing constraints on the stellar content through
SED-fitting techniques.


**ACKNOWLEDGEMENTS**


This work benefited from the support of the project Z-GAL ANRAAPG2019 of the French National Research Agency (ANR). EB
acknowledges the School of Physics and Astronomy of Cardiff University for hospitality while this paper was in progress. EB, EMC, and
GR are supported by Padua University grants Dotazione Ordinaria
Ricerca (DOR) 2019-2021 and by the Italian Ministry for Education, University, and Research (MIUR) grant Progetto di Ricerca di
Interesse Nazionale (PRIN) 2017 20173ML3WW-001. EMC is also
funded by the Istituto Nazionale di Astrofisica (INAF) through grant
PRIN 2022 C53D23000850006. LM and MV acknowledge financial support from the Inter-University Institute for Data Intensive
Astronomy (IDIA), a partnership of the University of Cape Town,
the University of Pretoria and the University of the Western Cape,
and from the South African Department of Science and Innovation’s
National Research Foundation under the ISARP RADIOSKY2020

and RADIOMAP+ Joint Research Schemes (DSI-NRF Grant Numbers 113121 and 150551) and the SRUG Projects (DSI-NRF Grant
Numbers 121291, SRUG22031677 and SRUG2204254729). DW ac


_Characterisation of HST confirmed lenses_ 29


knowledges support from program number HST-GO-15242, provided by NASA through a grant from the Space Telescope Science
Institute, which is operated by the Association of Universities for
Research in Astronomy, Incorporated, under NASA contract NAS526555. AA is supported by ERC Advanced Investigator grant, DMIDAS [GA 786910], to C. S. Frenk. PC acknowledges the support
of the project Z-GAL ANR-AAPG2019 of the French National Research Agency (ANR). HD acknowledges financial support from the
Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (AEI-MCINN) under grant (La evolución de los cíumulos de
galaxias desde el amanecer hasta el mediodía cósmico) with reference (PID2019-105776GB-I00/DOI:10.13039/501100011033) and
acknowledge support from the ACIISI, Consejería de Economía,
Conocimiento y Empleo del Gobierno de Canarias and the European
Regional Development Fund (ERDF) under grant with reference
PROID2020010107. JGN acknowledges financial support from the
PGC projects PGC2018-101948-B-I00 and PID2021-125630NBI00 (MICINN, FEDER). SJ is supported by the European Union’s
Horizon Europe research and innovation program under the Marie
Skłodowska-Curie grant agreement No. 101060888. AL is partly supported by the PRIN MIUR 2017 prot. 20173ML3WW 002 ‘Opening
the ALMA window on the cosmic evolution of gas, stars, and massive
black holes’. IPF acknowledges support from the Spanish State Research Agency (AEI) under grant number PID2019-105552RB-C43.
SS was partly supported by ESCAPE – The European Science Cluster of Astronomy & Particle Physics ESFRI Research Infrastructures,
which in turn received funding from the European Union’s Horizon
2020 research and innovation programme under Grant Agreement
no. 824064. SS thanks the Science and Technology Facilities Council for support under grants ST/P000584/1. CY acknowledges the
support from the ERC Advanced Grant 789410.


**DATA AVAILABILITY**


The reduced images, models, residuals, and PSF cutouts are available on Zenodo at the following link `[https://doi.org/10.5281/](https://doi.org/10.5281/zenodo.10007041)`
`[zenodo.10007041](https://doi.org/10.5281/zenodo.10007041)` . Future versions will be available at `[https:](https://zenodo.org/doi/10.5281/zenodo.10007040)`
`[//zenodo.org/doi/10.5281/zenodo.10007040](https://zenodo.org/doi/10.5281/zenodo.10007040)` .


**REFERENCES**


[Aguirre P., et al., 2018, ApJ, 855, 26](http://dx.doi.org/10.3847/1538-4357/aaaab0)
[Albareti F. D., et al., 2017, ApJS, 233, 25](http://dx.doi.org/10.3847/1538-4365/aa8992)
[Amvrosiadis A., et al., 2018, MNRAS, 475, 4939](http://dx.doi.org/10.1093/mnras/sty138)

[Asboth V., et al., 2016, MNRAS, 462, 1989](http://dx.doi.org/10.1093/mnras/stw1769)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
Auger M. W., Treu T., Bolton A. S., Gavazzi R., Koopmans L. V. E., Marshall
[P. J., Bundy K., Moustakas L. A., 2009, ApJ, 705, 1099](http://dx.doi.org/10.1088/0004-637X/705/2/1099)
[Bakx T. J. L. C., et al., 2018, MNRAS, 473, 1751](http://dx.doi.org/10.1093/mnras/stx2267)

[Bakx T. J. L. C., et al., 2020, MNRAS, 496, 2372](http://dx.doi.org/10.1093/mnras/staa1664)
[Beers T. C., Flynn K., Gebhardt K., 1990, AJ, 100, 32](http://dx.doi.org/10.1086/115487)
[Berman D. A., et al., 2022, MNRAS, 515, 3911](http://dx.doi.org/10.1093/mnras/stac1494)

[Berta S., et al., 2021, A&A, 646, A122](http://dx.doi.org/10.1051/0004-6361/202039743)
Bolton A. S., Burles S., Koopmans L. V. E., Treu T., Gavazzi R., Moustakas
[L. A., Wayth R., Schlegel D. J., 2008, ApJ, 682, 964](http://dx.doi.org/10.1086/589327)
[Borys C., et al., 2006, ApJ, 636, 134](http://dx.doi.org/10.1086/497983)
Bradley L., et al., 2021, astropy/photutils: 1.1.0,
[doi:10.5281/zenodo.4624996,](http://dx.doi.org/10.5281/zenodo.4624996) `[https://doi.org/10.5281/zenodo.](https://doi.org/10.5281/zenodo.4624996)`

```
  4624996

```

[Brown M. J. I., et al., 2014, ApJS, 212, 18](http://dx.doi.org/10.1088/0067-0049/212/2/18)
[Bussmann R. S., et al., 2012, ApJ, 756, 134](http://dx.doi.org/10.1088/0004-637X/756/2/134)


MNRAS **000**, 1–57 (2022)

30 _E. Borsato et al._


[Bussmann R. S., et al., 2013, ApJ, 779, 25](http://dx.doi.org/10.1088/0004-637X/779/1/25)
[Bussmann R. S., et al., 2015, ApJ, 812, 43](http://dx.doi.org/10.1088/0004-637X/812/1/43)
[Butler K. M., et al., 2021, ApJ, 919, 5](http://dx.doi.org/10.3847/1538-4357/ac0c7a)
[Cañameras R., et al., 2015, A&A, 581, A105](http://dx.doi.org/10.1051/0004-6361/201425128)

[Cañameras R., et al., 2017, A&A, 604, A117](http://dx.doi.org/10.1051/0004-6361/201630186)
[Cai Z.-Y., et al., 2013, ApJ, 768, 21](http://dx.doi.org/10.1088/0004-637X/768/1/21)
[Cai Z.-Y., Negrello M., De Zotti G., 2022, ApJ, 932, 13](http://dx.doi.org/10.3847/1538-4357/ac6c83)
[Calanog J. A., et al., 2014, ApJ, 797, 138](http://dx.doi.org/10.1088/0004-637X/797/2/138)
[Carlstrom J. E., et al., 2011, PASP, 123, 568](http://dx.doi.org/10.1086/659879)
[Carrasco M., et al., 2017, ApJ, 834, 210](http://dx.doi.org/10.3847/1538-4357/834/2/210)
[Champagne J. B., et al., 2021, ApJ, 913, 110](http://dx.doi.org/10.3847/1538-4357/abf4e6)
[Ciambur B. C., 2015, ApJ, 810, 120](http://dx.doi.org/10.1088/0004-637X/810/2/120)
[Cox P., et al., 2011, ApJ, 740, 63](http://dx.doi.org/10.1088/0004-637X/740/2/63)
[Cox P., et al., 2023, A&A, 678, A26](http://dx.doi.org/10.1051/0004-6361/202346801)
Dalla Bontà E., Davies R. L., Houghton R. C. W., D’Eugenio F., Méndez[Abreu J., 2018, MNRAS, 474, 339](http://dx.doi.org/10.1093/mnras/stx2477)

[Díaz-Santos T., et al., 2021, A&A, 654, A37](http://dx.doi.org/10.1051/0004-6361/202140455)
Dressel L., 2022, WFC3 Instrument Handbook for Cycle 30 v. 14. STScI,
Baltimore, MD, US
[Dye S., et al., 2018, MNRAS, 476, 4383](http://dx.doi.org/10.1093/mnras/sty513)
[Dye S., et al., 2022, MNRAS, 510, 3734](http://dx.doi.org/10.1093/mnras/stab3569)
[Eales S., et al., 2010, PASP, 122, 499](http://dx.doi.org/10.1086/653086)

[Enia A., et al., 2018, MNRAS, 475, 3467](http://dx.doi.org/10.1093/mnras/sty021)
[Etherington A., et al., 2023, arXiv e-prints, p. arXiv:2301.05244](http://dx.doi.org/10.48550/arXiv.2301.05244)
[Everett W. B., et al., 2020, ApJ, 900, 55](http://dx.doi.org/10.3847/1538-4357/ab9df7)
[Falgarone E., et al., 2017, Nature, 548, 430](http://dx.doi.org/10.1038/nature23298)
[Farrah D., et al., 2001, MNRAS, 326, 1333](http://dx.doi.org/10.1111/j.1365-2966.2001.04721.x)
[Fu H., et al., 2012, ApJ, 753, 134](http://dx.doi.org/10.1088/0004-637X/753/2/134)
[Gaia Collaboration et al., 2021, A&A, 649, A1](http://dx.doi.org/10.1051/0004-6361/202039657)
[Gavazzi R., et al., 2011, ApJ, 738, 125](http://dx.doi.org/10.1088/0004-637X/738/2/125)
[Geach J. E., et al., 2015, MNRAS, 452, 502](http://dx.doi.org/10.1093/mnras/stv1243)

[Giulietti M., et al., 2022, MNRAS, 511, 1408](http://dx.doi.org/10.1093/mnras/stac145)
[Giulietti M., et al., 2023, ApJ, 943, 151](http://dx.doi.org/10.3847/1538-4357/aca53f)
[Gómez-Guĳarro C., et al., 2019, ApJ, 872, 117](http://dx.doi.org/10.3847/1538-4357/ab002a)
[González-Nuevo J., et al., 2012, ApJ, 749, 65](http://dx.doi.org/10.1088/0004-637X/749/1/65)
[González-Nuevo J., et al., 2019, A&A, 627, A31](http://dx.doi.org/10.1051/0004-6361/201935475)
[Harrington K. C., et al., 2016, MNRAS, 458, 4383](http://dx.doi.org/10.1093/mnras/stw614)
[Harris A. I., et al., 2012, ApJ, 752, 152](http://dx.doi.org/10.1088/0004-637X/752/2/152)
Hernán-Caballero A., Spoon H. W. W., Lebouteiller V., Rupke D. S. N., Barry
[D. P., 2016, MNRAS, 455, 1796](http://dx.doi.org/10.1093/mnras/stv2464)
Hoffmann S. L., Mack J., Avila R., Martlin C., Cohen Y., Bajaj V., 2021, in
American Astronomical Society Meeting Abstracts. p. 216.02
[Ikarashi S., et al., 2011, MNRAS, 415, 3081](http://dx.doi.org/10.1111/j.1365-2966.2011.18918.x)
[Ivison R. J., et al., 2013, ApJ, 772, 137](http://dx.doi.org/10.1088/0004-637X/772/2/137)
[Jarugula S., et al., 2021, ApJ, 921, 97](http://dx.doi.org/10.3847/1538-4357/ac21db)
[Jedrzejewski R. I., 1987, MNRAS, 226, 747](http://dx.doi.org/10.1093/mnras/226.4.747)
[Kamieneski P. S., et al., 2023a, arXiv e-prints, p. arXiv:2301.09746](http://dx.doi.org/10.48550/arXiv.2301.09746)
[Kamieneski P. S., et al., 2023b, arXiv e-prints, p. arXiv:2303.05054](http://dx.doi.org/10.48550/arXiv.2303.05054)
Lapi A., Negrello M., González-Nuevo J., Cai Z. Y., De Zotti G., Danese L.,
[2012, ApJ, 755, 46](http://dx.doi.org/10.1088/0004-637X/755/1/46)
[Leung T. K. D., et al., 2019, ApJ, 871, 85](http://dx.doi.org/10.3847/1538-4357/aaf860)
[Lewis A. J. R., et al., 2018, ApJ, 862, 96](http://dx.doi.org/10.3847/1538-4357/aacc25)
[Liu B., et al., 2022, ApJ, 929, 41](http://dx.doi.org/10.3847/1538-4357/ac5745)
Liu Z., Morishita T., Kodama T., 2023, A Multi-Wavelength Investigation
of Dust and Stellar Mass Distributions in Galaxies: Insights from HighResolution JWST Imaging ( `[arXiv:2305.10944](http://arxiv.org/abs/2305.10944)` )
[Ma J., et al., 2019, ApJS, 244, 30](http://dx.doi.org/10.3847/1538-4365/ab4194)
[Maddox S. J., et al., 2018, ApJS, 236, 30](http://dx.doi.org/10.3847/1538-4365/aab8fc)
Manjón-García A., Herranz D., Diego J. M., Bonavera L., González-Nuevo
[J., 2019, A&A, 622, A106](http://dx.doi.org/10.1051/0004-6361/201834549)

[Maresca J., et al., 2022, MNRAS, 512, 2426](http://dx.doi.org/10.1093/mnras/stac585)
[Méndez-Abreu J., Aguerri J. A. L., Corsini E. M., Simonneau E., 2008, A&A,](http://dx.doi.org/10.1051/0004-6361:20078089)

[478, 353](https://ui.adsabs.harvard.edu/abs/2008A&A...478..353M)

[Méndez-Abreu J., et al., 2017, A&A, 598, A32](http://dx.doi.org/10.1051/0004-6361/201629525)

[Messias H., et al., 2014, A&A, 568, A92](http://dx.doi.org/10.1051/0004-6361/201424410)
[Mocanu L. M., et al., 2013, ApJ, 779, 61](http://dx.doi.org/10.1088/0004-637X/779/1/61)
Nadadur D., Haralick R. M., 2000, IEEE Transactions on Image Processing,
9, 749


MNRAS **000**, 1–57 (2022)



[Nayyeri H., et al., 2016, ApJ, 823, 17](http://dx.doi.org/10.3847/0004-637X/823/1/17)
[Nayyeri H., et al., 2017, ApJ, 844, 82](http://dx.doi.org/10.3847/1538-4357/aa7aa0)
Negrello M., Perrotta F., González-Nuevo J., Silva L., de Zotti G., Granato
[G. L., Baccigalupi C., Danese L., 2007, MNRAS, 377, 1557](http://dx.doi.org/10.1111/j.1365-2966.2007.11708.x)
[Negrello M., et al., 2010, Science, 330, 800](http://dx.doi.org/10.1126/science.1193420)
[Negrello M., et al., 2014, MNRAS, 440, 1999](http://dx.doi.org/10.1093/mnras/stu413)
[Negrello M., et al., 2017, MNRAS, 465, 3558](http://dx.doi.org/10.1093/mnras/stw2911)
[Neri R., et al., 2020, A&A, 635, A7](http://dx.doi.org/10.1051/0004-6361/201936988)
[Nightingale J. W., Dye S., Massey R. J., 2018, MNRAS, 478, 4738](http://dx.doi.org/10.1093/mnras/sty1264)
[Nightingale J., et al., 2021, The Journal of Open Source Software, 6, 2825](http://dx.doi.org/10.21105/joss.02825)
Okido D. H., Furlanetto C., Trevisan M., Tergolina M., 2021, in Storchi
Bergmann T., Forman W., Overzier R., Riffel R., eds, Proceedings of the International Astronomical Union Vol. 359, Galaxy Evolution and Feedback across Different Environments. pp 188–189,
[doi:10.1017/S1743921320001945](http://dx.doi.org/10.1017/S1743921320001945)

[Oliver S. J., et al., 2012, MNRAS, 424, 1614](http://dx.doi.org/10.1111/j.1365-2966.2012.20912.x)

[Omont A., et al., 2013, A&A, 551, A115](http://dx.doi.org/10.1051/0004-6361/201220811)

[Pantoni L., et al., 2021, MNRAS, 507, 3998](http://dx.doi.org/10.1093/mnras/stab2346)
[Peng C. Y., Ho L. C., Impey C. D., Rix H.-W., 2002, AJ, 124, 266](http://dx.doi.org/10.1086/340952)
[Peng C. Y., Ho L. C., Impey C. D., Rix H.-W., 2010, AJ, 139, 2097](http://dx.doi.org/10.1088/0004-6256/139/6/2097)
[Penney J. I., et al., 2020, MNRAS, 496, 1565](http://dx.doi.org/10.1093/mnras/staa1582)
Perrotta F., Baccigalupi C., Bartelmann M., De Zotti G., Granato G. L., 2002,

[MNRAS, 329, 445](http://dx.doi.org/10.1046/j.1365-8711.2002.05009.x)

[Pilbratt G. L., et al., 2010, A&A, 518, L1](http://dx.doi.org/10.1051/0004-6361/201014759)

[Planck Collaboration VI 2020, A&A, 641, A6](http://dx.doi.org/10.1051/0004-6361/201833910)
[Ratzlaff K. L., Johnson J. T., 1989, Analytical Chemistry, 61, 1303](http://dx.doi.org/10.1021/ac00186a026)
[Renzini A., 2009, MNRAS, 398, L58](http://dx.doi.org/10.1111/j.1745-3933.2009.00710.x)
[Reuter C., et al., 2020, ApJ, 902, 78](http://dx.doi.org/10.3847/1538-4357/abb599)
[Rowan-Robinson M., et al., 2018, A&A, 619, A169](http://dx.doi.org/10.1051/0004-6361/201832671)
[Shirley R., et al., 2021, MNRAS, 507, 129](http://dx.doi.org/10.1093/mnras/stab1526)
[Speagle J. S., 2020, MNRAS, 493, 3132](http://dx.doi.org/10.1093/mnras/staa278)
[Spilker J. S., et al., 2016, ApJ, 826, 112](http://dx.doi.org/10.3847/0004-637X/826/2/112)
Stanford S. A., Gonzalez A. H., Brodwin M., Gettings D. P., Eisenhardt P.
[R. M., Stern D., Wylezalek D., 2014, ApJS, 213, 25](http://dx.doi.org/10.1088/0067-0049/213/2/25)
[Su T., et al., 2017, MNRAS, 464, 968](http://dx.doi.org/10.1093/mnras/stw2334)
[Sun F., et al., 2021, ApJ, 908, 192](http://dx.doi.org/10.3847/1538-4357/abd6e4)
Surace J. A., Sanders D. B., Vacca W. D., Veilleux S., Mazzarella J. M., 1998,

[ApJ, 492, 116](http://dx.doi.org/10.1086/305028)
[Urquhart S. A., et al., 2022, MNRAS, 511, 3017](http://dx.doi.org/10.1093/mnras/stac150)
[Valiante E., et al., 2016, MNRAS, 462, 3146](http://dx.doi.org/10.1093/mnras/stw1806)
[Vieira J. D., et al., 2010, ApJ, 719, 763](http://dx.doi.org/10.1088/0004-637X/719/1/763)
[Vieira J. D., et al., 2013, Nature, 495, 344](http://dx.doi.org/10.1038/nature12001)
[Viero M. P., et al., 2014, ApJS, 210, 22](http://dx.doi.org/10.1088/0067-0049/210/2/22)
[Wang T., et al., 2018, ApJ, 867, L29](http://dx.doi.org/10.3847/2041-8213/aaeb2c)
[Ward B. A., et al., 2022, MNRAS, 510, 2261](http://dx.doi.org/10.1093/mnras/stab3300)
[Wardlow J. L., et al., 2013, ApJ, 762, 59](http://dx.doi.org/10.1088/0004-637X/762/1/59)
[Watkins A. E., et al., 2022, A&A, 660, A69](http://dx.doi.org/10.1051/0004-6361/202142627)
[Yang C., et al., 2016, A&A, 595, A80](http://dx.doi.org/10.1051/0004-6361/201628160)
[Yang C., et al., 2017, A&A, 608, A144](http://dx.doi.org/10.1051/0004-6361/201731391)
[Yang C., et al., 2019, A&A, 624, A138](http://dx.doi.org/10.1051/0004-6361/201833876)
[Zhang Z.-Y., et al., 2018, MNRAS, 481, 59](http://dx.doi.org/10.1093/mnras/sty2082)


**APPENDIX A:** **THE FULL ‘A’ SAMPLE**

**Figure** **A1.** _From_ _left_ _to_ _right_ _panels:_ Observed _HST_ F110W image, best-fitting surface-brightness model of the lens, residual obtained after the subtraction of the lens model from the image, and SNR map of
the residuals for the A class candidates. The contours in the model images are taken at two levels corresponding to _SNR_ = 5 and 10 (thick curves), and five uniformly spaced levels between the _SNR_ = 10 and the
maximum SNR in the model image (thin curves). The residual map shows the pixel mask (corresponding to the black-shaded regions) adopted for the surface brightness modelling. The residual maps show the
contours of available high-resolution multiwavelength data taken at two levels corresponding to _SNR_ = 5 and 10 (thick curves), and five uniformly spaced levels between the _SNR_ = 10 and the maximum SNR in the
multiwavelength image (thin black curves). The images are oriented such that N is up and E is to the left. For S_55, we show the image and SNR map panels alone since we do not model the lensing galaxy that is
undetected in the _HST_ snapshot.



40


30


20


10







3


3


3


3


3


3



20


15


10


5





0







30


25


20


15


10


5





40


30


20


10





0



0


15


10


5



20


15


10


5





80


60


40


20





30


25


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


25


20


15


10


5





20


15


10


5













25


20


15


10


5








|Col1|HATLASJ000330.6 321136<br>1 arcsec|HATLASJ000330.6 321136|/HerBS155/No.|1 arcsec|1 arcsec|3<br>0|
|---|---|---|---|---|---|---|
||1 arcse<br>HATLASJ000912.7<br>300807|HATLASJ000912.7<br>300807|/SD.v1.70/No.|c<br>1 arcse|c<br>1 arcsec|<br>0<br>3|
||1 arcsec<br>HELMSJ001353.5<br>060200/|HELMSJ001353.5<br>060200/|HeLMS31/No. S|1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ003619.8+002420/|HELMSJ003619.8+002420/|HeLMS14/No. S|1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HERSJ011722.3+005624/H|HERSJ011722.3+005624/H|erS10/No. S6|1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HERSJ012620.5+012950/H|HERSJ012620.5+012950/H|erS5/No. S_7<br>1 arcsec|1 arcsec|1 arcsec|0<br>3|


|Col1|HERMESJ032637 270044/<br>1 arcsec|HERMESJ032637 270044/|HECDFS05/No. S|
|---|---|---|---|
||1 arcsec<br>HERMESJ033732<br>295353/|HERMESJ033732<br>295353/|HECDFS02/No. S|
||1 arcsec<br>HERMESJ103827+581544/|HERMESJ103827+581544/|HLock04/No. S_13|
||1 arcsec<br>HERMESJ110016+571736/|HERMESJ110016+571736/|HLock12/No. S_14|
||1 arcsec<br>HATLASJ114638<br>001132/H|HATLASJ114638<br>001132/H|erBS2/No. S15|
||1 arcsec<br>HATLASJ125126+254928/H|HATLASJ125126+254928/H|erBS52/No. S_16|


|1 arcsec|1 arcsec|3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3|
|---|---|---|
|1 arcsec|1 arcsec|1 arcsec|
|<br>1 arcsec|<br>1 arcsec|<br>1 arcsec|
|1 arcsec|1 arcsec|1 arcsec|
|1 arcsec|1 arcsec<br>ALMA band 6|1 arcsec<br>ALMA band 6|
|1 arcsec|1 arcsec|1 arcsec|

8


6


4


2





30


20


10













40


30


20


10


0


20


15


10


5







30


20


10


0


20


15


10


5







20


15


10


5











60


40


20


0


8


6


4


2



15


10


5









15.0


12.5


10.0


7.5


5.0


2.5















3


3


3


3


3



20


15


10


5









3

|Col1|HATLASJ125760+224558/<br>1 arcsec|HATLASJ125760+224558/|/No. S _17<br>1 arcsec|1 arcsec|1 arcsec|3<br>0|
|---|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ133008+245860/H|HATLASJ133008+245860/H|erBS12/No. S|1 arcsec|1 arcsec<br>ALMA band 7|0<br>3|
||1 arcsec<br>HATLASJ133846+255057/H|HATLASJ133846+255057/H|erBS29/No. S_|1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HERMESJ171451+592634/|HERMESJ171451+592634/|HFLS02/No. S_|1 arcsec|1 arcsec|0<br>3|
||1 arcse<br>HERMESJ171545+601238/|1 arcse<br>HERMESJ171545+601238/|c<br>HFLS08/No. S_22<br>1<br>2<br>1 arcse|c<br>1 arcse|c<br>1 arcsec|<br>0<br>3|
||1 arcsec<br>HATLASJ225844.8<br>295124|HATLASJ225844.8<br>295124|/HerBS26/No.|1 arcsec|1 arcsec|0<br>3|


|Col1|HELMSJ232210.3 033559/<br>1 arcsec|HELMSJ232210.3 033559/|HeLMS19/No. S24|1 arcsec|1 arcsec|3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3<br>3<br>0 S/N<br>3|
|---|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ233037.2<br>331217|HATLASJ233037.2<br>331217|/HerBS123/No. S2|1 arcsec|1 arcsec|1 arcsec|
||1 arcsec<br>HELMSJ001626.0+042613/|HELMSJ001626.0+042613/|HeLMS22/No. S_26|1 arcsec|1 arcsec<br>ALMA band 6<br>ALMA band 7|1 arcsec<br>ALMA band 6<br>ALMA band 7|
||1 arcsec<br>HATLASJ002624.8<br>341737|HATLASJ002624.8<br>341737|/HerBS22/No. S_27|1 arcsec|1 arcsec|1 arcsec|
||1 arcsec<br>HELMSJ004723.6+015751/|1 arcsec<br>HELMSJ004723.6+015751/|<br>HeLMS9/No. S_28<br>1<br>2<br>1 arcsec|<br>1 arcsec|<br>1 arcsec<br>ALMA band 6|<br>1 arcsec<br>ALMA band 6|
||1 arcsec<br>HERSJ012041.6<br>002705/H|HERSJ012041.6<br>002705/H|erS2/No. S_29<br>1 arcsec|1 arcsec|1 arcsec|1 arcsec|



**Figure A1** – _continued_

40


30


20


10







3


3


3


3


3


3



150


125


100


75


50


25



20


15


10


5



3







0





0



8


6


4


2



8


6


4


2


0


30


20


10























30


20


10


0


20


15


10


5











20


15


10


5







0





40


30


20


10


0


20


15


10


5


0







3


0


3


0


3


0


3


0


3


0


3


0



12.5


10.0


7.5


5.0


2.5














|Col1|HATLASJ085112+004934/<br>1 arcsec|HATLASJ085112+004934/|/No. S _30<br>1 arcsec|1 arcsec|1 arcsec|
|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ085359+015537/G<br>4|HATLASJ085359+015537/G|09v1.40/No. S_|1 arcsec|1 arcsec<br>ALMA band 6<br>ALMA band 7|
||1 arcsec<br>HERMESJ104549+574512/<br>2|HERMESJ104549+574512/|HLock06/No. S|5<br>1 arcsec|<br>1 arcsec|
||1 arcsec<br>HERMESJ105551+592845/|HERMESJ105551+592845/|HLock08/No. S|6<br>1 arcsec|1 arcsec|
||1 arcse<br>HERMESJ105751+573026/|1 arcse<br>HERMESJ105751+573026/|c<br>HLock01/No. S_34<br>1<br>2<br>3<br>4<br>5<br>6<br>1 arcse|c<br>1 arcse|c<br>1 arcse<br>SMA 340 GHz|
||1 arcsec<br>HATLASJ132630+334410/N|HATLASJ132630+334410/N|Av1.195/No. S_|<br>1 arcse|c<br>1 arcsec<br>ALMA band 6<br>ALMA band 3|


|Col1|HATLASJ133543+300404/H<br>1 arcse|HATLASJ133543+300404/H|erBS35/No. S _36|4<br>2<br>1 arcsec 1 arcse|c 1 arcse|Col7|
|---|---|---|---|---|---|---|
||1 arcse<br>HATLASJ133543+300404/H|HATLASJ133543+300404/H|c<br>1<br><br>3|c<br>1<br><br>3|c<br>1<br><br>3|c<br>1<br><br>3|
||1 arcsec<br>HATLASJ142140+000448/H|HATLASJ142140+000448/H|erBS140/No. S_3|7<br>1 arcsec<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HATLASJ142140+000448/H|HATLASJ142140+000448/H|||||
||1 arcsec<br>HERMESJ142824+352620/|HERMESJ142824+352620/|HBootes03/No. S|38<br>1 arcsec<br>1 arcsec|1 arcsec<br>ALMA band 6|3<br>0<br>3|
||1 arcsec<br>HERMESJ142824+352620/|HERMESJ142824+352620/|_|_|_|_|
||1 arcsec<br>HATLASJ223753.8<br>305828|HATLASJ223753.8<br>305828|/HerBS68/No. S|39<br>1 arcsec<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HATLASJ223753.8<br>305828|HATLASJ223753.8<br>305828|_|_|_|_|
||1 arcsec<br>HATLASJ225250.7<br>313657|1 arcsec<br>HATLASJ225250.7<br>313657|/HerBS47/No. S_4|0<br>1 arcsec<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HELMSJ233441.0<br>065220/|HELMSJ233441.0<br>065220/|HeLMS1/No. S_41|<br>1 arcsec<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HELMSJ233441.0<br>065220/|HELMSJ233441.0<br>065220/|||||



**Figure A1** – _continued_

3


3


3


3


3


3





3


3


3


3


3


3



60


40


20





3


0


3


0


3


0


3


0


3


0


3


0



0







40


30


20


10


0


15


10


5


0


30


20


10


0


30


20


10


0


30


20


10


0


15.0


12.5


10.0


7.5


5.0


2.5


0.0





40



3


0


3


0


3


0


3


0


3


0


3


0







30


20


10


0

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


10


8


6


4


2


0


25


20


15


10


5


0








































|Col1|HELMSJ233633.5 032119/<br>1 arcsec|Col3|HeLMS41/No. S _4<br>2|2 1<br>1 arcsec 1 arcsec|1 arcsec|
|---|---|---|---|---|---|
||1 arcsec<br>HELMSJ001615.7+032435/|1 arcsec<br>HELMSJ001615.7+032435/|<br>HeLMS13/No. S_4|3<br>1 arcsec<br>1 arcse|c<br>1 arcsec<br>ALMA band 7|
||1 arcsec<br>HELMSJ002220.9<br>015524/|HELMSJ002220.9<br>015524/|HeLMS29/No. S4|4<br>1 arcsec<br>1 arcsec|1 arcsec<br>ALMA band 7|
||1 arcsec<br>HELMSJ002220.9<br>015524/|HELMSJ002220.9<br>015524/|_|_|_|
||1 arcsec<br>HELMSJ003814.1<br>002252/|HELMSJ003814.1<br>002252/|HeLMS24/No. S4|5<br>1 arcsec<br>1 arcsec|1 arcsec<br>ALMA band 7|
||1 arcsec<br>HELMSJ003814.1<br>002252/|HELMSJ003814.1<br>002252/|_<br>|_<br>|_<br>|
||1 arcsec<br>HELMSJ003929.6+002426/|HELMSJ003929.6+002426/|HeLMS11/No. S4|6<br>1 arcsec<br>1 arcsec|1 arcsec<br>ALMA band 7|
||1 arcsec<br>HELMSJ003929.6+002426/|HELMSJ003929.6+002426/|_<br>|_<br>|_<br>|
||1 arcsec<br>HELMSJ004714.2+032454/|1 arcsec<br>HELMSJ004714.2+032454/|HeLMS8/No. S_47|<br>1 arcsec<br>1 arcsec|1 arcsec<br>ALMA band 7|


|Col1|HELMSJ005159.5+062241/<br>1 arcse|Col3|HeLMS18/No. S _48<br>2<br>1<br>3<br>c 1 arcse|c 1 arcse|c|
|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ005724.2<br>273122|1 arcsec<br>HATLASJ005724.2<br>273122|/HerBS60/No. S_49<br>1 arcsec|1 arcsec||
||1 arcsec<br>HERMESJ033211<br>270536/|HERMESJ033211<br>270536/|HECDFS04/No. S|1 arcsec||
||1 arcsec<br>HERMESJ044154<br>540352/|HERMESJ044154<br>540352/|HADFS01/No. S|1 arcsec||
||1 arcsec<br>HATLASJ083932<br>011760/H|HATLASJ083932<br>011760/H|erBS105/No. S|1 arcsec||
||1 arcsec<br>HATLASJ091841+023048/H|1 arcsec<br>HATLASJ091841+023048/H|erBS32/No. S_54<br>1<br>2<br>1 arcsec|1 arcsec||



**Figure A1** – _continued_

|2<br>1 arcsec|1 arcsec|A AL LM MA b ba an nd 4<br>A L M A b a n d 6<br>A d 7<br>1 arcsec|A AL LM MA b ba an nd 4<br>A L M A b a n d 6<br>A d 7|
|---|---|---|---|
|S_62<br>1 arcsec|1 arcsec|1 arcsec<br>SMA 340 GHz|1 arcsec<br>SMA 340 GHz|
|S_63<br>1 arcsec|1 arcsec|1 arcsec<br>ALMA band 6|1 arcsec<br>ALMA band 6|
|_64<br>1 arcsec|1 arcsec|1 arcsec<br>ALMA band 7|1 arcsec<br>ALMA band 7|
|_65<br>1 arcsec|1 arcsec|1 arcsec<br>ALMA band 6<br>ALMA band 8|1 arcsec<br>ALMA band 6<br>ALMA band 8|



**Figure A1** – _continued_
































































|HATLASJ113526 014606/<br>1 arcsec|HerBS10/No. S<br>_|Col3|
|---|---|---|
|1 arcsec<br>HATLASJ115433.6+00504|2/HerBS177/No. S_56<br>1 arcsec|1 arcsec|
|1 arcsec<br>HATLASJ120127.6<br>01404|3/HerBS61/No. S|1 arcsec|
|1 arcsec<br>HATLASJ131611+281220/|HerBS89/No. S_58<br>1 arcsec|1 arcsec<br>N|
|1 arcsec<br>HATLASJ134429+303036/|HerBS1/No. S_59<br>1 arcsec|1 arcsec|
|1 arcs<br>HATLASJ141352<br>000027/|HerBS15/No S|1 arcsec|

36 _E. Borsato et al._


**APPENDIX B:** **FULL CANDIDATES TABLE**


Below, we present the figures and tables that did not enter the full
body of the paper for the sake of readability.
In Table B1, we summarise the properties for all the systems
classified as B, C and D after the inclusion of the multiwavelength
follow-ups and the lens subtraction. Figure B2 shows the candidates
classified as C or D.


**APPENDIX C:** **LENS MODELLING RESULTS**


MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 37


**Table A1.** Structural parameters of the systems classified as A obtained from a parametric fit of their surface brightness distributions.


No. IAU Name Type Components _𝜇_ e _𝑅_ e _𝑛_ _𝑞_ _𝑃𝐴_ _𝑚_ PSF _𝐶_ / _𝑇_ _𝜒_ [2] _𝑁_ dof

[mag arcsec [−][2] ] [arcsec] [deg] [mag]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13)


S_1 HATLASJ000330.6 − 321136 1 Sérsic 20 _._ 69 [+] − [0] 0 _[.]_ _._ [12] 11 0 _._ 36 ± 0 _._ 02 4 _._ 52 [+] − [0] 0 _[.]_ _._ [28] 27 0 _._ 803 ± 0 _._ 009 73 _._ 05 [+] − [0] 0 _[.]_ _._ [96] 95 – 0 _._ 71 ± 0 _._ 05 1.03 35501
Sérsic 23 _._ 39 [+] − [0] 0 _[.]_ _._ [15] 13 1 _._ 17 ± 0 _._ 06 0 _._ 57 ± 0 _._ 05 0 _._ 96 ± 0 _._ 02 0 _._ 003 [+] − [1] 1 _[.]_ _._ [933] 884 – 0 _._ 29 ± 0 _._ 05


Sérsic 21 _._ 63 [+] − [0] 0 _[.]_ _._ [23] 20 1 _._ 16 [+] − [0] 0 _[.]_ _._ [17] 18 3 _._ 96 ± 0 _._ 27 0 _._ 929 ± 0 _._ 006 34 _._ 92 [+] − [1] 1 _[.]_ _._ [39] 42 – 0 _._ 42 [+] − [0] 0 _[.]_ _._ [09] 10
S_2 HATLASJ000912.7 − 300807 1 Sérsic 26 _._ 24 [+] − [0] 0 _[.]_ _._ [14] 12 5 _._ 24 [+] − [0] 0 _[.]_ _._ [19] 18 0 _._ 80 ± 0 _._ 07 0 _._ 27 ± 0 _._ 03 121 _._ 76 [+] − [6] 6 _[.]_ _._ [00] 17 – 0 _._ 018 [+] − [0] 0 _[.]_ _._ [005] 004 1.03 135697
Sérsic 23 _._ 31 [+] − [0] 0 _[.]_ _._ [14] 12 3 _._ 93 ± 0 _._ 11 1 _._ 54 ± 0 _._ 13 0 _._ 78 ± 0 _._ 02 139 _._ 43 [+] − [3] 3 _[.]_ _._ [96] 97 – 0 _._ 56 [+] − [0] 0 _[.]_ _._ [10] 09


S_3 HELMSJ001353.5 − 060200 1 Sérsic 21 _._ 21 [+] − [0] 0 _[.]_ _._ [28] 22 0 _._ 26 [+] − [0] 0 _[.]_ _._ [04] 03 4 _._ 03 ± 0 _._ 60 0 _._ 90 ± 0 _._ 02 20 _._ 44 [+] − [3] 3 _[.]_ _._ [85] 82 – 0 _._ 45 ± 0 _._ 11 1.03 61093
Exp. disk 24 _._ 41 [+] − [0] 0 _[.]_ _._ [22] 18 2 _._ 02 ± 0 _._ 19 [1] 0 _._ 66 ± 0 _._ 05 2 _._ 58 [+] − [4] 4 _[.]_ _._ [59] 42 – 0 _._ 55 ± 0 _._ 11


Sérsic 20 _._ 59 [+] − [0] 0 _[.]_ _._ [23] 19 1 _._ 35 ± 0 _._ 17 1 _._ 26 ± 0 _._ 07 0 _._ 905 ± 0 _._ 005 109 _._ 96 [+] − [1] 1 _[.]_ _._ [05] 06 – 0 _._ 46 [+] − [0] 0 _[.]_ _._ [08] 09
S_4 HELMSJ003619.8 + 002420 1 Sérsic 17 _._ 78 [+] − [0] 0 _[.]_ _._ [16] 14 0 _._ 177 [+] − [0] 0 _[.]_ _._ [006] 005 1 _._ 54 ± 0 _._ 15 0 _._ 90 ± 0 _._ 02 159 _._ 86 [+] − [2] 2 _[.]_ _._ [55] 57 – 0 _._ 11 [+] − [0] 0 _[.]_ _._ [03] 02 1.01 171928
Sérsic 23 _._ 65 [+] − [0] 0 _[.]_ _._ [14] 13 5 _._ 68 ± 0 _._ 17 0 _._ 88 [+] − [0] 0 _[.]_ _._ [08] 07 0 _._ 92 ± 0 _._ 02 128 _._ 85 [+] − [4] 4 _[.]_ _._ [37] 42 – 0 _._ 42 [+] − [0] 0 _[.]_ _._ [08] 07



HERSJ011722.3 + 005624 1

S_6 3



Sérsic 21 _._ 64 [+] − [0] 0 _[.]_ _._ [29] 23 0 _._ 60 [+] − [0] 0 _[.]_ _._ [08] 07 5 _._ 19 [+] − [0] 0 _[.]_ _._ [42] 41 0 _._ 70 ± 0 _._ 02 2 _._ 90 [+] − [1] 1 _[.]_ _._ [96] 92 – 0 _._ 85 [+] − [0] 0 _[.]_ _._ [05] 07 1.01 55924
Gauss 24 _._ 97 [+] − [0] 0 _[.]_ _._ [21] 17 1 _._ 79 ± 0 _._ 16 [0 _._ 5] 0 _._ 83 [+] − [0] 0 _[.]_ _._ [10] 11 180 _._ 53 [+] − [36] 36 _[.]_ _._ [51] 53 – 0 _._ 15 [+] − [0] 0 _[.]_ _._ [07] 05



HERSJ011722.3 + 005624 2 Sérsic 22 _._ 52 [+] − [0] 0 _[.]_ _._ [17] 15 0 _._ 25 ± 0 _._ 02 1 _._ 12 ± 0 _._ 15 0 _._ 93 ± 0 _._ 03 −0 _._ 001 [+] − [3] 3 _[.]_ _._ [108] 000 – [1] 1.01 56315


S_7 HERSJ012620.5 + 012950 1 Sérsic 22 _._ 23 [+] − [0] 0 _[.]_ _._ [31] 24 0 _._ 89 ± 0 _._ 12 5 _._ 86 [+] − [0] 0 _[.]_ _._ [48] 47 0 _._ 70 ± 0 _._ 02 13 _._ 18 [+] − [1] 1 _[.]_ _._ [91] 92 – 0 _._ 66 [+] − [0] 0 _[.]_ _._ [08] 11 1.04 66653
Gauss 21 _._ 72 [+] − [0] 0 _[.]_ _._ [09] 08 0 _._ 76 ± 0 _._ 05 [0 _._ 5] 0 _._ 88 ± 0 _._ 05 74 _._ 75 ± 3 _._ 74 – 0 _._ 34 [+] − [0] 0 _[.]_ _._ [11] 08


S_9 HERMESJ032637 − 270044 1 Sérsic 22 _._ 70 ± 0 _._ 05 1 _._ 01 [+] − [0] 0 _[.]_ _._ [02] 03 5 _._ 73 ± 0 _._ 11 0 _._ 997 [+] − [0] 0 _[.]_ _._ [002] 003 46 _._ 45 [+] − [0] 0 _[.]_ _._ [69] 70 – [1] 1.04 58583


Sérsic 20 _._ 23 [+] − [0] 0 _[.]_ _._ [25] 21 0 _._ 50 ± 0 _._ 09 4 _._ 51 [+] − [0] 0 _[.]_ _._ [37] 38 0 _._ 804 ± 0 _._ 009 53 _._ 64 [+] − [1] 1 _[.]_ _._ [65] 68 – 0 _._ 15 [+] − [0] 0 _[.]_ _._ [06] 05
S_10 HERMESJ033732 − 295353 1 Sérsic 22 _._ 12 [+] − [0] 0 _[.]_ _._ [13] 11 2 _._ 96 [+] − [0] 0 _[.]_ _._ [08] 07 1 _._ 73 ± 0 _._ 15 0 _._ 96 ± 0 _._ 02 149 _._ 69 [+] − [1] 1 _[.]_ _._ [32] 33 – 0 _._ 71 [+] − [0] 0 _[.]_ _._ [05] 06 1.05 177156
Sérsic 20 _._ 61 [+] − [0] 0 _[.]_ _._ [16] 14 0 _._ 83 ± 0 _._ 03 0 _._ 69 ± 0 _._ 06 0 _._ 90 ± 0 _._ 02 54 _._ 94 [+] − [2] 2 _[.]_ _._ [84] 94 – 0 _._ 14 [+] − [0] 0 _[.]_ _._ [03] 02


S_13 HERMESJ103827 + 581544 1 Sérsic 20 _._ 25 [+] − [0] 0 _[.]_ _._ [10] 09 0 _._ 47 ± 0 _._ 03 1 _._ 56 ± 0 _._ 07 0 _._ 762 ± 0 _._ 008 6 _._ 07 ± 0 _._ 82 – 0 _._ 27 ± 0 _._ 03 1.02 107445
Sérsic 22 _._ 65 [+] − [0] 0 _[.]_ _._ [07] 06 2 _._ 56 [+] − [0] 0 _[.]_ _._ [07] 08 1 _._ 07 ± 0 _._ 05 0 _._ 74 ± 0 _._ 01 12 _._ 31 [+] − [1] 1 _[.]_ _._ [06] 07 – 0 _._ 73 ± 0 _._ 03


S_14 HERMESJ110016 + 571736 1 Sérsic 21 _._ 76 ± 0 _._ 04 1 _._ 01 ± 0 _._ 02 2 _._ 68 ± 0 _._ 04 0 _._ 807 ± 0 _._ 004 120 _._ 78 [+] − [0] 0 _[.]_ _._ [60] 59 – [1] 1.06 46997



HATLASJ114638 − 001132 1



S_15



2



Sérsic 20 _._ 30 [+] − [0] 0 _[.]_ _._ [24] 20 0 _._ 19 ± 0 _._ 02 1 _._ 36 ± 0 _._ 17 0 _._ 53 ± 0 _._ 03 50 _._ 27 [+] − [1] 1 _[.]_ _._ [72] 69 – 0 _._ 58 [+] − [0] 0 _[.]_ _._ [08] 09

Sérsic 24 _._ 52 [+] − [0] 0 _[.]_ _._ [16] 13 1 _._ 14 ± 0 _._ 07 0 _._ 45 [+] − [0] 0 _[.]_ _._ [07] 08 0 _._ 81 [+] − [0] 0 _[.]_ _._ [05] 04 53 _._ 88 [+] − [2] 2 _[.]_ _._ [83] 87 – 0 _._ 42 [+] − [0] 0 _[.]_ _._ [09] 08
1.03 44201



HATLASJ114638 − 001132 2 SérsicSérsic 2125 _.._ 1749 [+][+] −− [0][0] 00 _[.][.]_ _.._ [25][14] 2112 02 _.._ 1829 ± ± 0 0 _.._ 0210 31 _._ 26 _._ 73 ± [+] − [0] 0 0 _[.]_ _._ [15] _._ 14 43 00 _.._ 8186 ± ± 0 0 _.._ 0303 128132 _.._ 8615 [+][+] −− [1][1] 11 _[.][.]_ _.._ [77][64] 7566 –– 00 _.._ 2971 [+][+] −− [0][0] 00 _[.][.]_ _.._ [08][07] 0708


S_16 HATLASJ125126 + 254928 1 Sérsic 23 _._ 11 [+] − [0] 0 _[.]_ _._ [06] 05 1 _._ 50 ± 0 _._ 04 7 _._ 96 ± 0 _._ 16 0 _._ 504 ± 0 _._ 005 135 _._ 36 ± 0 _._ 77 – [1] 1.07 50036


S_17 HATLASJ125760 + 224558 1 Sérsic 22 _._ 33 ± 0 _._ 04 1 _._ 13 ± 0 _._ 02 4 _._ 63 ± 0 _._ 08 0 _._ 814 ± 0 _._ 004 6 _._ 39 [+] − [0] 0 _[.]_ _._ [58] 61 – [1] 1.07 50512


S_18 HATLASJ133008 + 245860 1 Sérsic 21 _._ 81 [+] − [0] 0 _[.]_ _._ [30] 24 0 _._ 69 ± 0 _._ 09 6 _._ 34 [+] − [0] 0 _[.]_ _._ [49] 50 0 _._ 80 ± 0 _._ 01 81 _._ 56 [+] − [1] 1 _[.]_ _._ [97] 95 – 0 _._ 83 [+] − [0] 0 _[.]_ _._ [05] 07 1.04 44862
Gauss 22 _._ 85 [+] − [0] 0 _[.]_ _._ [11] 10 0 _._ 83 ± 0 _._ 05 [0 _._ 5] 0 _._ 91 [+] − [0] 0 _[.]_ _._ [05] 06 96 _._ 76 [+] − [10] 11 _[.]_ _._ [85] 16 – 0 _._ 17 [+] − [0] 0 _[.]_ _._ [07] 05


S_19 HATLASJ133846 + 255057 1 Sérsic 23 _._ 46 [+] − [0] 0 _[.]_ _._ [07] 06 1 _._ 11 ± 0 _._ 04 5 _._ 25 [+] − [0] 0 _[.]_ _._ [15] 16 0 _._ 696 ± 0 _._ 007 50 _._ 61 [+] − [0] 0 _[.]_ _._ [87] 90 – [1] 1.04 57037


S_21 HERMESJ171451 + 592634 1 de Vauc. 22 _._ 05 [+] − [0] 0 _[.]_ _._ [05] 04 0 _._ 45 ± 0 _._ 01 [4] 0 _._ 55 ± 0 _._ 01 144 _._ 39 [+] − [1] 1 _[.]_ _._ [69] 64 – [1] 1.10 31356



HERMESJ171545 + 601238 1

S_22 3



Sérsic 22 _._ 47 [+] − [0] 0 _[.]_ _._ [17] 15 0 _._ 56 ± 0 _._ 04 4 _._ 43 [+] − [0] 0 _[.]_ _._ [33] 34 0 _._ 992 [+] − [0] 0 _[.]_ _._ [006] 009 180 _._ 00 [+] − [1] 1 _[.]_ _._ [08] 07 – 0 _._ 17 [+] − [0] 0 _[.]_ _._ [04] 03
PSF – – – – – [24 _._ 97] 0 _._ 0023 ± 0 _._ 0002 1.05 55119
Sérsic 24 _._ 43 ± 0 _._ 08 4 _._ 10 [+] − [0] 0 _[.]_ _._ [14] 13 2 _._ 72 ± 0 _._ 16 0 _._ 69 ± 0 _._ 01 96 _._ 24 [+] − [1] 1 _[.]_ _._ [29] 27 – 0 _._ 83 [+] − [0] 0 _[.]_ _._ [03] 04



HERMESJ171545 + 601238 2 Sérsic 23 _._ 87 [+] − [0] 0 _[.]_ _._ [10] 09 1 _._ 23 ± 0 _._ 06 3 _._ 76 ± 0 _._ 20 0 _._ 39 ± 0 _._ 01 99 _._ 53 [+] − [1] 0 _[.]_ _._ [02] 99 – [1] 1.05 54970



HATLASJ225844.8 − 295124 1



Sérsic 20 _._ 69 [+] − [0] 0 _[.]_ _._ [07] 06 0 _._ 44 [+] − [0] 0 _[.]_ _._ [01] 02 1 _._ 84 ± 0 _._ 06 0 _._ 448 ± 0 _._ 008 145 _._ 47 [+] − [0] 0 _[.]_ _._ [87] 83 – [1]



S_23



HATLASJ225844.8 − 295124 2 Sérsic 22 _._ 59 [+] − [0] 0 _[.]_ _._ [24] 20 0 _._ 61 ± 0 _._ 07 1 _._ 12 ± 0 _._ 15 0 _._ 39 ± 0 _._ 03 58 _._ 30 ± 1 _._ 77 – 0 _._ 10 ± 0 _._ 03



2



1.05 15053



Sérsic 24 _._ 93 [+] − [0] 0 _[.]_ _._ [10] 09 3 _._ 29 [+] − [0] 0 _[.]_ _._ [15] 14 2 _._ 83 [+] − [0] 0 _[.]_ _._ [27] 28 0 _._ 69 [+] − [0] 0 _[.]_ _._ [03] 02 26 _._ 28 [+] − [3] 3 _[.]_ _._ [28] 25 – 0 _._ 90 ± 0 _._ 03



HELMSJ232210.3 − 033559 1

S_24 3



Sérsic 23 _._ 38 [+] − [0] 0 _[.]_ _._ [10] 09 1 _._ 42 ± 0 _._ 08 2 _._ 25 ± 0 _._ 14 0 _._ 963 [+] − [0] 0 _[.]_ _._ [008] 009 80 _._ 29 [+] − [0] 0 _[.]_ _._ [86] 89 – 0 _._ 81 ± 0 _._ 03 1.08 54469
Sérsic 19 _._ 99 [+] − [0] 0 _[.]_ _._ [13] 12 0 _._ 214 ± 0 _._ 008 1 _._ 29 ± 0 _._ 12 0 _._ 57 ± 0 _._ 03 7 _._ 88 [+] − [1] 1 _[.]_ _._ [32] 33 – 0 _._ 19 ± 0 _._ 03



HELMSJ232210.3 − 033559 2 de Vauc. 21 _._ 44 ± 0 _._ 06 0 _._ 134 ± 0 _._ 006 [4] 0 _._ 74 ± 0 _._ 03 64 _._ 64 [+] − [4] 4 _[.]_ _._ [21] 33 – [1] 1.07 50334


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the _Herschel_ detection. Indices 1 and 2 refer to the two components of the lens candidate.
Col. (3): Type of the system. Col. (4): Adopted model for the lens components. Col. (5): Effective surface brightness, i.e., the surface brightness at the effective
radius. Col. (6): Effective radius, i.e., the semi-major axis of the isophote containing half of the light of the component. Col. (7): Sérsic index. Values fixed in
the fit are bracketed. Col. (8): Axial ratio. Col. (9): Position angle. Col. (10): Magnitude of the unresolved component. Col. (11): Relative flux of the component
_𝐶_ / _𝑇_ . Col. (12): Reduced _𝜒_ [2] of the fit. Col. (13): Number of degrees of freedom of the fit.


MNRAS **000**, 1–57 (2022)

38 _E. Borsato et al._


**Table A1** – _continued_


No. IAU Name Type Components _𝜇_ e _𝑅_ e _𝑛_ _𝑞_ _𝑃𝐴_ _𝑚_ PSF _𝐶_ / _𝑇_ _𝜒_ [2] _𝑁_ dof

[mag arcsec [−][2] ] [arcsec] [deg] [mag]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13)



HATLASJ233037.2 − 331217 1

S_25 3



Sérsic 20 _._ 79 [+] − [0] 0 _[.]_ _._ [23] 19 0 _._ 25 ± 0 _._ 02 7 _._ 05 [+] − [0] 0 _[.]_ _._ [58] 57 0 _._ 58 ± 0 _._ 02 75 _._ 25 [+] − [1] 1 _[.]_ _._ [03] 05 – 0 _._ 32 [+] − [0] 0 _[.]_ _._ [07] 06

Sérsic 23 _._ 71 [+] − [0] 0 _[.]_ _._ [12] 10 1 _._ 66 ± 0 _._ 06 1 _._ 44 ± 0 _._ 14 0 _._ 89 ± 0 _._ 03 139 _._ 93 [+] − [3] 3 _[.]_ _._ [41] 29 – 0 _._ 68 [+] − [0] 0 _[.]_ _._ [06] 07 1.05 47114



HATLASJ233037.2 − 331217 2 PSF – – – – – [23 _._ 14] [1]


_Confirmed after the lens subtraction_


S_26 HELMSJ001626.0 + 042613 1 Sérsic 19 _._ 39 ± 0 _._ 05 0 _._ 52 ± 0 _._ 01 4 _._ 23 ± 0 _._ 09 0 _._ 467 ± 0 _._ 004 7 _._ 10 [+] − [0] 0 _[.]_ _._ [26] 25 – 0 _._ 59 ± 0 _._ 03 1.05 55249
Sérsic 22 _._ 22 [+] − [0] 0 _[.]_ _._ [09] 08 1 _._ 83 ± 0 _._ 06 1 _._ 27 ± 0 _._ 08 0 _._ 63 ± 0 _._ 01 162 _._ 98 [+] − [1] 1 _[.]_ _._ [24] 26 – 0 _._ 41 ± 0 _._ 03


S_27 HATLASJ002624.8 − 341737 1 Sérsic 21 _._ 92 [+] − [0] 0 _[.]_ _._ [25] 20 0 _._ 31 ± 0 _._ 03 4 _._ 94 [+] − [0] 0 _[.]_ _._ [51] 52 0 _._ 63 ± 0 _._ 02 172 _._ 06 [+] − [1] 1 _[.]_ _._ [73] 74 – 0 _._ 54 [+] − [0] 0 _[.]_ _._ [08] 09 1.05 52636
Sérsic 24 _._ 33 [+] − [0] 0 _[.]_ _._ [13] 12 1 _._ 08 ± 0 _._ 04 0 _._ 69 [+] − [0] 0 _[.]_ _._ [09] 08 0 _._ 97 [+] − [0] 0 _[.]_ _._ [02] 03 180 _._ 01 ± 1 _._ 36 – 0 _._ 46 [+] − [0] 0 _[.]_ _._ [09] 08



HELMSJ004723.6 + 015751 1

S_28 2



de Vauc. 18 _._ 60 [+] − [0] 0 _[.]_ _._ [30] 23 0 _._ 09 ± 0 _._ 01 [4] 0 _._ 84 [+] − [0] 0 _[.]_ _._ [04] 03 43 _._ 47 [+] − [4] 4 _[.]_ _._ [28] 38 – 0 _._ 11 [+] − [0] 0 _[.]_ _._ [04] 03

Sérsic 21 _._ 92 ± 0 _._ 02 1 _._ 57 ± 0 _._ 02 1 _._ 37 [+] − [0] 0 _[.]_ _._ [08] 07 0 _._ 851 ± 0 _._ 004 165 _._ 60 [+] − [1] 1 _[.]_ _._ [09] 13 – 0 _._ 89 [+] − [0] 0 _[.]_ _._ [03] 04 1.03 58679



HELMSJ004723.6 + 015751 2 Sérsic 22 _._ 17 ± 0 _._ 06 0 _._ 80 ± 0 _._ 02 3 _._ 14 ± 0 _._ 07 0 _._ 856 [+] − [0] 0 _[.]_ _._ [006] 007 79 _._ 44 [+] − [0] 0 _[.]_ _._ [83] 82 – [1]


S_29 HERSJ012041.6 − 002705 1 Sérsic 19 _._ 91 [+] − [0] 0 _[.]_ _._ [20] 17 0 _._ 19 ± 0 _._ 02 4 _._ 39 ± 0 _._ 34 0 _._ 71 ± 0 _._ 01 86 _._ 79 ± 1 _._ 04 – 0 _._ 44 ± 0 _._ 07 1.03 50744
Sérsic 23 _._ 67 [+] − [0] 0 _[.]_ _._ [13] 12 1 _._ 37 [+] − [0] 0 _[.]_ _._ [05] 06 1 _._ 98 ± 0 _._ 18 0 _._ 79 ± 0 _._ 02 3 _._ 03 [+] − [2] 2 _[.]_ _._ [85] 88 – 0 _._ 56 ± 0 _._ 07


Sérsic 20 _._ 24 [+] − [0] 0 _[.]_ _._ [41] 30 0 _._ 27 ± 0 _._ 06 4 _._ 45 [+] − [0] 0 _[.]_ _._ [72] 71 0 _._ 61 ± 0 _._ 02 81 _._ 52 [+] − [1] 1 _[.]_ _._ [84] 83 – 0 _._ 25 [+] − [0] 0 _[.]_ _._ [12] 10
S_30 HATLASJ085112 + 004934 1 Sérsic 21 _._ 51 [+] − [0] 0 _[.]_ _._ [17] 14 0 _._ 78 ± 0 _._ 02 0 _._ 44 ± 0 _._ 04 0 _._ 94 ± 0 _._ 03 158 _._ 68 [+] − [6] 6 _[.]_ _._ [02] 11 – 0 _._ 37 ± 0 _._ 07 1.06 40914

Sérsic 22 _._ 35 [+] − [0] 0 _[.]_ _._ [14] 12 1 _._ 39 ± 0 _._ 04 0 _._ 72 ± 0 _._ 07 0 _._ 55 ± 0 _._ 02 81 _._ 26 [+] − [1] 1 _[.]_ _._ [61] 71 – 0 _._ 38 ± 0 _._ 07


S_31 HATLASJ085359 + 015537 1 Sérsic 22 _._ 69 [+] − [0] 0 _[.]_ _._ [26] 20 0 _._ 45 ± 0 _._ 05 6 _._ 78 ± 0 _._ 96 0 _._ 30 ± 0 _._ 03 117 _._ 52 [+] − [1] 1 _[.]_ _._ [82] 81 – 0 _._ 30 [+] − [0] 0 _[.]_ _._ [08] 07 1.13 22254
Sérsic 26 _._ 34 [+] − [0] 0 _[.]_ _._ [14] 12 2 _._ 34 ± 0 _._ 09 5 _._ 14 ± 0 _._ 48 0 _._ 85 ± 0 _._ 03 156 _._ 50 [+] − [1] 1 _[.]_ _._ [28] 29 – 0 _._ 70 [+] − [0] 0 _[.]_ _._ [07] 08


S_32 HERMESJ104549 + 574512 1 Sérsic 19 _._ 59 [+] − [0] 0 _[.]_ _._ [23] 19 0 _._ 16 ± 0 _._ 02 3 _._ 86 [+] − [0] 0 _[.]_ _._ [40] 39 0 _._ 37 ± 0 _._ 02 121 _._ 59 [+] − [1] 1 _[.]_ _._ [47] 38 – 0 _._ 22 [+] − [0] 0 _[.]_ _._ [06] 05 1.04 60465
Sérsic 21 _._ 54 [+] − [0] 0 _[.]_ _._ [12] 11 0 _._ 64 ± 0 _._ 03 1 _._ 74 ± 0 _._ 17 0 _._ 68 ± 0 _._ 03 89 _._ 59 [+] − [3] 3 _[.]_ _._ [16] 13 – 0 _._ 78 [+] − [0] 0 _[.]_ _._ [05] 06


HERMESJ105551 + 592845 1 Sérsic 22 _._ 62 ± 0 _._ 08 0 _._ 66 ± 0 _._ 03 1 _._ 82 ± 0 _._ 08 0 _._ 762 ± 0 _._ 009 92 _._ 59 ± 0 _._ 85 – [1]

S_33 2 1.15 6328
HERMESJ105551 + 592845 2 Sérsic 21 _._ 85 [+] − [0] 0 _[.]_ _._ [15] 13 0 _._ 28 ± 0 _._ 02 1 _._ 25 ± 0 _._ 12 0 _._ 79 ± 0 _._ 02 123 _._ 08 [+] − [1] 1 _[.]_ _._ [84] 82 – [1]



HERMESJ105751 + 573026 1



Sérsic 20 _._ 36 ± 0 _._ 09 0 _._ 41 ± 0 _._ 02 3 _._ 90 ± 0 _._ 18 0 _._ 752 ± 0 _._ 008 91 _._ 89 [+] − [0] 0 _[.]_ _._ [83] 84 – 0 _._ 27 ± 0 _._ 03

Sérsic 24 _._ 58 ± 0 _._ 07 5 _._ 16 ± 0 _._ 15 2 _._ 63 [+] − [0] 0 _[.]_ _._ [13] 12 0 _._ 74 ± 0 _._ 01 30 _._ 55 [+] − [1] 1 _[.]_ _._ [03] 05 – 0 _._ 73 ± 0 _._ 03



S_34



HERMESJ105751 + 573026 2 de Vauc.Sérsic 1922 _.._ 3080 [+][+] −− [0][0] 00 _[.][.]_ _.._ [27][67] 2242 00 _._ 10 _._ 43 ± [+] − [0] 0 0 _[.]_ _._ [23] _._ 21 02 5 _._ 95[4 [+] − [2] ] 2 _[.]_ _._ [42] 72 00 _._ 37 _._ 76 ± [+] − [0] 0 0 _[.]_ _._ [12] _._ 13 04 3294 _.._ 2368 [+][+] −− [4][7] 47 _[.][.]_ _.._ [35][37] 5346 –– 00 _.._ 5842 [+][+] −− [0][0] 00 _[.][.]_ _.._ [36][24] 2436


2

HERMESJ105751 + 573026 3 Sérsic 20 _._ 72 [+] − [0] 0 _[.]_ _._ [15] 13 0 _._ 137 ± 0 _._ 009 3 _._ 63 [+] − [0] 0 _[.]_ _._ [31] 32 0 _._ 82 ± 0 _._ 02 74 _._ 54 [+] − [1] 1 _[.]_ _._ [82] 84 – [1]


HERMESJ105751 + 573026 4 de Vauc. 21 _._ 16 ± 0 _._ 05 0 _._ 220 ± 0 _._ 007 [4] 0 _._ 61 ± 0 _._ 02 100 _._ 13 [+] − [2] 2 _[.]_ _._ [05] 07 – [1]


HERMESJ105751 + 573026 5 Sérsic 20 _._ 30 [+] − [0] 0 _[.]_ _._ [13] 12 0 _._ 131 [+] − [0] 0 _[.]_ _._ [008] 007 3 _._ 11 ± 0 _._ 23 0 _._ 89 ± 0 _._ 01 175 _._ 89 [+] − [1] 1 _[.]_ _._ [42] 45 – [1]


HERMESJ105751 + 573026 6 PSF – – – – – [23 _._ 60] [1]



1.11 31547



S_35 HATLASJ132630 + 334410 1 Sérsic 23 _._ 80 ± 0 _._ 04 2 _._ 53 ± 0 _._ 05 5 _._ 73 ± 0 _._ 09 0 _._ 595 ± 0 _._ 004 72 _._ 04 [+] − [0] 0 _[.]_ _._ [57] 59 – [1] 1.05 39273



HATLASJ133543 + 300404 1



Sérsic 22 _._ 42 ± 0 _._ 08 0 _._ 65 ± 0 _._ 03 0 _._ 88 ± 0 _._ 04 0 _._ 902 ± 0 _._ 009 127 _._ 84 ± 0 _._ 89 – 0 _._ 954 ± 0 _._ 005


PSF – – – – – [24 _._ 11] 0 _._ 046 ± 0 _._ 005



1.03 41523



S_36



HATLASJ133543 + 300404 2 2 Sérsic 21 _._ 90 [+] − [0] 0 _[.]_ _._ [09] 08 0 _._ 41 ± 0 _._ 02 4 _._ 97 [+] − [0] 0 _[.]_ _._ [23] 24 0 _._ 567 ± 0 _._ 010 24 _._ 77 [+] − [0] 0 _[.]_ _._ [94] 95 – [1]



HATLASJ133543 + 300404 3 Sérsic 23 _._ 50 ± 0 _._ 06 1 _._ 10 ± 0 _._ 03 5 _._ 58 ± 0 _._ 15 0 _._ 844 ± 0 _._ 007 64 _._ 17 [+] − [0] 0 _[.]_ _._ [92] 94 – [1]


HATLASJ133543 + 300404 4 Sérsic 23 _._ 58 [+] − [0] 0 _[.]_ _._ [07] 06 1 _._ 02 ± 0 _._ 04 6 _._ 21 ± 0 _._ 21 0 _._ 609 ± 0 _._ 008 165 _._ 10 [+] − [0] 0 _[.]_ _._ [80] 84 – [1]


S_37 HATLASJ142140 + 000448 1 Sérsic 21 _._ 27 [+] − [0] 0 _[.]_ _._ [07] 06 0 _._ 38 ± 0 _._ 01 2 _._ 28 ± 0 _._ 05 0 _._ 925 ± 0 _._ 005 0 _._ 67 ± 0 _._ 77 – [1] 1.11 44658


S_38 HERMESJ142824 + 352620 1 Sérsic 21 _._ 47 [+] − [0] 0 _[.]_ _._ [08] 07 0 _._ 49 ± 0 _._ 02 2 _._ 43 [+] − [0] 0 _[.]_ _._ [10] 09 0 _._ 487 ± 0 _._ 008 92 _._ 76 [+] − [0] 0 _[.]_ _._ [89] 91 – [1] 1.17 7204


S_39 HATLASJ223753.8 − 305828 1 Sérsic 21 _._ 81 ± 0 _._ 05 0 _._ 72 ± 0 _._ 02 5 _._ 03 [+] − [0] 0 _[.]_ _._ [10] 09 0 _._ 940 ± 0 _._ 005 87 _._ 28 [+] − [0] 0 _[.]_ _._ [70] 71 – [1] 1.03 63365


S_40 HATLASJ225250.7 − 313657 1 Sérsic 22 _._ 23 [+] − [0] 0 _[.]_ _._ [12] 10 0 _._ 40 ± 0 _._ 02 6 _._ 21 ± 0 _._ 40 0 _._ 53 ± 0 _._ 01 75 _._ 70 [+] − [1] 1 _[.]_ _._ [21] 25 – [1] 1.04 34943


S_41 HELMSJ233441.0 − 065220 1 Sérsic 19 _._ 47 [+] − [0] 0 _[.]_ _._ [20] 17 0 _._ 28 ± 0 _._ 02 1 _._ 14 ± 0 _._ 09 0 _._ 38 ± 0 _._ 01 22 _._ 16 [+] − [1] 1 _[.]_ _._ [00] 01 – 0 _._ 49 [+] − [0] 0 _[.]_ _._ [07] 08 1.57 35357
Sérsic 22 _._ 59 [+] − [0] 0 _[.]_ _._ [15] 13 1 _._ 00 ± 0 _._ 06 0 _._ 62 ± 0 _._ 06 0 _._ 68 ± 0 _._ 03 167 _._ 72 [+] − [2] 2 _[.]_ _._ [29] 37 – 0 _._ 51 [+] − [0] 0 _[.]_ _._ [08] 07


MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 39





3


3


3


3


3


3


3


3


3


3



8


6


4


2



3



30


20


10







0



20


15


10


5



20


15


10


5


0


30


20


10


0







7.5


5.0


2.5



30


20


10





7.5


5.0


2.5









0





8


6


4


2





7.5


5.0


2.5







20


15


10


5







8


6


4


2


0


8


6


4


2







8


6


4


2









7.5


5.0


2.5



30


20


10



20


10



0



20


10















20


10







8


6


4


2






|Col1|HELMSJ000215.9012829/HeL<br>1 arcsec|HELMSJ000215.9012829/HeL|MS3/No. S _66<br>4 3<br>2<br>1<br>1 arcsec|1 arcsec|3<br>0|
|---|---|---|---|---|---|
||1 arcsec<br>HELMSJ001800.1<br>060235/HeL|HELMSJ001800.1<br>060235/HeL|MS21/No. S_67|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ002208.1+034044/HeL|HELMSJ002208.1+034044/HeL|MS38/No. S_68|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ002533.5<br>333825/He|HATLASJ002533.5<br>333825/He|rBS87/No. S_69|1 arcsec|0<br>3|
||1 arcsec<br>HERMESJ002906<br>421419/HEL|1 arcsec<br>HERMESJ002906<br>421419/HEL|AISS01/No. S_70<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ003207.7<br>303724/He|HATLASJ003207.7<br>303724/He|rBS56/No. S_71|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ004747.1+061444/HeL|HELMSJ004747.1+061444/HeL|MS26/No. S_73|1 arcsec|0<br>3|
||1 arcsec<br>HERSJ010301.2<br>003301/HerS|HERSJ010301.2<br>003301/HerS|6/No. S_74|1 arcsec|0<br>3|
||1 arcsec<br>HERSJ011640.1<br>000454/HerS|1 arcsec<br>HERSJ011640.1<br>000454/HerS|4/No. S_75<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ012415.9<br>310500/He|1 arcsec<br>HATLASJ012415.9<br>310500/He|rBS69/No. S_76<br>1 arcsec|1 arcsec|0<br>3|


|Col1|Col2|Col3|2|Col5|Col6|
|---|---|---|---|---|---|
||1 arcsec<br>HERSJ012521.0+011724/HerS|HERSJ012521.0+011724/HerS|13/No. S_77<br>1 arcsec|1<br>1 arcsec|3<br>0<br>3|
||1 arcsec<br>HERSJ012546.3<br>001143/HerS|HERSJ012546.3<br>001143/HerS|12/No. S_78<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HERSJ012754.1+004940/HerS|HERSJ012754.1+004940/HerS|3/No. S_79<br>1<br>2<br>3<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HATLASJ012853.0<br>332719/He|HATLASJ012853.0<br>332719/He|rBS73/No. S_80|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HATLASJ013840.5<br>281855/He|1 arcsec<br>HATLASJ013840.5<br>281855/He|rBS14/No. S_81<br>1 arcsec|1 arcsec<br>ALMA band 6|3<br>0<br>3|
||1 arcsec<br>HATLASJ013951.9<br>321446/He|HATLASJ013951.9<br>321446/He|rBS55/No. S_82|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HERSJ021402.6<br>004612/HerS|HERSJ021402.6<br>004612/HerS|17/No. S_83<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HERSJ021434.4+005926/HerS|HERSJ021434.4+005926/HerS|16/No. S_84<br>1 arcsec|1 arcsec|3<br>0<br>3|
||1 arcsec<br>HERMESJ022017<br>060143/HXM|1 arcsec<br>HERMESJ022017<br>060143/HXM|M01/No. S_85<br>1<br>2<br>1 arcsec|1 arcsec<br>ALMA band 6<br>ALMA band 7|3<br>0<br>3|
||1 arcsec<br>HERMESJ022135<br>062617/HXM|1 arcsec<br>HERMESJ022135<br>062617/HXM|M03/No. S_88<br>1 arcsec|1 arcsec<br>ALMA band 7|3<br>0<br>3|



**Figure B1.** _From left to right panels:_ Observed _HST_ F110W image, best-fitting surface-brightness model of the lens and SNR map of the residuals for the B class
candidates. The contours in the model images are taken at two levels corresponding to _SNR_ = 5 and 10 (thick curves), and five uniformly spaced levels between
the _SNR_ = 10 and the maximum SNR in the model image (thin curves). The residual maps show the contours of available high-resolution multiwavelength data
taken at two levels corresponding to _SNR_ = 5 and 10 (thick curves), and five uniformly spaced levels between the _SNR_ = 10 and the maximum SNR in the
multiwavelength image (thin black curves). The images are oriented such that N is up and E is to the left.


MNRAS **000**, 1–57 (2022)

40 _E. Borsato et al._


30


20


10







3


3


3


3


3


3


3


3


3


3



30


20


10





3


3


3


3


3


3


3


3


3


3



30


20


10



0



0



0


8


6


4


2





15


10


5











0





15



30


20


10







10


5







0



0



30


20


10



7.5


5.0


2.5



0



30


20


10



10


5





0



0



30


20


10



30


20


10



0



0



20


10



10


5





0



30


20


10





30


20


10





0







0



15





10


5







10


5









0



0





15


10


5





0


|Col1|HERMESJ045058531654/HAD<br>1 arcsec|Col3|FS03/No. S _91<br>1 arcsec|ALMA band 7<br>1 arcsec|3<br>0|
|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ084958+010713/HerB|HATLASJ084958+010713/HerB|S157/No. S93|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ090453.2+022017/He|HATLASJ090453.2+022017/He|rBS183/No. S_94|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ091331<br>003644/SDP|HATLASJ091331<br>003644/SDP|44/No. S_95|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ092136+000132/HerB|HATLASJ092136+000132/HerB|S91/No. S_96<br>1<br>2<br>3<br>4<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ092409<br>005018/HerB|HATLASJ092409<br>005018/HerB|S185/No. S_97|1 arcsec|0<br>3|
||1 arcsec<br>HERMESJ103618+585454/HLo|HERMESJ103618+585454/HLo|ck05/No. S_98|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ113804<br>011736/HerB|HATLASJ113804<br>011736/HerB|S96/No. S_99<br>1<br>2<br>3<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ113833.3+004909/He|HATLASJ113833.3+004909/He|rBS100/No. S_10|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ113841<br>020237/<br>/No|HATLASJ113841<br>020237/<br>/No|. S101|1 arcsec|0<br>3|


|Col1|HATLASJ115112012638/HerB<br>1 arcsec|Col3|S53/No. S _102<br>1 arcsec|1 arcsec|3<br>0|
|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ115120<br>003322/<br>/No|HATLASJ115120<br>003322/<br>/No|. S_103<br>1<br>2<br>3<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ120127.8<br>021648/<br>/|HATLASJ120127.8<br>021648/<br>/|No. S_104<br>1<br>2<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ120319.1<br>011253/He|HATLASJ120319.1<br>011253/He|rBS50/No. S_105|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ121301.5<br>004922/He|HATLASJ121301.5<br>004922/He|rBS48/No. S_106|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ121334.9<br>020323/<br>/|HATLASJ121334.9<br>020323/<br>/|No. S_107<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ121542.7<br>005220/He|HATLASJ121542.7<br>005220/He|rBS62/No. S_108|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ130054+260303/HerB|HATLASJ130054+260303/HerB|S129/No. S_109|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ131322+285836/<br>/No|HATLASJ131322+285836/<br>/No|. S_110<br>1<br>2<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ134159+292833/<br>/No|HATLASJ134159+292833/<br>/No|. S_111<br>1 arcsec|1 arcsec|0<br>3|



**Figure B1** – _continued_



MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 41


**Table A1** – _continued_


No. IAU Name Type Components _𝜇_ e _𝑅_ e _𝑛_ _𝑞_ _𝑃𝐴_ _𝑚_ PSF _𝐶_ / _𝑇_ _𝜒_ [2] _𝑁_ dof

[mag arcsec [−][2] ] [arcsec] [deg] [mag]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13)



HELMSJ233633.5 − 032119 1

S_42 2



Sérsic 18 _._ 38 ± 0 _._ 05 0 _._ 332 ± 0 _._ 009 2 _._ 82 ± 0 _._ 06 0 _._ 577 [+] − [0] 0 _[.]_ _._ [004] 003 42 _._ 72 [+] − [0] 0 _[.]_ _._ [24] 25 – 0 _._ 34 ± 0 _._ 02

Sérsic 21 _._ 94 ± 0 _._ 04 2 _._ 55 [+] − [0] 0 _[.]_ _._ [03] 04 1 _._ 25 ± 0 _._ 04 0 _._ 738 ± 0 _._ 006 46 _._ 04 ± 0 _._ 84 – 0 _._ 66 ± 0 _._ 02 1.06 58206



HELMSJ233633.5 − 032119 2 Sérsic 23 _._ 16 [+] − [0] 0 _[.]_ _._ [06] 05 1 _._ 79 ± 0 _._ 04 2 _._ 21 ± 0 _._ 04 0 _._ 723 ± 0 _._ 005 160 _._ 63 [+] − [0] 0 _[.]_ _._ [74] 75 – [1]


_Confirmed through sub-mm/mm follow-up_


S_43 HELMSJ001615.7 + 032435 1 Sérsic 24 _._ 18 [+] − [0] 0 _[.]_ _._ [31] 25 3 _._ 46 [+] − [0] 0 _[.]_ _._ [45] 44 7 _._ 32 [+] − [0] 0 _[.]_ _._ [38] 39 0 _._ 579 [+] − [0] 0 _[.]_ _._ [007] 006 31 _._ 91 [+] − [0] 0 _[.]_ _._ [67] 65 – 0 _._ 86 [+] − [0] 0 _[.]_ _._ [04] 06 1.09 57290
Gauss 24 _._ 61 ± 0 _._ 09 3 _._ 25 ± 0 _._ 21 [0 _._ 5] 0 _._ 50 ± 0 _._ 07 17 _._ 05 [+] − [3] 3 _[.]_ _._ [68] 72 – 0 _._ 14 [+] − [0] 0 _[.]_ _._ [06] 04


S_44 HELMSJ002220.9 − 015524 1 Sérsic 25 _._ 43 [+] − [0] 0 _[.]_ _._ [10] 09 2 _._ 09 ± 0 _._ 10 3 _._ 77 [+] − [0] 0 _[.]_ _._ [19] 20 0 _._ 58 ± 0 _._ 01 98 _._ 62 ± 0 _._ 99 – [1] 1.13 37251


S_45 HELMSJ003814.1 − 002252 1 PSF – – – – – [22 _._ 45] [1] 1.04 18416


S_47 HELMSJ004714.2 + 032454 1 Sérsic 20 _._ 79 [+] − [0] 0 _[.]_ _._ [18] 15 0 _._ 20 ± 0 _._ 02 0 _._ 60 ± 0 _._ 10 0 _._ 75 ± 0 _._ 03 103 _._ 11 [+] − [4] 4 _[.]_ _._ [11] 17 – 0 _._ 17 [+] − [0] 0 _[.]_ _._ [06] 05 1.01 26442
Exp. disk 23 _._ 42 [+] − [0] 0 _[.]_ _._ [19] 17 1 _._ 47 [+] − [0] 0 _[.]_ _._ [14] 13 [1] 0 _._ 60 [+] − [0] 0 _[.]_ _._ [04] 05 111 _._ 21 [+] − [4] 4 _[.]_ _._ [52] 42 – 0 _._ 83 [+] − [0] 0 _[.]_ _._ [05] 06



HELMSJ005159.5 + 062241 1



Sérsic 18 _._ 59 [+] − [0] 0 _[.]_ _._ [21] 17 0 _._ 113 [+] − [0] 0 _[.]_ _._ [009] 010 2 _._ 28 ± 0 _._ 18 0 _._ 77 ± 0 _._ 01 119 _._ 44 ± 1 _._ 05 – 0 _._ 14 ± 0 _._ 03

Sérsic 23 _._ 10 [+] − [0] 0 _[.]_ _._ [08] 07 2 _._ 10 ± 0 _._ 06 1 _._ 95 [+] − [0] 0 _[.]_ _._ [10] 09 0 _._ 96 ± 0 _._ 01 9 _._ 11 [+] − [1] 1 _[.]_ _._ [24] 22 – 0 _._ 86 ± 0 _._ 03



S_48



HELMSJ005159.5 + 062241 2 2 de Vauc. 20 _._ 48 ± 0 _._ 03 0 _._ 201 ± 0 _._ 004 [4] 0 _._ 76 ± 0 _._ 01 173 _._ 86 [+] − [1] 1 _[.]_ _._ [76] 70 – [1]



1.03 48792



HELMSJ005159.5 + 062241 3 SérsicPSF 24 _._ 00 – [+] − [0] 0 _[.]_ _._ [07] 06 1 _._ 92 ± – 0 _._ 06 1 _._ 33 ± – 0 _._ 04 0 _._ 703 – [+] − [0] 0 _[.]_ _._ [007] 008 37 _._ 42 – [+] − [0] 0 _[.]_ _._ [90] 87 [22 – _._ 52] 00 _.._ 899101 [+][+] −− [0][0] 00 _[.][.]_ _.._ [008][009] 009008


S_49 HATLASJ005724.2 − 273122 1 Sérsic 24 _._ 83 [+] − [0] 0 _[.]_ _._ [07] 06 1 _._ 46 ± 0 _._ 05 9 _._ 11 ± 0 _._ 30 0 _._ 858 ± 0 _._ 008 126 _._ 93 [+] − [0] 0 _[.]_ _._ [84] 83 – [1] 1.05 37643


S_51 HERMESJ033211 − 270536 1 PSF – – – – – [23 _._ 01] [1] 1.07 9735


S_52 HERMESJ044154 − 540352 1 Sérsic 21 _._ 75 ± 0 _._ 06 0 _._ 54 ± 0 _._ 02 7 _._ 49 ± 0 _._ 17 0 _._ 783 ± 0 _._ 007 9 _._ 27 ± 0 _._ 86 – [1] 1.03 44932



HATLASJ091841 + 023048 1

S_54 2



Sérsic 20 _._ 11 [+] − [0] 0 _[.]_ _._ [34] 27 0 _._ 11 ± 0 _._ 02 1 _._ 83 [+] − [0] 0 _[.]_ _._ [30] 31 0 _._ 69 ± 0 _._ 03 152 _._ 52 [+] − [1] 1 _[.]_ _._ [94] 93 – 0 _._ 19 [+] − [0] 0 _[.]_ _._ [07] 06

Sérsic 25 _._ 92 [+] − [0] 0 _[.]_ _._ [14] 12 2 _._ 99 ± 0 _._ 14 2 _._ 44 ± 0 _._ 20 0 _._ 76 ± 0 _._ 02 70 _._ 78 [+] − [1] 1 _[.]_ _._ [87] 88 – 0 _._ 81 [+] − [0] 0 _[.]_ _._ [06] 07 1.07 43760



HATLASJ091841 + 023048 2 de Vauc. 21 _._ 80 ± 0 _._ 06 0 _._ 155 ± 0 _._ 006 [4] 0 _._ 91 ± 0 _._ 03 115 _._ 92 [+] − [4] 4 _[.]_ _._ [12] 11 – [1]


S_56 HATLASJ115433.6 + 005042 1 Sérsic 21 _._ 10 [+] − [0] 0 _[.]_ _._ [08] 07 0 _._ 48 ± 0 _._ 02 1 _._ 83 ± 0 _._ 08 0 _._ 337 ± 0 _._ 009 169 _._ 27 [+] − [0] 0 _[.]_ _._ [85] 87 – [1] 1.01 34603


S_57 HATLASJ120127.6 − 014043 1 Sérsic 25 _._ 61 [+] − [0] 0 _[.]_ _._ [35] 26 1 _._ 51 ± 0 _._ 23 1 _._ 00 ± 0 _._ 18 0 _._ 74 ± 0 _._ 03 42 _._ 98 [+] − [1] 1 _[.]_ _._ [91] 83 – 0 _._ 25 [+] − [0] 0 _[.]_ _._ [09] 08 1.06 28398
Sérsic 19 _._ 56 [+] − [0] 0 _[.]_ _._ [14] 12 0 _._ 225 ± 0 _._ 009 2 _._ 12 ± 0 _._ 20 0 _._ 27 ± 0 _._ 03 20 _._ 79 [+] − [1] 1 _[.]_ _._ [31] 29 – 0 _._ 75 [+] − [0] 0 _[.]_ _._ [08] 09


S_58 HATLASJ131611 + 281220 1 Sérsic 22 _._ 68 [+] − [0] 0 _[.]_ _._ [15] 13 0 _._ 45 ± 0 _._ 03 5 _._ 08 [+] − [0] 0 _[.]_ _._ [44] 43 0 _._ 40 ± 0 _._ 02 1 _._ 47 [+] − [1] 1 _[.]_ _._ [77] 73 – [1] 1.02 28595


S_59 HATLASJ134429 + 303036 1 Sérsic 19 _._ 44 [+] − [0] 0 _[.]_ _._ [37] 28 0 _._ 20 ± 0 _._ 03 2 _._ 50 ± 0 _._ 29 0 _._ 65 ± 0 _._ 01 161 _._ 16 [+] − [2] 2 _[.]_ _._ [23] 21 – 0 _._ 54 [+] − [0] 0 _[.]_ _._ [13] 14 1.04 48806
Exp. disk 22 _._ 71 [+] − [0] 0 _[.]_ _._ [20] 16 1 _._ 64 ± 0 _._ 15 [1] 0 _._ 26 [+] − [0] 0 _[.]_ _._ [04] 05 173 _._ 10 [+] − [4] 4 _[.]_ _._ [55] 49 – 0 _._ 46 [+] − [0] 0 _[.]_ _._ [14] 13



HATLASJ141352 − 000027 1



Sérsic 20 _._ 47 [+] − [0] 0 _[.]_ _._ [18] 15 0 _._ 51 ± 0 _._ 05 3 _._ 36 [+] − [0] 0 _[.]_ _._ [21] 22 0 _._ 825 ± 0 _._ 006 83 _._ 00 ± 1 _._ 08 – 0 _._ 55 [+] − [0] 0 _[.]_ _._ [07] 08 1.01 73852
Exp. disk 23 _._ 99 ± 0 _._ 11 2 _._ 87 ± 0 _._ 17 [1] 0 _._ 96 ± 0 _._ 03 −0 _._ 01 [+] − [4] 4 _[.]_ _._ [33] 12 – 0 _._ 45 [+] − [0] 0 _[.]_ _._ [08] 07



S_60



3

HATLASJ141352 − 000027 2 Sérsic 21 _._ 05 ± 0 _._ 08 0 _._ 31 ± 0 _._ 01 3 _._ 64 [+] − [0] 0 _[.]_ _._ [17] 16 0 _._ 536 ± 0 _._ 010 148 _._ 77 [+] − [0] 0 _[.]_ _._ [88] 89 – [1] 1.01 63073


HATLASJ141352 − 000027 3 Sérsic 21 _._ 69 ± 0 _._ 05 0 _._ 68 ± 0 _._ 02 4 _._ 91 ± 0 _._ 10 0 _._ 866 ± 0 _._ 005 41 _._ 57 [+] − [0] 0 _[.]_ _._ [79] 75 – [1] 1.01 64764



HATLASJ142414 + 022304 1

S_61 2



Sérsic 24 _._ 20 [+] − [0] 0 _[.]_ _._ [07] 06 1 _._ 49 ± 0 _._ 05 3 _._ 76 ± 0 _._ 11 0 _._ 910 ± 0 _._ 007 15 _._ 97 [+] − [0] 0 _[.]_ _._ [94] 89 – 0 _._ 880 [+] − [0] 0 _[.]_ _._ [009] 010

PSF – – – – – [22 _._ 25] 0 _._ 120 [+] − [0] 0 _[.]_ _._ [010] 009 1.04 22914



HATLASJ142414 + 022304 2 Sérsic 24 _._ 59 [+] − [0] 0 _[.]_ _._ [10] 09 1 _._ 13 ± 0 _._ 06 7 _._ 02 ± 0 _._ 36 0 _._ 68 ± 0 _._ 01 149 _._ 22 [+] − [1] 0 _[.]_ _._ [02] 98 – [1]


S_62 HATLASJ230815.5 − 343801 1 Sérsic 22 _._ 86 [+] − [0] 0 _[.]_ _._ [21] 17 0 _._ 56 ± 0 _._ 05 8 _._ 73 [+] − [0] 0 _[.]_ _._ [65] 69 0 _._ 89 ± 0 _._ 01 157 _._ 26 ± 1 _._ 05 – 0 _._ 76 [+] − [0] 0 _[.]_ _._ [05] 06 1.13 21244
Sérsic 22 _._ 89 [+] − [0] 0 _[.]_ _._ [14] 13 0 _._ 75 ± 0 _._ 03 0 _._ 52 ± 0 _._ 07 0 _._ 56 [+] − [0] 0 _[.]_ _._ [03] 04 7 _._ 75 [+] − [1] 1 _[.]_ _._ [49] 48 – 0 _._ 24 [+] − [0] 0 _[.]_ _._ [06] 05


S_63 HELMSJ232439.5 − 043936 1 Sérsic 21 _._ 14 [+] − [0] 0 _[.]_ _._ [22] 18 0 _._ 27 [+] − [0] 0 _[.]_ _._ [02] 03 3 _._ 26 ± 0 _._ 24 0 _._ 98 ± 0 _._ 01 89 _._ 07 [+] − [1] 1 _[.]_ _._ [07] 03 – 0 _._ 67 [+] − [0] 0 _[.]_ _._ [06] 08 1.06 53698
Sérsic 23 _._ 95 [+] − [0] 0 _[.]_ _._ [13] 12 1 _._ 10 ± 0 _._ 04 1 _._ 61 ± 0 _._ 18 0 _._ 52 ± 0 _._ 03 129 _._ 07 [+] − [1] 1 _[.]_ _._ [13] 16 – 0 _._ 33 [+] − [0] 0 _[.]_ _._ [08] 06


S_64 HELMSJ233620.8 − 060828 1 Sérsic 20 _._ 53 ± 0 _._ 05 0 _._ 64 ± 0 _._ 02 4 _._ 76 [+] − [0] 0 _[.]_ _._ [10] 09 0 _._ 878 ± 0 _._ 004 52 _._ 62 ± 0 _._ 24 – 0 _._ 85 ± 0 _._ 02 1.04 27656
Sérsic 22 _._ 22 [+] − [0] 0 _[.]_ _._ [12] 10 0 _._ 96 ± 0 _._ 04 0 _._ 87 ± 0 _._ 08 0 _._ 73 ± 0 _._ 03 127 _._ 25 [+] − [3] 3 _[.]_ _._ [16] 17 – 0 _._ 15 ± 0 _._ 02


MNRAS **000**, 1–57 (2022)

42 _E. Borsato et al._


30


20



3


3


3


3


3


3


3


3


3


3



20


15


10


5





3


3


3


3


3


3


3


3


3


3





30


20


10



10





0



0



30


20


10





30


20


10





0



0



15


10


5



30


20


10







0



0



15


10


5





40


20



0











20


15


10


5


0


20


15


10


5







30


20


10











0





10


5









0



30


20


10





7.5


5.0


2.5





0









15



10


5



10


5



0



0



10.0


7.5


5.0


2.5





10


5



30


20


10



0





0




|Col1|HATLASJ141833+010212/HerB<br>1 arcsec|HATLASJ141833+010212/HerB|S110/No. S _112|1 arcsec|3<br>0|
|---|---|---|---|---|---|
||1 arcsec<br>HERMESJ142201+533214/HEG|HERMESJ142201+533214/HEG|S01/No. S_113|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ142318.3+013913/<br>/|HATLASJ142318.3+013913/<br>/|No. S_114<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ143203<br>005219/<br>/No|HATLASJ143203<br>005219/<br>/No|. S_115<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HERMESJ143331+345440/HBo|1 arcsec<br>HERMESJ143331+345440/HBo|otes01/No. S_116<br>1 arcsec|1 arcsec<br>SMA 340 GHz|0<br>3|
||1 arcsec<br>HATLASJ144243+015506/HerB|HATLASJ144243+015506/HerB|S153/No. S_117|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ144715<br>012114/<br>/No|HATLASJ144715<br>012114/<br>/No|. S_118<br>1<br>2<br>3<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ223942.4<br>333304/He|HATLASJ223942.4<br>333304/He|rBS111/No. S_12|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ224026.5<br>315154/He|HATLASJ224026.5<br>315154/He|rBS148/No. S_12|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ224759.6<br>310134/He|HATLASJ224759.6<br>310134/He|rBS141/No. S_12|1 arcsec|0<br>3|


|Col1|HATLASJ224805.3335820/He<br>1 arcsec|HATLASJ224805.3335820/He|rBS33/No. S _123|1 arcsec|3<br>0|
|---|---|---|---|---|---|
||1 arcsec<br>HATLASJ225045.5<br>304719/He|HATLASJ225045.5<br>304719/He|rBS168/No. S_124|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ230546.2<br>331038/He|HATLASJ230546.2<br>331038/He|rBS49/No. S_125|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ231447.5<br>045658/HeL<br>~~1~~|HELMSJ231447.5<br>045658/HeL|MS44/No. S_126|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ232210.9<br>333749/He|1 arcsec<br>HATLASJ232210.9<br>333749/He|2<br>rBS146/No. S_127<br>1<br>2<br>1 arcsec|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ232531.3<br>302235/He|HATLASJ232531.3<br>302235/He|rBS17/No. S_128|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ232617.5<br>025319/HeL|HELMSJ232617.5<br>025319/HeL|MS51/No. S_129|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ232831.8<br>004035/HeL|HELMSJ232831.8<br>004035/HeL|MS55/No. S_130|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ232833.6<br>031416/HeL|HELMSJ232833.6<br>031416/HeL|MS48/No. S_131|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ233420.4<br>003458/HeL|HELMSJ233420.4<br>003458/HeL|MS43/No. S_132|1 arcsec|0<br>3|



**Figure B1** – _continued_



MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 43


3


3


3


3


3


3


3


**Figure B1** – _continued_


MNRAS **000**, 1–57 (2022)



30


20


10



0



10


5



0



30


20


10







0



15


10


5



0



40


20



0



30


20


10







0





40


30


20


10









0


|Col1|HELMSJ233721.9064740/HeL<br>1 arcsec|HELMSJ233721.9064740/HeL|MS49/No. S _133|1 arcsec|3<br>0|
|---|---|---|---|---|---|
||1 arcsec<br>HELMSJ233728.8<br>045106/HeL|HELMSJ233728.8<br>045106/HeL|MS20/No. S_134|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ234314.0+012152/HeL|HELMSJ234314.0+012152/HeL|MS36/No. S_135|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ234955.7<br>330833/He|HATLASJ234955.7<br>330833/He|rBS184/No. S_136|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ235101.7<br>024426/HeL|HELMSJ235101.7<br>024426/HeL|MS50/No. S_137|1 arcsec|0<br>3|
||1 arcsec<br>HATLASJ235121.9<br>332902/He|HATLASJ235121.9<br>332902/He|rBS159/No. S_138|1 arcsec|0<br>3|
||1 arcsec<br>HELMSJ235332.0+031718/HeL|1 arcsec<br>HELMSJ235332.0+031718/HeL|MS40/No. S_139<br>1<br>2<br>1 arcsec|1 arcsec<br>ALMA band 7|0<br>3|

44 _E. Borsato et al._










|HERMESJ003824 433705<br>HELAISS02/No. S _72<br>D<br>ALMA band 7|Col2|HERMESJ022022 015329<br>HXMM04/No. S _86<br>D<br>ALMA band 7|Col4|HERMESJ022029 064846<br>HXMM09/No. S _87<br>D<br>ALMA band 7|Col6|HERMESJ022548 041750<br>HXMM05/No. S _89<br>D<br>ALMA band 8|Col8|HERMESJ045027 524126<br>HADFS08/No. S _90<br>D<br>ALMA band 7|Col10|
|---|---|---|---|---|---|---|---|---|---|
|HERMESJ003824<br>433705<br> HELAISS02/No. S_72<br>D<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 8|ALMA band 8|ALMA band 7|
|HATLASJ084933+021443<br> G09-v1.124/No. S_92<br>D<br>ALMA band 6|HATLASJ084933+021443<br> G09-v1.124/No. S_92<br>D<br>ALMA band 6|HATLASJ222503.7<br>304847<br> HerBS166/No. S_119<br>D<br>ALMA band 7|HATLASJ222503.7<br>304847<br> HerBS166/No. S_119<br>D<br>ALMA band 7|HATLASJ000455.3<br>330811<br> HerBS170/No. S_140<br>D<br>ALMA band 6|HATLASJ000455.3<br>330811<br> HerBS170/No. S_140<br>D<br>ALMA band 6|HATLASJ001030.1<br>330621<br> HerBS98/No. S_141<br>C|HATLASJ001030.1<br>330621<br> HerBS98/No. S_141<br>C|HELMSJ001226.9+020810<br> HeLMS45/No. S_142<br>C|HELMSJ001226.9+020810<br> HeLMS45/No. S_142<br>C|
|HATLASJ084933+021443<br> G09-v1.124/No. S_92<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 7|ALMA band 7|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|
|HELMSJ001325.7+042509<br> HeLMS56/No. S_143<br>C|HELMSJ001325.7+042509<br> HeLMS56/No. S_143<br>C|HATLASJ002144.8<br>295217<br> HerBS156/No. S_144<br>C|HATLASJ002144.8<br>295217<br> HerBS156/No. S_144<br>C|HELMSJ002719.5+001204<br> HeLMS34/No. S_145<br>C|HELMSJ002719.5+001204<br> HeLMS34/No. S_145<br>C|HERMESJ002854<br>420457<br> HELAISS04/No. S_146<br>C|HERMESJ002854<br>420457<br> HELAISS04/No. S_146<br>C|HELMSJ003519.7+072806<br> HeLMS57/No. S_147<br>C|HELMSJ003519.7+072806<br> HeLMS57/No. S_147<br>C|
|HATLASJ003728.7<br>284124<br> HerBS174/No. S_148<br>C|HATLASJ003728.7<br>284124<br> HerBS174/No. S_148<br>C|HELMSJ004622.3+073509<br> HeLMS46/No. S_149<br>C|HELMSJ004622.3+073509<br> HeLMS46/No. S_149<br>C|HATLASJ005132.8<br>301848<br> HerBS45/No. S_150<br>C|HATLASJ005132.8<br>301848<br> HerBS45/No. S_150<br>C|HELMSJ005258.6+061319<br> HeLMS10/No. S_151<br>D<br>ALMA band 7|HELMSJ005258.6+061319<br> HeLMS10/No. S_151<br>D<br>ALMA band 7|HATLASJ005849.9<br>290122<br> HerBS181/No. S_152<br>C|HATLASJ005849.9<br>290122<br> HerBS181/No. S_152<br>C|
|HATLASJ003728.7<br>284124<br> HerBS174/No. S_148<br>C|HATLASJ003728.7<br>284124<br> HerBS174/No. S_148<br>C|HELMSJ004622.3+073509<br> HeLMS46/No. S_149<br>C|HELMSJ004622.3+073509<br> HeLMS46/No. S_149<br>C|HATLASJ005132.8<br>301848<br> HerBS45/No. S_150<br>C|HATLASJ005132.8<br>301848<br> HerBS45/No. S_150<br>C|HELMSJ005258.6+061319<br> HeLMS10/No. S_151<br>D<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|
|HATLASJ011014.5<br>314813<br> HerBS160/No. S_153<br>C<br>ALMA band 7|HATLASJ011014.5<br>314813<br> HerBS160/No. S_153<br>C<br>ALMA band 7|HATLASJ011730.3<br>320719<br> HerBS138/No. S_154<br>C|HATLASJ011730.3<br>320719<br> HerBS138/No. S_154<br>C|HATLASJ012209.4<br>273824<br> HerBS114/No. S_155<br>C|HATLASJ012209.4<br>273824<br> HerBS114/No. S_155<br>C|HATLASJ012335.1<br>314618<br> HerBS145/No. S_156<br>D<br>ALMA band 6|HATLASJ012335.1<br>314618<br> HerBS145/No. S_156<br>D<br>ALMA band 6|HERSJ013212.2+001754<br> HerS18/No. S_157<br>C|HERSJ013212.2+001754<br> HerS18/No. S_157<br>C|
|HATLASJ011014.5<br>314813<br> HerBS160/No. S_153<br>C<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 6|ALMA band 6|ALMA band 6|
|HATLASJ013239.9<br>330906<br> HerBS40/No. S_158<br>C|HATLASJ013239.9<br>330906<br> HerBS40/No. S_158<br>C|HERSJ014057.3<br>010547<br> HerS14/No. S_159<br>C|HERSJ014057.3<br>010547<br> HerS14/No. S_159<br>C|HATLASJ014520.0<br>313834<br> HerBS107/No. S_160<br>C|HATLASJ014520.0<br>313834<br> HerBS107/No. S_160<br>C|HERSJ020529.1+000501<br> HerS19/No. S_161<br>C|HERSJ020529.1+000501<br> HerS19/No. S_161<br>C|HERMESJ021632<br>053421<br> HXMM14/No. S_162<br>C|HERMESJ021632<br>053421<br> HXMM14/No. S_162<br>C|
|HERMESJ021837<br>035315<br> HXMM13/No. S_163<br>C|HERMESJ021837<br>035315<br> HXMM13/No. S_163<br>C|HERMESJ021943<br>052433<br> HXMM20/No. S_164<br>D<br>ALMA band 7|HERMESJ021943<br>052433<br> HXMM20/No. S_164<br>D<br>ALMA band 7|HERMESJ022206<br>070727<br> HXMM23/No. S_165<br>D<br>ALMA band 7|HERMESJ022206<br>070727<br> HXMM23/No. S_165<br>D<br>ALMA band 7|HERMESJ022213<br>070222<br> HXMM28/No. S_166<br>C|HERMESJ022213<br>070222<br> HXMM28/No. S_166<br>C|HERMESJ022251<br>032414<br> HXMM22/No. S_167<br>C|HERMESJ022251<br>032414<br> HXMM22/No. S_167<br>C|
|HERMESJ021837<br>035315<br> HXMM13/No. S_163<br>C|HERMESJ021837<br>035315<br> HXMM13/No. S_163<br>C|HERMESJ021943<br>052433<br> HXMM20/No. S_164<br>D<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|



**Figure B2.** Systems classified as C or D. Each panel show a ∼ 20 arcsec × 20 arcsec


cutout of the _HST_ image, the black shaded regions mark the _Herschel_ /SPIRE beam at 250 _𝜇_ m. Lastly, we show the contours of available high-resolution
multiwavelength data taken at two levels corresponding to _SNR_ = 5 and 10.


MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 45


**Figure B2** – _continued_











|HERMESJ022515 024707<br>HXMM19/No. S _168<br>C|Col2|HERMESJ022518 044610<br>HXMM27/No. S _169<br>C|HERMESJ023006 034153<br>HXMM12/No. S _170<br>C<br>ALMA band 7|Col5|HERMESJ032434 292646<br>HECDFS08/No. S _171<br>C|Col7|HERMESJ032443 282134<br>HECDFS03/No. S _172<br>C|Col9|
|---|---|---|---|---|---|---|---|---|
|HERMESJ022515<br>024707<br> HXMM19/No. S_168<br>C|HERMESJ022515<br>024707<br> HXMM19/No. S_168<br>C|HERMESJ022518<br>044610<br> HXMM27/No. S_169<br>C|HERMESJ023006<br>034153<br> HXMM12/No. S_170<br>C<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|
|HERMESJ032713<br>285106<br> HECDFS09/No. S_173<br>C|HERMESJ032713<br>285106<br> HECDFS09/No. S_173<br>C|HERMESJ033118<br>272015<br> HECDFS11/No. S_174<br>C|HERMESJ043341<br>540338<br> HADFS04/No. S_175<br>C<br>ALMA band 7|HERMESJ043341<br>540338<br> HADFS04/No. S_175<br>C<br>ALMA band 7|HERMESJ043830<br>541832<br> HADFS02/No. S_176<br>D<br>ALMA band 7|HERMESJ043830<br>541832<br> HADFS02/No. S_176<br>D<br>ALMA band 7|HERMESJ044947<br>525427<br> HADFS09/No. S_177<br>D<br>ALMA band 7|HERMESJ044947<br>525427<br> HADFS09/No. S_177<br>D<br>ALMA band 7|
|HERMESJ032713<br>285106<br> HECDFS09/No. S_173<br>C|HERMESJ032713<br>285106<br> HECDFS09/No. S_173<br>C|HERMESJ033118<br>272015<br> HECDFS11/No. S_174<br>C|HERMESJ043341<br>540338<br> HADFS04/No. S_175<br>C<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 7|
|HATLASJ083153+014014<br> -/No. S_178<br>D<br>ALMA band 3|HATLASJ083153+014014<br> -/No. S_178<br>D<br>ALMA band 3|HATLASJ083546+002804<br> -/No. S_179<br>C|HATLASJ083817<br>004134<br> HerBS108/No. S_180<br>C|HATLASJ083817<br>004134<br> HerBS108/No. S_180<br>C|HATLASJ083859.3+021325<br> HerBS169/No. S_181<br>C|HATLASJ083859.3+021325<br> HerBS169/No. S_181<br>C|HATLASJ083945+021023<br> HerBS171/No. S_182<br>C|HATLASJ083945+021023<br> HerBS171/No. S_182<br>C|
|HATLASJ083153+014014<br> -/No. S_178<br>D<br>ALMA band 3|ALMA band 3|ALMA band 3|ALMA band 3|ALMA band 3|ALMA band 3|ALMA band 3|ALMA band 3|ALMA band 3|
|HATLASJ084259.9+024959<br> HerBS188/No. S_183<br>C|HATLASJ084259.9+024959<br> HerBS188/No. S_183<br>C|HATLASJ085033+012914<br> -/No. S_184<br>C|HATLASJ085126+014638<br> -/No. S_185<br>C|HATLASJ085126+014638<br> -/No. S_185<br>C|HATLASJ085309<br>005727<br> HerBS136/No. S_186<br>C|HATLASJ085309<br>005727<br> HerBS136/No. S_186<br>C|HATLASJ090953<br>010811<br> SDP.60/No. S_187<br>C|HATLASJ090953<br>010811<br> SDP.60/No. S_187<br>C|
|HATLASJ091454<br>010357<br> HerBS142/No. S_188<br>D<br>ALMA band 6|HATLASJ091454<br>010357<br> HerBS142/No. S_188<br>D<br>ALMA band 6|HATLASJ091809+001927<br> HerBS99/No. S_189<br>C|HATLASJ091857<br>000047<br> -/No. S_190<br>C|HATLASJ091857<br>000047<br> -/No. S_190<br>C|HATLASJ091949<br>005037<br> -/No. S_191<br>C|HATLASJ091949<br>005037<br> -/No. S_191<br>C|HATLASJ092141+005356<br> -/No. S_192<br>C|HATLASJ092141+005356<br> -/No. S_192<br>C|
|HATLASJ091454<br>010357<br> HerBS142/No. S_188<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|
|HERMESJ100057+022014<br> HCOSMOS02/No. S_193<br>D<br>ALMA band 6|HERMESJ100057+022014<br> HCOSMOS02/No. S_193<br>D<br>ALMA band 6|HERMESJ103958+563120<br> HLock17/No. S_194<br>C|HERMESJ104051+560654<br> HLock02/No. S_195<br>C|HERMESJ104051+560654<br> HLock02/No. S_195<br>C|HERMESJ104140+570859<br> HLock11/No. S_196<br>C|HERMESJ104140+570859<br> HLock11/No. S_196<br>C|HERMESJ105712+565458<br> HLock03/No. S_197<br>C|HERMESJ105712+565458<br> HLock03/No. S_197<br>C|
|HERMESJ100057+022014<br> HCOSMOS02/No. S_193<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|
|HATLASJ113243<br>005109<br> HerBS71/No. S_198<br>C|HATLASJ113243<br>005109<br> HerBS71/No. S_198<br>C|HATLASJ113834<br>014657<br> HerBS119/No. S_199<br>C|HATLASJ114753<br>005832<br> HerBS85/No. S_200<br>C|HATLASJ114753<br>005832<br> HerBS85/No. S_200<br>C|HATLASJ115521<br>021332<br> HerBS179/No. S_201<br>D<br>ALMA band 6|HATLASJ115521<br>021332<br> HerBS179/No. S_201<br>D<br>ALMA band 6|HATLASJ115820<br>013754<br> HerBS66/No. S_202<br>C|HATLASJ115820<br>013754<br> HerBS66/No. S_202<br>C|
|HATLASJ113243<br>005109<br> HerBS71/No. S_198<br>C|HATLASJ113243<br>005109<br> HerBS71/No. S_198<br>C|HATLASJ113834<br>014657<br> HerBS119/No. S_199<br>C|HATLASJ114753<br>005832<br> HerBS85/No. S_200<br>C|HATLASJ114753<br>005832<br> HerBS85/No. S_200<br>C|HATLASJ115521<br>021332<br> HerBS179/No. S_201<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|


MNRAS **000**, 1–57 (2022)

46 _E. Borsato et al._

|H HA eT rL BA SS 7J 41 /2 N0 o6 0 S0 _.27 0+ 3003459<br>.<br>C|H HA eT rL BA SS 5J 11 /2 N0 o7 0 S9 _.22 04014702<br>.<br>C|H HA eT rL BA SS 1J 11 62 /1 N3 o4 8 S. _1 2+ 00 510812<br>.<br>C|H HA eT rL BA SS 1J 61 42 /1 N4 o1 6 S. _3 200 613704<br>.<br>C|Col5|H HA eT rL BA SS 8J 31 /2 N1 o8 1 S2 _.28 0+ 7011841<br>.<br>D<br>ALMA band 6|Col7|
|---|---|---|---|---|---|---|
|HATLASJ120600.7+003459<br> HerBS74/No. S_203<br>C|HATLASJ120709.2<br>014702<br> HerBS51/No. S_204<br>C|HATLASJ121348.1+010812<br> HerBS116/No. S_205<br>C|HATLASJ121416.3<br>013704<br> HerBS164/No. S_206<br>C|HATLASJ121416.3<br>013704<br> HerBS164/No. S_206<br>C|HATLASJ121812.8+011841<br> HerBS83/No. S_207<br>D<br>ALMA band 6|ALMA band 6|
|HATLASJ122034.3<br>003805<br> HerBS197/No. S_208<br>C|HATLASJ122117.0<br>014924<br> -/No. S_209<br>C|HATLASJ122158.5+003326<br> HerBS124/No. S_210<br>C|HATLASJ122407.4<br>003247<br> HerBS161/No. S_211<br>D<br>ALMA band 6|HATLASJ122407.4<br>003247<br> HerBS161/No. S_211<br>D<br>ALMA band 6|HATLASJ122459.1<br>005647<br> HerBS150/No. S_212<br>D<br>ALMA band 6|HATLASJ122459.1<br>005647<br> HerBS150/No. S_212<br>D<br>ALMA band 6|
|HATLASJ122034.3<br>003805<br> HerBS197/No. S_208<br>C|HATLASJ122117.0<br>014924<br> -/No. S_209<br>C|HATLASJ122158.5+003326<br> HerBS124/No. S_210<br>C|HATLASJ122407.4<br>003247<br> HerBS161/No. S_211<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|
|HATLASJ125105+261653<br> NGP.2070/No. S_213<br>C|HATLASJ125653+275903<br> HerBS31/No. S_214<br>C|HATLASJ125810+263710<br> -/No. S_215<br>C|HATLASJ130601+231322<br> -/No. S_216<br>C|HATLASJ130601+231322<br> -/No. S_216<br>C|HATLASJ131001+264759<br> -/No. S_217<br>C|HATLASJ131001+264759<br> -/No. S_217<br>C|
|HATLASJ131020+253731<br> -/No. S_218<br>C|HATLASJ131609+254931<br> -/No. S_219<br>C|HATLASJ131642+251158<br> -/No. S_220<br>C|HATLASJ131805+325018<br> HerBS173/No. S_221<br>C|HATLASJ131805+325018<br> HerBS173/No. S_221<br>C|HATLASJ132128+282023<br> HerBS127/No. S_222<br>C|HATLASJ132128+282023<br> HerBS127/No. S_222<br>C|
|HATLASJ132227+300723<br> -/No. S_223<br>C|HATLASJ132302+341650<br> HerBS30/No. S_224<br>C|HATLASJ132419+320754<br> HerBS43/No. S_225<br>C|HATLASJ132909+300958<br> HerBS204/No. S_226<br>C|HATLASJ132909+300958<br> HerBS204/No. S_226<br>C|HATLASJ133255+265529<br> -/No. S_227<br>C|HATLASJ133255+265529<br> -/No. S_227<br>C|
|HATLASJ133256+342210<br> HerBS44/No. S_228<br>C|HATLASJ133440+353140<br> HerBS134/No. S_229<br>C|HATLASJ133534+341837<br> HerBS76/No. S_230<br>C|HATLASJ133623+343806<br> -/No. S_231<br>C|HATLASJ133623+343806<br> -/No. S_231<br>C|HATLASJ133715+352058<br> -/No. S_232<br>C|HATLASJ133715+352058<br> -/No. S_232<br>C|
|HATLASJ133905+340820<br> -/No. S_233<br>C|HATLASJ134124+354007<br> -/No. S_234<br>C|HATLASJ134139+322837<br> -/No. S_235<br>C|HATLASJ134403+242627<br> HerBS196/No. S_236<br>C|HATLASJ134403+242627<br> HerBS196/No. S_236<br>C|HATLASJ134442+240346<br> HerBS133/No. S_237<br>C|HATLASJ134442+240346<br> HerBS133/No. S_237<br>C|



MNRAS **000**, 1–57 (2022)







**Figure B2** – _continued_

_Characterisation of HST confirmed lenses_ 47


**Figure B2** – _continued_











|HATLASJ134654+295659<br>-/No. S _238<br>C|HATLASJ140422 001218<br>HerBS206/No. S _239<br>C|Col3|HATLASJ141118 010655<br>HerBS201/No. S _240<br>D<br>ALMA band 6|Col5|H HA eT rL BA SS 1J 41 34 /1 N8 o1 0 S. _0 240 103747<br>.<br>C|Col7|H -/A NT oL .A SS _J 21 44 21955.5 003449<br>C|Col9|
|---|---|---|---|---|---|---|---|---|
|HATLASJ134654+295659<br> -/No. S_238<br>C|HATLASJ140422<br>001218<br> HerBS206/No. S_239<br>C|HATLASJ140422<br>001218<br> HerBS206/No. S_239<br>C|HATLASJ141118<br>010655<br> HerBS201/No. S_240<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|
|HERMESJ142549+345024<br> -/No. S_243<br>C|HERMESJ142558+332549<br> HBootes09/No. S_244<br>C|HERMESJ142558+332549<br> HBootes09/No. S_244<br>C|HATLASJ142707+002258<br> HerBS130/No. S_245<br>C|HATLASJ142707+002258<br> HerBS130/No. S_245<br>C|HATLASJ143403.5+000234<br> HerBS147/No. S_246<br>C|HATLASJ143403.5+000234<br> HerBS147/No. S_246<br>C|HERMESJ143544+344743<br> HBootes12/No. S_247<br>C|HERMESJ143544+344743<br> HBootes12/No. S_247<br>C|
|HERMESJ144030+333843<br> HBootes07/No. S_248<br>C|HATLASJ144556.1<br>004853<br> HerBS46/No. S_249<br>D<br>SMA 340 GHz|HATLASJ144556.1<br>004853<br> HerBS46/No. S_249<br>D<br>SMA 340 GHz|HATLASJ144608.6+021927<br> HerBS38/No. S_250<br>C|HATLASJ144608.6+021927<br> HerBS38/No. S_250<br>C|HATLASJ145135.2<br>011418<br> HerBS126/No. S_251<br>C|HATLASJ145135.2<br>011418<br> HerBS126/No. S_251<br>C|HATLASJ145337.2+000407<br> HerBS137/No. S_252<br>C|HATLASJ145337.2+000407<br> HerBS137/No. S_252<br>C|
|HERMESJ144030+333843<br> HBootes07/No. S_248<br>C|HATLASJ144556.1<br>004853<br> HerBS46/No. S_249<br>D<br>SMA 340 GHz|SMA 340 GHz|SMA 340 GHz|SMA 340 GHz|SMA 340 GHz|SMA 340 GHz|SMA 340 GHz|SMA 340 GHz|
|HATLASJ145754+000017<br> HerBS195/No. S_253<br>C|HERMESJ161332+544358<br> HELAISN01/No. S_254<br>C|HERMESJ161332+544358<br> HELAISN01/No. S_254<br>C|HERMESJ170508+594056<br> HFLS07/No. S_255<br>C|HERMESJ170508+594056<br> HFLS07/No. S_255<br>C|HERMESJ170608+590921<br> HFLS03/No. S_256<br>C|HERMESJ170608+590921<br> HFLS03/No. S_256<br>C|HERMESJ170818+582845<br> HFLS05/No. S_257<br>C|HERMESJ170818+582845<br> HFLS05/No. S_257<br>C|
|HERMESJ172222+582611<br> HFLS10/No. S_258<br>C|HERMESJ172612+583742<br> HFLS01/No. S_259<br>C|HERMESJ172612+583742<br> HFLS01/No. S_259<br>C|HATLASJ222629.4<br>321111<br> HerBS144/No. S_260<br>C|HATLASJ222629.4<br>321111<br> HerBS144/No. S_260<br>C|HATLASJ224027.7<br>343134<br> HerBS97/No. S_261<br>C|HATLASJ224027.7<br>343134<br> HerBS97/No. S_261<br>C|HATLASJ224207.2<br>324159<br> HerBS67/No. S_262<br>D<br>ALMA band 6|HATLASJ224207.2<br>324159<br> HerBS67/No. S_262<br>D<br>ALMA band 6|
|HERMESJ172222+582611<br> HFLS10/No. S_258<br>C|HERMESJ172612+583742<br> HFLS01/No. S_259<br>C|HERMESJ172612+583742<br> HFLS01/No. S_259<br>C|HATLASJ222629.4<br>321111<br> HerBS144/No. S_260<br>C|HATLASJ222629.4<br>321111<br> HerBS144/No. S_260<br>C|HATLASJ224027.7<br>343134<br> HerBS97/No. S_261<br>C|HATLASJ224027.7<br>343134<br> HerBS97/No. S_261<br>C|HATLASJ224207.2<br>324159<br> HerBS67/No. S_262<br>D<br>ALMA band 6|ALMA band 6|
|HATLASJ224400.8<br>340030<br> HerBS84/No. S_263<br>C|HATLASJ225324.2<br>323504<br> HerBS103/No. S_264<br>C|HATLASJ225324.2<br>323504<br> HerBS103/No. S_264<br>C|HATLASJ225339.1<br>325549<br> HerBS131/No. S_265<br>C|HATLASJ225339.1<br>325549<br> HerBS131/No. S_265<br>C|HATLASJ225611.6<br>325652<br> HerBS135/No. S_266<br>C|HATLASJ225611.6<br>325652<br> HerBS135/No. S_266<br>C|HATLASJ230002.6<br>315005<br> HerBS80/No. S_267<br>C|HATLASJ230002.6<br>315005<br> HerBS80/No. S_267<br>C|
|HATLASJ230538.5<br>312204<br> HerBS182/No. S_268<br>C|HATLASJ231205.1<br>295026<br> HerBS132/No. S_269<br>C|HATLASJ231205.1<br>295026<br> HerBS132/No. S_269<br>C|HELMSJ231857.2<br>053035<br> HeLMS16/No. S_270<br>C|HELMSJ231857.2<br>053035<br> HeLMS16/No. S_270<br>C|HATLASJ232200.0<br>355622<br> HerBS118/No. S_271<br>D<br>ALMA band 6|HATLASJ232200.0<br>355622<br> HerBS118/No. S_271<br>D<br>ALMA band 6|HATLASJ232419.8<br>323926<br> HerBS18/No. S_272<br>C|HATLASJ232419.8<br>323926<br> HerBS18/No. S_272<br>C|
|HATLASJ230538.5<br>312204<br> HerBS182/No. S_268<br>C|HATLASJ231205.1<br>295026<br> HerBS132/No. S_269<br>C|HATLASJ231205.1<br>295026<br> HerBS132/No. S_269<br>C|HELMSJ231857.2<br>053035<br> HeLMS16/No. S_270<br>C|HELMSJ231857.2<br>053035<br> HeLMS16/No. S_270<br>C|HATLASJ232200.0<br>355622<br> HerBS118/No. S_271<br>D<br>ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|


MNRAS **000**, 1–57 (2022)

48 _E. Borsato et al._

|H HE eL LM MS SJ2 13 72 /N5 o5 .8 S.3 _270 344525<br>C|Col2|H HA eT rL BA SS 3J 72 /3 N2 o6 2 S3 _.20 74342642<br>.<br>C|Col4|H HE eL LM MS SJ2 43 24 /N0 o1 .4 S.6 _270 570738<br>C|H HE eL LM MS SJ2 43 74 /N9 o5 .1 S.6 _270 630019<br>C|H HE eR rS SJ 90 /1 N0 o9 1 S1 _2.7 77011733<br>.<br>D|
|---|---|---|---|---|---|---|
|HATLASJ083345+000109<br> HerBS88/No. S_278<br>D<br>ALMA band 7|HATLASJ083345+000109<br> HerBS88/No. S_278<br>D<br>ALMA band 7|HATLASJ090613.8<br>010042<br> HerBS165/No. S_279<br>D<br>ALMA band 6|HATLASJ090613.8<br>010042<br> HerBS165/No. S_279<br>D<br>ALMA band 6|HATLASJ091238+020050<br> -/No. S_280<br>D|HATLASJ142004+014045<br> -/No. S_281<br>D|HATLASJ142004+014045<br> -/No. S_281<br>D|
|HATLASJ083345+000109<br> HerBS88/No. S_278<br>D<br>ALMA band 7|ALMA band 7|ALMA band 7|ALMA band 6|ALMA band 6|ALMA band 6|ALMA band 6|



MNRAS **000**, 1–57 (2022)







**Figure B2** – _continued_

**Table A2.** Derived properties of the lensing systems.


No. IAU Name _𝑚𝐹_ 110 _𝑊_ _𝜇_ 50 _𝑅_ 50 _𝐶_ 31 _𝜇𝑆_ 1 _._ 1

[mag] [mag arcsec [−][2] ] [arcsec] [ _𝜇_ Jy]
_𝑀𝐹_ 110 _𝑊_ _𝜇_ 50 _,_ 0 _𝑅_ 50 _,_ 0

[mag] [mag kpc [−][2] ] [kcp]
(1) (2) (3) (4) (5) (6) (7)

S_1 HATLASJ000330.6 − 321136 − [19] 17 _[.]_ [30] _._ 78 [ ±][+] − [ 0][0] 0 _[.][.]_ _._ [73][14] 59 21 [20] _[.]_ _._ [10] 49 [+][+] −− [0][0] 00 _[.][.]_ _.._ [37][21] 3520 02 _.._ 5699 ± [+] − [0] 0 0 _[.]_ _._ [52] _._ 5505 7 _._ 24 [+] − [0] 0 _[.]_ _._ [43] 40 1 _._ 81 ± 0 _._ 06

S_2 HATLASJ000912.7 − 300807 − [17] 19 _[.]_ [09] _._ 26 [ ±][+] − [ 0][0] 0 _[.][.]_ _._ [83][19] 68 [22][21] _[.][.]_ [18][10][ ±][+] − [0] 0 [ 0] _[.]_ _._ [38] _[.]_ 37 [26] 102 _.._ 3849 [+] − [+] − [0] 0 [2] 2 _[.]_ _._ _[.]_ [20] _._ 17 [19] 36 5 _._ 34 [+] − [0] 0 _[.]_ _._ [38] 40 45 _._ 35 ± 0 _._ 12

S_3 HELMSJ001353.5 − 060200 −1918 _._ 99 _._ 29 ± [+] − 0 [0] 0 _[.]_ _.._ [92] 2472 23 [21] _[.]_ _._ [09] 16 [+][+] −− [0][0] 00 _[.][.]_ _.._ [67][41] 6450 50 _.._ 9890 [+][+] −− [1][0] 10 _[.][.]_ _.._ [98][25] 5721 7 _._ 26 [+] − [1] 1 _[.]_ _._ [15] 34 3 _._ 00 ± 0 _._ 10

S_4 HELMSJ003619.8 + 002420 −1619 _._ 41 _._ 72 ± [+] − 0 [0] 0 _[.]_ _.._ [18] 1817 21 [20] _[.]_ _._ [29] 29 [+][+] −− [0][0] 00 _[.][.]_ _.._ [46][46] 3636 82 _.._ 5507 [+][+] −− [1][0] 00 _[.][.]_ _.._ [06][26] 8420 6 _._ 38 [+] − [1] 0 _[.]_ _._ [30] 97 13 _._ 58 ± 0 _._ 25

S_6 HERSJ011722.3 + 005624 1 −1919 _._ 45 _._ 82 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [34] _[.]_ 31 _._ [37] 36 [19] 22 _[.]_ _._ [38] 10 [+][+] −− [0][0] 00 _[.][.]_ _.._ [47][47] 3734 50 _.._ 3367 [+][+] −− [0][0] 00 _[.][.]_ _.._ [66][08] 5507 8 _._ 68 [+] − [0] 0 _[.]_ _._ [74] 68 2 _._ 23 ± 0 _._ 10

HERSJ011722.3 + 005624 2 22 _._ 87 – [+] − [0] 0 _[.]_ _._ [23] 22 22 _._ 52 – [+] − [0] 0 _[.]_ _._ [17] 15 0 _._ 24 ± – 0 _._ 02 2 _._ 95 ± 0 _._ 18


S_7 HERSJ012620.5 + 012950 −1818 _._ 86 _._ 55 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [29] _[.]_ 28 _._ [42] 40 [19] 21 _[.]_ _._ [67] 22 [+][+] −− [0][0] 00 _[.][.]_ _.._ [20][13] 1911 04 _.._ 7427 ± [+] − [0] 0 0 _[.]_ _._ [43] _._ 4205 4 _._ 64 [+] − [1] 0 _[.]_ _._ [03] 76 5 _._ 72 ± 0 _._ 09


S_9 HERMESJ032637 − 270044 19 _._ 10 ± – 0 _._ 07 22 _._ 70 ± – 0 _._ 05 1 _._ 01 [+] − – [0] 0 _[.]_ _._ [02] 03 10 _._ 12 ± 0 _._ 22 3 _._ 81 ± 0 _._ 13


S_10HERMESJ033732 − 295353 −1618 _._ 47 _._ 89 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [13] _[.]_ 12 _._ [68] 55 [20] 21 _[.]_ _._ [40] 15 [+][+] −− [0][0] 00 _[.][.]_ _.._ [25][19] 2720 61 _.._ 1591 ± ± 1 0 _.._ 3216 5 _._ 36 [+] − [0] 0 _[.]_ _._ [33] 32 2 _._ 93 ± 0 _._ 07

S_13HERMESJ103827 + 581544 −1720 _._ 86 _._ 38 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [09] _[.]_ 08 _._ [09] 08 [19] 21 _[.]_ _._ [93] 95 [+][+] −− [0][0] 00 _[.][.]_ _.._ [12][12] 1313 101 _._ 53 _._ 48 ± [+] − 0 [0] 0 _[.]_ _.._ [76] 1172 4 _._ 75 [+] − [0] 0 _[.]_ _._ [19] 20 10 _._ 12 ± 0 _._ 23


S_14HERMESJ110016 + 571736 −1820 _._ 78 _._ 19 ± ± 0 0 _._ 06 _._ 06 1921 _.._ 7625 ± ± 0 0 _.._ 0404 06 _.._ 9197 ± ± 0 0 _.._ 0215 4 _._ 99 ± 0 _._ 06 12 _._ 71 ± 0 _._ 19

S_15HATLASJ114638 − 001132 1 −2119 _._ 15 _._ 03 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [21] _[.]_ 20 _._ [21] 20 [18] 21 _[.]_ _._ [50] 97 [+][+] −− [1][1] 00 _[.][.]_ _.._ [01][01] 7070 20 _.._ 5129 [+][+] −− [0][0] 00 _[.][.]_ _.._ [86][10] 4205 7 _._ 50 [+] − [0] 1 _[.]_ _._ [98] 17 6 _._ 33 ± 0 _._ 14

HATLASJ114638 − 001132 2 −2019 _._ 52 _._ 66 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [16] _[.]_ 15 _._ [16] 15 [21] 24 _[.]_ _._ [05] 52 [+][+] −− [0][0] 00 _[.][.]_ _.._ [29][29] 3737 101 _._ 28 _._ 90 ± [+] − 0 [2] 2 _[.]_ _.._ [06] 2409 8 _._ 90 [+] − [1] 1 _[.]_ _._ [82] 84

S_16HATLASJ125126 + 254928 −1919 _._ 21 _._ 16 ± [+] − 0 [0] 0 _[.]_ _.._ [46] 0840 23 [21] _[.]_ _._ [02] 11 [+][+] −− [0][0] 00 _[.][.]_ _.._ [27][06] 2605 17 _.._ 0746 ± [+] − [0] 0 0 _[.]_ _._ [52] _._ 6103 15 _._ 14 [+] − [0] 0 _[.]_ _._ [42] 41 4 _._ 18 ± 0 _._ 15


S_17HATLASJ125760 + 224558 −1819 _._ 83 _._ 25 ± ± 0 0 _._ 06 _._ 06 2022 _.._ 3342 ± ± 0 0 _.._ 0404 16 _.._ 0276 ± ± 0 0 _.._ 0215 8 _._ 05 ± 0 _._ 13 10 _._ 13 ± 0 _._ 12

S_18HATLASJ133008 + 245860 −1918 _._ 05 _._ 36 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [35] _[.]_ 32 _._ [35] 32 [20] 21 _[.]_ _._ [01] 55 [+][+] −− [0][0] 00 _[.][.]_ _.._ [23][23] 2020 30 _.._ 9568 ± ± 0 0 _.._ 3105 7 _._ 33 [+] − [1] 1 _[.]_ _._ [09] 03 3 _._ 54 ± 0 _._ 11


S_19HATLASJ133846 + 255057 20 _._ 09 [+] − [0] 0 _[.]_ _._ [10] 09 23 _._ 46 [+] − [0] 0 _[.]_ _._ [07] 06 0 _._ 93 ± 0 _._ 03 9 _._ 19 ± 0 _._ 29 12 _._ 23 ± 0 _._ 12
−17 _._ 25 [+] − [0] 0 _[.]_ _._ [70] 55 [21] _[.]_ [94][+] − [0] 0 _[.]_ _._ [32] 30 5 _._ 27 [+] − [0] 0 _[.]_ _._ [68] 84

S_21HERMESJ171451 + 592634 −2119 _._ 03 _._ 17 ± ± 0 0 _._ 08 _._ 08 2218 _.._ 5605 [+][+] −− [0][0] 00 _[.][.]_ _.._ [05][05] 0404 [0] 2 _[.]_ [336] _._ 87 ± [+] − [0] 0 0 _[.]_ _._ [010] _._ 009608 _._ 9887 [+] − [0] 0 _[.]_ _._ [0005] 0003 [7] _[.]_ [00][ ±][ 0] _[.]_ [13]

S_22HERMESJ171545 + 601238 1 −1818 _._ 38 _._ 78 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [11] _[.]_ 10 _._ [64] 53 23 [22] _._ _[.]_ 86 [43] ± [+] − [0] 0 0 _[.]_ _._ [30] _._ 2912 142 _._ 68 _._ 54 ± [+] − 0 [2] 2 _[.]_ _.._ [11] 1740 6 _._ 51 [+] − [0] 0 _[.]_ _._ [37] 35 6 _._ 65 ± 0 _._ 14

HERMESJ171545 + 601238 2 21 _._ 09 – [+] − [0] 0 _[.]_ _._ [15] 14 23 _._ 87 – [+] − [0] 0 _[.]_ _._ [10] 09 0 _._ 77 ± – 0 _._ 04 6 _._ 60 ± 0 _._ 32


_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the
_Herschel_ detection. Indices 1 and 2 refer to the two components of the lens
candidate. Col. (3): Apparent magnitude of the model (first row), absolute
magnitude of the model (second row). Col. (4): Total effective radius in
arcsec (first row) and in kpc (second row). Col. (5): Total effective surface
brightness before (first row) and after correcting for cosmological dimming
(second row). Col. (6): _𝐶_ 31 of the model. Col. (7): Flux density of the
background source uncorrected for the magnification.



_Characterisation of HST confirmed lenses_ 49


**Table A2** – _continued_


No. IAU Name _𝑚𝐹_ 110 _𝑊_ _𝜇_ 50 _𝑅_ 50 _𝐶_ 31 _𝜇𝑆_ 1 _._ 1

[mag] [mag arcsec [−][2] ] [arcsec] [ _𝜇_ Jy]
_𝑀𝐹_ 110 _𝑊_ _𝜇_ 50 _,_ 0 _𝑅_ 50 _,_ 0

[mag] [mag kpc [−][2] ] [kcp]
(1) (2) (3) (4) (5) (6) (7)

S_23HATLASJ225844.8 − 295124 1 −2018 _._ 37 _._ 28 ± [+] − 0 [0] 0 _[.]_ _.._ [93] 1069 [18] 20 _._ _[.]_ [41] 69 [+][+] −− [0][0] 00 _[.][.]_ _.._ [07][57] 0649 02 _.._ 2913 ± [+] − [0] 0 0 _[.]_ _._ [22] _._ 3301 3 _._ 86 ± 0 _._ 08 1 _._ 41 ± 0 _._ 08

HATLASJ225844.8 − 295124 2 −1919 _._ 43 _._ 18 ± [+] − 0 [0] 0 _[.]_ _.._ [92] 1473 [22] 24 _._ _[.]_ 60 [33][+][+] −− [0][0] 00 _[.][.]_ _.._ [12][56] 1452 162 _.._ 3260 [+] − [+] − [0] 0 [2] 2 _[.]_ _._ _[.]_ [19] _._ 20 [34] 76 6 _._ 47 [+] − [0] 0 _[.]_ _._ [56] 53

S_24HELMSJ232210.3 − 033559 1 −1915 _._ 33 _._ 46 [+] − [+] − [0] 0 [1] 1 _[.]_ _._ [14] _[.]_ 13 _._ [76] 08 [22] 22 _[.]_ _._ [13] 74 [ ±][+] − [0] 0 [ 0] _[.]_ _._ [13] _[.]_ 14 [33] 12 _.._ 0064 [+][+] −− [0][1] 01 _[.][.]_ _.._ [11][20] 3012 7 _._ 18 [+] − [0] 0 _[.]_ _._ [50] 53 3 _._ 47 ± 0 _._ 08

HELMSJ232210.3 − 033559 2 22 _._ 74 ± – 0 _._ 12 21 _._ 44 ± – 0 _._ 06 0 _._ 116 [+] − – [0] 0 _[.]_ _._ [006] 005 6 _._ 982 [+] − [0] 0 _[.]_ _._ [004] 001


S_25HATLASJ233037.2 − 331217 1 −1919 _._ 45 _._ 07 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [14] _[.]_ 13 _._ [82] 63 22 [20] _._ _[.]_ [71] 91 [+][+] −− [0][0] 00 _[.][.]_ _.._ [19][52] 2147 17 _.._ 0866 ± [+] − [1] 1 0 _[.]_ _._ [16] _._ 3212 6 _._ 58 [+] − [1] 1 _[.]_ _._ [32] 03 19 _._ 93 ± 0 _._ 21
HATLASJ233037.2 − 331217 2 −15[23 _._ 40 _._ 14 [+] − [0] 0] _[.]_ _._ [80] 60 –– –– –


_Confirmed after the lens subtraction_

S_26HELMSJ001626.0 + 042613 −1718 _._ 63 _._ 06 ± ± 0 0 _._ 07 _._ 07 2019 _.._ 3550 ± ± 0 0 _.._ 1111 02 _.._ 7363 ± [+] − [0] 0 0 _[.]_ _._ [16] _._ 1504 7 _._ 11 ± 0 _._ 17 1 _._ 46 ± 0 _._ 08

S_27HATLASJ002624.8 − 341737 −2018 _._ 82 _._ 61 [+] − [+] − [0] 0 [1] 0 _[.]_ _._ [20] _[.]_ 19 _._ [20] 88 23 [20] _._ _[.]_ 13 [28][+][+] −− [0][0] 00 _[.][.]_ _.._ [30][88] 3178 04 _.._ 6288 [+][+] −− [0][0] 00 _[.][.]_ _.._ [08][81] 8507 6 _._ 69 [+] − [0] 0 _[.]_ _._ [86] 94 0 _._ 90 ± 0 _._ 03

S_28HELMSJ004723.6 + 015751 1 −1818 _._ 14 _._ 86 ± ± 0 0 _._ 06 _._ 06 2021 _.._ 6732 [+][+] −− [0][0] 00 _[.][.]_ _.._ [09][09] 1111 16 _.._ 2765 [+][+] −− [0][0] 00 _[.][.]_ _.._ [06][33] 3807 4 _._ 10 [+] − [0] 0 _[.]_ _._ [49] 35 10 _._ 99 ± 0 _._ 18

HELMSJ004723.6 + 015751 2 19 _._ 58 – [+] − [0] 0 _[.]_ _._ [09] 08 22 _._ 17 ± – 0 _._ 06 0 _._ 74 ± – 0 _._ 02 5 _._ 65 ± 0 _._ 10


S_29HERSJ012041.6 − 002705 −1919 _._ 59 _._ 21 ± [+] − 0 [0] 0 _[.]_ _.._ [21] 1520 [19] 21 _._ _[.]_ [59] 97 [+][+] −− [0][0] 00 _[.][.]_ _.._ [34][35] 3738 04 _.._ 5836 [+][+] −− [0][0] 00 _[.][.]_ _.._ [10][75] 6609 9 _._ 37 [+] − [0] 0 _[.]_ _._ [72] 85 2 _._ 57 ± 0 _._ 10

S_30HATLASJ085112 + 004934 −1819 _._ 68 _._ 86 [+] − [+] − [0] 0 [1] 1 _[.]_ _._ [17] _[.]_ 19 _._ [58] 07 20 [18] _._ _[.]_ 81 [60][+][+] −− [0][0] 00 _[.][.]_ _.._ [18][88] 2079 05 _.._ 7527 ± [+] − [0] 1 0 _[.]_ _._ [91] _._ 4706 3 _._ 25 [+] − [0] 0 _[.]_ _._ [66] 47 9 _._ 37 ± 0 _._ 15

S_31HATLASJ085359 + 015537 −2019 _._ 77 _._ 26 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [16] _[.]_ 15 _._ [58] 49 [21] 24 _[.]_ _._ [58] 92 [ ±][+] − [0] 0 [ 0] _[.]_ _._ [36] _[.]_ 38 [57] [10] 1 _._ _[.]_ 22 [17][+] − [+] − [0] 0 [1] 1 _[.]_ _._ _[.]_ [20] _._ 18 [76] 54 14 _._ 19 [+] − [1] 1 _[.]_ _._ [47] 44 [0] _[.]_ [87][ ±][ 0] _[.]_ [03]

S_32HERMESJ104549 + 574512 −1915 _._ 69 _._ 81 ± [+] − 0 [0] 0 _[.]_ _.._ [29] 1428 [20] 20 _._ _[.]_ [15] 94 [+][+] −− [0][0] 00 _[.][.]_ _.._ [17][18] 1819 01 _.._ 4139 ± [+] − [0] 0 0 _[.]_ _._ [17] _._ 1604 5 _._ 16 [+] − [0] 0 _[.]_ _._ [46] 43 7 _._ 20 ± 0 _._ 10

S_33HERMESJ105551 + 592845 1 −2016 _._ 84 _._ 26 ± [+] − 0 [0] 0 _[.]_ _.._ [85] 1266 22 [21] _._ _[.]_ 62 [22] ± [+] − [0] 0 0 _[.]_ _._ [37] _._ 3308 03 _.._ 5809 ± [+] − [0] 0 0 _[.]_ _._ [51] _._ 6302 3 _._ 83 ± 0 _._ 10 5 _._ 60 ± 0 _._ 08

HERMESJ105551 + 592845 2 22 _._ 06 – [+] − [0] 0 _[.]_ _._ [21] 20 21 _._ 86 – [+] − [0] 0 _[.]_ _._ [15] 13 0 _._ 25 ± – 0 _._ 02 3 _._ 10 ± 0 _._ 14



HATLASJ133543 + 300404 1 −2018 _._ 76 _._ 83 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [12] _[.]_ 11 _._ [12] 11 22 [19] _._ _[.]_ 35 [38][+][+] −− [0][0] 00 _[.][.]_ _.._ [08][08] 0707 04 _.._ 6090 ± ± 0 0 _.._ 0322 2 _._ 88 [+] − [0] 0 _[.]_ _._ [06] 05

HATLASJ133543 + 300404 2 −2018 _._ 98 _._ 62 ± ± 0 0 _._ 13 _._ 13 1821 _.._ 9092 [+][+] −− [0][0] 00 _[.][.]_ _.._ [09][09] 0808 02 _.._ 3150 ± [+] − [0] 0 0 _[.]_ _._ [12] _._ 1101 8 _._ 66 [+] − [0] 0 _[.]_ _._ [43] 42
HATLASJ133543 + 300404 3 −1919 _._ 92 _._ 67 ± ± 0 0 _._ 09 _._ 09 2023 _.._ 5053 ± ± 0 0 _.._ 0606 18 _.._ 0127 ± [+] − [0] 0 0 _[.]_ _._ [25] _._ 2603 9 _._ 81 ± 0 _._ 30

HATLASJ133543 + 300404 4 −2019 _._ 45 _._ 18 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [11] _[.]_ 10 _._ [11] 10 23 [20] _._ _[.]_ 58 [58][+][+] −− [0][0] 00 _[.][.]_ _.._ [07][07] 0606 06 _.._ 8056 ± ± 0 0 _.._ 0323 11 _._ 10+−00 _.._ 4544



HERMESJ105751 + 573026 1 −1720 _._ 82 _._ 47 ± [+] − 0 [0] 0 _[.]_ _.._ [20] 0819 [21] 23 _._ _[.]_ [43] 48 [+][+] −− [0][0] 00 _[.][.]_ _.._ [15][19] 1720 182 _._ 64 _._ 16 ± [+] − 0 [1] 1 _[.]_ _.._ [76] 2472 9 _._ 89 [+] − [0] 0 _[.]_ _._ [72] 71

HERMESJ105751 + 573026 2 20 _._ 98 – [+] − [0] 0 _[.]_ _._ [70] 81 20 _._ 67 – [+] − [0] 1 _[.]_ _._ [99] 12 0 _._ 16 [+] − – [0] 0 _[.]_ _._ [19] 08 11 _._ 33 [+] − [4] 2 _[.]_ _._ [02] 77

HERMESJ105751 + 573026 3 21 _._ 93 – [+] − [0] 0 _[.]_ _._ [22] 20 20 _._ 72 – [+] − [0] 0 _[.]_ _._ [15] 13 [0] _[.]_ [124][ ±] – [ 0] _[.]_ [008] 6 _._ 39 ± 0 _._ 49

HERMESJ105751 + 573026 4 21 _._ 59 – [+] − [0] 0 _[.]_ _._ [10] 09 21 _._ 16 ± – 0 _._ 05 0 _._ 172 ± – 0 _._ 0066 _._ 987+−00 _.._ 002001

HERMESJ105751 + 573026 5 21 _._ 58 – [+] − [0] 0 _[.]_ _._ [19] 18 20 _._ 30 – [+] − [0] 0 _[.]_ _._ [13] 12 [0] _[.]_ [124][ ±] – [ 0] _[.]_ [007] 5 _._ 60 ± 0 _._ 34

HERMESJ105751 + 573026 6 [23 – _._ 60] –– –– –



−20 _._ 47 [+] − [0] 0 _[.]_ _._ [20] 19 [21] _[.]_ [43][+] − [0] 0 _[.]_ _._ [19] 20 18 _._ 16 [+] − [1] 1 _[.]_ _._ [76] 72



S_34



43 _._ 86 ± 0 _._ 21



S_35HATLASJ132630 + 334410 −1820 _._ 76 _._ 23 ± ± 0 0 _._ 06 _._ 06 2321 _.._ 8028 ± ± 0 0 _.._ 0404 151 _._ 95 _._ 00 ± [+] − 0 [0] 0 _[.]_ _.._ [32] 0431 10 _._ 11+−00 _.._ 1918 [1] _[.]_ [34][ ±][ 0] _[.]_ [06]



−18 _._ 83 [+] − [0] 0 _[.]_ _._ [12] 11 [19] _[.]_ [38][+] − [0] 0 _[.]_ _._ [08] 07 4 _._ 90 ± 0 _._ 22



S_36



15 _._ 09 ± 0 _._ 23



MNRAS **000**, 1–57 (2022)

50 _E. Borsato et al._


**Table A2** – _continued_


No. IAU Name _𝑚𝐹_ 110 _𝑊_ _𝜇_ 50 _𝑅_ 50 _𝐶_ 31 _𝜇𝑆_ 1 _._ 1

[mag] [mag arcsec [−][2] ] [arcsec] [ _𝜇_ Jy]
_𝑀𝐹_ 110 _𝑊_ _𝜇_ 50 _,_ 0 _𝑅_ 50 _,_ 0

[mag] [mag kpc [−][2] ] [kcp]
(1) (2) (3) (4) (5) (6) (7)


S_37HATLASJ142140 + 000448 20 _._ 34 ± 0 _._ 10 21 _._ 27 [+] − [0] 0 _[.]_ _._ [07] 06 0 _._ 36 ± 0 _._ 01 4 _._ 44 ± 0 _._ 10 3 _._ 24 ± 0 _._ 05
−19 _._ 62 [+] − [1] 0 _[.]_ _._ [19] 80 18 _._ 00 [+] − [0] 0 _[.]_ _._ [91] 73 3 _._ 08 [+] − [0] 0 _[.]_ _._ [17] 34


S_38HERMESJ142824 + 352620 20 _._ 69 [+] − [0] 0 _[.]_ _._ [12] 11 21 _._ 47 [+] − [0] 0 _[.]_ _._ [08] 07 0 _._ 34 ± 0 _._ 01 4 _._ 64 ± 0 _._ 13 1 _._ 93 ± 0 _._ 05
−19 _._ 04 [+] − [0] 0 _[.]_ _._ [12] 11 18 _._ 38 [+] − [0] 0 _[.]_ _._ [08] 07 2 _._ 81 ± 0 _._ 11

S_39HATLASJ223753.8 − 305828 − [19] 18 _[.]_ [09] _._ 92 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [08] _[.]_ 07 _._ [79] 63 2119 _.._ 8193 ± [+] − [0] 0 0 _[.]_ _._ [43] _._ 3905 04 _.._ 7055 ± [+] − [0] 0 0 _[.]_ _._ [53] _._ 7202 8 _._ 77 [+] − [0] 0 _[.]_ _._ [18] 17 3 _._ 56 ± 0 _._ 08

S_40HATLASJ225250.7 − 313657 − [21] 17 _[.]_ [31] _._ 32 [+] − [+] − [0] 0 [1] 0 _[.]_ _._ [17] _[.]_ 16 _._ [21] 86 1922 _.._ 9723 [+][+] −− [0][0] 00 _[.][.]_ _.._ [72][12] 6310 02 _.._ 2909 ± [+] − [0] 0 0 _[.]_ _._ [27] _._ 4302 11 _._ 10 [+] − [0] 0 _[.]_ _._ [86] 81 2 _._ 04 ± 0 _._ 03

S_41HELMSJ233441.0 − 065220 −1918 _._ 79 _._ 09 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [17] _[.]_ 16 _._ [17] 16 [19] 21 _[.]_ _._ [23] 04 [ ±] ± [ 0] 0 _[.]_ _._ [51] 51 20 _.._ 4438 [+][+] −− [0][0] 00 _[.][.]_ _.._ [53][08] 3505 5 _._ 13 [+] − [0] 0 _[.]_ _._ [39] 40 172 _._ 09 ± 0 _._ 22

S_42HELMSJ233633.5 − 032119 1 16 _._ 99 – [+] − [0] 0 _[.]_ _._ [05] 04 20 _._ 94 ± – 0 _._ 08 1 _._ 29 ± – 0 _._ 06 7 _._ 24 [+] − [0] 0 _[.]_ _._ [28] 29 14 _._ 41 ± 0 _._ 21

HELMSJ233633.5 − 032119 2 19 _._ 16 ± – 0 _._ 08 23 _._ 16 – [+] − [0] 0 _[.]_ _._ [06] 05 1 _._ 53 ± – 0 _._ 04 4 _._ 34 ± 0 _._ 06


_Confirmed through sub-mm/mm follow-up_

S_43HELMSJ001615.7 + 032435 −1820 _._ 24 _._ 31 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [36] _[.]_ 34 _._ [36] 34 2123 _.._ 4364 [+][+] −− [0][0] 00 _[.][.]_ _.._ [18][18] 1616 182 _.._ 5425 [+] − [+] − [0] 0 [1] 1 _[.]_ _._ _[.]_ [24] _._ 22 [76] 62 9 _._ 16 [+] − [1] 1 _[.]_ _._ [47] 63 _<_ 0 _._ 04


S_44HELMSJ002220.9 − 015524 21 _._ 07 [+] − [0] 0 _[.]_ _._ [15] 14 25 _._ 43 [+] − [0] 0 _[.]_ _._ [10] 09 1 _._ 59 ± 0 _._ 08 6 _._ 62 ± 0 _._ 31 _<_ 0 _._ 04
−18 _._ 27 [+] − [0] 0 _[.]_ _._ [50] 44 22 _._ 66 [+] − [0] 0 _[.]_ _._ [36] 34 12 _._ 62 [+] − [0] 0 _[.]_ _._ [82] 90

S_45HELMSJ003814.1 − 002252 −12[22 _._ 66 _._ 45 [+] − [1] 0] _[.]_ _._ [43] 95 –– –– – _<_ 0 _._ 04

S_46HELMSJ003929.6 + 002426 [22] −16 _[.]_ [398] _._ 34 [ ±][+] − [ 0][0] 0 _[.][.]_ _._ [99][003] 73 19 [22] _._ _[.]_ 83 [17][+][+] −− [0][0] 00 _[.][.]_ _.._ [61][02] 5301 [0] _[.]_ 1 [256] _._ 90 [ ±][+] − [0] 0 [ 0] _[.]_ _._ [18] _[.]_ 31 [003] 2 _._ 38 [+] − [0] 0 _[.]_ _._ [08] 09 _<_ 0 _._ 04

S_47HELMSJ004714.2 + 032454 −2017 _._ 25 _._ 43 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [24] _[.]_ 23 _._ [54] 48 2123 _.._ 3807 [+][+] −− [0][0] 00 _[.][.]_ _.._ [31][17] 3016 05 _.._ 9257 ± [+] − [1] 1 0 _[.]_ _._ [05] _._ 0414 4 _._ 40 [+] − [0] 0 _[.]_ _._ [61] 60 _<_ 0 _._ 04



**Table A2** – _continued_


No. IAU Name _𝑚_ _𝐹_ 110 _𝑊_ _𝜇_ 50 _𝑅_ 50 _𝐶_ 31

[mag] [mag arcsec [−][2] ] [arcsec]
_𝑀_ _𝐹_ 110 _𝑊_ _𝜇_ 50 _,_ 0 _𝑅_ 50 _,_ 0

[mag] [mag kpc [−][2] ] [kcp]
(1) (2) (3) (4) (5) (6)



S_60



HATLASJ141352 − 000027 1 −1819 _._ 19 _._ 85 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [18] _[.]_ 17 _._ [18] 17 2022 _.._ 2111 [+][+] −− [0][0] 00 _[.][.]_ _.._ [43][43] 4242 81 _.._ 0122 [+][+] −− [1][0] 10 _[.][.]_ _.._ [52][23] 1718 7 _._ 67 ± 0 _._ 48

HATLASJ141352-000027 2 20 _._ 91 – [+] − [0] 0 _[.]_ _._ [13] 12 21 _._ 05 ± – 0 _._ 08 0 _._ 229 ± – 0 _._ 010 6 _._ 40 +−00 _.._ 2726

HATLASJ141352 − 000027 3 −1918 _._ 18 _._ 87 ± ± 0 0 _._ 08 _._ 08 1921 _.._ 6979 ± ± 0 0 _.._ 0505 04 _._ 64 _._ 20 ± [+] − [0] 0 0 _[.]_ _._ [10] _._ 11 02 8 _._ 56 ± 0 _._ 18



_<_ 0 _._ 04



S_61HATLASJ142414 + 022304 1 −1918 _.._ 9531 [+] ± − [0] 0 0 _[.]_ _._ [09] 08 _._ 09 2321 _.._ 0468 ± ± 0 0 _.._ 0905 17 _._ 11 _._ 65 ± [+] − [0] 0 0 _[.]_ _._ [39] _._ 40 06 10 _._ 30 +−00 _.._ 6453 _<_ 0 _._ 03

HATLASJ142414 + 022304 2 −2117 _._ 05 _._ 21 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [15] _[.]_ 14 _._ [15] 14 2422 _.._ 5956 [+][+] −− [0][0] 00 _[.][.]_ _.._ [10][10] 0909 06 _._ 93 _._ 41 ± [+] − [0] 0 0 _[.]_ _._ [31] _._ 30 05 12 _._ 87 +−00 _.._ 8480


19 _._ 254 ± 0 _._ 001 20 _._ 801 ± 0 _._ 0070 _._ 542 ± 0 _._
S_62HERMESJ142826+345547 −18 _._ 065 ± 0 _._ 00119 _._ 297 ± 0 _._ 007 3 _._ 07 ± 0 _._ 003202 _._ 56 ± 0 _._ 03 _<_ 0 _._ 03

S_63HATLASJ230815.5 − 343801 −2018 _._ 18 _._ 58 [+] − [+] − [0] 0 [0] _[.]_ 0 _._ [21] _[.]_ 20 _._ [93] 72 2219 _.._ 1580 [+][+] −− [0][0] 00 _[.][.]_ _.._ [13][59] 1152 04 _.._ 5505 [+][+] −− [0][0] 00 _[.][.]_ _.._ [02][42] 0360 7 _._ 71 [+] − [1] 1 _[.]_ _._ [59] 35 _[<]_ [ 0] _[.]_ [04]

S_64HELMSJ232439.5 − 043936 −2018 _._ 34 _._ 21 [+] − [+] − [0] 0 [1] _[.]_ 0 _._ [21] _[.]_ 20 _._ [27] 89 2119 _.._ 6444 [+][+] −− [0][0] 00 _[.][.]_ _.._ [31][77] 2667 02 _._ 40 _._ 86 ± [+] − [0] 0 0 _[.]_ _._ [43] _._ 65 03 5 _._ 96 [+] − [0] 0 _[.]_ _._ [32] 29 _[<]_ [ 0] _[.]_ [04]


S_65HELMSJ233620.8 − 060828 −1719 _._ 97 _._ 24 ± ± 0 0 _._ 07 _._ 07 1820 _.._ 3994 ± ± 0 0 _.._ 0505 03 _.._ 6662 ± ± 0 0 _.._ 0209 6 _._ 58 [+] − [0] 0 _[.]_ _._ [20] 19 _[<]_ [ 0] _[.]_ [04]



HELMSJ005159.5 + 062241 1 18 _._ 36 ± 0 _._ 09 22 _._ 71 [+][+] − [0][0] 0 _[.]_ _._ [10][10] 12 1 _._ 67 [+] − [+][0] 0 [0] _[.]_ _._ [11] 12 [74] 5 _._ 95 [+] − [0] 0 _[.]_ _._ [91] 64



−19 _._ 94 ± 0 _._ 09 20 _._ 66 [+] − [0] 0 _[.]_ _._ [10] 12 11 _._ 54 [+] − [0] 0 _[.]_ _._ [74] 80 −0 _._ 64
HELMSJ005159.5 + 062241 2 20 _._ 87 ± – 0 _._ 06 20 _._ 48 ± – 0 _._ 03 0 _._ 176 ± – 0 _._ 004 6 _._ 987+−00 _.._ 001002 _<_ 0 _._ 04



S_48



HELMSJ005159.5 + 062241 3 −2018 _._ 03 _._ 24 ± ± 0 0 _._ 09 _._ 09 2321 _.._ 7875 ± ± 0 0 _.._ 0505 19 _.._ 4278 ± [+] − [0] 0 0 _[.]_ _._ [41] _._ 4206 4 _._ 08 [+] − [0] 0 _[.]_ _._ [13] 11

S_49HATLASJ005724.2 − 273122 − [20] 19 _[.]_ [36] _._ 00 [ ±][+] − [ 0][1] 0 _[.][.]_ _._ [52][10] 99 2224 _.._ 0583 [+][+] −− [1][0] 00 _[.][.]_ _.._ [01][07] 8306 101 _._ 35 _._ 76 ± [+] − 0 [0] 2 _[.]_ _.._ [88] 0522 18 _._ 23 [+] − [0] 0 _[.]_ _._ [86] 84 _<_ 0 _._ 05


S_51HERMESJ033211 − 270536 [23 – _._ 01] –– –– – _<_ 0 _._ 03


S_52HERMESJ044154 − 540352 19 _._ 64 – [+] − [0] 0 _[.]_ _._ [09] 08 21 _._ 75 ± – 0 _._ 06 0 _._ 48 ± – 0 _._ 01 13 _._ 98 [+] − [0] 0 _[.]_ _._ [40] 41 _<_ 0 _._ 03


S_53HATLASJ083932 − 011760 19−17 _._ 992 _._ 34 ± [+] − 0 [0] 0 _[.]_ _.._ [84] 00265 2119 _.._ 1665 ± [+] − [0] 0 0 _[.]_ _._ [38] _._ 3501 0 _._ 2458 _._ 60 ± [+] − [0] 0 0 _[.]_ _._ [38] _._ 50005 2 _._ 18 ± 0 _._ 03 _<_ 0 _._ 03

S_54HATLASJ091841 + 023048 1 −2018 _._ 48 _._ 92 [+] − [+] − [0] 0 [1] 0 _[.]_ _._ [17] _[.]_ 16 _._ [12] 80 2225 _.._ 4327 [+][+] −− [0][0] 00 _[.][.]_ _.._ [82][24] 7130 141 _.._ 8530 [+] − [+] − [0] 0 [2] 3 _[.]_ _._ _[.]_ [30] _._ 34 [89] 32 9 _._ 93 [+] − [5] 2 _[.]_ _._ [55] 95 _<_ 0 _._ 04
HATLASJ091841 + 023048 2 −2216 _._ 56 _._ 84 ± [+] − 0 [1] 0 _[.]_ _.._ [12] 1180 2118 _.._ 8097 ± [+] − [0] 0 0 _[.]_ _._ [78] _._ 6706 0 _._ 1148 _._ 18 ± [+] − [0] 0 0 _[.]_ _._ [09] _._ 170066 _._ 9849+−00 _.._ 00290010

S_56HATLASJ115433.6 + 005042 − [20] 17 _[.]_ [89] _._ 03 [ ±][+] − [ 0][0] 0 _[.][.]_ _._ [62][13] 51 1921 _.._ 2810 [+][+] −− [0][0] 00 _[.][.]_ _.._ [33][08] 3107 01 _.._ 2879 ± [+] − [0] 0 0 _[.]_ _._ [19] _._ 2301 3 _._ 83 [+] − [0] 0 _[.]_ _._ [10] 11 _<_ 0 _._ 03

S_57HATLASJ120127.6 − 014043 − [20] 18 _[.]_ [85] _._ 43 [ ±][+] − [ 0][1] 0 _[.][.]_ _._ [34][19] 91 1720 _.._ 8144 [+][+] −− [1][0] 00 _[.][.]_ _.._ [06][60] 9142 10 _.._ 3718 [+][+] −− [0][0] 00 _[.][.]_ _.._ [36][04] 2903 8 _._ 27 [+] − [3] 1 _[.]_ _._ [41] 67 _<_ 0 _._ 04

S_58HATLASJ131611 + 281220 −2117 _._ 87 _._ 48 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [22] _[.]_ 20 _._ [46] 42 1922 _.._ 9168 [+][+] −− [0][0] 00 _[.][.]_ _.._ [34][15] 3313 02 _.._ 2931 ± [+] − [0] 0 0 _[.]_ _._ [18] _._ 1902 8 _._ 86 [+] − [0] 0 _[.]_ _._ [84] 78 _<_ 0 _._ 03

S_59HATLASJ134429 + 303036 −1919 _._ 57 _._ 01 [+] − [+] − [0] 0 [0] 0 _[.]_ _._ [32] _[.]_ 30 _._ [32] 30 1820 _.._ 6185 [+][+] −− [0][0] 00 _[.][.]_ _.._ [73][73] 6969 20 _.._ 7438 [+][+] −− [1][0] 00 _[.][.]_ _.._ [00][14] 5808 6 _._ 09 [+] − [0] 0 _[.]_ _._ [69] 68 _<_ 0 _._ 04


MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 51


**Table B1.** Properties of the 217 systems classified as B, C and D by visual inspection


No. IAU Name Alt. Name Ref. RA Dec Vis. Class. Multiw. Class. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)



.



S_66 HELMSJ000215.9 − 012829 HELMS3 Na16 00:02:16 − 01:28:29.00 B – 643 _._ 0 ± 7 _._ 0 510 _._ 0 ± 6 _._ 0 258 _._ 0 ± 7 _._ 0 Na16

S_67 HELMSJ001800.1 − 060235 HELMS21 Na16 00:18:00 − 06:02:35.00 B – 206 _._ 0 ± 6 _._ 0 186 _._ 0 ± 7 _._ 0 130 _._ 0 ± 7 _._ 0 Na16

S_68 HELMSJ002208.1 + 034044 HELMS38 Na16 00:22:08 + 03:40:44.00 B – 190 _._ 0 ± 6 _._ 0 157 _._ 0 ± 6 _._ 0 113 _._ 0 ± 7 _._ 0 Na16

S_69 HATLASJ002533.5 − 333825 HerBS87 Ba18 00:25:34 − 33:38:26.00 B – 114 _._ 7 ± 5 _._ 2 127 _._ 8 ± 6 _._ 1 96 _._ 0 ± 7 _._ 3 Ba18

S_70 HERMESJ002906 − 421419 HELAISS01 Wa13 00:29:06 − 42:14:19.00 B – 129 _._ 0 116 _._ 0 81 _._ 0 Ca14

S_71 HATLASJ003207.7 − 303724 HerBS56 Ba18 00:32:08 − 30:37:24.00 B – 80 _._ 3 ± 5 _._ 0 106 _._ 2 ± 5 _._ 2 105 _._ 8 ± 6 _._ 3 Ne17

S_72 HERMESJ003824 − 433705 HELAISS02 Ca14 00:38:24 − 43:37:05.00 B D 115 _._ 0 ± 6 _._ 0 124 _._ 0 ± 6 _._ 0 108 _._ 0 ± 6 _._ 0 Bu15

S_73 HELMSJ004747.1 + 061444 HELMS26 Na16 00:47:47 + 06:14:44.00 B – 85 _._ 0 ± 7 _._ 0 119 _._ 0 ± 6 _._ 0 125 _._ 0 ± 8 _._ 0 Na16

S_74 HERSJ010301.2 − 003300 HERS6 Na16 01:03:01 − 00:33:01.00 B – 121 _._ 0 ± 7 _._ 0 147 _._ 0 ± 6 _._ 0 130 _._ 0 ± 8 _._ 0 Na16

S_75 HERSJ011640.1 − 000454 HERS4 Na16 01:16:40 − 00:04:54.00 B – 137 _._ 5 ± 6 _._ 75 196 _._ 11 ± 6 _._ 56 189 _._ 91 ± 7 _._ 81 Su17

S_76 HATLASJ012415.9 − 310500 HerBS69 Ba18 01:24:16 − 31:05:00.00 B – 140 _._ 4 ± 5 _._ 4 154 _._ 5 ± 5 _._ 7 100 _._ 3 ± 7 _._ 0 Ne17

S_77 HERSJ012521.0 + 011724 HERS13 Na16 01:25:21 + 01:17:24.00 B – 165 _._ 0 ± 8 _._ 0 153 _._ 0 ± 7 _._ 0 114 _._ 0 ± 10 _._ 0 Na16

S_78 HERSJ012546.3 − 001143 HERS12 Na16 01:25:46 − 00:11:43.00 B – 152 _._ 0 ± 8 _._ 0 135 _._ 0 ± 7 _._ 0 114 _._ 0 ± 9 _._ 0 Na16

S_79 HERSJ012754.1 + 004940 HERS3 Na16 01:27:54 + 00:49:40.00 B – 253 _._ 0 ± 6 _._ 0 250 _._ 0 ± 6 _._ 0 191 _._ 0 ± 7 _._ 0 Na16

S_80 HATLASJ012853.0 − 332719 HerBS73 Ba18 01:28:53 − 33:27:19.00 B – 117 _._ 1 ± 6 _._ 0 129 _._ 0 ± 6 _._ 2 99 _._ 6 ± 7 _._ 4 Ba18

S_81 HATLASJ013840.5 − 281855 HerBS14 Ba18 01:38:41 − 28:18:56.00 B Unc. 116 _._ 3 ± 5 _._ 7 177 _._ 0 ± 6 _._ 0 179 _._ 4 ± 7 _._ 1 Ne17

S_82 HATLASJ013951.9 − 321446 HerBS55 Ba18 01:39:52 − 32:14:46.00 B – 109 _._ 0 ± 4 _._ 9 116 _._ 5 ± 5 _._ 3 107 _._ 1 ± 6 _._ 2 Ne17

S_83 HERSJ021402.6 − 004612 HERS17 Na16 02:14:03 − 00:46:12.00 B – 110 _._ 0 ± 8 _._ 0 130 _._ 0 ± 8 _._ 0 105 _._ 0 ± 9 _._ 0 Na16

S_84 HERSJ021434.4 + 005926 HERS16 Na16 02:14:34 + 00:59:26.00 B – 110 _._ 0 ± 9 _._ 0 134 _._ 0 ± 8 _._ 0 109 _._ 0 ± 10 _._ 0 Na16

S_85 HERMESJ022017 − 060143 HXMM01 Wa13 02:20:17 − 06:01:44.00 B Unc. 179 _._ 0 ± 7 _._ 0 188 _._ 0 ± 8 _._ 0 134 _._ 0 ± 7 _._ 0 Bu15

S_86 HERMESJ022022 − 015329 HXMM04 Wa13 02:20:22 − 01:53:29.00 B D 162 _._ 0 ± 7 _._ 0 157 _._ 0 ± 8 _._ 0 125 _._ 0 ± 11 _._ 0 Bu15

S_87 HERMESJ022029 − 064846 HXMM09 Wa13 02:20:29 − 06:48:46.00 B D 129 _._ 0 ± 7 _._ 0 118 _._ 0 ± 8 _._ 0 85 _._ 0 ± 7 _._ 0 Bu15

S_88 HERMESJ022135 − 062617 HXMM03 Wa13 02:21:35 − 06:26:17.00 B Unc. 114 _._ 0 ± 7 _._ 0 134 _._ 0 ± 8 _._ 0 116 _._ 0 ± 7 _._ 0 Bu15

S_89 HERMESJ022548 − 041750 HXMM05 Wa13 02:25:48 − 04:17:50.00 B D 103 _._ 0 ± 7 _._ 0 118 _._ 0 ± 8 _._ 0 97 _._ 0 ± 7 _._ 0 Bu15

S_90 HERMESJ045027 − 524126 HADFS08 Ca14 04:50:27 − 52:41:26.00 B D 142 _._ 0 ± 6 _._ 0 133 _._ 0 ± 6 _._ 0 90 _._ 0 ± 6 _._ 0 Bu15

S_91 HERMESJ045058 − 531654 HADFS03 Ca14 04:50:58 − 53:16:54.00 B Unc. 119 _._ 0 ± 6 _._ 0 102 _._ 0 ± 6 _._ 0 63 _._ 0 ± 6 _._ 0 Bu15

S_92 HATLASJ084933 + 021443 G09-v1.124 08:49:33 + 02:14:43.14 B D 216 _._ 7 ± 7 _._ 5 248 _._ 5 ± 8 _._ 2 208 _._ 6 ± 8 _._ 6 Ne17

HerBS8 Ba18

S_93 HATLASJ084958 + 010713 G09v1.1259 08:49:58 + 01:07:12.73 B – 81 _._ 2 ± 7 _._ 3 98 _._ 9 ± 8 _._ 2 85 _._ 2 ± 8 _._ 7 Ba18

HerBS157 Ba18

S_94 HATLASJ090453.2 + 022017 HerBS183 Ba18 09:04:53 + 02:20:17.87 B – 87 _._ 0 ± 7 _._ 2 98 _._ 2 ± 8 _._ 0 82 _._ 3 ± 8 _._ 8 Ba18

SDP.392

S_95 HATLASJ091331 − 003644 SDP.44 09:13:31 − 00:36:44.00 B – 175 _._ 5 ± 6 _._ 5 142 _._ 2 ± 7 _._ 4 85 _._ 8 ± 7 _._ 8 Va16

S_96 HATLASJ092136 + 000132 HerBS91 Ba18 09:21:36 + 00:01:31.92 B – 139 _._ 2 ± 7 _._ 3 128 _._ 8 ± 8 _._ 1 95 _._ 1 ± 8 _._ 6 Ba18

S_97 HATLASJ092409 − 005018 HerBS185 09:24:09 − 00:50:18.00 B – 71 _._ 8 ± 7 _._ 4 87 _._ 7 ± 8 _._ 2 82 _._ 2 ± 8 _._ 5 Ba18

S_98 HERMESJ103618 + 585454 HLock05 Wa13 10:36:18 + 58:54:54.36 B – 71 _._ 0 102 _._ 0 98 _._ 0 Ca14

S_99 HATLASJ113804 − 011736 HerBS96 Ba18 11:38:04 − 01:17:36.00 B – 85 _._ 1 ± 7 _._ 3 98 _._ 4 ± 8 _._ 2 94 _._ 8 ± 8 _._ 8 Ba18

S_100 HATLASJ113833.3 + 004909 HerBS100 Ba18 11:38:33 + 00:49:09.68 B – 96 _._ 8 ± 7 _._ 3 106 _._ 4 ± 8 _._ 1 93 _._ 4 ± 8 _._ 7 Ba18

S_101 HATLASJ113841 − 020237 – – 11:38:41 − 02:02:37.00 B – 45 _._ 2 ± 7 _._ 0 72 _._ 7 ± 7 _._ 7 71 _._ 7 ± 8 _._ 1 Ma18

S_102 HATLASJ115112 − 012638 HerBS53 Ba18 11:51:12 − 01:26:38.00 B – 141 _._ 2 ± 7 _._ 4 137 _._ 7 ± 8 _._ 2 108 _._ 4 ± 8 _._ 8 Ne17

S_103 HATLASJ115120 − 003322 – – 11:51:20 − 00:33:22.00 B – 146 _._ 9 ± 7 _._ 8 150 _._ 3 ± 8 _._ 5 88 _._ 0 ± 8 _._ 8 Ma18

S_104 HATLASJ120127.8 − 021648 – – 12:01:28 − 02:16:48.00 B – 207 _._ 9 ± 7 _._ 3 160 _._ 9 ± 8 _._ 2 103 _._ 6 ± 8 _._ 7 Ne17

S_105 HATLASJ120319.1 − 011253 HerBS50 Ba18 12:03:19 − 01:12:54.00 B – 114 _._ 3 ± 7 _._ 4 142 _._ 8 ± 8 _._ 2 110 _._ 2 ± 8 _._ 6 Ne17

S_106 HATLASJ121301.5 − 004922 HerBS48 Ba18 12:13:02 − 00:49:23.00 B – 136 _._ 6 ± 6 _._ 6 142 _._ 6 ± 7 _._ 4 110 _._ 9 ± 7 _._ 7 Ne17

S_107 HATLASJ121334.9 − 020323 – – 12:13:35 − 02:03:23.00 B – 211 _._ 0 197 _._ 9 129 _._ 9 Ne17

S_108 HATLASJ121542.7 − 005220 HerBS62 Ba18 12:15:43 − 00:52:20.00 B – 119 _._ 7 ± 7 _._ 4 135 _._ 5 ± 8 _._ 2 103 _._ 4 ± 8 _._ 6 Ne17

S_109 HATLASJ130054 + 260303 HerBS129 Ba18 13:00:54 + 26:03:02.68 B – 59 _._ 4 ± 5 _._ 9 85 _._ 4 ± 5 _._ 9 89 _._ 0 ± 7 _._ 0 Ba18

S_110 HATLASJ131322 + 285836 – – 13:13:22 + 28:58:35.61 B – 160 _._ 8 ± 7 _._ 4 116 _._ 0 ± 8 _._ 4 68 _._ 0 ± 8 _._ 8 Ma18

S_111 HATLASJ134159 + 292833 – – 13:41:59 + 29:28:32.54 B – 174 _._ 4 ± 6 _._ 7 172 _._ 3 ± 7 _._ 7 109 _._ 2 ± 8 _._ 1 Ne17

S_112 HATLASJ141833 + 010212 HerBS110 Ba18 14:18:33 + 01:02:12.40 B – 66 _._ 0 106 _._ 5 92 _._ 8 Ba18

S_113 HERMESJ142201 + 533214 HEGS01 14:22:01 + 53:32:13.70 B – 74 _._ 0 98 _._ 0 89 _._ 0 Ca14

S_114 HATLASJ142318.3 + 013913 – – 14:23:18 + 01:39:13.80 B – 61 _._ 8 ± 7 _._ 5 83 _._ 0 ± 8 _._ 2 65 _._ 1 ± 8 _._ 8 Ma18

S_115 HATLASJ143203 − 005219 – – 14:32:03 − 00:52:19.00 B – 160 _._ 6 ± 7 _._ 6 125 _._ 0 ± 8 _._ 3 76 _._ 1 ± 8 _._ 9 Ma18

S_116 HERMESJ143331 + 345440 HBootes01 14:33:31 + 34:54:39.60 B Unc. 158 _._ 0 191 _._ 0 160 _._ 0 Ca14

S_117 HATLASJ144243 + 015506 HerBS153 Ba18 14:42:43 + 01:55:05.86 B – 123 _._ 2 ± 7 _._ 2 133 _._ 4 ± 8 _._ 1 85 _._ 7 ± 8 _._ 8 Ba18

S_118 HATLASJ144715 − 012114 – – 14:47:15 − 01:21:14.00 B – 132 _._ 7 ± 7 _._ 3 118 _._ 9 ± 8 _._ 2 74 _._ 7 ± 8 _._ 6 Ma18

S_119 HATLASJ222503.7 − 304847 HerBS166 Ba18 22:25:04 − 30:48:48.00 B D 32 _._ 4 ± 7 _._ 2 50 _._ 1 ± 8 _._ 5 84 _._ 3 ± 10 _._ 3 Ba18

UR085S

S_120 HATLASJ223942.4 − 333304 HerBS111 Ba18 22:39:42 − 33:33:04.00 B – 105 _._ 9 ± 6 _._ 5 115 _._ 6 ± 6 _._ 2 92 _._ 7 ± 7 _._ 4 Ba18

S_121 HATLASJ224026.5 − 315154 HerBS148 Ba18 22:40:27 − 31:51:55.00 B – 120 _._ 6 ± 5 _._ 0 121 _._ 2 ± 5 _._ 5 86 _._ 3 ± 6 _._ 8 Ba18

S_122 HATLASJ224759.6 − 310134 HerBS141 Ba18 22:48:00 − 31:01:35.00 B – 122 _._ 1 ± 6 _._ 1 124 _._ 4 ± 6 _._ 5 87 _._ 3 ± 7 _._ 5 Ba18



_Notes_ : Col. (1): Source reference number. Col. (2): IAU name of the _Herschel_ detection. Cols. (3) and (4): Alternative name and reference. Cols. (5) and (6):
ICRS RA and Dec coordinate (J2000.0) of the _Herschel_ detection. Cols. (7) and (8): Visual and multiwavelength lens classifications. Col. (9), (10), (11), and
(11): SPIRE flux density at 250 _𝜇_ m, 350 _𝜇_ m, 500 _𝜇_ m and reference.


MNRAS **000**, 1–57 (2022)

52 _E. Borsato et al._


**Table B1** – _continued_


No. IAU Name Alt. Name Ref. RA Dec Vis. Class. Multiw. Class. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)


S_123 HATLASJ224805.3 − 335820 HerBS33 Ba18 22:48:05 − 33:58:20.00 B – 122 _._ 3 ± 5 _._ 7 135 _._ 5 ± 6 _._ 3 126 _._ 9 ± 7 _._ 2 Ne17

S_124 HATLASJ225045.5 − 304719 HerBS168 Ba18 22:50:46 − 30:47:19.00 B – 65 _._ 5 ± 6 _._ 1 88 _._ 1 ± 6 _._ 1 84 _._ 0 ± 7 _._ 5 Na16

S_125 HATLASJ230546.2 − 331038 HerBS49 Ba18 23:05:46 − 33:10:39.00 B – 76 _._ 8 ± 5 _._ 6 110 _._ 9 ± 5 _._ 9 110 _._ 4 ± 7 _._ 0 Ne17

S_126 HELMSJ231447.5 − 045658 HELMS44 Na16 23:14:48 − 04:56:58.00 B – 220 _._ 0 ± 8 _._ 0 141 _._ 0 ± 7 _._ 0 106 _._ 0 ± 8 _._ 0 Na16

S_127 HATLASJ232210.9 − 333749 HerBS146 Ba18 23:22:11 − 33:37:49.00 B – 122 _._ 4 ± 5 _._ 2 134 _._ 6 ± 5 _._ 4 86 _._ 6 ± 6 _._ 8 Ba18

S_128 HATLASJ232531.3 − 302235 HerBS17 Ba18 23:25:31 − 30:22:36.00 B – 175 _._ 5 ± 4 _._ 3 227 _._ 0 ± 4 _._ 7 175 _._ 7 ± 5 _._ 7 Ne17

S_129 HELMSJ232617.5 − 025319 HELMS51 Na16 23:26:18 − 02:53:19.00 B – 86 _._ 0 ± 6 _._ 0 109 _._ 0 ± 6 _._ 0 104 _._ 0 ± 7 _._ 0 Na16

S_130 HELMSJ232831.8 − 004035 HELMS55 Na16 23:28:32 − 00:40:35.00 B – 95 _._ 0 ± 7 _._ 0 120 _._ 0 ± 6 _._ 0 102 _._ 0 ± 7 _._ 0 Na16

S_131 HELMSJ232833.6 − 031416 HELMS48 Na16 23:28:34 − 03:14:16.00 B – 49 _._ 0 ± 6 _._ 0 104 _._ 0 ± 6 _._ 0 105 _._ 0 ± 8 _._ 0 Na16

S_132 HELMSJ233420.4 − 003458 HELMS43 Na16 23:34:20 − 00:34:58.00 B – 156 _._ 0 ± 7 _._ 0 141 _._ 0 ± 5 _._ 0 109 _._ 0 ± 8 _._ 0 Na16

S_133 HELMSJ233721.9 − 064740 HELMS49 Na16 23:37:22 − 06:47:40.00 B – 173 _._ 0 ± 6 _._ 0 161 _._ 0 ± 7 _._ 0 105 _._ 0 ± 8 _._ 0 Na16

S_134 HELMS233728.8 − 045106 HELMS20 Na16 23:37:29 − 04:51:06.00 B – 162 _._ 0 ± 6 _._ 0 178 _._ 0 ± 7 _._ 0 132 _._ 0 ± 8 _._ 0 Na16

S_135 HELMSJ234314.0 + 012152 HELMS36 Na16 23:43:14 + 01:21:52.00 B – 115 _._ 0 ± 6 _._ 0 115 _._ 0 ± 6 _._ 0 113 _._ 0 ± 8 _._ 0 Na16

S_136 HATLASJ234955.7 − 330833 HerBS184 Ba18 23:49:56 − 33:08:33.00 B – 91 _._ 9 ± 5 _._ 9 107 _._ 6 ± 6 _._ 0 82 _._ 3 ± 7 _._ 1 Ba18

S_137 HELMSJ235101.7 − 024425 HELMS50 Na16 23:51:02 − 02:44:26.00 B – 112 _._ 0 ± 6 _._ 0 124 _._ 0 ± 6 _._ 0 105 _._ 0 ± 7 _._ 0 Na16

S_138 HATLASJ235121.9 − 332902 HerBS159 Ba18 23:51:22 − 33:29:02.00 B Unc. 92 _._ 1 ± 5 _._ 9 98 _._ 3 ± 5 _._ 9 85 _._ 0 ± 7 _._ 1 Ba18

S_139 HELMSJ235331.7 + 031717 HELMS40 Na16 23:53:32 + 03:17:18.00 B – 102 _._ 0 ± 6 _._ 0 123 _._ 0 ± 7 _._ 0 111 _._ 0 ± 7 _._ 0 Na16

S_140 HATLASJ000455.3 − 330811 HerBS170 Ba18 00:04:55 − 33:08:12.00 C D 61 _._ 9 ± 5 _._ 4 78 _._ 8 ± 6 _._ 0 83 _._ 8 ± 7 _._ 0 Ba18

S_141 HATLASJ001030.1 − 330621 HerBS98 Ba18 00:10:30 − 33:06:22.00 C – 56 _._ 3 ± 4 _._ 9 51 _._ 7 ± 5 _._ 0 94 _._ 4 ± 6 _._ 5 Ba18

S_142 HELMSJ001226.9 + 020810 HELMS45 Na16 00:12:27 + 02:08:10.00 C – 107 _._ 0 ± 6 _._ 0 142 _._ 0 ± 6 _._ 0 106 _._ 0 ± 7 _._ 0 Na16

S_143 HELMSJ001325.7 + 042509 HELMS56 Na16 00:13:26 + 04:25:09.00 C – 89 _._ 0 ± 6 _._ 0 98 _._ 0 ± 6 _._ 0 102 _._ 0 ± 7 _._ 0 Na16

S_144 HATLASJ002144.8 − 295217 HerBS156 Ba18 00:21:45 − 29:52:18.00 C – 103 _._ 7 ± 5 _._ 7 91 _._ 3 ± 6 _._ 1 85 _._ 4 ± 6 _._ 9 Ba18

S_145 HELMSJ002719.5 + 001204 HELMS34 Na16 00:27:20 + 00:12:04.00 C – 248 _._ 0 ± 6 _._ 0 206 _._ 0 ± 7 _._ 0 116 _._ 0 ± 8 _._ 0 Na16

S_146 HERMESJ002854 − 420457 HELAISS04 Ca14 00:28:54 − 42:04:57.00 C – 131 _._ 0 102 _._ 0 58 _._ 0 Ca14

S_147 HELMSJ003519.7 + 072806 HELMS57 Na16 00:35:20 + 07:28:06.00 C – 134 _._ 0 ± 7 _._ 0 135 _._ 0 ± 7 _._ 0 101 _._ 0 ± 8 _._ 0 Na16

S_148 HATLASJ003728.7 − 284124 HerBS174 Ba18 00:37:29 − 28:41:25.00 C – 95 _._ 6 ± 5 _._ 7 84 _._ 8 ± 5 _._ 9 83 _._ 2 ± 7 _._ 4 Ba18

S_149 HELMSJ004622.3 + 073509 HELMS46 Na16 00:46:22 + 07:35:09.00 C – 82 _._ 0 ± 9 _._ 0 113 _._ 0 ± 9 _._ 0 105 _._ 0 ± 10 _._ 0 Na16

S_150 HATLASJ005132.8 − 301848 HerBS45 Ba18 00:51:33 − 30:18:48.00 C – 164 _._ 6 ± 5 _._ 4 160 _._ 2 ± 5 _._ 8 113 _._ 0 ± 7 _._ 2 Ne17

S_151 HELMSJ005258.6 + 061319 HELMS10 Na16 00:52:59 + 06:13:19.00 C D 88 _._ 0 ± 6 _._ 0 129 _._ 0 ± 6 _._ 0 155 _._ 0 ± 7 _._ 0 Na16

S_152 HATLASJ005849.9 − 290122 HerBS181 Ba18 00:58:50 − 29:01:22.00 C – 92 _._ 5 ± 5 _._ 7 116 _._ 6 ± 6 _._ 0 82 _._ 6 ± 7 _._ 2 Ba18

S_153 HATLASJ011014.5 − 314813 HerBS160 Ba18 01:10:15 − 31:48:14.00 C Unc. 48 _._ 6 ± 5 _._ 6 84 _._ 2 ± 6 _._ 0 84 _._ 8 ± 7 _._ 1 Ba18

S_154 HATLASJ011730.3 − 320719 HerBS138 Ba18 01:17:30 − 32:07:19.00 C – 120 _._ 4 ± 5 _._ 8 111 _._ 2 ± 6 _._ 4 87 _._ 4 ± 7 _._ 8 Ba18

S_155 HATLASJ012209.4 − 273824 HerBS114 Ba18 01:22:09 − 27:38:24.00 C – 81 _._ 7 ± 5 _._ 9 93 _._ 8 ± 6 _._ 0 91 _._ 8 ± 7 _._ 7 Ba18

S_156 HATLASJ012335.1 − 314618 HerBS145 Ba18 01:23:35 − 31:46:19.00 C D 54 _._ 7 ± 6 _._ 0 67 _._ 4 ± 6 _._ 2 86 _._ 8 ± 7 _._ 7 Ba18

S_157 HERSJ013212.2 + 001754 HERS18 Na16 01:32:12 + 00:17:54.00 C – 176 _._ 0 ± 7 _._ 0 175 _._ 0 ± 6 _._ 0 104 _._ 0 ± 8 _._ 0 Na16

S_158 HATLASJ013239.9 − 330906 HerBS40 Ba18 01:32:40 − 33:09:07.00 C – 112 _._ 0 ± 5 _._ 5 148 _._ 8 ± 6 _._ 2 117 _._ 7 ± 7 _._ 0 Ne17

S_159 HERSJ014057.3 − 010547 HERS14 Na16 01:40:57 − 01:05:47.00 C – 136 _._ 0 ± 8 _._ 0 143 _._ 0 ± 8 _._ 0 112 _._ 0 ± 9 _._ 0 Na16

S_160 HATLASJ014520.0 − 313834 HerBS107 Ba18 01:45:20 − 31:38:35.00 C – 97 _._ 3 ± 6 _._ 1 99 _._ 1 ± 6 _._ 4 93 _._ 1 ± 7 _._ 8 Ba18

S_161 HERSJ020529.1 + 000501 HERS19 Na16 02:05:29 + 00:05:01.00 C – 89 _._ 0 ± 6 _._ 0 112 _._ 0 ± 6 _._ 0 102 _._ 0 ± 8 _._ 0 Na16

S_162 HERMESJ021632 − 053421 HXMM14 Ca14 02:16:32 − 05:34:21.00 C – 98 _._ 0 98 _._ 0 78 _._ 0 Ca14

S_163 HERMESJ021837 − 035315 HXMM13 Ca14 02:18:37 − 03:53:15.00 C – 55 _._ 0 88 _._ 0 94 _._ 0 Ca14

S_164 HERMESJ021943 − 052433 HXMM20 Ca14 02:19:43 − 05:24:33.00 C D 85 _._ 0 79 _._ 0 67 _._ 0 Ca14

S_165 HERMESJ022206 − 070727 HXMM23 Ca14 02:22:06 − 07:07:27.00 C D 137 _._ 0 108 _._ 0 57 _._ 0 Ca14

S_166 HERMESJ022213 − 070222 HXMM28 Ca14 02:22:13 − 07:02:22.00 C – 27 _._ 0 47 _._ 0 87 _._ 0 Ca14

S_167 HERMESJ022251 − 032414 HXMM22 Ca14 02:22:51 − 03:24:14.00 C D 101 _._ 0 ± 6 _._ 0 85 _._ 0 ± 6 _._ 0 61 _._ 0 ± 6 _._ 0 Bu15

S_168 HERMESJ022515 − 024707 HXMM19 Ca14 02:25:15 − 02:47:07.00 C – 43 _._ 0 67 _._ 0 70 _._ 0 Ca14

S_169 HERMESJ022518 − 044610 HXMM27 Ca14 02:25:17 − 04:46:10.00 C – 0 _._ 0 48 _._ 0 43 _._ 0 Ca14

S_170 HERMESJ023006 − 034153 HXMM12 Ca14 02:30:06 − 03:41:53.00 C Unc. 98 _._ 0 ± 7 _._ 0 106 _._ 0 ± 8 _._ 0 82 _._ 0 ± 7 _._ 0 Bu15

S_171 HERMESJ032434 − 292646 HECDFS08 Ca14 03:24:34 − 29:26:46.00 C – 104 _._ 0 67 _._ 0 54 _._ 0 Ca14

S_172 HERMESJ032443 − 282134 HECDFS03 Ca14 03:24:43 − 28:21:34.00 C – 83 _._ 0 118 _._ 0 113 _._ 0 Ca14

S_173 HERMESJ032713 − 285106 HECDFS09 Ca14 03:27:13 − 28:51:06.00 C – 77 _._ 0 66 _._ 0 51 _._ 0 Ca14

S_174 HERMESJ033118 − 272015 HECDFS11 Ca14 03:31:18 − 27:20:15.00 C – 45 _._ 0 52 _._ 0 42 _._ 0 Ca14

S_175 HERMESJ043341 − 540338 HADFS04 Ca14 04:33:41 − 54:03:38.00 C Unc. 74 _._ 0 ± 6 _._ 0 93 _._ 0 ± 6 _._ 0 84 _._ 0 ± 6 _._ 0 Bu15

S_176 HERMESJ043830 − 541832 HADFS02 Ca14 04:38:30 − 54:18:32.00 C D 19 _._ 0 ± 6 _._ 0 39 _._ 0 ± 5 _._ 0 52 _._ 0 ± 6 _._ 0 Bu15

S_177 HERMESJ044947 − 525427 HADFS09 Ca14 04:49:47 − 52:54:27.00 C D 98 _._ 0 ± 6 _._ 0 102 _._ 0 ± 6 _._ 0 72 _._ 0 ± 6 _._ 0 Bu15

S_178 HATLASJ083153 + 014014 – – 08:31:53 + 01:40:14.43 C D 69 _._ 8 ± 7 _._ 3 93 _._ 0 ± 8 _._ 1 82 _._ 0 ± 8 _._ 6 Va16

S_179 HATLASJ083546 + 002804 – – 08:35:46 + 00:28:03.75 C – 86 _._ 6 ± 6 _._ 6 94 _._ 5 ± 7 _._ 5 79 _._ 5 ± 8 _._ 0 Va16

S_180 HATLASJ083817 − 004134 HerBS108 Ba18 08:38:17 − 00:41:34.00 C – 84 _._ 5 ± 7 _._ 4 106 _._ 1 ± 8 _._ 2 93 _._ 0 ± 8 _._ 8 Ba18

S_181 HATLASJ083859.3 + 021325 HerBS169 Ba18 08:38:59 + 02:13:25.87 C – 95 _._ 2 ± 7 _._ 5 105 _._ 2 ± 8 _._ 2 84 _._ 0 ± 8 _._ 7 Ba18

S_182 HATLASJ083945 + 021023 HerBS171 Ba18 08:39:45 + 02:10:22.83 C – 71 _._ 3 ± 7 _._ 3 97 _._ 4 ± 8 _._ 1 83 _._ 4 ± 8 _._ 6 Ba18

S_183 HATLASJ084259.9 + 024959 HerBS188 Ba18 08:43:00 + 02:49:59.02 C – 84 _._ 2 ± 7 _._ 4 101 _._ 5 ± 8 _._ 1 81 _._ 8 ± 8 _._ 6 Ba18

S_184 HATLASJ085033 + 012914 – – 08:50:33 + 01:29:14.10 C – 182 _._ 5 ± 6 _._ 9 131 _._ 6 ± 7 _._ 7 74 _._ 7 ± 8 _._ 0 Ma18

S_185 HATLASJ085126 + 014638 – – 08:51:26 + 01:46:38.37 C – 66 _._ 4 ± 7 _._ 4 92 _._ 3 ± 8 _._ 1 79 _._ 1 ± 8 _._ 5 Va16

S_186 HATLASJ085309 − 005727 HerBS136 Ba18 08:53:09 − 00:57:27.00 C – 68 _._ 3 ± 7 _._ 5 97 _._ 5 ± 8 _._ 2 87 _._ 7 ± 8 _._ 6 Ne17

S_187 HATLASJ090953 − 010811 SDP.60 09:09:53 − 01:08:11.00 C – 152 _._ 1 ± 7 _._ 2 109 _._ 3 ± 8 _._ 1 83 _._ 5 ± 8 _._ 4 Va16

S_188 HATLASJ091454 − 010357 HerBS142 Ba18 09:14:54 − 01:03:57.00 C D 69 _._ 0 ± 7 _._ 3 72 _._ 2 ± 8 _._ 1 87 _._ 2 ± 8 _._ 5 Ba18

S_189 HATLASJ091809 + 001927 HerBS99 Ba18 09:18:09 + 00:19:27.27 C – 93 _._ 2 ± 7 _._ 4 116 _._ 6 ± 8 _._ 2 94 _._ 3 ± 8 _._ 7 Ba18

S_190 HATLASJ091857 − 000047 – – 09:18:57 − 00:00:47.00 C – 171 _._ 6 ± 6 _._ 4 145 _._ 7 ± 7 _._ 4 85 _._ 1 ± 7 _._ 7 Va16

S_191 HATLASJ091949 − 005037 – – 09:19:49 − 00:50:37.00 C – 150 _._ 7 ± 7 _._ 5 141 _._ 4 ± 8 _._ 4 90 _._ 4 ± 8 _._ 7 Va16

S_192 HATLASJ092141 + 005356 – – 09:21:41 + 00:53:55.58 C – 71 _._ 2 ± 7 _._ 3 85 _._ 4 ± 8 _._ 2 79 _._ 6 ± 8 _._ 8 Va16

S_193 HERMESJ100057 + 022014 HCOSMOS02 Ca14 10:00:57 + 02:20:13.70 C D 70 _._ 0 ± 6 _._ 0 85 _._ 0 ± 6 _._ 0 71 _._ 0 ± 6 _._ 0 Bu15

COSBO3


MNRAS **000**, 1–57 (2022)

_Characterisation of HST confirmed lenses_ 53


**Table B1** – _continued_


No. IAU Name Alt. Name Ref. RA Dec Vis. Class. Multiw. Class. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)


S_194 HERMESJ103958 + 563120 HLock17 Wa13 10:39:58 + 56:31:19.92 C – 62 _._ 0 82 _._ 0 67 _._ 0 Ca14

S_195 HERMESJ104051 + 560654 HLock02 Wa13 10:40:51 + 56:06:54.14 C – 53 _._ 0 115 _._ 0 140 _._ 0 Ca14

LSW102

S_196 HERMESJ104140 + 570859 HLock11 Wa13 10:41:40 + 57:08:59.42 C – 97 _._ 0 112 _._ 0 80 _._ 0 Ca14

S_197 HERMESJ105712 + 565458 HLock03 Wa13 10:57:12 + 56:54:58.25 C – 114 _._ 0 ± 7 _._ 0 147 _._ 0 ± 10 _._ 0 114 _._ 0 ± 8 _._ 0 Ca14

S_198 HATLASJ113243 − 005109 HerBS71 Ba18 11:32:43 − 00:51:09.00 C – 68 _._ 0 ± 7 _._ 0 106 _._ 0 ± 8 _._ 0 100 _._ 0 ± 9 _._ 0 Ma19

S_199 HATLASJ113834 − 014657 HerBS119 Ba18 11:38:34 − 01:46:57.00 C – 68 _._ 5 ± 7 _._ 2 85 _._ 6 ± 8 _._ 1 91 _._ 2 ± 8 _._ 6 Ba18

S_200 HATLASJ114753 − 005832 HerBS85 Ba18 11:47:53 − 00:58:32.00 C – 92 _._ 1 ± 6 _._ 6 104 _._ 2 ± 7 _._ 4 96 _._ 0 ± 7 _._ 7 Ba18

S_201 HATLASJ115521 − 021332 HERBS179 11:55:21 − 02:13:32.00 C D 67 _._ 3 ± 7 _._ 2 84 _._ 9 ± 8 _._ 1 75 _._ 7 ± 8 _._ 9 Va16

S_202 HATLASJ115820 − 013754 HerBS66 Ba18 11:58:20 − 01:37:54.00 C – 120 _._ 0 ± 7 _._ 0 124 _._ 0 ± 8 _._ 0 101 _._ 0 ± 8 _._ 0 Ma19

S_203 HATLASJ120600.7 + 003459 HerBS74 Ba18 12:06:01 + 00:34:59.51 C – 88 _._ 7 ± 7 _._ 4 104 _._ 1 ± 8 _._ 1 98 _._ 8 ± 8 _._ 7 Ba18

S_204 HATLASJ120709.2 − 014702 HerBS51 Ba18 12:07:09 − 01:47:03.00 C – 143 _._ 2 ± 7 _._ 4 149 _._ 2 ± 8 _._ 1 110 _._ 3 ± 8 _._ 7 Ne17

S_205 HATLASJ121348.0 + 010812 HerBS116 Ba18 12:13:48 + 01:08:12.59 C – 65 _._ 1 ± 7 _._ 4 96 _._ 6 ± 8 _._ 2 93 _._ 6 ± 8 _._ 5 Ba18

S_206 HATLASJ121416.3 − 013704 HerBS164 Ba18 12:14:16 − 01:37:04.00 C – 88 _._ 0 ± 6 _._ 4 99 _._ 3 ± 7 _._ 4 84 _._ 3 ± 7 _._ 7 Ba18

S_207 HATLASJ121812.8 + 011841 HerBS83 Ba18 12:18:13 + 01:18:41.67 C D 49 _._ 5 ± 7 _._ 2 79 _._ 7 ± 8 _._ 1 94 _._ 1 ± 8 _._ 8 Ba18

S_208 HATLASJ122034.2 − 003805 HerBS197 Ba18 12:20:34 − 00:38:06.00 C – 81 _._ 9 ± 7 _._ 5 93 _._ 8 ± 8 _._ 2 84 _._ 8 ± 8 _._ 7 Ba18

S_209 HATLASJ122117.0 − 014924 – – 12:21:17 − 01:49:24.00 C – 146 _._ 6 ± 7 _._ 4 128 _._ 9 ± 8 _._ 2 87 _._ 2 ± 8 _._ 3 Va16

S_210 HATLASJ122158.5 + 003326 HerBS124 Ba18 12:21:59 + 00:33:26.15 C – 135 _._ 7 ± 7 _._ 3 116 _._ 1 ± 8 _._ 2 89 _._ 8 ± 8 _._ 6 Ba18

S_211 HATLASJ122407.4 − 003247 HerBS161 Ba18 12:24:07 − 00:32:47.00 C D 56 _._ 5 ± 7 _._ 3 75 _._ 7 ± 8 _._ 1 82 _._ 4 ± 8 _._ 8 Ba18

S_212 HATLASJ122459.1 − 005647 HerBS150 Ba18 12:24:59 − 00:56:47.00 C D 53 _._ 6 ± 7 _._ 2 81 _._ 3 ± 8 _._ 3 92 _._ 0 ± 8 _._ 9 Ba18

S_213 HATLASJ125105 + 261653 NGP.2070 12:51:05 + 26:16:52.62 C – 116 _._ 5 ± 5 _._ 5 125 _._ 3 ± 6 _._ 5 81 _._ 3 ± 7 _._ 7 Va16

S_214 HATLASJ125653 + 275903 HerBS31 Ba18 12:56:53 + 27:59:02.98 C – 133 _._ 9 ± 7 _._ 5 164 _._ 1 ± 8 _._ 2 131 _._ 8 ± 8 _._ 9 Ne17

S_215 HATLASJ125810 + 263710 – – 12:58:10 + 26:37:09.99 C – 131 _._ 6 ± 7 _._ 3 122 _._ 9 ± 8 _._ 3 78 _._ 8 ± 8 _._ 5 Ma18

S_216 HATLASJ130601 + 231322 – – 13:06:01 + 23:13:21.65 C – 86 _._ 0 ± 7 _._ 3 88 _._ 0 ± 8 _._ 2 76 _._ 5 ± 8 _._ 6 Va16

S_217 HATLASJ131001 + 264759 – – 13:10:01 + 26:47:59.05 C – 142 _._ 1 ± 7 _._ 3 124 _._ 1 ± 8 _._ 2 81 _._ 2 ± 8 _._ 9 Va16

S_218 HATLASJ131020 + 253731 – – 13:10:20 + 25:37:31.47 C – 186 _._ 4 ± 7 _._ 3 158 _._ 7 ± 8 _._ 1 93 _._ 7 ± 8 _._ 5 Va16

S_219 HATLASJ131609 + 254931 – – 13:16:09 + 25:49:31.15 C – 121 _._ 4 ± 7 _._ 3 108 _._ 2 ± 8 _._ 1 76 _._ 8 ± 8 _._ 7 Va16

S_220 HATLASJ131642 + 251158 – – 13:16:42 + 25:11:58.38 C – 62 _._ 7 ± 6 _._ 9 71 _._ 5 ± 7 _._ 7 63 _._ 9 ± 8 _._ 1 Ma18

S_221 HATLASJ131805 + 325018 HerBS173 Ba18 13:18:05 + 32:50:18.05 C – 73 _._ 3 ± 5 _._ 6 92 _._ 7 ± 6 _._ 0 83 _._ 3 ± 7 _._ 2 Ba18

S_222 HATLASJ132128 + 282023 HerBS127 Ba18 13:21:28 + 28:20:22.74 C – 110 _._ 0 ± 5 _._ 5 122 _._ 7 ± 6 _._ 1 89 _._ 5 ± 6 _._ 9 Ba18

S_223 HATLASJ132227 + 300723 – – 13:22:27 + 30:07:22.54 C – 48 _._ 0 ± 7 _._ 3 78 _._ 6 ± 8 _._ 2 25 _._ 0 ± 8 _._ 8 Va16

S_224 HATLASJ132302 + 341650 HerBS30 Ba18 13:23:02 + 34:16:49.66 C – 124 _._ 2 ± 7 _._ 3 144 _._ 6 ± 8 _._ 2 137 _._ 0 ± 8 _._ 7 Ne17

S_225 HATLASJ132419 + 320754 HerBS43 Ba18 13:24:19 + 32:07:54.43 C – 84 _._ 5 ± 6 _._ 8 116 _._ 0 ± 7 _._ 6 115 _._ 4 ± 8 _._ 0 Ne17

S_226 HATLASJ132909 + 300958 HerBS204 Ba18 13:29:09 + 30:09:58.23 C – 57 _._ 9 ± 5 _._ 5 95 _._ 3 ± 6 _._ 1 80 _._ 1 ± 7 _._ 1 Ba18

S_227 HATLASJ133255 + 265529 – – 13:32:55 + 26:55:29.23 C – 192 _._ 5 ± 7 _._ 4 167 _._ 4 ± 8 _._ 1 116 _._ 6 ± 8 _._ 6 Ne17

S_228 HATLASJ133256 + 342210 HerBS44 Ba18 13:32:56 + 34:22:09.50 C – 164 _._ 3 ± 7 _._ 5 186 _._ 8 ± 8 _._ 1 114 _._ 9 ± 8 _._ 7 Ne17

NA.v1.267

S_229 HATLASJ133440 + 353140 HerBS134 Ba18 13:34:40 + 35:31:40.17 C – 69 _._ 9 ± 5 _._ 9 97 _._ 3 ± 6 _._ 2 87 _._ 9 ± 7 _._ 3 Ba18

S_230 HATLASJ133534 + 341837 HerBS76 Ba18 13:35:34 + 34:18:36.97 C – 108 _._ 5 ± 5 _._ 9 124 _._ 3 ± 6 _._ 0 98 _._ 5 ± 7 _._ 0 Ba18

S_231 HATLASJ133623 + 343806 – – 13:36:23 + 34:38:05.88 C – 78 _._ 8 ± 7 _._ 4 83 _._ 2 ± 8 _._ 3 79 _._ 1 ± 8 _._ 6 Ma18

S_232 HATLASJ133715 + 352058 – – 13:37:15 + 35:20:58.04 C – 69 _._ 9 ± 7 _._ 5 88 _._ 1 ± 8 _._ 3 69 _._ 4 ± 8 _._ 8 Ma18

S_233 HATLASJ133905 + 340820 – – 13:39:05 + 34:08:20.20 C – 59 _._ 3 ± 7 _._ 3 82 _._ 7 ± 8 _._ 2 70 _._ 1 ± 8 _._ 7 Va16

S_234 HATLASJ134124 + 354007 – – 13:41:24 + 35:40:06.58 C – 62 _._ 9 ± 7 _._ 3 79 _._ 9 ± 8 _._ 2 82 _._ 2 ± 8 _._ 5 Va16

S_235 HATLASJ134139 + 322837 – – 13:41:39 + 32:28:37.34 C – 39 _._ 8 ± 7 _._ 4 42 _._ 7 ± 8 _._ 1 80 _._ 1 ± 8 _._ 8 Va16

S_236 HATLASJ134403 + 242627 HerBS196 Ba18 13:44:03 + 24:26:26.95 C – 86 _._ 9 ± 5 _._ 7 92 _._ 3 ± 6 _._ 3 81 _._ 0 ± 7 _._ 1 Ba18

S_237 HATLASJ134442 + 240346 HerBS133 Ba18 13:44:42 + 24:03:46.12 C – 85 _._ 4 ± 5 _._ 5 98 _._ 5 ± 6 _._ 1 88 _._ 1 ± 7 _._ 3 Ba18

S_238 HATLASJ134654 + 295659 – – 13:46:54 + 29:56:59.06 C – 85 _._ 0 ± 7 _._ 6 82 _._ 0 ± 8 _._ 3 77 _._ 8 ± 8 _._ 6 Va16

S_239 HATLASJ140422 − 001218 HerBS206 Ba18 14:04:22 − 00:12:18.00 C – 79 _._ 3 ± 7 _._ 4 102 _._ 6 ± 8 _._ 4 80 _._ 2 ± 8 _._ 8 Ba18

S_240 HATLASJ141118 − 010655 HerBS201 Ba18 14:11:18 − 01:06:55.00 C D 52 _._ 2 ± 7 _._ 2 78 _._ 6 ± 8 _._ 2 80 _._ 5 ± 8 _._ 7 Ba18

S_241 HATLASJ141810.0 − 003747 HerBS143 Ba18 14:18:10 − 00:37:47.00 C – 77 _._ 7 ± 6 _._ 5 97 _._ 3 ± 7 _._ 4 87 _._ 1 ± 7 _._ 9 Ba18

S_242 HATLASJ141955.5 − 003449 – – 14:19:56 − 00:34:49.00 C – 76 _._ 4 ± 7 _._ 5 94 _._ 9 ± 8 _._ 0 80 _._ 2 ± 8 _._ 9 Va16

S_243 HERMESJ142549 + 345024 – – 14:25:49 + 34:50:23.57 C – 48 _._ 0 ± 7 _._ 4 64 _._ 4 ± 8 _._ 3 52 _._ 9 ± 9 _._ 0 Ma18

S_244 HERMESJ142558 + 332549 HBootes09 14:25:58 + 33:25:48.68 C – 69 _._ 0 81 _._ 0 60 _._ 0 Ca14

S_245 HATLASJ142707 + 002258 HerBS130 Ba18 14:27:07 + 00:22:57.60 C – 119 _._ 4 ± 7 _._ 3 118 _._ 7 ± 8 _._ 1 88 _._ 8 ± 8 _._ 6 Ba18

S_246 HATLASJ143403.5 + 000234 HerBS147 Ba18 14:34:04 + 00:02:34.34 C – 103 _._ 3 ± 7 _._ 4 103 _._ 3 ± 8 _._ 1 86 _._ 6 ± 8 _._ 5 Ba18

S_247 HERMESJ143544 + 344743 HBootes12 14:35:44 + 34:47:43.37 C – 11 _._ 0 52 _._ 0 21 _._ 0 Ca14

S_248 HERMESJ144030 + 333843 HBootes07 14:40:30 + 33:38:42.68 C – 86 _._ 0 88 _._ 0 72 _._ 0 Ca14

S_249 HATLASJ144556.1 − 004853 G15v2.481 14:45:56 − 00:48:53.00 C Unc. 126 _._ 7 ± 7 _._ 3 132 _._ 6 ± 8 _._ 4 111 _._ 8 ± 8 _._ 7 Ne17

HerBS46 Ba18

S_250 HATLASJ144608.6 + 021927 HerBS38 Ba18 14:46:09 + 02:19:27.01 C – 73 _._ 4 ± 7 _._ 1 111 _._ 7 ± 8 _._ 1 122 _._ 1 ± 8 _._ 7 Ne17

S_251 HATLASJ145135.2 − 011418 HerBS126 Ba18 14:51:35 − 01:14:18.00 C – 81 _._ 9 ± 7 _._ 2 95 _._ 9 ± 8 _._ 2 89 _._ 8 ± 8 _._ 8 Ba18

S_252 HATLASJ145337.2 + 000407 HerBS137 Ba18 14:53:37 + 00:04:07.94 C – 86 _._ 0 ± 7 _._ 2 103 _._ 6 ± 8 _._ 0 87 _._ 7 ± 8 _._ 6 Ba18

S_253 HATLASJ145754 + 000017 HerBS195 Ba18 14:57:54 + 00:00:17.07 C – 70 _._ 3 ± 7 _._ 3 92 _._ 7 ± 8 _._ 1 81 _._ 0 ± 8 _._ 8 Ba18

S_254 HERMESJ161332 + 544358 HELAISN01 16:13:32 + 54:43:57.76 C – 123 _._ 0 129 _._ 0 88 _._ 0 Ca14

S_255 HERMESJ170508 + 594056 HFLS07 Ca14 17:05:08 + 59:40:56.32 C – 115 _._ 0 92 _._ 0 69 _._ 0 Ca14

S_256 HERMESJ170608 + 590921 HFLS03 Ca14 17:06:08 + 59:09:21.28 C – 98 _._ 0 105 _._ 0 81 _._ 0 Ca14

S_257 HERMESJ170818 + 582845 HFLS05 Ca14 17:08:18 + 58:28:45.41 C – 40 _._ 0 75 _._ 0 74 _._ 0 Ca14

S_258 HERMESJ172222 + 582611 HFLS10 Ca14 17:22:22 + 58:26:10.82 C – 52 _._ 0 50 _._ 0 32 _._ 0 Ca14

S_259 HERMESJ172612 + 583742 HFLS01 Ca14 17:26:12 + 58:37:42.24 C – 107 _._ 0 123 _._ 0 98 _._ 0 Ca14

S_260 HATLASJ222629.4 − 321111 HerBS144 Ba18 22:26:29 − 32:11:12.00 C – 98 _._ 9 ± 8 _._ 4 116 _._ 5 ± 8 _._ 2 87 _._ 0 ± 11 _._ 5 Ba18

S_261 HATLASJ224027.7 − 343134 HerBS97 Ba18 22:40:28 − 34:31:35.00 C – 96 _._ 1 ± 6 _._ 0 98 _._ 5 ± 6 _._ 3 94 _._ 4 ± 7 _._ 7 Ba18

S_262 HATLASJ224207.2 − 324159 HerBS67 Ba18 22:42:07 − 32:41:59.00 C Unc. 73 _._ 0 ± 5 _._ 5 88 _._ 1 ± 6 _._ 2 100 _._ 8 ± 7 _._ 7 Ne17

S_263 HATLASJ224400.8 − 340030 HerBS84 Ba18 22:44:01 − 34:00:31.00 C – 105 _._ 1 ± 5 _._ 9 123 _._ 0 ± 6 _._ 4 97 _._ 0 ± 7 _._ 6 Ba18

S_264 HATLASJ225324.2 − 323504 HerBS103 Ba18 22:53:24 − 32:35:04.00 C – 126 _._ 1 ± 5 _._ 3 131 _._ 2 ± 5 _._ 7 93 _._ 5 ± 7 _._ 0 Ba18


MNRAS **000**, 1–57 (2022)

54 _E. Borsato et al._


**Table B1** – _continued_


No. IAU Name Alt. Name Ref. RA Dec Vis. Class. Multiw. Class. _𝑆_ 250 _𝑆_ 350 _𝑆_ 500 Ref.

[h m s] [d m s] [mJy] [mJy] [mJy]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)


S_265 HATLASJ225339.1 − 325549 HerBS131 Ba18 22:53:39 − 32:55:50.00 C – 85 _._ 5 ± 5 _._ 2 99 _._ 7 ± 5 _._ 5 88 _._ 0 ± 6 _._ 9 Ba18

S_266 HATLASJ225611.6 − 325652 HerBS135 Ba18 22:56:12 − 32:56:53.00 C – 85 _._ 4 ± 5 _._ 5 96 _._ 7 ± 6 _._ 2 87 _._ 8 ± 7 _._ 5 Ba18

S_267 HATLASJ230002.6 − 315005 HerBS80 Ba18 23:00:03 − 31:50:05.00 C – 122 _._ 7 ± 5 _._ 7 122 _._ 1 ± 6 _._ 3 97 _._ 7 ± 7 _._ 6 Ba18

S_268 HATLASJ230538.5 − 312204 HerBS182 Ba18 23:05:39 − 31:22:04.00 C – 89 _._ 0 ± 5 _._ 7 109 _._ 1 ± 6 _._ 2 82 _._ 3 ± 7 _._ 9 Ba18

S_269 HATLASJ231205.1 − 295026 HerBS132 Ba18 23:12:05 − 29:50:27.00 C – 86 _._ 7 ± 5 _._ 8 102 _._ 6 ± 6 _._ 0 90 _._ 6 ± 7 _._ 8 Ba18

S_270 HELMSJ231857.2 − 053035 HELMS16 Na16 23:18:57 − 05:30:35.00 C – 143 _._ 0 ± 7 _._ 0 183 _._ 0 ± 7 _._ 0 146 _._ 0 ± 8 _._ 0 Na16

S_271 HATLASJ232200.0 − 355622 HerBS118 Ba18 23:22:00 − 35:56:22.00 C D 60 _._ 0 ± 6 _._ 3 84 _._ 3 ± 6 _._ 6 90 _._ 9 ± 7 _._ 7 Ba18

S_272 HATLASJ232419.8 − 323926 HerBS18 Ba18 23:24:20 − 32:39:27.00 C – 213 _._ 0 ± 4 _._ 4 244 _._ 2 ± 4 _._ 8 169 _._ 4 ± 5 _._ 8 Ne17

SC.v1.128

S_273 HELMSJ232558.3 − 044525 HELMS17 Na16 23:25:58 − 04:45:25.00 C – 190 _._ 0 ± 6 _._ 0 189 _._ 0 ± 6 _._ 0 142 _._ 0 ± 8 _._ 0 Na16

S_274 HATLASJ232623.0 − 342642 HerBS37 Ba18 23:26:23 − 34:26:42.00 C – 153 _._ 7 ± 4 _._ 4 178 _._ 3 ± 5 _._ 0 123 _._ 5 ± 6 _._ 2 Ne17

SB.v1.202

S_275 HELMSJ234014.6 − 070738 HELMS42 Na16 23:40:15 − 07:07:38.00 C – 158 _._ 0 ± 6 _._ 0 154 _._ 0 ± 6 _._ 0 110 _._ 0 ± 8 _._ 0 Na16

S_276 HELMSJ234951.6 − 030019 HELMS47 Na16 23:49:52 − 03:00:19.00 C – 186 _._ 0 ± 7 _._ 0 167 _._ 0 ± 6 _._ 0 105 _._ 0 ± 8 _._ 0 Na16

S_277 HERSJ010911.7 − 011733 HERS9 Na16 01:09:12 − 01:17:33.00 D – 393 _._ 0 ± 8 _._ 0 220 _._ 0 ± 8 _._ 0 118 _._ 0 ± 9 _._ 0 Na16

S_278 HATLASJ083345 + 000109 HerBS88 Ba18 08:33:45 + 00:01:09.41 D D 71 _._ 0 ± 7 _._ 6 96 _._ 0 ± 8 _._ 1 95 _._ 9 ± 8 _._ 8 Ba18

S_279 HATLASJ090613.8 − 010042 HerBS165 Ba18 09:06:14 − 01:00:43.00 D D 73 _._ 4 ± 7 _._ 4 80 _._ 2 ± 8 _._ 0 84 _._ 3 ± 8 _._ 7 Ba18

S_280 HATLASJ091238 + 020050 – – 09:12:38 + 02:00:49.71 D – 173 _._ 2 ± 7 _._ 7 140 _._ 2 ± 8 _._ 2 97 _._ 6 ± 9 _._ 1 Ma18

S_281 HATLASJ142004 + 014045 – – 14:20:04 + 01:40:44.73 D – 191 _._ 7 ± 7 _._ 5 150 _._ 1 ± 8 _._ 3 65 _._ 2 ± 8 _._ 7 Ma18


MNRAS **000**, 1–57 (2022)

6


4


2


0


6


4


2


0


3


2


1


0


1

12


10


8


6


4


2


0


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




HERSJ020941.2+001558/HerS1/No. S_8


1 arcsec 1 arcsec



6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0


6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0


3



1 arcsec 1 arcsec


1 arcsec 1 arcsec



1 arcsec 1 arcsec


6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0


3


2


1


0.1 arcsec 0


1 arcsec 1 arcsec


6


4


2


0.1 arcsec 0

1 arcsec 1 arcsec


6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0




HATLASJ125126+254928/HerBS52/No. S_16


1 arcsec 1 arcsec


HATLASJ125760+224558/-/No. S_17


HATLASJ133008+245860/HerBS12/No. S_18



6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0


3



0.1 arcsec



2


1


0



1


1



1 arcsec 1 arcsec 0.1 arcsec



2


1


0


1

12


10


8


6


4


2



1 arcsec 1 arcsec 0.1 arcsec 0


6


4


2


0.1 arcsec 0



6


4


2


0


3


2


1


0


1


6


4


2


0


3


2


1


0


1


6


4


2


0


6


4


2


0



0.1 arcsec



2.0


1.5


1.0


0.5


0.0


0.5



**Figure C1.** _From left to right panels:_ Lens subtracted image, best-fitting model of the lensed source, SNR _>_ 3 regions of the reconstructed source plane lensed back to the image plane, SNR map of the residuals
obtained after subtracting the model of the lensed source from the input lens-subtracted image, and the reconstructed background source with caustic curves (green line). Each of the first three panels shows the pixel
mask (black-shaded region) adopted for the lens modelling. The second panel from the left also shows the critical curves (black curve). In the source plane image, we highlighted with black contours the _SNR_ _>_ 3
region adopted for computing the magnification and source size.

1 arcsec 1 arcsec


HATLASJ225250.7 313657/HerBS47/No. S_40


HELMSJ233633.5 032119/HeLMS41/No. S_42


1 arcsec 1 arcsec



6


4


2


0


3


2


1


0


1


3


2


1


0


1


6


4


2


0


6


4


2


0



HATLASJ133846+255057/HerBS29/No. S_19


HERMESJ104549+574512/HLock06/No. S_32


1 arcsec 1 arcsec



6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0


3


2


1


0


1 arcsec 1 arcsec 0.1 arcsec 1


3



0.1 arcsec


1 arcsec 1 arcsec 0.1 arcsec


0.1 arcsec



3


2


1


0


1 arcsec 1 arcsec 0.1 arcsec 1


6


4


2


0
1 arcsec 1 arcsec 0.1 arcsec


6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0



6


4


2


1 arcsec 1 arcsec 0.1 arcsec 0



2


1


0


6


4


2


0


6


4


2


0



1



3


2


1


0


1


6


4


2


0


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


0.5


6


4


2


0



0.1 arcsec



2.5


2.0


1.5


1.0


0.5


0.0


0.5



1 arcsec 1 arcsec



**Figure C1** – _continued_

**AFFILIATIONS**


1
_Dipartimento_ _di_ _Fisica_ _e_ _Astronomia_ _"G._ _Galilei",_ _Università_ _di_
_Padova, vicolo dell’Osservatorio 3, I-35122 Padova, Italy._
2 _Department of Astronomy, University of Cape Town, 7701 Ronde-_
_bosch, Cape Town, South Africa._
3 _INAF - Istituto di Radioastronomia, Via Piero Gobetti 101, 40129,_
_Bologna, Italy._
4 _School of Physics and Astronomy, Cardiff University, The Parade,_
_Cardiff, CF24 3AA, UK._
5 _INAF_ _-_ _Osservatorio_ _Astronomico_ _di_ _Padova,_ _vicolo_
_dell’Osservatorio 2, I-35122 Padova, Italy._
6 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _North_
_Carolina_ _Asheville,_ _1_ _University_ _Heights,_ _Asheville,_ _NC_ _28804,_

_USA._
7 _Department_ _of_ _Physics,_ _Institute_ _for_ _Computational_ _Cosmology,_
_Durham University, South Road, Durham DH1 3LE, UK._
8 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _Rutgers,_ _the_ _State_ _Uni-_
_versity_ _of_ _New_ _Jersey,_ _136_ _Frelinghuysen_ _Road,_ _Piscataway,_ _NJ_
_08854-8019, United States._
9 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _the_ _Western_
_Cape, Robert Sobukwe Road, Bellville 7535, South Africa._
10 _Division_ _of_ _Particle_ _and_ _Astrophysical_ _Science,_ _Graduate_ _School_
_of Science, Nagoya University, Aichi 464-8602, Japan._
11 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1,_ _Osawa,_
_Mitaka, Tokyo 181-8588, Japan._
12 _Institut d’Astrophysique Spatiale,_ _B_ ˆ _𝑎t._ _121, Université_ _Paris-Sud,_
_91405 Orsay Cedex, France._
13 _Institut de Radioastronomie Millimétrique, 300 rue de la piscine,_
_F-38406 Saint-Martin-d’Hères, France._
14 _Blackett_ _Lab,_ _Imperial_ _College,_ _Prince_ _Consort_ _Road,_ _London_
_SW7 2AZ, UK._
15 _Department_ _of_ _Physics_ _&_ _Astronomy,_ _University_ _of_ _California,_
_Irvine, CA 92697, USA._
16 _Sorbonne Université, UPMC Université Paris 6 and CNRS, UMR_
_7095,_ _Institut_ _d’Astrophysique_ _de_ _Paris,_ _98bis_ _boulevard_ _Arago,_
_75014 Paris, France._
17 _Instituto_ _de_ _Astrofísica_ _de_ _Canarias,_ _C/Vía_ _Láctea,_ _s/n,_ _E-38205_
_San Cristóbal de La Laguna, Tenerife, Spain._
18 _Universidad_ _de_ _La_ _Laguna,_ _Dpto._ _Astrofísica,_ _E-38206_ _San_
_Cristóbal de La Laguna, Tenerife, Spain._
19 _School_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Nottingham,_
_University Park, Nottingham, NG7 2RD, UK._
20 _University_ _of_ _Bologna_ _–_ _Department_ _of_ _Physics_ _and_ _Astronomy_
_“Augusto Righi” (DIFA), Via Gobetti 93/2, I-40129 Bologna, Italy._
21
_INAF-_ _Osservatorio_ _di_ _Astrofisica_ _e_ _Scienza_ _dello_ _Spazio,_ _Via_
_Gobetti 93/3, I-40129, Bologna, Italy._
22 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Hawai’i,_
_2505 Correa Road, Honolulu, HI 96822, USA._
23 _Institute_ _for_ _Astronomy,_ _2680_ _Woodlawn_ _Drive,_ _University_ _of_
_Hawai’i, Honolulu, HI 96822, USA._
24 _Departamento_ _de_ _Física,_ _Universidad_ _de_ _Oviedo,_ _C._ _Federico_
_García Lorca 18, 33007 Oviedo, Spain._
25 _Instituto_ _Universitario_ _de_ _Ciencias_ _y_ _Tecnologías_ _Espaciales_ _de_
_Asturias (ICTEA), C. Independencia 13, 33004 Oviedo, Spain._
26 _Instituto_ _Nacional_ _de_ _Astrofísica,_ _Óptica_ _y_ _Electrónica,_ _Luis_
_Enrique Erro 1, Tonantzintla, Puebla, C.P. 72840, Mexico._
27 _Aix-Marseille_ _Universit‘e,_ _CNRS_ _and_ _CNES,_ _Laboratoire_
_d’Astrophysique_ _de_ _Marseille,_ _38,_ _rue_ _Fr‘ed‘eric_ _Joliot-Curie,_
_13388 Marseille, France._
28 _Cosmic Dawn Center (DAWN)._
29 _DTU_ _Space,_ _Technical_ _University_ _of_ _Denmark,_ _Elektrovej_ _327,_



_Characterisation of HST confirmed lenses_ 57


_2800 Kgs. Lyngby, Denmark._
30 _SISSA, Via Bonomea 265, 34136 Trieste, Italy._
31 _Université_ _Lyon_ _1,_ _ENS_ _de_ _Lyon,_ _CNRS_ _UMR5574,_ _Centre_ _de_
_Recherche_ _Astrophysique_ _de_ _Lyon,_ _F-69230_ _Saint-Genis-Laval,_

_France._
32 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _British_
_Columbia, Canada._
33 _School_ _of_ _Physical_ _Sciences,_ _The_ _Open_ _University,_ _Walton_ _Hall,_
_Milton Keynes, MK7 6AA, UK._
34 _Department of Earth and Space Sciences, Chalmers University of_
_Technology, Onsala Observatory, 439 94 Onsala, Sweden._
35 _Leiden_ _Observatory,_ _Leiden_ _University,_ _PO_ _Box_ _9513,_ _2300_ _RA,_
_Leiden, The Netherlands._
36 _Inter-university_ _Institute_ _for_ _Data_ _Intensive_ _Astronomy,_ _Depart-_
_ment_ _of_ _Astronomy,_ _University_ _of_ _Cape_ _Town,_ _7701_ _Rondebosch,_
_Cape Town, South Africa._
37 _Inter-university_ _Institute_ _for_ _Data_ _Intensive_ _Astronomy,_ _Depart-_
_ment_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _the_ _Western_ _Cape,_
_7535 Bellville, Cape Town, South Africa._
38 _SRON_ _Netherlands_ _Institute_ _for_ _Space_ _Research,_ _Landleven_ _12,_
_9747, AD Groningen, The Netherlands._
39 _Kapteyn Astronomical Institute, University of Groningen, Postbus_
_800, 9700, AV, Groningen, The Netherlands._


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–57 (2022)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[2].provided.evidence[1]",
  "value": "Archival high-resolution continuum images and UV tables at ~0.5 arcsec resolution",
  "failed_quote": "For the SMA data, we either use the reduced continuum images from Enia et al. (2018), or we download the UV tables from the science archive and we produce the continuum images"
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Herschel SPIRE flux densities at 250, 350, and 500 um",
  "failed_quote": "The candidates belonging to the other surveys were covered by the catalogues of Wardlow et al. (2013), Bussmann et al. (2013, 2015), Calanog et al. (2014), and Nayyeri et al. (2016)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Redshifts of lens candidates and background sources",
  "failed_quote": "In addition to these high-resolution observations, we search both previous literature works and the NASA/IPAC Extragalactic Database for the lens candidates and/or potential lenses redshifts."
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Initial rough estimate of Einstein radius as half the separation between multiple images",
  "failed_quote": "Depending on the morphology of the lensing features, we define 𝜃E as either the radius of the circle centred on the lens that best fits the Einstein ring (e.g., S_4), or as half of the separation between the multiple images (e.g., S_2) following the approach of Amvrosiadis et al. (2018)."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Compute curve of growth from 10^4 MC realizations of component parameters to derive R50, mu50, m_F110W, and C31 = R75/R25; measure aperture photometry of lensed background sources at 1.1 um; compute K-corrections using Brown Atlas elliptical templates.",
  "failed_quote": "To estimate the F110W magnitude of the SLACS lenses, we redshift and normalize the template to match the F814W magnitude using PySynphot package."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Fit singular isothermal ellipsoid (SIE) mass model (plus external shear for S_3, S_19, S_40) and reconstruct background source using a preliminary Sersic parametric fit followed by a Voronoi pixelization with constant regularization.",
  "failed_quote": "The lens modelling is performed with PyAutoLens (Nightingale et al. 2018, 2021), by using a non-linear search trough dynesty (Speagle 2020) ."
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "Nested sampling non-linear search via dynesty with Gaussian, uniform, and log-uniform priors",
  "failed_quote": "The lens modelling is performed with PyAutoLens (Nightingale et al. 2018, 2021), by using a non-linear search trough dynesty (Speagle 2020) ."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Producing continuum images from archival SMA UV tables",
  "failed_quote": "or we download the UV tables from the science archive and we produce the continuum images with the Common Astronomy Software Applications (CASA) software."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Environment for running ELLIPSE/ISOFIT and CMODEL tasks",
  "failed_quote": "It supersedes the IRAF task ELLIPSE (Jedrzejewski 1987)"
 },
 {
  "path": "software[8].used_for.evidence[0]",
  "value": "Language in which GASP2D is written",
  "failed_quote": "GASP2D and GALFIT are written in IDL and C, respectively."
 },
 {
  "path": "software[9].used_for.evidence[0]",
  "value": "Source segmentation masking (make_sources_mask) for sky subtraction and centroid finding (find_centroids) for PSF construction",
  "failed_quote": "using the make_sources_mask task of the photutils.background python package (Bradley et al. 2021)."
 },
 {
  "path": "software[10].used_for.evidence[0]",
  "value": "Two-dimensional Savitsky-Golay smoothing of the stacked PSF",
  "failed_quote": "The stacked PSF is smoothed using a python two-dimensional Savitsky-Golay filter (e.g. Ratzlaff & Johnson 1989) to remove noise."
 },
 {
  "path": "software[11].used_for.evidence[0]",
  "value": "Gravitational lens modelling and pixelized background source reconstruction",
  "failed_quote": "The lens modelling is performed with PyAutoLens (Nightingale et al. 2018, 2021), by using a non-linear search trough dynesty (Speagle 2020) ."
 },
 {
  "path": "software[12].used_for.evidence[0]",
  "value": "Non-linear nested sampling search in PyAutoLens",
  "failed_quote": "The lens modelling is performed with PyAutoLens (Nightingale et al. 2018, 2021), by using a non-linear search trough dynesty (Speagle 2020) ."
 },
 {
  "path": "software[13].used_for.evidence[0]",
  "value": "Computing synthetic magnitudes and K-corrections for lens galaxies",
  "failed_quote": "To estimate the F110W magnitude of the SLACS lenses, we redshift and normalize the template to match the F814W magnitude using PySynphot package ."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Einstein radius of S_8 (HERSJ020941.2+001558) = 2.4579 arcsec",
  "failed_quote": "S_8 HERSJ020941.2 + 001558 −0.259 +0.005 −0.010 0.046 +0.008 −0.002 2.4579 +0.002 −0.003"
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Einstein radius of S_18 (HATLASJ133008+245860) = 0.974 arcsec",
  "failed_quote": "S_18 HATLASJ133008 + 245860 0.037 +0.003 −0.010 −0.287 +0.010 −0.005 0.974 +0.001 −0.002"
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "GASP2D automatically sets initial parameter guesses for single/well-separated lenses, GALFIT enables simultaneous fitting of blended multi-galaxy lenses, and ISOFIT handles highly inclined disk lenses where parametric fits fail.",
  "failed_quote": "GASP2D has the advantage of automatically setting the initial guess values needed to fit the galaxy image, whereas GALFIT allows us to perform the simultaneous fit of multiple systems. We adopt the non-parametric Isophote Fitting algorithm (ISOFIT; Ciambur 2015) to model highly-inclined disk lenses for which GASP2D and GALFIT fail."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Reduced HST images, surface brightness models, residuals, and PSF cutouts are publicly available on Zenodo (doi:10.5281/zenodo.10007041); ALMA and SMA data were retrieved from public science archives.",
  "failed_quote": "The reduced images, models, residuals, and PSF cutouts are available on Zenodo at the following link https://doi.org/10.5281/zenodo.10007041 ."
 }
]
```
