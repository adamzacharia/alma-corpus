# ALMA High-frequency Long Baseline Campaign in 2017: Band-to-band Phase Referencing in Submillimeter Waves

`2020ApJS..247...23A` | The Astrophysical Journal Supplement Series 2020 | first author: Asaki, Yoshiharu | arXiv: 2003.07472 | DOI: 10.3847/1538-4365/ab6b20

Card schema 1.0 | model claude-haiku-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, protoplanetary_disks, evolved_stars
- Question: Can band-to-band (B2B) phase referencing, with a phase calibrator tracked at a lower frequency, give high-quality ALMA images at submm frequencies (Bands 7-10) on baselines up to 16 km, and how does its image quality and calibrator availability compare with in-band phase referencing?  
  > "We investigated image qualities using ALMA receiver Bands 7, 8, 9, and 10 (285–875 GHz) by adopting band-to-band (B2B) phase referencing in which a phase calibrator is tracked at a lower frequency." (abstract)
- Target **QSO J2228-0753 (point-source test, Bands 7-3 and 8-4)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc (cite: Rebull2004)." (Complex structure target I: HL Tau in Band 9-4); distance from Rebull2004 (cite)  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc (cite: Rebull2004)." (Complex structure target I: HL Tau in Band 9-4)
- Target **VY CMa**: coordinates _not stated_; z/distance 1.17 kpc  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc (cite: Zhang2012)." (Complex structure target II: VY CMa in Band 9-4); distance from Zhang2012 (cite)  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc (cite: Zhang2012)." (Complex structure target II: VY CMa in Band 9-4)
- Target **QSO J0633-2333 (stage 3 comparison target, Band 8-4)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV, 2011.0.00011.SV
- bands: Bands 7, 8, 9 used for results; Band 10 tests failed and are not reported; Bands 3-7 used on the low-frequency side  
  > "We conducted two Band 10 experiments, one each for stages 2 and 3. Both failed after that because the observed sources were too weak to confirm whether the fringes were detected or not." (Strategy of HF-LBC-2017)
- frequencies and spectral setup: Target/phase-calibrator LO1 pairs: QSO 289 GHz (Band 7) and 405 GHz (Band 8) with LF 96 and 135 GHz; HL Tau 671 GHz (Band 9) with LF 149 GHz; VY CMa 669 GHz (Band 9) with LF 149 GHz  
  > "The high LO1 frequencies are 289 (Band 7) and 405 (Band 8) GHz, while the corresponding low LO1 frequencies are 96 (Band 3) and 135 (Band 4) GHz, respectively." (Point-source target: QSO J2228$-$0753 in Bands 7–3 and 8–4); "The LO1 frequencies for the target and the phase calibrator are 671 (Band 9) and 149 (Band 4) GHz, respectively." (Complex structure target I: HL Tau in Band 9–4)
- continuum bandwidth: Band 9 HL Tau: 8 SPWs x 2 GHz with 90 degree phase switching; VY CMa: 8 SPWs x 1.875 GHz; Bands 3-8 nominal 7.5 GHz in the calibrator-availability analysis  
  > "The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 2 GHz each using the $90^{\circ}$ phase switching." (Complex structure target I: HL Tau in Band 9–4); "The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 1.875 GHz each using the $90^{\circ}$ phase switching." (Complex structure target II: VY CMa in Band 9–4)
- arrays: 12 m antenna arrays; stage 4 configurations with 40-50 antennas; mid-baseline stages with about 20 or more antennas  
  > "Array configurations with $B_{\mathrm{max}}\sim 14-16$ km were arranged containing 40–50 12-m antennas." (Stage 4: high angular resolution imaging test)
- configurations: _not stated_
- baselines: Stage 2: 400 m to 3 km; stage 3: 400 m to 4 km and later over 10 km; stage 4: 133 m to 13.8 km (Band 9)  
  > "The longest and shortest baseline lengths are 13.8 km and 133 m, corresponding to angular resolutions of 7 mas and 0.7 arcsec in Band 9, respectively." (Stage 4: high angular resolution imaging test)
- angular resolution: HL Tau 14x11 mas (Briggs robust 0.5); VY CMa 10x8 mas  
  > "allowing us to achieve an angular resolution of $14 \times 11$ and $10 \times 8$ mas for HL Tau and VY CMa, respectively." (abstract)
- max recoverable scale: Not sampled above about 0.2 arcsec in stage 4 (few baselines shorter than 200 m)  
  > "Note, there were only a few baselines shorter than 200 m during the stage-4 period and thus we could not properly sample structures larger than 0.2 arcsec." (Stage 4: high angular resolution imaging test)
- sensitivity: _not stated_
- time on source: HL Tau 45 min combined on-source; VY CMa 344 s on-source  
  > "Combined, there is 45 minutes on-source time for HL Tau." (Complex structure target I: HL Tau in Band 9–4); "The total observing time was 47 minutes, and the on-source time for VY CMa was 344 s." (Complex structure target II: VY CMa in Band 9–4)
- observing dates: Campaign ran 2017 (stages from March to November); HL Tau and VY CMa observed 2017 Nov 3; QSO EBs mid-October and early November 2017  
  > "On 2017 November 3,VY CMa was observed in Band 9 with a switching cycle time of 82 s." (Complex structure target II: VY CMa in Band 9–4); "when combining two EBs taken in the middle of October and the beginning of 2017 November." (Stage 4: high angular resolution imaging test)
- pi or archival as stated: Observations made in the authors' own HF-LBC-2017 campaign; proposal codes not printed for these data  
  > "This was the focus of the fourth long baseline capability campaign organized in 2017." (Introduction)
- Line: H2O (water maser) v2=1, 1(1,0)-1(0,1) (658.00655 GHz)
- Other facility **ALMA calibrator source catalog**: Flux densities of 3316 QSOs measured with ALMA, used for calibrator source counts  
  > "In the catalogue, 3316 QSOs whose flux densities have been measured with ALMA are available." (Discussions)
- External data: Band 7 continuum peak of 11.56 mJy/beam from LBC-2014-SV, used to scale expected Band 9 peak for HL Tau  
  > "scaling from the LBC-2014-SV Band 7 data (11.56 mJy beam$^{-1}$," (Complex structure target I: HL Tau in Band 9–4) [from (cite: ALMApartnership2015b)]
- External data: Stellar contribution of 111-124 mJy at around 658 GHz for VY CMa  
  > "estimated a stellar contribution of 111–124 mJy at around 658 GHz based on the analytical stellar properties." (Complex structure target II: VY CMa in Band 9–4) [from (cite: OGorman2015)]
- External data: VY CMa photosphere diameter of 11.4 mas  
  > "It is expected that the unresolved point source in HF-LBC-2017 represents the RSG photosphere with the diameter of 11.4 mas" (Complex structure target II: VY CMa in Band 9–4) [from (cite: Wittkowski2012)]
- External data: HL Tau distance 140 pc  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc" (Complex structure target I: HL Tau in Band 9–4) [from (cite: Rebull2004)]
- Simulation/model as data: Relative dispersive delay at PWV = 1 mm computed with the ALMA ATM program, used to judge frequency-ratio dispersion; not a simulated dataset  
  > "calculated with the ALMA ATM program" (Basic concept of B2B phase referencing)

## Processing

### Calibration

- pipeline or manual: In-band data reduced with a standard ALMA procedure; B2B data additionally need DGC solutions; manual flagging commands were entered for frequency-switching segments  
  > "The data reduction of the in-band phase referencing was undertaken with a standard ALMA data reduction procedure" (Results); "there were a number of manual flagging commands to be entered for these data" (Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: DGC source used as an HF flux calibrator (stage 3); QSO J0522-3627 used as DGC source and for bandpass and flux-scale calibration for VY CMa  
  > "we used the DGC source as an HF flux calibrator in addition to the system noise temperature calibration in both the B2B and in-band phase referencing" (Stage 3: image quality comparative test between B2B and in-band phase referencing); "as well as for bandpass and flux-scale calibration." (Complex structure target II: VY CMa in Band 9–4)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration with ~1 s solution interval (stage 3, high S/N); target-scan-length solution for QSO; VY CMa continuum 16 s then maser-peak 4 s solutions; HL Tau not self-calibrated  
  > "with a short solution interval (here we could use a solution interval of $\sim 1$ s as the S/N was high)" (Stage 3: image quality comparative test between B2B and in-band phase referencing); "phase and amplitude self-calibrations were performed for the line-free continuum channels with the solution interval of 16 s" (Complex structure target II: VY CMa in Band 9–4); "We have not, however, performed any form of self-calibration" (Complex structure target I: HL Tau in Band 9–4)

### Imaging

- task: CASA CLEAN (task name not stated)  
  > "using a Briggs robust 0.5 weighting in CASA CLEAN" (Stage 4: high angular resolution imaging test)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (stage 3 and QSO/HL Tau HF images); natural weighting for HL Tau Band 9 image; robust = 2 for VY CMa continuum; robust = 0.5 for VY CMa maser cube; robust = 0 for VY CMa continuum used for position comparison  
  > "we use a Briggs weighting with a robustness parameter (robust) of 0.5" (Stage 3: image quality comparative test between B2B and in-band phase referencing); "with Briggs weighting (robust $= 2$)" (Complex structure target II: VY CMa in Band 9–4)
- uv taper: _not stated_
- cell size: Cell chosen so that 5 pixels (Bands 7 and 8) or 7 pixels (Band 9) cover the synthesized beam major axis  
  > "The cell size is chosen such that 5 (for Bands 7 and 8) or 7 (Band 9) pixels cover the synthesized beam major axis." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- image size: _not stated_
- masking: Fixed 50 CLEAN iterations with a 15 pixel radius box around the target at the phase tracking center  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Line-free continuum channels used for VY CMa; channel selection not stated  
  > "phase and amplitude self-calibrations were performed for the line-free continuum channels with the solution interval of 16 s" (Complex structure target II: VY CMa in Band 9–4)
- primary beam correction: _not stated_
- array combination: HL Tau: two EBs combined; VY CMa: eight SPWs averaged for the continuum image  
  > "Figure 14 presents the HF-LBC-2017 images of HL Tau in Band 9 after combining the two EBs." (Complex structure target I: HL Tau in Band 9–4)
- smoothing: _not stated_
- final beam: VY CMa continuum 10x8 mas  
  > "The continuum emission map has a synthesized beam of $10 \times 8$ mas and the image RMS noise of 1.8 mJy beam$^{-1}$." (Complex structure target II: VY CMa in Band 9–4)
- final rms: VY CMa continuum 1.8 mJy/beam  
  > "The continuum emission map has a synthesized beam of $10 \times 8$ mas and the image RMS noise of 1.8 mJy beam$^{-1}$." (Complex structure target II: VY CMa in Band 9–4)

### Inherited from earlier work

- WVR phase correction and its performance taken from previous reports  
  > "The WVR phase correction and its performance are described in previous reports" (Basic concept of B2B phase referencing) [from (cite: Matsushita2017; Maud2017)]
- Cross-band calibration method for the instrumental phase offset difference (DGC)  
  > "The instrumental phase offset difference can be independently measured with a cross-band calibration" (DGC) [from (cite: Holdaway2004b)]
- Frequency phase transfer procedure  
  > "This procedure is referred to as frequency phase transfer" (B2B phase referencing) [from (cite: Rioja2014)]
- Full stage-3 data reduction and 50-dataset study deferred to a forthcoming paper  
  > "The full study of 50 datasets will be detailed in the forthcoming paper" (Stage 3: image quality comparative test between B2B and in-band phase referencing) [from (cite: Maud2020)]
- Further observation and data analysis details of the Band 7-3 and 8-4 QSO and related experiments  
  > "Further details of the observations and data analysis results are described in another paper" (Complex structure target II: VY CMa in Band 9–4) [from (cite: Asaki2019)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and imaging task settings (tclean or CLEAN), CLEAN threshold and convergence rules beyond the fixed 50 iterations
- Identity of the manually flagged scans, frequency-switching segments and antennas (for example the longest-baseline antennas flagged for HL Tau)
- Method used to remove the linear trend from the DGC solutions and the time-averaging window for each DGC block
- How LF SPW phases are mapped to HF SPWs and how the 90 degree phase switching is combined in the frequency transfer
- Which calibrator scans were culled to emulate longer switching cycles, and how
- Definition of the self-calibration mode and solution-interval rules for each QSO image, and the peak-measurement region used for image coherence
- Source list and flux-density extrapolation rules (power-law fit range) for the calibrator counts, plus the top-30% flux cut

## Analysis recipe

1. **derive the DGC instrumental phase offset**: Average LF DGC phases over all scans per antenna, subtract to get short-term LF atmospheric solutions, frequency-transfer them to the HF DGC phases, average HF DGC phases to one HF offset (the DGC solution)  
  > "We derive a time-averaged solution for all of the LF DGC scans" (Implementation of B2B phase referencing and DGC)
   - software: CASA
   - parameter: Switching cycle time for frequency switching of 20-30 s; WVR correction applied before workflow  
  > "The switching cycle time for the frequency switching is of the order of 20 – 30 s." (DGC)
   - assumption: Ionospheric term negligible for small perturbations such as MSTIDs  
  > "The first term is negligible for relatively small ionospheric perturbations, such as MSTIDs." (DGC)
   - fitting: _not stated_
   - validation: RMS phase noise of DGC solutions typically 10-20 deg in Band 7 and 30-40 deg in Bands 8 and 9  
  > "the RMS phase noise of the DGC solutions is typically $10^{\circ}$–$20^{\circ}$ in Band 7, while this can increase to $30^{\circ}$–$40^{\circ}$ in Bands 8 and 9." (Stage 2: DGC solution stability)
2. **apply B2B correction to the target and image it**: Subtract the frequency-transferred LF calibrator phase (scaled by R = nu_HF/nu_LF, averaged over the two closest calibrator scans) from the target phase, then apply the DGC offset  
  > "The B2B phase referencing is carried out by subtracting $\Phi^{\mathrm{C}}_{\mathrm{cal}}$ of" (B2B phase referencing)
   - software: CASA
   - parameter: Briggs robust 0.5, 50 CLEAN iterations, 15 pixel masking box  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - assumption: Phase calibrator separation of 1-2 deg for B2B tests  
  > "B2B phase referencing uses a small separation of $1^{\circ}$–$2^{\circ}$" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - fitting: _not stated_
   - validation: Comparison with in-band phase referencing using the same calibrator  
  > "confirm that B2B and in-band phase referencing produce the same result when using the same phase calibrator" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
3. **quantify image coherence after phase referencing**: Apply phase self-calibration with short solution interval; coherence is the ratio of peak flux densities with and without self-calibration  
  > "Here we define the image coherence as the ratio between peak flux densities for data with and without self-calibration applied." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - parameter: Self-calibration solution interval about 1 s for stage 3 (high S/N)  
  > "with a short solution interval (here we could use a solution interval of $\sim 1$ s as the S/N was high)" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - assumption: Residual RMS phase noise is Gaussian, so coherence equals a coherence factor  
  > "Assuming that the residual RMS phase noise in the visibility has characteristics of a Gaussian random noise" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - fitting: _not stated_
   - validation: Atmospheric phase over switching cycle below 35 deg, expected coherence above 85%  
  > "the atmospheric phase fluctuations over the switching cycle time are low ($<35^{\circ}$)" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
4. **image the QSO, HL Tau and VY CMa targets at the highest resolution**: Briggs or natural weighting images of each target; VY CMa maser cube at 8 km/s with 18 averaged channels; comparison with LBC-2013-SV and LBC-2014-SV images  
  > "A bright submm H$_{2}$O maser cube with a velocity resolution of 8 km s$^{-1}$ was generated for the 18 averaged frequency channels" (Complex structure target II: VY CMa in Band 9–4)
   - software: CASA
   - parameter: Continuum self-calibration for VY CMa: 16 s then 4 s solutions  
  > "the bright maser peak, which has a higher S/N, was used for further self-calibration, now making and applying the solutions with an interval of 4 s to all data." (Complex structure target II: VY CMa in Band 9–4)
   - assumption: Distances: HL Tau 140 pc; VY CMa 1.17 kpc  
  > "located at a distance of 1.17 kpc (cite: Zhang2012)" (Complex structure target II: VY CMa in Band 9–4)
   - fitting: Two-dimensional Gaussian fit to VY CMa in the LBC-2013-SV image for comparison; aperture sum for our image  
  > "A resolved two-dimensional Gaussian component fitted to VY CMa in the LBC-2013-SV image" (Complex structure target II: VY CMa in Band 9–4)
   - validation: Comparison with previous ALMA SV images in Band 7 (LBC-2014-SV) and Band 9 (LBC-2013-SV)  
  > "We evaluated the image fidelity of our Band 9 data by comparison with the long baseline SV in Band 7 in LBC-2014 (ADS/JAO.ALMA #2011.0.00015.SV, hereafter LBC-2014-SV)." (Complex structure target I: HL Tau in Band 9–4)
5. **assess phase calibrator availability for B2B vs in-band phase referencing**: Count ALMA calibrator QSOs above a flux requirement set by sensitivity; derive mean angular separation per band  
  > "First, we count only the sources whose flux density is higher than the flux density requirement." (Discussions)
   - parameter: Phase calibrator scan length fixed to 8 s; total bandwidth 7.5 GHz (Bands 3-8) or 15 GHz (Bands 9-10)  
  > "The phase calibrator scan length is fixed to 8 s." (Discussions)
   - assumption: Antennas pointed at zenith for sensitivity; galactic crowding of calibrators assumed not to bias the statistics  
  > "The antennas are assumed to be directed to zenith." (Discussions)
   - fitting: Flux density at arbitrary frequency from a power-law nu^alpha fit to Band 3-7 or Band 3-6 measurements; highest value used for multi-epoch sources  
  > "flux density at an arbitrary frequency is evaluated by fitting the flux density measurements between Bands 3 and 7 or Bands 3 and 6 to a power-law function of $\nu^{\alpha}$" (Discussions)
   - validation: Calibrator distribution bias judged not to affect the result  
  > "We conclude that the current investigation is not seriously affected by the calibrator distribution bias." (Discussions)

## Software

- **CASA** : Data reduction (including CLEAN imaging with Briggs weighting) for many parts of the reduction  
  > "For many parts of our data reduction, we made use of the Common Astronomy Software Applications (CASA) package" (Results); "using a Briggs robust 0.5 weighting in CASA CLEAN" (Stage 4: high angular resolution imaging test)
- **AATM (ALMA ATM program)** : Calculating the dispersive atmospheric water-vapour delay at PWV = 1 mm (Figure 2)  
  > "calculated with the ALMA ATM program" (Basic concept of B2B phase referencing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DGC solution RMS phase noise in Band 7 | 10-20 | not stated | degrees | 1 | the RMS phase noise of the DGC solutions is typically $10^{\circ}$–$20^{\circ}$ in Band 7, while this can increase to $30^{\circ}$–$40^{\circ}$ in Bands 8 and 9. |
| DGC solution RMS phase noise in Bands 8 and 9 | 30-40 | not stated | degrees | 1 | while this can increase to $30^{\circ}$–$40^{\circ}$ in Bands 8 and 9. |
| Image coherence, Band 8-4, calibrator at 5.8 deg | 71 | not stated | % | 3 | Relative to the self-calibrated image, the image coherence is 71% and 64% for the $5.^{\circ}8$ and $8.^{\circ}7$ separation angles. |
| Image coherence, Band 8-4, calibrator at 8.7 deg | 64 | not stated | % | 3 | Relative to the self-calibrated image, the image coherence is 71% and 64% for the $5.^{\circ}8$ and $8.^{\circ}7$ separation angles. |
| Phase calibrator separation for image coherence of 70% or more | 6 (within about 6 deg) | not stated | degrees | 3 | the phase calibrator separation angle should be within $\sim 6^{\circ}$ |
| Image coherence of QSO J2228-0753 in Band 7 | 94 | not stated | % | 4 | We obtained high image coherences of 94% and 84% in Bands 7 and 8, respectively |
| Image coherence of QSO J2228-0753 in Band 8 | 84 | not stated | % | 4 | We obtained high image coherences of 94% and 84% in Bands 7 and 8, respectively |
| HL Tau Band 9 natural-weighted peak flux density | 24.9 | not stated | mJy/beam | 4 | The naturally weighted HF-LBC-2017 Band 9 image yields a peak of 24.9 mJy beam$^{-1}$, suggesting a coherence of around 56%. |
| HL Tau Band 9 image coherence (lower limit) | 56 | not stated | % | 4 | suggesting a coherence of around 56% |
| HL Tau beam size, Briggs robust 0.5 | 14x11 | not stated | mas | 4 | The final beams achieved were 20$\times$18 and 14$\times$11 mas, respectively. |
| VY CMa continuum peak before and after self-calibration | 42 to 135 | not stated | mJy/beam | 4 | Improvements were seen on the continuum peak, which increased from 42 to 135 mJy beam$^{-1}$ |
| VY CMa image coherence loss after B2B referencing | 70 | not stated | % | 4 | This indicates that stochastic phase errors remained even after B2B phase referencing, which gave an image coherence loss of $\sim 70$%. |
| VY CMa flux density in aperture at 669 GHz | 394 | not stated | mJy | 4 | Fitting to a similar sized-aperture for VY CMa in our image gives 394 mJy at the reference frequency of 669 GHz. |
| VY CMa peak position offset from LBC-2013-SV position | (47, 5) | not stated | mas | 4 | The position is offset by (47, 5) mas from the position measured from the most astrometrically accurate LBC-2013-SV observations at 321 GHz in Band 7 |
| VY CMa Band 9 RMS phase and coherence loss | 80 deg, 62% coherence loss | not stated | degrees; % | 4 | The RMS phase was extremely high for all of our Band 9 observations around $80^{\circ}$, corresponding to a coherence loss of 62%. |
| Mean separation angle to in-band phase calibrator in Band 10 | 12.6 | not stated | degrees | 5 | Band 10 is the most difficult Band in searching for an in-band phase calibrator, whose expected mean separation angle is $12.^{\circ}6$. |

## Qualitative findings

- DGC solution shows no significant phase instability and is successfully applied to the target phase after B2B phase referencing  
  > "The DGC solution shows no significant phase instability and is successfully applied to the target phase after B2B phase referencing" (Summary)
- B2B phase referencing is more beneficial for finding a phase calibrator in Bands 8-10 while there is no apparent merit in Band 7  
  > "B2B phase referencing is more beneficial for finding a phase calibrator in Bands 8–10 while there is no apparent merit in Band 7" (Summary)
- Stage-4 Band 9 HL Tau image arguably as good as Band 7 image after fair comparison  
  > "based upon these fairer comparisons, our Band 9 image of HL Tau is arguably as good as that in Band 7." (Complex structure target I: HL Tau in Band 9–4)

## Claim tuples

- H: B2B phase referencing can be used to image sources with high angular resolution at submm frequencies on long baselines | E: Stage 4 imaging of QSO J2228-0753 (Bands 7 and 8), HL Tau and VY CMa (Band 9) using B2B phase referencing with self-calibration coherence check | R: Coherence 94% (Band 7) and 84% (Band 8) for the QSO; beams of 14x11 mas (HL Tau) and 10x8 mas (VY CMa) | F: B2B phase referencing has been technically proved effective for high-frequency long-baseline observations | **supported**
- H: B2B phase referencing performs as well as in-band phase referencing when the same nearby calibrator is used | E: Stage 3 comparison in Band 8-4 with the same phase calibrator for B2B and in-band referencing, using self-calibration to measure coherence | R: Peak flux densities almost identical; image coherence almost unity for the close calibrator | F: B2B coherence is comparable to in-band coherence when the same close calibrator is used, with in-band marginally better because of the extra DGC requirement | **supported**
- H: Image quality degrades with increasing phase calibrator separation, so closer calibrators are needed | E: Band 8-4 comparison with in-band calibrators at 1.2, 3.8, 5.8 and 8.7 deg from the target | R: Peak flux falls below 80% at 5.8 and 8.7 deg; coherence 71% and 64% at those separations | F: A calibrator within about 6 deg is needed for coherence of at least 70%; the 6 deg limit is from one experiment set | **partially**
- H: B2B phase referencing allows closer phase calibrators than in-band referencing, especially at high frequency | E: Calibrator source counts from the ALMA calibrator catalog with flux requirements per band for B2B and in-band referencing | R: In-band mean separation in Band 10 is 12.6 deg; B2B availability superior in Bands 8, 9 and 10 but comparable in Band 7 | F: B2B is more beneficial for finding a phase calibrator in Bands 8-10 and offers no apparent merit in Band 7 | **supported**

## Reasoning

- Why this data: Tests cover stages from mid-baseline to 16 km to check DGC stability, comparative image quality and imaging of real sources  
  > "(4) verify that astronomical celestial sources can be imaged with a suitable image fidelity at HFs using long baselines." (Strategy of HF-LBC-2017)
- Why this method: Harmonic frequency switching with a fixed photonic LO minimises switching overhead to about 2 s, allowing 20 s cycles  
  > "This technique is referred to as harmonic frequency switching and can minimize the overhead to $\sim$2 s." (Harmonic frequency switching)
- Alternative: Retuning the photonic LO each switch rejected because of about 20 s overhead; fixed photonic LO used instead  
  > "essentially makes 20 s switching cycle times with frequency switching impossible." (Harmonic frequency switching)
- Alternative: Optimized frequency scaling ratio not pursued; simple R = nu_HF/nu_LF adopted  
  > "Optimization of the frequency scaling ratio for a given frequency combination must be a future subject for B2B phase referencing." (Strategy of HF-LBC-2017)
- How they decided it was enough: Image coherence of at least 70% (or about 85% under stable conditions) taken as the quality threshold  
  > "should allow all images to achieve $>$85% image coherence." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- Limitation (authors): Several longest-baseline antennas flagged for instrumental instability, so the expected 10 mas resolution for HL Tau was not reached  
  > "Due to instrumental instabilities, a number of flags were applied so that some of the longest baseline antennas were flagged out; thus, we could not achieve the expected $\sim$10 mas angular resolution with the EBs." (Complex structure target I: HL Tau in Band 9–4)
- Limitation (authors): Band 10 experiments failed because sources were too weak  
  > "Both failed after that because the observed sources were too weak to confirm whether the fringes were detected or not." (Strategy of HF-LBC-2017)
- Limitation (authors): Complex-structure imaging lacks short baselines, so extended emission is not recovered  
  > "However, it is apparent for the complex structure sources that the visibility data cannot fully recover the extended structure without short ($u$, $v$) coverage." (Summary)
- Caveat (inferred, ours): Acknowledgments names the project for HL Tau (Band 7) and VY CMa (Band 9) inconsistently with the body text, so data provenance is ambiguous
- Caveat (inferred, ours): HL Tau comparison with LBC-2014-SV mixes unlike on-source times, weightings and self-calibration, so the fidelity claim is qualitative
- Caveat (inferred, ours): Coherence values are peak-flux ratios without uncertainties, and the self-calibration solution intervals are only partly stated
- Caveat (inferred, ours): The 6 deg separation limit rests on one Band 8-4 experiment set, and B2B separation dependence was not systematically tested
- Caveat (inferred, ours): Calibrator counts rely on power-law flux extrapolation and a zenith-pointing assumption
- Caveat (inferred, ours): Manual flagging is not described, so the processed data cannot be reproduced from the text alone

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Exact CASA version and per-EB flagging lists
- Missing: DGC linear-trend removal and time-averaging windows
- Missing: Self-calibration modes and solution intervals for the QSO and HL Tau images
- Missing: Per-SPW frequency-transfer mapping for 90 degree phase switching
- Missing: Scan culling list used to emulate longer switching cycles
- Missing: Calibrator catalogue selection criteria and power-law fit ranges used for counts
- Data volume (inferred): Inferred: tens of execution blocks across Bands 7-9 with 8 s scans, likely tens of GB in total; not stated in the paper
- Score (inferred): 3/5, Methods are described at a feasibility level with clear targets and numbers, but flagging, self-calibration settings, and code/data availability are missing, and key details are deferred to companion papers.
- Rediscovery candidate: no, Data and recipe are only partly specified (manual flagging, DGC trend handling, and self-calibration details missing), and data public status is not stated.

## Links

- Method: (cite: Holdaway2004b) (Cross-band calibration used to define the DGC procedure)
- Method: (cite: Rioja2014) (Frequency phase transfer procedure used to transfer LF phases to HF)
- Method: (cite: Matsushita2017) (WVR phase correction and switching cycle requirements)
- Method: (cite: Maud2017) (WVR phase correction performance reference)
- Method: (cite: Nikolic2009) (ALMA ATM program used for dispersive delay calculation)
- Companion: (cite: Maud2020) (Full study of 50 datasets and longer switching cycle tests, in preparation)
- Companion: (cite: Asaki2019) (Further details of the observations and data analysis of the HF-LBC-2017 experiments)
- Related: ALMA Long Baseline Campaigns LBC-2013, LBC-2014 and LBC-2015
- Related: ALMA online calibrator catalogue

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 72,
  "rate": 0.727
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (schematic, 1 panel(s), schematic): Timeline schematic of a B2B phase referencing observing sequence, showing alternating DGC blocks (low and high frequency DGC source scans), B2B phase referencing blocks (low-frequency phase calibrator and high-frequency target scans), and high-frequency calibration scans over observing time.
  - axes: x: observing time [not labelled]
  - supports step 2
- **Figure 2** (other, 1 panel(s), model): Relative dispersive delay of atmospheric water vapor versus observing frequency at PWV = 1 mm, with ALMA receiver bands marked and the LF and HF spectral ranges of the campaign indicated.
  - axes: x: observing frequency [GHz]; y: relative dispersive delay [%]
  - supports step 5
  - read off the plot: approx. Band 10 delay reaching about 70 % near 950 GHz; approx. Band 9 delay from about -45 % near 600 GHz to about 40 % near 720 GHz; approx. Band 3 delay near 0 % at about 100 GHz
- **Figure 3** (schematic, 1 panel(s), schematic): Logical workflow of the B2B phase referencing and DGC implementation, showing the averaging of DGC phases, LF phase offset corrections, frequency phase transfer to HF, and the final HF target phase correction.
  - axes: x: not applicable [not applicable]
  - supports step 1
- **Figure 4** (other, 3 panel(s), data): Antenna array configurations used in the stage 2 tests for the Band 7-3, Band 8-4 and Band 9-6 experiments, with DGC reference and solution antennas marked.
  - axes: x: East-West position [m]; y: North-South position [m]
  - supports step 1
  - read off the plot: approx. largest baseline extent about 500 m in Band 8-4 layout
- **Figure 5** (other, 3 panel(s), data): Time series of WVR-corrected antenna-based phase of quasar J2253+1608 on antenna DV17 for Band 7 and Band 3, before and after frequency scaling, and after correction with Band 3 phases.
  - axes: y: antenna-based phase [deg]; x: time [UT (hours minutes seconds)]
  - supports step 1
  - validation: Checks that Band 3 phase time series scaled by frequency ratio tracks Band 7 phase, so the corrected residual is near zero.
  - read off the plot: approx. phase range -180 to 180 deg on DV17
- **Figure 6** (other, 16 panel(s), data, model): Left: time series of WVR-corrected antenna-based phases in Band 7 for several DGC quasars on eight antennas; right: antenna-based DGC solutions per SPW and polarization with linear fits.
  - axes: x: time [UT]; y: antenna-based phase [deg]
  - supports step 1
  - validation: Linear fit to DGC phase residuals per antenna checks the stability of the DGC solutions over the observation.
  - read off the plot: approx. DGC solution range -60 to 60 deg on DA41 right panels
- **Figure 7** (other, 16 panel(s), data, model): Stage 2 DGC solutions for Band 8-4 (left) and Band 9-6 (right) antennas versus time, with linear fits to the phase residuals for each antenna.
  - axes: x: time [UT]; y: DGC solution phase [deg]
  - supports step 1
  - validation: Linear fit to the DGC phase solutions checks temporal stability of the DGC in Bands 8 and 9.
  - read off the plot: approx. DGC solution range -60 to 60 deg
- **Figure 8** (scatter_or_relation, 1 panel(s), residual): Residual DGC solutions after subtracting the linear fits for all antennas and SPWs in Band 7-3, plotted against baseline length from the reference antenna DV09.
  - axes: x: baseline length from reference antenna DV09 [m]; y: residual phase offset [deg]
  - supports step 1
  - validation: Checks whether residual DGC phase offsets are small and show no systematic trend with baseline length, supporting DGC stability.
  - read off the plot: approx. residual scatter within about ±30 deg at 200 m baselines
- **Figure 9** (scatter_or_relation, 2 panel(s), residual): Residual DGC solutions after subtracting the linear fits versus baseline length from reference antennas, for Band 8-4 (top) and Band 9-6 (bottom).
  - axes: x: baseline length from reference antenna [m]; y: residual phase offset [deg]
  - supports step 1
  - validation: Checks residual DGC phase offset scatter versus baseline length in Bands 8 and 9, indicating DGC stability.
  - read off the plot: approx. Band 8 residual scatter within about ±90 deg at 500 m baselines
- **Figure 10** (channel_maps, 6 panel(s), data): Synthesized continuum images of J0633-2223 in Band 8 from the comparative B2B versus in-band phase referencing experiment, with B2B images on the left and in-band images on the right for three calibrator separations.
  - axes: x: right ascension offset [arcsec]; y: declination offset [arcsec]; colour: flux density [Jy/beam]; contours: flux density [mJy/beam]
  - supports step 3
  - validation: Compares image coherence and signal-to-noise of B2B and in-band phase referenced images of the same target at different calibrator separations.
  - read off the plot: approx. B2B coherence 83.8 % at 1.2 deg separation; approx. in-band coherence 64.1 % at 9 deg separation; approx. peak flux 0.166 Jy/beam
  - reproduction target
- **Figure 11** (scatter_or_relation, 2 panel(s), data): Peak flux density and peak position offset of J0633-2223 images from the Band 8-4 comparison, as functions of separation angle to the phase calibrator, for in-band, B2B and self-calibrated images.
  - axes: x: separation angle to phase calibrator [deg]; y: peak flux density [mJy/beam]; y: peak position offset [mas]
  - supports step 3
  - validation: Checks how the peak flux and position of the target image depend on calibrator separation for B2B versus in-band referencing.
  - read off the plot: approx. in-band peak flux 115 mJy/beam at 8.7 deg; approx. B2B peak flux 130 to 140 mJy/beam at 1.2 deg; approx. peak position offset 19 mas at 8.7 deg for in-band
- **Figure 12** (other, 1 panel(s), data): Antenna configuration on 2017 November 3 used for the stage 4 imaging test, with 12 m antenna positions plotted.
  - axes: x: East-West position [m]; y: North-South position [m]
  - supports step 4
  - read off the plot: approx. maximum East-West extent about 5000 m; approx. maximum North-South extent about 6000 m
- **Figure 13** (moment_map, 2 panel(s), data): Continuum synthesis images of quasar J2228-0753 in Band 7 and Band 8 calibrated with B2B phase referencing, with contours at multiples of the noise level.
  - axes: x: right ascension J2000 [s]; y: declination J2000 [arcsec]; contours: flux density [mJy/beam]
  - supports step 4
  - read off the plot: approx. Band 7 peak flux 45.32 mJy/beam; approx. Band 8 peak flux 32.35 mJy/beam; approx. Band 7 beam 19 x 16 mas; approx. Band 8 beam 16 x 12 mas
  - reproduction target
- **Figure 14** (moment_map, 6 panel(s), data): Band 9 continuum maps of HL Tau calibrated with B2B phase referencing, with natural, Briggs robust 0.5 and >500 kλ weightings, in full and enlarged views with annotated dark rings.
  - axes: x: right ascension J2000 [s]; y: declination J2000 [arcsec]; colour: flux density [mJy/beam]
  - supports step 4
  - read off the plot: approx. natural-weighted beam 20 x 18 mas; approx. robust 0.5 beam 14 x 11 mas; approx. peak about 20 mJy/beam in natural map
  - reproduction target
- **Figure 15** (moment_map, 4 panel(s), data): Band 9 and Band 7 continuum maps of HL Tau from a single execution block, using natural, Briggs weightings and >500 kλ baseline restriction.
  - axes: x: right ascension J2000 [s]; y: declination J2000 [arcsec]; colour: flux density [mJy/beam]
  - supports step 4
  - validation: Checks whether the HL Tau ring structure is recovered from a single execution block in Band 9 with B2B and in Band 7 without B2B.
  - read off the plot: approx. Band 9 single-EB natural peak about 20 mJy/beam; approx. Band 7 single-EB Briggs 1.0 peak about 6 mJy/beam
- **Figure 16** (moment_map, 3 panel(s), data): Band 9 continuum maps of VY CMa from HF-LBC-2017 without and with self-calibration, and the 2013 SV Band 7 image, showing the VY CMa and C clump structures.
  - axes: x: right ascension J2000 [s]; y: declination J2000 [arcsec]; contours: flux density [mJy/beam]
  - supports step 4
  - read off the plot: approx. HF-LBC-2017 peak 41.5 mJy/beam; approx. self-calibrated peak 135.5 mJy/beam; approx. 2013 SV brightest C clump peak 316.0 mJy/beam
  - reproduction target
- **Figure 17** (channel_maps, 6 panel(s), data): 658 GHz H2O maser cube of VY CMa at six LSRK velocities, with the Band 9 continuum shown as white contours.
  - axes: x: right ascension offset [mas]; y: declination offset [mas]; colour: integrated maser emission [Jy/beam]; contours: continuum flux density [sigma]
  - supports step 4
  - read off the plot: approx. colour scale peak about 35 Jy/beam; approx. channel velocities 5.8, 13.8, 21.8, 29.8, 37.8, 45.8 km/s
  - reproduction target
