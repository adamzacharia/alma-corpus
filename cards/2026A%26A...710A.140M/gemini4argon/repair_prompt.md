# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...710A.140M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2026
April 14, 2026

## **Observations of highly inclined disks with ALMA**

### **Results from [12] CO gas and continuum observations**


L. Martinien [1], G. Duchêne [1][,][ 2], Á. Ribas [3][,][ 4], M. Villenave [1], F. Ménard [1], K.R. Stapelfeldt [5][,⋆], and C. Pinte [1]


1 Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France
e-mail: `laurine.martinien@univ-grenoble-alpes.fr`
2 Astronomy Department, University of California Berkeley, Berkeley CA 94720-3411, USA
3 Astronomy Unit, Department of Physics and Astronomy, Queen Mary University of London, Mile End Road, London E1 4NS, UK
4 Institute of Astronomy, University of Cambridge, Madingley Road, Cambridge, CB3 0HA, UK
5 Jet Propulsion Laboratory, California Institute of Technology, 4800 Oak Grove Drive, Pasadena, CA 91109, USA


Received ; accepted


**ABSTRACT**


_Aims._ We aim to study the radial and vertical extents of [12] CO gas, millimeter dust thermal emission and optical/near infrared scattered
light by dust in highly inclined protoplanetary disks. These parameters are indicators of radial drift and vertical settling, essential for
better constraining planet formation. Additionally, we aim to provide estimates of the dynamical stellar masses including those for
which no prior measurements exist.
_Methods._ We analyze a sample of 14 highly inclined protoplanetary disks for which the vertical extent of the emission layers can
be constrained directly. We present ALMA high angular resolution band 7 (0.9 mm) continuum images and [12] CO (3-2) gas moment
maps as well as HST and VLT/SPHERE scattered light images. We estimate the dynamical masses using position-velocity diagrams.
_Results._ The majority of disks in our sample (11 out of 14) follow _R_ gas   - _R_ dust, µm   - _R_ dust, mm . The other 3 disks, including 2 in multiple
systems, appear more extended in millimeter continuum than in scattered light. Highly inclined disks tend to appear less radially
extended in CO gas line emission than in millimeter dust continuum compared to less inclined disks. This results from optical depth
effects and/or radial drift. The known correlation between disk size and millimeter continuum and line fluxes are confirmed in our
sample with highly inclined disks significantly fainter than disks seen at lower inclination for a given disk radius. We found that this
correlation is significantly tightened once fluxes are corrected for the disk inclination, consistent with the disks being optically thick
at millimeter wavelengths. Regarding the vertical extent defined as the apparent emitting height, most disks in our sample follow _H_ gas
  - _H_ dust, mm . This strengthens our previous findings that the millimeter dust is highly decoupled from the gas and forms a layer in the
disk midplane due to vertical settling. Most disks appear more vertically extended in gas than in scattered light, suggesting that the
µm-sized dust is not fully coupled to the gas. We also estimated dynamical masses for the first time for most of the objects in our
sample. We found an anti-correlation between the dynamical mass and the aspect ratio, emphasizing the dominant role of gravity in
setting the disk vertical extent, but no correlation with the disk radius.


**Key words.** protoplanetary disks – stars: formation – circumstellar matter – stars: variables: T Tauri, Herbig Ae/Be



**1.** **Introduction**


Planets form in gas-rich protoplanetary disks (Benisty et al.
2023; Pinte et al. 2023). The process leading to km-sized bodies
and larger is a long-standing puzzle. The classic core-accretion
scenario (Pollack et al. 1996) that requires small µm-sized particles to grow up by collisions into large pebbles, boulders, and
eventually planetesimals, remains the main framework for planet
building today. However, given the short lifetimes of disks (typical 5 Myr, e.g. Hernández et al. 2008) some models requiring
an increase of dust concentration in the midplane have been proposed to speed-up the grain growth up to planetesimal scales,
e.g., streaming instability (Youdin & Goodman 2005; Johansen
& Youdin 2007) and pebble accretion (Lambrechts & Johansen
2012). Large mm-sized grains that experience gas drag and are
subject to vertical settling toward the midplane and inward radial drift (Weidenschilling 1977; Barrière-Fouchet et al. 2005).
Radial drift is predicted to be ≈ 100 times slower than vertical settling (Laibe et al. 2014). Vertical settling results from the


⋆ On sabbatical leave at IPAG



damping of gravity-induced vertical oscillations of dust particles, while radial drift arises from the azimuthal velocity difference between Keplerian dust and sub-Keplerian gas. However, the expected timescale for µm-sized grains, probed by scattered light, is longer than the disk lifetime time, implying that
small grains should remain colocated with the gas. Protoplanetary disks appear larger radially in their gas component than in
their mm-sized dust component (e.g. Ansdell et al. 2018). This
can be explained by radial drift. However, these studies were biased toward low- or mid-inclination disks for which low optical
depth in the outer disk (Andrews 2020) and limited sensitivity
can affect detectability, and therefore interpretation. As a result,
these processes are poorly constrained.


In order to constrain vertical settling and radial drift, it is
important to quantify the radial and vertical distribution of dust
of different sizes and compare it to the gas extent. Indeed, the
dust extent is regulated by grain growth and the degree of migration in the disk, while the gas extent is dominated by physical
and chemical interactions and dynamics of the disk. This gas extent is preferentially measured with the [12] CO emission, the most


Article number, page 1 of 16

_A&A proofs:_ manuscript no. main



common isotopologue of the most abundant molecule after H 2,
allowing to trace the outer parts of disks. Most studies focused
on the radial sizes in low- or mid- inclination disks which revealed rings, spirals, gaps (Ansdell et al. 2018; Avenhaus et al.
2018; Pinte et al. 2018; Garufi et al. 2020; Galloway-Sprietsma
et al. 2025; Trapman et al. 2025; Vioque et al. 2025). However,
these disks do not allow the study of vertical sizes because of
their viewing geometry. Highly inclined disks are the best objects for this study because their vertical extent is more directly
accessible, with minimal de-projection required. Previous studies of edge-on disks at different wavelengths demonstrated that
the concentration of pebbles is largely enhanced in the midplane
(e.g., Villenave et al. 2020, 2022; Duchêne et al. 2024; Tazaki
et al. 2025). Moreover, highly inclined disks can provide better
constraints on the disk outer radii because of the line-of-sight integration which compensates the low optical depth in the fainter
outer regions.
Beyond the disk structure and extent, the stellar properties
are also fundamental to inform the planetary formation process. Indeed, several key disk parameters (e.g. radius, mass) are
broadly correlated with the stellar mass (Andrews 2020). Furthermore even the disk lifetime is correlated with the stellar mass
(e.g. Ribas et al. 2015). Unfortunately, it is not possible to determine the mass of the central star in highly inclined disks by comparison to evolutionary models in the HR diagram due to the lack
of luminosity estimates. Indeed, the edge-on geometry of these
systems blocks most of the stellar light, but exactly how much
is extremely difficult to establish, the photosphere not being visible directly. If possible, estimating the dynamical mass thanks
to the interaction between the host star and the gas of the disk
in rotation is the most reliable method to determine this parameter independently of stellar models or viewing geometry (e.g.,
Rosenfeld et al. 2012; Czekala et al. 2016; Simon et al. 2019).
In this study, we present observations of a sample of highly
inclined protoplanetary disks combining millimeter observations
obtained with the Atacama Large Millimeter Array (ALMA) and
optical/near-infrared (NIR) observations by the _Hubble_ Space
Telescope (HST) and the ESO Very Large Telescope (VLT). This
work is the follow-up of the study presented by Villenave et al.
(2020), with 5 new sources observed in the continuum and CO
line data presented for the first time for all sources of the sample.
We present estimations of the radial and vertical sizes of disks in
µm-sized dust (scattered light), mm-sized dust (thermal continuum emission) and [12] CO (3-2) gas line, as well as the dynamical
masses of the central stars.
The sample and the data reduction are described in Sect.
2. We present the images as well as our methods to extract
the radial, vertical sizes and dynamical masses in Sect. 3 for
the ALMA continuum and [12] CO images. Sect. 4 shows the
scattered-light HST and VLT images. After drawing comparisons on the distribution of dust of different sizes and [12] CO gas,
we discuss the differences in Sect. 5, as well as trends with dynamical masses. Finally, we summarize our conclusions in Sect.
6.


**2.** **Observations and data reduction**


_2.1._ _Target selection_


This study is a follow up of the survey presented in Villenave
et al. (2020) which combined several observing programs in
Taurus, Ophiuchus and Chamaeleon (Projects 2013.1.01175.S,
2016.1.01505.S, 2016.1.00771.S, 2016.1.00460.S, PIs: C.
Dougados, F. Louvet, G. Duchêne and F. Ménard). The au

Article number, page 2 of 16



thors analyzed a sample of 12 highly inclined disks in continuum emission. In this paper, we focus on 5 new highly inclined
disks in Ophiuchus, Upper Scorpius and Lupus, in both millimeter continuuum and [12] CO gas (Project 2022.1.00742.S, PI:
F. Ménard). CO data for 9 disks from the previous survey are
also included. We choose to not include 3 disks from the previous survey either because of the presence of an envelope, a
CO outflow, or because of the circumbinary nature of the source
(IRAS 04302, HH 30, and IRAS 04158 respectively). Thus, our
final sample consists of 14 highly inclined protoplanetary disks.
All sources were identified as candidates from their spectral energy distribution and confirmed as highly inclined by optical and/or NIR scattered-light imaging (Stapelfeldt et al. 2014).
The properties of the sample in our study are reported in Table
1. We considered 3 categories in our sample: edge-on disks in
single and multiple systems and, grazing angle disks. As their
names indicate, the edge-on disks are the most inclined ones.
They totally block the direct stellar light and only two bright
reflection nebulae on both sides of the midplane are visible in
scattered light. The grazing-angle disks are less inclined and partially mask the central star but a central point source is visible,
with less pronounced nebulae in scattered light. The trends between the categories are discussed in Sect. 5.


_2.2._ _New ALMA data_


The new data are from Project 2022.1.00742.S (PI: F. Ménard).
The first scheduling block (SB) was executed on 6 June 2023 and
included Lup 160703 and Lup 160708 (∼18 minutes on source
per target). The second SB was executed on 7 June 2023 for
the Flying Saucer, PDS 144 N, and Oph 162305 (∼14 minutes on
source per target). In both cases, 44 antennas were used dur
∼
ing the Band 7 ( 0.88 mm) observations, with baselines ranging
from 27 m to ∼3.6 km. The correlator was set up with four spectral windows (SPW), three of which with a 1.875 GHz bandwidth (128 channels) targeting continuum (centered at 332.2,
334.0, and 344.5 GHz for the first SB, and at 333.0, 340.0,
and 344.5 GHz for the second SB). The last SPW was set to
a 0.469 GHz bandwidth (1920 channels, 0.2 km s [−][1] per channel)
targeting the [12] CO (3-2) line (rest frequency 345.796 GHz).
The data were calibrated using the ALMA pipeline with
`CASA` version 6.5.4.9. For the Flying Saucer, PDS 144 N, and
Oph 162305, we performed between one and three rounds of
phase-only self-calibration using the continuum emission to improve the quality of the observations, and the correspondings
solutions were then applied to the [12] CO (3-2) data. After subtracting the continuum emission, we imaged the [12] CO (3-2) line
using channels of ∼0.8 km s [−][1] . For the imaging, we used the
`tclean` task in `CASA` with Briggs weighting and a robust parameter of 1.0. The final beam sizes of the [12] CO (3-2) data cubes are
listed in Table A.1.


_2.3._ _Archival ALMA data_


The second part of this survey is based on ALMA observations from project 2016.1.00460.S (PI: F. Ménard), for which the
continuum images have previously been published in Villenave
et al. (2020). In this program, three Cha I sources (ESO Hα 574,
ESO Hα 569, HH 48 NE) have been observed in a compact array configuration, and 6 sources located in Taurus (Tau 042021,
HK Tau B, HV Tau C, Haro 6-5B, Tau 042307) were observed
with two array configurations (compact and extended), allowing
to reach a higher angular resolution without suffering from sig

L. Martinien et al.: Observations of highly inclined disks with ALMA


**Table 1.** Stellar parameters.


Full name Adopted name SFR Distance Spectral Geometry Multiplicity
(pc) type
2MASS J16281370-2431391 Flying Saucer Ophiuchus 140 - Edge-on
IRAS 15462-2551 PDS 144 N Up Sco - Ophiuchus 140 A2 _[a]_ Edge-on Binary
2MASS J16230544-2302566 Oph 162305 Ophiuchus 140 - Edge-on
2MASS J16070384-3911113 Lup 160703 Lupus III 160 M4.5 _[b]_ Grazing-angle
2MASS J16070854-3914075 Lup 160708 Lupus III 160 M1.75 _[c]_ Grazing-angle
HK Tau B HK Tau B Taurus 130 M0.5 _[d]_ Edge-on Binary
HV Tau C HV Tau C Taurus 130 K6 _[e]_ Edge-on Multiple
2MASS J04220069+2657324 Haro 6-5B Taurus 130 K5 _[e]_ Grazing-angle
IRAS 04200+2759 Tau 042307 Taurus 130 M3.5-M6 _[e]_ Grazing-angle
2MASS J04202144+2813491 Tau 042021 Taurus 130 M1 _[f]_ Edge-on
ESO-Hα 569 ESO Hα 569 Chamaeleon I 190 M2.5 _[g]_ Edge-on
ESO-Hα 574 ESO Hα 574 Chamaeleon I 190 K7-M0 _[g]_ Edge-on
HH 48 NE HH 48 NE Chamaeleon I 190 K7 _[g]_ Edge-on Binary
2MASS J16313124-2426281 Oph 163131 Ophiuchus 140 K4-K5 _[h]_ Edge-on


**Notes.** SFR: Star-Forming Region. The distances come from Zucker et al. (2020). The horizontal line delimitates the new sources and the previous
sample analyzed in the continuum by Villenave et al. (2020).
**References.** _[a]_ Vieira et al. (2003), _[b]_ Ansdell et al. (2018), _[c]_ Muži´c et al. (2014), _[d]_ Monin et al. (1998), _[e]_ Luhman et al. (2010), _[f]_ Luhman et al. (2009),
_g_ Luhman (2007), _h_ Flores et al. (2021).



nificant flux losses. We refer the reader to Villenave et al. (2020)
for a detailed description of the setup and calibration of the observations. In this study, we focus on the [12] CO J=3-2 emission
line of center frequency 345.796 GHz. The intrinsic velocity resolution of the observations is 0.21 km/s.

To increase the signal-to-noise and dynamical range of the
observations, we self-calibrated the continuum visibilities of
the brightest sources (Tau 042021, HK Tau B, HV Tau C, Haro 65B), and applied the continuum self-calibration solution to the
line spectral window. Then, we extracted the continuum emission from the line spectral window using the `uvcontsub` CASA
task. We imaged the CO emission line with the `tclean` task and
the `multiscale` option, using a Briggs robust weighting parameter of 0.5, a velocity resolution of 0.25 km/s. We use scales of
0, 1, 3, and 7 times the beam FWHM for all sources. In addition, for the very extended sources Haro 6-5B and HV Tau C,
we added one extra scale of respectively 12, 10, and 10 times
the beam size. Finally, to improve the signal-to-noise ratio of
the faintest targets (namely Tau 042021, HK Tau B, HV Tau C,
Haro 6-5B, and Tau 042307), we used the `uvtaper` option to increase the beam size. We report the final beam sizes in Table A.1.
We also include Band 6 12 CO (2-1) observations of
Oph 163131 from projects 2016.1.00771.S (PI: G. Duchêne) and
2018.1.00958.S (PI: M. Villenave). The observations combined
a compact and an extended array configuration and were previously published in Villenave et al. (2022). We refer to that study
for further description on the data reduction.


_2.4._ _Scattered light archival data (HST and VLT)_


To compare the observed extent of our target disks between the
submillimeter continuum and CO emission from ALMA to that
observed in scattered light, we gathered HST optical and nearinfrared Level 3 images from the Mikulski Archive for Space
Telescopes (MAST). Specifically, we retrieved the NICMOS
F110W image of the Flying Saucer and the ACS F814W image of PDS 144 N from program 10603 (PI: D. Padgett), the
ACS F814W images of Lup 160703 and Lup 160708 from pro


gram 14212 (PI: K. Stapelfeldt), and the WFC3 F814W image of
Oph 162305 from program 17067 (PI: G. Duchêne). All archival
images are fully calibrated. Some of these images were previously published (Stapelfeldt et al. 1998; Duchêne et al. 2010;
Wolff et al. 2017; Wolff et al. 2021; Sturm et al. 2023; Duchêne
et al. 2024). In the case of HV Tau C, the HST optical images
present a rather extended and round morphology indicating the
presence of a remnant envelope. To better assess the size of the
scattered light disk, we instead used the 2 µm VLT/NaCo adaptive optics image presented in Duchêne et al. (2010).


**3.** **Results from ALMA**


In this section, we estimate the radial and vertical extents of the
millimeter continuum, and [12] CO emission. For the systems studied in continuum in Villenave et al. (2020), we simply report
their results.


_3.1._ _ALMA continuum images and_ [12] _CO emission moment_

_maps_


All millimeter-wavelength continuum images of our new sample are presented in Fig. 1. All of our disks present a continuous
and very elongated emission shape with a large axis ratio, confirming their highly inclined geometry, except for Lup 160703
and Lup 160708 which show a knotty structure (possibly due to
low signal-to-noise ratio, SNR) and a ring, respectively. These
disks are less inclined than others, allowing us to observe structures that are not visible in the edge-on geometry. This geometry, which we refer to as grazing-angle, was also observed in the
previous continuum survey for Haro 6-5B and IRAS 04158 (Villenave et al. 2020). We determined the position angle of each
disks by manually measuring the orientation of their major axes
(column 2 in Table 2).
The results of the [12] CO (3-2) gas from both surveys are presented in Figs. 2 and 4 for the moment 1 and moment 0 (M1 and
M0) maps, respectively. We constructed the moment maps using
the `bettermoments` package developed by Teague & Foreman

Article number, page 3 of 16

**Fig. 1.** Continuum images of the newly observed sources normalized to their peak intensity (reported in the bottom right corner of each image).
The beam size (ellipse) and a 0 [′′] . 5 scale (dark line) are shown in the ~~bo~~ ttom left corner of each panel.



Mackey (2018), applying a 3σ clipping. The companions in binary systems (third row on Fig. 2) are also displayed in the moment maps, except for the HV Tau system for which the companions do not host a disk. We also notice that the gas emission
of the two disks of the binary system HH 48 overlap with each
other. HH 48 SW presents a long tail (see Sect. 5.3) but we did
not take it into account in the measure of the line flux.
We identified three different geometries in the moment maps
of Fig. 2: the typical rectangular elongated shape of edge-on
disks (HK Tau B, HV Tau C, HH 48 NE, PDS 144 N – intriguingly, all are members of multiple systems), the X-shape associated with edge-on disks (Dutrey et al. 2017; Louvet et al.
2018; Duchêne et al. 2024) with sharp edges (Flying Saucer,
Tau 042021, Oph 163131), and finally, the fluffy X-shape for the
less inclined disks (Haro 6-5B, Lup 160703 and Lup 160708).
The X-shape is due to the projection of CO emission layers in
the warm molecular layer separated by a cold zone where CO
freezes out. For the thinner disks, the two layers are not resolved
leading to the rectangular shape. Regarding the grazing-angle
disks (bottom row on Fig. 2), their [12] CO gas shape seems different from the vertically narrow emission or the sharp X-shape of
edge-on disks, with a more spread-out emission. Their X-shape
is more fluffy and filled in. There is also a vertical asymmetry
(particularly pronounced for Haro 6-5B and Lup 160708) with
fainter CO emission in the lower nebula as identified from the
scattered light images, as expected from the vertical temperature
gradient in the molecular layer. We do not attribute a category
for Oph 162305, ESO Hα 569, ESO Hα 574 and Tau 042307 because of the modest angular resolution for the first three disks
and irregular morphology, respectively.


_3.2._ _Millimeter continuum and_ [12] _CO (3-2) line fluxes_


All continuum and gas brightness values are reported in Table
3. The fluxes were measured by integrating within rectangular
apertures tailored to each disk. We quadratically combined the
measurement error and the calibration error estimated at 10%
which correspond to the typical flux calibration errors of ALMA
(see ALMA Technical Handbook [1] ). We note that the error was
dominated by the calibration one. The gas flux was extracted
from the M0 maps, following the same process as the continuum
flux with a 10% calibration error.


_3.3._ _ALMA radial extents_


To measure the radial extent of the disks from their continuum
emission we extracted surface brightness profiles along the major axis of each disk. We integrated over the full vertical extent


1 `[https://almascience.eso.org/documents-and-tools/](https://almascience.eso.org/documents-and-tools/cycle12/alma-technical-handbook)`
```
cycle12/alma-technical-handbook

```

Article number, page 4 of 16



**Table 2.** Disks parameters.


Sources PA _i_ AxisRatio _i_ _literature_
( [◦] ) ( [◦] ) ( [◦] )
Flying Saucer 93 >86 87.0 ± 0.1 _[b]_
PDS 144 N 45 >81 83 ± 1 _[c]_
Oph 162305 77 >72     Lup 160703 146 >73     Lup 160708 154 66     HK Tau B 41 >83 _[a]_ 85 ± 1 _[d]_

HV Tau C 108 >80 _[a]_ 83 [+] − [1] 2 _e_

Haro 6-5B 145 74± 2 _[a]_ 81 [+] − [1] 2 _f_
Tau 042307 129 69± 2 _[a]_     
Tau 042021 164 >85 _[a]_ 88 _[g]_

ESO Hα 569 144 >64 _[a]_ 87.3 ± 0.3 _[h]_

ESO Hα 574 141 >69 _[a]_    HH 48 NE 75 >68 _[a]_ 88 ± 1 _[i]_

Oph 163131 49 >80 _[a]_ 84 _[j]_


**Notes.** The _i_ AxisRatio values are estimated from the
ALMA continuum data.
**References** . _[a]_ Villenave et al. (2020), _[b]_ Dutrey et al.
(2025), _[c]_ Perrin et al. (2006), _[d]_ McCabe et al. (2011),
_e_ Duchêne et al. (2010), _f_ Kirchschlager et al. (2016),
_g_ Duchêne et al. (2024), _h_ Wolff et al. (2017), _i_ Sturm
et al. (2023), _[j]_ Villenave et al. (2022).


of the disk and normalized by the maximum intensity. We then
estimated the noise level (σ) outside of the disk signal. The major axis size was determined at a level of 3σ above the background. We have re-evaluated the uncertainties associated with
the continuum sizes measurements in Villenave et al. (2020),
which previously accounted only for the beam-related uncertainty. The dominant source of error is methodological: the estimated size depends slightly on the size over which we integrated
to do the profile. Therefore, we estimated the associated uncertainty by varying the window over which the profile is estimated
and quadratically added a tenth of the beam size along the major
axis direction. Because of the vertical integration, this method is
sensitive to lower signal which is not visible in contour images.
The resulting major axis sizes are presented in column 2 of Table
4.

The gas extent is more difficult to measure because the emission is intrinsically fuzzier and noisier than in the continuum, especially at the outer radii. We measured the radial extent of the
12 CO emission with cuts along the major axis directly through
the image cubes. Instead of processing all the channels for which
the [12] CO emission is detected, we visually selected the channel
for which the radial extent is maximum, for the blue and red
side to maximize SNR. We then followed the same method de

L. Martinien et al.: Observations of highly inclined disks with ALMA



**Table 3.** ALMA Source Brightness Measurements


Sources Continuum 12 CO (3-2) Central
flux density line flux wavelength
(mJy) (Jy km s [−][1] ) (µm)
Flying Saucer 61 ± 6 1.2 ± 0.1 868
PDS 144 N 213 ± 21 5.4 ± 0.5 868
Oph 162305 12 ± 1 0.43 ± 0.04 868
Lup 160703 4.30 ± 0.40 1.3 ± 0.1 868
Lup 160708 76 ± 8 3.0 ± 0.3 868
HK Tau B 56 ± 6 _[a]_ 1.5 ± 0.2 868

HV Tau C 91 ± 9 _[a]_ 7.9 ± 0.8 868

Haro 6-5B 341 ± 34 _[a]_ 9.7 ± 1.0 868

Tau 042307 66 ± 7 _[a]_ 1.4 ± 0.1 868

Tau 042021 124 ± 12 _[a]_ 6.8 ± 0.7 868

ESO Hα 569 40 ± 4 _[a]_ 2.3 ± 0.2 868

ESO Hα 574 9 ± 1 _[a]_ 1.3 ± 0.1 868

HH 48 NE 31 ± 3 _[a]_ 5.9 ± 0.6 868
Oph 163131 125.8 ± 2.4 _[b]_ 5.7 ± 0.6 [∗] 1300


**Notes.** [∗][12] CO (2-1) line flux.
**References** . _[a]_ Villenave et al. (2020), _[b]_ Cox et al. (2017).


scribed above for the size of the continuum emission to measure
the radius at a level of 3σ above the background. However, for
HH 48 NE, on the West side the signal does not go down to 3σ
because of contamination by the companion. In this case, we
estimated the maximal extent as the point of the minimum emission between the two disks, which slightly underestimates the
size since this minimum is at the 5σ level. The uncertainties are
estimated following the same process as that used for the radial extent of the continuum. The values are reported in column
4 of Table 4. We note that a few of these values are larger by
up to 40% (in the most pathological case) than those estimated
from the moment 0 maps due to differences in noise statistics
and cloud contamination, confirming the inadequacy of moment
maps to estimate the full radial extent of disks. However, there
is an exception for Flying Saucer, for which the value is lower
compared to what is apparent in the moment map (Fig. 4) likely
due to low SNR. For this disk, in the following part of our study,
we adopt the diameter radial extent of 5 [′′] . 5 (Dutrey et al. 2017).


_3.4._ _ALMA vertical extents_


To measure the vertical extent of the disks from the continuum images, we extracted brightness profiles along the minor
axis of each disk. We applied the same method as for the continuum radial extent. The profiles being single peaked because
the continuum vertical extent is not well resolved, we estimated
the FWHM by fitting Gaussians to the disk profiles except for
Lup 160708 where the ring geometry prevents a measurement of
the intrinsic vertical extent. The measurements errors correspond
to a tenth of the beam size projected in the direction of the cut.
We also quadratically subtract the FWHM of the beam from the
measured FWHM to obtain the intrinsic FWHM and propagated
the errors. The resulting minor axis sizes are presented in column
2 in Table 5.

We also estimated the disk inclinations from their measured
axis ratio. To measure the axis ratio, we use the major axis size
at 50% of the maximum flux that can be readily compared to the
intrinsic FWHM along the minor axis. The values are reported
in column 3 in Table 2 as lower limits because the aspect ratio
is a combination of the intrinsic vertical extent and projection



**Table** **4.** Major axis diameters measurements from the ALMA continuum, HST scattered light observations and ALMA [12] CO.


Sources Millimeter Optical/NIR Millimeter
continuum scattered 12 CO gas
( [′′] ) ( [′′] ) ( [′′] )
Flying Saucer 3.18 ± 0.05 3.2 ± 0.10 2.64 ± 0.10 [∗]
PDS 144 N 1.25 ± 0.05 1.7 ± 0.10 1.84 ± 0.10
Oph 162305 0.67 ± 0.05 0.9 ± 0.10 1.02 ± 0.10
Lup 160703 0.84 ± 0.05 1.7 ± 0.10 2.08 ± 0.10
Lup 160708 1.78 ± 0.05 2.0 ± 0.10 3.04 ± 0.10
HK Tau B 0.99 ± 0.05 _[a]_ 1.3 ± 0.10 _[a]_ 1.73 ± 0.10

HV Tau C 1.20 ± 0.05 _[a]_ 0.8 ± 0.10 _[a]_ 3.74 ± 0.10

Haro 6-5B 2.06 ± 0.05 _[a]_ 3.4 ± 0.10 6.27 ± 0.10

Tau 042307 1.00 ± 0.05 _[a]_ 1.5 ± 0.10 2.49 ± 0.10

Tau 042021 4.10 ± 0.05 _[a]_ 5.0 ± 0.10 _[a]_ 7.05 ± 0.10

ESO Hα 569 1.88 ± 0.06 _[a]_ 2.0 ± 0.10 _[a]_ 3.67 ± 0.11

ESO Hα 574 1.35 ± 0.06 _[a]_ 1.2 ± 0.10 _[a]_ 2.32 ± 0.11

HH 48 NE 1.72 ± 0.05 _[a]_ 1.3 ± 0.10 _[a]_ 3.40 ± 0.10
Oph 163131 2.50 ± 0.05 _[a]_ 3.0 ± 0.10 4.44 ± 0.10


**Notes.** [∗] The larger size of the Flying source in scattered light compared
to the millimeter emission is likely due to the low SNR of the ALMA
data. In the following part of our study, we used the diameter radial
extent of 5 [′′] . 5 (Dutrey et al. 2017)
**References** . _[a]_ Villenave et al. (2020). All observations are in Band 7
except for Oph 163131 which are in Band 6.


effects, except for Lup 160708 where an ellipse is fitted to the
ring.
The vertical extent of the [12] CO emission was also measured
with cuts along the minor axis. Contrary to the radial extent, the
vertical extent does not vary much from channel to channel. We
have chosen to collapse all channels for which the gas emission
was detected to gain SNR. To estimate the gas vertical extent,
we followed the same method as for the radial extent of the gas
without fitting Gaussians to the disk profiles as for the continuum
vertical extent because the gas is vertically well resolved compared to the continuum. In this case, the dominant uncertainty is
the same described as for the radial extent of the continuum. We
quadratically added 10% of the beam size in the direction of the
cut to that uncertainty. The values are reported in column 4 in
Table 5.


_3.5._ _Dynamical masses_


Fig. 3 presents a position-velocity (PV) diagram for each source.
Relevant keplerian velocity curves are superimposed in each
diagram to estimate the stellar masses. To draw these curves,
we considered inclinations from the literature when available
or used the results from column 3 of Table 2 for systems with
no previous values. For the latter, when a lower limit is estimated, we considered the midpoint between this lower limit
and 90°, but note that the PV diagram is hardly affected by
the inclination in nearly edge-on configurations. Since GAIA
DR3 distance measurements are unreliable for edge-on disks,
we considered distance of 130 pc for Taurus, 140 pc for Ophiuchus, 140 pc for Upper-Scorpius, 160 pc for Lupus and 190 pc
for Chamaeleon (Zucker et al. 2020). We note, however, that
the dynamical masses scale linearly with distance. We note that
two disks only contain information along the vertical direction
in their PV diagrams (Haro 6-5B and Lup 160708). This can be
the tracer of a ring geometry (Dutrey et al. 2017), which is con

Article number, page 5 of 16

_A&A proofs:_ manuscript no. main



Velocity (km/s)
0 1 2 3 4 5



Velocity (km/s)
0 1 2 3 4 5 6



Velocity (km/s)
2 3 4 5 6 7



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0









2 1 0 1 2



1.00


0.75


0.50


0.25


0.00


0.25


0.50


0.75


1.00



1.0 0.5 0.0 0.5 1.0



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0



2 1 0 1 2



RA (arcsec)


Velocity (km/s)
6.0 6.5 7.0 7.5 8.0 8.5 9.0



RA (arcsec)


Velocity (km/s)
3.0 3.5 4.0 4.5 5.0 5.5 6.0



RA (arcsec)


Velocity (km/s)
2.0 2.5 3.0 3.5 4.0 4.5 5.0 5.5 6.0







3


2


1


0


1


2


3





3 2 1 0 1 2 3

RA (arcsec)


Velocity (km/s)
3 4 5 6 7 8 9 10



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0



RA (arcsec)


Velocity (km/s)
4 5 6 7 8 9



2 1 0 1 2



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0



2 1 0 1 2



RA (arcsec)


Velocity (km/s)
2 3 4 5 6 7



Velocity (km/s)
0 2 4 6 8 10



4 2 0 2 4



3 2 1 0 1 2 3



1


0


1


2


3


4


5


6





3





2


1


0


1


2 1 0 1 2 3

RA (arcsec)


Velocity (km/s)
4.0 4.5 5.0 5.5 6.0 6.5 7.0 7.5 8.0



RA (arcsec)


Velocity (km/s)
4 5 6 7 8 9 10



3


2


1


0


1


2


3


4



3 2 1 0 1 2 3 4



2


1


0


1


2


3


4


5


6


7



RA (arcsec)


Velocity (km/s)
0 1 2 3 4 5


1.5


1.0


0.5


0.0


0.5


1.0



RA (arcsec)


Velocity (km/s)
0 1 2 3 4 5



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0





3


2


1


0


1


2







RA (arcsec)



2 1 0 1 2



3 2 1 0 1 2 3

RA (arcsec)



1.51.5 1.0 0.5 0.0 0.5 1.0 1.5

RA (arcsec)



2 1 0 1 2



RA (arcsec)



**Fig. 2.** [12] CO moment 1 maps of the 14 disks in both surveys. The first two rows correspond to edge-on disks, the third row to multiple systems
with one edge-on disk and the last row to grazing-angle disks.



firmed in the millimeter continuum image of Lup 160708 (see
Fig. 1) and Haro 6-5B (Villenave et al. 2020).

The estimation of stellar masses from PV diagrams is generally ill defined due to the modest SNR per spaxel, cloud contamination, and the presence of possible substructures and asymmetries, which precludes a robust statistical approach. With a coarse
exploration, we thus choose to add 3 Keplerian velocity curves:
a first one which fits the outermost maximum intensity of the PV
diagram, a second one which follows the transition between the
signal and the noise and a last one clearly off the signal. These
3 Keplerian curves allow to constrain a lower limit, a preferred
mass as well as an upper limit, respectively. The lower and upper limits should be treated as very conservative (≈ 3σ) limits.
We visually estimated the systemic velocity so that the Keple

Article number, page 6 of 16



rian curves were symmetrically aligned with the PV diagrams.
All values of systemic velocity and stellar mass are summarized
in Table. 6.


We also notice that the lowest dynamical masses (ranging
from 0.5 to 1.0 M ⊙ ) correspond to 3 out of 4 grazing-angle systems (Tau 042307, Lup 160703, Lup 160708) and 3 edge-on systems (Flying Saucer, ESO Hα 569, Tau 042021). Furthermore, 4
disks out of 6 among the lowest masses show a clear X-shape.
A possible interpretation is that a low dynamical mass implies
a larger _h_ / _r_ ratio (Fig. 9), which is a case where the X-shape is
well-defined if the angular resolution is sufficiently high.

L. Martinien et al.: Observations of highly inclined disks with ALMA


**Fig. 3.** Position-velocity diagrams with 3 Keplerian velocity curves corresponding to the preferred dynamical mass of the star, as well as conservative upper and lower limits.



**4.** **Results from HST and VLT optical and**
**near-infrared scattered light**


In this section, we estimate the radial and vertical extents of the
scattered light. Villenave et al. (2020) reported the radial extent
of all but one of their disks and we report their results here. We
also determine the radial extent of Tau 042307, which they had
not estimated.



_4.1._ _Optical and NIR scattered light images_


Fig. 4 shows overlays of optical and NIR scattered light images with continuum millimeter and [12] CO images. The scattered
light images in the first three rows present the typical features
of edge-on disks: two bright reflection nebulae separated by a
dark lane blocking direct starlight. However, the morphology of
disks shown in the last row is different with a less visible bottom


Article number, page 7 of 16

_A&A proofs:_ manuscript no. main



**Table** **5.** Minor axis sizes measurements from the ALMA continuum,
HST scattered light observations and ALMA [12] CO.


Sources Millimeter Optical/NIR Millimeter
continuum scattered 12 CO gas
( [′′] ) ( [′′] ) ( [′′] )
Flying Saucer 0.20 ± 0.01 1.13 ± 0.02 0.86 ± 0.02 [∗]
PDS 144 N 0.14 ± 0.03 0.62 ± 0.02 0.60 ± 0.03
Oph 162305 0.10 ± 0.01 0.17 ± 0.03 0.28 ± 0.02
Lup 160703 0.15 ± 0.02 0.35 ± 0.05 0.81 ± 0.02
Lup 160708  - 0.65 ± 0.05 1.05 ± 0.02
HK Tau B 0.10 ± 0.01 _[a]_ 0.23 ± 0.04 0.53 ± 0.02

HV Tau C 0.13 ± 0.02 _[a]_ 0.30 ± 0.04 0.65 ± 0.02

Haro 6-5B 0.34 ± 0.01 _[a]_ 1.36 ± 0.02 1.33 ± 0.02

Tau 042307 0.31 ± 0.01 _[a]_ 0.43 ± 0.03 1.03 ± 0.03

Tau 042021 0.31 ± 0.01 _[a]_ 2.15 ± 0.05 2.18 ± 0.04

ESO Hα 569 <0.13 _[a]_ 0.90 ± 0.02 1.06 ± 0.03

ESO Hα 574 <0.21 _[a]_ 0.40 ± 0.08 0.75 ± 0.04

HH 48 NE <0.24 _[a]_ 0.40 ± 0.10 1.41 ± 0.04
Oph 163131 <0.14 _[a]_ 0.42 ± 0.06 0.97 ± 0.02


**Notes.** See Sect. 3.4 and 4.3 for definitions of the three quantities.
∗ The larger size of the Flying source in scattered light compared to the
millimeter emission is likely due to the low SNR of the ALMA data.

**References** . _[a]_ Villenave et al. (2020). All observations are in Band 7
except for Oph 163131 which are in Band 6.


**Table 6.** Systemic velocities and dynamical masses from this work and
from the literature.


Sources V _sys_ M ⋆ M ⋆ _literature_
(km s [−][1] ) (M⊙) (M⊙)
Flying Saucer 3.2 0.9 (0.6..1.5) 0.60 _[a]_
PDS 144 N 4.9 2.1 (1.4..2.8)
Oph 162305 2.5 1.2 (0.7..1.7)
Lup 160703 3.1 0.4 (0.2..0.6)
Lup 160708 2.7 1.0 (0.5..1.3)
HK Tau B 6.9 1.2 (0.9..1.5) 0.89 ± 0.04 _[b]_

HV Tau C 6.4 1.9 (1.2..2.3) 1.33 ± 0.04 _[b]_
Haro 6-5B 7.5 1.6 (1.0..2.5) 0.25 _[c]_

Tau 042307 6.3 0.7 (0.5..1.0) 0.52 ± 0.04 _[b]_

Tau 042021 7.4 0.5 (0.3..0.6) 0.25 - 0.4 _[d]_
ESO Hα 569 4.7 0.7 (0.4..0.9)
ESO Hα 574 4.3 1.2 (0.7..1.5)
HH 48 NE 4.75 1.5 (1.0..2.5) 1 - 1.4 _[e]_

Oph 163131 4.5 1.6 (1.1..2.2) 1.2 ± 0.2 _[f]_


**Notes.** We present a preferential mass with lower and upper limits.

**References** . _[a]_ Dutrey et al. (2025), _[b]_ Simon et al. (2019), _[c]_ Yokogawa
et al. (2002), _[d]_ Duchêne et al. (2024), _[e]_ Sturm et al. (2023), _[f]_ Flores
et al. (2021).


nebula and a visible central point source. These disks are seen
at grazing angle (i.e. inclined so that the stellar light lay in our
line-of-sight). We notice a bizarre observation for Oph 162305.
Indeed, the PA in the HST scattered light image (69 [◦] ) does
not match the PA in the millimeter continuum image (77 [◦] ). A
possible explanation lies in the fact that, Oph 162305 is a very
compact disk resulting in less well defined PAs. Moreover, the
ALMA beam is tilted relative to the disk major axis and may
affect the interpretation. Higher quality ALMA observations are
needed to conclude whether this is a physical effect or an artifact
of the observations.


Article number, page 8 of 16



_4.2._ _Optical and NIR scattered light radial extent_


We estimated the scattered light major axis sizes by following
the spine of the more extended nebula, based on the method
described in Appendix D in Villenave et al. (2020). The errors
correspond to a typical value of ∼2 pixels in the image due
to the uncertain transition between clearly detected signal and
background noise. We checked the radial extents of the disks
from the previous survey and updated them for Haro 6-5B and
Oph 163131, which had been underestimated. The major axis
sizes are summarized in column 3 of Table 4.


_4.3._ _Optical and NIR scattered light vertical extent_


We also estimated the scattered light minor axis sizes based on
the spine method used to estimate the major sizes for all the
sources. In this case, we considered the distance along the vertical direction between the upper and lower nebulae at the edges of
the disk. The vertical extent is defined as the mean between the
vertical extent on both sides of the disk. The errors correspond
to half the difference between these two values. The values are
summarized in column 3 of Table 5. However, these sizes should
be considered as underestimates if the disk radially extends further on one side than the other.


**5.** **Discussion**


_5.1._ _Comparison of radial and vertical disk sizes_


The differences in radial and vertical extents between gas, millimeter dust and scattered light dust allow us to draw interpretations related to the growth and dynamics of grains. In this subsection, we compare the radius size, _R_ (left column of Fig. 5),
and the vertical apparent emitting height, _H_, –which should not
be confused with the scale height– (right column of Fig. 5) between the gas and the two population of dust sizes. In the following, we suppose that the [12] CO emission and the µm-sized dust
are much more optically thick than the millimeter continuum.


All disks in our new sample are more radially extended in
scattered light than in the millimeter continuum (see Fig. 4). The
conclusion is similar for the disks of the previous survey, with
the exception of HV Tau C, ESO Hα 574 and HH 48 NE that are
more compact in scattered light. Two of these three disks are
members of multiple systems and we will discuss differences in
these systems in Sect. 5.3. The more extended scattered light
compared to the continuum millimeter can be linked to dust radial drift that drags dust grains towards pressure maximum or
opacity effects. Moreover, all disks are more extended in the
12 CO gas emission than in scattered light and in the continuum
emission. These results are discused in Sect. 5.1.1.


As for the radial extent, the disks appear clearly vertically
extended in scattered light as opposed to the millimeter continuum which appears flat and concentrated to the midplane. On
the other hand, the vertical extent of the [12] CO gas is closer to
the vertical extent of the scattered light images. This is expected
since the scattered light images probe the small µm-sized grains
that are expected to be well coupled to the gas, whereas the
millimeter continuum probes bigger grains that have settled to
the midplane (Villenave et al. 2020). This is further discused in
Sect. 5.1.2.

L. Martinien et al.: Observations of highly inclined disks with ALMA



0.6


0.4


0.2


0.0


0.2


0.4


0.6





2


1


0


1


2













2 1 0 1 2

RA (arcsec)

























2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0







RA (arcsec)









3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.5


1.0









2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2.0











2 1 0 1 2







RA (arcsec)













1.5


1.0


0.5


0.0


0.5


1.0





3


2


1



0


1







RA (arcsec)



1.5

1.5 1.0 0.5 0.0 0.5 1.0 1.5

RA (arcsec)



2


RA (arcsec)





RA (arcsec)



**Fig.** **4.** Overlay of scattered light (grayscale image), ALMA 0.9 mm continuum (blue contours) and ALMA [12] CO gas (semi-transparent red
image) for all sources in this study. The scattered light images are plotted on a logarithmic stretch and the contours of ALMA continuum are
plotted at 30, 50, 70, and 90% of the maximum emission, except for the binaries for which we adjusted the contours due to the brightness of the
companion as well as for Oph 163131 to distinguish the rings structure. The blue and red ellipses in the bottom left corner indicate the beam size
of the ALMA continuum and ALMA [12] CO gas, respectively. Scattered light images: Flying Saucer: 1.1 µm; Oph 162305: 0.81 µm; Oph 163131:
0.81 µm; Tau 042021: 0.81 µm; ESO Hα 569: 0.81 µm; ESO Hα 574: 0.6 µm; HK Tau: 0.48 µm; HV Tau C: 2.1 µm; HH 48: 0.81 µm; PDS 144:
0.81 µm; Tau 042307: 0.6 µm; Haro 6-5B: 1.6 µm; Lup 160703: 0.81 µm; Lup 160708: 0.8 µm.



5.1.1. Radial extents


In all three tracers (millimeter continuum, CO emission and scattered light), highly inclined disks appear generally larger than
lower inclination ones. This is a consequence of a known selection bias as only the larger edge-on disks are well-resolved in the
HST images used to identify them in the first place (Angelo et al.
2023).



_Continuum_ _emission_ _vs_ _gas._ To better place edge-on disks
in context, we also added size measurements of less inclined
Class II disks from the literature (Ansdell et al. 2018; Trapman
et al. 2025; Vioque et al. 2025), see Fig. 5a. The disks in our
sample follow the trend of less inclined disks with _R_ gas larger
than _R_ dust, mm . For the general population, the _R_ gas / _R_ dust, mm
ratio is centered around 2–3 (Ansdell et al. 2018; Deng et al.
2025). However, the highly inclined disks tend to have smaller
gas-to-dust radius ratios, and appear closer to _R_ gas ≈ 1.5–2 ×


Article number, page 9 of 16

_A&A proofs:_ manuscript no. main


**Fig. 5.** Comparison between disks radius in gas, millimeter dust and scattered light dust in the radial direction (top row) and disks heights (bottom
row). We added radius measurements of Class II disks in the millimeter dust from Ansdell et al. (2018); Vioque et al. (2025), in the scattered light
dust from Avenhaus et al. (2018); Garufi et al. (2020) and in the gas from Pinte et al. (2018); Galloway-Sprietsma et al. (2025). The inclinations
are not indicated in the sample of Garufi et al. (2020), however, all the disks are at low inclinations, except one disk which is the more extended in
millimeter and scattered light.



_R_ line-of-sight integration e dust, mm . These smaller ratios may be expected because, e.g., offfects, the highly inclined disks providing more robust estimates of _R_ dust, mm, with larger values than for
less inclined disks. Is it worth noting however that statistical tests
show that the difference between the two samples is marginal.
The Mann-Whitney _U_ test, most sensitive to the median value of
each sample, yields a ≈90% confidence level that the two populations are intrinsically different. Similarly, the Kolmogorov

Article number, page 10 of 16



Smirnov test, which is more sensitive to the shape of the underlying distribution, yields a 93% confidence level.
The smaller dust radius compared to the gas radius can be
explained in more details by a combination of optical depth effects and radial drift (Facchini et al. 2017; Ansdell et al. 2018).
Indeed, the millimeter dust is less optically thick than the [12] CO
emission, which can lead to an easier detection of gas at larger
radii. This effect is attenuated in the case of highly inclined disks,
where line-of-sight integration enhances the detectability of the

L. Martinien et al.: Observations of highly inclined disks with ALMA



continuum emission in the outer regions. From a model perspective, Ansdell et al. (2018) and Trapman et al. (2019) showed that
a _R_ gas / _R_ dust, mm ratio ≳ 3–4 is a clear indicator of grain growth
and radial drift. Conversely, Ansdell et al. (2018), following the
models of Facchini et al. (2017), found _R_ gas / _R_ dust, mm ≈ 1.5
for a model with uniform dust distribution, i.e., no growth and
no drift. Only a few disks in the literature sample and none of
our highly inclined disks sample are above the maximum ratio
predicted by the radial drift models (see Fig. 5a). Taken at face
value, these results suggest that the ratios in most of our highly
inclined disks can be explained by optical depth effects because
their _R_ gas / _R_ dust, mm ratios are close to 1.5. However, these model
ratios are predicted in the case of mid-inclinations disks and do
not account for (large) radiative transfer effects expected in very
highly inclined ones. Models of radial drift with radiative transfer dedicated to highly inclined disks are required to disentangle between radial drift and opacity effects based on the _R_ gas /
_R_ dust, mm ratio.
_Continuum_ _emission_ _vs_ _scattered_ _light._ The comparison between the millimeter (large grains) and scattered light (small
grains) dust is more poorly constrained in the literature. We
added disk size estimates of all objects from Garufi et al. (2020)
to our sample. The scattered light dust is more radially extended
than the millimeter dust, except for 4 disks (see Fig. 5b). The
disks tend to follow _R_ dust, µm / _R_ dust, mm ≈ 1–2, which is consistent with the results in Villenave et al. (2020) and with the
radial drift theory between millimeter and scattered light dust
( _R_ dust, µm / _R_ dust, mm ≈ 1.6; e.g., Laibe et al. 2014). In other words,
the disks with clear indicator of radial drift are those for which
the millimeter dust is less extended than the scattered light dust.
Ultimately, this ratio can be an indicator of more or less evolved
disks, although it should not be used as the single argument Ultimately, this ratio may represent a potentially more reliable indicator of dust radial drift, a claim that dedicated models should
verify. One must keep in mind however that the more evolved
disks, with traces of more radial drift, are not necessarily the
older ones.

_Scattered_ _light_ _vs_ _gas._ Regarding the comparison between
the scattered light (small grains) dust and the gas, the disks are
more radially extended in gas than in scattered light (see Fig. 5c).
All the disks in our sample are in the range _R_ gas / _R_ dust, µm ≈ 1–2,
except two disks, which are in multiple systems, and have a size
ratio above 2 and 3. This could be explained by the fact that the
dust in the outer regions is not illuminated by the central star, due
to shadowing, while the CO emission is still detectable, or there
are not enough µm-sized grains to be detected. Nonetheless, several indications suggest that only a small amount of µm dust
lays in the midplane in the outermost regions probed by the scattered light, such as the silhouette in Flying Saucer (Dartois et al.
2024, Ma et al. in prep) and the detection of a galaxy behind
Tau 042021 (Duchêne et al. 2024). Another explanation suggests
that the small dust is not perfectly radially coupled to the gas
which extends over larger radii. This is in line with the analytical models (Birnstiel & Andrews 2014), who demonstrated that
even µm-sized dust can drift inward in the outermost regions of
a disk, where the gas density is low enough. These models suggest that most protoplanetary disks should present a sharp outer
edge in their dust component well inside the outer gas radius,
consistent with our findings. Barrière-Fouchet et al. (2005) also
showed in models without dust evolution that the outer radius of
µm-sized dust is smaller than the gas outer radius.
Strong correlations between flux density and disk radius have
been documented in the literature for both the continuum (e.g.,
Tripathi et al. 2017; Andrews et al. 2018; Hendler et al. 2020)



and line emission (e.g., Sanchis et al. 2021; Long et al. 2022; Zagaria et al. 2023; Zallio et al. 2026). This is also observed in our
sample of highly inclined disks, where the two quantities are significantly correlated ( _r_ = 0.47 and _r_ = 0.67) with confidence levels of 91% and 99.2% based on Pearson tests for the continuum
and line emission, respectively. Since the flux density roughly
scales as _R_ [2]
lation is a geometrical e dust, mm [, the most common interpretation of this corre-] ffect that arises if disks are optically thick
and the total flux primarily depends on the solid angle subtended
by the disk and the filling factor of the disk emission (Tripathi
et al. 2017). The highly inclined disks studied here provide a
fresh opportunity to test this hypothesis as inclination plays a key
factor in setting this solid angle. Fig. 6 shows that highly inclined
disks are significantly fainter in both continuum and line emission than disks seen at lower inclination for a given disk radius.
Furthermore, within the latter sample, there is a clear gradient of
disk flux with inclination for the continuum emission, the lower
inclination systems being systematically brighter. To further test
this geometrical effect, we apply a simple correction to account
for projection effects, i.e., we divide the measured flux by cos( _i_ ).
We note that this correction assumes an infinitely thin emitting
layer, which may not be perfect for the CO emission or for the
continuum emission when the inclination approaches 90 [◦] . Furthermore, small inclination uncertainties result in large errors on
the correction factor. Nonetheless, this simple approach provides
a purely geometrical correction that enables a comparison of the
overall sample. As the right panels of Fig. 6 illustrate, the correlation between disk size and flux becomes much tighter and
highly-inclined disks now reside along the same correlations as
lower inclination systems. For highly-inclined disks, the confidence level in the correlation between millimeter flux and disks
increases to 99.1% and 99.5% ( _r_ = 0.66 and _r_ = 0.71 from
Pearson tests) for the continuum and line emission, respectively.
Overall, these results provide strong support for the optical depth
interpretation of the radius-flux correlation for both continuum
and line emission.


5.1.2. Vertical extents


The comparison of vertical extents between gas and dust populations is not as well documented as the radial extent. For the comparison between the scattered light dust and the gas, we added
vertical size measurements of 3 Class II low inclination disks
from Avenhaus et al. (2018) and Pinte et al. (2018); GallowaySprietsma et al. (2025), respectively (Fig. 5d). Contrary to the
radial direction, a few disks are more extended vertically in scattered light than in gas, or close to _H_ gas ≈ _H_ dust, µm . We stress
again that both quantities represent the full vertical extension of
the two tracers, not their scale height. We can attribute these results to less evolved disks with the majority of small grains in
the upper layers of the disk. This is consistent with the finding
that grains as large as 10 µm are fully mixed to the gas up to the
disk surface in Tau 0420201 (Duchêne et al. 2024), for which
_H_ gas ≈ _H_ dust, µm However, this is surprising since the scattering
surface should shield the gas underneath from the stellar radiation, preventing photodissociation. On the other hand, the majority of disks are close to _H_ gas ≈ 2–3 _H_ dust, µm . This suggests that
the scattered light dust is not perfectly coupled to the gas and
some µm-size grains of the order of a few µm may have started
to settle toward the midplane. Alternatively, given its high optical
depth, CO self-shielding could result in an extended molecular
layer that reaches out above the scattered light surface. We did
not notice a different behavior between low and high inclinations


Article number, page 11 of 16

_A&A proofs:_ manuscript no. main



disks, although constraints on the vertical extent across a larger
sample of disks are needed.


However, we can see that the millimeter dust is clearly settled
in the midplane, indicating significant decoupling from the gas
(see Fig. 5e), much more pronounced than for the radial direction. The majority of the disks follow _H_ gas ≈ 3–6 _H_ dust,mm, indicator of strong dust settling. This fact has already been reported
(e.g. Villenave et al. 2020) when comparing thermal emission
and scattered light. Instead, here, we present the first quantitative
analysis by comparing directly gas and continuum on a significant sample of disks.


_5.2._ _Implications of dynamical masses_


In this subsection, we discuss implications of dynamical masses
on disks and stellar properties: gas and millimeter dust disk radius, aspect ratio ( _h_ / _r_ ) and spectral type. Despite significant uncertainties on the derived stellar masses, several notable trends
emerge from our survey.


5.2.1. Disk properties


No correlation is found between the stellar mass and the disk
size but one is found for the aspect ratio. The comparison between stellar mass and millimeter dust is shown in Fig. 7. According to a Pearson test, we found no correlation between the
stellar dynamical mass and the millimeter dust disk radius, with
a ≈ 62% confidence level, which is too low to claim any correlation. This is in agreement with previous studies on less inclined
disks (Hendler et al. 2020). Long et al. (2022) found a mild correlation between the gas disk radius and the stellar mass. However, we found that the gas size is even less correlated with the
dynamical mass than the dust size. This could be a consequence
of selection biases in either samples, but we also note that the
correlation found by Long et al. (2022) is driven by the lowmass end of their sample (M < 0.25 M ⊙ ), which our sample does

not cover.


Fig. 9 shows the stellar mass as a function of _h_ / _r_ ratio defined here as the ratio between the vertical and radial gas sizes.
As expected, we find an anti-correlation between the dynamical
mass and the h/r ratio with disks around higher mass stars thinner
than disks around lower mass stars. A Pearson test to check if the
dynamical mass and the aspect ratio is correlated indicates that
the two quantities seem anti-correlated with a ≈ 91% confidence
level and a correlation coefficient of _r_ = −0.49. Indeed, higher
mass stars have a stronger gravity pull, which tends to make the
disk thinner. More massive stars are also more luminous, resulting in hotter dust, and thus pushing up the gas scale height, i.e.,
making the disk thicker. However, for pre-main-sequence stars,
the effect of gravity is much steeper than that of luminosity, resulting in thinner disks around higher-mass stars (Walker et al.
2004; Angelo et al. 2023). We caution that the aspect ratio we
discuss here is based on the full height of the gas-emitting layer,
instead of its hydrostatic scale height. A thorough interpretation
of this anti-correlation will require full radiative transfer models
tailored to each system, as well as tomographic reconstruction of
their vertical temperature profile (e.g., Dutrey et al. 2017; Flores
et al. 2021), which is beyond the scope of this study. Finally,
there is no significant correlation between the disk radius (dust
and gas) and the aspect ratio.


Article number, page 12 of 16



5.2.2. Stellar properties


Fig. 8 displays the dynamical mass as a function of the spectral type. We also add measurements from Simon et al. (2019)
derived with the DiskFit package method (Piétu et al. 2007).
Our values are consistent with the reported trend of a decreasing dynamical mass for spectral type ranging from A2 to M4.75,
although there is a large scatter in the literature sample, suggestive of significant uncertainties. However, a few disks constitute outliers: the K6 multiple system HV Tau C, the M1 edge-on
system Tau 042021, as well as the M4.75 grazing-angle system
Tau 042307. Outliers might be due to an incorrect estimate of the
spectral type or an inaccurate estimation of the dynamical mass
linked to the limitation of the method in the highly inclined configuration in some cases.
By comparing our dynamical masses values with the ones
in the literature, when available, we found our values systematically higher than those of the literature by 30–50%, although
our values are consistent within uncertainties, at the exception
of Haro 6-5B (see Table 6). The dynamical mass estimated by
Yokogawa et al. (2002) for Haro 6-5B is significantly lower (0.25
M ⊙ as opposed to our estimate of 1.6 M ⊙ ), and seems incompatible with both our PV-diagrams (Fig. 3) and the K5 spectral
type of the system. However, we note that the dynamical masses
found for the edge-on disks in Simon et al. (2019) might not be
fully accurate because of the limitation of their method due to
projection effects when the two CO surfaces are well-separated.
Instead, this issue is irrelevant to our PV diagram analysis.


_5.3._ _Multiple systems_


The dust component of disks in multiple systems are expected
to be smaller than disks in single systems due to dynamical interactions with the disks companions (Manara et al. 2019), impacting planetary formation. However, we found no significant
difference between single and binary stars within our sample in
any tracer (see top panels of Fig. 7). Moreover, as mentioned in
Sect. 5.1, HV Tau C and HH 48 NE also appear radially smaller
in scattered light than in millimeter continuum which is surprising because their gas components are very extended. These small
sizes could be explained as the result of stronger radial drift of
µm-size grains than in single systems or to a shadowing effect.
Hydrodynamical models indicate that gas disks should be truncated at ≈ 30% of the companion separation (Artymowicz &
Lubow 1994; Zagaria et al. 2021). However, the binary separation is 2 [′′] . 32 for HK Tau (Rota et al. 2022), 5 [′′] . 4 for PDS 144 (Perrin et al. 2006), 4 [′′] . 04 for HV Tau (Duchêne et al. 2010) and 2 [′′] . 3
for HH 48 (Sturm et al. 2023). This implies that the gas radius of
the disk is below 30% of the separation for HK Tau and PDS 144
but is higher for HV Tau and HH 48. Thus, the small sizes of
these disks can not be explained by tidal truncation alone. This
has already been reported by Garufi et al. (2020). One possible
interpretation of the disks larger than their predicted truncationdriven size is that their real separation is much larger than the
separation projected on the sky. Another possible explanation
is more complex interactions. At each periastron passage, material can be stripped from the disk, leading to structures, such
as tails, that extend out to much larger distances (Cuello et al.
2025). We observe this in HH 48 and it could also be happening
in the HV Tau system. We also notice that HV Tau recently experienced a flyby by DO Tau (Howard et al. 2013), which could
also have stirred the HV Tau C disk. Moreover, according to Rota
et al. (2022) there is no evidence of correlation between the size
ratio and the projected separation, suggesting that there is no size

L. Martinien et al.: Observations of highly inclined disks with ALMA



100


10


100



80


70


60


50


40


30


0.01 0.1 1

Scaled Submillimeter Flux (Jy)


80


70


60


50


40


30


1 10


Scaled [12] CO 3-2 Line Flux (Jy km/s)



100


10


100



80


70


60


50


40


30


0.01 0.1 1

Inclination-Corrected Scaled Submillimeter Flux (Jy)


80


70


60


50


40


30


1 10 100


Inclination-Corrected Scaled [12] CO 3-2 Line Flux (Jy km/s)



**Fig. 6.** Disk radii measured in the ALMA continuum (top row) and [12] CO 3–2 line (bottom row) as a function of their submillimeter continuum
and line flux (scaled to 140 pc for uniformity), respectively. Small circles represent low- to moderate-inclination disks from the literature (Hendler
et al. 2020; Zallio et al. 2026) while large circles and squares are highly inclined disks from this study in single and multiple systems, respectively.
The disk inclination is color-coded. In the right column, the fluxes are further corrected for inclination, i.e., divided by cos( _i_ ), to account for their
projected shape.











|Tau 042021<br>Flying Saucer<br>ESO H𝜶569<br>Oph 163131<br>Lup 160708 HH 48 NE<br>Haro 6-5B<br>ESO H𝜶574<br>PDS144N<br>Lup 160703 HK Tau B<br>HV Tau C<br>Tau 042307<br>Oph 162305|Tau 042021<br>Flying Saucer<br>ESO H𝜶569<br>Oph 163131<br>Lup 160708 HH 48 NE<br>Haro 6-5B<br>ESO H𝜶574<br>PDS144N<br>Lup 160703 HK Tau B<br>HV Tau C<br>Tau 042307<br>Oph 162305|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|**Tau 042021**<br>**Lup 160708**<br>**Lup 160703**<br>**Tau 042307**<br>**HK Tau B**<br>**HH 48 NE**<br>**Haro 6-5B**<br>**Oph 163131**<br>**PDS 144 N**<br>**HV Tau C**<br>**ESO H**𝜶**574**<br>**ESO H**𝜶**569**<br>**Oph 162305**<br>**Flying Saucer**|**Tau 042021**<br>**Lup 160708**<br>**Lup 160703**<br>**Tau 042307**<br>**HK Tau B**<br>**HH 48 NE**<br>**Haro 6-5B**<br>**Oph 163131**<br>**PDS 144 N**<br>**HV Tau C**<br>**ESO H**𝜶**574**<br>**ESO H**𝜶**569**<br>**Oph 162305**<br>**Flying Saucer**|||||||


**Fig. 7.** Millimeter dust disk radius as a function of stellar mass.


dependence with the separation between components in the system. However, Rota et al. (2022) found that the ratio of the dust
to gas ratio in multiple stellar systems is lower compared to single stars, which is in agreement with what we found (see Fig.
5a).



**Fig.** **8.** Dynamical mass as a function of spectral type. We averaged
for objects which the spectral type is a range. The error bars represent
conservative (≈ 3σ) limits derived from our PV diagram analysis (see
Sect. 3.5).


We also estimated the dynamical masses as well as their
12 CO gas radial and vertical extents as we did for the primary


Article number, page 13 of 16

_A&A proofs:_ manuscript no. main


_5.4._ _Grazing-angle systems_













|PDS144N<br>HV Tau C<br>Oph 163131<br>Haro 6-5B<br>HH48NE<br>Oph 162305 ESO H𝜶574<br>HK Tau B<br>Flying Saucer<br>Lup 160708<br>ESO H𝜶569 Tau 042307<br>Tau 042021<br>Lup 160703|PDS144N<br>HV Tau C<br>Oph 163131<br>Haro 6-5B<br>HH48NE<br>Oph 162305 ESO H𝜶574<br>HK Tau B<br>lying Saucer<br>Lup 160708<br>ESO H𝜶569 Tau 042307<br>Tau 042021<br>Lup 160703|
|---|---|
|**Haro 6-5B**<br>**Lup 160708**<br>**Flying Saucer**<br>**ESO H**𝜶**574**<br>**Tau 042307**<br>**Lup 160703**<br>**Tau 042021**<br>**ESO H**𝜶**569**<br>**HV Tau C**<br>**Oph 163131**<br>**Oph 162305**<br>**PDS 144 N**<br>**HH 48 NE**<br>**HK Tau B**||


**Fig. 9.** Dynamical mass as a function of aspect ratio ( _h_ / _r_ ), which represents the vertical extent over the radial extent of [12] CO gas. Flying Saucer
is shown in gray to represent the low SNR (see Sect. 3) and is not included in the statistical test presented in Sect. 3.5 .


stars for all disk-hosting companions: HK Tau A, PDS 144 S and
HH 48 SW. All values are summarized in Appendix B. The primary star in a multiple system being the most massive component, we identify HK Tau B, HH 48 NE and PDS 144 N as the
primaries in their respective systems, although it is more debatable for the PDS 144 system because the two companions have
almost the same masses (see App. B.5). Given the spectral types
of the two components (A2 and A5 Vieira et al. 2003), we considered PDS 144 N as the primary. Primary stars generally host
brighter disks than their companions (Akeson et al. 2019; Manara et al. 2019), which is consistent with our findings — except for HK Tau, for which both the continuum and line flux are
brighter around the secondary. We also found that the millimeter dust radial extent is larger in the primary than in secondary
component, which is in agreement with Manara et al. (2019), as
is also the case for the [12] CO gas radial extent. However, this is
the opposite for the [12] CO gas vertical extent which is more extended in the secondary component than in the primary component, which could be due to a larger scale height due to the lower
stellar mass of the secondaries. Even though the disks around
companions are also highly inclined, there is no clear tendency
for coplanar disks in the systems studied here, which is expected
given their large separations (Jensen & Akeson 2014; Rota et al.
2022).


We also estimated an inclination of the disks around companions based on their millimeter continuum radial and vertical extents. Their inclinations also suggest highly inclined disks
(≳ 75 [◦] ), even though the star is directly visible in the optical/NIR, which suggest lower inclinations. Only the HK Tau A
disk has a moderate inclination in the mm. The fact that some
disks could appear highly inclined at millimeter wavelengths and
less inclined in scattered-light might be explained by a combination of a smaller scale height and a grazing-angle configuration
with an inclination a few degrees too low to fully obscure the
star. This can be confirmed in these systems with high-contrast
scattered light imaging of the disks around these companions.
Indeed, Garufi et al. (2026) recently presented the first scattered
light image with ground-based adaptive optics of PDS 144 S,
which is well aligned with the ALMA continuum and CO maps,
confirming its highly inclined nature.


Article number, page 14 of 16



The grazing-angle disks constitute a category of highly inclined
disks that is different from edge-on disks. Four disks in our sample present a grazing-angle geometry: Tau 042307, Haro 6-5B,
Lup 160703 and Lup 160708. Their millimeter continuum and
12 CO gas images are not as easy recognizable as in optical/NIR
image. However, as mentioned in Sect. 3 some distinguishable
features can be present in the grazing-angle disks images allowing to disentangle between the edge-on disks images.
These disks represent the best compromise between pole-on
disks and edge-on disks for which the radial and vertical structures, respectively, are accessible, allowing to study both the radial and the vertical structure of the continuum emission of disks.
The grazing-angle geometry also provides an ideal configuration to probe the vertical temperature gradient through the COemitting layer, as for less inclined disks (e.g., Pinte et al. 2018).
Indeed, the lower nebula appears fainter than the upper nebula
in optical/NIR due to the combination of the high optical depth
of the [12] CO line and the large vertical extent of, and temperature
gradient through, the CO-emitting layer. Therefore, since methods developed for edge-on disks are also applicable to these systems, grazing-angle disks can be used as benchmarks to bridge
the gap between pole-on and edge-on disks, ultimately providing
a global context.
Grazing-angle disks are also of great interest in the study
of ices because this geometry is the only one for which we can
observe both scattering and absorption components (Martinien
et al. 2024, 2025a,b), allowing an estimation of ices abundances.
Thus, they offer a unique opportunity – through modeling –
to compare the solid state, with James Webb Space Telescope
spectroscopic observations, and gaseous CO abundances, with
ALMA observations. This can address whether the two can be
co-located, i.e., partial sublimation. Unfortunately, high resolution, high SNR data are missing for most grazing angle for now.


**6.** **Conclusion**


This study presents a high-resolution gas and continuum survey
of highly inclined protoplanetary disks with ALMA. From these
observations, we perform a comparison of disks sizes in millimeter continuum, [12] CO gas and optical/NIR observations along the
radial and vertical direction, within a sample of highly inclined
disks. It also provides the first dynamical mass estimates for
most of the objects using the position–velocity diagram method.
Our conclusions are as follows:


1. Most of the radial disks sizes in our sample follow: _R_ gas _R_ dust, µm  - _R_ dust, mm, with the exception of 3 disks (including 2 in multiples systems) for which _R_ dust, mm is greater than
_R_ dust, µm . Highly inclined disks follow the same trend as less
inclined disks, albeit with a lower value of _R_ gas / _R_ dust, mm ≈
1.5–2. While this is broadly consistent with optical depth effects in disks with a uniform gas and dust mixture, we stress
that radial drift could nonetheless be active, especially in systems with _R_ dust, mm < _R_ dust, µm . Highly inclined disks provide
a more robust estimate of the outer disk radius because of
line-of-sight integration.
2. Along the vertical direction, all disks in our sample follow
_H_ gas » _H_ dust,mm . Most of disks follow _H_ gas  - _H_ dust, µm, but a
few disks follow _H_ gas ≊ _H_ dust, µm or even _H_ gas < _H_ dust, µm . This
suggests that the millimeter dust is vertically settled toward
the midplane, while the µm-sized dust is not fully coupled to
the gas.

L. Martinien et al.: Observations of highly inclined disks with ALMA



3. We revisited the long-known correlation between the size
and millimeter continuum and line emission of disks.
Highly-inclined disks are systematically fainter than disks at
lower inclinations, in a way that is consistent with the smaller
solid angle they subtend. This reinforces the idea that the
correlation is primarily a consequence of the fact that both
the continuum and line emission are optically thick in most
disks.
4. We found an anti-correlation between the dynamical mass
and the _h_ / _r_ ratio, consistent with the dominating effect of
gravity in setting the height of a disk, but no correlation between the dynamical mass and the disk radius.
5. We also studied the companions in multiple systems. Even
though they are directly visible in optical images, 2 of the 3
companions also host highly inclined disks (≳ 75 [◦] ), which
could be due to a tilt or a warp, easily induced in multiple
systems. The disk associated with the most massive component, always the edge-on disk component, are more radially
extended in all tracers. Conversely, disks around the lowermass components are more vertically extended in their gas
component but similarly thick in their continuum emission.
6. We can distinguish between edge-on and grazing-angle
disks, which can offer a unique viewing geometry, providing
the best compromise to study radial and vertical structure of
disks.


Higher resolution observations are needed to better constrain the dynamical masses and a larger sample is needed to
strengthen comparison between grazing-angle, edge-on and multiple systems among a sample of highly inclined disks. In this
context, the ongoing DiskStrat ALMA Large Program (Project
2024.1.01212.L, PI: R. Le Gal) will provide critical observations
to improve our characterization and understanding of highly inclined disks.


_Acknowledgements._ This project has received funding from the European Research Council (ERC) under the European Union’s Horizon Europe research and
innovation program (grant agreement No. 101053020, project Dust2Planets, PI:
F. Ménard). AR has received funding from the Royal Society through a University Research Fellowship grant number URF\R1\241791 and from the UK
Science and Technology research Council (STFC) via the consolidated grant
ST/W000997/1.


**References**


Akeson, R. L., Jensen, E. L. N., Carpenter, J., et al. 2019, ApJ, 872, 158
Andrews, S. M. 2020, ARA&A, 58, 483
Andrews, S. M., Terrell, M., Tripathi, A., et al. 2018, ApJ, 865, 157
Angelo, I., Duchene, G., Stapelfeldt, K., et al. 2023, ApJ, 945, 130
Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21
Artymowicz, P. & Lubow, S. H. 1994, ApJ, 421, 651
Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44
Barrière-Fouchet, L., Gonzalez, J.-F., Murray, J. R., Humble, R. J., & Maddison,
S. T. 2005, A&A, 443, 185
Benisty, M., Dominik, C., Follette, K., et al. 2023, in Astronomical Society of
the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 605
Birnstiel, T. & Andrews, S. M. 2014, ApJ, 780, 153
Cox, E. G., Harris, R. J., Looney, L. W., et al. 2017, ApJ, 851, 83
Cuello, N., Alaguero, A., & Poblete, P. P. 2025, Symmetry, 17, 344
Czekala, I., Andrews, S. M., Torres, G., et al. 2016, ApJ, 818, 156
Dartois, E., Noble, J. A., Caselli, P., et al. 2024, Nature Astronomy
Deng, D., Vioque, M., Pascucci, I., et al. 2025, ApJ, 989, 3
Duchêne, G., McCabe, C., Pinte, C., et al. 2010, ApJ, 712, 112
Duchêne, G., Ménard, F., Stapelfeldt, K. R., et al. 2024, AJ, 167, 77
Dutrey, A., Denis-Alpizar, O., Guilloteau, S., et al. 2025, arXiv e-prints,
arXiv:2509.26033
Dutrey, A., Guilloteau, S., Piétu, V., et al. 2017, A&A, 607, A130
Facchini, S., Birnstiel, T., Bruderer, S., & van Dishoeck, E. F. 2017, A&A, 605,
A16



Flores, C., Duchêne, G., Wolff, S., et al. 2021, AJ, 161, 239
Galloway-Sprietsma, M., Bae, J., Izquierdo, A. F., et al. 2025, ApJ, 984, L10
Garufi, A., Avenhaus, H., Pérez, S., et al. 2020, A&A, 633, A82
Garufi, A., Ginski, C., Benisty, M., et al. 2026, arXiv e-prints, arXiv:2603.01703
Hendler, N., Pascucci, I., Pinilla, P., et al. 2020, ApJ, 895, 126
Hernández, J., Hartmann, L., Calvet, N., et al. 2008, ApJ, 686, 1195
Hornbeck, J. B., Grady, C. A., Perrin, M. D., et al. 2012, ApJ, 744, 54
Howard, C. D., Sandell, G., Vacca, W. D., et al. 2013, ApJ, 776, 21
Jensen, E. L. N. & Akeson, R. 2014, Nature, 511, 567
Johansen, A. & Youdin, A. 2007, ApJ, 662, 627
Kirchschlager, F., Wolf, S., & Madlener, D. 2016, MNRAS, 462, 858
Laibe, G., Gonzalez, J.-F., Maddison, S. T., & Crespe, E. 2014, MNRAS, 437,
3055

Lambrechts, M. & Johansen, A. 2012, A&A, 544, A32
Long, F., Andrews, S. M., Rosotti, G., et al. 2022, ApJ, 931, 6
Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120
Luhman, K. L. 2007, ApJS, 173, 104
Luhman, K. L., Allen, P. R., Espaillat, C., Hartmann, L., & Calvet, N. 2010,
ApJS, 186, 111
Luhman, K. L., Mamajek, E. E., Allen, P. R., & Cruz, K. L. 2009, ApJ, 703, 399
Manara, C. F., Tazzari, M., Long, F., et al. 2019, A&A, 628, A95
Martinien, L., Duchêne, G., Ménard, F., et al. 2025a, A&A, 704, L17
Martinien, L., Duchêne, G., Ménard, F., Tazaki, R., & Stapelfeldt, K. R. 2025b,
A&A, 696, L6
Martinien, L., Ménard, F., Duchêne, G., et al. 2024, A&A, 692, A111
McCabe, C., Duchêne, G., Pinte, C., et al. 2011, ApJ, 727, 90
Monin, J. L., Menard, F., & Duchene, G. 1998, A&A, 339, 113
Muži´c, K., Scholz, A., Geers, V. C., Jayawardhana, R., & López Martí, B. 2014,
ApJ, 785, 159
Perrin, M. D., Duchêne, G., Kalas, P., & Graham, J. R. 2006, ApJ, 645, 1272
Piétu, V., Dutrey, A., & Guilloteau, S. 2007, A&A, 467, 163
Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJ, 860, L13
Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka,
Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645
Pollack, J. B., Hubickyj, O., Bodenheimer, P., et al. 1996, Icarus, 124, 62
Ribas, Á., Bouy, H., & Merín, B. 2015, A&A, 576, A52
Rosenfeld, K. A., Andrews, S. M., Wilner, D. J., & Stempels, H. C. 2012, ApJ,
759, 119
Rota, A. A., Manara, C. F., Miotello, A., et al. 2022, A&A, 662, A121
Sanchis, E., Testi, L., Natta, A., et al. 2021, A&A, 649, A19
Simon, M., Guilloteau, S., Beck, T. L., et al. 2019, ApJ, 884, 42
Stapelfeldt, K. R., Duchêne, G., Perrin, M., et al. 2014, in IAU Symposium,
Vol. 299, Exploring the Formation and Evolution of Planetary Systems, ed.
M. Booth, B. C. Matthews, & J. R. Graham, 99–103
Stapelfeldt, K. R., Krist, J. E., Ménard, F., et al. 1998, ApJ, 502, L65
Sturm, J. A., McClure, M. K., Law, C. J., et al. 2023, A&A, 677, A17
Tazaki, R., Ménard, F., Duchêne, G., et al. 2025, ApJ, 980, 49
Teague, R. & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173
Trapman, L., Facchini, S., Hogerheijde, M. R., van Dishoeck, E. F., & Bruderer,
S. 2019, A&A, 629, A79
Trapman, L., Vioque, M., Kurtovic, N. T., et al. 2025, ApJ, 989, 10
Tripathi, A., Andrews, S. M., Birnstiel, T., & Wilner, D. J. 2017, ApJ, 845, 44
Vieira, S. L. A., Corradi, W. J. B., Alencar, S. H. P., et al. 2003, AJ, 126, 2971
Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164
Villenave, M., Stapelfeldt, K. R., Duchêne, G., et al. 2022, ApJ, 930, 11
Vioque, M., Kurtovic, N. T., Trapman, L., et al. 2025, ApJ, 989, 9
Walker, C., Wood, K., Lada, C. J., et al. 2004, MNRAS, 351, 607
Weidenschilling, S. J. 1977, Ap&SS, 51, 153
Wolff, S. G., Duchêne, G., Stapelfeldt, K. R., et al. 2021, AJ, 161, 238
Wolff, S. G., Perrin, M. D., Stapelfeldt, K., et al. 2017, The Astrophysical Journal, 851, 56
Yokogawa, S., Kitamura, Y., Momose, M., & Kawabe, R. 2002, in 8th AsianPacific Regional Meeting, Volume II, ed. S. Ikeuchi, J. Hearnshaw, &
T. Hanawa, 239–240
Youdin, A. N. & Goodman, J. 2005, ApJ, 620, 459
Zagaria, F., Facchini, S., Miotello, A., et al. 2023, A&A, 672, L15
Zagaria, F., Rosotti, G. P., & Lodato, G. 2021, MNRAS, 504, 2235
Zallio, L., Rosotti, G. P., Vioque, M., et al. 2026, A&A, 705, A49
Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2020, A&A, 633, A51


Article number, page 15 of 16

**Appendix A:** **Beam sizes**



_A&A proofs:_ manuscript no. main


**Table B.2.** Disks parameters of the companions.



We present the beam sizes obtained for the observations in Table
A.1.


**Table A.1.** Beam sizes of our observations.


Sources Continuum 12 CO
FWHM ( [′′] ) PA (°) FWHM ( [′′] ) PA (°)
Flying Saucer 0.14 × 0.07 -77.5 0.14 × 0.07 -77.3
PDS 144 N 0.16 × 0.06 -75.6 0.18 × 0.07 -73.9
Oph 162305 0.11 × 0.05 -78.0 0.14 × 0.07 -76.0
Lup 160703 0.10 × 0.07 -80.1 0.12 × 0.08 -80.6
Lup 160708 0.10 × 0.07 -82.7 0.12 × 0.08 -80.9
HK Tau B 0.11 × 0.07 3 0.13 × 0.12 79.7

HV Tau C 0.11 × 0.08 4 0.14 × 0.13 78.0

Haro 6-5B 0.12 × 0.07 -19 0.15 × 0.14 -32.8

Tau 042307 0.11 × 0.07 -8 0.24 × 0.22 -76.1

Tau 042021 0.12 × 0.08 -13 0.26 × 0.24 -77.8

ESO Hα 569 0.48 × 0.28 -8 0.50 × 0.30 -10.4

ESO Hα 574 0.47 × 0.28 -10 0.49 × 0.30 -11.7

HH 48 NE 0.48 × 0.28 -5 0.52 × 0.31 -8.3
Oph 163131 0.48 × 0.28 -70 0.08 × 0.07 88.9


**Notes.** All observations are in Band 7 except Oph 163131 which are in
Band 6.


**Appendix B:** **Parameters of disk-hosting**
**companions**


We performed the same analyses on the disk-hosting companions of the multiple systems as we did for the objects in our
main sample. The continuum and line fluxes are listed in Table
B.1. The position angles and inclinations are summarized in Table. B.2. The major axis sizes as well as the minor axis sizes are
listed in Table B.3 and B.4, respectively. The PV diagrams are
presented in Fig. B.1. Finally, the estimated systemic velocities
as well as dynamical stellar masses are presented in Table B.5.


**Table B.1.** ALMA fluxes of the companions.


Sources Continuum flux 12 CO (3-2) line flux
(mJy) (Jy km s [−][1] )
PDS 144 S 57.0 ± 5.7 2.1 ± 0.2

HK Tau A 74.6 ± 7.5 2.0 ± 0.2

HH 48 SW 58.0 ± 5.8 4.6 ± 0.4


Article number, page 16 of 16



Sources PA _i_ AxisRatio _i_ _literature_
( [◦] ) ( [◦] ) ( [◦] )
PDS 144 S 35 >74 73 ± 7 _[a]_

HK Tau A 178 >54 63.1 ± 1.5 _[b]_

HH 48 SW 4 >75    
**References** . _[a]_ Hornbeck et al. (2012), _[b]_ Simon et al.
(2019).


**Table** **B.3.** Major axis diameters measurements from the ALMA continuum, ALMA [12] CO and HST scattered light observations.


Sources ALMA HST ALMA
continuum scattered 12 CO
( [′′] ) ( [′′] ) ( [′′] )
PDS 144 S 0.85 ± 0.05 unresolved 1.38 ± 0.10

HK Tau A 0.61 ± 0.05 unresolved 1.33 ± 0.10

HH 48 SW 1.37 ± 0.07 unresolved 3.61 ± 0.11


**Table B.4.** Minor axis sizes measurements from the ALMA continuum,
ALMA [12] CO and HST-VLT scattered light observations.


Sources ALMA HST ALMA
continuum scattered 12 CO
( [′′] ) ( [′′] ) ( [′′] )
PDS 144 S 0.12 ± 0.03 unresolved 0.68 ± 0.02

HK Tau A 0.14 ± 0.01 unresolved 0.56 ± 0.02

HH 48 SW 0.17 ± 0.01 unresolved 1.64 ± 0.06


**Notes.** See Sect. 3.4 and 4.3 for definitions of the three quantities.


**Fig.** **B.1.** Position-velocity diagrams of the companions with 3 Keplerian velocity curves corresponding to the preferred dynamical mass of
the star, as well as conservative upper and lower limits.


**Table** **B.5.** Systemic velocities and dynamical masses from this work
and from the literature.


Sources V _sys_ M ⋆ M ⋆ _literature_
(km s [−][1] ) (M⊙) (M⊙)
PDS 144 S 3.5 2.0 (1.3..2.6)   HK Tau A 6.0 0.6 (0.3..1.0) 0.53 ± 0.03 _[a]_
HH 48 SW 4.8 0.9 (0.5..2.0)  

**References** . _[a]_ Simon et al. (2019).


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[14].redshift_or_distance.evidence[0]",
  "value": "140 pc",
  "failed_quote": "We also estimated the dynamical masses as well as their 12 CO gas radial and vertical extents as we did for the primary stars for all disk-hosting companions: HK Tau A, PDS 144 S and HH 48 SW."
 },
 {
  "path": "science.targets[14].distance_source.evidence[0]",
  "value": "Zucker et al. (2020)",
  "failed_quote": "We also estimated the dynamical masses as well as their 12 CO gas radial and vertical extents as we did for the primary stars for all disk-hosting companions: HK Tau A, PDS 144 S and HH 48 SW."
 },
 {
  "path": "science.targets[15].redshift_or_distance.evidence[0]",
  "value": "130 pc",
  "failed_quote": "We also estimated the dynamical masses as well as their 12 CO gas radial and vertical extents as we did for the primary stars for all disk-hosting companions: HK Tau A, PDS 144 S and HH 48 SW."
 },
 {
  "path": "science.targets[15].distance_source.evidence[0]",
  "value": "Zucker et al. (2020)",
  "failed_quote": "We also estimated the dynamical masses as well as their 12 CO gas radial and vertical extents as we did for the primary stars for all disk-hosting companions: HK Tau A, PDS 144 S and HH 48 SW."
 },
 {
  "path": "science.targets[16].redshift_or_distance.evidence[0]",
  "value": "190 pc",
  "failed_quote": "We also estimated the dynamical masses as well as their 12 CO gas radial and vertical extents as we did for the primary stars for all disk-hosting companions: HK Tau A, PDS 144 S and HH 48 SW."
 },
 {
  "path": "science.targets[16].distance_source.evidence[0]",
  "value": "Zucker et al. (2020)",
  "failed_quote": "We also estimated the dynamical masses as well as their 12 CO gas radial and vertical extents as we did for the primary stars for all disk-hosting companions: HK Tau A, PDS 144 S and HH 48 SW."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Generate moment 0 and moment 1 maps from the 12CO image cubes using bettermoments with 3-sigma clipping.",
  "failed_quote": "We constructed the moment maps using the bettermoments package developed by Teague & Foreman-Mackey (2018), applying a 3σ clipping."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "3-sigma clipping",
  "failed_quote": "We constructed the moment maps using the bettermoments package developed by Teague & Foreman-Mackey (2018), applying a 3σ clipping."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Extract surface brightness profiles along the major axis integrated over the vertical extent and normalized by peak intensity. For 12CO, visually select the channel with maximum radial extent on blue and red sides in the image cube. Measure diameter at 3-sigma above background noise.",
  "failed_quote": "To measure the radial extent of the disks from their continuum emission we extracted surface brightness profiles along the major axis of each disk. We integrated over the full vertical extent of the disk and normalized by the maximum intensity."
 },
 {
  "path": "analysis_steps[4].method.evidence[2]",
  "value": "Construct position-velocity (PV) diagrams and superimpose 3 Keplerian velocity curves (fitting outermost maximum intensity for lower limit, signal-to-noise transition for preferred mass, and off-signal for upper limit) while visually aligning systemic velocity symmetrically.",
  "failed_quote": "We visually estimated the systemic velocity so that the Keplerian curves were symmetrically aligned with the PV diagrams."
 },
 {
  "path": "analysis_steps[5].fitting.evidence[0]",
  "value": "Mann-Whitney U test, Kolmogorov-Smirnov test, and Pearson correlation test",
  "failed_quote": "The Mann-Whitney U test, most sensitive to the median value of each sample, yields a ≈90% confidence level that the two populations are intrinsically different. Similarly, the Kolmogorov-Smirnov test, which is more sensitive to the shape of the underlying distribution, yields a 93% confidence level."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Constructing 12CO moment 0 and moment 1 maps with 3-sigma clipping",
  "failed_quote": "We constructed the moment maps using the bettermoments package developed by Teague & Foreman-Mackey (2018), applying a 3σ clipping."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "Lup 160708 and Haro 6-5B show ring geometries in continuum and vertical-only emission in PV diagrams.",
  "failed_quote": "We note that two disks only contain information along the vertical direction in their PV diagrams (Haro 6-5B and Lup 160708). This can be the tracer of a ring geometry (Dutrey et al. 2017), which is confirmed in the millimeter continuum image of Lup 160708 (see Fig. 1) and Haro 6-5B (Villenave et al. 2020)."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "Most disks follow R_gas > R_dust,um > R_dust,mm, and highly inclined disks show smaller gas-to-mm-dust radius ratios than less inclined disks due to line-of-sight integration enhancing outer mm continuum detection, consistent with optical depth effects and/or radial drift.",
  "failed_quote": "However, the highly inclined disks tend to have smaller gas-to-dust radius ratios, and appear closer to R gas ≈ 1.5–2 × R dust, mm ."
 },
 {
  "path": "claims[0].evidence[2]",
  "value": "Most disks follow R_gas > R_dust,um > R_dust,mm, and highly inclined disks show smaller gas-to-mm-dust radius ratios than less inclined disks due to line-of-sight integration enhancing outer mm continuum detection, consistent with optical depth effects and/or radial drift.",
  "failed_quote": "The Mann-Whitney U test, most sensitive to the median value of each sample, yields a ≈90% confidence level that the two populations are intrinsically different. Similarly, the Kolmogorov-Smirnov test, which is more sensitive to the shape of the underlying distribution, yields a 93% confidence level."
 }
]
```
