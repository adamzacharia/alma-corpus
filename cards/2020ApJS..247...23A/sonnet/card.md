# ALMA High-frequency Long Baseline Campaign in 2017: Band-to-band Phase Referencing in Submillimeter Waves

`2020ApJS..247...23A` | The Astrophysical Journal Supplement Series 2020 | first author: Asaki, Yoshiharu | arXiv: 2003.07472 | DOI: 10.3847/1538-4365/ab6b20

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, protoplanetary_disks, evolved_stars
- Question: Can band-to-band (B2B) phase referencing, with a phase calibrator tracked at lower frequency, deliver long-baseline (up to 16 km) imaging in ALMA Bands 7-9, and does it allow closer phase calibrators than in-band phase referencing?  
  > "We investigated image qualities using ALMA receiver Bands 7, 8, 9, and 10 (285–875 GHz) by adopting band-to-band (B2B) phase referencing in which a phase calibrator is tracked at a lower frequency." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc" (4.3.2 Complex structure target I: HL Tau in Band 9–4); distance from Rebull2004  
  > "HL Tau is a protoplanetary disk system surrounding a young star at a distance of 140 pc" (4.3.2 Complex structure target I: HL Tau in Band 9–4)
- Target **VY CMa**: coordinates 7h22m58.3261s, -25d46m03.038s (J2000, measured peak before self-cal)  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc" (4.3.3 Complex structure target II: VY CMa in Band 9–4); "($\alpha$, $\delta$)$=$($7^{\mathrm{h}}22^{\mathrm{m}}58^{\mathrm{s}}.3261$, $-25^{\circ}46'03''.038$) (J2000)" (4.3.3 Complex structure target II: VY CMa in Band 9–4); z/distance 1.17 kpc  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc" (4.3.3 Complex structure target II: VY CMa in Band 9–4); "($\alpha$, $\delta$)$=$($7^{\mathrm{h}}22^{\mathrm{m}}58^{\mathrm{s}}.3261$, $-25^{\circ}46'03''.038$) (J2000)" (4.3.3 Complex structure target II: VY CMa in Band 9–4); distance from Zhang2012  
  > "Our second high-resolution imaging experiment targeted VY CMa, located at a distance of 1.17 kpc" (4.3.3 Complex structure target II: VY CMa in Band 9–4); "($\alpha$, $\delta$)$=$($7^{\mathrm{h}}22^{\mathrm{m}}58^{\mathrm{s}}.3261$, $-25^{\circ}46'03''.038$) (J2000)" (4.3.3 Complex structure target II: VY CMa in Band 9–4)
- Target **QSO J2228-0753**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **QSO J0633-2333 (Stage 3 target)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV, 2011.0.00011.SV
- bands: Bands 7, 8, 9 (Band 10 attempts failed); LF Bands 3, 4, 6  
  > "at 289 GHz in Band 7 and 405 GHz in Band 8 and complex structure sources of HL Tau and VY CMa at $\sim$670 GHz in Band 9" (abstract)
- frequencies and spectral setup: HL Tau: eight 2 GHz SPWs, LO1 671 GHz (Band 9) and 149 GHz (Band 4), 90 deg phase switching  
  > "The correlator was configured to have eight SPWs in Band 9 with a bandwidth of 2 GHz each using the $90^{\circ}$ phase switching." (4.3.2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 16 km (stage 4 Bmax ~14-16 km)  
  > "using the long baselines ($B_{\mathrm{max}}\sim$14–16 km)" (3 Strategy)
- angular resolution: 14x11 mas (HL Tau), 10x8 mas (VY CMa)  
  > "allowing us to achieve an angular resolution of $14 \times 11$ and $10 \times 8$ mas for HL Tau and VY CMa, respectively" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: HL Tau 45 min combined; VY CMa 344 s  
  > "Combined, there is 45 minutes on-source time for HL Tau." (4.3.2); "the on-source time for VY CMa was 344 s" (4.3.3)
- observing dates: Stage 4 HL Tau/VY CMa on 2017 Nov 3; QSO tests Oct-Nov 2017  
  > "On 2017 November 3,VY CMa was observed in Band 9 with a switching cycle time of 82 s." (4.3.3)
- pi or archival as stated: _not stated_
- Line: H2O maser v2=1, 1(1,0)-1(0,1) (658.00655 GHz)
- Other facility **ALMA calibrator source catalog**: flux densities of 3316 QSOs for phase calibrator availability statistics  
  > "In the catalogue, 3316 QSOs whose flux densities have been measured with ALMA are available." (5 Discussions)
- External data: HL Tau Band 7 SV peak 11.56 mJy/beam used to scale expected Band 9 peak  
  > "scaling from the LBC-2014-SV Band 7 data (11.56 mJy beam$^{-1}$," (4.3.2) [from ALMApartnership2015b]
- External data: VY CMa stellar contribution 111–124 mJy near 658 GHz  
  > "estimated a stellar contribution of 111–124 mJy at around 658 GHz based on the analytical stellar properties." (4.3.3) [from OGorman2015]
- External data: RSG photosphere diameter 11.4 mas  
  > "the RSG photosphere with the diameter of 11.4 mas" (4.3.3) [from Wittkowski2012]

## Processing

### Calibration

- pipeline or manual: Manual CASA-based reduction with DGC solutions for B2B; standard ALMA procedure for in-band; manual flagging of frequency switching segments  
  > "Throughout almost all of the tests, there were a number of manual flagging commands to be entered for these data, mostly for the frequency switching segments" (4 Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: DGC source used as HF flux calibrator (Stage 3); J0522-3627 for VY CMa  
  > "For the amplitude calibration, we used the DGC source as an HF flux calibrator in addition to the system noise temperature calibration" (4.2)
- flux scale uncertainty: _not stated_
- self calibration: Stage 3 solint ~1 s; QSO solint = target scan length; VY CMa phase+amp 16 s then maser 4 s  
  > "phase and amplitude self-calibrations were performed for the line-free continuum channels with the solution interval of 16 s" (4.3.3)

### Imaging

- task: _not stated_
- deconvolver: CLEAN, 50 iterations with 15 pixel radius mask box (Stage 3)  
  > "A fixed number of 50 CLEAN iterations were made with a 15 pixel radius masking box around the target" (4.2)
- weighting robust: Briggs robust 0.5 (Stage 3, QSOs, HL Tau); natural for HL Tau; robust 2 VY CMa continuum; robust 0.5 maser cube; robust 0 continuum overlay  
  > "we use a Briggs weighting with a robustness parameter (robust) of 0.5" (4.2)
- uv taper: _not stated_
- cell size: 5 (Bands 7, 8) or 7 (Band 9) pixels per synthesized beam major axis  
  > "The cell size is chosen such that 5 (for Bands 7 and 8) or 7 (Band 9) pixels cover the synthesized beam major axis." (4.2)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 19x16 mas (B7), 16x12 mas (B8); HL Tau 20x18 and 14x11 mas; VY CMa continuum 12x11 mas  
  > "The achieved beam sizes are $19 \times 16$ and $16 \times 12$ mas in Bands 7 and 8, respectively." (4.3.1)
- final rms: VY CMa continuum 1.5 mJy/beam; 1.8 mJy/beam for robust 0 continuum  
  > "The synthesized beam size is $12 \times 11$ mas, and the image RMS noise is 1.5 mJy beam$^{-1}$." (4.3.3)

### Inherited from earlier work

- Details of QSO Band 7/8 observations and analysis  
  > "Further details of the observations and data analysis results are described in another paper" (4.3.1) [from (cite: Asaki2019)]
- Full study of 50 Stage 3 datasets incl. culling for longer cycle times  
  > "The full study of 50 datasets will be detailed in the forthcoming paper" (4.2) [from (cite: Maud2020)]
- Cross-band calibration concept (DGC)  
  > "The instrumental phase offset difference can be independently measured with a cross-band calibration" (2.2 DGC) [from (cite: Holdaway2004b)]

### Not stated but needed to reproduce (our reading)

- CASA version and tasks used for B2B/DGC phase transfer (custom scripts not described or released)
- Exact manual flagging commands and antennas flagged
- Imaging parameters for HL Tau/VY CMa (cell size, image size, masks, niter, thresholds)
- Line-free channel selection for VY CMa continuum
- Self-calibration reference model and gain interpolation
- Calibrator names for bandpass in HL Tau; coordinates of targets
- Method for calculating image coherence/peak measurements and fitting Gaussian components

## Analysis recipe

1. **Derive DGC solutions**: Time-average LF DGC phases, apply to LF DGC, frequency-transfer short-term solutions to HF DGC, average HF to get HF offset (DGC solution)  
  > "This should correct the HF atmospheric fluctuations, so the HF DGC data can then be averaged in time and used to derive a HF phase offset" (2.3 Implementation)
   - software: CASA
   - parameter: Frequency scaling ratio R = HF/LF; WVR and Tsys corrections applied beforehand  
  > "The WVR phase correction and the system noise temperature correction have been applied to all of the data before this workflow starts." (2.3 Implementation)
   - assumption: Non-dispersive atmosphere with simple frequency scaling  
  > "we adopted the simple frequency scaling ratio for B2B phase referencing" (3 Strategy)
   - fitting: _not stated_
   - validation: DGC stability vs sky position and baseline; std dev 10-20 deg (Band 7), ~30 deg Bands 8-9  
  > "The DGC solution in Band 7 has a roughly a standard deviation of $10^{\circ}$–$20^{\circ}$, independent of the sky positions of the QSOs." (4.1 Stage 2)
2. **Compare B2B vs in-band phase referencing image quality**: Image the same target with B2B and in-band calibrators at several separations; cull calibrator scans to mimic 60 s cycles; compute image coherence as peak ratio with/without self-cal  
  > "Here we define the image coherence as the ratio between peak flux densities for data with and without self-calibration applied." (4.2 Stage 3)
   - software: CASA
   - parameter: Briggs robust 0.5, 50 CLEAN iterations, self-cal solint ~1 s  
  > "we could use a solution interval of $\sim 1$ s as the S/N was high" (4.2)
   - fitting: _not stated_
   - validation: Self-calibrated images as reference; coherence factor exp(-sigma^2/2)  
  > "the image coherence can be equivalent to a coherence factor $\exp(-{{{\sigma_{\phi}}^{2}/{2}}})$" (4.2)
3. **High-resolution imaging of QSO, HL Tau, VY CMa and fidelity comparison with SV data**: B2B + DGC calibration, imaging with natural/Briggs weights, self-cal for VY CMa, comparison with LBC-2014/2013 SV images and flux scaling  
  > "ALMA quasi end-to-end observation experiments were arranged in stage 4." (4.3)
   - software: CASA
   - assumption: HL Tau central peak optically thick (alpha=2) for flux scaling from Band 7 to 671 GHz  
  > "Using the simple assumption that the central peak of emission is completely optically thick ($\alpha$=2)" (4.3.2)
   - fitting: 2D Gaussian fit to VY CMa in image plane  
  > "A resolved two-dimensional Gaussian component fitted to VY CMa in the LBC-2013-SV image" (4.3.3)
   - validation: Compared images/flux densities with SV data  
  > "These results are consistent within the $\sim 20$% error for the LBC-2013-SV fluxes." (4.3.3)
4. **Phase calibrator availability statistics**: Fit power law to catalog fluxes (Bands 3-7 or 3-6), count sources above required flux density for S/N=20xR in 8 s, derive mean solid angle and separation  
  > "flux density at an arbitrary frequency is evaluated by fitting the flux density measurements between Bands 3 and 7 or Bands 3 and 6 to a power-law function" (5 Discussions)
   - parameter: 8 s scan, 43 antennas, 7.5 GHz (Bands 3-8) or 15 GHz (Bands 9, 10), top 30% brightest sources, decl < +25 deg  
  > "We constrain the decl. range lower than $+25^{\circ}$." (5 Discussions)
   - assumption: Antennas at zenith; highest flux across epochs used  
  > "The antennas are assumed to be directed to zenith." (5 Discussions)
   - fitting: _not stated_
   - validation: Checked sky-distribution bias qualitatively  
  > "We conclude that the current investigation is not seriously affected by the calibrator distribution bias." (5 Discussions)

## Software

- **CASA** : data reduction, CLEAN imaging  
  > "For many parts of our data reduction, we made use of the Common Astronomy Software Applications (CASA) package" (4 Results)
- **AATM** : atmospheric dispersive delay calculation (ALMA ATM program)  
  > "calculated with the ALMA ATM program" (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Image coherence at 5.8 deg in-band separation | 71 | not stated | % | 2 | the image coherence is 71% and 64% for the $5.^{\circ}8$ and $8.^{\circ}7$ separation angles |
| Image coherence at 8.7 deg in-band separation | 64 | not stated | % | 2 | the image coherence is 71% and 64% for the $5.^{\circ}8$ and $8.^{\circ}7$ separation angles |
| Image coherence QSO J2228-0753 Band 7 / Band 8 | 94 / 84 | not stated | % | 3 | We obtained high image coherences of 94% and 84% in Bands 7 and 8, respectively |
| HL Tau Band 9 peak (natural weighting) | 24.9 | not stated | mJy/beam | 3 | The naturally weighted HF-LBC-2017 Band 9 image yields a peak of 24.9 mJy beam$^{-1}$, suggesting a coherence of around 56%. |
| VY CMa continuum peak before/after self-cal | 42 to 135 | not stated | mJy/beam | 3 | Improvements were seen on the continuum peak, which increased from 42 to 135 mJy beam$^{-1}$ |
| VY CMa flux density in HF-LBC-2017 image at 669 GHz | 394 | ~20% | mJy | 3 | Fitting to a similar sized-aperture for VY CMa in our image gives 394 mJy at the reference frequency of 669 GHz. |
| VY CMa position offset from LBC-2013-SV | (47, 5) | LBC-2013-SV 35 mas | mas | 3 | The position is offset by (47, 5) mas from the position measured from the most astrometrically accurate LBC-2013-SV observations |
| Mean separation to phase calibrator, Band 10 B2B with Band 3 vs in-band | 4.3 vs 12.6 | not stated | deg | 4 | Band 10 (873) /   Band 3 (97)   /        0.287         /       4.3       /; Band 10 (873) /  Band 10 (873)  /         0.792         /      12.6       / |
| DGC solution RMS phase noise Band 7 / Bands 8-9 | 10-20 / 30-40 | not stated | deg | 1 | the RMS phase noise of the DGC solutions is typically $10^{\circ}$–$20^{\circ}$ in Band 7, while this can increase to $30^{\circ}$–$40^{\circ}$ in Bands 8 and 9 |

## Qualitative findings

- DGC instrumental phase offset difference is stable for approximately 1 hr  
  > "the instrumental phase offset difference determined from the DGC solution is stable for approximately 1 hr" (4.1)

## Claim tuples

- H: DGC can remove the instrumental phase offset between LF and HF bands stably | E: Stage 2 observations of bright QSOs up to 100 deg apart | R: DGC std dev 10-20 deg Band 7, ~30 deg Bands 8-9, independent of sky position | F: DGC is satisfactorily stable, apart from problematic antennas | **supported**
- H: B2B matches in-band phase referencing with the same calibrator and in-band degrades with separation | E: Stage 3 Band 8-4 comparison with four separation angles | R: coherence 71% and 64% at 5.8 and 8.7 deg; B2B at 1.2 deg ~ unity | F: Calibrator should be within ~6 deg for coherence >=70% | **supported**
- H: B2B phase referencing enables high-fidelity submm imaging at the longest baselines | E: Stage 4 imaging of QSO, HL Tau, VY CMa | R: beams 14x11 mas (HL Tau) and 10x8 mas (VY CMa); coherence 56-94% depending on source | F: Capability demonstrated, but short uv coverage needed for extended sources | **supported**
- H: B2B offers closer phase calibrators than in-band | E: Calibrator catalog counting | R: mean separation lower in Bands 8-10, comparable in Band 7 | F: B2B beneficial in Bands 8-10, no merit in Band 7 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Bright calibrators are scarce at high frequency, so tracking a calibrator at lower frequency allows a closer one  
  > "For B2B phase referencing, it is expected that a closer phase calibrator to a target can be used, comparing to standard in-band phase referencing." (abstract)
- Alternative: Briggs weightings with smaller robust rejected for HL Tau as they resolve out extended emission  
  > "Briggs weightings with smaller robustness parameters form too-sharp beams resolving out almost all of the extended emission" (4.3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Poor uv sampling at short baselines causes sidelobe stripes and loss of extended structure; many flags, problematic antennas  
  > "the poor ($u$, $v$) sampling of the largely extended disk structure causes a striped side-lobe pattern throughout our Band 9 image" (4.3.2)
- Limitation (authors): Band 10 experiments failed; B2B separation dependence not systematically tested  
  > "Both failed after that because the observed sources were too weak to confirm whether the fringes were detected or not." (3 Strategy)
- Caveat (inferred, ours): B2B image-quality vs separation inferred from in-band tests, not measured
- Caveat (inferred, ours): Small number of datasets shown; full study deferred to unpublished paper
- Caveat (inferred, ours): Coherence estimates depend on atmosphere and untuned scan settings
- Caveat (inferred, ours): No uncertainties on most coherence numbers

## Reproducibility

- Data public (paper): EB uids listed in tables; SV projects cited  
  > "For this research, we used the ALMA data listed in" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom B2B/DGC CASA scripts
- Missing: CASA version
- Missing: Full imaging parameters for stage 4
- Missing: Maud2020 and Asaki2019 details
- Data volume (inferred): Several hundred GB to ~1 TB for the listed EBs (long-baseline, wide bandwidth)
- Score (inferred): 3/5, EBs are listed but the B2B/DGC calibration software and many imaging/flagging details are not given.
- Rediscovery candidate: no, Calibration workflow is non-standard and not fully specified; custom scripts needed.

## Links

- Method: (cite: Holdaway2004b) (Cross-band calibration concept)
- Method: (cite: Matsushita2017) (WVR and phase referencing performance)
- Companion: (cite: Asaki2019) (Details of QSO Band 7/8 observations)
- Companion: (cite: Maud2020) (Full Stage 3 study of 50 datasets)
- Related: ALMA Long Baseline Campaigns 2013, 2014, 2015
- Related: HF-LBC-2017

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 50,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
