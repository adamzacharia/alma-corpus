# Radial Surface Density Profiles of Gas and Dust in the Debris Disk around 49 Ceti

`2017ApJ...839...86H` | The Astrophysical Journal 2017 | first author: Hughes, A. Meredith | arXiv: 1704.01972 | DOI: 10.3847/1538-4357/aa6b04

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What are the radial surface density profiles of dust and gas in the 49 Ceti debris disk, and what do they imply for the origin of the gas?  
  > "We analyze the ALMA visibilities in tandem with the broad-band spectral energy distribution to measure the radial surface density profiles of dust and gas emission from the system." (abstract)
- Target **49 Ceti**: coordinates _not stated_; z/distance 59 pc  
  > "corresponding to an outer diameter of the CO disk of 430 au at a distance of 59 pc." (3.3 ALMA CO(3-2)); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00195.S
- bands: Band 7  
  > "using the Band 7 receivers under excellent weather conditions" (2.1 ALMA Observations)
- frequencies and spectral setup: Continuum bands at 357 and 344 GHz (2 GHz each); HCN window 1.9 GHz at 355 GHz, 488 kHz channels; CO(3-2) window 234 MHz, 61 kHz channels  
  > "The fourth spectral window, with a bandwidth of 234 MHz and channel spacing of 61 kHz, was centered on the CO(3-2) transition" (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 to 1284 m, 28 12 m antennas  
  > "The observation incorporated 28 12 m antennas with baseline lengths between 17 and 1284 m" (2.1 ALMA Observations)
- angular resolution: continuum 0.47x0.39 arcsec; CO(3-2) 0.50x0.38 arcsec  
  > "| CO(3-2) | 0.50$\times$0.38 | 84 | 8.9 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 40 minutes  
  > "49 Ceti (40 minutes total on source)" (2.1 ALMA Observations)
- observing dates: 2013 November 4  
  > "49 Ceti was observed with ALMA on 2013 November 4." (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.79599 GHz)
- Line: HCN J=4-3 (354.50547 GHz)
- Other facility **CARMA**: 1.3 mm continuum, 2.1±0.7 mJy detection  
  > "We derive a total flux of $2.1 \pm 0.7$ mJy by fitting a point source to the visibilities" (3.2 CARMA Dust Continuum)
- Other facility **SMA**: previously published CO(2-1) data fit jointly  
  > "we fit the new ALMA CO(3-2) visibilities in tandem with previously published SMA CO(2-1) observations of the gas disk (cite: hug08)" (4.2 CO(3-2))
- External data: SED photometry (Yerkes, Michigan, Spitzer IRS, WISE, IRAS, Keck, ISO, Herschel)  
  > "We compare each model to the SED of the 49 Ceti system at observed photometric points gathered from the literature" (4.1 Continuum) [from Table 1 sources, e.g. (cite: rob13), (cite: leb11), (cite: wah07)]
- External data: SMA CO(2-1) visibilities  
  > "previously published SMA CO(2-1) observations of the gas disk (cite: hug08)" (4.2 CO(3-2)) [from (cite: hug08)]

## Processing

### Calibration

- pipeline or manual: CASA and MIRIAD with standard ALMA reduction scripts  
  > "The visibilities were calibrated and imaged using the `CASA` and `MIRIAD` software packages, including the standard reduction scripts provided by ALMA." (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-401  
  > "while the absolute flux scale was calibrated using observations of the quasar J0334-401." (2.1 ALMA Observations)
- flux scale uncertainty: 10%  
  > "The flux scale is subject to a standard 10% systematic calibration uncertainty." (2.1 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "imaged using standard Fourier inversion (assuming natural weighting) and the `CLEAN` algorithm" (2.1 ALMA Observations)
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
- final rms: continuum 0.056 mJy/beam; CO 8.9 mJy/beam; HCN 3.0 mJy/beam  
  > "| 850 $\mu$m Continuum | 0.47$\times$0.39 | 89 | 0.056 |" (Table 1)

### Inherited from earlier work

- Dust modelling approach and assumptions  
  > "The modeling process and simplifying assumptions are described in detail in (cite: ric13) and (cite: ste16)" (4.1 Continuum) [from (cite: ric13); (cite: ste16)]
- Gas surface density similarity solution  
  > "a similarity solution for the surface density (cite: hug08b)" (4.2 CO(3-2)) [from (cite: hug08b)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (cell size, image size, masks, thresholds)
- continuum-subtraction and line-free channels
- MCMC priors ranges and convergence criteria in detail
- LIME setup (photons, grid, collision rates)
- visibility weighting/ SMA data reduction details
- SED photosphere details beyond summary

## Analysis recipe

1. **Image continuum and lines**: Calibrate with CASA/MIRIAD, CLEAN with natural weighting  
  > "imaged using standard Fourier inversion (assuming natural weighting) and the `CLEAN` algorithm" (2.1 ALMA Observations)
   - software: CASA, MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit dust surface density with SED+visibilities**: Joint SED and visibility chi2; single power law, power law with ring, double power law; inner disk of 0.1 micron grains  
  > "We fit the sum of the SED and visibility $\chi^2$ values, assuming uniform priors on all parameters" (4.1.2 MCMC Fitting)
   - software: emcee, MIRIAD uvmodel, MCFOST
   - parameter: about 100 walkers, 1000 steps, ~100 step burn-in  
  > "Most of our MCMC chains included approximately 100 walkers that were allowed to move for 1000 steps" (4.1.2 MCMC Fitting)
   - assumption: geometrically flat, optically thin disk; astrosilicate  
  > "we assume a geometrically flat and optically thin dust disk, astrosilicate opacities" (4.1 Continuum)
   - fitting: affine-invariant MCMC, uniform priors  
  > "we utilize the affine-invariant MCMC fitting technique as described by (cite: good10) and implemented in Python as `emcee`" (4.1.2 MCMC Fitting)
   - validation: AIC and BIC model comparison  
  > "we employ both the AIC and the related Bayesian Information Criterion (BIC)" (4.1.2 MCMC Fitting)
3. **Fit CO gas disk**: LIME non-LTE models fit to ALMA CO(3-2) plus SMA CO(2-1) with coarse-to-fine chi2 grid search, for CO/H2=1e-4 and 1  
  > "we carry out a simple $\chi^2$ minimization via a grid search technique" (4.2 CO(3-2))
   - software: LIME
   - parameter: free: M*, Mdisk, Rc, Rin,gas, gamma, T100, i, h0  
  > "In the final fit, we therefore varied the following parameters: {$M_*$, $M_\mathrm{disk}$, $R_c$, $R_\mathrm{in,gas}$, $\gamma$, $T_{100}$, $i$, $h_0$}." (4.2 CO(3-2))
   - assumption: T∝R^-0.5, vertically isothermal, turbulent linewidth 10 m/s, PA fixed at -71.4 deg  
  > "We further assume a constant turbulent linewidth of 10 m s$^{-1}$" (4.2 CO(3-2))
   - fitting: chi2 grid search  
  > "Instead, we carry out a simple $\chi^2$ minimization via a grid search technique, which is good at locating the best-fit combination of model parameters in a well-behaved space" (4.2 CO(3-2))
   - validation: AIC significance; residual moment maps  
  > "which represents a significantly better fit at the $>10\sigma$ level according to the AIC test" (4.2 CO(3-2))

## Software

- **CASA** : calibration and imaging  
  > "calibrated and imaged using the `CASA` and `MIRIAD` software packages" (2.1 ALMA Observations)
- **MIRIAD** : uvfit, uvmodel, cgcurs measurements  
  > "we use the MIRIAD task `uvfit` to fit an elliptical Gaussian to the visibilities" (3.1 ALMA Dust Continuum)
- **emcee** : MCMC fitting of continuum  
  > "implemented in Python as `emcee` by (cite: fore13)" (4.1.2 MCMC Fitting)
- **LIME** : non-LTE CO radiative transfer  
  > "non-LTE Line Modeling Engine (LIME) radiative transfer code written by (cite: bri10)" (4.2 CO(3-2))
- **MCFOST** : Mie theory opacities  
  > "using the Mie theory implementation in MCFOST (cite: pin06; pin09)" (4.1 Continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 850 um flux density | 17 | 3 | mJy | 1 | This method results in a measured total flux density of $17\pm3$ mJy. |
| CO(3-2) integrated flux | 6.0 | 0.1 | Jy km/s | 1 | We derive a total flux density of 6.0$\pm$0.1 Jy km s$^{-1}$. |
| Dust disk inclination (ring fit) | 80.6 | 0.4 | deg | 1 | this axis ratio implies an inclination to the line of sight of $80.6^\circ \pm 0.4^\circ$ |
| Single power law index p | 1.29 | +0.11/-0.11 | dimensionless | 2 | / $p$                                                         / $1.29^{+0.11}_{-0.11}$  / 1.27 |
| Ring radius | 114 | +3/-3 | au | 2 | / $R_\mathrm{Ring}$ \[au\]                                    / –                       / –        / $114^{+3}_{-3}$ |
| Gas surface density index gamma (CO/H2=1e-4) | -0.5 | not stated | dimensionless | 3 | / $\gamma$                                          / -0.5       / -2.0 to 1.6     / -1.8 |
| Stellar mass from CO fit | 2.1 | not stated | Msun | 3 | The derived stellar mass of 2.1 M$_\ensuremath{\odot}$ is in good agreement |
| Systemic LSR velocity | 2.78 | 0.13 | km/s | 3 | We settle on a best-fit LSR velocity of $2.78\pm0.13$ km s$^{-1}$. |
| Scale height factor h0 (CO/H2=1e-4) | 0.75 | not stated | dimensionless | 3 | / $h_0$                                             / 0.75       / 0.2 to 1.2      / 2.1 |

## Qualitative findings

- HCN(4-3) not detected  
  > "We do not detect any HCN(4-3) emission from the 49 Ceti disk to within the uncertainties in the data." (3.4 ALMA HCN(4-3))

## Claim tuples

- H: Does the gas surface density decrease with radius as in protoplanetary disks? | E: LIME fits to ALMA CO(3-2) and SMA CO(2-1) | R: gamma negative for both CO/H2 values; gamma=0 worse by Δchi2=1631 | F: Gas surface density increases with radius | **supported**
- H: Is there a dust surface density enhancement near 100 au? | E: Joint SED+visibility fits with three profile models, AIC/BIC | R: AIC 2.2-2.9 sigma preference over single power law | F: marginally significant enhancement near ~110 au | **partially**
- H: Is the gas disk smaller than the dust disk? | E: CO outer radius vs dust model outer radius | R: CO ~220 au vs dust ~300 au | F: gas disk smaller than dust disk | **supported**
- H: Is the CO disk axisymmetric? | E: Residuals of axisymmetric model | R: residuals ~16-20% of peak with offsets | F: suggests spiral arms or warp | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Grid search does not characterize uncertainties on CO parameters  
  > "does not efficiently characterize the uncertainties on each parameter" (4.2 CO(3-2))
- Caveat (inferred, ours): CO fit parameters have no uncertainties
- Caveat (inferred, ours): Assumed T∝R^-0.5 and CO/H2 values drive gas interpretation
- Caveat (inferred, ours): Dust enhancement only marginal
- Caveat (inferred, ours): Single-track CARMA flux affects beta

## Reproducibility

- Data public (paper): ALMA project listed in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00195.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Continuum-modeling code (Ricarte et al.) not stated as released
- Missing: LIME grid details
- Missing: SMA CO(2-1) data access
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Data public and models described, but CLEAN and LIME details and code are missing.
- Rediscovery candidate: no, Fitting code and imaging settings incomplete; relies on SMA data and in-house code.

## Links

- Method: (cite: ric13) (dust disk modeling method)
- Method: (cite: ste16) (dust disk modeling method)
- Companion: (cite: hug08) (SMA CO(2-1) data of 49 Ceti)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
