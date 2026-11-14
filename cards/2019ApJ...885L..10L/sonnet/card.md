# Detection of Pulses from the Vela Pulsar at Millimeter Wavelengths with Phased ALMA

`2019ApJ...885L..10L` | The Astrophysical Journal Letters 2019 | first author: Liu, Kuo | arXiv: 1910.07974 | DOI: 10.3847/2041-8213/ab4da8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, instrumentation
- Question: Can phased ALMA detect, time and search for pulsars at 3 mm, and what are the flux density and polarization of the Vela pulsar at 85-101 GHz?  
  > "We describe the pipeline and demonstrate the capability of ALMA to perform pulsar timing and searching." (abstract)
- Target **Vela pulsar (PSR J0835-4510)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00004.E
- bands: Band 3 (85-101 GHz)  
  > "The detection was made in the Band-3 frequency range ($85-101$ GHz)" (abstract)
- frequencies and spectral setup: 4x2-GHz sub-bands centred at 86.268, 88.268, 98.268, 100.268 GHz; 32x62.5-MHz channels per sub-band; 8 us time resolution  
  > "providing 4$\times$2-GHz sub-bands centered at 86.268, 88.268, 98.268 and 100.268 GHz, respectively." (2 Observations); "Each sub-band was subdivided into $32\times 62.5$-MHz frequency channels." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 37 12-m antennas phased, equivalent to a 73-m dish  
  > "In total, 37 12-m antennas were phased up to form a tied-array beam, delivering a collecting area equivalent to a 73-m parabolic dish." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~40 min observation; 25 min effective integration  
  > "The observation spanned approximately 40 min." (2 Observations); "An effective integration time of 25 min yields a peak signal-to-noise ratio" (3 Results)
- observing dates: 2017 January 29  
  > "conducted with ALMA using Band-3 on 2017 January 29 under excellent weather conditions." (2 Observations)
- pi or archival as stated: Test data from ALMA Phasing Project commissioning runs  
  > "used test data obtained in conjunction with ALMA Phasing Project commissioning runs in 2016 April and 2017 January." (2 Observations)
- Other facility **Parkes Radio Telescope**: 1.4 GHz profile of Vela for phase comparison  
  > "phase of the pulse arrival time at 1.4 GHz (obtained at the Parkes Radio Telescope)" (3.3.2 Profile evolution)
- External data: Vela multi-frequency profiles, 24 GHz flux density, component spectral indices and polarisation template  
  > "We use those presented by (cite: kjlb11), following their alignment based on a separation of the profile into individual components" (3.3.2 Profile evolution) [from (cite: kjlb11)]

## Processing

### Calibration

- pipeline or manual: Phased-array data: phasing on calibrator, passive phasing on Vela; parallel interferometric data calibrated with phased-ALMA procedures  
  > "calibrated following the dedicated procedures developed for phased ALMA (cite: Goddi2019)" (3.3.1 Flux Density)
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

- Calibration of parallel interferometric data  
  > "calibrated following the dedicated procedures developed for phased ALMA (cite: Goddi2019)" (3.3.1 Flux Density) [from (cite: Goddi2019)]
- Flux calibration formula  
  > "by using the standard flux calibration formula (cite: lk04)" (3.3.1 Flux Density) [from (cite: lk04)]

### Not stated but needed to reproduce (our reading)

- Vela ephemeris used for folding
- Folding parameters and number of profile bins
- Template profile used for TOA
- PRESTO search parameters
- Polarisation calibration fitting details
- Interferometric imaging settings
- Phasing solution details

## Analysis recipe

1. **fold search-mode data**: Fold into 10-s sub-integrations using ephemeris from low-frequency observations  
  > "the data were folded to form 10-s sub-integrations, using an ephemeris obtained from low frequency observations" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **timing**: Frequency-averaged profile TOAs by template matching; residuals vs ephemeris  
  > "calculated its time-of-arrival (TOA) with the canonical template-matching method (cite: tay92)" (3.1 Timing)
   - fitting: _not stated_
   - validation: rms consistent with radiometer-noise TOA errors  
  > "which is in general consistent with the TOA errors expected from radiometer noise" (3.1 Timing)
3. **blind periodicity search**: Average sub-bands, combine scans with mean-padded gaps, search power spectrum  
  > "Then a periodicity search was performed using the PRESTO software package (cite: rem02)." (3.2 Search capability)
   - software: PRESTO
   - fitting: _not stated_
   - validation: _not stated_
4. **flux density**: Calibrate pulsed flux with nearest calibrator scan; cross-check with interferometric images  
  > "we used the closest calibrator scan to calibrate the flux density of the pulsed emission" (3.3.1 Flux Density)
   - fitting: _not stated_
   - validation: Consistent with interferometric measurements  
  > "These are fully consistent with the measurements derived from the phased ALMA data." (3.3.1 Flux Density)
5. **polarisation calibration**: Use 24 GHz profile as polarisation template; fit differential gain and phase  
  > "we can use the data by (cite: kjlb11) as a polarisation template and perform a system calibration" (3.3.3 Polarization properties)
   - assumption: Polarisation similar to that at 24 GHz  
  > "Assuming that the observed polarisation characteristics are similar to those observed at 24 GHz" (3.3.3 Polarization properties)
   - fitting: _not stated_
   - validation: PA consistent with 1.4 GHz after Faraday correction  
  > "the position angle is perfectly consistent with the 1.4 GHz data (after correcting for Faraday rotation)" (3.3.3 Polarization properties)

## Software

- **PRESTO** : Periodicity search  
  > "a periodicity search was performed using the PRESTO software package (cite: rem02)" (3.2 Search capability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak S/N lower sideband | ~50 | not stated | dimensionless | 1 | yields a peak signal-to-noise ratio of the detection of $\sim$50 for the lower and $\sim$40 for the upper sideband |
| Weighted rms timing uncertainty | 134 | not stated | us | 2 | A weighted root-mean-square (rms) timing uncertainty of 134 $\mu$s has been achieved |
| Flux density at 87.268 GHz (phased) | 0.99 | 0.17 | mJy | 4 | mean flux density of $0.99\pm0.17$ mJy and $0.69\pm0.12$ mJy at 87.268 and 99.268 GHz |
| Flux density at 99.268 GHz (phased) | 0.69 | 0.12 | mJy | 4 | mean flux density of $0.99\pm0.17$ mJy and $0.69\pm0.12$ mJy at 87.268 and 99.268 GHz |
| Search candidates above 3 sigma | 28 | not stated | dimensionless | 3 | The periodicity search resulted in 28 candidates with detection significance above $3\sigma$. |
| Delay of ALMA peak vs 1.4 GHz main peak | ~1.8 | not stated | ms | 0 | the latter is delayed by about 1.8 ms with respect to the main pulse peak at 1.4 GHz |
| Linear polarisation degree | ~20 | not stated | % | 5 | the degree of linear polarisation ($\sim 20\%$) is lower than at 24 GHz |

## Qualitative findings

- Vela detected up to 101.268 GHz, the highest frequency at which its profile has been seen  
  > "The signal was detected at frequencies up to 101.268 GHz, the highest radio frequency that the pulse profile of Vela has ever been seen." (3 Results)

## Claim tuples

- H: Phased ALMA can detect pulsars and provide timing | E: Fold and time Vela data | R: S/N ~50 and ~40; 134 us rms | F: ~100 us timing precision is possible at 3 mm | **supported**
- H: Phased ALMA data allow blind periodicity searches | E: PRESTO search | R: Vela fundamental top of 28 candidates | F: Search capability demonstrated | **supported**
- H: Vela mm flux matches extrapolation from lower frequencies | E: Compare measured flux to extrapolated component | R: 0.94 and 0.82 mJy expected vs measured | F: Agreement | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Systematics associated with phasing cycles in active-phasing scans  
  > "we noticed significant systematics in the time series which are associated with the phasing cycles." (4 Discussion)
- Caveat (inferred, ours): Single observation; no formal polarisation uncertainties
- Caveat (inferred, ours): Flux errors from only four scans
- Caveat (inferred, ours): Profile alignment with literature done by eye

## Reproducibility

- Data public (paper): Data staged on ALMA science portal  
  > "The data are available via: <https://almascience.eso.org/alma-data/enhanced-data-products/vela-pulsar-j0835-4510>." (Footnote 8)
- Products in archive: _not stated_
- Missing: MPIfR pipeline not released or described in detail
- Missing: Ephemeris, folding and PRESTO parameters
- Missing: Polarisation calibration details
- Data volume (inferred): Large, likely hundreds of GB of baseband/search-mode data
- Score (inferred): 3/5, Data public but the custom pipeline and key parameters are not given.
- Rediscovery candidate: no, Requires non-public custom pipeline and baseband processing with missing parameters.

## Links

- Method: (cite: mcd+18) (ALMA phasing system)
- Method: (cite: Goddi2019) (Phased ALMA calibration procedures)
- Companion: (cite: kjlb11) (Multi-frequency Vela profiles and polarisation template)
- Related: ALMA Phasing Project
- Related: ALMA Pulsar Mode Project

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 25,
  "rate": 0.379
 },
 "evidence_ok": true
}
```
