# FAUST: XVIII. Evidence of annular substructure in a very young Class 0 disk

`2024A&A...689L...5M` | Astronomy and Astrophysics 2024 | first author: Maureira, M. J. | arXiv: 2407.20074 | DOI: 10.1051/0004-6361/202451166

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the very young Class 0 disk around Oph A SM1 show annular substructure (gap or ring) in 3 mm dust continuum, and is the emission at that location optically thin?  
  > "To mitigate the problem of optical depth, we investigate substructures within a very young Class 0 disk characterized by a low inclination using observations at longer wavelengths." (abstract); "the 3 mm emission at the location of the possible gap or ring is determined to be optically thin" (abstract)
- Target **Oph A SM1 (SM1)**: coordinates R.A. 16:26:27.852, Dec. -24:23:59.723 (centre from 2D Gaussian fit with imfit)  
  > "Oph A SM1 (hereafter SM1) is located in the Oph A region in the Ophiuchus molecular cloud at a distance of 137 pc (cite: 2018OrtizLeonGaia)." (Introduction); "center coordinates R.A.: 16:26:27.852, Dec.: -24:23:59.723" (Analysis); z/distance 137 pc  
  > "Oph A SM1 (hereafter SM1) is located in the Oph A region in the Ophiuchus molecular cloud at a distance of 137 pc (cite: 2018OrtizLeonGaia)." (Introduction); "center coordinates R.A.: 16:26:27.852, Dec.: -24:23:59.723" (Analysis); distance from (cite: 2018OrtizLeonGaia)  
  > "Oph A SM1 (hereafter SM1) is located in the Oph A region in the Ophiuchus molecular cloud at a distance of 137 pc (cite: 2018OrtizLeonGaia)." (Introduction); "center coordinates R.A.: 16:26:27.852, Dec.: -24:23:59.723" (Analysis)

## Data provenance

- ALMA projects: 2019.1.01074.S, 2018.1.01205.L
- bands: Band 3 (3 mm)  
  > "The ALMA band 3 observations using the C-10 configuration were taken in September 2021." (Data)
- frequencies and spectral setup: four spectral windows, central frequencies between 93 and 105 GHz (C-10 data)  
  > "The spectral setup consisted of four spectral windows with central frequencies between 93 and 105 GHz." (Data)
- continuum bandwidth: 1.875 GHz per spectral window  
  > "the maximum bandwidth of 1.875 GHz for each spectral window was used" (Data)
- arrays: _not stated_
- configurations: C-10 (extended, Cycle 7) combined with C-6 (compact, FAUST)  
  > "The ALMA band 3 observations using the C-10 configuration were taken in September 2021." (Data); "combined with the C-6 configuration of the FAUST" (Data)
- baselines: _not stated_
- angular resolution: 7 au (6.9 au); synthesized beam 0.060 x 0.042 arcsec at PA -79.5 deg  
  > "We use 3 mm ALMA observations tracing dust emission at a resolution of 7 au" (abstract); "We use ALMA observations at 3 mm with a resolution of 6.9 au" (Summary and conclusions)
- max recoverable scale: _not stated_
- sensitivity: 25 uJy/beam rms near SM1  
  > "0.060 ″$\times$0.042 ″ (at PA -79.5$^{\circ}$) and 25 $\mu$Jy beam$^{-1}$, respectively" (Data)
- time on source: _not stated_
- observing dates: September 2021 (C-10)  
  > "taken in September 2021" (Data)
- pi or archival as stated: C-10: Cycle 7 project 2019.1.01074.S (PI M. Maureira); C-6: FAUST Large program 2018.1.01205.L (PI S. Yamamoto)  
  > "Cycle 7 project ID:2019.1.01074.S (PI: M. Maureira)" (Data); "project ID:2018.1.01205.L, PI: S. Yamamoto" (Data)
- Other facility **Spitzer and Herschel/PACS**: Non-detection of the protostar at wavelengths <= 70 micron (literature)  
  > "The protostellar source is not detected at wavelengths $\leq$ 70 $\mu$m by Spitzer or Herschel/PACS" (Introduction)
- External data: Distance to SM1 of 137 pc  
  > "at a distance of 137 pc (cite: 2018OrtizLeonGaia)" (Introduction) [from (cite: 2018OrtizLeonGaia)]
- External data: SED consistent with ~17 K core of 1.3 Msun  
  > "The spectral energy distribution (SED) is consistent with a cold $\sim 17$ K core with a mass of 1.3 M$_\odot$(cite: 2015PattkeOph)." (Introduction) [from (cite: 2015PattkeOph)]
- External data: Maximum internal luminosity of ~1 Lsun from the 70 micron upper limit  
  > "derived a maximum internal luminosity of $\sim$ 1 L$_{\odot}$" (Introduction) [from (cite: 2018FriesenALMA)]
- External data: Dust opacity at 3 mm of ~1 cm2/g  
  > "Using an opacity at 3 mm of $\sim$ 1 cm$^2$ gr$^{-1}$ (cite: 1990beckwithSurvey; 2018Birnsteil)" (Optical depth, temperature, and mass) [from (cite: 1990beckwithSurvey; 2018Birnsteil)]
- External data: 0.8% flux calibration error between spectral windows  
  > "a 0.8% flux calibration error between spectral windows (cite: 2020FrancisFluxCal)" (Optical depth, temperature, and mass) [from (cite: 2020FrancisFluxCal)]
- External data: Gap-width to planet-mass relation (Equation 4)  
  > "Following Equation 4 in (cite: 2016KanagawaMassConstraint)" (Estimation of planetary mass from gap properties) [from (cite: 2016KanagawaMassConstraint)]
- External data: H/R ~0.1-0.3 taken from the IRS 63 derivation  
  > "an aspect ratio H/R$\sim$0.1-0.3 (following the (cite: 2020SeguraCoxRing) derivation for the Class I disk IRS 63)" (Estimation of planetary mass from gap properties) [from (cite: 2020SeguraCoxRing)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 0.8% flux calibration error between spectral windows (systematic 0.1 on spectral index)  
  > "there is a systematic uncertainty at all radii of 0.1 due to a 0.8% flux calibration error between spectral windows" (Optical depth, temperature, and mass)
- self calibration: C-10: phase-only, solint inf down to 10s; C-6: phase then amp+phase self-cal; combined: four phase-only steps then three amplitude steps  
  > "For the extended configuration observations (C-10) we performed phase self-calibration only." (Data self-calibration); "We performed four successive steps of phase-only self-calibration in the combined dataset." (Data self-calibration); "Finally, we performed three steps of amplitude self-calibration" (Data self-calibration)

### Imaging

- task: _not stated_
- deconvolver: multiscale, then mtmfs with nterms=2 for the final phase and amplitude steps  
  > "The cleaning in the self-calibration iterations was done first with the ‘multiscale’ and later with the ‘mtmfs’ deconvolver with nterms$=2$ for the final phase and amplitude steps." (Data)
- weighting robust: robust = 0  
  > "A robust parameter of 0 was set with 4 scales for cleaning in all steps." (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual mask, adjusted when necessary  
  > "A manual mask was set and adjusted during the process when necessary." (Data)
- multiscale scales: 4 scales (values not given)  
  > "A robust parameter of 0 was set with 4 scales for cleaning in all steps." (Data)
- continuum subtraction: _not stated_
- line free channels: C-6 data: line-free channels used for the continuum model (two of seven spectral windows contain line emission); channels not listed  
  > "there were seven spectral windows, two of which contained spectral line emission. Line-free channels were used to obtain a continuum model" (Data self-calibration)
- primary beam correction: _not stated_
- array combination: C-10 and C-6 self-calibrated separately, then combined and self-calibrated together  
  > "We performed self-calibration separately for the observations in the extended and compact configuration, which were then combined and self-calibrated together." (Data)
- smoothing: combined data averaged in time to 9 s bins and in frequency to 30 MHz channels  
  > "We averaged in time in bins of 9 seconds." (Data self-calibration); "The final channel width used was 30 MHz." (Data self-calibration)
- final beam: 0.060 x 0.042 arcsec at PA -79.5 deg  
  > "0.060 ″$\times$0.042 ″ (at PA -79.5$^{\circ}$)" (Data)
- final rms: 25 uJy/beam  
  > "and 25 $\mu$Jy beam$^{-1}$, respectively" (Data)

### Inherited from earlier work

- The 3 mm FAUST C-6 data were observed as part of the FAUST Large program and combined with the new C-10 data  
  > "combined with the C-6 configuration of the FAUST" (Data) [from (cite: 2021CodellaFAUST)]
- Gap and ring models built as a smooth disk with a single carved gap or a single ring  
  > "Following (cite: 2019LongCompact), we modeled these by considering either a smooth disk with a single carved gap or a smooth disk with a single ring exterior to the disk." (Modelling the disk intensity profile) [from (cite: 2019LongCompact)]
- Smooth-disk profile is a modified self-similar profile with distinct inner and outer power-law indices  
  > "we used a modified version of the self-similar profile (cite: 1974LyndenBellEvolution) with distinct power-law indices constraining the inner and outer cutoff behaviors (cite: 2019LongCompact; 2019Manara; 2021TazzariSizes)" (Modelling the disk intensity profile) [from (cite: 1974LyndenBellEvolution); (cite: 2019LongCompact; 2019Manara; 2021TazzariSizes)]
- Intra-band spectral index from lower and upper sideband images  
  > "Following (cite: 2020SeguraCoxRing) and (cite: 2016CiezaImaging), we calculated the intra-band spectral index $\alpha$" (Optical depth, temperature, and mass) [from (cite: 2020SeguraCoxRing); (cite: 2016CiezaImaging)]
- Optical depth and dust temperature from modified blackbody fit of the 106 and 94 GHz profiles; temperature extrapolated with exponent -0.5  
  > "To estimate the optical depth and dust temperature we followed (cite: 2020SeguraCoxRing)" (Optical depth, temperature, and mass); "Following (cite: 2020SeguraCoxRing), we computed the temperature therein by extrapolating the temperature obtained in the optically thick regime" (Optical depth, temperature, and mass) [from (cite: 2020SeguraCoxRing)]
- Planet mass from gap width via the Kanagawa relation, H/R from IRS 63 analysis  
  > "Following Equation 4 in (cite: 2016KanagawaMassConstraint)" (Estimation of planetary mass from gap properties) [from (cite: 2016KanagawaMassConstraint); (cite: 2020SeguraCoxRing)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or a manual calibration was used for each dataset
- Image size and cell size for the final images
- Values of the four multiscale scales
- Line-free channel selection for the C-6 continuum model
- Number of spectral windows and exact solint/combine choices per step for C-10 self-calibration beyond 'inf' to '10s'
- Which channels/spectral windows define the lower- and upper-sideband images and their beams
- Whether the images used for the radial profile are primary-beam corrected (PB response at SM1 is 0.35)
- Radial bin width and number of annuli for the intensity profile
- How the imfit region and the flux calibrator/uncertainty of the individual executions were set
- Exact dust opacity index beta and opacity law used in the modified blackbody fit
- Parameters of the emcee initialization and exact beam used in the convolution

## Analysis recipe

1. **Calibrate, self-calibrate and image the 3 mm continuum**: Self-calibration of C-10 and C-6 separately, then combined, with multiscale then mtmfs cleaning  
  > "We performed self-calibration separately for the observations in the extended and compact configuration, which were then combined and self-calibrated together." (Data)
   - software: CASA
   - parameter: robust = 0, 4 scales, manual mask  
  > "A robust parameter of 0 was set with 4 scales for cleaning in all steps." (Data)
   - parameter: S/N improved by ~40% (C-10) and ~10% (combined)  
  > "signal-to-noise S/N improvements of $\sim$40% and $\sim$10% for the extended configuration only, and combined dataset, respectively" (Data)
   - parameter: Combined data averaged to 9 s and 30 MHz channels  
  > "The final channel width used was 30 MHz." (Data self-calibration)
   - assumption: Primary beam response at SM1 is 0.35 because the field target was VLA 1623-2417  
  > "The primary beam response at the location of SM1 is 0.35 because the target of this field was the Class 0 source VLA 1623-2417." (Data self-calibration)
   - fitting: _not stated_
   - validation: Improvement in image fidelity and S/N after self-calibration  
  > "The self-calibration process improved the overall image fidelity" (Data)
2. **Fit disk geometry**: 2D Gaussian fit to the 3 mm emission to get centre, inclination (circular geometry) and PA  
  > "Using CASA *imfit* we fit a 2D Gaussian to the emission resulting in center coordinates" (Analysis)
   - software: CASA imfit
   - parameter: inclination 15.6 deg, PA 147 +/- 35 deg  
  > "an inclination (assuming circular geometry) of $15.6^{\circ}$ and P.A. of $147\pm35^{\circ}$" (Analysis)
   - assumption: Circular geometry  
  > "an inclination (assuming circular geometry)" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build the deprojected radial intensity profile in brightness temperature**: Deproject with the fitted geometry, azimuthally average, express as brightness temperature with the full Planck function; error sigma_std/sqrt(N)  
  > "We used these values to deproject the emission, and produce an azimuthally averaged radial intensity profile" (Analysis); "The error is calculated as $\sigma_{std}/\sqrt{N}$, where $\sigma_{std}$ and $N$ are the standard deviation and number of beams in each bin." (Analysis)
   - software: velocity_tools coordinate_offsets.py
   - parameter: brightness temperature calculated using the full Planck function  
  > "calculated using the full Planck function" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit smooth, gap and ring models to the intensity profile**: Beam-convolved models fitted with emcee; log of model and data used in the likelihood to weight fractional errors  
  > "Each model was convolved with the synthesized beam and values for each of the parameters were obtained using the Python module `emcee`" (Modelling the disk intensity profile); "The logarithms of the convolved model and the data were used in the likelihood function in order to consider the fractional errors instead of the absolute errors." (Fit of the intensity profiles)
   - software: emcee, scipy fftconvolve
   - parameter: 50 walkers, max 300,000 steps, stop when steps > 100x autocorrelation time and autocorrelation estimate varied < 1%  
  > "We use 50 walkers and run it up to a maximum of 300,000 steps stopping the run when the number of steps was larger than 100$\times$ the autocorrelation time" (Fit of the intensity profiles)
   - parameter: burn-in twice the autocorrelation time, thinning half the autocorrelation time  
  > "The burn-in was computed as twice the autocorrelation time and the chains were thinned using a thinning parameter of half the autocorrelation time." (Fit of the intensity profiles)
   - assumption: Gap and ring each modelled as a Gaussian annular feature  
  > "Both the gap and ring are modeled as a Gaussian." (Modelling the disk intensity profile)
   - fitting: emcee, uniform priors per parameter (Table of priors), log-space likelihood  
  > "We used uniform priors for each parameter" (Fit of the intensity profiles)
   - validation: Residuals compared; chains showed no large-scale variations; corner plots shown  
  > "The resulting chains showed no large-scale variations." (Fit of the intensity profiles)
5. **Compare models**: Akaike Information Criterion; lowest AIC favoured; difference >~10 taken as significant  
  > "The model with the lowest AIC is favored over the others." (Modelling the disk intensity profile)
   - software: astropy akaike_info_criterion
   - parameter: AIC 37.8 (smooth), 21.2 (gap), 19.8 (ring)  
  > "The AIC values are 37.8, 21.2, and 19.8 for the smooth disk, disk with a gap and disk with a ring, respectively." (Modelling the disk intensity profile)
   - fitting: _not stated_
   - validation: Gap and ring models not distinguishable by AIC  
  > "although the AIC value is lower for the model with a ring the difference is not sufficient to favor one of the two non-smooth models" (Modelling the disk intensity profile)
6. **Measure the intra-band spectral index profile**: Image lower- and upper-sideband spectral windows separately with the same imaging parameters, build intensity profiles and compute alpha = ln(I1/I2)/ln(nu1/nu2)  
  > "by imaging the lower-sideband and upper-sideband spectral windows separately, using the parameters for imaging described in Section [2](#sec:data)" (Optical depth, temperature, and mass)
   - software: CASA
   - parameter: nu1 = 106.05 GHz, nu2 = 94.05 GHz  
  > "where $\nu_1$ and $\nu_2$ correspond to 106.05 GHz and 94.05, respectively" (Optical depth, temperature, and mass)
   - parameter: alpha constrained only within ~30 au (beyond that below 3 sigma)  
  > "Due to the limited sensitivity, the profile for $\alpha$ is limited to the inner $\sim$ 30 au." (Optical depth, temperature, and mass)
   - fitting: _not stated_
   - validation: Systematic uncertainty of 0.1 on alpha from flux calibration error between spectral windows  
  > "there is a systematic uncertainty at all radii of 0.1 due to a 0.8% flux calibration error between spectral windows" (Optical depth, temperature, and mass)
7. **Derive dust temperature and 3 mm optical depth**: Modified blackbody fit of the 106 and 94 GHz profiles; in the optically thick inner region temperature equals brightness temperature; outside r~15 au temperature extrapolated with a -0.5 power law  
  > "fit the emission of the profiles at 106 GHz and 94 GHz with a modified blackbody" (Optical depth, temperature, and mass); "assuming a radial profile with a power-law exponent of $-0.5$ (passive heating)" (Optical depth, temperature, and mass)
   - parameter: temperature at gap/ring about 15/13 K, tau(3 mm) below 1  
  > "The temperature in the region with the gap/ring is about 15/13 K while the optical depth at 3 mm is below 1 therein." (Optical depth, temperature, and mass)
   - assumption: Passive heating profile T ~ r^-0.5 beyond ~15 au  
  > "assuming a radial profile with a power-law exponent of $-0.5$ (passive heating)" (Optical depth, temperature, and mass)
   - fitting: _not stated_
   - validation: Tested steeper extrapolation: temperature lower and tau up by up to 20% and 30%, still tau(3 mm) < 1 at gap/ring  
  > "This would still result in $\tau_{3mm}$ below one at the location of the gap/ring feature." (Optical depth, temperature, and mass)
8. **Estimate disk mass and protostar luminosity limit**: M_disk = 2 pi integral Sigma r dr with Sigma = tau/kappa; constant tau_3mm = 8 inside ~15 au, R = 40 au; luminosity from temperature scaling T ~ (phi L)^(1/4)/r^(1/2)  
  > "We used a constant value for $\tau_{3mm}$ of 8 for the inner $\sim$ 15 au region" (Optical depth, temperature, and mass); "In a passive disk the temperature and central source luminosity are related by $T_{mid}(r)\propto(\varphi L_*)^{1/4}/r^{1/2}$" (Optical depth, temperature, and mass)
   - parameter: R = 40 au  
  > "and $R=40$ au to obtain a conservative estimation" (Optical depth, temperature, and mass)
   - assumption: kappa(3 mm) ~ 1 cm2/g and gas-to-dust ratio 100  
  > "and a gas to dust ratio of 100 we estimate a total gas mass of 0.13 M$_\odot$" (Optical depth, temperature, and mass)
   - assumption: Temperature difference to other embedded disks is due only to luminosity (similar flaring, irradiation heating only)  
  > "i.e., flaring is similar for these embedded disks and temperature in this region is set by irradiation only" (Optical depth, temperature, and mass)
   - fitting: _not stated_
   - validation: Mass compared with Class 0 disk masses from 9 mm observations; opacity uncertainty gives factor 2-5  
  > "the derived mass can be higher or lower in a factor of 2-5 due to uncertainties on the dust opacities" (Optical depth, temperature, and mass)
9. **Predict 1.3 mm intensity and optical depth**: Extrapolate tau_3mm to 1.3 mm with constant beta between 1 and 1.7, using the derived temperature profile; also test an inclination of 60 deg  
  > "by extrapolating $\tau_{3mm}$, using constant $\beta$ values between 1 and 1.7, and the temperature profile derived in Section" (Intensity and optical depth predictions at 1.3 mm)
   - parameter: beta = 1 to 1.7  
  > "using constant $\beta$ values between 1 and 1.7" (Intensity and optical depth predictions at 1.3 mm)
   - assumption: Inclination of 60 deg raises optical depth by a factor of about 2  
  > "This inclination corresponds to an increase in optical depth by a factor of about 2." (Intensity and optical depth predictions at 1.3 mm)
   - fitting: _not stated_
   - validation: _not stated_
10. **Estimate possible planet mass from gap width**: Gap width relation from Kanagawa et al. (Eq. 4), cross-checked against Rosotti et al. simulations  
  > "Following Equation 4 in (cite: 2016KanagawaMassConstraint) and assuming $\alpha_{vis}=10^{-3}$" (Estimation of planetary mass from gap properties)
   - parameter: alpha_vis = 1e-3, H/R ~ 0.1-0.3, 1 Msun protostar  
  > "an aspect ratio H/R$\sim$0.1-0.3" (Estimation of planetary mass from gap properties); "and a 1 M$_{\odot}$ protostar" (Estimation of planetary mass from gap properties)
   - assumption: Protostar mass of 1 Msun (unknown); planet mass scales linearly with it  
  > "The planet’s mass scales linearly with the protostar mass." (Estimation of planetary mass from gap properties)
   - fitting: _not stated_
   - validation: Comparable range with Rosotti et al. simulations  
  > "A comparable range is found when compared with the numerical simulations by (cite: 2016RosottiMinimum)." (Estimation of planetary mass from gap properties)

## Software

- **CASA** : Calibration, self-calibration, imaging (tclean-type cleaning with multiscale and mtmfs) and imfit  
  > "We used CASA (cite: 2022CASATeam) to calibrate and image the data." (Data); "Using CASA *imfit* we fit a 2D Gaussian to the emission" (Analysis)
- **emcee** : MCMC fit of beam-convolved intensity-profile models  
  > "values for each of the parameters were obtained using the Python module `emcee`" (Modelling the disk intensity profile)
- **scipy fftconvolve** : Convolution of the models with the beam  
  > "The convolution of the model was done using the function `fftconvolve` from the Python module `scipy.fftconvolve`" (Fit of the intensity profiles)
- **astropy akaike_info_criterion** : AIC computation for model comparison  
  > "https://docs.astropy.org/en/stable/api/astropy.stats.akaike_info_criterion.html" (Analysis)
- **velocity_tools (coordinate_offsets.py)** : Deprojection and azimuthal averaging for the radial intensity profile (linked in a footnote)  
  > "https://github.com/jpinedaf/velocity_tools/blob/master/velocity_tools/coordinate_offsets.py" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 15.6 | not stated | deg | 2 | an inclination (assuming circular geometry) of $15.6^{\circ}$ and P.A. of $147\pm35^{\circ}$ |
| Disk position angle | 147 | 35 | deg | 2 | an inclination (assuming circular geometry) of $15.6^{\circ}$ and P.A. of $147\pm35^{\circ}$ |
| Peak brightness temperature | 57 | not stated | K | 1 | with a brightness temperature peak of 57 K and a 3$\sigma$ contour extending up to $\sim$ 40 au from the center |
| Disk extent (3 sigma contour) | ~40 | not stated | au | 1 | a 3$\sigma$ contour extending up to $\sim$ 40 au from the center |
| Gap radius | 27.9 | +0.6/-0.6 | au | 4 | The models with gap and ring locate the annular substructure at a radius of $27.9^{+0.6}_{-0.6}$ au and $34.4^{+1.7}_{-2.1}$ au, respectively. |
| Ring radius | 34.4 | +1.7/-2.1 | au | 4 | The models with gap and ring locate the annular substructure at a radius of $27.9^{+0.6}_{-0.6}$ au and $34.4^{+1.7}_{-2.1}$ au, respectively. |
| Gap Gaussian width sigma_a | 1.4 | +2.3/-1.2 | au | 4 | The resultant $\sigma_a$ are $1.4^{+2.3}_{-1.2}$ au and $3.9^{+2.0}_{-1.9}$ au, for the gap and the ring, respectively. |
| Ring Gaussian width sigma_a | 3.9 | +2.0/-1.9 | au | 4 | The resultant $\sigma_a$ are $1.4^{+2.3}_{-1.2}$ au and $3.9^{+2.0}_{-1.9}$ au, for the gap and the ring, respectively. |
| Inner power-law index gamma_1 (smooth-profile fit) | ~-0.7 | not stated | dimensionless | 4 | we obtained a power-law exponent value $\gamma_1\sim-0.7$ from the intensity profile fit in the inner region of the disk |
| AIC smooth disk | 37.8 | not stated | dimensionless | 5 | The AIC values are 37.8, 21.2, and 19.8 for the smooth disk, disk with a gap and disk with a ring, respectively. |
| AIC disk with gap | 21.2 | not stated | dimensionless | 5 | The AIC values are 37.8, 21.2, and 19.8 for the smooth disk, disk with a gap and disk with a ring, respectively. |
| AIC disk with ring | 19.8 | not stated | dimensionless | 5 | The AIC values are 37.8, 21.2, and 19.8 for the smooth disk, disk with a gap and disk with a ring, respectively. |
| Spectral index in optically thick inner region (~15 au) | ~2 | not stated | dimensionless | 6 | At about 15 au the spectral index reaches the optically thick limit value of 2 and remains slightly below at small radii. |
| Spectral index outside ~15 au | 3 to 4 | not stated | dimensionless | 6 | Outside this radius it increases reaching values between 3 and 4 |
| Dust temperature at gap / ring location | 15 / 13 | not stated | K | 7 | The temperature in the region with the gap/ring is about 15/13 K while the optical depth at 3 mm is below 1 therein. |
| 3 mm optical depth at gap/ring location | <1 | not stated | dimensionless | 7 | The temperature in the region with the gap/ring is about 15/13 K while the optical depth at 3 mm is below 1 therein. |
| Lower limit on SM1 luminosity | ~0.08 | not stated | Lsun | 8 | The 2$\times$ difference in temperature implies a 16$\times$ lower luminosity for SM1 of $\sim$0.08 $L_{\odot}$. |
| Total gas mass of the disk | 0.13 | factor 2-5 | Msun | 8 | we estimate a total gas mass of 0.13 M$_\odot$(or $\sim$ 430 M$_{\oplus}$ dust mass); the derived mass can be higher or lower in a factor of 2-5 due to uncertainties on the dust opacities |
| Dust mass of the disk | ~430 | factor 2-5 | Mearth | 8 | we estimate a total gas mass of 0.13 M$_\odot$(or $\sim$ 430 M$_{\oplus}$ dust mass) |
| Possible planet mass from gap | few tens to 200 | not stated | Mearth | 10 | we obtain possible planet masses in the range from few tens to 200 M$_{\oplus}$ |

## Qualitative findings

- The 3 mm profile shows a clear intensity deviation near 30 au, reproduced equally well by a gap at ~28 au or a ring at ~34 au; a smooth profile is statistically disfavoured  
  > "non-smooth disk models are statistically preferred over a smooth disk model" (Modelling the disk intensity profile)
- At 1.3 mm the emission would be optically thick (tau > 1) within 40 au, reducing the contrast of the feature  
  > "We predict that the optical depth at 1.3 mm for SM1 would indeed be above one within 40 au of the central source" (Discussion)
- Derived temperature is about 2x lower than in other embedded disks, suggesting a very low luminosity Class 0 protostar (VeLLO) or quiescent accretion  
  > "Thus, it is possible that SM1 is a very low luminosity Class 0 protostar or VeLLO" (Optical depth, temperature, and mass)

## Claim tuples

- H: Annular substructure can already be present in a Class 0 disk | E: Fit smooth, gap and ring models to the deprojected 3 mm radial intensity profile of SM1 with emcee and compare with AIC | R: Gap at 27.9 au or ring at 34.4 au preferred over a smooth disk (AIC 21.2 / 19.8 vs 37.8); gap and ring not distinguishable | F: Evidence for annular substructure in a very young Class 0 disk | **supported**
- H: The feature is not an artifact of high optical depth | E: Intra-band spectral index and modified blackbody fit of the 94 and 106 GHz profiles to get tau and T | R: tau(3 mm) below 1 at the gap/ring location, T about 15/13 K | F: The 3 mm emission at the feature is optically thin | **supported**
- H: Observing at 1.3 mm would hide such a feature | E: Extrapolate tau_3mm to 1.3 mm with beta 1-1.7 and the derived temperature profile, plus a 60 deg inclination case | R: tau(1.3 mm) above 1 within 40 au; reduced contrast and a spurious bump at 15-25 au | F: Substructure detection is harder at 1.3 mm and for higher inclination | **partially**
- H: SM1 is a low-luminosity, very young Class 0 protostar with a massive disk | E: Compare derived disk temperature with other embedded disks and estimate disk mass from tau_3mm | R: Luminosity ~0.08 Lsun; gas mass 0.13 Msun (dust ~430 Mearth) | F: SM1 may be a VeLLO or quiescent Class 0 source; solid mass is consistent with other Class 0 disks | **partially**

## Reasoning

- Why this data: Longer wavelength (3 mm) and low inclination chosen to mitigate high optical depth that can hide substructure  
  > "To mitigate the problem of optical depth, we investigate substructures within a very young Class 0 disk characterized by a low inclination using observations at longer wavelengths." (abstract)
- Why this method: Radial profiles of disks are usually described by a truncated power law, so a smooth profile is the null model against which a gap or ring is tested  
  > "Radial intensity profiles of disks are usually well described by a power-law in radius for the inner part, which is then truncated in the outer disk" (Analysis)
- Alternative: Smooth disk model excluded by AIC  
  > "The smooth disk model can be excluded based on the significant difference" (Modelling the disk intensity profile)
- Alternative: Changes in dust opacity at icelines (e.g. N2 iceline near the gap/ring temperature) or grain-size variation or planet-induced pressure bumps also considered as origins  
  > "other scenarios that could potentially lead to the observed deviation in the intensity profile of SM1 are changes in the dust opacity at the location of icelines" (Discussion)
- How they decided it was enough: AIC difference >~10 taken as significant to exclude the smooth model; gap vs ring left open when difference is small  
  > "although the AIC value is lower for the model with a ring the difference is not sufficient to favor one of the two non-smooth models" (Modelling the disk intensity profile)
- Limitation (authors): Gap model degenerate between a deep narrow and a shallow broad gap; higher resolution needed  
  > "there is a degeneracy between models with a deep and narrow gap or a shallow broad one as both lead to a similar profile once convolved with the beam" (Fit of the intensity profiles); "Higher resolution observations are required to improve the constrains on the gap morphology." (Fit of the intensity profiles)
- Limitation (authors): Spectral index unconstrained beyond ~30 au due to limited sensitivity  
  > "Beyond this radius $\alpha$ values are smaller than the $3\sigma$ statistical uncertainty, leaving $\alpha$ unconstrained." (Optical depth, temperature, and mass)
- Limitation (authors): Disk mass uncertain by factor 2-5 from dust opacity; planet mass should not be over-interpreted  
  > "the derived mass can be higher or lower in a factor of 2-5 due to uncertainties on the dust opacities" (Optical depth, temperature, and mass); "We should be cautious not to overinterpret these values given the number of unknown parameters." (Estimation of planetary mass from gap properties)
- Caveat (inferred, ours): Single object and a single 3 mm image; gap vs ring cannot be distinguished (delta AIC ~1.4)
- Caveat (inferred, ours): Gap/ring significance rests on the radial-profile model choice and a log-likelihood with bin errors sigma/sqrt(N); beam-correlated pixels may make the errors underestimated
- Caveat (inferred, ours): Temperature outside 15 au is an extrapolation of a -0.5 power law, so tau and mass depend on that assumption
- Caveat (inferred, ours): Disk mass uses tau = 8 constant and kappa = 1 cm2/g; large opacity uncertainty
- Caveat (inferred, ours): Sensitivity to the self-calibration of a combined C-10 + C-6 dataset at a primary-beam response of 0.35 is not tested for imaging artifacts

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version, calibration pipeline details and flux calibrators
- Missing: Image and cell size, multiscale scale values, line-free channels
- Missing: Radial binning of the intensity profile
- Missing: Exact beams for the sideband images and the opacity/beta treatment in the temperature fit
- Missing: Analysis scripts are not released (only a third-party helper script is linked)
- Data volume (inferred): Large: two ALMA Band 3 datasets (C-10 and a FAUST C-6 Large Program field); likely tens of GB of raw visibilities
- Score (inferred): 3/5, Project codes and the self-calibration recipe are given and results are numeric, but CASA version, image/cell size, scales, channel selection and binning are not stated and no code is released.
- Rediscovery candidate: yes, Both project codes are stated and the data are ALMA archive projects; the self-calibration, profile fitting and AIC steps are described with numeric results, though imaging details need to be inferred.

## Links

- Method: (cite: 2020SeguraCoxRing) (Method for spectral index, dust temperature and optical depth in an embedded disk)
- Method: (cite: 2019LongCompact) (Gap and ring intensity-profile models)
- Method: (cite: 2016KanagawaMassConstraint) (Planet mass from gap width)
- Companion: (cite: 2021CodellaFAUST) (FAUST Large program providing the C-6 data)
- Companion: (cite: 2018FriesenALMA) (Earlier ALMA study of SM1 (CO outflow, infall, luminosity limit))
- Related: FAUST ALMA Large Program (2018.1.01205.L)
- Related: DSHARP
- Related: ODISEA

## Checks

```json
{
 "quotes": 141,
 "quotes_ok": 141,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 122,
  "stated": 93,
  "rate": 0.762
 },
 "evidence_ok": true
}
```
