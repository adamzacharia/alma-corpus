# Solar Chromospheric Temperature Diagnostics: A Joint ALMA-Hα Analysis

`2019ApJ...881...99M` | The Astrophysical Journal 2019 | first author: Molnar, Momchil E. | arXiv: 1906.08896 | DOI: 10.3847/1538-4357/ab2ba3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How does the ALMA Band 3 brightness temperature relate to the H-alpha core width as a chromospheric temperature diagnostic, and what physical mechanism explains the relation?  
  > "we concentrate on the comparison between the brightness temperature observed in ALMA Band 3 (3 mm; 100 GHz) and the core width of the H$\alpha$ 6563 Å line" (abstract)
- Target **Plage, network and fibrils in NOAA AR 12651**: coordinates E04, N11 (solar disk)  
  > "The center of the target region was at E04, N11 at the time of the observations ($\mu = 0.96$ or heliocentric angle of 16$^{\circ}$)." (Observations); z/distance mu = 0.96 (heliocentric angle 16 deg)  
  > "The center of the target region was at E04, N11 at the time of the observations ($\mu = 0.96$ or heliocentric angle of 16$^{\circ}$)." (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01129.S
- bands: Band 3 (2.8-3.3 mm, 92-108 GHz)  
  > "The data analyzed here were obtained in Band 3 (2.8-3.3 mm, 92-108 GHz) in the interval 17:19 to 18:53 UT." (2.2 ALMA Observations and Processing)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3, max baseline 460 m nominal, 396 m actual  
  > "The ALMA data were obtained with the array in configuration C40-3 with a maximum baseline of 460 m. However, due to antenna issues, during these observations the maximum baseline was 396 m." (2.2 ALMA Observations and Processing)
- baselines: _not stated_
- angular resolution: restoring beam 1.75'' x 1.91''; ~2.0''  
  > "the restoring beam size of the ALMA image, as calculated in CLEAN, is 1.75$''$ x 1.91$''$ in the x-y directions" (2.2 ALMA Observations and Processing)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: eight intervals of ~593 s on target with 145 s phase calibrator gaps  
  > "dwelled for approximately 593 seconds on the target followed by a 145 second gap for observations of a phase calibrator." (2.2 ALMA Observations and Processing)
- observing dates: April 23, 2017, 17:19-18:53 UT  
  > "We obtained a coordinated set of observations between ALMA and the Dunn Solar Telescope (cite: 1991AdSpR..11..139D) on April 23, 2017." (2 Observations)
- pi or archival as stated: _not stated_
- Line: H I H-alpha (IBIS) (6563 Å)
- Other facility **DST/IBIS**: H-alpha, Ca II 8542, Na I D1 spectral scans  
  > "The lines were scanned with 29, 27, and 24 spectral sampling points, respectively" (2.1 DST/IBIS Observations)
- Other facility **SDO/HMI**: continuum images for IBIS alignment and magnetic field maps  
  > "using the nearest-in-time HMI continuum intensity images in order to precisely map the IBIS spectral data onto a regular, fixed spatial grid" (2.1 DST/IBIS Observations)
- Other facility **ALMA single-dish full-disk**: background emission for feathering and absolute calibration  
  > "single-dish observations that scan the full disk were taken nearly simultaneously with the interferometer array" (2.2 ALMA Observations and Processing)
- External data: Quiet-Sun central disk brightness temperature of 7300 K used for absolute calibration  
  > "the brightness temperature in the central region of the disk (diameter 190 arcsec) was equal to 7300 K, as determined by (cite: 2017SoPh..292...88W)" (2.2 ALMA Observations and Processing) [from (cite: 2017SoPh..292...88W)]
- External data: SRPM 1D atmosphere models (B to P, Q) as RH input  
  > "We chose the 1D Solar Radiation Physical Modeling (SRPM from now on) models (cite: 2011JGRD..11620108F) as input for our work." (4 Synthetic Spectral Diagnostics with RH) [from (cite: 2011JGRD..11620108F)]
- Simulation/model as data: RH synthesis from SRPM models B-P, Q and VAL C  
  > "We also included the heritage quiet Sun VAL C model for comparison (cite: 1981ApJS...45..635V)." (4 Synthetic Spectral Diagnostics with RH)

## Processing

### Calibration

- pipeline or manual: standard CASA calibration, then self-calibration per interval  
  > "After applying the standard radio interferometer data calibration procedures using CASA (cite: 2012ASPC..461..849P)" (2.2 ALMA Observations and Processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: absolute temperature accurate to 2-5%  
  > "provides an absolute temperature accurate to 2-5% (cite: 2017SoPh..292...88W)" (2.2 ALMA Observations and Processing)
- self calibration: per 10-minute interval, average clean image used to remove phase variations in individual images  
  > "For each 10 minutes observation interval, an average (clean) image is generated and then used to remove the random phase variations in the individual images within that observing interval." (2.2 ALMA Observations and Processing)

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
- array combination: feathering with full-disk single-dish image in CASA  
  > "Through the feathering process provided in CASA, we combine the two datasets covering the full range of spatial scales." (2.2 ALMA Observations and Processing)
- smoothing: _not stated_
- final beam: 1.75'' x 1.91''  
  > "the restoring beam size of the ALMA image, as calculated in CLEAN, is 1.75$''$ x 1.91$''$ in the x-y directions" (2.2 ALMA Observations and Processing)
- final rms: _not stated_

### Inherited from earlier work

- Absolute calibration and single-dish full-disk data  
  > "was equal to 7300 K, as determined by (cite: 2017SoPh..292...88W)" (2.2 ALMA Observations and Processing) [from (cite: 2017SoPh..292...88W)]
- H-alpha core width measurement technique  
  > "We calculated the width of the line core following the technique described in (cite: 2009A&A...503..577C)" (3.1 IBIS Line Widths) [from (cite: 2009A&A...503..577C)]

### Not stated but needed to reproduce (our reading)

- tclean/CLEAN parameters (weighting, robust, cell, niter) for ALMA images
- Self-calibration solution intervals and reference model details
- Feather parameters and single-dish image scaling details
- IBIS calibration and HMI destretch parameters
- RH setup details beyond a 4-level hydrogen atom
- Alignment procedure between ALMA and IBIS
- CASA version

## Analysis recipe

1. **Calibrate and self-calibrate ALMA data, feather with full-disk**: Standard CASA calibration, per-interval self-calibration, feathering with single-dish, normalised to 7300 K  
  > "we apply a self-calibration technique." (2.2 ALMA Observations and Processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure H-alpha core width**: Width of line profile at half line depth, with depth defined relative to intensity at ±1.0 Å  
  > "we measure the separation of the line profile wings at half of the line depth, defined as the difference between the line minimum and the intensity at $\pm$ 1.0 Å from the core position" (3.1 IBIS Line Widths)
   - fitting: second-order polynomial to line core for minimum  
  > "were determined through fitting of a second-order polynomial to the line core" (3.1 IBIS Line Widths)
   - validation: width errors about 0.005 Å  
  > "the errors in the line width were determined to be about 0.005 Å" (3.1 IBIS Line Widths)
3. **Match resolution, align and correlate**: Convolve IBIS with elliptical Gaussian 1.95'' x 2.03'', bin ALMA in time by 8 maps, align, 2D histogram, Pearson r and orthogonal distance regression  
  > "Because of the scatter present in both measurements, we perform an orthogonal distance regression (cite: 1990ApJ...364..104I) to find the best linear fit between the two parameters." (3.3 Comparison)
   - fitting: _not stated_
   - validation: _not stated_
4. **Forward model with RH**: Synthesize H-alpha and 3 mm intensity from SRPM and VAL C models with 4-level hydrogen with PRD for Ly-alpha, Ly-beta, H-alpha; compare to observed correlation  
  > "The RH calculations were done using a 4-level (including continuum) hydrogen atom with the Ly-alpha, Ly-beta and Balmer-alpha transitions treated under partial redistribution (PRD)" (4 Synthetic Spectral Diagnostics with RH)
   - software: RH
   - assumption: 1D hydrostatic semi-empirical atmospheres; mm radiation in Rayleigh-Jeans approximation  
  > "The emergent millimetric radiation was calculated from the synthetic intensity under the Rayleigh-Jeans approximation" (4 Synthetic Spectral Diagnostics with RH)
   - fitting: _not stated_
   - validation: model points compared with observed correlation  
  > "coincide well with the observational data for models B to P" (4 Synthetic Spectral Diagnostics with RH)

## Software

- **CASA** : ALMA calibration, imaging (CLEAN), feathering  
  > "Through the feathering process provided in CASA, we combine the two datasets covering the full range of spatial scales." (2.2 ALMA Observations and Processing)
- **RH** : forward radiative transfer synthesis  
  > "we utilized the RH code (cite: 2001ApJ...557..389U) to synthesize observables" (4 Synthetic Spectral Diagnostics with RH)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pearson correlation between T_B and H-alpha width | 0.84 | not stated | dimensionless | 3 | with a Pearson correlation coefficient of 0.84 |
| ODR fit: H-alpha width vs T | 0.533 + 6.12e-5 T | not stated | Å (T in K) | 3 | The best fit equation is $0.533 + 6.12\times10^{-5}\;T$ |
| Mean T_B of FOV | ~8600 | not stated | K | 1 | The overall average $T_B$ for our field is $\sim$ 8600 K |
| Thermal broadening for 6000 to 12000 K | 0.025 | not stated | Å | 3 | would only be expected to increase the line width by 0.025 Å |

## Qualitative findings

- Bright fibril-like structures are seen in on-disk ALMA images, contrary to Rutten (2017) prediction of dark fibrils  
  > "we identify them as bright (hence hot) features, rather than dark, strong fibrils" (3.2 ALMA Band 3 Intensity)

## Claim tuples

- H: Is ALMA 3 mm T_B correlated with H-alpha core width? | E: Pixelwise comparison of resolution-matched maps | R: Pearson r = 0.84; linear fit | F: Strong correlation; width is a temperature proxy over 6500-12000 K | **supported**
- H: Is H-alpha width broadening thermal Doppler? | E: Compare ALMA T range with width variation | R: 0.025 Å expected vs ~0.3 Å observed | F: Thermal broadening cannot explain it | **supported**
- H: A shared dependence on n=2 hydrogen population drives the correlation | E: RH synthesis on SRPM models | R: Models B to P reproduce the trend; n2 rises with hotter models | F: Both diagnostics depend on n2 via Ly-alpha flux | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: 3D MHD models (BIFROST) not used because they do not reproduce correct chromospheric line widths  
  > "they do not reproduce the correct width of chromospheric lines" (4 Synthetic Spectral Diagnostics with RH)
- How they decided it was enough: _not stated_
- Limitation (authors): 1D hydrostatic models and 1D radiative transfer for H-alpha  
  > "The SRPM models have shortcomings as they are 1D, hydro-static, semi-empirical models" (4 Synthetic Spectral Diagnostics with RH)
- Caveat (inferred, ours): Mechanism is argued from a few 1D models, not tested directly
- Caveat (inferred, ours): Single field, single day, near disk center
- Caveat (inferred, ours): Alignment with ALMA tuned on the same images used for correlation
- Caveat (inferred, ours): No uncertainties on fit parameters

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; public availability not stated  
  > "This paper makes use of the following ALMA data: ADS/NRAO.ALMA#2016.1.01129.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: IBIS data access
- Missing: CLEAN and self-cal parameters
- Missing: Single-dish data details
- Data volume (inferred): tens to hundreds of GB (ALMA solar time series) plus IBIS data
- Score (inferred): 3/5, Concise processing description with missing parameters; IBIS data needed.
- Rediscovery candidate: no, Requires non-ALMA IBIS data and underspecified solar ALMA processing.

## Links

- Method: (cite: 2009A&A...503..577C) (H-alpha width technique)
- Method: (cite: 2017SoPh..292...88W) (single-dish full-disk and absolute calibration)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 35,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
