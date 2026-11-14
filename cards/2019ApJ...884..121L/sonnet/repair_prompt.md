# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...884..121L\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# A Reverse Shock in GRB 181201A

## Abstract

We present comprehensive multiwavelength radio to X-ray observations of GRB 181201A spanning from $\approx150$ s to $\approx163$ days after the burst, comprising the first joint ALMA–VLA–GMRT observations of a gamma-ray burst (GRB) afterglow. The radio and millimeter-band data reveal a distinct signature at $\approx3.9$ days, which we interpret as reverse-shock (RS) emission. Our observations present the first time that a single radio-frequency spectral energy distribution can be decomposed directly into RS and forward shock (FS) components. We perform detailed modeling of the full multiwavelength data set, using Markov Chain Monte Carlo sampling to construct the joint posterior density function of the underlying physical parameters describing the RS and FS synchrotron emission. We uncover and account for all discovered degeneracies in the model parameters. The joint RS–FS modeling reveals a weakly magnetized ($\sigma\approx3\times10^{-3}$), mildly relativistic RS, from which we derive an initial bulk Lorentz factor of $\Gamma_0\approx103$ for the GRB jet. Our results support the hypothesis that low-density environments are conducive to the observability of RS emission. We compare our observations to other events with strong RS detections and find a likely observational bias selecting for longer lasting, non-relativistic RSs. We present and begin to address new challenges in modeling posed by the present generation of comprehensive, multifrequency data sets.

NHFP Einstein Fellow

# Introduction

Long-duration gamma-ray bursts, produced in the core collapse of massive stars, host the most energetic and most highly relativistic jets in the universe (cite: mr93; rm94; fkn+97; wb06). However, the nature of the central engine, as well as the mechanism by which these jets are launched and collimated, remain poorly understood (cite: mes06). Probing the nature of the central engine, such as magnetars or an accreting black hole, requires foremost determining the energetics and composition of the GRB jets themselves (cite: mgt+11; lcj17). Unfortunately, the forward shock (FS) synchrotron ‘afterglow’ emission, produced by the interaction of the jet with the environment, is insensitive to the properties of GRB jets; instead, the baryon content, initial bulk Lorentz factor, and magnetization of the ejecta can be studied by capturing emission from the reverse shock (RS), produced in the jet during its rapid deceleration by the ambient medium (cite: spn98; pk00; gk03; gt05; zk05).

Strong RSs are expected in ejecta where the magnetic field is dynamically unimportant, and the ratio of the magnetic energy density to the bulk kinetic energy $\sigma\lesssim1$. On the other hand, highly magnetized outflows are expected to produce weak RS emission (cite: zk05; mkp06; lcj17). The expected signature of RS radiation comprises a characteristic synchrotron spectrum superposed on the afterglow emission (cite: kob00), resulting in a flash beginning in the optical and typically lasting a few tens of seconds to minutes, and which rapidly cascades to radio frequencies, where it typically lasts a few days (cite: abb+99; sp99a; np04).

Recent multiwavelength observations have unequivocally isolated excess radio emission attributable to the RS, and a careful decomposition of the observed multifrequency (radio to X-ray) spectral energy distribution (SED) at different epochs into FS and RS contributions has allowed the first inferences of the Lorentz factor and magnetization of GRB jets (cite: lbz+13; pcc+14; vdhpdb+14; lab+16; alb+17; lbm+18; lab+18). These works have usually provided point estimates on the RS parameters with no uncertainty estimates, owing to limitations of the modeling process.

Here, we present multiwavelength observations of GRB 181201A spanning from $\approx150$ s to $\approx163$ days after the burst at 35 frequencies from $6\times10^{8}$ Hz to $3\times10^{17}$ Hz, including the first joint Giant Meterwave Radio Telescope (GMRT), Karl G. Jansky Very Large Array (VLA), and Atacama Large Millimeter/submillimeter Array (ALMA) data set (Section [2](#text:obs_basic)). Our radio and millimeter-band observations reveal an RS spectral peak superposed on the FS emission, which we are able to decompose into RS and FS components in a single radio SED for the first time (Section [3](#text:basic)), while using the optical and X-ray observations to constrain the nature of the circumburst environment. We fit the entire multiwavelength dataset simultaneously to derive the properties of the RS and FS emission, and demonstrate that the two components are consistent with emission from a double-shock system (Section [4](#text:multimodel)). We use this decomposition to derive the initial Lorentz factor and magnetization of the ejecta using full statistical modeling. We conclude with a detailed discussion of the results, placed in context of other GRBs with multiwavelength RS detections (Section [5](#text:discussion)). Unless otherwise stated, all uncertainties are reported at the $1\sigma$ level, and all magnitudes are in the AB system and not corrected for Galactic extinction. We employ the $\Lambda$CDM cosmological parameters of $\Omega_m=0.31$, $\Omega_{\Lambda}=0.69$, and $H_0=68$ km s$^{-1}$ Mpc$^{-1}$ throughout.

# Observations and Data Analysis

GRB 181201A was discovered by the IBIS and ISGRI instruments on board the *INTEGRAL* satellite on 2018 December 1 at 02:38 UT (cite: gcn23469). The burst, which lasted $\approx180$ s, saturated the telemetry, and hence only a lower limit to its $\gamma$-ray flux is available from *INTEGRAL*. The GRB was also detected by the *Fermi* Large Area Telescope (LAT) beginning at 02:38:00 UT (cite: gcn23480), by *Konus*-Wind at 02:39:52.36 UT with a burst duration of $\approx172$ s (cite: gcn23495), and by *Astrosat* with a duration of $T_{90}\approx19.2$ s (cite: gcn23501). We take the *Fermi* and *INTEGRAL* time as $T_0$ for this burst, and reference all times hereafter to this $T_0$. The time-averaged *Konus*-Wind spectrum in the 20 keV–10 MeV energy range can be fit with a Band model, with low-energy photon index $\alpha_{\gamma} = -1.25\pm0.05$, high-energy photon index $\beta = 
-2.73_{-0.12}^{+0.11}$, peak energy $E_{\gamma,\rm peak} = (152\pm6)$ keV, and a fluence of $(1.99\pm0.06)\times10^{-4}$ erg cm$^{-2}$ (cite: gcn23495).

The optical afterglow was discovered in MASTER (cite: lkg+10) Global Robotic Net observations (cite: gcn23470) 10 s after the *INTEGRAL* alert and later by the *Swift* UV/optical telescope (cite: rkm+05; gcn23499). Spectroscopic observations with the Very Large Telescope at the European Southern Observatory yielded a redshift of $z=0.450$ based on identification of the Mg II doublet (cite: gcn23488). At this redshift, the *Konus*-Wind spectrum implies an isotropic-equivalent $\gamma$-ray energy of $E_{\gamma,\rm iso}=(1.20\pm0.04)\times10^{53}$ erg, This value is consistent with the GRB $E_{\rm peak}$-$E_{\gamma,\rm iso}$ relation (cite: ama06), suggesting that the prompt $\gamma$-ray emission in GRB 181201A is typical among the GRB population.

## X-ray: Swift/XRT

The *Swift* X-ray Telescope (cite: bhn+05) began observing GRB 181201A 0.16 days after the burst, and detected a fading X-ray afterglow at RA = $21^{\rm h}17^{\rm m}11{\rlap.}^{\rm 
s}$20, Dec = -12$^\circ$ 37$'$ 50.9$''$ (J2000), with an uncertainty radius of 1.4$''$ (90% containment)[^1]. XRT continued observing the afterglow for $20$ d in photon counting mode. The GRB entered a Sun constraint for *Swift* at $\approx21$ days after the burst and was dropped from the *Swift* schedule. We obtained 4.4 ks of *Swift* ToO observations on 2019 April 7 ($\approx 127$ days), when it was visible again. The X-ray afterglow was weakly detected. The data were automatically calibrated using the XRT pipeline and incorporated into the on-line light curve. We use a photon index of $\Gamma_{\rm X}\approx1.77$ and an unabsorbed counts-to-flux conversion rate from the *Swift* website of $4.75\times10^{-11}$ erg ${\rm cm}^{-2}$ ct$^{-1}$ to convert the 0.3–10 keV count rate light curve[^2] to flux density at 1 keV for subsequent analysis.

|                |       |                     |                     |            |
|:--------------:|:------|:-------------------:|:-------------------:|:----------:|
|   Mid-time,    | UVOT  |    Flux density     |     Uncertainty     | Detection? |
| $\Delta t$ (d) | band  |        (mJy)        |        (mJy)        |  (1=Yes)   |
|     0.176      | *uw2* | $6.19\times10^{-1}$ | $2.92\times10^{-2}$ |     1      |
|     0.246      | *uw2* | $4.61\times10^{-1}$ | $2.17\times10^{-2}$ |     1      |
|     0.302      | *uw2* | $3.31\times10^{-1}$ | $1.88\times10^{-2}$ |     1      |
|       …        | …     |          …          |                     |            |

: *Swift* UVOT Observations of GRB 181201A

Table notes: This is a sample of the full table available on-line.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $\Delta t$ | Observatory | Instrument | Filter | Frequency | Flux density | Uncertainty | Detection? | Reference |
| \(d\) |  |  |  | (Hz) | (mJy) | (mJy) | 1=Yes |  |
| $1.81\times10^{-3}$ | MASTER-OAFA | MASTER | *CR* | $4.67\times10^{14}$ | $1.25\times10^{1}$ | $1.27\times10^{-1}$ | 1 | This work |
| $2.42\times10^{-3}$ | MASTER-OAFA | MASTER | *CR* | $4.67\times10^{14}$ | $2.85\times10^{1}$ | $1.58\times10^{-1}$ | 1 | This work |
| $3.46\times10^{-1}$ | iTelescope | T31 | *R* | $4.67\times10^{14}$ | $6.52\times10^{-1}$ | $1.83\times10^{-2}$ | 1 | (cite: gcn23475) |
| … | … | … | … | … | … | … | … | … |

: Optical and Near-IR Observations of GRB 181201A

Table notes: The data have not been corrected for Galactic extinction. This is a sample of the full table available on-line.

## UV, optical, and near-IR

We derived aperture photometry from pipeline processed UVOT images downloaded from the *Swift* data center[^3] with the uvotproduct (v2.4) software. We used a circular source extraction region with a 3.5$''$ radius, followed by an aperture correction based on the standard 5$''$ aperture for UVOT photometry (cite: pbp+08). We present our UVOT measurements in Table [1](#tab:data:UVOT).

Four MASTER-net observatories (MASTER-Kislovodsk, MASTER-IAC, MASTER-SAAO, and MASTER-OAFA) participated in rapid-response and follow-up observations of GRB181201A, beginning with 10 s exposures at 02:40:30 UT on 2019 December 1, $\approx150$ s after the burst and 10 s after the *INTEGRAL* alert in $BVRI$ and Clear bands[^4] (cite: gcn23470). The MASTER auto-detection system (cite: lkg+10; lvg+19) discovered a bright optical afterglow at RA = $21^{\rm h}17^{\rm 
m}11{\rlap.}^{\rm s}$20, Dec = -12$^\circ$ 37$'$ 51.4$''$ (J2000) with unfiltered magnitude $\approx13.2$ mag (Vega). MASTER follow-up observations continued until $\approx3$ days after the burst. We carried out astrometry and aperture photometry (using a $\approx2.5\ensuremath{''}$ aperture radius) for observations taken at each telescope separately, calibrated to 6 nearby SDSS reference stars. We verified our photometry by measuring the brightness of comparison stars with similar brightness as the afterglow, and incorporated the derived systematic calibration uncertainty into the photometric uncertainty (cite: tlm+17; lvg+19).

We observed the afterglow of GRB 181201A with the Gamma-Ray Burst Optical/Near-Infrared Detector (GROND) on the MPI/ESO 2.2m telescope in La Silla in Chile beginning 0.91 days after the burst in $g^{\prime}r^{\prime}i^{\prime}z^{\prime}JHK$ filters. We calibrated the data with tools and methods standard for GROND observations and detailed in (cite: kkysg+08). We performed aperture photometry calibrated against PanSTARRS field stars in the $g^{\prime}r^{\prime}i^{\prime}z^{\prime}$ filters and against the 2MASS catalog in $JHK$.

We observed the afterglow with the Ohio State Multi-Object Spectrograph (cite: msd+11) on the 2.4 m Hiltner telescope at MDM Observatory on 2018 December 04, with 120 s exposures each in the *BVRI* bands. We obtained two later epochs of imaging using the Templeton detector on the 1.3m McGraw-Hill telescope on the nights of 2018 December 9 and 10, obtaining $4\times300$ s each in $r^{\prime}$ and $i^{\prime}$ bands. Observations on December 10 were taken at a high airmass of 1.91 and under poor seeing. We performed aperture photometry with a 2$''$ aperture on the Hiltner and McGraw-Hill images, referenced to SDSS.

We obtained Liverpool Telescope (cite: ssr+04) imaging with the infrared/optical camera (IO:O) at $\approx2.7$ days, comprising $3\times120$ s exposures in $g^{\prime}r^{\prime}i^{\prime}$ bands. We performed aperture photometry using the Astropy Photutils package (cite: bsr+16) calibrated to SDSS. We also collected all optical photometry for this event published in GCN circulars. We present our combined optical and NIR data set in Table [2](#tab:data:opt).

|           |           |         |              |             |
|:---------:|:---------:|:-------:|:------------:|:-----------:|
| Telescope | Frequency |  Time   | Flux density | Uncertainty |
|           |   (GHz)   | (days)  |    (mJy)     |  ($\mu$Jy)  |
|   ALMA    |  $97.5$   | $0.885$ |    $3.41$    |    $23$     |
|   ALMA    |  $96.4$   | $1.92$  |    $1.99$    |    $25$     |
|    VLA    |  $2.73$   | $2.93$  |   $0.478$    |    $70$     |
|     …     |     …     |    …    |      …       |      …      |

: Radio and millimeter observations of GRB 181201A

Table notes: This is a sample of the full table available on-line.

## Millimeter: ALMA

We obtained 5 epochs of ALMA Band 3 (3 mm) observations of GRB 181201A spanning 0.88 days to 29.8 days after the burst through program 2018.1.01454.T (PI: Laskar). The observations utilized two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz, respectively, in the first epoch, and at 90.4 and 102.4 GHz in subsequent epochs. One of J2258-2758, J2148+0657, and J2000-1748 was used for bandpass and flux density calibration, while J2131-1207 was used for complex gain calibration in all epochs. We analyzed the data using the Common Astronomy Software Application (cite: mws+07) and the afterglow was well-detected in all epochs. We performed one round of phase-only self-calibration in the first two epochs, where the deconvolution residuals indicated the presence of phase errors. We list the results of our ALMA observations in Table [\[tab:data:radio\]](#tab:data:radio).

## Centimeter: VLA

We observed the afterglow using the VLA starting 2.9 d after the burst through programs 18A-088 and 18B-407 (PI: Laskar). We detected and tracked the flux density of the afterglow from 1.2 GHz to 37 GHz over multiple epochs until $\approx164$ d after the burst. We used 3C48 as the flux and bandpass calibrator and J2131-1207 as complex gain calibrator. Where phase errors appeared to be present after deconvolution, we performed phase-only self-calibration in epochs with sufficient signal-to-noise. The effect of self-calibration impacted the measured flux density by $\lesssim15\%$ and only at the highest frequencies ($\gtrsim15$ GHz). We carried out data reduction using CASA, and list the results of our VLA observations in Table [\[tab:data:radio\]](#tab:data:radio).

## Meter: uGMRT

We observed the afterglow using the upgraded Giant Meterwave Radio Telescope (uGMRT) through program 35_065 (PI: Laskar) starting 12.5 d and 13.5 d after the burst in Bands 4 (center frequency 550 MHz) and 5 (center frequency 1450 MHz), respectively. The observations utilized the full 400 MHz bandwidth of the uGMRT Wide-band Backend (GWB) system. We used 3C48 for bandpass and flux density calibration, and J2131-1207 for complex gain calibration. We carried out data reduction using CASA, and list the results of our uGMRT observations in Table [\[tab:data:radio\]](#tab:data:radio).

# Basic Considerations

We now interpret the X-ray to radio afterglow observations in the context of synchrotron emission arising from electrons accelerated to a non-thermal power-law distribution, $N_{\rm 
\gamma_{\rm e}}\propto \gamma_{\rm e}^{-p}$, in relativistic shocks produced by the interaction of the GRB jet with the circum-burst environment (cite: spn98). We assume the energy density of accelerated particles and that of the magnetic field downstream of the shock to be a fraction $\ensuremath{\epsilon_{\rm e}}$ and $\ensuremath{\epsilon_{\rm B}}$, respectively, of the shock kinetic energy density for a given total ejecta kinetic energy, $E_{\rm K,iso}$. The observed spectral energy distribution (SED) of each synchrotron component is described by three break frequencies (the self-absorption frequency, $\nu_{\rm a}$, the characteristic frequency, $\nu_{\rm m}$, and the cooling frequency, $\nu_{\rm c}$), and the flux density normalization, $F_{\nu,\rm m}$ (cite: gs02). The evolution of these quantities with time depends upon the radial density profile of the circum-burst medium, $\rho = 
AR^{-k}$, for which we consider two standard possibilities: a constant density ($k=0$, $A\equiv\ensuremath{n_{0}}
m_{\rm p}$; ISM) model (cite: spn98) and a wind-like ($k=2$, $A\equiv5\times10^{11}$g cm$^{-1}\ensuremath{A_{*}}$) environment (cite: cl00). We compute the resulting synchrotron spectra using the weighting prescription described in (cite: lbt+14) to generate smooth light curves at all observed frequencies.

## Radio/mm: presence of additional component

One of the most striking features of GRB 181201A revealed by our VLA and ALMA observations is a spectral bump in the cm to mm-band SED at 3.9 days (Fig. [1](#fig:4dsed)). The feature spans 3–24 GHz, and can be fit with a smoothly broken power law, with low-frequency index[^5], $\beta_1 = 1.43\pm0.23$, high-frequency index, $\beta_2 = -0.35\pm0.03$, break frequency, $\nu_{\rm 
peak}=5.5\pm0.4$ GHz, and peak flux density, $F_{\nu,\rm peak}=1.48\pm0.06$ mJy. The steeply rising spectrum below the spectral peak suggests the underlying emission is self-absorbed[^6]. Fitting the VLA cm-band data above 24 GHz and the ALMA observations at the same epoch with a single power law model yields $\beta_{\rm 24-ALMA}=0.09\pm0.02$.

The radio and millimeter SED at 3.9 days clearly exhibits two distinct components. The simplest explanation for multiple components in the radio is to attribute one to a RS and the other to a FS. Since the RS emission is expected to peak at lower frequencies than the FS and the RS spectrum is expected to cut off steeply above the RS cooling frequency (cite: kob00), the lower-peaking component is more naturally associated with RS emission.

The ALMA mm-band light curve can be fit with a single power law, with decay rate $\alpha_{\rm ALMA}=-0.71\pm0.01$ (Fig. [2](#fig:ALMAlc_pl)). From the radio SED at 3.9 days, we know that $\ensuremath{\nu_{\rm m,f}}> \nu_{\rm ALMA}$ at this time. In this spectral regime, the expected rise rate for FS emission is $t^{1/2}$ in the ISM environment and $t^0$ in the wind environment, both of which are incompatible with the observed mm-band light curve. Thus, the mm-band light curve at $<4$ days originates from a separate component. The shallowest decline rate for an RS light curve at $\nu\gtrsim\ensuremath{\nu_{\rm m,r}}$ is $\alpha\approx-2.1$ for a relativistic RS and $\alpha-1.5$ for a non-relativistic RS, in each case corresponding to a wind environment with $p\approx2$. Both of these are steeper than the observed mm-band light curve. However, the sum of the contributions from the two emission components (RS and FS) may yield the observed shallower decay. We investigate this further in Section [5.2](#text:mmexcess).

For the remainder of this article, we associate the low- and high-frequency components with emission from the RS and the FS, respectively, and consider other scenarios in Section [5.5](#text:other_scenarios). In this framework, our observations of GRB 181201A provide the first instance where a single radio SED can be instantaneously and cleanly decomposed into RS and FS components, with the RS dominating at the lower frequency bands, and the underlying FS emission clearly visible as an optically thin, rising spectrum at higher frequencies. We note that a more detailed characterization of these components, including the determination of the precise locations of their spectral break frequencies, requires a multi-band model fit, which we undertake in Section [4](#text:multimodel).

![](181201A_simplesed_4d)

![](181201A_ALMAlc_pl)

## Circum-burst density profile

The identification of the FS component now allows us to constrain the circum-burst density profile. We note that there is no evidence for a jet break until $\approx21$ days, as the X-ray light curve declines as a single power law from $\approx0.15$ days to $\approx21$ days ($\alpha_{\rm X} = -1.22\pm0.01$; Fig. [3](#fig:XRToptlc_pl)). The rising radio spectrum to $\approx90$ GHz at $3.9$ days indicates that $\ensuremath{\nu_{\rm m,f}}\gtrsim90$ GHz at this time. The relatively shallow spectral index of $\beta\approx0.1$ compared to the expected index of $\beta=1/3$ may result from the smoothness and potential proximity of the $\ensuremath{\nu_{\rm m,f}}$ break (cite: gs02).

Because $\ensuremath{\nu_{\rm m,f}}\gtrsim90$ GHz at 3.9 days, the FS peak flux density, $\ensuremath{F_{\nu,\rm m,f}}\gtrsim F_{\rm 3\,mm}(3.9~{\rm days})\approx1.2$ mJy. In the ISM environment, this peak flux density, $F_{\rm p}$, remains fixed and must appear at a lower cm-band frequency, $\nu_{\rm cm}$, at a later time given by, $$\begin{equation}
t_{\rm p} = \left(\frac{\nu_{\rm ALMA}}{\nu_{\rm cm}}\right)^{2/3}  \left(\frac{F_{\rm p}}{F_{\rm 
ALMA}}\right)^2.  
\end{equation}$$ This implies a flux density of $F_{\rm p}\gtrsim1.2$ mJy at $t_{\rm p} \gtrsim13.2$ days at 16 GHz, which is a factor of 2 brighter than the observed 16 GHz light curve at the corresponding time. Indeed, all cm-band light curves are inconsistent with this extrapolation, and thus inconsistent with an ISM-like environment.

We now show that the optical to X-ray data are also inconsistent with an ISM environment, and indicate a wind-like circum-burst medium. The GROND SED at 0.91 days corrected for Galactic extinction of $A_{\rm V} = 0.17$ mag (cite: sf11) can be fit with a single power law, with index $\beta_{\rm opt} = -0.49\pm0.04$ (Fig. [4](#fig:optxrtsed)). On the other hand, the spectral index between the GROND $K$-band and the X-rays is steeper, $\beta_{\rm NIR,X}=-0.75\pm0.02$, indicating that a spectral break lies between the optical/NIR and X-rays. The most natural explanation for these observations is $\ensuremath{\nu_{\rm m,f}}<\nu_{\rm 
opt}<\ensuremath{\nu_{\rm c,f}}<\ensuremath{\nu_{\rm X}}$. Fitting the optical and X-ray SED at 0.9 days, 2.9 days, and 4.9 days with broken power law models[^7] fixing the low frequency index to $\beta_{\rm opt}=-0.5$ and the high frequency index to $\beta_{\rm X}=-1.0$, we find a break frequency, $\nu_{\rm b}=(5.7\pm1.5)\times10^{15}$ Hz, $(8.1\pm2.0)\times10^{15}$ Hz, and $(9.1\pm3.3)\times10^{15}$ Hz, respectively (Fig. [4](#fig:optxrtsed)). The rising break frequency is roughly consistent with the evolution of $\ensuremath{\nu_{\rm c,f}}\propto t^{1/2}$ in a wind-like environment. We caution that the inferred location of the break is only indicative, as it is degenerate with the spectral slopes and break smoothness.

For $\ensuremath{\nu_{\rm m,f}}<\ensuremath{\nu_{\rm opt}}<\ensuremath{\nu_{\rm c}}$, we expect a spectral index of $\beta=(1-p)/2$. Combined with the observed GROND SED at 0.9 days, this implies $p\approx2$, which yields a light curve decay rate of $\alpha_{\rm opt}\approx-1.25$ for the wind environment and $\alpha_{\rm opt}\approx-0.75$ for the ISM environment. The observed decay rate in the *Swift*/UVOT $uvw2$-band and in ground-based optical $r^{\prime}$-band observations at $\approx0.2$–8.7 days is $\alpha_{\rm UV} = 
-1.21\pm0.02$, consistent with the wind case and inconsistent with an ISM environment (Fig. [3](#fig:XRToptlc_pl)).

![](181201A_XRToptlc)

Above $\ensuremath{\nu_{\rm c,f}}$, we expect a decay rate of $\alpha=(2-3p)/4\approx-1$. A power law fit to the X-ray light curve yields a decay rate of $\alpha_{\rm X} = -1.212 \pm 0.013$; however, the light curve after $\approx6$ days is consistently above the single power law fit. Adding a temporal break at $t_{\rm b}\approx0.4$ days yields a better fit with $\alpha_{X,1}=-1.7\pm0.1$ and $\alpha_{X,2}=-0.96\pm0.02$. The steep early decay may imply that the cooling break is not far below the X-ray band, and we verify this with our full multi-wavelength model in Section [4.1](#text:MCMC). On the other hand, the late-time excess is unusual, and we discuss this further in Section [5.3](#text:xrayexcess).

The measured X-ray photon index of $\Gamma_{\rm X}=1.77\pm0.06$ implies $\beta_{\rm 
X}=-0.77\pm0.06$, which is not consistent with $\beta=-p/2\approx-1$ expected for $p\approx2$. We note that the Klein-Nishina (KN) correction may yield a spectral index of $\beta=-3(p-1)/4\approx-0.75$ in some regimes (cite: nas09), and it is possible that this may impact the X-ray spectrum but not the light curve[^8]. We defer a detailed discussion of the KN corrections to future work.

To summarize, the radio SED at 3.9 days and the mm-band light curve indicate the presence of a separate emission component than that responsible for the X-ray and optical emission. We interpret this low-frequency component as RS emission.

Furthermore, we have described several observations that favor a wind-like circum-burst environment: (i) the high mm-band flux density at $4$ days that does not appear in the lower frequency radio light curve, (ii) a slowly rising break between the optical and X-rays, and (iii) the optical light curve, which is consistent with $\ensuremath{\nu_{\rm m,f}}<\ensuremath{\nu_{\rm opt}}<\ensuremath{\nu_{\rm c}}$ in a wind environment. We therefore focus on the wind environment in the remainder of this article.

![](181201A_optxrtsed)

## Afterglow onset

The first two MASTER observations at 156 and 209 s after the burst (156 s and 209 s, respectively) reveal a rapid brightening, $\alpha\approx2.8$. Such brightenings have only been seen in a few other optical afterglows (cite: mvm+07; mkm+10; lyz+10), and have been interpreted as onset of the afterglow, where the increase in flux density corresponds to an on-going transfer of energy from the ejecta to the forward shock, ultimately resulting in the deceleration of the ejecta (cite: rm92; mr93; sp99; kps99; kz07). Unfortunately, our data do not capture the time of the peak in the optical bands. As the FS is not fully set up during this onset period, we do not include these points in our multiwavelength modeling (Section [4](#text:multimodel)). We discuss these data further in Section [\[text:optrise2\]](#text:optrise2).

+------------------------------------------+--------------+---------------------------+
| Parameter                                | Best fit     | MCMC$^{a}$                |
+:=========================================+=============:+==========================:+
| Forward Shock                                                                       |
+------------------------------------------+--------------+---------------------------+
| $p$                                      | $2.11$       | $2.11\pm0.01$             |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{\epsilon_{\rm e}}$      | $-0.43$      | $-0.39^{+0.12}_{-0.17}$   |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{\epsilon_{\rm B}}$      | $-2.01$      | $-2.20^{+0.42}_{-0.78}$   |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{A_{*}}$                 | $-1.72$      | $-1.66^{+0.23}_{-0.13}$   |
+------------------------------------------+--------------+---------------------------+
| $\log(\ensuremath{E_{\rm K,iso}}/$erg)   | $53.3$       | $53.41^{+0.13}_{-0.16}$   |
+------------------------------------------+--------------+---------------------------+
| $\log(\ensuremath{A_{\rm V}}/$mag)       | $-1.83$      | $-1.84^{+0.14}_{-0.18}$   |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{\nu_{\rm a,f}}$ (Hz)    | $7.74$$^{b}$ | …                         |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{\nu_{\rm m,f}}$ (Hz)    | $12.7$       | …                         |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{\nu_{\rm c,f}}$ (Hz)    | $16.4$       | …                         |
+------------------------------------------+--------------+---------------------------+
| $\log\ensuremath{F_{\nu,\rm m,f}}$ (mJy) | $0.62$       | …                         |
+------------------------------------------+--------------+---------------------------+
|                                          |              |                           |
+------------------------------------------+--------------+---------------------------+
| Reverse Shock                                                                       |
+------------------------------------------+--------------+---------------------------+
| $\log(\ensuremath{\nu_{\rm a,r}}/$Hz)    | $12.1$       | $12.11\pm0.06$            |
+------------------------------------------+--------------+---------------------------+
| $\log(\ensuremath{\nu_{\rm m,r}}/$Hz)    | $8.6$        | $8.64^{+1.01}_{-0.45}$    |
+------------------------------------------+--------------+---------------------------+
| $\log(\ensuremath{\nu_{\rm c,r}}/$Hz)    | $14.7$       | $14.65^{+0.25}_{-0.22}$   |
+------------------------------------------+--------------+---------------------------+
| $\log(\ensuremath{F_{\nu,\rm m,r}}/$mJy) | $5.2$        | $5.16^{+0.26}_{-0.56}$    |
+------------------------------------------+--------------+---------------------------+
| $g$                                      | 2.72         | $2.74^{+0.38}_{-0.31}$    |
+------------------------------------------+--------------+---------------------------+

: FS and RS Model Parameters

Table notes: Frequencies and flux densities are calculated at 1 day (FS) and $10^{-2}$ days (RS). $^{a}$ Summary statistics from the marginalized posterior density distributions, with median and $\pm34.1\%$ quantiles (corresponding to $\pm1\sigma$ for Gaussian distributions; Fig. [9](#fig:corner)). $^{b}$ This frequency is not directly constrained by the data.

|  |  |
|:--:|:--:|
| ![image](181201A_multimodel_wind_XRT) | ![image](181201A_multimodel_wind_UV) |
| ![image](181201A_multimodel_wind_opt) | ![image](181201A_multimodel_wind_radio_high) |
| ![image](181201A_multimodel_wind_radio_mid) | ![image](181201A_multimodel_wind_radio_low) |

|  |  |  |
|:--:|:--:|:--:|
| ![image](181201A_epoch1_model_radio) | ![image](181201A_epoch2_model_radio) | ![image](181201A_epoch3_model_radio) |
| ![image](181201A_epoch4_model_radio) | ![image](181201A_epoch5_model_radio) | ![image](181201A_epoch6_model_radio) |
| ![image](181201A_epoch7_model_radio) | ![image](181201A_epoch8_model_radio) | ![image](181201A_epoch9_model_radio) |
| ![image](181201A_epoch10_model_radio) | ![image](181201A_epoch11_model_radio) | ![image](181201A_epoch12_model_radio) |
| ![image](181201A_epoch13_model_radio) |  |  |

![](181201A_SEDs)

![](181201A_lcs_rs)

![](corner)

# Multi-wavelength Modeling

## Markov Chain Monte Carlo Analysis

Guided by the basic considerations discussed above, we fit all available X-ray to radio observations with a model comprising an FS and RS produced by a relativistic jet propagating in a wind-like circum-burst environment. The free parameters for the FS model are $p$, $E_{\rm 
K,iso,52}$, $A_*$, $\ensuremath{\epsilon_{\rm e}}$, $\ensuremath{\epsilon_{\rm B}}$, and the extinction, $\ensuremath{A_{\rm V}}$. Given the relatively shallow decline rate of the mm-band light curve ($\alpha\approx-0.72$) corresponding to the RS component, we focus on the non-relativistic RS model, which allows for shallower light curve decay than a relativistic RS. The free parameters for the RS model[^9] are the break frequencies $\ensuremath{\nu_{\rm a,r}}$, $\ensuremath{\nu_{\rm m,r}}$, $\ensuremath{\nu_{\rm c,r}}$ and the RS peak flux, $\ensuremath{F_{\nu,\rm m,r}}$ all at a reference time, $t_{\rm ref}\equiv0.01$ days selected to be $\approx {\rm few}\times T_{90}$ (and hence comparable to $\ensuremath{t_{\rm dec}}$). Additionally, we allow the parameter $g$, corresponding to the evolution of the RS Lorentz factor with radius after the deceleration time ($\Gamma\propto R^{-g}$) to vary (cite: mr99; ks00). Finally, we allow for a constant contribution to the light curves from an underlying host galaxy in bands where late-time flattening is evident (optical $griz$ bands and the cm-bands from 2.7 to 24.5 GHz). All free parameters, including RS and FS components and the underlying host galaxy contamination, are fit simultaneously. Further details of the modeling procedure, including the likelihood function employed, are described elsewhere (cite: lbz+13; lbt+14; lab+16).

We performed a Markov Chain Monte Carlo (MCMC) exploration of the multi-dimensional parameter space using `emcee` (cite: fhlg13). We ran 512 walkers for 10k steps and discarded a few ($\lesssim0.15\%$) initial non-converged steps with low log likelihood as burn-in. Our highest likelihood model with $p\approx2.1$, $\ensuremath{\epsilon_{\rm e}}\approx0.37$ $\ensuremath{\epsilon_{\rm B}}\approx9.6\times10^{-3}$, $E_{\rm K,iso}\approx2.2\times10^{53}$ erg, $\ensuremath{A_{*}}\approx1.9\times10^{-2}$, and negligible extinction, $\ensuremath{A_{\rm V}}\lesssim0.02$ mag, together with an RS model with $g\approx2.7$, $\ensuremath{\nu_{\rm a,r}}\approx4.2$ GHz, $\ensuremath{\nu_{\rm c,r}}\approx90$ GHz, and $F_{\nu,\rm a,r}\approx0.6$ mJy at $3.9$ days fits the X-ray to radio light curves and radio SEDs well (Figs. [5](#fig:modellc_RS_splits) and [6](#fig:modelsed_RS)). The peak in the cm-band spectrum at 3.9 days corresponds to $\ensuremath{\nu_{\rm a,r}}$. The sum of the RS self-absorbed spectrum and the FS optically thin $\nu^{1/3}$ spectrum below $F_{\nu,\rm a,r}$ (Fig. [6](#fig:modelsed_RS)) explains the intermediate $\beta\approx1.4$ spectral index below the cm-band peak (Section [3.1](#text:4dsed)). We present a selection of SEDs spanning radio to X-rays in Figure [7](#fig:modelseds), and all light curves together in Figure [8](#fig:modellc_RS).

For this model, the FS cooling frequency, $\ensuremath{\nu_{\rm c,f}}\approx2.6\times10^{16}$ Hz at 1 d lies between the optical and X-rays, as expected from the basic considerations in Section [3.2](#text:densityprofile). The proximity of $\ensuremath{\nu_{\rm c,f}}$ to the X-ray band ($\ensuremath{\nu_{\rm c,f}}\approx0.3$ keV at 8 days) explains the moderately steep decline in the X-ray light curve, compared to the expectation for $\ensuremath{\nu_{\rm X}}\gtrsim\ensuremath{\nu_{\rm c,f}}$. Furthermore, $\ensuremath{\nu_{\rm a,f}}\approx60$ MHz is below the VLA and GMRT frequencies, and is therefore not constrained, resulting in degeneracies between the model parameters (Fig. [9](#fig:corner)). The FS characteristic frequency at 4 days, $\ensuremath{\nu_{\rm m,f}}\approx6\times10^{11}$ Hz is above the ALMA band, as expected from the radio/mm SED at that time (Section [3.1](#text:4dsed)). We list the properties of the best fit model and summarize the marginalized posterior density function in Table [3](#tab:params).

## Determination of Ejecta Initial Lorentz Factor

We now use the MCMC results to derive the initial Lorentz factor of the jet. The jet’s initial Lorentz factor can be determined from joint RS and FS observations by solving the following equations self-consistently (cite: zkm03; lab+18) at the deceleration time, $\ensuremath{t_{\rm dec}}$, $$\begin{align}
 \frac{\ensuremath{\nu_{\rm m,r}}}{\ensuremath{\nu_{\rm m,f}}} &\sim \ensuremath{\Gamma_{0}}^{-2}\ensuremath{R_{\rm B}}, \nonumber \\
 \frac\ensuremath{\nu_{\rm c,r}}\ensuremath{\nu_{\rm c,f}}&\sim \ensuremath{R_{\rm B}}^{-3}, \nonumber \\
 \frac\ensuremath{F_{\nu,\rm m,r}}\ensuremath{F_{\nu,\rm m,f}}&\sim \ensuremath{\Gamma_{0}}\ensuremath{R_{\rm B}},
 \label{eq:consistency}
\end{align}$$ where $\ensuremath{\Gamma_{0}}$ is the initial Lorentz factor of the GRB jet, $\ensuremath{R_{\rm B}}\equiv(\epsilon_{\rm 
B,r}/\epsilon_{\rm B,f})^{1/2}$ is the relative magnetization of the ejecta, and we have assumed similar values of $\ensuremath{\epsilon_{\rm e}}$ and the Compton $y$ parameter in the two regions. The effective magnetizations of the shocked ejecta and shock external medium may well be very different, and the introduction of $R_{\rm B}$ allows us to investigate such variations caused, for instance, by the presence of magnetic fields produced in the initial GRB and advected in the outflow (cite: uso92; mr97; zkm03).

This system of equations has three unknowns ($t_{\rm dec}$, $R_{\rm B}$, and $\Gamma_0$), and can be inverted exactly, to yield $$\begin{align}
 \ensuremath{t_{\rm dec}}&= t_{\rm ref} \left[
                        \left(\frac{\ensuremath{\nu_{\rm c,f}}^{\prime}}{\ensuremath{\nu_{\rm c,r}}^{\prime}}\right)
                        \left(\frac{\ensuremath{F_{\nu,\rm m,f}}^{\prime}}{\ensuremath{F_{\nu,\rm m,r}}^{\prime}}\right)^2
                        \left(\frac{\ensuremath{\nu_{\rm m,f}}^{\prime}}{\ensuremath{\nu_{\rm m,r}}^{\prime}}\right)
                        \right]^\tau, \nonumber \\
\tau &\equiv \left[\frac{15}{2(4-k)}-\frac{8(g+3)}{7(2g+1)}\right]^{-1}
\label{eq:tdec}
\end{align}$$ where the primed quantities refer to values at the reference time of $t_{\rm ref}=0.01$ days used in the MCMC analysis. For our best-fit model, this yields $\ensuremath{t_{\rm dec}}\approx5.3\times10^{-3}$ days or $\approx460$ s; the full MCMC analysis gives $\log(\ensuremath{t_{\rm dec}}/{\rm days})=-2.27^{+0.13}_{-0.14}$. We note that this is longer than the burst duration, $T_{90}\approx172$ s (Section [2](#text:obs_basic)), consistent with the thin shell case (cite: zkm03).

Given this value of $\ensuremath{t_{\rm dec}}$, which satisfies equation [\[eq:consistency\]](#eq:consistency), we can in principle compute the initial Lorentz factor and magnetization, $$\begin{align}
\ensuremath{R_{\rm B}}= \left(\frac\ensuremath{\nu_{\rm c,f}}\ensuremath{\nu_{\rm c,r}}\right)^{1/3} \nonumber\\
\ensuremath{\Gamma_{0}}= \frac\ensuremath{F_{\nu,\rm m,r}}\ensuremath{F_{\nu,\rm m,f}}\ensuremath{R_{\rm B}}^{-1}.
\label{eq:jetpropcalc}
\end{align}$$ However, we find that whereas $\ensuremath{\nu_{\rm c,r}}$ and $\ensuremath{\nu_{\rm c,f}}$ are reasonably well constrained, $\ensuremath{F_{\nu,\rm m,r}}$ is completely degenerate with $\ensuremath{\nu_{\rm m,r}}$. This is because the RS peak in the radio band corresponds to $\ensuremath{\nu_{\rm a,r}}$, and hence the data do not constrain $\ensuremath{\nu_{\rm m,r}}$. In the observed regime of $\ensuremath{\nu_{\rm m,r}}<\ensuremath{\nu_{\rm a,r}}$, the peak flux density of the RS component, $F_{\nu,\rm a,r}\propto \ensuremath{F_{\nu,\rm m,r}}(\ensuremath{\nu_{\rm a,r}}/\ensuremath{\nu_{\rm m,r}})^{(1-p)/2}$ results in the degeneracy, $\ensuremath{F_{\nu,\rm m,r}}\propto\ensuremath{\nu_{\rm m,r}}^{(1-p)/2}\propto\ensuremath{\nu_{\rm m,r}}^{-0.5}$ for $p\approx2$, which exactly explains the observed correlation between these parameters (Figure [9](#fig:corner)). Our MCMC samples span 4 orders of magnitude in $\ensuremath{\nu_{\rm m,r}}$ and correspondingly about 2 orders of magnitude in $\ensuremath{F_{\nu,\rm m,r}}$. The sampling is clipped at the lower end in $\ensuremath{\nu_{\rm m,r}}$ by the prior on $\ensuremath{\nu_{\rm m,r}}>10^8$ Hz (corresponding to $\ensuremath{F_{\nu,\rm m,r}}\lesssim10^8$ mJy) and at the lower end in $\ensuremath{F_{\nu,\rm m,r}}$ by the actual observed peak flux density of the RS component (corresponding to $\ensuremath{\nu_{\rm m,r}}\lesssim10^{12}$ Hz). This degeneracy between $\ensuremath{\nu_{\rm m,r}}$ and $\ensuremath{F_{\nu,\rm m,r}}$ does not affect the calculation of $\ensuremath{t_{\rm dec}}$ (equation [\[eq:tdec\]](#eq:tdec)), because $\ensuremath{\nu_{\rm m,r}}$ and $\ensuremath{F_{\nu,\rm m,r}}$ enter in the combination $\ensuremath{F_{\nu,\rm m,r}}\ensuremath{\nu_{\rm m,r}}^2\propto\ensuremath{\nu_{\rm m,r}}^{2-p}$, which is only weakly dependent on $\ensuremath{\nu_{\rm m,r}}$ for $p\approx2$ (i.e., the degenerate terms cancel out). Therefore, we can constrain $\ensuremath{t_{\rm dec}}$ and $\ensuremath{R_{\rm B}}$ through this system of equations, but not $\ensuremath{\Gamma_{0}}$. We find $\ensuremath{R_{\rm B}}\approx0.65$ for the best-fit solution, and $\ensuremath{R_{\rm B}}=0.64^{+0.07}_{-0.08}$ from the MCMC.

![](gamma)

To infer $\ensuremath{\Gamma_{0}}$ in this case, we turn to an energy balance argument (cite: zkm03). At $\ensuremath{t_{\rm dec}}$, the energy in the swept-up material ($E_{\rm sw}$) is similar to the rest energy of the ejecta (which is the same as the explosion kinetic energy, $E$), $$\begin{align}
E_{\rm sw} = \ensuremath{\Gamma_{0}}^2 M_{\rm sw} c^2 \approx E,
\label{eq:E_sw}
\end{align}$$ where the swept-up mass at radius, $R$, $$\begin{align}
 M_{\rm sw} = \frac{4\pi A R^{3-k}}{3-k}
\label{eq:M_sw}
\end{align}$$ Combining equations [\[eq:E_sw\]](#eq:E_sw) and [\[eq:M_sw\]](#eq:M_sw), the deceleration radius, $$\begin{align}
 R = \left[\frac{(3-k)E}{4\pi A\ensuremath{\Gamma_{0}}^2 c^2}\right]^{1/(3-k)} = \ensuremath{\Gamma_{0}}^{-2/(3-k)}\ensuremath{l_{\rm Sedov}}, 
\end{align}$$ where $\ensuremath{l_{\rm Sedov}}$ is the Sedov length, which depends only on the energy and density, parameters that are known from the FS modeling. For a point source moving along the line of sight, this radius corresponds to the deceleration time given by, $R = 2\ensuremath{\Gamma_{0}}^2 c \ensuremath{t_{\rm dec}}/(1+z)$, which gives the initial Lorentz factor, $$\begin{align}
 \ensuremath{\Gamma_{0}}\approx 
\left[\frac{\ensuremath{l_{\rm Sedov}}}{c}\left(\frac{2\ensuremath{t_{\rm dec}}}{1+z}\right)\right]^{\frac{3-k}{2(4-k)}}
\label{eq:Gammajet}
\end{align}$$ We note that this is a simplified treatment, and a more rigorous analysis requires integrating over the full fluid profile, and using the specific enthalpy of the shocked region while calculating the swept-up mass. However, for our purposes, this approximate expression will suffice to estimate $\Gamma_{0}$. We compute $\ensuremath{\Gamma_{0}}$ for all MCMC samples using equation [\[eq:Gammajet\]](#eq:Gammajet), resulting in $\ensuremath{\Gamma_{0}}= 103^{+10}_{-8}$ (Fig. [10](#fig:gamma)).

# Discussion

## Early optical rise

We now return to the optical rise observed at $\lesssim2.4\times10^{-3}$ days with MASTER (Fig. [5](#fig:modellc_RS_splits)). These observations were performed at $\lesssim\ensuremath{t_{\rm dec}}$ in our best-fit RS+FS model (Section [4](#text:multimodel) and Table [3](#tab:params)), consistent with the afterglow onset scenario. The spectral ordering at $\ensuremath{t_{\rm dec}}$ is $\ensuremath{\nu_{\rm m,r}}<\ensuremath{\nu_{\rm a,r}}<\ensuremath{\nu_{\rm opt}}\approx\ensuremath{\nu_{\rm c,r}}$ and $\ensuremath{\nu_{\rm a,f}}<\ensuremath{\nu_{\rm c,f}}<\ensuremath{\nu_{\rm opt}}<\ensuremath{\nu_{\rm m,f}}$. In this model, the RS light curve at $\lesssim\ensuremath{t_{\rm dec}}$ is expected to rise at the rate $\alpha=(p-1)/2\approx0.5$, while the FS light curve should rise as $\alpha=1/2$ (cite: zwd05). However, the observed rise of $\alpha\approx2.8$ is not consistent with either prediction. The proximity of $\ensuremath{\nu_{\rm c,r}}$ to $\ensuremath{\nu_{\rm opt}}$ at the deceleration time may suppress the RS flux. On the other hand, the FS model also over-predicts the observed flux. One possible solution is rapid injection of energy into the FS during this period. We find that an energy increase at the rate $E\propto 
t^{1.8}$ until $\ensuremath{t_{\rm dec}}$ roughly accounts for the optical rise[^10] (Fig. [11](#fig:enj)). Such an injection could arise, for instance, by the presence of energy at Lorentz factors $\lesssim\ensuremath{\Gamma_{0}}$ owing to velocity stratification in the ejecta (cite: sm00), which has previously been inferred in other GRB afterglows (cite: lbm+15; lbm+18; lab+18). An alternate scenario could be a pair-dominated optical flash, as suggested for GRB 130427A (cite: vhb14). However, the paucity of data around the optical peak preclude a more detailed analysis.

![](181201A_rlc)

## Intermediate millimeter excess

The 3 mm model light curve under-predicts two of the ALMA detections at $\approx1.9$ and $\approx3.9$ days by $\approx20\%$ (Fig. [12](#fig:almacomparison)). In particular, the observed light curve exhibits a shallower decline than afforded by the current model, where the transition between RS-dominant to FS-dominant at $\approx 1.5$ days results in an inflexion in the model light curve, which is not seen in the data. One possibility for a shallower RS decline rate is for the RS to be refreshed by slower ejecta catching up with the FS (cite: sm00). This scenario requires a distribution of Lorentz factors in the jet, which has indeed been inferred in other events (cite: lbm+15; lbm+18; lab+18), and remains feasible here. We note that a similar discrepancy was present in the only other ALMA light curve of a GRB available at this date, that of GRB 161219B (cite: lab+18). In that case, the model under-predicts the data at $\approx 3$ days, corresponding to a similar RS-FS transition. These similarities may indicate that the RS evolution is more complex than previously thought, or that the mm-band emission is not dominated by the RS at all, and is in fact a separate component. Further ALMA 3 mm observations of GRBs, together with detailed multi-wavelength modeling, may help shed light on this issue.

![](almacomparison)

## Late X-ray excess

The observed 1 keV light curve exhibits a late time shallowing (Fig. [3](#fig:XRToptlc_pl)), and can therefore not be fit perfectly in our model (Fig. [5](#fig:modellc_RS_splits)), where only steepenings are expected (cite: sph99). As a result, our best-fit model under-predicts the X-ray flux density at 127 days. Above $\ensuremath{\nu_{\rm m,f}}$, the afterglow light curves are indeed expected to become shallower at late times when the FS becomes non-relativistic at $\ensuremath{t_{\rm NR}}$ (cite: wkf98). One simple definition of $\ensuremath{t_{\rm NR}}$ corresponds to the time when $\Gamma\beta\approx1$ (i.e., $\Gamma\approx\sqrt{2}$). For the best-fit model, these parameters correspond to $\ensuremath{t_{\rm NR}}\approx220$ years, which cannot explain the X-ray excess at $\approx127$ days.

Another possibility is that the late-time excess corresponds to a contaminating source within the XRT point spread function, which has been observed at least once before; however, this possibility is quite rare and unlikely. One way to test this is to obtain observations of the afterglow with *Chandra*; however, at the time of writing, the target was within an extended Sun-constraint for *Chandra*, and not visible.

We note that late-time excess X-ray flux has been uncovered in other events (cite: fbm+14; mgl+15; lbc+18). Suggested explanations have included dust echoes, inverse-Compton scattering, late-time radiation from spin-down of a magnetar central engine, and interaction of the FS with the shocked stellar wind at the edge of the stellar wind bubble (cite: sd07; ccf+08; lrz+08; mg11; gvem13; fbm+14; mgl+15). For reference, the shock radius at 127 days is $\approx30$ pc for our best-fit parameters, which is significantly larger than the mean distance between O stars in a typical massive stellar cluster (cite: fmm99).

## Late radio excess

The 1–2 GHz GMRT light curves appear to exhibit an unexpected brightening of the afterglow between 30–48 days after the burst. The corresponding radio maps were dynamic range limited, with noise dominated by image deconvolution errors. Thus, it is possible that our reported uncertainties underestimate the true variation of the non-Gaussian image noise. In that scenario, the light curve may be consistent with being flat, and therefore host-dominated. We caution that while a similar brightening is evident in the GMRT $750$ MHz observations, they appear to be absent at $620$ MHz. The two bands were observed together as part of a broader frequency coverage with the upgraded GMRT (GWB) system, and no systematic errors are expected in the light curve produced from different parts of the observing band.

On the other hand, we note that late-time light curve flattenings or re-brightenings have been observed in several radio afterglows (cite: bck+03; pk04; alb+17; lbc+18; lab+18). If real, the re-brightening in this event might indicate (i) late-time energy injection due to slower ejecta shells[^11] (cite: sm00; kbdg16), which has been inferred in several instances (cite: lbm+15; lbm+18; lab+18), or (ii) interaction of the FS with the wind termination shock, a scenario discussed above in the context of the X-ray light curve flattening (Section [5.3](#text:xrayexcess)). Any contribution from the emerging supernova is expected to peak on $\gtrsim 10$ year time scales, and therefore an unlikely explanation for this excess (cite: bdg15). The emergence of a counterjet, such as has been claimed in cm-band observations GRB 980703 at $\gtrsim500$ days after the burst (cite: ls04; phtp17) should occur at $\gtrsim \ensuremath{t_{\rm NR}}\approx220$ yr for this event (Section [5.3](#text:xrayexcess)), and is also disfavored.

## Are we really seeing the reverse shock?

We note that our derived value of $g\approx2.7$, while higher than the theoretically expected upper limit for a wind environment (cite: zwd05), is comparable to $g\approx2.3$ in GRB 140304A (cite: lbm+15). Previous studies have found even higher values of $g\approx5$ in the case of the RS emission from GRB 130427A (cite: lbz+13; pcc+14). Higher values of $g$ result in a more slowly evolving spectrum, and are preferred by the fit due to the relatively slowly evolving cm/mm emission observed in these events, including in the event studied here. Owing to this mismatch with the theoretical prediction for $g$, as well as some of the other issues described above, it is natural to ask whether the RS+FS model is the only one that can explain the observations. It is possible that the emission observed here and in similar events in the past, which has been ascribed to the RS, is in fact from a different emission mechanism.

One possible alternate explanation is to invoke a two-component jet, one in which the optical and X-ray emission arises from a narrower, faster jet than that producing the cm-band observations (cite: bkp+03; pkg05; odpp+07; rks+08; hdpm+12). In such a case, we expect the radio peak frequency and peak flux density to evolve according to the standard FS prescription as $\ensuremath{\nu_{\rm m}}\propto t^{-3/2}$ and $\ensuremath{F_{\nu,\rm m}}\propto t^{-1/2}$, respectively. From the SED at 3.9 days (Section [3.1](#text:4dsed) and Fig. [1](#fig:4dsed)), this would imply an $R$-band peak at $\approx2.2\times10^{-3}$ days with a flux density of $\approx60$ mJy. While this would over-predict the MASTER observations at $\approx2.4\times10^{-2}$ days, if the jet producing this emission component were still decelerating at this time, then the flux could be significantly lower. Furthermore, we find that this component would not contribute significantly to the remainder of the optical light curve. For instance, at the time of the earliest UVOT observation at $\approx0.18$ days, the predicted flux density of $\approx0.2$ mJy is below the observed flux density of $\approx0.6$ mJy. Whereas it is not possible for us to confirm or rule out two-component jet models, we note that decoupling the cm/mm emission from the optical/X-ray emission reduces the predictive power of such a model.

Another alternate scenario to explain the radio spectral bump at 3.9 days is the presence of a population of non-accelerated (“thermal”) electrons, which are not accelerated by the passage of the FS into a relativistic power-law distribution, but instead form a Maxwellian distribution at lower energies (cite: ew05). However, a disjoint spectral component as observed here would likely require a very specific electron distribution, one in which the typical Lorentz factor of the thermal electrons is much lower than the minimum Lorentz factor of the shock-accelerated electrons, the so-called ‘cold electron model’ (cite: rl17).

The emission signature from such a population is expected to be quite broad. We demonstrate this by setting the electron participation fraction, usually assumed to be unity, to $f_{\rm NT}\approx0.6$, and computing the resultant spectrum as described in (cite: rl17). We use a cold electron model, with a ratio of electron temperature ($T_{\rm e}$) to gas temperature ($T_{\rm g}$) set at $\eta_{\rm e} 
\equiv T_{\rm e}/T_{\rm g}\approx10^{-2}$. The resultant spectrum exhibits a broad peak in the cm-band, and does not match the observations as well as the RS model (Fig. [13](#fig:thermales)). While increasing $f_{\rm NT}$ increases the sharpness of the peak (relative to the underlying FS emission), doing so also increases the relative brightness of the thermal bump beyond the data, and so no combination of $f_{\rm NT}$ and $\eta_{\rm e}$ appears to match the cm-band data. A more detailed analysis requires a complete parameter search over $f_{\rm NT}$ and $\eta_{\rm 
e}$ that also includes the FS parameters. Such a study is currently not possible due to the computational intensiveness of the thermal electron calculation, and we defer it to future work.

![](181201A_thermales)

## FS parameter degeneracies

Our modeling reveals degeneracies between the FS model parameters (Fig. [9](#fig:corner)), which cannot be explained by the unknown value of $\ensuremath{\nu_{\rm a,f}}$ alone. For instance, the correlation contours between $\ensuremath{A_{*}}$ and $E_{\rm K,iso}$ lie parallel to the degenerate line $E_{\rm K,iso}\propto 
\ensuremath{A_{*}}^{1.4}$. However, the expected relation between these parameters when $\ensuremath{\nu_{\rm a}}$ is unknown is $E_{\rm K,iso}\propto \ensuremath{A_{*}}^{-0.2}$ (cite: gs02; lbt+14). We note that the Compton $Y$ parameter varies by about two orders of magnitude along the axis of the observed degeneracy, and thus the change in the physical parameters is compensated for by varying $Y$.

Our prescription for calculating Compton $Y$ relies on a simplistic global approximation (cite: se01; lbm+15). However, we note that in low density environments, the Klein-Nishina suppression limits the maximum value of $Y$ (cite: nas09). We derive an expression for this maximum value of $Y$ corresponding to the Lorentz factor of cooling electrons in a wind environment by substituting equation (18) from (cite: pk00) for the effective density as a function of observer time in equation (64) from (cite: nas09) for the maximum value of $Y$ when KN corrections are included, to obtain, $$\begin{align}
 Y_{\rm max}(\gamma_{\rm c}) &= 10 e^{\frac{27(3.2-p)^2-17}{(p+2)(4-p)}}
                                   e^{\left(\frac{8-p}{2(p+2)}\ln{0.73}\right)}  \nonumber \\
                             &\times \epsilon_{\rm e,-1}^{\frac{5(p-1)}{p+2}}
                                E_{53}^{\frac{p-3}{p+2}}
                                \ensuremath{A_{*}}^{\frac{8-p}{p+2}}
                                t_{\rm days}^{-\frac{(2p-1)}{(p+2)}}.
\end{align}$$ For our best-fit parameters (Table [3](#tab:params)), this evaluates to $Y_{\rm max}(\gamma_{\rm c})\approx2 t_{\rm days}^{-0.8}$, which is lower than some of the values in the degenerate models discussed. Thus, a future, more accurate calculation incorporating Klein-Nishina corrections may resolve this source of degeneracy.

## Burst Energetics and radiative efficiency

The data do not reveal a jet break (cite: rho99; sph99), and hence the degree of collimation remains unknown for this burst. As of the time of writing, we are continuing VLA observations of this event, and expect that late-time observations may allow for beaming-independent calorimetry provided the contribution from the underlying host is negligible (cite: fwk00; bkp+03; bkf04; fsk+05; sb11; dcrgl12). With that said, we note that our modeling does require some host contribution at 2.7 to 24.5 GHz at the $\approx50\,\mu$Jy level (Fig. [5](#fig:modellc_RS_splits)), corresponding to a star formation rate of $\approx 2~M_{\odot}{\rm yr}^{-1}$ (cite: yc02; bck+03); hence it is not clear whether such calorimetry will be feasible for this burst. For a jet break time of $\ensuremath{t_{\rm jet}}\gtrsim163$ days, we can only set a lower limit to the jet half opening angle of $\ensuremath{\theta_{\rm jet}}\gtrsim6^{\circ}$, corresponding to a minimum beaming-corrected energy of $1.4\times10^{52}$ erg.

The radiative efficiency, on the other hand, is independent of the beaming correction. For our best-fit model, we find $\ensuremath{\eta_{\rm rad}}\approx0.35$. This value corresponds to a slightly lower efficiency than for other GRBs at similar $E_{\gamma,\rm iso}$ as derived from X-ray afterglow observations (cite: lz04). However, the observed distribution of $\ensuremath{\eta_{\rm rad}}$ for *Swift* GRBs spans a broad range (cite: bkf03; nkg+06; zlp+07; bndp15), and this value of $\ensuremath{\eta_{\rm rad}}$ is unremarkable.

## Low circum-burst density

There is a strong observed correlation between multi-wavelength detections of RS emission with low density circum-burst environments, typically $\ensuremath{n_{0}}$, $\ensuremath{A_{*}}\lesssim10^{-2}$ (cite: lab+18). We note that the circum-burst density for our best-fit model, $\ensuremath{A_{*}}\approx0.02$ is also similarly low. We have previously remarked on the possibility that this is an observational selection effect, since low density environments are more likely to result in a slow-cooling RS with long-lasting emission (cite: lbz+13; lab+16; lab+18; lag+19; kmk+15; alb+17). In the case of GRB 161219B, we used constraints on the RS cooling frequency to determine a maximal particle density for the ISM environment under which RS emission was expected, and showed that the observed density satisfied the constraint in that case. We repeat that argument here, now for the wind medium.

Combining equation [\[eq:consistency\]](#eq:consistency) with the expression for FS cooling frequency from (cite: gs02), $$\begin{align}
 \ensuremath{\nu_{\rm c,f}}&= 4.40\times10^{10}(3.45-p)e^{0.45p}(1+z)^{-3/2} \nonumber\\
       &\times  \ensuremath{\epsilon_{\rm B}}^{-3/2}\ensuremath{A_{*}}^{-2}E_{\rm K,iso,52}^{1/2}(1+Y_{\rm f})^{-2}\ensuremath{t_{\rm d}}^{1/2}
         {\rm Hz} \nonumber \\
       &\approx 10^{13} \ensuremath{A_{*}}^{-2} {\rm Hz} \nonumber \\
       &\sim \ensuremath{R_{\rm B}}^{3}\ensuremath{\nu_{\rm c,r}}
\end{align}$$ for the best-fit parameters at $t\approx1$ d yields, $$\begin{align}
 \ensuremath{A_{*}}&\approx \left(\frac{\ensuremath{\nu_{\rm c,r}}}{10^{13}\,{\rm Hz}}\right)^{-1/2}\ensuremath{R_{\rm B}}^{-3/2}
\nonumber\\
 &\lesssim 0.24\ensuremath{R_{\rm B}}^{-3/2}\ensuremath{{\rm cm}^{-3}}, 
\end{align}$$ which is indeed satisfied for GRB 181201A where $\ensuremath{A_{*}}\approx2\times10^{-2}$ (corresponding to a mass loss rate, $\dot{M}\approx2\times10^{-7}~M_{\odot}{\rm yr}^{-1}$ for a wind speed of $10^3$ km s$^{-1}$). We note that a similar low wind parameter of $\ensuremath{A_{*}}\approx3\times10^{-3}$ was inferred in the case of GRB 130427A, which also exhibited a strong RS signature (cite: lbz+13; pcc+14). Our observation of RS emission in GRB 181201A therefore supports the hypothesis that RS emission is more easily detectable in low density environments, in both the ISM and wind scenarios.

## Reverse shock Lorentz factor

During our analysis above, we have assumed a non-relativistic reverse shock. We now check this assumption by calculating the Lorentz factor of the RS itself. During the shock crossing, the Lorentz factor of the shocked fluid in the cold ejecta frame is given by $$\begin{align}
\bar{\gamma} &\approx \frac12\left(\frac{\Gamma_{\rm FS}/\sqrt{2}}{\ensuremath{\Gamma_{0}}}
                      +\frac{\ensuremath{\Gamma_{0}}}{\Gamma_{\rm FS}/\sqrt{2}}\right),
\end{align}$$ where $\Gamma_{\rm FS}$ is the FS Lorentz factor, assumed to be highly relativistic. The RS Lorentz factor is then given by the shock jump condition (cite: bm76), $$\begin{align}
\bar{\Gamma}_{\rm RS} = \frac{(\bar{\gamma}+1)\left[\hat{\varsigma}\left(\bar{\gamma}-1\right)+1\right]^2}{\hat{\varsigma}(2-\hat{\varsigma})(\bar{\gamma}-1)+2},
\end{align}$$ where we take the adiabatic index $\hat{\varsigma}=4/3$, appropriate for a relativistic fluid (cite: ks00). We compute these quantities from our MCMC results, and find $\bar{\Gamma}_{\rm 
RS}=1.97^{+0.08}_{0.07}$, corresponding to a shock speed of $\bar{\beta}_{\rm RS}=0.74\pm0.02$ and 4-velocity, $\bar{\Gamma}_{\rm RS}\bar{\beta}_{\rm RS}=1.7\pm0.1$. Thus the RS is at most mildly relativistic, and definitely not ultra-relativistic ($\bar{\Gamma}_{\rm RS}\bar{\beta}_{\rm 
RS}\gg1$). Whereas the expressions we have used for the RS evolution in the modeling are strictly valid only in the asymptotic regime of a Newtonian RS, they are expected to be approximately correct for cold shells where the post-shock evolution deviates from the Blandford-McKee solution. A more detailed analysis requires numerical calculation of the RS hydrodynamics and radiation simultaneously with the MCMC fitting, which is beyond the scope of this work.

## Ejecta magnetization

The relative magnetization of $\ensuremath{R_{\rm B}}\approx0.6$ observed in this event is similar to $\ensuremath{R_{\rm B}}\approx1$ for GRB 161219B (cite: lab+18) and $\ensuremath{R_{\rm B}}\approx0.6$ for GRB 140304A (cite: lbm+18). On the other hand, these values are all smaller than $1\lesssim\ensuremath{R_{\rm B}}\lesssim5$ for GRB 130427A (cite: lbz+13), $\ensuremath{R_{\rm B}}\approx8$ for GRB 160509A (cite: lab+16), $\ensuremath{R_{\rm B}}\sim1$-100 for GRB 160509A (cite: alb+17), and $\ensuremath{R_{\rm B}}\approx1$–100 derived for GRBs with optical flashes (cite: gkg+08; gkm+09; jkck+14). Interpreting these values requires accounting for the variation in $\epsilon_{\rm B,f}$ between events, which we perform next.

The plasma magnetization in the ejecta, $\sigma$, defined as the ratio of the magnetic energy density to the rest mass energy density, corresponds to $\sigma\approx\epsilon_{\rm 
B,r}\bar{\Gamma}_{\rm RS}$. For the non-relativistic reverse shocks observed in all of these cases, this implies $\sigma\approx\epsilon_{\rm B,r} = \ensuremath{R_{\rm B}}^2\epsilon_{\rm B,f}$. A detailed statistical comparison of $\sigma$ between GRBs requires full posterior density functions for $\ensuremath{R_{\rm B}}$ in each case, which are not currently available. However, we can use the typical parameters in each case for a rough comparison.

For our best-fit parameters, we have $\epsilon_{\rm B,r}\approx2.6\times10^{-3}$ for GRB 181201A. For GRB 160625B, the large feasible range of $\ensuremath{R_{\rm B}}\sim1$–100 makes comparison less meaningful. For GRB 160509A, $\ensuremath{R_{\rm B}}^2\epsilon_{\rm B,f}>1$; however, the RS in that case was long-lived and continuously refreshed, thus suggesting additional physics not captured by the simple calculation of $\sigma$. For the other bursts with radio RS emission, we find $\epsilon_{\rm 
B,r}\approx6\times10^{-2}$ (161219B), $\epsilon_{\rm B,r}\approx2\times10^{-2}$ (140304A), $\epsilon_{\rm B,r}\approx 0.2$–1 (130427A). Thus for all GRBs with detected and well-constrained RS emission, $\sigma$ ranges between $10^{-3}$ and $\approx 1$, indicating that the ejecta are weakly magnetized. However, we caution that this outcome is largely built into the formalism for non-relativistic reverse shocks, for which $\sigma\approx\epsilon_{\rm B,r}$. The multiwavelength detection and characterization of a relativistic RS might enable us to explore a broader regime in $\sigma$.

In summary, the detection of the RS signature in this GRB argues against the scenario where the jet is Poynting flux dominated, since in that case, no RS emission is expected (cite: lcj17). The mildly relativistic RS observed in this case argues against propagation in a highly magnetized, relativistic outflow, such as in a magnetar wind (cite: mgt+11). This event brings the number of GRBs with radio RS detections to seven (cite: kfs+99; sp99a; lbz+13; pcc+14; lab+16; alb+17; lbm+18; lab+18; lag+19).

# Conclusions

We have presented multi-wavelength radio to X-ray observations of GRB 181201A spanning from $\approx150$ s to $\approx163$ days after the burst. We have modeled these observations in the standard afterglow synchrotron emission framework to derive the burst energetics and parameters of the explosion. The radio data we present reveal the presence of an additional component, which we interpret as emission from electrons heated by a mildly relativistic ($\bar{\Gamma}_{\rm 
RS}\approx2$) reverse shock that propagates through the ejecta in $\ensuremath{t_{\rm dec}}\approx460$ s. We have performed detailed, self-consistent modeling of the RS and FS to derive the initial Lorentz factor, $\Gamma=103^{+10}_{-8}$ and magnetization, $\ensuremath{R_{\rm B}}\equiv B_{\rm RS}/B_{\rm FS}=0.64^{+0.07}_{-0.08}$ of the jet that produced this gamma-ray burst. The low inferred ejecta magnetization disfavors a Poynting flux-dominated outflow. The derived low circum-burst density is consistent with the emerging requirement of low density environments for long-lasting, detectable RS emission to be produced. The MCMC analysis performed here explores degeneracies between the RS and FS parameters for the first time, and can be used to derive the properties of the ejecta and surrounding environment. We have explored deviations of the data from the proposed model, including a steep early optical rise, an excess in the millimeter band on intermediate time scales, and a late-time excess in the X-ray and radio emission, and have placed these observations in the context of similar signatures observed in other events. Detailed multi-frequency observations and modeling of GRBs followed by a summative sample study may provide greater insight into the origin of these deviations. Our results reveal additional degeneracies in the forward shock parameters due to an incomplete treatment of inverse Compton cooling; future work that incorporates the Klein-Nishina corrections may help alleviate this problem, allowing for even better constraints on the underlying physical processes and central engine responsible for GRBs and their afterglows.

# Acknowledgments

We thank the anonymous referee for their helpful suggestions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01454.T (PI: Laskar). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

VLA observations for this study were obtained via project 18A-088 and 18B-407 (PI: Laskar). The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

GMRT observations for this study were obtained via project 35_065 (PI: Laskar). We thank the staff of the GMRT that made these observations possible. GMRT is run by the National Centre for Radio Astrophysics of the Tata Institute of Fundamental Research.

MASTER equipment is supported by the Development Program of Lomonosov MSU and by Moscow Union Optika. MASTER-SAAO is supported by National Research Foundation of South Africa.

MASTER-Tunka equipment is supported by RFMSHE grants 2019-05-592-0001-7293, 2019-05-595-0001-2496 .

We thank J. Rupert for obtaining some of the MDM observations. This work is based in part on observations obtained at the MDM Observatory, operated by Dartmouth College, Columbia University, Ohio State University, Ohio University, and the University of Michigan.

The Bath Astrophysics Group acknowledges support from the University of Bath and the Science and Technologies Facilities Council.

KDA acknowledges support provided by NASA through the NASA Hubble Fellowship grant HST-HF2-51403.001 awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555.

RBD acknowledges support from the National Science Foundation under Grant 1816694.

The Berger Time-Domain Group at Harvard is supported in part by NSF under grant AST-1714498 and by NASA under grant NNX15AE50G.

RC thanks the Kavli Institute for Theoretical Physics for its hospitality while some of this work was completed. This research was supported in part by the National Science Foundation under Grant No. NSF PHY-1748958.

AG acknowledges the financial support from the Slovenian Research Agency (grants P1-0031, I0-0033, and J1-8136) and networking support by the COST Actions CA16104 GWverse and CA16214 PHAROS.

NJ is supported by a Jim and Hiroko Sherwin Studentship in Astrophysics.

RY is in part supported by Grants-in-Aid for KAKENHI grants No. 18H01232.

VL, EG, and NT acknowledge support by the Russian Foundation for Basic Research 17-52-80133.

DAHB acknowledges research support from the National Research Foundation of South Africa.

This work makes use of data supplied by the UK Swift Science Data Centre at the University of Leicester and of data obtained through the High Energy Astrophysics Science Archive Research Center On-line Service, provided by the NASA/Goddard Space Flight Center.

natexlab

(ref: abb+99) Akerlof, C., Balsano, R., Barthelmy, S., et al. 1999, Nature, 398, 400

(ref: alb+17) Alexander, K. D., Laskar, T., Berger, E., et al. 2017, ApJ, 848, 69

(ref: ama06) Amati, L. 2006, MNRAS, 372, 233

(ref: gcn23480) Arimoto, M., Axelsson, M., & Ohno, M. 2018, GRB Coordinates Network, Circular Service, No. 23480, #1 (2018/December-0), 23480

(ref: bdg15) Barniol Duran, R., & Giannios, D. 2015, MNRAS, 454, 1711

(ref: bndp15) Beniamini, P., Nava, L., Duran, R. B., & Piran, T. 2015, MNRAS, 454, 1073

(ref: bck+03) Berger, E., Cowie, L. L., Kulkarni, S. R., et al. 2003a, ApJ, 588, 99

(ref: bkf03) Berger, E., Kulkarni, S. R., & Frail, D. A. 2003b, ApJ, 590, 379

(ref: bkf04) —. 2004, ApJ, 612, 966

(ref: bkp+03) Berger, E., Kulkarni, S. R., Pooley, G., et al. 2003c, Nature, 426, 154

(ref: bm76) Blandford, R. D., & McKee, C. F. 1976, Physics of Fluids, 19, 1130

(ref: bsr+16) Bradley, L., Sipocz, B., Robitaille, T., et al. 2016, Photutils: Photometry tools, ascl:1609.011

(ref: bhn+05) Burrows, D. N., Hill, J. E., Nousek, J. A., et al. 2005, Space Sci. Rev., 120, 165

(ref: ccf+08) Chandra, P., Cenko, S. B., Frail, D. A., et al. 2008, ApJ, 683, 924

(ref: cl00) Chevalier, R. A., & Li, Z.-Y. 2000, ApJ, 536, 195

(ref: dcrgl12) De Colle, F., Ramirez-Ruiz, E., Granot, J., & Lopez-Camara, D. 2012, ApJ, 751, 57

(ref: ew05) Eichler, D., & Waxman, E. 2005, ApJ, 627, 861

(ref: fmm99) Figer, D. F., McLean, I. S., & Morris, M. 1999, ApJ, 514, 202

(ref: fbm+14) Fong, W., Berger, E., Metzger, B. D., et al. 2014, ApJ, 780, 118

(ref: fhlg13) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: fkn+97) Frail, D. A., Kulkarni, S. R., Nicastro, L., Feroci, M., & Taylor, G. B. 1997, Nature, 389, 261

(ref: fsk+05) Frail, D. A., Soderberg, A. M., Kulkarni, S. R., et al. 2005, ApJ, 619, 994

(ref: fwk00) Frail, D. A., Waxman, E., & Kulkarni, S. R. 2000, ApJ, 537, 191

(ref: gvem13) Gat, I., van Eerten, H., & MacFadyen, A. 2013, ApJ, 773, 2

(ref: gkg+08) Gomboc, A., Kobayashi, S., Guidorzi, C., et al. 2008, ApJ, 687, 443

(ref: gkm+09) Gomboc, A., Kobayashi, S., Mundell, C. G., et al. 2009, in American Institute of Physics Conference Series, Vol. 1133, American Institute of Physics Conference Series, ed. . N. G. C. Meegan, C. Kouveliotou, 145–150

(ref: gk03) Granot, J., & Königl, A. 2003, ApJL, 594, L83

(ref: gs02) Granot, J., & Sari, R. 2002, ApJ, 568, 820

(ref: gt05) Granot, J., & Taylor, G. B. 2005, ApJ, 625, 263

(ref: hdpm+12) Holland, S. T., De Pasquale, M., Mao, J., et al. 2012, ApJ, 745, 41

(ref: gcn23488) Izzo, L., de Ugarte Postigo, A., Kann, D. A., et al. 2018, GRB Coordinates Network, Circular Service, No. 23488, #1 (2018/December-0), 23488

(ref: jkck+14) Japelj, J., Kopǎ c, D., Kobayashi, S., et al. 2014, ApJ, 785, 84

(ref: kbdg16) Kathirgamaraju, A., Barniol Duran, R., & Giannios, D. 2016, MNRAS, 461, 1568

(ref: gcn23501) Khanam, T., Sharma, V., Vibhute, A., et al. 2018, GRB Coordinates Network, Circular Service, No. 23501, #1 (2018/December-0), 23501

(ref: kob00) Kobayashi, S. 2000, ApJ, 545, 807

(ref: kps99) Kobayashi, S., Piran, T., & Sari, R. 1999, ApJ, 513, 669

(ref: ks00) Kobayashi, S., & Sari, R. 2000, ApJ, 542, 819

(ref: kz07) Kobayashi, S., & Zhang, B. 2007, ApJ, 655, 973

(ref: gcn23475) Kong, A. K. H. 2018, GRB Coordinates Network, Circular Service, No. 23475, #1 (2018/December-0), 23475

(ref: kmk+15) Kopac, D., Mundell, C. G., Kobayashi, S., et al. 2015, ApJ, 806, 179

(ref: kkysg+08) Krühler, T., Küpcü Yoldas, A., Greiner, J., et al. 2008, ApJ, 685, 376

(ref: kfs+99) Kulkarni, S. R., Frail, D. A., Sari, R., et al. 1999, ApJL, 522, L97

(ref: lbc+18) Laskar, T., Berger, E., Chornock, R., et al. 2018a, ApJ, 858, 65

(ref: lbm+15) Laskar, T., Berger, E., Margutti, R., et al. 2015, ApJ, 814, 1

(ref: lbz+13) Laskar, T., Berger, E., Zauderer, B. A., et al. 2013, ApJ, 776, 119

(ref: lbt+14) Laskar, T., Berger, E., Tanvir, N., et al. 2014, ApJ, 781, 1

(ref: lab+16) Laskar, T., Alexander, K. D., Berger, E., et al. 2016, ApJ, 833, 88

(ref: lbm+18) Laskar, T., Berger, E., Margutti, R., et al. 2018b, ApJ, 859, 134

(ref: lab+18) Laskar, T., Alexander, K. D., Berger, E., et al. 2018c, ApJ, 862, 94

(ref: lag+19) Laskar, T., Alexander, K. D., Gill, R., et al. 2019, ApJL, 878, L26

(ref: ls04) Li, Z., & Song, L. M. 2004, ApJL, 614, L17

(ref: lrz+08) Liang, E.-W., Racusin, J. L., Zhang, B., Zhang, B.-B., & Burrows, D. N. 2008, ApJ, 675, 528

(ref: lyz+10) Liang, E.-W., Yi, S.-X., Zhang, J., et al. 2010, ApJ, 725, 2209

(ref: lkg+10) Lipunov, V., Kornilov, V., Gorbovskoy, E., et al. 2010, Advances in Astronomy, 2010, 349171

(ref: lvg+19) Lipunov, V. M., Vladimirov, V. V., Gorbovskoi, E. S., et al. 2019, Astronomy Reports, 63, 293

(ref: lz04) Lloyd-Ronning, N. M., & Zhang, B. 2004, ApJ, 613, 477

(ref: lcj17) Lyutikov, M., & Camilo Jaramillo, J. 2017, ApJ, 835, 206

(ref: mgl+15) Margutti, R., Guidorzi, C., Lazzati, D., et al. 2015, ApJ, 805, 159

(ref: msd+11) Martini, P., Stoll, R., Derwent, M. A., et al. 2011, PASP, 123, 187

(ref: mkp06) McMahon, E., Kumar, P., & Piran, T. 2006, MNRAS, 366, 575

(ref: mws+07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mkm+10) Melandri, A., Kobayashi, S., Mundell, C. G., et al. 2010, ApJ, 723, 1331

(ref: gcn23469) Mereghetti, S., Gotz, D., Ferrigno, C., et al. 2018, GRB Coordinates Network, Circular Service, No. 23469, #1 (2018/December-0), 23469

(ref: mes06) Mészáros, P. 2006, Reports on Progress in Physics, 69, 2259

(ref: mr93) Meszaros, P., & Rees, M. J. 1993, ApJ, 405, 278

(ref: mr97) Mészáros, P., & Rees, M. J. 1997, ApJL, 482, L29

(ref: mr99) —. 1999, MNRAS, 306, L39

(ref: mgt+11) Metzger, B. D., Giannios, D., Thompson, T. A., Bucciantini, N., & Quataert, E. 2011, MNRAS, 413, 2031

(ref: mg11) Mimica, P., & Giannios, D. 2011, MNRAS, 418, 583

(ref: mvm+07) Molinari, E., Vergani, S. D., Malesani, D., et al. 2007, A&A, 469, L13

(ref: nas09) Nakar, E., Ando, S., & Sari, R. 2009, ApJ, 703, 675

(ref: np04) Nakar, E., & Piran, T. 2004, MNRAS, 353, 647

(ref: nkg+06) Nousek, J. A., Kouveliotou, C., Grupe, D., et al. 2006, ApJ, 642, 389

(ref: odpp+07) Oates, S. R., de Pasquale, M., Page, M. J., et al. 2007, MNRAS, 380, 270

(ref: pk00) Panaitescu, A., & Kumar, P. 2000, ApJ, 543, 66

(ref: pk04) Panaitescu, A., & Kumar, P. 2004, MNRAS, 350, 213

(ref: pkg05) Peng, F., Königl, A., & Granot, J. 2005, ApJ, 626, 966

(ref: phtp17) Perley, D. A., Hjorth, J., Tanvir, N. R., & Perley, R. A. 2017, MNRAS, 465, 970

(ref: pcc+14) Perley, D. A., Cenko, S. B., Corsi, A., et al. 2014, ApJ, 781, 37

(ref: gcn23470) Podesta, R., Lopez, C., Podesta, F., et al. 2018, GRB Coordinates Network, Circular Service, No. 23470, #1 (2018/December-0), 23470

(ref: pbp+08) Poole, T. S., Breeveld, A. A., Page, M. J., et al. 2008, MNRAS, 383, 627

(ref: rks+08) Racusin, J. L., Karpov, S. V., Sokolowski, M., et al. 2008, Nature, 455, 183

(ref: rm92) Rees, M. J., & Meszaros, P. 1992, MNRAS, 258, 41P

(ref: rm94) —. 1994, ApJL, 430, L93

(ref: rl17) Ressler, S. M., & Laskar, T. 2017, ApJ, 845, 150

(ref: rho99) Rhoads, J. E. 1999, ApJ, 525, 737

(ref: rkm+05) Roming, P. W. A., Kennedy, T. E., Mason, K. O., et al. 2005, Space Sci. Rev., 120, 95

(ref: se01) Sari, R., & Esin, A. A. 2001, ApJ, 548, 787

(ref: sm00) Sari, R., & Mészáros, P. 2000, ApJL, 535, L33

(ref: sp99a) Sari, R., & Piran, T. 1999a, ApJL, 517, L109

(ref: sp99) —. 1999b, ApJ, 520, 641

(ref: sph99) Sari, R., Piran, T., & Halpern, J. P. 1999, ApJL, 519, L17

(ref: spn98) Sari, R., Piran, T., & Narayan, R. 1998, ApJL, 497, L17+

(ref: sf11) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103

(ref: sd07) Shao, L., & Dai, Z. G. 2007, ApJ, 660, 1319

(ref: sb11) Shivvers, I., & Berger, E. 2011, ApJ, 734, 58

(ref: gcn23499) Siegel, M. H., & Cannizzo, J. K. 2018, GRB Coordinates Network, Circular Service, No. 23499, #1 (2018/December-0), 23499

(ref: ssr+04) Steele, I. A., Smith, R. J., Rees, P. C., et al. 2004, in Proc. SPIE, Vol. 5489, Ground-based Telescopes, ed. J. M. Oschmann, Jr., 679–692

(ref: gcn23495) Svinkin, D., Golenetskii, S., Aptekar, R., et al. 2018, GRB Coordinates Network, Circular Service, No. 23495, #1 (2018/December-0), 23495

(ref: tlm+17) Troja, E., Lipunov, V. M., Mundell, C. G., et al. 2017, Nature, 547, 425

(ref: uso92) Usov, V. V. 1992, Nature, 357, 472

(ref: vdhpdb+14) van der Horst, A. J., Paragi, Z., de Bruyn, A. G., et al. 2014, MNRAS, 444, 3151

(ref: vhb14) Vurm, I., Hascoët, R., & Beloborodov, A. M. 2014, ApJL, 789, L37

(ref: wkf98) Waxman, E., Kulkarni, S. R., & Frail, D. A. 1998, ApJ, 497, 288

(ref: wb06) Woosley, S. E., & Bloom, J. S. 2006, ARA&A, 44, 507

(ref: yc02) Yun, M. S., & Carilli, C. L. 2002, ApJ, 568, 88

(ref: zk05) Zhang, B., & Kobayashi, S. 2005, ApJ, 628, 315

(ref: zkm03) Zhang, B., Kobayashi, S., & Mészáros, P. 2003, ApJ, 595, 950

(ref: zlp+07) Zhang, B., Liang, E., Page, K. L., et al. 2007, ApJ, 655, 989

(ref: zwd05) Zou, Y. C., Wu, X. F., & Dai, Z. G. 2005, MNRAS, 363, 93

[^1]: <http://www.swift.ac.uk/xrt_positions/00020848/>

[^2]: Obtained from the *Swift* website at <http://www.swift.ac.uk/xrt_curves/00020848> and re-binned to a minimum signal-to-noise ratio per bin of 8.

[^3]: <http://www.swift.ac.uk/swift_portal>

[^4]: MASTER Clear band ($CR$) magnitudes are best described by the ratio, $CR = 0.8R + 0.2B$.

[^5]: We use the convention $F_{\nu}\propto t^{\alpha}\nu^{\beta}$ throughout.

[^6]: The deviation of this low-frequency power law from the expected value of $\beta\approx2$ arises from a contribution from an underlying $\nu^{1/3}$ power law extending down from the mm band (Section [4](#text:multimodel)).

[^7]: $F_{\nu} = F_{\rm b} \left[
     \frac{1}{2} \left(\frac{\nu}{\nu_{\rm b}}\right)^{-y\beta_1} + 
     \frac{1}{2} \left(\frac{\nu}{\nu_{\rm b}}\right)^{-y\beta_2} 
     \right]^{-1/y}.$ We fix $y=3$ in this fit to emulate a moderately smooth break.

[^8]: When $p\approx2$, the effect of KN corrections on the evolution of $\nu_{\rm c}$ with time, and hence on the light curve above $\ensuremath{\nu_{\rm c}}$, is small. However, the spectral corrections remain, and in particular, we may have $\ensuremath{\nu_{\rm c}}< 
    \widehat{\nu}_{\rm c} < \ensuremath{\nu_{\rm X}}$, which would result in a spectral index of $\beta\approx-0.75$ (cite: nas09). Here $\widehat{\nu}_{\rm c}/\ensuremath{\nu_{\rm c}}= (\widehat{\gamma}_{\rm c}/\gamma_{\rm c})^2$, $\widehat{\gamma}_{\rm c} = \gamma_{\rm self}^3/\gamma_{\rm c}^2$, $\gamma_{\rm self} = (B_{\rm 
    QED}/B)^{1/3}$, $B$ is the post-shock magnetic field, and $B_{\rm QED}$ is the quantum critical field.

[^9]: We opt to fit for the observable quantities rather than the derived quantities of $\ensuremath{\Gamma_{0}}$, $\ensuremath{t_{\rm dec}}$, and $\ensuremath{R_{\rm B}}$ for the RS, as these observables uniquely specify the RS spectrum independent of the FS parameters during the fitting process.

[^10]: The FS dynamics during shock crossing for a shell with a uniform $\Gamma_{0}$ is equivalent to energy injection at the rate $E\propto t$ (cite: lbm+15).

[^11]: the Lorentz factor of the FS is $\Gamma\approx10$ at 40 days.

</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "FS electron index p = 2.11 dimensionless",
  "failed_quote": "$p$ & $2.11$ & $2.11\\pm0.01$"
 }
]
```
