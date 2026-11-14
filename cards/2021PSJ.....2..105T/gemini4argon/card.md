# Neptune's Spatial Brightness Temperature Variations from the VLA and ALMA

`2021PSJ.....2..105T` | The Planetary Science Journal 2021 | first author: Tollefson, Joshua | arXiv: 2104.06554 | DOI: 10.3847/PSJ/abf837

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Retrieve H2S, NH3, and CH4 abundance profiles across Neptune's disk from ~1 bar to ~50 bar using spatially resolved VLA and ALMA radio maps.  
  > "We use radiative transfer modeling coupled to Markov Chain Monte Carlo methods to retrieve H 2 S, NH 3, and CH 4 abundance profiles across the disk, though only strong constraints can be made for H 2 S." (abstract)
- Target **Neptune**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00859.S
- bands: ALMA 1-3 mm (including Band 6); VLA Bands Ka (0.9 cm), Ku (2.0 cm), X (3.0 cm), C (5.1 cm), S (9.7 cm)  
  > "Maps were obtained at wavelengths of 0.9 cm (Band Ka), 2.0 cm (Band Ku), 3.0 cm (Band X), 5.1 cm (Band C), and 9.7 cm (Band S)." (2.1. Data); "The radio observations analyzed here only reach frequencies as high as 242 GHz (ALMA Band 6), meaning only the wings of the absorption line are detectable." (3.3.1. Phosphine (PH 3 )); "Models are fit to data from both the VLA presented in this work and 1 − 3 mm ALMA maps from Tollefson et al. (2019)." (6. CONCLUSIONS)
- frequencies and spectral setup: ALMA: 95.012, 96.970, 107.000, 109.000, 135.986, 137.924, 147.986, 149.986, 223.982, 225.982, 239.981, 241.981 GHz; VLA: 3.096-42.827 GHz  
  > "95.012 ALMA 07-Jul-2017 126 . 6 ± 6 . 3 121.6 0.1" (Table 2); "135.986 ALMA 08-Oct-2016 108 . 5 ± 5 . 4 105.8 0.3" (Table 2); "241.981 ALMA 24-Oct-2016 92 . 8 ± 4 . 6 89.8 0.6" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.1'' - 1.0''  
  > "We present spatially resolved (0 . 1 [′′] − 1 . 0 [′′] ) radio maps of Neptune taken from the Very Large Array and Atacama Large Submillimeter/Millimeter Array between 2015 − 2017." (abstract)
- max recoverable scale: _not stated_
- sensitivity: ALMA sky RMS: 0.1-0.6 K; VLA sky RMS: 0.4-2.0 K  
  > "RMS values range from 0 . 4 − 2 . 0K and are similar to the RMS at a given latitude within the disk of a residual map." (2.3. Error estimation); "95.012 ALMA 07-Jul-2017 126 . 6 ± 6 . 3 121.6 0.1" (Table 2); "241.981 ALMA 24-Oct-2016 92 . 8 ± 4 . 6 89.8 0.6" (Table 2)
- time on source: _not stated_
- observing dates: ALMA: 08-Oct-2016, 24-Oct-2016, 07-Jul-2017; VLA: 01-Sep-2015, 02-Sep-2015 (and 2003)  
  > "95.012 ALMA 07-Jul-2017 126 . 6 ± 6 . 3 121.6 0.1" (Table 2); "135.986 ALMA 08-Oct-2016 108 . 5 ± 5 . 4 105.8 0.3" (Table 2); "223.982 ALMA 24-Oct-2016 93 . 4 ± 4 . 7 92.1 0.4" (Table 2)
- pi or archival as stated: ALMA data from Tollefson et al. (2019); new 2015 VLA observations  
  > "This work makes use of two primary data sets: 1) ALMA millimeter observations of Neptune taken from 2016 2017, described in Section 2 of Tollefson et al. (2019); 2) centimeter observations of Neptune taken with the upgraded VLA taken in 2015, described below." (2.1. Data)
- Line: PH3 1-0 (266.9 GHz)
- Other facility **Very Large Array (VLA)**: Centimeter continuum maps of Neptune at 0.9, 2.0, 3.0, 5.1, and 9.7 cm from September 2015 (and archival 2003 maps from 0.7 to 6 cm).  
  > "We observed Neptune with the expanded VLA, an interferometer located near Socorro, New Mexico, on 1 and 2 September, 2015." (2.1. Data); "Maps were obtained at wavelengths of 0.9 cm (Band Ka), 2.0 cm (Band Ku), 3.0 cm (Band X), 5.1 cm (Band C), and 9.7 cm (Band S)." (2.1. Data); "We supplement these observations with VLA maps in 2003 from de Pater et al. (2014) in order to model Neptune’s disk-average temperature." (2.1. Data)
- External data: ALMA millimeter observations of Neptune from 2016-2017  
  > "This work makes use of two primary data sets: 1) ALMA millimeter observations of Neptune taken from 2016 2017, described in Section 2 of Tollefson et al. (2019); 2) centimeter observations of Neptune taken with the upgraded VLA taken in 2015, described below." (2.1. Data) [from Tollefson et al. (2019)]
- External data: VLA 2003 centimeter maps of Neptune  
  > "We supplement these observations with VLA maps in 2003 from de Pater et al. (2014) in order to model Neptune’s disk-average temperature." (2.1. Data) [from de Pater et al. (2014)]
- External data: Voyager 2 temperature of 71.5 K at 1 bar and equatorial/polar radii  
  > "Resolution at sub-observer location, assuming equatorial and polar radii of 24,766 km and 24,323 km, respectively (Lindal 1992)." (Table 1); "Temperature profiles are calculated from deep in the atmosphere upward, assuming either a dry or wet adiabat such that the profile matches the Voyager 2 temperature of 71.5 K at 1 bar (Lindal 1992)." (3.1. Temperature Profile) [from Lindal (1992)]
- External data: Temperature profile at pressures shallower than 1 bar derived from mid-infrared inversions  
  > "At pressures shallower than 1 bar, the temperature profile follows that derived from mid-infrared inversions by Fletcher et al. (2014)." (3.1. Temperature Profile) [from Fletcher et al. (2014)]
- External data: Protosolar elemental abundances (C/H2, N/H2, O/H2, S/H2)  
  > "We use the protosolar values from Asplund et al. (2009): C/H 2 = 5.90E-4; N/H 2 = 1.48E-4; O/H 2 = 1.07E-3; S/H 2 = 2.89E-5." (3.1. Temperature Profile) [from Asplund et al. (2009)]
- Simulation/model as data: Radio-BEAR synthetic radiative transfer spectra of Neptune's atmosphere  
  > "We generate models of Neptune’s brightness temperature using the radiative transfer (RT) code Radio-BEAR [2] ." (3. MODELING)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C48 (for VLA; ALMA calibration in Tollefson et al. 2019)  
  > "The calibrators used were 3C48 (flux density) and J2246-1206 (phase)." (2.2. Calibration and Imaging)
- flux scale uncertainty: 5%  
  > "Uncertainties in the flux density are estimated at 5% or less in each band so we use this as a conservative estimate for the absolute error in our disk-averaged temperature data." (2.3. Error estimation); "The listed errors are the absolute errors, estimated at 5% from the calibrators." (Table 2)
- self calibration: Phase self-calibration using a limb-darkened disk model (VLA)  
  > "In addition, self-calibration was performed to correct for short-term variability in the phases caused by fast atmospheric fluctuations. The self-calibration model used was a limb-darkened disk that best matched the observations." (2.2. Calibration and Imaging)

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
- final rms: ALMA: 0.1-0.6 K; VLA: 0.4-2.0 K  
  > "RMS values range from 0 . 4 − 2 . 0K and are similar to the RMS at a given latitude within the disk of a residual map." (2.3. Error estimation); "95.012 ALMA 07-Jul-2017 126 . 6 ± 6 . 3 121.6 0.1" (Table 2); "241.981 ALMA 24-Oct-2016 92 . 8 ± 4 . 6 89.8 0.6" (Table 2)

### Inherited from earlier work

- ALMA millimeter observations, calibration, and imaging of Neptune  
  > "This work makes use of two primary data sets: 1) ALMA millimeter observations of Neptune taken from 2016 2017, described in Section 2 of Tollefson et al. (2019); 2) centimeter observations of Neptune taken with the upgraded VLA taken in 2015, described below." (2.1. Data) [from Tollefson et al. (2019)]
- Radio-BEAR model atmosphere construction, absorption coefficients, and line profiles  
  > "For a fuller description of Radio-BEAR, we refer the reader to de Pater et al. (2005), de Pater et al. (2014), and de Pater et al. (2019), which outline how the model atmosphere is constructed from bottom-up and details the absorption coefficients and line profiles for the species in this work." (3. MODELING) [from de Pater et al. (2005), de Pater et al. (2014), and de Pater et al. (2019)]
- Cosmic microwave background (CMB) correction procedure for interferometric disk-averaged brightness temperatures  
  > "The CMB correction is applied following the procedure laid out in Appendix A of de Pater et al. (2014)." (4.1. Disk-Averaged Profiles) [from de Pater et al. (2014)]
- MCMC Gaussian log-likelihood formulation and uniform/log-uniform priors  
  > "We use similar log-likelihood Gaussian function and uniform/log-uniform priors as these authors; letting θ represent the free parameters in the model, the likelihood function ln p is:" (3.5. Retrievals) [from de Kleer et al. (2015); Luszcz-Cook et al. (2016)]

### Not stated but needed to reproduce (our reading)

- Complete ALMA data reduction, calibration, self-calibration, and imaging parameters (inherited from Tollefson et al. 2019)
- Exact MIRIAD imaging parameters for the VLA data (weighting/robustness, cell size, deconvolution algorithm, self-calibration solution intervals)
- Exact prior bounds (minimum and maximum values) for all free parameters in the emcee MCMC retrievals
- Exact values of the limb-darkening parameters Tb and k at each wavelength used for self-calibration and residual map subtraction

## Analysis recipe

1. **Calibrate and image VLA observations and construct residual maps and latitude bins**: Flag, calibrate, self-calibrate against a limb-darkened disk model (Tb cos^k theta), and image VLA data in MIRIAD; subtract best-fit limb-darkened disks and divide Neptune into seven latitude bins.  
  > "Flagging, calibration, and imaging were performed within MIRIAD." (2.2. Calibration and Imaging); "The self-calibration model used was a limb-darkened disk that best matched the observations." (2.2. Calibration and Imaging); "We divide Neptune into seven regions where the transitions in the brightness temperature variations are apparent: 90 [◦] S − 66 [◦] S, 66 [◦] S − 50 [◦] S, 50 [◦] S − 36 [◦] S, 36 [◦] S − 12 [◦] S, 12 [◦] S − 4 [◦] N, 4 [◦] N − 20 [◦] N, 20 [◦] N − 50 [◦] N." (2.2. Calibration and Imaging)
   - software: MIRIAD
   - parameter: Seven latitude bins: 90S-66S, 66S-50S, 50S-36S, 36S-12S, 12S-4N, 4N-20N, 20N-50N  
  > "We divide Neptune into seven regions where the transitions in the brightness temperature variations are apparent: 90 [◦] S − 66 [◦] S, 66 [◦] S − 50 [◦] S, 50 [◦] S − 36 [◦] S, 36 [◦] S − 12 [◦] S, 12 [◦] S − 4 [◦] N, 4 [◦] N − 20 [◦] N, 20 [◦] N − 50 [◦] N." (2.2. Calibration and Imaging)
   - assumption: Equatorial and polar radii of 24,766 km and 24,323 km (Lindal 1992)  
  > "Resolution at sub-observer location, assuming equatorial and polar radii of 24,766 km and 24,323 km, respectively (Lindal 1992)." (Table 1)
   - assumption: Flux density calibration uncertainty of 5% in each band  
  > "Uncertainties in the flux density are estimated at 5% or less in each band so we use this as a conservative estimate for the absolute error in our disk-averaged temperature data." (2.3. Error estimation)
   - fitting: Minimize difference between limb-darkened model disk (Tb * cos^k(theta)) and observations at each wavelength  
  > "Values for T b and k were found at each wavelength such that the difference between the limb-darkened model disk and observations were minimized." (2.2. Calibration and Imaging)
   - validation: Measure random noise RMS across four sky boxes equal to Neptune's diameter and compare with residual map RMS  
  > "The random noise in our VLA maps is calculated by averaging over four regions of the sky with boxes equal to the diameter of Neptune and taking the root-mean-square (RMS)." (2.3. Error estimation)
2. **Extract disk-averaged and zonally-averaged brightness temperatures**: Sum flux density within Neptune's disk plus three model beam diameters past the limb and apply CMB correction for disk averages; average pixels within +/- 60 degrees of sub-observer longitude for latitude bands.  
  > "We calculate Neptune’s disk-average brightness temperature by totaling the flux density contained within Neptune’s disk plus the area extending out three times the model beam diameter past the limb." (4.1. Disk-Averaged Profiles); "The CMB correction is applied following the procedure laid out in Appendix A of de Pater et al. (2014)." (4.1. Disk-Averaged Profiles); "The brightness temperatures fed into MCMC are obtained by averaging over all pixels that are within ± 60 degrees of the sub-observer longitude at each latitude band." (4.2. 36 ◦ S − 12 ◦ S and 90 ◦ S − 66 ◦ S Profiles)
   - parameter: Aperture radius for disk average: disk plus 3x model beam diameter past limb  
  > "We calculate Neptune’s disk-average brightness temperature by totaling the flux density contained within Neptune’s disk plus the area extending out three times the model beam diameter past the limb." (4.1. Disk-Averaged Profiles)
   - parameter: Longitude averaging window: +/- 60 degrees of sub-observer longitude  
  > "The brightness temperatures fed into MCMC are obtained by averaging over all pixels that are within ± 60 degrees of the sub-observer longitude at each latitude band." (4.2. 36 ◦ S − 12 ◦ S and 90 ◦ S − 66 ◦ S Profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **Perform radiative transfer forward modeling and MCMC atmospheric retrievals for disk-average and south pole / mid-latitude regions**: Couple Radio-BEAR radiative transfer models to emcee MCMC sampler to retrieve deep H2S, NH3, CH4 abundances, H2S relative humidity, P_mix, PH3, and H2 state for disk-averaged data and simultaneously for 90S-66S and 36S-12S.  
  > "We generate models of Neptune’s brightness temperature using the radiative transfer (RT) code Radio-BEAR [2] ." (3. MODELING); "In order to estimate uncertainties in our model parameters, we couple our Radio-BEAR models to Markov Chain Monte Carlo (MCMC) simulations via a python implementation of the Goodman & Weare (2010) ensemble sampler called emcee (Foreman et al. 2013)." (3.5. Retrievals); "The retrieved probability density functions for the condensible abundances below P mix are then used as priors for the condensible abundance below the NH 4 SH cloud in the cold mid-latitude band between 36 [◦] S − 12 [◦] S." (4.2. 36 ◦ S − 12 ◦ S and 90 ◦ S − 66 ◦ S Profiles)
   - software: Radio-BEAR, emcee
   - parameter: 30 walkers, 4000-5000 steps, 50% burn-in  
  > "We use 30 walkers and let MCMC run for between 4000 − 5000 steps." (3.5. Retrievals); "The burn-in phase ends after 50% of the steps have been completed." (3.5. Retrievals)
   - parameter: PSF-scale convolution correction factor and free error parameter sigma_PSF = sigma * T * S  
  > "The ratio of the PSF convolved disk-averaged model temperature to that without convolution is called the PSF-scale. We multiply each MCMC retrieved model by the PSF-scale to obtain our final model brightness temperature incorporating the effect of convolution." (3.5. Retrievals); "σ P SF = σ · T · S, (3)" (3.5. Retrievals)
   - assumption: Hydrostatic equilibrium and local thermodynamic equilibrium; wet or dry adiabat matching 71.5 K at 1 bar (Voyager 2) and Fletcher et al. (2014) above 1 bar  
  > "Temperature profiles are calculated from deep in the atmosphere upward, assuming either a dry or wet adiabat such that the profile matches the Voyager 2 temperature of 71.5 K at 1 bar (Lindal 1992)." (3.1. Temperature Profile); "Temperatures, pressures, and altitudes are related through hydrostatic equilibrium. We assume that the atmosphere is in local thermodynamic equilibrium." (3.1. Temperature Profile)
   - assumption: Cloud opacity is ignored; gas opacity dominated by H2S, NH3, H2O, and CIA of H2 (H2-H2, H2-He, H2-CH4)  
  > "Therefore, we ignore the effect of cloud opacity in our modeling and focus instead on the effect of gas opacity." (3.2. Cloud Structure); "The gas opacity of the microwave spectrum for gas giant atmospheres is dominated by H 2 S, NH 3, H 2 O, and the collision-induced absorption (CIA) of H 2 (we include: H 2 -H 2, H 2 -He, and H 2 -CH 4 ) (de Pater & Mitchell 1993)." (3.3. Condensible Species)
   - assumption: NH4SH cloud chemistry follows Lewis (1969); aqueous solution cloud removes 5% of interior H2S and 25% of interior NH3; protosolar abundances from Asplund et al. (2009)  
  > "We use the protosolar values from Asplund et al. (2009): C/H 2 = 5.90E-4; N/H 2 = 1.48E-4; O/H 2 = 1.07E-3; S/H 2 = 2.89E-5." (3.1. Temperature Profile); "In our model, the formation of the NH 4 SH cloud is governed by equilibrium chemistry described in Lewis (1969)." (3.3. Condensible Species); "For the nominal abundances, the solution cloud in full thermochemical equilibrium removes about 5% of the interior H 2 S and 25% of the interior NH 3 ." (3.3. Condensible Species)
   - fitting: MCMC ensemble sampling (emcee) maximizing Gaussian log-likelihood (Eq. 1) with uniform/log-uniform priors  
  > "In order to estimate uncertainties in our model parameters, we couple our Radio-BEAR models to Markov Chain Monte Carlo (MCMC) simulations via a python implementation of the Goodman & Weare (2010) ensemble sampler called emcee (Foreman et al. 2013)." (3.5. Retrievals); "We use similar log-likelihood Gaussian function and uniform/log-uniform priors as these authors; letting θ represent the free parameters in the model, the likelihood function ln p is:" (3.5. Retrievals)
   - validation: Autocorrelation time checked against step count; posterior distributions inspected after 50% burn-in; south polar fit compared against 2003 VLA data  
  > "This run length ensured that the autocorrelation time was sufficiently shorter than the number of steps." (3.5. Retrievals); "to south polar 2003 VLA data are overplotted as well, showing good agreement." (4.2 36S-12S and 90S-66S Profiles)
4. **Simultaneously retrieve latitudinal variations relative to 36S-12S and compare thermal models**: Simultaneously fit absolute brightness temperatures in 36S-12S and temperature differences Delta T_b between 36S-12S and other latitude bands using Eq. 4, allowing H2S subsaturation or supersaturation up to P_ss, and compare wet vs dry adiabats using the Deviance Information Criterion (DIC).  
  > "In this section, we simultaneously model the atmospheric properties matching both the observed brightness temperature within the 36 _[◦]_ S _−_ 12 _[◦]_ S latitudinal band" (4.3 Globally-Varying Profiles - Mitigating Systematic Uncertainty); "H 2 S may be supersaturated up to a pressure P ss . At altitudes shallower than P ss, the H 2 S profile follows the saturation curve with 100% relative humidity." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty); "A measure of the improvement in the fit between two models is the Deviance Information Criterion (DIC, Spiegelhalter et al. (2002))." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty)
   - software: Radio-BEAR, emcee
   - parameter: Reference latitude band: 36S-12S; compared bands: 90S-66S, 66S-50S, 50S-36S, 12S-4N, 4N-20N  
  > "Latitude Bin: 90◦S−66◦S 66◦S−50◦S 50◦S−36◦S 12◦S−4◦N 4◦N−20◦N" (Table 7)
   - parameter: No PH3 and fully intermediate H2 assumed at all latitudes  
  > "We assume no PH 3 and fully intermediate H 2 at all latitudes as we do not expect to be sensitive to these parameters given our prior findings (Table 6)." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty)
   - assumption: Differential uncertainty sigma_Delta includes 5% of Delta T_b, sky RMS per root number of beams in each band, and sigma_PSF (Eq. 6)  
  > "The first term on the right-hand side is the difference in brightness temperature between the reference and modeled latitude band times the 5% calibration error. σ RMS is the random error on the sky divided by the square root of the number of beams that fit within the reference and modeled latitude bands." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty)
   - fitting: Joint Gaussian log-likelihood (Eq. 4) on T_b(36S-12S) and Delta T_b; model selection via DIC (Eq. 7) and variable lapse rate models in Appendix .2  
  > "The first sum on the right-hand side is the same as equation (1) and represents the fit to the observed brightness temperature at 36 [◦] S − 12 [◦] S with errors dominated by systematic calibration. The second sum represents the brightness temperature difference between 36 [◦] S − 12 [◦] S and the other latitudinal band:" (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty); "Differences greater than 10 favor the model with the lower DIC score." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty); "We run three models fitting ∆ T b between 66 [◦] S-50 [◦] S and 36 [◦] S-12 [◦] S." (.2. Varying Temperature and Trace Gas Abundances with MCMC)
   - validation: Consistency of retrieved 36S-12S parameters across all pairwise latitude runs; DIC comparison; Appendix .2 lapse rate retrieval and chi-squared check  
  > "Moreover, the retrieved parameters for the 36 [◦] S − 12 [◦] S band are consistent between model runs to within uncertainties, indicating this approach is self-consistent." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty); "Figure A5 plots the χ [2] goodness-of-fit as a function of wavelength for the best fitting spectra in each of the three models considered." (.2. Varying Temperature and Trace Gas Abundances with MCMC)

## Software

- **MIRIAD** : Flagging, calibration, self-calibration, and imaging of the VLA observations  
  > "The VLA observations were loaded from the NRAO data archive and converted for use in the MIRIAD software package (Sault et al. 1995). Flagging, calibration, and imaging were performed within MIRIAD." (2.2. Calibration and Imaging)
- **Radio-BEAR** : Radiative transfer forward modeling of Neptune's synthetic microwave brightness temperature spectra  
  > "We then combine these new VLA maps with 2003 VLA and ALMA observations of Neptune and use a Markov chain Monte Carlo (MCMC) implementation of the radiative transfer code Radio BErkeley Atmospheric Radiative transfer (Radio-BEAR) to obtain retrievals for the abundance profiles of Neptune’s condensibles (Section 4)." (1. INTRODUCTION); "We generate models of Neptune’s brightness temperature using the radiative transfer (RT) code Radio-BEAR [2] ." (3. MODELING)
- **emcee** : Markov Chain Monte Carlo ensemble sampling coupled to Radio-BEAR for atmospheric parameter retrievals  
  > "In order to estimate uncertainties in our model parameters, we couple our Radio-BEAR models to Markov Chain Monte Carlo (MCMC) simulations via a python implementation of the Goodman & Weare (2010) ensemble sampler called emcee (Foreman et al. 2013)." (3.5. Retrievals)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deep H2S abundance below all clouds (dry adiabat) | 1.3e-3 | +0.4e-3/-0.3e-3 | dimensionless | 3 | 1 _._ 3 [+0] _−_ 0 _[.]_ _._ [4] 3 _[×]_ [ 10] _[−]_ [3] [(53] _[.]_ [8] [+18] _−_ 13 _[.]_ _._ [9] 4 _[×]_ [protosolar)] [for] [a] [dry] [adiabat.] |
| Deep H2S protosolar enrichment below all clouds (dry adiabat) | 53.8 | +18.9/-13.4 | x protosolar | 3 | Below all cloud formation, the data are well fit by 53 . 8 [+18] − 13 [.] . [9] 4 [×] [ and 3] [.] [9] − [+2] 3 [.] . [1] 1 [×] [ protosolar] enrichment in the H 2 S and NH 3 abundances, respectively, assuming a dry adiabat. |
| Deep NH3 abundance below all clouds (dry adiabat) | 4.7e-4 | +2.5e-4/-3.7e-4 | dimensionless | 3 | We obtain loose bounds on the NH 3 abundance: 2 . 5 [+2] − 2 [.] . [7] 3 [×] [10] [−] [4] [(2] [.] [1] [+2] − 1 [.] . [3] 9 [×] [ protosolar) for a wet adiabat and 4] [.] [7] − [+2] 3 [.] . [5] 7 [×] [10] [−] [4] [(3] [.] [9] [+2] − 3 [.] . [1] 1 [×] [ protosolar)] for a dry adiabat. |
| Deep NH3 protosolar enrichment below all clouds (dry adiabat) | 3.9 | +2.1/-3.1 | x protosolar | 3 | Below all cloud formation, the data are well fit by 53 . 8 [+18] − 13 [.] . [9] 4 [×] [ and 3] [.] [9] − [+2] 3 [.] . [1] 1 [×] [ protosolar] enrichment in the H 2 S and NH 3 abundances, respectively, assuming a dry adiabat. |
| Deep H2S abundance below all clouds (wet adiabat) | 8.7e-4 | +2.6e-4/-1.7e-4 | dimensionless | 3 | Below all cloud formation, we obtain H 2 S abundances of 8 _._ 7 [+2] _−_ 1 _[.]_ _._ [6] 7 _[×]_ [10] _[−]_ [4] [(37] _[.]_ [3] [+15] _−_ 10 _[.]_ _._ [7] 3 _[×]_ [ protosolar)] |
| Deep NH3 abundance below all clouds (wet adiabat) | 2.5e-4 | +2.7e-4/-2.3e-4 | dimensionless | 3 | We obtain loose bounds on the NH 3 abundance: 2 . 5 [+2] − 2 [.] . [7] 3 [×] [10] [−] [4] [(2] [.] [1] [+2] − 1 [.] . [3] 9 [×] [ protosolar) for a wet adiabat and 4] [.] [7] − [+2] 3 [.] . [5] 7 [×] [10] [−] [4] [(3] [.] [9] [+2] − 3 [.] . [1] 1 [×] [ protosolar)] for a dry adiabat. |
| Disk-averaged H2S below all clouds (wet adiabat) | 6.6e-4 | +2.0e-4/-1.3e-4 | dimensionless | 3 | H2S below all clouds 6.6+2.0 −1.3 × 10−4 28.2+8.5 −5.4 |
| Disk-averaged H2S below all clouds (dry adiabat) | 9.3e-4 | +2.1e-4/-2.2e-4 | dimensionless | 3 | H2S below all clouds 9.3+2.1 −2.2 × 10−4 39.4+9.9 −9.4 |
| South polar cap mixing pressure P_mix (90S-66S, dry adiabat) | 33 | +6/-4 | bar | 3 | Pmix 33+6 −4 bar — |
| South polar cap mixing pressure P_mix (90S-66S, wet adiabat) | 41 | +9/-7 | bar | 3 | Pmix 41+9 −7 bar — |
| PH3 abundance 2-sigma upper limit (36S-12S, dry adiabat) | <= 4.4e-7 | 2 sigma upper limit | dimensionless | 3 | PH3 ≤4.4 × 10−7 ≤0.1; Our retrievals are consistent with a PH 3 2 σ upper limit of 0.4 ppm ( ≤ 0 . 1 × protosolar). |
| Total Deviance Information Criterion (DIC) difference (wet minus dry adiabat) | +95 | not stated | dimensionless | 4 | Wet Adiabat DIC 177 152 145 134 173 781; Dry Adiabat DIC 151 134 130 116 155 689; Diﬀerence +26 +18 +15 +18 +18 +95 |

## Qualitative findings

- Neptune's south polar region (90S-66S) is 5-40 K brighter than the mid-latitudes and northern equatorial region depending on wavelength, consistent with subsiding air depleted in H2S and NH3 down to ~33-41 bar.  
  > "the south polar region is 5 40 K brighter than the mid-latitudes and northern equatorial region." (abstract); "The downwelling south polar cap (90 [◦] S − 66 [◦] S) is consistent with depleted H 2 S and NH 3 down to a mixing pressure P mix around the NH 4 SH cloud formation: ∼ 33 bar." (6. CONCLUSIONS)
- Neptune's observable sulfur-to-nitrogen (S/N) ratio exceeds unity, as H2S is more abundant than NH3 in every retrieval and removes all NH3 at the NH4SH cloud layer near 50 bar.  
  > "Our results imply that Neptune’s sulfur-to-nitrogen ratio exceeds unity as H 2 S is more abundant than NH 3 in every retrieval." (abstract); "Using the H 2 S/NH 3 ratio as a proxy for the S/N ratio, we completely rule out observable S/N ratios less than unity." (5. DISCUSSION)
- A global dry adiabatic temperature profile is statistically favored over a wet adiabat across Neptune's latitude bands.  
  > "The dry adiabat is statistically favored everywhere, apart from 50 [◦] S − 36 [◦] S where neither thermal profile is favored." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty); "A global dry adiabat is preferred over a wet adiabat as a warmer thermal profile is statistically favored in models fitting brightness temperature variations across the disk." (6. CONCLUSIONS)
- H2S abundance above the NH4SH cloud decreases poleward from the equator and southern mid-latitudes, requiring H2S supersaturation at 36S-12S (and possibly 4N-20N) if the thermal profile is globally uniform.  
  > "However, above NH 4 SH formation, the H 2 S abundance decreases poleward, mirroring brightness temperature increases poleward (Fig. 1)." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty); "Supersaturated H 2 S between 36 [◦] S − 12 [◦] S and possibly between 4 [◦] N − 20 [◦] N is required to obtain good fits to the observed brightness temperature variations if the thermal profile is fixed globally." (5. DISCUSSION)
- Neither the deep CH4 abundance nor the ortho/para H2 fraction can be constrained by the radio data, and no spectral evidence of PH3 is found.  
  > "The abundance of CH 4 is unconstrained due to its limited impact on the microwave opacity longward of 1 cm." (6. CONCLUSIONS); "We find no spectral evidence of PH 3 ." (6. CONCLUSIONS); "We cannot constrain the ortho/para H 2 fraction anywhere on Neptune." (6. CONCLUSIONS)

## Claim tuples

- H: Neptune's deep atmospheric H2S abundance exceeds its NH3 abundance, yielding a bulk observable S/N ratio greater than unity. | E: Couple Radio-BEAR radiative transfer models with emcee MCMC to retrieve deep H2S and NH3 abundances from combined ALMA (1-3 mm) and VLA (0.9-9.7 cm) brightness temperature spectra. | R: Below all cloud formation (dry adiabat), H2S is 53.8 (+18.9/-13.4) x protosolar and NH3 is 3.9 (+2.1/-3.1) x protosolar; H2S exceeds NH3 in every retrieval. | F: Neptune's observable S/N ratio is strictly greater than unity, with all NH3 consumed in forming the NH4SH cloud near 50 bar. | **supported**
- H: Latitudinal brightness temperature variations on Neptune are driven by spatial variations in condensible gas opacity, including H2S supersaturation in cold bands and depletion at the south pole, rather than kinetic temperature variations alone. | E: Simultaneously fit brightness temperature differences Delta T_b between 36S-12S and other latitude bands using MCMC, and test models varying lapse rate with and without H2S supersaturation. | R: Above the NH4SH cloud, H2S decreases poleward and is depleted down to P_mix ~ 33 bar at 90S-66S; fitting the 0.9 cm datum at 36S-12S requires H2S supersaturation or >=8 K localized temperature anomalies near 10 bar, while retrieved temperature differences at 5 bar are consistent with 0 K (<1 K). | F: Meridional variations in H2S and NH3 opacity explain Neptune's brightness temperature bands, and models with H2S supersaturation at 36S-12S (and possibly 4N-20N) are statistically favored over strict thermochemical equilibrium. | **supported**
- H: Neptune's global tropospheric temperature-pressure profile follows a dry adiabat rather than a wet adiabat. | E: Compare MCMC retrievals assuming global wet and dry adiabats across five latitude band pairs using the Deviance Information Criterion (DIC), and retrieve the lapse rate directly as a free parameter. | R: The total DIC score is 689 for the dry adiabat versus 781 for the wet adiabat (difference +95), and free lapse rate retrievals yield ~1.11-1.17 K/km, matching a dry adiabat and enabling H2S cloud tops consistent with Irwin et al. (2019a). | F: A global dry adiabatic thermal profile is statistically favored over a wet adiabat on Neptune. | **supported**

## Reasoning

- Why this data: Upgraded VLA centimeter maps (5-20x improved continuum sensitivity) combined with ALMA millimeter maps probe from ~1 bar to ~50 bar across the CH4, H2S, and NH4SH cloud decks at 0.1''-1.0'' spatial resolution.  
  > "In 2011, an upgrade of the VLA was completed. This expansion improved the continuum sensitivity by 5-to-20-fold and increased the wavelength coverage and bandwidth." (1. INTRODUCTION); "The mm and cm probe between ∼ 1 − 50 bar on Neptune, meaning the most complete picture of Neptune’s upper atmosphere to date can be reconstructed by synthesizing these data." (1. INTRODUCTION)
- Why this method: Coupling Radio-BEAR to emcee MCMC provides full posterior uncertainty distributions on atmospheric parameters (unlike forward model chi-squared ruling out in Tollefson et al. 2019), PSF-scale avoids expensive 2D disk convolutions at every MCMC step, and fitting differential temperatures Delta T_b mitigates the 5% flux calibration error.  
  > "A downside to this approach is that one can only rule out models which are improbable from χ [2] -statistics, meaning uncertainties are not retrieved." (3.5. Retrievals); "This effect is hard to model while conducting MCMC for two reasons: convolving the whole disk with the PSF is computationally expensive; and the model composition of the surrounding latitudes must be simultaneously known in order to obtain the exact temperature distribution across the disk." (3.5. Retrievals); "One shortcoming of the analysis in the previous section is that the calibration error masks the evident brightness variations across the disk." (4.3 Globally-Varying Profiles - Mitigating Systematic Uncertainty)
- Alternative: Purely kinetic temperature variations (with globally uniform nominal trace gas abundances) or variable lapse rates without H2S supersaturation as the cause of latitudinal brightness temperature variations  
  > "If the kinetic temperature were the sole cause of the brightness temperature variations, then substantial local variations on the order of 8K or greater are required." (.1. Globally Uniform Temperature Profiles); "Allowing latitudinal temperature variations without H 2 S supersaturation (models 1 and 2) can not explain all the observed data." (.2. Varying Temperature and Trace Gas Abundances with MCMC)
- How they decided it was enough: 30 walkers run for 4000-5000 steps ensured the autocorrelation time was sufficiently shorter than the number of steps, with 50% discarded as burn-in; DIC differences > 10 used for model selection.  
  > "We use 30 walkers and let MCMC run for between 4000 − 5000 steps. This run length ensured that the autocorrelation time was sufficiently shorter than the number of steps." (3.5. Retrievals); "Differences greater than 10 favor the model with the lower DIC score." (4.3. Globally-Varying Profiles - Mitigating Systematic Uncertainty)
- Limitation (authors): High degree of longitudinal smearing in the maps because Neptune was observed over nearly a full 16.11 hr rotation period.  
  > "Neptune throughout nearly an entire 16.11 hr rotation period (Warwick et al. 1989)." (2.1 Data)
- Limitation (authors): Cloud opacity is ignored in the radiative transfer modeling.  
  > "Therefore, we ignore the effect of cloud opacity in our modeling and focus instead on the effect of gas opacity." (3.2. Cloud Structure)
- Limitation (authors): Observations only extend to 9.7 cm, so NH3 below the NH4SH cloud (~50 bar) cannot be probed directly and is only weakly constrained via chemical coupling with H2S.  
  > "Therefore, while NH 3 and H 2 O are strong microwave absorbers, they are only abundant deeper than ∼ 40 bar and only impact Neptune’s radio spectrum significantly at wavelengths longer than 10 cm." (3.3. Condensible Species); "While NH 3 can not be probed directly with our wavelength coverage, the chemical connection between H 2 S and NH 3 means its abundance can be inferred." (3.3. Condensible Species)
- Limitation (authors): Deep CH4 abundance, PH3 abundance, and ortho/para H2 state cannot be strongly constrained due to calibration uncertainties and competing opacity effects in the millimeter.  
  > "Note, however, that our ability to retrieve the deep CH 4 abundance is limited compared to that of H 2 S. This is due to a combination of having less overall impact on the microwave opacity, lower than our calibration errors, and other sources like the H 2 S relative humidity, PH 3, and the H 2 state having comparable or stronger effects in the mm." (3.6. Atmospheric Models and Free Parameters)
- Limitation (authors): Evidence for H2S supersaturation when allowing lapse rate to vary relies heavily on a single 0.9 cm data point.  
  > "While the 0.9 cm datum is just one point of evidence in favor of supersaturated H 2 S, it can not be explained away by an error in calibration, as discussed in Section 4.3." (.2. Varying Temperature and Trace Gas Abundances with MCMC)
- Caveat (inferred, ours): ALMA data from 2016-2017 and VLA data from 2015 (plus 2003 VLA for disk-average) are non-simultaneous, assuming no temporal variability in Neptune's brightness temperature structure across 2015-2017.
- Caveat (inferred, ours): The 1D PSF-scale approximation used in MCMC calculates beam smearing from a uniform limb-darkened disk rather than self-consistently convolving a 2D latitudinally banded model at each MCMC step.
- Caveat (inferred, ours): Degeneracy between kinetic temperature profile and trace gas opacity is only partially broken, and the statistical preference for H2S supersaturation over lapse-rate variations hinges on the 0.9 cm VLA band.

## Reproducibility

- Data public (paper): VLA data available from the NRAO Science Data Archive (program VLA/15A-118); ALMA project code ADS/JAO.ALMA#2016.1.00859.S stated.  
  > "This paper makes use of the following VLA data from program VLA/15A-118." (ACKNOWLEDGMENTS); "VLA data used in this report are available from the NRAO Science Data Archive at https://archive.nrao.edu/archive/advquery.jsp." (ACKNOWLEDGMENTS); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00859.S." (ACKNOWLEDGMENTS)
- Products in archive: _not stated_
- Code: Radio-BEAR radiative transfer code available on GitHub at https://github.com/david-deboer/radiobear  
  > "This code is available at: https://github.com/david-deboer/radiobear ." (3. MODELING)
- Missing: Tabulated zonally-averaged brightness temperatures T_b and uncertainties for each of the seven latitude bins at all VLA and ALMA frequencies (only plotted in Fig. 2, 7, 8, 9, 10; only disk-averaged T_b is tabulated in Table 2)
- Missing: Exact PSF-scale multiplicative factors for each latitude bin and wavelength
- Missing: Exact prior distributions and bounds for all MCMC free parameters
- Missing: Scripts coupling Radio-BEAR to emcee and implementing the specific cloud/chemistry parameterizations
- Data volume (inferred): A few tens of GB for the raw VLA (15A-118) and ALMA (2016.1.00859.S) visibility datasets; <100 MB for the calibrated continuum maps and MCMC chains.
- Score (inferred): 72/5, Raw VLA and ALMA project codes and the core radiative transfer code (Radio-BEAR) are publicly available, and disk-averaged brightness temperatures are tabulated in Table 2; however, ALMA processing is deferred to Tollefson et al. (2019), exact zonally-averaged brightness temperatures per latitude bin are not tabulated, and MCMC prior bounds and wrapper scripts are not provided.
- Rediscovery candidate: yes, Both the ALMA (2016.1.00859.S) and VLA (15A-118) datasets and the Radio-BEAR code are public, Table 2 provides a complete numeric benchmark for the disk-averaged spectrum, and the main atmospheric retrieval results are quantitative.

## Links

- Method: Sault et al. 1995 (MIRIAD software package used for flagging, calibration, and imaging of VLA observations)
- Method: de Pater et al. (2005), de Pater et al. (2014), and de Pater et al. (2019) (Radio-BEAR radiative transfer code description, model atmosphere construction, absorption coefficients, line profiles, and CMB correction)
- Method: Foreman et al. 2013; Goodman & Weare 2010 (emcee Python MCMC ensemble sampler used for atmospheric retrievals)
- Method: de Kleer et al. 2015; Luszcz-Cook et al. 2016 (MCMC Gaussian log-likelihood formulation and uniform/log-uniform priors)
- Method: Spiegelhalter et al. (2002) (Deviance Information Criterion (DIC) used for statistical model comparison)
- Companion: Tollefson et al. (2019) (Presents the primary 2016-2017 ALMA 1-3 mm observations of Neptune combined with VLA data in this work)
- Companion: de Pater et al. (2014) (Presents the 2003 VLA centimeter observations of Neptune used to supplement the disk-averaged and south polar analyses)
- Related: VLA/15A-118

## Checks

```json
{
 "quotes": 140,
 "quotes_ok": 140,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 19,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 64,
  "rate": 0.681
 },
 "evidence_ok": true
}
```
