# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...680A.110C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#  Radio outburst from a massive (proto)star

# Introduction

In recent years, observations have provided us with increasing evidence of circumstellar rotating structures around B-type (proto)stars, especially since the advent of the Atacama Large Millimeter/submillimeter Array (ALMA; see e.g. the review by Beltrán & de Wit (cite: beldew)). This strongly suggests that disk-mediated accretion could be a viable mechanism to feed even the most massive stars. However, we still do not understand the physical properties of these rotating structures, nor how such an accretion proceeds, whether through a smooth, continuous flow or episodically with parcels of material falling onto the star. The recent detection of outbursts (Stecklum (cite: steck16; steck21); Caratti o Garatti et al. (cite: cagana); Hunter et al. (cite: hunt17; hunt21); Burns et al. (cite: burns20; burns23); Chen et al. (cite: chen21)) in a few luminous young stellar objects (YSOs) $>$8 $M_\odot$ provides us with the intriguing possibility that these phenomena could be the consequence of episodic accretion events, akin to those commonly observed in low-mass YSOs as FU Orionis and EX Orionis events (Audard et al. (cite: aud); Fischer et al. (cite: fischppvii)).

In this study we focus on the outburst from the massive (proto)star S255IR NIRS 3, located at a distance of $1.78^{+0.12}_{-0.11}$ kpc (Burns et al. (cite: burns16)). This object is unique because the outburst has been observed not only in the emission of some maser species (Fujisawa et al. (cite: fuji); Moscadelli et al. (cite: mosca17); Hirota et al. (cite: hiro21)) and in lines and continua at IR and (sub-)millimetre wavelengths (Caratti o Garatti et al. (cite: cagana); Uchiyama et al. (cite: uchi); Liu et al. (cite: liu18)), but also in the centimetre domain (Cesaroni et al. (cite: cesa18); hereafter Paper I). A time delay of $\sim$1 yr was found between the onset of the IR and radio outbursts, consistent with the different mechanisms at the origin of the two: in fact, the IR outburst is based on radiative processes propagating at velocities comparable to the speed of light, whereas the radio outburst is due to shocks expanding approximately at the speed of sound. In Paper I we present compelling evidence of an exponential increase in the radio emission from the thermal jet associated with this source. Given the existence of a disk-jet system in S255IR NIRS 3 (Boley et al. (cite: bole13); Wang et al. (cite: wang); Zinchenko et al. (cite: zin15); Liu et al. (cite: liu20)), we believe that we are witnessing an episodic accretion event mediated by the disk, where part of the infalling material has been diverted into the associated jet (Fedriani et al. (cite: fedr23)). In Paper I we show that a simple model of an expanding jet can satisfactorily reproduce the increase in the radio flux observed in four bands. Although the emission was basically unresolved, we predicted that in a few years the jet expansion should make it possible to resolve its structure. With this in mind, we performed both monitoring of the radio emission and sub-arcsecond millimetre imaging at two epochs, several years after the beginning of the outburst. In this article we report on the results of these observations.

# Observations

The radio emission was monitored with the *Karl G. Jansky* Very Large Array (VLA) and, at a later time, with ALMA. In the following we describe the observational setup and data reduction separately for the two datasets. In both cases, for the phase centre we chose the position $\alpha$(J2000)=$06^{\rm h}\,12^{\rm m}\,54.02s$, $\delta$(J2000)=17$^\circ$ 59$'$ 23.1$''$.

## Very Large Array

S255IR NIRS 3 was observed at 11 epochs from January 2017 to January 2018 (project codes: 16B-427 and 17B-045). The observing dates and array configurations are listed in Table [\[tflux\]](#tflux), where for the sake of completeness we have also included the 2016 data already presented in Paper I. We note that the table contains as yet unpublished data in the L band obtained in the same observing run (project 16A-424) described in Paper I.

The signal was recorded with the Wideband Interferometric Digital ARchitecture (WIDAR) correlator in six bands, centred approximately at 1.5 (L band), 3 (S), 6 (C), 10 (X), 22.2 (K), and 45.5 GHz (Q), in dual polarisation mode. The total observing bandwidth (per polarisation) was 1 GHz in the L band, 2 GHz in the S band, 4 GHz in the C and X bands, and 8 GHz in the K and Q bands. The primary flux calibrator was 3C48 and the phase-calibrators were J0632+1022 in the L and S bands, J0559$+$2353 in the C and X bands, and J0539+1433 in the K and Q bands.

We made use of the calibrated dataset provided by the NRAO pipeline and subsequent inspection of the data and imaging were performed with the CASA[^2] package, version 5.6.2-2. The continuum images were constructed using natural weighting to maximise flux recovery. Typical values of the 1$\sigma$ RMS noise level and synthesised beam are given in Table [1](#tnoise) for each band and array configuration.

+-----------------+---+----------------------------------------------------+
| year:           |   | 2016$^a$                                           |
+:===============:+:=:+:======:+:======:+:=====:+:======:+:======:+:======:+
| 1-1 date:       |   | Mar 11 | Jul 10 | Aug 1 | Oct 15 | Nov 20 | Dec 27 |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| days:           |   | –121   | 0      | 22    | 97     | 133    | 170    |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| array:          |   | C      | B      | B     | A      | A      | A      |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 1-1 $\nu$ (GHz) |   | $S_\nu$ (mJy)                                      |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 1-1 1.5         |   | —      | —      | —     | 3.58   | 3.3    | 4.7    |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 3.0             |   | —      | —      | —     | —      | —      | —      |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 6.0             |   | 0.87   | 0.79   | 1.1   | 2.63   | 4.8    | 7.9    |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 10.0            |   | 1.0    | 1.2    | 1.8   | 3.49   | 6.7    | 11.0   |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 22.2            |   | 2.7    | 2.2    | 3.1   | 6.58   | 11.3   | 17.6   |
+-----------------+---+--------+--------+-------+--------+--------+--------+
| 45.5            |   | 4.4    | 1.9    | 3.8   | 13.6   | 21.3   | 26.8   |
+-----------------+---+--------+--------+-------+--------+--------+--------+

$^a$ Data acquired in 2016 at $\nu\ge6$ GHz have already been reported by Cesaroni et al. ((cite: cesa18)) and are listed here for the sake of completeness.\

+-----------------+---+-------------------------------------------------------------------------------------------------------------+
| year:           |   | 2017                                                                                                        |
+:===============:+:=:+:========:+:========:+:========:+:========:+:========:+:========:+:========:+:========:+:========:+:========:+
| 1-1 date:       |   | Jan 26   | Mar 3    | Mar 19   | Jul 29   | Aug 19   | Aug 25   | Sep 17   | Oct 23   | Dec 8    | Dec 27   |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| days:           |   | 200      | 236      | 252      | 384      | 405      | 411      | 434      | 470      | 516      | 535      |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| array:          |   | A        | D        | D        | C        | C        | C        | B        | B        | B        | B        |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 1-1 $\nu$ (GHz) |   | $S_\nu$ (mJy)$^b$                                                                                           |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 1-1 1.5         |   | 3.9      | $<$8.5   | $<$14.9  | $<$14.2  | $<$17.4  | $<$10.8  | $<$7.5   | $<$9.3   | $<$8.7   | $<$7.3   |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 3.0             |   | 6.1      | $<$9.9   | $<$13.8  | $<$11.2  | $<$14.1  | $<$13.4  | 14.6     | 14.7     | 14.5     | 13.4     |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 6.0             |   | 8.1      | 9.2$^c$  | 10.0$^c$ | 14.3     | 16.3     | 16.1     | 17.7     | 18.5     | 16.9     | 17.4     |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 10.0            |   | 11.4     | 12.8$^d$ | 12.8$^d$ | 20.9     | 22.3     | 22.6     | 24.0     | 23.1     | 22.7     | 22.7     |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 22.2            |   | 20.4     | 20.7     | 22.8     | 30.0     | 34.0     | 36.8     | 29.5     | 29.5     | 27.6     | 26.9     |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+
| 45.5            |   | 26.8     | 28.9     | 34.5     | 35.9     | 44.1     | 45.3     | 26.0     | 28.3     | 24.2     | 23.3     |
+-----------------+---+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------+

$^b$ The symbol ‘$<$’ indicates that the value also includes the contribution from the two large-scale lobes, due to insufficient angular resolution.\
$^c$ Corrected by subtracting a fiducial value of 1.8 mJy for the two large-scale lobes (see main text).\
$^d$ Corrected by subtracting a fiducial value of 1.0 mJy for the two large-scale lobes (see main text).\

+-----------------+---+----------------------------------+---+-----------------+---+-----------------+---+---+
| year:           |   | 2018                             |   | 2019            |   | 2021            |   |   |
+:===============:+:=:+:==========:+:========:+:========:+:=:+:===============:+:=:+:===============:+:=:+:=:+
| 1-1 date:       |   | Jan 15     | Mar 29   | May 5    |   | Jun 6           |   | Sep 3           |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| days:           |   | 554        | 627      | 664      |   | 1061            |   | 1881            |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| array:          |   | B          | A        | A        |   | C43-9/10        |   | C43-9/10        |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 1-1 $\nu$ (GHz) |   | $S_\nu$ (mJy)                    |   | $S_\nu$ (mJy)   |   | $S_\nu$ (mJy)   |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 1-1 1.5         |   | $<$6.9$^b$ | —        | —        |   | —               |   | —               |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 3.0             |   | 13.3       | —        | —        |   | —               |   | —               |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 6.0             |   | 16.8       | 15.1$^e$ | —        |   | —               |   | —               |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 10.0            |   | 22.2       | —        | —        |   | —               |   | —               |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 22.2            |   | 25.0       | —        | 24.7$^e$ |   | —               |   | —               |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 45.5            |   | 23.3       | —        | —        |   | —               |   | —               |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+
| 92.2            |   | —          | —        | —        |   | 46.0 (22.8)$^f$ |   | 42.3 (18.8)$^f$ |   |   |
+-----------------+---+------------+----------+----------+---+-----------------+---+-----------------+---+---+

$^e$ From Obonyo et al. ((cite: obonyo)).\
$^f$ The value in parentheses is the flux density of the NE lobe only (see Sect. [4.1](#smmem)).\
Note: The row labelled with ‘days’ gives the number of days after the beginning of the radio burst. The error on the flux densities is estimated to be $\sim$10% (see main text).

The flux density of the compact, variable source centred on S255IR NIRS 3 has been estimated inside a polygonal shape encompassing the compact, unresolved radio source and is given in Table [\[tflux\]](#tflux) for each band and epoch. As explained in Paper I, in our VLA observations the continuum emission from S255IR NIRS 3 appears as an unresolved component (the variable source of interest for our study) plus two large-scale lobes separated by $\sim$8$''$, or $\sim$15000 au, in projection (see Fig. 1 of Paper I) that in all likelihood are originating from a previous outburst that occurred many decades ago. At the longest wavelengths it was possible to resolve the central source from the lobes only in the most extended array configuration. In the other cases, we could only measure the total flux density from all components and the corresponding values are reported in Table [\[tflux\]](#tflux) as upper limits. In a few cases, as indicated in the footnotes of the table, we attempted a correction to the flux, under the assumption that the flux of the lobes is constant in time and thus equal to the value measured (at a different epoch) with the A array. With this approach a caveat is in order, because a compact configuration may be sensitive to lobe structures that are resolved out in a more extended configuration. This implies that the corrected flux densities could be still an upper limit.

In order to estimate the uncertainty on the flux density measurements of S255IR NIRS 3, we took advantage of the presence of a compact, marginally resolved continuum source located approximately at $\alpha$(J2000)=$06^{\rm h}\,12^{\rm m}\,53.61s$, $\delta$(J2000)=18$^\circ$ 00$'$ 26.4$''$, which happens to fall in the primary beam in all bands except band Q. Under the reasonable assumption that this object is not variable, by comparing the flux density measurements obtained at different epochs at the same frequency, we estimated a relative error of 10% in all bands.

## Atacama Large Millimeter/submillimeter Array

S255IR NIRS 3 was observed with ALMA in band 3 on June 6, 2019, and September 3, 2021 (project 2018.1.00864.S, P.I. R. Cesaroni). The main characteristics of the observations are summarised in Table [2](#talma). The correlator was configured with 4 units of 2 GHz, in double polarisation, centred at 85.2, 87.2, 97.2, and 99.2 GHz. The spectral resolution is 0.49 MHz (corresponding to $\sim$1.5–1.7 km s$^{-1}$, depending on the frequency), sufficient to identify line-free channels and obtain a measurement of the continuum emission.

The data were calibrated through the ALMA data reduction pipeline. For each 2 GHz correlator unit, we created a data cube using task *tclean* of CASA, adopting natural weighting and a circular beam of 0.097$''$ for the first epoch and 0.087$''$ for the second one. To create a continuum map for each 2 GHz band, we used the STATCONT software[^3] developed by Sánchez-Monge et al. ((cite: statcont)). In this way we also obtained cubes of the continuum-subtracted line emission. Finally, the four continuum maps were averaged together to increase the signal-to-noise ratio. The measured fluxes at the two epochs are reported in Table [\[tflux\]](#tflux).

We note that the derivation of the continuum images described above also provides us with continuum-subtracted channel maps. Although a study of the line emission in this region goes beyond the purposes of this article, in the following we briefly consider the maps of two molecular transitions, SO(2$_2$–1$_1$) at 86093.983 MHz and H$^{13}$CN(1–0) at 86338.7 MHz.

+:-----------------:+:---------:+:--------:+:--------:+:--------:+
| band – $\nu$(GHz) | noise, beam                                |
+-------------------+--------------------------------------------+
|                   | ($\mu$Jy/beam), (arcsec)                   |
+-------------------+-----------+----------+----------+----------+
| 2-5               | A         | B        | C        | D        |
+-------------------+-----------+----------+----------+----------+
| L – 1.5           | 84, 1.4   | 53, 4.7  | 148, 15  | 662, 44  |
+-------------------+-----------+----------+----------+----------+
| S – 3             | 27, 0.69  | 31, 2.3  | 68, 7.2  | 347, 23  |
+-------------------+-----------+----------+----------+----------+
| C – 6             | 11, 0.37  | 24, 1.2  | 67, 3.8  | 693, 12  |
+-------------------+-----------+----------+----------+----------+
| X – 10            | 8, 0.21   | 14, 0.71 | 37, 2.3  | 342, 7.7 |
+-------------------+-----------+----------+----------+----------+
| K – 22.2          | 16, 0.094 | 19, 0.36 | 36, 1.1  | 111, 3.4 |
+-------------------+-----------+----------+----------+----------+
| Q – 45.5          | 81, 0.061 | 42, 0.20 | 51, 0.57 | 102, 1.9 |
+-------------------+-----------+----------+----------+----------+

:  Typical 1$\sigma$ RMS noise and synthesised beam for different bands and VLA configurations.

|        date         |    2019/6/6     |    2021/9/3     |
|:-------------------:|:---------------:|:---------------:|
|    configuration    |    C43-9/10     |    C43-9/10     |
|      antennae       |       43        |       47        |
|    baselines (m)    |    237–1524     |    122–1619     |
|      flux cal.      |   J0750+1231    |   J0750+1231    |
|    bandpass cal.    |   J0750+1231    |   J0750+1231    |
|     phase cal.      |   J0613+1708    |   J0613+1708    |
|  synthesised beam   |    0.097$''$    |    0.087$''$    |
| 1$\sigma$ RMS noise | 50 $\mu$Jy/beam | 30 $\mu$Jy/beam |

:  Main parameters of the ALMA observations.

# Results

## Continuum emission at $\lambda=3$ mm

![](3mm_maps.eps)

![](so_h13cn.eps)

The structure of the radio jet from S255IR NIRS 3 at the two epochs observed with ALMA is shown in Fig. [1](#falma). The most striking result is the clear expansion of the jet, which becomes significantly more elongated to both the NE and SW. At first look, the figure seems to outline a bipolar structure, where the star might be located close to the geometrical centre, between the two jet lobes. However, this is not the case. Careful comparison between Fig. [1](#falma)a and [1](#falma)b reveals that, while the NE peak is moving away from the centre, the SW peak stays still, consistent with this being the location of the (proto)star. This result is confirmed by the coincidence of the SW peak with the peak of the sub-millimetre emission (white cross) measured by Liu et al. ((cite: liu20)), as expected if the (proto)star lies inside the parental molecular, dusty core. Figure [2](#fmols) clearly confirms this scenario by showing an overlay of the molecular emission maps of the SO(2$_2$–1$_1$) and H$^{13}$CN(1–0) lines observed by us, with an image of the 3 mm continuum emission. It is worth noting that in both transitions a dip is seen towards the continuum peak, which suggests that part of the line emission is likely absorbed against the bright continuum. This is consistent with the high brightness temperature of both 3 mm continuum peaks, of the order of 500 K (obtained from the maps cleaned with uniform weighting).

With all the above in mind, in the following we assume that the (proto)star powering the radio jet is located at the SW peak of the 3 mm continuum emission, namely at $\alpha$(J2000)=$06^{\rm h}\,12^{\rm m}\,54.012s$, $\delta$(J2000)=17$^\circ$ 59$'$ 23.04$''$. We prefer to use the peak position of our maps instead of that of the sub-millimetre maps of Liu et al. ((cite: liu20)), because of the higher angular resolution (0.087$''$ instead of 0.14$''$).

|     tracer     |       size        |     PA     |              ref.              |
|:--------------:|:-----------------:|:----------:|:------------------------------:|
| $^{12}$CO(2–1) | 40$''$ (0.35 pc)  | 75$^\circ$ |   Wang et al. ((cite: wang))   |
|    cm cont.    |  8$''$ (0.07 pc)  | 70$^\circ$ |            Paper I             |
|    mm cont.    | 0.6$''$ (1000 au) | 48$^\circ$ |           this paper           |
| H$_2$O masers  | 0.5$''$ (900 au)  | 44$^\circ$ | Hirota et al. ((cite: hiro21)) |

:  Position angles of the jet outflow from S255IR NIRS 3 in different tracers.

It is also interesting to compare the jet lobes observed in our ALMA maps with those seen on a much larger scale (see Fig. 1 of Paper I). The comparison is presented in Fig. [3](#fjets), where we show the maps of the 3.6 cm and 3 mm continuum emission. Clearly, the directions of the symmetry axes of the two pairs of lobes are remarkably different, with position angle (PA) of $\sim$70$^\circ$, on the large scale, and $\sim$48$^\circ$, on the small scale. The fact that the two axes have different orientations and do not intersect at the position of the star (i.e. at the SW peak of the 3 mm continuum) can be interpreted in two ways: either we are dealing with two jets originating from two different YSOs, or the jet is precessing and the star is moving on the plane of the sky at a different speed with respect to the large-scale lobes. The latter scenario implies that either the star or the ejected material is experiencing deceleration or acceleration, such that one of the two is lagging behind the other.

![](2jets.eps)

![](cont_fits.eps)

Although it is impossible to rule out one of the two hypotheses, in the following we assume that all lobes belong to the same jet, because there is only one core lying along the jet axis and evidence for precession has been found in S255IR NIRS 3 (Wang et al. (cite: wang); Fedriani et al. (cite: fedr23)), as well as other similar objects (see e.g. Shepherd et al. (cite: shep00), Cesaroni et al. (cite: cesa05), Sánchez-Monge et al. (cite: sanch14), Beltrán et al. (cite: bel16)). Further support for this hypothesis is given by the progressive change of the position angle of the jet from the large to the small scale, as shown in Table [3](#tpa). This trend is indeed consistent with a jet outflow undergoing precession.

## Continuum emission at $\lambda\ge7$ mm

In Fig. [4](#fsedfits) we present the continuum spectra obtained from the flux densities in Table [\[tflux\]](#tflux). Our VLA observations of S255IR NIRS 3 span an interval of time prior to the ALMA observations (see Table [\[tflux\]](#tflux)) and the radio emission of the variable source in S255IR NIRS 3 is basically unresolved in all of our VLA observations. However, we can study the spatial evolution of the jet by determining the position of the peak at different times. For this purpose we fitted a 2D Gaussian to the K-band maps with sub-arcsecond resolution. We prefer the 1.3 cm data to the 7 mm data, which would provide us with better resolution, because in the K band the S/N is higher and in the Q band contamination by dust thermal emission might be present. In Fig. [5](#fpeaks) we plot the distribution of the peak positions thus obtained. To give an idea of the uncertainty on these positions, we also draw ellipses corresponding to one-fifth of the synthesised beams. For our analysis we also included the NE peak of our ALMA data and that of Obonyo et al. ((cite: obonyo); hereafter OLHKP). Despite the large uncertainties, it is clear that the distance of the peak from the star is increasing with time, as expected if the jet is expanding. This expansion appears to slow down with time, because the mean velocity (projected on the plane of the sky) estimated from the ratio between the separation of the peaks at the last two epochs (ALMA data) and the corresponding time interval is $\sim$40 au/820 days$\simeq$84 km s$^{-1}$, much less than the mean velocity from the beginning of the radio burst, namely $\sim$472 au/1881 days$\simeq$436 km s$^{-1}$, where $\sim$472 au is the distance of the NE peak from the star at the last epoch. Using the same approach, Fedriani et al. ((cite: fedr23)) estimated an expansion speed of $450\pm50$ km s$^{-1}$ from their IR data. We further analyse the expansion of the jet in Sect. [4.3.1](#sexp).

![](r_t_k-a.eps)

The flux density of S255IR NIRS 3 is changing with time in all bands, as shown in Fig. [6](#fvar). One can identify two phases: the first when the flux increases exponentially for $\sim$200 days; the second when the flux remains basically constant, or slightly declines towards the end of our monitoring. This behaviour is the same at all frequencies $\ge$6 GHz, but is not so obvious at the two longest wavelengths, where a precise estimate of the flux density of the compact variable source is not possible for the reason explained in Sect. [2.1](#svla). Moreover, in these bands our monitoring is more limited in time. It is hence quite possible that the flux density below 6 GHz has a different behaviour than that at higher frequencies. Therefore, the radio emission at 1.5 and 3 GHz, and probably also part of the 6 GHz flux, might not be due to free-free radiation but to another mechanism, such as synchrotron emission, which has been detected towards a number of extended radio jets from YSOs (e.g. Carrasco-Gonzalez et al. (cite: cargon10), Moscadelli et al. (cite: mosca13), Brogan et al. (cite: brog18), Sanna et al. (cite: sanna19) and references therein). The evident change of slope in some of the VLA spectra seems to support this possibility. In this respect, the most representative is the spectrum acquired on 2016/10/15 (see Fig. [4](#fsedfits)), where the 1.5 GHz point lies well above any plausible extrapolation of the other fluxes. For all these reasons, in the following we focus our study on the emission above 6 GHz, with the caveat that even the 6 GHz flux might be partly contaminated by a non-thermal contribution, as suggested by OLHKP. It is worth noting that the existence of synchrotron emission from S255IR NIRS 3 is supported by the recent possible detection of high-energy gamma-ray emission from this source (see Wilhelmi et al. (cite: wilh23)).

![](flux_time.eps)

# Analysis and discussion

## Nature of the 3 mm continuum emission

For the reasons presented in Sect. [3.1](#srmm), we have concluded that the (proto)star should lie at the SW peak of the 3 mm continuum map. If this is the case, one expects this peak to have a significant contribution from thermal dust emission, whereas the NE peak, being part of a jet lobe, should be dominated by free-free emission. To investigate these assumptions, we computed the spectral index of the 3 mm continuum over the maps in Fig. [1](#falma). For this purpose, we used the maps obtained from the four correlator units centred at 85.2, 87.2, 97.2, and 99.2 GHz (see Sect. [2.2](#salma)), created with the same clean beam. For each pixel of the maps, the spectral index was computed from a least-square fit to the four fluxes in a $\log S_\nu$–$\log\nu$ plot. The fit was performed only in those pixels where all of the four fluxes were above the 5$\sigma$ level. The result is shown in Fig. [7](#fspi), where the formal error obtained from the fit ranges from 0.03 towards the emission peaks to 0.3 towards the borders.

At 3 mm it is reasonable to assume that dust emission is optically thin and the flux density is $\propto\nu^\gamma$, with $\gamma=2$–4, because the dust absorption coefficient is believed to vary as $\nu^\beta$ with $\beta=0$–2 (see e.g. D’Alessio et al. (cite: dale01), Sadavoy et al. (cite: sada13)), where $\beta=0$ corresponds to the case of large grains (‘pebbles’) in disks (Testi et al. (cite: testi)). The same assumption also holds for the free-free emission: the spectra in Fig. [4](#fsedfits) flatten beyond 45 GHz, and hence the flux density is $\propto\nu^{-0.1}$. Therefore, more positive spectral indices can be associated with dust emission and, conversely, more negative ones with free-free emission. At both epochs dust emission arises from the region around the SW peak, as expected for a deeply embedded star, while the NE lobe of the jet is characterised by free-free emission. Noticeably, some free-free emission is also detected towards the most south-western tip.

When estimating the flux density at wavelengths of 3 mm or shorter, it is thus necessary to distinguish between the NE lobe and the rest of the source. In Table [4](#tf3mm) we give all these fluxes for the two epochs of the ALMA observations. It is worth pointing out that the spectral index over the SW region is mostly $\ensuremath{\lesssim}$2, whereas the typical index expected for pure dust emission, should lie approximately between 2 and 4. This suggests the presence of non-negligible free-free emission around the SW peak as well. It is possible to estimate what fraction of the total flux is due to free-free as follows. The total flux can be written as $S_\nu=S_\nu^{\rm d}+S_\nu^{\rm
ff}$, where $S_\nu^{\rm ff}\propto\nu^{-0.1}$ is the optically thin free-free flux and $S_\nu^{\rm d}\propto\nu^\gamma$, with $\gamma=2$–4, is the dust flux. As previously explained, the spectral index between $\nu_1=85.2$ GHz and $\nu_2=99.2$ GHz was estimated assuming $S_\nu\propto\nu^\alpha$, and hence we have $$\begin{eqnarray}
\frac{S_{\nu_2}}{S_{\nu_1}} & = & \left(\frac{\nu_2}{\nu_1}\right)^\alpha \\
\frac{S_{\nu_2}}{S_{\nu_1}} & = & \frac{S^{\rm d}_{\nu_2} + S^{\rm ff}_{\nu_2}}
                                   {S^{\rm d}_{\nu_1} + S^{\rm ff}_{\nu_1}} ~=~
                              \frac{S^{\rm d}_{\nu_1}\left(\frac{\nu_2}{\nu_1}\right)^\gamma + S^{\rm ff}_{\nu_1}\left(\frac{\nu_2}{\nu_1}\right)^{-0.1}}
                                   {S^{\rm d}_{\nu_1} + S^{\rm ff}_{\nu_1}}.
\end{eqnarray}$$ After some algebra, we obtain the ratio $$\begin{equation}
 R_{\rm S} \equiv \frac{S^{\rm ff}_{\nu_1}}{S^{\rm d}_{\nu_1}}
             = \frac{\left(\frac{\nu_2}{\nu_1}\right)^\gamma - \left(\frac{\nu_2}{\nu_1}\right)^\alpha}
                    {\left(\frac{\nu_2}{\nu_1}\right)^\alpha - \left(\frac{\nu_2}{\nu_1}\right)^{-0.1}}
\end{equation}$$ and, from this, the fraction of the total flux due to free-free emission, $R_{\rm S}/(1+R_{\rm S})$. Using the values of $\alpha$ in Fig. [7](#fspi), we find that such a fraction on average ranges from 65%, for $\gamma$=2, to 85%, for $\gamma$=4. This implies that 15–20 mJy out of 23 mJy emitted by the SW component (see Table [4](#tf3mm)), are contributed by free-free emission, also consistent with the brightness temperature of $\sim$500 K measured at 3 mm towards the SW peak, probably too large to be due only to dust emission. We note that part of this free-free emission might be due to ionisation by the embedded star of $\sim$20 $M_\odot$ (Zinchenko et al. (cite: zin15)).

![](simaps.eps)

|   date   |    NE    |    SW    | total |
|:--------:|:--------:|:--------:|:-----:|
| 2019/6/6 | 22.8$^a$ | 23.2$^b$ | 46.0  |
| 2021/9/3 | 18.8$^a$ | 23.4$^b$ | 42.3  |

:  Flux densities in millijanskys measured at 92.5 GHz with ALMA towards the NE and SW components of S255IR NIRS 3.

$^a$ Free-free emission.\
$^b$ Both dust and free-free emission.

As already mentioned, some free-free emission is also detected towards the tip of the SW region and becomes more prominent and more extended with time, as one can see by comparing Fig. [1](#falma)a to Fig. [1](#falma)b. This hints at the existence of another jet lobe emerging from the dusty core and expanding towards the SW.

To shed light on the nature of this putative lobe and set a constraint on its age, in Fig. [8](#flobes) we compare the jet structure observed by OLHKP at 1.3 cm on May 5, 2018, with our ALMA image at 3 mm. It seems that during the period of our monitoring, up to the observation of OLHKP (664 days after the onset of the radio outburst), no significant free-free emission was seen to the SW of the (proto)star at any of the wavelengths observed with the VLA. We thus conclude that in all likelihood the SW jet lobe appeared only recently, between May 2018 and June 2019. Therefore, the radio flux variations monitored by us until January 2018 are to be attributed only to the NE lobe.

## Origin of the SW lobe

One may wonder if the emerging SW lobe corresponds to a new radio burst or is somehow related to the accretion outburst observed by Caratti o Garatti et al. ((cite: cagana)). Only follow-up observations of the jet structure will allow us to establish if the new lobe is as prominent and long-lasting as the NE one. However, we point out that the IR monitoring performed by Uchiyama et al. ((cite: uchi)) and Fedriani et al. ((cite: fedr23)) between November 2015 and February 2022 as well as the methanol maser observations[^4] of the Maser Monitoring Organization (M2O)[^5] have not revealed any other burst after that of Caratti o Garatti et al. ((cite: cagana)) and before the ejection of the SW lobe. We conclude that both jet lobes could arise from the same accretion event, although with a time lag between them of 22–35 months.

This hypothesis is also supported by a noticeable feature of the jet system in S255IR NIRS 3, namely that the extension of the NE lobe is about twice as much as that of the SW lobe. This is true not only for the large-scale and small-scale lobes in Fig. [3](#fjets), but also for the H$_2$O masers distribution, as shown in Fig. [9](#fwat). The existence of the same asymmetry on different scales and tracers cannot be a coincidence and is suggestive of a mechanism that causes a delay of the ejection of the SW lobe with respect to the NE lobe. In our opinion, two explanations are possible: either the accretion (and hence ejection) event is intrinsically stronger on the NE side of the disk, or the expansion towards the SW is hindered by the presence of denser material. We favour the latter hypothesis since the near-IR emission is much fainter from the SW lobe than from the NE lobe (see Caratti o Garatti et al. (cite: cagana) and Fedriani et al. (cite: fedr23)). This finding is surprising, because the SW lobe corresponds to the blue-shifted emission of the jet outflow (see Wang et al. (cite: wang)), which means that the jet is pointing towards the observer on that side and the extinction should be lower than on the NE side. The weakness of the IR emission to the SW is thus indicative of an asymmetry in the density distribution along the jet axis, a fact that could naturally also explain the delay of the expansion of the SW lobe with respect to the NE lobe.

![](lobe_sw.eps)

![](h2ojet.eps)

## Evolution of the radio emission

In this section we present a model fit to the observed spectra, following the approach adopted in Paper I, with some modifications. As done in Paper I, we adopted the ‘standard spherical’ model from Reynolds ((cite: reyn)) to describe the radio continuum emission from the jet. In practice, this means that we assume a jet where at a given time the opening angle, electron temperature, ionisation degree, and expansion speed do not depend on the distance from the star, $r$.

### Expansion law of the jet

In Paper I the jet was assumed to undergo expansion at constant velocity so that the maximum radius could be described by the simple expression $r_{\rm m}(t)=r_{\rm m}(0)+\varv_0t$, with $\varv_0$=900 km s$^{-1}$. While this assumption could hold for the first few months after the onset of the radio outburst, it is inconsistent with the most recent data. In fact, in Sect. [3.2](#srcm) we show that the jet expansion is slowing down with time. We thus need to adopt a more realistic law for $r_{\rm m}(t)$.

For this purpose, we assume that the jet is expanding in a medium with density $\propto r^{-2}$, with $r$ the distance from the star. It is possible to demonstrate (see Appendix [6](#aexp)) that applying momentum conservation one obtains $$\begin{equation}
 y_{\rm m}(t) = y_{\rm m 0}+ 2T\varv_0\cos\psi \left(\sqrt{1+\frac{t}{T}}-1\right)  \label{eym}
,
\end{equation}$$ where we have multiplied both terms of Eq. ([\[earm\]](#earm)) by $\cos\psi$, with $\psi$ the angle between the jet axis and the plane of the sky. For consistency with Reynolds ((cite: reyn)), we have indicated with $y$ the projection of $r$ on the plane of the sky. Here, $T$ is a suitable timescale, and $\varv_0$ and $y_{\rm m 0}$ are, respectively, the expansion velocity and the value of $y_{\rm m}$ at the onset of the radio outburst (i.e. on July 10, 2016). As in Paper I, we chose $\varv_0$=900 km s$^{-1}$, while the two parameters $T$ and $y_{\rm m 0}$ can be determined from the values of $y_{\rm m}$ estimated from the two ALMA maps at $t$=1061 days and $t$=1881 days.

The problem is that $y_{\rm m}$ cannot be trivially obtained from the position of the NE peak, which corresponds to the maximum brightness temperature. This temperature is attained either at the inner radius, if the whole jet is optically thin, or at the border between the optically thin and the optically thick parts of the jet (denoted by $y_1$ in Reynolds’ notation). Beyond this point, the emission is optically thin and the brightness temperature scales with the opacity $\tau \propto r^{-3}$, as from Reynolds’ Eq. (4). For this reason, the jet can extend much beyond the position of the observed peak.

In order to obtain a reliable estimate of $y_{\rm m}$, we have fitted the NE lobe in the two ALMA maps of Fig. [1](#falma) assuming that the 3 mm emission is optically thin all over the jet surface. Under this hypothesis the brightness temperature can be expressed as $$\begin{equation}
T_{\rm B} = T_0 \tau = T_0 \left(\frac{y}{y_0}\right)^{-3}
,
\end{equation}$$ where $y=r\,\cos\psi$ is the projection of $r$ on the plane of the sky and $y_0=r_0\,\cos\psi$ with $r_0$ the inner radius of the jet. For a given set of $y_0$, $y_{\rm m}$, and $\theta_0$ (the opening angle of the jet) a map was generated, convolved with the instrumental beam, and the model brightness temperature was computed for each pixel of the observed map. The best fit was obtained by minimising the expression $$\begin{equation}
\chi^2=\sum_i \left(T_{\rm B}^i({\rm model})-T_{\rm B}^i({\rm data})\right)^2
,
\end{equation}$$ with $i$ a generic pixel, after varying the three parameters over suitable ranges. The best-fit models are compared to the observed maps in Fig. [10](#fmods) and correspond to $\theta_0$=9$^\circ$, $y_0$=0.206$''$=367 au, and $y_{\rm m}$=0.29$''$=516 au, for the first map, and $\theta_0$=2.4$^\circ$, $y_0$=0.207$''$=368 au, and $y_{\rm m}$=0.356$''$=634 au, for the second map.

From Eq. ([\[eym\]](#eym)) written for $t$=1061 days and $t$=1881 days, one obtains a system of two equations in the two unknowns $T$ and $y_{\rm m 0}$, the solutions to which are $T$=124 days and $y_{\rm m 0}$=251 au. Hence, one has $$\begin{equation}
 y_{\rm m}({\rm au}) = 251 + 127 \left(\sqrt{1+\frac{t({\rm days})}{124}}-1\right). \label{eymnum}
\end{equation}$$ The value of $r_{\rm m}$ can be computed from Eq. ([\[eym\]](#eym)) assuming $\psi$=10$^\circ$ (see Paper I, where the complementary angle $i=90\ensuremath{^\circ}-\psi=80\ensuremath{^\circ}$ was used). Figure [11](#frmax) compares our solution, $y_{\rm m}$, as a function of time (blue curve) with (i) the positions of the maximum brightness temperature (the same as in Fig. [5](#fpeaks)) and (ii) the value of $y_1$ obtained from the model fits described later in Sect. [4.3.2](#smod). The latter corresponds to the border between the optically thin and optically thick parts of the jet. Clearly, the brightness appears to peak much closer to $y_1$ than to $y_{\rm m}$, as previously mentioned.

![](model3mm.eps)

![](r_t_k-b.eps)

### Modelling the jet variability

We wish to reproduce the spectral variation shown in Fig. [4](#fsedfits) and thus derive the values of the jet parameters as a function of time. For this purpose, we introduce some modifications with respect to the original model by Reynolds ((cite: reyn)), which was used in Paper I. Reynolds’ equations were derived under the approximation of small $\theta_0$, the opening angle of the jet[^6]. However, in Paper I we find that $\theta_0$$\simeq$20$^\circ$–50$^\circ$ is needed to fit the spectra. In order to overcome this limitation we re-wrote Reynolds’ equations under suitable assumptions, as detailed in Appendix [7](#amodel), so that they are now valid for any $\theta_0<90\ensuremath{^\circ}$.

All observed spectra have been fitted with Eq. ([\[eaflux\]](#eaflux)) using only the measurements with $\nu$$\ge$6 GHz, for the reasons discussed in Sect. [3.2](#srcm). We stress that, unlike Paper I, here we assume the jet to be mono-polar, because there is no hint of the existence of a SW lobe during the whole period of our VLA monitoring (see Sect. [4.1](#smmem)). The input parameters of the model are the angle between the jet axis and the plane of the sky, $\psi$, the ionised gas temperature, $T_0$, the inner radius, $r_0$, the projection of the outer radius on the plane of the sky, $y_{\rm m}$, the opening angle, $\theta_0$, and the parameter $\Lambda=x_0\,\dot{M}/\varv_0$, where $x_0$ is the fraction of ionised gas, $\varv_0$ the expansion velocity, and $\dot{M}$ the total mass loss rate (neutral plus ionised). The quantities $T_0$, $\varv_0$, and $x_0$ are assumed to be constant along the jet, while $T_0$ is also constant in time.

![](pars3_bestfit.eps)

![](tho_t.eps)

To simplify the fitting procedure as much as possible, we fixed $T_0=10^4$ K and $\psi=10\ensuremath{^\circ}$ (see Paper I), and computed $y_{\rm m}$ from Eq. ([\[eymnum\]](#eymnum)). Unlike in Paper I, we decided to leave $r_0$ free, because a priori the inner radius could change while the jet is expanding. So, we are left with three free parameters: $r_0$, $\theta_0$, and $\Lambda$. The best fit to each spectrum has been obtained by minimising the $\chi^2$ given in Eq. (10) of Paper I, after varying the parameters over the ranges $\theta_0$=3$^\circ$–50$^\circ$, $r_0$=50–300 au, and $\Lambda$=$10^{-10}$–$10^{-7}$ $M_\odot$ yr$^{-1}$/(km s$^{-1}$). The best-fit spectra are represented by the solid curves in Fig. [4](#fsedfits) and the best-fit parameters are given in Table [5](#tpars). The errors on the parameters have been computed using the criterion of Lampton et al. ((cite: lamp)), as done in Paper I.

While most of the fits look to be in agreement with the data within the uncertainties, the 6 GHz fluxes appear to be underestimated by the model at the last five to six epochs. In our opinion, such a discrepancy could indicate contamination from non-thermal emission at this frequency, as already suggested by OLHKP. Indeed, as discussed in Sect. [3.2](#srcm), non-thermal emission is very prominent at longer wavelengths in the same spectra (red points in Fig. [4](#fsedfits)) and it is hence not surprising that this type of emission can contribute significantly to the flux up to 6 GHz.

In Fig. [12](#fpars) we plot the best-fit parameters as a function of time. One sees that the opening angle rapidly increases up to the maximum value allowed by us. It may seem that an opening angle of 50$^\circ$ is too large for a jet, but it is similar to that predicted by theory for a jet powered by a $\sim$20 $M_\odot$ YSO (Zinchenko et al. (cite: zin15)), namely $\sim$52$^\circ$, obtained by interpolating the values in Table 2 of Staff et al. ((cite: staff19)). Moreover, we can obtain a direct estimate of $\theta_0$ from the observed peak brightness temperature in the synthesised beam, $T_{\rm SB}$, assuming optically thick emission. Approximating the jet as a Gaussian source, one has $$\begin{equation}
T_{\rm SB}=T_{\rm B}\frac{\Theta_{\rm S}^2}{\Theta_{\rm S}^2+\Theta_{\rm B}^2}
,
\end{equation}$$ where $T_{\rm B}$ is the intrinsic brightness temperature of the source and $\Theta_{\rm S}$ and $\Theta_B$ are, respectively, the full widths at half power of the source and synthesised beam. Consequently, $$\begin{equation}
\Theta_{\rm S} = \Theta_{\rm B} \sqrt{\frac{T_{\rm SB}}{T_{\rm B}-T_{\rm SB}}}. \label{eths}
\end{equation}$$ This expression can be used to calculate a lower limit on the source diameter, $\Theta_{\rm S}^{\rm min}$, assuming that the free-free emission is optically thick, namely for $T_{\rm B}$=$T_0$=$10^4$ K. Correspondingly, a lower limit on the opening angle is obtained from $$\begin{equation}
\theta_0^{\rm min} = \arcsin\left(\frac{\Theta_{\rm S}^{\rm min}}{2\Delta}\right) = \arcsin\left(\frac{\Theta_{\rm B}}{2\Delta}\sqrt{\frac{T_{\rm SB}}{T_0-T_{\rm SB}}}\right)   \label{etho}
,
\end{equation}$$ where $\Delta$ is the separation between the peak of $T_{\rm SB}$ and the position of the (proto)star. We estimated $\theta_0^{\rm min}$ for all of our maps, and for each epoch we computed the mean $\theta_0^{\rm min}$ obtained from the four bands. This is plotted in Fig. [13](#ftho) as a function of time. For the sake of comparison we also plot $\theta_0$ obtained from our model fits (dashed line). We conclude that, despite the crude approximations adopted to derive Eq. ([\[etho\]](#etho)), values of $\theta_0$ of a few times 10$^\circ$ seem plausible and consistent with our model fit results. It is worth noting that $\theta_0$ computed from the map of OLHKP and from our ALMA maps (Fig. [1](#falma)) using Eq. ([\[etho\]](#etho)) turns out to be much less, namely 7$^\circ$, 1.7$^\circ$, and 1.3$^\circ$, respectively 664, 1061, and 1881 days after the radio outburst. We speculate that the jet could be re-collimating on a timescale of a couple of years.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| date | time | $y_{\rm m}$$^a$ | $\theta_0$ | $r_0$ | $\Lambda\times10^8$ |
| (yy/mm/dd) | (days) | (au) | (deg) | (au) |  $(M_\odot~{\rm yr}^{-1}/({\rm km~s}^{-1}))$ |
| 16/07/10 | 0 | 251 | $11_{-3}^{+8}$ | $64_{-14}^{+44}$ | $0.19_{-0.04}^{+0.07}$ |
| 16/08/01 | 22 | 262 | $14_{-4}^{+5}$ | $50_{-0}^{+29}$ | $0.28_{-0.06}^{+0.07}$ |
| 16/10/15 | 97 | 294 | $20_{-4}^{+5}$ | $50_{-0}^{+9}$ | $0.72_{-0.13}^{+0.14}$ |
| 16/11/20 | 133 | 307 | $38_{-8}^{+12}$ | $50_{-0}^{+11}$ | $1.69_{-0.35}^{+0.37}$ |
| 16/12/27 | 170 | 320 | $50_{-5}^{+0}$ | $61_{-11}^{+24}$ | $2.90_{-0.41}^{+0.47}$ |
| 17/01/26 | 200 | 329 | $50_{-6}^{+0}$ | $68_{-18}^{+29}$ | $3.11_{-0.47}^{+0.57}$ |
| 17/03/03 | 236 | 340 | $50_{-5}^{+0}$ | $73_{-23}^{+30}$ | $3.33_{-0.50}^{+0.61}$ |
| 17/03/19 | 252 | 345 | $50_{-4}^{+0}$ | $63_{-13}^{+25}$ | $3.38_{-0.45}^{+0.54}$ |
| 17/07/29 | 384 | 381 | $50_{-2}^{+0}$ | $106_{-25}^{+30}$ | $4.78_{-0.65}^{+0.73}$ |
| 17/08/19 | 405 | 386 | $50_{-2}^{+0}$ | $96_{-25}^{+26}$ | $4.98_{-0.63}^{+0.66}$ |
| 17/08/25 | 411 | 388 | $50_{-2}^{+0}$ | $97_{-25}^{+27}$ | $5.12_{-0.66}^{+0.71}$ |
| 17/09/17 | 434 | 393 | $50_{-1}^{+0}$ | $136_{-24}^{+26}$ | $5.12_{-0.60}^{+0.65}$ |
| 17/10/23 | 470 | 402 | $50_{-1}^{+0}$ | $136_{-27}^{+27}$ | $5.19_{-0.66}^{+0.65}$ |
| 17/12/08 | 516 | 413 | $50_{-2}^{+0}$ | $155_{-30}^{+28}$ | $5.33_{-0.76}^{+0.71}$ |
| 17/12/27 | 535 | 417 | $50_{-2}^{+0}$ | $161_{-31}^{+27}$ | $5.41_{-0.81}^{+0.67}$ |
| 18/01/15 | 554 | 421 | $50_{-2}^{+0}$ | $166_{-32}^{+29}$ | $5.41_{-0.83}^{+0.72}$ |

:  Parameters of the best fits to the spectra in Fig. [4](#fsedfits).

$^a$ obtained from Eq. ([\[eymnum\]](#eymnum))

Another interesting result from Fig. [12](#fpars) is the behaviour of $r_0$, which remains basically constant for $\sim$250 days after the radio outburst, thereafter showing a systematic increase until the end of our monitoring – and even beyond that, as we estimate values of $\sim$370 au at the time of our first ALMA observations (see Sect. [4.3.1](#sexp)). A straightforward interpretation is that the inner radius expands when the mechanism feeding the jet is switched off. Noticeably, $\Lambda$ appears to reach a maximum just when $r_0$ starts increasing, supporting the idea that no more material is added to the jet. This hypothesis is confirmed by Fig. [14](#fmjet), which shows how the ionised jet mass, computed from Eq. ([\[eamjet\]](#eamjet)), varies with time. In the same figure we also plot $r_0$ for the sake of comparison. It is quite clear that both quantities have a bi-modal temporal behaviour, before and after the time interval marked by the grey area. From the onset of the radio outburst up to $\sim$250 days, $r_0$ remains approximately constant, whereas the jet mass increases. After that, the reverse occurs: as soon as the inner radius starts increasing, the jet stops growing in mass, with the grey area marking the transition between these two phases. This is consistent with mass conservation in an expanding jet that is not fed anymore by the outburst.

It is also worth noting that the ratio, $R_{\rm e}$, between the mass ejected, $M_{\rm jet}$, and that accreted during the outburst, $M_{\rm acc}$, can be computed from the final value of $x_0\,M_{\rm jet}$ in Fig. [14](#fmjet) and that quoted by Caratti o Garatti et al. ((cite: cagana)) ($M_{\rm acc}\simeq3.4\times10^{-3}$ $M_\odot$). One obtains $R_{\rm e}\simeq7.5\times10^{-5}/(3.4\times10^{-3}\,x_0)\simeq2.2\times10^{-2}/x_0$. Since by definition $x_0\le1$, we conclude that $R_{\rm e}$ must be greater than a few percent. Vice versa, assuming that at least 10% of the infalling material will be redirected into outflow, one has $R_{\rm e}>0.1,$ which sets an upper limit of $\sim$0.2 on the ionisation fraction, consistent with the estimate obtained in Paper I and the values estimated for similar sources (see Fedriani et al. (cite: fedr19)).

![](mjet.eps)

# Summary and conclusions

As a follow-up to Paper I, we monitored the radio continuum emission of the outburst from the massive YSO S255IR NIRS 3 over $\sim$13 months at six wavelengths with the VLA. We also imaged the radio jet at 3 mm with ALMA at two epochs separated by $\sim$27 months, with an angular resolution $\ensuremath{\lesssim}$0.1$''$. Our results indicate that after an exponential increase in the radio flux in all observed bands, the intensity becomes constant or slightly decreasing. A comparison of the two ALMA maps shows that the radio jet is expanding both to the NE and SW, although only the NE lobe was present during our VLA monitoring. The SW lobe appeared between May 2018 and June 2019, namely at a much later time than the NE lobe. We believe that this ejection event is related to the same accretion outburst, which occurred in 2015. We speculate that the delay between the two lobes might be due to a greater density of the medium facing the SW lobe, which could curb the expansion of the jet on that side.

From the analysis of the continuum spectra, we infer that two mechanisms are needed to explain the observed fluxes: free-free emission at short wavelengths and non-thermal (probably synchrotron) emission at long wavelengths. We believe that the latter should become dominant at frequencies $\ensuremath{\lesssim}$6 GHz. For this reason, we fitted only the data with $\nu\ge6$ GHz using a slightly modified version of the jet model adopted in Paper I, which works for any opening angle of the jet $<$90$^\circ$. We conclude that the spectra can be satisfactorily reproduced with an expanding, decelerating, mono-polar thermal jet that was actively powered by the outburst until mid-2017. After this date, no more mass is injected into the lobes and the inner jet radius expands, which, over the long term, is bound to give rise to one of the knots that characterise thermal jets from YSOs.

# Acknowledgements

A.C.G. acknowledges from PRIN-MUR 2022 20228JPA3A “The path to star and planet formation in the JWST era (PATH)” and by INAF-GoG 2022 “NIR-dark Accretion Outbursts in Massive Young stellar objects (NAOMY)” and Large Grant INAF 2022 “YSOs Outflows, Disks and Accretion: towards a global framework for the evolution of planet forming systems (YODA)”. R.F. acknowledges support from the grants Juan de la Cierva JC2021-046802-I, PID2020-114461GB-I00 and CEX2021-001131-S funded by MCIN/AEI/ 10.13039/501100011033 and by “European Union NextGenerationEU/PRTR”. T.P.R acknowledges support from ERC grant 743029 EASY. This study is based on observations made under project 16A-424, 16B-427, and 17B-045 of the VLA of NRAO. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.. This paper makes also use of the following ALMA data: ADS/JAO.ALMA#2018.1.00864.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

(ref: aud) Audard, M., Ábrahám, P., Dunham, M. M., et al. 2014, in Protostars and Planets VI, ed. T. Henning, C. P. Dullemond, R. S. Klessen and H. Beuther (Tucson: Univ. of Arizona Press), 387 (ref: beldew) Beltrán, M. T. & de Wit, W. J. 2016, A&ARv, 24, 6 (ref: bel16) Beltrán, M. T., Cesaroni, R., Moscadelli, L., et al. 2016, A&A, 593, A49 (ref: bole13) Boley, P.A., Linz, H., van Boekel, R., et al. 2013, A&A, 558, A24 (ref: brog18) Brogan, C. L., Hunter, T. R., Cyganowski, C. J., et al. 2018, ApJ, 866, 87 (ref: burns16) Burns, R. A., Handa, T., Nagayama, T., Sunada, K., & Omodaka, T. 2016, MNRAS, 460, 283 (ref: burns20) Burns, R. A., Sugyiama, K., Hirota, T., et al. 2020, Nature Astronomy, 4, 506 (ref: burns23) Burns, R. A., Uno, Y., Sakai, N., et al. 2023, Nature Astronomy, 7, 557 (ref: cagana) Caratti o Garatti, A., Stecklum, B., Garcia Lopez, R., et al. 2017, Nature Physics, 13, 276 (ref: cargon10) Carraco-González, C., Rodrı́guez, L.F., Anglada, G. et al. 2010, Science, 330, 1209 (ref: cesa05) Cesaroni, R., Neri, R., Olmi, L., et al. 2005, A&A, 434, 1039 (ref: cesa18) Cesaroni, R., Moscadelli, L., Neri, R., et al. 2018, A&A, 612, A103 (Paper I) (ref: chen21) Chen, Z., Sun, W., Chini, R., et al. 2021, ApJ, 922, 90 (ref: dale01) D’Alessio, P., Calvet, N., & Hartmann, L. 2001, ApJ, 553, 321 (ref: fedr19) Fedriani, R., Caratti o Garatti, A., Purser, S. J. D., et al. 2019, Nature Communications, 10, 3630 (ref: fedr23) Fedriani, R., Caratti o Garatti, A., Cesaroni, R., et al. 2023, A&A, submitted (ref: fischppvii) Fischer, W. J., Hillenbrand, L. A., Herczeg, G. J., et al. in Protostars and Planets VII, in press (ref: fuji) Fujisawa, K., Yonekura, Y., Sugiyama, K., et al. 2015, The Astronomer’s Telegram, 8286, 1 (ref: goddi07) Goddi, C., Moscadelli, L., Sanna, A., Cesaroni, R., & Minier, V. 2007, A&A, 461, 1027 (ref: hiro21) Hirota, T., Cesaroni, R., Moscadelli, L., et al. 2021, A&A, 647, A23 (ref: hunt17) Hunter, T. R., Brogan, C. L., MacLeod, G., et al. 2017, ApJ, 837, L29 (ref: hunt21) Hunter, T. R., Brogan, C. L., De Buizer, J. M., et al. 2021, ApJ, 912, L17 (ref: lamp) Lampton, M., Margon, B., & Bowyer, S. 1976, ApJ, 208, 177 (ref: liu18) Liu, S.-Y., Su, Y.-N., Zinchenko, I., Wang, K.-S., Wang, Y. 2018, ApJ, 863, L12 (ref: liu20) Liu, S.-Y., Su, Y.-N., Zinchenko, I., et al. 2020, ApJ, 904, 181 (ref: mosca13) Moscadelli, L., Cesaroni, R., Sánchez-Monge, Á., et al. 2013, A&A, 558, A145 (ref: mosca17) Moscadelli, L., Sanna, A., Goddi, C., et al. 2017, A&A, 600, L8 (ref: obonyo) Obonyo, W. O., Lumsden, S. L., Hoare, M. G., Kurtz, S. E., & Purser, S. J. D. 2021, MNRAS, 501, 5197 (OLHKP) (ref: reyn) Reynolds, S.P. 1986, ApJ, 304, 713 (ref: sada13) Sadavoy, S. I., Di Francesco, J., Johnstone, D., et al. 2013, ApJ, 767, 126 (ref: sanch14) Sánchez-Monge, Á., Beltrán, M. T., Cesaroni, R., et al. 2014, A&A, 569, A11 (ref: statcont) Sánchez-Monge, Á., Schilke, P., Ginzburg, A., Cesaroni, R., & Schmiedeke, A. 2018, A&A, 609, A101 (ref: sanna19) Sanna, A., Moscadelli, L., Goddi, C., et al. 2019, A&A, 623, L3 (ref: shep00) Shepherd, D.S., Yu, K.C., Bally, J., & Testi, L. 2000, ApJ, 535, 833 (ref: staff19) Staff, J. E., Tanaka, K. E. I., & Tan, J. C. 2019, ApJ 882, 123 (ref: steck16) Stecklum, B., Caratti o Garatti, A., Cardenas, M. C., et al. 2016, The Astronomer’s Telegram, 8732, 1 (ref: steck21) Stecklum, B., Wolf V., Linz H., et al. 2021, A&A, 646, A161 (ref: testi) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. T. Henning, C. P. Dullemond, R. S. Klessen and H. Beuther (Tucson: Univ. of Arizona Press), 339 (ref: uchi) Uchiyama, M., Yamashita, T., Sugyiama, K., et al. 2020, PASJ, 72, 4-1 (ref: wilh23) Wilhelmi, E. de Oña, López-Coto, R., & Su, Y. 2023, MNRAS, in press (ref: wang) Wang, Y., Beuther, H., Bik, A., et al. 2011, A&A, 527, A32 (ref: zin15) Zinchenko, I., Liu, S.-Y., Su, Y.-N., et al. 2015, ApJ, 810, 10

# Jet expansion law

As discussed in Sect. [4.3.1](#sexp), the jet is not expanding at constant velocity during the period of our monitoring, but it appears to slow down. It is thus necessary to adopt an expression for the maximum radius, $r_{\rm m}$, that properly takes this effect into account. A reasonable scenario may be that of a jet confined in a solid angle $\Omega\,$, with initial mass $M_0$, which expands with initial velocity $\varv_0$ through a medium with density $\rho\propto r^{-2}$, where $r$ is the distance from the jet origin. Because of momentum conservation one can write $$\begin{eqnarray}
 M_0 \varv_0 & = & M(t) \frac{{\rm d}r_{\rm m}}{{\rm d}t}  \nonumber \\
  & = & \left[M_0 + \int_{r_{\rm m 0}}^{r_{\rm m}} \rho_0\left(\frac{r_{\rm m 0}}{r}\right)^2 \Omega\,r^2 \, {\rm d}{r} \right] \frac{{\rm d}r_{\rm m}}{{\rm d}t}  \nonumber \\
  & = & \left[M_0 + \Omega\,\rho_0 r_{\rm m 0}^2 \left(r_{\rm m}-r_{\rm m 0}\right) \right] \frac{{\rm d}r_{\rm m}}{{\rm d}t}
,
\end{eqnarray}$$ with $\rho_0$ density at radius $r_{\rm m 0}$. The solution of this differential equation is $$\begin{eqnarray}
 M_0 \varv_0 t & = & M_0 \left(r_{\rm m}-r_{\rm m 0}\right)  \nonumber \\
 & & +~ \Omega\,\rho_0 r_{\rm m 0}^2 \left[\frac{r_{\rm m}^2-r_{\rm m 0}^2}{2} - r_{\rm m 0}\left(r_{\rm m}-r_{\rm m 0}\right)\right]
,
\end{eqnarray}$$ which after some algebra gives $$\begin{equation}
 r_{\rm m}(t) = r_{\rm m 0}+ 2 T \varv_0 \left( \sqrt{1+\frac{t}{T}} -1 \right)
  \label{earm}
,
\end{equation}$$ where we have defined $T \equiv M_0/(2\rho_0\Omega\,r_{\rm m 0}^2 \varv_0)$.

While this expression provides us with a more realistic description of the jet expansion than the constant velocity assumption adopted in Paper I, we stress that it is not to be taken as the real equation of motion of the jet but as the simplest way to parametrise the observed deceleration of it.

# Description of the model

In Paper I we adopted the jet model by Reynolds ((cite: reyn)) to describe the integrated flux density of the radio jet from S255IR NIRS 3. More specifically, we assumed what is defined as the ‘standard spherical’ case in Reynolds’ Table 1, namely a jet where the opening angle ($\theta_0$), internal velocity ($\varv_0$), ionisation degree ($x_0$), and temperature ($T_0$) do not depend on the distance $r$ from the star. Conservation of mass along the flow implies that the gas number density can be expressed as $n=n_0(r/r_0)^{-2}$.

Despite its simplicity, the model was successful in fitting the observed spectra in Paper I. However, Reynolds’ equations have been derived under the assumptions of small $\theta_0$, an approximation that is not satisfied by the best fit to the radio spectra obtained in Paper I (see Table 3 there), which requires angles as large as $\sim$50$^\circ$. In order to overcome this limitation, we propose here a slightly modified version of Reynolds’ model that works for any $\theta_0<90\ensuremath{^\circ}$.

To allow for an analytic solution of the equations, we maintain Reynolds’ assumption that the opacity depends only on $r$. This is equivalent to assuming that the jet is not conical but has a pyramidal shape with two faces parallel to the line of sight. We also assumed that the jet is delimited by two cylindrical surfaces, with radii $r_0$ and $r_{\rm m}$, and that its axis is inclined by a small angle, $\psi$, with respect to the plane of the sky. Figure [15](#fask) schematically illustrates the geometry of the jet, where the star lies at the origin of the axes and the line of sight is parallel to the $z$-axis.

![image](sketch-a.eps)\
![image](sketch-b.eps)

Following Reynolds, the absorption coefficient of the ionised gas and the opacity can be written as $$\begin{equation}
 \kappa(r) = \kappa_0 \left(\frac{r}{r_0}\right)^{-4}
,
\end{equation}$$ where $$\begin{equation}
 \kappa_0 = a_\kappa n_0^2 x_0^2 T_0^{-1.35} \nu^{-2.1}   \label{eakz}
,
\end{equation}$$ with $a_\kappa=0.212$ in CGS units, and $$\begin{eqnarray}
 \tau(R) & = & \int_{-R\tan(\theta_0-\psi)}^{R\tan(\theta_0+\psi)} \kappa \, {\rm d}{z} ~=~ \kappa_0 r_0^4 \int_{-R\tan(\theta_0-\psi)}^{R\tan(\theta_0+\psi)} \left(R^2+z^2\right)^{-2} \, {\rm d}{z} \nonumber \\
         & = & \frac{\kappa_0r_0^4}{2 R^3} \left[ \frac{\tan(\theta_0+\psi)}{1+\tan^2(\theta_0+\psi)} + \frac{\tan(\theta_0-\psi)}{1+\tan^2(\theta_0-\psi)} + 2\theta_0\right] \nonumber \\
         & = & \frac{\kappa_0r_0^4}{2 R^3} \left[ \sin(2\theta_0) \cos(2\psi) + 2\theta_0\right] \nonumber \\
         & = & \tau_0 \left(\frac{r_0}{R}\right)^3.   \label{eatau}
\end{eqnarray}$$ Here we have defined the two quantities $$\begin{equation}
 R=\sqrt{x^2+y^2}
\end{equation}$$ and $$\begin{equation}
\tau_0 = \kappa_0 r_0\frac{\sin(2\theta_0) \cos(2\psi) + 2\theta_0}{2}.
 \label{eatauo}
\end{equation}$$

To ease the comparison with Reynolds’ expressions, we indicate with $y_0$ and $y_{\rm m}$ the projections of $r_0$ and $r_{\rm m}$ on the plane of the sky, namely $y_0=r_0\cos\psi$ and $y_{\rm m}=r_{\rm m}\cos\psi$, and with $y_1$ the value of $R$ at which $\tau(R)=1$. From Eq. ([\[eatau\]](#eatau)) one has $$\begin{equation}
  
  y_1 = r_0\tau_0^\frac{1}{3}.    \label{eayu}
\end{equation}$$

For the calculation of the total flux density of the jet we follow Reynolds’ approach and assume that the emission between $R=0$ and $R=y_1$ is optically thick, and that between $R=y_1$ and $R=y_{\rm m}$ is optically thin. Under this approximation the flux can be written as $$\begin{eqnarray}
 S_\nu & = & \frac{1}{d^2} \int_{y_0}^{y_{\rm m}} B_\nu(T_0) \left(1-{\rm e}^{-\tau}\right) 2\theta'_0R \, {\rm d}{R} \nonumber \\
       & \simeq & \frac{2\theta'_0B_\nu(T_0)}{d^2} \left[ \int_{y_0}^{y_1} R \, {\rm d}{R} + \int_{y_1}^{y_{\rm m}} \tau(R) R \, {\rm d}{R} \right] \nonumber \\
       & = & \frac{2\theta'_0B_\nu(T_0)}{d^2} \left[ \frac{y_1^2-y_0^2}{2} + y_1^3 \left(\frac{1}{y_1}-\frac{1}{y_{\rm m}}\right) \right]
       \label{easnu}
,
\end{eqnarray}$$ where $B_\nu$ is the Planck function and $\theta'_0$ is the projection of $\theta_0$ on the plane of the sky. The two angles are related by the expression $$\begin{equation}
 \tan\theta'_0= \frac{\tan\theta_0}{\cos\psi}.
\end{equation}$$ We note that it is not strictly correct to integrate from $y_0$ to $y_{\rm m}$ because the projections of the two circles with radii $r_0$ and $r_{\rm m}$ on the plane of the sky are ellipses, and the integral should be made not only in the variable $R$ but also in the azimuthal angle. However, the approximation adopted by us is acceptable for small $\psi$.

The expression of $S_\nu$ in the case of a jet totally thin ($y_1<y_0$) or thick ($y_1>y_{\rm m}$) can be obtained in a similar way, by considering only the relevant approximation in the argument of the integral in Eq. ([\[easnu\]](#easnu)). In conclusion, one obtains $$\begin{eqnarray}
S_\nu & = & \frac{2\theta'_0B_\nu(T_0)}{d^2} \nonumber \\
& & \times \left\{ 
\begin{array}{lcl}
 y_1^3 \left(\frac{1}{y_0}-\frac{1}{y_{\rm m}}\right) & \Leftrightarrow & y_1\le y_0\\
\left[ \frac{y_1^2-y_0^2}{2} + y_1^3 \left(\frac{1}{y_1}-\frac{1}{y_{\rm m}}\right) \right]
            & \Leftrightarrow & y_0<y_1<y_{\rm m}\\ 
 \frac{y_{\rm m}^2-y_0^2}{2} & \Leftrightarrow & y_1\ge y_{\rm m}
\label{eaflux}
\end{array}
\right. 
.
\end{eqnarray}$$ We note that this expression gives the total flux emitted by a single jet lobe, whereas Eq. (5) of Paper I takes into account both lobes. The different approach is justified by the fact that our new findings have proved that only the NE lobe was present during our monitoring (see Sect. [4.1](#smmem)).

The quantity $y_1$ is a function of $n_0$, in addition to other parameters. However, following Reynolds, it may be convenient to express it in terms of the mass loss rate of the jet, $\dot{M}$, which is obtained by integrating the flux of mass through the inner surface of the jet. Obviously, $\dot{M}$ does not depend on the inclination of the jet with respect to the line of sight, so we can simplify the calculation by assuming $\psi=0$. Hence, we obtain $$\begin{eqnarray}
 \dot{M} & = & \int_{-r_0\tan\theta_0}^{r_0\tan\theta_0} \mu n_0\frac{r_0^2}{r_0^2+z^2} \varv_0\frac{r_0}{\sqrt{r_0^2+z^2}} 2\theta_0r_0\, {\rm d}{z} \nonumber \\
         & = & 4 \mu n_0\varv_0\theta_0r_0^4 \int_{0}^{r_0\tan\theta_0} \left(r_0^2+z^2\right)^{-\frac{3}{2}} \, {\rm d}{z} \nonumber \\
         & = & 4 \mu n_0\varv_0\theta_0r_0^2 \frac{\tan\theta_0}{\sqrt{1+\tan^2\theta_0}}
         \label{eamdot}
,
\end{eqnarray}$$ where $\mu$ is the mean particle mass per hydrogen atom (we assume $\mu=1.67\times10^{-24}$ g) and $\varv_0\frac{r_0}{\sqrt{r_0^2+z^2}}$ is the component of the velocity perpendicular to the inner surface of the jet. From this it is trivial to express $n_0$ as a function of $\dot{M}$, and from Eqs. ([\[eakz\]](#eakz)), ([\[eatauo\]](#eatauo)), and ([\[eayu\]](#eayu)) one obtains $$\begin{equation}
 y_1 = \left( \frac{a_\kappa}{16\mu^2} \Lambda^2 T_0^{-1.35} \nu^{-2.1} \,
              \frac{1+\tan^2\theta_0}{\tan^2\theta_0} \,
              \frac{\sin(2\theta_0)\cos(2\psi)+2\theta_0}{2\theta_0^2} \right)^\frac{1}{3}
,
\end{equation}$$ where we have defined $\Lambda\equiv x_0\dot{M}/\varv_0$.

Finally, a quantity of interest for our purposes is the ionised mass of the jet, which is given by the expression $$\begin{eqnarray}
 M_{\rm i}& = & \int_{-\theta_0}^{\theta_0} {\rm d}{\theta} \int_{r_0}^{r_{\rm m}} R \, {\rm d}{R} \int_{-R\tan\theta_0}^{R\tan\theta_0} \mu x_0n_0\frac{r_0^2}{R^2+z^2} \, {\rm d}{z} \\
  & = & 4 \mu x_0n_0\theta_0^2 r_0^2 \left(r_{\rm m}-r_0\right) \nonumber \\
  & = & \Lambda\theta_0\frac{\sqrt{1+\tan^2\theta_0}}{\tan\theta_0} \left(r_{\rm m}-r_0\right)
  \label{eamjet}
,
\end{eqnarray}$$ where we have used Eq. ([\[eamdot\]](#eamdot)) to replace $n_0$.

[^1]: Based on observations carried out with the VLA and ALMA.

[^2]: The Common Astronomy Software Applications software can be downloaded at http://casa.nrao.edu

[^3]: https://hera.ph1.uni-koeln.de/$\sim$sanchez/statcont

[^4]: Available at http://vlbi.sci.ibaraki.ac.jp/iMet/data/192.6-00

[^5]: The M2O is a global cooperative of maser monitoring programmes; see https://MaserMonitoring.org

[^6]: We stress that our definition of $\theta_0$ corresponds to one-half of the $\theta_0$ defined by Reynolds ((cite: reyn)).

</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[0].what.evidence[1]",
  "value": "Initial jet expansion velocity v_0 = 900 km s^-1, inclination angle to plane of sky psi = 10 deg (i = 80 deg), ionised gas temperature T_0 = 10^4 K, and chi^2 minimisation formulation (Eq. 10 of Paper I)",
  "failed_quote": "To simplify the fitting procedure as much as possible, we fixed $T_0=10^4$ K and $\\psi=10\\ensuremath{^\\circ}$ (see Paper I), and computed $y_{\\rm m}$ from Eq. ([eymnum])."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Integrate flux density inside a polygonal shape encompassing the compact source across VLA bands and ALMA 3 mm maps; subtract fiducial large-scale lobe flux (1.8 mJy at 6 GHz, 1.0 mJy at 10 GHz) in D-array when needed; separate NE and SW components at 3 mm.",
  "failed_quote": "The flux density of the compact, variable source centred on S255IR NIRS 3 has been estimated inside a polygonal shape encompassing the compact, unresolved radio source and is given in Table [tflux] for each band and epoch."
 },
 {
  "path": "analysis_steps[2].method.evidence[2]",
  "value": "Create continuum maps for the four ALMA Band 3 spectral windows (85.2, 87.2, 97.2, 99.2 GHz) with identical clean beams, fit pixel-by-pixel spectral index alpha where all four fluxes exceed 5 sigma, and calculate the free-free flux fraction R_S/(1+R_S).",
  "failed_quote": "After some algebra, we obtain the ratio $R_{\\rm S} \\equiv \\frac{S^{\\rm ff}_{\\nu_1}}{S^{\\rm d}_{\\nu_1}} = \\frac{\\left(\\frac{\\nu_2}{\\nu_1}\\right)^\\gamma - \\left(\\frac{\\nu_2}{\\nu_1}\\right)^\\alpha}{\\left(\\frac{\\nu_2}{\\nu_1}\\right)^\\alpha - \\left(\\frac{\\nu_2}{\\nu_1}\\right)^{-0.1}}$ and, from this, the fraction of the total flux due to free-free emission, $R_{\\rm S}/(1+R_{\\rm S})$."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Generate synthetic 2D brightness temperature maps of an optically thin jet (T_B = T_0 (y/y_0)^-3), convolve with the ALMA beam, fit to the observed NE lobe at t = 1061 and 1881 days to find y_0, y_m, and theta_0, and solve the momentum-conserving deceleration equation for T and y_m0.",
  "failed_quote": "From Eq. ([eym]) written for $t$=1061 days and $t$=1881 days, one obtains a system of two equations in the two unknowns $T$ and $y_{\\rm m 0}$, the solutions to which are $T$=124 days and $y_{\\rm m 0}$=251 au."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "t = 1061 days and t = 1881 days; v_0 = 900 km s^-1; psi = 10 deg",
  "failed_quote": "The value of $r_{\\rm m}$ can be computed from Eq. ([eym]) assuming $\\psi$=10$^\\circ$ (see Paper I, where the complementary angle $i=90\\ensuremath{^\\circ}-\\psi=80\\ensuremath{^\\circ}$ was used)."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Grid search over y_0, y_m, and theta_0 minimising pixel-by-pixel chi^2 = sum (T_B^i(model) - T_B^i(data))^2",
  "failed_quote": "The best fit was obtained by minimising the expression $\\chi^2=\\sum_i \\left(T_{\\rm B}^i({\\rm model})-T_{\\rm B}^i({\\rm data})\\right)^2$, with $i$ a generic pixel, after varying the three parameters over suitable ranges."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Fit the modified mono-polar Reynolds jet model (Eq. A.10) to each VLA continuum spectrum at nu >= 6 GHz across 16 epochs by varying theta_0, r_0, and Lambda, then compute the ionised jet mass M_i(t) and ejection-to-accretion ratio R_e.",
  "failed_quote": "All observed spectra have been fitted with Eq. ([eaflux]) using only the measurements with $\\nu$$\\ge$6 GHz, for the reasons discussed in Sect. 3.2."
 },
 {
  "path": "analysis_steps[4].method.evidence[2]",
  "value": "Fit the modified mono-polar Reynolds jet model (Eq. A.10) to each VLA continuum spectrum at nu >= 6 GHz across 16 epochs by varying theta_0, r_0, and Lambda, then compute the ionised jet mass M_i(t) and ejection-to-accretion ratio R_e.",
  "failed_quote": "This hypothesis is confirmed by Fig. 14, which shows how the ionised jet mass, computed from Eq. ([eamjet]), varies with time."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "Fixed T_0 = 10^4 K, psi = 10 deg, y_m(t) from Eq. 6, mu = 1.67e-24 g; grid ranges theta_0 = 3-50 deg, r_0 = 50-300 au, Lambda = 10^-10 to 10^-7 M_sun yr^-1 / (km s^-1)",
  "failed_quote": "To simplify the fitting procedure as much as possible, we fixed $T_0=10^4$ K and $\\psi=10\\ensuremath{^\\circ}$ (see Paper I), and computed $y_{\\rm m}$ from Eq. ([eymnum])."
 },
 {
  "path": "analysis_steps[4].validation.evidence[1]",
  "value": "Independent lower limit on opening angle theta_0^min derived from observed peak synthesised-beam brightness temperature T_SB assuming optically thick Gaussian source (Eq. 9) and comparison with theoretical MHD jet models (Staff et al. 2019)",
  "failed_quote": "We conclude that, despite the crude approximations adopted to derive Eq. ([etho]), values of $\\theta_0$ of a few times 10$^\\circ$ seem plausible and consistent with our model fit results."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "ALMA 92.2/92.5 GHz total continuum flux density (2019/6/6, day 1061) = 46.0 mJy",
  "failed_quote": "| 92.2 | — | — | — | | 46.0 (22.8)$^f$ | | 42.3 (18.8)$^f$ | | |"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "ALMA 92.2/92.5 GHz total continuum flux density (2021/9/3, day 1881) = 42.3 mJy",
  "failed_quote": "| 92.2 | — | — | — | | 46.0 (22.8)$^f$ | | 42.3 (18.8)$^f$ | | |"
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Jet deceleration timescale T = 124 days",
  "failed_quote": "From Eq. ([eym]) written for $t$=1061 days and $t$=1881 days, one obtains a system of two equations in the two unknowns $T$ and $y_{\\rm m 0}$, the solutions to which are $T$=124 days and $y_{\\rm m 0}$=251 au."
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Initial projected outer radius y_m0 at radio burst onset = 251 au",
  "failed_quote": "From Eq. ([eym]) written for $t$=1061 days and $t$=1881 days, one obtains a system of two equations in the two unknowns $T$ and $y_{\\rm m 0}$, the solutions to which are $T$=124 days and $y_{\\rm m 0}$=251 au."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "In compact VLA configurations (B, C, D) at long wavelengths (1.5-10 GHz), the central compact source cannot be fully separated from the 8'' large-scale lobes, making those flux measurements upper limits even when subtracting a fiducial A-array lobe flux.",
  "failed_quote": "At the longest wavelengths it was possible to resolve the central source from the lobes only in the most extended array configuration. In the other cases, we could only measure the total flux density from all components and the corresponding values are reported in Table [tflux] as upper limits."
 }
]
```
