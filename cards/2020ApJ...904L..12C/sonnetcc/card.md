# Detection of Dynamical Instability in Titan's Thermospheric Jet

`2020ApJ...904L..12C` | The Astrophysical Journal Letters 2020 | first author: Cordiner, M. A. | arXiv: 2106.01911 | DOI: 10.3847/2041-8213/abc688

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Is Titan's thermospheric equatorial jet temporally variable? Map the 3D wind field with ALMA in May 2017 and compare with a reanalysis of the August 2016 data  
  > "We obtained spectrally and spatially resolved ALMA observations in May 2017 to map Titan’s 3D global wind field and compare our results with a reanalysis of the August 2016 data." (abstract); "This has enabled the first study of temporal variability in Titan’s thermospheric jet, leading to new insights regarding its (in)stability and possible driving mechanisms." (Introduction)
- Target **Titan**: coordinates _not stated_; z/distance Geocentric distance 9.75 au (2016), 9.21 au (2017)  
  > "as projected in the plane of the sky at $\Delta=9.75$ au in 2016 and $\Delta=9.21$ au in 2017" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.A.00014.S, 2015.1.01023.S
- bands: Band 7  
  > "The correlator was configured to observe several Band 7 frequency windows in the range 349–364 GHz." (Observations)
- frequencies and spectral setup: 2017: several Band 7 windows 349-364 GHz; HNC J=4-3 and HC3N J=40-39 at 244 kHz (0.2 km/s); CH3CN J=19-18 at 488 kHz (0.4 km/s). 2016: HNC and CH3CN at 122 kHz (CH3CN also 488 kHz); HC3N J=39-38 at 122 kHz  
  > "The HNC ($J=4-3$) and HC$_3$N ($J=40-39$) transitions were observed at a spectral resolution of $\Delta{\nu}=244$ kHz (0.2 km s$^{-1}$), while the CH$_3$CN ($J=19-18$) band was observed at $\Delta{\nu}=488$ kHz (0.4 km s$^{-1}$)" (Observations); "covering HNC ($J=4-3$, with $\Delta{\nu}=122$ kHz) and CH$_3$CN ($J=19-18$, with $\Delta{\nu}=122$ kHz and 488 kHz)" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m main array, 46 antennas (2017)  
  > "Interferometric observations of Titan were carried out using 46 antennas of the main (12 m) array on 2017-05-08 and 2017-05-16" (Observations)
- configurations: moderately extended (2017)  
  > "The antenna configuration was moderately extended" (Observations)
- baselines: _not stated_
- angular resolution: ≈0.24 x 0.19 arcsec (natural weighting, 2017)  
  > "resulting in a spatial resolution of $\approx0.24\times0.19''$ (using natural visibility weighting)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS ≈2 mJy/beam/MHz (2017)  
  > "leading to RMS noise levels $\approx2$ mJy beam$^{-1}$ MHz$^{-1}$" (Observations)
- time on source: 138 min (2017)  
  > "The total on-source observing time was 138 min" (Observations)
- observing dates: 2017-05-08 and 2017-05-16; 2016-08-18 (HNC, CH3CN) and 2016-08-19 (HC3N J=39-38)  
  > "Interferometric observations of Titan were carried out using 46 antennas of the main (12 m) array on 2017-05-08 and 2017-05-16" (Observations); "obtained on 2016-08-19 as part of the same program" (Observations)
- pi or archival as stated: 2017 data: PI M. Cordiner (2016.A.00014.S); 2016 data: archival, PI M. Gurwell (2015.1.01023.S)  
  > "as part of ALMA program 2016.A.00014.S (PI: M. Cordiner)" (Observations); "Raw data were obtained from the ALMA archive (project 2015.1.01023.S; PI: M. Gurwell)" (Observations)
- Line: HNC J=4-3 (not stated)
- Line: HC3N J=40-39 (2017); J=39-38 (2016) (354,697 MHz (J=39-38 only))
- Line: CH3CN J=19-18 (not stated)
- External data: Mean emission altitudes of the limb emission: CH3CN 345 km, HC3N 710 km, HNC 990 km  
  > "CH$_3$CN emission is from a mean altitude of $\bar{z}=345$ km, HC$_3$N from $\bar{z}=710$ km and HNC from $\bar{z}=990$ km" (Results) [from (cite: lel19)]
- External data: Molecular abundance and temperature in each model cell, from limb retrievals  
  > "an abundance, and a temperature (the latter two quantities were obtained from the limb retrievals of (cite: cor19))" (Wind Velocity Retrievals) [from (cite: cor19)]
- External data: Molecular line rest frequencies (systematic uncertainty 0.3 m/s CH3CN, 2-8 m/s HC3N, 7 m/s HNC)  
  > "0.3 m $\rm{s}^{-1}$ for CH$_3$CN, 2–8 m $\rm{s}^{-1}$ for HC$_3$N and 7 m $\rm{s}^{-1}$ for HNC (cite: pic98; mul01)" (Results) [from (cite: pic98; mul01)]

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

- task: tclean in CASA 5.6  
  > "algorithm in CASA 5.6 (cite: emo19)" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "(using natural visibility weighting)" (Observations)
- uv taper: _not stated_
- cell size: 0.025 arcsec  
  > "The image pixel size was set to $0.025''$, with a flux threshold of twice the RMS noise per channel, and a deconvolution mask diameter of $1.3''$, encircling the entirety of the detected flux." (Observations)
- image size: _not stated_
- masking: deconvolution mask diameter 1.3 arcsec; threshold twice the RMS noise per channel  
  > "The image pixel size was set to $0.025''$, with a flux threshold of twice the RMS noise per channel, and a deconvolution mask diameter of $1.3''$, encircling the entirety of the detected flux." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: low-order polynomial fits to line-free spectral regions adjacent to the lines  
  > "The raw observations were first continuum-subtracted using low-order polynomial fits to the line-free spectral regions adjacent to our lines of interest." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 2016 and 2017 cubes convolved to common circular beams in km at Titan  
  > "both datasets were convolved to common circular beam dimensions ($\theta_{km}$), as projected in the plane of the sky at $\Delta=9.75$ au in 2016 and $\Delta=9.21$ au in 2017" (Observations)
- final beam: 1670 km (CH3CN), 1570 km (HC3N), 1600 km (HNC)  
  > "resulting in $\theta_{km}=1670$ km for CH$_3$CN, $\theta_{km}=1570$ km for HC$_3$N and $\theta_{km}=1600$ km for HNC" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Observation details of the 2017 data  
  > "For additional details on these observations see (cite: cor19)." (Observations) [from (cite: cor19)]
- Doppler-mapping method for radial velocities  
  > "We followed the method of (cite: lel19) to determine radial velocities (along the line of sight) for each gas as a function of spatial coordinate." (Doppler Mapping) [from (cite: lel19)]
- Monte Carlo velocity uncertainty approach  
  > "derived using a similar Monte Carlo approach to (cite: lel19)" (Doppler Mapping) [from (cite: lel19)]
- Deconvolution / wind modeling procedure  
  > "We therefore performed a deconvolution/wind modeling procedure similar to (cite: lel19)" (Deconvolved Wind Models) [from (cite: lel19)]
- 3D-grid wind retrieval method  
  > "Our method is based on (cite: lel19) and involved construction of a 3D grid of (100 km wide) cubic cells, covering Titan’s entire atmosphere." (Wind Velocity Retrievals) [from (cite: lel19)]
- Radiative transfer equation integrated along the line of sight  
  > "calculated by integrating the equation of radiative transfer (cite: van07) along the line of sight" (Wind Velocity Retrievals) [from (cite: van07)]
- Line-wing treatment (pressure-broadened Lorentzian wings for HC3N and CH3CN)  
  > "As shown by (cite: cor19) and (cite: lel19), pressure-broadened Lorentzian line wings are apparent for HC$_3$N and CH$_3$CN" (Doppler Mapping) [from (cite: cor19; lel19)]

### Not stated but needed to reproduce (our reading)

- Calibration route (pipeline vs manual), CASA version used for calibration, and the flux, bandpass and phase calibrators
- How Titan's ephemeris motion was handled in calibration and imaging (ephemeris table, spectral frame, tclean phasecenter/specmode settings)
- Execution blocks / scheduling blocks used for each epoch and any data flagged
- Order of the polynomial and the exact line-free channel/frequency ranges for continuum subtraction
- tclean settings not given: niter, gridder, image size, deconvolver, primary-beam correction and spectral regridding of channels
- Definition of the signal-to-noise used for the >10 mask and initial guesses and bounds for the Gaussian line fits
- Rest frequencies adopted for each transition and for the three CH3CN K-components
- Abundance and temperature profiles from the cor19 limb retrievals and the lel19 wind contribution functions needed for the 3D model
- Initial parameters, weights and convergence criteria of the MPFIT wind-profile fit; how the line-core Gaussian offsets map to the model
- Flux scale and absolute calibration uncertainties

## Analysis recipe

1. **continuum subtraction and imaging**: Continuum-subtract with low-order polynomials, then image with tclean into cubes in Titan's rest frame  
  > "The raw observations were first continuum-subtracted using low-order polynomial fits to the line-free spectral regions adjacent to our lines of interest." (Observations); "algorithm in CASA 5.6 (cite: emo19)" (Observations)
   - software: CASA, tclean
   - parameter: pixel size 0.025 arcsec; threshold twice the RMS noise per channel; mask diameter 1.3 arcsec  
  > "The image pixel size was set to $0.025''$, with a flux threshold of twice the RMS noise per channel, and a deconvolution mask diameter of $1.3''$, encircling the entirety of the detected flux." (Observations)
   - parameter: cubes in the rest frame of Titan's center-of-mass  
  > "so the resulting image cubes are in the rest frame of Titan’s center-of-mass" (Observations)
   - fitting: _not stated_
   - validation: Rest frequency scale checked: Doppler shifts close to zero along sight lines through Titan's polar axis  
  > "Reliability of the rest frequency scale was established based on the observation that the emission line Doppler shifts were typically close to zero (within the uncertainties) along the lines of sight intersecting Titan’s polar axis." (Observations)
2. **match 2016 and 2017 resolution**: Convolve both epochs to common circular beams defined in km at Titan  
  > "both datasets were convolved to common circular beam dimensions ($\theta_{km}$), as projected in the plane of the sky at $\Delta=9.75$ au in 2016 and $\Delta=9.21$ au in 2017" (Observations)
   - parameter: 1670 km (CH3CN), 1570 km (HC3N), 1600 km (HNC)  
  > "resulting in $\theta_{km}=1670$ km for CH$_3$CN, $\theta_{km}=1570$ km for HC$_3$N and $\theta_{km}=1600$ km for HNC" (Observations)
   - assumption: Titan geocentric distance 9.75 au (2016) and 9.21 au (2017)  
  > "as projected in the plane of the sky at $\Delta=9.75$ au in 2016 and $\Delta=9.21$ au in 2017" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **line-of-sight Doppler velocity maps**: Extract a spectrum per pixel, fit emission lines with Gaussians for the Doppler shift; for HC3N and CH3CN fit 3 MHz windows around the line cores with a constant offset; average three CH3CN lines  
  > "This involved extracting individual spectra from the 2016 and 2017 ALMA image cubes and fitting the emission lines with Gaussians to determine their Doppler shifts." (Doppler Mapping); "the fits were restricted to narrow (3 MHz wide) spectral regions, centered on each of the line cores." (Doppler Mapping)
   - software: atmWindMapGaussFit
   - parameter: constant additive intensity offset to remove the pseudo-continuum from broad line wings  
  > "A constant (additive) intensity offset was also accounted for, to remove the pseudo-continuum created by the broad emission line wings" (Doppler Mapping)
   - parameter: maps masked to total signal-to-noise > 10  
  > "The maps have been masked to only show the circular/annular regions where the total signal-to-noise ratio was $>10$." (Results)
   - assumption: Limb emission optically thin and thermally broadened, so the Gaussian Doppler shift gives the line-of-sight wind  
  > "Since the observed limb emission is predominantly optically thin, and originates from sufficiently high altitudes that thermal broadening dominates the line core shapes" (Doppler Mapping)
   - fitting: Gaussian line fits; 300 noisy synthetic datasets re-fitted, 68th percentiles taken as 1 sigma  
  > "re-fitting the Gaussian line model to a large set of (300) noisy, synthetic datasets." (Doppler Mapping); "The $\pm68^{th}$ percentiles of the resulting parameter distributions are interpreted as $1\sigma$ errors." (Doppler Mapping)
   - validation: 2016 maps closely consistent with Lellouch et al. results  
  > "for 2016, our results are closely consistent with those obtained by (cite: lel19)" (Results)
4. **deconvolve to intrinsic zonal wind profiles**: 3D grid of 100 km cubic cells with wind, abundance, temperature; radiative transfer along the line of sight, convolve to beam, centroid velocity per pixel, fit Gaussian v(latitude) profile with vmax, FWHM, phi0  
  > "construction of a 3D grid of (100 km wide) cubic cells, covering Titan’s entire atmosphere." (Wind Velocity Retrievals); "the convolved image cube was integrated along the spectral axis to determine the centroid velocity of each pixel." (Wind Velocity Retrievals)
   - software: atmWindMapGaussFit, MPFIT
   - parameter: three free parameters: peak wind speed vmax, Gaussian FWHM, latitudinal offset phi0  
  > "(1) the peak wind speed $v_{max}$, (2) the Gaussian FWHM, and (3) a latitudinal offset ($\phi_0$)" (Deconvolved Wind Models)
   - assumption: Titan obliquity of 26 degrees toward the observer  
  > "Titan’s obliquity (26$^{\circ}$ toward the observer)" (Deconvolved Wind Models)
   - assumption: v(latitude) profile does not vary with height for each molecule  
  > "The derived ${v}(\phi)$ profile for each molecule is assumed not to vary with height" (Wind Velocity Retrievals)
   - assumption: 1D Gaussian latitudinal profile  
  > "we decided on a Gaussian parameterization, which is able to reproduce the main features in our observed velocity maps, with a minimum number of free parameters" (Deconvolved Wind Models)
   - fitting: Least-squares (sum of squared residuals) minimization with MPFIT; 1 sigma from the MPFIT covariance matrix; likelihood/priors not stated  
  > "The sum of squares of the residuals (model minus observations) was minimized using the MPFIT algorithm (cite: mar12)" (Wind Velocity Retrievals); "The ($1\sigma$) uncertainties on each parameter were obtained from the MPFIT covariance matrix." (Wind Velocity Retrievals)
   - validation: Synthetic maps compared with observed maps and with 2016 maps of Lellouch et al.  
  > "A good match to the observations (Figure 2) is evident in each case" (Wind Velocity Retrievals); "for 2016, our synthetic wind maps compare well with those in Supplementary Fig. 7 of (cite: lel19)" (Wind Velocity Retrievals)
5. **test jet instability**: Apply the Rayleigh-Kuo criterion (beta - Uyy < 0) to the fitted HNC latitudinal wind profile  
  > "for barotropic instability via the Rayleigh-Kuo criterion ($\beta-U_{yy}<0$), which compares the meridional gradient of the Coriolis force ($\beta$) to the second derivative of the zonal wind as a function of latitude ($U_{yy}$)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: imaging and cleaning of the ALMA data  
  > "algorithm in CASA 5.6 (cite: emo19)" (Observations)
- **tclean** : imaging and deconvolution of the continuum-subtracted visibilities  
  > "The data were then imaged and cleaned (deconvolved) using the" (Observations)
- **atmWindMapGaussFit** : wind speed profile retrievals (code on Zenodo)  
  > "atmWindMapGaussFit (cite: zen20c)" (Software); "The code used to perform these wind speed profile retrievals is available for download from zenodo.org (cite: zen20c)." (Wind Velocity Retrievals)
- **MPFIT** : least-squares minimization of the wind model residuals  
  > "The sum of squares of the residuals (model minus observations) was minimized using the MPFIT algorithm (cite: mar12)" (Wind Velocity Retrievals)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HNC mean absolute Doppler shift 2016 | 265 | ±11 | m/s | 3 | resulting in a mean absolute Doppler shift of $265\pm11$ m $\rm{s}^{-1}$ in 2016 and $142\pm6$ m $\rm{s}^{-1}$ in 2017 (averaged over the east and west limbs) |
| HNC mean absolute Doppler shift 2017 | 142 | ±6 | m/s | 3 | resulting in a mean absolute Doppler shift of $265\pm11$ m $\rm{s}^{-1}$ in 2016 and $142\pm6$ m $\rm{s}^{-1}$ in 2017 (averaged over the east and west limbs) |
| HNC equatorial wind speed, West, 2017 | -157 | ±5 | m/s | 3 | the equatorial wind speed was slightly faster in the West ($-157\pm5$ m $\rm{s}^{-1}$) than the East ($129\pm6$ m $\rm{s}^{-1}$) |
| HNC equatorial wind speed, East, 2017 | 129 | ±6 | m/s | 3 | the equatorial wind speed was slightly faster in the West ($-157\pm5$ m $\rm{s}^{-1}$) than the East ($129\pm6$ m $\rm{s}^{-1}$) |
| CH3CN vmax 2016 (z=345 km) | 254 | ±4 | m/s | 4 | $254\pm4$ / $-13\pm1$ / $88\pm3$ |
| CH3CN vmax 2017 (z=345 km) | 185 | ±3 | m/s | 4 | $185\pm3$ / $-11\pm1$ / $91\pm3$ |
| HC3N vmax 2016 (z=710 km) | 341 | ±2 | m/s | 4 | $341\pm2$ / $-2\pm1$ / $91\pm1$ |
| HC3N vmax 2017 (z=710 km) | 225 | ±2 | m/s | 4 | $225\pm2$ / $-1\pm1$ / $93\pm2$ |
| HNC vmax 2016 (z=990 km) | 373 | ±6 | m/s | 4 | $373\pm6$ / $0\pm1$ / $70\pm2$ |
| HNC vmax 2017 (z=990 km) | 196 | ±2 | m/s | 4 | $196\pm2$ / $3\pm1$ / $101\pm2$ |
| CH3CN Gaussian FWHM 2016 / 2017 | 88 / 91 | ±3 / ±3 | degrees | 4 | $254\pm4$ / $-13\pm1$ / $88\pm3$; $185\pm3$ / $-11\pm1$ / $91\pm3$ |
| HC3N Gaussian FWHM 2016 / 2017 | 91 / 93 | ±1 / ±2 | degrees | 4 | $341\pm2$ / $-2\pm1$ / $91\pm1$; $225\pm2$ / $-1\pm1$ / $93\pm2$ |
| HNC Gaussian FWHM 2016 / 2017 | 70 / 101 | ±2 / ±2 | degrees | 4 | $373\pm6$ / $0\pm1$ / $70\pm2$; $196\pm2$ / $3\pm1$ / $101\pm2$ |
| Drop in peak deconvolved zonal wind speed, CH3CN | 27 | ±1 | % | 4 | the peak deconvolved zonal wind speed ($v_{max}$) dropped by $27\pm1$% during the 9-month period |
| Drop in peak deconvolved zonal wind speed, HC3N | 34 | ±1 | % | 4 | A larger drop was observed for HC$_3$N ($34\pm1$%) and larger-still for HNC ($47\pm1$%). |
| Drop in peak deconvolved zonal wind speed, HNC | 47 | ±1 | % | 4 | A larger drop was observed for HC$_3$N ($34\pm1$%) and larger-still for HNC ($47\pm1$%). |
| Average velocity uncertainty in masked regions, HNC 2016 / 2017 | 19.6 / 7.5 | not stated | m/s | 3 | HNC (2016): 19.6 m $\rm{s}^{-1}$, HNC (2017): 7.5 m $\rm{s}^{-1}$ |

## Qualitative findings

- Wind variability grows with altitude: stronger temporal change from CH3CN to HC3N to HNC  
  > "Thus, we see a significant trend for stronger temporal variability with increasing altitude above Titan’s stratosphere." (Discussion)
- CH3CN winds peak 11-13 degrees south of the equator at both epochs  
  > "the lower-altitude zonal winds revealed by CH$_3$CN reach a peak velocity $11^{\circ}$–$13^{\circ}$ south of the equator (at both epochs)" (Discussion)
- In 2016 wind speed increased with altitude, much less apparent in 2017  
  > "In 2016, however, there was a clear trend for increasing equatorial zonal wind speed with altitude, which is much less apparent in the 2017 data." (Results)

## Claim tuples

- H: Titan's thermospheric equatorial jet is temporally variable | E: Doppler maps and Gaussian wind-profile fits for CH3CN, HC3N and HNC in August 2016 (reanalysed) and May 2017 | R: Peak deconvolved zonal wind speed dropped 27%, 34% and 47% for CH3CN, HC3N and HNC | F: A large, altitude-dependent slowing of the equatorial jet occurred over 9 months | **supported**
- H: The jet's latitudinal shape changed along with its speed | E: Compare fitted Gaussian FWHM and latitudinal offset between epochs | R: HNC FWHM went from 70 to 101 degrees; CH3CN and HC3N shapes unchanged | F: The thermospheric (HNC) jet lost latitudinal confinement | **supported**
- H: The 2016 HNC jet was dynamically unstable | E: Rayleigh-Kuo criterion applied to the fitted HNC latitudinal wind profile | R: beta - Uyy << 0 for the 2016 profile, still < 0 at high latitudes in 2017 | F: Dynamical instability explains the slowing and broadening | **supported**
- H: Gravity-wave forcing from the middle atmosphere drives the thermospheric jet | E: Qualitative comparison with Cassini CIRS and circulation results from other work | R: Reduced middle-atmosphere wind shear in 2016-2017 coincides with the slower jet | F: Loss of gravity-wave forcing may have slowed the jet; the cause is speculative | **partially**

## Reasoning

- Why this data: Re-analyse the 2016 archive data with the same pipeline as 2017 for consistency  
  > "To ensure consistency of the data analysis methodology between 2016 and 2017, we re-analyzed the CH$_3$CN, HC$_3$N and HNC data observed by (cite: lel19) on 2016-08-18." (Observations)
- Why this method: A Gaussian v(latitude) profile reproduces the main features with few free parameters  
  > "we decided on a Gaussian parameterization, which is able to reproduce the main features in our observed velocity maps, with a minimum number of free parameters" (Deconvolved Wind Models)
- Alternative: 2016 HC3N J=40-39 data rejected for low spectral resolution; J=39-38 used instead  
  > "but at a lower spectral resolution ($\Delta{\nu}=977$ kHz, insufficient for accurate radial velocity measurements), so we instead used observations of the HC$_3$N ($J=39-38$) line" (Observations)
- Alternative: More complex latitudinal/longitudinal wind forms considered but not used  
  > "Although more complex functional forms can be envisaged (allowing for longitudinal as well as additional latitudinal variability)" (Deconvolved Wind Models)
- How they decided it was enough: _not stated_
- Limitation (authors): Wind-field map fidelity limited by coarse altitude sampling and altitude smearing  
  > "The fidelity of these maps is limited by (1) the coarse altitude sampling of our data, (2) smearing due to the broad range of altitudes" (Discussion)
- Limitation (authors): Timescale of the jet variability unknown due to sparse temporal sampling  
  > "Due to the incomplete temporal sampling, however, the actual timescale of the thermospheric jet’s variability remains unknown." (Discussion)
- Limitation (authors): Retrieved profiles may be biased by emission from altitudes other than the mean contribution altitude  
  > "the possibility that the retrieved velocity profiles could be biased by emission from altitudes different from the mean wind contribution function altitude should be considered" (Wind Velocity Retrievals)
- Caveat (inferred, ours): Only two epochs, so seasonal versus intermittent variability cannot be separated
- Caveat (inferred, ours): Instability conclusion rests on a 1D Gaussian fit with a single altitude per molecule; no formal test of the criterion's sensitivity to fit uncertainty
- Caveat (inferred, ours): Flux calibration and absolute velocity systematics beyond rest-frequency errors are not discussed
- Caveat (inferred, ours): The 2016 and 2017 data differ in spectral resolution and line sets (HC3N J=39-38 vs 40-39)

## Reproducibility

- Data public (paper): 2016 data obtained from the ALMA archive; public status of 2017 program not stated  
  > "Raw data were obtained from the ALMA archive (project 2015.1.01023.S; PI: M. Gurwell)" (Observations)
- Products in archive: _not stated_
- Code: Wind retrieval code available on Zenodo (atmWindMapGaussFit)  
  > "The code used to perform these wind speed profile retrievals is available for download from zenodo.org (cite: zen20c)." (Wind Velocity Retrievals)
- Missing: Calibration details and calibrator list
- Missing: Line-free channel ranges and polynomial order for continuum subtraction
- Missing: Full tclean parameter set and Titan ephemeris handling
- Missing: Limb-retrieval abundance and temperature profiles from cor19 and contribution functions from lel19
- Missing: Fit initial conditions and rest frequencies per transition
- Data volume (inferred): Likely tens to a few hundred GB of raw data for the two epochs (46 antennas, high spectral resolution Band 7 windows)
- Score (inferred): 3/5, Archive data for 2016, released fitting code and a numeric results table exist, but calibration, tclean and line-free settings are not given and key inputs come from cor19 and lel19.
- Rediscovery candidate: yes, 2016 data are archival, code is on Zenodo and the main results (vmax, FWHM) are tabulated; 2017 data public status is not stated in the paper.

## Links

- Method: (cite: lel19) (Doppler mapping, Monte Carlo errors and wind deconvolution method followed)
- Method: (cite: emo19) (CASA reference for imaging)
- Method: (cite: mar12) (MPFIT least-squares algorithm)
- Method: (cite: van07) (radiative transfer equation used in the wind model)
- Companion: (cite: lel19) (Discovery of the thermospheric jet from the 2016 ALMA data)
- Companion: (cite: cor19) (Observation details and limb retrievals of abundance and temperature for the 2017 data)
- Related: 2016.A.00014.S
- Related: 2015.1.01023.S

## Checks

```json
{
 "quotes": 108,
 "quotes_ok": 108,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 65,
  "rate": 0.707
 },
 "evidence_ok": true
}
```
