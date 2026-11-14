# The ALMA Band 9 receiver. Design, construction, characterization, and first light

`2015A&A...577A.129B` | Astronomy and Astrophysics 2015 | first author: Baryshev, A. M. | arXiv: 1503.01988 | DOI: 10.1051/0004-6361/201425529

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, star_formation
- Question: Design, construction, laboratory performance and on-sky first-light performance of the ALMA Band 9 (600–720 GHz) receivers  
  > "On-sky characterization and tests of the performance of the Band 9 cartridges are presented using commissioning data." (abstract)
- Target **IRAS 16293-2422**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1924-292**: coordinates RA=19:24:51.056, Dec=-29:14:30.121 (J2000)  
  > "ALMA observed the quasar J1924-292 (RA=19:24:51.056, Dec=$-29$:14:30.121, J2000)" (4.2 Quasar tracking); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00007.SV
- bands: Band 9 (602–720 GHz)  
  > "Frequency range | 602–720 GHz" (Table 1)
- frequencies and spectral setup: four spectral windows including 12CO 6-5; spectrum binned to 1.95 MHz (~0.8 km/s)  
  > "The four spectral windows are binned to a resolution of 1.95 MHz ($\sim$0.8 km s$^{-1}$)" (3.3.1 Science verification: IRAS 16293-2422)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 extended configuration  
  > "with ALMA in a Cycle 0 extended configuration" (3.3.1 Science verification: IRAS 16293-2422)
- baselines: _not stated_
- angular resolution: ≈0.22 arcsec for IRAS 16293-2422  
  > "resulting in a resolution of $\approx$0 $''$22" (3.3.1 Science verification: IRAS 16293-2422)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 9.2 hours total for seven-point mosaic including calibration  
  > "A total of 9.2 hours were spent on a seven-point mosaic and the necessary calibration" (3.3.1 Science verification: IRAS 16293-2422)
- observing dates: 16 and 17 April 2012  
  > "Science Verification of Band 9 was undertaken on April 16 and 17, 2012" (3.3.1 Science verification: IRAS 16293-2422)
- pi or archival as stated: _not stated_
- Line: 12CO J=6-5 (691.47308 GHz)

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

- Observation and calibration details of IRAS 16293-2422 SV data given in CASA guide  
  > "More detailed information on the observations and calibration can be found in the CASA guide" (3.3.1 Science verification: IRAS 16293-2422) [from CASA guide IRAS16293Band9 (casaguides.nrao.edu)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, cell, clean masks) for IRAS 16293 cubes
- Calibration procedure, CASA version and calibrators for SV data
- Line-free channels and continuum subtraction

## Analysis recipe

1. **Extract Band 9 spectrum toward IRAS 16293 B**: Spectrum averaged over a 0.3"x0.3" region centered on source B, binned to 1.95 MHz  
  > "the spectrum is averaged over a $0\,\ensuremath{''}3\times0\,\ensuremath{''}3$ region centered on source B" (3.3.1 Science verification: IRAS 16293-2422)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **WVRGCAL** : Water vapor radiometer corrections applied to quasar test data  
  > "Corrections using the water vapor radiometer solutions, derived using the WVRGCAL software (cite: Nikolic12), were applied in the test" (4.2 Quasar tracking)
- **CASA** : Referenced via CASA guide for SV data reduction  
  > "More detailed information on the observations and calibration can be found in the CASA guide" (3.3.1 Science verification: IRAS 16293-2422)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average aperture efficiency of Band 9 receivers (62 cartridges) | 81.89 | ±0.90 | percent | 0 | $\eta_{aperture}$ / $81.89$  / $\pm$ 0.90 |
| Phase RMS on J1924-292 | ~30–35 | not stated | degrees | 0 | All phases are extremely flat with RMS numbers of $\sim$30–35 degrees. |
| Number of emission lines in IRAS 16293 B spectrum | >100 | not stated | lines | 1 | Over 100 emission lines are clearly visible in the spectrum. |

## Qualitative findings

- All Band 9 receivers comply with ALMA specifications in the laboratory; AlN-barrier junctions cover the band better than AlOx  
  > "The laboratory results show that all receivers complied with ALMA specifications prior to integration in the ALMA antennas." (4. Conclusions)

## Claim tuples

- H: Do the Band 9 receivers meet ALMA specifications? | E: Laboratory measurements of noise temperature, gain compression and beam on 73 cartridges | R: All receivers perform better than the specification with margin; gain compression within 4% | F: Receivers comply with specifications | **supported**
- H: Is Band 9 phase and amplitude stability good on sky? | E: Quasar tracking and four-quasar phase-transfer tests | R: Phase RMS 10–25 deg in four-quasar test; stable phases on J1924-292 | F: Excellent on-sky performance | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO 6-5 line profile not correctly cleaned and filtered by lack of short baselines  
  > "CO $J$=6–5 emission extends over a large area (cite: 2013A&A...549L...6K), and is thus not correctly cleaned." (3.3.1 Science verification: IRAS 16293-2422)
- Caveat (inferred, ours): On-sky tests are qualitative, with uncalibrated amplitudes and few baselines
- Caveat (inferred, ours): ALMA science data processing not described

## Reproducibility

- Data public (paper): IRAS 16293-2422 dataset is publicly available  
  > "This dataset is publicly available." (1 Introduction)
- Products in archive: _not stated_
- Missing: Full data reduction script (only via external CASA guide)
- Missing: Lab measurement raw data
- Data volume (inferred): tens of GB for the IRAS 16293 SV dataset
- Score (inferred): 2/5, Mostly hardware paper; ALMA data analysis is minimal and not detailed.
- Rediscovery candidate: no, Main results are hardware characterizations, not reproducible from ALMA data.

## Links

- Method: Baryshev et al. 2004a (cite: baryshev2004verification) (Beam and gain compression measurement method)
- Companion: Jørgensen et al. 2012 (cite: 2012ApJ...757L...4J) (Glycolaldehyde detection from the same SV data)
- Related: ALMA Science Verification IRAS 16293-2422 Band 9

## Checks

```json
{
 "quotes": 23,
 "quotes_ok": 23,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 54,
  "stated": 15,
  "rate": 0.278
 },
 "evidence_ok": true
}
```
