# Asymmetric Dust Accumulation of the PDS 70 Disk Revealed by ALMA Band 3 Observations

`2024ApJ...974L..25D` | The Astrophysical Journal Letters 2024 | first author: Doi, Kiyoaki | arXiv: 2408.09216 | DOI: 10.3847/2041-8213/ad7f51

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: How is dust distributed in the PDS 70 disk at 3.0 mm compared with Band 7, what do the spectral index and ring eccentricity say about dust accumulation, and what upper limit do they place on the mass of PDS 70c  
  > "In this study, we characterize the dust distribution of PDS 70 using high-resolution ALMA Band 3 (3.0 mm) continuum observations." (Introduction); "We constrain the eccentricity of the outer ring to be $e<0.04$ from the position of the central star and the outer ring." (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 112.39 +/- 0.24 pc  
  > "a distance of $112.39 \pm 0.24 \ \mathrm{pc}$ (cite: Gaia2023)" (Introduction); distance from Gaia Collaboration 2023 (Gaia2023)  
  > "a distance of $112.39 \pm 0.24 \ \mathrm{pc}$ (cite: Gaia2023)" (Introduction)

## Data provenance

- ALMA projects: 2022.1.00893.S, 2022.1.01477.S, 2015.1.00888.S, 2018.A.00030.S
- bands: Band 3 (3.0 mm, new data); Band 7 (0.87 mm, archival, from Benisty et al. 2021)  
  > "Previous high-resolution ALMA observations of PDS 70 have been limited to ALMA Band 7 (0.87 mm)" (Introduction); "The Band 7 data are those shown in the left panel of Fig. 1 in (cite: Benisty2021)." (Observations)
- frequencies and spectral setup: Band 3: four spectral windows centered at 90.5, 92.5, 102.5, 104.5 GHz, 1.875 GHz bandwidth each; MFS central frequency 97.5 GHz. Band 7 central frequency 350.6 GHz  
  > "Four spectral windows were set at the central frequency of 90.5, 92.5, 102.5, and 104.5 GHz with a bandwidth of 1.875 GHz each to maximize the continuum sensitivity." (Observations); "at the central frequency of 350.6 GHz" (Observations)
- continuum bandwidth: 4 x 1.875 GHz spectral windows  
  > "Four spectral windows were set at the central frequency of 90.5, 92.5, 102.5, and 104.5 GHz with a bandwidth of 1.875 GHz each to maximize the continuum sensitivity." (Observations)
- arrays: _not stated_
- configurations: Band 3: C5, C6, C8 and C9  
  > "The observations were performed in four configurations, C5, C6, C8 and C9, on March 26, May 4, July 2 and July 28, 2023" (Observations)
- baselines: _not stated_
- angular resolution: Band 3 beam 0.073" x 0.066", PA -64.2 deg; Band 7 beam 0.046" x 0.035", PA -53.1 deg  
  > "The resulting image has a beam size of $0.073\ensuremath{''} \times 0.066\ensuremath{''}$ with a position angle of $-64.2\ensuremath{^\circ}$" (Observations); "The resulting image has a beam size of $0.046\ensuremath{''} \times 0.035\ensuremath{''}$ at a position angle of $-53.1\ensuremath{^\circ}$" (Observations)
- max recoverable scale: 9.83 arcsec (C5, Band 3)  
  > "The maximum recoverable scale of the C5 observations is $9.83\ensuremath{''}$, which is sufficient to avoid missing flux." (Observations)
- sensitivity: Band 3 rms 4.94 uJy/beam; Band 7 rms 12.7 uJy/beam  
  > "the rms noise level measured in the emission free region is $4.94\ \mathrm{\mu Jy\ beam^{-1}}$" (Observations); "the rms noise level is $12.7\ \mathrm{\mu Jy\ beam^{-1}}$ at the central frequency of 350.6 GHz" (Observations)
- time on source: Band 3: 2600, 756, 5334 and 3193 s for C5, C6, C8, C9  
  > "on March 26, May 4, July 2 and July 28, 2023, with on-source integration times of 2600, 756, 5334 and 3193 seconds, respectively." (Observations)
- observing dates: Band 3: March 26, May 4, July 2 and July 28, 2023 (Cycle 10)  
  > "on March 26, May 4, July 2 and July 28, 2023, with on-source integration times of 2600, 756, 5334 and 3193 seconds, respectively." (Observations)
- pi or archival as stated: Band 3: Cycle 10 projects PI K. Doi and PI H. Liu; Band 7: archival 2015.1.00888.S (PI E. Akiyama) and 2018.A.00030.S (PI M. Benisty), calibrated data of Benisty et al. 2021  
  > "The ALMA Band 3 observations of PDS 70 were conducted in Cycle 10 as two projects, 2022.1.00893.S (PI: K. Doi) and 2022.1.01477.S (PI: H. Liu)." (Observations); "We re-ran `tclean` on the calibrated data of (cite: Benisty2021)" (Observations)
- Other facility **ALMA Band 7 archival data (Benisty et al. 2021)**: Band 7 (0.87 mm) continuum image used for the spectral index and morphology comparison  
  > "The Band 7 data are those shown in the left panel of Fig. 1 in (cite: Benisty2021)." (Observations)
- External data: Band 7 calibrated data (2015.1.00888.S, 2018.A.00030.S), reduced by Benisty et al. 2021 and re-imaged here without JvM correction  
  > "The data reduction is described in (cite: Benisty2021)." (Observations); "without applying the JvM correction (cite: JvM1995), which was applied in (cite: Benisty2021)" (Observations) [from Benisty et al. 2021 (cite: Benisty2021)]
- External data: Band 7 intensity of PDS 70 c, 86 +/- 16 uJy  
  > "assuming the Band 7 intensity of PDS 70 c is $86 \pm 16$ $\mu$Jy (cite: Benisty2021)" (Circumplanetary Disk) [from Benisty et al. 2021 (cite: Benisty2021)]
- External data: Distance to PDS 70, 112.39 +/- 0.24 pc  
  > "a distance of $112.39 \pm 0.24 \ \mathrm{pc}$ (cite: Gaia2023)" (Introduction) [from Gaia Collaboration 2023 (cite: Gaia2023)]
- External data: Stellar age 5.4 +/- 1.0 Myr  
  > "an age of $5.4 \pm 1.0 \ \mathrm{Myr}$ (cite: Muller2018)" (Introduction) [from Muller et al. 2018 (cite: Muller2018)]
- External data: Disk inclination 51.7 deg and position angle 160.4 deg fixed in ring fitting  
  > "We fixed the inclination $i = 51.7^{\circ}$ and the position angle PA = $160.4^{\circ}$ based on (cite: Keppler2019)." (Image Fitting) [from Keppler et al. 2019 (cite: Keppler2019)]
- External data: Ring temperature of 16 K for dust mass  
  > "We assumed a temperature of 16 K for the disk ring, based on the temperature model of (cite: Law2024)." (Ring) [from Law et al. 2024 (cite: Law2024)]
- External data: DSHARP dust opacity model (upper-limit Band 3 kappa_abs = 0.47 cm^2/g)  
  > "Here, we used the DSHARP dust model for the dust opacity (cite: Birnstiel2018)" (Ring) [from Birnstiel et al. 2018 (cite: Birnstiel2018)]
- External data: Critical planet mass formula (equation 18) for eccentric ring, with M_star = 0.85 Msun and h/r = 0.079  
  > "Using their equation (18)[^1], the critical planet mass to induce the eccentricity is" (Eccentricity and Exoplanet Mass); "for the central star mass $M_{\mathrm{star}} = 0.85 M_{\odot}$ and the aspect ratio $h/r = 0.079$ (cite: Bae2019)" (Eccentricity and Exoplanet Mass) [from Tanaka et al. 2022 (cite: Tanaka2022); Bae et al. 2019 (cite: Bae2019)]
- Simulation/model as data: Tanaka et al. 2022 2D single-planet simulations (empirical critical planet mass for eccentric outer ring) used to convert the ring eccentricity limit to a planet mass limit  
  > "A caveat is that the simulation of (cite: Tanaka2022) is a 2D simulation assuming a single planet on a circular orbit" (Eccentricity and Exoplanet Mass)

## Processing

### Calibration

- pipeline or manual: Pipeline calibration, then further reduction in CASA modular version  
  > "The pipeline calibration was performed with Common Astronomical Software Applications (CASA) version 6.4.1.12 and the subsequent reduction was performed with CASA modular version 6.6.3.22" (Observations)
- casa version: CASA 6.4.1.12 (pipeline calibration); CASA modular 6.6.3.22 (subsequent reduction)  
  > "The pipeline calibration was performed with Common Astronomical Software Applications (CASA) version 6.4.1.12 and the subsequent reduction was performed with CASA modular version 6.6.3.22" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Amplitude calibrator J1427-4206 (phase calibrator J1407-4302), for all Band 3 observations  
  > "The phase calibrator was J1407-4302, and the amplitude calibrator was J1427-4206 for all observations." (Observations)
- flux scale uncertainty: 5% for Band 3 and 10% for Band 7 (ALMA Technical Handbook)  
  > "when the absolute flux calibration error is 5% for Band 3 and 10% for Band 7" (Results)
- self calibration: Phase-only self-calibration per EB on line-subtracted data; none on the combined data (peak SNR of 21 too low)  
  > "We subtracted the line emission and then performed phase-only self-calibration for each EB on the line-subtracted data." (Observations); "We did not apply self-calibration to the combined data because it did not improve SNR due to the insufficient peak SNR of 21." (Observations)

### Imaging

- task: tclean, MFS at 97.5 GHz, nterms = 2 (Band 3); Band 7 re-imaged with tclean  
  > "Imaging was performed with Multi-Frequency Synthesis (MFS) at a central frequency of 97.5 GHz, using `nterms = 2`" (Observations); "We re-ran `tclean` on the calibrated data of (cite: Benisty2021)" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (Band 3)  
  > "Briggs weighting with a robust parameter of 0.5." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line emission subtracted before self-calibration (method not given)  
  > "We subtracted the line emission and then performed phase-only self-calibration for each EB on the line-subtracted data." (Observations)
- line free channels: _not stated_
- primary beam correction: Band 7 re-imaged without the JvM correction applied in Benisty et al. 2021  
  > "without applying the JvM correction (cite: JvM1995), which was applied in (cite: Benisty2021)" (Observations)
- array combination: All four Band 3 configuration EBs combined and imaged together  
  > "The data were then combined and imaged using the `tclean` task." (Observations)
- smoothing: Band 7 smoothed to the Band 3 beam for the spectral index; both bands smoothed to a circular 0.12" deprojected beam for azimuthal profiles  
  > "The Band 7 image is smoothed to match the resolution of the Band 3 beam." (Results); "we further smoothed both images so that the beam became a circular Gaussian after deprojection with a beam size of $0.12\ensuremath{''}$" (Ring)
- final beam: Band 3: 0.073" x 0.066", PA -64.2 deg; Band 7: 0.046" x 0.035", PA -53.1 deg  
  > "The resulting image has a beam size of $0.073\ensuremath{''} \times 0.066\ensuremath{''}$ with a position angle of $-64.2\ensuremath{^\circ}$" (Observations); "The resulting image has a beam size of $0.046\ensuremath{''} \times 0.035\ensuremath{''}$ at a position angle of $-53.1\ensuremath{^\circ}$" (Observations)
- final rms: Band 3 4.94 uJy/beam; Band 7 12.7 uJy/beam (15.1 uJy/beam after smoothing to Band 3 beam)  
  > "the rms noise level measured in the emission free region is $4.94\ \mathrm{\mu Jy\ beam^{-1}}$" (Observations); "The rms noise level of the smoothed Band 7 image is $15.1 \ \mathrm{\mu Jy\ beam^{-1}}$." (Results)

### Inherited from earlier work

- Band 7 data reduction/calibration  
  > "The data reduction is described in (cite: Benisty2021)." (Observations) [from Benisty et al. 2021 (cite: Benisty2021)]
- Ring/central-source image fitting code and method  
  > "We perform image fitting using `ring_fit` (cite: Doi2023)" (Image Fitting) [from Doi & Kataoka 2023 (cite: Doi2023)]
- Inclination and position angle used for deprojection  
  > "We fixed the inclination $i = 51.7^{\circ}$ and the position angle PA = $160.4^{\circ}$ based on (cite: Keppler2019)." (Image Fitting) [from Keppler et al. 2019 (cite: Keppler2019)]
- Dust temperature model for the ring mass estimate  
  > "We assumed a temperature of 16 K for the disk ring, based on the temperature model of (cite: Law2024)." (Ring) [from Law et al. 2024 (cite: Law2024)]
- Dust opacity model and size distribution  
  > "Here, we used the DSHARP dust model for the dust opacity (cite: Birnstiel2018)" (Ring) [from Birnstiel et al. 2018 (cite: Birnstiel2018)]
- Azimuthal profile smoothing to a circular deprojected beam to avoid beam-shape effects  
  > "To avoid the effect of the elliptical beam shape on the azimuthal variation of the intensity (cite: Doi2021)" (Ring) [from Doi & Kataoka 2021 (cite: Doi2021)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and the method/order used for continuum (line) subtraction
- Self-calibration solution intervals, reference antennas and number of iterations for the per-EB phase-only self-calibration
- tclean cell size, image size, clean mask, threshold, number of iterations and deconvolver settings (only nterms = 2, robust = 0.5 and MFS at 97.5 GHz given)
- Whether any weight or flux-scale alignment between the four Band 3 EBs was applied before combining
- Exact tclean parameters used to re-image the Band 7 data (robust, mask, cell, uv range) and how it was smoothed
- Band 3 and Band 7 coordinates of PDS 70 and the phase centre/shift used to align the two images
- Deprojection/aperture choices and exact definition of the northwest-peak sector for the 2.5x contrast and spectral index values
- Priors and walker initialisation in the ring_fit MCMC (only walkers, steps and burn-in given)
- Dust mass calculation details beyond temperature and opacity: the exact flux/integration region and handling of optical depth
- Public release status of the Cycle 10 Band 3 data is not stated in the paper

## Analysis recipe

1. **Calibrate and prepare Band 3 visibilities**: Pipeline calibration, line subtraction, phase-only self-calibration per EB  
  > "We subtracted the line emission and then performed phase-only self-calibration for each EB on the line-subtracted data." (Observations)
   - software: CASA
   - parameter: CASA 6.4.1.12 pipeline; CASA modular 6.6.3.22 for later reduction  
  > "The pipeline calibration was performed with Common Astronomical Software Applications (CASA) version 6.4.1.12 and the subsequent reduction was performed with CASA modular version 6.6.3.22" (Observations)
   - fitting: _not stated_
   - validation: Self-calibration on the combined data was tested and not applied since it did not improve SNR  
  > "We did not apply self-calibration to the combined data because it did not improve SNR due to the insufficient peak SNR of 21." (Observations)
2. **Image Band 3 continuum**: Combine EBs and image with tclean using MFS  
  > "The data were then combined and imaged using the `tclean` task." (Observations)
   - software: CASA, tclean
   - parameter: MFS at 97.5 GHz, nterms = 2, Briggs robust = 0.5  
  > "Imaging was performed with Multi-Frequency Synthesis (MFS) at a central frequency of 97.5 GHz, using `nterms = 2` and Briggs weighting with a robust parameter of 0.5." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Re-image Band 7 continuum**: Re-run tclean on the calibrated Band 7 data of Benisty et al. 2021 without JvM correction  
  > "We re-ran `tclean` on the calibrated data of (cite: Benisty2021) without applying the JvM correction (cite: JvM1995)" (Observations)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit ring and central source morphology**: Fit Gaussian ring and Gaussian central source models, convolved with the beam, to the images with ring_fit and emcee  
  > "We created these model images, smoothed them with the beam, and minimized the residuals between models and observations using `emcee` (cite: Foreman-Mackey2013)." (Image Fitting)
   - software: ring_fit, emcee
   - parameter: Ring fitted over 35 au < r < 105 au and central source over r < 15 au; also fit excluding the northwest peak (0 to 270 deg)  
  > "We fitted the ring in the range of $35\ \mathrm{au} < r < 105\ \mathrm{au}$ and the central source in the range of $r < 15$ au." (Image Fitting)
   - parameter: 16 walkers, 20,000 steps, first 1,000 steps burn-in  
  > "We perform MCMC fitting with 16 walkers and 20,000 steps, excluding the first 1,000 steps as burn-in." (Image Fitting)
   - assumption: Inclination 51.7 deg and PA 160.4 deg fixed; Gaussian ring and Gaussian central disk profiles  
  > "We fixed the inclination $i = 51.7^{\circ}$ and the position angle PA = $160.4^{\circ}$ based on (cite: Keppler2019)." (Image Fitting)
   - fitting: emcee MCMC, minimizing residuals between beam-convolved models and images; priors and likelihood not stated  
  > "We created these model images, smoothed them with the beam, and minimized the residuals between models and observations using `emcee` (cite: Foreman-Mackey2013)." (Image Fitting)
   - validation: Fit repeated excluding the northwest peak; conclusions do not change  
  > "In the main discussion, we use the fitting results for full azimuthal angle, while the conclusions do not change depending on which results are used." (Image Fitting)
5. **Compute Band 7 to Band 3 spectral index map**: Align images on the fitted outer-ring center, smooth Band 7 to the Band 3 beam, compute alpha from the intensity ratio  
  > "The two images are aligned to match the center of the outer ring" (Results); "The Band 7 image is smoothed to match the resolution of the Band 3 beam." (Results)
   - parameter: Flux calibration error 5% (Band 3) and 10% (Band 7) gives Delta alpha = 0.083  
  > "when the absolute flux calibration error is 5% for Band 3 and 10% for Band 7" (Results)
   - fitting: _not stated_
   - validation: Uncertainty reported with rms noise only and with flux calibration error  
  > "unless otherwise noted, the spectral index uncertainty mentioned below only considers the uncertainty due to the rms noise" (Results)
6. **Extract azimuthal and radial intensity/spectral index profiles**: Azimuthal profile on images smoothed to a circular deprojected 0.12" beam; azimuthally averaged radial profiles of intensity and spectral index  
  > "we further smoothed both images so that the beam became a circular Gaussian after deprojection with a beam size of $0.12\ensuremath{''}$" (Ring); "The upper panel of Figure [3](#fig:PDS70_radial) shows the azimuthally averaged radial profile of the intensity" (Ring)
   - fitting: _not stated_
   - validation: Profiles also shown separately for the northwest peak direction and the other directions  
  > "Here, we show the radial profiles for the northwest peak direction and the rest directions separately." (Radial Profile)
7. **Estimate lower limit of ring dust mass**: Dust mass from Band 3 emission with a fixed temperature and DSHARP opacity  
  > "We estimated the lower limit of the dust mass to be 28 $M_{\mathrm{Earth}}$ in the entire ring" (Ring)
   - parameter: Temperature 16 K; kappa_abs = 0.47 cm^2/g (Band 3 upper limit); size distribution q = 3.5 from 0.1 um to 3.4 mm  
  > "We assumed a temperature of 16 K for the disk ring, based on the temperature model of (cite: Law2024)." (Ring); "assuming a power-law size distribution of $q= 3.5$ (cite: Mathis1977; Doi2023) from $0.1 \ \mathrm{\mu m}$ grains to $3.4 \ \mathrm{mm}$ grains" (Ring)
   - assumption: 16 K is an upper limit for the temperature; maximum grain size chosen to maximize opacity for a conservative mass  
  > "This is considered an upper limit model for the temperature, as it is derived from the upper layer of the gas, and the midplane temperature may be lower." (Ring); "in which the maximum dust size was chosen to maximize the opacity for conservative mass estimates" (Ring)
   - fitting: _not stated_
   - validation: _not stated_
8. **Derive ring eccentricity and PDS 70c mass limit**: Eccentricity from offset between fitted ring center and central point source (e = delta r / r0), mapped to planet mass with the Tanaka et al. 2022 critical mass relation  
  > "We can estimate the eccentricity from the offset between the position of the central star and the center of the ring, $\delta r$, and the semi-major axis $r_0$ as" (Eccentricity and Exoplanet Mass); "set the 84th percentile as the upper limit of the deviation of the ring center position" (Image Fitting)
   - software: emcee
   - parameter: M_star = 0.85 Msun, h/r = 0.079, alpha_turb = 1e-3  
  > "for the central star mass $M_{\mathrm{star}} = 0.85 M_{\odot}$ and the aspect ratio $h/r = 0.079$ (cite: Bae2019)" (Eccentricity and Exoplanet Mass)
   - assumption: 2D single planet on a circular orbit (Tanaka et al. 2022); alpha_turb = 1e-3; M_crit scales as sqrt(alpha_turb)  
  > "A caveat is that the simulation of (cite: Tanaka2022) is a 2D simulation assuming a single planet on a circular orbit" (Eccentricity and Exoplanet Mass); "which is proportional to the square root of the turbulent strength $\alpha_{\mathrm{turb}}$" (Eccentricity and Exoplanet Mass)
   - fitting: Offset posterior from the ring and central-source MCMC fits; 84th percentile as upper limit  
  > "set the 84th percentile as the upper limit of the deviation of the ring center position" (Image Fitting)
   - validation: Band 7 ring-center offset gives a consistent, tighter limit  
  > "provides the eccentricity of $e < 0.02$" (Eccentricity and Exoplanet Mass)

## Software

- **CASA** 6.4.1.12 (pipeline); modular 6.6.3.22: Pipeline calibration and subsequent reduction  
  > "The pipeline calibration was performed with Common Astronomical Software Applications (CASA) version 6.4.1.12 and the subsequent reduction was performed with CASA modular version 6.6.3.22" (Observations)
- **tclean** : Imaging Band 3 and re-imaging Band 7 continuum  
  > "The data were then combined and imaged using the `tclean` task." (Observations)
- **ring_fit** : Fitting ring and central-source morphology  
  > "We perform image fitting using `ring_fit` (cite: Doi2023)" (Image Fitting)
- **emcee** : MCMC minimization of residuals in image fitting  
  > "minimized the residuals between models and observations using `emcee` (cite: Foreman-Mackey2013)" (Image Fitting)
- **astropy** : Listed in the software statement; specific use not stated  
  > "Software: *CASA* (cite: McMullin2007), *astropy* (cite: astropy2022), *emcee* (cite: Foreman-Mackey2013), *scipy* (cite: scipy2020)," (Acknowledgments)
- **scipy** : Listed in the software statement; specific use not stated  
  > "Software: *CASA* (cite: McMullin2007), *astropy* (cite: astropy2022), *emcee* (cite: Foreman-Mackey2013), *scipy* (cite: scipy2020)," (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Northwest peak intensity contrast, Band 3 | 2.5 | not stated | dimensionless | 6 | In Band 7, the intensity at the northwest peak is 1.3 times larger than in other directions, while it is 2.5 times larger in Band 3. |
| Northwest peak intensity contrast, Band 7 | 1.3 | not stated | dimensionless | 6 | In Band 7, the intensity at the northwest peak is 1.3 times larger than in other directions, while it is 2.5 times larger in Band 3. |
| Spectral index at the northwest peak | 2.17 | +/-0.04 (rms); +/-0.09 (with flux calibration error) | dimensionless | 5 | $\alpha_{\mathrm{SED}} = 2.17 \pm 0.04$ with the rms error, and $\alpha_{\mathrm{SED}} = 2.17 \pm 0.09$ with flux calibration error |
| Spectral index of the central point source | 1.53 | +/-0.13 (rms); +/-0.15 (with flux calibration error) | dimensionless | 5 | $\alpha_{\mathrm{SED}} = 1.53 \pm 0.13$ with the rms error, and $\alpha_{\mathrm{SED}} = 1.53 \pm 0.15$ with flux calibration error |
| Minimum azimuthally averaged radial spectral index near ring peak | 2.69 | +/-0.01 | dimensionless | 6 | has a minimum value of $\alpha_{\mathrm{SED}} = 2.69 \pm 0.01$ near the radial peak of the ring |
| Spectral index at inner and outer half-peak radii (r = 0.511" and 0.770") | 3.12 (inner), 2.81 (outer) | +/-0.05 (inner), +/-0.03 (outer) | dimensionless | 6 | the spectral index is $\alpha_{\mathrm{SED}} = 3.12 \pm 0.05$ at the inner side and $\alpha_{\mathrm{SED}} = 2.81 \pm 0.03$ at the outer side |
| Ring width w, Band 3 and Band 7 | 8.45 au (Band 3); 11.23 au (Band 7) | +0.22/-0.21 (Band 3); +0.03/-0.03 (Band 7) | au | 4 | with $w = 8.45_{-0.21}^{+0.22}$ au in Band 3 and $w = 11.23_{-0.03}^{+0.03}$ au in Band 7 |
| Peak flux of the central source in Band 3 | 31.1 | not stated | uJy | 4 | The flux estimated from the peak intensity of the central source in Band 3 is 31.1 $\mu$Jy. |
| Lower limit of dust mass in the entire ring | 28 | lower limit | Earth masses | 7 | We estimated the lower limit of the dust mass to be 28 $M_{\mathrm{Earth}}$ in the entire ring |
| Lower limit of dust mass around the northwest peak (270-360 deg) | 9.3 | lower limit | Earth masses | 7 | and 9.3 $M_{\mathrm{Earth}}$ even within the narrow range |
| Lower limit of spectral index of PDS 70 c | > 1.5 | 3 sigma Band 3 upper limit 15 uJy | dimensionless | 5 | We put a lower limit on the spectral index of PDS 70 c as $\alpha_{\mathrm{SED}} > 1.5$ |
| Ring eccentricity from Band 3 (ring center vs central source) | < 0.04 | upper limit | dimensionless | 8 | indicating that the ring is circular with the eccentricity $e < 0.04$ |
| Ring eccentricity from Band 7 | < 0.02 | upper limit | dimensionless | 8 | provides the eccentricity of $e < 0.02$ |
| Upper limit on mass of PDS 70 c for alpha_turb = 1e-3 | < 4.9 | upper limit | Jupiter masses | 8 | These low eccentricities put the mass of PDS 70 c below $4.9 M_{\mathrm{Jupiter}}$ for $\alpha_{\mathrm{turb}} = 10^{-3}$ |

## Qualitative findings

- Band 3 shows a prominent northwest peak in the ring, a compact central point source, and no circumplanetary disk detection  
  > "First, the ring exhibits more prominent asymmetric peak in the northwest direction (hereafter, the northwest peak)." (Results); "Third, the circumplanetary disk is not detected in Band 3." (Results)
- The ring is narrower in Band 3 than in Band 7 and the inner shoulder is weaker in Band 3  
  > "The upper panel shows that the dust ring width is narrower in Band 3 than in Band 7." (Ring)
- Central Band 3 emission is interpreted as dominated by free-free emission, Band 7 central emission by dust  
  > "Therefore, the compact central emission in Band 3 is dominated by free-free emission" (Central Source)

## Claim tuples

- H: Is dust in the PDS 70 ring accumulated azimuthally as well as radially? | E: Compare Band 3 and Band 7 azimuthal intensity profiles and the Band 7 to Band 3 spectral index map | R: Northwest peak 2.5x brighter than other directions in Band 3 (1.3x in Band 7) with minimum alpha of 2.17 | F: Dust is accumulated radially and azimuthally outside the planets, in a vortex-like peak | **supported**
- H: Is there enough dust in the ring to form further planets? | E: Estimate the dust mass lower limit from Band 3 emission with 16 K and DSHARP opacity | R: 28 Earth masses in the whole ring and 9.3 Earth masses near the northwest peak | F: Enough dust for additional solid planets or a gas giant core, suggesting inside-out planet formation | **supported**
- H: Is the outer ring eccentric, and what does that imply for PDS 70 c mass? | E: Fit ring and central point-source centers in Band 3 and Band 7 and apply the Tanaka et al. 2022 critical mass criterion | R: e < 0.04 (Band 3) and e < 0.02 (Band 7) | F: The ring is circular; the mass of PDS 70 c is below 4.9 Jupiter masses for alpha_turb = 1e-3 | **supported**
- H: What is the nature of the central emission and are circumplanetary disks detected in Band 3? | E: Fit central source in both bands, compute the spectral index, and search for point sources at PDS 70 b and c | R: Central alpha = 1.53, compact in Band 3 and extended in Band 7; no point source at b or c, alpha > 1.5 for c | F: Band 3 central emission is likely free-free; circumplanetary disk non-detection is consistent with thermal dust spectrum | **partially**

## Reasoning

- Why this data: Band 7 may be optically thick; Band 3 is likely more optically thin and reveals the detailed dust distribution  
  > "In this study, we present high-resolution observations at Band 3, which is likely more optically thin compared to Band 7" (Introduction)
- Why this method: Detecting the central point source in Band 3 fixes the stellar position (the ellipse focus) so ring eccentricity can be measured accurately  
  > "The Band 3 observations allow us to accurately estimate the eccentricity by detecting point-source free-free emission at the position of the central star" (Eccentricity and Exoplanet Mass)
- Alternative: Self-calibration of the combined Band 3 data was not applied because it did not improve SNR  
  > "We did not apply self-calibration to the combined data because it did not improve SNR due to the insufficient peak SNR of 21." (Observations)
- Alternative: Narrower ring in Band 3 explained either by larger grains concentrating at the ring center or by Band 7 saturating at high optical depth  
  > "The other explanation is that the peak intensity saturates due to the higher optical depth in Band 7 than in Band 3." (Ring)
- How they decided it was enough: _not stated_
- Limitation (authors): The double-peak structure at the northwest peak has an intensity dip below 3 sigma, so it is not conclusive  
  > "but the intensity dip between the peaks is less than $3 \sigma$, making it difficult to conclusively characterize this feature." (Ring)
- Limitation (authors): The planet-mass limit relies on a 2D single-planet circular-orbit simulation; planet multiplicity, eccentricity or 3D effects may change the disk eccentricity  
  > "A caveat is that the simulation of (cite: Tanaka2022) is a 2D simulation assuming a single planet on a circular orbit" (Eccentricity and Exoplanet Mass)
- Limitation (authors): Gaussian ring model is not a perfect description of the emission  
  > "The caveat is that the emission of the object is not perfectly Gaussian" (Image Fitting)
- Caveat (inferred, ours): The planet-mass limit depends on alpha_turb = 1e-3 and on the Tanaka et al. 2022 equation (18) chosen as the conservative of two criteria; the h/r of 0.079 comes from a simulation paper
- Caveat (inferred, ours): Free-free interpretation of the central source rests on alpha < 2 and an unresolved size with a degenerate width/intensity fit; Liu et al. 2024 find free-free not dominant
- Caveat (inferred, ours): Ring center versus central source offset is limited by fit uncertainty of ~1.5 au, so e < 0.04 is a weak constraint relative to the 75 au ring radius
- Caveat (inferred, ours): Band 7 and Band 3 images were aligned on the fitted ring center, which could bias the spectral index near the ring if alignment errors exist

## Reproducibility

- Data public (paper): Project codes are given for all data, and the acknowledgment lists ADS/JAO ALMA data; public release status is not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO. ALMA#2015.1.00888.S, 2018.A.00030, 2022.1.00893.S, and 2022.1.01477.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Line-free channels, self-calibration solint and tclean cell/image size/mask/threshold
- Missing: ring_fit priors and initialisation, and exact sector definitions for the northwest peak
- Missing: Band 7 re-imaging parameters and image alignment/smoothing procedure
- Data volume (inferred): Four Band 3 configurations (C5, C6, C8, C9) plus two Band 7 projects; likely a few hundred GB to ~1 TB raw, roughly tens of GB of calibrated MS
- Score (inferred): 3/5, Archival project codes and CASA versions given and the main results are numeric, but tclean geometry, mask, self-calibration and line-flagging settings are missing and the ring_fit code release is not stated
- Rediscovery candidate: no, Public status is not stated and several imaging and self-calibration settings are missing, although the main results (spectral index, ring width, eccentricity, dust mass) are numeric

## Links

- Method: Doi & Kataoka 2023 (cite: Doi2023) (ring_fit image fitting method and dust size distribution)
- Method: Doi & Kataoka 2021 (cite: Doi2021) (Beam-shape effect on azimuthal intensity variations)
- Method: Tanaka et al. 2022 (cite: Tanaka2022) (Critical planet mass criterion for eccentric outer ring)
- Companion: Benisty et al. 2021 (cite: Benisty2021) (Band 7 data reduction and prior high-resolution PDS 70 observations)
- Companion: Liu et al. 2024 (cite: Liu2024) (Multi-wavelength ALMA and JVLA analysis of PDS 70 from the same Band 3 project family)
- Related: 2022.1.00893.S
- Related: 2022.1.01477.S
- Related: 2015.1.00888.S
- Related: 2018.A.00030.S

## Checks

```json
{
 "quotes": 128,
 "quotes_ok": 128,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 84,
  "rate": 0.778
 },
 "evidence_ok": true
}
```
