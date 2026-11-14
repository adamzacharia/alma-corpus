# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...909..181L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
D RAFT VERSION J ANUARY 14, 2021
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**Revisited cold gas content with atomic carbon [C** **I** **] in z=2.5 protocluster galaxies**


M INJU [M. L](http://orcid.org/0000-0002-2419-3068) EE, [1] I CHI T [ANAKA](http://orcid.org/0000-0002-4937-4738), [2] D [AISUKE](http://orcid.org/0000-0002-2364-0823) I ONO, [3, 4] R YOHEI [K](http://orcid.org/0000-0002-8049-7525) AWABE, [3, 4] T ADAYUKI [K](http://orcid.org/0000-0002-2993-1576) ODAMA, [5] K OTARO [K](http://orcid.org/0000-0002-4052-2394) OHNO, [6, 7]

T OSHIKI [S](http://orcid.org/0000-0002-2501-9328) AITO, [8] Y OICHI T [AMURA](http://orcid.org/0000-0003-4807-8117), [9]


1 _Max-Planck-Institut f¨ur Extraterrestrische Physik (MPE), Giessenbachstr., D-85748 Garching, Germnay_
2 _Subaru Telescope, National Astronomical Observatory of Japan, 650 North Aohoku Place, Hilo, HI 96720, USA_
3 _National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan_
4 _The Graduate University for Advanced Studies (SOKENDAI),2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan_
5 _Astronomical Institute, Tohoku University, Aoba-ku, Sendai 980-8578, Japan_
6 _Institute of Astronomy, Graduate School of Science, University of Tokyo, 2-21-1 Osawa, Mitaka, Tokyo 181-0015, Japan_
7 _Research Center for the Early Universe, School of Science, The University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033, Japan_
8 _Max-Planck Institute for Astronomy, Konigstuhl 17, D-69117, Heidelberg, Germany_
9 _Department of Physics, Nagoya University, Furo-cho, Chikusa-ku, Nagoya 464-8601, Japan_


(Received; Revised; Accepted)


Submitted to


ABSTRACT


We revisit the cold gas contents of galaxies in a protocluster at _z_ = 2 _._ 49 using the lowest neutral atomic
carbon transition [C I ] [3] _P_ 1 _−_ [3] _P_ 0 from Atacama Large Millimeter/submillimeter Array observations. We aim
to test if the same gas mass calibration used in field galaxies can be applied to protocluster galaxies. Five
galaxies out of sixteen targeted galaxies are detected in the [C I ] line, and these are all previously detected
in CO (3–2) and CO (4–3) and three in 1.1 mm dust continuum. We investigate the line luminosity relations
between CO and [C I ] in the protocluster and compare with other previous studies. We then compare the gas
mass based on three gas tracers of [C I ], CO(3–2), and dust if at least one of the last two tracers are available.
Using the calibration adopted for field main-sequence galaxies, the [C I ] -based gas measurements are lower
than or comparable to the CO-based gas measurements by -0.35 dex at the lowest with the mean deviation of
-0.14 dex. The differences between [C I ] - and the dust- based measurements are relatively mild by up to 0.16
dex with the mean difference of 0.02 dex. Taking these all together with calibration uncertainties, with the

[C I ] line, we reconfirm our previous findings that the mean gas fraction is comparable to field galaxies for
a stellar-mass range of log ( _M_ star _/M_ _⊙_ ) = [10 _._ 6 _,_ 11 _._ 3]. However, at least for these secure five detections, the
depletion time scale decreases more rapidly with stellar mass than field galaxies that might be related to earlier
quenching in dense environments.


_Keywords:_ galaxies: clusters: general – galaxies: evolution – galaxies: high-redshift – galaxies: ISM – large
scale structure of universe



1. INTRODUCTION


Molecular gas plays a prominent role in the evolution of
galaxies by fuelling star-forming activities. The bulk of the
gas is the molecular hydrogen (H 2 ), but it does not have a permanent dipole moment. A weak emission is only allowed at
a high energy level, hampering direct observations of it in the


Corresponding author: Minju M. Lee

[minju@mpe.mpg.de](mailto: minju@mpe.mpg.de)



typical ISM condition. As alternative tracers, CO lines and
dust have been used to weigh the total molecular gas in galaxies through the “conversion factors” calibrated by the Milky
Way and nearby galaxy observations. With the advent of
sensitive interferometric facilities such as the Atacama Large
Millimeter/submillimeter Array (ALMA), the NOrthern Extended Millimeter Array (NOEMA), and the Karl G. Jansky
Very Large Array (JVLA), the cosmic evolution of molecular gas up to _z_ _∼_ 6 is measured for many field galaxies (e.g.,
Tacconi et al. 2020).

2 M INJU M. L EE ET AL .



However, it is still an open question whether the same
calibration (or conversion factor) can be applied to galaxies
in dense environments of clusters or their progenitors, protoclusters, because the calibration might be different from
isolated field galaxies due to different excitation conditions,
metallicity, and ambient radiation fields. Such a test is necessary by using an independent method, whether the calibration
of field galaxies can be applied in the same manner.
Fine structure lines of atomic carbon [C I ] is an alternative
tracer of the molecular gas. A traditional theoretical model of
photodissociation regions (PDRs) viewed that the [C I ] line
is originated from a narrow region at the interface between

[C II ] and CO (e.g., Tielens & Hollenbach 1985a,b; Hollenbach & Tielens 1999; Kaufman et al. 1999), but it was
challenged by the observations that CO and [C I ] can coexist
based on the constant column density ratio N([C I ] )/N(CO)
over a wide range of ambient FUV field and physical conditions in the Orion clouds and Galactic center (Ikeda et al.
1999, 2002; Ojha et al. 2001) pointing to a potential use of

[C I ] as a molecular gas tracer (Gerin & Phillips 2000; Papadopoulos et al. 2004). A tight, linear correlation between
the CO (1–0) and [C I ] line luminosities over five orders
of magnitude for local galaxies strengthened this view (e.g.,
Jiao et al. 2019).
Not only is an independent molecular gas tracer, but

[C I ] line can also be an efficient gas tracer than the lowest CO (1–0) in terms of observing time with the current
facilities. The current JVLA can target CO (1–0) line for
_z_ _>_ 1 _._ 3 galaxies, observing the [C I ] can be more efficient
than CO (1–0) considering the positive K-correction at the
same resolution and the robustness of [C I ] against CMB at
very high redshifts ( _z_ ≳ 4, da Cunha et al. 2013; Zhang et al.
2016). The frequency coverage of ALMA and NOEMA only
allows _J_ _>_ 1 transitions of CO for galaxies at _z_ ≳ 0 _._ 5 so
that one needs an additional assumption of gas excitation to
convert the line flux into the CO (1–0) luminosity.
The lowest transition of [C I ] [3] _P_ 1 _−_ [3] _P_ 0 (hereafter written
simply as the [C I ] (1–0) transition) is optically thin in most
cases, less sensitive to excitation temperature compared to

[C I ] [3] _P_ 2 _−_ [3] _P_ 1 (hereafter [C I ] (2–1)) when converting to a
mass (Weiß et al. 2005). Similar to CO (1–0)-to-H 2 conversion factor, converting the [C I ] (1–0) line flux into a gas measurement needs an assumption of the [C I ] /[H 2 ] abundance
ratio (hereafter _X_ CI ). Recent calculations showed that _X_ CI
is robust or well-behaved even in low metallicity and high
cosmic ray environments (e.g., Offner et al. 2013; Glover &
Clark 2016; Bisbas et al. 2017).
So far, [C I ] line searches and detections at high- _z_ have
happened in galaxies well above the star-forming mainsequence, or on the main-sequence in general fields (e.g.,
Walter et al. 2011; Alaghband-Zadeh et al. 2013; Popping
et al. 2017; Valentino et al. 2018, 2020 (hereafter V20);



Bourne et al. 2019). In this Paper, we perform a [CI] line
search by targeting main-sequence galaxies associated with
a protocluster at _z_ = 2 _._ 49, where CO and dust emissions
are already detected (Lee et al. 2017, 2019, hereafter we refer to these two papers as Paper I and Paper II, respectively).
These main-sequence star-forming galaxies are H _α_ emitters
selected by a narrow-band filter technique using the Subaru
telescope (Tanaka et al. 2011). We report [C I ] (1–0) detections using ALMA and revisit the gas mass and compare gas

masses derived from the three different tracers.

This paper is organized as follows. In Section 2, we present
a summary of the ALMA Band 4 observations targeting the

[C I ] line. In Section 3, we show the [C I ] line detections and
compare the line properties with the previous CO observa
tions. We discuss the derived molecular mass from different

gas tracers in Section 4. Finally, a summary is presented in
Section 5. Throughout this paper, we assume a Λ cold dark
matter cosmology with _H_ 0 =70 km s _[−]_ [1] Mpc _[−]_ [1], Ω m = 0.3,
and Ω Λ = 0 _._ 7. The adopted initial mass function (IMF) is
the Chabrier initial mass function (IMF; Chabrier 2003) in
the mass range of 0.1-100 _M_ _⊙_ .


2. OBSERVATIONS


2.1. _ALMA Band 4 observations_


We used ALMA Band 4 receivers to obtain the red
shifted [C I ] (1–0) emission (ID: ADS/JAO.ALMA
#2015.1.00152.S, PI: Minju Lee). We designed our observations to use two-point positions, which is the same as the
CO (4–3) observations summarized in Paper II, covering a
total of 16 out of 25 parent H _α_ emitters (HAEs). A total of either 38 or 39 antennas were used with the base
line length between 15 m and 3.1 km. For each pointing, on-source time was _≃_ 95 mins to get the line emission. We used four spectral windows (SPWs), two of each
were placed in the upper and the lower sideband, respectively. One SPW was set in the Frequency-Division Mode
(FDM) to detect the redshifted [C I ] (1–0) with a channel
width of 7.82 MHz ( _∼_ 16.6 km s _[−]_ [1] ) covering 1.875 GHz
bandwidth. The remaining three SPWs were observed in the
Time-Division Mode (TDM) with a 2.0-GHz bandwidth at

the 15.6-MHz resolution to cover the dust continuum at 2

mm. J2025+3343 and J2148+0657 were chosen for band
pass calibrators. J2148+0657 and J1751+0939 were used for
flux calibration. A phase calibrator was J2114+2832.
We used `CASA` (McMullin et al. 2007) version 4.7.0 and
5.6.1 for the calibration of visibility data and imaging, respectively. For visibility calibration, we used the pipeline
script provided by the ALMA Regional Center staffs.
Images were produced by `CASA` task, `tclean`, and decon
volved down to 2 _σ_ noise level. The CLEAN masks were
created based on the positions of HAEs taking 1 _[′′]_ -radius circular regions. The synthesized beam is 0 _[′′]_ _._ 42 _×_ 0 _[′′]_ _._ 29 and the

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 3



typical noise level is 0.10 mJy beam _[−]_ [1] around the phase center at 80 km s _[−]_ [1] for natural weighting. We take the velocity
resolution of 80 km s _[−]_ [1] as a default, or otherwise specified.
Tapered images were also created by three different uvtaper parameters of 0 _[′′]_ _._ 3, 0 _[′′]_ _._ 5 and 0 _[′′]_ _._ 9 in the `tclean` task
to check the robustness of the line detections and the presence of extended emissions. The corresponding beam sizes
are 0 _[′′]_ _._ 53 _×_ 0 _[′′]_ _._ 43, 0 _[′′]_ _._ 65 _×_ 0 _[′′]_ _._ 57 and 0 _[′′]_ _._ 97 _×_ 0 _[′′]_ _._ 92 for the
uvtaper values of 0 _[′′]_ _._ 3, 0 _[′′]_ _._ 5 and 0 _[′′]_ _._ 9, respectively. We subtracted the continuum emission on the image domain using
`imcontsub` (fitorder = 0) after we made smaller data cubes
(10 _[′′]_ _×_ 10 _[′′]_ ) centered on the target HAEs. This is to get improved results of continuum subtraction for galaxies not close
to the phase center. We then performed a primary beam correction. Hereafter, we refer to the data cube that is corrected
for the primary beam response and of which the continuum

emission is subtracted.


2.2. _Detection criteria and flux measurements_


We impose the same detection criteria applied in the
CO (4–3) line detection (Paper II) that were found to be robust to identify line detections for known positions. In summary, we regard a galaxy as detected by imposing doublestep criteria. Firstly, the [C I ] line detection candidates are selected if (a) a signal-to-noise (S/N) ratio at the peak position
( _I_ CI _,_ peak ) is equal to or greater than 4.5 ( _S/N_ _I_ CI _,_ peak _≥_ 4 _._ 5).
We then regard these candidates as detected if the peak position spectrum satisfies either of the following criteria : (b) a
peak flux density ( _S_ CI _,_ peak ) _≥_ 3 _._ 5 _σ_ ; (c) at least two continuous channels, including a maximum-peak-flux channel have
fluxes _>_ 2 _._ 5 _σ_, where _σ_ is the average channel noise level,
estimated from the line-free positions.
The noise estimate for the peak line intensity is based on
the calculation after taking into account the channel noise,
integrating channel range following Hainline et al. (2004) assuming the source is unresolved. We also checked the noise
level by bootstrapping from 30 random positions of the map,
which matches the theoretical expectation. The total line flux
is measured by performing 2D gaussian fitting using `imfit`
in CASA for a given aperture.
We check the growth curves in natural and tapered maps
to find the optimal imaging parameters that give the highest
S/Ns and total flux. In summary, for HAE 3 and HAE 16,
we use the 0 _[′′]_ _._ 3-tapered map and a circular aperture size of
1 _[′′]_ _._ 0. For HAE 4, we use the natural-weighted map and a
circular aperture size of 0 _[′′]_ _._ 7 (but see Section 3.1 for a different choice of aperture size for “HAE 4b”). For HAE 8 and
HAE 9, we use the 0 _[′′]_ _._ 5-tapered map and an aperture size of
1 _[′′]_ _._ 0.
For HAE 8, we use 50 km s _[−]_ [1] considering the narrow
width known from the previous CO line detections. For low
S/N galaxies (HAE 4 and HAE 3), we also checked whether



different velocity binnings (50 km s _[−]_ [1] versus 80 km s _[−]_ [1] )
change our results. We confirmed that the results did not
change in terms of the line widths and fluxes within uncertainties between two different velocity binnings.
For [C I ] (1–0) non-detection, we calculate a 3 _σ_ limit for
galaxies by assuming the same line width and aperture sizes
used in the CO (4–3) if it is detected, and in other cases,
we take a full-width half-maximum (FWHM) of 300 km
_−_ 1 for the integrated flux. We note that except for HAE 5,
which was not targeted for the [C I ] (1–0) and CO (4–3)
observations, galaxies with CO (3–2) detection are a subset of the CO (4–3) detected galaxy group, i.e., if CO (3–
2) line is detected, then CO (4–3) is also detected. If a
galaxy is not detected in any of the lines, we use the natural weight image and the aperture size of 0 _[′′]_ _._ 7 for calculating the [C I ] flux limit. The current detection criteria exclude a possible [C I ] detection with the _peak_ S/N = 5.4 for
HAE 7, which was previously detected in CO (4–3), but not
satisfying neither (b) nor (c) in Step 2 for the [C I ] analysis
(the spectra are presented in Appendix A). The 2D Gaussian
best-fit flux (0 _._ 28 _±_ 0 _._ 09) gives _≈_ 10% higher flux than the
3 _σ_ upper limit placed by the noise level, but still within the
uncertainty and it does not impact our later discussion. The
data cubes were also visually checked further for the candidate galaxies without any CO line detections because of the
redshift uncertainty, which is ∆ _z_ _≈_ 0 _._ 03, coming from the
original selection (i.e., narrow-band filter detected).


2.3. _Reanalysis of previous CO and dust measurements_


We reanalyzed the CO (3–2), CO (4–3), and dust data
for unified analyses to reduce the systematic errors coming
from different flux measurement methods. The flux values
in our previous studies were measured in different spatial
and/or spectral resolutions and various methods. Here we
performed the same analyzing procedures applied in the measurement of the [C I ] line. The beamsizes of the CO (4–3),
CO (3–2) and dust are 0 _[′′]_ _._ 53 _×_ 0 _[′′]_ _._ 32, 0 _[′′]_ _._ 89 _×_ 0 _[′′]_ _._ 66, and
0 _[′′]_ _._ 78 _×_ 0 _[′′]_ _._ 68, respectively, for natural weighting. As the
beam size of the CO (4–3) observations is very similar to
that of [C I ] observations, we took the same aperture sizes
and imaging parameters described in Section 2.2 when doing
`imfit` . We used the natural weighting map for CO (3–2) and
for dust continuum, taper parameter of 0 _[′′]_ _._ 5, which gives the
synthesized beam of 0 _[′′]_ _._ 89 _×_ 0 _[′′]_ _._ 82. For the CO (3–2) data
and dust, we used a fixed aperture size of 1 _[′′]_ _._ 0 to measure the
flux values.
The choice of the aperture sizes in flux measurement is
based on our investigation to maximize the S/N. However,
we note that choosing 1 _[′′]_ _._ 0 for all galaxies instead of different aperture sizes does not change our flux estimate. Indeed,
HAE 4 is the only galaxy using different aperture sizes between different lines, we note that [C I ] and CO (4–3) fluxes

4 M INJU M. L EE ET AL .



using the 1 _[′′]_ _._ 0-circular aperture for HAE 4 are consistent
with the 0 _[′′]_ _._ 7 measurement but with low S/N (but see Section 3.1 for further discussion on HAE 4). Since we probe
close transitions between _J_ = 3 and 4 for CO, the difference
in radial distribution might be small. We note, however, that
for non-detection different aperture sizes can give _≈_ 40% (or
_≈_ 0 _._ 14 dex) change in the 3 _σ_ upper limit.
The number of line detection does not change (i.e., seven
galaxies for CO (3–2), eleven galaxies for CO (4–3), and four
galaxies for dust), but the total flux values and signal-to-noise
ratios are updated. For CO (4–3), HAE 3 and HAE 16 fluxes
increased by _≈_ 40 _−_ 50% than Paper II. We also note that the
S/Ns of HAE 1, 2, 7, 12 and 23, which are detected only in
CO (4–3), are lower than the previous measurements that we
decided not to include in the line ratio analysis in Section 3.2
(see their spectra in Appendix A). The CO (3–2) fluxes of
HAE 8 and HAE 4 have increased roughly by a factor of
two than the one in Paper I, where we took a peak flux from
the smoothed maps, instead of fitting Gaussian for all galaxies (see the Appendix for the related discussions on the flux
measurements in Paper I). However, we note that the updated
values are consistent with the values reported in Tadaki et al.
(2019) within uncertainties.
The updated fluxes do not change the main conclusion
made in Paper I that (1) the mean gas fraction of galaxies
with log ( _M_ star _/M_ _⊙_ ) = [10 _._ 6 _,_ 11 _._ 3] is consistent with the
field within the error bars and (2) the depletion time scale (or
star-formation efficiency) decreases (increases) with increasing stellar mass but with an outlier of an AGN-dominated
galaxy (HAE 5). We summarize the flux values in Table 1.
Table 1 supersedes the previous measurements and we will
regard the updated measurements for further analysis.


3. RESULTS


3.1. _Detection of [C_ _I_ _] and line properties compared to CO_


We detect the [C I ] line from five galaxies previously detected in CO (3–2) and CO (4–3) lines, i.e., HAE 3, 4, 8, 9
and 16. Three galaxies, HAE 3, 8, and 9, were detected in
the 1.1 mm continuum data as well. In the left panels of Figure 1, we show the spectra of [C I ], CO (3–2), and CO (4–3)
emissions at the peak position of the [C I ] (1–0) emission for

[CI] detections. The spectra of the [C I ] and CO (4–3) lines
are taken from the 0 _[′′]_ _._ 3-tapered maps and CO (3–2) from the
natural-weighted maps.
We find the line properties (widths and redshifts) of

[C I ] centered at each peak position of the [C I ] and CO (3–2)
with a fixed aperture (1 _[′′]_ _._ 0) size are broadly consistent with
those of CO (3–2), except for HAE 3 and HAE 9 (Figure 1
middle panels). These two galaxies show signatures of mergers in their stellar and/or CO maps (Paper I; Paper II). For
HAE 3, the [C I ] line is narrower (FWHM = 172 _±_ 106 km
s _[−]_ [1] ) than two CO lines (FWHM = 500 km s _[−]_ [1] ) which may



indicate kinematically different origins of the emission lines.
If we integrate the [C I] cube of HAE 3 over the same velocity range defined by two CO lines, the 1D Gaussian fitted flux (0 _._ 15 _±_ 0 _._ 08) is consistent within uncertainties. For
HAE 9, we discussed its kinematic properties in Paper II that
the galaxy is undergoing a gas-rich merger. The red-shifted
component of HAE 9 is not detected in [C I ] (or does not satisfy the detection criteria), which was detected in CO (4–3).
Accordingly, in Table 1, we list additional flux measurements
for HAE 3 and HAE 9 (named HAE 3a and HAE 9a) to refer
to the flux values for which integrating ranges are matched to
those of the CO (3–2) lines. In the later analysis of the gas
measurements, we will use these values.
The peak positions of [C I ] are also consistent within the
positional errors except for HAE 4 if the beam size and the
S/Ns are taken into account (Figure 1 right panels). HAE 4
shows a positional offset of 0 _._ 6 _[′′]_ between H _α_ and CO (3–
2) peak positions (Paper I) and extended H _α_ emission. The
CO (4–3) peak is closer to the H _α_ peak in contrast to the offset from CO (3–2) peak position. The [C I ] line peak is also
offset from the other line peak positions by _≈_ 0 _[′′]_ _._ 5 _−_ 0 _[′′]_ _._ 6
( _≈_ 4-5 kpc). It may indicate different gas excitation conditions within the galaxy as discussed in Paper II. For this
reason, we take another flux measurement for HAE 4. We
list the line fluxes from different positions which give the
highest S/N for individual emission lines (HAE 4), and from
the CO (4–3) peak position (HAE 4b, see Appendix B for its
spectrum). For HAE 4b, we derive the fluxes using a 1 _[′′]_ _._ 0
circular aperture to be consistent with other [C I ] detected
galaxies. Owing to the low S/N at the CO (4–3) position,
we do not derive the flux in the 2D map for HAE 4b using
imfit task in CASA, but by fitting the 1D spectrum with a
single Gaussian. We note that the aperture photometry in the
2D map, using the same circular aperture of 1 _[′′]_ _._ 0, is lower
than or comparable to the 1D Gaussian fit listed in Table 1,
i.e., 0 _._ 13 _±_ 0 _._ 03, 0 _._ 14 _±_ 0 _._ 04, 0 _._ 20 _±_ 0 _._ 05 for [C I ], CO (3–2)
and CO (4–3), respectively. Other galaxies also show similar
signatures in their CO and [C I ] line profiles; the line profiles
taken from the the [C I ] peak position show a varying degree of relative line ratios at each velocity bin (Figure 1 left
panels). Discussing the resolved gas excitation conditions is
beyond the scope of this paper, and this would need more
sensitive and higher angular resolution observations to get
more details. In this paper, we assume that the line emissions
are _globally_ coming from the same galaxy.


3.2. _The L_ _[′]_ [CI](1 _−_ 0) _[–][ L]_ _[′]_ CO(J _−_ J _−_ 1) _[relation]_


We compare the line luminosities between the [C I ] (1–0)
and CO lines. We first fit the literature values compiled in
V20 and _z_ _∼_ 1 galaxies from the ASPECS survey (Boogaard
et al. 2020) as well as the mean values of the SPT sources
from Spilker et al. (2014). The data from V20 includes local

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 5


**Table 1.** Summary of line observations for HAEs associated to 4C23.56 protocluster


ID R.A. Decl. [C I ] beam aperture([CI]) ∆ _v_ ([CI]) integ _._ FWHM [CI](1 _−_ 0) _I_ [CI]10 _I_ CO32 _I_ CO43 _S_ 1 _._ 1mm


J2000 J2000 _′′_ _×_ _′′_ _′′_ km s _[−]_ [1] km s _[−]_ [1] Jy km s _[−]_ [1] Jy km s _[−]_ [1] Jy km s _[−]_ [1] mJy


(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11)


HAE1 _[*]_ 316.81166 23.52921 0.42 _×_ 0.29 0.7 560 ... _<_ 0 _._ 17 _<_ 0 _._ 18 0.34 _±_ 0.13 _<_ 0 _._ 25

HAE2 _[*]_ 316.84074 23.53043 0.42 _×_ 0.29 0.7 400 ... _<_ 0 _._ 14 _<_ 0 _._ 12 0.16 _±_ 0.07 _<_ 0 _._ 36

HAE3 316.83763 23.52055 0.53 _×_ 0.43 1.0 160 172 _±_ 106 0.17 _±_ 0.05 0.43 _±_ 0.12 0.67 _±_ 0.17 0.77 _±_ 0.26

HAE3a _[†]_ 316.83763 23.52055 0.53 _×_ 0.43 1.0 560 172 _±_ 106 0.15 _±_ 0.08 0.43 _±_ 0.12 0.63 _±_ 0.18 0.77 _±_ 0.26

HAE4 316.84013 23.52810 0.42 _×_ 0.29 0.7 480 228 _±_ 130 0.20 _±_ 0.06 0.42 _±_ 0.10 0.19 _±_ 0.06 _<_ 0 _._ 42

HAE4b _[‡]_ 316.84013 23.52810 0.53 _×_ 0.43 1.0 480 292 _±_ 138 0.13 _±_ 0.08 0.17 _±_ 0.07 0.22 _±_ 0.10 _<_ 0 _._ 42

HAE5 316.82069 23.50846 ... ... ... ... ... 0.14 _±_ 0.04 ... _<_ 0 _._ 29

HAE6 316.83955 23.52209 0.42 _×_ 0.29 0.7 300 ... _<_ 0 _._ 09 _<_ 0 _._ 14 _<_ 0 _._ 11 _<_ 0 _._ 31

HAE7 _[*]_ 316.81468 23.52707 0.53 _×_ 0.43 1.0 1520 ... _<_ 0 _._ 25 _<_ 0 _._ 23 0.43 _±_ 0.12 _<_ 0 _._ 51

HAE8 316.81638 23.52431 0.65 _×_ 0.57 1.0 150 154 _±_ 62 0.24 _±_ 0.04 0.55 _±_ 0.09 0.49 _±_ 0.06 0.90 _±_ 0.19

HAE9 316.84409 23.52871 0.65 _×_ 0.57 1.0 560 410 _±_ 171 0.38 _±_ 0.09 0.64 _±_ 0.10 0.61 _±_ 0.12 1.52 _±_ 0.29

HAE9a _[†]_ 316.84409 23.52871 0.65 _×_ 0.57 1.0 800 410 _±_ 171 0.55 _±_ 0.14 0.64 _±_ 0.10 1.23 _±_ 0.23 1.52 _±_ 0.29

HAE10 316.81543 23.52003 0.53 _×_ 0.43 1.0 480 ... _<_ 0 _._ 17 0.53 _±_ 0.12 0.26 _±_ 0.10 0.50 _±_ 0.16

HAE11 316.79338 23.51373 ... ... ... ... ... ..... ...

HAE12 _[*]_ 316.81222 23.52988 0.42 _×_ 0.29 0.7 240 ... _<_ 0 _._ 13 _<_ 0 _._ 12 0.19 _±_ 0.07 _<_ 0 _._ 25

HAE13 316.84092 23.52826 0.42 _×_ 0.29 0.7 300 ... _<_ 0 _._ 09 _<_ 0 _._ 10 _<_ 0 _._ 11 _<_ 0 _._ 32

HAE14 316.83241 23.51417 ... 0.7 300 ... ... _<_ 0 _._ 11 ... _<_ 1 _._ 05

HAE15 316.83315 23.51896 ... 0.7 300 ... ... _<_ 0 _._ 10 ... ...

HAE16 316.81102 23.52107 0.53 _×_ 0.43 1.0 800 453 _±_ 201 0.33 _±_ 0.07 0.57 _±_ 0.14 0.82 _±_ 0.12 _<_ 0 _._ 94

HAE17 316.82340 23.53068 ... ... 300 ... ... _<_ 0 _._ 20 ... ...

HAE18 316.84011 23.53366 ... ... 300 ... ... _<_ 0 _._ 14 ... ...

HAE19 316.84247 23.52944 0.42 _×_ 0.29 0.7 300 ... _<_ 0 _._ 11 _<_ 0 _._ 10 _<_ 0 _._ 13 _<_ 0 _._ 27

HAE20 316.81228 23.52238 0.42 _×_ 0.29 0.7 300 ... _<_ 0 _._ 08 _<_ 0 _._ 13 _<_ 0 _._ 10 ...

HAE21 316.81175 23.52857 0.42 _×_ 0.29 0.7 300 ... _<_ 0 _._ 11 _<_ 0 _._ 13 _<_ 0 _._ 13 _<_ 0 _._ 26

HAE22 316.82441 23.52909 ... ... 300 ... ... _<_ 0 _._ 20 ... ...

HAE23 _[*]_ 316.81147 23.52184 0.42 _×_ 0.29 0.7 800 ... _<_ 0 _._ 13 _<_ 0 _._ 23 0.27 _±_ 0.09 ...

HAE24 316.84344 23.54678 ... ... ... ... ... ..... ...

HAE25 316.80971 23.53572 ... ... ... ... ... ..... ...


N OTE —

_†_ : flux values obtained by integrating the velocity range used in CO (3–2) line (column 6)

_‡_ : flux values at a fixed position to the CO (4–3) peak, which is the closest (∆ _r_ = 0 _[′′]_ _._ 15) to the original H _α_ emission.
_∗_ : HAE 1, 2, 7, 12, and 23 satisfy our detection criteria in CO (4–3) but we note that they have lower significance levels of the line detection in comparison with
other secure detections those have other line and/or dust detections (see Appendix A for their spectra). Therefore, we suggest readers use these values with caution.
Colums: (1) Source ID. For sources without a dagger mark( _†_ ) or a double dagger mark ( _‡_ ) behind the ID, we list fluxes integrated over the velocity range with beams
and aperture sizes that maximizes the S/N of the peak position flux and total flux, centered at the peak position of each line; (2) Right Ascension (J2000) of H _α_
position from Subaru/MOIRCS observations (Tanaka et al. 2011; I. Tanaka in preparation); (3) Declination (J2000) of H _α_ position; (4) Synthesized beam of the

[C I ] images to measure the flux; (5) Aperture size to measure the [C I ] flux or the 3 _σ_ upper limit; (6) Velocity integrating range to measure the [C I ] flux. If the

[C I ] line is non-detection but other lines (i.e., CO (4–3) or CO (3–2)) are detected, we used the integrating range referring to their integrating ranges that is listed in
this column. If no other lines are detected, we set the integrating range fixed as 300 km s _[−]_ [1] for 3 _σ_ upper limits; (7) Full-width half-maximum of the [C I ] line fitted
with a single 1D Gaussian profile; (8) [C I ] (1–0) flux measured using CASA imfit (but 1D Gaussian fit for HAE 4b) with the aperture size listed in Col. (5) and
(6). Upper limits are 3 _σ_ ; (9) CO (3–2) flux using CASA imfit (but 1D Gaussian fit for HAE 4b) with an aperture of 1 _[′′]_ _._ 0. Upper limits are 3 _σ_ using the value
listed in Col (5) and (6); (10) CO (4–3) flux using CASA imfit (but 1D Gaussian fit for HAE 4b) with the same aperture size listed in Col. 5. Upper limits are
3 _σ_ using the value listed in Col (5) and (6); (11) 1.1 mm dust continuum flux using an aperture of 1 _[′′]_ _._ 0. All measurements presented here supersede the previous
measurement reported in Paper I and Paper II.

6 M INJU M. L EE ET AL .


**Figure 1.** Left: [C I ] (1–0) line spectrum for detections at the [C I ] peak. Color-filled regions indicate the velocity range to integrate to derive
the line flux for [C I ] (1–0), which gives the largest S/N. For comparison, CO (4–3) and CO (3–2) spectrum at the [C I ] peak position are shown
with a base level shift of 2.0 and 1.0, respectively. The velocity resolution is 80 km s _[−]_ [1] except for HAE 8. For HAE 8, the resolution is 50
km s _[−]_ [1] . Middle: [C I ] (1–0) line spectrum using a 1 _[′′]_ _._ 0 aperture centered at the peak. CO (3–2) spectrum using the same aperture size at
the CO (3–2) peak is plotted in black thinner line. Right: the velocity-integrated map of [C I ] (1–0). The size of the panel is 3 _[′′]_ _×_ 3 _[′′]_ . Cross
symbols indicate the peak positions of CO (4–3) (black), CO (3–2) (red), and H _α_ (white) emissions. The contour levels are starting from 4 _σ_ in
steps of 1 _σ_ . Dashed contours are also plotted for _−_ 4 _σ_ indicating no 4- _σ_ peak around the galaxies. The synthesized beam (0 _[′′]_ _._ 53 _×_ 0 _[′′]_ _._ 43) is
shown as an filled-ellipse on the bottom left of each panel.

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 7


**Table 2.** _L_ _[′]_ CO [and] _[ L]_ _[′]_ CI [relation fit]


log _L_ _[′]_ CO43 [=] _[ a][ ×]_ [ (log] _[ L]_ _[′]_ CI10 _[−]_ [10) +] _[ b]_ log _L_ _[′]_ CO43 [=] _[ a]_ [fixed] _[ ×]_ [ (log] _[ L]_ _[′]_ CI10 _[−]_ [10) +] _[ b]_


References (1)+(2)+(3) high- _z_ MS gals in (1), and (2) protocluster (this work) protocluster (this work)


a 1 _._ 04 _±_ 0 _._ 02 1 _._ 32 _±_ 0 _._ 22 1 _._ 16 _±_ 0 _._ 23 fixed to 1 _._ 04 fixed to 1 _._ 32

b 10 _._ 32 _±_ 0 _._ 02 10 _._ 47 _±_ 0 _._ 12 10 _._ 46 _±_ 0 _._ 08 10 _._ 42 _±_ 0 _._ 03 10 _._ 51 _±_ 0 _._ 03


log _L_ _[′]_ CO32 [=] _[ a][ ×]_ [ (log] _[ L]_ _[′]_ CI10 _[−]_ [10) +] _[ b]_ log _L_ _[′]_ CO32 [=] _[ a]_ [fixed] _[ ×]_ [ (log] _[ L]_ _[′]_ CI10 _[−]_ [10) +] _[ b]_
References (1)+(3) _[∗]_ protocluster (this work) protocluster (this work)

a 1 _._ 32 _±_ 0 _._ 10 0 _._ 43 _±_ 0 _._ 20 fixed to 1 _._ 32

b 10 _._ 36 _±_ 0 _._ 05 10 _._ 39 _±_ 0 _._ 08 10 _._ 70 _±_ 0 _._ 08


N OTE — References (1) = V20, (2) = Boogaard et al. (2020), (3) = Spilker et al. (2014)
_∗_ : We note that for this fitting, the sample is largely dominated by high- _z_ DSFGs and only one is a main-sequence galaxy at _z_ = 2 _._ 2 from
Popping et al. (2017) that observed a compact star-forming galaxy.
The fit for the protocluster is using six secure galaxies at least two line detections (i.e., HAE 3a, 4b, 8, 9a, 10 and 16). If we include other

[C I ] 3 _σ_ upper limits of the remaining galaxies for CO (4–3) (see Section 2.3 and Table 1 note regarding single line detections), the best-fit
parameters change slightly but still consistent within the uncertainties; slope for CO (4–3) becomes steeper with higher normalization, i.e.,
_a_ = 1 _._ 40 _±_ 0 _._ 26, _b_ = 10 _._ 55 _±_ 0 _._ 13; if we fix the slope, _b_ = 10 _._ 39 _±_ 0 _._ 04 and 10 _._ 52 _±_ 0 _._ 04 for _a_ = 1 _._ 04 and 1 _._ 32, respectively.



IR-luminous galaxies (LIRGs), high- _z_ main-sequence galaxies, where most of the samples are at _z_ _∼_ 1 except for one
at _z_ = 2 _._ 2, and high- _z_ dusty star-forming galaxies (DSFGs)
and QSOs. We note that the local galaxies compiled in V20
are representative of star-bursting population rather than typical spiral galaxies. The mean deviation of these local galaxies from the main-sequence defined by Speagle et al. (2014)
is _⟨_ log ∆MS _⟩_ = 1 _._ 3. Hereafter, we define “starburst” galaxies to be galaxies well-above the main-sequence by 3 _σ_ from
the main-sequence (i.e., log ∆MS _>_ 0 _._ 6).
We fit the data using the orthogonal distance regression to
take into account uncertainties in both axes. For fitting, we
have included the non-detections using the 3- _σ_ upper limits
if another line is detected, and the uncertainties of all data
points are set to the 1- _σ_ noise level. We use a linear model
of log _L_ _[′]_ CO43 _,_ or CO32 [=] _[ a][ ×]_ [ (log] _[ L]_ _[′]_ CI10 _[−]_ [10) +] _[ b]_ [.] [We fit for]
_L_ _[′]_ CO43 _[−][L]_ _[′]_ CI10 [relation by excluding star-bursting population]
of local galaxies and high- _z_ DSFGs (i.e., _z_ _≃_ 1 _−_ 2 mainsequence galaxies only) as well. For _L_ _[′]_ CO32 _[−]_ _[L]_ _[′]_ CI10 [relation,]
the data sets become sparse and most of the galaxies available
are high- _z_ DSFGs except for one from Popping et al. (2017),
which is a compact star-forming galaxy (cSFG) at _z_ = 2 _._ 2.
The best-fit slope values indicate super-linear relations between _L_ _[′]_ CO [and] _[L]_ _[′]_ [CI](1 _−_ 0) [.] [A] [summary] [of] [the] [best-fit] [pa-]
rameters is listed in Table 2. Figure 2 shows the best-fit
relations (red dashed – all galaxies in the literature – and
blue solid lines – high- _z_ main-sequence galaxies –). We also
note that the residual variance is higher for the CO (3–2)–

[C I] fit, partially owing to the limited data points. Simply by taking the best-fit models listed in the second column in Table 2, i.e., (1)+(2)+(3) fit and (1)+(3) fit for
_L_ _[′]_ CO43 _[−][L]_ _[′]_ CI10 [and] _[ L]_ _[′]_ CO32 _[−][L]_ _[′]_ CI10 [, respectively), the bright-]



ness temperature (luminosity) ratio between CO (4–3) and
CO (3–2) ( _R_ 43 = _L_ _[′]_ CO43 _[/L]_ _[′]_ CO32 [) becomes higher (smaller)]
for smaller (higher) _L_ _[′]_ [CI](1 _−_ 0) [luminosity.]
We perform the same exercise for the protocluster galaxies
only while keeping in mind that the dynamic range is much
narrower i.e., less than an order of magnitude in luminosities.
We fit using six galaxies with secure detections (i.e., at least
two lines of detection; HAE 3a, 4b, 8, 9a, 10 and 16). The
best-fit parameters are summarized in Table 2 using the same
fitting model but with two options of a variable slope and a
fixed slope.
For log _L_ _[′]_ CO(4 _−_ 3) _[−]_ [log] _[ L]_ _[′]_ [CI](1 _−_ 0) [relation,] [the] [slope] [is]
super-linear for the protocluster members, consistent with
other best-fit using the literature values. The super-linear
relation between log _L_ _[′]_ CO(4 _−_ 3) [and] [log] _[ L]_ _[′]_ [CI](1 _−_ 0) [may] [indi-]
cate that CO (4–3) emission is not tracing the total gas mass,
but either dense gas that directly forms stars and, hence starformation, while the [C I ] emission is tracing the total gas
mass, mimicking the global Kennicutt-Schmidt law (Schmidt
1959; Kennicutt 1998). Also, it may be worth noting that
there is a hint of a steeper super-linear slope for high- _z_ galaxies than our protocluster galaxies. Concerning this, there are
a few studies in local galaxies (e.g., Juneau et al. 2009; Bayet
et al. 2009) that reported a super-linear correlation between
far-infrared luminosity and low- _J_ CO transitions ( _J_ _<_ 3)
spanning a wide IR luminosity range. Some local galaxy surveys reported a linear relation instead (e.g., Gao & Solomon
2004; Greve et al. 2014) for _L_ _F IR_ _>_ 10 [11] _L_ _⊙_ galaxies. The
difference is often explained as the different dense gas fractions (i.e, constantly higher dense gas fraction for galaxies
with high IR luminosity; e.g., Gao & Solomon 2004; Wu
et al. 2005; Greve et al. 2014). Greve et al. (2014) discussed

**Table 3.** Derived gas mass based on [C I ], CO and
dust


ID _M_ mol _,_ CI _M_ mol _,_ CO _M_ mol _,_ RJ


_×_ 10 [10] _M_ _⊙_ _×_ 10 [10] _M_ _⊙_ _×_ 10 [10] _M_ _⊙_


HAE3a 5.5 _±_ 3.0 11.4 _±_ 3.2 8.0 _±_ 2.7

HAE4 7.4 _±_ 2.2 11.2 _±_ 2.7 _<_ 4.4

HAE4b 4.8 _±_ 3.0 4.5 _±_ 1.9 _<_ 4.4

HAE8 8.9 _±_ 1.5 14.6 _±_ 2.4 9.4 _±_ 2.0

HAE9a 20.3 _±_ 5.2 16.9 _±_ 2.6 15.9 _±_ 3.0

HAE10 _<_ 6.3 14.1 _±_ 3.2 5.2 _±_ 1.7

HAE16 12.2 _±_ 2.6 15.1 _±_ 3.7 _<_ 9.8



**Figure** **2.** The relations between [C I ] luminosity and CO (4–3)
luminosity (top) and between [C I ] luminosity and CO (3–2) luminosity (bottom). Protocluster galaxies are shown as squares, and
smaller squares (HAE 4 and 9) are excluded in the gas mass calibration in Section 4.1 (see the text and Table 1 caption for the description of the galaxy name tags). We also plot other data points
from V20 (circles), Spilker et al. (2014) (diamond), Boogaard et al.
(2020) (crosses), and Popping et al. (2017) (X-cross). In each panel,
the 3 _σ_ upper limits for [CI] non-detection with CO line detections
are also plotted; arrows for the protocluster members and left faced
triangles for others. Red dashed and blue solid lines are the best-fit
using the data points excluding the protocluster galaxies (see Table 2 and the main text). Using six secure detections (HAE 3a, 4b,
8, 9a, 10 and 16) with at least two line detections, dash-dotted and
dotted lines are the best-fit depending on the model assumptions.
Shaded regions indicate 1 _σ_ uncertainties of the best-fit parameters
for varying slopes.


further for the _L_ FIR -low- _J_ CO relation that a linear slope



or higher normalization factor may be physically related to
the existence of dense gas, which is limited by the Eddington
limit (see also Andrews & Thompson 2011). If we can apply a similar interpretation, a hint of a shallower slope (close
to a linear relation) and a higher normalization factor in protocluster galaxies than other high- _z_ main-sequence galaxies
might hint at the existence of more denser gas in protocluster
galaxies than high- _z_ field main-sequence galaxies.
There is a hint of a systematically different relation in the
protocluster for the _L_ _[′]_ CO(3 _−_ 2) _[−]_ _[L]_ _[′]_ [CI](1 _−_ 0) [relation] [(at] [1] _[σ]_ [).]
Considering that the fit for the literature values is biased towards high- _z_ DSFGs and the fit for protocluster galaxies
with a varying slope shows a sub-linear relation, our previous simple interpretation of _L_ _[′]_ CO _[−]_ _[L]_ _[′]_ [CI](1 _−_ 0) [as] [an] [ana-]
log of _L_ FIR _−_ _L_ _[′]_ CO [(or] [the] [K-S] [law)] [might] [not] [be] [always]
viable. Or, the CO excitation condition might be different
from high- _z_ DSFGs while CO (3–2) line still traces dense
gas. Regarding this, it may be worth noting that the line ratio
( _L_ _[′]_ _−_ _−_ [of] [cSFG] [from] [Popping] [et] [al.] [(][2017][)]
CO(3 2) _[/L]_ _[′]_ [CI](1 0) [)]
is comparable to the protocluster galaxies. In any case, it is
a surprising result to see such a large difference in these two
close transitions but in a (similarly) narrow dynamic range.
The current data set is not sufficient to robustly conclude
because of the the low number statistics and unknown systematic biases for currently available data sets in different
environments. Depending on our model selection for the
fit (fixed slope or not), the relation between _L_ _[′]_ _CO_ 43 _[/L]_ _[′]_ _CO_ 32
as a function of _L_ _[′]_ CI10 [also] [varies] [(negative] [or] [positive),]
which further denotes the current limitation. Therefore, we
defer further discussions on the existence of systematically
_L_ _[′]_ CO _[−]_ _[L]_ _[′]_ [CI](1 _−_ 0) [relations in different environments to a fu-]
ture work. We will have to wait for more data from future

surveys for fairer comparison.


3.3. _Molecular gas mass from [C_ _I_ _], CO and dust_


The relation between CO and [C I ] demonstrates that

[C I ] traces the global gas mass well. We derive gas mass

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 9



**Figure** **3.** Comparison between the derived molecular gas mass
from [C I ], CO and dust. Squares show the measurements from
this work using 1.1 mm (brown) and CO (3–2) (turquoise). Upper
limits (3 _σ_ ) are plotted as triangles. We compare our results with
_z_ _∼_ 1 galaxies on the main-sequence and local galaxies compiled
in V20, where both CO (2–1) and [C I ] fluxes are available. For a
comparison of dust-based measurements, we plot data points from
Bourne et al. (2019) using the 1.2mm detections. The dashed line is
to guide 1:1 relation.


from [C I ], CO and dust to investigate whether the general
assumptions are valid to protocluster galaxies.
Following Papadopoulos et al. (2004), we estimate the total
molecular gas mass from [C I ] as



_M_ mol [[CI]] = 4 _πµm_ H 2
_M_ _⊙_ _h c A_ 10 _X_ CI _Q_ 10



_d_ 2L
� 1 + _z_



_S_ [CI] _[′]_ [∆] _[V]_ (1)
�



local galaxies without AGNs, based on the comparison with
low _J_ CO-based gas measurements, they have higher abundance ratio of log ( _X_ CI ) = _−_ 4 _._ 2 _±_ 0 _._ 2 and comparable to
high- _z_ DSFGs ([-3.9, -4.2], Walter et al. 2011; Danielson
et al. 2011; Alaghband-Zadeh et al. 2013; Valentino et al.
2018). Here, we adopt the mean value of log( _X_ CI ) = _−_ 4 _._ 8
found in Valentino et al. (2018) that studied main-sequence
galaxies at _z_ _∼_ 1.
For CO (3–2) and dust, we use the same recipe adopted
in Paper I. In brief, we take a line luminosity ratio between
CO (3–2) and CO (1–0) ( _R_ 13 = 1.9), a similar value measured or used in Dannerbauer et al. (2009), and Tacconi et al.
(2018) for _z_ = 1 _−_ 3 main-sequence galaxies, but see e.g.,
Bolatto et al. (2015); Riechers et al. (2020); Boogaard et al.
(2020) for a lower value, or a slightly higher average value reported in Daddi et al. (2015). We use the Milky Way (MW)like CO-to-H 2 conversion factor ( _α_ CO = 4 _._ 36 M _⊙_ (K km
s _[−]_ [1] pc [2] ) _[−]_ [1] ; e.g., Bolatto et al. 2013; Genzel et al. 2015).
Here, we don’t correct for the metallicity-dependence of the
_α_ CO conversion factor. For the underlying stellar mass range
that we observe (log ( _M_ star _/M_ _⊙_ ) _>_ 10 _._ 5), the metallicitydependent _α_ CO factor only increases the gas estimate the
up to 0.07 dex for the lowest mass galaxies (HAE 16 and
HAE 10) and does not affect higher mass regime. For dustbased measurements, we adopt the calibration described in
Scoville et al. (2016). The details of the calculations are presented in Paper I.
Figure 3 compares the molecular gas masses derived from
three different tracers, and Table 3 summarizes the derived
values. The gas mass derived from CO is different by -0.08
dex up to 0.35 dex compared to the [C I ] -based gas mass and
0.14 dex higher on average. Meanwhile, the dust-based measurements are lower than the [C I ] -based mass by 0.02 dex
on average, and the differences range between -0.11 dex and
0.16 dex. The mean values of the difference compared to the

[C I ] -based measurement are shown as the arrows along the
vertical line of the top-left panel of Figure 4. In summary,
three gas tracers are broadly in good agreement for the inferred molecular masses within _≈_ 0.3 dex, but CO-based gas
measurements give _≈_ 40% (0.14 dex) higher value than other

gas tracers on average.
For comparison, we also plot the local and high- _z_ field

[C I ] studies in Figure 3. The data points are taken from V20
and Bourne et al. (2019). V20 collected local galaxy and
high- _z_ [C I ] (1–0) studies. From their catalogs, we take the
_z_ _∼_ 1 main-sequence measurements and local galaxies for
which CO (2–1) measurements are available. For the _z_ _∼_ 1
galaxies, we assumed _R_ 12 = 1 _._ 2 and the same _α_ CO and _X_ CI
with protocluster galaxies given that they are on the mainsequence. For local galaxies with CO (2–1) we used the different _α_ CO = 0 _._ 8 and log ( _X_ CI ) = _−_ 4 _._ 2 given that they
are on average above the main-sequence ( _⟨_ log ∆MS _⟩_ =1.3).



where _µ_ = 1 _._ 36 accounts for the mass of helium and _m_ H 2 is
the molecular mass of H 2 in _M_ _⊙_ . For the [C I ] (1–0) transition, the Einstein coefficient A 10 is 7 _._ 93 _×_ 10 _[−]_ [8] s _[−]_ [1] and the
excitation factor _Q_ 10 is determined by the gas density and
temperature. Without measurements of both [C I ] (1–0) and

[C I ] (2–1), we cannot measure _Q_ 10 . Here, we adopt a moderate value of _Q_ 10 = 0 _._ 35 for typical conditions of kinematic
temperature 20 _<_ _T_ kin _<_ 40 K and density 300 _<_ _n_ _<_ 10 [4]

cm _[−]_ [3] based on Papadopoulos & Geach (2012) and Jiao et al.
(2017). _S_ [CI] _[′]_ [∆] _[V]_ [is] [the] [measured] [[C] [I] [] flux] [in] [Jy] [km] [s] _[−]_ [1] [.]
The remainders are luminosity distance _d_ _L_, speed of light _c_,
and Planck constant in SI unit. To convert the [C I ] mass into
the H 2 mass, we need to assume _X_ CI .
Observational constraints of the log ( _X_ CI ) for the Milky
Way are in a range of [-5.7, -4.7] (Frerking et al. 1989) and
the typically assumed value is -4.5 (Weiß et al. 2003). For

10 M INJU M. L EE ET AL .



From Bourne et al. (2019), we compare the dust-based measurements and [C I ] . From the Table 2 in Bourne et al.
(2019), we used the flux values obtained from larger aperture
sizes for Galaxy 1 and 2. In general, they are well-matched

with each other.


4. DISCUSSION


4.1. _Self-consistent calibration from three tracers_


The general key assumptions for deriving gas mass from
different tracers are the following. In the dust-based calibration of Scoville et al. (2016), the mass-weighted dust temperature is fixed to _T_ d = 25 K and the dust-to-gas mass ratio is implicitly fixed. In the CO-based calibration, we need
to assume the _α_ CO and CO gas excitation condition. For
the [C I ] -based calibration, we need to assume the _X_ CI
abundance ratio (or [C I ] -conversion factor). The excitation
temperature may matter, especially for the higher transition

[C I ] (2–1) but has less impact for [C I ] (1–0) (Weiß et al.
2005). The value of _X_ CI is not constrained observationally
in high-z galaxies. In the following, we discuss the possible changes of the parameters ( _T_ d, gas-to-dust mass ratio,
_α_ CO _× R_ 13 and _X_ CI ) to get self-consistent gas mass from
different tracers focusing on non-detection case.
If the dust continuum is non-detection (i.e., HAE 4 and
HAE 16), it may be attributed to a high dust temperature
and/or intrinsically low dust mass (at fixed _T_ d ). For a case of
high dust temperature, the dust SED would shift to a shorter
wavelength hampering the detection at a given sensitivity. It
would imply the dust-based gas mass to an even lower value
if the mass-weighted temperature is also high enforcing other
gas measurements also to be lowered. Alternatively, if the
dust mass intrinsically is low, this would require higher gasto-dust mass ratio to match other gas measurements. The
dust-to-gas mass ratio is closely connected to the metallicity (e.g., R´emy-Ruyer et al. 2014). Considering the massmetallicity relation and the stellar mass of the galaxies, e.g.,
log ( _M_ star _/M_ _⊙_ ) _≈_ 11 _._ 3 (HAE4) and _≈_ 10 _._ 6 (HAE16), the
scatter of the gas-to-dust ratio at fixed metallicity ( _∼_ 0 _._ 37
dex) could allow such variation. Therefore, we can reasonably choose the 3 _σ_ upper limit as face value for the following

discussion.

Firstly, we consider whether the mild differences are depending on galaxy parameters, especially for the CO-based
measurements, which show systematically higher value than
the [C I ] -based gas mass. Figure 4 compares the difference between the molecular gas masss derived from three
different tracers as a function of stellar mass ( _M_ star ), deviation from the main-sequence (sSFR/sSFR(MS)), gas-tostellar mass ratio ( _µ_ gas = _M_ gas _/M_ star ) and gas depletion
time scale ( _τ_ depl _._ = _M_ gas _/_ SFR) where the latter two are
measured using the [C I ] -based gas measurements. We do
not find a statistically meaningful correlation with galactic



parameters and the gas mass discrepancies. For example,
we cannot reject the null hypothesis that depletion time scale
and the gas mass ratio of CO-based and [C I ] -based measurements, which is a proxy for the overestimated amount
of _α_ CO _× R_ 13 at fixed _X_ CI, are not correlated (i.e., Spearman’s Rank coefficient of = -0.37 with a _p_ -value of 0.47,
but note that if HAE 4b is excluded, the strength of the correlation becomes stronger, -0.90 with a moderate _p_ -value
of 0.04.) Given the small number statistics, we conclude
that there is no clear dependency on the stellar mass (for
log _M_ star _/M_ _⊙_ = [10 _._ 5 _,_ 11 _._ 3]), deviation from the mainsequence (for log ∆MS = [ _−_ 0 _._ 1 _,_ 0 _._ 2]), gas-to-stellar mass
ratio (for log _µ_ gas = [ _−_ 0 _._ 6 _,_ 0 _._ 5]) and depletion time scale
(for log( _τ_ depl _._ /Myr) = [2 _._ 1 _,_ 3 _._ 3]), and the differences are
coming from galaxy-to-galaxy variations creating a scatter.
Detailed investigations for the gas mass cross-calibration
for individual galaxies are presented in Appendix C. We
briefly summarize here the results as follows: (1) the CO (4–
3)-to-[C I](1–0) luminosity ratio of two galaxies (HAE 3a
and HAE 16) suggests the existence of dense gas that
may resemble the ISM properties of DSFGs (see also Section 3.2); (2) the non-detection of [C I](1–0) in HAE 10,
the current constraints on mass-weighted dust temperature
and log ( _X_ CI ) suggest that it is more likely that the assumed
_α_ CO _× R_ 13 would be lower than what is assumed. We note
all of these galaxies are all on the main-sequence defined by
Speagle et al. (2014) (i.e., log ∆MS _≤±_ 0 _._ 2).
Overall, there is a hint that the assumed _α_ CO _× R_ 13 needs
to be lowered for HAE 3, 10, and 16 (thus reducing the CObased gas mass), though it is not conclusive for the remaining
galaxies. If the protocluster galaxies share similar properties,
it is more reasonable to lower the CO-based gas mass (thus
reducing the _α_ CO _× R_ 13 ) to match with dust and [C I ] based
gas mass. We finally note that the gas mass cross calibrations
do not require more than a factor of _>_ 0 _._ 6 dex change that
would characterize the protocluster galaxies well above the
main-sequence where the assumptions of _α_ CO _×R_ 13 and _X_ CI

are different.


4.2. _Gas depletion time scale compared to field galaxies_


In the previous section, we showed that the [C I ] line is a
reliable gas tracer of protocluster galaxies. The same calibration of log( _X_ CI ) = _−_ 4 _._ 8 applied for the field main-sequence
galaxies can be used for these galaxies. By investigating

[C I ] -based gas mass, we gained one additional data point
compared to 1.1 mm dust and more robust gas measurement
compared to CO. In this section, we revisit how gas scaling
relation (i.e., gas depletion time scale determined by redshift,
stellar mass, and deviation from the main sequence) differs
from field galaxies based on the [C I ] observations.
Figure 5 shows the gas depletion time scale of the protocluster galaxies normalized by the (field) gas scaling relation

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 11


**Figure** **4.** The gas mass comparison from CO (3–2), dust and [C I ] (1–0) emissions. In the vertical axes, we plot the CO- and dust- based
gas mass divided by [C I ] -based mass. In the horizontal axes, we plot stellar mass (top left), deviation from the main-sequence (top right),
molecular gas-to-stellar mass ratio (bottom left) and depletion time scale (bottom right). The mean values of the galaxy properties are marked
as dark blue arrows. The arrows plotted along the vertical axis of the top left panel is the average deviation of dust- based (turquiose, -0.02 dex)
and CO-based (pink, +0.14 dex) from [C I ] - based including the upper limits.



determined in Scoville et al. (2017), Tacconi et al. (2018)
and Liu et al. (2019) at given stellar mass, redshift and deviation from the main sequence. We plot for the [C I ] nondetections as well for those with CO (4–3) line detections for
galaxies with log _M_ star _/M_ _⊙_ _>_ 9 _._ 5, where the stellar mass
constraint is more reliable than the lower mass regime. For
non-detections, we assume the [C I ] line width the same as
the CO (4–3) width (the sixth column of Table 1) to get the
3 _σ_ upper limit of the depletion time scale. Other [C I ] -based
data points in circles are _z_ _∼_ 1 main sequence galaxies taken
from Bourne et al. (2019) and V20.



Compared to high- _z_ ( _z_ _∼_ 1) field main-sequence galaxies, we find a trend that the depletion time scale for mainsequence protocluster galaxies steeply decreases with stellar
mass. In comparison with field scaling relation, a stronger
anti-correlation is found between depletion time scale normalized by three different scaling relations and stellar mass
in protocluster galaxies. We find negative Spearman coefficient values ( _p_ -value) of -0.81 (0.008, Scoville et al. 2017),
-0.68 (0.04, Tacconi et al. 2018), -0.53 (0.14, Liu et al. 2019),
when the 3 _σ_ upper limits are all taken into account. We also
note that the correlation coefficient is -0.9 with p-value of
0.04 if only the secure detections are considered. As control

12 M INJU M. L EE ET AL .


**Figure 5.** Gas depletion time scale for the protocluster galaxies as a function of stellar mass normalized by field scaling relation (depletion time
scale) from Scoville et al. (2017) (left), Tacconi et al. (2018) (middle) and Liu et al. (2019) (right). In addition to five [C I ] detections (squares),
non-detections for galaxies above log ( _M_ star _/M_ _⊙_ ) _>_ 9 _._ 5 are also shown as up-side-down triangles. Filled circles are other [C I ] -based data
points for _z_ _∼_ 1 main-sequence for a reference of field galaxies from Bourne et al. (2019) and V20.



samples, field galaxies from Bourne et al. (2019), and V20
show less compelling evidence of such anti-correlation, i.e.,
Spearman coefficient ( _p_ -value) = -0.35 (0.06, Scoville et al.
2017), -0.20 (0.30, Tacconi et al. 2018) and 0.23 (0.22, Liu
et al. 2019). The gas scaling relation in Liu et al. (2019) has
the strongest stellar-mass dependency compared to the other
two studies, which is why we find less significant signature
of anti-correlation when normalized by Liu et al. (2019) in
the protocluster members and field galaxies, if any.
With the [C I ] line detections, we reconfirm the trend seen
in Paper I and Tadaki et al. (2019) that used CO/dust and CO
only, respectively, though the absolute vertical scale would
be slightly different due to the different flux values. Overall,
we find a signature of stronger anti-correlation between the
stellar mass and the gas depletion time scale normalized by
field scaling relation: the more the galaxy becomes massive,
the faster it consumes or removes gas, though we caution
that the number statistics and potential selection effects are
remaining concerns.
What kind of physical mechanisms can derive this trend?
In Paper II, we discussed that the larger CO (4–3) line widths
for protocluster galaxies could arise from unresolved gas-rich
mergers or smaller sizes. These are not necessarily exclusive that mergers can also make galaxies smaller. There are
still other possible mechanisms to make the galaxy smaller,
for example, compaction through disk-instability (e.g., Bournaud et al. 2008; Genzel et al. 2008; Genel et al. 2012;
Agertz et al. 2009; Ceverino et al. 2010; Zolotov et al. 2015;
Tacchella et al. 2016; Barro et al. 2016) and gas stripping
(e.g., Gunn & Gott 1972; Haynes et al. 1984; Poggianti et al.
2017). Gas stripping in molecular phase remains inconclusive (e.g., Stark et al. 1986; Kenney & Young 1989; Boselli
et al. 1997), but there is a growing body of evidence that
more tightly bound molecular gas can even be stripped or



disturbed (e.g., Vollmer et al. 2008; Fumagalli et al. 2009;
Boselli et al. 2014; Zabel et al. 2019). We note also that
the conventional picture of gas stripping is more likely to
happen in low mass galaxies in massive clusters, but some
group members also show such signature for neutral atomic
gas (e.g., Verdes-Montenegro et al. 2001; Rasmussen et al.
2006; Hess & Wilcots 2013). Considering these, the molecular gas stripping in massive galaxies in the group-like environments (i.e., protoclusters) may be less efficient, but it
remains one of the possibilities. At the same time, this protocluster also shows a hint that more massive galaxies tend to
reside in denser regions (Paper I) that other environmentally
driven mechanisms (gas strangulation; Larson et al. 1980;
Peng et al. 2015) might play an additional role for the protocluster members, for earlier quenching. All these mechanisms can be efficient in consuming gas or removing gas out
of the galaxies, though the efficiency of these mechanisms
in protoclusters is unknown observationally and current data
sets are not sufficient to reject or accept any of the possibilities. In this regard, we may get more hints of possible mechanisms from either very massive ( _M_ star _/M_ _⊙_ _>_ 11) or lower
mass ( _M_ star _/M_ _⊙_ _<_ 10 _._ 5) galaxies in protoclusters, which
will also help to verify the observed trend.


5. SUMMARY AND CONCLUSION


We revisited the gas content of the protocluster by

[C I ] line observations using ALMA. We aimed to test if the
same calibrations in measuring gas content using CO and
dust can be applied to protocluster galaxies using an independent gas tracer of [C I ] . Five galaxies are detected in

[C I ] out of sixteen galaxies targeted. We first compared
the CO-to-[C I] luminosity relation with other studies. It
revealed the [C I ] is a good gas tracer for the protocluster
galaxies. The CO (4–3)-to-[C I ] line relation further hinted
at the presence of denser gas in protocluster galaxies com

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 13



pared to field galaxies though the dynamic range was still
too narrow to robustly conclude on the existence of different
relation in different environments. We then compared the gas
mass based on [C I ], CO(3–2), and dust when at least one of
the last two tracers was available. Given that these five galaxies are all on the main-sequence, we adopted the general calibration methods applied to (field) main-sequence galaxies
by assuming log ( _X_ CI ) = _−_ 4 _._ 8 for the [C I ] -based gas measurement. The [C I ] -based gas measurements are, in general,
bridging the gap between CO (3–2)-based and dust-based gas
estimates. They are lower or comparable to the CO-based
gas measurements by -0.35 dex at the lowest. The difference
between [C I ] - and the dust- based measurements are mild
by up to 0.16 with the mean difference of 0.02 dex. Considering the CO (4–3)-to-[C I ] line ratios and the parameter
space allowed for typical main-sequence galaxies, there are
three galaxies that CO-based gas mass may be overestimated
than the other tracers, suggesting different calibrations (or
conversion factors). Hence, the combination of _α_ CO _× R_ 13
needs to be lowered for these protocluster galaxies by up to
_≈_ 0.35 (0.43) dex to match the [C I ] -(dust-)based gas measurements. Such adjustment is still within the uncertainty of
the individual calibration methods, however.
We generally reconfirm our previous findings that the
mean gas fraction is comparable to field galaxies for a stellar mass range of log _M_ star _/M_ _⊙_ = [10 _._ 6 _,_ 11 _._ 3] ( _f_ gas =
_M_ gas _/_ ( _M_ gas + _M_ star ) _≈_ 50%)). At least for these five [C I ] detected galaxies, the depletion time scale decreases more
rapidly with stellar mass than field galaxies that might lead
galaxies to quench earlier than field galaxies. More detailed
studies on more massive galaxies (log _M_ star _/M_ _⊙_ _>_ 11) and
less massive ones (log _M_ star _/M_ _⊙_ _>_ 10 _._ 5) would help to
disentangle potential physical mechanisms that are dominant
than field galaxies making the observed trend.
Our findings support the idea that optically-thin gas tracer
of [C I ] is indeed a good tracer for probing gas content even



for protocluster galaxies. Based on the similarity between
dust-based and [C I ] -based gas measurement, dust observations would be a more efficient tool for a larger number of
galaxies to improve statistics, especially for the galaxies on
the main-sequence. However, [C I ] can still be an efficient
tracer for high- _z_ where getting CO (1–0) is more expensive,
and for such, the line can be used as an alternative anchor for

dust-based calibration.

Finally, we caution against the generalization of our findings. With limited number of galaxies detected in [C I ] (also
CO and dust), it is difficult to verify whether there is any
selection bias delivering such mass dependency. Such bias
could originate not only from the flux-limited galaxy selection (H _α_ ) but also from the halo property (mass, evolutionary
stage) of the protocluster. More galaxies in the probed mass
range (log _M_ star _/M_ _⊙_ = [10 _._ 5 _,_ 11]) in differently selected
protoclusters would also help to broaden our understanding
of galaxy evolution in different environments.


ACKNOWLEDGMENTS


We are immensely grateful to the anonymous referee for
constructive comments. We thank Dr. Daizhong Liu for
fruitful discussions and Dr. Frencesco Valentino for providing the observed data set before it became public. This paper
makes use of the following ALMA data: ADS/JAO.ALMA
#2015.1.00152.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan)
and KASI (Republic of Korea), in cooperation with the Republic of Chile. Y.T is supported by NAOJ ALMA Scientific
Research Grant No. 2018-09B.


_Facilities:_ ALMA


_Software:_ astropy (Astropy Collaboration et al. 2013),
Scikit-learn (Pedregosa et al. 2011), CASA (McMullin et al.
2007)



A. SPECTRA FOR SINGLE LINE (CO (4–3))

DETECTIONS



APPENDIX


B. HAE 4 AND HAE 10 SPECTRA AT THE CO (4–3)

PEAK POSITION



We show in Figure 6 the spectra of CO (4–3) detection
without other line dections. The spectra are obtained with
aperture sizes listed in Table 1 centered at the CO (4–3)
peak. The shaded area is to indicate the integrating range for
CO (4–3) (light red), and the corresponding velocity range
for [C I ] (light green) and CO (3–2) (light brown).



We show in Figure 7 the spectra of HAE 4b and HAE 10
centered at the CO (4–3) peak position. The shaded area is
to indicate the integrating range for CO (4–3) (light red), and
the corresponding velocity range for [C I ] (light green) and
CO (3–2) (light brown).

14 M INJU M. L EE ET AL .


**Figure 6.** The spectra of galaxies with CO (4–3) single detection (see Appendix A for details).

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 15



C. GAS MASS CROSS CALIBRATION OF INDIVIDUAL

GALAXIES


We describe here the detailed gas mass cross calibration for
individual galaxies. We investigate by first assuming that the
dust measurement, which gives the lowest value on average,
is true. In this case, the _X_ CI is recalibrated within a range
between -0.16 dex and 0.11 dex from the original assumption
of log( _X_ CI ) = _−_ 4 _._ 8, which is negligible if we consider the
scatter of the reported values (e.g., Valentino et al. 2018, _σ_ =
0 _._ 19 _−_ 0 _._ 23 dex). For _α_ CO _× R_ 13, the adjustment could be
as large as a factor of 2.7 (0.43 dex, HAE 10).
To investigate further for a best solution, we check the line
luminosity ratio between [CI] and CO. HAE 16 has a [C I]-toCO (4–3) line luminosity (in _L_ _⊙_ ) ratio (log ( _L_ CI10 _/L_ CO43 ))
of _−_ 0 _._ 37 _±_ 0 _._ 11. HAE 3a shows a [C I]-to-CO (4–3) luminosity ratio of _−_ 0 _._ 57 _±_ 0 _._ 17 in log. These line ratios are
lower relative to the average value of _z_ _∼_ 1 main-sequence
galaxies, and the value is comparable to the high- _z_ DSFGs
average value (V20). The fit to the CO-to-[CI] line luminosity (see Section 3.2) shows a hint of higher CO luminosity at
given [C I ] luminosity towards higher [C I ] for field galaxies.
While these galaxies are not as luminous as high- _z_ DSFGs,
the CO(4–3)-to-[CI] line ratios of two galaxies are comparable to them. Using a PDR model (Pound & Wolfire 2008;
Kaufman et al. 2006) [1], the line ratio suggests the existence
of _n_ H _∼_ 10 [4] _[.]_ [5] cm _[−]_ [3] gas both in HAE 16 and HAE 3a. If
the ISM properties of HAE 3a and HAE 16 resembles those
of DSFGs (those with lower _α_ CO and _R_ 13 ), the _α_ CO _× R_ 13
value may be lower than what is assumed, which leads to

more consistent values from different tracers. It would also

be worth noting that both galaxies are on the main-sequence



(log ∆MS = -0.02 and -0.03 for HAE 3a and HAE 16, respectively; Figure 4 top right). The level of adjustment in
both galaxies are -0.15 and -0.19 dex in _α_ CO _× R_ 13 .
Secondly, we consider the [C I ] non-detection case with
other emissions detected. In HAE 10 (see Appendix B for
CO and [C I ] spectra), [C I ] line is not detected and the dustbased gas mass is consistent with the [C I ] -based upper limit.
To be consistent, _α_ CO _× R_ 13 should be lowered by a factor
of _≈_ 2.7, otherwise, both the _X_ CI and dust temperature need
to be recalibrated. The latter case is less likely, because _X_ CI
needs to be lowered by 0.35 dex, and the dust temperature

should be lower than 20 K unless the difference is due to

a higher gas-to-dust ratio. While the recipe from Scoville
et al. (2016) assumes a fixed dust temperature of _T_ d = 25 K,
the mass-weighted dust temperature of star-forming galaxies could increase at least up to _z_ _∼_ 4 (Schreiber et al. 2018).
From the redshift-dependent dust temperature fit in Schreiber
et al. (2018), the expected dust temperature is above 30 K at
_z_ _∼_ 2. It is less likely that the dust temperature is lower than
20 K if the dust temperature evolution is only a function of
redshift and happening in the same manner in the protocluster galaxies. Meanwhile, the abundance ratio which is lower
by 0.35 dex than the assumed value (log ( _X_ CI ) = _−_ 4 _._ 8)
is not a commonly observed value for high-redshift galaxies. The galaxy would be a unique galaxy on the mainsequence to match with CO-based measurements. Therefore,
it would be more reasonable to conclude that the CO gas excitation condition of HAE 10 is close to, but not an extreme
case of, starburst-like phase lowering the _α_ CO _× R_ 13, while
the galaxy is on the main-sequence by Speagle et al. (2014)
(log (∆ _MS_ ) = 0 _._ 10 _±_ 0 _._ 29; Figure 4 top right).



REFERENCES



Agertz, O., Lake, G., Teyssier, R., et al. 2009, MNRAS, 392, 294


Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al.


2013, MNRAS, 435, 1493


Andrews, B. H., & Thompson, T. A. 2011, ApJ, 727, 97


Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013,


A&A, 558, A33


Barro, G., Kriek, M., P´erez-Gonz´alez, P. G., et al. 2016, ApJL,


827, L32


Bayet, E., Viti, S., Williams, D. A., Rawlings, J. M. C., & Bell, T.


2009, ApJ, 696, 1466


Bisbas, T. G., van Dishoeck, E. F., Papadopoulos, P. P., et al. 2017,


ApJ, 839, 90


Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51,


207


1 [http://dustem.astro.umd.edu/](http://dustem.astro.umd.edu/)



Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2015, ApJ, 809,


175


Boogaard, L. A., van der Werf, P., Weiß, A., et al. 2020, arXiv


e-prints, arXiv:2009.04348


Boselli, A., Cortese, L., Boquien, M., et al. 2014, A&A, 564, A67


Boselli, A., Gavazzi, G., Lequeux, J., et al. 1997, A&A, 327, 522


Bournaud, F., Daddi, E., Elmegreen, B. G., et al. 2008, A&A, 486,


741


Bourne, N., Dunlop, J. S., Simpson, J. M., et al. 2019, MNRAS,


482, 3135


Ceverino, D., Dekel, A., & Bournaud, F. 2010, MNRAS, 404, 2151


Chabrier, G. 2003, PASP, 115, 763


da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13


Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46


Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2011,


MNRAS, 410, 1687

16 M INJU M. L EE ET AL .


**Figure 7.** The spectra of the HAE 4b and HAE 10 (see Appendix B for details).

A TOMIC CARBON IN A Z =2.49 PROTOCLUSTER 17



Dannerbauer, H., Daddi, E., Riechers, D. A., et al. 2009, ApJ, 698,

L178

Frerking, M. A., Keene, J., Blacke, G. A., & Phillips, T. G. 1989,

ApJ, 344, 311

Fumagalli, M., Krumholz, M. R., Prochaska, J. X., Gavazzi, G., &

Boselli, A. 2009, ApJ, 697, 1811

Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271

Genel, S., Naab, T., Genzel, R., et al. 2012, ApJ, 745, 11

Genzel, R., Burkert, A., Bouch´e, N., et al. 2008, ApJ, 687, 59

Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

Gerin, M., & Phillips, T. G. 2000, ApJ, 537, 644

Glover, S. C. O., & Clark, P. C. 2016, MNRAS, 456, 3596

Greve, T. R., Leonidaki, I., Xilouris, E. M., et al. 2014, ApJ, 794,

142

Gunn, J. E., & Gott, III, J. R. 1972, ApJ, 176, 1

Hainline, L. J., Scoville, N. Z., Yun, M. S., et al. 2004, ApJ, 609, 61

Haynes, M. P., Giovanelli, R., & Chincarini, G. L. 1984, ARA&A,

22, 445

Hess, K. M., & Wilcots, E. M. 2013, AJ, 146, 124

Hollenbach, D. J., & Tielens, A. G. G. M. 1999, Reviews of

Modern Physics, 71, 173

Ikeda, M., Oka, T., Tatematsu, K., Sekimoto, Y., & Yamamoto, S.

2002, ApJS, 139, 467

Ikeda, M., Maezawa, H., Ito, T., et al. 1999, ApJL, 527, L59

Jiao, Q., Zhao, Y., Zhu, M., et al. 2017, ApJL, 840, L18

Jiao, Q., Zhao, Y., Lu, N., et al. 2019, ApJ, 880, 133

Juneau, S., Narayanan, D. T., Moustakas, J., et al. 2009, ApJ, 707,

1217

Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ,

644, 283

Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman,

M. L. 1999, ApJ, 527, 795

Kenney, J. D. P., & Young, J. S. 1989, ApJ, 344, 171

Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189

Larson, R. B., Tinsley, B. M., & Caldwell, C. N. 1980, ApJ, 237,

692

Lee, M. M., Tanaka, I., Kawabe, R., et al. 2017, ApJ, 842, 55

—. 2019, ApJ, 883, 92

Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235

McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K.

2007, in Astronomical Society of the Pacific Conference Series,

Vol. 376, Astronomical Data Analysis Software and Systems

XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

Offner, S. S. R., Bisbas, T. G., Viti, S., & Bell, T. A. 2013, ApJ,

770, 49

Ojha, R., Stark, A. A., Hsieh, H. H., et al. 2001, ApJ, 548, 253

Papadopoulos, P. P., & Geach, J. E. 2012, ApJ, 757, 157

Papadopoulos, P. P., Thi, W. F., & Viti, S. 2004, MNRAS, 351, 147

Pedregosa, F., Varoquaux, G., Gramfort, A., et al. 2011, Journal of

Machine Learning Research, 12, 2825



Peng, Y., Maiolino, R., & Cochrane, R. 2015, Nature, 521, 192


Poggianti, B. M., Jaff´e, Y. L., Moretti, A., et al. 2017, Nature, 548,

304


Popping, G., Decarli, R., Man, A. W. S., et al. 2017, A&A, 602,

A11


Pound, M. W., & Wolfire, M. G. 2008, in Astronomical Society of

the Pacific Conference Series, Vol. 394, Astronomical Data

Analysis Software and Systems XVII, ed. R. W. Argyle, P. S.

Bunclark, & J. R. Lewis, 654


Rasmussen, J., Ponman, T. J., & Mulchaey, J. S. 2006, MNRAS,

370, 453


R´emy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A,

563, A31


Riechers, D. A., Boogaard, L. A., Decarli, R., et al. 2020, ApJL,

896, L21


Schmidt, M. 1959, ApJ, 129, 243


Schreiber, C., Labb´e, I., Glazebrook, K., et al. 2018, A&A, 611,

A22


Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83


Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150


Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D.

2014, ApJS, 214, 15


Spilker, J. S., Marrone, D. P., Aguirre, J. E., et al. 2014, ApJ, 785,

149


Stark, A. A., Knapp, G. R., Bally, J., et al. 1986, ApJ, 310, 660


Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 457,

2790


Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, arXiv e-prints,

arXiv:2003.06245


Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179


Tadaki, K.-i., Kodama, T., Hayashi, M., et al. 2019, PASJ, 71, 40


Tanaka, I., De Breuck, C., Kurk, J. D., et al. 2011, PASJ, 63, 415


Tielens, A. G. G. M., & Hollenbach, D. 1985a, ApJ, 291, 722


—. 1985b, ApJ, 291, 747


Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27


—. 2020, ApJ, 890, 24


Verdes-Montenegro, L., Yun, M. S., Williams, B. A., et al. 2001,

A&A, 377, 812


Vollmer, B., Braine, J., Pappalardo, C., & Hily-Blant, P. 2008,

A&A, 491, 455


Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011,

ApJ, 730, 18


Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429,

L25


Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A, 409,

L41


Wu, J., Evans, Neal J., I., Gao, Y., et al. 2005, ApJL, 635, L173


Zabel, N., Davis, T. A., Smith, M. W. L., et al. 2019, MNRAS,

483, 2251

18 M INJU M. L EE ET AL .



Zhang, Z.-Y., Papadopoulos, P. P., Ivison, R. J., et al. 2016, Royal


Society Open Science, 3, 160025



Zolotov, A., Dekel, A., Mandelker, N., et al. 2015, MNRAS, 450,

2327


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0''.42 x 0''.29 (natural weighting for [C I]); 0''.53 x 0''.43, 0''.65 x 0''.57, and 0''.97 x 0''.92 (tapered)",
  "failed_quote": "The synthesized beam is 0 ′′ . 42 × 0 ′′ . 29 and the typical noise level is 0.10 mJy beam − 1 around the phase center at 80 km s − 1 for natural weighting."
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "0.10 mJy beam^-1 at 80 km s^-1 around phase center (natural weighting)",
  "failed_quote": "The synthesized beam is 0 ′′ . 42 × 0 ′′ . 29 and the typical noise level is 0.10 mJy beam − 1 around the phase center at 80 km s − 1 for natural weighting."
 },
 {
  "path": "data.external_data_from_literature[6].what.evidence[0]",
  "value": "Field galaxy gas scaling relations for gas depletion time scale",
  "failed_quote": "Figure 5 shows the gas depletion time scale of the protocluster galaxies normalized by the (field) gas scaling relation determined in Scoville et al. (2017), Tacconi et al. (2018) and Liu et al. (2019) at given stellar mass, redshift and deviation from the main sequence."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "natural weighting",
  "failed_quote": "The synthesized beam is 0 ′′ . 42 × 0 ′′ . 29 and the typical noise level is 0.10 mJy beam − 1 around the phase center at 80 km s − 1 for natural weighting."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "[C I]: 0''.42 x 0''.29 (natural), 0''.53 x 0''.43 (0''.3 taper), 0''.65 x 0''.57 (0''.5 taper), 0''.97 x 0''.92 (0''.9 taper); CO (4-3): 0''.53 x 0''.32 (natural); CO (3-2): 0''.89 x 0''.66 (natural); 1.1 mm dust: 0''.78 x 0''.68 (natural), 0''.89 x 0''.82 (0''.5 taper)",
  "failed_quote": "The synthesized beam is 0 ′′ . 42 × 0 ′′ . 29 and the typical noise level is 0.10 mJy beam − 1 around the phase center at 80 km s − 1 for natural weighting."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "0.10 mJy beam^-1 around the phase center at 80 km s^-1 (natural weighting)",
  "failed_quote": "The synthesized beam is 0 ′′ . 42 × 0 ′′ . 29 and the typical noise level is 0.10 mJy beam − 1 around the phase center at 80 km s − 1 for natural weighting."
 },
 {
  "path": "processing.inherited[3].what.evidence[1]",
  "value": "CO (3-2) and 1.1 mm dust molecular gas mass calibration recipes, stellar masses, and SFRs",
  "failed_quote": "For dust-based measurements, we adopt the calibration described in Scoville et al. (2016). The details of the calculations are presented in Paper I."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Compute [C I]-based gas depletion time scales (tau_depl = M_gas / SFR), normalize by field scaling relations from Scoville et al. (2017), Tacconi et al. (2018), and Liu et al. (2019), and compute Spearman rank correlation coefficients with stellar mass.",
  "failed_quote": "Figure 5 shows the gas depletion time scale of the protocluster galaxies normalized by the (field) gas scaling relation determined in Scoville et al. (2017), Tacconi et al. (2018) and Liu et al. (2019) at given stellar mass, redshift and deviation from the main sequence."
 },
 {
  "path": "analysis_steps[4].validation.evidence[0]",
  "value": "Compared Spearman correlation coefficients with those of z ~ 1 field control samples from Bourne et al. (2019) and V20, and checked correlation for secure detections only.",
  "failed_quote": "We also note that the correlation coefficient is -0.9 with p-value of 0.04 if only the secure detections are considered. As control samples, field galaxies from Bourne et al. (2019), and V20 show less compelling evidence of such anti-correlation"
 }
]
```
