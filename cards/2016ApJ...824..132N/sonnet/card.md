# ALMA Science Verification Data: Millimeter Continuum Polarimetry of the Bright Radio Quasar 3C 286

`2016ApJ...824..132N` | The Astrophysical Journal 2016 | first author: Nagai, H. | arXiv: 1605.00051 | DOI: 10.3847/0004-637X/824/2/132

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, instrumentation
- Question: What are the millimeter (1.3 mm) total intensity and linear polarization properties of the quasar 3C 286, and how do they relate to the centimeter EVPA trend and core shift?  
  > "In this paper we present the results from the SV data, as well as an interpretation of the frequency dependence of the EVPA and the nature of 3C 286 with the aid of VLBA data." (Introduction)
- Target **3C 286**: coordinates _not stated_; z/distance z = 0.849  
  > "3C 286 is a bright radio quasar at the redshift $z = 0.849$ (cite: Burbidge1969)." (Introduction); distance from Burbidge1969  
  > "3C 286 is a bright radio quasar at the redshift $z = 0.849$ (cite: Burbidge1969)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00017.SV
- bands: Band 6 (1.3 mm)  
  > "using thirty-one 12 m antennas in Band 6 (1.3 mm)." (2 Observation and Data Reduction)
- frequencies and spectral setup: 4 spws (2 LSB, 2 USB), 64 channels each, 31.25 MHz channels, 2 GHz per spw; centers 224, 226, 240, 242 GHz  
  > "The central frequencies in spws 0, 1, 2, and 3 are 224 GHz, 226 GHz, 240 GHz, and 242 GHz, respectively." (2 Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: thirty-one 12 m antennas  
  > "using thirty-one 12 m antennas in Band 6 (1.3 mm)." (2 Observation and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~2 hours total  
  > "yielding $\sim$ 2 hours of integration in total." (2 Observation and Data Reduction)
- observing dates: 2014 July 1 and July 2  
  > "The observations were performed on 2014 July 1 and July 2" (2 Observation and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **VLBA (MOJAVE, RRFID archival)**: Archival images at 13, 4, 2 cm for core-shift analysis  
  > "we analyzed archival VLBA images at 13 cm, 4 cm, and 2 cm obtained from the “Monitoring Of Jets in Active galactic nuclei with the VLBA Experiments” (MOJAVE) and the Radio Reference Frame Image Database (RRFID)." (4 Discussion)
- External data: SW component flux 31.4 mJy at 8.4 GHz  
  > "The flux density of the SW component reported in (cite: Akujor1995) is 31.4 mJy at 8.4 GHz." (3 Results) [from Akujor1995]

## Processing

### Calibration

- pipeline or manual: Manual CASA calibration following CASA guide, plus refined gain calibration and self-calibration  
  > "The data reduction procedure presented here is also described in the CASA guide." (2 Observation and Data Reduction)
- casa version: CASA 4.3.1  
  > "The data reduction was done using Common Astronomical Software Applications (CASA) version 4.3.1." (2 Observation and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres  
  > "The flux scaling factor was estimated using Ceres." (2 Observation and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase then amp+phase self-cal, 30 s solint, using CLEAN models of I, Q, U  
  > "we performed both amplitude and phase self-calibration (`calmode=ap`) with a solution interval of 30 seconds." (2 Observation and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5 (for self-cal models)  
  > "using `CLEAN` with Briggs weighting and a robustness value of 0.5." (2 Observation and Data Reduction)
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
- final rms: 0.05 (I), 0.04 (Q), 0.04 (U) mJy/beam  
  > "We obtained a final image rms of 0.05 mJy beam$^{-1}$, 0.04 mJy beam$^{-1}$, and 0.04 mJy beam$^{-1}$ for Stokes $I$, $Q$, and $U$, respectively." (2 Observation and Data Reduction)

### Inherited from earlier work

- Data reduction procedure follows the 3C 286 polarization CASA guide  
  > "The data reduction procedure presented here is also described in the CASA guide." (2 Observation and Data Reduction) [from 3C 286 polarization CASA guide (footnote)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, and CLEAN iterations/threshold/masks
- Which data were excluded in the first half of the observation
- Flagged channels and antennas list
- Beam size of final images
- Fitting regions/method for core and SW flux and polarization
- Details of core-shift power-law extrapolation and error propagation
- Image parameters for VLBA reduction and super-resolution beam

## Analysis recipe

1. **Polarization calibration**: Gain solution without polarization model, qufromgain for Q/U of calibrator, KCROSS and XYf+QU for cross-hand, then polcal for D-terms with J1337-1257  
  > "The cross-hand delay and cross-hand phase differences relative to a reference antenna were calibrated using the CASA task `gaincal` with the modes `KCROSS` and `XYf+QU` respectively." (2 Observation and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Repeated D-term calibration with 3C 279; agreement within 0.5%  
  > "The differences between the two solutions is not greater than 0.5% and is typically 0.1–0.3% over the band" (A.1.2 Reproducibility of the Instrumental Polarization Calibration)
2. **Refine gain calibration and self-calibrate**: Model gain calibrator I,Q,U with CLEAN and redo gains; self-cal 3C 286 with phase then amp+phase  
  > "we re-performed the gain calibration of the gain calibrator based on the models, and then applied the calibration to 3C 286." (2 Observation and Data Reduction)
   - software: CASA
   - parameter: solint 30 s; Briggs robust 0.5  
  > "we performed phase self-calibration with a solution interval of 30 seconds." (2 Observation and Data Reduction)
   - fitting: _not stated_
   - validation: Time dependence of phase and amplitude significantly improved  
  > "After all of these processes the time dependence of phase and amplitude were significantly improved." (2 Observation and Data Reduction)
3. **Measure core and SW intensity and polarization**: Peak intensities from I, Q, U images; polarization bias correction for the SW component  
  > "we should take into account the polarization bias (cite: Vaillancourt2006) for this component." (3 Results)
   - software: CASA
   - assumption: Absolute EVPA error 0.4 deg from 2 deg misalignment over 29 antennas  
  > "Throughout this paper, we adopt $0.4^{\circ}$ for the absolute EVPA accuracy." (2 Observation and Data Reduction)
   - fitting: _not stated_
   - validation: Agreement with Hull2015 and Agudo2012 EVPA  
  > "The obtained EVPA shows a good agreement with (cite: Hull2015) and (cite: Agudo2012)" (3 Results)
4. **Core-shift analysis from archival VLBA**: Gaussian fits of C1 and C2 with JMFIT; separation vs frequency; extrapolate with power law k=1 to 230 GHz; super-resolution at 13 cm  
  > "Instead, we assume $k=1$, which is the case for a conical jet (cite: Konigl1981)" (4 Discussion)
   - software: AIPS JMFIT
   - assumption: C2 position independent of frequency and optically thin  
  > "Assuming that C2 has no frequency dependence of its position, the change in the relative distance can be regarded as the position shift of the radio core (C1)." (4 Discussion)
   - fitting: Power law r_c = A + B nu^-1/k with k=1 assumed since only three points  
  > "Since we have only three data points, it is not possible to perform a fit with the function $r_\textrm{c}=A+B\nu^{-1/k}$" (4 Discussion)
   - validation: 4 cm images convolved with several beams show monotonic separation decrease  
  > "We confirmed that the resultant separation monotonically decreased from $\sim$ 5.5 mas to $\sim$ 4.5 mas with increasing size of the convolving beam, as expected." (A.2 Core Shift Analysis for 3C 286)

## Software

- **CASA** 4.3.1: Calibration, polarization calibration, CLEAN imaging, self-calibration  
  > "The data reduction was done using Common Astronomical Software Applications (CASA) version 4.3.1." (2 Observation and Data Reduction)
- **almapolhelpers.py (qufromgain)** : Extract Stokes Q and U of calibrator from gain solution  
  > "we used the function `qufromgain` in an add-on script `almapolhelpers.py` in CASA." (2 Observation and Data Reduction)
- **AIPS JMFIT** : Gaussian fitting of VLBI components C1 and C2  
  > "We performed Gaussian model fitting to C1 and C2 using the AIPS task `JMFIT`" (4 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core peak intensity I | 387.77 | 0.05 | mJy/beam | 3 | 387.77$\pm$0.05 mJy |
| Core polarized intensity | 64.81 | 0.07 | mJy/beam | 3 | 64.81$\pm$0.07 mJy |
| Core fractional polarization | 16.7 | 0.2 | % | 3 | The polarization percentage of the core is 16.7$\pm$0.2% |
| Core EVPA | 38.6 | 0.4 | degrees | 3 | The EVPA of the core is $38.6\pm0.4$ degrees. |
| SW component peak intensity | 0.55 | 0.05 | mJy/beam | 3 | 0.55$\pm$0.05 mJy |
| Predicted 1.3 mm core offset upstream of 2 cm core | 0.17 mas (~1.3 pc projected) | not stated | mas | 4 | we expect the 1.3 mm radio core to be located $\sim$ 0.17 mas upstream of the 2 cm core. |

## Qualitative findings

- Serendipitous 6 sigma sub-mJy point source ~11 arcsec NNW of core, likely a submillimeter galaxy  
  > "A $6\sigma$ point source is detected at the position (RA, DEC)=(13:31:08.0, 30:30:43.0)" (3 Results)

## Claim tuples

- H: EVPA of 3C 286 continues to increase from cm to mm wavelengths | E: ALMA 1.3 mm full-polarization imaging | R: EVPA 38.6±0.4 deg vs ~33 deg at 20 cm | F: Confirms slow EVPA increase toward mm | **supported**
- H: mm core is more ordered than cm emission | E: Measure fractional polarization | R: 16.7% vs ~10% at 20 cm | F: Magnetic field more ordered in mm core | **supported**
- H: EVPA change relates to frequency-dependent core position | E: VLBA C1-C2 separation vs frequency | R: Core shift extrapolated ~0.17 mas | F: Consistent with core shift but not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Faraday rotation rejected since EVPA does not change at cm bands; bent-jet beamed model deemed unlikely  
  > "This trend cannot be explained by Faraday rotation since the change in the EVPA is not observed in centimeter bands (cite: Perley2013)." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Only three VLBI points, non-simultaneous, C2 may be optically thick; Stokes I dynamic-range limited  
  > "Since we have only three data points, it is not possible to perform a fit" (4 Discussion)
- Caveat (inferred, ours): Core-shift extrapolation from three non-simultaneous points with k=1 assumed is weakly constrained
- Caveat (inferred, ours): Absolute EVPA error from private communication
- Caveat (inferred, ours): SW polarization only 2.8 sigma

## Reproducibility

- Data public (paper): ALMA Science Verification data publicly released  
  > "The Atacama Large Millimeter and Submillimeter Array (ALMA) released the Science Verification (SV) data of 3C 286 on 2015 July 28." (Introduction)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, iterations)
- Missing: Exact flagging/excluded time range
- Missing: VLBA fit details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public SV data and CASA guide, but imaging and flagging details missing.
- Rediscovery candidate: yes, Public SV data, CASA guide recipe, numeric results (flux, polarization fraction, EVPA).

## Links

- Method: 3C 286 polarization CASA guide (Calibration procedure)
- Companion: Hull2015 (mm polarization of 3C 286 with CARMA)
- Related: MOJAVE
- Related: RRFID

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 36,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
