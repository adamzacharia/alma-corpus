# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...923..251H\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version November 2, 2021
Typeset using L [A] TEX twocolumn style in AASTeX62


Second Epoch ALMA Observations of 321 GHz Water Maser Emission in NGC 4945 and the Circinus Galaxy


Yoshiaki [Hagiwara,](http://orcid.org/0000-0002-9043-6048) [1] Shinji [Horiuchi,](http://orcid.org/0000-0002-8395-3557) [2] [Masatoshi](http://orcid.org/0000-0001-6186-8792) Imanishi, [3, 4] and Philip G. Edwards [5]


1 Natural Science Laboratory, Toyo University, 5-28-20, Hakusan, Bunkyo-ku, Tokyo 112-8606, Japan
2 CSIRO Space and Astronomy, Canberra Deep Space Communications Complex

PO Box 1035, Tuggeranong, ACT 2901, Australia
3 National Astronomical Observatory of Japan, National Institutes of Natural Sciences (NINS)

2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan
4 Department of Astronomy, School of Science, The Graduate University for Advanced Studies, SOKENDAI

2-21-1 Osawa, Mitaka, Tokyo 181-8588 Japan
5 CSIRO Space and Astronomy,

PO Box 76, Epping NSW 1710, Australia


(Accepted October, 18 2021)


ABSTRACT


We present the results of second epoch ALMA observations of 321 GHz H 2 O emission toward two
nearby active galactic nuclei, NGC 4945 and the Circinus galaxy, together with Tidbinbilla 70-m monitoring of their 22 GHz H 2 O masers. The two epoch ALMA observations show that the strengths of
the 321 GHz emission are variable by a factor of at least a few, confirming a maser origin. In the
second epoch, 321 GHz maser emission from NGC 4945 was not detected, while for the Circinus galaxy
the flux density significantly increased and the velocity gradient and dispersion have been measured.
With the velocity gradient spanning ∼110 km s [−][1], we calculate the disk radius to be ∼28 pc, assuming
disk rotation around the nucleus. We also estimate the dynamical mass within the central 28 pc to be
4.3 × 10 [8] M ⊙, which is significantly larger than the larger scale dynamical mass, suggesting the velocity
gradient does not trace circular motions on that scale. The overall direction of the velocity gradient
and velocity range of the blueshifted features are largely consistent with those of the 22 GHz maser
emission in a thin disk with smaller radii of 0.1–0.4 pc and molecular outflows within ∼1 pc from the
central engine of the galaxy, implying that the 321 GHz masers could trace part of the circumnuclear
disk or the nuclear outflows.


Keywords: galaxies: active — galaxies: individual (NGC 4945) — galaxies: individual (Circinus
galaxy) — galaxies: nuclei — masers — submillimeter: galaxies



1. INTRODUCTION


Luminous H 2 O masers in the 6 16 –5 23 transition (rest
frequency, ν rest = 22.23508GHz) have been detected in
more than 180 galaxies [1], with most of them are detected
toward obscured active galactic nuclei (AGNs) hosting a
Seyfert or LINER nucleus (e.g., Braatz et al. 1994, 1996;
Braatz & Gugliucci 2008; Hagiwara et al. 2002, 2003,
2018; Greenhill et al. 2003a, 2009; Henkel et al. 2005;
Kondratko et al. 2006; Zhang et al. 2006; Tarchi et al.


Corresponding author: Yoshiaki Hagiwara
[yhagiwara@toyo.jp](mailto: yhagiwara@toyo.jp)


1 https://safe.nrao.edu/wiki/bin/view/Main/
MegamaserCosmologyProjects



2011). These are known as H 2 O megamasers. A fraction of the megamasers are classified as “nuclear masers”
as they are associated with AGN-activity in their host
galaxy. These exhibit spectra indicating evidence for
emission from sub-parsec–scale edge-on rotating discs
surrounding a super massive black hole (SMBH) (e.g.,
Miyoshi et al. 1995), as revealed by Very Long Baseline Interferometry (VLBI) observations at milliarcsecond (mas) angular resolution.
H 2 O maser emission occurs at (sub-)millimeter wavelengths in external galaxies: the pioneering observational study of extragalactic (sub-)millimeter masers
was the discovery of H 2 O maser in the 3 13 − 2 20 transition (ν rest = 183.31009GHz) toward the LINER galaxy
NGC 3079 (Humphreys et al. 2005), which was later fol

2 Hagiwara, Horiuchi, Imanishi, & Edwards



lowed by the detection of a 183 GHz maser in the nearby
AGN NGC 4945 (Humphreys et al. 2016).

Hagiwara et al. (2013) conducted a search for H 2 O masers
in the 10 29 −9 36 transition (ν rest = 321.226GHz) toward
H 2 O megamaser galaxies, which resulted in the first
extragalactic detection of a 321 GHz H 2 O maser toward
the center of the Circinus galaxy, obtained with the Atacama Large Millimeter/submillimeter Array (ALMA).
The detection of 321 GHz H 2 O maser emission toward
the center of NGC 4945 from this search was reported
later (Hagiwara et al. 2016; Pesce et al. 2016).
NGC 4945 is an edge-on type 2 Seyfert galaxy hosting a Compton-thick nucleus, which is heavily obscured by foreground material (e.g., Iwasawa et al. 1993;
Puccetti et al. 2014). The presence of a bright transient
X-ray source was reported on the south-west arm of the
galaxy (Isobe et al. 2008).
The Circinus galaxy is one of the closest Comptonthick AGN with a highly obscured type 2 Seyfert nucleus
(e.g., Ar´evalo et al. 2014; Yang et al. 2009), exhibiting
a kiloparsec-scale one-sided ionization cone at a position
angle of 245 [◦] (Marconi et al. 1994), which approximately
agrees with that of a nuclear outflow that is optically
identified on kiloparsec scales. Recent ALMA observations of thermalized CO (J=3–2) molecular line emission
at ∼0.3 [′′] angular resolution have traced the circumnuclear disk (∼70 × 30 pc) and spiral arms within ∼200 pc
of the nucleus (Izumi et al. 2018).
Prominent 22 GHz H 2 O masers in the center of the
galaxies (Dos Santos & L´epine 1979; Whiteoak et al.
1986; Greenhill et al. 1997b) were studied at milliarcsec
(mas) spatial resolution using VLBI. In the Circinus
galaxy, these observations revealed the presence of an
edge-on disk-like linear structure surrounding what is a
most likely a SMBH. It is claimed that some fraction of
the maser emission in the Circinus galaxy traces molecular outflows emanating within ∼1 pc from the nucleus
of the galaxy (Greenhill et al. 2003b). In NGC 4945, an
edge-on linear structure extending over 0.7 pc at a position angle of 45 [◦], closer to that of the galactic disk of
the galaxy, was revealed (Greenhill et al. 1997b, 2003b).
Currently, the only other extragalactic sub-millimeter
H 2 O line emission detected is the 5 15 −4 22 transition
(ν rest = 325.15292GHz) toward the ultraluminous infrared galaxy (ULIRG), Arp 220 (Cernicharo et al. 2006;
Galametz et al. 2016; K¨onig et al. 2017), although thermalized molecular gas emission is favoured as the origin
due to lack of intensity variability and the broad linewidth of the emission. Very recently, luminous 183 GHz
H 2 O maser emission (L H 2 O ∼ 10 [4] L ⊙ ) has been detected
toward the ULIRG, IRAS 19254−7245 (the “Superantennae galaxy”) at z=0.0617 (Imanishi et al. 2021), pro


viding the possibility of studying dense molecular gas
around a SMBH beyond the local universe.
Similar to the 22 GHz nuclear megamasers, submillimeter H 2 O masers can probe the nuclear kinematics
of AGN or dense molecular gas structures such as a rotating disk surrounding a SMBH, which provides new
insights into the nuclear region of nearby AGN.
In this paper, we present new results from second
epoch observations of the 321 GHz H 2 O masers in
NGC 4945 and the Circinus galaxy, conducted with
ALMA at higher angular resolution. The optical velocity definition is adopted throughout, and the velocities
are calculated with respect to the Local Standard of
Rest (LSR).


2. OBSERVATIONS AND DATA REDUCTION


2.1. ALMA Cycle 4 observations


We conducted Cycle 4 ALMA observations of H 2 O masers
in the 10 29 − 9 36 transition (ν rest = 321.226GHz) towards NGC 4945 and the Circinus galaxy for project
2016.1.00150.S (PI: Y. Hagiwara) in November 2016
and May 2017. These band 7 spectral-line observations
lasted for about 30–35 minutes (approximately 8–10
minutes on-source), with 45–47 antennas, depending on
the target source. The observations were made with a
single spectral window (1875 MHz bandwidth) and one
polarization, divided into 7680 spectral channels, yielding spectral resolutions of 244.1 kHz or 0.228 km s [−][1] at
each observed frequency and a total velocity coverage of
∼1750 km s [−][1] in order to cover Doppler-shifted emission
within ±900 km s [−][1] of the galaxy’s systemic velocity.
The spectral windows were centered near the systemic
velocity. After the channel smoothing to 3840 spectral points, the resulting spectral resolution is 488.3 kHz
or 0.458 km s [−][1] at the observed center frequency to
match that of the 22 GHz H 2 O maser observations at
Tidbinbilla (see Section 2.2). The observations were
made at ∼0.3 [′′] angular resolution. A summary of the

observations is listed in Table 1.

Data calibration was performed using the Common
Astronomy Software Applications (CASA) [2] (McMullin et al.
2007). Flux density and bandpass calibration were
performed using J1427−4206 and phase calibration
was made using J1326−5256 for the observations of
NGC 4945. The flux density, bandpass, and phase calibrators were J1617−5848, J1427−4206, and J1424−6807,
respectively, for the Circinus galaxy. We adopted a flux
density error of 10 percent, as stated in the capabilities
of Cycle 4 Band 7 observations.


2 [https://casa.nrao.edu](https://casa.nrao.edu)

321 GHz H 2 O masers in NGC 4945 and Circinus galaxy 3



Imaging of the calibrated data was carried out with
CASA and the NRAO Astronomical Image Processing Software (AIPS)(van Moorsel, Kemball, & Greisen
1996). After phase and amplitude calibrations, the
321 GHz continuum emission of NGC4945 and the Circi- [˙]

nus galaxy was subtracted from the spectral line visibilities using line-free channels prior to CLEAN deconvolution of line emission. The line emission from each

galaxy was separated out from the continuum emission.
Imaging was performed using CASA with Briggs weighting (robust = 0.5). The synthesized beam sizes and the
beam position angles used in the CLEAN process and
the resultant rms noise levels in the spectral line images
are listed in Table 1.


2.2. Tidbinbilla Observations


H 2 O maser spectra of the galaxies in the 6 16 − 5 23
transition (ν rest =22.23508GHz) were obtained using
NASA Deep Space Network 70-m antenna at Tidbinbilla, DSS-43. Observations of the masers from June
2012 to April 2014 were conducted using a K-band
receiver and ATNF correlator with a 64 MHz band
width, 2048 spectral channels, and dual circular polarization at a spectral resolution of 31.25 kHz or 0.42 km
s [−][1] (Hagiwara et al. 2013, 2016), and observations from
April 2016 to May 2017 were conducted using a new
K-band receiver and SAO Spectrometer with a 1 GHz
bandwidth, 32000 spectral channels, and dual circular
polarization (Kuiper et al. 2019) at a spectral resolution of 31.25 kHz or 0.42 km s [−][1] . We used a velocity
resolution of better than ∼1 km s [−][1] to avoid blending of
different velocity features. We adopted a telescope sensitivity of 2.6 Jy K [−][1] to convert antenna temperature to
flux density with a conservatively estimated uncertainty
in the flux density of 50%, as stated in the Tidbinbilla
70 m radio telescope guide [3] or in Kuiper et al. (2019).
Data reduction, including baseline calibration, averaging the two circular polarizations, and flagging bad
scans when required were carried out using GBTIDL [4]

All velocities in the final plots are then converted relative to the Local Standard of Rest using the optical definition. Rms noise levels (1 σ) estimated from each spectrum were ∼50–300mJy for NGC 4945 and ∼40–90mJy
for the Circinus galaxy in each 0.42 km s [−][1] channel. A
summary of the observations is given in Table 2.


3. OBSERVATIONAL RESULTS


3 https://www.atnf.csiro.au/observers/docs/tid obs guide
/tid obs guide.html
4 [https://gbtidl.nrao.edu.](https://gbtidl.nrao.edu) Analysis of the data obtained om
ATNF Correlator was made using ASAP [5] .



Following the approach used for the first detections in
2012, observations of the 321 GHz H 2 O masers toward
the center of NGC 4945 and the Circinus galaxy were
centered on the phase-tracking center of the galaxy
in the velocity range of V LSR =−319.5 – 1436.5 km
s [−][1] for NGC 4945 and V LSR =−439.9 – 1314.1 km
s [−][1] for the Circinus galaxy, covering the total velocity range of the known 22 GHz H 2 O maser emission in
the galaxies (Greenhill et al. 1997b; Braatz et al. 2003;
Greenhill et al. 2003a). No search was made for 321 GHz
maser emission beyond these velocity on this occasion.
Figure 1 (left) compares the two epoch spectra of the
321 GHz H 2 O maser toward the center of NGC 4945.
No maser emission is detected in the second epoch
(2016 November) as the strength of the maser has decreased below the detection limit (3 σ) of 38 mJy. Also,
a counterpart to the highly redshifted velocity feature
at V LSR = 1138.6 km s [−][1] in the 183 GHz H 2 O maser
spectrum (Humphreys et al. 2016) was not found in the
second epoch spectrum. Figure 1 (right) displays multiepoch spectra of the 22 GHz H 2 O maser emission that
were taken from 2014 April to 2016 December with the
Tidbinbilla 70-m telescope, DSS-43, showing a definite
decrease of the maser intensity from mid-2014, at least,
until late 2016.

Figure 2 shows spectra of the 321 GHz H 2 O maser
emission toward the center of the Circinus galaxy in
2012 June and 2017 May, and Figure 3 displays fourepoch spectra of 22 GHz H 2 O maser emission taken at
Tidbinbilla from 2012 June to 2017 May. It should be
noted that the second epoch spectrum at 321 GHz and
the last epoch spectrum at 22 GHz were obtained on the
same date, making it possible to precisely compare velocities of the maser features between the 22 GHz and

321 GHz maser spectra.
In the Circinus galaxy, the most prominent H 2 O maser
emission is detected with a peak flux density of 1.56 Jy at
V LSR = 601.6 km s [−][1] with a signal-to-noise ratio (SNR)
of >80 and a 1 σ rms level of ∼19 mJy per spectral
channel (Figure 3). The line-widths of the detected
Doppler-shifted features may be narrower (<0.445 km
s [−][1] ) than one spectral channel, and narrower than the
22 GHz H 2 O maser features of ∼0.9 km s [−][1] reported
previously (Nakai et al. 1995; Greenhill et al. 1997a;
Braatz et al. 2003; McCallum et al. 2005). In the second epoch observation of the 321 GHz H 2 O maser,
blueshifted features spanning from V LSR =358–360km
s [−][1] are evident with a peak at V LSR = 359.29 km s [−][1],
Doppler-shifted ∼−74 km s [−][1] from the systemic velocity of V LSR = 433 km s [−][1] (de Vaucouleurs et al. 1991;
Braatz et al. 2003), with a peak flux density of 198 mJy.
Blueshifted features between V LSR = 200 and 400 km

4 Hagiwara, Horiuchi, Imanishi, & Edwards



s [−][1] were also found in the 22 GHz maser spectrum on
the same day. The most blueshifted and redshifted
velocity features peak at V LSR = 260.81km s [−][1] and
V LSR = 627.25 km s [−][1], respectively. The total integrated intensity estimated from the spectra of the
321 GHz H 2 O features detected at SNR >5 between
V LSR = 200 and 800 km s [−][1] is 11.1±1.1Jy km s [−][1] .
Figure 4 (left) shows the spectrum of the 321 GHz
maser emission spanning from V LSR = 180−820 km
s [−][1] in the Circinus galaxy. Figure 4 (right) compares
the two epoch spectra at 321 GHz in the highly redshifted velocity range. Signs of marginal features were
suggested at V LSR = 1069 km s [−][1] and V LSR = 1138.6km
s [−][1] in Hagiwara et al. (2013), however these features
were not identified in the second epoch spectrum. As
argued by Pesce et al. (2016), it is most likely that this
portion of the band is impacted by higher atmospheric
absorption resulting in a somewhat higher noise level.
Sub-millimeter 321 GHz (Band 7) continuum images
of NGC 4945 and the Circinus galaxy, obtained by
integrating over the full frequency range (after the
removal of the maser line emission), are shown in
Figure 5. The continuum map of NGC 4945 shows
resolved radio structures, a bright radio source and
extended components, which are consistent with the
map at the same frequency at 0.54 [′′] angular resolution (Hagiwara et al. 2016; Pesce et al. 2016), with
a peak position of α(2000):13 [h] 05 [m] 27.482, δ(2000):
−49 [◦] 28 [′] 05 [′′] .40. The continuum map of the Circinus galaxy shows a bright radio source in the center, accompanying extended structure tracing the spiral arms (Izumi et al. 2018), with a peak position of
α(2000):14 [h] 13 [m] 09.954, δ(2000):−65 [◦] 20 [′] 21 [′′] .01, which
is also consistent with that measured at lower angular resolution (0.54 [′′] ) within uncertainties of ∼0.01 [′′]

(Hagiwara et al. 2013). The flux densities of the
321 GHz continuum and the 321 GHz H 2 O maser emis
sion are summarized in Table 3.

All the maser features detected in our observations

remain unresolved at the angular resolution of ∼0.33 [′′],
or 6.9 pc. The position of the prominent blue-shifted
feature peaking at V LSR = 269.2 km s [−][1] is α(J2000):
14 [h] 13 [m] 09 [s] .952, δ(J2000): −65 [◦] 20 [′] 21.013 [′′], and that
of the strongest feature at V LSR = 600.92 km s [−][1] is
α(J2000): 14 [h] 13 [m] 09 [s] .949, δ(J2000): −65 [◦] 20 [′] 21.019 [′′] .
From the ALMA Cycle 4 Capabilities, the image registration accuracy is ∼θ/20.0, where θ is the angular
resolution. Consequently, the registration accuracy is
∼0.33 [′′] /20 ∼ 0.0165 [′′] in our observations and these positions of the bulk of Doppler-shifted features between
V LSR = 200 and 800 km s [−][1] in Figure 4 are consistent
within that accuracy.



Figure 6 displays the velocity-integrated line intensity (0th moment), overlaid on the 321 GHz continuum (contour map), mean velocity (first moment),
and velocity dispersion (second moment) maps for the
321 GHz H 2 O maser in the Circinus galaxy. From the
0th moment map, the source size of the maser emission deconvolved by the synthesized beam is calculated to be 266±7 mas × 158±2mas, corresponding to
5.6 pc × 3.3 pc, at a position angle (PA) of 35 [◦] ± 1 [◦] .


4. DISCUSSION


Given the observed flux density variability of the
maser features in the spectra, it is clear that the 321 GHz
H 2 O emission in NGC 4945 and the Circinus galaxy
occurs through the maser amplification process. Here
we briefly discuss our non-detection of the 321 GHz
H 2 O maser in NGC 4945 and results of the image analysis of the 321 GHz maser in the Circinus galaxy.


4.1. No Detection and Intensity Variability of 321 GHz
H 2 O Maser in NGC 4945


From the two-epoch observations at 321 GHz in 2012
and 2016 and five-epoch single-dish observations at
22 GHz from 2014–2016, we find that strengths of the
321 GHz and 22 GHz H 2 O masers vary in an apparently
correlated fashion (Figure 1). The total and peak fluxes
of the 321 GHz continuum in 2016 have decreased from
those in 2012 (Table 3). The detected 321 GHz continuum emission of the galaxy is dominated by dust
emission and contributions from the synchrotron and
free-free emissions to the observed flux density are small
as they decrease rapidly at sub-millimeter wavelengths.
The most dominant nuclear continuum component in
the center of the galaxy on the map traces the dust
lanes heated by the AGN in the obscured nucleus.
Although we have only two epochs of data, there is an
apparent correlation between the strength of the masers
and the 321 GHz radio continuum emission from the obscured nucleus (Table 3). This is consistent with the
non-detection of 321 GHz maser emission in 2016. The

321 GHz maser emission that was detected in 2012 and

higher intensity of the 22 GHz maser emission in 2014
were most likely to be enhanced by increased AGNactivity through the thick dust lane in our line of sight
around that period. This supports the conclusion that
the 321 GHz H 2 O emission in the galaxy is a nuclear

maser.

If the maser is powered by X-ray emission from an
AGN (e.g., Neufeld et al. 1994), then the observed intensity variability of the 22 and 321 GHz maser could be
due to the central engine (e.g., Maloney 2002). In the
galaxy, there is a luminous nuclear hard X-ray source

321 GHz H 2 O masers in NGC 4945 and Circinus galaxy 5


Table 1. Summary of the ALMA observations


Galaxy RA DEC D Date N A θ b,PA t on σ c σ l


(J2000) (J2000) (Mpc) (arcsec [2], [◦] ) (min)


(1) (2) (3) (4) (5) (6) (7) (8) (9) (10)

NGC 4945 13 [h] 05 [m] 27 [s] .279 −49 [◦] 28 [′] 04 [′′] .44 3.7 2016-11-18 45 0.381×0.313, -56.5 33 0.6 12.6
Circinus 14 [h] 13 [m] 09 [s] .906 −65 [◦] 20 [′] 20 [′′] .46 4.2 2017-05-06 47 0.330×0.206, 31.0 28 0.6 13.9


Note—(2)-(3) Interferometry phase center positions in R.A. and Declination; (4) Adopted distances for NGC 4945
from Tully et al. (2013) and for Circinus from Freeman et al. (1977); (5) Date of observations in YYYY-mm-dd
format; (6) Number of 12-m antennas used in the ALMA observations; (7) Synthesized beam size and the beam
position angle; (8) On-source time for the target source; (9) Rms noise values in mJy beam [−][1] in the clean continuum
images; (10) Rms noise levels in mJy beam [−][1] in a 488.3 kHz (0.458 km s [−][1] ) spectral channel in the clean line images.


Table 2. Summary of the Tidbinbilla Observations


Galaxy Date of Observation ∆V ∆ν T sys t on σ l


(km s [−][1] ) (km s [−][1] ) (K) (min) (mJy)


(1) (2) (3) (4) (5) (6) (7)


NGC 4945 2014-04-07 [a], 2016-04-13, 2016-10-24 -250–1450 0.42 45–90 6–28 50–300

2016-11-26, 2016-12-10
Circinus Galaxy 2012-06-26, 2012-09-07 [b], 2016-10-24 0–800 0.42 50–65 2–11 40–90

2017-05-06


Note—(2) Date of observations in YYYY-mm-dd format (a: From published data in Hagiwara et al. (2016),
b: from Hagiwara et al. (2013)); (3) Velocity range of 22 GHz maser spectra in Figures 1, 3; (4) Velocity
resolution in each spectrum; (5) Typical values of system noise temperature; (6) Approximate on-source
time for the target source; (7) Rms noise levels in the 0.42 km s [−][1] spectral channel in each spectrum. Note
that the rms values have an uncertainty due to less accurate flux density estimation (see Section 2.2). The
ATNF Correlator was used for the observations up to 2014 April 7, and the Smithsonian Astrophysical
Observatory (SAO) spectrometer was used for the subsequent observations.


Table 3. Measured properties of 321 GHz H 2 O Maser and Continuum Emission toward Circinus galaxy and NGC 4945


Galaxy Epoch [a] Date [b] Maser Line Continuum [d]


Total Flux Peak Flux Peak Velocity [c] Total Flux Peak Flux


(Jy) (Jy beam [−][1] ) (km s [−][1] ) (mJy) (mJy beam [−][1] )


Circinus 1 2012-06-03 0.35±0.04 0.13±0.01 531.1 km s [−][1] 55±6 40.6±4.1

galaxy 2 2017-05-06 4.3±0.4 1.56±0.16 601.6 km s [−][1] 90.4±9.0 42.5±4.3
NGC 4945 1 2012-06-03 0.052±0.005 0.040±0.004 722.6 km s [−][1] 543±54 136.5±13.7

2 2016-11-18        -        -        - 475±48 61.6±6.2


Note—a: Epoch number; b: Date of observations in YYYY-mm-dd format; c: Center velocities of a maser feature in
optical LSR definition; d: 321 GHz continuum emission from the nuclei of the galaxies

6 Hagiwara, Horiuchi, Imanishi, & Edwards



0.06


0.05


0.04


0.03


0.02


0.01


0


-0.01


-0.02


-0.03


0.06


0.05


0.04


0.03


0.02


0.01


0


-0.01


-0.02


-0.03





-200 0 200 400 600 800 1000 1200 1400



15


10


5


0


-5


-10


-15









-200 0 200 400 600 800 1000 1200 1400


Velocity (LSR, km/s)



-200 0 200 400 600 800 1000 1200 1400


Velocity [LSR, km/s]



Figure 1. Spectra of H 2 O maser emission toward the nucleus of NGC 4945. The LSR systemic velocity of NGC 4945, 556 km
s [−][1] is denoted by the vertical arrow. Left: Spectra of 321 GHz H 2 O maser for two epochs, obtained with ALMA. The velocity
resolution is 0.458 km s [−][1] . Right: Spectra of 22 GHz H 2 O maser, obtained with the NASA Deep Space Network 70 m antenna
at Tidbinbilla, DSS-43, for five epochs from 2014 April to 2016 December. The vertical axis shows relative flux density in Jy.
The amplitude scale of each 22 GHz spectrum is displayed with an offsets for display purposes. The velocity resolution is 0.42 km
s [−][1] . The 1 σ noise levels are ∼28–55 mJy in a 0.42 km s [−][1] channel.



1.4


1.2


1


0.8


0.6


0.4


0.2


0


-0.2







-400 -200 0 200 400 600 800 1000 1200



1.4


1.2







1


0.8


0.6


0.4


0.2


0


-0.2

-400 -200 0 200 400 600 800 1000 1200


Velocity [LSR, km/s]


Figure 2. Comparison of 321 GHz H 2 O maser spectra between 2012 June and 2017 May, obtained with ALMA. The velocity
resolution is 0.458 km s [−][1] .

321 GHz H 2 O masers in NGC 4945 and Circinus galaxy 7


Circinus galaxy (22 GHz)



70
60
50
40
30
20
10
0





0 100 200 300 400 500 600 700 800



70
60
50
40
30
20
10
0





0 100 200 300 400 500 600 700 800



70
60
50
40
30
20
10
0





0 100 200 300 400 500 600 700 800



70
60
50
40
30
20
10
0





0 100 200 300 400 500 600 700 800


Velocity [LSR, km/s]


Figure 3. Spectra of 22 GHz H 2 O maser for four epochs, obtained at Tidbinbilla from 2012 June to 2017 May. The LSR systemic
velocity of the galaxy, 433 km s [−][1] is indicated by a longer arrow in each epoch and a shorter arrow indicates blueshifted features
centered at V LSR = 389.5 km s [−][1] .



35


30


25


20


15


10


5


0


1.6


1.4


1.2


1


0.8


0.6


0.4


0.2


0


-0.2





0.2


0.15


0.1


0.05


0


-0.05


-0.1





200 300 400 500 600 700 800



800 900 1000 1100 1200 1300





0.2


0.15


0.1


0.05


0


-0.05


-0.1





200 300 400 500 600 700 800


Velocity [LSR, km/s]



800 900 1000 1100 1200 1300


Velocity [LSR, km/s]



Figure 4. Left: Comparison of 22 GHz (upper) and 321 GHz (lower) H 2 O maser spectra toward the nucleus of Circinus galaxy
zoomed in the velocity range of V LSR = 150–800 km s [−][1] in Figure 2. Note that the both spectra were taken on 2017 May 6. The
longer arrow in each panel shows the systemic velocity, and V LSR = 389.49 km s [−][1] (upper) and V LSR = 359.29 km s [−][1] (lower)
features are marked by a shorter arrow. Right: Highly Doppler-shifted (high-velocity) 321 GHz maser spectra toward the nucleus
of the Circinus galaxy in the velocity range of V LSR = 800–1300 km s [−][1] at epoch 1 (upper) and epoch 2 (lower). The channel
spacing is 0.458 km s [−][1] . In the epoch 1 spectrum, high-velocity tentative features were suggested at V LSR = 1069 km s [−][1] and
1129 km s [−][1] (shown by arrows)(Hagiwara et al. 2013). However, in the epoch 2 spectrum no emission was observed at these
frequencies.



(X-ray luminosity: L X ∼ 4 × 10 [43] erg s [−][1] ) buried in
the Compton-thick nucleus (e.g., Marinucci et al. 2017).
The X-ray luminosity is highly variable with a time scale
of ∼1 day, suggesting that the size scale of X-ray emitting region is no more than ∼0.001pc (Madejski et al.
2000), however it is uncertain whether this compact X


ray region is responsible for the decreased maser intensities over the four years. Moreover, little is known about
the variability of the 321 GHz masers.


4.2. The 321 GHz Maser in Circinus galaxy

8 Hagiwara, Horiuchi, Imanishi, & Edwards


Figure 5. Continuum maps of NGC 4945 (left) and the Circinus galaxy (right) at 321 GHz (Band 7). The synthesized beams
are shown in the bottom left in each panel (NGC 4945: 0.381 [′′] ×0.313 [′′] ; Circinus galaxy: 0.330 [′′] ×0.206 [′′] ). For both maps the
flux densities are shown by color-scales in Jy beam [−][1] .


Figure 6. Color-scale maps of 321 GHz H 2 O maser emission in the Circinus galaxy: (a) Integrated line intensity map (0th
moment) and 321 GHz continuum with overlaying contours having a peak flux density of 42.5 mJy beam [−][1] with the contour
levels at 7, 9.8, 14, 19.7, 28, 39.5, and 56 σ (1 σ = 0.63 mJy beam [−][1] ), (b) mean velocity (first moment) map, and (c) velocity
dispersion (second moment) map. These figures are obtained from our ALMA Cycle 4 observations. The total velocity coverage
of the figures is V LSR = 228−685 km s [−][1] . The synthesized beam sizes (0.33 [′′] ×0.21 [′′] ) are shown in the bottom left of each panel.
A cross in each panel marks the nucleus (the continuum peak) of the galaxy. The horizontal bar at the bottom marks 10 pc.
Note that in (b) the surrounding components, reaching an extreme of ∼650 km s [−][1] (pink) are H 2 O emission extending larger
than the synthesized beam size, resulting in a ring-like appearance. The blueshifted maser features peaking at V LSR ≃ 269 km
s [−][1] in Figure 4 (left) are also extended and do not show any velocity gradient on the map.


4.2.1. Origin of the maser and physical conditions giving The isotropic luminosity of the 321 GHz maser emisrise to the maser sion, assuming isotropic radiation of the maser, is cal

321 GHz H 2 O masers in NGC 4945 and Circinus galaxy 9



culated to be ∼65 L ⊙ using the formula,
L = 1.04×10 [−][3] ν D [2] [ �] S dv L ⊙, where ν is the rest frequency (321.226 GHz), D is the distance to the Circinus galaxy of 4.2 Mpc (Freeman et al. 1977), and
� S dv is the integrated intensity (11.1 Jy km s −1 )
(Humphreys et al. 2016). This value is roughly a factor
of two larger than the isotropic luminosity of the 22 GHz
maser emission of ∼32 L ⊙ in the galaxy (Whiteoak et al.
1986) (adopting D = 4.2 Mpc). This strongly supports
the belief that the maser in the galaxy is a nuclear
maser arising from AGN-activity and not from starforming activity in the galaxy. Moreover, the position
of the 321 GHz maser coincides with the radio nucleus
and the significant flux variability is measured between
the two epochs, which indicates that the maser may be
associated with ejecta from the active nucleus such as a
radio jet. Given the relatively higher maser luminosity,
comparable with that of the 22 GHz megamaser known
in the galaxy, we conclude that the maser amplifies the
background continuum and its variability is due to the
activity from a central engine in the active nucleus and
so the observed 321 GHz maser in the Circinus can be

categorized as a luminous H 2 O megamaser.
The isotropic luminosity of the 183 GHz H 2 O maser
in NGC 4945, ∼1300 L ⊙ is roughly two orders of magnitude larger than that of the 321 GHz maser in NGC 4945
at ≈5 L ⊙ and the Circinus galaxy at ≈ 65–100 L ⊙ (this
paper; Humphreys et al. 2016; Hagiwara et al. 2016;
Pesce et al. 2016). The upper state energies (E u /k) of
the H 2 O emission for the 22 GHz and 183 GHz transition are 644 K and 205 K, respectively, while E u /k
for the 321 GHz transition is much higher: 1862 K.
In NGC4945, [˙] the energy of a significant portion of
dense gas giving rise to maser amplification may not be
sufficiently high enough for intense 321 GHz maser to
arise, while it could be sufficient for elevating the strong
183 GHz maser emission. Therefore, insufficient excitation of the 321 GHz maser in NGC 4945 could make the

strength of the maser weaker than that of the 183 and
22 GHz masers (Humphreys et al. 2016). It is therefore
most likely that the strength of the 183 GHz maser in
the Circinus galaxy will be greater than the 321 GHz
maser in the galaxy in future observations. However,
due to the higher excitation condition required for the
321 GHz maser, it is more likely that the 321 GHz masers
can probe regions closer to the nucleus, which can be
verified with higher angular resolution observations.


4.2.2. Velocity Gradient


One of the most exciting results from our observations
is that part of the velocity field of the dense molecular gas within ∼6 pc of the nucleus in the Circinus



galaxy has been resolved at our ∼0.3 [′′] spatial resolution. As is evident in Figure 6(b), there is a distinct
velocity gradient in the 321 GHz H 2 O maser emission
spanning ∼110 km s [−][1] in the first moment map. Figure 6(c) shows the second moment map which, as for
Figure 6(b), is produced from the spectral-line cube containing maser features lying at V LSR = 256–670km s [−][1] .
This indicates that the maser emission is partly resolved
in our second epoch observation at ∼0.3 [′′] (∼6 pc) resolution, although neither velocity gradient nor velocity
dispersion was found in the first epoch observation in
2011 (Hagiwara et al. 2013). This is likely to have arisen
from the improvement in (u, v) coverage due to the significantly larger number of baselines, as a result of the
number of antennas increasing from 18 to 47, and the
longer integration time of 28 minutes, compared to 18
minutes in the first epoch.
Assuming that the observed masers are on a simple circular disk with a rotational velocity of V rot at
a radius r from the nucleus, the observed velocity
gradient (dV /dl) along PA = 35 [◦] can be expressed as
dV /dl ≃d(V rot sinθ sini)/d(rθ) ≃ V rot sini/r, where
l(=rθ) is the projected distance, i is the disk inclination, and the approximation of sinθ ≃ θ is being made.
Adopting the disk inclination of >75 [◦] (sini ≃1) estimated from the near-infrared emission (Tristram et al.
2014) or the CO disk with r = 100–600pc (Curran et al.
2008), together with the observed parameters of dV/dl
= 8.8 km s [−][1] pc [−][1] and V red − V sys = 682 km s [−][1] –
433 km s [−][1] = V rot ≃ 250 km s [−][1], r is estimated to be
∼28 pc. Since the most red- or blue-shifted features
are interpreted as originating in an edge-on disk (e.g.,
Miyoshi et al. 1995), the rotation speed ranges up to
∼250 km s [−][1] using the most Doppler-shifted velocity of
V LSR ≃682 km s [−][1] . This value is to the “lower” rotation
velocity (∼260 km s [−][1] ) of the sub-parsec scale disk in
the Circinus galaxy, estimated from the 22 GHz maser
emission (McCallum et al. 2009), compared to the Keplerian rotation velocity (∼1100 km s [−][1] ) of the disk in
NGC 4258. Considering a simple circular motion around
the nucleus, we estimate the dynamical mass (M dyn )
confined within the central 28 pc to be ∼4.3×10 [8] M ⊙,
which is approximately two orders of magnitude larger
than the enclosed mass of ∼1.7×10 [6] M ⊙ within r = 0.1 pc
that was measured by VLBI observations, assuming a
circular motion (Greenhill et al. 2003b).
We note that the derived value of the dynamical
mass (r ≲ 28 pc) is comparable with that of the larger
scale dynamical mass of ∼3.2×10 [8] M ⊙ within the central 140 pc (Curran et al. 1998) and approximately two
orders of magnitude larger than the total molecular
mass of M H 2 ≈ 3×10 [6] M ⊙ within the central ∼75 pc in

10 Hagiwara, Horiuchi, Imanishi, & Edwards



the circumnuclear disk probed by CO (3–2) molecular
gas with the deconvolved source size of 3.62 [′′] × 1.66 [′′]

(∼76 pc × 35 pc) (Izumi et al. 2018). This gives a gas
mass fraction of only M H 2 /M dyn ≈ 0.6% within the central 28 pc.
For the Circinus galaxy, a molecular gas fraction in the
central 500 pc of M H 2 /M dyn ≈ 50% has been reported
Curran et al. (2008). It is suggested that the fraction
of the gas mass is up to 25% of the dynamical mass in
spiral galaxies (Young and Scoville 1982).
This discrepancy is probably caused by our assumption that the 321 GHz maser traces the outer part of the
central disk within the central ∼28 pc, which would result in an overestimate of the dynamical mass on a scale
of 10 pc.
If the 321 GHz maser resides in the 22 GHz maser disk

with r ≃ 0.1–0.4pc, obtained by VLBI mapping of the
22 GHz maser (Greenhill et al. 2003b; McCallum et al.
2009), the 321 GHz masers should be located closer
to the central engine than the 22 GHz masers as
the 321 GHz maser requires higher temperatures than
22 GHz masers. For the 321 GHz masers, strong inversion of the emission occurs in denser regions at a gas
kinetic temperature, T k ≳ 1000 K and n(H 2 ) = 10 [8] –
10 [10] cm [−][3] . For the 22 GHz masers, the strong inversion
occurs over a broader range of physical conditions, spanning T k of ∼300–1000 K and n(H 2 ) ≲10 [8] to 10 [10] cm [−][3]

(Elitzur et al. 1989; Yates et al. 1997).
We thus postulate that the 321 GHz maser traces the
inner part of the masering disk with r = 0.1–0.4pc, as
in the circumnuclear disk illuminated by X-rays the
temperature increases closer to the central engine (e.g.,
Neufeld & Maloney 1995). Alternatively, the observed
H 2 O velocity gradient could trace non-circular motions
and may not be connected to the overall velocity field
on that scale.

Since the position angle of the detected gradient is
comparable to that of the synthesized beam (see Table 3), the intrinsic position angle of the velocity gradient is unknown. However, the position angle (35 [◦] ±1 [◦] )
of the maser emission deconvolved by the synthesized
beam largely agrees with that of the 22 GHz H 2 O maser
disk (29 [◦] ±3 [◦] at r = 0.1 pc, and 56 [◦] ±6 [◦] at r = 0.4 pc
(Greenhill et al. 2003b). This suggests that the inner
part of each gas structure has similar position angles on
all spatial scales (Curran et al. 2008).
Further observations at higher angular resolution
would enable us to clarify the inner part of gaseous
structure and the true origin of the velocity gradient.


4.2.3. 22 GHz Maser and 321 GHz Maser Comparison



The VLBI study of the 22 GHz maser emission by
Greenhill et al. (2003b) revealed the spatial distribution
of the individual maser features within the total extent of ∼0.04 [′′] × 0.09 [′′] (∼0.8 × 1.9 pc) and the origins
of those maser sources were divided into two categories:
the thin disk or outflows in the galaxy. They found that
the velocity range of the maser emission associated with
outflows is up to ∼±160 km s [−][1] from the systemic velocity, which corresponds to V LSR ≃ 300–570km s [−][1],
while the disk maser emission spans V LSR ≃ 250–280
km s [−][1] in the blueshifted velocity range and V LSR ≃
570–700 km s [−][1] in the redshifted range. The bulk of the
emission in the 321 GHz maser spectra has been detected
in blue- and red-ward velocities but not at V LSR ≃ 300–
500 km s [−][1], which implies that the 321 GHz maser features in the blue- and redshifted velocity ranges largely
originate from the thin disk, as in the case of the 22 GHz
masers revealed by the VLBI study. However, in the case
of the 321 GHz maser, it is not possible to distinguish
whether the maser originates from a disk, an outflow, or
both a disk and outflow due to lack of spatial resolution
of our ALMA observations.
Contrary to the disk maser, on 2017 May 6 (Figure 2 and Figure 4(left)), strong features centered
on V LSR = 359.29km s [−][1] appeared in the 321 GHz
spectrum, while blueshifted features centered around
V LSR = 380 km s [−][1] were found in the 22 GHz maser
spectrum. We interpret this to mean that these
blueshifted features, that appeared at both 321 GHz
and 22 GHz, are outflow masers that flared at the same
period and they are associated with significant shocks
with the surrounding molecular materials in the nuclear region. This also supports the hypothesis that the
321 GHz and 22 GHz masers are powered by the central
engine, as argued in Section 4.1.
It should be noted that submillimeter stellar H 2 O masers
are often found to be associated with outflow jets, while
the 22 GHz masers are primarily found in disks (e.g.,
Patel et al. 2007). However, it still remains unclear to
what extent these findings can be applied to the cases
of extragalactic 321 GHz H 2 O masers.


4.2.4. Velocity Dispersion


In Figure 6(c), we find a high velocity dispersion region, with a velocity dispersion (σ v ) of ∼148 km s [−][1],
where the rotation velocity (V rot = V LSR – V SYS ) is
29 km s [−][1] in the first moment map, is offset to the northeast of the continuum nucleus and a gradient of the velocity dispersion is seen between V LSR ≃ 98 km s [−][1] and
148 km s [−][1] along the southwest to northeast direction.
We speculate that velocities at the northeastern part are
more blueshifted than those at the southeast part in the

321 GHz H 2 O masers in NGC 4945 and Circinus galaxy 11



first moment map, which reduces the opacity and results
in making the turbulent molecular gas appear stronger
(Imanishi et al. 2018, 2020). It is interesting to note
that the relative velocity dispersion values of V rot /σ v
(Treister et al. 2020) increase from ∼ 0.2 to 1.4 from
the northeast to the southwest direction and the veloc
ity dispersion distribution is similar to the velocity gradient. It is not certain whether the velocity dispersion
distribution can be explained by our simple speculation,
however it could be dynamically linked to circular or
non-circular motion on scales of 10 pc.
Future sub-millimeter VLBI mapping of the 321 GHz
H 2 O masers at milliarcsecond resolution (e.g., Fish et al.
2013) should be able to clarify the sub–parsec-scale kinematics of the galaxy by pin-pointing the distributions
of each of the maser features.


5. CONCLUSIONS


We have observed H 2 O masers in the 321 GHz transition toward the nearby active galactic nuclei NGC 4945
and the Circinus galaxy at ∼0.3 [′′] angular resolution with
ALMA Band 7. Comparison of two epochs of ALMA observations show that the flux densities of the 321 GHz
H 2 O masers in the galaxies are significantly variable
on timescales of 4–5 years and the nuclear continuum
emission varies in a correlated fashion with the maser

in NGC 4945, while the correlation between the maser
and the nuclear continuum is less certain in the Circinus
galaxy. The significant variability in the flux densities
has confirmed that the observed H 2 O emission arises
from nuclear masers. With the 70 m telescope at Tidbinbilla we also conducted single-dish measurements of
the 22 GHz maser emission over 3–5 epochs between the
two ALMA observations toward the galaxies to compare
the variability of the fluxes and velocities between the
321 GHz and 22 GHz maser lines. This revealed in the
Circinus galaxy the flaring features of the 321 GHz and
22 GHz maser emission were found largely in the same
blueshifted velocity range on the same day. It is thus
likely that the 321 GHz and 22 GHz masers originate in
similar kinematics and physical conditions.
Contrary to the previous lower spatial resolution observations, made with a much smaller number of antennas, in the Circinus galaxy we detected a velocity gradient and dispersion, traced by the 321 GHz H 2 O maser
emission, in a roughly southwest to northeast direction.
This position angle is similar to that of the sub-parsec
scale thin disk probed by the 22 GHz H 2 O masers. With
the velocity gradient spanning ∼110 km s [−][1], we estimate the dynamical mass within the central 28 pc to
be ∼4.3×10 [8] M ⊙, which is significantly larger than the
dynamical mass and the molecular gas mass within the



similar radii. Therefore, the observed velocity gradient
does not likely trace the extension of the sub-parsec–
scale 22 GHz maser disk but might indicate non-circular
motion rather than the simple circular motion of the
disk on that scale. If the 321 GHz maser is in the cir
cumnuclear disk, it should be observed closer to the central engine than the 22 GHz masers as the excitation of
321 GHz maser needs a higher temperature in denser

gas.
We speculate that blueshifted H 2 O maser emission at
north-eastern region reduces the opacity, making turbulence of molecular gas more conspicuous, which results
in the higher velocity dispersion at that region. The
gradient of the velocity dispersion is also found along
the same position angle as the velocity gradient. Its
origin is uncertain from our data, however it could be
physically connected to organized movements like circular motion. Overall, the comparison of our data to
the earlier VLBI studies of the 22 GHz H 2 O maser suggests that the 321 GHz H 2 O maser could not trace an
extension of the sub-parsec scale thin disk but the variable blue-shifted features might trace the nuclear outflows. Higher spatial observations using ALMA or future
sub-millimeter VLBI might reveal whether the 321 GHz
H 2 O maser probes a dynamical structure of inner parsecs or inner part of the circumnuclear disk in the Circinus galaxy.


We thank the anonymous referee for useful comments.
YH thanks Kazuya Saigo for his support with the ALMA
data reduction pipeline. This work was supported by
JSPS KAKENHI Grant Number JP15H03644 (YH) and
21K03632 (MI). This paper makes use of the following ALMA data: ADS/JAO.ALMA #2016.1.00150.S,
#2011.0.00121.S. ALMA is a partnership of ESO, NSF
and NINS, together with NRC, MOST and ASIAA,
and KASI, in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ. The Tidbinbilla 70-m telescope,
DSS-43, is part of the NASA Deep Space Network and
is operated by CSIRO. This research has made use of
the NASA/IPAC Extragalactic Database (NED), which
is funded by the National Aeronautics and Space Administration and operated by the California Institute
of Technology. This project made use of the Smithsonian Astrophysical Observatory 4×32k-channel spectrometer (SAO32k) and the TAMS observatory Ctrl observing system, which were developed by L. Greenhill
(Center for Astrophysics), I. Zaw (New York University
Abu Dhabi), D. Price, and D. Shaff, with funding from
SAO and the NYUAD Research Enhancement Fund and

in-kind support from the Xilinx University Program.

12 Hagiwara, Horiuchi, Imanishi, & Edwards


Facilities: ALMA, Tidbinbilla 70m (DSS-43) Software: CASA,AIPS,ASAP,GBTIDL


REFERENCES



Ar´evalo, P., Bauer, F. E., Puccetti, S., et al. 2014, ApJ,

791, 81

Braatz, J. A., Wilson, A. S., & Henkel, C. 1994, ApJL, 437,

L99

Braatz J. A., Wilson A. S., & Henkel C. 1996, ApJS, 106, 51

Braatz, J. A., Wilson, A. S., Henkel, C., Gough, R., &

Sinclair, M. 2003, ApJS, 146, 249

Braatz, J. A., & Gugliucci, N. E. 2008, ApJ, 678, 96

Cernicharo, J., Pardo, J. R., & Weiss, A. 2006, ApJ, 646,

L49

Curran, S. J., Johansson, L. E. B., Rydbeck, G., & Booth,

R. S. 1998, A&A, 338, 863

Curran, S. J., Rydbeck, G., Johansson, L. E. B., & Booth,

R. S. 1999, A&A, 344, 767

Curran, S. J., Koribalski, B. S., & Bains, I. 2008, MNRAS,

389, 63

de Vaucouleurs, G., de Vaucouleurs, A., Corwin, H. G., et

al. 1991, Third Reference Catalog of Bright Galaxies

(Berlin: Springer)

Dos Santos, P. M., & L´epine, J. R. D. 1979, Nature, 278, 34

Elitzur, M., Hollenbach, D. J., & McKee, C. F. 1989, ApJ,

346, 983

Fish, V., Alef, W., Anderson, J., et al. 2013,

arXiv:1309.3519

Freeman, K. C., Karlsson, B., Lynga, G., et al. 1977, A&A,

55, 445

Galametz, M., Zhang, Z.-Y., Immer, K., et al. 2016,

MNRAS, 462, L36

Greenhill, L. J., Ellingsen, S. P., Norris, R. P., et al. 1997a,

ApJ, 474, L103

Greenhill, L. J., Moran, J. M., & Herrnstein, J. R. 1997b,

ApJ, 481, L23

Greenhill, L. J., Kondratko, P. T., Lovell, J. E. J., et al.

2003a, ApJL, 582, L11

Greenhill, L. J., Booth, R. S., Ellingsen, S. P., et al. 2003b,

ApJ, 590, 162

Greenhill, L. J., Kondratko, P. T., Moran, J. M., et al.

2009, ApJ, 707, 787

Hagiwara, Y., Diamond, P. J., & Miyoshi, M. 2002, A&A,

383, 65

Hagiwara, Y., Diamond, P. J., Miyoshi, M., et al. 2003,

MNRAS, 344, L53

Hagiwara, Y., Miyoshi, M., Doi, A., & Horiuchi, S. 2013,

ApJL, 768, L38

Hagiwara, Y., Horiuchi, S., Doi, A., Miyoshi, M., &

Edwards, P. G. 2016, ApJ, 827, 69



Hagiwara, Y., Doi, A., Hachisuka, K., & Horiuchi, S. 2018,

PASJ, 70, 54

Henkel, C., Peck, A. B., Tarchi, A., et al. 2005, A&A, 436,

75

Humphreys, E. M. L., Greenhill, L. J., Reid, M. J., et al.

2005, ApJ, 634, L133

Humphreys, E. M. L., Vlemmings, W. H. T., Impellizzeri,

C. M. V., et al. 2016, A&A, 592, L13

Imanishi, M., Nakanishi, K., Izumi, T., et al. 2018, ApJL,

853, L25

Imanishi, M., Nguyen, D. D., Wada, K., et al. 2020, ApJ,

902, 99

Imanishi, M., Hagiwara, Y., Horiuchi, S., et al. 2021,

MNRAS, 502, L79

Isobe, N., Kubota, A., Makishima, K., et al. 2008, PASJ,

60, 241

Iwasawa, K., Koyama, K., Awaki, H., et al. 1993, ApJ, 409,

155

Izumi, T., Wada, K., Fukushige, R., Hamamura, S., &

Kohno, K. 2018, ApJ, 867, 48

Kondratko, P. T., Greenhill, L. J., Moran, J. M., et al.

2006, ApJ, 638, 100

K¨onig, S., Mart´ın, S., Muller, S., et al. 2017, A&A, 602, A42

Kuiper, T. B. H., Franco, M., Smith, S., et al. 2019,

Journal of Astronomical Instrumentation, 8, 1950014
Madejski, G., Zycki, [˙] P., Done, C., et al. 2000, ApJL, 535,

L87

Maloney, P. R. 2002, PASA, 19, 401

Marconi. A., Moorwood, A. F. M., Origlia, L., & Olivia, E.

1994, Messenger, 78, 20

Marinucci, A., Bianchi, S., Fabbiano, G., et al. 2017,

MNRAS, 470, 4039

McCallum, J. N., Ellingsen, S. P., Jauncey, D. L., Lovell, J.

E. J., & Greenhill, L. J. 2005, AJ, 129, 1231

McCallum, J. N., Ellingsen, S. P., Lovell, J. E. J., Phillips,

C. J., & Reynolds, J. E. 2009, MNRAS, 392, 1339

McMullin, J. P., Waters, B., Schiebel, D., et al. 2007,

Astronomical Data Analysis Software and Systems XVI,

376, 127

Miyoshi, M., Moran, J., Herrnstein, J., et al. 1995, Nature,

373, 127

Nakai, N., Inoue, M., Miyazawa, K., Miyoshi, M., & Hall,

P. 1995, PASJ, 47, 771

Neufeld, D. A., Maloney, P. R., & Conger, S. 1994, ApJL,

436, L127

Neufeld, D. A. & Maloney, P. R. 1995, ApJL, 447, L17

321 GHz H 2 O masers in NGC 4945 and Circinus galaxy 13



Patel, N. A., Curiel, S., Zhang, Q., et al. 2007, ApJL, 658,

L55

Pesce, D. W., Braatz, J. A., & Impellizzeri, C. M. V. 2016,

ApJ, 827, 68

Puccetti, S., Comastri, A., Fiore, F., et al. 2014, ApJ, 793,

26

Tarchi, A., Castangia, P., Columbano, A., et al. 2011,

A&A, 532, A125

Treister, E., Messias, H., Privon, G. C., et al. 2020, ApJ,

890, 149. doi:10.3847/1538-4357/ab6b28
Tristram, K. R. W., Burtscher, L., Jaffe, W., et al. 2014,

A&A, 563, A82

Tully, R. B., Courtois, H. M., Dolphin, A. E. et al. 2013,

AJ, 146, 86



van Moorsel, G., Kemball, A., & Greisen, E. 1996,


Astronomical Data Analysis Software and Systems V,


101, 37


Whiteoak, J. B., & Gardner, F. F. 1986, MNRAS, 222, 513


Yang, Y., Wilson, A. S., Matt, G., et al. 2009, ApJ, 691, 131


Yates, J. A., Field, D., & Gray, M. D. 1997, MNRAS, 285,


303


Young, J. S., & Scoville, N. 1982, ApJ, 258, 467


Zhang, J. S., Henkel, C., Kadler, M., et al. 2006, A&A, 450,


933


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "ALMA CO(3-2) circumnuclear disk molecular gas mass (M_H2 ~ 3x10^6 M_sun within central ~75 pc) and size in Circinus galaxy",
  "failed_quote": "total molecular mass of M H 2 ≈ 3×10 [6] M ⊙ within the central ∼75 pc in the circumnuclear disk probed by CO (3–2) molecular gas with the deconvolved source size of 3.62 [′′] × 1.66 [′′] (∼76 pc × 35 pc) (Izumi et al. 2018)."
 },
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "Subtracted from spectral line visibilities using line-free channels prior to CLEAN deconvolution",
  "failed_quote": "After phase and amplitude calibrations, the 321 GHz continuum emission of NGC4945 and the Circinus galaxy was subtracted from the spectral line visibilities using line-free channels prior to CLEAN deconvolution of line emission."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Compute isotropic luminosity from integrated intensity, and derive rotating disk radius and enclosed dynamical mass from the measured velocity gradient and maximum rotation velocity",
  "failed_quote": "The isotropic luminosity of the 321 GHz maser emission, assuming isotropic radiation of the maser, is calculated to be ∼65 L ⊙ using the formula, L = 1.04×10 [−][3] ν D [2] [ �] S dv L ⊙"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Isotropic radiation of the maser and distance D = 4.2 Mpc",
  "failed_quote": "The isotropic luminosity of the 321 GHz maser emission, assuming isotropic radiation of the maser, is calculated to be ∼65 L ⊙ using the formula, L = 1.04×10 [−][3] ν D [2] [ �] S dv L ⊙, where ν is the rest frequency (321.226 GHz), D is the distance to the Circinus galaxy of 4.2 Mpc"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Isotropic luminosity of 321 GHz H2O maser in Circinus galaxy = 65 L_sun",
  "failed_quote": "The isotropic luminosity of the 321 GHz maser emission, assuming isotropic radiation of the maser, is calculated to be ∼65 L ⊙"
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[1]",
  "value": "Only two ALMA epochs are available, limiting the certainty of correlations between maser variability, continuum variability, and compact X-ray variability.",
  "failed_quote": "however it is uncertain whether this compact X-ray region is responsible for the decreased maser intensities over the four years."
 }
]
```
