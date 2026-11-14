# The 2014 ALMA Long Baseline Campaign: An Overview

`2015ApJ...808L...1A` | The Astrophysical Journal Letters 2015 | first author: ALMA Partnership | arXiv: 1504.04877 | DOI: 10.1088/2041-8205/808/1/L1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation
- Question: Can ALMA make accurate images at tens-of-mas resolution on baselines up to ~15 km, and what limits phase coherence and astrometry at long baselines?  
  > "A major goal of the Atacama Large Millimeter/submillimeter Array (ALMA) is to make accurate images with resolutions of tens of milliarcseconds, which at submillimeter (submm) wavelengths requires baselines up to $\sim$15 km." (abstract)
- Target **3C138**: coordinates 05h21m09.9s +16d38m22s (J2000 phase center)  
  > "| 3C 138 | 05$^{h}$21$^{m}$09$^{s}$.9 +16$^{\ensuremath{^\circ}}$38$^{\ensuremath{'}}$22$^{\ensuremath{''}}$ |" (Table 2); "a redshift of 0.759 (cite: CO1997)" (ALMA Observations of 3C138); z/distance z = 0.759  
  > "| 3C 138 | 05$^{h}$21$^{m}$09$^{s}$.9 +16$^{\ensuremath{^\circ}}$38$^{\ensuremath{'}}$22$^{\ensuremath{''}}$ |" (Table 2); "a redshift of 0.759 (cite: CO1997)" (ALMA Observations of 3C138); distance from Cotton et al. 1997 (cite: CO1997)  
  > "| 3C 138 | 05$^{h}$21$^{m}$09$^{s}$.9 +16$^{\ensuremath{^\circ}}$38$^{\ensuremath{'}}$22$^{\ensuremath{''}}$ |" (Table 2); "a redshift of 0.759 (cite: CO1997)" (ALMA Observations of 3C138)
- Target **HL Tau**: coordinates 04h31m38.45s +18d13m59.0s  
  > "| HL Tau | 04$^{h}$31$^{m}$38$^{s}$.45 +18$^{\ensuremath{^\circ}}$13$^{\ensuremath{'}}$59$^{\ensuremath{''}}$.0 |" (Table 2); z/distance _not stated_; distance from _not stated_
- Target **SDP.81**: coordinates 09h03m11.61s +00d39m06.7s  
  > "| SDP.81 | 09$^{h}$03$^{m}$11$^{s}$.61 $+$00$^{\ensuremath{^\circ}}$39$^{\ensuremath{'}}$06$^{\ensuremath{''}}$.7 |" (Table 2); "a high-$z$ ($z$=3.042), gravitationally lensed, submm galaxy" (5 Science Verification); z/distance z = 3.042  
  > "| SDP.81 | 09$^{h}$03$^{m}$11$^{s}$.61 $+$00$^{\ensuremath{^\circ}}$39$^{\ensuremath{'}}$06$^{\ensuremath{''}}$.7 |" (Table 2); "a high-$z$ ($z$=3.042), gravitationally lensed, submm galaxy" (5 Science Verification); distance from _not stated_
- Target **Mira**: coordinates 02h19m20.79s -02d58m39.5s  
  > "| Mira | 02$^{h}$19$^{m}$20$^{s}$.79 -02$^{\ensuremath{^\circ}}$58$^{\ensuremath{'}}$39$^{\ensuremath{''}}$.5 |" (Table 2); z/distance _not stated_; distance from _not stated_
- Target **Juno**: coordinates ephemeris target  
  > "| Juno | ephemeris target | 6 | cont., ephemeris |" (Table 2); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00013.SV, 2011.0.00014.SV, 2011.0.00015.SV, 2011.0.00016.SV
- bands: Bands 3, 4, 6, 7 (SV targets); most tests at Band 3  
  > "Bands 3, 4, 6, & 7 correspond to frequencies of approximately 100 GHz, 140 GHz, 230 GHz & 340 GHz, respectively." (3C138 and Table 2); "Most test observations were made at 100 GHz (ALMA Band 3)." (2.2 LBC Test Strategy)
- frequencies and spectral setup: Continuum spws 2.0 GHz bandwidth, 15.6 MHz channels; line spws vary  
  > "Channel widths were 15.6 MHz for continuum windows, 2.0 GHz bandwidth." (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 21-23 antennas on 400 m-15 km baselines plus 6-12 antennas <300 m; total 22-36 antennas  
  > "The nominal LBC configuration consisted of 21–23 antennas on baselines of between 400 m and 15 km" (2.1 The LBC Array)
- baselines: _not stated_
- angular resolution: as fine as 19 mas at ~350 GHz (Band 7); 3C138 Band 6 37x23 mas  
  > "achieved angular resolutions as fine as 19 mas at $\sim$350 GHz" (abstract); "The resolution is 37$\times$23 mas in P.A. $-11^\circ$" (ALMA Observations of 3C138)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: LBC 2014 September to late November  
  > "a Long Baseline Campaign (LBC) was carried out from September to late November 2014" (abstract)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 43 GHz A-configuration image of 3C138 (16 Feb 2014, 45 min) for comparison  
  > "The VLA observations at 43 GHz were made on February 16, 2014 in the A-configuration, and the integration time on 3C138 was 45 min." (ALMA Observations of 3C138)
- External data: ALMA calibrator catalog and AT20G / VLA calibrator catalogs used as candidate sources for weak calibrator survey  
  > "observe candidate sources from the AT20G (cite: MA2011) and VLA calibrator catalogs" (4.3 Weak Calibrator Survey) [from Massardi et al. 2011 (cite: MA2011)]

## Processing

### Calibration

- pipeline or manual: 3C138 calibration, editing, imaging, self-cal done in obit rather than CASA  
  > "The standard phase referencing calibration, editing, imaging, and self-calibration for the ALMA and VLA data was carried out using the *obit* software package" (ALMA Observations of 3C138)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: J0510+1800 derived 1.20 Jy (97 GHz), 0.97 Jy (241 GHz); VLA: 3C48  
  > "The flux density scale for ALMA was based on the derived flux density of 1.20 Jy and 0.97 Jy (10% uncertainty) for J0510+1800 at 97 and 241 GHz, respectively." (ALMA Observations of 3C138)
- flux scale uncertainty: 10%  
  > "(10% uncertainty) for J0510+1800 at 97 and 241 GHz" (ALMA Observations of 3C138)
- self calibration: Self-calibration applied to 3C138 (rms down ~10x); limited for HL Tau, none for SDP.81  
  > "The rms noise level decreases about a factor of 10 from the phase referenced to the self-calibrated image." (Self-Calibration)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Astrometry: uniform weighting, spacings >1 km; 3C138 high-res image natural weight  
  > "Uniform weighting with only spacings longer than 1 km were used to obtain the highest resolution and most accurate positions." (4.4 Astrometric Accuracy); "The ALMA Band 6 image using the high resolution data at natural weight" (ALMA Observations of 3C138)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Data weighted to similar uv range then convolved with common Gaussian beam  
  > "each data set was weighted to include approximately the same range of spacings for each image, and then convolved with the above Gaussian beam size." (ALMA Observations of 3C138)
- final beam: 91x51 mas PA -13 deg for three-frequency comparison; 37x23 mas PA -11 deg for Band 6 high-res  
  > "same resolution (91$\times$51 mas in P.A. $-13^\circ$)" (ALMA Observations of 3C138)
- final rms: _not stated_

### Inherited from earlier work

- Details of Juno, HL Tau and SDP.81 observations and results given in companion papers  
  > "Further details of the Juno, HL Tau, and SDP.81 observations and results are given in three accompanying papers" (Table 2) [from ALMA Partnership et al. 2015a,b,c]
- SV imaging details given in a CASA guide  
  > "Details of the imaging of the SV targets, including important lessons learned, are described in a CASA guide page" (5 Science Verification) [from CASA guide ALMA2014_LBC_SVDATA]
- WVR system and PWV estimation described elsewhere  
  > "is given in (cite: NI2013)" (3.1 WVR correction) [from (cite: NI2013)]

### Not stated but needed to reproduce (our reading)

- obit task settings and parameters for 3C138 imaging and self-calibration
- Self-calibration solution intervals
- Exact uv ranges and weighting for common-resolution 3C138 images
- CASA version and pipeline used for SV data
- Which execution blocks were used for the 3C138 analysis
- Procedure for fitting the structure function slopes and Go/noGo thresholds

## Analysis recipe

1. **Measure short-term phase rms vs baseline (SSF)**: Source stares and Go/noGo observations; phase rms versus baseline with and without WVR correction  
  > "30-min observations of a single bright source to determine the temporal phase variation statistics as a function of baseline length" (2.2 LBC Test Strategy)
   - parameter: Go/noGo: 2-min Band 3 strong-quasar observation, rms averaged over 5-15 km baselines  
  > "consisting of a 2-min observation of a strong quasar at Band 3" (3.2 Go/noGo System)
   - assumption: Coherence loss exp(-sigma^2/2); rms <30 deg acceptable  
  > "the loss of coherence is acceptable and reasonably accurate image quality can be obtained if the rms phase fluctuations are $<30^\circ$." (3 Short-term Coherence)
   - fitting: _not stated_
   - validation: Go/noGo rms phase compared with phase-referenced image coherence  
  > "This demonstrates that the target image coherence is reasonably well correlated with the rms phase at the longer baselines of the calibrator." (3.2 Go/noGo System)
2. **Diagnose systematic phase errors from delay model**: Baseline observations fitted for antenna positions; residual phase versus elevation compared with and without per-antenna pressure estimates  
  > "After fitting for the best baseline, the residual fit, shown by the red points, contains a large residual phase versus elevation term." (4.2 Measurement of Delay Model Errors)
   - software: CALC
   - assumption: Zenith dry delay 0.228 P mbar; pressure at each antenna from lapse rate  
  > "The zenith dry air delay $\tau_i$ above antenna $i$ is accurately given by $\tau_i\approx 0.228P_i$" (4.1 The Delay Model)
   - fitting: _not stated_
   - validation: Residual phase vs elevation flat after lapse-rate correction  
  > "After the best baseline fit to the data, the residual phase versus elevation is flat." (4.2 Measurement of Delay Model Errors)
3. **Measure astrometric accuracy**: Phase-referenced images of quasar quartet; offsets from peak position; six epochs; mean and STD  
  > "the positional offset for each source was determined by the displacement of the quasar peak from the center of the image." (4.4 Astrometric Accuracy)
   - parameter: 1-min scans, Band 3, within 10 deg radius  
  > "observed sequentially with 1-min scans at Band 3" (4.4 Astrometric Accuracy)
   - fitting: _not stated_
   - validation: Compared with theoretical rms and predicted 0.18 mas  
  > "The predicted ALMA astrometric accuracy is $\sim$0.18 mas (Lestrade 2008)" (4.4 Astrometric Accuracy)
4. **Compare ALMA and VLA images of 3C138**: Calibrate, self-calibrate and image ALMA 97/241 GHz and VLA 43 GHz data in obit, convolve to common beam, compare images and spectral indices  
  > "The main conclusion is that the differences between the ALMA and VLA images are at the level of a few percent of their peak levels." (ALMA Observations of 3C138)
   - software: obit
   - parameter: Common beam 91x51 mas PA -13 deg; only Band 6 upper sideband used  
  > "only the upper sideband of the Band 6 data was used." (footnote 14)
   - fitting: _not stated_
   - validation: Agreement between ALMA and VLA images at few percent level  
  > "the agreement of the images to a few percent strongly suggests that both arrays can image the radio emission from the sky at tens of milliarcsecond resolution" (ALMA Observations of 3C138)

## Software

- **obit** : Calibration, editing, imaging and self-calibration of 3C138 ALMA and VLA data  
  > "was carried out using the *obit*[^15] software package (cite: CO2008)" (ALMA Observations of 3C138)
- **CASA** 4.2.2 or higher (possible): Alternative processing noted for ALMA data; SV imaging guide  
  > "Note that the ALMA data could have been processed in CASA 4.2.2 or higher" (footnote 15)
- **CALC** : Computing the correlator delay model  
  > "which is calculated using the CALC[^4] third-party software" (4.1 The Delay Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index of 3C138 core | -0.70 | 0.03 | dimensionless | 4 | respectively have spectral indices of $-0.70\pm
0.03$ and $-0.75\pm 0.05$ |
| Spectral index of 3C138 eastern jet/lobe | -0.75 | 0.05 | dimensionless | 4 | respectively have spectral indices of $-0.70\pm
0.03$ and $-0.75\pm 0.05$ |
| Spectral index of 3C138 western counter-jet | -0.95 | 0.13 | dimensionless | 4 | has a spectral index of $-0.95\pm 0.13$ |
| Nominal astrometric rms error | ~1.5 | not stated | mas | 3 | is an rms positional error of $\sim$1.5 mas |
| Best angular resolution | 19 | not stated | mas | 0 | Angular resolutions achieved were as fine as 19 mas (Band 7; 344 GHz |
| WVR phase noise improvement | ~2 | not stated | dimensionless | 1 | the WVR correction typically improves the phase noise by a factor of $\sim$2. |
| 3C138 sidelobe/peak at 241 GHz before to after self-cal | 17% to 0.6% | not stated | percent | 4 | For the 241 GHz image, the ratio drops from 17% to 0.6%. |

## Qualitative findings

- Systematic phase offsets between calibrator and target are dominated by inaccurate dry atmospheric delay model with only one pressure sensor.  
  > "Systematic phase differences between calibrator and science target are dominated mainly by the lack of an accurate dry atmospheric delay model." (6 Conclusions)

## Claim tuples

- H: ALMA can image accurately on baselines up to ~15 km | E: End-to-end SV observations of five targets with the LBC array | R: Resolutions as fine as 19 mas achieved | F: Long baseline science observations are now possible | **supported**
- H: ALMA images agree with VLA images at matched resolution | E: 3C138 at 97 and 241 GHz compared with VLA 43 GHz | R: Differences at few percent of peak | F: Both arrays image with this accuracy or better | **supported**
- H: Phase conditions can be predicted from weather parameters | E: Compared weather measurements with phase rms | R: Not reliably predictable | F: Go/noGo short observation of a strong quasar is recommended | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only one weather station available, degrading astrometry relative to predicted 0.18 mas  
  > "is likely the major cause of the poorer than expected astrometric accuracy observed during the LBC" (4.4 Astrometric Accuracy)
- Caveat (inferred, ours): 3C138 analysis is preliminary and uses obit, with few processing parameters given
- Caveat (inferred, ours): Astrometry based on only six epochs of one quasar quartet
- Caveat (inferred, ours): No quantitative uncertainty on the percent-level ALMA-VLA agreement

## Reproducibility

- Data public (paper): Public from ALMA Science Portal  
  > "The data is publicly available from the ALMA Science Portal" (Table 2)
- Products in archive: _not stated_
- Missing: obit scripts and parameters
- Missing: Go/noGo and phase rms analysis code
- Missing: Exact execution blocks for each analysis
- Data volume (inferred): Large (hundreds of GB to TB across all SV datasets)
- Score (inferred): 3/5, Data public but analysis details are sparse and many results are descriptive.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative or tied to non-archival test data.

## Links

- Method: Nikolic et al. 2013 (cite: NI2013) (WVR correction description)
- Companion: ALMA Partnership et al. 2015a,b,c (Juno, HL Tau, SDP.81 SV results)
- Related: 2014 ALMA Long Baseline Campaign
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 45,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
