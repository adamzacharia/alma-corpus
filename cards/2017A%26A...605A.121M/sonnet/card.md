# Phase correction for ALMA. Investigating water vapour radiometer scaling: The long-baseline science verification data case study

`2017A&A...605A.121M` | Astronomy and Astrophysics 2017 | first author: Maud, L. T. | arXiv: 1707.03506 | DOI: 10.1051/0004-6361/201731197

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation
- Question: Whether scaling the water vapour radiometer (WVR) solutions in wvrgcal improves phase correction, coherence and image S/N in ALMA long-baseline science verification data, and how the optimal scaling relates to weather conditions  
  > "We attempt to provide an extra step in reducing the phase variations via the application of a scaling factor in the WVR solutions." (Introduction)
- Target **Juno (asteroid)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Mira**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SDP.81**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00013.SV, 2011.0.00014.SV, 2011.0.00015.SV, 2011.0.00016.SV
- bands: Bands 3, 4, 6, 7 (Juno B6; Mira B3, B6; HL Tau B3, B6, B7; SDP.81 B4, B6, B7)  
  > "the young protostar with circumstellar disk, HL Tau, at bands 3, 6, and 7 (2011.0.00015.SV)" (Observations and reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: long-baseline campaign, 5 to 15 km (2014 campaign)  
  > "The 2014 campaign specifically focussed on baselines from 5 to 15 km." (Introduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~1 hr per EB; 75 EBs; bandpass calibrator ~5 min (Mira B6 ~10 min); target scans ~60-80 s, phase calibrator ~15-18 s  
  > "has a typical observing time of $\sim$1 hour." (Observations and reduction); "Typically the on source (i.e. the science target) time for each scan ranges from $\sim$60 to 80 seconds" (Observations and reduction)
- observing dates: October-November 2014  
  > "2014/10/19" (Table A.1)
- pi or archival as stated: _not stated_

## Processing

### Calibration

- pipeline or manual: Data calibrated with the SV reduction scripts in CASA with standard WVR application, then re-run with scaling in wvrgcal  
  > "we first calibrated the data following the reduction scripts supplied with the SV data via casa (cite: McMullin2007) with the standard WVR application without a scaling factor applied." (Observations and reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Bandpass: natural weighting; science targets: briggs as in SV scripts (robust value not stated)  
  > "Images were made with natural weighting with a shallow clean (50 iterations including a source mask of the central 15 pixels in radius)" (4.2.1 Bandpass calibrator)
- uv taper: _not stated_
- cell size: _not stated_
- image size: Increased relative to SV scripts  
  > "We also increased the image size to better understand if there is an improvement in the image noise" (4.2.3 Science targets)
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

- Science target imaging parameters (clean threshold, weighting, multi-scale clean) taken from the SV imaging scripts  
  > "These images are produced with exactly the same clean parameters as delivered in the SV imaging scripts for the respective sources" (4.2.3 Science targets) [from ALMA SV delivered scripts]
- Initial calibration and flagging follow SV reduction scripts  
  > "These standard calibrated datasets were flagged for errors as noted in the provided SV scripts." (Observations and reduction) [from ALMA SV delivered scripts]

### Not stated but needed to reproduce (our reading)

- CASA version
- Briggs robust, clean thresholds, cell size, multiscale scales for science images (only in SV scripts)
- Exact wvrgcal options besides scale factor
- Number of clean iterations used for science images
- Which antennas were additionally flagged in scaling analysis

## Analysis recipe

1. **Extract and unwrap bandpass-calibrator phases**: Extract phases from widest single spectral window of bandpass calibrator and unwrap  
  > "our algorithm extracts the visibilities (i.e. phases) from only the averaged solution of the widest single spectral window from the dataset" (3.2 Data processing)
   - software: CASA, custom python package
   - fitting: _not stated_
   - validation: Diagnostic plots checked per four baselines to catch wrong unwraps  
  > "these plots allow the user to check the phase streams and two-point-deviation profiles for subsets of four baselines per figure." (3.2 Data processing)
2. **Find optimal WVR scaling factor**: Apply standard WVR solutions scaled by a range of factors to raw phases (via unity point-source dataset) and minimise the two-point-deviation of corrected phases  
  > "Our algorithm searches for the WVR scaling factor associated with the lowest TPD of the corrected phases" (3.3 Scaling the WVR solutions)
   - software: CASA, wvrgcal, custom python package
   - parameter: T = 6, 12, 32, 64 s; scale range 0.05-2.5, step 0.01; reference-antenna-only or all baselines  
  > "The range of the scaling values is capped between 0.05 and 2.5 with the smallest scaling increment of 0.01." (3.3 Scaling the WVR solutions)
   - fitting: Grid search, refined within narrower range, minimising overlapping two-point deviation  
  > "Our algorithm searches for the WVR scaling factor associated with the lowest TPD of the corrected phases, i.e. those with the lowest fluctuations, and further acts to re-adjust the WVR scaling factor (within a narrower range)" (Scaling the WVR solutions)
   - validation: Reference-antenna-only results compared with all-baseline results  
  > "They are also coincident between those found using baselines with the reference antenna only and those found while assessing all baselines" (4.1 Scaling factors)
3. **Estimate coherence improvement**: Coherence from exp(-phi_rms^2/2) using phase RMS over 60 s and full bandpass; ratio of scaled to standard WVR  
  > "The coherence is calculated from Equation [\[eqn0\]](#eqn0) for each baseline via the phase RMS." (4.1 Phase results)
   - assumption: Gaussian random phase noise  
  > "where $\phi_{rms}$ (in radians) is assumed to be Gaussian random phase noise occurring during the observations of the targeted source" (Troposphere and its effects)
   - fitting: _not stated_
   - validation: _not stated_
4. **Correlate scaling with weather**: Spearman rank correlation of scaling factors against weather parameters  
  > "The Spearman rank correlation coefficients ($\rho$) are $-$0.38, $-$0.39, and $-$0.76 for pressure, temperature, and PWV" (4.1.1 Scaling relationship with conditions)
   - fitting: _not stated_
   - validation: Significance from Ramsey 1989 tables  
  > "For the 75 datasets a correlation $\rho$ of $\pm$0.355 is significant at the 99.9 percent level (Table 3 of (cite: Ramsey1989))" (Water vapour radiometer scaling relationship with conditions)
5. **Image bandpass and science targets with and without scaling**: Re-run reduction with scaling in wvrgcal; compare peak flux (dirty) and S/N (cleaned) of scaled vs standard  
  > "Subsequently the delivered reduction scripts were edited to implement the scaling in the wvrgcal routine and then re-run." (Observations and reduction)
   - software: CASA, wvrgcal
   - fitting: _not stated_
   - validation: Same number of clean iterations for both images; noise measured in same regions  
  > "We clean automatically to allow each image made with the normal WVR or scaled WVR calibrated data to be cleaned by the same number of iterations" (4.2.3 Science targets)

## Software

- **CASA** : Calibration, WVR application, imaging  
  > "following the reduction scripts supplied with the SV data via casa" (Observations and reduction)
- **wvrgcal** : Computing WVR phase solutions with scale factor  
  > "The scale factor is introduced in the wvrgcal code" (Introduction)
- **custom python package (alma-allegro WVR scaling)** : Phase extraction, TPD statistics and scaling optimisation  
  > "are fully automated in our python package created for the ALMA community" (3.2 Data processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EBs with TPD improvement | 62 of 75 | not stated | EBs | 2 | There are 62 EBs of the 75 that indicate the TPD statistic of the phase fluctuation is improved |
| EBs with coherence improvement (full bandpass) | 39 of 75 | not stated | EBs | 3 | 39 of the total 75 EBs, have a coherence improvement |
| EBs with coherence improvement over 60 s | 12 | not stated | EBs | 3 | only 12 EBs indicate there is an improvement on shorter timescales |
| Optimal scaling factor range (6 and 12 s) | ~0.6 to ~2.0 | not stated | dimensionless | 2 | The scaling factors we find vary from $\sim$0.6 to $\sim$2.0 for ($T$= 6 and 12 s). |
| Spearman rho scaling vs PWV | -0.76 | not stated | dimensionless | 4 | $-$0.38, $-$0.39, and $-$0.76 for pressure, temperature, and PWV, respectively |
| Bandpass images improved | 33 of 39 | not stated | EBs | 5 | there are 33 that have image improvements (25 of these $>$5%) |
| Science images with S/N improvement | 23 of 33 | not stated | EBs | 5 | a reduced number of 23 show science target image improvements, in terms of S/N. |
| Scaling factor for EB X760 (12 s) | 1.42 | not stated | dimensionless | 2 | scaled WVR solution, factor 1.42, applied to the raw data |

## Qualitative findings

- Bands 6 and 7 respond to scaling; bands 3 and 4 do not; scaling larger in low-PWV (<1 mm) stable conditions  
  > "bands 6 and 7 respond to the WVR scaling, whereas lower frequencies (bands 3 and 4), which already have good phase coherence, do not." (Summary)

## Claim tuples

- H: Standard WVR solutions are not optimal and scaling improves phase correction | E: TPD minimisation over scaling factors for 75 EBs | R: Optimal factor generally not unity; 62/75 improve TPD | F: Scaling improves phase statistics in most EBs | **supported**
- H: Scaling improves image quality | E: Compare scaled vs standard images of bandpass and science targets | R: 33/39 bandpass and 23/33 science images improved, typically 1-2% S/N | F: Gains modest for science targets, larger for bandpass | **partially**
- H: Scaling factor depends on weather conditions | E: Spearman correlations | R: Correlation with PWV (-0.76), strongest at PWV<1 mm; none with wind, humidity etc. | F: Lower PWV needs larger scaling; cause possibly dry-wet air mixing | **partially**

## Reasoning

- Why this data: Public SV long-baseline data with bandpass calibrators observed ~5 min allow TPD analysis  
  > "for all science datasets the observation of the QSO at the start of the observations, targeted as the bandpass calibrator, can be used for a similar analysis." (3 Methodology)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Bandpass calibrator is not co-located with science target; short observations; weather from a single station; cause of scaling undetermined  
  > "in these SV data we only have access to parameters from a single ground-based weather station data" (5.1.2)
- Caveat (inferred, ours): Improvement for science targets is small and some may be within noise
- Caveat (inferred, ours): Scaling derived on the same bandpass phases used to assess improvement
- Caveat (inferred, ours): SV data are unrepresentatively good

## Reproducibility

- Data public (paper): Publicly available SV data  
  > "publicly available ALMA Science Verification (SV) observations" (Observations and reduction)
- Products in archive: _not stated_
- Code: Python code at alma-allegro.nl WVR scaling page  
  > "python code: http://www.alma-allegro.nl/wvr-and-phase-metrics/wvr-scaling/" (footnote)
- Missing: CASA version and wvrgcal options
- Missing: Science imaging parameters (only in SV scripts)
- Data volume (inferred): Large: 75 EBs, likely several TB
- Score (inferred): 3/5, Public data and released code, but imaging and calibration details deferred to SV scripts and CASA version missing.
- Rediscovery candidate: yes, Public data, released code, numeric results in tables.

## Links

- Method: Nikolic et al. 2013 (cite: Nikolic2013) (WVR correction and wvrgcal)
- Method: McKinnon 1988 (cite: McKinnon1988) (Two-point deviation definition)
- Companion: Matsushita et al. 2017 (cite: Matsushita2017) (Atmospheric phase characteristics from the ALMA long-baseline campaign)
- Related: ALMA Long Baseline Campaign science verification

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 30,
  "rate": 0.39
 },
 "evidence_ok": true
}
```
