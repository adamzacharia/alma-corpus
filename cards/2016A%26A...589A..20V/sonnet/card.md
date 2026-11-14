# The correct estimate of the probability of false detection of the matched filter in weak-signal detection problems

`2016A&A...589A..20V` | Astronomy and Astrophysics 2016 | first author: Vio, R. | arXiv: 1602.02392 | DOI: 10.1051/0004-6361/201527463

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies, instrumentation
- Question: How to correctly estimate the probability of false detection when a matched filter is applied to data where the signal position is unknown (peak detection in Gaussian noise)  
  > "The correct method to accurately compute this quantity is also presented." (Introduction)
- Target **BDF-3299 (Ly-alpha emitter)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00719.S
- bands: Band 6  
  > "a deep map taken with ALMA in Band 6" (3 Application to an ALMA observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms 7.8 uJy/beam  
  > "the reached rms value is $7.8 \mu$ Jy/beam" (3 Application to an ALMA observation)
- time on source: roughly 300 minutes  
  > "The total on-source integration time was roughly $300$ minutes" (3 Application to an ALMA observation)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: ALMA Band 6 map of BDF-3299 (central part), provided before publication  
  > "The authors thank Stefano Carniani and Roberto Maiolino for providing the ALMA data before publication" (Acknowledgements) [from Carniani et al. 2015 (cite: car15); Maiolino et al. 2015 (cite: mai15)]
- External data: Analytical PDF of peaks of Gaussian isotropic random fields and expected number of peaks  
  > "provide the explicit PDF of the values $z$ of the peaks in a $N$-dimensional Gaussian isotropic random field of zero-mean and unit-variance" (2.1.3) [from Cheng & Schwartzman 2015a,b (cite: che15a; che15b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Map not corrected for the primary beam; calibration details not given  
  > "The map has been not corrected for the primary beam, and therefore the resulting noise is uniform across the observed area." (3 Application to an ALMA observation)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: 256 x 256 pixels (central part of map)  
  > "which is shown in Figure 4(a) as a $256 \times 256$ pixel map" (3 Application to an ALMA observation)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied  
  > "The map has been not corrected for the primary beam" (3 Application to an ALMA observation)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 7.8 uJy/beam  
  > "the reached rms value is $7.8 \mu$ Jy/beam" (3 Application to an ALMA observation)

### Inherited from earlier work

- Map data and area from Maiolino et al. 2015; only central part analysed  
  > "We are analysing here only the central part of the map shown in (cite: mai15)" (3 Application to an ALMA observation) [from (cite: mai15)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, cell size, CLEAN settings) of the map
- Exact map coordinates, beam and pixel scale
- Procedure for source removal and spline fill (region sizes)
- Peak-finding definition and fitting details for the ACF model (fit range, parameter values b and c)
- Whether the map is the archive product or a custom reduction

## Analysis recipe

1. **remove bright sources and standardize map**: Remove two bright sources, fill area with 2D cubic spline interpolation, standardize to zero mean and unit variance  
  > "when this is removed and the corresponding area filled with an interpolating two-dimensional cubic spline, another bright source becomes visible." (3 Application to an ALMA observation)
   - fitting: _not stated_
   - validation: Pixel histogram compared to Gaussian PDF; comparison with phase-randomized Gaussian random field  
  > "the histogram of the pixel values is compared to the standard Gaussian probability density function" (3 Application to an ALMA observation)
2. **fit noise correlation function**: Fit two-point correlation function with model rho(r)=b^{-ln(1+c r^2)}, giving kappa  
  > "is able to provide a very good fit to the two-point correlation function of the map." (3 Application to an ALMA observation)
   - assumption: Noise approximately isotropic Gaussian field; MF reduces to simple thresholding of peaks  
  > "this condition is approximately satisfied." (3 Application to an ALMA observation)
   - fitting: _not stated_
   - validation: Predicted peak PDF agrees with histogram of peak values  
  > "Its agreement with the histogram of the peak values is good." (3 Application to an ALMA observation)
3. **compute false-detection probability of highest peak**: Use peak PDF Psi(u) (Cheng & Schwartzman) instead of Gaussian Phi(u); compare expected number of peaks with observed  
  > "the expected number of peaks that are equal or randomly exceed $z_{\rm max}$ is $2.62 \times 10^{-3} \times 806 \approx 2$" (3 Application to an ALMA observation)
   - fitting: _not stated_
   - validation: Expected vs observed peak number 822 vs 806  
  > "The result is $822$ whereas the number effectively observed is $806$." (3 Application to an ALMA observation)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| kappa of map noise | 0.95 | not stated | dimensionless | 2 | in the present case it results in $\kappa= 0.95$ |
| Expected number of peaks | 822 | not stated | peaks | 3 | The result is $822$ whereas the number effectively observed is $806$. |
| Highest peak z_max | 3.68 | not stated | dimensionless (sigma) | 3 | the value of the highest peak is $z_{\rm max} = 3.68$ |
| Psi(z_max) | 2.62e-3 | not stated | dimensionless | 3 | $\Psi(z_{\rm max}) \approx 2.62 \times 10^{-3}$ |

## Qualitative findings

- No point sources beyond the two bright ones can be claimed; remaining peaks are compatible with noise  
  > "it is not possible to claim the presence of point-sources in addition to the two bright ones detected beforehand" (3 Application to an ALMA observation)

## Claim tuples

- H: Gaussian-based false-alarm probability is correct for peaks in matched-filtered noise | E: Compare Phi(u) with peak PDF Psi(u) and apply to ALMA map | R: At u=4 Phi gives about 30 times smaller probability than Psi; z_max=3.68 expects ~2 noise peaks vs ~0.1 under Gaussian | F: The standard approach severely underestimates false-detection probability and can give spurious detections | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Equations strictly apply to continuous fields; isotropy only approximate; deconvolution is problematic  
  > "Strictly speaking, the equations above apply only to continuous random fields." (2.1.3)
- Caveat (inferred, ours): Single map used as test; no simulation-based validation of false-alarm rates shown
- Caveat (inferred, ours): Fitted noise model chosen ad hoc
- Caveat (inferred, ours): Interferometric noise correlation after deconvolution may not be stationary

## Reproducibility

- Data public (paper): ALMA data cited with project code; provided by authors before publication  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00719.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Map imaging parameters
- Missing: ACF fit details
- Missing: Peak detection definition
- Data volume (inferred): ~10-50 GB raw if reimaging; small if a final map is used
- Score (inferred): 3/5, Method is analytic and equations are given, but the map processing and fit details are missing.
- Rediscovery candidate: no, Imaging recipe and fit details are missing, and the result is a methodological illustration.

## Links

- Method: Cheng & Schwartzman 2015a,b (cite: che15a; che15b) (Peak PDF and peak count formulas)
- Companion: Maiolino et al. 2015 (cite: mai15) (Original ALMA observation of BDF-3299)

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
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
  "facts": 58,
  "stated": 21,
  "rate": 0.362
 },
 "evidence_ok": true
}
```
