# Misaligned protoplanetary disks in a young binary star system

`2014Natur.511..567J` | Nature 2014 | first author: Jensen, Eric L. N. | arXiv: 1407.8211 | DOI: 10.1038/nature13521

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the three-dimensional misalignment between the protoplanetary disks around the two stars of the young binary HK Tau?  
  > "Here we report that the protoplanetary disks in the young binary system HK Tau are misaligned by 60°–68°" (abstract)
- Target **HK Tau (A and B)**: coordinates _not stated_; z/distance 161 pc  
  > "a young binary system with a projected separation of 2.4 arcsec [15], which is 386 AU at the 161 parsec distance of this part of the Taurus clouds [16]" (main text); distance from Torres et al. 2009 VLBA (ref 16)  
  > "a young binary system with a projected separation of 2.4 arcsec [15], which is 386 AU at the 161 parsec distance of this part of the Taurus clouds [16]" (main text)

## Data provenance

- ALMA projects: 2011.0.00150.S
- bands: Band 6 (CO 2-1, 230.5 GHz) and Band 7 (CO 3-2, 345.8 GHz)  
  > "In Band 6, one of the correlator basebands was set to cover the CO (2–1) transition at 230.5 GHz, while in Band 7, one baseband covered CO (3–2) at 345.8 GHz." (Methods)
- frequencies and spectral setup: four basebands, 1.875 GHz each, 488 kHz channels; 1.3 and 0.85 km/s resolution  
  > "each of the four basebands covering a total bandwidth of 1.875 GHz with a channel spacing of 488 kHz." (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.06" x 0.73" (Band 6); 0.69" x 0.51" (Band 7)  
  > "These settings resulted in a clean beam size of 1.06” x 0.73” in Band 6 and 0.69” x 0.51” in Band 7." (Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 17 Nov 2012 (Band 6, 27 antennas); 16 Nov 2012 (Band 7, 28 antennas)  
  > "Band 6 observations were taken on 17 Nov 2012 with 27 antennas and Band 7 observations on 16 Nov 2012 with 28 antennas." (Methods)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.5 GHz)
- Line: CO 3-2 (345.8 GHz)
- External data: HK Tau B disk inclination 85°±1° and PA 42° from scattered-light imaging  
  > "we adopt from that work [18] an inclination _i_ = 85°±1° and position angle _PA_ = 42°." (main text) [from McCabe et al. 2011 (cite: 18)]

## Processing

### Calibration

- pipeline or manual: CASA with NRAO ALMA center scripts  
  > "We calibrated the data for each band separately using the _CASA_ software and scripts provided by the NRAO ALMA center." (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, 2012 flux models; zero-spacing flux 8.54 Jy at 230 GHz and 19.45 Jy at 345 GHz  
  > "The absolute flux calibration used Callisto and the 2012 flux models, which resulted in a zero spacing flux of 8.54 Jy at 230 GHz and 19.45 Jy at 345 GHz." (Methods)
- flux scale uncertainty: _not stated_
- self calibration: phase-only, using HK Tau continuum, data averaged to a single point  
  > "we applied a phaseQonly selfQ calibration using HK Tau as the reference." (Methods)

### Imaging

- task: CLEAN in CASA  
  > "We generated continuum and CO images using the CLEAN task within _CASA_, with a robust beam weighting of –1.0." (Methods)
- deconvolver: _not stated_
- weighting robust: robust = -1.0  
  > "with a robust beam weighting of –1.0" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: not subtracted  
  > "The continuum emission is not strong enough to substantially affect the individual channels in the CO data and thus we did not" (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.06" x 0.73" (B6); 0.69" x 0.51" (B7)  
  > "clean beam size of 1.06” x 0.73” in Band 6 and 0.69” x 0.51” in Band 7" (Methods)
- final rms: _not stated_

### Inherited from earlier work

- Disk model: self-similarity solution, specific parameterization of Rosenfeld et al. 2013  
  > "we adopt a form for our disk model that is given by a selfQsimilarity solution for circumstellar disks [33] and use the specific parameterization of ref 34." (Methods) [from Hartmann et al. 1998 (cite: 33); Rosenfeld et al. 2013 (cite: 34)]
- HK Tau B PA and inclination adopted from scattered-light work  
  > "we adopt from that work [18] an inclination _i_ = 85°±1° and position angle _PA_ = 42°." (main text) [from McCabe et al. 2011 (cite: 18)]

### Not stated but needed to reproduce (our reading)

- MCMC prior ranges for the disk parameters
- CASA version and clean parameters (image size, cell, niter, threshold)
- Self-calibration solution interval details
- Fixed positions of components (coordinates)
- Model grid/photon settings in RADMC-3D, inner radius, CO abundance treatment details
- Gas opacity/line broadening assumptions

## Analysis recipe

1. **Calibrate and image data**: Standard CASA calibration, phase-only self-cal, CLEAN with robust -1  
  > "We generated continuum and CO images using the CLEAN task within _CASA_, with a robust beam weighting of –1.0." (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Preliminary image-plane disk model fits for each disk**: RADMC-3D model images sampled with the observed uv coverage in CASA, cleaned identically, chi2 versus data, with MCMC  
  > "we find the model parameters that provide the best fits for the A and B disks in the image plane." (Methods)
   - software: RADMC-3D, CASA, emcee
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
3. **uv-plane MCMC fits of disk orientation**: Vary 8 parameters of one disk at a time while holding the other fixed; compare model visibilities to data binned to 0.85 km/s, excluding 3 absorbed channels; 10 channels used  
  > "we vary parameters for only one disk at a time." (Methods)
   - software: emcee, RADMC-3D, CASA
   - parameter: 30 walkers, at least 500 steps, first 150 discarded as burn-in; flat priors except sin i prior for inclination  
  > "In each chain, the ensemble had 30 “walkers” and ran for at least 500 steps." (Methods)
   - fitting: posterior = exp(-chi2/2) times prior; affine-invariant ensemble sampler (emcee)  
  > "We evaluate the posterior probability of each model as exp(–χ [2] /2) times the prior probability." (Methods)
   - validation: Several chains from different starts were consistent and were combined  
  > "Because the results from different chains were consistent with each other, we combined them to produce our final parameter estimates." (Methods)
4. **Derive angle between disk angular momentum vectors**: Spherical trigonometry on PA and i posteriors, with HK Tau B fixed to scattered-light values; median and 68.3% credible interval  
  > "We take the median of the posterior distribution as the most probable value" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, CLEAN imaging, sampling model on uv coverage  
  > "We calibrated the data for each band separately using the _CASA_ software" (Methods)
- **RADMC-3D** 0.35: model disk radiative transfer  
  > "Monte Carlo radiation transfer code _RADMC)3D_ version 0.35" (Methods)
- **emcee** : MCMC sampling  
  > "We use the Python code _emcee_ [39], which implements an affineQinvariant ensemble sampler [40]" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HK Tau A PA | 352 | ±3 | deg | 3 | The MCMC analysis gives _PA_ =352°±3° and inclination _i_ = 43°±5° |
| HK Tau A inclination | 43 | ±5 | deg | 3 | The MCMC analysis gives _PA_ =352°±3° and inclination _i_ = 43°±5° |
| Misalignment angle (same side / opposite sides) | 60 / 68 | ±3 | deg | 4 | the angle between the two disks’ angular momentum vectors is 60°±3° if both vectors point to the same side of the sky plane, or 68°±3° if they do not |
| HK Tau A stellar mass | 0.6 | ±0.1 | Msun | 3 | our MCMC analysis yields ! ∗ = 0.6 ± 0.1 ! Sun for HK Tau A and ! ∗ = 1.0 ± 0.1 ! Sun for HK Tau B |
| HK Tau B stellar mass | 1.0 | ±0.1 | Msun | 3 | our MCMC analysis yields ! ∗ = 0.6 ± 0.1 ! Sun for HK Tau A and ! ∗ = 1.0 ± 0.1 ! Sun for HK Tau B |

## Qualitative findings

- Both disks show Keplerian-like rotation with different orientations; the HK Tau B mass estimate is likely inaccurate  
  > "Thus, we suspect that our stellar mass estimate for HK Tau B may be inaccurate." (Methods)

## Claim tuples

- H: The two HK Tau disks are misaligned | E: MCMC fit of disk models to ALMA CO(3-2) uv data | R: Misalignment of 60°±3° or 68°±3° | F: At least one disk is inclined by ≥30° to the binary orbit; conditions for Kozai-Lidov exist at planet formation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Modest resolution, compact disks and cloud absorption prevent tight stellar mass constraints; inclination ambiguity for HK Tau A unresolved  
  > "we are unable to place tight constraints on the stellar masses." (Methods)
- Caveat (inferred, ours): Model assumes untested symmetric non-warped disks
- Caveat (inferred, ours): Fits one disk at a time assuming uncorrelated parameters
- Caveat (inferred, ours): Fixed systemic velocity and cloud-absorbed channels

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Custom modeling code not released
- Missing: MCMC priors and fixed positions not given
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and clear outline, but modeling code and several settings are missing.
- Rediscovery candidate: no, Recipe depends on custom unreleased modeling code and unspecified settings.

## Links

- Method: Rosenfeld et al. 2013 (cite: 34) (disk model parameterization)
- Companion: Akeson & Jensen 2014 (cite: 31) (survey of binaries in Taurus from which the data come)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
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
  "facts": 65,
  "stated": 29,
  "rate": 0.446
 },
 "evidence_ok": true
}
```
