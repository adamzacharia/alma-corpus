# ALMA Observations of SPT-discovered, Strongly Lensed, Dusty, Star-forming Galaxies

`2013ApJ...767..132H` | The Astrophysical Journal 2013 | first author: Hezaveh, Y. D. | arXiv: 1303.2722 | DOI: 10.1088/0004-637X/767/2/132

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are four SPT-discovered dusty sources gravitationally lensed, and what are their magnifications and intrinsic properties from visibility-plane lens modeling?  
  > "These observations confirm the lensing origin of these objects, allow us to measure the their intrinsic sizes and luminosities" (abstract)
- Target **SPT0346-52**: coordinates SPT-S J034640-5205.1  
  > "SPT-S J034640$-$5205.1 | 5.656" (Table 1); z/distance z=5.656 (lens assumed z=0.8)  
  > "SPT-S J034640$-$5205.1 | 5.656" (Table 1); distance from ALMA Band 3 line survey (2011.0.00957.S)  
  > "SPT-S J034640$-$5205.1 | 5.656" (Table 1)
- Target **SPT0418-47**: coordinates SPT-S J041840-4752.0  
  > "SPT-S J041840$-$4752.0 | 4.224   | 0.265" (Table 1); z/distance z=4.224; lens z=0.265  
  > "SPT-S J041840$-$4752.0 | 4.224   | 0.265" (Table 1); distance from ALMA Band 3 survey; VLT FORS2 for lens  
  > "SPT-S J041840$-$4752.0 | 4.224   | 0.265" (Table 1)
- Target **SPT0529-54**: coordinates SPT-S J052903-5436.6  
  > "SPT-S J052903$-$5436.6 | 3.369   | 0.140" (Table 1); z/distance z=3.369; lens z=0.140  
  > "SPT-S J052903$-$5436.6 | 3.369   | 0.140" (Table 1); distance from ALMA Band 3 survey; VLT FORS2 for lens  
  > "SPT-S J052903$-$5436.6 | 3.369   | 0.140" (Table 1)
- Target **SPT0538-50**: coordinates SPT-S J053816-5030.8  
  > "SPT-S J053816$-$5030.8 | 2.782   | 0.404" (Table 1); z/distance z=2.782; lens z=0.404  
  > "SPT-S J053816$-$5030.8 | 2.782   | 0.404" (Table 1); distance from mm and optical spectroscopy (Greve et al. 2012); XSHOOTER for lens  
  > "SPT-S J053816$-$5030.8 | 2.782   | 0.404" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00958.S, 2011.0.00957.S
- bands: Band 7 (275-373 GHz) for imaging; Band 3 for redshift survey  
  > "dual-polarization Band 7 (275-373 GHz) receivers" (2.1 ALMA Imaging)
- frequencies and spectral setup: LO 343.8 GHz; four spectral windows, 128 channels of 15.625 MHz  
  > "The first local oscillator was set to 343.8 GHz, with all four spectral windows configured in time domain mode with 128 channels of 15.625 MHz width" (2.1 ALMA Imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, 16 and 14 antennas  
  > "There were 16 and 14 antennas available on these days, respectively, arranged in a compact configuration." (2.1 ALMA Imaging)
- baselines: 15-150 kλ (Nov 16); 15-240 kλ (Nov 28)  
  > "Observations on Nov 16 included baselines of 15–150 k$\lambda$" (2.1 ALMA Imaging)
- angular resolution: 1.5"x1.3" (Nov 16); 2.1"x0.9" (Nov 28)  
  > "providing a synthesized beam of 2.1$''$$\times$0.9$''$ for the other two sources" (2.1 ALMA Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 61 s and 91 s per source in first and second tracks  
  > "The total integration time per source was 61 and 91 seconds in the first and second tracks, respectively" (2.1 ALMA Imaging)
- observing dates: 2011 Nov 16 and 28  
  > "on two dates, 2011 Nov 16 and 28" (2.1 ALMA Imaging)
- pi or archival as stated: _not stated_
- Other facility **VLT FORS2/XSHOOTER**: Lens galaxy redshifts  
  > "redshifts for the lensing galaxies were measured by fitting Gaussians to the Ca K+H absorption lines" (2.2 Redshift Determinations)
- Other facility **SOAR, VLT ISAAC, HST**: NIR imaging of lenses  
  > "Deep near-infrared (NIR) imaging data were acquired from the Southern Astrophysical Research (SOAR) Telescope" (2.3 Other Supporting Data)
- Other facility **LABOCA, Herschel-SPIRE, SPT**: Photometry for FIR luminosities  
  > "we use 870 $\mu$m observations from LABOCA" (2.3 Other Supporting Data)
- External data: Photometry (SPT, LABOCA, Herschel) provided in Weiss et al.  
  > "are provided in (cite: weiss12)" (2.3 Other Supporting Data) [from (cite: weiss12)]

## Processing

### Calibration

- pipeline or manual: CASA, standard continuum steps  
  > "using standard steps for a continuum observation" (2.1 ALMA Imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto day 1; J0403-360 set to 1.84 Jy day 2  
  > "derived by setting the flux of quasar J0403-360 to 1.84 Jy" (2.1 ALMA Imaging)
- flux scale uncertainty: 15%  
  > "The absolute flux density scale is correct to within 15%." (2.1 ALMA Imaging)
- self calibration: Antenna phases fit simultaneously with lens model in MCMC  
  > "We optimize the $\chi^2$ for each step in the Markov chain by adjusting the $N-1$ antenna phases." (3.1 Lens Modeling)

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
- primary beam correction: Gaussian FWHM 18" in model  
  > "We use a symmetric Gaussian with FWHM of 18$''$ for the primary beam" (3.1 Lens Modeling)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- LABOCA data analysis  
  > "The LABOCA data were analyzed according to the procedure described in (cite: greve12)." (2.3 Other Supporting Data) [from (cite: greve12)]
- Herschel data reduction  
  > "The *Herschel* data are reduced as described in (cite: weiss12)." (2.3 Other Supporting Data) [from (cite: weiss12)]
- Greybody SED model for luminosities  
  > "Luminosities are calculated using a greybody model like that described in (cite: greve12)" (2.3 Other Supporting Data) [from (cite: greve12)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration scripts
- Imaging parameters (weighting, cleaning, cell size)
- MCMC chain length, priors, tempering schedule T
- Greybody fit parameters (T_dust, beta) and FIR luminosity integration range
- Lens priors and source-model starting values
- Phase calibrator names
- Code for lens modeling not released

## Analysis recipe

1. **Calibrate and image ALMA Band 7 data**: Standard CASA continuum processing, clean imaging  
  > "The data were processed with the Common Astronomy Software Applications package" (2.1 ALMA Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Check sources with ICRF positions used to verify astrometry and calibration  
  > "were added to the tracks to verify astrometry and calibration" (2.1 ALMA Imaging)
2. **Visibility-plane lens modeling with integrated phase self-calibration**: Gaussian source lensed by SIE, Fourier transformed and sampled at ALMA uv; chi^2 vs visibilities with antenna phases solved at each chain step  
  > "We model the lenses by generating model lensed images that are subjected to simulated observations and compared to the data." (3.1 Lens Modeling)
   - software: custom MCMC code
   - parameter: Source: 4 params; SIE lens: 5 params  
  > "The lens is modelled as a Singular Isothermal Ellipsoid (SIE) with five free parameters" (3.1 Lens Modeling)
   - assumption: WMAP7 cosmology h=0.71, Om=0.27, OL=0.73  
  > "with WMAP7 parameters, with $h=0.71$, $\Omega_M=0.27$, and $\Omega_\Lambda=0.73$" (1 Introduction)
   - fitting: MCMC with Metropolis-Hastings sampling, tempering (posterior^1/T); noise from differencing adjacent visibilities  
  > "We explore the model parameter space using a Markov Chain Monte Carlo (MCMC) method with Metropolis-Hastings sampling." (3.1 Lens Modeling)
   - validation: Simulated observations recover input antenna phases; extended-array data compared with predictions  
  > "The excellent agreement between input and recovered phase demonstrates that the simultaneous fitting of the lens model and antenna phases does not bias the antenna phase measurement" (Lens Model Self-Calibration)
3. **Derive intrinsic properties**: Divide observed fluxes by magnification; greybody SED for L_FIR; SFR from Kennicutt conversion  
  > "The lens models permit the calculation of some intrinsic properties of the lensed galaxies by simply dividing observed properties by the magnification." (4 Discussion)
   - assumption: Standard starburst SFR conversion (Kennicutt 1998)  
  > "assuming a standard conversion for starbursting galaxies (cite: kennicutt98)" (4 Discussion)
   - fitting: _not stated_
   - validation: LABOCA 870 um flux agrees with modeled ALMA flux within ~10%  
  > "agree with the total flux density in the modeled ALMA data (described below) to within calibration uncertainties, typically 10%" (2.3 Other Supporting Data)

## Software

- **CASA** : Calibration and processing of ALMA data  
  > "The data were processed with the Common Astronomy Software Applications package" (2.1 ALMA Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SPT0346-52 magnification | 5.4 | 0.2 | dimensionless | 2 | 5.4$\pm$0.2 |
| SPT0418-47 magnification | 21.0 | 3.5 | dimensionless | 2 | 21.0$\pm$3.5 |
| SPT0529-54 magnification | 9.4 | 1.0 | dimensionless | 2 | 9.4$\pm$1.0 |
| SPT0346-52 Einstein radius | 1.124 | 0.004 | arcsec | 2 | 1.124$\pm$0.004 |
| SPT0346-52 intrinsic L_FIR | 37.3 | 2.8 | 1e12 Lsun | 3 | 37.3$\pm$2.8 |
| SPT0346-52 SFR surface density | 4200 | not stated | Msun/yr/kpc^2 | 3 | implying a star-formation rate of 4200 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| SPT0346-52 magnification from extended data | 5.26 | 0.12 | dimensionless | 2 | $5.26 \pm 0.12$ |

## Qualitative findings

- ALMA images show ring-like multiple images consistent with galaxy-galaxy lensing; intrinsic sizes 0.5-2.4 kpc  
  > "We find that these objects resolve into ring-like structures expected from gravitational lensing" (5 Conclusion)

## Claim tuples

- H: SPT-selected dusty sources are strongly lensed | E: ALMA 860um imaging plus lens redshifts | R: Multiple images separated by 1-3" with foreground lenses at lower z | F: Lensing origin confirmed | **supported**
- H: Visibility-based modeling with integrated phase correction gives reliable lens models | E: MCMC fits with antenna phases solved per step; simulations and extended-data comparison | R: Phases recovered; compact-data model predicts extended data; magnification 5.26±0.12 agrees | F: Method is robust | **supported**
- H: SPT0346-52 is extreme | E: Lens model of source size and FIR luminosity | R: 3.7e13 Lsun, 4200 Msun/yr/kpc^2 | F: One of the most luminous, intensely star-forming sources known | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single-component source for SPT0538-50 rejected; two components needed  
  > "A single-component source does not provide an adequate fit" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Only compact-configuration data used; SPT0529-54 posterior bimodal  
  > "The extended array data on this source can possibly break this degeneracy." (4 Discussion)
- Caveat (inferred, ours): Simple Gaussian source and SIE lens assumptions
- Caveat (inferred, ours): Lens z for SPT0346-52 assumed 0.8
- Caveat (inferred, ours): Low-resolution data limit source structure constraints

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Lens modeling code
- Missing: MCMC settings
- Missing: Imaging details
- Missing: Photometry tables in unpublished Weiss et al.
- Data volume (inferred): ~ few GB
- Score (inferred): 3/5, Method described but code, MCMC settings and imaging details missing.
- Rediscovery candidate: no, Custom code and unstated settings required.

## Links

- Method: (cite: greve12) (LABOCA analysis and greybody model)
- Companion: (cite: weiss12) (Photometry and redshift survey)
- Companion: (cite: vieira12) (ALMA redshift survey)
- Related: South Pole Telescope survey

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 46,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
