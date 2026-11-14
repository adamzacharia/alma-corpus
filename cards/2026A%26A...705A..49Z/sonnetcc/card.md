# The <SUP>12</SUP>CO gas structures of protoplanetary disks in the Upper Scorpius region

`2026A&A...705A..49Z` | Astronomy and Astrophysics 2026 | first author: Zallio, Luigi | arXiv: 2511.16734 | DOI: 10.1051/0004-6361/202557366

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Infer bulk gas-disk properties (radius, 12CO emission-layer height, brightness temperature, integrated flux) for the Upper Scorpius disks by fitting 12CO J=3-2 visibilities with parametric models  
  > "to infer important quantities of protoplanetary disks, such as radius, line-emission layer, and integrated flux." (1 Introduction); "but it has never been applied on a large survey: in this work, we filled this gap." (1 Introduction)
- Target **Upper Scorpius 12CO J=3-2 detections (83 detections, 37 fitted)**: coordinates _not stated_; z/distance per-source distances listed in Tables 4 and 5 (about 126-166 pc)  
  > "We were able to fit 37 sources out of a sample of 83, 33 with prescription A and four with prescription B." (4 Results); "The distances were taken from the Gaia DR3 collaboration" (Table 4 notes); distance from Gaia DR3  
  > "We were able to fit 37 sources out of a sample of 83, 33 with prescription A and four with prescription B." (4 Results); "The distances were taken from the Gaia DR3 collaboration" (Table 4 notes)

## Data provenance

- ALMA projects: 2011.0.00526.S, 2012.1.00688.S, 2013.1.00395.S, 2018.1.00564.S
- bands: Band 7  
  > "The observations were obtained in Band 7, with spectral windows centered at 334.2, 336.1, 346.2, and 348.1 GHz." (2 Sample selection)
- frequencies and spectral setup: spws centered at 334.2, 336.1, 346.2, 348.1 GHz; 346.2 GHz window includes 12CO J=3-2; channel width 0.488 MHz (0.429 km/s)  
  > "The observations were obtained in Band 7, with spectral windows centered at 334.2, 336.1, 346.2, and 348.1 GHz." (2 Sample selection); "with a channel width of 0.488 MHz (0.429 kms$^{-1}$ for $^{12}$CO $J=3 - 2$)" (2 Sample selection)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 43 to 50 antennas  
  > "The observations were taken with the 12-m array using between 43 and 50 antennas" (2 Sample selection)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.1-0.3 arcsec  
  > "providing an angular resolution from $0.1^{\prime\prime}-0.3^{\prime\prime}$, with a typical on-source integration time of 2.5 minutes." (2 Sample selection)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: typical on-source integration time of 2.5 minutes  
  > "with a typical on-source integration time of 2.5 minutes" (2 Sample selection)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.7959 GHz)
- Other facility **VLT/X-Shooter**: Spectra used to derive stellar properties of disks overlapping with the ALMA sample  
  > "we used the Very Large Telescope / X-Shooter spectra presented in" (2 Sample selection); "to derive the stellar properties of the disks that overlap with our ALMA sample." (2 Sample selection)
- External data: 12CO J=3-2 ALMA data, calibration and list of 83 detections (S/N>=3) among 202 Upper Sco sources  
  > "identified 83 $^{12}$CO $J=3 - 2$ detections with S/N $\geq3$; these are the sources we analyzed." (2 Sample selection) [from (cite: Carpenter2025)]
- External data: Stellar luminosities (log L*) used in Tables 4 and 5  
  > "The stellar luminosities were taken from Empey et al., in prep." (Table 4 notes) [from Empey et al., in prep.]
- External data: Source distances  
  > "The distances were taken from the Gaia DR3 collaboration" (Table 4 notes) [from (cite: Gaia_DR3_2023)]
- External data: Literature aspect-ratio values for comparison (Law+22,23,24 and Galloway-Sprietsma+25)  
  > "values were collected from the works of" (Table 7 notes) [from (cite: Law_2022; Law_2023; Law_2024), (cite: Galloway2025)]
- External data: Image-plane R90 values for the same sources used for the CCDF comparison  
  > "which analyzed the same sources of our sample, but using an image-plane analysis as described above." (3.2.2 Gas-disk radii extraction) [from Zagaria et al., in prep.]
- External data: AGE-PRO Upper Sco gas-disk radii used for CDF comparison  
  > "compare it with that of" (4.1 Gas-disk radii) [from (cite: Trapman_2025)]
- Simulation/model as data: Five csalt model cubes (best-fit parameters of J16213469-2612269, inclination 8, 20, 40, 55, 70 deg) used to show how moment-0 R90 depends on inclination  
  > "we generated five model cubes in the velocity range" (9 Appendix (R90 vs inclination)); "we set the inclination to five different values: 8°, 20°, 40°, 55°, 70°." (9 Appendix (R90 vs inclination))

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline (as stated for the Carpenter2025 data)  
  > "The data were calibrated with the ALMA calibration pipeline." (2 Sample selection)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, CASA 6.6.0.20 (used for channel maps of data, best-fit model and residual visibilities, not for the fit itself)  
  > "To produce these channel maps, we used the tclean routine in Common Astronomy Software Applications" (3.2.1 Fitting procedure and residual plots); "version 6.6.0.20" (3.2.1 Fitting procedure and residual plots)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1  
  > "We set four different scales (0, 10, 30, 60), with a Briggs weighting of robust=1, a threshold of 20 mJy per beam." (3.2.1 Fitting procedure and residual plots)
- uv taper: _not stated_
- cell size: 0.01 arcsec  
  > "For cleaning, we used an image size of 1500 pix, with a cell of 0.01" (3.2.1 Fitting procedure and residual plots)
- image size: 1500 pix  
  > "For cleaning, we used an image size of 1500 pix, with a cell of 0.01" (3.2.1 Fitting procedure and residual plots)
- masking: Keplerian mask from best-fit parameters of each disk; threshold 20 mJy per beam  
  > "We also specified a Keplerian mask based on the best-fit parameters for each specific disk." (3.2.1 Fitting procedure and residual plots); "We set four different scales (0, 10, 30, 60), with a Briggs weighting of robust=1, a threshold of 20 mJy per beam." (3.2.1 Fitting procedure and residual plots)
- multiscale scales: 0, 10, 30, 60 (units not stated)  
  > "We set four different scales (0, 10, 30, 60), with a Briggs weighting of robust=1, a threshold of 20 mJy per beam." (3.2.1 Fitting procedure and residual plots)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration, 12CO imaging products and detection list (S/N>=3) taken from the ALMA survey paper  
  > "The data were calibrated with the ALMA calibration pipeline." (2 Sample selection); "identified 83 $^{12}$CO $J=3 - 2$ detections with S/N $\geq3$; these are the sources we analyzed." (2 Sample selection) [from (cite: Carpenter2025)]
- Likelihood that treats spectral covariance  
  > "calculated a likelihood that explicitly treats the spectral covariance following" (3 Analysis) [from (cite: Loomis_2018)]
- Model A conceptually similar to DISCMINER but with different line-width parametrization  
  > "this parametric model is conceptually similar to the one implemented in" (3.1.1 Parametric model A) [from (cite: Izquierdo2021)]
- Power-law brightness temperature prescription  
  > "The model uses a power-law prescription for the brightness temperature, similarly to other studies" (3.1.1 Parametric model A) [from (cite: Law2021)]
- Aspect ratio <z/r> computed with the Law2021 / Paneque_2023 procedure  
  > "in the same way as" (4.3 Vertical heights); "to homogenize our analysis." (4.3 Vertical heights) [from (cite: Law2021) and (cite: Paneque_2023)]
- Temperature of optically thin-to-stellar-irradiation superheated dust layer from Eq. 7  
  > "the expected temperature of the optically thin-to-stellar irradiation-superheated dust layer reported in Eq. 7 of" (5.1 Brightness temperature - stellar luminosity correlation) [from (cite: Dullemond2001)]
- Planck mean opacities computed with dsharp_opac  
  > "We adopted a pure silicate dust composition for the Planck mean opacities" (5.1 Brightness temperature - stellar luminosity correlation) [from (cite: Birnstiel2018)]

### Not stated but needed to reproduce (our reading)

- csalt version or commit (the code is cited as in prep.)
- Which measurement sets and spectral windows were passed to csalt, and any time or channel averaging of the visibilities
- Velocity or channel range used per disk in the likelihood and the exact frequency ranges excluded for cloud absorption (only partly given in the flux table)
- Per-disk priors for all 37 sources (only the J16213469-2612269 example is tabulated; rest on GitHub)
- Whether the Carpenter2025 pipeline products or re-calibrated data were used and any continuum subtraction applied
- Random seeds, walker initialisation and exact number of extra steps needed until convergence
- Radial grid and resolution used to integrate the peak-intensity profile for R68 and R90
- Details of the bootstrap behind the quoted AD and log-rank p-value ranges
- linmix and Pearson-coefficient settings for the correlation fits, and how upper limits entered them
- Unit of the multiscale scales (0, 10, 30, 60) and clean threshold per channel

## Analysis recipe

1. **Select the sample**: Take the 12CO J=3-2 detections with S/N>=3 from the earlier ALMA survey of Upper Sco (83 sources) and attempt to fit all  
  > "identified 83 $^{12}$CO $J=3 - 2$ detections with S/N $\geq3$; these are the sources we analyzed." (2 Sample selection); "We attempted to perform our analysis on all 83" (4 Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 12CO visibilities with parametric disk models (A: two-layer, B: midplane) using csalt and emcee**: Model visibility spectra in LSRK at each timestamp, convolve with the ALMA correlator SRF, likelihood with spectral covariance, sample posterior with emcee; prescription A for 33 resolved disks, B for 4 marginally resolved disks; cloud-absorbed frequency ranges excluded from the likelihood  
  > "we generated a set of model visibility spectra in the kinematic Local Standard of Rest (LSRK) frequencies at each timestamp, convolved it with the spectral response function (SRF) of the ALMA correlator" (3 Analysis); "With this prescription, we fit the 33" (3.1.1 Parametric model A); "that allows one to exclude specific frequency ranges from the MCMC likelihood evaluation" (3.2.4 Dealing with cloud-absorbed channels)
   - software: csalt, emcee
   - parameter: 250 burn-in steps; 90 walkers; 1000 steps before first convergence check  
  > "We chose a conservative number of burn-in steps (250), we let 90 walkers evolve for 1000 steps afterward, and we then checked the results." (3.2.1 Fitting procedure and residual plots)
   - parameter: Stop when relative change in the median of each parameter is below 5% over the last 500 steps; otherwise continue  
  > "If the relative change in the median value of each parameter was below $5\%$ over the last 500 steps, the fit was stopped" (3.2.1 Fitting procedure and residual plots)
   - parameter: Priors chosen per disk for inc, PA, v_sys, M*, r_tau and r_z from the channel maps; Gaussian and uniform priors (example in Table 3)  
  > "Inspecting the channel maps, we chose priors for inc, PA," (3.2.1 Fitting procedure and residual plots); "Reference table for priors used in fitting J16213469-2612269 with model A." (Table 3)
   - parameter: Best fit = median, uncertainties = 68% interval of posterior  
  > "the median as the best fit and the uncertainties as its" (3.2.1 Fitting procedure and residual plots)
   - assumption: Emission from two thin layers, back surface mirrored from front (z_b = -z_f)  
  > "We assumed that all the disk emission comes from two thin vertical layers, with the back surface beyond the front one from the perspective of the observer." (3.1.1 Parametric model A)
   - assumption: Pure Keplerian rotation and purely thermal line width  
  > "The model takes into account pure Keplerian rotation" (3.1.1 Parametric model A); "is purely thermal and described through" (3.1.1 Parametric model A)
   - assumption: Temperature and optical depth profiles equal for front and back surfaces  
  > "Both temperature and optical depth profiles are assumed to be equal for the front and back surfaces." (3.1.1 Parametric model A)
   - assumption: Model B: emission in the midplane with constant optical depth out to R_out  
  > "The model B case assumes the emission is generated in the midplane" (3.1.2 Parametric model B)
   - assumption: Distances from Gaia DR3  
  > "The distances were taken from the Gaia DR3 collaboration" (Table 4 notes)
   - fitting: emcee MCMC inside csalt; spectral-covariance likelihood; Gaussian/uniform priors  
  > "We used Markov chain Monte Carlo (MCMC) algorithms to model the posterior distribution of our parametric models, and we sampled it using" (3.2.1 Fitting procedure and residual plots); "calculated a likelihood that explicitly treats the spectral covariance following" (3 Analysis)
   - validation: Residual channel maps (best-fit visibilities subtracted) checked for 3 and 5 sigma residuals  
  > "In the third row, we show the channel maps of residuals, which were obtained by cleaning the residual visibilities (data - model)." (3.2.1 Fitting procedure and residual plots)
3. **Image data, best-fit model and residual visibilities for channel-map comparison**: tclean on data, best-fit model visibilities and residual visibilities with identical parameters  
  > "to clean the best-fit visibilities we used the same cleaning parameters as above." (3.2.1 Fitting procedure and residual plots); "We chose a different velocity range for each disk so that it was possible to visualize the full-disk emission in ten channels." (3.2.1 Fitting procedure and residual plots)
   - software: CASA, tclean
   - parameter: image size 1500 pix, cell 0.01 arcsec, scales (0, 10, 30, 60), robust=1, threshold 20 mJy per beam, Keplerian mask  
  > "For cleaning, we used an image size of 1500 pix, with a cell of 0.01" (3.2.1 Fitting procedure and residual plots); "We set four different scales (0, 10, 30, 60), with a Briggs weighting of robust=1, a threshold of 20 mJy per beam." (3.2.1 Fitting procedure and residual plots)
   - fitting: _not stated_
   - validation: Non-Keplerian motion would appear as red or blue blobs in residual maps  
  > "if any non-Keplerian motion is found in the data, it manifests as either a red or blue blob in the residual maps." (3.2.1 Fitting procedure and residual plots)
4. **Derive gas-disk radii R68 and R90**: Compute the peak surface-brightness profile of the front surface at the 12CO J=3-2 rest frequency from the best-fit model, integrate in cylindrical coordinates, take radii enclosing 68% and 90% of the emission; uncertainties from MCMC draws (16th and 84th percentiles)  
  > "Secondly, we integrated the peak surface-brightness profile in cylindrical coordinates and extracted the radius that encompasses" (3.2.2 Gas-disk radii extraction); "To determine the uncertainties of the gas-disk radii, we selected all random draws from the MCMC chain parameters needed in Eq." (3.2.2 Gas-disk radii extraction)
   - software: csalt
   - parameter: rest frequency 345.7959 GHz  
  > "rest frequency $(\nu=345.7959$ GHz)" (3.2.2 Gas-disk radii extraction)
   - fitting: _not stated_
   - validation: Anderson-Darling two-sample test of the R90 CCDF against an image-plane analysis of the same sources (p=0.8, range 0.6-0.9) and against AGE-PRO (p=0.7, range 0.5-0.8)  
  > "which means that the two distributions cannot be distinguished within uncertainties." (3.2.2 Gas-disk radii extraction); "To determine if our results are consistent, we ran the AD two-sample test" (4.1 Gas-disk radii)
5. **Measure data and model integrated 12CO fluxes**: Moment-0 maps over +/-15 km/s around systemic velocity, summed inside a geometric mask from the best-fit geometry with size R90+0.2 arcsec; uncertainty from the scatter of the mask moved to 8 emission-free positions; model fluxes from best-fit cubes with bootstrapped uncertainty  
  > "we first generated moment 0 maps using a bandwidth of $\pm15$ km s$^{-1}$ centered around the systemic velocity" (10 Appendix (fluxes)); "we moved the mask around the moment 0 maps in 8 different locations that were not enclosing any disk emission" (10 Appendix (fluxes))
   - software: bettermoments
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit the 12CO size-luminosity correlation**: Linear regression of log R90 against log L_CO (flux scaled to 140 pc) with linmix; compared with Long2022 slope and intercept  
  > "We fit the correlation using the" (4.2.1 12CO flux - size correlation); "The slope we derived is comparable to that found in" (4.2.1 12CO flux - size correlation)
   - software: linmix
   - assumption: L_CO = F_CO x (d/140 pc)^2  
  > "disk luminosity" (4.2.1 12CO flux - size correlation)
   - fitting: linmix regression  
  > "We fit the correlation using the" (4.2.1 12CO flux - size correlation)
   - validation: _not stated_
7. **Derive emission-surface heights and aspect ratio <z/r>**: Evaluate z(r) from random MCMC draws (median, 16th and 84th percentiles); r_cut is where the height profile stops increasing, r_taper = 0.8 r_cut, <z/r> averaged over 0<=r<=r_taper; compare with literature via Kaplan-Meier estimator and log-rank test  
  > "using random draws from the MCMC chains of" (4.3 Vertical heights); "as the value of the radius for which the vertical-height profile stops increasing." (4.3 Vertical heights); "which accounts for upper limits via the Kaplan-Meier estimator" (4.3 Vertical heights)
   - software: lifelines
   - fitting: _not stated_
   - validation: Log-rank test against Galloway-Sprietsma+25 and Law+22,23,24 samples; caveat about lower angular resolution noted  
  > "are based on observations with significantly lower angular resolution compared to those used in" (4.3 Vertical heights)
8. **Relate 12CO brightness temperature at 10 au to stellar luminosity and dust temperature**: Fit T_b,10 against L*; compare with blackbody equilibrium temperature and the superheated-dust temperature from Dullemond2001 Eq. 7 using Planck mean opacities of pure silicate; infer opacity-temperature exponent beta  
  > "We adopted a pure silicate dust composition for the Planck mean opacities" (5.1 Brightness temperature - stellar luminosity correlation); "the expected temperature of the optically thin-to-stellar irradiation-superheated dust layer reported in Eq. 7 of" (5.1 Brightness temperature - stellar luminosity correlation)
   - software: dsharp_opac
   - assumption: Dust opacity: pure silicate composition  
  > "We adopted a pure silicate dust composition for the Planck mean opacities" (5.1 Brightness temperature - stellar luminosity correlation)
   - fitting: _not stated_
   - validation: Slope of dust-temperature line (about 0.22) compared with the observed correlation  
  > "the existence of this correlation offers empirical evidence that the basic dust models we used are reasonable." (5.1 Brightness temperature - stellar luminosity correlation)
9. **Test the <z/r> versus R90 correlation**: Linear fit of <z/r> on R90 after removing the face-on disk J16042165-2130284 and treating three disks as upper limits; compared with Galloway-Sprietsma+25 best fit  
  > "We removed J16042165-2130284 from the sample, as it is found to be a face-on disk" (5.2 <z/r> - disk size correlation); "The solid black curve represents the best fit, and in blue we over-plot the best-fit curve found by" (5.2 <z/r> - disk size correlation)
   - fitting: _not stated_
   - validation: Correlation stated to remain significant without the exclusions; fraction of posterior samples with intercept > 0 is about 0.999  
  > "We stress that the correlation would still be significant if we had not made such arrangements." (5.2 <z/r> - disk size correlation)

## Software

- **csalt** : Visibility-spectra forward modelling and parameter inference of the disk models  
  > "which allows robust inference on model parameters using visibility fitting." (3 Analysis)
- **emcee** : MCMC posterior sampling  
  > "We used Markov chain Monte Carlo (MCMC) algorithms to model the posterior distribution of our parametric models, and we sampled it using" (3.2.1 Fitting procedure and residual plots)
- **CASA (tclean)** 6.6.0.20: Imaging channel maps of data, best-fit models and residuals  
  > "To produce these channel maps, we used the tclean routine in Common Astronomy Software Applications" (3.2.1 Fitting procedure and residual plots); "version 6.6.0.20" (3.2.1 Fitting procedure and residual plots)
- **bettermoments** : Moment-0 maps for integrated fluxes  
  > "For this step, we used bettermoments" (10 Appendix (fluxes))
- **scipy** : Anderson-Darling two-sample test  
  > "After running the Anderson-Darling two-sample test (AD; as implemented in" (3.2.2 Gas-disk radii extraction)
- **linmix** : Linear regression of the R90 - L_CO correlation  
  > "We fit the correlation using the" (4.2.1 12CO flux - size correlation)
- **lifelines** : Kaplan-Meier estimator and log-rank test with upper limits  
  > "we show the Kaplan-Meier estimator (as implemented in" (4.3 Vertical heights)
- **gofish** : Radial profiles of convolved model moment maps in the R90-inclination test  
  > "we extracted the radial profile of our convolved models and integrated it to derive" (9 Appendix (R90 vs inclination))
- **dsharp_opac** : Planck mean opacities of silicate dust  
  > "We adopted a pure silicate dust composition for the Planck mean opacities" (5.1 Brightness temperature - stellar luminosity correlation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disks fitted (prescription A + B) out of 83 12CO detections | 37 (33 + 4) | not stated | dimensionless | 2 | We were able to fit 37 sources out of a sample of 83, 33 with prescription A and four with prescription B. |
| Median gas-disk size R90 | ~82 | not stated | au | 4 | We find a median gas-disk size of $R_{90\%} \sim 82$ au |
| R90 of J16042165-2130284 (largest disk) | 247 | +/-1 | au | 4 | for which we derive $R_{90\%}=247\pm1$ au |
| R90 of J16095933-1800090 (most compact disk) | 22 | +/-3 | au | 4 | for which we derive $R_{90\%}=22\pm3$ au. |
| R90 of compact disk J16062861-2121297 | 56 | +/-1 | au | 4 | gas-disk size $R_{90\%} = 56\pm1$ au |
| AD p-value, R90 distribution vs image-plane analysis | 0.8 | range [0.6, 0.9] | dimensionless | 4 | we obtained an AD $p$-value $p=0.8$ in the range of $[0.6, 0.9]$ |
| AD p-value, R90 distribution vs AGE-PRO | 0.7 | range [0.5, 0.8] | dimensionless | 4 | we obtained a $p$-value $p=0.7$ in the range of $[0.5, 0.8]$ |
| R90 - L_CO fit: intercept and slope of log10 R90 vs log10 L_CO | intercept 1.77, slope 0.49 | +/-0.03 (intercept), +/-0.05 (slope) | dimensionless | 6 | (1.77\pm0.03) + (0.49\pm0.05) |
| Median aspect ratio <z/r> | ~0.16 | not stated | dimensionless | 7 | We find a median value of $\langle z/r \rangle \sim0.16$ |
| Log-rank p-value of <z/r> vs Galloway-Sprietsma+25 | 0.05 | range [0.02, 0.12] | dimensionless | 7 | ($p=0.05$ in a range $[0.02, 0.12]$) |
| Log-rank p-value of <z/r> vs Law+22,23,24 | 0.03 | range [0.01, 0.08] | dimensionless | 7 | ($p=0.03$ in a range $[0.01, 0.08]$) |
| log T_b,10 vs log L* correlation (intercept, slope) | intercept 2.10, slope 0.24 | +/-0.05 (intercept), +/-0.07 (slope) | dimensionless | 8 | (2.10 \pm 0.05) + (0.24 \pm 0.07) |
| Pearson coefficient of T_b,10 - L* | 0.6 | range [0.4, 0.7] | dimensionless | 8 | with a Pearson correlation coefficient of 0.6 in a range $[0.4, 0.7]$ |
| T_b,10 vs R90 relation (intercept, slope) | intercept 70 K, slope 0.2 K/au | +/-12 (intercept), +/-0.1 (slope) | K; K per au | 8 | (70\pm12) + (0.2\pm0.1) |
| Planck mean opacity temperature exponent beta | ~0.2 | not stated | dimensionless | 8 | from this we found $\beta\sim0.2$. |
| <z/r> vs R90 relation (intercept, slope) | intercept 0.05, slope 0.0009 per au | +/-0.03 (intercept), +/-0.0003 (slope) | dimensionless; per au | 9 | (0.05 \pm 0.03) + (0.0009 \pm 0.0003) |
| Pearson coefficient of <z/r> - R90 | 0.6 | not stated | dimensionless | 9 | and it is found with a Pearson correlation coefficient of $0.6$. |
| Overestimate of moment-0 R90 for a 70 deg inclined disk with <z/r>=0.14 | ~40 | not stated | percent | 0 | can be $\sim 40\%$ greater than the true value. |

## Qualitative findings

- csalt separates diffuse foreground cloud emission from Keplerian disk emission in cloud-contaminated disks  
  > "is able to separate the diffuse cloud emission, which results in red residuals, and Keplerian disk emission." (3.2.4 Dealing with cloud-absorbed channels)
- J16113134-1838259 (AS 205) likely shows a fly-by and J16193570-1950426 shows probable inflow/outflow, so neither could be fit  
  > "shows what is very likely to be a fly-by" (5.4 Multiple systems); "shows evidence for what is likely to be an emission inflow/outflow" (5.4 Multiple systems)
- Basic dust models used are supported by the T_b - L* correlation  
  > "the existence of this correlation offers empirical evidence that the basic dust models we used are reasonable." (5.1 Brightness temperature - stellar luminosity correlation)

## Claim tuples

- H: Can spectral-line visibility fitting be applied to a whole moderate-resolution survey? | E: csalt fits with models A and B to 83 12CO J=3-2 detections in Upper Sco | R: 37 of 83 fitted; failures tied to low spectral sampling, low S/N and poor resolution | F: Visibility fitting becomes difficult when the integrated-flux S/N is below about 10 | **supported**
- H: Do model-derived gas-disk radii agree with image-plane radii? | E: Compare R90 CCDF from csalt peak-intensity profile with image-plane analysis and AGE-PRO using the AD test | R: p=0.8 [0.6, 0.9] and p=0.7 [0.5, 0.8] | F: The method gives results comparable to the usual literature approach on the same sample | **supported**
- H: Does the 12CO brightness temperature track stellar luminosity, and where is the CO layer relative to superheated dust? | E: Fit T_b,10 vs L*, compare with equilibrium and superheated-dust temperatures | R: log T_b,10 = (2.10 +/- 0.05) + (0.24 +/- 0.07) log L*, Pearson 0.6 | F: The optically thick 12CO layer lies deeper than the optically thin-to-stellar-irradiation dust layer | **supported**
- H: Does the <z/r> - R90 correlation found for large bright disks hold for compact Upper Sco disks? | E: Fit <z/r> vs R90 for fitted model-A disks and compare with Galloway-Sprietsma+25 | R: <z/r> = (0.05 +/- 0.03) + (0.0009 +/- 0.0003) R90, Pearson 0.6; median <z/r> ~0.16 | F: The correlation holds for fainter, more compact disks; median <z/r> is lower than for larger, brighter disks | **supported**
- H: Is the R90 - L_CO relation in Upper Sco the same as in other samples? | E: linmix fit of log R90 vs log L_CO and comparison with Long2022 | R: slope 0.49 +/- 0.05; intercept differs by about 0.3 (about 7 sigma) from Long2022 | F: Slope is comparable (optically thick emission) but the intercept differs, likely from different radius techniques and data quality | **partially**

## Reasoning

- Why this data: Large uniform Upper Sco 12CO J=3-2 survey with moderate resolution; visibility modelling had never been applied to a large survey  
  > "but it has never been applied on a large survey: in this work, we filled this gap." (1 Introduction)
- Why this method: Radii from the model peak-intensity profile avoid the inclination and projected-velocity dependence of moment-0 radii  
  > "To avoid this intrinsic effect, to determine the gas-disk radii, we first computed the peak surface-brightness profile of the disk front surface at the" (3.2.2 Gas-disk radii extraction)
- Alternative: Back surface fixed at the midplane or removed was tested and rejected in favour of z_b = -z_f  
  > "This choice was adopted as the optimal compromise after testing different parametric prescriptions where the back surface was fixed at the midplane or completely removed." (Footnote 4)
- Alternative: Moment-0 radii not used because they depend on inclination and velocity field  
  > "To avoid this intrinsic effect, to determine the gas-disk radii, we first computed the peak surface-brightness profile of the disk front surface at the" (3.2.2 Gas-disk radii extraction)
- How they decided it was enough: Fit stopped when median parameter change was small over the last 500 steps  
  > "over the last 500 steps, the fit was stopped; otherwise, the walkers were allowed to evolve for additional steps until this condition was met." (3.2.1 Fitting procedure and residual plots)
- Limitation (authors): Only 37 of 83 detections could be fit; results sensitivity-limited  
  > "we were unable to achieve any acceptable convergence for our parametric models on the remaining 46 disks for a variety of reasons." (4 Results); "However, as said before, our results are sensitivity-limited." (4.1 Gas-disk radii)
- Limitation (authors): Radii not directly comparable with literature definitions  
  > "we stress that our results are not directly comparable with what has been done in the literature so far." (3.2.2 Gas-disk radii extraction)
- Limitation (authors): Model A is a simplistic description of the disk  
  > "this is still very simplistic in comparison with the real complexity of the disk." (3.1.1 Parametric model A)
- Limitation (authors): Lower angular resolution than comparison samples limits the <z/r> comparison  
  > "are based on observations with significantly lower angular resolution compared to those used in" (4.3 Vertical heights)
- Caveat (inferred, ours): Radius and temperature results depend on simplified parametric models with thermal-only line widths and mirrored front/back surfaces; no check against radiative transfer
- Caveat (inferred, ours): Per-disk priors were chosen by hand from channel maps, which may bias parameters; prior sensitivity not shown
- Caveat (inferred, ours): Fitted subset (37 of 83) is biased toward bright, large disks, so population medians are not representative
- Caveat (inferred, ours): Stellar luminosity, stellar mass and distances come from other work in prep., limiting independent checking of T_b-L* result
- Caveat (inferred, ours): The T_b,10 correlation extrapolates a power law to 10 au where the data have no resolution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: csalt is on GitHub  
  > "https://github.com/seanandrews/csalt" (Footnote 3)
- Code: Priors, scripts to generate them, corner plots and flux table are on GitHub  
  > "The full set of priors used in this work and the scripts to generate them for both parametrizations are available on" (3.2.1 Fitting procedure and residual plots); "https://github.com/lzallio/USco_gas_2025" (Footnote 5)
- Missing: csalt release or commit (cited as in preparation)
- Missing: Exact visibility input products and data selection per disk
- Missing: Stellar luminosities from Empey et al. in prep.
- Missing: Image-plane radii of Zagaria et al. in prep. used in the CCDF comparison
- Data volume (inferred): Four archival Band 7 projects with very short (2.5 min) observations of 202 sources; raw data likely tens of GB, with only the 12CO spectral window needed for 83 detections (a few GB of visibilities).
- Score (inferred): 3/5, Data come from public ALMA archive projects and the priors, scripts and csalt are on GitHub, with numeric tables, but csalt is in prep. and key inputs (visibility selection, stellar luminosities, per-disk setup) are external or unstated.
- Rediscovery candidate: yes, Project codes are listed, per-disk fit tables and flux tables are numeric, and the csalt code and priors are on GitHub, so R90 and <z/r> for a few disks could be redone, though the full pipeline needs the csalt release.

## Links

- Method: (cite: Carpenter2025) (Source of the ALMA observations, calibration and 12CO detection list)
- Method: (cite: Loomis_2018) (Spectral-covariance likelihood used in csalt)
- Method: (cite: Law2021) (Aspect-ratio <z/r> method and brightness-temperature parametrization)
- Method: Andrews et al., in prep. (csalt visibility fitting code)
- Method: (cite: Dullemond2001) (Superheated dust-layer temperature (Eq. 7))
- Companion: (cite: 2026A&A...708L...1Z) (Will cover the derived stellar masses)
- Companion: Zagaria et al., in prep. (Image-plane analysis of R90 for the same sources)
- Companion: (cite: Trapman_2025) (AGE-PRO Upper Sco gas-disk radii used for comparison)
- Companion: (cite: Galloway2025) (exoALMA <z/r> values used for comparison)
- Related: AGE-PRO
- Related: exoALMA

## Checks

```json
{
 "quotes": 144,
 "quotes_ok": 144,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 83,
  "rate": 0.703
 },
 "evidence_ok": true
}
```
