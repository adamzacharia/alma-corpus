# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Implications for Spectral Line Intensity Mapping at Millimeter Wavelengths and CMB Spectral Distortions

`2016ApJ...833...73C` | The Astrophysical Journal 2016 | first author: Carilli, C. L. | arXiv: 1607.06773 | DOI: 10.3847/1538-4357/833/1/73

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, cosmology
- Question: What is the mean sky brightness temperature from line emission of distant galaxies in bands around 99 GHz and 242 GHz, measured from the ASPECS blind survey, and how does it compare to predictions and CMB spectral distortions?  
  > "We present direct estimates of the mean sky brightness temperature in observing bands around 99GHz and 242GHz due to line emission from distant galaxies." (abstract)
- Target **Hubble Ultra Deep Field (ASPECS field)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00146.S, 2013.1.00718.S
- bands: 3 mm (84–115 GHz) and 1.25 mm (212–272 GHz); mean frequencies 99 and 242 GHz  
  > "over the frequency range 84–115 GHz (3 mm), and of $\sim 0.13$ Jy km s$^{-1}$ over the frequency range 212–272 GHz." (3 ASPECS)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 3-sigma ~0.05 Jy km/s (3 mm) and ~0.13 Jy km/s (1 mm), for 200 km/s line widths  
  > "to a 3-$\sigma$ depth of $\sim 0.05$ Jy km s$^{-1}$ (assuming line widths of 200 km s$^{-1}$)" (3 ASPECS)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Table of detected lines and fluxes from the ASPECS blind search (line list used for summing)  
  > "Table 2 in Walter et al. (2016) lists the lines detected according to the blind search criteria outlined in Section 3." (4 Mean Brightness Temperatures) [from Walter et al. 2016]
- External data: Line identification, fidelity >60% selection and completeness from Decarli et al.  
  > "we only include lines with a $> 60\%$ ’fidelity’ rating." (3 ASPECS) [from Decarli et al. 2016a]

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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Survey observations, line search, completeness/fidelity tests and line identification  
  > "The ALMA spectral deep field observations (ASPECS) and results are described in Walter et al. (2016); Aravena et al. (2016a); Decarli et al. (2016)." (3 ASPECS) [from Walter et al. 2016; Aravena et al. 2016a; Decarli et al. 2016]

### Not stated but needed to reproduce (our reading)

- Individual line fluxes and uncertainties (only in Walter et al. 2016 Table 2)
- Exact ASPECS pointing coordinates and field area definition beyond 3600 arcsec^2
- Which lines passed fidelity cut per band

## Analysis recipe

1. **Sum detected line fluxes per band**: Sum total flux of all lines detected in the blind survey in each band, independent of transition and redshift  
  > "we simply sum all the lines detected in the blind survey in a give observing band, independent of what transition and redshift the line happens to be." (3 ASPECS)
   - parameter: 99 GHz: 10 lines, 2.53±0.25 Jy km/s; 242 GHz: 11 lines, 6.93±0.42 Jy km/s  
  > "the total flux for the 10 lines detected in the band is $2.53\pm 0.25$ Jy km s$^{-1}$" (4 Mean Brightness Temperatures)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert to mean brightness temperature**: Divide by total bandwidth to get mean flux density, then Rayleigh-Jeans conversion with field solid angle: T_B ~ 1360 S_nu lambda_obs^2 / Omega_f  
  > "T_B \sim
1360 ~ S_\nu ~ \lambda_{obs}^2 ~ \Omega_f^{-1} ~~ \rm K" (4 Mean Brightness Temperatures)
   - parameter: Bandwidths 31 GHz and 60 GHz; field 3600 arcsec^2  
  > "The total bandwidth is 31GHz, so the mean flux density across the band is" (4 Mean Brightness Temperatures)
   - assumption: Rayleigh-Jeans approximation; band-center frequencies 99 and 242 GHz  
  > "we adopt the mean frequencies for each band, which are 99GHz and 242GHz." (3 ASPECS)
   - fitting: _not stated_
   - validation: Compared with model predictions; cosmic variance discussed  
  > "Hence, our conclusions and uncertainties are dominated by cosmic variance and simple shot noise (Poisson statistics)." (Discussion, Limits)

## Software

- **CosmoSpec** : Computing cosmological recombination radiation shown in Fig. 3  
  > "which was computed using `CosmoSpec` (Chluba & Ali-Haïmoud, 2016)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean brightness temperature, 99 GHz band | 0.94 | 0.09 | microK | 2 | The mean surface brightness in the 99GHZ band is: $T_B = 0.94\pm 0.09\mu$K. |
| Mean brightness temperature, 242 GHz band | 0.55 | 0.033 | microK | 2 | In the 242GHz band, the mean brightness is: $T_B = 0.55\pm 0.033\mu$K. |
| Mean flux density 99 GHz band | 2.7e-5 | 0.27e-5 | Jy | 2 | $S_\nu = (2.7 \pm 0.27) \times 10^{-5}$ Jy |
| Mean flux density 242 GHz band | 9.3e-5 | 0.6e-5 | Jy | 2 | $S_\nu = (9.3 \pm 0.6) \times 10^{-5}$ Jy |

## Qualitative findings

- Measurements argue for the faint end of model predictions (~1–10 microK) and are lower limits  
  > "argue for the faint end of these predictions, although we again emphasize that these should be treated as lower limits." (5.2 Comparison)

## Claim tuples

- H: Can the mean line surface brightness be measured directly from a blind ALMA survey? | E: Summed fluxes of lines detected in ASPECS per band and converted to T_B | R: T_B = 0.94±0.09 microK (99 GHz), 0.55±0.033 microK (242 GHz) | F: Direct, model-independent lower limits on mean line brightness | **supported**
- H: Is line emission a significant foreground for CMB spectral distortions? | E: Compared measured T_B to recombination and mu distortion levels | R: Distortions of 3–30 nK are well below the mean line brightness | F: Primordial distortion extraction requires removal of integrated line emission | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small volume and few detections; cosmic variance possibly up to factor two; only detected lines summed so lower limits  
  > "our conclusions and uncertainties are dominated by cosmic variance and simple shot noise (Poisson statistics)." (5.1 Limits)
- Caveat (inferred, ours): Uncertainty ignores cosmic variance and spurious/missed lines
- Caveat (inferred, ours): Flux uncertainties assumed to add in quadrature, not stated
- Caveat (inferred, ours): Line sample includes fidelity-cut candidates with ambiguous identifications

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Line list with fluxes from Walter et al. 2016
- Data volume (inferred): Not needed if using published line list; raw ASPECS data ~100s GB
- Score (inferred): 4/5, Simple arithmetic on published line fluxes reproduces results, but depends on external table.
- Rediscovery candidate: no, The recipe is simple but relies on a table from another paper rather than on data reduction.

## Links

- Method: Walter et al. 2016 (ASPECS line search and line list)
- Method: Decarli et al. 2016 (line identification and fidelity)
- Companion: Aravena et al. 2016b (cosmic variance in the field)
- Related: ASPECS
- Related: PIXIE

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 15,
  "rate": 0.259
 },
 "evidence_ok": true
}
```
