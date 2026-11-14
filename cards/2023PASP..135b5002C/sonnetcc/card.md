# A Characterization of the ALMA Phasing System at 345 GHz

`2023PASP..135b5002C` | Publications of the Astronomical Society of the Pacific 2023 | first author: Crew, G. B. | arXiv: 2301.04543 | DOI: 10.1088/1538-3873/acb348

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation
- Question: How well does the ALMA phasing system (APS) perform at 345 GHz (Band 7), and how do weather, array size and baseline length affect phasing efficiency?  
  > "Here we present a characterization of the performance and phasing efficiency of the APS at 345 GHz based on test sessions conducted between 2015 March and 2021 September." (Introduction)
- Target **3C454.3**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **CTA102**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **BL Lac**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J0423-0120**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J0510+1800**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J0522-3627**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **3C273**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1924-2914**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00019.CSV, 2018.1.00005.CSV, 2018.1.00006.CSV, 2018.1.00007.CSV
- bands: Band 7 (0.87 mm, 345 GHz) phasing tests; Band 6 (1.3 mm) blocks for comparison  
  > "Testing and characterization of the performance of the APS for use in Band 7 were done using a combination of ALMA standalone tests and a global VLBI campaign." (Observations); "A total of six ALMA scheduling blocks were built and executed" (2.2 The 2018 Global VLBI Test Campaign)
- frequencies and spectral setup: Band 7 SPW centres 335.5, 337.5, 347.7, 349.7 GHz, 120 channels of 15.625 MHz; Band 6 240 channels of 7.8125 MHz; 4.032 s correlator time resolution  
  > "| 7 (0.85 mm) | 335.5   | 337.5   | 347.7   | 349.7   | 15.625      | 120       | 4.03        |" (Table 3); "In Band 6 there were 240 channels per SPW (resulting in a channel spacing of 7.8125 MHz)." (Observational Setup); "The spectral data from the ALMA Baseline Correlator are available with a time resolution of 4.032 s." (Observational Setup)
- continuum bandwidth: four SPWs, each 1875 MHz wide  
  > "The spectral setup included four spectral windows (SPWs), each with a bandwidth of 1875 MHz, that were processed by the ALMA Baseline Correlator." (Observational Setup)
- arrays: 12 m antennas only (23-29 phased in the 2018 campaign)  
  > "Only 12 m antennas were included in the array;" (Observational Setup)
- configurations: 2018: transition from C43-6 (max baseline 2500 m) to C43-5 (max baseline 1400 m)  
  > "the ALMA antennas were in transition from configuration C43-6 (maximum baseline 2500 m) to C43-5 (maximum baseline 1400 m)" (Observational Setup)
- baselines: 2018 campaign: phasing radius limited to 300 m, with outlying antennas (max baselines 1400-2500 m) withheld as comparison antennas  
  > "There were 23–29 12 m antennas included in the ALMA phased array (depending on the session), with a phasing radius limited to 300 m." (Observational Setup)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: standalone tests lasted from a few minutes up to 40 minutes  
  > "typically lasted from a few minutes up to 40 minutes" (2.1 Initial Testing: ALMA Standalone Observations)
- observing dates: standalone tests 2015 March to 2021 September; global VLBI test campaign 2018 October 17-21  
  > "based on test sessions conducted between 2015 March and 2021 September" (Introduction); "APS operations at 345 GHz were characterized during a series of four observing windows from October 17–21." (2.2 The 2018 Global VLBI Test Campaign)
- pi or archival as stated: ALMA EOC/Engineering time tests and CSV data; ALMA Cycle 5 North America Development award  
  > "These observations were conducted during ALMA Extension and Optimization of Capabilities (EOC) time or Engineering time" (2.1 Initial Testing: ALMA Standalone Observations); "This work was supported by an ALMA Cycle 5 North America Development award" (Acknowledgments)
- Other facility **Event Horizon Telescope (global VLBI partner sites)**: Global VLBI test campaign in 2018 October that produced the first 345 GHz VLBI fringes (described in Paper II)  
  > "The data sets include observations obtained in 2018 as part of a multi-day global VLBI test campaign that produced for the first time VLBI fringes in the 345 GHz band" (Introduction)
- Other facility **ALMA Compact Array (ACA) Grid Source monitoring**: Archival flux densities of bright quasars used to check the Band 7 flux scale  
  > "Most of the target quasars are routinely observed at ALMA as part of the flux-density monitoring program with the ALMA Compact Array (ACA)." (2.1 Initial Testing: ALMA Standalone Observations)
- Other facility **AMAPOLA polarimetric Grid Sources**: Stokes parameters of J0510+1800 and J0522-3627 used for the polarization model  
  > "we could estimate their Stokes parameters using the AMAPOLA" (Polarization Calibration)
- Other facility **ALMA Calibrator Source Catalogue**: Recent 230 and 345 GHz flux densities for cross-comparison  
  > "recent flux density measurements at 230 and 345 GHz were available from the ALMA Calibrator Source Catalogue." (Observed Targets)
- External data: Archival Grid Source flux densities at the time and frequency of the VLBI observations (retrieved from the ALMA archive)  
  > "The expected flux density of Grid Sources at a given time and frequency are retrieved from the ALMA archive" (Accuracy of the Absolute Flux-density Scale) [from ALMA archive Grid Source monitoring (ALMA Technical Handbook, cite: Remijan2019)]
- External data: Aperture efficiency of a 12 m ALMA dish in Band 7: 0.63  
  > "For a 12 m ALMA dish in Band 7, $\eta_{A}$=0.63 (cite: Remijan2019)." (SEFD) [from (cite: Remijan2019)]
- External data: Stokes parameters of J0510+1800 at Band 7 from AMAPOLA monitoring  
  > "we could estimate their Stokes parameters using the AMAPOLA" (Polarization Calibration) [from AMAPOLA polarimetric Grid Source monitoring (footnote URL, no cite key)]

## Processing

### Calibration

- pipeline or manual: manual CASA calibration following the VLBI QA2 procedure (modified)  
  > "we have calibrated the ALMA data using the Common Astronomy Software Applications (casa) package (cite: CASA2022)" (Calibration of the 2018 VLBI Campaign Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C454.3 (only Grid Source observed in both Bands 6 and 7)  
  > "The absolute flux-density scale was derived from self-calibration on 3C454.3." (Absolute Flux-density Scale)
- flux scale uncertainty: nominal Band 7 uncertainty about 10%; CTA102 16% lower and J0522-3627 13% higher than archival  
  > "The nominal calibration uncertainty at ALMA in Band 7 is $\sim$10% (see ALMA Technical Handbook" (Accuracy of the Absolute Flux-density Scale); "with the exception of CTA102 (with a 16% lower flux)" (Accuracy of the Absolute Flux-density Scale); "(with a 13% higher flux)" (Accuracy of the Absolute Flux-density Scale)
- self calibration: amplitude scale from self-calibration on 3C454.3; opacity correction applied right after gain calibration  
  > "The absolute flux-density scale was derived from self-calibration on 3C454.3." (Absolute Flux-density Scale); "Here we have followed a similar approach, except that the opacity correction is applied to the data right after the gain calibration" (Absolute Flux-density Scale)

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
- primary beam correction: not applied to the test images  
  > "The correction for the attenuation of the primary beam is not applied to these maps." (Interferometric Test Images)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: synthesized beam of roughly 0.45 arcsec  
  > "have a synthesized beamsize of roughly 0$\rlap{.}^{\prime\prime}$45" (Interferometric Test Images)
- final rms: _not stated_

### Inherited from earlier work

- Calibration of the 2018 data uses a modified version of the VLBI QA2 procedure  
  > "using a modified version of the procedure described in (cite: QA2Paper)" (Calibration of the 2018 VLBI Campaign Data) [from (cite: QA2Paper)]
- Extra cross-hand delay correction added relative to the QA2 polarization procedure  
  > "We therefore included this additional correction with respect to the procedures outlined in Section 5 of (cite: QA2Paper)." (Polarization Calibration) [from (cite: QA2Paper)]
- Test imaging of the VLBI targets follows earlier procedures  
  > "following the same procedures outlined in (cite: Goddi2021)" (Interferometric Test Images) [from (cite: Goddi2021)]
- Flux densities from the images estimated by the earlier methods  
  > "following the methods outlined in (cite: Goddi2021)" (Interferometric Test Images) [from (cite: Goddi2021)]
- Definition of phasing efficiency and the original APS efficiency requirement  
  > "As described in (cite: APPPaper), for an idealized phased array, a phasing efficiency" (Concerning Phasing Efficiency) [from (cite: APPPaper)]

### Not stated but needed to reproduce (our reading)

- CASA version used for the QA2-style calibration
- Complete QA2 script (flagging of the phase-up intervals, bandpass and gain solints, reference antenna choice)
- Exact imaging parameters for the test images (task, weighting, cell, image size, deconvolution, masks)
- How the per-baseline phase RMS values in Table 6 and Figure 6 were computed (averaging time, flagging, antenna selection)
- How the 2018 data from Oct 16/17 were excluded in detail (scan lists)
- WVR correction (wvrgcal) parameters used for the off-line test
- Source of the assumed 3C454.3 flux density and spectral index (3.53 Jy at 343 GHz, alpha=-0.69)
- How TelCal efficiency and quality values were extracted from the ASDM metadata
- Beam, rms and peak flux values of the test images

## Analysis recipe

1. **Extract APS phasing efficiency and quality per correlator subscan**: Read TelCal-computed eta_v and phasing quality from the ASDM metadata, averaged over basebands, and plot per correlator subscan  
  > "For monitoring purposes, this quantity is computed by TelCal for a designated comparison antenna and can be extracted from the archival science data model (ASDM) file metadata (cite: QA2Paper)." (APS Performance Metrics)
   - software: TelCal
   - parameter: eta_v averaged over polarizations and basebands  
  > "Phasing efficiency, averaged over polarizations and basebands" (Table 1 notes)
   - parameter: quality metric runs from 0 (no solution) to 1 (excellent fit), built from the RMS of the phase residuals  
  > "and assumes values ranging between 0 (no solution) to 1 (excellent fit)" (APS Performance Metrics)
   - fitting: _not stated_
   - validation: Quality metric used to separate rapid water-vapour variations (low eta_v, quality near 1) from wind-limited sessions (low eta_v, quality much less than 1)  
  > "The contrast between these days and the first two makes clear that the quality metric is a useful discriminator between different causes of low-phasing efficiency." (APS Performance Metrics)
2. **Inspect correlated amplitude and phase versus time on baselines to the sum antenna**: Plot amplitude and phase of visibilities on baselines from reference and sum antennas to unphased comparison antennas and judge phasing against the ideal sqrt(N_phased) gain  
  > "For an optimally phased array, the correlated amplitude of (ii) should ideally improve by a factor of" (APS Performance Metrics)
   - fitting: _not stated_
   - validation: On October 21 nearly ideal phasing performance is seen  
  > "Finally on October 21 nearly ideal phasing performance is seen." (APS Performance Metrics)
3. **Relate phasing efficiency to PWV and wind speed**: Plot eta_v and quality versus wind speed for every data set, colour-coded by PWV  
  > "To obtain a preliminary assessment of how the combination of wind speed and PWV affects phasing performance at 345 GHz, we plot in Figure 4 the phasing efficiency" (Impact of Weather Conditions)
   - parameter: PWV split at 2.0 mm (red at or above, black below)  
  > "Data points with PWV$\ge$2.0 mm are shown in red and data with PWV$<$2.0 mm are shown in black." (Impact of Weather Conditions)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test the expected benefit of fast WVR-based phasing corrections off-line**: Apply WVR-derived corrections to individual antennas and compare phase coherence on single baselines  
  > "we have investigated the expected impact of such corrections by applying WVR-derived corrections off-line to the individual elements of the phased array" (Impact of Weather Conditions)
   - software: CASA, wvrgcal
   - assumption: Fast corrections cannot be applied in post-processing to the phased sum, so only single-baseline coherence is evaluated  
  > "Since the phased sum is formed in real time, it is not possible to use the fast corrections in post-processing to improve the SNR" (Impact of Weather Conditions)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare phase dispersion for different maximum baseline lengths**: Compare RMS phase dispersion versus uv distance for three tests with maximum baselines of 180 m, 1500 m and 6900 m taken at similar PWV  
  > "we find that the RMS dispersion in the phases for all baselines in the phased array is significantly higher in the B1500 data (69 deg) and the B6900 data (55 deg) compared with the B180 data (16 deg)" (Impact of Array Size and Maximum Baseline Length)
   - parameter: single correlation quadrant SPW=0 and XX polarization  
  > "Considering the single correlation quadrant (SPW=0) and polarization (XX) that is plotted for each data set" (Impact of Array Size and Maximum Baseline Length)
   - fitting: _not stated_
   - validation: Repeated with baselines under 200 m only  
  > "This is true even if we limit our comparison to baselines" (Impact of Array Size and Maximum Baseline Length)
6. **Compare Band 6 and Band 7 phasing performance**: Compare phase fluctuations on J0522-3627 in each band within one session (2017 Feb 1) and check 2018 Oct 18 data  
  > "The RMS phase fluctuations for all phased baselines were 43 deg in Band 6 and 36 deg in Band 7." (Comparison between Band 6 and Band 7)
   - assumption: Differences are attributed to PWV and source elevation because the scans were not co-temporal  
  > "those differences can be ascribed to changes in PWV, coupled with changes in the source elevation" (Comparison between Band 6 and Band 7)
   - fitting: _not stated_
   - validation: A preliminary analysis of the 2018 data gave similar conclusions  
  > "We reach similar conclusions from a preliminary analysis on the 2018 test dataset." (Comparison between Band 6 and Band 7)
7. **Calibrate the 2018 campaign data (QA2-style)**: Concatenate the 2018 October data, flag days 16 and 17, compute bandpass and polarization tables from Oct 21 and apply to all; flux scale from 3C454.3; polarization via J0510+1800 model plus cross-hand delay correction  
  > "we concatenated the data collected in 2018 October into a single dataset." (Calibration of the 2018 VLBI Campaign Data); "We set J0510+1800 as the polarization calibrator" (Polarization Calibration)
   - software: CASA, gaincal, polcal
   - parameter: Oct 21 data used for bandpass and polarization calibration tables  
  > "the latter yielded the highest-quality data and were used to compute the bandpass and polarization calibration tables" (Calibration of the 2018 VLBI Campaign Data)
   - assumption: Sources stable over 2.5 days  
  > "under the assumption that the observed sources are stable over a time interval of 2.5 days" (Calibration of the 2018 VLBI Campaign Data)
   - assumption: 3C454.3 at 343 GHz is 3.53 Jy with spectral index -0.69  
  > "For this purpose, $S^P_{343 GHz} = 3.53$ Jy and $\alpha$=–0.69 was assumed." (Absolute Flux-density Scale)
   - fitting: _not stated_
   - validation: _not stated_
8. **Check the absolute flux-density scale against ACA Grid Source values**: Measure VLBI-target flux densities per SPW in the uv-plane with a point-source model and compare with archival Grid Source values  
  > "We have performed a similar analysis for the Grid Sources observed in Band 7." (Accuracy of the Absolute Flux-density Scale); "which adopts a point-source model (this assumption is valid since Grid Sources are unresolved on ALMA baselines)" (Accuracy of the Absolute Flux-density Scale)
   - software: CASA, fluxscale, CASA analysis utils
   - assumption: Grid Sources are unresolved on ALMA baselines  
  > "this assumption is valid since Grid Sources are unresolved on ALMA baselines" (Accuracy of the Absolute Flux-density Scale)
   - fitting: _not stated_
   - validation: Most estimates agree with archival values within the nominal Band 7 uncertainty  
  > "most of our new flux density estimates are consistent with the archival values to within this range" (Accuracy of the Absolute Flux-density Scale)
9. **Image the VLBI targets as a quality test**: Produce images from fully calibrated visibilities following Goddi et al. 2021 and run self-consistency tests  
  > "we have produced images of the VLBI targets from fully-calibrated ALMA interferometric visibilities (see Appendix A), following the same procedures outlined in (cite: Goddi2021)" (Interferometric Test Images)
   - software: CASA
   - assumption: Targets are point-like on the sampled scales  
  > "We first assessed that the images are consistent with unresolved point sources (as expected for the selected VLBI targets)" (Interferometric Test Images)
   - fitting: Gaussian fit to compare source size with synthesized beam  
  > "We then established that the size determined from a Gaussian fit matches the size of the synthesized beam" (Interferometric Test Images)
   - validation: Image-based flux densities consistent with uv-plane estimates within about 10% (Oct 18/19) and about 5% (Oct 21)  
  > "assessed that they are consistent with the values estimated in Table" (Interferometric Test Images)
10. **Derive DPFU, Tsys and SEFD of phased ALMA in Band 7**: Set phased-ALMA DPFU to the antenna-wise average of single-antenna DPFUs computed from QA2 gains and Tsys; derive effective phased-array Tsys for ANTAB files; compute SEFD = Tsys/DPFU  
  > "In order to keep the DPFU of phased ALMA constant over a given observation (for calibration purposes), we set the DPFU of phased ALMA to the antenna-wise" (DPFU)
   - software: CASA, AIPS
   - parameter: DPFU from Oct 21 data  
  > "Using the data collected on October 21 (which have higher quality), we estimate DPFU = 0.011 K/Jy." (DPFU)
   - assumption: Aperture efficiency 0.63 for a 12 m dish in Band 7  
  > "For a 12 m ALMA dish in Band 7, $\eta_{A}$=0.63 (cite: Remijan2019)." (SEFD)
   - assumption: Phased array of 29 antennas of 12 m diameter  
  > "Assuming a phased array of 29 antennas of 12 m diameter" (SEFD)
   - fitting: _not stated_
   - validation: Measured SEFD compared with the theoretical value scaled by 90% efficiency  
  > "close to the estimate from the QA2 gain calibration" (SEFD)
11. **Validate the polarization model of J0510+1800**: Rerun polcal with 17 alternative models (polarized flux scaled by 0.25-2.0, position angle shifted by +/-10 to 50 deg) and compare D-term channel dispersion  
  > "To evaluate the goodness of the AMAPOLA model for J0510+1800, we ran the" (Assessment of the Polarization Calibration model); "we considered the following 17 alternative models" (Assessment of the Polarization Calibration model)
   - software: CASA, polcal
   - fitting: _not stated_
   - validation: All deviations from the AMAPOLA model worsened the D-terms  
  > "We found that deviations from the AMAPOLA model always resulted in a deterioration of the D-terms of the phased-antennas" (Assessment of the Polarization Calibration model)

## Software

- **CASA** : Calibration (QA2-style), WVR corrections, polarization and flux calibration, imaging  
  > "we have calibrated the ALMA data using the Common Astronomy Software Applications (casa) package (cite: CASA2022)" (Calibration of the 2018 VLBI Campaign Data)
- **TelCal** : Online phasing engine; computes phasing efficiency and quality  
  > "this quantity is computed by TelCal for a designated comparison antenna" (APS Performance Metrics)
- **CASA analysis utils** : Retrieve archival Grid Source flux densities with getALMAflux()  
  > "via the `getALMAflux()` function implemented in the `CASA analysis utils`" (Accuracy of the Absolute Flux-density Scale)
- **AIPS** : Reads the ANTAB amplitude-calibration files used in VLBI  
  > "readable by the Astronomical Image Processing System (AIPS) task" (Tsys and ANTAB files)
- **AMAPOLA** : Polarimetric Grid Source monitoring used to set the J0510+1800 polarization model  
  > "we could estimate their Stokes parameters using the AMAPOLA" (Polarization Calibration)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Phasing efficiency eta_v on 2018 Oct 21 | above 90% | not stated | dimensionless | 1 | the APS has achieved 90% phasing efficiency on October 21; the estimated phasing efficiency reported by TelCal was consistently $>$90%, and frequently above 95% |
| eta_v in Band 7 when PWV exceeds 2.0 mm | generally below about 50% | not stated | dimensionless | 3 | when PWV$>$2.0 mm, phasing efficiency in Band 7 generally falls below $\sim$50% |
| eta_v when wind speed exceeds about 10 m/s | consistently quite low (about 20% or less) | not stated | dimensionless | 3 | phasing efficiency is consistently quite low |
| RMS phase dispersion, all baselines (B180 / B1500 / B6900) | 16 / 69 / 55 | not stated | deg | 5 | significantly higher in the B1500 data (69 deg) and the B6900 data (55 deg) compared with the B180 data (16 deg) |
| RMS phase dispersion, baselines under 200 m (B180 / B1500 / B6900) | 16 / 35 / 39 | not stated | deg | 5 | in this case the RMS phase dispersions are 35 deg (B1500), 39 deg (B6900) and 16 deg (B180) |
| RMS phase fluctuation on J0522-3627, Band 6 / Band 7 (2017 Feb 1) | 43 / 36 | not stated | deg | 6 | The RMS phase fluctuations for all phased baselines were 43 deg in Band 6 and 36 deg in Band 7. |
| Single-antenna DPFU, Band 7 phased ALMA (Oct 21) | 0.011 | not stated | K/Jy | 10 | we estimate DPFU = 0.011 K/Jy |
| DPFU of a 29-antenna phased array | 0.32 | not stated | K/Jy | 10 | The DPFU for a phased array of 29 antennas would be: (DPFU)$_{29}$ = 0.32 K/Jy. |
| Median phased-array Tsys, Oct 21 | 2.6 | not stated | K | 10 | the median of the phased-array $T_{\rm sys}$ values measured on October 21 (2.6 K) |
| SEFD of phased ALMA, Band 7, Oct 21 | 238 | not stated | Jy | 10 | one derives SEFD = 238 Jy in Band 7 |
| Theoretical SEFD, 29 antennas, Tsys 155 K | 207 | not stated | Jy | 10 | one derives SEFD$_{\rm th}$ = 207 Jy |
| SEFD on Oct 18/19, Band 6 and Band 7 | 150 (Band 6), 578 (Band 7) | not stated | Jy | 10 | provides SEFD = 150 Jy in Band 6 and SEFD = 578 Jy in Band 7 |
| Flux difference from archival value, CTA102 and J0522-3627 | 16% lower (CTA102), 13% higher (J0522-3627) | not stated | percent | 8 | with the exception of CTA102 (with a 16% lower flux); (with a 13% higher flux) |
| APS sum-signal delay | 24 lags (192 ns), about 20% loss in correlated amplitude | not stated | lags / ns | 0 | it arrives with a 24-lag delay (192 ns) |

## Qualitative findings

- Off-line WVR corrections did not improve phase coherence for the Oct 16/17 data and added noise, suggesting that wind-induced turbulence as well as water vapour caused the rapid fluctuations  
  > "We find, however, that for the October 16/17 data the WVR-based corrections do not improve the overall phase coherence; instead they appear to add additional noise." (Impact of Weather Conditions)
- Including long baselines in the phased array degrades the least-squares phasing solutions  
  > "too many noisy baselines (typically those longer than a few hundred meters) will impact the overall quality of the phasing solutions" (Impact of Array Size and Maximum Baseline Length)
- The 24-lag delay of the sum signal explains the previously unaccounted ~20% efficiency loss  
  > "Subsequent investigation has now uncovered the source of this additional loss" (Concerning Phasing Efficiency)

## Claim tuples

- H: Can ALMA act as an effective phased array at 345 GHz? | E: Standalone phasing tests and the 2018 global VLBI campaign, measuring eta_v versus PWV and wind | R: eta_v reached about 90% or more on Oct 21 (PWV about 0.8 mm, low wind); below about 50% for PWV above 2 mm | F: Under PWV about 2 mm or lower and wind below 10 m/s, phased ALMA works with eta_v of about 0.5 or better | **supported**
- H: Does high wind limit Band 7 phasing? | E: Plot eta_v and quality versus wind speed for all test data | R: eta_v is low and quality declines for wind above about 10 m/s | F: Band 7 phased observations should be avoided in high wind | **supported**
- H: Does a larger phased array hurt phasing efficiency? | E: Compare phase dispersion for maximum baselines of 180 m, 1500 m and 6900 m | R: Phase RMS 16, 69 and 55 deg, and 16, 35, 39 deg for baselines under 200 m | F: Limit the phased array to a few hundred metres | **supported**
- H: Is Band 7 phasing performance worse than Band 6? | E: Compare phase fluctuations in both bands within single sessions | R: 43 deg (Band 6) versus 36 deg (Band 7) on 2017 Feb 1 | F: No appreciable loss in Band 7, though comparison data are limited | **partially**
- H: Are the QA2-style calibrated Band 7 phased data scientifically usable? | E: Flux-scale comparison with Grid Sources and point-source image checks | R: Most fluxes within about 10% of archival; images consistent with point sources | F: Calibration is sound enough for combination with other VLBI stations | **supported**

## Reasoning

- Why this data: Tests span different arrays and weather, allowing the effect of array parameters and conditions to be studied  
  > "this allows us to begin to investigate how different array parameters, weather conditions, and other variables affect APS performance in Band 7." (Variables Impacting Phased Array Performance in Band 7)
- Why this method: eta_v is independent of the phased sum, so free of quantization and 24-lag losses  
  > "Because this definition is not computed based on the phased sum signal, it is free from losses due to quantization and the 24-lag delay." (Concerning Phasing Efficiency)
- Alternative: Real-time fast WVR phasing corrections were not used in 2018; their benefit was only estimated off-line  
  > "These real-time fast corrections were not used during the 2018 October observations" (Impact of Weather Conditions)
- Alternative: Sum-antenna efficiency eta_p is used only qualitatively; eta_v is the quantitative metric  
  > "we limit the use of the phasing efficiency" (Concerning Phasing Efficiency)
- How they decided it was enough: _not stated_
- Limitation (authors): 2018 data were engineering tests without a full suite of calibrators  
  > "a full suite of calibrators was not observed" (Additional Assessments of Phased Array Data Quality)
- Limitation (authors): Band 6 and Band 7 comparison data are limited and not co-temporal  
  > "as the observations we compare here were not co-temporal" (Comparison between Band 6 and Band 7)
- Limitation (authors): Targets observed on earlier days were excluded because of poor weather  
  > "targets observed on previous days were not included in the analysis owing to poor weather conditions" (Observed Targets)
- Caveat (inferred, ours): Efficiency-versus-weather conclusions rest on a small number of heterogeneous test sessions with confounded array size, elevation and weather
- Caveat (inferred, ours): No uncertainties are given on eta_v, phase RMS or SEFD values
- Caveat (inferred, ours): The threshold values (PWV 2 mm, wind 10 m/s) are read off a scatter plot without a formal fit
- Caveat (inferred, ours): Flux-scale check relies on ACA values taken up to 71 days apart for BL Lac

## Reproducibility

- Data public (paper): datasets identified by ALMA archive UIDs; public release status not stated  
  > "Unique identifier (UID) of the data set in the ALMA Archive." (Table 1 notes)
- Products in archive: QA2 calibration tables produced for the 2018 data  
  > "These tables can be used to fully calibrate the ALMA interferometric visibilities" (Validation of the APS Calibration)
- Missing: Access to ASDM metadata with TelCal efficiency and quality values
- Missing: QA2 scripts and flagging choices
- Missing: Phase RMS computation details
- Missing: Imaging parameters for the test images
- Missing: Public release status of the CSV and engineering data
- Data volume (inferred): Roughly 100-300 GB for the ~22 scheduling blocks (4 SPWs, 120-240 channels, 4 s integrations, 23-45 antennas, 8-90 min each); tens of GB if only the 2018 Oct 18/19 and 21 blocks are used
- Score (inferred): 2/5, Main results are numeric but depend on TelCal metadata and a QA2 procedure not fully specified; imaging and phase RMS procedures are not given
- Rediscovery candidate: no, Recipe is incomplete (no QA2 scripts, phase RMS method, or imaging parameters) and key efficiency values come from online system metadata

## Links

- Method: (cite: QA2Paper) Goddi et al. 2019, PASP 131, 075003 (Defines the QA2 VLBI calibration procedure the 2018 calibration modifies)
- Method: (cite: APPPaper) Matthews et al. 2018, PASP 130, 015002 (Describes the ALMA Phasing System and the efficiency definitions)
- Method: (cite: Goddi2021) (Source of the imaging and flux-density procedures for the test images)
- Method: (cite: CASA2022) (Describes CASA)
- Companion: Event Horizon Telescope Collaboration et al., in preparation (Paper II) (Reports the 345 GHz VLBI fringe detections from the 2018 campaign)
- Related: Event Horizon Telescope
- Related: Global mm-VLBI Array
- Related: ALMA Phasing Project
- Related: ALMA ACA Grid Source flux monitoring
- Related: AMAPOLA

## Checks

```json
{
 "quotes": 118,
 "quotes_ok": 118,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00019.CSV",
  "2018.1.00005.CSV",
  "2018.1.00006.CSV",
  "2018.1.00007.CSV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 136,
  "stated": 79,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
