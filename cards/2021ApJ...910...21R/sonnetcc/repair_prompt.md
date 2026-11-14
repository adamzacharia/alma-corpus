# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...910...21R\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# A broadband view on microquasar MAXI J$1820+070$ during the 2018 outburst

## Abstract

The microquasar MAXI J$1820+070$ went into outburst from mid-March until mid-July 2018 with several faint rebrightenings afterwards. With a peak flux of approximately 4 Crab in the $20-50$ keV, energy range the source was monitored across the electromagnetic spectrum with detections from radio to hard X-ray frequencies. Using these multi-wavelength observations, we analyzed quasi-simultaneous observations from 12 April, near the peak of the outburst ($\sim 23$ March). Spectral analysis of the hard X-rays found a $kT_e \sim 30$ keV and $\tau \sim 2$ with a `CompTT` model, indicative of an accreting black hole binary in the hard state. The flat/inverted radio spectrum and the accretion disk winds seen at optical wavelengths are also consistent with the hard state. Then we constructed a spectral energy distribution spanning $\sim 12$ orders of magnitude using modelling in `JetSeT`. The model is composed of an irradiated disk with a Compton hump and a leptonic jet with an acceleration region and a synchrotron-dominated cooling region. `JetSeT` finds the spectrum is dominated by jet emission up to approximately $10^{14}$ Hz after which disk and coronal emission dominate. The acceleration region has a magnetic field of $B \sim 1.6 \times 10^4$ G, a cross section of $R \sim 2.8 \times 10^{9}$ cm, and a flat radio spectral shape naturally obtained from the synchroton cooling of the accelerated electrons. The jet luminosity of $> 8 \times 10^{37}$ erg/s ($> 0.15L_{Edd}$) compared to an accretion luminosity of $\sim 6 \times 10^{37}$ erg/s, assuming a distance of 3 kpc. Because these two values are comparable, it is possible the jet is powered predominately via accretion with only a small contribution needed from the Blanford-Znajek mechanism from the reportedly slowly spinning black hole.

# Introduction

The term "microquasar" was first applied to the persistent black hole candidate (BHC) 1E $1740.7-2942$ after detecting radio jets from the known hard X-ray source (cite: 1992Natur.358..215M) that were similar to radio-loud active galactic nuclei (AGNs). Jets were later found to be common features in accreting BH systems in the hard state. Multi-wavelength studies showed correlations between radio and X-ray luminosities (cite: 2003MNRAS.344...60G), indicating a relationship between the emission mechanisms despite a large physical separation between the two. Additionally, this correlation holds also for supermassive BHs in AGN when accounting for mass (cite: 2003MNRAS.345.1057M), thus linking the mechanisms in stellar mass and supermassive BHs. Therefore understanding the jet and X-ray components in microquasars can shed light on AGN.

The low-mass X-ray binary MAXI J$1820+070$ (=ASASSN-18ey) was first detected on 6.59 March 2018[^1] with the All-Sky Automated Survey for SuperNovae (cite: 2014ApJ...788...48S) and was detected $\sim 6$ days later by the *MAXI*/GSC at 11 March 2018 19:48 UTC (cite: 2018ATel11399....1K). With a peak flux of $\sim 4$ Crab in the $20-50$ keV energy band (cite: 2019ApJ...870...92R) and a long decay, the source was a good candidate for numerous observing campaigns across the electromagnetic (EM) spectrum (e.g. (cite: 2019ApJ...879L...4M; 2018ApJ...867L...9T; 2020ApJ...889..142S; 2020NatAs.tmp....2B)) to explore various aspects of the source. Combining observations from various campaigns enables studying the various emission processes together.

Therefore we compiled quasi-simultaneous observations from public archives, Astronomer’s Telegrams, and Gamma-ray Coordination Network Circulars to construct the widest possible frequency range, we were able to find detections covering nearly 12 orders of magnitude from the meter-wavelength frequencies to hard X-rays on 12 April 2018 (MJD 58220). With this spectral energy distribution (SED), we studied the spectral components independently before investigating them jointly by constructing a model consisting of a leptonic jet, an irradiated disk, and a corona, using the `JetSeT` software[^2].

![](maxij1820_lc_inset_200718.pdf)

# Observations

Figure [1](#fig:bat_lc) shows the initial period of MAXI J$1820+070$ outburst in several wavelengths across the spectrum using data *Swift*/BAT (black diamonds), *Swift*/XRT (green squares) (cite: 2020ApJ...889..142S), and 4.7 GHz RATAN (blue triangles) (cite: 2018ATel11539....1T). The XRT and RATAN data have been normalized to be on the same scale of the BAT data. The period of the observations used in this work are bracketed in red.

In the following, we give information about the different simultaneous observations collected from archives, covering different bands from radio to gamma-ray on April 12, 2018. Further details can be found in Table [1](#tab:obs).

## JVLA

We retrieved calibrated Karl G. Jansky Very Large Array (VLA) data for experiment VLA/18A-470 from the National Radio Astronomy (NRAO) online archive. The JVLA antennas, in A configuration, were split in 3 subarrays in order to obtain simultaneous observations at 6 different central frequencies (4.7 GHz, 7.5 GHz, 8.5 GHz, 11 GHz, 20.7 GHz, 25.5 GHz). Data were imaged using `CASA` (`Common Astronomy Software Applications` package) version 5.6.2[^3] following standard procedures.

## ALMA

Atacama Large Millimiter/submillimiter Array (ALMA) data for project 2017.1.01103.T were retrieved from the ESO archive, and pipelined at the the Italian node of the European ALMA Regional Centre (INAF-Istituto di Radioastronomia, Bologna). Imaging was performed with `CASA` version 5.1.1, separately for each one of the 4 spectral windows (spw) present in the data (Band 7, spw 5, 7, 9, 11) corresponding to the following central frequencies: 336 GHz, 338 GHz, 348 GHz, 350 GHz (cite: 2018MNRAS.478.1512B).

## VLT/X-shooter

A number of observations of MAXI J$1820+070$ were performed with the X-shooter spectrograph (cite: vernet11) in the framework of the ESO program 0101.D-0356(A). We retrieved the processed spectra obtained during the 2018 outburst on 12 April from the European Southern Observatory (ESO) archive science portal. These data have been reduced by using the ESO X-shooter pipeline V2.7.0 and cover the 3000-25000 Åwavelength range. The observations were conduced in nodding configuration with the slit oriented at the parallactic angle and using slit widths of 1.3$\ensuremath{''}\times$11, 1.2$\ensuremath{''}\times$11 and 1.2$\ensuremath{''}\times$11 for the UVB, VIS and NIR arm, respectively. This configuration yields a spectral resolution R=$\lambda$/$\Delta \lambda$ of 4100, 6500 and 4300 for the UVB, VIS and NIR arm, respectively. The observing conditions where good with a seeing of 0.47$\ensuremath{''}$ and an average airmass of the source during the acquisition of 1.3$\ensuremath{''}$. The total exposure times are 1640 s, 1300 s and 1520 s for the UVB, VIS, and NIR arm, respectively. The reduced spectra have been corrected for the foreground extinction using the Cardelli function (cite: cardelli89) with R(V)=3.1 and A$_V$=0.627 mag (cite: Schlafly11).

In order to estimate the slit loss effect in the X-shooter spectra, we first applied standard aperture photometry on the $i^\prime$ acquisition image using the `iraf` task `phot`. The zero point was calibrated using the stars in the Panoramic Survey Telescope and Rapid Response System (cite: Flewelling2016) catalog.

From the aperture photometry we obtain an $i^\prime$ band apparent magnitude of m$_{AB}$= (12.20 $\pm$ 0.11) mag, corrected for foreground extinction. The derived flux at the filter central wavelength is $\lambda$F$_{i}$ = (2.01$\pm$0.2)$\times$10$^{-10}$ erg s$^{-1}$ cm$^{-2}$ which is in agreement with the average flux measured from the spectrum in the 7300-7600 Å wavelength range: $\lambda$F$_{i}$=(1.8$\pm$0.7)$\times$10$^{-10}$ erg s$^{-1}$ cm$^{-2}$.

## *XMM-Newton*/EPIC-pn

*XMM-Newton* ToO observations were carried out from 2018-04-12 07:27:58 to 09:39:28 UTC (obsid 0820880501) using burst mode. The European Photon Imaging Camera (EPIC)-pn data were analyzed using the standard procedures with the Science Analysis System (SAS) software version `xmmsas_20190531_1155-18.0.0`[^4].

## INTEGRAL

The *INTErnational Gamma-Ray Astrophysics Laboratory* (*INTEGRAL*) observed MAXI J$1820+070$ every 2–3 days between March 16, and May 8, via a series of Target of Opportunity (ToO) observations. For this work, we selected the data covering the interval (UTC) 11 April 2018 23:41:01 to 12 April 2018 11 14:00:21 (*INTEGRAL* revolution 1941). Here we focus on the analysis of data provided by the Integral Soft Gamma-Ray Imager (ISGRI; $18-1000$ keV) placed on the upper layer of the detector plane of the Imager on Board the INTEGRAL Satellite (IBIS) telescope ((cite: Ubertini2003)) and by the Optical Monitoring Camera (OMC) ($500-600$ nm) instruments. The data were analyzed using the Offline Science Analysis software (OSA) v11.0 available at the *INTEGRAL* Science Data Center (ISDC).[^5] We followed standard analysis procedures.

| Instrument |  Start Time (UTC)   |   Stop Time (UTC)    |     |     |
|:----------:|:-------------------:|:--------------------:|:---:|:---:|
|   VLITE    | 07:25:00 12-04-2018 | 13:07:00 12-04-2018. |     |     |
|    JVLA    | 07:15:00 12-04-2018 | 13:14:50 12-04-2018  |     |     |
|    ALMA    | 08:13:18 12-04-2018 | 09:20:16 12-04-2018  |     |     |
| X-shooter  | 07:41:08 12-04-2018 | 08:15:48 12-04-2018  |     |     |
|  EPIC-pn   | 07:27:58 12-04-2018 | 09:39:28 12-04-2018  |     |     |
|    OMC     | 23:41:01 11-04-2018 | 14:00:21 12-04-2018  |     |     |
|   ISGRI    | 23:41:01 11-04-2018 | 14:00:21 12-04-2018  |     |     |

: MAXI J$1820+070$ observations log

|            |           |                   |     |     |
|:----------:|:---------:|:-----------------:|:---:|:---:|
| Instrument | Frequency |   Flux density    |     |     |
|            |   (Hz)    |       (Jy)        |     |     |
|   VLITE    | 3.39E+08  |   0.033$\pm$5.3   |     |     |
|    JVLA    | 4.70E+09  | 0.0469$\pm$0.0047 |     |     |
|            | 7.50E+09  | 0.0488$\pm$0.0029 |     |     |
|            | 8.50E+09  | 0.0479$\pm$0.0048 |     |     |
|            | 1.10E+10  | 0.0483$\pm$0.0048 |     |     |
|            | 2.07E+10  | 0.0525$\pm$0.0054 |     |     |
|            | 2.55E+10  | 0.0530$\pm$0.0054 |     |     |
|    ALMA    | 3.36E+11  |  0.116$\pm$0.006  |     |     |
|            | 3.38E+11  |  0.114$\pm$0.006  |     |     |
|            | 3.48E+11  |  0.115$\pm$0.006  |     |     |
|            | 3.50E+11  |  0.110$\pm$0.006  |     |     |
| X-shooter  | 1.37E+14  | 0.0920$\pm$0.0002 |     |     |
|            | 1.81E+14  | 0.0757$\pm$0.0012 |     |     |
|            | 2.40E+14  | 0.0652$\pm$0.0003 |     |     |
|            | 2.86E+14  | 0.0634$\pm$0.0006 |     |     |
|            | 3.79E+14  | 0.0689$\pm$0.0007 |     |     |
|            | 4.00E+14  | 0.0709$\pm$0.0002 |     |     |
|            | 4.42E+14  | 0.0743$\pm$0.0003 |     |     |
|            | 4.87E+14  | 0.0775$\pm$0.0005 |     |     |
|            | 5.15E+14  | 0.0794$\pm$0.0002 |     |     |
|            | 5.32E+14  | 0.0803$\pm$0.0003 |     |     |
|            | 5.76E+14  | 0.0831$\pm$0.0005 |     |     |
|            | 6.27E+14  | 0.0868$\pm$0.0003 |     |     |
|            | 7.00E+14  | 0.0952$\pm$0.0004 |     |     |
|    OMC     | 5.66E+14  | 0.0813$\pm$0.0071 |     |     |

: Collected flux densities for the jet modelling.

![](radio_jet.pdf)

# Results and discussion

## The compact jet emission

With the collected flux densities between radio and UV bands, we built the jet SED. In addition to the JVLA and ALMA data mentioned above, we considered Very Large Array Low-band Ionosphere and Transient Experiment (VLITE, (cite: 2016SPIE.9906E..5BC)), also collected on 12 April 2018 (cite: 2018ATel11540....1P). We show in Figure [2](#fig:jet_compact) data from JVLA, ALMA, X-shooter, and OMC. For X-shooter, we considered only the part of the spectrum not affected by absorption/emission features, and averaged values for each of these intervals to obtain continuum flux density values. In this way, we calculated 12 photometric measurements (Table [2](#tab:fluxes)) covering the interval from NIR to UV. The overall shape of the X-shooter spectrum shows a break, resulting in a change of the spectral index, at about 2$\times$10$^{14}$ Hz. This is most probably the frequency at which the broadband SED is no longer dominated by the jet synchrotron emission, while the accretion disk thermal emission increases (see Sec. [4](#Sec:SED)). The single value from OMC is in good agreement with the X-shooter photometry.

We fitted the radio to optical data set with a broken-power law to identify the synchrotron peak frequency and the spectral slopes of the optically thin and thick regions (cite: 2013MNRAS.429..815R). We used the Astropy `BrokenPowerLaw1D` function (see (cite: astropy:2013; astropy:2018)) adopting the `LevMarLSQFitter` routine to perform a Levenberg-Marquardt least squares statistic. We excluded from the fit the X-shooter points above the third one (Optical and UV ranges) since they show a turn-up of the flux density liekly due to accretion disk emission. Similarly, we did not consider data points below 20 GHz, since they show a different slope, probably belonging to a physically distinct (and more expanded) radio jet component. We obtained a synchrotron peak frequency of 1.6$\pm$0.2$\times10^{13}$ Hz. The estimated slope for the optically thick part of the spectrum is $\alpha_{thick}=0.28\pm0.02$ and $\alpha_{thin}=-0.61\pm0.01$ for the optically thin one (adopting the convention $S\propto\nu^{\alpha}$, where $S$ is the flux density, $\nu$ the frequency, and $\alpha$ the spectral index). The slope of the lower frequency radio SED (0.3$-$10 GHz), fitted with the `PowerLaw1D` Astropy function, is $\alpha=0.11\pm0.02$. In Sec. [4](#Sec:SED), a detailed physical model of this source is presented and provides a more precise estimate of the jet parameters.

![](P-Cygni.pdf)

## Accretion disk winds

(cite: 2019ApJ...879L...4M) discovered accretion disk winds in MAXI J$1820+070$ during both the 2018 hard state rise and decay. Absorption wind signatures were detected in the blue wings of He I $\lambda$5876 and $\lambda$6678 emission lines, reaching a maximum terminal velocity ($v_t$) of 1200 km/s in one of the epochs. For H$\alpha$, both a blue-wing broadened emission line profile, implying a wind component of 1800 km/s, and a superimposed absorption trough with a $v_t$=1200 km/s were found. Those authors collected several epochs from 15 March to 4 November 2018, allowing them to follow the evolution of the winds from the hard state to the disappearance during soft state, and back.

The VLT/X-shooter data presented in this work add an epoch to monitoring in (cite: 2019ApJ...879L...4M), falling in an uncovered time window of one month between 26 March and 23 April. We normalized these spectra by dividing them for the continuum emission, fitted with a third order spline3 function by using the IRAF task `continuum`. These spectra are rich with emission lines from the UVB to the NIR arms. Following the (cite: 2019ApJ...879L...4M) analysis, we explored the presence of wind signatures linked to the mentioned emission lines (He I and H$\alpha$), and found a significant absorption on the left wing of He I $\lambda$5876. In Fig. [3](#fig:winds) (left panel) we show the relative portion of the spectrum, with the absorption features highlighted in purple. We consider as bona-fide absorption troughs the ones with a dip of at least three times the continuum RMS. A prominent He I absorption feature is visible between -700 and -900 km/s, showing the same profile as the correspondent emission line. This one has a $v_t$ of 880 km/s. Further blue-ward absorption features are visible, but since they are narrower and not connected to the previous ones, we consider those as not related to the accretion disk wind. The same is true for the narrow absorption features detected blue-wards of the H$\alpha$ emission line (Fig. [3](#fig:winds), central panel). For the He I $\lambda$6678 line, a single absorption trough is detected between -800 and -850 km/s (Fig. [3](#fig:winds), right panel) with a $v_t$ of -825 km/s.\
During this period, we observe strong asymmetries in the emission lines which are commonly observed in lines emitted from the disc, particularly in the He I $\lambda$ 6678 and in the H$\alpha$.

Therefore, we explored line profile properties by applying multi-component Gaussian fits using the `python` packages `curvefit` and `leastsq`. In Figure [4](#fig:linefit) we show the result of this analysis for H$\alpha$ (left panel) and He I $\lambda$6678 (right panel). The H$\alpha$ line analysis has been performed in the wavelength region 644$-$670 nm, which includes the feature of interest and the local continuum. In this case we have ignored from the fit the He I emission line, which falls at the end of the analyzed wavelength range. The H$\alpha$ profile is well modelled by two narrow Gaussian components, and only one broad Gaussian component is needed to fit the red wing of the emission line. We note the absence of a blue-shifted broad wing, which has been observed in (cite: 2019ApJ...879L...4M), as well as p-cygni profiles signatures. However a forest of narrow absorption lines is clearly visible in the blue region of the H$\alpha$. The two narrow components are characterized by a central wavelength ($\lambda_{c}$) and a full width at half maximum (FWHM) of $\lambda_{c}$= (6574.4$\pm$0.4) Å  FWHM = (389$\pm$20) km/s and $\lambda_{c}$= (6559.8$\pm$ 0.3) Å  FWHM = (914$\pm$18) km/s, respectively. While the broad red wing is centered at $\lambda_{c}$= (6583.0$\pm$3.0) Å and has FWHM=(2982$\pm$210) km/s. From the redshift of the broad wing with respect to the H$\alpha$ rest frame wavelength we derive an outflow velocity of $v$= (923$\pm$14) km/s, while the separation between the two narrow components is $\sim$ 667 km/s.

For the He I $\lambda$6678 line analysis we used the wavelength region $664-672$ nm, which includes also the local continuum but excludes the wavelength range in which the H$\alpha$ falls. The He I $\lambda$6678 line profile is well modelled by three Gaussian components. The first one is well centered on the rest-frame He I wavelength with a $\lambda_{c}$= (6679.2 $\pm$ 0.4) Å and has a FWHM=(536$\pm$54) km/s. The two remaining Gaussians are blueshifted and redshifted of $\sim$450 km/s with respect to the first component, and are characterized by $\lambda_{c}$= (6669.4 $\pm$ 0.2) Å, FWHM = (307$\pm$12) km/s and $\lambda_{c}$= (6689.7 $\pm$ 0.3) Å, FWHM = (295$\pm$29) km/s, respectively.

As a whole, the detected optical disk wind features show properties with in between what was found in the hard and soft state epochs collected by (cite: 2019ApJ...879L...4M), confirming the decreasing trend of the optical wind between the two states of the source.

![image](fitHa.pdf) ![image](fitHeI.pdf)

## Soft X-ray

We fitted the *XMM Newton*/EPIC-pn spectrum in the $0.5-12$ keV energy range in `XSPEC` using a(`Tbabs*Powerlaw` model. With this model we derive the following parameters: nH = $0.13 \pm 0.04 \times 10^{22} \textrm{ cm}^{-2}, kT_{bb} = 0.24 \pm 0.03 \textrm{ keV, and } \Gamma= 1.65 \pm 0.08$ with $\chi2/\nu = 1.00$.

## Hard X-ray

We fitted the *INTEGRAL*/IBIS/ISGRI spectrum in the $30-400$ keV energy range. A systematic 1.5 % error was added to the data, following OSA 11 standard recommendations[^6]. A power-law fit to the data in `XSPEC` found a photon index of $\Gamma=2.41 \pm 0.01$ and a $\chi^2/\nu = 71.80$. The spectrum deviates from a simple power-law model, especially at high energies, with residuals suggesting a Comptonized spectrum. Fitting the data with a `CompTT` model using a photon temperature of 0.24 keV fixed to the $kT_{bb}$ value from *XMM* finds a better fit, with $k_T = 36.4 \pm 0.9 \textrm{ keV, } \tau = 1.27 \pm 0.05, \textrm{ and } \chi^2/\nu= 6.21$. When including a reflecting component (REFLECT) with the reflection fraction fixed to 1, the fit improves to $\chi^2/\nu = 3.45 \textrm{ with } k_T = 38 \pm 1 \textrm{ keV and } \tau = 1.44 \pm 0.06$. Following (cite: 2019ApJ...870...92R), a cutoff power-law was added `Reflect*(CompTT)+cutoff` with $\Gamma = 1.6$ and a cutoff energy of 200 keV that improved the fit to $0.71$ and has fit parameters $k_T = 27 \pm 4 \textrm{ keV, } \tau = 2.2$.

To characterize the X-ray spectrum, a joint fit was performed between the two instruments spanning $0.5 - 400$ keV using the model `Tbabs*Reflect*(diskbb+CompTT)+Tbabs*cutoff` found best-fit parameters of $kt_{BB} = 0.27 \pm 0.01 \textrm{ keV, } kT = 27 \pm 1 \textrm{ keV, and } \tau = 2.2 \pm 0.1 \textrm{ with } \chi^2 / \nu = 0.95$.

Using this joint spectrum, we calculated the accretion luminosity in the $1 - 200$ kev energy range and found a value of $\sim 6 \times 10^{37}$ erg/s for a distance 3 kpc.

|                  |          `diskir`           |        `diskir+po`         |
|:----------------:|:---------------------------:|:--------------------------:|
| $kT_{disk}$(keV) |      $0.116 \pm 0.007$      |     $0.122 \pm 0.007$      |
|     $\Gamma$     |       $1.78 \pm 0.02$       |      $1.70 \pm 0.04$       |
|   $kT_e$ (keV)   |         $58 \pm 4$          |         $37 \pm 4$         |
|    $L_C/L_D$     |        $4.7 \pm 0.5$        |       $4.7 \pm 0.6$        |
|    $f_{out}$     | $(1 \pm 40) \times 10^{-7}$ | $(4 \pm 15) \times10^{-2}$ |
| $\log(r_{out})$  |       $3.45 \pm 0.04$       |         $3 \pm 1$          |
|  $\Gamma_{po}$   |             $-$             |       $1.6 \pm 0.3$        |
|   Norm$_{po}$    |             $-$             |       $1.0 \pm 1.7$        |
|  $\chi^2/ \nu$   |           $1.30$            |           $0.97$           |

: Irradiated disk fit parameters.

### IR $-$ Hard X-ray Spectrum

Subsequently, we fit our data from the near-IR to hard X-rays using an irradiated disk model to compare with (cite: 2018ApJ...868...54S), which analyzed a similar energy range using observations from 24 March. The irradiated disk model accounts for the effects of the Comptonized emission on the accretion disk and the soft-excess that is seen in the hard state (cite: DiskIrrModel2009). Figure [5](#fig:diskir_sed) shows the spectrum from $0.001 - 400$ keV with the `diskir` model shown as a solid red line and the power-law component of the `diskir+po` model as a dashed black line. The power law is used to model the high-energy cutoff power-law component in the previous section. Table [3](#table:diskir_para) contains the fit parameters using a `diskir` model with and without an additional power-law component. We found that including a power-law component improved the fit at high energies and reduced the $\chi^2 / \nu$ from 1.30 to $\chi^2 / \nu = 0.97$ with an f-test probability of $3.7 \times 10^{-8}$.

The origin of the power-law component is unclear. As shown below in Figure [7](#fig:jet), the expected jet flux is too low for the component to be jet emission at those energies. However, the emission could possibly be from Comptonization of non-thermal electrons as in the case of GRS $1716-249$ (cite: 2020MNRAS.494..571B).

![](maxij1820_spectra_diskir_210113.pdf)

# Broadband SED modelling

We modelled the broadband SED of MAXI J1820+070 using a combination of jet leptonic models and irradiated disk and corona model implemented in Jets SED modeler and fitting Tool (`JetSeT`) [^7] (cite: jetsetascl; Tramacere2011; Tramacere2009). A more accurate description of the model is discussed in (cite: TramacereInPrep). We assume that the optical/UV up to keV energies is dominated by disc irradiation and coronal emission. The emission in the mm to optical region is dominated by the non-thermal emission of leptons accelerated in the jet by shock and/or stochastic acceleration, and we assume that the break at $\approx 1.5\times 10^{13}$ Hz is due to the transition from the optically thin to the optically thick synchrotron emission. The radio emission is dominated by the terminal part of the jet that starts beyond the acceleration region and extends up to a distance of $\approx 1\times 10^{15}$ cm according to (cite: 2020NatAs.tmp....2B). A schematic view of the model is provided in Fig. [6](#fig:jet_diagram)

## Individual Model Components Description

In the following we describe the implementation of each model component.

### Irradiated Disk and Hot Corona

To model the UV to hard-X-ray emission we have used the disk Comptonization plus disk irradiation model, `DiskIrrComp` implemented in `JetSeT`. The `DiskIrrComp` is based on the `diskir` model (cite: DiskIrrModel2009) and the Comptonization model of (cite: Zdziarski2009). In detail, we assume that a classical multi-temperature disk with an inner temperature $T_{Disk}$ and an extension $R_{in}=3 R_{S}$ to $R_{out}$, expressed by the dimensionless parameters $r_{in}=R/R_{in}$ and $r_{out}=R/R_{out}$. The disk spectrum is modified due to the reprocessing of irradiated emission from the disk itself and from the corona Compotonization tail. The corona emission is described by a power law with an exponential cutoff with a photon index $\Gamma_{Comp}$ and a cut-off energy $E_{Comp}=kT_{e}$ where $kT_{e}$ is the corresponding electron temperature. The Compton hump component is described by a power-law with exponential cut-off with a photon index $\Gamma_{hump}$ and a cut-off energy $E_{hump}$. We refer to this model as `Comp. hump`. The normalization of the Compton tail component is parameterized as a fraction of the disk luminosity $L_{Disk}$ according to $L_{Comp}^{ratio}=L_{C}/L_{Disk}$. The total bolometric flux will be $L_{bol}=L_{Disk}+L_{rep}+L_{C}$, where $L_{rep}$ represents the thermalized fraction $f_{in}$ of $L_{C}$ thermalized within $r_{in}$ and $r_{irr}=R_{irr}/R_{in}$, where $R_{irr}$ is the radius of the inner disk irradiated by the Compton tail. A fraction $f_{out}$ of the bolometric luminosity will irradiate the outer disk. The irradiation creates a shoulder with a spectral trend $f_{out}\propto L_{bol}\nu^{-1}$ that extends between $\nu_1=3kT(r_{out})$ and $\nu_2=3kT(r_{t})$, where $r_{t}$ is the transitional radius between gravitational and irradiation energy release. This effect depends strongly on $r_{out}$ and $f_{out}$, and it is present even without corona Comptonization, because it represents the disk self-irradiation. The presence of a Comptonization component will provide a further heating of the disk in the inner part modifying the pure gravitational temperature profile.

### Pre-acceleration and Acceleration Region

We assume that electrons in the pre-acceleration region close to the base of the jet are described by a thermal plasma with cooling dominated by adiabatic losses. Once the particles approach the acceleration region they are accelerated under the effect of diffusive shock acceleration and/or stochastic acceleration and the corresponding energy distribution can be modeled by a power-law with a high-energy cutoff $$\begin{equation}
  N_{e,acc}(\gamma)=N \gamma^{-s} \exp(-\gamma/\gamma_{cut})
\end{equation}$$ where the value of $\gamma_{cut}$ takes into account the balance between cooling and acceleration terms. The index $s$ is dictated by the competition of the acceleration time scales and escape time scales (cite: Tramacere2011). We assume that the acceleration region extends from $z_{acc}^{start}$ to $z_{acc}^{end}$, with cross section $R_{acc}$ equal to the average cross section of the jet at $z=(z_{acc}^{start} + z_{acc}^{end})/2$, with $z_{acc}^{end} - z_{acc}^{start}=2 R_{acc}$. The emission from the acceleration region is reproduced using the jet leptonic model `Jet` implemented in `JetSeT`, and we refer to it as `JetAcc` (cite: TramacereInPrep).

### Radio Jet

To model the radio jet emission we have used the `JetSeT` multi-zone radio jet model `RadioJet`. This model implements a continuous jet as a sum of $N_{c}$ single zones, following the approach of (cite: Kaiser2006), where for each zone the values of $R$ and $B$ are ruled by Eq. [\[Eq-jet-ballistic\]](#Eq-jet-ballistic), and the particle density scales as $$\begin{equation}
  N_{s,i}= N_{s,0}(z_{s,0}/z_i)^{m_N}
\end{equation}$$ where $N_{s,0}$ is the initial density of emitters at the starting point of the radio jet $z_{s,0}$, $z_i$ is the average position of the $i_{th}$ component, and $m_N$ is the index of the particle density law fixed to 2. The initial particle density is a fraction $N_{frac}$ of that present in the acceleration region and we fix it to 1. The radio jet extends from $z_{radio}^{start}=(z_{acc} +R_{acc}) K_R^{start}$ to $z_{radio}^{end}(z_{acc} +R_{acc}) K_R^{end}$, where $K_R^{start}$ and $K_R^{end}$ are free parameters. In the present analysis we fix $K_R^{start}= 1$ , and $K_R^{end}$ is fixed in order to match the value of $1\times 10^{15}$ cm according to the analysis presented in (cite: 2020NatAs.tmp....2B). The particle distribution in each region has the same spectral law as in the acceleration region, but we decrease the value of $\gamma_{cut}$ to take into account the effect of the cooling when the particles leave the acceleration region. In our analysis we take into account only synchrotron cooling and we evolve $\gamma_{cut}$ according to Eq. 27 in (cite: Kaiser2006). More details about the connection between the acceleration and radio are discussed in Sec. [4.3](#model-fit)

![](jet-model-scheme.png)

## Phenomenological Model Setup

As a first step we set the geometrical properties of the jet, i.e. we define the extent of the pre-acceleration, acceleration, and radio emission sites, and the values of the magnetic field. We assume that the jet is launched at distance $z_0$ from the BH, with an initial cross section $R_0$, and that the bulk Lorentz factor ($\Gamma_{jet}$) of the jet is constant over the full jet extent. The acceleration region starts at a distance $z_{acc}^{start}$ with a width equal to jet cross section diameter $R_{acc}=2R(z_{acc})$, and we treat it as a spherical region. The radio region starts at $z^{start}_{radio}=K_{R}^{start}( z_{acc} + R_{acc}$) and ends at a distance $z^{end}_{radio}=K_{R}^{end} (z_{acc} +R_{acc})$ (a scheme of the model is presented in Fig. [6](#fig:jet_diagram)). According to (cite: 2020NatAs.tmp....2B) we fix the distance of jet from the observer to the value of $d=3$ kpc, the termination of the radio jet to the value of $z_{end}\approx 1\times 10^{15}$ cm, and the value of the beaming factor to $\delta=[\Gamma_{jet}(1-\beta_{jet}\cos(\theta_{obs})]^{-1}\approx 2.2$, using the values of $\beta_{jet}=0.89$ and $\theta_{obs}= 63^{\circ}$ reported in (cite: 2020NatAs.tmp....2B). We assume a ballistic jet model (cite: Kaiser2006; BBR) characterized by $$\begin{eqnarray}
    B(z) &\propto& B_0(z_0/z)^{m_B} \nonumber \\ 
   \label{Eq-jet-ballistic}
    R(z) &\propto& R_0(z/z_0)^{m_R} \\ 

    N(z) &\propto& R_0(z_0/z)^{m_N}  \nonumber 
\end{eqnarray}$$

with $m_B\approx 1$ and $m_R = 1$, and $m_N=2.0$. This choice assumes that the jet is very close to the ballistic regime, with a magnetic field dominated by the toroidal component and justifies the assumption that the bulk Lorentz factor is constant along the jet.

We use a black hole mass of $M_{BH}= 8 M_{\Sun}$. The jet luminosity $L_{jet}$ is linked to the Eddington luminosity ($L_{Edd}$) according to $$\begin{equation}
 L_{jet}=  \frac{1}{2} q_{jet} L_{Edd}
 \label{Eq-jet-eff}
    
\end{equation}$$ where $L_{Edd}\approx 1.3\times 10^{38} (M_{BH}/M_{\Sun})$ erg s$^{-1}$ (cite: Ryb1986). It is worth noting that our $q_{jet}$ parameter is not linked directly to the accretion efficiency process, because the jet powering could, in principle, be supported also by other mechanisms such as the Blandford–Znajek mechanism (cite: BZ1977), that predicts electromagnetic extraction of energy and angular momentum from magnetized accretion disc surround a black hole. Hence, our $q_{jet}$ parameter should not be used to infer or constrain the accretion efficiency, and will be discussed in a more accurate physical context in (cite: TramacereInPrep).

We assume that the jet is launched at a distance $z=z_{0}$ from the BH with $z_0=50 R_S\approx 1.2 \times 10^{8}$ cm, where $R_S=(2GM_{BH})/{c^2}$. The launching jet position $z=z_{0}$, in the current analysis is assumed constant, to reduce the model complexity, and it is chosen according to reference values published in previous analysis (cite: Romero2010). The initial radius of the jet is set to $R(z_0)=0.1 z_0$, resulting in an opening angle of $\theta_{open} \approx 5.7 ^\circ$. We impose that in the launching region the entire jet power is in the form of magnetic energy $$\begin{equation}
     L_{jet}= L_B(z_0)= \pi U_B(z_0) R(z_0)^2\Gamma_{jet}^2\beta_{jet}c
    \label{Eq-jet-eff}
\end{equation}$$ where $U_B=B^2/(8\pi)$, and setting $q_{jet}=0.2$ we obtain $B_0\approx 6.8 \times 10^{6}$ G.

The value of $m_B$ can be constrained from the spectral index of radio jet emission, $\alpha_{R}\approx 0.15$, according to the Eq. 39 in (cite: Kaiser2006) that refers to the case of strong radiative cooling and almost constant value of the electron distribution high-energy cutoff. According to this scenario, that is very similar to what we expect in our case, we can rearrange Eq. 39 in (cite: Kaiser2006) as: $$\begin{equation}
    m_B=\frac{1+m_R}{2 - \alpha_{R}}
\end{equation}$$ that is similar to the trend of the thick radio spectrum discussed in (cite: Peer:2009), and we obtain a value of $m_B\approx 1.1$ We stress that this is an initial guess done assuming that the jet is not changing after the acceleration region. As we will discuss in the next section, during the model fit we need to take into account that jet expansion might change above the acceleration region, hence we will relax the constraint on $m_{B}$ and $m_R$ considered in the `RadioJet` emission.

To constrain the value of $z_{acc}$ we impose that $R_{acc} =R(z_{acc} )$, $B_{acc} =B(z_{acc} )$ and $N_{e,acc}$ correspond to a synchrotron self-absorption frequency of $\nu_t \approx 1.5 \times10^{13}$ Hz. This value of $\nu_t$ is obtained from the phenomenological fit of the optically-thin to optically-thick synchrotron emission between mm and optical data shown in Fig. [2](#fig:jet_compact). In order to solve this problem we combine the analytical expression of the synchrotron self-absorption frequency ($\nu_t$) (cite: Ryb1986), evaluated at the peak i.e. $\alpha_{\nu}=0$ $$\begin{equation}
    \nu_t=\nu_L 
    \Big[
    \frac{\pi\sqrt{\pi}}{4}
    \frac{q R_{acc}  N_{e,acc}}{B_{acc} }
    f_{k}(s)
    \Big]^{\frac{2}{s+4}},
     \label{eq-synch-nu-abs}
\end{equation}$$ and of that the synchrotron emissivity (cite: Ryb1986) $\epsilon_s(\nu)$ : $$\begin{equation}
    \epsilon_s(\nu)= \frac{F_\nu d_L^2 }{V}= 
    \frac{3\sigma_T c N_{e,acc} U_B^{acc}}{16 \pi \sqrt(\pi) \nu_L}
    f_{\epsilon}(s),
    \label{eq-synch-em}
\end{equation}$$ where $q$ is the electron charge, $U_B^{acc}$ is the value of the magnetic field, $V$ is the volume of a spherical geometry of volume $V$ of radius $R_{acc}$, $s$ is the slope of the electron distribution power-law and $\nu_L=\frac{qB}{2\pi m_e c}$ is the Larmor frequency, and where the functions $f_{k}(s)$ and $f_{\epsilon}(s)$ are approximated to percent accuracy as reported in (cite: Ghisellini2013). The value of $s$ is obtained using the optically thin spectral index $\approx 0.6$ from the phenomenological fit in Fig. [2](#fig:jet_compact), according to the relation $s= 2\alpha +1\approx 2.2$ (cite: Ryb1986). We solve Eq. [\[eq-synch-em\]](#eq-synch-em) with respect to $N_{e}^{acc}$ and then substitute in Eq. [\[eq-synch-nu-abs\]](#eq-synch-nu-abs), and we insert the functional form of $B=B(z_{acc})$ and $R=R(z_{acc})$ according to Eq. [\[Eq-jet-ballistic\]](#Eq-jet-ballistic). The final equation solved with respect to $z_{acc}$ reads:

$$\begin{equation}
z_{acc} = \Big[
\Big(\frac{\nu_t 2\pi m_e c}{q B_0^2 z_0^{m_B}}\Big)^{\frac{s+4}{2}}
\frac{3 \sigma_{T}   (B_0 R_0)^2  f_{\epsilon}(s)  z_0^{2 \Delta_m}}{16 r_e^2 \pi^3   f_k(s) F_{\nu} d_L^2  }
\Big]^{\psi}
\label{eq-z_acc}
\end{equation}$$

where $r_e=q^2/(m_e c^2)$ is the classical electron radius, $\Delta_m  =   m_B - m_R$, and $\psi   =  \frac{2}{ 4  \Delta_m  - m_B (s + 4 )}$.

Consequently, the starting position of the radio jet is set to $z_{radio}^{start}=z_{acc}^{end}=z_{acc}+R_{acc} \approx 3.1\times 10^{10}$ cm, with an extent derived from (cite: 2020NatAs.tmp....2B) of $z_{end} \gtrsim 30000 z_{radio}^{start}$

The value of the cut-off of the electron distribution is set to $\gamma_{cut}=60$, in order to produce the peak of the synchrotron emission above the IR frequencies for a magnetic field $B_{acc}\approx 1.8 \times 10^4$ G, with a power-law slope $s\approx 2.1$ that is slightly lower then the value derived from the optically thin spectral index.

The constrained value of $z_{acc}$ can be used to derive the hadroninc content of the jet energetic in form of cold protons. Following (cite: Romero2010) we impose that in the acceleration region of the jet the magnetic energy of the jet is in subequipartition with the bulk kinetic energy of the cold protons, a condition that is mandatory to allow the mechanical compressibility of the plasma (cite: Kossimarov2007). We define the parameter $\rho^{acc}_{p,B}=U_{p}(z_{acc})/U_{B}(z_{acc})$, where $U_{p}(z)=n_p(z) m_p c^2$, and we require that $\rho_{p,B}>1$. This choice sets a value of cold proton luminosity in the acceleration region $L_p(z_{acc})>3.6 \times 10^{37}$ erg $s^{-1}$.

+----------------------------------------------------------------+
|                                                                |
+:====================+:============:+:=========================:+
| Input Parameters                                               |
+---------------------+--------------+---------------------------+
| par. name           | units        | input value               |
+---------------------+--------------+---------------------------+
| $z_0$               | cm           | $1.12   \times 10^{8}$    |
+---------------------+--------------+---------------------------+
| $r_0$               | cm           | $1.12   \times 10^{7}$    |
+---------------------+--------------+---------------------------+
| $M_{BH}$            | $M_{\Sun}$   | 8                         |
+---------------------+--------------+---------------------------+
| $q_{jet}$           |              | 0.20                      |
+---------------------+--------------+---------------------------+
| $F_{\nu}^t$         | Jy           | $0.5$                     |
+---------------------+--------------+---------------------------+
| $\nu_t$             | Hz           | $1.5   \times 10^{13}$    |
+---------------------+--------------+---------------------------+
| $s$                 |              | 2.1                       |
+---------------------+--------------+---------------------------+
| $\rho^{acc}_{p,B}$  |              | $>1$                      |
+---------------------+--------------+---------------------------+
| $m_{B}$             |              | 1.1                       |
+---------------------+--------------+---------------------------+
| $m_{R}$             |              | 1.0                       |
+---------------------+--------------+---------------------------+
| Output Parameters                                              |
+---------------------+--------------+---------------------------+
| par. name           | units        | output value              |
+---------------------+--------------+---------------------------+
| $B_0$               | G            | $6.8     \times 10^{6}$   |
+---------------------+--------------+---------------------------+
| $B_{acc}$           | G            | $1.8\times 10^{-4}$       |
+---------------------+--------------+---------------------------+
| $L_{p}^{acc}$       | erg s$^{-1}$ | $>3.6     \times 10^{37}$ |
+---------------------+--------------+---------------------------+
| $z_{acc}^{start}$   | cm           | $2.4      \times 10^{10}$ |
+---------------------+--------------+---------------------------+
| $z_{acc}^{end}$     | cm           | $2.9      \times 10^{10}$ |
+---------------------+--------------+---------------------------+
| $z_{acc}$           | cm           | $2.6      \times 10^{10}$ |
+---------------------+--------------+---------------------------+
| $R_{acc}$           | cm           | $2.6      \times 10^{9}$  |
+---------------------+--------------+---------------------------+
| $z_{radio}^{start}$ | cm           | $2.9      \times 10^{10}$ |
+---------------------+--------------+---------------------------+
| $z_{radio}^{end}$   | cm           | $\gtrsim 1\times 10^{15}$ |
+---------------------+--------------+---------------------------+

: Phenomenological Setup Parameters

+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                                                                                                                                  |
+:=============:+:===================+:============:+:====================:+:====================:+:===================:+:===============================================:+:======:+
| model name    | par. name          | units        | best fit value       | error                | starting value      | fit boundaries                                  | frozen |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| `CompHump`    | $E_{hump}$         | keV          | 26                   | 14                   | 20                  | \[ 15 ; 35\]                                    | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $\Gamma_{hump}$    |              | -0.5                 | 2                    | -1.2                | \[ -2 ; 2\]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| `DiskIrrComp` | $T_{Disk}$         | K            |                      |                      | $1.55 \times 10^6$  |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $L_{Disk}$         | erg s$^{-1}$ | $1.09\times 10^{37}$ | $1.0\times 10^{32}$  | $1 \times 10^{37}$  | \[ $1\times 10^{36}$ ; $1 \times 10^{39}$\]     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $r_{out}$          |              | $3.58\times 10^{3}$  | $0.21\times 10^{3}$  | $5 \times 10^{3}$   | \[ 1 ; – \]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $r_{irr}$          |              |                      |                      | 1.1                 |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $\Gamma_{Comp}$    |              | 1.64                 | 0.12                 | 1.65                | \[ 1.3 ; 1.9 \]                                 | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $E_{Comp}$         | keV          | 150                  | 100                  | 140                 | \[ 20 ; 200 \]                                  | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $L_{Comp}^{ratio}$ |              | 4.1                  | 0.6                  | 4.5                 | \[ 0 ; – \]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $f_{in}$           |              |                      |                      | 0.1                 |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $f_{out}$          |              | $1 \times 10^{-2}$   | $40 \times 10^{-2}$  | 0.01                | \[ 0 ; – \]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| `DiskIrrComp` | $r_{out}$          |              | $3.4\times 10^{3}$   | $0.5\times 10^{3}$   | $3.58\times 10^{3}$ | \[ 1 ; – \]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $f_{out}$          |              | $7.33\times 10^{-3}$ | $0.15\times 10^{-3}$ | $1 \times 10^{-2}$  | \[ 0 ; – \]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $L_{Comp}^{ratio}$ |              | 4.270                | 0.016                | 4.1                 | \[ 0 ; – \]                                     | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| `JetAcc`      | $N_{e,acc}$        | cm$^{-3}$    | $9.998\times10^{11}$ | $0.001\times10^{11}$ | $1.0\times10^{12}$  | \[0 ; – \]                                      | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $s$                |              | 2.082                | 0.007                | 2.1                 | \[- ; - \]                                      | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $\gamma_{cut}$     |              | $65.4$               | $1.7$                | 60                  | \[1 ; – \]                                      | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $R_{acc}$          | cm           | $2.6\times 10^{9}$   | $1.0\times10^{1}$    | $2.6\times 10^{9}$  | \[ $1.32\times 10^{9}$ ; $3.96 \times 10^{9}$\] | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $z_{acc}$          | cm           |                      |                      | $2.8\times 10^{10}$ |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $B_{acc}$          | G            | 17986                | $1.0\times10^{-3}$   | 17986               | \[ 8993 ; 26980 \]                              | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $\theta_{jet}$     | deg          |                      |                      | 63                  |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $\Gamma_{jet}$     |              |                      |                      | 2.19                |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| `RadioJet`    | $z_{inj}$          |              |                      |                      | $2.5\times 10^{10}$ |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $N_{frac}$         |              |                      |                      | 1                   |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $K_{R}^{start}$    |              |                      |                      | 1                   |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $K_{R}^{end}$      |              |                      |                      | 30000               |                                                 | True   |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+
| "             | $m_{jet}$          |              | 1.203                | 0.001                | 1.1                 | \[ 0.5 ; 1.5 \]                                 | False  |
+---------------+--------------------+--------------+----------------------+----------------------+---------------------+-------------------------------------------------+--------+

## Model Fit and Results

### Initial model setup

To optimize the model we use the composite model interface `FitModel` provided by `JetSeT`, that allows combining different models in a global model. This model can be optimized by inserting it to the `ModelMinimizer` `JetSeT` plugin. In the current analysis we use a frequentist approach and we use the `Minuit`  `ModelMinimizer` option. We have used the  `Data` and  `ObsData` `JetSeT` tools to import the observed data, and we have added a 5% systematic error in the range $[1\times 10^{8},1\times 10^{16}]$ Hz, to avoid that the large inhomogeneity on the fractional error between radio and optical/UV data, could bias the fit convergence. For the error estimate we provide only errors derived form the `MIGRAD` module of `Minuit`, a more reliable estimate based on a Markov chain Monte Carlo (MCMC) will be presented in (cite: TramacereInPrep)

The `DiskIrrComp` model, the `Comp. hump` model, and the `JetAcc` are independent, on the contrary, `JetAcc` and radio `RadioJet` are bound.

![image](jetset_best_fit_model_1_Fnu_no_res)\

![](jetset_best_fit_model_1_nuFnu)

The initial values of the parameters for the `DiskIrrComp` model are chosen according to the analysis presented in Sec [3.3](#Soft-X-ray-analysis) and Sec. [3.4](#Hard-X-ray-analysis). In detail, we set the initial values of $L_{disk}=1\times 10^{37}$ erg s$^{-1}$, of $r_{out}=5000$, of $f_{out}=0.01$, and $L_{Comp}^{ratio}=4.5$ and we fix the inner disk temperature to $T_{Disk}=1.55\times 10^{6}$K, and the parameters $r_{irr}=1.1$ and $f_{in}=0.1$, the choice adopted in (cite: DiskIrrModel2009), when the Comptonization of the outer disk is included in the irradiated disk.

For the `JetAcc` model, we fix $\theta_{jet}=63^{\circ}$, $\Gamma_{jet}=2.19$, we put a relative bound of +/- 0.5 centered on the parameters values derived in the previous section, $R_{acc}=2.6 \times 10^{19}$ cm, and $B_{acc}\approx 1.8 \times 10^4$ G, we freeze the initial value of $z_{acc}=2.6 \times 10^{10}$ cm, and we leave free the parameters for the electron distribution.

The initial setup of the parameters of the `RadioJet` is more complex and we need to take into account the physical connection with the acceleration region and the cooling process.

This effect plays a crucial role, indeed, as already discussed in (cite: Kaiser2006) and (cite: Peer:2009), the combination of synchrotron cooling and jet expansion (assuming a negligible contribution from adiabatic cooling) will result in an asymptotic value of $\gamma_{cut}(t)$, that can naturally explain the flat radio spectrum without the need to introduce significant particle re-acceleration in the radio jet. We follow the approach reported in (cite: Peer:2009) (in the case of negligible adiabatic cooling) and we set $m_B^{radio}=m_R^{radio}=m_{jet}$. The particle cut-off evolution in the radio jet will evolve according to (cite: Kaiser2006): $$\begin{equation}
\label{radio-synch-cooling}
\gamma_{cut}(t)=
\frac{\gamma_{cut}}
     {1+
     \frac{\sigma_T B0^2}
          {6 m_e c\pi (f) }
    \gamma_{cut}
    t_0^{1-f}
    (t^{f} -t_{inj}^{f})}
\end{equation}$$

where $f=1 - 2 m_{jet}$, and $t_0=z_0/\beta_{jet}c\Gamma_{jet}$, $t_{inj}=z_{inj}/\beta_{jet}c\Gamma_{jet}$ and $t=z_/\beta_{jet}c\Gamma_{jet}$, are the comoving time scales. We freeze a starting value of $z_{inj}=z_{acc}^{start}\approx 2.5 \times 10^{10}$ cm.

Another effect to take into account is the fact that for $z>z_{acc}$ the structure of the jet could change, for this reason we leave free the parameters $m_{jet}$ with a fit boundary of \[0.5,1.5\], with an initial value of 1.18, that is slightly larger than the value used for the phenomenological constraining, but gives a better agreement with radio-to-optical data.

The density of emitters at the base of the `RadioJet`, is bound to be equal to the density of emitters in the acceleration region $N_e$ calculated according to Eq. [\[Eq-jet-ballistic\]](#Eq-jet-ballistic), at $z=z_{radio}^{start}$, by fixing $N_{frac}=1.0$. We fix the values of $K_{R}^{end}=3000$ and of $K_{R}^{start}=1$.

A list of the free and frozen and of the bounds is reported in Table [\[best-fit-table\]](#best-fit-table) in the columns ‘staring values’, ‘fit boundaries’, respectively.

### Model fit results for the Disk and Corona emission

We fit first the `DiskIrrComp` and `Comp. hump` components restricting the fit range to $\nu$= $[5\times 10^{14},10^{20}]$ Hz and we get $\chi^2 =152$ for 98 degree of freedom ($N_{dof}$), corresponding to reduced $\chi^2_{red}=1.55$. The parameters values are reported in the upper part of Table [\[best-fit-table\]](#best-fit-table).

The best-fit parameters resulting from `JetSeT` are similar to those obtained form the `XSPEC` analysis for the `diskir` model. In particular the $r_{out}$ value ($3.58 \times 10^3 R_{in}$ and $3.45 \times 10^3 R_{in}$) and $L_C / L_D$ (4.1 and 4.6), for `JetSeT` and `XSPEC` respectively. The $f_{out}$ parameter, is unconstrained both for `XSPEC` and the `JetSeT`. However, a well constrained value is obtained when the jet component is added as shown in section [4.3.3](#model-fit-jet). Because the `JetSeT` model for the Comptonized emission is phenomenological, the high-energy range of the irradiated disk is fit as a cutoff power-law and thus is not directly comparable to the `diskir` parameters. For that portion of the spectrum, `JetSeT` found $\Gamma = 1.64$ (compared to 1.78 from `diskir`) and $E_C = 150$ keV (compared to $kT_e = 58$ keV from `diskir`). We do note that $E_C / kT_e \approx 2.6$, which falls within the predicted range of ratios between cutoff energy and electron temperature (cite: 2000ApJ...540..131P; 2001ApJ...556..716P), suggesting that the values are in agreement, even though the incertitude on the `JetSeT` value is quite large.

### Model fit results for the jet emission

To fit the full band SED we freeze all the parameters in the `CompHump` and `DiskIrrComp` components, except for $r_{out}$, $f_{out}$, and $L_C / L_D$, and we fit the global model over the full SED band in the range $\nu$= $[5\times 10^{8},10^{20}]$ Hz .

The model fit converged with a final $\chi^2 = 181$ for 122 degree of freedom ($N_{dof}$), corresponding to a $\chi^2_{red}=1.48$. The parameters values are reported in the bottom part of Table [\[best-fit-table\]](#best-fit-table), and the parameters derived from the best-fit model are reported in Table [5](#model-fit-derived-table). Regarding the `DiskIrrComp`, we note that adding the jet component results in a better constraint on the value of $f_{out}$=$(7.33\pm0.15)\times10^{-3}$, that is in the expected range of other black hole binaries in the hard state (cite: DiskIrrModel2009). Moreover, restricting the fit statistics to the same interval used in the `XSPEC` analysis, we get a $\chi^2 = 157$ with $N_{dof}=107$, corresponding to a $\chi^2_{red}=1.6$. Regarding the jet component, we note that final best-fit model parameters did not change significantly from the input values, suggesting that the phenomenological setup was able to find a configuration very close to the optimal one, even though the fit might be biased by the degeneracy among some parameters. We will investigate this problem in a forthcoming work (cite: TramacereInPrep), by means of Bayesian approach based on the MCMC technique. In general, we find that our assumption based on the connection between a compact acceleration region feeding the extended radio jet is able to model self-consistently the UV-to-optical emission, reproducing the observed flat radio spectrum. In particular, we find that, according to our best fit model, the particles in the radio region reach the asymptotic value of $\gamma_{cut} \approx 8$, and keep it almost constant as result of the decrease in the cooling synchrotron cooling rate due to the jet expansion. This behaviour is in agreement with the results of (cite: Peer2009) and (cite: Kaiser2006) for the case of synchrotron cooling dominating over the adiabatic one. It is worth discussing some specific parameters in detail:

+----------------------------------------------------------------------------------------+
|                                                                                        |
+:=======================+:============:+:======================:+:=====================:+
| par. name              | units        | value                  | setup value           |
+------------------------+--------------+------------------------+-----------------------+
| $q_{jet}$              |              | $>0.15$                | 0.20                  |
+------------------------+--------------+------------------------+-----------------------+
| $U_e/U_B$              |              | 0.18                   | –                     |
+------------------------+--------------+------------------------+-----------------------+
| $N^{acc}_e/N_p^{cold}$ |              | $<94$                  | –                     |
+------------------------+--------------+------------------------+-----------------------+
| $L_{jet}^{acc}$        | erg s$^{-1}$ | $>8.0  \times 10^{37}$ | –                     |
+------------------------+--------------+------------------------+-----------------------+
| $L_{rad}^{acc}$        | erg s$^{-1}$ | $1.1   \times 10^{36}$ | –                     |
+------------------------+--------------+------------------------+-----------------------+
| $L_{B}^{acc}$          | erg s$^{-1}$ | $3.6   \times 10^{37}$ | $3.6 \times 10^{37}$  |
+------------------------+--------------+------------------------+-----------------------+
| $L_{e}^{acc}$          | erg s$^{-1}$ | $6.6   \times 10^{36}$ | –                     |
+------------------------+--------------+------------------------+-----------------------+
| $L_{p}^{acc}$          | erg s$^{-1}$ | $>3.6  \times 10^{37}$ | $>3.6 \times 10^{37}$ |
+------------------------+--------------+------------------------+-----------------------+

: Model parameters evaluated from the best-fit model

- $q_{jet} > 0.15$. This value is compatible with the input value $q_{jet}=0.2$. As already discussed in the previous section, the $q_{jet}$ parameter is not linked directly to the accretion efficiency because the jet powering could, in principle, be supported also by other mechanisms such as the Blandford–Znajek mechanism (cite: BZ1977), that takes into account advection of magnetic flux from an accretion disk surrounding the Black Hole. Hence, our $q_{jet}$ parameter can not be used to infer or constrain the accretion efficiency.

- $U_e/U_B=0.18$. The $U_e/U_B$ is not far from equipartition, and it is obtained without providing any constraint. This proves that the combination of the phenomenological model setup and the minimization of the global model converged naturally toward a configuration close to the physical equipartition of $U_e$ and $U_B$, giving further support to the choice of a compact acceleration region that is connecting the pre-acceleration region to the radio jet.

- $N^{acc}_e/N_p^{cold}<94$. Since our model is leptonic, the content of cold protons can be derived from ancillary conditions, as the condition that the magnetic energy of the jet has to be in subequipartition with the bulk kinetic energy of the cold protons, in order to allow the mechanical compressibility of the plasma (cite: Kossimarov2007), and formation of shocks/turbulent acceleration sites in the acceleration region. From the best fit model we get that to respect the condition $\rho^{acc}_{p,B}>1.0$ we need to impose a lower limit of the ratio of relativistic electrons to cold protons $N_e/N_p^{cold}<112$. This value is compatible with the usual value of $N_e/N_p^{cold}=10$ (cite: Celotti2008) used in the case of relativistic jets with a leptonic radiative domination. Moreover, we note that the value of $B_{acc}$ obtained from the best fit did not require a significant change in the value of $L_B$ as derived from the phenomenological model setup, and demonstrating that constraining $z_{acc}$ based on the value of $\nu_{t}$ is naturally in agreement with formation of mechanical compression in the jet when $U_p>U_B$.

- $m_{jet}=1.2$. The value of $m_{jet}$ is one the most critical, indeed it dictates the topology and intensity of the magnetic field beyond the acceleration region, and it is interesting to compare to the value of $m_B$ that is used to model the jet below the acceleration region. The initial guess based on the value of $\alpha_{R}$ has required a small modification in order to reproduce the observed radio spectrum, and the final model naturally explains the almost flat radio spectrum as emission of the cooled electron leaving the acceleration region.

# Discussion and Conclusions

As MAXI J$1820+070$ was observed numerous times across the EM spectrum during its outburst, there are multiple works relevant to portions of our multi-wavelength analysis, though to date none study the source in such a complete picture as is presented with our model from `JetSeT`.

(cite: 2018ApJ...868...54S) provides the most direct comparison to the analysis in this work, though the source behavior is different before and after 26 March (MJD 58206). They found that the optical and near-IR emission is not entirely from disk emission and thus included a power-law to their `diskir` model with a spectrum described by fixed parameters $kT_{disk} = 0.35$ keV, $L_C/L_D = 70$, $f_{out} = 5 \times 10^{-3}$, and $R_{out} = 10^5 R_{in}$. Our fit found a considerably lower $kT_{disk}$ (0.12 keV), $L_C/L_D$ (4.7), and $R_{out}$ ($10^3 R_{in}$), but a higher $f_{out}$ ($4 \times 10^{-2}$). We note that the source behavior between the two observations is different with changes in the spectral hardness in hard X-rays (cite: 2019ApJ...870...92R), the development of type-C QPOs (cite: 2020ApJ...889..142S), and a reduction in the size of the corona (cite: 2019Natur.565..198K) that can possibly explain the differences.

Following the work of (cite: 2019ApJ...879L...4M), we explored the presence of disk wind signatures in our VLT/X-shooter optical spectrum, as this data-set falls between epochs 11 and 12 of (cite: 2019ApJ...879L...4M) campaign and adds an epoch in their uncovered time window (between 26 March and 23 April). We focus our spectral analysis on the He I $\lambda$ 5876, He I $\lambda$ 6678 and H$\alpha$ wavelength regions. We found shallow p-cygni profiles and strong line asymmetries in all the three mentioned lines, while a broad outflow component is detected only in the red wing of the H$\alpha$. Among the observed absorption troughs, the one detected in the blue wing of He I $\lambda$ 5876 is the more prominent and it results in a terminal wind velocity $v_{t}$=880 km/s, which is consistent with the outflow velocity of $v\sim$900 km/s, derived from the H$\alpha$ redshifted broad component.

These properties indicate that at this epoch optical disk winds are still present, although with slower velocities with respect to what found in (cite: 2019ApJ...879L...4M). The author also report an evolution of the line profiles during their monitoring campaign and our observation confirms this trend. In particular the observed H$\alpha$ profile can be interpreted as a continuation in the evolving pattern of the line between the epochs 9 and 12 shown in Figure 2 of (cite: 2019ApJ...879L...4M). Similar spectral variations were previously reported by (cite: 2018ApJ...867L...9T) and ascribed to the orbital motion of the system. Interestingly, some of the most conspicuous optical wind detections in (cite: 2019ApJ...879L...4M) occur in epochs corresponding to the hard state of the source, when radio emission and strong jet activity are present (cite: 2020NatAs.tmp....2B) and the peak of the optical outburst of the source is reported. This led the authors to the conclusion that the optical wind detected in MAXI J$1820+070$ is simultaneous with the jet. Our wind signatures detection, together with the results from our broad band spectral analysis are consistent with this scenario.

Our phenomenological analysis of the compact jet found the data could be modelled by a broken power-law with $\alpha_{thick}=0.28\pm0.02$ and $\alpha_{thin}=-0.61\pm0.01$. Combining observations from late March and early April, (cite: 2018ATel11533....1R) performed a similar analysis and found spectral indices of $\alpha_{thick} \sim 0.3$ and $\alpha_{thin} \sim -0.7$. Building on (cite: 2018ATel11533....1R), (cite: 2018ApJ...868...54S) estimated a transition frequency of $\sim 3\times 10^{13}$ Hz and a corresponding flux density of $\sim 0.4$ Jy. From these values they determined $B \sim 1 \times 10^4$ G and $R \sim 2 \times 10^9$ cm using equations from (cite: 2011PASJ...63S.785S). Our model peaks at 1.6$\pm$0.2$\times10^{13}$ Hz with a flux density of $\sim 0.35$ Jy thus resulting in similar values.

These values are in agreement with the phenomenological setup and with the best-fit model from `JetSeT`. In particular the `JetSeT` best-fit model gives a magnetic field in the acceleration region of $\approx 1.8 \times 10^4$ G, and a region radius of $\approx 2.6 \times 10^9$ cm.

The corresponding energy density of the magnetic field is $\approx 1.3\times10^7 \textrm{ erg/cm}^3$ compared to the values of $8 \times 10^6 \textrm{erg/cm}^3$ from (cite: 2018ApJ...868...54S).

Additionally, we identify a separate radio spectral components at frequencies below $\sim$10 GHz, showing an inverted power-law spectrum with slope $\alpha=0.11\pm0.02$. (cite: 2020NatAs.tmp....2B), collecting data from different epochs of VLA, Multi-Element Radio Linked Interferometer Network (eMERLIN), and Meer Karoo Array Telescope (MeerKAT) observations, could identify at least one ejected component during the transition from the hard to the soft state (mid-June to mid-September 2018). Though the source is unresolved down to a sub-arcsec resolution in the VLA observations considered here (collected in a previous epoch), the presence of an additional low-frequency spectral component could suggest that the ejecta later detected by (cite: 2020NatAs.tmp....2B) were already present at a sub-pc scale during the April 12th 2018 epoch considered here.

This component is represented in the `JetSeT` broadband model by the `RadioJet` component, and stems naturally from the cooling of the accelerated particle leaving the acceleration region. Interestingly we find that the best-fit index $m_{jet}\approx 1.2$ predicts a radio spectral index of $\alpha=1-1/m_{jet}\approx 0.166$ that is close to the value found in the power-law fit. We note, that the small difference between the two values, is due to the fact the `JetSeT``RadioJet` model takes into account the data range from radio-to-mm frequencies, differently from the power-law fit, whose range extends up $\approx 10^{10}$ Hz.

In conclusion, our broadband analyses of MAXI J$1820+070$ found the source in a hard state with parameters similar to what was reported by (cite: 2018ApJ...868...54S) The `JetSeT` broadband model was able to reproduce the full SED taking into account both the disk/corona emission, and the leptonic radiativelly dominated relativistic jet contribution. We found that the relativistic jet required a total energy of $L_{jet}\geq 8.0\times10^{37}$ erg/s, corresponding to 0.15 $L_{Edd}$. This value represents a lower limit, since we assume that the hadronic content of the jets is only in terms of cold protons, without a significant radiative contribution. The flat radio spectral shape stems naturally from the synchroton cooling of the electrons in the acceleration regions, in agreement with previous analyses (cite: Kaiser2006; Peer:2009). In comparison, the accretion luminosity ($6 \times 10^{37}$ erg/s) is comparable to the lower limit of the jet luminosity. Thus in MAXI J$1820+070$, it is possible for the jet to be powered predominately via accretion with only a small contribution from the Blanford-Znajek mechanism, which in this case cannot provide much power since the black hole spin is reported to be low (cite: Bassi2020; Zhao2020).

# Acknowledgments

We thank the Italian node of the European ALMA Regional Centre (ARC) for the support.

JR and GB acknowledge financial support under the INTEGRAL ASI-INAF agreement 2019-35-HH.0 and ASI/INAF n. 2017-14-H.0. FO acknowledge the support of the H2020 European Hemera program, grant agreement No 730970. The research leading to these results has received funding from the European Union’s Horizon 2020 Programme under the AHEAD2020 project (grant agreement n. 871158) F.O. acknowledges the support of the H2020 European Hemera program, grant agreement No 730970, and the support of the GRAWITA/PRIN-MIUR project: "*The new frontier of the Multi-Messenger Astrophysics: follow-up of electromagnetic transient counterparts of gravitational wave sources*". Based on observations with INTEGRAL, an ESA project with instruments and science data centre funded by ESA member states (especially the PI countries: Denmark, France, Germany, Italy, Switzerland, Spain) and with the participation of Russia and the USA.

This research has made use of the services of the ESO Science Archive Facility. Based on observations collected at the European Southern Observatory under ESO programmes 2017.1.01103.T (ALMA) and 0101.D-0356(A) (VLT). ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in co- operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

natexlab

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Bassi2020) Bassi, T., Malzac, J., Del Santo, M. et al. 2020, MNRAS, 494, 571 doi: [`10.1093/mnras/staa739`](http://doi.org/10.1093/mnras/staa739)

(ref: BBR) Begelman, M. C., Blandford, R. D., & Rees, M. J. 1984, Rev. Mod. Phys., 56, 255, doi: [`10.1103/RevModPhys.56.255`](http://doi.org/10.1103/RevModPhys.56.255)

(ref: BZ1977) Blandford, R. D., & Znajek, R. L. 1977, MNRAS, 179, 433, doi: [`10.1093/mnras/179.3.433`](http://doi.org/10.1093/mnras/179.3.433)

(ref: 2018MNRAS.478.1512B) Bonato, M., Liuzzo, E., Giannetti, A., et al. 2018, MNRAS, 478, 1512, doi: [`10.1093/mnras/sty1173`](http://doi.org/10.1093/mnras/sty1173)

(ref: 2020NatAs.tmp....2B) Bright, J. S., Fender, R. P., Motta, S. E., et al. 2020, Nature Astronomy, doi: [`10.1038/s41550-020-1023-5`](http://doi.org/10.1038/s41550-020-1023-5)

(ref: cardelli89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](http://doi.org/10.1086/167900)

(ref: Celotti2008) Celotti, A., & Ghisellini, G. 2008, MNRAS, 385, 283, doi: [`10.1111/j.1365-2966.2007.12758.x`](http://doi.org/10.1111/j.1365-2966.2007.12758.x)

(ref: 2016SPIE.9906E..5BC) Clarke, T. E., Kassim, N. E., Brisken, W., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9906, Proc. SPIE, 99065B, doi: [`10.1117/12.2233036`](http://doi.org/10.1117/12.2233036)

(ref: Flewelling2016) Flewelling, H. A., Magnier, E. A., Chambers, K. C., et al. 2016, arXiv e-prints, arXiv:1612.05243. [`https://arxiv.org/abs/1612.05243`](https://arxiv.org/abs/1612.05243)

(ref: 2003MNRAS.344...60G) Gallo, E., Fender, R. P., & Pooley, G. G. 2003, MNRAS, 344, 60, doi: [`10.1046/j.1365-8711.2003.06791.x`](http://doi.org/10.1046/j.1365-8711.2003.06791.x)

(ref: Ghisellini2013) Ghisellini, G. 2013, Radiative Processes in High Energy Astrophysics, Vol. 873, doi: [`10.1007/978-3-319-00612-3`](http://doi.org/10.1007/978-3-319-00612-3)

(ref: DiskIrrModel2009) Gierliński, M., Done, C., & Page, K. 2009, Monthly Notices of the Royal Astronomical Society, 392, 1106

(ref: Kaiser2006) Kaiser, C. R. 2006, Monthly Notices of the Royal Astronomical Society, 367, 1083

(ref: 2019Natur.565..198K) Kara, E., Steiner, J. F., Fabian, A. C., et al. 2019, Nature, 565, 198, doi: [`10.1038/s41586-018-0803-x`](http://doi.org/10.1038/s41586-018-0803-x)

(ref: 2018ATel11399....1K) Kawamuro, T., Negoro, H., Yoneyama, T., et al. 2018, The Astronomer’s Telegram, 11399, 1

(ref: Kossimarov2007) Komissarov, S. S., Barkov, M. V., Vlahakis, N., & Königl, A. 2007, MNRAS, 380, 51, doi: [`10.1111/j.1365-2966.2007.12050.x`](http://doi.org/10.1111/j.1365-2966.2007.12050.x)

(ref: 2003MNRAS.345.1057M) Merloni, A., Heinz, S., & di Matteo, T. 2003, MNRAS, 345, 1057, doi: [`10.1046/j.1365-2966.2003.07017.x`](http://doi.org/10.1046/j.1365-2966.2003.07017.x)

(ref: 1992Natur.358..215M) Mirabel, I. F., Rodriguez, L. F., Cordier, B., Paul, J., & Lebrun, F. 1992, Nature, 358, 215, doi: [`10.1038/358215a0`](http://doi.org/10.1038/358215a0)

(ref: 2019ApJ...879L...4M) Muñoz-Darias, T., Jiménez-Ibarra, F., Panizo-Espinar, G., et al. 2019, ApJL, 879, L4, doi: [`10.3847/2041-8213/ab2768`](http://doi.org/10.3847/2041-8213/ab2768)

(ref: Peer:2009) Pe’er, A., & Casella, P. 2009a, Astrophysical Journal, 699, 1919

(ref: Peer2009) —. 2009b, Astrophysical Journal, 699, 1919

(ref: 2000ApJ...540..131P) Petrucci, P. O., Haardt, F., Maraschi, L., et al. 2000, ApJ, 540, 131, doi: [`10.1086/309319`](http://doi.org/10.1086/309319)

(ref: 2001ApJ...556..716P) —. 2001, ApJ, 556, 716, doi: [`10.1086/321629`](http://doi.org/10.1086/321629)

(ref: 2018ATel11540....1P) Polisensky, E., Giacintucci, S., Peters, W. M., Clarke, T. E., & Kassim, N. E. 2018, The Astronomer’s Telegram, 11540, 1

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2019ApJ...870...92R) Roques, J.-P., & Jourdain, E. 2019, ApJ, 870, 92, doi: [`10.3847/1538-4357/aaf1c9`](http://doi.org/10.3847/1538-4357/aaf1c9)

(ref: 2013MNRAS.429..815R) Russell, D. M., Markoff, S., Casella, P., et al. 2013, MNRAS, 429, 815, doi: [`10.1093/mnras/sts377`](http://doi.org/10.1093/mnras/sts377)

(ref: 2018ATel11533....1R) Russell, D. M., Baglio, M. C., Bright, J., et al. 2018, The Astronomer’s Telegram, 11533, 1

(ref: Ryb1986) Rybicki, G. B., & Lightman, A. P. 1986, Radiative Processes in Astrophysics

(ref: Schlafly11) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103, doi: [`10.1088/0004-637X/737/2/103`](http://doi.org/10.1088/0004-637X/737/2/103)

(ref: 2014ApJ...788...48S) Shappee, B. J., Prieto, J. L., Grupe, D., et al. 2014, ApJ, 788, 48, doi: [`10.1088/0004-637X/788/1/48`](http://doi.org/10.1088/0004-637X/788/1/48)

(ref: 2011PASJ...63S.785S) Shidatsu, M., Ueda, Y., Tazaki, F., et al. 2011, PASJ, 63, S785, doi: [`10.1093/pasj/63.sp3.S785`](http://doi.org/10.1093/pasj/63.sp3.S785)

(ref: 2018ApJ...868...54S) Shidatsu, M., Nakahira, S., Yamada, S., et al. 2018, ApJ, 868, 54, doi: [`10.3847/1538-4357/aae929`](http://doi.org/10.3847/1538-4357/aae929)

(ref: 2020ApJ...889..142S) Stiele, H., & Kong, A. K. H. 2020, ApJ, 889, 142, doi: [`10.3847/1538-4357/ab64ef`](http://doi.org/10.3847/1538-4357/ab64ef)

(ref: jetsetascl) Tramacere, A. 2020, JetSeT: Numerical modeling and SED fitting tool for relativistic jets. [`http://ascl.net/2009.001`](http://ascl.net/2009.001)

(ref: TramacereInPrep) Tramacere, A. in prep.

(ref: Tramacere2009) Tramacere, A., Giommi, P., Perri, M., Verrecchia, F., & Tosti, G. 2009, A&A, 501, 879, doi: [`10.1051/0004-6361/200810865`](http://doi.org/10.1051/0004-6361/200810865)

(ref: Tramacere2011) Tramacere, A., Massaro, E., & Taylor, A. M. 2011, ApJ, 739, 66, doi: [`10.1088/0004-637X/739/2/66`](http://doi.org/10.1088/0004-637X/739/2/66)

(ref: 2018ATel11539....1T) Trushkin, S. A., Nizhelskij, N. A., Tsybulev, P. G., & Erkenov, A. 2018, The Astronomer’s Telegram, 11539, 1

(ref: 2018ApJ...867L...9T) Tucker, M. A., Shappee, B. J., Holoien, T. W. S., et al. 2018, ApJL, 867, L9, doi: [`10.3847/2041-8213/aae88a`](http://doi.org/10.3847/2041-8213/aae88a)

(ref: Ubertini2003) Ubertini, P., Lebrun, F., Di Cocco, G., et al. 2003, A&A, 411, L131, doi: [`10.1051/0004-6361:20031224`](http://doi.org/10.1051/0004-6361:20031224)

(ref: vernet11) Vernet, J., Dekker, H., D’Odorico, S., et al. 2011, A&A, 536, A105, doi: [`10.1051/0004-6361/201117752`](http://doi.org/10.1051/0004-6361/201117752)

(ref: Romero2010) Vila, G. S., & Romero, G. E. 2010, Monthly Notices of the Royal Astronomical Society, 403, 1457

(ref: Zdziarski2009) Zdziarski, A. A., Malzac, J., & Bednarek, W. 2009, MNRAS, 394, L41, doi: [`10.1111/j.1745-3933.2008.00605.x`](http://doi.org/10.1111/j.1745-3933.2008.00605.x)

(ref: Zhao2020) Zhao, X., Gou, L., Dong, Y. et al. 2020, arXiv e-prints, arXiv:2012.05544

[^1]: http://www.astronomy.ohio-state.edu/asassn/transients.html

[^2]: <https://jetset.readthedocs.io/en/latest/>

[^3]: [https://casa.nrao.edu](#https://casa.nrao.edu)

[^4]: https://www.cosmos.esa.int/web/xmm-newton/sas-threads

[^5]: [https://www.isdc.unige.ch/integral/analysis](#https://www.isdc.unige.ch/integral/analysis)

[^6]: https://www.isdc.unige.ch/integral/analysis

[^7]: <https://jetset.readthedocs.io/en/latest/>

</paper>

## Items to check

```json
[
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Reduction of XMM-Newton EPIC-pn data",
  "failed_quote": "using the Science Analysis System (SAS) software version `xmmsas_20190531_1155-18.0.0`"
 }
]
```
