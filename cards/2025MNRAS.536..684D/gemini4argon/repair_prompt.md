# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.536..684D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–29 (2023) Preprint 14 November 2024 Compiled using MNRAS L [A] TEX style file v3.0

## − **The salty emission of the intermediate-mass AGB star OH 30.1 0.7**


T. Danilovich [1] _[,]_ [2] _[,]_ [3] _[★]_, A. M. S. Richards [4], M. Van de Sande [5], C. A. Gottlieb [6], T. J. Millar [7], A. I. Karakas [1] _[,]_ [2],
H. S. P. Müller [8], K. Justtanont [9], J. M. C. Plane [10], S. Etoka [4], S. H. J. Wallström [3], L. Decin [3] _[,]_ [10], D. Engels [11],
M. A. T. Groenewegen [12], F. Kerschbaum [13], T. Khouri [9], A. de Koter [14] _[,]_ [3], H. Olofsson [9], C. Paladini [15],
R. J. Stancliffe [16]

1 _School of Physics & Astronomy, Monash University, Wellington Road, Clayton 3800, Victoria, Australia_
2 _ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Clayton 3800, Australia_
3 _Institute of Astronomy, KU Leuven, Celestĳnenlaan 200D, 3001 Leuven, Belgium_
4 _JBCA, Department Physics and Astronomy, University of Manchester, Manchester M13 9PL, UK_
5 _Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA Leiden, The Netherlands_
6 _Harvard-Smithsonian Center for Astrophysics, 60 Garden Street, Cambridge, MA 02138, USA_
7 _Astrophysics Research Centre, School of Mathematics and Physics, Queen’s University Belfast, University Road, Belfast BT7 1NN, UK_
8 _Astrophysik/I. Physikalisches Institut, Universität zu Köln, 50937 Köln, Germany_
9 _Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, 43992 Onsala, Sweden_
10 _School of Chemistry, University of Leeds, Leeds LS2 9JT, UK_
11 _Hamburger Sternwarte, Universität Hamburg, Gojenbergsweg 112, 21029 Hamburg, Germany_
12 _Koninklĳke Sterrenwacht van België, Ringlaan 3, 1180 Brussels, Belgium_
13 _Department of Astrophysics, University of Vienna, Türkenschanzstrasse 17, A-1180 Vienna, Austria_
14 _Anton Pannekoek Institute for Astronomy, University of Amsterdam, 1090 GE Amsterdam, The Netherlands_
15 _European Southern Observatory, Alonso de Cordova 3107, Vitacura, Santiago, Chile_
16 _H.H. Wills Physics Laboratory, University of Bristol, Tyndall Avenue, Bristol BS8 1TL, UK_


Accepted 2024 November 12. Received 2024 November 11; in original form 2024 August 30


**ABSTRACT**

We analyse continuum and molecular emission, observed with ALMA, from the dust-enshrouded intermediate-mass AGB star
OH 30.1 −0.7. We find a secondary peak in the continuum maps, “feature B”, separated by 4.6 [′′] from the AGB star, which
corresponds to a projected separation of 1 _._ 8 × 10 [4] au, placing a lower limit on the physical separation. This feature is most likely
composed of cold dust and is likely to be ejecta associated with the AGB star, though we cannot rule out that it is a background
object. The molecular emission we detect includes lines of CO, SiS, CS, SO 2, NS, NaCl, and KCl. We find that the NS emission
is off centre and arranged along an axis perpendicular to the direction of feature B, indicative of a UV-emitting binary companion
(e.g. a G-type main sequence star or hotter), perhaps on an eccentric orbit, contributing to its formation. However, the NaCl and
KCl emission constrain the nature of that companion to not be hotter than a late B-type main sequence star. We find relatively
warm emission arising from the inner wind and detect several vibrationally excited lines of SiS (𝑣= 1), NaCl (up to 𝑣= 4)
and KCl (up to 𝑣= 2), and emission from low energy levels in the mid to outer envelope, as traced by SO 2 . The CO emission
is abruptly truncated around 3 _._ 5 [′′] or 14,000 au from the continuum peak, suggesting that mass loss at a high rate may have
commenced as little as 2800 years ago.


**Key words:** stars: AGB and post-AGB – circumstellar matter – stars: individual: OH 30.1-0.7



**1** **INTRODUCTION**


The asymptotic giant branch (AGB) phase is a late evolutionary
stage that low- and intermediate-mass stars (with initial masses
0 _._ 8 M ⊙ ≲ _𝑀_ _𝑖_ ≲ 8 M ⊙ ) pass through towards the end of their lives.
During this phase, the stars eject a significant amount of material
through a stellar wind, with mass-loss rates in the range ∼ 10 [−][8] to
10 [−][4] M ⊙ yr [−][1] . Some lower-mass stars, with initial masses ∼ 1 _._ 5 to
4 M ⊙, are expected to end their lives as carbon stars, after dredging
up newly-synthesised carbon from their interiors to their surfaces


_★_ E-mail: taissa.danilovich@monash.edu


© 2023 The Authors



(Herwig 2005; Karakas & Lattanzio 2014). Intermediate-mass stars,
with initial masses in the range ∼ 4 to 8 M ⊙, are not expected to end
their lives as carbon stars (Herwig 2005; Karakas & Lattanzio 2014;
Ventura et al. 2018; Marigo et al. 2020) because they are massive
enough to initiate hot bottom burning (HBB), a phenomenon where
the star’s convective envelope penetrates the hydrogen-burning shell
and enables additional (proton-capture) nucleosynthesis processes
(Karakas & Lattanzio 2014). In particular, HBB destroys [12] C and
18 O. The destruction of 12 C prevents the formation of carbon stars
and results in low [12] C/ [13] C ratios, and the destruction of [18] O results
in very large [17] O/ [18] O ratios, allowing us to observationally identify
stars in which HBB has taken place (Justtanont et al. 2015). We also

2 _Danilovich et al_


note that the precise mass ranges of stars that become carbon stars or
which undergo HBB depends on their initial metallicity and on some
numerical details of the models (such as the treatment of convection
and mass-loss rates, Karakas & Lugaro 2016). The numbers given
here are for solar metallicity.
A small sample of stars have been shown to have intermediate
initial masses based on the prevalence of H 2 [17] O emission and the
absence of H 2 [18] O emission in _Herschel_ observations (Justtanont
et al. 2015). Some of these stars have also been found to have low
12 C/ 13 C ratios (e.g. Delfosse et al. 1997), providing further evidence
for HBB. These intermediate-mass stars have all previously been
found to have high mass-loss rates, though the precise values of the
mass-loss rates have been the subject of much debate since different
values are found using different methods (see for example Heske
et al. 1990; Justtanont et al. 2006). Several explanations have been
put forward to explain these discrepant results, including the concept
of a “superwind”: a recently-initiated period of enhanced mass-loss
(Heske et al. 1990; Delfosse et al. 1997; Justtanont et al. 2013).
This scenario could explain the relatively high mass-loss rates obtained from spectral energy distributions (SEDs) and dust modelling,
thought to represent the more recent mass loss, while the lower massloss rates from CO are thought to be the remnant of an earlier period
of lower mass loss.

Thus far, no studies of the circumstellar chemistry of confirmed
intermediate-mass AGB stars have been presented. In this work we
focus on the intermediate-mass AGB star OH 30.1 −0.7, thought to
have a very high mass-loss rate ( _>_ 10 [−][4] M ⊙ yr [−][1] based on SED
modelling, Justtanont et al. 2013, 2015). This star has featured in
several other studies of extremely dusty stars based on various (spatially unresolved) infrared and radio observations (Heske et al. 1990;
Delfosse et al. 1997; Justtanont et al. 2006). Although several previous studies have considered OH 30.1 −0.7 to have a superwind, Decin
et al. (2019) argued for a binary scenario rather than a superwind.
Atacama Large Millimetre/sub-millimetre Array (ALMA) observations of CO around two intermediate-mass stars (OH 30.1 −0.7 and
OH 26.5 +0.6) were presented by Decin et al. (2019) who attributed
structures in their circumstellar envelopes (CSEs) to interactions
with binary companions. Decin et al. (2019) further argue that the
apparently high mass-loss rates could be explained by an equatorial
density enhancement of gas and dust arising from gravitational shaping by a companion. This would then change the apparent mass-loss
rate depending on the orientation of the system and the line of sight
through the CSE. Certainly some of the structures observed in the
winds of both of these stars are similar to structures seen around

other AGB stars that are also attributed to binary interactions (for
example Cernicharo et al. 2015; Kim et al. 2017; Decin et al. 2020).
For AGB stars more generally, it has recently been shown that
binary companions, especially solar-like stars emitting notable UV
flux, can have an impact on circumstellar chemistry (Van de Sande
& Millar 2022). Observational studies have found some molecular
emission distributions that are best explained through the presence of
a solar-type companion (Siebert et al. 2022; Coenegrachts et al. 2023;
Danilovich et al. 2024). In particular, Danilovich et al. (2024) showed
that asymmetric distributions of SiN, SiC and NS could be attributed
to a main sequence companion on a highly eccentric orbit passing
through the inner wind of W Aql every ∼ 1100 years. Coenegrachts
et al. (2023) found asymmetric clumps of NaCl emission forming
an approximate spiral in the inner wind of the oxygen-rich AGB star
IK Tau, which they attributed to an unseen companion close to the
AGB star.

We present here a complete molecular inventory of the existing
ALMA data of OH 30.1 −0.7 (also known as V1362 Aql, IRAS


MNRAS **000**, 1–29 (2023)



18460 –0254, AFGL 5535), where previously only CO observations
were published. In Sect. 2 we describe our re-reduction of the ALMA
data, present the continuum, and describe our analysis of the molecular lines. In Sect. 3 we present the detected molecular lines and
discuss the implications of these results in Sect. 4, in particular how
these observations support the presence of a companion star. We
summarise our conclusions in Sect. 5.


**2** **OBSERVATIONS**


OH 30.1 −0.7 was observed with two ALMA receivers, Bands 3
and 6, in 2016 and 2017, as part of project 2016.1.00005.S. The
frequency ranges, restoring beams, observation dates and ALMA
configurations are given for each tuning in Table A1. The Band
3 data were observed with a single ALMA configuration (angular
resolution ∼ 1 _._ 3 [′′] ), whereas the Band 6 data were observed with
two antenna configurations and, for convenience, we refer to these
as the extended (angular resolution ∼ 0 _._ 3 [′′] ) and compact (angular
resolution ∼ 1 _._ 5 [′′] ) configurations. The Band 3 data were observed
with velocity resolutions of 2.6 to 2.9 km s [−][1] (1 MHz) and the Band
6 data were observed with a velocity resolution around 2.5 km s [−][1]

(2 MHz). More precise velocity and frequency resolutions are noted
in Table A1 for each tuning. At the time of the ALMA observations,
the star was close to minimum light (phase _𝜙_ ∼ 0 _._ 45) in its variability
cycle.


**2.1** **Data reduction**


_2.1.1_ _Imaging_


Rather than using the data products from the standard
ALMA pipeline, we performed an additional self-calibration for
OH 30.1 −0.7. First we downloaded the standard ALMA data products for project 2016.1.00005.S from the ALMA Science Archive
(Stoehr et al. 2017) and reconstituted the calibrated Measurement
Sets (MS) for each array configuration and spectral tuning. We
mainly followed the data processing steps as listed for ATOMIUM
in Sect. 3.2.1 of Gottlieb et al. (2022). In summary, we split out each
spectral window of the calibrated target data, adjusting the frequencies to constant velocity with respect to the Local Standard of Rest
( _𝜐_ LSR ) in the target direction. We identified the line-free channels by
inspection of the visibility spectra and (where available) the archive
example image cubes. We made continuum-only images for each
configuration and used these as a starting model for self-calibration.
Continuum subtracted image cubes were made for each spectral window as listed in Table A1. The Band 6 data for OH 30.1 −0.7 were

observed in two configurations with equivalent spectral tunings, and
these were combined as described in Sect. 3.2.3 of Gottlieb et al.

(2022) to make combined continuum images and combined spectral
cubes.

The details of the various continuum images we made are given
in Table A2. These include continua for each individual configuration, the combined images created using different weightings, and
an additional Band 3 image created with the same beam parameters
as the compact Band 6 continuum image, to allow for a more direct
comparison, as discussed below. In all imaging, Briggs weighting
(Briggs et al. 1999) was used with robust 0.5 to interpolate across
unsampled regions of the visibility plane, giving more weight to cells
closer to measured samples. In combining data from extended and
compact configurations, we gave both data sets equal weight which
gives a full resolution close to that of the extended configuration but

with better sensitivity to large angular scales. However, the sampling
of the visibility plane is sparsest for the longest baselines, which can
lead to slight artefacts. To mitigate this we applied a Gaussian taper
to the visibility weights as a function of projected baseline length to
reduce the weight of data from the longest baselines. The FWHM
(full width half maximum) of the taper is selected to correspond
to a slightly smaller angular resolution than the desired synthesised
beam. This gives a coarser resolution but reduces errors due to unsampled scales. The resulting beam sizes and tapers for the combined
continuum data are given in Table A2. No taper was used for the line
data and beam sizes for those cubes are given in Table A1.


_2.1.2_ _Accuracy_


The factors contributing to absolute flux scale and astrometric accuracy are described in the ALMA Technical Handbook (Cortes et al.
2023), as applied to similar data in Sect. 3.2.2 of Gottlieb et al.
(2022). We matched the continuum flux densities on baselines of
similar length for the two band 6 configurations to remove relative
flux errors to the level of the noise (see Table A2). The ALMA flux
scale in Band 6, for a single observation, is accurate to 5%, or up to

∼
10% for combined images, and somewhat better in Band 3.
After fitting a 2D Gaussian component to a compact source, the
relative (stochastic) position error is proportional to the beam size
divided by the signal to noise (S/N). The constant of proportionality
is 0.5 for a well-filled array (Condon 1997), rising for sparser _𝑢𝑣_
coverage such as ALMA at higher frequencies and a more extended
configuration. This gives stochastic errors for the position of the stellar peaks of ∼ 12, ∼ 7 and ∼ 1 mas, for Band 3 and the Band 6 lower
and higher resolutions, respectively (using the values in Table A2 and
constants of 0.5, 0.75 and 1). These are relevant for relative separations e.g. from a putative companion. The phase-reference source was
J1851+0035, 3 [′′] _._ 5 from the target. The main contribution to astrometric uncertainty is errors in transferring the phase reference solutions
to the target (approximately [phase rms]/360× beam). The phase rms
on a point source was about 25 [◦], 15 [◦], and 10 [◦] at Band 3 and the Band
6 compact and extended configurations, respectively. This leads to
astrometric errors of approximately [beam size]/15, /25, and /35, respectively. Using the mean beam sizes (Table A2) this corresponds
to astrometric errors of approximately 90 mas, 60 mas, and 10 mas
for Band 3 and the Band 6 lower and higher resolutions, respectively.
This is in addition to S/N (stochastic) errors; other contributions
such as antenna position errors are negligible except at the highest
resolution, giving total astrometric errors for the continuum peaks of
about 91, 63 and 10 mas, respectively. The position of OH 30.1 −0.7
based on our observations, using a weighted mean and taking these
astrometric uncertainties into account, is given in Table 1. We find
that the measured positions are offset from the observing positions
(also given in Table 1) by ∼ 0 [′′] _._ 6 in each coordinate.


**2.2** **Continua**


In Fig. 1 we plot the continuum images for each configuration, and
the combined Band 6 continuum image. The central continuum emission is resolved in the Band 6 images, and we detect some extended
emission. The red crosses in Fig. 1 indicate the peaks of the continuum emission, which we found through fitting a 2D Gaussian to the
extended configuration continua using the CASA routine `imfit` . In
the continuum plots (and all subsequent plots of molecular emission)
the data is normalised such that the continuum peaks lie at (0,0). The
precise location of this peak, in J2000 coordinates, is given in Table 1



_The salty emission of OH 30.1_ − _0.7_ 3


**Table 1.** Sky positions and key parameters of OH 30.1 −0.7.


Right Ascension Declination
Observed position B6 18:48:41.91 −2:50:28.3
Observed position B3 18:48:41.91 −2:50:28.3

Band 6 extended _[𝑎]_ 18:48:41.94961 −2:50:28.9241

Band 6 compact _[𝑎]_ 18:48:41.94932 −2:50:28.8653
Band 3 _[𝑎]_ 18:48:41.95096 −2:50:28.8333


Mean position _[𝑏]_ 18:48:41.9496 −2:50:28.921

±1 _._ 3 mas ±7 _._ 8 mas

Distance _[𝑐]_ 3900 ± 800 pc
_𝜐_ LSR _[𝑑]_ 100 _._ 3 ± 1 _._ 2 km s [−][1]


**Notes.** ( _[𝑎]_ ) Astrometric positions in ICRS J2000 obtained from fits to the
continuum peaks in this work. Uncertainties as described in Sect. 2.1.2. ( _[𝑏]_ )
The weighted mean position, assuming negligible proper motion between
epochs at the distance of OH 30.1 −0.7, with the associated uncertainty
calculated from the standard deviation. ( _[𝑐]_ ) Distance calculated using the
maser phase-lag method by Engels et al. (2015). ( _[𝑑]_ ) LSR velocity calculated
in Sect. 2.5.


as are the positions measured from the other ALMA configurations.
We find that the slight differences between positions are close to the
predicted astrometric errors.
Considering the combined Band 6 continuum emission, the 5 _𝜎_
contour shows some ellipticity with a major axis running from southeast to northwest and varying in extent from 0.57 [′′] to 0.73 [′′] . The 3 _𝜎_
contour has a less regular shape, encompassing more faint emission
with a greater extent of 1.06 [′′] to the southeast and a minimum extent of 0.64 [′′] to the northwest. These measurements consider only
regions of flux enclosing the continuum peak and neglect isolated
islands of emission. We use a similar method to measure extents

(including the extents of molecular emission) as that described in
Danilovich et al. (2021) for angular sizes. Based on the distance of
3900 pc (Engels et al. 2015), these continuum extents correspond to
dust at projected separations of 2200 – 4100 au from the continuum
peak of OH 30.1 −0.7. Although we mainly analysed the combined
(equal weighting) continuum, we find essentially identical results
when considering the continuum from the extended array only.


_2.2.1_ _Secondary peak: feature B_


We detect a secondary peak to the north of the primary peak, with
a certainty _>_ 10 _𝜎_ . This lies well beyond the extent of the emission
centred on the primary peak. As can be seen in Fig. 1, there are some
less intense regions of continuum emission (detected at _>_ 3 _𝜎_ ) lying
between the primary and secondary peaks, hinting at a connection
between them. To check whether the secondary peak is truly associated with the AGB star, rather than being a coincidental background
or foreground source, we checked the individual configuration data
observed with Band 6 and the Band 3 data. The secondary peak is
clearly detected in data from both the extended and compact Band
6 configurations. However, the Band 3 continuum for OH 30.1 −0.7
has a lower signal to noise ratio and we do not detect the secondary
peak. In Fig. A1 we plot the Band 3 continuum next to the compact
configuration Band 6 continuum, with the former processed to have
the same restoring beam as the Band 6 data. In the compact Band 6
data, there appears to be a bridge connecting the primary and secondary peaks, traces of which are seen in the combined and extended
continuum data in Fig. 1. This suggests an association between the
two peaks. For simplicity we will henceforth refer to the secondary
continuum peak as “feature B” and will assume that the AGB star
coincides with the primary continuum peak. We find the separation


MNRAS **000**, 1–29 (2023)

4 _Danilovich et al_





RA offset [arcsec]

|Compact|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||



6 4 2 0 2 4 6

RA offset [arcsec]



















10 3


10 4



6


4


2


0


2


4


6


6


4


2


0


2


4


6



10 3


10 4









**Figure 1.** Various continuum images for OH 30.1 −0.7, plotted using logarithmic flux scales. The configurations are given in the top left corner of each image
and refer to the Band 6 observations unless Band 3 is indicated. The contours indicate levels of 3 _𝜎_ (thinnest white line), and 5, 10, 30 and 100 _𝜎_ (thicker white
lines). The red crosses indicate the position of the continuum peak; see Table 1 for the astrometric precision of the position. The beams are shown as white
ellipses in the bottom left corners. North is up and east is left. Additional details are given in Table A2.



between the two peaks to be 4.6 [′′] . At a distance of 3.9 kpc, this gives
a projected separation of 1 _._ 8 × 10 [4] au (2 _._ 7 × 10 [17] cm), corresponding
to a lower limit on the physical separation. Feature B lies beyond the
extent of the CO _𝐽_ = 2 − 1 and _𝐽_ = 1 − 0 emission, as discussed in

Sect. 4.3.


_2.2.2_ _Spectral indices_


Since we have observations from two different ALMA Bands for
OH 30.1 −0.7, we next calculate the spectral indices of the AGB
star and of feature B. This is done using the continuum images from
the compact Band 6 configuration and the Band 3 data processed to
have the same beam as the compact Band 6 data (see Fig. A1 and
Table A2). The nominal centre frequencies for the Band 3 and Band
6 continua are 107.86 and 236.02 GHz, and the rms are 0.013 and
0.042 mJy respectively. The continuum peaks are 0.788 and 7.26
mJy beam [−][1] . Allowing for the rms and a 7% flux scale uncertainty
as applied to the target, per band, we find a spectral index of 2 _._ 8 ± 0 _._ 3
for the AGB star.
For feature B, the Band 6 flux is 0.46 mJy beam [−][1] and for Band 3
the flux in the same region is 0.028 mJy beam [−][1] (i.e. _<_ 3 _𝜎_ ). Using
the Band 3 flux as an upper limit, this gives a lower limit on the


MNRAS **000**, 1–29 (2023)



spectral index of _>_ 3 _._ 6, even steeper than for the AGB star itself.
These results are discussed in more detail in Sect. 4.3.


**2.3** **Line identification**


The line identification was initially carried out by extracting spectra in
circular apertures centred on the stellar continuum peak. Spectra were
extracted for apertures of different radii to ensure that lines excited
in different parts of the circumstellar envelope were not overlooked.
For example, compact lines, excited close to the star, are most easily
detected in spectra extracted for smaller apertures, whereas more
extended lines, especially those with shell-like emitting regions, are
more easily detected in larger extraction apertures, where the aperture
encompasses large fractions of their fluxes. In cases where the line
detection appeared marginal in the spectra, we constructed zeroth
moment maps (integrated intensity maps) to check for emission. The
lines identified towards OH 30.1 −0.7 are listed in Table A3. Lines
are included in our list of detections if they are seen at levels of
≥ 3 _𝜎_ above the noise in at least one of the spectra and/or the zeroth
moment map. Lines marked as tentative either fulfil only one of
these criteria or are blended with another line. Zeroth moment maps
were constructed to include all channels with emission _>_ 3 _𝜎_ in the

spectra plus an additional 1–2 channels on either side of the line. An

_The salty emission of OH 30.1_ − _0.7_ 5



0.5


0.4


0.3


0.2


0.1


0.0


0.04







0.02


0.00


229.25 229.50 229.75 230.00 230.25 230.50 230.75 231.00
Frequency [GHz]


**Figure 2.** ALMA spectra of one tuning towards OH 30.1 −0.7, extracted for two apertures, as indicated in the top right of each subplot. The molecular carriers
of various spectral lines are indicated at the top of each plot; see Table A3 for further details. The narrow feature at 230.6 GHz is interstellar CO contamination
(see Sect. 2.4).



exception are the partially blended lines Na [37] Cl and [30] SiS at 227.560
and 227.590 GHz, for which we carefully chose a minimal channel
between the two peaks that was not then included in either zeroth
moment map, to avoid cross-contamination.
We used data from the Cologne Database of Molecular Spectroscopy (CDMS, Müller et al. 2001, 2005) to assign carriers to
detected lines. Once we had constructed our initial list of identified
lines, we checked which lines from each species were covered by
our observations, including lines in vibrationally excited states. The
detailed results of these checks are given in Sect. 3, but we note here
that in some cases we identified additional lines in this manner that
are blended with other, often brighter, lines. In those cases, we note
the potentially blended lines in the notes columns of Table A3.
An example spectrum from the Band 6 data, plotted for two extraction apertures, is given in Fig. 2 with the identified lines labelled.
The remaining Band 6 spectra are shown in Fig. A2 and the Band 3
spectra are shown in Fig. A3.


**2.4** **Interstellar contamination and resolved-out flux**


Previous observations of CO towards OH 30.1 −0.7 have encoun
tered problems with contamination by interstellar features, see for
example De Beck et al. (2010). In short, because this star is located
in the direction of a densely populated region of the galactic disc,
a larger telescope beam — such as one from a single antenna — is
prone to capture emission, especially of low-energy CO lines, from
background or foreground sources along the line of sight, in addition to the emission originating from the target AGB star. The contaminating sources are commonly molecular clouds with relatively
narrow lines, compared with the wide lines of AGB circumstellar
envelopes, making them easy to distinguish, though not necessarily
easy to disentangle from the AGB emission. In the particular case
of OH 30.1 −0.7, we have identified the massive star-forming region



where the central velocity of the line is _𝜐_ cent, the width of the line
is _𝜐_ w, and the flux at the centre of the line is _𝐹_ 0 . The fit is done
over the free parameters _𝐹_ 0, _𝜐_ cent, _𝜐_ w, and _𝛾_ . The soft parabola


MNRAS **000**, 1–29 (2023)



W43 as the likely source of background contamination, which has
been found to have gas velocities comparable to the velocities at
which we see contamination (Nguyen Luong et al. 2011). (See also
Saral et al. 2017, where OH 30.1 −0.7 can be seen as a bright orange
point source on the edge of W43 in their Fig. 2.)
ALMA has an advantage because, although the ALMA field of
view can be similar to the half-power beam width (HPBW) of a
single antenna, the interferometer acts as a spatial filter, resolving
out smooth large-scale emission, including that from large molecular
clouds. Unfortunately, some contamination persists, as can be seen in
our CO channel maps in Figs. 3 and A6. A more thorough discussion
of the contamination is given in Appendix B.
A common problem with observing using an interferometer such
as ALMA is the possibility of resolved-out flux – that is, smooth largescale flux is filtered out of the observations. However, the maximum
recoverable scale of our lowest resolution Band 6 observations is
12.8 [′′], larger than the CO emitting region (see Fig. 3), and the spectra
of the low and high resolution Band 6 observations are in good
agreement, indicating that no flux has been resolved out.


**2.5** **Integrated line fluxes and central velocities**


Having identified the carriers of the lines in our data, as described
in Sect. 2.3, we performed a basic analysis of all the unambiguous
detections of unblended lines. We fit a soft parabola line profile
function (Olofsson et al. 1993) defined as



2 [�] _𝛾_ /2

_,_ (1)
�



_𝐹_ ( _𝜐_ ) = _𝐹_ 0



�



1 − _𝜐_ − _𝜐_ cent
� _𝜐_ w

6 _Danilovich et al_


fit is performed for all extraction apertures in which a given line
is detected. In Table A3 we list the central velocities and velocity
widths obtained from these fits and the extraction aperture for which
we determined that the line was most clearly detected. This means
that for lines with compact emission we fit soft parabolas to spectra
extracted for smaller apertures, while for extended emission we used
spectra extracted for larger apertures. Generally, we were not able to
fit soft parabolas to tentative lines or lines with hyperfine structure.
After obtaining the line widths from the soft parabola fits, we used
these as a guide to calculate the integrated line fluxes, over velocity
ranges a few km s [−][1] wider than the line widths from the soft parabola
fits, to better account for flux that may be in line wings. For each
individual line, the same spectrum (extracted for the same aperture)
was used to find both the central velocity and the integrated flux. The
integrated fluxes are also listed in Table A3.
Some examples of lines with their corresponding soft parabola fit
are shown in Fig. A4, where we plot CO ( _𝐽_ = 2 − 1), low energy
lines of SiS and SO 2, and a higher energy (𝑣= 2) line of NaCl.
The fits to the SiS and SO 2 lines produce larger line widths than
for CO: _𝜐_ w ∼ 22 km s [−][1] compared with _𝜐_ w = 18 km s [−][1] for CO.
This is because the automated fit does not account for the blue wing
of the CO emission where flux is strongly detected in the channels
76.5–81.5 km s [−][1], despite there not being a clear CO detection in the
channel at 84.1 km s [−][1] . The reason for this phenomena is discussed
further in Sect. 4.2.2. To better account for the full velocity width
of the CO line, and hence the expansion velocity of the CSE, we
calculate the full width of the CO line from the channel maps (Fig. 3.
By considering the reddest and bluest channels with CO detections
centred on the continuum peak with a certainty _>_ 30 _𝜎_, we determine
the expansion velocity to be 23 km s [−][1] .
By averaging the central velocities found from the soft parabola
fits, we calculate a systemic velocity of _𝜐_ LSR = 100 _._ 3 ± 1 _._ 2 km s [−][1] .
This value is in agreement with the LSR velocity of 100.0 km s [−][1]

found by De Beck et al. (2010) from CO observations. The most
significant outlier in our sample is the Na [35] Cl (𝑣= 1 _,_ _𝐽_ = 8 − 7)
line at 103.415 GHz in Band 3, which has a central velocity of
103.7 km s [−][1] . We judge the line unlikely to be misidentified since
several other NaCl lines are detected in our observations, including vibrationally excited lines. It is possible that this line might be
blended with another, unidentified line. However, we note that the
other vibrationally excited NaCl lines tend to lie redwards of the
systemic velocity, while the lines in the ground vibrational state lie
closer to the systemic velocity (within 1 km s [−][1] but on the blue side).
We also find that the KCl lines overall tend to lie slightly redwards of
the systemic velocity (with the exception of one [41] K [35] Cl line). The
CO lines also lie 0.6 to 1.6 km s [−][1] redwards of the systemic velocity.
In contrast, the SiS, SO 2, and CS lines tend to lie bluewards of the
systemic velocity. These differences are likely because of differences
in excitation conditions and regions and certainly contribute to the
moderate uncertainty on our averaged systemic velocity.


**3** **DETECTED MOLECULES**


In the following subsections we discuss the detections of the various
molecular species seen towards OH 30.1 −0.7 in our observations.
The observations, including the number of detected lines and the
range of lower level energies they cover, are summarised in Table
2. Of particular note are the large number of NaCl and KCl lines
(discussed in Sect. 3.6) and the NS lines detected (discussed in
Sect. 3.5). After carefully checking our data, we were not left with
any unidentified lines.


MNRAS **000**, 1–29 (2023)



**Table 2.** An overview of all the molecules detected towards OH 30.1 −0.7.


Molecule _𝐸_ low [K] _𝑁_ lines _𝑁_ iso Sect. Ref.

CO 0–6 3 2 3.1 1

SiS 66–1134 8 4 3.2 2

CS 24 1 1 3.3 3

SO 2 3–108 10 3 3.4 4

NS 3 2* 1 3.5 5

NaCl 17–2143 9 2 3.6 6

KCl 39–977 9 3 3.6 7


**Notes.** The _𝐸_ low columns give the range of lower level energies among the
detected lines of that molecule. The _𝑁_ lines column indicates the total number
of lines from that molecule, including isotopologues but excluding hyperfine
components, that were detected. The _𝑁_ iso column indicates the total number
of isotopologues that were detected. The Sect column gives the reference to

the section in this work where observations of that molecule are discussed in

more detail. The Ref column gives the reference for the line frequencies
included in this work. (*) indicates that the molecular lines are made up of
multiple (hyperfine) components which are not counted as separate lines.
**References.** 1: Winnewisser et al. (1997), 2: Müller et al. (2007), 3: Gottlieb
et al. (2003), 4: Belov et al. (1998); Klisch et al. (1997); Müller & Brünken
(2005) 5: Lee et al. (1995) 6: Caris et al. (2002), 7: Caris et al. (2004).


**3.1** **CO**


CO is a well-studied density tracer of circumstellar envelopes. In
Fig. 3 we plot the combined channel maps of the _𝐽_ = 2 − 1 emission
towards OH 30.1 −0.7. Because of the large amount of interstellar
contamination, we highlight contours at and above 10 _𝜎_ and also
show significant (3 and 5 _𝜎_ ) negative contours, which arise from
resolved out (interstellar) flux. The CO emission originating from
OH 30.1 −0.7 has an almost circular distribution across channels,
with the diameter of the emission shrinking towards more extreme red
and blue velocities, as is typical of emission from a fairly spherical,
radially expanding envelope. The most significant deviation from this
is the absence of circumstellar emission in the channel at 84.1 km s [−][1] .

This could be the result of CO self-absorption or a background ISM
source with a similar flux level visually blended with the CSE and
resulting in the CSE being resolved out in this channel. Singledish observations (e.g. Heske et al. 1990; Justtanont et al. 2013,
and Fig. B1) show significant contamination around this channel.
There are also some internal arcs contributing to density structures
within the CSE, notably in the channels from 86.6 to 114.0 km s [−][1] .
The internal structures are more clearly seen in the (overall slightly
less sensitive) extended configuration only channel maps, shown in
Fig. A5, which also show less contamination owing to a smaller
maximum recoverable scale. The _𝐽_ = 1 − 0 channel maps are shown
in Fig. A6 and show a similar almost-circular distribution. However,
the internal structures are not resolved, owing to a larger beam size
(1 _._ 5 [′′] × 1 _._ 1 [′′], see Table A1).
The emission in the central channel of _𝐽_ = 2 − 1, which we defined
as the channel with LSR velocity _𝜐_ LSR = 99 _._ 3 km s [−][1] because it
is the closest to the systemic velocity, extends out to separations
of 2.5 to 3.9 [′′] (9800 to 15000 au) from the continuum peak when
considering the 3 _𝜎_ contour. The minimum extent occurs to the north
northwest, while the maximum extent is in the southeasterly direction
(see Fig. 4). For the Band 3 data of CO _𝐽_ = 1 − 0, the channel closest
to the systemic velocity (99.2 km s [−][1] ) suffers from a large amount of
interstellar contamination, so we measured the extent for the channel
with _𝜐_ LSR = 101 _._ 7 km s [−][1], and found that the smallest and largest
extents were 3.3 and 4.4 [′′], in the same directions as for the _𝐽_ = 2 − 1
emission (see Fig. A6).
In Fig. 4 we plot integrated intensity maps of CO _𝐽_ = 2 − 1 and

8


6


4


2


0


2


4


6


88


6


4


2


0


2


4


6


88


6


4


2


0


2


4


6


88


6


4


2


0


2


4


6


88


6


4


2


0


2


4


6


8



_The salty emission of OH 30.1_ − _0.7_ 7


0.200


0.175


0.150


0.125


0.100















0.075


0.050


0.025


0.000


|68 .8 km/s|68 .8 km/s|71 .4 km/s|71 .4 km/s|73 .9 km/s|73 .9 km/s|76 .5 km/s|76 .5 km/s|79 .0 km/s|79 .0 km/s|
|---|---|---|---|---|---|---|---|---|---|
|81.5 km/s|81.5 km/s|84.1 km/s|84.1 km/s|86.6 km/s|86.6 km/s|89.2 km/s|89.2 km/s|91.7 km/s|91.7 km/s|
|94.2 km/s|94.2 km/s|96.8 km/s|96.8 km/s|99.3 km/s|99.3 km/s|101.9 km/s|101.9 km/s|104.4 km/s|104.4 km/s|
|106.9 km/s|106.9 km/s|109.5 km/s|109.5 km/s|112.0 km/s|112.0 km/s|114.6 km/s|114.6 km/s|117.1 km/s|117.1 km/s|
|119.7 km/s|119.7 km/s|122.2 km/s|122.2 km/s|124.7 km/s|124.7 km/s|127.3 km/s|127.3 km/s|129.8 km/s|129.8 km/s|



7.5 5.0 2.5 0.0 2.5 5.0 7.5



7.5 5.0 2.5 0.0 2.5 5.0 7.5



7.5 5.0 2.5 0.0 2.5 5.0 7.5



7.5 5.0 2.5 0.0 2.5 5.0 7.5



7.5 5.0 2.5 0.0 2.5 5.0 7.5



RA offset [arcsec]



RA offset [arcsec]



RA offset [arcsec]



RA offset [arcsec]



RA offset [arcsec]



**Figure 3.** Combined ALMA observations of CO _𝐽_ = 2 − 1 towards OH 30.1 −0.7. The thicker white contours are drawn at levels of 10, 30, 50, 70, 100, 150,
200, 300, and 500 _𝜎_, the thinner grey contours at levels of 3 and 5 _𝜎_, and the dashed cyan contours at levels of −3 and −5 _𝜎_ . The red crosses indicate the position
of the continuum peak. The velocity of each channel is shown in the top right corner of each panel and the beam is shown as a white ellipse in the bottom left
corners. North is up and east is left. Note that there is significant interstellar contamination, especially for channels with velocities lower than 100 km s [−][1] .



_𝐽_ = 1 − 0 emission. For the _𝐽_ = 2 − 1 map we also overplot the
combined continuum emission. For the _𝐽_ = 1 − 0 map we overplot
the continuum emission from the Band 6 compact array, which is of
a comparable resolution and is sensitive to feature B, unlike the Band
3 continuum. For the _𝐽_ = 1 − 0 emission we only integrate over the
red part of the CO line (i.e. for _𝜐_ ≥ 101 _._ 7 km s [−][1] ) because the ISM
contamination is too large and confounds the data at lower velocities.
The comparison in Fig. 4 shows that the “indentation” seen in the CO
emission to the north-northwest, corresponds well to the location of
feature B in the continuum emission. The indentation is most clearly
seen in the CO _𝐽_ = 2 − 1 emission in the velocity channels from 91.7
to 114.6 km s [−][1] (Fig. 3). In the CO _𝐽_ = 1−0 emission the indentation



is less apparent, owing to the larger beam size of those observations.
Nevertheless, there is a slight asymmetry in the direction of feature
B. This phenomenon is discussed in more detail in Sect. 4.3.


One line of CO in the first vibrationally excited state was covered
in our observations but not detected. In addition to the main isotopologue of CO, we tentatively detect the C [17] O _𝐽_ = 1 − 0 line in
the spectrum. The line is not clearly seen in the zeroth moment map
and it is possible that there is some interstellar contamination around
that frequency. No lines of [13] CO or C [18] O were covered and we note
that detections of C [18] O were not expected, as previous studies have
shown evidence of HBB (Justtanont et al. 2015), which destroys [18] O
(Karakas & Lugaro 2016).


MNRAS **000**, 1–29 (2023)

8 _Danilovich et al_


6


4


2


0


2


4


6



|Col1|CO<br>J = 1-0|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||||
|||||
|||||


6 4 2 0 2 4 6

RA offset [arcsec]



|Col1|CO<br>J = 2-1|CO<br>J = 2-1|
|---|---|---|
||||
||||
||||
||||
||||


6 4 2 0 2 4 6

RA offset [arcsec]





10


8


6


4


2


0



4


3


2


1


0



6


4


2


0


2


4


6



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


2


4


6


|Col1|CO<br>J = 2-1|CO<br>J = 2-1|
|---|---|---|
||||
||||
||||
||||
||||



6 4 2 0 2 4 6

RA offset [arcsec]



**Figure** **4.** _Left:_ The zeroth moment map of CO _𝐽_ = 2 − 1 from the combined data towards OH 30.1 −0.7. The contours indicate flux levels of 5, 10, 30 and
50 _𝜎_ . The continuum peak is indicated by a red cross and the beam is shown as a white ellipse in the bottom left corner. North is up and east is left. _Centre:_ The
same CO _𝐽_ = 2 − 1 emission overplotted with red contours showing the continuum emission in Band 6 at levels of 5, 10, 30 and 100 _𝜎_ . The white ellipse in the
bottom left corner corresponds to the CO beam and the red ellipse to the continuum beam. _Right:_ The intensity map of CO _𝐽_ = 1 − 0 integrated over the red
channels (from 101.7 to 124.6 km s [−][1], refer to Fig. A6), overplotted with the Band 6 compact array continuum emission. The white contours indicated levels of
3, 5, 10, 30, and 50 _𝜎_ in the CO flux and the red contours indicated the 5, 10, and 30 _𝜎_ levels of the continuum flux. The white ellipse in the bottom left corner
corresponds to the CO beam and the red ellipse to the continuum beam.



**3.2** **SiS**


Our spectral coverage of SiS is uneven and misses lines from the
most abundant isotopologue, [28] Si [32] S (hereafter we drop the isotope
labels for [28] Si and [32] S). Therefore, although we detect several lines
from isotopologues of SiS, we do not perform an analysis of isotopic
ratios in this work.
We detect all the covered lines of [29] SiS, [30] SiS and Si [34] S in the
ground and first vibrationally excited states and note that these lines
were not covered for Si [33] S. The vibrational ground state [29] Si [34] S line
covered in our Band 6 observations was also detected. No lines in

the lowest two vibrationally excited states were covered by our Band
3 observations. The Band 3 data were not sensitive enough to detect
any lines of doubly substituted isotopologues.
Zeroth moment maps of our SiS detections are plotted in Fig. 5.
The lines in the ground vibrational state of the singly-substituted
isotopologues are relatively featureless, with only a few small protrusions seen for the [30] SiS 𝑣= 0 _,_ _𝐽_ = 14 − 13 line at a level of 3 _𝜎_ .
The lines in the vibrational ground state extend out to 0.3 to 0.7 [′′]

(1200 to 2700 au) from the continuum peak, and the peaks of the SiS
zeroth moment maps tend to be offset slightly from the continuum
peak in the southwest direction. The SiS lines in vibrationally excited
states and for the doubly-substituted isotopologue are either spatially
unresolved or marginally resolved and do not exhibit any structure,
though some are still slightly offset to the southwest of the continuum
peak.


**3.3** **CS**


One line of [12] C [32] S (hereafter, CS) in the vibrational ground state
was detected. The zeroth moment map for CS is shown in Fig. 6. The
emission is centrally peaked and the smoothed 3 _𝜎_ contour extends
out to ∼ 1 [′′] (3900 au). We smoothed the contour by binning and averaging it over 60 [◦] sections, to reduce the ragged edges of the contour.
We also neglected isolated islands of emission for this measurement.
No lines in the vibrational ground state of [13] CS or C [34] S were
covered in our frequency setups. One line of C [33] S in the ground
vibrational state was covered and not detected, as expected given the
likely isotopic ratio and the intensity of the corresponding C [32] S line.


MNRAS **000**, 1–29 (2023)



**3.4** **SO** **2**


SO 2 was detected towards OH 30.1 −0.7 with a shell-like distribution, as expected for a star with a high mass-loss rate and a dense
stellar wind (Danilovich et al. 2016; Wallström et al. 2024, see also
Sect. C3). In general, the detected transitions span relatively low
energy levels ( _𝐸_ low _<_ 110, see Table 2). This is despite higherenergy transitions being covered by our observations, in line with
SO 2 mainly being formed and excited further out in the wind. A notable non-detection was the SO 2 _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 11 5 _,_ 7 − 12 4 _,_ 8 line, which
has a lower level energy of 111 K, only 3 K above our highest-energy
detected line ( _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 14 3 _,_ 11 − 14 2 _,_ 12, _𝐸_ low = 108 K). This result is in line with the trend reported by Wallström et al. (2024) for
higher mass-loss rate AGB stars to exhibit lower-energy SO 2 lines,
and lower mass-loss rate AGB stars to exhibit higher-energy SO 2
lines.

In Fig. 7 we plot the predicted line intensities of all the SO 2 lines
(taken from CDMS) with lower level energies _<_ 500 K. If we consider
the predicted line intensities at 300 K (see right panel in Fig. 7), then
all the covered lines with lower level energies between 100 and 500 K
are expected to be brighter than at least one or two lines that were
detected. We checked the predicted line intensities for several other
temperatures and found that the undetected _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 11 5 _,_ 7 − 12 4 _,_ 8
line is only predicted to be fainter than all the detected lines for temperatures ≲ 25 K. The distribution for predicted line intensities at
25 K is shown in the left panel of Fig. 7. This suggests a surprisingly
low excitation temperature for SO 2 around OH 30.1 −0.7. This result
from the most abundant isotopologue is in agreement with the exclusively very low energy transitions (tentatively) detected for [34] SO 2
and [33] SO 2 .

In Fig. 8 we plot zeroth moment maps of the most clearly detected
SO 2 lines. In total, five lines of SO 2 were detected, one of which we
do not plot because it is blended with a line of KCl, and four lines
of [34] SO 2 were detected, two of which are bright enough to plot in
Fig. 8. We tentatively detected one [33] SO 2 line, which we do not plot
because the emission is too faint in the zeroth moment map (but is
tentatively detected in the spectrum). The two plotted Band 3 lines
of SO 2 and [34] SO 2 coincidentally have the lowest level energies with
_𝐸_ low _<_ 10 K. The lines are resolved and show some internal structure
in the zeroth moment maps, with visible emission peaks offset from
the continuum peak. We find that the Band 3 emission extends out

_The salty emission of OH 30.1_ − _0.7_ 9



1.5


1.0


0.5


0.0


0.5


1.0




|Col1|Col2|Col3|
|---|---|---|
|30SiS, v = 0<br>J = 14-13|30SiS, v = 0<br>J = 14-13|SiS, v = 0<br>J = 14-13|
|1|1<br>0|1<br>0|



1.5


1.0


0.5


0.0


0.5


1.0


1.5







0.8


0.6


0.4


0.2


0.0


0.8


0.6


0.4


0.2


0.0



1.0


0.5


0.0


0.5


1.0



0.04


0.02


0.00


0.02


0.06


0.04


0.02


0.00







1.0


0.5


0.0


0.5


1.0



1.5

1 0 1



1.5



1.5

1 0 1



1.5


1.0


0.5


0.0


0.5


1.0



|Si3 J4 =S, 1v = 0<br>3 -1 2|Col2|Col3|3 J4 =S, 1v = 0<br>3 -1 2|
|---|---|---|---|
|||||


1 0 1

RA offset [arcsec]



|Si3 J4 =S, 1v = 1<br>4 -1 3|Col2|Si3 J4 =S, 1v = 1<br>4 -1 3|Col4|
|---|---|---|---|
|Si34S, v = 1<br>J = 14-13||||


1 0 1

RA offset [arcsec]





0.6


0.4


0.2


0.0


0.06


0.04


0.02


0.00


0.04


0.03


0.02


0.01


0.00


0.01



1.5


1.0


0.5


0.0


0.5


1.0


1.5



1.5

|30S i =S, 1v = 1<br>J 4 -1 3|Col2|Col3|
|---|---|---|
||||



1 0 1



1.5


1.0


0.5


0.0


0.5


1.0





1.5

|29Si3 J4 =S, 1v = 0<br>4 -1 3|Col2|Col3|
|---|---|---|
||||



1 0 1

RA offset [arcsec]


**Figure 5.** Zeroth moment maps of SiS towards OH 30.1 −0.7. The details of the transitions are given in Table A3. The transitions are indicated in the top right
of each panel with the details of the transitions given in Table A3. The contours are drawn at levels of 3, 5, 10 and 30 _𝜎_ . The beam is shown as a white ellipse in
the bottom left corner and the location of the continuum peak is indicated by the red cross. North is up and east is left.



3


2


1


0


1


2



0.20


0.15


0.10


0.05


0.00





3


2 0 2

RA offset [arcsec]


**Figure 6.** Zeroth moment map of CS towards OH 30.1 −0.7. The details of
the transition are given in Table A3. The contours are drawn at levels of 3, 5,
10 and 30 _𝜎_ . The beam is shown as a white ellipse in the bottom left corner
and the location of the continuum peak is indicated by the red cross. North is
up and east is left.



to a minimum of 1.5 [′′] and a maximum of 2.5 [′′] from the continuum

peak for the SO 2 line (measured after binning the 3 _𝜎_ contours, as
described for CS), and out to a minimum of 1.7 [′′] and a maximum of
2.2 [′′] for the [34] SO 2 line. The slight difference between these extents
and between the corresponding flux distribution patterns shown in
Fig. 8 are most likely a result of different sensitivities and the slightly
different gas temperatures being probed by the lines. The Band 6
observations of SO 2 show well-resolved emission and cover slightly
higher energy lines (40–108 K for SO 2 and 8–82 K for [34] SO 2 ).
The _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 14 0 _,_ 14 − 13 1 _,_ 13 line is the brightest covered line
( _𝐸_ low = 82 K) and exhibits well-resolved extended emission. As can
be seen in the channel maps plotted in Fig. A7, the emission peak
lies to the northwest of the continuum peak in most channels. The
smoothed 3 _𝜎_ contour in the zeroth moment map (Fig. 8) extends
out to 1.1–2.1 [′′], comparable to the Band 3 emission. The _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ =
10 3 _,_ 7 − 10 2 _,_ 8 ( _𝐸_ low = 61 K) has a very similar distribution, including
the offset emission peak, and a slightly smaller extent for the 3 _𝜎_
contour, ranging from 0.7–1.9 [′′] . This difference most likely arises
because the full (outer) extent of the weaker line is below the noise.


MNRAS **000**, 1–29 (2023)

10 _Danilovich et al_


2


4


6


8



|Detectedlin<br>Undetected|Col2|Col3|Band6<br>Band3|Col5|
|---|---|---|---|---|
|Detected lin<br>Undetected|Detected lin<br>Undetected||Band 6<br>Band 3||
|Detected lin<br>Undetected|Detected lin<br>Undetected||Band 6<br>Band 3||
|Detected lin<br>Undetected|Detected lin<br>Undetected||Band 6<br>Band 3||
|Detected lin<br>Undetected|Detected lin<br>Undetected||Band 6<br>Band 3||
|Detected lin<br>Undetected|Detecte n<br>Undetected|es<br> lines|Ban 6<br>Band 3||


0 200 400



2


4


6


8


10



10



0 200 400



Lower level energy [K]


**Figure 7.** The predicted relative integrated intensities for the SO 2 lines covered by our observations with lower level energies _<_ 500 K. The detected
lines are shown as blue squares and the other covered lines as orange circles.
Filled markers are lines that were covered in Band 6 and unfilled markers in
Band 3. On the left we show the predictions for a gas temperature of 25 K
and on the right we show the same for a gas temperature of 300 K.


The highest-energy detected line is _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 14 3 _,_ 11 − 14 2 _,_ 12 with
_𝐸_ low = 108 K. The emission peak of this line is also offset slightly
to the northwest. As can be seen in Fig. 8, it has the smallest extent
of the well-detected SO 2 lines, out to only 0.4–0.8 [′′] . This could be
a result of observational sensitivity and the line being intrinsically
fainter, or could be an indication that the slightly warmer emission
is not distributed as widely as for the lower-energy lines. Given our
low estimate for the SO 2 gas temperature, the former explanation is
more likely.
We also note that the central velocities found for the sufficiently
bright SO 2 lines (see Table A3) tend to fall on the blue side of
the average systemic LSR velocity by 1–2 km s [−][1] for SO 2, and by
0.4 km s [−][1] for [34] SO 2 . The two brightest Band 6 SO 2 lines are the
most blueshifted. We do not calculate isotopic ratios here because we
do not clearly detect any two pairs of lines with the same quantum
numbers across isotopologues.


**3.5** **NS**


NS was only covered by the less sensitive Band 3 observations.
Two lines in the [2] Π 1/2 ladder were covered, though only the _𝑒_ line
was clearly detected. Spectra for both lines are shown in Fig. 9
with the hyperfine components marked. In Table A3 we list the
three brightest hyperfine components for each line. For the _𝑓_ line,
the brightest hyperfine component is separated from the next two
brightest components by 38 and 41 km s [−][1], further than the halfwidth of single-component lines towards this star. Whereas for the
_𝑒_ line, the brightest hyperfine component is only 7.5 and 24 km s [−][1]

from the next two brightest components. The overlap of the two
brightest components means that their fluxes combine to make the
_𝑒_ line more detectable. We plot a theoretical Gaussian profile with
the spectra (red dotted line in Fig. 9, assuming Gaussian components
with widths of 5 km s [−][1] ) to emphasise the theoretical line shapes.
The observed _𝑒_ component has a more double-peaked profile than the
predicted Gaussian profile, suggesting that emission might originate


MNRAS **000**, 1–29 (2023)



in a shell around the star, rather than in a spherical region centred on
the star.

The zeroth moment map in Fig. 9 shows that the NS emission is
mostly located to the east and north of OH 30.1 −0.7, and is only
marginally spatially resolved. The emission is highly asymmetric;
the averaged 3 _𝜎_ contour of the emission extends out to only 0.7 [′′] to
the south-southwest and out to 1.8 [′′] to the east-northeast. The major
axis of the emitting region lies perpendicular to the projected axis
joining the AGB continuum peak and feature B. This is emphasised
by overplotting two dotted lines on the zeroth moment map in Fig. 9.
Although the signal to noise of the NS emission is rather low in
individual channels (summing to a 5 _𝜎_ detection in the zeroth moment
map), we constructed a position-velocity diagram along the major
axis (69 [◦] east of north, as illustrated in Fig. 9), which shows emission
offset from the continuum peak by around ∼ 1 _._ 5 to 2 [′′] and ∼ 5 km s [−][1]

(see Fig. A8). The potential astrochemical implications of the NS
distribution will be discussed in Sect. 4.1.1.


**3.6** **NaCl and KCl**


We detect several lines of NaCl and KCl, including lines from the
35 Cl and 37 Cl isotopologues of both species. We detect lines up to the
third and fourth vibrationally excited states of Na [35] Cl and up to the
third vibrationally excited state of K [35] Cl. These data represent the
first detections of highly excited vibrational states of both NaCl and
KCl towards AGB stars. Zeroth moment maps of NaCl are given in
Fig. 10, and of KCl in Fig. 11. The emitting regions of both molecules
are generally featureless and uniform, even for the lower-energy lines
which are spatially resolved.
No lines of Na [35] Cl in the ground vibrational state were covered by
our observations. However, we clearly detect three lines of Na [37] Cl in
the ground vibrational state. All lines of both isotopologues covered
in Band 6 were detected up to 𝑣= 4. Owing to the lower sensitivity
of the Band 3 data, only one Na [35] Cl line in the first vibrationally
excited state was detected.
The 𝑣= 0 _,_ _𝐽_ = 8 − 7 line of Na [37] Cl is appears to be marginally
spatially resolved, with the 3 _𝜎_ contour extended out to 1–1.6 [′′] from
the continuum peak. This is likely an over-estimate of the emission
extent owing to the larger beam for the Band 3 observations compared
with the Band 6 observations. We note that the _𝐽_ = 9 − 8 line appears
slightly smaller, despite the line being a little brighter, but this is
almost certainly a sensitivity effect since the line lies in a slightly
noisier part of the spectrum. Most of the NaCl lines covered in Band
6 appear to be more spatially resolved than the Band 3 lines (with
the exception of the 𝑣= 4 line). However, we note that even the two
brightest lines, the Na [37] Cl 𝑣= 0 _,_ _𝐽_ = 18 − 17 and 𝑣= 1 _,_ _𝐽_ = 19 − 18
lines, which appear several times larger than the beam, still have a
slightly oblong shape along the same axis as the beam, suggesting
that they are not truly resolved. The smoothed 3 _𝜎_ contour for the
Na [37] Cl 𝑣= 0 _,_ _𝐽_ = 18 − 17 line (the only ground vibrational state
line observed in Band 6) extends out to 0.3–0.6 [′′] .
Our Band 3 data were only sensitive enough to detect the single
covered [39] K [35] Cl line in the ground vibrational state, which is partly
blended with CO, and none of the lines in higher vibrational states.
In the Band 6 data, we detect all covered lines in the ground, first and
second vibrational states of [39] K [35] Cl and [39] K [37] Cl. We detect two
lines of [41] K [35] Cl in the second vibrationally excited state, one tentatively, and we note that no lines in the ground or first vibrationally
excited state were covered in the Band 6 observations.

As can be seen in Fig. 11, the KCl lines are not spatially resolved.
Similar to the observed NaCl emission, the two KCl lines in the
ground vibrational state appear larger than the beam but are still

_The salty emission of OH 30.1_ − _0.7_ 11



0.25


0.20


0.15


0.10


0.05



7.5


5.0


2.5


0.0


2.5


5.0


7.5


4


2


0


2


4



|SO2<br>JKa, Kc = 22, 0 31, 3|Col2|SO2<br>JKa, Kc = 22, 0 31, 3|Col4|Col5|
|---|---|---|---|---|
||||||


5 0 5

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|SO2<br>JKa, Kc = 140, 14<br>131, 13|SO2<br>JKa, Kc = 140, 14<br>131, 13|SO2<br>JKa, Kc = 140, 14<br>131, 13|SO2<br>JKa, Kc = 140, 14<br>131, 13|||
|||||||



4 2 0 2 4

RA offset [arcsec]



4


2


0


2


4

4 2 0 2 4


4


2


0


2


4


4 2 0 2 4

RA offset [arcsec]



0.06


0.04


0.02


0.00


0.02


0.4


0.3


0.2


0.1


0.0



2.5


0.0


2.5


5.0


7.5


5 0 5


4


2


0


2


4


4 2 0 2 4

RA offset [arcsec]



0.08


0.06


0.04


0.02


0.00


0.02


0.04


0.10


0.05


0.00


0.05



0.00


0.04


0.02



0.00


0.02


0.04



**Figure 8.** Zeroth moment maps of SO 2 towards OH 30.1 −0.7. The top left and centre lines were observed with ALMA band 3 and the remaining lines were
observed with ALMA band 6. Note the different angular scales and resolutions for the two sets of observations. The transitions are indicated in the top right of
each panel with the details of the transitions given in Table A3. The contours are drawn at levels of 3, 5, 10 and 30 _𝜎_ . The beam is shown as a white ellipse in
the bottom left corner and the location of the continuum peak is indicated by the red cross. North is up and east is left.


|Col1|Col2|Col3|2|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|2<br>0<br>2<br>4||N<br>J|S,<br>1/2, e<br> = 5/2-3/2|||0<br>0<br>0|
|2<br>0<br>2<br>4||N<br>J|||||













4



4 2 0 2 4

RA offset [arcsec]



0.10


0.05


0.00


0.05





**Figure 9.** NS emission towards OH 30.1 −0.7. The details of the transitions are given in Table A3. **Left:** Zeroth moment map of _𝑒_ component of NS towards
OH 30.1 −0.7. The contours are drawn at levels of 3 and 5 _𝜎_ . The pink dotted lines are drawn such that one connects the AGB continuum peak (red cross) with
the peak of feature B (not shown) and the second line is perpendicular to this, passing through the AGB continuum peak. The beam is shown as a white ellipse
in the bottom left corner. North is up and east is left. **Right:** Spectra extracted from centred circular apertures with radii of 2 [′′] for NS lines observed towards
OH 30.1 −0.7. The positions of the hyperfine components are shown as vertical red lines with heights corresponding to their relative intensities. The dotted red
lines show the predicted line profiles for Gaussian hyperfine components of width 5 km s [−][1] . The velocities are calculated with respect to the brightest hyperfine

component.



slightly elongated along the same axis as the beam. The 3 _𝜎_ contours
for both lines extend out to 0.2–0.5 [′′] from the continuum peak.


The significance of detecting so many (high-energy) lines of NaCl
and KCl are discussed in Sect. 4.1.2, as are the potential chemical formation pathways. Based on the data presented here, we constructed population diagrams for Na [35] Cl and K [35] Cl. The resultant
plot is given in Fig. A9. We derive very similar temperatures for both
species: approximately 600 K. This is consistent with the emission



originating from the inner wind, unlike the low-energy SO 2 emission
(see Sect. 3.4). We also derive column densities of 1 _._ 4 × 10 [12] cm [−][2]

for Na [35] Cl and 1 _._ 6×10 [11] cm [−][2] for K [35] Cl, resulting in Na [35] Cl/K [35] Cl
= 8.8. This is higher than expected based on chemical equilibrium
and may be an indication that the abundance ratio of Na/K is higher
than solar (in agreement with models for intermediate mass stars,
especially if OH 30.1 −0.7 had a higher initial metallicity than solar,


MNRAS **000**, 1–29 (2023)

12 _Danilovich et al_





















































































**Figure 10.** Zeroth moment maps of NaCl towards OH 30.1 −0.7. The lines in the top row were observed with ALMA Band 3 and the middle and bottom rows
were observed with ALMA Band 6. Note the different angular scales and resolutions. The details of the transitions are given in Table A3. The contours are
drawn at levels of 3, 5, 10 and 30 _𝜎_ . The beam is shown as a white ellipse in the bottom left corner and the location of the continuum peak is indicated by the
red cross. North is up and east is left.



Cinquegrana & Karakas 2022). This will be explored in more detail
in a follow up study.


**4** **DISCUSSION**



**4.1** **The circumstellar chemistry of OH 30.1** − **0.7**


Several of the molecules detected towards OH 30.1 −0.7 are com
monly seen around oxygen-rich AGB stars generally. These include
CO, SiS, and CS. In the case of oxygen-rich AGB stars, SiS, CS are
commonly seen for those with high mass-loss rates (or, equivalently,
high wind densities; Danilovich et al. 2018). SO 2 is very commonly
detected around oxygen-rich AGB stars (but has not been detected
for carbon-rich or S-type stars), with a shell-like distribution for high
mass-loss rate stars (Danilovich et al. 2020; Wallström et al. 2024).

The observations of all of these molecules towards OH 30.1 −0.7

agree with previously established trends, as explained in more detail
in Appendix C.



NS, NaCl and KCl have been observed less frequently and hence
studied in less detail thus far. It is on these three molecules that we will

focus our discussion in the following subsections. Some additional
background on past observations of these molecules is also given in
Appendix C.


_4.1.1_ _NS_


Previous observations of the NS molecule towards AGB stars include

the oxygen-rich AGB star IK Tau (Velilla Prieto et al. 2017), where
resolved ALMA observations show its emitting region to be close to
the continuum peak (within 170 au, Decin et al. 2018), and the S-type
AGB star W Aql (Danilovich et al. 2024). For W Aql, Danilovich et al.
(2024) found that NS may have been formed when the main-sequence
(F9V) companion to the AGB star passed through the dense inner
circumstellar envelope, temporarily driving UV photochemistry in
that region. This conclusion is based on the chemical models of Van
de Sande & Millar (2022), who found that the formation of NS was



MNRAS **000**, 1–29 (2023)

_The salty emission of OH 30.1_ − _0.7_ 13



1.5


1.0


0.5


0.0


0.5


1.0




|Col1|0<br>0<br>0<br>0|
|---|---|
|||


|.5 K35Cl, v = 0|K35Cl, v = 0|Col3|35Cl, v = 0|Col5|
|---|---|---|---|---|
|.5<br>.0<br>.5<br>.0<br>.5<br>.0<br>.<br>K35Cl, v = 0<br>J = 32-31|K35Cl, v = 0<br>J = 32-31|K35Cl, v = 0<br>J = 32-31|5Cl, v = 0<br>J = 32-31|5Cl, v = 0<br>J = 32-31|
|.5<br>.0<br>.5<br>.0<br>.5<br>.0<br>.<br>K35Cl, v = 0<br>J = 32-31|K35Cl, v = 0<br>J = 32-31||||


|Col1|K35 C =l, 3v = 0<br>J 0 -2 9|K35 C =l, 3v = 0<br>J 0 -2 9|
|---|---|---|
||||
||||
||||
||||
||||
|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|


|Col1|0<br>0<br>0<br>0|
|---|---|
|||


|K37 C =l, 3v = 1<br>J 1 -3 0|Col2|7 C =l, 3v = 1<br>J 1 -3 0|Col4|
|---|---|---|---|
|||||


|Col1|K35 C =l, 3v = 2<br>J 1 -3 0|K35 C =l, 3v = 2<br>J 1 -3 0|
|---|---|---|
||||
||||
||||
||||
||||
|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|



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



1.5


1.5



1.5


1.0


0.5


0.0


0.5


1.0





0.30


0.25


0.20


0.15


0.10


0.05


0.00


0.08


0.06


0.04


0.02


0.00


0.02


0.04


0.02


0.00


0.02



1 0 1


1.5



1.0


0.5


0.0


0.5


1.0



0.30


0.25


0.20


0.15


0.10


0.05


0.00


0.04


0.02


0.00


0.02


0.02


0.01


0.00


0.01


0.02


0.03



1.0


0.5


0.0


0.5


1.0


1.5



0.06


0.04


0.02


0.00


0.02


0.03


0.02


0.01


0.00


0.01







1.5



RA offset [arcsec]



1.5


1.0


0.5


0.0


0.5


1.0


1.5



|Col1|41K35 C =l, 3v = 2<br>J 1 -3 0|Col3|1K35 C =l, 3v = 2<br>J 1 -3 0|
|---|---|---|---|
|||||
|||||
|||||
|||||
|||||
|||||


1 0 1

RA offset [arcsec]



1.5

1 0 1



|41K35 C =l, 3v = 2<br>J 3 -3 2|Col2|
|---|---|
|0<br>1|1|


RA offset [arcsec]


|Col1|0<br>.<br>0<br>.<br>0<br>.|
|---|---|
|||
|||



**Figure 11.** Zeroth moment maps of KCl towards OH 30.1 −0.7. The details of the transitions are given in Table A3. The contours are drawn at levels of 3, 5, 10
and 30 _𝜎_ . The beam is shown as a white ellipse in the bottom left corner and the location of the continuum peak is indicated by the red cross. North is up and

east is left.



enhanced in the presence of UV photons from a companion star.
Although NS towards IK Tau has not been analysed in detail (only
some basic measurements are given in Decin et al. 2018), the recent
analysis of NaCl in the same star found evidence that a companion
may be driving or enhancing the formation of NaCl (Coenegrachts
et al. 2023). It is also possible that the formation of NS around IK Tau
could be driven by that companion, albeit primarily through UV
chemistry rather than the shock-heating proposed by Coenegrachts
et al. (2023) for NaCl.

The radial extent of NS in the case of OH 30.1 −0.7 is much

larger than the extents seen for IK Tau or W Aql. The integrated NS
emission towards W Aql is irregular but is detected no more than
0.4 [′′] ≈ 160 au from the star (Danilovich et al. 2024). For IK Tau,
the angular width is reported to be 490–650 mas (Decin et al. 2018),
which corresponds to radial extents of ∼ 130 to 170 au. In contrast,
for OH 30.1 −0.7 the most distant NS emission within the 3 _𝜎_ contour
is seen at 1.8 [′′] . This corresponds to 7000 au, while the southeastern
extent of 0.7 [′′] corresponds to 2700 au. These distances come with the
caveat that the Band 3 emission is only marginally resolved, so the
radial extents may be overestimated and only represent upper limits



(for example, see the difference between the Band 3 and 6 emission
extents for NaCl in Sec. 3.6). Taken at face value, this emission
appears to be 20–40 times further from the AGB star than the most
distant NS emission seen around W Aql and IK Tau. The theoretical
study of Van de Sande & Millar (2022) found that higher mass-loss
rates result in NS peaks further from AGB star and that a relatively
warm companion star is required to form NS; i.e. a solar-type or
white dwarf companion will drive NS formation but a red dwarf will

not.


The asymmetric NS emission in the zeroth moment map (Fig. 9)
is reminiscent of the SiN emission around W Aql (Danilovich et al.
2024), which was determined to lie on the side of the AGB star that
aligned with the periastron of the binary orbit. If a similar scenario
can account for the NS around OH 30.1 −0.7, then the alignment
of the NS emission can help constrain the projection of the orbital
plane on the sky. Another possibility is a companion on a circular
but wider orbit such that NS is preferentially formed on the side of
the CSE where the companion is presently located.


MNRAS **000**, 1–29 (2023)

14 _Danilovich et al_


_4.1.2_ _Chlorides_


There have been enough adequately sensitive observations of a variety of AGB stars that we can firmly say that NaCl and KCl are not
ubiquitously present in circumstellar envelopes. This is most clearly
illustrated by the detection of one or both molecules in 3 AGB stars
out of a sample of 14 in the ATOMIUM survey (Wallström et al.
2024). Some physical or chemical characteristic must set these stars
apart from their unsalted counterparts. Similarly, something should
also set stars like OH 30.1 −0.7, with a large number of NaCl and
KCl lines, apart from stars like IK Tau, with detections only in the
ground vibrational state (Velilla Prieto et al. 2017; Decin et al. 2018).

Coenegrachts et al. (2023) proposed that an unseen companion
could be contributing to the formation of NaCl around IK Tau, since
the motion of the companion through the CSE would be supersonic,
hence generating a shock. As discussed by Decin et al. (2019), and
evidenced by our detection of NS, OH 30.1 −0.7 is also thought to
have a companion. Since the OH 30.1 −0.7 shows evidence of hot
bottom burning (Justtanont et al. 2015), we can conclude it had an
intermediate initial mass, ≳ 4 M ⊙ . In this mass range, the binary
fraction is thought to be close to one or higher (that is, stars with
masses from 4–8 M ⊙ are expected to have one or more companions
with mass ratios _𝑞>_ 0 _._ 1, Moe & Di Stefano 2017). In light of
this, and the results of Coenegrachts et al. (2023), it is highly likely
that a companion is present around OH 30.1 −0.7 and that such a
companion could be driving the formation of NaCl and KCl in a
similar way. Unlike the case of IK Tau, we see many vibrationally
excited NaCl and KCl lines around OH 30.1 −0.7. This is consistent

with the different temperatures found for NaCl around the two stars:
14 to 70 K for IK Tau (Velilla Prieto et al. 2017; Coenegrachts et al.
2023) and 600 K for OH 30.1 −0.7 (see Sect. 3.6 and Fig. A9). This
may be a result of more extreme shocks owing to the higher wind
density of OH 30.1 −0.7 and possibly a higher orbital velocity of the
companion.
The formation pathways of NaCl and KCl are discussed in detail
in Appendix C5.1. We conclude that a companion star hotter than
around ∼ 12000 K would cause too much photoionisation of Na and
K to reconcile our observations, unless densities are very high in that
region of the wind. Hence, we can hypothesise that the companion
to OH 30.1 −0.7 cannot be hotter than a late B-type main sequence

star.


**4.2** **Our evolving understanding of OH 30.1** − **0.7**


OH 30.1 −0.7 has been classified as an extreme OH/IR star, which is
to say, a dusty AGB star with a high mass-loss rate and bright OH
masers (Justtanont et al. 2006). It is an example of a large-amplitude
variable star with one of the longest periods known ( _𝑃_ = 2170 days
∼ 6 years [1], Engels et al. 2024). Such stars are thought to have evolved
to the end of the AGB phase (e.g. Olofsson et al. 2022). From _Her-_
_schel_ observations of H 2 O isotopologues, OH 30.1 −0.7 was determined to have an intermediate initial mass (≳ 4 M ⊙, Justtanont
et al. 2015). This is in contrast with several other OH/IR stars which
have been found to have lower initial masses ∼ 1 _._ 5 M ⊙ (Olofsson
et al. 2022). An overview of past observational difficulties, including a discussion on the reliability of observations in light of ISM
contamination towards OH 30.1 −0.7, are given in Appendix D.


1 Obtained from its OH maser light curve: `[https://hsweb.hs.](https://hsweb.hs.uni-hamburg.de/projects/nrt_monitoring/stockert.html)`
```
uni-hamburg.de/projects/nrt_monitoring/stockert.html

```

MNRAS **000**, 1–29 (2023)



_4.2.1_ _Past results from the literature_


OH 30.1 −0.7 was included in the CO study of Heske et al. (1990),
which was the first to observe a sample of OH/IR stars in CO emission. Heske et al. (1990) found that their observed intensity ratios of
the CO _𝐽_ = 1 − 0 and _𝐽_ = 2 − 1 lines could be explained by variable mass-loss rates at different eras, which could be the reason why
mass-loss rates derived from CO observations resulted in an order

of magnitude lower mass-loss than those from dust. This idea, first
dubbed the “superwind” scenario by Renzini (1981), was taken up
and developed in subsequent work (e.g. Justtanont & Tielens 1992;
Delfosse et al. 1997; Justtanont et al. 2013). The idea, as it developed,
being that in the last portion of the AGB phase, mass loss increases
substantially (i.e. the stellar wind becomes a superwind) during a relatively short period immediately before the completion of the AGB
phase.

Decin et al. (2019) presented the ALMA CO observations of
OH 30.1 −0.7 (from the dataset also presented here, though we have
performed a new reduction of the ALMA data using self-calibration,
see Sect. 2.1) and of another extreme OH/IR star, OH 26.5 +0.6. A
key argument of Decin et al.’s (2019) work was that it is statistically
unlikely that a dozen extreme OH/IR stars should all be observed in
the midst of the relatively short superwind phase. Rather, they interpret the structures within the CO emission of OH 30.1 −0.7 (and the
spiral structure seen for OH 26.5 +0.6) as interactions with a companion star. The ultimate result of these interactions, they argue, is an
equatorial density enhancement; that is, the companion pulls some
of the wind into a toroidal structure of denser gas and dust around
the star. This equatorial density enhancement could then mimic the
superwind by making the mass-loss rate appear high because of the
line of sight alignment of this region.
Low [12] CO/ [13] CO ratios ∼ 3 _._ 5 were found by both Delfosse et al.
(1997) and Justtanont et al. (2013) for OH 30.1 −0.7, using different observational datasets and a similar approach involving radiative transfer modelling. This low [12] CO/ [13] CO ratio provides further evidence of hot bottom burning in OH 30.1 −0.7, and hence
that it must be an intermediate mass star, with an initial mass
4 M ⊙ ≲ _𝑀_ _𝑖_ ≲ 8 M ⊙ .
The recent study of Marini et al. (2023) modelled the SED of
OH 30.1 −0.7 and compared various properties such as luminosity
and pulsation period of the star to theoretical models. Based on
their results (and considering the distance derived by Engels et al.
(2015)), their determination of the initial mass of OH 30.1 −0.7 is
likely between 4 and 5 M ⊙ . However, if the luminosity is higher
(i.e. 5 × 10 [4] L ⊙ based on the luminosity adopted by Justtanont et al.
(2013), scaled to our adopted distance of 3.9 kpc) then OH 30.1 −0.7
could have an initial mass of 6 M ⊙ .


_4.2.2_ _New understanding from ALMA CO_


Our ALMA observations show that the angular extent of the CO
emission for both the _𝐽_ = 2 − 1 and _𝐽_ = 1 − 0 are essentially the same.
Our measured maximum angular extents (see Sect. 3.1) are 3 _._ 5 [′′] for
_𝐽_ = 2 − 1 from the combined data and 4 _._ 2 [′′] for _𝐽_ = 1 − 0. Although
it may appear from this that the _𝐽_ = 1 − 0 extent is larger than the
_𝐽_ = 2−1 extent, this is primarily a function of the different beam sizes
(see Table A1). If we instead compare the data from only the compact
array configuration for _𝐽_ = 2 − 1 (with a comparable beam to the
Band 3 data), then we find a maximum angular extent of 4 _._ 2 [′′], as for
the _𝐽_ = 1 − 0. This unexpected result suggests that both the emission
from CO _𝐽_ = 1 − 0 and _𝐽_ = 2 − 1 trace the outer extent of the CO

envelope. Note also that in the channel maps close to the LSR velocity

(and ignoring the regions with the most contamination) the lowest
few contours are very close together (3, 5, and 10 _𝜎_ for _𝐽_ = 1 − 0,
Fig. A6, and 5, 10, 30, and 50 _𝜎_ for _𝐽_ = 2 − 1, Fig. 3), indicating a
sharp drop-off in CO emission and likely also CO abundance. This
is also seen in the reddest and bluest channels (more clearly for CO
_𝐽_ = 2 − 1 because of higher contamination for CO _𝐽_ = 1 − 0) where
the CO emission is detected above 30 _𝜎_, then not detected in the
subsequent channel at all. This behaviour is in contrast with other
spatially resolved observations of AGB stars which typically have less
abrupt edges, with gradually decreasing emission across the velocity
and angular axes (see for example Cernicharo et al. (2015), Kim et al.
(2017) and the channel maps in the supplementary material of Decin
et al. (2020) for a selection of varied AGB stars).
If we take half the maximum velocity extent in the CO channel maps as the wind speed (23 km s [−][1] ) and consider the wellconstrained distance of 3.9 kpc, we find that it took around 2800
years for the gas to expand to 3 _._ 5 [′′] (2 × 10 [17] cm = 14000 au) from
the star. This is around a factor of 3 longer than the superwind phase
obtained for this star by Delfosse et al. (1997) and a factor of 8
larger than the superwind radius derived by Justtanont et al. (2013).
We also do not detect any significant emission beyond this radius,
aside from the background contamination, which is not evenly distributed around the star. In conjunction with the sharp drop-off in
CO emission discussed above, this suggests that any earlier massloss must have been at a much lower rate, if it was present at all. If we
consider the photodissociation radius of CO based on the mass-loss
rate, expansion velocity and interstellar radiation field, and take the
measured envelope size to be the half-abundance radius for CO destruction, then the mass-loss corresponding to the observed envelope
size is _𝑀_ [�] ≈ 2 × 10 [−][5] M ⊙ yr [−][1] (Mamon et al. 1988; Saberi et al.
2019). Essentially, any earlier mass-loss at this rate or lower would
not be detectable, because that CO would have photodissociated before expanding to larger radii. So if there was a lower mass-loss rate
(≤ 2 × 10 [−][5] M ⊙ yr [−][1] ) before the current high mass-loss rate period
commenced 2800 years ago, it would not be detectable.
If we take the mass-loss rate of _𝑀_ [�] = 1 _._ 8 × 10 [−][4] M ⊙ yr [−][1] computed by Justtanont et al. (2013), and assume it has not changed over
the past 2800 years, we calculate that 0 _._ 5 M ⊙ has been ejected
by� the star in this time. If we instead use a lower rate such as
_𝑀_ = 2 × 10 [−][5] M ⊙ yr [−][1], close to the value found by Heske et al.
(1990) and in agreement with the findings of Decin et al. (2019),
we correspondingly find less mass ejected in that time frame: only
0 _._ 06 M ⊙ . Clearly the mass-loss rate will significantly affect the
longevity of this object. A further analysis of the CO properties
of OH 30.1 −0.7 would require a detailed radiative transfer analysis
and is beyond the scope of the present work, but will be the subject
of a follow-up paper.


_4.2.3_ _Evidence from other molecular species_


As discussed in Sect. 4.1, the circumstellar chemistry of
OH 30.1 −0.7, especially the detection of NS, strongly suggests the
presence of a companion star emitting UV in the inner wind. However, while the companion star should emit enough UV to facilitate
the formation of NS through the photodissociation of N 2 (it should
not be a red dwarf), the companion should not be too hot ( _<_ 12000 K)
to avoid photoionising Na and K and inhibiting the formation of NaCl
and KCl. Hence, the companion ought not to be a massive star and is
likely to be a late B- to G-type star. This would put a companion in
the mass range of ∼ 1 to 4 M ⊙, which also fulfils the criteria of being
less massive than the AGB star, since the AGB star has evolved off
the main sequence first.



_The salty emission of OH 30.1_ − _0.7_ 15


Based on the temperature we calculated for the SO 2 lines (see
Fig. 7 and Sect. 3.4), we can make an estimate of the average radial
temperature profile of the circumstellar envelope. For this we take the
SO 2 temperature to be 25 K and the average outer radius of SO 2 to be
1 × 10 [17] cm (corresponding to ∼ 1 _._ 7 [′′], close to the average maximal
extent of the SO 2 observations, see Fig. 8, and in good agreement
with the radius of the outer SO 2 shell visible in Fig. A7). We take
the inner temperature to be 2000 K close to the surface of the star
(at 1 _._ 3 × 10 [14] cm). Assuming a power law radial temperature profile,
_𝑇_ ( _𝑟_ ) = _𝑇_ _★_ ( _𝑟_ / _𝑅_ _★_ ) [−] _[𝜖]_, we then calculate the exponent, _𝜖_ = 0 _._ 66. This
is very close to the values found for lower mass-loss rate oxygenrich AGB stars such as R Dor (0.65, Van de Sande et al. 2018) and
W Hya (0.65, Khouri et al. 2014). If we try to include the average
NaCl and KCl temperature (600 K, Fig. A9) at the apparent size of
the emitting region, we find an implausibly high value of _𝜖_ = 2 _._ 4.
This is most likely because the NaCl and KCl lines are not spatially
resolved in our observations, as noted in Sect. 3.6. If we instead use
the estimated radial temperature profile with _𝜖_ = 0 _._ 66 to calculate
the average radius of the salt extents, we find _𝑅_ salt = 8 × 10 [14] cm,
which corresponds to ∼ 0 _._ 014 [′′] (and ∼ 50 au), much smaller than
our restoring beams (Table A1).
The companion is most likely driving the formation of the salt
molecules. Hence, the above indicates that the separation between
the AGB star and the likely main sequence companion is significantly smaller than our minimum resolution of ∼ 0 _._ 3 [′′] = 1200 au
≈ 2 × 10 [16] cm. From our estimate of the average salt extent, we
predict that observations with an angular resolution of 5 mas or better are required to resolve the structures in the inner wind. Further
observations targeting molecular tracers of UV-emitting companions
such as NS and SiN (Van de Sande & Millar 2022), will help us to
understand the nature and orbit of such a companion.
Finally, we note that as well as affecting the circumstellar chemistry and gravitationally shaping the wind, a companion may also
contribute to dust formation. Even wide binary companions (with
semimajor axes on the order of hundreds of au) are essentially guaranteed to have orbital velocities in excess of the local sound speed,
resulting in additional shocks in the wind. Freytag & Höfner (2023)
found, in the context of stellar pulsations, that dust forms in the wake
of shocks. Some evidence for this was seen by Coenegrachts et al.
(2023) who found that an asymmetric dust distribution in the inner
CSE of IK Tau correlated with a clumpy spiral of NaCl emission that
may have formed partly as a result of shocks and other interactions
with an unseen binary companion. Indeed, a more extreme version
of companion-enhanced dust formation has long been known to take
place for Wolf-Rayet stars, where dust forms at the nexus of colliding
winds from massive stars (Usov 1991). The lack of prior direct detection of such a companion is not evidence of its absence, since the
optically thick circumstellar dust would very strongly attenuate the
signal at optical wavelengths (e.g. see the strong silicate absorption
in Fig. 1 of Justtanont et al. 2013).


**4.3** **On the nature of feature “B”**


Feature B is detected in the continuum and lies 4 _._ 6 [′′] north and

slightly west of the primary continuum peak. The lower limit on the
separation is 1 _._ 8 × 10 [4] au. We extracted spectra around this peak,
using a circular aperture with a radius of 0 _._ 3 [′′], and did not detect any
line emission above the noise aside from CO. As shown in our channel

maps (Figs. 3 and A5), this emission is most likely dominated by
contamination from the background molecular cloud associated with
W43. Inspecting the channel maps, there are no localised features in
the CO emission associated with the position of feature B. As can


MNRAS **000**, 1–29 (2023)

16 _Danilovich et al_


be clearly seen in the channel maps and in the integrated intensity
(zeroth moment) map in Fig. 4, feature B lies beyond any of the
molecular emission associated with the AGB star. The size of feature
B, when considering the 5 _𝜎_ contours, is approximately 0 _._ 8 × 0 _._ 5 [′′] .
In Sect. 2.2.2 we calculated the spectral indices of both the primary continuum peak and feature B. The spectral index of the primary peak, 2 _._ 8 ± 0 _._ 3 is in general agreement with past results for
OH 30.1 −0.7. For example Nicolaes et al. (2018) found spectral
indices ranging from 2.13 at shorter (far-IR) wavelengths to 3.42
at long wavelengths, based on _Herschel_ /PACS and _Herschel_ /SPIRE
observations. The lower limit of 3.6 for feature B is very high compared with commonly found spectral indices (see for example Juvela
et al. 2015, who find values around 1–2 for cold cores). Nicolaes
et al. (2018) found some comparably steep slopes for other evolved
stars in their sample, notably at longer wavelengths ( _>_ 100 _𝜇_ m) and
for stars classed as OH/IR stars, similar to OH 30.1 −0.7. When it
comes to dust sources not associated with evolved stars, Kuan et al.
(1996) found very steep spectral indices (up to 4.6) for Sagittarius
B2(N). They conclude that this is most likely a result of a cold dust
temperature and ice-coated grains and that Sgr B2(N) is a young
object in an early stage of star formation. Whether our feature B is
a similar background source to Sgr B2(N) or more closely associated with OH 30.1 −0.7, cold ice-coated dust grains are a feasible
explanation for the spectral index. Given that Justtanont et al. (2006)
found evidence of H 2 O ice in the dust around OH 30.1 −0.7, the high
spectral index of feature B could indicate a similar dust composition
(i.e. ice-coated grains) but at a lower temperature since the feature
is located further from the AGB star with much of the stellar light
obscured by the circumstellar dust.


_4.3.1_ _A direct association with OH 30.1_ − _0.7?_


If we draw a line connecting the primary continuum peak and feature
B, we find it lies 20 _._ 5 [◦] west of north (clockwise on the observed
maps in Fig. 1). The CO emission appears mostly round in shape
(Fig. 3), however, there is a slight indentation in the direction of feature B. The centre of the indentation sits about 2.4 [′′] from the primary
continuum peak whereas on the opposite side the 5 _𝜎_ contour of the
CO emission extends to around 3.1 [′′] from the primary continuum
peak. This alignment could be coincidental, but it is also possible
that feature B is contributing to the shaping of the CO emission
or was formed through the same interaction as the CO indentation.
This would imply that feature B is an object at the same distance as
OH 30.1 −0.7. Given the large separation between the CO indentation
and feature B (around 2.2 [′′] ), it is unlikely that the source of feature
B is (at present) contributing to significant gravitational shaping of
the AGB circumstellar environment. Decin et al. (2019) suggested
that the indentation in the CO was a knot caused by a companion and
its density wake. Another possibility is that feature B is causing the
indentation through non-gravitational means, perhaps through high
energy UV photons, although this is difficult to reconcile with the
cold dust implied by the spectral index.
A recent study of the S-type AGB star, W Aql, found that the
F-type main sequence companion, located around 200 au from the
AGB star, contributed to the enhanced photodissociation of several
molecular species, including SiO, SiS, CS and HCN. The channels
exhibiting such photodissociation bear some resemblance to the CO
towards OH 30.1 −0.7, although the CO indentation is less extreme.
At 6000 K, the companion to W Aql did not produce enough energetic
UV photons to significantly photodissociate CO. However, a hotter
stellar companion could potentially affect the CO distribution. For
example, when analysing the impact of increasing the interstellar


MNRAS **000**, 1–29 (2023)



radiation field on the size of the CO envelopes of AGB stars, Saberi
et al. (2019) found that, for stars with similar mass-loss rates and
velocities to OH 30.1 −0.7, doubling the strength of the interstellar
radiation field reduced the size of the CO envelope by 14–20%. High
mass-loss rates result in smaller effects because of CO self-shielding.
For example, Van de Sande & Millar (2022) found that including a
hot 80,000 K (white dwarf) inner companion in their model did not
significantly impact the CO distribution for higher mass-loss rates.
If feature B is a hot star, it could act as a localised increase in the
UV radiation field. Counter to this and unlike a companion located
within the dust envelope of OH 30.1 −0.7, it is unclear why such a
UV source would be too attenuated to be detected from Earth but

not too attenuated to affect the OH 30.1 −0.7 CO envelope. Or why
such a hot source would not destroy ice-covered dust grains. We also
note that if feature B does correspond to a companion, this would not
negate the potential presence of a closer companion that does shape
the wind, even though feature B is too distant to be such a companion
itself.

A more likely possibility is that feature B is a clump of dust
(and perhaps undetected gas) that was ejected from OH 30.1 −0.7
itself, perhaps as a pre-cursor to the present-day mass loss (beginning
2800 years ago, according to the CO extent) or owing to a complex
binary interaction. The fact that the extent of the NS emission lies
perpendicular to the projected separation between the AGB star and
feature B lends some weight to this scenario. If feature B were ejected
with the same velocity as the observed CO envelope, that would
suggest an ejection around 3700 years ago. However, if the ejection
took place at the same time that mass loss was initiated, that would
imply a velocity of 30 km s [−][1], which is not implausibly high. If
feature B is rather a high velocity bullet, such as those seen for the
carbon star V Hya (which has a relatively close companion on an
eccentric orbit, Sahai et al. 2016), then feature B could have been
ejected more recently at a higher velocity. In both of these cases
we are assuming that feature B was moving in the plane of the sky,
making our time and distance estimates lower limits. An ejection
scenario could, however, account for the apparent bridge between
the primary continuum peak and feature B, if some ejecta were not
accelerated as strongly.


_4.3.2_ _A background source?_


It is possible that feature B is a coincident background (or foreground) source. Given the line of sight proximity of OH 30.1 −0.7
to the star-forming region W43, that is the most likely origin of
background sources. The distance to W43 has been determined to
be 5 _._ 5 ± 0 _._ 3 kpc (Zhang et al. 2014), significantly further than the
3.9 kpc to OH 30.1 −0.7 (Engels et al. 2015). At the distance of W43,
the extent of feature B would correspond to around 2800–4400 au.
Placing it at the distance of OH 30.1 −0.7 gives an extent of around
2000–3000 au. Both of these sizes are upper limits as they are not
significantly larger than the beam size.


**5** **CONCLUSIONS**


We present newly reduced ALMA observations of the intermediatemass AGB star OH 30.1 −0.7, including continuum and line emission. In the continuum maps, we identified a secondary peak (feature
B), detected with a certainty of _>_ 10 _𝜎_, and we speculate that it is most
likely ejecta associated with the AGB star, but may be a background
source or a companion object. With a high lower limit for its spectral
index, feature B is likely composed of cold dust with ice covering the

dust grains. We do not conclusively find any molecular emission associated with the feature, aside from some weak CO emission which
may originate from background contamination rather than from that

source.

We identified all the molecular emission present in the ALMA
maps and spectra, finding rotational transitions arising from CO, SiS,
CS, SO 2, NS, NaCl, and KCl. In addition to transitions in the ground
vibrational state, we find several rotational transitions in vibrationally
excited states from SiS (up to 𝑣= 1), NaCl (up to 𝑣= 4) and KCl (up
to 𝑣= 2). Based on a simplified molecular line excitation analysis, we
estimate the radial temperature profile as a power law with a similar
index to other oxygen-rich AGB stars.
We interpret the presence of NS as indicative of a UV-emitting
main sequence companion in the inner regions of the OH 30.1 −0.7
wind, with a separation smaller than our resolution limit of ∼ 1200 au.
The distribution of the NS emission suggests an eccentric binary
orbit with an orbital plane that may be perpendicular to the direction
of feature B. While the presence of NS suggests a UV emitting
companion, the presence of NaCl and KCl require that the companion
not be too hot. From this we determine that the companion cannot be
hotter than a late B-type main sequence star, but may be as cool as
a G-type star, and that a red dwarf star would not be able to trigger
adequate NS formation.
Past observations and studies of OH 30.1 −0.7 have indicated optically thick dust and CO emission — which our observations support
— and have suggested that the AGB star may have entered a superwind phase at the tail end of the AGB. Our observations reveal a very
steep drop off at the edges of the CO emission, both in the plane of
the sky and in velocity space. This suggests that the bounds of the
CO envelope are not truncated by the interstellar radiation field, as is
usually the case. Instead it seems that the observed CO corresponds
to a period of high mass loss beginning around 2800 years ago. This
is a longer period than predicted by the superwind scenario, and a
detailed explanation is deferred to a later study. We also conclude
that _𝑀_ � ≤any2 ×earlier 10 [−][5] periodM ⊙ yr [−] of [1] ) lowerwouldmassnot belossdetectable(with a mass-lossin light ofratethe
recent high mass loss. We suggest companion-enhanced dust production, leading to a higher mass-loss rate, as a possible explanation
for the current high mass-loss rate.
Additional higher angular resolution observations are required to
fully understand OH 30.1 −0.7 and its high mass loss and dense wind.
In particular, we recommend observations with angular resolution of
5 mas or better to resolve possible companion interactions in the
inner wind.


**ACKNOWLEDGEMENTS**


The authors thank Elvire De Beck for sharing the original data from
her 2010 paper (De Beck et al. 2010). TD is supported in part by
the Australian Research Council through a Discovery Early Career
Researcher Award (DE230100183). This research is supported in
part by the Australian Research Council Centre of Excellence for
All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project
number CE170100013. MVdS acknowledges the Oort Fellowship at
Leiden Observatory. TJM’s research at QUB is supported by grant
number ST/T000198/1 from the STFC. HSPM thanks the Deutsche

Forschungsgemeinschaft (DFG) for support through the collaborative research center SFB 1601 (project ID 500700252) subprojects
A4 and Inf. KJ acknowledges the support from the Swedish National Space Agency (SNSA). JMCP was supported by STFC grant
number ST/T000287/1. SHJW acknowledges support from the Re


_The salty emission of OH 30.1_ − _0.7_ 17


search Foundation Flanders (FWO) through grant 1285221N. LD
acknowledges support from the KU Leuven C1 MAESTRO grant
C16/17/007, the FWO research grant G099720N, and the KU Leuven C1 BRAVE grant C16/23/009. This paper makes use of the
following ALMA data: ADS/JAO.ALMA#2016.1.00005.S. ALMA
is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ. We acknowledge excellent support
from the UK ALMA Regional Centre (UK ARC), which is hosted
by the Jodrell Bank Centre for Astrophysics (JBCA) at the University of Manchester. The UK ARC Node is supported by STFC Grant
ST/P000827/1. Based on observations with the Atacama Pathfinder
EXperiment (APEX) telescope with project ID: O-0102.F-9301B.
APEX is a collaboration between the Max Planck Institute for Ra
dio Astronomy, the European Southern Observatory, and the Onsala
Space Observatory. Swedish observations on APEX are supported
through Swedish Research Council grant No 2017-00648. This research made use of Astropy (Astropy Collaboration et al. 2013, 2018),
SciPy (Virtanen et al. 2020), Matplotlib (Hunter 2007) and NumPy
(Harris et al. 2020).


**DATA AVAILABILITY**


The observational data used here are openly available through the
data archives for ALMA ( `[https://almascience.nrao.edu/aq/](https://almascience.nrao.edu/aq/)` )
and ESO for the APEX data ( `[http://archive.eso.org](http://archive.eso.org)` ). Custom
ALMA data products that were produced for this study are available
from TD or AMSR upon reasonable request.


**REFERENCES**


Agúndez M., Fonfría J. P., Cernicharo J., Kahane C., Daniel F., Guélin M.,
[2012, A&A, 543, A48](http://dx.doi.org/10.1051/0004-6361/201218963)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
[Baudry A., et al., 2023, A&A, 674, A125](http://dx.doi.org/10.1051/0004-6361/202245193)
Belov S. P., Tretyakov M. Y., Kozin I. N., Klisch E., Winnewisser G., Lafferty
[W. J., Flaud J. M., 1998, J. Mol. Spectrosc., 191, 17](http://dx.doi.org/10.1006/jmsp.1998.7576)
Briggs D. S., Schwab F. R., Sramek R. A., 1999, in Taylor G. B., Carilli C. L.,
Perley R. A., eds, Astronomical Society of the Pacific Conference Series
Vol. 180, Synthesis Imaging in Radio Astronomy II. p. 127
Caris M., Lewen F., Winnewisser G., 2002, Zeitschrift [Naturforschung](http://dx.doi.org/10.1515/zna-2002-0805) Teil
[A, 57, 663](http://dx.doi.org/10.1515/zna-2002-0805)

[Caris M., Lewen F., Müller H. S. P., Winnewisser G., 2004, Journal of Molec-](http://dx.doi.org/10.1016/j.molstruc.2003.11.010)

[ular Structure, 695, 243](http://dx.doi.org/10.1016/j.molstruc.2003.11.010)

[Cernicharo J., Guelin M., 1987, A&A, 183, L10](https://ui.adsabs.harvard.edu/abs/1987A&A...183L..10C)
[Cernicharo J., Marcelino N., Agúndez M., Guélin M., 2015, A&A, 575, A91](http://dx.doi.org/10.1051/0004-6361/201424565)
[Cherchneff I., 2012, A&A, 545, A12](http://dx.doi.org/10.1051/0004-6361/201118542)
[Cinquegrana G. C., Karakas A. I., 2022, MNRAS, 510, 1557](http://dx.doi.org/10.1093/mnras/stab3379)
[Coenegrachts A., Danilovich T., De Ceuster F., Decin L., 2023, A&A, 678,](http://dx.doi.org/10.1051/0004-6361/202346116)
[A85](https://ui.adsabs.harvard.edu/abs/2023A&A...678A..85C)

[Condon J. J., 1997, PASP, 109, 166](http://dx.doi.org/10.1086/133871)
Cortes P., et al., 2023, ALMA Cycle 10 Technical Handbook,
[doi:10.5281/zenodo.7822943.](http://dx.doi.org/10.5281/zenodo.7822943. )

Cutri R. M., et al., 2012, Explanatory Supplement to the WISE All-Sky Data
Release Products, Explanatory Supplement to the WISE All-Sky Data

Release Products

Danilovich T., De Beck E., Black J. H., Olofsson H., Justtanont K., 2016,


[A&A, 588, A119](http://dx.doi.org/10.1051/0004-6361/201527943)

Danilovich T., Lombaert R., Decin L., Karakas A., Maercker M., Olofsson

[H., 2017a, A&A, 602, A14](http://dx.doi.org/10.1051/0004-6361/201630055)


MNRAS **000**, 1–29 (2023)

18 _Danilovich et al_


Danilovich T., Van de Sande M., De Beck E., Decin L., Olofsson H., Ramstedt

[S., Millar T. J., 2017b, A&A, 606, A124](http://dx.doi.org/10.1051/0004-6361/201731203)

Danilovich T., Ramstedt S., Gobrecht D., Decin L., De Beck E., Olofsson H.,

[2018, A&A, 617, A132](http://dx.doi.org/10.1051/0004-6361/201833317)

Danilovich T., Richards A. M. S., Karakas A. I., Van de Sande M., Decin L.,

[De Ceuster F., 2019, MNRAS, 484, 494](http://dx.doi.org/10.1093/mnras/stz002)

Danilovich T., Richards A. M. S., Decin L., Van de Sande M., Gottlieb C. A.,

[2020, MNRAS, 494, 1323](http://dx.doi.org/10.1093/mnras/staa693)

[Danilovich T., et al., 2021, A&A, 655, A80](http://dx.doi.org/10.1051/0004-6361/202141757)
[Danilovich T., et al., 2024, Nature Astronomy, 8, 308](http://dx.doi.org/10.1038/s41550-023-02154-y)
De Beck E., Decin L., de Koter A., Justtanont K., Verhoelst T., Kemper F.,
[Menten K. M., 2010, A&A, 523, A18](http://dx.doi.org/10.1051/0004-6361/200913771)

[Decin L., et al., 2016, A&A, 592, A76](http://dx.doi.org/10.1051/0004-6361/201527934)

Decin L., Richards A. M. S., Danilovich T., Homan W., Nuth J. A., 2018,


[A&A, 615, A28](http://dx.doi.org/10.1051/0004-6361/201732216)
[Decin L., et al., 2019, Nature Astronomy, 3, 408](http://dx.doi.org/10.1038/s41550-019-0703-5)
[Decin L., et al., 2020, Science, 369, 1497](http://dx.doi.org/10.1126/science.abb1229)

[Delfosse X., Kahane C., Forveille T., 1997, A&A, 320, 249](http://adsabs.harvard.edu/abs/1997A%26A...320..249D)
Engels D., Etoka S., Gérard E., Richards A., 2015, in Kerschbaum F., Wing
R. F., Hron J., eds, Astronomical Society of the Pacific Conference Series
Vol. 497, Why Galaxies Care about AGB Stars III: A Closer Look in
Space and Time. p. 473 ( `[arXiv:1503.04674](http://arxiv.org/abs/1503.04674)` )
Engels D., Etoka S., Jiménez-Esteban F., Herrmann W., LópezMartí B., 2024, in de Grĳs R., Whitelock P. A., Catelan M.,
eds, IAU Symposium Vol. 376, IAU Symposium. pp 328–333,
[doi:10.1017/S1743921323002983](http://dx.doi.org/10.1017/S1743921323002983)

[Freytag B., Höfner S., 2023, A&A, 669, A155](http://dx.doi.org/10.1051/0004-6361/202244992)
Ginsburg A., McGuire B., Plambeck R., Bally J., Goddi C., Wright M., 2019,

[ApJ, 872, 54](http://dx.doi.org/10.3847/1538-4357/aafb71)
[Ginsburg A., et al., 2023, ApJ, 942, 66](http://dx.doi.org/10.3847/1538-4357/ac9f4a)
[Gottlieb C. A., Myers P. C., Thaddeus P., 2003, ApJ, 588, 655](http://dx.doi.org/10.1086/368378)
[Gottlieb C. A., et al., 2022, A&A, 660, A94](http://dx.doi.org/10.1051/0004-6361/202140431)
Güsten R., Nyman L. Å., Schilke P., Menten K., Cesarsky C., Booth R., 2006,

[A&A, 454, L13](http://dx.doi.org/10.1051/0004-6361:20065420)

[Harris C. R., et al., 2020, Nature, 585, 357](http://dx.doi.org/10.1038/s41586-020-2649-2)
[Helmer M., Plane J. M. C., 1993, The Journal of Chemical Physics, 99, 7696](http://dx.doi.org/10.1063/1.466215)
Helou G., Walker D. W., eds, 1988, Infrared Astronomical Satellite (IRAS)
Catalogs and Atlases.Volume 7: The Small Scale Structure Catalog. Vol.

7

[Herwig F., 2005, ARA&A, 43, 435](http://dx.doi.org/10.1146/annurev.astro.43.072103.150600)
Heske A., Forveille T., Omont A., van der Veen W. E. C. J., Habing H. J.,
[1990, A&A, 239, 173](https://ui.adsabs.harvard.edu/abs/1990A&A...239..173H)
Highberger J. L., Thomson K. J., Young P. A., Arnett D., Ziurys L. M., 2003,

[ApJ, 593, 393](http://dx.doi.org/10.1086/376446)
Hoang T. D., Karska A., Lee M. Y., Wyrowski F., Tram L. N., Yang A.,
[Menten K. M., 2023, A&A, 679, A121](http://dx.doi.org/10.1051/0004-6361/202347163)
[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
[Husain D., Marshall P., 1986, International Journal of Chemical Kinetics, 18,](http://dx.doi.org/https://doi.org/10.1002/kin.550180108)

83

Irvine W. M., Senay M., Lovell A. J., Matthews H. E., McGonagle D., Meier
[R., 2000, Icarus, 143, 412](http://dx.doi.org/10.1006/icar.1999.6281)
[Justtanont K., Tielens A. G. G. M., 1992, ApJ, 389, 400](http://dx.doi.org/10.1086/171215)
[Justtanont K., Olofsson G., Dĳkstra C., Meyer A. W., 2006, A&A, 450, 1051](http://dx.doi.org/10.1051/0004-6361:20054569)
Justtanont K., Teyssier D., Barlow M. J., Matsuura M., Swinyard B., Waters
[L. B. F. M., Yates J., 2013, A&A, 556, A101](http://dx.doi.org/10.1051/0004-6361/201321812)

[Justtanont K., et al., 2015, A&A, 578, A115](http://dx.doi.org/10.1051/0004-6361/201526270)

[Juvela M., et al., 2015, A&A, 584, A94](http://dx.doi.org/10.1051/0004-6361/201425269)
Kamiński T., Gottlieb C. A., Young K. H., Menten K. M., Patel N. A., 2013,

[ApJS, 209, 38](http://dx.doi.org/10.1088/0067-0049/209/2/38)
[Karakas A. I., Lattanzio J. C., 2014, Publ. Astron. Soc. Australia, 31, e030](http://dx.doi.org/10.1017/pasa.2014.21)
[Karakas A. I., Lugaro M., 2016, ApJ, 825, 26](http://dx.doi.org/10.3847/0004-637X/825/1/26)
[Kessler M. F., et al., 1996, A&A, 315, L27](http://adsabs.harvard.edu/abs/1996A%26A...315L..27K)

[Khouri T., et al., 2014, A&A, 561, A5](http://dx.doi.org/10.1051/0004-6361/201322578)
Kim H., Trejo A., Liu S.-Y., Sahai R., Taam R. E., Morris M. R., Hirano N.,
[Hsieh I. T., 2017, Nature Astronomy, 1, 0060](http://dx.doi.org/10.1038/s41550-017-0060)
[Klisch E., Schilke P., Belov S. P., Winnewisser G., 1997, J. Mol. Spectrosc.,](http://dx.doi.org/10.1006/jmsp.1997.7447)

[186, 314](https://ui.adsabs.harvard.edu/abs/1997JMoSp.186..314K)
[Kuan Y.-J., Mehringer D. M., Snyder L. E., 1996, ApJ, 459, 619](http://dx.doi.org/10.1086/176926)


MNRAS **000**, 1–29 (2023)



[Lee S. K., Ozeki H., Saito S., 1995, ApJS, 98, 351](http://dx.doi.org/10.1086/192165)
Lindqvist M., Nyman L.-A., Olofsson H., Winnberg A., 1988, A&A, [205,](http://adsabs.harvard.edu/abs/1988A%26A...205L..15L)
[L15](http://adsabs.harvard.edu/abs/1988A%26A...205L..15L)

[Mamon G. A., Glassgold A. E., Huggins P. J., 1988, ApJ, 328, 797](http://dx.doi.org/10.1086/166338)
[Marigo P., et al., 2020, Nature Astronomy, 4, 1102](http://dx.doi.org/10.1038/s41550-020-1132-1)
[Marini E., et al., 2023, A&A, 670, A97](http://dx.doi.org/10.1051/0004-6361/202245501)
Martín S., Mauersberger R., Martín-Pintado J., García-Burillo S., Henkel C.,
[2003, A&A, 411, L465](http://dx.doi.org/10.1051/0004-6361:20031442)

[Martín S., et al., 2021, A&A, 656, A46](http://dx.doi.org/10.1051/0004-6361/202141567)
[Massalkhi S., Agúndez M., Cernicharo J., 2019, A&A, 628, A62](http://dx.doi.org/10.1051/0004-6361/201935069)
[McGonagle D., Irvine W. M., 1997, ApJ, 477, 711](http://dx.doi.org/10.1086/303749)
[Milam S. N., Apponi A. J., Woolf N. J., Ziurys L. M., 2007, ApJ, 668, L131](http://dx.doi.org/10.1086/522928)
[Millar T. J., Herbst E., 1990, A&A, 231, 466](https://ui.adsabs.harvard.edu/abs/1990A&A...231..466M)
[Moe M., Di Stefano R., 2017, ApJS, 230, 15](http://dx.doi.org/10.3847/1538-4365/aa6fb6)
[Müller H. S. P., Brünken S., 2005, J. Mol. Spectrosc., 232, 213](http://dx.doi.org/10.1016/j.jms.2005.04.010)
[Müller H. S. P., Thorwirth S., Roth D. A., Winnewisser G., 2001, A&A, 370,](http://dx.doi.org/10.1051/0004-6361:20010367)

[L49](http://adsabs.harvard.edu/abs/2001A%26A...370L..49M)

[Müller H. S. P., Schlöder F., Stutzki J., Winnewisser G., 2005, J Mol. Struct.,](http://dx.doi.org/10.1016/j.molstruc.2005.01.027)


[742, 215](http://adsabs.harvard.edu/abs/2005JMoSt.742..215M)
[Müller H. S. P., et al., 2007, Physical Chemistry Chemical Physics, 9, 1579](http://dx.doi.org/10.1039/B618799D)
NCBI 2024, Ionization Energy in the Periodic Table of Elements, `[https://pubchem.ncbi.nlm.nih.gov/periodic-table/](https://pubchem.ncbi.nlm.nih.gov/periodic-table/ionization-energy)`
```
  ionization-energy
```

[Nguyen Luong Q., et al., 2011, A&A, 529, A41](http://dx.doi.org/10.1051/0004-6361/201016271)
Nicolaes D., Groenewegen M. A. T., Royer P., Lombaert R., Danilovich T.,
[Decin L., 2018, A&A, 618, A143](http://dx.doi.org/10.1051/0004-6361/201833168)
[Olofsson H., Eriksson K., Gustafsson B., Carlstrom U., 1993, ApJS, 87, 267](http://dx.doi.org/10.1086/191804)
[Olofsson H., et al., 2022, A&A, 665, A82](http://dx.doi.org/10.1051/0004-6361/202244053)
[Plane J. M. C., Rajasekhar B., Bartolotti L., 1989, The Journal of Chemical](http://dx.doi.org/10.1063/1.457436)
[Physics, 91, 6177](http://dx.doi.org/10.1063/1.457436)
Price S. D., Murdock T. L., 1983, AFGL-TR-0208 Environemental Research
[papers, 161, 0](https://ui.adsabs.harvard.edu/abs/1983AFGL..161....0P)
[Quintana-Lacaci G., et al., 2016, ApJ, 818, 192](http://dx.doi.org/10.3847/0004-637X/818/2/192)
Quintana-Lacaci G., Velilla-Prieto L., Agúndez M., Fonfría J. P., Cernicharo
[J., Decin L., Castro-Carrizo A., 2023, A&A, 669, A56](http://dx.doi.org/10.1051/0004-6361/202244396)
Renzini A., 1981, in Iben I., Renzini A., eds, Physical Processes in Red Giants.
Springer Netherlands, Dordrecht, pp 431–446
[Saberi M., Vlemmings W. H. T., De Beck E., 2019, A&A, 625, A81](http://dx.doi.org/10.1051/0004-6361/201935309)
Saberi M., Khouri T., Velilla-Prieto L., Fonfría J. P., Vlemmings W. H. T.,
[Wedemeyer S., 2022, A&A, 663, A54](http://dx.doi.org/10.1051/0004-6361/202141704)
[Sahai R., Scibelli S., Morris M. R., 2016, ApJ, 827, 92](http://dx.doi.org/10.3847/0004-637X/827/2/92)
Samus’ N. N., Kazarovets E. V., Durlevich O. V., Kireeva N. N., Pastukhova
[E. N., 2017, Astronomy Reports, 61, 80](http://dx.doi.org/10.1134/S1063772917010085)
Sánchez Contreras C., Bujarrabal V., Neri R., Alcolea J., 2000, A&A, [357,](http://adsabs.harvard.edu/abs/2000A%26A...357..651S)
[651](http://adsabs.harvard.edu/abs/2000A%26A...357..651S)

Sánchez Contreras C., Alcolea J., Bujarrabal V., Castro-Carrizo A., Velilla
Prieto L., Santand er-García M., Quintana-Lacaci G., Cernicharo J., 2018,
[A&A, 618, A164](http://dx.doi.org/10.1051/0004-6361/201833632)
Sánchez Contreras C., Alcolea J., Rodríguez Cardoso R., Bujarrabal V.,
Castro-Carrizo A., Quintana-Lacaci G., Velilla-Prieto L., Santander[García M., 2022, arXiv e-prints, p. arXiv:2206.12185](https://ui.adsabs.harvard.edu/abs/2022arXiv220612185S)
[Saral G., et al., 2017, ApJ, 839, 108](http://dx.doi.org/10.3847/1538-4357/aa6575)
[Schöier F. L., Bast J., Olofsson H., Lindqvist M., 2007, A&A, 473, 871](http://dx.doi.org/10.1051/0004-6361:20077887)
[Siebert M. A., Van de Sande M., Millar T. J., Remĳan A. J., 2022, ApJ, 941,](http://dx.doi.org/10.3847/1538-4357/ac9e52)

[90](https://ui.adsabs.harvard.edu/abs/2022ApJ...941...90S)

[Singh A. P., Edwards J. L., Ziurys L. M., 2022, AJ, 164, 230](http://dx.doi.org/10.3847/1538-3881/ac8df0)
[Stoehr F., et al., 2017, The Messenger, 167, 2](https://ui.adsabs.harvard.edu/abs/2017Msngr.167....2S)
[Usov V. V., 1991, MNRAS, 252, 49](http://dx.doi.org/10.1093/mnras/252.1.49)

[Van de Sande M., Millar T. J., 2022, MNRAS, 510, 1204](http://dx.doi.org/10.1093/mnras/stab3282)
Van de Sande M., Decin L., Lombaert R., Khouri T., de Koter A., Wyrowski
[F., De Nutte R., Homan W., 2018, A&A, 609, A63](http://dx.doi.org/10.1051/0004-6361/201731298)
[Van de Sande M., Walsh C., Millar T. J., 2023, Faraday Discussions, 245, 586](http://dx.doi.org/10.1039/D3FD00039G)
[Velilla Prieto L., et al., 2017, A&A, 597, A25](http://dx.doi.org/10.1051/0004-6361/201628776)
Ventura P., Karakas A., Dell’Agli F., García-Hernández D. A., Guzman[Ramirez L., 2018, MNRAS, 475, 2282](http://dx.doi.org/10.1093/mnras/stx3338)

[Virtanen P., et al., 2020, Nature Methods, 17, 261](http://dx.doi.org/10.1038/s41592-019-0686-2)
[Viti S., Caselli P., Hartquist T. W., Williams D. A., 2001, A&A, 370, 1017](http://dx.doi.org/10.1051/0004-6361:20010300)
[Vlemmings W. H. T., et al., 2018, A&A, 613, L4](http://dx.doi.org/10.1051/0004-6361/201832929)

[Wallström S. H. J., et al., 2024, A&A, 681, A50](http://dx.doi.org/10.1051/0004-6361/202347632)

[Winnewisser G., Belov S. P., Klaus T., Schieder R., 1997, Journal of Molecular](http://dx.doi.org/10.1006/jmsp.1997.7341)
[Spectroscopy, 184, 468](http://dx.doi.org/10.1006/jmsp.1997.7341)
[Xu J.-L., Wang J.-J., 2013, MNRAS, 431, 2385](http://dx.doi.org/10.1093/mnras/stt331)
[Zhang B., et al., 2014, ApJ, 781, 89](http://dx.doi.org/10.1088/0004-637X/781/2/89)


**APPENDIX A:** **ADDITIONAL TABLES AND PLOTS**


In this section we present additional tables and plots which provide
additional details of our observations. Table A1 provides details of
the ALMA line observations and Table A2 provides details of the
continuum images. Additional continuum images, with a focus on
the Band 3 data, are shown in Fig. A1. The molecular line IDs are
given in Table A3 and the full spectra are shown in Fig. A2 for the
Band 6 spectra (with one spectral window given in Fig. 2) and in
Fig. A3 for the Band 6 spectra.
The additional figures in this section are supplemental to the results
presented in the body of the paper. In Fig. A4 we show some examples
of soft parabola fits, as were discussed in Sect. 2.5. Figures A5 and A6
present channel maps of the CO emission as respectively observed
with the extended array configuration in Band 6 and with Band 3.
Fig. A7 shows the channel maps of the brightest observed SO 2 line,
which is discussed in Sect. 3.4. In Fig. A8 we give a PV diagram
of the NS line detected in Band 3, discussed in Sect. 3.5, and in
Fig. A9 we present the population diagrams of Na [35] Cl and K [35] Cl,
as discussed in Sect. 3.6.


**APPENDIX B:** **INTERSTELLAR CONTAMINATION**


Here we discuss in more detail the interstellar contamination experienced by OH 30.1 −0.7 (see also Sect. 2.4), which we believe arises
from the background star-forming region W43. Contamination can
be seen in most previous studies of CO towards this object (e.g. De
Beck et al. 2010), most of which rely on single-dish observations.
Although some clever observational techniques can be employed to
improve the single-dish observations of contaminated stars (see for
example Heske et al. 1990), these are generally less precise than the
spatial filtering of an interferometer.
In Fig. B1 we plot the combined ALMA spectra of CO _𝐽_ = 2−1, extracted for two apertures of different size, superposed with the spectra
of the same line observed with the Atacama Pathfinder Experiment
(APEX, Güsten et al. 2006), the James Clerk Maxwell Telescope
(JCMT), and the IRAM 30m telescope. The JCMT spectrum was
first published in De Beck et al. (2010), the IRAM spectrum was
first published in Justtanont et al. (2013), and the APEX spectrum
is previously unpublished and was observed by the APEX/PI230
instrument [2] in August 2018 (project ID: O-0102.F-9301B). There
is considerable contamination in the JCMT observation, especially
below velocities of around 107 km s [−][1] . The effect is even larger
for the APEX observation, which has a larger HPBW ( _𝜃_ = 27 [′′] for
APEX and _𝜃_ = 20 [′′] for JCMT). IRAM, which has the smallest beam
( _𝜃_ = 10 _._ 7 [′′] ), suffers from the least amount of contamination, but the
contamination still impacts the flux below ∼ 107 km s [−][1] . In Fig. B1,
we adjust the flux axis of the left panel to best show the CO emission
originating from OH 30.1 −0.7, while the middle panel shows the full
range of the emission/absorption detected by APEX and JCMT. The
contamination entirely dominates the APEX and JCMT flux below


2 PI230 is a collaboration between the European Southern Observatory
(ESO) and the Max-Planck-Institut für Radioastronomie (MPIfR).



_The salty emission of OH 30.1_ − _0.7_ 19


100 km s [−][1] . Nevertheless, the ALMA observations are in general
agreement with the single-dish observations above 107 km s [−][1], suggesting that the AGB flux is likely not resolved out at those velocities
in the Band 6 observations. The fact that the ALMA spectra extracted
for two apertures of different sizes (radii of 8 [′′] and 3 [′′] ) largely agree
with each other indicates that the CO flux is mostly confined within
3 [′′] of the continuum peak. We also checked the line profile of the
ALMA observations taken with only the extended array configuration, and found that the flux (for an extraction aperture with diameter
6 [′′] ) does not deviate from that of the combined data; i.e. even for
the extended configuration, there is no resolved-out flux (see also
the extended configuration channel maps in Fig. A5). Based on these
comparisons, and considering that CO is the most extended observed
molecule, we assert that none of the Band 6 observations suffer from
resolved out flux.
We also compare the ALMA Band 3 CO _𝐽_ = 1 − 0 line with
the IRAM observation of the same line first published in Justtanont
et al. (2013), plotted in the right panel of Fig. B1. Since the singledish beam is larger at the lower frequency, the IRAM line suffers
from significant contamination. The Band 3 observation has a larger
maximum resolvable scale than the Band 6 observation, and hence is
also more susceptible to contamination. From inspecting the channel
maps, shown in Fig. A6, we can see significant contamination, in
the form of diagonal bars, in the channels with velocities below
100 km s [−][1] . The contamination can also be seen as spikes in the full
spectrum in Fig. A3 and contributes to a difficulty in disentangling a
possible K [35] Cl 𝑣= 0 line from both the AGB CO emission and the
background contamination (see Table A3). However, given the shape
of the CO emission and the larger maximum resolvable scale for the
Band 3 data, we also assume that there is no resolved out flux in the
Band 3 observations.


**APPENDIX C:** **COMPARISON WITH PREVIOUS STUDIES**

**OF MOLECULAR DETECTIONS AND DISTRIBUTIONS**


**C1** **SiS**


SiS is a commonly observed molecule that has been detected in the
envelopes of all chemical types of AGB stars. It is generally found
to be more abundant in carbon-rich CSEs than oxygen-rich CSEs
(Schöier et al. 2007). However, Danilovich et al. (2018) found that
SiS was more likely to be detected for AGB stars with higher massloss rates and hence denser circumstellar envelopes, across chemical
types. This trend was confirmed by Massalkhi et al. (2019) for a larger
sample of carbon stars, although Danilovich et al. (2019) also found
that very sensitive ALMA observations could detect low abundances
of SiS (down to ∼ 10 [−][8] relative to H 2 ) for even low mass-loss rate
oxygen-rich stars. Since OH 30.1 −0.7 is thought to have a high massloss rate, detections of SiS are expected where the lines are covered
by our observations.


**C2** **CS**


Since it is a carbon-bearing molecule, CS has often been associated
with carbon-rich CSEs. However, it has also been detected in several oxygen-rich CSEs, as well as towards S-type AGB stars (e.g.
Lindqvist et al. 1988; Danilovich et al. 2018). Similar to SiS, CS has
been found to be more prevalent in higher density oxygen-rich and
S-type CSEs (Danilovich et al. 2018), possibly because of a higher
prevalence of shocks (e.g. from larger pulsations in Mira variables as


MNRAS **000**, 1–29 (2023)

20 _Danilovich et al_


**Table A1.** Parameters of Band 3 and Band 6 ALMA observations for OH 30.1−0.7 from project 2016.1.00005.S.


Band, configuration Frequencies Restoring beam Beam PA Channel separation MRS _[𝑎]_ Date observed

[GHz] [ [′′] ] [ [◦] ] [km s [−][1] ] [MHz] [ [′′] ]

Band 3 100.028 – 101.899 1 _._ 756 × 1 _._ 179 −56 _._ 0 2.88 0.98 15.0 2016-12-05

Band 3 101.830 – 103.701 1 _._ 731 × 1 _._ 155 −55 _._ 7 2.83 0.98 15.0 2016-12-05

Band 3 111.947 – 113.818 1 _._ 576 × 1 _._ 078 −54 _._ 6 2.62 0.98 15.0 2016-12-05

Band 3 113.827 – 115.698 1 _._ 535 × 1 _._ 059 −54 _._ 9 2.57 0.98 15.0 2016-12-05

Band 6, extended 226.086 – 227.957 0 _._ 390 × 0 _._ 265 −67 _._ 2 2.57 1.95 4.5 2017-05-05
Band 6, compact 226.086 – 227.957 1 _._ 714 × 1 _._ 500 −76 _._ 6 2.57 1.95 12.8 2017-03-28
Band 6, combined 226.090 – 227.957 0 _._ 412 × 0 _._ 277 −67 _._ 1 2.57 1.95        -        
Band 6, extended 229.085 – 230.956 0 _._ 395 × 0 _._ 256 −78 _._ 4 2.54 1.95 4.5 2017-05-05
Band 6, compact 229.085 – 230.956 1 _._ 711 × 1 _._ 480 −75 _._ 8 2.54 1.95 12.8 2017-03-28
Band 6, combined 229.089 – 230.956 0 _._ 427 × 0 _._ 273 −78 _._ 0 2.54 1.95        -        
Band 6, extended 242.073 – 243.944 0 _._ 355 × 0 _._ 255 −73 _._ 5 2.42 1.95 4.5 2017-05-05
Band 6, compact 242.073 – 243.943 1 _._ 626 × 1 _._ 397 −75 _._ 9 2.42 1.95 12.8 2017-03-28
Band 6, combined 242.073 – 243.940 0 _._ 379 × 0 _._ 269 −73 _._ 1 2.42 1.95        -        
Band 6, extended 244.086 – 245.957 0 _._ 373 × 0 _._ 251 −78 _._ 0 2.40 1.95 4.5 2017-05-05
Band 6, compact 244.086 – 245.957 1 _._ 617 × 1 _._ 384 −76 _._ 2 2.40 1.95 12.8 2017-03-28
Band 6, combined 244.086 – 245.953 0 _._ 401 × 0 _._ 265 −78 _._ 6 2.40 1.95        -        

**Notes.** ( _[𝑎]_ ) MRS is the maximum recoverable scale.


**Table A2.** Parameters of continuum images of OH 30.1−0.7 constructed from the observations of project 2016.1.00005.S.


Band, configuration Restoring beam Beam PA rms Peak flux Dynamic range

[ [′′] ] [ [◦] ] [mJy/beam] [mJy/beam]
Band 3 1 _._ 661 × 1 _._ 105 −55 _._ 9 1 _._ 27 × 10 [−][2] 0 _._ 746 59
Band 3, resolution matching Band 6, compact 1 _._ 630 × 1 _._ 400 −75 _._ 0 1 _._ 34 × 10 [−][2] 0 _._ 788 59
Band 6, extended 0 _._ 372 × 0 _._ 239 −71 _._ 7 1 _._ 40 × 10 [−][2] 5 _._ 22 372
Band 6, compact 1 _._ 628 × 1 _._ 399 −75 _._ 0 4 _._ 21 × 10 [−][2] 7 _._ 26 172
Band 6, combined, full resolution 0 _._ 397 × 0 _._ 252 −71 _._ 6 1 _._ 41 × 10 [−][2] 5 _._ 26 374
Band 6, combined, taper = 0 _._ 5 0 _._ 662 × 0 _._ 536 −88 _._ 3 1 _._ 51 × 10 [−][2] 6 _._ 47 427
Band 6, combined, taper = 0 _._ 8 0 _._ 986 × 0 _._ 829 −87 _._ 7 1 _._ 78 × 10 [−][2] 7 _._ 19 403


|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||
||||||
||||||
||||||
||||||



RA offset [arcsec]





6


4


2





Flux [Jy/beam]
10 4





Flux [Jy/beam]
10 4


RA offset [arcsec]



0


2


4


6



Flux [Jy/beam]
10 4 10 3


5 0 5

RA offset [arcsec]





**Figure A1.** The continuum plots for OH 30.1 −0.7 observed with ALMA Band 3 ( _left_ ) and the compact configuration of ALMA Band 6 ( _centre_ ), plotted on a
logarithmic flux scale. The Band 3 image has been convolve to have the same beam as the Band 6 image. The contours indicate levels of 3 _𝜎_ (thinnest white
line), and 5, 10, 30 and 100 _𝜎_ (thicker white lines). On the _right_ we plot the Band 3 continuum with the 5 and 10 _𝜎_ contours of the compact Band 6 continuum
overplotted in pink. In all panels, the red crosses indicate the continuum peak. The beams are shown as white ellipses in the bottom left corners. North is up and

east is left.


MNRAS **000**, 1–29 (2023)

_The salty emission of OH 30.1_ − _0.7_ 21


**Table A3.** Lines identified towards OH 30.1 −0.7. Spectra are shown in Figures A2 and A3.


Species Freq E low Transition _𝜐_ cent _𝜐_ w Flux Ap. _[𝑎]_ Notes

[GHz] [K] [km s [−][1] ] [km s [−][1] ] [Jy km s [−][1] ] [ [′′] ]
SO 2 100.878 7.8 _𝜈_ = 0 _, 𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 2 2 _,_ 0 − 3 1 _,_ 3 99.3 18.9 0.32 3.0
Na [37] Cl 101.962 17.1 𝑣= 0 _, 𝐽_ = 8 − 7 100.2 19.0 0.24 2.0
3433 SOSO 22 102.032102.998 2.72.8 _𝜈𝜈_ == 0 0 _, 𝐽, 𝐽_ _𝐾𝐾_ _𝑎𝑎_ _,𝐾,𝐾_ _𝑐𝑐_ == 3 3 11 _,,_ 33 −− 22 00 _,,_ 22 99.9... 19.0... 0.40... 3.0... Tentative and hyperfine
Na [35] Cl 103.415 537.4 𝑣= 1 _, 𝐽_ = 8 − 7 103.7 12.0 0.06 2.0
C [17] O 112.359 0.0 𝑣= 0 _, 𝐽_ = 1 − 0 ... ... ... ... Tentative
Na [37] Cl 114.701 22.0 𝑣= 0 _, 𝐽_ = 9 − 8 99.4 23.2 0.19 1.0
NS 115.154 3.3 2 Π 1/2 _,_ 𝑣= 0 _, 𝑒,_ _𝐽_ = 5/2 − 3/2 _,_ _𝐹_ = 7/2 − 5/2 ... ... ... ... Brightest hyperfine component
NS 115.157 3.3 2 Π 1/2 _,_ 𝑣= 0 _, 𝑒,_ _𝐽_ = 5/2 − 3/2 _,_ _𝐹_ = 5/2 − 3/2 ... ... ... ... Hyperfine
NS 115.163 3.3 2 Π 1/2 _,_ 𝑣= 0 _, 𝑒,_ _𝐽_ = 5/2 − 3/2 _,_ _𝐹_ = 3/2 − 1/2 ... ... ... ... Hyperfine
CO 115.271 0.0 𝑣= 0 _, 𝐽_ = 1 − 0 100.9 17.0 48.20 5.0
K [35] Cl 115.292 38.8 𝑣= 0 _, 𝐽_ = 15 − 14 ... ... ... ... Blend with CO; tentative
NS 115.556 3.4 2 Π 1/2 _,_ 𝑣= 0 _,_ _𝑓,_ _𝐽_ = 5/2 − 3/2 _,_ _𝐹_ = 5/2 − 3/1 ... ... ... ... Brightest hyperfine, tentative
NS 115.571 3.4 2 Π 1/2 _,_ 𝑣= 0 _,_ _𝑓,_ _𝐽_ = 5/2 − 3/2 _,_ _𝐹_ = 5/2 − 3/2 ... ... ... ... Hyperfine, tentative
NS 115.572 3.3 2 Π 1/2 _,_ 𝑣= 0 _,_ _𝑓,_ _𝐽_ = 5/2 − 3/2 _,_ _𝐹_ = 3/2 − 1/2 ... ... ... ... Hyperfine, tentative
SO 30 SiS 2 226.502226.300 1118.2108.2 𝑣= _𝜈_ = 1 0 _, 𝐽, 𝐽_ _𝐾_ = _𝑎_ 13 _,𝐾_ − _𝑐_ =12 14 3 _,_ 11 − 14 2 _,_ 12 99.299.7 19.011.7 0.790.05 2.00.3
Na [35] Cl 227.351 2143.1 𝑣= 4 _, 𝐽_ = 18 − 17 101.2 7.6 0.05 0.5
K [35] Cl 227.497 954.4 𝑣= 2 _, 𝐽_ = 30 − 29 100.3 7.0 0.07 0.5
Na [37] Cl 227.560 607.5 𝑣= 1 _, 𝐽_ = 18 − 17 101.8 12.6 0.33 0.5 Blend with wing of [30] SiS
30 SiS 227.590 65.6 𝑣= 0 _, 𝐽_ = 13 − 12 99.8 22.0 1.04 1.0 Blend with wing of Na [37] Cl
Na [37] Cl 229.246 93.6 𝑣= 0 _, 𝐽_ = 18 − 17 100.2 18.1 1.11 1.0
Si [34] S 229.501 66.1 𝑣= 0 _, 𝐽_ = 13 − 12 98.7 22.8 1.34 1.0
41 K 35 Cl 229.682 952.3 𝑣= 2 _, 𝐽_ = 31 − 30 98.6 14.6 0.06 0.3
K [37] Cl 229.819 559.6 𝑣= 1 _, 𝐽_ = 31 − 30 100.6 9.5 0.07 0.5
34 SO 2 229.858 7.6 _𝜈_ = 0 _, 𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 4 2 _,_ 2 − 3 1 _,_ 3 99.9 22.6 1.54 3.0
K [35] Cl 230.321 160.5 𝑣= 0 _, 𝐽_ = 30 − 29 101.6 13.4 0.36 0.5
29 SiS 230.510 1128.6 𝑣= 1 _, 𝐽_ = 13 − 12 ... ... ... ... Blend with wing of CO
CO 230.538 5.5 𝑣= 0 _, 𝐽_ = 2 − 1 101.9 17.9 214.50 5.0
Na [35] Cl 230.779 1129.3 𝑣= 2 _, 𝐽_ = 18 − 17 101.2 11.8 0.31 0.5
29 Si 34 S 242.478 75.7 𝑣= 0 _, 𝐽_ = 14 − 13 ... ... ... ...
K [35] Cl 242.612 976.6 𝑣= 2 _, 𝐽_ = 32 − 31 100.5 14.8 0.12 0.5
SO 2 243.088 41.4 _𝜈_ = 0 _, 𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 5 4 _,_ 2 − 6 3 _,_ 3 ... ... ... ... Tentative. Blend with K [37] Cl
K [37] Cl 243.110 971.5 𝑣= 2 _, 𝐽_ = 33 − 32 ... ... ... ... Blend with SO 2
Na [35] Cl 243.574 1140.4 𝑣= 2 _, 𝐽_ = 19 − 18 101.5 11.4 0.34 0.5
30 SiS 243.917 1129.1 𝑣= 1 _, 𝐽_ = 14 − 13 100.2 6.2 0.07 0.3
SO 41 K 235 Cl 244.448244.254 974.782.2 𝑣= _𝜈_ = 2 0 _, 𝐽, 𝐽_ _𝐾_ = _𝑎_ 33 _,𝐾_ − _𝑐_ =32 14 0 _,_ 14 − 13 1 _,_ 13 98.7... 21.7... 5.38... 3.0... Tentative
34 SO 2 244.482 81.9 _𝜈_ = 0 _, 𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 14 0 _,_ 14 − 13 1 _,_ 13 ... ... ... ... Tentative
K [37] Cl 244.594 582.1 𝑣= 1 _, 𝐽_ = 33 − 32 100.6 8.0 0.03 0.3

CS 244.936 23.5 𝑣= 0 _, 𝐽_ = 5 − 4 99.39 18.2 1.95 3.0
30 SiS 245.088 76.5 𝑣= 0 _, 𝐽_ = 14 − 13 99.3 19.6 1.10 1.0
34 SO 2 245.302 28.9 _𝜈_ = 0 _, 𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 6 3 _,_ 3 − 6 2 _,_ 4 ... ... ... ... Tentative
Na [35] Cl 245.401 626.2 𝑣= 1 _, 𝐽_ = 19 − 18 101.3 14.6 0.77 0.5
SO 2 245.563 61.0 _𝜈_ = 0 _, 𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 10 3 _,_ 7 − 10 2 _,_ 8 98.3 19.7 2.79 3.0
K [35] Cl 245.624 183.0 𝑣= 0 _, 𝐽_ = 32 − 31 101.9 12.2 0.34 0.5
Si [34] S 245.960 1134.2 𝑣= 1 _, 𝐽_ = 14 − 13 99.7 7.7 0.07 0.5


**Notes.** For NS, we list the three brightest hyperfine components (see discussion in Sect. 3.5). For C [17] O, we give the frequency and quantum numbers
corresponding to the brightest hyperfine component, which happens to also be the central hyperfine component. ( _[𝑎]_ ) Ap. gives the radius of the circular aperture
used to extract the spectrum from which the central velocity ( _𝜐_ cent ), velocity width ( _𝜐_ w ) and integrated flux were calculated. These line parameters were not
calculated for known blended lines or lines that were too marginal in the spectra to fit a soft parabola function (see text for details).



compared with semiregular variables) in these CSEs which can liberate C from CO to enable the formation of CS. This may also result
in CS being more abundant for Mira variable stars than semiregular
variable stars, among the oxygen-rich AGBs (Danilovich et al. 2019).
However, for carbon-rich AGB stars, the abundance of CS has generally been found to be one to two orders of magnitude higher than
for oxygen-rich stars (Massalkhi et al. 2019; Danilovich et al. 2018).
Since OH 30.1 −0.7 has a high mass-loss rate and hence high wind



density, detections of CS are expected despite it being an oxygen-rich

star.


**C3** **SO** **2**


SO 2 is thought to be formed in circumstellar envelopes from SO.
Previous studies, mostly focussing on AGB stars known to have low
initial masses, have shown that the distributions of SO and SO 2
can be divided into two groups of morphological structures in AGB


MNRAS **000**, 1–29 (2023)

22 _Danilovich et al_


0.05


0.04


0.03


0.02


0.01


0.00


0.01


0.02


0.04


0.02


0.00







226.25 226.50 226.75 227.00 227.25 227.50 227.75 228.00
Frequency [GHz]



0.03


0.02


0.01


0.00


0.01


0.02


0.02







0.01


0.00


242.25 242.50 242.75 243.00 243.25 243.50 243.75 244.00
Frequency [GHz]


−
**Figure A2.** ALMA Band 6 spectra for OH 30.1 0.7. For each spectral window we show spectra for a large extraction aperture and a small extraction aperture,
with the extraction aperture radius and ALMA configuration given in the top right of each subplot. The molecular carriers of various spectral lines are indicated
at the top of each plot. See Table A3 for details.



circumstellar envelopes. Danilovich et al. (2016) found, from a small
sample, that SO distributions could either be centred on the star or
could exhibit a shell-like distribution, with the relative abundance of
SO peaking further out in the CSE, rather than being centred on the
star. It was found that the stars with lower mass-loss rates (or lower
wind densities) exhibited centralised SO distributions, while stars
with higher mass-loss rates (or higher wind densities) exhibited shelllike SO distributions. The larger ATOMIUM survey, using spatially
resolved ALMA observations, confirmed this trend for SO and also
for SO 2 (Wallström et al. 2024). Earlier data had been insufficient
to determine the spatial distribution of SO 2 . The chemical models
of Van de Sande & Millar (2022) and Van de Sande et al. (2023)


MNRAS **000**, 1–29 (2023)



predict more shell-like SO and SO 2 distributions for AGB stars with
UV-producing companions and/or with more clumpy CSEs.


**C4** **NS**


Aside from the AGB stars discussed in Sect. 4.1.1, NS has been
detected towards an early planetary nebula (Sánchez Contreras et al.
2000), giant molecular clouds (where it seen to be enhanced in massive star-forming regions such as Orion KL, McGonagle & Irvine
1997), hot cores (Xu & Wang 2013), comets (e.g. Irvine et al. 2000),
and a starburst galaxy (Martín et al. 2003, 2021). All of these objects

_The salty emission of OH 30.1_ − _0.7_ 23





0.15


0.10


0.05


0.00


0.04


0.02


0.00





244.25 244.50 244.75 245.00 245.25 245.50 245.75 246.00
Frequency [GHz]


**Figure A2.** continued.



contain regions with high UV fluxes (or experience UV flux during
part of their orbits, in the case of comets), suggesting that this could
be the dominant formation mechanism of astronomical NS. Viti et al.

(2001) performed chemical models of shocks in hot cores and found
that NS can be enhanced through shock heating, which is broadly
similar to the UV-driven chemistry driving the NS formation around
W Aql (Van de Sande & Millar 2022; Danilovich et al. 2024). Older
chemical models, which do not consider shocks or enhanced UV
chemistry were not able to reproduce the observed abundances of
NS in hot cores by several orders of magnitude (e.g. Millar & Herbst
1990).


**C5** **Chlorides**


The first astronomical detections of NaCl and KCl were reported by
Cernicharo & Guelin (1987) towards the nearby carbon-rich AGB
star CW Leo (along with AlCl). Subsequently, abundances relative
to H 2 of 1 _._ 8 × 10 [−][9] for NaCl and ∼ 5 × 10 [−][10] for KCl were derived
from more comprehensive observations by Agúndez et al. (2012),
who also found the [35] Cl/ [37] Cl isotopic ratio to be 2 _._ 9 ± 0 _._ 3, close to
the solar isotopic value of 3 _._ 3 ± 0 _._ 3. Spatially resolved observations
by Quintana-Lacaci et al. (2016) found elongated NaCl and KCl
emission and concluded that the NaCl was likely arranged in a spiral
or torus (with the formation of such a structure likely driven by a
companion). That study also detected NaCl in the first vibrationally
excited state for the first time.
NaCl has also been detected towards a handful of oxygen-rich stars.
The low-mass AGB star IK Tau (initial mass ∼ 1 _._ 3 M ⊙, Danilovich
et al. 2017a) has been observed to exhibit several different rotational lines of NaCl in the ground vibrational state (Milam et al.
2007; Velilla Prieto et al. 2017). Spatially resolved observations with
ALMA found it to have clumpy irregular NaCl (𝑣= 0) emission
(Decin et al. 2018). A subsequent 3D analysis by Coenegrachts et al.
(2023) found that the emission was roughly arranged in a clumpy
spiral and the formation of NaCl may have been driven by a stellar



or planetary companion. We note that the nearby low-mass AGB star
R Dor — observed with the same spectral setup and sensitivity as
IK Tau but not presently thought to have a solar type binary companion (Vlemmings et al. 2018) — did not have any detections of
NaCl (or NS, Decin et al. 2018). Additional detections of NaCl and
KCl were reported by Wallström et al. (2024) in the ATOMIUM
survey for the AGB stars IRC−10529 (NaCl in 𝑣= 0 _,_ 1 and KCl
in 𝑣= 0), IRC+10011 (NaCl in 𝑣= 0 _,_ 1 _,_ 2 and KCl in 𝑣= 0) and
GY Aql (NaCl in 𝑣= 0). All three of these oxygen-rich AGB stars are
thought to have companions shaping their winds, though the precise
natures of these companions are not yet known (Decin et al. 2020).
The RSGs VY CMa, NML Cyg and VX Sgr also have NaCl detected
towards them (Milam et al. 2007; Kamiński et al. 2013; Decin et al.
2016; Singh et al. 2022; Quintana-Lacaci et al. 2023; Wallström et al.
2024). In the spatially-resolved observations of VY CMa, NaCl is
seen to trace high velocity jets (Quintana-Lacaci et al. 2023).
There have also been detections of NaCl towards early post-AGB
stars, such as CRL 2688 (the Egg Nebula, Highberger et al. 2003)
and OH 231.8 +4.2 (the Rotten Egg Nebula Sánchez Contreras et al.
2018, 2022), both of which have bipolar outflows, with NaCl detected
in shell-like structures. Highberger et al. (2003) used the IRAM 30m
telescope to detect several NaCl lines in the ground vibrational state
towards CRL 2688. They suggest that the formation of NaCl is likely
driven by shocks and clumping in the high-velocity outflows. Sánchez
Contreras et al. (2022) used ALMA to observe OH 231.8 +4.2, an
AGB star which seems to be undergoing a premature evolution into
the pre-Planetary Nebula phase, possibly driven by the A0 companion
on a relatively close orbit (20 au). They detect vibrationally excited
NaCl up to 𝑣= 2 (and tentatively 𝑣= 3) and KCl (up to 𝑣= 1) in a
rotating and expanding cylindrical structure around the central star,
coinciding with a circumbinary dust disc. They also find a relatively
high vibrational temperature ( _𝑇_ vib = 1125 ± 160 K), consistent with
NaCl forming in hot conditions. In this case the dust disc could also
shield the Na and K atoms, preventing excessive photoionisation.
Sánchez Contreras et al. (2022) conclude that NaCl and KCl are


MNRAS **000**, 1–29 (2023)

24 _Danilovich et al_


0.0125


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025


0.0050


0.004


0.002


0.000


100.25 100.50 100.75 101.00 101.25 101.50 101.75
Frequency [GHz]


0.0150


0.0125


0.0100


0.0075


0.0050


0.0025


0.0000


0.0025


0.0050


0.004


0.002


0.000


102.00 102.25 102.50 102.75 103.00 103.25 103.50
Frequency [GHz]











−
**Figure A3.** ALMA Band 3 spectra for OH 30.1 0.7. For each spectral window we show spectra for a large extraction aperture and a small extraction aperture,
with the extraction aperture radius in the top right of each subplot. The molecular carriers of various spectral lines are indicated at the top of each plot. See Table

A3 for details.



good tracers of high-density regions and may be shock tracers. While
OH 30.1 −0.7 may have a similar companion to OH 231.8 +4.2, it
clearly does not have a bipolar outflow (and is not easily detected
in the optical, unlike the Rotten Egg Nebula), suggesting a different
orbital configuration.


Another astrophysical environment in which NaCl and KCl have
been frequently detected are high-mass young stellar objects (Ginsburg et al. 2019, 2023). Dubbed “brinaries” because of the strong
correlation between NaCl and H 2 O detections, Ginsburg et al. (2023)
found that the salt detections were neither rare nor ubiquitous. They
also find that the NaCl emission is restricted to the relatively inner
regions of discs or outflows, which are likely to be the warmer (but


MNRAS **000**, 1–29 (2023)



not ionised) regions of their sources. This is broadly similar to the
centrally confined NaCl and KCl detected here for OH 30.1 −0.7, and
likely correspond to similar hot and shocked formation conditions.


_C5.1_ _The formation of NaCl and KCl_


The main formation pathway for NaCl and KCl is thought to be
through neutral-neutral reactions between the alkali metal atom and
HCl. The reaction for NaCl has a relatively high activation energy
of 42 kJ mol [−][1] (Husain & Marshall 1986; Plane et al. 1989), significantly more than the 12 kJ mol [−][1] barrier for K + HCl (Helmer &
Plane 1993). Thus formation of NaCl and KCl is favoured at higher

_The salty emission of OH 30.1_ − _0.7_ 25



0.0100


0.0075


0.0050


0.0025


0.0000


0.0025


0.0050


0.0075


0.0100


0.002


0.000


0.002







112.00 112.25 112.50 112.75 113.00 113.25 113.50 113.75
Frequency [GHz]





0.4


0.2


0.0


0.2


0.4

0.02


0.01


0.00





114.00 114.25 114.50 114.75 115.00 115.25 115.50
Frequency [GHz]


**Figure A3.** continued



temperatures. Furthermore, both reactions are endothermic (by 19.2
and 7.8 kJ mol [−][1], respectively), and the reverse reactions of NaCl
and KCl with H are fast with small temperature dependences. This
means that NaCl and KCl can only persist if the H density is relatively low (see below). Another important consideration is that Na
and K have low ionisation potentials (5.139 eV for Na, 4.341 eV for
K, NCBI 2024, which correspond to wavelengths of 241 nm and
286 nm, respectively) and their singly ionised states, Na [+] and K [+],
are un-reactive closed shell ions. This means that UV photons from
a hot star could easily ionise Na and K and subsequent ion-neutral
reactions would not readily occur, hence effectively removing Na
and K and preventing the formation of their chlorides. This dilemma
is avoided if the environment is dense enough to provide shielding
against ionisation. Given the thick, dusty envelope of OH 30.1 −0.7



(see Sect. 4.2 and Marini et al. 2023) and its high mass-loss rate,
there should be an extremely high amount of extinction in the inner
wind, which would strongly attenuate any UV photons except for
in the immediate vicinity of the UV-producing star. For this reason,
heating from UV photons alone is unlikely to drive the formation of
NaCl or KCl since the UV photons will be highly attenuated and, if
they were not, they would instead ionise the metals and prevent the
formation of NaCl and KCl. Note that this is the opposite scenario to
the formation of NS. NS forms after its precursor N 2 has been photodissociated (Van de Sande & Millar 2022; Danilovich et al. 2024),
whereas NaCl and KCl require that their precursors Na and K not be
photoionised. This difference could explain why the distributions of
NaCl and NS in the Band 3 zeroth moment maps (Fig. 10 and Fig. 9)
are not co-located. An interesting additional check on the chemistry


MNRAS **000**, 1–29 (2023)

26 _Danilovich et al_

























50 75 100 125 150
Velocity [km/s]



50 75 100 125 150
Velocity [km/s]



50 75 100 125 150
Velocity [km/s]



50 75 100 125 150
Velocity [km/s]



**Figure A4.** Examples of soft parabola fits to selected lines towards OH 30.1 −0.7. Data is plotted as black histograms and the fits are shown as dashed red lines.
The molecular carriers and the corresponding transitions are given in the top right corner of each panel. Further details for each line, including the extraction
aperture for the spectrum, are given in Table A3. Details of the fitting procedure are given in Sect. 2.5.



would be mapping the SiN emission (which was not covered in our
observations) because its formation follows after the photoionisation
of Si to Si [+] .

Another possible obstacle for the formation of NaCl and KCl is
the H/H 2 ratio in the wind. If this is too high (e.g. if H/H 2 ≳ 10 [−][4] )
then the steady state reactions will favour the formation of HCl, Na,
and K, rather than NaCl and KCl. Given the observations presented
here and the implied high abundances of both NaCl and KCl, we can
confidently say that the H/H 2 ratio is low. High temperatures (e.g.
1000–2000 K) and high densities will also contribute to more rapid
formation of NaCl and KCl (as all chemical reactions proceed more
rapidly at higher number densities). This fits with previous results
finding that NaCl is preferentially formed as a consequence of shocks
(Cherchneff 2012).


**C6** **Species not detected or not covered**


Some of the species that we might expect to see towards a star such
as OH 30.1 −0.7 were either not covered in our observations or were

not detected. To eliminate confusion between these two possibilities,
we briefly summarise here which key molecular species were not
detected and which were not covered.

SiO and HCN are both seen almost ubiquitously towards AGB stars
of all types. Our spectral set up was such that no lines in the ground or
first four vibrationally excited states of [28] Si [16] O, [29] Si [16] O or [30] Si [16] O
were covered. No lines of HCN or H [13] CN in the ground vibrational
state were covered. Transitions of CN, the photodissociation product
of HCN, were covered but not detected above the noise.
SO is generally observed towards the same stars as SO 2, with
similar distribution patterns in the CSEs (Danilovich et al. 2016;
Wallström et al. 2024). Although we present several detections of
SO 2 towards OH 30.1 −0.7, no lines of SO or its isotopologues
( [32] SO, [34] SO, or [33] SO) were covered in our observations.
The recent work of Baudry et al. (2023) identified several highly
excited H 2 O lines (with upper level energies in the range 3954–
9012 K) in ALMA observations of a sample of oxygen-rich AGB
and RSG stars. Unfortunately, none of the emission lines detected in
the Baudry et al. (2023) sample were covered in our spectral configurations. We found no other lines of H 2 O towards OH 30.1 −0.7,
despite clear detections of relatively low-energy H 2 O lines observed
by _Herschel_ /HIFI (Justtanont et al. 2015). No OH lines in the ground
vibrational state were covered in the Band 6 data.

H 2 S is associated with high mass-loss rate/high CSE density


MNRAS **000**, 1–29 (2023)



oxygen-rich AGB stars (Danilovich et al. 2017b). Only two lines of
H 2 S were covered in our observations and both were high-energy
lines ( _𝐸_ low _>_ 2000 K) that have not previously been detected
for any AGB stars. One lower-energy line of H 2 [34] S was covered
( _𝐸_ low = 240 K) but not detected.
Despite our detections of NaCl and KCl, Al [35] Cl was not detected.
However, the only line in the ground vibrational state of Al [35] Cl fell
in the less sensitive Band 3 data and could be blended with [34] SO 2 .
In the case of Al [37] Cl, one line in the ground vibrational state fell in
each of the Band 3 and 6 observations. Neither is detected above the

noise.

AlF, which was detected alongside AlCl towards W Aql
(Danilovich et al. 2021) and has been seen towards various oxygenrich AGB stars (Saberi et al. 2022; Wallström et al. 2024), was not
detected towards OH 30.1 −0.7. This is despite a line in the ground
vibrational state being covered by our Band 6 observations. The
chemistry behind AlF is not yet fully understood (see Danilovich
et al. 2021, for a more extended discussion), but it seems to not be
directly linked to the other metal halides (i.e. NaCl and KCl) that are
so conclusively detected towards OH 30.1 −0.7.
SiN and SiC were identified by Van de Sande & Millar (2022) as
tracers of a UV-emitting companion star, along with NS. Although
NS was detected for OH 30.1 −0.7, SiN was not covered in our
observations, and two lines of SiC were covered in Band 6 but not

detected above the noise.


**APPENDIX D:** **PREVIOUS OBSERVATIONAL STUDIES OF**

**OH 30.1** − **0.7**



The study of rotational CO lines towards OH 30.1 −0.7 has been
hampered by contamination along its line of sight, as discussed in
Sect. 2.4 (see also De Beck et al. 2010), mainly originating from
the massive star-forming region W43, located around 1.6 kpc behind
OH 30.1 −0.7. The observations taken with APEX and JCMT shown

in Fig. B1 are too contaminated to allow any meaningful study of
the star and, indeed, a determination of the mass-loss rate was not
carried out by De Beck et al. (2010) for this reason. The IRAM 30m
telescope has a smaller HPBW and hence appears to suffer less from
ISM contamination, especially for the CO _𝐽_ = 2 − 1 line, but it is
clear from our ALMA observations, especially from inspection of
the channel maps (Figs. 3 and A6) that there is unavoidable contamination directly along the line of sight to OH 30.1 −0.7. Even though
a lot of this is resolved out by ALMA, some elements of the contami

6


4


2


0


2


4


66


4


2


0


2


4


66


4


2


0


2


4


66


4


2


0


2


4


66


4


2


0


2


4


6



|68 .8 km/s|68 .8 km/s|71 .3 km/s|71 .3 km/s|73 .9 km/s|73 .9 km/s|76 .4 km/s|76 .4 km/s|79 .0 km/s|79 .0 km/s|
|---|---|---|---|---|---|---|---|---|---|
|81.5 km/s|81.5 km/s|84.1 km/s|84.1 km/s|86.6 km/s|86.6 km/s|89.1 km/s|89.1 km/s|91.7 km/s|91.7 km/s|
|94.2 km/s|94.2 km/s|96.8 km/s|96.8 km/s|99.3 km/s|99.3 km/s|101.8 km/s|101.8 km/s|104.4 km/s|104.4 km/s|
|106.9 km/s|106.9 km/s|109.5 km/s|109.5 km/s|112.0 km/s|112.0 km/s|114.5 km/s|114.5 km/s|117.1 km/s|117.1 km/s|
|119.6 km/s|119.6 km/s|122.2 km/s|122.2 km/s|124.7 km/s|124.7 km/s|127.3 km/s|127.3 km/s|129.8 km/s|129.8 km/s|


6 4 2 0 2 4 **6**

RA offset [arcsec]



_The salty emission of OH 30.1_ − _0.7_ 27


0.10





4 2 0 2 4 **6**

RA offset [arcsec]



4 2 0 2 4 **6**

RA offset [arcsec]



4 2 0 2 4 **6**

RA offset [arcsec]



4 2 0 2 4 6

RA offset [arcsec]



0.08


0.06


0.04


0.02


0.00



**Figure A5.** Channel maps for CO _𝐽_ = 2 − 1 towards OH 30.1 −0.7, as observed with the more extended ALMA configuration. The thicker white contours are
drawn at levels of 10, 30, 50, 70, 100, 150, 200, 300, and 500 _𝜎_, the thinner grey contours at levels of 3 and 5 _𝜎_, and the dashed cyan contours at levels of −3
and −5 _𝜎_ . The red cross indicates the position of the continuum peak. The velocity of each channel is shown in the top right corner of each panel and the beam
is shown as a white ellipse in the bottom left corners. North is up and east is left. Note that although some interstellar contamination has been resolved out by
ALMA, a significant amount remains, especially for channels with velocities lower than 100 km s [−][1] .



nating molecular cloud cannot be avoided owing to the small angular
sizes of dense elements, comparable in size to the OH 30.1 −0.7 CO
envelope extent. Giant molecular clouds are generally expected to
be relatively cold, so they are brighter in the lower-energy CO transitions. However, massive star-forming clumps have been shown to
also exhibit high- _𝐽_ CO lines (e.g. Hoang et al. 2023). Without spatially resolved observations for all studied CO transitions, we cannot
completely rule out contamination in any CO towards OH 30.1 −0.7.



**D1** **Forensic astronomy**


Through a careful examination of past catalogues and other observations of OH 30.1 −0.7, we have determined that there has historically
been some uncertainty in the precise position of this star. Our ALMA
continuum observations are of high astrometric accuracy (see Table
1) and represent the best measured position for OH 30.1 −0.7. Some
examples of past uncertainties are detailed below.


The study of Justtanont et al. (2013) included the IRAM observations shown in Fig. B1 and two higher-energy CO lines observed with
APEX, _𝐽_ = 7 − 6 and _𝐽_ = 4 − 3. Both of these higher-energy lines


MNRAS **000**, 1–29 (2023)

28 _Danilovich et al_

















0.200


0.175


0.150


0.125


0.100


0.075


0.050


0.025


0.000


|68 .7 km/s|68 .7 km/s|71 .2 km|/s 73 .7 k|m/s 76 .3 km|76 .3 km|/s 78 .8 km/s|
|---|---|---|---|---|---|---|
|81.4 km/s|81.4 km/s|83.9 km|/s<br>86.5 k|m/s<br>89.0 km|89.0 km|/s<br>91.5 km/s|
|94.1 km/s|94.1 km/s|96.6 km|/s<br>99.2 k|m/s<br>101.7 km|101.7 km|/s<br>104.2 km/s|
|106.8 km/s|06.8 km/s|109.3 km|/s<br>111.9 k|m/s<br>114.4 km|114.4 km|/s<br>116.9 km/s|
|119.5 km/s|19.5 km/s|122.0 km|/s<br>124.6 k|m/s<br>127.1 km|127.1 km|/s<br>129.7 km/s|



**Figure A6.** Channel maps for CO _𝐽_ = 1 − 0 towards OH 30.1 −0.7. The contours are drawn at levels of 3, 5, 10, 30, 50, and 100 _𝜎_ and the red cross indicates
the position of the continuum peak. The velocity of each channel is shown in the top right corner of each panel and the beam is shown as a white ellipse in the
bottom left corners. North is up and east is left. Note that there is significant interstellar contamination for channels with velocities lower than 100 km s [−][1] .



were not detected above the noise but also do not exhibit significant
contamination, which is somewhat perplexing, since the _𝐽_ = 9−8 and
_𝐽_ = 5 − 4 lines were clearly detected by _Herschel_ /HIFI (with some
possible contamination seen in _𝐽_ = 5 − 4, see Fig. 10 in Justtanont
et al. 2013).


To investigate this conundrum we checked the original observations discussed above and plot the HPBW and right ascension and
declination (RA and Dec) of these observations in Fig. D1. We also
checked various catalogues and past observations for the coordinates
listed for OH 30.1 −0.7 and compared them with the RA and Dec
we find for the continuum peak in this work (based on the Band 6
extended continuum, see Table 1). The majority of the listed coordinates for this star fall within ≲ 1 [′′] of our continuum peak, including
those from the Wide-field Infrared Survey Explorer (WISE, Cutri


MNRAS **000**, 1–29 (2023)



et al. 2012), the General Catalogue of Variable Stars (GCVS 5.1,
Samus’ et al. 2017), the Infrared Space Observatory (ISO, Kessler
et al. 1996) and from the aforementioned IRAM, HIFI (Justtanont
et al. 2013), and APEX ( _𝐽_ = 2 − 1, this work, ID:O-0102.F-9301B)

observations. The JCMT CO _𝐽_ = 2 − 1 and _𝐽_ = 3 − 2 observations

(De Beck et al. 2010) are offset from the ALMA continuum peak by
about 7 [′′], meaning that the telescope beam at _𝐽_ = 2 − 1 mostly covers the extent of the emission observed with ALMA, but the smaller
_𝐽_ = 3 − 2 misses a significant portion of the AGB emission.


This is illustrated in Fig. D1, where we approximate the ALMA
CO emission as a circle of radius 3 _._ 5 [′′] centred on the continuum peak
and plot various telescope beams and their pointings. The relatively
small APEX beams covering the CO _𝐽_ = 4 − 3 and _𝐽_ = 7 − 6 lines

3


2


1


0


1


2


33


2


1


0


1


2


33


2


1


0


1


2


33


2


1


0


1


2


3



|74 .7 km/s|74 .7 km/s|77 .1 km/s|77 .1 km/s|79 .5 km/s|79 .5 km/s|81 .9 km/s|81 .9 km/s|84 .3 km/s|84 .3 km/s|
|---|---|---|---|---|---|---|---|---|---|
|86.7 km/s|86.7 km/s|89.1 km/s|89.1 km/s|91.5 km/s|91.5 km/s|93.9 km/s|93.9 km/s|96.3 km/s|96.3 km/s|
|98.7 km/s|98.7 km/s|101.1 km/s|101.1 km/s|103.5 km/s|103.5 km/s|105.9 km/s|105.9 km/s|108.3 km/s|108.3 km/s|
|110.7 km/s|110.7 km/s|113.1 km/s|113.1 km/s|115.5 km/s|115.5 km/s|117.9 km/s|117.9 km/s|120.3 km/s|120.3 km/s|


3 2 1 0 1 2 **3**

RA offset [arcsec]



_The salty emission of OH 30.1_ − _0.7_ 29


0.016


0.014


0.012


0.010





2 1 0 1 2 **3**

RA offset [arcsec]



2 1 0 1 2 **3**

RA offset [arcsec]



2 1 0 1 2 **3**

RA offset [arcsec]



2 1 0 1 2 3

RA offset [arcsec]



0.008


0.006


0.004


0.002


0.000



**Figure A7.** Channel maps for SO 2 _𝐽_ _𝐾_ _𝑎_ _,𝐾_ _𝑐_ = 14 0 _,_ 14 → 13 1 _,_ 13 at 244.254 GHz towards OH 30.1 −0.7. The contours are drawn at levels of 3, 5, and 10 _𝜎_ and
the red cross indicates the position of the continuum peak. The velocity of each channel is shown in the top right corner of each panel and the beam is shown as
a white ellipse in the bottom left corners. North is up and east is left.


are centred on a point ∼ 17 [′′] from the ALMA continuum peak and,
as shown in Fig. D1, do not overlap with the CO envelope at all.
We also note that some older catalogues, such as the Infrared Astronomical Satellite (IRAS, Helou & Walker 1988) and the Revised
Air Force Geophysical Laboratory Infrared Sky Survey (RAFGL,
Price & Murdock 1983), list coordinates even more significantly offset from our continuum peak (by ∼ 25 [′′] for both IRAS and RAFGL),
most likely owing to resolution limitations. The coordinates listed in
the study of Heske et al. (1990), discussed in Sect. 4.2.1, agree with
our position to within 0.33 [′′] .


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–29 (2023)

30 _Danilovich et al_


4


2


0


2


4





0.006


0.005


0.004


0.003


0.002


0.001


0.000



0.001


80 85 90 95 100 105 110 115 120
Velocity [km/s]

|Col1|0.|
|---|---|
||0<br>0<br>0<br>0<br>0<br>0<br>0|
|||



**Figure A8.** Position-velocity diagram for NS _𝑒_ towards OH 30.1 −0.7. The
diagram was constructed for line passing through the continuum peak at an
angle of 69 [◦] east from north (as shown in Fig. 9). The contours are drawn at
levels of 3 _𝜎_ and the red cross indicates the position and systemic velocity of

the AGB star.



37





36


35


34


33


32


31

0 250 500 750 1000 1250 1500 1750 2000
Upper level energy [K]


**Figure** **A9.** Population diagrams for Na [35] Cl (blue) and K [35] Cl (pink). The
lines give the best linear fit to the data. Average gas temperatures are given
in the legend and are close to 600 K for both molecules. The source averaged
column densities are 1 _._ 4 × 10 [12] cm [−][2] and 1 _._ 6 × 10 [11] cm [−][2] for Na [35] Cl and
K [35] Cl, respectively.


MNRAS **000**, 1–29 (2023)

_The salty emission of OH 30.1_ − _0.7_ 31























**Figure B1.** ALMA observations of CO towards OH 30.1 −0.7 compared with APEX, JCMT and IRAM 30m observations of the same lines. The legends give
the HPBW, _𝜃_, for the single-dish data, and the diameter of the circular extraction apertures, D, for the ALMA data. TE refers to data observed with only the
ALMA extended configuration. The single-dish observations show significant line contamination from sources other than the AGB stars. The left and middle
panels show CO ( _𝐽_ = 2 − 1) with the left panel having a flux scale that allows the CO emission to be clearly seen, while the middle panel has a flux scale that
shows the full range of the ISM contamination at velocities ≲ 100 km s [−][1] . The right panel shows CO ( _𝐽_ = 1 − 0).



2.838


2.839


2.840


2.841



2.842


2.843





2.844


2.845



282.178 282.176 282.174 282.172 282.170 282.168

RA [deg]



**Figure D1.** Location on the sky of OH 30.1 −0.7 and the pointings of various observations targeting the star. The continuum peak based on our observations
is plotted as a purple star and a purple shaded circular region with a radius of 3 _._ 5 [′′] represents the extent of the CO _𝐽_ = 2 − 1 (see Fig. 3). The coordinates
and HPBW of various other observations are also plotted (see text for references). Note that the centres of the APEX CO (2-1) and IRAM beams are at the
same coordinates, as are the HIFI observations, the large beams for which are not plotted. Not shown are the coordinates given in the WISE, ISO and GCVS
catalogues, which are all within ∼ 1 [′′] of the ALMA continuum peak.


MNRAS **000**, 1–29 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[1]",
  "value": "IRAM 30m CO J=2-1 and J=1-0 spectra, and mass-loss rate of 1.8e-4 M_sun/yr",
  "failed_quote": "If we take the mass-loss rate of 𝑀  = 1 . 8 × 10 −4 M ⊙ yr −1 computed by Justtanont et al. (2013), and assume it has not changed over the past 2800 years, we calculate that 0 . 5 M ⊙ has been ejected"
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Fit a soft parabola profile to unblended lines to obtain central velocity and line width, integrate line fluxes over a velocity range a few km/s wider than the fitted width, average central velocities for systemic velocity, and measure full CO expansion velocity from >30 sigma detections in channel maps.",
  "failed_quote": "We fit a soft parabola line profile function (Olofsson et al. 1993) defined as 𝐹 ( 𝜐 ) = 𝐹 0 1 − 𝜐 − 𝜐 cent 𝜐 w 2 𝛾 /2 , (1)"
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "Power-law radial temperature profile T(r) = T_*(r/R_*)^-epsilon; constant expansion velocity of 23 km/s at distance 3.9 kpc",
  "failed_quote": "If we take half the maximum velocity extent in the CO channel maps as the wind speed (23 km s −1 ) and consider the well-constrained distance of 3.9 kpc, we find that it took around 2800 years for the gas to expand to 3 . 5 ′′ (2 × 10 17 cm = 14000 au) from the star."
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "Dynamical age of the current high mass-loss phase = 2800 yr",
  "failed_quote": "If we take half the maximum velocity extent in the CO channel maps as the wind speed (23 km s −1 ) and consider the well-constrained distance of 3.9 kpc, we find that it took around 2800 years for the gas to expand to 3 . 5 ′′ (2 × 10 17 cm = 14000 au) from the star."
 },
 {
  "path": "claims[2].evidence[2]",
  "value": "High mass-loss commenced around 2800 years ago (longer than classical superwind predictions), and any earlier mass loss at a rate <= 2e-5 M_sun/yr would have already photodissociated at smaller radii.",
  "failed_quote": "We also conclude that 𝑀  ≤any2 ×earlier 10 −5 periodM ⊙ yr − of 1 ) lowerwouldmassnot belossdetectable(with a mass-lossin light ofratethe recent high mass loss."
 }
]
```
