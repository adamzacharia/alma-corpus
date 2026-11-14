# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021MNRAS.506..514K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–8 (2021) Preprint 10 June 2021 Compiled using MNRAS L [A] TEX style file v3.0

## H 2 molecular gas absorption-selected systems trace CO molecular gas-rich **galaxy overdensities**


Anne Klitsch, [1] _[★]_ Céline Péroux, [2] _[,]_ [3] Martin A. Zwaan, [2] Annalisa De Cia, [4] Cédric Ledoux, [5]

Sebastian Lopez [6]

1 _DARK, Niels Bohr Institute, University of Copenhagen, Jagdtvej 128, 2200 Copenhagen, Denmark_
2 _European Southern Observatory, Karl-Schwarzschildstrasse 2, D-85748 Garching bei München, Germany_
3 _Aix Marseille Univ, CNRS, CNES, LAM, (Laboratoire d’Astrophysique de Marseille), UMR 7326, 13388, Marseille, France_
4 _Department of Astronomy, University of Geneva, Chemin Pegasi 51, 1290 Versoix, Switzerland_
5 _European Southern Observatory, Alonso de Córdova 3107, Casilla 19001, Vitacura, Santiago, Chile_
6 _Departamento de Astronomía, Universidad de Chile, Casilla 36-D, Santiago, Chile_


Accepted 2021 June 5. Received 2021 June 4; in original form 2021 January 20.


**ABSTRACT**

Absorption-selected galaxies offer an effective way to study low-mass galaxies at high redshift. However, the physical properties
of the underlying galaxy population remains uncertain. In particular, the multiphase circum-galactic medium is thought to
hold key information on gas flows into and out of galaxies that are vital for galaxy evolution models. Here we present ALMA
observations of CO molecular gas in host galaxies of H 2 -bearing absorbers. In our sample of six absorbers we detect molecular
gas-rich galaxies in five absorber fields although we did not target high-metallicity ( _>_ 50 per cent solar) systems for which
previous studies reported the highest detection rate. Surprisingly, we find that the majority of the absorbers are associated with
multiple galaxies rather than single haloes. Together with the large impact parameters these results suggest that the H 2 -bearing
gas seen in absorption is not part of an extended disk, but resides in dense gas pockets in the circum-galactic and intra-group

medium.


**Key words:** quasars: absorption lines – galaxies: ISM – galaxies: groups – ISM: molecules



**1** **INTRODUCTION**


Conventional surveys identify galaxies based on the continuum or
line emission and are therefore preferentially select the most luminous part of the galaxy populations. These are high stellar mass and
star-formation rate galaxies. An alternative galaxy selection technique is based on the absorption signature that the gas content
imprints in the spectra of otherwise unrelated background quasars
(damped Ly _𝛼_ absorbers with a column density of HI > 2×10 [20] cm [−][2]

Wolfe et al. 2005). The absorption traces the neutral HI gas in galaxies. Damped Ly _𝛼_ absorbers trace the majority of HI in the Universe,
as well as the majority of metals at high redshift (Péroux & Howk
2020). These absorption-selected galaxies include the selection of
lower-mass galaxies that lie at or below the main sequence for starforming galaxies at their respective redshifts (e.g. Kanekar et al.
2018; Rhodin et al. 2018).
Therefore, a good understanding of the underlying galaxy population traced by absorption-selection is required to draw firm conclusions on the evolution of the whole galaxy population. It has been
suggested that absorption-selected galaxies at intermediate redshift
( _𝑧_ ∼ 0 _._ 5) are extremely molecular gas-rich and have a low star formation efficiency compared to emission-selected galaxies at low ( _𝑧_ ∼ 0)
and high ( _𝑧_ ∼ 2) redshift (Kanekar et al. 2018; Kanekar et al. 2020).
The authors of these studies selected high metallicity absorbers and


_★_ E-mail: anne.klitsch@gmail.com


© 2021 The Authors



report CO detection rates of 40–70 per cent. In another sample of
six absorption-selected galaxies observed with MUSE and ALMA,
the MUSE-ALMA Halos survey, Szakacs et al. (2021) report a CO
detection rate of 1/3. However, in total only small samples of molecular gas mass measurements at low, intermediate and high redshifts
are available.


At the same time the advent of large field-of-view integral field
spectrographs in the optical such as the Multi Unit Spectroscopic
Explorer (MUSE) on the VLT and the Keck Cosmic Web Imager
(KCWI) on the Keck II telescope enabled efficient detection of absorber host galaxies with star-formation rate limits of ∼ 0 _._ 1M ⊙ yr [−][1] .
These surveys have revealed an increasing number of absorbers associated to groups of galaxies rather than individual systems (e.g.
Bielby et al. 2017; Péroux et al. 2017; Klitsch et al. 2018; Péroux
et al. 2019; Hamanowicz et al. 2020; Schroetter et al. 2021; Lofthouse et al. 2020). Recently, a group of nine galaxies associated with
an H 2 absorber within 600 proper kpc tracing a galaxy overdensity
was presented by Boettcher et al. (2020).


A growing sample of molecular gas observations in absorptionselected systems is now available (e.g. Neeleman et al. 2016; Neeleman et al. 2018; Møller et al. 2018; Klitsch et al. 2018, 2019; Kanekar
et al. 2018; Kanekar et al. 2020; Fynbo et al. 2018; Szakacs et al.
2021) Only in two absorption-selected systems more than one molecular gas-rich galaxy have been reported in emission (Klitsch et al.
2019; Péroux et al. 2019). However, a systematic study in CO emis

2 _A. Klitsch et al._


sion observed with ALMA similar to those for ionised gas carried
out in the optical with MUSE is still missing.
The goal of this study is tofollow-upLy _𝛼_ absorberswith previously
identified H 2 absorption identified from UV absorption lines. The
presence of H 2 -bearing gas in absorption potentially suggests a large
reservoir of molecular gas also observable in CO emission. We search
for molecular gas emission from the absorber host galaxy(s) and aim
to identify the origin of the absorbing gas.
This paper is organised as follows: In Section 2 we describe the
target selection, observations and data reduction, the detected galaxies and the relations between the absorbing gas and the host galaxies
are presented in Section 3 and in Section 4 we give a summary of
this work and list our conclusions.

Throughout the paper we adopt a ΛCDM cosmological model with
_𝐻_ 0 = 70 km s [−][1] Mpc [−][1], Ω m = 0 _._ 3, and Ω Λ = 0 _._ 7.


**2** **OBSERVATIONS AND DATA REDUCTION**


**2.1** **Target selection**


The absorbers were selected to have an H 2 molecular gas absorption
detection at UV wavelength. Additionally, we selected absorbers
observable with ALMA and at _𝑧_ ≲ 1 to limit the required observing
time. The neutral gas column densities of these absorbers are in
the range of log(N(HI)/cm [−][2] ) = 19 _._ 00 − 20 _._ 50 and the molecular
fractions cover a range of log _𝑓_ mol = −4 to −0 _._ 4. We find that
although it was not a selection parameter, some absorbers in our
sample have a high metallicity of above 30 per cent solar, but we
also include low metallicity systems with only ∼ 10 per cent of
solar metallicity. We note that some of these metallicity estimates do
not include ionisation corrections and could therefore be somewhat

higher. This distribution is expected for a sample of H 2 absorbers
(Bolmer et al. 2019). The absorber properties including optically
identified host galaxies are listed in Table 1.


**2.2** **ALMA observations**


The six target fields are listed in Table 1. We observe the lowest possible CO transition for each absorber where the specific transition
is determined by the absorber redshift ( _𝑧_ abs ). The lowest CO transition is observed to minimize uncertainties from the line luminosity
conversion, needed to evaluate the total molecular gas mass. The
observations are carried out under program 2018.1.01575.S (PI Klitsch). All observations use four ALMA 1.875 GHz bands, with one
band (in spectral-line mode of the correlator) covering the respective
expected redshifted CO line frequency, and the other three bands (in
continuum mode) placed at neighbouring frequencies to measure the
continuum emission. We start the data reduction with the pipeline
calibrated uv-data sets, as delivered by ALMA. Additional data reduction steps are carried out with the Common Astronomy Software
Applications (CASA) software package version 5.6 (McMullin et al.
2007). The imaging is done using the standard _tclean_ algorithm with
a final field of view of 1.5 times the primary beam size. This results
in an image diameter of 1 _._ 4 [′] in ALMA Band 3 and 1 _._ 2 [′] in ALMA
Band 4. A ‘natural’ weighting scheme is applied, which guarantees
optimal sensitivity appropriate for a line detection experiment. The
final beam sizes as well as the rms noise are listed in Table 2. We use
a channel width of 15 - 20 km s [−][1] .


MNRAS **000**, 1–8 (2021)



**2.3** **Archival MUSE observations**


One of the ALMA targets (HE 0515-4414) was observed with MUSE
under the project ID: 1100.A-0528 (PI: Fumagalli). The MUSE FoV
covers a 1 [′] × 1 [′] area, slightly narrower than that of our ALMA
observations. We have downloaded the pipeline-processed and flux
calibrated data cube from the ESO Phase 3 archive. We use this data

to search for optical counterparts for the CO detected galaxies.


**3** **RESULTS**


We search for CO line emission in the ALMA image cubes before
correcting for the primary beam response to ensure constant noise
properties across the field of view. We search for line emission both
by-eye and using the line finder software SoFiA and detect CO line
emission in four out of six absorber fields. We find in total nine

galaxies. Three out of four absorbers have more than one galaxy in
close proximity. In addition to the detections from this work we use
the results for Q2131-1207 presented by Szakacs et al. (2021). The
properties of our detections are listed in table 3.
The velocity profiles of the detected galaxies have a FWHM of
60—500 km s [−][1] . Previously reported CO detections of absorption
selected galaxies have a FWHM of _>_ 300 km s [−][1] (e.g. Kanekar et al.
2018; Kanekar et al. 2020; Klitsch et al. 2018, 2019; Møller et al.
2018; Péroux et al. 2019). While the narrow CO emission lines could
trace low mass galaxies we also note that the detection is only significant over few channels in the ALMA data. Therefore, we flag galaxies
with a FWHM _<_ 300 km s [−][1] as low significance detections unless
the detection is confirmed by independent observations. These are
still included in the further analysis to avoid a bias against low mass
galaxies. When studying trends and drawing general conclusions we
regard both, the high significance sample only and the full sample.


**3.1** **Notes on the individual quasar fields**


Emission line maps and extracted spectra of the detections are shown
in Fig. 1 and 2. The relation between the CO detection and the
absorber in velocity space is illustrated in Fig. 3. The CO spectra are
obtained from the primary beam corrected image cubes. Since many
sources are resolved we integrate the spectra over a region defined
by the 3 _𝜎_ contour in the integrated flux map. We do not detect
significant continuum emission from any galaxy detected in CO. A
detailed analysis of the different fields is presented in the following.


**B0120-28** **(** _𝑧_ abs = 0 _._ 18562 **)** We do not detect a host galaxy associated with the absorber in this field. Oliveira et al. (2014) report
an absorber host galaxy at an impact parameter of 70 kpc based
on imaging and spectroscopic data. However, the full details of this
galaxy remain unpublished. We have therefore calculated an upper
limit on the molecular gas mass based on the sensitivity limit of our
CO(1–0) emission line observations.


**J1342-0053** **(** _𝑧_ abs = 0 _._ 22711 **)** We report a detection of CO(1–0)
emission coincident with a previously optically identified absorber
host galaxy (Werk et al. 2013). The authors report a SFR of 6.04M⊙
yr [−][1], a stellar mass of 10 [10] _[.]_ [93] M⊙, a luminosity of 1.08 _𝐿_ _[★]_, and a
super solar metallicity of 12 + log(O/H) = 9.05.


**Q2131-1207 (** _𝑧_ abs = 0 _._ 4298 **)** We do not detect CO(2–1) emission in
the field of Q2131-1207 at the sensitivity limit of our observations.
This field has been observed with VLT/MUSE presented by Péroux

_CO molecular gas-rich galaxy overdensities_ 3


**Table 1.** Physical properties of quasar absorbers targeted in this sample.


Field Alternative _𝑧_ QSO _𝑧_ abs log(N(HI)/cm [−][2] ) log(N(H 2 )/cm [−][2] ) log _𝑍_ / _𝑍_ ⊙ Θ
Name [kpc]


QSO B0120-28 0.434 0.18561 20 _._ 50 ± 0 _._ 10 _[𝑑]_ 20 _._ 00 ± 0 _._ 10 _[𝑑]_ −1 _._ 19 ± 0 _._ 21 _[𝑑]_ 70 _[𝑑]_

J1342-0053 LBQS 1340–0038 0.326 0.22711 19 _._ 0 [+] − [0] 0 _[.]_ _._ [5] 8 _𝑒_ 14 _._ 63 ± 0 _._ 06 _[𝑎]_ −0 _._ 40 [+] − [0] 0 _[.]_ _._ [40] 10 _𝑘_ 35 _[𝑒]_

Q2131–1207 PKS 2128–123 0.500 0.4298 19 _._ 5 ± 0 _._ 15 _[𝑗]_ 16 _._ 36 ± 0 _._ 08 _[𝑗]_ _>_ −0 _._ 96 _[𝑏]_ 12, 48 _[𝑓]_

Q1241+176 QSO J1244+1721 1.273 0.55048 _>_ 19 _._ 00 _[𝑖]_ 15 _._ 81 ± 0 _._ 17 _[𝑎]_ _<_ 0 _._ 18 _[𝑎]_ 21 _[𝑔]_

Q0107-0232 LBQS 0107-0232 0.728 0.55733 19 _._ 50 ± 0 _._ 20 _[ℎ]_ 17 _._ 27 ± 0 _._ 30 _[ℎ]_ −0 _._ 72 ± 0 _._ 32 _[ℎ]_ 10, 11 _[ℎ]_

HE 0515-4414 QSO B0515-4414 1.713 1.15 19 _._ 88 ± 0 _._ 05 _[𝑐]_ 16 _._ 94 [+] − [0] 0 _[.]_ _._ [23] 41 _𝑐_ −0 _._ 38 ± 0 _._ 04 _[𝑙]_


**Notes:** Θ denotes the impact parameter between the quasar sight-line and a previously identified absorber host galaxy. **References:** _[𝑎]_ Average metallicities
([S/H] or [Si/H]) from Muzahid et al. (2015) without ionization correction, _[𝑏]_ Som et al. (2015), _[𝑐]_ Reimers et al. (2003), _[𝑑]_ Oliveira et al. (2014), _[𝑒]_ Werk et al.
(2013), _[𝑓]_ Péroux et al. (2017), _[𝑔]_ Steidel et al. (1994), _[ℎ]_ Crighton et al. (2013), _[𝑖]_ Rao et al. (2006), _[𝑗]_ Muzahid et al. (2016), _[𝑘]_ Werk et al. (2014), _[𝑙]_ Quast et al.
(2008)


**Figure 1.** CO emission line maps for all absorption-selected galaxies in this sample. The maps show a 6 × 6 [′′] wide field. Contours mark the 3, 5, 7, 10 sigma level
in the integrated intensity plot, negative contours are plotted as dashed lines, the white ellipse shows the ALMA synthesized beam, the spectrum is extracted
from the region where the integrated flux map is above 3 sigma. We also report the emission line and the confidence flag in the plot labels. The confidence flags
(H: high, L: low) are discussed in Section 3. We report nine CO detections of host galaxies in close proximity to four absorbers with three absorbers showing
significant galaxy overdensities.



et al. (2017). We carefully examine the positions of the galaxies
presented by the authors of this work, however, we also do not detect
any low confidence emission from these galaxies. Szakacs et al.
(2021) have followed-up this field in CO(3–2) to a higher SNR. They
report CO emission from one associated galaxy (SFR= 2 _._ 0 M ⊙ yr [−][1],
L= 0 _._ 6 L _★_ ). We calculate an upper limit of the CO(2-1) emission



at the position of this galaxy which is consistent with the detection
by Szakacs et al. (2021) (assuming a Milky Way type CO line ratio
_𝐿_ CO [′] (3−2) [/] _[𝐿]_ CO [′] (2−1) [=] _[ 𝑟]_ [32] [=][ 0] _[.]_ [54;] [Bolatto et al. 2013][). We include]
this field in the further analysis using the CO(3–2) detection.


MNRAS **000**, 1–8 (2021)

4 _A. Klitsch et al._


**Figure 2.** CO emission line spectra for all absorption-selected galaxies in this sample. The spectra are extracted from the region where the integrated intensity
maps in Fig. 1 are above 3 sigma, spectra are PB corrected and re-binned for display. The zero velocity is set to the systemic velocity of the galaxy with the
smallest impact parameter. We also report the emission line and the confidence flag in the plot labels. The confidence flags (H: high, L: low) are discussed in

Section 3.



**Table 2.** Details of the ALMA observations.


Field CO ALMA RMS beam beam

line Band [mJy/beam] [ [′′] × [′′] ] [kpc × kpc]


QSO J0120-28 1-0 3 0.62 1.0 x 0.8 3 x 3
Q1342-0053 1-0 3 0.33 0.9 x 0.8 3 x 3

PKS 2128-123 2-1 4 0.90 0.9 x 0.8 5 x 5

PG 1241+176 2-1 4 0.50 1.6 x 1.4 11 x 9

Q0107-0232 2-1 4 0.42 1.6 x 1.3 10 x 9

HE 05151-4414 3-2 4 0.34 1.5 x 1.2 12 x 10


**Q1241+176 (** _𝑧_ abs = 0 _._ 55048 **)** In this field, we detect three galaxies
at the absorber redshift. The galaxies lie at impact parameters of 60
– 120 kpc. In addition, Steidel et al. (1994) have identified a host
galaxy at an impact parameter of 21 _._ 2 ± 0 _._ 3kpc. However, the exact


MNRAS **000**, 1–8 (2021)



details of this detection are not reported. We carefully search for CO
emission at this impact parameter, but do not report a host galaxy.


**Q0107-0232 (** _𝑧_ abs = 0 _._ 55733 **)** Crighton et al. (2013) have identified
two galaxies within _<_ 2 [′′] of the quasar sight-line in K-band imaging.
If these galaxies were at the absorber redshift this would translate to
impact parameters of 10 kpc and 11 kpc. We do not find CO emission
from the position of these galaxies. However, we note that there is
no redshift information available for these galaxies and these could
be a chance alignment. We therefore exclude these galaxies as the
absorber hosts. Instead, we detect three galaxies at impact parameters
of 60 – 140 kpc. Given the narrow FWHM of these CO emission lines
we label those as low confidence detections. In the further analysis
these galaxies are excluded when drawing general conclusions.

_CO molecular gas-rich galaxy overdensities_ 5


**Table 3.** Molecular gas physical properties of galaxies associated with the absorbers.


Name Flag RA Dec Θ _𝑣_ 0 FWHM _𝑆_ int _𝑆_ peak _𝐿_ CO [′] [×][ 10] [9] M mol × 10 [9]

[kpc] [km s [−][1] ] [km s [−][1] ] [Jy km s [−][1] ] [Jy] [K km s [−][1] ] [M ⊙ ]


QSO J0120–28 - - - - - - _<_ 0.94 - _<_ 1.6 _<_ 6.8
QSO J1342–0053 G1 H 13h42m51.85s -00d53m54.2s 35 -9 165 ± 8 0.59 ± 0.06 4.0 ± 0.7 1.5 ± 0.1 6.5 ± 0.6
Q2131–1207 G1 2-1  -  -  - 52  -  - _<_ 1.57  - _<_ 3.8 _<_ 8.2
Q2131–1207 G1 3-2 _[𝑎]_ H 52 184 ± 50 0.355 5.29

PG 1241+176 G1 H 12h44m09.59s +17d20m58.1s 120 620 500 ± 10 1.49 ± 0.19 7.0 ± 1.8 5.9 ± 0.8 12.8 ± 1.6

PG 1241+176 G2 H 12h44m10.00s +17d20m58.1s 86 460 300 ± 10 0.64 ± 0.09 3.0 ± 0.8 2.5 ± 0.3 5.5 ± 0.7

PG 1241+176 G3 H 12h44m10.64s +17d20m55.6s 60 100 360 ± 10 0.41 ± 0.06 2.2 ± 0.6 1.6 ± 0.2 3.5 ± 0.5

LBQS 0107–0232 G1 L 01h10m14.22s -02d17m06.6s 63 -291 60 ± 10 0.13 ± 0.02 2.4 ± 0.6 0.5 ± 0.1 1.1 ± 0.2
LBQS 0107–0232 G2 L 01h10m15.56s -02d17m12.4s 144 449 240 ± 10 0.39 ± 0.07 4.7 ± 1.0 1.6 ± 0.3 3.4 ± 0.6
LBQS 0107–0232 G3 L 01h10m14.82s -02d17m06.6s 69 -651 140 ± 10 0.17 ± 0.03 1.7 ± 0.5 0.7 ± 0.1 1.5 ± 0.2

HE 05151–4414 G1 H 05h17m08.51s -44d10m51.4s 82 -188 600 ± 10 0.80 ± 0.06 2.6 ± 0.5 6.2 ± 0.5 7.2 ± 0.5

HE 05151–4414 G2 L 05h17m07.12s -44d11m01.5s 67 -213 105 ± 8 0.08 ± 0.01 0.8 ± 0.3 0.6 ± 0.1 0.7 ± 0.1


_Notes:_ The flag column shows the confidence (H: high, L: low) we assign to the detection. For more information see Section 3. _𝑇ℎ𝑒𝑡𝑎_ denotes the impact
parameter measured between the QSO sight line and the galaxy position. _𝑣_ 0 is the velocity difference between the H 2 velocity centroid and the CO emission of
the galaxy. The uncertainties in the molecular gas mass only include the flux measurement uncertainty, uncertainties in the conversion factors are discussed in
Section 3.2. Upper limits are calculated assuming a 5 _𝜎_ detection threshold and a linewidth of 300 km s [−][1] . For QSO J0120-28 we use the sensitivity in the center
of the image cube since no reliable counterpart has been reported. For Q2131-1207 we give the upper limit at the position of the optical counterpart reported by
Péroux et al. (2017) and Szakacs et al. (2021). _[𝑎]_ In addition, we list as Q2131-1207 G1 3-2 the CO(3-2) measurement reported by Szakacs et al. (2021).



**HE 0515–414 (** _𝑧_ abs = 1 _._ 15 **)** We have identified two galaxies at the
absorber redshift (one high and one low confidence) with impact
parameters of 67 and 85 kpc.
This field was also observed using WFC3/G141 HST GRISM
spectroscopy (PI: Bielby, ID: 14594). They have detected 9 galaxies
at _𝑧_ = 1 _._ 14 − 1 _._ 16 within a field-of-view of 6’ out of which one

is G1 that we detect in CO (Bielby private comm.). Other galaxies
identified in these data are outside the field-of-view of our ALMA

observations.

We have obtained additional archival MUSE observations de
scribed in Section 2.3. We search for counterparts of the CO detected galaxies. At the absorber redshift the [OII] line is covered by
the MUSE spectral range. We detect [OII] emission from G1, but not
from G2. The [OII] emission line profile and emission line map are
shown in Fig. A1. Following the description by Kennicutt (1998) we
measure a non dust-corrected SFR of 9.4 M ⊙ yr [−][1] which represents
a lower limit on the true SFR. This translates to an upper limit for the
molecular gas depletion time of 0.8 Gyr. This is in contrast to the long
gas depletion times for absorption selected galaxies at intermediate
redshifts reported by Kanekar et al. (2018); Péroux et al. (2019) and
Szakacs et al. (2021).
Additionally, we use the [OII] and CO observations of G1 to study
the ionised and molecular gas kinematics. The line of sight velocity
maps are shown in Fig. A2. The CO line emission is only marginally
resolved and the [OII] emission is not significant enough to allow
for a detailed analysis using state-of-the-art forward modelling techniques. However, a qualitative analysis shows that the molecular and
ionized gas kinematics are coupled. Both show rotation with similar
orientation and maximum velocity.


**3.2** **Molecular gas masses**


We convert the CO emission line luminosities in the observed tran
sitions to the CO(1-0) line luminosity using a Milky Way type line
ratio as reported by Carilli & Walter (2013). As we have no further
information on the CO line excitation this assumption yields an upper limit of the molecular gas mass. We stress that previous studies
of the CO spectral line energy distribution of absorption-selected



galaxies have in some cases shown more excited ISM conditions
than that of the Galaxy (Klitsch et al. 2019). The CO(1–0) line fluxes
could therefore be overestimated by a factor of 2 – 4. We have used
a CO-to-H 2 conversion factor of _𝛼_ CO = 4 _._ 36M⊙(K km s [−][1] pc [2] ) [−][1]

that is applicable for galaxies of solar metallicity that do not undergo
a starburst (including a factor of 1.36 to account for the presence
of helium Bolatto et al. 2013). We caution, however, that the true
molecular gas mass might be overestimated by up to a factor of six
compared to _𝛼_ CO = 0 _._ 8M⊙(K km s [−][1] pc [2] ) [−][1], appropriate for starburst environments. In case of a systematically too high conversion
factor chosen for all galaxies the relative trends remain the same. If,
however, only some galaxies in this sample have a Milky Way type
CO line ratio and _𝛼_ CO while for others a starburst type conversion is
more appropriate this could introduce also relative shifts.


**4** **DISCUSSION**


**4.1** **Detection rate**


In this study we have selected the targets based on previously identified H 2 -bearing gas detected in absorption instead of a metallicity
based selection that has sometimes been used in previous such surveys. We find that the absorbers cover a range of 1/10 [th] to solar
metallicity. We list the molecular gas column density as well as the
metallicity of the absorbers in Table 1. We find molecular gas-rich
galaxies in five out of six fields and we detect multiple galaxies in
three absorber fields. It is known from archival MUSE observations

that in a fourth field (Q2131-1207) an overdensity of four galaxies
is detected (Péroux et al. 2017). This success rate of _>_ 80 per cent
is remarkable for a study of molecular gas in absorption-selected
systems. Similar studies at intermediate and high redshift focussing
on high metallicity absorbers achieved a detection rate of ∼ 40 − 70
per cent with a clear relation to the absorber metallicity (Kanekar
et al. 2018; Kanekar et al. 2020; Szakacs et al. 2021). We attribute
the higher detection rate of CO emission to the presence of the H2bearing clouds in absorption that indicate the presence of particularly
molecular gas-rich systems.


MNRAS **000**, 1–8 (2021)

6 _A. Klitsch et al._


**Figure** **3.** Comparison between absorption profiles and the galaxy detections in CO. The absorption lines shown are QSO1342: Ly _𝛼_ (HST COS),
PG1241: Ly _𝛿_ (HST COS), LBQS0107: Ly _𝛿_ (HST COS), HE 0515: MgI
2852Å(UVES). The zero velocity refers to the systemic velocity of the host
galaxy with the smallest impact parameter. Blue points mark the velocity
offset of the CO detections, the errorbar width marks the FWHM, the vertical
position marks the impact parameter from the quasar (see right axis). Filled
and open symbols represent the high and low significance flags described
in Section 3. The grey vertical dashed line marks the centroid of the H 2
absorption. Different absorption components around the main Ly transition
are interlopers from the dense Ly _𝛼_ forest. The MgI absorption for HE0515
shows several velocity components spreading from −100 – 250 km s [−][1] that
all belong to the same absorber.


MNRAS **000**, 1–8 (2021)



**Figure** **4.** HI and H 2 absorber column density and molecular gas fraction
as a function of molecular gas mass of the host galaxies (top to bottom).
Larger markers indicate the galaxy with the smallest impact parameter. Filled
and open symbols represent the high and low significance flags described in
Section 3. Grey markers represent literature measurements from (Neeleman
et al. 2016; Szakacs et al. 2021). We report no clear trend of absorption
properties with the molecular gas mass of the host galaxies in both the full
and the high significance sample. This suggests that H 2 absorption is tracing
pockets of H 2 -bearing gas in the outskirts of the CGM rather than an extended

molecular disk.


**4.2** **Absorption associated to galaxy overdensities rather than**
**single galaxies**


A remarkable finding of this work is the detection of multiple galaxies
associated to one absorber in most fields (three out of four fields
presented here and in Q2131-1207 presented by Péroux et al. 2017;
Szakacs et al. 2021). For the field of HE0515-4414 we report an even
more extended structure of galaxies including 10 galaxies within
∼ 3 Mpc. A similar finding was reported by Hamanowicz et al.
(2020) who present a sample of absorption-selected galaxies with
follow-up VLT/MUSE IFU observations.
We test if the observed multiple galaxies are indeed overdensities
by calculating the expected number of galaxies within the co-moving
volume traced by our observations. We use the CO luminosity function reported by Fletcher et al. (2021) and integrate with a lower limit
of 10 [9] K km s [−][1] which is equivalent to the faintest detections in our
sample. We find that at both, the low and high redshift end of our
targets we expect fewer than one galaxy within the volume probed by
the ALMA Band 3 and 4 observations. Here we consider a velocity
range of ±1000 km s [−][1] from the absorber redshift. This suggests that

**Figure** **5.** H 2 column density as a function of impact parameter for the
detected galaxies in this work (blue, filled - high significance, open - low
significance) and galaxies presented in the literature (Neeleman et al. 2016;
Oliveira et al. 2014; Crighton et al. 2013; Szakacs et al. 2021). The lack of a
correlation between H 2 molecular gas column density and the impact parameter in both samples (full and high significance) suggests that the absorption
is not tracing extended molecular gas distributions.


the multiple galaxies detected in each field represent overdensities in
the galaxy distribution at the absorber redshift.


**4.3** **Molecular gas mass relation to absorber properties**


Although the sample size is limited and the connection between
absorber and host galaxies might be complex due to identification
of multiple host galaxies, we test if we can find a relation between
the molecular gas mass of the absorption-selected galaxies and the
absorber properties. In Fig. 4 we show the Hi column density, the H 2
column density and the molecular gas fraction as a function of the
molecular gas mass of the host galaxies. We do not report a significant
correlation in any of these parameter spaces for both, the full sample
and the high significance detections only. This is probably expected
as the connection between the absorber and the host galaxy in such
complex systems is not straightforward. A similar non-correlation
was identified in optical studies finding galaxy overdensities related
to absorbers in a similar redshift range (Hamanowicz et al. 2020).


**4.4** **Do molecular gas absorbers probe disks of galaxies or**
**pockets of dense gas in the CGM?**


To test whether the H 2 -bearing gas traces disks of galaxies or pockets
of dense gas in the circum-galactic medium (CGM) we analyse the
distance between the absorber and the host galaxies in both projected
distance on sky (impact parameter) and distance in velocity space to
probe the full extent of the three dimensional structure. In Fig. 3 we
show the absorption profiles in relation with emission line width of
the CO detected galaxies in terms of both sky position (right y-axis)
and velocity space (x-axis). The lack of comparison spectra of strong
metal absorption lines often hampers a direct comparison. For some
sight lines the only available lines are embedded in the Ly _𝛼_ forest
making a comparison between the absorption components and CO
emission lines challenging.
We find large impact parameters of 35 – 140 kpc suggesting that
the molecular absorption does not probe the extended molecular disk
of a single galaxy. In addition, we find a good agreement between



_CO molecular gas-rich galaxy overdensities_ 7


the absorption and CO emission in velocity space. This suggests an
association between the neutral and H 2 -bearing gas at the position
of the quasar sight line and the molecular gas in the host galaxies.
Additionally, we test for a relation between the H 2 column density
and the impact parameter (see Fig. 5), that would be expected if
the absorption is tracing the disk of the host galaxy. We do not
identify a clear trend between these two quantities adding further
evidence that the absorption is tracing pockets of H 2 -bearing gas
rather then the disk of a molecular gas-rich galaxy. Comparing the
detection rates of our work with previous studies focussing on high
metallicity we find that first with a success rate of _>_ 80 per cent our
detection rate is significantly higher and second we find overdensities
of galaxies rather then single galaxies. This suggests that there is
possibly more diffuse gas around overdensities of galaxies which
provides the appropriate conditions for molecular gas to form in-situ
or survive the outflow from a galaxy traced in absorption.
Galaxy interactions are numerous in overdense environments. Interactions can produce tidal streams as well as promote starburst
or AGN driven outflows. The H 2 molecular gas could therefore be
part of self-shielded, tidally stripped or ejected disk material. This
scenario is supported by the observations of molecular gas in high
velocity clouds in the Milky Way (Richter et al. 2001; Putman et al.
2012). Furthermore, the molecular gas could be transported out to
large distances by outflows (Richings & Faucher-Giguere 2018).
We note that we cannot exclude the presence of low molecular gas
mass galaxies below our detection limit at small impact parameters.
Ideal follow-up observations to settle this question would be optical
IFU observations to detect all galaxies in these fields down to low
star formation rates.


**5** **CONCLUSIONS**


In this paper we present a systematic search for molecular gas traced
by CO emission in H 2 absorption selected systems. We report the detection of CO emission from galaxies in close proximity to absorbers
in five out of six quasar fields (including the deeper observations
presented by Szakacs et al. 2021). Our main conclusions can be
summarised as follows:


 - Our detection rate of _>_ 80 per cent is higher than that reported in
previous studies (Kanekar et al. 2018; Kanekar et al. 2020) suggesting that the H 2 -bearing gas absorbers trace CO molecular gas-rich
galaxies.

 - Interestingly, the only system without a CO detection has the
lowest metallicity. However, the CO detected galaxies are related to
absorbers with a wide range of absorption metallicities.

 - The H 2 -bearing gas in absorption in all except two sight-lines
traces galaxy overdensities. In the case of HE0515-4414 this is also
supported by GRISM spectroscopy tracing scales of 3 Mpc. In the
case of Q2131-1207 only one galaxy is detected in CO, but additional
MUSE observations reveal three additional [OIII] emitting galaxies
connected to the absorber. This adds further evidence that absorption
selection is efficient at tracing overdense environments.

 - In the case of HE0515-4414 G1, we gather first insights in the
molecular and ionised gas kinematics traced by ALMA and MUSE
observations, respectively. We find that both velocity fields qualitatively agree in orientation and maximum velocity. Deeper high resolution observations are necessary for a complete morpho-kinematic
modelling.

 - We detect galaxies at impact parameters of 35 – 144 kpc. We
conclude that the H 2 -bearing absorbers do not trace the inner disk of
a galaxy, but pockets of diffuse molecular gas in the circum-galactic


MNRAS **000**, 1–8 (2021)

8 _A. Klitsch et al._


and intra-group medium. This is also supported by the lack of a clear
correlation between the absorber column density or molecular gas
fraction with impact parameter or host galaxy molecular gas mass.


**ACKNOWLEDGEMENTS**


The authors thank Palle Møller for important discussions related
to this work and Roland Szakacs for sharing preliminary results.
A.K. thanks Aleksandra Hamanowicz for important discussions related to this work. A.K. gratefully acknowledges support from the
Independent Research Fund Denmark via grant number DFF 802100130. A.D.C. acknowledges support by the Swiss National Science
Foundation under grant 185692. S.L. was funded by FONDECYT
grant number 1191232. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2018.1.01575.S. ALMA is a partnership of
ESO (representing its member states), NSF (USA) and NINS (Japan),
together with NRC (Canada), MOST and ASIAA (Taiwan), and
KASI (Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ. In addition, publications from NA authors must include the
standard NRAO acknowledgement: The National Radio Astronomy
Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.
This research made use of Astropy [1] a community-developed core
Python package for Astronomy(Astropy Collaboration et al. 2013;
Price-Whelan et al. 2018). This research has made use of NASA’s
Astrophysics Data System.


**DATA AVAILABILITY**


The data underlying this article are available in the respective observatories online archives. Used ALMA data is available through
the ALMA Science Archive ( `[https://almascience.eso.org/](https://almascience.eso.org/asax/)`
`[asax/](https://almascience.eso.org/asax/)` ), VLT/MUSE data is available through the ESO SciencenArchive Facility ( `[http://archive.eso.org/cms.html](http://archive.eso.org/cms.html)` ) and HST
data through the Hubble Legacy Archive ( `[https://hla.stsci.](https://hla.stsci.edu)`
`[edu](https://hla.stsci.edu)` ). Project IDs are given in Section 2 and 3.


**REFERENCES**


[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
Bielby R., Crighton N. H. M., Fumagalli M., Morris S. L., Stott J. P., Tejos
[N., Cantalupo S., 2017, MNRAS, 468, 1373](http://dx.doi.org/10.1093/mnras/stx528)
Boettcher E., et al., 2020, arXiv:2010.11958 [astro-ph]
[Bolatto A. D., Wolfire M., Leroy A. K., 2013, ARA&A, 51, 207](http://dx.doi.org/10.1146/annurev-astro-082812-140944)
[Bolmer J., et al., 2019, A&A, 623, A43](http://dx.doi.org/10.1051/0004-6361/201834422)

[Carilli C., Walter F., 2013, ARA&A, 51, 105](http://dx.doi.org/10.1146/annurev-astro-082812-140953)
[Crighton N. H. M., et al., 2013, MNRAS, 433, 178](http://dx.doi.org/10.1093/mnras/stt714)
Fletcher T. J., Saintonge A., Soares P. S., Pontzen A., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa3025) [501,](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501..411F)

[411](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501..411F)

[Fynbo J. P. U., et al., 2018, MNRAS, 479, 2126](http://dx.doi.org/10.1093/mnras/sty1520)
[Hamanowicz A., et al., 2020, MNRAS, 492, 2347](http://dx.doi.org/10.1093/mnras/stz3590)
[Kanekar N., et al., 2018, ApJL, 856, L23](http://dx.doi.org/10.3847/2041-8213/aab6ab)
Kanekar N., Prochaska J. X., Neeleman M., Christensen L., Møller P., Zwaan
[M. A., Fynbo J. P. U., Dessauges-Zavadsky M., 2020, ApJ, 901, L5](http://dx.doi.org/10.3847/2041-8213/abb4e1)
[Kennicutt Jr. R. C., 1998, ApJ, 498, 541](http://dx.doi.org/10.1086/305588)
Klitsch A., Péroux C., Zwaan M. A., Smail I., Oteo I., Biggs A. D., Popping
[G., Swinbank A. M., 2018, MNRAS, 475, 492](http://dx.doi.org/10.1093/mnras/stx3184)

[Klitsch A., et al., 2019, MNRAS, 482, L65](http://dx.doi.org/10.1093/mnrasl/sly187)


1 `[http://www.astropy.org](http://www.astropy.org)`


MNRAS **000**, 1–8 (2021)



[Lofthouse E. K., et al., 2020, MNRAS, 491, 2057](http://dx.doi.org/10.1093/mnras/stz3066)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127
[Møller P., et al., 2018, MNRAS, 474, 4039](http://dx.doi.org/10.1093/mnras/stx2845)

[Muzahid S., Srianand R., Charlton J., 2015, MNRAS, 448, 2840](http://dx.doi.org/10.1093/mnras/stv133)
[Muzahid S., Kacprzak G. G., Charlton J. C., Churchill C. W., 2016, ApJ, 823,](http://dx.doi.org/10.3847/0004-637X/823/1/66)

[66](https://ui.adsabs.harvard.edu/abs/2016ApJ...823...66M)

[Neeleman M., et al., 2016, ApJL, 820, L39](http://dx.doi.org/10.3847/2041-8205/820/2/L39)
Neeleman M., Kanekar N., Prochaska J. X., Christensen L., DessaugesZavadsky M., Fynbo J. P. U., Møller P., Zwaan M. A., 2018, [ApJ,](http://dx.doi.org/10.3847/2041-8213/aab5b1) [856,](https://ui.adsabs.harvard.edu/abs/2018ApJ...856L..12N)

[L12](https://ui.adsabs.harvard.edu/abs/2018ApJ...856L..12N)

Oliveira C. M., Sembach K. R., Tumlinson J., O’Meara J., Thom C., 2014,

[ApJ, 783, 22](http://dx.doi.org/10.1088/0004-637X/783/1/22)
[Péroux C., Howk J. C., 2020, ARA&A, 58, 363](http://dx.doi.org/10.1146/annurev-astro-021820-120014)

[Péroux C., et al., 2017, MNRAS, 464, 2053](http://dx.doi.org/10.1093/mnras/stw2444)

[Péroux C., et al., 2019, MNRAS, 485, 1595](http://dx.doi.org/10.1093/mnras/stz202)

[Price-Whelan A. M., et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
[Putman M. E., Peek J. E. G., Joung M. R., 2012, ARA&A, 50, 491](http://dx.doi.org/10.1146/annurev-astro-081811-125612)
[Quast R., Reimers D., Baade R., 2008, A&A, 477, 443](http://dx.doi.org/10.1051/0004-6361:20054773)
[Rao S. M., Turnshek D. A., Nestor D. B., 2006, ApJ, 636, 610](http://dx.doi.org/10.1086/498132)
[Reimers D., Baade R., Quast R., Levshakov S. A., 2003, A&A, 410, 785](http://dx.doi.org/10.1051/0004-6361:20031313)
Rhodin N. H. P., Christensen L., Møller P., Zafar T., Fynbo J. P. U., 2018,

[A&A, 618, A129](http://dx.doi.org/10.1051/0004-6361/201832992)
[Richings A. J., Faucher-Giguere C.-A., 2018, MNRAS, 474, 3673](http://dx.doi.org/10.1093/mnras/stx3014)
[Richter P., Sembach K. R., Wakker B. P., Savage B. D., 2001, ApJ, 562, L181](http://dx.doi.org/10.1086/338050)
[Schroetter I., et al., 2021, MNRAS,](http://dx.doi.org/10.1093/mnras/stab1447)
Som D., Kulkarni V. P., Meiring J., York D. G., Péroux C., Lauroesch J. T.,
[Aller M. C., Khare P., 2015, ApJ, 806, 25](http://dx.doi.org/10.1088/0004-637X/806/1/25)
[Steidel C. C., Dickinson M., Persson S. E., 1994, ApJ, 437, L75](http://dx.doi.org/10.1086/187686)
[Szakacs R., et al., 2021, arXiv e-prints, p. arXiv:2105.07280](https://ui.adsabs.harvard.edu/abs/2021arXiv210507280S)
Werk J. K., Prochaska J. X., Thom C., Tumlinson J., Tripp T. M., O’Meara
[J. M., Peeples M. S., 2013, ApJS, 204, 17](http://dx.doi.org/10.1088/0067-0049/204/2/17)
[Werk J. K., et al., 2014, ApJ, 792, 8](http://dx.doi.org/10.1088/0004-637X/792/1/8)
[Wolfe A. M., Gawiser E., Prochaska J. X., 2005, ARA&A, 43, 861](http://dx.doi.org/10.1146/annurev.astro.42.053102.133950)


**APPENDIX A:** **LINE OF SIGHT VELOCITY MAPS OF THE**

**IONISED AND MOLECULAR GAS IN HE0515-4414 G1**


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.

_CO molecular gas-rich galaxy overdensities_ 9


**Figure A1.** Ionized gas observations of HE 0515-4414 Galaxy 1 ( _𝑧_ = 1 _._ 15) traced by [OII] emission observed using MUSE. _Left:_ spectrum of the [OII] emission
line, where the zero velocity marks the position of the absorber. _Right:_ integrated intensity map of the [OII] emission line integrated over the yellow region
marked in the spectrum.


**Figure A2.** Line of sight velocity map of the molecular gas traced by CO(3–2) observed using ALMA ( _left_ ) and the ionized gas traced by [OII] observed using
MUSE ( _right_ ) in HE 0515-4414 Galaxy 1.


MNRAS **000**, 1–8 (2021)


</paper>

## Items to check

```json
[
 {
  "path": "claims[1].evidence[1]",
  "value": "H2 absorption-selected systems predominantly trace galaxy overdensities rather than single galaxies.",
  "failed_quote": "This suggests that the multiple galaxies detected in each field represent overdensities in the galaxy distribution at the absorber redshift."
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "H2-bearing absorbers do not probe the inner or extended disk of a single galaxy, but rather dense gas pockets in the circum-galactic and intra-group medium.",
  "failed_quote": "We detect galaxies at impact parameters of 35 – 144 kpc. We conclude that the H 2 -bearing absorbers do not trace the inner disk of a galaxy, but pockets of diffuse molecular gas in the circum-galactic and intra-group medium."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Publicly available in the ALMA Science Archive (2018.1.01575.S), ESO Science Archive Facility (1100.A-0528), and Hubble Legacy Archive (14594).",
  "failed_quote": "Used ALMA data is available through the ALMA Science Archive ( https://almascience.eso.org/ asax/ ), VLT/MUSE data is available through the ESO SciencenArchive Facility ( http://archive.eso.org/cms.html ) and HST data through the Hubble Legacy Archive ( https://hla.stsci. edu )."
 }
]
```
