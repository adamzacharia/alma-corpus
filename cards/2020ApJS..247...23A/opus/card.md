# ALMA High-frequency Long Baseline Campaign in 2017: Band-to-band Phase Referencing in Submillimeter Waves

`2020ApJS..247...23A` | The Astrophysical Journal Supplement Series 2020 | first author: Asaki, Yoshiharu | arXiv: 2003.07472 | DOI: 10.3847/1538-4365/ab6b20

Card schema 1.0 | model claude-opus-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, protoplanetary_disks, evolved_stars
- Question: Can ALMA image at Bands 7-10 with baselines up to 16 km using band-to-band (B2B) phase referencing with a differential gain calibration (DGC), and does B2B allow closer phase calibrators and better images than in-band phase referencing?  
  > "We aimed to prove that ALMA has observation capabilities in Bands 7, 8, 9, and 10 (285–875 GHz) with up to the longest 16 km baselines using B2B phase referencing." (Introduction); "is B2B phase referencing more beneficial for selecting a phase calibrator than in-band phase referencing?" (Discussions)
- Target **QSO J2228-0753 (stage 4 point-source target)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **QSO J0633-2333 (stage 3 target; J0633-2223 in Table 4)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc" (Complex structure target I: HL Tau in Band 9–4); distance from Rebull2004  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc" (Complex structure target I: HL Tau in Band 9–4)
- Target **VY CMa**: coordinates 07h22m58.3261s, -25d46'03.038" (J2000, measured peak)  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc" (Complex structure target II: VY CMa in Band 9–4); "The peak position of VY CMa was estimated before the self-calibration to be located at ($\alpha$, $\delta$)$=$($7^{\mathrm{h}}22^{\mathrm{m}}58^{\mathrm{s}}.3261$, $-25^{\circ}46'03''.038$) (J2000)." (Complex structure target II: VY CMa in Band 9–4); z/distance 1.17 kpc  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc" (Complex structure target II: VY CMa in Band 9–4); "The peak position of VY CMa was estimated before the self-calibration to be located at ($\alpha$, $\delta$)$=$($7^{\mathrm{h}}22^{\mathrm{m}}58^{\mathrm{s}}.3261$, $-25^{\circ}46'03''.038$) (J2000)." (Complex structure target II: VY CMa in Band 9–4); distance from Zhang2012  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc" (Complex structure target II: VY CMa in Band 9–4); "The peak position of VY CMa was estimated before the self-calibration to be located at ($\alpha$, $\delta$)$=$($7^{\mathrm{h}}22^{\mathrm{m}}58^{\mathrm{s}}.3261$, $-25^{\circ}46'03''.038$) (J2000)." (Complex structure target II: VY CMa in Band 9–4)

## Data provenance

- ALMA projects: 2011.0.00015.SV, 2011.0.00011.SV
- bands: Bands 7, 8, 9 (and 10, failed) for targets; LF calibrator Bands 3, 4, 6, 7 (pairs 7–3, 8–4, 9–4, 9–6, 10–7)  
  > "We investigated image qualities using ALMA receiver Bands 7, 8, 9, and 10 (285–875 GHz) by adopting band-to-band (B2B) phase referencing in which a phase calibrator is tracked at a lower frequency." (abstract); "Various harmonic frequency pairs were tested (Bands 7–3, 8–4, 9–4, 9–6, and 10–7)." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- frequencies and spectral setup: Stage 4 QSO: 289/405 GHz HF with 96/135 GHz LF; HL Tau: 671 GHz with 149 GHz LF, eight 2 GHz SPWs with 90° phase switching; VY CMa: 669/149 GHz, eight 1.875 GHz SPWs, one covering 658 GHz H2O maser at 15.625 kHz  
  > "The high LO1 frequencies are 289 (Band 7) and 405 (Band 8) GHz, while the corresponding low LO1 frequencies are 96 (Band 3) and 135 (Band 4) GHz, respectively." (Point-source target: QSO J2228-0753 in Bands 7–3 and 8–4); "The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 2 GHz each using the $90^{\circ}$ phase switching." (Complex structure target I: HL Tau in Band 9–4); "One of the SPWs covers the 658 GHz H$_{2}$O maser with the frequency resolution of 15.625 kHz." (Complex structure target II: VY CMa in Band 9–4)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array, 40–50 antennas in stage 4  
  > "Array configurations with $B_{\mathrm{max}}\sim 14-16$ km were arranged containing 40–50 12-m antennas." (Point-source target: QSO J2228-0753 in Bands 7–3 and 8–4)
- configurations: _not stated_
- baselines: Stage 2/3: Bmax ~400 m–4 km; stage 4: Bmax ~14–16 km; 2017 Nov 3: 133 m–13.8 km  
  > "From 2017 March to July, we conducted the tests of stages 2 and 3 tests using the mid-baseline lengths ($B_{\mathrm{max}}\sim$400 m–4 km)" (Strategy of HF-LBC-2017); "The longest and shortest baseline lengths are 13.8 km and 133 m, corresponding to angular resolutions of 7 mas and 0.7 arcsec in Band 9, respectively." (Stage 4: high angular resolution imaging test)
- angular resolution: 14 × 11 mas (HL Tau), 10 × 8 mas (VY CMa); 19 × 16 and 16 × 12 mas for QSO in Bands 7 and 8  
  > "The B2B phase referencing was successfully applied, allowing us to achieve an angular resolution of $14 \times 11$ and $10 \times 8$ mas for HL Tau and VY CMa, respectively." (abstract); "The achieved beam sizes are $19 \times 16$ and $16 \times 12$ mas in Bands 7 and 8, respectively." (Point-source target: QSO J2228-0753 in Bands 7–3 and 8–4)
- max recoverable scale: structures larger than 0.2 arcsec not properly sampled in stage 4  
  > "there were only a few baselines shorter than 200 m during the stage-4 period and thus we could not properly sample structures larger than 0.2 arcsec." (Stage 4: high angular resolution imaging test)
- sensitivity: VY CMa continuum RMS 1.5 mJy beam^-1 (robust 2); 1.8 mJy beam^-1 (robust 0)  
  > "The synthesized beam size is $12 \times 11$ mas, and the image RMS noise is 1.5 mJy beam$^{-1}$." (Complex structure target II: VY CMa in Band 9–4)
- time on source: HL Tau 45 min (two EBs); VY CMa 344 s  
  > "Combined, there is 45 minutes on-source time for HL Tau." (Complex structure target I: HL Tau in Band 9–4); "The total observing time was 47 minutes, and the on-source time for VY CMa was 344 s." (Complex structure target II: VY CMa in Band 9–4)
- observing dates: 2017 March–November; stage 2 Apr 11, Apr 23, May 4; stage 3 Jul 18; stage 4 Oct–Nov 3 2017  
  > "The baselines were longer than 10 km from the middle of July to the end of November, during which time more stage 3 tests and the stage 4 tests were undertaken." (Strategy of HF-LBC-2017); "Two B2B phase referencing EBs were taken on 2017 November 3 with switching cycle times of 37 and 26 s, respectively." (Complex structure target I: HL Tau in Band 9–4)
- pi or archival as stated: Campaign test data (EBs listed in Tables 3–5) plus archival SV data 2011.0.00015.SV and 2011.0.00011.SV  
  > "For this research, we used the ALMA data listed in" (Acknowledgments)
- Line: H2O v2=1, 1_{1,0}-1_{0,1} (maser) (658.00655 GHz)
- Other facility **ALMA calibrator source catalog**: Flux densities of 3316 QSOs used for phase calibrator source counts  
  > "In the catalogue, 3316 QSOs whose flux densities have been measured with ALMA are available." (Discussions)
- External data: LBC-2014-SV Band 7 HL Tau peak 11.56 mJy beam^-1 used to predict Band 9 peak  
  > "scaling from the LBC-2014-SV Band 7 data (11.56 mJy beam$^{-1}$," (Complex structure target I: HL Tau in Band 9–4) [from (cite: ALMApartnership2015b)]
- External data: HL Tau disk features D1, B1, D2, B2, B6  
  > "The features are coincident with D1 and B1, dark and bright features reported by" (Complex structure target I: HL Tau in Band 9–4) [from (cite: ALMApartnership2015b)]
- External data: VY CMa stellar contribution 111–124 mJy at ~658 GHz  
  > "estimated a stellar contribution of 111–124 mJy at around 658 GHz based on the analytical stellar properties." (Complex structure target II: VY CMa in Band 9–4) [from (cite: OGorman2015)]
- External data: VY CMa photosphere diameter 11.4 mas  
  > "It is expected that the unresolved point source in HF-LBC-2017 represents the RSG photosphere with the diameter of 11.4 mas" (Complex structure target II: VY CMa in Band 9–4) [from (cite: Wittkowski2012)]
- External data: LBC-2013-SV VY CMa continuum image/maser comparison  
  > "we cannot identify which maser emissions correspond to those observed by" (Complex structure target II: VY CMa in Band 9–4) [from (cite: Richards2014)]
- External data: Distances: HL Tau 140 pc, VY CMa 1.17 kpc  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc" (Complex structure target I: HL Tau in Band 9–4) [from (cite: Rebull2004); (cite: Zhang2012)]
- External data: Turbulent layer height 500 m and velocity 6 m s^-1  
  > "Assuming an atmospheric turbulent layer height of 500 m and its velocity of 6 m s$^{-1}$ at the ALMA site" (B2B phase referencing) [from (cite: Robson2001)]
- Simulation/model as data: ALMA ATM program used to compute relative dispersive delay of water vapor (PWV = 1 mm)  
  > "calculated with the ALMA ATM program" (B2B phase referencing)

## Processing

### Calibration

- pipeline or manual: Manual CASA reduction with custom DGC/B2B workflow; in-band data with standard ALMA procedure; manual flagging  
  > "The data reduction of the in-band phase referencing was undertaken with a standard ALMA data reduction procedure, while the B2B phase referencing data reduction procedure requires the application of the DGC solutions." (Stage 3: image quality comparative test between B2B and in-band phase referencing); "there were a number of manual flagging commands to be entered for these data, mostly for the frequency switching segments" (Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: DGC source used as HF flux calibrator (stage 3); J0522-3627 for VY CMa bandpass and flux  
  > "For the amplitude calibration, we used the DGC source as an HF flux calibrator in addition to the system noise temperature calibration in both the B2B and in-band phase referencing." (Stage 3: image quality comparative test between B2B and in-band phase referencing); "A bright QSO, J0522$-$3627, $28^{\circ}$ away from the target, was used as the DGC source, as well as for bandpass and flux-scale calibration." (Complex structure target II: VY CMa in Band 9–4)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal for coherence checks (solint ~1 s stage 3; target scan length stage 4 QSO); VY CMa phase+amp self-cal solint 16 s on continuum then 4 s on maser; none for HL Tau  
  > "with a short solution interval (here we could use a solution interval of $\sim 1$ s as the S/N was high)" (Stage 3: image quality comparative test between B2B and in-band phase referencing); "phase and amplitude self-calibrations were performed for the line-free continuum channels with the solution interval of 16 s to remove residual phase offsets between the SPWs." (Complex structure target II: VY CMa in Band 9–4); "We have not, however, performed any form of self-calibration" (Complex structure target I: HL Tau in Band 9–4)

### Imaging

- task: CASA CLEAN; fixed 50 iterations in stage 3  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target (located at the phase tracking center in the image)." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (stage 3, QSO, HL Tau, maser); natural for HL Tau; robust 2 and 0 for VY CMa continuum; robust -1 for LBC-2014-SV comparison  
  > "For the imaging, we use a Briggs weighting with a robustness parameter (robust) of 0.5, as this is representative of the common robust generally used in ALMA images." (Stage 3: image quality comparative test between B2B and in-band phase referencing); "The line-free continuum emission image using the averaged eight SPWs with Briggs weighting (robust $= 2$) is shown in the left panel of" (Complex structure target II: VY CMa in Band 9–4)
- uv taper: _not stated_
- cell size: 5 (Bands 7, 8) or 7 (Band 9) pixels across beam major axis  
  > "The cell size is chosen such that 5 (for Bands 7 and 8) or 7 (Band 9) pixels cover the synthesized beam major axis." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- image size: _not stated_
- masking: 15 pixel radius box around target (stage 3); HL Tau also reimaged excluding baselines <500 kλ  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target (located at the phase tracking center in the image)." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: line-free continuum channels of eight SPWs (VY CMa); specific channels not given  
  > "The line-free continuum emission image using the averaged eight SPWs" (Complex structure target II: VY CMa in Band 9–4)
- primary beam correction: _not stated_
- array combination: Two EBs combined (QSO Bands 7/8; HL Tau)  
  > "when combining two EBs taken in the middle of October and the beginning of 2017 November." (Point-source target: QSO J2228-0753 in Bands 7–3 and 8–4)
- smoothing: H2O maser cube: 18 channels averaged to 8 km s^-1  
  > "A bright submm H$_{2}$O maser cube with a velocity resolution of 8 km s$^{-1}$ was generated for the 18 averaged frequency channels" (Complex structure target II: VY CMa in Band 9–4)
- final beam: HL Tau 20×18 mas (natural), 14×11 mas (robust 0.5); VY CMa 12×11 mas (robust 2), 10×8 mas (maser, robust 0.5)  
  > "The final beams achieved were 20$\times$18 and 14$\times$11 mas, respectively." (Complex structure target I: HL Tau in Band 9–4)
- final rms: VY CMa 1.5 mJy beam^-1 (robust 2); 1.8 mJy beam^-1 (robust 0)  
  > "The continuum emission map has a synthesized beam of $10 \times 8$ mas and the image RMS noise of 1.8 mJy beam$^{-1}$." (Complex structure target II: VY CMa in Band 9–4)

### Inherited from earlier work

- WVR phase correction and its performance  
  > "The WVR phase correction and its performance are described in previous reports" (Basic concept of B2B phase referencing) [from (cite: Matsushita2017; Maud2017)]
- Details of stage 4 QSO observations and analysis  
  > "Further details of the observations and data analysis results are described in another paper" (Point-source target: QSO J2228-0753 in Bands 7–3 and 8–4) [from (cite: Asaki2019)]
- Full stage 3 study of 50 datasets and switching cycle culling  
  > "The full study of 50 datasets will be detailed in the forthcoming paper" (Stage 3: image quality comparative test between B2B and in-band phase referencing) [from (cite: Maud2020)]
- Cross-band calibration concept for instrumental phase offset (DGC)  
  > "The instrumental phase offset difference can be independently measured with a cross-band calibration" (DGC) [from (cite: Holdaway2004b)]
- Coherence factor exp(-σφ²/2) relating image coherence to RMS phase  
  > "where $\sigma_{\phi}$ is the residual RMS phase noise in radians" (Stage 3: image quality comparative test between B2B and in-band phase referencing) [from (cite: TMS2001)]

### Not stated but needed to reproduce (our reading)

- CASA version and exact tasks used for the DGC workflow (gaincal/applycal parameters, combine settings, interpolation)
- Reference antenna choices and flagging commands for each EB
- Image size, deconvolver and number of CLEAN iterations for stage 4 images
- Clean thresholds/iterations and masks for HL Tau and VY CMa images
- Exact frequency scaling ratio applied (LO1 ratio vs. actual SPW frequency ratio)
- Which LBC-2014-SV EB was used for the single-EB comparison and its uv-range limit
- Line-free channel ranges for VY CMa
- Details of the calibrator count procedure: sky area, catalog snapshot date, how mean separation is computed from solid angle

## Analysis recipe

1. **apply WVR and Tsys corrections**: WVR phase correction and system noise temperature correction applied to all data before DGC workflow  
  > "The WVR phase correction and the system noise temperature correction have been applied to all of the data before this workflow starts." (Implementation of B2B phase referencing and DGC)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **derive DGC solution and apply B2B phase referencing**: Time-average LF DGC phases, frequency-transfer short-term LF solutions to HF DGC scans, average to obtain HF phase offset, then apply offset plus scaled LF calibrator phases to target  
  > "Finally, the HF phase offset correction $\left <\bar \Phi^{\mathrm{DGC}}_{\mathrm{HF}} \right >$ is applied to the target phase $\Phi^{\mathrm{T}}_{\mathrm{HF}}$, along with the time-dependent phase solutions derived from the LF phase calibrator, $\Delta\Phi^{\mathrm{C}}_{\mathrm{LF}}$ (panel (f))." (Implementation of B2B phase referencing and DGC)
   - software: CASA
   - parameter: switching cycle ~20 s with 8 s scans; 20–82 s overall  
  > "We adopted a consistent switching cycle time of $\sim$20 s, typically consisting of 8 s target and phase calibrator scans and two 2 s overheads to switch sources and/or frequencies." (Results)
   - parameter: harmonic frequency switching with fixed photonic LO  
  > "In HF-LBC-2017, we adopted harmonic frequency switching for all of the B2B phase referencing experiments." (Harmonic frequency switching)
   - assumption: Phase error proportional to frequency; simple scaling ratio R = νHF/νLF despite dispersive term  
  > "we adopted the simple frequency scaling ratio for B2B phase referencing because other comparable delay errors, such as the antenna position errors, do not have a frequency dependence." (Strategy of HF-LBC-2017)
   - fitting: _not stated_
   - validation: _not stated_
3. **test DGC solution stability (stage 2)**: Observe several bright QSOs in succession up to 100° apart; compute antenna-based DGC solutions per SPW/polarization, subtract linear trend, examine scatter vs baseline length  
  > "one set targeting several bright QSOs as DGC sources in succession with the sky separations of up to 100$^{\circ}$ to check the dependence of the DGC solutions with the sky position" (Stage 2: DGC solution stability)
   - software: CASA
   - assumption: v_w = 6 m s^-1  
  > "If we assume $v_{\mathrm{w}}=6$ m s$^{-1}$, this baseline length is expected to 60 m." (Stage 2: DGC solution stability)
   - fitting: single linear trend subtracted per antenna  
  > "shows the antenna-based DGC solutions as a function of baseline length to the reference antenna after subtracting a single linear trend for each antenna." (Stage 2: DGC solution stability)
   - validation: _not stated_
4. **compare B2B vs in-band image quality (stage 3)**: Interleaved DGC/in-band/B2B blocks on same target with calibrators at 1.2°–8.7°; image, then phase self-calibrate to define image coherence as ratio of peak fluxes  
  > "Here we define the image coherence as the ratio between peak flux densities for data with and without self-calibration applied." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - software: CASA
   - parameter: robust 0.5, 50 CLEAN iterations, 15 pixel mask; switching cycle 60 s by culling  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target (located at the phase tracking center in the image)." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - assumption: Residual phase noise Gaussian, coherence = exp(-σφ²/2)  
  > "Assuming that the residual RMS phase noise in the visibility has characteristics of a Gaussian random noise" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
   - fitting: _not stated_
   - validation: Self-calibrated images as reference  
  > "After self-calibration, the image noise of the B2B and in-band phase referencing are equivalent, indeed confirming that the residual offsets have been fully corrected." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
5. **long-baseline QSO imaging in Bands 7 and 8**: B2B referencing with 0.7° calibrator, two EBs combined, robust 0.5 imaging, self-cal for coherence  
  > "We also performed phase self-calibration with a solution interval of the target scan length and obtained the images free from the atmospheric and instrumental phase errors in order to investigate the image coherence." (Point-source target: QSO J2228-0753 in Bands 7–3 and 8–4)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **HL Tau Band 9 imaging and fidelity comparison**: Image combined EBs with natural and robust 0.5, and with uv>500 kλ; compare with LBC-2014-SV Band 7 single-EB image (robust -1, and uv-limited robust 0.5); estimate coherence from expected peak  
  > "To provide a fairer comparison of the image structure, we use only one Band 9 HF-LBC-2017 EB compared with a Band 7 image with a single LBC-2014-SV EB." (Complex structure target I: HL Tau in Band 9–4)
   - software: CASA
   - assumption: Central peak optically thick, α = 2  
  > "Using the simple assumption that the central peak of emission is completely optically thick ($\alpha$=2)" (Complex structure target I: HL Tau in Band 9–4)
   - fitting: _not stated_
   - validation: RMS phase of bandpass calibrator over 30 s  
  > "Using the high-S/N bandpass calibrator observation, we performed an assessment of the Band 9 RMS phase with a time interval of 30 s" (Complex structure target I: HL Tau in Band 9–4)
7. **VY CMa continuum and maser imaging**: Continuum image (robust 2), self-cal on continuum (16 s) then maser (4 s), aperture flux vs LBC-2013-SV Gaussian fit, peak position, maser cube (robust 0.5)  
  > "the bright maser peak, which has a higher S/N, was used for further self-calibration, now making and applying the solutions with an interval of 4 s to all data." (Complex structure target II: VY CMa in Band 9–4)
   - software: CASA
   - fitting: Two-dimensional Gaussian fit to LBC-2013-SV image; similar-sized aperture on new image  
  > "Fitting to a similar sized-aperture for VY CMa in our image gives 394 mJy at the reference frequency of 669 GHz." (Complex structure target II: VY CMa in Band 9–4)
   - validation: Consistency with LBC-2013-SV flux within ~20%  
  > "These results are consistent within the $\sim 20$% error for the LBC-2013-SV fluxes." (Complex structure target II: VY CMa in Band 9–4)
8. **phase calibrator availability statistics**: Power-law fit of catalog fluxes, count sources above required flux (S/N 20×R per 8 s scan, SEFDs, 43 antennas), derive mean solid angle and mean separation per band  
  > "First, we count only the sources whose flux density is higher than the flux density requirement. Second, we obtain a mean solid angle per phase calibrator from the above number count." (Discussions); "flux density at an arbitrary frequency is evaluated by fitting the flux density measurements between Bands 3 and 7 or Bands 3 and 6 to a power-law function of $\nu^{\alpha}$, where $\alpha$ is a spectral index." (Discussions)
   - parameter: Required S/N per scan 20 × R; 8 s scan; 43 antennas  
  > "Required S/N (per scan)" (Table 5)
   - parameter: Declination limited below +25°  
  > "We constrain the decl. range lower than $+25^{\circ}$." (Discussions)
   - assumption: Antennas at zenith; highest catalog flux used for multi-epoch sources  
  > "The antennas are assumed to be directed to zenith." (Discussions); "If a certain calibrator has been observed at multiple epochs, we refer to the highest value" (Discussions)
   - fitting: power-law ν^α fit  
  > "flux density at an arbitrary frequency is evaluated by fitting the flux density measurements between Bands 3 and 7 or Bands 3 and 6 to a power-law function of , where  is a spectral index." (Discussions)
   - validation: Checked calibrator distribution bias  
  > "We conclude that the current investigation is not seriously affected by the calibrator distribution bias." (Discussions)

## Software

- **CASA** : data reduction and imaging  
  > "For many parts of our data reduction, we made use of the Common Astronomy Software Applications (CASA) package" (Results)
- **AATM (ALMA ATM program)** : computing dispersive delay of atmospheric water vapor  
  > "calculated with the ALMA ATM program" (B2B phase referencing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DGC solution standard deviation, Band 7 | 10–20 | not stated | deg | 3 | The DGC solution in Band 7 has a roughly a standard deviation of $10^{\circ}$–$20^{\circ}$, independent of the sky positions of the QSOs. |
| DGC solution standard deviation, Bands 8–4 and 9–6 | ~30 | not stated | deg | 3 | the standard deviation of the DGC solution is increased to $\sim$30$^{\circ}$. |
| DGC instrumental offset stability time | approximately 1 | not stated | hr | 3 | the instrumental phase offset difference determined from the DGC solution is stable for approximately 1 hr. |
| Band 8 in-band image coherence at 5.8° and 8.7° separation | 71 and 64 | not stated | % | 4 | Relative to the self-calibrated image, the image coherence is 71% and 64% for the $5.^{\circ}8$ and $8.^{\circ}7$ separation angles. |
| Max calibrator separation for ≥70% coherence | ~6 | not stated | deg | 4 | If we wish to obtain an image coherence of $\geq$70%, the separation angle should be within $\sim 6^{\circ}$. |
| QSO J2228-0753 image coherence, Bands 7 and 8 | 94 and 84 | not stated | % | 5 | We obtained high image coherences of 94% and 84% in Bands 7 and 8, respectively, so that B2B phase referencing works effectively in those experiments. |
| Implied RMS phase noise, Band 7 / Band 8 | 21 / 34 | not stated | deg | 5 | The 94% image coherence in Band 7 corresponds to an RMS phase noise of $21^{\circ}$, |
| QSO beam sizes Band 7 / Band 8 | 19 × 16 / 16 × 12 | not stated | mas | 5 | The achieved beam sizes are $19 \times 16$ and $16 \times 12$ mas in Bands 7 and 8, respectively. |
| HL Tau Band 9 natural-weighted peak | 24.9 | not stated | mJy beam^-1 | 6 | The naturally weighted HF-LBC-2017 Band 9 image yields a peak of 24.9 mJy beam$^{-1}$, suggesting a coherence of around 56%. |
| HL Tau inferred coherence | ~56 | lower limit | % | 6 | The naturally weighted HF-LBC-2017 Band 9 image yields a peak of 24.9 mJy beam$^{-1}$, suggesting a coherence of around 56%. |
| HL Tau beams (natural / robust 0.5) | 20×18 / 14×11 | not stated | mas | 6 | The final beams achieved were 20$\times$18 and 14$\times$11 mas, respectively. |
| VY CMa continuum peak before/after self-cal | 42 / 135 | not stated | mJy beam^-1 | 7 | Improvements were seen on the continuum peak, which increased from 42 to 135 mJy beam$^{-1}$, while the image RMS noise was largely unchanged at 1.5 mJy beam$^{-1}$. |
| VY CMa aperture flux density at 669 GHz | 394 | not stated | mJy | 7 | Fitting to a similar sized-aperture for VY CMa in our image gives 394 mJy at the reference frequency of 669 GHz. |
| VY CMa position offset from LBC-2013-SV | (47, 5) | LBC-2013-SV positional uncertainty 35 mas | mas | 7 | The position is offset by (47, 5) mas from the position measured from the most astrometrically accurate LBC-2013-SV observations at 321 GHz in Band 7 (resolution of 180$\times$90 mas). |
| Mean separation to B2B calibrator, Band 10 with Band 3 / Band 7 | 4.3 / 5.4 | not stated | deg | 8 | By introducing B2B phase referencing, one is expected to find a suitable phase calibrator within $4.^{\circ}3$ in Band 3.; There is a high probability of finding a low-frequency calibrator within $5^{\circ}.4$ in B2B phase referencing, bright enough to use an 8 s scan length combined with a 7.5 GHz bandwidth. |
| Mean separation to in-band calibrator, Band 10 | 12.6 | not stated | deg | 8 | Band 10 is the most difficult Band in searching for an in-band phase calibrator, whose expected mean separation angle is $12.^{\circ}6$. |

## Qualitative findings

- DGC solutions independent of sky position over 100° and free of rapid instrumental variations, excluding problematic antennas  
  > "As a whole, the DGC solutions are stable for QSOs with positions separated by 100$^{\circ}$ apart on the sky." (Stage 2: DGC solution stability)
- B2B and in-band give comparable coherence with the same close calibrator; in-band degrades with separation  
  > "we found that in-band phase referencing has a noticeable degradation of image quality in terms of the image coherence and defects with increasing separation angle." (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- HL Tau Band 9 image recovers D1/B1 features and is arguably as good as Band 7 SV in fair comparison; extended structure poorly recovered due to uv sampling  
  > "Aside from the unfortunate ($u$, $v$) sampling, based upon these fairer comparisons, our Band 9 image of HL Tau is arguably as good as that in Band 7." (Complex structure target I: HL Tau in Band 9–4)
- B2B more beneficial than in-band for calibrator availability in Bands 8–10, no merit in Band 7  
  > "Our statistical investigation for the phase calibrator availability shows that B2B phase referencing is more beneficial for finding a phase calibrator in Bands 8–10 while there is no apparent merit in Band 7." (Summary)

## Claim tuples

- H: Instrumental phase offset between bands can be removed stably with DGC | E: Stage 2 multi-QSO DGC blocks in Bands 7–3, 8–4, 9–6 | R: DGC scatter 10–20° (Band 7), ~30° (Bands 8, 9), independent of sky position; stable ~1 hr | F: DGC is satisfactorily stable | **supported**
- H: B2B with a close calibrator outperforms in-band with distant calibrators | E: Stage 3 Band 8–4 comparisons with calibrators at 1.2°–8.7° | R: Comparable coherence for same calibrator; in-band coherence 71%/64% at 5.8°/8.7° | F: Calibrator within ~6° needed for ≥70% coherence; closer calibrator via B2B improves images in Bands 8–10 | **supported**
- H: B2B enables long-baseline high-frequency imaging | E: Stage 4 imaging of QSO (Bands 7, 8), HL Tau and VY CMa (Band 9) on 14–16 km baselines | R: QSO coherence 94%/84%; HL Tau 14×11 mas, VY CMa 10×8 mas beams | F: Objects imaged at highest resolutions with expected fidelity, but extended structure not recovered without short spacings | **supported**
- H: B2B gives better calibrator availability despite needing higher S/N | E: Source counts from ALMA calibrator catalog with flux requirements | R: B2B mean separation 3.1–5.4°; in-band 3.7–12.6° | F: B2B beneficial in Bands 8–10, not in Band 7 | **supported**

## Reasoning

- Why this data: HL Tau and VY CMa chosen because high-fidelity earlier SV images exist for comparison  
  > "to examine whether the image quality of B2B phase referencing is as expected in Band 9 when compared with the known high-fidelity image from previous ALMA SV data." (Complex structure target I: HL Tau in Band 9–4)
- Why this method: Frequencies chosen for harmonic switching availability and small dispersive term  
  > "In selecting the observing frequencies, we prioritized the following two points: (1) the harmonic frequency switching is available for a combination of HF and LF to achieve the fast switching" (Strategy of HF-LBC-2017)
- Alternative: Smaller robust values rejected for HL Tau because they resolve out extended emission  
  > "as Briggs weightings with smaller robustness parameters form too-sharp beams resolving out almost all of the extended emission." (Complex structure target I: HL Tau in Band 9–4)
- Alternative: Band 10 experiments failed and excluded  
  > "In this paper, the Band 10 results are not mentioned further." (Strategy of HF-LBC-2017)
- How they decided it was enough: _not stated_
- Limitation (authors): Flagged longest-baseline antennas prevented expected ~10 mas resolution for HL Tau  
  > "we could not achieve the expected $\sim$10 mas angular resolution with the EBs." (Complex structure target I: HL Tau in Band 9–4)
- Limitation (authors): Dispersive water vapor term not fully investigated; simple scaling ratio used  
  > "Another important subject not fully investigated for HFs is where the dispersive term of the atmospheric water vapor is greater than a few tens of percent." (Summary)
- Limitation (authors): B2B not systematically tested at various separation angles  
  > "Although we have not systematically tested the B2B phase referencing image quality for a variety of separation angles" (Stage 3: image quality comparative test between B2B and in-band phase referencing)
- Limitation (authors): Observations in non-optimal atmospheric conditions; high Band 9 RMS phase  
  > "the observations were performed during available time and thus not during the most optimal conditions." (Complex structure target II: VY CMa in Band 9–4)
- Limitation (authors): VY CMa positional offset not yet understood  
  > "We are still investigating this positional offset" (Complex structure target II: VY CMa in Band 9–4)
- Caveat (inferred, ours): Stage 3 conclusions rest on a single detailed Band 8–4 night; broader statistics deferred to Maud2020
- Caveat (inferred, ours): Image coherence via self-cal peak ratio with 50 fixed CLEAN iterations may depend on cleaning depth
- Caveat (inferred, ours): HL Tau coherence relies on optically thick α=2 extrapolation from Band 7
- Caveat (inferred, ours): Calibrator counts use the highest catalog flux per source, which may overestimate availability given QSO variability
- Caveat (inferred, ours): Target name inconsistency (J0633-2333 in text vs J0633-2223 in Table 4)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: EB uids for test data listed in Tables 3–5; SV projects 2011.0.00015.SV and 2011.0.00011.SV  
  > "For this research, we used the ALMA data listed in" (Acknowledgments)
- Missing: CASA version and scripts implementing the DGC/B2B workflow
- Missing: Flagging commands for frequency-switching segments
- Missing: Imaging parameters (niter, thresholds, image size) for stage 4 images
- Missing: Snapshot of the ALMA calibrator catalog used and exact source-count computation
- Missing: Explicit statement whether HF-LBC-2017 EBs are publicly available in the archive
- Data volume (inferred): Tens of EBs (stage 2/3 short tests plus ~7 stage 4 long-baseline EBs with 40–50 antennas, 8 SPWs at Band 9), likely a few hundred GB to ~1 TB raw
- Score (inferred): 3/5, On a 1–5 scale: workflow and key imaging parameters are described and EB uids given, but no software versions, scripts or flag lists, and the custom DGC workflow requires substantial reimplementation.
- Rediscovery candidate: no, Public availability of the HF-LBC-2017 test EBs is not stated and the custom B2B/DGC calibration plus manual flagging are not specified in enough detail to redo directly.

## Links

- Method: (cite: Holdaway2004b) (cross-band calibration and phase structure function concepts)
- Method: (cite: Rioja2014) (frequency phase transfer)
- Method: (cite: Schwab1980) (self-calibration)
- Method: (cite: TMS2001) (coherence factor, SEFD, 90° phase switching)
- Method: (cite: Nikolic2009) (ALMA ATM atmospheric model)
- Method: (cite: Matsushita2017; Maud2017) (WVR phase correction)
- Companion: (cite: Asaki2019) (details of stage 4 QSO observations)
- Companion: (cite: Maud2020) (full stage 3 study of 50 datasets)
- Companion: (cite: ALMApartnership2015b) (LBC-2014-SV HL Tau comparison image)
- Companion: (cite: Richards2014) (LBC-2013-SV VY CMa comparison)
- Related: HF-LBC-2017
- Related: LBC-2013
- Related: LBC-2014
- Related: LBC-2015
- Related: ALMA calibrator source catalog

## Checks

```json
{
 "quotes": 127,
 "quotes_ok": 126,
 "quote_pass_rate": 0.992,
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
  "facts": 113,
  "stated": 83,
  "rate": 0.735
 },
 "evidence_ok": false
}
```
