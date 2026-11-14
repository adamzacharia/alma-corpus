# Peculiar Dust Emission within the Orion Molecular Cloud

`2025ApJ...979..142N` | The Astrophysical Journal 2025 | first author: Nozari, Parisa | arXiv: 2411.12693 | DOI: 10.3847/1538-4357/ad93c7

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks, milky_way_ism
- Question: What is the origin of the flattened spectral energy distribution (SED) slope at wavelengths > 2 mm toward protostellar cores in the OMC 2/3 complex on core and envelope scales (~0.02 - 0.08 pc)?  
  > "The origin of this flattening is not yet known but it may be due to the intrinsic properties of the dust grains or contamination from other sources of emission." (Abstract); "By comparing multiwavelength data on $<0.1$ pc scales, we aim to identify how the SED slope is changing over the critical wavelength range between 1 and 3 mm using data that capture similar scales." (Introduction)
- Target **FIR2**: coordinates 05:35:24.305 -05.08.30.58  
  > "FIR2 | 05:35:24.305 | -05.08.30.58 | I | 58.4 | 403.1 | 0.96 | HOPS-68" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **FIR6B**: coordinates 05:35:23.289 -05.12.03.72  
  > "FIR6B | 05:35:23.289 | -05.12.03.72 | 0 | 152.7 | 790.3 | 0.11 | HOPS-60" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **MMS6**: coordinates 05:35:23.442 -05.01.30.44  
  > "MMS6 | 05:35:23.442 | -05.01.30.44 | 0 | 627.5 | 1510.3 | 0.097 | HOPS-87" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **MMS7**: coordinates 05:35:26.545 -05.03.55.28  
  > "MMS7 | 05:35:26.545 | -05.03.55.28 | I | 168.4 | 700.8 | 0.034 | HOPS-84" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **MMS9**: coordinates 05:35:25.993 -05.05.43.90  
  > "MMS9 | 05:35:25.993 | -05.05.43.90 | 0 | 10.4 | 106.4 | 0.24 | HOPS-78" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **NW167**: coordinates 05:35:29.720 -04.58.48.86  
  > "NW167 | 05:35:29.720 | -04.58.48.86 | 0 | 135.0 | 759.0 | 1.9 | HOPS-96" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00357.S
- bands: Band 4 (1.9 – 2.1 mm) and Band 5 (1.6 – 1.8 mm)  
  > "ALMA-ACA in Band 4 (1.9 – 2.1 mm) and Band 5 (1.6 – 1.8 mm)" (Abstract); "We observed the entire OMC 2/3 filament in Band 4 (137-153 GHz) and Band 5 (163-179 GHz) with the Atacama Large Millimeter/submillimeter Array (ALMA) ACA" (ALMA-ACA Data)
- frequencies and spectral setup: Band 4: 137-153 GHz (Band 4-Low: 138.9607 GHz, Band 4-High: 150.9918 GHz); Band 5: 163-179 GHz (Band 5-Low: 164.9749 GHz, Band 5-High: 177.007 GHz)  
  > "We observed the entire OMC 2/3 filament in Band 4 (137-153 GHz) and Band 5 (163-179 GHz) with the Atacama Large Millimeter/submillimeter Array (ALMA) ACA" (ALMA-ACA Data); "Band 4 - Low | 138.9607 | 2.16" (Table 2); "Band 5 - High | 177.007 | 1.69" (Table 2)
- continuum bandwidth: 3.6 GHz per baseband  
  > "NOEMA basebands are 4 GHz, ALMA basebands are 3.6 GHz." (Table 2)
- arrays: ACA  
  > "We observed the entire OMC 2/3 filament in Band 4 (137-153 GHz) and Band 5 (163-179 GHz) with the Atacama Large Millimeter/submillimeter Array (ALMA) ACA" (ALMA-ACA Data)
- configurations: _not stated_
- baselines: uv > 5 klambda cutoff applied  
  > "we generated images from the ACA visibilities with a uv range cutoff of uv $> 5~k\lambda$, which corresponds to spatial scales of $\lesssim$ 40 arcsec." (ALMA-ACA Data)
- angular resolution: Native (uv > 5 klambda): 13.7'' x 5.7'' to 9.7'' x 5.0''; Smoothed: 14.2'' x 8.9'' to 10.7'' x 7.6''  
  > "Band 4 - Low | 138.9607 | 2.16 | 13.7 | 5.7 | -87.7 | 1.1 | 14.2 | 8.9 | 86.7" (Table 2); "Band 5 - High | 177.007 | 1.69 | 9.7 | 5.0 | -81.4 | 1.7 | 10.7 | 7.6 | -79.1" (Table 2)
- max recoverable scale: <= 40 arcsec  
  > "we generated images from the ACA visibilities with a uv range cutoff of uv $> 5~k\lambda$, which corresponds to spatial scales of $\lesssim$ 40 arcsec." (ALMA-ACA Data)
- sensitivity: 1.1, 1.5, 1.2, 1.7 mJy beam^-1 (1.2x higher for MMS9 and NW167)  
  > "Band 4 - Low | 138.9607 | 2.16 | 13.7 | 5.7 | -87.7 | 1.1" (Table 2); "For the ALMA data, the rms values will be 1.2 times higher for MMS9 and NW167 because of their primary beam corrections." (Table 2)
- time on source: 9.53 hours total observing time  
  > "The region was divided into two mosaics with one centered on OMC 2 (area of 3.2 $\times$ 7.0 arcmin) and the other on OMC 3 (area 3.7 $\times$ 7.5 arcmin in Band 4 and 3.4 $\times$ 7.4 arcmin in Band 5) for a total observing time of 9.53 hours." (ALMA-ACA Data)
- observing dates: October 2017 to December 2017  
  > "We observed the entire OMC 2/3 filament in Band 4 (137-153 GHz) and Band 5 (163-179 GHz) with the Atacama Large Millimeter/submillimeter Array (ALMA) ACA from October 2017 to December 2017." (ALMA-ACA Data)
- pi or archival as stated: PI (observed by authors)  
  > "We observed the entire OMC 2/3 filament in Band 4 (137-153 GHz) and Band 5 (163-179 GHz) with the Atacama Large Millimeter/submillimeter Array (ALMA) ACA from October 2017 to December 2017." (ALMA-ACA Data)
- Other facility **IRAM NOEMA Interferometer**: 3 mm continuum observations (81-104 GHz, four basebands from 2.9 to 3.6 mm) in D-configuration of the six dense cores under project W18BG  
  > "We observed six dense cores within the OMC 2/3 filament with NOEMA in D-configuration with 10 antennas on 19 February 2019." (NOEMA Data); "The correlator was set to 81-104 GHz, with a total bandwidth of 16 GHz split between four basebands with 2 MHz resolution and 1828 channels per baseband." (NOEMA Data); "This work is based on observations carried out under project number W18BG with the IRAM NOEMA Interferometer." (Acknowledgements)
- External data: Protostellar classifications, ALMA 0.87 mm (338.5 GHz) disk fluxes and masses, and VLA 9 mm disk masses  
  > "Protostellar classifications (column 4) and disk masses (columns 5 and 6) are taken from (cite: Tobin2020), which presents ALMA 0.87 mm and VLA 9 mm observations." (Table 1); "$S_{disk}$ flux values are measured at 0.87 mm (338.5 GHz) and represent the sum of all disks in the targets from (cite: Tobin2020)." (Table 5) [from (cite: Tobin2020)]
- External data: Envelope masses from the Herschel Orion Protostellar Survey (HOPS)  
  > "The envelope masses (column 7) are taken from the Herschel Orion Protostellar Survey (cite: Furlan2016)." (Table 1) [from (cite: Furlan2016)]
- External data: Single-dish modified blackbody fits and dust opacity indices (beta-SD) from Herschel and IRAM 30 m (0.16 - 2 mm) data  
  > "the best-fit modified black body function obtained using single-dish data ($\beta$-SD; solid lines) from (cite: Sadavoy2016) using data from Herschel and IRAM (0.16 – 2 mm)." (Results); "$\beta$-SD is measured using a modified black-body fit to single-dish data only from (cite: Sadavoy2016)." (Table 4) [from (cite: Sadavoy2016)]
- External data: 90 GHz (3.3 mm) GBT MUSTANG continuum data  
  > "Moreover, we find excellent agreement between the NOEMA data and the 90 GHz (3.3 mm) data obtained from MUSTANG presented by (cite: Schnee2014)." (Spectral Line Contamination) [from (cite: Schnee2014)]
- External data: Estimated free-free emission fractions at 32.9 GHz and spectral indices between 32.9, 246.2, and 333 GHz for FIR2 and MMS9  
  > "Table [\[FF\]](#FF) displays their estimated free-free emission fractions at 32.9 GHz based on the analysis of (cite: Bouvier2021)." (Free-Free Emission) [from (cite: Bouvier2021)]

## Processing

### Calibration

- pipeline or manual: standard procedures from NAASC  
  > "The Band 4 and Band 5 datasets were calibrated through standard procedures from the North American ALMA Science Center (NAASC)." (ALMA-ACA Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627  
  > "The flux calibrator was J0522-3627, and the phase calibrator was J0541-0211 for the Band 4 data and J0542-0913 for the Band 5 data." (ALMA-ACA Data)
- flux scale uncertainty: 10%  
  > "Errors are from the fit alone and do not include calibration uncertainties, which we estimate to be 10%." (Source Extraction); "we further used a Monte Carlo approach to better determine the power-law slope error from the ALMA Band 4 and Band 5 data, which each have estimated flux calibration uncertainties of 10%." (SED Fitting)
- self calibration: Three rounds of phase-only self-calibration with solution intervals of full scan, 30s, and 15s  
  > "We applied three rounds of phase only self-calibration with successively smaller solution intervals starting from the full scan to 30s and then 15s." (ALMA-ACA Data)

### Imaging

- task: tclean  
  > "We employed the `tclean` algorithm in the CASA software (cite: McMullin2007), utilizing the Hogbom deconvolver." (ALMA-ACA Data)
- deconvolver: Hogbom  
  > "We employed the `tclean` algorithm in the CASA software (cite: McMullin2007), utilizing the Hogbom deconvolver." (ALMA-ACA Data)
- weighting robust: Briggs weighting, robust = 0.5  
  > "For all cleaning rounds, we used Briggs weighting with a robust parameter of 0.5 to optimize both sensitivity and resolution (cite: Briggs1995; Briggs1999)." (ALMA-ACA Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-contaminated channels inspected and flagged prior to cleaning  
  > "Prior to cleaning, the ALMA data were inspected to identify any channels that could be contaminated by line emission and such channels were flagged." (ALMA-ACA Data)
- line free channels: _not stated_
- primary beam correction: applied (rms 1.2x higher for MMS9 and NW167 due to primary beam corrections)  
  > "For the ALMA data, the rms values will be 1.2 times higher for MMS9 and NW167 because of their primary beam corrections." (Table 2)
- array combination: _not stated_
- smoothing: ALMA and NOEMA data smoothed by the synthesized beam of the other (LSB-O with Band 4-Low, LSB-I with Band 4-High, USB-I with Band 5-Low, USB-O with Band 5-High)  
  > "Final resolution after smoothing the NOEMA and ALMA data using the beam of the other data. We paired the ALMA and NOEMA data as follows: LSB-O with Band 4-Low, LSB-I with Band 4-High, USB-I with Band 5-Low, and USB-O with Band 5-High." (Table 2); "For simplicity, we smoothed the ALMA and NOEMA data by the synthesized beam of the other, matching the highest to lowest frequencies for each pair (e.g., LSB-O with Band 4-Low, LSB-I with Band 4-High, etc.)." (Source Extraction)
- final beam: Native (uv > 5 klambda): Band 4-Low 13.7'' x 5.7'' (PA -87.7 deg), Band 4-High 12.2'' x 5.7'' (PA -87.9 deg), Band 5-Low 10.8'' x 5.4'' (PA -80.8 deg), Band 5-High 9.7'' x 5.0'' (PA -81.4 deg); Smoothed: Band 4-Low 14.2'' x 8.9'' (PA 86.7 deg), Band 4-High 13.2'' x 8.4'' (PA 86.2 deg), Band 5-Low 11.5'' x 7.9'' (PA -79.4 deg), Band 5-High 10.7'' x 7.6'' (PA -79.1 deg)  
  > "Band 4 - Low | 138.9607 | 2.16 | 13.7 | 5.7 | -87.7 | 1.1 | 14.2 | 8.9 | 86.7" (Table 2); "Band 4 - High | 150.9918 | 1.99 | 12.2 | 5.7 | -87.9 | 1.5 | 13.2 | 8.4 | 86.2" (Table 2); "Band 5 - Low | 164.9749 | 1.82 | 10.8 | 5.4 | -80.8 | 1.2 | 11.5 | 7.9 | -79.4" (Table 2)
- final rms: Band 4-Low: 1.1 mJy beam^-1, Band 4-High: 1.5 mJy beam^-1, Band 5-Low: 1.2 mJy beam^-1, Band 5-High: 1.7 mJy beam^-1  
  > "Band 4 - Low | 138.9607 | 2.16 | 13.7 | 5.7 | -87.7 | 1.1" (Table 2); "Band 5 - High | 177.007 | 1.69 | 9.7 | 5.0 | -81.4 | 1.7" (Table 2)

### Inherited from earlier work

- Iterative phase-only self-calibration approach  
  > "We applied an iterative approach for phase-only self-calibration, similar to the method described by (cite: Ginsburg2018)." (ALMA-ACA Data) [from (cite: Ginsburg2018)]

### Not stated but needed to reproduce (our reading)

- CASA software version used for calibration, tclean, and imfit
- Cell size (pixel scale), image size, and cleaning thresholds/stopping criteria for the ALMA-ACA mosaics
- Specific channel ranges flagged for spectral line contamination in ALMA Band 4 and Band 5
- Number of MCMC steps and burn-in length for the emcee power-law fitting
- Adopted distance to OMC 2/3 used to convert angular scales to physical scales (0.02 - 0.08 pc)

## Analysis recipe

1. **Match spatial scales and angular resolution between ALMA-ACA and NOEMA continuum images**: Image ALMA-ACA sidebands with a uv > 5 klambda cutoff to match the minimum baseline of NOEMA, then smooth each paired ALMA and NOEMA image by the synthesized beam of the other.  
  > "To ensure a consistent comparison between the ALMA and NOEMA data, we generated images from the ACA visibilities with a uv range cutoff of uv $> 5~k\lambda$, which corresponds to spatial scales of $\lesssim$ 40 arcsec." (ALMA-ACA Data); "For simplicity, we smoothed the ALMA and NOEMA data by the synthesized beam of the other, matching the highest to lowest frequencies for each pair (e.g., LSB-O with Band 4-Low, LSB-I with Band 4-High, etc.)." (Source Extraction)
   - software: CASA, tclean, GILDAS
   - parameter: uv > 5 klambda  
  > "we generated images from the ACA visibilities with a uv range cutoff of uv $> 5~k\lambda$, which corresponds to spatial scales of $\lesssim$ 40 arcsec." (ALMA-ACA Data)
   - parameter: Baseband pairings: LSB-O with Band 4-Low, LSB-I with Band 4-High, USB-I with Band 5-Low, USB-O with Band 5-High  
  > "We paired the ALMA and NOEMA data as follows: LSB-O with Band 4-Low, LSB-I with Band 4-High, USB-I with Band 5-Low, and USB-O with Band 5-High." (Table 2)
   - fitting: _not stated_
   - validation: Compare smoothed NOEMA data (at 10.8'' resolution) with 90 GHz MUSTANG GBT data, finding agreement within 30%.  
  > "For consistency, we smoothed the NOEMA data to a common resolution of 10.8$''$ to match the resolution of the GBT data (cite: Schnee2014). We find that the GBT measurements are within $30\%$ of the SED outlined by the 10.8$''$-smoothed NOEMA data." (Spectral Line Contamination)
2. **Extract integrated source fluxes and sizes across all 8 frequency bands**: Fit 2D Gaussian functions plus a free constant background level in the image plane using CASA imfit.  
  > "The integrated flux of each source is extracted using the `imfit` task in CASA. This task fits the source emission with two-dimensional Gaussian functions in the image plane" (Source Extraction); "In both cases, we fitted both a Gaussian and a background level, with the background being treated as a free parameter (`dooff` = True) since there was still extended emission around the sources." (Source Extraction)
   - software: CASA
   - parameter: NOEMA box size: 30x30 pixels; ALMA box size: about 50x50 pixels; dooff = True  
  > "For the NOEMA data, we used a $30\times30$ pixel box centered in the individual pointing map for all of the sources. For the ALMA data, we generated boxes with a box size of about $50\times50$ pixels centered on each source in the mosaics." (Source Extraction); "with the background being treated as a free parameter (`dooff` = True) since there was still extended emission around the sources." (Source Extraction)
   - assumption: 2D Gaussian source morphology with constant local background  
  > "In both cases, we fitted both a Gaussian and a background level, with the background being treated as a free parameter (`dooff` = True)" (Source Extraction)
   - fitting: Image-plane 2D Gaussian + background fitting via CASA imfit  
  > "The integrated flux of each source is extracted using the `imfit` task in CASA." (Source Extraction)
   - validation: _not stated_
3. **Fit SED spectral index (alpha) and dust opacity index (beta) for NOEMA and ALMA separately**: Fit simple power-law models S_nu = A * nu^alpha to the NOEMA (4 bands) and ALMA-ACA (4 bands) fluxes separately using MCMC (emcee), and perform a 5000-sample Monte Carlo simulation to include 10% correlated Band 4 and Band 5 flux calibration uncertainties.  
  > "To optimize the fitting process, we utilized the `emcee` code (cite: emcee2013) with an assumed, simple power-law model of $S_\nu = A\nu^{\alpha}$. To test how the slope changes for each source, we fitted power-law functions to the NOEMA data and ALMA-ACA data separately." (SED Fitting); "We used a random selector to generate two sets of 5000 samples from a Gaussian distribution with mean 1 and standard deviation of 0.1 to represent the 10% flux calibration uncertainty in each band." (SED Fitting)
   - software: emcee
   - parameter: 32 walkers, uniform prior -5.0 < alpha < 5.0, 5000 Monte Carlo samples with Gaussian(mean=1, std=0.1) for ALMA calibration error  
  > "When running `emcee`, we employed uniform priors on the parameter $\alpha$, with bounds set as $-5.0 < \alpha < 5.0$. We also performed `emcee` with 32 walkers" (SED Fitting); "We used a random selector to generate two sets of 5000 samples from a Gaussian distribution with mean 1 and standard deviation of 0.1 to represent the 10% flux calibration uncertainty in each band." (SED Fitting)
   - assumption: Rayleigh-Jeans approximation: alpha = 2 + beta, with power-law dust opacity kappa_nu propto nu^beta  
  > "where the dust opacity term has been replaced with a power law given by $\kappa_\nu \propto \nu^\beta$." (SED Fitting); "where $\alpha = 2+ \beta$ is called the spectral index." (SED Fitting)
   - fitting: MCMC via emcee with 32 walkers and uniform priors (-5.0 < alpha < 5.0), combined with 5000-realization Monte Carlo propagation of 10% flux calibration uncertainty  
  > "When running `emcee`, we employed uniform priors on the parameter $\alpha$, with bounds set as $-5.0 < \alpha < 5.0$. We also performed `emcee` with 32 walkers" (SED Fitting)
   - validation: Tested Rayleigh-Jeans assumption against full modified blackbody at T_d = 25 K and beta = 1, finding beta underestimated by ~15% (ALMA) and ~10% (NOEMA), which is smaller than the fit uncertainties.  
  > "To verify this assumption, we calculated $\alpha$ from Equation [\[MBB\]](#MBB) assuming a typical dust temperature of 25 K (cite: Sadavoy2016; Friesen2017) and fixed $\beta = 1$ to represent the typical values in OMC 2/3." (Results); "The inferred $\beta$ values derived from the $\beta = \alpha - 2$ assumption compared to the more accurate modified blackbody fit were approximately 15% and 10% underestimated for the ALMA and NOEMA data, respectively." (Results)
4. **Estimate fraction of NOEMA and ALMA continuum flux arising from embedded protostellar disks**: Sum 338.5 GHz (0.87 mm) disk fluxes within the NOEMA beam from Tobin et al. (2020) and extrapolate to NOEMA and ALMA frequencies using a power law S_nu propto nu^alpha with alpha = 2 and alpha = 3.  
  > "For simplicity, we extrapolated ALMA observations at 340 GHz (0.87 mm) with 40 au resolution from (cite: Tobin2020) using a power-law relationship, $S_{\nu} \sim \nu^\alpha$ to infer the contribution of disk emission." (Disk Contamination); "To quantify the contribution of disk emission to the total flux for each protostellar core, we summed the contributions of all disks within the beam area of the NOEMA observations for each source." (Disk Contamination)
   - parameter: Reference frequency = 338.5 GHz; assumed disk spectral indices alpha = 2 (beta = 0) and alpha = 3 (beta = 1)  
  > "where $S_{disk,e}$ is the extrapolated disk flux at an extrapolated frequency of $\nu_e$, $S_{disk}$ is the disk flux from (cite: Tobin2020) observed at 338.5 GHz" (Disk Contamination); "We adopted two different spectral indices, $\alpha = 2$ and $\alpha = 3$, corresponding to values of $\beta =$ 0 or 1, which are representative of typical values in disks (cite: Tychoniec2020; miotello2022)." (Disk Contamination)
   - assumption: 340 GHz high-resolution (40 au) ALMA observations filter out core and envelope emission and trace only disk emission, which follows a constant power law with alpha between 2 and 3.  
  > "Although the 340 GHz ALMA observations from (cite: Tobin2020) filtered out dust emission in the core and envelope, our focus is to estimate contamination coming from the disk alone." (Disk Contamination)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data imaging with tclean and 2D Gaussian source flux extraction with imfit  
  > "We employed the `tclean` algorithm in the CASA software (cite: McMullin2007), utilizing the Hogbom deconvolver." (ALMA-ACA Data); "The integrated flux of each source is extracted using the `imfit` task in CASA." (Source Extraction)
- **tclean** : Deconvolving and imaging ALMA-ACA visibilities  
  > "We employed the `tclean` algorithm in the CASA software (cite: McMullin2007), utilizing the Hogbom deconvolver." (ALMA-ACA Data)
- **GILDAS** : NOEMA data imaging using the MAPPING method  
  > "We employed the `MAPPING` method in GILDAS (cite: GILDAS) for data imaging with a map size of 128 by 128 pixels, corresponding to 92.16$''$ by 92.16$''$, and 0.72$''$ pixels." (NOEMA Data)
- **emcee** : MCMC power-law fitting of the SED spectral index alpha  
  > "To optimize the fitting process, we utilized the `emcee` code (cite: emcee2013) with an assumed, simple power-law model of $S_\nu = A\nu^{\alpha}$." (SED Fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FIR2 spectral index alpha-NOEMA | 1.84 | 0.56 | dimensionless | 3 | FIR2 / 1.84 $\pm$ 0.56 / 3.95 $\pm$ 0.52 / -0.16 $\pm$ 0.56 / 1.95 $\pm$ 0.52 / 1.3$\pm$0.1 |
| FIR2 spectral index alpha-ALMA | 3.95 | 0.52 | dimensionless | 3 | FIR2 / 1.84 $\pm$ 0.56 / 3.95 $\pm$ 0.52 / -0.16 $\pm$ 0.56 / 1.95 $\pm$ 0.52 / 1.3$\pm$0.1 |
| FIR2 dust opacity index beta-NOEMA | -0.16 | 0.56 | dimensionless | 3 | FIR2 / 1.84 $\pm$ 0.56 / 3.95 $\pm$ 0.52 / -0.16 $\pm$ 0.56 / 1.95 $\pm$ 0.52 / 1.3$\pm$0.1 |
| FIR2 dust opacity index beta-ALMA | 1.95 | 0.52 | dimensionless | 3 | FIR2 / 1.84 $\pm$ 0.56 / 3.95 $\pm$ 0.52 / -0.16 $\pm$ 0.56 / 1.95 $\pm$ 0.52 / 1.3$\pm$0.1 |
| FIR6B spectral index alpha-NOEMA | 2.51 | 0.55 | dimensionless | 3 | FIR6B / 2.51 $\pm$ 0.55 / 2.64 $\pm$ 0.29 / 0.51$\pm$ 0.55 / 0.64 $\pm$ 0.29 / 1.9$\pm$0.1 |
| FIR6B spectral index alpha-ALMA | 2.64 | 0.29 | dimensionless | 3 | FIR6B / 2.51 $\pm$ 0.55 / 2.64 $\pm$ 0.29 / 0.51$\pm$ 0.55 / 0.64 $\pm$ 0.29 / 1.9$\pm$0.1 |
| FIR6B dust opacity index beta-NOEMA | 0.51 | 0.55 | dimensionless | 3 | FIR6B / 2.51 $\pm$ 0.55 / 2.64 $\pm$ 0.29 / 0.51$\pm$ 0.55 / 0.64 $\pm$ 0.29 / 1.9$\pm$0.1 |
| FIR6B dust opacity index beta-ALMA | 0.64 | 0.29 | dimensionless | 3 | FIR6B / 2.51 $\pm$ 0.55 / 2.64 $\pm$ 0.29 / 0.51$\pm$ 0.55 / 0.64 $\pm$ 0.29 / 1.9$\pm$0.1 |
| MMS6 spectral index alpha-NOEMA | 3.45 | 0.30 | dimensionless | 3 | MMS6 / 3.45 $\pm$ 0.30 / 2.47 $\pm$ 0.17 / 1.45 $\pm$ 0.30 / 0.47 $\pm$ 0.17 / 1.3$\pm$0.1 |
| MMS6 spectral index alpha-ALMA | 2.47 | 0.17 | dimensionless | 3 | MMS6 / 3.45 $\pm$ 0.30 / 2.47 $\pm$ 0.17 / 1.45 $\pm$ 0.30 / 0.47 $\pm$ 0.17 / 1.3$\pm$0.1 |
| MMS6 dust opacity index beta-NOEMA | 1.45 | 0.30 | dimensionless | 3 | MMS6 / 3.45 $\pm$ 0.30 / 2.47 $\pm$ 0.17 / 1.45 $\pm$ 0.30 / 0.47 $\pm$ 0.17 / 1.3$\pm$0.1 |
| MMS6 dust opacity index beta-ALMA | 0.47 | 0.17 | dimensionless | 3 | MMS6 / 3.45 $\pm$ 0.30 / 2.47 $\pm$ 0.17 / 1.45 $\pm$ 0.30 / 0.47 $\pm$ 0.17 / 1.3$\pm$0.1 |
| MMS7 spectral index alpha-NOEMA | 2.74 | 0.39 | dimensionless | 3 | MMS7 / 2.74 $\pm$ 0.39 / 2.33 $\pm$ 0.42 / 0.74 $\pm$ 0.39 / 0.33 $\pm$ 0.42 / 1.7$\pm$0.1 |
| MMS7 spectral index alpha-ALMA | 2.33 | 0.42 | dimensionless | 3 | MMS7 / 2.74 $\pm$ 0.39 / 2.33 $\pm$ 0.42 / 0.74 $\pm$ 0.39 / 0.33 $\pm$ 0.42 / 1.7$\pm$0.1 |
| MMS7 dust opacity index beta-NOEMA | 0.74 | 0.39 | dimensionless | 3 | MMS7 / 2.74 $\pm$ 0.39 / 2.33 $\pm$ 0.42 / 0.74 $\pm$ 0.39 / 0.33 $\pm$ 0.42 / 1.7$\pm$0.1 |
| MMS7 dust opacity index beta-ALMA | 0.33 | 0.42 | dimensionless | 3 | MMS7 / 2.74 $\pm$ 0.39 / 2.33 $\pm$ 0.42 / 0.74 $\pm$ 0.39 / 0.33 $\pm$ 0.42 / 1.7$\pm$0.1 |
| MMS9 spectral index alpha-NOEMA | 3.24 | 0.49 | dimensionless | 3 | MMS9 / 3.24 $\pm$ 0.49 / 2.84 $\pm$ 0.38 / 1.24 $\pm$ 0.49 / 0.84 $\pm$ 0.38 / 2.1$\pm$0.1 |
| MMS9 spectral index alpha-ALMA | 2.84 | 0.38 | dimensionless | 3 | MMS9 / 3.24 $\pm$ 0.49 / 2.84 $\pm$ 0.38 / 1.24 $\pm$ 0.49 / 0.84 $\pm$ 0.38 / 2.1$\pm$0.1 |
| MMS9 dust opacity index beta-NOEMA | 1.24 | 0.49 | dimensionless | 3 | MMS9 / 3.24 $\pm$ 0.49 / 2.84 $\pm$ 0.38 / 1.24 $\pm$ 0.49 / 0.84 $\pm$ 0.38 / 2.1$\pm$0.1 |
| MMS9 dust opacity index beta-ALMA | 0.84 | 0.38 | dimensionless | 3 | MMS9 / 3.24 $\pm$ 0.49 / 2.84 $\pm$ 0.38 / 1.24 $\pm$ 0.49 / 0.84 $\pm$ 0.38 / 2.1$\pm$0.1 |
| NW167 spectral index alpha-NOEMA | 2.44 | 0.30 | dimensionless | 3 | NW167 / 2.44 $\pm$ 0.30 / 2.68 $\pm$ 0.23 / 0.44 $\pm$ 0.30 / 0.68 $\pm$ 0.23 / 1.8$\pm$0.1 |
| NW167 spectral index alpha-ALMA | 2.68 | 0.23 | dimensionless | 3 | NW167 / 2.44 $\pm$ 0.30 / 2.68 $\pm$ 0.23 / 0.44 $\pm$ 0.30 / 0.68 $\pm$ 0.23 / 1.8$\pm$0.1 |
| NW167 dust opacity index beta-NOEMA | 0.44 | 0.30 | dimensionless | 3 | NW167 / 2.44 $\pm$ 0.30 / 2.68 $\pm$ 0.23 / 0.44 $\pm$ 0.30 / 0.68 $\pm$ 0.23 / 1.8$\pm$0.1 |
| NW167 dust opacity index beta-ALMA | 0.68 | 0.23 | dimensionless | 3 | NW167 / 2.44 $\pm$ 0.30 / 2.68 $\pm$ 0.23 / 0.44 $\pm$ 0.30 / 0.68 $\pm$ 0.23 / 1.8$\pm$0.1 |
| Median dust opacity index beta-NOEMA across sample | 0.74 | not stated | dimensionless | 3 | The median $\beta$ indices are 0.74, 0.68, and 1.8 for the NOEMA, ALMA, and single-dish data, respectively |
| Median dust opacity index beta-ALMA across sample | 0.68 | not stated | dimensionless | 3 | The median $\beta$ indices are 0.74, 0.68, and 1.8 for the NOEMA, ALMA, and single-dish data, respectively |
| FIR2 integrated flux at 138.9607 GHz (ALMA Band 4-Low) | 75.2 | 7.8 | mJy | 2 | 138.9607 & $< 13.4^a$ & $< 11.1^a$ & ... & 75.2 $\pm$ 7.8 |
| FIR2 integrated flux at 177.007 GHz (ALMA Band 5-High) | 199 | 15 | mJy | 2 | 177.007 & 8.7 $\pm$ 1.3 & 2.9 $\pm$ 2.4 & 166 $\pm$ 14 & 199 $\pm$ 15 |
| MMS6 integrated flux at 138.9607 GHz (ALMA Band 4-Low) | 514 | 15 | mJy | 2 | 138.9607 & $< 13.8^a$ & $< 9.8^a$ & ... & 514 $\pm$ 15 |
| MMS6 integrated flux at 177.007 GHz (ALMA Band 5-High) | 945 | 31 | mJy | 2 | 177.007 & 4.2 $\pm$ 0.5 & 1.8 $\pm$ 1.1 & 163 $\pm$ 18 & 945 $\pm$ 31 |

## Qualitative findings

- All six cores show flattened dust opacity indices between 2.9 mm and 3.6 mm (beta approx -0.16 to 1.45), with five out of six cores (all except MMS6) having significantly flatter slopes than single-dish modified blackbody fits.  
  > "We confirm flattened opacity indices between 2.9 mm and 3.6 mm for the six cores with $\beta \approx -0.16 - 1.45$, which are notably lower than the $\beta$ values of $> 1.3$ measured for these sources on $0.08$ pc scales from single-dish data." (Abstract); "All sources except MMS6 give flatter SED slopes between 82.7 GHz and 102.3 GHz (2.9 – 3.7 mm) compared to modified blackbody fits using single dish data (from 0.16 – 2.0 mm)." (Conclusions)
- Four sources (FIR6B, MMS7, MMS9, NW167) show consistent SED slopes within 1 sigma between ALMA-ACA and NOEMA, whereas two sources (FIR2 and MMS6) have slopes that differ by ~2 sigma.  
  > "FIR6B, MMS7, MMS9, and NW167 all show SEDs where the ALMA and NOEMA slopes are in agreement, indicating that the two instruments are tracing the same continuum emission mechanism. By contrast, FIR2 and MMS6 have discrepant ($>2 \sigma$) slopes between the ALMA and NOEMA data, suggesting that they are tracing different types of emission." (Conclusions)

## Claim tuples

- H: Protostellar cores in OMC 2/3 exhibit flattened SED slopes at lambda > 2 mm (< 150 GHz) on core and envelope scales (~0.02 - 0.08 pc) compared to single-dish modified blackbody fits at shorter wavelengths. | E: Imaged four NOEMA basebands (82.7-102.3 GHz) and four ALMA-ACA sidebands (139.0-177.0 GHz) matched in spatial scale (uv > 5 klambda) and smoothed to matched beams, extracted fluxes with CASA imfit, and fitted power-law slopes using emcee. | R: NOEMA and ALMA median beta values are 0.74 and 0.68 respectively, compared to 1.8 for single-dish data; 5 of 6 sources have flatter NOEMA slopes than single-dish fits, and 4 sources have consistent slopes between ALMA and NOEMA. | F: Flattened SED profiles at frequencies < 150 GHz are confirmed on 0.02 - 0.08 pc scales. | **supported**
- H: Embedded protostellar disks with large dust grains can contaminate and flatten the continuum SED measured on core and envelope scales (0.02 - 0.08 pc). | E: Extrapolated 338.5 GHz (0.87 mm, 40 au resolution) ALMA disk fluxes from Tobin et al. (2020) to NOEMA and ALMA frequencies using power-law indices alpha = 2 and alpha = 3 and compared with measured core fluxes. | R: Disk emission could account for up to 70% (up to 100% for alpha=2, 29-43% for alpha=3) of the flux in FIR6B and MMS7, <= 40% in MMS9 and NW167, and only 5-23% in FIR2 and 20-25% in MMS6. | F: Disk contamination can explain the flattened slopes for some sources (notably FIR6B and MMS7) and is a non-negligible factor on core/envelope scales, but cannot explain all sources (especially FIR2 and MMS6). | **partially**
- H: Spectral line contamination, free-free emission, or Anomalous Microwave Emission (AME) are the primary causes of the flattened SED slopes at < 150 GHz across the sample. | E: Excluded line-contaminated channels before imaging, compared 10.8''-smoothed NOEMA fluxes to broadband 90 GHz GBT MUSTANG fluxes, compared 32.9 GHz free-free estimates to 82-177 GHz slopes, and checked for negative spectral indices expected from AME turnover. | R: Line-free NOEMA fluxes agree within 30% with GBT MUSTANG fluxes; no negative spectral index turnover (alpha < 0) is observed at 80-100 GHz; only FIR2 has alpha approx 2 at NOEMA frequencies but steepens to alpha approx 4 at ALMA frequencies. | F: Spectral line contamination, free-free emission, and AME are insufficient to explain the flattened SED slopes across the sample. | **refuted**

## Reasoning

- Why this data: NOEMA 3 mm and ALMA-ACA Band 4 and Band 5 observations were chosen to span the critical 1 to 3 mm wavelength transition on matched < 0.1 pc scales toward six bright, compact, isolated protostellar cores with known elevated 3 mm emission.  
  > "These cores all exhibited elevated 3 mm emission based on prior Herschel and GBT data (cite: Sadavoy2016; mason2020), and they are all bright, compact, and isolated, making them the best targets to map the SED slope by imaging the basebands separately" (Introduction); "By comparing multiwavelength data on $<0.1$ pc scales, we aim to identify how the SED slope is changing over the critical wavelength range between 1 and 3 mm using data that capture similar scales." (Introduction)
- Why this method: Applied a uv > 5 klambda cutoff and cross-beam smoothing so ALMA and NOEMA trace identical spatial scales, and fitted Rayleigh-Jeans power laws to slopes rather than full modified blackbodies or absolute fluxes because dust temperatures on 0.02 - 0.08 pc scales are unknown and slopes are more robust against calibration and filtering uncertainties.  
  > "The purpose of specifying the uv range was to enable the characterization of the SED slope for each target using data that trace the same spatial scales." (ALMA-ACA Data); "Hereafter, we focus on the slopes instead of the absolute flux values in our analysis as relative values (slopes) should be more robust against uncertainties from flux calibration, flux extraction, and spatial filtering." (Results); "We nevertheless prefer to use a power-law fit over a modified blackbody fit because the temperatures themselves are unknown at these scales." (Results)
- Alternative: Full modified blackbody SED fitting instead of Rayleigh-Jeans power-law fitting (rejected as primary method because core-scale dust temperatures are unknown, though tested at T_d = 25 K)  
  > "We nevertheless prefer to use a power-law fit over a modified blackbody fit because the temperatures themselves are unknown at these scales." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperatures on 0.02 - 0.08 pc scales are unknown, and using the Rayleigh-Jeans approximation (beta = alpha - 2) underestimates beta by ~15% (ALMA) and ~10% (NOEMA) relative to a 25 K modified blackbody.  
  > "The inferred $\beta$ values derived from the $\beta = \alpha - 2$ assumption compared to the more accurate modified blackbody fit were approximately 15% and 10% underestimated for the ALMA and NOEMA data, respectively." (Results)
- Limitation (authors): Flux calibration error at 177 GHz (ALMA Band 5-High) may be larger than 10% due to proximity to the 183 GHz atmospheric water line wing.  
  > "However, it should be noted that the calibration error at 177 GHz may be larger due to its proximity to the 183 GHz atmospheric water line wing, potentially affecting the accuracy of flux measurements at this frequency." (SED Fitting)
- Limitation (authors): Image-plane analysis cannot break the degeneracy between large dust grains in envelopes and contamination from unresolved embedded disks; visibility modeling of disk and envelope emission is required.  
  > "Therefore, modeling disk and envelope emission using visibilities over images would be necessary to break this degeneracy (cite: Miotello2014; Galametz2019; Cacciapuoti2023)." (Unusual Dust Properties)
- Limitation (authors): Differences in source extraction and map resolution limit direct comparison of absolute fluxes between the interferometric data and single-dish modified blackbody fits.  
  > "Nevertheless, we caution against over-interpreting the difference in flux between ALMA and the modified blackbody fit from the single-dish data as differences in source extraction and map resolution could also be a factor." (Results)
- Caveat (inferred, ours): Cross-smoothing ALMA and NOEMA images by each other's beams produces four different beam sizes across the eight frequency bands (from 14.2'' x 8.9'' at the lowest frequencies to 10.7'' x 7.6'' at the highest frequencies) rather than a single common resolution across all bands, which could introduce a frequency-dependent aperture/resolution bias into the fitted spectral slopes.
- Caveat (inferred, ours): Extrapolating 338.5 GHz disk fluxes to 83-177 GHz using fixed spectral indices (alpha = 2 or 3) ignores potential spectral curvature or optical depth transitions within the disks themselves.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Raw or calibrated NOEMA visibility data (project W18BG)
- Missing: Exact CASA pixel size, image dimensions, and cleaning stopping thresholds for the ALMA-ACA mosaics
- Missing: Exact spectral channel ranges flagged for line subtraction in NOEMA and ALMA-ACA
- Missing: Exact pixel coordinates of the 30x30 (NOEMA) and ~50x50 (ALMA) imfit bounding boxes for each target
- Data volume (inferred): tens of GB (9.53 hours of ALMA-ACA Band 4 and Band 5 mosaic visibilities plus 1.18 hours of NOEMA 10-antenna wideband visibilities)
- Score (inferred): 72/5, The ALMA project code, calibrators, self-calibration intervals, uv-cut, robust weighting, beam pairing, source extraction task (imfit with dooff=True), intermediate extracted fluxes (Table 3), and MCMC/MC fitting procedure are all clearly reported; however, NOEMA visibilities are less accessible, and exact ALMA imaging parameters (cell size, clean thresholds, line-free channel masks) are omitted.
- Rediscovery candidate: yes, The ALMA-ACA dataset (2017.1.00357.S) is public in the ALMA archive, the imaging and source extraction recipe is straightforward, and all intermediate fluxes and final ALMA spectral indices (alpha-ALMA and beta-ALMA) are tabulated separately from the NOEMA data, providing a clean numeric answer key.

## Links

- Method: (cite: Ginsburg2018) (Iterative phase-only self-calibration procedure adopted for the ALMA-ACA data)
- Method: (cite: emcee2013) (MCMC sampler used for fitting SED power-law slopes)
- Companion: (cite: Sadavoy2016) (Prior Herschel and IRAM 30 m study of OMC 2/3 providing the single-dish modified blackbody fits (beta-SD) and motivating target selection)
- Companion: (cite: mason2020) (Prior GBT 3 mm and 1 cm study of OMC 2/3 motivating target selection and providing the modified blackbody/AME framework)
- Related: Herschel Orion Protostellar Survey (HOPS)

## Checks

```json
{
 "quotes": 134,
 "quotes_ok": 134,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 11,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 30,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 66,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
