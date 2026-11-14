# First Very Long Baseline Interferometry Fringe Detection at 690 GHz

`2026PASP..138h4104C` | Publications of the Astronomical Society of the Pacific 2026 | first author: Chen, Ming-Tang | arXiv: 2609.09886 | DOI: 10.1088/1538-3873/ae92b6

Card schema 1.0 | model gemini-4-argon | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: Evaluate the feasibility and practical requirements—including instrumental readiness, ALMA Band 9 phasing performance, calibration strategy, and atmospheric conditions—for ground-based very long baseline interferometry (VLBI) in the 690 GHz atmospheric window.  
  > "The objective of this work was not only to achieve a technical milestone but also to evaluate the practical requirements—including instrumental readiness, calibration strategy, atmospheric conditions, and operational resources—necessary for sustained near-terahertz VLBI." (1. Introduction); "Our goal in this 690 GHz experiment was to demonstrate the feasibility of VLBI at such high frequencies, thereby establishing a critical stepping stone toward future observations of the supermassive black holes Sgr A* and M87*." (1. Introduction)
- Target **J0423-0120**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J0433+0521**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Orion BN (ORIBN)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00014.E
- bands: Band 9 (690 GHz) and Band 6 (230 GHz)  
  > "On 2024 November 21, observations with the Atacama Large Millimeter/submillimeter Array, the Atacama Pathfinder EXperiment (APEX), and the James Clerk Maxwell Telescope (JCMT) were carried out using ALMA’s newly developed Band 9 phasing capability." (Abstract); "For the primary and secondary targets, we also scheduled a Band 6 (230 GHz) session as a VLBI benchmark test of overall system, since observations in this band are well established." (4.1. The Observing Targets)
- frequencies and spectral setup: Primary LO at 685 GHz capturing four 2 GHz subbands at 678, 680, 690, and 692 GHz (only BB_2/b2 ≈ 679 GHz and BB_3/b3 ≈ 691 GHz correlated for VLBI); 230 GHz (214 GHz) benchmark session  
  > "Thus, we set the primary local oscillator (LO) frequency to 685 GHz to capture four subbands, centered at 678 GHz, 680 GHz, 690 GHz, and 692 GHz, respectively, each with a 2 GHz bandwidth." (4.3. RF Frequency and LO); "The Band-9 fringe test used the 35 first three scans (Scan 1, 2 and 3) with the two LO tunings (b2 ≈ 679 GHz and b3 ≈ 691 GHz)." (6.1. Correlation); "In standard EHT observations, all four ALMA basebands are used, but in this experiment only BB_2 and BB_3 were correlated." (6.1. Correlation)
- continuum bandwidth: 2 GHz per baseband  
  > "Thus, we set the primary local oscillator (LO) frequency to 685 GHz to capture four subbands, centered at 678 GHz, 680 GHz, 690 GHz, and 692 GHz, respectively, each with a 2 GHz bandwidth." (4.3. RF Frequency and LO); "where ΔB is the observation bandwidth (2 GHz) and t the integration time." (6.2. Sensitivity Estimation)
- arrays: ALMA 12 m phased array (45 antennas phased, 1 comparison antenna DV01; virtual sum antenna attached to 7 m antenna CM12)  
  > "For the Band 9 observations, the ALMA Phasing System (APS) coherently combined all available 12 m antennas within 200 m of DA45." (5. 2024 November 21 Observation); "We are also deeply grateful to the ALMA management for the observing time allocated to this experiment, conducted under exceptional weather conditions with the participation of 45 ALMA antennas." (Acknowledgments)
- configurations: _not stated_
- baselines: Internal ALMA phased array: up to 183.934 m from DA45; VLBI baselines at 685 GHz: ALMA-APEX = 6 Mλ, ALMA-JCMT = 21,720 Mλ (22 Gλ)  
  > "The most distant participating antenna from DA45 was DV14 at 183.9 m." (5. 2024 November 21 Observation); "2 685 AX 6 0.11 20 12" (Table 4); "AM 21,720 0.25 9 Non-detect" (Table 4)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: Estimated 1σ VLBI baseline sensitivity at 680 GHz: 0.11 Jy (ALMA-APEX, 20 s) and 0.25 Jy (ALMA-JCMT, 10 s)  
  > "Using the efficiency factors discussed above, the resulting 1σ baseline sensitivities are 0.11 Jy for the ALMA–APEX baseline and 0.25 Jy for the ALMA–JCMT baseline." (6.2. Sensitivity Estimation)
- time on source: 5 hours total allocation including 90 minute VLBI block; nominal scan duration ~300 s (usable FSI 44-100 s)  
  > "The experiment was allocated five hours, including time for the prior phasing tests and a 90 minute VLBI observing block." (5. 2024 November 21 Observation); "Although the nominal scan duration is approximately 300 s, only about 100 s of data is effectively usable because of phasing stability and data-quality limitations" (6.1. Correlation)
- observing dates: 2024 November 21 (UT)  
  > "On 2024 November 21, observations with the Atacama Large Millimeter/submillimeter Array, the Atacama Pathfinder EXperiment (APEX), and the James Clerk Maxwell Telescope (JCMT) were carried out" (Abstract); "On 2024 November 21 (UT), weather conditions at ALMA/APEX and JCMT were excellent, with precipitable water vapor (PWV) values of 0.46 mm and 1.3 mm, respectively, and negligible wind at both sites." (5. 2024 November 21 Observation)
- pi or archival as stated: PI/commissioning VLBI experiment  
  > "The experiment conducted an observation at 685 GHz, the highest frequency ever attempted for ground-based VLBI, using the Atacama Large Millimeter/submillimeter Array (ALMA), the Atacama Pathfinder EXperiment (APEX), and the James Clerk Maxwell Telescope (JCMT)." (1. Introduction); "This paper makes use of the following ALMA data:ADS/JAO.ALMA#2011.0.00014.E." (Acknowledgments)
- Line: CO 6-5 (691.435 GHz)
- Other facility **Atacama Pathfinder EXperiment (APEX)**: 12 m VLBI station on Chajnantor participating in 690 GHz observations with a dual-polarization 2SB receiver and hydrogen maser (iMaser 56).  
  > "On 2024 November 21, observations with the Atacama Large Millimeter/submillimeter Array, the Atacama Pathfinder EXperiment (APEX), and the James Clerk Maxwell Telescope (JCMT) were carried out" (Abstract); "The JCMT and APEX use dual-polarization, 2SB receivers (Belitsky et al 2018; Bintley et al 2024), and the data were processed with the EHT hardware and recorders" (4.3. RF Frequency and LO)
- Other facility **James Clerk Maxwell Telescope (JCMT)**: 15 m VLBI station on Maunakea participating in 690 GHz and 230 GHz observations using the Kuntur 690 GHz dual-polarization 2SB receiver and a Vector Atomic iodine optical clock.  
  > "The VLBI experiment described in this report was made possible by an opportunity to outfit the JCMT with a 690 GHz receiver (Bintley et al. 2024)." (1. Introduction); "In contrast, JCMT was referenced to an optically stabilized 10 MHz signal derived from a VA iodine clock, as introduced earlier." (4.2. Frequency Standard)
- Other facility **Greenland Telescope (GLT)**: Scheduled to participate in the 230 GHz VLBI benchmark session, but adverse weather prevented usable data acquisition; also loaned cryostat for JCMT 690 GHz receiver.  
  > "The system combined a cryostat originally built for the Greenland Telescope (GLT) (Chen et al. 2023) with a new ALMA Band 9–type receiver cartridge" (1. Introduction); "The GLT was scheduled to participate in this observation, with receiver and backend systems configured analogously to the 230 GHz EHT setup (Chen et al. 2023). However, adverse weather conditions at the GLT site prevented usable data acquisition" (5. 2024 November 21 Observation)
- Other facility **Large Latin American Millimeter Array (LLAMA)**: Loaned the Kuntur Band 9 receiver cartridge installed at JCMT.  
  > "with a new ALMA Band 9–type receiver cartridge developed by the NOVA laboratory in Groningen, the Netherlands, for the Large Latin American Millimeter Array (LLAMA)." (1. Introduction); "This work was made possible through the loan of the Kuntur 650 GHz (Band 9) receiver provided by the LLAMA collaboration." (Acknowledgments)
- Other facility **Submillimeter Array (SMA)**: Hosted the two Vector Atomic iodine clocks in its hydrogen maser room and provided optical fiber link to JCMT.  
  > "Prior to the observations, two VA iodine clocks were installed in the SMA hydrogen maser room, from which JCMT derived its frequency standard." (4.2. Frequency Standard)
- External data: ALMA Band 9 aperture efficiency of 0.43  
  > "In this work, the aperture efficiencies for Band 9 are taken as 0.43 (Table 9.3, Cortés et al. 2024) and 0.32 37 for ALMA and JCMT, respectively." (6.2. Sensitivity Estimation) [from Cortés et al. 2024]
- External data: JCMT Band 9 aperture efficiency of 0.32  
  > "In this work, the aperture efficiencies for Band 9 are taken as 0.43 (Table 9.3, Cortés et al. 2024) and 0.32 37 for ALMA and JCMT, respectively." (6.2. Sensitivity Estimation) [from JCMT Telescope Overview webpage]
- External data: APEX conversion factor of 62 Jy K^-1 and T_sys measurement from 2025 April 5  
  > "sky loads on 2025 April 5, adopting the APEX-specific conversion factor of 62 Jy" (Section 6.2) [from APEX efficiency webpage]
- External data: APS end-to-end phasing efficiency of ~61% (and ~70% with improvements) and VLBI phased-sum formation efficiency factor of 0.93 (7% loss)  
  > "Matthews et al. (2018, Section 8.2) reported an end-to-end phasing efficiency of approximately 61% under typical conditions." (6.2. Sensitivity Estimation); "Crew (2020) reported an additional efficiency reduction of approximately 7%, corresponding to a multiplicative factor of 0.93 applied to the VLBI data stream." (6.2. Sensitivity Estimation) [from Matthews et al. 2018; Crew 2020]
- External data: ALMA calibrator flux densities for J0423-0120 (~3.9 Jy at 233 GHz, ~3.3 Jy at 343 GHz, ~2.3 Jy at 674/690 GHz) and J0433+0521 (~2 Jy at 343 GHz)  
  > "Near the time of the experiment, ALMA calibrator measurements report flux densities of ∼3.9 Jy at 233 GHz and ∼3.3 Jy at 343 GHz" (4.1. The Observing Targets); "Its flux density was measured at about 2.3 Jy at 674 GHz on both 2024 November 15 and December 14." (6.2. Sensitivity Estimation) [from ALMA calibrator monitoring]
- External data: Allan variance K2 and K0 parameters for active hydrogen maser comparison  
  > "For comparison, values from TMS (Table 9.4) are also included." (Appendix); "TMS, 2ed. H(active) 1.0 e-13 3.0 e-14" (Table A1) [from Thompson et al. 2017 (TMS)]

## Processing

### Calibration

- pipeline or manual: Real-time ALMA Phasing System (APS) with delay-fix mechanism, 90-deg Walsh switching disabled, 180-deg Walsh switching enabled, LO offsetting for sideband suppression; VLBI correlation in DiFX and fringe fitting in HOPS; no dedicated VLBI amplitude calibration scans  
  > "The delay-fix applied full-band delay correction during the experiment." (2. ALMA Phasing System (APS)); "Thus, during the APS operation, the 90° Walsh-switching must be turned off, and the DSB-to-SSB signal conversion is also disabled." (4.3. RF Frequency and LO); "Due to the limited allotted ALMA time allocated to this experiment, no dedicated calibration scans were included." (6.2. Sensitivity Estimation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: None (sensitivities estimated from station technical parameters and ALMA calibrator monitoring of J0423-0120)  
  > "Due to the limited allotted ALMA time allocated to this experiment, no dedicated calibration scans were included. Thus, sensitivities were estimated from station technical parameters." (6.2. Sensitivity Estimation)
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

- ALMA Phasing System (APS) legacy architecture and delay-fix upgrade  
  > "The legacy APS architecture is documented in early publications (Matthews et al. 2018; Goddi et al. 2019), while the new delay-fix is formally detailed in the APP2 Final Report (Matthews & Crew 2024)." (2. ALMA Phasing System (APS)) [from Matthews et al. 2018; Goddi et al. 2019; Matthews & Crew 2024]
- EHT VLBI hardware and recorders at JCMT and APEX  
  > "The JCMT and APEX use dual-polarization, 2SB receivers (Belitsky et al 2018; Bintley et al 2024), and the data were processed with the EHT hardware and recorders as described in (EHT Collaboration 2019c)." (4.3. RF Frequency and LO) [from EHT Collaboration 2019c]
- Statistical fringe detection and coherence formalism in cohfit and Appendix  
  > "While 36 cohfit itself is an internal HOPS tool, it implements statistical fringe detection and coherence concepts developed for VLBI data analysis (e.g., Rogers et al. 1995) within the Mark 4/HOPS framework (Whitney et al. 2004)." (6.1. Correlation); "This section summarizes the evaluation of the coherence function following Section 9 of TMS (Rogers and Moran 1981)." (Appendix) [from Rogers & Moran 1981; Rogers et al. 1995; Whitney et al. 2004; Thompson et al. 2017]

### Not stated but needed to reproduce (our reading)

- Exact DiFX (v2.7.1) correlation configuration files (.v2d, .vex) including spectral channelization, accumulation period, and earth orientation/station clock models
- Exact time intervals (UTC start and stop times) selected for the usable fringe search intervals (FSI) in each scan
- Complete raw VLBI voltage recordings from ALMA, APEX, and JCMT (the paper notes only a small sample is included in the ALMA Archive)

## Analysis recipe

1. **Verify station frequency standards and evaluate clock-limited coherence**: Measure Allan deviation and PPS drift rates of the Vector Atomic iodine optical clock at JCMT (against a secondary VA clock, a Rakon OCXO, and GPS) and the hydrogen masers at ALMA and APEX; parameterize Allan variance with K2 and K0 to numerically integrate the rms clock coherence function at 685 GHz.  
  > "Allan deviation and drift rate were also measured for the frequency standards at all participating stations." (4.2. Frequency Standard); "Using these parameters, we numerically evaluated the rms coherence function for the ALMA–APEX and ALMA–JCMT baselines at 685 GHz." (Appendix)
   - parameter: Observing frequency = 685 GHz; integration times τ = 10 s (ALMA-JCMT) and 20 s (ALMA-APEX)  
  > "with rms values of 0.96 (ALMA–JCMT) at 10 s and 0.85 (ALMA–APEX) at 20 s." (Figure A1 caption)
   - assumption: At very short timescales (τ < 0.1 s), clock stability is dominated by white noise; for 10^-2 to 10^2 s, only K_-2 and K_0 terms in the Allan variance parameterization need to be considered.  
  > "where, for the time spans relevant here (10−2–102 s), only the K2 and K0 need to be considered." (Appendix); "In the evaluation, we assume that at very short timescales (τ < 0.1 s), the stability is dominated by white noise." (Appendix)
   - fitting: _not stated_
   - validation: Independent comparison of primary VA optical clock against a second VA clock, a Rakon OCXO, and JCMT GPS receiver.  
  > "The second VA unit was configured for independent evaluation against both the primary and a Rakon 32 oscillator in the same location. Stability was additionally assessed using JCMT’s Global Positioning System (GPS) receiver" (4.2. Frequency Standard)
2. **Phase the ALMA array at Band 9 and Band 6 using the ALMA Phasing System (APS)**: Coherently sum 45 ALMA 12 m antennas within 200 m of DA45 using the APS with the full-band (2 GHz) delay-fix mechanism enabled, 16 s slow cross-correlation phase loop, 1 Hz fast WVR loop, 90-deg Walsh switching disabled, 180-deg Walsh switching enabled, and LO offsetting for sideband suppression.  
  > "APS operates with two phase correction loops: a slow loop, updating every ∼16 s using internal cross-correlations, and a fast loop, applying ∼1 Hz corrections based on water vapor radiometer (WVR) data." (2. ALMA Phasing System (APS)); "To mitigate these challenges, a new phasing mechanism called the delay-fix was introduced—an upgrade that directly measures and corrects delays across the full 2 GHz baseband" (2. ALMA Phasing System (APS)); "For the Band 9 observations, the ALMA Phasing System (APS) coherently combined all available 12 m antennas within 200 m of DA45." (5. 2024 November 21 Observation)
   - parameter: Slow loop cadence ~ 16 s; fast WVR loop ~ 1 Hz; 45 phased 12 m antennas; comparison antenna DV01 excluded from sum; virtual sum antenna attached to CM12  
  > "Antenna DV01 (61.2 m from DA45) was excluded from the phased sum and used as an independent comparison antenna to evaluate phasing performance." (5. 2024 November 21 Observation); "In the data products, it inherits the name of the antenna to which it is logically attached—CM12, a 7 m antenna not otherwise part of the 12 m array for these observations." (5. 2024 November 21 Observation)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Evaluated near-real-time phasing efficiency using comparison antenna DV01 and verified >90% phasing efficiency during 230 GHz benchmark scans.  
  > "In contrast, the 230 GHz scans all maintained a phasing efficiency above 90% throughout the 300 s scan." (6. Results and Analysis)
3. **Correlate VLBI data and verify Band 9 spectral-line tuning**: Correlate recorded VLBI baseband data at MIT Haystack using DiFX v2.7.1; first correlate Band 6 (Scans 7 and 8) to verify station clocks and delay rates, then extract JCMT VLBI autocorrelation spectra on Orion BN (Scans 5 and 6) referenced to Scan 4 (J0433+0521) via division and subtraction over a 20 s segment to confirm CO(6-5) emission and telluric H2O absorption, and finally correlate Band 9 continuum scans (Scans 1-3).  
  > "Correlation was performed at MIT Haystack using DiFX (Deller et al. 2011), version 2.7.1, with subsequent analysis carried out using the Haystack Observatory Postprocessing System (HOPS 34 ) package." (6.1. Correlation); "The spectra were extracted from the JCMT VLBI autocorrelation data produced by the correlator. In a manner analogous to sky switching, Scan 4 served as a reference background against which Scans 5 and 6 were processed using both ratio and subtraction to highlight weak spectral structure." (6.1. Correlation)
   - software: DiFX, HOPS
   - parameter: 20 s segment for Orion BN spectral check; Band 9 basebands b2 ≈ 679 GHz and b3 ≈ 691 GHz correlated; 70 s test correlations on Scan 2  
  > "Although several minutes of data were obtained on Orion BN, only a representative 20 s segment was processed for this spectral check in order to limit correlator usage." (6.1. Correlation); "Short 70 s test correlations on Scan 2 produced clear detections across all polarization products, confirming that both tunings generated real Band-9 fringes." (6.1. Correlation)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Confirmed astrophysical CO(6-5) emission at 691.435 GHz and telluric water-vapor absorption at 692.366 GHz in both spectral ratio and difference plots; confirmed clock and delay-rate alignment in Band 6 scans.  
  > "Both Scan 5 and Scan 6 clearly detect the CO (6–5) line at 691.435 GHz, as expected for the Orion BN target. In addition, a prominent telluric absorption feature is observed near 692.366 GHz" (6.1. Correlation)
4. **Perform VLBI fringe fitting and coherence timescale analysis**: Run fourfit and the cohfit segmented incoherent-averaging utility in HOPS v3.26 over a range of solution intervals and usable fringe search intervals (FSI) to measure fringe SNR, probability of false detection (PFD), multi-band delay (MBD), fringe rate, and optimal integration timescales at 230 GHz and 690 GHz.  
  > "The fringe-detection analysis was performed using the cohfit utility within the HOPS analysis package." (6.1. Correlation); "The visibility data are segmented into intervals of different durations, and fringe solutions are obtained over a range of solution intervals." (6.1. Correlation); "For each scan and polarization product, we list the fourfit fringe quality (Qcode), signal-to-noise ratio (SNR), probability of false detection (PFD), fitted multi-band delay (MBD), fringe rate, and fringe search interval (FSI)." (Table 2)
   - software: HOPS, fourfit, cohfit
   - parameter: Nominal solution interval = 20 s for ALMA-APEX at 690 GHz; extrapolated reference solution interval = 10 s for ALMA-JCMT at 690 GHz (scaled from 30 s peak at 230 GHz); usable FSI = 44-100 s  
  > "We therefore use 20 s as a nominal solution interval for sensitivity estimation of the ALMA–APEX 690 GHz fringe detection." (6.1. Correlation); "The corresponding interval at 690 GHz is reduced by about a factor of three, suggesting an approximate solution interval of order 10 s for the ALMA–JCMT baseline in a similar fringe-detection analysis." (6.1. Correlation)
   - assumption: Non-dispersive tropospheric path-length fluctuations scale linearly with observing frequency, so the reference solution interval scales inversely with frequency (from 230 GHz to 690 GHz by a factor of ~3).  
  > "If atmospheric fluctuations are the primary cause of the SNR degradation, the associated non-dispersive path-length fluctuations imply residual phase fluctuations that scale approximately linearly with observing frequency (e.g., TMS; Carilli & Holdaway 1999). As a simple approximation, we therefore scale the reference solution interval inversely with frequency." (6.1. Correlation)
   - fitting: Delay-rate and multi-band delay fringe search in fourfit; segmented incoherent averaging across solution intervals in cohfit.  
  > "The visibility data are segmented into intervals of different durations, and fringe solutions are obtained over a range of solution intervals." (6.1. Correlation)
   - validation: Assessed physical consistency of fringe solutions including stability of delay-rate peaks across parallel-hand and cross-hand polarizations and between adjacent scans.  
  > "This classification is based not solely on statistical significance, but also on the physical consistency of the fringe solution, including stability of the delay–rate peak across parallel-hand polarizations and comparison between adjacent scans." (6.1. Correlation); "We verified the polarization labelling by examining the cross-polarization products (XY and YX), which show consistent fringe solutions and no evidence of an X/Y swap." (6.2. Sensitivity Estimation)
5. **Estimate baseline sensitivities, expected SNRs, and source size constraints**: Calculate station SEFDs from measured T_sys and aperture efficiencies using radiometer theory, account for ALMA phasing losses and VLBI efficiency factors (quantization, clock coherence, polarization), compute 1σ baseline sensitivities and expected SNRs for J0423-0120, and derive a lower limit on source angular FWHM from the ALMA-JCMT non-detection.  
  > "The system temperatures of ALMA and JCMT were measured during the observation. Their SEFDs are derived using radiometer theory" (6.2. Sensitivity Estimation); "We consider three primary efficiency factors: the quantization efficiency (η q ), the coherence efficiency (η c ), and the polarization efficiency (η p )" (6.2. Sensitivity Estimation); "On the other hand, if the non-detection of the primary target on the ALMA–JCMT baseline is due to the source being resolved, one can place a lower limit on the source size by assuming a circular Gaussian brightness distribution." (7. Discussion)
   - parameter: Bandwidth ΔB = 2 GHz; t = 20 s (ALMA-APEX) and 10 s (ALMA-JCMT); η_q = 0.88; η_c = 0.85 (ALMA-APEX) and 0.96 (ALMA-JCMT); η_p = 0.71; ALMA 3-bit quantization efficiency = 0.96, phasing efficiency = 0.70, VLBI sum factor = 0.93  
  > "The standard 2-bit quantization used in astronomical VLBI introduces a signal loss of approximately 12%, corresponding to a quantization efficiency of η q ≈ 0.88." (6.2. Sensitivity Estimation); "Numerical evaluation of the coherence function at 685 GHz indicates rms coherence values of 0.96 for the ALMA–JCMT baseline and 0.85 for the ALMA–APEX baseline at an integration time of 10 s and 20 s, respectively" (6.2. Sensitivity Estimation); "Because both JCMT linear feeds were correlated against ALMA, the worst-case loss in correlated amplitude due to an unknown polarization-frame rotation is limited to cos 45° ≈ 0.71." (6.2. Sensitivity Estimation)
   - assumption: Aperture efficiencies of 0.43 (ALMA) and 0.32 (JCMT); APEX conversion factor 62 Jy K^-1; J0423-0120 total flux density = 2.3 Jy; circular Gaussian brightness distribution and 7σ detection threshold for source size limit.  
  > "In this work, the aperture efficiencies for Band 9 are taken as 0.43 (Table 9.3, Cortés et al. 2024) and 0.32 37 for ALMA and JCMT, respectively." (6.2. Sensitivity Estimation); "Adopting a conservative detection threshold of 7σ, with σ ≈ 0.25 Jy, on the 22 Gλ baseline, the correlated flux density of J0423–0120 (total flux density ≈ 2.3 Jy) must fall below ≈ 1.75 Jy." (7. Discussion)
   - fitting: _not stated_
   - validation: Compared predicted SNRs against measured fourfit SNRs on ALMA-APEX and ALMA-JCMT baselines.  
  > "For J0423–0120, a fringe was detected only on the ALMA–APEX baseline in Scan 2, with a measured SNR of 12. No fringes were detected on the ALMA–JCMT baseline." (Table 4 note)

## Software

- **DiFX** 2.7.1: VLBI correlation of ALMA, APEX, and JCMT recordings at MIT Haystack  
  > "Correlation was performed at MIT Haystack using DiFX (Deller et al. 2011), version 2.7.1, with subsequent analysis carried out using the Haystack Observatory Postprocessing System (HOPS 34 ) package." (6.1. Correlation)
- **HOPS (Haystack Observatory Postprocessing System)** 3.26: Post-correlation VLBI fringe-fitting and coherence analysis  
  > "Correlation was performed at MIT Haystack using DiFX (Deller et al. 2011), version 2.7.1, with subsequent analysis carried out using the Haystack Observatory Postprocessing System (HOPS 34 ) package." (6.1. Correlation); "The HOPS software used in this analysis will is released as version 3.26" (6.1. Correlation)
- **fourfit** : VLBI fringe fitting to determine SNR, PFD, multi-band delay, and fringe rate within HOPS  
  > "To place these results in a more general and consistent context, Table 2 presents a subset of fourfit output parameters most relevant to fringe detection." (6.1. Correlation); "Figure 5 illustrate representative cases using fourfit (Rogers et al. 1995) fringe diagnostics." (6.1. Correlation)
- **cohfit** : Segmented fringe-detection and coherence analysis as a function of solution interval within HOPS  
  > "The fringe-detection analysis was performed using the cohfit utility within the HOPS analysis package." (6.1. Correlation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLBI fringe SNR on ALMA-APEX baseline at 691 GHz (Scan 2, J0423-0120, Pol X1X) | 12.0 | not stated | dimensionless | 4 | Fringes were detected on the ALMA–APEX baseline during a scan of the quasar J0423–0120, with a signal-to-noise ratio of ∼12; a fringe was detected only on the ALMA–APEX baseline in Scan 2, with a measured SNR of 12. |
| Nominal Band 9 VLBI solution interval on ALMA-APEX baseline | 20 | not stated | s | 4 | We therefore use 20 s as a nominal solution interval for sensitivity estimation of the ALMA–APEX 690 GHz fringe detection. |
| Estimated reference Band 9 VLBI solution interval on ALMA-JCMT baseline | 10 | not stated | s | 4 | The corresponding interval at 690 GHz is reduced by about a factor of three, suggesting an approximate solution interval of order 10 s for the ALMA–JCMT baseline in a similar fringe-detection analysis. |
| ALMA single-antenna system temperature (T_sys) at 680 GHz | 1250 | not stated | K | 5 | ALMA (12 m) Single antenna ∼45.0 1250 1800 70.9 102 |
| ALMA single-antenna system temperature (T_sys) at 690 GHz | 1800 | not stated | K | 5 | ALMA (12 m) Single antenna ∼45.0 1250 1800 70.9 102 |
| Phased ALMA (45 antennas) SEFD at 680 GHz | 2500 | not stated | Jy | 5 | Phased 45 antennas 0.46 (avg. ALMA antennas) 2.5 3.5 |
| Phased ALMA (45 antennas) SEFD at 690 GHz | 3500 | not stated | Jy | 5 | Phased 45 antennas 0.46 (avg. ALMA antennas) 2.5 3.5 |
| JCMT system temperature (T_sys) at 680 GHz | 3800 | not stated | K | 5 | JCMT (15 m) ∼39.3 1.3 3800 4666 185 228 |
| JCMT SEFD at 680 GHz | 185000 | not stated | Jy | 5 | JCMT (15 m) ∼39.3 1.3 3800 4666 185 228 |
| APEX SEFD at 680 and 690 GHz | 58900 | not stated | Jy | 5 | APEX (12 m) ∼45.8 0.46 (same as ALMA) 950 950 58.9 58.9 |
| Estimated 1σ VLBI baseline sensitivity at 680 GHz on ALMA-APEX (20 s) | 0.11 | not stated | Jy | 5 | Using the efficiency factors discussed above, the resulting 1σ baseline sensitivities are 0.11 Jy for the ALMA–APEX baseline and 0.25 Jy for the ALMA–JCMT baseline. |
| Estimated 1σ VLBI baseline sensitivity at 680 GHz on ALMA-JCMT (10 s) | 0.25 | not stated | Jy | 5 | Using the efficiency factors discussed above, the resulting 1σ baseline sensitivities are 0.11 Jy for the ALMA–APEX baseline and 0.25 Jy for the ALMA–JCMT baseline. |
| Expected VLBI SNR at 680 GHz on ALMA-APEX (Scan 2, J0423-0120) | 20 | not stated | dimensionless | 5 | 2 685 AX 6 0.11 20 12 |
| Expected VLBI SNR at 680 GHz on ALMA-JCMT (Scan 2, J0423-0120) | 9 | not stated | dimensionless | 5 | AM 21,720 0.25 9 Non-detect |
| Lower limit on angular FWHM of J0423-0120 at 685 GHz (if resolved on ALMA-JCMT) | >= 2.6 (or >= 4) | not stated | μas | 5 | Under these assumptions, the inferred full width at half maximum (FWHM) of the source is required to be ≳ 2.6 μas.; If the non-detection on ALMA–JCMT reflects source structure rather than purely instrumental loss, the data imply a lower limit of ≳4 μas on the FWHM of J0423–0120 under a circular Gaussian assumption. |
| Vector Atomic optical clock fractional frequency stability | 5.0e-14 (τ=1 s), 1.5e-14 (τ=10 s), 1.5e-15 (τ=100 s) | not stated | dimensionless | 1 | A separate comparison between two optically derived 10 MHz outputs indicates a fractional stability of approximately 5.0e-14 at τ = 1 s, 1.5e-14 at τ = 10 s, and 1.5e-15 at τ = 100 s. |
| Clock-limited coherence time at 685 GHz | 92 (ALMA-APEX) and 150 (ALMA-JCMT) | not stated | s | 1 | In this context, the coherence times, where 〈 C 2 clock ( T )〉∼0.5, are 92 s and 150 s for ALMA-APEX and ALMA-JCMT baselines, respectively. |
| RMS clock coherence factor at 685 GHz | 0.85 (ALMA-APEX at 20 s) and 0.96 (ALMA-JCMT at 10 s) | not stated | dimensionless | 1 | with rms values of 0.96 (ALMA–JCMT) at 10 s and 0.85 (ALMA–APEX) at 20 s. |

## Qualitative findings

- First ground-based VLBI fringe detection in the 690 GHz atmospheric window was achieved on the ALMA-APEX baseline on quasar J0423-0120 with SNR ~ 12.  
  > "Fringes were detected on the ALMA–APEX baseline during a scan of the quasar J0423–0120, with a signal-to-noise ratio of ∼12 and useful fringe recovery over solution intervals of order tens of seconds, representing the highest-frequency ground-based VLBI fringe detection reported to date." (Abstract)
- The ALMA Phasing System (APS) at Band 9 started at ~70% phasing efficiency on J0423-0120 but degraded toward ~30% after 1-2 minutes, limiting usable scan durations to ~60-90 s.  
  > "the phasing efficiency initially started reasonably well, as expected due to the excellent weather conditions, but subsequently degraded towards a level of 30%." (Section 6); "For the first two scans on the primary targets, the phasing efficiency initially started reasonably well, as expected due to the excellent weather conditions, but subsequently degraded towards a level of 30%." (6. Results and Analysis)
- No Band 9 fringes were detected on the intercontinental ALMA-JCMT baseline, consistent with sensitivity predictions once the ~40% SNR degradation observed on ALMA-APEX is accounted for.  
  > "On the ALMA–APEX baseline, the measured SNR was ∼12, above the threshold but 40% below our estimate of 20. This shortfall indicates additional loss terms not captured in the nominal sensitivity estimate. Applying a comparable degradation to the ALMA–JCMT baseline would place its effective SNR below the detection threshold." (7. Discussion)
- A transportable Vector Atomic iodine optical clock successfully served as the VLBI frequency standard at JCMT, demonstrating short-term phase stability comparable to or exceeding a hydrogen maser.  
  > "On short timescales, the VA clock exhibited stability comparable to, and in some regimes exceeding, that of the SMA hydrogen maser it replaced." (4.2. Frequency Standard)

## Claim tuples

- H: Ground-based VLBI fringe detection in the 690 GHz atmospheric window is technically feasible using the ALMA Phasing System at Band 9 in combination with submillimeter VLBI stations. | E: Conducted a 685 GHz VLBI experiment on 2024 November 21 with phased ALMA (45 antennas), APEX, and JCMT observing quasar J0423-0120, correlating the data with DiFX and fitting fringes with HOPS. | R: Detected statistically significant fringes on the ALMA-APEX baseline in Scan 2 at 691 GHz with SNR = 12.0 (X1X) and 9.7 (Y1Y) over a 60 s fringe search interval and 20 s nominal solution interval. | F: Near-terahertz ground-based VLBI at 690 GHz is technically feasible under excellent weather conditions. | **supported**
- H: The non-detection of 690 GHz fringes on the intercontinental ALMA-JCMT baseline is due to frequency-dependent coherence and sensitivity losses rather than gross instrumental failure, timing errors, or station clock instability. | E: Correlated 230 GHz benchmark scans on the ALMA-JCMT baseline, verified JCMT Band 9 tuning via Orion BN CO(6-5) and telluric H2O spectra, evaluated optical clock Allan variance, and compared predicted vs. measured Band 9 SNRs. | R: Band 6 scans yielded strong fringes (SNR up to 123.3) with aligned clocks/rates; JCMT detected CO(6-5) at 691.435 GHz; clock coherence at 10 s is 0.96 (coherence time 150 s); applying the 40% SNR shortfall seen on ALMA-APEX reduces the predicted ALMA-JCMT SNR of 9 below the detection threshold of ~7. | F: The ALMA-JCMT non-detection is explained by atmospheric decoherence, finite APS phasing cadence (16 s), and frequency-dependent losses rather than instrumental or clock failure. | **supported**
- H: The ALMA Phasing System (APS) with the new delay-fix upgrade can sustain stable phased-array operation at Band 9 across standard 300 s VLBI scans. | E: Operated APS at Band 9 on J0423-0120 (~2.3 Jy) and J0433+0521 across four 300 s scans while monitoring near-real-time phasing efficiency. | R: Phasing efficiency on J0423-0120 began at ~70% or better but degraded to ~30% after 1-2 minutes, and never phased well on the weaker target J0433+0521, whereas 230 GHz scans maintained >90% efficiency over 300 s. | F: APS Band 9 phasing works initially on bright sources under excellent weather but degrades after ~1-2 minutes due to rapid atmospheric fluctuations, dispersive dry-air effects, and the 16 s slow-loop cadence. | **partially**

## Reasoning

- Why this data: Observations were triggered on 2024 November 21 when weather was simultaneously excellent at Chajnantor (PWV 0.46 mm) and Maunakea (PWV 1.3 mm); J0423-0120 was selected as a bright (~2.3 Jy), compact Band 9 calibrator observable above 30 deg elevation at both sites, Orion BN was chosen to verify CO(6-5) spectral tuning, and a 230 GHz session was included as a system benchmark.  
  > "Both are relatively bright in submillimeter wavelengths and are located such that they could be observed from both ALMA/APEX and JCMT at elevations exceeding 30°, ensuring favorable atmospheric transmission." (4.1. The Observing Targets); "In addition, the Becklin–Neugebauer (BN) object in Orion (ORIBN) was selected for dedicated scans to verify the Band 9 spectral-line tuning." (4.1. The Observing Targets); "For the primary and secondary targets, we also scheduled a Band 6 (230 GHz) session as a VLBI benchmark test of overall system, since observations in this band are well established." (4.1. The Observing Targets)
- Why this method: Used the new full-band delay-fix mechanism in APS to reduce residual delay errors across the 2 GHz baseband, disabled 90-deg Walsh switching so the recorded VLBI sum signal was not scrambled, and used segmented incoherent averaging (cohfit) to recover fringe SNR when atmospheric phase fluctuations limit coherent integration.  
  > "To mitigate these challenges, a new phasing mechanism called the delay-fix was introduced—an upgrade that directly measures and corrects delays across the full 2 GHz baseband, replacing the earlier chunked (∼234 MHz) correction scheme." (2. ALMA Phasing System (APS)); "The purpose of the APS is to provide a combined, coherent signal for recording, and the 90° Walsh-switching process completely scrambles the signal that is ultimately recorded." (4.3. RF Frequency and LO); "is more consistent with the segmented, incoherent-averaging approach used in cohfit, in which fringe strength can still be accumulated when residual phase fluctuations limit fully coherent averaging" (Section 6.1)
- Alternative: Standard ALMA Band 9 90-degree Walsh phase-switching for DSB-to-SSB separation was rejected/disabled because it occurs outside the APS domain and scrambles the recorded VLBI signal.  
  > "The purpose of the APS is to provide a combined, coherent signal for recording, and the 90° Walsh-switching process completely scrambles the signal that is ultimately recorded. Thus, during the APS operation, the 90° Walsh-switching must be turned off, and the DSB-to-SSB signal conversion is also disabled." (4.3. RF Frequency and LO)
- Alternative: Adopting the ALMA-APEX 20 s solution interval for the ALMA-JCMT baseline was rejected because ALMA and APEX are separated by only a few km and share partially correlated atmospheric fluctuations; instead, the 230 GHz ALMA-JCMT solution interval (30 s) was scaled inversely with frequency to 10 s.  
  > "Because the two sites are separated by only a few kilometers, atmospheric phase fluctuations sampled by the two stations may remain partially correlated (Matsushita et al. 2017b)." (6.1. Correlation); "Rather than directly adopting the ALMA–APEX value, we use the 230 GHz ALMA–JCMT data as the empirical reference because they sample the same long baseline under similar observing conditions." (6.1. Correlation)
- How they decided it was enough: Required a minimum SNR of ~7 for robust VLBI fringe detection alongside low probability of false detection (PFD) and physical consistency of delay and rate solutions across polarizations and adjacent scans.  
  > "This classification is based not solely on statistical significance, but also on the physical consistency of the fringe solution, including stability of the delay–rate peak across parallel-hand polarizations and comparison between adjacent scans." (6.1. Correlation); "In VLBI practice, a SNR ratio of about ∼7 is generally taken as the minimum for robust fringes (TMS)." (7. Discussion)
- Limitation (authors): The present dataset does not allow a clean separation of the new delay-fix performance from other contributing factors.  
  > "However, as will be shown in the next sections, the APS performance remained limited by signal-to-noise constraints at these frequencies, and the present dataset does not allow a clean separation of delay-fix performance from other contributing factors." (2. ALMA Phasing System (APS))
- Limitation (authors): APS phasing efficiency at Band 9 degraded after ~1-2 minutes toward ~30%, limiting usable scan durations to ~60-90 s.  
  > "The similar pattern in all the scans suggests that the APS could only sustain coherent phasing for about one minute before losing effective phase summation." (6. Results and Analysis)
- Limitation (authors): Adverse weather at the Greenland Telescope (GLT) prevented usable data acquisition there, and a 40 s late recording start at APEX in Scan 1 plus missing polarization channels/data-quality issues in Scan 3 left Scan 2 as the sole robust Band 9 fringe detection.  
  > "However, adverse weather conditions at the GLT site prevented usable data acquisition; no instrumental issues were identified." (5. 2024 November 21 Observation); "recording roughly 40 s late, leaving too little usable overlap for a stable fringe. Scan 3 also produced no detection, consistent with its known data-quality issues and missing polarization channels." (Section 6.1)
- Limitation (authors): No dedicated VLBI amplitude calibration scans were obtained due to limited ALMA time, and single linear polarization recording without quarter-wave plates or PolConvert introduced up to a 29% (cos 45 deg ≈ 0.71) amplitude loss.  
  > "Due to the limited allotted ALMA time allocated to this experiment, no dedicated calibration scans were included." (6.2. Sensitivity Estimation); "In this experiment, all three stations recorded a single linear polarization. In the worst case, an unknown relative polarization angle can reduce the correlated amplitude by a factor of cos 45° ≈ 0.71, corresponding to a conservative ≈29% loss in correlated flux." (7. Discussion)
- Caveat (inferred, ours): Noticeable numerical inconsistency in the source size lower limit for J0423-0120 between Section 7 (≳ 2.6 μas) and Section 8 Summary (≳ 4 μas).
- Caveat (inferred, ours): The detected 690 GHz fringe is exclusively on a short (~2 km, 6 Mλ) baseline sharing the same Chajnantor atmosphere, so intercontinental 690 GHz VLBI fringe detection remains unproven.

## Reproducibility

- Data public (paper): A small sample of the recorded VLBI data is available in the ALMA Archive under project code ADS/JAO.ALMA#2011.0.00014.E.  
  > "The data made available at the ALMA Archive includes a small sample of the recorded VLBI data to allow further investigations of this unique data set." (Acknowledgments); "This paper makes use of the following ALMA data:ADS/JAO.ALMA#2011.0.00014.E." (Acknowledgments)
- Products in archive: _not stated_
- Code: HOPS version 3.26 is publicly available at the MIT Haystack website.  
  > "The HOPS software used in this analysis will is released as version 3.26 and available at https://www.haystack.mit.edu/haystack-observatory-postprocessing-system-hops." (6.1. Correlation)
- Missing: Full raw VLBI baseband recordings from ALMA, APEX, and JCMT (only a small sample is archived under 2011.0.00014.E)
- Missing: DiFX 2.7.1 correlation control files (.v2d, .vex) and station clock/delay model parameters
- Missing: Exact UTC time ranges used for the fringe search intervals (FSI) in Table 2 and Figure 4
- Data volume (inferred): Several terabytes for the raw VLBI baseband recordings across 3 stations (8 Gbps per 2 GHz subband), though the correlated DiFX/HOPS visibility products and archived sample are likely a few gigabytes.
- Score (inferred): 65/5, The post-correlation fringe-fitting software (DiFX 2.7.1, HOPS 3.26, fourfit, cohfit), sensitivity equations, efficiency factors, and Allan variance parameters are clearly documented, and a sample of the VLBI data is archived under 2011.0.00014.E, but full reproduction from raw voltages is limited by the partial data release and missing DiFX correlation configuration files.
- Rediscovery candidate: no, This is a technical VLBI commissioning and fringe-detection experiment where only a small sample of raw VLBI baseband data from ALMA, APEX, and JCMT is archived rather than a complete standard ALMA interferometric dataset.

## Links

- Method: Matthews et al. 2018 ( foundational description of the ALMA Phasing System (APS) architecture and phasing efficiency)
- Method: Matthews & Crew 2024 (ALMA Phasing Project Phase 2 Final Report detailing the full-band delay-fix mechanism)
- Method: Deller et al. 2011 (DiFX software correlator used to correlate the VLBI recordings)
- Method: Rogers et al. 1995 (Statistical fringe detection and incoherent segmented averaging formalism implemented in fourfit and cohfit)
- Method: Whitney et al. 2004 (Mark 4 / HOPS post-processing framework used for VLBI fringe fitting)
- Method: Thompson et al. 2017 (TMS) (Standard radio interferometry reference used for Walsh switching, SNR thresholds, and clock coherence function evaluation)
- Companion: Bintley et al. 2024 (Describes the Kuntur 690 GHz receiver system installed on the JCMT for this VLBI experiment)
- Related: Event Horizon Telescope (EHT)
- Related: ALMA Phasing Project (APP / APP2)
- Related: Large Latin American Millimeter Array (LLAMA)
- Related: Greenland Telescope (GLT)

## Checks

```json
{
 "quotes": 144,
 "quotes_ok": 144,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00014.E"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 64,
  "rate": 0.621
 },
 "evidence_ok": true
}
```
