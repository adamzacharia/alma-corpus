# Detecting low-mass haloes with strong gravitational lensing I: the effect of data quality and lensing configuration

`2022MNRAS.510.2480D` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Despali, Giulia | arXiv: 2111.08718 | DOI: 10.1093/mnras/stab3537

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: cosmology, high_z_galaxies
- Question: How does the lowest halo mass that can be detected with galaxy-galaxy strong gravitational lensing depend on the quality of the observations and the characteristics of the observed lens systems?  
  > "This paper aims to quantify how the lowest halo mass that can be detected with galaxy-galaxy strong gravitational lensing depends on the quality of the observations and the characteristics of the observed lens systems." (Abstract)
- Target **SPT 0532-50**: coordinates _not stated_; z/distance z_L = 1.15, z_S = 3.399  
  > "SPT 0532$-$50 | ALMA1 | 1.15 | 3.399 | 0.557 | ALMA | - | 0.045 | - | band 7 | 880 $\mu$m" (Table 1); distance from _not stated_
- Target **J1110+3649**: coordinates _not stated_; z/distance z_L = 0.733, z_S = 2.502  
  > "J1110+3649 | BELLS1 | 0.733 | 2.502 | 1.141 | HST | 0.04 | 0.09 | WFC3 | F606W | 588.7 nm" (Table 1); distance from _not stated_
- Target **J1201+4743**: coordinates _not stated_; z/distance z_L = 0.563, z_S = 2.126  
  > "J1201+4743 | BELLS2 | 0.563 | 2.126 | 1.035 | HST | 0.04 | 0.09 | WFC3 | F606W | 588.7 nm" (Table 1); distance from _not stated_
- Target **JVAS B1938+666**: coordinates _not stated_; z/distance z_L = 0.881, z_S = 2.059  
  > "JVAS B1938+666 | SHARP1 | 0.881 | 2.059 | 0.4156 | Keck-AO | 0.01 | 0.07 | NIRC2 | K’ | 2200 nm" (Table 1); distance from _not stated_
- Target **NGC 5457**: coordinates _not stated_; z/distance low-z  
  > "In order to explore the effect of source structure further, we also use three additional source models, combined with the BELLS1 lens model: two analytical sources created with Gaussian distributions and the image of a low-$z$ spiral galaxy (NGC 5457) extracted from HST archival data (Proposal ID:13361, PI: Blair)." (Source and lens galaxies); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01374.S
- bands: band 7 (880 um)  
  > "SPT 0532$-$50 | ALMA1 | 1.15 | 3.399 | 0.557 | ALMA | - | 0.045 | - | band 7 | 880 $\mu$m" (Table 1); "To create this mock data, we use band 7 observations of SPT 0532$-$50 at 0.045 arcsec resolution (project code 2016.1.01374.S; PI: Hezaveh)." (Interferometric observations with ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.045 arcsec  
  > "SPT 0532$-$50 | ALMA1 | 1.15 | 3.399 | 0.557 | ALMA | - | 0.045 | - | band 7 | 880 $\mu$m" (Table 1); "To create this mock data, we use band 7 observations of SPT 0532$-$50 at 0.045 arcsec resolution (project code 2016.1.01374.S; PI: Hezaveh)." (Interferometric observations with ALMA)
- max recoverable scale: _not stated_
- sensitivity: median SNR = 4  
  > "M20 | ALMA1 | ALMA1 | 0.045 | - | 4 hours | 4 | 0.557 |" (Table 2)
- time on source: 4 hours  
  > "M20 | ALMA1 | ALMA1 | 0.045 | - | 4 hours | 4 | 0.557 |" (Table 2); "for the ALMA data considered in this work (M20), the integration time was 4 hours, thus reaching a number of expected detections significantly above one might prove to be extremely challenging." (Perspective on future observations)
- observing dates: _not stated_
- pi or archival as stated: Archival; PI: Hezaveh  
  > "To create this mock data, we use band 7 observations of SPT 0532$-$50 at 0.045 arcsec resolution (project code 2016.1.01374.S; PI: Hezaveh)." (Interferometric observations with ALMA); "We chose this system because it provides the best combination of SNR, angular resolution, and source redshift of currently available data in the ALMA archive." (Interferometric observations with ALMA)
- Other facility **Hubble Space Telescope (HST WFC3)**: F606W observations of BELLS-GALLERY systems (J1110+3649 and J1201+4743) and archival image of NGC 5457 (Proposal ID: 13361, PI: Blair; program 14189)  
  > "The BELLS-GALLERY sample consists of HST (WCF3, F606W) observations of high-redshift ($\bar{z}\sim3$) Lyman-alpha emitters lensed by ($\bar{z}\sim1$) massive Early-Type galaxies." (Source and lens galaxies); "and the image of a low-$z$ spiral galaxy (NGC 5457) extracted from HST archival data (Proposal ID:13361, PI: Blair)." (Source and lens galaxies); "These observations are associated with program 14189." (Public data and software)
- Other facility **Keck-II Adaptive Optics (NIRC2)**: K' band observations of JVAS B1938+666 from the SHARP survey  
  > "The SHARP survey focuses on Keck-II AO (NIRC2, K’ band) observations of red lensed galaxies." (Source and lens galaxies); "JVAS B1938+666 | SHARP1 | 0.881 | 2.059 | 0.4156 | Keck-AO | 0.01 | 0.07 | NIRC2 | K’ | 2200 nm" (Table 1)
- External data: Reconstructed pixellated background sources and smooth elliptical power-law lens models for BELLS1 and BELLS2  
  > "assuming a pixellated model for the background source galaxy and an elliptical power-law mass density profile for the foreground lens galaxy" (Mock data, Source and lens galaxies); "We start from their most probable reconstructed sources and lens them forward through their best smooth lens model (i.e. without the contribution of subhaloes), creating mock observations with the same set-up of the original data." (Source and lens galaxies) [from (cite: ritondale19a)]
- External data: Reconstructed pixellated background source and smooth elliptical power-law lens model for JVAS B1938+666 (SHARP1)  
  > "assuming a pixellated model for the background source galaxy and an elliptical power-law mass density profile for the foreground lens galaxy" (Mock data, Source and lens galaxies) [from (cite: vegetti12)]
- External data: Concentration-mass relation for NFW haloes  
  > "The typical values of $\rho_s$ and $r_{s}$ for haloes of given mass at each redshift are here set by the (redshift-dependent) concentration-mass relation (cite: duffy08)." (Sensitivity map) [from (cite: duffy08)]
- Simulation/model as data: 21 mock strong gravitational lens datasets (M1-M20) created by forward lensing reconstructed or analytical sources through smooth elliptical power-law lens models, convolving with PSF or Fourier transforming to visibilities, and adding noise  
  > "In total, we create 21 strong gravitational lens systems of varying configuration, SNR and angular resolution" (Mock data, Source and lens galaxies); "The mock data were created by directly overwriting the visibility data with the Fourier-transformed sky model, then adding Gaussian noise at the same level as measured in the actual data." (Interferometric observations with ALMA)

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

- Pixellated regularised source and lens modelling methodology  
  > "We follow (cite: vegetti09) and model the source $\mathbf{s}$ in a pixellated regularised fashion." (Lens modelling); "We refer the reader to the original paper and (cite: rybak15), (cite: rizzo18) and (cite: powell21) for more details on the lens modelling procedure." (Lens modelling) [from (cite: vegetti09); (cite: rybak15); (cite: rizzo18); (cite: powell21)]
- Interferometric extension of the pixellated lens modelling method  
  > "The real data were modelled using the pixellated method of (cite: vegetti09) extended for use with interferometric data as described in (cite: powell21)." (Interferometric observations with ALMA) [from (cite: vegetti09); (cite: powell21)]
- ALMA data reduction and lens modelling of SPT 0532-50  
  > "Further details of the data reduction and lens modelling will be given in Stacey et al. (in prep)." (Interferometric observations with ALMA) [from Stacey et al. (in prep)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction, calibration, and visibility averaging parameters (deferred to Stacey et al. in prep.)
- Exact macro-model parameters (kappa_0, gamma, q, position angle, external shear) for BELLS1, BELLS2, SHARP1, and ALMA1
- Prior ranges used in MultiNest for macro-model parameters and source regularization
- Spatial grid resolution on the lens plane and mass grid spacing used to compute the sensitivity maps

## Analysis recipe

1. **Model real observations and generate mock lensing datasets**: Start from most probable reconstructed pixellated sources and smooth elliptical power-law lens models of real HST, Keck-AO, and ALMA systems; forward lens sources, convolve with PSF (or overwrite ALMA visibilities with Fourier-transformed sky model), and add Poisson and/or Gaussian noise.  
  > "We start from their most probable reconstructed sources and lens them forward through their best smooth lens model (i.e. without the contribution of subhaloes), creating mock observations with the same set-up of the original data." (Source and lens galaxies); "The mock data were created by directly overwriting the visibility data with the Fourier-transformed sky model, then adding Gaussian noise at the same level as measured in the actual data." (Interferometric observations with ALMA)
   - parameter: Core radius r_c = 10^-4 arcsec fixed; 21 mock configurations M1-M20 varying FWHM (0.045, 0.07, 0.09, 0.16 arcsec), pixel scale (0.01, 0.04, 0.1 arcsec), and SNR  
  > "The core radius $r_c$ is fixed at $10^{-4}$ arcsec." (Lens modelling); "In total, we create 21 strong gravitational lens systems of varying configuration, SNR and angular resolution" (Mock data, Source and lens galaxies)
   - assumption: Elliptical power-law mass density profile plus external shear for the main lens; pixellated regularised background source  
  > "We represent the lens mass distribution by an elliptical power-law model, with dimensionless surface mass density given by" (Lens modelling); "In addition, an external shear component of strength $\Gamma$ and position angle $\Gamma_{\theta}$ is added to the model." (Lens modelling)
   - fitting: _not stated_
   - validation: _not stated_
2. **Calculate Bayesian evidence and sensitivity maps on a 2D grid of subhalo mass and position**: Create a 2D grid in subhalo mass (10^8 to 10^11 M_sun) and lens-plane position x; for each grid point, compute Bayesian evidence of the smooth model and perturbed model (with an NFW subhalo at z = z_L) marginalising over source and main lens parameters, and find the lowest mass M_low where Delta log E >= 50.  
  > "as the mass of an NFW subhalo that, when added to the main lens, creates a difference in the Bayes factor between the smooth and perturbed models of" (Methodology, Sensitivity map); "In practice, we create a two-dimensional grid in subhalo mass and position and for each point on this grid we perform the integral" (Methodology, Sensitivity map); "Given the quality of the data used here, we consider masses between $10^{8}$ and $10^{11}M_{\odot}$." (Sensitivity map)
   - software: MultiNest
   - parameter: Detection threshold Delta log E >= 50 (roughly 10-sigma); subhalo mass range 10^8 to 10^11 M_sun  
  > "The threshold $\Delta\log E \geq50$ is chosen because it roughly corresponds to a 10-$\sigma$ detection threshold (cite: ritondale19b) and has been established as a reliable way to limit the rate of false-positive detections, and so to provide robust and conservative results (cite: ritondale19b)." (Sensitivity map); "Given the quality of the data used here, we consider masses between $10^{8}$ and $10^{11}M_{\odot}$." (Sensitivity map)
   - assumption: Perturbing subhaloes located at z = z_L follow spherical NFW profiles with concentration fixed to the mean redshift-dependent concentration-mass relation of Duffy et al. (2008)  
  > "We describe the perturbing subhaloes with NFW profiles (cite: navarro96)," (Sensitivity map); "This means that here we fix the subhalo concentration to the mean value $\bar{c}(m)$ predicted by the relation for any given mass at the redshift of the lens $z=z_{L}$." (Sensitivity map)
   - fitting: Bayesian evidence integration with MultiNest assuming uniform priors on lens parameters eta and uniform prior in logarithmic space on source regularisation lambda_s, marginalising over both source and main lens parameters  
  > "Both integrals are performed with MultiNest (cite: feroz13) assuming uniform priors on the parameters $\boldsymbol{\eta}$ and a uniform prior in logarithmic space on the source regularisation $\lambda_{s}$." (Lens modelling); "Unlike them, we marginalise both over the source (including its regularisation level) and over the main lens parameters." (Sensitivity map)
   - validation: Tested stability against 30 Gaussian noise realisations of BELLS2, marginalisation vs fixed macro-model parameters (Appendix 8), and lower detection thresholds Delta log E = 12.5 and 35 (Appendix 10)  
  > "For this, we created 30 additional mocks of the system BELLS2 at the original level of noise." (Noise realisation); "Instead of the fiducial value $\Delta\log E$=50, adopted throughout the paper, we use two lower evidence threshold: 12.5 and 35." (On the sensitivity threshold)
3. **Quantify dependence of M_low and sensitive area on SNR, angular resolution, and lensing configuration**: Compare sensitivity maps across the 21 mock systems to derive analytic linear scaling of Delta log M_low with SNR/SNR_0 and evaluate changes in mean/minimum M_low and sensitive area.  
  > "On average, $M_{\rm low}$ decreases linearly with SNR as:" (The effect of the signal-to-noise ratio); "In Figure [5], we summarise the results for all systems, in terms of the sensitive area and the minimum and mean values of $M_{\rm low}$ in the maps." (Sensitivity for improved data)
   - software: Astropy, NumPy, SciPy, matplotlib
   - fitting: Linear relation between Delta log M_low and SNR/SNR_0  
  > "On average, $M_{\rm low}$ decreases linearly with SNR as:" (The effect of the signal-to-noise ratio)
   - validation: _not stated_

## Software

- **MultiNest** : Performing Bayesian evidence integrals for smooth and perturbed lens models  
  > "Both integrals are performed with MultiNest (cite: feroz13) assuming uniform priors on the parameters $\boldsymbol{\eta}$ and a uniform prior in logarithmic space on the source regularisation $\lambda_{s}$." (Lens modelling)
- **Astropy** : General astronomical analysis  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy13), of the matplotlib (cite: matplotlib), SciPy (cite: scipy) and NumPy (cite: numpy) packages." (Public data and software)
- **matplotlib** : Plotting and data visualisation  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy13), of the matplotlib (cite: matplotlib), SciPy (cite: scipy) and NumPy (cite: numpy) packages." (Public data and software)
- **SciPy** : Scientific computing  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy13), of the matplotlib (cite: matplotlib), SciPy (cite: scipy) and NumPy (cite: numpy) packages." (Public data and software)
- **NumPy** : Numerical computations  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy13), of the matplotlib (cite: matplotlib), SciPy (cite: scipy) and NumPy (cite: numpy) packages." (Public data and software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Minimum detectable subhalo mass in ALMA mock (M20 / SPT 0532-50) | 1.8e9 | not stated | M_odot | 2 | From the sensitivity map calculation, we find these observations to be sensitive to haloes at the redshift of the lens in the mass range $M\geq1.8\times10^{9}M_{\odot}$. |
| Range of minimum detectable mass across sensitive mock images | 1.5e8 to 3e9 | not stated | M_odot | 2 | We find that for the sensitive mock images considered in this work, the minimum mass that we can detect at the redshift of the lens lies between $1.5\times10^{8}$ and $3\times10^{9}M_{\odot}$. |
| Average improvement in M_low from angular resolution increase (0.07 arcsec vs 0.09 arcsec) | 0.25 | not stated | dex | 3 | (ii) a moderate increase in angular resolution (0.07" vs 0.09") and pixel scale (0.01" vs 0.04") improves the sensitivity by on average 0.25 dex in halo mass, with more significant improvement around the most sensitive regions;; In this case, the average gain in $M_{\rm low}$ is 0.25 dex at all masses, with a larger spread at the intermediate values of $M_{\rm low}$ and a tendency for larger improvements at the locations where the sensitivity is already good (see the right panel of Figure [6]). |
| Intercept of linear relation between Delta log M_low and SNR/SNR_0 | 1.5 | +-0.1 | dimensionless | 3 | \Delta\log M_{\rm low} = \log \frac{M_{\rm low}}{M_{\rm low,0}} = 1.5(\pm0.1) -0.725(\pm0.12)\times \mathrm{\frac{SNR}{SNR_{0}}}, |
| Slope of linear relation between Delta log M_low and SNR/SNR_0 | -0.725 | +-0.12 | dimensionless | 3 | \Delta\log M_{\rm low} = \log \frac{M_{\rm low}}{M_{\rm low,0}} = 1.5(\pm0.1) -0.725(\pm0.12)\times \mathrm{\frac{SNR}{SNR_{0}}}, |
| Improvement in minimum M_low from centrally-aligned source position (M15 vs M14) / source structure and position | 0.5 | not stated | dex | 3 | Even if the overall median SNR is comparable, M15 is clearly a more promising system for dark matter studies: in the bottom panel of Figure [5], we see that the minimum $M_{\rm low}$ value is $\sim$0.5 dex lower than in M14.; a brighter and more structured source and a source located mostly within the caustic lines (thus more magnified) can lead to an improvement in the mean $M_{\rm low}$ of $\sim$0.5 dex. |
| Uncertainty in M_low due to different Gaussian noise realisations | 0.15 | not stated | dex | 2 | We find that the measurement of the sensitivity map is quite stable for different noise realisations, leading to fluctuations in evidence of the order of $\simeq$10 and, in turn, to uncertainties in the $M_{\rm low}$ values within 0.15 dex. |
| Mean log(M_low/M_odot) for BELLS1 at Delta log E = (12.5, 35, 50) | 10.32, 10.43, 10.6 | not stated | log(M_odot) | 2 | For these maps the mean value of $M_{\rm low}$ for $\Delta\log$Ev= (12.5,35,50) is (10.32,10.43,10.6) for BELLS1 and (10.1,10.42,10.8) for BELLS2. |
| Mean log(M_low/M_odot) for BELLS2 at Delta log E = (12.5, 35, 50) | 10.1, 10.42, 10.8 | not stated | log(M_odot) | 2 | For these maps the mean value of $M_{\rm low}$ for $\Delta\log$Ev= (12.5,35,50) is (10.32,10.43,10.6) for BELLS1 and (10.1,10.42,10.8) for BELLS2. |
| Minimum log(M_low/M_odot) for BELLS1 at Delta log E = (12.5, 35, 50) | 9, 9, 9.2 | not stated | log(M_odot) | 2 | The minimum $M_{\rm low}$ value is instead (9,9,9.2) and (9.,9.25,9.375). |
| Minimum log(M_low/M_odot) for BELLS2 at Delta log E = (12.5, 35, 50) | 9., 9.25, 9.375 | not stated | log(M_odot) | 2 | The minimum $M_{\rm low}$ value is instead (9,9,9.2) and (9.,9.25,9.375). |

## Qualitative findings

- Marginalising over main lens parameters is essential when computing sensitivity maps for NFW subhaloes; keeping macro-model parameters fixed leads to overly optimistic sensitivity maps.  
  > "Failing to allow readjustment of the main lens potential can lead to overly optimistic predictions for the sensitivity: a large difference in Bayesian evidence arising from a failure to reproduce the image positions can be compensated by a small change in the (a priori unknown) main lens parameters without requiring a superposed small halo." (Sensitivity map); "In the second case, given that we are dealing with a higher mass far from the lensed images, the residuals and the Bayes factor are much higher for a fixed macro model, leading to an overly optimistic sensitivity map." (Main lensing potential)
- Mock images with Euclid-like resolution (PSF FWHM 0.16 arcsec, pixel scale 0.1 arcsec; M18 and M19) are insensitive to NFW haloes with M <= 5 x 10^10 M_odot.  
  > "Finally, we calculate the sensitivity maps for the two systems with the lowest resolution M18 and M19 (PSF FWHM of 0.16 arcsec, pixel scale of 0.1 arcsec) and found them insensitive to NFW haloes in the mass range $M\leq5\times10^{10}M_{\odot}$." (The effect of the angular resolution)

## Claim tuples

- H: Increasing the signal-to-noise ratio of strong lensing observations lowers the minimum detectable subhalo mass and increases the sensitive area on the lens plane. | E: Generated mock HST lensing images (M1-M3 and M4-M6) with SNR increased by factors of ~2 and ~3.16 and calculated Bayesian sensitivity maps. | R: log(M_low/M_low,0) decreases linearly with SNR/SNR_0 with slope -0.725(+-0.12), and the sensitive area expands far from the brightest lensed images. | F: Higher SNR consistently lowers M_low across the lens plane and enlarges the sensitive area, particularly improving sensitivity at the high-mass end. | **supported**
- H: Increasing the angular resolution of strong lensing observations improves sensitivity to low-mass NFW haloes. | E: Compared sensitivity maps of paired mock datasets with matched SNR per unit area at 0.09 arcsec FWHM / 0.04 arcsec pixels (M10-M13) versus 0.07 arcsec FWHM / 0.01 arcsec pixels (M14-M17), plus Euclid-like mocks (M18-M19) and an ALMA 0.045 arcsec mock (M20). | R: M10-M12 and M18-M19 are insensitive to NFW haloes in the explored range, whereas M14-M16 are sensitive; comparing M17 to M13 shows an average gain of 0.25 dex in M_low, and ALMA mock M20 reaches M >= 1.8 x 10^9 M_odot. | F: Even a moderate improvement in angular resolution and pixel scale improves M_low by ~0.25 dex on average (especially in the most sensitive regions) and is essential to detect low-mass NFW haloes. | **supported**
- H: Source structure, source alignment with caustics, and Einstein radius size strongly impact subhalo mass sensitivity. | E: Compared mock images with analytical Gaussian, clumpy, and spiral galaxy sources (M1, M7, M8, M9), shifted source positions relative to caustics (M14 vs M15), and different Einstein radii (M16 vs M17). | R: More structured/brighter sources and sources inside the caustic lines improve mean/minimum M_low by ~0.5 dex and increase the sensitive area; larger Einstein radii yield larger sensitive areas. | F: Sensitivity to low-mass haloes is maximised for bright, structured lensed galaxies located inside the caustic curves and lensed into larger Einstein rings (r_E >= 1.0 arcsec). | **supported**

## Reasoning

- Why this data: Simulated mock data based on real HST (BELLS-GALLERY), Keck-AO (SHARP), and ALMA (SPT 0532-50) systems were chosen to systematically vary SNR, resolution, and lensing configuration in a controlled fashion; SPT 0532-50 was selected as having the best combination of SNR, angular resolution, and source redshift in the ALMA archive.  
  > "We chose, therefore, to work with mock data so that we can investigate the effect of each variable in a controlled fashion while keeping uncertainties and systematic errors under control." (Mock data); "We chose this system because it provides the best combination of SNR, angular resolution, and source redshift of currently available data in the ALMA archive." (Interferometric observations with ALMA)
- Why this method: Detailed Bayesian sensitivity maps marginalising over both the pixellated source and main lens parameters are necessary to account for degeneracies between the macro-model and diffuse NFW subhaloes and to avoid overly optimistic forecasts.  
  > "Our results will demonstrate that an accurate sensitivity map is a sine qua non for inferring constraints on structure formation models from the observations." (Methodology); "Unlike them, we marginalise both over the source (including its regularisation level) and over the main lens parameters." (Sensitivity map)
- Alternative: Fixing the main lens macro-model parameters when computing the sensitivity map (as in Vegetti et al. 2014 for Pseudo-Jaffe profiles) was tested and rejected for NFW profiles because it fails to account for macro-model degeneracy and yields overly optimistic sensitivity maps.  
  > "Failing to allow readjustment of the main lens potential can lead to overly optimistic predictions for the sensitivity: a large difference in Bayesian evidence arising from a failure to reproduce the image positions can be compensated by a small change in the (a priori unknown) main lens parameters without requiring a superposed small halo." (Sensitivity map); "In the second case, given that we are dealing with a higher mass far from the lensed images, the residuals and the Bayes factor are much higher for a fixed macro model, leading to an overly optimistic sensitivity map." (Main lensing potential)
- Alternative: Pseudo-Jaffe (PJ) subhalo mass profiles were compared against NFW profiles to explain why B1938+666 (M14) showed a subhalo detection in Vegetti et al. (2012) at a mass below the NFW M_low map.  
  > "When we consider a PJ profile, we find values of $M_{\rm low}$ consistent with the mass detected in the real data." (The effect of the angular resolution)
- How they decided it was enough: _not stated_
- Limitation (authors): Only perturbers at the lens redshift (subhaloes) with fixed mean NFW concentration-mass relation are considered here; line-of-sight field haloes and concentration scatter are deferred to Paper II.  
  > "In this first paper we discuss the detectability of perturbers located at the redshift of the main lens (i.e. subhaloes), focusing on estimates of the detectable masses and the dependence on the lensing configuration, data quality and source structure." (Introduction); "This means that here we fix the subhalo concentration to the mean value $\bar{c}(m)$ predicted by the relation for any given mass at the redshift of the lens $z=z_{L}$." (Sensitivity map)
- Limitation (authors): Higher SNR mock images were generated from sources reconstructed from lower SNR real observations and thus may lack small-scale source features.  
  > "We created all the mock images presented here from the reconstructed sources of real observations with the lowest SNR considered. As a result our higher SNR images may be missing small scale features compared to an actual observation of comparable quality." (The effect of the signal-to-noise ratio)
- Limitation (authors): In reality, changing angular resolution requires changing instrument or wavelength filter, which changes the intrinsic morphology of the lensed source.  
  > "One limitation of this approach is that, in reality, an increase in resolution requires a change of instrument, or filter, leading to source galaxies with a different structure." (Noise model)
- Limitation (authors): The direct resolution comparison between M13 and M17 is based on a single system using a rescaled low-z spiral galaxy (NGC 5457) that may be morphologically unrealistic for high-z sources.  
  > "This is a promising result, but it should be interpreted with caution, given that it is based on only one system and the source model used here is a rescaled low-$z$ spiral galaxy, that could be unrealistic in terms of morphology." (The effect of the angular resolution)
- Caveat (inferred, ours): Only a single ALMA mock dataset (M20) is analysed, limiting general conclusions about interferometric subhalo sensitivity across diverse uv-coverages.
- Caveat (inferred, ours): The ALMA data reduction and lens model for SPT 0532-50 are taken from an unpublished work in preparation (Stacey et al. in prep).

## Reproducibility

- Data public (paper): Original HST, Keck-AO, and ALMA data are publicly available in archives; simulated mock data and images are available upon request from the corresponding author.  
  > "The images and mock data analysed in this work are available upon request to the corresponding author." (Data availability); "Moreover, the original HST, Keck-AO and ALMA images for the considered systems are publicly available in the corresponding archives." (Data availability)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: The proprietary pixellated gravitational lens modelling and visibility-plane modelling code (from Vegetti & Koopmans 2009 / Powell et al. 2021) is not publicly released.
- Missing: Exact best-fit smooth lens parameters and reconstructed pixellated source maps used as inputs to generate M1-M20 (available only upon request or in Stacey et al. in prep for ALMA1).
- Missing: ALMA calibration and visibility data reduction steps for 2016.1.01374.S.
- Data volume (inferred): Small (<10 GB) for the mock images and visibility dataset, though high-performance computing is needed for the MultiNest sensitivity map grids.
- Score (inferred): 4/5, The methodology and mock parameters are clearly explained and archival raw data are public, but the core pixellated lens modelling software is not publicly released, the mock datasets require requesting from the author, and the ALMA data reduction/modelling details are deferred to a paper in preparation.
- Rediscovery candidate: no, The paper analyses synthetic mock data generated from proprietary lens reconstructions and an unpublished ALMA model (Stacey et al. in prep), and requires specialized non-public Bayesian pixellated lensing code.

## Links

- Method: (cite: vegetti09) (Foundational Bayesian pixellated source and lens modelling method used throughout the paper)
- Method: (cite: powell21) (Extension of the pixellated lens modelling method to interferometric visibility data used for ALMA1)
- Method: (cite: rybak15) (Lens modelling procedure details)
- Method: (cite: rizzo18) (Lens modelling procedure details)
- Method: (cite: feroz13) (MultiNest nested sampling algorithm used to compute Bayesian evidence)
- Companion: Stacey et al. (in prep) (Provides the ALMA data reduction and lens modelling of SPT 0532-50 used to create mock M20)
- Companion: Vegetti et al. in prep. (Discusses ELT/GMT/TMT constraints on the halo mass function)
- Related: BELLS-GALLERY
- Related: SHARP
- Related: SPT
- Related: SLACS
- Related: Euclid

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 46,
  "rate": 0.505
 },
 "evidence_ok": true
}
```
