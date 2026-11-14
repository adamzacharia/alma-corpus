# Observing radio transients with Phased ALMA: Pulses from the Galactic Centre magnetar

`2025A&A...701A.191V` | Astronomy and Astrophysics 2025 | first author: Vera-Casanova, J. | arXiv: 2504.06234 | DOI: 10.1051/0004-6361/202555088

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: stellar_physics, transients
- Question: Can Phased ALMA at Band 3 detect and characterize single pulses and the cumulative energy distribution of the Galactic Centre magnetar PSR J1745-2900, and what are the prospects for observing radio transients (pulsars and FRBs) with Phased ALMA?  
  > "We studied the Galactic Centre (GC) magnetar, PSR J1745-2900, as a laboratory for magnetars in complex magneto-turbulent environments and for linking with FRBs." (abstract); "We searched for the magnetar –single pulses to link them to FRB emission. We examined the potential of phased ALMA to open a window to higher frequency observations of radio transients." (Introduction)
- Target **PSR J1745-2900**: coordinates 17:45:40.1662(8) -29:00:29.89(1)  
  > "Right ascension, $\alpha$ (J2000) | 17:45:40.1662(8)" (Table 3); "Declination, $\delta$ (J2000) | $-$29:00:29.89(1)" (Table 3); "where D corresponds to the source luminosity distance, equal to 8.3 kpc (cite: yim)." (Pulse characterisation); z/distance 8.3 kpc  
  > "Right ascension, $\alpha$ (J2000) | 17:45:40.1662(8)" (Table 3); "Declination, $\delta$ (J2000) | $-$29:00:29.89(1)" (Table 3); "where D corresponds to the source luminosity distance, equal to 8.3 kpc (cite: yim)." (Pulse characterisation); distance from (cite: yim)  
  > "Right ascension, $\alpha$ (J2000) | 17:45:40.1662(8)" (Table 3); "Declination, $\delta$ (J2000) | $-$29:00:29.89(1)" (Table 3); "where D corresponds to the source luminosity distance, equal to 8.3 kpc (cite: yim)." (Pulse characterisation)

## Data provenance

- ALMA projects: 2017.1.00795.V
- bands: Band 3 (3.5 mm, 86 GHz)  
  > "We used observations of Sgr A* from the 2017 GMVA campaign at 3.5 mm (Project Code: 2017.1.00795.V, PI: M. Johnson)." (Observations); "The observations were carried out on April 3, using 37 12m antennas in Band 3 configuration centred at 86 GHz (cite: Liu_2021)." (Observations)
- frequencies and spectral setup: 86.268 GHz central frequency (85.268-87.268 GHz), 2000 MHz bandwidth, 32 frequency channels, 62.5 MHz channel width, 32 microsecond sample time  
  > "ALMA (Band 3) | 85.268 | 87.268 | 86.268 | 2000 | 32 | 46 | 1" (Table 1); "As discussed in (cite: Liu_2021), the data was converted to PSRFITS format (cite: psrfits) with full Stokes information (I,Q,U,V) and 32 frequency channels, each with a 62.5 MHz channel width." (Observations)
- continuum bandwidth: 2 GHz  
  > "Table notes: The data is centered at 86.268 GHz with 2 GHz of bandwidth." (Table 2)
- arrays: 37 12m antennas (ALMA Phasing System)  
  > "The observations were carried out on April 3, using 37 12m antennas in Band 3 configuration centred at 86 GHz (cite: Liu_2021)." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesised beam ~ 5.7"  
  > "This is because the source is located within the same synthesised beam of Sgr A$^{*}$ ($\theta \approx$ 5.7”), due to its 0.07-2 pc projected distance (cite: reapsr)." (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 2.5 hr total on-source (~2 hr used, excluding 30 minutes of unusable data; 5.2 hr total dataset)  
  > "The dataset covered a total of 5.2 hr, with on-source time of 2.5 hr. We used a total of $\sim$2 hr observing time, excluding 30 minutes of unusable data (see Table 2)." (Observations)
- observing dates: 2017-04-03  
  > "The observations were carried out on April 3, using 37 12m antennas in Band 3 configuration centred at 86 GHz (cite: Liu_2021)." (Observations); "No0133 | 2017-04-03 07:46:05 | 2017-04-03 07:53:05" (Table 2)
- pi or archival as stated: Archival, PI: M. Johnson  
  > "We used observations of Sgr A* from the 2017 GMVA campaign at 3.5 mm (Project Code: 2017.1.00795.V, PI: M. Johnson)." (Observations)
- External data: Dispersion measure DM = 1770 pc cm^-3, system temperature T_sys = 51 K, and system gain G = 1.15 K/Jy  
  > "Therefore, DM trials were unnecessary, and we adopted the reported value of the source, 1770 $\rm{pc \hspace{0.1cm}cm^{-3}}$ (cite: Liu_2021)." (Methods and data processing); "where $\rm{k_b}$ is the Boltzmann constant, $\rm{T_{sys}}$ is the system temperature, G is the system gain of phased ALMA (51 K and 1.15 K/Jy respectively on (cite: Liu_2021)), and $\rm{A_{eff}}$ is the effective area." (Pulse characterisation) [from (cite: Liu_2021)]
- External data: ATNF Pulsar Catalogue ephemeris, DM uncertainty, and known pulsars with flux densities at 1.4 GHz or 2 GHz  
  > "This step was necessary as the ephemeris listed in the ATNF catalogue (cite: catalogue) was not sufficient to fully recover the signal of the magnetar." (Results); "Table notes: The DM uncertainty was taken from the ATNF catalogue (cite: catalogue)." (Table 3); "To this end, we selected all the known pulsars from the ATNF catalogue (cite: catalogue) having flux density reported at 1.4 GHz or 2 GHz." (Pulsars) [from (cite: catalogue)]
- External data: Source luminosity distance D = 8.3 kpc  
  > "where D corresponds to the source luminosity distance, equal to 8.3 kpc (cite: yim)." (Pulse characterisation) [from (cite: yim)]
- External data: ALMA system parameters (T_sys = 74 K, G = 1.08 K/Jy for Band 3; T_sys = 45 K, G = 1.12 K/Jy for Band 1; declination limit < 47 deg)  
  > "We derived the minimum sensitivity for Band 3 using the radiometer equation for pulsars and considering telescope parameters such as $T_{sys}$ = 74 K, $G$ = 1.08 K/Jy (cite: almahand) for Band 3" (Pulsars); "Assuming that the Band 1 system behaves similarly ($T_{sys}$ = 45 K, $G$ = 1.12 K/Jy in (cite: almahand)), then we expect a minimum detectable flux of 0.035 mJy, using the same 37-antenna set-up." (Pulsars) [from (cite: almahand)]
- External data: Phasing efficiency eta_p ~ 0.6  
  > "a phasing efficiency of $\eta_{p} \sim 0.6$ (cite: matthews2017), a minimum detected S/N of 6 and 1 hour of on-source integration time." (Pulsars) [from (cite: matthews2017)]
- External data: Pulsar spectral index normal distribution (mean = -1.6, standard deviation = 0.54)  
  > "For the sources that do not have a reported spectral index, we draw a spectral index from a normal distribution, considering a mean of -1.6 and standard deviation equal to 0.54 (cite: index)." (Pulsars) [from (cite: index)]
- External data: FRB 20121102A L-band burst rates (122 events/hr and 218 +/- 16 events/hr) and power-law index (gamma = -1.1)  
  > "We take FRB 20121102A, whose reported rates at L-band are 122 events/hr (cite: li2; li) and 218$\pm$16 events/hr (cite: NovRain)." (FRBs); "If on the contrary, we take the flatter value of $\gamma=-1.1$ reported for FRB 20121102A at L-band in (cite: papermary), we estimate instead between 10 $\pm$ 3 and 32 $\pm$ 6 events/hr." (FRBs) [from (cite: li2; li), (cite: NovRain), (cite: papermary)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
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

- Conversion of phased ALMA data to PSRFITS format with full Stokes information (I,Q,U,V) and 32 frequency channels of 62.5 MHz width  
  > "As discussed in (cite: Liu_2021), the data was converted to PSRFITS format (cite: psrfits) with full Stokes information (I,Q,U,V) and 32 frequency channels, each with a 62.5 MHz channel width." (Observations) [from (cite: Liu_2021)]
- PRESTO-based single pulse search pipeline, modified to account for PSRFITS containing Stokes  
  > "We searched for single pulses using a PRESTO-based pipeline (cite: presto), detailed in (cite: Braga2024) with some modifications to account for PSRFITS containing Stokes." (Methods and data processing) [from (cite: Braga2024)]
- Multi-Gaussian fitting routine for single pulse width analysis  
  > "To estimate the pulse width, we used a multi-Gaussian fitting routine developed for single pulse analysis (Limaye et al. in prep.)." (Pulse characterisation) [from Limaye et al. in prep.]

### Not stated but needed to reproduce (our reading)

- How the 18.192 s periodic drop-off artefact from the ALMA phasing cycle was masked, excised, or mitigated during the single-pulse search
- Quantitative thresholds for linear and circular polarisation fractions used to accept or reject single-pulse candidates during visual inspection
- Exact boxcar widths or matched-filtering parameters used in the PRESTO single-pulse search
- Specific details of the multi-Gaussian fitting routine from the unpublished work (Limaye et al. in prep.)

## Analysis recipe

1. **Update magnetar timing ephemeris**: Created integrated pulse profiles per scan, extracted TOAs from scans with highest S/N, and performed timing residual minimisation in TEMPO with spin period as the only free parameter  
  > "we created integrated pulse profiles per scan. From those with the highest S/N, we obtained TOAs that we input to TEMPO" (Results); "Through residual minimisation, with the spin period as the only free parameter, we generated a new ephemeris file shown in Table 3." (Results)
   - software: TEMPO
   - parameter: PEPOCH = 57846.349663  
  > "Reference Epoch, PEPOCH | 57846.349663" (Table 3)
   - assumption: DM = 1770(3) cm^-3 pc, RA = 17:45:40.1662(8), Dec = -29:00:29.89(1) fixed  
  > "Right ascension, $\alpha$ (J2000) | 17:45:40.1662(8)" (Table 3); "Declination, $\delta$ (J2000) | $-$29:00:29.89(1)" (Table 3); "Dispersion measure, DM ($\text{cm}^{-3}\,\text{pc}$) | 1770(3)" (Table 3)
   - fitting: Residual minimisation with spin period as the only free parameter  
  > "Through residual minimisation, with the spin period as the only free parameter, we generated a new ephemeris file shown in Table 3." (Results)
   - validation: _not stated_
2. **Search for and validate single pulses**: Summed all 32 frequency channels of PSRFITS files in Stokes I at fixed DM = 1770 pc cm^-3 using a PRESTO-based pipeline, applied S/N threshold of 6, and visually inspected candidates in intensity, linear and circular polarisation, and arrival spin phase  
  > "We searched for single pulses using a PRESTO-based pipeline (cite: presto), detailed in (cite: Braga2024) with some modifications to account for PSRFITS containing Stokes." (Methods and data processing); "We used a signal-to-noise ratio (S/N) threshold of 6, determined through analysis of the noise floor of the time series on pulse-free regions." (Methods and data processing); "According to our criteria, if a pulse candidate has significant linear and circularly polarised flux and it arrives in phase with the integrated pulse profile of PSR J1745$-$2900, then it is considered a real pulse." (Methods and data processing)
   - software: PRESTO
   - parameter: S/N threshold = 6  
  > "We used a signal-to-noise ratio (S/N) threshold of 6, determined through analysis of the noise floor of the time series on pulse-free regions." (Methods and data processing)
   - parameter: Fixed DM = 1770 pc cm^-3 (no DM trials)  
  > "Therefore, DM trials were unnecessary, and we adopted the reported value of the source, 1770 $\rm{pc \hspace{0.1cm}cm^{-3}}$ (cite: Liu_2021)." (Methods and data processing)
   - assumption: Dispersion delay across the 2 GHz band at 86 GHz is negligible (46 microseconds, 1 sample)  
  > "Given the high DM of the source and the high observing frequency at Band 3, the dispersion delay between the highest and the lowest frequency channel is 46" (Methods and data processing)
   - fitting: _not stated_
   - validation: Visual inspection of linear and circular polarisation and arrival phase alignment with the integrated pulse profile; recovered all 3 pulses previously reported by Liu et al. (2021)  
  > "According to our criteria, if a pulse candidate has significant linear and circularly polarised flux and it arrives in phase with the integrated pulse profile of PSR J1745$-$2900, then it is considered a real pulse." (Methods and data processing); "In our search we found the three pulses reported by (cite: Liu_2021) plus five new pulses." (Results)
3. **Characterize pulse widths, flux densities, fluences, and isotropic energies**: Normalised time series using pulse-free regions (downsampled by 128) to get peak S/N, fitted multi-Gaussian models to measure FWHM, and computed flux density, fluence, and isotropic energy via radiometer equation  
  > "We computed the S/N by normalising the time series using a pulse-free region and taking the pulse peak. To estimate the pulse width, we used a multi-Gaussian fitting routine developed for single pulse analysis (Limaye et al. in prep.)." (Pulse characterisation); "Table notes: The S/N was obtained from the pulse profile using a downsampling factor of 128." (Table 4)
   - parameter: Downsampling factor = 128  
  > "Table notes: The S/N was obtained from the pulse profile using a downsampling factor of 128." (Table 4)
   - parameter: Bandwidth = 2 GHz  
  > "The flux density and fluence were obtained considering all the 2 GHz bandwidth of the observation." (Table 4)
   - assumption: T_sys = 51 K and G = 1.15 K/Jy  
  > "where $\rm{k_b}$ is the Boltzmann constant, $\rm{T_{sys}}$ is the system temperature, G is the system gain of phased ALMA (51 K and 1.15 K/Jy respectively on (cite: Liu_2021)), and $\rm{A_{eff}}$ is the effective area." (Pulse characterisation)
   - assumption: Luminosity distance D = 8.3 kpc  
  > "where D corresponds to the source luminosity distance, equal to 8.3 kpc (cite: yim)." (Pulse characterisation)
   - fitting: Multi-Gaussian fitting routine (FWHM defined from S/N peak to 50% drop on outermost components)  
  > "The FWHM was obtained from a multi-Gaussian fitting, where the width is defined from the S/N peak to the point where the value drops to 50$\%$. Whenever the pulse was fitted with multiple Gaussians, the outermost components were considered for the S/N drop." (Table 4)
   - validation: _not stated_
4. **Fit cumulative energy distribution of the magnetar pulses**: Sorted events above the completeness limit, counted events above energy thresholds, and fit a power law R proportional to E^gamma  
  > "We constructed the cumulative energy distribution by sorting the events and then counting the number above an energy threshold, until all the pulses were contained." (Energy distribution); "We fit a power law to the cumulative energy distribution using a least-squares minimisation considering that the event rate scales with the energy as $R \propto E^{\gamma}$." (Energy distribution)
   - parameter: Completeness limit = 1120 mJy ms (using mean FWHM ~ 0.07 s, T_sys = 51 K, G = 1.15 K Jy^-1)  
  > "We included only events above the completeness limit, which is $\sim$1120 mJy ms using a $T_{sys} =$ 51 K and $G$ = 1.15 K Jy$^{-1}$ (cite: Liu_2021) and considering the pulse width as the mean FWHM of our pulses, $\approx$ 0.07 s." (Energy distribution)
   - assumption: Event rate scales with energy as a power law R proportional to E^gamma  
  > "We fit a power law to the cumulative energy distribution using a least-squares minimisation considering that the event rate scales with the energy as $R \propto E^{\gamma}$." (Energy distribution)
   - fitting: Least-squares minimisation of power law  
  > "We fit a power law to the cumulative energy distribution using a least-squares minimisation considering that the event rate scales with the energy as $R \propto E^{\gamma}$." (Energy distribution)
   - validation: _not stated_
5. **Predict event rates and detectability for PSR J1745-2900, FRBs, and ATNF pulsars at Phased ALMA Band 1 and Band 3**: Scaled observed Band 3 event rate and L-band FRB rates to Band 1 using fluence completeness thresholds and power-law index gamma; extrapolated 2301 ATNF pulsar fluxes (Dec < 47 deg) to 42 GHz using spectral indices and compared against radiometer sensitivity  
  > "Based on our detections, we report a Poissonian rate of $\rm{R_{Band\hspace{1mm}3}}$ = 4 per hour (events/hr) for PSR J1745-2900 at ALMA Band 3." (PAM Band 1 predictions); "To this end, we selected all the known pulsars from the ATNF catalogue (cite: catalogue) having flux density reported at 1.4 GHz or 2 GHz. We limited the sources detectable by ALMA based on a declination below 47° (cite: almahand)." (Pulsars); "We used the spectral index to estimate the flux of each source at 42 GHz (Band 1). To extrapolate we used a simple power-law:" (Pulsars)
   - parameter: Fluence limits: F_Band3 = 1330 mJy ms (37 antennas, 0.1 s width), F_Band1 = 1200 mJy ms (37 antennas, 0.1 s width), F_Band1 = 900 mJy ms (49 antennas, 0.1 s width), F_Band1 = 90 mJy ms (49 antennas, 1 ms FRB width)  
  > "The fluence completeness limit using 37 antennas of 12m at Band 3 is $\rm{F_{Band\hspace{1mm}3}}$ = 1330 mJy ms and at Band 1 $\rm{F_{Band\hspace{1mm}1}}$ = 1200 mJy ms, considering a pulse width of 0.1 s." (PAM Band 1 predictions); "However, if we instead consider a total of 49 antennas for the phasing, then the expected rate rises to $\rm{R_{Band\hspace{1mm}1}} = 10 \pm 3$ events/hr, as the fluence threshold drops to $\rm{F_{Band\hspace{1mm}1}}$ = 900 mJy ms." (PAM Band 1 predictions); "In this case, we re-calculated the fluence threshold for ALMA assuming bursts of 1 ms duration (typical for FRBs), and obtain $\rm{F_{Band-1}}$ = 90 mJy ms." (FRBs)
   - parameter: Integration times = 1, 1.5, and 2.5 hours; S/N = 6; pulsar period = 1 s; duty cycle = 10%  
  > "We assumed a pulse width equal to 10$\%$ of the period and considered on-source integration times of 1, 1.5, and 2.5 hours." (Pulsars); "For a pulsar spin period of 1 s with a duty cycle of 10%, we estimate that the Band 3 system is sensitive to 0.060 mJy." (Pulsars)
   - assumption: Phasing efficiency eta_p ~ 0.6; Band 3 T_sys = 74 K, G = 1.08 K/Jy; Band 1 T_sys = 45 K, G = 1.12 K/Jy  
  > "We derived the minimum sensitivity for Band 3 using the radiometer equation for pulsars and considering telescope parameters such as $T_{sys}$ = 74 K, $G$ = 1.08 K/Jy (cite: almahand) for Band 3, a phasing efficiency of $\eta_{p} \sim 0.6$ (cite: matthews2017), a minimum detected S/N of 6 and 1 hour of on-source integration time." (Pulsars); "Assuming that the Band 1 system behaves similarly ($T_{sys}$ = 45 K, $G$ = 1.12 K/Jy in (cite: almahand)), then we expect a minimum detectable flux of 0.035 mJy, using the same 37-antenna set-up." (Pulsars)
   - assumption: Missing pulsar spectral indices drawn from normal distribution with mean = -1.6 and std = 0.54  
  > "For the sources that do not have a reported spectral index, we draw a spectral index from a normal distribution, considering a mean of -1.6 and standard deviation equal to 0.54 (cite: index)." (Pulsars)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PRESTO** : Single pulse search pipeline  
  > "We searched for single pulses using a PRESTO-based pipeline (cite: presto), detailed in (cite: Braga2024) with some modifications to account for PSRFITS containing Stokes." (Methods and data processing)
- **TEMPO** : Pulsar timing analysis and generating a new ephemeris via residual minimisation  
  > "From those with the highest S/N, we obtained TOAs that we input to TEMPO (cite: tempo), following standard timing procedures." (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of detected single pulses from PSR J1745-2900 | 8 | not stated | dimensionless | 2 | We detected eight highly polarised pulses from the GC magnetar with energies in the range of $10^{29}$ erg.; We report eight single pulses from the GC magnetar, PSR J1745-2900, which are shown in Fig. 1. |
| Spin frequency (F) of PSR J1745-2900 at MJD 57846.349663 | 0.26762 | 0.00008 | s^-1 | 1 | Spin frequency, $F$ ($\text{s}^{-1}$) / 0.26762(8); Reference Epoch, PEPOCH / 57846.349663 |
| Cumulative energy distribution power-law exponent (gamma) | -2.4 | 0.1 | dimensionless | 4 | The result is an exponent of $\gamma = -2.4 \pm 0.1$, which is consistent with values reported for magnetars at cm-waves and repeating FRBs.; The result is a power-law exponent of $\gamma = -2.4 \pm  0.1$. |
| Candidate 1 S/N | 11.0 | not stated | dimensionless | 3 | 1 / 11.0 / 57846.3495 / 0.11 / 0.023 / 2.589 / 4.27 |
| Candidate 1 FWHM | 0.11 | not stated | s | 3 | 1 / 11.0 / 57846.3495 / 0.11 / 0.023 / 2.589 / 4.27 |
| Candidate 1 Flux density | 0.023 | not stated | Jy | 3 | 1 / 11.0 / 57846.3495 / 0.11 / 0.023 / 2.589 / 4.27 |
| Candidate 1 Fluence | 2.589 | not stated | Jy ms | 3 | 1 / 11.0 / 57846.3495 / 0.11 / 0.023 / 2.589 / 4.27 |
| Candidate 1 Isotropic Energy | 4.27 | not stated | 10^29 erg | 3 | 1 / 11.0 / 57846.3495 / 0.11 / 0.023 / 2.589 / 4.27 |
| Candidate 2 S/N | 6.6 | not stated | dimensionless | 3 | 2 / 6.6 / 57846.5413 / 0.13 / 0.013 / 1.660 / 2.74 |
| Candidate 2 FWHM | 0.13 | not stated | s | 3 | 2 / 6.6 / 57846.5413 / 0.13 / 0.013 / 1.660 / 2.74 |
| Candidate 2 Flux density | 0.013 | not stated | Jy | 3 | 2 / 6.6 / 57846.5413 / 0.13 / 0.013 / 1.660 / 2.74 |
| Candidate 2 Fluence | 1.660 | not stated | Jy ms | 3 | 2 / 6.6 / 57846.5413 / 0.13 / 0.013 / 1.660 / 2.74 |
| Candidate 2 Isotropic Energy | 2.74 | not stated | 10^29 erg | 3 | 2 / 6.6 / 57846.5413 / 0.13 / 0.013 / 1.660 / 2.74 |
| Candidate 3 S/N | 15.6 | not stated | dimensionless | 3 | 3 / 15.6 / 57846.5730 / 0.04 / 0.058 / 2.068 / 3.41 |
| Candidate 3 FWHM | 0.04 | not stated | s | 3 | 3 / 15.6 / 57846.5730 / 0.04 / 0.058 / 2.068 / 3.41 |
| Candidate 3 Flux density | 0.058 | not stated | Jy | 3 | 3 / 15.6 / 57846.5730 / 0.04 / 0.058 / 2.068 / 3.41 |
| Candidate 3 Fluence | 2.068 | not stated | Jy ms | 3 | 3 / 15.6 / 57846.5730 / 0.04 / 0.058 / 2.068 / 3.41 |
| Candidate 3 Isotropic Energy | 3.41 | not stated | 10^29 erg | 3 | 3 / 15.6 / 57846.5730 / 0.04 / 0.058 / 2.068 / 3.41 |
| Candidate 4 S/N | 22.2 | not stated | dimensionless | 3 | 4 / 22.2 / 57846.5422 / 0.04 / 0.074 / 3.284 / 5.41 |
| Candidate 4 FWHM | 0.04 | not stated | s | 3 | 4 / 22.2 / 57846.5422 / 0.04 / 0.074 / 3.284 / 5.41 |
| Candidate 4 Flux density | 0.074 | not stated | Jy | 3 | 4 / 22.2 / 57846.5422 / 0.04 / 0.074 / 3.284 / 5.41 |
| Candidate 4 Fluence | 3.284 | not stated | Jy ms | 3 | 4 / 22.2 / 57846.5422 / 0.04 / 0.074 / 3.284 / 5.41 |
| Candidate 4 Isotropic Energy | 5.41 | not stated | 10^29 erg | 3 | 4 / 22.2 / 57846.5422 / 0.04 / 0.074 / 3.284 / 5.41 |
| Candidate 5 S/N | 7.5 | not stated | dimensionless | 3 | 5 / 7.5 / 57846.3478 / 0.08 / 0.018 / 1.499 / 2.47 |
| Candidate 5 FWHM | 0.08 | not stated | s | 3 | 5 / 7.5 / 57846.3478 / 0.08 / 0.018 / 1.499 / 2.47 |
| Candidate 5 Flux density | 0.018 | not stated | Jy | 3 | 5 / 7.5 / 57846.3478 / 0.08 / 0.018 / 1.499 / 2.47 |
| Candidate 5 Fluence | 1.499 | not stated | Jy ms | 3 | 5 / 7.5 / 57846.3478 / 0.08 / 0.018 / 1.499 / 2.47 |
| Candidate 5 Isotropic Energy | 2.47 | not stated | 10^29 erg | 3 | 5 / 7.5 / 57846.3478 / 0.08 / 0.018 / 1.499 / 2.47 |
| Candidate 6 S/N | 10.7 | not stated | dimensionless | 3 | 6 / 10.7 / 57846.3493 / 0.04 / 0.036 / 1.556 / 2.57 |
| Candidate 6 FWHM | 0.04 | not stated | s | 3 | 6 / 10.7 / 57846.3493 / 0.04 / 0.036 / 1.556 / 2.57 |
| Candidate 6 Flux density | 0.036 | not stated | Jy | 3 | 6 / 10.7 / 57846.3493 / 0.04 / 0.036 / 1.556 / 2.57 |
| Candidate 6 Fluence | 1.556 | not stated | Jy ms | 3 | 6 / 10.7 / 57846.3493 / 0.04 / 0.036 / 1.556 / 2.57 |
| Candidate 6 Isotropic Energy | 2.57 | not stated | 10^29 erg | 3 | 6 / 10.7 / 57846.3493 / 0.04 / 0.036 / 1.556 / 2.57 |
| Candidate 7 S/N | 8.9 | not stated | dimensionless | 3 | 7 / 8.9 / 57846.5412 / 0.10 / 0.020 / 1.956 / 3.23 |
| Candidate 7 FWHM | 0.10 | not stated | s | 3 | 7 / 8.9 / 57846.5412 / 0.10 / 0.020 / 1.956 / 3.23 |
| Candidate 7 Flux density | 0.020 | not stated | Jy | 3 | 7 / 8.9 / 57846.5412 / 0.10 / 0.020 / 1.956 / 3.23 |
| Candidate 7 Fluence | 1.956 | not stated | Jy ms | 3 | 7 / 8.9 / 57846.5412 / 0.10 / 0.020 / 1.956 / 3.23 |
| Candidate 7 Isotropic Energy | 3.23 | not stated | 10^29 erg | 3 | 7 / 8.9 / 57846.5412 / 0.10 / 0.020 / 1.956 / 3.23 |
| Candidate 8 S/N | 14.7 | not stated | dimensionless | 3 | 8 / 14.7 / 57846.3767 / 0.01 / 0.127 / 0.837 / 1.38 |
| Candidate 8 FWHM | 0.01 | not stated | s | 3 | 8 / 14.7 / 57846.3767 / 0.01 / 0.127 / 0.837 / 1.38 |
| Candidate 8 Flux density | 0.127 | not stated | Jy | 3 | 8 / 14.7 / 57846.3767 / 0.01 / 0.127 / 0.837 / 1.38 |
| Candidate 8 Fluence | 0.837 | not stated | Jy ms | 3 | 8 / 14.7 / 57846.3767 / 0.01 / 0.127 / 0.837 / 1.38 |
| Candidate 8 Isotropic Energy | 1.38 | not stated | 10^29 erg | 3 | 8 / 14.7 / 57846.3767 / 0.01 / 0.127 / 0.837 / 1.38 |
| Mean FWHM of detected pulses | 0.07 | not stated | s | 4 | We included only events above the completeness limit, which is $\sim$1120 mJy ms using a $T_{sys} =$ 51 K and $G$ = 1.15 K Jy$^{-1}$ (cite: Liu_2021) and considering the pulse width as the mean FWHM of our pulses, $\approx$ 0.07 s. |
| Observed Band 3 Poissonian event rate for PSR J1745-2900 | 4 | not stated | events/hr | 5 | Based on our detections, we report a Poissonian rate of $\rm{R_{Band\hspace{1mm}3}}$ = 4 per hour (events/hr) for PSR J1745-2900 at ALMA Band 3. |
| Predicted Band 1 event rate for PSR J1745-2900 (37 12m antennas) | 5 | 2 | events/hr | 5 | We obtain a rate of $\rm{R_{Band\hspace{1mm}1}} = 5 \pm 2$ events/hr. |
| Predicted Band 1 event rate for PSR J1745-2900 (49 12m antennas) | 10 | 3 | events/hr | 5 | However, if we instead consider a total of 49 antennas for the phasing, then the expected rate rises to $\rm{R_{Band\hspace{1mm}1}} = 10 \pm 3$ events/hr, as the fluence threshold drops to $\rm{F_{Band\hspace{1mm}1}}$ = 900 mJy ms. |
| Predicted Band 1 event rate for FRB 20121102A at peak activity (49 12m antennas) | 1 to 32 | not stated | events/hr | 5 | For the periodic FRB 20121102A, at peak activity, we obtained a rate between 1 and 32 events/hr with PAM Band 1 using 49 12m antennas. |
| Number of known pulsars detectable with PAM Band 1 in 1 hr integration | 166 | not stated | dimensionless | 5 | This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively. |
| Number of known pulsars detectable with PAM Band 1 in 1.5 hr integration | 188 | not stated | dimensionless | 5 | This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively. |
| Number of known pulsars detectable with PAM Band 1 in 2.5 hr integration | 209 | not stated | dimensionless | 5 | This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively. |
| Number of repeating FRBs currently visible to ALMA | 19 | not stated | dimensionless | 5 | As shown in Fig. 4, currently ALMA could potentially detect 19 repeating FRBs.; Currently, there are 19 repeating FRBs that are visible to ALMA. |

## Qualitative findings

- Five of the eight detected pulses exhibit nearly 100% linear polarisation, the remaining three have ~50% linear polarisation, and the majority have ~30% circular polarisation.  
  > "Among the pulses, five of them (P1, P2, P3, P5, and P8) exhibit nearly 100$\%$ of the linearly polarised flux, while the remaining three (P4, P6, and P7) have values close to 50$\%$. In addition, for the majority of them there is a degree of circular polarisation of approximately 30$\%$." (Discussion)
- Most of the detected pulses from PSR J1745-2900 have at least two components and show broadband emission across the entire 2 GHz bandwidth at Band 3.  
  > "most of the pulses have at least two components, which vary in relative intensity. All pulses show emission across the entire 2 GHz bandwidth." (Discussion)
- Coherent magnetar radio emission persists into the millimetre band (86 GHz).  
  > "Magnetar radio emission–known to be coherent at cm-wavelengths–persists into the mm-band, as demonstrated by our work, by (cite: Liu_2021), and by (cite: torne2016)." (Discussion)

## Claim tuples

- H: Single pulses from the Galactic Centre magnetar PSR J1745-2900 can be detected at 86 GHz (ALMA Band 3) using polarisation properties and arrival spin phase when dispersion delay is negligible. | E: Searched ~2 hr of archival Phased ALMA Band 3 PSRFITS data of Sgr A* using a PRESTO-based pipeline with S/N >= 6, verifying candidates via linear and circular polarisation and arrival phase alignment. | R: Detected eight highly polarised single pulses with isotropic energies of 1.38 to 5.41 x 10^29 erg (recovering three previously reported by Liu et al. 2021 plus five new pulses). | F: Phased ALMA at Band 3 successfully detects highly polarised single pulses from the GC magnetar, confirming coherent radio emission persists at 86 GHz. | **supported**
- H: The cumulative energy distribution of single pulses from the GC magnetar at 86 GHz follows a power law consistent with magnetars at cm-wavelengths and repeating FRBs. | E: Constructed the cumulative energy distribution of detected pulses above the completeness limit (~1120 mJy ms) and fit a power law R proportional to E^gamma via least-squares minimisation. | R: Obtained a power-law exponent of gamma = -2.4 +/- 0.1. | F: The cumulative energy distribution exponent at 86 GHz is consistent with values reported for magnetar giant pulses at cm-wavelengths and repeating FRBs, though a gap of at least seven orders of magnitude in isotropic energy remains. | **supported**
- H: Phased ALMA Mode (PAM), particularly at Band 1, is sensitive enough to detect a large population of known radio pulsars and bursts from repeating FRBs during peak activity. | E: Extrapolated event rates for PSR J1745-2900 and FRB 20121102A to Band 1 using fluence thresholds and power-law exponents, and extrapolated fluxes of 2301 ATNF pulsars (Dec < 47 deg) to 42 GHz to compare with radiometer sensitivity. | R: Predicted 5 +/- 2 to 10 +/- 3 events/hr for PSR J1745-2900, 1 to 32 events/hr for FRB 20121102A at peak activity, and 166 to 209 detectable pulsars in 1 to 2.5 hr integrations at Band 1. | F: Phased ALMA Band 1 can serve as a pioneer for millimetre-wave searches and studies of pulsars and repeating FRBs in complex environments. | **supported**

## Reasoning

- Why this data: High-frequency (86 GHz) phased ALMA observations overcome severe low-frequency propagation effects (scattering and dispersion) in the dense Galactic Centre while providing high sensitivity (~84 m equivalent dish) and including PSR J1745-2900 within the Sgr A* synthesised beam (~5.7").  
  > "One way to overcome these two propagation effects and reach the densest regions is to observe at higher frequencies. To compensate for the lower flux densities, the largest possible radio telescopes are required." (Introduction); "For this work we studied the GC magnetar, PSR J1745-2900, using ALMA archival data of Sgr A$^{*}$. This is because the source is located within the same synthesised beam of Sgr A$^{*}$ ($\theta \approx$ 5.7”), due to its 0.07-2 pc projected distance (cite: reapsr)." (Introduction)
- Why this method: Because the dispersion delay across the 2 GHz Band 3 bandwidth is negligible (46 microseconds, 1 sample), DM trials cannot distinguish real astrophysical pulses from noise; therefore, polarisation properties and spin-phase alignment were used to confirm candidates, and a cumulative energy distribution was fit due to the small sample size.  
  > "Importantly, due to the negligible dispersion delay, we relied primarily on polarisation to confirm the pulse candidates. We complemented these data with a second test –in which we used the spin period of the magnetar to assign a phase to the arrival time of each pulse." (Methods and data processing); "This definition corresponds to the cumulative energy distribution, which is broadly used in cases where the number of pulses is limited, such as the case of FRBs." (Discussion)
- Alternative: Performing dispersion measure (DM) trials was rejected as unnecessary because the dispersion delay across the band at 86 GHz is only 46 microseconds (1 sample).  
  > "Therefore, DM trials were unnecessary, and we adopted the reported value of the source" (Methods and data processing)
- Alternative: Using the ATNF catalogue ephemeris directly was insufficient to recover the magnetar signal, requiring generation of a new ephemeris via TEMPO.  
  > "This step was necessary as the ephemeris listed in the ATNF catalogue (cite: catalogue) was not sufficient to fully recover the signal of the magnetar." (Results)
- Alternative: Fitting the differential energy distribution or a log-normal distribution was not used due to the small sample size of eight pulses.  
  > "It is important to note that in our work we reported a limited sample of eight pulses. With a larger sample size (hundreds of pulses) the differential energy distribution could also be fit." (Comparison with FRBs)
- How they decided it was enough: Used all available usable archival data from the 2017 GMVA campaign (~2 hr after excluding 30 minutes of unusable data) and set the S/N threshold to 6 based on noise floor analysis of pulse-free regions.  
  > "We used a total of $\sim$2 hr observing time, excluding 30 minutes of unusable data (see Table 2)." (Observations); "We used a signal-to-noise ratio (S/N) threshold of 6, determined through analysis of the noise floor of the time series on pulse-free regions." (Methods and data processing)
- Limitation (authors): Every 18.192 s there is a drop-off in the time series caused by the phasing cycle of the array, and 30 minutes of data were unusable.  
  > "We used a total of $\sim$2 hr observing time, excluding 30 minutes of unusable data (see Table 2)." (Observations); "Every 18.192 s there was a drop-off on the time series caused by the phasing cycle of the array." (Observations)
- Limitation (authors): Pulses with small polarisation fractions or arriving outside the main integrated pulse profile phase window would not be detected by the selection criteria.  
  > "It is worth noting that pulses with small polarisation fractions would have not been detected by our pipelines." (Methods and data processing); "Nevertheless, in some cases magnetars also show single pulses outside the main profile (cite: camiloxte)." (Methods and data processing)
- Limitation (authors): The sample size is limited to eight pulses over a limited energy range.  
  > "Alternatively, a power-law relation for the cumulative energy distribution would be the result of the limited energy range of our pulses." (Discussion); "It is important to note that in our work we reported a limited sample of eight pulses." (Comparison with FRBs)
- Limitation (authors): Phased ALMA surveys are unlikely to be sensitive to millisecond pulsars (MSPs).  
  > "It is important to mention that these surveys are unlikely to be sensitive to millisecond pulsars (MSPs, (cite: Liu_2021))." (Pulsars)
- Caveat (inferred, ours): Fitting a power law to a cumulative energy distribution of only 7 pulses above the completeness limit has strong bin-to-bin correlations; ordinary least-squares minimisation underestimates the uncertainty on the slope (+/- 0.1) compared to maximum-likelihood methods.
- Caveat (inferred, ours): Requiring significant linear and circular polarisation and visual inspection introduces unquantified selection biases into the completeness limit and cumulative energy distribution.
- Caveat (inferred, ours): Extrapolating pulsar flux densities from 1.4-2 GHz to 42 GHz with a single power-law spectral index ignores spectral breaks, turnovers, or high-frequency flattening.

## Reproducibility

- Data public (paper): Archival ALMA data from the 2017 GMVA campaign (Project Code: 2017.1.00795.V)  
  > "We used observations of Sgr A* from the 2017 GMVA campaign at 3.5 mm (Project Code: 2017.1.00795.V, PI: M. Johnson)." (Observations)
- Products in archive: _not stated_
- Missing: Availability or conversion scripts to produce the channelised full-Stokes PSRFITS files from raw VLBI Mark 6 voltage recordings (originally processed in Liu et al. 2021)
- Missing: Modified PRESTO single-pulse search scripts supporting Stokes PSRFITS and masking of the 18.192 s phasing cycle drop-offs
- Missing: Quantitative polarisation thresholds used during visual candidate selection
- Missing: The unpublished multi-Gaussian fitting code (Limaye et al. in prep.)
- Data volume (inferred): ~10-50 GB for the converted 32-channel, 32-microsecond PSRFITS files covering ~2.5 hr (several TB if starting from raw Mark 6 VLBI voltage recordings)
- Score (inferred): 45/5, Although the ALMA project code, scan list, updated ephemeris, and equations are clearly provided, reproduction from the ALMA archive requires specialised VLBI baseband-to-PSRFITS conversion (from Liu et al. 2021), custom unpublished code for multi-Gaussian width fitting (Limaye et al. in prep.), and subjective visual inspection of polarisation time series.
- Rediscovery candidate: no, Requires specialised VLBI phased-array PSRFITS data products not standardly served as ready-to-use files in the ALMA archive, plus subjective visual inspection of polarisation candidates and an unpublished fitting script.

## Links

- Method: (cite: Liu_2021) (Previous analysis of the same 2017 GMVA Phased ALMA dataset, describing the PSRFITS conversion, system parameters (T_sys, G), DM, and three of the pulses)
- Method: (cite: Braga2024) (Describes the PRESTO-based single pulse search pipeline adapted in this work)
- Method: (cite: matthews2017) (Describes the ALMA Phasing System (APS) and phasing efficiency)
- Method: (cite: goddialmadata) (Describes the phasing of ALMA antennas and VLBI/time-domain data processing)
- Companion: (cite: Liu_2021) (Analyzed the exact same 2017 GMVA ALMA Band 3 dataset of PSR J1745-2900 and reported the first three single pulses)
- Related: Global Millimetre VLBI Array (GMVA)
- Related: ATNF Pulsar Catalogue

## Checks

```json
{
 "quotes": 163,
 "quotes_ok": 163,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 9,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 52,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 62,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
