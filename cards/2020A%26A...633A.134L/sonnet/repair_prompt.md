# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...633A.134L\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Molecular outflows in local galaxies: Method comparison and a role of intermittent AGN driving

# Introduction

|  |  |  |  |  |  |  |  |
|:---|---:|---:|---:|:--:|:--:|:--:|:--:|
| Source | cz$_{\rm h}$ | RA | DEC | Date(s) | Min, Max | RMS (20km/s) | Beam |
|  | km/s | J2000 | J2000 |  | baseline \[m\] | mJy/beam | arcsec |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |
| III Zw 035 | 8221 | 01:44:30.71 | 17:06:07.6 | 07/2016 - 02/2018 | 18.4, 760.0 | 0.30 | 1.42$\times$0.94 |
| NGC 2623 | 5524 | 08:38:24.08 | 25:45:16.7 | 05/2017 - 09/2017 | 15.0, 174.1 | 0.75 | 4.03$\times$3.33 |
| IC 860 | 3889 | 13:15:03.53 | 24:37:07.9 | 08/2016 - 11/2016 | 15.0, 303.4 | 0.92 | 2.81$\times$1.79 |
| NGC 7479 | 2387 | 23:04:56.65 | 12:19:22.3 | 05/2016 - 06/2016 | 15.0, 262.0 | 1.15 | 2.98$\times$2.27 |
| IRAS F05189-2524 | 12843 | 05:21:01.47 | -25:21:45.4 | 09/2015 | 15.1, 1600 | 0.37 | 0.52$\times$0.47 |
| IRAS F09111-1007W | 16276 | 09:13:36.38 | -10:19:28.2 | 12/2016 | 15.1, 460.0 | 0.33 | 1.84$\times$1.47 |
| IRAS F10173+0828 | 14687 | 10:20:00.26 | 08:13:33.6 | 12/2016 | 15.1, 460.0 | 0.34 | 1.84$\times$1.68 |
| IRAS F12224-0624 | 7938 | 12:25:03.91 | -06:40:52.0 | 12/2016 | 15.1, 491.0 | 0.37 | 1.76$\times$1.53 |
| NGC 4418 | 2099 | 12:26:54.65 | -00:52:38.4 | 01/2017 | 15.1, 460.0 | 0.58 | 1.62$\times$1.19 |
| IRAS 13120-5453 | 9308 | 13:15:06.20 | -55:09:24.0 | 07/2015 - 08/2016 | 15.1, 1800 | 0.65 | 0.54$\times$0.52 |
| IRAS F14378-3651 | 20417 | 14:40:59.01 | -37:04:32.0 | 07/2015 | 43.3, 1600 | 0.67 | 0.57$\times$0.51 |
| IRAS F17207-0014 | 12825 | 17:23:21.98 | -00:17:01.7 | 01/2017 | 15.1, 452.8 | 0.46 | 2.52$\times$1.87 |
| IRAS F20551-4250 | 12891 | 20:58:26.79 | -42:39:00.3 | 06/2015 | 43.3, 1600 | 0.64 | 0.57$\times$0.45 |

Table notes: Observations obtained with NOEMA (top) and ALMA (bottom).\
(1) Source name\
(2) Heliocentric radial velocity based on our CO(1-0) data\
(3), (4) Coordinates of adopted phase center. See Table [\[tab:continuum\]](#tab:continuum) for the measured position of mm continuum.\
(5) Observation period\
(6) Interferometer baselines used\
(7) RMS sensitivity for a 20 km/s channel width\
(8) Beam size

|  |  |  |  |  |  |  |  |
|:---|---:|---:|:--:|:--:|:--:|:--:|---:|
| Source | RA | DEC | E(RA) | E(DEC) | FWHM | $\nu_{\rm Obs}$ | S$_{\rm \nu ,Obs}$ |
|  | J2000 | J2000 | arcsec | arcsec | arcsec | GHz | mJy |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |
| III Zw 035 | 01:44:30.538 | 17:06:08.68 | 0.01 | 0.01 | 0.43$\pm$0.01 | 112.2 | 3.84$\pm$0.03 |
| IRAS F05189-2524 | 05:21:01.401 | -25:21:45.28 | 0.01 | 0.01 | 0.17$\pm$0.03 | 104.1 | 2.40$\pm$0.03 |
| NGC 2623 | 08:38:24.087 | 25:45:16.67 | 0.01 | 0.02 | 1.22$\pm$0.06 | 113.2 | 6.40$\pm$0.08 |
| IRAS F09111-1007W | 09:13:36.452 | -10:19:30.00 | 0.01 | 0.01 | 0.76$\pm$0.11 | 102.3 | 1.33$\pm$0.03 |
| IRAS F09111-1007E | 09:13:38.829 | -10:19:19.98 | 0.01 | 0.01 | $<$3.12 | 102.3 | 0.62$\pm$0.12 |
| IRAS F10173+0828 | 10:20:00.203 | 08:13:33.93 | 0.01 | 0.01 | $<$0.75 | 102.9 | 1.72$\pm$0.03 |
| IRAS F12224-0624 | 12:25:03.909 | -06:40:52.63 | 0.01 | 0.01 | $<$0.48 | 105.8 | 2.33$\pm$0.33 |
| NGC 4418 | 12:26:54.610 | -00:52:39.45 | 0.01 | 0.01 | 0.17$\pm$0.05 | 107.7 | 11.13$\pm$0.04 |
| IC 860 | 13:15:03.505 | 24:37:07.70 | 0.01 | 0.01 | $<$0.54 | 113.8 | 6.64$\pm$0.08 |
| IRAS 13120-5453 | 13:15:06.328 | -55:09:22.80 | 0.01 | 0.01 | 0.89$\pm$0.03 | 105.3 | 10.07$\pm$0.16 |
| IRAS F14378-3651 | 14:40:59.013 | -37:04:31.91 | 0.01 | 0.01 | 0.37$\pm$0.05 | 101.4 | 1.47$\pm$0.06 |
| IRAS F17207-0014 | 17:23:21.959 | -00:17:00.91 | 0.01 | 0.01 | 0.66$\pm$0.06 | 104.1 | 8.70$\pm$0.06 |
| IRAS F20551-4250 | 20:58:26.792 | -42:39:00.29 | 0.01 | 0.01 | 0.25$\pm$0.03 | 104.1 | 2.78$\pm$0.05 |
| NGC 7469 | 23:04:56.634 | 12:19:22.67 | 0.04 | 0.04 | 0.89$\pm$0.15 | 114.4 | 1.77$\pm$0.09 |

Table notes: Results are from UV fitting a Gaussian model to the NOEMA continuum visibilities, and from fitting a Gaussian model to the ALMA continuum image. IRAS F09111-1007E is not part of our sample but detected along with IRAS F09111-1007W.\
(1) Source name\
(2), (3) Continuum position\
(4), (5) Uncertainties of position. These include only the formal fit errors, to which 2–5% of the beam size should be added to account for phase calibration stability (cite: almatechhandbook18)\
(6) Intrinsic source full width at half maximum FWHM (beam-deconvolved)\
(7) Observed Frequency\
(9) Total continuum flux density from Gaussian fit.

Gas outflows triggered by intense star formation and/or active galactic nuclei are important agents in the evolution of galaxies, in regulating the fraction of baryons inside a dark matter halo that are converted to stars, and for the metal enrichment of the circumgalactic and intergalactic medium (cite: veilleux05; fabian12). A significant step forward in characterizing the *molecular* phase of outflows from local galaxies has been made recently via detection of P-Cygni profiles of far-infrared OH lines (cite: fischer10; sturm11; veilleux13; spoon13; gonzalez-alfonso17) and detection of broad line wings to the mm emission lines of CO (cite: feruglio10; alatalo11; cicone14; pereira-santaella18; fluetsch19). Molecular outflows have been detected preferentially but not exclusively in dusty (ultra)luminous infrared galaxies ((U)LIRGs). Outflow rates $\dot{M}_{\rm out}$ up to several 100 M$_\odot$ yr$^{-1}$ and mass loading factors $\dot{M}_{\rm out}$/SFR around and significantly above 1 have been observed. In extreme cases and if velocities are high enough to escape the galaxy, extrapolation of the current outflow rate would clear out most of a galaxy’s gas content within $10^7$ yr. While both star formation and active galactic nuclei (AGN) may contribute to driving outflows, the OH outflow velocity in ULIRGs as well as the CO-based outflow rates seem to be best correlated with AGN luminosity (cite: veilleux13; cicone14; fiore17; fluetsch19). Ionized, atomic, and molecular gas phases may all significantly contribute to the outflow rates (cite: contursi13; rupke13; janssen16; rupke17), in this paper we focus on the usually dominant molecular phase. There is a continuum of properties from the fast and energetic outflows reported in the studies mentioned above, towards smaller scale and typically slower and less energetic molecular outflows. These are increasingly reported from high spatial and spectral resolution ALMA and NOEMA interferometric studies of nearby galaxies (cite: combes14; querejeta16; salak16; slater19; ramakrishnan19; alonsoherrero19; combes19), along with indications for inflow, warps, and for non-circular motions in complex, for example barred, potentials. Here, we focus on fast and energetic outflows with potential non-local impact.

|  |  |  |  |  |  |  |
|:---|---:|---:|---:|---:|---:|---:|
| Source | $S_{\rm CO}$ (gauss) | $S_{\rm CO}$(wings) | $\Delta v$ | $FW_{10\% }$ | $v_{\rm out}$ | $R_{\rm out}$ |
|  | Jy km s$^{-1}$ | Jy km s$^{-1}$ | km s$^{-1}$ | km s$^{-1}$ | km s$^{-1}$ | $''$ |
| III Zw 035 | 41.05 | 14.25 | 23 | 579 | 313 | 4.00 |
| IRAS F05189-2524 | 2.85 | 1.11 | 60 | 771 | 446 | 1.24 |
| NGC 2623 | 3.21 | 0.92 | -33 | 1108 | 587 | 1.62 |
| NGC 2623 fossil |  | 0.37 |  |  | 400 | 14.00 |
| IRAS F09111-1007W | 3.34 | 0.95 | -9 | 644 | 331 | 0.58 |
| IRAS F10173+0828 |  | $<$0.22 |  |  |  |  |
| IRAS F12224-0624 | 0.84 | 0.35 | 2 | 1128 | 566 | 0.50 |
| NGC 4418 | 2.53 | 0.43 | 9 | 630 | 324 | 0.23 |
| IC 860 |  | $<$0.58 |  |  |  |  |
| IRAS 13120-5453 | 34.50 | 4.29 | 1 | 588 | 301 | 0.63 |
| IRAS F14378-3651 |  | $<$0.43 |  |  |  |  |
| IRAS F17207-0014 | 0.84 | 0.49 | -514 | 1203 | 1116 | 0.45 |
| IRAS F20551-4250 | 0.98 | 0.40 | 96 | 787 | 490 | 0.27 |
| NGC 7479 |  | $<$0.73 |  |  |  |  |

Table notes: See Sect. [3](#sect:outprop) for definitions and methods to measure these quantities.

Thanks to efficient *Herschel* spectroscopy, the best statistics up to now is available from searches for OH P-Cygni absorptions. For those, the step from measuring outflow kinematics (cite: veilleux13; stone16) to deriving outflow masses and outflow rates involves complex modeling (cite: sturm11; gonzalez-alfonso17; stone18). For the CO-based searches, the obvious and highly desirable next steps are to extend the local galaxy samples under study, and to broaden the range of galaxy parameters covered. Additional value can come from truly spatially resolved studies of very nearby outflow sources.

Three major sources of uncertainty currently affect the derivation of molecular outflow rates from interferometric CO data: (i) the emission from outflowing gas has to be separated from that of the host; (ii) a CO conversion factor has to be adopted to convert from luminosity to gas mass, but may not necessarily be the same as for typical Galactic molecular clouds; (iii) if only an outflow velocity and overall size are known, the conversion from outflow mass to outflow rate is uncertain by at least a factor of three due to different possible geometrical assumptions (cite: cicone14; veilleux17). Poorly known inclination of the outflow can add to these geometrical uncertainties.

Even if separated reliably from gas orbiting in the host, the outflowing gas will face a different fate depending on its velocity and the depth of the potential. There is a continuum from ‘fountains’ that will re-join the host in much less than a Gyr, to gas staying in the circumgalactic medium for longer periods until being re-accreted, and to gas able to escape the galaxy’s dark matter halo. In Sect. [3](#sect:outprop) below we conservatively identify outflowing gas with line wings only. This emphasizes the second and third path, but at typical escape velocities of order 600 km s$^{-1}$ the fraction of gas truly escaping a galaxy’s potential is typically small if ballistic motion is assumed (cite: fluetsch19). Focus on fast wings outside the galaxy’s line core also avoids ambiguities between more modest velocity outflow and other non-circular motions such as inflow or flows in the potential of a stellar bar.

Using *Herschel* 70 $\mu$m data, (cite: lutz16) and (cite: lutz18) derive sizes of the far-infrared emission region for large samples of local galaxies, in order to derive scaling relations of far-infrared size and surface brightness with salient galaxy properties, and establish that AGN hosts preferentially have more compact star formation than non-active galaxies. This sample can be used for an objective selection of compact far-infrared sources (cite: lutz16), based on observations in the *Herschel* archive that are not affected by bright neighbors. The 18 sources in that table include several for which CO outflows have been recently detected, as one might expect for their high far-infrared surface brightness $\Sigma_{\rm FIR}$ $\gtrsim 10^{11.75}$ L$_\odot$ kpc$^{-2}$. If star formation powers the far-infrared, this is well beyond thresholds in star formation rate surface density above which star formation-driven outflows from galaxy disks tend to be observed in the local universe (cite: heckman02) or at high redshift (cite: newman12; davies19). Alternatively, if an AGN significantly contributes to the observed far-infrared emission, it must be luminous and could drive an outflow. The likelihood of hosting outflows, and the sample’s proximity (z=0.0072 to 0.0676 with median 0.027) make it an obvious basis for a search for local outflow laboratories, well suited for detailed study.

We here report on a NOEMA and ALMA search for CO(1-0) outflows in galaxies from the (cite: lutz16) sample of compact far-infrared galaxies that lack previous deep CO data, and discuss the results in conjunction with literature results for the remainder of the sample and outside the sample’s definition criteria. We adopt an $\Omega_m =0.3$, $\Omega_\Lambda =0.7$ and $H_0=70$ km s$^{-1}$ Mpc$^{-1}$ cosmology, redshift-independent distances from the NASA Extragalactic Database (NED), if available, for z$<$0.01 galaxies, a (cite: chabrier03) initial mass function (IMF), a conversion for far-infrared luminosity to star formation rate (SFR) ${\rm SFR} = 1.9\times 10^{-10}~L_{\rm FIR=40-120\mbox{$\mu$m}}$ as appropriate for the (cite: kennicutt98) conversion scaled to Chabrier IMF, and $L_{\rm IR}$(8–1000 $\mu$m)/$L_{\rm FIR}$(40–120 $\mu$m)=1.9.

![](outflowgauss_visu.pdf)

# Sample and Observations

## NOEMA observations

Observations for the DEC$>$10$^\circ$ targets were taken with the IRAM NOrthern Extended Millimeter Array (NOEMA) on Plateau de Bure between May 2016 and February 2018 (Projects s16bh, s17ar, w17cp). CO(1-0) was observed in the 3 mm band, mostly using the WideX correlator (3.6 GHz bandwidth) and typically 6 or 7 antennae in configurations between C and D. These low 2–4$''$ spatial resolution configurations were chosen to initially provide maximum detection sensitivity, and not over-resolve faint and possibly extended high velocity outflow components.

Table [\[tab:observations\]](#tab:observations) lists the baselines used, achieved RMS sensitivity per beam for a 20 km s$^{-1}$ channel, and beam size. For III Zw 035, a strong outflow was detected and already spatially resolved in the low resolution data. This source was followed up in the higher resolution A configuration using the new PolyFix correlator and new receivers. The combined data yield the smaller beam listed for this source in Table [\[tab:observations\]](#tab:observations).

Calibration and mapping followed standard procedures in the GILDAS[^1] environment (cite: guilloteau00). For CO-bright and compact sources (III Zw 035, IC 860, NGC 2623), self calibration was able to improve the dynamic range in the channels with bright line emission, this is of little impact for the detection of outflow wings and continuum, though. Velocities quoted below are relative to our CO-based heliocentric redshifts as listed in Table [\[tab:observations\]](#tab:observations). Millimeter continuum emission was clearly detected for all sources. Positional offsets quoted below are relative to the continuum positions that are listed along with other continuum properties in Table [\[tab:continuum\]](#tab:continuum). The continuum was subtracted from the visibilities, and all line information is based on continuum free visibilities or spectral cubes. The observations were targeted at CO(1-0), for which we derived spectral cubes at 20, 60, and 200 km s$^{-1}$ resolution and occasionally used in addition data for velocity ranges specifically tailored to the outflow properties of a given source. Total fluxes for CO and some other transitions detected in the wide spectral bandwidth are listed in Table [\[tab:applines\]](#tab:applines).

## ALMA observations

The DEC$<$10$^\circ$ targets were observed with the Atacama Large Millimeter/submillimeter Array (ALMA) Cycle 4 program 2016.1.00177.S in late 2016 to early 2017, using between 38 and 46 antennae. Again, the CO(1-0) line was observed in a relatively compact configuration yielding an $\approx$2$''$ beam in ALMA Band 3, and observational parameters are listed in Table [\[tab:observations\]](#tab:observations). The pipeline-calibrated data were mapped using standard CASA (cite: mcmullin07) procedures. Three more sources from Table 1 of (cite: lutz16) were already observed in CO(1-0) in ALMA program 2012.1.00306.S (PI E. Sturm) using $\sim$0.5$''$ beams. For IRAS 13120-5453, we combined our 2012.1.00306.S CO(1-0) data with a similar dataset from 2015.1.00287.S (PI K. Sliwa), in order to improve signal-to-noise. Again, we mapped the calibrated data in CASA and include the fourth target of 2012.1.00306.S, IRAS F20511-4250, which falls just below the criteria of Table 1 of (cite: lutz16).

In reducing the ALMA data, we adopted the same channel widths as for the NOEMA data. Self calibration was applied for IRAS F09111-1007W, NGC 4418, IRAS F17207-0014, IRAS F20551-4250 but not the other sources for which we found no noticeable improvement.

# Outflow properties of the targets

First, we determine whether an outflow is present, and then measure its CO flux, velocity, and size. Outflow identification can be relatively straightforward in cases where an extremely broad outflow line component is superposed on a core of velocity width that is typical for undisturbed gas moving in a galaxy’s gravitational potential. This distinction is more difficult if the velocity range with observed ‘broad’ CO emission does not strongly exceed plausible non-outflow rotational velocities within the galaxy’s potential. Different radial distributions of molecular gas disks rotating in the potential, misaligned disk components, bar flows, or gas moving in the potential of a merger all can lead to quite complex total line profiles over a velocity range that is similar to local circular velocities. For outflows from spatially resolved disks in regular rotation, the kinematic separation of outflowing and non-outflowing gas can be improved by removing the regular velocity field (cite: newman12), but this approach is less suited for a sample of compact nuclei that also includes mergers. Needing two Gaussian components for a satisfactory fit of the line profile is alone not sufficient to ascribe the broader component to an outflow.

We hence continue with a brief discussion of individual targets on the basis of total CO maps and selected channel maps, spectra, positions in different velocity channels, and position-velocity diagrams, and visualize in Figures [13](#fig:iiizw035) to [25](#fig:ngc7479) such basic CO(1-0) properties. As appropriate for the observed spatial extent of an outflow, we extract nuclear or aperture spectra and fit multiple Gaussians to the spectrum which, is the sum of host emission and (if present) broad outflow. Visual inspection is used to choose the number of Gaussians needed to fit the host emission. Fig. [1](#fig:outflowgauss_visu) illustrates the adopted conventions for outflow velocity and flux. For intrinsically somewhat asymmetric outflows and little obscuration, the shift $\Delta v$ of the broad component can take positive as well as negative values, this is indeed observed (Table [\[tab:outobs\]](#tab:outobs)). Unless mentioned otherwise, we adopt as outflow velocity

$$\begin{equation}
v_{\rm out}= |\Delta v| + \frac{FW_{10\%}} {2}
\label{eq:voutdef}
\end{equation}$$

computed from the shift of the centroid of the broad Gaussian line component for the outflow with respect to the systemic velocity, and the full width at a tenth of the maximum of this broad outflow component. With this definition, $v_{\rm out}$ will be in the line profile wings that are dominated by the outflow. Because outflow components at velocities that also show host CO emission are hard to quantify, we quote below in Table [\[tab:outobs\]](#tab:outobs) two measured CO fluxes for the outflow: $S_{\rm CO}$ (gauss) is the integral of the full Gaussian broad line component, while $S_{\rm CO}$(wings) integrates this Gaussian only over the range(s) where the outflow dominates emission (i.e., contributes more than 50% of the total fitted profile). In further analysis, we adopt the more conservative $S_{\rm CO}$(wings). This is similar to the integration of wings only (cite: cicone14) or to removal of host flux on the basis of a disk model (cite: veilleux17; herrera-camus19), but different from adopting the full broad Gaussian flux as in several other references in the literature. For objects without outflow detection, we assign limits for the outflow CO flux: $S_{\rm CO,wings} < 10\times RMS_{200} \times 200$, based on the RMS noise (Jy/beam) over a 200 km s$^{-1}$ channel. Using here a factor 10 rather than 3 considers that undetected outflows may be spatially extended or spectrally broad. The outflow radius is directly taken from the maps for a few well resolved outflows, otherwise we derive a radius

$$\begin{equation}
R_{\rm out}= |\Delta R| + FWHM/2
\label{eq:routdef}
\end{equation}$$

Here, $|\Delta R|$ is the spatial shift between line position and continuum position and FWHM refers to the line emission. Both line position and FWHM are derived from a Gaussian spatial fit in the UV plane using a velocity range that is dominated by outflow, i.e. by the broad component of the spectral multi-Gaussian fit. $R_{\rm out}$ is effectively a beam-deconvolved intrinsic radius. For symmetric bipolar outflow we use average properties of the two lobes. We do not attempt to correct the measured $R_{\rm out}$ or $v_{\rm out}$, or the literature results adopted in Sect [3.2](#sect:literature), for the effects of outflow opening angle and inclination. This emphasizes homogeneity of results with respect to more complete information that may be available for a few of the best spatially resolved and strongly collimated outflows. Observed outflow quantities or limits are listed in Table [\[tab:outobs\]](#tab:outobs).

## Properties of individual targets

**III Zw 035** (Fig. [13](#fig:iiizw035)): Extended CO emission is centered on the brighter northern lenticular-shaped component of this galaxy pair (cite: kim13). The second fainter optical component, offset roughly along the major axis of the brighter galaxy by $\sim$7$''$ toward PA $\sim$200$^\circ$, does not stand out in CO emission or kinematics. On top of this extended disk-like CO emission with a weak SW-NE velocity gradient that does not strictly follow the galaxy’s major axis, we detect a strong and asymmetric spatially resolved bipolar CO outflow up to velocities of $\pm$500 to 600 km/s. The outflow has PA$\sim$-45$^\circ$ and we adopt as $R_{\rm out}$ the 4$''$ extent of its stronger NW (redshifted) side.

The line profile in an r=3$''$ aperture, offset by 1$''$ each to N and W, includes both sides of the outflow and is well fit by the sum of three Gaussians. One is narrow and the other two are broad and (on average) redshifted, with FWHM 270 km s$^{-1}$ and 633 km s$^{-1}$. We assign both broad components to the outflow. The sum of the two broad Gaussians dominates the flux within this aperture at all velocities. Hence, it is not possible to follow our standard procedure and separate the outflow line wings from the line core at a velocity where the outflow starts to dominate the line profile. Instead, guided by the PV diagrams, we adopt the velocity range from -120 km s$^{-1}$ to 120 km s$^{-1}$ as line core and include into our ‘wings’ CO flux only emission from both broad components that is outside that range. The adopted $\Delta v$, $FW_{10\%}$ and $v_{\rm out}$ are the flux-weighted means of the respective values for the two broad components.

**IRAS F05189-2524** (Fig. [14](#fig:f05189)): Extended CO emission centered on the nucleus shows only little velocity change on 1–2$''$ scales, consistent with a mostly face-on view of this Type 1 AGN host. A gradient from approaching (W) to receding (E) velocities is seen in the inner 0.3$''$. Beyond the $\sim\pm$200 km s$^{-1}$ covered by these host structures, a clear red wing reaches out to $\sim$500 km s$^{-1}$ and traces an outflow. This emission is extended and we use an r=1$''$ aperture to extract its flux (green component in the multi-Gaussian fit of Fig. [14](#fig:f05189) top right). There may be a hint of near-nuclear blueshifted emission down to $\sim$-1000 km s$^{-1}$, but this nowhere reaches $>$3$\sigma$, and hence is not discussed further. We adopt $v_{\rm out} = 446$ km s$^{-1}$ from the Gaussian fit to the r$<$1$''$ outflow spectrum, and $R_{\rm out} = 0.41\ensuremath{''} +0.5\times 1.66$$''$ from a Gaussian spatial fit to the 210–510 km s$^{-1}$ visibilities.

**NGC 2623** (Fig. [15](#fig:ngc2623)): The inner 2$''$ shows a roughly E/W velocity gradient from gas rotating around the nucleus of this merger. At $|v|>$300 km s$^{-1}$, line wings trace a bipolar outflow in approximately N/S (polar) direction. We adopt $v_{\rm out} = 587$ km s$^{-1}$ from the fit to the r$<$4$''$ outflow spectrum and $R_{\rm out} = 1.62$$''$ from averaging the properties of the blue and red outflows at $|v|=[300,500]$ km s$^{-1}$.

In addition to the bipolar outflow with its blue component shifted to the N, the \[-500,-300\] km s$^{-1}$ channel shows emission at $\sim$14$''$ from the nucleus, at PA$\sim$130$^\circ$. This emission peaks at 4.2$\sigma$ and has total flux 0.37 Jy km s$^{-1}$. Given the quite distinct morphology, we do not assign this emission to the main bipolar outflow but interpret it as the result of an earlier outflow episode with different orientation (see also Sect. [5.3](#sect:intermittent)). We list this outflow as ‘NGC 2623 fossil’.

**IRAS F09111-1007W** (Fig. [16](#fig:f09111)): The inner 2$''$ shows a roughly E/W velocity gradient from gas rotating around the nucleus of this galaxy, which is part of a wide pair. At $|v|\gtrsim 200$ km s$^{-1}$, line wings trace a bipolar outflow in approximately N/S (polar) direction. We adopt $v_{\rm out} = 331$ km s$^{-1}$ from the fit to the nuclear outflow spectrum and $R_{\rm out} = 0.58$$''$ from averaging the properties of the blue and red outflows at $|v|=[210,510]$ km s$^{-1}$.

**IRAS F10173+0828** (Fig. [17](#fig:f10173)): A rotating disk with kinematic major axis at PA$\sim$45$^\circ$ is seen out to radius $\sim$8$''$. The bright and compact nuclear CO emission does not obviously connect to this rotating disk and has wings out to $\pm$300km s$^{-1}$, beyond the $\pm$100 km s$^{-1}$ LOS velocities of the disk. While this could indicate a modest velocity outflow, we cannot firmly exclude bound motion in the near-nuclear potential and hence assign an upper limit to the emission of a faster molecular outflow.

**IRAS F12224-0624** (Fig. [18](#fig:f12224)): Weak blue- and redshifted outflow components are 4$\sigma$ detected in addition to bright spatially compact CO that has a velocity gradient along PA$\sim$-30$^\circ$. We adopt $v_{\rm out} = 566$ km s$^{-1}$ from the fit to the nuclear outflow spectrum. The spatial width of the weak outflow is very poorly constrained, we adopt a fiducial $R_{\rm out} = 0.5$$''$.

**NGC 4418** (Fig. [19](#fig:ngc4418)): CO emission shows a compact core that is on average redshifted by $\approx$15 km s$^{-1}$ relative to the extended emission. The redshift in Table [\[tab:observations\]](#tab:observations) refers to extended emission at radii 3–8$''$. At first glance, the nuclear spectrum and PV diagram suggest a strong red and a weak blue wing to CO(1-0). But the compact, warm and dense nuclear region of NGC 4418 is known to have a rich chemistry and a complex mm/submm spectrum (cite: sakamoto13; costagliola15), so that sensitive ALMA data detect rare molecules in addition to CO and CN, which are detected for all sources of the sample within the frequency range of our data. Specifically, there is emission near $\sim$-740 km s$^{-1}$ relative to CO, which we identify with emission from the nitrogen sulfide radical NS, $J=5/2-3/2$ at $\sim$115.55 GHz rest frequency (cite: aladro15; meier15). This includes six hyperfine components, and $\Lambda$-doubling means that similar strength NS emission is superposed on the red wing of CO at $\sim$290 km s$^{-1}$, with another six hyperfine components at $\sim$115.15 GHz rest. We use the ‘blue’ complex and local thermal equilibrium line ratios for the 6+6 lines in the blue and red complex (M. Drosdovskaya, priv. comm.) to infer and subtract contamination by NS for the red wing of CO. The adopted intensities are for T=150 K but the relative strength of blue and red complex varies by less than a percent between 100 and 200 K, the range of central dust temperatures suggested for NGC 4418 by (cite: sakamoto13). We fix relative fluxes of the NS line components and their velocities relative to CO, but vary the overall flux normalization and line width to fit the blue nitrogen sulfide complex, and then subtract both complexes from the spectrum (see Fig. [19](#fig:ngc4418)).

Indeed much of the wing red-wards of the CO(1-0) line is contributed by nitrogen sulfide, but CO line wings out to $\gtrsim\pm$300km s$^{-1}$ remain on both the blue and red side after subtraction of that contamination. We proceed with the NS-subtracted spectrum and adopt $v_{\rm out} = 324$ km s$^{-1}$ from a 3 host + 1 outflow component multi-Gaussian fit. As geometrical size we use $R_{\rm out} = 0.23$$''$ from data that are averaging $v=[-330,-190]$ km s$^{-1}$ in the blue wing only, because the red wing is contaminated by nitrogen sulfide. (cite: fluetsch19) present CO(2-1) data for NGC 4418 with a line profile that is very similar to our NS-subtracted CO(1-0) profile (see also Fig. [2](#fig:excitation) below), but adopt a simple two Gaussian decomposition that assigns a larger fraction of the total line flux to an outflow that dominates at $|v|\gtrsim 100$ km s$^{-1}$. We maintain our more conservative decomposition but note that none of the available data exclude that such a large fraction of low velocity emission is due to slow outflow-like motion, rather than gravitationally bound motion.

**IC 860** (Fig. [20](#fig:ic860)): CO emission shows a prominent compact core with intrinsic diameter about 1.5$''$. We find no significant emission at $|v|>250$ km s$^{-1}$. The $|v|\lesssim 200$ km s$^{-1}$ line wings near the nucleus are broader than the velocity of larger scale rotation and the positions of these channels fold back to near the nucleus rather than extending the PA$\sim$20–30$^\circ$ rotation pattern. We cannot discriminate some modest outflow motion (unable to escape the galaxy) from bound motion in the near-nuclear potential. We assign a limit of 0.58 Jy km s$^{-1}$ to a fast outflow.

**IRAS 13120-5453** (Fig. [21](#fig:i13120)): This merger shows prominent CO emission (cite: sliwa17). Our data indicate a clear rotating disk extending to at least 4$''$, with projected rotation velocity $\sim$150 km s$^{-1}$. Channel maps near systemic velocity show a depression at the center of this disk. The central line profile is double-horned with peak velocities similar to the larger scale rotation, and shows additional outflow wings in the blue and red. Wings suggesting outflow are also seen in HCN(4-3) (cite: privon17) and CO(3-2) (cite: fluetsch19). Spectral decomposition using 4 host plus 2 outflow Gaussian components results in the outflow Gaussians contributing roughly half of the r$<$1$''$ CO flux (15% of the total flux), if integrating over the full profile. This type of profile decomposition is backed by the need for a strong optically thin central outflow component, in order to explain the relation of CO(3-2) and (1-0) emission in this source (see discussion in Sect. [4.1](#sect:convfact) below, including Figs. [2](#fig:excitation) and [3](#fig:r31_i13120)). We adopt $v_{\rm out} = 301$ km s$^{-1}$ from this fit to the r=1$''$ outflow spectrum and $R_{\rm out} = 0.63$$''$ from averaging the properties of the blue and red outflows at $v=[-690,-270]$ km s$^{-1}$ and $v=[270,690]$ km s$^{-1}$. The adopted $\Delta v$, $FW_{10\%}$ and $v_{\rm out}$ are the flux-weighted means of the respective values for the two broad components.

**IRAS F14378-3651** (Fig. [22](#fig:f14378)): The data show CO emission extended over a radius $\sim$2$''$, with a velocity gradient along PA$\sim$20$^\circ$. The nuclear line profile is well fitted with two Gaussians. While there may be a slight flux excess over this fit at $|v|\sim 250$ km s$^{-1}$, we do not consider this clear evidence for an outflow and assign a flux limit of 0.43 Jy km s$^{-1}$ to a faster outflow.

**IRAS F17207-0014** (Fig. [23](#fig:f17207)): The inner arc second of this merger shows a disk-like velocity gradient along PA$\sim$-50$^\circ$ but larger scales do not follow this trend. The spatial and velocity structure of CO in this merger is complex, including a tidal arm that is detected in CO out to at least 15$''$. The line profile of the galaxy is extremely broad and reaches out to $\sim\pm$500 km s$^{-1}$. Beyond that, an outflow is detected on the blue side only, out to $v\gtrsim -1000$ km s$^{-1}$. An outflow covering a similar velocity range has been reported for CO(2-1) (cite: garcia-burillo15). Our lower spatial resolution data are consistent with their PA$\sim$160$^\circ$ for the blue outflow. We adopt $v_{\rm out} = 1116$ km s$^{-1}$ from the fit to the nuclear outflow spectrum and an uncertain $R_{\rm out} = 0.45$$''$ from the properties of the blue outflow at $v=[-1000,-500]$ km s$^{-1}$.

**IRAS F20551-4250** (Fig. [24](#fig:f20551)): The velocity field of this merger is complex with a general NE/SW velocity gradient in the inner arc second. A clear red outflow is detected out to $v\sim 500$ km s$^{-1}$, spatially offset towards the opposite direction as the red ‘disk’ emission. A weaker blue counter-outflow is indicated, at $>$4$\sigma$ in the contours for the \[-510,-210\] km s$^{-1}$ range as shown in Fig. [24](#fig:f20551), but only $\sim$3$\sigma$ for ranges ending at -270 km s$^{-1}$. We base quantitative analysis on the red outflow only, but stay aware of the tentative blue outflow when comparing to other outflow indicators. We adopt $v_{\rm out} = 490$ km s$^{-1}$ from the spectral fit at the position of the red outflow, and $R_{\rm out} = 0.27$$''$.

**NGC 7479** (Fig. [25](#fig:ngc7479)): There is strong CO(1-0) emission near the center and along the bar of this galaxy. The spectrum inside r=3$''$ shows no evidence for fast outflow at $|v|>300$ km s$^{-1}$. The centroid positions of different channel maps as well as the PV-diagram indicate a pronounced bipolar CO structure at $|v|\sim 200$km s$^{-1}$, at PA$\sim$30$^\circ$. We do not ascribe this structure to outflow, but follow previous works (cite: sempere95; laine99; baker00), which on the basis of shallower data ascribed CO kinematics in the inner region of NGC 7479 to gravitationally bound gas flows within the barred potential of this galaxy. We assign a limit of 0.73 Jy km s$^{-1}$ to a fast outflow.

## Outflow data from the literature

|  |  |  |  |  |  |
|:---|---:|---:|---:|---:|:---|
| Source | J$_{\rm up}$ | $S_{\rm CO}$(wings) | $v_{\rm out}$ | $R_{\rm out}$ | Reference |
|  |  | Jy km s$^{-1}$ | km s$^{-1}$ | $''$ |  |
| NGC 253 | 1 | 707.00 | 50 | 13.35 | (cite: bolatto13) |
| I Zw 1 | 1 | $<$0.30 |  |  | (cite: cicone14) |
| PG 0157+001 | 3 | 0.86 | 402 | 0.23 | (cite: fluetsch19) |
| NGC 1068 | 3 | 98.00 | 100 | 1.50 | (cite: garcia-burillo14) |
| NGC 1266 | 1 | 26.70 | 322 | 2.75 | (cite: alatalo11) |
| IRAS F03158+4227 | 1 | 1.11 | 876 | 2.60 | (cite: gowardhan18) |
| NGC 1377 | 2 | 29.77 | 138 | 1.96 | (cite: aalto12a) |
| NGC 1433 | 3 | 16.10 | 100 | 2.00 | (cite: combes13) |
| NGC 1614 | 1 | 3.55 | 360 | 1.73 | (cite: garcia-burillo15) |
| IRAS F05081+7936 | 1 | 0.90 | 800 | 0.96 | (cite: leroy15) |
| NGC 2146 | 1 | 1450.0 | 200 | 25.00 | (cite: tsai09) |
| IRAS F08572+3915 | 1 | 2.91 | 800 | 0.73 | (cite: cicone14) |
| M 82 | 1 | 2413.33 | 100 | 53.00 | (cite: walter02) |
| IRAS F10035+4852 | 1 | $<$1.80 |  |  | (cite: leroy15) |
| NGC 3256 N | 1 | 7.65 | 700 | 2.40 | (cite: sakamoto14) |
| NGC 3256 S | 1 | 5.65 | 500 | 4.00 | (cite: sakamoto14) |
| IRAS F10565+2448 | 1 | 3.22 | 450 | 1.30 | (cite: cicone14) |
| IRAS F11119+3257 | 1 | 0.40 | 1000 | 2.22 | (cite: veilleux17) |
| NGC 3628 | 1 | 82.00 | 90 | 11.00 | (cite: tsai12) |
| ESO 320-G030 | 2 | 5.21 | 340 | 3.71 | (cite: pereira-santaella16) |
| IRAS F12112+0305 SW | 2 | 0.57 | 324 | 0.55 | (cite: pereira-santaella18) |
| IRAS F12112+0305 NE | 2 | 10.70 | 465 | 1.15 | (cite: pereira-santaella18) |
| Mrk 231 | 1 | 4.16 | 700 | 0.72 | (cite: cicone12) |
| Mrk 273 | 1 | 3.11 | 650 | 0.73 | (cite: cicone14) |
| 4C 12.50 | 1 | $<$0.18 | 640 | 0.07 | (cite: dasyra12; dasyra14) |
| SDSSJ135656.10+102609.0 | 3 | 0.99 | 500 | 0.14 | (cite: sun14) |
| IRAS F14348-1447 SW | 2 | 7.60 | 419 | 1.05 | (cite: pereira-santaella18) |
| IRAS F14348-1447 NE | 2 | 1.48 | 373 | 0.60 | (cite: pereira-santaella18) |
| Zw 049.057 | 2 | 5.00 | 300 | 0.30 | (cite: falstad18) |
| Arp 220 | 1 | 0.88 | 380 | 0.20 | (cite: barcos-munoz18) |
| Mrk 876 | 1 | 3.75 | 1050 | 1.54 | (cite: cicone14) |
| NGC 6240 | 1 | 17.80 | 450 | 1.33 | (cite: feruglio13) |
| IRAS F17020+4544 | 1 | 1.37 | 1670 | 0.86 | (cite: longinotti18) |
| IRAS F17132+5313 | 1 | $<$1.50 |  |  | (cite: leroy15) |
| PDS 456 | 3 | 1.42 | 900 | 1.00 | (cite: bischetti19) |
| NGC 6764 | 1 | 1.40 | 53 | 7.00 | (cite: leon07) |
| IRAS F20100-4156 | 1 | 1.12 | 929 | 1.00 | (cite: gowardhan18) |
| IC 5063 | 2 | 12.30 | 500 | 2.00 | (cite: dasyra16) |
| IRAS F22491-1808 | 2 | 2.00 | 325 | 0.35 | (cite: pereira-santaella18) |
| IRAS F23060+0505 | 1 | 2.26 | 700 | 1.38 | (cite: cicone14) |
| IRAS 23365+3604 | 1 | 0.86 | 450 | 1.00 | (cite: cicone14) |

Table notes: These parameters may differ from those published in the original references. They are reconstructed from the published information in order to be consistent with our adopted separation between line core and line wings, and our definitions for $v_{\rm out}$ and $R_{\rm out}$. For consistency, they are not corrected for outflow inclination, even if this is constrained in some original references. See also Sect. [3.2](#sect:literature) for details.

![](plot_excitation.pdf)

We have searched the literature for local galaxies with interferometric low-J CO outflow detections or limits, starting with the sources from Table 1 of (cite: lutz16) that we did not observe, but also including galaxies outside that parameter range. As noted in the introduction, our selection is not complete towards some of the smallest scale and least energetic outflows that were recently reported from very high resolution interferometric studies. These would escape detection with ‘outflow wing’ methods similar to ours, and be of lower impact beyond the local (nuclear) region of the host. Since different references follow a range of approaches for measuring outflow properties, we use the published results to reconstruct ‘observed’ $S_{\rm CO}$ (wings), $v_{\rm out}$, $R_{\rm out}$ that are homogenized to our adopted conventions and consider differences in adopted distance and CO conversion factor where applicable. Where full parameters of multiple Gaussian fits are reported in the literature, our approach as described in Sect. [3](#sect:outprop) can be directly followed for deriving $S_{\rm CO}$ (wings) and $v_{\rm out}$. For references that only quote outflow fluxes for a velocity range outside the host-dominated line core (cite: cicone14), we adopt those fluxes and the average velocity of the outflow bin. If only the total $S_{\rm CO}$ (gauss) for a broad Gaussian component is available, we assume $S_{\rm CO}$ (wings) to be 1/3 of $S_{\rm CO}$ (gauss), where the factor 1/3 is adopted from the typical value measured for our own data. Again, we do not attempt to correct for outflow opening angle and inclination. This provides a homogeneous sample but does not make full use of all information that is in hand for some of the best studies cases (cite: barcos-munoz18; aalto16). In a few cases we use published plotted spectra to estimate $v_{\rm out}$. For 4C 12.50 we adopt the (cite: dasyra14) limit for CO outflow in emission but we add their outflow velocity from CO(3-2) absorption and their size estimate. For the single dish outflow detection of IRAS F17020+4544 and the low resolution interferometry of IRAS 05083+7936 we adopt a fiducial 1 kpc for $R_{\rm out}$. Our adopted homogenized literature data are summarized in Table [\[tab:litobs\]](#tab:litobs).

From this point on, we treat our observational results and the adopted literature values jointly and consistently, as described in Sect. [4](#sect:derivprop), and call this the ‘combined’ sample. For literature sources observed in CO transitions other than CO(1-0), we adopt the brightness temperature ratios in Table 4 of (cite: bothwell13) for conversion to CO(1-0).

![](plot_r31_i13120.pdf)

# Outflow structure and derived properties

Deriving outflow masses $M_{\rm out}$, mass outflow rates $\dot{M}_{\rm out}$, and energy and momentum flows from the direct observed quantities (Sect. [3](#sect:outprop), Table [\[tab:outobs\]](#tab:outobs), Table [\[tab:litobs\]](#tab:litobs)) is a multi-step procedure. We describe here our assumptions, and to what extent our data constrain the uncertainties in the conversions involved.

## Outflow masses and CO conversion factor

Outflowing molecular gas may not necessarily be in self-gravitating molecular clouds for which the standard ‘Galactic’ conversion factor from CO luminosity to molecular gas mass is originally derived (cite: bolatto13a). A range of possible conversion factors have been discussed for molecular outflows, ranging from a Galactic $\alpha_{\rm CO(1-0)}$ = 4.36 M$_\odot$ / (K km s$^{-1}$ pc$^2$) to $\alpha_{\rm CO(1-0)}$ = 0.80 M$_\odot$ / (K km s$^{-1}$ pc$^2$) as often used for ULIRGs (adopted partly due to the first outflow detections being in ULIRGs), and finally yet lower values for $\alpha_{\rm CO(1-0)}$ that may arise in gas with optically thin CO emission. In that case, $\alpha_{\rm CO(1-0)}$ $\approx$ 0.34 M$_\odot$ / (K km s$^{-1}$ pc$^2$) for an excitation temperature $T_{\rm ex}=30$ K (cite: bolatto13a), and the ratio of a rotational transition i and a lower transition j (in brightness temperature units) may exceed the value $R_{\rm ij}\lesssim$1 for thermalized optically thick gas. Ratios may reach higher values up to $R_{21}\approx 2.8$ and $R_{32}\approx 1.3$, for $T_{\rm ex}=30$ K (cite: leroy15a).

Indeed, high CO line ratios and optically thin CO have been suggested for the outflow of IC 5063 (cite: dasyra16). For four sources in our sample we can compare our CO(1-0) outflow results to published spectra for higher J CO transitions, which we have re-extracted for consistent apertures (Fig. [2](#fig:excitation)). Values consistent with $R_{\rm i1}\lesssim 1$ are found for three targets: $R_{31}=1.35\pm 0.23$ for IRAS F05189-2524 (cite: fluetsch19), $R_{21}=0.66\pm 0.15$ for IRAS F17207-0014, (cite: garcia-burillo15)), and $R_{31}=1.34\pm 0.23$ for NGC 4418 (cite: fluetsch19)). We have derived these brightness temperature ratios by fitting multiple Gaussians to the higher J transition where mean velocity and width of the outflow component(s) are fixed to the CO(1-0) derived values, and only their normalization is varied. The error estimates combine statistical errors and an assumed 10% calibration uncertainty for each line. These results do not point toward the low conversion factor of the optically thin case. This is consistent with similar ratios reported for other outflows (cite: weiss05; cicone12; feruglio15; zschaechner18; cicone18), with $\alpha_{\rm CO(1-0)}$ = $2.1\pm 1.2$ M$_\odot$ / (K km s$^{-1}$ pc$^2$) suggested by (cite: cicone18) on the basis of CO and \[CI\] in the N6240 outflow, and with an attempt to constrain the outflow conversion factor for M 82, leading to $\alpha_{\rm CO(1-0)}$ 2 to 4 times below the Galactic value (cite: leroy15a).

The clear exception in our sample is IRAS 13120-5453. The CO(3-2) spectrum (cite: fluetsch19), divided by 9 to get consistent brightness temperature scale with CO(1-0), clearly has wings above the CO(1-0) spectrum (Fig. [2](#fig:excitation)). We derive $R_{31}=2.10\pm 0.29$, above the maximum of 1 that is possible for thermalized optically thick CO emission, and consistent with a large contribution of optically thin gas that may have a moderate $T_{\rm ex}\sim 30$ K. This high excitation is not only observed in the line wings. Fig. [3](#fig:r31_i13120) shows the beam-matched ratio map of CO(3-2) and CO(1-0) flux (in brightness temperature units $R_{\rm ij}$), integrated over the line core within $\pm$200 km s$^{-1}$. Values corresponding to $R_{31}\sim 0.6$ are observed in the disk, but $R_{31}>1$ is found in the nuclear region. Combined with the general CO morphology of the source (see moment 0 map and PV diagrams in Fig. [21](#fig:i13120)), the source is best described as combination of a rotating disk with normal ‘molecular cloud’ CO properties and radius at least 4$''$, and a largely optically thin CO outflow that is dominating the nuclear region over the full line width.

Three of the four targets studied here and the vast majority of literature results are consistent with optically thick CO emission in the outflows. But the clear detection of a high ratio (optically thin CO) for IRAS 13120-5453 is a strong warning that this is not true for all outflows, and that associated uncertainties on conversion factor and on outflow masses cannot be fully removed with the present data. Below, we follow much of the local universe molecular outflow literature and adopt $\alpha_{\rm CO(1-0)}$ = 0.8 M$_\odot$ / (K km s$^{-1}$ pc$^2$) but note that our CO data alone do not determine a preference for this ‘ULIRG’ value compared to a Galactic one. For a Galactic $\alpha_{\rm CO(1-0)}$ = 4.36 M$_\odot$ / (K km s$^{-1}$ pc$^2$), recently found to be consistent also with ULIRG gas/dust comparisons (cite: tacconi18), derived outflow masses and rates would increase more than five-fold. It is also important to recall that outflows may be complex and multi-phase. For detection and current constraints from high density tracers in the Mrk 231 and NGC 253 outflows, see (cite: aalto12; aalto15; walter17).

In the absence of a reliable source-specific conversion factor, we also apply $\alpha_{\rm CO(1-0)}$ = 0.8 M$_\odot$ / (K km s$^{-1}$ pc$^2$) to IRAS 13120-5453, noting that the associated overestimate of outflow mass for the gas that is optically thin in CO and the underestimate due to including only line wings may partly compensate. Concerning the full sample, the good agreement that we report below with OH-based outflow masses (Sect. [5.1](#sect:ohcomp)) is sensitive to our adopted CO conversion factor.

## Outflow rates

![image](flowhistory_c1.pdf) ![image](radialprofile_c1.pdf) ![image](demo_c1.pdf) ![image](myeqn_c1.pdf) ![image](flowhistory_c3.pdf) ![image](radialprofile_c3.pdf) ![image](demo_c3.pdf) ![image](myeqn_c3.pdf) ![image](flowhistory_shell.pdf) ![image](radialprofile_shell.pdf) ![image](demo_shell.pdf) ![image](myeqn_shell.pdf)

Given an observed outflow mass $M_{\rm out}$, radius $R_{\rm out}$ and velocity $v_{\rm out}$, mass outflow rates are commonly derived by assuming a spherical or (multi-)cone geometry with constant velocity within that volume, that is with the simplifying assumption of no temporal or spatial acceleration or deceleration of the flow. This is a nontrivial assumption given that a multitude of mechanisms such as ballistic deceleration in the galaxy’s potential, acceleration by radiation pressure, or interaction with an entraining non-molecular wind can all affect velocities, but it is appropriate for interpretation of the current body of observations which is typically not highly resolved. The outflow rate is then derived via

$$\begin{equation}
\dot{M}_{\rm out} = C  \frac{M_{\rm out} v_{\rm out}}{R_{\rm out}}
\label{eq:mdot}
\end{equation}$$

The value of C depends on the adopted outflow history (see also illustration in Fig. [4](#fig:schemastruc)). Assuming that the outflow has started at a point in the past at $-t_{\rm flow} = -R_{\rm out}/v_{\rm out}$ and has continued with a constant mass outflow rate until now directly leads to C=1. This is what we adopt, and agrees with the ‘time averaged thin shell’ approach often used to derive outflow rates from absorption line data (cite: rupke05b; gonzalez-alfonso17). In this case, the average volume density of the outflowing gas decreases outwards $\rho\propto R^{-2}$ but local cloud or filament densities may not follow this drop.

Several recent works have derived molecular outflow rates assuming C=3 (cite: cicone14; fiore17). This is obtained when one assumes that the outflowing gas fills the spherical or (multi-)cone volume with constant average volume density. This corresponds to a mass outflow rate that starts with its maximum in the past at -$t_{\rm flow}$, when the material was emitted that is now reaching $R_{\rm out}$, and for which $\dot{M}_{\rm out}$ is quoted. After the start at -$t_{\rm flow}$ the mass outflow rate drops in time $\propto (t/t_{\rm flow})^2$, reaching zero now.

Adopting a fixed CO conversion factor means CO light traces molecular gas mass. This is plausible if the outflow is seen as an ensemble of flowing clouds or filaments with conversion factor reflecting local cloud conditions rather than the larger scale average density of the flow. This is an important assumption for both cases, but in particular for the first case (C=1) with average density decreasing outwards.

Both scenarios are strongly simplified, but for resolved outflows that are strongly inclined with respect to the line of sight and have moderate opening angle, the radial profiles can provide insights into the outflow history. Fig. [4](#fig:schemastruc) schematically shows outflow history, radial profile of the average density, and projected surface brightness, for these two scenarios and for a thin shell case. Most CO outflows in our sample and in the current literature are barely spatially resolved, preventing any related conclusions. An exception is III Zw 035 (Fig. [13](#fig:iiizw035)). Its data suggest an inclined outflow of modest opening angle, lacking the brightening at large radius that is expected for the constant volume density or thin shell cases (Fig. [4](#fig:schemastruc)). Similar arguments can be made for the strongly inclined outflows of M 82 (cite: walter02; leroy15a), NGC 253 (cite: bolatto13) and NGC 3256S (cite: sakamoto14). For ESO 320-G030 substructure is observed, but again no brightening at large radii (cite: pereira-santaella16).

We hence proceed computing outflow rates with C=1 in Eqn. [\[eq:mdot\]](#eq:mdot).

# Widespread molecular outflows

## Consistency of *Herschel* OH-based and interferometric CO outflow detections

Samples of dozens of galaxies each have now been studied using the two complementary techniques for detecting molecular outflows in local galaxies: P-Cygni profiles of far-infrared OH lines, enabled by the *Herschel* mission, and CO line wings, enabled by wide-band receivers at mm interferometers. Comparing results from these two approaches is mandated in the first place by their basic difference. OH absorption probes columns along the lines of sight towards the far-infrared emitting region, inducing a need for model derivations of covering factor and radial location, under the assumption of overall spherical symmetry. CO emission traces all emitting gas, but only to the extent it can be kinematically and/or spatially separated from the host CO emission. Both methods invoke conversions from observables to total outflowing molecular gas mass that include explicit conversion factors – OH abundance and $\alpha_{\rm CO(1-0)}$, respectively. We compare the two approaches in two ways. First, we use our combined CO sample and a large set of OH data from the literature (cite: veilleux13; spoon13; falstad15; stone16) to check for consistency of detections and of the measured outflow velocities. Second, we compare the outflow properties that (cite: gonzalez-alfonso17) derive for a dozen well-characterized OH outflow sources with CO results – interferometric data are available for their entire sample from our observations and from the literature.

![](co_oh.pdf)

Figure [5](#fig:co_oh) compares CO- and OH-derived outflow velocities. $v_{\rm out}$(CO) is derived as described is Sect. [4](#sect:derivprop). Our $v_{\rm out}$(CO) (not corrected for outflow inclination) are compared with the OH absorption in the line of sight. For OH, several different conventions are in use. We adopt $v_{84}{\rm (abs)}$ as defined by (cite: veilleux13), since it is more robust at limited S/N than the alternative $v_{\rm max}$, and better matched to our $v_{\rm out}$ convention for CO which samples the outflow wings but not the maximum detected velocity. In one case where the original OH reference quotes only $v_{\rm max}$ (cite: spoon13), we estimate $v_{84}{\rm (abs)}$$\sim$800 km s$^{-1}$ from their Fig. 10.

The agreement between the two approaches is good: Of 26 sources with data from both methods, 21 show both CO outflow and absorption dominated or P-Cygni OH spectra with available $v_{84}{\rm (abs)}$. CO- and OH-based velocities are in broad agreement, but there is considerable $\sim$0.36 dex scatter around the 1:1 line. Correlations of outflow velocities with galaxy properties will be subject to related scatter, likely for either of the two methods in use.

Some insights can be gained also from the few galaxies for which CO and OH disagree in reported outflows. NGC 7479 shows a clear fast OH outflow with $v_{84}{\rm (abs)}$$\sim$-650 km s$^{-1}$ (cite: stone16) but no detectable CO outflow at such velocities (Fig. [25](#fig:ngc7479)). The line of sight sampling the OH outflow against the FIR continuum must have conditions that cannot be extrapolated to a larger scale and large covering factor outflow. Conversely, NGC 1068 exhibits no OH outflow (cite: stone16) but molecular outflows have been suggested in CO studies. This discrepancy may be due to its moderate velocity CO outflow occurring mostly in the disk plane (cite: garcia-burillo14), and not affecting our line of sight. The faster outflow reported by (cite: gallimore16) might be closer to the line of sight, but restricted to a much smaller volume and covering only a small fraction of the far-infrared continuum. For NGC 4418, (cite: gonzalez-alfonso12) and (cite: veilleux13) report OH absorption but the absorption is slightly redshifted, suggesting molecular gas in slow $\approx 100$ km s$^{-1}$ inflow. Inflow is also suggested for atomic gas by an inverse P-Cygni profile in \[Oi\] 63 $\mu$m (cite: gonzalez-alfonso12). Any CO emission from this slow inflow component would be hard to separate from the line core in Fig. [19](#fig:ngc4418). Finally, the modest OH outflow velocity for IRAS F17207-0014 clearly differs from the fast (but low flux density) outflow seen both in CO(1-0) (this paper) and CO(2-1) (cite: garcia-burillo15), indicating that the OH column at these fast velocities must be low towards our line of sight.

As in the explanation of these mismatches in OH and CO outflow detection, we believe that for the comparison of OH and CO velocities of the outflows in Fig. [5](#fig:co_oh) that are detected in both tracers, systematic factors and geometry are main contributors to the scatter. Similar arguments apply to the comparisons of outflow masses, velocities, and rates below in Fig. [6](#fig:ga17). Concerning CO outflow velocities, the nominal errors of typically $\lesssim 10$% for the fitted width of the broad CO outflow component do not consider the effects of possibly non-Gaussian true profiles, nor the impact of varying flux and width of host CO emission on the splitting off of the outflow wings that are adopted in our analysis (Fig. [1](#fig:outflowgauss_visu)). Concerning the OH $v_{84}{\rm (abs)}$, (cite: veilleux13) estimate a typical uncertainty of 50 km s$^{-1}$ that is dominated by continuum placement uncertainties. Both estimates do not consider the different response of the CO emission and OH absorption methods to variations in alignment of complex outflow geometries with respect to the line of sight, among other systematics such as the properties of the background FIR source against which OH is observed.

For the vast $\approx$80% majority of the objects with both OH and CO diagnostics in hand, both OH absorption and CO outflow are detected, with plausible mainly geometrical explanations for the remaining mismatches. For a sample of obscured nuclei characterized by HCN mm emission from vibrationally excited levels, (cite: falstad19) discuss in more detail geometrical and evolutionary factors that might lead to absence of far-infrared OH outflow signatures. The different sampling of the outflow geometry by emission and by absorption, as well as the modest S/N of many detections certainly also contribute to the scatter around the 1:1 line in the velocity comparison of Fig. [5](#fig:co_oh). This good agreement would be too optimistic if dominated by CO followup of OH outflows, with preferential reporting of detections in the literature. But CO detections/limits for our high FIR surface brightness sample, and the analysis of the (cite: gonzalez-alfonso17) sample in the next paragraph argue that such effects are not dominant.

![image](ga17_mout.pdf) ![image](ga17_vout.pdf) ![image](ga17_rout.pdf) ![image](ga17_mdot.pdf) ![image](ga17_pdot.pdf) ![image](ga17_edot.pdf)

A deeper comparison of CO-based outflow masses, rates, and energetics is possible for the 12 ULIRGs for which (cite: gonzalez-alfonso17) were able to derive reliable spherically symmetric outflow models that are constrained by both ground state and excited level transitions of OH, observed with *Herschel*-PACS. All twelve sources are part of our combined CO sample. Fig. [6](#fig:ga17) compares basic outflow mass, radius, and velocity as well as derived mass, momentum, and energy outflow rates. The OH models include up to three components per source, we follow (cite: gonzalez-alfonso17) in comparing CO data only to fast $v\geq 200$ km s$^{-1}$ OH components, since the CO equivalent of the slower OH components will be blended with the host line core. Masses are the sum of values for individual high velocity OH components ($v\geq 200$ km s$^{-1}$), while radii and velocities are averages. Concerning outflow history, the assumptions of (cite: gonzalez-alfonso17) agree with our use of C=1 in Eqn. [\[eq:mdot\]](#eq:mdot). For IRAS F14348-1447, (cite: pereira-santaella18) report two distinct CO outflows from the two nuclei while the *Herschel* beam includes both. We use the dominant southwest CO outflow for comparison to OH.

Of the 12 ULIRGs, only IRAS F14378-3651 lacks a CO outflow detection and our assigned upper limit for CO-based outflow mass is within a factor 2 of the OH result. In fact, Fig. [22](#fig:f14378) indicates some excess at $v\sim$250 km s$^{-1}$ above the fit with two Gaussians, but we have conservatively opted in Sect. [3](#sect:outprop) to not assign this excess at modest velocity to an outflow. Also, any weak CO flux excess at the velocities -500 to -1000 km s$^{-1}$ which are reached by the OH outflow is not significant. For the remaining 11 ULIRGs, outflow masses agree very well (top left of Fig. [6](#fig:ga17)), with mean log$(M_{\rm out,OH}/M_{\rm out,CO})= 0.06$ dex and dispersion 0.29 dex. This agreement is noteworthy given the independent derivation of these masses, including in particular the conversion factor $\alpha_{\rm CO} = 0.8$ M$_\odot$ / (K km s$^{-1}$ pc$^2$) on the CO side, and an interstellar medium OH abundance $X_{\rm OH} = 2.5 \times 10^{-6}$ on the OH side. A consistent lower limit on $X_{\rm OH}$ has been obtained by (cite: stone18). The good agreement can be regarded as support of the adopted $\alpha_{\rm CO(1-0)}$, but see also the discussion below in the context of outflow sizes.

Outflow velocities are in excellent agreement for these bright and well-studied galaxies (top center), with mean log$(v_{\rm out,OH}/v_{\rm out,CO})= -0.03$ dex and dispersion 0.08 dex.

Larger but still modest differences are found for the outflow radii. Outflow radii from the OH models are around 0.3 kpc for all ULIRGs, while the CO observations vary more widely and detect radii up to several kpc. In the mean, log$(R_{\rm out,OH}/R_{\rm out,CO})= -0.54$ dex with dispersion 0.39 dex. Similar $\approx$0.5 dex differences are found for the outflow rates for mass, momentum, and mechanical energy (bottom panels of Fig. [6](#fig:ga17)). While the OH radii are based on spherically symmetric models and the CO radii measured, it is improbable to ascribe all differences to modeling uncertainties. This is in particular the case given the observed OH absorptions in the 84 $\mu$m and/or 65 $\mu$m transitions that are radiatively excited by intense FIR radiation fields close to an optically thick and necessarily small FIR source (cite: gonzalez-alfonso17). Breakup into several individually optically thick sources could enlarge the sizes but is not supported by the usually compact structure of high resolution (sub)mm images (cite: barcos-munoz17).

Assuming that much of the size difference between OH and CO outflow (top right of Fig. [6](#fig:ga17)) is real, one is led to a scenario where a more compact and embedded molecular outflow region traced by the OH absorptions connects to a larger and older component that can still be traced by the collisionally excited CO emission. In contrast, the covering by clumps absorbing OH will decrease with outward motion. In that case, the good agreement of outflow masses (top left of Fig. [6](#fig:ga17)) will be partly fortuitous or erroneous since the two molecules trace different though overlapping regions. A further factor in this comparison arises from the definition of outflow masses. OH-based outflow masses from (cite: gonzalez-alfonso17) reflect all directions of a spherically symmetric outflow. Emission line components of such a flow that are moving close to the plane of sky blend with the bright core of the line and are excluded by our definition of $S_{\rm CO}$ (wings), see also Fig. [1](#fig:outflowgauss_visu). Toy model calculations for a spherically symmetric case suggest $S_{\rm CO}$ (wings) would measure a mass 2–3 times smaller than the 4$\pi$ outflow, but this correction is obviously dependent on outflow velocity, width of the line core, and may be an upper limit if replacing the spherically symmetric flow with a wide angle flow with large line of sight component.

A non-unique scenario that further reduces the small tensions in Fig. [6](#fig:ga17) between OH- and CO-based results can be described as follows: (i) An outflow that is constant in rate and velocity over the flow time derived from CO data is sampled in its entirety by CO emission, and in its inner half or somewhat less by the OH absorptions. The molecular outflow masses traced by CO and by OH should reflect the different fractions of the flow that are sampled – the CO-based molecular outflow mass should be larger than the OH-based one. (ii) The similar actually derived outflow masses (Fig. [6](#fig:ga17)) then must be due to an additional correction. Depending on actual outflow geometry, this could be achieved by considering the fraction of an about spherically symmetric CO outflow that is missed by the emission line wings (see above). Alternatively, increased $\alpha_{\rm CO(1-0)}$ or increased OH abundance (decreased molecular hydrogen mass traced by OH) could help achieving an appropriate ratio of masses traced by CO and by OH. (iii) Either of the corrections described in (ii) would also bring the outflow rates in the bottom panels of Fig. [6](#fig:ga17) closer to agreement, consistent with the assumed constant outflow rate.

In summary, the comparisons provide a very successful cross-validation of the OH P-Cygni and CO interferometric methods of characterizing molecular outflows. There is no indication for a need to modify the methods and conversions adopted for CO outflows in Sect. [3](#sect:outprop) and [4](#sect:derivprop), nor for modifying the OH modeling methods of (cite: gonzalez-alfonso17). At least for ULIRG-like systems which constitute the bulk of current outflow samples and definitely of the comparisons above, the comparison also backs the large molecular outflow covering factor reported in OH outflow studies. This finding is originally based on the high incidence of P-Cygni absorptions in ULIRGs (cite: sturm11; veilleux13), and is supported by the model results of (cite: gonzalez-alfonso17). Current knowledge of outflow geometries and histories for large samples is however insufficient to clarify whether remaining modest differences between OH- and CO-based results can find a purely geometrical explanation. Use of the time-efficient OH spectroscopy for high-z outflow searches is encouraged, be it with ALMA (cite: spilker18; herrera-camus19b) or with planned future far-infrared/submm space facilities (cite: roelfsema18).

## Relation of outflow properties to FIR surface brightness, AGN luminosity, and bolometric luminosity

Several recent papers have studied scaling relations of molecular outflow masses, mass outflow rates, momentum flows and energy flows with star formation rate, AGN luminosity and bolometric luminosity of the hosting galaxies (cite: cicone14; fiore17; gonzalez-alfonso17; fluetsch19), and to what extent the flows may be momentum or energy driven. We here focus on the additional comparison with far-infrared surface brightness, and briefly revisit the relations to AGN and bolometric luminosity. Table [\[tab:multi\]](#tab:multi) summarizes these and related properties for the combined sample. As far as other quantities are concerned, our sample concurs with observational results from these references with modest modifications due to different assumptions (e.g. C = 1 or 3 in Eqn. [\[eq:mdot\]](#eq:mdot), outflow line fluxes corresponding only to wings or to entire broad components). One should note that all these studies have overlapping samples, since they are enlarging their original samples from the literature (Sect. [3.2](#sect:literature) for this paper), or are entirely literature based.

![image](vout_sigfir.pdf) ![image](mmolout_sigfir.pdf) ![image](mmoldot_sigfir.pdf) ![image](outgalratio_sigfir.pdf)

Fig. [7](#fig:sigfir) shows outflow velocity, outflow molecular mass, mass outflow rate, and the ratio of outflow and host molecular gas mass as a function of far-infrared surface brightness for 39 sources in our combined sample, which have measurements or limits for far-infrared surface brightness (cite: lutz16; lutz18). None of these quantities shows a significant trend with far-infrared surface brightness, but see the note below on selection effects at low surface brightness. If we first focus on the high surface brightness end with log($\Sigma_{\rm FIR}$)$\gtrsim$11.75 L$_\odot$ kpc$^{-2}$, we indeed find the expected very high incidence of molecular outflows that motivated our observations. Of the 18 sources with log($\Sigma_{\rm FIR}$)$\geq$11.75 L$_\odot$ kpc$^{-2}$ and/or close to optically thick FIR emission that are listed in Table 1 of (cite: lutz16), all but ESO 173-G015 have deep CO observations probing for outflows, from our own data or from the literature in the combined sample. Of these 17 objects, CO outflows have been detected in 13 sources while upper limits have been derived for IRAS F10173, IC 860, IRAS F14378 and NGC 7479. In several cases, these limits are conservative and a contribution of an outflow to the observed moderate velocity line wings remains a possibility. As expected, high far-infrared surface brightness galaxies are excellent hunting grounds for molecular outflows. This is reflected in the high detection rate, at least 13/18 sources. On the other hand, the cases with sensitive upper limits demonstrate that far-infrared surface brightness alone is not sufficient to produce strong and fast outflows in *all* cases, despite strongly exceeding SFR thresholds above which outflows from galaxy disks are prevalent (cite: heckman02; newman12; davies19).

Given its selection above an already high surface brightness threshold and the modest sample size, it is not surprising that no trends of outflow properties with surface brightness are detected within this high surface brightness sample. More noteworthy is the absence of trends in Fig. [7](#fig:sigfir) over the full range of the combined sample, which extends to more than an order of magnitude lower surface brightness. A high incidence of molecular outflows is found also among the low surface brightness members of this sample. Severe and poorly known selection effects may, however, be at work here. Much of the molecular outflow literature is in papers studying single or very few sources, and selection criteria are diverse. Upper limits may often remain unpublished. We certainly cannot exclude abundant existence of low surface brightness galaxies that have only weak or no molecular outflows. An obvious speculation is that the molecular outflow detection rate is smaller in this regime than for the high surface brightness sample. But unbiased studies of larger samples are needed to establish such a difference, or detect any trends in outflow properties over a large range of FIR surface brightness.

![image](vout_lagn.pdf) ![image](mmolout_lagn.pdf) ![image](mmoldot_lagn.pdf) ![image](outgalratio_lagn.pdf)

![image](vout_lbol.pdf) ![image](mmolout_lbol.pdf) ![image](mmoldot_lbol.pdf) ![image](outgalratio_lbol.pdf)

![image](energy_lagn.pdf) ![image](energy_lbol.pdf)

![image](momentum_lagn.pdf) ![image](momentum_lbol.pdf)

Fig. [8](#fig:lagn) and Fig. [9](#fig:lbol) show the same outflow quantities for the combined sample, now in relation to AGN luminosity and to bolometric luminosity, as also listed in Table [\[tab:multi\]](#tab:multi). Consistent with previous results that are based on samples that are partly overlapping with our combined sample (cite: sturm11; veilleux13; spoon13; cicone14; fiore17; gonzalez-alfonso17; fluetsch19), we find higher outflow velocities, outflow masses, and outflow rates for sources that host luminous AGN. But clearly to be noted in our larger sample (Fig. [8](#fig:lagn)) is the presence of some quite important outflows also in sources with low values or upper limits for L$_{\rm AGN}$ (e.g. III Zw 035), that were not included in early work. There is no obvious link of outflow properties to $L_{\rm AGN}$ at low $L_{\rm AGN}$$\lesssim$$10^{10}$ L$_\odot$, the observed trends are driven by the high $L_{\rm AGN}$ sources only. Such increased scatter in the relation to AGN luminosity was also noted by (cite: fluetsch19). A further contribution to variation in outflow properties for given $L_{\rm AGN}$ will arise from different geometries affecting the coupling of AGN wind to the larger scale interstellar medium. In combination, these findings suggest an important though not exclusive role of driving that is linked to present AGN activity.

In fact, quite clear relations of molecular outflow mass and mass outflow rate with bolometric luminosity are observed (Fig. [9](#fig:lbol)), which we quantify as:

$$\begin{multline}
{\rm log} (M_{\rm out} / {\rm M_\odot}) = \\ (7.76\pm 0.09) + (0.78\pm 0.12)\times ({\rm log}(L_{\rm Bol} / {\rm erg\ s^{-1}})
-45.5).
\label{eq:moutlbol}
\end{multline}$$

$$\begin{multline}
{\rm log} (\dot{M}_{\rm out} / {\rm M_\odot\ yr^{-1}}) = \\ (1.64\pm 0.09) + (0.75\pm 0.10)\times ({\rm log}(L_{\rm Bol} / {\rm erg\ s^{-1}})
-45.5).
\label{eq:mdotlbol}
\end{multline}$$

Here we have used linmix_err (cite: kelly07) and adopted errors of 0.15 dex for the bolometric luminosities and 0.3 dex for the outflow quantities. 0.15 dex is conservatively larger than uncertainties in measured $L_{\rm IR}$ or optical AGN continuum, in order to consider also uncertainties in the extrapolation from these to bolometric luminosity, and possible AGN variability. The fit for outflow mass is derived including both detections and upper limits, while the fit for mass outflow rates includes only the outflow detections since $R_{\rm out}$ and $v_{\rm out}$ are needed to derive outflow rate or limit. We have verified that adopting fiducial $R_{\rm out}$ = 0.7 kpc and $v_{\rm out}$ = 450 km/s to tentatively include the limits on outflow mass also for outflow rate leaves the slope of Eqn. [\[eq:mdotlbol\]](#eq:mdotlbol) effectively unchanged, and reduces the normalization by $\sim$0.1 dex. While these relations can be helpful in assessing the likely importance of a molecular outflow from a given object, or for estimating total outflow rates for ensembles, we caution again about possible selection effects in the combined sample that is significantly literature based. In addition, bolometric luminosity, AGN luminosity, and SFR are all correlated for this sample, causing a link of outflow properties to all three, including the SFR that we do not discuss in detail here.

There are two obvious ways to reconcile the preference of strong molecular outflows for AGN hosts with the detection of outflows also in galaxies that are lacking an AGN, and with the increased scatter at low $L_{\rm AGN}$ in Fig. [8](#fig:lagn). First, intense star formation is a significant contributor to driving molecular outflows, which becomes dominant in the absence of a powerful AGN. Second, AGN driven outflows may not be recognized as such because they persist for some time even if rapid accretion rate variations lower the AGN luminosity. A third possibility is driving by highly obscured AGN activity, but we note that for many cases the AGN luminosities in Table [\[tab:multi\]](#tab:multi) use infrared spectroscopy which is sensitive to AGN heated dust even for obscured cases. We believe that both star formation driving and intermittent AGN activity are at work here, and address the second option in some more detail in Sect. [5.3](#sect:intermittent). But first we discuss constraints from kinetic power and momentum rate balance.

Figure [10](#fig:energy) compares the outflow kinetic power $P_{\rm kin} = 0.5 \dot{M}_{\rm out} v_{\rm out}^2$ with AGN luminosity and bolometric luminosity. Most AGN hosts stay below a wind kinetic power of 5% of the AGN luminosity, which is often considered the limit for coupling AGN radiative power into outflows via ‘energy-conserving’ winds (cite: king15). Three AGN hosts (NGC 1266, Mrk 876, IRAS F17020+4544) hover around or slightly above that line, still consistent with plausible uncertainties of wind parameters or with modest AGN variability. Notable is that limits on AGN luminosity place many of the sources with non-detected AGN well above that line. Also, their outflow momentum rate would sometimes require ‘momentum boosts’ far above the maximum AGN radiative momentum that corresponds to the limit on $L_{\rm AGN}$. This boost reaches up to more than a factor 100 (Fig. [11](#fig:momentum)), beyond plausibility even for energy conserving flows (cite: faucher-giguere12; zubovas12). These two findings quantify that some of the observed molecular outflows cannot be driven by the currently observed level of AGN activity.

The right panels of Figs. [10](#fig:energy) and [11](#fig:momentum) compare outflow power and momentum rate to bolometric luminosity and associated momentum rate, which for the non-AGN systems are both dominated by star formation. Comparing outflow kinetic power to the total mechanical luminosity delivered by supernovae $P_{\rm kin,SN} = 7\times 10^{41}$ ($SFR/{\rm M}_\odot$ yr$^{-1})$ erg s$^{-1}$ (cite: veilleux05), a quite high conversion efficiency $\gtrsim$10% would be needed in some cases. Similarly, the momentum rate of some of the stronger outflows from non-AGN hosts exceeds the radiative momentum rate. While this is in principle possible via multiple scattering in heavily obscured regions (cite: murray05), we consider it more likely that we are facing a mix of driving by star formation and by past AGN activity.

Given the quite clear relations of outflow kinetic power and momentum rate with bolometric luminosity, we quote fitting relations, again with a caveat about possible selection effects from the literature selection:

$$\begin{multline}
{\rm log} (P_{\rm kin} / {\rm erg\ s^{-1}}) = \\ (42.39\pm 0.14) + (1.34\pm 0.17)\times ({\rm log}(L_{\rm Bol} / {\rm erg\ s^{-1}})
-45.5).
\label{eq:pkinlbol}
\end{multline}$$

$$\begin{multline}
{\rm log} (\dot{M}_{\rm out}v / {\rm g\ cm\ s^{-2}}) = \\ (35.07\pm 0.11) + (1.04\pm 0.13)\times ({\rm log}(L_{\rm Bol} / {\rm erg\ s^{-1}})
-45.5).
\label{eq:mrlbol}
\end{multline}$$

## Evidence for a role of intermittent AGN-driving

We next present arguments that the contribution of AGN to the driving of outflows must have a short timescale and intermittent component, in order to match the observed outflow properties.

![](flowtimehisto.pdf)

Figure [12](#fig:flowtime) shows that typical flow times $t_{\rm flow}=R_{\rm out}/v_{\rm out}$ for the combined sample are short, just above a million years (median 1.5 Myr). For an outflow which is so massive that it needs to be driven not only by single young cluster or star formation region, but rather by a large part of a galaxy’s total (SFR+AGN) energetics and/or momentum, such a short timescale is difficult to achieve with star formation events. Given the star formation history and the smoothing effect of massive star lifetimes, star formation events would naturally lead to a $\gtrsim 10^7$ yr timescale, even in merger-induced starbursts with peaked star formation histories (cite: mihos96; hopkins08; hopkins13; hayward14). In a suite of 112 hydrodynamic major merger simulations from (cite: cox06) and (cite: wuyts10), the star formation rate stays above half of its peak value for a median duration of $\sim$70 Myr, with a minimum of 5 Myr and only three cases with duration below 10 Myr. Short $\sim$Myr outflow events in massive galaxies hence are much easier explained by the highly and rapidly variable accretion onto an AGN, even if considering that observed outflows may average to some extent over rapid repetitive AGN ‘flickering’ (cite: zubovas16).

This argument assumes that the $R_{\rm out}$, $v_{\rm out}$ values obtained from CO interferometry and used to derive the flow time are representative for the full duration of the outflow event, having constant velocity and starting at the center of the galaxy. This assumption would be wrong if molecular gas from earlier phases of this outflow event would remain undetected due to observational limitations, or due to being converted to atomic or ionized gas phases. What might happen to such molecular gas? If just hiding at low surface density and CO surface brightness, observations with too small beams might miss an important fraction of the outflow. While such effects surely exist, we infer from the lack of a trend in the inset of Fig. [12](#fig:flowtime) that beam size effects are not dominating the observed flow time distribution. Also, accumulated fast molecular gas from long outflow episodes has not been reported in large aperture single dish data that are sensitive to low surface brightness CO.

In a situation where a large fraction of the outflowing gas will not finally escape the halo (cite: fluetsch19), flow times as derived here are also limited by deceleration. Such effects will however work on $\gtrsim$10$^7$ yr timescales related to the dynamical timescale, longer than the short typical $t_{\rm flow}$ observed here.

Several studies have compared molecular outflows to outflows in the atomic phase and the ionized $\sim 10^4$ K phase and concluded that, while the mass in those phases may sometimes approach the outflowing molecular mass, it does not exceed it by large factors (cite: contursi13; rupke13; leroy15a; janssen16; rupke17; fiore17; fluetsch19). Specifically for M 82, (cite: leroy15a) suggest a molecular fraction in the outflow that is decreasing with radius, and falling below half at $\sim$1 kpc, but with overall similar molecular and atomic outflowing mass. Less observationally constrained is a path to very hot $\gtrsim 10^7$ K dilute gas that is not easily detected in common X-ray data (cite: strickland09). However, only for the fastest observed molecular outflows could the post-shock temperature $T=\frac{3}{16} \frac{\mu v_s^2}{k}$ reach beyond $10^7$ K, and potentially high local densities may favor re-cooling. Finally, some outflowing molecular gas could be converted to stars (cite: zubovas14; elbadry16; wang18), but observational confirmation is still scarce (cite: maiolino17; gallagher19; rodriguezdelpino19), not yet having reached unambiguous detection of young stars that are both moving at the outflow speed and trapping a significant fraction of the outflow rate. Very large masses of young stars above the molecular outflow mass would build up, and should be little obscured, since the outflows typically extend beyond the dusty galaxy centers. In summary, there seems to be no obvious storage of molecular outflow in other phases that would help to drastically shorten the observed molecular gas flow times.

A second argument for time-dependent AGN driving rests on the energy and momentum budget. For about 10% of their sample, (cite: fluetsch19) argue that outflow kinetic power and momentum cannot be driven by the combination of the currently available AGN luminosity and SFR – a past episode of higher AGN luminosity must have been present.

Finally and most directly, in a few spatially well resolved cases distinct outflow episodes can be inferred from the morphology. NGC 2623 shows both a clear bipolar outflow with the blue lobe north of the nucleus, and a second ‘fossil’ blue component at larger offset to the southeast. (see Sect. [3](#sect:outprop), Fig. [15](#fig:ngc2623)). Flow times for these two differ by more than an order of magnitude: 1 Myr vs. 13 Myr. Rapidly evolving near-nuclear conditions of this advanced merger or driving by different nuclei (cite: rossa07) might be responsible for the different orientation of these two flows. For IRAS 08572+3915, deep IRAM-NOEMA data detect a second spatially separated outflow cloud that is offset by $\sim$6 kpc (cite: janssen16b; herrera-camus19a) in addition to the previously known outflow (cite: cicone14). On a smaller scale, spatially resolved ALMA data of ESO 302-G030 (cite: pereira-santaella16) show several clumps over a total scale of $\sim$0.8 kpc, with a rather well defined blue/red symmetry. Driving by individual supernovae may be just energetically possible in this case, but intermittent AGN emission appears equally plausible.

Accretion rate variations on many timescales are a characteristic of the AGN phenomenon. Beyond the timescales of direct flux monitoring programs or archival light curve studies, their imprint on local AGN phenomena has been demonstrated in various ways. Light echoes of past activity can be seen in the form of (extended) narrow line regions that are too powerful for the currently observed AGN luminosity (e.g., (cite: lintott09; keel12; schirmer13); see also (cite: sartori18)). Conversely, AGN with deficient NLR compared to their X-ray luminosity may trace the onset of activity (cite: schawinski15). Perhaps most directly, X-ray light echoes trace accretion variations of the (much less luminous) activity in our Galactic Center (cite: clavel13). Recent simulations start to reproduce the observed ‘flickering’ AGN accretion variations (cite: novak11; gabor13). At high redshift, the smoothing of accretion rate variations provided by the observed outflow can explain the higher incidence of AGN-driven nuclear outflows, compared to direct AGN indicators such as X-rays (cite: genzel14; foersterschreiber19).

Molecular outflow statistics in a complete mass selected sample could provide further insights into the timescales of AGN driving. Limitations arise from the additional role of star formation driven outflows that can be hard to discern from fossil AGN-driven outflows, and from the diverse target selection of outflow studies in the current literature. Tentatively, both the identification of multiple episodes in a few targets and the large 13/17 outflow incidence for the (cite: lutz16) high surface brightness sample argue that the $\sim$1 Myr outflow events may be episodes in a longer outflow history. However, the latter sample is a special population that favors a compact dense circumnuclear ISM, and the low incidence of OH outflows in the Seyfert sample of (cite: stone16) clearly shows that its statistics cannot be transferred to AGN in general. In any case, ‘depletion times’ needed to expel a galaxy’s entire molecular gas mass have to be viewed with great caution, if ones assumes that the current outflow rate persists unchanged over a very long time.

# Conclusions

We have presented new CO(1-0) interferometry from ALMA and NOEMA, probing molecular outflows in 13 local galaxies with high far-infrared surface brightness, and combined our results with literature data on local universe molecular outflows. Our main findings are:

\(1\) Galaxies with high far-infrared surface brightness log($\Sigma_{\rm FIR}$)$\gtrsim$11.75 L$_\odot$ kpc$^{-2}$ show the expected high incidence of molecular outflows. 17 of 18 sources in the (cite: lutz16) sample now have suitable CO data, and 13 of these exhibit molecular outflows. Several of these nearby targets, in particular III Zw 035, are well-suited to spatially resolved studies.

\(2\) Partly constrained by observed line ratios and by spatial structure of the best cases, we adopt in the conversion of CO observables to outflow physical properties $\alpha_{\rm CO(1-0)}$ = 0.8 M$_\odot$ / (K km s$^{-1}$ pc$^2$) and C=1 in $\dot{M}_{\rm out} = C \frac{M_{\rm out}  v_{\rm out}}{R_{\rm out}}$. The high $R_{31}=2.1$ in IRAS 13120-5453 clearly indicates that this outflow is optically thin in CO. This cautions that $\alpha_{\rm CO(1-0)}$ may vary between outflows, but the good agreement with independent OH-based results globally supports the adopted CO conversion factor for outflows. We adopt conservative definitions of outflow flux and outflow velocity that focus on the line wings. While this may miss slow outflow components, which are likely to fall back, it improves robustness against confusion of outflow with undisturbed host gas.

\(3\) We compare our results with outflow properties that are based on *Herschel* far-infrared spectra of OH absorption, with special focus on the 12 ULIRGs with detailed OH models by (cite: gonzalez-alfonso17). The good agreement in derived properties is an important cross-validation of the two main methods for characterizing molecular outflows. Modest remaining differences may relate to different but overlapping regions sampled by the two methods: Smaller for the OH absorption vs. larger for CO emission.

\(4\) Outflow properties correlate better with AGN luminosity and with bolometric luminosity than with far-infrared surface brightness. The outflows with largest mass and mass outflow rate prefer systems with current luminous AGN activity, suggesting an important role of AGN driving, but significant outflows in some non-AGN systems must relate to star formation or to AGN activity in the recent past.

\(5\) We report scaling relations of outflow properties with bolometric luminosity (Eqns. [\[eq:moutlbol\]](#eq:moutlbol) to [\[eq:mrlbol\]](#eq:mrlbol)), but note that these might still be influenced by selection effects.

\(6\) Short $\sim 10^6$ yr flow times and some sources with spatially resolved multiple outflow episodes support a role of intermittent/episodic driving, likely by AGN.

# Acknowledgements

We thank the referee for a helpful report. This work is based on observations carried out under project numbers S16BH, S17AR, and W17CP with the IRAM NOEMA interferometer. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain). It is also based on ALMA projects ADS/JAO.ALMA#2016.1.00177.S and ADS/JAO.ALMA#2012.1.00306.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We acknowledge reduction support support by IRAM astronomers Miguel Montarges, Michael Bremer, and Melanie Krips. We thank Maria Drosdovskaya and Stefano Facchini for help concerning emission of the NS radical. S.V. acknowledges support from a Raymond and Beverley Sackler Distinguished Visitor Fellowship and thanks the host institute, the Institute of Astronomy, where this work was concluded. S.V. also acknowledges support by the Science and Technology Facilities Council (STFC) and by the Kavli Institute for Cosmology, Cambridge. R.M. acknowledges ERC Advanced Grant 695671 “QUENCH”.

132 natexlab

(ref: aalto16) Aalto, S., Costagliola, F., Muller, S., et al. 2016, A&A, 590, A73

(ref: aalto15) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2015, A&A, 574, A85

(ref: aalto12) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012a, A&A, 537, A44

(ref: aalto12a) Aalto, S., Muller, S., Sakamoto, K., et al. 2012b, A&A, 546, A68

(ref: aladro15) Aladro, R., Martı́n, S., Riquelme, D., et al. 2015, A&A, 579, A101

(ref: alatalo11) Alatalo, K., Blitz, L., Young, L. M., et al. 2011, ApJ, 735, 88

(ref: alonsoherrero19) Alonso-Herrero, A., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2019, A&A, 628, A65

(ref: alonso-herrero12) Alonso-Herrero, A., Pereira-Santaella, M., Rieke, G. H., & Rigopoulou, D. 2012, ApJ, 744, 2

(ref: baker00) Baker, A. J. 2000, PhD thesis, California Institute of Technology

(ref: barcos-munoz18) Barcos-Muñoz, L., Aalto, S., Thompson, T. A., et al. 2018, ApJL, 853, L28

(ref: barcos-munoz17) Barcos-Muñoz, L., Leroy, A. K., Evans, A. S., et al. 2017, ApJ, 843, 117

(ref: bischetti19) Bischetti, M., Piconcelli, E., Feruglio, C., et al. 2019, A&A, 628, A118

(ref: bolatto13) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013a, Nature, 499, 450

(ref: bolatto13a) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013b, ARA&A, 51, 207

(ref: bothwell13) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: brightman11) Brightman, M. & Nandra, K. 2011, MNRAS, 414, 3084

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: cicone18) Cicone, A., Severgnini, P., Papadopoulos, P., et al. 2018, ApJ, 863, 143

(ref: cicone12) Cicone, C., Feruglio, C., Maiolino, R., et al. 2012, A&A, 543, A99

(ref: cicone14) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: clavel13) Clavel, M., Terrier, R., Goldwurm, A., et al. 2013, A&A, 558, A32

(ref: combes19) Combes, F., Garcı́a-Burillo, S., Audibert, A., et al. 2019, A&A, 623, A79

(ref: combes13) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2013, A&A, 558, A124

(ref: combes14) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2014, A&A, 565, A97

(ref: contursi13) Contursi, A., Poglitsch, A., Grácia Carpio, J., et al. 2013, A&A, 549, A118

(ref: costagliola15) Costagliola, F., Sakamoto, K., Muller, S., et al. 2015, A&A, 582, A91

(ref: cox06) Cox, T. J., Dutta, S. N., Di Matteo, T., et al. 2006, ApJ, 650, 791

(ref: dasyra12) Dasyra, K. M. & Combes, F. 2012, A&A, 541, L7

(ref: dasyra14) Dasyra, K. M., Combes, F., Novak, G. S., et al. 2014, A&A, 565, A46

(ref: dasyra16) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7

(ref: davies19) Davies, R. L., Förster Schreiber, N. M., Übler, H., et al. 2019, ApJ, 873, 122

(ref: elbadry16) El-Badry, K., Wetzel, A., Geha, M., et al. 2016, ApJ, 820, 131

(ref: evans08) Evans, A. S., Vavilkin, T., Pizagno, J., et al. 2008, ApJL, 675, L69

(ref: fabian12) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: falstad18) Falstad, N., Aalto, S., Mangum, J. G., et al. 2018, A&A, 609, A75

(ref: falstad15) Falstad, N., González-Alfonso, E., Aalto, S., et al. 2015, A&A, 580, A52

(ref: falstad19) Falstad, N., Hallqvist, F., Aalto, S., et al. 2019, A&A, 623, A29

(ref: faucher-giguere12) Faucher-Giguère, C.-A. & Quataert, E. 2012, MNRAS, 425, 605

(ref: feruglio15) Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99

(ref: feruglio13) Feruglio, C., Fiore, F., Piconcelli, E., et al. 2013, A&A, 558, A87

(ref: feruglio10) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: fiore17) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: fischer10) Fischer, J., Sturm, E., González-Alfonso, E., et al. 2010, A&A, 518, L41

(ref: fluetsch19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: foersterschreiber19) Förster Schreiber, N. M., Übler, H., Davies, R. L., et al. 2019, ApJ, 875, 21

(ref: gabor13) Gabor, J. M. & Bournaud, F. 2013, MNRAS, 434, 606

(ref: gallagher19) Gallagher, R., Maiolino, R., Belfiore, F., et al. 2019, MNRAS, 485, 3409

(ref: gallimore16) Gallimore, J. F., Elitzur, M., Maiolino, R., et al. 2016, ApJL, 829, L7

(ref: garcia-burillo15) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2015, A&A, 580, A35

(ref: garcia-burillo14) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: genzel14) Genzel, R., Förster Schreiber, N. M., Rosario, D., et al. 2014, ApJ, 796, 7

(ref: giroletti17) Giroletti, M., Panessa, F., Longinotti, A. L., et al. 2017, A&A, 600, A87

(ref: gonzalez-alfonso12) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2012, A&A, 541, A4

(ref: gonzalez-alfonso17) González-Alfonso, E., Fischer, J., Spoon, H. W. W., et al. 2017, ApJ, 836, 11

(ref: gonzalez-martin15) González-Martı́n, O., Masegosa, J., Márquez, I., et al. 2015, A&A, 578, A74

(ref: gowardhan18) Gowardhan, A., Spoon, H., Riechers, D., et al. 2018, ApJ, 859, 35

(ref: guilloteau00) Guilloteau, S. & Lucas, R. 2000, in Astronomical Society of the Pacific Conference Series, Vol. 217, Imaging at Radio through Submillimeter Wavelengths, ed. J. G. Mangum & S. J. E. Radford, 299

(ref: hayward14) Hayward, C. C., Torrey, P., Springel, V., Hernquist, L., & Vogelsberger, M. 2014, MNRAS, 442, 1992

(ref: heckman02) Heckman, T. M. 2002, in Astronomical Society of the Pacific Conference Series, Vol. 254, Extragalactic Gas at Low Redshift, ed. J. S. Mulchaey & J. T. Stocke, 292

(ref: herrera-camus19a) Herrera-Camus, R., Janssen, A., Sturm, E., et al. 2019, A&A submitted

(ref: herrera-camus19b) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2019, in preparation

(ref: herrera-camus19) Herrera-Camus, R., Tacconi, L., Genzel, R., et al. 2019, ApJ, 871, 37

(ref: hopkins13) Hopkins, P. F., Cox, T. J., Hernquist, L., et al. 2013, MNRAS, 430, 1901

(ref: hopkins08) Hopkins, P. F., Cox, T. J., Kereš, D., & Hernquist, L. 2008, ApJS, 175, 390

(ref: iwasawa11) Iwasawa, K., Sanders, D. B., Teng, S. H., et al. 2011, A&A, 529, A106

(ref: janssen16b) Janssen, A. 2016, PhD thesis, Ludwig-Maximilians-Universität München

(ref: janssen16) Janssen, A. W., Christopher, N., Sturm, E., et al. 2016, ApJ, 822, 43

(ref: keel12) Keel, W. C., Chojnowski, S. D., Bennert, V. N., et al. 2012, MNRAS, 420, 878

(ref: kelly07) Kelly, B. C. 2007, ApJ, 665, 1489

(ref: kennicutt98) Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189

(ref: kim13) Kim, D.-C., Evans, A. S., Vavilkin, T., et al. 2013, ApJ, 768, 102

(ref: king15) King, A. & Pounds, K. 2015, ARA&A, 53, 115

(ref: laine99) Laine, S., Kenney, J. D. P., Yun, M. S., & Gottesman, S. T. 1999, ApJ, 511, 709

(ref: leon07) Leon, S., Eckart, A., Laine, S., et al. 2007, A&A, 473, 747

(ref: leroy15) Leroy, A. K., Walter, F., Decarli, R., et al. 2015a, ApJ, 811, 15

(ref: leroy15a) Leroy, A. K., Walter, F., Martini, P., et al. 2015b, ApJ, 814, 83

(ref: lintott09) Lintott, C. J., Schawinski, K., Keel, W., et al. 2009, MNRAS, 399, 129

(ref: longinotti18) Longinotti, A. L., Vega, O., Krongold, Y., et al. 2018, ApJL, 867, L11

(ref: lutz16) Lutz, D., Berta, S., Contursi, A., et al. 2016, A&A, 591, A136

(ref: lutz18) Lutz, D., Shimizu, T., Davies, R. I., et al. 2018, A&A, 609, A9

(ref: maiolino17) Maiolino, R., Russell, H. R., Fabian, A. C., et al. 2017, Nature, 544, 202

(ref: mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: meier15) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, ApJ, 801, 63

(ref: mihos96) Mihos, J. C. & Hernquist, L. 1996, ApJ, 464, 641

(ref: murray05) Murray, N., Quataert, E., & Thompson, T. A. 2005, ApJ, 618, 569

(ref: nardini10) Nardini, E., Risaliti, G., Watabe, Y., Salvati, M., & Sani, E. 2010, MNRAS, 405, 2505

(ref: newman12) Newman, S. F., Genzel, R., Förster-Schreiber, N. M., et al. 2012, ApJ, 761, 43

(ref: novak11) Novak, G. S., Ostriker, J. P., & Ciotti, L. 2011, ApJ, 737, 26

(ref: pereira-santaella16) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2016, A&A, 594, A81

(ref: pereira-santaella18) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2018, A&A, 616, A171

(ref: privon17) Privon, G. C., Aalto, S., Falstad, N., et al. 2017, ApJ, 835, 213

(ref: querejeta16) Querejeta, M., Schinnerer, E., Garcı́a-Burillo, S., et al. 2016, A&A, 593, A118

(ref: ramakrishnan19) Ramakrishnan, V., Nagar, N. M., Finlez, C., et al. 2019, MNRAS, 487, 444

(ref: ricci17) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017, ApJS, 233, 17

(ref: rodriguezdelpino19) Rodrı́guez del Pino, B., Arribas, S., Piqueras López, J., Villar-Martı́n, M., & Colina, L. 2019, MNRAS, 486, 344

(ref: roelfsema18) Roelfsema, P. R., Shibai, H., Armus, L., et al. 2018, PASA, 35, e030

(ref: rossa07) Rossa, J., Laine, S., van der Marel, R. P., et al. 2007, AJ, 134, 2124

(ref: rupke05b) Rupke, D. S., Veilleux, S., & Sanders, D. B. 2005, ApJS, 160, 115

(ref: rupke17) Rupke, D. S. N., Gültekin, K., & Veilleux, S. 2017, ApJ, 850, 40

(ref: rupke13) Rupke, D. S. N. & Veilleux, S. 2013, ApJ, 768, 75

(ref: sakamoto14) Sakamoto, K., Aalto, S., Combes, F., Evans, A., & Peck, A. 2014, ApJ, 797, 90

(ref: sakamoto13) Sakamoto, K., Aalto, S., Costagliola, F., et al. 2013, ApJ, 764, 42

(ref: salak16) Salak, D., Nakai, N., Hatakeyama, T., & Miyamoto, Y. 2016, ApJ, 823, 68

(ref: sartori18) Sartori, L. F., Schawinski, K., Trakhtenbrot, B., et al. 2018, MNRAS, 476, L34

(ref: schawinski15) Schawinski, K., Koss, M., Berney, S., & Sartori, L. F. 2015, MNRAS, 451, 2517

(ref: schirmer13) Schirmer, M., Diaz, R., Holhjem, K., Levenson, N. A., & Winge, C. 2013, ApJ, 763, 60

(ref: sempere95) Sempere, M. J., Combes, F., & Casoli, F. 1995, A&A, 299, 371

(ref: slater19) Slater, R., Nagar, N. M., Schnorr-Müller, A., et al. 2019, A&A, 621, A83

(ref: sliwa17) Sliwa, K., Wilson, C. D., Aalto, S., & Privon, G. C. 2017, ApJL, 840, L11

(ref: spilker18) Spilker, J. S., Aravena, M., Béthermin, M., et al. 2018, Science, 361, 1016

(ref: spoon13) Spoon, H. W. W., Farrah, D., Lebouteiller, V., et al. 2013, ApJ, 775, 127

(ref: stone18) Stone, M., Veilleux, S., González-Alfonso, E., Spoon, H., & Sturm, E. 2018, ApJ, 853, 132

(ref: stone16) Stone, M., Veilleux, S., Meléndez, M., et al. 2016, ApJ, 826, 111

(ref: strickland09) Strickland, D. K. & Heckman, T. M. 2009, ApJ, 697, 2030

(ref: sturm11) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: sun14) Sun, A.-L., Greene, J. E., Zakamska, N. L., & Nesvadba, N. P. H. 2014, ApJ, 790, 160

(ref: tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: tsai12) Tsai, A.-L., Matsushita, S., Kong, A. K. H., Matsumoto, H., & Kohno, K. 2012, ApJ, 752, 38

(ref: tsai09) Tsai, A.-L., Matsushita, S., Nakanishi, K., et al. 2009, PASJ, 61, 237

(ref: veilleux17) Veilleux, S., Bolatto, A., Tombesi, F., et al. 2017, ApJ, 843, 18

(ref: veilleux05) Veilleux, S., Cecil, G., & Bland-Hawthorn, J. 2005, ARA&A, 43, 769

(ref: veilleux13) Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27

(ref: walter17) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265

(ref: walter02) Walter, F., Weiss, A., & Scoville, N. 2002, ApJL, 580, L21

(ref: wang18) Wang, X. & Loeb, A. 2018, New A, 61, 95

(ref: almatechhandbook18) Warmels, R., Biggs, A., Cortes, P., A., et al. 2018, ALMA Technical Handbook, ALMA Doc 6.3, ver 1.0, ISBN 978-3-923524-66-2

(ref: weiss05) Weiß, A., Walter, F., & Scoville, N. Z. 2005, A&A, 438, 533

(ref: wuyts10) Wuyts, S., Cox, T. J., Hayward, C. C., et al. 2010, ApJ, 722, 1666

(ref: zschaechner18) Zschaechner, L. K., Bolatto, A. D., Walter, F., et al. 2018, ApJ, 867, 111

(ref: zubovas12) Zubovas, K. & King, A. 2012, ApJL, 745, L34

(ref: zubovas16) Zubovas, K. & King, A. 2016, MNRAS, 462, 4055

(ref: zubovas14) Zubovas, K. & King, A. R. 2014, MNRAS, 439, 400

# Figures for individual sources

![image](plot_1stmom_iiizw035.pdf) ![image](plot_spec_iiizw035.pdf) ![image](plot_poschan_iiizw035.pdf) ![image](plot_pv_iiizw035_PA-45.pdf) ![image](plot_pv_iiizw035_PA+25.pdf)

![image](plot_1stmom_f05189.pdf) ![image](plot_spec_f05189.pdf) ![image](plot_poschan_f05189.pdf) ![image](plot_pv_f05189_PA+135.pdf) ![image](plot_pv_f05189_PA+90.pdf)

![image](plot_1stmom_ngc2623.pdf) ![image](plot_spec_ngc2623.pdf) ![image](plot_poschan_ngc2623.pdf) ![image](plot_pv_ngc2623_PA-10.pdf) ![image](plot_blue_ngc2623.pdf) ![image](plot_pv_ngc2623_PA+80.pdf)

![image](plot_1stmom_f09111.pdf) ![image](plot_spec_f09111.pdf) ![image](plot_poschan_f09111.pdf) ![image](plot_pv_f09111_PA+0.pdf) ![image](plot_pv_f09111_PA+90.pdf)

![image](plot_1stmom_f10173.pdf) ![image](plot_spec_f10173.pdf) ![image](plot_poschan_f10173.pdf) ![image](plot_pv_f10173_PA+45.pdf) ![image](plot_pv_f10173_PA-45.pdf)

![image](plot_1stmom_f12224.pdf) ![image](plot_spec_f12224.pdf) ![image](plot_poschan_f12224.pdf) ![image](plot_pv_f12224_PA+90.pdf) ![image](plot_pv_f12224_PA-30.pdf)

![image](plot_1stmom_ngc4418.pdf) ![image](plot_spec_ngc4418_nssub_3hostcomp.pdf) ![image](plot_poschan_ngc4418.pdf) ![image](plot_pv_ngc4418_PA-35.pdf) ![image](plot_pv_ngc4418_PA+55.pdf)

![image](plot_1stmom_ic860.pdf) ![image](plot_spec_ic860.pdf) ![image](plot_poschan_ic860.pdf) ![image](plot_pv_ic860_PA+25.pdf)

![image](plot_1stmom_i13120.pdf) ![image](plot_spec_i13120.pdf) ![image](plot_poschan_i13120.pdf) ![image](plot_pv_i13120_PA+0.pdf) ![image](plot_pv_i13120_PA+90.pdf)

![image](plot_1stmom_f14378.pdf) ![image](plot_spec_f14378.pdf) ![image](plot_poschan_f14378.pdf) ![image](plot_pv_f14378_PA-70.pdf) ![image](plot_pv_f14378_PA+20.pdf)

![image](plot_1stmom_f17207.pdf) ![image](plot_spec_f17207.pdf) ![image](plot_poschan_f17207.pdf) ![image](plot_pv_f17207_PA+160.pdf) ![image](plot_pv_f17207_PA-50.pdf)

![image](plot_1stmom_f20551.pdf) ![image](plot_spec_f20551.pdf) ![image](plot_poschan_f20551.pdf) ![image](plot_pv_f20551_PA+45.pdf) ![image](plot_pv_f20551_PA-45.pdf)

![image](plot_1stmom_ngc7479.pdf) ![image](plot_spec_ngc7479.pdf) ![image](plot_poschan_ngc7479.pdf) ![image](plot_pv_ngc7479.pdf)

# Detected lines

The observations used in this paper were targeted at CO(1-0) but some additional lines are detected in the wide NOEMA or ALMA bands. Table [\[tab:applines\]](#tab:applines) lists these lines and their measured total fluxes.

|  |  |  |  |  |
|:---|---:|:---|:---|---:|
| Source | $\nu_{\rm Obs}$ | Line | $\nu_{\rm Rest}$ | Flux |
|  | GHz |  | GHz | Jy km s$^{-1}$ |
| III Zw 035 | 112.21 | CO(1-0) | 115.27 | 70.6 |
| III Zw 035 | 110.45 | CN N=1-0 | 113.49 m | 5.8 |
| III Zw 035 | 110.15 | CN N=1-0 | 113.19 m | 2.7 |
| IRAS F05189-2524 | 110.54 | CO(1-0) | 115.27 | 25.7 |
| IRAS F05189-2524 | 108.83 | CN N=1-0 | 113.49 m | 4.4 |
| IRAS F05189-2524 | 108.52 | CN N=1-0 | 113.19 m | 2.3 |
| IRAS F05189-2524 | 95.96 | HC$_3$N 11-10 | 100.08 | 0.5 |
| NGC 2623 | 113.18 | CO(1-0) | 115.27 | 161.0 |
| NGC 2623 | 111.44 | CN N=1-0 | 113.49 m | 8.5 |
| NGC 2623 | 111.13 | CN N=1-0 | 113.19 m | 4.9 |
| IRAS F09111-1007W | 109.33 | CO(1-0) | 115.27 | 51.0 |
| IRAS F09111-1007W | 107.64 | CN N=1-0 | 113.49 m | 4.0 |
| IRAS F09111-1007W | 107.33 | CN N=1-0 | 113.19 m | 2.6 |
| IRAS F09111-1107W | 94.92 | HC$_3$N 11-10 | 100.08 | 0.3 |
| IRAS F09111-1007E | 109.28 | CO(1-0) | 115.27 | 19.7 |
| IRAS F10173+0828 | 109.89 | CO(1-0) | 115.27 | 24.2 |
| IRAS F10173+0828 | 108.19 | CN N=1-0 | 113.49 m | 1.4 |
| IRAS F10173+0828 | 107.89 | CN N=1-0 | 113.19 m | 0.7 |
| IRAS F10173+0828 | 95.41 | HC$_3$N 11-10 | 100.08 | 0.7 |
| IRAS F12224-0624 | 112.30 | CO(1-0) | 115.27 | 22.6 |
| IRAS F12224-0624 | 110.56 | CN N=1-0 | 113.49 m | 2.0 |
| IRAS F12224-0624 | 110.25 | CN N=1-0 | 113.19 m | 1.1 |
| IRAS F12224-0624 | 98.02 | ? | 100.62 m | 0.4 |
| IRAS F12224-0624 | 97.50 | HC$_3$N 11-10 | 100.08 | 0.8 |
| NGC 4418 | 114.47 | CO(1-0) | 115.27 | 117.0 |
| NGC 4418 | 112.70 | CN N=1-0 | 113.49 | 10.5 |
| NGC 4418 | 112.38 | CN N=1-0 | 113.19 | 4.6 |
| NGC 4418 | 101.81 | CH$_3$CCH | 102.54 | 0.7 |
| IC 860 | 113.80 | CO(1-0) | 115.27 | 73.1 |
| IC 860 | 112.05 | CN N=1-0 | 113.49 m | 4.6 |
| IRAS 13120-5453 | 111.80 | CO(1-0) | 115.27 | 234.0 |
| IRAS 13120-5453 | 110.07 | CN N=1-0 | 113.49 m | 24.6 |
| IRAS 13120-5453 | 109.75 | CN N=1-0 | 113.19 m | 14.6 |
| IRAS 13120-5453 | 97.58 | ? | 100.61 m | 0.8 |
| IRAS 13120-5453 | 97.08 | HC$_3$N 11-10 | 100.08 | 1.0 |
| IRAS F14378-3651 | 107.92 | CO(1-0) | 115.27 | 24.7 |
| IRAS F14378-3651 | 106.26 | CN N=1-0 | 113.49 m | 2.4 |
| IRAS F14378-3651 | 105.95 | CN N=1-0 | 113.19 m | 1.3 |
| IRAS F17207-0014 | 110.54 | CO(1-0) | 115.27 | 171.0 |
| IRAS F17207-0014 | 108.83 | CN N=1-0 | 113.49 m | 10.0 |
| IRAS F17207-0014 | 108.53 | CN N=1-0 | 113.19 m | 4.5 |
| IRAS F17207-0014 | 98.33 | CH$_3$CCH | 102.54 | 0.2 |
| IRAS F17207-0014 | 96.50 | ? | 100.63 m | 0.5 |
| IRAS F17207-0014 | 95.97 | HC$_3$N 11-10 | 100.08 | 2.9 |
| IRAS F20551-4250 | 110.52 | CO(1-0) | 115.27 | 54.9 |
| IRAS F20551-4250 | 108.82 | CN N=1-0 | 113.49 | 2.3 |
| IRAS F20551-4250 | 108.50 | CN N=1-0 | 113.19 | 1.0 |
| NGC 7479 (30$''$) | 114.39 | CO(1-0) | 115.27 | 270.0 |
| NGC 7479 (30$''$) | 112.60 | CN N=1-0 | 113.49 m | 6.4 |

Table notes: Total fluxes, or fluxes in the indicated aperture diameter, for lines detected in the spectral ranges covered by NOEMA and ALMA. For the very rich spectrum of NGC 4418 we list only a few bright lines that are also detected in other targets. The listed frequencies are indicative for identification purposes only, in particular for lines with multiple components marked ’m’.

[^1]: http://www.iram.fr/IRAMFR/GILDAS

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Multi-Gaussian fit to nuclear/aperture spectra with visual choice of host components; v_out=|dv|+FW10%/2; S_CO(wings) integrates the broad component where it contributes >50%; R_out=|dR|+FWHM/2 from UV-plane Gaussian fit to outflow velocity range",
  "failed_quote": "we adopt as outflow velocity $v_{\\rm out}= |\\Delta v| + \\frac{FW_{10\\%}} {2}$"
 },
 {
  "path": "analysis_steps[5].validation.evidence[0]",
  "value": "Tested adding fiducial R_out=0.7 kpc, v_out=450 km/s for limits: slope unchanged, normalization -0.1 dex",
  "failed_quote": "leaves the slope of Eqn. effectively unchanged, and reduces the normalization by $\\sim$0.1 dex"
 }
]
```
