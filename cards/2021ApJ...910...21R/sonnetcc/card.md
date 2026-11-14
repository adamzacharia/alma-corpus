# A Broadband View on Microquasar MAXI J1820+070 during the 2018 Outburst

`2021ApJ...910...21R` | The Astrophysical Journal 2021 | first author: Rodi, J. | arXiv: 2101.10767 | DOI: 10.3847/1538-4357/abdfd0

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, stellar_physics
- Question: Build a quasi-simultaneous radio-to-hard-X-ray SED of MAXI J1820+070 on 12 April 2018 and model it with a leptonic jet, irradiated disk and corona  
  > "Therefore we compiled quasi-simultaneous observations from public archives, Astronomer’s Telegrams, and Gamma-ray Coordination Network Circulars to construct the widest possible frequency range" (Introduction); "we studied the spectral components independently before investigating them jointly by constructing a model consisting of a leptonic jet, an irradiated disk, and a corona" (Introduction)
- Target **MAXI J1820+070 (=ASASSN-18ey)**: coordinates _not stated_; z/distance d = 3 kpc  
  > "The low-mass X-ray binary MAXI J$1820+070$ (=ASASSN-18ey) was first detected on 6.59 March 2018" (Introduction); "we fix the distance of jet from the observer to the value of $d=3$ kpc" (Phenomenological Model Setup); distance from Bright et al. 2020 (cite: 2020NatAs.tmp....2B)  
  > "The low-mass X-ray binary MAXI J$1820+070$ (=ASASSN-18ey) was first detected on 6.59 March 2018" (Introduction); "we fix the distance of jet from the observer to the value of $d=3$ kpc" (Phenomenological Model Setup)

## Data provenance

- ALMA projects: 2017.1.01103.T
- bands: Band 7  
  > "(Band 7, spw 5, 7, 9, 11)" (ALMA)
- frequencies and spectral setup: 4 spectral windows (spw 5, 7, 9, 11) at central frequencies 336, 338, 348, 350 GHz, imaged separately  
  > "version 5.1.1, separately for each one of the 4 spectral windows (spw) present in the data (Band 7, spw 5, 7, 9, 11) corresponding to the following central frequencies: 336 GHz, 338 GHz, 348 GHz, 350 GHz" (ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 12 April 2018, 08:13:18 to 09:20:16 UTC  
  > "covering different bands from radio to gamma-ray on April 12, 2018" (Observations); "08:13:18 12-04-2018" (Table 1); "09:20:16 12-04-2018" (Table 1)
- pi or archival as stated: Archival: retrieved from the ESO archive  
  > "data for project 2017.1.01103.T were retrieved from the ESO archive" (ALMA)
- Other facility **JVLA (project VLA/18A-470)**: Radio flux densities at 4.7, 7.5, 8.5, 11, 20.7, 25.5 GHz from retrieved calibrated archive data  
  > "We retrieved calibrated Karl G. Jansky Very Large Array (VLA) data for experiment VLA/18A-470 from the National Radio Astronomy (NRAO) online archive." (JVLA); "The JVLA antennas, in A configuration, were split in 3 subarrays in order to obtain simultaneous observations at 6 different central frequencies (4.7 GHz, 7.5 GHz, 8.5 GHz, 11 GHz, 20.7 GHz, 25.5 GHz)." (JVLA)
- Other facility **VLITE**: Low-frequency radio flux density (3.39E+08 Hz) taken from the literature  
  > "we considered Very Large Array Low-band Ionosphere and Transient Experiment (VLITE, (cite: 2016SPIE.9906E..5BC)), also collected on 12 April 2018 (cite: 2018ATel11540....1P)" (The compact jet emission)
- Other facility **VLT/X-shooter (ESO program 0101.D-0356(A))**: NIR to UV continuum flux densities (12 photometric points) and optical wind line profiles  
  > "We retrieved the processed spectra obtained during the 2018 outburst on 12 April from the European Southern Observatory (ESO) archive science portal." (VLT/X-shooter); "In this way, we calculated 12 photometric measurements (Table 2) covering the interval from NIR to UV." (The compact jet emission)
- Other facility **XMM-Newton/EPIC-pn**: Soft X-ray spectrum (0.5-12 keV)  
  > "*XMM-Newton* ToO observations were carried out from 2018-04-12 07:27:58 to 09:39:28 UTC (obsid 0820880501) using burst mode." (XMM-Newton/EPIC-pn)
- Other facility **INTEGRAL (ISGRI and OMC)**: Hard X-ray spectrum (30-400 keV) and optical flux  
  > "The data were analyzed using the Offline Science Analysis software (OSA) v11.0 available at the *INTEGRAL* Science Data Center (ISDC)." (INTEGRAL)
- External data: Source distance 3 kpc  
  > "we fix the distance of jet from the observer to the value of $d=3$ kpc" (Phenomenological Model Setup) [from Bright et al. 2020 (cite: 2020NatAs.tmp....2B)]
- External data: Jet speed and viewing angle (beta_jet = 0.89, theta_obs = 63 deg), giving beaming factor of about 2.2  
  > "using the values of $\beta_{jet}=0.89$ and $\theta_{obs}= 63^{\circ}$ reported in (cite: 2020NatAs.tmp....2B)" (Phenomenological Model Setup) [from Bright et al. 2020 (cite: 2020NatAs.tmp....2B)]
- External data: Radio jet extends to about 1e15 cm  
  > "extends up to a distance of $\approx 1\times 10^{15}$ cm according to (cite: 2020NatAs.tmp....2B)" (Broadband SED modelling) [from Bright et al. 2020 (cite: 2020NatAs.tmp....2B)]
- External data: VLITE flux density on 12 April 2018  
  > "also collected on 12 April 2018 (cite: 2018ATel11540....1P)" (The compact jet emission) [from Polisensky et al. 2018 ATel 11540 (cite: 2018ATel11540....1P)]
- External data: Foreground extinction A_V = 0.627 mag with R(V) = 3.1  
  > "with R(V)=3.1 and A$_V$=0.627 mag (cite: Schlafly11)" (VLT/X-shooter) [from Schlafly & Finkbeiner 2011 (cite: Schlafly11)]

## Processing

### Calibration

- pipeline or manual: Data pipelined at the Italian ARC node (INAF-IRA, Bologna)  
  > "and pipelined at the the Italian node of the European ALMA Regional Centre (INAF-Istituto di Radioastronomia, Bologna)" (ALMA)
- casa version: CASA 5.1.1 (stated for imaging)  
  > "version 5.1.1, separately for each one of the 4 spectral windows (spw) present in the data" (ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA imaging and central frequencies of the 4 spectral windows cite Bonato et al. 2018  
  > "(Band 7, spw 5, 7, 9, 11) corresponding to the following central frequencies: 336 GHz, 338 GHz, 348 GHz, 350 GHz (cite: 2018MNRAS.478.1512B)" (ALMA) [from (cite: 2018MNRAS.478.1512B)]
- Detailed description of the JetSeT jet/disk model deferred to a paper in preparation  
  > "A more accurate description of the model is discussed in (cite: TramacereInPrep)." (Broadband SED modelling) [from (cite: TramacereInPrep)]
- Fixed disk irradiation parameters r_irr = 1.1 and f_in = 0.1 in the JetSeT fit  
  > "and the parameters $r_{irr}=1.1$ and $f_{in}=0.1$, the choice adopted in (cite: DiskIrrModel2009)" (Initial model setup) [from (cite: DiskIrrModel2009)]
- Cutoff power-law component added to the hard X-ray CompTT fit  
  > "Following (cite: 2019ApJ...870...92R), a cutoff power-law was added" (Hard X-ray) [from (cite: 2019ApJ...870...92R)]
- Disk wind search in X-shooter lines follows the earlier analysis  
  > "Following the (cite: 2019ApJ...879L...4M) analysis, we explored the presence of wind signatures linked to the mentioned emission lines" (Accretion disk winds) [from (cite: 2019ApJ...879L...4M)]
- Multi-zone radio jet built as a sum of single zones  
  > "following the approach of (cite: Kaiser2006)" (Radio Jet) [from (cite: Kaiser2006)]
- Jet launching position z_0 = 50 R_S taken from earlier reference values  
  > "it is chosen according to reference values published in previous analysis (cite: Romero2010)" (Phenomenological Model Setup) [from (cite: Romero2010)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details: pipeline version, flux and bandpass calibrators, flux-scale accuracy, whether any self-calibration was applied
- ALMA imaging settings: tclean parameters (weighting, robust, cell, image size, deconvolver, masking, threshold) and the continuum or line-free channel selection in each spw
- How the source flux density was measured in the ALMA images (aperture, point-source fit, or peak) and any primary beam correction
- ALMA array configuration, baselines, angular resolution, time on source and rms (only start and stop times are tabulated)
- Which Table 2 points were included in each fit and how the X-shooter continuum intervals were chosen
- JetSeT version and Minuit minimizer settings
- JVLA, VLITE and X-shooter reduction details beyond 'standard procedures'

## Analysis recipe

1. **Image the ALMA Band 7 data and obtain continuum flux densities**: Pipelined ALMA data imaged with CASA separately for each of the 4 spectral windows; resulting flux densities listed in Table 2  
  > "version 5.1.1, separately for each one of the 4 spectral windows (spw) present in the data" (ALMA)
   - software: CASA
   - parameter: spw 5, 7, 9, 11 at 336, 338, 348, 350 GHz  
  > "(Band 7, spw 5, 7, 9, 11) corresponding to the following central frequencies: 336 GHz, 338 GHz, 348 GHz, 350 GHz" (ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build the jet SED and fit a broken power law**: Combine JVLA, VLITE, ALMA, X-shooter continuum and OMC points; fit radio-to-optical data with a broken power law to get the synchrotron peak and the optically thick and thin slopes, and fit the 0.3-10 GHz radio SED with a power law  
  > "We fitted the radio to optical data set with a broken-power law to identify the synchrotron peak frequency and the spectral slopes of the optically thin and thick regions" (The compact jet emission); "For X-shooter, we considered only the part of the spectrum not affected by absorption/emission features, and averaged values for each of these intervals to obtain continuum flux density values." (The compact jet emission)
   - software: Astropy
   - parameter: Data points below 20 GHz excluded from the broken-power-law fit  
  > "Similarly, we did not consider data points below 20 GHz, since they show a different slope, probably belonging to a physically distinct (and more expanded) radio jet component." (The compact jet emission)
   - fitting: Levenberg-Marquardt least squares (Astropy BrokenPowerLaw1D with LevMarLSQFitter)  
  > "We used the Astropy `BrokenPowerLaw1D` function (see (cite: astropy:2013; astropy:2018)) adopting the `LevMarLSQFitter` routine to perform a Levenberg-Marquardt least squares statistic." (The compact jet emission)
   - validation: _not stated_
3. **Fit XMM and INTEGRAL X-ray spectra and an irradiated disk model**: Fit XMM and INTEGRAL spectra with Comptonization models, a joint 0.5-400 keV fit, then a near-IR to hard X-ray fit with the diskir irradiated disk model with and without an extra power law  
  > "To characterize the X-ray spectrum, a joint fit was performed between the two instruments spanning $0.5 - 400$ keV using the model `Tbabs*Reflect*(diskbb+CompTT)+Tbabs*cutoff`" (Soft X-ray); "Subsequently, we fit our data from the near-IR to hard X-rays using an irradiated disk model to compare with (cite: 2018ApJ...868...54S)" (IR - Hard X-ray Spectrum)
   - software: XSPEC
   - parameter: 1.5% systematic error added to the INTEGRAL data  
  > "A systematic 1.5 % error was added to the data, following OSA 11 standard recommendations" (Hard X-ray)
   - assumption: Accretion luminosity computed for a distance of 3 kpc  
  > "found a value of $\sim 6 \times 10^{37}$ erg/s for a distance 3 kpc" (Soft X-ray)
   - fitting: Chi-square fitting in XSPEC  
  > "A power-law fit to the data in `XSPEC` found a photon index of" (Hard X-ray)
   - validation: F-test used to justify the added power-law component in the diskir fit  
  > "with an f-test probability of $3.7 \times 10^{-8}$" (IR - Hard X-ray Spectrum)
4. **Fit the full broadband SED with the JetSeT jet, disk and corona model**: Fit DiskIrrComp and Comp. hump first over nu = 5e14 to 1e20 Hz, then freeze most disk parameters and fit the global model including JetAcc and RadioJet over the full SED band  
  > "We fit first the `DiskIrrComp` and `Comp. hump` components restricting the fit range to $\nu$= $[5\times 10^{14},10^{20}]$ Hz" (Model fit results for the Disk and Corona emission); "and we fit the global model over the full SED band in the range $\nu$= $[5\times 10^{8},10^{20}]$ Hz" (Model fit results for the jet emission)
   - software: JetSeT, Minuit
   - parameter: 5% systematic error added over 1e8 to 1e16 Hz  
  > "we have added a 5% systematic error in the range $[1\times 10^{8},1\times 10^{16}]$ Hz" (Initial model setup)
   - parameter: Jet launch distance z_0 = 50 R_S, initial jet radius 0.1 z_0, q_jet = 0.2 for the phenomenological setup  
  > "We assume that the jet is launched at a distance $z=z_{0}$ from the BH with $z_0=50 R_S\approx 1.2 \times 10^{8}$ cm" (Phenomenological Model Setup); "setting $q_{jet}=0.2$ we obtain $B_0\approx 6.8 \times 10^{6}$ G" (Phenomenological Model Setup)
   - assumption: Black hole mass 8 solar masses  
  > "We use a black hole mass of $M_{BH}= 8 M_{\Sun}$." (Phenomenological Model Setup)
   - assumption: Ballistic jet with toroidal-dominated magnetic field and constant bulk Lorentz factor  
  > "This choice assumes that the jet is very close to the ballistic regime, with a magnetic field dominated by the toroidal component" (Phenomenological Model Setup)
   - assumption: Only synchrotron cooling in the radio jet  
  > "In our analysis we take into account only synchrotron cooling" (Radio Jet)
   - fitting: Frequentist fit with Minuit; errors from MIGRAD only, no MCMC  
  > "In the current analysis we use a frequentist approach and we use the  `Minuit`  `ModelMinimizer` option." (Initial model setup); "For the error estimate we provide only errors derived form the" (Initial model setup)
   - validation: Compared with XSPEC diskir fit parameters; model said to reproduce the UV-to-optical emission and flat radio spectrum  
  > "we find that our assumption based on the connection between a compact acceleration region feeding the extended radio jet is able to model self-consistently the UV-to-optical emission, reproducing the observed flat radio spectrum" (Model fit results for the jet emission)
5. **Fit X-shooter wind line profiles**: Normalise spectra by a spline continuum, search for absorption troughs in He I and H-alpha, fit multi-component Gaussians to the line profiles  
  > "We consider as bona-fide absorption troughs the ones with a dip of at least three times the continuum RMS." (Accretion disk winds); "by applying multi-component Gaussian fits using the `python` packages `curvefit` and `leastsq`" (Accretion disk winds)
   - software: IRAF, python curvefit/leastsq
   - parameter: H-alpha fit region 644-670 nm; He I 6678 fit region 664-672 nm  
  > "The H$\alpha$ line analysis has been performed in the wavelength region 644$-$670 nm" (Accretion disk winds); "we used the wavelength region $664-672$ nm" (Accretion disk winds)
   - fitting: Multi-component Gaussian least squares  
  > "by applying multi-component Gaussian fits using the `python` packages `curvefit` and `leastsq`" (Accretion disk winds)
   - validation: _not stated_

## Software

- **CASA (ALMA imaging)** 5.1.1: Imaging of the ALMA Band 7 spectral windows  
  > "version 5.1.1, separately for each one of the 4 spectral windows (spw) present in the data" (ALMA)
- **CASA (JVLA imaging)** 5.6.2: Imaging of the JVLA data  
  > "Data were imaged using `CASA` (`Common Astronomy Software Applications` package) version 5.6.2" (JVLA)
- **JetSeT** : Broadband SED modelling with jet, irradiated disk and corona components  
  > "We modelled the broadband SED of MAXI J1820+070 using a combination of jet leptonic models and irradiated disk and corona model implemented in Jets SED modeler and fitting Tool (`JetSeT`)" (Broadband SED modelling)
- **Astropy** : Broken power-law and power-law fits to the radio-to-optical SED  
  > "We used the Astropy `BrokenPowerLaw1D` function (see (cite: astropy:2013; astropy:2018)) adopting the `LevMarLSQFitter` routine to perform a Levenberg-Marquardt least squares statistic." (The compact jet emission)
- **XSPEC** : X-ray spectral fitting of INTEGRAL and XMM data  
  > "A power-law fit to the data in `XSPEC` found a photon index of" (Hard X-ray)
- **Minuit** : Minimizer for the JetSeT global fit  
  > "In the current analysis we use a frequentist approach and we use the  `Minuit`  `ModelMinimizer` option." (Initial model setup)
- **SAS** xmmsas_20190531_1155-18.0.0: Reduction of XMM-Newton EPIC-pn data  
  > "The European Photon Imaging Camera (EPIC)-pn data were analyzed using the standard procedures with the Science Analysis System (SAS) software version" (XMM-Newton/EPIC-pn)
- **OSA** v11.0: Analysis of INTEGRAL ISGRI and OMC data  
  > "The data were analyzed using the Offline Science Analysis software (OSA) v11.0 available at the *INTEGRAL* Science Data Center (ISDC)." (INTEGRAL)
- **ESO X-shooter pipeline** V2.7.0: Reduction of X-shooter spectra  
  > "These data have been reduced by using the ESO X-shooter pipeline V2.7.0" (VLT/X-shooter)
- **IRAF** : Continuum normalisation of X-shooter spectra (task continuum)  
  > "We normalized these spectra by dividing them for the continuum emission, fitted with a third order spline3 function by using the IRAF task `continuum`." (Accretion disk winds)
- **python curvefit/leastsq** : Multi-component Gaussian fits to emission line profiles  
  > "by applying multi-component Gaussian fits using the `python` packages `curvefit` and `leastsq`" (Accretion disk winds)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA flux density, spw at 3.36E+11 Hz | 0.116 | 0.006 | Jy | 1 | 0.116$\pm$0.006 |
| ALMA flux density, spw at 3.38E+11 Hz | 0.114 | 0.006 | Jy | 1 | 0.114$\pm$0.006 |
| ALMA flux density, spw at 3.48E+11 Hz | 0.115 | 0.006 | Jy | 1 | 0.115$\pm$0.006 |
| ALMA flux density, spw at 3.50E+11 Hz | 0.110 | 0.006 | Jy | 1 | 0.110$\pm$0.006 |
| Synchrotron peak frequency (broken power-law fit) | 1.6e13 | 0.2e13 | Hz | 2 | We obtained a synchrotron peak frequency of 1.6$\pm$0.2$\times10^{13}$ Hz. |
| Optically thick spectral index alpha_thick | 0.28 | 0.02 | dimensionless | 2 | The estimated slope for the optically thick part of the spectrum is $\alpha_{thick}=0.28\pm0.02$ and $\alpha_{thin}=-0.61\pm0.01$ for the optically thin one |
| Optically thin spectral index alpha_thin | -0.61 | 0.01 | dimensionless | 2 | The estimated slope for the optically thick part of the spectrum is $\alpha_{thick}=0.28\pm0.02$ and $\alpha_{thin}=-0.61\pm0.01$ for the optically thin one |
| Low-frequency (0.3-10 GHz) radio spectral index | 0.11 | 0.02 | dimensionless | 2 | The slope of the lower frequency radio SED (0.3$-$10 GHz), fitted with the `PowerLaw1D` Astropy function, is $\alpha=0.11\pm0.02$. |
| Accretion luminosity (1-200 keV) | ~6e37 | not stated | erg/s | 3 | we calculated the accretion luminosity in the $1 - 200$ kev energy range and found a value of $\sim 6 \times 10^{37}$ erg/s for a distance 3 kpc |
| Joint XMM+INTEGRAL fit electron temperature kT and optical depth tau | kT = 27 keV, tau = 2.2 | kT +/- 1 keV, tau +/- 0.1 | keV; dimensionless | 3 | $kt_{BB} = 0.27 \pm 0.01 \textrm{ keV, } kT = 27 \pm 1 \textrm{ keV, and } \tau = 2.2 \pm 0.1 \textrm{ with } \chi^2 / \nu = 0.95$ |
| JetSeT global fit chi-square | 181 for 122 dof (reduced 1.48) | not stated | dimensionless | 4 | The model fit converged with a final $\chi^2 = 181$ for 122 degree of freedom ($N_{dof}$), corresponding to a $\chi^2_{red}=1.48$. |
| Disk outer-irradiation fraction f_out from JetSeT fit | 7.33e-3 | 0.15e-3 | dimensionless | 4 | adding the jet component results in a better constraint on the value of $f_{out}$=$(7.33\pm0.15)\times10^{-3}$ |
| Acceleration-region magnetic field and radius (best-fit model) | B ~ 1.8e4 G, R ~ 2.6e9 cm | not stated | G; cm | 4 | gives a magnetic field in the acceleration region of $\approx 1.8 \times 10^4$ G, and a region radius of $\approx 2.6 \times 10^9$ cm |
| Jet luminosity (lower limit) | >= 8.0e37 (0.15 L_Edd) | lower limit | erg/s | 4 | We found that the relativistic jet required a total energy of $L_{jet}\geq 8.0\times10^{37}$ erg/s, corresponding to 0.15 $L_{Edd}$. |
| Radio-jet field index m_jet | ~1.2 | not stated | dimensionless | 4 | the best-fit index $m_{jet}\approx 1.2$ |
| He I 5876 wind terminal velocity | 880 | not stated | km/s | 5 | This one has a $v_t$ of 880 km/s. |
| H-alpha broad red wing outflow velocity | 923 | 14 | km/s | 5 | we derive an outflow velocity of $v$= (923$\pm$14) km/s |

## Qualitative findings

- The source was in the hard state on 12 April 2018, with a flat/inverted radio spectrum and optical disk winds  
  > "The flat/inverted radio spectrum and the accretion disk winds seen at optical wavelengths are also consistent with the hard state." (abstract)
- The jet is a lower limit on power because only cold protons are assumed for the hadronic content  
  > "This value represents a lower limit, since we assume that the hadronic content of the jets is only in terms of cold protons, without a significant radiative contribution." (Discussion and Conclusions)

## Claim tuples

- H: Is MAXI J1820+070 in the hard state at the 12 April 2018 epoch? | E: Comptonization fits to XMM and INTEGRAL spectra, radio spectral shape and optical wind lines | R: kT about 27 keV, tau about 2.2 in the joint fit; flat/inverted radio spectrum | F: The source is a black hole binary in the hard state | **supported**
- H: Which components dominate the SED across frequency? | E: JetSeT broadband fit with jet, irradiated disk and corona | R: Jet-dominated to about 1e14 Hz, disk and corona above | F: The jet dominates up to the near-IR/optical | **supported**
- H: Can the flat radio spectrum arise from the cooling of electrons leaving a compact acceleration region? | E: RadioJet zones fed by the acceleration region with synchrotron cooling, fit to the SED | R: Best-fit m_jet about 1.2 reproduces the flat radio spectrum | F: Flat radio spectrum follows naturally from synchrotron cooling of accelerated electrons | **supported**
- H: Is the jet powered mainly by accretion? | E: Compare the JetSeT jet luminosity lower limit with the X-ray accretion luminosity | R: L_jet >= 8e37 erg/s versus L_acc about 6e37 erg/s at 3 kpc | F: Jet could be powered mainly by accretion, with a small Blandford-Znajek contribution | **partially**
- H: Are optical disk winds still present at this epoch? | E: Absorption trough search and Gaussian fits to He I and H-alpha lines in X-shooter spectra | R: He I 5876 trough with v_t = 880 km/s; H-alpha red-wing outflow of 923 km/s | F: Winds are present but slower than in earlier hard-state epochs | **supported**

## Reasoning

- Why this data: Quasi-simultaneous public archive data give the widest possible frequency range  
  > "Therefore we compiled quasi-simultaneous observations from public archives, Astronomer’s Telegrams, and Gamma-ray Coordination Network Circulars to construct the widest possible frequency range" (Introduction)
- Why this method: Irradiated disk fit chosen to compare with an earlier analysis of 24 March data  
  > "Subsequently, we fit our data from the near-IR to hard X-rays using an irradiated disk model to compare with (cite: 2018ApJ...868...54S)" (IR - Hard X-ray Spectrum)
- Alternative: Adding a power-law component to the diskir fit improved the fit at high energies over diskir alone  
  > "We found that including a power-law component improved the fit at high energies" (IR - Hard X-ray Spectrum)
- How they decided it was enough: _not stated_
- Limitation (authors): Parameter errors come only from MIGRAD; MCMC deferred to future work  
  > "a more reliable estimate based on a Markov chain Monte Carlo (MCMC) will be presented in" (Initial model setup)
- Limitation (authors): Fit may be biased by parameter degeneracies  
  > "even though the fit might be biased by the degeneracy among some parameters" (Model fit results for the jet emission)
- Caveat (inferred, ours): ALMA enters as four continuum flux densities with no imaging or flux-calibration details, so the ALMA points cannot be independently checked from the paper
- Caveat (inferred, ours): Abstract quotes B ~ 1.6e4 G and R ~ 2.8e9 cm while the text gives 1.8e4 G and 2.6e9 cm; the Table 4 value of B_acc in the setup list is printed as 1.8e-4 G; the VLITE flux error 5.3 is implausible
- Caveat (inferred, ours): Error bars come only from MIGRAD with a frozen-parameter fit and a 5% systematic floor, so uncertainties on jet parameters are likely underestimated
- Caveat (inferred, ours): Distance of 3 kpc, black hole mass of 8 solar masses and jet geometry are assumed or borrowed, and the jet luminosity scales with them

## Reproducibility

- Data public (paper): ALMA data retrieved from the ESO archive; X-shooter from the ESO archive; JVLA from the NRAO archive  
  > "data for project 2017.1.01103.T were retrieved from the ESO archive" (ALMA); "We retrieved calibrated Karl G. Jansky Very Large Array (VLA) data for experiment VLA/18A-470 from the National Radio Astronomy (NRAO) online archive." (JVLA)
- Products in archive: _not stated_
- Code: JetSeT is a public code with an ASCL entry; the authors' own fit scripts are not stated as released  
  > "JetSeT: Numerical modeling and SED fitting tool for relativistic jets." (References)
- Missing: ALMA calibration and imaging recipe and the method used to extract flux density
- Missing: JetSeT version and exact fit scripts
- Missing: Selection of X-shooter continuum windows
- Data volume (inferred): Roughly tens of GB for the raw ALMA Band 7 execution (about 1 h), plus the other archives
- Score (inferred): 3/5, Public data and a public code with tabulated starting values and bounds allow redoing the JetSeT fit from Table 2, but the ALMA reduction and flux extraction are not specified.
- Rediscovery candidate: no, ALMA is a minor input (four flux points) and its imaging and flux-extraction recipe is incomplete; the main results come from multi-facility SED modelling.

## Links

- Method: Bonato et al. 2018 (cite: 2018MNRAS.478.1512B) (Cited alongside the ALMA imaging and spectral window frequencies)
- Method: Tramacere 2020 JetSeT (cite: jetsetascl) (SED modelling code)
- Method: Gierlinski, Done & Page 2009 (cite: DiskIrrModel2009) (diskir irradiated disk model and fixed parameter choices)
- Companion: Bright et al. 2020 (cite: 2020NatAs.tmp....2B) (Distance, jet speed, viewing angle and radio jet extent)
- Companion: Munoz-Darias et al. 2019 (cite: 2019ApJ...879L...4M) (Optical disk wind analysis followed here)
- Companion: Shidatsu et al. 2018 (cite: 2018ApJ...868...54S) (Irradiated disk fit to 24 March data used for comparison)
- Companion: Roques & Jourdain 2019 (cite: 2019ApJ...870...92R) (Hard X-ray cutoff power-law model followed)
- Related: ESO program 0101.D-0356(A)
- Related: VLA/18A-470
- Related: XMM-Newton obsid 0820880501

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 67,
  "rate": 0.657
 },
 "evidence_ok": true
}
```
