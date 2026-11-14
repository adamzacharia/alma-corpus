# ALMA Polarimetry of Sgr A*: Probing the Accretion Flow from the Event Horizon to the Bondi Radius

`2018ApJ...868..101B` | The Astrophysical Journal 2018 | first author: Bower, Geoffrey C. | arXiv: 1810.07317 | DOI: 10.3847/1538-4357/aae983

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, milky_way_ism
- Question: What are the linear and circular polarization and Faraday rotation measure of Sgr A* at 1.3 mm, and how do they vary in time, as a probe of the accretion flow?  
  > "Millimeter polarimetry of Sgr A* probes the linearly polarized emission region on a scale of ~10 Schwarzschild radii" (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance 8.1 kpc  
  > "1 R_S \approx 10 \mu as$ for a distance of 8.1 kpc" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00764.S
- bands: Band 6 (1.3 mm), full polarization continuum  
  > "ALMA observed Sgr A* in Band 6 (1.3 mm wavelength) in full polarimetric continuum mode on three epochs" (2 Observations)
- frequencies and spectral setup: 4 SPWs, 2 GHz each, 64 channels; centers 223.96, 225.96, 239.96, 241.96 GHz  
  > "The SPW center frequencies are 223.96 GHz, 225.96 GHz, 239.96 GHz, and 241.96 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec (natural weighting)  
  > "naturally-weighted synthesized beam sizes $\sim 1$ arcsec" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~3 h in epochs 1 and 2; ~5 h over 7 h in epoch 3  
  > "Approximately three hours of observations were obtained in epochs 1 and 2." (2 Observations)
- observing dates: 3 Mar 2016, 3 May 2016, 13 Aug 2016  
  > "| 03 Mar 2016 | 0936 – 1314 |" (Table 1)
- pi or archival as stated: _not stated_
- External data: Historical RM measurements of Sgr A* (BIMA+JCMT, SMA) used in structure function  
  > "Historical Measurements of Rotation Measure" (Table 4) [from not stated]

## Processing

### Calibration

- pipeline or manual: CASA pipelines with standard a priori and calculated calibrations  
  > "Data reduction was performed in CASA using pipelines that applied standard *a priori* and calculated calibrations." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (epochs 1, 2); J1751+0939 monitoring extrapolated, 2.4 Jy (epoch 3)  
  > "Absolute flux calibration was set by observations of the moon Titan in epochs 1 and 2." (2 Observations)
- flux scale uncertainty: ~20% in epoch 3  
  > "estimated flux density of 2.4 Jy, constant across all SPWs, with an accuracy of $\sim 20\%$" (2 Observations)
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
- array combination: Baselines shorter than 50 kλ rejected  
  > "We rejected all baselines shorter than $50 k\lambda$ in order to eliminate any extended structure around Sgr A*." (2 Observations)
- smoothing: _not stated_
- final beam: ~1 arcsec natural-weighted  
  > "naturally-weighted synthesized beam sizes $\sim 1$ arcsec" (2 Observations)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- Pipeline version
- Imaging parameters (cell, size, clean settings)
- Polarization calibration procedure details (leakage, D-terms, angle)
- Time-binning and fitting weighting for RM fits
- Structure function binning

## Analysis recipe

1. **Measure Stokes I,Q,U,V**: Image-domain point-source fits per SPW and per time slice; position fixed from Stokes I for Q,U,V  
  > "Fits in the Stokes Q, U, and V domains were obtained with the point-source position fixed at the fitted peak of the Stokes I image." (2 Observations)
   - software: CASA
   - parameter: baselines <50 kλ rejected  
  > "We rejected all baselines shorter than $50 k\lambda$" (2 Observations)
   - fitting: _not stated_
   - validation: Consistent with visibility-domain point-source fits  
  > "These image-domain results are consistent with point-source fits obtained in the visibility domain." (2 Observations)
2. **Fit rotation measure**: Fit chi = chi_0 + RM lambda^2 to position angle per epoch and per time slice  
  > "$\chi = \chi_0 + RM \lambda^2,$" (3.1 Inter-Epoch)
   - software: MATLAB
   - fitting: _not stated_
   - validation: Calibrators observed in same way to set systematic limits  
  > "We use calibrator results in this Section to set limits on systematic errors on LP fraction, CP fraction, and rotation measure." (Appendix)
3. **RM variability structure function**: SF^2(tau)=<(RM(t+tau)-RM(t))^2> within epochs and over epoch-averaged plus archival RMs  
  > "We analyze variability in the RM using the structure function" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration pipelines and imaging  
  > "Data reduction was performed in CASA using pipelines" (2 Observations)
- **MATLAB** : Listed in software section; use not stated  
  > "CASA, MATLAB" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RM epoch 1 | -7.83 | 0.10 | 1e5 rad m^-2 | 2 | $-7.83 \pm  0.10$ |
| RM epoch 2 | -4.77 | 0.07 | 1e5 rad m^-2 | 2 | $-4.77 \pm  0.07$ |
| RM epoch 3 | -2.90 | 0.11 | 1e5 rad m^-2 | 2 | $-2.90 \pm  0.11$ |
| Mean circular polarization | -1.1 | 0.2 | % | 1 | We find a mean CP of $\approx -1.1 \pm 0.2$%. |
| RM change across epochs | 4.93 | not stated | 1e5 rad m^-2 | 2 | the change $\delta {\rm RM} = 4.93 \times 10^5 {\rm\ rad\ m^{-2}}$ across the three epochs is detected at a $5 \sigma$ threshold |

## Qualitative findings

- No characteristic RM variability timescale between hours and decades; RM anticorrelated with polarized flux  
  > "we do not identify any characteristic time scale between hours and decades for variability of the RM" (4.2)

## Claim tuples

- H: Mean RM of Sgr A* remains consistent with historical values | E: Three-epoch ALMA Band 6 RM fits | R: RM -7.8 to -2.9e5 rad/m^2 | F: Consistent with RIAF accretion flow, Mdot~1e-8 Msun/yr | **supported**
- H: RM varies in time | E: Compare epochs and intra-epoch fits against calibrator systematics | R: Variability from hours to months | F: First detection of RM variability | **supported**
- H: CP handedness is stable | E: Measure Stokes V | R: Mean -1.1±0.2%, same sign as earlier | F: Stable handedness | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Largest fitted RMs are suspect due to phase wrap, poor fits and calibration errors at low polarization  
  > "The largest fitted values of the RM are suspect for three reasons" (3.2)
- Caveat (inferred, ours): Only three epochs, undersampled long timescales
- Caveat (inferred, ours): Systematic limits from calibrators with possibly intrinsic RM
- Caveat (inferred, ours): Polarization leakage calibration not detailed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and exact polarization calibration steps
- Missing: Fitting weights and uncertainties
- Missing: Archival RM data provenance
- Data volume (inferred): ~100-300 GB raw for three epochs
- Score (inferred): 3/5, Data identified with project code, recipe simple but calibration details missing.
- Rediscovery candidate: no, Public status not stated and calibration details insufficient.

## Links

- Method: 2016ApJ...824..132N (ALMA polarimetry science verification accuracy)
- Related: Event Horizon Telescope

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
  "facts": 58,
  "stated": 23,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
