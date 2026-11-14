# Edge-On Disk Study (EODS): I. Thermal structure of the Flying Saucer disk

`2025A&A...700L...5G` | Astronomy and Astrophysics 2025 | first author: Guilloteau, S. | arXiv: 2507.03716 | DOI: 10.1051/0004-6361/202554853

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Measure the dust and CO temperature profiles in the edge-on Flying Saucer disk.  
  > "We attempted an accurate measurement of the dust and CO temperature profile in the edge-on disk of the Flying Saucer." (abstract)
- Target **Flying Saucer**: coordinates R.A. 16:28:13.6979; Declination -24:31:39.491; Epoch 2016.0  
  > "All observations were then registered to Epoch 2016.0 using the derived proper motion, the nominal position of the source being then R.A. 16:28:13.6979 and Declination -24:31:39.491." (Proper motions:); "Since the Flying Saucer appears in front of molecular clouds, we adopt a distance of 120 pc in this work." (Proper motions:); "The distance of the Flying Saucer is unfortunately not known." (Proper motions:); z/distance 120 pc  
  > "All observations were then registered to Epoch 2016.0 using the derived proper motion, the nominal position of the source being then R.A. 16:28:13.6979 and Declination -24:31:39.491." (Proper motions:); "Since the Flying Saucer appears in front of molecular clouds, we adopt a distance of 120 pc in this work." (Proper motions:); "The distance of the Flying Saucer is unfortunately not known." (Proper motions:); distance from Adopted because the Flying Saucer appears in front of molecular clouds; its distance is not known.  
  > "All observations were then registered to Epoch 2016.0 using the derived proper motion, the nominal position of the source being then R.A. 16:28:13.6979 and Declination -24:31:39.491." (Proper motions:); "Since the Flying Saucer appears in front of molecular clouds, we adopt a distance of 120 pc in this work." (Proper motions:); "The distance of the Flying Saucer is unfortunately not known." (Proper motions:)

## Data provenance

- ALMA projects: 2023.1.00907.S, 2013.1.00387.S, 2013.2.00163.S, 2013.1.00163.S
- bands: Band 6 and Band 7  
  > "It covers two spectral setups, one in Band 6 and one in Band 7" (Observations and Imaging)
- frequencies and spectral setup: Continuum at 230 and 345 GHz; spectral resolutions 40 m/s to 0.2 km/s depending on line; final CO resolution 0.23 km s−1.  
  > "We fit simultaneously the 230 and 345 GHz data" (Dust temperature from disk model fitting); "spectral resolutions ranging from 40 m/s to 0.2 km/s, depending on the spectral line." (Observations and Imaging); "the noise level is $\sim 0.1$ K at 0.23 km s$^{-1}$ spectral resolution." (Spectral and continuum imaging:)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Two configurations in each of Band 6 and Band 7; compact and extended configurations.  
  > "The two configurations observed in each of Band 6 and Band 7 gave very consistent flux measurements" (Flux calibration:); "Self-calibration using the continuum data was performed on the most compact configurations, but not for the most extended ones" (Proper motions:)
- baselines: _not stated_
- angular resolution: New observations as high as 0.18 arcsec; archival continuum about 0.5 arcsec.  
  > "at a spatial resolution as high as 0.18$''$" (Observations and Imaging); "that offered continuum images at slightly different frequencies but with lower angular resolution, about $0.5''$" (Observations and Imaging)
- max recoverable scale: _not stated_
- sensitivity: CO: ~0.1 K at 0.23 km s−1; continuum dynamic range about 60, actual noise 1.5 to 2 times thermal noise.  
  > "the noise level is $\sim 0.1$ K at 0.23 km s$^{-1}$ spectral resolution." (Spectral and continuum imaging:); "The continuum data is however dynamic range limited, with actual noise level 1.5 to 2 times larger than the thermal noise, and dynamic range about 60 at high resolution." (Spectral and continuum imaging:)
- time on source: _not stated_
- observing dates: New project: 2024; older observations: May 2015.  
  > "The ALMA project 2023.1.00907.S was observed in 2024." (Observations and Imaging); "the older observations from May 2015 (2013.1.00387.S and 2013.2.00163.S)" (Flux calibration:)
- pi or archival as stated: Archival: 2013.1.00387.S, P.I. S.Guilloteau; 2013.2.00163.S, P.I. M.Simon.  
  > "We also used archival data from Projects 2013.1.00387.S (P.I. S.Guilloteau) and ALMA 2013.2.00163.S (P.I. M.Simon)" (Observations and Imaging)
- Line: 12CO 2-1 (not stated)
- Other facility **IRAM 30-m telescope**: Velocity-dependent brightness of the extended CO background.  
  > "the dust disk is in front of an extended CO cloud whose apparent brightness, as measured by the IRAM 30-m telescope" (The shadow method for dust)
- Other facility **GAIA**: Nearby-star proper-motion comparison and distances informing the adopted Flying Saucer distance.  
  > "are consistent with those derived for stars close to the Flying Saucer in $\rho$ Oph (Elias 2-27, YLW 58, and YLW 18) using GAIA (cite: Gaia_DR3)." (Proper motions:); "From GAIA, Elias 2-27 is at 110 pc, while YLW 58 and 18 lie at 135 and 137 pc respectively." (Proper motions:)
- External data: 30-m CO spectrum used as the velocity-dependent ray-tracing background.  
  > "using the 30-m CO spectrum from (cite: Guilloteau+2016), shown in Fig.[2](#fig:midplane), as a background for ray-tracing as a function of velocities." (Gas temperature from CO disk model fitting) [from (cite: Guilloteau+2016)]
- External data: GAIA proper motions of Elias 2-27, YLW 58 and YLW 18; distances of 110, 135 and 137 pc respectively.  
  > "are consistent with those derived for stars close to the Flying Saucer in $\rho$ Oph (Elias 2-27, YLW 58, and YLW 18) using GAIA (cite: Gaia_DR3)." (Proper motions:); "From GAIA, Elias 2-27 is at 110 pc, while YLW 58 and 18 lie at 135 and 137 pc respectively." (Proper motions:) [from (cite: Gaia_DR3)]
- External data: NIR images indicating a flared morphology consistent with a flaring index of 1.25.  
  > "Furthermore, the NIR images from (cite: Grosso+2003) indicate a flared morphology consistent with a flaring index of 1.25." (Dust Settling) [from (cite: Grosso+2003)]
- External data: CO freeze-out temperature on pure ice used to interpret the depletion boundary.  
  > "This is in good agreement with the freeze out temperature of CO on pure ice (cite: Bisschop+2006; Minissale+2022)" (Gas disk and CO depletion) [from (cite: Bisschop+2006; Minissale+2022)]
- External data: CO-to-CO2 conversion on grains could raise the apparent freeze-out temperature up to 35 K.  
  > "It seems to exclude significant CO to CO$_2$ conversion on grains, that could raise the apparent freeze-out temperature up to 35 K (cite: Reboussin+2015; Bosman+2018; Ruaud+2022)." (Gas disk and CO depletion) [from (cite: Reboussin+2015; Bosman+2018; Ruaud+2022)]
- External data: HD 163296 mid-plane temperature of 17 K from optically thick CO, used for comparison.  
  > "(cite: Dullemond+2020) measured a mid-plane temperature of 17 K in HD 163296 (based on optically thick CO)" (Gas disk and CO depletion) [from (cite: Dullemond+2020)]

## Processing

### Calibration

- pipeline or manual: CASA calibration scripts provided by the ALMA observatory.  
  > "Data were calibrated using the CASA calibration scripts provided by the ALMA observatory." (Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-calibration on the most compact configurations only; extended configurations too resolved.  
  > "Self-calibration using the continuum data was performed on the most compact configurations, but not for the most extended ones" (Proper motions:); "is heavily resolved and does not leave enough flux on most baselines for this purpose." (Proper motions:)

### Imaging

- task: IMAGER; bandwidth synthesis for continuum.  
  > "Calibrated visibilities were then exported into UVFITS data format for imaging and further analysis, using the `IMAGER` package" (Data reduction); "Bandwidth synthesis was used to obtain the images." (Spectral and continuum imaging:)
- deconvolver: _not stated_
- weighting robust: Various robust weighting parameters; numerical values not stated.  
  > "Various choices of robust weighting parameters were used in order to offer an adequate compromise between angular resolution, sensitivity and dirty beam shape" (Spectral and continuum imaging:)
- uv taper: _not stated_
- cell size: 0.025 arcsec  
  > "All data was then imaged using a common grid, with a pixel size of $0.025''$." (Spectral and continuum imaging:)
- image size: CO field of view: 25.6 arcsec  
  > "A field of view of $25.6''$ was used for CO to best handle the extended background clouds" (Spectral and continuum imaging:)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Different configurations combined after astrometric and flux corrections; older data rescaled before merging.  
  > "Once the astrometric and flux calibration issues were solved, data from different configurations were combined together." (Spectral and continuum imaging:); "were found to be too bright by about 5 and 7 % respectively, and were rescaled accordingly in flux before being merged with the newer data for imaging and analysis." (Flux calibration:)
- smoothing: _not stated_
- final beam: Appendix: CO 0.217 × 0.144 arcsec, PA 104°; continuum 230 GHz 0.172 × 0.113 arcsec, PA 100°; 345 GHz 0.166 × 0.121 arcsec, PA 90°. Main-text continuum beams differ slightly.  
  > "The CO synthesized beam is $0.217 \times 0.144''$ at PA $104^\circ$" (Spectral and continuum imaging:); "The resolution is $0.172\times  0.113''$ at PA $100^\circ$ at 230 GHz, and $0.166 \times 0.121''$ at PA $90^\circ$ at 345 GHz." (Spectral and continuum imaging:); "The angular resolution is $0.173\times0.114''$ at PA $98^\circ$ at 230 GHz, and $0.165\times0.122''$ at PA $91^\circ$ at 345 GHz respectively." (Observations and Imaging)
- final rms: CO ~0.1 K per 0.23 km s−1; continuum absolute rms not stated, actual noise 1.5–2 times thermal noise.  
  > "the noise level is $\sim 0.1$ K at 0.23 km s$^{-1}$ spectral resolution." (Spectral and continuum imaging:); "The continuum data is however dynamic range limited, with actual noise level 1.5 to 2 times larger than the thermal noise" (Spectral and continuum imaging:)

### Inherited from earlier work

- Dust shadow method repeated at higher angular resolution.  
  > "We used the “shadow” method developed by (cite: Guilloteau+2016)" (The dust disk shadow onto the CO extended emission) [from (cite: Guilloteau+2016)]
- Continuum disk-fitting method: radially truncated power-law surface density and temperature.  
  > "We followed the method explained in (cite: Guilloteau+etal_2011), using a simple power law distribution for the dust surface density and temperature, radially truncated at an inner and outer radii." (Dust temperature from disk model fitting) [from (cite: Guilloteau+etal_2011)]
- Radially varying dust opacity index prescription.  
  > "with the exponent following the prescription of (cite: Guilloteau+etal_2011)" (Dust temperature from disk model fitting) [from (cite: Guilloteau+etal_2011)]
- DiskFit ray-tracing model.  
  > "we fitted the continuum emission using a simple inclined disk model, using the ray tracing DiskFit tool (cite: Pietu+2007)." (Dust temperature from disk model fitting) [from (cite: Pietu+2007)]
- Vertical gas-temperature-gradient model and prescription.  
  > "we assume a disk model that has a vertical temperature gradient (cite: Dartois+etal_2003) following the prescription from (cite: Dutrey+etal_2017; Foucher+2025)" (Gas temperature from CO disk model fitting) [from (cite: Dartois+etal_2003); (cite: Dutrey+etal_2017; Foucher+2025)]
- Visibility-plane minimization and propagation of noise-induced errors.  
  > "Parameters are adjusted by a minimization based on visibility comparison in the $uv$ plane to propagate noise induced errorbars, see (cite: Pietu+2007)." (Gas temperature from CO disk model fitting) [from (cite: Pietu+2007)]
- Interpret apparent scale height and flaring from a non-settled model as settling diagnostics.  
  > "(cite: Bohler+2013) showed that settling may be diagnosed even by fitting a non-settled disk model" (Dust Settling) [from (cite: Bohler+2013)]

### Not stated but needed to reproduce (our reading)

- Resolve whether the older Simon project is 2013.1.00163.S or 2013.2.00163.S.
- CASA, IMAGER and DISKFIT versions and the actual calibration and analysis scripts.
- Configuration identifiers, execution-block selection and exact observing frequencies.
- Continuum bandwidths and the UV_FILTER line-rejection selections.
- Self-calibration solution intervals, gain modes, reference antenna, iteration count and acceptance criteria.
- Exact flux multipliers applied to each older data set and absolute flux-scale uncertainty.
- Numerical robust weights for each image, deconvolution algorithm, masks and stopping thresholds.
- Exact spectral-resampling grid and interpolation settings.
- Availability, calibration and numerical sampling of the adopted 30-m background spectrum.
- Exact shadow-map velocity selections and uncertainty propagation.
- Visibility weights, excluded data, fitted parameter bounds, starting parameter sets and convergence criteria.

## Analysis recipe

1. **Register and combine the calibrated observations**: Resample spectra and convert to LSR in CASA; export UVFITS; register observations to Epoch 2016.0; rescale older fluxes; combine configurations and image with IMAGER.  
  > "Spectral resampling and conversion to the LSR velocity frame were done withing CASA prior to exportation to UVFITS format." (Data reduction); "All observations were then registered to Epoch 2016.0 using the derived proper motion" (Proper motions:); "Once the astrometric and flux calibration issues were solved, data from different configurations were combined together." (Spectral and continuum imaging:)
   - software: CASA, IMAGER, UV_FILTER
   - parameter: Older 2013.1.00387.S and 2013.2.00163.S fluxes too bright by about 5 and 7%, respectively; rescaled before merging.  
  > "the older observations from May 2015 (2013.1.00387.S and 2013.2.00163.S) were found to be too bright by about 5 and 7 % respectively" (Flux calibration:)
   - parameter: Filter spectral lines with UV_FILTER; rotate final images 3.1° clockwise.  
  > "The continuum images were produced after filtering the spectral line emission using the `UV_FILTER` command of `IMAGER`." (Spectral and continuum imaging:); "All spectral and continuum images were finally rotated by 3.1$^\circ$ clockwise to align the disk major axis along the X axis." (Spectral and continuum imaging:)
   - fitting: Derive proper motion by comparing continuum positions across epochs.  
  > "we were able to derive the proper motion of the source by comparing the apparent positions as a function of time, using the continuum data obtained for each data set." (Proper motions:)
   - validation: Configuration fluxes agree within <2%; several deconvolution methods agree within expected spectral-line noise.  
  > "The two configurations observed in each of Band 6 and Band 7 gave very consistent flux measurements (within $< 2$ %)." (Flux calibration:); "We tested several deconvolution methods, all giving consistent results within the expected noise level for the spectral line observations." (Spectral and continuum imaging:)
2. **Constrain dust temperature from the continuum brightness ratio**: Compare continuum brightness at the two frequencies using a uniform slab and Planck-function corrections; infer a temperature upper limit.  
  > "In the optically thick limit, or when opacities are equal at both frequencies, this $S_{23}$ value corresponds to $T_d = 13$ K." (Direct analysis of dust emission); "this value is an upper limit: a partially optically thin medium would need to be colder." (Direct analysis of dust emission)
   - parameter: Brightness ratio approximately 1.25 between 20 and 120 au in the appendix.  
  > "The uniform slab approximation is reasonable, since $S_{23}$ is approximately constant at 1.25 between 20 and 120 au" (Direct analysis of dust emission)
   - assumption: Common beam filling factor at both frequencies.  
  > "Given the similar geometrical thickness and spatial resolution at both frequencies" (Direct analysis of dust emission); "a common beam filling factor can be used." (Direct analysis of dust emission)
   - assumption: Dust opacity larger at 345 GHz than at 230 GHz.  
  > "for all reasonable dust properties the opacity is larger at 345 GHz than at 230 GHz" (Direct analysis of dust emission)
   - fitting: _not stated_
   - validation: Approximately constant brightness ratio supports the uniform-slab approximation.  
  > "The uniform slab approximation is reasonable, since $S_{23}$ is approximately constant at 1.25 between 20 and 120 au" (Direct analysis of dust emission)
3. **Measure dust temperature against the CO background**: Use continuum and velocity-dependent shadow brightness with the 30-m cloud spectrum; take the median of independent velocity estimates. Cross-check with spectral zeros.  
  > "The cloud emission being velocity dependent provides several independent estimates for each direction, and we take the median value to obtain the dust temperature map" (The shadow method for dust); "Whenever the computed spectra are 0, the dust (brightness) temperature is directly given by the CO spectrum intensity." (The dust disk shadow onto the CO extended emission)
   - parameter: Average mid-plane spectra between 24 and 180 au and between -24 and -180 au.  
  > "we compute the average spectra from the disk mid-plane between 24 and 180 au, and -24 and -180 au" (The dust disk shadow onto the CO extended emission)
   - parameter: Use uncontaminated low velocities of the red spectrum and high velocities of the blue spectrum; correct cosmic background and Rayleigh Jeans deviation.  
  > "Using the part of the spectra which are not contaminated by CO emission from the disk (low velocities of red spectrum, and high velocities of the blue one), and after correction from the cosmic background and Rayleigh Jeans deviation" (The dust disk shadow onto the CO extended emission)
   - parameter: Dust spectral zeros at 2.7 and 7.3 km s−1.  
  > "but this only occurs at two velocities, (2.7 and 7.3 km s$^{-1}$" (The shadow method for dust)
   - assumption: No scattering; 30-m spectrum represents uniform emission behind the disk.  
  > "these shadow methods assume no scattering" (Mid-plane temperature); "the shadow methods also assume that the 30-m spectrum represents uniform emission behind the dust disk." (Mid-plane temperature)
   - fitting: _not stated_
   - validation: Zero-crossing temperatures agree with the median shadow-map value.  
  > "These mean temperatures are quite consistent with the median value derived before." (The dust disk shadow onto the CO extended emission)
4. **Estimate gas temperature from spectral zeros**: Use zeros at velocities containing disk CO emission; assess beam filling and velocity-dependent emitting extent.  
  > "we are left with the methods relying only on the zero values" (The shadow method for gas); "Assuming $f=1$, we get temperatures ranging from 9.5 K to 14.7 K." (The shadow method for gas)
   - parameter: Zeros within [2.0,5.4] km s−1 require no emitting-radius correction; filling factor 0.5 at 3.7 km s−1 raises the estimate to 14.2 K.  
  > "Fortunately, all zeros are within the \[2.0,5.4\] km s$^{-1}$ velocity range and do not need to be corrected." (The shadow method for gas); "Using a more appropriate beam filling factor of 0.5 for this case raises the temperature to 14.2 K." (The shadow method for gas)
   - assumption: CO likely thermalized.  
  > "since CO is likely to be thermalized." (Gas temperature determined from the background)
   - assumption: Neglect a 0.2 K apparent-brightness effect from CO hiding dust.  
  > "However, this is a small effect on the apparent brightness (only 0.2 K) that we can neglect." (The shadow method for gas)
   - fitting: _not stated_
   - validation: Check that the zeros do not require velocity-dependent emitting-radius corrections.  
  > "Fortunately, all zeros are within the \[2.0,5.4\] km s$^{-1}$ velocity range and do not need to be corrected." (The shadow method for gas)
5. **Fit the dust continuum disk**: Simultaneously fit 230 and 345 GHz continuum with an inclined, flared disk; power-law radial surface density, temperature and scale height; Gaussian vertical density; inner and outer truncation.  
  > "We followed the method explained in (cite: Guilloteau+etal_2011), using a simple power law distribution for the dust surface density and temperature, radially truncated at an inner and outer radii." (Dust temperature from disk model fitting); "The disk is flared, with a Gaussian distribution in density as a function of distance to the mid-plane, and its scale height is a power law of the radius." (Dust temperature from disk model fitting); "We fit simultaneously the 230 and 345 GHz data" (Dust temperature from disk model fitting)
   - software: DISKFIT
   - parameter: κ(ν) = κ0(ν/ν0)^β(r); β(r) = β0 + βr log(r/R0); κ(230 GHz) = 3.5 cm² per gram of dust.  
  > "assuming the dust opacity is given by $\kappa(\nu) = \kappa_0 (\nu/\nu_0)^{\beta(r)}$" (Dust temperature from disk model fitting); "$\beta(r) = \beta_0 + \beta_r\log(r/R_0)$, with $\kappa(\mathrm{230\,GHz}) = 3.5$ cm$^2$ per gram of dust." (Dust temperature from disk model fitting)
   - assumption: Dust temperature depends only on radius.  
  > "The dust temperature only depends on radius." (Dust temperature from disk model fitting)
   - assumption: 120 pc; dust to gas ratio of 100, as written.  
  > "we adopt a distance of 120 pc in this work." (Proper motions:); "We derive the H$_2$ surface density assuming a dust to gas ratio of 100." (Dust temperature from disk model fitting)
   - fitting: Modified Levenberg-Marquardt minimization; several starting parameter sets; covariance-matrix error bars.  
  > "We use a modified Levenberg-Marquardt minimization method, with several starting parameter sets to avoid local minima." (Dust temperature from disk model fitting); "Error bars were derived from the covariance matrix." (Dust temperature from disk model fitting)
   - validation: Multiple starting sets address local minima; compare with independently derived shadow temperatures.  
  > "with several starting parameter sets to avoid local minima." (Dust temperature from disk model fitting); "However, DISKFIT yields a higher value, around 9 K, with slightly larger errors due to the coupling between the assumed dust emissivity profiles" (Mid-plane temperature)
6. **Fit CO thermal structure and depletion**: Ray-trace CO against the velocity-dependent 30-m background; fit visibilities with a vertical temperature gradient, power-law surface density and scale height, inner and outer truncation, and no CO below ZdH(r).  
  > "we assume that CO is not present below some depletion scale $z_d$, i.e. for $z < z_d = Z_d H(r)$." (Gas temperature from CO disk model fitting); "using the 30-m CO spectrum from (cite: Guilloteau+2016), shown in Fig.[2](#fig:midplane), as a background for ray-tracing as a function of velocities." (Gas temperature from CO disk model fitting); "Parameters are adjusted by a minimization based on visibility comparison in the $uv$ plane to propagate noise induced errorbars" (Gas temperature from CO disk model fitting)
   - software: DISKFIT
   - parameter: Fit orientation, inclination, systemic velocity, stellar mass and local line width.  
  > "To reproduce the velocity pattern, we also account for the geometric and kinematics parameters" (Disk Model); "orientation ($PA=3.1\pm0.2^\circ$), inclination ($i=86.3\pm0.2^\circ$), systemic velocity ($V_\mathrm{LSR}=3.71\pm0.01$ km s$^{-1}$), stellar mass (M$_*=0.59\pm0.01 \,\mathrm{M}_\odot$), and local line width" (Disk Model)
   - assumption: Gaussian vertical density; prescribed mid-plane-to-atmosphere temperature gradient; CO scale height independent of mid-plane temperature.  
  > "the density distribution is assumed to be a Gaussian as a function of height $z$ above the mid-plane" (Disk Model); "We do not impose the scale height to be related to the mid-plane temperature." (Disk Model); "$z_q$ indicates the start of the (isothermal) atmosphere, $\delta$ the gradient steepness." (Disk Model)
   - assumption: Local line width constant across the disk; no a priori temperature information imposed on the depletion boundary.  
  > "local line width ($\delta V = 0.20\pm0.01$ km s$^{-1}$, assumed constant across the disk)." (Disk Model); "we used a prescribed shape for the depleted layer that did not incorporate any a priori temperature information" (Gas disk and CO depletion)
   - fitting: Visibility-plane minimization; alleviate coupled Tmid, Zd, H0 and δ by fixing one parameter and solving for the others.  
  > "Parameters are adjusted by a minimization based on visibility comparison in the $uv$ plane to propagate noise induced errorbars" (Gas temperature from CO disk model fitting); "Significant coupling exists between $T_\mathrm{mid}$, $Z_d$, $H_0$ and $\delta$." (Disk Model); "To alleviate this problem, we performed fits fixing one parameter and solving for the others." (Disk Model)
   - validation: Explore an alternate sine-based temperature profile; all explored cases retain low Tmid and about 17 K at the depletion height.  
  > "We also explored an alternate functional shape" (Disk Model); "All explored cases yielded low $T_\mathrm{mid}$, and the temperature at $z = z_d$ was always around 17 K." (Disk Model)
7. **Check dust optical depth**: Fit vertical Gaussian profiles, deconvolve the beam minor axis, infer filling factors and compare brightness with dust temperature; independently verify model optical depths analytically.  
  > "Apparent sizes were derived by Gaussian fit to the observed (vertical) profile." (Direct determination:); "The intrinsic thickness is derived (to first order) by deconvolving the apparent thickness from the effective resolution, here the beam minor axis" (Direct determination:); "a simple analytical verification is possible because, for dust, the best fit model is essentially one of an isothermal, uniform surface density disk." (From the model:)
   - software: DISKFIT
   - parameter: Mean filling factor 0.83; possible seeing-corrected filling factor 0.7; adopted dust temperature 9 K.  
  > "The mean filling factor is $0.83$." (Direct determination:); "This may bring down the beam filling factor to $0.7$" (Direct determination:); "When compared to the estimated dust temperature, 9 K, this indicates dust opacities of order 0.25." (Direct determination:)
   - assumption: Analytical check assumes edge-on geometry and ignores incidence-angle effects up to about 120 au.  
  > "Assuming edge-on geometry, at an impact parameter $R$, the line of sight optical depth in the midplane is approximately given by" (From the model:); "which allows us to ignore the incidence angle at each radius, an approximation that is valid up to about 120 au" (From the model:)
   - fitting: Gaussian fits to observed vertical profiles.  
  > "Apparent sizes were derived by Gaussian fit to the observed (vertical) profile." (Direct determination:)
   - validation: Analytical optical-depth estimate agrees with the fitted inner-radius upper limit.  
  > "The disk becomes optically thick only for radii smaller than 2 au, consistent with an inner radius upper limit found in the minimization process." (From the model:)
8. **Interpret depletion and settling**: Compare temperature at the fitted depletion boundary with CO freeze-out expectations; compare dust scale height and flaring with hydrostatic gas expectations and NIR morphology.  
  > "This is in good agreement with the freeze out temperature of CO on pure ice (cite: Bisschop+2006; Minissale+2022)" (Gas disk and CO depletion); "the dust scale height (9 au) is not significantly lower than the predicted gas scale height (11 au) if the mid-plane temperature is 10 K (at 100 au)." (Dust Settling); "the flaring index is $-h = 0.9$ for dust compared to the expected value of $1.5$ for the gas under hydrostatic equilibrium at constant mid-plane temperature" (Dust Settling)
   - assumption: Hydrostatic gas comparison at constant mid-plane temperature.  
  > "the expected value of $1.5$ for the gas under hydrostatic equilibrium at constant mid-plane temperature" (Dust Settling)
   - fitting: _not stated_
   - validation: Compare self-shadowing interpretation with the flat radial temperature profile and independently observed NIR flaring.  
  > "a simple shadowing would result in a steep radial temperature gradient like in GG Tau (cite: Dutrey+2014), in contrast to our flat temperature profile." (Dust Settling); "Furthermore, the NIR images from (cite: Grosso+2003) indicate a flared morphology consistent with a flaring index of 1.25." (Dust Settling)

## Software

- **CASA** : ALMA-script calibration, spectral resampling and LSR-frame conversion before UVFITS export.  
  > "Data were calibrated using the CASA calibration scripts provided by the ALMA observatory." (Data reduction); "Spectral resampling and conversion to the LSR velocity frame were done withing CASA prior to exportation to UVFITS format." (Data reduction)
- **IMAGER** : Imaging and further analysis of UVFITS visibilities.  
  > "Calibrated visibilities were then exported into UVFITS data format for imaging and further analysis, using the `IMAGER` package" (Data reduction)
- **UV_FILTER** : IMAGER command filtering spectral-line emission before continuum imaging.  
  > "The continuum images were produced after filtering the spectral line emission using the `UV_FILTER` command of `IMAGER`." (Spectral and continuum imaging:)
- **DISKFIT** : Continuum disk fitting, CO radiative transfer and optical-depth maps.  
  > "we fitted the continuum emission using a simple inclined disk model, using the ray tracing DiskFit tool (cite: Pietu+2007)." (Dust temperature from disk model fitting); "The radiative transfer is solved by the DISKFIT code" (Gas temperature from CO disk model fitting); "the DISKFIT tool can produce optical depth maps for the best fit model parameters" (From the model:)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust brightness ratio Tb(230)/Tb(345), 0–140 au | 1.25 | not stated | dimensionless | 2 | we find a $T_b(230)/T_b(345)$ brightness ratio of 1.25 in the 0-140 au range |
| Uniform-slab dust-temperature upper limit | 13 | not stated | K | 2 | In the optically thick limit, or when opacities are equal at both frequencies, this $S_{23}$ value corresponds to $T_d = 13$ K.; this value is an upper limit: a partially optically thin medium would need to be colder. |
| Mean shadow-method dust temperature, 20–180 au | 5.5 | ±0.5 | K | 3 | the dust temperature is roughly constant between 20 au and the disk edge, 180 au, with a mean value of $5.5\pm0.5$ K |
| Dust temperatures from the two uncontaminated spectral-zero estimates | 5.2 and 5.4 | not stated | K | 3 | we find dust temperatures of $5.2\,$K and $5.4$ K. |
| Gas shadow temperatures assuming f = 1 | 9.5 to 14.7 | not stated | K | 4 | Assuming $f=1$, we get temperatures ranging from 9.5 K to 14.7 K. |
| Gas shadow temperature with filling factor 0.5 at the systemic-velocity zero | 14.2 | not stated | K | 4 | Using a more appropriate beam filling factor of 0.5 for this case raises the temperature to 14.2 K. |
| Dust-model mid-plane temperature at 100 au | 9.0 | ±1.0 | K | 5 | $9.0$          / $\pm$ / $1.0$          / K           / Mid-plane Temperature at 100 au |
| CO-model mid-plane temperature at 100 au | 9.2 | ±0.8 | K | 6 | K           / Mid-plane Temperature at 100 au / 9.2            / $\pm$ / 0.8 |
| CO atmosphere temperature normalization | 26.6 | ±0.1 | K | 6 | Atmosphere Temperature          / 26.6           / $\pm$ / 0.1; a warmer CO layer where $T(r) \approx 27\,(r/100\,\mathrm{au})^{-0.3}$ K. |
| CO atmosphere radial temperature exponent | 0.28 | ±0.01 | dimensionless | 6 | Exponent                        / 0.28           / $\pm$ / 0.01 |
| Total disk mass with adopted opacity | about 0.009 | not stated | M⊙ | 5 | With our adopted opacity, the total disk mass is about $0.009 \,\mathrm{M}_\odot$. |
| Dust scale height at 100 au | 8.6 | ±0.35 | au | 5 | $8.6$          / $\pm$ / $0.35$         / au          / Scale height at 100 au |
| CO scale height at 100 au | 19.1 | ±0.3 | au | 6 | au          / Scale height at 100 au          / 19.1           / $\pm$ / 0.3 |
| CO depletion height in units of H(r) | 0.7 | ±0.2 | dimensionless | 6 | Depletion Height                / 0.7            / $\pm$ / 0.2 $H(r)$ |
| Dust outer radius | 187 | ±2 | au | 5 | $187$          / $\pm$ / $2$            / au          / Outer radius |
| CO outer radius | 300 | ±4 | au | 6 | au          / Outer radius                    / 300            / $\pm$ / 4 |
| Minimum CO depletion factor needed for low mid-plane optical depth | at least 500 | not stated | dimensionless | 6 | The best fit model indicates strong CO depletion below about $0.7\,H(r)$ (at least a factor 500 to ensure low optical depth for the 2-1 transition in the mid-plane). |
| Temperature at the depletion height | 19 at 100 au; 15 at 300 au | not stated | K | 6 | Using the derived temperature profile, the temperature at this height varies between 19 K at 100 au to 15 K at 300 au. |
| Disk orientation PA | 3.1 | ±0.2 | degrees | 6 | orientation ($PA=3.1\pm0.2^\circ$) |
| Disk inclination | 86.3 | ±0.2 | degrees | 6 | inclination ($i=86.3\pm0.2^\circ$) |
| Systemic velocity | 3.71 | ±0.01 | km s−1 | 6 | systemic velocity ($V_\mathrm{LSR}=3.71\pm0.01$ km s$^{-1}$) |
| Stellar mass | 0.59 | ±0.01 | M⊙ | 6 | stellar mass (M$_*=0.59\pm0.01 \,\mathrm{M}_\odot$) |
| Local line width | 0.20 | ±0.01 | km s−1 | 6 | local line width ($\delta V = 0.20\pm0.01$ km s$^{-1}$, assumed constant across the disk) |
| Direct dust optical-depth estimate | of order 0.25 | not stated | dimensionless | 7 | When compared to the estimated dust temperature, 9 K, this indicates dust opacities of order 0.25. |
| Analytical mid-plane optical depth at 70 au and 235 GHz | 0.2 | not stated | dimensionless | 7 | yielding $\tau(70\,\mathrm{au},235\,\mathrm{GHz}) =0.2$ in the mid-plane. |

## Qualitative findings

- A substantial vertical gas-temperature gradient separates the cold mid-plane from warmer CO-emitting layers.  
  > "We find clear evidence for a substantial gas temperature vertical gradient, with a cold (10 K) disk mid-plane and a warmer CO layer" (abstract)
- DISKFIT dust temperatures are preferred over lower shadow-method temperatures.  
  > "We thus consider the DISKFIT results more reliable, and that our observations and analysis indicate low temperatures for the dust, around 9 K, throughout most of the disk." (Mid-plane temperature)
- CO depletion is consistent with freeze-out on grains and disfavors significant CO-to-CO2 conversion.  
  > "This is consistent with CO freeze-out on grains, but not with significant conversion of CO to CO$_2$ on grain surfaces." (Dust Settling)
- Dust is optically thin at 345 GHz and moderately settled.  
  > "The dust disk appears optically thin at 345 GHz, and exhibits moderate settling." (abstract)

## Claim tuples

- H: The disk mid-plane is very cold, and independent dust-temperature methods can establish its temperature. | E: Compare CO-background shadow thermometry with simultaneous two-frequency DISKFIT continuum modeling. | R: Shadow methods give 5.5±0.5 K; DISKFIT gives around 9 K. | F: Cold dust is established, but the absolute temperature is method-dependent; DISKFIT is preferred. | **partially**
- H: The gas has a substantial vertical temperature gradient. | E: Fit CO visibilities with a vertically varying temperature model and explore coupled parameters and an alternate gradient shape. | R: A roughly 10 K mid-plane contrasts with warmer upper layers; explored models retain low mid-plane temperatures. | F: A substantial vertical gradient is supported, while the mid-plane value depends on extrapolation through depleted gas. | **supported**
- H: Missing mid-plane CO traces a depleted layer consistent with CO freeze-out. | E: Fit a depletion height without imposing a temperature threshold and evaluate the fitted temperature at that height. | R: Strong depletion below about 0.7 H(r), requiring at least a factor 500; boundary temperatures 19 K at 100 au to 15 K at 300 au. | F: The depleted layer is consistent with CO freeze-out and disfavors significant conversion to CO2. | **supported**
- H: The dust distribution shows settling. | E: Compare fitted dust thickness and flaring with hydrostatic gas expectations, and assess self-shadowing as an alternative. | R: Dust scale height is about 9 au versus predicted gas 11 au; dust flaring index 0.9 versus expected gas 1.5. | F: Moderate settling is suggested, especially in the outer disk. | **partially**

## Reasoning

- Why this data: Edge-on geometry and foreground placement against CO clouds enable independent dust thermometry; higher resolution improves the previous study.  
  > "We used the unique properties of the Flying Saucer, its edge-on geometry and its fortunate position in front of CO clouds with different brightness temperatures to provide independent constraints on the dust temperature." (abstract); "We use here ALMA project 2023.1.00907.S to improve this study at higher angular resolution" (Introduction)
- Why this method: DISKFIT provides an independent dust-temperature estimate; visibility-plane fitting propagates noise-induced errors.  
  > "To obtain an independent estimate of the dust temperature, we fitted the continuum emission using a simple inclined disk model" (Dust temperature from disk model fitting); "Parameters are adjusted by a minimization based on visibility comparison in the $uv$ plane to propagate noise induced errorbars" (Gas temperature from CO disk model fitting)
- Alternative: Dust self-scattering could lower shadow-method brightness, but the low optical depth seems to exclude it.  
  > "self-scattering by dust may reduce the apparent disk brightness (cite: Kataoka+2015); however, the low derived optical depth ($\sim 0.3$, see Appendix [7](#app:C-opacity)) seems to exclude this effect." (Mid-plane temperature)
- Alternative: Background-cloud inhomogeneities may bias shadow temperatures.  
  > "these inhomogeneities may bias the derived dust temperature, especially if combined with spatial structures in the dust disk." (Mid-plane temperature)
- Alternative: Alternate sine-based vertical-temperature shape retains low mid-plane temperatures and about 17 K at the depletion boundary.  
  > "We also explored an alternate functional shape" (Disk Model); "All explored cases yielded low $T_\mathrm{mid}$, and the temperature at $z = z_d$ was always around 17 K." (Disk Model)
- Alternative: Self-shadowing as an alternative to settling is disfavored by the flat radial temperature profile and flared NIR morphology.  
  > "a simple shadowing would result in a steep radial temperature gradient like in GG Tau (cite: Dutrey+2014), in contrast to our flat temperature profile." (Dust Settling); "Furthermore, the NIR images from (cite: Grosso+2003) indicate a flared morphology consistent with a flaring index of 1.25." (Dust Settling)
- How they decided it was enough: Check agreement across deconvolutions and parameter explorations, and use multiple starts to avoid local minima.  
  > "We tested several deconvolution methods, all giving consistent results within the expected noise level for the spectral line observations." (Spectral and continuum imaging:); "with several starting parameter sets to avoid local minima." (Dust temperature from disk model fitting); "All explored cases yielded low $T_\mathrm{mid}$, and the temperature at $z = z_d$ was always around 17 K." (Disk Model)
- Limitation (authors): Two continuum frequencies leave dust temperature degenerate with the opacity law.  
  > "With only 2 observing frequencies, the error bar on the temperature remains significant because of the degeneracy with the opacity law" (Dust temperature from disk model fitting)
- Limitation (authors): Shadow temperature scale inherits single-dish calibration uncertainty and assumes a uniform background.  
  > "since the single dish spectrum is the same, the absolute temperature scale in the shadow methods remains affected by the same calibration uncertainty." (Mid-plane temperature); "the shadow methods also assume that the 30-m spectrum represents uniform emission behind the dust disk." (Mid-plane temperature)
- Limitation (authors): CO mid-plane temperature is an extrapolation because CO is depleted there.  
  > "because CO appears depleted in the mid-plane, the mid-plane temperature is essentially a result of the extrapolation of prescribed shape of the vertical temperature gradient." (Gas disk and CO depletion)
- Limitation (authors): Gas shadow temperatures have a filling-factor ambiguity.  
  > "we only measure the average brightness temperature, and its value can be interpreted as being due to either cold gas filling the beam, or warmer gas with a smaller filling factor." (The shadow method for gas)
- Limitation (authors): Continuum images are dynamic-range limited by residual long-baseline phase noise, affecting inferred thickness and filling factor.  
  > "the images are dynamic range limited due to significant phase noise remaining on the long baselines." (Direct determination:); "This results in a seeing effect that should be combined in quadrature with the beam size." (Direct determination:)
- Limitation (authors): Power-law disk models cannot represent the disk edge; results are relevant to 50–250 au.  
  > "With power laws for surface density and scale heights, our model cannot represent the disk edge shape, and only yields results relevant to the 50 au to 250 au radius range." (Disk Model)
- Limitation (authors): CO-derived flaring traces CO location rather than necessarily the underlying gas distribution.  
  > "the flaring index derived from CO only reflects the location of the bulk of CO emission, and not necessarily the underlying (H$_2$ and He) gas distribution." (Dust Settling)
- Limitation (authors): Stellar properties do not constrain the system age.  
  > "Unfortunately, the stellar properties are not sufficiently known to constrain the system age." (Dust Settling)
- Caveat (inferred, ours): The inconsistent 2013.1.00163.S/2013.2.00163.S identifier needs resolution before archive retrieval.
- Caveat (inferred, ours): The main text and appendix give slightly different continuum beams and brightness-ratio radial ranges.
- Caveat (inferred, ours): The appendix defines a 235/345 GHz brightness ratio while the main text uses 230/345 GHz; exact frequency handling needs clarification.
- Caveat (inferred, ours): The phrase 'dust to gas ratio of 100' needs clarification before reproducing surface densities and disk mass.
- Caveat (inferred, ours): Covariance errors do not establish the full uncertainty from opacity, background structure and coupled vertical-model parameters.
- Caveat (inferred, ours): The strong CO-to-CO2 interpretation depends on a prescribed depleted-layer geometry and a model-extrapolated mid-plane temperature.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Unambiguous older-project identifier and execution-block manifest.
- Missing: Versioned calibration, self-calibration, imaging and fitting scripts with numerical settings.
- Missing: The numerical 30-m CO spectrum and its calibration uncertainty.
- Missing: Exact continuum channel selections, visibility weights and shadow-spectrum velocity selections.
- Missing: Fit bounds, initial parameter sets, convergence criteria and parameter-covariance products.
- Missing: Public-data status and access to the exact reduced products are not stated.
- Data volume (inferred): Not estimable from the text: multiple epochs, two bands and configurations are described, but visibility counts, integration times and bandwidths are absent.
- Score (inferred): 5/5, On a 0–10 scale: substantial equations, fitted results and cross-checks are supplied, but exact processing settings, versioned scripts, background data access and an unambiguous project manifest are missing.
- Rediscovery candidate: no, Main results are numeric, but public availability is not stated and the processing recipe lacks settings needed for a faithful rerun.

## Links

- Method: (cite: Guilloteau+2016) (Origin of the shadow method and source of the adopted 30-m CO background spectrum.)
- Method: (cite: Guilloteau+etal_2011) (Continuum disk-fitting method and radially varying dust-opacity prescription.)
- Method: (cite: Pietu+2007) (DISKFIT ray tracing and visibility-plane minimization.)
- Method: (cite: Dartois+etal_2003) (Vertical gas-temperature-gradient model.)
- Method: (cite: Dutrey+etal_2017; Foucher+2025) (Adopted vertical-temperature prescription.)
- Method: (cite: Bohler+2013) (Settling diagnostics from fitting a non-settled disk model.)
- Companion: Dutrey et al (in prep.) (Analysis of the spectral lines and evidence for a common molecular layer.)
- Related: Edge-On Disk Study (EODS)

## Checks

```json
{
 "quotes": 208,
 "quotes_ok": 208,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.2.00163.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 123,
  "stated": 99,
  "rate": 0.805
 },
 "evidence_ok": true
}
```
