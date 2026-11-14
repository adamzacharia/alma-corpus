# Zonal Winds in Titan's Middle Atmosphere from a Stellar Occultation Observed with Keck Adaptive Optics

`2025PSJ.....6..286M` | The Planetary Science Journal 2025 | first author: Marlin, Theresa C. | arXiv: 2509.16937 | DOI: 10.3847/PSJ/ae03a6

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Which ALMA-derived or GCM zonal wind profiles reproduce the resolved occultation light distributions around Titan?  
  > "We use a forward model to compare our occultation data to a wind field derived from the ALMA Doppler shift measurements, as well as to wind fields from an existing GCM simulation for Titan’s middle atmosphere." (Introduction)
- Target **Titan**: coordinates _not stated_; z/distance geocentric distance of 8.94 au  
  > "For plotting purposes, the data were projected onto a spatial grid in the plane of the sky, according to Titan’s geocentric distance of 8.94 au." (ALMA observations and data reduction); "by using the plate scale of the observations and the distance between Titan and Earth (taken from JPL HORIZONS)." (Occultation data reduction and processing); distance from JPL HORIZONS for occultation offsets  
  > "For plotting purposes, the data were projected onto a spatial grid in the plane of the sky, according to Titan’s geocentric distance of 8.94 au." (ALMA observations and data reduction); "by using the plate scale of the observations and the distance between Titan and Earth (taken from JPL HORIZONS)." (Occultation data reduction and processing)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 9 (602–720 GHz; ~0.42–0.5 mm)  
  > "using the Band 9 (602–720 GHz; $\sim0.42$–0.5 mm) receivers" (ALMA observations and data reduction)
- frequencies and spectral setup: 4 CH3CN J=35-34 lines at 643.1–643.3 GHz; 4 J=36-35 lines at 661.4–661.7 GHz; 122 kHz (55–57 m s^-1)  
  > "covering 4 lines of the CH$_3$CN $J=35-34$ rotational band (between 643.1–643.3 GHz) and 4 lines of the $J=36-35$ band (between 661.4–661.7 GHz)." (ALMA observations and data reduction); "The correlator was set to a spectral resolution of 122 kHz, corresponding to $\Delta{v}=55$–57 m s$^{-1}$." (ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.21'' × 0.18'' FWHM restoring beam  
  > "Image restoration was performed for both CH$_3$CN bands using the smallest common elliptical Gaussian beam, of FWHM $0.21'' \times 0.18''$." (ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: UT 2022-09-06, 02:29–05:48  
  > "ALMA observations of Titan were obtained on UT 2022-09-06 between 02:29–05:48 (less than 24 hours after the occultation observation)" (ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CH3CN J=35-34; 4 lines (not stated)
- Line: CH3CN J=36-35; 4 lines (not stated)
- Other facility **Keck II/NIRC2**: Spatially resolved occultation images on September 5, 2022; Kp filter  
  > "We collected data from 7:51 to 10:21 UTC (second quarter-night) on September 5, 2022 using the NIRC2 instrument on Keck II." (Adaptive optics imaging of the stellar occultation); "Data were collected in the Kp filter (1.90-2.35 $\mu$m) with frame size of 512 $\times$ 512 pixels." (Adaptive optics imaging of the stellar occultation)
- Other facility **Gemini-North/NIRI**: Concurrent spatially resolved occultation images; timing accuracy limited to 0.5 seconds  
  > "Spatially-resolved occultation data were concurrently collected with the NIRI instrument on the Gemini-North telescope, also at a cadence of roughly one frame per nine seconds." (Adaptive optics imaging of the stellar occultation); "However, the Gemini images have time stamps that are only accurate to 0.5 seconds (compared to tens of microseconds for the Keck time stamps)." (Adaptive optics imaging of the stellar occultation)
- Other facility **Huygens/HASI**: Reference temperature profile for the occultation forward model  
  > "In this paper we use the Huygens/HASI profile as our starting reference for Titan’s atmosphere" (Forward modeling of a stellar occultation)
- External data: Huygens/HASI temperature profile  
  > "In this paper we use the Huygens/HASI profile as our starting reference for Titan’s atmosphere" (Forward modeling of a stellar occultation); "(cite: fulchignoni_situ_2005)" (Forward modeling of a stellar occultation) [from (cite: fulchignoni_situ_2005)]
- External data: TAM seasonal zonal wind simulations  
  > "The seasonal cycle of the zonal winds simulated by (cite: lombardo_heat_2023) closely resembles the seasonality inferred from thermal wind measurements; we make use of these simulations." (Titan’s zonal winds simulated with General Circulation Models) [from (cite: lombardo_heat_2023)]
- External data: CH3CN abundance profile for the a priori atmospheric state  
  > "updated to incorporate the more recent CH$_3$CN abundance profile from (cite: nosowitz_improved_2025) for the *a priori* atmospheric state." (ALMA wind retrieval) [from (cite: nosowitz_improved_2025)]
- External data: Atmospheric temperature profile for ALMA radiative transfer modeling  
  > "The atmospheric temperature profile was obtained from (cite: 2020ApJ...903L..22T)." (ALMA wind retrieval) [from (cite: 2020ApJ...903L..22T)]
- External data: Seasonally Varying Radiative Species Dataset (SVRS), used in the updated TAM simulations  
  > "an observationally driven database of Titan’s atmospheric composition and aerosol opacity (the Seasonally Varying Radiative Species Dataset \[SVRS\], (cite: lombardo_influence_2023)) to calculate realistic radiative heating rates" (Titan’s zonal winds simulated with General Circulation Models) [from (cite: lombardo_influence_2023)]
- Simulation/model as data: 36 snapshots of 2D TAM zonal wind profiles over a Titan year  
  > "We used 36 snapshots of 2D zonal wind profiles over a Titan year derived from simulations with TAM." (Forward model input from GCM zonal wind profiles)
- Simulation/model as data: Original 36 GCM profiles and 1 ALMA profile, plus doubled and halved magnitudes: 111 input profiles  
  > "Input profiles include the original 36 GCM and 1 ALMA inputs (that are shown above), and the same 37 profiles with both halved and doubled magnitudes (total of 111 input profiles)." (Table 2)
- Simulation/model as data: Butler-JPL-Horizons 2012 Titan model included with CASA  
  > "Additional self-calibration of the phases was performed with respect to the Butler-JPL-Horizons 2012 Titan model included with CASA" (ALMA observations and data reduction)

## Processing

### Calibration

- pipeline or manual: Flagged and calibrated in CASA using standard scripts supplied by the Joint ALMA Observatory  
  > "The interferometric data were flagged and calibrated in the Common Astronomy Software Applications (CASA) package (cite: casa_2008) using standard scripts supplied by the Joint ALMA Observatory." (ALMA observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: as much as approximately 10%, due to uncertainty in the amplitude calibrator flux  
  > "errors on the ALMA flux scale (which may be as much as $\approx10$%, due to uncertainty in the amplitude calibrator flux)" (ALMA wind retrieval)
- self calibration: Phase self-calibration against Butler-JPL-Horizons 2012 Titan model; adjacent continuum windows centered at 649 and 666 GHz  
  > "Additional self-calibration of the phases was performed with respect to the Butler-JPL-Horizons 2012 Titan model included with CASA" (ALMA observations and data reduction); "using separate continuum windows adjacent to the main spectral windows of interest (centered at 649 GHz and 666 GHz, respectively)." (ALMA observations and data reduction)

### Imaging

- task: CASA tclean, per channel; threshold twice the RMS noise  
  > "The spectral image data were deconvolved (per channel) using the CASA `tclean` Hogböm algorithm with Briggs weighting (robust = 0.5) and a threshold twice the RMS noise" (ALMA observations and data reduction)
- deconvolver: Hogböm  
  > "using the CASA `tclean` Hogböm algorithm" (ALMA observations and data reduction)
- weighting robust: Briggs weighting (robust = 0.5)  
  > "with Briggs weighting (robust = 0.5)" (ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Visibility-domain 2nd order polynomial fit to line-free (pseudo-)continuum regions in each spectral window  
  > "Prior to imaging, the Titan continuum was subtracted from the interferometric visibility data using a 2nd order polynomial fit to the line-free (pseudo-)continuum regions in each spectral window." (ALMA observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Smallest common elliptical Gaussian beam; FWHM 0.21'' × 0.18'' for both bands  
  > "Image restoration was performed for both CH$_3$CN bands using the smallest common elliptical Gaussian beam, of FWHM $0.21'' \times 0.18''$." (ALMA observations and data reduction)
- final rms: σ=29 mJy at 643 GHz and 38 mJy at 662 GHz  
  > "$\sigma=29$ mJy at 643 GHz and 38 mJy at 662 GHz" (ALMA observations and data reduction)

### Inherited from earlier work

- Latitudinal wind retrieval strategy based on spectral-line Doppler shifts  
  > "We followed a similar strategy to (cite: cordiner_detection_2020) to retrieve the latitudinal wind velocity profile based on fits to the observed spectral lines to determine their Doppler shifts." (ALMA wind retrieval) [from (cite: cordiner_detection_2020)]
- Use of Moffat profiles instead of Gaussian or Voigt line shapes  
  > "which was found by (cite: light2024measurements) to provide a significantly better fit to the CH$_3$CN lineshapes than Gaussian or Voigt functions, especially in the presence of pressure-broadened Lorentzian line wings." (ALMA wind retrieval) [from (cite: light2024measurements)]
- NEMESIS atmospheric modeling strategy, with an updated CH3CN a priori profile  
  > "We followed a similar modeling strategy to (cite: thelen2019abundance), updated to incorporate the more recent CH$_3$CN abundance profile from (cite: nosowitz_improved_2025) for the *a priori* atmospheric state." (ALMA wind retrieval) [from (cite: thelen2019abundance)]
- Wind contribution weighting using the spectral-line gradient  
  > "to provide weighting according to the frequencies contributing most to the retrieved line Doppler shifts (see *e.g.* (cite: lellouch2019intense)), which were then averaged and peak-normalized." (ALMA wind retrieval) [from (cite: lellouch2019intense)]
- Simplified 3D radiative transfer Doppler-map deconvolution; modified atmWindMapGaussFit for a continuously variable latitudinal profile  
  > "We therefore followed a similar method to (cite: cordiner_detection_2020) to model the Doppler map and extract a latitudinal wind speed profile using a simplified 3D radiative transfer model." (ALMA wind retrieval); "The `atmWindMapGaussFit` code of (cite: cordiner_detection_2020) was modified to allow a continuously variable wind speed as a function of latitude ($v(l)$), instead of the Gaussian profile previously assumed by those authors." (ALMA wind retrieval) [from (cite: cordiner_detection_2020)]
- Convert zonal winds into radial distortions using Equations 4.16–4.26  
  > "In order to incorporate a zonal wind profile into the description of Titan’s atmospheric density structure, we follow the methodology conducted by (cite: bouchez_seasonal_2004) (Equations 4.16-4.26)." (Deriving level surface distortions from zonal winds) [from (cite: bouchez_seasonal_2004)]
- Seasonal TAM wind simulations used as forward-model inputs  
  > "The seasonal cycle of the zonal winds simulated by (cite: lombardo_heat_2023) closely resembles the seasonality inferred from thermal wind measurements; we make use of these simulations." (Titan’s zonal winds simulated with General Circulation Models) [from (cite: lombardo_heat_2023)]

### Not stated but needed to reproduce (our reading)

- ALMA project identifier and dataset identifiers.
- Antenna configuration, baselines, on-source integration time and complete spectral-window/channel layout.
- CASA and calibration-script versions, detailed flagging and calibrator identities.
- Phase self-calibration solution intervals, iteration count and solution-selection criteria.
- Exact line-free channels used for the polynomial continuum subtraction.
- Image cell size, dimensions, cleaning masks and maximum iteration count.
- Individual CH3CN transition identities, adopted rest frequencies and frequency/velocity reference convention.
- Exact Doppler zero-point correction and the pixel-selection rule used to average velocities inside the limb.
- Moffat initialization, bounds and MPFIT configuration.
- NEMESIS opacity inputs, retrieval regularization and full prior/error settings.
- Modified atmWindMapGaussFit source and full 3D emissivity/geometry configuration.
- Keck plate scale, orientation calibration, selected PSF frame and Richardson-Lucy iteration count.
- Hydrostatic pressure boundary condition, reference co-latitude and exact reference-radius convention.
- Forward-model spatial grid, effective wavelength, PSF prescription and numerical integration settings beyond the stated chord sampling.
- Exact lightspot extraction regions, usable-frame list, Gaussian fit settings and angular wrap handling.

## Analysis recipe

1. **Isolate occultation starlight**: Reduce Keck images, Richardson-Lucy deconvolve, align disks and subtract median disk emission  
  > "Reduction steps included median sky subtraction, application of a flat field, construction of a bad pixel map and subsequent bad pixel removal, cosmic ray removal, and flux calibration using the photometric standard stars." (Occultation data reduction and processing); "For image deconvolution, we used the richardson_lucy function from the skimage.restoration image restoration module by Scikit-Image (cite: van_der_walt_scikit-image_2014)." (Occultation data reduction and processing); "we determined the median disk emission (calculated from the reduced, deconvolved, and stacked frames) and subtracted it from all of the frames so that only refracted starlight along the limb was visible in each frame." (Occultation data reduction and processing)
   - software: nirc2reduce, Scikit-Image, image_registration
   - parameter: Universal PSF from the frame with the sharpest star  
  > "We ultimately used a universal PSF derived from the frame with the sharpest star, as this gave the sharpest deconvolved disks." (Occultation data reduction and processing)
   - parameter: Fit a circle to minimum radial gradients; align fitted disk centers  
  > "Then, a circle was fit to the minimum radial gradient values for all angles around the circle" (Occultation data reduction and processing); "the images were then aligned so that the (x,y) coordinates of the center of the fitted circles were stacked on top of each other." (Occultation data reduction and processing)
   - fitting: Circle fit to minimum radial gradient values  
  > "Then, a circle was fit to the minimum radial gradient values for all angles around the circle" (Occultation data reduction and processing)
   - validation: Compare PSFs on pre- and post-occultation frames; choose the sharpest deconvolved disks  
  > "To find the best PSF for deconvolution, we studied the effectiveness of different PSFs in frames before and after occultation, when the occulted star was in the frame alongside Titan." (Occultation data reduction and processing); "We ultimately used a universal PSF derived from the frame with the sharpest star, as this gave the sharpest deconvolved disks." (Occultation data reduction and processing)
2. **Determine the occultation trajectory**: Fit star centroids outside occultation, subtract fitted Titan centers and linearly interpolate x/y offsets through occultation  
  > "Two one-dimensional Gaussians led to centroids with the least variability." (Occultation data reduction and processing); "Titan-star offsets were calculated for all pre- and post-occultation frames by taking the difference of the star centroid and the fitted circle center for Titan’s disk." (Occultation data reduction and processing); "Linear fits were applied to both the x- and y- directions (as a function of time) in order to interpolate the x- and y-offsets during the frames when the star was not visible" (Occultation data reduction and processing)
   - software: JPL HORIZONS
   - parameter: 9×9 pixel star subframe for x; 11×11 for y  
  > "the star was isolated in a 9$\times$9 pixel subframe (x-direction) or an 11$\times$11 pixel subframe (y-direction)." (Occultation data reduction and processing)
   - parameter: Convert detector offsets using plate scale and JPL HORIZONS Titan–Earth distance  
  > "by using the plate scale of the observations and the distance between Titan and Earth (taken from JPL HORIZONS)." (Occultation data reduction and processing)
   - fitting: Two one-dimensional Gaussians for stellar centroids; linear fits to x/y offsets versus time  
  > "Two one-dimensional Gaussians led to centroids with the least variability." (Occultation data reduction and processing); "Linear fits were applied to both the x- and y- directions (as a function of time)" (Occultation data reduction and processing)
   - validation: Choose subframe widths and centroid method with the lowest variability  
  > "These star subframe widths were selected based on which led to the lowest variability in centroid fitting." (Occultation data reduction and processing); "Two one-dimensional Gaussians led to centroids with the least variability." (Occultation data reduction and processing)
3. **Measure ALMA Doppler shifts**: Simultaneously fit eight CH3CN lines with Moffat functions in every image pixel  
  > "The Gaussian line fitting method was updated to use the Moffat function (cite: moffat1969theoretical) instead" (ALMA wind retrieval); "All eight CH$_3$CN spectral lines were fitted simultaneously for all pixels in the ALMA images, using a Levenberg-Marquardt least-squares minimization routine written in Python, based on the MPFIT package (cite: markwardt2009non)." (ALMA wind retrieval)
   - software: Python, MPFIT
   - parameter: Common variable velocity offset across all lines; other Moffat parameters independent for each line  
  > "All parameters of the Moffat function were allowed to vary independently for each line, apart from the velocity offset parameter, for which a common (variable) value was used for all lines." (ALMA wind retrieval)
   - fitting: Levenberg-Marquardt least squares; Doppler uncertainties from covariance-matrix diagonal elements  
  > "using a Levenberg-Marquardt least-squares minimization routine written in Python, based on the MPFIT package (cite: markwardt2009non)." (ALMA wind retrieval); "The uncertainty on the Doppler shift for each pixel was derived from the diagonal elements of the covariance matrix." (ALMA wind retrieval)
   - validation: Moffat functions reproduce observed line profiles within the noise  
  > "We found that the Moffat function was able to fully reproduce our observed line profiles (within the noise), resulting in a more accurate determination of the line Doppler shift than the conventional Gaussian fitting method." (ALMA wind retrieval)
4. **Correct the Doppler zero point**: Average fitted line-of-sight velocities inside Titan’s limb and subtract the resulting zero-point shift from individual pixels  
  > "The magnitude of the shift was calculated by taking the average of the fitted line-of-sight velocities inside Titan’s limb." (ALMA wind retrieval); "This “zero point shift” was then subtracted from the individual pixel Doppler shifts for the subsequent data analysis steps." (ALMA wind retrieval)
   - parameter: Approximately +30 m s^-1 offset  
  > "A significant ($\approx+30$ m s$^{-1}$) offset in the spectral line Doppler shifts was identified at the center of Titan’s disk (and along the direction of its polar axis)." (ALMA wind retrieval)
   - assumption: Zonal winds symmetric with respect to Titan’s polar axis  
  > "Our ALMA data analysis here therefore also inherently assumes that the zonal winds are symmetric with respect to Titan’s polar axis." (ALMA wind retrieval)
   - fitting: _not stated_
   - validation: _not stated_
5. **Determine ALMA altitude sensitivity**: NEMESIS radiative transfer and CH3CN abundance retrieval; derive wind contribution from altitude functional derivatives weighted by the spectral-line gradient  
  > "we used the Non-linear optimal Estimator for MultivariatE spectral analySIS (NEMESIS) to generate a detailed radiative transfer model for the observed CH$_3$CN emission" (ALMA wind retrieval); "This abundance profile formed the basis of our “wind contribution function” calculation, which was obtained from the corresponding NEMESIS functional derivatives ($dQ/dz$) of flux with respect to altitude, as a function of frequency." (ALMA wind retrieval); "The $dQ/dz$ values were convolved with the gradient of the (continuum-subtracted) model spectral line profile, to provide weighting according to the frequencies contributing most to the retrieved line Doppler shifts" (ALMA wind retrieval)
   - software: CASA, tclean, NEMESIS
   - parameter: Re-image calibrated cubes before continuum subtraction; extract disk-averaged spectra with 1.5'' diameter aperture  
  > "The calibrated ALMA data cubes were re-imaged prior to continuum subtraction" (ALMA wind retrieval); "Disk-averaged spectra were then extracted using a circular aperture with a diameter of 1.5$''$" (ALMA wind retrieval)
   - parameter: 35 annuli; emission angles 0–75 degrees; tangential altitude up to 1050 km  
  > "Titan’s disk (plus atmosphere) was divided into 35 annuli corresponding to emission angles between 0-75 degrees, covering the center of Titan up to a tangential altitude of 1050 km" (ALMA wind retrieval)
   - parameter: Model vertical extent 1200 km; negligible emission above 1000 km  
  > "the vertical extent of our model was 1200 km, but emission is negligible above 1000 km" (ALMA wind retrieval)
   - parameter: Scale observed data, including continuum, by 0.982  
  > "The observed ALMA data (including the continuum) were scaled by a constant factor of 0.982 to produce a match between the modeled and observed continuum levels." (ALMA wind retrieval)
   - parameter: Average and peak-normalize the weighted contribution functions  
  > "which were then averaged and peak-normalized." (ALMA wind retrieval)
   - assumption: Atmospheric temperature profile from (cite: 2020ApJ...903L..22T)  
  > "The atmospheric temperature profile was obtained from (cite: 2020ApJ...903L..22T)." (ALMA wind retrieval)
   - assumption: A priori CH3CN abundance profile from (cite: nosowitz_improved_2025)  
  > "updated to incorporate the more recent CH$_3$CN abundance profile from (cite: nosowitz_improved_2025) for the *a priori* atmospheric state." (ALMA wind retrieval)
   - assumption: J=36-35 has the same altitude sensitivity range because line opacities and energy levels are similar  
  > "Due to the similarity of the line opacities and energy levels, this range is also applicable to the $J=36-35$ band." (ALMA wind retrieval)
   - fitting: Continuously retrieve CH3CN abundance at each altitude against J=35-34 line profiles  
  > "The CH$_3$CN abundance profile was continuously retrieved at each altitude to obtain a fit to the observed $J=35-34$ spectral line profiles." (ALMA wind retrieval)
   - validation: Continuum matching after the 0.982 scaling  
  > "The observed ALMA data (including the continuum) were scaled by a constant factor of 0.982 to produce a match between the modeled and observed continuum levels." (ALMA wind retrieval)
6. **Retrieve intrinsic latitudinal winds**: Fit a simplified 3D radiative transfer Doppler map with modified atmWindMapGaussFit to account for beam-smearing and axial tilt  
  > "Due to the effects of beam-smearing, combined with Titan’s axial tilt, extraction of the intrinsic zonal wind field requires deconvolution of the Doppler shift data." (ALMA wind retrieval); "We therefore followed a similar method to (cite: cordiner_detection_2020) to model the Doppler map and extract a latitudinal wind speed profile using a simplified 3D radiative transfer model." (ALMA wind retrieval); "The `atmWindMapGaussFit` code of (cite: cordiner_detection_2020) was modified to allow a continuously variable wind speed as a function of latitude ($v(l)$), instead of the Gaussian profile previously assumed by those authors." (ALMA wind retrieval)
   - software: atmWindMapGaussFit, MPFIT
   - parameter: Seven latitude points separated by 30 degrees  
  > "Seven latitudinal points (with $\Delta{(l)}=30^{\circ}$ separation) were found to produce a good fit to the observed Doppler map" (ALMA wind retrieval)
   - parameter: Segmented linear interpolation, smoothed with Gaussian FWHM equal to point spacing  
  > "by a segmented linear function. This function was then smoothed by a Gaussian function of FWHM equal to the spacing between the points." (ALMA wind retrieval)
   - parameter: Exponential taper with 1 degree scale length; zero wind at poles  
  > "An exponential taper was applied at the ends of the $v(l)$ profile (with an exponential smoothing scale length of 1$^{\circ}$), to ensure a velocity of zero at the poles." (ALMA wind retrieval)
   - assumption: Zonal winds symmetric with respect to Titan’s polar axis  
  > "Our ALMA data analysis here therefore also inherently assumes that the zonal winds are symmetric with respect to Titan’s polar axis." (ALMA wind retrieval)
   - fitting: Optimize each velocity point with MPFIT least squares and associated error estimates  
  > "Each velocity point $v_i$ was then optimized using MPFIT, to obtain the least-squares solution and associated error estimates." (ALMA wind retrieval)
   - validation: Experiment with point counts; seven points give a good Doppler-map fit while remaining constrained by the data  
  > "To maximize the information content in the $v(l)$ retrieval, we experimented in fitting the observations with profiles incorporating different numbers of variable latitudinal points $i$." (ALMA wind retrieval); "Seven latitudinal points (with $\Delta{(l)}=30^{\circ}$ separation) were found to produce a good fit to the observed Doppler map, while still allowing the retrieved profile to be well constrained by the data" (ALMA wind retrieval)
7. **Construct wind-distorted atmospheres**: Use HASI temperature, integral hydrostatic equilibrium and ideal gas law; distort density and refractivity profiles using ALMA or TAM winds  
  > "Calculate the pressure profile from $T(r)$ using the law of hydrostatic equilibrium and the assumption of a nitrogen atmosphere" (Forward modeling of a stellar occultation); "Calculate the number density profile, $N(r)$, from $T(r)$ and $P(r)$, using the ideal gas law." (Forward modeling of a stellar occultation); "we chose to apply the radial distortions derived from zonal wind profiles in each GCM snapshot" (Forward model input from GCM zonal wind profiles)
   - software: Titan Atmospheric Model (TAM)
   - parameter: Integral form of hydrostatic equilibrium  
  > "We use the integral form of hydrostatic equilibrium in our forward model exploring modifications to surfaces of level pressure exerted by zonal winds." (Forward model input from GCM zonal wind profiles)
   - parameter: Reference altitude corresponding to the ALMA contribution-function peak  
  > "A reference altitude $r(P,\phi_0)$ at reference co-latitude $\phi_0$ is used, in our case corresponding to the peak altitude from the ALMA contribution function." (Deriving level surface distortions from zonal winds)
   - parameter: GCM wind profiles displayed at reference altitude 307 km  
  > "for a reference altitude (307 km)." (Forward model input from GCM zonal wind profiles)
   - assumption: HASI temperature profile; nitrogen atmosphere  
  > "In this paper we use the Huygens/HASI profile as our starting reference for Titan’s atmosphere" (Forward modeling of a stellar occultation); "Calculate the pressure profile from $T(r)$ using the law of hydrostatic equilibrium and the assumption of a nitrogen atmosphere" (Forward modeling of a stellar occultation)
   - assumption: No imposed equatorial symmetry; uniform winds at each latitude, with no longitudinal variation  
  > "Our forward model does not impose equatorial symmetry; however, we do assume that any given latitude will experience uniform winds throughout (i.e. we assume no longitudinal variations in wind speeds)." (Variation in radial distortion profiles)
   - assumption: Nearly spherical level surfaces allow radius and gravity to be removed from the latitude integral  
  > "Radius $r$ and gravitational acceleration $g$ can be removed from the integral when the surfaces are nearly spherical" (Deriving level surface distortions from zonal winds)
   - fitting: _not stated_
   - validation: Scaling HASI temperatures by TAM latitude differences produced negligible changes  
  > "We also considered scaling the HASI profile by the latitudinal temperature differences simulated in the TAM GCM, but found the differences in the results to be negligible when compared to using the HASI profile without GCM scaling." (Forward modeling of a stellar occultation)
8. **Simulate resolved occultation images**: Calculate refractivity, integrate along chords, derive bending angles from phase-delay gradients, trace stellar rays and convolve with a PSF  
  > "We calculate the refractivity through $N_2$ gas at standard temperature and pressure, then scale that refractivity by the ratio of the actual number density to Loschmidt’s number" (Forward modeling of a stellar occultation); "Calculate bending angles from the gradient of the phase delay screen" (Forward modeling of a stellar occultation); "We convolve the traced light locations with an appropriate PSF to produce an image that we can compare to the AO observations." (Forward modeling of a stellar occultation)
   - parameter: Line-of-sight steps of 1 km; chord length 8000 km  
  > "We use step sizes of 1 km and a chord length of 8000 km, since number densities at distances of 4000 km (and beyond) from Titan’s center are negligible." (Forward modeling of a stellar occultation)
   - parameter: ν_STP = 29.06×10^-5 (1 + 7.7×10^-3/λ²), with λ in μm  
  > "\nu_{STP} = 29.06 \times 10^{-5} (1 + \frac{7.7 \times 10^{-3}}{\lambda^2})" (Forward modeling of a stellar occultation); "where $\lambda$ is the wavelength in $\mu$m" (Forward modeling of a stellar occultation)
   - parameter: Loschmidt’s number 2.687×10^19 particles per cm³; STP 273.15 K and 1 atmosphere  
  > "Standard Temperature and Pressure: 273.15 K and 1 atmosphere" (Forward modeling of a stellar occultation); "Loschmidt’s number ($N_{LOS}$) is $2.687 \times 10^{19}$ particles per cm$^3$." (Forward modeling of a stellar occultation)
   - assumption: 2-D screens perpendicular to the line of sight  
  > "Approximate Titan and its atmosphere as 2-D screens perpendicular to the observer’s line of sight" (Forward modeling of a stellar occultation)
   - assumption: Neglect seasonal haze effects at the probed altitudes and observing wavelengths  
  > "While we considered the effect of Titan’s seasonally variable haze, we determined the effect was negligible due to the high altitudes that are probed by occultations and the wavelength range that the occultation was observed in." (Forward modeling of a stellar occultation)
   - assumption: Applying isobar distortions to bending-angle fields introduces undetectable errors over small temperature ranges  
  > "Although isobars and isopycnals are not identical, applying the isobar distortions to the bending angle fields over small temperature ranges gives undetectable errors." (Forward modeling of a stellar occultation)
   - fitting: _not stated_
   - validation: 2-D screen approximation justified by bending angles of about 2 μrad  
  > "the bending angles we detect are only about 2 $\mu$rad, so that each detectable ray essentially travels straight through Titan’s atmosphere." (Forward modeling of a stellar occultation)
9. **Compare observed and simulated lightspots**: Sum limb light versus angle, Gaussian-fit ingress/egress spot angles and rank input atmospheres by angular sum of squared errors  
  > "Quantitative comparisons were carried out by plotting the summed distribution of light around the limb in both data and model images as a function of $\theta$" (Quantifying refracted lightspot patterns); "finding the sum of squared errors (SSE) between data and model $\theta$ values for the ingress spot and the egress spot in data frames where the lightspots could be isolated." (Quantifying refracted lightspot patterns); "$\theta$ values for data and model were determined with Gaussian fitting (cite: matthew_newville_built-fitting_2024)." (Quantifying refracted lightspot patterns)
   - software: Built-in Fitting Models in the models module
   - parameter: θ=0 degrees in the positive x-direction  
  > "with $\theta = 0^{\circ}$ in the positive x-direction" (Quantifying refracted lightspot patterns)
   - parameter: 46 occultation frames; ingress spot in 22, egress spot in 18, both spots in 10  
  > "we collected 46 frames covering the entirety of the occultation." (Quantifying refracted lightspot patterns); "We identified an “ingress lightspot" (appearing along the limb near the point of star ingress) in 22 of the 46 frames" (Quantifying refracted lightspot patterns); "an “egress lightspot" (appearing along the limb near the point of star egress) in 18 of the 46 frames" (Quantifying refracted lightspot patterns)
   - parameter: Original, doubled and halved 37-profile sets; 111 input profiles  
  > "Input profiles include the original 36 GCM and 1 ALMA inputs (that are shown above), and the same 37 profiles with both halved and doubled magnitudes (total of 111 input profiles)." (Table 2)
   - fitting: Gaussian fits to lightspot angles; SSE comparison for ingress, egress and both combined  
  > "$\theta$ values for data and model were determined with Gaussian fitting (cite: matthew_newville_built-fitting_2024)." (Quantifying refracted lightspot patterns); "Sum of squared errors table of the closest model-data matches for both ingress and egress spots combined, ingress spots alone, and egress spots alone." (Table 1)
   - validation: Compare ingress and egress separately and test doubled/halved wind magnitudes  
  > "After determining the combined best match, we probed each individual lightspot to see what distinct trends appeared at ingress and egress." (Data versus model: overall); "we ran the forward model with both doubled and halved zonal wind speeds from each of the GCM snapshots to determine the effect of increased and decreased atmospheric distortion on the correspondence between the data and the model." (Forward model input from GCM zonal wind profiles)

## Software

- **CASA** : ALMA flagging, calibration, phase self-calibration and imaging  
  > "The interferometric data were flagged and calibrated in the Common Astronomy Software Applications (CASA) package (cite: casa_2008) using standard scripts supplied by the Joint ALMA Observatory." (ALMA observations and data reduction); "Additional self-calibration of the phases was performed with respect to the Butler-JPL-Horizons 2012 Titan model included with CASA" (ALMA observations and data reduction); "using the CASA `tclean` Hogböm algorithm" (ALMA observations and data reduction)
- **tclean** : Per-channel spectral-image deconvolution  
  > "The spectral image data were deconvolved (per channel) using the CASA `tclean` Hogböm algorithm" (ALMA observations and data reduction)
- **Python** : Levenberg-Marquardt spectral-line fitting routine  
  > "using a Levenberg-Marquardt least-squares minimization routine written in Python, based on the MPFIT package (cite: markwardt2009non)." (ALMA wind retrieval)
- **MPFIT** : Spectral-line Doppler fitting and optimization of latitudinal wind points  
  > "using a Levenberg-Marquardt least-squares minimization routine written in Python, based on the MPFIT package (cite: markwardt2009non)." (ALMA wind retrieval); "Each velocity point $v_i$ was then optimized using MPFIT, to obtain the least-squares solution and associated error estimates." (ALMA wind retrieval)
- **NEMESIS** : CH3CN radiative transfer, abundance retrieval and wind contribution functions  
  > "we used the Non-linear optimal Estimator for MultivariatE spectral analySIS (NEMESIS) to generate a detailed radiative transfer model for the observed CH$_3$CN emission" (ALMA wind retrieval); "This abundance profile formed the basis of our “wind contribution function” calculation, which was obtained from the corresponding NEMESIS functional derivatives ($dQ/dz$) of flux with respect to altitude, as a function of frequency." (ALMA wind retrieval)
- **atmWindMapGaussFit** : Modified Doppler-map retrieval with continuously variable wind speed versus latitude  
  > "The `atmWindMapGaussFit` code of (cite: cordiner_detection_2020) was modified to allow a continuously variable wind speed as a function of latitude ($v(l)$), instead of the Gaussian profile previously assumed by those authors." (ALMA wind retrieval)
- **nirc2reduce** : Keck/NIRC2 data reduction  
  > "We reduced Keck/NIRC2 data using the `nirc2reduce` Python package (cite: molter_emolternirc2_reduce_2024)." (Occultation data reduction and processing)
- **Scikit-Image; skimage.restoration.richardson_lucy** : Richardson-Lucy image deconvolution  
  > "For image deconvolution, we used the richardson_lucy function from the skimage.restoration image restoration module by Scikit-Image (cite: van_der_walt_scikit-image_2014)." (Occultation data reduction and processing)
- **image_registration; fft_tools.shift.shift2d** : Align image centers for stacking  
  > "Using the shift2d function from the fft_tools.shift module of the image_registration package by PyPI (cite: ginsburg_image-registration_2023)" (Occultation data reduction and processing); "the images were then aligned so that the (x,y) coordinates of the center of the fitted circles were stacked on top of each other." (Occultation data reduction and processing)
- **JPL HORIZONS** : Titan–Earth distance for occultation offset conversion  
  > "by using the plate scale of the observations and the distance between Titan and Earth (taken from JPL HORIZONS)." (Occultation data reduction and processing)
- **Titan Atmospheric Model (TAM)** : GCM wind-profile snapshots for occultation forward models  
  > "The Titan Atmospheric Model (cite: lora_gcm_2015) is a three-dimensional GCM" (Titan’s zonal winds simulated with General Circulation Models); "We used 36 snapshots of 2D zonal wind profiles over a Titan year derived from simulations with TAM." (Forward model input from GCM zonal wind profiles)
- **TitanWRF** : Earlier Titan GCM discussed as background  
  > "TitanWRF, a three-dimensional GCM reported by (cite: newman_stratospheric_2011), which utilized a higher model top and modified diffusion scheme, simulated faster zonal winds" (Titan’s zonal winds simulated with General Circulation Models)
- **Built-in Fitting Models in the models module** : Gaussian fitting of data and model lightspot angles  
  > "$\theta$ values for data and model were determined with Gaussian fitting (cite: matthew_newville_built-fitting_2024)." (Quantifying refracted lightspot patterns)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral-line Doppler zero-point offset | approximately +30 | not stated | m s^-1 | 4 | A significant ($\approx+30$ m s$^{-1}$) offset in the spectral line Doppler shifts was identified at the center of Titan’s disk (and along the direction of its polar axis). |
| ALMA continuum scaling factor | 0.982 | not stated | dimensionless | 5 | The observed ALMA data (including the continuum) were scaled by a constant factor of 0.982 to produce a match between the modeled and observed continuum levels. |
| Average CH3CN emission altitude | 303 | not stated | km | 5 | The corresponding average emission altitude is 303 km, with sensitivity to winds primarily in the range $\sim150$-450 km. |
| Primary ALMA wind sensitivity altitude range | ~150-450 | not stated | km | 5 | The corresponding average emission altitude is 303 km, with sensitivity to winds primarily in the range $\sim150$-450 km. |
| Peak ALMA-derived wind speed | just under 200 | not stated | m/s | 6 | The best match for the ingress lightspot was observed with the ALMA data with a peak wind speed just under 200 m/s, higher than nearly all of the zonal wind profiles simulated by the GCM. |
| Best combined original-amplitude GCM solar longitude | 120 | not stated | degrees | 9 | the overall best match to the occultation data was for the input GCM atmosphere corresponding to $L_s = 120^{\circ}$ |

## Qualitative findings

- Occultation data support stronger winds in the southern hemisphere during late northern summer  
  > "Our data support the presence of stronger winds in the southern hemisphere during late northern summer." (Abstract)
- Original ALMA profile best matches ingress, but not ingress and egress combined  
  > "The ALMA wind profile provides the best match to the occultation data when only the ingress data were considered, but is not the best match when data from ingress and egress are combined." (Abstract)
- Halving GCM winds slightly improves overall matches, mainly through egress  
  > "Halving the wind speed magnitudes from the GCM led to slightly improved matches" (Data versus model: overall); "Halving the wind speed profiles did not improve the matches for the ingress spot, but generally led to better matches for the egress spot in many cases" (Data versus model: overall)
- No tested forward model reproduces the mid-event limb arcs  
  > "Finally, the mid-event frame shows wider arcs on both the north and south limbs in a pattern that we were unable to reproduce with any of our forward models." (Conclusions)

## Claim tuples

- H: Titan has stronger southern-hemisphere winds during late northern summer | E: Compare observed occultation limb light with wind-distorted forward models and inspect the mid-event geometry | R: Best-matching profiles have southern wind peaks; the mid-event geometry is consistent with stronger southern winds | F: The data support stronger southern-hemisphere winds | **supported**
- H: A seasonal GCM profile can match the resolved occultation data | E: Rank original-amplitude GCM and ALMA forward models by combined ingress/egress SSE | R: L_s 120 degrees gives combined SSE 570.5 | F: L_s 120 degrees is the best original-amplitude profile, with nearby seasonal profiles close behind | **supported**
- H: Lower peak GCM wind speeds improve agreement with the occultation | E: Repeat forward models with halved and doubled wind magnitudes | R: Halved profiles slightly improve combined matches; doubled profiles give poorer combined matches | F: Lower winds are favored by egress and combined comparisons, but not by ingress alone | **partially**
- H: Near-concurrent ALMA winds predict the occultation lightspot behavior | E: Use the ALMA wind profile as an occultation forward-model atmosphere | R: ALMA is the best original-profile ingress match, but has poorer egress agreement | F: The techniques are complementary, with agreement dependent on the lightspot considered | **partially**
- H: The tested ALMA and GCM atmospheres reproduce the mid-event light distribution | E: Compare simulated limb light with the observed mid-event arcs | R: All tested forward models fail to reproduce the observed pattern | F: The tested atmosphere family does not explain the complete occultation morphology | **refuted**

## Reasoning

- Why this data: Near-concurrent occultation and ALMA observations probe complementary middle-atmosphere altitudes  
  > "ALMA observations of Titan were obtained on UT 2022-09-06 between 02:29–05:48 (less than 24 hours after the occultation observation)" (ALMA observations and data reduction); "The altitude ranges for these three methods are complementary" (Introduction)
- Why this method: Moffat functions fit CH3CN line wings better; HASI preserves vertical resolution missing from TAM density profiles  
  > "which was found by (cite: light2024measurements) to provide a significantly better fit to the CH$_3$CN lineshapes than Gaussian or Voigt functions, especially in the presence of pressure-broadened Lorentzian line wings." (ALMA wind retrieval); "The limited vertical resolution in TAM 2D density profiles means the resulting refractivity profiles lack the necessary resolution across occultation-relevant altitudes." (Forward model input from GCM zonal wind profiles)
- Alternative: Frame-dependent stellar PSFs and Gaussian PSFs considered; universal sharpest-star PSF selected  
  > "a frame-to-frame PSF of the star (where the PSF varied by frame), a universal PSF where the sharpest star (as determined by the lowest width of distributed light) was used as PSF for all frames" (Occultation data reduction and processing); "a frame-to-frame Gaussian, and a universal Gaussian." (Occultation data reduction and processing); "We ultimately used a universal PSF derived from the frame with the sharpest star, as this gave the sharpest deconvolved disks." (Occultation data reduction and processing)
- Alternative: Two-dimensional Gaussian, center of mass and quadratic centroid methods considered; two one-dimensional Gaussians selected  
  > "including two one-dimensional Gaussians, a two-dimensional Gaussian, center of mass, and a quadratic polynomial." (Occultation data reduction and processing); "Two one-dimensional Gaussians led to centroids with the least variability." (Occultation data reduction and processing)
- Alternative: HASI temperature scaling by TAM latitude differences had negligible effects  
  > "We also considered scaling the HASI profile by the latitudinal temperature differences simulated in the TAM GCM, but found the differences in the results to be negligible when compared to using the HASI profile without GCM scaling." (Forward modeling of a stellar occultation)
- Alternative: Direct use of TAM density profiles replaced by wind-distorted HASI refractivity profiles  
  > "The limited vertical resolution in TAM 2D density profiles means the resulting refractivity profiles lack the necessary resolution across occultation-relevant altitudes." (Forward model input from GCM zonal wind profiles); "we chose to apply the radial distortions derived from zonal wind profiles in each GCM snapshot" (Forward model input from GCM zonal wind profiles)
- Alternative: Doubled and halved wind magnitudes tested  
  > "Input profiles include the original 36 GCM and 1 ALMA inputs (that are shown above), and the same 37 profiles with both halved and doubled magnitudes (total of 111 input profiles)." (Table 2)
- How they decided it was enough: Seven latitude points balance Doppler-map fit quality and constrained wind-profile errors  
  > "Seven latitudinal points (with $\Delta{(l)}=30^{\circ}$ separation) were found to produce a good fit to the observed Doppler map, while still allowing the retrieved profile to be well constrained by the data" (ALMA wind retrieval); "keeping the resulting $v(l)$ errors reasonably small with respect to variations in the retrieved profile" (ALMA wind retrieval)
- Limitation (authors): ALMA rubidium-maser cable-routing error likely introduced an unknown frequency shift and slight spectral broadening  
  > "an error in the cable routing of the ALMA rubidium maser at the time of our observations, which is likely to have introduced an erroneous and unknown frequency shift in our observations" (ALMA wind retrieval); "accompanied by a slight broadening of the spectral lines by a few tens of meters per second (R. Loomis, private communication)." (ALMA wind retrieval)
- Limitation (authors): ALMA winds are not vertically resolved; equatorial-jet contributions cannot be isolated  
  > "As the ALMA wind profile is not vertically resolved, isolating the contribution of the equatorial jet from the contributions of winds at lower altitudes that contribute more heavily to the CH$_3$CN profile is not possible." (Comparison between GCM, occultation, and ALMA zonal winds)
- Limitation (authors): GCM and ALMA forward-model inputs differ in vertical treatment  
  > "the implementations of ALMA and GCM profiles into our forward model varied slightly due to GCM simulations being altitudinally resolved while ALMA retrieved wind speeds are averaged over an altitude contribution function" (Comparison between GCM, occultation, and ALMA zonal winds)
- Limitation (authors): Best combined fit is driven by the poorer-fitting egress lightspot; untested wind shapes may fit better  
  > "The best match was driven by the degree of data-model overlap observed for the egress lightspot" (On the better model match to the ingress than egress data); "It is additionally possible that a zonal wind profile that varies distinctly from all simulated GCM profiles would provide a better match to the data." (On the better model match to the ingress than egress data)
- Limitation (authors): Longitudinal symmetry excludes possible localized atmospheric events  
  > "assuming longitudinal symmetry excludes possible localized events that could be happening in the atmosphere regions probed by ingress and egress, such as planetary-scale waves." (Conclusions)
- Limitation (authors): HASI lacks temporal and latitudinal resolution  
  > "While the HASI temperature profile lacks temporal and latitudinal resolution, it offers unparalleled altitudinal resolution" (Forward modeling of a stellar occultation)
- Limitation (authors): Omitting methane overestimates bending angles by roughly 0.5% under the stated 1.5% methane assumption  
  > "Omitting methane leads to an overestimation of roughly 0.5% in bending angles, assuming a constant 1.5% concentration of methane at relevant occultation altitudes" (Forward modeling of a stellar occultation)
- Limitation (authors): Mid-event arcs are not reproduced by any tested forward model  
  > "Finally, the mid-event frame shows wider arcs on both the north and south limbs in a pattern that we were unable to reproduce with any of our forward models." (Conclusions)
- Caveat (inferred, ours): The approximate Doppler zero-point correction has no stated uncertainty propagation into the retrieved wind profile.
- Caveat (inferred, ours): Angular SSE ranks models without a stated error-weighted likelihood or significance test.
- Caveat (inferred, ours): The preferred original-amplitude profile differs from the preferred profile across all tested amplitudes; answer keys must distinguish those searches.
- Caveat (inferred, ours): Table 2 reports 29.0 for doubled L_s 240-degree ingress SSE, whereas Table 4 reports 28.9.
- Caveat (inferred, ours): The 303 km average emission altitude, contribution-function peak reference and 307 km GCM reference should not be treated as interchangeable.
- Caveat (inferred, ours): Failure at mid-event limits interpretation of the best-ranked profile as a complete atmospheric solution.
- Caveat (inferred, ours): The source of the specific 8.94 au ALMA plotting distance is not explicitly identified.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Paper-stated ALMA project code, dataset identifiers and public-access statement.
- Missing: Raw/reduced Keck frames, timestamps, selected PSF and frame-selection table.
- Missing: Exact ALMA calibration, self-calibration, continuum subtraction and imaging scripts.
- Missing: Modified wind-retrieval and occultation forward-model source with software versions.
- Missing: Machine-readable retrieved ALMA wind profile and numerical error estimates.
- Missing: The exact TAM snapshots, HASI profile and NEMESIS atmospheric/opacity inputs used.
- Missing: Pressure boundary condition, complete viewing geometry, detector calibration and numerical grids.
- Missing: Lightspot angle measurements, uncertainties and full comparison settings.
- Data volume (inferred): Indeterminate from the text: ALMA antenna count, integration sampling and complete channel counts are absent.
- Score (inferred): 5/5, The paper gives a substantial retrieval and forward-model recipe with numeric comparison tables, but lacks dataset identifiers, software versions, exact processing settings and a release of the modified analysis code and numerical inputs.
- Rediscovery candidate: no, The supplied paper does not state public data availability or an ALMA project code, and essential custom-code inputs and settings remain unspecified despite numeric results.

## Links

- Method: (cite: cordiner_detection_2020) (Doppler wind retrieval strategy and original atmWindMapGaussFit code.)
- Method: (cite: light2024measurements) (Moffat line-profile fitting for CH3CN.)
- Method: (cite: moffat1969theoretical) (Moffat function.)
- Method: (cite: markwardt2009non) (MPFIT least-squares optimization.)
- Method: (cite: 2008JQSRT.109.1136I) (NEMESIS radiative transfer and retrieval.)
- Method: (cite: thelen2019abundance) (Inherited atmospheric spectral-modeling strategy.)
- Method: (cite: lellouch2019intense) (Wind contribution-function frequency weighting.)
- Method: (cite: bouchez_seasonal_2004) (Conversion of zonal winds to level-surface distortions, Equations 4.16–4.26.)
- Method: (cite: Richardson_deconv; lucy_deconv) (Richardson-Lucy image deconvolution.)
- Method: (cite: molter_emolternirc2_reduce_2024) (NIRC2 reduction package.)
- Method: (cite: van_der_walt_scikit-image_2014) (Scikit-Image deconvolution implementation.)
- Method: (cite: ginsburg_image-registration_2023) (Image alignment using shift2d.)
- Method: (cite: matthew_newville_built-fitting_2024) (Gaussian fits to lightspot angular distributions.)
- Method: (cite: casa_2008) (ALMA calibration and imaging software.)

## Checks

```json
{
 "quotes": 196,
 "quotes_ok": 196,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2021.A.00034.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 152,
  "stated": 124,
  "rate": 0.816
 },
 "evidence_ok": true
}
```
