# First Very Long Baseline Interferometry Detections at 870 μm

`2024AJ....168..130R` | The Astronomical Journal 2024 | first author: Raymond, Alexander W. | arXiv: 2410.07453 | DOI: 10.3847/1538-3881/ad5bdb

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: Can VLBI fringes be detected at 870 um (345 GHz) on inter-continental baselines with Event Horizon Telescope array stations (ALMA phased array, APEX, IRAM30m, SMA, GLT, NOEMA), and how do SNR, coherence and phase stability compare with 1.3 mm?  
  > "The experiment we describe was intended as a first technical demonstration of the 870  VLBI capability using facilities that are part of the Event Horizon Telescope (EHT) array." (Introduction); "The detections confirm that the sensitivity and signal chain stability of stations in the Event Horizon Telescope (EHT) array are suitable for VLBI observations at 870" (abstract)
- Target **Blazars and quasars observed in the 870 um fringe test (source names are missing from the supplied text)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01154.V, 2011.0.00010.E, 2011.0.00012.E
- bands: 870 um (345 GHz nominal); ALMA Band 7 cartridges  
  > "The present article reports the first fringe detections made at 870  wavelength (345 GHz nominal frequency)" (Introduction); "ALMA observed in dual linear polarization with IRAM designed 870" (ALMA)
- frequencies and spectral setup: four 2.048 GHz subbands centred at 335.6, 337.541406, 347.6 and 349.6 GHz at ALMA; most stations recorded one 2048 MHz band at 4-6 GHz IF with 342.6 GHz sky LO (346.552 to 348.6 GHz sky range); SMA LO 341.6 GHz  
  > "the four recorded 2.048 GHz subbands were tuned to center frequencies of 335.6, 337.541406, 347.6 and 349.6 GHz." (ALMA); "That frequency setup corresponds to a sky frequency range of 346.552 to 348.6 GHz." (Instrumentation and Array); "The sky LO was set to 341.6 GHz, not 342.6 GHz" (SMA)
- continuum bandwidth: four 2-GHz wide bands, two polarizations, 64 Gbps recording  
  > "across four 2-GHz wide bands and two polarizations." (Instrumentation and Array)
- arrays: Eastern subarray: ALMA, APEX, GLT, IRAM30m, NOEMA; western subarray: ALMA, APEX, GLT, SMA  
  > "An eastern subarray, comprising ALMA, the Atacama Pathfinder EXperiment (APEX), Greenland Telescope (GLT), the Institut de Radioastronomie Millimétrique 30 m telescope (IRAM30m), and the Northern Extended Millimeter Array (NOEMA)" (Schedule); "A western subarray, comprising ALMA, APEX, GLT, and the Submillimeter Array (SMA)" (Schedule)
- configurations: ALMA phased array of 25 (eastern) or 29 (western) 12 m antennas, max spacing 600 m; SMA 7 antennas, compact configuration, max baseline 69.1 m  
  > "The ALMA phased array included twenty-five 12 m antennas during the eastern track and twenty-nine 12 m antennas during the western track with a maximum antenna spacing of 600 m in both cases." (ALMA); "The SMA station observed with seven antennas arranged in the compact configuration with a maximum baseline of 69.1 m." (SMA)
- baselines: ALMA-APEX (AX), ALMA-IRAM30m (AP), ALMA-SMA (AS); AS baseline longer than 10.9 G lambda  
  > "The maximum spatial frequencies sampled are greater than 10.9 G$\lambda$ between ALMA and the SMA" (870 um (345 GHz) Fringes); "Baselines: AX (ALMA-APEX), AP (ALMA-IRAM30m), AS (ALMA-SMA)" (Table 1)
- angular resolution: 19 (fringe spacing on longest baselines; unit symbol missing from text, compared with 25 $\mu$as at 1.3 mm)  
  > "corresponding to an angular resolution, or fringe spacing, of 19" (abstract); "than the highest-resolution detections (nominally 25 $\mu$as)" (1.3 mm (230 GHz) Comparison)
- max recoverable scale: _not stated_
- sensitivity: ALMA SEFD about 580 Jy at 870 um versus 150 Jy at 1.3 mm; IRAM30m about 10^5 Jy at 870 um versus 3800 Jy at 1.3 mm; detection threshold S/N > 7  
  > "The SEFD on scans at ALMA were approximately 150 Jy at 1.3 mm versus 580 Jy at 870" (1.3 mm (230 GHz) Comparison); "At IRAM30m, SEFDs during the scans were 3800 Jy at 1.3 mm versus 10$^5$ Jy at 870" (1.3 mm (230 GHz) Comparison)
- time on source: scheduling blocks of 1 to 2 hours, at least two scans per source, most scans five minutes  
  > "they spanned a duration of between 1 and 2 hours with at least two scans on every source. Most scans lasted five minutes." (Schedule)
- observing dates: 2018 October 17-21 window; successful eastern runs 2018 October 18-19, western run 2018 October 21  
  > "The observing window consisted of five nights 2018 October 17–21" (Schedule); "We report herein on successful observations with the eastern array on 2018 October 18-19 and with the western array on 2018 October 21." (Schedule)
- pi or archival as stated: _not stated_
- Other facility **APEX**: Station on ALMA-APEX baselines; 345 GHz FLASH+ receiver, right-circular polarization only  
  > "APEX observed using the 345 GHz FLASH+ linear receiver (cite: Klein_2014)." (APEX)
- Other facility **IRAM30m**: Station on ALMA-IRAM30m baselines; Eight MIxer Receiver (E330)  
  > "The IRAM30m telescope used the heterodyne Eight MIxer Receiver (cite: carter2012) in the 870  band also known as E330." (IRAM30m)
- Other facility **SMA**: Phased 7-antenna station on ALMA-SMA baselines (the best detections)  
  > "The SMA station observed with seven antennas arranged in the compact configuration with a maximum baseline of 69.1 m." (SMA)
- Other facility **GLT**: Participated but no detections on its baselines; still commissioning  
  > "The GLT station participated in the observation but at the time was still commissioning specific subsystems." (GLT); "the opacities at GLT and NOEMA were unfavorable and detections on baselines to those stations were not achieved" (Results and Discussion)
- Other facility **NOEMA**: Single-antenna station, no detections on its baselines  
  > "NOEMA observed in dual polarization as a single-antenna station not as a phased array." (NOEMA)
- External data: ALMA local interferometry zero-baseline flux densities at 870 um (1.4, 1.0, 2.4, 1.2 and 4.9 Jy) and 1.2 Jy at 1.3 mm  
  > "The zero-baseline flux densities at 870  were obtained from the ALMA local interferometry (cite: crew2023)." (870 um (345 GHz) Fringes); "The flux densities were 1.4, 1.0, 2.4, 1.2, and 4.9 Jy" (870 um (345 GHz) Fringes) [from (cite: crew2023)]
- External data: 2017 EHT 1.3 mm Fourier coverage and Allan deviations of high-S/N 1.3 mm scans used for comparison  
  > "compares the Fourier components of the 870  detections on various sources to the 1.3 mm coverage of the 2017 EHT array on (cite: paperiii)" (1.3 mm (230 GHz) Comparison); "the Allan deviations for a large number of high-$S/N$ 1.3 mm scans from the 2017 EHT campaign (cite: paperiii)" (Coherence and Allan Deviation) [from (cite: paperiii)]
- External data: ALMA phasing efficiency of more than about 90% during the October 21 track  
  > "phasing efficiency was more stable and greater than approximately 90% (cite: crew2023)" (ALMA) [from (cite: crew2023)]
- Simulation/model as data: MERRA-2 reanalysis with radiative transfer used to estimate 345 GHz opacity  
  > "we use MERRA-2 reanalysis and radiative transfer (cite: paine2022) that is validated by measurements at 225 GHz" (Results and Discussion)
- Simulation/model as data: GRMHD models shown as Fourier amplitudes versus radius (Figure 9, illustrative)  
  > "Fourier amplitudes as a function of radius for GRMHD" (Future Directions)

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

- 870 um frequency setup follows the 1.3 mm EHT setup  
  > "similar to that described in Table 4 of (cite: paperii)" (Instrumentation and Array) [from (cite: paperii)]
- ALMA Phasing System used to phase the array  
  > "The ALMA Phasing System (APS) (cite: matthews2018) was used to aggregate the collecting area of the active dishes in the ALMA array." (ALMA) [from (cite: matthews2018)]
- Incoherent averaging technique for noise-debiased VLBI quantities  
  > "The incoherent averaging technique (cite: rogers1995) estimates noise-debiased VLBI quantities" (870 um (345 GHz) Fringes) [from (cite: rogers1995)]
- Zero-baseline flux densities and ALMA conditions taken from ALMA local interferometry  
  > "were obtained from the ALMA local interferometry (cite: crew2023)" (870 um (345 GHz) Fringes) [from (cite: crew2023)]
- Atmospheric Kolmogorov Allan deviation curve follows an earlier approach  
  > "following the approach outlined by (cite: treuhaft1987)" (Coherence and Allan Deviation) [from (cite: treuhaft1987)]
- Opacity estimate by reanalysis and radiative transfer  
  > "we use MERRA-2 reanalysis and radiative transfer (cite: paine2022)" (Results and Discussion) [from (cite: paine2022)]

### Not stated but needed to reproduce (our reading)

- Names and coordinates of the observed blazars and quasars (they are missing from the supplied text and appear only in figures)
- HOPS control parameters: segment durations tried, delay and rate search windows, frequency averaging and band selection, polarization handling in the fit
- DiFX correlation settings (integration time, FFT size, a priori model, clock and delay model)
- How the S/N and noise-debiased amplitude were computed in detail and how the S/N>7 threshold was calibrated against false-detection rate
- Allan deviation computation details (averaging, baseline and scan selection, phase unwrapping, normalization constants)
- ALMA APS settings (phasing interval, reference antenna, solution parameters) and the flux density and phasing efficiency data used
- Tabulated SEFD values per scan and station
- Which ALMA archive products (correlated VLBI data under the three project codes) correspond to each table row

## Analysis recipe

1. **Correlate recorded station data**: Station data correlated with DiFX at MIT Haystack; ALMA baselines kept in mixed-polarization basis  
  > "The recorded station data were correlated using DiFX software (cite: deller2011) at the MIT Haystack Observatory." (Instrumentation and Array); "Visibility data on baselines to ALMA remained in a mixed-polarization basis" (Instrumentation and Array)
   - software: DiFX
   - parameter: No linear to circular conversion because schedules were too short to track polarization calibrators over parallactic angle  
  > "because the observing schedules were not long enough to track polarization calibrators over a wide range of parallactic angle" (Instrumentation and Array)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fringe fit with segmented incoherent averaging and apply detection threshold**: Search delay and delay-rate for a correlation power peak with HOPS, dividing each scan into short segments and averaging them incoherently  
  > "the correlator output was searched by dividing each scan into short segments and incoherently averaging them." (870 um (345 GHz) Fringes); "the correlator output is thus searched over a range of delay and delay-rate to find a peak in correlator power" (870 um (345 GHz) Fringes)
   - software: HOPS
   - parameter: Detection threshold S/N > 7  
  > "The fringe detection threshold was conservatively set at $S/N$\>7 to prevent false detections" (870 um (345 GHz) Fringes)
   - parameter: Scans of about 300 s; segment duration varied to find the S/N maximum and coherence time  
  > "Compared to a single coherent integration over a full scan (approximately 300 s in most of the measurements)" (870 um (345 GHz) Fringes); "HOPS reports two coherence times: one corresponding to the point below which there is only a small amount of coherence loss within the uncertainty of amplitudes and another corresponding to the maximum $S/N$." (870 um (345 GHz) Fringes)
   - parameter: Multi-band delay ambiguity window of (-8.53 ns, 8.53 ns) from 58.592375 MHz channel separation  
  > "Multi-band delays fall within an ambiguity search window of (-8.53 ns, 8.53 ns)" (870 um (345 GHz) Fringes)
   - fitting: HOPS fringe fit; coherence time reported as the loss-free point, or the S/N-maximising segment time when the fit fails  
  > "In a few low-$S/N$ cases where the routine was unable to fit the coherence, the coherence time based on $S/N$ is reported instead." (870 um (345 GHz) Fringes)
   - validation: Incoherent averaging raises S/N by up to a factor of two over a full-scan coherent integration; 1.3 mm scans processed the same way as a check  
  > "incoherently averaging the parts of a segmented scan increases the $S/N$ by up to a factor of two on many of the measurements" (870 um (345 GHz) Fringes); "The 1.3 mm scans provide a check of the 870  processing and a point of comparison for the 870  detections." (1.3 mm (230 GHz) Comparison)
3. **Compare with 1.3 mm detections on ALMA-IRAM30m**: Same HOPS incoherent averaging applied to three 1.3 mm scans at the end of the eastern block, compared with the 870 um S/N, coherence time and baseline length  
  > "Those data were searched using the same HOPS incoherent averaging method as was used for the 870  observations" (1.3 mm (230 GHz) Comparison); "ALMA and IRAM30m observed at 1.3 mm during three scans at the end of the eastern subarray scheduling block" (1.3 mm (230 GHz) Comparison)
   - software: HOPS
   - fitting: _not stated_
   - validation: S/N trends consistent between 870 um and 1.3 mm, suggesting a real feature of the data  
  > "The consistency of the $S/N$ trends in the 870  and 1.3 mm scans suggests that the behavior is a real feature of the data and not an artifact of the analysis." (1.3 mm (230 GHz) Comparison)
4. **Explain S/N ratio between bands with SEFD scaling**: S/N scaled as inverse root product of station SEFDs (ALMA factor 3.9, IRAM30m factor about 25)  
  > "The $S/N$ is inversely proportional to the root product of the SEFDs, or $\sqrt{3.9 \times 25} \approx 10$" (1.3 mm (230 GHz) Comparison)
   - parameter: ALMA SEFD 150 Jy (1.3 mm) vs 580 Jy (870 um); IRAM30m 3800 Jy vs 10^5 Jy  
  > "The SEFD on scans at ALMA were approximately 150 Jy at 1.3 mm versus 580 Jy at 870" (1.3 mm (230 GHz) Comparison); "At IRAM30m, SEFDs during the scans were 3800 Jy at 1.3 mm versus 10$^5$ Jy at 870" (1.3 mm (230 GHz) Comparison)
   - fitting: _not stated_
   - validation: Predicted factor of about 10 matches the observed roughly 10-fold S/N ratio  
  > "The $S/N$ values are approximately 10-fold greater at 1.3 mm than at 870" (1.3 mm (230 GHz) Comparison)
5. **Compute Allan deviation of visibility phase and compare with maser and turbulence limits**: Allan deviation of the interferometer phase on ALMA-SMA 870 um scans, normalised by observing frequency, compared with the maser-maser reference, 2017 EHT 1.3 mm scans and a Kolmogorov turbulence curve  
  > "When computing the Allan deviation of observed VLBI interferometer phase one normalizes by the frequency of observation to produce a dimensionless quantity." (Coherence and Allan Deviation); "Figure [8](#fig:adev) shows the Allan deviation for 870  scans on the ALMA-SMA baseline." (Coherence and Allan Deviation)
   - parameter: Nominal Kolmogorov case: 10 m/s wind, 2 km scale height, 1.99e-7 m^-1/3 coefficient, independent distant sites  
  > "following the approach outlined by (cite: treuhaft1987): 10 m $\mathrm{s}^{-1}$ wind speed, 2 km troposphere scale height, 1.99$\times 10^{-7}$ m$^{-1/3}$ Kolmogorov coefficient, and independent distant sites." (Coherence and Allan Deviation)
   - assumption: Tropospheric delay independent of wavelength above about 600 um, so Allan deviation should be wavelength independent  
  > "The tropospheric delay is essentially independent of wavelength for wavelengths longer than about 600" (Coherence and Allan Deviation)
   - fitting: _not stated_
   - validation: Authors caution that the 870 um data set is extremely small and the 2017 and 2018 weather differed  
  > "Further, the observations in 2017 April and 2018 October observations were of course made in differing weather conditions." (Coherence and Allan Deviation)
6. **Estimate 345 GHz opacity at each site**: MERRA-2 reanalysis plus radiative transfer, validated against 225 GHz measurements  
  > "we use MERRA-2 reanalysis and radiative transfer (cite: paine2022) that is validated by measurements at 225 GHz" (Results and Discussion)
   - software: MERRA-2 reanalysis with radiative transfer (paine2022)
   - fitting: _not stated_
   - validation: Validated by 225 GHz measurements  
  > "that is validated by measurements at 225 GHz" (Results and Discussion)

## Software

- **DiFX** : Correlation of recorded station data at MIT Haystack Observatory  
  > "The recorded station data were correlated using DiFX software (cite: deller2011) at the MIT Haystack Observatory." (Instrumentation and Array)
- **HOPS (Haystack Observatory Post-processing System)** : Fringe fitting with incoherent segmented averaging, coherence times  
  > "Subsequent fringe fitting was done using the Haystack Observatory Post-processing System" (Instrumentation and Array)
- **APHIDS** : Post-processing of SMA phased-array (SWARM) data to match standard EHT single-dish products before correlation  
  > "APHIDS (Adaptive Phased Array Interpolating Downsampler for SWARM) post-processing was completed to interpolate and invert (from frequency- to time-domain) the SWARM data sets in preparation for VLBI correlation." (SMA)
- **ALMA Phasing System (APS)** : Phasing the ALMA antennas into a single VLBI station  
  > "The ALMA Phasing System (APS) (cite: matthews2018) was used to aggregate the collecting area of the active dishes in the ALMA array." (ALMA)
- **MERRA-2 reanalysis with radiative transfer** : Estimating 345 GHz opacity  
  > "we use MERRA-2 reanalysis and radiative transfer (cite: paine2022)" (Results and Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Longest baseline with detection, ALMA-SMA | greater than 10.9 | not stated | G lambda | 2 | The maximum spatial frequencies sampled are greater than 10.9 G$\lambda$ between ALMA and the SMA |
| Fringe spacing on longest detected baselines | 19 | not stated | unit symbol missing in text (microarcsec implied by comparison with 25 $\mu$as) | 2 | corresponding to an angular resolution, or fringe spacing, of 19 |
| Highest detection S/N | exceed 70 | not stated | dimensionless | 2 | The highest $S/N$ detections exceed 70. |
| Range of detection S/N | approximately 10 to 70 | not stated | dimensionless | 2 | Signal-to-noise ratios were between approximately 10 and 70. |
| Coherence time across baselines | approximately ten to thirty seconds for most cases | not stated | s | 2 | The coherence times across baselines range from approximately ten to thirty seconds for most cases. |
| S/N gain from incoherent segment averaging | up to a factor of two | not stated | dimensionless | 2 | increases the $S/N$ by up to a factor of two on many of the measurements |
| 345 GHz opacity, eastern subarray (October 18/19) | 0.2 at ALMA and APEX; 0.8 at IRAM30m | not stated | dimensionless | 6 | For the eastern subarray on October 18/19, $\tau_{345}$ was 0.2 at the ALMA and APEX sites, and 0.8 at IRAM30m. |
| 345 GHz opacity, western subarray (October 21) | approximately 0.17 at ALMA and APEX; 0.7 at SMA | not stated | dimensionless | 6 | For the western subarray on October 21, $\tau_{345}$ was approximately 0.17 at the ALMA and APEX sites and 0.7 at SMA. |
| S/N ratio, 1.3 mm versus 870 um | approximately 10-fold greater at 1.3 mm | not stated | dimensionless | 3 | The $S/N$ values are approximately 10-fold greater at 1.3 mm than at 870 |
| ALMA SEFD at 870 um versus 1.3 mm | 580 versus 150 (factor 3.9) | not stated | Jy | 4 | The SEFD on scans at ALMA were approximately 150 Jy at 1.3 mm versus 580 Jy at 870 |
| IRAM30m SEFD at 870 um versus 1.3 mm | 10^5 versus 3800 (factor about 25) | not stated | Jy | 4 | At IRAM30m, SEFDs during the scans were 3800 Jy at 1.3 mm versus 10$^5$ Jy at 870 |
| Beamformer phasing efficiency at 870 um (ALMA and SMA) | just below 50% to about 80% | not stated | percent | 0 | varied from just below 50% to as high as about 80% |
| Atmospheric opacity ratio 870 um to 1.3 mm at the same PWV | 3 to 3.5 | not stated | dimensionless | 0 | atmospheric opacity is between 3 and 3.5 times that for 1.3 mm given the same precipitable water vapor |
| Ratio of 1.3 mm mean Allan deviation to 870 um mean | within a factor of approximately two | not stated | dimensionless | 5 | The mean of the 1.3 mm scans is within a factor of approximately two of the mean of the 870 |
| GLT surface accuracy during observations | 170 | not stated | um rms | 0 | the surface accuracy was estimated to be 170$\mu$m rms during the observations reported here |

## Qualitative findings

- The Allan deviation of the visibility phase at 870 um is comparable to that at 1.3 mm on 2 to 100 s timescales  
  > "The Allan deviation of the visibility phase at 870  is comparable to that at 1.3 mm on the relevant integration time scales between 2 and 100 s." (abstract)
- Detections were made on ALMA-SMA, ALMA-IRAM30m and ALMA-APEX baselines; no detections on GLT or NOEMA baselines  
  > "detections on baselines to those stations were not achieved" (Results and Discussion); "VLBI fringe detections on baselines between ALMA-APEX, ALMA-IRAM30m, and ALMA-SMA have been achieved at 870" (Conclusions)
- S/N values asymptote at the shortest segment durations rather than falling below the coherence time, possibly from changing coherence during the scan in windy conditions  
  > "The behavior we observe could be indicative of a changing coherence during the scan consistent with the windy conditions at ALMA" (870 um (345 GHz) Fringes)
- ALMA-APEX S/N appears anomalously low for the short baseline, likely from suspected APEX receiver phase instabilities  
  > "This is likely attributable to phase instabilities suspected in the APEX receiver" (870 um (345 GHz) Fringes)

## Claim tuples

- H: VLBI fringes can be detected at 870 um with EHT-array stations | E: October 2018 fringe test with eastern and western subarrays, correlation with DiFX and fringe fitting with HOPS | R: Detections with S/N from about 10 to above 70 on ALMA-SMA, ALMA-IRAM30m and ALMA-APEX baselines, up to more than 10.9 G lambda | F: First VLBI detections at 870 um, with the highest angular resolution yet from the Earth surface | **supported**
- H: Phase stability at 870 um is comparable to 1.3 mm | E: Allan deviation of ALMA-SMA 870 um scans compared with maser-maser limit and 2017 1.3 mm EHT scans | R: 870 um Allan deviation comparable to but greater than the maser-maser reference; 1.3 mm mean within about a factor of two of the 870 um mean | F: Phase stability is similar to 1.3 mm over 2 to 100 s, though the 870 um sample is very small | **supported**
- H: The 870 um S/N deficit relative to 1.3 mm is explained by system noise | E: Compared ALMA-IRAM30m detections at both wavelengths and SEFD ratios | R: S/N about 10-fold lower at 870 um, matching root of product of SEFD ratios (3.9 and about 25) | F: Higher system noise at 870 um explains the lower S/N and some non-detections | **supported**
- H: EHT sensitivity and signal chain stability suit 870 um VLBI | E: Fringe test across ALMA, APEX, IRAM30m, SMA, GLT and NOEMA in marginal weather | R: Detections despite 3 to 3.5 times higher opacity, phasing efficiency of 50 to 80%, and commissioning issues at some stations | F: EHT instrumentation is viable at 870 um | **supported**

## Reasoning

- Why this data: Technical demonstration of 870 um VLBI with existing EHT stations  
  > "The experiment we describe was intended as a first technical demonstration of the 870  VLBI capability using facilities that are part of the Event Horizon Telescope (EHT) array." (Introduction)
- Why this method: Incoherent segment averaging suits low-S/N data on sparse arrays and integrates beyond the coherence time  
  > "it is well suited to processing low-$S/N$ VLBI data on sparse arrays as it allows integration beyond the nominal atmospheric coherence time" (870 um (345 GHz) Fringes)
- Alternative: Conversion of ALMA data from linear to circular polarization basis was not done  
  > "because the observing schedules were not long enough to track polarization calibrators over a wide range of parallactic angle" (Instrumentation and Array)
- How they decided it was enough: Detections accepted at S/N above 7  
  > "The fringe detection threshold was conservatively set at $S/N$\>7 to prevent false detections" (870 um (345 GHz) Fringes)
- Limitation (authors): Observations were a detection experiment without the procedures for robust VLBI flux density calibration; source structure not known a priori  
  > "these observations were designed to be a detection experiment, and not carried out with all procedures that would allow robust VLBI flux density calibration." (870 um (345 GHz) Fringes); "The source structure of the targets in this work is not known apriori" (870 um (345 GHz) Fringes)
- Limitation (authors): GLT pointing and focus were still in commissioning and its surface was 170 um rms; NOEMA partly commissioning  
  > "Pointing and focus calibration at 345 GHz were still in the commissioning phase during the 870  observation reported here." (GLT); "Portions of the NOEMA station were still being commissioned during the 870  experiment." (NOEMA)
- Limitation (authors): ALMA-APEX baseline S/N anomalously low, attributed to suspected APEX receiver phase instability  
  > "This is likely attributable to phase instabilities suspected in the APEX receiver" (870 um (345 GHz) Fringes)
- Limitation (authors): WVR phasing corrections not in use and weather marginal (high wind, high opacity)  
  > "Water vapor radiometer (WVR) based phasing corrections were not in use during the 2018 test." (Phasing Efficiency)
- Caveat (inferred, ours): Source names are absent from the text provided, so which scans belong to which source cannot be checked from the paper text alone
- Caveat (inferred, ours): Detection significance rests on an S/N>7 threshold with no stated false-alarm calibration
- Caveat (inferred, ours): The 870 um Allan deviation comparison uses very few scans in one weather state
- Caveat (inferred, ours): No amplitude calibration, so correlated flux densities are not interpretable as visibility amplitude versus baseline
- Caveat (inferred, ours): Several S/N values depend on the HOPS segment length chosen per scan; the choice rule is only partly described

## Reproducibility

- Data public (paper): ALMA VLBI data are accessible at the ALMA science archive EHT 2018 page  
  > "See https://almascience.eso.org/almadata/ec/eht-2018 for more detail and access to the data." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Raw station recordings from APEX, IRAM30m and SMA and correlation settings
- Missing: HOPS control file and segment-duration choices
- Missing: Names and coordinates of the observed sources
- Missing: Allan deviation computation details and Kolmogorov inputs beyond those listed
- Missing: Per-station SEFD and phasing efficiency time series
- Data volume (inferred): Large: raw VLBI recordings at 64 Gbps per station are petabyte-scale in aggregate; correlated products for the 5 to 6 scans per baseline are likely a few GB to tens of GB
- Score (inferred): 2/5, ALMA correlated data are public, but the HOPS and DiFX parameters, source names and calibration details are not given, and the tabulated results are numeric only for detections rather than a fully specified pipeline.
- Rediscovery candidate: no, Station recordings and correlation setups are not available to a typical reproducer, and the fringe-fitting recipe is not fully specified in the paper.

## Links

- Method: (cite: paperii) (Describes EHT instrumentation and 1.3 mm frequency setup that this test follows)
- Method: (cite: matthews2018) (ALMA Phasing System used for VLBI)
- Method: (cite: rogers1995) (Incoherent averaging technique for noise-debiased VLBI quantities)
- Method: (cite: treuhaft1987) (Atmospheric Kolmogorov turbulence Allan deviation approach)
- Companion: (cite: crew2023) (ALMA conditions, phasing system performance and local interferometry flux densities during the 870 um test)
- Companion: (cite: paperiii) (2017 EHT 1.3 mm data used for coverage and Allan deviation comparison)
- Related: Event Horizon Telescope
- Related: next-generation EHT (ngEHT)
- Related: ALMA Phasing Project

## Checks

```json
{
 "quotes": 113,
 "quotes_ok": 113,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00010.E",
  "2011.0.00012.E"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 64,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
