# Resolving the planetesimal belt of HR 8799 with ALMA

`2016MNRAS.460L..10B` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Booth, Mark | arXiv: 1603.04853 | DOI: 10.1093/mnrasl/slw040

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Where are the inner and outer edges of the planetesimal belt of HR 8799, and is the inner edge consistent with sculpting by planet b?  
  > "These observations allow the inner edge of the planetesimal belt to be resolved for the first time." (abstract)
- Target **HR 8799**: coordinates _not stated_; z/distance 39.4 pc  
  > "Given the distance to the star of 39.4 pc (cite: leeuwen07)" (2 Observations); distance from van Leeuwen 2007  
  > "Given the distance to the star of 39.4 pc (cite: leeuwen07)" (2 Observations)

## Data provenance

- ALMA projects: 2012.1.00482.S
- bands: Band 6 (1.34 mm)  
  > "HR 8799 was observed with ALMA in band 6 (1.34 mm) for the cycle 1 project 2012.1.00482.S." (2 Observations)
- frequencies and spectral setup: Four 2 GHz basebands centred at 216, 218, 231, 233 GHz, 128 channels of 16 MHz each  
  > "four, 2 GHz-wide basebands centred at 216, 218, 231 and 233 GHz, each with 128 spectral channels of width 16 MHz (20 kms$^{-1}$)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Compact array format  
  > "The observations were taken with a compact array format with baselines between 15-349 m." (2 Observations)
- baselines: 15-349 m (32 and 430 AU scales)  
  > "baselines between 15-349 m" (2 Observations)
- angular resolution: 1.7" x 1.3" synthesised beam  
  > "The resulting synthesised beam has a size 1.7$''$$\times$1.3$''$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 16 uJy/beam RMS  
  > "the RMS is measured to be $\sigma=16$ $\mu$Jy/beam" (2 Observations)
- time on source: 2.8 hours  
  > "The total on source time is 2.8 hours." (2 Observations)
- observing dates: 3-18 January 2015, 5 observations  
  > "The data are comprised of 5 separate observations taken between 3rd and 18th January 2015." (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- External data: PHOENIX stellar model fit used to extrapolate stellar flux of 17 uJy at 1.3 mm  
  > "we extrapolate the PHOENIX model (cite: brott05) fit of (cite: matthews14) to give a stellar flux density at this wavelength of $F_*=$17 $\mu$Jy" (3 Modelling) [from (cite: matthews14)]
- External data: Planet orbital astrometric fit used for chaotic zone estimates  
  > "The latest astrometric fit to all the observations of the planets is given in (cite: zurlo16)." (4.2 Interaction between planets and the disc) [from (cite: zurlo16)]

## Processing

### Calibration

- pipeline or manual: Standard observatory calibration  
  > "The data was calibrated using standard observatory calibration in `CASA` version 4.3.1" (2 Observations)
- casa version: CASA 4.3.1  
  > "standard observatory calibration in `CASA` version 4.3.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (obs 1-4), Neptune (obs 5); J2253+1608 phase  
  > "Uranus was used as a flux calibrator for observations 1-4 and Neptune was used for observation 5." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN with zero iterations (dirty image), multi-frequency synthesis  
  > "These were created using `CLEAN` with zero iterations and a natural weighting, taking advantage of the multi-frequency synthesis." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "These were created using `CLEAN` with zero iterations and a natural weighting" (2 Observations)
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
- final beam: 1.7" x 1.3"  
  > "The resulting synthesised beam has a size 1.7$''$$\times$1.3$''$." (2 Observations)
- final rms: 16 uJy/beam, measured in dirty image offset +90" in declination  
  > "the RMS was measured by creating a dirty image pointing slightly away from the target (+90$''$ in declination)" (2 Observations)

### Not stated but needed to reproduce (our reading)

- Image size and cell size of the dirty image
- Pixel-wise treatment of stellar position offset and whether it was fitted
- MCMC burn-in and convergence tests
- Bounds of uniform priors
- Whether observation 2 was the only data flagged beyond the standard pipeline

## Analysis recipe

1. **Make dirty continuum image and measure noise**: CLEAN with zero iterations, natural weighting, MFS; RMS from offset dirty image  
  > "These were created using `CLEAN` with zero iterations and a natural weighting, taking advantage of the multi-frequency synthesis." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric ring model in image plane**: Line-of-sight integrator ring model, attenuated by primary beam, convolved with dirty beam, chi^2 compared with dirty image  
  > "It is then convolved with the dirty beam (the Fourier transform of the sampling function) and the likelihood ($-\chi^2/2$) is then calculated by comparison with the dirty image." (3 Modelling)
   - software: emcee
   - parameter: 120 walkers, 2500 timesteps; 6 free parameters (Rin, Rout, gamma, F_nu, I, Omega)  
  > "which is run with 120 walkers and for 2500 timesteps" (3 Modelling)
   - parameter: sigma scaled by square root of beam area in pixels for correlated noise  
  > "the value of $\sigma$ used in the $\chi^2$ is modified by a noise correlation ratio given by the square root of the beam area in pixels" (3 Modelling)
   - assumption: Blackbody grains; star at offset peak; stellar flux 17 uJy; sharp edges, single power law  
  > "For the radial temperature profile we treat the grains as blackbodies." (3 Modelling)
   - fitting: emcee, uniform priors in Rin, Rout, gamma, ln(F_nu), cos(I), Omega  
  > "they are uniform in $R_{\rm{in}}$, $R_{\rm{out}}$, $\gamma$, $\ln(F_{\nu})$, $\cos(I)$ and $\Omega$" (3 Modelling)
   - validation: Residual RMS equals measured noise; residuals smooth apart from three ~3 sigma features  
  > "The residuals are otherwise smooth and the RMS in the residual image is equivalent to the noise measured in section [2](#sobs)." (3 Modelling)
3. **Compare inner edge with planet-b chaotic zone**: Analytic chaotic zone width using equations (9) and (10) of Pearce & Wyatt 2014  
  > "using equations (9) and (10) of (cite: pearce14), which gives the highest estimate of the width of the chaotic zone" (4.2 Interaction between planets and the disc)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: Calibration and CLEAN dirty imaging  
  > "standard observatory calibration in `CASA` version 4.3.1" (2 Observations)
- **emcee** : MCMC fitting of disc model  
  > "an MCMC routine is run making use of `emcee` (cite: foreman13)" (3 Modelling)
- **Astropy** : acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy13)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner radius | 145 | +12/-12 | AU | 2 | $145^{+12}_{-12}$ |
| Outer radius | 429 | +37/-32 | AU | 2 | $429^{+37}_{-32}$ AU |
| Optical depth power-law index gamma | -1.0 | +0.4/-0.4 | dimensionless | 2 | $-1.0^{+0.4}_{-0.4}$ |
| Total disc flux density at 1.3 mm | 2.8 | +0.5/-0.4 | mJy | 2 | $2.8^{+0.5}_{-0.4}$ |
| Inclination | 40 | +5/-6 | deg | 2 | inclination of $40^{+5}_{-6}{{\ensuremath{^\circ}}}$ |
| Position angle | 51 | +8/-8 | deg | 2 | position angle of $51^{+8}_{-8}{{\ensuremath{^\circ}}}$ |
| Image RMS | 16 | not stated | uJy/beam | 1 | the RMS is measured to be $\sigma=16$ $\mu$Jy/beam |

## Qualitative findings

- CO J=2-1 emission detected consistent with line-of-sight cloud HLCG 92-35, clump ~12" SW of star  
  > "Our ALMA observations therefore confirm the presence of CO emission along the line of sight to HR8799 originating from the HLCG 92-35 cloud." (2 Observations)

## Claim tuples

- H: Is the planetesimal belt inner edge consistent with far-IR models and with planet b sculpting? | E: MCMC fit of ring model to ALMA band 6 dirty image | R: Rin=145 AU, Rout=429 AU | F: Inner edge agrees with SMA but not far-IR models, and is too far out for planet b's chaotic zone, requiring varied orbit or an extra planet | **supported**
- H: Does the belt orientation match that of the small grains? | E: Compare fit I and Omega with Herschel results | R: I=40, PA=51 vs 26 and 64 | F: Consistent at 95% level; possible real difference not established | **partially**

## Reasoning

- Why this data: Infrared data cannot distinguish planetesimal belt emission from halo grains; sub-mm traces only the belt  
  > "sub-mm observations, which only detect dust in the planetesimal belt" (Conclusions)
- Why this method: Image-plane modelling is more efficient while retaining accuracy  
  > "it is more efficient, whilst still retaining accuracy, to work in the image plane" (3 Modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Sharp-edged single power law assumed; low S/N does not warrant more detailed radial profiles  
  > "The low level of signal-to-noise in the data does not warrant exploration of more detailed radial distributions" (4.2 Interaction between planets and the disc)
- Caveat (inferred, ours): Image-plane fit to a dirty image with correlated noise is approximate versus visibility fitting
- Caveat (inferred, ours): Background CO cloud emission may bias the continuum fit
- Caveat (inferred, ours): Star position assumed from a marginal peak
- Caveat (inferred, ours): Only 4 of 5 executions used

## Reproducibility

- Data public (paper): ALMA cycle 1 project cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00482.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Pixel/image size
- Missing: Model code is not released
- Missing: Prior bounds and burn-in
- Data volume (inferred): ~20-50 GB raw for 5 compact-array executions
- Score (inferred): 3/5, Simple approach with named software and numeric results, but model code and several settings are not given.
- Rediscovery candidate: no, Model code is custom and unreleased, and key imaging and prior settings are missing, so the fit cannot be redone exactly.

## Links

- Method: Wyatt et al. 1999 (cite: wyatt99) (Line-of-sight integrator disc model)
- Method: Pearce & Wyatt 2014 (cite: pearce14) (Chaotic zone width equations)
- Companion: Matthews et al. 2014 (cite: matthews14) (Herschel disc model for comparison)
- Companion: Hughes et al. 2011 (cite: hughes11) (SMA observations of the disc)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 36,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
