# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...673A..46B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Another X-ray UFO without a momentum-boosted molecular outflow

# Introduction

Galaxy formation and evolution is a complex process involving several different physical phenomena acting simultaneously on different physical and temporal scales. Gas is a key player in this picture, feeding star formation and the accretion onto the central supermassive black hole (SMBH), and is in turn affected by feedback mechanisms. The feedback can manifest through powerful winds that are able to blow away the gas from the centre of the galaxy, quenching star formation and starving the BH of fuel (cite: 2020Veilleux). Active galactic nucleus (AGN) feedback processes play a fundamental role in galaxy growth and evolution; they are thought to be at the origin of the M$_{\rm BH}-\sigma_\star$ relation (cite: 2010King; 1998Silk-Rees) and to prevent the overgrowth of massive galaxies (cite: 2012Bower; 2014Hopkins).

In the hard X-ray spectrum, hot (T$\sim10^6-10^7$ K) ultra-fast outflows (UFOs) have been observed in $\sim$40% of the bright nearby local AGN population (cite: 2010Tombesi; Tombesi2012; Gofford2013; Gofford2015). These winds, developed from the AGN accretion disk ($\le$ 1 pc), are observed through the detection of blueshifted (velocities up to $v\sim 0.3$c) absorption lines associated with highly ionised iron transitions in the hard X-ray spectrum (cite: 2003Reeves; 2010Tombesi).

Massive galaxy-scale cold ($T_{kin}\sim10-100$ K) molecular outflows with velocities between hundreds of and a few thousand km s$^{-1}$ have been observed in the last decade (cite: 2010Feruglio; 2010Fisher). These winds can be detected by P Cygni profiles of the OH molecule in the far-IR regime (cite: 2010Fisher; 2010Feruglio; 2011Sturm; 2013Veilleux) as well as blue- and redshifted high-velocity wings in the CO, HCN, or HCO$^+$ profiles using interferometric observations in the millimetre band (cite: 2012Aalto; 2012Cicone; 2014Cicone).

The theoretical model that is usually invoked to explain large-scale outflows launched by AGNs is the blast-wave scenario (cite: 1998Silk-Rees; 2010King; 2012Faucher-Giguere). According to this model, a nuclear wind arises from the accretion disk of an AGN and impacts on the interstellar medium (ISM) producing a forward shock and a reverse shock. The forward shock propagates through the unperturbed ISM producing a large-scale outflow. This outflow could be either energy- or momentum-driven, depending on whether cooling of the reverse shock is efficient. If it is, the energy is conserved and outflow propagates adiabatically (energy-driven), showing a momentum boost with respect to the X-ray wind ($\dot{p}_{out}^{\rm ISM}/\dot{p}_{out}^{\rm X-ray}>>1$; (cite: 2012Faucher-Giguere)). Otherwise, the energy is radiated away and only momentum is transferred to the ISM ($\dot{p}_{out}^{\rm ISM}/\dot{p}_{out}^{\rm X-ray}\sim1$; (cite: 2010King)).

Which model is most favoured by observations is a highly debated question. Simultaneous observations of X-ray winds and large-scale outflows are needed to test their predictions. The momentum rate versus wind velocity diagram is a widely used tool to visualise and compare the properties of different outflows (cite: 2015Feruglio; 2015Tombesi). (cite: 2019Smith) recently summarised the momentum rate versus the wind velocity for a sample of ten objects with observed X-ray UFOs and large-scale galactic outflows (see also Fig. [16](#fig:smithplot), this work). Some of these sources, such as the luminous quasar PDS 456 (cite: 2019Bischetti) and the ultra-luminous infrared galaxy (ULIRG[^2]) IRAS F11119+3257 (cite: 2015Tombesi; 2017Veilleux), seem to favour the momentum-driven scenario, while other objects, such as the ULIRG Mrk 231 (cite: 2015Feruglio) and the Seyfert 1 galaxy IRAS 17020+4544 (cite: 2015Longinotti; 2018Longinotti), show large-scale outflows whose momentum rate is boosted compared to the X-ray wind. Finally, other sources, such as the multiple-lensed quasar SDSS J1353+1138 (cite: 2021Tozzi), do not appear to favour either of the AGN feedback models. Overall, as clearly drawn by (cite: 2019Smith), the picture is much more complex than expected from AGN blast-wave feedback models.

Furthermore, most sources in the sample explored by (cite: 2019Smith) are ULIRGs. These objects have an intense star formation, whose contribution to feedback processes is hard to distinguish from the AGN contribution. Testing the prediction of the blast-wave scenario in galaxies with a more moderate star formation activity is necessary to overcome this issue. The work by (cite: 2019Sirressi) on the local Seyfert 2 galaxy MCG-03-58-007, with a star formation rate (SFR) $\sim$20 M$_\odot$ yr$^{-1}$, was a first step towards this direction. These authors detected a compact H$_2$ component that, if interpreted as an outflow, would present a momentum rate equal to $\sim$40% of that of the X-ray UFO. Our study on the LIRG and galaxy pair IRAS 05054+1718 (also known as CGCG 468-002) also fits into this context. The main target of this work is the western component of the pair (hereafter NED01), a local LIRG hosting a Seyfert 1.9 nucleus. The source shows a moderate SFR of 5-10 M $_\odot$ yr$^{-1}$ (cite: 2014Delooze; 2015Pereira) and hosts a powerful X-ray wind (cite: 2015Ballo), being a suitable candidate to test the AGN feedback scenario reducing the possible contamination from star formation-driven outflows.

Our aim is to investigate the presence of a large-scale molecular outflow in NED01 and in the companion NED02, by studying the distribution and the kinematics of the molecular gas. The latter is the phase of the ISM that is most tightly connected to star formation (cite: 2002Wong; 2008Bigiel; 2008Leroy), as stars form primarily in molecular clouds (cite: 2010Lada; 2014Andre). We use carbon monoxide (CO) as a tracer of cold molecular hydrogen ($H_2$), because it is the second most abundant molecule after $H_2$, and its rotational transitions are easily observable at submillimetre–millimetre wavelengths. The lowest J levels of CO can be easily excited at molecular cloud temperatures (cite: 2007Omont) and so the CO(1-0) and CO(2-1) lines can be used to estimate the total molecular gas mass in galaxies. Since these lines are optically thick at typical molecular cloud conditions, their luminosity is not proportional to the H$_2$ gas column density, but a CO(1-0)$-$to$-H_2$ conversion factor ($\alpha_{\rm CO}$) needs to be assumed. The estimate of this value is not straightforward as it depends on the physical state of the gas and needs to be calibrated using multiple molecular line tracers, which are often difficult to detect in extragalactic sources. For the Milky Way ISM and for normal star-forming galaxies, a value of $\alpha_{\rm CO}$= 4.3 M$_\odot$ (K km s$^{-1}$ pc$^2$) is widely accepted (cite: 2013Bolatto). For different ISM environments, such as the massive molecular outflows discovered in local starbursts and AGN host galaxies (cite: 2020Veilleux), the $\alpha_{\rm CO}$ parameter is very poorly constrained. In this work we assume that molecular outflows have an $\alpha_{\rm CO}$=2.1$\pm$1.2 M$_\odot$ (K km s$^{-1}$ pc$^2$), which is the value measured by (cite: 2018Cicone2) on the molecular outflow of the well-studied local ULIRG NGC 6240. We use $\alpha_{\rm CO}$=4.3$\pm$1.3 M$_\odot$ (K km s$^{-1}$ pc$^2$), a value typically assumed when treating the molecular ISM of isolated galaxies like the Milky Way (cite: 2013Bolatto), to evaluate the molecular mass of the galaxy disk.

This paper is organised as follows. The selected targets are presented in Sect. [2](#sec:targets). In Sect. [3](#sec:observations) we describe the new high-sensitivity Atacama Large Millimetre/submillimetre Array (ALMA) CO(1-0) observations used in this work. The analysis performed on the data is reported in Sect. [4](#sec:analysis). In Sect. [5](#sec:kinematics) we model the kinematics of the CO(1-0) emission using the 3D-Based Analysis of Rotating Object via Line Observations (3D-BAROLO) software for the two targets. In Sects. [6](#sec:X-ray) and [7](#sec:X-ray_analysis) we present the observations and the analysis of the new X-ray datasets, and in Sect. [8](#sec:X-ray_energetics) we derive the energetics of the X-ray wind. The interpretation of the results is discussed in Sect. [9](#sec:discussion), where we test different hypothesis in the AGN-driven feedback scenario. In Sect. [10](#sec:summary) we summarise our results and conclusions.

Throughout the paper we adopt a standard $\Lambda$CDM cosmological model with $H_0=67.8$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\Lambda}=0.692$, and $\Omega_M=0.308$ (cite: 2016PlanckCollaboration). At the distance of IRAS 05054+1718 NED01 ($z=0.0178$, revised in this work), the physical scale is 0.373 kpc arcsec$^{-1}$.

# Target description

The western and eastern pair members, in this work indicated respectively as NED01 and NED02 (see also (cite: 2015Pereira)), have a projected distance of $\sim29.6''\sim11$ kpc. Figure [1](#fig:source) shows the ALMA CO(1-0) contours overlayed onto a g-band image from the Pan-STARR Survey 1 (cite: Panstar). According to (cite: 2013Stierwalt), the system is in an early merger stage after a first encounter between the two galaxies since their disks are still symmetric, but show signs of tidal tales.

![image](Figures/PanSTARRS_CO10_image.png)\

The western galaxy NED01, at $z=0.0178\pm0.0004$[^3], hosts a Seyfert 1.9 nucleus, and it is classified as a LIRG ($\rm log(L_{IR(8-1000\mu m)}/L_\odot$)=10.6, (cite: 2015Pereira)). Because of the presence of the AGN, its SFR is not well constrained in the literature, with values ranging between 5 M$_{\rm \odot}$ yr$^{-1}$ (cite: 2014Delooze; 2015Pereira) and $\sim$10 M$_{\rm \odot}$ yr$^{-1}$ (cite: 2010Howell). Based on the ratio of the SFR to the BH accretion rate ($\rm \log(SFR/\dot{m}_{BH})\sim2$), obtained from the \[Neii\]15.56 $\mu m$ and \[Oiii\]$\lambda5007$ gas velocity dispersion, the stellar velocity dispersion, and the 8-1000 $\mu m$ IR-luminosity, (cite: 2013Alonso-Herrero) suggested that NED01 is transitioning from a Hii-dominated to a Seyfert-dominated LIRG.

NED01 represents an interesting case study for the effects of AGN feedback on galaxies. (cite: 2015Ballo) detected a deep absorption trough at $E\sim7.8$ keV (2.1$\sigma$ significance) in its *Swift*-XRT (X-ray telescope) spectrum, which has been interpreted as a highly ionised (log$\xi\sim3$ erg cm$^{-2}$ s$^{-1}$), high column density ($N_{\rm H}\sim10^{23}$ cm$^{-2}$), and ultra-fast ($v_{\rm out}=(0.11\pm0.03) c$) disk wind.

The companion NED02 is also a LIRG ($L_{IR}=10^{11}L_\odot$, (cite: 2015Pereira)) and has a measured redshift of $z=0.016812\pm0.000003.$[^4] NED02 was classified as a composite galaxy according to the BPT classification by (cite: 2015Pereira), but no evidence for AGN emission has been detected to date (cite: 2012Alonso-Herrero). The SFR estimates for this galaxy range between SFR$_{\rm (1-10) Myr}\sim15$ M$_{\rm \odot}$ yr$^{-1}$ (cite: 2015Pereira) and SFR$\sim20$ M$_{\rm \odot}$ yr$^{-1}$ (cite: 2010Howell; 2014Delooze).

# ALMA CO(1-0) observations

The ALMA Band 3 (84.0-116.0 GHz) observations of IRAS 05054+1718 were carried out in Cycle 5 (Project code: 2016.1.00694.S, PI: P. Severgnini). The primary target was NED01 (corresponding to the phase centre of the interferometric dataset), but the field of view and spectral bandwidth of the data also cover the CO(1-0) emission from the companion NED02, and so we include the latter in our analysis. We only use data from the two scheduling blocks that have passed the ALMA data quality assurance (QA0), which are also the only datasets that were delivered to the PI, with observing dates 5 and 6 March 2017. According to the QA0 report, the total observing time including overheads for the two combined valid execution blocks was 100 min, and the total time on target was 62 min. The 40 ALMA 12m antennas were arranged in the most compact configuration (C40-1), with baselines ranging from 14 m to 310 m. The precipitable water vapour (PWV) varied from 3mm to 8mm, wind speed was 3.3 m s$^{-1}$, and humidity $\sim50$%. The quasar J0423-0120 was used for flux calibration, J0510+1800 was instead used for band-pass response, phase calibration, and pointing, and both sources in addition to the main target were used for atmospheric calibration and radiometric phase correction.

We employed four spectral windows, two for each side band of the ALMA correlator. Two adjacent high-resolution, 1.875 GHz wide spectral windows (960 channels each, channel width of 1953.13 kHz, corresponding to 5.2 km s$^{-1}$) were centred at sky frequencies of $113.179$ GHz and $111.438$ GHz in order to sample both the CO(1-0) line and the $N=1$ spin-doublet transition of CN, which have rest-frame frequencies of $\nu^{rest}_{CO(1-0)}=115.2712$ GHz and $\nu^{rest}_{CN(1-0)}\simeq113.4910$ GHz.[^5] Two additional low-resolution 2 GHz wide spectral windows (128 channels, 15.625 MHz channel width, corresponding to $\sim50$ km s$^{-1}$) were centred at sky frequencies of 101.190 GHz and 99.387 GHz to probe the 3 mm continuum. In this work, we focus on the CO(1-0) line data, and we postpone the analysis of the CN(1-0) line to a future publication. Through the spectral line modelling described in Sect. [4.1](#sec:z-calc), we found the CO(1-0) lines of NED01 and NED02 to be respectively centred at (sky) frequencies of $\nu=113.2578$ GHz and $\nu=113.3651$ GHz, which we used to compute new estimates of the systemic redshift of the two galaxies. Except for Sect. [4.1](#sec:z-calc), where we worked with the initial datacubes not corrected for the right redshift, the rest of the analysis presented in this paper was performed on two separate datacubes (one for NED01 and one for NED02) corrected for their new CO-based redshift estimates.

The data were calibrated by running the version 5.4.0 of the Common Astronomy Software Applications (CASA) package calibration pipeline (cite: CASA). For the cleaning and other analysis steps we used CASA software version 5.6.1-8. We combined the measurement sets of the two execution blocks by using the task `concat`, after having pre-selected with `split` the CO(1-0) line spectral windows relevant to our target. An analysis of the continuum at $100$ GHz, conducted using the two line-free spectral windows (see further details in Appendix [11](#sec:appendix_continuum)), shows a clear detection of both NED01 and NED02, with respective continuum peak flux densities equal to $S_{cont}^{NED01} = 0.71\pm0.03$ mJy beam$^{-1}$ and $S_{cont}^{NED02} = 2.26\pm0.05$ mJy beam$^{-1}$. For this reason, before proceeding with the analysis of the CO kinematics, we subtracted the continuum from the CO(1-0) spectral windows in the *uv* visibility plane using the task `uvcontsub`. We selected a zeroth-order polynomial fit to the continuum channels adjacent to the CO(1-0) line in the 112.26-113.0 GHz and 113.57-114.12 GHz sky frequency ranges (corresponding to $v\in[-2650,-690]$ km s$^{-1}$ and $v\in[820, 2280]$ km s$^{-1}$ with respect to the CO(1-0) line centre). We then worked exclusively on the continuum-subtracted CO(1-0) line data.

The cleaning procedure for modelling the true sky brightness distribution of the source out of the *uv* visibility data was performed using the task `tclean`, by selecting the automasking algorithm (`auto-multithresh` parameter), which creates a different mask for every channel, minimising negative sidelobes. We used Briggs weighting with the robust parameter set equal to zero, and a cell size of $0.2''$. The synthesised beam size of the resulting cleaned datacube changes slightly with spectral channels, with a median value of $2.59''\times2.25''$, corresponding to an average spatial resolution of $\rm 0.97~kpc\times0.84~kpc$. We adopted the native spectral resolution of 5.17 km s$^{-1}$ for the channel size. We selected a cleaning threshold equal to our first estimate of the average line rms of $2.5$ mJy beam$^{-1}$ per channel. In order to account for the bias of the primary beam (PB) pattern on the image, we divided the cleaned datacube by the PB response using the task `impbcor`.

The mean rms CO(1-0) line sensitivity for source NED01 as measured in the cleaned and PB-corrected cube is 2.2 mJy beam$^{-1}$ per 5.2 km s$^{-1}$ channel. This value was calculated with the task `imstat`, by selecting the central $40''$ portion of the field of view, and so it is adequate to characterise the noise fluctuations of the CO(1-0) data for NED01. We also verified that the noise follows a Gaussian distribution, so we adopted the mean rms value across the whole CO(1-0) spectral range on which our analysis is focused. For the companion NED02 instead, given its proximity to the edge of the PB’s FWHM, the CO(1-0) line sensitivity is lower, with an average 1$\sigma$ rms value of 4.0 mJy beam$^{-1}$ per 5.2 km s$^{-1}$ channel. For this source, the 3D-BAROLO kinematic analysis (presented in Sect. [5.2](#sec:NED02_BBarolo)) will be conducted on a portion of the datacube centred on NED02 and not corrected for the PB. Table [1](#tab:obs-feature) summarises the main observational parameters.

|                                 |                                 |
|:--------------------------------|:--------------------------------|
| Instrument                      | ALMA Band 3                     |
| Target IDs                      | IRAS05054+1718 (pair)           |
|                                 | CGCG468-002 NED01 and NED02     |
| RA, Dec (ICRS)                  | 05:08:19.700, +17:21:48.100     |
| $\nu_{\rm rest}^{\rm CO(1-0)}$  | 115.2712 GHz                    |
| Spectral resolution             | 1953.125 kHz = 5.17 km s$^{-1}$ |
| Angular resolution              | $2.59''\times2.25''$            |
| Max recoverable scale           | $28''$                          |
| Field of view                   | $55''\times 55''$               |
| $1\sigma$ rms (5.2 km s$^{-1}$) | 2.2 mJy beam$^{-1}$ (NED01)     |
| $1\sigma$ rms (5.2 km s$^{-1}$) | 4.0 mJy beam$^{-1}$ (NED02)     |

: Description of observations

# Analysis of the CO(1-0) line emission

## CO-based redshift estimates

![image](Figures/redshift_NED01_tot_freq.pdf) ![image](Figures/redshift_NED02_freq.pdf)\
![image](Figures/fit_all.pdf) ![image](Figures/fit_ned02.pdf)\

+:--------+:---------------------:+:------------------:+:--------------------------:+:--------+:---------------------:+:------------------:+:--------------------------:+
| **NED01**                                                                         | **NED02**                                                                         |
+---------+-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
| Fit     | $\nu_0$ \[GHz\]       | $S_{peak}$ \[mJy\] | $\sigma_\nu$ \[MHz\]       | Fit     | $\nu_0$ \[GHz\]       | $S_{peak}$ \[mJy\] | $\sigma_\nu$ \[MHz\]       |
+---------+-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
| 1-Gauss | 113.2578 (0.0009)     | 78.5 (0.9)         | 66.2 (0.9)                 | 1-Gauss | 113.3651 (0.0003)     | 269 (2)            | 33.5 (0.3)                 |
+---------+-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
| 2-Gauss | 113.2176 (0.0010)     | 83.9 (1.3)         | 33.7 (1.0)                 |         |                       |                    |                            |
|         +-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
|         | 113.3125 (0.0011)     | 72.7 (1.4)         | 30.3 (1.0)                 |         |                       |                    |                            |
+---------+-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
| Fit     | $v_0$ \[km s$^{-1}$\] | $S_{peak}$ \[mJy\] | $\sigma_v$ \[km s$^{-1}$\] | Fit     | $v_0$ \[km s$^{-1}$\] | $S_{peak}$ \[mJy\] | $\sigma_v$ \[km s$^{-1}$\] |
+---------+-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
| 2-Gauss | $-146$ (3)            | 72.7 (1.3)         | 79 (2)                     | 1-Gauss | $-0.4$ (0.8)          | 265 (2)            | 88.4 (0.8)                 |
|         +-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+
|         | 106 (2)               | 82.9 (1.2)         | 90 (2)                     |         |                       |                    |                            |
+---------+-----------------------+--------------------+----------------------------+---------+-----------------------+--------------------+----------------------------+

*Notes:* The top and bottom parts of the table list respectively the best-fit parameters of the top and bottom panels of Fig. [2](#fig:total_co_spectra). For each Gaussian component, we report its centre, peak CO(1-0) flux density, and standard deviation ($\sigma$), from which it is possible to compute the full width at half maximum (FWHM = 2.3548$\sigma$). Uncertainties, always reported within brackets, correspond to 1$\sigma$ statistical errors and do not include the absolute flux calibration error.

### NED01

![](Figures/pv.pdf)

The continuum-subtracted CO(1-0) spectrum of NED01, reported in the left panels of Fig. [2](#fig:total_co_spectra), shows a double-peaked emission line centred at $\nu=113.26$ GHz. This is slightly different from the (redshifted) CO(1-0) central frequency of 113.189 GHz that was expected from a previous redshift estimate of this source ($z=0.0184$), derived from the heliocentric velocity (error-weighted average of the optical and radio velocities) reported in the HyperLeda catalogue (cite: 2014Makarov). To refine the redshift estimate of NED01 we performed two spectral fits, one with a single-Gaussian function and one with two Gaussians, both displayed in the top left panel of Fig. [2](#fig:total_co_spectra), with results listed in Table [\[tab:total_co_spectral_fits\]](#tab:total_co_spectral_fits). We computed a new systemic redshift using the central frequency value derived from the single-Gaussian fit ($\nu=113.2578\pm0.0009$ GHz). However, the source shows a double-peaked profile with clear asymmetries. To take this into account, we conservatively assigned to such CO-based redshift an uncertainty equal to the average frequency difference between the two CO line peaks (as measured from the double-Gaussian fit) and the single-Gaussian fit peak frequency value. We obtained $z=0.0178\pm0.0004$, which is offset by $v\sim-210 \ kms^{-1}$ with respect to the previously known redshift. We further checked that the new redshift estimate matches with the kinematic centre of NED01’s host galaxy disk. The CO(1-0) position-velocity (PV) diagrams displayed in Fig. [3](#fig:p-v) were computed in `CASA` from slit-like apertures with sizes of $\sim30''$ and $\sim9''$, aligned with the major and minor axes of the CO(1-0) disk of NED01 respectively (see kinematic modelling reported in Sect 5). The new redshift estimate (obtained through the spectral analysis described above) is shown as a black cross at the centre of the two PV diagrams, hence confirming the correspondence with the rotational centre of the CO(1-0) disk.

### NED02

A similar analysis aimed at refining the systemic redshift of the host galaxy was performed on the companion source, NED02. The total continuum-subtracted CO(1-0) spectrum of NED02, displayed in the right panel of Fig. [2](#fig:total_co_spectra), presents a single peak. We modelled it using a single-Gaussian function, whose best-fit parameters are reported in Table [\[tab:total_co_spectral_fits\]](#tab:total_co_spectral_fits). The previous redshift estimate for this source, $z=0.016842$, derived from the heliocentric velocity reported in the 2MASS *Redshift Survey* (cite: 2012Huchra), would have produced a CO(1-0) emission line peaked at 113.1385 GHz. Instead, our spectral analysis of the new ALMA CO(1-0) observations of NED02 shows that the CO(1-0)  line is centred at a higher frequency of $113.3651\pm 0.0003$ GHz. We used this value and its associated uncertainty to compute a new systemic redshift of NED02 equal to $z=0.016812\pm0.000003$, which is offset by $\sim50$ km s$^{-1}$ with respect to the previously known redshift.

## CO(1-0) morphology

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Source | $S_{\rm CO(1-0)}dv$ | $L^{\prime}_{\rm CO(1-0)}$ | $M_{mol}$ |
|  | \[Jy km s$^{-1}$\] | \[10$^8$ K km s$^{-1}$ pc$^2$\] | \[10$^9$ M$_{\odot}$\] |
| \(1\) | \(2\) | \(3\) | \(4\) |
| NED01 | 33.1 (1.4) | 5.1 (0.2) | 2.1 (0.7) |
| NED02 | 59 (3) | 8.0 (0.4) | 3.4 (1.1) |

: Molecular gas mass estimates

*Notes:* Col. (1): Source; Col. (2): Total CO(1-0) line flux, computed from the spectral line fit results (Table [\[tab:total_co_spectral_fits\]](#tab:total_co_spectral_fits)). For NED01, the total flux was computed by adding the contribution of the two Gaussian components employed in the spectral fit. Errors on the CO(1-0) integrated fluxes include a systematic calibration error of 5%, typical for ALMA Band 3 observations. Col. (3): CO(1-0) line luminosity computed following the definition by (cite: 1997Solomon); Col. (4): Molecular gas mass computed using a CO-to-H$_2$ conversion factor of $\alpha_{CO}$ = $4.3\pm1.3$ M$_{\odot}$ K km s$^{-1}$ pc$^2$ (cite: 2013Bolatto).

The redshift-corrected CO(1-0) emission line spectra of NED01 and NED02, plotted as a function of line-of-sight velocity, are shown in the bottom panels of Fig. [2](#fig:total_co_spectra). The corresponding best-fit spectral parameters are listed in Table [\[tab:total_co_spectral_fits\]](#tab:total_co_spectral_fits). By using the CO(1-0) line fluxes obtained from the spectral fits, we computed the total CO(1-0) line luminosities of the two galaxies, and from these estimated their molecular line masses, by adopting a standard CO-to-H$_2$ conversion factor of $\alpha_{CO}$ = $4.3\pm1.3$ M$_{\odot}$ K km s$^{-1}$ pc$^2$. These values are reported in Table [2](#tab:mol_masses).

![image](Figures/NED01_moment0.pdf) ![image](Figures/NED01_moment1_letters.pdf) ![image](Figures/NED01_moment2.pdf)\

![image](Figures/NED02_moment0.pdf) ![image](Figures/NED02_moment1.pdf) ![image](Figures/NED02_moment2.pdf)\

Figure [4](#fig:NED01_mom_maps) displays the zeroth, first, and second moment maps of the source NED01, computed by applying an intensity threshold of 0.01 Jy beam$^{-1}$ and within a box $30\ensuremath{''}$ in size centred on the AGN. The velocity map shows clearly that the CO(1-0) gas kinematics in NED01 is dominated by ordered rotation. The blueshifted emission arises from the western side of the galaxy, and the redshifted emission from the eastern side, following the typical pattern of a rotating disk. Therefore, from Fig. [4](#fig:NED01_mom_maps) we can already infer that if a molecular outflow is present, it does not seem to impact the bulk of the CO(1-0) kinematics in this source. This was also evident from the CO(1-0) spectrum of NED01, which presents a clear double peak and no evidence for very high-velocity wings, which are typical of extreme molecular outflows detected in some local (U)LIRGs (cite: 2014Cicone).

In addition to the central molecular disk (component A), the CO moment maps of NED01 reveal two apparently disconnected CO(1-0) emitting structures in this galaxy, labelled B and C in Fig. [4](#fig:NED01_mom_maps). Component B is $\sim3.3$ kpc and component C is $\sim2.3$ kpc from the centre of NED01’s main disk. Despite their apparent offset from the disk in the moment maps shown in Fig. [4](#fig:NED01_mom_maps), which results from the adoption of a sensitivity threshold, these two components are physically linked to the central disk, and also follow the same velocity pattern. This will be confirmed by the kinematic modelling with the BBarolo software presented in the next section. The CO(1-0) spectral line profiles of components B and C are single-peaked and narrow. Component B is redshifted, centred at a velocity of $v\simeq150$ km s$^{-1}$, with a velocity dispersion of $\sigma_v\simeq13$ km s$^{-1}$, and entrains a CO(1-0) flux of $0.65$ Jy km s$^{-1}$, which, if adopting the same $\alpha_{\rm CO}$ as above, corresponds to $\sim4\times10^7$ M$_\odot$ of molecular hydrogen gas. Component C is only slightly redshifted ($v\sim9$ km s$^{-1}$), and can be modelled with a single-Gaussian with $\sigma_v\simeq30$ km s$^{-1}$ and an integrated CO(1-0) flux of $2$ Jy km s$^{-1}$, corresponding to $1.3\times10^8$ M$_\odot$. Figure [1](#fig:source) shows that components B and C of the CO(1-0) emission from NED01 (detected respectively at 3 and 10$\sigma$ in the CO(1-0) channel map shown as contours in Fig. [1](#fig:source)) do not correspond to any significant sub-structure in the optical continuum; instead, they overlap with diffuse lower surface brightness stellar light. We can rule out the hypothesis that the CO components B and C are not distinguishable in the g-band Pan-STARR image because of high dust extinction, since in this case we would expect to detect them in the ALMA 3 mm continuum map, which is not the case (see Appendix [11](#sec:appendix_continuum)). We therefore suggest that the CO(1-0) components B and C are ISM substructures of the main galaxy disk, possibly tracing a spiral arm.

The companion galaxy NED02 is located close to the edge of the PB, and so the moment maps, reported in Fig. [5](#fig:NED02_mom_maps), were computed from the datacube not corrected for the PB. The CO(1-0) emission in this edge-on galaxy (see Fig. [1](#fig:source)) appears more compact than in NED01. The spider diagram shows a velocity gradient skewed towards blueshifted velocities, tracing a disturbed rotating disk. The modelling presented in the next section supports this interpretation.

# Modelling of the CO(1-0) kinematics

In this section we analyse the gas kinematics in IRAS 05054+1718. As shown by Fig. [4](#fig:NED01_mom_maps), the bulk of the CO(1-0) emission from NED01 traces a rotating molecular disk, while the disk of NED02 appears more disturbed (Fig. [5](#fig:NED02_mom_maps)). In order to study the presence of CO(1-0) components that are not participating in the rotation and may trace the effect of AGN feedback on the large-scale ISM, we first model the disk kinematics, and then study any residual emission, similar to (cite: 2019Sirressi). For completeness, we perform the same analysis on the companion galaxy NED02, even though we do not have any evidence for the presence of an AGN in this source. A uniform and common analysis of the CO(1-0) gas kinematics of both members of the galaxy pair can give us insights into the role of galaxy interactions in shaping the cold ISM kinematics.

## Modelling of the CO(1-0) disk in NED01

We model the disk rotation in NED01 using the 3D-Based Analysis of Rotating Object via Line Observations (cite: BAROLO). BBarolo identifies the set of geometrical and kinematic parameters that best fit the rotating gaseous disk observations, and uses these parameters to produce a mock datacube of the best-fit model. An important assumption of the BBarolo model, to consider when interpreting the results, is the hypothesis that the line emission is distributed in a geometrically thin disk whose kinematics is dominated by pure rotational motion. In other words, the model does not consider the presence of additional outflow components, tidal tails, or other features that do not belong to the main rotating disk. The disk model is built up by combining concentric rings with a user-defined width, and the comparison between models and data is performed ring by ring.

As shown by Fig. [4](#fig:NED01_mom_maps), the CO(1-0) line emission from NED01 has a complex morphology. In order to study the effect of adding the extended CO(1-0) line components in the BBarolo modelling, we run BBarolo on three regions with different sizes, and compare the results. The regions are as follows (see Fig. [20](#fig:mommap1)): the *small region*, which includes only component A, with size=$10''\times8''$ ($3.7\times3.0$ kpc); the *medium region*, which includes components A and C, with size=$16''\times15''$ ($6.0\times5.6$ kpc); and the *big region*, which includes all three components, with size=$35''\times35''$ ($13\times13$ kpc).

We produced the CO(1-0) datacubes that need to be given as an input to the software by cropping the continuum-subtracted ALMA CO(1-0) (clean) datacube with the CASA task `imsubimage` and then exporting it into a FITS file using the `exportfits` task. We selected a spectral range corresponding to $v$=\[-600,+600\]  km s$^{-1}$. For each region, we also produced a residual map by subtracting the BBarolo disk model from the input datacube.

As parameters of the BBarolo model we kept the inclination ($\iota$, i.e. the angle of the disk with respect to the line of sight) and the position angle (PA) of the molecular gas disk fixed at all radii. Using the ALMA moment 1 map shown in Fig. [20](#fig:mommap1), we estimated $PA=95^\circ\pm10^\circ$ and $\iota=45^\circ\pm15^\circ$. The inclination was inferred from the ratio of the minor to the major axis of the molecular disk. The fitting was performed considering only pixels with a $S/N>2.3$ to enable inclusion of the low-S/N extended features.

![](Figures/big/big_now_plot_maps_local.pdf)

![](Figures/big/big_new_plot_pv_local.pdf)

![](Figures/big/big_new_chanmaps_local.pdf)

In the following we present the results obtained by using the *Big region*, which includes all three CO(1-0) emission line components (A, B, and C) observed in the moment 1 map of NED01, while the results from the other two regions are reported in Appendix [12](#sec:appendix). We focus on the *Big region* because, once it has been subtracted from the ALMA datacube, this is the fit that produces the lowest residual CO(1-0) emission. Additionally, the analysis of the *Big region* fit allows us to study the global CO(1-0) emission from NED01 as this region includes also components B and C. We therefore believe that the fit on the *Big region* is the most conservative one for our goal, which is to study residual emission whose kinematics is inconsistent with a rotating disk.

We constructed the BBarolo model disk by using seven rings of width $2\ensuremath{''}$ (0.7 kpc), covering in total a region of $28\ensuremath{''}$ in diameter (10.4 kpc) around NED01. The results of this fit are shown in Figures [6](#fig:bigmom), [7](#fig:bigpv), and [8](#fig:bigchann). Although the rotating disk clearly provides a very good fit for the bulk of CO(1-0) emission in and around NED01, there are statistically significant residuals. We note that the moment maps and the PV diagrams produced by BBarolo (Figures [6](#fig:bigmom) and  [7](#fig:bigpv)) are not optimised to visualise residual emission, because they use a colour scale that is fine-tuned to enhance the match between data and model. The bottom rows of the channel maps in Fig. [8](#fig:bigchann), displaying the residual CO(1-0) emission, show that positive (green contours) and negative (grey contours) residuals with similar significance ($\sim3\sigma$) are present in each channel map with velocity $|v|>200$ km s$^{-1}$, consistent with low-level residual rotation that is not accounted for by the fit. However, at blueshifted velocities, within a range $-290<v<-200$ km s$^{-1}$, we detected only positive residuals at much higher significance ($S/N\ge15$), showing a compact morphology.

![image](Figures/big/big_res_blue.pdf) ![image](Figures/big/res_big.pdf) ![image](Figures/big/big_res_comp.pdf)\

Figure [9](#fig:residuals_bigregion) displays the CO(1-0) residual emission in NED01 after subtracting the best-fit disk model computed by BBarolo. The left panel of Fig. [9](#fig:residuals_bigregion) shows a contour map of such compact residual structure, obtained integrating the CO(1-0) residual flux within the velocity ranges where it is most prominent, that is $-290\lesssim v [\rm km~s^{-1}] \lesssim -200$. This structure can be enclosed within a box of $8.4''\times8.4''$ ($\sim3$ kpc, see black box overlayed on the map). We find that a similar residual, compact, and blueshifted structure is common to all three fits performed with BBarolo, and it is actually minimised in this one performed on the *Big region* compared to those using the smaller regions. The spectrum reported in the central panel of Fig. [9](#fig:residuals_bigregion), extracted from the black squared aperture in the left panel, shows that the blueshifted CO(1-0) residual emission is spectrally resolved into two emission peaks, which we modelled with double-Gaussian functions (see best-fit parameters in Table [3](#tab:bigres1_fit)). There is also a negative feature at the systemic velocity, common to all three BBarolo fits, which is probably an indication of overfitting of the rotational structure. By mapping separately the two blueshifted spectral components, we find that they trace two apparently independent, spatially offset structures, as shown in the right panel of Fig. [9](#fig:residuals_bigregion). Here we plotted with different colours the first component of this residual CO(1-0) emission, which is the most blueshifted one integrated between $v\in[-400, -200]$ km s$^{-1}$ (blue contours), and the second component, which was integrated between $v\in[-200, 0]$ km s$^{-1}$ and displayed using the black contours. The first component peaks closer to the dynamic centre of the molecular disk, at a distance of $R=0.7\pm0.2$ kpc, while the second component peaks further away, at a distance of $R=1.5\pm0.2$ kpc. Table [3](#tab:bigres1_fit) lists for each of the two components their spectral best-fit Gaussian parameters and corresponding CO(1-0) flux, CO(1-0) luminosity, molecular gas mass, and their physical distance from the best-fit BBarolo disk model.

| Parameter | Comp. 1 | Comp. 2 |
|:---|:--:|:--:|
| $v_{cen}$ \[km s$^{-1}$\] | -239 (2) | -146.9 (1.7) |
| $\sigma_v$ \[km s$^{-1}$\] | 31 (2) | 19.8 (1.8) |
| $S_{\rm CO(1-0)}dv$ \[Jy km s$^{-1}$\] | 1.63 (0.14) | 0.98 (0.11) |
| $L^{\prime}_{\rm CO(1-0)}$ \[10$^7$ K km s$^{-1}$ pc$^2$\] | 2.5 (0.2) | 1.50 (0.17) |
| $M_{mol}$$^{\dag}$ \[10$^8$ M$_{\odot}$\] | 0.5 (0.3) | 0.31 (0.18) |
| R \[kpc\] | 0.7 (0.2) | 1.5 (0.2) |

: Best-fit Gaussian parameters of the CO(1-0) residual spectrum of NED01 shown in Fig. [9](#fig:residuals_bigregion).

$^{\dag}$ Computed assuming $\alpha_{\rm CO} = 2.1 \pm 1.2$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$, which is the value with associated uncertainty estimated by (cite: 2018Cicone2) for the molecular outflow in NGC 6240.

## Modelling of the CO(1-0) disk in NED02

Compared to NED01, the CO(1-0) moment maps of NED02 in Fig. [5](#fig:NED02_mom_maps) show a more disturbed, higher inclination, molecular disk. The CO(1-0) emission detected by ALMA in this source is also more compact in size, and hence its morphology and kinematics are more affected by beam smearing effects. We used BBarolo to model this CO(1-0) disk, following a procedure similar to NED01. However, given the absence of significant extended features, we did not deem it necessary for NED02 to run BBarolo on regions of different sizes. The input 3D dataset for the BBarolo modelling was obtained by cropping the cleaned (non-PB-corrected) continuum-subtracted ALMA datacube around NED02 using a box size of $27.4''\times25.4''$ (i.e $9.4\times8.7$ kpc), and selecting a velocity range of $v\in[-1000,+1000]$ km s$^{-1}$, computed with respect to the systemic redshift of NED02. From the ALMA observations, we estimated a position angle of $PA=120^\circ\pm10^\circ$ and an inclination of $\iota=70^\circ\pm15^\circ$. We applied a S/N threshold of $S/N>3$ for each pixel included in the modelling. We used five rings, each of $2\ensuremath{''}$ width (0.7 kpc).

![](Figures/ned02/ned02_new_plot_maps_local.pdf)

![](Figures/ned02/ned02_new_plot_pv_local.pdf)

Figures [10](#fig:ned02mom),  [11](#fig:ned02pv), and  [21](#fig:ned02chann) show the moment maps, PV diagrams, and channel maps of NED02 produced by the fitting code, comparing the data with the best-fit model of a rotating disk. Although BBarolo can reproduce the global rotation pattern, we detect significant residuals, especially at blueshifted velocities, similar to what was found for NED01. The map of such residual CO(1-0) emission around NED02, integrated over the spectral range $v\in[-170, 20]$ km s$^{-1}$, is shown in the left panel of Fig. [12](#fig:residuals_NED02). The box shown on the map enclosing the 3$\sigma$ level CO(1-0) contours has a size of $8''\times8''$ ($\sim3\times3$ kpc). The spectrum of the CO(1-0) residual emission extracted from this region (central panel of Fig. [12](#fig:residuals_NED02)) shows two peaks. The two spectral features peak at different positions (right panel of Fig. [12](#fig:residuals_NED02)), where the CO(1-0) residual emission components integrated between $v\in(-350, -120)$ km s$^{-1}$ (blue contours) and $v\in(-120, 0)$ km s$^{-1}$ (black contours) are plotted separately. The two components do not overlap on the map, suggesting they trace physically distinct structures. Table [4](#tab:ned02_res) lists the best-fit spectral parameters of these two CO(1-0) residual features, their corresponding fluxes, luminosities, molecular gas mass estimates, and their distance from the CO(1-0) rotation centre of NED02.

![image](Figures/ned02/ned02_res.pdf) ![image](Figures/ned02/res_NED02.pdf) ![image](Figures/ned02/ned02_res_comp.pdf)\

| Parameter | Comp. 1 | Comp. 2 |
|:---|:--:|:--:|
| $v_{cen}$ \[km s$^{-1}$\] | -165 (3) | -73 (3) |
| $\sigma_v$ \[km s$^{-1}$\] | 34 (2) | 30 (2) |
| $S_{\rm CO(1-0)}dv$ \[Jy km s$^{-1}$\] | 2.4 (0.2) | 1.8 (0.2) |
| $L^{\prime}_{\rm CO(1-0)}$ \[10$^7$ K km s$^{-1}$ pc$^2$\] | 3.7 (0.3) | 2.7 (0.3) |
| $M_{mol}$$^{\dag}$ \[10$^8$ M$_{\odot}$\] | 0.8 (0.5) | 0.6 (0.3) |
| R \[kpc\] | 0.8 (0.2) | 1.6 (0.2) |

: Best-fit Gaussian parameters of the CO(1-0) residual spectrum of NED02 shown in Fig. [12](#fig:residuals_NED02).

$^{\dag}$ Computed assuming $\alpha_{\rm CO} = 2.1 \pm 1.2$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$; see also Table [3](#tab:bigres1_fit).

# X-ray observations

## Observations and data reduction

IRAS 05054+1718 was observed three times in the X-ray band. In 2012 it was observed by Nuclear Spectroscopic Telescope Array (*NuSTAR*, (cite: Harrison2013)) for a total of $\sim 16$ ksec; in 2014 it was the target of a monitoring programme (totalling $\sim 72$ ksec) performed with the Neil Gehrels Swift Observatory (cite: Gehrels2004); and more recently we obtained a simultaneous deep observation with *XMM-Newton* and *NuSTAR* (PI: V. Braito, 2021). The results of the *Swift* observations were published by (cite: 2015Ballo), while the 2012 *NuSTAR* data are reported in (cite: Ricci2017). According to these works, the X-ray spectrum of NED01 is that of a moderately absorbed Seyfert 2 galaxy (with photon index $\Gamma\sim 1.7$, column density $N_{\mbox{\scriptsize H}}\sim (1-2) \times 10^{22}$ cm$^{-2}$, and flux in the 2-10 keV regime $F_{\rm 2-10\, keV}=(0.6-1)\times10^{-11}$ erg cm$^{-2}$ s$^{-1}$) with the *NuSTAR* 3-10 keV flux in 2012 being a factor 1.6 brighter than the *Swift* value. (cite: 2015Ballo) first reported the presence of an absorption trough at $E\sim 7.8$ keV (at $2.1 \sigma$), which was interpreted as the presence of highly ionised wind, outflowing with a velocity of $v_{\rm out}\sim  0.1\,c$.

In this work, we re-analyse all X-ray spectra collected for NED01; we re-reduced the *XMM-Newton* and *NuSTAR* data, while for the *Swift* monitoring we consider the spectrum extracted by (cite: 2015Ballo). In Table [\[tab:X-rayobs\]](#tab:X-rayobs) we report the summary of the *XMM-Newton* and *NuSTAR* observations, while the list of the *Swift* observations can be found in Table 1 of (cite: 2015Ballo). Although the dominant X-ray source is NED01, the inspection of the soft (0.3-1.5 keV) *XMM* images revealed a faint X-ray source at the expected location of the NED02 as well as possible extended emission. In particular, for NED02 we detected $\sim200$ X-ray counts in the 0.3-1.5 keV band with *XMM*. Assuming that they are due to thermal emission ($kT=0.6\pm 0.2$ keV), as generally seen in star-forming galaxies, we derived $F_\mathrm {(0.5-2) keV}\sim 2\times 10^{-14}$ erg cm$^{-2}$ s$^{-1}$ and $L_\mathrm {(0.5-2) keV}\sim 2\times 10^{40}$ erg s$^{-1}$. At higher energies, we cannot assess if there is any X-ray emission from NED02 that could be indicative of a weak or highly obscured AGN because it falls within the wings of the PSF of the bright companion.

## *XMM-Newton*

We processed and cleaned the *XMM-Newton* data using the Science Analysis Software (SAS ver. 18.0.0) and the resulting spectra were analysed using standard software packages (FTOOLS ver. 6.30.1, XSPEC ver. 12.11; (cite: xspecref)). The *XMM-Newton*-EPIC instruments operated in full-frame mode and with the thin filter. We first filtered the EPIC data for high background, which only moderately affected the observations. The EPIC-pn, MOS1, and MOS2 source spectra were extracted using a circular region with a radius of $20''$, while for the background we adopted two circular regions with a radius of $20''$. The response matrices and the ancillary response files at the source position were generated using the SAS tasks *arfgen* and *rmfgen* and the latest calibration available. After checking for consistency we combined the spectra from each of the individual MOS detectors into a single spectrum. Both the pn and MOS spectra were then binned to at least 100 counts per bin.

## *NuSTAR*

*NuSTAR* observed IRAS 05054+1718 twice; the second observation was coordinated with *XMM-Newton*, starting at the same time but extending for 100 ksec beyond the *XMM-Newton* observation (see Table [\[tab:X-rayobs\]](#tab:X-rayobs)). We reduced the data following the standard procedure using the HEASOFT task NUPIPELINE (version 0.4.9) of the *NuSTAR* Data Analysis Software (NUSTARDAS, ver. 1.8.0). We used the calibration files released with the CALDB version 20220426 and applied the standard screening criteria, where we filtered for the passages through the SAS setting the mode to ‘optimised’ in NUCALSAA. For each of the Focal Plane Modules (FPMA and FPMB) the source spectra were extracted from a circular region with a radius of $50''$, while the background spectra were extracted from two circular regions with a $50''$ radius located on the same detector. Since the second set of observations partially overlap with the *XMM-Newton* exposure, we also extracted light curves in the 7-10 keV and 10-30 keV band from the same regions using the NUPRODUCTS task to check whether we could use the averaged spectra when performing a joint fit with the *XMM* spectra. The FPMA and FPMB background-subtracted light curves were then combined into a single curve. The inspection of these light curves revealed that in the last 100 ksec, not covered by *XMM-Newton*, NED01 was slightly brighter; we thus created a good time intervals (GTI) file corresponding to the strictly simultaneous part of the observation. This GTI file was then used to extract source and background spectra and the corresponding response files.

# X-ray spectral analysis

The spectral fits were performed with XSPEC (ver. 12.11) and in all the models we included the galactic absorption in the direction of NED01 ($N_{\mbox{\scriptsize H}}=1.93\times 10^{21}$ cm$^{-2}$, (cite: nhHI4PICollaboration)), which was modelled with the Tuebingen - Boulder absorption model (tbabs component in XSPEC, (cite: Wilms2000)). The source spectra were binned to have at least 20 counts in each energy bin for the *Swift* data, and 100 counts for the EPIC-pn, the EPIC-MOS, and the *NuSTAR* spectra. For the portion of the *NuSTAR* spectra that is strictly simultaneous with *XMM* we adopted a lower binning of 50 counts. We employed $\chi^2$ statistics and errors are quoted at the 90% confidence level for one interesting parameter. All the outflow velocities are relativistically corrected.

In Fig. [13](#fig:allxdata) we show all the X-ray spectra collected for NED01, obtained by unfolding the data against a power-law model with photon index $\Gamma=2$. It is clear that the *Swift* and the 2012 *NuSTAR* observations (black and red data points, respectively) caught NED01 in a similar bright state, while the most recent *XMM-Newton* and *NuSTAR* observations found the source in a much fainter state (blue and light blue data points, respectively). We therefore fit separately the 2012-2014 and 2021 epochs. It is also noticeable that the hard ($E>10$ keV) X-ray emission measured in the first *NuSTAR* observation is at the same level as the averaged *Swift*-BAT spectrum from the 70-month survey[^6] suggesting the bright one as the most frequent state (grey data points in Fig. [13](#fig:allxdata)).

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Observatory | Start Date | Instrument | Elapsed Time | Exposure$_{\rm(net)}$ | Count rate$_{\rm(net)}$ |
|  | \[UT time\] |  | \[ks\] | \[ks\]$^{\dag}$ | \[count s$^{-1}$\] |
| *NuSTAR*  | 2012-07-23 21:46 | FPMA/B | 26.5 | 15.5 | 0.242$\pm$0.003 |
| *XMM* | 2021-09-11 14:38 | MOS1 | 62.2 | 58.9 | 0.061$\pm$0.001 |
| *XMM* | 2021-09-11 14:38 | MOS2 | 62.1 | 59.2 | 0.062$\pm$0.001 |
| *NuSTAR*  | 2021-09-11 14:36 | FPMA/B | 165.6 | 81.3 | 0.038$\pm$0.001 |
| *XMM* | 2021-09-11 15:10 | PN | 59.9 | 54.2 | 0.174$\pm$0.002 |

$^{\dag}$ The net exposure times are obtained after the screening of the cleaned event files for high background and dead time.

![](Figures/X-ray/inset3.pdf)

## 2012 *NuSTAR* and 2014 *Swift* observations

We performed a joint fit for the *Swift* and *NuSTAR* spectra and considered the 0.3-10 keV and the 3.5-60 keV data for the *Swift* and FPM data, respectively. We first tested the baseline continuum model as reported in (cite: 2015Ballo), which is a typical model for a moderately obscured Seyfert 2 as NED01. The model is composed of an absorbed primary power-law component, a scattered component, with the same $\Gamma$, and a reflected component (modelled with the XILLVER component in XSPEC). The reflected component represents the emission produced by a distant material, such as the putative torus. We tied only the photon index. We allowed the $N_{\mbox{\scriptsize H}}$ of the neutral absorber, and the normalisation of the primary power-law and of the reflection components to differ.

This model provides a reasonable fit ($\chi^2=343.9/293$ degrees of freedom) and requires a standard photon index ($\Gamma=1.81\pm 0.06$). The column density of the neutral absorber is $N_{\mbox{\scriptsize H,  SW}}=(2.4\pm 0.2) \times 10^{22}$ cm$^{-2}$ and $N_{\mbox{\scriptsize H,  NU}}=(4.4\pm1.9)\times 10^{22}$cm$^{-2}$ for the *Swift* and the *NuSTAR* spectra, respectively. The *NuSTAR* 3-10 keV flux is a factor of 1.6 higher than the *Swift* value. Overall, this model is able to reproduce the broad-band emission, but it leaves some residuals in absorption that are shown in the inset of Fig. [13](#fig:allxdata). We thus included in the model two Gaussian absorption lines, and the fit improved by $\Delta \chi^2/\Delta \nu=19/6$. One feature is detected in the *Swift* spectrum at $E= 7.8\pm0.3$ keV ($\Delta \chi^2=6$) and the second at $E= 8.6\pm 0.2$ keV ($\Delta \chi^2=13$) in the *NuSTAR* data. The equivalent widths (EWs) of the absorption troughs are $220\pm 150$  eV and $190\pm 100$ eV in the *Swift* and *NuSTAR* data, respectively.

To self-consistently account for these features, we replaced the two Gaussian absorption lines with a multiplicative grid of photoionised absorbers generated with the XSTAR photoionisation code ((cite: xstar)). Since the lines appear to be broad ($\sigma_{\rm SW} \sim 0.2$ keV, $\sigma_{\rm NU} =0.3\pm 0.2$ keV), we chose a grid that was generated with a high turbulence velocity ($v_{\rm turb}=5000$ km s$^{-1}$) and with column density in the range $N_{\mbox{\scriptsize H}}=10^{21}$ - $3\times10^{24}$cm$^{-2}$ and ionisation[^7] log$\,\xi=1-6$. We assumed that the ionised absorber has the same ionisation, but allowed the $N_{\mbox{\scriptsize H}}$ and velocity to be different in the two epochs. The inclusion of the fast-outflowing and highly ionised (log$\,\xi=3.4\pm0.5$) absorber improves the fit by $\Delta \chi^2/\nu=20/5$. For the *Swift* observation we found $N_{\rm H, SW}=1.3_{-0.9}^{+1.7}\times10^{23}$ cm$^{-2}$ and $v_{\rm{out}}/c=- 0.12_{-0.05}^{+0.02}$, while for the *NuSTAR* spectrum we found $N_{\rm H, NU}=1.1\pm 0.6\times10^{23}$ cm$^{-2}$ and $v_{\rm{out}}/c= -0.23\pm 0.02$. Our independent analysis confirms the results reported by (cite: 2015Ballo), and also suggests that the wind in IRAS 05054+1718 could be variable or have multiple velocity components, as seen for other X-ray disk winds (e.g. PDS 456, (cite: Matzeu2017; Reeves2018); IRAS 13224-3809, (cite: Parker2018); MCG-03-58-007, (cite: Braito2022); HS0810+2554, (cite: Chartas2016); and IRAS 17020+4544, (cite: 2015Longinotti)). The best-fit model is given in Table [\[tab:bestfits\]](#tab:bestfits), while the spectra with their respective best-fit models are shown in Fig. [14](#fig:olddata).

![](Figures/X-ray/swift_nust_fit_new2.pdf)

## 2021 simultaneous **XMM-Newton** and *NuSTAR* observations

The 2021 *XMM* and *NuSTAR* observation caught NED01 in a faint state (see Fig. [13](#fig:allxdata)), where the observed 2-10 keV X-ray flux dropped by a factor of $\sim 4$ with respect to the 2012 and 2014 observations. At this lower flux level the *NuSTAR* spectrum becomes background-dominated above 40 keV. We thus limited our spectral analysis to the 0.3-10 keV energy band for the *XMM* data, and the 3.5-40 keV band for the *NuSTAR* spectrum. Figure [13](#fig:allxdata) also reveals that the average *NuSTAR* spectrum (light blue) lies well above the EPIC-pn spectrum (blue data points). If we apply the best-fit continuum model derived in the previous section, we find a cross-normalisation between *XMM* and *NuSTAR* of $C=1.36\pm 0.05$, which is well above the current uncertainties in the cross normalisation between the two observatories. We therefore considered only the portion of the *NuSTAR* observation that is strictly simultaneous with *XMM*, where we found $C=1.17\pm 0.06$. We note that the variation is mainly a flux change between the simultaneous spectrum and the last 100 ksec exposure, with no clear spectral variations. We applied the same baseline continuum model to the new observation, which describes well the overall spectral shape and already provides a reasonable fit ($\chi^2=255.7/205$ d.o.f.) to the spectra with no evident residuals. The broad-band spectra and the best-fit models are presented in Figure [15](#fig:newdata). The best-fit parameters are reported in Table [\[tab:bestfits\]](#tab:bestfits), where we note that the faint state is caused by a drop in the primary emission and not by an increase in absorption, as is often found for obscured AGN. Here the primary emission drops by a factor of $\sim 4$ with respect to the 2014 *Swift* spectrum and by an order of magnitude with respect to the 2012 *NuSTAR* observation.

Although there are no residuals that can be associated with the disk wind observed in the past observations, we estimated the upper limits on the column density for a putative ionised absorber outflowing at $v_{\rm{out}} =0.12\;c$ or $v_{\rm{out}}= 0.23\; c$ for the same ionisation parameter as found previously, of $\log \xi=3.4$. We found that they are of the order of $\sim 3\times 10^{22}$cm$^{-2}$ and $\sim 4\times 10^{22}$cm$^{-2}$ for the slower and the faster phase, respectively. The upper limits are only marginally below the 90% lower value of $N_{\mbox{\scriptsize H}}$ estimated in the past observations.

![](Figures/X-ray/new_data_eeuf2.pdf)

# The X-ray disk wind energetics of NED01

Here we compute a first-order estimate of the energetics of the disk wind detected in NED01. The values were estimated using only the 2012 *NuSTAR* and the 2014 *Swift* data where the wind was clearly detected.

Following the same arguments presented in many works on disk winds (e.g. (cite: Nardini2015; ReevesBraito2019; Braito2021)), we estimate the mass outflow rate of the X-ray wind using the equation $$\begin{equation}
\label{eq:xray_ofrate}
 \dot M_{out}^{X-ray}=\Omega~\mu~m_{\mathrm p}~v_{out}~R_{\rm w}~N_{\rm {H}},
\end{equation}$$ which assumes a biconical geometry for the flow ((cite: Krongold2007)). In Eq. [\[eq:xray_ofrate\]](#eq:xray_ofrate), $\mu$ is a constant factor set to $\mu=n_{\rm H}/n_{\rm e}=1.2$ for solar abundances, $\Omega$ is the wind solid angle, $R_{\rm{ w}}$ is the disk wind launching radius, $N_{\mbox{\scriptsize H}}$ and $v_{\rm {out}}$ are the column density and the velocity of the disk wind. The main uncertainties in Eq. [\[eq:xray_ofrate\]](#eq:xray_ofrate) are the wind opening angle ($\Omega$) and the launch radius $R_{\rm w}$. We assume that the wind subtends $\Omega/4\pi = 0.5$. This is justified by the systematic searches of ultra-fast disk winds in bright nearby AGN ((cite: Gofford2013) and (cite: 2010Tombesi)), which resulted in a detection rate of about 40%, thus suggesting that the disk winds have a wide opening angle. A lower limit on the launching radius can be derived assuming that the wind is launched at its escape radius $R_{\mathrm{min}} = 2\,G\,M_{\rm {BH}}/v^2$. We note that by adopting this value for $R_{\rm w}$, we obtain the most conservative estimate of the mass outflow rate and energetics (see (cite: Gofford2015; Tombesi2012)). Since the main uncertainty in the $R_{\rm min}$ derivation is the black hole mass of NED01, we decided to normalise the mass outflow rate by the Eddington rate, $$\begin{equation}
\label{eq:Edd_rate}
 \dot M_{Edd}= \frac{4~\pi~G~m_{\mathrm p}~M_{\rm {BH}}}{\sigma_{\rm {T}}~\eta~c},
\end{equation}$$ where $\sigma_{\rm {T}}$ is the Thomson cross section and $\eta=0.1$ is the accretion efficiency. Thus, combining Eq. [\[eq:xray_ofrate\]](#eq:xray_ofrate) and Eq. [\[eq:Edd_rate\]](#eq:Edd_rate), and substituting for $R_{\rm{min}}$, we obtain $$\begin{equation}
\frac{\dot M_{out}^{X-ray}}{\dot M_{Edd}}=2\frac{\Omega}{4\pi}\mu \,N_{\rm {H}}\,\sigma_{\rm {T}}\,\eta\,\left(\frac{v_{\rm{out}}}{c}\right)^{-1}.
\end{equation}$$ The X-ray wind kinetic power ($\dot E^{X-ray}_{\rm {kin}}=1/2 \dot M_{out}\, v_{\rm{out}}^2$) normalised by the Eddington luminosity ($L_{\rm{Edd}}=\eta\, \dot M_{\rm {Edd}} \,c^2$) is $$\begin{equation}
\frac{\dot E^{X-ray}_{kin}}{L_{Edd}}=\frac{\Omega}{4\pi}\, \mu\, N_{\rm {H}}\,\sigma_{\rm {T}}\frac{v_{\rm{out}}}{c}.
\end{equation}$$ For the nuclear wind detected by *Swift*, we measure $N_{\mbox{\scriptsize H}}=1.3\ensuremath{^{+1.7}_{-0.9}}\times 10^{23}$ cm$^{-2}$ and $v_{\rm {out}}/c = -0.12\ensuremath{^{+0.02}_{-0.05}}$. The (*Swift*) mass outflow rate is thus $\dot M_{ out}^{X-ray}/\dot{M}_{\rm Edd}\sim 0.09$ and the wind kinetic power is then $\dot E^{X-ray}_{out} \sim 0.6$% of Eddington. Conversely, for the 2012 *NuSTAR* spectrum we derive $\dot M^{X-ray}_{out}/\dot{M}_{\rm Edd}\sim0.04$ and $\dot E^{X-ray}_{out}\sim 1$% of Eddington. Considering a BH mass of $\sim 10^8 M_\odot$, as estimated by (cite: Alonso13) in NED01, these values correspond to $\dot E_{out}^{\rm Swift}\sim 8\times 10^{43}$ erg s$^{-1}$ and $\dot E_{out}^{\rm Nustar}\sim 1.3\times 10^{44}$ erg s$^{-1}$, where the higher value measured in the 2012 observation is driven by the higher velocity of the wind. We note that these estimates are clearly affected by large errors; only considering the 90% errors on the column density of the wind, we derive that the kinetic power of the X-ray wind detected in the *Swift* observations could range between $2.5\times 10^{43}$ erg s$^{-1}$ and $1.7\times 10^{44}$ erg s$^{-1}$, while for the *NuSTAR* wind the range is $0.6-2\times 10^{44}$ erg s$^{-1}$. The momentum rate of the X-ray wind is $\dot p_{out}^{X-ray}\sim (4\pm2)\times 10^{34}$ g cm s$^{-2}$ from *NuSTAR*, which is consistent with the value obtained from the *Swift* data, although the latter has a larger uncertainty.

+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
| Model Component   | Parameter                                                            | *Swift*                              | 2012 *NuSTAR*  | 2021*XMM* & *NuSTAR*  |
+:==================+:=====================================================================+:====================================:+:==============:+:=====================:+
| Primary Power law | $\Gamma$                                                             | $1.80\pm 0.06$                       | 1.80$^t$       | $1.75\pm0.06$         |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | Norm.$^{\dag}$                                                       | $1.9\pm0.2$                          | $3.7\pm0.5$    | $0.33\pm0.03$         |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
| Neutral absorber  | $N_\mathrm{H}(\times 10^{22}$ cm$^{-2}$)                             | $2.3\pm0.2$                          | $4.8\pm 1.9$   | $2.7\pm0.2$           |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
| Disk wind         | $N_\mathrm{H}$($\times 10^{23}$ cm$^{-2}$)                           | $1.3\ensuremath{^{+1.7}_{-0.9}}$     | $1.1\pm0.6$    | \-                    |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | $log \xi_1$                                                          | $3.4\pm 0.5$                         | $3.4^{t}$      | \-                    |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | $v_\mathrm{out}/c$                                                   | $-0.12\ensuremath{^{+0.02}_{-0.05}}$ | $-0.23\pm0.02$ | \-                    |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | $\chi^2/\nu$                                                         | $323.9/288$                                           | $257.5/205$           |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | $F_{(2-10)\,\mathrm {keV}}\times 10^{-12}$ (erg cm$^{-2}$ s$^{-1}$)  | 6.4                                  | $9.9$          | 1.5                   |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | $F_{(10-30)\,\mathrm {keV}}\times 10^{-11}$ (erg cm$^{-2}$ s$^{-1}$) | \-                                   | $1.3$          | 0.3                   |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   | $L_{(2-10)\,\mathrm {keV}}\times 10^{42}$ (erg s$^{-1}$)             | 5.1                                  | $9.0$          | 1.2                   |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+
|                   |                                                                      |                                      |                |                       |
+-------------------+----------------------------------------------------------------------+--------------------------------------+----------------+-----------------------+

*Notes:* $^{\dag}$: The normalisation units are $10^{-3}$ ph keV$^{-1}$ cm$^{-2}$. $^{t}$: Denotes that the parameter was tied.

# Discussion

Since the large amount of energy released by AGN and the associated feedback processes affect the ISM on different physical scales, studying outflows in different ISM phases using multi-wavelength data is the only way to probe the AGN–ISM interplay. A multi-phase analysis is the only method that leads to a complete description of the outflows, allowing us to determine their physical parameters (e.g. their full extent and mass) and to obtain an overview of their driving mechanisms to test their theoretical models. The goal of our ALMA CO(1-0) observations was to investigate the presence of a high-velocity molecular outflow in NED01, which is expected to be experiencing strong AGN feedback since it hosts a powerful X-ray wind. At first look, the ALMA CO(1-0) data did not show any evidence for a massive powerful molecular outflow in this source, and instead presented clear evidence for CO(1-0) rotating disks in both NED01 and its companion galaxy NED02. Our BBarolo modelling confirmed that the bulk of the CO(1-0) emissions from the two galaxies can be fitted using a rotating disk model. We then focused on studying the presence of any CO(1-0) residual emission, not accounted for by the disk modelling, following a methodology commonly adopted in the literature (e.g. (cite: 2019Sirressi; 2021BewketuBelete; 2022RamosAlmeida)).

By subtracting the best-fit BBarolo disk model from the ALMA datacube, we detected CO(1-0) residual emission at the $\sim10$% level around NED01, for all three models constructed by applying BBarolo on regions of different sizes (see also Appendix [12](#sec:appendix)). The fit that leaves the least residuals in NED01, with flux corresponding to $\sim8$ % of its total CO(1-0) emission, is the one described in Sect. [5.1](#sec:NED01_BBarolo) and performed on the *Big region*. The subtraction of this fit leaves mainly blueshifted residual emission within $v\in (-400, -100)$ km s$^{-1}$, whose contours are enclosed in a squared box of 3 kpc in size, which is rather compact compared to the main rotating disk that has a diameter of $\sim10$ kpc. Quite strikingly, blueshifted residual CO(1-0) emission was detected consistently in the data after subtracting all three BBarolo best-fit disk models, with similar morphology and spectral properties, and so we believe it traces structures that may be truly disconnected from the main disk and whose origin is worth exploring further. On the other hand, redshifted residual emission was not detected in the fit performed on the *Big region* around NED01, although it was detected in the other two fits performed on smaller regions, which did not properly account for the extended redshifted CO(1-0) components (labelled B and C in the central panel of Fig [4](#fig:NED01_mom_maps)).

For NED02, after subtracting the best-fit BBarolo disk model from the ALMA data, we also detected residual CO(1-0) emission, corresponding to $\sim7$ % of the total line flux from this galaxy. Similar to NED01, the residuals are blueshifted with respect to the CO(1-0) systemic velocity and have a compact morphology, being enclosed within the central 3 kpc of the source. In the following, we discuss possible interpretations for the blueshifted CO(1-0) residual emission detected in the IRAS 05054+1718 galaxy pair.

### Hypothesis I: Molecular outflows

The first hypothesis we consider is that the CO(1-0) residuals trace a molecular outflow, which was the scenario we aimed to test with the acquisition of these new ALMA data.

Under the hypothesis that the CO(1-0) residual emission in NED01 traces a molecular outflow, we used the best-fit Gaussian parameters reported in Table [3](#tab:bigres1_fit) to estimate its energetics, by summing the contribution from the two blueshifted CO(1-0) spectral components. For each spectral feature, we set $v_{out}$ equal to the Gaussian central velocity, the outflow radius $R$ as the projected distance from the disk centre (see Table [3](#tab:bigres1_fit) and [4](#tab:ned02_res) for NED01 and NED02, respectively), and compute the dynamical timescale of the outflow as $\tau_{dyn}^{mol}=R/v_{out}$. Using the molecular gas mass inferred from the CO(1-0) luminosity reported in Table [3](#tab:bigres1_fit), we computed the mass-loss rate ($\dot{M}^{mol}_{out}=M^{mol}_{out}/\tau_{dyn}$), momentum rate ($v\dot{M}^{mol}_{out}$) and kinetic power ($0.5\dot{M}^{mol}_{out}v^2$) for each of the two CO residual spectral features, and report these numbers in Table [\[tab:ned01_ned02_energetics\]](#tab:ned01_ned02_energetics). A similar exercise was performed for NED02, with results listed in Table [\[tab:ned01_ned02_energetics\]](#tab:ned01_ned02_energetics).

+----------------------------------------------------------------------------------------------+
| IRAS 05054+1718 NED01                                                                        |
+:=======================================================+:=========:+:===========:+:=========:+
| Parameter                                              | Comp. 1   | Comp. 2     | Total     |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\tau^{mol}_{dyn}$ \[Myr\]                             | 3.0 (0.8) | 10.0 (1.4)  |           |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\dot{M}^{mol}_{out}$$^{\dag}$ \[$M_{\odot}~yr^{-1}$\] | 16 (12)   | 3 (2)       | 19 (14)   |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\dot{p}^{mol}_{out}$ \[$10^{34}g~cm~s^{-2}$\]         | 2.4 (2.2) | 0.3 (0.2)   | 2.7 (2.4) |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\dot{E}^{mol}_{out}$ \[$10^{41}~erg~s^{-1}$\]         | 3 (2)     | 0.22 (0.15) | 3.2 (2.2) |
+--------------------------------------------------------+-----------+-------------+-----------+
| IRAS 05054+1718 NED02                                                                        |
+--------------------------------------------------------+-----------+-------------+-----------+
| Parameter                                              | Comp. 1   | Comp. 2     | Total     |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\tau^{mol}_{dyn}$ \[Myr\]                             | 4.7 (1.3) | 21 (4)      |           |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\dot{M}^{mol}_{out}$$^{\dag}$ \[$M_{\odot}~yr^{-1}$\] | 17 (15)   | 3 (2)       | 20 (16)   |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\dot{p}^{mol}_{out}$ \[$10^{34}~g~cm~s^{-2}$\]        | 1.8 (1.6) | 0.13 (0.09) | 2.0 (1.7) |
+--------------------------------------------------------+-----------+-------------+-----------+
| $\dot{E}^{mol}_{out}$ \[$10^{41}~erg~s^{-1}$\]         | 1.5 (1.3) | 0.05 (0.04) | 1.6 (1.3) |
+--------------------------------------------------------+-----------+-------------+-----------+

*Notes:* $^{\dag}$ Computed assuming $\alpha_{\rm CO} = 2.1 \pm 1.2$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: 2018Cicone2).

The total properties of the putative outflow in NED01 were computed by summing the contribution of all the residual components obtaining a total mass-loss rate of $\dot M^{mol}_{out}=\sum_{i} M^{mol}_{out,i}=19\pm14$ M$_{\odot}$ yr$^{-1}$ (including a systematic uncertainty on the $\alpha_{\rm CO}$ factor), a total momentum rate of $\dot p^{mol}_{out}=\sum_{i} v_i\dot{M}^{mol}_{out,i}=(2.7\pm2.4)\times10^{34}$ g cm s$^{-1}$, and a total kinetic power of $\dot E^{mol}_{out}=\sum_{i} 0.5\dot{M}^{mol}_{out,i}v_i^2=(3.2\pm2.2)\times10^{41}$ erg s$^{-1}$. For NED02, we get a putative outflow mass-loss rate of $20\pm16$ M$_{\odot}$ yr$^{-1}$. However, a molecular outflow, if present, cannot be brighter than the residuals, implying all computed values as upper limits on the outflow energetics parameters.

In a blast-wave AGN feedback scenario (cite: 2012Faucher-Giguere; 1999Fabian), the energetics of the molecular outflow detected on galactic scales should be compared with that of the X-ray disk wind, since the former is theoretically expected to be triggered by the latter. According to (cite: 2015Ballo), and to the new analysis based on the 2012 *NuSTAR* data (see Sect. 6), the X-ray wind in NED01 has a velocity of $v\sim0.2c$ with corresponding X-ray wind outflow and momentum rates values, although highly uncertain,[^8] of $\sim0.13$ M$_{\odot}~yr^{-1}$ and $\sim 4 \times 10^{34}$ g cm s$^{-1}$, respectively. The kinetic power is estimated to range between 2.5$\times 10^{43}$ erg s$^{-1}$ and 1.7$\times 10^{44}$ erg s$^{-1}$ and $0.6-2\times 10^{43}$ erg s$^{-1}$ for the *Swift*  and the *NuSTAR*  winds, respectively. This is two orders of magnitude higher than that inferred for the putative molecular outflow in this source. The corresponding ratio of the momentum rates of the molecular and X-ray winds is $\dot{p}^{mol}_{out}/\dot{p}^{X-ray}_{out}\sim0.67$, consistent with unity within the large uncertainties. Even in the (unlikely) scenario that all of the CO(1-0) residual emission detected in NED01 can be ascribed to a molecular outflow, there is no evidence for a boost in the momentum rate of the molecular outflow with respect to the X-ray wind, which would be an expectation of a ‘classic’ energy-driven outflow model (cite: 2012Faucher-Giguere).

We can robustly conclude that the current data do not require any momentum rate boost for the large-scale outflow.

![](Figures/smith_plot2.pdf)

The position of NED01 in the outflow momentum rate ratio versus velocity diagram proposed by (cite: 2015Feruglio; 2015Tombesi) is shown in brown in Fig. [16](#fig:smithplot), compared to other galaxies studied in the literature. One of these sources is the Seyfert 2 galaxy MCG-03-58-007, whose ALMA CO(1-0) observations were analysed by (cite: 2019Sirressi). With a similar methodology to this work, based on the subtraction from ALMA CO(1-0) data of a rotating disk model obtained with the BBarolo code, (cite: 2019Sirressi) detected compact CO(1-0) residual emission within $\sim2$ kpc of the AGN, presenting two symmetric components at blueshifted velocities and one at redshifted velocities ($v= \pm170$ km s$^{-1}$). These authors cautiously interpreted such CO(1-0) residuals as possible evidence for either a compact molecular outflow or a kiloparsec-scale rotating structure disconnected from the main disk. In the outflow scenario, the momentum rate of the putative molecular outflow in MCG-03-58-007 would be $\dot{p}^{mol}_{out}\sim6\times10^{34}$ g cm s$^{-2}$, corresponding to 40% of the momentum rate of the X-ray UFO, consistent with our new findings on IRAS 05054+1718 NED01.

Overall, Fig. [16](#fig:smithplot) shows that the interplay between nuclear disk winds and large-scale molecular outflows is more complex than predicted by theoretical blast-wave feedback models, and the data suggest a range of values for the outflow momentum rates on small and large scales.

In order to directly compare observational values with predictions of the blast-wave model, Fig. [17](#fig:marascoplot) shows the ratio of the outflow rate to the X-ray UFO momentum rate, and the ratio of the estimated values of the related energy- and momentum-driven regimes. Following (cite: 2020Marasco; 2021Tozzi), we extended this analysis including our targets and some sources from (cite: 2019Mizumoto). Since (cite: 2020Marasco; 2021Tozzi) adopted $\alpha_{\rm CO} = 0.8 \pm 1.2$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: 1998Downes; 2013Carilli; 2013Bolatto) in their analysis, we re-derived the energetics applying this conversion factor, obtaining $\dot{p}^{mol}_{out}/\dot{p}^{X-ray}_{out}\sim0.3$. Overall, the energetics of the outflows appears to be consistent in most of the targets (15 out of 17 objects) with either a momentum-driven (12) or an energy-driven (3) scenario. There are only two cases where the outflow energetics seems completely unrelated to the nuclear source. The momentum ratio of the quasar SDSS J1353+1138 is $\sim$100 times smaller than the momentum-driven prediction. According to (cite: 2021Tozzi), this low value may be associated with a massive molecular outflow not considered in that work or to a high variability among the quasar activity. The other exception is the Seyfert 1 galaxy IRAS 17020+4544 studied by (cite: 2015Longinotti; 2018Longinotti), with its extremely high molecular outflow momentum rate, possibly related to an uncertain estimate of $\dot p^{mol}_{out}$ or again to the high AGN variability. Overall, according to (cite: 2020Marasco), Fig. [17](#fig:marascoplot) shows that the blast-wave scenario either in a momentum- or an energy-driven regime appears to describe the interplay between nuclear winds and large-scale outflows, although the majority of measurements suggests the absence of a significant momentum boost.

![](Figures/marasco_plot.pdf)

Many of the local galaxies with a molecular outflow detection shown in Fig. [16](#fig:smithplot) (but also see the review by (cite: 2020Veilleux)) are intensely star forming, and so their large-scale outflows may be driven by star formation. In comparison to the extreme ULIRGs that have been the focus of previous investigations, the SFRs of both members of the IRAS 05054+1718 galaxy pair are rather modest. From its total CO(1-0) line luminosity (see Table [2](#tab:mol_masses)), by assuming an $L^{\prime}_{CO(1-0)}$–SFR relation typical of local star-forming galaxies (cite: 2017Cicone), we estimate a SFR$_{NED01}$($L^{\prime}_{CO}$)=$2.5\pm0.3$ M$_{\odot}$ yr$^{-1}$ for NED01, which is lower than the range reported in the literature obtained from the IR luminosity and SED modelling (SFR=5-10 M$_{\odot}$ yr$^{-1}$; see Sect. [2](#sec:targets)), possibly because of AGN contamination affecting photometric measurements of this source. For NED02, using the same procedure, we estimate from the total CO(1-0) luminosity SFR$_{NED02}$($L^{\prime}_{CO}$) = $3.6\pm0.5$ M$_{\odot}$ yr$^{-1}$, which is also lower than the values reported in the literature based on IR luminosity. Since the presence of an AGN has not been confirmed in this source, the discrepancy could be due to a particularly high star formation efficiency in this source (SFE=SFR/M$_{mol}$) or to the presence of additional molecular gas undetected by our ALMA CO(1-0) line observations. As shown in Fig. [1](#fig:source), the CO(1-0) emission from NED02 is rather compact compared to its optical extent. According to (cite: 2005Veilleux), assuming a maximum coupling efficiency of $\sim10\%$, star formation feedback in galaxies with the SFRs inferred for NED01 and NED02 would drive weak outflows, with mass loss rates of $\dot{M}_{out}<1$ M$_{\odot}$ yr$^{-1}$, which would be undetectable in our data and as not consistent with the blueshifted CO residuals investigated here.

### Hypothesis II: Compact rotating structures

An alternative hypothesis that can account for the residual emission is the presence of a compact structure, similar to the circumnuclear disks (CNDs) detected in some local AGNs (cite: 2014Garcia-Burillo; 2019Combes), whose rotation departs from the rotating molecular disk modelled by BBarolo. Although this was a viable hypothesis for the CO(1-0) residual components detected in MCG-03-58-007 by (cite: 2019Sirressi), it seems an unlikely scenario in the case of the galaxy pair IRAS 05054+1718 studied in this work. The CO(1-0) residuals in both NED01 and NED02 have a complex, asymmetrical, spectral profile, with multiple peaks at blueshifted velocities, and lack a reliable redshifted counterpart.

### Hypothesis III: ISM disk asymmetries

Finally, the blueshifted CO residuals detected in both NED01 and NED02 could be due to other types of asymmetries of the molecular disks that are not properly captured by the BBarolo model. The negative residuals seen around the systemic velocity in both sources would also be consistent with this hypothesis. As discussed by (cite: BAROLO), although BBarolo manages quite well minor asymmetries such as the disk warp in NGC 5055, the code always favours the model that generates the lowest residuals, which necessarily results in an average rotation curve that may follow one side of the disk more closely than the other. In the case of our target, the ongoing gravitational interaction between the two members of the pair could have already slightly perturbed their ISM, hence producing perturbations of the molecular disk that are not properly captured by BBarolo, causing the residual emission. We note that in this case, the residuals obtained after subtracting the best-fit BBarolo model may not correspond directly to the perturbed components of the ISM, as it could be that the model is forcing the fit to adapt better to the perturbations than to the rest of the (unperturbed) disk, hence producing artificial residuals with spectral and spatial characteristics that are unrelated to the underlying physical process. Therefore, this third scenario can only be tested using higher resolution data.

# Summary and conclusions

In this study we presented new high-sensitivity ALMA CO(1-0) observations of the interacting galaxy pair IRAS 05054+1718 (projected distance between the components $\sim29.6''\sim11$ kpc).

We investigated the presence of a galactic-scale molecular outflow in the main target NED01 ($z=0.0178\pm0.0004$, this work) and its possible relation with the powerful X-ray wind detected in its nucleus (cite: 2015Ballo).

Given its moderate SFR (cite: 2014Delooze; 2015Pereira), NED01 is a suitable object to study AGN feedback mechanisms and the blast-wave scenario, usually tested in environments that are extremely bright in the IR and with high SFRs where the AGN contribution is hard to isolate from the stellar contribution. The companion NED02 ($z=0.016812\pm 0.000003$, this work) was included in the field of view of our compact-configuration ALMA data. This source is a LIRG, classified as composite by (cite: 2015Pereira), but there is no clear evidence of the presence of an AGN (cite: 2012Alonso-Herrero).

We investigated the distribution and kinematics of the CO(1-0) emission at a spatial resolution of $\sim1$ kpc, which appears dominated by the rotating molecular gas disk for both targets. We modelled the disk using 3D-BAROLO and studied the residual emission to identify structures deviating from the rotation. We detected residual emission (S/N $\ge15$) at $v  \in  (-400,-100)$ km s$^{-1}$ corresponding to the 8% of its total CO(1-0) emission in the main target NED01, characterised by a compact morphology and extending within 3 kpc of the galaxy centre. We also detected a similar blueshifted residual CO(1-0) emission ($\sim7$ % of the total CO(1-0) flux from this galaxy) in the companion NED02. A molecular outflow in NED01, if present, cannot be brighter than this residual, implying an upper limit on its mass-loss rate of $19\pm14$ M$_{\odot}$ yr$^{-1}$, on its momentum rate of $(2.7\pm2.4)\times10^{34}$ g cm s$^{-1}$, and on its kinetic power of $(3.2\pm2.2)\times10^{41}$ erg s$^{-1}$. For NED02, we obtain a putative outflow mass-loss rate of $20\pm16$ M$_{\odot}$ yr$^{-1}$.

Regarding the X-ray UFO, the analysis performed on the 2012 *NuSTAR* data confirmed the results already found by (cite: 2015Ballo) regarding the presence of a highly ionised and high-velocity outflowing disk wind in the NED01 nucleus. Although no disk wind features have been detected in the more recent *XMM-Newton* and *NuSTAR* data, the upper limits estimated for the column density of a putative ionised absorber outflowing are only marginally below the 90% lower value of $N_{\rm H}$ estimated in the past observations. This suggests that a small change in the opacity of the wind can explain a non-detection of the wind at the low-flux state during 2021. This, combined with the factor of 4 lower intrinsic flux of the 2021 X-ray observations, can account for the non-detection in the most recent data.

As for the companion NED02, we derive a faint soft (0.5-2 keV) flux of the order of $\sim$2$\times
10^{-14}$ erg cm$^{-2}$ s$^{-1}$, corresponding to $L_\mathrm {(0.5-2) keV}\sim 2\times 10^{40}$ erg s$^{-1}$. According to the $\rm L_X-SFR$ relations derived from several surveys of LIRGs and ULIRGs (see e.g. (cite: 2017Cicone)) this would correspond to a $\rm SFR \sim 7\,M_\odot/$ yr. At higher energies, only X-ray observations with the high spatial resolution, such as that offered by the *Chandra* observatory, will allow us to properly separate the X-ray emission of NED02 from the brighter companion NED01 and reach a definitive answer on the possible presence of a weak and/or obscured AGN in NED02.

We tested the AGN feedback blast-wave scenario in NED01 by comparing the energetics of the UFO and the putative molecular outflow. The results we obtained are not consistent with an energy-driven scenario since there is no evidence for a boost in the momentum rate of the molecular outflow with respect to the X-ray wind.

We also considered the hypothesis of an outflow triggered by star formation activity. The SFR of NED01, equal to $\rm SFR_{NED01}(L'_{CO})=2.5\pm$0.3 M$_\odot$ s$^{-1}$, refined using its CO(1-0) luminosity and a local tight $\rm L_{CO}-SFR$ relation, is too low to account for a putative star formation-driven molecular outflow.

Since the presence of an AGN has not been confirmed in the companion NED02, the hypothesis of AGN feedback cannot apply to this case. Following the hypothesis of a star formation-driven outflow, we estimated CO(1-0) luminosity in NED02 as $\rm SFR_{NED01}(L'_{CO})=3.6\pm$0.5 M$_\odot$ s$^{-1}$, lower than the values reported in the literature based on IR luminosity. As for the main target, the estimated SFR is too low to account for the observed residual emission.

Because of the ambiguous interpretation of the CO residual emission obtained after subtracting the best-fit disks modelled by BBarolo, the residuals observed in NED01 and NED02 may have a different explanation from that of a molecular outflow. We considered the alternative hypothesis that the detected residual CO emission is due to an additional compact structure similar to a circumnuclear disk whose rotation cannot be associated with the central molecular disk. This hypothesis seems unlikely since the residuals detected in NED01 and NED02 show a complex asymmetrical profile without a redshifted counterpart. We also considered a third hypothesis, according to which the residuals may be due to disk asymmetries that are not properly captured by the BBarolo model. In this case the position and spectral properties of such residuals may not be highly informative of the underlying physical process responsible for the disk perturbations, and only higher resolution data could reveal their origin.

Our study, together with other recent works in the literature (e.g. (cite: 2019Smith), (cite: 2019Sirressi), (cite: 2020Veilleux)), has increased the sample of AGN hosting an ultra-fast X-ray wind with observational constraints on the presence and properties of a molecular outflow, on which it is possible to test the predictions of the AGN-driven feedback scenario. The increased statistics of observations appears to complicate the scenario of AGN-driven feedback mechanisms more and more, drawing a much more complex picture than expected. Furthermore, the high sensitivity to extended structures enabled by the use of a compact array configuration has revealed important information on the close environment of the target galaxy. These data have indeed allowed us to study NED01 simultaneously with its nearby companion NED02, and to investigate the low surface brightness components of their respective molecular disks, hence to compare their molecular ISM morphologies. Our understanding of diffuse low surface brightness and extended molecular gas components due to feedback processes and gravitational interactions will be transformed by a facility such as the Atacama Large Aperture Submillimetre Telescope (AtLAST)[^9].

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2016.1.00694.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 951815 (AtLAST). FB acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (Grant agreement No. 851435). CV acknowledges funding from PRIN MIUR 2017PH3WAT (‘Black hole winds and the baryon life cycle of galaxies’). CC, PS, VB, CV, RDC, LB and MD acknowledge financial contributions from Bando Ricerca Fondamentale INAF 2022 Large Grant “Dual and binary supermassive black holes in the multi-messenger era: from galaxy mergers to gravitational waves” and from the agreement ASI-INAF n.2017-14-H.O. VB acknowledges financial support through the NASA grant 80NSSC22K0220. VB and JR acknowledge support from NASA grant 80NSSC22K0474.

90 natexlab

(ref: 2012Aalto) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, A&A, 537, A44

(ref: 2013Alonso-Herrero) Alonso-Herrero, A., Pereira-Santaella, M., Rieke, G. H., et al. 2013a, ApJ, 765, 78

(ref: Alonso13) Alonso-Herrero, A., Pereira-Santaella, M., Rieke, G. H., et al. 2013b, ApJ, 765, 78

(ref: 2012Alonso-Herrero) Alonso-Herrero, A., Pereira-Santaella, M., Rieke, G. H., & Rigopoulou, D. 2012, ApJ, 744, 2

(ref: 2014Andre) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 27

(ref: xspecref) Arnaud, K. A. 1996, in Astronomical Society of the Pacific Conference Series, Vol. 101, Astronomical Data Analysis Software and Systems V, ed. G. H. Jacoby & J. Barnes, 17

(ref: 2015Ballo) Ballo, L., Severgnini, P., Braito, V., et al. 2015, A&A, 581, A87

(ref: Baumgartner2013) Baumgartner, W. H., Tueller, J., Markwardt, C. B., et al. 2013, ApJS, 207, 19

(ref: 2021BewketuBelete) Bewketu Belete, A., Andreani, P., Fernández-Ontiveros, J. A., et al. 2021, A&A, 654, A24

(ref: 2008Bigiel) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846

(ref: 2019Bischetti) Bischetti, M., Piconcelli, E., Feruglio, C., et al. 2019, A&A, 628, A118

(ref: 2013Bolatto) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: 2012Bower) Bower, R. G., Benson, A. J., & Crain, R. A. 2012, MNRAS, 422, 2816

(ref: Braito2022) Braito, V., Reeves, J. N., Matzeu, G., et al. 2022, ApJ, 926, 219

(ref: 2018Braito) Braito, V., Reeves, J. N., Matzeu, G. A., et al. 2018, MNRAS, 479, 3592

(ref: Braito2021) Braito, V., Reeves, J. N., Severgnini, P., et al. 2021, MNRAS, 500, 291

(ref: 2013Carilli) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Panstar) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv e-prints, arXiv:1612.05560

(ref: Chartas2016) Chartas, G., Cappi, M., Hamann, F., et al. 2016, ApJ, 824, 53

(ref: 2020Chartas) Chartas, G., Davidson, E., Brusa, M., et al. 2020, MNRAS, 496, 598

(ref: 2009Chartas) Chartas, G., Saez, C., Brandt, W. N., Giustini, M., & Garmire, G. P. 2009, ApJ, 706, 644

(ref: 2017Cicone) Cicone, C., Bothwell, M., Wagg, J., et al. 2017, A&A, 604, A53

(ref: 2012Cicone) Cicone, C., Feruglio, C., Maiolino, R., et al. 2012, A&A, 543, A99

(ref: 2020Cicone) Cicone, C., Maiolino, R., Aalto, S., Muller, S., & Feruglio, C. 2020, A&A, 633, A163

(ref: 2014Cicone) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: 2018Cicone2) Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018, ApJ, 863, 143

(ref: 2019Combes) Combes, F., Garcı́a-Burillo, S., Audibert, A., et al. 2019, A&A, 623, A79

(ref: 2014Delooze) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: BAROLO) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: 1998Downes) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: 1999Fabian) Fabian, A. C. 1999, MNRAS, 308, L39

(ref: 2012Faucher-Giguere) Faucher-Giguère, C.-A. & Quataert, E. 2012, MNRAS, 425, 605

(ref: 2017Feruglio) Feruglio, C., Ferrara, A., Bischetti, M., et al. 2017, A&A, 608, A30

(ref: 2015Feruglio) Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99

(ref: 2010Feruglio) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: 2010Fisher) Fischer, J., Sturm, E., González-Alfonso, E., et al. 2010, A&A, 518, L41

(ref: 2019Fleutsch) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: 2014Garcia-Burillo) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: Gehrels2004) Gehrels, N., Chincarini, G., Giommi, P., et al. 2004, ApJ, 611, 1005

(ref: Gofford2015) Gofford, J., Reeves, J. N., McLaughlin, D. E., et al. 2015, MNRAS, 451, 4169

(ref: Gofford2013) Gofford, J., Reeves, J. N., Tombesi, F., et al. 2013, MNRAS, 430, 60

(ref: 2017Gonzalez-Alfonso) González-Alfonso, E., Fischer, J., Spoon, H. W. W., et al. 2017, ApJ, 836, 11

(ref: Harrison2013) Harrison, F. A., Craig, W. W., Christensen, F. E., et al. 2013, ApJ, 770, 103

(ref: nhHI4PICollaboration) HI4PI Collaboration, Ben Bekhti, N., Flöer, L., et al. 2016, A&A, 594, A116

(ref: 2014Hopkins) Hopkins, P. F., Kereš, D., Oñorbe, J., et al. 2014, MNRAS, 445, 581

(ref: 2010Howell) Howell, J. H., Armus, L., Mazzarella, J. M., et al. 2010, ApJ, 715, 572

(ref: 2012Huchra) Huchra, J. P., Macri, L. M., Masters, K. L., et al. 2012, ApJS, 199, 26

(ref: xstar) Kallman, T. R., Palmeri, P., Bautista, M. A., Mendoza, C., & Krolik, J. H. 2004, ApJS, 155, 675

(ref: 2010King) King, A. R. 2010, MNRAS, 402, 1516

(ref: Krongold2007) Krongold, Y., Nicastro, F., Elvis, M., et al. 2007, ApJ, 659, 1022

(ref: 2010Lada) Lada, C. J., Lombardi, M., & Alves, J. F. 2010, ApJ, 724, 687

(ref: 2008Leroy) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: 2015Longinotti) Longinotti, A. L., Krongold, Y., Guainazzi, M., et al. 2015, ApJL, 813, L39

(ref: 2018Longinotti) Longinotti, A. L., Vega, O., Krongold, Y., et al. 2018, ApJL, 867, L11

(ref: 2018Luminari) Luminari, A., Piconcelli, E., Tombesi, F., et al. 2018, A&A, 619, A149

(ref: 2020Lutz) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134

(ref: 2014Makarov) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13

(ref: 2020Marasco) Marasco, A., Cresci, G., Nardini, E., et al. 2020, A&A, 644, A15

(ref: Matzeu2017) Matzeu, G. A., Reeves, J. N., Braito, V., et al. 2017, MNRAS, 472, L15

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2019Mizumoto) Mizumoto, M., Izumi, T., & Kohno, K. 2019, ApJ, 871, 156

(ref: Nardini2015) Nardini, E., Reeves, J. N., Gofford, J., et al. 2015, Science, 347, 860

(ref: 2007Omont) Omont, A. 2007, Reports on Progress in Physics, 70, 1099

(ref: Parker2018) Parker, M. L., Matzeu, G. A., Guainazzi, M., et al. 2018, MNRAS, 480, 2365

(ref: 2015Pereira) Pereira-Santaella, M., Alonso-Herrero, A., Colina, L., et al. 2015, A&A, 577, A78

(ref: 2016PlanckCollaboration) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13

(ref: 2022RamosAlmeida) Ramos Almeida, C., Bischetti, M., Garcı́a-Burillo, S., et al. 2022, A&A, 658, A155

(ref: ReevesBraito2019) Reeves, J. N. & Braito, V. 2019, ApJ, 884, 80

(ref: Reeves2018) Reeves, J. N., Braito, V., Nardini, E., et al. 2018, ApJ, 867, 38

(ref: 2003Reeves) Reeves, J. N., O’Brien, P. T., & Ward, M. J. 2003, ApJL, 593, L65

(ref: Ricci2017) Ricci, C., Bauer, F. E., Treister, E., et al. 2017, MNRAS, 468, 1273

(ref: 2017Rupke) Rupke, D. S. N., Gültekin, K., & Veilleux, S. 2017, ApJ, 850, 40

(ref: 2003Sanders) Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607

(ref: 1998Silk-Rees) Silk, J. & Rees, M. J. 1998, A&A, 331, L1

(ref: 2019Sirressi) Sirressi, M., Cicone, C., Severgnini, P., et al. 2019, MNRAS, 489, 1927

(ref: 2019Smith) Smith, R. N., Tombesi, F., Veilleux, S., Lohfink, A. M., & Luminari, A. 2019, ApJ, 887, 69

(ref: 1997Solomon) Solomon, P. M. 1997, IAU Symposium, 170, 289

(ref: 2013Stierwalt) Stierwalt, S., Armus, L., Surace, J. A., et al. 2013, ApJS, 206, 1

(ref: 2011Sturm) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: Tombesi2012) Tombesi, F., Cappi, M., Reeves, J. N., & Braito, V. 2012, MNRAS, 422, L1

(ref: 2010Tombesi) Tombesi, F., Cappi, M., Reeves, J. N., et al. 2010, A&A, 521, A57

(ref: 2015Tombesi) Tombesi, F., Meléndez, M., Veilleux, S., et al. 2015, Nature, 519, 436

(ref: 2017Tombesi) Tombesi, F., Veilleux, S., Meléndez, M., et al. 2017, ApJ, 850, 151

(ref: 2021Tozzi) Tozzi, G., Cresci, G., Marasco, A., et al. 2021, A&A, 648, A99

(ref: 2017Veilleux) Veilleux, S., Bolatto, A., Tombesi, F., et al. 2017, ApJ, 843, 18

(ref: 2005Veilleux) Veilleux, S., Cecil, G., & Bland-Hawthorn, J. 2005, ARA&A, 43, 769

(ref: 2020Veilleux) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2

(ref: 2013Veilleux) Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27

(ref: Wilms2000) Wilms, J., Allen, A., & McCray, R. 2000, ApJ, 542, 914

(ref: 2002Wong) Wong, T. & Blitz, L. 2002, ApJ, 569, 157

# ALMA map of the 3mm continuum

![image](Figures/cont_pbcor.pdf)\

![image](Figures/cont_over_COlinecont.pdf)\

The ALMA interferometric map of the 3 mm continuum emission from the target is shown in Figure [18](#fig:cont_pbcor). The map was obtained by combining the data (total bandwidth $\Delta\nu=4$ GHz) from the two low-resolution spectral windows centred at 101.190 GHz and 99.387 GHz, which are not contaminated by line emission. A 2D Gaussian fit performed on the PB-corrected map shown in Fig. [18](#fig:cont_pbcor) delivers best-fit peak flux densities of $S_{cont}^{NED01}=0.71\pm0.03$ mJy beam$^{-1}$ and $S_{cont}^{NED02}=2.26\pm0.05$ mJy beam$^{-1}$, indicating that the 3 mm continuum of NED02 is approximately three times brighter than NED01. The fit also provides information about the size and position of the two sources. For NED01, we get a peak centre at RA(ICRS) =05:08:19.713 and Dec(ICRS)=17.21.48.11, with a deconvolved size of $3.0\ensuremath{''}\times2.4\ensuremath{''}$ (PA=84.5 deg). For NED02, the ALMA continuum peaks at RA(ICRS)=05:08:21.211 and Dec(ICRS)=17.22.08.40 (PA=98.4 deg), with a deconvolved size of $3.0\ensuremath{''}\times2.5\ensuremath{''}$. The source-integrated continuum flux obtained through the fit is $S_{3mm}=0.76$ mJy for NED01 and $S_{3mm}=2.4$ mJy for NED02. These results indicate that the 3 mm continuum emission from the targets is only marginally resolved at the resolution of our ALMA data, and much more compact than the CO(1-0) line emission. This is further shown by Figure [19](#fig:cont_overCO), which displays the overlay of the ALMA 3 mm continuum contours on the CO(1-0) line emission map.

# Alternative BBarolo CO(1-0) disk models for NED01

![](Figures/NED01_velmap_region.png)

![](Figures/ned02/ned02_new_chanmaps_local.pdf)

![image](Figures/small/small_now_plot_maps_local.pdf) ![image](Figures/medium/med_now_plot_maps_local.pdf)\

![image](Figures/small/small_res.pdf) ![image](Figures/small/res_small.pdf) ![image](Figures/small/small_res_comp_blue.pdf)\
![image](Figures/medium/res_medium.pdf) ![image](Figures/medium/residui_med.pdf) ![image](Figures/medium/med_res_comp_blue.pdf)\

The *Small* region, shown in Fig. [20](#fig:mommap1), includes only the central molecular disk of NED01 (i.e. component A in Fig. [4](#fig:NED01_mom_maps)), whereas the *Medium* region also embeds the southern extension (component C) of the CO(1-0) emission from NED01. We ran the BBarolo disk modelling for NED01 on these two additional regions, and the results are reported in Fig. [22](#fig:small_medium_mom). For the *Small* region we used three rings, each $2\ensuremath{''}$ in width, while for the *Medium* region we increased the number of rings to seven. The rotation patterns resulting from these two fits does not differ significantly from the fit shown in the main text, which was performed by selecting the *Big region* around NED01. However, these two fits, performed on smaller areas, produce more significant residuals, at both blue- and redshifted velocities, as shown in Fig. [23](#fig:residuals_NED01_small_medium). The best-fit parameters of the CO(1-0) residuals obtained in these two fits performed on the *Small* and *Medium* regions are listed in Table [\[tab:ned01_small_medium_res\]](#tab:ned01_small_medium_res).

Quite strikingly, the spectral profile and morphology of the blueshifted residuals are consistent with those produced by the fit performed on the *Big region*, shown in the main body of the paper shown in Sect. [5.1](#sec:NED01_BBarolo). This is best visualised in the left panel of Fig. [24](#fig:comparison_residuals_NED01), which compares on the same map the blueshifted CO(1-0) residual emission obtained from all three fits performed on NED01. Our analysis focuses on these blueshifted residuals, which are persistent in all three fits. In addition, the two fits reported here produce residuals at receding velocities, east of the NED01 galaxy centre, which were not detected in the *Big region* fit. The right panel of Fig. [24](#fig:comparison_residuals_NED01) compares the morphology of this redshifted CO(1-0) residual emission obtained in the *Small* and *Medium* region fits. The contours from the two fits overlap only partially. These redshifted residuals must be due to the additional extended CO(1-0) features that are not captured in these smaller regions, but were instead well modelled by the fit performed on the *Big region*, where they displayed redshifted velocities on the eastern side of the galaxy consistent with components that follow the same pattern as the main disk rotation.

+-----------------------------------------------------------------------------------------------------------------------------------+
| *Small Region*                                                                                                                    |
+:===========================================================+:===========:+:============:+:===========:+:===========:+:===========:+
| Parameter                                                  | Comp. 1     | Comp. 2      | Comp. 3     | Comp. 4     | Comp. 5     |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $v_{cen}$ \[km s$^{-1}$\]                                  | -248 (3)    | -140 (2)     | 64 (2)      | 114 (2)     | 209 (2)     |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $\sigma_v$ \[km s$^{-1}$\]                                 | 33 (3)      | 21 (2)       | 8.0 (1.7)   | 13 (2)      | 20 (3)      |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $S_{\rm CO(1-0)}dv$ \[Jy km s$^{-1}$\]                     | 1.21 (0.13) | 0.84 (0.10)  | 0.22 (0.06) | 0.39 (0.08) | 0.54 (0.09) |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $L^{\prime}_{\rm CO(1-0)}$ \[10$^7$ K km s$^{-1}$ pc$^2$\] | 1.9 (0.2)   | 1.3 (0.2)    | 0.34 (0.09) | 0.60 (0.12) | 0.83 (0.15) |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $M_{mol}$$^{\dag}$ \[10$^7$ M$_{\odot}$\]                  | 4 (2)       | 3 (2)        | 0.7 (0.4)   | 1.3 (0.8)   | 1.7 (1.0)   |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| R \[kpc\]                                                  | 0.9 (0.2)   | 1.2 (0.2)    | 1.8 (0.2)   | 1.8 (0.2)   | 1.0 (0.2)   |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| *Medium Region*                                                                                                                   |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| Parameter                                                  | Comp. 1     | Comp. 2      | Comp. 3     |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $v_{cen}$ \[km s$^{-1}$\]                                  | -233 (2)    | -146.1 (1.9) | 207 (3)     |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $\sigma_v$ \[km s$^{-1}$\]                                 | 34 (2)      | 20 (2)       | 21 (3)      |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $S_{\rm CO(1-0)}dv$ \[Jy km s$^{-1}$\]                     | 2.26 (0.18) | 1.13 (0.13)  | 0.55 (0.12) |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $L^{\prime}_{\rm CO(1-0)}$ \[10$^7$ K km s$^{-1}$ pc$^2$\] | 3.5 (0.3)   | 1.7 (0.2)    | 0.8 (0.2)   |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| $M_{mol}$$^{\dag}$ \[10$^7$ M$_{\odot}$\]                  | 7 (4)       | 4 (2)        | 1.8 (1.1)   |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+
| R \[kpc\]                                                  | 0.7 (0.2)   | 1.4 (0.2)    | 1.5 (0.2)   |             |             |
+------------------------------------------------------------+-------------+--------------+-------------+-------------+-------------+

$^{\dag}$ Computed assuming $\alpha_{\rm CO} = 2.1 \pm 1.2$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: 2018Cicone2).

![](Figures/residuals.pdf)

[^1]: francesca.bonanomi@univie.ac.at

[^2]: ULIRGs are galaxies that are extremely bright in the infrared, i.e. L$_{\rm IR}\ge10^{12}$ L$_\odot$, (cite: 2003Sanders).

[^3]: CO-based redshift measured in this work, see Sect. [4.1](#sec:z-calc)

[^4]: CO-based redshift, measured in this work, see Sect. [4.1](#sec:z-calc).

[^5]: Frequency of the expected brightest component of the CN(1-0) line group, see also (cite: 2020Cicone).

[^6]: <http://swift.gsfc.nasa.gov/results/bs70mon/>

[^7]: The ionisation parameter is defined as $\xi=L_{\rm {ion}}/nR^2$, where $L_{\rm ion}$ is the ionising luminosity in the 1-1000 Rydberg range, $R$ is the distance to the ionising source, and $n$ is the electron density. The units of $\xi$ are erg cm s$^{-1}$.

[^8]: The errors on the amount of the absorption are of the order of $\sim70$%

[^9]: <https://www.atlast.uio.no>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].fitting.evidence[1]",
  "value": "1-Gaussian and 2-Gaussian spectral line fits",
  "failed_quote": "We modelled it using a single-Gaussian function, whose best-fit parameters are reported in Table [tab:total_co_spectral_fits]."
 },
 {
  "path": "reasoning.limitations_admitted[5].evidence[0]",
  "value": "X-ray wind energetics are affected by large uncertainties (~70% on absorption amount, plus uncertainties on wind opening angle, launching radius, and black hole mass).",
  "failed_quote": "The main uncertainties in Eq. [eq:xray_ofrate] are the wind opening angle ($\\Omega$) and the launch radius $R_{\\rm w}$."
 }
]
```
