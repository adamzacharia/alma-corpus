# ALMA High-frequency Long Baseline Campaign in 2017: Band-to-band Phase Referencing in Submillimeter Waves

`2020ApJS..247...23A` | The Astrophysical Journal Supplement Series 2020 | first author: Asaki, Yoshiharu | arXiv: 2003.07472 | DOI: 10.3847/1538-4365/ab6b20

Card schema 1.0 | model gemini-3.8-flash | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, protoplanetary_disks, evolved_stars, agn_and_quasars
- Question: Whether band-to-band (B2B) phase referencing using harmonic frequency switching and differential gain calibration (DGC) enables high-angular-resolution submillimeter imaging on ALMA baselines up to 16 km.  
  > "We investigated image qualities using ALMA receiver Bands 7, 8, 9, and 10 (285–875 GHz) by adopting band-to-band (B2B) phase referencing in which a phase calibrator is tracked at a lower frequency." (abstract); "We aimed to prove that ALMA has observation capabilities in Bands 7, 8, 9, and 10 (285–875 GHz) with up to the longest 16 km baselines using B2B phase referencing." (1 Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "Located in the Taurus molecular cloud, HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc (cite: Rebull2004)." (4.3.2 Complex structure target I: HL Tau in Band 9–4); distance from (cite: Rebull2004)  
  > "Located in the Taurus molecular cloud, HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc (cite: Rebull2004)." (4.3.2 Complex structure target I: HL Tau in Band 9–4)
- Target **VY CMa**: coordinates 7h22m58s.3261, −25°46'03''.038 (J2000)  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc (cite: Zhang2012)." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "The peak position of VY CMa was estimated before the self-calibration to be located at (α, δ)=(7h22m58s.3261, −25°46'03''.038) (J2000)." (4.3.3 Complex structure target II: VY CMa in Band 9–4); z/distance 1.17 kpc  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc (cite: Zhang2012)." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "The peak position of VY CMa was estimated before the self-calibration to be located at (α, δ)=(7h22m58s.3261, −25°46'03''.038) (J2000)." (4.3.3 Complex structure target II: VY CMa in Band 9–4); distance from (cite: Zhang2012)  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc (cite: Zhang2012)." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "The peak position of VY CMa was estimated before the self-calibration to be located at (α, δ)=(7h22m58s.3261, −25°46'03''.038) (J2000)." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- Target **QSO J2228-0753**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **QSO J0633-2333**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV, 2011.0.00011.SV
- bands: Bands 3, 4, 6, 7, 8, 9, 10  
  > "We investigated image qualities using ALMA receiver Bands 7, 8, 9, and 10 (285–875 GHz) by adopting band-to-band (B2B) phase referencing in which a phase calibrator is tracked at a lower frequency." (abstract); "Various harmonic frequency pairs were tested (Bands 7–3, 8–4, 9–4, 9–6, and 10–7)." (3 Strategy of HF-LBC-2017)
- frequencies and spectral setup: LO1: Band 7 at 285/289 GHz; Band 8 at 400/405/462 GHz; Band 9 at 669/671/675 GHz; with LF LO1 at 95/96 GHz (Band 3), 133/135/149/154 GHz (Band 4), 225 GHz (Band 6); 8 SPWs of 1.875 or 2.0 GHz in Band 9 using 90 deg phase switching; 15.625 kHz resolution maser channel for VY CMa  
  > "The LO1 frequencies in Bands 7 and 3 are 285 and 95 GHz, respectively." (4.1 Stage 2: DGC solution stability); "The LO1 frequencies for the target and the phase calibrator are 671 (Band 9) and 149 (Band 4) GHz, respectively. The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 2 GHz each using the 90° phase switching." (4.3.2 Complex structure target I: HL Tau in Band 9–4); "The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 1.875 GHz each using the 90° phase switching. One of the SPWs covers the 658 GHz H2O maser with the frequency resolution of 15.625 kHz." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- continuum bandwidth: 7.5 GHz (Bands 3–8), 15 GHz or 16 GHz (Bands 9 and 10 using 90 deg phase switching)  
  > "The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 2 GHz each using the 90° phase switching." (4.3.2 Complex structure target I: HL Tau in Band 9–4); "The available total bandwidth is 7.5 GHz in Bands 3– 8 assuming that four 1.75 GHz SPWs are used, while in Bands 9 and 10, the total bandwidth is 15 GHz by configuring eight SPWs using the 90° phase switching in the correlator." (5 Discussions)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 16.2 km  
  > "In 2017, an Atacama Large Millimeter/submillimeter Array (ALMA) high-frequency long baseline campaign was organized to test image capabilities with baselines up to 16 km at submillimeter (submm) wavelengths." (abstract); "15−396 m" (Table 3); "233−16196 m" (3 Strategy of HF-LBC-2017)
- angular resolution: 19 x 16 mas (Band 7), 16 x 12 mas (Band 8), 14 x 11 mas (HL Tau Band 9 robust 0.5), 10 x 8 mas (VY CMa Band 9 robust 0.5 maser cube / robust 0 continuum)  
  > "The achieved beam sizes are 19 × 16 and 16 × 12 mas in Bands 7 and 8, respectively." (4.3.1 Point-source target: QSO J2228−0753 in Bands 7–3 and 8–4); "The final beams achieved were 20×18 and 14×11 mas, respectively." (4.3.2 Complex structure target I: HL Tau in Band 9–4); "the resultant synthesized beam size is 10 × 8 mas." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 45 minutes (HL Tau combined 2 EBs); 344 s (VY CMa)  
  > "Combined, there is 45 minutes on-source time for HL Tau." (4.3.2 Complex structure target I: HL Tau in Band 9–4); "The total observing time was 47 minutes, and the on-source time for VY CMa was 344 s." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- observing dates: 2017 March to 2017 November  
  > "From 2017 March to July, we conducted the tests of stages 2 and 3 tests using the mid-baseline lengths (Bmax∼400 m–4 km) to check the DGC solution stability and a basic image performance" (3 Strategy of HF-LBC-2017); "The baselines were longer than 10 km from the middle of July to the end of November, during which time more stage 3 tests and the stage 4 tests were undertaken." (3 Strategy of HF-LBC-2017)
- pi or archival as stated: High Frequency Long Baseline Campaign 2017 (HF-LBC-2017) campaign data  
  > "This paper presents results from our feasibility study made during the High Frequency Long Baseline Campaign 2017 (HF-LBC-2017)." (1 Introduction)
- Line: H2O v2=1, 1(1,0)-1(0,1) (658.00655 GHz)
- External data: ALMA Calibrator Source Catalog with 3316 QSOs  
  > "To answer this question, we conducted calibrator source counts for B2B and in-band phase referencing using the ALMA calibrator source catalog. In the catalogue, 3316 QSOs whose flux densities have been measured with ALMA are available." (5 Discussions) [from https://almascience.nrao.edu/alma-data/calibrator-catalogue]
- External data: HL Tau Band 7 long baseline SV data  
  > "We evaluated the image fidelity of our Band 9 data by comparison with the long baseline SV in Band 7 in LBC-2014 (ADS/JAO.ALMA #2011.0.00015.SV, hereafter LBC-2014-SV)." (4.3.2 Complex structure target I: HL Tau in Band 9–4) [from (cite: ALMApartnership2015b)]
- External data: VY CMa Band 9 SV data from LBC-2013  
  > "making it one of the best targets for the image fidelity check by comparison with the previous SV in Band 9 in LBC-2013 with a Bmax of 2.7 km (ADS/JAO.ALMA #2011.0.00011.SV, hereafter LBC-2013-SV) not only for the continuum emission but also for the 658.00655 GHz v2=1, 11,0−10,1 H2O maser" (4.3.3 Complex structure target II: VY CMa in Band 9–4) [from (cite: Richards2014)]

## Processing

### Calibration

- pipeline or manual: manual flagging and standard ALMA data reduction procedures  
  > "Throughout almost all of the tests, there were a number of manual flagging commands to be entered for these data, mostly for the frequency switching segments, due to the nature of testing such an experimental observation mode" (4 Results); "The data reduction of the in-band phase referencing was undertaken with a standard ALMA data reduction procedure, while the B2B phase referencing data reduction procedure requires the application of the DGC solutions." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: DGC source used as HF flux calibrator (e.g. J0522-3627, J2253+1608)  
  > "For the amplitude calibration, we used the DGC source as an HF flux calibrator in addition to the system noise temperature calibration in both the B2B and in-band phase referencing." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing); "A bright QSO, J0522−3627, 28° away from the target, was used as the DGC source, as well as for bandpass and flux-scale calibration." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration with ~1 s or scan-length solution interval for point sources; phase and amplitude self-calibration with 16 s interval on line-free continuum channels then 4 s interval on bright maser peak for VY CMa  
  > "In order to check the image quality after phase referencing, we performed phase self-calibration (cite: Schwab1980) with a short solution interval (here we could use a solution interval of ∼ 1 s as the S/N was high)" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing); "phase and amplitude self-calibrations were performed for the line-free continuum channels with the solution interval of 16 s to remove residual phase offsets between the SPWs. The self-calibration solutions were then applied to all target data, and the bright maser peak, which has a higher S/N, was used for further self-calibration, now making and applying the solutions with an interval of 4 s to all data." (4.3.3 Complex structure target II: VY CMa in Band 9–4)

### Imaging

- task: CASA CLEAN  
  > "using a Briggs robust 0.5 weighting in CASA CLEAN when combining two EBs taken in the middle of October and the beginning of 2017 November." (4.3.1 Point-source target: QSO J2228−0753 in Bands 7–3 and 8–4)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (stage 3 and QSO stage 4; HL Tau), robust = 2 (VY CMa continuum initial), robust = 0 (VY CMa continuum comparison), natural weighting (HL Tau)  
  > "For the imaging, we use a Briggs weighting with a robustness parameter (robust) of 0.5, as this is representative of the common robust generally used in ALMA images." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing); "For the left and middle images, natural and Briggs (robust = 0.5) weightings are used, as Briggs weightings with smaller robustness parameters form too-sharp beams resolving out almost all of the extended emission." (4.3.2 Complex structure target I: HL Tau in Band 9–4); "The line-free continuum emission image using the averaged eight SPWs with Briggs weighting (robust = 2) is shown in the left panel of Figure 16." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "The continuum image was made with Briggs weighting (robust = 0) to compare relative positions between the photosphere emission and maser cloud emission." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- uv taper: short baselines <500 klambda excluded in test imaging of HL Tau  
  > "Similarly, the right panels of Figure 14 are after reimaging but excluding the short baselines <500 kλ (∼220 m in Band 9 sensitive to scales >0.''5) and using a natural weighting." (4.3.2 Complex structure target I: HL Tau in Band 9–4)
- cell size: 5 (Bands 7 and 8) or 7 (Band 9) pixels covering synthesized beam major axis  
  > "The cell size is chosen such that 5 (for Bands 7 and 8) or 7 (Band 9) pixels cover the synthesized beam major axis." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
- image size: _not stated_
- masking: 15 pixel radius masking box around the target  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target (located at the phase tracking center in the image)." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
- multiscale scales: _not stated_
- continuum subtraction: averaged eight SPWs line-free continuum channels  
  > "The line-free continuum emission image using the averaged eight SPWs with Briggs weighting (robust = 2) is shown in the left panel of Figure 16." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 19 x 16 mas (J2228-0753 Band 7), 16 x 12 mas (J2228-0753 Band 8), 14 x 11 mas (HL Tau Band 9 robust 0.5), 20 x 18 mas (HL Tau natural), 12 x 11 mas (VY CMa continuum robust 2), 10 x 8 mas (VY CMa maser / robust 0 continuum)  
  > "The achieved beam sizes are 19 × 16 and 16 × 12 mas in Bands 7 and 8, respectively." (4.3.1 Point-source target: QSO J2228−0753 in Bands 7–3 and 8–4); "The final beams achieved were 20×18 and 14×11 mas, respectively." (4.3.2 Complex structure target I: HL Tau in Band 9–4); "The synthesized beam size is 12 × 11 mas, and the image RMS noise is 1.5 mJy beam−1." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "the resultant synthesized beam size is 10 × 8 mas." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- final rms: 1.5 mJy/beam (VY CMa robust 2 continuum), 1.8 mJy/beam (VY CMa robust 0 continuum), 1.4 mJy/beam (after self-cal)  
  > "The synthesized beam size is 12 × 11 mas, and the image RMS noise is 1.5 mJy beam−1." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "The continuum emission map has a synthesized beam of 10 × 8 mas and the image RMS noise of 1.8 mJy beam−1." (4.3.3 Complex structure target II: VY CMa in Band 9–4); "Those resolved emissions probably contribute to the slightly high continuum RMS of 1.4 mJy beam−1 while a 0.7–1.0 mJy beam−1 noise level is predicted across the line-free continuum" (4.3.3 Complex structure target II: VY CMa in Band 9–4)

### Inherited from earlier work

- WVR phase correction method and performance  
  > "The WVR phase correction and its performance are described in previous reports (cite: Matsushita2017; Maud2017) and references therein." (2 Basic concept of B2B phase referencing) [from (cite: Matsushita2017; Maud2017)]
- Frequency phase transfer concept  
  > "This procedure is referred to as frequency phase transfer (cite: Rioja2014)." (2.1 B2B phase referencing) [from (cite: Rioja2014)]
- Cross-band differential gain calibration concept  
  > "The instrumental phase offset difference can be independently measured with a cross-band calibration (cite: Holdaway2004b) in which a quasar is observed at ν_HF and ν_LF in turn to obtain the phase difference." (2.2 DGC) [from (cite: Holdaway2004b)]

### Not stated but needed to reproduce (our reading)

- CASA version used for data reduction
- Specific line-free channel ranges for continuum subtraction in VY CMa
- Exact self-calibration gaincal mode, SNR cutoffs, and reference antenna used

## Analysis recipe

1. **WVR and system temperature correction**: Apply water vapor radiometer (WVR) phase correction and system noise temperature calibration to all target, calibrator, and DGC scans.  
  > "The WVR phase correction and the system noise temperature correction have been applied to all of the data before this workflow starts." (2.3 Implementation of B2B phase referencing and DGC)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive DGC solutions for instrumental phase offset differences**: Derive time-averaged LF phase offset on DGC source, apply it to obtain short-term LF phase solutions, scale by frequency ratio R = nu_HF / nu_LF, apply to HF DGC data, and time-average to obtain HF phase offset correction.  
  > "We derive a time-averaged solution for all of the LF DGC scans represents an LF phase offset for each antenna. In the next step, we apply to the LF DGC phases and derive short-term phase solutions for atmospheric phase fluctuations alone... These solutions are frequency phase-transferred, and applied to the HF DGC phases" (2.3 Implementation of B2B phase referencing and DGC); "This should correct the HF atmospheric fluctuations, so the HF DGC data can then be averaged in time and used to derive a HF phase offset... Finally, the HF phase offset correction is applied to the target phase" (2.3 Implementation of B2B phase referencing and DGC)
   - software: CASA
   - parameter: Frequency scaling ratio R = nu_HF / nu_LF  
  > "multiplying by an observing frequency ratio R = nu_HF / nu_LF" (2.1 B2B phase referencing)
   - assumption: Atmospheric delay refraction is predominantly non-dispersive away from strong absorption lines, permitting a simple frequency scaling ratio R.  
  > "The assumption of the nondispersiveness is likely to be correct except close to strong atmospheric water vapor absorption lines (cite: Pardo2001)." (2.1 B2B phase referencing)
   - fitting: Time-averaging phase solutions to suppress thermal and residual atmospheric noise  
  > "If we take a time average of equation (5) to suppress the random noise, we obtain the following phase error" (2.2 DGC)
   - validation: Checked stability of DGC solutions across ~1 hr and across separation angles up to 100 deg on the sky.  
  > "Generally, as part of the later-stage feasibility checks with a baseline out to 16 km, the instrumental phase offset difference determined from the DGC solution is stable for approximately 1 hr." (4.1 Stage 2: DGC solution stability)
3. **Calibrate target data using LF phase calibrator and DGC solution**: Apply LF phase offset to LF phase calibrator, derive short-term atmospheric phase solutions at LF, frequency scale by R, and apply to HF target along with HF DGC phase offset.  
  > "We then apply the LF phase offset to the LF phase calibrator phase to remove the common LF phase offset and to obtain the short term phase solutions containing corrections for atmospheric fluctuations at ν_LF... Finally, the HF phase offset correction is applied to the target phase, along with the time-dependent phase solutions" (2.3 Implementation of B2B phase referencing and DGC)
   - software: CASA
   - fitting: _not stated_
   - validation: Comparative test between B2B and in-band phase referencing on the same calibrator and targets.  
  > "confirm that B2B and in-band phase referencing produce the same result when using the same phase calibrator" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
4. **Deconvolution and imaging**: CLEAN deconvolution using Briggs weighting (robust 0.5, 0, or 2) or natural weighting, cell size with 5 to 7 pixels across synthesized beam major axis.  
  > "For the imaging, we use a Briggs weighting with a robustness parameter (robust) of 0.5, as this is representative of the common robust generally used in ALMA images. A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - software: CASA
   - parameter: robust = 0.5, 50 CLEAN iterations, 15 pixel radius masking box  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target (located at the phase tracking center in the image)." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - fitting: CLEAN deconvolution  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - validation: Comparison to SV images of HL Tau and VY CMa.  
  > "We evaluated the image fidelity of our Band 9 data by comparison with the long baseline SV in Band 7 in LBC-2014" (4.3.2 Complex structure target I: HL Tau in Band 9–4)
5. **Quantify image coherence and perform self-calibration**: Compare peak flux densities before and after phase/amplitude self-calibration to calculate image coherence factor exp(-sigma_phi^2 / 2).  
  > "Here we define the image coherence as the ratio between peak flux densities for data with and without self-calibration applied." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing); "the image coherence can be equivalent to a coherence factor exp(−σ_ϕ^2/2), where σ_ϕ is the residual RMS phase noise in radians (cite: TMS2001)." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - software: CASA
   - parameter: Solution intervals: ~1 s or scan length for bright QSOs, 16 s for continuum channels and 4 s for maser peak in VY CMa  
  > "here we could use a solution interval of ∼ 1 s as the S/N was high" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing); "phase and amplitude self-calibrations were performed for the line-free continuum channels with the solution interval of 16 s to remove residual phase offsets between the SPWs. The self-calibration solutions were then applied to all target data, and the bright maser peak, which has a higher S/N, was used for further self-calibration, now making and applying the solutions with an interval of 4 s to all data." (4.3.3 Complex structure target II: VY CMa in Band 9–4)
   - assumption: Residual RMS phase noise has characteristics of Gaussian random noise  
  > "Assuming that the residual RMS phase noise in the visibility has characteristics of a Gaussian random noise, the image coherence can be equivalent to a coherence factor exp(−σ_ϕ^2/2)" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - fitting: Self-calibration gain solutions (Schwab 1980)  
  > "we performed phase self-calibration (cite: Schwab1980) with a short solution interval" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - validation: Coherence recovery and noise comparison before and after self-calibration.  
  > "After self-calibration, the image noise of the B2B and in-band phase referencing are equivalent, indeed confirming that the residual offsets have been fully corrected." (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing)

## Software

- **CASA** : Data reduction, calibration, imaging (CLEAN), and self-calibration  
  > "For many parts of our data reduction, we made use of the Common Astronomy Software Applications (CASA) package (cite: McMullin2007)." (4 Results)
- **AATM** : Calculation of dispersive delay of atmospheric water vapor at ALMA site  
  > "calculated with the ALMA ATM program (cite: Nikolic2009) and the ALMA bands." (2.1 B2B phase referencing); "AATM (cite: Nikolic2009), CASA (cite: McMullin2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Image coherence for QSO J2228-0753 in Band 7 | 94 | not stated | % | 5 | We obtained high image coherences of 94% and 84% in Bands 7 and 8, respectively, so that B2B phase referencing works effectively in those experiments. |
| Image coherence for QSO J2228-0753 in Band 8 | 84 | not stated | % | 5 | We obtained high image coherences of 94% and 84% in Bands 7 and 8, respectively, so that B2B phase referencing works effectively in those experiments. |
| RMS phase noise for QSO J2228-0753 in Band 7 | 21 | not stated | deg | 5 | The 94% image coherence in Band 7 corresponds to an RMS phase noise of 21°, and the Band 8 image coherence of 84% is consistent with an RMS phase noise of 34°. |
| RMS phase noise for QSO J2228-0753 in Band 8 | 34 | not stated | deg | 5 | The 94% image coherence in Band 7 corresponds to an RMS phase noise of 21°, and the Band 8 image coherence of 84% is consistent with an RMS phase noise of 34°. |
| Naturally weighted peak flux density for HL Tau in Band 9 | 24.9 | not stated | mJy beam-1 | 4 | The naturally weighted HF-LBC-2017 Band 9 image yields a peak of 24.9 mJy beam−1, suggesting a coherence of around 56%. |
| VY CMa continuum peak flux before self-calibration | 42 | not stated | mJy beam-1 | 4 | Improvements were seen on the continuum peak, which increased from 42 to 135 mJy beam−1, while the image RMS noise was largely unchanged at 1.5 mJy beam−1. |
| VY CMa continuum peak flux after self-calibration | 135 | not stated | mJy beam-1 | 5 | Improvements were seen on the continuum peak, which increased from 42 to 135 mJy beam−1, while the image RMS noise was largely unchanged at 1.5 mJy beam−1. |
| VY CMa aperture flux density at 669 GHz | 394 | not stated | mJy | 5 | Fitting to a similar sized-aperture for VY CMa in our image gives 394 mJy at the reference frequency of 669 GHz. |

## Qualitative findings

- Instrumental phase offset differences between low and high frequency bands are stable for approximately 1 hr and across sky separations up to 100 degrees, allowing cross-band differential gain calibration (DGC) with 2-3 scans per execution.  
  > "From the stage 2 test, we found that the DGC is satisfactorily stable, i.e. there are no rapid instrumental variations, excluding obvious problematic antennas. As a whole, the DGC solutions are stable for QSOs with positions separated by 100° apart on the sky." (4.1 Stage 2: DGC solution stability); "Generally, as part of the later-stage feasibility checks with a baseline out to 16 km, the instrumental phase offset difference determined from the DGC solution is stable for approximately 1 hr." (4.1 Stage 2: DGC solution stability)
- B2B phase referencing achieves image coherence comparable to in-band phase referencing when using the same nearby calibrator, and significantly outperforms in-band when a closer calibrator is available at lower frequency.  
  > "Taking into account all the sets of comparative experiments, the image coherence of B2B phase referencing is comparable to that of in-band phase referencing when using the same close phase calibrator" (4.2 Stage 3: image quality comparative test between B2B and in-band phase referencing); "These results demonstrate that the use of a closer phase calibrator together with B2B phase referencing can improve the image quality compared with in-band phase referencing in Bands 8–10." (6 Summary)
- For extended sources like HL Tau and VY CMa, the lack of short (u,v) coverage on 16 km baseline configurations leads to severe resolving out of extended structures and side-lobe striping, demonstrating the critical need for multi-configuration array combination.  
  > "Our results highlight that, for high-fidelity images of extended sources, it is essential to consider the combination of multiple array configurations to acquire shorter (u, v) coverages for achieving not only a detectable sensitivity but also well-sampled spatial frequency components." (6 Summary)

## Claim tuples

- H: Band-to-band (B2B) phase referencing using harmonic frequency switching can stabilize ALMA interferometer phases on baselines up to 16 km at submillimeter wavelengths (receiver Bands 7, 8, 9). | E: Observed test targets including a quasar (J2228-0753), a protoplanetary disk (HL Tau), and a red supergiant (VY CMa) using fast switching between targets and low-frequency calibrators with DGC scans to remove instrumental phase offset differences. | R: Obtained image coherences of 94% in Band 7, 84% in Band 8, and resolved HL Tau and VY CMa with synthesized beams as fine as 10 x 8 mas in Band 9. | F: B2B phase referencing is technically feasible and effective for submillimeter long-baseline imaging with ALMA. | **supported**
- H: Image coherence in submillimeter long baseline observations degrades with calibrator separation angle, requiring calibrators within ~6 degrees to maintain >=70% coherence. | E: Conducted comparative Band 8-4 imaging of QSO J0633-2333 with phase calibrators at separation angles from 1.2 to 8.7 degrees. | R: Image coherence dropped from ~100% at 1.2 deg to 71% at 5.8 deg and 64% at 8.7 deg. | F: Calibrators should be located within ~5-6 degrees of the target to maintain >=70% coherence. | **supported**
- H: B2B phase referencing significantly increases the probability of finding a suitable phase calibrator close to a target compared to in-band phase referencing in Bands 8, 9, and 10. | E: Evaluated phase calibrator availability and mean separation angles using the ALMA calibrator source catalog (3316 QSOs) for both B2B and in-band phase referencing. | R: Mean separation angles for B2B phase referencing are 3.5-3.6 deg (Band 8), 4.1 deg (Band 9), and 4.3-5.4 deg (Band 10), compared to in-band separations of 5.0 deg (Band 8), 7.8 deg (Band 9), and 12.6 deg (Band 10). | F: B2B phase referencing provides substantial advantages for calibrator selection in Bands 8–10, whereas Band 7 shows comparable availability between in-band and B2B. | **supported**

## Reasoning

- Why this data: ALMA Long Baseline Campaign 2017 commissioning data taken specifically to develop and test high-frequency long-baseline capabilities up to 16 km using band-to-band phase referencing.  
  > "In order to offer new ALMA image capabilities at the highest angular resolutions, implementation of B2B phase referencing is crucial. This was the focus of the fourth long baseline capability campaign organized in 2017." (1 Introduction)
- Why this method: Harmonic frequency switching allows switching between bands in ~2 s without retuning the photonic local oscillator, enabling fast switching cycle times of 20 s necessary for submillimeter atmospheric phase correction.  
  > "To minimize the overhead time and maximize reliability when using B2B phase referencing, we switch Bands using a fixed photonic LO frequency for both receivers" (2.5 Harmonic frequency switching); "This technique is referred to as harmonic frequency switching and can minimize the overhead to ∼ 2 s." (2.5 Harmonic frequency switching)
- Alternative: Standard in-band phase referencing rejected for general submillimeter long-baseline observing due to lack of sufficiently bright calibrators close to targets.  
  > "However, as the observing frequency increases, the flux densities of most QSOs diminish, and the system noise temperature rises. This indicates that fewer bright-enough phase calibrators are available close to targets at arbitrary sky positions." (1 Introduction)
- Alternative: Retuning photonic LO for frequency switching rejected due to ~20 s overhead per switch, which makes 20 s fast switching cycles impossible.  
  > "a temporal overhead of ∼ 20 s takes place for every frequency switching event that requires a retuning of the photonic local oscillator (LO) signal (cite: Shillue2012). This hinders the fast switching and essentially makes 20 s switching cycle times with frequency switching impossible." (2.5 Harmonic frequency switching)
- How they decided it was enough: Verified instrumental phase offset stability over ~1 hr and across 100 deg separation, and confirmed image reconstruction against known science verification structures in Band 7 (HL Tau) and Band 9 (VY CMa).  
  > "From the stage 2 test, we found that the DGC is satisfactorily stable, i.e. there are no rapid instrumental variations, excluding obvious problematic antennas." (4.1 Stage 2: DGC solution stability); "We evaluated the image fidelity of our Band 9 data by comparison with the long baseline SV in Band 7 in LBC-2014" (4.3.2 Complex structure target I: HL Tau in Band 9–4)
- Limitation (authors): Undersampling of short baselines on 14-16 km configurations causes severe side-lobe striping and resolves out extended structures in sources like HL Tau and VY CMa.  
  > "Furthermore, due to the relatively short on-source time and the handful of short baselines, the poor (u, v) sampling of the largely extended disk structure causes a striped side-lobe pattern throughout our Band 9 image at the 50%–60% level with natural weighting." (4.3.2 Complex structure target I: HL Tau in Band 9–4)
- Limitation (authors): Submillimeter atmospheric water vapor dispersion near strong absorption lines was not corrected by the simple frequency scaling ratio R.  
  > "Although spectral regions with a relatively large dispersive term were used in Bands 8 and 10, we adopted the simple frequency scaling ratio for B2B phase referencing because other comparable delay errors, such as the antenna position errors, do not have a frequency dependence." (3 Strategy of HF-LBC-2017); "Another important subject not fully investigated for HFs is where the dispersive term of the atmospheric water vapor is greater than a few tens of percent." (6 Summary)
- Limitation (authors): Higher manual flagging rate required during frequency switching segments and occasional antenna phase drifts in DGC solutions.  
  > "Throughout almost all of the tests, there were a number of manual flagging commands to be entered for these data, mostly for the frequency switching segments, due to the nature of testing such an experimental observation mode" (4 Results); "there were several technical problems in the experiments, for example, more flagged raw data comparing with the ordinal ALMA observations and some problematic antennas showing a relatively large phase drift in the DGC solution in some cases." (6 Summary)
- Caveat (inferred, ours): Campaign observations were conducted during available engineering test slots rather than strictly optimum weather conditions, resulting in high atmospheric phase noise in Band 9.
- Caveat (inferred, ours): B2B phase referencing introduces additional noise into HF phases via scaling thermal noise from LF calibrator by R, requiring bright LF calibrators.
- Caveat (inferred, ours): Astrometric peak offsets of tens of mas between campaigns may be confounded by proper motion, annual parallax, or beam convolution of asymmetric diffuse structure.

## Reproducibility

- Data public (paper): Execution block UIDs listed in tables; comparison SV datasets explicitly referenced  
  > "EB (uid://A002/)" (Table 3); "For this research, we used the ALMA data listed in Tables 3–tbl:05, in addition to ADS/JAO.ALMA #2011.0.00015.SV and (HL Tau in Band 7) ADS/JAO.ALMA #2011.0.00011.SV (VY CMa in Band 9)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Specific CASA calibration scripts implementing the DGC phase extraction, scaling, and application pipeline.
- Missing: List of manual flagging commands applied to frequency switching segments.
- Missing: Detailed continuum channel selection mask for VY CMa.
- Data volume (inferred): 100 GB - 500 GB
- Score (inferred): 6/5, The paper provides complete lists of execution block UIDs and explains the mathematical and logical workflow of B2B phase referencing and DGC calibration clearly. However, extensive manual flagging was required during data reduction, exact calibration scripts are not provided, and full detailed results of the 50-dataset stage 3 study are deferred to companion papers (Maud et al. 2020, Asaki et al. 2019).
- Rediscovery candidate: no, This is a technical commissioning and calibration methodology paper establishing observation modes rather than deriving standalone astrophysical parameters amenable to blind re-derivation.

## Links

- Method: (cite: McMullin2007) (CASA software reference)
- Method: (cite: Nikolic2009) (ALMA ATM program (AATM) reference)
- Method: (cite: Rioja2014) (Frequency phase transfer method reference)
- Method: (cite: Holdaway2004b) (Cross-band differential gain calibration reference)
- Companion: (cite: Asaki2019) (Detailed presentation of stage 4 QSO J2228-0753 long baseline imaging results)
- Companion: (cite: Maud2020) (Detailed presentation of the full 50-dataset stage 3 comparative study)
- Related: ALMA Long Baseline Campaign 2013 (LBC-2013)
- Related: ALMA Long Baseline Campaign 2014 (LBC-2014)
- Related: ALMA Long Baseline Campaign 2015 (LBC-2015)
- Related: ALMA High Frequency Long Baseline Campaign 2017 (HF-LBC-2017)

## Checks

```json
{
 "quotes": 119,
 "quotes_ok": 111,
 "quote_pass_rate": 0.933,
 "quotes_too_long": 13,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 62,
  "rate": 0.705
 },
 "evidence_ok": false
}
```
