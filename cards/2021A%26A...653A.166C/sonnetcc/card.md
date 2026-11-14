# Structured velocity field in the inner envelope of B335: ALMA observations of rare CO isotopologues

`2021A&A...653A.166C` | Astronomy and Astrophysics 2021 | first author: Cabedo, Victoria | arXiv: 2107.01986 | DOI: 10.1051/0004-6361/202140754

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Investigate the molecular line velocity profiles of the Class 0 protostar B335 and constrain the infall motions in its circumstellar gas, in particular the origin of double-peaked C17O profiles  
  > "This work aims at investigating the molecular line velocity profiles of the Class 0 protostellar object B335 and attempts to put constraints on the infall motions happening in the circumstellar gas of the object." (abstract)
- Target **B335**: coordinates alpha = 19:37:00.9, delta = +07:34:09.6 (J2000), dust continuum peak  
  > "$\alpha =$ 19:37:00.9 and $\delta =$ +07:34:09.6 in J2000 coordinates" (Observations and data reduction); "is located at a distance of 164.5 pc, (cite: Watson2020)" (Introduction); z/distance 164.5 pc  
  > "$\alpha =$ 19:37:00.9 and $\delta =$ +07:34:09.6 in J2000 coordinates" (Observations and data reduction); "is located at a distance of 164.5 pc, (cite: Watson2020)" (Introduction); distance from Watson 2020 (cite: Watson2020)  
  > "$\alpha =$ 19:37:00.9 and $\delta =$ +07:34:09.6 in J2000 coordinates" (Observations and data reduction); "is located at a distance of 164.5 pc, (cite: Watson2020)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01552.S
- bands: _not stated_
- frequencies and spectral setup: Rest frequencies: 12CO (2-1) 230.53 GHz, C17O (1-0) 112.359 GHz, C18O (1-0) 109.782 GHz; image spectral resolution 0.20 km/s  
  > "| Rest Frequency (GHz) | 230.53 | 112.359 | 109.782 |" (Table 1); "because of the limited spectral resolution (0.2 km s$^{-1}$)" (Linewidths and kinetic temperature)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C17O and C18O: C40-2 and C40-5 (only C40-2 used for maps); 12CO: C40-1 and C40-4 (combined)  
  > "C$^{17}$O (1-0) and C$^{18}$O (1-0) were targeted using two configurations, C40-2 and C40-5, and $^{12}$CO (2-1) was targeted using C40-1 and C40-4." (Observations and data reduction); "The C$^{17}$O emission was only detected in the most compact configuration (C40-2), therefore only this configuration has been used to produce C$^{17}$O and C$^{18}$O maps" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: Beam 2.6 x 1.9 arcsec (C17O, 12CO after smoothing), 2.7 x 2.0 arcsec (C18O)  
  > "| Beam major (arcsec) | 2.6 | 2.6 | 2.7 |" (Table 1); "| Beam minor (arcsec) | 1.9 | 1.9 | 2.0 |" (Table 1)
- max recoverable scale: LRS = 10.6 arcsec (12CO), 21.9 (C17O), 22.4 (C18O)  
  > "| 10.6 | 21.9 | 22.4 |" (Table 1)
- sensitivity: RMS 10.0 mJy/beam (C17O), 10.7 mJy/beam (C18O), 2016.9 (12CO, as printed)  
  > "| RMS (mJy/beam) | 2016.9 | 10.0 | 10.7 |" (Table 1)
- time on source: _not stated_
- observing dates: Cycle 4, October 2016 to September 2017  
  > "during the cycle 4 observation period from October 2016 to September 2017" (Observations and data reduction)
- pi or archival as stated: Project 2016.1.01552.S, PI A. Maury (paper does not say archival)  
  > "as part of the project 2016.1.01552.S (PI. A. Maury)" (Observations and data reduction)
- Line: C17O J=1-0 (112.359 GHz)
- Line: C18O J=1-0 (109.782 GHz)
- Line: 12CO J=2-1 (230.53 GHz)
- Other facility **Nobeyama 45 m**: Single-dish C18O (1-0) data from Saito et al. 1999, used to estimate the flux recovered by ALMA  
  > "comparing it with the 45 m Nobeyama data of the same transition presented in (cite: Saito1999)" (Possible origins of the observed gas motions)
- External data: H2 peak column density 3.1e22 cm^-2 at 3600 au, used for the opacity estimate  
  > "3.1 $\times$ 10$^{22}$ cm$^{-2}$ is the peak column density of H$_{2}$ in B335 at a radius of 3600 au ((cite: Launhardt2013))" (Line opacity estimation) [from (cite: Launhardt2013)]
- External data: C17O abundance relative to H2 of 5e-8  
  > "= 5 $\times$ 10$^{-8}$ is the C$^{17}$O abundance relative to H$_{2}$ abundance ((cite: Thomas2008))" (Line opacity estimation) [from (cite: Thomas2008)]
- External data: Einstein coefficient A10 = 6.695e-8 s^-1 for C17O J=1-0  
  > "is the Einstein coefficient for the C$^{17}$O J = 1–0 transition ((cite: Hitran2017), (cite: Splatalogue2005))" (Line opacity estimation) [from (cite: Hitran2017), (cite: Splatalogue2005)]
- External data: C18O is a factor of 3.6-3.9 more abundant than C17O  
  > "C$^{18}$O is a factor of 3.6-3.9 more abundant than C$^{17}$O ((cite: Penzias1981), (cite: Jorgensen2002))" (Intensity ratio) [from (cite: Penzias1981), (cite: Jorgensen2002)]
- External data: Dust temperature formula for optically thin regime with central heating, adapted to 164.5 pc, used as gas kinetic temperature  
  > "formula for dust temperature in an optically thin regime assuming only central heating by the B335 protostar derived by (cite: Shirley2011)" (Linewidths and kinetic temperature); "which we adapted to the new distance of 164.5 pc" (Linewidths and kinetic temperature) [from (cite: Shirley2011); (cite: Evans2015)]
- External data: Central object mass 0.05-0.26 Msun from infall models  
  > "which are the predicted values from infall models (see (cite: Yen2015b), (cite: Evans2015), Evans et al. in prep.)" (Linewidths and kinetic temperature) [from (cite: Yen2015b), (cite: Evans2015), Evans et al. in prep.]
- External data: B335 continuum centroid position taken from high resolution maps  
  > "corresponding to the peak of dust continuum obtained from high resolution maps ((cite: Maury2018))" (Observations and data reduction) [from (cite: Maury2018)]

## Processing

### Calibration

- pipeline or manual: standard script for cycle-4 ALMA data  
  > "Calibration of the raw data was done using the standard script for cycle-4 ALMA data using the Common Astronomy Software Applications (CASA) version 5.6.1-8." (Observations and data reduction)
- casa version: CASA 5.6.1-8  
  > "Calibration of the raw data was done using the standard script for cycle-4 ALMA data using the Common Astronomy Software Applications (CASA) version 5.6.1-8." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: Delivered product images used only for a preliminary check; final images made from calibrated visibilities  
  > "Preliminary analysis of the data was done with the product images delivered by ALMA to check if emission was detected and to check the shape of the line profiles." (Observations and data reduction)
- flux calibrator: C40-2: J1751+0939; C40-4: J2148+0657; C40-5: J2148+0657  
  > "| 110.0 | 0.08 | J1751+0939 | J1938+0448 | J1751+0939 |" (Technical details of the ALMA observations); "| 231.0 | 0.09 | J2148+0657 | J1851+0035 | J2148+0657 |" (Technical details of the ALMA observations); "| 110.0 | 0.08 | J2148+0657 | J1938+0448 | J2025+3343 |" (Technical details of the ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-calibrated with CASA; line data calibrated with the continuum self-cal model when possible  
  > "Continuum emission was self-calibrated with CASA. Line emission was calibrated using the self-calibrated model derived from the continuum data when it was possible." (Observations and data reduction)

### Imaging

- task: tCLEAN within CASA  
  > "Final images of the data were generated from the calibrated visibilities using the tCLEAN algorithm within CASA" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 2 for C17O and C18O; robust = 1 for 12CO  
  > "using Briggs weighting with robust parameter set to 2 for C$^{17}$O and C$^{18}$O and 1 for $^{12}$CO" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C17O/C18O: C40-2 only; 12CO: combination of two configurations  
  > "while $^{12}$CO was detected in both configurations so a combination of the two data sets has been used to produce the maps" (Observations and data reduction)
- smoothing: 12CO maps smoothed to the angular resolution of C17O and C18O  
  > "After imaging, $^{12}$CO maps were smoothed to reach the same angular resolution as C$^{17}$O and C$^{18}$O." (Observations and data reduction)
- final beam: 2.6 x 1.9 arcsec (C17O), 2.7 x 2.0 arcsec (C18O), 2.6 x 1.9 arcsec (12CO)  
  > "| Beam major (arcsec) | 2.6 | 2.6 | 2.7 |" (Table 1); "| Beam minor (arcsec) | 1.9 | 1.9 | 2.0 |" (Table 1)
- final rms: 10.0 mJy/beam (C17O), 10.7 mJy/beam (C18O), 2016.9 (12CO, as printed)  
  > "| RMS (mJy/beam) | 2016.9 | 10.0 | 10.7 |" (Table 1)

### Inherited from earlier work

- Calibration done with the standard ALMA cycle-4 script  
  > "Calibration of the raw data was done using the standard script for cycle-4 ALMA data" (Observations and data reduction) [from standard script for cycle-4 ALMA data (no citation)]
- Largest recoverable scale definition  
  > "is the minimum baseline of the configuration, in m ((cite: ALMAc4))" (Table 1) [from (cite: ALMAc4)]
- Opacity estimated from H2 column density and a standard C17O abundance  
  > "The maximum opacity at the center of the source has been estimated from the H$_{2}$ column density and assuming a standard C$^{17}$O abundance" (Line opacity estimation) [from (cite: Jansen1995)]
- Envelope mass from integrated 110 GHz continuum with standard assumptions  
  > "and using standard assumptions (see Eq. 4 in (cite: Jorgensen2007))" (Linewidths and kinetic temperature) [from Eq. 4 in (cite: Jorgensen2007)]
- Hyperfine-structure line fitting with the HfS program  
  > "The spectrum at each pixel has been modeled using a program that allows to fit the hyperfine structure of spectral lines with multiple velocity components" (Modeling of the molecular line profiles) [from (cite: Estalella2017)]
- Central object mass range and infall rate taken from infall models, partly in prep.  
  > "which are the predicted values from infall models (see (cite: Yen2015b), (cite: Evans2015), Evans et al. in prep.)" (Linewidths and kinetic temperature) [from (cite: Yen2015b), (cite: Evans2015), Evans et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Self-calibration parameters (continuum channels/spws, solints, number of iterations, solution mode)
- How the continuum was formed and which channels were line-free; how continuum was subtracted from line cubes (task, order)
- tclean parameters: deconvolver, niter, threshold, masks, cell size, image size, primary-beam correction, spectral gridding
- Smoothing kernel and method used to match 12CO to the C17O/C18O beam, and how beam-matched C17O/C18O maps were made
- 12CO RMS of 2016.9 mJy/beam looks like a unit error; true value not given
- Initial guesses, hyperfine component setup and rest frequencies/relative intensities used in HfS, and how the 3 sigma threshold was applied per pixel
- Dust opacity, dust temperature and gas-to-dust ratio behind the 'standard assumptions' for envelope mass within 100 and 860 au
- Exact regions and apertures used for averaged linewidths, opacities and the missing flux comparison; how the 860 au 3 sigma radius was measured
- Which execution blocks and how many were combined for each configuration, and calibration flux scale uncertainty

## Analysis recipe

1. **Calibrate, self-calibrate and image the lines**: Standard cycle-4 calibration in CASA, continuum self-calibration, tCLEAN imaging with Briggs weighting, 12CO smoothed to the C17O/C18O resolution  
  > "Calibration of the raw data was done using the standard script for cycle-4 ALMA data using the Common Astronomy Software Applications (CASA) version 5.6.1-8." (Observations and data reduction); "Final images of the data were generated from the calibrated visibilities using the tCLEAN algorithm within CASA" (Observations and data reduction)
   - software: CASA, tclean
   - parameter: Briggs robust = 2 for C17O and C18O, robust = 1 for 12CO  
  > "using Briggs weighting with robust parameter set to 2 for C$^{17}$O and C$^{18}$O and 1 for $^{12}$CO" (Observations and data reduction)
   - parameter: C17O/C18O maps from C40-2 only; 12CO from two configurations combined  
  > "The C$^{17}$O emission was only detected in the most compact configuration (C40-2), therefore only this configuration has been used to produce C$^{17}$O and C$^{18}$O maps" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and per-pixel spectra**: Moment 0 maps of C17O and 12CO; C17O spectra extracted at every 0.5 arcsec pixel to build a spectral map  
  > "the C$^{17}$O spectra were taken at every 0.5$''$ pixel of the emission cube, producing a spectral map" (Results and analysis)
   - parameter: Mean radius of 3 sigma C17O emission is 860 au  
  > "The mean radius of the 3$\sigma$ emission is 860 au, indicating that it traces the dense envelope." (Results and analysis)
   - fitting: _not stated_
   - validation: Interferometric filtering of a dip discarded because emission size is of the order of the largest recoverable scale; 12CO moment 0 used to check C17O is not outflow  
  > "The possibility of the dip being caused by interferometric filtering is discarded since the recovered emission size is of the order of the Largest Recoverable Scale" (Results and analysis)
3. **Estimate maximum C17O line opacity from column density**: Opacity tau0 from A10, nu, peak H2 column density, C17O abundance and linewidth (Jansen 1995 formula)  
  > "The maximum opacity at the center of the source has been estimated from the H$_{2}$ column density and assuming a standard C$^{17}$O abundance" (Line opacity estimation)
   - parameter: Delta V approx 1 km/s average linewidth of the two components together  
  > "$\Delta V$ $\approx$ 1 kms$^{-1}$ is the average observed linewidth for the two components together" (Line opacity estimation)
   - assumption: H2 column density 3.1e22 cm^-2 (peak at 3600 au) and C17O abundance 5e-8  
  > "3.1 $\times$ 10$^{22}$ cm$^{-2}$ is the peak column density of H$_{2}$ in B335 at a radius of 3600 au ((cite: Launhardt2013))" (Line opacity estimation); "= 5 $\times$ 10$^{-8}$ is the C$^{17}$O abundance relative to H$_{2}$ abundance ((cite: Thomas2008))" (Line opacity estimation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare C17O and C18O integrated intensities**: Beam-matched C17O and C18O maps; ratio of integrated intensities W(C17O)/W(C18O) compared with the optically thin expectation from abundances  
  > "We produced beam-matching maps for C$^{17}$O and C$^{18}$O to compare the gas at similar scales in both isotopes." (Intensity ratio); "where W$_{i}$ is the integrated intensity of each C$^{17}$O and C$^{18}$O individual spectra" (Intensity ratio)
   - parameter: Integration ranges: C17O 4.8-6.2 and 7.4-9.4 km/s (two hyperfine components); C18O 7.4-9.4 km/s  
  > "Intensities are integrated over the two velocity ranges of 4.8-6.2 km s$^{-1}$ and 7.4-9.4 km s$^{-1}$ for C$^{17}$O" (Intensity ratio)
   - assumption: C17O and C18O probe similar conditions; differences arise only from opacity; no fractionation or selective photodissociation  
  > "Thus, the only difference in the emission from these two isotopes should result from opacity effects" (Intensity ratio)
   - fitting: _not stated_
   - validation: Observed ratio agrees with the expected optically thin ratio and no increase toward the center  
  > "Our observations are therefore in general agreement with the expected ratio if both transitions are optically thin." (Intensity ratio)
5. **Fit two-component hyperfine model to C17O spectra**: HfS fit per pixel with two velocity components (blue and red), giving velocity, linewidth and opacity maps  
  > "it was attempted to model the double-peaked profiles with two velocity components, one blue- and another red-shifted" (Modeling of the molecular line profiles)
   - software: HfS
   - parameter: Per component, four free parameters: linewidth (shared by hyperfine components), main line central velocity, main line peak intensity, optical depth  
  > "fits simultaneously four independent parameters: the linewidth assumed to be the same for each hyperfine component; the main line central velocity; the main line peak intensity and the optical depth" (Modeling of the molecular line profiles)
   - parameter: Minimum signal-to-noise of 3 sigma for fitting  
  > "the program is allowed to proceed to fit emission with a minimum signal-to-noise ratio of 3$\sigma$" (Modeling of the molecular line profiles)
   - assumption: C17O (1-0) expected to be optically thin  
  > "Because the C$^{17}$O (1-0) emission is expected to be optically thin" (Modeling of the molecular line profiles)
   - fitting: Parameter space sampled to minimise chi^2 of the residual; no priors stated  
  > "The fitting procedure samples the space parameters to find the minimum value of the fit residual $\chi^{2}$." (Modeling of the molecular line profiles)
   - validation: Fitted opacities compared with the earlier upper limit  
  > "which is in concordance with the upper limit estimated before" (Modeling of the molecular line profiles)
6. **Kinetic temperature, thermal and non-thermal linewidths**: Tk(r) from a central-heating temperature profile at 100 and 860 au; thermal linewidth for C17O (29.01 amu); non-thermal part from v_obs^2 = v_th^2 + v_nonth^2  
  > "The gas kinetic temperature was computed for the two radii probed" (Linewidths and kinetic temperature); "The non-thermal contribution of the line has been computed for both velocity components" (Linewidths and kinetic temperature)
   - parameter: Radii 100 au (about half the FWHM beam) to 860 au  
  > "A region enclosing radii from 100 (about half of the FWHM beam) to 860 au has been chosen to analyze the gas kinematics." (Linewidths and kinetic temperature)
   - assumption: Dust and gas in thermal equilibrium, coupled by collisions at densities above 1e5 cm^-3  
  > "The underlying assumption is that dust and gas are expected to be in thermal equilibrium, being coupled via collisions at the densities probed here" (Linewidths and kinetic temperature)
   - fitting: _not stated_
   - validation: _not stated_
7. **Estimate free-fall velocity difference between 100 and 860 au**: Difference of free-fall velocities v_ff(r1) - v_ff(r2) with enclosed mass = envelope mass (from 110 GHz continuum) plus central object mass  
  > "We can do a rough estimation of the contribution from infall, by measuring the infall velocity difference from two different radii" (Linewidths and kinetic temperature); "To compute the mass we consider that the total mass at different radii is the sum of the mass in the envelope plus the mass of the central object." (Linewidths and kinetic temperature)
   - parameter: Central object mass 0.05-0.26 Msun adopted from infall models  
  > "which are the predicted values from infall models (see (cite: Yen2015b), (cite: Evans2015), Evans et al. in prep.)" (Linewidths and kinetic temperature)
   - assumption: Maximum velocity difference along the line of sight occurs at the core center; envelope mass uses standard dust assumptions  
  > "The maximum velocity difference along the line-of-sight would occur at the core’s center." (Linewidths and kinetic temperature)
   - fitting: _not stated_
   - validation: Non-thermal linewidth compared with the free-fall broadening and found to be of the same order  
  > "the non-thermal contribution of the linewidth is of the same order as the broadening due to free-fall motions along the line of sight" (Linewidths and kinetic temperature)
8. **Estimate flux missed by the interferometer**: ALMA C18O map smoothed to the Nobeyama 45 m beam, spectrum over one beam, flux converted to brightness temperature (Rayleigh-Jeans) and compared with single-dish data; C17O missing flux then inferred to be smaller  
  > "Our C$^{18}$O map was smoothed to match the beam size of the Nobeyama telescope" (Possible origins of the observed gas motions); "transformed the flux density to brightness temperature using the Rayleigh-Jeans law" (Possible origins of the observed gas motions)
   - assumption: C17O is much more compact than C18O so its missing flux is smaller  
  > "because C$^{17}$O is expected to be much more compact than C$^{18}$O we expect the missing flux to be much less for the former" (Possible origins of the observed gas motions)
   - fitting: _not stated_
   - validation: Missing flux judged too small to produce the dip and unable to explain the velocity pattern at the systemic velocity  
  > "it can not explain the structured velocity pattern we observe in the spectral maps" (Possible origins of the observed gas motions)

## Software

- **CASA** 5.6.1-8: Calibration, continuum self-calibration and imaging  
  > "Calibration of the raw data was done using the standard script for cycle-4 ALMA data using the Common Astronomy Software Applications (CASA) version 5.6.1-8." (Observations and data reduction)
- **tCLEAN** : Final imaging of calibrated visibilities  
  > "Final images of the data were generated from the calibrated visibilities using the tCLEAN algorithm within CASA" (Observations and data reduction)
- **HfS** : Fitting hyperfine structure of C17O with multiple velocity components and deriving opacity  
  > "The spectrum at each pixel has been modeled using a program that allows to fit the hyperfine structure of spectral lines with multiple velocity components" (Modeling of the molecular line profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean radius of 3 sigma C17O emission | 860 | not stated | au | 2 | The mean radius of the 3$\sigma$ emission is 860 au |
| Peak C17O opacity at the source center (column-density estimate) | 0.77 | not stated | dimensionless | 3 | $\tau_{0}$ = 0.77, which corresponds to an opacity typical from an optically thin line |
| Integrated intensity ratio W(C17O)/W(C18O): range and mean | 0.15 to 0.50, mean 0.28 | not stated | dimensionless | 4 | with values ranging from 0.15 to 0.50 and a mean value centered at 0.28 |
| Mean average velocity of blue and red components | 8.1 and 8.6 | not stated | km/s | 5 | The mean average, velocity for the two components are 8.1 and 8.6 km s$^{-1}$ respectively. |
| Mean velocity dispersion of blue and red components | 0.7 and 0.5 | not stated | km/s | 5 | show a mean velocity dispersion for the two components of 0.7 and 0.5 km s$^{-1}$ |
| Average opacity of blue and red components from HfS | 0.464 and 0.474 | not stated | dimensionless | 5 | is found to be $\tau_{bs}$ = 0.464 and $\tau_{rs}$ = 0.474, for the blue- and red-shifted components respectively |
| Gas kinetic temperature at 100 au and 860 au | 46 and 20 | not stated | K | 6 | with values in range of T$_{k}$(100 au) = 46 K and T$_{k}$(860 au) = 20 K |
| Thermal C17O linewidth at 100 au and 860 au | 0.27 and 0.17 | not stated | km/s | 6 | (100 au) = 0.27 km s$^{-1}$ and; (860 au) = 0.17 km s$^{-1}$ |
| Observed total FWHM, blue and red components | 0.78 and 0.56 | not stated | km/s | 5 | / Observed total / 0.78 / 0.56 / |
| Non-thermal FWHM at 100 au, blue and red components | 0.73 and 0.48 | not stated | km/s | 6 | / Non-thermal (100au) / 0.73 / 0.48 / |
| Non-thermal FWHM at 860 au, blue and red components | 0.76 and 0.52 | not stated | km/s | 6 | / Non-thermal (860au) / 0.76 / 0.52 / |
| Envelope mass within 860 au and 100 au | ~0.16 and ~0.012 | not stated | Msun | 7 | $\sim$0.16 $M_\odot$ and $\sim$0.012 $M_\odot$, respectively |
| Total enclosed mass within 100 au and 860 au | 0.06-0.16 and 0.27-0.41 | not stated | Msun | 7 | the total mass enclosed within a 100 and 860 au radii are in the 0.06–0.16 $M_\odot$ and 0.27–0.41 $M_\odot$ ranges, respectively |
| Free-fall velocity difference between 100 and 860 au | 0.46 - 1.01 | not stated | km/s | 7 | is 0.46 - 1.01 km s$^{-1}$ |
| Peak single-dish-matched C18O main-beam temperature (ALMA smoothed to 16 arcsec) | 0.79 | 0.08 | K | 8 | = 0.79 $\pm$ 0.08 K |
| Fraction of single-dish C18O flux recovered by ALMA | around 14 | not stated | percent | 8 | This means that our ALMA observations are recovering around 14 $\%$ of the total flux detected with single-dish data. |

## Qualitative findings

- C17O (1-0) shows widespread double-peaked profiles; the blue component dominates in the east and the red in the west  
  > "the blue component more intense in the Eastern part of the core, while the red component is dominant in the Western part" (Results and analysis)
- C17O is optically thin, so the two peaks are two distinct velocity components rather than self-absorption  
  > "The optical depth of the C$^{17}$O emission has been estimated and found to be less than 1" (abstract)
- Non-thermal linewidths are supersonic  
  > "This means that the non-thermal contribution to the linewidth is supersonic." (Linewidths and kinetic temperature)
- Infall, possibly anisotropic along outflow cavity walls, is favoured to explain the velocity field  
  > "it is suggested that those are produced by non-isotropic accretion from the envelope into the central source along the outflow cavity walls" (abstract)

## Claim tuples

- H: Are the two C17O velocity peaks caused by optically thick self-absorption? | E: Three independent opacity estimates: column density, C17O/C18O intensity ratio and HfS hyperfine fitting | R: tau0 = 0.77; ratio 0.15-0.50 (mean 0.28) vs expected 0.25; HfS opacities 0.464 and 0.474 | F: The emission is optically thin, so the peaks trace two distinct velocity components | **supported**
- H: Could the velocity pattern come from rotation, outflow or interferometric filtering? | E: Inspect velocity gradients, compare with 12CO and outflow tracers, estimate missing flux against single-dish data | R: No clear equatorial velocity gradient; C17O morphology differs from outflow tracers; missing flux cannot explain the structured pattern | F: Rotation, outflow and filtering are discarded as the main origin | **supported**
- H: Are the linewidths of the two components compatible with infall? | E: Compare non-thermal linewidths with the free-fall velocity difference between 100 and 860 au | R: Non-thermal FWHM 0.48-0.76 km/s vs free-fall difference 0.46-1.01 km/s | F: The linewidths are of the same order as free-fall broadening, so infall is possible | **partially**
- H: Can isotropic inside-out symmetric collapse explain the observed profiles? | E: Interpret the optically thin double-peaked profiles and the velocity maps along the outflow cavity walls | R: Highest velocities lie along the northern cavity walls at reverse velocities relative to the outflow; profiles are not produced by self-absorption | F: Symmetric inside-out collapse cannot explain them; non-isotropic accretion along the cavity walls is suggested | **partially**

## Reasoning

- Why this data: C17O is a rare isotopologue that traces dense envelope gas and is not expected in outflow cavities  
  > "C$^{17}$O is a rare isotopologue which is known to trace dense envelope gas and is not expected to be detected in more tenuous outflow cavities." (Possible origins of the observed gas motions)
- Why this method: Because C17O is expected to be optically thin, a two-velocity-component fit was tried instead of a self-absorbed single component  
  > "Because the C$^{17}$O (1-0) emission is expected to be optically thin, it was attempted to model the double-peaked profiles with two velocity components, one blue- and another red-shifted." (Modeling of the molecular line profiles)
- Alternative: Dip caused by interferometric filtering: discarded  
  > "The possibility of the dip being caused by interferometric filtering is discarded since the recovered emission size is of the order of the Largest Recoverable Scale" (Results and analysis)
- Alternative: Organized core rotation: not supported by the data  
  > "A possible cause for observing blueshifted and redshifted gas motions in protostellar envelopes could be organized core rotation." (Possible origins of the observed gas motions)
- Alternative: Outflow as the origin: cannot produce the pattern alone  
  > "Therefore, the kinematic pattern observed in our C$^{17}$O maps cannot be produced by outflow alone" (Possible origins of the observed gas motions)
- How they decided it was enough: _not stated_
- Limitation (authors): No clear velocity gradient along the cavity walls could be resolved; better spatial resolution needed  
  > "no clear velocity gradient could be resolved in the current observations: additional observations with better spatial resolution may allow to test further this hypothesis" (Possible origins of the observed gas motions)
- Limitation (authors): Outflow contamination cannot be completely excluded  
  > "Although some contamination by the gas from the outflow cannot be completely ruled out" (Possible origins of the observed gas motions)
- Limitation (authors): ALMA data may miss flux; only about 14 percent of C18O single-dish flux recovered  
  > "We also note that while our observation might be missing flux" (Possible origins of the observed gas motions)
- Limitation (authors): Origin of C17O line broadening in the north and south-west is unknown  
  > "The origin of this broadening is unknown" (Intensity ratio)
- Caveat (inferred, ours): Infall interpretation rests on a rough linewidth comparison with large mass uncertainties; no kinematic model is fitted to the cubes
- Caveat (inferred, ours): The opacity estimate uses a standard abundance and an H2 column density at 3600 au, not at the resolved radii
- Caveat (inferred, ours): Missing flux of about 14 percent for C18O and an extrapolated 30 percent for C17O is not measured directly
- Caveat (inferred, ours): Two-component HfS fits are not tested against alternative models such as a single optically thick component with a dip
- Caveat (inferred, ours): The 12CO RMS value in Table 1 appears wrong, and image weighting (robust = 2) differs from file names suggesting robust 0.5

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA delivered product images used only for preliminary checks  
  > "Preliminary analysis of the data was done with the product images delivered by ALMA to check if emission was detected and to check the shape of the line profiles." (Observations and data reduction)
- Missing: Self-calibration, continuum definition and continuum subtraction settings
- Missing: tclean parameters other than robust (masks, thresholds, cell and image size, spectral grid)
- Missing: HfS initial guesses and per-pixel acceptance criteria
- Missing: Dust and gas assumptions for the envelope mass; 'Evans et al. in prep.' values
- Missing: Corrected 12CO RMS and smoothing details
- Data volume (inferred): About 4 execution blocks (C40-1, C40-2, C40-4, C40-5), likely tens of GB raw and several GB after splitting the line spws
- Score (inferred): 3/5, Project code, lines, configurations, robust values and CASA version are given and numbers are clear, but self-calibration, continuum subtraction, clean settings and HfS setup are missing.
- Rediscovery candidate: yes, Cycle 4 data from project 2016.1.01552.S (public status not stated in the paper but long past the proprietary period); the recipe is short and the main results (opacities, ratio, linewidths) are numeric.

## Links

- Method: (cite: Estalella2017) (HfS program for fitting hyperfine structure used for the two-component fits)
- Method: (cite: Jorgensen2007) (Equation 4 used for envelope mass from continuum emission)
- Method: (cite: Shirley2011) (Dust temperature formula used for gas kinetic temperature)
- Method: (cite: Jansen1995) (Opacity formula from column density)
- Companion: (cite: Maury2018) (High resolution B335 dust continuum and magnetic field from related ALMA data; continuum peak position)
- Companion: (cite: Evans2015) (Infall models and temperature profile for B335)
- Companion: (cite: Yen2015b) (Earlier ALMA C18O observations of B335 and infall modelling)
- Companion: (cite: Saito1999) (Nobeyama 45 m C18O (1-0) data used for the missing flux estimate)
- Related: 2016.1.01552.S (PI A. Maury)

## Checks

```json
{
 "quotes": 127,
 "quotes_ok": 127,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 82,
  "rate": 0.745
 },
 "evidence_ok": true
}
```
