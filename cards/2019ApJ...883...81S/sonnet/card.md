# Evidence for Inside-out Galaxy Growth and Quenching of a z ∼ 2 Compact Galaxy From High-resolution Molecular Gas Imaging

`2019ApJ...883...81S` | The Astrophysical Journal 2019 | first author: Spilker, Justin S. | arXiv: 1908.02294 | DOI: 10.3847/1538-4357/ab3804

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Are the molecular gas fraction and depletion time of the compact z=2.234 star-forming galaxy COSMOS 27289 suppressed in its center, as expected for inside-out quenching?  
  > "are lower in the central 1–2 kpc of the galaxy and rise at larger radii" (abstract)
- Target **COSMOS 27289**: coordinates _not stated_; z/distance z = 2.234  
  > "COSMOS 27289, a massive, compact star forming galaxy at $z=2.234$" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00137.S
- bands: ALMA 343 GHz (rest-frame ~270 um)  
  > "archival ALMA 343 GHz imaging of COSMOS 27289 from project 2015.1.00137.S" (2.2 Archival ALMA and HST Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz  
  > "combining the full 7.5 GHz of observed bandwidth using natural weighting of the visibilities" (2.2 Archival ALMA and HST Data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5x0.7 arcsec  
  > "The ALMA data reach a spatial resolution of $\sim$0.5$\times$0.7$''$" (2.2 Archival ALMA and HST Data)
- max recoverable scale: _not stated_
- sensitivity: 0.14 mJy/beam, peak S/N ~20  
  > "a sensitivity of 0.14 mJy/beam" (2.2 Archival ALMA and HST Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA data, re-reduced  
  > "We downloaded, re-reduced, and re-imaged these data using the standard ALMA pipeline." (2.2 Archival ALMA and HST Data)
- Other facility **VLA**: CO(1-0) imaging in C array (16A-203) and new B array (17B-223), combined  
  > "The B array observations were taken in October 2017 in project 17B-223 (PI: Spilker)." (2.1 VLA Observations)
- Other facility **HST WFC3/F160W (CANDELS/3D-HST)**: rest-frame 500 nm stellar light image  
  > "COSMOS 27289 was observed in the HST WFC3/F160W filter as part of the CANDELS program" (2.2 Archival ALMA and HST Data)
- Other facility **Herschel PACS/SPIRE**: far-IR photometry for L_IR and SFR  
  > "This source was detected by the *Herschel*/PACS and SPIRE instruments" (2.4 Converting Observed to Physical Quantities)
- External data: Stellar mass 1.3e11 Msun from 3D-HST SED fitting  
  > "the stellar mass from full UV-to-IR SED fitting from the 3D-HST catalog, $1.3 \times 10^{11}$ $\rm{M}_\odot$" (2.4 Converting Observed to Physical Quantities) [from (cite: skelton14)]
- External data: Simulated radial gas fraction profiles of quenching galaxies  
  > "We use the simulated outputs from (cite: tacchella16), specifically of galaxies classified in their ‘quenching’ phase" (3.3 Inside-Out Quenching and Comparison to Simulations) [from (cite: tacchella16)]
- Simulation/model as data: Tacchella et al. 2016 simulation, 12 galaxies with logMstar>10.2 at z=2, molecular fraction via Krumholz 2013  
  > "using the 12 simulated galaxies with stellar masses $\log\ensuremath{M_{\rm{star}}}/\ensuremath{\rm{M}_\odot}>10.2$ at $z=2$" (3.3 Inside-Out Quenching and Comparison to Simulations)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline (re-reduced)  
  > "We downloaded, re-reduced, and re-imaged these data using the standard ALMA pipeline." (2.2 Archival ALMA and HST Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "combining the full 7.5 GHz of observed bandwidth using natural weighting of the visibilities" (2.2 Archival ALMA and HST Data)
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

- alpha_CO = 1 Msun (K km/s pc^2)^-1  
  > "we assume a single CO-H$_2$ conversion factor $\ensuremath{\alpha_{\rm{CO}}}= 1$ $\rm{M}_\odot$(K $\rm{km\,s}^{-1}$ pc$^2$)$^{-1}$ as in our previous work" (2.4 Converting Observed to Physical Quantities) [from (cite: spilker16b)]
- first-order Sersic residual correction for radial profiles  
  > "following (cite: szomoru10; szomoru12)" (2.3 Radial Profile Fitting) [from (cite: szomoru10; szomoru12)]

### Not stated but needed to reproduce (our reading)

- ALMA pipeline/CASA version and calibrators
- uv-fit priors, MCMC settings and Sersic parameters for VLA and ALMA
- ALMA continuum image size/cell
- Modified blackbody parameters (T, beta) for L_IR
- Exact 270 um flux to SFR conversion constant
- Elliptical aperture parameters and radial bins
- Weight-rescaling details for combining VLA data

## Analysis recipe

1. **Fit HST stellar light profile**: Single Sersic fit to F160W with first-order residual correction  
  > "we fit the WFC3/F160W image using the `GALFIT` software (cite: peng10)" (2.3 Radial Profile Fitting)
   - software: GALFIT
   - fitting: _not stated_
   - validation: agrees with published structural parameters  
  > "We find structural parameters in excellent agreement with the values published previously for this galaxy" (2.3 Radial Profile Fitting)
2. **Fit VLA CO and ALMA dust visibilities**: uv-plane Sersic model fitting with MCMC, residual profile added  
  > "This code uses a Bayesian Markov Chain Monte Carlo (MCMC) sampling algorithm to determine the best-fit shape parameters and their covariances." (2.3 Radial Profile Fitting)
   - software: visilens
   - fitting: MCMC, chi^2 on visibilities  
  > "compared to the data with a standard $\chi^2$ figure of merit based on the uncertainty of each visibility" (2.3 Radial Profile Fitting)
   - validation: little structure in residuals  
  > "For both the VLA and ALMA data, little significant structure is seen in the residuals." (2.3 Radial Profile Fitting)
3. **Convert to mass, gas, SFR profiles and derive f_H2, t_dep, sSFR**: Measure profiles in identical elliptical apertures from F160W; apply global conversion factors  
  > "We thus measure all radial profiles in identical elliptical apertures centered on the peak of the F160W emission" (2.3 Radial Profile Fitting)
   - assumption: single M/L, alpha_CO=1, single 270um-to-SFR conversion with SFR~400 Msun/yr  
  > "a single mass-to-light ratio for the F160W image, a single $\alpha_{\rm{CO}}$ conversion factor for the CO(1–0) data, and a single 270 $\mu\rm{m}$-to-SFR conversion" (2.4 Converting Observed to Physical Quantities)
   - fitting: _not stated_
   - validation: discussed likely radial variations of conversion factors accentuate the trend  
  > "the probable radial variations in conversion factors to physical units in each case serve to accentuate the central low gas fraction and short depletion time we observe" (3.2 Impact of Assumptions in Physical Conversion Factors)
4. **Compare with simulation**: Mean gas fraction profile of 12 quenching galaxies from Tacchella+16 with Krumholz13 molecular fraction  
  > "we estimate the molecular fraction using a crude analytic approximation from (cite: krumholz13)" (3.3 Inside-Out Quenching and Comparison to Simulations)
   - assumption: solar metallicity, high stellar density, no hot gas  
  > "we apply the (cite: krumholz13) results assuming solar metallicity and high galactic stellar density and neglect any contribution from hot (non-molecular) gas" (3.3 Inside-Out Quenching and Comparison to Simulations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GALFIT** : Sersic fit to HST F160W  
  > "we fit the WFC3/F160W image using the `GALFIT` software (cite: peng10)" (2.3 Radial Profile Fitting)
- **visilens** : uv-plane Sersic fitting of VLA and ALMA data  
  > "we used the `visilens` code originally developed for modeling of gravitational lensing systems in the $uv$-plane" (2.3 Radial Profile Fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA C+B CO(1-0) sensitivity per 125 km/s channel | 34 | not stated | uJy/beam | 0 | The combined C and B array data reach a sensitivity of 34 $\mu\rm{Jy}$/beam in the 125 $\rm{km\,s}^{-1}$ channel width |
| F160W Sersic index | 3.1 | 0.1 | dimensionless | 1 | Sérsic index $n = 3.1 \pm 0.1$ and circularized effective radius $2.6 \pm 0.1$ kpc |
| F160W circularized effective radius | 2.6 | 0.1 | kpc | 1 | Sérsic index $n = 3.1 \pm 0.1$ and circularized effective radius $2.6 \pm 0.1$ kpc |
| Central depletion time | 10-15 | not stated | Myr | 3 | We find extremely short depletion times in the central regions of COSMOS 27289, $\sim$10-15 Myr |
| Central gas fraction | ~0.07, doubling to maximum at 2-4 kpc | not stated | dimensionless | 3 | the gas fraction approximately doubles from $\sim0.07$ in the central 1–2 kpc of this galaxy to its maximum at radii $\sim$2-4 kpc |

## Qualitative findings

- Simulated f_H2 profile peaks at larger radii (3-8 kpc) with stronger central suppression and lower normalization than observed  
  > "the simulated $f_{\rm{H}_2}$ profile peaks at larger radii $\sim$3-8 kpc" (3.3 Inside-Out Quenching and Comparison to Simulations)

## Claim tuples

- H: Quenching of COSMOS 27289 proceeds inside-out | E: Radial f_H2 and t_dep profiles from VLA CO, HST, ALMA | R: f_H2 ~0.07 in center rising to maximum at 2-4 kpc; t_dep 10-15 Myr central, doubling by 3 kpc | F: Consistent with inside-out quenching | **supported**
- H: Hydrodynamical simulations reproduce the observed profile | E: Compared with Tacchella+16 quenching galaxies | R: Good qualitative agreement, peak at larger radii | F: Reasonable quantitative agreement | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data are low resolution, giving large t_dep uncertainties; simple conversion factors assumed  
  > "though with significantly larger uncertainties arising from the low resolution of the ALMA data" (3.1 Depletion of Molecular Gas in the Central Kiloparsecs)
- Caveat (inferred, ours): Peak CO S/N only ~8
- Caveat (inferred, ours): Single object
- Caveat (inferred, ours): Uniform alpha_CO, M/L, T_dust assumptions
- Caveat (inferred, ours): Dust continuum only marginally resolved

## Reproducibility

- Data public (paper): ALMA data described as archival; VLA 16A-203 and 17B-223 projects named  
  > "We also make use of archival ALMA 343 GHz imaging of COSMOS 27289 from project 2015.1.00137.S." (2.2 Archival ALMA and HST Data)
- Products in archive: _not stated_
- Missing: visilens settings and priors
- Missing: ALMA pipeline version
- Missing: uv-weight rescaling details
- Missing: conversion constants
- Data volume (inferred): ~10-50 GB (VLA B+C array plus ALMA single band)
- Score (inferred): 3/5, Public data and a clear approach, but many fit and conversion details are missing.
- Rediscovery candidate: no, The ALMA role is minor and key VLA processing and fitting details are not given.

## Links

- Method: (cite: szomoru10; szomoru12) (profile residual correction)
- Method: (cite: spilker16) (visilens uv-plane fitting code)
- Companion: (cite: spilker16b) (previous lower-resolution VLA observations of COSMOS 27289)
- Related: CANDELS
- Related: 3D-HST
- Related: VLA 16A-203
- Related: VLA 17B-223

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 32,
  "rate": 0.464
 },
 "evidence_ok": true
}
```
