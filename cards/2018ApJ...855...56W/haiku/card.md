# Resolved Millimeter Observations of the HR 8799 Debris Disk

`2018ApJ...855...56W` | The Astrophysical Journal 2018 | first author: Wilner, David J. | arXiv: 1803.00054 | DOI: 10.3847/1538-4357/aaacd7

Card schema 1.0 | model claude-haiku-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks
- Question: Measure the structure of the cold planetesimal belt around HR 8799 at 1.3 mm with SMA data combined with archival ALMA data, use the inner edge to constrain the mass of planet b, and use a 9 mm VLA flux with the 1.3 mm flux to constrain the grain size distribution.  
  > "We present 1.3 millimeter observations of the debris disk surrounding the HR 8799 multi-planet system from the Submillimeter Array" (abstract); "this inner edge location translates into a constraint on the planet b mass of" (abstract)
- Target **HR 8799**: coordinates 23h07m28.72s, +21d08m03.3s (J2000) SMA phase center  
  > "The young (cite: malo13) and nearby (cite: van07) A-type star HR 8799 is the host of the first (and so far only) directly imaged multiple planet system." (Introduction); "The phase center was set at" (Observations / Submillimeter Array); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00482.S
- bands: ALMA Band 6 (1.3 mm, archival); SMA near 1.3 mm; VLA 9 mm (Ka-band range 30-36 GHz)  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (Observations / Atacama Large Millimeter/submillimeter Array); "We observed the HR 8799 system with the VLA at 9 mm wavelength in the most compact D configuration." (Observations / Very Large Array)
- frequencies and spectral setup: SMA: bands ±(4-12) GHz from LO 225.5 GHz, 140 kHz channels; ALMA: four spectral windows of 2 GHz, 16 MHz channels, centered 216, 218, 231, 233 GHz; VLA: 4 bands centered 30, 32, 34, 36 GHz  
  > "together spanned bands ±(4-12) GHz from the LO frequency of 225.5 GHz, with uniform channel spacing 140 kHz" (Observations / Submillimeter Array); "four spectral windows with width 2 GHz and channel spacing 16 MHz, centered at 216, 218, 231 and 233 GHz" (Observations / Atacama Large Millimeter/submillimeter Array); "comprised of 4 bands centered at 30, 32, 34, and 36 GHz, for two polarizations" (Observations / Very Large Array)
- continuum bandwidth: SMA 16 GHz; ALMA 2 GHz per window after averaging; VLA 8 GHz  
  > "This setup provided a total of 16 GHz of continuum bandwidth" (Observations / Submillimeter Array); "The correlator was used to obtain the maximum continuum bandwidth of 8 GHz" (Observations / Very Large Array)
- arrays: SMA (subcompact configuration, 6 m antennas); ALMA (12 m antennas); VLA (27 antennas, 25 m)  
  > "in the subcompact configuration that provides projected baselines as short as 6 meters" (Observations / Submillimeter Array); "The primary beam FWHM size of the 12-meter diameter array antennas" (Observations / Atacama Large Millimeter/submillimeter Array)
- configurations: SMA subcompact; ALMA not stated; VLA D configuration  
  > "in the most compact D configuration" (Observations / Very Large Array)
- baselines: SMA 6-69 m (6-45 m on 2016 Sep 21); ALMA 15-349 m; VLA 0.04-1.03 km  
  > "The observations included baseline lengths from 15 to 349 meters." (Observations / Atacama Large Millimeter/submillimeter Array); "The baselines ranged from 0.04 to 1.03 km." (Observations / Very Large Array)
- angular resolution: SMA+ALMA combined image 3.8 arcsec (150 AU); ALMA-only beam about 1.5 arcsec; VLA 6.2 x 5.8 arcsec  
  > "The image morphology at 3.8'' (150 AU) resolution indicates an optically thin circumstellar belt" (abstract); "with a beam size of 1.5'' , and it shows a noisy ring of emission surrounding the star." (Results and Analysis / Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: VLA 9 mm rms noise 4.3 μJy/beam (taper 5 arcsec); ALMA image noise an order of magnitude lower than SMA  
  > "and rms noise of 4.3" (Results and Analysis / Continuum Emission)
- time on source: SMA: 2 min on each quasar loop, 10 min on target per loop; VLA: 5 min on HR 8799 per 1 min gain cal cycle  
  > "and 10 minutes on the target source HR 8799" (Observations / Submillimeter Array); "interleaved 1 minute observations of the complex gain calibrator 3C454.3 with 5 minute observations on HR 8799" (Observations / Very Large Array)
- observing dates: SMA 2016 Aug 17 to 2016 Sep 21 (six tracks); ALMA 2015 January (five scheduling blocks); VLA early 2017 (4 dates)  
  > "Table [1](#tab:sma) provides a log of these observations, including the observing dates" (Observations / Submillimeter Array); "on 4 dates in early 2017" (Observations / Very Large Array)
- pi or archival as stated: SMA and VLA observations obtained for this work; ALMA data archival  
  > "to complement archival ALMA observations that spatially filtered away the bulk of the emission" (abstract)
- Line: 12CO J=2-1 (230.53800 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Other facility **Submillimeter Array (SMA)**: New 1.3 mm observations of the HR 8799 system in the subcompact configuration  
  > "We observed the HR 8799 system with the SMA on Mauna Kea, Hawaii, at a wavelength near 1.3 millimeters" (Observations / Submillimeter Array)
- Other facility **Karl G. Jansky Very Large Array (VLA)**: New 9 mm continuum observations used to measure the spectral index  
  > "We also present new 9 millimeter observations of the debris disk from the Very Large Array" (abstract)
- External data: Archival ALMA Band 6 observations of HR 8799 whose calibrated data are reused and whose observations are described in that paper  
  > "Details of these observations are described in (cite: booth16)." (Observations / Atacama Large Millimeter/submillimeter Array) [from (cite: booth16)]
- External data: Flux density of about 3.5 mJy at 1.3 mm predicted from submillimeter observations, used as Gaussian prior on total belt flux for ALMA-only fit  
  > "motivated by submillimeter observations (cite: matthews14) that predict a flux density of" (SMA/ALMA Disk Model Fits) [from (cite: matthews14)]
- External data: Disk inclination of 26 +/- 3 deg from ellipticity of far-infrared (Herschel) outer edge  
  > "lower (and more precise) disk inclination of" (System Geometry) [from (cite: matthews14)]
- External data: Disk position angle of 64 +/- 3 deg from far-infrared emission  
  > "with the latter yielding a higher value of" (System Geometry) [from (cite: matthews14)]
- External data: Typical spectral index of debris disks (2.5) and sample weighted mean grain size index q = 3.36 +/- 0.02 for 15 debris disks  
  > "This result is consistent with the weighted mean value of" (Grain Size Distribution) [from (cite: macgregor16)]
- External data: Inner edge of millimeter belt in SED modeling, used for comparison only  
  > "or from the ALMA data alone (cite: booth16), both of which suffer from substantial systematic uncertainty" (Dynamical Constraints on the Mass of Planet b) [from (cite: su09)]
- External data: Stellar mass 1.56 Msun and planet b semi-major axis 68 AU from dynamical analysis  
  > "from dynamical analysis (cite: soummer11)" (Dynamical Constraints on the Mass of Planet b) [from (cite: soummer11)]
- External data: Dust opacity power-law index beta_s = 1.8 +/- 0.2 for interstellar grain materials  
  > "for interstellar grain materials (cite: draine06)" (Grain Size Distribution) [from (cite: draine06)]

## Processing

### Calibration

- pipeline or manual: Mixed: SMA via MIR standard procedures; ALMA via archive CASA reduction scripts re-run; VLA via VLA pipeline processing  
  > "All of the basic calibration was performed using standard procedures in the MIR software package." (Observations / Submillimeter Array); "We calibrated the five individual scheduling block executions using the associated" (Observations / Atacama Large Millimeter/submillimeter Array); "The basic calibration was done using VLA pipeline processing" (Observations / Very Large Array)
- casa version: CASA 4.7.2 for SMA and VLA; CASA 4.3.1 reduction scripts for archival ALMA  
  > "software package (version 4.7.2)" (Observations / Submillimeter Array); "4.3.1 reduction scripts" (Observations / Atacama Large Millimeter/submillimeter Array)
- pipeline version: _not stated_
- archive products used as is: No: archival ALMA scheduling blocks were recalibrated and averaged in this work  
  > "We calibrated the five individual scheduling block executions" (Observations / Atacama Large Millimeter/submillimeter Array)
- flux calibrator: SMA: Uranus in each track (bandpass 3C454.3 and Uranus); VLA: 3C48 in each execution; ALMA not stated  
  > "The absolute flux scale was set using observations of Uranus obtained in each track" (Observations / Submillimeter Array); "The absolute flux scale was set with observations of the standard calibrator 3C48 in each execution" (Observations / Very Large Array)
- flux scale uncertainty: 10% overall for SMA and 10% for VLA  
  > "with 10% overall accuracy" (Observations / Submillimeter Array); "with an estimated accuracy of 10%" (Observations / Very Large Array)
- self calibration: _not stated_

### Imaging

- task: CASA clean task (SMA, ALMA, VLA); tclean not mentioned  
  > "Imaging was carried out with the" (Observations / Atacama Large Millimeter/submillimeter Array)
- deconvolver: clean  
  > "Fourier inversion for continuum and spectral line imaging and" (Observations / Submillimeter Array)
- weighting robust: natural weighting for continuum and 13CO images  
  > "These images were obtained with natural weighting" (Results and Analysis / Continuum Emission)
- uv taper: 4 arcsec FWHM Gaussian taper for SMA-including continuum and 13CO; 5 arcsec for VLA  
  > "those including SMA data use a 4'' FWHM Gaussian taper to improve surface brightness sensitivity" (Results and Analysis / Continuum Emission); "obtained with natural weighting and a 5'' FWHM Gaussian taper" (Results and Analysis / Continuum Emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: ALMA: channels containing CO line emission flagged before continuum output; SMA line-free selection not stated  
  > "Continuum visibilities were output for analysis after flagging the channels with CO line emission" (Observations / Atacama Large Millimeter/submillimeter Array)
- primary beam correction: VLA correction for primary beam attenuation negligible; model multiplied by primary beam response of each telescope in fits  
  > "correction for primary beam attenuation is negligible" (VLA 9 millimeter Flux Estimate); "the model emission is multiplied by the appropriate primary beam response of each telescope" (SMA/ALMA Disk Model Fits)
- array combination: SMA and ALMA visibilities jointly fit; combined image uses SMA with ALMA data  
  > "and then fit the observations from both telescopes simultaneously" (SMA/ALMA Disk Model Fits)
- smoothing: _not stated_
- final beam: 3.8 arcsec for combined SMA+ALMA image  
  > "The image morphology at 3.8'' (150 AU) resolution indicates an optically thin circumstellar belt" (abstract)
- final rms: 4.3 μJy/beam for VLA 9 mm image; other rms not stated  
  > "and rms noise of 4.3" (Results and Analysis / Continuum Emission)

### Inherited from earlier work

- ALMA observation setup and processing details taken from the earlier paper describing the archival data  
  > "Details of these observations are described in (cite: booth16)." (Observations / Atacama Large Millimeter/submillimeter Array) [from (cite: booth16)]
- Visibility fitting procedure for axisymmetric belt models  
  > "we model the observations using the visibility fitting procedure described in (cite: macgregor13)" (SMA/ALMA Disk Model Fits) [from (cite: macgregor13)]
- Background-source flux prior and offset location from prior Herschel and JCMT imaging  
  > "Since imaging with both Herschel (cite: matthews14) and JCMT (cite: holland17) shows the presence of a compact background source" (SMA/ALMA Disk Model Fits) [from (cite: matthews14); (cite: holland17)]
- Flux density prior of 3.0-4.0 mJy for ALMA-only fit, motivated by prior submillimeter predictions  
  > "motivated by submillimeter observations (cite: matthews14) that predict a flux density of" (SMA/ALMA Disk Model Fits) [from (cite: matthews14)]
- Chaotic-zone truncation formula R_in = a_pl + 5 a_pl (M_pl/3M*)^(1/3) adopted for planet mass constraint  
  > "If we adopt the (cite: pearce14) formula" (Dynamical Constraints on the Mass of Planet b) [from (cite: pearce14)]
- Millimeter spectral index to grain size index conversion with beta_s=1.8 and interstellar grain opacity  
  > "for interstellar grain materials (cite: draine06)" (Grain Size Distribution) [from (cite: draine06)]

### Not stated but needed to reproduce (our reading)

- Calibrated SMA visibility data and calibration tables (MIR outputs) are not provided, so the SMA calibration cannot be redone from the paper alone
- CASA imaging parameters (cell size, image size, mask, number of iterations, threshold) for the SMA, ALMA and VLA images are not given
- ALMA archival calibration choices beyond re-running the scripts (flagging, time/frequency averaging for the final visibilities other than 30 s and 2 GHz) are only partly given
- Continuum subtraction or the line-free channel selection for the SMA continuum is not stated
- Initial parameter values, walker starting positions and prior bounds for the combined SMA+ALMA fit are not stated
- Background point-source prior ranges and its treatment in the combined fit are not stated
- Whether the SMA and ALMA continuum images use the same spectral window selection and weighting when combined is not stated
- Distance to HR 8799 used in the physical scale conversion (150 AU at 3.8 arcsec) is not given
- Gas-to-dust ratio, dust temperature for the 9 mm and 1.3 mm fluxes beyond 39.7 K is not stated for the spectral index
- Aperture radius and background region for the VLA flux measurement are not stated

## Analysis recipe

1. **calibrate and image the 1.3 mm and 9 mm continuum**: Calibrate SMA data with MIR procedures and image with clean; calibrate archival ALMA executions with archive scripts and average to 30 s and 2 GHz; calibrate VLA with pipeline and image with clean; combine SMA and ALMA with a 4 arcsec taper  
  > "Continuum visibilities were output in 30 second scans spanning 4 GHz widths" (Observations / Submillimeter Array); "averaging in time to 30 seconds, and averaging in frequency to 2 GHz bandwidth" (Observations / Atacama Large Millimeter/submillimeter Array)
   - software: CASA, MIR
   - parameter: natural weighting; 4 arcsec Gaussian taper for combined image; 30 s time averaging; 2 GHz frequency averaging for ALMA  
  > "These images were obtained with natural weighting" (Results and Analysis / Continuum Emission)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Residual image after subtracting best-fit model visibilities is noise-like, interpreted as a good fit  
  > "The goodness-of-fit is demonstrated by the noise-like residual image." (SMA/ALMA Disk Model Fits)
2. **fit an axisymmetric radial power-law belt to the visibilities with MCMC**: Model an axisymmetric, geometrically thin belt with radial power-law surface brightness between R_in and R_out, primary beam multiplied, plus an unresolved background point source for SMA and joint fits; compute synthetic visibilities with vissample and fit by chi-square likelihood with emcee  
  > "we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt" (SMA/ALMA Disk Model Fits); "we calculate synthetic visibilities using vissample" (SMA/ALMA Disk Model Fits)
   - software: vissample, emcee
   - parameter: uniform priors: 0 < R_in < R_out, F_belt > 0, -3 < x < 3 for SMA-only fit  
  > "we adopt uniform priors for all parameters, in particular" (SMA/ALMA Disk Model Fits)
   - parameter: ALMA-only fit uses Gaussian prior on total belt flux 3.0 to 4.0 mJy and logistic prior on R_out with k=-10 and x0=512 AU  
  > "we implemented a logistic function" (SMA/ALMA Disk Model Fits)
   - parameter: background point source omitted for ALMA-only fit because of primary beam attenuation  
  > "When modeling the ALMA data alone, this additional background source is omitted on account of primary beam attenuation at the offset location." (SMA/ALMA Disk Model Fits)
   - assumption: Belt geometry is axisymmetric and geometrically thin; belt is optically thin  
  > "indicates an optically thin circumstellar belt" (abstract)
   - assumption: Proper motion of 0.20 arcsec between SMA and ALMA epochs ignored  
  > "the small proper motion of HR 8799 between SMA and ALMA observing epochs" (SMA/ALMA Disk Model Fits)
   - fitting: emcee ensemble MCMC; ln L = -chi^2/2 incorporating visibility weights; 50,000 iterations; best fit and 68 percent uncertainties from marginalized posteriors  
  > "We explore the posterior with 50,000 iterations" (SMA/ALMA Disk Model Fits); "Table [2](#tab:par) lists the best-fit parameters from each of these fits" (SMA/ALMA Disk Model Fits)
   - validation: Gelman-Rubin statistic below 1.1 for all parameters  
  > "check that the Gelman-Rubin statistic (cite: gelman14) is" (SMA/ALMA Disk Model Fits)
3. **measure the 9 mm VLA flux density of the disk**: Measure the flux density in a circular aperture centered on the disk with the diameter from the 1.3 mm belt model; uncertainty from ten random apertures  
  > "we measure the flux density in CASA within a circular aperture centered at the location of the disk" (VLA 9 millimeter Flux Estimate); "at ten random locations in the image and taking the average" (VLA 9 millimeter Flux Estimate)
   - software: CASA
   - parameter: aperture diameter from combined SMA+ALMA belt model; disk detected only at about 3 sigma per beam  
  > "assuming the diameter of the disk determined from the combined modeling of the SMA and ALMA data" (VLA 9 millimeter Flux Estimate)
   - assumption: Disk diameter from belt model applied to VLA image  
  > "assuming the diameter of the disk determined from the combined modeling of the SMA and ALMA data" (VLA 9 millimeter Flux Estimate)
   - fitting: not stated; image-based aperture photometry, no model fit to 9 mm visibilities  
  > "we do not apply the same MCMC modeling technique to these data" (VLA 9 millimeter Flux Estimate)
   - validation: Uncertainty from average flux in ten random apertures  
  > "at ten random locations in the image and taking the average" (VLA 9 millimeter Flux Estimate)
4. **derive the millimeter spectral index and grain size power-law index**: Compute spectral index from best-fit 1.3 mm total flux and 9 mm flux; convert to grain size index q using beta_s and Planck spectral index  
  > "we use the best-fit total flux density from the combined SMA and ALMA models at 1.3 millimeters and the VLA flux density measured at 9 millimeters" (Grain Size Distribution)
   - parameter: q = (alpha_mm - alpha_Pl)/beta_s + 3, valid for 3<q<4; beta_s = 1.8 +/- 0.2; alpha_Pl = 1.92 +/- 0.10  
  > "In this expression, valid for 3<q<4" (Grain Size Distribution)
   - assumption: Dust temperature 39.7 K assumed for HR 8799  
  > "the 39.7 K dust temperature assumed for HR 8799" (Grain Size Distribution)
   - assumption: Interstellar grain materials for opacity; small grain limit beta_s  
  > "for interstellar grain materials (cite: draine06)" (Grain Size Distribution)
   - fitting: _not stated_
   - validation: Consistency with weighted mean q of other debris disks  
  > "This result is consistent with the weighted mean value of" (Grain Size Distribution)
5. **convert belt inner edge into a mass for planet b**: Translate the posterior of R_in into planet b mass using the chaotic-zone truncation formula of Pearce and Wyatt, assuming planet b truncates the belt  
  > "Figure [7](#fig:planet_mass) shows the result of this translation of the inner radius posterior distribution from our modeling, assuming planet b truncates the belt." (Dynamical Constraints on the Mass of Planet b)
   - parameter: a_pl = 68 AU; M_* = 1.56 Msun  
  > "For this calculation, we adopt the planet semi-major axis" (Dynamical Constraints on the Mass of Planet b)
   - assumption: Zero eccentricity limit of chaotic zone formula; planet b truncates the planetesimal belt  
  > "taken in the limit of zero eccentricity" (Dynamical Constraints on the Mass of Planet b)
   - fitting: Translation of R_in posterior distribution (no separate fit stated)  
  > "translate the radial location of the inner edge of the millimeter belt" (Dynamical Constraints on the Mass of Planet b)
   - validation: Comparison with hot-start and warm-start planet cooling models  
  > "compatible with standard planet cooling models" (Dynamical Constraints on the Mass of Planet b)
6. **infer the planetesimal surface density slope from the surface brightness index**: Convert best-fit surface brightness index x to a surface density index assuming a radial temperature profile for radiative equilibrium  
  > "to approximate radiative equilibrium with stellar heating" (Stirring Mechanisms)
   - parameter: T(r) proportional to r^-0.5  
  > "If we assume a radial temperature profile" (Stirring Mechanisms)
   - assumption: Radial temperature profile T proportional to r^-0.5  
  > "If we assume a radial temperature profile" (Stirring Mechanisms)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (SMA, VLA); 4.3.1 (archival ALMA scripts): Imaging with clean for SMA, ALMA and VLA continuum, VLA pipeline processing, statwt weight homogenization, and aperture flux measurement  
  > "software package (version 4.7.2)" (Observations / Submillimeter Array); "to homogenize the visibility weights among scheduling blocks" (Observations / Atacama Large Millimeter/submillimeter Array); "we measure the flux density in CASA within a circular aperture" (VLA 9 millimeter Flux Estimate)
- **MIR** : Basic calibration of the SMA observations  
  > "All of the basic calibration was performed using standard procedures in the MIR software package." (Observations / Submillimeter Array)
- **vissample** : Computing synthetic visibilities from model images for the MCMC fit  
  > "a python package for visibility sampling that improves on the sampling and interpolation of the" (SMA/ALMA Disk Model Fits)
- **emcee** : MCMC sampling of the posterior probability distribution of the belt model parameters  
  > "to sample the posterior probability distribution of the data conditioned on the model" (SMA/ALMA Disk Model Fits)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total belt flux density, SMA+ALMA joint fit | 3.44 | +0.31/-0.56 | mJy | 2 | $3.44 (+0.31, - 0.56)$ |
| Belt inner edge radius, SMA+ALMA joint fit | 104 | +8/-12 | AU | 2 | The models constrain the radial location of the inner edge of the belt to |
| Belt outer edge radius, SMA+ALMA joint fit | 361 | +16/-18 | AU | 2 | $361. (+16., -18.)$ |
| Surface brightness power law index x, SMA+ALMA joint fit | -0.38 | +/-0.47 | dimensionless | 2 | the best-fit power law index for the millimeter emission radial profile is |
| Disk inclination, SMA+ALMA joint fit | 32.8 | +5.6/-9.6 | deg | 2 | constrain the millimeter belt inclination |
| Disk position angle, SMA+ALMA joint fit | 35.6 | +9.4/-10.1 | deg | 2 | and position angle |
| Total belt flux density, SMA-only fit | 5.13 | +0.34/-1.01 | mJy | 2 | $5.13 (+0.34, -1.01)$ |
| Total belt flux density, ALMA-only fit with priors | 3.5 | +/-0.5 | mJy | 2 | fitting the ALMA observations alone yields |
| 9 mm disk flux density (VLA) | 32.6 | +/-9.9 | microJy | 3 | The measured total flux density of the disk from our VLA observations is |
| Millimeter spectral index alpha_mm | 2.41 | +/-0.17 | dimensionless | 4 | determine a millimeter spectral index of 2.41±0.17 |
| Grain size distribution power-law index q | 3.27 | +/-0.10 | dimensionless | 4 | the resulting grain size distribution power-law index is |
| Planet b mass from inner edge truncation | 5.8 | +7.9/-3.1 | M_Jup | 5 | this inner edge location translates into a constraint on the planet b mass of |
| Surface density power-law index inferred from x | 0.12 | +/-0.47 | dimensionless | 6 | this implies a surface density profile |

## Qualitative findings

- The belt is broad (Delta R/R greater than or about 1), axisymmetric and inclined, with no significant azimuthal asymmetries in the residuals  
  > "These data provide no evidence for the presence of clumps or other azimuthal asymmetries" (Conclusions)
- Millimeter belt geometry is compatible with coplanarity of the belt with the planet orbits within large uncertainties  
  > "they are consistent with a coplanar configuration of the disk and planetary orbits within the (still large) mutual uncertainties" (Conclusions)
- The derived mass is consistent with planet b truncating the belt and no additional unseen outer planet is needed  
  > "there is no need to posit the presence of an additional unseen planet orbiting beyond planet b" (Dynamical Constraints on the Mass of Planet b)

## Claim tuples

- H: Is the belt inclination and position angle consistent with coplanarity of the planet orbits? | E: Fit an axisymmetric belt model with MCMC to the joint SMA and ALMA visibilities and compare the inclination and PA with astrometric orbit constraints | R: Inclination 32.8 (+5.6/-9.6) deg and PA 35.6 (+9.4/-10.1) deg | F: Belt geometry is consistent with the planet orbital parameters within the mutual uncertainties, with the uncertainties still large | **supported**
- H: Does the inner edge of the millimeter belt constrain the mass of planet b if the chaotic zone truncates the belt? | E: Translate the posterior of the inner edge radius into a planet mass with the Pearce and Wyatt chaotic-zone formula | R: Planet b mass 5.8 (+7.9/-3.1) M_Jup | F: The dynamical mass estimate is commensurate with hot-start evolutionary models, with large uncertainties allowing a range of initial conditions | **supported**
- H: Does the millimeter spectral index indicate a classical collisional cascade grain size distribution? | E: Compute the spectral index from 1.3 mm SMA+ALMA model flux and 9 mm VLA flux, then convert to q using beta_s = 1.8 and the Planck index | R: alpha_mm = 2.41 +/- 0.17 and q = 3.27 +/- 0.10 | F: Grain size distribution is close to predictions for a classical collisional cascade | **supported**
- H: Does the radial surface density profile favor planet-stirring over self-stirring? | E: Convert best-fit surface brightness index x to a surface density index assuming T proportional to r^-0.5 | R: Surface density index 0.12 +/- 0.47 | F: The shallow profile is not predicted by self-stirring, which favors planet-stirring, though uncertainties are significant | **partially**

## Reasoning

- Why this data: New SMA data provide larger angular scales than the previous millimeter interferometer studies, to recover the extended belt flux that archival ALMA filtered away  
  > "sensitive to larger angular scales than the previous millimeter interferometer studies" (Introduction)
- Why this method: A simple axisymmetric thin belt with radial power-law brightness fitted in the visibility domain, because the structure is not well resolved  
  > "we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt" (SMA/ALMA Disk Model Fits)
- Alternative: Fitting the 9 mm visibilities with a parametric model was rejected in favor of image-based aperture photometry  
  > "We adopt this image-based approach instead of fitting to the millimeter visibilities due to the difficulty in selecting a function" (VLA 9 millimeter Flux Estimate)
- Alternative: An additional unseen outer planet was considered as a truncation cause and rejected  
  > "there is no need to posit the presence of an additional unseen planet orbiting beyond planet b" (Dynamical Constraints on the Mass of Planet b)
- How they decided it was enough: MCMC convergence checked with the Gelman-Rubin statistic  
  > "check that the Gelman-Rubin statistic (cite: gelman14) is" (SMA/ALMA Disk Model Fits)
- Limitation (authors): ALMA-only fit has no constraints on outer radius or total flux without strong priors  
  > "To obtain constraints on these parameters from the ALMA data alone, we must impose strong priors on both" (SMA/ALMA Disk Model Fits)
- Limitation (authors): The disk is detected only at about 3 sigma per beam in the VLA image  
  > "In the VLA image, the disk is detected only at the" (VLA 9 millimeter Flux Estimate)
- Limitation (authors): Regardless of weighting and clean parameters, line imaging shows pronounced artifacts  
  > "all of our attempts at imaging the line emission show pronounced artifacts" (Line Emission)
- Caveat (inferred, ours): The ALMA-only result depends on imposed Gaussian and logistic priors, so the outer radius and flux there are prior-driven
- Caveat (inferred, ours): The SMA-only flux (5.13 mJy) and ALMA prior (3.5 mJy) differ, so the joint fit depends on how the two datasets are weighted
- Caveat (inferred, ours): The planet mass scales steeply with inner edge radius and uses one chaotic-zone formula at zero eccentricity
- Caveat (inferred, ours): The 9 mm flux comes from a 3 sigma detection with aperture photometry and no model fit
- Caveat (inferred, ours): The inclination and PA differ from Herschel values, and the paper leaves the physical origin unresolved
- Caveat (inferred, ours): The spectral index conversion assumes beta_s = 1.8 and a single dust temperature

## Reproducibility

- Data public (paper): ALMA data were retrieved from the archive; public status of the SMA and VLA data is not stated  
  > "We retrieved observations of HR 8799 from the ALMA archive" (Observations / Atacama Large Millimeter/submillimeter Array)
- Products in archive: _not stated_
- Code: vissample is publicly available as a Python package  
  > "publicly available at https://github.com/AstroChem/vis_sample" (Footnote 1)
- Missing: SMA visibilities and MIR calibration outputs
- Missing: Exact CASA imaging parameters (cell, image size, masking, iterations, thresholds) for all images
- Missing: Starting positions, walker initialization and full prior bounds for the joint SMA+ALMA fit
- Missing: Background point source prior ranges
- Missing: VLA aperture size and background region used for the 9 mm flux
- Missing: Distance to HR 8799 for the AU scale conversion
- Data volume (inferred): small: six SMA tracks, five ALMA scheduling blocks and four VLA sessions of continuum data; total size not stated
- Score (inferred): 3/5, Recipe is partly complete for the model fits and the spectral index, but SMA data access, calibration products and key imaging parameters are not given.
- Rediscovery candidate: no, Data availability for the SMA and VLA observations is not stated, and imaging parameters and the fitting setup are incomplete, so the analysis cannot be redone from the paper alone.

## Links

- Method: (cite: macgregor13) (Visibility fitting procedure for axisymmetric belt models)
- Method: (cite: foreman13) (emcee MCMC sampler used for posterior exploration)
- Method: (cite: pearce14) (Chaotic-zone formula relating inner edge to planet mass)
- Method: (cite: macgregor16) (Millimeter spectral index and grain size index comparison sample)
- Companion: (cite: booth16) (Earlier analysis of the same archival ALMA 1.3 mm data)
- Companion: (cite: hughes11) (First millimeter interferometric detection of the disk with SMA at 870 micron)
- Related: ALMA archival project 2012.1.00482.S

## Checks

```json
{
 "quotes": 135,
 "quotes_ok": 134,
 "quote_pass_rate": 0.993,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 89,
  "rate": 0.84
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 1** (sky_image, 3 panel(s), data): 1.3 mm continuum images of the HR 8799 debris disk from the SMA alone, ALMA alone, and combined SMA+ALMA data, with the stellar position and best-fit belt position angle marked.
  - axes: x: RA offset from star [arcsec]; y: Dec offset from star [arcsec]; colour: 1.3 mm continuum surface brightness [not labelled]
  - supports step 1
  - read off the plot: approx. SMA beam 6.1 x 5.6 arcsec; approx. ALMA beam 1.7 x 1.2 arcsec; approx. combined beam 3.8 x 3.7 arcsec; approx. rms 180, 16 and 30 µJy/beam for SMA, ALMA and combined images
  - reproduction target
- **Figure 2** (uv_plot, 2 panel(s), data, model): Real and imaginary parts of 1.3 mm visibilities binned in deprojected uv distance for SMA and ALMA data, with the best-fit axisymmetric belt model overplotted.
  - axes: x: deprojected uv distance [kilolambda]; y: real visibility amplitude [mJy]; y: imaginary visibility amplitude [mJy]
  - supports step 2
  - validation: Imaginary parts consistent with zero, as expected for an axisymmetric belt, and the best-fit model tracks the binned real visibilities.
  - read off the plot: approx. real visibility 3.6 mJy at about 5 kλ; approx. real visibility near 0 mJy beyond about 30 kλ; approx. model real value 3.4 mJy at uv distance 0
  - reproduction target
- **Figure 3** (sky_image, 1 panel(s), data): 9 mm continuum image of the disk from the VLA with natural weighting and a 5 arcsec taper, showing faint emission around the star.
  - axes: x: RA offset from star [arcsec]; y: Dec offset from star [arcsec]; colour: 9 mm continuum surface brightness [not labelled]
  - supports step 3
  - read off the plot: approx. rms 4.3 µJy/beam; approx. beam 6.2 x 5.8 arcsec
  - reproduction target
- **Figure 4** (channel_maps, 9 panel(s), data): SMA channel maps of 13CO J=2-1 emission toward HR 8799 at LSR velocities from about -5.3 to -3.8 km/s, showing no clear coherent gas emission.
  - axes: x: RA offset from star [arcsec]; y: Dec offset from star [arcsec]; colour: 13CO(2-1) intensity [not labelled]; velocity: LSR velocity [km/s]
  - read off the plot: approx. channel velocities -5.32 to -3.80 km/s; approx. rms noise 100 mJy/beam
- **Figure 5** (corner_plot, 36 panel(s), model): Corner plot of MCMC posterior distributions for the belt model parameters fit to combined SMA and ALMA data, including inner and outer radius, belt flux, power-law index x, inclination and position angle.
  - axes: diagonal x: marginalised parameter value (R_in, R_out, F_belt, x, i, PA) [AU, AU, mJy, dimensionless, deg, deg]; off-diagonal y: paired parameter posterior [as per diagonal]
  - supports step 2
  - validation: Posterior distributions with 1 and 2 sigma contours show parameter constraints of the axisymmetric belt model.
  - read off the plot: approx. R_in peak near 100 AU; approx. R_out peak near 360 AU; approx. F_belt peak near 3.3 mJy; approx. inclination peak near 32 deg; approx. PA peak near 32 deg
  - reproduction target
- **Figure 6** (residual_map, 4 panel(s), data, model, residual): Combined SMA+ALMA data, the best-fit model at full resolution, the best-fit model convolved with the beam, and the residuals after subtracting the imaged model from the data.
  - axes: x: RA offset from star [arcsec]; y: Dec offset from star [arcsec]; colour: 1.3 mm continuum surface brightness [not labelled]
  - supports step 2
  - validation: Residuals after subtracting the imaged best-fit belt model from the data show no significant structure above the rms noise.
  - read off the plot: approx. contour step 2 x 30 µJy/beam; approx. pixel size 0.5 arcsec = 2 AU at 39.4 pc
  - reproduction target
- **Figure 7** (other, 1 panel(s), model): Normalised histogram of the planet b mass implied by truncation of the belt inner edge, using the inner radius posterior from the MCMC fit, with best-fit and 1 sigma limits marked.
  - axes: x: planet b mass [Jupiter masses]; y: normalised counts [dimensionless]
  - supports step 5
  - read off the plot: approx. best-fit planet mass 6 Jupiter masses; approx. 1 sigma range about 2.5 to 14 Jupiter masses; approx. histogram peak at about 4 to 6 Jupiter masses
  - reproduction target
