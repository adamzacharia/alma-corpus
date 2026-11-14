# First M87 Event Horizon Telescope Results. II. Array and Instrumentation

`2019ApJ...875L...2E` | The Astrophysical Journal Letters 2019 | first author: Event Horizon Telescope Collaboration | arXiv: 1906.11239 | DOI: 10.3847/2041-8213/ab0c96

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: How is the EHT VLBI array designed, instrumented and performing, such that it can image horizon-scale structure in SMBH candidates (M87, Sgr A*)?  
  > "we describe the system design of the EHT, detail the technology and instrumentation that enable observations, and provide measures of its performance." (abstract)
- Target **M87**: coordinates α J2000 = 12h30m49.4234s, δ = 12°23'28.044"  
  > "Distance D (pc) 8.34 ´ 10 [3] (2) 16.8 ´ 10 [6] (7)" (Table 1); "when scaled to a distance of 16.8 Mpc (Paper VI)" (1.2 Target Sources and Confirmation of Horizon-scale Structure); z/distance 16.8 Mpc  
  > "Distance D (pc) 8.34 ´ 10 [3] (2) 16.8 ´ 10 [6] (7)" (Table 1); "when scaled to a distance of 16.8 Mpc (Paper VI)" (1.2 Target Sources and Confirmation of Horizon-scale Structure); distance from Paper VI (EHT Collaboration 2019e); Blakeslee et al. 2009  
  > "Distance D (pc) 8.34 ´ 10 [3] (2) 16.8 ´ 10 [6] (7)" (Table 1); "when scaled to a distance of 16.8 Mpc (Paper VI)" (1.2 Target Sources and Confirmation of Horizon-scale Structure)
- Target **Sgr A***: coordinates α J2000 = 17h45m40.0409s, δ = -29°00'28.118"  
  > "Distance D (pc) 8.34 ´ 10 [3] (2) 16.8 ´ 10 [6] (7)" (Table 1); z/distance 8.34e3 pc  
  > "Distance D (pc) 8.34 ´ 10 [3] (2) 16.8 ´ 10 [6] (7)" (Table 1); distance from Reid et al. (2014)  
  > "Distance D (pc) 8.34 ´ 10 [3] (2) 16.8 ´ 10 [6] (7)" (Table 1)
- Target **3C 279**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: Band 6 (1.3 mm), 230 GHz; 0.87 mm planned  
  > "Operating in the 1.3 mm window in full polarimetric mode and with an aggregate bandwidth of 8 GHz" (1.4 Current EHT Array)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~25 μas nominal (λ/D) at 1.3 mm  
  > "At a nominal operating wavelength of ∼1.3 mm, EHT angular resolution (λ/D) is ∼25 μas" (abstract)
- max recoverable scale: _not stated_
- sensitivity: scan-averaged thermal noise well below 1 mJy on most ALMA baselines (2 GHz band)  
  > "The scan-averaged thermal noise within one 2 GHz frequency band was significantly better than 1 mJy on most baselines to ALMA" (3.8 The Array)
- time on source: _not stated_
- observing dates: 2017 April  
  > "In 2017 April, the EHT carried out global observations with an array of eight telescopes" (1.4 Current EHT Array)
- pi or archival as stated: _not stated_
- Other facility **APEX, JCMT, SMA, SMT, LMT, PV 30m, SPT**: Other 2017 EHT stations  
  > "participating telescopes were APEX, JCMT, SMA, SMT, the Large Millimeter Telescope Alfonso Serrano (LMT), the Pico Veleta 30 m telescope (PV), and the South Pole Telescope (SPT)" (1.4 Current EHT Array)
- External data: _not stated_ [from Walsh et al. 2013; Gebhardt et al. 2011; Blakeslee et al. 2009; Reid et al. 2014]

## Processing

### Calibration

- pipeline or manual: Detailed in Paper III; ALMA X/Y to circular conversion via PolConvert after DiFX correlation  
  > "a linear-to-circular polarization conversion is performed on ALMA baselines after VLBI correlation. PolConvert (Martí-Vidal et al. 2016)" (5. Correlation and Calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: self-calibration used to correct telescope gain variations  
  > "by the application of selfcalibration techniques to correct for variations in telescope gain over time and frequency" (5. Correlation and Calibration)

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

- Data pipeline, systematic error estimates, and calibration details  
  > "Precise estimates of the observed systematic errors during the 2017 April EHT campaign are detailed in Paper III." (5. Correlation and Calibration) [from EHT Collaboration et al. 2019b (Paper III)]
- Imaging techniques and RML/CLEAN comparison on M87  
  > "Similar comparisons and results on M87, one of the EHT primary targets, can be found in Paper IV." (2.1 Angular Resolution) [from EHT Collaboration et al. 2019c (Paper IV)]

### Not stated but needed to reproduce (our reading)

- Not a data-analysis paper; no imaging or reduction recipe given
- Observing-run-level ALMA scheduling blocks not listed

## Analysis recipe

1. **Estimate baseline sensitivity and detection S/N**: Radiometer equation for VLBI baseline S/N using SEFDs, 2-bit efficiency, bandwidth and integration time  
  > "is the digital loss due to sampling the received signal at each antenna with finite precision" (Section 2.2 Sensitivity)
   - parameter: ηQ = 0.88 for 2-bit samples  
  > "( _h_ _Q_ = 0.88 for 2-bit samples)" (2.2 Sensitivity)
   - fitting: _not stated_
   - validation: _not stated_
2. **Correlate and calibrate VLBI data**: DiFX correlation, fringe fitting of delay and rate, ALMA-phased referencing of non-ALMA baselines  
  > "Correlation is performed using the Distributed FX (DiFX) software correlator (Deller et al. 2011)" (5. Correlation and Calibration)
   - software: DiFX, PolConvert
   - parameter: averaging bandwidth 0.5 MHz, averaging time 0.4 s  
  > "the typical averaging bandwidth is 0.5 MHz and the averaging time is 0.4 s" (5. Correlation and Calibration)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DiFX** : VLBI software correlation  
  > "Correlation is performed using the Distributed FX (DiFX) software correlator (Deller et al. 2011)" (5. Correlation and Calibration)
- **PolConvert** : Linear-to-circular polarization conversion of ALMA data  
  > "PolConvert (Martí-Vidal et al. 2016) is a software routine developed for this purpose" (5. Correlation and Calibration)
- **VLBImonitor** : Centralized monitoring of observing status  
  > "The EHT developed a centralized monitoring tool called VLBImonitor to visualize observing status" (4.3 Monitoring and VLBI Backend Control)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA–SPT S/N for Sgr A* in 3 s | about 12 | not stated | dimensionless | 1 | an integration time of 3 s yields an S/N of about 12 |
| Fraction of ALMA-baseline scans with Tcoh > 10 s | >75% | not stated | percent | 0 | more than 75% of scans on baselines in the 2017 array that include ALMA had T coh greater than 10 s |
| ALMA thermal noise to APEX (10 s, 4 GHz) | 0.53 (Table 5 median, M87)  | not stated | mJy | 0 | ALMA37 0.53 0.80 0.34 0.43 0.54 0.57 1.75 |
| Recording rate | 64 | not stated | Gbps | 0 | As of 2018, EHT stations record at 64 Gbps |

## Qualitative findings

- Phased ALMA increases sensitivity by nearly an order of magnitude and enables full baseline coverage via two-stage fringe detection  
  > "the resulting increase in sensitivity above the first horizon-scale detections was nearly an order of magnitude" (1.4 Current EHT Array)

## Claim tuples

- H: The 2017 EHT array meets sensitivity and coverage specifications for horizon-scale imaging | E: Measured scan-averaged thermal noise and (u,v) coverage on M87 in 2017 | R: Noise well below 1 mJy on most ALMA baselines; few mJy otherwise | F: EHT met its essential specification for imaging SMBH shadow-scale features | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: ALMA phasing gives high S/N baselines to remove atmospheric phase on other stations  
  > "these ALMA detections are used to remove the effects of phase fluctuations (due to atmospheric turbulence) above the non-ALMA stations" (2.2 Sensitivity)
- How they decided it was enough: _not stated_
- Limitation (authors): No real-time fringe verification; data shipping takes days to months  
  > "the EHT lacks real-time verification of fringes" (3.7 Setup and Verification)
- Caveat (inferred, ours): Instrument description paper; few reproducible numeric results
- Caveat (inferred, ours): ALMA data are only the phased-array contribution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Raw VLBI data and correlator outputs not described as available here
- Missing: Pipeline details deferred to Paper III
- Data volume (inferred): Petabyte-scale raw VLBI data (~15 PB per campaign across array)
- Score (inferred): 1/5, Instrumentation overview without a data analysis recipe.
- Rediscovery candidate: no, Not an analysis paper; recipe and data not specified.

## Links

- Method: Matthews et al. 2018 (ALMA phasing system)
- Method: Goddi et al. 2019 (ALMA VLBI phasing details)
- Companion: EHT Collaboration et al. 2019b (Paper III) (Data processing and calibration)
- Companion: EHT Collaboration et al. 2019c (Paper IV) (Imaging)
- Related: Event Horizon Telescope
- Related: ALMA Phasing Project

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 66,
  "stated": 26,
  "rate": 0.394
 },
 "evidence_ok": true
}
```
