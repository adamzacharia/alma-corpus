# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.535.1533B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–42 (2024) Preprint 23 October 2024 Compiled using MNRAS L [A] TEX style file v3.0

## A Novel high- 𝑧 submm Galaxy Efficient Line Survey in ALMA bands 3 **through 8 - An ANGELS Pilot**


T. J. L. C. Bakx [1] _[,]_ [2] _[,]_ [3] _[★]_, A. Amvrosiadis [4], G. J. Bendo [5], H. S. B. Algera [6] _[,]_ [3], S. Serjeant [7], L. Bonavera [8] _[,]_ [9],
E. Borsato [10], X. Chen [3], P. Cox [11], J. González-Nuevo [8] _[,]_ [9], M. Hagimoto [3], K. C. Harrington [12],
R. J. Ivison [13] _[,]_ [14] _[,]_ [15] _[,]_ [16], P. Kamieneski [17] L. Marchetti [18] _[,]_ [19], D. A. Riechers [20], T. Tsukui [21] _[,]_ [16],
P. P. van der Werf [22], C. Yang [1], J. A. Zavala [3], P. Andreani [23], S. Berta [24], A. R. Cooray [25], G. De Zotti [10],
S. Eales [26], R. Ikeda [27] _[,]_ [28], K. K. Knudsen [1], I. Mitsuhashi [3], M. Negrello [26], R. Neri [24],
A. Omont [11], D. Scott [29], Y. Tamura [3], P. Temi [30], and S. A. Urquhart [7] .
_Affiliations can be found after the references_


Accepted 2024 October 21. Received 2024 October 21; in original form 2024 June 28


**ABSTRACT**

We use the Atacama Large sub/Millimetre Array (ALMA) to efficiently observe spectral lines across Bands 3, 4, 5, 6, 7, and
8 at high-resolution (0 [′′] _._ 5 – 0 [′′] _._ 1) for 16 bright southern _Herschel_ sources at 1 _._ 5 _<_ _𝑧<_ 4 _._ 2. With only six and a half hours
of observations, we reveal 66 spectral lines in 17 galaxies. These observations detect emission from CO (3–2) to CO(18–17),
as well as atomic ([C i](1-0), (2-1), [O i] 145 _𝜇_ m and [N ii] 205 _𝜇_ m) lines. Additional molecular lines are seen in emission
(H 2 O and H 2 O [+] ) and absorption (OH [+] and CH [+] ). The morphologies based on dust continuum ranges from extended sources to
strong lensed galaxies with magnifications between 2 and 30. CO line transitions indicate a diverse set of excitation conditions

∼
with a fraction of the sources ( 35%) showcasing dense, warm gas. The resolved gas to star-formation surface densities vary
strongly per source, and suggest that the observed diversity of dusty star-forming galaxies could be a combination of lensed,
compact dusty starbursts and extended, potentially-merging galaxies. The predicted gas depletion timescales are consistent with
100 Myr to 1 Gyr, but require efficient fueling from the extended gas reservoirs onto the more central starbursts, in line with
the Doppler-shifted absorption lines that indicate inflowing gas for two out of six sources. This pilot paper explores a successful
new method of observing spectral lines in large samples of galaxies, supports future studies of larger samples, and finds that the
efficiency of this new observational method will be further improved with the planned ALMA Wideband Sensitivity Upgrade.


**Key words:** general – galaxies: evolution - submillimetre: galaxies – galaxies: high-redshift



**1** **INTRODUCTION**


The discovery of a population of dusty galaxies – called either submm galaxies (SMGs; Smail et al. 1997; Hughes et al. 1998; Blain
et al. 2002) or dusty star-forming galaxies (DSFGs; Casey et al.
2014) – showed that more than half of the star-formation in the
early Universe was shrouded in dust. With total infrared luminosities
exceeding several times 10 [12] L ⊙, the star-formation rates in these
SMGs and DSFGs (hereafter, we use DSFGs for simplicity) approach
the stability limit of 1000 M ⊙ year [−][1] and may even exceed this
limit (Andrews & Thompson 2011; Fudamoto et al. 2017; RowanRobinson et al. 2018). These intense star-formation rates – enough
to build a large galaxy in only 0.1 Gyr – suggest that these may be
the ancestors of present-day early-type galaxies (Eales et al. 1999;
Lilly et al. 1999). Evidence of this evolutionary pathway of DSFGs
to quenched elliptical galaxies is mounting, given their high stellar
masses (Hainline et al. 2011; Aravena et al. 2016; Long et al. 2023;
Smail et al. 2023), high specific star-formation rates (Straatman et al.


_★_ E-mail: tom.bakx@chalmers.se


© 2024 The Authors



2014; Spilker et al. 2016; Glazebrook et al. 2017; Schreiber et al.
2018; Merlin et al. 2019) and location in overdense regions (Blain
et al. 2004; Weiß et al. 2009; Hickox et al. 2012). However, the DSFG
population appears diverse (e.g., Hagimoto et al. 2023), and because
the types of galaxies studied in this paper are very rare (a few /
deg [2] for _>_ 10 [12] _[.]_ [5] L ⊙ ), hydrodynamical models struggle to include a
large enough volume to simulate these galaxies accurately to test the
evolutionary pathways of these DSFGs (e.g., Narayanan et al. 2015).
Observations of large numbers of DSFGs are thus the only direct
way of understanding this population.


The _Herschel_ Space Observatory increased the number of known
DSFGs from hundreds to over half a million sources through several
large-area surveys. In these surveys, the SPIRE instrument (Griffin
et al. 2010) observed these large areas at the peak of the redshifted
DSFG dust spectra without the hindering effects of the atmosphere.
The total mapping area of _Herschel_ surveys is over one thousand
square degrees, with 660 deg [2] _Herschel_ ATLAS (H-ATLAS; Eales
et al. 2010) and the 380 deg [2] _Herschel_ Multi-tiered Extragalactic
Survey (HerMES; Oliver et al. 2012) and the _Herschel_ Stripe 82
Survey (HerS; Viero et al. 2014) accounting for the bulk of the area

2 _Bakx et al._


**Figure** **1.** The 88 _Herschel_ Bright Sources (Bakx et al. 2018, 2020b) in the 285 square degree South Galactic Pole field (85 observed in the BEARS survey;
Urquhart et al. 2022). Observations within ten degrees on the sky can be done in rapid succession, without the need for additional calibration. Here we show
the five different regions across the SGP field indicated with different symbols, with the central field used for Pilot observations ( _star-symbols_ ), while the four
remaining fields ( _upward- and downward triangles, hexagons and diamonds_ ) are left for subsequent follow-up. Note that four sources were excluded at the time
of observation ( _crosses_ ). The circle with a radius of ∼ 7 degrees indicates the typical size for sources that the ALMA Observing Tool predicts can be observed
with only a single calibration step for ALMA configuration schedules C43-6 and smaller.



increase (Shirley et al. 2021). The vast increase in survey area (at
the time, ground-based surveys only covered ∼1 deg [2] in total) also
meant that _Herschel_ discovered many more of the most extreme
DSFGs. This has been complemented by observations in the mm
regime, such as the South Pole Telescope survey, which revealed
around a hundred sources that are also at high redshift from over
2500 deg [2] (Reuter et al. 2020).


To examine the nature of these extreme high-redshift sources, it
is crucial to perform detailed studies characterizing the conditions
of the Inter-Stellar Medium (ISM) conditions seen through resolved
spectral line observations (e.g., Hodge et al. 2019). Recent highresolution follow-up studies of H-ATLAS sources, to use one survey
as an example, have revealed 14 sources with 4 _<_ _𝑧<_ 6 _._ 5 with starformation rates up to 8,000 M ⊙ year [−][1], well over the _maximal star-_
_burst_ limit (Fudamoto et al. 2017; Zavala et al. 2018; Montaña et al.
2021), and the discovery of a source at _𝑧_ = 4 _._ 002 which when followed up with Atacama Large sub/Millimetre Array (ALMA) turned
out to be the core of a proto-cluster (Oteo et al. 2018), with its large
scale environment forming stars at a rate of several tens of thousands
of solar masses per year.


Given the large beam size of single-dish telescopes, high-redshift
sub-mm astronomy was often jokingly referred to as _blobology_ prior
to the advent of interferometer facilities such as ALMA, CARMA,
NOEMA (Northern Extended Millimeter Array; previously PdBI)
and the SMA. These interferometers were able to reveal large numbers of spectral lines of individual sources with NOEMA (e.g., Yang
et al. 2023), as well as stunning lensing arcs and Einstein rings (e.g.,
Dye et al. 2015, 2018; Spilker et al. 2016) while targeting spectral
lines at high resolution with ALMA (e.g., Rizzo et al. 2020). Particularly since the advent of large samples of DSFGs with robust redshifts
(Reuter et al. 2020; Urquhart et al. 2022; Cox et al. 2023), spectroscopic follow-up studies are the key next step in a full characterisation
of this extreme population. Unfortunately, while interferometers are
powerful instruments, the modest bandwidths currently available at
ALMA mean that spectral line observations require dedicated tunings for every source, resulting in either runaway observation times
or statistically-insignificant samples. Consequently, a comprehensive high-resolution spectroscopic study of complete bright _Herschel_
samples, or for that matter any survey from large-area mapping studies, is beyond the scope of current instrumentation. The Wideband


MNRAS **000**, 1–42 (2024)



Sensitivity Upgrade (WSU; Carpenter et al. 2023) will provide some
relief, but as we will show, even its most optimistic goals can benefit
from the methods detailed in this exploratory paper.
To break the current paradigm – i.e., long observations or small
samples – this paper attempts short snapshot-style observations with
ALMA (similar to Dye et al. 2018; Amvrosiadis et al. 2018) while
targeting as many spectral lines as possible: **A N** ovel high- _𝑧_ submm
**G** alaxy **E** fficient **L** ine **S** urvey (ANGELS; Appendix Figure F1). We
describe this technique in Section 2, together with the definition of
the sample of galaxies, and the ALMA data reduction steps. We
describe the results of the observations, both for continuum and line
measurements, in Section 3. We find lensing morphology for around
half of the sample, and we report the lensing and ancillary data
properties in Section 4. We place the line properties into context of
the literature in Section 5. The resolved studies of ANGELS sources

are discussed in Section 6. We collate an overview of the nature of

the ANGELS sources, as became apparent by these observations,
in Section 7. We evaluate this efficient line survey in Section 8,
where we also detail the inevitable caveats and look into the future

of surveys including the benefits of the WSU (Carpenter et al. 2023).
Conclusions are summarized in Section 9. Throughout this paper,
we assume a flat Λ-CDM cosmology with the best-fit parameters
derived from the _Planck_ results (Planck Collaboration et al. 2020),
which are Ω m = 0 _._ 315, Ω Λ = 0 _._ 685 and _ℎ_ = 0 _._ 674.


**2** **OBSERVATIONS**


We target a group of sources within 10 degrees on the sky using rapid
two minute snapshots across Bands 3 through 8 to test the viability
of a rapid line survey with ALMA across the available bands with
the best atmospheric transmission. Prior high-redshift observations
with ALMA were limited to observations that have to retune the local

oscillator and subsequently repeat the calibration observations. This
approach results in large overheads (∼ 20 − 30 min. per target) and
requires a Large Program before one hundred lines are reached. Our
method instead asks: _what_ _specific_ _tuning_ _would_ _allow_ _us_ _to_ _target_
_as_ _many_ _spectral_ _lines_ _as_ _possible?_ The purpose of this paper is to
test the usefulness of a snapshot-style line survey with bandwidths
optimised to cover as many lines as possible. In Section 2.1, we

describe the selected sources, and detail the ANGELS method in
Section 2.2, before describing the data reduction steps in Section 2.3.


**2.1** **Target selection**


The group of sources is selected from the 285 square degree South
Galactic Pole (SGP) field from the H-ATLAS survey (Eales et al.
2010). The field is centered on RA, DEC = 23:24:46, −33:00:00,
and is shown in Figure 1 (Valiante et al. 2016; Ward et al. 2022).
In total, this field contains 88 bright high-redshift _Herschel_ sources
(5 _>_ _𝑧_ phot _>_ 2 and 350 _>_ S 500 _>_ 80 mJy; Bakx et al. 2018, 2020b),
of which 65 sources have one or more ALMA-resolved sources with

spectroscopic redshifts (which increased to 68 sources by including
the spectroscopic redshifts identified by this program). These sources
represent a larger sample of roughly the 300 brightest high-redshift
objects (Nayyeri et al. 2016; Negrello et al. 2017; Bakx et al. 2018,
2020b) selected from a thousand square degrees of _Herschel_ surveys, and typically have slightly lower observed luminosities than the
majority-lensed SPT- (Reuter et al. 2020, _𝜇𝐿_ IR = 4 _._ 4 × 10 [13] _𝐿_ ⊙ ) and
_Planck_ -selected galaxies (Berman et al. 2022, _𝜇𝐿_ IR = 1 _._ 2 × 10 [14] _𝐿_ ⊙ )
from ∼ 2500 square degrees and an all-sky survey, respectively.
Meanwhile, these _Herschel_ sources have higher apparent luminosities than the more abundant, typically-unlensed SMGs from groundbased sub-mm observations (e.g., Garratt et al. 2023), that are selected from surveys of up to ∼ 10 square degrees. The Bright Extragalactic ALMA Redshift Survey (BEARS) provided the bulk of the
spectroscopic redshifts across 62 _Herschel_ sources (Urquhart et al.
2022), for a total of 71 ALMA-resolved galaxies with average lensed
infrared luminosities of _𝜇𝐿_ IR = 4 _._ 0×10 [13] _𝐿_ ⊙ . This survey efficiently
used Band 3 and 4 to derive robust spectroscopic redshifts using multiple Carbon-monoxide (CO) and atomic carbon ([C i]) lines (Bakx
& Dannerbauer 2022); and in addition, the data enabled subsequent
marginally-resolved studies of the dust continuum (Bendo et al. 2023)
and molecular gas (Hagimoto et al. 2023).
The observations in this pilot program aimed to target a group of
sources close on the sky ( _<_ 10 deg) with spectroscopic redshifts.
We identified this group of sources using the ALMA Observing
Tool, which split the 88 sources across six groups on the sky that
can each be observed within a single calibration, i.e., all sources
that are closer together than 10 degrees on the sky. The group that
was selected ( _𝑅𝐴, 𝐷𝐸𝐶_ = 00:00:00, −33:29:00) contains most fields
with spectroscopic redshifts; thirteen out of sixteen fields had at least
one source with a spectroscopic redshift, ranging between _𝑧_ = 1 _._ 536
and 4 _._ 182 with a median value of _𝑧_ ¯ = 2 _._ 843, see Table 1. The
average infrared luminosities of these sixteen fields are on average
_𝜇𝐿_ IR = 4 _._ 2×10 [13] _𝐿_ ⊙ based on the luminosities documented in (Bakx
et al. 2018, 2020b) [1], and thus these fields are representative of the
larger BEARS and HerBS samples. In total, 26 resolved galaxies exist
within these sixteen fields. An additional four fields were not targeted
in these initial ANGELS observations, although they were within the
range of this field (shown as crosses in Figure 1). Only one line was
detected in the spectra of the three remaining sources (HerBS-87,
HerBS-104, and HerBS-170), and it was not possible to determine
robust redshifts for these targets. The additional observations from
ANGELS allowed us to cut through this redshift degeneracy and
measure redshifts for these three sources (see Section 8.1).


1 This value is slightly higher than the luminosities from a re-fit using the
spectroscopic redshifts with the Eyelash template (e.g. Ivison et al. 2016) of
2 _._ 9 × 10 [13] _𝐿_ ⊙, which still comparable to the average luminosity of the BEARS
sample.



_Efficient high-resolution line survey_ 3


**Table 1.** Sources targeted by ANGELS Pilot


Source _𝑧_ RA Dec ΔV [km/s]


HerBS-21AB 3.323 23:44:18.112 −30:39:36.58 550 ± 110

HerBS-22A 3.050 00:26:25.000 −34:17:38.22 680 ± 150
HerBS-22B [‡] – 00:26:25.560 −34:17:23.30 –

HerBS-25 2.912 23:58:27.505 −32:32:45.05 210 ± 40

HerBS-36 3.095 23:56:23.079 −35:41:19.64 550 ± 80

HerBS-41A 4.098 00:01:24.796 −35:42:11.15 680 ± 100
HerBS-41B [‡] – 00:01:23.240 −35:42:10.80 –
HerBS-41C [‡] – 00:01:25.820 −35:42:18.00 –

HerBS-42A 3.307 00:00:07.458 −33:41:03.07 640 ± 70

HerBS-42B 3.314 00:00:07.428 −33:40:55.82 490 ± 90
HerBS-42C [‡] – 00:00:07.050 −33:41:03.40 –

HerBS-81A 3.160 00:20:54.739 −31:27:50.96 670 ± 200

HerBS-81B 2.588 00:20:54.201 −31:27:57.49 650 ± 190

HerBS-86 2.564 23:53:24.569 −33:11:11.93 460 ± 100
HerBS-87 [†] 2.059 00:25:33.683 −33:38:26.21 370 ± 110

HerBS-93 2.402 23:47:50.443 −35:29:30.13 640 ± 160
HerBS-104A [‡] – 00:18:39.470 −35:41:48.00 –
HerBS-104B [†] 1.536 00:18:38.851 −35:41:33.09 430 ± 130

HerBS-106A 2.369 00:18:02.467 −31:35:05.17 500 ± 170
HerBS-106B [‡] – 00:18:01.104 −31:35:08.00 –

HerBS-155A 3.077 00:03:30.644 −32:11:35.00 500 ± 150
HerBS-155B [‡] – 00:03:30.060 −32:11:39.30 –

HerBS-159A 2.236 23:51:21.750 −33:29:00.53 280 ± 80

HerBS-159B 2.236 23:51:22.363 −33:29:08.14 330 ± 90
HerBS-170 [†] 4.182 00:04:55.445 −33:08:12.85 680 ± 180

HerBS-184 2.507 23:49:55.661 −33:08:34.48 320 ± 40


**Notes:** Col. 1: Source name. In the case of source multiplicity, we denote
the brightest component with the letter A, and subsequent letters mark the
source sensitivity. Col. 2: Spectroscopic redshift from sub-mm observations.
Col. 3: Right Ascension in [hms] units. Col. 4: Declination in [dms] units.
Col. 5: Velocity-width in [km/s] units from unresolved ALMA observations
(Urquhart et al. 2022). [†] The redshifts of these sources are confirmed using
the ANGELS observations, and are based on the lines included in this paper,
see Section 8.1. [‡] These sources do not have spectroscopic redshifts and are
not completely covered by the primary beam across Bands 3 through 8. If the
field only has one galaxy with a spectroscopic redshift, we drop the sub-index
(i.e., A, B etc.) throughout the paper for legibility reasons. These sources are
shown in Appendix B.


**2.2** **The ANGELS method**


The number density of sources allowed the use of short snapshots
(≈ 2 min) with only a single ∼ 20 − 30 min. calibration step to
reduce the overheads typically associated with line surveys (∼one
calibration per targeted line). As a result, each observation required
roughly one hour per band. This style of snapshot observation is not
unique (e.g., Amvrosiadis et al. 2018 showed short snapshots can
reveal the morphology of 15 lensed galaxies with only 2 min. of onsource time), however this ANGELS pilot project explicitly focuses
to include as many spectral lines as possible, while covering a much
larger range of frequencies between Bands 3 through 8. Since we
knew the redshifts of all of our targets (except for HerBS-87, -104
and -170, at the time of observing), we could use the cosmological
frequency shift of the Universe as our spectrometer and evaluate the
coverage of the spectral windows at the rest-frame frequencies of
all of the _Herschel_ galaxies (see Figure 2). The sources are shown
by their spectral windows shifted to their restframe frequency, and
any lines within the spectral windows are marked as circles in the
bottom panel. Typically, Bands 3 and 4 are able to target carbonmonoxide (CO) and atomic Carbon ([C i] at 492.161 GHz) emission
lines. Bands 5, 6 and 7 are sensitive to molecular lines such as


MNRAS **000**, 1–42 (2024)

4 _Bakx et al._


water, and absorption lines including CH [+] and OH [+] . The highestfrequency Band 8 is able to target atomic emission lines, such as [O i]
(2060 GHz) and [N ii] (1461 GHz).
This shared calibration step is only enabled for sources within
10 deg. on the sky for configurations below ∼ 3 km (C43-6 or lower),
while for longer baselines this condition is more stringent ( _<_ 1 deg.).
This places a rough limit on the maximum resolution between 0 [′′] _._ 3
and ∼ 0 [′′] _._ 07 for Bands 3 through 8, respectively. Given the spatial
extent of DSFGs, any higher resolution could run into problems with
maximum resolvable scales and the dilution of emission across the

increasing number of beams.
The ALMA observations were carried out in Cycle 8 between
November 2021 and July 2022 (Program ID: 2021.1.01628.S; P.I.
T. Bakx). Table 2 shows the exact tuning frequencies used in this
ANGELS pilot, together with the observing depth across the entire
image (i.e., the continuum depth), and across 35 km/s bins. A quasar
was used for the complex gain calibration (J2359-3133), while another quasar was used for bandpass calibration (J2258-2758). We
found this exact set-up of the spectral windows by parameterizing
each of the spectral set-ups of the bands by their starting frequency.
Appendix Figure A1 compares each potential tuning with ALMA to
the total number of lines that can be targeted. The bottom part of
the graph shows the atmospheric transmission, normalized between
0 and 1, to indicate the effect of tuning at this specific frequency. The
variability in the observable number of lines with frequency reveals
an important fact: _The_ _simple_ _act_ _of_ _optimizing_ _the_ _tuning_ _towards_
_the known spectroscopic redshifts can triple the number lines within_
_any snapshot program._


**2.3** **Data reduction**


All data were processed using the common astronomy software
applications (casa) package (McMullin et al. 2007; CASA Team
et al. 2022). The pipeline calibration of the visibility data were first
restored using the standard scripts from the ALMA Science Archive
and using casa version 6.2.1. After this, the data were imaged using
tclean. The continuum images were created with casa version 6.2.1,
while the image cubes were created with casa version 6.4.1.
We initially created image cubes binning the channels by a factor
of 16 to identify detectable spectral lines from each target within
each spectral window (corresponding to a channel width between
50 and 15 km/s between Bands 3 and 8, respectively). After this,
we subtracted the continuum from the visibility data for each field
and spectral window containing a detectable spectral line. We also
had spectral windows that covered spectral lines that were expected
to be present based on the redshifts of the individual targets from
Urquhart et al. (2022) but that were not detected. In these situations,
we identified all channels that lied within a 0.4 GHz region centred
on the expected frequency of the spectral line for each target as potentially containing line emission and used all channels not covering
the potential line emission to measure and subtract the continuum
from the visibility data. These continuum-subtracted image cubes
were then used for the final analysis. The channels in the visibility
data without the continuum subtraction that were identified as not

containing emission were used to create the final continuum images.
Natural weighting was used to create the continuum images, but
when creating the image cubes, we set the weighting to briggsbwtaper, which is a variant of Briggs weighting that makes adjustments
for variations in the beam size with frequency, and we set the robust
factor to 2, which is equivalent to natural weighting and which is best
for detecting faint emission in ALMA data. To further optimize the
images for the detection of faint line or continuum emission, we used


MNRAS **000**, 1–42 (2024)



the Hogbom deconvolver. Additionally, a _uv_ taper of 0.05 arcsec was
applied to remove noise with very high spatial frequencies. The channel width in the image cubes was adjusted to attempt to maximize the
peak signal-to-noise of the beam while preserving as much spectral
structure of the line as possible. The final images have pixel scales
that sample the full-width at half maxima (FWHM) of the beams by
at least 5×; the specific pixel scales and reconstructed beam sizes
are listed in Table 2. This table also lists the fields of view in the

ALMA images in each band, the maximum recoverable scales, and
the calibration uncertainties, which are based on information from
the ALMA Technical Handbook [2] (Cortes et al. 2023).


**3** **RESULTS**


The ANGELS observations resulted in a high-angular resolution
spectral perspective on sixteen Herschel galaxies, across the frequency range from 200 to 2000 GHz in the rest-frame. In this Section, we present the main results on the underlying dust continuum
(Section 3.1) and the line measurements (Section 3.2).


**3.1** **Continuum snapshots**


Figure 3 displays the dust continuum images for all the sources that
have complete coverage in Bands 3 through 8. We further present
sources separated beyond the primary beams of the higher-frequency
bands in Appendix Figure B1. The sources have starkly varying morphologies, with lensing structures such as (partial) Einstein rings
seen for HerBS-21, -22, -25, -36, -41A, -87, -104, and -155. HerBS21 has a much more complicated gravitational lensing morphology
when compared to the other sources, which are single galaxy-galaxy
lensed systems (see Section 7.1). Other sources are resolved into
bright single components, such as HerBS-42A and -B, -81A, -86,
-93, -170 and -184. HerBS-81B and -106 (and potentially -170) are
resolved into multiple components on the scale of _<_ 1 _._ 5 arcsec, and
were seen as individual clumps in the BEARS observations (discussed further in Section 7.2). Since the maximum recoverable scale
(MRS) is between 4 and 1.5 arcseconds for the ALMA observations
(see Table 2), we expect this to play little effect in the final imaging
quality.
Interestingly, HerBS-159A and -B are not seen in the imaging.
For these sources, we create tapered images in Figure 4 to see if
any emission of these 500 _𝜇_ m-bright sources is seen at these longer
wavelengths. Tapering reveals the dust emission in Bands 5 and
beyond. For HerBS-159A, the emission appears to be split across
several sources separated at ∼ 1 arcsec, while HerBS-159B appears
to be a single bright component. We discuss the significance of these
types of sources in Section 7.3.
The morphology of the ANGELS sources varies across the different bands, and provides a strong argument towards a multi-band
interpretation of dusty galaxies, particularly if only lower frequencies
are available. For example, even though the observations are at high
enough resolution in Bands 3 and 4, the lensing nature of HerBS-41A
remained unclear until the convincing arcs seen in Bands 7 and 8.
We provide the continuum spectral energy distribution fitting in a
subsequent paper (Bendo et al. in prep.) that will investigate the nature
of dust in these ANGELS sources. In this paper, we employ two methods for calculating the far-infrared luminosity, which are broadly in


2 Available from `[https://almascience.eso.org/](https://almascience.eso.org/documents-and-tools/cycle10/alma-technical-handbook)`
`[documents-and-tools/cycle10/alma-technical-handbook](https://almascience.eso.org/documents-and-tools/cycle10/alma-technical-handbook)` .

Flux density [arb.]



_Efficient high-resolution line survey_ 5


Flux density [arb.]



|Col1|Col2|Col3|CO(1−0)|
|---|---|---|---|
||||<br>|
||||~~CO (2~~~~_−_1)~~<br>~~CO (3~~~~_−_2)~~<br>~~CO (4~~~~_−_3)~~<br>~~CO (5~~~~_−_4)~~<br>CO(6_−_5)<br>~~[C i] 609~~~~_µm_~~|
||||<br>CO (7_−_6)<br>CO (8_−_7)<br>CO (9_−_8)<br><br>[C i] 370_µm_<br>~~H~~2~~O (2~~1_,_1 ~~_−_2~~0_,_2~~)~~<br>H2O (20_,_2_ −_11_,_1)<br>H2O (31_,_2_ −_30_,_3)<br>~~H2O (11~~~~_,_1~~~~_ −_00~~~~_,_0)~~<br>~~CH~~+ ~~(1~~~~_−_0)~~<br>~~OH+ (1~~0 ~~_−_0~~1~~)~~<br>~~OH+ (12~~~~_ −_01)~~<br>~~OH+ (11~~~~_ −_01)~~<br>H2O~~+~~<br>~~H2O+~~|
||||CO (10_−_9)<br>CO (11_−_10)<br>~~H2O (32~~~~_,_1~~~~_ −_31~~~~_,_2)~~<br>~~HF (1~~~~_−_0)~~|
||||~~CO (12~~~~_−_11)~~<br>~~N205~~|
||||~~CO (13~~~~_−_12)~~<br>~~CO (14~~~~_−_13)~~<br>~~[ ii] ~~~~_µm_~~<br>~~CH~~+ ~~(2~~~~_−_1)~~|
||||~~CO (15~~~~_−_14)~~<br>~~CO1615~~|
||||~~(~~~~_−_)~~<br>~~C ii158~~|
||||~~CO(17~~~~_−_16)~~<br> ~~_µm_~~|
||||<br>CO (18_−_17)<br>[O i] 145_µm_|
||||~~CO(19~~~~_−_18)~~|
||||<br>~~CO(20~~~~_−_19)~~|
|||||


**Figure 2.** _The top panel_ shows the rest-frame spectra of a typical dusty galaxy, assuming a two-body dust spectrum based on _Herschel_ observations (Pearson
et al. 2013) in conjunction with the spectral lines of a local ULIRG, in this case based on the line ratios of Arp220 by Rangwala et al. (2011). Most lines are
seen in emission, with carbon-monoxide (CO; grey), atomic carbon ([C i], orange) and water (blue, of course) lines at low frequencies, and atomic lines at high
frequencies (shown in black). A _forest_ of absorption lines is seen at the ∼ 1000 GHz frequency range, consisting of CH [+], OH [+] and (ionized) water lines, shown
in red. _The bottom panel_ shows the restframe frequencies of the optimized tunings in Bands 3, 4, 5, 6, 7 and 8 for each of the sources in ANGELS. The tunings
(shown as the aperture-extracted spectra in black lines) were optimized to target as many lines as possible, and wherever they are expected to observe a line, we
mark the frequency with a circle. The sources are sorted by redshift, with the lowest-redshift source at the bottom, and the highest-redshift source at the top.


MNRAS **000**, 1–42 (2024)

6 _Bakx et al._

#### Band 3 Band 4 Band 5 Band 6 Band 7 Band 8



HerBS-22


HerBS-36


HerBS-41A


HerBS-42A


HerBS-42B


HerBS-81A



10 kpc


2 kpc


2 kpc


2 kpc


2 kpc


2 kpc


2 kpc



**Figure** **3.** The dust continua of HerBS-21 through -81A are shown as white contours (3, 5, 8 _𝜎_ and beyond, following the Fibonacci sequence, see Table 2
for the _𝜎_ -values) between Bands 3 through 8 from left to right. The beam size is shown as a white ellipsoid in the top-left, and the scale bar is shown in the
bottom-right of the Band 8 image, using the proper distance at the redshift of the _Herschel_ source. The images are scaled to contain the source, using a 7 arcsec
square poststamp for HerBS-21 field, a 3 arcsec poststamp for HerBS-22 and -25, and a 2 arcsec poststamp for HerBS-36 through 81A. For fair comparison, we
show the images before primary-beam corrections, as these effects could vary across the different bands.


MNRAS **000**, 1–42 (2024)

_Efficient high-resolution line survey_ 7

#### Band 3 Band 4 Band 5 Band 6 Band 7 Band 8



HerBS-86


HerBS-93


HerBS-104


HerBS-106


HerBS-155


HerBS-159A



2 kpc


2 kpc


2 kpc


2 kpc


2 kpc


2 kpc


10 kpc



**Figure 3.** _Continued._ The dust continua of HerBS-81B through -159A are shown as white contours (3, 5, 8 _𝜎_ and beyond, following the Fibonacci sequence, see
Table 2 for the _𝜎_ -values). The images are scaled to contain the source, using a 2 arcsec square poststamp for all fields, except a 1.6 arcsec square poststamp for
HerBS-104, a 2.4 arcsec square poststamp for HerBS-155, and a 4 arcsec square poststamp for HerBS-159A. For fair comparison, we show the images before
primary-beam corrections, as these effects could vary across the different bands.


MNRAS **000**, 1–42 (2024)

8 _Bakx et al._


**Table 2.** ANGELS optimized observation set-up


Tuning Bandwidth Observing depth Resolution FoV MRS Pix. size Cal. unc.
Cont. 35 km/s

[GHz] [mJy / beam] [" × "] (arcsec) (arcsec) (arcsec)


Band 3 [@] 98.3705 ... 102.0895 & 110.3705 ... 114.0895 0.051 1.25 0.51 × 0.30 82 4.2 0.05 5 %
Band 4 [#] 132.4405 ... 136.1605 & 144.4405 ... 148.1605 0.049 1.04 0.38 × 0.34 62 4.1 0.05 5 %
Band 5 [†] 190.8645 ... 194.5855 & 202.8645 ... 206.5855 0.051 0.92 0.31 × 0.26 44 2.9 0.04 5 %
Band 6 [‡] 222.9465 ... 226.6665 & 237.4465 ... 241.1665 0.069 1.89 0.20 × 0.18 38 2.5 0.03 10 %

Band 7 [∗] 279.2225 ... 282.9425 & 291.2225 ... 294.9425 0.102 1.52 0.17 × 0.12 30 2.1 0.02 10 %

Band 8 [∗∗] 403.9195 ... 407.6395 & 415.9195 ... 419.6395 0.210 2.61 0.17 × 0.16 21 1.5 0.02 20 %


**Notes:** Col. 1: ALMA Band used for the tuning. Col. 2: Frequency set-up, contiguous between the triple-dots, and with the lower- and upper sidebands
separated by an ampersand. Col. 3: Sensitivity of the observations across the complete ≈ 7 _._ 5 GHz. Col. 4: Average sensitivity of the observations across a
35 km/s bin. Col. 5: Average beam size in units of arcsec by arcsec. Col. 6: Field of View in units of arcsec, this corresponds to the diameter where the primary
beam reaches 0.35 of its peak value. Col. 7: Maximum recoverable scale in units of arcsec. Note that none of our sources extend beyond this scale. Col. 8: Pixel
size in units of arcsec. Col. 9: Calibration uncertainty in flux density measurements. Following Bakx & Conway (2024), our observations are conducted using
the Local Oscillator (Bryerton et al. 2013) and the following receivers: [@] The Band 3 performance is documented in Claude et al. (2008); Kerr et al. (2014) [#]

The Band 4 performance is documented in Asayama et al. (2014) [†] The Band 5 performance is documented in Belitsky et al. (2018) [‡] The Band 6 performance
is documented in Ediss et al. (2004); Kerr et al. (2004, 2014) [∗] The Band 7 receiver performance is reported in Mahieu et al. (2012). [∗∗] The Band 8 receiver
performance is reported in Sekimoto et al. (2008).


**Figure 3.** _Continued._ The dust continua of HerBS-159B through -184 are shown as white contours (3, 5, 8 _𝜎_ and beyond, following the Fibonacci sequence, see
Table 2 for the _𝜎_ -values). The images are scaled to contain the source, using a 3 arcsec square poststamp for HerBS-159B, and a 2 arcsec square poststamp for
HerBS-170 and -184. For fair comparison, we show the images before primary-beam corrections, as these effects could vary across the different bands.



agreement between one-another (Bendo et al. 2023). Firstly, where
it is necessary to discuss the resolved luminosity (e.g., in the resolved star-formation law; Section 6.1), we use a single-temperature
modified black-body estimate of the far-infrared luminosity of these
sources with 35 K and _𝛽_ dust = 2 (Bendo et al. 2023) fit to the Band 7
flux densities of the sources, which typically have the highest signalto-noise ratio. Secondly, in scenarios where the bulk luminosity is
important (e.g., for the total intrinsic luminosity after lensing correction; Section 6.2), we use the _Herschel_ -photometry to re-derive
the luminosity by fixing the redshift to the _𝑧_ spec (Bakx et al. 2018,
2020b) assuming the spectrum of the famous Eyelash galaxy (see e.g.
Ivison et al. 2016). For sources resolved into multiple components,
we distribute this luminosity based on the relative flux densities of


MNRAS **000**, 1–42 (2024)



the individual components as measured in Band 7. Note that this
implicitly assumes these sources have the same colour temperature
and are at the same redshift. In Appendix D, we provide the infrared
luminosities derived using three methods of fitting, including the
Eyelash template, the _Herschel_ -derived template from Pearson et al.
(2013); Bakx et al. (2018, 2020b), and a single-temperature blackbody. The latter also provides an estimate for the dust temperature
and dust mass. As a sanity check, when we investigate the luminosity of the sources based on the total Band 7 flux both assuming a
constant dust temperature and a best-fit dust temperature, we find a
comparable, albeit uncertain (a standard deviation of ∼ 50 per cent)
luminosity when compared to the second method, with a better fit of
the constant dust temperature (= 35 _𝐾_ ) when compared to the best-fit

_Efficient high-resolution line survey_ 9


**Figure 4.** HerBS-159A and -B are undetected in the natural weighted maps. Instead, we create tapered images with an additional weighting term on the _𝑢𝑣_ -data
of 0.5 arcsec. These reveal the extended structure missed at higher resolutions. HerBS-159A appears to consist of multiple components separated by ∼ 1 arcsec,
while HerBS-159B appears to be a single bright component. Similar to Figures 3, the dust continua are shown as white contours (3, 5 _𝜎_ ) between Bands 3
through 8 from left to right. The beam size is shown as a white ellipsoid in the top-left, and the scale length is shown in the bottom-right of the Band 8 image.
For fair comparison, we show the images before primary-beam corrections, as these effects could vary across the different bands.



dust temperature. A more thorough investigation of the ALMA and
_Herschel_ dust properties is planned for a subsequent paper (Bendo et
al. in prep.).


**3.2** **Line measurements**


The main aim of this study is to perform efficient line surveys across
a large sample of galaxies in an effort to out-perform the _point-_
_tune-and-shoot_ style observations that are the norm for extragalactic
surveys with ALMA. We present the line results in Table C1 and
show the spectral line profiles in Appendix Figures C1.
These sources are mostly resolved systems with line emission
extending across multiple beams. Calculating the total line fluxes is
therefore a non-trivial exercise, and we use the following procedure
on the image-plane data to collect the properties of the emission lines

across our spectrum.
In an effort to extract the total line fluxes, we tried several flux
measurement techniques, including 2 _𝜎_ moment-0 apertures (biased
to including false positive 2 _𝜎_ features and missing the 0−2 _𝜎_ regions
on the edges of the contours; Stanley et al. 2023) and dust continuum
apertures (presuming dust and star-formation are coincident with
line emission). Instead, we combine these methods into an algorithm
that matches the highest-fidelity (band 7) observation to the cube



resolution, and extending the 2 _𝜎_ continuum contour by up to 3
beams of the cube. Effectively, we test the best aperture for each line
to include as much flux as possible, favouring larger apertures to
measure the total flux as accurately as possible at the potential cost
of signal-to-noise ratio.
For sources where the apertures cover a large number of beams,
an additional aperture selection criterion is used, based on the 2 _𝜎_
contours of the moment-0 map before extending the aperture by up
to 3 beams. This step guides the aperture to match the line emission,
but also reduces the effect of _𝑝_ -hacking. Note that, in the case of
absorption lines, typically no additional spatial smoothing is used,
since the expected absorption is only seen at the location where
continuum emission is seen.

The subsequent spectrum is then fitted with a single Gaussian profile to provide a line estimate. We list all line properties in Table C1,
and provide the moment-0 and spectra of the detected lines in the
Appendix Figures C1, where we further highlight the thresholds used
to create the aperture (i.e., _𝜎_ cont _, 𝜎_ mom−0 _, 𝑁_ beam ).


**4** **LENSING**


Nine sources show lensing features in their dust continuum. As gravitational lensing is a purely geometric process, it is achromatic, and


MNRAS **000**, 1–42 (2024)

10 _Bakx et al._


we can use the _𝑢𝑣_ -based lensing reconstruction of Band 7 – which
typically has the highest signal-to-noise detections for our sample –
to deduce the properties of our galaxies across the entire frequency

range.


**4.1** **Lensing reconstruction**


In this section we give a general description of the methodology
and models that we used to obtain source-plane reconstructions.
We perform this lens modelling (lens mass model optimization and
background source reconstructions) using the open-source software
`PyAutoLens`, which is described in Nightingale & Dye (2015);
Nightingale et al. (2018, 2021) and builds on the methods from
previous works in the literature (e.g. Warren & Dye 2003; Suyu et al.
2006). We perform lens modelling in the visibility (i.e., _𝑢𝑣_ ) plane
(e.g. Enia et al. 2018; Maresca et al. 2022; Powell et al. 2021).
The analysis pipeline is broken down in two phases. In the first
phase we fit a parametric model for the source (i.e. a Sersic profile)
while in the second phase we switch to pixelated reconstructions.
In both phases the mass model for the lensing galaxy is a Singular
Isothermal Ellipsoid (SIE).

The analysis pipeline was divided into two phases for both technical and observational reasons. Technically, the non-linear search
involving a pixelated reconstruction, which is computationally intensive, benefits from a robust initial estimate of the lens’s mass model
to converge more efficiently. While a parametric model of the source
may not fully capture the complexity of the background source, it
provides a reliable initial mass model. This model, derived from
the parametric phase, serves as a prior for the subsequent pixelated
phase. Observationally, at higher resolutions, complex structures in
some sources emerge that cannot be accurately modeled with a parametric approach. In such cases, relying on a parametric model could
introduce biases in the lens parameters and, by extension, in the
derived magnification factors, which are primarily what we aim to
determine from the lensing analysis in this paper. In the sub-sections
that follow we give more details about the various models that are
used in our analysis.


_4.1.1_ _Lens_


The convergence of the SIE model is defined as,



in terms of _𝛾_ ext _,_ 1 and _𝛾_ ext _,_ 2, with relations:



_𝛾_ ext =
~~√~~



_𝛾_ ext [2] _,_ 1 [+] _[ 𝛾]_ ext [2] _,_ 2 _[,]_ tan2 _𝜃_ ext = _𝛾_ _[𝛾]_ ext [ext] _,_ _[,]_ 1 [2] _._ (3)



_4.1.2_ _Source_


As mentioned before two different approaches are used to represent
the background source. The first approach is to use a parametric
profile, specifically a Sersic (Sérsic 1963), which is the most common
type of profile that is used to describe the light distribution of galaxies.
This has a functional form that is given by,



��



_𝐼_ ( _𝑟_ ) = _𝐼_ e exp



�



− _𝑏_ n



_𝑟_

_𝑟_ e
��



1/ _𝑛_
− 1
�



_,_ (4)



where _𝑟_ _𝑒_ is the effective radius, _𝐼_ e the intensity at the effective radius,
_𝑛_ the Sersic index and _𝑏_ n a constant parameter that only depends on
_𝑛_ (Trujillo et al. 2004).
The second approach is to use a pixelated grid to reconstruct the
source’s surface brightness distribution, independent of the parametric method described above. For this we use an irregular Voronoi
mesh grid (e.g. Nightingale & Dye 2015). This irregular grid has
the advantage that adapts to the magnification pattern in the sourceplane, meaning that more source-plane pixels are dedicated to regions
with higher magnifications (since the resolution will also be higher
in these regions, roughly scaling as _𝜇_ [−][1][/][2] ) compared to regions with
lower magnification. In addition, it is preferred in cases where the
morphology of the background source is complex and can not be
described with simple parametric profiles (e.g. Sersic). When reconstructing a source on a pixelated grid it is also necessary to introduce
some form of regularization in order to avoid over-fitting (e.g. Suyu
et al. 2006). In this work we use a constant regularization scheme,
where the level of regularization is controlled by the regularization
coefficient, _𝜆_ reg .
As seen in Figure 5, some sources display extended structures
at faint flux levels, possibly indicating interactions. However, the
majority of sources show simple morphologies, in particular at the
brighter flux levels. We can therefore use our best-fit parametric
profiles to get an estimate of the sizes of the star-forming regions,
which are presented in Table 3. For the same reason we also use the
parametric fits to estimate magnifications, also presented in Table 3
as the ratio of the image-plane to source-plane flux.


**4.2** **Multi-wavelength perspective**


In total, six ANGELS fields have _Hubble_ imaging from surveys
reported in Borsato et al. (2023), shown in Figure 6. These _Hubble_
observations use JH-band snapshot-style observations between 7 and
11 minutes to reveal the foreground structure of these galaxies. The
near-complete Einstein rings of HerBS-22, -87 and -155 are shown
to lie directly behind foreground lensing galaxies. In fact, HerBS-155
was already identified as a gravitational lens through a foreground
removal study (Borsato et al. 2023), where the lensing features were
already apparent in the pre-subtracted images. They find a comparable lensing magnification ( _𝜇_ ≈ 20 − 21) to the ALMA-based lensing
magnification of _𝜇_ = 28 _._ 3 ± 5 _._ 6, although they are derived independently. The astrometry of the _HST_ images is corrected using _GAIA_
stars and the imaging is thus accurate to _<_ 0 _._ 1 arcsec. Given the



−1

_,_ (1)
�



1
_𝜅_ ( _𝑥, 𝑦_ ) =
1 + _𝑞_



_𝜃_ E
� ~~√~~ _𝑥_ [2] + _𝑦_ [2] / _𝑞_ [2]



where _𝑞_ is the axis ratio (minor to major axis) and _𝜃_ E is the Einstein
radius. Our model also has additional free parameters that control
the position of the centre ( _𝑥_ _𝑐_ _,_ _𝑦_ _𝑐_ ) and its position angle, _𝜃_, which is
measured counterclockwise from the positive x-axis. In practise we
parametrise the model’s axis ratio, _𝑞_, and position angle, _𝜃_, in terms
of two components of ellipticity,



_𝑒_ 1 = [1][ −] _[𝑞]_




[1][ −] _[𝑞]_ _[,]_ _𝑒_ 2 = [1][ −] _[𝑞]_

1 + _𝑞_ [sin][ (][2] _[𝜃]_ [)] 1 + _𝑞_




_[,]_ (2)
1 + _𝑞_ [cos][ (][2] _[𝜃]_ [)]



which help to prevent periodic boundaries and discontinuities in the
parameter space, which are associated with the position angle and
axis ratio, respectively. Finally, our model also has an additional component to model the potential presence of external shear and/or any
mass distributions with more complexity than a single SIE (Etherington et al. 2023). This is typically described by two parameters, its
magnitude, _𝛾_ ext, and position angle, _𝜃_ ext, but here we express them


MNRAS **000**, 1–42 (2024)

_Efficient high-resolution line survey_ 11


**Figure 5.** Source-plane reconstructions for the 9 confirmed strong lenses in our sample. The gray curve in each panel of the figure shows the caustic curve while
the white scalebar at the bottom corresponds to a physical scale of 1 kpc.



**Table 3.** Intrinsic properties of ANGELS sources


Source Magnification Intrinsic source radii
_𝜇_ ± _𝜎_ _𝜇_ [mas] [kpc]


HerBS-21 9.0 ± 1.8 121 [+] − [13] 10 0 _._ 924 [+] − [0] 0 _[.]_ _._ [100] 080
HerBS-22 18.8 ± 3.7 38 [+] − [1] 1 0 _._ 301 [+] − [0] 0 _[.]_ _._ [009] 009
HerBS-25 9.2 ± 1.8 279 [+] − [46] 27 2 _._ 217 [+] − [0] 0 _[.]_ _._ [368] 222
HerBS-36 4.1 ± 0.8 86 [+] − [3] 3 0 _._ 672 [+] − [0] 0 _[.]_ _._ [027] 023
HerBS-41 2.6 ± 0.5 90 [+] − [2] 2 0 _._ 633 [+] − [0] 0 _[.]_ _._ [018] 018
HerBS-42A [∗] _1.0_ 265 ± 9 2.02 ± 0.07

HerBS-42B [∗] _1.0_ 287 ± 38 2.19 ± 0.29

HerBS-81A [∗] _1.0_ 301 ± 70 2.33 ± 0.54

HerBS-81B [∗] _1.0_ 322 ± 63 2.64 ± 0.52

HerBS-86 [∗] _1.0_ 422 ± 28 3.47 ± 0.23
HerBS-87 8.7 ± 1.7 49 [+] − [3] 2 0 _._ 417 [+] − [0] 0 _[.]_ _._ [024] 021
HerBS-93 [∗] _1.0_ 284 ± 24 2.36 ± 0.20
HerBS-104 6.3 ± 1.2 83 [+] − [5] 2 0 _._ 721 [+] − [0] 0 _[.]_ _._ [046] 024
HerBS-106 2.3 ± 0.4 239 [+] − [16] 15 2 _._ 001 [+] − [0] 0 _[.]_ _._ [131] 129
HerBS-155 28.3 ± 5.6 71 [4] −3 0 _._ 553 [+] − [0] 0 _[.]_ _._ [030] 027
HerBS-159A [∗] _1.0_ 1415 ± 530 11.9 ± 4.48

HerBS-159B [∗] _1.0_ 433 ± 189 3.65 ± 1.60

HerBS-170 [∗] _1.0_ 952 ± 67 6.64 ± 0.47

HerBS-184 [∗] _1.0_ 246 ± 14 2.03 ± 0.12


**Notes:** Col. 1: Source name. Col. 2: Magnification and uncertainties. Numbers
in italics assume no lensing magnification as is apparent in the ∼ 0 _._ 1 arcsec
Band 7 observations. Col. 3: The source-plane size estimates in units of
milli-arcseconds. Col. 4: The source-plane size estimates in units of kpc. The
source sizes were calculated for both Sersic profiles of the lensed sources,
which is left as a free parameter. The IMFIT routine is used for the non-lensed
sources, which are indicated by a star ( [∗] ).


high astrometric accuracy of ALMA [3], the relative astrometric accuracy between _HST_ and ALMA imaging thus lies below 0.1 arcsec.
The sources with extended emission (HerBS-159A and -B) show a
complex foreground system. This suggests that extended emission,
particularly in HerBS-159A, could be caused by gravitational lensing


3 Estimated to lie below 0 _._ 05 arcsec for _>_ 5 _𝜎_ observations in Band 7 using
eq. 10.7 in `[https://almascience.eso.org/documents-and-tools/](https://almascience.eso.org/documents-and-tools/cycle10/alma-technical-handbook)`
`[cycle10/alma-technical-handbook](https://almascience.eso.org/documents-and-tools/cycle10/alma-technical-handbook)` .



extending across multiple arcseconds. Unfortunately, the signal-tonoise of HerBS-159A does not allow for a robust lensing model to
test this hypothesis.
On top of the _HST_ fields, seven _Herschel_ fields (nine ALMA
sources including the multiplicity) have _Spitzer_ imaging. Note that
two of these sources (HerBS-170 and -184) also have _HST_ imaging,
shown in Figure 7. The image PSFs are wider, complicating the astro
∼
metric correction ( 1"), and as a result, provide a less clear picture of
the lensing nature of several galaxies. HerBS-25 and -41A, together
with the _HST_ -identified Einstein rings, are shown to lie directly on
top of a foreground galaxy. HerBS-36 is likely lensed with a very
small Einstein radius (predicted down to ∼ 0 _._ 2 arcsec, Amvrosiadis
et al. 2018). The continuum emission is a barely-resolved clump with
a double-peaked internal structure of ≈ 3 × 7 kpc, and the southern
clump appears to arc (see Appendix Figure F1). The lensing nature
of the HerBS-42, -81, and -184 systems remain unclear. The emission of HerBS-42A and -B coincide with _Spitzer_ -bright emission,
although the emission does not appear to resemble an obvious lensing feature. The double emission peaks of HerBS-81B are close to
a _Spitzer_ -imaged source, although the geometry is not reminiscent
of a lensing system. While the _HST_ image of HerBS-184 does not
suggest a bright foreground system, _Spitzer_ shows a bright source
adjacent to the ALMA emission. Meanwhile, the continuum emission of HerBS-184 is clumpy and extended, although the lack of a
counter-image likely rules out lensing. HerBS-170 is not seen in _HST_
imaging, although some faint _Spitzer_ emission appears visible at the
position of HerBS-170. The spatial association of nearby objects
does not suggest any lensing association. The continuum emission
is clumpy and extended, particularly in Band 5 (≈ 10 × 12 kpc; see
Table 3). As there is no nearby lensing galaxy seen for HerBS-170,
and no counter-image is seen, HerBS-170 is thus likely not lensed.


**5** **SPECTRAL LINE PROPERTIES**


The ANGELS observations have revealed a multitude of lines, consisting of 54 emission and 12 absorption lines, summarized in Table 4.
In this section, we discuss the CO Spectral Line Energy Distributions
(SLEDs; Section 5.1), the in- and outflow distribution of our sample seen in absorption lines (Section 5.2), a brief investigation of
the atomic lines (Section 5.3), and a stacked spectrum (Section 5.4).


MNRAS **000**, 1–42 (2024)

12 _Bakx et al._


**Figure** **6.** _Hubble_ JH-band snapshot data is available for seven of our target galaxies, which provide a high-resolution imaging of several lensed sources,
particularly on the top row. The contours of Band 7 continuum emission are drawn at levels of 3, 5, 8 _𝜎_ and beyond, following the Fibonacci sequence (see
Table 2 for the _𝜎_ -values). HerBS-159A, a source with extended emission requiring tapering to image, is shown to lie in front of a foreground galaxy which is
likely causing a gravitational lensing scenario. Gravitational lensing could be a likely explanation for the extended emission seen in this source.


**Figure 7.** _Spitzer_ 3.6 _𝜇_ m data is available for seven of our ANGELS fields (nine sources in total), which are shown with the _Spitzer_ imaging in the background,
and the ALMA Band 7 contours in the foreground (at 3, 5, 8 _𝜎_ and beyond according to Fibonacci’s sequence). The majority of sources lie close to, or on top of a
bright _Spitzer_ galaxy. The nature of sources with obvious lensing features (e.g., HerBS-25) is not in doubt, but it is unclear whether sources such as HerBS-170,
or -184 are lensed from the current ANGELS and multi-wavelength imaging.



These investigations show the wealth of data from this modest project,
and detailed examination of each subject is planned for subsequent
studies.


**5.1** **CO Spectral Line Energy Distributions**


The rotational transitions of Carbon Monoxide (CO) have proved
a particularly good tracer of the internal structure of DSFGs (e.g.,
Rizzo et al. (2024) and references therein). CO is the second-most


MNRAS **000**, 1–42 (2024)



abundant molecule in the Universe after molecular Hydrogen (H 2 ).
However, unlike the a-polar H 2, it emits brightly from gas clouds
fueling star-formation and is therefore a useful probe of the available
star-forming gas (e.g., Carilli & Walter 2013). Starting at its ground
state at 115 _._ 270 GHz, CO transitions scale linearly in frequency with
higher rotational transitions. These so-called higher- _𝐽_ transitions are
sensitive to denser, warmer gas, and a comparison between the brightness of different CO transitions can illuminate the properties of the
ISM. Recent comparisons of unresolved low-to-mid _𝐽_ CO line ratios,

**Table 4.** Detected emission lines


Line Det. Sources


**54 Emission lines**


CO (3–2) 3 87; 93; 184
CO (4–3) 5 22; 36; 81A; 93; 155
CO (5–4) 5 21; 25; 41A; 42A; 42B
CO (6–5) 7 41A; 81B; 86; 87; 93; 106; 170
CO (7–6) 5 25; 81A; 81B; 86; 106
CO (8–7) 2 36; 155
CO (9–8) 4 21; 41A; 42A; 42B
CO (10–9) 3 25; 36; 41A
CO (11–10) 2 21; 42A
CO (13–12) 1 41A
CO (18–17) 1 41A

[C i] 370 _𝜇𝑚_ 2 93; 106

[C i] 609 _𝜇𝑚_ 3 93; 104; 106

[N ii] 205 _𝜇𝑚_ 2 170; 184

[O i] 145 _𝜇𝑚_ 1 41A
H 2 O (2 0 _,_ 2 − 1 1 _,_ 1 ) 2 41A, 184
H 2 O (2 1 _,_ 1 − 2 0 _,_ 2 ) 1 25
H 2 O (3 1 _,_ 2 − 3 0 _,_ 3 ) 1 25
H 2 O (3 2 _,_ 1 − 3 1 _,_ 2 ) 2 81A; 170
H 2 O [+] (1 1 _,_ 1 − 0 0 _,_ 0 ) 2 22; 25


**12 Absorption lines**


CH [+] (1−0) 3 21; 22; 36
CH [+] (2−1) 1 36
OH [+] (1 0 − 0 1 ) 1 22
OH [+] (1 1 − 0 1 ) 4 21; 41A; 42A; 104
OH [+] (1 2 − 0 1 ) 3 21; 22


often called SLEDs, find a large diversity among DSFGs (Harrington
et al. 2021; Sulzenauer et al. 2021; Hagimoto et al. 2023), ranging
from near-thermalized excitation to low-excitation conditions similar

to the Milky Way (Fixsen et al. 1999).
The ANGELS observations provide detections and upper limits
on both mid- _𝐽_ ( _𝐽_ = 3 − 7) and high- _𝐽_ transitions ( _𝐽_ = 8 − 18). This
large spread in the CO _𝐽_ levels allows us to qualitatively investigate
the presence of dense gas in some of these sources. We show the CO
SLEDs in Figure 8 for the sources with CO lines from ANGELS.
We normalize the CO SLEDs against the CO(4–3) observations, and
if they are not available, we use the average CO SLED template
of Harrington et al. (2021) to translate from the lowest-available
_𝐽_ transition to CO(4–3), and subsequently normalize against that
transition. The choice to normalize to CO(4–3) – which is the most
frequently detected CO line for our sample – will best allow us to see
variations between the CO SLEDs. Similarly, since the galaxies used
to derive the CO SLED template from Harrington et al. (2021) are
likely similar to the DSFGs in this _Herschel_ -selected sample, the CO
SLED should be an accurate representation of the typical behaviour
of the ANGELS galaxies.

Although the BEARS and ANGELS CO line fluxes agree on the
whole, several sources show discrepancies in CO line fluxes, even
when observed in the same CO transition. Appendix Figure E1 shows
the velocity-integrated flux densties for the six galaxies with line measurements of the same CO transition in both BEARS and ANGELS,
as well as the fluxes extracted from the resolved maps using the
same method as BEARS. Careful re-examination of the BEARS data

(Urquhart et al. 2022; Hagimoto et al. 2023) and ANGELS data suggests these discrepancies could be caused by the different apertures
and different approaches taken in the flux extraction. Firstly, in this



_Efficient high-resolution line survey_ 13


paper we match the apertures to extract flux despite the additional
noise that arises from increased apertures, while previous studies
use a curve-of-growth approach that stops velocity-integrated flux
density measurements at a 5 _𝜎_ threshold, which appears to bias the
observed fluxes low. The comparison between the 5 _𝜎_ and the ANGELS methods on the complete resolved data finds only a 4 ± 8 per
cent systemic difference between the two methods (with modestlylarger fluxes in the ANGELS methodology), although there appears a
large (45 per cent) variation for each line between the methods. This
effect could thus influence the analysis of individual SLEDs. Secondly, we also note that there are consistently-found discrepancies
between unresolved and resolved studies (Jorsater & van Moorsel
1995; Czekala et al. 2021), such as the flux estimates from ALMA
large program ALPINE when compared to the resolved CRISTAL
study (Posses et al. 2024), or the flux estimates reported in resolved
observations of bright AGNs (Novak et al. 2019). The origin of
these issues arise from the deconvolution technique in TCLEAN
that produces a combined image of background noise (in units of
Jy / dirty beam) and signal (assuming a Gaussian point-spread function in units of Jy / clean beam). As a consequence, the fluxes from
resolved maps might produce a different total flux estimate than those
from unresolved observations. Regardless of this caveat, our subsequent interpretation does not depend solely on the BEARS data and
we have confidence in our ANGELS-to-ANGELS CO SLED analysis
presented below.

As seen for other samples (Yang et al. 2017; Cañameras et al. 2018;
Stanley et al. 2023), the CO SLEDs of sources vary strongly, with
several sources showing evidence of large reservoirs of warm, dense
gas (i.e., HerBS-25, -41A, -42A, -87, and -170), with HerBS-87
tentatively showing steep SLED features similar to the broad absorption line quasar APM 08279+5255 (Weiß et al. 2007). Meanwhile,
the other sources (i.e., HerBS-21, -93) follow the trend reported in
Harrington et al. (2021). Some of these sources were not observed
in high- _𝐽_ CO transitions (HerBS-22 and -86), which impedes us to
extend the interpretation towards all sources. Unfortunately, the noncomprehensive nature of this survey means that the current statistics
are limited to only a handful of sources.
The ANGELS observations are not deep enough to detect all lines,
but they do indicate the broad statistics of the ANGELS Pilot sample,
such as the lensing fraction and the ratio of sources with high- _𝐽_ CO
lines. The prevalence of dense, warm gas thus appears diverse across
distant dusty galaxies, with ∼ 36 ± 13 per cent (using a binomial distribution; Gehrels 1986) of sources showing such evidence, which
could indicate the presence of an AGN (e.g., van der Werf et al. 2010;
Rosenberg et al. 2015). A visual inspection of Figure 5 of Harrington
et al. (2021) seems to suggest they have a similar ratio of sources
with extreme high- _𝐽_ CO SLEDs. Broadly, their _𝜒_ [2] -minimized turbulence models of the CO SLEDs report 5 sources with no emission
at _𝐽_ up = 10, while 4 sources have bright CO(10–9) emission. 14
ANGELS sources fall between these two categories, indicating there
is some dense gas, but that the sample is not dominated by dense gas.
Since the SLEDs with emission from higher- _𝐽_ CO emission are distributed between lensed and unlensed sources, there does not appear
a large effect of differential lensing (Serjeant 2012, 2024), and we
note that a thorough characterization of the gas in ANGELS sources
requires more extensive modelling beyond the scope of this paper
(e.g., Harrington et al. 2021).


**5.2** **Absorption lines**


These dusty galaxies probably lie at the centre of overdensities from
quantum-fluctuations left over from the Big Bang (Chiang et al. 2013,


MNRAS **000**, 1–42 (2024)

14 _Bakx et al._


0

2 4 6 8 10
J up


8


7


6


5


4


3


2


1


0

5 10 15
J up


0

2 4 6 8 10
J up


0



0


0


0



2 4 6 8 10
J up


2 4 6 8 10
J up


2 4 6 8 10
J up


0



2 4 6 8 10
J up


2 4 6 8 10
J up


2 4 6 8 10 12
J up



2 4 6 8 10
J up


2 4 6 8 10
J up


2 4 6 8 10
J up



0


7


6


5


4


3


2


1


0



0


0


0



Weiss+07

Harrington+21

Constant brightness

Cosmic Eyelash

Milky Way

BEARS

ANGELS



2 4 6 8 10
J up



2 4 6 8 10
J up



**Figure** **8.** The CO SLEDs of all sources including the new CO line observations from the ANGELS survey and previous values from the BEARS survey
(Urquhart et al. 2022; Hagimoto et al. 2023) show the velocity-integrated line intensities of the CO lines normalized against the CO(4–3) line. If the CO(4–3)
line is not available, we use the lowest- _𝐽_ CO line and the stacked CO template from Harrington et al. (2021) to derive the expected CO(4–3) emission line. We
compare CO SLEDs against the _thermalized_ constant-brightness profile (∝ _𝐽_ [2] ; i.e., optically-thick in all lines), a highly-excited quasar (Weiß et al. 2007), the
stacked profile by Harrington et al. (2021), the Cosmic Eyelash (Swinbank et al. 2010; Ivison et al. 2010), and the Milky Way (Fixsen et al. 1999).



2017; Casey 2016). As the Universe expanded, filaments funneled
gas onto these central nodes (e.g., Springel 2005; Dekel et al. 2009),
allowing for the formation of massive galaxies. This feeding subsequently triggers the onset of feedback mechanisms (Man & Belli
2018) via Active Galactic Nuclei (AGN) heating (Hlavacek-Larrondo
et al. 2022) and star-formation driven winds (e.g., Furlanetto &
Mirocha 2022). Such dynamics are sometimes seen through wide
or asymmetric emission lines, but outflow signatures are difficult to


MNRAS **000**, 1–42 (2024)



detect against the often-brighter systemic emission in galaxies due
to velocity smearing effects and the multi-phase nature of outflows.


Absorption lines offer a more unbiased and high-fidelity (Spilker
et al. 2018, 2020a) approach at detecting gas dynamics inside galaxies, by searching for the shadow of an absorption line against the
bright continuum of dusty sources. Since the absorption feature originates between the bright continuum-emitting regions and us (the observers), any velocity offset immediately reveals whether the gas is inor outflowing. Consequently, absorption lines are an important tracer

of the gas cycle of distant galaxies. To date, a handful of studies have
characterized distant dusty galaxies using absorption lines such as the
methylidyne cation (CH [+] ; Falgarone et al. 2017; Indriolo et al. 2018),
ionized hydroxyl (OH [+] ; Berta et al. 2021; Butler et al. 2021, 2023;
Riechers et al. 2021), and hydroxyl (OH 119 _𝜇_ m; Spilker et al. 2018,
2020b,a). [4] The CH [+] ion is very unstable, formed through strongly
endothermic processes, with a dissociation time of around 1 year.
As such, it is only observed where it is created, in strongly-shocked
regions. Meanwhile, OH [+] traces more diffuse molecular gas feeding
star-formation. In total, around forty sources have been observed in
sub-mm absorption lines, with around twenty-five sources showing
absorption lines at velocities outside of the systemic velocity. The
majority of these sources show signs of outflowing gas because of
rapid star-formation or AGN feedback. Meanwhile, inflows of gas
are likely occurring as well, although they might be more difficult
to image. Observations will need to see _down_ _the_ _barrel_ of inflowing gas filaments, and as a result large samples tracing the delicate
balance of gas in- and outflows are still lacking. Without these necessary observational constraints, hydrodynamical models of the gas
flows struggle to benchmark mass loading factors (i.e., outflowing
gas over star-formation rate) in the distant Universe, which are crucial
to test the duration of star-forming events such as the extreme DSFGs
studied in this paper.
The bright continuum emission from these galaxies, particularly
in Bands 6 and beyond, allowed the detection of twelve absorption
lines across six sources (HerBS-21, -22, -36, -41A, -42A, and 104), where two molecules were seen in absorption (CH [+] and OH [+] ).
Several transitions of OH [+] are seen, namely the strong (1 1 -0 1 ) and
(1 2 -0 1 ) ground-transitions, as well as the weaker (1 0 -0 1 ) transition
for HerBS-22 (see e.g., Berta et al. 2021). Meanwhile, this is only
the second time that CH [+] (2–1) is seen in the _𝑧>_ 0 _._ 1 Universe
(Bakx et al. 2024), although we note that we might miss the Δ _𝑉<_
0 km/s component in the ANGELS observations. The ANGELS
observations also covered multiple other lines that are sometimes
seen in absorption, including water and ionized water. The sensitivity
limits, and the limits to the bandwidth result in non-detections for the
fainter species in absorption, particularly given the fainter continuum
emission regions (i.e., below Band 5). Similarly, lower-significance
line features such as P-Cygni might be hard to identify, with tentative
cases seen in, for example, CH [+] in HerBS-21.
We show an overview of the absorption lines in Figure 9 as a function of their redshift and relative velocity compared to the ANGELSdetected CO transitions. The sources are compared against other
absorption line studies of _𝑧>_ 1 sources (Falgarone et al. 2017; Indriolo et al. 2018; Spilker et al. 2018, 2020a; Berta et al. 2021; Butler
et al. 2021; Riechers et al. 2021). Three of the sources (-21, -36
and -104) have evidence of inflowing gas in their absorption lines,
although only the relative velocities of HerBS-21 are outside of the
error margins. There appears to be a relation between the velocity offset with redshift, transitioning between in- to outflowing gas at _𝑧_ = 3.
However, since that this collation of data was obtained with different
line tracers and observing differently-selected sources having a range
intrinsic velocity widths, larger samples of observations with similar
observational parameters (beam size, observation depth, tracers) are
necessary before such investigations become more robust.
HerBS-21, -22, -36 and -42A have multiple molecules seen in
absorption. Even though these can be sensitive to vastly different
phases of the ISM and even the circum-galactic medium, they indi

4 Systemic emission of these lines, and neighbouring ones, can interfere with
a complete interpretation of these lines, although this effect is often minimal.



Large gas clouds surround the ionizing emission of bright young Oand B-stars and shield the outer layers of the highest-energy photons. As a result, high-ionization states of specific elements (e.g.,
hydrogen, helium, oxygen and nitrogen) mostly emit from the central regions of these photo-dissociation regions (PDRs; Tielens &
Hollenbach 1985), i.e., H II regions. The PDR model of the ISM
of galaxies in the distant Universe suggests an onion-like distribu

MNRAS **000**, 1–42 (2024)













sources, shown in blue. Filled triangles indicate CH [+] detections and circles
indicate OH [+] observations. We compare against other high-redshift observations of absorption lines with a velocity shift (Falgarone et al. 2017; Indriolo
et al. 2018; Spilker et al. 2018, 2020a; Berta et al. 2021; Butler et al. 2021;
Riechers et al. 2021). About half of the sources are seen with inflowing gas,
with the other half showing outflowing gas with velocities between ±300 km/s.
The sources with multiple transitions (HerBS-21 and -22) find similar systematic velocity offsets for both their tracers, suggesting that the shocked gas
traced by CH [+] and the more diffuse molecular gas traced by OH [+] originate
from similar regions.


cate similar velocity offsets relative to the host galaxy. This suggests
that the shocked regions seen by CH [+] of HerBS-21 and HerBS-22
lie close to large volumes of low-density molecular gas traced by
OH [+] . The shocked gas in HerBS-36 seems to be red-shifted relative to the bulk molecular gas reservoirs, which could indicate rapid
inflows encountering the strong star-forming environments. Given
the large velocity widths of these sources (Table 1), these are likely
dynamically-complex systems, and the small relatively velocity offsets (| _𝛿𝑉_ | _<_ 500 km/s) between the absorption and emission lines
could obfuscate a more intricate interaction of the in- or outflow
ing gas and the host galaxy. In order to secure a good interpretation
of these sources, deeper and higher-resolution observations on absorption lines in these sources are thus important. A more thorough
investigation of in- and outflowing gas masses are beyond the scope
of this paper, and they are strongly dependent on geometry arguments
(e.g., Butler et al. 2023).


**5.3** **Atomic lines**

16 _Bakx et al._


tion of gas around ionisation sources such as bright, massive (O &
B) stars, where gas temperature decreases as the column density of
neutral hydrogen increases. Lines from forbidden transitions such
as atomic oxygen [O i] and singly-ionized nitrogen [N ii] can trace
these higher ionization rates and can be important cooling lines of
galaxies (Stacey 2011; Vogelsberger et al. 2020). Current studies of
FIR atomic lines typically focus on the low-redshift Universe with
now-defunct observatories such as _Spitzer_, _Herschel_ (Cormier et al.
2015; Díaz-Santos et al. 2017; Zhang et al. 2018) and SOFIA (Ura
et al. 2023), or require high redshifts ( _𝑧>_ 4 _._ 5; Lee et al. 2019, 2021;
Le Fèvre et al. 2020; Bouwens et al. 2022; Bakx et al. 2023) to shift
these lines in more favourable atmospheric transmission windows.
The local studies often only detect a small fraction of the targeted
sources, resulting in difficulties in interpreting the sample as a whole
(Bonato et al. 2014), while the most distant searches probe a population different than the DSFGs located at the peak of cosmic evolution
(Madau & Dickinson 2014). ANGELS offers to increase the number

of DSFGs in the cosmic noon with atomic line observations to better

characterize the PDR conditions in the most violent star-bursts across

cosmic time.

The highest frequency bands (Band 7 & 8) covered atomic lines
for four sources, namely [N ii] 205 _𝜇_ m for HerBS-170 and HerBS184 (in Band 7) and HerBS-81B (in Band 8), and [O i] 145 _𝜇_ m for
HerBS-41A (in Band 7). The [N ii] emission line is detected in both
HerBS-170 and HerBS-184. In the case of HerBS-81, only part of
the [N ii] emission line was covered ( _𝑉>_ 50 km/s) and hence not
detected in the current data. The [O i] emission line was detected in
HerBS-41A, although we note that the total flux estimate might be
underestimated since we probe only the Δ _𝑉<_ 150 km/s region.
Figure 10 shows the observed [O i] and [N ii] line luminosity scaling relations of the three detected ANGELS sources, compared to
local (Brauher et al. 2008) and distant galaxies (Herrera-Camus et al.
2018; Cheng et al. 2020; Cunningham et al. 2020) from other surveys.
We note that we do not scale our luminosity for the magnification
of HerBS-41A, since we do not have lensing models of our spectral line. Our sources lie on the bright end of the scaling relations,
and HerBS-170 qualifies as the brightest Nitrogen emitter observed
to date. There is no evidence for a far-infrared line deficit, which
appears to affect high star-formation surface-density galaxies (e.g.,
Rybak et al. 2019). As we build catalogues of atomic lines, these lines
become invaluable to provide strong constraints of the gas densities
(e.g., Doherty et al. 2020), ionisation parameters (Hagimoto et al.
2023) and metallicities (e.g., Tadaki et al. 2022) to characterize this
diverse sample of DSFGs.


**5.4** **Stacked spectrum**


In an effort to reveal fainter line transitions, line stacking experiments
combine the emission from multiple galaxies together for a higherfidelity signal (Spilker et al. 2014; Fudamoto et al. 2017; Birkin
et al. 2021; Chen et al. 2022; Hagimoto et al. 2023; Reuter et al.
2023). These fainter lines can reveal unique phases of the ISM. For
example, hydrogen cyanide traces dense, star-forming gas (Riechers
et al. 2006, 2010; Oteo et al. 2017; Béthermin et al. 2018; Cañameras
et al. 2021; Rybak et al. 2022; Yang et al. 2023), and the presence of
carbon and oxygen isotopologues are a measure of metal enrichment
history (Henkel et al. 2010; Béthermin et al. 2018; Zhang et al. 2018;
Maiolino & Mannucci 2019). These lines are often faint and thus
require long observation times. The observations of multiple sources
can be combined through stacking, although these often are done only
at the wavelengths where spectral scans searched for the redshifts,
i.e., the 3 and 2 mm observed wavelengths. Consequently, faint


MNRAS **000**, 1–42 (2024)



10 [10]


10 [9]


10 [8]


10 [7]


10 [6]


10 [5]


10 [4]


10 [9] 10 [11] 10 [13]
Infrared Luminosity [L ]


10 [9]


10 [8]


10 [7]


10 [11] 10 [12] 10 [13] 10 [14]
Infrared Luminosity [L ]


**Figure** **10.** The luminosity scaling relation between [O i] (top) and [N ii]
205 _𝜇_ m (bottom) for local galaxies (normal star-forming systems, starbursts,
and active galactic nuclei; Brauher et al. 2008), and high-redshift galaxies (for

[O i] Herrera-Camus et al. 2018; for [N ii] Cheng et al. 2020; Cunningham
et al. 2020 and references therein). HerBS-41A is detected in [O i] with
the ANGELS observations, and the detections of [N ii] in HerBS-170 and
HerBS-184 places them as the brightest Nitrogen emitters in the Universe
observed to date. We note that the [O i] flux estimate for HerBS-41A might
be an underestimate since we are only sensitive to emission from the Δ _𝑉<_
150 km/s. There is no evidence of far-infrared line deficits, often seen in [C ii]
high surface star-formation rate galaxies.


lines in the 1 mm regime remain poorly studied, even though many
molecular species exist in this wavelength range. Consequently, even
if individual observations are not able to directly detect individual
lines, stacking is thus an important tool, particularly when samples
become large enough to enable A/B comparison tests.
Figure 11 shows the stacked spectrum from the ANGELS observations using the same method as Hagimoto et al. (2023). In short,
we extract the complete spectra from the regions where the band 7
emission exceeds 2 _𝜎_ surrounding the sources using an additional
smoothing of one beam. We decide to stack the spectrum of each
galaxy with the goal of representing a single archetypal galaxy at
_𝑧_ = 2 _._ 5 (approximately the mean of this sample; Urquhart et al.
2022) with an infrared luminosity of 10 [13] L ⊙ . This involves normalizing all spectra to the same luminosity and to a common redshift.
Consequently, we require a constant _𝐿_ [′] across all redshifts, and normalize the spectrum accordingly:



2
1 + _𝑧_ common
_,_ (5)
� 1 + _𝑧_ source



_𝑆_ _𝜈,_ common = _𝑆_ _𝜈_



_𝐷_ L ( _𝑧_ source )
� _𝐷_ L ( _𝑧_ common )



where _𝐷_ L refers to the luminosity distance at redshift _𝑧_, and _𝑧_ common
is set to 2.5. This factor accounts for the cosmological dimming for

10


5


0


5


3


0


3


40


20


0









_Efficient high-resolution line survey_ 17


|CO (1−0) CO (2−1) CO (3−2) O ( m C 64 0− 93 µ) [C i] CO (5−4) 2 O H2 1 1, ( −20,2) −− CC OO 76 65 (( ))|m 3 [ + −µ Hi] 10 CC (7 0) +++ −−− HHH 111 OOO 000 120 111 ((( ))) −− CC OO 98 87 (( )) −− HH OO 32 31 22 10 22 01 31,,,, (( )) H2O (11,1 −00,0) H2O+ H2O+ ) O 3 1 −2, HH2 F 1( 0 ( ) −− 11 10 19 CC OO 0− (( )31,2) CO (12−11) m µ [ i] 12 −1 CN Oi 305 ( 2) CO (14−13) CH+ (2−1)|CO (15−14) CO (16−15) 158µm [C ii] CO (17−16) m [ −µ 14 CO Oi] 85 17 (1 )|CO (19−18) CO (20−19)|
|---|---|---|---|
|||||
|||||
|||||
|||||
|||||
|||||
|SPT (Reuter+22)|SPT (Reuter+22)|SPT (Reuter+22)|SPT (Reuter+22)|
|ALESS (Birkin+21; distribution unknown)<br>HFLS (Riechers+13)<br>Arp 220 (Rangwala+13)<br>ALCHEMI (Martin+21)<br>SUNRISE (Yang+23)<br>Individual sources|ALESS (Birkin+21; distribution unknown)<br>HFLS (Riechers+13)<br>Arp 220 (Rangwala+13)<br>ALCHEMI (Martin+21)<br>SUNRISE (Yang+23)<br>Individual sources|ALESS (Birkin+21; distribution unknown)<br>HFLS (Riechers+13)<br>Arp 220 (Rangwala+13)<br>ALCHEMI (Martin+21)<br>SUNRISE (Yang+23)<br>Individual sources|ALESS (Birkin+21; distribution unknown)<br>HFLS (Riechers+13)<br>Arp 220 (Rangwala+13)<br>ALCHEMI (Martin+21)<br>SUNRISE (Yang+23)<br>Individual sources|



500 1000 1500 2000
Restframe Frequency [GHz]


**Figure 11.** The composite spectrum based on the ANGELS observations. _The top panel_ shows the noise-weighted stacked spectrum of an archetypal _𝑧_ = 2 _._ 5
L IR = 10 [13] L ⊙ galaxy. The brightest spectral line is the [N ii] line at around 10 mJy (see Sect. 5.4). _The_ _middle_ _panel_ shows the signal-to-noise ratio of the
spectrum. _The bottom panel_ shows the number of sources that contribute to each of the spectral line in a solid _blue line_ . Similar stacking experiments (Reuter
et al. 2020; Chen et al. 2022; Hagimoto et al. 2023) are shown as histograms, and the predicted coverage of the full SGP sample is shown in _a blue dashed line_ .
Follow-up studies of individual sources (Rangwala et al. 2014; Riechers et al. 2013; Birkin et al. 2021; Martín et al. 2021; Yang et al. 2023) are shown as solid
lines. While the coverage of the ANGELS sources in this paper becomes sparse at higher frequency, the full survey aims to detect at least a few sources out to

2300 GHz.



each spectral line, as well as for the redshift-dependence of the flux
density unit.


We use the _Herschel_ -based infrared luminosities as discussed in

Section 3.1, where we reweight the fields by their respective Band 7
fluxes (Bendo et al. in prep.; see Table D1), since the sources are most
reliably detected at this frequency. When compared to the method in
Hagimoto et al. (2023), where the weighting was performed based on
the infrared luminosities derived from the ALMA Band 4 continuum,
there appears to be a marginal ( _<_ 15 per cent) effect from source to
source when compared to a fixed constant dust temperature. Each
of the weighted spectra are then added by their variance-weighted
fluxes, which prioritizes the highest signal-to-noise ratios (SNR)
of the lines. As discussed in detail by Hagimoto et al. (2023) and
Reuter et al. (2023), this means that the brightest sources are still
predominantly determining the spectrum. It explains the lack of effect
in line SNR when changing the (intrinsic) luminosity or dust-mass
weightings as shown in Spilker et al. (2014). However, the relative
line ratios within the composite spectrum do strongly vary as different
weighting schemes are used (see e.g. the discussion in Reuter et al.
2023), and are important to account for in future composite spectra.


The top panel of Figure 11 shows the rest-frame composite spectrum using the above-mentioned weighting scheme. The middle panel
shows the signal-to-noise ratio of the observations, while the lowest



panel shows the total number of spectral lines seen per rest-frame
frequency, and compares it to other and future stacking experiments.


All CO lines with _𝐽_ up _<_ 11 are seen in the stacked spectrum. Only
two out of five of the [C i](1–0) lines are detected individually, but
the [C i](1–0) line is clearly detected in the stacked emission. The line
profile of [C i](1–0) appears broader, and could remain undetected
because of its potentially more extended nature (Valentino et al.
2020b). Both H 2 O (2 1 _,_ 1 –2 0 _,_ 2 ) and (2 0 _,_ 2 - 1 1 _,_ 1 ) are detected in the
stacked spectrum, in line with the individual detections and previous
stacking experiments (Yang et al. 2016; Zavala et al. 2018; Hagimoto et al. 2023; Reuter et al. 2023). The brightest stacked spectral
line, [N ii], is detected, and stands out in the stacked spectrum. Three
molecular absorption lines are seen at the −3 _𝜎_ level, CH [+] (1–0),
OH [+] (1 1 -0 1 ), and (1 2 -0 1 ), which are also seen in individual observations, while the fainter OH [+] feature (1 0 -0 1 ) remains undetected.
Importantly, the velocity difference relative to the systemic redshift
of absorption lines are large. Detecting such features in a line stack
is thus surprising. In future observations, larger samples will be able
to more fully characterize fainter lines, and combine the resolved
(ANGELS) and unresolved (BEARS) data to better characterize the
200 - 800 GHz regime, while short-wavelength observations fill in
a contiguous composite spectrum well into the THz regime, probing
atomic lines such as [C ii] 158 _𝜇_ m and [O iii] 88 _𝜇_ m, as well as pro

MNRAS **000**, 1–42 (2024)

18 _Bakx et al._


vide a composite CO SLED out to high- _𝐽_ transitions as explored in
previous work (Hagimoto et al. 2023; Reuter et al. 2023).


**6** **RESOLVED PROPERTIES OF ANGELS SOURCES**


The ANGELS observations have provided a high-resolution view
on a sample of sixteen _Herschel_ fields, revealing 54 emission and
12 absorption lines, while providing meaningful upper limits on
another 27 lines. The beam sizes of the observations range between
0.5 to 0.1 arcseconds, enough to resolve the internal structure of
these distant sources. In the following, we will use this resolved data
to investigate the properties of the star-formation in the ANGELS

sources.


**6.1** **The resolved star-formation law in ANGELS sources**


The Schmidt-Kennicutt relation between the star-formation surface

density and molecular gas mass surface density (Σ SFR –Σ H 2 ; Schmidt
1959; Kennicutt 1998) is a diagnostic of the star-formation mode.
High-redshift dusty starbursts typically have higher star-formation
rates (SFRs) relative to their molecular gas compared to normal starforming galaxies (e.g., Casey et al. 2014), which results in a shorter

∼
depletion time scale ( 100 Myr). The reasons for this boost in star
formation are often hypothesised to be connected with recent merger
events (Sanders et al. 1988; Barnes & Hernquist 1991; Hopkins et al.
2008), although several other theories have been posited, including
secular evolution and violent disc collapse (Cai et al. 2013; Gullberg
et al. 2019; Hodge et al. 2019; Rizzo et al. 2020; Fraternali et al.
2021; Zavala et al. 2022).
Figure 12 shows the resolved Schmidt-Kennicutt relation (Schmidt
1959; Kennicutt 1998) for the ANGELS sources and reference samples of low-redshift galaxies (Kennicutt 1989; de los Reyes & Kennicutt 2019a,b; Kennicutt & De Los Reyes 2021), high-redshift starforming galaxies (Tacconi et al. 2013) and high-redshift DSFGs
(Hatsukade et al. 2015; Chen et al. 2017 and references therein). The
parent sample of BEARS is shown in _dark_ _red_ _circles_ (Hagimoto
et al. 2023). These modestly-resolved observations show more extreme star-forming environments in the mixed lensed- and unlensed
sample than found for unlensed DSFGs. We use a CO-H 2 conversion
factor ( _𝛼_ CO ) value of 4 _._ 0 from the recent study of Dunne et al. (2021,
2022), adjusting the reference sample of DSFGs accordingly for a fair
comparison, although we note that this molecular gas conversion can
vary sharply from source to source (Harrington et al. 2021). Similarly,
we use an IR luminosity-to-SFR factor of 1 _._ 73 × 10 [−][10] M ⊙ yr [−][1] /L ⊙
valid for a Salpeter 1-100 M ⊙ initial mass function. We calculate
the position of each galaxy using a pixel-by-pixel comparison between the dust continuum emission from Band 7 to the lowest- _𝐽_

ANGELS-observed CO transition. Since pixels within each beam
are not statistically independent, we subsequently down-sample to
account for this effect.

The higher-resolution Band 7 dust continuum is smoothed to the
same beam size as the Band 3, 4 or 5 CO emission using the images as
they appear in the sky. Then we compare the maps on a pixel-by-pixel
basis to provide a distribution of the sources, and while the selection
itself could be affected by differential lensing, the position of these
sources on the star-formation law should not be affected by the lensing
as surface brightness is preserved during a lensing event. We use pixels with either the moment-0 CO or dust emission beyond 3 _𝜎_ within
a radius including all of the source flux, as shown in the Appendix
figures. As a lower limit, we demand that the pixel in the other image
has at least 1 _𝜎_ emission, and ensure that the majority ( _>_ 80 per cent)


MNRAS **000**, 1–42 (2024)



of pixels are not excluded from this additional constraint. We show
these pixel-per-pixel comparison of the star-formation law in the Appendix Figures G1 and G2 to investigate the individual properties
of the sources, and for all sources where available, compare directly
to the CO and [C i]-derived star-formation and gas surface densities
from the moderately-resolved study in Hagimoto et al. (2023). These
show a relatively wide distribution of star-formation or gas surface
densities, varying by up to an order of magnitude as seen in previous studies as well (Ikeda et al. 2022). Note that the sharp lines in
resolved Schmidt-Kennicutt relations in Figure G2, particularly for
HerBS-25 and -106, come from the _>_ 1 _𝜎_ criterion. Deeper observations of these sources could reveal lower star-formation rate and gas
mass surface densities on the source outskirts. This could shift their

average position on the star-formation diagram downwards by up to
∼ 0 _._ 2 dex based on the current distribution of the _>_ 1 _𝜎_ emission

shown in Figure G2. This further demonstrates the internal variation
of the star-formation law within galaxies, and the need for efficient
fueling of gas within galaxies to sustain these high star-formation
rates for durations in excess of 100 Myrs.

The difference between the moderately resolved study (Hagimoto
et al. 2023) and the ANGELS observations mostly lie along the constant depletion times (i.e., the diagonal lines). This indicates that the
discrepancy between these studies could originate from less accurate, and dependent size estimations. Additionally, CO line tracers
between CO(3–2) and CO(6–5) are used for the molecular gas mass
estimates, which add additional uncertainties in the conversion to
the ground-state, i.e., to the luminosity of CO(1–0). This can explain the additional offset in the x-direction (Σ H 2 ) for HerBS-86
and -106, where CO(6–5) was the lowest- _𝐽_ transition. Reassuringly,
there do not appear to be significant y-axis offsets, indicating that the
star-formation rate estimates are in agreement (both this study and
Hagimoto et al. (2023) use ALMA dust continuum measurements).
The distribution of the sources is similar to the moderatelyresolved pilot sample of BEARS ( _red_ _points_ ), with larger gas and
SFR surface densities than those found by previous observations for
unlensed sources (Chen et al. 2017). There appears to be enough gas
available for around 100 megayears or one gigayear of star-formation
in these sources. The extended gas reservoirs seen in even these short
snapshots thus indicate that the spatial distribution of gas and dust
can play an important role in the evolution of dusty star-forming
galaxies (see e.g., Ikeda et al. 2022). The order of magnitude spread
in the pixel-per-pixel surface gas densities and surface star-formation
rates indicates that DSFGs require efficient feeding of gas from the
gas-rich regions into star-forming regions to ensure that the high
star-formation rates can be sustained for the depletion timescales indicated by un- or marginally-resolved observations (e.g., Hagimoto
et al. 2023).


**6.2** **Star-formation surface densities of ANGELS sources**


When many stars are formed in a small environment, star-formation
feedback becomes a more important contributor of the evolution of
galaxies. Figure 13 compares the intrinsic sizes of the ANGELS
sources against their intrinsic infrared luminosities. By comparing
their star-formation surface densities to other galaxies (Bothwell et al.
2013; Spilker et al. 2016; Kamieneski et al. 2024) and to expected
limits of star-formation rate (Andrews & Thompson 2011), we find
a large variation across our sample of sources. We use the Sersic
profiles for the sources when available from the lensing reconstruction (seen by crosses; Table 3), where the Sersic indices are free to
vary between 0.5 and 5. The non-lensed sources are fitted using the
`casa` task `IMFIT`, which assumes a Sersic index of 0.5 that appears

_squares_ ) from Chen et al. (2017) from the initially-assumed _𝛼_ CO = 0 _._ 8 to
4 _._ 0 for a fair comparison. These sources lie in the upper-right region of the
star-formation law, with similar depletion times as the resolved observations
of unlensed sources Chen et al. (2017). The sources have similar or slightly
smaller volumes of star-forming gas than unresolved studies with similar
surface star-formation rates. This could indicate that the dense star-forming
regions deplete faster than the moderately-resolved studies, and require efficient fueling from more gas-rich regions to maintain their high surface

star-formation rates.


to match the emission profiles well based on the residual images.
These unlensed sources are broadly larger in size (shown in pentagons instead of crosses). We calculate the per-source luminosity
using the _Herschel_ -photometry, which better accounts for the total
star-formation rate in the total system, but could cause discrepancies
between the Σ SFR estimates from the resolved star-formation law
and this discussion (see Sec. 3.1). In the case of any multiplicity, we
distribute the flux based on the weighted flux densities of the Band 7
continuum emission.
The bulk of sources reside between the 10 and 100 M ⊙ /yr/kpc [2]

regime, similar to other sources seen with _Herschel_ and SPT. Broadly,
three sources are close to the _forbidden_ regime of star-formation, of
which two are in the HyLIRG regime. Although likely the bulk of
the sub-mm emission of these sources is due to star-formation (Bakx
et al. 2018), an obscured AGN could be contributing to the emission
and produce these compact-but-bright sources. In total, eight sources
are in the _𝐿_ IR _>_ 10 [13] L ⊙ regime. The more diffuse galaxies, HerBS159A and B (see Section 7.3) lie in the _<_ 10 M ⊙ /yr/kpc [2] regime,
where typically more normal star-forming galaxies are found (e.g.,
Tacconi et al. 2013). Note that the radius of these sources is extracted
on a tapered image ( _uv_ -taper of 0.5 arcsec), resulting in larger errors,



≈ 10 M ⊙ /yr/kpc [2] .


but regardless their radii are larger than average. The diverse and
complex nature of ANGELS sources is apparent from these resolved
ALMA observations. In the subsequent Section, we compare these
rich results against the known literature of DSFGs.


**7** **NATURE OF ANGELS SOURCES**


The ANGELS sources are effectively randomly sampled from the
BEARS survey, with a selection based solely by their proximity
to each other on scales beyond the scales of the cosmic web (see
Figure 1), as is discussed further in Negrello et al. (2017). The
guiding principle behind the observations was solely to maximize the
number of lines that we could target within a single tuning modulo
the atmosphere. As a result, these observations provide an unbiased
sampling of the properties of high-redshift, bright _Herschel_ sources.
In this section, we investigate the properties of ANGELS sources in
an effort to better characterize the bright end of _Herschel_ sources.


**7.1** **Lensing among the HerBS sources**


The total sample of sixteen _Herschel_ sources turned out to consist
of 26 separate ALMA sources. Out of these, nine ALMA sources
are apparent lenses from the observations. Although an additional
number of sources might still be lensed (HerBS-42A, -159A), we
exclude these in the statistics of these sources. The lensing fraction of
56 ± 13 per cent (assuming a binomial distribution; Gehrels 1986) is
on the lower end of theoretical predictions (e.g., 70 per cent; Negrello


MNRAS **000**, 1–42 (2024)

20 _Bakx et al._


et al. 2007), with direct comparisons to galaxy evolution models (Cai
et al. 2013; Bakx et al. 2018, 2020b) expected even higher fractions

∼
( 85 per cent), in line with subsequent comparisons to near-infrared
imaging (∼ 82 per cent; Bakx et al. 2020a). Lensed galaxies allow
the probing of populations that would remain under the detection
capabilities of facilities, with magnifications up to several tens (Dye
et al. 2015, 2018; Spilker et al. 2016; Amvrosiadis et al. 2018; Zavala
et al. 2018; Rizzo et al. 2020; Kamieneski et al. 2024). The properties
of these sources appears diverse, with over two order of magnitudes
spread in the source radius and associated star-formation surface
density (Figure 13). The comparison samples between the lensed
and unlensed ANGELS sources are selected from different areas and

depths. As a result, larger scale surveys will select towards more
rare geometries of lensing where strongly-boosting caustics intersect
with bright central regions resulting in brighter fluxes. Four of the
sources in ANGELS are also present in the sample from Negrello
et al. (2017), namely HerBS-21, 22, 25, and 42A/B. Two sources
(HerBS-36 and 41A) also meet the Negrello et al. (2017) selection
criterion of _𝑆_ 500 _>_ 100 mJy, and are also lensed. All four common
sources have lensing rank C (unclear lensing nature). HerBS-42A/B is a double system and the individual _𝑆_ 500 fluxes fall below
the 100 mJy criterion, confirming the prediction by Negrello et al.
(2007) that most of the _𝑆_ 500 _>_ 100 mJy sources – also those with C
rank – are likely strongly lensed.
The _HerBS_ sample is selected at the transition from mostly lensed
surveys (Harrington et al. 2016; Spilker et al. 2016; Negrello et al.
2017) to unlensed systems found often in ground-based surveys such
as LABOCA (e.g., Weiß et al. 2009) and SCUBA(-2) (e.g., Simpson
et al. 2019; Garratt et al. 2023). Among the lensed sources, differential lensing [5] (Serjeant 2012, 2024) could more strongly affect
the lensed samples, resulting in a more biased and inhomogeneous
survey at the higher magnifications. Meanwhile, the lensing magnifications of our survey ( _𝜇_ = 2 − 28 with a median _𝜇_ = 8 _._ 9) are
surprisingly similar to those seen of the SPT ( _𝜇_ = 2 − 33 with a
median _𝜇_ = 6 _._ 3; Spilker et al. 2016; Reuter et al. 2020) and _Planck_
( _𝜇_ = 2 − 28 with a median _𝜇_ = 7; Kamieneski et al. 2024), and
the effect of bias could be similar across our samples. We find that
the majority of these lensed systems are small (0.3–3 kpc) central
dusty systems, similar to the sources found in ALESS (Hodge et al.
2013; Karim et al. 2013). The line profiles of these galaxies do not
appear to indicate any source multiplicity or merging state contrary
to the idea that all DSFGs are mergers as often seen in the local
Universe (Sanders et al. 1988; Barnes & Hernquist 1991; Hopkins
et al. 2008). Instead, central dusty star-bursts could be driving the
bulk of the lensed sources seen in _Herschel_ and other surveys (Barro
et al. 2016; Hodge et al. 2016; Cibinel et al. 2017; Ikarashi et al.
2017; Tadaki et al. 2017; Gullberg et al. 2019; Pantoni et al. 2021),
where galaxies are building up a compact central dense stellar component and change their morphology from disk-dominated to bulgedominated systems, perhaps in late-stage mergers and/or violent disk
instabilities (Zolotov et al. 2015). This could be a bias due to the
lensing selection – where compact sources are more susceptible to
be strongly lensed, either because of their prevalence or their high
star-formation surface densities, than extended merging systems – or
an effect of differential lensing. Only deep observations tracing the


5 Due to sharp variations in the lensing magnification of different regions of
a galaxy, the observed, lensed line and continuum fluxes of galaxies could
give a warped perspective on the intrinsic properties of galaxies. This effect is
exacerbated by the initial selection effects, which might favour the selection
of galaxies with strong amplifications of star-forming regions.


MNRAS **000**, 1–42 (2024)



more extended emission in the lower-magnification regions would be
able to differentiate between these two scenarios.


**7.2** **Hyperluminous galaxies**


The high-resolution observations revealed the lensing properties of
the ANGELS sources. Eleven sources remain above the HyperLuminous Infrared Galaxy (HyLIRG; _>_ 10 [13] _𝐿_ IR in Fig. 13) regime.,
although HerBS-159A is potentially lensed. This is higher than typically observed in other samples (c.f., Reuter et al. 2020; Liao et al.
2024), likely because of the fainter selection of the _HerBS_ sources
relative to other surveys. Unlike the lensed sources (sizes between
300 − 2000 pc with a median size of 600 pc), unlensed systems
appear to be more extended (0.3-3 kpc), such as HerBS-93, -170
and -184. The extended morphology of HerBS-170 further makes its
HST-dark nature surprising, as it requires a large, homogeneous dust
screen to obscure this emission. Source confusion affects many of the
_apparently-brightest Herschel_ galaxies (Bendo et al. 2023), however
several of the _intrinsically-brightest_ sources also come from fields
with multiples, such as HerBS-41A, -42A, -81A. This means that
source confusion only little affects the ability of _Herschel_ to find
HyLIRGs in the slightly-fainter flux regimes ( _𝑆_ 500 = 50 − 100 mJy;
Ivison et al. 2016; Oteo et al. 2017).

Four sources showcase the extreme end of star-formation in this

sample: HerBS-36, -41A, -42A, and -81A. Their CO SLEDs indicate
similar star-forming conditions as found in other intense star-forming
systems, such as Planck-selected systems. The surprising discovery
of inflowing gas seen in a shocked tracer for HerBS-36 could further
suggest that inflows play an important role in boosting star-formation
rates (Berta et al. 2021), with part of the source close to the limits of
star formation (Andrews & Thompson 2011), which can thus provide
a ready source for shocks.
The morphology of these systems furthermore appears clumpy,
with modest amounts of the flux density (≈ 10 − 20 per cent for
HerBS-93, -170 and -184) and thus associated star-formation originating from these clumps. Such structures could be essential for
the formation of bulges and of wider star-formation across these
intense starbursts (Hodge et al. 2019; Rujopakarn et al. 2019; Gullberg et al. 2019). Contrary to this, observations of lensed ULIRGs
(Dye et al. 2018; Rizzo et al. 2020) often find more stable rotators,
although SDP.81 is an obvious counter-example (Dye et al. 2015;
Rybak et al. 2015; Tamura et al. 2015). An important consideration
here is also that lensing could affect our picture of the clumpiness of
these sources, both through differential lensing and _𝑢𝑣_ -plane issues
addressed in Gullberg et al. (2019). HerBS-41A and -93 show velocity widths of approximately 1000 km/s, which indicates that they
are already very massive systems (∼ 5 × 10 [11] M ⊙ ; Hagimoto et al.
2023) without obvious indications of merging. The discrepancy between smaller compact lensed ULIRGs and the larger weakly- or
unlensed clumpy HyLIRGs is an important avenue for future investigations, as we find five of our sources to show these extended clumpy
morphologies, with an incidence rate of roughly 35 ± 25 per cent.
Particularly the lack of Hubble counterpart for HerBS-170 poses
an interesting test for the clumpy morphology of dust. At a rest-frame
wavelength of 2100 Å, these Hubble observations are sensitive to direct starlight. With a total star-formation rate of 3000 − 7000M ⊙ /yr
depending on the IMF, the dust screen needs to extend across the
system to obscure both the small-scale clumps (a few 100 _𝑀_ ⊙ / _𝑦𝑟_ )
and the central star-forming region. HerBS-170 has roughly 4 orders
of magnitude higher dust mass than the optically-selected _𝑧_ = 6 − 8
REBELS sources (Ferrara et al. 2022), whose dust screen size extends

∼
about thirty times further ( 1000 times in terms of area). Using eq.

11 from Ferrara et al. (2022), the optical depth of HerBS-170 is thus
roughly ten times higher than REBELS with _𝐴_ _𝑉_ = 0 _._ 1 − 0 _._ 4 (Inami
et al. 2022). Meanwhile, the REBELS observations are only moderately deeper (1 _𝜎_ 1500 = 0 _._ 06 _𝜇_ Jy and 1 _𝜎_ 2100 = 0 _._ 1 _𝜇_ Jy, respectively),
although REBELS lie at higher redshifts. The rest-frame optical dust
obscuration of HerBS-170 is thus, as expected, much higher than
optically-selected sources, but perhaps more importantly, the distribution of this dust must be coincident with star-formation across the

entire extended system, suggestive of a remarkably-homogeneous
dust screen or of star-formation occuring in separate but similarlyobscured clumps across the system at 10 kpc separation (see e.g.,
Cochrane et al. 2021).
While the dust properties in DSFGs are quite similar (dust emissivity index, gas-to-dust ratio; Bendo et al. 2023; Hagimoto et al.
2023), the CO excitations and other line ratios suggest a diverse
group (Daddi et al. 2015; Valentino et al. 2020a; Birkin et al. 2021;
Hagimoto et al. 2023; Stanley et al. 2023), indicating that there are
multiple ways to form a DSFG (Quirós-Rojas et al. 2024). The morphological and kinematic properties of these HyLIRGs seems to indicate a potential pathway where star-forming clumps are associated
with gaseous disks that are unstable (Toomre _𝑄<_ 1) due to high turbulence (Krumholz et al. 2012; Harrington et al. 2021). This would
be contrary to smaller central dusty star-bursts that are rotationallydominated (Dekel et al. 2009) seen mostly through lenses (Dye et al.
2018; Rizzo et al. 2020) and ground-based surveys (Hodge et al.
2013; Karim et al. 2013). The diversity of models to explain DSFGs
(Baugh et al. 2005; Davé et al. 2010; Narayanan et al. 2009, 2015)
should thus accurately reflect the multiple pathways of starbursts and
their transition to quenched galaxies (Toft et al. 2014; Barro et al.
2016).


**7.3** **Spatially-extended sources**


HerBS-159A & B are extended sources, which made the emission fall
below the detection criteria of our observations. By tapering the data
(see Section 3.1) we find ∼ 3−5 _𝜎_ continuum emission visible across
Bands 5, 6, 7 and 8 for these galaxies. This system is of particular
interest, as HerBS-159B is one of the CUBS (Companion sources
with Unusually Bright lineS) sources in Hagimoto et al. (2023). The
CO SLED of this system is in excess of the maximum expected
behaviour from the equipartition theorem between CO excitations;
i.e., it is _super-thermalized_, and cannot be explained by linear-scaling
effects such as differential lensing (Serjeant 2024). Out of the total
sample of 46 sources within the CO studies in Hagimoto et al. (2023),
only four CUBS sources are found. If there is any intrinsic physical
difference between these sources, their physical interpretation thus
offers insight into a unique galaxy process within the DSFG phase,
with an occurrence rate of ∼ 8 per cent. Under the assumption of a
single DSFG phase with a duration of ≈ 200 Myr (i.e., their average
gas depletion time; Hagimoto et al. 2023), this could thus point to a
galaxy phase duration of ∼ 20 Myr.
It is still unclear how galaxies would achieve such a galaxy phase,
however it is possible to physically provide an _super-thermalized_ CO
SLED through optical depth effects (see the modelling in Hagimoto
et al. 2023). These could be triggered by a merger phase or by the
presence of an obscured AGN. Unfortunately, HerBS-159B does not
have any observations of spectral emission lines within ANGELS
that further provide constraints on the system properties.
Instead, the fact that the HerBS-159 system requires tapering to
reveal the component galaxies is an important hint to their galaxy
evolutionary phase. Similar galaxies have been reported in different
studies. Tadaki et al. (2020) reported on such a galaxy with extended



_Efficient high-resolution line survey_ 21


emission, missed in the untapered data, while looking at 85 massive galaxies with ALMA. Sun et al. (2021) investigated a sample
of lensed sources with _Herschel_ through ALMA observations. Two
sources out of a sample of 29 have similar features to the HerBS-159
system. They report that these sources lack the central star-bursts
dominating the majority of galaxies, similar to the morphologies that
are seen in the lensing reconstructions for our sources (Fig. 5). This
is not in agreement with a bright central component associated with
a far-infrared luminous AGN.

_HST_ imaging revealed that HerBS-159A is likely a lensed system with extended emission across multiple arcseconds. Regardless,
this means that the Einstein rings also carry a certain thickness, implying extended emission in the source plane. No obvious lensing
morphology is seen for HerBS-159B (the CUBS source; Hagimoto
et al. 2023), with no evidence of a nuclear emitting region. The fact
that all CUBS sources were seen as multiples suggests this could be
an important component to the formation of this phase. The early
merging, pre-coalescence phase thus seems the most likely explanation for this phase. This early phase, also occurring on the scale of

∼
ten megayears. Rare fields such as HerBS-159 thus require detailed
further study to find out how they fit within the emerging paradigm
of DSFGs, and might reflect an important part in merging history
still missing from models.


**8** **ANGELS AS A LINE SURVEY TECHNIQUE**


The ANGELS pilot aimed to investigate the use of Bands 3 through 8
in line observations through quick snapshots. In this Section, we summarize the results of this method, and provide caveats and suggested
improvements towards expansion of this survey to larger samples of
bright sources.


**8.1** **ANGELS as a redshift machine!?**


Three sources did not yet have spectroscopic redshifts at the start of
the ANGELS observations: HerBS-87, -104, and -170 (see Table 1).
The BEARS observations revealed single line detections (Urquhart
et al. 2022), but not at sufficient depth to exclude different redshift
solutions (Bakx & Dannerbauer 2022). HerBS-87 had a single line
detected at 160.96 GHz. HerBS-104 had a line detected at 90.91 GHz.

The quality of the emission lines seen for HerBS-170 was below the
significance to conclusively state the redshift, with lines at 111.15
and 156.13 GHz.

ANGELS observations revealed additional lines to ensure the ro
bust redshifts of each of these three sources. Of course, these ANGELS tunings did not optimize towards lines for these three sources,
but we use the method from Bakx & Dannerbauer (2022) to estimate
the chance of a single line, or better yet, a robust redshift estimate
from even blind observations. In total, we find a roughly 50 per cent
chance to derive a robust redshift from six tunings (Bands 3 through
8) on a typical DSFG-like redshift distribution, and a _>_ 75 per cent
chance of detecting a single line for each source targeted. ANGELS
thus offers a good chance of assisting in the redshift completion of the
SGP fields. In this pilot study, thirteen galaxies (+ three neighbouring
galaxies) had spectroscopic redshifts, and the choice for observing
windows was driven solely by the expected lines in our observing
window for these sixteen galaxies. However, in a scenario where
much fewer spectroscopic redshifts are known, preference to lower
frequency observations could be given when using tools similar to
Appendix Figure A1, as they relatively cover a larger redshift region
for the same observing window.


MNRAS **000**, 1–42 (2024)

22 _Bakx et al._











galaxies - without any prior line confirmations. These show a large probability
for robust redshift identification for sources without known redshifts beyond
_𝑧>_ 2 ( _blue_ _regions_ ). The HerBS (Bakx et al. (2018, 2020b)) and SPT
sources (Reuter et al. 2020; the two right-most histograms) show the predicted
capability to find robust and single-line ( _orange region_ ) redshifts for a sample
with the same redshift distribution as the HerBS and SPT samples. The
blue regions indicate the chance of finding more than one spectral line, while
orange regions suggest a single spectral line will be found in a tuning. _Hatched_
_blue fill_ indicates cases where one can identify the redshift robustly with even
a single spectral line, while _hatched orange fill_ indicates the situation where
redshift degeneracies remain down to a 5 _𝜎_ uncertainty in _𝑧_ phot . The _grey_
_dotted_ _lines_ indicate the robust redshifts if we include the possibility of
detecting atomic lines such as [C i], and the _black_ _dashed_ _lines_ indicate the
robust redshifts if we include the possibility of single-line robust redshifts
and for cases where there still remains a degeneracy between multiple CO
line solutions (see Bakx & Dannerbauer (2022) for details). The three sources
with ANGELS-confirmed redshifts already had a single line detection, and
ANGELS thus offers a good chance of assisting in the redshift completion of

the SGP fields.


**8.2** **Efficiency compared to overhead-limited surveys**


ANGELS has offered a high-resolution view on galaxies across a
wide spectroscopic scope using ALMA. The project was uniquely
enabled by the bright nature of _Herschel_ sources with yet high enough
surface density to enable efficient scheduling (see Figure 1). In total,
94 spectral lines were targeted across 28 different line transitions. On
average, each source is observed in five transitions, with HerBS-41A
being targeted in as many as 12 lines. 66 lines were detected, resulting
in a detection ratio of 70%. In Bands 3 and 4, eleven transitions were
targeted, and respectively 8 and 9 of these transitions were detected.
Band 5 targeted 19 lines, and we detected 14. Most lines were targeted
in Band 6, where out of 27 lines, 19 were detected. Band 7 had 17
lines targeted and 11 were detected, and Band 8 targeted 9 lines, with
five lines detected.

At only 6.5 hours of observing time, the ANGELS survey targeted
one line every four minutes, and detected a line every six minutes.
Since each band required around one hour (and Band 8 required 1.5
hours), the Band 6 tunings were most efficient, at one line detected


MNRAS **000**, 1–42 (2024)



every three minutes. This is faster than even efficient blind redshift
surveys of sub-mm bright sources such as BEARS, which detected
around 150 spectral lines across roughly 30 hours of observation
time (12 min. per line). We note that this method also used the
optimized observations of clusters of sources (see Fig. 1) to increase
the efficiency. Similarly, the _𝑧_ -GAL NOEMA survey (Cox et al. 2023;
Berta et al. 2023; Ismail et al. 2023) managed to detect 318 emission
lines for 135 _Herschel_ -selected galaxies, resulting in a detection rate
of about one line every 30 minutes. As a rough estimate, every
targeted observation requires between twenty and thirty minutes of
overheads such as calibration steps, reducing even surveys of bright
sources to an efficiency of one line per every thirty minutes. As
such, clustering is an important tool for future spectral surveys, and
the ANGELS method demonstrated here offers at the very least a
doubling, but even an order-of-magnitude increase in the efficiency
of line surveys with ALMA on bright targets.


**8.3** **Caveats with the ANGELS method**


We note several short-comings of this method, which could be used
as caveats for future attempts to do efficient line surveys with ALMA.
Firstly, the ANGELS method is efficient, but does not provide the
homogeneity of targeted observations with ALMA. In fact, these
observations are not deep enough to guarantee a detection, and if
these observations were set to guarantee a detection, the efficiency
boost of ANGELS would reduce significantly. Detection bias can
strongly influence the scientific consensus surrounding important
topics, such as the gas depletion time or ionization state of galaxies
(e.g., Bonato et al. 2014). Lines that remain below the detection limit
could be teased out using line stacking. Here we note an important
caveat of line stacking, which reflects only the behaviour of a group
of galaxies (see the Section below). Since DSFGs are found to be
a diverse population, line stacking alone cannot reveal more than
population-wide behaviour, although once large-enough samples of
data are explored, AB tests (i.e., comparing one subsample directly
to another) in stacking might provide a solution to this problem.
Secondly, there exist a few more variables that can be optimized
towards future ANGELS observations. The optimized tuning set-up
for each cluster was determined on pre-defined clusters of galaxies.
Sources on the edges of these clusters could switch between clusters, providing potentially more efficient or targeted observations to
increase the total number of detected spectral lines. Meanwhile, the
parametrization of the number of lines is based on a fixed set-up of
spectral windows, which provide the widest bandwidth for all Bands
except for Band 6. Band 6 has a variable intermediate frequency
which has not been further optimized during these ANGELS observations, and would require higher-order optimization steps to fully
explore. The method for finding the tunings to detect as many lines
as possible (Appendix Fig. A1) does not account for the chance to
detect lines that were already observed in previous (BEARS) observations. The method also did not highlight that several sources, such
as HerBS-159, did not have any detected spectral lines in their observations. Figure A1 does account for an estimate of the atmospheric
windows. However, it is hard to notice where the spectral lines exactly fall within these windows, and the effect of poor transparency is
hard to properly take into account. Line species or even line types are
clumped together, and as the sensitivity of receivers change with frequency, these graphs do not fully represent the difficulty of detecting
specific species.
Lastly, although this has not turned out to be a major issue with our
observations, these graphs do not account for the change in primary
beam sensitivity with increasing frequency. As several of our sources

were known multiples, we are unable to resolve some sources across
all bands.


**8.4** **Future perspectives on complete** _**Herschel**_ **samples**


Figure 1 offers an alluring peek on the potential of ANGELS on the
complete sample of southern _Herschel_ sources. The current observations target 16 sources in just 6.5 hours. To cover the full 88 southern
HerBS sources, we would require around thirty hours. Scaling up
the number of detected lines, we could expect to detect ∼ 350 lines,
exceeding even the most successful high- _𝑧_ large programmes with
ALMA and NOEMA (e.g., Le Fèvre et al. 2020). On top of expanding the catalogues of high- _𝐽_ CO SLEDs, in- and outflowing
lines, and atomic lines, a full-scale SGP survey would enable a comprehensive stacked spectrum into the Terahertz regime, a crucial
next step until space-based missions such as the Origins Space Telescope (Meixner et al. 2019) take flight. The ability to characterize
88 sources, notwithstanding multiples (roughly an additional 30% of
sources) would enable sample comparisons on the order of 10 %, and
could better test the claims made on this smaller sample of ANGELS
pilot souces.
These pilot observations use the ALMA Bands with relativelygood atmospheric transmission. Observations in Bands 9 and 10
would be technically difficult because of the atmospheric transmissivity, but would also offer a unique view on the short-wavelength
dust continuum and on bright atomic lines, which are important diagnostics of the ISM (e.g., [O i], [O iii], [C ii], [N ii] and [N iii]; Ramos
Padilla et al. 2023). The initial _Herschel_ observations are to a greater
or lesser extent affected by source confusion (Bendo et al. 2023), and
a per-band view on these (and all southern) ANGELS sources would
reveal the dust temperature in a pixel-by-pixel fashion, find any internal properties such as strong nuclear emission (Tsukui et al. 2023),
and provide a solid foundation to study the complete dust emission
of these dusty galaxies.
One of the main aims of ALMA development is the wideband sensitivity upgrade (Carpenter et al. 2023). The goal of ALMA in 2030
is to double the receiver bandwidth, with a final goal of a quadrupling of the bandwidths. Here we estimate the effect this would have
on the efficiency of the ANGELS method beyond 2030. Appendix
Figure A1 is the _tool_ used to derive the optimum tunings. As a mathematical abstraction, this graph depicts a convolution of the available
lines (i.e., a set of delta functions at their redshifted, observed wavelengths) with the observable bandwidths across Bands 3 through 8.
These graphs would look like flat lines for both extremes in bandwidths; a limitless spectral coverage would not require (or allow)
optimization, while a very narrow spectral windows would quickly
reduce the probability of finding lines across multiple sources in a
single set-up. The current set-up sees at least a few lines per Band, so
as the bandwidths increase from their current state, the peak values
would increase. However, the troughs would increase faster still, reducing the relative effect of optimization (i.e., the difference between
the best and worst tuning set-ups).
This does not mean that the ANGELS method becomes redundant.

Firstly, these pilot observations were not deep enough to detect all
targeted lines, particularly across the fainter sources. By increasing
the integration time of our short snapshots to even a modest 5 minutes per source, the number of sources in a cluster identified by the
ALMA Observing Tool would reduce rapidly (i.e., within 10 degrees
on the sky). This would leave fewer lines per selected set-up, again
increasing the importance of optimization. Secondly, this pilot aims
to target _as_ _many_ _lines_ _as_ _possible_ . More science-case guided observations (instead of proof-of-principle) might want to target only



_Efficient high-resolution line survey_ 23


specific line transitions such as CO(1–0), atomic lines or [C i]. With
an increasing bandwidth, it becomes easier to design experiments
that are able to widely target specific lines while also increasing the
serendipity of the observations. Instead of designing the observations to place the targeted spectral line in the middle of the wider
bandwidth, the ALMA tool should consider the possibility to pick up
lines from multiple sources without the need for changing the local
oscillator and the subsequent recalibration. Another such use-case
might overcome the current limit on the resolution. The ANGELS
strategy does not work with the ALMA configurations with a baseline greater than 3 km (C43-7 and beyond), which require sources
to be within 1 degree on the sky instead of 10. Although several
sources are on the sky closer than this (particularly in lower-flux
selections), this would make the current version of the ANGELS
method difficult to execute on a large sample. Finally, these observations provide a showcase towards the careful inspection of the
data cubes of observations without the explicit goal to detect lines.
As ALMA approaches ultra-wide data cubes, careful exploration of
ancillary lines in the spectra becomes more important, in particular
when tools such as Machine Learning become better able to assist in
the full exploitation of ALMA data (Guglielmetti et al. 2023).


**9** **CONCLUSIONS**


The ANGELS observations have efficiently shared calibrators to facilitate a spectral survey of sixteen sources in just 6.5 hours of observation time. These observations revealed


 - ALMA targeted 94 lines and detected 66 of these lines. The
majority (54) were seen in emission, with an additional twelve lines
seen in absorption.

 - The dust continuum observations across six bands revealed the

intrinsic nature of the sample, and for two diffuse sources, tapering
was required to image them at _>_ 5 _𝜎_ significance. Of the 26 targets
that have been observed, 21 sources have spectroscopic redshifts that
enabled detailed studies of their emission and absorption lines.

 - The CO SLEDs show a variation of sources, with extreme
SLEDs shown for a small fraction (36%) of sources, which suggests
a fraction of DSFGs are dominated by dense, warm gas.

 - The observations of 12 absorption line features show one rare
case of inflowing gas through a red-shifted molecular absorption
lines, and two cases of strongly outflowing gas through blue-shifted
emission. The sources that are seen in multiple molecular absorption
lines have similar systematic velocity offsets, suggesting that the
absorption features are sensitive to similar regions of the circumgalactic and internal gas.

 - Atomic lines have been detected in three sources, namely: the

[O i] 145 _𝜇_ m emission line in HerBS-41A, and the [N ii] 205 _𝜇_ m
emission line seen in HerBS-170 and HerBS-184, with HerBS-170
being the strongest [N ii] emitter found to date.

 - A stacked spectrum offers a preliminary view on the capabilities
of a large sample, which will be able to characterize DSFGs out to
≈ 2000 GHz.


 - A preliminary bimodal picture of DSFGs is appearing, where
lensed sources are indicative of typically central dusty star-bursts,
found in other surveys to be rotationally stable, while the weakly- or
unlensed HyLIRGs could represent turbulent massive star-forming
events driven by unstable galaxy kinematics and clumpy gas flows.


Exploitation of the complete southern Herschel bright sources
samples could enable a large line survey of ∼350 molecular and
atomic lines, providing robust statistics with a fidelity of ∼10 per


MNRAS **000**, 1–42 (2024)

24 _Bakx et al._


cent. This increase in fidelity will help characterize the diversity of
DSFGs at _cosmic noon_, in order to investigate the origins of the most
violent star-forming events in the Universe. Similarly, studies with
short-wavelengths will enable a complete characterization of the dust,
target short-wavelength emission lines, and allow for a more accurate
separation of the unresolved _Herschel_ fluxes. With the advent of the
WSU (Carpenter et al. 2023), this method will become even more
efficient – and arguably important to include in most observations – as
the bandwidths of ALMA receivers and capabilities of the correlators
increase in the near future.


**ACKNOWLEDGEMENTS**


The authors kindly thank the anonymous referee for their insightful comments and suggestions to improve this manuscript. Financial
support from the Knut and Alice Wallenberg foundation is gratefully acknowledged through grant no. KAW 2020.0081. This work
was supprted by NAOJ ALMA Scientific Research Grant Numbers 2018-09B and JSPS KAKENHI No. 17H06130, 22H04939,
and 22J21948, 22KJ1598. SS was partly supported by the ESCAPE project; ESCAPE - The European Science Cluster of Astronomy and Particle Physics ESFRI Research Infrastructures has
received funding from the European Union’s Horizon 2020 research and innovation programme under Grant Agreement no.
824064. SS also thanks the Science and Technology Facilities Council for financial support under grant ST/P000584/1. SU would
like to thank the Open University School of Physical Sciences
for supporting this work. This paper makes use of the following
ALMA data: ADS/JAO.ALMA#2016.2.00133.S, 2018.1.00804.S,
2019.1.01477.S, and 2021.1.01628.S.


**DATA AVAILABILITY**


The data underlying this article will be shared on reasonable request
to the corresponding author.


**REFERENCES**


[Amvrosiadis A., et al., 2018, MNRAS, 475, 4939](http://dx.doi.org/10.1093/mnras/sty138)
[Andrews B. H., Thompson T. A., 2011, ApJ, 727, 97](http://dx.doi.org/10.1088/0004-637X/727/2/97)
[Aravena M., et al., 2016, MNRAS, 457, 4406](http://dx.doi.org/10.1093/mnras/stw275)
[Asayama S., et al., 2014, PASJ, 66, 57](http://dx.doi.org/10.1093/pasj/psu026)
[Bakx T., Conway J., 2024, arXiv e-prints, p. arXiv:2409.02164](http://dx.doi.org/10.48550/arXiv.2409.02164)
[Bakx T. J. L. C., Dannerbauer H., 2022, MNRAS, 515, 678](http://dx.doi.org/10.1093/mnras/stac1306)

[Bakx T. J. L. C., et al., 2018, MNRAS, 473, 1751](http://dx.doi.org/10.1093/mnras/stx2267)

[Bakx T. J. L. C., Eales S., Amvrosiadis A., 2020a, MNRAS, 493, 4276](http://dx.doi.org/10.1093/mnras/staa506)

[Bakx T. J. L. C., et al., 2020b, MNRAS, 494, 10](http://dx.doi.org/10.1093/mnras/staa658)

[Bakx T. J. L. C., et al., 2021, MNRAS, 508, L58](http://dx.doi.org/10.1093/mnrasl/slab104)

[Bakx T. J. L. C., et al., 2023, MNRAS, 519, 5076](http://dx.doi.org/10.1093/mnras/stac3723)
Bakx T. J. L. C., Gray B. S., González-Nuevo J., Bonavera L., Amvrosiadis
[A., Eales S., Hagimoto M., Serjeant S., 2024, MNRAS, 527, 8865](http://dx.doi.org/10.1093/mnras/stad3759)
[Barnes J. E., Hernquist L. E., 1991, ApJ, 370, L65](http://dx.doi.org/10.1086/185978)
[Barro G., et al., 2016, ApJ, 827, L32](http://dx.doi.org/10.3847/2041-8205/827/2/L32)
Baugh C. M., Lacey C. G., Frenk C. S., Granato G. L., Silva L., Bressan A.,
[Benson A. J., Cole S., 2005, MNRAS, 356, 1191](http://dx.doi.org/10.1111/j.1365-2966.2004.08553.x)
[Belitsky V., et al., 2018, A&A, 611, A98](http://dx.doi.org/10.1051/0004-6361/201731883)
[Bendo G. J., et al., 2023, MNRAS, 522, 2995](http://dx.doi.org/10.1093/mnras/stac3771)

[Berman D. A., et al., 2022, MNRAS, 515, 3911](http://dx.doi.org/10.1093/mnras/stac1494)

[Berta S., et al., 2021, A&A, 646, A122](http://dx.doi.org/10.1051/0004-6361/202039743)

[Berta S., et al., 2023, A&A, 678, A28](http://dx.doi.org/10.1051/0004-6361/202346803)

[Béthermin M., et al., 2018, A&A, 620, A115](http://dx.doi.org/10.1051/0004-6361/201833081)

[Birkin J. E., et al., 2021, MNRAS, 501, 3926](http://dx.doi.org/10.1093/mnras/staa3862)


MNRAS **000**, 1–42 (2024)



[Blain A. W., Smail I., Ivison R. J., Kneib J. P., Frayer D. T., 2002, Phys. Rep.,](http://dx.doi.org/10.1016/S0370-1573(02)00134-5)

[369, 111](https://ui.adsabs.harvard.edu/abs/2002PhR...369..111B)
[Blain A. W., Chapman S. C., Smail I., Ivison R., 2004, ApJ, 611, 725](http://dx.doi.org/10.1086/422353)
[Bonato M., et al., 2014, MNRAS, 438, 2547](http://dx.doi.org/10.1093/mnras/stt2375)

[Borsato E., et al., 2023, MNRAS,](http://dx.doi.org/10.1093/mnras/stad3381)

[Bothwell M. S., et al., 2013, MNRAS, 429, 3047](http://dx.doi.org/10.1093/mnras/sts562)
[Bouwens R. J., et al., 2022, ApJ, 931, 160](http://dx.doi.org/10.3847/1538-4357/ac5a4a)
[Brauher J. R., Dale D. A., Helou G., 2008, ApJS, 178, 280](http://dx.doi.org/10.1086/590249)
Bryerton E., Saini K., Muehlberg J., Vaselaar D., Thacker D., 2013, in
IEEE MTT-S International Microwave Symposium Digest. p. 6697622,
[doi:10.1109/MWSYM.2013.6697622](http://dx.doi.org/10.1109/MWSYM.2013.6697622)

[Bussmann R. S., et al., 2013, ApJ, 779, 25](http://dx.doi.org/10.1088/0004-637X/779/1/25)
[Butler K. M., et al., 2021, ApJ, 919, 5](http://dx.doi.org/10.3847/1538-4357/ac0c7a)
Butler K. M., van der Werf P. P., Topkaras T., Rybak M., Venemans B. P.,
[Walter F., Decarli R., 2023, ApJ, 944, 134](http://dx.doi.org/10.3847/1538-4357/acad03)
[CASA Team et al., 2022, PASP, 134, 114501](http://dx.doi.org/10.1088/1538-3873/ac9642)

[Cañameras R., et al., 2018, A&A, 620, A61](http://dx.doi.org/10.1051/0004-6361/201833625)

[Cañameras R., et al., 2021, A&A, 645, A45](http://dx.doi.org/10.1051/0004-6361/202038979)
[Cai Z.-Y., et al., 2013, ApJ, 768, 21](http://dx.doi.org/10.1088/0004-637X/768/1/21)
[Carilli C. L., Walter F., 2013, ARA&A, 51, 105](http://dx.doi.org/10.1146/annurev-astro-082812-140953)
Carpenter J., Brogan C., Iono D., Mroczkowski T., 2023, in Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial
Scales. p. 304 ( `[arXiv:2211.00195](http://arxiv.org/abs/2211.00195)` [), doi:10.48550/arXiv.2211.00195](http://dx.doi.org/10.48550/arXiv.2211.00195)
[Casey C. M., 2016, ApJ, 824, 36](http://dx.doi.org/10.3847/0004-637X/824/1/36)
[Casey C. M., Narayanan D., Cooray A., 2014, Phys. Rep., 541, 45](http://dx.doi.org/10.1016/j.physrep.2014.02.009)
[Chen C.-C., et al., 2017, ApJ, 846, 108](http://dx.doi.org/10.3847/1538-4357/aa863a)
[Chen C.-C., et al., 2022, ApJ, 929, 159](http://dx.doi.org/10.3847/1538-4357/ac61df)
[Cheng C., et al., 2020, ApJ, 898, 33](http://dx.doi.org/10.3847/1538-4357/ab980b)
[Chiang Y.-K., Overzier R., Gebhardt K., 2013, ApJ, 779, 127](http://dx.doi.org/10.1088/0004-637X/779/2/127)
Chiang Y.-K., Overzier R. A., Gebhardt K., Henriques B., 2017, [ApJ,](http://dx.doi.org/10.3847/2041-8213/aa7e7b) [844,](https://ui.adsabs.harvard.edu/abs/2017ApJ...844L..23C)

[L23](https://ui.adsabs.harvard.edu/abs/2017ApJ...844L..23C)

[Cibinel A., et al., 2017, MNRAS, 469, 4683](http://dx.doi.org/10.1093/mnras/stx1112)
Claude S., et al., 2008, in Duncan W. D., Holland W. S., Withington
S., Zmuidzinas J., eds, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series Vol. 7020, Millimeter and Submillimeter Detectors and Instrumentation for Astronomy IV. p. 70201B,

[doi:10.1117/12.788128](http://dx.doi.org/10.1117/12.788128)

[Cochrane R. K., et al., 2021, MNRAS, 503, 2622](http://dx.doi.org/10.1093/mnras/stab467)

[Cormier D., et al., 2015, A&A, 578, A53](http://dx.doi.org/10.1051/0004-6361/201425207)
Cortes P. C., et al., 2023, ALMA Cycle 10 Technical Handbook, ALMA Doc.
8.3. Joint ALMA Observatory, Vitacura, Santiago, Chile
[Cox P., et al., 2023, A&A, 678, A26](http://dx.doi.org/10.1051/0004-6361/202346801)
[Cunningham D. J. M., et al., 2020, MNRAS, 494, 4090](http://dx.doi.org/10.1093/mnras/staa820)
[Czekala I., et al., 2021, ApJS, 257, 2](http://dx.doi.org/10.3847/1538-4365/ac1430)
[Daddi E., et al., 2015, A&A, 577, A46](http://dx.doi.org/10.1051/0004-6361/201425043)
Davé R., Finlator K., Oppenheimer B. D., Fardal M., Katz N., Kereš D.,
[Weinberg D. H., 2010, MNRAS, 404, 1355](http://dx.doi.org/10.1111/j.1365-2966.2010.16395.x)
[Dekel A., et al., 2009, Nature, 457, 451](http://dx.doi.org/10.1038/nature07648)
[Díaz-Santos T., et al., 2017, ApJ, 846, 32](http://dx.doi.org/10.3847/1538-4357/aa81d7)
[Doherty M. J., Geach J. E., Ivison R. J., Dye S., 2020, ApJ, 905, 152](http://dx.doi.org/10.3847/1538-4357/abc5b9)
Dunne L., Maddox S. J., Vlahakis C., Gomez H. L., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa3526) [501,](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501.2573D)

[2573](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501.2573D)

Dunne L., Maddox S. J., Papadopoulos P. P., Ivison R. J., Gomez H. L., 2022,

[MNRAS,](http://dx.doi.org/10.1093/mnras/stac2098)
[Dye S., et al., 2015, MNRAS, 452, 2258](http://dx.doi.org/10.1093/mnras/stv1442)
[Dye S., et al., 2018, MNRAS, 476, 4383](http://dx.doi.org/10.1093/mnras/sty513)
Eales S., Lilly S., Gear W., Dunne L., Bond J. R., Hammer F., Le Fèvre O.,
[Crampton D., 1999, ApJ, 515, 518](http://dx.doi.org/10.1086/307069)
[Eales S., et al., 2010, PASP, 122, 499](http://dx.doi.org/10.1086/653086)
Ediss G. A., et al., 2004, in Narayanan G., ed., Fifteenth International Symposium on Space Terahertz Technology. pp 181–188
[Enia A., et al., 2018, MNRAS, 475, 3467](http://dx.doi.org/10.1093/mnras/sty021)
[Etherington A., et al., 2023, MNRAS, 521, 6005](http://dx.doi.org/10.1093/mnras/stad582)
[Falgarone E., et al., 2017, Nature, 548, 430](http://dx.doi.org/10.1038/nature23298)
[Ferrara A., et al., 2022, MNRAS, 512, 58](http://dx.doi.org/10.1093/mnras/stac460)
[Fixsen D. J., Bennett C. L., Mather J. C., 1999, ApJ, 526, 207](http://dx.doi.org/10.1086/307962)
Fraternali F., Karim A., Magnelli B., Gómez-Guĳarro C., Jiménez-Andrade
[E. F., Posses A. C., 2021, A&A, 647, A194](http://dx.doi.org/10.1051/0004-6361/202039807)

[Fudamoto Y., et al., 2017, MNRAS, 472, 2028](http://dx.doi.org/10.1093/mnras/stx1956)

[Furlanetto S. R., Mirocha J., 2022, MNRAS, 511, 3895](http://dx.doi.org/10.1093/mnras/stac310)

[Garratt T. K., et al., 2023, MNRAS, 520, 3669](http://dx.doi.org/10.1093/mnras/stad307)
[Gehrels N., 1986, ApJ, 303, 336](http://dx.doi.org/10.1086/164079)
[Glazebrook K., et al., 2017, Nature, 544, 71](http://dx.doi.org/10.1038/nature21680)

[Griffin M. J., et al., 2010, A&A, 518, L3](http://dx.doi.org/10.1051/0004-6361/201014519)
[Guglielmetti F., et al., 2023, arXiv e-prints, p. arXiv:2311.10657](http://dx.doi.org/10.48550/arXiv.2311.10657)
[Gullberg B., et al., 2019, MNRAS, 490, 4956](http://dx.doi.org/10.1093/mnras/stz2835)
[Hagimoto M., et al., 2023, MNRAS, 521, 5508](http://dx.doi.org/10.1093/mnras/stad784)
Hainline L. J., Blain A. W., Smail I., Alexander D. M., Armus L., Chapman
[S. C., Ivison R. J., 2011, ApJ, 740, 96](http://dx.doi.org/10.1088/0004-637X/740/2/96)
[Harrington K. C., et al., 2016, MNRAS, 458, 4383](http://dx.doi.org/10.1093/mnras/stw614)
[Harrington K. C., et al., 2021, ApJ, 908, 95](http://dx.doi.org/10.3847/1538-4357/abcc01)
Hatsukade B., Tamura Y., Iono D., Matsuda Y., Hayashi M., Oguri M., 2015,

[PASJ, 67, 93](http://dx.doi.org/10.1093/pasj/psv061)

Henkel C., Downes D., Weiß A., Riechers D., Walter F., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/200912889) [516,](https://ui.adsabs.harvard.edu/abs/2010A&A...516A.111H)

[A111](https://ui.adsabs.harvard.edu/abs/2010A&A...516A.111H)

[Herrera-Camus R., et al., 2018, ApJ, 861, 94](http://dx.doi.org/10.3847/1538-4357/aac0f6)
[Hickox R. C., et al., 2012, MNRAS, 421, 284](http://dx.doi.org/10.1111/j.1365-2966.2011.20303.x)
Hlavacek-Larrondo J., Li Y., Churazov E., 2022, in, Handbook of X-ray
and Gamma-ray Astrophysics. Edited by Cosimo Bambi and Andrea
[Santangelo. p. 5, doi:10.1007/978-981-16-4544-0_122-1](http://dx.doi.org/10.1007/978-981-16-4544-0_122-1)
[Hodge J. A., et al., 2013, ApJ, 768, 91](http://dx.doi.org/10.1088/0004-637X/768/1/91)
[Hodge J. A., et al., 2016, ApJ, 833, 103](http://dx.doi.org/10.3847/1538-4357/833/1/103)
[Hodge J. A., et al., 2019, ApJ, 876, 130](http://dx.doi.org/10.3847/1538-4357/ab1846)
[Hopkins P. F., Hernquist L., Cox T. J., Kereš D., 2008, ApJS, 175, 356](http://dx.doi.org/10.1086/524362)
[Hughes D. H., et al., 1998, Nature, 394, 241](http://dx.doi.org/10.1038/28328)
[Ikarashi S., et al., 2017, ApJ, 849, L36](http://dx.doi.org/10.3847/2041-8213/aa9572)
[Ikeda R., et al., 2022, ApJ, 933, 11](http://dx.doi.org/10.3847/1538-4357/ac6cdc)
[Inami H., et al., 2022, MNRAS, 515, 3126](http://dx.doi.org/10.1093/mnras/stac1779)
Indriolo N., Bergin E. A., Falgarone E., Godard B., Zwaan M. A., Neufeld
[D. A., Wolfire M. G., 2018, ApJ, 865, 127](http://dx.doi.org/10.3847/1538-4357/aad7b3)
[Ismail D., et al., 2023, A&A, 678, A27](http://dx.doi.org/10.1051/0004-6361/202346804)

[Ivison R. J., et al., 2010, A&A, 518, L35](http://dx.doi.org/10.1051/0004-6361/201014548)
[Ivison R. J., et al., 2016, ApJ, 832, 78](http://dx.doi.org/10.3847/0004-637X/832/1/78)
[Jorsater S., van Moorsel G. A., 1995, AJ, 110, 2037](http://dx.doi.org/10.1086/117668)
[Kamieneski P. S., et al., 2024, ApJ, 961, 2](http://dx.doi.org/10.3847/1538-4357/acf930)
[Karim A., et al., 2013, MNRAS, 432, 2](http://dx.doi.org/10.1093/mnras/stt196)
[Kennicutt Robert C. J., 1989, ApJ, 344, 685](http://dx.doi.org/10.1086/167834)
[Kennicutt Robert C. J., 1998, ApJ, 498, 541](http://dx.doi.org/10.1086/305588)
[Kennicutt Robert C. J., De Los Reyes M. A. C., 2021, ApJ, 908, 61](http://dx.doi.org/10.3847/1538-4357/abd3a2)
Kerr A. R., et al., 2004, in Narayanan G., ed., Fifteenth International Symposium on Space Terahertz Technology. pp 55–61
Kerr A. R., Pan S.-K., Claude S. M. X., Dindo P., Lichtenberger A. W., Effland
J. E., Lauria E. F., 2014, IEEE Transactions on Terahertz Science and
[Technology, 4, 201](http://dx.doi.org/10.1109/TTHZ.2014.2302537)
[Krumholz M. R., Dekel A., McKee C. F., 2012, ApJ, 745, 69](http://dx.doi.org/10.1088/0004-637X/745/1/69)
[Le Fèvre O., et al., 2020, A&A, 643, A1](http://dx.doi.org/10.1051/0004-6361/201936965)
[Lee M. M., et al., 2019, ApJ, 883, L29](http://dx.doi.org/10.3847/2041-8213/ab412e)
[Lee M. M., et al., 2021, ApJ, 913, 41](http://dx.doi.org/10.3847/1538-4357/abe7ea)
[Liao C.-L., et al., 2024, ApJ, 961, 226](http://dx.doi.org/10.3847/1538-4357/ad148c)
Lilly S. J., Eales S. A., Gear W. K. P., Hammer F., Le Fèvre O., Crampton
[D., Bond J. R., Dunne L., 1999, ApJ, 518, 641](http://dx.doi.org/10.1086/307310)
Long A. S., Casey C. M., del P. Lagos C., Lambrides E. L., Zavala J. A.,
[Champagne J., Cooper O. R., Cooray A. R., 2023, ApJ, 953, 11](http://dx.doi.org/10.3847/1538-4357/acddde)
[Madau P., Dickinson M., 2014, ARA&A, 52, 415](http://dx.doi.org/10.1146/annurev-astro-081811-125615)

Mahieu S., et al., 2012, IEEE Transactions on [Terahertz](http://dx.doi.org/10.1109/TTHZ.2011.2177734) Science and Tech[nology, 2, 29](http://dx.doi.org/10.1109/TTHZ.2011.2177734)
[Maiolino R., Mannucci F., 2019, A&ARv, 27, 3](http://dx.doi.org/10.1007/s00159-018-0112-2)
[Man A., Belli S., 2018, Nature Astronomy, 2, 695](http://dx.doi.org/10.1038/s41550-018-0558-1)
[Maresca J., et al., 2022, MNRAS, 512, 2426](http://dx.doi.org/10.1093/mnras/stac585)

[Martín S., et al., 2021, A&A, 656, A46](http://dx.doi.org/10.1051/0004-6361/202141567)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Meixner M., et al., 2019, arXiv e-prints, p. arXiv:1912.06213](https://ui.adsabs.harvard.edu/abs/2019arXiv191206213M)
[Merlin E., et al., 2019, MNRAS, 490, 3309](http://dx.doi.org/10.1093/mnras/stz2615)



_Efficient high-resolution line survey_ 25


[Montaña A., et al., 2021, MNRAS, 505, 5260](http://dx.doi.org/10.1093/mnras/stab1649)
Narayanan D., Cox T. J., Hayward C. C., Younger J. D., Hernquist L., 2009,

[MNRAS, 400, 1919](http://dx.doi.org/10.1111/j.1365-2966.2009.15581.x)
[Narayanan D., et al., 2015, Nature, 525, 496](http://dx.doi.org/10.1038/nature15383)
[Nayyeri H., et al., 2016, ApJ, 823, 17](http://dx.doi.org/10.3847/0004-637X/823/1/17)
Negrello M., Perrotta F., González-Nuevo J., Silva L., de Zotti G., Granato
[G. L., Baccigalupi C., Danese L., 2007, MNRAS, 377, 1557](http://dx.doi.org/10.1111/j.1365-2966.2007.11708.x)
[Negrello M., et al., 2017, MNRAS, 465, 3558](http://dx.doi.org/10.1093/mnras/stw2911)
[Nightingale J. W., Dye S., 2015, MNRAS, 452, 2940](http://dx.doi.org/10.1093/mnras/stv1455)
[Nightingale J. W., Dye S., Massey R. J., 2018, MNRAS, 478, 4738](http://dx.doi.org/10.1093/mnras/sty1264)
[Nightingale J., et al., 2021, The Journal of Open Source Software, 6, 2825](http://dx.doi.org/10.21105/joss.02825)
[Novak M., et al., 2019, ApJ, 881, 63](http://dx.doi.org/10.3847/1538-4357/ab2beb)
[Oliver S. J., et al., 2012, MNRAS, 424, 1614](http://dx.doi.org/10.1111/j.1365-2966.2012.20912.x)
[Oteo I., et al., 2017, ApJ, 850, 170](http://dx.doi.org/10.3847/1538-4357/aa8ee3)
[Oteo I., et al., 2018, ApJ, 856, 72](http://dx.doi.org/10.3847/1538-4357/aaa1f1)
[Pantoni L., et al., 2021, MNRAS, 504, 928](http://dx.doi.org/10.1093/mnras/stab674)

[Pearson E. A., et al., 2013, MNRAS, 435, 2753](http://dx.doi.org/10.1093/mnras/stt1369)

[Planck Collaboration et al., 2020, A&A, 641, A6](http://dx.doi.org/10.1051/0004-6361/201833910)
[Posses A., et al., 2024, arXiv e-prints, p. arXiv:2403.03379](http://dx.doi.org/10.48550/arXiv.2403.03379)
Powell D., Vegetti S., McKean J. P., Spingola C., Rizzo F., Stacey H. R., 2021,

[MNRAS, 501, 515](http://dx.doi.org/10.1093/mnras/staa2740)
Quirós-Rojas M., Montaña A., Zavala J. A., Aretxaga I., Hughes D. H., 2024,

[arXiv e-prints, p. arXiv:2406.15729](http://dx.doi.org/10.48550/arXiv.2406.15729)
[Ramos Padilla A. F., Wang L., van der Tak F. F. S., Trager S. C., 2023, A&A,](http://dx.doi.org/10.1051/0004-6361/202243358)

[679, A131](https://ui.adsabs.harvard.edu/abs/2023A&A...679A.131R)
[Rangwala N., et al., 2011, ApJ, 743, 94](http://dx.doi.org/10.1088/0004-637X/743/1/94)
Rangwala N., Maloney P. R., Glenn J., Wilson C. D., Kamenetzky J., Schirm
[M. R. P., Spinoglio L., Pereira Santaella M., 2014, ApJ, 788, 147](http://dx.doi.org/10.1088/0004-637X/788/2/147)
[Reuter C., et al., 2020, ApJ, 902, 78](http://dx.doi.org/10.3847/1538-4357/abb599)
[Reuter C., et al., 2023, ApJ, 948, 44](http://dx.doi.org/10.3847/1538-4357/acaf51)
Riechers D. A., Walter F., Carilli C. L., Weiss A., Bertoldi F., Menten K. M.,
[Knudsen K. K., Cox P., 2006, ApJ, 645, L13](http://dx.doi.org/10.1086/505908)
[Riechers D. A., Weiß A., Walter F., Wagg J., 2010, ApJ, 725, 1032](http://dx.doi.org/10.1088/0004-637X/725/1/1032)
[Riechers D. A., et al., 2013, Nature, 496, 329](http://dx.doi.org/10.1038/nature12050)
[Riechers D. A., Cooray A., Pérez-Fournon I., Neri R., 2021, ApJ, 913, 141](http://dx.doi.org/10.3847/1538-4357/abf6d7)
Rizzo F., Vegetti S., Powell D., Fraternali F., McKean J. P., Stacey H. R.,
[White S. D. M., 2020, Nature, 584, 201](http://dx.doi.org/10.1038/s41586-020-2572-6)
[Rizzo F., et al., 2024, arXiv e-prints, p. arXiv:2407.06261](http://dx.doi.org/10.48550/arXiv.2407.06261)
[Rosenberg M. J. F., et al., 2015, ApJ, 801, 72](http://dx.doi.org/10.1088/0004-637X/801/2/72)
[Rowan-Robinson M., et al., 2018, A&A, 619, A169](http://dx.doi.org/10.1051/0004-6361/201832671)
[Rujopakarn W., et al., 2019, ApJ, 882, 107](http://dx.doi.org/10.3847/1538-4357/ab3791)
Rybak M., McKean J. P., Vegetti S., Andreani P., White S. D. M., 2015,

[MNRAS, 451, L40](http://dx.doi.org/10.1093/mnrasl/slv058)
[Rybak M., et al., 2019, ApJ, 876, 112](http://dx.doi.org/10.3847/1538-4357/ab0e0f)
[Rybak M., et al., 2022, A&A, 667, A70](http://dx.doi.org/10.1051/0004-6361/202243894)
Sanders D. B., Soifer B. T., Elias J. H., Madore B. F., Matthews K., Neuge[bauer G., Scoville N. Z., 1988, ApJ, 325, 74](http://dx.doi.org/10.1086/165983)
[Schmidt M., 1959, ApJ, 129, 243](http://dx.doi.org/10.1086/146614)
[Schreiber C., et al., 2018, A&A, 618, A85](http://dx.doi.org/10.1051/0004-6361/201833070)
Sekimoto Y., Iizuko Y., Satou N., Ito T., Kumagai K., Kamikura M., Naruse
M., Shan W. L., 2008, in Wild W., ed., Ninteenth International Symposium on Space Terahertz Technology. pp 253–257
[Serjeant S., 2012, MNRAS, 424, 2429](http://dx.doi.org/10.1111/j.1365-2966.2012.20761.x)
[Serjeant S., 2024, Research Notes of the American Astronomical Society, 8,](http://dx.doi.org/10.3847/2515-5172/ad2bfe)
[52](https://ui.adsabs.harvard.edu/abs/2024RNAAS...8...52S)

Sérsic J. L., 1963, Boletin de la Asociacion Argentina de Astronomia La Plata
[Argentina, 6, 41](https://ui.adsabs.harvard.edu/abs/1963BAAA....6...41S)
[Shirley R., et al., 2021, MNRAS, 507, 129](http://dx.doi.org/10.1093/mnras/stab1526)
[Simpson J. M., et al., 2019, ApJ, 880, 43](http://dx.doi.org/10.3847/1538-4357/ab23ff)
[Smail I., Ivison R. J., Blain A. W., 1997, ApJ, 490, L5](http://dx.doi.org/10.1086/311017)
[Smail I., et al., 2023, arXiv e-prints, p. arXiv:2306.16039](http://dx.doi.org/10.48550/arXiv.2306.16039)
[Spilker J. S., et al., 2014, ApJ, 785, 149](http://dx.doi.org/10.1088/0004-637X/785/2/149)
Spilker J. S., Bezanson R., Marrone D. P., Weiner B. J., Whitaker K. E.,
[Williams C. C., 2016, ApJ, 832, 19](http://dx.doi.org/10.3847/0004-637X/832/1/19)
[Spilker J. S., et al., 2018, Science, 361, 1016](http://dx.doi.org/10.1126/science.aap8900)
[Spilker J. S., et al., 2020a, ApJ, 905, 85](http://dx.doi.org/10.3847/1538-4357/abc47f)
[Spilker J. S., et al., 2020b, ApJ, 905, 86](http://dx.doi.org/10.3847/1538-4357/abc4e6)
[Springel V., 2005, MNRAS, 364, 1105](http://dx.doi.org/10.1111/j.1365-2966.2005.09655.x)


MNRAS **000**, 1–42 (2024)

26 _Bakx et al._


[Stacey G. J., 2011, IEEE Transactions on Terahertz Science and Technology,](http://dx.doi.org/10.1109/TTHZ.2011.2159649)

[1, 241](https://ui.adsabs.harvard.edu/abs/2011ITTST...1..241S)
[Stanley F., et al., 2023, ApJ, 945, 24](http://dx.doi.org/10.3847/1538-4357/acb6f7)
[Straatman C. M. S., et al., 2014, ApJ, 783, L14](http://dx.doi.org/10.1088/2041-8205/783/1/L14)
Sulzenauer N., Dannerbauer H., Díaz-Sánchez A., Ziegler B., Iglesias-Groth
[S., Rebolo R., 2021, ApJ, 923, L27](http://dx.doi.org/10.3847/2041-8213/ac2eba)
[Sun F., et al., 2021, ApJ, 908, 192](http://dx.doi.org/10.3847/1538-4357/abd6e4)
[Suyu S. H., Marshall P. J., Hobson M. P., Blandford R. D., 2006, MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2006.10733.x)

[371, 983](https://ui.adsabs.harvard.edu/abs/2006MNRAS.371..983S)

[Swinbank A. M., et al., 2010, Nature, 464, 733](http://dx.doi.org/10.1038/nature08880)
[Tacconi L. J., et al., 2013, ApJ, 768, 74](http://dx.doi.org/10.1088/0004-637X/768/1/74)
[Tadaki K.-i., et al., 2017, ApJ, 834, 135](http://dx.doi.org/10.3847/1538-4357/834/2/135)
[Tadaki K.-i., et al., 2020, ApJ, 901, 74](http://dx.doi.org/10.3847/1538-4357/abaf4a)
[Tadaki K.-i., et al., 2022, PASJ, 74, L9](http://dx.doi.org/10.1093/pasj/psac018)
Tamura Y., Oguri M., Iono D., Hatsukade B., Matsuda Y., Hayashi M., 2015,

[PASJ, 67, 72](http://dx.doi.org/10.1093/pasj/psv040)
[Tielens A. G. G. M., Hollenbach D., 1985, ApJ, 291, 722](http://dx.doi.org/10.1086/163111)
[Toft S., et al., 2014, ApJ, 782, 68](http://dx.doi.org/10.1088/0004-637X/782/2/68)
[Trujillo I., Erwin P., Asensio Ramos A., Graham A. W., 2004, AJ, 127, 1917](http://dx.doi.org/10.1086/382712)
[Tsukui T., Wisnioski E., Krumholz M. R., Battisti A., 2023, arXiv e-prints,](http://dx.doi.org/10.48550/arXiv.2302.07272)

[p. arXiv:2302.07272](https://ui.adsabs.harvard.edu/abs/2023arXiv230207272T)
[Ura R., et al., 2023, ApJ, 948, 3](http://dx.doi.org/10.3847/1538-4357/acc530)
[Urquhart S. A., et al., 2022, arXiv e-prints, p. arXiv:2201.07815](https://ui.adsabs.harvard.edu/abs/2022arXiv220107815U)
[Valentino F., et al., 2020a, A&A, 641, A155](http://dx.doi.org/10.1051/0004-6361/202038322)
[Valentino F., et al., 2020b, ApJ, 890, 24](http://dx.doi.org/10.3847/1538-4357/ab6603)
[Valiante E., et al., 2016, MNRAS, 462, 3146](http://dx.doi.org/10.1093/mnras/stw1806)
[Viero M. P., et al., 2014, ApJS, 210, 22](http://dx.doi.org/10.1088/0067-0049/210/2/22)
[Vogelsberger M., et al., 2020, MNRAS, 492, 5167](http://dx.doi.org/10.1093/mnras/staa137)
[Ward B. A., et al., 2022, MNRAS, 510, 2261](http://dx.doi.org/10.1093/mnras/stab3300)
[Warren S. J., Dye S., 2003, ApJ, 590, 673](http://dx.doi.org/10.1086/375132)
Weiß A., Downes D., Neri R., Walter F., Henkel C., Wilner D. J., Wagg J.,
[Wiklind T., 2007, A&A, 467, 955](http://dx.doi.org/10.1051/0004-6361:20066117)
[Weiß A., et al., 2009, ApJ, 707, 1201](http://dx.doi.org/10.1088/0004-637X/707/2/1201)
[Yang C., et al., 2016, A&A, 595, A80](http://dx.doi.org/10.1051/0004-6361/201628160)
[Yang C., et al., 2017, A&A, 608, A144](http://dx.doi.org/10.1051/0004-6361/201731391)
[Yang C., et al., 2023, A&A, 680, A95](http://dx.doi.org/10.1051/0004-6361/202347610)
Zavala J. A., Casey C. M., da Cunha E., Spilker J., Staguhn J., Hodge J., Drew
[P. M., 2018, ApJ, 869, 71](http://dx.doi.org/10.3847/1538-4357/aaecd2)
[Zavala J. A., et al., 2022, ApJ, 933, 242](http://dx.doi.org/10.3847/1538-4357/ac7560)
[Zhang Z.-Y., et al., 2018, MNRAS, 481, 59](http://dx.doi.org/10.1093/mnras/sty2082)
[Zolotov A., et al., 2015, MNRAS, 450, 2327](http://dx.doi.org/10.1093/mnras/stv740)
[de los Reyes M. A. C., Kennicutt Robert C. J., 2019a, ApJ, 872, 16](http://dx.doi.org/10.3847/1538-4357/aafa82)
[de los Reyes M. A. C., Kennicutt Robert C. J., 2019b, ApJ, 878, 74](http://dx.doi.org/10.3847/1538-4357/ab22af)
[van der Werf P. P., et al., 2010, A&A, 518, L42](http://dx.doi.org/10.1051/0004-6361/201014682)


**AFFILIATIONS**


MNRAS **000**, 1–42 (2024)

1 _Department_ _of_ _Space,_ _Earth,_ _&_ _Environment,_ _Chalmers_ _University_ _of_

_Technology, Chalmersplatsen 4 412 96 Gothenburg, Sweden_
2 _Department_ _of_ _Physics,_ _Graduate_ _School_ _of_ _Science,_ _Nagoya_ _University,_

_Aichi 464-8602, Japan_
3 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1,_ _Osawa,_ _Mitaka,_

_Tokyo, Japan_
4 _Centre_ _for_ _Extragalactic_ _Astronomy,_ _Durham_ _University,_ _Department_ _of_

_Physics, South Road, Durham DH1 3LE, UK_
5 _UK_ _ALMA_ _Regional_ _Centre_ _Node,_ _Jodrell_ _Bank_ _Centre_ _for_ _Astrophysics,_

_Department of Physics and Astronomy,_

_University of Manchester, Oxford Road, Manchester M13 9PL, UK_
6 _Hiroshima_ _Astrophysical_ _Science_ _Center,_ _Hiroshima_ _University,_ _1-3-1_

_Kagamiyama, Higashi-Hiroshima, Hiroshima 739-8526, Japan_
7 _School_ _of_ _Physical_ _Sciences,_ _The_ _Open_ _University,_ _Milton_ _Keynes,_ _MK7_

_6AA, UK_
8 _Departamento de Fisica, Universidad de Oviedo, C. Federico Garcia Lorca_

_18, E-33007 Oviedo, Spain_
9 _Instituto_ _Universitario_ _de_ _Ciencias_ _y_ _Tecnologas_ _Espaciales_ _de_ _Asturias_

_(ICTEA), C. Independencia 13, E-33004 Oviedo, Spain_
10 _INAF,_ _Osservatorio_ _Astronomico_ _di_ _Padova,_ _Vicolo_ _Osservatorio_ _5,_

_I-35122 Padova, Italy_
11 _Institut_ _d’Astrophysique_ _de_ _Paris,_ _Sorbonne_ _Université,UPMC_ _Université_

_Paris_ _6_ _and_ _CNRS,_ _UMR_ _7095,_ _98_ _bis_ _boulevard_ _Arago,_ _F-75014_ _Paris,_

_France_
12 _European_ _Southern_ _Observatory,_ _Alonso_ _de_ _Córdova_ _3107,_ _Vitacura,_

_Casilla 19001, Santiago de Chile, Chile_
13 _European_ _Southern_ _Observatory_ _(ESO),_ _Karl-Schwarzschild-Strasse_ _2,_

_D-85748 Garching, Germany_
14 _School_ _of_ _Cosmic_ _Physics,_ _Dublin_ _Institute_ _for_ _Advanced_ _Studies,_ _31_

_Fitzwilliam Place, Dublin D02 XF86, Ireland_
15 _Institute_ _for_ _Astronomy,_ _University_ _of_ _Edinburgh,_ _Royal_ _Observatory,_

_Blackford Hill, Edinburgh EH9 3HJ, UK_
16 _ARC_ _Centre_ _of_ _Excellence_ _for_ _All_ _Sky_ _Astrophysics_ _in_ _3_ _Dimensions_

_(ASTRO 3D)_
17 _School_ _of_ _Earth_ _and_ _Space_ _Exploration,_ _Arizona_ _State_ _University,_ _Tempe,_

_AZ 85287-6004, USA_
18 _Department_ _of_ _Astronomy,_ _University_ _of_ _Cape_ _Town,_ _Private_ _Bag_ _X3,_

_Rondebosch 7701, Cape Town, South Africa_
19 _INAF,_ _Instituto_ _di_ _Radioastronomia-Italian_ _ARC,_ _Via_ _Piero_ _Gobetti_ _101,_

_I-40129 Bologna, Italy_
20 _I._ _Physikalisches_ _Institut,_ _Universität_ _zu_ _Köln,_ _Zülpicher_ _Strasse_ _77,_

_D-50937 Köln, Germany_
21 _Research_ _School_ _of_ _Astronomy_ _and_ _Astrophysics,_ _Australian_ _National_

_University, Cotter Road, Weston Creek, ACT 2611, Australia_
22 _Leiden_ _Observatory,_ _Leiden_ _University,_ _PO_ _Box_ _9513,_ _NL-2300_ _RA_

_Leiden, Netherlands_
23 _INAF_ _-_ _Osservatorio_ _Astronomico_ _di_ _Roma,_ _via_ _di_ _Frascati_ _33,_ _I-00078_

_Monte Porzio Catone, Italy_
24 _Institut de Radioastronomie Millimétrique (IRAM), 300 Rue de la Piscine,_

_38400 Saint-Martin-d’Hères, France_
25 _Department_ _of_ _Physics_ _&_ _Astronomy,_ _University_ _of_ _California,_ _Irvine,_

_4129 Reines Hall, Irvine, CA 92697, USA_
26 _School of Physics and Astronomy, Cardiff University, The Parade, Cardiff,_

_CF24 3AA, UK_
27 _Department of Astronomy, School of Science, SOKENDAI (The Graduate_

_University_ _for_ _Advanced_ _Studies),_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_

_Japan_
28 _Department of Astronomy, The University of Tokyo, 7-3-1 Hongo, Bunkyo,_

_Tokyo 113-0033, Japan_
29 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _British_ _Columbia,_

_6224 Agricultural Road, Vancouver, BC V6T 1Z1, Canada_
30 _Astrophysics_ _Branch,_ _NASA—Ames_ _Research_ _Center,_ _MS_ _245-6,_ _Moffett_



_Efficient high-resolution line survey_ 27


_Field, CA 94035, USA_


MNRAS **000**, 1–42 (2024)

28 _Bakx et al._


**APPENDIX A:** **GRAPH TO OPTIMIZE THE OBSERVING**

**BANDS**


Figure A1 shows the tool used to define the optimum observing
conditions for efficiently targeting as many spectral lines as possible.


**APPENDIX B:** **SOURCES WITHOUT SPECTROSCOPIC**

**REDSHIFTS**


In this section we report the seven sources without spectroscopic redshifts that were included in the field-of-view of ALMA. We present
their continua in Figure B1.


**APPENDIX C:** **SPECTRAL LINE PROFILES**


The tabulated measured properties of the spectral lines are shown in
Table C1. All detected lines are shown in Figures C1.


MNRAS **000**, 1–42 (2024)

_Efficient high-resolution line survey_ 29


**Figure A1.** These six graphs were used to find the optimum tuning of each of the bands to target the most lines given a fixed spectral set-up. The _x_ -axis shows the
frequency set-up by indicating the lowest frequency of the spectral windows, and the lower- and upper-sidebands are separated by 8 GHz. The grey bar indicates
the selected frequency set-up, and the dashed line indicates the total number of expected lines that are targeted with the observations. The optical transparency
of the atmosphere is indicated by the bottom panel of each graph, between 1 (fully transparent) and 0 (fully opaque), in order to evaluate the effect of the optical
transmission while targeting as many lines as possible. Notable absorptions include the water feature in Band 5, a central absorption component in Band 7, and
the majority of Band 8. As such, we did not always choose the highest position in the top panel for our observations.


MNRAS **000**, 1–42 (2024)

30 _Bakx et al._


**Figure B1.** These sources are not the main targets in the ANGELS data, but were found through unresolved BEARS observations (Bendo et al. 2023). They do
not have spectroscopic redshifts, and the majority are not completely covered by the primary beam (pb-cor _<_ 0 _._ 3) for the highest frequencies. Here, we show
the images before the primary beam correction to better showcase the source across the bands.


MNRAS **000**, 1–42 (2024)

_Efficient high-resolution line survey_ 31


Table C1: Line tables


Line Frequency Band SdV dV V - V CO

[GHz] [Jy km/s] [km/s] [km/s]

**HerBS-21 z = 3.323**

[C i] 609 _𝜇𝑚_ 113.847 band 3 _<_ 1 _._ 54
CO (5–4) 133.251 band 4 14.18 ± 3.34 521 ± 92 -23 ± 39
CH [+] (1−0) 193.171 band 5 -1.21 ± 0.75 360 ± 169 205 ± 71
OH [+] (1 2 − 0 1 ) 224.799 band 6 -6.1 ± 1.45 439 ± 78 189 ± 33
OH [+] (1 1 − 0 1 ) 238.982 band 6 -2.54 ± 0.95 177 ± 50 142 ± 21
CO (9–8) 239.851 band 6 8.99 ± 2.82 642 ± 152 13 ± 64
CO (11–10) 293.311 band 7 4.91 ± 1.4 416 ± 89 -109 ± 37
**HerBS-22 z = 3.051**

CO (4–3) 113.820 band 3 11.72 ± 3.25 568 ± 118 34 ± 50
CH [+] (1−0) 206.141 band 5 -0.75 ± 0.36 107 ± 39 -138 ± 15
OH [+] (1 0 − 0 1 ) 224.428 band 6 -1.84 ± 0.75 178 ± 55 -65 ± 23
OH [+] (1 2 − 0 1 ) 239.893 band 6 -5.14 ± 1.0 470 ± 0 -140 ± 44
H 2 O [+] (1 1 _,_ 1 − 0 0 _,_ 0 ) 281.373 band 7 11.89 ± 3.19 941 ± 163 869 ± 93
**HerBS-25 z = 2.912**

CO (5–4) 147.324 band 4 18.96 ± 2.17 226 ± 19 9 ± 8
H 2 O (2 1 _,_ 1 − 2 0 _,_ 2 ) 192.238 band 5 6.35 ± 2.81 478 ± 160 -73 ± 68
CO (7–6) 206.220 band 5 12.61 ± 3.66 249 ± 54 -34 ± 23
H 2 O (3 1 _,_ 2 − 3 0 _,_ 3 ) 280.512 band 7 5.93 ± 2.52 196 ± 63 -106 ± 26
H 2 O [+] (1 1 _,_ 1 − 0 0 _,_ 0 ) 291.299 band 7 3.88 ± 2.7 136 ± 71 -128 ± 30
CO (10–9) 294.661 band 7 17.76 ± 4.98 941 ± 185 357 ± 93
**HerBS-36 z = 3.095**

CO (4–3) 112.619 band 3 6.88 ± 1.85 464 ± 94 -18 ± 40
CH [+] (1−0) 203.926 band 5 -2.23 ± 0.38 283 ± 36 10 ± 15
CO (8–7) 225.208 band 6 5.80 ± 2.03 440 ± 116 -4 ± 49
CO (10–9) 281.541 band 7 4.69 ± 1.79 392 ± 112 56 ± 48
CH [+] (2−1) 407.638 band 8 -5.21 ± 2.03 128 ± 43 64 ± 16
**HerBS-41A z = 4.098**

CO (5–4) 113.147 band 3 5.05 ± 1.64 710 ± 174 12 ± 74
CO (6–5) 135.869 band 4 4.35 ± 1.51 842 ± 221 248 ± 93
H 2 O (2 1 _,_ 1 − 2 0 _,_ 2 ) 147.515 band 4 _<_ 1.89
H 2 O (2 0 _,_ 2 − 1 1 _,_ 1 ) 193.787 band 5 1.31 ± 0.97 647 ± 363 -232 ± 154
OH [+] (1 1 − 0 1 ) 202.652 band 5 -0.88 ± -0.47 349 ± 147 -540 ± 57
CO (9–8) 203.663 band 5 3.44 ± 2.1 790 ± 363 -37 ± 154
H 2 O [+] (1 1 _,_ 1 − 0 0 _,_ 0 ) 223.531 band 6 _<_ 2 _._ 9
CO (10–9) 226.111 band 6 1.59 ± 1.15 940 ± 524 -21 ± 211
CO (13–12) 293.944 band 7 5.77 ± 1.2 941 ± 72 -200 ± 89

[O i] 145 _𝜇𝑚_ 404.081 band 8 10.27 ± 2.72 941 ± 135 -481 ± 106
CO (18–17) 406.999 band 8 3.15 ± 1.11 941 ± 4 -173 ± 299
**HerBS-42A z = 3.307**

CO (5–4) 133.787 band 4 13.42 ± 1.75 667 ± 65 -18 ± 27
CH [+] (1−0) 193.889 band 5 _<_ 1 _._ 13
OH [+] (1 1 − 0 1 ) 225.634 band 6 -0.4 ± 0.32 342 ± 203 -418 ± 86
OH [+] (1 2 − 0 1 ) 239.87 band 6 -0.73 ± 0.5 340 ± 177 -182 ± 75
CO (9–8) 240.775 band 6 10.6 ± 2.84 647 ± 134 -18 ± 53
CO (11–10) 294.401 band 7 7.54 ± 2.94 941 ± 190 255 ± 153
**HerBS-42B z = 3.314**

[C i] 609 _𝜇𝑚_ 114.085 band 3 _<_ 2 _._ 28
CO (5–4) 133.601 band 4 3.35 ± 1.58 564 ± 201 16 ± 85
CH [+] (1−0) 193.574 band 5 _<_ 1 _._ 67
CO (9–8) 240.482 band 6 1.84 ± 0.74 150 ± 45 42 ± 19
OH [+] (1 2 − 0 1 ) 239.48 band 6 _<_ 3 _._ 44
CO (11–10) 293.923 band 7 _<_ 2 _._ 90
**HerBS-81A z = 3.160**

CO (4–3) 110.800 band 3 6.05 ± 2.05 587 ± 150 -63 ± 63
CO (7–6) 194.002 band 5 4.38 ± 1.69 442 ± 129 149 ± 54
_Continued on next page_


MNRAS **000**, 1–42 (2024)

32 _Bakx et al._


MNRAS **000**, 1–42 (2024)



Table C1 – _continued from previous page_


Line Frequency Band SdV dV V - V CO

[GHz] [Jy km/s] [km/s] [km/s]

[C i] 370 _𝜇𝑚_ 194.509 band 5 _<_ 1 _._ 32
H 2 O (2 0 _,_ 2 − 1 1 _,_ 1 ) 237.482 band 6 _<_ 1 _._ 54
H 2 O (3 2 _,_ 1 − 3 1 _,_ 2 ) 279.546 band 7 8.32 ± 4.78 762 ± 336 -337 ± 137
**HerBS-81B z = 2.588**

CO (6–5) 192.976 band 5 3.16 ± 1.93 870 ± 401 61 ± 167
CO (7–6) 225.139 band 6 2.46 ± 1.96 932 ± 563 60 ± 235

[C i] 370 _𝜇𝑚_ 225.769 band 6 _<_ 1 _._ 62
CO (13–12) 418.115 band 8 _<_ 3 _._ 5

[N ii] 205 _𝜇𝑚_ 407.678 band 8 _<_ 3 _._ 87
**HerBS-86 z = 2.564**

CO (6–5) 194.045 band 5 5.36 ± 1.68 532 ± 126 -3 ± 53
CO (7–6) 226.320 band 6 5.32 ± 1.68 446 ± 106 -8 ± 45
**HerBS-87 z = 2.059**

CO (3–2) 113.066 band 3 5.16 ± 2.03 474 ± 156 70 ± 64
CO (6–5) 226.127 band 6 13.84 ± 4.06 280 ± 62 118 ± 26
**HerBS-93 z = 2.402**

CO (3–2) 101.638 band 3 4.01 ± 1.53 821 ± 237 0 ± 100
CO (4–3) 135.547 band 4 8.72 ± 3.22 782 ± 218 -46 ± 92

[C i] 609 _𝜇𝑚_ 144.668 band 4 4.79 ± 2.18 371 ± 140 203 ± 52
CO (6–5) 203.420 band 5 6.1 ± 2.08 941 ± 101 464 ± 215

[C i] 370 _𝜇𝑚_ 237.987 band 6 2.07 ± 1.34 155 ± 76 499 ± 3
CO (12–11) 406.84 band 8 _<_ 2 _._ 67
**HerBS-104 z = 1.536**

[C i] 609 _𝜇𝑚_ 194.070 band 5 3.56 ± 1.0 324 ± 68 58 ± 29
OH [+] (1 1 − 0 1 ) 407.397 band 8 -2.09 ± 1.03 121 ± 45 64 ± 19
**HerBS-106 z = 2.369**

[C i] 609 _𝜇𝑚_ 146.0854 band 4 4.36 ± 1.78 229 ± 70 -31 ± 29
CO (6–5) 205.254 band 5 9.49 ± 2.12 542 ± 91 -11 ± 39
H 2 O (2 1 _,_ 1 − 2 0 _,_ 2 ) 223.221 band 6 _<_ 1 _._ 20
CO (7–6) 239.507 band 6 5.02 ± 2.17 219 ± 71 -14 ± 30

[C i] 370 _𝜇𝑚_ 240.177 band 6 23.39 ± 5.68 941 ± 116 -58 ± 96
H 2 O (2 0 _,_ 2 − 1 1 _,_ 1 ) 293.24 band 7 _<_ 4 _._ 91
**HerBS-155 z = 3.077**

CO (4–3) 113.121 band 3 5.32 ± 0.52 144 ± 15 -20 ± 12
CH [+] (1−0) 204.827 band 5 _<_ 2 _._ 33
OH [+] (1 0 − 0 1 ) 222.997 band 6 _<_ 2 _._ 82
CO (8–7) 226.150 band 6 5.36 ± 1.75 212 ± 52 -2 ± 22
H 2 O [+] (1 1 _,_ 1 − 0 0 _,_ 0 ) 279.51 band 7 _<_ 1 _._ 14
CO (10–9) 282.735 band 7 _<_ 6 _._ 18
**HerBS-159A z = 2.236**
OH [+] (1 0 − 0 1 ) 280.951 band 7 _<_ 2 _._ 6
**HerBS-159B z = 2.236**
OH [+] (1 0 − 0 1 ) 280.951 band 7 _<_ 1 _._ 38
**HerBS-170 z = 4.182**

CO (5–4) 111.188 band 3 _<_ 2 _._ 07
CO (6–5) 133.426 band 4 3.37 ± 1.59 421 ± 150 -15 ± 63
H 2 O (2 1 _,_ 1 − 2 0 _,_ 2 ) 145.079 band 4 _<_ 2 _._ 10
H 2 O (3 2 _,_ 1 − 3 1 _,_ 2 ) 224.344 band 6 4.8 ± 2.61 941 ± 479 43 ± 87
HF (1−0) 237.765 band 6 _<_ 2 _._ 3

[N ii] 205 _𝜇𝑚_ 281.873 band 7 4.36 ± 1.93 304 ± 102 51 ± 43
**HerBS-184 z = 2.507**

CO (3–2) 98.577 band 3 4.32 ± 1.29 395 ± 89 6 ± 37
CH [+] (1−0) 238.118 band 6 _<_ 1 _._ 74
H 2 O (2 0 _,_ 2 − 1 1 _,_ 1 ) 281.701 band 7 1.39 ± 0.96 472 ± 245 -22 ± 104
OH [+] (1 1 − 0 1 ) 294.587 band 7 _<_ 1 _._ 74

[N ii] 205 _𝜇𝑚_ 416.629 band 8 4.15 ± 2.94 362 ± 194 4 ± 82

23 [h] 44 [m] 18.318.2 [s] [s] 18.1 [s] 18.0 [s] 17.9 [s]


RA (ICRS)


23 [h] 44 [m] 18.318.2 [s] [s] 18.1 [s] 18.0 [s] 17.9 [s]


RA (ICRS)


23 [h] 44 [m] 18.318.2 [s] [s] 18.1 [s] 18.0 [s] 17.9 [s]


RA (ICRS)



_Efficient high-resolution line survey_ 33









-30°39'34"


36"


38"


40"


-30°39'34"


36"


38"


40"


-30°39'34"


36"


38"


40"



-30°39'34"


36"



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



38"


40"



-30°39'34"


36"



38"


40"



23 [h] 44 [m] 18.318.2 [s] [s] 18.1 [s] 18.0 [s] 17.9 [s]


RA (ICRS)


23 [h] 44 [m] 18.318.2 [s] [s] 18.1 [s] 18.0 [s] 17.9 [s]


RA (ICRS)


23 [h] 44 [m] 18.318.2 [s] [s] 18.1 [s] 18.0 [s] 17.9 [s]


RA (ICRS)



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-21 at _𝑧_ = 3 _._ 323. The white contours show the untapered band 7 image at 2 _,_ 3 _,_ 5 _...𝜎_, and
the red solid / blue dashed contours show the +/−2 _,_ 3 _,_ 5 _...𝜎_ moment-0 line emission. The yellow contour shows the selected aperture based on the selection
criteria highlighted in the bottom-right of the spectrum, using an aperture based on the tapered band 7 continuum ( _𝜎_ cont ) and moment-0 ( _𝜎_ mom−0 ) emission,
which are subsequently tapered by N beams times the moment-0 beam. Similarly, the moment-0 image is created from the highlighted emission bins. The line
properties listed in Table C1 are derived from the line fits.




1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



-34°17'36"


37"


38"


39"


40"


41"



0 [h] 26 [m] 25.2 [s] 25.1 [s] 25.0 [s] 24.9 [s] 24.8 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


20


1500 1000 500 0 500 1000 1500

Velocity [km/s]



-34°17'37"


38"


39"


0 [h] 26 [m] 25.1025.05 [s] [s] 25.00 [s] 24.95 [s] 24.90 [s]


RA (ICRS)


-34°17'37"


38"


39"


0 [h] 26 [m] 25.1025.05 [s] [s] 25.00 [s] 24.95 [s] 24.90 [s]


RA (ICRS)



-34°17'37"


38"


39"



0 [h] 26 [m] 25.1025.05 [s] [s] 25.00 [s] 24.95 [s] 24.90 [s]


RA (ICRS)


-34°17'37"


38"


39"


0 [h] 26 [m] 25.1025.05 [s] [s] 25.00 [s] 24.95 [s] 24.90 [s]


RA (ICRS)



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-22 at _𝑧_ = 3 _._ 050



MNRAS **000**, 1–42 (2024)

34 _Bakx et al._


-32°32'43"


44"


45"


46"


47"


48"


23 [h] 58 [m] 27.7 [s] 27.6 [s] 27.5 [s] 27.4 [s] 27.3 [s]


RA (ICRS)


-32°32'43"


44"


45"


46"


47"


48"


23 [h] 58 [m] 27.7 [s] 27.6 [s] 27.5 [s] 27.4 [s] 27.3 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]





1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]















23 [h] 58 [m] 27.6 [s] 27.5 [s] 27.4 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]



-32°32'43"


23 [h] 58 [m] 27.7 [s] 27.6 [s] 27.5 [s] 27.4 [s] 27.3 [s]


RA (ICRS)


-32°32'44"


45"


46"


47"


23 [h] 58 [m] 27.6 [s] 27.5 [s] 27.4 [s]


RA (ICRS)


-32°32'44"


45"


46"


47"


23 [h] 58 [m] 27.6 [s] 27.5 [s] 27.4 [s]


RA (ICRS)



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-25 at _𝑧_ = 2 _._ 912









23 [h] 56 [m] 23.2023.15 [s] [s] 23.10 [s] 23.05 [s] 23.00 [s]


RA (ICRS)


-35°41'19.0"


19.5"


20.0"


20.5"


23 [h] 56 [m] 23.15 [s] 23.10 [s] 23.05 [s] 23.00 [s]


RA (ICRS)


-35°41'19.0"


19.5"


20.0"


20.5"


23 [h] 56 [m] 23.15 [s] 23.10 [s] 23.05 [s] 23.00 [s]


RA (ICRS)


MNRAS **000**, 1–42 (2024)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



23 [h] 56 [m] 23.15 [s] 23.10 [s] 23.05 [s] 23.00 [s]


RA (ICRS)


-35°41'19.0"


19.5"


20.0"


20.5"


23 [h] 56 [m] 23.15 [s] 23.10 [s] 23.05 [s] 23.00 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-36 at _𝑧_ = 3 _._ 095

_Efficient high-resolution line survey_ 35





-35°42'10"


11"


12"


0 [h] 01 [m] 24.9024.85 [s] [s] 24.80 [s] 24.75 [s] 24.70 [s]


RA (ICRS)


-35°42'10.5"


11.0"


11.5"


12.0"


0 [h] 01 [m] 24.85 [s] 24.80 [s] 24.75 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



-35°42'10"


11"


12"


0 [h] 01 [m] 24.9024.85 [s] [s] 24.80 [s] 24.75 [s] 24.70 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]





1500 1000 500 0 500 1000 1500

Velocity [km/s]









1500 1000 500 0 500 1000 1500

Velocity [km/s]





0 [h] 01 [m] 24.85 [s] 24.80 [s] 24.75 [s]


RA (ICRS)


0 [h] 01 [m] 24.85 [s] 24.80 [s] 24.75 [s]



-35°42'10.5"


11.0"


11.5"


12.0"


-35°42'10.5"


11.0"


11.5"


12.0"



0 [h] 01 [m] 24.9024.85 [s] [s] 24.80 [s] 24.75 [s] 24.70 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]



RA (ICRS)





-35°42'10.5"


11.0"


11.5"


12.0"


-35°42'10.5"


11.0"


11.5"


12.0"



0 [h] 01 [m] 24.85 [s] 24.80 [s] 24.75 [s]


RA (ICRS)


0 [h] 01 [m] 24.85 [s] 24.80 [s] 24.75 [s]


RA (ICRS)







1500 1000 500 0 500 1000 1500

Velocity [km/s]


**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-41A at _𝑧_ = 4 _._ 098



1500 1000 500 0 500 1000 1500

Velocity [km/s]



1500 1000 500 0 500 1000 1500

Velocity [km/s]



0 [h] 01 [m] 24.85 [s] 24.80 [s] 24.75 [s]


RA (ICRS)



MNRAS **000**, 1–42 (2024)

36 _Bakx et al._



0 [h] 00 [m] 07.50 [s] 07.45 [s] 07.40 [s]


RA (ICRS)


0 [h] 00 [m] 07.50 [s] 07.45 [s] 07.40 [s]


RA (ICRS)





-33°41'02.5"


03.0"


03.5"


04.0"


-33°41'02.5"


03.0"


03.5"


04.0"



0 [h] 00 [m] 07.50 [s] 07.45 [s] 07.40 [s]


RA (ICRS)


0 [h] 00 [m] 07.50 [s] 07.45 [s] 07.40 [s]


RA (ICRS)


0 [h] 00 [m] 07.50 [s] 07.45 [s] 07.40 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



-33°41'02.5"


03.0"


03.5"


04.0"


-33°41'02.5"


03.0"


03.5"


04.0"



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-42A at _𝑧_ = 3 _._ 307



1500 1000 500 0 500 1000 1500

|Col1|Observed frequency|Col3|
|---|---|---|
||35s<br>1500<br>1000<br>500<br>0<br>5<br>0<br>5<br>10<br>Flux Density [mJy]<br>240.5<br>241.0<br>241.5<br>Observed frequency|35s<br>1500<br>1000<br>500<br>0<br>5<br>0<br>5<br>10<br>Flux Density [mJy]<br>240.5<br>241.0<br>241.5<br>Observed frequency|
||35s<br>1500<br>1000<br>500<br>0<br>5<br>0<br>5<br>10<br>Flux Density [mJy]<br>240.5<br>241.0<br>241.5<br>Observed frequency||
|0m0750s<br>0745s<br>0740s<br>07|0m0750s<br>0745s<br>0740s<br>07|00<br>1000<br>500<br>0|



Velocity [km/s]





0 [h] 00 [m] 07.50 [s] 07.45 [s] 07.40 [s]


RA (ICRS)


0 [h] 20 [m] 54.30 [s] 54.25 [s] 54.20 [s] 54.15 [s] 54.10 [s]


RA (ICRS)


-31°27'57"



1500 1000 500 0 500 1000 1500

Velocity [km/s]



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



-33°40'55.0"


55.5"


56.0"


56.5"


RA (ICRS)



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-42B at _𝑧_ = 3 _._ 314





-31°27'57"


58"


28'00"


0 [h] 20 [m] 54.3054.25 [s] [s] 54.20 [s] 54.15 [s] 54.10 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]





28'00"


0 [h] 20 [m] 54.30 [s] 54.25 [s] 54.20 [s] 54.15 [s] 54.10 [s]


RA (ICRS)


MNRAS **000**, 1–42 (2024)



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-81A at _𝑧_ = 3 _._ 160

_Efficient high-resolution line survey_ 37



-31°27'50"


51"


52"


0 [h] 20 [m] 54.8554.80 [s] [s] 54.75 [s] 54.70 [s] 54.65 [s]


RA (ICRS)


-31°27'50"


51"


52"


0 [h] 20 [m] 54.85 [s] 54.80 [s] 54.75 [s] 54.70 [s] 54.65 [s]


RA (ICRS)


-33°11'11"


12"


13"


23 [h] 53 [m] 24.6524.60 [s] [s] 24.55 [s] 24.50 [s] 24.45 [s]


RA (ICRS)


-33°38'25"


26"


27"


28"


0 [h] 25 [m] 33.8 [s] 33.7 [s] 33.6 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]



0 [h] 25 [m] 33.8 [s] 33.7 [s] 33.6 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]





1500 1000 500 0 500 1000 1500

Velocity [km/s]



-31°27'50"


51"


52"


0 [h] 20 [m] 54.8554.80 [s] [s] 54.75 [s] 54.70 [s] 54.65 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-81B at _𝑧_ = 2 _._ 588


-33°11'11"





1500 1000 500 0 500 1000 1500

Velocity [km/s]



12"


13"



23 [h] 53 [m] 24.6524.60 [s] [s] 24.55 [s] 24.50 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-86 at _𝑧_ = 2 _._ 564



-33°38'25"


26"


27"


28"



1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-87 at _𝑧_ = 2 _._ 059



MNRAS **000**, 1–42 (2024)

38 _Bakx et al._


-35°29'29"


30"


31"


32"

23 [h] 47 [m] 50.6 [s] 50.5 [s] 50.4 [s] 50.3 [s]


RA (ICRS)





-35°29'29"


30"


31"



32"


23 [h] 47 [m] 50.6 [s] 50.5 [s] 50.4 [s] 50.3 [s]


RA (ICRS)





1500 1000 500 0 500 1000 1500

Velocity [km/s]



23 [h] 47 [m] 50.6 [s] 50.5 [s] 50.4 [s] 50.3 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]





23 [h] 47 [m] 50.6 [s] 50.5 [s] 50.4 [s] 50.3 [s]


RA (ICRS)







1500 1000 500 0 500 1000 1500

Velocity [km/s]







23 [h] 47 [m] 50.6 [s] 50.5 [s] 50.4 [s] 50.3 [s]


RA (ICRS)


-35°41'32"


33"


34"


0 [h] 18 [m] 38.9538.90 [s] [s] 38.85 [s] 38.80 [s] 38.75 [s]


RA (ICRS)



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-93 at _𝑧_ = 2 _._ 402











1500 1000 500 0 500 1000 1500

Velocity [km/s]



-35°41'32"


33"


34"



0 [h] 18 [m] 38.9538.90 [s] [s] 38.85 [s] 38.80 [s] 38.75 [s]


RA (ICRS)





1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-104 at _𝑧_ = 1 _._ 536





-31°35'04"


05"















06"


07"





0 [h] 18 [m] 02.6 [s] 02.5 [s] 02.4 [s]


RA (ICRS)


-31°35'04"


05"


06"


07"


0 [h] 18 [m] 02.6 [s] 02.5 [s] 02.4 [s]


RA (ICRS)


MNRAS **000**, 1–42 (2024)



1500 1000 500 0 500 1000 1500

Velocity [km/s]



0 [h] 18 [m] 02.6 [s] 02.5 [s] 02.4 [s]


RA (ICRS)





-31°35'04"


05"



1500 1000 500 0 500 1000 1500

Velocity [km/s]



06"


07"



0 [h] 18 [m] 02.6 [s] 02.5 [s] 02.4 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-106 at _𝑧_ = 2 _._ 369

-32°11'34.0"


34.5"



_Efficient high-resolution line survey_ 39



-32°11'33"


34"


35"


36"


37"


0 [h] 03 [m] 30.8 [s] 30.7 [s] 30.6 [s] 30.5 [s]


RA (ICRS)





-33°08'11"


12"


13"







35.0"


35.5"



1500 1000 500 0 500 1000 1500

Velocity [km/s]



36.0"



0 [h] 03 [m] 30.70 [s] 30.65 [s] 30.60 [s] 30.55 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]



**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-155 at _𝑧_ = 3 _._ 077









1500 1000 500 0 500 1000 1500

Velocity [km/s]



0 [h] 04 [m] 55.6 [s] 55.5 [s] 55.4 [s] 55.3 [s]


RA (ICRS)


-33°08'12"


13"


14"


0 [h] 04 [m] 55.5555.50 [s] [s] 55.45 [s] 55.40 [s] 55.35 [s]


RA (ICRS)

|Col1|Obs|
|---|---|
|-33°08'33"<br>34"<br>c (ICRS)|5<br>10<br> ity [mJy]<br>98.8<br>99.0<br>Ob|
|23h4<br>35"<br>36"<br>De|9m558s<br>557s<br>556s<br>1500<br>1000<br>500<br>5<br>0<br>Flux Dens|



RA (ICRS)


-33°08'34.0"


34.5"


35.0"


35.5"


23 [h] 49 [m] 55.70 [s] 55.65 [s] 55.60 [s]


RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]


|Col1|Observed frequen|
|---|---|
||0s<br>1500<br>1000<br>500<br>0<br>7.5<br>5.0<br>2.5<br>0.0<br>2.5<br>5.0<br>7.5<br>Flux Density [mJy]<br>281.5<br>282.0<br>282.5<br>283.0<br>Observed freque|
|23h49m5570s<br>5565s<br>55|23h49m5570s<br>5565s<br>55|



1500 1000 500 0 500 1000 1500

Velocity [km/s]



14"


0 [h] 04 [m] 55.6 [s] 55.5 [s] 55.4 [s] 55.3 [s]



RA (ICRS)





1500 1000 500 0 500 1000 1500

Velocity [km/s]


**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-170 at _𝑧_ = 4 _._ 182



Observed frequency

99.0 98.8 98.6 98.4 98.2







-33°08'34.0"


34.5"


35.0"



1500 1000 500 0 500 1000 1500

Velocity [km/s]



35.5"



RA (ICRS)



1500 1000 500 0 500 1000 1500

Velocity [km/s]





**Figure C1.** The moment-0 (left) and line spectra (right) of HerBS-184 at _𝑧_ = 2 _._ 507



MNRAS **000**, 1–42 (2024)

40 _Bakx et al._


**Table D1.** Infrared luminosities and dust masses for the ANGELS sources


Source _𝑧_ _𝑟_ _𝐵_ 7 _𝜇_ _𝜇𝐿_ IR [eye] _𝐿_ IR [eye] _𝜇𝐿_ IR [B][+][18] _𝐿_ IR [B][+][18] _𝑇_ d _𝜇𝐿_ IR [fit] _𝐿_ IR [fit] _𝜇𝑀_ _𝑑_ _𝑀_ _𝑑_

[0-1] [10 [12] _𝐿_ ⊙ ] [10 [12] _𝐿_ ⊙ ] [10 [12] _𝐿_ ⊙ ] [10 [12] _𝐿_ ⊙ ] [K] [10 [12] _𝐿_ ⊙ ] [10 [12] _𝐿_ ⊙ ] [10 [8] _𝑀_ ⊙ ] [10 [8] _𝑀_ ⊙ ]


21 3.323 1 9 51.7 5.7 56.3 6.2 34.1 46.3 5.1 109.4 12.1

22 3.050 1 18.8 45.5 2.4 50.5 2.6 32.6 39.2 2.0 121.7 6.4

25 2.912 1 9.2 34.8 3.7 38.7 4.2 30.6 28.7 3.1 130.9 14.2

36 3.095 1 4.1 40.3 9.8 44.7 10.9 33.4 35.5 8.6 95.4 23.2

41 4.098 1 2.6 42.5 16.3 45.6 17.5 35.9 40.3 15.5 70.3 27.0

42A 3.307 0.726 1 31.9 _31.9_ 35.4 _35.4_ 36.7 31.3 _31.3_ 47.7 _47.7_

42B 3.314 0.274 1 12.0 _12.0_ 13.4 _13.4_ 36.8 11.8 _11.8_ 17.9 _17.9_

81A 3.160 0.579 1 16.9 _16.9_ 18.6 _18.6_ 33.9 15.1 _15.1_ 40.8 _40.8_

81B 2.584 0.421 1 8.5 _8.5_ 9.6 _9.6_ 29.2 6.8 _6.8_ 37.2 _37.2_

86 2.564 1 1 17.8 _17.8_ 20.2 _20.2_ 28.1 13.7 _13.7_ 103.1 _103.1_

87 1.860 1 8.7 13.2 1.5 15.6 1.8 25.9 9.2 1.0 113.7 13.0

93 2.400 1 1 15.2 _15.2_ 17.5 _17.5_ 27.6 11.5 _11.5_ 97.5 _97.5_

104 1.540 1 6.3 10.7 1.7 12.6 2.0 24.6 6.6 1.0 113.1 17.9

106 2.369 1 2.3 20.9 9.0 24.2 10.5 31.7 17.9 7.8 66.2 28.7

155 3.077 0.860 28.3 20.2 0.7 22.2 0.8 30.6 16.6 0.6 75.1 2.6

159A 2.236 0.690 1 10.1 _10.1_ 11.8 _11.8_ 28.5 7.8 _7.8_ 54.6 _54.6_

159B 2.236 0.310 1 4.5 _4.5_ 5.3 _5.3_ 28.5 3.5 _3.5_ 24.5 24.5

170 4.184 1 1 38.1 _38.1_ 41.5 _41.5_ 38.2 37.2 _37.2_ 45.0 _45.0_

184 2.507 1 1 18.6 _18.6_ 21.5 _21.5_ 30.6 15.4 _15.4_ 69.9 _69.9_


**Notes:** Col. 1: Source name. Col. 2: Spectroscopic redshift Col. 3: Band 7 flux ratio between the component and other sources in the field. Col. 4: Magnifications
as derived in Section 4 Col. 5-6: Observed and magnification-corrected infrared luminosity derived from the Eyelash template (e.g. Ivison et al. 2016) using the
_𝑧_ spec fitted to the _Herschel_ fluxes. Col. 7-8: Observed and magnification-corrected infrared luminosity derived from the template in Bakx et al. (2018, 2020b)
using the _𝑧_ spec fitted to the _Herschel_ fluxes. Col. 9-13: Single-temperature modified black-body using the _𝑧_ spec fitted to the _Herschel_ fluxes, assuming _𝛽_ dust = 2 _._ 0,
providing the dust temperature, observed and magnification-corrected infrared luminosities and observed and magnification-corrected dust masses using the
methodology from Bakx et al. (2021). Italics indicate unchanged values in the case of an unlensed source.


**APPENDIX D:** **INFRARED LUMINOSITIES OF ANGELS SOURCES**


We provide the infrared luminosities for the ANGELS targets using three methodologies in Table D1: 1) using the Eyelash galaxy template
(e.g. Ivison et al. 2016), 2) using the _Herschel_ -derived template from Bakx et al. (2018, 2020b), and thirdly assuming a modified black-body
with a _𝛽_ dust = 2 _._ 0, based on the method outlined in Bakx et al. (2021). On average the luminosities of the first two methods are roughly 50 per
cent higher than for a single-temperature fit, as much of the shorter-wavelength emission is missed in a single-temperature fit, which reflects
mostly the colder dust (see e.g. Eales et al. 1999). Meanwhile, the latter option also provides us an estimate of the dust masses for these targets,
which are primarily at these colder dust temperatures.


**APPENDIX E:** **COMPARISON OF BEARS AND ANGELS FLUXES**


Figure E1 shows the velocity-integrated flux densties for the six galaxies with line measurements of the same CO transition in both BEARS and
ANGELS, and compare this against the resolved observations extracted using the same technique as the BEARS study (Urquhart et al. 2022),
where the aperture is increased in a curve-of-growth fashion until a signal-to-noise ratio of 5 is reached in the velocity-integrated flux density.
The line fluxes of the resolved ANGELS observations are often higher than those extracted from the moderately-resolved BEARS observations,
and could point to differences between the curve-of-growth approach from BEARS (Urquhart et al. 2022). Similarly, unresolved and resolved
studies (Jorsater & van Moorsel 1995; Czekala et al. 2021) have found different fluxes on the same object, such as the flux estimates from
ALMA large program ALPINE when compared to the resolved CRISTAL study (Posses et al. 2024), or the flux estimates reported in resolved
observations of bright AGNs (Novak et al. 2019). The origin of these issues is believed to arise from the deconvolution technique in TCLEAN
that produces a combined image of background noise (in units of Jy / dirty beam) and signal (assuming a Gaussian point-spread function
in units of Jy / clean beam). As a consequence, the fluxes from resolved maps might produce a different total flux estimate than those from
unresolved observations.


**APPENDIX F:** **RGB IMAGES FROM THE DUST CONTINUUM**


Figure F1 shows an RGB image using the Bands 6, 7 and 8 photometry of ANGELS across nineteen sources. These galaxies show a large
diversity.


MNRAS **000**, 1–42 (2024)

_Efficient high-resolution line survey_ 41









**Figure** **E1.** The velocity-integrated line fluxes of the BEARS (x-axis) and ANGELS (y-axis) flux extraction methods show discrepant flux densities across
the six CO lines that are observed in both the unresolved ( _blue_ _squares_ ) and resolved ( _red_ _triangles_ data. A comparison of the fields with only resolved data
( _grey circles_ ) also show a bias towards higher fluxes when the ANGELS method is used for flux extraction, suggesting the flux difference between BEARS and
ANGELS is both because of the use of resolved data (i.e., Jorsater & van Moorsel (1995); Czekala et al. (2021)) and because of a difference in methods of flux

extraction.


**Figure F1.** A composite rgb image across all nineteen fields with Bands 6 ( _red), 7 (green) and 8 (blue) photometry shows the spread in morphologies across the_

_ANGELS sources._


MNRAS **000**, 1–42 (2024)

42 _Bakx et al._


4


3


2



HerBS-21



HerBS-25

4


3


2


1

3 4 5 6


HerBS-42B

4


3


2


1

3 4 5 6


HerBS-87

4


3


2


1

3 4 5 6


HerBS-170

4


3


2


1

3 4 5 6



HerBS-36

4


3


2


1

3 4 5 6


HerBS-81A

4


3


2


1

3 4 5 6


HerBS-93

4


3


2


1

3 4 5 6


HerBS-184

4



1

3 4 5 6



1

3 4 5 6


HerBS-41A

4


3


2


1

3 4 5 6


HerBS-81B

4


3


2


1

3 4 5 6


HerBS-106

4


3


2


1

3 4 5 6



HerBS-22

4


3


2


1

3 4 5 6


HerBS-42A

4


3


2


1

3 4 5 6


HerBS-86

4


3


2


1

3 4 5 6


HerBS-155

4


3


2


1

3 4 5 6



3


2



ANGELS avg.

Indv. pixel

CO est.

CI est.


## log( H 2 [)] [[M] pc 2 ]

**Figure G1.** The pixel-per-pixel comparison of the Schmidt-Kennicutt relation for each source is shown for individual pixels ( _black points_ ) and as the most likely
value ( _blue pentagon_ ) and associated errors. We show the constant depletion timescales as diagonal lines for direct comparison to Figure 12. The _red upward_
_and downward triangles_ indicate the position of the source on the Schmidt-Kennicutt relation based on the unresolved observations in Hagimoto et al. (2023)
for CO and [C i]-derived dust masses, respectively.


**APPENDIX G:** **RESOLVED COMPARISON OF DUST TO GAS**


The data enables a spatially-resolved study of Schmidt-Kennicutt (see Figure 12). We derive this in a pixel-per-pixel comparison shown in
Appendix Figure G1 for each of the sources with observed spectral lines.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–42 (2024)

_Efficient high-resolution line survey_ 43



HerBS-21


2.75


2.50


2.25


4.25 4.50 4.75


HerBS-41


2.7


2.6


2.5

4.6 4.8 5.0


HerBS-81


2.2


2.0


1.8

3.50 3.75 4.00


HerBS-106


2.2


2.0


1.8

3.25 3.50 3.75



HerBS-22


2.5


2.4


2.3


2.2

4.75 5.00


HerBS-42


3.0


2.8


2.6


5.0 5.2


HerBS-86


2.4


2.3


2.2


3.6 3.8


HerBS-155


2.1


2.0


4.0 4.2 4.4



2.3

4.25 4.50 4.75


HerBS-87


2.3


2.2


3.8 4.0 4.2


HerBS-170


2.4


2.2


2.0


1.8

4.00 4.25 4.50



3.0


2.8


2.6


2.1


2.0



HerBS-36


4.6 4.8


~~Her~~ BS-81



2.5


2.0


2.6


2.5


2.4



HerBS-25


~~4.0~~ 4.5


HerBS-42



1.9

4.4 4.6


HerBS-93


2.3


2.2


2 ~~.1~~


4.2 4.4 4.6


HerBS-184


2.5


2.4


2.3


4.4 4.6 4.8


## log( H 2 [)] [[M] pc 2 ]

**Figure G2.** A zoomed-in version of Fig. G1 focusing on the pixel-per-pixel comparison of the Schmidt-Kennicutt relation _black points_ ) and its most likely value
( _blue_ _pentagon_ ). The constant depletion timescales are shown as diagonal lines for direct comparison to Figure 12. The variation of the gas depletion times
across the sources is spread roughly 0.2 to 0.5 dex. in both surface star-formation rate and gas density. The sharp cut-offs seen most clearly for HerBS-25 and
-106 originate from the


MNRAS **000**, 1–42 (2024)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].validation.evidence[0]",
  "value": "Compared extracted CO fluxes with BEARS curve-of-growth 5-sigma method on resolved and unresolved data (finding 4 +/- 8% systemic difference on resolved data).",
  "failed_quote": "The comparison between the 5𝜎 and the ANGELS methods on the complete resolved data finds only a 4 ± 8 per cent systemic difference between the two methods (with modestly-larger fluxes in the ANGELS methodology)"
 },
 {
  "path": "analysis_steps[2].method.evidence[2]",
  "value": "Two-phase visibility-plane (uv-plane) lens modelling of Band 7 data using PyAutoLens (SIE lens + external shear; Phase 1: Sersic source, Phase 2: pixelated Voronoi mesh with constant regularization). For unlensed sources, fit Sersic profile in image plane using CASA IMFIT.",
  "failed_quote": "The non-lensed sources are fitted using the casa task IMFIT, which assumes a Sersic index of 0.5 that appears to match the emission profiles well based on the residual images."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Fit Herschel photometry at fixed spectroscopic redshift using (1) Cosmic Eyelash template, (2) Bakx et al. (2018, 2020b) template, and (3) single-temperature modified black-body with beta_dust = 2.0; distribute multi-component luminosity by Band 7 flux ratios. For resolved luminosity, fit Band 7 flux with T_d = 35 K, beta_dust = 2 MBB.",
  "failed_quote": "Firstly, where it is necessary to discuss the resolved luminosity (e.g., in the resolved star-formation law; Section 6.1), we use a single-temperature modified black-body estimate of the far-infrared luminosity of these sources with 35 K and 𝛽_dust = 2 (Bendo et al. 2023) fit to the Band 7 flux densities of the sources."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "T_d = 35 K, beta_dust = 2.0 for resolved Band 7 MBB; beta_dust = 2.0 for Herschel MBB fit",
  "failed_quote": "we use a single-temperature modified black-body estimate of the far-infrared luminosity of these sources with 35 K and 𝛽_dust = 2 (Bendo et al. 2023) fit to the Band 7 flux densities of the sources."
 },
 {
  "path": "software[3].used_for.evidence[1]",
  "value": "Fitting Sersic profiles (n=0.5) to non-lensed sources to measure intrinsic radii",
  "failed_quote": "The non-lensed sources are fitted using the casa task IMFIT, which assumes a Sersic index of 0.5 that appears to match the emission profiles well based on the residual images."
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Strong lensing fraction in ANGELS sample = 56 per cent",
  "failed_quote": "The lensing fraction of 56 ± 13 per cent (assuming a binomial distribution; Gehrels 1986) is on the lower end of theoretical predictions (e.g., 70 per cent; Negrello et al. 2007)"
 }
]
```
