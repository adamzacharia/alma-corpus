# STATCONT: A statistical continuum level determination method for line-rich sources

`2018A&A...609A.101S` | Astronomy and Astrophysics 2018 | first author: Sánchez-Monge, Á. | arXiv: 1710.02419 | DOI: 10.1051/0004-6361/201730425

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: astrochemistry, star_formation, instrumentation
- Question: How can the continuum level of line-rich spectra and datacubes be determined automatically and accurately with a statistical method?  
  > "In this paper we present `STATCONT`, a python-based tool, that automatically determines the continuum level of line-rich sources in a statistical way." (Introduction)
- Target **Sgr B2(N)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **G29.96-0.02**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00332.S, 2013.1.00489.S
- bands: ALMA band 6  
  > "observed different frequency ranges of the ALMA band 6." (3 Application to real datasets)
- frequencies and spectral setup: Sgr B2(N): 211-213 GHz, 1875 MHz effective bandwidth, 3480 channels, 0.7 km/s; G29.96: 256 MHz bandwidth centered at 231.85 GHz, 0.6 km/s  
  > "The selected spectral window of Sgr B2(N) covers the frequency range 211 GHz to 213 GHz, with an effective bandwidth of 1875 MHz and 3480 channels" (3 Application to real datasets)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Simulation/model as data: Synthetic spectra (five types, then 750 spectra with noise 1, 3, 5 K) and a synthetic datacube generated with XCLASS, continuum 50 K  
  > "All these spectra have been produced with the XCLASS[^1] software package" (2 Determination of the continuum level); "The final statistically significant sample consists of 750 different synthetic spectra." (2.2 Statistical comparison of continuum methods)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
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
- continuum subtraction: Classical approach: line-free channels identified in average spectrum around position A; compared to c-SCM continuum  
  > "are produced after identifying line-free channels in an average spectrum extracted around position A" (3 Application to real datasets)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details of the ALMA datasets  
  > "Details of the observations can be found in (cite: Cesaroni2017), and in (cite: SanchezMonge2017)." (3 Application to real datasets) [from (cite: Cesaroni2017), (cite: SanchezMonge2017)]

### Not stated but needed to reproduce (our reading)

- Sigma-clipping alpha value, tolerance and iteration limit
- Calibration and imaging parameters of the ALMA cubes (beam, rms, CASA version)
- Line-free channel ranges used for the classical maps
- Random seeds and XCLASS parameters for the synthetic spectra
- Positions of A and B in the real data

## Analysis recipe

1. **Generate synthetic spectra**: XCLASS spectra with 50 K continuum, emission/absorption components, Gaussian noise; 50 per group x 5 groups x 3 noise levels  
  > "we randomly modify the number of molecules and components as well as the molecular abundances, temperatures and velocities of each component." (2.2 Statistical comparison of continuum methods)
   - software: XCLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare continuum estimators**: Maximum, mean, median, percentiles, Gaussian, KDE maximum and sigma-clipping applied to intensity distributions and scored by discrepancy from 50 K  
  > "We determine the continuum level for all the spectra using all the methods described in Section" (2.2 Statistical comparison of continuum methods)
   - software: STATCONT
   - parameter: Histogram bin size set by rms noise; KDE Gaussian kernel with Silverman's rule  
  > "In `STATCONT` the size of the bins is defined by the rms noise level of the observations" (2.1 Continuum level in spectral data: statistical methods)
   - fitting: _not stated_
   - validation: Success rate vs discrepancy from known continuum  
  > "we list the success rate determined as the number (in percentage) of synthetic spectra for which the continuum level has been determined with a certain level of accuracy" (Statistical comparison of continuum methods)
3. **Correct sigma-clipping (c-SCM)**: Add or subtract sigma_SCM (+1, +0.5, 0, -0.5, -1) based on fractions of emission/absorption channels relative to oSCL±rms (33% and 25% thresholds)  
  > "the continuum emission level is corrected by adding or subtracting the value of the uncertainty to the continuum level" (2.4 Corrected sigma-clipping continuum level)
   - software: STATCONT
   - fitting: _not stated_
   - validation: Tested on 750 synthetic spectra  
  > "The final statistically significant sample consists of 750 different synthetic spectra." (Statistical comparison of continuum methods)
4. **Apply to ALMA cubes**: Pixel-by-pixel c-SCM to produce continuum, noise and line cubes; compare with classical line-free-channel continuum  
  > "We apply the c-SCM in `STATCONT` to determine the continuum level in real observational data." (3 Application to real datasets)
   - software: STATCONT
   - fitting: _not stated_
   - validation: Compared with classical continuum maps  
  > "In the top-right panel, we compare with the continuum map that is created after searching for line-free channels following the classical approach." (Application to real datasets)

## Software

- **STATCONT** : Continuum level determination in spectra and datacubes  
  > "a python-based tool, that automatically determines the continuum level of line-rich sources" (Introduction)
- **XCLASS** : Synthetic spectra and datacube  
  > "All these spectra have been produced with the XCLASS[^1] software package" (2 Determination of the continuum level)
- **GILDAS/CLASS** : Zeroth-order baseline fits to line-free channels; GREG for figures  
  > "fit a 0$^\mathrm{th}$-order polynomial baseline to the line-free channels" (2.3 Effect of noise)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| c-SCM success rate (discrepancy <5%) | 87.9 | not stated | percent | 3 | *(L)* c-SCM / 50.19 / 50.22 / $\phantom{0}$8.2 / 48.8             / 87.9 |
| c-SCM success rate (discrepancy <1%) | 48.8 | not stated | percent | 3 | *(L)* c-SCM / 50.19 / 50.22 / $\phantom{0}$8.2 / 48.8             / 87.9 |
| SCM success rate (discrepancy <5%) | 77.1 | not stated | percent | 2 | *(K)* SCM                      / 50.60 / 50.49  / $\phantom{0}$8.4 / 33.8             / 77.1 |

## Qualitative findings

- Sigma-clipping is the most accurate and gives an uncertainty; correction makes it successful in >90% of cases when >10% of channels are line-free  
  > "If the spectrum to be analyzed contains more than 10% of line-free channels, c-SCM is accurate in the determination of the continuum level." (Summary)

## Claim tuples

- H: A statistical sigma-clipping method can recover the continuum of line-rich spectra | E: Compare 12 estimators on 750 synthetic spectra | R: c-SCM discrepancy <5% in 87.9% of cases | F: c-SCM is the best default method | **supported**
- H: STATCONT works on real ALMA data | E: Apply to Sgr B2(N) and G29.96-0.02 cubes and compare to classical continuum maps | R: Uncertainties of about 1-5%, up to 10% in chemically rich positions; avoids line contamination seen in classical map | F: STATCONT gives continuum maps without line structure | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Mean, median, percentile, Gaussian, KDE and maximum methods were less accurate or depended on binning  
  > "The mean, median and Gaussian methods have a large standard deviation when applied to the whole spectral histogram, i.e., broad distributions resulting in low success rates" (Statistical comparison of continuum methods)
- How they decided it was enough: _not stated_
- Limitation (authors): c-SCM assumes a flat continuum and can fail with <10% line-free channels for complex spectra  
  > "A current limitation of `STATCONT` is that it assumes that the continuum level, or baseline of the spectrum, is flat" (Summary)
- Caveat (inferred, ours): Real-data validation is only qualitative, with no ground truth
- Caveat (inferred, ours): Synthetic spectra from one code may not represent real line forests
- Caveat (inferred, ours): Correction thresholds look empirical and tuned on the test set

## Reproducibility

- Data public (paper): Code freely available; ALMA data acknowledged by project code  
  > "The code is freely available for download[^4] from GitHub or as a `STATCONT.tar.gz` file." (5 Description of the STATCONT procedures)
- Products in archive: _not stated_
- Code: STATCONT available from GitHub and the author's webpage  
  > "The code is freely available for download[^4] from GitHub or as a `STATCONT.tar.gz` file." (5 Description of the STATCONT procedures)
- Missing: Synthetic spectra generation parameters
- Missing: Sigma-clipping parameters
- Missing: Calibrated ALMA cubes
- Data volume (inferred): ~10-50 GB for two ALMA spectral windows
- Score (inferred): 3/5, Code is public and the method is described, but the synthetic generation and clipping parameters are missing.
- Rediscovery candidate: no, The synthetic test setup is not specified enough to redo, and the real-data results are not numeric.

## Links

- Method: (cite: Moeller2017) (XCLASS used for synthetic spectra)
- Companion: (cite: SanchezMonge2017) (Applies STATCONT to Sgr B2 ALMA data)
- Companion: (cite: Cesaroni2017) (Observation details of G29.96 and G31.41 data)

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 22,
  "rate": 0.324
 },
 "evidence_ok": true
}
```
