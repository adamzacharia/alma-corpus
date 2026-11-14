# A New Constraint on the Molecular Oxygen Abundance at z ~ 0.886

`2015ApJ...811L..23K` | The Astrophysical Journal Letters 2015 | first author: Kanekar, Nissim | arXiv: 1509.03670 | DOI: 10.1088/2041-8205/811/2/L23

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, high_z_galaxies
- Question: What is the molecular oxygen (O2) abundance in the z = 0.88582 absorber towards PKS 1830-21, probed via redshifted O2 56 GHz (VLA) and 424 GHz (ALMA) absorption?  
  > "We have used the Karl G. Jansky Very Large Array (VLA) and the Atacama Large Millimeter Array (ALMA) to search" (1. INTRODUCTION)
- Target **PKS 1830-21 (z = 0.88582 lens)**: coordinates _not stated_; z/distance z = 0.88582 (absorber); z = 2.507 (background quasar)  
  > "from the z = 0.88582 gravitational lens towards PKS 1830−21" (abstract); distance from z = 2.507 from Lidman et al. 1999  
  > "from the z = 0.88582 gravitational lens towards PKS 1830−21" (abstract)

## Data provenance

- ALMA projects: 2012.1.00581.S
- bands: ALMA Band 6  
  > "The Band-6 receivers of ALMA were used in March 2014" (2.2. ALMA observations)
- frequencies and spectral setup: Four 1.875 GHz IF bands, 3840 channels each, centred at 225.780, 228.530, 241.033, 243.733 GHz  
  > "The four IF bands were centred at 225.780 GHz (covering the redshifted O 2 424 GHz line frequency), 228.530 GHz, 241.033 GHz and 243.733 GHz." (2.2. ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈1.0″ × 0.8″  
  > "The final image has a synthesized beam of ≈ 1.0 [′′] × 0.8 [′′]" (2.2. ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ALMA ≈2 hours with 25 antennas; VLA 2 hours with 19 antennas  
  > "The total on-source time was ≈ 2 hours, with 25 ALMA antennas." (2.2. ALMA observations)
- observing dates: ALMA March 2014; VLA July 2010  
  > "The Band-6 receivers of ALMA were used in March 2014" (2.2. ALMA observations)
- pi or archival as stated: _not stated_
- Line: O2 1_2 → 3_2 (424.7631 GHz)
- Other facility **VLA**: Ka-band search for O2 56.2648 GHz absorption (proposal AK725), 2 h in C-configuration  
  > "The Ka-band receivers of the VLA were used in July 2010 to carry out a search for O 2 1 2 → 1 1 56.2648 GHz absorption" (2.1. VLA observations)
- External data: N(H2) ≈ 2.5e22 cm^-2 for the z~0.886 lens  
  > "The H 2 column density of the z ∼ 0.886 lens has been estimated to be ≈ 2.5 × 10 [22] cm [−][2]" (3. DISCUSSION) [from Gerin et al. 1997; Wiklind & Combes 1998]
- External data: Kinetic temperature T_k ≈ 80 K and n_H2 ~ 1700-2600 cm^-3  
  > "T k ≈ 80 K (Henkel et al. 2008, 2009)" (3. DISCUSSION) [from Henkel et al. 2008, 2009]
- External data: S-W component holds ≈38% of total flux density  
  > "the S-W component contains ≈ 38% of the total flux density of PKS 1830−21 at these frequencies" (2.1. VLA observations) [from Muller et al. 2011]

## Processing

### Calibration

- pipeline or manual: CASA pipeline initial calibration, then self-calibration in AIPS  
  > "first using the CASA pipeline to carry out the initial calibration procedure, and then self-calibrating the data of PKS 1830−21 in AIPS" (2.2. ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (short baselines), bootstrapped to J1923−2104  
  > "The flux density scale was calibrated using the shortbaseline data on Titan, and this was then extended to longer baselines by bootstrapping the data of J1923−2104." (2.2. ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: A few rounds of phase-only, then one round of amplitude-and-phase self-cal in AIPS  
  > "a standard self-calibration procedure was used in AIPS, with a few rounds of phase-only selfcalibration followed by a single round of amplitude-and-phase self-calibration" (2.2. ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image subtracted from visibilities per IF band with UVSUB  
  > "The continuum image of PKS 1830−21 was then subtracted from the calibrated visibilities of each IF band using the task UVSUB" (2.2. ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing and resampling to ≈6.5 km/s  
  > "All spectra are shown after smoothing to, and re-sampling at, a velocity resolution of ≈ 6.5 km s [−][1]" (2.2. ALMA observations)
- final beam: ≈1.0″ × 0.8″  
  > "The final image has a synthesized beam of ≈ 1.0 [′′] × 0.8 [′′]" (2.2. ALMA observations)
- final rms: ≈0.14 mJy/Beam continuum; 1.0-1.3 mJy spectra at ≈1.3 km/s  
  > "an RMS noise of ≈ 0.14 mJy/Beam." (2.2. ALMA observations)

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, cell size, image size, deconvolution) for AIPS imaging
- Self-calibration solution intervals
- Line-free channels used for the second-order baseline
- Exact line-width/velocity range for the integrated optical depth limit
- Excitation modeling details converting tau to N(O2) (rate coefficients, partition function)
- Pipeline CASA version

## Analysis recipe

1. **Calibrate and self-calibrate ALMA data**: CASA pipeline initial calibration, then AIPS self-calibration  
  > "first using the CASA pipeline to carry out the initial calibration procedure, and then self-calibrating the data of PKS 1830−21 in AIPS" (2.2. ALMA observations)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux densities**: 2-Gaussian fit to the final image with JMFIT  
  > "The task JMFIT was used to measure the flux densities of the N-E and S-W image components, via a 2-Gaussian fit to the final image" (2.2. ALMA observations)
   - software: AIPS JMFIT
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract optical-depth spectra and search for O2 424 GHz**: Subtract continuum with UVSUB, image to cube, take cut at S-W component, Hanning smooth, subtract 2nd-order baseline  
  > "The spectrum for each IF band was then produced via a cut through the cube at the location of the S-W image component." (2.2. ALMA observations)
   - software: AIPS UVSUB
   - parameter: velocity resolution ≈6.5 km/s  
  > "the resolution at which the search for redshifted O 2 424 GHz absorption was carried out" (2.2. ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive O2 column density and abundance limits**: 3σ integrated optical depth limit converted to N(O2) assuming thermalized levels; divide by N(H2)  
  > "For T x = 80 K, this gives N(O 2 ) ≤ 5.8 × 10 [17] cm [−][2], at 3σ significance." (3. DISCUSSION)
   - assumption: T_x = T_k = 80 K; N(H2) = 2.5e22 cm^-2  
  > "Using a value of N(H 2 ) = 2.5 × 10 [22] cm [−][2] yields O 2 abundances" (3. DISCUSSION)
   - fitting: _not stated_
   - validation: Compared 424 GHz limit with VLA 56 GHz feature, with tau424 ≈ 1.1 × tau56  
  > "the 424 GHz line is expected to be slightly stronger than the 56 GHz line, τ 424 ≈ 1.1 × τ 56" (3. DISCUSSION)

## Software

- **CASA** : pipeline initial calibration of ALMA data  
  > "first using the CASA pipeline to carry out the initial calibration procedure" (2.2. ALMA observations)
- **AIPS** : self-calibration, imaging, JMFIT, UVSUB; VLA data analysis  
  > "The VLA data were analysed in “classic” AIPS using standard procedures." (2.1. VLA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(O2) 3σ upper limit (ALMA) | 5.8e17 | not stated | cm^-2 | 4 | N (O 2 ) ≤ 5.8 × 10 [17] cm [−][2] |
| N(O2) 3σ upper limit (VLA, CH3CHO-subtracted) | 2.3e17 | not stated | cm^-2 | 4 | yields N (O 2 ) ≤ 2.3 × 10 [17] cm [−][2] |
| X(O2) upper limit (ALMA) | 2.3e-5 | not stated | dimensionless | 4 | X(O 2 ) ≤ 2.3 × 10 [−][5] (ALMA) |
| X(O2) upper limit (VLA) | 9.1e-6 | not stated | dimensionless | 4 | X(O 2 ) ≤ 9.1 × 10 [−][6] (VLA) |
| ALMA 3σ integrated O2 424 GHz optical depth limit | 0.037 | not stated | km/s | 3 | Our ALMA 3σ limit on the integrated O 2 424 GHz optical depth is ≈ 0.037 km s [−][1] |
| ALMA continuum flux densities | 549.98 (N-E), 342.63 (S-W) | 0.43 mJy each | mJy | 2 | 549.98 ± 0.43 mJy (N-E) and 342.63 ± 0.43 mJy (S-W) |

## Qualitative findings

- An unidentified absorption line at ≈226.033 GHz was detected in the ALMA spectra.  
  > "we have been unable to identify the fourth transition, at ≈ 226.033 GHz" (2.2. ALMA observations)

## Claim tuples

- H: Does the VLA 29.836 GHz feature arise from O2 56 GHz? | E: Compare the ALMA O2 424 GHz optical depth limit with the VLA feature | R: ALMA limit 0.037 km/s vs VLA 0.146 km/s | F: The feature is CH3CHO, not O2 | **supported**
- H: How low is X(O2) in the z=0.886 absorber? | E: Subtract the CH3CHO line profile from the VLA spectrum; use the ALMA limit | R: X(O2) ≤ 9.1e-6 (VLA), ≤ 2.3e-5 (ALMA) | F: The tightest extragalactic constraint, ≳15 times better than previous | **supported**
- H: Why is O2 abundance low? | E: Compare with literature neutral carbon abundance and cloud properties | R: N(C)/N(H2) ≈ 1e-4 and diffuse/translucent clouds | F: High C abundance and translucent clouds may explain low O2 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: A much higher N(H2) (Muller & Guélin 2008) appears ruled out by X-ray data.  
  > "such a high value of N(H 2 ) appears to be ruled out by the X-ray data" (3. DISCUSSION)
- How they decided it was enough: _not stated_
- Limitation (authors): Limits remain well above Galactic values, and high gas temperature makes improvement difficult.  
  > "it will not be easy to improve upon our present constraint" (3. DISCUSSION)
- Caveat (inferred, ours): Limits depend on the assumed T_x=80 K and N(H2)
- Caveat (inferred, ours): Frequency-dependent covering factor and lens differential absorption not discussed
- Caveat (inferred, ours): Strongest limit relies on the VLA CH3CHO subtraction assumption of equal line strengths

## Reproducibility

- Data public (paper): ALMA project 2012.1.00581.S acknowledged; VLA proposal 10A-110  
  > "This paper also makes use of VLA data (proposal 10A-110)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: AIPS imaging and self-cal parameters
- Missing: Conversion from optical depth to column density details
- Missing: Line-free channel selection
- Data volume (inferred): tens of GB (ALMA Band 6, 4 spectral windows × 3840 channels, ~2 h)
- Score (inferred): 3/5, Short letter with clear numeric limits but sparse processing details.
- Rediscovery candidate: no, Recipe details (AIPS parameters, tau-to-N conversion) are insufficiently specified, though data are archival.

## Links

- Companion: Henkel et al. 2008, 2009 (Physical conditions (T_k, density) of the absorber)
- Companion: Combes et al. 1997 (Previous O2 limit in the z=0.685 absorber)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 32,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
