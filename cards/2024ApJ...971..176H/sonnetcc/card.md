# Unraveling the Mystery of the Low CO-to-H<SUB>2</SUB> Conversion Factor in Starburst Galaxies: RADEX Modeling of the Antennae

`2024ApJ...971..176H` | The Astrophysical Journal 2024 | first author: He, Hao | arXiv: 2401.16476 | DOI: 10.3847/1538-4357/ad5544

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What is the CO-to-H2 conversion factor (alpha_CO) in the starburst merger the Antennae at GMC (150 pc) and kpc scales, how does it depend on CO intensity, 13CO/CO ratio and velocity dispersion, and what does it imply for GMC dynamical states  
  > "In this paper, we perform LVG modeling on high-resolution ($\sim$ 150 pc) CO and $^{13}$CO molecular lines from ALMA observations of the Antennae to constrain the physical properties of the molecular gas and $\alpha_{\mathrm{CO}}$ at both GMC and kpc scales." (Introduction)
- Target **The Antennae (NGC 4038/9)**: coordinates _not stated_; z/distance 22 Mpc  
  > "At a distance of 22 Mpc (cite: schweizer2008), ALMA can readily resolve molecular gas at GMC scales." (Introduction); distance from Schweizer et al. 2008 (cite: schweizer2008)  
  > "At a distance of 22 Mpc (cite: schweizer2008), ALMA can readily resolve molecular gas at GMC scales." (Introduction)

## Data provenance

- ALMA projects: 2018.1.00272.S, 2021.1.00439.S
- bands: Band 3, 6 and 7 (CO 1-0 and 13CO 1-0 in Band 3; CO 2-1 and 13CO 2-1 in Band 6; CO 3-2 and continuum in Band 7)  
  > "We obtained ALMA Band 3, 6 and 7 observations from cycle 5 project 2018.1.00272.S and cycle 8 project 2021.00439.S to capture multiple CO and $^{13}$CO lines." (2.1 ALMA Spectral Lines); "continuum | 2021.1.00439.S | 7 | $0.65\ensuremath{''}$, 72 pc | $0.34\ensuremath{'}$, 2.2 kpc | – | 0.18 mJy/beam | 0.4 mJy/beam" (Table 1)
- frequencies and spectral setup: Five lines (CO 1-0, 2-1, 3-2, 13CO 1-0, 2-1); C18O 1-0 and 2-1 detected in same tuning as 13CO; velocity resolution 2.54 km/s (CO 1-0, 2-1), 3.4 km/s (CO 3-2), 2.7 km/s (13CO 1-0), 5.3 km/s (13CO 2-1); continuum has no TP data  
  > "we also have C$^{18}$O $J$=1-0 and 2-1 detected in the same spectral tuning as $^{13}$CO $J$=1-0 and 2-1, respectively." (2.1 ALMA Spectral Lines); "$^{13}$CO $J$=2-1 | 2018.1.00272.S | 6 | $0.71\ensuremath{''}$, 76 pc | $6.9\ensuremath{'}$, 44 kpc | 5.3 km s$^{-1}$ | 0.09 K | 0.05 K" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12 m array (compact and extended configurations), 7 m array (ACA) and total power (TP); continuum has no TP  
  > "we have observations from the 12 m-array used in both a compact and extended configuration, 7 m-array (ACA) and total power (TP) array" (2.1 ALMA Spectral Lines); "The continuum does not have TP observations." (2.1 ALMA Spectral Lines)
- configurations: 12 m array in compact and extended configurations (specific configuration names not given)  
  > "we have observations from the 12 m-array used in both a compact and extended configuration" (2.1 ALMA Spectral Lines)
- baselines: _not stated_
- angular resolution: Native (smallest round beam): 0.84 arcsec (90 pc) CO 1-0; 0.51 arcsec (54 pc) CO 2-1; 0.67 arcsec (71 pc) CO 3-2; 1.41 arcsec (150 pc) 13CO 1-0; 0.71 arcsec (76 pc) 13CO 2-1; 0.65 arcsec (72 pc) continuum. All smoothed to 150 pc (1.41 arcsec); also 1 kpc  
  > "CO $J$=2-1 | 2018.1.00272.S | 6 | $0.51\ensuremath{''}$, 54 pc | $6.9\ensuremath{'}$, 44 kpc | 2.54 km s$^{-1}$ | 0.24 K | 0.11 K" (Table 1); "We smooth all five image cubes to the resolution of 150 pc (1.41 arcsec)" (2.1 ALMA Spectral Lines); "In Section 7, we will also use the five CO and $^{13}$CO maps at a resolution of 1 kpc." (2.1 ALMA Spectral Lines)
- max recoverable scale: Largest angular scale: 14.5 arcmin (93 kpc) CO 1-0; 6.9 arcmin (44 kpc) CO 2-1 and 13CO 2-1; 4.5 arcmin (29 kpc) CO 3-2; 15 arcmin (96 kpc) 13CO 1-0; 0.34 arcmin (2.2 kpc) continuum  
  > "(5) Largest angular scale." (Table 1); "$^{13}$CO $J$=1-0 | 2021.1.00439.S | 3 | $1.41\ensuremath{''}$, 150 pc | $15\ensuremath{'}$, 96 kpc | 2.7 km s$^{-1}$ | 0.04 K | 0.04 K" (Table 1)
- sensitivity: Cube noise at native / 150 pc: CO 1-0 0.09 / 0.05 K; CO 2-1 0.24 / 0.11 K; CO 3-2 0.09 / 0.04 K; 13CO 1-0 0.04 / 0.04 K; 13CO 2-1 0.09 / 0.05 K; continuum 0.18 / 0.4 mJy/beam  
  > "(7) Noise of the image cubes at the native resolution. (8) Noise of the image cubes after smoothing to the resolution of 150 pc." (Table 1); "CO $J$=1-0 | 2018.1.00272.S | 3 | $0.84\ensuremath{''}$, 90 pc | $14.5\ensuremath{'}$, 93 kpc | 2.54 km s$^{-1}$ | 0.09 K | 0.05 K" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Line: CO J=2-1 (not stated)
- Line: CO J=3-2 (not stated)
- Line: 13CO J=1-0 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=1-0 and 2-1 (detected, not modeled) (not stated)
- Other facility **Spitzer**: 3.6 um (Program 10136) and 4.5 um (Program 61068) images used for stellar mass surface density at kpc scale  
  > "We use the *Spitzer* 3.6 $\mu$m (Program 10136) and 4.5 $\mu$m (Program 61068) data to calculate the stellar mass surface density of the Antennae at kpc scale." (2.3 Spitzer Data)
- External data: Dust temperatures for each subregion and overall dust temperature of the galaxy (about 20 K)  
  > "We adopt the dust temperature from (cite: klaas2010) for pixels in each defined subregion" (7.1 / 6.1 dust); "The dust temperature calculated in (cite: klaas2010) is $\sim$ 20 K" (6.1 dust) [from Klaas et al. 2010 (cite: klaas2010)]
- External data: Dust mass equation and fiducial dust opacity kappa = 0.9 g^-1 cm^2  
  > "We chose 0.9 g$^{-1}$ cm$^{2}$ as the fiducial value for $\kappa$ (cite: wilson_luminous_2008)" (6.1 Constraining the xCO abundance ratio with the dust mass) [from Wilson et al. 2008 (cite: wilson_luminous_2008)]
- External data: Stellar mass equation from Spitzer 3.6 and 4.5 um fluxes  
  > "We then calculate the stellar mass for each pixel with the equation (cite: eskew2012)" (2.3 Spitzer Data) [from Eskew et al. 2012 (cite: eskew2012)]
- External data: [CO]/[H2] abundance ratio of 3e-4, commonly adopted for starburst systems  
  > "The value we assume (3$\times 10^{-4}$) is commonly adopted for starburst systems (cite: sliwa2017)." (3.2 Modeling of the CO-to-H2 conversion factor) [from Sliwa et al. 2017 (cite: sliwa2017)]
- External data: Distance to the Antennae of 22 Mpc  
  > "At a distance of 22 Mpc (cite: schweizer2008), ALMA can readily resolve molecular gas at GMC scales." (Introduction) [from Schweizer et al. 2008 (cite: schweizer2008)]
- External data: Simulation prediction relations of alpha_CO versus CO intensity (slope -0.32), compared with the observed fits  
  > "We can see that our power-law fit has almost the same slope as that predicted (slope of -0.32) in (cite: narayanan2012)." (5.1 Dependence on CO J=1-0 intensity) [from Narayanan et al. 2012 (cite: narayanan2012); also Gong et al. 2020 (cite: gong2020), Hu et al. 2022 (cite: hu2022)]
- Simulation/model as data: RADEX one-component 5D model grids of integrated line intensities for the five lines (n, Tkin, NCO, X12/13, beam filling factor) fitted to observed intensities per pixel  
  > "We adopt the one-component RADEX modeling to generate 5D grids of integrated line intensities for the five lines" (3.1 General Modeling Procedure)

## Processing

### Calibration

- pipeline or manual: Observatory-supplied calibration scripts with the appropriate CASA pipeline version  
  > "We calibrate the raw visibility data with the observatory-supplied calibration scripts and the appropriate version of the CASA pipeline." (2.1 ALMA Spectral Lines)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Modified version of the PHANGS-ALMA imaging pipeline (Leroy et al. 2021); visibilities extracted and imaged per molecular line  
  > "we extract and image a relevant subset of visibility data for each molecular line using a modified version of the PHANGS–ALMA imaging pipeline (cite: leroy2021)" (2.1 ALMA Spectral Lines)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "For the weighting of the visibility data, we adopt the *Briggs* method with robustness parameter of 0.5." (2.1 ALMA Spectral Lines)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Continuum: auto-multithresh. Moment-map masks: high-confidence mask of at least two consecutive channels with S/N above 5, expanded to S/N above 2 for at least two consecutive channels, combined over lines into a common 'combo' mask  
  > "We then use the `auto-multithresh` algorithm to clean the continuum data down to threshold of 2 $\times$ RMS (RMS of $\sim$ 0.18 mJy/beam)." (2.2 ALMA continuum); "starts from a high-confidence mask including at least two consecutive channels with S/N above 5 and then expand the mask to include pixels with S/N above 2 for at least two consecutive channels." (2.1 ALMA Spectral Lines)
- multiscale scales: _not stated_
- continuum subtraction: 1st-order fit to line-free channels, subtracted before line imaging  
  > "Before imaging the lines, we performed continuum subtraction by subtracting the 1st-order fit modeling on line-free channels." (2.1 ALMA Spectral Lines)
- line free channels: _not stated_
- primary beam correction: Applied after cleaning and feathering  
  > "After the cleaning, we then feather the cleaned image product with TP data and apply the primary beam correction to get final image cubes for each line." (2.1 ALMA Spectral Lines)
- array combination: 12m and 7m measurement sets combined before imaging; cleaned image feathered with TP data  
  > "We then combine the 12m and 7m measurement sets together and perform the imaging." (2.1 ALMA Spectral Lines); "we then feather the cleaned image product with TP data" (2.1 ALMA Spectral Lines)
- smoothing: All cubes smoothed to 150 pc (1.41 arcsec) and matched to the CO 1-0 grid; moment 0 and effective width maps Nyquist-sampled; also 1 kpc version  
  > "We smooth all five image cubes to the resolution of 150 pc (1.41 arcsec) and match all their spatial grids to the CO $J$=1-0 line." (2.1 ALMA Spectral Lines); "we Nyquist-sample the moment 0 and effective width maps for all the lines to remove the spatial correlation between different pixels." (2.1 ALMA Spectral Lines)
- final beam: Smallest round beam at native resolution; 150 pc (1.41 arcsec) for the common-resolution analysis  
  > "We also smooth all the images to the smallest round beam." (2.1 ALMA Spectral Lines)
- final rms: At 150 pc: CO 1-0 0.05 K, CO 2-1 0.11 K, CO 3-2 0.04 K, 13CO 1-0 0.04 K, 13CO 2-1 0.05 K, continuum 0.4 mJy/beam (continuum native RMS ~0.18 mJy/beam)  
  > "(8) Noise of the image cubes after smoothing to the resolution of 150 pc." (Table 1); "CO $J$=2-1 | 2018.1.00272.S | 6 | $0.51\ensuremath{''}$, 54 pc | $6.9\ensuremath{'}$, 44 kpc | 2.54 km s$^{-1}$ | 0.24 K | 0.11 K" (Table 1)

### Inherited from earlier work

- Imaging steps follow the PHANGS-ALMA imaging scheme, with a modified version of the PHANGS-ALMA imaging pipeline  
  > "The imaging steps generally follow the PHANGS imaging scheme (cite: leroy2021)." (2.1 ALMA Spectral Lines) [from Leroy et al. 2021 (cite: leroy2021)]
- Masking scheme for moment maps from the PHANGS-ALMA pipeline  
  > "we start with generating masks adopting the scheme of the PHANGS-ALMA pipeline" (2.1 ALMA Spectral Lines) [from PHANGS-ALMA pipeline (cite: leroy2021)]
- Continuum processing (combining 12m and 7m, extracting line-free channels) uses the PHANGS-ALMA pipeline  
  > "we use the PHANGS-ALMA pipeline (cite: leroy2021) to combine the 12m and 7m measurement sets and extract the line-free channels from the combined measurement set for the continuum imaging." (2.2 ALMA continuum) [from Leroy et al. 2021 (cite: leroy2021)]
- RADEX modeling code, Bayesian likelihood analysis and alpha_CO derivation adapted from earlier work  
  > "We briefly summarize the code and our adaptation below (cite: teng2022; teng2023)." (3.1 General Modeling Procedure); "We then follow the Bayesian likelihood analyses in (cite: teng2022) to characterize the probability density function (PDF) for the five varying parameters" (3.1 General Modeling Procedure) [from Teng et al. 2022 (cite: teng2022); Teng et al. 2023 (cite: teng2023)]
- Fiducial linewidth of 15 km/s for the RADEX grid  
  > "The 15 km s$^{-1}$ is the fiducial value used in (cite: teng2022; teng2023)." (3.1 General Modeling Procedure) [from Teng et al. 2022, 2023 (cite: teng2022; teng2023)]
- alpha_CO definition and posterior derivation method  
  > "We then follow the method in (cite: teng2022) and (cite: teng2023) to derive the posterior probability of $\alpha_{\mathrm{CO}}$" (3.2 Modeling of the CO-to-H2 conversion factor) [from Teng et al. 2022, 2023 (cite: teng2022; teng2023)]
- Effective width as a velocity dispersion estimate rather than moment 2  
  > "because it gives a more stable estimate of velocity dispersion within clouds, specifically if two or more clouds are along the same line of sight (cite: heyer2001; sun_cloud-scale_2018)" (2.1 ALMA Spectral Lines) [from Heyer et al. 2001 (cite: heyer2001); Sun et al. 2018 (cite: sun_cloud-scale_2018)]
- Theoretical slope of -0.5 for alpha_CO versus velocity dispersion  
  > "This power-law slope is derived from theoretical predictions under the LVG approximation for two-level optically thick systems" (5.3 Dependence on GMC velocity dispersion) [from Teng et al. 2024 (cite: teng2024)]

### Not stated but needed to reproduce (our reading)

- CASA version and CASA pipeline version used for each project, and which calibration scripts and execution blocks were used
- What the 'modified' PHANGS-ALMA imaging pipeline changes relative to the public one, and its version
- Line-free channel ranges and continuum fit windows for the 1st-order continuum subtraction
- tclean parameters for lines: deconvolver, cell and image size, niter, thresholds, line cleaning masks, mosaic pointings
- Feathering details with the TP data (scaling, uv range) and units conversion to Kelvin
- Flux calibrator, flux scale uncertainty and any self-calibration
- Observing dates, PI and number of execution blocks or pointings
- Per-pixel measurement uncertainty sigma_i used in the chi2 (how moment-0 errors were computed)
- Fitting method for the power-law relations (least squares, orthogonal, weighting, treatment of correlated Nyquist pixels and alpha_CO uncertainties)
- Subregion definitions and the dust temperature values assigned per subregion (from Klaas et al. 2010), and the assumed T_dust for subregion A1a
- How the GMC virial parameter and surface density contours of the dynamical-state analysis are computed
- Continuum frequency range and bandwidth
- CO and 13CO rest frequencies and the RADEX collision-rate files used

## Analysis recipe

1. **Calibrate and image the five CO and 13CO line cubes**: Run observatory calibration scripts with CASA pipeline, then image per line with a modified PHANGS-ALMA imaging pipeline (continuum subtraction, 12m+7m combination, Briggs weighting, feathering with TP, primary beam correction, conversion to Kelvin)  
  > "We calibrate the raw visibility data with the observatory-supplied calibration scripts and the appropriate version of the CASA pipeline." (2.1 ALMA Spectral Lines); "In the final step, we convert all the image cubes to units of Kelvin (K)." (2.1 ALMA Spectral Lines)
   - software: CASA, PHANGS-ALMA imaging pipeline
   - parameter: Briggs robust = 0.5; 1st-order continuum fit on line-free channels  
  > "For the weighting of the visibility data, we adopt the *Briggs* method with robustness parameter of 0.5." (2.1 ALMA Spectral Lines); "we performed continuum subtraction by subtracting the 1st-order fit modeling on line-free channels." (2.1 ALMA Spectral Lines)
   - fitting: _not stated_
   - validation: _not stated_
2. **Homogenize cubes to 150 pc and make moment and effective-width maps**: Smooth all cubes to 150 pc (1.41 arcsec), regrid to the CO 1-0 grid, build a common combo mask, make moment 0 and effective width maps with error maps, apply S/N cut of 3 on moment 0, Nyquist-sample  
  > "We run this scheme for each line and combine all the mask together to create a "combo" mask." (2.1 ALMA Spectral Lines); "We also apply a S/N cut of 3 to the moment 0 maps of each line to exclude noisy pixels in weak line maps." (2.1 ALMA Spectral Lines)
   - software: PHANGS-ALMA pipeline
   - parameter: Effective width sigma_v = I / (sqrt(2 pi) T_peak), ratio of moment 0 to peak brightness temperature (moment 8)  
  > "the effective width is measured as the ratio between integrated intensity (moment 0) and peak brightness temperature (moment 8) maps" (2.1 ALMA Spectral Lines)
   - parameter: Mask: at least two consecutive channels with S/N above 5, expanded to S/N above 2 for at least two consecutive channels  
  > "starts from a high-confidence mask including at least two consecutive channels with S/N above 5 and then expand the mask to include pixels with S/N above 2 for at least two consecutive channels." (2.1 ALMA Spectral Lines)
   - assumption: For a Gaussian line profile the effective width equals the moment 2 width  
  > "For a perfect Gaussian line profile, the effective width is identical to the traditionally used moment 2 measurements." (2.1 ALMA Spectral Lines)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image Band 7 continuum for dust mass**: Combine 12m and 7m, extract line-free channels, collapse each spectral window to one channel, clean with auto-multithresh to 2 x RMS, smooth to 150 pc and regrid to the Nyquist-sampled CO images  
  > "We also collapse each spectral window into a single channel in order to speed up the continuum imaging process." (2.2 ALMA continuum); "After imaging, we smooth the dust continuum map to the resolution of 150 pc and regrid the map to the nyquist-sampled CO images." (2.2 ALMA continuum)
   - software: PHANGS-ALMA pipeline, auto-multithresh
   - parameter: Clean threshold 2 x RMS, RMS ~0.18 mJy/beam  
  > "clean the continuum data down to threshold of 2 $\times$ RMS (RMS of $\sim$ 0.18 mJy/beam)" (2.2 ALMA continuum)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive stellar mass surface density from Spitzer images (kpc scale)**: Background subtract Spitzer 3.6 and 4.5 um images, reproject to the CO 150 pc grid, compute stellar mass per pixel with the Eskew et al. equation, divide by pixel area, regrid to the 1 kpc CO map  
  > "We estimate the background level of each image by calculating the mean of an aperture drawn outside the galaxy and perform background subtraction." (2.3 Spitzer Data); "At the final step, we regrid our calculated stellar surface density map to the grid of 1 kpc resolution nyquist sampled CO $J$=1-0 moment 0 map." (2.3 Spitzer Data)
   - assumption: Stellar mass from F3.6 and F4.5 using the Eskew et al. 2012 relation with luminosity distance D  
  > "We then calculate the stellar mass for each pixel with the equation (cite: eskew2012)" (2.3 Spitzer Data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit non-LTE RADEX models to the five line intensities per pixel**: Per-pixel one-component RADEX grid modeling with all five CO and 13CO lines, using adapted Teng et al. code; Bayesian likelihood over a 5D grid; median adopted for each parameter except X12/13 where the 1DMax is used  
  > "to perform non-LTE radiative transfer modeling for each pixel with all five CO and $^{13}$CO lines detected at 150 pc." (3.1 General Modeling Procedure); "For all the parameters except for $X_{12/13}$, we use the median as the solution." (3.1 General Modeling Procedure)
   - software: RADEX, multiline-bayesian-modeling code (Teng et al. 2022)
   - parameter: Grid: log n 2-5.1 (step 0.2), log Tkin 1-2.4 (step 0.1), log NCO x 15 km/s / dv 16-21 (step 0.2)  
  > "log ($n$) ($\mathrm{cm^{-3}}$) | 2 – 5.1 | 0.2" (Table 2); "log ($T_{\mathrm{kin}}$) (K) | 1 – 2.4 | 0.1" (Table 2); "log ($N_{\mathrm{CO}} \times \frac{15 \mathrm{km s^{-1}}}{\Delta v}$) (cm$^{-2}$) | 16 – 21 | 0.2" (Table 2)
   - parameter: Grid: X12/13 10-400 (step 10), beam filling factor 0.05-1 (step 0.05), [CO]/[H2] fixed at 3e-4  
  > "$X_{12/13}$ | 10 – 400 | 10" (Table 2); "$\Phi_{\mathrm{bf}}$ | 0.05 – 1 | 0.05" (Table 2)
   - parameter: Fiducial NCO per 15 km/s, rescaled to real NCO with Delta v = 2.35 sigma_v from the CO 1-0 velocity dispersion map; modeled intensity rescaled by the ratio of measured linewidth to 15 km/s  
  > "Later we will rescale this value to the real CO column density based on the measured $\Delta v$ in the CO $J$=1-0 velocity dispersion map ($\Delta v = 2.35 \sigma_v$)." (3.1 General Modeling Procedure); "we need to rescale modeled intensity by multiplying the ratio of measured linewidth to the fixed linewidth of 15 km s$^{-1}$ for each pixel." (Appendix Bayesian Analyses in Our RADEX Modeling)
   - assumption: Homogeneous medium, escape probability formalism, one component  
  > "which assumes a homogeneous medium and uses radiative transfer equations based on the escape probability formalism" (3.1 General Modeling Procedure)
   - assumption: Same beam filling factor for all five lines  
  > "In the modeling, we assume the same $\Phi_{\mathrm{bf}}$ for all 5 lines." (3.1 General Modeling Procedure)
   - assumption: [CO]/[H2] abundance ratio x_CO = 3e-4  
  > "We also assume the $[\mathrm{CO}]$/$[\mathrm{H}_2]$ abundance ratio ($x_{\mathrm{co}}$) of 3$\times 10^{-4}$." (3.1 General Modeling Procedure)
   - fitting: Grid-based Bayesian likelihood: chi2 against the five integrated intensities, posterior P = exp(-chi2/2)/Q over the 5D grid, marginalized 1D PDFs; no MCMC sampler; priors not stated beyond uniform grid sampling  
  > "For each pixel, the code calculates the $\chi^2$ by comparing the modeled line intensities with the measured line intensities." (Appendix Bayesian Analyses in Our RADEX Modeling); "We can also calculate the marginalized 1D probability distribution for each individual modeled parameter by integrating the 5D $P(\vec{\theta}|\vec{I}_{\mathrm{obs}})$ over the rest of parameter space." (Appendix Bayesian Analyses in Our RADEX Modeling)
   - validation: Median of the 1D PDF compared with the 1DMax value for an example pixel; excitation temperatures compared to kinetic temperature for LTE test  
  > "For most quantities, the median of the 1D probability distribution corresponds well with the ‘1DMax’ value of the distribution, which suggests that our modeling recovers the most probable solution." (Appendix Bayesian Analyses in Our RADEX Modeling)
6. **Derive the alpha_CO posterior per pixel and select reliable pixels**: alpha_CO = 1.36 m_H2 NCO Phi_bf / (x_CO I_CO(1-0)); posterior from summing 5D probabilities for each alpha_CO, divided by the alpha_CO prior probability in the sampling space; median with 16th and 84th percentiles adopted  
  > "For the rest of the paper, we choose the median value of the posterior as our derived $\alpha_{\mathrm{CO}}$, and 16$^{\mathrm{th}}$ and 84$^{\mathrm{th}}$ percentile as the $\pm 1\sigma$ values." (3.2 Modeling of the CO-to-H2 conversion factor); "To get the unbiased PDF, we calculate the normalized ratio of our biased $\alpha_{\mathrm{CO}}$ probability to the $\alpha_{\mathrm{CO}}$ prior probability in our sampling space" (Appendix Modeling of the CO-to-H2 conversion factor)
   - software: multiline-bayesian-modeling code (Teng et al. 2022)
   - parameter: Exclude pixels with median alpha_CO below 0.1, with chi2 greater than 10, with 1dMax values at the edge of the grid (X12/13 <= 30, log n >= 4.9, log NCO(15 km/s) <= 16.1, log Tkin < 1.1) and with alpha_CO pos1sig/neg1sig < 16 (uncertainty within a factor of 4)  
  > "Therefore, we exclude the pixels with median $\alpha_{\mathrm{CO}}$ value below 0.1." (Appendix Modeling of the CO-to-H2 conversion factor); "We also exclude pixels with $\chi^2$ value greater than 10." (Appendix Modeling of the CO-to-H2 conversion factor)
   - assumption: Helium correction factor 1.36; x_CO = 3e-4 (alpha_CO scales as 3e-4 / x_CO)  
  > "This equation includes the correction coefficient of 1.36 for the contribution of helium." (3.2 Modeling of the CO-to-H2 conversion factor); "Note that our derived $\alpha_{\mathrm{CO}}$ is dependent on our assumed $x_{\mathrm{CO}}$ value." (3.2 Modeling of the CO-to-H2 conversion factor)
   - fitting: Posterior from the grid; no sampler  
  > "We calculate the $\alpha_{\mathrm{CO}}$ 1D distribution by summing up all the probabilities of parameters in 5D space that yield a given $\alpha_{\mathrm{CO}}$ value" (Appendix Modeling of the CO-to-H2 conversion factor)
   - validation: Pixel selection by marginalized-distribution inspection; 508 pixels kept  
  > "After our selection procedure, we have 508 pixels with good RADEX model constraints." (3.2 Modeling of the CO-to-H2 conversion factor)
7. **Fit empirical relations between alpha_CO and observables**: Power-law fits of alpha_CO versus CO 1-0 intensity, CO 1-0 optical depth, 13CO/CO 1-0 ratio (alone and with X12/13), velocity dispersion sigma_v (free slope and fixed -0.5), and 13CO/CO 2-1 ratio for S/N>10; correlation of alpha_CO with line ratios and Tkin  
  > "Fig. [8](#fig:alphaCO_Ico) shows a significant anti-correlation between $\alpha_{\mathrm{CO}}$ and $I_{\text{CO 1-0}}$." (5.1 Dependence on CO J=1-0 intensity); "We fit the anti-correlation with a power-law function, which is" (5.3 Dependence on GMC velocity dispersion)
   - parameter: 13CO/CO 2-1 relation fitted only for pixels with S/N > 10  
  > "We perform the same power-law fit to the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 2{-}1}}$ relation for pixels with S/N$>10$" (Appendix alpha_CO versus 13CO/CO J=2-1 ratio)
   - assumption: Theoretical slope of -0.5 for alpha_CO vs sigma_v under the LVG approximation for two-level optically thick systems  
  > "This power-law slope is derived from theoretical predictions under the LVG approximation for two-level optically thick systems" (5.3 Dependence on GMC velocity dispersion)
   - fitting: Power-law fits in log-log; fitting algorithm not stated  
  > "The value in the brackets indicates the 1-$\sigma$ error for the fitted parameter." (5.1 Dependence on CO J=1-0 intensity)
   - validation: Compared with simulation predictions (Narayanan et al. 2012, Gong et al. 2020, Hu et al. 2022) and with Teng et al. 2023, 2024  
  > "We can see that our power-law fit has almost the same slope as that predicted (slope of -0.32) in (cite: narayanan2012)." (5.1 Dependence on CO J=1-0 intensity)
8. **Check the assumed x_CO with a dust-based gas-to-dust ratio**: Compute dust mass and surface density from the 350 GHz (880 um) continuum with an assumed dust temperature and opacity, compare with modeled molecular gas surface density to get the gas-to-dust ratio  
  > "From the dust continuum map, we calculate the dust mass as (cite: wilson_luminous_2008)" (6.1 Constraining the xCO abundance ratio with the dust mass); "We can see that a high $x_{\mathrm{CO}}$ value is favored in order to get a reasonable gas-to-dust ratio (GDR) below 200." (6.1 Constraining the xCO abundance ratio with the dust mass)
   - parameter: kappa = 0.9 g^-1 cm^2; T_dust from Klaas et al. 2010 per subregion (about 20 K)  
  > "We chose 0.9 g$^{-1}$ cm$^{2}$ as the fiducial value for $\kappa$ (cite: wilson_luminous_2008)" (6.1 Constraining the xCO abundance ratio with the dust mass); "We adopt the dust temperature from (cite: klaas2010) for pixels in each defined subregion" (6.1 Constraining the xCO abundance ratio with the dust mass)
   - assumption: Dense GMCs expected to have GDR of 50-100 rather than 200; subregion A1a assumed to have the galaxy-integrated dust temperature  
  > "we would expect them to have GDR values closer to dense gas values of 50 – 100 instead of more diffuse medium values of 200" (6.1 Constraining the xCO abundance ratio with the dust mass); "For subregion A1a which does not have a temperature measurement, we assume the temperature to be the same as the overall dust temperature derived from the integrated fluxes of the entire galaxy" (6.1 Constraining the xCO abundance ratio with the dust mass)
   - fitting: _not stated_
   - validation: Higher dust temperature or opacity would give higher GDR at fixed x_CO, so they do not reduce the preferred x_CO  
  > "Therefore, increasing dust temperature and dust opacity does not help with reducing $x_{\mathrm{CO}}$ value" (6.1 Constraining the xCO abundance ratio with the dust mass)
9. **Reassess GMC dynamical states with modeled alpha_CO**: Use modeled alpha_CO to compute GMC surface density and virial parameter, compare with a constant Milky Way alpha_CO  
  > "With our modeled $\alpha_{\mathrm{CO}}$, we can put a more accurate constraint on GMC dynamical states in the Antennae." (6.2 GMC dynamical states in the Antennae)
   - assumption: x_CO = 3e-4 gives alpha_CO close to the U/LIRG value of 1.1  
  > "With $x_{\mathrm{CO}}$ = $3 \times 10^{-4}$, most of our modeled $\alpha_{\mathrm{CO}}$ are close to U/LIRG values of 1.1" (6.2 GMC dynamical states in the Antennae)
   - fitting: _not stated_
   - validation: Compared with merger simulation predictions of He et al. 2023  
  > "which is consistent with the simulation prediction from (cite: he2023)" (6.2 GMC dynamical states in the Antennae)
10. **Model alpha_CO at 1 kpc and compare with GMC scale**: Repeat the RADEX procedure on 1 kpc cubes and moment maps with beam filling factor sampled in log space; compute the CO 1-0 luminosity-weighted average of 150 pc alpha_CO in each kpc pixel; compute GMC fraction f_GMC; test dependence on I_CO and total surface density  
  > "except that we sample the beam filling factor in log space ($\log \Phi_{\mathrm{bf}}$ from -3 to 0 with step of 0.1)" (7.1 Modeling setup); "$\alpha_{\mathrm{CO}}$ is calculated as the CO $J$=1-0 intensity averaged value of the smaller pixels that are associated with the regridded pixel" (7.2 alpha_CO comparison at GMC and kpc scales)
   - software: RADEX, multiline-bayesian-modeling code (Teng et al. 2022)
   - parameter: Extra exclusions at kpc scale: X12/13 1dmax <= 30, log Tkin 1dmax < 1.1 or > 2  
  > "specifically, pixels with $X_{\mathrm{12/13, 1dmax}} \leq 30$, $\log T_{\mathrm{kin, 1dmax}} < 1.1$ or $\log T_{\mathrm{kin, 1dmax}} > 2$." (7.1 Modeling setup)
   - assumption: RADEX assumes uniform spherical structure, more applicable to individual GMCs than to ensembles at kpc scale  
  > "RADEX modeling generally assumes a uniform spherical structure, which is more applicable to individual GMCs than an ensemble of GMCs at kpc-scale resolution." (7.2 alpha_CO comparison at GMC and kpc scales)
   - fitting: Same grid Bayesian procedure as step 5  
  > "In modeling $\alpha_{\mathrm{CO}}$ at kpc scales, we generally follow the same procedure as in Section [3.1](#subsec:RADEX_general)" (7.1 Modeling setup)
   - validation: Pearson correlation of the kpc/GMC alpha_CO ratio with f_GMC  
  > "find a strong correlation between these two quantities with the coefficient of 0.62." (7.2 alpha_CO comparison at GMC and kpc scales)

## Software

- **CASA** : Calibration pipeline for raw visibilities (appropriate CASA pipeline version) and listed in Software section  
  > "We calibrate the raw visibility data with the observatory-supplied calibration scripts and the appropriate version of the CASA pipeline." (2.1 ALMA Spectral Lines)
- **PHANGS-ALMA imaging pipeline (modified)** : Extracting and imaging visibilities per line, continuum imaging, and generating masks and moment maps  
  > "using a modified version of the PHANGS–ALMA imaging pipeline (cite: leroy2021)" (2.1 ALMA Spectral Lines)
- **auto-multithresh** : Cleaning the continuum data  
  > "We then use the `auto-multithresh` algorithm to clean the continuum data down to threshold of 2 $\times$ RMS" (2.2 ALMA continuum)
- **RADEX** : Non-LTE radiative transfer modeling with escape probability formalism for line intensity grids  
  > "This code runs RADEX (cite: van_der_tak_computer_2007) modeling" (3.1 General Modeling Procedure)
- **multiline-bayesian-modeling (Teng et al. 2022 code, adapted)** : Per-pixel RADEX grid generation and Bayesian likelihood analysis  
  > "to perform non-LTE radiative transfer modeling for each pixel with all five CO and $^{13}$CO lines detected at 150 pc." (3.1 General Modeling Procedure)
- **astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pixels with good RADEX model constraints | 508 | not stated | pixels | 6 | After our selection procedure, we have 508 pixels with good RADEX model constraints. |
| alpha_CO versus CO 1-0 intensity (log alpha_CO = a + b log I) | intercept 0.77, slope -0.3 | +/-0.04 (intercept), +/-0.02 (slope) | alpha_CO in Msun (K km/s pc^2)^-1; I in K km/s | 7 | \log \alpha_{\mathrm{CO}} = 0.77 (\pm 0.04) - 0.3 (\pm 0.02) \log I_{\mathrm{CO 1-0}} |
| alpha_CO versus CO 1-0 optical depth (log alpha_CO = log tau + c) | c = -1.05 | +/-0.01 | dimensionless (log) | 7 | \log \alpha_{\mathrm{CO}} = \log \tau_{\mathrm{CO 1-0}} - 1.05 (\pm 0.01) |
| alpha_CO versus 13CO/CO 1-0 ratio (log alpha_CO = a log R + b) | slope 0.85, intercept 0.97 | +/-0.04, +/-0.04 | dimensionless (log) | 7 | \log \alpha_{\mathrm{CO}} = 0.85 (\pm 0.04) \log R_{\mathrm{^{13}CO/CO 1{-}0}} + 0.97 (\pm 0.04) |
| alpha_CO versus 13CO/CO 1-0 ratio and X12/13 (two-variable fit) | 0.7 + 1.03 log R + 0.21 log X12/13 | +/-0.06 (intercept), +/-0.05 (R), +/-0.03 (X12/13) | dimensionless (log) | 7 | 1.03 (\pm 0.05) \log R_{\mathrm{^{13}CO/CO 1-0}}; 0.21 (\pm 0.03) \log X_{12/13} + 0.7 (\pm 0.06) |
| alpha_CO versus velocity dispersion sigma_v (log alpha_CO = a + b log sigma_v) | intercept 0.7, slope -0.46 | +/-0.04 (intercept), +/-0.03 (slope) | alpha_CO in Msun (K km/s pc^2)^-1; sigma_v in km/s | 7 | \log \alpha_{\mathrm{CO}} = 0.7 (\pm 0.04) - 0.46 (\pm 0.03) \log \sigma_{v} |
| alpha_CO versus 13CO/CO 2-1 ratio for S/N>10 (log alpha_CO = a log R + b) | slope 0.58, intercept 0.65 | +/-0.04, +/-0.05 | dimensionless (log) | 7 | \log \alpha_{\mathrm{CO}} = 0.58 (\pm 0.04) \log R_{\mathrm{^{13}CO/CO 2{-}1}} + 0.65 (\pm 0.05) |
| Pearson coefficient of alpha_CO versus 13CO/CO 2-1 ratio for S/N>10 | 0.7 | not stated | dimensionless | 7 | with a Pearson correlation coefficient of 0.7 |
| Pearson coefficient of alpha_CO versus Tkin | -0.17 | not stated | dimensionless | 7 | only has a weak anti-correlation with $T_{\mathrm{kin}}$ (Pearson coefficient of -0.17) |
| Typical X12/13 abundance ratio | 100 - 300 (about 200) | not stated | dimensionless | 5 | We also find most regions have $X_{12/13}$ values between 100 – 300. |
| CO 2-1/1-0 line ratio | close to 1 | not stated | dimensionless | 2 | the CO $J$=2-1/1-0 ratio is generally uniform with values close to 1 across the entire molecular gas detected regions |
| Average CO 3-2/1-0 line ratio | ~0.4 - 0.7 | not stated | dimensionless | 2 | The average CO $J$=3-2/1-0 ratio is $\sim$ 0.4 – 0.7 |
| 13CO/CO 1-0 and 2-1 line ratios | ~0.1 | not stated | dimensionless | 2 | have values of $\sim$ 0.1, similar to the typical $R_{\mathrm{^{13}CO/CO 1{-}0}}$ ratio for normal spiral galaxies |
| Typical modeled alpha_CO at GMC scale (x_CO = 3e-4) | close to 1.1 | not stated | Msun (K km/s pc^2)^-1 | 6 | With $x_{\mathrm{CO}}$ = $3 \times 10^{-4}$, most of our modeled $\alpha_{\mathrm{CO}}$ are close to U/LIRG values of 1.1 |
| Gas-to-dust ratio implied with x_CO = 3e-4 | ~100 | not stated | dimensionless | 8 | gives us reasonable gas-to-dust ratios of $\sim$ 100 |
| Ratio of kpc-scale alpha_CO to the CO 1-0 intensity averaged 150 pc alpha_CO | about 60% | not stated | dimensionless | 10 | We can see that $\alpha_{\mathrm{CO}}$ values at kpc scale are about 60% of the CO $J$=1-0 intensity averaged $\alpha_{\mathrm{CO}}$ values at 150 pc scale. |
| Pearson coefficient between alpha_CO,1kpc / <alpha_CO,150pc> and f_GMC | 0.62 | not stated | dimensionless | 10 | find a strong correlation between these two quantities with the coefficient of 0.62. |
| Pearson coefficient of kpc-scale alpha_CO versus total surface density (Antennae alone; Antennae plus other U/LIRGs) | -0.11; -0.16 | not stated | dimensionless | 10 | We also do not see a significant correlation between these two quantities for the Antennae alone (Pearson coefficient of -0.11) or the Antennae and other U/LIRGs combined (Pearson coefficient of -0.16). |
| Ratio of Narayanan et al. 2012 predicted alpha_CO to the GMC-scale measurement | factor of 1.7 | not stated | dimensionless | 7 | are higher than our $\alpha_{\mathrm{CO}}$ measurement by a factor of 1.7 |

## Qualitative findings

- Most GMCs in the Antennae have alpha_CO about 4 times smaller than the Milky Way value (4.3)  
  > "we find that most GMCs in the Antennae have $\alpha_{\mathrm{CO}}$ values $\sim$4 times smaller than the commonly adopted Milky Way value (4.3)" (abstract)
- alpha_CO is mainly driven by CO optical depth rather than kinetic temperature  
  > "This suggests that $\alpha_{\mathrm{CO}}$ variations in starburst systems are mainly driven by optical depth variations rather than kinetic temperature variations" (Conclusions)
- GMCs in the Antennae are less gravitationally bound than in normal spiral galaxies  
  > "we find that GMCs in the Antennae are less gravitationally bound than in normal spiral galaxies, which is more consistent with what is predicted by merger simulations" (abstract)
- alpha_CO shows only a weak correlation with CO line ratios, so excitation conditions do not play a major role in its variation  
  > "The weak correlation between $\alpha_{\mathrm{CO}}$ and CO line ratios suggest that excitation conditions does not play a major role in the $\alpha_{\mathrm{CO}}$ variation within starburst mergers." (5.4 Dependence on CO line ratios)

## Claim tuples

- H: Is alpha_CO in the Antennae lower than the Milky Way value at GMC scale? | E: Per-pixel RADEX modeling of five CO and 13CO lines at 150 pc with fixed x_CO = 3e-4, checked against dust-based gas-to-dust ratios | R: Modeled alpha_CO is close to 1.1 Msun (K km/s pc^2)^-1 for most pixels, about 4 times below 4.3 | F: The Antennae GMCs have alpha_CO close to U/LIRG values, not the Milky Way value; absolute values depend on the assumed x_CO | **supported**
- H: Does alpha_CO depend on CO intensity, 13CO/CO ratio and velocity dispersion as theory predicts? | E: Power-law fits of modeled alpha_CO against I_CO(1-0), tau_CO, 13CO/CO 1-0 ratio and sigma_v | R: Slope -0.3 versus intensity, tight linear relation with optical depth, slope 0.85 versus 13CO/CO, slope -0.46 versus sigma_v | F: The 13CO/CO ratio and sigma_v can be used to infer alpha_CO in starburst regions; sigma_v slope is near the theoretical -0.5 | **supported**
- H: Is the low alpha_CO of starbursts driven by higher temperature or by optical depth and velocity dispersion? | E: Correlated modeled alpha_CO with Tkin, tau_CO, CO line ratios and sigma_v | R: Weak anti-correlation with Tkin (Pearson -0.17) and with CO line ratios; strong correlation with tau | F: Temperature is not the major factor in lowering alpha_CO; optical depth and velocity dispersion matter more | **supported**
- H: Are Antennae GMCs gravitationally bound when a modeled alpha_CO is used instead of the Milky Way value? | E: Compute GMC surface density and virial state with the modeled alpha_CO | R: Higher virial parameters, GMCs more turbulent | F: Most GMCs in the Antennae are out of virial equilibrium, consistent with merger simulations | **supported**
- H: Is kpc-scale alpha_CO equal to the luminosity-weighted GMC-scale alpha_CO? | E: RADEX modeling at 1 kpc compared with CO 1-0 intensity averaged 150 pc alpha_CO, with f_GMC correlation | R: kpc-scale alpha_CO is about 60% of the averaged GMC-scale value; ratio correlates with f_GMC (Pearson 0.62) | F: A diffuse gas component with lower alpha_CO may lower the kpc-scale value, though the paper notes it is debated whether diffuse gas has higher or lower alpha_CO | **partially**

## Reasoning

- Why this data: Diagnosing GMC physical states needs multiple CO and optically thin lines at about 100 pc resolution; the Antennae is one of the closest starburst mergers  
  > "it is necessary to observe multiple CO and other molecular lines (specifically optically thin lines) at GMC resolution ($\sim$ 100 pc) to perform comprehensive LVG modeling." (Introduction); "As one of the closest starburst mergers, NGC 4038/9 (the Antennae) is an ideal target for this study." (Introduction)
- Why this method: Effective width used because it is a more stable velocity dispersion estimate when clouds overlap along the line of sight  
  > "We adopt this alternative method because it gives a more stable estimate of velocity dispersion within clouds" (2.1 ALMA Spectral Lines)
- Alternative: Antennae might truly have a high gas-to-dust ratio; rejected because most regions have solar metallicity  
  > "An alternative explanation is that the Antennae might actually have a high GDR values." (6.1 Constraining the xCO abundance ratio with the dust mass); "Therefore, we would not expect the Antennae to have abnormally high GDR values." (6.1 Constraining the xCO abundance ratio with the dust mass)
- Alternative: Higher dust temperature or dust opacity considered and found not to reduce the preferred x_CO  
  > "However, if we assume the higher dust temperature, we would obtain an even higher GDR value given a fixed $x_{\mathrm{CO}}$ value." (6.1 Constraining the xCO abundance ratio with the dust mass)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO depends on the assumed x_CO, which the modeling cannot constrain  
  > "Note that our derived $\alpha_{\mathrm{CO}}$ is dependent on our assumed $x_{\mathrm{CO}}$ value." (3.2 Modeling of the CO-to-H2 conversion factor); "We note that our modeling does not have the ability to constrain $x_{\mathrm{CO}}$." (7.2 alpha_CO comparison at GMC and kpc scales)
- Limitation (authors): 13CO 1-0 assumed to share the CO beam filling factor, which may underestimate its excitation temperature  
  > "our models assume $^{13}$CO $J$=1-0 has the same beam filling factor as the CO $J$=1-0 emission." (4.2 Modeling results and their connection to the line ratios)
- Limitation (authors): Modeling restricted to regions with 13CO 1-0 and 2-1 detections, mostly nuclei and overlap region; cloud-scale average biased low  
  > "Finally, we note that our modeling results are limited to regions with $^{13}$CO $J$=1-0 and $J$=2-1 detections." (4.2 Modeling results and their connection to the line ratios); "In other words, our cloud-scale averaged $\alpha_{\mathrm{CO}}$ values are biased towards lower values." (7.2 alpha_CO comparison at GMC and kpc scales)
- Limitation (authors): Large uncertainty (factor of about 3) in modeled alpha_CO may smear out trends  
  > "the large uncertainty (factor of $\sim$3) in our modeled $\alpha_{\mathrm{CO}}$ values might act to smear out the trend." (7.3 alpha_CO dependence at kpc scale)
- Caveat (inferred, ours): Absolute alpha_CO is set by the fixed x_CO = 3e-4; the dust-based GDR check uses a literature T_dust (~20 K) and a single kappa, so it does not independently fix x_CO
- Caveat (inferred, ours): alpha_CO is derived from the same modeled NCO, beam filling factor and I_CO that appear in the relations tested, so correlations with I_CO, tau and 13CO/CO are partly built in
- Caveat (inferred, ours): The chi2 equation as printed has no square on the residual, so the exact likelihood used is ambiguous
- Caveat (inferred, ours): One-component homogeneous RADEX with shared beam filling factor for all lines and optically thin 13CO assumption is a strong simplification
- Caveat (inferred, ours): Sample is limited to 508 Nyquist pixels with 13CO detections in dense regions, so relations may not extend to diffuse gas
- Caveat (inferred, ours): Fit methodology and error treatment for the power laws are not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Modeled maps are available from the corresponding author on request, not in a public archive  
  > "The modeled maps of gas physical properties and CO-to-H$_2$ conversion factor are available from the corresponding author on request." (Data Availability)
- Code: RADEX grid generation and Bayesian analysis code released on Zenodo and GitHub  
  > "The code to generate RADEX modeling grids and perform Bayesian analysis on multiple CO and its isotopologue lines is available on both Zenodo" (Data Availability)
- Missing: Exact calibration and imaging parameters of the modified PHANGS-ALMA pipeline (versions, line-free channels, clean settings)
- Missing: Per-subregion dust temperatures and subregion definitions
- Missing: Measurement uncertainty definitions in the chi2 and power-law fitting algorithm
- Missing: Statement of data public status, PI and observing dates for the two projects
- Data volume (inferred): Likely several hundred GB to about 2 TB raw (12m, 7m and TP data for three bands over a mosaic of the Antennae; 5 lines plus continuum, 2 projects); processed cubes and moment maps much smaller
- Score (inferred): 3/5, ALMA project codes, RADEX grid ranges, selection cuts and numeric fit coefficients are given and the modeling code is public, but the imaging pipeline is a modified version with unstated parameters and the modeled maps are only available on request.
- Rediscovery candidate: no, Data public status is not stated by the paper and the line imaging recipe is incomplete, though the downstream modeling code and fit results are well specified.

## Links

- Method: Leroy et al. 2021 (cite: leroy2021) (PHANGS-ALMA imaging pipeline and masking scheme used and modified)
- Method: Teng et al. 2022 (cite: teng2022) (Source of the multi-line RADEX Bayesian modeling code and alpha_CO derivation)
- Method: Teng et al. 2023 (cite: teng2023) (Adaptation of the code and 15 km/s fiducial linewidth; alpha_CO versus 13CO/CO relation)
- Method: van der Tak et al. 2007 (cite: van_der_tak_computer_2007) (RADEX non-LTE radiative transfer code)
- Companion: He et al. 2023 (cite: he2023) (Merger simulation predictions of alpha_CO effects on GMC virial parameters)
- Companion: Teng et al. 2024 (cite: teng2024) (Calibrated alpha_CO versus sigma_v relation and theoretical slope)
- Companion: Sliwa et al. 2017 (cite: sliwa2017) (x_CO and X12/13 values for starburst mergers)
- Related: PHANGS-ALMA

## Checks

```json
{
 "quotes": 167,
 "quotes_ok": 167,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 127,
  "stated": 96,
  "rate": 0.756
 },
 "evidence_ok": true
}
```
