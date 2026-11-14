# ALMA Observations of Circumstellar Disks in the Upper Scorpius OB Association

`2016ApJ...827..142B` | The Astrophysical Journal 2016 | first author: Barenfeld, Scott A. | arXiv: 1605.05772 | DOI: 10.3847/0004-637X/827/2/142

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: How do disk dust masses (and CO emission) of low-mass stars in Upper Sco at 5-11 Myr compare with younger Taurus disks, and how do they depend on stellar mass?  
  > "We then compare the distribution of disk dust masses in Upper Sco to that in Taurus in order to quantify the evolution of dust mass in disks between an age of 1-2 Myr and 5-11 Myr." (Introduction)
- Target **106 disk-hosting G-M type stars in Upper Sco (2MASS-named)**: coordinates _not stated_; z/distance 145 pc  
  > "We adopt $d=145$ pc, which is the mean distance to the OB stars of Upper Sco (cite: deZeeuw1999)." (5.1 Primordial Disk Dust Masses); distance from mean distance to OB stars of Upper Sco (cite: deZeeuw1999)  
  > "We adopt $d=145$ pc, which is the mean distance to the OB stars of Upper Sco (cite: deZeeuw1999)." (5.1 Primordial Disk Dust Masses)

## Data provenance

- ALMA projects: 2013.1.00395.S, 2011.0.00966.S
- bands: Band 7 (0.88 mm)  
  > "All observations used band 7 with the correlator configured to record dual polarization." (3 ALMA Observations)
- frequencies and spectral setup: Cycle 2 SPWs at 334.2, 336.1, 346.2, 348.1 GHz, 1.875 GHz each; CO window 0.488 MHz (0.429 km/s) channels  
  > "Spectral windows for Cycle 2 were centered at 334.2, 336.1, 346.2, and 348.1 GHz for a mean frequency of 341.1 GHz (0.88 mm)." (3 ALMA Observations); "The 345.8 GHz window has channel widths of 0.488 MHz (0.429 km s$^{-1}$) to observe the $^{12}$CO $J$ = 3$-$2 line." (3 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "ALMA observations were obtained in Cycle 0 and Cycle 2 using the 12 m array." (3 ALMA Observations)
- configurations: _not stated_
- baselines: Cycle 0 up to ~400 m; Cycle 2 out to 650 m  
  > "Cycle 2 observations used between 34 and 36 antennas with baselines extending out to 650 m, corresponding to an angular resolution of 0$\overset{''}{.}$34." (3 ALMA Observations)
- angular resolution: ~0.55" (Cycle 0); 0.34" (Cycle 2)  
  > "Cycle 0 observations used between 17 and 28 antennas with maximum baselines of $\sim$400 m, for an angular resolution of $\sim$0$\overset{''}{.}$55." (3 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5.5 min (Cycle 0), 2.5 min (Cycle 2) typical  
  > "The typical on-source integration times were 5.5 minutes for Cycle 0 observations and 2.5 minutes for Cycle 2 observations." (3 ALMA Observations)
- observing dates: Cycle 0: 2012 Aug-Dec; Cycle 2: 2014 June-July  
  > "Twenty sources were observed in Cycle 0 between 2012 August and 2012 December. Eighty-seven sources were observed in 2014 June and 2014 July." (3 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79599 GHz)
- Other facility **Spitzer/WISE**: infrared excess disk selection (via Carpenter2006, Luhman2012)  
  > "that are thought to be surrounded by a disk based on the presence of excess infrared emission observed by *Spitzer* or *WISE*" (2 Stellar Sample)
- Other facility **2MASS / DENIS**: photometry and positions for stellar properties  
  > "luminosity was estimated using J-band photometry from the Two Micron All Sky Survey" (2 Stellar Sample)
- External data: Taurus 0.89 mm flux catalog, scaled to 0.88 mm with S∝ν^2.4  
  > "we use the 0.89 mm flux densities, scaled to our mean wavelength of 0.88 mm assuming $S_{\nu}\propto\nu^{2.4}$" (6.2 Relative Dust Masses) [from (cite: Andrews2013)]
- External data: Disk classification and spectral types of Upper Sco stars  
  > "Spectral types were taken from (cite: Luhman2012), with an assumed uncertainty of $\pm$1 subclass." (2 Stellar Sample) [from (cite: Luhman2012)]
- External data: Flux 218.76±0.81 mJy for 2MASS J16042165-2130284  
  > "we adopt a flux of $218.76\pm0.81$ mJy measured by (cite: Zhang2014) using a 1$\overset{''}{.}$5 radius circular aperture." (4.1 Continuum Fluxes) [from (cite: Zhang2014)]
- Simulation/model as data: Siess et al. 2000 pre-main-sequence tracks (Z=0.02, no overshoot) for stellar masses  
  > "using the (cite: Siess2000) pre-main-sequence evolutionary tracks with a metallicity of $Z=0.02$ and no convective overshoot." (2 Stellar Sample)

## Processing

### Calibration

- pipeline or manual: CASA with reduction scripts provided by ALMA project  
  > "The reduction scripts were kindly provided by the ALMA project." (3 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (mostly), Neptune, J1733-130 (see Table)  
  > "2014 Jun 15 | 34 | 16-650 | 0.78 | Titan, J1733-130" (Table 2)
- flux scale uncertainty: 10% (1σ)  
  > "We assume a 1$\sigma$ calibration uncertainty of 10$\%$." (3 ALMA Observations)
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
- continuum subtraction: uvcontsub, linear fit to continuum in the CO spectral window  
  > "subtracting the continuum dust emission using the *uvcontsub* routine in CASA, which removes a linear fit to the continuum in the spectral window containing the CO line" (4.2 CO Line Fluxes)
- line free channels: continuum: exclude -15 to +30 km/s about CO rest frequency (LSR)  
  > "the four spectral windows were combined after excluding a -15 to +30 km s$^{-1}$ region about the $^{12}$CO $J$ = 3$-$2 rest frequency" (4.1 Continuum Fluxes)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.35" (50 au)  
  > "compact relative to the beam size of $\sim$0$\overset{''}{.}$35 (50 au)" (4.1 Continuum Fluxes)
- final rms: _not stated_

### Inherited from earlier work

- Stellar luminosities, Teff and masses determined as in Carpenter2014  
  > "Stellar luminosities ($L_*$), effective temperatures ($T_*$), and masses ($M_*$) were determined as described in (cite: Carpenter2014)." (2 Stellar Sample) [from (cite: Carpenter2014)]
- Dust opacity and temperature assumptions follow Andrews2013  
  > "For consistency, we follow the opacity and temperature assumptions of (cite: Andrews2013)" (5.1 Primordial Disk Dust Masses) [from (cite: Andrews2013)]
- Power-law fit approach following Andrews2013 using Kelly2007  
  > "Following (cite: Andrews2013), we fit a power law to dust mass as a function of stellar mass using the Bayesian approach of (cite: Kelly2007)" (5.2 Stellar Mass Dependence) [from (cite: Andrews2013); (cite: Kelly2007)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, clean threshold/masks) for images and CO cubes
- CASA version used
- Priors/sampler settings of the Kelly (2007) fit
- Details of how Taurus stellar masses and upper limits entered Kaplan-Meier tests
- Deconvolution details for clean-component aperture photometry
- Final rms and beam per source

## Analysis recipe

1. **Visibility error rescaling**: Grid visibilities in uv, scale sigma to empirical scatter per SPW/polarization; apply median scale factor of cells with ≥10 visibilities  
  > "The median scaling factor of the cells with at least 10 visibilities was then applied to all $\sigma$ values for that polarization and spectral window." (3 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux densities**: uvmodelfit point source; elliptical Gaussian if BIC favors at 3σ; aperture photometry for two cavity sources; uvmultifit for fields with secondary sources  
  > "Flux densities were determined by first fitting a point source to the visibility data using the *uvmodelfit* routine in CASA." (4.1 Continuum Fluxes)
   - software: CASA uvmodelfit, uvmultifit
   - parameter: detection if flux >3× uncertainty; non-detections refit at fixed expected position (2MASS + PPMXL proper motions)  
  > "If the flux density of a source is less than three times its statistical uncertainty, the source is considered a non-detection" (4.1 Continuum Fluxes)
   - fitting: BIC model selection; adopt Gaussian if point-source probability <0.0027  
  > "if the probability of a point-source model relative to an elliptical Gaussian model is $<0.0027$ ($3\sigma$ confidence), we adopt the latter model for the source." (4.1 Continuum Fluxes)
   - validation: image-domain search for >5σ secondary sources  
  > "we searched each field in the image domain for any pixels (not including those associated with the target star) brighter than five times the RMS noise of the image." (4.1 Continuum Fluxes)
3. **Measure CO J=3-2 line fluxes**: uvcontsub, then aperture photometry on clean components+residuals, with per-source velocity range and optimal aperture; 5σ detection threshold; 0.3" aperture over -1.5 to 10.5 km/s for non-detections  
  > "For sources that were not detected at $\geq5\sigma$ using the above method, we measured the flux using a 0$\overset{''}{.}$3 radius aperture between the velocity range of $-$1.5 km s$^{-1}$ and 10.5 km s$^{-1}$." (4.2 CO Line Fluxes)
   - software: CASA
   - parameter: uncertainty = std of 20 random apertures  
  > "we measured the flux within 20 circular apertures of the same radius and over the same velocity range randomly distributed around the clean component and residual images" (4.2 CO Line Fluxes)
   - fitting: _not stated_
   - validation: Repeated at 50-62 km/s (emission-free): no 5σ detections, one 3σ  
  > "No 5$\sigma$ detections were identified in this velocity range, but one 3$\sigma$ detection was made." (4.2 CO Line Fluxes)
4. **Derive dust masses**: Optically thin isothermal M_d = S d^2/(κ B(T_d))  
  > "For optically thin, isothermal dust emission, the dust mass is given by" (5.1 Primordial Disk Dust Masses)
   - parameter: upper limits = 3σ plus any positive flux  
  > "calculated as three times the uncertainty plus any positive measured flux density" (5.1 Primordial Disk Dust Masses)
   - assumption: κ=2.3 cm2/g at 230 GHz, ∝ν^0.4; T_d=25 K (L*/Lsun)^0.25; d=145±20 pc  
  > "assuming a dust opacity of $\kappa_{\nu}=2.3$ cm$^2$g$^{-1}$ at 230 GHz which scales with frequency as $\nu^{0.4}$." (5.1 Primordial Disk Dust Masses)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dust mass vs stellar mass relation**: Cox proportional hazards test for correlation; Bayesian linear regression with censoring (Kelly 2007)  
  > "we fit a power law to dust mass as a function of stellar mass using the Bayesian approach of (cite: Kelly2007), which incorporates uncertainties in both parameters, intrinsic scatter about the relation, and observational upper limits." (5.2 Stellar Mass Dependence)
   - software: R
   - fitting: Kelly (2007) Bayesian method including intrinsic scatter and upper limits  
  > "we fit a power law to dust mass as a function of stellar mass using the Bayesian approach of (cite: Kelly2007), which incorporates uncertainties in both parameters, intrinsic scatter about the relation, and observational upper limits." (Stellar Mass Dependence)
   - validation: _not stated_
6. **Stack debris/evolved transitional non-detections**: Images with 0.4" circular beam centered on stellar position, noise-weighted mean; 4 stars with offset sources excluded  
  > "Each pixel of the stacked image was calculated as the mean of the corresponding pixels of the source images, weighted by the RMS noise of each image." (5.3 Debris/Evolved Transitional Disks)
   - assumption: median dust temperature 18 K  
  > "assuming a median dust temperature of 18 K" (5.3 Debris/Evolved Transitional Disks)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare Upper Sco with Taurus**: Compare Mdust/M* using log-rank and Peto-Peto tests and Kaplan-Meier mean estimates, with Taurus from Andrews2013 rescaled to 0.88 mm  
  > "Figure [27] shows the distributions of $M_{\mathrm{dust}}/M_*$ in Taurus and Upper Sco found using the Kaplan$-$Meier estimator for censored data." (6.2 Relative Dust Masses)
   - software: R
   - fitting: _not stated_
   - validation: Cox test shows no Mdust/M* correlation with M* in either region  
  > "we find $p$ values of 0.19 and 0.49 for Taurus and Upper Sco, respectively, consistent with no correlation." (6.2 Relative Dust Masses)
8. **Constrain CO non-detections**: Brightness-temperature dilution and optically thin column density analysis (Mangum & Shirley 2015)  
  > "we place a $5\sigma$ upper limit on the CO $J$ = 3$-$2 optical depth of $\tau_{\mathrm{CO}}=0.28$" (6.2 The Relationship between Gas and Dust)
   - assumption: T_CO ≥20 K, inclination 60°, gas-to-dust 100, CO/H2 = 7e-5, disk radius 43.5 au  
  > "Assuming a gas to dust mass ratio of 100, a disk radius of 43.5 au to fill the measurement aperture" (6.2 The Relationship between Gas and Dust)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, uvmodelfit, uvcontsub, imaging  
  > "The data were calibrated using the Common Astronomy Software Applications (CASA) package (cite: McMullin2007)." (3 ALMA Observations)
- **uvmultifit** : multi-component visibility fits with secondary sources  
  > "were fit to each source using the *uvmultifit* Python library (cite: Marti-Vidal2014)" (4.1 Continuum Fluxes)
- **R** : Cox, log-rank, Peto-Peto tests and Kaplan-Meier  
  > "implemented with the *R Project for Statistical Computing* (cite: R)" (5.2 Stellar Mass Dependence)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections, primordial disks | 53 of 75 | not stated | sources | 2 | Of the 75 primordial disks in the sample, 53 are detected in the dust continuum and 26 in CO. |
| CO >5σ detections, primordial disks | 26 of 75 | not stated | sources | 3 | Of the 75 primordial disks in the sample, 53 are detected in the dust continuum and 26 in CO. |
| Debris/evolved transitional continuum detections | 5 of 31 | not stated | sources | 2 | Of the 31 disks classified as debris/evolved transitional disks, 5 are detected in the continuum and none in CO. |
| Mdust-M* slope | 1.67 | ±0.37 | dimensionless | 5 | $\log (M_{\mathrm{dust}}/M_{\oplus}) = (1.67\pm0.37)\log(M_*/M_{\odot}) + (0.76\pm0.21)$ |
| Mdust-M* intercept | 0.76 | ±0.21 | log M_earth | 5 | $\log (M_{\mathrm{dust}}/M_{\oplus}) = (1.67\pm0.37)\log(M_*/M_{\odot}) + (0.76\pm0.21)$ |
| Intrinsic scatter | 0.69 | ±0.08 | dex | 5 | with an intrinsic scatter of $0.69\pm0.08$ dex |
| Median detected dust mass | 0.52 | not stated | M_earth | 4 | detected dust masses range from 0.17 to 126 $M_{\oplus}$, with a median of 0.52 $M_{\oplus}$. |
| Mean log(Mdust/M*) Taurus | -4.44 | ±0.05 | dex | 7 | $\langle\log(M_{\mathrm{dust}}/M_*)\rangle = -4.44 \pm 0.05$ in Taurus |
| Mean log(Mdust/M*) Upper Sco | -5.08 | ±0.08 | dex | 7 | $\langle\log(M_{\mathrm{dust}}/M_*)\rangle = -5.08 \pm 0.08$ in Upper Sco |
| Difference Taurus-Upper Sco | 0.64 | ±0.09 | dex | 7 | $\Delta\langle\log(M_{\mathrm{dust}}/M_*)\rangle = 0.64\pm0.09$ (Taurus-Upper Sco) |
| Stacked debris disk dust mass 3σ upper limit | 0.06 | not stated | M_earth | 6 | find a $3\sigma$ upper limit to the dust mass of 0.06 $M_{\oplus}$ |
| CO optical depth 5σ upper limit | 0.28 | not stated | dimensionless | 8 | $\tau_{\mathrm{CO}}=0.28$ |
| CO emitting radius upper limit | ~40 | not stated | au | 8 | sets an upper limit on $R_{\mathrm{CO}}$ of $\sim$40 au |

## Qualitative findings

- CO flux is correlated with continuum flux over ~3 orders of magnitude  
  > "This figure shows that CO flux is correlated with continuum flux over $\sim3$ orders of magnitude." (6.2 The Relationship between Gas and Dust)

## Claim tuples

- H: Dust masses in Upper Sco are lower than in Taurus | E: Compare Mdust/M* distributions with censored statistics | R: Δ<log(Mdust/M*)> = 0.64±0.09; p~1e-7 | F: Mdust/M* lower in Upper Sco by factor ~4.5 | **supported**
- H: Disk dust mass correlates with stellar mass in Upper Sco | E: Cox test and Kelly regression | R: slope 1.67±0.37, p=2.1e-4 | F: Strong evidence for correlation, slope consistent with Taurus | **supported**
- H: Why half of continuum-detected disks lack CO | E: Brightness temperature and column density limits | R: R_CO ≲40 au if optically thick or τ≲0.28 with ~1000x depletion | F: CO compact or heavily depleted | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lower Upper Sco dust mass could instead reflect grain growth (opacity change) with unchanged dust mass; cannot be excluded  
  > "Thus, we cannot exclude the possibility that the disk mass distribution is the same, but the underlying particle size distribution differs." (7.1 Dust Mass Evolution)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute dust masses depend on assumed opacity and temperature  
  > "relative dust masses within the sample may be more accurate than the absolute dust masses if dust properties are similar within Upper Sco." (5.1 Primordial Disk Dust Masses)
- Caveat (inferred, ours): Taurus and Upper Sco upper limits computed differently
- Caveat (inferred, ours): Upper Sco age uncertain
- Caveat (inferred, ours): Single wavelength; opacity and temperature degeneracy
- Caveat (inferred, ours): T_d-L* relation may differ between regions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data from ALMA projects 2011.0.00966.S and 2013.1.00395.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00966.S and ADS/JAO.ALMA#2013.1.00395.S." (Acknowledgments)
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Fit priors
- Missing: Taurus catalog values must be fetched from Andrews2013
- Data volume (inferred): ~50-150 GB raw for two projects (107 short-integration fields)
- Score (inferred): 3/5, Tables of fluxes and masses allow checking, but imaging and fitting details are sparse.
- Rediscovery candidate: yes, Public archival data, clear recipe for flux fits and dust masses, numeric results.

## Links

- Method: (cite: Carpenter2014) (stellar property derivation and earlier Upper Sco ALMA sample)
- Method: (cite: Andrews2013) (Taurus catalog, opacity and temperature prescription)
- Method: (cite: Kelly2007) (Bayesian regression with censoring)
- Companion: (cite: Carpenter2014) (Cycle 0 Upper Sco sample of 20 disks)
- Related: Taurus submillimeter survey (Andrews2013)
- Related: Luhman & Mamajek 2012 Upper Sco disk census

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00966.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00526.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 51,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
