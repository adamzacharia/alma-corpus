# Massive, Absorption-selected Galaxies at Intermediate Redshifts

`2018ApJ...856L..23K` | The Astrophysical Journal Letters 2018 | first author: Kanekar, N. | arXiv: 1803.07563 | DOI: 10.3847/2041-8213/aab6ab

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Do high-metallicity absorption-selected (DLA/sub-DLA) galaxies at z~0.5-0.8 have molecular gas properties similar to emission-selected star-forming galaxies?  
  > "allow us to compare the gas properties of high-metallicity, absorption-selected galaxies to those of emission-selected, star-forming galaxies, to test whether the same galaxy populations are being selected by the different methods." (Results and Discussion)
- Target **Seven DLA/sub-DLA fields (B0827+243, B1629+120, J0058+0155, J2335+1501, J1323-0021, J1436-0051, J0138-0005)**: coordinates _not stated_; z/distance z_abs = 0.5247-0.7821  
  > "B0827+243 | $0.941$ | $0.5247$ | $2.0$" (Table 1); distance from absorber redshifts from low-ionization metal lines  
  > "B0827+243 | $0.941$ | $0.5247$ | $2.0$" (Table 1)

## Data provenance

- ALMA projects: 2013.1.01178.S, 2015.1.01034.S, 2015.1.00561.S
- bands: Band 4  
  > "using the ALMA Band-4 receivers" (Observations and Data analysis)
- frequencies and spectral setup: Four 1.875 GHz bands; one (480 channels, FDM) on redshifted CO(2-1), three (128 channels, TDM) for continuum; ~8 km/s resolution, ~4000 km/s coverage  
  > "with one band (sub-divided into 480 channels, using the FDM mode of the correlator) covering the expected redshifted CO(2$-$1) line frequency" (Observations and Data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams ~1.6-2.9 arcsec  
  > "B0827+243 | $0.941$ | $0.5247$ | $2.0$ | $2.1 \times 1.6$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS 150-275 uJy per 100 km/s channel; continuum RMS ~13-20 uJy (~40 uJy for B0827+243)  
  > "The root-mean-square (RMS) noise on the continuum images was $\approx 13-20 \mu$Jy" (Observations and Data analysis)
- time on source: _not stated_
- observing dates: 2014 December to 2017 January  
  > "over 2014 December to 2017 January" (Observations and Data analysis)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- External data: COLD GASS comparison sample (212 CO(1-0) detections)  
  > "the *COLD GASS* sample at low redshifts ($z \lesssim 0.05$), with 212 CO(1$-$0) detections" (Results and Discussion) [from (cite: saintonge11)]
- External data: PHIBSS comparison sample (49 CO(3-2) detections)  
  > "the *PHIBSS* sample at high redshifts ($z \approx 1.3,2.2$) with 49 CO(3$-$2) detections" (Results and Discussion) [from (cite: tacconi13)]
- External data: SFRs from [OII] or Hbeta lines, or U-band continuum for B1629+120  
  > "the star formation rates (SFRs) of the DLA galaxies were inferred from either the \[Oii\]$\lambda$3727Å or H$\beta$$\lambda$4382Å lines" (Results and Discussion) [from (cite: chen05; christensen14; straka16; moller18; rhodin18; rao03)]

## Processing

### Calibration

- pipeline or manual: Initial calibration by ALMA support staff with ALMA pipeline in CASA; self-calibration in AIPS for two bright quasars  
  > "The initial calibration of all data was done by the ALMA support staff, using the ALMA data pipeline in the Common Astronomy Software Applications (CASA) package" (Observations and Data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-calibration for B1629+120 and B0827+243 in AIPS; gains applied to line data  
  > "In two cases (B1629+120 and B0827+243), the quasar was sufficiently bright to allow us to self-calibrate the continuum data" (Observations and Data analysis)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "and used natural weighting, to maximize the signal-to-noise ratio" (Observations and Data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image subtracted to produce residual visibility set  
  > "the continuum image subtracted out to produce a residual visibility data set" (Observations and Data analysis)
- line free channels: _not stated_
- primary beam correction: applied to cubes before line search  
  > "A correction for the ALMA primary beam was applied to the cubes" (Observations and Data analysis)
- array combination: _not stated_
- smoothing: Cubes at velocity resolutions of 50-300 km/s  
  > "The cubes were made at velocity resolutions of $50-300$ km/s," (Observations and Data analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- J1323-0021 (z=0.7163) continuum and system discussed in detail elsewhere  
  > "this system is discussed in detail in (cite: moller18)" (Observations and Data analysis) [from (cite: moller18)]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (cell, image size, masking, deconvolution)
- Channels used for continuum model/subtraction
- Self-calibration solution intervals
- Region definitions for spectral extraction
- Stellar-mass photometry sources and SFR values per galaxy
- How uncertainties on line fluxes were derived
- Flux calibrators and flux scale uncertainty

## Analysis recipe

1. **Calibrate and image CO(2-1) cubes**: Pipeline calibration, AIPS self-cal of continuum for two fields, continuum subtraction, natural-weighted CASA imaging, primary beam correction  
  > "This was then imaged in the CASA package to produce the final spectral cubes." (Observations and Data analysis)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract CO spectra and measure sizes**: Flux per channel in elliptical region containing emission; sizes with CASA fitter  
  > "the final CO spectra were obtained by measuring the flux density per channel in an elliptical region chosen to contain all detected emission" (Observations and Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular gas masses**: Convert CO(2-1) to CO(1-0) luminosity and apply alpha_CO  
  > "we will assume this value for the ratio of the line flux densities in order to infer the CO(1$-$0) line luminosity" (Results and Discussion)
   - assumption: alpha_CO = 4.36 Msun (K km/s pc^2)^-1; CO(2-1)/(1-0) flux ratio 2.5  
  > "we will throughout use $\alpha_{\rm CO} \approx 4.36$ M$_\odot$ (K km/s pc$^{2}$)$^{-1}$" (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate stellar masses**: SED fitting of multi-band photometry with BC03 templates, chi2 minimisation over grid  
  > "M$_\star$ is determined by the parameter-set that minimises the $\chi^2$-statistic across a user pre-defined grid of models." (Results and Discussion)
   - software: HyperZ, LePhare
   - parameter: ages 0.01-13.5 Gyr; e-folding 0.1-30 Gyr; A_V 0-1 mag  
  > "The grid encompasses ages and e-folding time-scales in the ranges 0.01-13.5 Gyrs and 0.1-30 Gyrs respectively" (Results and Discussion)
   - assumption: Chabrier IMF, LMC-Fitzpatrick extinction  
  > "assuming a Chabrier initial mass function" (Results and Discussion)
   - fitting: chi2 minimisation on grid  
  > "M$_\star$ is determined by the parameter-set that minimises the $\chi^2$-statistic across a user pre-defined grid of models." (Results and Discussion)
   - validation: HyperZ and LePhare give consistent masses  
  > "We have verified that `HyperZ` and `LePhare` produce consistent stellar mass estimates, within the uncertainties." (Results and Discussion)
5. **Compare with COLD GASS and PHIBSS**: Compare SFR, Mmol, fmol, depletion times against emission-selected samples with same alpha_CO  
  > "We assume $\alpha_{\rm CO} = 4.36 \: {\rm M}_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for all galaxies." (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : pipeline calibration, imaging, size fitting  
  > "This was then imaged in the CASA package to produce the final spectral cubes." (Observations and Data analysis)
- **AIPS** : self-calibration of continuum  
  > "which was carried out in the Astronomical Image Processing System (cite: greisen03)" (Observations and Data analysis)
- **HyperZ** : SED stellar masses  
  > "matching spectral energy distribution (SED) templates to multi-band photometry using `HyperZ` (cite: bolzonella00)" (Results and Discussion)
- **LePhare** : SED stellar masses  
  > "`LePhare` (cite: arnouts99; ilbert06)" (Results and Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas mass range (detections) | (0.6-8.2)e10 | not stated | Msun | 3 | $M_{\rm Mol} \approx (0.6 - 8.2) \times 10^{10} \: {\rm M}_\odot$ |
| Molecular gas fraction range | 0.29-0.87 | not stated | dimensionless | 3 | $f_{\rm Mol} \equiv \: M_{\rm Mol}/(M_\ast + M_{\rm Mol}) \approx 0.29-0.87)$ |
| SFR range | 0.3-9.5 | not stated | Msun/yr | 0 | $\approx (0.3-9.5) \: {\rm M}_\odot$ yr$^{-1}$ |
| Depletion time range | 3-120 | not stated | Gyr | 5 | $\approx (3 - 120)$ Gyr |
| Median DLA depletion time | ~10 | not stated | Gyr | 5 | the median gas depletion time for the DLA galaxies is $\rm \tau_{\rm depl,DLA} \approx 10$ Gyr |
| CO(2-1) flux B0827+243 | 3.11 | 0.16 | Jy km/s | 2 | $3.11 \pm 0.16$ |

## Qualitative findings

- DLA galaxies have optical properties like star-forming galaxies but much larger gas masses, fractions and depletion times, suggesting quenching or a transition in star formation at z~0.7  
  > "The fact that the DLA galaxies lie below the correlation between SFR and molecular gas mass suggests that star formation activity is being quenched in these systems." (Results and Discussion)

## Claim tuples

- H: High-metallicity absorption-selected galaxies at z~0.7 resemble emission-selected star-forming galaxies in gas properties | E: ALMA CO(2-1) of seven absorbers compared with COLD GASS and PHIBSS | R: Five detections with large Mmol, fmol and low SFR, giving long depletion times | F: Gas properties are distinct from both comparison samples | **supported**
- H: A low alpha_CO could remove the discrepancy | E: Consider alpha_CO ~1 | R: Would lower masses by ~5 but implies ULIRGs | F: Considered unlikely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Same alpha_CO used for direct comparison with emission-selected samples  
  > "To allow for a direct comparison with emission-selected galaxies in the local Universe" (Results and Discussion)
- Alternative: alpha_CO ~1 (starburst) rejected as unlikely  
  > "We hence do not consider this possibility to be likely." (Results and Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample  
  > "While our sample is yet small" (Results and Discussion)
- Limitation (authors): SFR tracers may underestimate SFR in dusty galaxies  
  > "While these tracers may under-estimate the SFR for dusty galaxies" (Results and Discussion)
- Caveat (inferred, ours): Gas masses depend on assumed alpha_CO and r21
- Caveat (inferred, ours): Comparison samples differ in selection and CO transition
- Caveat (inferred, ours): Heterogeneous SFR and stellar mass methods
- Caveat (inferred, ours): No dust-corrected SFRs
- Caveat (inferred, ours): Uncertainties on gas mass exclude systematics

## Reproducibility

- Data public (paper): Data available in ALMA archive  
  > "The data reported in this paper are available though the ALMA archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Photometry and SFR inputs
- Missing: Spectral extraction regions
- Data volume (inferred): ~50-100 GB
- Score (inferred): 5/5, Public data and simple derivations, but imaging details and photometry/SFR inputs are missing.
- Rediscovery candidate: yes, Public data, numeric CO fluxes and masses via a simple recipe.

## Links

- Companion: Møller et al. 2018 (cite: moller18) (Detailed study of the z=0.7163 DLA towards J1323-0021)
- Related: COLD GASS
- Related: PHIBSS

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.00561.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
