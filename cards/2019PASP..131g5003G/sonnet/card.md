# Calibration of ALMA as a Phased Array. ALMA Observations During the 2017 VLBI Campaign

`2019PASP..131g5003G` | Publications of the Astronomical Society of the Pacific 2019 | first author: Goddi, C. | arXiv: 1901.09987 | DOI: 10.1088/1538-3873/ab136a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: How to calibrate and quality-assure ALMA phased-array (VLBI mode) interferometric data so that phased ALMA becomes a fully calibrated VLBI station, illustrated with the 2017 GMVA/EHT campaign  
  > "These procedures are required to turn the phased ALMA array into a fully calibrated VLBI station." (abstract)
- Target **OJ287, Sgr A*, 3C273, M87, 3C279, NGC1052, Cen A (VLBI targets)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00413.V, 2016.1.01116.V, 2016.1.01216.V, 2016.1.01114.V, 2016.1.01154.V, 2016.1.01176.V, 2016.1.01198.V, 2016.1.01290.V, 2016.1.01404.V
- bands: Band 3 (3 mm) with GMVA; Band 6 (1.3 mm) with EHT  
  > "at 3mm (Band 3) and 1.3mm (Band 6) as part of Cycle-4." (abstract)
- frequencies and spectral setup: 4 SPWs of 1875 MHz, 240 channels each (7.8125 MHz); Band 3 centered 86.26, 88.2, 98.26, 100.26 GHz; Band 6 213.1, 215.1, 227.1, 229.1 GHz  
  > "the spectral setup includes four spectral windows (SPWs) of 1875 MHz, two in the lower and two in the upper sideband, correlated with 240 channels per SPW" (3 VLBI Observations with phased-ALMA during Cycle 4)
- continuum bandwidth: _not stated_
- arrays: ~37 phased 12-m antennas within 180 m radius (~73 m equivalent diameter)  
  > "about 37 antennas[^5] within a radius of 180 m[^6] were normally phased together (which is equivalent to a telescope of $\sim$73 m diameter)" (3 VLBI Observations with phased-ALMA during Cycle 4)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 3: 2017 April 2-4; Band 6: April 5-11 2017  
  > "The projects were executed as part of the global VLBI observing campaign from April 2 to April 11 2017." (3 VLBI Observations with phased-ALMA during Cycle 4)
- pi or archival as stated: _not stated_
- Other facility **GMVA**: VLBI partner network for Band 3  
  > "the Global mm-VLBI Array (GMVA) and the Event Horizon Telescope (EHT) are available to serve as the respective partner networks." (3 VLBI Observations with phased-ALMA during Cycle 4)
- Other facility **EHT**: VLBI partner network for Band 6  
  > "the Global mm-VLBI Array (GMVA) and the Event Horizon Telescope (EHT) are available to serve as the respective partner networks." (3 VLBI Observations with phased-ALMA during Cycle 4)
- External data: ALMA calibrator grid-source flux archive values used for comparison  
  > "The expected flux density of GSs at a given time and frequency can be retrieved from the ALMA archive via the `getALMAflux()` function" (8.2 Comparison with ALMA calibrator grid source archive) [from ALMA calibrator source archive]

## Processing

### Calibration

- pipeline or manual: Manual special QA2 procedures in CASA, APS scans and ALMA scans processed separately  
  > "the two types of scans need to be processed independently within the Common Astronomy Software Applications package (CASA)" (4 Ordinary data calibration)
- casa version: CASA 5.1.1 (4.7.2 and 5.3.0 also tested)  
  > "The data reduction presented here was done using CASA version 5.1.1 (but also versions 4.7.2 and 5.3.0 were successfully tested)." (4 Ordinary data calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (Band 3 projects 00413, 01216), Ganymede (Band 6 tracks B, C); J0510+1800 and 3C279 bootstrapped elsewhere  
  > "For the GMVA, we used J0510+1800 and for EHT tracks we used 3C279." (4.4.1 Primary flux-density calibrators)
- flux scale uncertainty: within 10% in most cases  
  > "the overall uncertainty on the flux-density scale of targets observed with the GMVA and EHT is in most cases within 10%" (4.4.1 Primary flux-density calibrators)
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

- Phased-ALMA system design, TelCal, 90% phasing efficiency goal, eta_A=0.68  
  > "A full overview of the ALMA Phasing System (APS) (and its hardware and software components) as well as a description of the operation of ALMA as a VLBI station, is provided in (cite: APPPaper)." (2 Observing with ALMA as a phased array) [from (cite: APPPaper)]
- PolConvert algorithm for polarization conversion  
  > "Details of this process are described in (cite: PCPaper), and here we summarize the main concepts for completeness." (6.1 Polarization Conversion) [from (cite: PCPaper)]

### Not stated but needed to reproduce (our reading)

- Exact CASA task parameters for gaincal XYf+QU, polcal and smoothing window length of X-Y phase gains
- Specific antenna selection and flagging lists per track
- Reference antenna names per track
- Exact PolConvert settings
- Spectral index and flux values assumed for calibrators beyond tabulated ones

## Analysis recipe

1. **Import and flag data**: Concatenate ASDMs per project/track; no WVR, Tsys or antenna-position corrections; flag sum antenna DV03 and first ~22 s of each scan; no shadowing flags  
  > "Thus, the first $\sim$ 22 sec of each $\sim$ 4-8 min block (which is the typical length of a VLBI scan) are routinely flagged to prevent using poorly phased data." (4.1.2 Data flagging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Bandpass and phase gain calibration**: Bandpass from ALMAscans, phases zeroed copy for APSscans; gaincal phase with solint='int' separately for each scan type  
  > "The `gaincal` task derives phase gains tables with a solution interval equal to the integration time of the ALMA correlator (`solint = ’int’`)." (4.3 Phase Gains Calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Amplitude and flux scale calibration**: setjy, gaincal in T mode with scan solint, fluxscale; Tsys not used; post-QA2 opacity correction from Tsys  
  > "the gain calibration is performed in "T" mode (i.e., one common gain for the two polarizations)" (4.4 Amplitude Calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: Comparison with ALMA grid-source archive fluxes  
  > "Figure [16](#fig:fluxcomp_gs) shows such a comparison, which can be used to identify possible systematic trends" (8.2 Comparison with ALMA calibrator grid source archive)
4. **Polarization calibration**: gaincal G for pol calibrator; XYf+QU for X-Y phase; qufromgain to fix sign; polcal for D-terms per SPW; gaincal for X/Y amplitude ratios  
  > "The cross-hand phase differences relative to a reference antenna are calibrated using the CASA task `gaincal` with the mode `XYf+QU`" (5 Polarization calibration)
   - software: CASA, almapolhelpers
   - assumption: Stokes V = 0 and negligible second-order D-terms  
  > "Stokes V = 0 is assumed for simplicity." (Footnote 13)
   - fitting: _not stated_
   - validation: Q/U from cross-hands and gain ratio consistent  
  > "we assessed that both methods provide consistent values for the polarization angles and fractional linear polarization" (5.2.3 Estimating QU)
5. **Apply calibration to VLBI visibilities and assess phasing efficiency**: PolConvert applies QA2 tables; DPFU set to 0.031 K/Jy, SEFD derived; phasing efficiency from CalAppPhase and gains  
  > "We therefore set the average DPFU $= 0.031$ K/Jy as representative of the phased array during the whole campaign." (6.2.1 DPFU, Tsys, and SEFD)
   - software: PolConvert, DiFX
   - fitting: _not stated_
   - validation: SEFD compared with theoretical expectation  
  > "one derives SEFD = 74 Jy in Band 6, which matches perfectly the estimate from the QA2 gain calibration." (6.2.1 DPFU, Tsys, and SEFD)

## Software

- **CASA** 5.1.1: QA2 calibration of ALMA VLBI data  
  > "The data reduction presented here was done using CASA version 5.1.1" (4 Ordinary data calibration)
- **PolConvert** : Apply QA2 tables to VLBI visibilities and convert linear to circular  
  > "It is the `PolConvert` program that transforms the linear-polarization ALMA data streams into a circular basis for VLBI" (2.3 ALMA data QA2 and Polarization conversion)
- **DiFX** : VLBI correlation  
  > "The VLBI correlation is executed with the DiFX software (cite: Deller2011)" (2.2 VLBI correlation and polarization basis)
- **almapolhelpers** : qufromgain to extract Q and U  
  > "one can use the `almapolhelpers` function `qufromgain` in CASA" (5 Polarization calibration)
- **CASA analysis utils** : getALMAflux() for archive flux  
  > "via the `getALMAflux()` function implemented in the `CASA analysis utils`" (8.2 Comparison with ALMA calibrator grid source archive)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Representative phased-ALMA SEFD, Band 6 | 74 | not stated | Jy | 5 | We therefore take SEFD = 74 Jy as the representative sensitivity of phased-ALMA during the 2017 campaign in Band 6. |
| Representative phased-ALMA SEFD, Band 3 | 65 | not stated | Jy | 5 | A similar analysis provides SEFD = 65 Jy in Band 3. |
| Average DPFU | 0.031 | not stated | K/Jy | 5 | We therefore set the average DPFU $= 0.031$ K/Jy as representative of the phased array during the whole campaign. |
| Fraction of time APS met 90% phasing efficiency | ~80% | not stated | percent | 5 | for about 80% of the time, the APS has met 90 % phasing efficiency |
| 3C279 Band 6 flux (Track B) | 8.9 | 0.9 | Jy | 3 | B (Apr 6)  / 3C279     / $8.9 \pm 0.9$ |

## Qualitative findings

- 3C279 is the best polarization calibrator; alternative calibrators show high RM requiring per-SPW polarization models  
  > "the source 3C 279 was established as the best calibrator." (5.3 Polarization Calibrators)

## Claim tuples

- H: Can ALMA phased-array data be calibrated to serve as a VLBI station | E: Special QA2 calibration of 2017 Band 3 and Band 6 VLBI observations | R: Calibration tables produced for PolConvert; flux scale within ~10%; phasing efficiency >=90% about 80% of time | F: Procedures successfully turn phased ALMA into a calibrated VLBI station | **supported**
- H: Per-SPW polarization models reduce D-term bias from high RM calibrators | E: Compared D-terms with single vs per-SPW models | R: Systematics in single-model case minimized with per-SPW models | F: Calibrate each SPW separately in polarization | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Circular conversion at frontend or backend rejected in favor of post-correlation conversion  
  > "Therefore, the final chosen strategy was to apply a *post-correlation* conversion for the ALMA signal polarization." (2.2 VLBI correlation and polarization basis)
- How they decided it was enough: _not stated_
- Limitation (authors): Not applying Tsys leaves a source-dependent amplitude offset; flux uncertainty up to 10-20% in some sources  
  > "not accounting for the $T_\text{sys}$ of the individual ALMA antennas introduces an amplitude offset which is source-dependent and constant during the observing epoch." (4.4 Amplitude Calibration)
- Caveat (inferred, ours): Flux scale relies on assumption that 3C279 is constant across days, yet it varied ~13%
- Caveat (inferred, ours): No quantitative end-to-end VLBI validation shown here

## Reproducibility

- Data public (paper): Project codes listed as ALMA data used  
  > "This paper makes use of the following ALMA data:" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration scripts
- Missing: CASA task parameters
- Missing: Raw VLBI data from partner stations
- Data volume (inferred): Large (several TB of ASDMs across nine VLBI projects)
- Score (inferred): 3/5, Procedures are described in detail but scripts and many parameters are absent.
- Rediscovery candidate: no, Methods paper; recipe incomplete and results not primarily numeric science.

## Links

- Method: (cite: APPPaper) (ALMA Phasing System description)
- Method: (cite: PCPaper) (PolConvert)
- Companion: (cite: EHT2019III) (EHT data calibration)
- Related: Global mm-VLBI Array
- Related: Event Horizon Telescope
- Related: ALMA Phasing Project

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 32,
  "rate": 0.444
 },
 "evidence_ok": true
}
```
